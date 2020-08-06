---
title: '[メッセージキュータスクエディター] ([送信] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.send.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 565aa079-ac44-4407-8efc-cddab839de30
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3534e1a8b475f22064ef7f2283c2e70eb561294f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743354"
---
# <a name="message-queue-task-editor-send-page"></a><span data-ttu-id="3bb5d-102">[メッセージ キュー タスク エディター] ([送信] ページ)</span><span class="sxs-lookup"><span data-stu-id="3bb5d-102">Message Queue Task Editor (Send Page)</span></span>
  <span data-ttu-id="3bb5d-103">**[メッセージ キュー タスク エディター]** ダイアログ ボックスの **[送信]** ページを使用すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージからメッセージを送信するメッセージ キュー タスクを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-103">Use the **Send** page of the **Message Queue Task Editor** dialog box to configure a Message Queue task to send messages from a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span>  
  
 <span data-ttu-id="3bb5d-104">このタスクの詳細については、「 [Message Queue Task](control-flow/message-queue-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3bb5d-105">Options</span><span class="sxs-lookup"><span data-stu-id="3bb5d-105">Options</span></span>  
 <span data-ttu-id="3bb5d-106">**[UseEncryption]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-106">**UseEncryption**</span></span>  
 <span data-ttu-id="3bb5d-107">メッセージを暗号化するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-107">Indicate whether to encrypt the message.</span></span> <span data-ttu-id="3bb5d-108">既定では、 `False`です。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-108">The default is `False`.</span></span>  
  
 <span data-ttu-id="3bb5d-109">**[EncryptionAlgorithm]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-109">**EncryptionAlgorithm**</span></span>  
 <span data-ttu-id="3bb5d-110">暗号化を使用する場合は、使用する暗号化アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-110">If you choose to use encryption, specify the name of the encryption algorithm to use.</span></span> <span data-ttu-id="3bb5d-111">メッセージ キュー タスクでは、RC2 と RC4 のアルゴリズムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-111">The Message Queue task can use the RC2 and RC4 algorithms.</span></span> <span data-ttu-id="3bb5d-112">既定値は **[RC2]** です。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-112">The default is **RC2**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bb5d-113">RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-113">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="3bb5d-114">データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます</span><span class="sxs-lookup"><span data-stu-id="3bb5d-114">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="3bb5d-115">(非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-115">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="3bb5d-116">現在のリリースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]では、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-116">In the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3bb5d-117">これらは、メッセージ キュー (MSMQ) テクノロジでサポートされる暗号化アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-117">These are the encryption algorithms that the Message Queuing (also known as MSMQ) technology supports.</span></span> <span data-ttu-id="3bb5d-118">現在、いずれの暗号化アルゴリズムも、メッセージ キューでまだサポートされていない最新のアルゴリズムと比較して、暗号強度の弱さが指摘されています。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-118">Both of these encryption algorithms are now considered cryptographically weak compared to newer algorithms, which Message Queuing does not yet support.</span></span> <span data-ttu-id="3bb5d-119">そのため、メッセージ キュー タスクを使ってメッセージを送信する場合は、必要な暗号強度を満たすことができるかどうかを十分に検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-119">Therefore, you should consider your cryptography needs carefully when sending messages using the Message Queue task.</span></span>  
  
 <span data-ttu-id="3bb5d-120">**[MessageType]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-120">**MessageType**</span></span>  
 <span data-ttu-id="3bb5d-121">メッセージ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-121">Select the message type.</span></span> <span data-ttu-id="3bb5d-122">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-122">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="3bb5d-123">値</span><span class="sxs-lookup"><span data-stu-id="3bb5d-123">Value</span></span>|<span data-ttu-id="3bb5d-124">説明</span><span class="sxs-lookup"><span data-stu-id="3bb5d-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3bb5d-125">**[データ ファイル メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-125">**Data file message**</span></span>|<span data-ttu-id="3bb5d-126">メッセージはファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-126">The message is stored in a file.</span></span> <span data-ttu-id="3bb5d-127">この値を選択すると、動的オプションの **[DataFileMessage]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-127">Selecting the value displays the dynamic option, **DataFileMessage**.</span></span>|  
|<span data-ttu-id="3bb5d-128">**[変数メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-128">**Variable message**</span></span>|<span data-ttu-id="3bb5d-129">メッセージは変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-129">The message is stored in a variable.</span></span> <span data-ttu-id="3bb5d-130">この値を選択すると、動的オプションの **[VariableMessage]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-130">Selecting the value displays the dynamic option, **VariableMessage**.</span></span>|  
|<span data-ttu-id="3bb5d-131">**[文字列メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-131">**String message**</span></span>|<span data-ttu-id="3bb5d-132">メッセージはメッセージ キュー タスクに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-132">The message is stored in the Message Queue task.</span></span> <span data-ttu-id="3bb5d-133">この値を選択すると、動的オプションの **[StringMessage]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-133">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
  
## <a name="messagetype-dynamic-options"></a><span data-ttu-id="3bb5d-134">[MessageType] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="3bb5d-134">MessageType Dynamic Options</span></span>  
  
### <a name="messagetype--data-file-message"></a><span data-ttu-id="3bb5d-135">[MessageType] = [データ ファイル メッセージ]</span><span class="sxs-lookup"><span data-stu-id="3bb5d-135">MessageType = Data file message</span></span>  
 <span data-ttu-id="3bb5d-136">**[DataFileMessage]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-136">**DataFileMessage**</span></span>  
 <span data-ttu-id="3bb5d-137">データ ファイルのパスを入力します。または、参照ボタン ( **[...]** ) をクリックし、データ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-137">Type the path of the data file, or click the ellipsis **(...)** and then locate the file.</span></span>  
  
### <a name="messagetype--variable-message"></a><span data-ttu-id="3bb5d-138">[MessageType] = [変数メッセージ]</span><span class="sxs-lookup"><span data-stu-id="3bb5d-138">MessageType = Variable message</span></span>  
 <span data-ttu-id="3bb5d-139">**[VariableMessage]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-139">**VariableMessage**</span></span>  
 <span data-ttu-id="3bb5d-140">変数名を入力します。または、参照ボタン ( **[...]** ) をクリックし、変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-140">Type the variable names, or click the ellipsis **(...)** and then select the variables.</span></span> <span data-ttu-id="3bb5d-141">変数はコンマで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-141">Variables are separated by commas.</span></span>  
  
 <span data-ttu-id="3bb5d-142">**関連トピック:** [変数の選択]</span><span class="sxs-lookup"><span data-stu-id="3bb5d-142">**Related Topics:** Select Variables</span></span>  
  
### <a name="messagetype--string-message"></a><span data-ttu-id="3bb5d-143">[MessageType] = [文字列メッセージ]</span><span class="sxs-lookup"><span data-stu-id="3bb5d-143">MessageType = String message</span></span>  
 <span data-ttu-id="3bb5d-144">**[StringMessage]**</span><span class="sxs-lookup"><span data-stu-id="3bb5d-144">**StringMessage**</span></span>  
 <span data-ttu-id="3bb5d-145">文字列メッセージを入力します。または、参照ボタン ( **[...]** ) をクリックし、メッセージを **[メッセージの入力]** ダイアログ ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="3bb5d-145">Type the string message, or click the ellipsis **(...)** and then type the message in the **Enter String Message** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb5d-146">参照</span><span class="sxs-lookup"><span data-stu-id="3bb5d-146">See Also</span></span>  
 <span data-ttu-id="3bb5d-147">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3bb5d-147">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3bb5d-148">[メッセージキュータスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="3bb5d-148">[Message Queue Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="3bb5d-149">[メッセージキュータスクエディター &#40;受信ページ&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span><span class="sxs-lookup"><span data-stu-id="3bb5d-149">[Message Queue Task Editor &#40;Receive Page&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span></span>  
 <span data-ttu-id="3bb5d-150">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="3bb5d-150">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
