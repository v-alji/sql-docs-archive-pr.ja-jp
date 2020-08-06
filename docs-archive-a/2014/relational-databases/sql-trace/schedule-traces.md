---
title: トレースのスケジュール設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a698d88db35c84f7611293cf45807203c883865a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642722"
---
# <a name="schedule-traces"></a><span data-ttu-id="05197-102">トレースのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="05197-102">Schedule Traces</span></span>
  <span data-ttu-id="05197-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でトレースのスケジュールを設定するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="05197-103">There are two ways to schedule tracing in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05197-104">次のようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="05197-104">You can:</span></span>  
  
-   <span data-ttu-id="05197-105">トレース停止時刻を有効にする。</span><span class="sxs-lookup"><span data-stu-id="05197-105">Enable a trace stop time.</span></span>  
  
-   <span data-ttu-id="05197-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してトレースのスケジュールを設定する。</span><span class="sxs-lookup"><span data-stu-id="05197-106">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to schedule a trace.</span></span>  
  
## <a name="specifying-a-stop-time"></a><span data-ttu-id="05197-107">トレース停止時刻の指定</span><span class="sxs-lookup"><span data-stu-id="05197-107">Specifying a Stop Time</span></span>  
 <span data-ttu-id="05197-108">[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャまたは [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用する場合は、トレース停止時刻を指定できます。</span><span class="sxs-lookup"><span data-stu-id="05197-108">You can specify a trace stop time if you use [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures or if you use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="05197-109">停止時刻は、トレースを最初に構成する際に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05197-109">The stop time must be set when the trace is originally configured.</span></span>  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a><span data-ttu-id="05197-110">SQL Server エージェントを使用したトレースのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="05197-110">Scheduling Traces by Using SQL Server Agent</span></span>  
 <span data-ttu-id="05197-111">トレースのスケジュールを設定する最善の方法は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してトレースを開始してから、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ **sp_trace_setstatus**または [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用してトレース停止時刻を指定する方法です。</span><span class="sxs-lookup"><span data-stu-id="05197-111">The best way to schedule traces is to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to start the trace and then specify a trace stop time by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure **sp_trace_setstatus**, or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="05197-112">**トレースの終了時刻フィルターを設定するには**</span><span class="sxs-lookup"><span data-stu-id="05197-112">**To set an end time filter for a trace**</span></span>  
  
 [<span data-ttu-id="05197-113">イベントの終了時刻に基づいたフィルターでのイベントの選択 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="05197-113">Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [<span data-ttu-id="05197-114">sp_trace_setstatus &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05197-114">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="05197-115">参照</span><span class="sxs-lookup"><span data-stu-id="05197-115">See Also</span></span>  
 [<span data-ttu-id="05197-116">管理タスクの自動化 &#40;SQL Server エージェント&#41;</span><span class="sxs-lookup"><span data-stu-id="05197-116">Automated Administration Tasks &#40;SQL Server Agent&#41;</span></span>](../../ssms/agent/sql-server-agent.md)  
  
  
