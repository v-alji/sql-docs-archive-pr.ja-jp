---
title: SQL Server プロファイラーツール-[オプション] ([全般オプション] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.generaloptions.f1
helpviewer_keywords:
- General Options dialog box
ms.assetid: a888246d-ccfe-415f-bbdc-d6adafac250a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fad4d3529482835367898276a973bd7c8827b553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642947"
---
# <a name="sql-server-profiler---tools-options-general-options-page"></a><span data-ttu-id="ce77a-102">SQL Server プロファイラー-[オプション] ([全般オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="ce77a-102">SQL Server Profiler - Tools-Options (General Options Page)</span></span>
  <span data-ttu-id="ce77a-103">**[全般オプション]** ダイアログ ボックスを使用すると、以下のオプションを確認または指定できます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-103">Use the **General Options** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ce77a-104">Options</span><span class="sxs-lookup"><span data-stu-id="ce77a-104">Options</span></span>  
  
### <a name="display-options"></a><span data-ttu-id="ce77a-105">[表示オプション]</span><span class="sxs-lookup"><span data-stu-id="ce77a-105">Display Options</span></span>  
 <span data-ttu-id="ce77a-106">**フォント名**</span><span class="sxs-lookup"><span data-stu-id="ce77a-106">**Font name**</span></span>  
 <span data-ttu-id="ce77a-107">トレースの実行中にトレース結果グリッドで使用されるフォントの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-107">Displays the name of the font used in the trace results grid during traces.</span></span>  
  
 <span data-ttu-id="ce77a-108">**フォント サイズ**</span><span class="sxs-lookup"><span data-stu-id="ce77a-108">**Font size**</span></span>  
 <span data-ttu-id="ce77a-109">トレースの実行中にトレース結果グリッドで使用されるフォントのサイズを表示します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-109">Displays the size of the font used in the trace results grid during traces.</span></span>  
  
 <span data-ttu-id="ce77a-110">**[フォントの選択]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-110">**Choose Font**</span></span>  
 <span data-ttu-id="ce77a-111">フォント設定を変更するためのダイアログを開きます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-111">Opens a dialog to change the font settings.</span></span>  
  
 <span data-ttu-id="ce77a-112">**[日時の値の表示に地域別設定を使用する]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-112">**Use regional settings to display date and time values**</span></span>  
 <span data-ttu-id="ce77a-113">使用するコンピューター用に構成された地域の設定で日時の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-113">Displays date and time values in regional settings configured for your computer.</span></span> <span data-ttu-id="ce77a-114">このオプションを選択しない場合、日時の値は Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]が使用する固定形式 (ミリ秒を含む) で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-114">If you do not select this option, the date and time values are displayed in the fixed format used by Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], which includes milliseconds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce77a-115">このチェック ボックスのオン/オフを切り替えることで、 **[StartTime]** や **[EndTime]** などの時間列の表示形式が変更されます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-115">Toggling this checkbox changes the time columns display format such as **StartTime** and **EndTime**.</span></span> <span data-ttu-id="ce77a-116">ただし、言語イベントまたはリモート プロシージャ コール (RPC) 内の **DateTime** 値のパラメーターは変更されません。</span><span class="sxs-lookup"><span data-stu-id="ce77a-116">However, it does not change the **DateTime** value parameters inside the language events or remote procedure calls (RPCs).</span></span>  
  
 <span data-ttu-id="ce77a-117">**[実行時間列の値をマイクロ秒で表示する]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-117">**Show values in Duration column in microseconds**</span></span>  
 <span data-ttu-id="ce77a-118">トレースの **[実行時間]** データ列の値をマイクロ秒で表示します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-118">Displays the values in microseconds in the **Duration** data column of traces.</span></span> <span data-ttu-id="ce77a-119">既定では、 **[実行時間]** 列の値はミリ秒で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-119">By default, the **Duration** column displays values in milliseconds.</span></span>  
  
### <a name="tracing-options"></a><span data-ttu-id="ce77a-120">[トレース オプション]</span><span class="sxs-lookup"><span data-stu-id="ce77a-120">Tracing Options</span></span>  
 <span data-ttu-id="ce77a-121">**[接続の確立直後にトレースを開始する]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-121">**Start tracing immediately after making connection**</span></span>  
 <span data-ttu-id="ce77a-122">接続の確立直後に既定のテンプレートを使用してトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-122">Begin a trace using the default template as soon as a connection is made.</span></span>  
  
 <span data-ttu-id="ce77a-123">**[プロバイダーのバージョンが変更されたときに、トレース定義を更新する]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-123">**Update trace definition when provider version changes**</span></span>  
 <span data-ttu-id="ce77a-124">プロバイダーが更新されたときに、最新のトレース定義を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に適用します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-124">Apply the most current trace definition to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] when the provider is updated.</span></span> <span data-ttu-id="ce77a-125">既定ではオンになっていません。</span><span class="sxs-lookup"><span data-stu-id="ce77a-125">This item is not checked by default.</span></span> <span data-ttu-id="ce77a-126">このオプションをオンにすると、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] は、サーバーでトレース定義を問い合わせるクエリを実行し、トレース定義があればファイルをディスクに再作成します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-126">This forces [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to query the server for the trace definition and re-create, if one exists, the file on disk.</span></span>  
  
### <a name="file-rollover-options"></a><span data-ttu-id="ce77a-127">[ファイルのロールオーバー オプション]</span><span class="sxs-lookup"><span data-stu-id="ce77a-127">File Rollover Options</span></span>  
 <span data-ttu-id="ce77a-128">**[確認せずにすべてのロールオーバー ファイルを順に読み込む]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-128">**Load all rollover files in sequence without prompting**</span></span>  
 <span data-ttu-id="ce77a-129">トレース ファイルが開かれるとロールオーバー ファイルを自動的に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-129">Load rollover files automatically when a trace file is opened.</span></span> <span data-ttu-id="ce77a-130">トレースの実行中に複数のファイルが作成されたときに、このオプションがオンになっている場合、すべてのロールオーバー ファイルが自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-130">If more than one file was created while tracing, selecting this option automatically loads all rollover files.</span></span>  
  
 <span data-ttu-id="ce77a-131">**[ロールオーバー ファイルを読み込む前に確認する]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-131">**Prompt before loading rollover files**</span></span>  
 <span data-ttu-id="ce77a-132">トレース ファイルを開いたときに、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] はロールオーバー ファイルを追加するかどうかをユーザーに確認してから追加します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-132">Have [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] prompt you before adding a rollover file when a trace file is opened.</span></span>  
  
 <span data-ttu-id="ce77a-133">**[後続のロールオーバー ファイルを読み込まない]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-133">**Never load subsequent rollover files**</span></span>  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="ce77a-134">は、トレース ファイルを開いたときに、後続のロールオーバー ファイルを読み込みません。</span><span class="sxs-lookup"><span data-stu-id="ce77a-134">never loads subsequent rollover files when a trace file is opened.</span></span>  
  
### <a name="replay-options"></a><span data-ttu-id="ce77a-135">[再生オプション]</span><span class="sxs-lookup"><span data-stu-id="ce77a-135">Replay Options</span></span>  
 <span data-ttu-id="ce77a-136">**[再生スレッドの既定の数]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-136">**Default number of replay threads**</span></span>  
 <span data-ttu-id="ce77a-137">同時に使用する再生スレッドの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-137">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="ce77a-138">使用する数を多くすると再生中のリソースも多くなりますが、再生のコンカレンシー数が増えます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-138">A higher number consumes more resources during replay, but increases replay concurrency.</span></span>  
  
 <span data-ttu-id="ce77a-139">**[ヘルス モニターの既定の待機間隔 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-139">**Default health monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="ce77a-140">再生の待機間隔を秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-140">Specify the wait interval to replay in seconds.</span></span> <span data-ttu-id="ce77a-141">既定値は 3,600 秒 (1 時間) です。</span><span class="sxs-lookup"><span data-stu-id="ce77a-141">Default is 3600 seconds (1 hour).</span></span> <span data-ttu-id="ce77a-142">この設定は、ヘルス モニターでスレッドが終了するまでに、このスレッドを実行できる時間の長さに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-142">This setting affects the amount of time a thread is allowed to run before being terminated by the health monitor.</span></span>  
  
 <span data-ttu-id="ce77a-143">**[ヘルス モニターの既定のポーリング間隔 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="ce77a-143">**Default health monitor poll interval (sec)**</span></span>  
 <span data-ttu-id="ce77a-144">再生中のヘルス モニターのポーリング間隔を秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="ce77a-144">Specify the health monitor poll interval during replay in seconds.</span></span> <span data-ttu-id="ce77a-145">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="ce77a-145">Default is 60 seconds.</span></span> <span data-ttu-id="ce77a-146">ユーザーはこの値を指定することで、終了するプロセスを決定するためにヘルス モニターがポーリングする頻度を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ce77a-146">This value allows the user to configure how often the health monitor polls for candidates for termination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce77a-147">参照</span><span class="sxs-lookup"><span data-stu-id="ce77a-147">See Also</span></span>  
 <span data-ttu-id="ce77a-148">[サーバー &#40;SQL Server プロファイラーに接続した後、トレースを自動的に開始&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ce77a-148">[Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="ce77a-149">[トレース表示の既定値 &#40;SQL Server プロファイラー&#41;を設定します](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ce77a-149">[Set Trace Display Defaults &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="ce77a-150">[トレーステーブル &#40;SQL Server プロファイラーの再生&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ce77a-150">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="ce77a-151">[トレースファイル &#40;SQL Server プロファイラーを再生する&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ce77a-151">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="ce77a-152">[トレースの再生](../tools/sql-server-profiler/replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="ce77a-152">[Replay Traces](../tools/sql-server-profiler/replay-traces.md) </span></span>  
 <span data-ttu-id="ce77a-153">[グローバルトレースオプション &#40;SQL Server プロファイラー&#41;を設定します](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ce77a-153">[Set Global Trace Options &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="ce77a-154">[SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="ce77a-154">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="ce77a-155">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ce77a-155">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
