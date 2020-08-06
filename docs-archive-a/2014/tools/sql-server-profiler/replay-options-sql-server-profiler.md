---
title: 再生オプション (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
- health monitor [SQL Server]
- Replay Configuration dialog box
ms.assetid: 58761a25-a84f-4a90-9c61-97700bc5ad9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 695a1431145813f0a7829626a380e510d0e602e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737242"
---
# <a name="replay-options-sql-server-profiler"></a><span data-ttu-id="e4df0-102">再生オプション (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="e4df0-102">Replay Options (SQL Server Profiler)</span></span>
  <span data-ttu-id="e4df0-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、キャプチャされたトレースを再生するには、 **[構成の再生]** ダイアログ ボックスで、以下の再生オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-103">Before replaying a captured trace with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], specify replay options in the **Replay Configuration** dialog box.</span></span> <span data-ttu-id="e4df0-104">このダイアログ ボックスを表示するには、再生するトレース ファイルまたはトレース テーブルを [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]で開き、 **[再生]** メニューの **[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4df0-104">To launch this dialog box, open the replay trace file or table in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and on the **Replay** menu, click **Start**.</span></span> <span data-ttu-id="e4df0-105">トレースの再生に必要な権限の詳細については、「 [SQL Server Profiler の実行に必要な権限](sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4df0-105">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="e4df0-106">このトピックでは、 **[構成の再生]** ダイアログ ボックスで指定できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-106">This topic describes the options specified with the **Replay Configuration** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4df0-107">(アクティブなコンカレント接続が多数ある、またはスループットが高い) 集中型の OLTP アプリケーションを再生する場合は、Distributed Replay Utility を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e4df0-107">We recommend using the Distributed Replay Utility for replaying an intensive OLTP application (with many active concurrent connections or high throughput).</span></span> <span data-ttu-id="e4df0-108">Distributed Replay Utility では、複数のコンピューターからのトレース データを再生し、ミッションクリティカルなワークロードをより正確にシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="e4df0-108">The Distributed Replay Utility can replay trace data from multiple computers, better simulating a mission-critical workload.</span></span> <span data-ttu-id="e4df0-109">詳細については、「 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4df0-109">For more information, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
## <a name="basic-replay-options"></a><span data-ttu-id="e4df0-110">基本再生オプション</span><span class="sxs-lookup"><span data-stu-id="e4df0-110">Basic Replay Options</span></span>  
 <span data-ttu-id="e4df0-111">**[再生サーバー]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-111">**Replay server**</span></span>  
 <span data-ttu-id="e4df0-112">このサーバーは、トレースを再生する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前になります。</span><span class="sxs-lookup"><span data-stu-id="e4df0-112">The server is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] against which you want to replay the trace.</span></span> <span data-ttu-id="e4df0-113">このサーバーは、「 [再生を実行するための必要条件](replay-requirements.md)」に記載されている再生の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4df0-113">The server must adhere to the replay requirements described in [Replay Requirements](replay-requirements.md)."</span></span>  
  
 <span data-ttu-id="e4df0-114">**[ファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-114">**Save to file**</span></span>  
 <span data-ttu-id="e4df0-115">トレースの再生結果を後で閲覧できるように書き込む出力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-115">The output file where the result of replaying the trace is written for later viewing.</span></span> <span data-ttu-id="e4df0-116">既定では、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] によってトレースの再生結果が画面だけに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4df0-116">By default, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] displays only the results of replaying the trace on the screen.</span></span>  
  
 <span data-ttu-id="e4df0-117">**[テーブルに保存]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-117">**Save to table**</span></span>  
 <span data-ttu-id="e4df0-118">トレースの再生結果を後で閲覧できるように書き込むデータベース テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-118">The database table where the result of replaying the trace is written for later viewing.</span></span>  
  
 <span data-ttu-id="e4df0-119">**[再生スレッドの数]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-119">**Number of replay threads**</span></span>  
 <span data-ttu-id="e4df0-120">同時に使用する再生スレッドの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-120">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="e4df0-121">数が多いと、再生時に消費するリソース量は高くなりますが、再生時間は短縮されます。</span><span class="sxs-lookup"><span data-stu-id="e4df0-121">A higher number consumes more resources during replay, but replay is faster.</span></span> <span data-ttu-id="e4df0-122">複数のスレッドを使用する場合、イベントの順序が完全には維持されません。</span><span class="sxs-lookup"><span data-stu-id="e4df0-122">Event ordering is not fully maintained when multiple threads are used.</span></span>  
  
 <span data-ttu-id="e4df0-123">**[トレースされた順番にイベントを再生します。このオプションはデバッグを有効にします。]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-123">**Replay events in the order they were traced**</span></span>  
 <span data-ttu-id="e4df0-124">トレースごとにステップ実行などのデバッグ方法を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e4df0-124">Allows you to use debugging methods such as stepping through each trace.</span></span> <span data-ttu-id="e4df0-125">このオプションを選択しなかった場合、イベントの再生順序がキャプチャ時の順序になるとは保証されません。</span><span class="sxs-lookup"><span data-stu-id="e4df0-125">If this option is not selected, replay does not guarantee that events are replayed in an order that is consistent with the order in which events were originally captured.</span></span>  
  
 <span data-ttu-id="e4df0-126">**[複数のスレッドを使用してイベントを再生します。このオプションはパフォーマンスを最適にし、デバッグを無効にします。]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-126">**Replay events using multiple threads**</span></span>  
 <span data-ttu-id="e4df0-127">パフォーマンスを最適化し、デバッグを無効にします。</span><span class="sxs-lookup"><span data-stu-id="e4df0-127">Optimizes performance and disables debugging.</span></span> <span data-ttu-id="e4df0-128">イベントは、特定のサーバー プロセス ID (SPID) に対して記録された順序で再生されますが、SPID の順序は保証されません。</span><span class="sxs-lookup"><span data-stu-id="e4df0-128">Events are replayed in the order they were recorded for a particular server process ID (SPID), but ordering of SPIDs is not guaranteed.</span></span>  
  
 <span data-ttu-id="e4df0-129">**[再生結果を表示する]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-129">**Display replay results**</span></span>  
 <span data-ttu-id="e4df0-130">再生結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-130">Display the results of the replay.</span></span> <span data-ttu-id="e4df0-131">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="e4df0-131">This is the default option.</span></span> <span data-ttu-id="e4df0-132">再生するトレースのサイズが非常に大きい場合は、このオプションを無効にしてディスク領域を節約できます。</span><span class="sxs-lookup"><span data-stu-id="e4df0-132">If the trace you are replaying is very large, you may want to disable this to save disk space.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4df0-133">最高のパフォーマンスを得るためには、[複数のスレッドを使用してイベントを再生します。このオプションはパフォーマンスを最適にし、デバッグを無効にします。] を選択し、[再生結果を表示する] を選択しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e4df0-133">For best replay performance, we recommend that you select to replay events using multiple threads, and do not select to display the replay results.</span></span>  
  
## <a name="advanced-replay-options"></a><span data-ttu-id="e4df0-134">再生オプションの詳細設定</span><span class="sxs-lookup"><span data-stu-id="e4df0-134">Advanced Replay Options</span></span>  
 <span data-ttu-id="e4df0-135">**[システム SPID を再生する]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-135">**Replay system SPIDs**</span></span>  
 <span data-ttu-id="e4df0-136">すべての SPID を再生します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-136">Replay all SPIDs.</span></span> <span data-ttu-id="e4df0-137">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="e4df0-137">This is the default option.</span></span>  
  
 <span data-ttu-id="e4df0-138">**[1 つの SPID のみ再生する]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-138">**Replay one SPID only**</span></span>  
 <span data-ttu-id="e4df0-139">一覧から選択した SPID 番号のみを再生します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-139">Replays the SPID number you choose from the list.</span></span>  
  
 <span data-ttu-id="e4df0-140">**[日時により再生を制限する]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-140">**Limit replay by date and time**</span></span>  
 <span data-ttu-id="e4df0-141">**[開始時刻]** および **[終了時刻]** で指定された期間のトレースを再生します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-141">Replays the trace for the specified **Start time** and **End time**.</span></span>  
  
 <span data-ttu-id="e4df0-142">**[ヘルス モニターの待機間隔]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-142">**Health monitor wait interval**</span></span>  
 <span data-ttu-id="e4df0-143">ヘルス モニターにより終了されるまでの、プロセスに実行を許可する時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-143">Sets the amount of time a process is allowed to run before the health monitor terminates it.</span></span>  
  
 <span data-ttu-id="e4df0-144">**[ヘルス モニターのポーリング間隔]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-144">**Health monitor poll interval**</span></span>  
 <span data-ttu-id="e4df0-145">ヘルス モニターがプロセスの終了を確認するためにポーリングする頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-145">Sets how often the health monitor polls candidates for termination.</span></span>  
  
 <span data-ttu-id="e4df0-146">**[SQL Server のブロックされるプロセスの監視を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="e4df0-146">**Enable SQL Server blocked processes monitor**</span></span>  
 <span data-ttu-id="e4df0-147">ブロックされるプロセス モニターが、ブロックされているプロセスまたはブロックしているプロセスを検索する頻度を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-147">Sets how often the blocked processes monitor searches for blocked or blocking processes.</span></span>  
  
## <a name="about-the-health-monitor"></a><span data-ttu-id="e4df0-148">ヘルス モニターについて</span><span class="sxs-lookup"><span data-stu-id="e4df0-148">About the Health Monitor</span></span>  
 <span data-ttu-id="e4df0-149">ヘルス モニターは、トレースの再生に伴うシミュレートされたプロセスを監視するアプリケーション スレッドです。これらのプロセスのうち、再生内でブロックされているプロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="e4df0-149">The health monitor is an application thread that monitors the simulated processes involved in replaying a trace, and ends those processes that are blocked within the replay.</span></span> <span data-ttu-id="e4df0-150">**[再生の構成]** ダイアログ ボックスの **[再生オプションの詳細設定]** タブで、ブロックされているプロセスを終了するまでにヘルス モニターが待機する時間を秒単位で指定できます ( **[ヘルス モニターの待機間隔]** )。</span><span class="sxs-lookup"><span data-stu-id="e4df0-150">In the **Advanced Replay Options** tab of the **Replay Configuration** dialog box, you can specify how long the health monitor should wait in seconds before ending a blocked process (**Health monitor wait interval**).</span></span> <span data-ttu-id="e4df0-151">この間隔が 0 に設定されていると、ヘルス モニターは、再生されているトレース中のブロックしているシミュレートされたプロセスを終了しません。</span><span class="sxs-lookup"><span data-stu-id="e4df0-151">If you set this interval to 0, the health monitor never ends simulated blocking processes in the replaying trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4df0-152">参照</span><span class="sxs-lookup"><span data-stu-id="e4df0-152">See Also</span></span>  
 <span data-ttu-id="e4df0-153">[トレースの再生](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="e4df0-153">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="e4df0-154">[再生を実行するための必要条件](replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="e4df0-154">[Replay Requirements](replay-requirements.md) </span></span>  
 [<span data-ttu-id="e4df0-155">トレースの再生に関する注意点 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="e4df0-155">Considerations for Replaying Traces &#40;SQL Server Profiler&#41;</span></span>](considerations-for-replaying-traces-sql-server-profiler.md)  
  
  
