---
title: カーソルまで再生する (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfc5ba06b60100bf8ecc8d04909371021a5b00e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737231"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a><span data-ttu-id="99ee7-102">カーソルまでの再生 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="99ee7-102">Replay to a Cursor (SQL Server Profiler)</span></span>
  <span data-ttu-id="99ee7-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、カーソルに到達したときに一時停止するトレース ファイルまたはトレース テーブルの再生方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99ee7-103">This topic describes how to replay trace files or tables that pause when a cursor is reached by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="99ee7-104">カーソル到達時点でトレースを一時停止することでデバッグがサポートされることになります。これは、長いトレース スクリプトの再生を、順番に分析できる短いセグメントに分割できるためです。</span><span class="sxs-lookup"><span data-stu-id="99ee7-104">Pausing traces at cursors supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.</span></span>  
  
### <a name="to-replay-to-the-cursor"></a><span data-ttu-id="99ee7-105">カーソルまで再生するには</span><span class="sxs-lookup"><span data-stu-id="99ee7-105">To replay to the cursor</span></span>  
  
1.  <span data-ttu-id="99ee7-106">再生するトレース ファイルまたはトレース テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="99ee7-106">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="99ee7-107">詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="99ee7-107">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="99ee7-108">開いたトレース ファイルまたはトレース テーブルに、再生に必要なイベント クラスが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="99ee7-108">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="99ee7-109">詳細については、「 [再生を実行するための必要条件](replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99ee7-109">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="99ee7-110">トレース ウィンドウで、イベントを 1 つクリックします。</span><span class="sxs-lookup"><span data-stu-id="99ee7-110">In the trace window, click an event.</span></span>  
  
3.  <span data-ttu-id="99ee7-111">**[再生]** メニューの **[カーソルまで実行]** をクリックし、トレースを再生するサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="99ee7-111">On the **Replay** menu, click **Run to Cursor**, and then connect to the server where you want to replay the trace.</span></span>  
  
4.  <span data-ttu-id="99ee7-112">**[構成の再生]** ダイアログ ボックスで設定を確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99ee7-112">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
     <span data-ttu-id="99ee7-113">再生が開始され、最初のカーソルに到達した時点で一時停止されます。</span><span class="sxs-lookup"><span data-stu-id="99ee7-113">The replay starts, pausing when the first cursor is reached.</span></span>  
  
5.  <span data-ttu-id="99ee7-114">F5 キーを押してトレースを再開します。</span><span class="sxs-lookup"><span data-stu-id="99ee7-114">Press F5 to resume the trace.</span></span>  
  
6.  <span data-ttu-id="99ee7-115">手順 5. をトレースの最後まで繰り返します。</span><span class="sxs-lookup"><span data-stu-id="99ee7-115">Repeat Step 5 through the end of the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ee7-116">参照</span><span class="sxs-lookup"><span data-stu-id="99ee7-116">See Also</span></span>  
 <span data-ttu-id="99ee7-117">[ブレークポイントまでの再生 &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="99ee7-117">[Replay to a Breakpoint &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="99ee7-118">[トレースの再生](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="99ee7-118">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="99ee7-119">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="99ee7-119">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
