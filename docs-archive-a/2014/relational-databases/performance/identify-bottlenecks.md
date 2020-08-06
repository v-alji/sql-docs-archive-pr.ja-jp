---
title: ボトルネックの特定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource bottlenecks [SQL Server]
- database monitoring [SQL Server], bottlenecks
- performance [SQL Server], bottlenecks
- tuning databases [SQL Server], bottlenecks
- monitoring server performance [SQL Server], bottlenecks
- monitoring performance [SQL Server], bottlenecks
- database performance [SQL Server], bottlenecks
- server performance [SQL Server], bottlenecks
- bottlenecks [SQL Server]
- identifying bottlenecks [SQL Server]
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e941b3f4a1185177cef007eb6a02a71ae1adece7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713062"
---
# <a name="identify-bottlenecks"></a><span data-ttu-id="05d39-102">ボトルネックの特定</span><span class="sxs-lookup"><span data-stu-id="05d39-102">Identify Bottlenecks</span></span>
  <span data-ttu-id="05d39-103">共有リソースへの同時アクセスは、ボトルネックの原因になります。</span><span class="sxs-lookup"><span data-stu-id="05d39-103">Simultaneous access to shared resources causes bottlenecks.</span></span> <span data-ttu-id="05d39-104">一般に、ボトルネックはあらゆるソフトウェア システムに存在し、避けられないものです。</span><span class="sxs-lookup"><span data-stu-id="05d39-104">In general, bottlenecks are present in every software system and are inevitable.</span></span> <span data-ttu-id="05d39-105">ただし、共有リソースに対する過剰な要求により応答時間が遅くなる場合は、これを特定してチューニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="05d39-105">However, excessive demands on shared resources cause poor response time and must be identified and tuned.</span></span>  
  
 <span data-ttu-id="05d39-106">ボトルネックが発生する原因には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="05d39-106">Causes of bottlenecks include:</span></span>  
  
-   <span data-ttu-id="05d39-107">リソースが不十分なため、コンポーネントの追加やアップグレードが必要な場合。</span><span class="sxs-lookup"><span data-stu-id="05d39-107">Insufficient resources, requiring additional or upgraded components.</span></span>  
  
-   <span data-ttu-id="05d39-108">同じ種類のリソースで負荷が均等に分散されていない (たとえば、1 台のディスクが占有されている) 場合。</span><span class="sxs-lookup"><span data-stu-id="05d39-108">Resources of the same type among which workloads are not distributed evenly; for example, one disk is being monopolized.</span></span>  
  
-   <span data-ttu-id="05d39-109">リソースが誤動作する場合。</span><span class="sxs-lookup"><span data-stu-id="05d39-109">Malfunctioning resources.</span></span>  
  
-   <span data-ttu-id="05d39-110">リソースが不適切に構成されている場合。</span><span class="sxs-lookup"><span data-stu-id="05d39-110">Incorrectly configured resources.</span></span>  
  
## <a name="analyzing-bottlenecks"></a><span data-ttu-id="05d39-111">ボトルネックの分析</span><span class="sxs-lookup"><span data-stu-id="05d39-111">Analyzing Bottlenecks</span></span>  
 <span data-ttu-id="05d39-112">さまざまなイベントに対して過剰な要求が行われている期間は、ボトルネックをチューニングできる指標になります。</span><span class="sxs-lookup"><span data-stu-id="05d39-112">Excessive durations for various events are indicators of bottlenecks that can be tuned.</span></span>  
  
 <span data-ttu-id="05d39-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="05d39-113">For example:</span></span>  
  
-   <span data-ttu-id="05d39-114">他のいくつかのコンポーネントにより、このコンポーネントの負荷が低下しているため、負荷を完了するまでの時間がかかっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="05d39-114">Some other component may prevent the load from reaching this component thereby increasing the time to complete the load.</span></span>  
  
-   <span data-ttu-id="05d39-115">ネットワークの混雑により、クライアントからの要求に時間がかかっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="05d39-115">Client requests may take longer due to network congestion.</span></span>  
  
 <span data-ttu-id="05d39-116">サーバーのパフォーマンスを追跡し、ボトルネックを特定するときに監視する、5 つの主な要素を次に示します。</span><span class="sxs-lookup"><span data-stu-id="05d39-116">Following are five key areas to monitor when tracking server performance to identify bottlenecks.</span></span>  
  
|<span data-ttu-id="05d39-117">ボトルネックになる可能性のある要素</span><span class="sxs-lookup"><span data-stu-id="05d39-117">Possible bottleneck area</span></span>|<span data-ttu-id="05d39-118">サーバーへの影響</span><span class="sxs-lookup"><span data-stu-id="05d39-118">Effects on the server</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="05d39-119">メモリ使用量</span><span class="sxs-lookup"><span data-stu-id="05d39-119">Memory usage</span></span>|<span data-ttu-id="05d39-120">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に割り当てられたメモリまたは使用できるメモリが不足していると、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="05d39-120">Insufficient memory allocated or available to Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] degrades performance.</span></span> <span data-ttu-id="05d39-121">データをデータ キャッシュから直接読み取るのではなく、ディスクから読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="05d39-121">Data must be read from the disk rather than directly from the data cache.</span></span> <span data-ttu-id="05d39-122">Microsoft Windows オペレーティング システムでは、ページが必要になるたびに、ディスクとの間でデータを交換するので、過剰なページングが実行されます。</span><span class="sxs-lookup"><span data-stu-id="05d39-122">Microsoft Windows operating systems perform excessive paging by swapping data to and from the disk as the pages are needed.</span></span>|  
|<span data-ttu-id="05d39-123">CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="05d39-123">CPU utilization</span></span>|<span data-ttu-id="05d39-124">CPU の使用率が一様に高い場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリをチューニングするか、CPU のアップグレードが必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="05d39-124">A chronically high CPU utilization rate may indicate that [!INCLUDE[tsql](../../includes/tsql-md.md)] queries need to be tuned or that a CPU upgrade is needed.</span></span>|  
|<span data-ttu-id="05d39-125">ディスクの入力/出力 (I/O)</span><span class="sxs-lookup"><span data-stu-id="05d39-125">Disk input/output (I/O)</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="05d39-126">クエリについて、インデックスを使用するなどしてチューニングし、不要な I/O を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="05d39-126">queries can be tuned to reduce unnecessary I/O; for example, by employing indexes.</span></span>|  
|<span data-ttu-id="05d39-127">ユーザー接続数</span><span class="sxs-lookup"><span data-stu-id="05d39-127">User connections</span></span>|<span data-ttu-id="05d39-128">サーバーに同時にアクセスしているユーザー数が多すぎるとパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="05d39-128">Too many users may be accessing the server simultaneously causing performance degradation.</span></span>|  
|<span data-ttu-id="05d39-129">ブロッキング ロック</span><span class="sxs-lookup"><span data-stu-id="05d39-129">Blocking locks</span></span>|<span data-ttu-id="05d39-130">アプリケーションが適切にデザインされてないために、コンカレンシーがロックされて妨害され、応答時間が長くなり、トランザクションのスループット率が低下します。</span><span class="sxs-lookup"><span data-stu-id="05d39-130">Incorrectly designed applications can cause locks and hamper concurrency, thus causing longer response times and lower transaction throughput rates.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05d39-131">参照</span><span class="sxs-lookup"><span data-stu-id="05d39-131">See Also</span></span>  
 <span data-ttu-id="05d39-132">[CPU 使用率の監視](../performance-monitor/monitor-cpu-usage.md) </span><span class="sxs-lookup"><span data-stu-id="05d39-132">[Monitor CPU Usage](../performance-monitor/monitor-cpu-usage.md) </span></span>  
 <span data-ttu-id="05d39-133">[ディスクの使用量の監視](../performance-monitor/monitor-disk-usage.md) </span><span class="sxs-lookup"><span data-stu-id="05d39-133">[Monitor Disk Usage](../performance-monitor/monitor-disk-usage.md) </span></span>  
 <span data-ttu-id="05d39-134">[メモリ使用率の監視](../performance-monitor/monitor-memory-usage.md) </span><span class="sxs-lookup"><span data-stu-id="05d39-134">[Monitor Memory Usage](../performance-monitor/monitor-memory-usage.md) </span></span>  
 <span data-ttu-id="05d39-135">[SQL Server: General Statistics オブジェクト](../performance-monitor/sql-server-general-statistics-object.md) </span><span class="sxs-lookup"><span data-stu-id="05d39-135">[SQL Server, General Statistics Object](../performance-monitor/sql-server-general-statistics-object.md) </span></span>  
 [<span data-ttu-id="05d39-136">SQL Server の Locks オブジェクト</span><span class="sxs-lookup"><span data-stu-id="05d39-136">SQL Server, Locks Object</span></span>](../performance-monitor/sql-server-locks-object.md)  
  
  
