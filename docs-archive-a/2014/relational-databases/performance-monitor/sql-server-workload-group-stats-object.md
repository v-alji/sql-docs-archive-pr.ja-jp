---
title: SQL Server:Workload Group Stats オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Workload Group Stats object
- 'SQLServer: Workload Group Stats'
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fb363803c562b305687e78e1315f1c4255041b1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634479"
---
# <a name="sql-server-workload-group-stats-object"></a><span data-ttu-id="873a2-102">SQLServer:Workload Group Stats オブジェクト</span><span class="sxs-lookup"><span data-stu-id="873a2-102">SQL Server, Workload Group Stats Object</span></span>
  <span data-ttu-id="873a2-103">SQLServer:Workload Group Stats オブジェクトには、リソース ガバナーのワークロード グループ統計に関する情報を報告するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="873a2-103">The SQLServer:Workload Group Stats object contains performance counters that report information about Resource Governor workload group statistics.</span></span>  
  
 <span data-ttu-id="873a2-104">アクティブな各ワークロード グループでは、リソース ガバナー ワークロード グループ名と同じインスタンス名を持つ SQLServer:Workload Group Stats パフォーマンス オブジェクトのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="873a2-104">Each active workload group creates an instance of the SQLServer:Workload Group Stats performance object that has the same instance name as the Resource Governor workload group name.</span></span> <span data-ttu-id="873a2-105">次の表では、このインスタンスでサポートされるカウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="873a2-105">The following table describes counters supported on this instance.</span></span>  
  
|<span data-ttu-id="873a2-106">カウンター名</span><span class="sxs-lookup"><span data-stu-id="873a2-106">Counter name</span></span>|<span data-ttu-id="873a2-107">説明</span><span class="sxs-lookup"><span data-stu-id="873a2-107">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="873a2-108">Queued requests</span><span class="sxs-lookup"><span data-stu-id="873a2-108">Queued requests</span></span>|<span data-ttu-id="873a2-109">現在キューに置かれている処理待ちの要求の数。</span><span class="sxs-lookup"><span data-stu-id="873a2-109">The current number of queued requests that is waiting to be picked up.</span></span> <span data-ttu-id="873a2-110">この数は、GROUP_MAX_REQUESTS の上限に達してからスロットルが行われると、0 以外の値になることがあります。</span><span class="sxs-lookup"><span data-stu-id="873a2-110">This count can be non-zero if throttling occurs after the GROUP_MAX_REQUESTS limit is reached.</span></span>|  
|<span data-ttu-id="873a2-111">Active requests</span><span class="sxs-lookup"><span data-stu-id="873a2-111">Active requests</span></span>|<span data-ttu-id="873a2-112">このワークロード グループの現在実行中の要求数。</span><span class="sxs-lookup"><span data-stu-id="873a2-112">The number of requests that are currently running in this workload group.</span></span> <span data-ttu-id="873a2-113">グループ ID でフィルター選択した sys.dm_exec_requests の行数と同じ数になります。</span><span class="sxs-lookup"><span data-stu-id="873a2-113">This should be equivalent to the count of rows from sys.dm_exec_requests filtered by group ID.</span></span>|  
|<span data-ttu-id="873a2-114">Requests completed/sec</span><span class="sxs-lookup"><span data-stu-id="873a2-114">Requests completed/sec</span></span>|<span data-ttu-id="873a2-115">このワークロード グループの完了した要求の数。</span><span class="sxs-lookup"><span data-stu-id="873a2-115">The number of requests that have completed in this workload group.</span></span> <span data-ttu-id="873a2-116">この数は累積数です。</span><span class="sxs-lookup"><span data-stu-id="873a2-116">This number is cumulative.</span></span>|  
|<span data-ttu-id="873a2-117">CPU usage %</span><span class="sxs-lookup"><span data-stu-id="873a2-117">CPU usage %</span></span>|<span data-ttu-id="873a2-118">このワークロード グループのすべての要求による CPU 帯域幅の使用率。コンピューターを基準に測定され、システムのすべての CPU を基準に正規化されます。</span><span class="sxs-lookup"><span data-stu-id="873a2-118">The CPU bandwidth usage by all requests in this workload group measured relative to the computer and normalized to all the CPUs on the system.</span></span> <span data-ttu-id="873a2-119">この値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスで使用できる CPU の量によって変化します。</span><span class="sxs-lookup"><span data-stu-id="873a2-119">This value will change as the amount of CPU available to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process changes.</span></span> <span data-ttu-id="873a2-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスに割り当てられた内容を基準にして正規化されるのではありません。</span><span class="sxs-lookup"><span data-stu-id="873a2-120">It is not normalized to what the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process receives.</span></span>|  
|<span data-ttu-id="873a2-121">Max request CPU time (ms)</span><span class="sxs-lookup"><span data-stu-id="873a2-121">Max request CPU time (ms)</span></span>|<span data-ttu-id="873a2-122">ワークロード グループの現在実行中の要求で使用される最大 CPU 時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="873a2-122">The maximum CPU time, in milliseconds, used by a request currently running in the workload group.</span></span>|  
|<span data-ttu-id="873a2-123">Blocked requests</span><span class="sxs-lookup"><span data-stu-id="873a2-123">Blocked requests</span></span>|<span data-ttu-id="873a2-124">ワークロード グループのブロックされた要求の現在の数。</span><span class="sxs-lookup"><span data-stu-id="873a2-124">The current number of blocked requests in the workload group.</span></span> <span data-ttu-id="873a2-125">この数値を使用して負荷の特性を判別できます。</span><span class="sxs-lookup"><span data-stu-id="873a2-125">This can be used to determine workload characteristics.</span></span>|  
|<span data-ttu-id="873a2-126">Reduced memory grants/sec</span><span class="sxs-lookup"><span data-stu-id="873a2-126">Reduced memory grants/sec</span></span>|<span data-ttu-id="873a2-127">最適な量に満たないメモリ許可を取得している 1 秒間のクエリ数。</span><span class="sxs-lookup"><span data-stu-id="873a2-127">The number of queries that are getting less than ideal amount of memory grants per second.</span></span>|  
|<span data-ttu-id="873a2-128">Max request memory grant (KB)</span><span class="sxs-lookup"><span data-stu-id="873a2-128">Max request memory grant (KB)</span></span>|<span data-ttu-id="873a2-129">1 つのクエリに対するメモリ許可の最大値 (KB 単位)。</span><span class="sxs-lookup"><span data-stu-id="873a2-129">The maximum value of memory grant, in kilobytes (KB), for a query.</span></span>|  
|<span data-ttu-id="873a2-130">Query optimizations/sec</span><span class="sxs-lookup"><span data-stu-id="873a2-130">Query optimizations/sec</span></span>|<span data-ttu-id="873a2-131">1 秒間にこのワークロード グループで行われたクエリの最適化の数。</span><span class="sxs-lookup"><span data-stu-id="873a2-131">The number of query optimizations that have happened in this workload group per second.</span></span> <span data-ttu-id="873a2-132">この数値を使用して負荷の特性を判別できます。</span><span class="sxs-lookup"><span data-stu-id="873a2-132">This can be used to determine workload characteristics.</span></span>|  
|<span data-ttu-id="873a2-133">Suboptimal plans/sec</span><span class="sxs-lookup"><span data-stu-id="873a2-133">Suboptimal plans/sec</span></span>|<span data-ttu-id="873a2-134">1 秒間にこのワークロード グループで生成された最適ではないプランの数。</span><span class="sxs-lookup"><span data-stu-id="873a2-134">The number of suboptimal plans that are generated in this workload group per second.</span></span>|  
|<span data-ttu-id="873a2-135">Active parallel threads</span><span class="sxs-lookup"><span data-stu-id="873a2-135">Active parallel threads</span></span>|<span data-ttu-id="873a2-136">並列スレッド使用の現在の数。</span><span class="sxs-lookup"><span data-stu-id="873a2-136">The current count of parallel threads usage.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="873a2-137">参照</span><span class="sxs-lookup"><span data-stu-id="873a2-137">See Also</span></span>  
 <span data-ttu-id="873a2-138">[リソースの利用状況の監視 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="873a2-138">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="873a2-139">[SQLServer:Resource Pool Stats オブジェクト](sql-server-resource-pool-stats-object.md) </span><span class="sxs-lookup"><span data-stu-id="873a2-139">[SQL Server, Resource Pool Stats Object](sql-server-resource-pool-stats-object.md) </span></span>  
 [<span data-ttu-id="873a2-140">リソース ガバナー</span><span class="sxs-lookup"><span data-stu-id="873a2-140">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
