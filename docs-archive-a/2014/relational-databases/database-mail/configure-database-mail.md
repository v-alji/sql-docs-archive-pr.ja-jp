---
title: データベース メールの構成 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Sql12.swb.sqlimail.newaccount.f1
- Sql12.swb.sqlimail.manageexistingaccount.f1
- Sql12.swb.dbmail.manageexistingaccount.f1
- Sql12.swb.sqlimail.manageexistingprofile.f1
- Sql12.swb.sqlimail.newprofile.f1
- Sql12.swb.sqlimail.profileandaccountmanagement.f1
- Sql12.swb.dbmail.configuresystem.f1
- Sql12.swb.dbmail.profileandaccountmanagement.f1
- Sql12.swb.dbmail. manageprofilesecurity.profileview.f1
- Sql12.swb.dbmail.selectconfiguration.f1
- Sql12.swb.dbmail.newsqlimailaccount.f1
- Sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- Sql12.swb.sqlimail.newsqlimailaccount.f1
- Sql12.swb.dbmail.newaccount.f1
- Sql12.swb.dbmail.manageexistingprofile.f1
- Sql12.swb.sqlimail.configuresystem.f1
- Sql12.swb.sqlimail.selectconfiguration.f1
- Sql12.swb.dbmail.completewizard.f1
- Sql12.swb.sqlimail.welcome.f1
- sql12.swb.dbmail.sendtestemail.f1
- Sql12.swb.sqlimail.addaccounttoprofile.f1
- Sql12.swb.dbmail.welcome.f1
- Sql12.swb.dbmail.newprofile.f1
- Sql12.swb.dbmail.addaccounttoprofile.f1
- sql12.swb.dbmail.sendtestemail.test.f1
- Sql12.swb.sqlimail.completewizard.f1
- Sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- Sql12.swb.dbmail.manageprofilesecurity.principalview.f1
ms.assetid: 7edc21d4-ccf3-42a9-84c0-3f70333efce6
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbf9af4b5af3043c6ca8fa2cba01ebe43019fb41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645633"
---
# <a name="configure-database-mail"></a><span data-ttu-id="c37f4-102">データベース メールを構成する</span><span class="sxs-lookup"><span data-stu-id="c37f4-102">Configure Database Mail</span></span>
  <span data-ttu-id="c37f4-103">このトピックでは、データベース メール構成ウィザードを使用してデータベース メールを有効化して構成する方法、およびテンプレートを使用してデータベース メール構成スクリプトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-103">This topic describes how to enable and configure Database Mail using the Database Mail Configuration Wizard, and create a Database Mail Configuration script using templates.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c37f4-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="c37f4-104">Before You Begin</span></span>  
 <span data-ttu-id="c37f4-105">**Database Mail XPs** オプションを使用して、サーバーのデータベース メールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-105">Use the **DatabaseMail XPs** option to enable Database Mail on this server.</span></span> <span data-ttu-id="c37f4-106">詳細については、「 [Database Mail XPs サーバー構成オプション](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-106">For more information, see [Database Mail XPs Server Configuration Option](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) reference topic.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c37f4-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c37f4-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c37f4-108">任意のデータベースで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker を有効にするには、データベース ロックが必要です。</span><span class="sxs-lookup"><span data-stu-id="c37f4-108">Enabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker in any database requires a database lock.</span></span> <span data-ttu-id="c37f4-109">**msdb**で Service Broker が非アクティブ化された場合、データベース メールを有効にするには、最初に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを停止し、Service Broker が必要なロックを取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-109">If Service Broker was deactivated in **msdb**, to enable Database Mail, first stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent so Service Broker can obtain the necessary lock.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c37f4-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c37f4-110">Security</span></span>  
 <span data-ttu-id="c37f4-111">データベース メールを構成するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-111">To configure Database Mail you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="c37f4-112">データベース メールを送信するには、 **msdb** データベースの **DatabaseMailUserRole** データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-112">To send Database Mail you must be a member of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span>  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c37f4-113">データベース メール構成ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="c37f4-113">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="c37f4-114">**ウィザードを使用してデータベース メールを構成するには**</span><span class="sxs-lookup"><span data-stu-id="c37f4-114">**To configure Database Mail using a wizard**</span></span>  
  
1.  <span data-ttu-id="c37f4-115">オブジェクト エクスプローラーで、データベース メールを構成するインスタンスのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-115">In Object Explorer, expand the node for the instance  you want to configure Database mail.</span></span>  
  
2.  <span data-ttu-id="c37f4-116">[**管理**] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-116">Expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="c37f4-117">**[データベース メール]** を右クリックして、 **[データベース メールの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-117">Right-click **Database Mail**, and then click **Configure Database Mail**.</span></span>  
  
4.  <span data-ttu-id="c37f4-118">ウィザードの各ダイアログの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-118">Complete the Wizard dialogs</span></span>  
  

  
  
  
###  <a name="welcome-page"></a><a name="Welcome"></a><span data-ttu-id="c37f4-119">ようこそページ</span><span class="sxs-lookup"><span data-stu-id="c37f4-119">Welcome Page</span></span>  
 <span data-ttu-id="c37f4-120">このページでは、データベース メールを構成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-120">This page describes the steps to configuring Database Mail.</span></span>  
  
 <span data-ttu-id="c37f4-121">**次回からこのページを表示しない**-今後このページが表示されないようにするには、このチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-121">**Do not show this page again** - Check this to skip this welcome page from displaying in the future.</span></span>  
  
 <span data-ttu-id="c37f4-122">**[次へ]** : **[構成タスクの選択]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-122">**Next** - Proceeds to the **Select a configuration task** page.</span></span>  
  
 <span data-ttu-id="c37f4-123">**[キャンセル]** : データベースメールを構成せずにウィザードを終了します</span><span class="sxs-lookup"><span data-stu-id="c37f4-123">**Cancel** - Terminates the wizard without configuring Database Mail</span></span>  
  
 
  
###  <a name="select-configuration-task"></a><a name="ConfigTask"></a><span data-ttu-id="c37f4-124">構成タスクの選択</span><span class="sxs-lookup"><span data-stu-id="c37f4-124">Select Configuration Task</span></span>  
 <span data-ttu-id="c37f4-125">ウィザードを使用するたびに、 **[構成タスクの選択]** ページを使用して、完了するタスクを指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-125">Use the **Select Configuration Task** page, to indicate which task you will complete each time you use the wizard.</span></span> <span data-ttu-id="c37f4-126">ウィザードを完了する前に変更が必要になった場合は、 **[戻る]** ボタンを使用してこのページに戻り、別のタスクを選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-126">If you change your mind before you complete the wizard, use the **Back** button to return to this page and select a different task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c37f4-127">データベース メール機能が有効になっていない場合は、" **データベース メール機能は使用できません。有効にしますか? " というメッセージが表示されます。**</span><span class="sxs-lookup"><span data-stu-id="c37f4-127">If Database Mail has not been enabled, you will receive the message: **The Database Mail feature is not available.  Would you like to enable this feature?**</span></span> <span data-ttu-id="c37f4-128">ここで **[はい]** をクリックすることは、 [sp_configure](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) システム ストアド プロシージャの **Database Mail XPs オプション** を使用してデータベース メールを有効にすることと同じです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-128">Responding **Yes**, is equivalent to enabling Database Mail by using the [Database Mail XPs option](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) of the **sp_configure** system stored procedure.</span></span>  
  
 <span data-ttu-id="c37f4-129">**[次のタスクを実行してデータベース メールをセットアップする]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-129">**Set up Database Mail by performing the following tasks**</span></span>  
 <span data-ttu-id="c37f4-130">データベース メールを初めてセットアップするときに必要なタスクをすべて実行します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-130">Perform all of the tasks required to set up Database Mail for the first time.</span></span> <span data-ttu-id="c37f4-131">このオプションには、他の 3 つのオプションがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="c37f4-131">This option includes all of the other three options.</span></span>  
  
 <span data-ttu-id="c37f4-132">**[データベース メール アカウントおよびプロファイルを管理する]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-132">**Manage Database Mail accounts and profiles**</span></span>  
 <span data-ttu-id="c37f4-133">新しいデータベース メール アカウントおよびプロファイルの作成や、既存のデータベース メール アカウントおよびプロファイルの表示、変更、または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="c37f4-133">Create new Database Mail accounts and profiles or to view, change, or delete existing Database Mail accounts and profiles.</span></span>  
  
 <span data-ttu-id="c37f4-134">**[プロファイル セキュリティの管理]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-134">**Manage profile security**</span></span>  
 <span data-ttu-id="c37f4-135">データベース メール プロファイルへのアクセスを許可するユーザーを構成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-135">Configure which users have access to Database Mail profiles.</span></span>  
  
 <span data-ttu-id="c37f4-136">**[システム パラメーターを表示または変更する]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-136">**View or change system parameters**</span></span>  
 <span data-ttu-id="c37f4-137">添付ファイルの最大ファイル サイズなど、データベース メールのシステム パラメーターを構成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-137">Configure Database Mail system parameters such as the maximum file size for attachments.</span></span>  
  

  
###  <a name="new-account-page"></a><a name="NewAccount"></a><span data-ttu-id="c37f4-138">[新しいアカウント] ページ</span><span class="sxs-lookup"><span data-stu-id="c37f4-138">New Account Page</span></span>  
 <span data-ttu-id="c37f4-139">このページを使用すると、新しいデータベース メール アカウントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-139">Use this page to create a new Database Mail account.</span></span> <span data-ttu-id="c37f4-140">データベース メール アカウントには、SMTP サーバーへの電子メール送信に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-140">A Database Mail account contains information for sending e-mail to an SMTP server.</span></span>  
  
 <span data-ttu-id="c37f4-141">データベース メール アカウントには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SMTP サーバーに電子メールを送信するときに使用される情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c37f4-141">A Database Mail account contains the information that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to send e-mail messages to an SMTP server.</span></span> <span data-ttu-id="c37f4-142">各アカウントに、1 つの電子メール サーバーの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-142">Each account contains information for one e-mail server.</span></span>  
  
 <span data-ttu-id="c37f4-143">データベース メール アカウントは、データベース メールにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-143">A Database Mail account is only used for Database Mail.</span></span> <span data-ttu-id="c37f4-144">これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントや Microsoft Windows アカウントには対応していません。</span><span class="sxs-lookup"><span data-stu-id="c37f4-144">A Database Mail account does not correspond to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account or a Microsoft Windows account.</span></span> <span data-ttu-id="c37f4-145">データベース メールは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の資格情報、または指定したその他の資格情報を使用して送信できます。または、匿名で送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-145">Database Mail can be sent using the credentials of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], using other credentials that you supply, or anonymously.</span></span> <span data-ttu-id="c37f4-146">基本認証を使用する場合、データベース メール アカウントのユーザー名とパスワードは、電子メール サーバーとの認証だけに使用されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-146">When using basic authentication, the user name and password in a Database Mail account are only used for authentication with the e-mail server.</span></span> <span data-ttu-id="c37f4-147">アカウントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が動作しているコンピューターのユーザーに対応している必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c37f4-147">An account need not correspond to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user or a user on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c37f4-148">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-148">**Account name**</span></span>  
 <span data-ttu-id="c37f4-149">新しいアカウントの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-149">Type the name of the new account.</span></span>  
  
 <span data-ttu-id="c37f4-150">**説明**</span><span class="sxs-lookup"><span data-stu-id="c37f4-150">**Description**</span></span>  
 <span data-ttu-id="c37f4-151">アカウントの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-151">Type a description of the account.</span></span> <span data-ttu-id="c37f4-152">説明は省略できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-152">The description is optional.</span></span>  
  
 <span data-ttu-id="c37f4-153">**電子メールアドレス**</span><span class="sxs-lookup"><span data-stu-id="c37f4-153">**E-mail address**</span></span>  
 <span data-ttu-id="c37f4-154">アカウントの電子メール アドレスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-154">Type the name of the e-mail address for the account.</span></span> <span data-ttu-id="c37f4-155">これは、電子メールの送信元の電子メール アドレスです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-155">This is the e-mail address that e-mail is sent from.</span></span> <span data-ttu-id="c37f4-156">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントは、SqlAgent@Adventure-Works.com というアドレスから電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-156">For example, an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may send e-mail from the address SqlAgent@Adventure-Works.com.</span></span>  
  
 <span data-ttu-id="c37f4-157">**表示名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-157">**Display name**</span></span>  
 <span data-ttu-id="c37f4-158">このアカウントから送信する電子メール メッセージに表示する名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-158">Type the name to show on e-mail messages sent from this account.</span></span> <span data-ttu-id="c37f4-159">表示名はオプションです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-159">The display name is optional.</span></span> <span data-ttu-id="c37f4-160">これは、このアカウントから送信されたメッセージに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-160">This is the name displayed on messages sent from this account.</span></span> <span data-ttu-id="c37f4-161">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントは、電子メール メッセージに "SQL Server Agent Automated Mailer" という名前を表示できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-161">For example, an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may display the name "SQL Server Agent Automated Mailer" on e-mail messages.</span></span>  
  
 <span data-ttu-id="c37f4-162">**[電子メールの返信]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-162">**Reply e-mail**</span></span>  
 <span data-ttu-id="c37f4-163">このアカウントから送信された電子メール メッセージへの返信に使用される電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-163">Type the e-mail address that will be used for replies to e-mail messages sent from this account.</span></span> <span data-ttu-id="c37f4-164">電子メールの返信はオプションです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-164">The reply e-mail is optional.</span></span> <span data-ttu-id="c37f4-165">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントへの返信は、データベース管理者 danw@Adventure-Works.com をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-165">For example, replies to an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may go to the database administrator, danw@Adventure-Works.com.</span></span>  
  
 <span data-ttu-id="c37f4-166">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-166">**Server name**</span></span>  
 <span data-ttu-id="c37f4-167">アカウントが電子メールの送信に使用する SMTP サーバーの名前または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-167">Type the name or IP address of the SMTP server the account uses to send e-mail.</span></span> <span data-ttu-id="c37f4-168">通常、これは `smtp.` *<your_company>* に似た形式です `.com` 。</span><span class="sxs-lookup"><span data-stu-id="c37f4-168">Typically this is in a format similar to `smtp.`*<your_company>*`.com`.</span></span> <span data-ttu-id="c37f4-169">詳細については、電子メールの管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-169">For help with this, consult your mail administrator.</span></span>  
  
 <span data-ttu-id="c37f4-170">**ポート番号**</span><span class="sxs-lookup"><span data-stu-id="c37f4-170">**Port number**</span></span>  
 <span data-ttu-id="c37f4-171">このアカウントで使用する SMTP サーバーのポート番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-171">Type the port number of the SMTP server for this account.</span></span> <span data-ttu-id="c37f4-172">ほとんどの SMTP サーバーでは、ポート 25 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-172">Most SMTP servers use port 25.</span></span>  
  
 <span data-ttu-id="c37f4-173">**[このサーバーはセキュリティで保護された接続 (SSL) を必要とする]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-173">**This server requires a secure connection (SSL)**</span></span>  
 <span data-ttu-id="c37f4-174">SSL (Secure Sockets Layer) を使用して通信を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-174">Encrypts communication using Secure Sockets Layer.</span></span>  
  
 <span data-ttu-id="c37f4-175">**[データベース エンジン サービスの資格情報を使用する Windows 認証]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-175">**Windows Authentication using Database Engine service credentials**</span></span>  
 <span data-ttu-id="c37f4-176">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サービスに対して構成されている資格情報を使用して、SMTP サーバーとの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-176">Connection is made to the SMTP server using the credentials configured for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="c37f4-177">**基本認証**</span><span class="sxs-lookup"><span data-stu-id="c37f4-177">**Basic Authentication**</span></span>  
 <span data-ttu-id="c37f4-178">SMTP サーバーで必要なユーザー名およびパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-178">Specify the user name and password required by the SMTP server.</span></span>  
  
 <span data-ttu-id="c37f4-179">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-179">**User name**</span></span>  
 <span data-ttu-id="c37f4-180">データベース メールで SMTP サーバーへのログインに使用されるユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-180">Type the user name that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="c37f4-181">SMTP サーバーで基本認証が求められる場合、ユーザー名が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-181">The user name is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="c37f4-182">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="c37f4-182">**Password**</span></span>  
 <span data-ttu-id="c37f4-183">データベース メールで SMTP サーバーへのログインに使用されるパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-183">Type the password that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="c37f4-184">SMTP サーバーで基本認証が求められる場合、パスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-184">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="c37f4-185">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-185">**Confirm password**</span></span>  
 <span data-ttu-id="c37f4-186">パスワードに間違いがないことを確認するために、設定したパスワードをもう一度入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-186">Type the password again to confirm the password.</span></span> <span data-ttu-id="c37f4-187">SMTP サーバーで基本認証が求められる場合、パスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-187">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="c37f4-188">**匿名認証**</span><span class="sxs-lookup"><span data-stu-id="c37f4-188">**Anonymous authentication**</span></span>  
 <span data-ttu-id="c37f4-189">メールはログイン資格情報なしで SMTP サーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-189">Mail is sent to the SMTP server without login credentials.</span></span> <span data-ttu-id="c37f4-190">このオプションは、SMTP サーバーで認証が必要ない場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-190">Use this option when the SMTP server does not require authentication.</span></span>  
  
 
  
###  <a name="manage-existing-account-page"></a><a name="ExistingAccount"></a><span data-ttu-id="c37f4-191">[既存のアカウントの管理] ページ</span><span class="sxs-lookup"><span data-stu-id="c37f4-191">Manage Existing Account Page</span></span>  
 <span data-ttu-id="c37f4-192">このページを使用すると、既存のデータベース メール アカウントを管理できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-192">Use this page to manage an existing Database Mail account.</span></span>  
  
 <span data-ttu-id="c37f4-193">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-193">**Account name**</span></span>  
 <span data-ttu-id="c37f4-194">表示、更新、または削除するアカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-194">Select the account to view, update or delete.</span></span>  
  
 <span data-ttu-id="c37f4-195">**削除**</span><span class="sxs-lookup"><span data-stu-id="c37f4-195">**Delete**</span></span>  
 <span data-ttu-id="c37f4-196">選択されているアカウントを削除します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-196">Delete the selected account.</span></span> <span data-ttu-id="c37f4-197">関連付けられたプロファイルからこのアカウントを削除するか、選択したアカウントを削除する前にこのようなプロファイルを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-197">You must remove this account from associated profiles, or delete such profiles, before you delete the selected account.</span></span>  
  
 <span data-ttu-id="c37f4-198">**説明**</span><span class="sxs-lookup"><span data-stu-id="c37f4-198">**Description**</span></span>  
 <span data-ttu-id="c37f4-199">アカウントの説明を表示または更新します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-199">View or update the description of the account.</span></span> <span data-ttu-id="c37f4-200">説明は省略できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-200">The description is optional.</span></span>  
  
 <span data-ttu-id="c37f4-201">**電子メールアドレス**</span><span class="sxs-lookup"><span data-stu-id="c37f4-201">**E-mail address**</span></span>  
 <span data-ttu-id="c37f4-202">アカウントの電子メール アドレスの名前を表示または更新します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-202">View or update the name of the e-mail address for the account.</span></span> <span data-ttu-id="c37f4-203">これは、電子メールの送信元の電子メール アドレスです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-203">This is the e-mail address that e-mail is sent from.</span></span> <span data-ttu-id="c37f4-204">たとえば、Microsoft SQL Server エージェントのアカウントは、アドレスから電子メールを送信でき **SqlAgent@Adventure-Works.com** ます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-204">For example, an account for Microsoft SQL Server Agent may send e-mail from the address **SqlAgent@Adventure-Works.com**.</span></span>  
  
 <span data-ttu-id="c37f4-205">**表示名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-205">**Display name**</span></span>  
 <span data-ttu-id="c37f4-206">このアカウントから送信する電子メール メッセージに表示する名前を表示または更新します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-206">View or update the name to show on e-mail messages sent from this account.</span></span> <span data-ttu-id="c37f4-207">表示名はオプションです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-207">The display name is optional.</span></span> <span data-ttu-id="c37f4-208">これは、このアカウントから送信されたメッセージに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-208">This is the name displayed on messages sent from this account.</span></span> <span data-ttu-id="c37f4-209">たとえば、SQL Server エージェントのアカウントは、電子メールのメッセージに " **SQL Server Agent Automated Mailer** " という名前を表示できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-209">For example, an account for SQL Server Agent may display the name **SQL Server Agent Automated Mailer** on e-mail messages.</span></span>  
  
 <span data-ttu-id="c37f4-210">**[電子メールの返信]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-210">**Reply e-mail**</span></span>  
 <span data-ttu-id="c37f4-211">このアカウントから送信された電子メール メッセージへの返信に使用される電子メール アドレスを表示または更新します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-211">View or update the e-mail address that will be used for replies to e-mail messages sent from this account.</span></span> <span data-ttu-id="c37f4-212">電子メールの返信はオプションです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-212">The reply e-mail is optional.</span></span> <span data-ttu-id="c37f4-213">たとえば、SQL Server エージェントのアカウントへの返信は、データベース管理者であるに送ら **danw@Adventure-Works.com** れます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-213">For example, replies to an account for SQL Server Agent may go to the database administrator, **danw@Adventure-Works.com**.</span></span>  
  
 <span data-ttu-id="c37f4-214">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-214">**Server name**</span></span>  
 <span data-ttu-id="c37f4-215">アカウントが電子メールの送信に使用する SMTP サーバーの名前を表示または更新します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-215">View or update the name of the SMTP server the account uses to send e-mail.</span></span> <span data-ttu-id="c37f4-216">通常、これは**smtp. <your_company>** に似た形式です。</span><span class="sxs-lookup"><span data-stu-id="c37f4-216">Typically this is in a format similar to **smtp.<your_company>.com**.</span></span> <span data-ttu-id="c37f4-217">詳細については、電子メールの管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-217">For help with this, consult your mail administrator.</span></span>  
  
 <span data-ttu-id="c37f4-218">**ポート番号**</span><span class="sxs-lookup"><span data-stu-id="c37f4-218">**Port number**</span></span>  
 <span data-ttu-id="c37f4-219">このアカウントの SMTP サーバーのポート番号を表示または更新します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-219">View or update the port number of the SMTP server for this account.</span></span> <span data-ttu-id="c37f4-220">ほとんどの SMTP サーバーでは、ポート 25 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-220">Most SMTP servers use port 25.</span></span>  
  
 <span data-ttu-id="c37f4-221">**[このサーバーはセキュリティで保護された接続 (SSL) を必要とする]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-221">**This server requires a secure connection (SSL)**</span></span>  
 <span data-ttu-id="c37f4-222">SSL (Secure Sockets Layer) を使用して通信を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-222">Encrypts communication using Secure Sockets Layer.</span></span>  
  
 <span data-ttu-id="c37f4-223">**[データベース エンジン サービスの資格情報を使用する Windows 認証]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-223">**Windows Authentication using Database Engine service credentials**</span></span>  
 <span data-ttu-id="c37f4-224">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サービスに対して構成されている資格情報を使用して、SMTP サーバーとの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-224">Connection is made to the SMTP server using the credentials configured for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="c37f4-225">**基本認証**</span><span class="sxs-lookup"><span data-stu-id="c37f4-225">**Basic Authentication**</span></span>  
 <span data-ttu-id="c37f4-226">SMTP サーバーで必要なユーザー名およびパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-226">Specify the user name and password required by the SMTP server.</span></span>  
  
 <span data-ttu-id="c37f4-227">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-227">**User name**</span></span>  
 <span data-ttu-id="c37f4-228">データベース メールで SMTP サーバーへのログインに使用されるユーザー名を表示または更新します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-228">View or update the user name that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="c37f4-229">SMTP サーバーで基本認証が求められる場合、ユーザー名が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-229">The user name is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="c37f4-230">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="c37f4-230">**Password**</span></span>  
 <span data-ttu-id="c37f4-231">データベース メールで SMTP サーバーへのログインに使用されるパスワードを変更します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-231">Change the password that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="c37f4-232">SMTP サーバーで基本認証が求められる場合、パスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-232">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="c37f4-233">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-233">**Confirm password**</span></span>  
 <span data-ttu-id="c37f4-234">パスワードに間違いがないことを確認するために、設定したパスワードをもう一度入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-234">Type the password again to confirm the password.</span></span> <span data-ttu-id="c37f4-235">SMTP サーバーで基本認証が求められる場合、パスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-235">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="c37f4-236">**匿名認証**</span><span class="sxs-lookup"><span data-stu-id="c37f4-236">**Anonymous authentication**</span></span>  
 <span data-ttu-id="c37f4-237">メールはログイン資格情報なしで SMTP サーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-237">Mail is sent to the SMTP server without login credentials.</span></span> <span data-ttu-id="c37f4-238">このオプションは、SMTP サーバーで認証が必要ない場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-238">Use this option when the SMTP server does not require authentication.</span></span>  
  

  
###  <a name="new-profile-page"></a><a name="NewProfile"></a><span data-ttu-id="c37f4-239">[新しいプロファイル] ページ</span><span class="sxs-lookup"><span data-stu-id="c37f4-239">New Profile Page</span></span>  
 <span data-ttu-id="c37f4-240">このページを使用すると、データベース メール アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-240">Use this page to create a Database Mail profile.</span></span> <span data-ttu-id="c37f4-241">データベース メール プロファイルは、データベース メール アカウントのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-241">A Database Mail profile is a collection of Database Mail accounts.</span></span> <span data-ttu-id="c37f4-242">プロファイルは、電子メール サーバーが到達不能になった場合に、代わりのデータベース メール アカウントを提供することにより、信頼性を向上させます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-242">Profiles improve reliability in cases where an e-mail server becomes unreachable, by providing alternative Database Mail accounts.</span></span> <span data-ttu-id="c37f4-243">少なくとも 1 つのデータベース メール アカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="c37f4-243">At least one Database Mail account is required.</span></span> <span data-ttu-id="c37f4-244">プロファイルのデータベース アカウントの優先順位設定の詳細については、「 [データベース メール プロファイルの作成](create-a-database-mail-profile.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-244">For more information about setting the priority of Database Mail accounts in the profile, see [Create a Database Mail Profile](create-a-database-mail-profile.md).</span></span>  
  
 <span data-ttu-id="c37f4-245">**[上へ移動]** ボタンと **[下へ移動]** ボタンを使用して、データベース メール アカウントを使用する順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-245">Use the **Move Up** and **Move Down** buttons to change the order in which Database Mail accounts are used.</span></span> <span data-ttu-id="c37f4-246">順序は、シーケンス番号と呼ばれる値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-246">This order is determined by a value called the sequence number.</span></span> <span data-ttu-id="c37f4-247">**[上へ移動]** ではシーケンス番号が小さくなり、 **[下へ移動]** ではシーケンス番号が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-247">**Move Up** lowers the sequence number and **Move Down** increases the sequence number.</span></span> <span data-ttu-id="c37f4-248">シーケンス番号によって、データベース メールではプロファイル内のアカウントがどの順番で使用されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-248">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="c37f4-249">新しい電子メール メッセージの場合、データベース メールでは、一番小さなシーケンス番号の付いたアカウントから処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-249">For a new e-mail message, Database Mail starts with the account that has the lowest sequence number.</span></span> <span data-ttu-id="c37f4-250">そのアカウントが失敗すると、データベース メールでは、このアカウントよりも大きいシーケンス番号を持つアカウントに処理が移ります。このように、データベース メールによってメッセージが正常に送信されるか、一番大きなシーケンス番号のアカウントが失敗するまで順に処理されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-250">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="c37f4-251">一番大きいシーケンス番号のアカウントで失敗した場合は、データベース メールの **AccountRetryDelay** パラメーターで設定された時間が経過するまで、メール送信の試行が一時停止されます。その後、一番小さいシーケンス番号のアカウントからメール送信が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-251">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the Database Mail **AccountRetryDelay** parameter, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="c37f4-252">データベース メールの **AccountRetryAttempts** パラメーターを設定し、外部メール プロセスで指定のプロファイルの各アカウントを使用して、電子メール メッセージを送信する場合の試行回数を構成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-252">Use the Database Mail **AccountRetryAttempts** parameter, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span> <span data-ttu-id="c37f4-253">データベース メール構成ウィザードの **[システム パラメーターの構成]** ページで、 **AccountRetryDelay** パラメーターおよび **AccountRetryAttempts** パラメーターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-253">You can configure the **AccountRetryDelay** and **AccountRetryAttempts** parameters on the **Configure System Parameters** page of the Database Mail Configuration Wizard.</span></span>  
  
 <span data-ttu-id="c37f4-254">[**プロファイル名**]</span><span class="sxs-lookup"><span data-stu-id="c37f4-254">**Profile name**</span></span>  
 <span data-ttu-id="c37f4-255">新しいプロファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-255">Type the name for the new profile.</span></span> <span data-ttu-id="c37f4-256">プロファイルはこの名前を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-256">The profile is created with this name.</span></span> <span data-ttu-id="c37f4-257">既存のプロファイルの名前を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-257">Do not use the name of an existing profile.</span></span>  
  
 <span data-ttu-id="c37f4-258">**説明**</span><span class="sxs-lookup"><span data-stu-id="c37f4-258">**Description**</span></span>  
 <span data-ttu-id="c37f4-259">プロファイルの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-259">Type a description for the profile.</span></span> <span data-ttu-id="c37f4-260">説明は省略できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-260">The description is optional.</span></span>  
  
 <span data-ttu-id="c37f4-261">**[SMTP アカウント]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-261">**SMTP accounts**</span></span>  
 <span data-ttu-id="c37f4-262">プロファイルのアカウントを 1 つ以上選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-262">Choose one or more accounts for the profile.</span></span> <span data-ttu-id="c37f4-263">データベースがアカウントを使用する順序は、優先度に応じて設定します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-263">The priority sets the order in which Database Mail uses the accounts.</span></span> <span data-ttu-id="c37f4-264">アカウントが一覧表示されない場合は、 **[追加]** をクリックして新しい SMTP アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-264">If no accounts are listed, you must click **Add** to continue, and add a new SMTP account.</span></span>  
  
 <span data-ttu-id="c37f4-265">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-265">**Add**</span></span>  
 <span data-ttu-id="c37f4-266">アカウントをプロファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-266">Add an account to the profile.</span></span>  
  
 <span data-ttu-id="c37f4-267">**削除**</span><span class="sxs-lookup"><span data-stu-id="c37f4-267">**Remove**</span></span>  
 <span data-ttu-id="c37f4-268">選択されたアカウントをプロファイルから削除します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-268">Remove the selected account from the profile.</span></span>  
  
 <span data-ttu-id="c37f4-269">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-269">**Move Up**</span></span>  
 <span data-ttu-id="c37f4-270">選択されたアカウントの優先順位を上げます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-270">Increase the priority of the selected account.</span></span>  
  
 <span data-ttu-id="c37f4-271">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-271">**Move Down**</span></span>  
 <span data-ttu-id="c37f4-272">選択されたアカウントの優先順位を下げます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-272">Decrease the priority of the selected account.</span></span>  
  

  
###  <a name="manage-existing-profile-page"></a><a name="ExistingProfile"></a><span data-ttu-id="c37f4-273">[既存のプロファイルの管理] ページ</span><span class="sxs-lookup"><span data-stu-id="c37f4-273">Manage Existing Profile Page</span></span>  
 <span data-ttu-id="c37f4-274">このページを使用すると、既存のデータベース メール プロファイルを管理できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-274">Use this page to manage an existing Database Mail profile.</span></span> <span data-ttu-id="c37f4-275">データベース メール プロファイルは、データベース メール アカウントのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-275">A Database Mail profile is a collection of Database Mail accounts.</span></span> <span data-ttu-id="c37f4-276">プロファイルは、電子メール サーバーが到達不能になった場合に、代わりのデータベース メール アカウントを提供することにより、信頼性を向上させます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-276">Profiles improve reliability in cases where an e-mail server becomes unreachable, by providing alternative Database Mail accounts.</span></span> <span data-ttu-id="c37f4-277">少なくとも 1 つのデータベース メール アカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="c37f4-277">At least one Database Mail account is required.</span></span> <span data-ttu-id="c37f4-278">プロファイルのデータベース アカウントの優先順位設定の詳細については、「 [データベース メール プロファイルの作成](create-a-database-mail-profile.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-278">For more information about setting the priority of Database Mail accounts in the profile, see [Create a Database Mail Profile](create-a-database-mail-profile.md).</span></span>  
  
 <span data-ttu-id="c37f4-279">**[上へ移動]** ボタンと **[下へ移動]** ボタンを使用して、データベース メール アカウントを使用する順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-279">Use the **Move Up** and **Move Down** buttons to change the order in which Database Mail accounts are used.</span></span> <span data-ttu-id="c37f4-280">順序は、シーケンス番号と呼ばれる値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-280">This order is determined by a value called the sequence number.</span></span> <span data-ttu-id="c37f4-281">**[上へ移動]** ではシーケンス番号が小さくなり、 **[下へ移動]** ではシーケンス番号が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-281">**Move Up** lowers the sequence number and **Move Down** increases the sequence number.</span></span> <span data-ttu-id="c37f4-282">シーケンス番号によって、データベース メールではプロファイル内のアカウントがどの順番で使用されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-282">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="c37f4-283">新しい電子メール メッセージの場合、データベース メールでは、一番小さなシーケンス番号の付いたアカウントから処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-283">For a new e-mail message, Database Mail starts with the account that has the lowest sequence number.</span></span> <span data-ttu-id="c37f4-284">そのアカウントが失敗すると、データベース メールでは、このアカウントよりも大きいシーケンス番号を持つアカウントに処理が移ります。このように、データベース メールによってメッセージが正常に送信されるか、一番大きなシーケンス番号のアカウントが失敗するまで順に処理されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-284">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="c37f4-285">一番大きいシーケンス番号のアカウントで失敗した場合は、データベース メールの **AccountRetryDelay** パラメーターで設定された時間が経過するまで、メール送信の試行が一時停止されます。その後、一番小さいシーケンス番号のアカウントからメール送信が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-285">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the Database Mail **AccountRetryDelay** parameter, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="c37f4-286">データベース メールの **AccountRetryAttempts** パラメーターを設定し、外部メール プロセスで指定のプロファイルの各アカウントを使用して、電子メール メッセージを送信する場合の試行回数を構成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-286">Use the Database Mail **AccountRetryAttempts** parameter, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span> <span data-ttu-id="c37f4-287">データベース メール構成ウィザードの **[システム パラメーターの構成]** ページで、 **AccountRetryDelay** パラメーターおよび **AccountRetryAttempts** パラメーターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-287">You can configure the **AccountRetryDelay** and **AccountRetryAttempts** parameters on the **Configure System Parameters** page of the Database Mail Configuration Wizard.</span></span>  
  
 <span data-ttu-id="c37f4-288">[**プロファイル名**]</span><span class="sxs-lookup"><span data-stu-id="c37f4-288">**Profile name**</span></span>  
 <span data-ttu-id="c37f4-289">管理するプロファイルの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-289">Select the name of the profile to manage.</span></span>  
  
 <span data-ttu-id="c37f4-290">**削除**</span><span class="sxs-lookup"><span data-stu-id="c37f4-290">**Delete**</span></span>  
 <span data-ttu-id="c37f4-291">選択されているプロファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-291">Delete the selected profile.</span></span> <span data-ttu-id="c37f4-292">確認のメッセージが表示されます。選択したプロファイルを削除し、未送信のメッセージを破棄する場合は **[はい]** を選択します。未送信のメッセージがないときのみ、選択したプロファイルを削除する場合は **[いいえ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-292">You will be prompted to select **Yes** to delete the selected profile and to fail any unsent messages, or to select **No** to delete the selected profile only if there are no unsent messages.</span></span>  
  
 <span data-ttu-id="c37f4-293">**説明**</span><span class="sxs-lookup"><span data-stu-id="c37f4-293">**Description**</span></span>  
 <span data-ttu-id="c37f4-294">選択されているプロファイルの説明を表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-294">View or change the description of the selected profile.</span></span> <span data-ttu-id="c37f4-295">説明は省略できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-295">The description is optional.</span></span>  
  
 <span data-ttu-id="c37f4-296">**[SMTP アカウント]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-296">**SMTP accounts**</span></span>  
 <span data-ttu-id="c37f4-297">プロファイルのアカウントを 1 つ以上選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-297">Choose one or more accounts for the profile.</span></span> <span data-ttu-id="c37f4-298">フェールオーバーが発生したときにデータベース メールがアカウントを使用する順序は、フェールオーバー優先度に応じて設定されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-298">The failover priority sets the order in which Database Mail uses the account in case of a failover.</span></span>  
  
 <span data-ttu-id="c37f4-299">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-299">**Add**</span></span>  
 <span data-ttu-id="c37f4-300">アカウントをプロファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-300">Add an account to the profile.</span></span>  
  
 <span data-ttu-id="c37f4-301">**削除**</span><span class="sxs-lookup"><span data-stu-id="c37f4-301">**Remove**</span></span>  
 <span data-ttu-id="c37f4-302">選択されたアカウントをプロファイルから削除します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-302">Remove the selected account from the profile.</span></span>  
  
 <span data-ttu-id="c37f4-303">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-303">**Move Up**</span></span>  
 <span data-ttu-id="c37f4-304">選択されたアカウントのフェールオーバー優先度を上げます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-304">Increase the failover priority of the selected account.</span></span>  
  
 <span data-ttu-id="c37f4-305">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-305">**Move Down**</span></span>  
 <span data-ttu-id="c37f4-306">選択されたアカウントのフェールオーバー優先度を下げます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-306">Decrease the failover priority of the selected account.</span></span>  
  
 <span data-ttu-id="c37f4-307">**優先順位**</span><span class="sxs-lookup"><span data-stu-id="c37f4-307">**Priority**</span></span>  
 <span data-ttu-id="c37f4-308">アカウントの現在のフェールオーバー優先度を表示します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-308">View the current failover priority of the account.</span></span>  
  
 <span data-ttu-id="c37f4-309">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-309">**Account name**</span></span>  
 <span data-ttu-id="c37f4-310">アカウントの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-310">View the name of the account.</span></span>  
  
 <span data-ttu-id="c37f4-311">**電子メールアドレス**</span><span class="sxs-lookup"><span data-stu-id="c37f4-311">**E-mail Address**</span></span>  
 <span data-ttu-id="c37f4-312">アカウントの電子メール アドレスを表示します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-312">View the e-mail address of the account.</span></span>  
  

  
###  <a name="add-account-to-profile-page"></a><a name="AddAccount"></a><span data-ttu-id="c37f4-313">[アカウントをプロファイルに追加] ページ</span><span class="sxs-lookup"><span data-stu-id="c37f4-313">Add Account to Profile Page</span></span>  
 <span data-ttu-id="c37f4-314">このページを使用すると、プロファイルに追加するアカウントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-314">Use this page to choose the account to add to the profile.</span></span> <span data-ttu-id="c37f4-315">既存のアカウントを **[アカウント名]** ボックスから選択するか、 **[新しいアカウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-315">Either choose an existing account from the **Account name** box, or click **New Account**.</span></span>  
  
 <span data-ttu-id="c37f4-316">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-316">**Account name**</span></span>  
 <span data-ttu-id="c37f4-317">プロファイルに追加するアカウントの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-317">Select the name of the account to add to the profile.</span></span>  
  
 <span data-ttu-id="c37f4-318">**電子メールアドレス**</span><span class="sxs-lookup"><span data-stu-id="c37f4-318">**E-mail address**</span></span>  
 <span data-ttu-id="c37f4-319">選択されたアカウントの電子メール アドレスを表示します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-319">View the e-mail address for the selected account.</span></span> <span data-ttu-id="c37f4-320">このページでは、電子メール アドレスを変更できません。</span><span class="sxs-lookup"><span data-stu-id="c37f4-320">You cannot change the e-mail address from this page.</span></span> <span data-ttu-id="c37f4-321">アカウントの電子メール アドレスを変更するには、ウィザードのメイン ページに戻り、 **[データベース メール アカウントおよびプロファイルを管理する]** オプションをオンにしてください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-321">To change the e-mail address for the account, go back to the main page of the wizard and select the **Manage Database Mail accounts and profiles** option.</span></span>  
  
 <span data-ttu-id="c37f4-322">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-322">**Server name**</span></span>  
 <span data-ttu-id="c37f4-323">選択されたアカウントのメール サーバー名を表示します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-323">View the mail server name for the selected account.</span></span> <span data-ttu-id="c37f4-324">このページでは、サーバー名を変更できません。</span><span class="sxs-lookup"><span data-stu-id="c37f4-324">You cannot change the server name from this page.</span></span> <span data-ttu-id="c37f4-325">アカウントのサーバー名を変更するには、ウィザードのメイン ページに戻り、 **[データベース メール アカウントおよびプロファイルを管理する]** オプションをオンにしてください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-325">To change the server name for the account, go back to the main page of the wizard and select the **Manage Database Mail accounts and profiles** option.</span></span>  
  
 <span data-ttu-id="c37f4-326">**新しいアカウント**</span><span class="sxs-lookup"><span data-stu-id="c37f4-326">**New Account**</span></span>  
 <span data-ttu-id="c37f4-327">新しいアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-327">Create a new account.</span></span>  
  

  
###  <a name="manage-accounts-and-profiles-page"></a><a name="AccountsProfiles"></a><span data-ttu-id="c37f4-328">[アカウントとプロファイルの管理] ページ</span><span class="sxs-lookup"><span data-stu-id="c37f4-328">Manage Accounts and Profiles Page</span></span>  
 <span data-ttu-id="c37f4-329">このページを使用すると、プロファイルまたはアカウントを管理するためのタスクを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-329">Use this page to choose a task for managing a profile or account.</span></span>  
  
 <span data-ttu-id="c37f4-330">**新しいアカウントを作成する**</span><span class="sxs-lookup"><span data-stu-id="c37f4-330">**Create a new account**</span></span>  
 <span data-ttu-id="c37f4-331">新しいアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-331">Create a new account.</span></span>  
  
 <span data-ttu-id="c37f4-332">**[既存のアカウントを表示、変更、または削除する]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-332">**View, change or delete an existing account**</span></span>  
 <span data-ttu-id="c37f4-333">既存のアカウントを管理または削除します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-333">Manage or delete an existing account.</span></span>  
  
 <span data-ttu-id="c37f4-334">**[新しいプロファイルを作成する]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-334">**Create a new profile**</span></span>  
 <span data-ttu-id="c37f4-335">新しいプロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-335">Create a new profile.</span></span>  
  
 <span data-ttu-id="c37f4-336">**既存のプロファイルを表示、変更、または削除します。また、プロファイルに関連付けられているアカウントを管理することもできます。**</span><span class="sxs-lookup"><span data-stu-id="c37f4-336">**View, change or delete an existing profile. You can also manage accounts associated with the profile.**</span></span>  
 <span data-ttu-id="c37f4-337">既存のプロファイルを更新または削除します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-337">Update or delete an existing profile.</span></span> <span data-ttu-id="c37f4-338">このオプションにより、プロファイルに関連付けられたアカウントを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-338">This option also allows you to manage accounts associated with the profile.</span></span>  
  

  
###  <a name="manage-profile-security-public-tab"></a><a name="ProfileSecurityPublic"></a><span data-ttu-id="c37f4-339">[プロファイルセキュリティの管理]、[パブリック] タブ</span><span class="sxs-lookup"><span data-stu-id="c37f4-339">Manage Profile Security, Public Tab</span></span>  
 <span data-ttu-id="c37f4-340">このページを使用して、パブリック プロファイルを構成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-340">Use this page to configure a public profile.</span></span>  
  
 <span data-ttu-id="c37f4-341">プロファイルには、パブリックとプライベートの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-341">Profiles are either public or private.</span></span> <span data-ttu-id="c37f4-342">プライベート プロファイルは、特定のユーザーまたはロールのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-342">A private profile is accessible only to specific users or roles.</span></span> <span data-ttu-id="c37f4-343">パブリック プロファイルは、メール ホスト データベース (**msdb**) にアクセスできる任意のユーザーまたはロールが、電子メールを送信するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-343">A public profile allows any user or role with access to the mail host database (**msdb**) to send e-mail using that profile.</span></span>  
  
 <span data-ttu-id="c37f4-344">任意のプロファイルを既定のプロファイルとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-344">A profile may be a default profile.</span></span> <span data-ttu-id="c37f4-345">それにより、ユーザーまたはロールは、プロファイルを明示的に指定しなくても、既定のプロファイルを使用して電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-345">In this case, users or roles can send e-mail using the profile without explicitly specifying the profile.</span></span> <span data-ttu-id="c37f4-346">電子メール メッセージを送信するユーザーまたはロールに既定のプライベート プロファイルがある場合、データベース メールではそのプロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-346">If the user or role sending the e-mail message has a default private profile, Database Mail uses that profile.</span></span> <span data-ttu-id="c37f4-347">ユーザーまたはロールに既定のプライベート プロファイルがない場合、 **sp_send_dbmail** では、 **msdb** データベースの既定のパブリック プロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-347">If the user or role has no default private profile, **sp_send_dbmail** uses the default public profile for the **msdb** database.</span></span> <span data-ttu-id="c37f4-348">ユーザーまたはロールに既定のプライベート プロファイルがなく、データベースに既定のパブリック プロファイルもない場合、 **sp_send_dbmail** はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-348">If there is no default private profile for the user or role and no default public profile for the database, **sp_send_dbmail** returns an error.</span></span> <span data-ttu-id="c37f4-349">既定のプロファイルとして指定できるプロファイルは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-349">Only one profile can be marked as the default profile.</span></span>  
  
 <span data-ttu-id="c37f4-350">**パブリック**</span><span class="sxs-lookup"><span data-stu-id="c37f4-350">**Public**</span></span>  
 <span data-ttu-id="c37f4-351">このオプションを選択すると、指定したプロファイルがパブリック プロファイルになります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-351">Select this option to make the specified profile public.</span></span>  
  
 <span data-ttu-id="c37f4-352">**[プロファイル名]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-352">**Profile Name**</span></span>  
 <span data-ttu-id="c37f4-353">プロファイルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-353">Displays the name of the profile.</span></span>  
  
 <span data-ttu-id="c37f4-354">**既定のプロファイル**</span><span class="sxs-lookup"><span data-stu-id="c37f4-354">**Default Profile**</span></span>  
 <span data-ttu-id="c37f4-355">このオプションを選択すると、指定したプロファイルが既定のプロファイルになります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-355">Select this option to make the specified profile the default profile.</span></span>  
  
 <span data-ttu-id="c37f4-356">**[既存のパブリック プロファイルのみを表示する]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-356">**Show only existing public profiles**</span></span>  
 <span data-ttu-id="c37f4-357">このオプションを選択すると、指定したデータベース内のパブリック プロファイルのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-357">Select this option to show only public profiles in the specified database.</span></span>  
  

  
###  <a name="manage-profile-security-private-tab"></a><a name="ProfileSecurityPrivate"></a><span data-ttu-id="c37f4-358">[プロファイルセキュリティの管理]、[プライベート] タブ</span><span class="sxs-lookup"><span data-stu-id="c37f4-358">Manage Profile Security, Private Tab</span></span>  
 <span data-ttu-id="c37f4-359">このページを使用して、プライベート プロファイルを構成します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-359">Use this page to configure a private profile.</span></span>  
  
 <span data-ttu-id="c37f4-360">プロファイルには、パブリックとプライベートの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-360">Profiles are either public or private.</span></span> <span data-ttu-id="c37f4-361">プライベート プロファイルは、特定のユーザーまたはロールのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-361">A private profile is accessible only to specific users or roles.</span></span> <span data-ttu-id="c37f4-362">パブリック プロファイルは、メール ホスト データベース (**msdb**) にアクセスできる任意のユーザーまたはロールが、電子メールを送信するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-362">A public profile allows any user or role with access to the mail host database (**msdb**) to send e-mail using that profile.</span></span>  
  
 <span data-ttu-id="c37f4-363">任意のプロファイルを既定のプロファイルとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-363">A profile may be a default profile.</span></span> <span data-ttu-id="c37f4-364">それにより、ユーザーまたはロールは、プロファイルを明示的に指定しなくても、既定のプロファイルを使用して電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-364">In this case, users or roles can send e-mail using the profile without explicitly specifying the profile.</span></span> <span data-ttu-id="c37f4-365">電子メール メッセージを送信するユーザーまたはロールに既定のプライベート プロファイルがある場合、データベース メールではそのプロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-365">If the user or role sending the e-mail message has a default private profile, Database Mail uses that profile.</span></span> <span data-ttu-id="c37f4-366">ユーザーまたはロールに既定のプライベート プロファイルがない場合、 **sp_send_dbmail** では、 **msdb** データベースの既定のパブリック プロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-366">If the user or role has no default private profile, **sp_send_dbmail** uses the default public profile for the **msdb** database.</span></span> <span data-ttu-id="c37f4-367">ユーザーまたはロールに既定のプライベート プロファイルがなく、データベースに既定のパブリック プロファイルもない場合、 **sp_send_dbmail** はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-367">If there is no default private profile for the user or role and no default public profile for the database, **sp_send_dbmail** returns an error.</span></span>  
  
 <span data-ttu-id="c37f4-368">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-368">**User name**</span></span>  
 <span data-ttu-id="c37f4-369">**msdb** データベース内のユーザーまたはロールの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-369">Select the name of a user or role in the **msdb** database.</span></span>  
  
 <span data-ttu-id="c37f4-370">**アクセス**</span><span class="sxs-lookup"><span data-stu-id="c37f4-370">**Access**</span></span>  
 <span data-ttu-id="c37f4-371">ユーザーまたはロールが指定されたプロファイルにアクセスできるかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-371">Select whether the user or role has access to the specified profile.</span></span>  
  
 <span data-ttu-id="c37f4-372">[**プロファイル名**]</span><span class="sxs-lookup"><span data-stu-id="c37f4-372">**Profile name**</span></span>  
 <span data-ttu-id="c37f4-373">プロファイルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-373">View the name of the profile.</span></span>  
  
 <span data-ttu-id="c37f4-374">**[既定のプロファイル]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-374">**Is Default Profile**</span></span>  
 <span data-ttu-id="c37f4-375">このプロファイルがユーザーまたはロールの既定のプロファイルかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-375">Select whether the profile is the default profile for the user or role.</span></span> <span data-ttu-id="c37f4-376">各ユーザーまたはロールには、既定のプロファイルを 1 つだけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-376">Each user or role may have only one default profile.</span></span>  
  
 <span data-ttu-id="c37f4-377">**[このユーザーの既存のプライベート プロファイルのみを表示する]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-377">**Show only existing private profiles for this user**</span></span>  
 <span data-ttu-id="c37f4-378">オンにすると、指定されたユーザーまたはロールが既にアクセスを許可されているプロファイルのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-378">Select this option to display only profiles that the specified user or role already has access to.</span></span>  
  

  
###  <a name="configure-system-parameters"></a><a name="SystemParameters"></a><span data-ttu-id="c37f4-379">システムパラメーターの構成</span><span class="sxs-lookup"><span data-stu-id="c37f4-379">Configure System Parameters</span></span>  
 <span data-ttu-id="c37f4-380">このページを使用して、データベース メールのシステム パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-380">Use this page to specify Database Mail system parameters.</span></span> <span data-ttu-id="c37f4-381">システム パラメーターの一覧および各パラメーターの現在の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-381">View the system parameters and the current value of each parameter.</span></span> <span data-ttu-id="c37f4-382">パラメーターを選択すると、簡単な説明が情報ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-382">Select a parameter to view a short description in the information pane.</span></span>  
  
 <span data-ttu-id="c37f4-383">**[アカウントの再試行回数]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-383">**Account Retry Attempts**</span></span>  
 <span data-ttu-id="c37f4-384">指定したプロファイル内の各アカウントを使用して、外部メール処理が電子メール メッセージの送信を試行する回数。</span><span class="sxs-lookup"><span data-stu-id="c37f4-384">The number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span>  
  
 <span data-ttu-id="c37f4-385">**[アカウントの再試行間隔 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-385">**Account Retry Delay (seconds)**</span></span>  
 <span data-ttu-id="c37f4-386">外部メール プロセスが、プロファイルのすべてのアカウントを使用してメッセージ配信を試行した後で、再度すべてのアカウントによって試行するまで待機する時間 (秒数)。</span><span class="sxs-lookup"><span data-stu-id="c37f4-386">The amount of time, in seconds, for the external mail process to wait after it tries to deliver a message using all accounts in the profile before it attempts all accounts again.</span></span>  
  
 <span data-ttu-id="c37f4-387">**[ファイルの最大ファイル サイズ (バイト数)]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-387">**Maximum File Size (Bytes)**</span></span>  
 <span data-ttu-id="c37f4-388">添付ファイルの最大サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="c37f4-388">The maximum size of an attachment, in bytes.</span></span>  
  
 <span data-ttu-id="c37f4-389">**[禁止する添付ファイルの拡張子]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-389">**Prohibited Attachment File Extensions**</span></span>  
 <span data-ttu-id="c37f4-390">電子メールへの添付ファイルとして送信できない拡張子のコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="c37f4-390">A comma-separated list of extensions which cannot be sent as an attachment to an e-mail message.</span></span> <span data-ttu-id="c37f4-391">**[...]** ボタンをクリックして新たに拡張子を追加できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-391">Click the browse button (**...**) to add additional extensions.</span></span>  
  
 <span data-ttu-id="c37f4-392">**[データベース メール実行可能ファイルの最短有効期間 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-392">**Database Mail Executable Minimum Lifetime (seconds)**</span></span>  
 <span data-ttu-id="c37f4-393">外部メール処理がアクティブな状態にとどまる最小時間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="c37f4-393">The minimum amount of time, in seconds, that the external mail process remains active.</span></span> <span data-ttu-id="c37f4-394">電子メールがデータベース メール キューに入っている間は、プロセスはアクティブな状態のままです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-394">The process remains active as long as there are e-mails in the Database Mail queue.</span></span> <span data-ttu-id="c37f4-395">このパラメーターは、処理するメッセージがない場合にプロセスがアクティブな状態を維持する秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-395">This parameter specifies the time the process remains active if there are no messages to process.</span></span>  
  
 <span data-ttu-id="c37f4-396">**ログ記録レベル**</span><span class="sxs-lookup"><span data-stu-id="c37f4-396">**Logging level**</span></span>  
 <span data-ttu-id="c37f4-397">データベース メール ログに記録されるメッセージ。</span><span class="sxs-lookup"><span data-stu-id="c37f4-397">Specify which messages are recorded in the Database Mail log.</span></span> <span data-ttu-id="c37f4-398">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-398">Possible values are:</span></span>  
  
-   <span data-ttu-id="c37f4-399">[標準] - エラーのみを記録します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-399">Normal - logs only errors</span></span>  
  
-   <span data-ttu-id="c37f4-400">[拡張] - エラー、警告、および情報メッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-400">Extended - logs errors, warnings, and informational messages</span></span>  
  
-   <span data-ttu-id="c37f4-401">[詳細] - エラー、警告、情報メッセージ、成功メッセージ、および追加情報メッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-401">Verbose - logs errors, warnings, informational messages, success messages, and additional internal messages.</span></span> <span data-ttu-id="c37f4-402">詳細ログ記録はトラブルシューティングに使用します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-402">Use verbose logging for troubleshooting.</span></span>  
  
 <span data-ttu-id="c37f4-403">既定値は [拡張] です。</span><span class="sxs-lookup"><span data-stu-id="c37f4-403">Default value is Extended.</span></span>  
  
 <span data-ttu-id="c37f4-404">**[すべてリセット]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-404">**Reset All**</span></span>  
 <span data-ttu-id="c37f4-405">このオプションを選択すると、ページ上の値が既定値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-405">Select this option to reset the values on the page to the default values.</span></span>  
  

  
###  <a name="complete-the-wizard-page"></a><a name="CompleteWizard"></a><span data-ttu-id="c37f4-406">[ウィザードの完了] ページ</span><span class="sxs-lookup"><span data-stu-id="c37f4-406">Complete the Wizard Page</span></span>  
 <span data-ttu-id="c37f4-407">このページを使用すると、 **データベース メール構成ウィザード** によって実行されるアクションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-407">Use this page to review the actions that **Database Mail Configuration Wizard** will perform.</span></span> <span data-ttu-id="c37f4-408">ウィザードを完了するまでは、変更を加えることはできません。</span><span class="sxs-lookup"><span data-stu-id="c37f4-408">No changes are made until you finish the wizard.</span></span>  
  

  
###  <a name="send-test-e-mail-page"></a><a name="TestEmail"></a> <span data-ttu-id="c37f4-409">Send Test E-Mail Page</span><span class="sxs-lookup"><span data-stu-id="c37f4-409">Send Test E-Mail Page</span></span>  
 <span data-ttu-id="c37f4-410">[_<instance_name>_ **からのテスト電子メールの送信**] ページを使用して、指定したデータベースメールプロファイルを使用して電子メールメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-410">Use the **Send Test E-Mail from**_<instance_name>_ page to send an e-mail message using the specified Database Mail profile.</span></span> <span data-ttu-id="c37f4-411">このページを使用してテスト電子メールを送信できるのは、固定サーバー ロール **sysadmin** のメンバーのみです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-411">Only members of the **sysadmin** fixed server role can send test e-mail using this page.</span></span>  
  
 <span data-ttu-id="c37f4-412">**[データベース メール プロファイル]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-412">**Database Mail Profile**</span></span>  
 <span data-ttu-id="c37f4-413">データベース メール プロファイルを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-413">Select a Database Mail profile from the list.</span></span> <span data-ttu-id="c37f4-414">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-414">This is a required field.</span></span> <span data-ttu-id="c37f4-415">プロファイルが 1 つも表示されない場合は、プロファイルがないか、またはプロファイルに対する権限がありません。</span><span class="sxs-lookup"><span data-stu-id="c37f4-415">If no profiles are shown, there are no profiles or you do not have permission to a profile.</span></span> <span data-ttu-id="c37f4-416">プロファイルの作成および構成には、 **データベース メール構成ウィザード** を使用します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-416">Use the **Database Mail Configuration Wizard** to create and configure profiles.</span></span> <span data-ttu-id="c37f4-417">プロファイルが表示されない場合は、データベース メール構成ウィザードを使用して、使用するプロファイルを作成してください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-417">If no profiles are listed, use the Database Mail Configuration Wizard to create a profile for your use.</span></span>  
  
 <span data-ttu-id="c37f4-418">**To**</span><span class="sxs-lookup"><span data-stu-id="c37f4-418">**To**</span></span>  
 <span data-ttu-id="c37f4-419">メッセージの受信者の電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="c37f4-419">The e-mail address of the message recipients.</span></span> <span data-ttu-id="c37f4-420">少なくとも 1 人の受信者を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-420">At least one recipient is required.</span></span>  
  
 <span data-ttu-id="c37f4-421">**件名**</span><span class="sxs-lookup"><span data-stu-id="c37f4-421">**Subject**</span></span>  
 <span data-ttu-id="c37f4-422">テスト電子メールの件名行。</span><span class="sxs-lookup"><span data-stu-id="c37f4-422">The subject line for the test e-mail.</span></span> <span data-ttu-id="c37f4-423">トラブルシューティングの内容に合わせて、既定の件名を変更します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-423">Change the default subject to better identify your email for troubleshooting.</span></span>  
  
 <span data-ttu-id="c37f4-424">**本文**</span><span class="sxs-lookup"><span data-stu-id="c37f4-424">**Body**</span></span>  
 <span data-ttu-id="c37f4-425">テスト電子メールの本文。</span><span class="sxs-lookup"><span data-stu-id="c37f4-425">The body of the test e-mail.</span></span> <span data-ttu-id="c37f4-426">トラブルシューティングの内容に合わせて、既定の件名を変更します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-426">Change the default subject to better identify your email for troubleshooting.</span></span>  
  
 <span data-ttu-id="c37f4-427">**[データベース メールのテスト電子メール]** ダイアログ ボックスでは、データベース メールがテスト メッセージの送信を試みたことが通知され、テスト電子メール メッセージの **mailitem_id** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-427">The **Database Mail Test E-Mail** dialog box confirms that the test message that Database Mail attempted to send the message and provides the **mailitem_id** for the test e-mail message.</span></span> <span data-ttu-id="c37f4-428">電子メールが到着したかどうか受信者に確認します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-428">Check with the recipient to determine if the e-mail arrived.</span></span> <span data-ttu-id="c37f4-429">通常、電子メールは数分以内に受信されますが、ネットワークのパフォーマンスが低速である場合や、メール サーバーにメッセージのバックログがある場合、またはサーバーが一時的に使用できない場合には、電子メールの到着が遅れることもあります。</span><span class="sxs-lookup"><span data-stu-id="c37f4-429">Normally e-mail is received in a few minutes, but the e-mail can be delayed because of slow network performance, a backlog of messages at the mail server, or if the server is temporarily unavailable.</span></span> <span data-ttu-id="c37f4-430">**mailitem_id** はトラブルシューティングに使用します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-430">Use the **mailitem_id** for troubleshooting.</span></span>  
  
 <span data-ttu-id="c37f4-431">**[送信された電子メール]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-431">**Sent e-mail**</span></span>  
 <span data-ttu-id="c37f4-432">テスト電子メール メッセージの **mailitem_id** 。</span><span class="sxs-lookup"><span data-stu-id="c37f4-432">The **mailitem_id** of the test e-mail message.</span></span>  
  
 <span data-ttu-id="c37f4-433">**[トラブルシューティング]**</span><span class="sxs-lookup"><span data-stu-id="c37f4-433">**Troubleshoot**</span></span>  
 <span data-ttu-id="c37f4-434">クリックすると、オンライン ブックのトピック「 [データベース メールのトラブルシューティング](https://msdn.microsoft.com/library/ms188663.aspx)」が開きます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-434">Click to open Books Online to the [Troubleshooting Database Mail](https://msdn.microsoft.com/library/ms188663.aspx)topic.</span></span>  
  

  
##  <a name="using-templates"></a><a name="Template"></a><span data-ttu-id="c37f4-435">テンプレートの使用</span><span class="sxs-lookup"><span data-stu-id="c37f4-435">Using Templates</span></span>  
 <span data-ttu-id="c37f4-436">**データベース メール構成スクリプトを作成するには**</span><span class="sxs-lookup"><span data-stu-id="c37f4-436">**To create a Database Mail configuration script**</span></span>  
  
1.  <span data-ttu-id="c37f4-437">**[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-437">On the **View** menu, select **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="c37f4-438">**[テンプレート エクスプローラー]** ウィンドウで、 **[Database Mail]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-438">In the **Template Explorer** window, expand the **Database Mail** folder.</span></span>  
  
3.  <span data-ttu-id="c37f4-439">**[Simple Database Mail Configuration]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-439">Double-click **Simple Database Mail Configuration**.</span></span> <span data-ttu-id="c37f4-440">テンプレートが新しいクエリ ウィンドウに開きます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-440">The template opens in a new query window.</span></span>  
  
4.  <span data-ttu-id="c37f4-441">**[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c37f4-441">On the **Query** menu, select **Specify Values for Template Parameters**.</span></span> <span data-ttu-id="c37f4-442">**[テンプレート パラメーターの値の指定]** ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-442">The **Replace Template Parameters** window opens.</span></span>  
  
5.  <span data-ttu-id="c37f4-443">**profile_name**、 **account_name**、 **SMTP_servername**、 **email_address**、および **display_name**の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="c37f4-443">Type values for the **profile_name**, **account_name**, **SMTP_servername**, **email_address**, and **display_name**.</span></span> <span data-ttu-id="c37f4-444">SQL Server Management Studio によって、テンプレートに入力値が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="c37f4-444">SQL Server Management Studio fills in the template with the values you provide.</span></span>  
  
6.  <span data-ttu-id="c37f4-445">スクリプトを実行して構成を行います。</span><span class="sxs-lookup"><span data-stu-id="c37f4-445">Execute the script to create the configuration.</span></span>  
  
7.  <span data-ttu-id="c37f4-446">このスクリプトでは、どのデータベース ユーザーにもこのプロファイルにアクセスする権限が与えられません。</span><span class="sxs-lookup"><span data-stu-id="c37f4-446">The script does not grant any database users access to the profile.</span></span> <span data-ttu-id="c37f4-447">そのため、既定では、プロファイルを使用できるのは **sysadmin** 固定セキュリティ ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="c37f4-447">Therefore, by default, the profile can only be used by members of the **sysadmin** fixed security role.</span></span> <span data-ttu-id="c37f4-448">プロファイルへのアクセスを許可する方法の詳細については、「[sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c37f4-448">For more information about granting access to profiles, see [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)</span></span>  
  
  
