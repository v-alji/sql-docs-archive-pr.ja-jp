---
title: ストアド プロシージャを使用した手動トレースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e2840dced22ccdba8fe71cc87c05d7fd6fb4be58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642011"
---
# <a name="create-manual-traces-using-stored-procedures"></a><span data-ttu-id="0cb77-102">ストアド プロシージャを使用した手動トレースの作成</span><span class="sxs-lookup"><span data-stu-id="0cb77-102">Create Manual Traces using Stored Procedures</span></span>
  <span data-ttu-id="0cb77-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、 [!INCLUDE[tsql](../../includes/tsql-md.md)] のインスタンスでトレースを作成するための [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]システム ストアド プロシージャが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0cb77-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to create traces on an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="0cb77-104">これらのシステム ストアド プロシージャを使用して、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]からではなく、ユーザー独自のアプリケーションからトレースを手動で作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0cb77-104">These system stored procedures can be used from within your own applications to create traces manually, instead of using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="0cb77-105">これにより、企業のニーズに合わせたカスタム アプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0cb77-105">This allows you to write custom applications specific to the needs of your enterprise.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0cb77-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0cb77-106">In This Section</span></span>  
 <span data-ttu-id="0cb77-107">次の表に、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスをトレースするためのシステム ストアド プロシージャを示します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-107">The following table lists the system stored procedures for tracing an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
|<span data-ttu-id="0cb77-108">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="0cb77-108">Stored procedure</span></span>|<span data-ttu-id="0cb77-109">実行するタスク</span><span class="sxs-lookup"><span data-stu-id="0cb77-109">Task performed</span></span>|  
|----------------------|--------------------|  
|[<span data-ttu-id="0cb77-110">sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb77-110">sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql)|<span data-ttu-id="0cb77-111">トレースに含まれるイベントに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-111">Returns information about events included in a trace.</span></span>|  
|[<span data-ttu-id="0cb77-112">sys.fn_trace_getinfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb77-112">sys.fn_trace_getinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)|<span data-ttu-id="0cb77-113">指定したトレースまたはすべての既存のトレースに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-113">Returns information about a specified trace or all existing traces.</span></span>|  
|[<span data-ttu-id="0cb77-114">sp_trace_create &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb77-114">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)|<span data-ttu-id="0cb77-115">トレース定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-115">Creates a trace definition.</span></span> <span data-ttu-id="0cb77-116">新しいトレースは停止状態になります。</span><span class="sxs-lookup"><span data-stu-id="0cb77-116">The new trace will be in a stopped state.</span></span>|  
|[<span data-ttu-id="0cb77-117">sp_trace_generateevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb77-117">sp_trace_generateevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)|<span data-ttu-id="0cb77-118">ユーザー定義イベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-118">Creates a user-defined event.</span></span>|  
|[<span data-ttu-id="0cb77-119">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb77-119">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)|<span data-ttu-id="0cb77-120">イベント クラスまたはデータ列をトレースに追加するか、トレースから削除します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-120">Adds an event class or data column to a trace, or removes one from it.</span></span>|  
|[<span data-ttu-id="0cb77-121">sp_trace_setstatus &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb77-121">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|<span data-ttu-id="0cb77-122">トレースを開始、停止、または終了します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-122">Starts, stops, or closes a trace.</span></span>|  
|[<span data-ttu-id="0cb77-123">sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb77-123">sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)|<span data-ttu-id="0cb77-124">トレースに適用されたフィルターに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-124">Returns information about filters applied to a trace.</span></span>|  
|[<span data-ttu-id="0cb77-125">sp_trace_setfilter &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb77-125">sp_trace_setfilter &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|<span data-ttu-id="0cb77-126">新しいフィルターまたは変更されたフィルターをトレースに適用します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-126">Applies a new or modified filter to a trace.</span></span>|  
  
 <span data-ttu-id="0cb77-127">**ストアド プロシージャを使用してユーザー独自のトレースを定義するには**</span><span class="sxs-lookup"><span data-stu-id="0cb77-127">**To define your own trace using stored procedures**</span></span>  
  
1.  <span data-ttu-id="0cb77-128">**sp_trace_setevent**を使用して、キャプチャするイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-128">Specify the events to capture using **sp_trace_setevent**.</span></span>  
  
2.  <span data-ttu-id="0cb77-129">イベント フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-129">Specify any event filters.</span></span> <span data-ttu-id="0cb77-130">詳細については、「[トレース フィルターの設定 &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cb77-130">For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md).</span></span>  
  
3.  <span data-ttu-id="0cb77-131">**sp_trace_create** を使用して、キャプチャされたイベント データの出力先を指定します。</span><span class="sxs-lookup"><span data-stu-id="0cb77-131">Specify the destination for the captured event data using **sp_trace_create**.</span></span>  
  
 <span data-ttu-id="0cb77-132">トレース ストアド プロシージャを使用した例については、「[トレースの作成 &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cb77-132">For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).</span></span>  
  
 <span data-ttu-id="0cb77-133">**トレース定義の既定値を設定するには**</span><span class="sxs-lookup"><span data-stu-id="0cb77-133">**To set trace definition defaults**</span></span>  
  
 [<span data-ttu-id="0cb77-134">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="0cb77-134">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
 <span data-ttu-id="0cb77-135">**トレース表示の既定値を設定するには**</span><span class="sxs-lookup"><span data-stu-id="0cb77-135">**To set trace display defaults**</span></span>  
  
 [<span data-ttu-id="0cb77-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="0cb77-136">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 <span data-ttu-id="0cb77-137">**トレースを作成するには**</span><span class="sxs-lookup"><span data-stu-id="0cb77-137">**To create a trace**</span></span>  
  
 [<span data-ttu-id="0cb77-138">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="0cb77-138">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [<span data-ttu-id="0cb77-139">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0cb77-139">Transact-SQL</span></span>](../sql-trace/create-a-trace-transact-sql.md)  
  
 <span data-ttu-id="0cb77-140">**トレース テンプレートからイベントを追加または削除するには**</span><span class="sxs-lookup"><span data-stu-id="0cb77-140">**To add or remove events from a trace template**</span></span>  
  
 [<span data-ttu-id="0cb77-141">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="0cb77-141">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="0cb77-142">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0cb77-142">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
