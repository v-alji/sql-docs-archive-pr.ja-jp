---
title: SQL Server プロファイラー-[構成の再生] ([再生オプションの詳細設定]) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.advanced.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: b4eb34f7-3af6-4a44-ba7e-2b8430ec3cd7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 95070d8defb5b7778859ce470aaa8cfc85955ba6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736691"
---
# <a name="sql-server-profiler---replay-configuration-advanced-replay-options"></a><span data-ttu-id="ab6e6-102">[SQL Server Profiler] - [構成の再生] ([再生オプションの詳細設定])</span><span class="sxs-lookup"><span data-stu-id="ab6e6-102">SQL Server Profiler - Replay Configuration (Advanced Replay Options)</span></span>
  <span data-ttu-id="ab6e6-103">**[構成の再生]** ダイアログ ボックスの **[再生オプションの詳細設定]** タブを使用すると、トレース ファイルの再生方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-103">In the **Replay Configuration** dialog box, use the **Advanced Replay Options** tab to specify how to replay a trace file.</span></span>  
  
 <span data-ttu-id="ab6e6-104">このウィンドウを表示するには、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を使用して、再生するイベントを含むトレース ファイルまたはテーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace file or table that contains the appropriate events for replay.</span></span> <span data-ttu-id="ab6e6-105">詳細については、「 [再生を実行するための必要条件](../tools/sql-server-profiler/replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-105">For more information, see [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md).</span></span> <span data-ttu-id="ab6e6-106">トレース ファイルまたはテーブルを開いているときに、 **[再生]** メニューの **[開始]** をクリックして、トレースを再生する SQL Server インスタンスに接続してから、 **[再生オプションの詳細設定]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-106">While the trace file or table is open, on the **Replay** menu, click **Start**, connect to the instance of SQL Server where you want to replay the trace, and then click the **Advanced Replay Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab6e6-107">Options</span><span class="sxs-lookup"><span data-stu-id="ab6e6-107">Options</span></span>  
 <span data-ttu-id="ab6e6-108">**[システム SPID を再生する]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-108">**Replay system SPIDs**</span></span>  
 <span data-ttu-id="ab6e6-109">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] でシステム プロセス識別子 (SPID) を再生するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-109">Specifies whether [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] replays system process identifiers (SPIDs).</span></span>  
  
 <span data-ttu-id="ab6e6-110">**[1 つの SPID のみ再生する]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-110">**Replay one SPID only**</span></span>  
 <span data-ttu-id="ab6e6-111">ソース トレース ファイルで、選択した SPID に関連する操作だけを再生します。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-111">Replays only the activity in the source trace file that is related to the selected SPID.</span></span>  
  
 <span data-ttu-id="ab6e6-112">**[再生する SPID]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-112">**SPID to replay**</span></span>  
 <span data-ttu-id="ab6e6-113">再生する SPID を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-113">Specify which SPID to replay.</span></span>  
  
 <span data-ttu-id="ab6e6-114">**[日時により再生を制限する]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-114">**Limit replay by date and time**</span></span>  
 <span data-ttu-id="ab6e6-115">オンにすると、ソース トレース ファイルの一部だけを再生します。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-115">Check to replay only a portion of the source trace file.</span></span>  
  
 <span data-ttu-id="ab6e6-116">**[開始時刻]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-116">**Start time**</span></span>  
 <span data-ttu-id="ab6e6-117">ソース トレース ファイル内の再生の開始位置を示す日付と時刻です。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-117">Date and time in the source trace file where the replay should start.</span></span>  
  
 <span data-ttu-id="ab6e6-118">**終了時刻**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-118">**End time**</span></span>  
 <span data-ttu-id="ab6e6-119">ソース トレース ファイル内の再生の終了位置を示す日付と時刻です。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-119">Date and time in the source trace file where the replay should stop.</span></span>  
  
 <span data-ttu-id="ab6e6-120">**[ヘルス モニターの待機間隔 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-120">**Health monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="ab6e6-121">再生の待機間隔を秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-121">Specify the wait interval to replay in seconds.</span></span> <span data-ttu-id="ab6e6-122">既定値は 3,600 秒 (1 時間) です。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-122">Default is 3600 seconds (1 hour).</span></span> <span data-ttu-id="ab6e6-123">この設定値によって、プロセスがヘルス モニターにより終了されるまでの実行時間の長さが決まります。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-123">This setting affects the amount of time a process is allowed to run before being terminated by the health monitor.</span></span>  
  
 <span data-ttu-id="ab6e6-124">**[ヘルス モニターのポーリング間隔 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-124">**Health monitor poll interval (sec)**</span></span>  
 <span data-ttu-id="ab6e6-125">再生中のヘルス モニターのポーリング間隔を秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-125">Specify the health monitor poll interval during replay in seconds.</span></span> <span data-ttu-id="ab6e6-126">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-126">Default is 60 seconds.</span></span> <span data-ttu-id="ab6e6-127">ユーザーはこの値を指定することで、終了するプロセスを決定するためにヘルス モニターがポーリングする頻度を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-127">This value allows the user to configure how often the health monitor polls for candidates for termination.</span></span>  
  
 <span data-ttu-id="ab6e6-128">**[SQL Server のブロックされるプロセスの監視を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-128">**Enable SQL Server blocked processes monitor**</span></span>  
 <span data-ttu-id="ab6e6-129">ブロックされるプロセス、またはブロックするプロセスを検索するプロセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-129">Enables a process that searches for blocked or blocking processes.</span></span>  
  
 <span data-ttu-id="ab6e6-130">**[ブロックされるプロセスの監視の待機間隔 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="ab6e6-130">**Blocked processes monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="ab6e6-131">ブロックされるプロセス モニターで、ブロックされるプロセスまたはブロックするプロセスを検索する頻度を設定します。</span><span class="sxs-lookup"><span data-stu-id="ab6e6-131">Configures how often the blocked processes monitor searches for blocked or blocking processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6e6-132">参照</span><span class="sxs-lookup"><span data-stu-id="ab6e6-132">See Also</span></span>  
 <span data-ttu-id="ab6e6-133">[トレーステーブル &#40;SQL Server プロファイラーの再生&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ab6e6-133">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="ab6e6-134">[トレースファイル &#40;SQL Server プロファイラーを再生する&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ab6e6-134">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="ab6e6-135">トレースの再生</span><span class="sxs-lookup"><span data-stu-id="ab6e6-135">Replay Traces</span></span>](../tools/sql-server-profiler/replay-traces.md)  
  
  
