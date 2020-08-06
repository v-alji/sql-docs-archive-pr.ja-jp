---
title: メモリ最適化されたハッシュインデックスのパフォーマンスに関する一般的な問題のトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 1954a997-7585-4713-81fd-76d429b8d095
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3cef98571edd7736bc45ba8caf17451007a74cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712350"
---
# <a name="troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes"></a><span data-ttu-id="5ef64-102">メモリ最適化されたハッシュ インデックスのパフォーマンスに関する一般的な問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5ef64-102">Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes</span></span>
  <span data-ttu-id="5ef64-103">このトピックはハッシュ インデックスの一般的な問題のトラブルシューティングと回避方法に焦点を当てて説明します。</span><span class="sxs-lookup"><span data-stu-id="5ef64-103">This topic will focus on troubleshooting and working around common issues with hash indexes.</span></span>  
  
## <a name="search-requires-a-subset-of-hash-index-key-columns"></a><span data-ttu-id="5ef64-104">検索を使用するにはハッシュ インデックス キー列のサブセットが必要になる</span><span class="sxs-lookup"><span data-stu-id="5ef64-104">Search Requires a Subset of Hash Index Key Columns</span></span>  
 <span data-ttu-id="5ef64-105">**問題:** ハッシュインデックスは、ハッシュ値を計算するためにすべてのインデックスキー列の値を必要とし、ハッシュテーブル内の対応する行を検索します。</span><span class="sxs-lookup"><span data-stu-id="5ef64-105">**Issue:** Hash indexes require values for all index key columns in order to compute the hash value, and locate the corresponding rows in the hash table.</span></span> <span data-ttu-id="5ef64-106">したがって、クエリに WHERE 句のインデックス キーのサブセットのみの等値述語が含まれていると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は WHERE 句の述語に対応する行を検索するインデックス シークを使用できません。</span><span class="sxs-lookup"><span data-stu-id="5ef64-106">Therefore, if a query includes equality predicates for only a subset of the index keys in the WHERE clause, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot use an index seek to locate the rows corresponding to the predicates in the WHERE clause.</span></span>  
  
 <span data-ttu-id="5ef64-107">これに対し、ディスク ベースの非クラスター化インデックスおよびメモリ最適化非クラスター化インデックスのような並べ替えられたインデックスは、インデックス内の先頭列である限り、インデックス キー列のサブセットに対するインデックス シークをサポートします。</span><span class="sxs-lookup"><span data-stu-id="5ef64-107">In contrast, ordered indexes like the disk-based nonclustered indexes and the memory-optimized nonclustered indexes support index seek on a subset of the index key columns, as long as they are the leading columns in the index.</span></span>  
  
 <span data-ttu-id="5ef64-108">**症状:** この結果、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インデックスシークではなくフルテーブルスキャンを実行する必要があるため、パフォーマンスが低下します。これは通常、より高速な操作です。</span><span class="sxs-lookup"><span data-stu-id="5ef64-108">**Symptom:** This results in a performance degradation, as [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] needs to execute full table scans rather than an index seek, which is typically a faster operation.</span></span>  
  
 <span data-ttu-id="5ef64-109">**トラブルシューティングの方法:** パフォーマンスの低下に加えて、クエリプランの検査では、インデックスシークではなくスキャンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ef64-109">**How to troubleshoot:** Besides the performance degradation, inspection of the query plans will show a scan instead of an index seek.</span></span> <span data-ttu-id="5ef64-110">クエリが非常に単純である場合は、クエリ テキストおよびインデックス定義の検査も検索にインデックス キー列のサブセットが必要かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5ef64-110">If the query is fairly simple, inspection of the query text and index definition will also show whether the search requires a subset of the index key columns.</span></span>  
  
 <span data-ttu-id="5ef64-111">次のテーブルとクエリを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="5ef64-111">Consider the following table and query:</span></span>  
  
```sql  
CREATE TABLE [dbo].[od]  
(  
     o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
     CONSTRAINT PK_od PRIMARY KEY NONCLUSTERED HASH (o_id, od_id) WITH (BUCKET_COUNT = 10000)  
)  
WITH (MEMORY_OPTIMIZED = ON)  
  
 SELECT p_id  
 FROM dbo.od  
 WHERE o_id=1  
```  
  
 <span data-ttu-id="5ef64-112">クエリには (o_id) に等値述語がありますが、テーブルには 2 列 (o_id、od_id) にハッシュ インデックスがあります。</span><span class="sxs-lookup"><span data-stu-id="5ef64-112">The table has a hash index on the two columns (o_id, od_id), while the query has an equality predicate on (o_id).</span></span> <span data-ttu-id="5ef64-113">クエリにはインデックス キー列のサブセットのみに等値述語があるため、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は PK_od を使用してインデックス シーク操作を実行できません。代わりに、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] はフル インデックス スキャンに戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ef64-113">As the query has equality predicates on only a subset of the index key columns, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot perform an index seek operation using PK_od; instead, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has to revert to a full index scan.</span></span>  
  
 <span data-ttu-id="5ef64-114">**回避策:** 考えられる回避策は多数あります。</span><span class="sxs-lookup"><span data-stu-id="5ef64-114">**Workarounds:** There are a number of possible workarounds.</span></span> <span data-ttu-id="5ef64-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5ef64-115">For example:</span></span>  
  
-   <span data-ttu-id="5ef64-116">インデックスを非クラスター化ハッシュではなく非クラスター化型として再作成します。</span><span class="sxs-lookup"><span data-stu-id="5ef64-116">Recreate the index as type nonclustered instead of nonclustered hash.</span></span> <span data-ttu-id="5ef64-117">メモリ最適化非クラスター化インデックスが順序付きであるため、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は先頭のインデックス キー列のインデックス シークを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5ef64-117">The memory-optimized nonclustered index is ordered, and thus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can perform an index seek on the leading index key columns.</span></span> <span data-ttu-id="5ef64-118">例の結果の主キーの定義は `constraint PK_od primary key nonclustered` です。</span><span class="sxs-lookup"><span data-stu-id="5ef64-118">The resulting primary key definition for the example would be `constraint PK_od primary key nonclustered`.</span></span>  
  
-   <span data-ttu-id="5ef64-119">WHERE 句の列と一致するように現在のインデックス キーを変更します。</span><span class="sxs-lookup"><span data-stu-id="5ef64-119">Change the current index key to match the columns in the WHERE clause.</span></span>  
  
-   <span data-ttu-id="5ef64-120">クエリの WHERE 句の列と一致する新しいハッシュ インデックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="5ef64-120">Add a new hash index that matches with the columns in the WHERE clause of the query.</span></span> <span data-ttu-id="5ef64-121">例では、結果のテーブル定義は次のようになります:</span><span class="sxs-lookup"><span data-stu-id="5ef64-121">In the example, the resulting table definition would look at follows:</span></span>  
  
    ```sql  
    CREATE TABLE dbo.od  
     ( o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
  
     CONSTRAINT PK_od PRIMARY KEY   
     NONCLUSTERED HASH (o_id,od_id) WITH (BUCKET_COUNT=10000),  
  
     INDEX ix_o_id NONCLUSTERED HASH (o_id) WITH (BUCKET_COUNT=10000)  
  
     ) WITH (MEMORY_OPTIMIZED=ON)  
    ```  
  
 <span data-ttu-id="5ef64-122">特定のインデックス キー値に多くの重複する行がある場合、メモリ最適化ハッシュ インデックスは適切に機能しないことに注意してください: 例では、列 o_id の一意の値の数がテーブルの行数よりもかなり少ない場合、(o_id) のインデックスを追加することは最適ではなく、代わりに、インデックス PK_od の種類をハッシュから非クラスター化に変更することがより適切な解決策です。</span><span class="sxs-lookup"><span data-stu-id="5ef64-122">Note that a memory-optimized hash index does not perform optimally if there are a lot of duplicate rows for a given index key value: in the example, if the number of unique values for the column o_id is much smaller than the number of rows in the table, it would not be optimal to add an index on (o_id); instead, changing the type of the index PK_od from hash to nonclustered would be the better solution.</span></span> <span data-ttu-id="5ef64-123">詳細については、「 [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef64-123">For more information, see [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef64-124">参照</span><span class="sxs-lookup"><span data-stu-id="5ef64-124">See Also</span></span>  
 [<span data-ttu-id="5ef64-125">メモリ最適化テーブルのインデックス</span><span class="sxs-lookup"><span data-stu-id="5ef64-125">Indexes on Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
