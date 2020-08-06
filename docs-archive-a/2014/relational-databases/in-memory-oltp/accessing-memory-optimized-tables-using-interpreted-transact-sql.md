---
title: 解釈された Transact-SQL を使用したメモリ最適化テーブルへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
author: rothja
ms.author: jroth
ms.openlocfilehash: af4b3ca7731e7ca13e697f43e76ac3cc3cacb4f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643826"
---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a><span data-ttu-id="a9dbb-102">解釈された Transact-SQL を使用したメモリ最適化テーブルへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a9dbb-102">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>
  <span data-ttu-id="a9dbb-103">いくつかの例外を除き、[!INCLUDE[tsql](../../includes/tsql-md.md)] クエリまたは DML 操作 (SELECT、INSERT、UPDATE、または DELETE)、アドホック バッチ、および SQL モジュール (ストアド プロシージャ、テーブル値関数、トリガー、ビューなど) を使用して、メモリ最適化テーブルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-103">With only a few exceptions, you can access memory-optimized tables using any [!INCLUDE[tsql](../../includes/tsql-md.md)] query or DML operation (SELECT, INSERT, UPDATE, or DELETE), ad hoc batches, and SQL modules such as stored procedures, table-value functions, triggers, and views.</span></span>  
  
 <span data-ttu-id="a9dbb-104">インタープリターによって処理される [!INCLUDE[tsql](../../includes/tsql-md.md)] とは、ネイティブ コンパイル ストアド プロシージャとは異なる、 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチまたはストアド プロシージャを意味します。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-104">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] refers to [!INCLUDE[tsql](../../includes/tsql-md.md)] batches or stored procedures other than a natively compiled stored procedure.</span></span> <span data-ttu-id="a9dbb-105">インタープリターによって処理される [!INCLUDE[tsql](../../includes/tsql-md.md)] による、メモリ最適化されたテーブルへのアクセスは、相互運用アクセスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-105">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access to memory-optimized tables is referred to as interop access.</span></span>  
  
 <span data-ttu-id="a9dbb-106">メモリ最適化テーブルには、ネイティブ コンパイル ストアド プロシージャを使用してアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-106">Memory-optimized tables can also be accessed using a natively compiled stored procedure.</span></span> <span data-ttu-id="a9dbb-107">ネイティブ コンパイル ストアド プロシージャは、パフォーマンスが重要な OLTP 操作に推奨されます。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-107">Natively compiled stored procedures are recommended for performance-critical OLTP operations.</span></span>  
  
 <span data-ttu-id="a9dbb-108">解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] によるアクセスは、次のシナリオにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-108">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access is recommended for these scenarios:</span></span>  
  
-   <span data-ttu-id="a9dbb-109">アドホック クエリおよび管理タスク。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-109">Ad hoc queries and administrative tasks.</span></span>  
  
-   <span data-ttu-id="a9dbb-110">通常は構造を使用するレポート クエリ (ウィンドウ関数など) は、ネイティブ コンパイル ストアド プロシージャでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-110">Reporting queries, which typically use constructs not available in natively compiled stored procedures (such as window functions).</span></span>  
  
-   <span data-ttu-id="a9dbb-111">アプリケーション コードの変更を最小限に抑えて (またはコードを変更することなく)、アプリケーションのパフォーマンスが重要な部分をメモリ最適化テーブルに移行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-111">To migrate performance-critical parts of your application to memory-optimized tables, with minimal (or no) application code changes.</span></span> <span data-ttu-id="a9dbb-112">テーブルを移行すると、パフォーマンス向上を確認できることがあります。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-112">You can potentially see performance improvements from migrating tables.</span></span> <span data-ttu-id="a9dbb-113">ストアド プロシージャをネイティブ コンパイル ストアド プロシージャに移行すると、いっそうのパフォーマンス向上が確認されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-113">If you then migrate stored procedures to natively compiled stored procedures, you may see further performance improvement.</span></span>  
  
-   <span data-ttu-id="a9dbb-114">ネイティブ コンパイル ストアド プロシージャでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用できません。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-114">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is not available for natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="a9dbb-115">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] 構造は、メモリ最適化テーブル内のデータにアクセスする、解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-115">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs are not supported in interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures that access data in a memory-optimized table.</span></span>  
  
|<span data-ttu-id="a9dbb-116">領域</span><span class="sxs-lookup"><span data-stu-id="a9dbb-116">Area</span></span>|<span data-ttu-id="a9dbb-117">サポートされていない</span><span class="sxs-lookup"><span data-stu-id="a9dbb-117">Unsupported</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a9dbb-118">テーブルへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a9dbb-118">Access to tables</span></span>|<span data-ttu-id="a9dbb-119">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="a9dbb-119">TRUNCATE TABLE</span></span><br /><br /> <span data-ttu-id="a9dbb-120">MERGE (ターゲットとしてのメモリ最適化テーブル)</span><span class="sxs-lookup"><span data-stu-id="a9dbb-120">MERGE (memory-optimized table as target)</span></span><br /><br /> <span data-ttu-id="a9dbb-121">動的カーソルおよびキーセット カーソル (これらは自動的に静的カーソルに降格されます)。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-121">Dynamic and keyset cursors (these automatically degrade to static).</span></span><br /><br /> <span data-ttu-id="a9dbb-122">コンテキスト接続を使用した CLR モジュールからのアクセス。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-122">Access from CLR modules, using the context connection.</span></span><br /><br /> <span data-ttu-id="a9dbb-123">インデックス付きビューから、メモリ最適化されたテーブルへの参照。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-123">Referencing a memory-optimized table from an indexed view.</span></span>|  
|<span data-ttu-id="a9dbb-124">複数のデータベース間</span><span class="sxs-lookup"><span data-stu-id="a9dbb-124">Cross-database</span></span>|<span data-ttu-id="a9dbb-125">複数データベースにまたがるクエリ</span><span class="sxs-lookup"><span data-stu-id="a9dbb-125">Cross-database queries</span></span><br /><br /> <span data-ttu-id="a9dbb-126">データベースにまたがるトランザクション</span><span class="sxs-lookup"><span data-stu-id="a9dbb-126">Cross-database transactions</span></span><br /><br /> <span data-ttu-id="a9dbb-127">リンク サーバー</span><span class="sxs-lookup"><span data-stu-id="a9dbb-127">Linked servers</span></span>|  
  
## <a name="table-hints"></a><span data-ttu-id="a9dbb-128">テーブル ヒント</span><span class="sxs-lookup"><span data-stu-id="a9dbb-128">Table Hints</span></span>  
 <span data-ttu-id="a9dbb-129">テーブル ヒントの詳細については、</span><span class="sxs-lookup"><span data-stu-id="a9dbb-129">For more information about table hints, see.</span></span> <span data-ttu-id="a9dbb-130">[テーブル ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span><span class="sxs-lookup"><span data-stu-id="a9dbb-130">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span> <span data-ttu-id="a9dbb-131">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] をサポートするために SNAPSHOT 分離が追加されました。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-131">SNAPSHOT isolation was added to support [!INCLUDE[hek_2](../../includes/hek-2-md.md)].</span></span>  
  
 <span data-ttu-id="a9dbb-132">次のテーブル ヒントは、解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してメモリ最適化テーブルにアクセスする場合はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-132">The following table hints are not supported when accessing a memory-optimized table using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="a9dbb-133">HOLDLOCK</span><span class="sxs-lookup"><span data-stu-id="a9dbb-133">HOLDLOCK</span></span>|<span data-ttu-id="a9dbb-134">IGNORE_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="a9dbb-134">IGNORE_CONSTRAINTS</span></span>|<span data-ttu-id="a9dbb-135">IGNORE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="a9dbb-135">IGNORE_TRIGGERS</span></span>|<span data-ttu-id="a9dbb-136">NOWAIT</span><span class="sxs-lookup"><span data-stu-id="a9dbb-136">NOWAIT</span></span>|  
|<span data-ttu-id="a9dbb-137">PAGLOCK</span><span class="sxs-lookup"><span data-stu-id="a9dbb-137">PAGLOCK</span></span>|<span data-ttu-id="a9dbb-138">READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="a9dbb-138">READCOMMITTED</span></span>|<span data-ttu-id="a9dbb-139">READCOMMITTEDLOCK</span><span class="sxs-lookup"><span data-stu-id="a9dbb-139">READCOMMITTEDLOCK</span></span>|<span data-ttu-id="a9dbb-140">READPAST</span><span class="sxs-lookup"><span data-stu-id="a9dbb-140">READPAST</span></span>|  
|<span data-ttu-id="a9dbb-141">READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="a9dbb-141">READUNCOMMITTED</span></span>|<span data-ttu-id="a9dbb-142">ROWLOCK</span><span class="sxs-lookup"><span data-stu-id="a9dbb-142">ROWLOCK</span></span>|<span data-ttu-id="a9dbb-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span><span class="sxs-lookup"><span data-stu-id="a9dbb-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span></span>|<span data-ttu-id="a9dbb-144">TABLOCK</span><span class="sxs-lookup"><span data-stu-id="a9dbb-144">TABLOCK</span></span>|  
|<span data-ttu-id="a9dbb-145">TABLOCKXX</span><span class="sxs-lookup"><span data-stu-id="a9dbb-145">TABLOCKXX</span></span>|<span data-ttu-id="a9dbb-146">UPDLOCK</span><span class="sxs-lookup"><span data-stu-id="a9dbb-146">UPDLOCK</span></span>|<span data-ttu-id="a9dbb-147">XLOCK</span><span class="sxs-lookup"><span data-stu-id="a9dbb-147">XLOCK</span></span>||  
  
 <span data-ttu-id="a9dbb-148">解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用した明示的または暗黙的なトランザクションからメモリ最適化テーブルにアクセスする場合は、SNAPSHOT、REPEATABLEREAD、SERIALIZABLE などの分離レベルのテーブル ヒントを含める必要があります。あるいは、MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-148">When accessing a memory-optimized table from an explicit or implicit transaction using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] you must include either an isolation level table hint such as SNAPSHOT, REPEATABLEREAD, or SERIALIZABLE, or you can use MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT.</span></span> <span data-ttu-id="a9dbb-149">詳細については、「[メモリ最適化テーブルを使用したトランザクション分離レベルのガイドライン](memory-optimized-tables.md)」および「 [transact-sql&#41;&#40;の ALTER database SET オプション](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-149">For more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](memory-optimized-tables.md) and [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9dbb-150">自動コミット モードで実行されるクエリでアクセスするメモリ最適化テーブルの場合、分離レベルのテーブル ヒントは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a9dbb-150">An isolation level table hint is not required for memory-optimized tables accessed by queries running in auto-commit mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9dbb-151">参照</span><span class="sxs-lookup"><span data-stu-id="a9dbb-151">See Also</span></span>  
 <span data-ttu-id="a9dbb-152">[Transact-SQL によるインメモリ OLTP のサポート](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="a9dbb-152">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="a9dbb-153">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="a9dbb-153">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
