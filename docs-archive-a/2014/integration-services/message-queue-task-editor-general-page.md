---
title: '[メッセージキュータスクエディター] ([全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dcec75f3a4dd85efb7c97226c592d6b1e1bb26ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645740"
---
# <a name="message-queue-task-editor-general-page"></a><span data-ttu-id="df74a-102">[メッセージ キュー タスク エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="df74a-102">Message Queue Task Editor (General Page)</span></span>
  <span data-ttu-id="df74a-103">**[メッセージ キュー タスク エディター]** の **[全般]** ページを使用すると、メッセージ キュー タスクの名前と説明を設定したり、メッセージの形式を指定したり、タスクでメッセージを送受信できるかどうかを指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="df74a-103">Use the **General page** of the **Message Queue Task Editor** dialog box to name and describe the Message Queue task, to specify the message format, and to indicate whether the task sends or receives messages.</span></span>  
  
 <span data-ttu-id="df74a-104">このタスクの詳細については、「 [Message Queue Task](control-flow/message-queue-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df74a-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="df74a-105">Options</span><span class="sxs-lookup"><span data-stu-id="df74a-105">Options</span></span>  
 <span data-ttu-id="df74a-106">**名前**</span><span class="sxs-lookup"><span data-stu-id="df74a-106">**Name**</span></span>  
 <span data-ttu-id="df74a-107">メッセージ キュー タスクの固有の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="df74a-107">Provide a unique name for the Message Queue task.</span></span> <span data-ttu-id="df74a-108">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="df74a-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df74a-109">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="df74a-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="df74a-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="df74a-110">**Description**</span></span>  
 <span data-ttu-id="df74a-111">メッセージ キュー タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="df74a-111">Type a description of the Message Queue task.</span></span>  
  
 <span data-ttu-id="df74a-112">**[Use2000Format]**</span><span class="sxs-lookup"><span data-stu-id="df74a-112">**Use2000Format**</span></span>  
 <span data-ttu-id="df74a-113">Message Queuing (MSMQ) の 2000 形式を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="df74a-113">Indicate whether to use the 2000 format of Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="df74a-114">既定では、 `False`です。</span><span class="sxs-lookup"><span data-stu-id="df74a-114">The default is `False`.</span></span>  
  
 <span data-ttu-id="df74a-115">**[MSMQConnection]**</span><span class="sxs-lookup"><span data-stu-id="df74a-115">**MSMQConnection**</span></span>  
 <span data-ttu-id="df74a-116">既存の MSMQ 接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="df74a-116">Select an existing MSMQ connection manager or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="df74a-117">**関連トピック:** [MSMQ 接続マネージャー](connection-manager/msmq-connection-manager.md)、[MSMQ 接続マネージャー エディター](../../2014/integration-services/msmq-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="df74a-117">**Related Topics**: [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md), [MSMQ Connection Manager Editor](../../2014/integration-services/msmq-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="df74a-118">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="df74a-118">**Message**</span></span>  
 <span data-ttu-id="df74a-119">メッセージ キュー タスクでメッセージを送信するのか、受信するのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="df74a-119">Specify whether the Message Queue task sends or receive messages.</span></span> <span data-ttu-id="df74a-120">**[メッセージの送信]** を選択すると、ダイアログ ボックスの左側のペインに [送信] ページが表示されます。 **[メッセージの受信]** を選択すると、[受信] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="df74a-120">If you select **Send message**, the Send page is listed in the left pane of the dialog box; if you select **Receive message**, the Receive page is listed.</span></span> <span data-ttu-id="df74a-121">既定では、 **[メッセージの送信]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="df74a-121">By default, this value is set to **Send message**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df74a-122">参照</span><span class="sxs-lookup"><span data-stu-id="df74a-122">See Also</span></span>  
 <span data-ttu-id="df74a-123">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="df74a-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="df74a-124">[メッセージキュータスクエディター &#40;受信ページ&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span><span class="sxs-lookup"><span data-stu-id="df74a-124">[Message Queue Task Editor &#40;Receive Page&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span></span>  
 <span data-ttu-id="df74a-125">[メッセージキュータスクエディター &#40;送信ページ&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span><span class="sxs-lookup"><span data-stu-id="df74a-125">[Message Queue Task Editor &#40;Send Page&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span></span>  
 <span data-ttu-id="df74a-126">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="df74a-126">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
