---
title: データベース メール アカウントの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], accounts
- accounts [Database Mail]
ms.assetid: c07abbc6-fc6a-470b-8fa3-532f2e06b16a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec7d1c9147998b5a19cc0e6af13220bd64e165fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634559"
---
# <a name="create-a-database-mail-account"></a><span data-ttu-id="9e47d-102">データベース メール アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="9e47d-102">Create a Database Mail Account</span></span>
  <span data-ttu-id="9e47d-103">データベース メール アカウントの作成には、 **データベース メール構成ウィザード** または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e47d-103">Use either the **Database Mail Configuration Wizard** or [!INCLUDE[tsql](../../includes/tsql-md.md)] to create a Database Mail account.</span></span>  
  
-   <span data-ttu-id="9e47d-104">**作業を開始する準備:** [前提条件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="9e47d-104">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
-   <span data-ttu-id="9e47d-105">**データベース メール アカウントを作成するには、** を使用[データベース メール構成ウィザード](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="9e47d-105">**To Create a Database Mail Account, using:**  [Database Mail Configuration Wizard](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
-   <span data-ttu-id="9e47d-106">**補足情報:** [データベース メールを構成する次の手順](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="9e47d-106">**Follow Up:**  [Next Steps to Configure the Database Mail](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9e47d-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="9e47d-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="9e47d-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="9e47d-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="9e47d-109">電子メールの送信に使用する SMTP (簡易メール転送プロトコル) サーバーの名前とポート番号を特定します。SMTP サーバーが認証を必要とする場合は、その SMTP サーバー用のユーザー名とパスワードを特定します。</span><span class="sxs-lookup"><span data-stu-id="9e47d-109">Determine the server name and port number for the Simple Mail Transfer Protocol (SMTP) server you use to send e-mail.If the SMTP server requires authentication, determine the user name and password for the SMTP server.</span></span>  
  
-   <span data-ttu-id="9e47d-110">サーバーの種類とそのサーバー用のポート番号を指定できます。この指定は省略できます。</span><span class="sxs-lookup"><span data-stu-id="9e47d-110">Optionally, you may also specify the type of the server and the port number for the server.</span></span> <span data-ttu-id="9e47d-111">送信メール用のサーバーの種類は、常に 'SMTP' になります。</span><span class="sxs-lookup"><span data-stu-id="9e47d-111">The server type is always 'SMTP' for outgoing mail.</span></span> <span data-ttu-id="9e47d-112">ほとんどの SMTP サーバーは、既定のポート 25 を使用しています。</span><span class="sxs-lookup"><span data-stu-id="9e47d-112">Most SMTP servers use port 25, the default.</span></span>  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9e47d-113">データベース メール構成ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="9e47d-113">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="9e47d-114">**ウィザードを使用して、データベース メール アカウントを作成するには**</span><span class="sxs-lookup"><span data-stu-id="9e47d-114">**To create a Database Mail account using a Wizard**</span></span>  
  
-   <span data-ttu-id="9e47d-115">オブジェクト エクスプローラーで、データベース メールを構成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9e47d-115">In Object Explorer, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to configure Database Mail on, and expand the server tree.</span></span>  
  
-   <span data-ttu-id="9e47d-116">**[管理]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="9e47d-116">Expand the **Management** node</span></span>  
  
-   <span data-ttu-id="9e47d-117">[データベース メール] をダブルクリックして、データベース メール構成ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="9e47d-117">Double Click Database Mail to open the Database Mail Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="9e47d-118">**[構成タスクの選択]** ページで、 **[データベース メール アカウントおよびプロファイルを管理する]** を選択して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e47d-118">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles**, and click **Next**.</span></span>  
  
-   <span data-ttu-id="9e47d-119">**[プロファイルとアカウントの管理]** ページで、 **[新しいアカウントを作成する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e47d-119">On the **Manage Profiles and Accounts** page, select **Create a new account** and click **Next**.</span></span>  
  
-   <span data-ttu-id="9e47d-120">**[新しいアカウント]** ページで、アカウント名、説明、メール サーバー情報、および認証の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="9e47d-120">On the **New Account** page, specify the account name, description, mail server information, and authentication type.</span></span> <span data-ttu-id="9e47d-121">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e47d-121">Click **Next**</span></span>  
  
-   <span data-ttu-id="9e47d-122">**[ウィザードの完了]** ページで、実行される動作を確認し、 **[完了]** をクリックして、新しいアカウントの作成を完了します。</span><span class="sxs-lookup"><span data-stu-id="9e47d-122">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete creating the new account.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9e47d-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9e47d-123">Using Transact-SQL</span></span>  
 <span data-ttu-id="9e47d-124">**Transact-SQL を使用して、データベース メール アカウントを作成するには**</span><span class="sxs-lookup"><span data-stu-id="9e47d-124">**To Create a Database Mail account using Transact-SQL**</span></span>  
  
 <span data-ttu-id="9e47d-125">**msdb.dbo.sysmail_add_account_sp** ストアド プロシージャを実行してアカウントを作成し、次の情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="9e47d-125">Execute the stored procedure **msdb.dbo.sysmail_add_account_sp** to create the account and specify the following information:</span></span>  
  
-   <span data-ttu-id="9e47d-126">作成するアカウントの名前。</span><span class="sxs-lookup"><span data-stu-id="9e47d-126">The name of the account to create.</span></span>  
  
-   <span data-ttu-id="9e47d-127">省略可能なアカウントの説明。</span><span class="sxs-lookup"><span data-stu-id="9e47d-127">An optional description of the account.</span></span>  
  
-   <span data-ttu-id="9e47d-128">送信する電子メール メッセージに表示する電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="9e47d-128">The e-mail address to show on outgoing e-mail messages.</span></span>  
  
-   <span data-ttu-id="9e47d-129">送信する電子メール メッセージに表示する表示名。</span><span class="sxs-lookup"><span data-stu-id="9e47d-129">The display name to show on outgoing e-mail messages.</span></span>  
  
-   <span data-ttu-id="9e47d-130">SMTP サーバーのサーバー名。</span><span class="sxs-lookup"><span data-stu-id="9e47d-130">The server name of the SMTP server.</span></span>  
  
-   <span data-ttu-id="9e47d-131">SMTP サーバーが認証を必要とする場合、SMTP サーバーへのログオンに使用するユーザー名。</span><span class="sxs-lookup"><span data-stu-id="9e47d-131">The user name to use to log on to the SMTP server, if the SMTP server requires authentication.</span></span>  
  
-   <span data-ttu-id="9e47d-132">SMTP サーバーが認証を必要とする場合、SMTP サーバーへのログオンに使用するパスワード。</span><span class="sxs-lookup"><span data-stu-id="9e47d-132">The password to use to log on to the SMTP server, if the SMTP server requires authentication.</span></span>  
  
 <span data-ttu-id="9e47d-133">次の例では、新しいデータベース メール アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e47d-133">The following example creates a new Database Mail account.</span></span>  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
##  <a name="follow-up-next-steps-to-configuring-the-database-mail"></a><a name="FollowUp"></a><span data-ttu-id="9e47d-134">補足情報: データベース メールを構成する次の手順</span><span class="sxs-lookup"><span data-stu-id="9e47d-134">Follow Up: Next Steps to Configuring the Database Mail</span></span>  
  
-   [<span data-ttu-id="9e47d-135">データベース メール プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="9e47d-135">Create a Database Mail Profile</span></span>](create-a-database-mail-profile.md)  
  
  
