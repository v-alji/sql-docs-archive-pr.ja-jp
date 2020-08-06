---
title: データ層アプリケーションの配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploydacwizard.updateconfiguration.f1
- sql12.swb.deploydacwizard.selectdac.f1
- sql12.swb.deploydacwizard.deploydac.f1
- sql12.swb.deploydacwizard.introduction.f1
- sql12.swb.deploydacwizard.summary.f1
helpviewer_keywords:
- Deploy data-tier application
- deploy DAC
- data-tier application [SQL Server], deploy
- How to [DAC], deploy
- wizard [DAC], deploy
ms.assetid: c117af35-aa53-44a5-8034-fa8715dc735f
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd4a09eed946863064728fd8c62230121ad3d403
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740038"
---
# <a name="deploy-a-data-tier-application"></a><span data-ttu-id="e442b-102">データ層アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="e442b-102">Deploy a Data-tier Application</span></span>
  <span data-ttu-id="e442b-103">ウィザードまたは PowerShell スクリプトを使用して、データ層アプリケーション (DAC) パッケージから [!INCLUDE[ssDE](../../includes/ssde-md.md)] または [!INCLUDE[ssSDS](../../includes/sssds-md.md)] の既存のインスタンスに DAC を配置できます。</span><span class="sxs-lookup"><span data-stu-id="e442b-103">You can deploy a data-tier application (DAC) from a DAC package to an existing instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] or [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using a wizard or a PowerShell script.</span></span> <span data-ttu-id="e442b-104">配置プロセスでは、 **msdb** システム データベース (**では** master [!INCLUDE[ssSDS](../../includes/sssds-md.md)]データベース) に DAC 定義を格納することで DAC インスタンスを登録し、データベースを作成して、DAC で定義されたすべてのデータベース オブジェクトをそのデータベースに設定します。</span><span class="sxs-lookup"><span data-stu-id="e442b-104">The deployment process registers a DAC instance by storing the DAC definition in the **msdb** system database (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]), creates a database, and then populates the database with all the database objects defined in the DAC.</span></span>  
  
-   <span data-ttu-id="e442b-105">**作業を開始する準備:**  [SQL Server ユーティリティ](#SQLUtility)、 [データベースのオプションと設定](#DBOptSettings)、 [制限事項と制約事項](#LimitationsRestrictions)、 [前提条件](#Prerequisites)、 [セキュリティ](#Security)、 [権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="e442b-105">**Before you begin:**  [SQL Server Utility](#SQLUtility), [Database Options and Settings](#DBOptSettings), [Limitations and Restrictions](#LimitationsRestrictions), [Prerequisites](#Prerequisites), [Security](#Security), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="e442b-106">**DAC を配置するために使用するもの:**  [データ層アプリケーションの配置ウィザード](#UsingDeployDACWizard)、 [PowerShell](#DeployDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="e442b-106">**To deploy a DAC, using:**  [The Deploy Data-tier Application Wizard](#UsingDeployDACWizard), [PowerShell](#DeployDACPowerShell)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> <span data-ttu-id="e442b-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="e442b-107">Before You Begin</span></span>  
 <span data-ttu-id="e442b-108">同じ DAC パッケージを [!INCLUDE[ssDE](../../includes/ssde-md.md)] の単一のインスタンスに複数回配置することはできますが、配置は一度に 1 つずつ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e442b-108">The same DAC package can be deployed to a single instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] multiple times, however the deployments must be run one at a time.</span></span> <span data-ttu-id="e442b-109">各配置に指定される DAC インスタンス名は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンス内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e442b-109">The DAC instance name specified for each deployment must be unique within the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
###  <a name="sql-server-utility"></a><a name="SQLUtility"></a><span data-ttu-id="e442b-110">SQL Server ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="e442b-110">SQL Server Utility</span></span>  
 <span data-ttu-id="e442b-111">データベース エンジンのマネージド インスタンスに DAC を配置した場合、その配置した DAC は、次回ユーティリティ コレクション セットがインスタンスからユーティリティ コントロール ポイントへと送信されるときに SQL Server ユーティリティに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="e442b-111">If you deploy a DAC to a managed instance of the Database Engine, the deployed DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="e442b-112">その後、DAC は [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の**ユーティリティ エクスプローラー**の **[配置済みのデータ層アプリケーション]** ノードに現れるようになり、 **[配置済みのデータ層アプリケーション]** の詳細ページで報告されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-112">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a><span data-ttu-id="e442b-113">データベースのオプションと設定</span><span class="sxs-lookup"><span data-stu-id="e442b-113">Database Options and Settings</span></span>  
 <span data-ttu-id="e442b-114">既定では、配置中に作成されたデータベースには、CREATE DATABASE ステートメントによる既定の設定すべてが適用されます。ただし、次の設定は除きます。</span><span class="sxs-lookup"><span data-stu-id="e442b-114">By default, the database created during the deployment will have all of the default settings from the CREATE DATABASE statement, except:</span></span>  
  
-   <span data-ttu-id="e442b-115">データベースの照合順序および互換性レベルは、DAC パッケージで定義された値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-115">The database collation and compatibility level are set to the values defined in the DAC package.</span></span> <span data-ttu-id="e442b-116">SQL Server 開発者ツールでデータベース プロジェクトから構築された DAC パッケージでは、データベース プロジェクトに設定された値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-116">A DAC package built from a database project in the SQL Server Developer Tools uses the values set in the database project.</span></span> <span data-ttu-id="e442b-117">既存のデータベースから抽出されたパッケージでは、元のデータベースの値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-117">A package extracted from an existing database uses the values from the original database.</span></span>  
  
-   <span data-ttu-id="e442b-118">一部のデータベース設定 (データベース名やファイル パスなど) は、 **[構成の更新]** ページで調整できます。</span><span class="sxs-lookup"><span data-stu-id="e442b-118">You can adjust some of the database settings, such as database name and file paths, in the **Update Configuration** page.</span></span> <span data-ttu-id="e442b-119">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]に配置する場合、ファイル パスは設定できません。</span><span class="sxs-lookup"><span data-stu-id="e442b-119">You cannot set the file paths when deploying to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
 <span data-ttu-id="e442b-120">TRUSTWORTHY、DB_CHAINING、HONOR_BROKER_PRIORITY など、データベース オプションによっては、配置作業中の調整はできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e442b-120">Some database options, such as TRUSTWORTHY, DB_CHAINING, and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the deployment process.</span></span> <span data-ttu-id="e442b-121">ファイル グループの数、ファイルの数やサイズなどの物理プロパティは、配置作業中に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="e442b-121">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the deployment process.</span></span> <span data-ttu-id="e442b-122">配置が完了すれば、ALTER DATABASE ステートメント、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell を使用して、データベースを調整できます。</span><span class="sxs-lookup"><span data-stu-id="e442b-122">After the deployment completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="e442b-123">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e442b-123">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e442b-124">DAC を配置できるのは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、または [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 4 (SP4) 以降を実行している [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e442b-124">A DAC can be deployed to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="e442b-125">新しいバージョンを使用して DAC を作成した場合、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ではサポートされないオブジェクトが DAC に含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e442b-125">If you create a DAC using a later version, the DAC may contain objects not supported by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="e442b-126">このような DAC を [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]のインスタンスに配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="e442b-126">You cannot deploy those DACs to instances of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="e442b-127">前提条件</span><span class="sxs-lookup"><span data-stu-id="e442b-127">Prerequisites</span></span>  
 <span data-ttu-id="e442b-128">ソースが不明または信頼されていない DAC パッケージは配置しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e442b-128">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="e442b-129">こうしたパッケージには、意図しない Transact-SQL コードを実行したり、スキーマを変更してエラーを発生したりする、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e442b-129">Such packages could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="e442b-130">パッケージのソースが不明または信頼されていない場合は、使用する前に、DAC をアンパックして、ストアド プロシージャやその他のユーザー定義コードなどのコードもご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e442b-130">Before you use a package from an unknown or untrusted source, unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span> <span data-ttu-id="e442b-131">これらのチェックの実行方法の詳細については、「 [Validate a DAC Package](validate-a-dac-package.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e442b-131">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e442b-132">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e442b-132">Security</span></span>  
 <span data-ttu-id="e442b-133">セキュリティを強化するために、SQL Server 認証のログインは、パスワードなしで DAC パッケージに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-133">To improve security, SQL Server Authentication logins are stored in a DAC package without a password.</span></span> <span data-ttu-id="e442b-134">パッケージが配置またはアップグレードされると、ログインは、生成されたパスワードを伴う無効なログインとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-134">When the package is deployed or upgraded, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="e442b-135">ログインを有効にするには、ALTER ANY LOGIN 権限を持つユーザーとしてログインし、ALTER LOGIN を使用してログインを有効にします。さらに、新しいパスワードを割り当て、そのパスワードを該当ユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e442b-135">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="e442b-136">Windows 認証ログインの場合、ログインのパスワードは SQL Server で管理されていないため、この操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e442b-136">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e442b-137">Permissions</span><span class="sxs-lookup"><span data-stu-id="e442b-137">Permissions</span></span>  
 <span data-ttu-id="e442b-138">DAC を配置できるのは、 **sysadmin** または **serveradmin** 固定サーバー ロールのメンバーか、 **dbcreator** 固定サーバー ロールに存在する ALTER ANY LOGIN 権限を持つログインのみです。</span><span class="sxs-lookup"><span data-stu-id="e442b-138">A DAC can only be deployed by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="e442b-139">あらかじめ登録された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者アカウント ( **sa** ) でも DAC を配置できます。</span><span class="sxs-lookup"><span data-stu-id="e442b-139">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also deploy a DAC.</span></span> <span data-ttu-id="e442b-140">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] へのログインが含まれる DAC を配置するには、loginmanager ロールまたは serveradmin ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="e442b-140">Deploying a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="e442b-141">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] へのログインが含まれない DAC を配置するには、dbmanager ロールまたは serveradmin ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="e442b-141">Deploying a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
##  <a name="using-the-deploy-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a><span data-ttu-id="e442b-142">データ層アプリケーションの配置ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="e442b-142">Using the Deploy Data-tier Application Wizard</span></span>  
 <span data-ttu-id="e442b-143">**ウィザードを使用して DAC を配置するには**</span><span class="sxs-lookup"><span data-stu-id="e442b-143">**To Deploy a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="e442b-144">**オブジェクト エクスプローラー**で、DAC を配置するインスタンスのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="e442b-144">In **Object Explorer**, expand the node for the instance to which you want to deploy the DAC.</span></span>  
  
2.  <span data-ttu-id="e442b-145">**[データベース]** ノードを右クリックし、**[データ層アプリケーションの配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e442b-145">Right-click the **Databases** node, then select **Deploy Data-tier Application...**</span></span>  
  
3.  <span data-ttu-id="e442b-146">ウィザードの各ダイアログの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e442b-146">Complete the wizard dialogs:</span></span>  
  
    -   <span data-ttu-id="e442b-147">[[説明] ページ](#Introduction)</span><span class="sxs-lookup"><span data-stu-id="e442b-147">[Introduction Page](#Introduction)</span></span>  
  
    -   <span data-ttu-id="e442b-148">[[DAC パッケージの選択] ページ](#Select_dac_package)</span><span class="sxs-lookup"><span data-stu-id="e442b-148">[Select DAC Package Page](#Select_dac_package)</span></span>  
  
    -   <span data-ttu-id="e442b-149">[[ポリシーの確認] ページ](#Review_policy)</span><span class="sxs-lookup"><span data-stu-id="e442b-149">[Review Policy Page](#Review_policy)</span></span>  
  
    -   <span data-ttu-id="e442b-150">[[構成の更新] ページ](#Update_configuration)</span><span class="sxs-lookup"><span data-stu-id="e442b-150">[Update Configuration Page](#Update_configuration)</span></span>  
  
    -   <span data-ttu-id="e442b-151">[[概要] ページ](#Summary)</span><span class="sxs-lookup"><span data-stu-id="e442b-151">[Summary Page](#Summary)</span></span>  
  
    -   <span data-ttu-id="e442b-152">[[配置] ページ](#Deploy)</span><span class="sxs-lookup"><span data-stu-id="e442b-152">[Deploy Page](#Deploy)</span></span>  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="e442b-153">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="e442b-153">Introduction Page</span></span>  
 <span data-ttu-id="e442b-154">このページでは、データ層アプリケーションを配置する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e442b-154">This page describes the steps for deploying a data-tier application.</span></span>  
  
 <span data-ttu-id="e442b-155">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="e442b-155">**Do not show this page again.**</span></span> <span data-ttu-id="e442b-156">: 今後このページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e442b-156">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="e442b-157">**[次へ >]**: **[DAC パッケージの選択]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="e442b-157">**Next >** - Proceeds to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="e442b-158">**[キャンセル]**: DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e442b-158">**Cancel** - Terminates the wizard without deploying a DAC.</span></span>  
  
##  <a name="select-dac-package-page"></a><a name="Select_dac_package"></a><span data-ttu-id="e442b-159">[DAC パッケージの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="e442b-159">Select DAC Package Page</span></span>  
 <span data-ttu-id="e442b-160">このページでは、配置するデータ層アプリケーションを含む DAC パッケージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e442b-160">Use this page to specify the DAC package that contains the data-tier application to be deployed.</span></span> <span data-ttu-id="e442b-161">このページは、3 つの状態を遷移します。</span><span class="sxs-lookup"><span data-stu-id="e442b-161">The page transitions through three states.</span></span>  
  
### <a name="select-the-dac-package"></a><span data-ttu-id="e442b-162">DAC パッケージの選択</span><span class="sxs-lookup"><span data-stu-id="e442b-162">Select the DAC Package</span></span>  
 <span data-ttu-id="e442b-163">ページの初期状態では、配置する DAC パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="e442b-163">Use the initial state of the page to choose the DAC package to deploy.</span></span> <span data-ttu-id="e442b-164">DAC パッケージは有効な DAC パッケージ ファイルで、拡張子は .dacpac である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e442b-164">The DAC package must be a valid DAC package file and must have a .dacpac extension.</span></span>  
  
 <span data-ttu-id="e442b-165">**[DAC パッケージ]** : 配置するデータ層アプリケーションを含む DAC パッケージのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e442b-165">**DAC Package** - Specify the path and file name of the DAC package that contains the data-tier application to be deployed.</span></span> <span data-ttu-id="e442b-166">ボックスの右にある **[参照]** をクリックして、DAC パッケージの場所に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="e442b-166">You can select the **Browse** button at the right of the box to browse to the location of the DAC package.</span></span>  
  
 <span data-ttu-id="e442b-167">**[アプリケーション名]** : DAC が作成されたとき、またはデータベースから抽出されたときに割り当てられた DAC 名が表示される読み取り専用のボックスです。</span><span class="sxs-lookup"><span data-stu-id="e442b-167">**Application Name** - A read-only box that displays the DAC name assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="e442b-168">**[バージョン]** : DAC が作成されたとき、またはデータベースから抽出されたときに割り当てられたバージョンが表示される読み取り専用のボックスです。</span><span class="sxs-lookup"><span data-stu-id="e442b-168">**Version** - A read-only box that displays the version assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="e442b-169">**[説明]** : DAC が作成されたとき、またはデータベースから抽出されたときに記述された説明が表示される読み取り専用のボックスです。</span><span class="sxs-lookup"><span data-stu-id="e442b-169">**Description** - A read-only box that displays the description written when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="e442b-170">\*\* \< Previous\*\* -[**概要**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="e442b-170">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="e442b-171">**[次へ]** : 選択したファイルが有効な DAC パッケージかどうかが確認され、進捗状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-171">**Next >** - Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span>  
  
 <span data-ttu-id="e442b-172">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e442b-172">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
### <a name="validating-the-dac-package"></a><span data-ttu-id="e442b-173">DAC パッケージの検証</span><span class="sxs-lookup"><span data-stu-id="e442b-173">Validating the DAC Package</span></span>  
 <span data-ttu-id="e442b-174">選択したファイルが有効な DAC パッケージかどうかが確認され、進捗状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-174">Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span> <span data-ttu-id="e442b-175">DAC パッケージが検証されると、 **[DAC パッケージの選択]** ページの最終状態に進み、検証の結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e442b-175">If the DAC package is validated, the wizard proceeds to the final version of the **Select Package** page where you can review the results of the validation.</span></span> <span data-ttu-id="e442b-176">ファイルが有効な DAC パッケージでない場合は、 **[DAC パッケージの選択]** が表示されたままになります。</span><span class="sxs-lookup"><span data-stu-id="e442b-176">If the file is not a valid DAC package, the wizard remains on the **Select DAC Package**.</span></span> <span data-ttu-id="e442b-177">別の有効な DAC パッケージを選択するか、ウィザードを取り消して新しい DAC パッケージを生成してください。</span><span class="sxs-lookup"><span data-stu-id="e442b-177">Either select another valid DAC package or cancel the wizard and generate a new DAC package.</span></span>  
  
 <span data-ttu-id="e442b-178">**[DAC パッケージの内容を検証しています]** : 検証プロセスの現在の状態を示す進捗状況バーです。</span><span class="sxs-lookup"><span data-stu-id="e442b-178">**Validating the contents of the DAC** - The progress bar that reports the current status of the validation process.</span></span>  
  
 <span data-ttu-id="e442b-179">[ \*\* \< 戻る\*\* **]: [パッケージの選択**] ページの初期状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="e442b-179">**\< Previous** - Returns to the initial state of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="e442b-180">**[次へ >]**: **[パッケージの選択]** ページの最終状態に進みます。</span><span class="sxs-lookup"><span data-stu-id="e442b-180">**Next >** - Proceeds to the final version of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="e442b-181">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e442b-181">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a><span data-ttu-id="e442b-182">[ポリシーの確認] ページ</span><span class="sxs-lookup"><span data-stu-id="e442b-182">Review Policy Page</span></span>  
 <span data-ttu-id="e442b-183">このページでは、DAC にポリシーが含まれている場合に DAC サーバーの選択ポリシーを評価した結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="e442b-183">Use this page to review the results of evaluating the DAC server selection policy, if the DAC has a policy.</span></span> <span data-ttu-id="e442b-184">DAC サーバーの選択ポリシーは、省略可能で、Visual Studio で DAC を作成するときに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e442b-184">The DAC server selection policy is optional, and is assigned to the DAC when it is created in Visual Studio.</span></span> <span data-ttu-id="e442b-185">このポリシーでは、サーバーの選択ポリシーのファセットを使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスで DAC をホストするために満たす必要がある条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="e442b-185">The policy uses the server selection policy facets to specify conditions an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] should meet to host the DAC.</span></span>  
  
 <span data-ttu-id="e442b-186">**[ポリシー条件の評価結果]** : DAC 配置ポリシーの条件が満たされたかどうかを示す読み取り専用のレポートです。</span><span class="sxs-lookup"><span data-stu-id="e442b-186">**Evaluation results of policy conditions** - A read-only report showing whether the conditions of the DAC deployment policy succeeded.</span></span> <span data-ttu-id="e442b-187">各条件の評価結果が、レポートの各行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-187">The results of evaluating each condition are reported on a separate line.</span></span>  
  
 <span data-ttu-id="e442b-188">サーバーの選択ポリシー (オペレーティング システムのバージョン、言語、名前付きパイプの有効化、プラットフォーム、および TCP の有効化) は、DAC を [!INCLUDE[ssSDS](../../includes/sssds-md.md)]に配置する場合は常に false となります。</span><span class="sxs-lookup"><span data-stu-id="e442b-188">The following server selection policies always evaluate to false when deploying a DAC to [!INCLUDE[ssSDS](../../includes/sssds-md.md)]: operating system version, language, named pipes enabled, platform, and tcp enabled.</span></span>  
  
 <span data-ttu-id="e442b-189">**[ポリシー違反を無視します]** : ポリシー条件が満たされていない場合に配置を続行するには、このチェック ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e442b-189">**Ignore policy violations** - Use this check box to proceed with the deployment if one or more of the policy conditions failed.</span></span> <span data-ttu-id="e442b-190">すべての条件が満たされていなくても DAC を正常に操作できるようにする場合のみ、このチェック ボックスをオンにしてください。</span><span class="sxs-lookup"><span data-stu-id="e442b-190">Only select this option if you are sure that all of the conditions which failed will not prevent the successful operation of the DAC.</span></span>  
  
 <span data-ttu-id="e442b-191">[ \*\* \< 戻る\*\* **]: [パッケージの選択**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="e442b-191">**\< Previous** - Returns to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="e442b-192">**[次へ >]**: **[構成の更新]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="e442b-192">**Next >** - Proceeds to the **Update Configureation** page.</span></span>  
  
 <span data-ttu-id="e442b-193">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e442b-193">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="update-configuration-page"></a><a name="Update_configuration"></a><span data-ttu-id="e442b-194">[構成の更新] ページ</span><span class="sxs-lookup"><span data-stu-id="e442b-194">Update Configuration Page</span></span>  
 <span data-ttu-id="e442b-195">このページでは、配置された DAC インスタンスと配置によって作成されたデータベースの名前を指定し、データベース オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e442b-195">Use this page to specify the names of the deployed DAC instance and the database created by the deployment, and to set database options.</span></span>  
  
 <span data-ttu-id="e442b-196">**[データベース名]** : 配置によって作成されるデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e442b-196">**Database Name:** - Specify the name of the database to be created by the deployment.</span></span> <span data-ttu-id="e442b-197">既定では、DAC の抽出元であるソース データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="e442b-197">The default is the name of the source database the DAC was extracted from.</span></span> <span data-ttu-id="e442b-198">この名前は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンス内で一意であり、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 識別子のルールに従っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e442b-198">The name must be unique within the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and comply with the rules for [!INCLUDE[ssDE](../../includes/ssde-md.md)] identifiers.</span></span>  
  
 <span data-ttu-id="e442b-199">データベース名を変更した場合、データ ファイルとログ ファイルの名前も新しいデータベース名に合わせて変更されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-199">If you change the database name, the names of the data file and log files will change to match the new value.</span></span>  
  
 <span data-ttu-id="e442b-200">また、データベース名は、DAC インスタンスの名前としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-200">The database name is also used as the name of the DAC instance.</span></span> <span data-ttu-id="e442b-201">インスタンス名は、 **オブジェクト エクスプローラー** の **[データ層アプリケーション]** ノードまたは **ユーティリティ エクスプローラー** の **[配置済みのデータ層アプリケーション]** ノードの下にある、DAC のノードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-201">The instance name is displayed on the node for the DAC under the **Data-tier Applications** node in **Object Explorer**, or the **Deployed Data-tier Applications** node in the **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="e442b-202">次のオプションは [!INCLUDE[ssSDS](../../includes/sssds-md.md)]には適用されず、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]の配置時には表示されません。</span><span class="sxs-lookup"><span data-stu-id="e442b-202">The following options do not apply to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], and are not displayed when deploying to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
 <span data-ttu-id="e442b-203">**[既定のデータベースの場所の使用]** : データベースのデータ ファイルおよびログ ファイルを [!INCLUDE[ssDE](../../includes/ssde-md.md)]インスタンスの既定の場所に作成するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e442b-203">**Use the default database location** - Select this option to create the database data and log files in the default location for the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="e442b-204">ファイル名は、データベース名を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-204">The file names will be built using the database name.</span></span>  
  
 <span data-ttu-id="e442b-205">**[データベース ファイルの指定]** : データ ファイルおよびログ ファイルに別の場所または名前を指定するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e442b-205">**Specify database files** - Select this option to specify a different location or name for the data and log files.</span></span>  
  
 <span data-ttu-id="e442b-206">**[データ ファイルのパスと名前]** : データ ファイルの完全パスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e442b-206">**Data file path and name: -** Specify the full path and file name for the data file.</span></span> <span data-ttu-id="e442b-207">このボックスには、既定のパスとファイル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-207">The box is populated with the default path and file name.</span></span> <span data-ttu-id="e442b-208">ボックス内の文字列を編集して既定値を変更するか、[参照] をクリックしてデータ ファイルを配置するフォルダーに移動してください。</span><span class="sxs-lookup"><span data-stu-id="e442b-208">Edit the string in the box to change the default, or use the Browse button to navigate to the folder where the data file is to be placed.</span></span>  
  
 <span data-ttu-id="e442b-209">**[ログ ファイルのパスと名前]** : ログ ファイルの完全パスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e442b-209">**Log file path and name:** - Specify the full path and file name for the log file.</span></span> <span data-ttu-id="e442b-210">このボックスには、既定のパスとファイル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-210">The box is populated with the default path and file name.</span></span> <span data-ttu-id="e442b-211">ボックス内の文字列を編集して既定値を変更するか、 **[参照]** をクリックしてログ ファイルを配置するフォルダーに移動してください。</span><span class="sxs-lookup"><span data-stu-id="e442b-211">Edit the string in the box to change the default, or use the **Browse** button to navigate to the folder where the log file is to be placed.</span></span>  
  
 <span data-ttu-id="e442b-212">[ \*\* \< 戻る\*\* **]: [DAC パッケージの選択**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="e442b-212">**\< Previous** - Returns to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="e442b-213">**[次へ]** : **[概要]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="e442b-213">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="e442b-214">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e442b-214">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="e442b-215">[概要] ページ</span><span class="sxs-lookup"><span data-stu-id="e442b-215">Summary Page</span></span>  
 <span data-ttu-id="e442b-216">このページでは、DAC の配置時にウィザードが行うアクションを確認します。</span><span class="sxs-lookup"><span data-stu-id="e442b-216">Use this page to review the actions the wizard will take when deploying the DAC.</span></span>  
  
 <span data-ttu-id="e442b-217">**[次の設定を使用して DAC を配置します。]**</span><span class="sxs-lookup"><span data-stu-id="e442b-217">**The following settings will be used to deploy your DAC.**</span></span> <span data-ttu-id="e442b-218">: 表示された情報を確認し、実行されるアクションが正しいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e442b-218">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="e442b-219">このウィンドウには、選択した DAC パッケージと、配置される DAC インスタンス用に選択した名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-219">The window displays the DAC package you selected, and the name you selected for the deployed DAC instance.</span></span> <span data-ttu-id="e442b-220">また、DAC に関連付けられたデータベースを作成する際に使用される設定も表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-220">The window also displays the settings that will be used when creating the database associated with the DAC.</span></span>  
  
 <span data-ttu-id="e442b-221">[ \*\* \< 前**へ]-[**構成の更新\*\*] ページに戻り、選択内容を変更します。</span><span class="sxs-lookup"><span data-stu-id="e442b-221">**\< Previous** - Returns you to the **Update Configuration** page to change your selections.</span></span>  
  
 <span data-ttu-id="e442b-222">**[次へ >]**: DAC を配置し、**[DAC の配置]** ページに結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="e442b-222">**Next >** - Deploys the DAC and displays the results in the **Deploy DAC** page.</span></span>  
  
 <span data-ttu-id="e442b-223">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e442b-223">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="deploy-page"></a><a name="Deploy"></a><span data-ttu-id="e442b-224">[配置] ページ</span><span class="sxs-lookup"><span data-stu-id="e442b-224">Deploy Page</span></span>  
 <span data-ttu-id="e442b-225">このページには、配置操作の成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-225">This page reports the success or failure of the deploy operation.</span></span>  
  
 <span data-ttu-id="e442b-226">**[DAC を配置しています]** : DAC を配置するために行った各アクションの成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-226">**Deploying the DAC** - Reports the success or failure of each action taken to deploy the DAC.</span></span> <span data-ttu-id="e442b-227">内容を確認して、各アクションの成功または失敗を判断します。</span><span class="sxs-lookup"><span data-stu-id="e442b-227">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="e442b-228">エラーが発生したアクションには、 **[結果]** 列にリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-228">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="e442b-229">そのアクションのエラーのレポートを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e442b-229">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="e442b-230">**[レポートの保存]** : 配置レポートを HTML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="e442b-230">**Save Report** - Select this button to save the deployment report to an HTML file.</span></span> <span data-ttu-id="e442b-231">ファイルには、アクションで発生したすべてのエラーを含む、各アクションのステータスが報告されます。</span><span class="sxs-lookup"><span data-stu-id="e442b-231">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="e442b-232">既定のフォルダーは、Windows アカウントの Documents フォルダーにある SQL Server Management Studio\DAC Packages フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="e442b-232">The default folder is the SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="e442b-233">**[完了]** : ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e442b-233">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="using-powershell"></a><a name="DeployDACPowerShell"></a><span data-ttu-id="e442b-234">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="e442b-234">Using PowerShell</span></span>  
 <span data-ttu-id="e442b-235">**PowerShell スクリプトから Install() メソッドを使用して DAC を配置するには**</span><span class="sxs-lookup"><span data-stu-id="e442b-235">**To deploy a DAC using the Install() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="e442b-236">SMO サーバー オブジェクトを作成し、DAC を配置するインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="e442b-236">Create a SMO Server object and set it to the instance to which you want to deploy the DAC.</span></span>  
  
2.  <span data-ttu-id="e442b-237">`ServerConnection` オブジェクトを開いて、同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e442b-237">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="e442b-238">`System.IO.File` を使用して、DAC パッケージ ファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e442b-238">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="e442b-239">`add_DacActionStarted` および `add_DacActionFinished` を使用して、DAC 配置イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e442b-239">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC deployment events.</span></span>  
  
5.  <span data-ttu-id="e442b-240">を設定 `DatabaseDeploymentProperties` します。</span><span class="sxs-lookup"><span data-stu-id="e442b-240">Set the `DatabaseDeploymentProperties`.</span></span>  
  
6.  <span data-ttu-id="e442b-241">`DacStore.Install` メソッドを使用して DAC を配置します。</span><span class="sxs-lookup"><span data-stu-id="e442b-241">Use the `DacStore.Install` method to deploy the DAC.</span></span>  
  
7.  <span data-ttu-id="e442b-242">DAC パッケージ ファイルの読み取りに使用するファイル ストリームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e442b-242">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="e442b-243">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="e442b-243">Example (PowerShell)</span></span>  
 <span data-ttu-id="e442b-244">次の例では、MyApplication.dacpac パッケージから DAC 定義を使用して、MyApplication という名前の DAC を [!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスに配置します。</span><span class="sxs-lookup"><span data-stu-id="e442b-244">The following example deploys a DAC named MyApplication on a default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], using a DAC definition from a MyApplication.dacpac package.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Subscribe to the DAC deployment events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Deploy the DAC and create the database.  
$dacName  = "MyApplication"  
$evaluateTSPolicy = $true  
$deployProperties = New-Object Microsoft.SqlServer.Management.Dac.DatabaseDeploymentProperties($serverconnection,$dacName)  
$dacstore.Install($dacType, $deployProperties, $evaluateTSPolicy)  
$fileStream.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="e442b-245">参照</span><span class="sxs-lookup"><span data-stu-id="e442b-245">See Also</span></span>  
 <span data-ttu-id="e442b-246">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e442b-246">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="e442b-247">[データベースから DAC を抽出する](extract-a-dac-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="e442b-247">[Extract a DAC From a Database](extract-a-dac-from-a-database.md) </span></span>  
 [<span data-ttu-id="e442b-248">データベース識別子</span><span class="sxs-lookup"><span data-stu-id="e442b-248">Database Identifiers</span></span>](../databases/database-identifiers.md)  
