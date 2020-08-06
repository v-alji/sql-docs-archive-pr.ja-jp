---
title: SQL Server コンポーネントの監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e8f1b16b-ea40-4e12-886c-967ebda4e6e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: baefe9aa1848bc3347a9a5a87c2ab81c382a6717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634477"
---
# <a name="monitor-sql-server-components"></a><span data-ttu-id="7e910-102">SQL Server コンポーネントの監視</span><span class="sxs-lookup"><span data-stu-id="7e910-102">Monitor SQL Server Components</span></span>
  <span data-ttu-id="7e910-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では動的な環境でサービスを提供しているため、監視することは重要です。</span><span class="sxs-lookup"><span data-stu-id="7e910-103">Monitoring is important because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a service in a dynamic environment.</span></span> <span data-ttu-id="7e910-104">アプリケーションのデータは変化します。</span><span class="sxs-lookup"><span data-stu-id="7e910-104">The data in the application changes.</span></span> <span data-ttu-id="7e910-105">ユーザーが必要とするアクセスの種類は変化します。</span><span class="sxs-lookup"><span data-stu-id="7e910-105">The type of access that users require changes.</span></span> <span data-ttu-id="7e910-106">ユーザーの接続方法も変化します。</span><span class="sxs-lookup"><span data-stu-id="7e910-106">The way that users connect changes.</span></span> <span data-ttu-id="7e910-107">また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアクセスするアプリケーションの種類が変わる可能性もあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、手動によるシステム レベルのチューニングを必要最低限に抑えるために、メモリやディスク領域などシステム レベルのリソースが自動的に管理されています。</span><span class="sxs-lookup"><span data-stu-id="7e910-107">The types of applications accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may even change, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically manages system-level resources, such as memory and disk space, to minimize the need for extensive system-level manual tuning.</span></span> <span data-ttu-id="7e910-108">管理者は、SQL Server を監視することにより、パフォーマンスの傾向を特定して、変更が必要かどうかを判断することができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-108">Monitoring lets administrators identify performance trends to determine if changes are necessary.</span></span>  
  
 <span data-ttu-id="7e910-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネントを効果的に監視するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7e910-109">To monitor any component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectively:</span></span>  
  
1.  <span data-ttu-id="7e910-110">監視目的を決定します。</span><span class="sxs-lookup"><span data-stu-id="7e910-110">Determine your monitoring goals.</span></span>  
  
2.  <span data-ttu-id="7e910-111">適切なツールを選択します。</span><span class="sxs-lookup"><span data-stu-id="7e910-111">Select the appropriate tool.</span></span>  
  
3.  <span data-ttu-id="7e910-112">監視するコンポーネントを決定します。</span><span class="sxs-lookup"><span data-stu-id="7e910-112">Identify components to monitor.</span></span>  
  
4.  <span data-ttu-id="7e910-113">これらのコンポーネントに対するメトリックを選択します。</span><span class="sxs-lookup"><span data-stu-id="7e910-113">Select metrics for those components.</span></span>  
  
5.  <span data-ttu-id="7e910-114">サーバーを監視します。</span><span class="sxs-lookup"><span data-stu-id="7e910-114">Monitor the server.</span></span>  
  
6.  <span data-ttu-id="7e910-115">データを分析します。</span><span class="sxs-lookup"><span data-stu-id="7e910-115">Analyze the data.</span></span>  
  
 <span data-ttu-id="7e910-116">これらの手順を順番に説明します。</span><span class="sxs-lookup"><span data-stu-id="7e910-116">These steps are discussed in turn below.</span></span>  
  
## <a name="determine-your-monitoring-goals"></a><span data-ttu-id="7e910-117">監視目的の決定</span><span class="sxs-lookup"><span data-stu-id="7e910-117">Determine Your Monitoring Goals</span></span>  
 <span data-ttu-id="7e910-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を効果的に監視するには、監視する理由を明確にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e910-118">To monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectively you should clearly identify your reason for monitoring.</span></span> <span data-ttu-id="7e910-119">監視する理由には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="7e910-119">Reasons can include the following:</span></span>  
  
-   <span data-ttu-id="7e910-120">パフォーマンスのベースラインを設定する。</span><span class="sxs-lookup"><span data-stu-id="7e910-120">Establish a baseline for performance.</span></span>  
  
-   <span data-ttu-id="7e910-121">長期にわたるパフォーマンスの変化を特定する。</span><span class="sxs-lookup"><span data-stu-id="7e910-121">Identify performance changes over time.</span></span>  
  
-   <span data-ttu-id="7e910-122">具体的なパフォーマンスの問題を診断する。</span><span class="sxs-lookup"><span data-stu-id="7e910-122">Diagnose specific performance problems.</span></span>  
  
-   <span data-ttu-id="7e910-123">最適化するコンポーネントまたはプロセスを特定する。</span><span class="sxs-lookup"><span data-stu-id="7e910-123">Identify components or processes to optimize.</span></span>  
  
-   <span data-ttu-id="7e910-124">いくつかのクライアント アプリケーションのパフォーマンスに対する影響を比較する。</span><span class="sxs-lookup"><span data-stu-id="7e910-124">Compare the effect of different client applications on performance.</span></span>  
  
-   <span data-ttu-id="7e910-125">現在のユーザー利用状況を監査する。</span><span class="sxs-lookup"><span data-stu-id="7e910-125">Audit user activity.</span></span>  
  
-   <span data-ttu-id="7e910-126">サーバーの負荷耐性をテストする。</span><span class="sxs-lookup"><span data-stu-id="7e910-126">Test a server under different loads.</span></span>  
  
-   <span data-ttu-id="7e910-127">データベース アーキテクチャをテストする。</span><span class="sxs-lookup"><span data-stu-id="7e910-127">Test database architecture.</span></span>  
  
-   <span data-ttu-id="7e910-128">メンテナンス スケジュールをテストする。</span><span class="sxs-lookup"><span data-stu-id="7e910-128">Test maintenance schedules.</span></span>  
  
-   <span data-ttu-id="7e910-129">バックアップ プランおよび復元プランをテストする。</span><span class="sxs-lookup"><span data-stu-id="7e910-129">Test backup and restore plans.</span></span>  
  
-   <span data-ttu-id="7e910-130">ハードウェア構成の変更時期を判断する。</span><span class="sxs-lookup"><span data-stu-id="7e910-130">Determining when to modify your hardware configuration.</span></span>  
  
## <a name="select-the-appropriate-tool"></a><span data-ttu-id="7e910-131">適切なツールの選択</span><span class="sxs-lookup"><span data-stu-id="7e910-131">Select the Appropriate Tool</span></span>  
 <span data-ttu-id="7e910-132">監視の理由が決まったら、監視に適切なツールを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e910-132">After determining why you are monitoring, you should select the appropriate tools for that type of monitoring.</span></span> <span data-ttu-id="7e910-133">Windows オペレーティング システムおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、トランザクションを集中的に使用する環境のサーバーを監視できる、ツールの完全なセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7e910-133">The Windows operating system and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provide a complete set of tools to monitor servers in transaction-intensive environments.</span></span> <span data-ttu-id="7e910-134">これらのツールを使用すると、SQL Server データベース エンジンのインスタンスや SQL Server Analysis Services のインスタンスの状態を明確に把握することができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-134">These tools clearly reveal the condition of an instance of the SQL Server Database Engine or an instance of SQL Server Analysis Services.</span></span>  
  
 <span data-ttu-id="7e910-135">Windows で提供されている、サーバーで実行中のアプリケーションを監視するためのツールは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7e910-135">Windows provides the following tools for monitoring applications that are running on a server:</span></span>  
  
-   <span data-ttu-id="7e910-136">システム モニター。このツールを使用すると、メモリ、ディスク、プロセッサの使用状況などのアクティビティに関するデータをリアルタイムに収集して参照できます。</span><span class="sxs-lookup"><span data-stu-id="7e910-136">System Monitor, which lets you collect and view real-time data about activities such as memory, disk, and processor usage</span></span>  
  
-   <span data-ttu-id="7e910-137">パフォーマンス ログと警告</span><span class="sxs-lookup"><span data-stu-id="7e910-137">Performance logs and alerts</span></span>  
  
-   <span data-ttu-id="7e910-138">タスク マネージャー</span><span class="sxs-lookup"><span data-stu-id="7e910-138">Task Manager</span></span>  
  
 <span data-ttu-id="7e910-139">Windows Server または Windows ツールの詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e910-139">For more information about Windows Server or Windows tools, see the Windows documentation.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7e910-140">で提供されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のコンポーネントを監視するためのツールは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7e910-140">provides the following tools for monitoring components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="7e910-141">SQL トレース (SQL Trace)</span><span class="sxs-lookup"><span data-stu-id="7e910-141">SQL Trace</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]  
  
-   <span data-ttu-id="7e910-142">Distributed Replay Utility</span><span class="sxs-lookup"><span data-stu-id="7e910-142">Distributed Replay Utility</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7e910-143">利用状況モニター</span><span class="sxs-lookup"><span data-stu-id="7e910-143">Activity Monitor</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7e910-144">グラフィカルなプラン表示</span><span class="sxs-lookup"><span data-stu-id="7e910-144">Graphical Showplan</span></span>  
  
-   <span data-ttu-id="7e910-145">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="7e910-145">Stored procedures</span></span>  
  
-   <span data-ttu-id="7e910-146">データベース コンソール コマンド (DBCC)</span><span class="sxs-lookup"><span data-stu-id="7e910-146">Database Console Commands (DBCC)</span></span>  
  
-   <span data-ttu-id="7e910-147">組み込み関数</span><span class="sxs-lookup"><span data-stu-id="7e910-147">Built-in functions</span></span>  
  
-   <span data-ttu-id="7e910-148">トレース フラグ</span><span class="sxs-lookup"><span data-stu-id="7e910-148">Trace flags</span></span>  
  
 <span data-ttu-id="7e910-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監視ツールを使用する方法の詳細については、「 [パフォーマンス監視およびチューニング ツール](performance-monitoring-and-tuning-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e910-149">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitoring tools, see [Performance Monitoring and Tuning Tools](performance-monitoring-and-tuning-tools.md).</span></span>  
  
## <a name="identify-the-components-to-monitor"></a><span data-ttu-id="7e910-150">監視するコンポーネントの決定</span><span class="sxs-lookup"><span data-stu-id="7e910-150">Identify the Components to Monitor</span></span>  
 <span data-ttu-id="7e910-151">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス監視の 3 つ目の手順は、監視するコンポーネントを決定することです。</span><span class="sxs-lookup"><span data-stu-id="7e910-151">The third step to monitoring an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is to identify the components that you monitor.</span></span> <span data-ttu-id="7e910-152">たとえば、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してサーバーをトレースする場合、特定のイベントに関するデータを収集するようにトレースを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-152">For example, if you are using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to trace a server you can define the trace to collect data about specific events.</span></span> <span data-ttu-id="7e910-153">また、状況に適用しないイベントをトレースの対象から除外することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e910-153">You can also exclude events that do not apply to your situation.</span></span>  
  
## <a name="select-metrics-for-monitored-components"></a><span data-ttu-id="7e910-154">監視するコンポーネントのメトリックの選択</span><span class="sxs-lookup"><span data-stu-id="7e910-154">Select Metrics for Monitored Components</span></span>  
 <span data-ttu-id="7e910-155">監視するコンポーネントが決定したら、監視するコンポーネントのメトリックを決めます。</span><span class="sxs-lookup"><span data-stu-id="7e910-155">After identifying the components to monitor, determine the metrics for components you monitor.</span></span> <span data-ttu-id="7e910-156">たとえば、トレースに含めるイベントを選択したら、それらのイベントの特定のデータのみを含めるように選択することができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-156">For example, after selecting the events to include in a trace, you can choose to include only specific data about the events.</span></span> <span data-ttu-id="7e910-157">トレースに関連のあるデータのみに制限すると、トレースを実行するのに必要なシステム リソースを最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="7e910-157">Limiting the trace to data that is relevant to the trace minimizes the system resources required to perform the tracing.</span></span>  
  
## <a name="monitor-the-server"></a><span data-ttu-id="7e910-158">サーバーの監視</span><span class="sxs-lookup"><span data-stu-id="7e910-158">Monitor the Server</span></span>  
 <span data-ttu-id="7e910-159">サーバーを監視するには、データを収集するように構成した監視ツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="7e910-159">To monitor the server, run the monitoring tool that you have configured to gather data.</span></span> <span data-ttu-id="7e910-160">たとえば、トレースを定義したら、トレースを実行して、サーバーで発生したイベントのデータを収集できます。</span><span class="sxs-lookup"><span data-stu-id="7e910-160">For example, after a trace is defined, you can run the trace to gather data about events raised in the server.</span></span>  
  
## <a name="analyze-the-data"></a><span data-ttu-id="7e910-161">データの分析</span><span class="sxs-lookup"><span data-stu-id="7e910-161">Analyze the Data</span></span>  
 <span data-ttu-id="7e910-162">トレースが終了したら、データを分析して、監視の目的を達成できたかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7e910-162">After the trace has finished, analyze the data to see if you have achieved your monitoring goal.</span></span> <span data-ttu-id="7e910-163">達成できていない場合は、サーバーの監視に使用したコンポーネントやメトリックを変更します。</span><span class="sxs-lookup"><span data-stu-id="7e910-163">If you have not, modify the components or metrics that you used to monitor the server.</span></span>  
  
 <span data-ttu-id="7e910-164">イベント データのキャプチャおよびその使用に関するプロセスは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7e910-164">The following outlines the process for capturing event data and putting it to use.</span></span>  
  
1.  <span data-ttu-id="7e910-165">フィルターを適用して、収集するイベント データを制限します。</span><span class="sxs-lookup"><span data-stu-id="7e910-165">Apply filters to limit the event data collected.</span></span>  
  
     <span data-ttu-id="7e910-166">イベント データを制限することで、監視シナリオに関連するイベントに集中した処理をシステムが行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="7e910-166">Limiting the event data allows for the system to focus on the events pertinent to the monitoring scenario.</span></span> <span data-ttu-id="7e910-167">たとえば、実行速度の遅いクエリを監視する場合は、アプリケーションによって実行されたクエリの中で、特定のデータベースに対して実行時間が 30 秒以上かかるクエリだけを監視するフィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e910-167">For example, if you want to monitor slow queries, you can use a filter to monitor only those queries issued by the application that take more than 30 seconds to run against a particular database.</span></span> <span data-ttu-id="7e910-168">詳細については、「[トレース フィルターの設定 &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)」および「[トレース内のイベントへのフィルターの適用 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e910-168">For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) and [Filter Events in a Trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="7e910-169">イベントを監視 (キャプチャ) します。</span><span class="sxs-lookup"><span data-stu-id="7e910-169">Monitor (capture) events.</span></span>  
  
     <span data-ttu-id="7e910-170">監視機能を有効にすると、指定したアプリケーション、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、またはオペレーティング システムのデータのキャプチャがすぐに開始されます。</span><span class="sxs-lookup"><span data-stu-id="7e910-170">As soon as it is enabled, active monitoring captures data from the specified application, instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or operating system.</span></span> <span data-ttu-id="7e910-171">たとえば、システム モニターでディスクの使用状況を監視している場合、ディスクの読み取りや書き込みなどのイベント データがキャプチャされ、そのデータが画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e910-171">For example, when disk activity is monitored using System Monitor, monitoring captures event data, such as disk reads and writes, and displays it on the screen.</span></span> <span data-ttu-id="7e910-172">詳細については、「[リソースの利用状況の監視 &#40;システム モニター&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e910-172">For more information, see [Monitor Resource Usage &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md).</span></span>  
  
3.  <span data-ttu-id="7e910-173">キャプチャしたイベント データを保存します。</span><span class="sxs-lookup"><span data-stu-id="7e910-173">Save captured event data.</span></span>  
  
     <span data-ttu-id="7e910-174">キャプチャしたイベント データを保存すると、後で、そのデータを解析したり、Distributed Replay Utility または [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して再生することができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-174">Saving captured event data lets you analyze it later or even replay it using the Distributed Replay Utility or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="7e910-175">キャプチャしたイベント データは、データの生成元ツールで、再度読み込んで解析することができるファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="7e910-175">Captured event data is saved to a file that can be loaded back into the tool that originally created it for analysis.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="7e910-176">では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにイベント データを保存することができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-176">permits event data to be saved to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="7e910-177">パフォーマンス ベースラインを作成する際は、キャプチャしたイベント データを保存することが重要です。</span><span class="sxs-lookup"><span data-stu-id="7e910-177">Saving captured event data is important when you are creating a performance baseline.</span></span> <span data-ttu-id="7e910-178">最近キャプチャしたイベント データを比較して、パフォーマンスが最適かどうかを判断する場合、保存したパフォーマンス ベースライン データを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e910-178">The performance baseline data is saved and used, when comparing recently captured event data, to determine whether performance is optimal.</span></span> <span data-ttu-id="7e910-179">詳細については、「 [SQL Server プロファイラーのテンプレートと権限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e910-179">For more information, see [SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md).</span></span>  
  
4.  <span data-ttu-id="7e910-180">イベントをキャプチャするように指定された設定を含むトレース テンプレートを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e910-180">Create trace templates that contain the settings specified to capture the events.</span></span>  
  
     <span data-ttu-id="7e910-181">トレース テンプレートには、データをキャプチャするときに使用するイベント自体、イベント データ、およびフィルターに関する指定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e910-181">Trace templates include specifications about the events themselves, event data, and filters that are used to capture data.</span></span> <span data-ttu-id="7e910-182">このテンプレートを使用すると、イベント、イベント データ、およびフィルターを再定義することなく、後で特定のイベント セットを監視することができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-182">These templates can be used to monitor a specific set of events later without redefining the events, event data, and filters.</span></span> <span data-ttu-id="7e910-183">たとえば、デッドロックの数やこれらのデッドロックに関係するユーザーの数を頻繁に監視する場合、これらのイベント、イベント データ、およびイベント フィルターを定義するテンプレートを作成して、その定義を保存しておくと、次にデッドロックを監視するときにフィルターを再適用できます。</span><span class="sxs-lookup"><span data-stu-id="7e910-183">For example, if you want to frequently monitor the number of deadlocks, and the users involved in those deadlocks, you can create a template defining those events, event data, and event filters; save the template; and reapply the filter the next time that you want to monitor deadlocks.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="7e910-184">では、この処理にトレース テンプレートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e910-184">uses trace templates for this purpose.</span></span> <span data-ttu-id="7e910-185">詳細については、「[トレース定義の既定値の設定 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)」および「[トレース テンプレートの作成 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e910-185">For more information, see [Set Trace Definition Defaults &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md) and [Create a Trace Template &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md).</span></span>  
  
5.  <span data-ttu-id="7e910-186">キャプチャしたイベント データを分析します。</span><span class="sxs-lookup"><span data-stu-id="7e910-186">Analyze captured event data.</span></span>  
  
     <span data-ttu-id="7e910-187">分析するには、キャプチャして保存したイベント データを、データのキャプチャに使用したアプリケーションで読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7e910-187">To be analyzed, the captured event data is loaded into the application that captured the data.</span></span> <span data-ttu-id="7e910-188">たとえば、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でキャプチャしたトレースは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で再度読み込んで、参照および分析することができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-188">For example, a captured trace from [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can be reloaded into [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] for viewing and analysis.</span></span> <span data-ttu-id="7e910-189">詳細については、「 [SQL Server Profiler を使用したトレースの表示と分析](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7e910-189">For more information, see [View and Analyze Traces with SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="7e910-190">イベント データの分析では、どのようなイベントがなぜ発生したのかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7e910-190">Analyzing event data involves determining what is occurring and why.</span></span> <span data-ttu-id="7e910-191">分析した情報に基づいて、メモリを増設する、インデックスを変更する、Transact-SQL ステートメントやストアド プロシージャのコードの問題を解決するなど、行った分析の種類に応じてパフォーマンスの向上を実現する変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-191">This information lets you make changes that can improve performance, such as adding more memory, changing indexes, correcting coding problems with Transact-SQL statements or stored procedures, and so on, depending on the type of analysis performed.</span></span> <span data-ttu-id="7e910-192">たとえば、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーを使用して、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でキャプチャしたトレースを分析し、その結果に基づいてインデックスの推奨設定を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7e910-192">For example, you can use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor to analyze a captured trace from [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and make index recommendations based on the results.</span></span>  
  
6.  <span data-ttu-id="7e910-193">キャプチャしたイベント データを再生します。</span><span class="sxs-lookup"><span data-stu-id="7e910-193">Replay captured event data.</span></span>  
  
     <span data-ttu-id="7e910-194">イベントの再生では、データをキャプチャしたデータベース環境のテスト コピーを設定して、キャプチャしたイベントを実際のシステムで発生したとおりに再生できます。</span><span class="sxs-lookup"><span data-stu-id="7e910-194">Event replay lets you establish a test copy of the database environment from which the data was captured, and then repeat the captured events as they occurred originally on the real system.</span></span> <span data-ttu-id="7e910-195">この機能は、Distributed Replay Utility または [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]でのみ提供されます。</span><span class="sxs-lookup"><span data-stu-id="7e910-195">This capability is only available with the Distributed Replay Utility or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="7e910-196">イベントの再生速度は、実際に発生したときと同じ速度にすることができます。また、システムに負荷を与えるためにできる限り高速にしたり、多くの場合に行われるように、一度に 1 ステップずつ再生して、各イベントの発生後にシステムを分析することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e910-196">You can replay the events at the same speed as they originally occurred, as fast as possible (to stress the system), or more likely, one step at a time (to analyze the system after each event has occurred).</span></span> <span data-ttu-id="7e910-197">テスト環境で実稼動システムとまったく同じイベントを分析できるので、実稼動システムへの悪影響を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="7e910-197">By analyzing the exact events in a test environment, you can prevent harm to the production system.</span></span> <span data-ttu-id="7e910-198">詳細については、「 [トレースの再生](../../tools/sql-server-profiler/replay-traces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e910-198">For more information, see [Replay Traces](../../tools/sql-server-profiler/replay-traces.md).</span></span>  
  
  
