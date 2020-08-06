---
title: トレースと Windows パフォーマンスログデータの関連付け (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], logs
ms.assetid: e1b3072c-8daf-49a7-9895-c8cccd2adb95
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 34575cf4270d817ecfbb5b2d1824831cc99454fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641225"
---
# <a name="correlate-a-trace-with-windows-performance-log-data-sql-server-profiler"></a><span data-ttu-id="c7f1b-102">トレースと Windows パフォーマンス ログ データの関連付け (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="c7f1b-102">Correlate a Trace with Windows Performance Log Data (SQL Server Profiler)</span></span>
  [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]<span data-ttu-id="c7f1b-103">では、Microsoft Windows システムモニターカウンターをまたはイベントに関連付けることができ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-103">can correlate Microsoft Windows System Monitor counters with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] events.</span></span> <span data-ttu-id="c7f1b-104">Windows システム モニターでは、指定されたカウンターのシステムの利用状況がパフォーマンス ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-104">Windows System Monitor logs system activity for specified counters in performance logs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7f1b-105">異なるバージョンの Windows 間でログを共有する方法の詳細については、このトピックの最後に記載されている手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-105">For information about sharing logs among different versions of Windows, see the procedure at the end of this topic.</span></span>  
  
### <a name="to-correlate-a-trace-with-performance-log-data"></a><span data-ttu-id="c7f1b-106">トレースとパフォーマンス ログ データとを相互に関連付けるには</span><span class="sxs-lookup"><span data-stu-id="c7f1b-106">To correlate a trace with performance log data</span></span>  
  
1.  <span data-ttu-id="c7f1b-107">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]で、保存されているトレース ファイルまたはトレース テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-107">In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], open a saved trace file or trace table.</span></span> <span data-ttu-id="c7f1b-108">イベント データを収集している実行中のトレースを相互に関連付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-108">You cannot correlate a running trace that is still collecting event data.</span></span> <span data-ttu-id="c7f1b-109">システム モニター データとの相関関係の精度を保証するには、 **[StartTime]** データ列と **[EndTime]** データ列の両方がトレースに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-109">For accurate correlation with System Monitor data, the trace must contain both **StartTime** and **EndTime** data columns.</span></span>  
  
2.  <span data-ttu-id="c7f1b-110">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **[ファイル]** メニューで、 **[パフォーマンス データのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-110">On the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **File** menu, click **Import Performance Data**.</span></span>  
  
3.  <span data-ttu-id="c7f1b-111">**[開く]** ダイアログ ボックスで、パフォーマンス ログが含まれているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-111">In the **Open** dialog box, select a file that contains a performance log.</span></span> <span data-ttu-id="c7f1b-112">パフォーマンス ログ データは、トレース データがキャプチャされたのと同じ期間にキャプチャされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-112">The performance log data must have been captured during the same time period in which the trace data is captured.</span></span>  
  
4.  <span data-ttu-id="c7f1b-113">**[パフォーマンス カウンター制限]** ダイアログ ボックスで、トレースと一緒に表示するシステム モニター オブジェクトとカウンターに対応するチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-113">In the **Performance Counters Limit** dialog box, select the check boxes that correspond to the System Monitor objects and counters that you want to display alongside the trace.</span></span> <span data-ttu-id="c7f1b-114">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-114">Click **OK.**</span></span>  
  
5.  <span data-ttu-id="c7f1b-115">トレース イベント ウィンドウでイベントを選択するか、トレース イベント ウィンドウ内のいくつかの隣接する行の間を、方向キーを使用して移動します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-115">Select an event in the trace events window, or navigate through several adjacent rows in the trace events window by using the arrow keys.</span></span> <span data-ttu-id="c7f1b-116">**[システム モニター データ]** ウィンドウ内の赤い縦棒は、選択したトレース イベントと相互に関連しているパフォーマンス ログ データを示します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-116">The vertical red bar in the **System Monitor data** window indicates the performance log data that is correlated with the selected trace event.</span></span>  
  
6.  <span data-ttu-id="c7f1b-117">システム モニターのグラフで、関心のあるポイントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-117">Click a point of interest in the System Monitor graph.</span></span> <span data-ttu-id="c7f1b-118">その時点に最も近い対応するトレース行が選択されます。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-118">The corresponding trace row that is nearest in time is selected.</span></span> <span data-ttu-id="c7f1b-119">時間範囲を拡大するには、システム モニターのグラフでマウス ポインターをクリックしてドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-119">To zoom in on a time range, press and drag the mouse pointer in the System Monitor graph.</span></span>  
  
### <a name="to-create-performance-logs-that-can-be-shared-among-different-versions-of-windows"></a><span data-ttu-id="c7f1b-120">異なるバージョンの Windows 間で共有できるパフォーマンス ログを作成するには</span><span class="sxs-lookup"><span data-stu-id="c7f1b-120">To create performance logs that can be shared among different versions of Windows</span></span>  
  
1.  <span data-ttu-id="c7f1b-121">コントロール パネルで **[管理ツール]** を開き、 **[パフォーマンス]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-121">In Control Panel, open **Administrative Tools**, and then double click **Performance**.</span></span>  
  
2.  <span data-ttu-id="c7f1b-122">**[パフォーマンス]** ダイアログ ボックスで、 **[パフォーマンス ログと警告]** を展開して、 **[カウンター ログ]** を右クリックし、 **[新しいログの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-122">In the **Performance** dialog box, expand **Performance Logs and Alerts**, right-click **Counter Logs**, and then click **New Log Settings**.</span></span>  
  
3.  <span data-ttu-id="c7f1b-123">カウンター ログの名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-123">Type a name for the counter log, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="c7f1b-124">**[全般]** タブで **[カウンターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-124">On the **General** tab, click **Add Counters**.</span></span>  
  
5.  <span data-ttu-id="c7f1b-125">**[パフォーマンス オブジェクト]** ボックスで、監視するパフォーマンス オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-125">In the **Performance object** list, select a performance object you want to monitor.</span></span> <span data-ttu-id="c7f1b-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] パフォーマンス オブジェクトの名前は 、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスの場合は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で始まり、名前付きインスタンスの場合は MSSQL$*instanceName*で始まります。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-126">The names of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] performance objects for default instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] start with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and named instances start with MSSQL$*instanceName*.</span></span>  
  
6.  <span data-ttu-id="c7f1b-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンス、プロセッサ時間やディスク時間などのその他の重要な値から必要なカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-127">Add as many counters as necessary for your [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and other important values, such as processor time and disk time.</span></span>  
  
7.  <span data-ttu-id="c7f1b-128">カウンターの追加を終了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-128">When you have finished adding counters, click **Close**.</span></span>  
  
8.  <span data-ttu-id="c7f1b-129">**[データのサンプル間隔]** の間隔の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-129">Set values for the **Sample data every** interval.</span></span> <span data-ttu-id="c7f1b-130">5 分程度のサンプリング間隔から始めて、必要に応じて間隔を調整します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-130">Start with a modest sampling interval, such as 5 minutes, and then adjust the interval if necessary.</span></span>  
  
9. <span data-ttu-id="c7f1b-131">**[ログ ファイル]** タブで、 **[ログ ファイルの種類]** ボックスの一覧から **[テキスト ファイル (カンマ区切り)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-131">On the **Log Files** tab, choose **TextFile (Comma delimited)** from the **Log file type** list.</span></span> <span data-ttu-id="c7f1b-132">コンマ区切りのテキストのログ ファイルは、異なるバージョンの Windows 間で共有できます。また、Microsoft Excel などのレポート ツールで後から表示できます。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-132">Comma-delimited text log files can be shared among different versions of Windows and can be viewed later in reporting tools such as Microsoft Excel.</span></span>  
  
10. <span data-ttu-id="c7f1b-133">**[スケジュール]** タブで、監視スケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-133">On the **Schedule** tab, specify a monitoring schedule.</span></span>  
  
11. <span data-ttu-id="c7f1b-134">**[OK]** をクリックし、パフォーマンス ログを作成します。</span><span class="sxs-lookup"><span data-stu-id="c7f1b-134">Click **OK** to create the performance log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f1b-135">参照</span><span class="sxs-lookup"><span data-stu-id="c7f1b-135">See Also</span></span>  
 <span data-ttu-id="c7f1b-136">[SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="c7f1b-136">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="c7f1b-137">SQL Server Profiler の起動</span><span class="sxs-lookup"><span data-stu-id="c7f1b-137">Start SQL Server Profiler</span></span>](../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  
