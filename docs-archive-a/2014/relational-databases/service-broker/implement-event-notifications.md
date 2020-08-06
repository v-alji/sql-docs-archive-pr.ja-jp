---
title: イベント通知の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], target service
- target service [SQL Server]
- event notifications [SQL Server], creating
ms.assetid: 29ac8f68-a28a-4a77-b67b-a8663001308c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a89c66ca5c3b420fff14c087bd604b16c641369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641569"
---
# <a name="implement-event-notifications"></a><span data-ttu-id="943cc-102">イベント通知の実装</span><span class="sxs-lookup"><span data-stu-id="943cc-102">Implement Event Notifications</span></span>
  <span data-ttu-id="943cc-103">イベント通知を実装するには、最初にイベント通知を受け取る通知先サービスを作成してから、イベント通知を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="943cc-103">To implement an event notification, you must first create a target service to receive event notifications, and then create the event notification.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="943cc-104">ダイアログ セキュリティを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="943cc-104">dialog security should be configured for event notifications that send messages to a service broker on a remote server.</span></span> <span data-ttu-id="943cc-105">ダイアログ セキュリティは完全なセキュリティ モデルに基づいて手動で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="943cc-105">Dialog security must be configured manually according to the full security model.</span></span>  
  
## <a name="creating-the-target-service"></a><span data-ttu-id="943cc-106">通知先サービスの作成</span><span class="sxs-lookup"><span data-stu-id="943cc-106">Creating the Target Service</span></span>  
 <span data-ttu-id="943cc-107">[!INCLUDE[ssSB](../../includes/sssb-md.md)]には次の特定のメッセージ型とイベント通知用コントラクトがあるため、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] によって開始されるサービスを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="943cc-107">You do not have to create a [!INCLUDE[ssSB](../../includes/sssb-md.md)]-initiating service because [!INCLUDE[ssSB](../../includes/sssb-md.md)] includes the following specific message type and contract for event notifications:</span></span>  
  
```  
https://schemas.microsoft.com/SQL/Notifications/PostEventNotification  
```  
  
 <span data-ttu-id="943cc-108">イベント通知を受け取る対象サービスは、この既存のコントラクトに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="943cc-108">The target service that receives event notifications must honor this preexisting contract.</span></span>  
  
 <span data-ttu-id="943cc-109">**通知先サービスを作成するには**:</span><span class="sxs-lookup"><span data-stu-id="943cc-109">**To create a target service**:</span></span>  
  
1.  <span data-ttu-id="943cc-110">メッセージを受信するキューを作成します。</span><span class="sxs-lookup"><span data-stu-id="943cc-110">Create a queue to receive messages.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="943cc-111">キューでは、 `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`で定義されているメッセージ型が受信されます。</span><span class="sxs-lookup"><span data-stu-id="943cc-111">The queue receives the following message type: `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`.</span></span>  
  
2.  <span data-ttu-id="943cc-112">このキューにイベント通知コントラクトを参照するサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="943cc-112">Create a service on the queue that references the event notifications contract.</span></span>  
  
3.  <span data-ttu-id="943cc-113">サービスにルートを作成し、そのサービスに対するメッセージを [!INCLUDE[ssSB](../../includes/sssb-md.md)] から送信する送信先のアドレスを定義します。</span><span class="sxs-lookup"><span data-stu-id="943cc-113">Create a route on the service to define the address to which [!INCLUDE[ssSB](../../includes/sssb-md.md)] sends messages for the service.</span></span> <span data-ttu-id="943cc-114">イベント通知の送信先が同じデータベース内のサービスの場合は、 `ADDRESS = 'LOCAL'`を指定します。</span><span class="sxs-lookup"><span data-stu-id="943cc-114">For event notifications that target a service in the same database, specify `ADDRESS = 'LOCAL'`.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="943cc-115">のルーティングにより、通知メッセージを受け取るサービスが特定されます。</span><span class="sxs-lookup"><span data-stu-id="943cc-115">routing determines the service that receives the notification messages.</span></span> <span data-ttu-id="943cc-116">イベント通知の通知先がリモート サーバーのサービスの場合、ソース サーバーとターゲット サーバーの両方でルートを定義し、双方向の通信を確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="943cc-116">If the event notification targets a service on a remote server, both the source server and the target server must have routes defined on them to make sure that two-way communication occurs.</span></span>  
  
 <span data-ttu-id="943cc-117">次に、キューを作成し、そのキューにサービスを作成し、そのサービスのルートを作成して、イベント通知コントラクトからのメッセージを処理する例を示します。</span><span class="sxs-lookup"><span data-stu-id="943cc-117">The following example creates a queue, a service on the queue, and a route on the service to handle messages from the event notification contract.</span></span>  
  
```  
CREATE QUEUE NotifyQueue ;  
GO  
CREATE SERVICE NotifyService  
ON QUEUE NotifyQueue  
(  
[https://schemas.microsoft.com/SQL/Notifications/PostEventNotification]  
);  
GO  
CREATE ROUTE NotifyRoute  
WITH SERVICE_NAME = 'NotifyService',  
ADDRESS = 'LOCAL';  
GO  
```  
  
## <a name="creating-the-event-notification"></a><span data-ttu-id="943cc-118">イベント通知の作成</span><span class="sxs-lookup"><span data-stu-id="943cc-118">Creating the Event Notification</span></span>  
 <span data-ttu-id="943cc-119">イベント通知の作成には [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION ステートメントを、削除には DROP EVENT NOTIFICATION ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="943cc-119">Event notifications are created by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION statement, and are dropped by using the DROP EVENT NOTIFICATION STATEMENT.</span></span> <span data-ttu-id="943cc-120">イベント通知を変更するには、イベント通知を削除して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="943cc-120">To modify an event notification, you must drop and re-create the event notification.</span></span>  
  
 <span data-ttu-id="943cc-121">次の例では、イベント通知 `CreateDatabaseNotification`を作成します。</span><span class="sxs-lookup"><span data-stu-id="943cc-121">The following example creates the event notification `CreateDatabaseNotification`.</span></span> <span data-ttu-id="943cc-122">この通知は、サーバー上で発生するすべての `CREATE_DATABASE` イベントに関するメッセージを、以前に作成した `NotifyService` サービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="943cc-122">This notification sends a message about any `CREATE_DATABASE` event that occurs on the server to the `NotifyService` service that was previously created.</span></span>  
  
```  
CREATE EVENT NOTIFICATION CreateDatabaseNotification  
ON SERVER  
FOR CREATE_DATABASE  
TO SERVICE 'NotifyService', '8140a771-3c4b-4479-8ac0-81008ab17984' ;  
```  
  
> [!CAUTION]  
>  <span data-ttu-id="943cc-123">イベント通知では、CREATE_SCHEMA イベントと、CREATE SCHEMA ステートメントの <schema_element> 定義を別々のイベントとして認識します。</span><span class="sxs-lookup"><span data-stu-id="943cc-123">Event notifications recognize CREATE_SCHEMA events and the <schema_element> definitions of CREATE SCHEMA statements as separate events.</span></span> <span data-ttu-id="943cc-124">たとえば、CREATE_SCHEMA イベントと CREATE_TABLE イベントの両方でイベント通知が作成され、次のバッチを実行します。</span><span class="sxs-lookup"><span data-stu-id="943cc-124">For example, an event notification is created on both the CREATE_SCHEMA and CREATE_TABLE events, and you run the following batch.</span></span>  
>   
>  `CREATE SCHEMA s`  
>   
>  `CREATE TABLE t1 (col1 int)`  
>   
>  <span data-ttu-id="943cc-125">この場合イベント通知は、CREATE_SCHEMA イベントの発生時に 1 回、CREATE_TABLE イベントの発生時にもう 1 回、合計 2 回発生します。</span><span class="sxs-lookup"><span data-stu-id="943cc-125">In this case, the event notification is raised two times: Onne time when the CREATE_SCHEMA event occurs, and again when the CREATE_TABLE event occurs.</span></span> <span data-ttu-id="943cc-126">CREATE_SCHEMA イベントと、対応するすべての CREATE SCHEMA 定義の <schema_element> テキストの両方でイベント通知が作成されないようにするか、または不要なイベント データのキャプチャを防止するためのロジックをアプリケーションに組み込むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="943cc-126">We recommend that you either avoid creating event notifications on both the CREATE_SCHEMA events and the <schema_element> texts of any corresponding CREATE SCHEMA definitions, or build logic into your application to avoid capturing unwanted event data.</span></span>  
  
 <span data-ttu-id="943cc-127">**イベント通知を作成するには**</span><span class="sxs-lookup"><span data-stu-id="943cc-127">**To create an event notification**</span></span>  
  
-   [<span data-ttu-id="943cc-128">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="943cc-128">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-notification-transact-sql)  
  
 <span data-ttu-id="943cc-129">**イベント通知を削除するには**</span><span class="sxs-lookup"><span data-stu-id="943cc-129">**To drop an event notification**</span></span>  
  
-   [<span data-ttu-id="943cc-130">DROP EVENT NOTIFICATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="943cc-130">DROP EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-event-notification-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="943cc-131">参照</span><span class="sxs-lookup"><span data-stu-id="943cc-131">See Also</span></span>  
 <span data-ttu-id="943cc-132">[イベント通知に関する情報の取得](event-notifications.md) </span><span class="sxs-lookup"><span data-stu-id="943cc-132">[Get Information About Event Notifications](event-notifications.md) </span></span>  
 [<span data-ttu-id="943cc-133">EVENTDATA &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="943cc-133">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
