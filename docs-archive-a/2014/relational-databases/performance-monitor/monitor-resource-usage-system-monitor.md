---
title: リソースの利用状況の監視 (システム モニター) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], resource usage
- System Monitor [SQL Server], about Windows System Monitor
- resource usage monitoring [SQL Server]
- System Monitor [SQL Server]
- counters [SQL Server], resource usage subjects
- performance counters [SQL Server], resource usage subjects
- Windows System Monitor [SQL Server], about Windows System Monitor
- monitoring [SQL Server], server resource usage
- monitoring resource usage [SQL Server]
- Windows System Monitor [SQL Server]
- database monitoring [SQL Server], resource usage
- database performance [SQL Server], resource usage
- tuning databases [SQL Server], resource usage
- server performance [SQL Server], resource usage
ms.assetid: f2993a28-0b81-46f2-aec0-6877fe990387
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d691091a41e3161c733902824bf439b6788cc4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645006"
---
# <a name="monitor-resource-usage-system-monitor"></a><span data-ttu-id="b89d8-102">リソースの利用状況の監視 (システム モニター)</span><span class="sxs-lookup"><span data-stu-id="b89d8-102">Monitor Resource Usage (System Monitor)</span></span>
  <span data-ttu-id="b89d8-103">Microsoft Windows サーバー オペレーティング システムを使用している場合は、システム モニター GUI ツールを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のパフォーマンスを測定します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-103">If you are running Microsoft Windows server operating system, use the System Monitor graphical tool to measure the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b89d8-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオブジェクトやパフォーマンス カウンターだけでなく、プロセッサ、メモリ、キャッシュ、スレッド、プロセスなどその他のオブジェクトの動作も確認できます。</span><span class="sxs-lookup"><span data-stu-id="b89d8-104">You can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects, performance counters, and the behavior of other objects, such as processors, memory, cache, threads, and processes.</span></span> <span data-ttu-id="b89d8-105">これらの各オブジェクトには、それに関連したデバイス使用率、キューの長さ、遅延を測定するカウンターと、スループットおよび内部輻輳を表示するインジケーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="b89d8-105">Each of these objects has an associated set of counters that measure device usage, queue lengths, delays, and other indicators of throughput and internal congestion.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b89d8-106">システム モニターは、Windows NT 4.0 以前に使用されていたパフォーマンス モニターの後継ツールです。</span><span class="sxs-lookup"><span data-stu-id="b89d8-106">System Monitor replaced Performance Monitor after Windows NT 4.0.</span></span>  
  
## <a name="benefits-of-system-monitor"></a><span data-ttu-id="b89d8-107">システム モニターの利点</span><span class="sxs-lookup"><span data-stu-id="b89d8-107">Benefits of System Monitor</span></span>  
 <span data-ttu-id="b89d8-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と Windows のパフォーマンスの相関を調べるには、Windows オペレーティング システムと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のカウンターを同時に監視することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b89d8-108">System Monitor can be useful to monitor Windows operating system and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counters at the same time to determine any correlation between the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows.</span></span> <span data-ttu-id="b89d8-109">たとえば、Windows のディスク I/O (入力/出力) カウンターと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Buffer Manager カウンターを同時に監視すると、システム全体の動作を把握できます。</span><span class="sxs-lookup"><span data-stu-id="b89d8-109">For example, monitoring the Windows disk input/output (I/O) counters and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Buffer Manager counters at the same time can reveal the behavior of the entire system.</span></span>  
  
 <span data-ttu-id="b89d8-110">システム モニターを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在の利用状況およびパフォーマンスに関する統計を取ることができます。</span><span class="sxs-lookup"><span data-stu-id="b89d8-110">System Monitor allows you to obtain statistics on current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity and performance.</span></span> <span data-ttu-id="b89d8-111">次に、システム モニターを使用して行うことができる操作を示します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-111">Using System Monitor, you can:</span></span>  
  
-   <span data-ttu-id="b89d8-112">任意の数のコンピューターのデータを同時に表示する。</span><span class="sxs-lookup"><span data-stu-id="b89d8-112">View data simultaneously from any number of computers.</span></span>  
  
-   <span data-ttu-id="b89d8-113">現在の利用状況を反映したグラフを表示して変更し、ユーザーが定義した頻度で更新されるカウンター値を表示する。</span><span class="sxs-lookup"><span data-stu-id="b89d8-113">View and change charts to reflect current activity, and show counter values that are updated at a frequency that the user defines.</span></span>  
  
-   <span data-ttu-id="b89d8-114">さらに操作を行ったり出力したりするために、グラフ、ログ、警告ログ、およびレポートから表計算アプリケーションまたはデータベース アプリケーションにデータをエクスポートする。</span><span class="sxs-lookup"><span data-stu-id="b89d8-114">Export data from charts, logs, alert logs, and reports to spreadsheet or database applications for further manipulation and printing.</span></span>  
  
-   <span data-ttu-id="b89d8-115">警告ログにイベントを記録し、ネットワーク警告によってユーザーに通知できるシステム警告を追加する。</span><span class="sxs-lookup"><span data-stu-id="b89d8-115">Add system alerts that list an event in the alert log and can notify you by issuing a network alert.</span></span>  
  
-   <span data-ttu-id="b89d8-116">カウンター値がユーザー定義値を上回るか下回るようなケースが発生するたびに、または最初に発生したときに、あらかじめ定義しておいたアプリケーションを実行する。</span><span class="sxs-lookup"><span data-stu-id="b89d8-116">Run a predefined application the first time or every time a counter value goes over or under a user-defined value.</span></span>  
  
-   <span data-ttu-id="b89d8-117">複数のコンピューターのさまざまなオブジェクトについてのデータを含むログ ファイルを作成する。</span><span class="sxs-lookup"><span data-stu-id="b89d8-117">Create log files that contain data about various objects from different computers.</span></span>  
  
-   <span data-ttu-id="b89d8-118">既存の複数のログ ファイルから選択した項目を 1 つのファイルに追加していき、長期的なアーカイブを作成する。</span><span class="sxs-lookup"><span data-stu-id="b89d8-118">Append to one file selected sections from other existing log files to form a long-term archive.</span></span>  
  
-   <span data-ttu-id="b89d8-119">現在の利用状況のレポートを表示するか、既存のログ ファイルからレポートを作成する。</span><span class="sxs-lookup"><span data-stu-id="b89d8-119">View current-activity reports, or create reports from existing log files.</span></span>  
  
-   <span data-ttu-id="b89d8-120">グラフ、警告、ログ、またはレポートの個々の設定、あるいはワークスペースの設定全体を再利用するために保存する。</span><span class="sxs-lookup"><span data-stu-id="b89d8-120">Save individual chart, alert, log, or report settings, or the entire workspace setup for reuse.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b89d8-121">Windows NT 4.0 以降では、パフォーマンス モニターがシステム モニターに変わっています。</span><span class="sxs-lookup"><span data-stu-id="b89d8-121">System Monitor replaced the Performance Monitor after Windows NT 4.0.</span></span> <span data-ttu-id="b89d8-122">ここで示したタスクには、システム モニターまたはパフォーマンス モニターのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b89d8-122">You can use either the System Monitor or Performance Monitor to do these tasks.</span></span>  
  
## <a name="system-monitor-performance"></a><span data-ttu-id="b89d8-123">システム モニターのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="b89d8-123">System Monitor Performance</span></span>  
 <span data-ttu-id="b89d8-124">パフォーマンス関連の問題を調査するために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および Microsoft Windows オペレーティング システムを監視するときは、大きく分けて次の 3 点に注目することから始めます。</span><span class="sxs-lookup"><span data-stu-id="b89d8-124">When you monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the Microsoft Windows operating system to investigate performance-related issues, concentrate your initial efforts in three main areas:</span></span>  
  
-   <span data-ttu-id="b89d8-125">ディスク利用状況</span><span class="sxs-lookup"><span data-stu-id="b89d8-125">Disk activity</span></span>  
  
-   <span data-ttu-id="b89d8-126">プロセッサ使用率</span><span class="sxs-lookup"><span data-stu-id="b89d8-126">Processor utilization</span></span>  
  
-   <span data-ttu-id="b89d8-127">メモリ使用量</span><span class="sxs-lookup"><span data-stu-id="b89d8-127">Memory usage</span></span>  
  
 <span data-ttu-id="b89d8-128">システム モニターを実行しているコンピューターを監視すると、コンピューターのパフォーマンスにわずかに影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b89d8-128">Monitoring a computer on which System Monitor is running can affect computer performance slightly.</span></span> <span data-ttu-id="b89d8-129">したがって、システム モニターのデータを他のディスク (またはコンピューター) に記録して監視対象のコンピューターへの影響を減らすか、リモート コンピューターからシステム モニターを実行してください。</span><span class="sxs-lookup"><span data-stu-id="b89d8-129">Therefore, either log the System Monitor data to another disk (or computer) so that it reduces the effect on the computer being monitored, or run System Monitor from a remote computer.</span></span> <span data-ttu-id="b89d8-130">また、監視するカウンターは関心のあるものだけに絞ります。</span><span class="sxs-lookup"><span data-stu-id="b89d8-130">Monitor only the counters in which you are interested.</span></span> <span data-ttu-id="b89d8-131">監視するカウンターが多すぎると、リソース使用量のオーバーヘッドが監視プロセスに上乗せされ、監視対象のコンピューターのパフォーマンスに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="b89d8-131">If you monitor too many counters, resource usage overhead is added to the monitoring process and affects the performance of the computer that is being monitored.</span></span>  
  
## <a name="system-monitor-tasks"></a><span data-ttu-id="b89d8-132">システム モニターのタスク</span><span class="sxs-lookup"><span data-stu-id="b89d8-132">System Monitor Tasks</span></span>  
  
|<span data-ttu-id="b89d8-133">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="b89d8-133">Task Description</span></span>|<span data-ttu-id="b89d8-134">トピック</span><span class="sxs-lookup"><span data-stu-id="b89d8-134">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="b89d8-135">どのような状況でシステム モニターを使用するかについて示し、システム モニター使用時のパフォーマンスのオーバーヘッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-135">Describes when to use System Monitor and discusses performance overhead when you use System Monitor.</span></span>|[<span data-ttu-id="b89d8-136">システム モニターの実行</span><span class="sxs-lookup"><span data-stu-id="b89d8-136">Run System Monitor</span></span>](run-system-monitor.md)|  
|<span data-ttu-id="b89d8-137">ディスク カウンターを監視することで、ディスクの利用状況と、SQL Server コンポーネントによって生成される I/O の量を調べる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-137">Describes how to monitor disk counters to determine disk activity and the amount of I/O generated by their SQL Server components.</span></span>|[<span data-ttu-id="b89d8-138">ディスクの使用量の監視</span><span class="sxs-lookup"><span data-stu-id="b89d8-138">Monitor Disk Usage</span></span>](monitor-disk-usage.md)|  
|<span data-ttu-id="b89d8-139">CPU 使用率が通常の範囲内にあるかどうかを確認するために、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを監視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-139">Describes how to monitor an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to determine whether CPU usage rates are within normal ranges.</span></span>|[<span data-ttu-id="b89d8-140">CPU 使用率の監視</span><span class="sxs-lookup"><span data-stu-id="b89d8-140">Monitor CPU Usage</span></span>](monitor-cpu-usage.md)|  
|<span data-ttu-id="b89d8-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを監視して、メモリ使用率が通常の範囲内であることを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-141">Describes how to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to confirm that memory usage is within typical ranges.</span></span>|[<span data-ttu-id="b89d8-142">メモリ使用率の監視</span><span class="sxs-lookup"><span data-stu-id="b89d8-142">Monitor Memory Usage</span></span>](monitor-memory-usage.md)|  
|<span data-ttu-id="b89d8-143">システム モニターのカウンターがしきい値に達したときに発生する警告を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-143">Describes how to create an alert that is raised when a threshold value for a System Monitor counter has been reached.</span></span>|[<span data-ttu-id="b89d8-144">SQL Server データベース警告の作成</span><span class="sxs-lookup"><span data-stu-id="b89d8-144">Create a SQL Server Database Alert</span></span>](create-a-sql-server-database-alert.md)|  
|<span data-ttu-id="b89d8-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを監視するためのグラフ、警告、ログ、およびレポートを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-145">Describes how to you create charts, alerts, logs, and reports to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="b89d8-146">グラフ、警告、ログ、およびレポートの作成</span><span class="sxs-lookup"><span data-stu-id="b89d8-146">Create Charts, Alerts, Logs, and Reports</span></span>](create-charts-alerts-logs-and-reports.md)|  
|<span data-ttu-id="b89d8-147">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを実行しているコンピューターの利用状況をシステム モニターで監視する際に使用されるオブジェクトとカウンターを示します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-147">Lists objects and counters that System Monitor uses to monitor activity in computers running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="b89d8-148">SQL Server オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="b89d8-148">Use SQL Server Objects</span></span>](use-sql-server-objects.md)|  
|<span data-ttu-id="b89d8-149">システム モニターでインメモリ OLTP のアクティビティを監視する際に使用されるオブジェクトとカウンターを示します。</span><span class="sxs-lookup"><span data-stu-id="b89d8-149">Lists objects and counters that System Monitor uses to monitor In-Memory OLTP activity.</span></span>|[<span data-ttu-id="b89d8-150">XTP &#40;インメモリ OLTP&#41; パフォーマンスカウンター</span><span class="sxs-lookup"><span data-stu-id="b89d8-150">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)|  
  
  
