---
title: トレースの作成 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], example
- traces [SQL Server], creating
ms.assetid: 79dd4254-e3c6-467a-bb6f-f99e51757e99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 35644891b2dca8359d6dc68fbddb67288d241cb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642012"
---
# <a name="create-a-trace-transact-sql"></a><span data-ttu-id="7e268-102">トレースの作成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e268-102">Create a Trace (Transact-SQL)</span></span>
  <span data-ttu-id="7e268-103">このトピックでは、ストアド プロシージャを使用してトレースを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e268-103">This topic describes how to use stored procedures to create a trace.</span></span>  
  
### <a name="to-create-a-trace"></a><span data-ttu-id="7e268-104">トレースを作成するには</span><span class="sxs-lookup"><span data-stu-id="7e268-104">To create a trace</span></span>  
  
1.  <span data-ttu-id="7e268-105">必要なパラメーターを指定して **sp_trace_create** を実行し、新しいトレースを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e268-105">Execute **sp_trace_create** with the required parameters to create a new trace.</span></span> <span data-ttu-id="7e268-106">新しいトレースは停止状態 (*status* の値が **0**) になります。</span><span class="sxs-lookup"><span data-stu-id="7e268-106">The new trace will be in a stopped state (*status* is **0**).</span></span>  
  
2.  <span data-ttu-id="7e268-107">必要なパラメーターを指定して **sp_trace_setevent** を実行し、トレースするイベントおよび列を選択します。</span><span class="sxs-lookup"><span data-stu-id="7e268-107">Execute **sp_trace_setevent** with the required parameters to select the events and columns to trace.</span></span>  
  
3.  <span data-ttu-id="7e268-108">必要に応じて、 **sp_trace_setfilter** を実行し、フィルターまたはフィルターの組み合わせを設定します。</span><span class="sxs-lookup"><span data-stu-id="7e268-108">Optionally, execute **sp_trace_setfilter** to set any or a combination of filters.</span></span>  
  
     <span data-ttu-id="7e268-109">**sp_trace_setevent** と **sp_trace_setfilter** は、停止状態の既存のトレースに対してのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="7e268-109">**sp_trace_setevent** and **sp_trace_setfilter** can be executed only on existing traces that are stopped.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7e268-110">通常のストアド プロシージャとは異なり、すべての SQL Server Profiler ストアド プロシージャ (<strong>sp_trace_*xx*</strong>) のパラメーターでは、データ型が厳密に定義されており、データ型の自動変換はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7e268-110">Unlike regular stored procedures, parameters of all SQL Server Profiler stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="7e268-111">これらのパラメーターが、引数の説明で指定されている正しいデータ型で呼び出されないと、このストアド プロシージャではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="7e268-111">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e268-112">例</span><span class="sxs-lookup"><span data-stu-id="7e268-112">Example</span></span>  
 <span data-ttu-id="7e268-113">[!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してトレースを作成するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7e268-113">The following code demonstrates creating a trace using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7e268-114">トレースの作成、トレース ファイルの設定、およびトレースの停止の、3 つのセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="7e268-114">It is in three sections: creating the trace, populating the trace file, and stopping the trace.</span></span> <span data-ttu-id="7e268-115">トレースするイベントを追加して、トレースをカスタマイズしてください。</span><span class="sxs-lookup"><span data-stu-id="7e268-115">Customize the trace by adding the events that you want to trace.</span></span> <span data-ttu-id="7e268-116">イベントと列の一覧については、「 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)を使用してトレースを作成するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7e268-116">For the list of events and columns, see [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql).</span></span>  
  
 <span data-ttu-id="7e268-117">次のコードでは、トレースを作成してイベントを追加し、トレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="7e268-117">The following code creates a trace, adds events to the trace, and then starts the trace:</span></span>  
  
```  
DECLARE @RC int, @TraceID int, @on BIT  
EXEC @rc = sp_trace_create @TraceID output, 0, N'C:\SampleTrace'  
  
-- Select the return code to see if the trace creation was successful.  
SELECT RC = @RC, TraceID = @TraceID  
  
-- Set the events and data columns you need to capture.  
SELECT @on = 1  
  
-- 10 is RPC:Completed event. 1 is TextData column.   
EXEC sp_trace_setevent @TraceID, 10, 1, @on   
-- 13 is SQL:BatchStarting, 11 is LoginName  
EXEC sp_trace_setevent @TraceID, 13, 11, @on   
-- 13 is SQL:BatchStarting, 14 is StartTime  
EXEC sp_trace_setevent @TraceID, 13, 14, @on   
-- 12 is SQL:BatchCompleted, 15 is EndTime  
EXEC sp_trace_setevent @TraceID, 12, 15, @on   
-- 13 is SQL:BatchStarting, 1 is TextData  
EXEC sp_trace_setevent @TraceID, 13, 1, @on   
  
-- Set any filter. Not provided in this example  
--EXEC sp_trace_setfilter 1, 10, 0, 6, N'%Profiler%'  
  
-- Start Trace (status 1 = start)  
EXEC @RC = sp_trace_setstatus @TraceID, 1  
GO  
  
```  
  
## <a name="example"></a><span data-ttu-id="7e268-118">例</span><span class="sxs-lookup"><span data-stu-id="7e268-118">Example</span></span>  
 <span data-ttu-id="7e268-119">トレースが作成および開始されたので、次のコードを実行して、トレースにアクティビティを設定します。</span><span class="sxs-lookup"><span data-stu-id="7e268-119">Now that the trace has been created and started, execute the following code to populate the trace with activity.</span></span>  
  
```  
SELECT * FROM master.sys.databases  
GO  
SELECT * FROM ::fn_trace_getinfo(default)  
GO  
  
```  
  
## <a name="example"></a><span data-ttu-id="7e268-120">例</span><span class="sxs-lookup"><span data-stu-id="7e268-120">Example</span></span>  
 <span data-ttu-id="7e268-121">トレースは、いつでも停止および再開できます。</span><span class="sxs-lookup"><span data-stu-id="7e268-121">The trace can be stopped and restarted at any time.</span></span> <span data-ttu-id="7e268-122">この例では次のコードを実行して、トレースを停止し、閉じ、トレース定義を削除します。</span><span class="sxs-lookup"><span data-stu-id="7e268-122">In this example, execute the following code to stop the trace, close the trace, and delete the trace definition.</span></span>  
  
```  
DECLARE @TraceID int  
-- Populate a variable with the trace_id of the current trace  
SELECT  @TraceID = TraceID FROM ::fn_trace_getinfo(default) WHERE VALUE = N'C:\SampleTrace.trc'  
  
-- First stop the trace.   
EXEC sp_trace_setstatus @TraceID, 0  
  
-- Close and then delete its definition from SQL Server.   
EXEC sp_trace_setstatus @TraceID, 2  
  
```  
  
## <a name="example"></a><span data-ttu-id="7e268-123">例</span><span class="sxs-lookup"><span data-stu-id="7e268-123">Example</span></span>  
 <span data-ttu-id="7e268-124">トレース ファイルを調べるには、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して SampleTrace.trc ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7e268-124">To examine the trace file, open the SampleTrace.trc file using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e268-125">参照</span><span class="sxs-lookup"><span data-stu-id="7e268-125">See Also</span></span>  
 <span data-ttu-id="7e268-126">[SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e268-126">[SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="7e268-127">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e268-127">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="7e268-128">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e268-128">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="7e268-129">sp_trace_setfilter &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7e268-129">sp_trace_setfilter &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)  
  
  
