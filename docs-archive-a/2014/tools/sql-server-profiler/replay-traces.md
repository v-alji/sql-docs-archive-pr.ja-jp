---
title: トレースの再生 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: c485317d1343958f9c430b73d858130097d44d75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737230"
---
# <a name="replay-traces"></a><span data-ttu-id="096a7-102">トレースの再生</span><span class="sxs-lookup"><span data-stu-id="096a7-102">Replay Traces</span></span>
  <span data-ttu-id="096a7-103">再生とは、トレースでキャプチャされたアクティビティを再現する機能です。</span><span class="sxs-lookup"><span data-stu-id="096a7-103">Replay is the ability to reproduce activity that has been captured in a trace.</span></span> <span data-ttu-id="096a7-104">トレースの作成または編集を行うときに、そのトレースをファイルに保存して後で再生できます。</span><span class="sxs-lookup"><span data-stu-id="096a7-104">When you create or edit a trace, you can save the trace to a file and replay it later.</span></span> <span data-ttu-id="096a7-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して、1 つのコンピューターからのトレース アクティビティを再生できます。</span><span class="sxs-lookup"><span data-stu-id="096a7-105">You can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to replay trace activity from a single computer.</span></span> <span data-ttu-id="096a7-106">ワークロードが大きい場合、Distributed Replay Utility を使用して複数のコンピューターからのトレース データを再生できます。</span><span class="sxs-lookup"><span data-stu-id="096a7-106">For large workloads, use the Distributed Replay Utility to replay trace data from multiple computers.</span></span>  
  
 <span data-ttu-id="096a7-107">このセクションでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の再生機能の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="096a7-107">This section describes how to use the replay features of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="096a7-108">Distributed Replay Utility の詳細については、「 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="096a7-108">For more information about the Distributed Replay Utility, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="096a7-109">には、ユーザー接続と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証をシミュレートできるマルチスレッド再生エンジンが備わっています。</span><span class="sxs-lookup"><span data-stu-id="096a7-109">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="096a7-110">再生は、アプリケーションまたはプロセスに関する問題のトラブルシューティングを行う際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="096a7-110">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="096a7-111">問題を特定して修正を実装したら、発生する可能性がある問題を検出したトレースを、修正されたアプリケーションまたはプロセスに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="096a7-111">When you have identified the problem and implemented corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="096a7-112">その後、元のトレースを再生し、結果を比較します。</span><span class="sxs-lookup"><span data-stu-id="096a7-112">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="096a7-113">トレースの再生では、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] の **[再生]** メニューの **[ブレークポイントの設定/解除]** や **[カーソルまで実行]** オプションを使用したデバッグがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="096a7-113">Trace replay supports debugging by using the **Toggle Breakpoint** and the **Run to Cursor** options on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Replay** menu.</span></span> <span data-ttu-id="096a7-114">これらのオプションでは、長いスクリプトを段階的に分析できるように、トレースの再生を短いセグメントに分割できるので、長いスクリプトの分析が特に強化されます。</span><span class="sxs-lookup"><span data-stu-id="096a7-114">These options especially improve the analysis of long scripts because they can break the replay of the trace into short segments so they can be analyzed incrementally.</span></span>  
  
 <span data-ttu-id="096a7-115">トレースの再生に必要な権限については、「 [SQL Server Profiler の実行に必要な権限](permissions-required-to-run-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="096a7-115">For information about the permissions required to replay traces, see [Permissions Required to Run SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="096a7-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="096a7-116">In This Section</span></span>  
  
|<span data-ttu-id="096a7-117">トピック</span><span class="sxs-lookup"><span data-stu-id="096a7-117">Topic</span></span>|<span data-ttu-id="096a7-118">説明</span><span class="sxs-lookup"><span data-stu-id="096a7-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="096a7-119">再生を実行するための必要条件</span><span class="sxs-lookup"><span data-stu-id="096a7-119">Replay Requirements</span></span>](replay-requirements.md)|<span data-ttu-id="096a7-120">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]で再生できるようにトレース定義に含める必要があるイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="096a7-120">Describes the events that must be included in a trace definition so that it can be replayed with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="096a7-121">再生オプション &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="096a7-121">Replay Options &#40;SQL Server Profiler&#41;</span></span>](replay-options-sql-server-profiler.md)|<span data-ttu-id="096a7-122">**の** [構成の再生] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]ダイアログ ボックスで設定できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="096a7-122">Describes the options you can set in the **Replay Configuration** dialog box of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="096a7-123">トレースの再生に関する注意点 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="096a7-123">Considerations for Replaying Traces &#40;SQL Server Profiler&#41;</span></span>](considerations-for-replaying-traces-sql-server-profiler.md)|<span data-ttu-id="096a7-124">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で再生できないトレース イベント、およびトレースの再生によるサーバー パフォーマンスへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="096a7-124">Describes trace events that can not be replayed with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and the effects on server performance of replaying traces.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="096a7-125">参照</span><span class="sxs-lookup"><span data-stu-id="096a7-125">See Also</span></span>  
 [<span data-ttu-id="096a7-126">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="096a7-126">SQL Server Distributed Replay</span></span>](../distributed-replay/sql-server-distributed-replay.md)  
  
  
