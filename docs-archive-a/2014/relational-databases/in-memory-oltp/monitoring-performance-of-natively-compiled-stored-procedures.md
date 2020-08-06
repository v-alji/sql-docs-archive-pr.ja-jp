---
title: ネイティブ コンパイル ストアド プロシージャのパフォーマンスの監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 55548cb2-77a8-4953-8b5a-f2778a4f13cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d14d27cdc20c0f090c7a030efe05cfce4842f437
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742069"
---
# <a name="monitoring-performance-of-natively-compiled-stored-procedures"></a><span data-ttu-id="72a48-102">ネイティブ コンパイル ストアド プロシージャのパフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="72a48-102">Monitoring Performance of Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="72a48-103">このトピックでは、ネイティブ コンパイル ストアド プロシージャのパフォーマンスを監視する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="72a48-103">This topic discusses how you can monitor the performance of natively compiled stored procedures</span></span>  
  
## <a name="using-extended-events"></a><span data-ttu-id="72a48-104">拡張イベントの使用</span><span class="sxs-lookup"><span data-stu-id="72a48-104">Using Extended Events</span></span>  
 <span data-ttu-id="72a48-105">クエリの実行をトレースするには、`sp_statement_completed` 拡張イベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="72a48-105">Use the `sp_statement_completed` extended event to trace execution of a query.</span></span> <span data-ttu-id="72a48-106">このイベントを使用して拡張イベント セッションを作成し、オプションで、特定のネイティブ コンパイル ストアド プロシージャに対応する object_id でフィルター処理を実行します。各クエリの実行後に、拡張イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="72a48-106">Create an extended event session with this event, optionally with a filter on object_id for a particular natively compiled stored procedure, The extended event is raised after the execution of each query.</span></span> <span data-ttu-id="72a48-107">拡張イベントによって報告された CPU 時間と期間は、クエリが使用した CPU 時間と実行時間の長さを示します。</span><span class="sxs-lookup"><span data-stu-id="72a48-107">The CPU time and duration reported by the extended event indicate how much CPU the query used and the execution time.</span></span> <span data-ttu-id="72a48-108">多くの CPU 時間を使用しているネイティブ コンパイル ストアド プロシージャには、パフォーマンスの問題が存在している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72a48-108">A natively compiled stored procedure that uses a lot of CPU time may have performance problems.</span></span>  
  
 <span data-ttu-id="72a48-109">拡張イベント内の `line_number` と `object_id` を組み合わせて使用し、クエリを調査することができます。</span><span class="sxs-lookup"><span data-stu-id="72a48-109">`line_number`, along with the `object_id` in the extended event can be used to investigate the query.</span></span> <span data-ttu-id="72a48-110">次のクエリを使用して、プロシージャの定義を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="72a48-110">The following query can be used to retrieve the procedure definition.</span></span> <span data-ttu-id="72a48-111">行番号を使用して、定義内のクエリを特定できます:</span><span class="sxs-lookup"><span data-stu-id="72a48-111">The line number can be used to identify the query within the definition:</span></span>  
  
```sql  
select [definition] from sys.sql_modules where object_id=object_id  
```  
  
 <span data-ttu-id="72a48-112">拡張イベントの詳細につい `sp_statement_completed` ては、「[イベントの原因となったステートメントを取得する方法](https://blogs.msdn.com/b/extended_events/archive/2010/05/07/making-a-statement-how-to-retrieve-the-t-sql-statement-that-caused-an-event.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72a48-112">For more information about the `sp_statement_completed` extended event, see [How to retrieve the statement that caused an event](https://blogs.msdn.com/b/extended_events/archive/2010/05/07/making-a-statement-how-to-retrieve-the-t-sql-statement-that-caused-an-event.aspx).</span></span>  
  
## <a name="using-data-management-views"></a><span data-ttu-id="72a48-113">データ管理ビューの使用</span><span class="sxs-lookup"><span data-stu-id="72a48-113">Using Data Management Views</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="72a48-114">は、プロシージャ レベルとクエリ レベルの両方で、ネイティブ コンパイル ストアド プロシージャに関する実行の統計の収集をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="72a48-114">supports collecting execution statistics for natively compiled stored procedures, both on the procedure level and the query level.</span></span> <span data-ttu-id="72a48-115">パフォーマンスに与える影響が原因で、実行の統計の収集は既定では有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="72a48-115">Collecting execution statistics is not enabled by default due to performance impact.</span></span>  
  
 <span data-ttu-id="72a48-116">ネイティブ コンパイル ストアド プロシージャに対する統計コレクションは、[sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql) を使用して有効化または無効化することができます。</span><span class="sxs-lookup"><span data-stu-id="72a48-116">You can enable and disable statistics collection on natively compiled stored procedures using [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="72a48-117">[sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql) で統計コレクションを有効にすると、[sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) を使用してネイティブ コンパイル ストアド プロシージャのパフォーマンスを監視することができます。</span><span class="sxs-lookup"><span data-stu-id="72a48-117">When statistics collection is enabled with [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql), you can use [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) to monitor performance of a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="72a48-118">[sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql) で統計コレクションを有効にすると、[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) を使用してネイティブ コンパイル ストアド プロシージャのパフォーマンスを監視することができます。</span><span class="sxs-lookup"><span data-stu-id="72a48-118">When statistics collection is enabled with [sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql), you can use [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) to monitor performance of a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="72a48-119">収集を開始するには、統計コレクションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="72a48-119">At the start of collection, enable statistics collection.</span></span> <span data-ttu-id="72a48-120">次に、ネイティブ コンパイル ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="72a48-120">Then, execute the natively compiled stored procedure.</span></span> <span data-ttu-id="72a48-121">収集を終了するには、統計コレクションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="72a48-121">At the end of collection, disable statistics collection.</span></span> <span data-ttu-id="72a48-122">次に、DMV によって返された実行の統計を分析します。</span><span class="sxs-lookup"><span data-stu-id="72a48-122">Then, analyze the execution statistics returned by the DMVs.</span></span>  
  
 <span data-ttu-id="72a48-123">統計を収集した後、ネイティブ コンパイル ストアド プロシージャに関する実行の統計を要求するには、プロシージャに対して [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) を使用し、クエリに対して [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) を使用することが実行できます。</span><span class="sxs-lookup"><span data-stu-id="72a48-123">After you collect statistics, the execution statistics for natively compiled stored procedures can be queried for a procedure with [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql), and for queries with [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72a48-124">ネイティブ コンパイル ストアド プロシージャに対する統計コレクションが有効になっている場合は、ワーカー時間がミリ秒単位で収集されます。</span><span class="sxs-lookup"><span data-stu-id="72a48-124">For natively compiled stored procedures when statistics collection is enabled, worker time is collected in milliseconds.</span></span> <span data-ttu-id="72a48-125">クエリが 1 ミリ秒未満で実行された場合は、値は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="72a48-125">If the query executes in less than a millisecond, the value will be 0.</span></span> <span data-ttu-id="72a48-126">ネイティブ コンパイル ストアド プロシージャに関して、多くの実行が 1 ミリ秒未満である場合は、 **total_worker_time** は精度が高くない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72a48-126">For natively compiled stored procedures, **total_worker_time** may not be accurate if many executions take less than 1 millisecond.</span></span>  
  
 <span data-ttu-id="72a48-127">次のクエリは、統計コレクションを有効にした後、現在のデータベース内で実行されたネイティブ コンパイル ストアド プロシージャに関するプロシージャ名と実行の統計を返します。</span><span class="sxs-lookup"><span data-stu-id="72a48-127">The following query returns the procedure names and execution statistics for natively compiled stored procedures in the current database, after statistics collection:</span></span>  
  
```sql  
select object_id,  
       object_name(object_id) as 'object name',  
       cached_time,  
       last_execution_time,  
       execution_count,  
       total_worker_time,  
       last_worker_time,  
       min_worker_time,  
       max_worker_time,  
       total_elapsed_time,  
       last_elapsed_time,  
       min_elapsed_time,  
       max_elapsed_time   
from sys.dm_exec_procedure_stats  
where database_id=db_id() and object_id in (select object_id   
from sys.sql_modules where uses_native_compilation=1)  
order by total_worker_time desc  
```  
  
 <span data-ttu-id="72a48-128">次のクエリは、統計コレクションが有効になっている現在のデータベースに対して実行されたネイティブ コンパイル ストアド プロシージャ内のすべてのクエリに対応するクエリ テキストと実行の統計を返し、合計ワーカー時間の降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="72a48-128">The following query returns the query text as well as execution statistics for all queries in natively compiled stored procedures in the current database for which statistics have been collected, ordered by total worker time, in descending order:</span></span>  
  
```sql  
select st.objectid,   
       object_name(st.objectid) as 'object name',   
       SUBSTRING(st.text, (qs.statement_start_offset/2) + 1, ((qs.statement_end_offset-qs.statement_start_offset)/2) + 1) as 'query text',   
       qs.creation_time,  
       qs.last_execution_time,  
       qs.execution_count,  
       qs.total_worker_time,  
       qs.last_worker_time,  
       qs.min_worker_time,  
       qs.max_worker_time,  
       qs.total_elapsed_time,  
       qs.last_elapsed_time,  
       qs.min_elapsed_time,  
       qs.max_elapsed_time  
from sys.dm_exec_query_stats qs cross apply sys.dm_exec_sql_text(sql_handle) st  
where  st.dbid=db_id() and st.objectid in (select object_id   
from sys.sql_modules where uses_native_compilation=1)  
order by qs.total_worker_time desc  
```  
  
 <span data-ttu-id="72a48-129">ネイティブ コンパイル ストアド プロシージャでは、SHOWPLAN_XML (推定実行プラン) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="72a48-129">Natively compiled stored procedures support SHOWPLAN_XML (estimated execution plan).</span></span> <span data-ttu-id="72a48-130">推定実行プランを使用してクエリ プランを調査し、不適切なプランの問題を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="72a48-130">The estimated execution plan can be used to inspect the query plan, to find any bad plan issues.</span></span> <span data-ttu-id="72a48-131">不適切なプランの一般的な理由は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="72a48-131">Common reasons for bad plans are:</span></span>  
  
-   <span data-ttu-id="72a48-132">プロシージャを作成する前に統計を更新していません。</span><span class="sxs-lookup"><span data-stu-id="72a48-132">Stats were not updated before the procedure was created.</span></span>  
  
-   <span data-ttu-id="72a48-133">欠落したインデックス</span><span class="sxs-lookup"><span data-stu-id="72a48-133">Missing indexes</span></span>  
  
 <span data-ttu-id="72a48-134">Showplan XML を取得するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)]を実行します。</span><span class="sxs-lookup"><span data-stu-id="72a48-134">Showplan XML is obtained by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
```sql  
SET SHOWPLAN_XML ON  
GO  
EXEC my_proc   
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 <span data-ttu-id="72a48-135">代わりに、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でプロシージャ名を選択し、 **[推定実行プランの表示]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="72a48-135">Alternatively, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the procedure name and click **Display Estimated Execution Plan**.</span></span>  
  
 <span data-ttu-id="72a48-136">ネイティブ コンパイル ストアド プロシージャに対応する推定実行プランでは、プロシージャ内に存在するクエリに関するクエリ演算子と式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="72a48-136">The estimated execution plan for natively compiled stored procedures shows the query operators and expressions for the queries in the procedure.</span></span> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="72a48-137">では、ネイティブ コンパイル ストアド プロシージャに対して、すべての SHOWPLAN_XML をサポートしているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="72a48-137">does not support all SHOWPLAN_XML attributes for natively compiled stored procedures.</span></span> <span data-ttu-id="72a48-138">たとえば、クエリ オプティマイザー コストに関連する属性は、プロシージャに対応する SHOWPLAN_XML の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="72a48-138">For example, attributes related to query optimizer costing are not part of the SHOWPLAN_XML for the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a48-139">参照</span><span class="sxs-lookup"><span data-stu-id="72a48-139">See Also</span></span>  
 [<span data-ttu-id="72a48-140">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="72a48-140">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
