---
title: メール送信タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.f1
helpviewer_keywords:
- mail [Integration Services]
- Send Mail task
- e-mail [Integration Services]
- messages [Integration Services]
- sending messages
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c93723f3c443705acc14226ce07f456da4d5a884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633257"
---
# <a name="send-mail-task"></a><span data-ttu-id="c1ac3-102">メール送信タスク</span><span class="sxs-lookup"><span data-stu-id="c1ac3-102">Send Mail Task</span></span>
  <span data-ttu-id="c1ac3-103">メール送信タスクは、電子メール メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-103">The Send Mail task sends an e-mail message.</span></span> <span data-ttu-id="c1ac3-104">メール送信タスクを使用すると、パッケージ ワークフロー内のタスクが成功または失敗した場合にパッケージからメッセージを送信したり、実行時にパッケージで発生するイベントに応答してメッセージを送信したりできます。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-104">By using the Send Mail task, a package can send messages if tasks in the package workflow succeed or fail, or send messages in response to an event that the package raises at run time.</span></span> <span data-ttu-id="c1ac3-105">たとえば、データベースのバックアップ タスクが成功または失敗したことを、メール送信タスクからデータベース管理者に通知できます。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-105">For example, the task can notify a database administrator about the success or failure of the Backup Database task.</span></span>  
  
 <span data-ttu-id="c1ac3-106">メール送信タスクは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-106">You can configure the Send Mail task in the following ways:</span></span>  
  
-   <span data-ttu-id="c1ac3-107">電子メール メッセージで使用するメッセージ テキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-107">Provide the message text for the e-mail message.</span></span>  
  
-   <span data-ttu-id="c1ac3-108">電子メール メッセージの件名行を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-108">Provide a subject line for the e-mail message.</span></span>  
  
-   <span data-ttu-id="c1ac3-109">メッセージの優先度レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-109">Set the priority level of the message.</span></span> <span data-ttu-id="c1ac3-110">タスクでは、標準、低、高の 3 種類の優先度レベルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-110">The task supports three priority levels: normal, low, and high.</span></span>  
  
-   <span data-ttu-id="c1ac3-111">[宛先]、[CC]、[BCC] 行に受信者を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-111">Specify the recipients on the To, Cc, and Bcc lines.</span></span> <span data-ttu-id="c1ac3-112">タスクで複数の受信者を指定する場合、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-112">If the task specifies multiple recipients, they are separated by semicolons.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1ac3-113">[宛先]、[CC]、[BCC] 行の文字数は、インターネット標準に従って 256 文字に制限されています。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-113">The To, Cc, and Bcc lines are limited to 256 characters each in accordance with Internet standards.</span></span>  
  
-   <span data-ttu-id="c1ac3-114">添付ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-114">Include attachments.</span></span> <span data-ttu-id="c1ac3-115">タスクで複数の添付ファイルを指定する場合、パイプ (|) 文字で区切られます。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-115">If the task specifies multiple attachments, they are separated by the pipe (|) character.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1ac3-116">パッケージの実行時に添付ファイルが存在しない場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-116">If an attachment file does not exist when the package runs, an error occurs.</span></span>  
  
-   <span data-ttu-id="c1ac3-117">使用する SMTP 接続マネージャーを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-117">Specify the SMTP connection manager to use.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c1ac3-118">SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-118">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="c1ac3-119">基本認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-119">It does not support basic authentication.</span></span>  
  
 <span data-ttu-id="c1ac3-120">メッセージ テキストには、指定する文字列、テキストを含むファイルへの接続、またはテキストを含む変数名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-120">The message text can be a string that you provide, a connection to a file that contains the text, or the name of a variable that contains the text.</span></span> <span data-ttu-id="c1ac3-121">タスクは、ファイル接続マネージャーを使用してファイルに接続します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-121">The task uses a File connection manager to connect to a file.</span></span> <span data-ttu-id="c1ac3-122">詳しくは、「 [フラット ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-122">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="c1ac3-123">タスクは、SMTP 接続マネージャーを使用してメール サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-123">The task uses an SMTP connection manager to connect to a mail server.</span></span> <span data-ttu-id="c1ac3-124">詳しくは、「 [SMTP 接続マネージャー](../connection-manager/smtp-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-124">For more information, see [SMTP Connection Manager](../connection-manager/smtp-connection-manager.md).</span></span>  
  
## <a name="custom-logging-messages-available-on-the-send-mail-task"></a><span data-ttu-id="c1ac3-125">メール送信タスクで使用できるカスタム ログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="c1ac3-125">Custom Logging Messages Available on the Send Mail Task</span></span>  
 <span data-ttu-id="c1ac3-126">次の表は、メール送信タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-126">The following table lists the custom log entries for the Send Mail task.</span></span> <span data-ttu-id="c1ac3-127">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-127">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="c1ac3-128">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="c1ac3-128">Log entry</span></span>|<span data-ttu-id="c1ac3-129">説明</span><span class="sxs-lookup"><span data-stu-id="c1ac3-129">Description</span></span>|  
|---------------|-----------------|  
|`SendMailTaskBegin`|<span data-ttu-id="c1ac3-130">タスクが電子メール メッセージの送信を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-130">Indicates that the task began to send an e-mail message.</span></span>|  
|`SendMailTaskEnd`|<span data-ttu-id="c1ac3-131">タスクが電子メール メッセージの送信を終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-131">Indicates that the task finished sending an e-mail message.</span></span>|  
|`SendMailTaskInfo`|<span data-ttu-id="c1ac3-132">タスクに関する説明情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-132">Provides descriptive information about the task.</span></span>|  
  
## <a name="configuring-the-send-mail-task"></a><span data-ttu-id="c1ac3-133">メール送信タスクの構成</span><span class="sxs-lookup"><span data-stu-id="c1ac3-133">Configuring the Send Mail Task</span></span>  
 <span data-ttu-id="c1ac3-134">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-134">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c1ac3-135">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-135">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="c1ac3-136">[[メール送信タスク エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="c1ac3-136">[Send Mail Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="c1ac3-137">[[メール送信タスク エディター] &#40;[メール] ページ&#41;](../send-mail-task-editor-mail-page.md)</span><span class="sxs-lookup"><span data-stu-id="c1ac3-137">[Send Mail Task Editor &#40;Mail Page&#41;](../send-mail-task-editor-mail-page.md)</span></span>  
  
-   <span data-ttu-id="c1ac3-138">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="c1ac3-138">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="c1ac3-139">プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-139">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="c1ac3-140">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c1ac3-140">Related Tasks</span></span>  
 <span data-ttu-id="c1ac3-141">これらのプロパティを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定する方法の詳細については、「 [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1ac3-141">For information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="c1ac3-142">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="c1ac3-142">Related Content</span></span>  
  
-   <span data-ttu-id="c1ac3-143">shareourideas.com の技術記事「 [配信通知付きで電子メールを送信する方法 (C#)](https://go.microsoft.com/fwlink/?LinkId=237625)」</span><span class="sxs-lookup"><span data-stu-id="c1ac3-143">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ac3-144">参照</span><span class="sxs-lookup"><span data-stu-id="c1ac3-144">See Also</span></span>  
 <span data-ttu-id="c1ac3-145">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="c1ac3-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="c1ac3-146">制御フロー</span><span class="sxs-lookup"><span data-stu-id="c1ac3-146">Control Flow</span></span>](control-flow.md)  
  
  
