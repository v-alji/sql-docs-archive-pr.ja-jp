---
title: SQL Server エージェントのプロパティ ([警告システム] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.alert.f1
ms.assetid: 3e6d3bfd-20ee-4593-86cc-f65b1c08c69d
author: stevestein
ms.author: sstein
ms.openlocfilehash: ff203be21efbd99b90f02261cfe94dd49bd0d849
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644273"
---
# <a name="sql-server-agent-properties-alert-system-page"></a><span data-ttu-id="32389-102">SQL Server エージェントのプロパティ ([警告システム] ページ)</span><span class="sxs-lookup"><span data-stu-id="32389-102">SQL Server Agent Properties (Alert System Page)</span></span>
  <span data-ttu-id="32389-103">このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告によって送信されるメッセージの設定を表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="32389-103">Use this page to view and modify the settings for messages sent by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="32389-104">オプション</span><span class="sxs-lookup"><span data-stu-id="32389-104">Options</span></span>  
 <span data-ttu-id="32389-105">**[メール セッション]**</span><span class="sxs-lookup"><span data-stu-id="32389-105">**Mail session**</span></span>  
 <span data-ttu-id="32389-106">このセクションのオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのメールを構成します。</span><span class="sxs-lookup"><span data-stu-id="32389-106">The options in this section configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail.</span></span>  
  
 <span data-ttu-id="32389-107">**[メール プロファイルを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="32389-107">**Enable mail profile**</span></span>  
 <span data-ttu-id="32389-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのメールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="32389-108">Enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail.</span></span> <span data-ttu-id="32389-109">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのメールは有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="32389-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail is not enabled.</span></span>  
  
 <span data-ttu-id="32389-110">**[メール システム]**</span><span class="sxs-lookup"><span data-stu-id="32389-110">**Mail System**</span></span>  
 <span data-ttu-id="32389-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用するメール システムを設定します。</span><span class="sxs-lookup"><span data-stu-id="32389-111">Sets the mail system for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use.</span></span> <span data-ttu-id="32389-112">データベース メール</span><span class="sxs-lookup"><span data-stu-id="32389-112">Database Mail</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32389-113">電子メール システムを変更したら、変更内容を有効にするために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32389-113">After changing the e-mail system, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service for the change to take effect.</span></span>  
  
 <span data-ttu-id="32389-114">**[メール プロファイル]**</span><span class="sxs-lookup"><span data-stu-id="32389-114">**Mail Profile**</span></span>  
 <span data-ttu-id="32389-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用するプロファイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="32389-115">Sets the profile for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use.</span></span> <span data-ttu-id="32389-116">**[\<new Database Mail profile...>]** を選択して、新しいプロファイルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="32389-116">You may also select **\<new Database Mail profile...>** to create a new profile.</span></span>  
  
 <span data-ttu-id="32389-117">**[ポケットベル メール]**</span><span class="sxs-lookup"><span data-stu-id="32389-117">**Pager e-mails**</span></span>  
 <span data-ttu-id="32389-118">このセクションのオプションを使用すると、ポケットベル アドレスに送信される電子メール メッセージをポケットベル システムに対応させることができます。</span><span class="sxs-lookup"><span data-stu-id="32389-118">The options in this section allow you to configure e-mail messages sent to pager addresses to work with your paging system.</span></span>  
  
 <span data-ttu-id="32389-119">**[ポケットベル メールのアドレス形式]**</span><span class="sxs-lookup"><span data-stu-id="32389-119">**Address formatting for pager e-mails**</span></span>  
 <span data-ttu-id="32389-120">このセクションでは、アドレスの形式とポケットベル メールに含める件名行を指定できます。</span><span class="sxs-lookup"><span data-stu-id="32389-120">This section allows you to specify the format of the addresses and the subject line included in pager e-mails.</span></span>  
  
 <span data-ttu-id="32389-121">**宛先 行**</span><span class="sxs-lookup"><span data-stu-id="32389-121">**To line**</span></span>  
 <span data-ttu-id="32389-122">メッセージの **[宛先]** 行のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="32389-122">Specifies the options for the **To** line of the message</span></span>  
  
 <span data-ttu-id="32389-123">**プレフィックス**</span><span class="sxs-lookup"><span data-stu-id="32389-123">**Prefix**</span></span>  
 <span data-ttu-id="32389-124">ポケットベルに送信されるメッセージの **[宛先]** 行の先頭に、システムから要求される固定テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="32389-124">Type any fixed text that your system requires at the beginning of the **To** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="32389-125">**ポケットベル**</span><span class="sxs-lookup"><span data-stu-id="32389-125">**Pager**</span></span>  
 <span data-ttu-id="32389-126">メッセージの電子メール アドレスを、プレフィックスとサフィックスの間に含めます。</span><span class="sxs-lookup"><span data-stu-id="32389-126">Includes the e-mail address for the message between the prefix and the suffix.</span></span>  
  
 <span data-ttu-id="32389-127">**サフィックス**</span><span class="sxs-lookup"><span data-stu-id="32389-127">**Suffix**</span></span>  
 <span data-ttu-id="32389-128">ポケットベルに送信されるメッセージの **[宛先]** 行の末尾に、ポケットベル システムから要求される固定テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="32389-128">Type any fixed text that your paging system requires at the end of the **To** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="32389-129">**[[CC] 行]**</span><span class="sxs-lookup"><span data-stu-id="32389-129">**Cc line**</span></span>  
 <span data-ttu-id="32389-130">メッセージの **[CC]** 行のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="32389-130">Specifies options for the **Cc** line of the message.</span></span>  
  
 <span data-ttu-id="32389-131">**プレフィックス**</span><span class="sxs-lookup"><span data-stu-id="32389-131">**Prefix**</span></span>  
 <span data-ttu-id="32389-132">ポケットベルに送信されるメッセージの **[CC]** 行の先頭に、システムから要求される固定テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="32389-132">Type any fixed text that your system requires at the beginning of the **Cc** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="32389-133">**ポケットベル**</span><span class="sxs-lookup"><span data-stu-id="32389-133">**Pager**</span></span>  
 <span data-ttu-id="32389-134">メッセージの電子メール アドレスを、プレフィックスとサフィックスの間に含めます。</span><span class="sxs-lookup"><span data-stu-id="32389-134">Includes the e-mail address for the message between the prefix and the suffix.</span></span>  
  
 <span data-ttu-id="32389-135">**サフィックス**</span><span class="sxs-lookup"><span data-stu-id="32389-135">**Suffix**</span></span>  
 <span data-ttu-id="32389-136">ポケットベルに送信されるメッセージの **[CC]** 行の末尾に、ポケットベル システムから要求される固定テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="32389-136">Type any fixed text that your paging system requires at the end of the **Cc** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="32389-137">**[件名]**</span><span class="sxs-lookup"><span data-stu-id="32389-137">**Subject**</span></span>  
 <span data-ttu-id="32389-138">メッセージの件名のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="32389-138">Specifies the options for the subject of the message.</span></span>  
  
 <span data-ttu-id="32389-139">**プレフィックス**</span><span class="sxs-lookup"><span data-stu-id="32389-139">**Prefix**</span></span>  
 <span data-ttu-id="32389-140">ポケットベルに送信されるメッセージの **[件名]** 行の先頭に、ポケットベル システムから要求される固定テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="32389-140">Type any fixed text that your paging system requires at the beginning of the **Subject** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="32389-141">**サフィックス**</span><span class="sxs-lookup"><span data-stu-id="32389-141">**Suffix**</span></span>  
 <span data-ttu-id="32389-142">ポケットベルに送信されるメッセージの **[件名]** 行の末尾に、ポケットベル システムから要求される固定テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="32389-142">Type any fixed text that your paging system requires at the end of the **Subject** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="32389-143">**[通知メッセージに電子メールの本文を含める]**</span><span class="sxs-lookup"><span data-stu-id="32389-143">**Include body of e-mail in notification message**</span></span>  
 <span data-ttu-id="32389-144">ポケットベルに送信されるメッセージに、電子メールの本文を含めます。</span><span class="sxs-lookup"><span data-stu-id="32389-144">Includes the body of the e-mail message in the message sent to the pager.</span></span>  
  
 <span data-ttu-id="32389-145">**[緊急時のオペレーター]**</span><span class="sxs-lookup"><span data-stu-id="32389-145">**Fail-safe operator**</span></span>  
 <span data-ttu-id="32389-146">このセクションでは、緊急時のオペレーターのオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="32389-146">This section allows you to specify the options for the fail-safe operator.</span></span>  
  
 <span data-ttu-id="32389-147">**[緊急時のオペレーターを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="32389-147">**Enable fail-safe operator**</span></span>  
 <span data-ttu-id="32389-148">緊急時のオペレーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="32389-148">Specifies a fail safe operator.</span></span>  
  
 <span data-ttu-id="32389-149">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="32389-149">**Operator**</span></span>  
 <span data-ttu-id="32389-150">緊急時の通知を受け取るオペレーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="32389-150">Sets the name of the operator to receive fail-safe notifications.</span></span>  
  
 <span data-ttu-id="32389-151">**[通知方法]**</span><span class="sxs-lookup"><span data-stu-id="32389-151">**Notify using**</span></span>  
 <span data-ttu-id="32389-152">緊急時のオペレーターへの通知方法を設定します。</span><span class="sxs-lookup"><span data-stu-id="32389-152">Sets the method to use for notifying the fail-safe operator.</span></span>  
  
 <span data-ttu-id="32389-153">**[トークンの置換]**</span><span class="sxs-lookup"><span data-stu-id="32389-153">**Token Replacement**</span></span>  
 <span data-ttu-id="32389-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント警告によって実行されるジョブで使用するジョブ ステップ トークンを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="32389-154">This section allows you to enable job step tokens that can be used in jobs run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span> <span data-ttu-id="32389-155">ジョブ ステップ トークンの詳細については、「 [ジョブ ステップでのトークンの使用](use-tokens-in-job-steps.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32389-155">For more information about job step tokens, see [Use Tokens in Job Steps](use-tokens-in-job-steps.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="32389-156">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント警告でアクティブになるジョブ ステップには、Windows イベント ログに書き込み権限を持つ任意の Windows ユーザーがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="32389-156">Any Windows user with write permissions on the Windows Event Log may be able to access job steps that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span> <span data-ttu-id="32389-157">このセキュリティ上のリスクを避けるために、警告によってアクティブになるジョブで使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント トークンは、既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="32389-157">To avoid this security risk, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tokens that can be used in jobs activated by alerts are disabled by default.</span></span> <span data-ttu-id="32389-158">無効になっているトークンは、 **$(A-DBN)** 、 **$(A-SVR)** 、 **$(A-ERR)** 、 **$(A-SEV)** 、 **$(A-MSG)** です。</span><span class="sxs-lookup"><span data-stu-id="32389-158">These tokens are: **$(A-DBN)**, **$(A-SVR)**, **$(A-ERR)**, **$(A-SEV)**, and **$(A-MSG)**.</span></span>  
>   
>  <span data-ttu-id="32389-159">これらのトークンを使用する必要がある場合は、有効にする前に、信頼された Windows セキュリティ グループ (Administrators など) のメンバーだけが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が動作するコンピューターのイベント ログに書き込み権限を持つことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="32389-159">If you need to use these tokens, ensure that only members of trusted Windows security groups, such as the Administrators group, have write permissions on the Event Log of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resides before enabling them.</span></span>  
  
 <span data-ttu-id="32389-160">**[警告に応答するすべてのジョブのトークンを置き換える]**</span><span class="sxs-lookup"><span data-stu-id="32389-160">**Replace tokens for all job responses to alerts**</span></span>  
 <span data-ttu-id="32389-161">このチェック ボックスをオンにすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってアクティブになるジョブに対してトークンの置換が有効になります。</span><span class="sxs-lookup"><span data-stu-id="32389-161">Select this check box to enable token replacement for jobs that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32389-162">参照</span><span class="sxs-lookup"><span data-stu-id="32389-162">See Also</span></span>  
 <span data-ttu-id="32389-163">[通信](operators.md) </span><span class="sxs-lookup"><span data-stu-id="32389-163">[Operators](operators.md) </span></span>  
 <span data-ttu-id="32389-164">[SQL Server エージェントメールを使用するように構成データベースメール](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="32389-164">[Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md) </span></span>  
 [<span data-ttu-id="32389-165">データベース メール</span><span class="sxs-lookup"><span data-stu-id="32389-165">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
