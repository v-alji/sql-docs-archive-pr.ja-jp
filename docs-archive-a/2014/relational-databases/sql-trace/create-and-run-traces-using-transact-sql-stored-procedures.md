---
title: Transact-SQL ストアド プロシージャを使用したトレースの作成と実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2905ce2822598502ef6337d1a083fb6fde001c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642013"
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a><span data-ttu-id="64d10-102">Transact-SQL ストアド プロシージャを使用したトレースの作成と実行</span><span class="sxs-lookup"><span data-stu-id="64d10-102">Create and Run Traces Using Transact-SQL Stored Procedures</span></span>
  <span data-ttu-id="64d10-103">トレースの作成や実行を Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して行うか、システム ストアド プロシージャを使用して行うかによって、SQL トレースでのトレースの処理が異なります。</span><span class="sxs-lookup"><span data-stu-id="64d10-103">The process of tracing with SQL Trace varies depending on whether you create and run your trace by using Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or by using system stored procedures.</span></span>  
  
 <span data-ttu-id="64d10-104">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の代替手段として、 [!INCLUDE[tsql](../../includes/tsql-md.md)] システム ストアド プロシージャを使用してトレースを作成および実行できます。</span><span class="sxs-lookup"><span data-stu-id="64d10-104">As an alternative to [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can use [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to create and run traces.</span></span> <span data-ttu-id="64d10-105">システム ストアド プロシージャを使用したトレースの処理は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="64d10-105">The process of tracing by using system stored procedures is as follows:</span></span>  
  
1.  <span data-ttu-id="64d10-106">**sp_trace_create**を使用して、トレースを作成します。</span><span class="sxs-lookup"><span data-stu-id="64d10-106">Create a trace by using **sp_trace_create**.</span></span>  
  
2.  <span data-ttu-id="64d10-107">**sp_trace_setevent**によりイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="64d10-107">Add events with **sp_trace_setevent**.</span></span>  
  
3.  <span data-ttu-id="64d10-108">必要に応じて、 **sp_trace_setfilter**によりフィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="64d10-108">(Optional) Set a filter with **sp_trace_setfilter**.</span></span>  
  
4.  <span data-ttu-id="64d10-109">**sp_trace_setstatus**によりトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="64d10-109">Start the trace with **sp_trace_setstatus**.</span></span>  
  
5.  <span data-ttu-id="64d10-110">**sp_trace_setstatus**によりトレースを停止します。</span><span class="sxs-lookup"><span data-stu-id="64d10-110">Stop the trace with **sp_trace_setstatus**.</span></span>  
  
6.  <span data-ttu-id="64d10-111">**sp_trace_setstatus**によりトレースを閉じます。</span><span class="sxs-lookup"><span data-stu-id="64d10-111">Close the trace with **sp_trace_setstatus**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="64d10-112">[!INCLUDE[tsql](../../includes/tsql-md.md)] システム ストアド プロシージャを使用すると、サーバー側のトレースが作成されます。これにより、ディスク上に空き領域があり、かつ書き込みエラーが発生しない限り、イベントが失われないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="64d10-112">Using [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures creates a server-side trace, which guarantees that no events will be lost as long as there is space on the disk and no write errors occur.</span></span> <span data-ttu-id="64d10-113">ディスクがいっぱいになるか、ディスク障害が発生した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの実行は続行されますが、トレースは停止されます。</span><span class="sxs-lookup"><span data-stu-id="64d10-113">If the disk becomes full or the disk fails, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance continues to run, but tracing stops.</span></span> <span data-ttu-id="64d10-114">**c2 audit mode** が設定されていて、書き込みエラーが発生すると、トレースが停止され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="64d10-114">If the **c2 audit mode** is set, and there is a write failure, tracing stops and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span> <span data-ttu-id="64d10-115">**c2 audit mode** 設定の詳細については、「 [c2 audit mode サーバー構成オプション](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64d10-115">For more information about the **c2 audit mode** setting, see [c2 audit mode Server Configuration Option](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64d10-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="64d10-116">In This Section</span></span>  
  
|<span data-ttu-id="64d10-117">トピック</span><span class="sxs-lookup"><span data-stu-id="64d10-117">Topic</span></span>|<span data-ttu-id="64d10-118">説明</span><span class="sxs-lookup"><span data-stu-id="64d10-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="64d10-119">SQL トレースの最適化</span><span class="sxs-lookup"><span data-stu-id="64d10-119">Optimize SQL Trace</span></span>](sql-trace.md)|<span data-ttu-id="64d10-120">システム パフォーマンスへのトレースの影響を軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="64d10-120">Contains information about ways you can reduce the effects of tracing on system performance.</span></span>|  
|[<span data-ttu-id="64d10-121">トレースへのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="64d10-121">Filter a Trace</span></span>](filter-a-trace.md)|<span data-ttu-id="64d10-122">トレースでのフィルターの使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="64d10-122">Contains information about using filters for tracing.</span></span>|  
|[<span data-ttu-id="64d10-123">トレース ファイルとテーブル サイズの制限</span><span class="sxs-lookup"><span data-stu-id="64d10-123">Limit Trace File and Table Sizes</span></span>](limit-trace-file-and-table-sizes.md)|<span data-ttu-id="64d10-124">トレース データが書き込まれるファイルやテーブルのサイズを制限する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="64d10-124">Contains information about how to limit the size of files and tables where trace data is written.</span></span> <span data-ttu-id="64d10-125">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でのみ、トレース情報をテーブルに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="64d10-125">Note that only [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can write trace information to tables.</span></span>|  
|[<span data-ttu-id="64d10-126">トレースのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="64d10-126">Schedule Traces</span></span>](schedule-traces.md)|<span data-ttu-id="64d10-127">トレースの開始時刻や終了時刻を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="64d10-127">Contains information about how to set the start time and the end time for tracing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64d10-128">参照</span><span class="sxs-lookup"><span data-stu-id="64d10-128">See Also</span></span>  
 <span data-ttu-id="64d10-129">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="64d10-129">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="64d10-130">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="64d10-130">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="64d10-131">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="64d10-131">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span></span>  
 [<span data-ttu-id="64d10-132">sp_trace_setstatus &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="64d10-132">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
  
