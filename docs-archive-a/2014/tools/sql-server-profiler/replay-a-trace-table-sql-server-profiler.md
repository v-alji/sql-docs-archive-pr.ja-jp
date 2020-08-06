---
title: トレーステーブルを再生する (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 6a0ad817-3d8d-4495-889d-c66a7ef9e8bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: f3c26858fa852686bc3d9ccf4a26d47e04852647
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717115"
---
# <a name="replay-a-trace-table-sql-server-profiler"></a><span data-ttu-id="6fcfb-102">トレース テーブルの再生 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="6fcfb-102">Replay a Trace Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="6fcfb-103">再生は、保存したトレースを開いて再実行する機能です。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-103">Replay is the ability to open a saved trace and replay it again.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="6fcfb-104">には、ユーザー接続と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証をシミュレートできるマルチスレッド再生エンジンが備わっています。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-104">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="6fcfb-105">再生は、アプリケーションまたはプロセスに関する問題のトラブルシューティングを行う際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-105">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="6fcfb-106">問題を特定して修正を実装したら、修正されたアプリケーションまたはプロセスに対して、発生する可能性のある問題を検出したトレースを実行します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-106">When you identify the problem and implement corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="6fcfb-107">その後、元のトレースを再生し、結果を比較します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-107">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="6fcfb-108">再生を有効にするには、監視する他のイベント クラスに加えて、特定のイベント クラスをキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-108">In addition to any other event classes you want to monitor, specific event classes must be captured to enable replay.</span></span> <span data-ttu-id="6fcfb-109">**TSQL_Replay** トレース テンプレートを使用すると、これらのイベントが既定でキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-109">These events are captured by default if you use the **TSQL_Replay** trace template.</span></span> <span data-ttu-id="6fcfb-110">詳細については、「 [再生を実行するための必要条件](replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
### <a name="to-replay-a-trace-table"></a><span data-ttu-id="6fcfb-111">トレース テーブルを再生するには</span><span class="sxs-lookup"><span data-stu-id="6fcfb-111">To replay a trace table</span></span>  
  
1.  <span data-ttu-id="6fcfb-112">再生に必要なイベント クラスが含まれたトレース テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-112">Open a trace table that contains the event classes necessary for replay.</span></span>  
  
2.  <span data-ttu-id="6fcfb-113">**[再生]** メニューの **[開始]** をクリックし、トレースを再生するサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-113">On the **Replay** menu, click **Start**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="6fcfb-114">**[構成の再生]** ダイアログ ボックスの **[再生オプションの基本設定]** タブで、 **[再生サーバー]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-114">In the **Replay Configuration** dialog box, on the **Basic Replay Options** tab, specify **Replay server**.</span></span> <span data-ttu-id="6fcfb-115">**[再生サーバー]** ボックスに表示されているサーバーを変更するには、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-115">Click **Change** to change the server that is displayed in the **Replay server** box.</span></span>  
  
4.  <span data-ttu-id="6fcfb-116">必要に応じて、再生の保存先として次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-116">Optionally, select one of the following destinations in which to save the replay:</span></span>  
  
    -   <span data-ttu-id="6fcfb-117">**[ファイルに保存]** : 再生の保存先となるファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-117">**Save to file,** which specifies a file in which to save the replay.</span></span>  
  
    -   <span data-ttu-id="6fcfb-118">**[テーブルに保存]** : 再生の保存先となるデータベース テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-118">**Save to table**, which specifies a database table in which to save the replay.</span></span>  
  
5.  <span data-ttu-id="6fcfb-119">**[トレースされた順番にイベントを再生します。このオプションはデバッグを有効にします。]** または **[複数のスレッドを使用してイベントを再生します。このオプションはパフォーマンスを最適にし、デバッグを無効にします。]** のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-119">Choose either **Replay the events in the order they were traced**or **Replay events using multiple threads**.</span></span> <span data-ttu-id="6fcfb-120">次の表では、これらの設定の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-120">The following table explains the difference between these settings.</span></span>  
  
    |<span data-ttu-id="6fcfb-121">オプション</span><span class="sxs-lookup"><span data-stu-id="6fcfb-121">Option</span></span>|<span data-ttu-id="6fcfb-122">説明</span><span class="sxs-lookup"><span data-stu-id="6fcfb-122">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="6fcfb-123">**[トレースされた順番にイベントを再生します。このオプションはデバッグを有効にします。]**</span><span class="sxs-lookup"><span data-stu-id="6fcfb-123">**Replay events in the order they were traced**</span></span>|<span data-ttu-id="6fcfb-124">記録された順番にイベントを再生します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-124">Replays events in the order they were recorded.</span></span> <span data-ttu-id="6fcfb-125">このオプションにより、デバッグが有効になります。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-125">This option enables debugging.</span></span>|  
    |<span data-ttu-id="6fcfb-126">**[複数のスレッドを使用してイベントを再生します。このオプションはパフォーマンスを最適にし、デバッグを無効にします。]**</span><span class="sxs-lookup"><span data-stu-id="6fcfb-126">**Replay events using multiple threads**</span></span>|<span data-ttu-id="6fcfb-127">このオプションでは、複数のスレッドを使用して、順序に関係なく各イベントを再生します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-127">This option uses multiple threads to replay each event regardless of the sequence.</span></span> <span data-ttu-id="6fcfb-128">このオプションにより、パフォーマンスが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-128">This option optimizes performance.</span></span>|  
  
6.  <span data-ttu-id="6fcfb-129">**[再生結果を表示する]** チェック ボックスをオンにすると、実行時に再生が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-129">Select **Display replay results** to view the replay as it occurs.</span></span>  
  
7.  <span data-ttu-id="6fcfb-130">必要に応じて、 **[再生オプションの詳細設定]** タブをクリックし、次のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-130">Optionally, click the **Advanced Replay Options**tab to specify the following options:</span></span>  
  
    -   <span data-ttu-id="6fcfb-131">すべてのサーバー プロセス ID (SPID) を再生するには、 **[システム SPID を再生する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-131">To replay all server process IDs (SPIDs), select **Replay system SPIDs**.</span></span>  
  
    -   <span data-ttu-id="6fcfb-132">特定の SPID に属しているプロセスに再生を制限するには、 **[1 つの SPID のみ再生する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-132">To limit the replay to processes belonging to a specific SPID, select **Replay one SPID only**.</span></span> <span data-ttu-id="6fcfb-133">**[再生する SPID]** ボックスには、SPID を入力します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-133">In the **SPID to replay**box, type the SPID.</span></span>  
  
    -   <span data-ttu-id="6fcfb-134">特定の期間に発生したイベントを再生するには、 **[日時により再生を制限する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-134">To replay events that occurred during a specific time period, select **Limit replay by date and time**.</span></span> <span data-ttu-id="6fcfb-135">**[開始時刻]** と **[終了時刻]** の日時を選択し、再生に含める期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-135">Select a date and time for the **Start time**and **End time**to specify the time period to include in the replay.</span></span>  
  
    -   <span data-ttu-id="6fcfb-136">再生中の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によるプロセスの管理方法を制御するには、 **[ヘルス モニター オプション]** を構成します。</span><span class="sxs-lookup"><span data-stu-id="6fcfb-136">To control how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manages processes during replay, configure **Health Monitor Options**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcfb-137">参照</span><span class="sxs-lookup"><span data-stu-id="6fcfb-137">See Also</span></span>  
 <span data-ttu-id="6fcfb-138">[SQL Server Profiler の実行に必要な権限](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6fcfb-138">[Permissions Required to Run SQL Server Profiler](sql-server-profiler.md) </span></span>  
 <span data-ttu-id="6fcfb-139">[トレースの再生](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="6fcfb-139">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="6fcfb-140">[トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6fcfb-140">[Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="6fcfb-141">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="6fcfb-141">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
