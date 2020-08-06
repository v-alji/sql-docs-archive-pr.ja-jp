---
title: SQL Server プロファイラー-構成の再生 (基本的な再生オプション) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cbf433c3108294909d91f7860136c0755b39b46f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736685"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a><span data-ttu-id="80bda-102">SQL Server Profiler - [構成の再生] ([再生オプションの基本設定])</span><span class="sxs-lookup"><span data-stu-id="80bda-102">SQL Server Profiler - Replay Configuration (Basic Replay Options)</span></span>
  <span data-ttu-id="80bda-103">**[構成の再生]** ダイアログ ボックスの **[再生オプションの基本設定]** ページを使用すると、トレース ファイルまたはテーブルの再生方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="80bda-103">In the **Replay Configuration** dialog box, use the **Basic Replay Options** page to specify how to replay a trace file or table.</span></span>  
  
 <span data-ttu-id="80bda-104">このウィンドウを表示するには、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を使用して、再生するイベントを含むトレース ファイルまたはテーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="80bda-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace file or table that contains the appropriate events for replay.</span></span> <span data-ttu-id="80bda-105">詳細については、「 [再生を実行するための必要条件](../tools/sql-server-profiler/replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80bda-105">For more information, see [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md).</span></span> <span data-ttu-id="80bda-106">トレース ファイルまたはテーブルが開いている状態で、 **[再生]** メニューの **[開始]** をクリックした後、トレースを再生する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="80bda-106">While the trace file or table is open, on the **Replay** menu, click **Start**, and then connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] where you want to replay the trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="80bda-107">Options</span><span class="sxs-lookup"><span data-stu-id="80bda-107">Options</span></span>  
 <span data-ttu-id="80bda-108">**[再生サーバー]**</span><span class="sxs-lookup"><span data-stu-id="80bda-108">**Replay server**</span></span>  
 <span data-ttu-id="80bda-109">再生のために接続する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="80bda-109">Displays the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to for the replay.</span></span>  
  
 <span data-ttu-id="80bda-110">**変更...**</span><span class="sxs-lookup"><span data-stu-id="80bda-110">**Change...**</span></span>  
 <span data-ttu-id="80bda-111">**[サーバーへの接続]** ダイアログ ボックスを表示して、別のサーバーへ接続します。</span><span class="sxs-lookup"><span data-stu-id="80bda-111">Launches the **Connect to Server** dialog box to connect to another server.</span></span>  
  
 <span data-ttu-id="80bda-112">**[ファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="80bda-112">**Save to file**</span></span>  
 <span data-ttu-id="80bda-113">再生結果をファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="80bda-113">Save the replay results to a file.</span></span> [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="80bda-114">により、ファイルを保存する場所を指定するための標準ファイル ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80bda-114">displays the standard file dialog, where you can specify the location to save the file.</span></span>  
  
 <span data-ttu-id="80bda-115">**[テーブルに保存]**</span><span class="sxs-lookup"><span data-stu-id="80bda-115">**Save to table**</span></span>  
 <span data-ttu-id="80bda-116">再生結果をテーブルに保存します。</span><span class="sxs-lookup"><span data-stu-id="80bda-116">Save the replay results to a table.</span></span> [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="80bda-117">により、テーブルを保存する場所を指定するためのテーブル選択ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80bda-117">displays the table selection dialog, where you can specify the location to save the table.</span></span>  
  
 <span data-ttu-id="80bda-118">**[再生スレッドの数]**</span><span class="sxs-lookup"><span data-stu-id="80bda-118">**Number of replay threads**</span></span>  
 <span data-ttu-id="80bda-119">同時に使用する再生スレッドの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="80bda-119">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="80bda-120">値を大きくするほど、再生時にはより多くのリソースが消費されますが、再生が高速になり、同時実行性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="80bda-120">A higher number consumes more resources during replay, but replay is faster and more concurrent.</span></span>  
  
 <span data-ttu-id="80bda-121">**[トレースされた順番にイベントを再生します。このオプションはデバッグを有効にします。]**</span><span class="sxs-lookup"><span data-stu-id="80bda-121">**Replay events in the order they were traced**</span></span>  
 <span data-ttu-id="80bda-122">イベントを順番に再生します。</span><span class="sxs-lookup"><span data-stu-id="80bda-122">Replay events sequentially.</span></span> <span data-ttu-id="80bda-123">このオプションは、デバッグのためにトレースを再生する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="80bda-123">Use this option if you are replaying a trace for debugging.</span></span>  
  
 <span data-ttu-id="80bda-124">**[複数のスレッドを使用してイベントを再生します。このオプションはパフォーマンスを最適にし、デバッグを無効にします。]**</span><span class="sxs-lookup"><span data-stu-id="80bda-124">**Replay events using multiple threads**</span></span>  
 <span data-ttu-id="80bda-125">イベントを同時に再生します。</span><span class="sxs-lookup"><span data-stu-id="80bda-125">Replay events concurrently.</span></span> <span data-ttu-id="80bda-126">このオプションを選択した場合は、イベントを順番に再生するよりも処理が高速になりますが、デバッグができなくなります。</span><span class="sxs-lookup"><span data-stu-id="80bda-126">This option is faster than replaying events sequentially, but disables debugging.</span></span> <span data-ttu-id="80bda-127">イベントは、システム プロセス識別子 (SPID) 内で順序付けられます。</span><span class="sxs-lookup"><span data-stu-id="80bda-127">The events are ordered within their system process identifiers (SPID).</span></span>  
  
 <span data-ttu-id="80bda-128">**[再生結果を表示する]**</span><span class="sxs-lookup"><span data-stu-id="80bda-128">**Display replay results**</span></span>  
 <span data-ttu-id="80bda-129">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]に再生結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="80bda-129">Display replay results in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80bda-130">参照</span><span class="sxs-lookup"><span data-stu-id="80bda-130">See Also</span></span>  
 <span data-ttu-id="80bda-131">[トレーステーブル &#40;SQL Server プロファイラーの再生&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="80bda-131">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="80bda-132">[トレースファイル &#40;SQL Server プロファイラーを再生する&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="80bda-132">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="80bda-133">トレースの再生</span><span class="sxs-lookup"><span data-stu-id="80bda-133">Replay Traces</span></span>](../tools/sql-server-profiler/replay-traces.md)  
  
  
