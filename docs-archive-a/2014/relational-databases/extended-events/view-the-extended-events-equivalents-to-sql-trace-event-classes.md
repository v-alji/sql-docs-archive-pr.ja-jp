---
title: SQL トレースのイベント クラスと等価な拡張イベントを確認する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, extended events equivalents
- extended events [SQL Server], SQL Trace equivalents
- extended events [SQL Server], user configurable events
ms.assetid: 7f24104c-201d-4361-9759-f78a27936011
author: rothja
ms.author: jroth
ms.openlocfilehash: 37459359f9f6cb7e3951b705c4007477ec43e36a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711922"
---
# <a name="view-the-extended-events-equivalents-to-sql-trace-event-classes"></a><span data-ttu-id="319ea-102">SQL トレースのイベント クラスと等価な拡張イベントを確認する</span><span class="sxs-lookup"><span data-stu-id="319ea-102">View the Extended Events Equivalents to SQL Trace Event Classes</span></span>
  <span data-ttu-id="319ea-103">拡張イベントを使用して、SQL トレース イベントのクラスや列に相当するイベント データを収集する場合、SQL トレース イベントが、拡張イベントのイベントおよびアクションとどのように対応しているかを理解しておくことが大切です。</span><span class="sxs-lookup"><span data-stu-id="319ea-103">If you want to use Extended Events to collect event data that is equivalent to SQL Trace event classes and columns, it is useful to understand how the SQL Trace events map to Extended Events events and actions.</span></span>  
  
 <span data-ttu-id="319ea-104">SQL トレースのイベントとそれに関連した列について、拡張イベントにおける等価なイベントとアクションを確認するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="319ea-104">You can use the following procedure to view the Extended Events events and actions that are equivalent to each SQL Trace event and its associated columns.</span></span>  
  
## <a name="to-view-the-extended-events-equivalents-to-sql-trace-events-using-query-editor"></a><span data-ttu-id="319ea-105">クエリ エディターを使用して SQL トレース イベントと等価な拡張イベントを確認するには</span><span class="sxs-lookup"><span data-stu-id="319ea-105">To view the Extended Events equivalents to SQL Trace events using Query Editor</span></span>  
  
-   <span data-ttu-id="319ea-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のクエリ エディターから、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="319ea-106">From Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], run the following query:</span></span>  
  
    ```  
    USE MASTER;  
    GO  
    SELECT DISTINCT  
       tb.trace_event_id,  
       te.name AS 'Event Class',  
       em.package_name AS 'Package',  
       em.xe_event_name AS 'XEvent Name',  
       tb.trace_column_id,  
       tc.name AS 'SQL Trace Column',  
       am.xe_action_name as 'Extended Events action'  
    FROM (sys.trace_events te LEFT OUTER JOIN sys.trace_xe_event_map em  
       ON te.trace_event_id = em.trace_event_id) LEFT OUTER JOIN sys.trace_event_bindings tb  
       ON em.trace_event_id = tb.trace_event_id LEFT OUTER JOIN sys.trace_columns tc  
       ON tb.trace_column_id = tc.trace_column_id LEFT OUTER JOIN sys.trace_xe_action_map am  
       ON tc.trace_column_id = am.trace_column_id  
    ORDER BY te.name, tc.name  
    ```  
  
 <span data-ttu-id="319ea-107">結果を確認する際は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="319ea-107">When you view the results, note the following:</span></span>  
  
-   <span data-ttu-id="319ea-108">イベント クラス列を除くすべての列で NULL が返された場合、そのイベント クラスは SQL トレースから移行されなかったことを意味します。</span><span class="sxs-lookup"><span data-stu-id="319ea-108">If all columns return NULL except for the Event Class column, this indicates that the event class was not migrated from SQL Trace.</span></span>  
  
-   <span data-ttu-id="319ea-109">拡張イベント アクション列の値のみが NULL である場合、次のいずれかの条件に該当します。</span><span class="sxs-lookup"><span data-stu-id="319ea-109">If only the value in the Extended Events action column is NULL, this indicates that either of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="319ea-110">SQL トレース列は、拡張イベントのイベントに関連付けられているいずれかのデータ フィールドに対応する。</span><span class="sxs-lookup"><span data-stu-id="319ea-110">The SQL Trace column maps to one of the data fields that is associated with the Extended Events event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="319ea-111">拡張イベントの各イベントは、結果セットに自動的に追加される既定のデータ フィールドのセットを持っています。</span><span class="sxs-lookup"><span data-stu-id="319ea-111">Each Extended Events event has a default set of data fields that are automatically included in the result set.</span></span>  
  
    -   <span data-ttu-id="319ea-112">アクション列には、意味のある等価な拡張イベントが存在しない。</span><span class="sxs-lookup"><span data-stu-id="319ea-112">The action column does not have a meaningful Extended Events equivalent.</span></span> <span data-ttu-id="319ea-113">たとえば、SQL トレースの EventClass 列がこれに該当します。</span><span class="sxs-lookup"><span data-stu-id="319ea-113">An example of this is the EventClass column in SQL Trace.</span></span> <span data-ttu-id="319ea-114">同じ目的はイベント名によって満たされるため、拡張イベントにこの列は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="319ea-114">This column is not needed in Extended Events because the event name serves the same purpose.</span></span>  
  
-   <span data-ttu-id="319ea-115">ユーザーが構成できる SQL トレースのイベント クラス (UserConfigurable:1 ～ UserConfigurable:9) は、拡張イベントでは単一のイベントに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="319ea-115">For user configurable SQL Trace event classes (UserConfigurable:1 through UserConfigurable:9), Extended Events uses a single event to replace these.</span></span> <span data-ttu-id="319ea-116">このイベントには、user_event という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="319ea-116">The event is named user_event.</span></span> <span data-ttu-id="319ea-117">このイベントは、SQL トレースと同じ sp_trace_generateevent ストアド プロシージャを使用して生成されます。</span><span class="sxs-lookup"><span data-stu-id="319ea-117">This event is raised by using sp_trace_generateevent, which is the same stored procedure that is used by SQL Trace.</span></span> <span data-ttu-id="319ea-118">user_event イベントは、ストアド プロシージャに渡されたイベント ID に関係なく返されます。</span><span class="sxs-lookup"><span data-stu-id="319ea-118">The user_event event is returned regardless of which event ID is passed to the stored procedure.</span></span> <span data-ttu-id="319ea-119">ただし、event_id フィールドは、イベント データの一部として返されます。</span><span class="sxs-lookup"><span data-stu-id="319ea-119">However, an event_id field is returned as part of the event data.</span></span> <span data-ttu-id="319ea-120">これによって、イベント ID に基づく述語の作成が可能となります。</span><span class="sxs-lookup"><span data-stu-id="319ea-120">This enables you to build a predicate that is based on the event ID.</span></span> <span data-ttu-id="319ea-121">たとえば、UserConfigurable:0 (イベント ID = 82) をコード内で使用する場合、user_event イベントをセッションに追加し、'event_id = 82' という述語を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="319ea-121">For example, if you use UserConfigurable:0 (event ID = 82) in the code, you can add the user_event event to the session, and specify a predicate of 'event_id = 82'.</span></span> <span data-ttu-id="319ea-122">拡張イベントの user_event イベントも SQL トレースにおける等価なイベント クラスも sp_trace_generateevent ストアド プロシージャによって生成されるため、コードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="319ea-122">Therefore, you do not have to change the code because the sp_trace_generateevent stored procedure generates the Extended Events user_event event, and the equivalent SQL Trace event class.</span></span>  
  
-   <span data-ttu-id="319ea-123">イベント クラス列を除くすべての列で NULL が返された場合、そのイベント クラスは SQL トレースから移行されなかったことを意味します。</span><span class="sxs-lookup"><span data-stu-id="319ea-123">If all columns return NULL except for the Event Class column, this indicates that the event class was not migrated from SQL Trace.</span></span>  
  
-   <span data-ttu-id="319ea-124">拡張イベント アクション列の値のみが NULL である場合、次のいずれかの条件に該当します。</span><span class="sxs-lookup"><span data-stu-id="319ea-124">If only the value in the Extended Events action column is NULL, this indicates that either of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="319ea-125">SQL トレース列は、拡張イベントのイベントに関連付けられているいずれかのデータ フィールドに対応する。</span><span class="sxs-lookup"><span data-stu-id="319ea-125">The SQL Trace column maps to one of the data fields that is associated with the Extended Events event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="319ea-126">拡張イベントの各イベントは、結果セットに自動的に追加される既定のデータ フィールドのセットを持っています。</span><span class="sxs-lookup"><span data-stu-id="319ea-126">Each Extended Events event has a default set of data fields that are automatically included in the result set.</span></span>  
  
    -   <span data-ttu-id="319ea-127">アクション列には、意味のある等価な拡張イベントが存在しない。</span><span class="sxs-lookup"><span data-stu-id="319ea-127">The action column does not have a meaningful Extended Events equivalent.</span></span> <span data-ttu-id="319ea-128">たとえば、SQL トレースの EventClass 列がこれに該当します。</span><span class="sxs-lookup"><span data-stu-id="319ea-128">An example of this is the EventClass column in SQL Trace.</span></span> <span data-ttu-id="319ea-129">同じ目的はイベント名によって満たされるため、拡張イベントにこの列は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="319ea-129">This column is not needed in Extended Events because the event name serves the same purpose.</span></span>  
  
-   <span data-ttu-id="319ea-130">ユーザーが構成できる SQL トレースのイベント クラス (UserConfigurable:1 ～ UserConfigurable:9) は、拡張イベントでは単一のイベントに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="319ea-130">For user configurable SQL Trace event classes (UserConfigurable:1 through UserConfigurable:9), Extended Events uses a single event to replace these.</span></span> <span data-ttu-id="319ea-131">このイベントには、user_event という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="319ea-131">The event is named user_event.</span></span> <span data-ttu-id="319ea-132">このイベントは、SQL トレースと同じ sp_trace_generateevent ストアド プロシージャを使用して生成されます。</span><span class="sxs-lookup"><span data-stu-id="319ea-132">This event is raised by using sp_trace_generateevent, which is the same stored procedure that is used by SQL Trace.</span></span> <span data-ttu-id="319ea-133">user_event イベントは、ストアド プロシージャに渡されたイベント ID に関係なく返されます。</span><span class="sxs-lookup"><span data-stu-id="319ea-133">The user_event event is returned regardless of which event ID is passed to the stored procedure.</span></span> <span data-ttu-id="319ea-134">ただし、event_id フィールドは、イベント データの一部として返されます。</span><span class="sxs-lookup"><span data-stu-id="319ea-134">However, an event_id field is returned as part of the event data.</span></span> <span data-ttu-id="319ea-135">これによって、イベント ID に基づく述語の作成が可能となります。</span><span class="sxs-lookup"><span data-stu-id="319ea-135">This enables you to build a predicate that is based on the event ID.</span></span> <span data-ttu-id="319ea-136">たとえば、UserConfigurable:0 (イベント ID = 82) をコード内で使用する場合、user_event イベントをセッションに追加し、'event_id = 82' という述語を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="319ea-136">For example, if you use UserConfigurable:0 (event ID = 82) in the code, you can add the user_event event to the session, and specify a predicate of 'event_id = 82'.</span></span> <span data-ttu-id="319ea-137">拡張イベントの user_event イベントも SQL トレースにおける等価なイベント クラスも sp_trace_generateevent ストアド プロシージャによって生成されるため、コードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="319ea-137">Therefore, you do not have to change the code because the sp_trace_generateevent stored procedure generates the Extended Events user_event event, and the equivalent SQL Trace event class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319ea-138">参照</span><span class="sxs-lookup"><span data-stu-id="319ea-138">See Also</span></span>  
 [<span data-ttu-id="319ea-139">sp_trace_generateevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="319ea-139">sp_trace_generateevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)  
  
  
