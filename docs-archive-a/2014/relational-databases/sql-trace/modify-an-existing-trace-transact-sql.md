---
title: 既存のトレースの変更 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 55b8172ef8e6188059c484ab41f1a719e0e9f8c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632299"
---
# <a name="modify-an-existing-trace-transact-sql"></a><span data-ttu-id="d980d-102">既存のトレースの変更 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d980d-102">Modify an Existing Trace (Transact-SQL)</span></span>
  <span data-ttu-id="d980d-103">このトピックでは、ストアド プロシージャを使用して既存のトレースを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d980d-103">This topic describes how to use stored procedures to modify an existing trace.</span></span>  
  
### <a name="to-modify-an-existing-trace"></a><span data-ttu-id="d980d-104">既存のトレースを変更するには</span><span class="sxs-lookup"><span data-stu-id="d980d-104">To modify an existing trace</span></span>  
  
1.  <span data-ttu-id="d980d-105">トレースが既に実行中の場合は、**@status = 0** を指定して **sp_trace_setstatus** を実行し、トレースを停止します。</span><span class="sxs-lookup"><span data-stu-id="d980d-105">If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="d980d-106">トレース イベントを変更するには、パラメーターを使用して変更を指定し、 **sp_trace_setevent** を実行します。</span><span class="sxs-lookup"><span data-stu-id="d980d-106">To modify trace events, execute **sp_trace_setevent** by specifying the changes through the parameters.</span></span> <span data-ttu-id="d980d-107">パラメーターは次の順序で指定します。</span><span class="sxs-lookup"><span data-stu-id="d980d-107">Listed in order, the parameters are:</span></span>  
  
    -   <span data-ttu-id="d980d-108">**@traceid**(トレース ID)</span><span class="sxs-lookup"><span data-stu-id="d980d-108">**@traceid** (Trace ID)</span></span>  
  
    -   <span data-ttu-id="d980d-109">**@eventid**(イベント ID)</span><span class="sxs-lookup"><span data-stu-id="d980d-109">**@eventid** (Event ID)</span></span>  
  
    -   <span data-ttu-id="d980d-110">**@columnid**(列 ID)</span><span class="sxs-lookup"><span data-stu-id="d980d-110">**@columnid** (Column ID)</span></span>  
  
    -   <span data-ttu-id="d980d-111">**@on**代わっ</span><span class="sxs-lookup"><span data-stu-id="d980d-111">**@on** (ON)</span></span>  
  
     <span data-ttu-id="d980d-112">パラメーターを変更する場合は **@on** 、パラメーターとの相互作用に注意してください **@columnid** 。</span><span class="sxs-lookup"><span data-stu-id="d980d-112">When you modify the **@on** parameter, keep in mind its interaction with the **@columnid** parameter:</span></span>  
  
    |<span data-ttu-id="d980d-113">ON</span><span class="sxs-lookup"><span data-stu-id="d980d-113">ON</span></span>|<span data-ttu-id="d980d-114">列 ID</span><span class="sxs-lookup"><span data-stu-id="d980d-114">Column ID</span></span>|<span data-ttu-id="d980d-115">結果</span><span class="sxs-lookup"><span data-stu-id="d980d-115">Result</span></span>|  
    |--------|---------------|------------|  
    |<span data-ttu-id="d980d-116">ON (**1**)</span><span class="sxs-lookup"><span data-stu-id="d980d-116">ON (**1**)</span></span>|<span data-ttu-id="d980d-117">NULL</span><span class="sxs-lookup"><span data-stu-id="d980d-117">NULL</span></span>|<span data-ttu-id="d980d-118">イベントはオンになります。</span><span class="sxs-lookup"><span data-stu-id="d980d-118">Event is turned on.</span></span> <span data-ttu-id="d980d-119">すべての列は消去されます。</span><span class="sxs-lookup"><span data-stu-id="d980d-119">All columns are cleared.</span></span>|  
    ||<span data-ttu-id="d980d-120">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="d980d-120">NOT NULL</span></span>|<span data-ttu-id="d980d-121">指定されたイベントに対して列はオンになります。</span><span class="sxs-lookup"><span data-stu-id="d980d-121">Column is turned on for the specified event.</span></span>|  
    |<span data-ttu-id="d980d-122">OFF (**0**)</span><span class="sxs-lookup"><span data-stu-id="d980d-122">OFF (**0**)</span></span>|<span data-ttu-id="d980d-123">NULL</span><span class="sxs-lookup"><span data-stu-id="d980d-123">NULL</span></span>|<span data-ttu-id="d980d-124">イベントはオフになります。</span><span class="sxs-lookup"><span data-stu-id="d980d-124">Event is turned off.</span></span> <span data-ttu-id="d980d-125">すべての列は消去されます。</span><span class="sxs-lookup"><span data-stu-id="d980d-125">All columns are cleared.</span></span>|  
    ||<span data-ttu-id="d980d-126">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="d980d-126">NOT NULL</span></span>|<span data-ttu-id="d980d-127">指定されたイベントに対して列はオフになります。</span><span class="sxs-lookup"><span data-stu-id="d980d-127">Column is turned off for the specified event.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="d980d-128">通常のストアド プロシージャとは異なり、すべての [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ストアド プロシージャ (<strong>sp_trace_*xx*</strong>) で、パラメーターのデータ型が厳密に定義されており、データ型の自動変換はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d980d-128">Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="d980d-129">これらのパラメーターが、引数の説明で指定されている正しいデータ型で呼び出されないと、このストアド プロシージャではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="d980d-129">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d980d-130">参照</span><span class="sxs-lookup"><span data-stu-id="d980d-130">See Also</span></span>  
 <span data-ttu-id="d980d-131">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d980d-131">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="d980d-132">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d980d-132">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="d980d-133">[システム ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d980d-133">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="d980d-134">SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d980d-134">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
