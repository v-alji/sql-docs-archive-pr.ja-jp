---
title: トレースの開始 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2b75519631269a1213077a4e295ac73fca1b950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719161"
---
# <a name="start-a-trace"></a><span data-ttu-id="3a7d3-102">トレースの開始</span><span class="sxs-lookup"><span data-stu-id="3a7d3-102">Start a Trace</span></span>
  <span data-ttu-id="3a7d3-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して新しいトレース定義するか、テンプレートを作成したら、新しいトレース定義またはテンプレートを使用してデータのキャプチャを開始、一時停止、または停止することができます。</span><span class="sxs-lookup"><span data-stu-id="3a7d3-103">After you have defined a new trace or created a template by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can start, pause, or stop capturing data by using the new trace definition or template.</span></span>  
  
## <a name="starting-a-trace"></a><span data-ttu-id="3a7d3-104">トレースの開始</span><span class="sxs-lookup"><span data-stu-id="3a7d3-104">Starting a Trace</span></span>  
 <span data-ttu-id="3a7d3-105">定義されているトレース元が [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスである場合、トレースを開始すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、キャプチャしたサーバー イベントを一時的に保持する場所を提供するキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3a7d3-105">When you start a trace and the defined source is an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates a queue that provides a temporary holding place for captured server events.</span></span>  
  
 <span data-ttu-id="3a7d3-106">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して SQL トレースにアクセスすると、トレース ウィンドウが表示されていない場合、トレースの開始時に新しいトレース ウィンドウが表示され、データがすぐにキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="3a7d3-106">When you use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to access SQL Trace, a new trace window opens (if one is not already open) when a trace is started, and data is immediately captured.</span></span>  
  
 <span data-ttu-id="3a7d3-107">[!INCLUDE[tsql](../../includes/tsql-md.md)] システム ストアド プロシージャを使用して SQL トレースにアクセスする際には、データをキャプチャする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動されるたびにトレースを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a7d3-107">When you use [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to access SQL Trace, you must start a trace every time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts for data to be captured.</span></span> <span data-ttu-id="3a7d3-108">トレースの開始後に変更できるのはトレースの名前のみです。</span><span class="sxs-lookup"><span data-stu-id="3a7d3-108">When a trace has been started, you can modify only the name of the trace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a7d3-109">既存のトレースを使用する場合、プロパティを参照できますが、変更できません。</span><span class="sxs-lookup"><span data-stu-id="3a7d3-109">When working with existing traces, you can view the properties, but you cannot modify the properties.</span></span> <span data-ttu-id="3a7d3-110">プロパティを変更するには、トレースを停止または一時停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a7d3-110">To modify the properties, stop or pause the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a7d3-111">参照</span><span class="sxs-lookup"><span data-stu-id="3a7d3-111">See Also</span></span>  
 <span data-ttu-id="3a7d3-112">[サーバー &#40;SQL Server プロファイラーに接続した後、トレースを自動的に開始&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="3a7d3-112">[Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="3a7d3-113">[トレースを一時停止 &#40;SQL Server プロファイラー&#41;](pause-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="3a7d3-113">[Pause a Trace &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="3a7d3-114">[トレース &#40;SQL Server プロファイラーの停止&#41;](stop-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="3a7d3-114">[Stop a Trace &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="3a7d3-115">[トレースウィンドウ &#40;SQL Server プロファイラーをクリア&#41;](clear-a-trace-window-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="3a7d3-115">[Clear a Trace Window &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="3a7d3-116">一時停止または停止したトレースの再開 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="3a7d3-116">Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;</span></span>](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  
