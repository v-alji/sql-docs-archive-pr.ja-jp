---
title: ブレークポイントまで再生する (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f33b6862847b042a2613d8c2aa035dd5805493ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737236"
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a><span data-ttu-id="df19a-102">ブレークポイントまでの再生 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="df19a-102">Replay to a Breakpoint (SQL Server Profiler)</span></span>
  <span data-ttu-id="df19a-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、再生するトレース ファイルまたはトレース テーブルにブレークポイントを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="df19a-103">This topic describes how to set breakpoints in a trace file or table that you want to replay by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="df19a-104">トレースの再生を開始する前に、トレース ファイルまたはトレース テーブルにブレークポイントを設定しておくと、特定のイベントが発生したときにトレースの再生を一時停止できます。</span><span class="sxs-lookup"><span data-stu-id="df19a-104">Setting breakpoints in a trace file or table before you start to replay the trace, enables you to pause replay of the trace at specific events.</span></span> <span data-ttu-id="df19a-105">トレース再生中にブレークポイントを使用するとデバッグが簡単になります。これは、長いトレース スクリプトの再生を短いセグメントに分けて小刻みに分析できるからです。</span><span class="sxs-lookup"><span data-stu-id="df19a-105">Using breakpoints while replaying a trace supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.</span></span>  
  
### <a name="to-replay-to-a-breakpoint"></a><span data-ttu-id="df19a-106">ブレークポイントまで再生するには</span><span class="sxs-lookup"><span data-stu-id="df19a-106">To replay to a breakpoint</span></span>  
  
1.  <span data-ttu-id="df19a-107">再生するトレース ファイルまたはトレース テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="df19a-107">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="df19a-108">詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="df19a-108">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="df19a-109">開いたトレース ファイルまたはトレース テーブルに、再生に必要なイベント クラスが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="df19a-109">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="df19a-110">詳細については、「 [再生を実行するための必要条件](replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df19a-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="df19a-111">トレース ウィンドウで、ブレークポイントとして使用するイベントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="df19a-111">In the trace window, click an event that you want to use as a breakpoint.</span></span> <span data-ttu-id="df19a-112">ブレークポイントを設定するには、次の 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="df19a-112">Use one of the following three methods to set a breakpoint:</span></span>  
  
    -   <span data-ttu-id="df19a-113">F9 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="df19a-113">Press F9.</span></span>  
  
    -   <span data-ttu-id="df19a-114">**[再生]** メニューの **[ブレークポイントの設定/解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="df19a-114">On the **Replay** menu, click **Toggle Breakpoint**.</span></span>  
  
    -   <span data-ttu-id="df19a-115">イベントを右クリックし、 **[ブレークポイントの設定/解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="df19a-115">Right-click the event, and then click **Toggle Breakpoint**.</span></span>  
  
     <span data-ttu-id="df19a-116">選択したトレース イベントの横に赤い点が表示され、それがトレースのブレークポイントであることを示します。</span><span class="sxs-lookup"><span data-stu-id="df19a-116">A red bullet appears next to the selected trace event, indicating that it is the trace breakpoint.</span></span>  
  
     <span data-ttu-id="df19a-117">複数のブレークポイントを設定するには、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="df19a-117">Repeat this step to set several breakpoints.</span></span>  
  
3.  <span data-ttu-id="df19a-118">**[再生]** メニューの **[開始]** をクリックし、トレースを再生するサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="df19a-118">On the **Replay** menu, click **Start**, and connect to the server where you want to replay the trace.</span></span>  
  
4.  <span data-ttu-id="df19a-119">**[構成の再生]** ダイアログ ボックスで設定を確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="df19a-119">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
     <span data-ttu-id="df19a-120">再生が開始され、ブレークポイントに達すると一時停止します。</span><span class="sxs-lookup"><span data-stu-id="df19a-120">The replay starts, pausing when the breakpoint is reached.</span></span>  
  
5.  <span data-ttu-id="df19a-121">F5 キーを押して再生を再開し、次のブレークポイントに進みます。</span><span class="sxs-lookup"><span data-stu-id="df19a-121">Press F5 to resume the replay and proceed to the next breakpoint.</span></span>  
  
6.  <span data-ttu-id="df19a-122">手順 5. をトレースの最後まで繰り返します。</span><span class="sxs-lookup"><span data-stu-id="df19a-122">Repeat Step 5 through the end of the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df19a-123">参照</span><span class="sxs-lookup"><span data-stu-id="df19a-123">See Also</span></span>  
 <span data-ttu-id="df19a-124">[カーソルまでの再生 &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="df19a-124">[Replay to a Cursor &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="df19a-125">[トレースの再生](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="df19a-125">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="df19a-126">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="df19a-126">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
