---
title: SharePoint 2013 用の SharePoint モードのインストール Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: b29d0f45-0068-4c84-bd7e-5b8a9cd1b538
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9190f990503a66a088351323effa6c17695f9757
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646002"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2013"></a><span data-ttu-id="51ed0-102">SharePoint 2013 用 Reporting Services の SharePoint モードのインストール</span><span class="sxs-lookup"><span data-stu-id="51ed0-102">Install Reporting Services SharePoint Mode for SharePoint 2013</span></span>
  <span data-ttu-id="51ed0-103">このトピックでは、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のシングル サーバー インストールの手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-103">The procedures in this topic guide you through a single server installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="51ed0-104">手順には、SQL Server インストール ウィザードの実行と、SharePoint サーバーの全体管理を使用する構成タスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-104">The steps include running the SQL Server installation wizard as well as configuration tasks that use SharePoint Central Administration.</span></span> <span data-ttu-id="51ed0-105">また、既存のインストールの更新について個々の手順 ( [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-105">The topic can also be used for individual procedures for updating an existing installation, for example to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
||  
|-|  
|<span data-ttu-id="51ed0-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124;**メモ:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint モードでは、sharepoint Server マルチテナントはサポート**されていません**。</span><span class="sxs-lookup"><span data-stu-id="51ed0-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; **Note:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode does **not** support SharePoint Server multi-tenancy.</span></span>|  
  
 <span data-ttu-id="51ed0-107">既存のファームへの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバーの追加については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-107">For information on adding more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers to an existing farm, see the following:</span></span>  
  
-   [<span data-ttu-id="51ed0-108">ファームへのレポート サーバーの追加 &#40;SSRS スケールアウト&#41;</span><span class="sxs-lookup"><span data-stu-id="51ed0-108">Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;</span></span>](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
-   [<span data-ttu-id="51ed0-109">ファームへの Reporting Services Web フロントエンドの追加</span><span class="sxs-lookup"><span data-stu-id="51ed0-109">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 <span data-ttu-id="51ed0-110">シングル サーバー インストールは、開発およびテストのシナリオには便利ですが、運用環境にはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-110">A single server installation is useful for development and testing scenarios but it is not recommended for production environments.</span></span>  
  
 <span data-ttu-id="51ed0-111">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="51ed0-111">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="51ed0-112">シングルサーバー配置の例</span><span class="sxs-lookup"><span data-stu-id="51ed0-112">Example Single-Server Deployment</span></span>](#bkmk_singleserver)  
  
-   [<span data-ttu-id="51ed0-113">セットアップアカウント</span><span class="sxs-lookup"><span data-stu-id="51ed0-113">Setup accounts</span></span>](#bkmk_setupaccounts)  
  
-   [<span data-ttu-id="51ed0-114">手順 1. SharePoint モードの Reporting Services レポート サーバーのインストール</span><span class="sxs-lookup"><span data-stu-id="51ed0-114">Step 1: Install Reporting Services Report Server in SharePoint mode</span></span>](#bkmk_install_SSRS)  
  
-   [<span data-ttu-id="51ed0-115">手順 2: Reporting Services SharePoint サービスを登録して開始する</span><span class="sxs-lookup"><span data-stu-id="51ed0-115">Step 2: Register and Start the Reporting Services SharePoint Service</span></span>](#bkmk_install_SSRS_sharedservice)  
  
-   [<span data-ttu-id="51ed0-116">手順 3: Reporting Services サービスアプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="51ed0-116">Step 3: Create a Reporting Services Service Application</span></span>](#bkmk_create_serrviceapplication)  
  
-   [<span data-ttu-id="51ed0-117">手順 4: Power View サイトコレクション機能をアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-117">Step 4: Activate the Power View Site Collection Feature.</span></span>](#bkmk_powerview)  
  
-   [<span data-ttu-id="51ed0-118">手順1-4 の Windows PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="51ed0-118">Windows PowerShell script for Steps 1-4</span></span>](#bkmk_full_script)  
  
-   <span data-ttu-id="51ed0-119">[Additional Configuration](#bkmk_additional_config) (サブスクリプションと警告の準備、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンテンツの種類、Analysis Services サーバーを使用するための Excel Services の構成など)</span><span class="sxs-lookup"><span data-stu-id="51ed0-119">[Additional Configuration](#bkmk_additional_config) including provisioning for subscriptions and alerts, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] content types, and configuring Excel Services to Use an Analysis Services Server.</span></span>  
  
-   [<span data-ttu-id="51ed0-120">インストールの確認</span><span class="sxs-lookup"><span data-stu-id="51ed0-120">Verify the installation</span></span>](#bkmk_verify_installation)  
  
##  <a name="example-single-server-deployment"></a><a name="bkmk_singleserver"></a><span data-ttu-id="51ed0-121">シングルサーバー配置の例</span><span class="sxs-lookup"><span data-stu-id="51ed0-121">Example Single-Server Deployment</span></span>  
 <span data-ttu-id="51ed0-122">シングル サーバー インストールは、開発およびテストのシナリオには便利ですが、シングル サーバーは運用環境にはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-122">A single-server installation is useful for development and testing scenarios but a single-server is not recommended for a production environment.</span></span> <span data-ttu-id="51ed0-123">シングル サーバー環境とは、同じコンピューターに SharePoint と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントがインストールされた 1 台のコンピューターのことです。</span><span class="sxs-lookup"><span data-stu-id="51ed0-123">The single-server environment refers to a single computer that has SharePoint and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components installed on the same computer.</span></span> <span data-ttu-id="51ed0-124">このトピックでは、複数の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバーへのスケールアウトについては説明しません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-124">The topic does not cover scale-out with multiple [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="51ed0-125">次の図は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のシングル サーバー配置に含まれるコンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="51ed0-125">The following diagram illustrates the components that are part of a single server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] deployment.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51ed0-126">**(1)**</span><span class="sxs-lookup"><span data-stu-id="51ed0-126">**(1)**</span></span>|<span data-ttu-id="51ed0-127">SharePoint サービス: SQL Server をインストールすると、インストールされます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-127">SharePoint service installed from SQL Server installation.</span></span> <span data-ttu-id="51ed0-128">1 つ以上の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-128">You can create one or more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>|  
|<span data-ttu-id="51ed0-129">**3**</span><span class="sxs-lookup"><span data-stu-id="51ed0-129">**(2)**</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="51ed0-130">SharePoint 製品用アドイン: SharePoint サーバーにユーザー インターフェイス コンポーネントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-130">add-in for SharePoint products provides the user interface components on the SharePoint Servers.</span></span>|  
|<span data-ttu-id="51ed0-131">**番**</span><span class="sxs-lookup"><span data-stu-id="51ed0-131">**(3)**</span></span>|<span data-ttu-id="51ed0-132">Power View と PowerPivot で使用される Excel サービス アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="51ed0-132">The Excel Service Application used by Power View and PowerPivot.</span></span>|  
|<span data-ttu-id="51ed0-133">**4/4**</span><span class="sxs-lookup"><span data-stu-id="51ed0-133">**(4)**</span></span>|<span data-ttu-id="51ed0-134">PowerPivot サービス アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="51ed0-134">PowerPivot service application.</span></span>|  
  
 <span data-ttu-id="51ed0-135">![SSRS SharePoint モードのシングル サーバー配置](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint モードのシングル サーバー配置")</span><span class="sxs-lookup"><span data-stu-id="51ed0-135">![SSRS SharePoint Mode Single Server Deployment](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint Mode Single Server Deployment")</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="51ed0-136"> より複雑な配置例については、「 [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-136">For more complex deployment examples, see [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>  
  
##  <a name="setup-accounts"></a><a name="bkmk_setupaccounts"></a> <span data-ttu-id="51ed0-137">セットアップ アカウント</span><span class="sxs-lookup"><span data-stu-id="51ed0-137">Setup accounts</span></span>  
 <span data-ttu-id="51ed0-138">このセクションでは、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の主な配置手順に使用するアカウントと権限について説明します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-138">This section describes the accounts and permissions used for the primary deployment steps of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>  
  
 <span data-ttu-id="51ed0-139">**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスのインストールと登録:**</span><span class="sxs-lookup"><span data-stu-id="51ed0-139">**Installation and registering the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service:**</span></span>  
  
-   <span data-ttu-id="51ed0-140">SharePoint モードでのインストール中の現在のアカウント (' セットアップ ' アカウントと呼ばれます) は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ローカルコンピューターの管理者権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-140">The current account during the installation (referred to as the 'setup' account) of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode needs to have administrative rights in the local computer.</span></span> <span data-ttu-id="51ed0-141">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint のインストール後にをインストールし、' セットアップ ' アカウントが sharepoint ファーム管理者グループのメンバーでもある場合は、インストールによって [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスが登録され [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-141">If you are installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] after SharePoint is installed and the 'setup' account is also a member of the SharePoint farm administrators group, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation will register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service for you.</span></span> <span data-ttu-id="51ed0-142">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint がインストールされる前にをインストールした場合、または ' セットアップ ' アカウントがファーム管理者グループのメンバーでない場合は、サービスを手動で登録します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-142">If you install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] before SharePoint is installed or the 'setup' account is not a member of the farm administrators group, you register the service manually.</span></span> <span data-ttu-id="51ed0-143">「 [手順 2。 Reporting Services SharePoint サービスの登録と開始](#bkmk_install_SSRS_sharedservice)。</span><span class="sxs-lookup"><span data-stu-id="51ed0-143">See the section [Step 2: Register and Start the Reporting Services SharePoint Service](#bkmk_install_SSRS_sharedservice).</span></span>  
  
 <span data-ttu-id="51ed0-144">**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成:**</span><span class="sxs-lookup"><span data-stu-id="51ed0-144">**Creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service Applications**</span></span>  
  
-   <span data-ttu-id="51ed0-145">インストールと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスの登録の後、1 つ以上の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-145">Following installation and registering the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service, create one or more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="51ed0-146">Reporting Services サービス アプリケーションを作成できるように、"SharePoint ファーム サービス アカウント" を一時的にローカルの Administrators グループのメンバーにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-146">The "SharePoint farm service account " needs to temporarily be a member of the local administrators group so the Reporting Services service application can be created.</span></span> <span data-ttu-id="51ed0-147">SharePoint 2013 アカウントのアクセス許可の詳細については、「 [sharepoint 2013 のアカウントのアクセス許可とセキュリティ設定](https://technet.microsoft.com/library/cc678863.aspx)」 (を参照してください https://technet.microsoft.com/library/cc678863.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="51ed0-147">For more information on SharePoint 2013 account permissions, see [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx) (https://technet.microsoft.com/library/cc678863.aspx).</span></span>  
  
     <span data-ttu-id="51ed0-148">セキュリティ上、SharePoint ファーム管理者アカウントがローカル オペレーティング システムの管理者アカウントを兼ねないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-148">It is security best practice that SharePoint farm administrator accounts are not also local operating system administrator accounts.</span></span> <span data-ttu-id="51ed0-149">インストール プロセスの一環としてファーム管理者アカウントをローカルの Administrators グループに追加する場合は、インストールの完了後にローカルの Administrators グループからそのアカウントを削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-149">If you add a farm admin account to the local administrators group as part of your installation process, it is recommended you remove the account from the local administrators group after installation is complete.</span></span>  
  
##  <a name="step-1-install-reporting-services-report-server-in-sharepoint-mode"></a><a name="bkmk_install_SSRS"></a><span data-ttu-id="51ed0-150">手順 1: Reporting Services レポートサーバーを SharePoint モードでインストールする</span><span class="sxs-lookup"><span data-stu-id="51ed0-150">Step 1: Install Reporting Services Report Server in SharePoint mode</span></span>  
 <span data-ttu-id="51ed0-151">この手順では、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーと SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-151">This step installs a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server in SharePoint mode and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span> <span data-ttu-id="51ed0-152">コンピューターに既にインストールされている内容によっては、次の手順で説明するインストール ページの一部は表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-152">Depending on what is already installed on your computer, you may not see some of the installation pages described in the following steps.</span></span>  
  
1.  <span data-ttu-id="51ed0-153">SQL Server インストール ウィザード (Setup.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-153">Run the SQL Server Installation Wizard (Setup.exe).</span></span>  
  
2.  <span data-ttu-id="51ed0-154">ウィザードの左側の **[インストール]** をクリックし、 **[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-154">Click **Installation** in the left side of the wizard and then click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
3.  <span data-ttu-id="51ed0-155">**[セットアップ サポート ルール]** ページで、すべてのルールに合格したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-155">Click **OK** on the **Setup Support Rules** page, assuming all rules passed.</span></span>  
  
4.  <span data-ttu-id="51ed0-156">**[セットアップ サポート ファイル]** ページで、 **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-156">Click **Install** on the **Setup Support Files** page.</span></span> <span data-ttu-id="51ed0-157">コンピューターに既にインストールされている内容によっては、次のメッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-157">Depending on what is already installed on your computer, you might see the following message:</span></span>  
  
    -   <span data-ttu-id="51ed0-158">"影響を受けた 1 つ以上のファイルで操作が保留されています。</span><span class="sxs-lookup"><span data-stu-id="51ed0-158">"One or more affected files have operations pending.</span></span> <span data-ttu-id="51ed0-159">セットアップ プロセスが完了した後で、コンピューターを再起動する必要があります。"</span><span class="sxs-lookup"><span data-stu-id="51ed0-159">You must restart your computer after the setup process is completed."</span></span>  
  
    -   <span data-ttu-id="51ed0-160">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-160">Click **Ok**.</span></span>  
  
5.  <span data-ttu-id="51ed0-161">サポート ファイルのインストールが完了し、 **[セットアップ サポート ルール]** ページに **[合格]** というステータスが表示されたら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-161">Click **Next** after the support files have completed installing and the **Support Rules** pages show a status of **Passed**.</span></span> <span data-ttu-id="51ed0-162">警告やインストールの障害となる問題を確認します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-162">Review any warnings or blocking issues.</span></span>  
  
6.  <span data-ttu-id="51ed0-163">**[インストールの種類]** ページで、 **[既存の SQL Server 2014 インスタンスに機能を追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-163">On the **Installation Type** page, click **Add features to an existing instance of SQL Server 2014**.</span></span> <span data-ttu-id="51ed0-164">ドロップダウン リストで適切なインスタンスを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-164">Select the correct instance in the drop-down list and click **Next**.</span></span>  
  
7.  <span data-ttu-id="51ed0-165">**[プロダクト キー]** ページが表示されたら、キーを入力するか、既定の "Enterprise Evaluation" を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-165">If you see the **Product Key** page, type your key or accept the default of the 'Enterprise Evaluation' edition.</span></span>  
  
     <span data-ttu-id="51ed0-166">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-166">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="51ed0-167">[ライセンス条項] ページが表示されたら、ライセンス条項を確認して同意します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-167">If you see the License terms page, review and accept the license terms.</span></span> <span data-ttu-id="51ed0-168">マイクロソフトでは、機能使用状況に関するデータを送信することに同意して、製品の機能やサポートの改善にご協力いただき感謝しております。</span><span class="sxs-lookup"><span data-stu-id="51ed0-168">Microsoft appreciates you clicking to agree to send feature usage data to help improve product features and support.</span></span>  
  
     <span data-ttu-id="51ed0-169">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-169">Click **Next**.</span></span>  
  
9. <span data-ttu-id="51ed0-170">**[セットアップ ロール]** ページが表示されたら、 **[SQL Server 機能のインストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-170">If you see the **Setup Role** page, select **SQL Server Feature Installation**</span></span>  
  
     <span data-ttu-id="51ed0-171">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-171">Click **Next**</span></span>  
  
     <span data-ttu-id="51ed0-172">![[セットアップ ロール] の [SQL Server 機能のインストール]](../../../2014/sql-server/install/media/rs-setuprole.gif "[セットアップ ロール] の [SQL Server 機能のインストール]")</span><span class="sxs-lookup"><span data-stu-id="51ed0-172">![SQL Server Feature Installation for setup role](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Feature Installation for setup role")</span></span>  
  
10. <span data-ttu-id="51ed0-173">**[機能の選択]** ページで、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-173">Select the following on the **Feature Selection** page:</span></span>  
  
    -   <span data-ttu-id="51ed0-174">**Reporting Services-SharePoint**</span><span class="sxs-lookup"><span data-stu-id="51ed0-174">**Reporting Services - SharePoint**</span></span>  
  
    -   <span data-ttu-id="51ed0-175">**SharePoint 製品用の Reporting Services アドイン**。</span><span class="sxs-lookup"><span data-stu-id="51ed0-175">**Reporting Services add-in for SharePoint Products**.</span></span>  
  
         <span data-ttu-id="51ed0-176">![メモ](../../../2014/reporting-services/media/rs-fyinote.png "注意")アドインをインストールするためのインストールウィザードオプションは、リリースで新しく追加されました [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="51ed0-176">![note](../../../2014/reporting-services/media/rs-fyinote.png "note") The installation wizard option for installing the add-in is new with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release.</span></span>  
  
    -   <span data-ttu-id="51ed0-177">SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスがまだインストールされていない場合は、 **[データベース エンジン サービス]** および **[管理ツール - 完全]** をクリックして完全な環境をインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-177">If you do not already have an instance of SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)], you could also select **Database Engine Services** and **Management Tools Complete** for a complete environment.</span></span>  
  
     <span data-ttu-id="51ed0-178">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-178">Click **Next**.</span></span>  
  
     <span data-ttu-id="51ed0-179">![SSRS の機能の選択 (SharePoint モード)](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS の機能の選択 (SharePoint モード)")</span><span class="sxs-lookup"><span data-stu-id="51ed0-179">![SSRS Feature Selection for SharePoint mode](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS Feature Selection for SharePoint mode")</span></span>  
  
11. <span data-ttu-id="51ed0-180">**[インストール ルール]** ページが表示されたら、</span><span class="sxs-lookup"><span data-stu-id="51ed0-180">If you see the **Installation Rules** page.</span></span> <span data-ttu-id="51ed0-181">警告やインストールの障害となる問題を確認します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-181">Review any warnings or blocking issues.</span></span> <span data-ttu-id="51ed0-182">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-182">Then click **Next**</span></span>  
  
12. <span data-ttu-id="51ed0-183">データベース エンジン サービスを選択した場合は、 **[インスタンスの構成]** ページで **MSSQLSERVER** の既定のインスタンスを受け入れて、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-183">If you selected the Database Engine services, accept the default instance of **MSSQLSERVER** on the **Instance Configuration** page and click **Next**.</span></span>  
  
     <span data-ttu-id="51ed0-184">![メモ](../../../2014/reporting-services/media/rs-fyinote.png "注意")Reporting Services SharePoint サービス アーキテクチャは、以前の Reporting Services アーキテクチャとは異なり、SQL Server "インスタンス" に基づいていません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-184">![note](../../../2014/reporting-services/media/rs-fyinote.png "note")The Reporting Services SharePoint service architecture is not based on a SQL Server "instance" as was the previous Reporting Services architecture.</span></span>  
  
13. <span data-ttu-id="51ed0-185">**[必要なディスク領域]** ページを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-185">Review the **Disk Space Requirements** page and click **Next**.</span></span>  
  
14. <span data-ttu-id="51ed0-186">**[サーバーの構成]** ページが表示されたら、適切な資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-186">If you see the **Server Configuration** page type appropriate credentials.</span></span> <span data-ttu-id="51ed0-187">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ警告機能またはサブスクリプション機能を使用する場合は、SQL Server エージェントの **[スタートアップの種類]** を **[自動]** に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-187">If you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerting or subscription features, you need to change the **Startup Type** for SQL Server Agent to **Automatic**.</span></span> <span data-ttu-id="51ed0-188">コンピューターに既にインストールされている内容によっては、 **[サーバーの構成]** ページは表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-188">You may not see the **Server Configuration** page, depending on what is already installed on the computer.</span></span>  
  
     <span data-ttu-id="51ed0-189">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-189">Click **Next**.</span></span>  
  
15. <span data-ttu-id="51ed0-190">データベース エンジン サービスを選択した場合は、 **[データベース エンジンの構成]** ページが表示されるので、SQL 管理者の一覧に適切なアカウントを追加して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-190">If you selected the Database Engine services, you will see the **Database Engine Configuration** page, add appropriate accounts to the list of SQL Administrators and click **Next**.</span></span>  
  
16. <span data-ttu-id="51ed0-191">**[Reporting Services の構成]** ページで、 **[インストールのみ]** オプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-191">On the **Reporting Services Configuration** page you should see the **Install only** option is selected.</span></span> <span data-ttu-id="51ed0-192">このオプションはレポート サーバー ファイルをインストールするもので、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]用の SharePoint 環境は構成されません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-192">This option installs the report server files, and does not configure the SharePoint environment for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51ed0-193">SQL Server のインストールが完了したら、このトピックの他のセクションに従って SharePoint 環境を構成します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-193">When the SQL Server installation is complete, follow the other sections of this topic to configure the SharePoint environment.</span></span> <span data-ttu-id="51ed0-194">これには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスのインストールと、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-194">This Includes installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service and creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>  
  
     <span data-ttu-id="51ed0-195">![SQL Server セットアップ ウィザード - SSRS 構成ページ](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server セットアップ ウィザード - SSRS 構成ページ")</span><span class="sxs-lookup"><span data-stu-id="51ed0-195">![SQL Server Setup Wizard - SSRS Configuration Page](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server Setup Wizard - SSRS Configuration Page")</span></span>  
  
17. <span data-ttu-id="51ed0-196">**[エラー レポート]** ページでエラー レポートを送信するためのチェック ボックスをオンにすると、マイクロソフトが SQL Server の機能とサービスを改善するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-196">Help Microsoft improve SQL Server features and services by clicking the check box to send error reports on the **Error Reporting** page.</span></span>  
  
     <span data-ttu-id="51ed0-197">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-197">Click **Next**.</span></span>  
  
18. <span data-ttu-id="51ed0-198">**[インストール構成ルール]** ページで警告を確認して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-198">Review any warnings and then click **Next** on the **Installation Configuration Rules** page.</span></span>  
  
19. <span data-ttu-id="51ed0-199">**[インストールの準備完了]** ページで、インストールの概要を確認して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-199">On the **Ready to Install** page, review the installation summary and then click **Next**.</span></span> <span data-ttu-id="51ed0-200">概要には、 **SharePointFilesOnlyMode** の値を示す **[Reporting Services SharePoint モード]** 子ノードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-200">The summary will include a **Reporting Services SharePoint Mode** child node that will show a value of **SharePointFilesOnlyMode**.</span></span> <span data-ttu-id="51ed0-201">**[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-201">Click **Install**.</span></span>  
  
20. <span data-ttu-id="51ed0-202">インストールには数分かかります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-202">The installation will take several minutes.</span></span> <span data-ttu-id="51ed0-203">機能の一覧と各機能の状態が表示された **[完了]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-203">You will see the **Complete** page with the features listed and the status of each feature.</span></span> <span data-ttu-id="51ed0-204">コンピューターの再起動が必要であることを示す情報ダイアログが表示される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-204">You may see an information dialog indicating the computer needs to be restarted.</span></span>  
  
##  <a name="step-2-register-and-start-the-reporting-services-sharepoint-service"></a><a name="bkmk_install_SSRS_sharedservice"></a><span data-ttu-id="51ed0-205">手順 2: Reporting Services SharePoint サービスを登録して開始する</span><span class="sxs-lookup"><span data-stu-id="51ed0-205">Step 2: Register and Start the Reporting Services SharePoint Service</span></span>  
 <span data-ttu-id="51ed0-206">![PowerShell 関連コンテンツ](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")</span><span class="sxs-lookup"><span data-stu-id="51ed0-206">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51ed0-207">既存の SharePoint ファームにインストールしている場合は、このセクションの手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-207">If you are installing into an existing SharePoint farm, you do not need to complete the steps in this section.</span></span> <span data-ttu-id="51ed0-208">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint サービスはインストールされており、このドキュメントの前のセクションの一部として SQL Server インストール ウィザードを実行したときに開始しています。</span><span class="sxs-lookup"><span data-stu-id="51ed0-208">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service is installed and started when you ran the SQL Server installation wizard as part of the previous section of this document.</span></span>  
  
 <span data-ttu-id="51ed0-209">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスを手動で登録する必要がある一般的な理由を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-209">The following are the common reasons why you need to manually register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="51ed0-210">SharePoint のインストール前に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードをインストールした。</span><span class="sxs-lookup"><span data-stu-id="51ed0-210">You installed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode before SharePoint was installed.</span></span>  
  
-   <span data-ttu-id="51ed0-211">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードのインストールに使用したアカウントが SharePoint ファーム管理者グループのメンバーではない。</span><span class="sxs-lookup"><span data-stu-id="51ed0-211">The account used to install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, was not a member of the SharePoint farm administrators group.</span></span> <span data-ttu-id="51ed0-212">詳細については、「 [Setup accounts](#bkmk_setupaccounts)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-212">For more information, see the section [Setup accounts](#bkmk_setupaccounts).</span></span>  
  
 <span data-ttu-id="51ed0-213">必要なファイルは SQL Server インストール ウィザードの中でインストールされていますが、サービスを SharePoint ファームに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-213">The necessary files were installed as part of the SQL Server installation wizard, but the services need to be registered into the SharePoint farm.</span></span> <span data-ttu-id="51ed0-214">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] リリースでは、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対する PowerShell が新たにサポートされました。</span><span class="sxs-lookup"><span data-stu-id="51ed0-214">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release introduces PowerShell support for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>  
  
 <span data-ttu-id="51ed0-215">以下では、SharePoint 管理シェルを開いてコマンドレットを実行する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-215">The following steps guide you through opening the SharePoint Management Shell and running cmdlets:</span></span>  
  
1.  <span data-ttu-id="51ed0-216">[**スタート**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-216">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="51ed0-217">**[Microsoft SharePoint 2013 製品]** グループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-217">Click the **Microsoft SharePoint 2013 Products** group.</span></span>  
  
3.  <span data-ttu-id="51ed0-218">**[SharePoint 2013 管理シェル]** を右クリックし、 **[管理者として実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-218">Right-click **SharePoint 2013 Management Shell** click **Run as administrator**.</span></span> <span data-ttu-id="51ed0-219">注: SharePoint コマンドは、標準的な Windows PowerShell ウィンドウでは認識されません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-219">NOTE: the SharePoint commands are not recognized in the standard Windows PowerShell window.</span></span> <span data-ttu-id="51ed0-220">**SharePoint 2013 管理シェル**を使用してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-220">Use the **SharePoint 2013 Management Shell**.</span></span>  
  
4.  <span data-ttu-id="51ed0-221">次の PowerShell コマンドを実行して、SharePoint サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-221">Run the following PowerShell command to install the SharePoint service.</span></span> <span data-ttu-id="51ed0-222">コマンドが正常に完了すると、管理シェルの表示が改行されます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-222">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="51ed0-223">コマンドが正常に完了しても、管理シェルに**メッセージは表示されません** 。</span><span class="sxs-lookup"><span data-stu-id="51ed0-223">**No message is returned** to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSService  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="51ed0-224">次のようなエラー メッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-224">If you see an error message similar to the following:</span></span>  
    >   
    >  <span data-ttu-id="51ed0-225">Install-sprsserviceinstall-sprsservice: 用語 ' Install-sprsserviceinstall-sprsservice ' は、次のように**認識されません**。</span><span class="sxs-lookup"><span data-stu-id="51ed0-225">Install-SPRSService : The term 'Install-SPRSService' **is not recognized** as the</span></span>  
    > <span data-ttu-id="51ed0-226">コマンドレット、関数、スクリプト ファイル、または操作可能なプログラムの名前として認識されません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-226">name of a cmdlet, function, script file, or operable program.</span></span> <span data-ttu-id="51ed0-227">データ移行ソリューションに関する推奨事項を入手するには、</span><span class="sxs-lookup"><span data-stu-id="51ed0-227">Check the</span></span>  
    > <span data-ttu-id="51ed0-228">パスが含まれている場合はそのパスが正しいことを確認してから、</span><span class="sxs-lookup"><span data-stu-id="51ed0-228">spelling of the name, or if a path was included, verify that the path is</span></span>  
    > <span data-ttu-id="51ed0-229">再試行してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-229">correct and try again.</span></span>  
  
5.  <span data-ttu-id="51ed0-230">次の PowerShell コマンドを実行して、サービス プロキシをインストールします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-230">Run the following PowerShell command to install the service proxy.</span></span> <span data-ttu-id="51ed0-231">コマンドが正常に完了すると、管理シェルの表示が改行されます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-231">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="51ed0-232">コマンドが正常に完了しても、管理シェルに**メッセージは表示されません** 。</span><span class="sxs-lookup"><span data-stu-id="51ed0-232">**No message is returned** to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  <span data-ttu-id="51ed0-233">次の PowerShell コマンドを実行してサービスを開始するか、または SharePoint サーバーの全体管理からサービスを開始する方法に関する後の注意事項を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-233">Run the following PowerShell command to start the service or see the following notes for instructions on how to start the service from SharePoint Central administration:</span></span>  
  
    ```powershell
    Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 <span data-ttu-id="51ed0-234">SharePoint 管理シェルではなく Windows Powershell が表示されているか、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードがインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-234">Either you are in the Windows Powershell instead of the SharePoint Management Shell  or [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode is not installed.</span></span> <span data-ttu-id="51ed0-235">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と PowerShell の詳細については、「 [Reporting Services SharePoint モード用の PowerShell コマンドレット](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-235">For more information on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and PowerShell, see [PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>  
  
 <span data-ttu-id="51ed0-236">3 番目の PowerShell コマンドを実行する代わりに、SharePoint サーバーの全体管理からサービスを開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-236">You can also start the service from SharePoint central Administration rather than running the third PowerShell command.</span></span> <span data-ttu-id="51ed0-237">次の手順を使用すると、サービスが実行していることを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-237">The following steps are also useful to verify that the service is running.</span></span>  
  
1.  <span data-ttu-id="51ed0-238">SharePoint サーバーの全体管理で、 **[システム設定]** の **[サーバーのサービスの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-238">In SharePoint Central Administration, click **Manage Services on Server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="51ed0-239">**[SQL Server Reporting Services サービス]** を探して、[アクション] 列の **[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-239">Find **SQL Server Reporting Services Service** and click **Start** in the Action column.</span></span>  
  
3.  <span data-ttu-id="51ed0-240">Reporting Services サービスのステータスが **[停止]** から **[開始]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-240">The status of the Reporting Services service will change from **Stopped** to **Started**.</span></span> <span data-ttu-id="51ed0-241">Reporting Services サービスが一覧にない場合は、PowerShell を使用してサービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-241">If the Reporting Services service is not in the list, use PowerShell to install the service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51ed0-242">Reporting Services サービスが [**開始**中] ステータスのままで、[**開始**] に変わらない場合は、Windows サーバーマネージャーで "SharePoint 2013 Administration" サービスが開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-242">If the Reporting Services service stays in the **Starting** status and does not change to **Started**, verify the 'SharePoint 2013 Administration' service is started in Windows Server Manager.</span></span>  
  
##  <a name="step-3-create-a-reporting-services-service-application"></a><a name="bkmk_create_serrviceapplication"></a> <span data-ttu-id="51ed0-243">手順 3. Reporting Services サービス アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="51ed0-243">Step 3: Create a Reporting Services Service Application</span></span>  
 <span data-ttu-id="51ed0-244">ここでは、既存のサービス アプリケーションを確認している場合に、サービス アプリケーションおよびプロパティの説明を作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-244">This section provides the steps to create a service application and a description of the properties, if you are reviewing an existing service application.</span></span>  
  
1.  <span data-ttu-id="51ed0-245">SharePoint サーバーの全体管理で、[**アプリケーション管理**] グループの [**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-245">In SharePoint Central Administration, in the **Application Management** group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="51ed0-246">SharePoint リボンで、 **[新規作成]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-246">In the SharePoint ribbon, click the **New** button.</span></span>  
  
3.  <span data-ttu-id="51ed0-247">[新規作成] メニューで、 **[SQL Server Reporting Services サービス アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-247">In the New menu, click **SQL Server Reporting Services Service Application.**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="51ed0-248">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] オプションが一覧に表示されない場合は、**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスがインストールされていない**ことを示しています。</span><span class="sxs-lookup"><span data-stu-id="51ed0-248">If the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] option does not appear in the list, it is an **indication that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service is not installed**.</span></span> <span data-ttu-id="51ed0-249">前のセクションの、PowerShell コマンドレットを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスをインストールする方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-249">Review the previous section on how to use PowerShell cmdlts to install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="51ed0-250">**[SQL Server Reporting Services サービス アプリケーションの作成]** ページで、アプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-250">In the **Create SQL Server Reporting Services Service Application** page, enter a name for the application.</span></span> <span data-ttu-id="51ed0-251">複数の Reporting Services サービス アプリケーションを作成する場合は、わかりやすい名前または名前付け規則を使用すると、管理および運用操作を体系化できます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-251">If you are creating multiple Reporting Services service applications, a descriptive name or naming convention will help you organize your administration and management operations.</span></span>  
  
5.  <span data-ttu-id="51ed0-252">**[アプリケーション プール]** セクションで、このアプリケーションのための新しいアプリケーション プールを作成します (推奨)。</span><span class="sxs-lookup"><span data-stu-id="51ed0-252">In **Application Pool** section, create a new application pool for the application (recommended).</span></span> <span data-ttu-id="51ed0-253">新しいアプリケーション プールの名前をサービス アプリケーションと同じにすると、日常の管理が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-253">If you use the same name for both the application pool and the services application, it can make ongoing administration easier.</span></span> <span data-ttu-id="51ed0-254">また、これは、作成するサービス アプリケーションの数や、シングル アプリケーション プールで複数使用する必要があるかどうかによっても影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-254">This can also be affected by how many service applications you will create and if you need to use several in a single application pool.</span></span> <span data-ttu-id="51ed0-255">アプリケーション プール管理の推奨事項とベスト プラクティスに関する SharePoint Server のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-255">See the SharePoint Server documentation on recommendations and best practices for application pool management.</span></span>  
  
     <span data-ttu-id="51ed0-256">そのアプリケーション プールのセキュリティ アカウントを選択または作成します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-256">Select or create a security account for the application pool.</span></span> <span data-ttu-id="51ed0-257">必ずドメイン ユーザー アカウントを指定してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-257">Be sure to specify a domain user account.</span></span> <span data-ttu-id="51ed0-258">ドメイン ユーザー アカウントにより、パスワードやアカウント情報をまとめて更新できる SharePoint の管理アカウント機能を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-258">A domain user account enables the use of the SharePoint managed account feature, which lets you update passwords and account information in one place.</span></span> <span data-ttu-id="51ed0-259">ドメイン アカウントは、配置をスケールアウトして、同じ ID で実行されるサービス インスタンスを追加する場合にも必要です。</span><span class="sxs-lookup"><span data-stu-id="51ed0-259">Domain accounts are also required if you plan to scale out the deployment to include additional service instances that run under the same identity.</span></span>  
  
6.  <span data-ttu-id="51ed0-260">**[データベース サーバー]** で、現在のサーバーを使用するか、または別の SQL Server を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-260">In the **Database Server**, you can use the current server or choose a different SQL Server.</span></span>  
  
7.  <span data-ttu-id="51ed0-261">**[データベース名]** の既定値は " `ReportingService_<guid>`" で、これは一意のデータベース名です。</span><span class="sxs-lookup"><span data-stu-id="51ed0-261">In **Database Name** the default value is `ReportingService_<guid>`, which is a unique database name.</span></span> <span data-ttu-id="51ed0-262">新しい値を入力する場合は、一意の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-262">If you type a new value, type a unique value.</span></span> <span data-ttu-id="51ed0-263">これは、サービス アプリケーションを明確な対象として作成される新しいデータベースです。</span><span class="sxs-lookup"><span data-stu-id="51ed0-263">This is the new database to be created specifically for the services application.</span></span>  
  
8.  <span data-ttu-id="51ed0-264">**[データベース認証]** の既定値は、"Windows 認証" です。</span><span class="sxs-lookup"><span data-stu-id="51ed0-264">In **Database Authentication**, the default is Windows Authentication.</span></span> <span data-ttu-id="51ed0-265">**[SQL 認証]** を選択する場合は、SharePoint のドキュメントを参照して、SharePoint 配置でその認証の種類を使用するためのベスト プラクティスを確認してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-265">If you choose **SQL Authentication**, refer to SharePoint documentation for best practices on how to use this authentication type in a SharePoint deployment.</span></span>  
  
9. <span data-ttu-id="51ed0-266">**[Web アプリケーションの関連付け]** セクションで、現在の Reporting Services サービス アプリケーションによるアクセス用に準備する Web アプリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-266">In the **Web Application Association** section, select the Web Application to be provisioned for access by the current Reporting Services Service Application.</span></span> <span data-ttu-id="51ed0-267">1 つの Reporting Services サービス アプリケーションを 1 つの Web アプリケーションに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-267">You can associate one Reporting Services service application to one web application.</span></span> <span data-ttu-id="51ed0-268">現在のすべての Web アプリケーションが既に Reporting Services サービス アプリケーションと関連付けられている場合は、警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-268">If all of the current web applications are already associated with a Reporting Services service application, you see a warning message.</span></span>  
  
10. <span data-ttu-id="51ed0-269">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-269">Click **OK**.</span></span>  
  
11. <span data-ttu-id="51ed0-270">サービス アプリケーションの作成処理には数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-270">The process to create a service application could take several minutes to complete.</span></span> <span data-ttu-id="51ed0-271">完了すると、確認メッセージと、 **[サブスクリプションと警告の準備]** ページへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-271">When it is complete, you will see a confirmation message and a link to a **Provision Subscriptions and Alerts** page.</span></span> <span data-ttu-id="51ed0-272">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサブスクリプション機能とデータ警告機能を使用する場合は、準備手順を行います。</span><span class="sxs-lookup"><span data-stu-id="51ed0-272">Complete the provision step if you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions feature or the data alerts feature.</span></span> <span data-ttu-id="51ed0-273">詳細については、「[SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-273">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).</span></span>  
  
 <span data-ttu-id="51ed0-274">![PowerShell 関連コンテンツ](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")PowerShell を使用してサービスアプリケーションを作成する方法の詳細については [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-274">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content") For information on using PowerShell to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, see:</span></span>  
  
-   <span data-ttu-id="51ed0-275">後の「[手順 1 ～ 4 に対応する Windows PowerShell スクリプト](#bkmk_full_script)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-275">See the following section [Windows PowerShell script for Steps 1-4](#bkmk_full_script).</span></span>  
  
-   <span data-ttu-id="51ed0-276">トピック「 [PowerShell を使用して Reporting Services サービス アプリケーションを作成するには](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp)」。</span><span class="sxs-lookup"><span data-stu-id="51ed0-276">Topic [To create a Reporting Services Service Application using PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).</span></span>  
  
##  <a name="step-4-activate-the-power-view-site-collection-feature"></a><a name="bkmk_powerview"></a><span data-ttu-id="51ed0-277">手順 4: Power View サイトコレクション機能をアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-277">Step 4: Activate the Power View Site Collection Feature.</span></span>  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]<span data-ttu-id="51ed0-278">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、SharePoint 製品用のアドインの機能で [!INCLUDE[msCoName](../../includes/msconame-md.md)] あり、サイトコレクション機能です。</span><span class="sxs-lookup"><span data-stu-id="51ed0-278">, a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint Products, is a site collection feature.</span></span> <span data-ttu-id="51ed0-279">この機能は、ルート サイト コレクションと、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインのインストール後に作成されたサイト コレクションで自動的にアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-279">The feature is activated automatically for root site collections and site collections created after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in is installed.</span></span> <span data-ttu-id="51ed0-280">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]を使用する場合は、この機能がアクティブ化されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-280">If you plan to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], verify that the feature is activated.</span></span>  
  
 <span data-ttu-id="51ed0-281">SharePoint Server のインストール後に SharePoint 製品用の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールした場合、レポート サーバーの統合機能と Power View の統合機能はルート サイト コレクションでのみアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-281">If you install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint Products after the installation of the SharePoint Server, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="51ed0-282">他のサイト コレクションについては、この機能を手動でアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-282">For other site collections, manually activate the features.</span></span>  
  
#### <a name="to-activate-or-verify-the-power-view-site-collection-feature"></a><span data-ttu-id="51ed0-283">Power View のサイト コレクション機能をアクティブ化または確認するには</span><span class="sxs-lookup"><span data-stu-id="51ed0-283">To Activate or Verify the Power View Site Collection Feature</span></span>  
  
1.  <span data-ttu-id="51ed0-284">次の手順は、SharePoint サイトが 2013 の **体験版**用に構成されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="51ed0-284">The following steps assume your SharePoint site is configured for the 2013 **experience version**.</span></span>  
  
     <span data-ttu-id="51ed0-285">ブラウザーで目的の SharePoint サイトを開きます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-285">Open your browser to the desired SharePoint site.</span></span> <span data-ttu-id="51ed0-286">例 http:// \<servername> /sites/bi</span><span class="sxs-lookup"><span data-stu-id="51ed0-286">For example http://\<servername>/sites/bi</span></span>  
  
2.  <span data-ttu-id="51ed0-287">[**設定**] [![SharePoint の設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-287">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings").</span></span>  
  
3.  <span data-ttu-id="51ed0-288">[**サイトの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-288">Click **Site settings**.</span></span>  
  
4.  <span data-ttu-id="51ed0-289">**[サイト コレクションの管理]** グループで **[サイト コレクションの機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-289">In the **Site Collection Administration** group Click **Site collection features**.</span></span>  
  
5.  <span data-ttu-id="51ed0-290">一覧で **[Power View 統合機能]** を探します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-290">Find **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="51ed0-291">**[アクティブ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-291">Click **Activate**.</span></span> <span data-ttu-id="51ed0-292">機能の状態が **[アクティブ]** に変化します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-292">The feature status will change to **Active**.</span></span>  
  
 <span data-ttu-id="51ed0-293">この手順は、サイト コレクションごとに実行します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-293">This procedure is completed per site collection.</span></span> <span data-ttu-id="51ed0-294">詳しくは、「 [SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-294">For more information, see [Activate the Report Server and Power View Integration Features in SharePoint](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md).</span></span>  
  
##  <a name="windows-powershell-script-for-steps-1-4"></a><a name="bkmk_full_script"></a><span data-ttu-id="51ed0-295">手順1-4 の Windows PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="51ed0-295">Windows PowerShell script for Steps 1-4</span></span>  
 <span data-ttu-id="51ed0-296">このセクション内の PowerShells スクリプトは、前のセクションで手順 1 ～ 4 を実行するときに使用したものと同じです。</span><span class="sxs-lookup"><span data-stu-id="51ed0-296">The PowerShells script in this section are the equivalent of completing steps 1 to 4 in the previous sections.</span></span> <span data-ttu-id="51ed0-297">このスクリプトは、次の作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-297">The script completes the following:</span></span>  
  
-   <span data-ttu-id="51ed0-298">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスおよびサービス プロキシをインストールし、そのサービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-298">Installs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service and service proxy, and starts the service.</span></span>  
  
-   <span data-ttu-id="51ed0-299">"Reporting Services" という名前のサービス プロキシを作成します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-299">Creates a service proxy named "Reporting Services".</span></span>  
  
-   <span data-ttu-id="51ed0-300">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]"Reporting Services アプリケーション" という名前のサービスアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-300">Creates a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application named "Reporting Services Application".</span></span>  
  
-   <span data-ttu-id="51ed0-301">サイト コレクションに対応する [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-301">Enables the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] feature for a site collection.</span></span>  
  
 <span data-ttu-id="51ed0-302">パラメーター</span><span class="sxs-lookup"><span data-stu-id="51ed0-302">Parameters</span></span>  
  
-   <span data-ttu-id="51ed0-303">サービス プロキシに合わせて **-Account** を更新します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-303">Update the **-Account** for the service proxy.</span></span> <span data-ttu-id="51ed0-304">このアカウントは、SharePoint ファーム内で管理されるサービス アカウントであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="51ed0-304">The account needs to be a managed service account in the SharePoint farm.</span></span> <span data-ttu-id="51ed0-305">詳細については、SharePoint のトピック「 [SharePoint 2013 の管理アカウントとサービス アカウントを計画する](https://technet.microsoft.com/library/cc263445.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-305">For more information, see the SharePoint topic [Plan for administrative and service accounts in SharePoint 2013](https://technet.microsoft.com/library/cc263445.aspx).</span></span>  
  
-   <span data-ttu-id="51ed0-306">サービスアプリケーションの **-databaseserver**パラメーターを更新します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-306">Update the **-DatabaseServer** parameter for the service application.</span></span> <span data-ttu-id="51ed0-307">このパラメーターは、データベース エンジンのインスタンスを意味します</span><span class="sxs-lookup"><span data-stu-id="51ed0-307">This parameter is the database engine instance</span></span>  
  
-   <span data-ttu-id="51ed0-308">機能を有効にするサイトの **-url**パラメーターを更新 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-308">Update the **-url** parameter of the site that you want the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] feature enabled.</span></span>  
  
 <span data-ttu-id="51ed0-309">**このスクリプトを使用するには、次の手順に従います。**</span><span class="sxs-lookup"><span data-stu-id="51ed0-309">**To use the script:**</span></span>  
  
1.  <span data-ttu-id="51ed0-310">管理者特権で Windows PowerShell を開きます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-310">Open Windows PowerShell with administrative privileges.</span></span>  
  
2.  <span data-ttu-id="51ed0-311">次のコードをスクリプト ウィンドウにコピーします。</span><span class="sxs-lookup"><span data-stu-id="51ed0-311">Copy the following code into the script window.</span></span>  
  
3.  <span data-ttu-id="51ed0-312">前のセクションで説明した 3 つのパラメーターを更新し、スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-312">Update the three parameters described in the previous section, and then run the script.</span></span>  
  
```powershell
#This script Configures SQL Server Reporting Services SharePoint mode  
  
$starttime = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
  
Write-Host -ForegroundColor Green "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
  
Write-Host -ForegroundColor Green "Install SSRS Service and Service Proxy, and start the service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
    Write-Host -ForegroundColor Green "Install the Reporting Services Shared Service"  
    Install-SPRSService  
  
    Write-Host -ForegroundColor Green " Install the Reporting Services Service Proxy"  
    Install-SPRSServiceProxy  
  
    # Get the ID of the RS Service Instance and start the service   
    Write-Host -ForegroundColor Green "Start the Reporting Services Service"  
    $RS = Get-SPServiceInstance | Where {$_.TypeName -eq "SQL Server Reporting Services Service"}  
    Start-SPServiceInstance -Identity $RS.Id.ToString()  
  
    # Wait for the Reporting Services Service to start...  
    $Status = Get-SPServiceInstance $RS.Id.ToString()  
    While ($Status.Status -ne "Online")  
    {  
        Write-Host -ForegroundColor Green "SSRS Service Not Online...Current Status = " $Status.Status  
        Start-Sleep -Seconds 2  
        $Status = Get-SPServiceInstance $RS.Id.ToString()  
    }  
  
$time = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Create a new application pool and Reporting Services service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Write-Host -ForegroundColor Green "Create a new application pool"  
#!!!! update "-Account" with an existing Managed Service Account  
New-SPServiceApplicationPool -Name "Reporting Services" -Account "<domain>\User name>"  
$appPool = Get-SPServiceApplicationPool "Reporting Services"  
  
Write-Host -ForegroundColor Green " Create the Reporting Services Service Application"  
#!!!! Update "-DatabaseServer", an instance of the SQL Server database engine   
$rsService = New-SPRSServiceApplication -Name "Reporting Services Application" -ApplicationPool $appPool -DatabaseName "Reporting_Services_Application" -DatabaseServer "<server name>"  
  
Write-Host -ForegroundColor Green "Create the Reporting Services Service Application Proxy"  
$rsServiceProxy = New-SPRSServiceApplicationProxy -Name "Reporting Services Application Proxy" -ServiceApplication $rsService  
  
Write-Host -ForegroundColor Green "Associate service application proxy to default web site and grant web applications rights to SSRS application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"     
# Associate the Reporting Services Service Applicatoin Proxy to the default web site...  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $rsServiceProxy  
  
$time=Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Enable the PowerView and reportserver site features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#!!!! update "-url"  of the site where you want the features enabled  
Enable-SPfeature -identity "powerview" -Url http://server/sites/bi  
Enable-SPfeature -identity "reportserver" -Url http://server/sites/bi  
  
####To Verify, you can run the following:  
#Get-SPRSServiceApplication  
#Get-SPServiceApplicationPool | where {$_.name -like "reporting*"}  
#Get-SPRSServiceApplicationProxy
```  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional_config"></a><span data-ttu-id="51ed0-313">追加の構成</span><span class="sxs-lookup"><span data-stu-id="51ed0-313">Additional Configuration</span></span>  
 <span data-ttu-id="51ed0-314">このセクションでは、SharePoint のほとんどの配置で重要になる追加の構成手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-314">This section describes additional configuration steps that are important in most SharePoint deployments.</span></span>  
  
###  <a name="configure-excel-services-and-powerpivot"></a><a name="bkmk_configure_ECS"></a><span data-ttu-id="51ed0-315">Excel Services と PowerPivot の構成</span><span class="sxs-lookup"><span data-stu-id="51ed0-315">Configure Excel Services and PowerPivot</span></span>  
 <span data-ttu-id="51ed0-316">SharePoint で Excel 2013 ブックの [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View レポートを表示する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーを SharePoint モードで使用するように、ファームの Excel Services アプリケーションを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-316">If you want to view [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View reports in an Excel 2013 workbook in SharePoint, an Excel Services Application on the farm needs to be configured to use an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Server in SharePoint mode.</span></span> <span data-ttu-id="51ed0-317">また、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションによって使用されるアプリケーション プールのセキュリティ アカウントは、Analysis Services サーバーの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-317">Also, the application pool security account used by the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, must be an administrator on the Analysis Services Server.</span></span> <span data-ttu-id="51ed0-318">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="51ed0-318">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="51ed0-319">[PowerPivot for SharePoint 2013 インストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)の「Analysis Services 統合用に Excel Services を構成する」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-319">The section "Configure Excel Services for Analysis Services integration" in [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
-   <span data-ttu-id="51ed0-320">[Excel Services のデータ モデルの設定を管理する (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx)。</span><span class="sxs-lookup"><span data-stu-id="51ed0-320">[Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).</span></span>  
  
###  <a name="provision-subscriptions-and-alerts"></a><a name="bkmk_provision_agent"></a><span data-ttu-id="51ed0-321">サブスクリプションとアラートを準備する</span><span class="sxs-lookup"><span data-stu-id="51ed0-321">Provision Subscriptions and Alerts</span></span>  
 <span data-ttu-id="51ed0-322">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサブスクリプションとデータ警告の機能を利用するには、SQL Server エージェントの権限の構成が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-322">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription and data alert features may require the configuration of SQL Server Agent permissions.</span></span> <span data-ttu-id="51ed0-323">SQL Server エージェントが実行中であるにもかかわらず、SQL Server エージェントが必要であることを示すエラー メッセージが表示された場合は、権限を更新します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-323">If you see an error message that indicates SQL Server Agent is required and you have verified SQL Server Agent is running, update the permissions.</span></span> <span data-ttu-id="51ed0-324">サービス アプリケーション作成成功ページの **[サブスクリプションと警告の準備]** リンクをクリックして、SQL Server エージェントを準備するための別のページに移動します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-324">You can click the link **Provision Subscriptions and Alerts** on the create service application success page to go to another page for provisioning SQL Server Agent.</span></span> <span data-ttu-id="51ed0-325">配置がコンピューターの境界をまたいでいる場合は (たとえば、SQL Server データベース インスタンスが異なるコンピューターにある場合)、準備手順を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-325">The provision step is needed if your deployment crosses machine boundaries, for example when the SQL Server database instance is on a different machine.</span></span> <span data-ttu-id="51ed0-326">詳細については、「 [SSRS サービスアプリケーションのサブスクリプションと警告の準備](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-326">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span></span>  
  
### <a name="configure-e-mail-for-ssrs-service-applications"></a><span data-ttu-id="51ed0-327">SSRS サービス アプリケーション用電子メールを構成する</span><span class="sxs-lookup"><span data-stu-id="51ed0-327">Configure E-mail for SSRS Service Applications</span></span>  
 <span data-ttu-id="51ed0-328">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ警告機能は、電子メール メッセージで警告を送信します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-328">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerts feature sends alerts in e-mail messages.</span></span> <span data-ttu-id="51ed0-329">電子メールを送信するには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを構成して、このサービス アプリケーションの電子メール配信拡張機能を変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-329">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="51ed0-330">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプション機能の電子メール配信拡張機能を使用する場合は、電子メールの設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="51ed0-330">If you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature, the e-mail settings are required.</span></span> <span data-ttu-id="51ed0-331">詳細については、「[Reporting Services サービス アプリケーションの電子メールの構成 &#40;SharePoint 2010 および SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-331">For more information, see [Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)</span></span>  
  
### <a name="add-reporting-services-content-types-to-content-libraries"></a><span data-ttu-id="51ed0-332">コンテンツ ライブラリに Reporting Services のコンテンツの種類を追加する</span><span class="sxs-lookup"><span data-stu-id="51ed0-332">Add Reporting Services Content Types to Content Libraries</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="51ed0-333">では、共有データ ソース (.rsds) ファイル、レポート モデル (.smdl)、レポート ビルダーのレポート定義 (.rdl) ファイルを管理する際に使用されるコンテンツの種類が、あらかじめ定義されています。</span><span class="sxs-lookup"><span data-stu-id="51ed0-333">provides predefined content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="51ed0-334">コンテンツの種類として、 **[レポート ビルダー レポート]**、 **[レポート モデル]**、および **[レポート データ ソース]** をライブラリに追加すると、 **[新規作成]** コマンドが有効になり、その種類のドキュメントを新規作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="51ed0-334">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span> <span data-ttu-id="51ed0-335">詳細については、「 [SharePoint 統合モードでのレポートサーバーコンテンツタイプのライブラリへの追加 &#40;Reporting Services」&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-335">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
### <a name="activate-the-report-server-file-sync-feature"></a><span data-ttu-id="51ed0-336">レポート サーバー ファイル同期機能をアクティブにする</span><span class="sxs-lookup"><span data-stu-id="51ed0-336">Activate the Report Server File sync Feature</span></span>  
 <span data-ttu-id="51ed0-337">ユーザーがパブリッシュされたレポート アイテムを SharePoint ドキュメント ライブラリに頻繁に直接アップロードする場合は、サイト レベルの **レポート サーバー ファイル同期** 機能が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-337">If users will frequently upload published report items directly to SharePoint document libraries, the **Report Server File Sync** site level feature will be beneficial.</span></span> <span data-ttu-id="51ed0-338">ファイル同期機能では、レポート サーバー カタログとドキュメント ライブラリのアイテムの同期が、より頻繁に行われます。</span><span class="sxs-lookup"><span data-stu-id="51ed0-338">The file sync feature will synchronize the report server catalog with items in document libraries on a more frequent basis.</span></span> <span data-ttu-id="51ed0-339">詳細については、「SharePoint サーバーの[全体管理でレポートサーバー File Sync 機能をアクティブにする](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-339">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).</span></span>  
  
##  <a name="verify-the-installation"></a><a name="bkmk_verify_installation"></a><span data-ttu-id="51ed0-340">インストールを確認する</span><span class="sxs-lookup"><span data-stu-id="51ed0-340">Verify the installation</span></span>  
 <span data-ttu-id="51ed0-341">次に、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の SharePoint モードの配置を確認するための推奨手順と手続きについて説明します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-341">The following are suggested steps and procedures to verify the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode deployment.</span></span>  
  
-   <span data-ttu-id="51ed0-342">検証トピック「 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)」の「SharePoint」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-342">See the SharePoint section in the verification topic [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).</span></span>  
  
-   <span data-ttu-id="51ed0-343">SharePoint ドキュメント ライブラリ内で、タイトルなどに使用するテキスト ボックスのみを含む基本的な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-343">In a SharePoint document library, create a basic [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that only contains a text box, for example a title.</span></span> <span data-ttu-id="51ed0-344">このレポートには、データ ソースやデータセットは何も含めません。</span><span class="sxs-lookup"><span data-stu-id="51ed0-344">The report does not contain any data sources or datasets.</span></span> <span data-ttu-id="51ed0-345">目標は、レポート ビルダーを開き、基本的なレポートを作成し、そのレポートをプレビューできることの確認です。</span><span class="sxs-lookup"><span data-stu-id="51ed0-345">The goal is to verify you can open Report Builder, build a basic report, and preview the report.</span></span>  
  
     <span data-ttu-id="51ed0-346">レポートをドキュメント ライブラリに保存し、ライブラリからレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="51ed0-346">Save the report to the document library and the run the report from the library.</span></span> <span data-ttu-id="51ed0-347">レポート ビルダーでレポートを作成する方法の詳細については、「 [レポート ビルダーの起動 (レポート ビルダー)](https://technet.microsoft.com/library/ms159221.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51ed0-347">For more information on creating reports with Report Builder, see [Start Report Builder (Report Builder)](https://technet.microsoft.com/library/ms159221.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ed0-348">参照</span><span class="sxs-lookup"><span data-stu-id="51ed0-348">See Also</span></span>  
 <span data-ttu-id="51ed0-349">[Reporting Services SharePoint モード用の PowerShell コマンドレット](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="51ed0-349">[PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="51ed0-350">[Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="51ed0-350">[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span></span>  
 <span data-ttu-id="51ed0-351">[コンテンツロードマップ: SharePoint Server と SQL Server BI のセットアップと構成](https://technet.microsoft.com/library/dn205112.aspx) </span><span class="sxs-lookup"><span data-stu-id="51ed0-351">[Content Roadmap: Set up and configure SharePoint Server and SQL Server BI](https://technet.microsoft.com/library/dn205112.aspx) </span></span>  
 <span data-ttu-id="51ed0-352">[SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="51ed0-352">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 [<span data-ttu-id="51ed0-353">Reporting Services の SharePoint サービスとサービス アプリケーション</span><span class="sxs-lookup"><span data-stu-id="51ed0-353">Reporting Services SharePoint Service and Service Applications</span></span>](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)
