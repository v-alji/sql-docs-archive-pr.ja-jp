---
title: SQL トレースの最適化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], traces
- SQL Trace, performance
- traces [SQL Server], performance
- performance [SQL Server], trace
ms.assetid: 50944218-925f-4576-aec8-4379846d7681
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 831875218423bdb9106d7d84995af1e788da44db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632296"
---
# <a name="optimize-sql-trace"></a><span data-ttu-id="fb247-102">SQL トレースの最適化</span><span class="sxs-lookup"><span data-stu-id="fb247-102">Optimize SQL Trace</span></span>
  <span data-ttu-id="fb247-103">SQL トレースを実行すると、データを収集するためにシステム リソースが使用されるのでパフォーマンス コストが発生しますが、このコストはさまざまな方法で最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="fb247-103">Although running SQL Trace incurs a performance cost because it uses system resources to gather data, you can do many things to minimize it.</span></span> <span data-ttu-id="fb247-104">トレースによって発生するパフォーマンス コストを最小限に抑えるには、次のようにしてください。</span><span class="sxs-lookup"><span data-stu-id="fb247-104">To minimize the performance cost incurred by a trace, try the following:</span></span>  
  
-   <span data-ttu-id="fb247-105">トレースの実行には、コマンド プロンプトを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="fb247-105">Consider using the command prompt to run traces.</span></span> <span data-ttu-id="fb247-106">グラフィカル ユーザー インターフェイスを使用すると、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="fb247-106">Using a graphical user interface hinders performance.</span></span> <span data-ttu-id="fb247-107">詳細については、「[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb247-107">For more information, see [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql).</span></span>  
  
-   <span data-ttu-id="fb247-108">頻繁に発生するイベントは含めないようにします。</span><span class="sxs-lookup"><span data-stu-id="fb247-108">Avoid including events that occur frequently.</span></span> <span data-ttu-id="fb247-109">可能な場合は、特定のイベント クラスやフィルターを使用してトレースの範囲を狭くします。</span><span class="sxs-lookup"><span data-stu-id="fb247-109">If possible, narrow your trace by means of specific event classes and filters.</span></span> <span data-ttu-id="fb247-110">収集するトレース イベントが少ないほど、トレースをサポートするために必要なシステム リソースも少なくて済みます。</span><span class="sxs-lookup"><span data-stu-id="fb247-110">If fewer trace events are gathered, fewer system resources are required to support tracing.</span></span>  
  
-   <span data-ttu-id="fb247-111">関連性のあるデータを提供するイベントだけを収集するようにトレースの焦点を絞ります。</span><span class="sxs-lookup"><span data-stu-id="fb247-111">Focus the trace to collect only events that provide relevant data.</span></span> <span data-ttu-id="fb247-112">たとえば、トレースでデッドロックを特定する場合は、 **Lock:Acquired** イベント クラスではなく **Lock:Deadlock** イベント クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="fb247-112">For example, if your trace is to identify deadlocks, include the **Lock:Deadlock** event class, but not the **Lock:Acquired** event class.</span></span> <span data-ttu-id="fb247-113">これらのイベント クラスを両方含めると、取得したすべてのロックをトレースしなければならないため、実行コストが倍増します。</span><span class="sxs-lookup"><span data-stu-id="fb247-113">If you include both event classes, the trace has to respond to every lock that is acquired, and your execution cost is doubled.</span></span>  
  
-   <span data-ttu-id="fb247-114">重複データは収集しないようにします。</span><span class="sxs-lookup"><span data-stu-id="fb247-114">Avoid collecting duplicate data.</span></span> <span data-ttu-id="fb247-115">たとえば、 **SQL:BatchStarted** と **SQL:BatchCompleted**を収集する場合は、 **SQL:BatchStarted** イベント クラスのテキスト データだけを収集することにより、結果セットのサイズを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="fb247-115">For example, if you collect **SQL:BatchStarted** and the **SQL:BatchCompleted**, you can minimize the size of the results set by collecting text data for the **SQL:BatchStarted** event class only.</span></span>  
  
-   <span data-ttu-id="fb247-116">トレース定義でフィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="fb247-116">Use filters in the trace definition.</span></span> <span data-ttu-id="fb247-117">たとえば、アドホック クエリの際のパフォーマンスの低下を報告しているユーザーがいる場合は、 **LoginName**に対するフィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb247-117">For example, if you know that a certain user is reporting slow performance during ad hoc queries, create a filter on **LoginName**.</span></span> <span data-ttu-id="fb247-118">**LoginName** がこのユーザー名と一致するイベントだけを含めるように、フィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="fb247-118">Set the filter to include only events where the **LoginName** matches that user name.</span></span>  
  
 <span data-ttu-id="fb247-119">パフォーマンスに重大な影響を与えるイベントのトレースを実行する必要がある場合は、次のいずれかの方法に従って、サーバーのパフォーマンスに対する影響を最小限に抑えるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="fb247-119">If you need to run a trace for events that create a significant impact on performance, consider limiting the performance impact on the server by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="fb247-120">トレースの実行時間の短縮。</span><span class="sxs-lookup"><span data-stu-id="fb247-120">Run traces for shorter periods of time.</span></span> <span data-ttu-id="fb247-121">トレースの実行時間の長さは、停止時刻を有効にすることによって調整できます。</span><span class="sxs-lookup"><span data-stu-id="fb247-121">You can control the length of time that a trace runs by enabling a stop time.</span></span> <span data-ttu-id="fb247-122">これは、イベント クラスの数を制限したり、イベントをフィルター選択したりすることができない場合に特に重要になります。</span><span class="sxs-lookup"><span data-stu-id="fb247-122">This is especially important if you cannot limit the event classes or filter an event.</span></span> <span data-ttu-id="fb247-123">停止時刻を有効にすると、トレースによって発生するパフォーマンス コストが永続しなくなります。</span><span class="sxs-lookup"><span data-stu-id="fb247-123">Enabling a stop time ensures that the performance incurred does not last indefinitely.</span></span>  
  
-   <span data-ttu-id="fb247-124">トレース結果のサイズの制限。</span><span class="sxs-lookup"><span data-stu-id="fb247-124">Limit the size of the trace results.</span></span> <span data-ttu-id="fb247-125">トレース結果のサイズの上限は、ファイルの最大サイズに設定できます。</span><span class="sxs-lookup"><span data-stu-id="fb247-125">You can limit the size of the trace results to a maximum file size.</span></span> <span data-ttu-id="fb247-126">この方法を採用すると、ファイル サイズの上限に達した時点でパフォーマンス コストが発生しなくなります (ファイル ロールオーバーが有効になっていない場合)。</span><span class="sxs-lookup"><span data-stu-id="fb247-126">This strategy ensures that the performance cost stops when the file-size limit is reached (if file rollover is not enabled).</span></span>  
  
-   <span data-ttu-id="fb247-127">返されるイベントの数の制限。</span><span class="sxs-lookup"><span data-stu-id="fb247-127">Limit the number of events returned.</span></span> <span data-ttu-id="fb247-128">[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] を使用すると、トレースをテーブルに保存し、行の最大数を設定することにより、返されるイベントの数を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="fb247-128">With [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] you can limit the number of events returned by saving the trace to a table and setting the maximum number of rows.</span></span> <span data-ttu-id="fb247-129">最大行数に達した後も、 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] の画面にはトレース結果が引き続き表示されますが、結果をテーブルに記録することによるコストは発生しなくなります。</span><span class="sxs-lookup"><span data-stu-id="fb247-129">Trace results are still returned to the [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] screen after the maximum number of rows has been reached, but the cost of recording the results to a table is eliminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb247-130">参照</span><span class="sxs-lookup"><span data-stu-id="fb247-130">See Also</span></span>  
 [<span data-ttu-id="fb247-131">トレースへのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="fb247-131">Filter a Trace</span></span>](../sql-trace/filter-a-trace.md)  
  
  
