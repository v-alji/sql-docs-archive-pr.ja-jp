---
title: レポート サーバーのパフォーマンスの監視 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Reporting Services]
- report servers [Reporting Services], performance
- counters [Reporting Services]
- monitoring performance [Reporting Services]
- SQL Server Reporting Services, performance
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: c1bc13d4-8297-4daf-bb19-4c1e5ba292a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 133dfae978faa4ae8f494cf4a03b282985fae695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711606"
---
# <a name="monitoring-report-server-performance"></a><span data-ttu-id="5200c-102">レポート サーバーのパフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="5200c-102">Monitoring Report Server Performance</span></span>
  <span data-ttu-id="5200c-103">パフォーマンス監視ツールを使用してレポート サーバーのパフォーマンスを監視することにより、サーバーの利用状況の評価、傾向の監視、システムのボトルネックの診断、および現在のシステム構成で十分かどうかを判断するためのデータの収集を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5200c-103">Use performance monitoring tools to monitor report server performance to evaluate server activity, watch trends, diagnose system bottlenecks, and gather data that can help you determine whether the current system configuration is sufficient.</span></span> <span data-ttu-id="5200c-104">サーバーのパフォーマンスを調整するには、レポート サーバー アプリケーション ドメインを再利用する頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="5200c-104">To tune server performance, you can specify how often to recycle the report server application domain.</span></span> <span data-ttu-id="5200c-105">詳細については、「 [レポート サーバー アプリケーションで利用可能なメモリの構成](../report-server/configure-available-memory-for-report-server-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5200c-105">For more information, see [Configure Available Memory for Report Server Applications](../report-server/configure-available-memory-for-report-server-applications.md).</span></span>  
  
## <a name="sources-of-performance-data"></a><span data-ttu-id="5200c-106">パフォーマンス データのソース</span><span class="sxs-lookup"><span data-stu-id="5200c-106">Sources of Performance Data</span></span>  
 <span data-ttu-id="5200c-107">システムの実行状況に関する包括的な情報を取得するには、各種のテクノロジとツールを組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="5200c-107">Use a combination of technologies and tools to get comprehensive information about how the system is performing.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="5200c-108">Windows Server オペレーティング システムでは、以下のツールでパフォーマンス情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5200c-108">Windows Server operating systems provide performance information through the following tools:</span></span>  
  
-   <span data-ttu-id="5200c-109">タスク マネージャー</span><span class="sxs-lookup"><span data-stu-id="5200c-109">Task Manager</span></span>  
  
-   <span data-ttu-id="5200c-110">イベント ビューアー</span><span class="sxs-lookup"><span data-stu-id="5200c-110">Event Viewer</span></span>  
  
-   <span data-ttu-id="5200c-111">パフォーマンス コンソール</span><span class="sxs-lookup"><span data-stu-id="5200c-111">Performance Console</span></span>  
  
 <span data-ttu-id="5200c-112">タスク マネージャーは、コンピューター上で現在実行されているプログラムおよびプロセスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5200c-112">Task Manager provides information about programs and processes running on your computer.</span></span> <span data-ttu-id="5200c-113">タスク マネージャーを使用することで、レポート サーバーのパフォーマンスに関する重要な指標を監視することができます。</span><span class="sxs-lookup"><span data-stu-id="5200c-113">You can use Task Manager to monitor key indicators of your report server's performance.</span></span> <span data-ttu-id="5200c-114">また、実行中のプロセスの利用状況を査定したり、CPU やメモリの使用状況に関するグラフやデータを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="5200c-114">You can also assess the activity of running processes and view graphs and data on CPU and memory usage.</span></span> <span data-ttu-id="5200c-115">タスク マネージャーの使用方法については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows の製品マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5200c-115">For information about using Task Manager, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows product documentation.</span></span>  
  
 <span data-ttu-id="5200c-116">パフォーマンス コンソールとイベント ビューアーは、レポートの処理やリソースの消費に関するログおよび警告を作成する際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5200c-116">You can use Performance Console and Event Viewer to create logs and alerts about report processing and resource consumption.</span></span> <span data-ttu-id="5200c-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]で生成される Windows イベントの詳細については、「 [Windows アプリケーション ログ](windows-application-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5200c-117">For information about Windows events that are generated by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Windows Application Log](windows-application-log.md).</span></span> <span data-ttu-id="5200c-118">パフォーマンス コンソールの詳細については、後の「Windows パフォーマンス カウンター」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5200c-118">For information about Performance Console, see "Windows Performance Counters" later in this topic.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5200c-119">ユーティリティでは、キャッシュおよびセッション管理に使用するレポート サーバー データベースと一時データベースに関する情報も提供されます。</span><span class="sxs-lookup"><span data-stu-id="5200c-119">utilities also provide information about the report server database and temporary databases used for caching and session management.</span></span>  
  
## <a name="windows-performance-counters"></a><span data-ttu-id="5200c-120">Windows パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="5200c-120">Windows Performance Counters</span></span>  
 <span data-ttu-id="5200c-121">個々のパフォーマンス カウンターを監視することで、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="5200c-121">Monitoring specific performance counters enables you to:</span></span>  
  
-   <span data-ttu-id="5200c-122">予測される負荷をサポートするために必要なシステム要件を算出する。</span><span class="sxs-lookup"><span data-stu-id="5200c-122">Estimate system requirements needed to support a predicted workload.</span></span>  
  
-   <span data-ttu-id="5200c-123">構成の変更やアプリケーションのアップグレードの影響を測定するために、パフォーマンスのベースラインを作成する。</span><span class="sxs-lookup"><span data-stu-id="5200c-123">Create a performance baseline to measure effect of configuration changes or application upgrades.</span></span>  
  
-   <span data-ttu-id="5200c-124">実際の負荷、または人為的に生成した負荷の下で、アプリケーションのパフォーマンスを監視する。</span><span class="sxs-lookup"><span data-stu-id="5200c-124">Monitor application performance under certain loads, whether real or artificially generated.</span></span>  
  
-   <span data-ttu-id="5200c-125">ハードウェアのアップグレードがパフォーマンスに所定の効果をもたらしたかどうかを検証する。</span><span class="sxs-lookup"><span data-stu-id="5200c-125">Verify that hardware upgrades have the desired effect on performance.</span></span>  
  
-   <span data-ttu-id="5200c-126">システム構成の変更がパフォーマンスに所定の効果をもたらしたかどうかを検証する。</span><span class="sxs-lookup"><span data-stu-id="5200c-126">Validate changes that were made to the system configuration have the desired effect on performance.</span></span>  
  
## <a name="reporting-services-performance-objects"></a><span data-ttu-id="5200c-127">Reporting Services パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5200c-127">Reporting Services Performance Objects</span></span>  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] <span data-ttu-id="5200c-128">には、次のパフォーマンス オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5200c-128">includes the following performance objects:</span></span>  
  
-   <span data-ttu-id="5200c-129">**MSRS 2011 Web サービス**および `MSRS 2011 SharePoint Mode Web Service` レポートサーバーのパフォーマンスを監視します。</span><span class="sxs-lookup"><span data-stu-id="5200c-129">**MSRS 2011 Web Service** and `MSRS 2011 SharePoint Mode Web Service` to monitor report server performance.</span></span> <span data-ttu-id="5200c-130">これらのパフォーマンス オブジェクトには複数のカウンターが含まれ、主に対話的なレポート表示操作によって開始されるレポート サーバー処理の追跡に使用されます。</span><span class="sxs-lookup"><span data-stu-id="5200c-130">These performance objects include a collection of counters used to track report server processing typically initiated through interactive report viewing operations.</span></span> <span data-ttu-id="5200c-131">これらのカウンターは、 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] がレポート サーバー Web サービスを停止した時点でリセットされます。</span><span class="sxs-lookup"><span data-stu-id="5200c-131">These counters are reset whenever [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>  
  
-   <span data-ttu-id="5200c-132">スケジュール設定した操作、およびレポートの配信を監視するための `MSRS 2011 Windows Service` および `MSRS 2011 Windows Service SharePoint Mode`。</span><span class="sxs-lookup"><span data-stu-id="5200c-132">`MSRS 2011 Windows Service` and `MSRS 2011 Windows Service SharePoint Mode` to monitor scheduled operations and report delivery.</span></span> <span data-ttu-id="5200c-133">これらのパフォーマンス オブジェクトには複数のカウンターが含まれ、スケジュールされた操作を介して開始されるレポート処理の追跡に使用されます。</span><span class="sxs-lookup"><span data-stu-id="5200c-133">These performance objects include a collection of counters used to track report processing that is initiated through scheduled operations.</span></span> <span data-ttu-id="5200c-134">スケジュールされた操作には、サブスクリプションと配信、レポート実行スナップショット、およびレポート履歴が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5200c-134">Scheduled operations include subscription and delivery, report execution snapshots, and report history.</span></span>  
  
-   <span data-ttu-id="5200c-135">HTTP 関連のイベントおよびメモリ管理を監視するための `ReportServer:Service` および `ReportServerSharePoint:Service`。</span><span class="sxs-lookup"><span data-stu-id="5200c-135">`ReportServer:Service` and `ReportServerSharePoint:Service` to monitor HTTP-related events and memory management.</span></span> <span data-ttu-id="5200c-136">これらは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に固有のカウンターです。要求、接続、ログオン試行など、レポート サーバーにおける HTTP 関連のイベントが追跡されます。</span><span class="sxs-lookup"><span data-stu-id="5200c-136">These counters are specific to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and they track HTTP-related events for the report server, such as requests, connections, and logon attempts.</span></span> <span data-ttu-id="5200c-137">このパフォーマンス オブジェクトには、メモリ管理に関連したカウンターも含まれています。</span><span class="sxs-lookup"><span data-stu-id="5200c-137">This performance object also includes counters related to memory management.</span></span>  
  
 <span data-ttu-id="5200c-138">1 台のコンピューターに複数のレポート サーバー インスタンスが存在する場合、インスタンスをまとめて監視することも個別に監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="5200c-138">If you have multiple report server instances on a single computer, you can monitor the instances together or separately.</span></span> <span data-ttu-id="5200c-139">カウンターを追加する場合は、監視対象に含めるインスタンスを選択してください。</span><span class="sxs-lookup"><span data-stu-id="5200c-139">Choose which instances to include when you add a counter.</span></span> <span data-ttu-id="5200c-140">パフォーマンス コンソール (perfmon.msc) の使用およびカウンターの追加に関する詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows の製品マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5200c-140">For more information about using Performance Console (perfmon.msc) and adding counters, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows product documentation.</span></span>  
  
## <a name="other-performance-counters"></a><span data-ttu-id="5200c-141">その他のパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="5200c-141">Other Performance Counters</span></span>  
 <span data-ttu-id="5200c-142">`MSRS 2008 Web Service`、`MSRS 2008 Windows Service`、および `ReportServer:Service` 専用に、カスタムの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] パフォーマンス カウンターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5200c-142">Custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] performance counters are provided only for `MSRS 2008 Web Service`, `MSRS 2008 Windows Service`, and `ReportServer:Service`.</span></span> <span data-ttu-id="5200c-143">次のパフォーマンス オブジェクトにより、レポート サーバーに関する補足的なパフォーマンス監視データが提供されます。</span><span class="sxs-lookup"><span data-stu-id="5200c-143">The following performance objects provide additional performance monitoring data for the report server.</span></span>  
  
|<span data-ttu-id="5200c-144">パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5200c-144">Performance object</span></span>|<span data-ttu-id="5200c-145">メモ</span><span class="sxs-lookup"><span data-stu-id="5200c-145">Notes</span></span>|  
|------------------------|-----------|  
|<span data-ttu-id="5200c-146">`.NET CLR Data` および `.NET CLR Memory`</span><span class="sxs-lookup"><span data-stu-id="5200c-146">`.NET CLR Data` and `.NET CLR Memory`</span></span>|<span data-ttu-id="5200c-147">レポート マネージャーでは、 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] パフォーマンス カウンターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5200c-147">Report Manager uses [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] performance counters.</span></span> <span data-ttu-id="5200c-148">詳細については、MSDN の「Improving .NET Application Performance and Scalability」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5200c-148">For more information, see "Improving .NET Application Performance and Scalability" on MSDN.</span></span>|  
|`Process`|<span data-ttu-id="5200c-149">ReportingServicesService のインスタンスでプロセス ID ごとの稼働時間を追跡するためのパフォーマンス カウンター `Elapsed Time` および `ID Process` を追加します。</span><span class="sxs-lookup"><span data-stu-id="5200c-149">Add the `Elapsed Time` and `ID Process` performance counters for a ReportingServicesService instance to track process uptime by process ID.</span></span>|  
  
## <a name="sharepoint-events"></a><span data-ttu-id="5200c-150">SharePoint のイベント</span><span class="sxs-lookup"><span data-stu-id="5200c-150">SharePoint Events</span></span>  
 <span data-ttu-id="5200c-151">レポート サーバーを SharePoint 統合モードで実行しており、SharePoint 製品を使用するようにレポート環境を構成している場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のパフォーマンス オブジェクトだけでなく、SharePoint のイベントを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="5200c-151">In addition to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] performance objects, you might also want to configure SharePoint events if you are running a report server in SharePoint integrated mode and have configured your reporting environment to use a SharePoint product.</span></span> <span data-ttu-id="5200c-152">このセクションでは、「SharePoint 統合モードにおけるレポート サーバーのイベント」を基に、SharePoint と統合されたレポート環境で役立てることのできる診断イベントについて確認します。</span><span class="sxs-lookup"><span data-stu-id="5200c-152">In this section, use the Events for a Report Server in SharePoint Integrated Mode to review diagnostic events that might provide useful information if your reporting environment is integrated with SharePoint.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5200c-153">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5200c-153">In This Section</span></span>  
 [<span data-ttu-id="5200c-154">MSRS 2014 Web サービスおよび MSRS 2014 Windows Service のパフォーマンスオブジェクトのパフォーマンスカウンター &#40;ネイティブモード&#41;</span><span class="sxs-lookup"><span data-stu-id="5200c-154">Performance Counters for the MSRS 2014 Web Service and MSRS 2014 Windows Service Performance Objects &#40;Native Mode&#41;</span></span>](performance-counters-msrs-2011-web-service-performance-objects.md)  
 <span data-ttu-id="5200c-155">レポート サーバー Web サービスで使用するパフォーマンス カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5200c-155">Describes the performance counters used by the Report Server Web service.</span></span>  
  
 [<span data-ttu-id="5200c-156">MSRS 2014 Web Service SharePoint モードおよび MSRS 2014 Windows Service SharePoint mode パフォーマンスオブジェクトのパフォーマンスカウンター &#40;SharePoint モード&#41;</span><span class="sxs-lookup"><span data-stu-id="5200c-156">Performance Counters for the MSRS 2014 Web Service SharePoint Mode and MSRS 2014 Windows Service SharePoint Mode Performance Objects &#40;SharePoint Mode&#41;</span></span>](performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)  
 <span data-ttu-id="5200c-157">レポート サーバー Windows サービスで使用するパフォーマンス カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5200c-157">Describes the performance counters used by the Report Server Windows service.</span></span>  
  
 [<span data-ttu-id="5200c-158">ReportServer:Service と ReportServerSharePoint:Service パフォーマンス オブジェクトのパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="5200c-158">Performance Counters for the ReportServer:Service  and ReportServerSharePoint:Service Performance Objects</span></span>](performance-counters-reportserver-service-performance-objects.md)  
 <span data-ttu-id="5200c-159">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]における HTTP およびメモリに関連したパフォーマンス カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5200c-159">Describes the HTTP-related and memory-related performance counters in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5200c-160">SharePoint 統合モードにおけるレポート サーバーのイベント</span><span class="sxs-lookup"><span data-stu-id="5200c-160">Events for a Report Server in SharePoint Integrated Mode</span></span>  
 <span data-ttu-id="5200c-161">レポート環境を SharePoint 製品と組み合わせて実行している場合に役立てることのできる診断イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5200c-161">Describes the useful diagnostic events to log when you run a reporting environment with a SharePoint product.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5200c-162">参照</span><span class="sxs-lookup"><span data-stu-id="5200c-162">See Also</span></span>  
 <span data-ttu-id="5200c-163">[レポート サーバー アプリケーションで利用可能なメモリの構成](../report-server/configure-available-memory-for-report-server-applications.md) </span><span class="sxs-lookup"><span data-stu-id="5200c-163">[Configure Available Memory for Report Server Applications](../report-server/configure-available-memory-for-report-server-applications.md) </span></span>  
 <span data-ttu-id="5200c-164">[Reporting Services レポート サーバー (ネイティブ モード)](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="5200c-164">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 [<span data-ttu-id="5200c-165">Reporting Services ツール</span><span class="sxs-lookup"><span data-stu-id="5200c-165">Reporting Services Tools</span></span>](../tools/reporting-services-tools.md)  
  
  
