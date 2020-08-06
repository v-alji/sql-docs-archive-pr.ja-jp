---
title: メール送信タスクエディター ([メール] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52cab62f3c88ea248b76061664547fd8f1314099
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742406"
---
# <a name="send-mail-task-editor-mail-page"></a><span data-ttu-id="aeacb-102">[メール送信タスク エディター] ([メール] ページ)</span><span class="sxs-lookup"><span data-stu-id="aeacb-102">Send Mail Task Editor (Mail Page)</span></span>
  <span data-ttu-id="aeacb-103">**[メール送信タスク エディター]** ダイアログ ボックスの **[メール]** ページを使用すると、受信者、メッセージの種類、メッセージの重要度を指定できます。</span><span class="sxs-lookup"><span data-stu-id="aeacb-103">Use the **Mail** page of the **Send Mail Task Editor** dialog box to specify recipients, message type, and priority for a message.</span></span> <span data-ttu-id="aeacb-104">メッセージにファイルを添付することもできます。</span><span class="sxs-lookup"><span data-stu-id="aeacb-104">You can also attach files to the message.</span></span> <span data-ttu-id="aeacb-105">メッセージ テキストは、入力した文字列、テキストが含まれるファイルへのファイル接続、またはテキストが含まれる変数の名前になります。</span><span class="sxs-lookup"><span data-stu-id="aeacb-105">The message text can be a string you provide, a file connection to a file that contains the text, or the name of a variable that contains the text.</span></span>  
  
 <span data-ttu-id="aeacb-106">このタスクの詳細については、「 [Send Mail Task](control-flow/send-mail-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeacb-106">To learn about this task, see [Send Mail Task](control-flow/send-mail-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="aeacb-107">Options</span><span class="sxs-lookup"><span data-stu-id="aeacb-107">Options</span></span>  
 <span data-ttu-id="aeacb-108">**[SMTPConnection]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-108">**SMTPConnection**</span></span>  
 <span data-ttu-id="aeacb-109">SMTP 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-109">Select an SMTP connection manager in the list, or click **\<New connection...>** to create a new connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aeacb-110">SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="aeacb-110">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="aeacb-111">基本認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="aeacb-111">It does not support basic authentication.</span></span>  
  
 <span data-ttu-id="aeacb-112">**関連トピック:** [SMTP 接続マネージャー](connection-manager/smtp-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="aeacb-112">**Related Topics:** [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)</span></span>  
  
 <span data-ttu-id="aeacb-113">**From**</span><span class="sxs-lookup"><span data-stu-id="aeacb-113">**From**</span></span>  
 <span data-ttu-id="aeacb-114">送信者の電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-114">Specify the e-mail address of the sender.</span></span>  
  
 <span data-ttu-id="aeacb-115">**To**</span><span class="sxs-lookup"><span data-stu-id="aeacb-115">**To**</span></span>  
 <span data-ttu-id="aeacb-116">受信者の電子メール アドレスを指定します。受信者はセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="aeacb-116">Provide the e-mail addresses of the recipients, delimited by semicolons.</span></span>  
  
 <span data-ttu-id="aeacb-117">**[Cc]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-117">**Cc**</span></span>  
 <span data-ttu-id="aeacb-118">メッセージのコピーを受け取る受信者の電子メール アドレスを指定します。受信者はセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="aeacb-118">Specify the e-mail addresses, delimited by semicolons, of individuals who also receive copies of the message.</span></span>  
  
 <span data-ttu-id="aeacb-119">**[Bcc]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-119">**Bcc**</span></span>  
 <span data-ttu-id="aeacb-120">メッセージのコピーを Bcc として受け取る受信者の電子メール アドレスを指定します。受信者はセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="aeacb-120">Specify the e-mail addresses, delimited by semicolons, of individuals who receive blind carbon copies (Bcc) copies of the message.</span></span>  
  
 <span data-ttu-id="aeacb-121">**件名**</span><span class="sxs-lookup"><span data-stu-id="aeacb-121">**Subject**</span></span>  
 <span data-ttu-id="aeacb-122">電子メール メッセージの件名を指定します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-122">Provide a subject for the e-mail message.</span></span>  
  
 <span data-ttu-id="aeacb-123">**[MessageSourceType]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-123">**MessageSourceType**</span></span>  
 <span data-ttu-id="aeacb-124">メッセージのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-124">Select the source type of the message.</span></span> <span data-ttu-id="aeacb-125">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-125">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="aeacb-126">値</span><span class="sxs-lookup"><span data-stu-id="aeacb-126">Value</span></span>|<span data-ttu-id="aeacb-127">説明</span><span class="sxs-lookup"><span data-stu-id="aeacb-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aeacb-128">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-128">**Direct input**</span></span>|<span data-ttu-id="aeacb-129">メッセージ テキストをソースとして設定します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-129">Set the source to the message text.</span></span> <span data-ttu-id="aeacb-130">この値を選択すると、動的オプション **[MessageSource]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aeacb-130">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
|<span data-ttu-id="aeacb-131">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-131">**File connection**</span></span>|<span data-ttu-id="aeacb-132">メッセージ テキストが含まれるファイルをソースとして設定します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-132">Set the source to the file that contains the message text.</span></span> <span data-ttu-id="aeacb-133">この値を選択すると、動的オプション **[MessageSource]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aeacb-133">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
|<span data-ttu-id="aeacb-134">**変数**</span><span class="sxs-lookup"><span data-stu-id="aeacb-134">**Variable**</span></span>|<span data-ttu-id="aeacb-135">メッセージ テキストが含まれる変数をソースとして設定します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-135">Set the source to a variable that contains the message text.</span></span> <span data-ttu-id="aeacb-136">この値を選択すると、動的オプション **[MessageSource]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aeacb-136">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
  
 <span data-ttu-id="aeacb-137">**優先順位**</span><span class="sxs-lookup"><span data-stu-id="aeacb-137">**Priority**</span></span>  
 <span data-ttu-id="aeacb-138">メッセージの重要度を設定します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-138">Set the priority of the message.</span></span>  
  
 <span data-ttu-id="aeacb-139">**[Attachments]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-139">**Attachments**</span></span>  
 <span data-ttu-id="aeacb-140">電子メール メッセージに添付するファイル名を指定します。ファイル名はパイプ文字 (|) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="aeacb-140">Provide the file names of attachments to the e-mail message, delimited by the pipe (|) character.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aeacb-141">[宛先]、[CC]、[BCC] 行の文字数は、インターネット標準に従って 256 文字に制限されています。</span><span class="sxs-lookup"><span data-stu-id="aeacb-141">The To, Cc, and Bcc lines are limited to 256 characters in accordance with Internet standards.</span></span>  
  
## <a name="messagesourcetype-dynamic-options"></a><span data-ttu-id="aeacb-142">MessageSourceType 動的オプション</span><span class="sxs-lookup"><span data-stu-id="aeacb-142">MessageSourceType Dynamic Options</span></span>  
  
### <a name="messagesourcetype--direct-input"></a><span data-ttu-id="aeacb-143">[MessageSourceType] = [直接入力]</span><span class="sxs-lookup"><span data-stu-id="aeacb-143">MessageSourceType = Direct Input</span></span>  
 <span data-ttu-id="aeacb-144">**[MessageSource]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-144">**MessageSource**</span></span>  
 <span data-ttu-id="aeacb-145">メッセージ テキストを入力するか、参照ボタン ( [...] ) をクリックして **[メッセージの送信元]** ダイアログ ボックスにメッセージを入力します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-145">Type the message text or click the browse button (...) and then type the message in the **Message source** dialog box.</span></span>  
  
### <a name="messagesourcetype--file-connection"></a><span data-ttu-id="aeacb-146">[MessageSourceType] = [ファイル接続]</span><span class="sxs-lookup"><span data-stu-id="aeacb-146">MessageSourceType = File connection</span></span>  
 <span data-ttu-id="aeacb-147">**[MessageSource]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-147">**MessageSource**</span></span>  
 <span data-ttu-id="aeacb-148">一覧でファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-148">Select a File connection manager in the list or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="aeacb-149">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="aeacb-149">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="messagesourcetype--variable"></a><span data-ttu-id="aeacb-150">[MessageSourceType] = [変数]</span><span class="sxs-lookup"><span data-stu-id="aeacb-150">MessageSourceType = Variable</span></span>  
 <span data-ttu-id="aeacb-151">**[MessageSource]**</span><span class="sxs-lookup"><span data-stu-id="aeacb-151">**MessageSource**</span></span>  
 <span data-ttu-id="aeacb-152">一覧で変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="aeacb-152">Select a variable in the list or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="aeacb-153">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="aeacb-153">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeacb-154">参照</span><span class="sxs-lookup"><span data-stu-id="aeacb-154">See Also</span></span>  
 <span data-ttu-id="aeacb-155">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="aeacb-155">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="aeacb-156">[[メール送信タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="aeacb-156">[Send Mail Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="aeacb-157">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="aeacb-157">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
