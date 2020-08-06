---
title: クエリエディターを使用して拡張イベントセッションを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- create extended events session
- extended events [SQL Server], create session
ms.assetid: cba0e02b-b201-4863-bf1b-9164e68e5fa8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 648370ecdd2938b6fb425955dc02da8960f884c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641222"
---
# <a name="create-an-extended-events-session-using-query-editor"></a><span data-ttu-id="c4aea-102">クエリ エディターを使用した拡張イベント セッションの作成</span><span class="sxs-lookup"><span data-stu-id="c4aea-102">Create an Extended Events Session Using Query Editor</span></span>
  <span data-ttu-id="c4aea-103">拡張イベント セッションを作成するには、クエリ エディターを使用するか、オブジェクト エクスプローラーでセッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-103">You can create an Extended Events session by using the Query Editor, or you can create a session in Object Explorer.</span></span> <span data-ttu-id="c4aea-104">オブジェクトエクスプローラーでは、拡張イベントに2つのユーザーインターフェイスが用意されています。このウィザードでは、イベントセッションの作成プロセスを案内するウィザードと、より高度な構成オプションを提供する新しいセッション UI を作成、変更、および表示するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-104">In Object Explorer, Extended Events provides two user interfaces you can use to create, modify, and view event session data - a wizard that guides you through the event session creation process, and a New Session UI that provides more advanced configuration options.</span></span> <span data-ttu-id="c4aea-105">拡張イベント セッションを作成して SQL Server のトレースを診断できます。これにより次のような問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-105">You can create Extended Events sessions to diagnose SQL Server tracing, which enables you to resolve issues such as the following:</span></span>  
  
-   <span data-ttu-id="c4aea-106">最も高価なクエリを見つける</span><span class="sxs-lookup"><span data-stu-id="c4aea-106">Find your most expensive queries</span></span>  
  
-   <span data-ttu-id="c4aea-107">ラッチ競合の根本的な原因を見つける</span><span class="sxs-lookup"><span data-stu-id="c4aea-107">Find root causes of latch contention</span></span>  
  
-   <span data-ttu-id="c4aea-108">他のクエリをブロックしているクエリを見つける</span><span class="sxs-lookup"><span data-stu-id="c4aea-108">Find a query that is blocking other queries</span></span>  
  
-   <span data-ttu-id="c4aea-109">クエリの再コンパイルにより、過剰な CPU 使用率をトラブルシューティングする</span><span class="sxs-lookup"><span data-stu-id="c4aea-109">Troubleshoot excessive CPU usage caused by query recompilation</span></span>  
  
-   <span data-ttu-id="c4aea-110">デッドロックのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c4aea-110">Troubleshoot deadlocks</span></span>  
  
 <span data-ttu-id="c4aea-111">新規セッション ウィザードを使用して拡張イベント セッションを作成する方法については、「[ウィザードを使用した拡張イベント セッションの作成 &#40;オブジェクト エクスプローラー&#41;](../ssms/object/object-explorer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-111">For information about how to create an Extended Events session using the New Session Wizard, see [Create an Extended Events Session Using the Wizard &#40;Object Explorer&#41;](../ssms/object/object-explorer.md).</span></span> <span data-ttu-id="c4aea-112">[新しいセッション] UI を使用して拡張イベント セッションを作成する方法については、「[[新しいセッション] ダイアログを使用した拡張イベント セッションの作成](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-112">For information about how to create an Extended Events session using the New Session UI, see [Create an Extended Events Session Using the New Session Dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md).</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4aea-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="c4aea-113">Permissions</span></span>  
 <span data-ttu-id="c4aea-114">拡張イベント セッションを作成するには、ALTER ANY EVENT SESSION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c4aea-114">To create an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
## <a name="creating-an-extended-events-session-using-query-editor"></a><span data-ttu-id="c4aea-115">クエリ エディターを使用した拡張イベント セッションの作成</span><span class="sxs-lookup"><span data-stu-id="c4aea-115">Creating an Extended Events session using Query Editor</span></span>  
  
#### <a name="to-create-an-extended-events-session"></a><span data-ttu-id="c4aea-116">拡張イベント セッションを作成するには</span><span class="sxs-lookup"><span data-stu-id="c4aea-116">To create an Extended Events session</span></span>  
  
1.  <span data-ttu-id="c4aea-117">次の手順は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のクエリ エディターを使用して拡張イベント セッションを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c4aea-117">The following procedure shows how to create an Extended Events session by using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="c4aea-118">セッションに使用するイベントを決めます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-118">Determine which events that you want to use in the session.</span></span> <span data-ttu-id="c4aea-119">利用可能なすべてのイベントをキーワードおよびチャネルと併せて表示するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-119">To see all the events that are available, together with the keyword and channel, use the following query:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4aea-120">キーワードおよびチャネルの詳細については、「 [SQL Server 拡張イベント パッケージ](../relational-databases/extended-events/sql-server-extended-events-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-120">For information about keywords and channels, see [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).</span></span>  
  
    ```  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
       (  
       SELECT event_package = o.package_guid, o.description,   
       event=c.object_name, channel = v.map_value  
       FROM sys.dm_xe_objects o  
       LEFT JOIN sys.dm_xe_object_columns c ON o.name = c.object_name  
       INNER JOIN sys.dm_xe_map_values v ON c.type_name = v.name   
       AND c.column_value = cast(v.map_key AS nvarchar)  
       WHERE object_type = 'event' AND (c.name = 'CHANNEL' or c.name IS NULL)  
       ) c LEFT JOIN   
       (  
       SELECT event_package = c.object_package_guid, event = c.object_name,   
       keyword = v.map_value  
       FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
       ON c.type_name = v.name AND c.column_value = v.map_key   
       AND c.type_package_guid = v.object_package_guid  
       INNER JOIN sys.dm_xe_objects o ON o.name = c.object_name   
       AND o.package_guid = c.object_package_guid  
       WHERE object_type = 'event' AND c.name = 'KEYWORD'   
       ) k  
       ON  
       k.event_package = c.event_package AND (k.event=c.event or k.event IS NULL)  
       INNER JOIN sys.dm_xe_packages p ON p.guid = c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
2.  <span data-ttu-id="c4aea-121">新しいクエリ ウィンドウで、イベント セッションを作成するためのステートメントを追加します。 *session_name* の部分は、使用するセッションの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-121">In a new query window, add the following statements to create an event session, replacing *session_name* with the session name that you want to use:</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c4aea-122">手順 2. ～ 6. は、イベント セッションの定義を断片的に記述しています。</span><span class="sxs-lookup"><span data-stu-id="c4aea-122">Steps 2 through 6 of this procedure describe each section of the event session definition.</span></span> <span data-ttu-id="c4aea-123">実際には、すべてのステートメントを単一のクエリ ウィンドウに追加してから実行することになります。</span><span class="sxs-lookup"><span data-stu-id="c4aea-123">You would add all the statements to a single query window before executing.</span></span> <span data-ttu-id="c4aea-124">サンプル全体については、このトピックの「使用例」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-124">For a full example, see the Example section of this topic.</span></span>  
  
    ```  
    CREATE EVENT SESSION session_name   
    ON SERVER  
    ```  
  
3.  <span data-ttu-id="c4aea-125">監視するイベントを *package_name*.*event_name*の形式で追加します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-125">Add the events that you want to monitor, in the format *package_name*.*event_name*.</span></span> <span data-ttu-id="c4aea-126">各イベントについて、次のような行を追加します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-126">For each event, add a line similar to the following:</span></span>  
  
    ```  
    ADD EVENT package_name.event_name  
    ```  
  
     <span data-ttu-id="c4aea-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-127">For example:</span></span>  
  
    ```  
    ADD EVENT sqlserver.file_read_completed,  
    ADD EVENT sqlserver.file_write_completed  
    ```  
  
4.  <span data-ttu-id="c4aea-128">(省略可能) イベントを追加すると、実行するアクションを追加できます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-128">(Optional) After you add an event, you can add actions to take.</span></span> <span data-ttu-id="c4aea-129">また、述語を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-129">You can also add predicates.</span></span> <span data-ttu-id="c4aea-130">述語は、イベント情報がどのようなときにターゲットによって消費されるかの基準を確立する目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-130">Predicates are used to establish criteria for when the event information should be consumed by the target.</span></span> <span data-ttu-id="c4aea-131">アクションは、ACTION 句を使用して追加します。述語は、WHERE 句を使用して追加します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-131">Actions are added by using an ACTION clause, and predicates are added by using a WHERE clause.</span></span> <span data-ttu-id="c4aea-132">たとえば、sqlserver.file_read_completed イベントについて、ファイル ID が 1 と等しいときに [!INCLUDE[tsql](../includes/tsql-md.md)] テキストをキャプチャするようなアクションと述語を追加するには、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-132">For example, to add an action and predicate where the [!INCLUDE[tsql](../includes/tsql-md.md)] text is captured for the sqlserver.file_read_completed event, where the file ID equals 1, you would include the following statement:</span></span>  
  
    ```  
    ADD EVENT sqlserver.file_read_completed  
       (ACTION (sqlserver.sql_text)  
       WHERE file_id = 1),  
    ```  
  
    -   <span data-ttu-id="c4aea-133">利用可能なアクションを表示するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-133">To view which actions are available, use the following query:</span></span>  
  
        ```  
        SELECT p.name AS 'package_name', xo.name AS 'action_name', xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'action'  
        AND (xo.capabilities & 1 = 0   
        OR xo.capabilities IS NULL)  
        ORDER BY p.name, xo.name  
        ```  
  
    -   <span data-ttu-id="c4aea-134">イベントに対して利用可能な述語を表示するには、次のクエリを使用します。 *event_name* の部分は、述語の追加対象となるイベントの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-134">To view which predicates are available for an event, use the following query, replacing *event_name* with the name of the event for which you want to add a predicate:</span></span>  
  
        ```  
        SELECT *  
        FROM sys.dm_xe_object_columns  
        WHERE object_name = 'event_name'  
        AND column_type = 'data'  
        ```  
  
         <span data-ttu-id="c4aea-135">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-135">For example:</span></span>  
  
        ```  
        SELECT *   
        FROM sys.dm_xe_object_columns   
        WHERE object_name = 'file_read_completed'  
        AND column_type = 'data'  
        ```  
  
         <span data-ttu-id="c4aea-136">グローバル述語ソースを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-136">Be aware that you can also add global predicate sources.</span></span> <span data-ttu-id="c4aea-137">グローバル述語ソースは、あらゆる述語式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-137">A global predicate source can be used in any predicate expression.</span></span> <span data-ttu-id="c4aea-138">利用可能なグローバル述語ソースを表示するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-138">To view which global predicate sources are available, use the following query:</span></span>  
  
        ```  
        SELECT p.name AS package_name, xo.name AS predicate_name  
           , xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'pred_source'  
        ORDER BY p.name, xo.name  
        ```  
  
         <span data-ttu-id="c4aea-139">たとえば、次の述語式を使用すると、最初の 5 回の発生に限定してイベント データを収集することができます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-139">For example, you could use the following predicate expression to specify that data should only be collected for an event the first five times that an event occurs.</span></span>  
  
        ```  
        WHERE package0.counter <= 5  
        ```  
  
5.  <span data-ttu-id="c4aea-140">適切なターゲットを追加します。イベント データはターゲットで処理され、消費されます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-140">Add the desired target, where the event data will be processed and consumed.</span></span> <span data-ttu-id="c4aea-141">次の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-141">Use the following format:</span></span>  
  
    ```  
    ADD TARGET package_name.target_name  
    ```  
  
     <span data-ttu-id="c4aea-142">次の例では、非同期のファイル ターゲットを追加します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-142">The following example adds the asynchronous file target:</span></span>  
  
    ```  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
    ```  
  
     <span data-ttu-id="c4aea-143">利用可能なターゲットを一覧表示するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-143">To view the list of available targets, use the following query:</span></span>  
  
    ```  
    SELECT p.name AS 'package_name', xo.name AS 'target_name'  
       , xo.description, xo.object_type   
    FROM sys.dm_xe_objects AS xo  
    JOIN sys.dm_xe_packages AS p  
       ON xo.package_guid = p.guid  
    WHERE xo.object_type = 'target'  
    AND (xo.capabilities & 1 = 0  
    OR xo.capabilities IS NULL)  
    ORDER BY p.name, xo.name  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4aea-144">ターゲットの種類については、「 [SQL Server 拡張イベント ターゲット](../../2014/database-engine/sql-server-extended-events-targets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-144">For information about the different target types, see [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).</span></span>  
  
6.  <span data-ttu-id="c4aea-145">他にも必要な構成オプションがあれば、確認して追加します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-145">Review and add any additional configuration options.</span></span> <span data-ttu-id="c4aea-146">たとえば、イベント保存モード、イベントをメモリにバッファリングする時間、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の起動時にイベント セッションを自動的に開始するかどうかなどのオプションを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-146">For example, you can configure options such as the event retention mode, how long events are buffered in memory, or whether the event session should start automatically when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="c4aea-147">これらのオプションについては、「[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)」のトピックに説明があります。</span><span class="sxs-lookup"><span data-stu-id="c4aea-147">The options are described in the topic [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql).</span></span> <span data-ttu-id="c4aea-148">これらのオプションを指定しなかった場合は、既定値が割り当てられる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-148">Be aware that default values are assigned if these options are not specified.</span></span>  
  
7.  <span data-ttu-id="c4aea-149">セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="c4aea-149">Start the session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4aea-150">セッションの結果を表示する方法の詳細については、オンライン ブックの「 [SQL Server 拡張イベント ターゲット](../../2014/database-engine/sql-server-extended-events-targets.md) 」ノードで、使用しているターゲットの種類に応じたトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4aea-150">For more information about how to view the session results, see the corresponding topic for the target type that you used in the [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) node of Books Online.</span></span>  
  
 <span data-ttu-id="c4aea-151">次の例では、IOActivity という名前の拡張イベント セッションを作成します。キャプチャする情報は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c4aea-151">The following example creates an Extended Events session named IOActivity that captures the following information:</span></span>  
  
-   <span data-ttu-id="c4aea-152">ファイル読み取り完了イベントのデータ (関連付けられている [!INCLUDE[tsql](../includes/tsql-md.md)] テキストを含む)。ファイル ID が 1 に等しいファイルの読み取りが対象となります。</span><span class="sxs-lookup"><span data-stu-id="c4aea-152">Event data for completed file reads, including the associated [!INCLUDE[tsql](../includes/tsql-md.md)] text for file reads where the file ID is equal to 1.</span></span>  
  
-   <span data-ttu-id="c4aea-153">ファイル書き込み完了イベントのデータ。</span><span class="sxs-lookup"><span data-stu-id="c4aea-153">Event data for completed file writes.</span></span>  
  
-   <span data-ttu-id="c4aea-154">ログ キャッシュ内のデータが物理ログ ファイルに書き込まれたときに発生するイベントのデータ。</span><span class="sxs-lookup"><span data-stu-id="c4aea-154">Event data for when data is written from the log cache to the physical log file.</span></span>  
  
 <span data-ttu-id="c4aea-155">このセッションでは、出力結果がファイル ターゲットに送信されます。</span><span class="sxs-lookup"><span data-stu-id="c4aea-155">The session sends the output to a file target.</span></span>  
  
```  
CREATE EVENT SESSION IOActivity  
ON SERVER  
  
ADD EVENT sqlserver.file_read_completed  
   (  
   ACTION (sqlserver.sql_text)  
   WHERE file_id = 1),  
ADD EVENT sqlserver.file_write_completed,  
ADD EVENT sqlserver.databases_log_flush  
  
ADD TARGET package0.asynchronous_file_target   
   (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4aea-156">参照</span><span class="sxs-lookup"><span data-stu-id="c4aea-156">See Also</span></span>  
 <span data-ttu-id="c4aea-157">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4aea-157">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="c4aea-158">[SQL Server 拡張イベント ターゲット](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="c4aea-158">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 [<span data-ttu-id="c4aea-159">SQL Server 拡張イベント パッケージ</span><span class="sxs-lookup"><span data-stu-id="c4aea-159">SQL Server Extended Events Packages</span></span>](../relational-databases/extended-events/sql-server-extended-events-packages.md)  
  
  
