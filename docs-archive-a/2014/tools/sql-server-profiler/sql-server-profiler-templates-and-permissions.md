---
title: SQL Server プロファイラーのテンプレートとアクセス許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f3e3bc180db4e59def5af7eae39d8f177c93268
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632869"
---
# <a name="sql-server-profiler-templates-and-permissions"></a><span data-ttu-id="5505f-102">SQL Server プロファイラーのテンプレートと権限</span><span class="sxs-lookup"><span data-stu-id="5505f-102">SQL Server Profiler Templates and Permissions</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="5505f-103">には、クエリが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部でどのように解決されるのかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5505f-103">shows how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resolves queries internally.</span></span> <span data-ttu-id="5505f-104">これにより管理者は、どのような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたは多次元式がサーバーに送信されるのか、また、そのサーバーではどのようにデータベースやキューブに接続して結果セットを返すのかを正確に知ることができます。</span><span class="sxs-lookup"><span data-stu-id="5505f-104">This allows administrators to see exactly what [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or Multi-Dimensional Expressions are submitted to the server and how the server accesses the database or cube to return result sets.</span></span>  
  
 <span data-ttu-id="5505f-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用すると、以下の操作を行えます。</span><span class="sxs-lookup"><span data-stu-id="5505f-105">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can do the following:</span></span>  
  
-   <span data-ttu-id="5505f-106">再利用可能なテンプレートに基づいたトレースを作成する</span><span class="sxs-lookup"><span data-stu-id="5505f-106">Create a trace that is based on a reusable template</span></span>  
  
-   <span data-ttu-id="5505f-107">トレースを実行しながらトレース結果を監視する</span><span class="sxs-lookup"><span data-stu-id="5505f-107">Watch the trace results as the trace runs</span></span>  
  
-   <span data-ttu-id="5505f-108">トレース結果をテーブルに保存する</span><span class="sxs-lookup"><span data-stu-id="5505f-108">Store the trace results in a table</span></span>  
  
-   <span data-ttu-id="5505f-109">必要に応じて、トレースの開始、停止、一時停止、および変更を行う</span><span class="sxs-lookup"><span data-stu-id="5505f-109">Start, stop, pause, and modify the trace results as necessary</span></span>  
  
-   <span data-ttu-id="5505f-110">トレース結果を再生できます。</span><span class="sxs-lookup"><span data-stu-id="5505f-110">Replay the trace results</span></span>  
  
 <span data-ttu-id="5505f-111">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、関心のあるイベントだけを監視できます。</span><span class="sxs-lookup"><span data-stu-id="5505f-111">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to monitor only the events in which you are interested.</span></span> <span data-ttu-id="5505f-112">トレースが大きくなりすぎた場合は、必要な情報だけをフィルターにより選択できます。その結果、イベント データのサブセットだけが収集されます。</span><span class="sxs-lookup"><span data-stu-id="5505f-112">If traces are becoming too large, you can filter them based on the information you want, so that only a subset of the event data is collected.</span></span> <span data-ttu-id="5505f-113">監視するイベントが多すぎると、サーバーと監視プロセスのオーバーヘッドが増え、トレース ファイルやトレース テーブルが非常に大きくなる可能性があります。特に、監視プロセスを長期にわたって実行する場合はこの可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="5505f-113">Monitoring too many events adds overhead to the server and the monitoring process, and can cause the trace file or trace table to grow very large, especially when the monitoring process takes place over a long period of time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5505f-114">トレース列の値が 1 GB を超えるとエラーを返し、1 GB を超えた値がトレース出力では切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="5505f-114">Trace column values greater than 1 GB return an error and are truncated in the trace output.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5505f-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5505f-115">In This Section</span></span>  
  
|<span data-ttu-id="5505f-116">トピック</span><span class="sxs-lookup"><span data-stu-id="5505f-116">Topic</span></span>|<span data-ttu-id="5505f-117">説明</span><span class="sxs-lookup"><span data-stu-id="5505f-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5505f-118">SQL Server Profiler のテンプレート</span><span class="sxs-lookup"><span data-stu-id="5505f-118">SQL Server Profiler Templates</span></span>](sql-server-profiler-templates.md)|<span data-ttu-id="5505f-119">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]に付属している定義済みのトレース テンプレートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-119">Contains information about the predefined trace templates that ship with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="5505f-120">SQL Server Profiler の実行に必要なアクセス許可</span><span class="sxs-lookup"><span data-stu-id="5505f-120">Permissions Required to Run SQL Server Profiler</span></span>](permissions-required-to-run-sql-server-profiler.md)|<span data-ttu-id="5505f-121">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の実行に必要な権限について説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-121">Contains information about the permissions that are required to run [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="5505f-122">トレースとトレース テンプレートの保存</span><span class="sxs-lookup"><span data-stu-id="5505f-122">Save Traces and Trace Templates</span></span>](save-traces-and-trace-templates.md)|<span data-ttu-id="5505f-123">トレース出力を保存する方法と、トレース定義をテンプレートに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-123">Contains information about saving trace output and about saving trace definitions into a template.</span></span>|  
|[<span data-ttu-id="5505f-124">トレース テンプレートを変更する</span><span class="sxs-lookup"><span data-stu-id="5505f-124">Modify Trace Templates</span></span>](modify-trace-templates.md)|<span data-ttu-id="5505f-125">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してトレース テンプレートを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-125">Contains information about modifying trace templates by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|  
|[<span data-ttu-id="5505f-126">トレースを開始する</span><span class="sxs-lookup"><span data-stu-id="5505f-126">Start a Trace</span></span>](start-a-trace.md)|<span data-ttu-id="5505f-127">トレースを開始、一時停止、または停止するとどのような状態になるのかを説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-127">Contains information about what happens when you start, pause, or stop a trace.</span></span>|  
|[<span data-ttu-id="5505f-128">トレースと Windows パフォーマンス ログ データの関連付け</span><span class="sxs-lookup"><span data-stu-id="5505f-128">Correlate a Trace with Windows Performance Log Data</span></span>](correlate-a-trace-with-windows-performance-log-data.md)|<span data-ttu-id="5505f-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler を使用して、Windows のパフォーマンス ログ データと特定のトレースを相互に関連付ける方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-129">Contains information about correlating Windows performance log data with a trace by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.</span></span>|  
|[<span data-ttu-id="5505f-130">SQL Server Profiler を使用したトレースの表示と分析</span><span class="sxs-lookup"><span data-stu-id="5505f-130">View and Analyze Traces with SQL Server Profiler</span></span>](view-and-analyze-traces-with-sql-server-profiler.md)|<span data-ttu-id="5505f-131">トレースを使用してデータのトラブルシューティングを行う方法、トレースに含まれているオブジェクト名を表示する方法、およびトレースに含まれているイベントを検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-131">Contains information about using traces to troubleshoot data, displaying object names in a trace, and finding events in a trace.</span></span>|  
|[<span data-ttu-id="5505f-132">SQL Server Profiler を使用したデッドロックの分析</span><span class="sxs-lookup"><span data-stu-id="5505f-132">Analyze Deadlocks with SQL Server Profiler</span></span>](analyze-deadlocks-with-sql-server-profiler.md)|<span data-ttu-id="5505f-133">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してデッドロックの原因を特定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-133">Contains information about using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to identify the cause of a deadlock.</span></span>|  
|[<span data-ttu-id="5505f-134">SQL Server Profiler での Showplan 結果を使用したクエリの分析</span><span class="sxs-lookup"><span data-stu-id="5505f-134">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|<span data-ttu-id="5505f-135">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して、Showplan と Showplan Statistics の結果を収集し表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-135">Contains information about using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to collect and display Showplan and Showplan Statistics results.</span></span>|  
|[<span data-ttu-id="5505f-136">SQL Server Profiler でのトレースへのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="5505f-136">Filter Traces with SQL Server Profiler</span></span>](filter-traces-with-sql-server-profiler.md)|<span data-ttu-id="5505f-137">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、データ列にフィルターを設定しトレース出力をフィルター処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5505f-137">Contains information about setting filters on data columns to filter trace output by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="5505f-138">トレースの再生</span><span class="sxs-lookup"><span data-stu-id="5505f-138">Replay Traces</span></span>](replay-traces.md)|<span data-ttu-id="5505f-139">トレースの再生について説明し、トレースの再生を実行するための条件を示します。</span><span class="sxs-lookup"><span data-stu-id="5505f-139">Contains information that explains what replaying a trace means and what is required to replay a trace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5505f-140">参照</span><span class="sxs-lookup"><span data-stu-id="5505f-140">See Also</span></span>  
 <span data-ttu-id="5505f-141">[[SQL Server Profiler]](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5505f-141">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="5505f-142">SQL Server Profiler の起動</span><span class="sxs-lookup"><span data-stu-id="5505f-142">Start SQL Server Profiler</span></span>](start-sql-server-profiler.md)  
  
  
