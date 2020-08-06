---
title: データベース メール プロファイルの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], public profiles
- profiles [SQL Server], Database Mail
- public profiles [Database Mail]
ms.assetid: 58ae749d-6ada-4f9c-bf00-de7c7a992a2d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0453d495c90c1e599bfc7777b4899f30e6659c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634558"
---
# <a name="create-a-database-mail-profile"></a><span data-ttu-id="fb4da-102">データベース メール プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="fb4da-102">Create a Database Mail Profile</span></span>
  <span data-ttu-id="fb4da-103">**データベース メール構成ウィザード** または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、データベース メールのパブリック プロファイルとプライベート プロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-103">Use either the **Database Mail Configuration Wizard** or [!INCLUDE[tsql](../../includes/tsql-md.md)] to create Database Mail public and private profiles.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fb4da-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="fb4da-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="fb4da-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="fb4da-105">Prerequisites</span></span>  
 <span data-ttu-id="fb4da-106">プロファイルに対応する 1 つ以上のデータベース メール アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-106">Create one or more Database Mail accounts for the profile.</span></span> <span data-ttu-id="fb4da-107">データベース メール アカウントの作成方法については、「 [データベース メール アカウントの作成](create-a-database-mail-account.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb4da-107">For more information about creating Database Mail accounts, see [Create a Database Mail Account](create-a-database-mail-account.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fb4da-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fb4da-108">Security</span></span>  
 <span data-ttu-id="fb4da-109">パブリック プロファイルにより、 **msdb** データベースにアクセスできるすべてのユーザーが、このプロファイルを使用して電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="fb4da-109">A public profile allows any user with access to the **msdb** database to send e-mail using that profile.</span></span> <span data-ttu-id="fb4da-110">プライベート プロファイルを使用できるのは、ユーザーまたはロールです。</span><span class="sxs-lookup"><span data-stu-id="fb4da-110">A private profile can be used by a user or by a role.</span></span> <span data-ttu-id="fb4da-111">プロファイルにロールのアクセス権を付与すると、保守が簡単なアーキテクチャを作成できます。</span><span class="sxs-lookup"><span data-stu-id="fb4da-111">Granting roles access to profiles creates a more easily maintained architecture.</span></span> <span data-ttu-id="fb4da-112">メールを送信するには、 **msdb** データベースの **DatabaseMailUserRole** のメンバーであることに加えて、少なくとも 1 つのデータベース メール プロファイルへのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="fb4da-112">To send mail you must be a member of the **DatabaseMailUserRole** in the **msdb** database, and have access to at least one Database Mail profile.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fb4da-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="fb4da-113">Permissions</span></span>  
 <span data-ttu-id="fb4da-114">プロファイル アカウントを作成し、ストアド プロシージャを実行するユーザーは、sysadmin 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb4da-114">The user creating the profiles accounts and executing stored procedures should be a member of the sysadmin fixed server role.</span></span>  
  

  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fb4da-115">データベース メール構成ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="fb4da-115">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="fb4da-116">**データベース メール プロファイルを作成するには**</span><span class="sxs-lookup"><span data-stu-id="fb4da-116">**To Create a Database Mail profile**</span></span>  
  
-   <span data-ttu-id="fb4da-117">オブジェクト エクスプローラーで、データベース メールを構成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-117">In Object Explorer, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to configure Database Mail on, and expand the server tree.</span></span>  
  
-   <span data-ttu-id="fb4da-118">**[管理]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-118">Expand the **Management** node</span></span>  
  
-   <span data-ttu-id="fb4da-119">[データベース メール] をダブルクリックして、データベース メール構成ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="fb4da-119">Double click Database Mail to open the Database Mail Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="fb4da-120">[**構成タスクの選択**] ページで、[**データベースメールアカウントとプロファイルを管理**する] オプションを選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-120">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option and click **Next**.</span></span>  
  
-   <span data-ttu-id="fb4da-121">**[プロファイルとアカウントの管理]** ページで、 **[新しいプロファイルを作成する]** オプションを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-121">On the **Manage Profiles and Accounts** page, select **Create a new profile** option, and click **Next**.</span></span>  
  
-   <span data-ttu-id="fb4da-122">**[新しいプロファイル]** ページで、プロファイル名と説明を指定し、プロファイルに含めるアカウントを追加して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-122">On the **New Profile** page, specify the Profile name, Description and add accounts to be included in the profile, and click **Next**.</span></span>  
  
-   <span data-ttu-id="fb4da-123">**[ウィザードの完了]** ページで、実行される動作を確認し、 **[完了]** をクリックして、新しいプロファイルの作成を完了します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-123">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete creating the new profile.</span></span>  
  
-   <span data-ttu-id="fb4da-124">**データベース メールのプライベート プロファイルを構成するには**</span><span class="sxs-lookup"><span data-stu-id="fb4da-124">**To configure a Database Mail private profile:**</span></span>  
  
    -   <span data-ttu-id="fb4da-125">データベース メール構成ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="fb4da-125">Open the Database Mail Configuration Wizard.</span></span>  
  
    -   <span data-ttu-id="fb4da-126">**[構成タスクの選択]** ページで、 **[データベース メール アカウントおよびプロファイルを管理する]** オプションを選択して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-126">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option, and click **Next**.</span></span>  
  
    -   <span data-ttu-id="fb4da-127">**[プロファイルとアカウントの管理]** ページで、 **[プロファイル セキュリティの管理]** オプションを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-127">On the **Manage Profiles and Accounts** page, select **Manage profile security** option and click **Next**.</span></span>  
  
    -   <span data-ttu-id="fb4da-128">**[プライベート プロファイル]** タブで、構成するプロファイルのチェック ボックスをオンにし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-128">In the **Private Profiles** tab, select the check box for the profile you would like to configure and click **Next**.</span></span>  
  
    -   <span data-ttu-id="fb4da-129">**[ウィザードの完了]** ページで、実行される動作を確認し、 **[完了]** をクリックして、プロファイルの構成を完了します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-129">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete configuring the profile.</span></span>  
  
-   <span data-ttu-id="fb4da-130">**データベース メールのパブリック プロファイルを構成するには**</span><span class="sxs-lookup"><span data-stu-id="fb4da-130">**To configure a Database Mail public profile:**</span></span>  
  
    -   <span data-ttu-id="fb4da-131">データベース メール構成ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="fb4da-131">Open the Database Mail Configuration Wizard.</span></span>  
  
    -   <span data-ttu-id="fb4da-132">**[構成タスクの選択]** ページで、 **[データベース メール アカウントおよびプロファイルを管理する]** オプションを選択して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-132">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option, and click **Next**.</span></span>  
  
    -   <span data-ttu-id="fb4da-133">**[プロファイルとアカウントの管理]** ページで、 **[プロファイル セキュリティの管理]** オプションを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-133">On the **Manage Profiles and Accounts** page, select **Manage profile security** option and click **Next**.</span></span>  
  
    -   <span data-ttu-id="fb4da-134">**[パブリック プロファイル]** タブで、構成するプロファイルのチェック ボックスをオンにし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb4da-134">In the **Public Profiles** tab, select the check box for the profile you would like to configure and click **Next**.</span></span>  
  
    -   <span data-ttu-id="fb4da-135">**[ウィザードの完了]** ページで、実行される動作を確認し、 **[完了]** をクリックして、プロファイルの構成を完了します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-135">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete configuring the profile.</span></span>  
  

  
## <a name="using-transact-sql"></a><span data-ttu-id="fb4da-136">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="fb4da-136">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-database-mail-private-profile"></a><a name="PrivateProfile"></a><span data-ttu-id="fb4da-137">データベースメールプライベートプロファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="fb4da-137">To Create a Database Mail private profile</span></span>  
  
-   <span data-ttu-id="fb4da-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-138">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="fb4da-139">新しいプロファイルを作成するには、システム ストアド プロシージャ [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) を次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-139">To create a new profile, run the system stored procedure [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="fb4da-140">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span><span class="sxs-lookup"><span data-stu-id="fb4da-140">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span></span>  
  
     <span data-ttu-id="fb4da-141">*@profile_name*= '*プロファイル名*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-141">*@profile_name* = '*Profile Name*'</span></span>  
  
     <span data-ttu-id="fb4da-142">*@description*= '*説明*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-142">*@description* = '*Desciption*'</span></span>  
  
     <span data-ttu-id="fb4da-143">*@profile_name*はプロファイルの名前です *@description* 。はプロファイルの説明です。</span><span class="sxs-lookup"><span data-stu-id="fb4da-143">where *@profile_name* is the name of the profile, and *@description* is the description of the profile.</span></span> <span data-ttu-id="fb4da-144">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="fb4da-144">This parameter is optional.</span></span>  
  
-   <span data-ttu-id="fb4da-145">アカウントごとに、ストアド プロシージャ [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) を次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-145">For each account, run the stored procedure [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="fb4da-146">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span><span class="sxs-lookup"><span data-stu-id="fb4da-146">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span></span>  
  
     <span data-ttu-id="fb4da-147">*@profile_name*= '*プロファイルの名前*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-147">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="fb4da-148">*@account_name*= '*アカウントの名前*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-148">*@account_name* = '*Name of the account*'</span></span>  
  
     <span data-ttu-id="fb4da-149">*@sequence_number*= '*プロファイル内のアカウントのシーケンス番号。*</span><span class="sxs-lookup"><span data-stu-id="fb4da-149">*@sequence_number* = '*sequence number of the account within the profile.*</span></span> <span data-ttu-id="fb4da-150">'</span><span class="sxs-lookup"><span data-stu-id="fb4da-150">'</span></span>  
  
     <span data-ttu-id="fb4da-151">*@profile_name*はプロファイルの名前です。はプロファイル *@account_name* に追加するアカウントの名前です。は、プロファイル *@sequence_number* でアカウントが使用される順序を決定します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-151">where *@profile_name* is the name of the profile, and *@account_name* is the name of the account to add to the profile, *@sequence_number* determines the order in which the accounts are used in the profile.</span></span>  
  
-   <span data-ttu-id="fb4da-152">このプロファイルを使用してメールを送信する各データベース ロールまたはユーザーについて、プロファイルへのアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-152">For each database role or user that will send mail using this profile, grant access to the profile.</span></span> <span data-ttu-id="fb4da-153">そのためには、ストアド プロシージャ [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) を次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-153">To do this, run the stored procedure [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="fb4da-154">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span><span class="sxs-lookup"><span data-stu-id="fb4da-154">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span></span>  
  
     <span data-ttu-id="fb4da-155">*@profile_name*= '*プロファイルの名前*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-155">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="fb4da-156">*@ principal_name* = '*Name of the database user or role*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-156">*@ principal_name* = '*Name of the database user or role*'</span></span>  
  
     <span data-ttu-id="fb4da-157">*@is_default*= '*既定のプロファイルの状態*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-157">*@is_default* = '*Default Profile status* '</span></span>  
  
     <span data-ttu-id="fb4da-158">*@profile_name*はプロファイルの名前です。は *@principal_name* データベースユーザーまたはロールの名前です。は、 *@is_default* このプロファイルが、データベースユーザーまたはロールの既定のプロファイルであるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-158">where *@profile_name* is the name of the profile, and *@principal_name* is the name of the database user or role, *@is_default* determines the whether this profile is the default for the database user or role.</span></span>  
  
 <span data-ttu-id="fb4da-159">次の例ではまず、データベース メール アカウントを作成し、データベース メールのプライベート プロファイルを作成します。その後、アカウントをプロファイルに追加し、そのプロファイルへのアクセス権を、 **msdb** データベースの **DBMailUsers** データベース ロールに与えます。</span><span class="sxs-lookup"><span data-stu-id="fb4da-159">The following example creates a Database Mail account, creates a Database Mail private profile, then adds the account to the profile and grants access to the profile to the **DBMailUsers** database role in the **msdb** database.</span></span>  
  
```  
-- Create a Database Mail account  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @account_name = 'AdventureWorks Administrator',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to the DBMailUsers role  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @principal_name = 'ApplicationUser',  
    @is_default = 1 ;  
```  
  
 
  
###  <a name="to-create-a-database-mail-public-profile"></a><a name="PublicProfile"></a><span data-ttu-id="fb4da-160">データベースメールパブリックプロファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="fb4da-160">To Create a Database Mail public profile</span></span>  
  
-   <span data-ttu-id="fb4da-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-161">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="fb4da-162">新しいプロファイルを作成するには、システム ストアド プロシージャ [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) を次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-162">To create a new profile, run the system stored procedure [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="fb4da-163">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span><span class="sxs-lookup"><span data-stu-id="fb4da-163">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span></span>  
  
     <span data-ttu-id="fb4da-164">*@profile_name*= '*プロファイル名*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-164">*@profile_name* = '*Profile Name*'</span></span>  
  
     <span data-ttu-id="fb4da-165">*@description*= '*説明*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-165">*@description* = '*Desciption*'</span></span>  
  
     <span data-ttu-id="fb4da-166">*@profile_name*はプロファイルの名前です *@description* 。はプロファイルの説明です。</span><span class="sxs-lookup"><span data-stu-id="fb4da-166">where *@profile_name* is the name of the profile, and *@description* is the description of the profile.</span></span> <span data-ttu-id="fb4da-167">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="fb4da-167">This parameter is optional.</span></span>  
  
-   <span data-ttu-id="fb4da-168">アカウントごとに、ストアド プロシージャ [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) を次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-168">For each account, run the stored procedure [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="fb4da-169">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span><span class="sxs-lookup"><span data-stu-id="fb4da-169">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span></span>  
  
     <span data-ttu-id="fb4da-170">*@profile_name*= '*プロファイルの名前*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-170">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="fb4da-171">*@account_name*= '*アカウントの名前*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-171">*@account_name* = '*Name of the account*'</span></span>  
  
     <span data-ttu-id="fb4da-172">*@sequence_number*= '*プロファイル内のアカウントのシーケンス番号。*</span><span class="sxs-lookup"><span data-stu-id="fb4da-172">*@sequence_number* = '*sequence number of the account within the profile.*</span></span> <span data-ttu-id="fb4da-173">'</span><span class="sxs-lookup"><span data-stu-id="fb4da-173">'</span></span>  
  
     <span data-ttu-id="fb4da-174">*@profile_name*はプロファイルの名前です。はプロファイル *@account_name* に追加するアカウントの名前です。は、プロファイル *@sequence_number* でアカウントが使用される順序を決定します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-174">where *@profile_name* is the name of the profile, and *@account_name* is the name of the account to add to the profile, *@sequence_number* determines the order in which the accounts are used in the profile.</span></span>  
  
-   <span data-ttu-id="fb4da-175">パブリック アクセス権を付与するには、ストアド プロシージャ [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) を次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-175">To grant public access, run the stored procedure [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="fb4da-176">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span><span class="sxs-lookup"><span data-stu-id="fb4da-176">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span></span>  
  
     <span data-ttu-id="fb4da-177">*@profile_name*= '*プロファイルの名前*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-177">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="fb4da-178">*@ principal_name* = '**public** or **0**'</span><span class="sxs-lookup"><span data-stu-id="fb4da-178">*@ principal_name* = '**public** or **0**'</span></span>  
  
     <span data-ttu-id="fb4da-179">*@is_default*= '*既定のプロファイルの状態*'</span><span class="sxs-lookup"><span data-stu-id="fb4da-179">*@is_default* = '*Default Profile status* '</span></span>  
  
     <span data-ttu-id="fb4da-180">*@profile_name*はプロファイルの名前です *@principal_name* 。は、このプロファイルがパブリックプロファイルであることを示し *@is_default* ます。は、このプロファイルが、データベースユーザーまたはロールの既定のプロファイルであるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="fb4da-180">where *@profile_name* is the name of the profile, and *@principal_name* to indicate this is a public profile, *@is_default* determines the whether this profile is the default for the database user or role.</span></span>  
  
 <span data-ttu-id="fb4da-181">次の例ではまず、データベース メール アカウントを作成し、データベース メールのプライベート プロファイルを作成します。その後、アカウントをプロファイルに追加し、そのプロファイルへのパブリック アクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="fb4da-181">The following example creates a Database Mail account, creates a Database Mail private profile, then adds the account to the profile and grants public access to the profile.</span></span>  
  
```  
-- Create a Database Mail account  
  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Public Account',  
    @description = 'Mail account for use by all database users.',  
    @email_address = 'db_users@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @account_name = 'AdventureWorks Public Account',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to all users in the msdb database  
  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @principal_name = 'public',  
    @is_default = 1 ;  
```  
  

  
  
