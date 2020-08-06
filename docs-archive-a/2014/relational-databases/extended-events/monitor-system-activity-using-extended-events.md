---
title: 拡張イベントを使用したシステムの使用状況の監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- extended events [SQL Server], monitoring system activity
ms.assetid: d83ad88f-818c-49fe-a9a9-299f704fca53
author: rothja
ms.author: jroth
ms.openlocfilehash: d847d156d8244ede533e684c9e6b753d7d7b5047
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631922"
---
# <a name="monitor-system-activity-using-extended-events"></a><span data-ttu-id="08736-102">拡張イベントを使用したシステムの使用状況の監視</span><span class="sxs-lookup"><span data-stu-id="08736-102">Monitor System Activity Using Extended Events</span></span>
  <span data-ttu-id="08736-103">この手順は、拡張イベントを Event Tracing for Windows (ETW) と共に使用してシステムの使用状況を監視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="08736-103">This procedure illustrates how Extended Events can be used with Event Tracing for Windows (ETW) to monitor system activity.</span></span> <span data-ttu-id="08736-104">また、CREATE EVENT SESSION、ALTER EVENT SESSION、DROP EVENT SESSION の各ステートメントの使用方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="08736-104">The procedure also shows how the CREATE EVENT SESSION, ALTER EVENT SESSION, and DROP EVENT SESSION statements are used.</span></span>  
  
 <span data-ttu-id="08736-105">この作業には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用した次の手順の実行も含まれます。</span><span class="sxs-lookup"><span data-stu-id="08736-105">Accomplishing these tasks involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span> <span data-ttu-id="08736-106">この手順では、コマンド プロンプトを使用して ETW コマンドを実行することも必要です。</span><span class="sxs-lookup"><span data-stu-id="08736-106">The procedure also requires using the command prompt to run ETW commands.</span></span>  
  
### <a name="to-monitor-system-activity-using-extended-events"></a><span data-ttu-id="08736-107">拡張イベントを使用してシステムの使用状況を監視するには</span><span class="sxs-lookup"><span data-stu-id="08736-107">To monitor system activity using Extended Events</span></span>  
  
1.  <span data-ttu-id="08736-108">クエリ エディターで次のステートメントを実行してイベント セッションを作成し、2 つのイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="08736-108">In Query Editor, issue the following statements to create an event session and add two events.</span></span> <span data-ttu-id="08736-109">checkpoint_begin と checkpoint_end のイベントは、データベース チェックポイントの開始時と終了時に起動されます。</span><span class="sxs-lookup"><span data-stu-id="08736-109">These events, checkpoint_begin and checkpoint_end, fire at the beginning and end of a database checkpoint.</span></span>  
  
    ```  
    CREATE EVENT SESSION test0  
    ON SERVER  
    ADD EVENT sqlserver.checkpoint_begin,  
    ADD EVENT sqlserver.checkpoint_end  
    WITH (MAX_DISPATCH_LATENCY = 1 SECONDS)  
    go  
    ```  
  
2.  <span data-ttu-id="08736-110">32 バケットのバケット ターゲットを追加して、データベース ID に基づいたチェックポイントの数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="08736-110">Add the bucketing target with 32 buckets to count the number of checkpoints based on the database ID.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.histogram  
    (  
          SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id'  
    )  
    go  
    ```  
  
3.  <span data-ttu-id="08736-111">次のステートメントを実行して ETW ターゲットを追加します。</span><span class="sxs-lookup"><span data-stu-id="08736-111">Issue the following statements to add the ETW target.</span></span> <span data-ttu-id="08736-112">こうすると開始イベントと終了イベントを表示できるので、これを使用してチェックポイントの所要時間を判断できます。</span><span class="sxs-lookup"><span data-stu-id="08736-112">This will enable you to see the begin and end events, which is used to determine how long the checkpoint takes.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.etw_classic_sync_target  
    go  
    ```  
  
4.  <span data-ttu-id="08736-113">次のステートメントを実行してセッションを開始し、イベント コレクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="08736-113">Issue the following statements to start the session and begin event collection.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = start  
    go  
    ```  
  
5.  <span data-ttu-id="08736-114">次のステートメントを実行して 3 つのイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="08736-114">Issue the following statements to cause three events to fire.</span></span>  
  
    ```  
    USE tempdb  
          checkpoint  
    go  
    USE master  
          checkpoint  
          checkpoint  
    go  
    ```  
  
6.  <span data-ttu-id="08736-115">次のステートメントを実行してイベント カウントを表示します。</span><span class="sxs-lookup"><span data-stu-id="08736-115">Issue the following statements to view the event counts.</span></span>  
  
    ```  
    SELECT CAST(xest.target_data AS xml) Bucketizer_Target_Data_in_XML  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'test0'  
    go  
    ```  
  
7.  <span data-ttu-id="08736-116">コマンド プロンプトで、次のコマンドを実行すると ETW のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08736-116">At the command prompt, issue the following commands to view the ETW data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08736-117">**tracerpt** コマンドのヘルプを表示するには、コマンド プロンプトで「 `tracerpt /?`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="08736-117">To get help for the **tracerpt** command, at the command prompt, enter `tracerpt /?`.</span></span>  
  
    ```  
    logman query -ets --- List the ETW sessions. This is optional.  
    logman update XE_DEFAULT_ETW_SESSION -fd -ets --- Flush the ETW log.  
    tracerpt %temp%\xeetw.etl -o xeetw.txt --- Dump the events so they can be seen.  
    ```  
  
8.  <span data-ttu-id="08736-118">次のステートメントを実行してイベント セッションを停止し、サーバーから削除します。</span><span class="sxs-lookup"><span data-stu-id="08736-118">Issue the following statements to stop the event session and remove it from the server.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = STOP  
    go  
  
    DROP EVENT SESSION test0  
    ON SERVER  
    go  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="08736-119">参照</span><span class="sxs-lookup"><span data-stu-id="08736-119">See Also</span></span>  
 <span data-ttu-id="08736-120">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="08736-120">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="08736-121">[Transact-sql&#41;&#40;のイベントセッションの変更](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="08736-121">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 <span data-ttu-id="08736-122">[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="08736-122">[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="08736-123">拡張イベント カタログ ビュー &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08736-123">Extended Events Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql)  
 <span data-ttu-id="08736-124">[拡張イベントの動的管理ビュー](../views/views.md) </span><span class="sxs-lookup"><span data-stu-id="08736-124">[Extended Events Dynamic Management Views](../views/views.md) </span></span>  
 [<span data-ttu-id="08736-125">SQL Server 拡張イベント ターゲット</span><span class="sxs-lookup"><span data-stu-id="08736-125">SQL Server Extended Events Targets</span></span>](../../database-engine/sql-server-extended-events-targets.md)  
  
  
