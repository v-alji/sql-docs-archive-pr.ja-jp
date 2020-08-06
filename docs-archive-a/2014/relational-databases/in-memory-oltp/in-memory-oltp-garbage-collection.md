---
title: インメモリ OLTP ガベージ コレクション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 23997d3664fb48902d2be08bbb22d2189c832298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739979"
---
# <a name="in-memory-oltp-garbage-collection"></a><span data-ttu-id="1c3e9-102">インメモリ OLTP ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="1c3e9-102">In-Memory OLTP Garbage Collection</span></span>
  <span data-ttu-id="1c3e9-103">アクティブでなくなったトランザクションで削除されたデータ行は古いと見なされます。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-103">A data row is considered stale if it was deleted by a transaction that is no longer active.</span></span> <span data-ttu-id="1c3e9-104">古い行は、ガベージ コレクションに適しています。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-104">A stale row is eligible for garbage collection.</span></span> <span data-ttu-id="1c3e9-105">[!INCLUDE[hek_2](../../includes/hek-2-md.md)]のガベージ コレクションには、次のような特性があります。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-105">The following are characteristics of garbage collection in [!INCLUDE[hek_2](../../includes/hek-2-md.md)]:</span></span>  
  
-   <span data-ttu-id="1c3e9-106">非ブロッキング。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-106">Non-blocking.</span></span> <span data-ttu-id="1c3e9-107">ガベージ コレクションは、ワークロードへの影響を最小限に抑えながら、時間的に分散されます。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-107">Garbage collection is distributed over time with minimal impact on the workload.</span></span>  
  
-   <span data-ttu-id="1c3e9-108">協調。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-108">Cooperative.</span></span> <span data-ttu-id="1c3e9-109">ユーザー トランザクションは、garbage-collection のメイン スレッドと共にガベージ コレクションに参加します。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-109">User transactions participate in garbage collection with main garbage-collection thread.</span></span>  
  
-   <span data-ttu-id="1c3e9-110">効率的。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-110">Efficient.</span></span> <span data-ttu-id="1c3e9-111">ユーザー トランザクションにより、使用されているアクセス パス (インデックス) の古い行とのリンクが解除されます。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-111">User transactions delink stale rows in the access path (the index) being used.</span></span> <span data-ttu-id="1c3e9-112">これにより、行が最終的に削除されるときに必要な作業が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-112">This reduces the work required when the row is finally removed.</span></span>  
  
-   <span data-ttu-id="1c3e9-113">応答性。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-113">Responsive.</span></span> <span data-ttu-id="1c3e9-114">メモリが不足すると積極的にガベージ コレクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-114">Memory pressure leads to aggressive garbage collection.</span></span>  
  
-   <span data-ttu-id="1c3e9-115">スケーラブル。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-115">Scalable.</span></span> <span data-ttu-id="1c3e9-116">コミット後、ユーザー トランザクションによりガベージ コレクションの作業の一部が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-116">After commit, user transactions do part of the work of garbage collection.</span></span> <span data-ttu-id="1c3e9-117">トランザクション アクティビティが多くなるほど、古い行とのリンクを解除するトランザクションが多くなります。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-117">The more transaction activity, the more the transactions delink stale rows.</span></span>  
  
 <span data-ttu-id="1c3e9-118">ガベージ コレクションは、ガベージ コレクションのメイン スレッドによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-118">Garbage collection is controlled by the main garbage collection thread.</span></span> <span data-ttu-id="1c3e9-119">ガベージ コレクションのメイン スレッドは、1 分ごとに、またはコミット済みトランザクションの数が内部しきい値を超えたときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-119">The main garbage collection thread runs every minute, or when the number of committed transactions exceeds an internal threshold.</span></span> <span data-ttu-id="1c3e9-120">ガベージ コレクターのタスクを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-120">The task of the garbage collector is to:</span></span>  
  
-   <span data-ttu-id="1c3e9-121">最も古いアクティブなトランザクションより前に、行セットを削除または更新し、コミットしたトランザクションを特定します。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-121">Identify transactions that have deleted or updated a set of rows and have committed before the oldest active transaction.</span></span>  
  
-   <span data-ttu-id="1c3e9-122">これらの古いトランザクションによって作成された行バージョンを特定します。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-122">Identity row versions created by these old transactions.</span></span>  
  
-   <span data-ttu-id="1c3e9-123">古い行を 16 行ごとの 1 つ以上の単位にグループ化します。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-123">Group old rows into one or more units of 16 rows each.</span></span> <span data-ttu-id="1c3e9-124">その目的は、ガベージ コレクターの作業を小さな単位に分散することです。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-124">This is done to distribute the work of the garbage collector into smaller units.</span></span>  
  
-   <span data-ttu-id="1c3e9-125">各スケジューラに 1 つずつ、これらの作業単位をガベージ コレクション キューに移動します。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-125">Move these work units into the garbage collection queue, one for each scheduler.</span></span> <span data-ttu-id="1c3e9-126">これらのガベージ コレクター DMV の詳細については、「[sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql)」、「[sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql)」、および「[sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-126">Refer to the garbage collector DMVs for the details: [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql), and [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="1c3e9-127">ユーザー トランザクションは、コミット後に、そのトランザクションが実行されているスケジューラに関連付けられたすべてのキュー項目を特定し、メモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-127">After a user transaction commits, it identifies all queued items associated with the scheduler it ran on and then releases the memory.</span></span> <span data-ttu-id="1c3e9-128">スケジューラのガベージ コレクションのキューが空の場合は、現在の NUMA ノードの空でないキューを検索します。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-128">If the garbage collection queue on the scheduler is empty, it searches for any non-empty queue in the current NUMA node.</span></span> <span data-ttu-id="1c3e9-129">トランザクション アクティビティが低レベルで、メモリに負荷がかかっている場合、ガベージ コレクターのメイン スレッドは、任意のキューからガベージ コレクト行にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-129">If there is low transactional activity and there is memory pressure, the main garbage-collection thread can access garbage collect rows from any queue.</span></span> <span data-ttu-id="1c3e9-130">(たとえば) 大量の行を削除したため、トランザクション アクティビティがなく、メモリにも負荷がかかっていない場合は、トランザクション アクティビティが再開されるか、メモリに負荷がかかってくるまで、削除された行のガベージ コレクションは実行されません。</span><span class="sxs-lookup"><span data-stu-id="1c3e9-130">If there is no transactional activity after (for example) deleting a large number of rows and there is no memory pressure, the deleted rows will not be garbage collected until the transactional activity resumes or there is memory pressure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c3e9-131">参照</span><span class="sxs-lookup"><span data-stu-id="1c3e9-131">See Also</span></span>  
 [<span data-ttu-id="1c3e9-132">インメモリ OLTP のメモリ管理</span><span class="sxs-lookup"><span data-stu-id="1c3e9-132">Managing Memory for In-Memory OLTP</span></span>](../../database-engine/managing-memory-for-in-memory-oltp.md)  
  
  
