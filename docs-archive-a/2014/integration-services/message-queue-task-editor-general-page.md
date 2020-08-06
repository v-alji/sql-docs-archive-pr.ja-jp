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
# <a name="message-queue-task-editor-general-page"></a>[メッセージ キュー タスク エディター] ([全般] ページ)
  **[メッセージ キュー タスク エディター]** の **[全般]** ページを使用すると、メッセージ キュー タスクの名前と説明を設定したり、メッセージの形式を指定したり、タスクでメッセージを送受信できるかどうかを指定したりできます。  
  
 このタスクの詳細については、「 [Message Queue Task](control-flow/message-queue-task.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **名前**  
 メッセージ キュー タスクの固有の名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **説明**  
 メッセージ キュー タスクの説明を入力します。  
  
 **[Use2000Format]**  
 Message Queuing (MSMQ) の 2000 形式を使用するかどうかを指定します。 既定では、 `False`です。  
  
 **[MSMQConnection]**  
 既存の MSMQ 接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [MSMQ 接続マネージャー](connection-manager/msmq-connection-manager.md)、[MSMQ 接続マネージャー エディター](../../2014/integration-services/msmq-connection-manager-editor.md)  
  
 **メッセージ**  
 メッセージ キュー タスクでメッセージを送信するのか、受信するのかを指定します。 **[メッセージの送信]** を選択すると、ダイアログ ボックスの左側のペインに [送信] ページが表示されます。 **[メッセージの受信]** を選択すると、[受信] ページが表示されます。 既定では、 **[メッセージの送信]** に設定されています。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [メッセージキュータスクエディター &#40;受信ページ&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md)   
 [メッセージキュータスクエディター &#40;送信ページ&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  
