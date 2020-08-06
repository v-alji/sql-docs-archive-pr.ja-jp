---
title: 既存の SQL トレース スクリプトから拡張イベント セッションへの変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, convert script to extended events
- extended events [SQL Server], convert SQL Trace script
ms.assetid: 4c8f29e6-0a37-490f-88b3-33493871b3f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e5b0d0e20fbf4fd55398c130abf6cfff128ebe8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643365"
---
# <a name="convert-an-existing-sql-trace-script-to-an-extended-events-session"></a><span data-ttu-id="feeec-102">既存の SQL トレース スクリプトから拡張イベント セッションへの変換</span><span class="sxs-lookup"><span data-stu-id="feeec-102">Convert an Existing SQL Trace Script to an Extended Events Session</span></span>
  <span data-ttu-id="feeec-103">拡張イベント セッションに変換する SQL トレース スクリプトが既に手元にある場合は、このトピックの手順を使用して、等価な拡張イベント セッションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="feeec-103">If you have an existing SQL Trace script that you want to convert to an Extended Events session, you can use the procedures in this topic to create an equivalent Extended Events session.</span></span> <span data-ttu-id="feeec-104">変換を実行するために必要な情報は、trace_xe_action_map および trace_xe_event_map システム テーブル内の情報を使用して収集できます。</span><span class="sxs-lookup"><span data-stu-id="feeec-104">By using the information in the trace_xe_action_map and trace_xe_event_map system tables, you can collect the information that you must have to do the conversion.</span></span>  
  
 <span data-ttu-id="feeec-105">手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="feeec-105">The steps include the following:</span></span>  
  
1.  <span data-ttu-id="feeec-106">既存のスクリプトを実行して SQL トレース セッションを作成し、トレースの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="feeec-106">Execute the existing script to create a SQL Trace session, and then obtain the ID of the trace.</span></span>  
  
2.  <span data-ttu-id="feeec-107">fn_trace_geteventinfo 関数を使用したクエリを実行して、SQL トレース イベント クラスとそれに関連付けられた列ごとに、等価な拡張イベントおよびアクションを探します。</span><span class="sxs-lookup"><span data-stu-id="feeec-107">Run a query that uses the fn_trace_geteventinfo function to find the equivalent Extended Events events and actions for each SQL Trace event class and its associated columns.</span></span>  
  
3.  <span data-ttu-id="feeec-108">使用するフィルターおよび等価な拡張イベントのアクションを、fn_trace_getfilterinfo 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="feeec-108">Use the fn_trace_getfilterinfo function to list the filters and the equivalent Extended Events actions to use.</span></span>  
  
4.  <span data-ttu-id="feeec-109">拡張イベントにおける等価なイベント、アクション、および述語 (フィルター) を使用して、拡張イベント セッションを手動で作成します。</span><span class="sxs-lookup"><span data-stu-id="feeec-109">Manually create an Extended Events session, using the equivalent Extended Events events, actions, and predicates (filters).</span></span>  
  
## <a name="to-obtain-the-trace-id"></a><span data-ttu-id="feeec-110">トレース ID を取得するには</span><span class="sxs-lookup"><span data-stu-id="feeec-110">To obtain the trace ID</span></span>  
  
1.  <span data-ttu-id="feeec-111">クエリ エディターで SQL トレース スクリプトを開き、スクリプトを実行してトレース セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="feeec-111">Open the SQL Trace script in Query Editor, and then execute the script to create the trace session.</span></span> <span data-ttu-id="feeec-112">この手順を実行するために必ずしもトレース セッションが実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="feeec-112">Note that the trace session does not need to be running to complete this procedure.</span></span>  
  
2.  <span data-ttu-id="feeec-113">トレースの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="feeec-113">Obtain the ID of the trace.</span></span> <span data-ttu-id="feeec-114">そのためには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="feeec-114">To do this, use the following query:</span></span>  
  
    ```sql
    SELECT * FROM sys.traces;  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="feeec-115">トレース ID 1 は通常、既定のトレースを示します。</span><span class="sxs-lookup"><span data-stu-id="feeec-115">Trace ID 1 typically indicates the default trace.</span></span>  
  
## <a name="to-determine-the-extended-events-equivalents"></a><span data-ttu-id="feeec-116">等価な拡張イベントを特定するには</span><span class="sxs-lookup"><span data-stu-id="feeec-116">To determine the Extended Events equivalents</span></span>  
  
1.  <span data-ttu-id="feeec-117">拡張イベントにおける等価なイベントとアクションを特定するには、次のクエリを実行します。 *trace_id* は、前の手順で取得したトレース ID の値に設定されています。</span><span class="sxs-lookup"><span data-stu-id="feeec-117">To determine the equivalent Extended Events events and actions, run the following query, where *trace_id* is set to the value of the trace ID that you obtained in the previous procedure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="feeec-118">この例では、既定のトレースの ID (1) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="feeec-118">In this example, the trace ID for the default trace (1) is used.</span></span>  
  
    ```sql
    USE MASTER;  
    GO  
    DECLARE @trace_id int;  
    SET @trace_id = 1;  
    SELECT DISTINCT el.eventid, em.package_name, em.xe_event_name AS 'event'  
       , el.columnid, ec.xe_action_name AS 'action'  
    FROM (sys.fn_trace_geteventinfo(@trace_id) AS el  
       LEFT OUTER JOIN sys.trace_xe_event_map AS em  
          ON el.eventid = em.trace_event_id)  
    LEFT OUTER JOIN sys.trace_xe_action_map AS ec  
       ON el.columnid = ec.trace_column_id  
    WHERE em.xe_event_name IS NOT NULL AND ec.xe_action_name IS NOT NULL;  
    ```  
  
     <span data-ttu-id="feeec-119">拡張イベントにおける等価なイベント ID、パッケージ名、イベント名、列 ID、およびアクション名が返されます。</span><span class="sxs-lookup"><span data-stu-id="feeec-119">The equivalent Extended Events event ID, package name, event name, column ID and action name are returned.</span></span> <span data-ttu-id="feeec-120">この出力結果は、このトピックの「拡張イベント セッションを作成するには」の手順で使用します。</span><span class="sxs-lookup"><span data-stu-id="feeec-120">You will use this output in the procedure "To create the Extended Events session" later in this topic.</span></span>  
  
     <span data-ttu-id="feeec-121">場合によっては、フィルター選択された列が、既定で含まれているイベント データ フィールドにマップされていることも考えられます。</span><span class="sxs-lookup"><span data-stu-id="feeec-121">In some cases, the filtered column maps to an event data field that is included by default in the Extended Events event.</span></span> <span data-ttu-id="feeec-122">このとき、"Extended_Events_action_name" 列は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="feeec-122">Therefore, the "Extended_Events_action_name" column will be NULL.</span></span> <span data-ttu-id="feeec-123">この場合、次の手順に従って、フィルター選択された列に対応するデータ フィールドを特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="feeec-123">If this occurs, you must do the following to determine which data field is equivalent to the filtered column:</span></span>  
  
    1.  <span data-ttu-id="feeec-124">NULL を返すアクションに関して、スクリプト内のどの SQL トレース イベント クラスに、フィルター選択の対象となる列が含まれているかを特定します。</span><span class="sxs-lookup"><span data-stu-id="feeec-124">For the actions that return NULL, identify which SQL Trace event classes in the script contain the column that is being filtered.</span></span>  
  
         <span data-ttu-id="feeec-125">たとえば、イベント クラス SP:StmtCompleted を使用し、トレース列名 Duration に対するフィルターを指定したとします (SQL トレース イベント クラス ID が 45 で、SQL トレースの列 ID が 13)。</span><span class="sxs-lookup"><span data-stu-id="feeec-125">For example, you may have used the SP:StmtCompleted event class, and specified a filter on the Duration trace column name (SQL Trace event class ID 45, and SQL Trace column ID 13).</span></span> <span data-ttu-id="feeec-126">この場合、クエリの結果には、アクション名が NULL として表示されます。</span><span class="sxs-lookup"><span data-stu-id="feeec-126">In this case, the action name will appear as NULL in the query results.</span></span>  
  
    2.  <span data-ttu-id="feeec-127">前の手順で特定した SQL トレース イベント クラスごとに、拡張イベントにおける等価なイベント名を探します。</span><span class="sxs-lookup"><span data-stu-id="feeec-127">For each SQL Trace event class that you identified in the previous step, find the equivalent Extended Events event name.</span></span> <span data-ttu-id="feeec-128">(等価なイベント名がわからない場合は、「 [SQL トレースのイベント クラスと等価な拡張イベントを確認する](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)」のトピックに記載されているクエリを使用してください。)。</span><span class="sxs-lookup"><span data-stu-id="feeec-128">(If you are not sure of the equivalent event name, use the query in the topic [View the Extended Events Equivalents to SQL Trace Event Classes](view-the-extended-events-equivalents-to-sql-trace-event-classes.md).)</span></span>  
  
    3.  <span data-ttu-id="feeec-129">次のクエリを使用して、前の手順で判明したイベントに使用する適切なデータ フィールドを特定します。</span><span class="sxs-lookup"><span data-stu-id="feeec-129">Use the following query to identify the correct data fields to use for the events that you identified in the previous step.</span></span> <span data-ttu-id="feeec-130">このクエリでは、拡張イベントのデータ フィールドが "event_field" 列に反映されます。</span><span class="sxs-lookup"><span data-stu-id="feeec-130">The query shows the Extended Events data fields in the "event_field" column.</span></span> <span data-ttu-id="feeec-131">クエリ内の *<event_name>* は、前の手順で指定したイベントの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="feeec-131">In the query, replace *<event_name>* with the name of an event that you specified in the previous step.</span></span>  
  
        ```sql
        SELECT xp.name package_name, xe.name event_name  
           ,xc.name event_field, xc.description  
        FROM sys.trace_xe_event_map AS em  
        INNER JOIN sys.dm_xe_objects AS xe  
           ON em.xe_event_name = xe.name  
        INNER JOIN sys.dm_xe_packages AS xp  
           ON xe.package_guid = xp.guid AND em.package_name = xp.name  
        INNER JOIN sys.dm_xe_object_columns AS xc  
           ON xe.name = xc.object_name  
        WHERE xe.object_type = 'event' AND xc.column_type <> 'readonly'  
           AND em.xe_event_name = '<event_name>';  
        ```  
  
         <span data-ttu-id="feeec-132">たとえば、SP:StmtCompleted イベント クラスは、sp_statement_completed 拡張イベントに対応します。</span><span class="sxs-lookup"><span data-stu-id="feeec-132">For example, the SP:StmtCompleted event class maps to the sp_statement_completed Extended Events event.</span></span> <span data-ttu-id="feeec-133">クエリの中で、イベント名として sp_statement_completed を指定した場合、そのイベントに既定で含まれているフィールドが "event_field" 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="feeec-133">If you specify sp_statement_completed as the event name in the query, the "event_field" column shows the fields that are included by default with the event.</span></span> <span data-ttu-id="feeec-134">これらのフィールドを見ると、"duration" というフィールドが存在するのがわかります。</span><span class="sxs-lookup"><span data-stu-id="feeec-134">Looking at the fields, you can see that there is a "duration" field.</span></span> <span data-ttu-id="feeec-135">等価な拡張イベント セッションにフィルターを作成するには、"WHERE duration > 0" などの述語を追加します。</span><span class="sxs-lookup"><span data-stu-id="feeec-135">To create the filter in the equivalent Extended Events session, you would add a predicate such as "WHERE duration > 0".</span></span> <span data-ttu-id="feeec-136">例については、このトピックの「拡張イベント セッションを作成するには」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="feeec-136">For an example, see the "To create the Extended Events session" procedure in this topic.</span></span>  
  
## <a name="to-create-the-extended-events-session"></a><span data-ttu-id="feeec-137">拡張イベント セッションを作成するには</span><span class="sxs-lookup"><span data-stu-id="feeec-137">To create the Extended Events session</span></span>  
 <span data-ttu-id="feeec-138">クエリ エディターを使用して拡張イベント セッションを作成し、出力結果をファイル ターゲットに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="feeec-138">Use Query Editor to create the Extended Events session, and to write the output to a file target.</span></span> <span data-ttu-id="feeec-139">以降の手順は、単一のクエリについて記述したものです。クエリの実際の作成方法を交えて説明しています。</span><span class="sxs-lookup"><span data-stu-id="feeec-139">The following steps describe a single query, with explanations to show you how to build the query.</span></span> <span data-ttu-id="feeec-140">クエリ全体の例については、このトピックの「使用例」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="feeec-140">For the full query example, see the "Example" section of this topic.</span></span>  
  
1.  <span data-ttu-id="feeec-141">イベント セッションを作成するためのステートメントを追加します。*session_name* の部分は、拡張イベント セッションに使用する名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="feeec-141">Add statements to create the event session, replacing s*ession_name* with the name that you want to use for the Extended Events session.</span></span>  
  
    ```sql
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
       DROP EVENT SESSION [Session_Name] ON SERVER;  
    CREATE EVENT SESSION [Session_Name]  
    ON SERVER;  
    ```  
  
2.  <span data-ttu-id="feeec-142">「等価な拡張イベントを特定するには」の手順の出力結果として返された拡張イベントのイベントとアクションを追加し、「スクリプトに使用されているフィルターを特定するには」の手順で特定した述語 (フィルター) を追加します。</span><span class="sxs-lookup"><span data-stu-id="feeec-142">Add the Extended Events events and actions that were returned as output in the procedure "Determine the Extended Events equivalents", and add the predicates (filters) that you identified in the procedure "To determine the filters that were used in the script".</span></span>  
  
     <span data-ttu-id="feeec-143">次の例には、SQL:StmtStarting イベント クラスと SP:StmtCompleted イベント クラス、さらに、セッションの ID と実行時間 (duration) のフィルターを含んだ SQL トレース スクリプトが使用されています。</span><span class="sxs-lookup"><span data-stu-id="feeec-143">The following example uses a SQL Trace script that includes the SQL:StmtStarting and SP:StmtCompleted event classes, with filters for session ID and duration.</span></span> <span data-ttu-id="feeec-144">「等価な拡張イベントを特定するには」の手順で紹介したクエリのサンプル出力では、次の結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="feeec-144">Sample output for the query in the "Determine the Extended Events equivalents" procedure returned the following result set:</span></span>  
  
    ```  
    Eventid  package_name  event                   columnid  action  
    44       sqlserver     sp_statement_starting   6         nt_username  
    44       sqlserver     sp_statement_starting   9         client_pid  
    44       sqlserver     sp_statement_starting   10        client_app_name  
    44       sqlserver     sp_statement_starting   11        server_principal_name  
    44       sqlserver     sp_statement_starting   12        session_id  
    45       sqlserver     sp_statement_completed  6         nt_username  
    45       sqlserver     sp_statement_completed  9         client_pid  
    45       sqlserver     sp_statement_completed  10        client_app_name  
    45       sqlserver     sp_statement_completed  11        server_principal_name  
    45       sqlserver     sp_statement_completed  12        session_id  
    ```  
  
     <span data-ttu-id="feeec-145">これを等価な拡張イベントに変換するには、sqlserver.sp_statement_starting イベントと sqlserver.sp_statement_completed events イベントを一連のアクションと共に追加します。</span><span class="sxs-lookup"><span data-stu-id="feeec-145">To convert this to the Extended Events equivalent, the sqlserver.sp_statement_starting and the sqlserver.sp_statement_completed events are added, with a list of actions.</span></span> <span data-ttu-id="feeec-146">述語のステートメントは、WHERE 句として追加されています。</span><span class="sxs-lookup"><span data-stu-id="feeec-146">Predicate statements are included as WHERE clauses.</span></span>  
  
    ```sql
    ADD EVENT sqlserver.sp_statement_starting  
       (ACTION  
          (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
          )  
       WHERE sqlserver.session_id = 59   
       ),  
  
    ADD EVENT sqlserver.sp_statement_completed  
       (ACTION  
          (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
          )  
       WHERE sqlserver.session_id = 59 AND duration > 0  
       )  
    ```  
  
3.  <span data-ttu-id="feeec-147">非同期のファイル ターゲットを追加します。ファイル パスは、出力結果の実際の保存場所に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="feeec-147">Add the asynchronous file target, replacing the file paths with the location where you want to save the output.</span></span> <span data-ttu-id="feeec-148">ファイル ターゲットを指定するときは、ログ ファイルとメタデータ ファイルのパス ファイルを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="feeec-148">When specifying the file target, you must include a log file and metadata file path file.</span></span>  
  
    ```sql
    ADD TARGET package0.asynchronous_file_target(  
       SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
    ```  
  
## <a name="to-view-the-results"></a><span data-ttu-id="feeec-149">結果を表示するには</span><span class="sxs-lookup"><span data-stu-id="feeec-149">To view the results</span></span>  
  
1.  <span data-ttu-id="feeec-150">出力結果は、sys.fn_xe_file_target_read_file 関数を使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="feeec-150">You can use the sys.fn_xe_file_target_read_file function to view the output.</span></span> <span data-ttu-id="feeec-151">そのためには、次のクエリを実行します。ファイル パスは、実際に指定したパスに置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="feeec-151">To do this, run the following query, replacing the file paths with the paths that you specified:</span></span>  
  
    ```sql
    SELECT *, CAST(event_data as XML) AS 'event_data_XML'  
    FROM sys.fn_xe_file_target_read_file('c:\temp\ExtendedEventsStoredProcs*.xel', 'c:\temp\ExtendedEventsStoredProcs*.xem', NULL, NULL);  
  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="feeec-152">イベント データを XML としてキャストしていますが、これは任意です。</span><span class="sxs-lookup"><span data-stu-id="feeec-152">Casting the event data as XML is optional.</span></span>  
  
     <span data-ttu-id="feeec-153">sys.fn_xe_file_target_read_file 関数の詳細については、「[sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="feeec-153">For more information about the sys.fn_xe_file_target_read_file function, see [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>  
  
    ```sql
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
       DROP EVENT SESSION [session_name] ON SERVER;  
    CREATE EVENT SESSION [session_name]  
    ON SERVER  
  
    ADD EVENT sqlserver.sp_statement_starting  
       (ACTION  
       (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
       )  
       WHERE sqlserver.session_id = 59   
       ),  
  
    ADD EVENT sqlserver.sp_statement_completed  
       (ACTION  
       (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
       )  
       WHERE sqlserver.session_id = 59 AND duration > 0  
       );  
  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
    ```  
  
## <a name="example"></a><span data-ttu-id="feeec-154">例</span><span class="sxs-lookup"><span data-stu-id="feeec-154">Example</span></span>  
  
```sql
IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
   DROP EVENT SESSION [session_name] ON SERVER;  
CREATE EVENT SESSION [session_name]  
ON SERVER  
  
ADD EVENT sqlserver.sp_statement_starting  
   (ACTION  
   (  
      sqlserver.nt_username,  
      sqlserver.client_pid,  
      sqlserver.client_app_name,  
      sqlserver.server_principal_name,  
      sqlserver.session_id  
   )  
   WHERE sqlserver.session_id = 59   
   ),  
  
ADD EVENT sqlserver.sp_statement_completed  
   (ACTION  
   (  
      sqlserver.nt_username,  
      sqlserver.client_pid,  
      sqlserver.client_app_name,  
      sqlserver.server_principal_name,  
      sqlserver.session_id  
   )  
   WHERE sqlserver.session_id = 59 AND duration > 0  
   )  
  
ADD TARGET package0.asynchronous_file_target  
   (SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
```  
  
## <a name="see-also"></a><span data-ttu-id="feeec-155">参照</span><span class="sxs-lookup"><span data-stu-id="feeec-155">See Also</span></span>  
 [<span data-ttu-id="feeec-156">SQL トレースのイベント クラスと等価な拡張イベントを確認する</span><span class="sxs-lookup"><span data-stu-id="feeec-156">View the Extended Events Equivalents to SQL Trace Event Classes</span></span>](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)  
  
  
