---
title: メモリ最適化オブジェクト用ストレージの作成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 622aabe6-95c7-42cc-8768-ac2e679c5089
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 118e5e582a284023dd8e5cc71629d635e79fb989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639528"
---
# <a name="creating-and-managing-storage-for-memory-optimized-objects"></a><span data-ttu-id="16dc7-102">メモリ最適化オブジェクト用ストレージの作成と管理</span><span class="sxs-lookup"><span data-stu-id="16dc7-102">Creating and Managing Storage for Memory-Optimized Objects</span></span>
  <span data-ttu-id="16dc7-103">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] には [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エンジンが統合されているため、メモリ最適化テーブルと (従来型の) ディスクベース テーブルの両方を同じデータベースに格納することができます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-103">The [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine is integrated into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], which lets you have both memory-optimized tables and (traditional) disk-based tables in the same database.</span></span> <span data-ttu-id="16dc7-104">ただし、メモリ最適化テーブルのストレージ構造は、ディスクベース テーブルとは異なります。</span><span class="sxs-lookup"><span data-stu-id="16dc7-104">However, the storage structure for memory-optimized tables is different from disk-based tables.</span></span>  
  
 <span data-ttu-id="16dc7-105">ディスクベース テーブルのストレージには、次のキー属性があります。</span><span class="sxs-lookup"><span data-stu-id="16dc7-105">Storage for disk-based table has following key attributes:</span></span>  
  
-   <span data-ttu-id="16dc7-106">ファイル グループにマップされます。ファイル グループは、1 つ以上のファイルを格納します。</span><span class="sxs-lookup"><span data-stu-id="16dc7-106">Mapped to a filegroup and the filegroup contains one or more files.</span></span>  
  
-   <span data-ttu-id="16dc7-107">各ファイルは 8 ページから成るエクステントに分割されます。各ページのサイズは 8K バイトです。</span><span class="sxs-lookup"><span data-stu-id="16dc7-107">Each file is divided into extents of 8 pages and each page is of size 8K bytes.</span></span>  
  
-   <span data-ttu-id="16dc7-108">1 つのエクステントは複数のテーブルで共有できます。ただし、割り当てられたページと、テーブルまたはインデックスの間には 1 対 1 のマッピングがあります。</span><span class="sxs-lookup"><span data-stu-id="16dc7-108">An extent can be shared across multiple tables, but a there is 1-to-1 mapping between an allocated page and the table or index.</span></span> <span data-ttu-id="16dc7-109">つまり、1 つのページに、2 つまたは複数のテーブルまたはインデックスの行を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="16dc7-109">In other words, a page can't have rows from two or more tables or index.</span></span>  
  
-   <span data-ttu-id="16dc7-110">データは必要に応じてメモリ (バッファー プール) に移動され、変更されたページや新しく作成されたページは非同期的にディスクに書き込まれ、ほぼランダムな IO が生成される結果になります。</span><span class="sxs-lookup"><span data-stu-id="16dc7-110">The data is moved into memory (the buffer pool) as needed and the modified or newly created pages are asynchronously written to the disk generating mostly random IO.</span></span>  
  
 <span data-ttu-id="16dc7-111">メモリ最適化テーブルのストレージには、次のキー属性があります。</span><span class="sxs-lookup"><span data-stu-id="16dc7-111">Storage for memory-optimized tables has following key attributes:</span></span>  
  
-   <span data-ttu-id="16dc7-112">すべてのメモリ最適化テーブルは、メモリ最適化ファイルグループにマップされます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-112">All memory-optimized tables are mapped to a memory-optimized filegroup.</span></span> <span data-ttu-id="16dc7-113">このファイルグループは、filestream ファイルグループを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-113">This filegroup is built using the filestream filegroup.</span></span>  
  
-   <span data-ttu-id="16dc7-114">ページという単位はなく、データは行として保存されます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-114">There are no pages and the data is persisted as a row.</span></span>  
  
-   <span data-ttu-id="16dc7-115">メモリ最適化テーブルに対するすべての変更は、アクティブ ファイルへの追加という形で格納されます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-115">All changes to memory-optimized tables are stored by appending to active files.</span></span> <span data-ttu-id="16dc7-116">ファイルの読み取りと書き込みのどちらもシーケンシャルに実行されます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-116">Both reading and writing to files is sequential.</span></span>  
  
-   <span data-ttu-id="16dc7-117">更新は、削除、およびその後に続く挿入という形で実装されます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-117">An update is implemented as a delete followed by an insert.</span></span> <span data-ttu-id="16dc7-118">削除された行は、ストレージから直ちに削除されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="16dc7-118">The deleted rows are not immediately removed from the storage.</span></span> <span data-ttu-id="16dc7-119">削除された行は、「 [メモリ最適化テーブルの持続性](memory-optimized-tables.md)」で説明されているポリシーに基づき、MERGE と呼ばれるバックグラウンド プロセスによって削除されます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-119">The deleted rows are removed by a background process, called MERGE, based on a policy as described in [Durability for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
-   <span data-ttu-id="16dc7-120">ディスクベース テーブルとは異なり、メモリ最適化テーブルのストレージは圧縮されません。</span><span class="sxs-lookup"><span data-stu-id="16dc7-120">Unlike disk-based tables, storage for memory-optimized tables is not compressed.</span></span> <span data-ttu-id="16dc7-121">圧縮された (行またはページの) ディスクベース テーブルをメモリ最適化テーブルに移行する場合は、サイズの変化を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16dc7-121">When migrating a compressed (ROW or PAGE) disk-based table to memory-optimized table, you will need to account for the change in size.</span></span>  
  
-   <span data-ttu-id="16dc7-122">メモリ最適化テーブルは、持続的にすることも、非持続的にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="16dc7-122">A memory-optimized table can be durable or can be non-durable.</span></span> <span data-ttu-id="16dc7-123">持続性のあるメモリのストレージを構成する必要があるのは、テーブルを最適化することだけです。</span><span class="sxs-lookup"><span data-stu-id="16dc7-123">You only need to configure storage for durable memory-optimize tables.</span></span>  
  
 <span data-ttu-id="16dc7-124">ここでは、チェックポイント ファイル ペアと、メモリ最適化テーブルのデータが格納されるしくみの他の側面について説明します。</span><span class="sxs-lookup"><span data-stu-id="16dc7-124">This section describes checkpoint file pairs and other aspects of how data in memory-optimized tables is stored.</span></span>  
  
 <span data-ttu-id="16dc7-125">このセクションのトピック:</span><span class="sxs-lookup"><span data-stu-id="16dc7-125">Topics in this section:</span></span>  
  
-   [<span data-ttu-id="16dc7-126">メモリ最適化テーブルのストレージの構成</span><span class="sxs-lookup"><span data-stu-id="16dc7-126">Configuring Storage for Memory-Optimized Tables</span></span>](configuring-storage-for-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="16dc7-127">メモリ最適化ファイルグループ</span><span class="sxs-lookup"><span data-stu-id="16dc7-127">The Memory Optimized Filegroup</span></span>](the-memory-optimized-filegroup.md)  
  
-   [<span data-ttu-id="16dc7-128">メモリ最適化テーブルの持続性</span><span class="sxs-lookup"><span data-stu-id="16dc7-128">Durability for Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
-   [<span data-ttu-id="16dc7-129">メモリ最適化テーブルのチェックポイント操作</span><span class="sxs-lookup"><span data-stu-id="16dc7-129">Checkpoint Operation for Memory-Optimized Tables</span></span>](checkpoint-operation-for-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="16dc7-130">メモリ最適化オブジェクトの持続性の定義</span><span class="sxs-lookup"><span data-stu-id="16dc7-130">Defining Durability for Memory-Optimized Objects</span></span>](defining-durability-for-memory-optimized-objects.md)  
  
-   [<span data-ttu-id="16dc7-131">ディスク ベース テーブル ストレージとメモリ最適化テーブル ストレージの比較</span><span class="sxs-lookup"><span data-stu-id="16dc7-131">Comparing Disk-Based Table Storage to Memory-Optimized Table Storage</span></span>](comparing-disk-based-table-storage-to-memory-optimized-table-storage.md)  
  
-   [<span data-ttu-id="16dc7-132">データ ファイルとデルタ ファイルのペアのマージに関する監視とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="16dc7-132">Monitoring and Troubleshooting Merge for Data and Delta File Pairs</span></span>](../../database-engine/monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs.md)  
  
## <a name="see-also"></a><span data-ttu-id="16dc7-133">参照</span><span class="sxs-lookup"><span data-stu-id="16dc7-133">See Also</span></span>  
 [<span data-ttu-id="16dc7-134">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="16dc7-134">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp-in-memory-optimization.md)  
  
  
