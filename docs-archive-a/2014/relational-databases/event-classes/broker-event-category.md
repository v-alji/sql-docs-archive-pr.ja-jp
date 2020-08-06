---
title: Broker イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23f839416e3404bfdf0a7e61d1b1e8dbbb90ec95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632524"
---
# <a name="broker-event-category"></a><span data-ttu-id="ed191-102">Broker イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="ed191-102">Broker Event Category</span></span>
  <span data-ttu-id="ed191-103">**Broker** イベント カテゴリには、一般的な Service Broker イベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ed191-103">The **Broker** event category contains general Service Broker events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed191-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ed191-104">In This Section</span></span>  
  
|<span data-ttu-id="ed191-105">トピック</span><span class="sxs-lookup"><span data-stu-id="ed191-105">Topic</span></span>|<span data-ttu-id="ed191-106">説明</span><span class="sxs-lookup"><span data-stu-id="ed191-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ed191-107">Broker:Activation イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-107">Broker:Activation Event Class</span></span>](broker-activation-event-class.md)|<span data-ttu-id="ed191-108">キュー モニターがアクティブ化ストアド プロシージャを開始するときに生成されるイベント。</span><span class="sxs-lookup"><span data-stu-id="ed191-108">An event generated when a queue monitor starts an activation stored procedure.</span></span>|  
|[<span data-ttu-id="ed191-109">Broker:Connection イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-109">Broker:Connection Event Class</span></span>](broker-connection-event-class.md)|<span data-ttu-id="ed191-110">Service Broker によって管理されるトランスポート接続のステータスをレポートするために生成されるイベントです。</span><span class="sxs-lookup"><span data-stu-id="ed191-110">An event generated to report the status of a transport connection managed by Service Broker.</span></span>|  
|[<span data-ttu-id="ed191-111">Broker:Conversation イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-111">Broker:Conversation Event Class</span></span>](broker-conversation-event-class.md)|<span data-ttu-id="ed191-112">メッセージ交換の進行状況をレポートするために生成されるイベントです。</span><span class="sxs-lookup"><span data-stu-id="ed191-112">An event generated to report the progress of a conversation.</span></span>|  
|[<span data-ttu-id="ed191-113">Broker:Conversation Group イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-113">Broker:Conversation Group Event Class</span></span>](broker-conversation-group-event-class.md)|<span data-ttu-id="ed191-114">データベースがメッセージ交換グループを作成または削除すると生成されるイベントです。</span><span class="sxs-lookup"><span data-stu-id="ed191-114">An event generated when the database creates or drops a conversation group.</span></span>|  
|[<span data-ttu-id="ed191-115">Broker:Corrupted Message イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-115">Broker:Corrupted Message Event Class</span></span>](broker-corrupted-message-event-class.md)|<span data-ttu-id="ed191-116">データベースが破損メッセージを受信したことを報告するために生成されるイベント。</span><span class="sxs-lookup"><span data-stu-id="ed191-116">An event generated to report that the database has received a corrupt message.</span></span>|  
|[<span data-ttu-id="ed191-117">Broker:Forwarded Message Dropped イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-117">Broker:Forwarded Message Dropped Event Class</span></span>](broker-forwarded-message-dropped-event-class.md)|<span data-ttu-id="ed191-118">転送された Service Broker メッセージが SQL Server によって削除されるときに生成されるイベント。</span><span class="sxs-lookup"><span data-stu-id="ed191-118">An event generated when SQL Server drops a Service Broker message that was to have been forwarded.</span></span>|  
|[<span data-ttu-id="ed191-119">Broker:Forwarded Message Sent イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-119">Broker:Forwarded Message Sent Event Class</span></span>](broker-forwarded-message-sent-event-class.md)|<span data-ttu-id="ed191-120">SQL Server によって Service Broker メッセージが転送されるときに生成されるイベント。</span><span class="sxs-lookup"><span data-stu-id="ed191-120">An event generated when SQL Server forwards a Service Broker message.</span></span>|  
|[<span data-ttu-id="ed191-121">Broker:Message Classify イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-121">Broker:Message Classify Event Class</span></span>](broker-message-classify-event-class.md)|<span data-ttu-id="ed191-122">Service Broker がメッセージのルーティングを決定するときに生成されるイベント。</span><span class="sxs-lookup"><span data-stu-id="ed191-122">An event generated when Service Broker determines the routing for a message.</span></span>|  
|[<span data-ttu-id="ed191-123">Broker:Message Drop イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-123">Broker:Message Drop Event Class</span></span>](broker-message-drop-event-class.md)|<span data-ttu-id="ed191-124">このインスタンスのサービスに配信する必要のある受信メッセージを、Service Broker が保持できないときに生成されるイベント。</span><span class="sxs-lookup"><span data-stu-id="ed191-124">An event generated when Service Broker is unable to retain a received message that should have been delivered to a service in this instance</span></span>|  
|[<span data-ttu-id="ed191-125">Broker:Remote Message Ack イベント クラス</span><span class="sxs-lookup"><span data-stu-id="ed191-125">Broker:Remote Message Ack Event Class</span></span>](broker-remote-message-ack-event-class.md)|<span data-ttu-id="ed191-126">Service Broker がメッセージの受信確認を送信または受信したときに生成されるイベント。</span><span class="sxs-lookup"><span data-stu-id="ed191-126">An event generated when Service Broker sends or receives a message acknowledgement.</span></span>|  
  
 <span data-ttu-id="ed191-127">Service Broker には、2 つのセキュリティ監査イベントも提供されます。</span><span class="sxs-lookup"><span data-stu-id="ed191-127">Two security audit events are also provided for Service Broker.</span></span> <span data-ttu-id="ed191-128">これらのイベントの詳細については、「 [Audit Broker Login イベント クラス](audit-broker-login-event-class.md) 」と「 [Audit Broker Conversation イベント クラス](audit-broker-conversation-event-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed191-128">For more information on those events, see [Audit Broker Login Event Class](audit-broker-login-event-class.md) and [Audit Broker Conversation Event Class](audit-broker-conversation-event-class.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed191-129">参照</span><span class="sxs-lookup"><span data-stu-id="ed191-129">See Also</span></span>  
 [<span data-ttu-id="ed191-130">セキュリティ監査イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="ed191-130">Security Audit Event Category</span></span>](https://docs.microsoft.com/bi-reference/trace-events/security-audit-event-category)  
  
  
