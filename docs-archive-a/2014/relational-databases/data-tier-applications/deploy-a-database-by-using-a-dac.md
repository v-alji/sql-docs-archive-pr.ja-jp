---
title: DAC を使用したデータベースの配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbdeployment.settings.f1
- sql12.swb.dbdeployment.progress.f1
- sql12.swb.dbdeployment.summary.f1
- sql12.swb.dbdeployment.results.f1
- sql12.swb.dbdeployment.welcome.f1
helpviewer_keywords:
- deploy database wizard
- database deploy [SQL Server]
ms.assetid: 08c506e8-4ba0-4a19-a066-6e6a5c420539
author: stevestein
ms.author: sstein
ms.openlocfilehash: f753cfaf44e51b5bd3ffb939e38e2a300acb9703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740032"
---
# <a name="deploy-a-database-by-using-a-dac"></a><span data-ttu-id="56d4e-102">DAC を使用したデータベースの配置</span><span class="sxs-lookup"><span data-stu-id="56d4e-102">Deploy a Database By Using a DAC</span></span>
  <span data-ttu-id="56d4e-103">**のインスタンスと** サーバー間、または 2 つの [!INCLUDE[ssDE](../../includes/ssde-md.md)] サーバー間でデータベースを配置するには、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] SQL Azure へのデータベースの配置ウィザード [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-103">Use the **Deploy a Database to SQL Azure** Wizard to deploy a database between an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and a [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] server, or between two [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> <span data-ttu-id="56d4e-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="56d4e-104">Before You Begin</span></span>  
 <span data-ttu-id="56d4e-105">このウィザードでは、データ層アプリケーション (DAC) の BACPAC アーカイブ ファイルを使用して、データおよびデータベース オブジェクトの定義を配置します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-105">The wizard uses a Data-tier Application (DAC) BACPAC archive file to deploy both the data and the definitions of database objects.</span></span> <span data-ttu-id="56d4e-106">ウィザードでは、ソース データベースからの DAC エクスポート操作と、配置先への DAC インポート操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-106">It performs a DAC export operation from the source database, and a DAC import to the destination.</span></span>  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a> <span data-ttu-id="56d4e-107">データベースのオプションと設定</span><span class="sxs-lookup"><span data-stu-id="56d4e-107">Database Options and Settings</span></span>  
 <span data-ttu-id="56d4e-108">既定では、配置中に作成されるデータベースには、CREATE DATABASE ステートメントの既定の設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-108">By default, the database created during the deployment will have the default settings from the CREATE DATABASE statement.</span></span> <span data-ttu-id="56d4e-109">ただし、データベースの照合順序と互換性レベルはソース データベースの値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-109">The exception is that the database collation and compatibility level are set to the values from the source database.</span></span>  
  
 <span data-ttu-id="56d4e-110">TRUSTWORTHY、DB_CHAINING、HONOR_BROKER_PRIORITY などのデータベース オプションは、配置プロセスで調整できません。</span><span class="sxs-lookup"><span data-stu-id="56d4e-110">Database options, such as TRUSTWORTHY, DB_CHAINING and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the deployment process.</span></span> <span data-ttu-id="56d4e-111">ファイル グループの数、ファイルの数やサイズなどの物理プロパティは、配置作業中に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="56d4e-111">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the deployment process.</span></span> <span data-ttu-id="56d4e-112">配置が完了すれば、ALTER DATABASE ステートメント、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell を使用して、データベースを調整できます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-112">After the deployment completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="56d4e-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="56d4e-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="56d4e-114">**データベース配置** ウィザードでサポートされるデータベースの配置は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="56d4e-114">The **Deploy Database** wizard supports deploying a database:</span></span>  
  
-   <span data-ttu-id="56d4e-115">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスから [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56d4e-115">From an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span>  
  
-   <span data-ttu-id="56d4e-116">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] から [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンス</span><span class="sxs-lookup"><span data-stu-id="56d4e-116">From [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="56d4e-117">2 つの [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバー間</span><span class="sxs-lookup"><span data-stu-id="56d4e-117">Between two [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] servers.</span></span>  
  
 <span data-ttu-id="56d4e-118">[!INCLUDE[ssDE](../../includes/ssde-md.md)]の 2 つのインスタンス間でのデータベースの配置はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="56d4e-118">The wizard does not support deploying databases between two instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="56d4e-119">ウィザードを使用するには、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスで [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 以降を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d4e-119">An instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later to work with the wizard.</span></span> <span data-ttu-id="56d4e-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンス上のデータベースに [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]でサポートされていないオブジェクトが含まれている場合、ウィザードを使用して [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]にデータベースを配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="56d4e-120">If a database on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] contains objects not supported on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you cannot use the wizard to deploy the database to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="56d4e-121">また、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 上のデータベースに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でサポートされていないオブジェクトが含まれている場合、ウィザードを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスにデータベースを配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="56d4e-121">If a database on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] contains objects not supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you cannot use the wizard to deploy the database to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="56d4e-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="56d4e-122">Security</span></span>  
 <span data-ttu-id="56d4e-123">セキュリティを強化するために、SQL Server 認証のログインは、パスワードなしで DAC BACPAC ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-123">To improve security, SQL Server Authentication logins are stored in a DAC BACPAC file without a password.</span></span> <span data-ttu-id="56d4e-124">BACPAC をインポートすると、ログインはパスワードが生成された無効なログインとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-124">When the BACPAC is imported, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="56d4e-125">ログインを有効にするには、ALTER ANY LOGIN 権限を持つユーザーとしてログインし、ALTER LOGIN を使用してログインを有効にします。さらに、新しいパスワードを割り当て、そのパスワードを該当ユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-125">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="56d4e-126">Windows 認証ログインの場合、ログインのパスワードは SQL Server で管理されていないため、この操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="56d4e-126">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
#### <a name="permissions"></a><span data-ttu-id="56d4e-127">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="56d4e-127">Permissions</span></span>  
 <span data-ttu-id="56d4e-128">ウィザードでは、ソース データベースに対する DAC エクスポート権限が必要となります。</span><span class="sxs-lookup"><span data-stu-id="56d4e-128">The wizard requires DAC export permissions on the source database.</span></span> <span data-ttu-id="56d4e-129">ログインには、ALTER ANY LOGIN 権限とデータベース スコープの VIEW DEFINITION 権限、および **sys.sql_expression_dependencies**に対する SELECT 権限が少なくとも必要です。</span><span class="sxs-lookup"><span data-stu-id="56d4e-129">The login requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="56d4e-130">DAC をエクスポートできるのは、DAC をエクスポートするデータベースの database_owner 固定データベース ロールのメンバーでもある、securityadmin 固定サーバー ロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="56d4e-130">Exporting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is exported.</span></span> <span data-ttu-id="56d4e-131">sysadmin 固定サーバー ロールのメンバーまたは **sa** という組み込みの SQL Server システム管理者アカウントも DAC をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-131">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also export a DAC.</span></span>  
  
 <span data-ttu-id="56d4e-132">ウィザードでは、配置先インスタンスまたはサーバーに対する DAC インポート権限が必要となります。</span><span class="sxs-lookup"><span data-stu-id="56d4e-132">The wizard requires DAC import permissions on the destination instance or server.</span></span> <span data-ttu-id="56d4e-133">ログインは、 **sysadmin** または **serveradmin** 固定サーバー ロールのメンバーであるか、 **dbcreator** 固定サーバー ロールに属し、ALTER ANY LOGIN 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d4e-133">The login must be a member of the **sysadmin** or **serveradmin** fixed server roles, or in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="56d4e-134">あらかじめ登録された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者アカウント ( **sa** ) も DAC をインポートできます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-134">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also import a DAC.</span></span> <span data-ttu-id="56d4e-135">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] へのログインが含まれる DAC をインポートするには、loginmanager ロールまたは serveradmin ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="56d4e-135">Importing a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="56d4e-136">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] へのログインが含まれない DAC をインポートするには、dbmanager ロールまたは serveradmin ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="56d4e-136">Importing a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
##  <a name="using-the-deploy-database-wizard"></a><a name="UsingDeployDACWizard"></a> <span data-ttu-id="56d4e-137">データベース配置ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="56d4e-137">Using the Deploy Database Wizard</span></span>  
 <span data-ttu-id="56d4e-138">**データベース配置ウィザードを使用してデータベースを移行するには**</span><span class="sxs-lookup"><span data-stu-id="56d4e-138">**To migrate a database using the Deploy Database Wizard**</span></span>  
  
1.  <span data-ttu-id="56d4e-139">データベースの配置先に接続します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-139">Connect to the location of the database you want to deploy.</span></span> <span data-ttu-id="56d4e-140">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスまたは [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-140">You can specify either an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] or a [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] server.</span></span>  
  
2.  <span data-ttu-id="56d4e-141">**オブジェクト エクスプローラー**で、データベースがあるインスタンスのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-141">In **Object Explorer**, expand the node for the instance that has the database.</span></span>  
  
3.  <span data-ttu-id="56d4e-142">**[データベース]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-142">Expand the **Databases** node.</span></span>  
  
4.  <span data-ttu-id="56d4e-143">配置するデータベースを右クリックして **[タスク]** を選択し、 **[SQL Azure へのデータベースの配置...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d4e-143">Right click the database you want to deploy, select **Tasks**, and then select **Deploy Database to SQL Azure...**</span></span>  
  
5.  <span data-ttu-id="56d4e-144">ウィザードの各ダイアログを完了します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-144">Complete the Wizard dialogs:</span></span>  
  
    -   <span data-ttu-id="56d4e-145">[[説明] ページ](#Introduction)</span><span class="sxs-lookup"><span data-stu-id="56d4e-145">[Introduction Page](#Introduction)</span></span>  
  
    -   [<span data-ttu-id="56d4e-146">配置の設定</span><span class="sxs-lookup"><span data-stu-id="56d4e-146">Deployment Settings</span></span>](#Deployment_settings)  
  
    -   <span data-ttu-id="56d4e-147">[[概要] ページ](#Summary)</span><span class="sxs-lookup"><span data-stu-id="56d4e-147">[Summary Page](#Summary)</span></span>  
  
    -   [<span data-ttu-id="56d4e-148">結果</span><span class="sxs-lookup"><span data-stu-id="56d4e-148">Results</span></span>](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="56d4e-149">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="56d4e-149">Introduction Page</span></span>  
 <span data-ttu-id="56d4e-150">このページには、 **データベース配置** ウィザードの手順が示されています。</span><span class="sxs-lookup"><span data-stu-id="56d4e-150">This page describes the steps for the **Deploy Database** Wizard.</span></span>  
  
 <span data-ttu-id="56d4e-151">**Options**</span><span class="sxs-lookup"><span data-stu-id="56d4e-151">**Options**</span></span>  
  
-   <span data-ttu-id="56d4e-152">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="56d4e-152">**Do not show this page again.**</span></span> <span data-ttu-id="56d4e-153">: 今後 [説明] ページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="56d4e-153">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="56d4e-154">**[次へ]** : **[配置設定]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-154">**Next** - Proceeds to the **Deployment Settings** page.</span></span>  
  
-   <span data-ttu-id="56d4e-155">**[キャンセル]** : 操作を取り消し、ウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-155">**Cancel** - Cancels the operation and closes the Wizard.</span></span>  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a><span data-ttu-id="56d4e-156">[展開設定] ページ</span><span class="sxs-lookup"><span data-stu-id="56d4e-156">Deployment Settings Page</span></span>  
 <span data-ttu-id="56d4e-157">このページを使用して、配置先サーバーと、新しいデータベースの詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-157">Use this page to specify the destination server and to provide details about your new database.</span></span>  
  
 <span data-ttu-id="56d4e-158">**[ローカル ホスト]**</span><span class="sxs-lookup"><span data-stu-id="56d4e-158">**Local host:**</span></span>  
  
-   <span data-ttu-id="56d4e-159">**サーバー接続**-サーバー接続の詳細を指定し、[**接続**] をクリックして接続を確認します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-159">**Server connection** - Specify server connection details and then click **Connect** to verify the connection.</span></span>  
  
-   <span data-ttu-id="56d4e-160">**新しいデータベース名**-新しいデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-160">**New database name** - Specify a name for the new database.</span></span>  
  
 <span data-ttu-id="56d4e-161">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)]データベースの設定:**</span><span class="sxs-lookup"><span data-stu-id="56d4e-161">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)] database settings:**</span></span>  
  
-   <span data-ttu-id="56d4e-162">[ \*\* [!INCLUDE[ssSDS](../../includes/sssds-md.md)] エディション\*\*]- [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ドロップダウンメニューからエディションを選択します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-162">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)] edition** - Select the edition of [!INCLUDE[ssSDS](../../includes/sssds-md.md)] from the drop-down menu.</span></span>  
  
-   <span data-ttu-id="56d4e-163">[**データベースの最大サイズ**]-ドロップダウンメニューからデータベースの最大サイズを選択します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-163">**Maximum database size** - Select the maximum database size from the drop-down menu.</span></span>  
  
 <span data-ttu-id="56d4e-164">**その他の設定:**</span><span class="sxs-lookup"><span data-stu-id="56d4e-164">**Other settings:**</span></span>  
  
-   <span data-ttu-id="56d4e-165">一時ファイル (BACPAC アーカイブ ファイル) のローカル ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-165">Specify a local directory for the temporary file, which is the BACPAC archive file.</span></span> <span data-ttu-id="56d4e-166">このファイルは指定した場所に作成され、操作の完了後もそのまま残されます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-166">Note that the file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="56d4e-167">[概要] ページ</span><span class="sxs-lookup"><span data-stu-id="56d4e-167">Summary Page</span></span>  
 <span data-ttu-id="56d4e-168">このページを使用すると、操作の指定ソースとターゲットの設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-168">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="56d4e-169">指定した設定で配置操作を実行するには、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d4e-169">To complete the deploy operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="56d4e-170">配置操作をキャンセルしてウィザードを終了するには、[**キャンセル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d4e-170">To cancel the deploy operation and exit the Wizard, click **Cancel**.</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="56d4e-171">[進行状況] ページ</span><span class="sxs-lookup"><span data-stu-id="56d4e-171">Progress Page</span></span>  
 <span data-ttu-id="56d4e-172">このページには、操作の進行状況を示す進行状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-172">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="56d4e-173">詳細な状態を表示するには、 **[詳細表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d4e-173">To view detailed status, click the **View details** option.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="56d4e-174">[結果] ページ</span><span class="sxs-lookup"><span data-stu-id="56d4e-174">Results Page</span></span>  
 <span data-ttu-id="56d4e-175">このページでは、配置操作の成功と失敗が報告され、各アクションの結果が示されます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-175">This page reports the success or failure of the deploy operation, showing the results of each action.</span></span> <span data-ttu-id="56d4e-176">エラーが発生したアクションには、 **[結果]** 列にリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-176">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="56d4e-177">そのアクションのエラーのレポートを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d4e-177">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="56d4e-178">[**完了**] をクリックしてウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="56d4e-178">Click **Finish** to close the Wizard.</span></span>  
  
## <a name="using-a-net-framework-application"></a><span data-ttu-id="56d4e-179">.Net Framework アプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="56d4e-179">Using a .Net Framework Application</span></span>  
 <span data-ttu-id="56d4e-180">**.Net Framework アプリケーションで DacStoreExport() メソッドおよび Import() メソッドを使用してデータベースを配置するには**</span><span class="sxs-lookup"><span data-stu-id="56d4e-180">**To deploy a database using the DacStoreExport() and Import() methods in a .Net Framework application.**</span></span>  
  
 <span data-ttu-id="56d4e-181">コード例を参照するには、 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)上の DAC サンプル アプリケーションをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="56d4e-181">To view a code example, download the DAC sample application on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)</span></span>  
  
1.  <span data-ttu-id="56d4e-182">SMO サーバー オブジェクトを作成し、配置するデータベースがあるインスタンスまたはサーバーに設定します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-182">Create a SMO Server object and set it to the instance or server that contains the database to be deployed.</span></span>  
  
2.  <span data-ttu-id="56d4e-183">`ServerConnection` オブジェクトを開いて、同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-183">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="56d4e-184">`Export` 型の `Microsoft.SqlServer.Management.Dac.DacStore` メソッドを使用して、BACPAC ファイルにデータベースをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="56d4e-184">Use the `Export` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to export the database to a BACPAC file.</span></span> <span data-ttu-id="56d4e-185">エクスポートするデータベースの名前と、BACPAC ファイルの出力先となるフォルダーのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-185">Specify the name of the database to be exported, and the path to the folder where the BACPAC file is to be placed.</span></span>  
  
4.  <span data-ttu-id="56d4e-186">SMO サーバー オブジェクトを作成し、配置先インスタンスまたはサーバーに設定します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-186">Create a SMO Server object and set it to the destination instance or server.</span></span>  
  
5.  <span data-ttu-id="56d4e-187">`ServerConnection` オブジェクトを開いて、同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-187">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
6.  <span data-ttu-id="56d4e-188">`Import` 型の `Microsoft.SqlServer.Management.Dac.DacStore` メソッドを使用して、BACPAC をインポートします。</span><span class="sxs-lookup"><span data-stu-id="56d4e-188">Use the `Import` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to import the BACPAC.</span></span> <span data-ttu-id="56d4e-189">エクスポートによって作成された BACPAC ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="56d4e-189">Specify the BACPAC file created by the export.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d4e-190">参照</span><span class="sxs-lookup"><span data-stu-id="56d4e-190">See Also</span></span>  
 <span data-ttu-id="56d4e-191">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="56d4e-191">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="56d4e-192">[データ層アプリケーションのエクスポート](export-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="56d4e-192">[Export a Data-tier Application](export-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="56d4e-193">BACPAC ファイルのインポートによる新しいユーザー データベースの作成</span><span class="sxs-lookup"><span data-stu-id="56d4e-193">Import a BACPAC File to Create a New User Database</span></span>](import-a-bacpac-file-to-create-a-new-user-database.md)  
  
  
