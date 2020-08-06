---
title: 一度に単一のイベントの再生 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 457bc94d9d8eae470fb60b450d30441c07e676df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737261"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a><span data-ttu-id="eba2e-102">一度に単一のイベントの再生 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="eba2e-102">Replay a Single Event at a Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="eba2e-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、再生トレース ファイルまたはテーブルで一度に単一のイベントを再生する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="eba2e-103">This topic describes how to replay one event at a time in a replay trace file or table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-replay-a-single-event-at-a-time"></a><span data-ttu-id="eba2e-104">一度に単一のイベントを再生するには</span><span class="sxs-lookup"><span data-stu-id="eba2e-104">To replay a single event at a time</span></span>  
  
1.  <span data-ttu-id="eba2e-105">再生するトレース ファイルまたはトレース テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="eba2e-105">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="eba2e-106">詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="eba2e-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="eba2e-107">開いたトレース ファイルまたはトレース テーブルに、再生に必要なイベント クラスが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eba2e-107">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="eba2e-108">詳細については、「 [再生を実行するための必要条件](replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba2e-108">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="eba2e-109">**[再生]** メニューの **[ステップ実行]** をクリックし、トレースを再生するサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="eba2e-109">On the **Replay** menu, click **Step**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="eba2e-110">**[構成の再生]** ダイアログ ボックスで設定を確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eba2e-110">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span> <span data-ttu-id="eba2e-111">**[構成の再生]** ダイアログ ボックスで設定内容を指定する方法の詳細については、「[トレース ファイルの再生 &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルの再生 &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba2e-111">For more information about specifying settings on the **Replay Configuration** dialog box, see [Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) or [Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md).</span></span>  
  
4.  <span data-ttu-id="eba2e-112">最初のイベントを再生するには、 **[構成の再生]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eba2e-112">To replay the first event, click **OK** in the **Replay Configuration** dialog box.</span></span>  
  
5.  <span data-ttu-id="eba2e-113">後続のイベントを再生するには、 **[再生]** メニューの **[ステップ実行]** をクリックするか、F10 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="eba2e-113">To replay subsequent events, on the **Replay** menu, click **Step**, or press F10.</span></span> <span data-ttu-id="eba2e-114">各イベントに対して **[ステップ実行]** をクリックするか、または F10 キーを押す操作を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="eba2e-114">Repeat clicking **Step** or pressing F10 for each event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba2e-115">参照</span><span class="sxs-lookup"><span data-stu-id="eba2e-115">See Also</span></span>  
 <span data-ttu-id="eba2e-116">[トレースの再生](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="eba2e-116">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="eba2e-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="eba2e-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
