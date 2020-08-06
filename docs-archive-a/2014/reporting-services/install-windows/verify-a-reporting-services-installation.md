---
title: Reporting Services のインストール状態の検証 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- checking report server installations
- verifying report server installations
- Report Designer [Reporting Services], verifying installations
- installing Reporting Services, verifying installations
- Report Manager [Reporting Services], verifying installations
- report servers [Reporting Services], verifying installations
- Setup [Reporting Services], verifying installations
ms.assetid: 82a51a99-66f0-4b0c-b05b-07d22387adb0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b90f997f99cfc9d3f8625eb4e08d193af52d7f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631642"
---
# <a name="verify-a-reporting-services-installation"></a><span data-ttu-id="5c1a8-102">Verify a Reporting Services Installation</span><span class="sxs-lookup"><span data-stu-id="5c1a8-102">Verify a Reporting Services Installation</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5c1a8-103">レポート サーバーは、ネイティブまたは SharePoint の 2 つのモードのうちのいずれかのモードでインストールできます。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-103">report servers can be installed in one of two modes, Native or SharePoint.</span></span> <span data-ttu-id="5c1a8-104">インストールの確認に必要な手順は、レポート サーバーのモードによって変わります。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-104">The steps you should follow for verifying the installation depend on the report server mode.</span></span>  
  
 <span data-ttu-id="5c1a8-105">このトピックの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-105">This topic contains the following information:</span></span>  
  
-   [<span data-ttu-id="5c1a8-106">SharePoint モードのインストールの確認</span><span class="sxs-lookup"><span data-stu-id="5c1a8-106">Verify SharePoint Mode Installation</span></span>](#bkmk_sharepointmode)  
  
-   [<span data-ttu-id="5c1a8-107">ネイティブ モードのインストールの確認</span><span class="sxs-lookup"><span data-stu-id="5c1a8-107">Verify a Native Mode Installation</span></span>](#bkmk_nativemode)  
  
##  <a name="verify-sharepoint-mode-installation"></a><a name="bkmk_sharepointmode"></a> <span data-ttu-id="5c1a8-108">SharePoint モードのインストールの確認</span><span class="sxs-lookup"><span data-stu-id="5c1a8-108">Verify SharePoint Mode Installation</span></span>  
  
#### <a name="to-verify-the-reporting-services-service"></a><span data-ttu-id="5c1a8-109">Reporting Services サービスを確認するには</span><span class="sxs-lookup"><span data-stu-id="5c1a8-109">To verify the Reporting Services Service</span></span>  
  
1.  <span data-ttu-id="5c1a8-110">SharePoint サーバーの全体管理で、 **[システム設定]** の **[サーバーのサービスの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-110">From SharePoint central administration, click **Manage services on server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="5c1a8-111">**SQL Server Reporting Services サービス** がインストールされ、 **実行中** の状態であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-111">Verify the **SQL Server Reporting Services Service** is installed and in the **Running** state.</span></span>  
  
     <span data-ttu-id="5c1a8-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスが一覧に表示されない場合は、サービスがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-112">If you do not see the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service in the list, verify the service is installed.</span></span> <span data-ttu-id="5c1a8-113">詳細については、「sharepoint [2010 用 Reporting Services Sharepoint モードのインストール](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」の「Reporting Services sharepoint サービスのインストールと開始」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-113">For more information, see the "Install and start the Reporting Services SharePoint Service" section of [Install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>  
  
#### <a name="to-verify-the-service-application"></a><span data-ttu-id="5c1a8-114">サービス アプリケーションを確認するには</span><span class="sxs-lookup"><span data-stu-id="5c1a8-114">To verify the Service Application</span></span>  
  
1.  <span data-ttu-id="5c1a8-115">サーバーの全体管理から確認するには、少なくとも 1 つの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを使用します。 **[アプリケーション構成の管理]** で **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-115">To verify from Central Administration you have at least one [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="5c1a8-116">種類が **[SQL Server Reporting Services サービス アプリケーション]** のサービス アプリケーションと、対応するアプリケーション プロキシがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-116">Verify there is a service application of type **SQL Server Reporting Services Service Application** and a corresponding application proxy.</span></span>  
  
3.  <span data-ttu-id="5c1a8-117">サービス アプリケーションの名前の **近く** をクリックし、SharePoint ツール バーの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-117">Click **near** the name of the service application and then click **Properties** in the SharePoint toolbar.</span></span>  <span data-ttu-id="5c1a8-118">サービス アプリケーションの名前をクリックすると、プロパティ ページではなく、サービス アプリケーションの管理ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-118">If you click the name of the service application it will open the Management pages of the service application, not the properties page.</span></span>  
  
4.  <span data-ttu-id="5c1a8-119">必要な Web アプリケーションを指すように **[Web アプリケーションの関連付け]** が構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-119">Verify the **Web Application Association** is configured to point to the desired web application.</span></span>  
  
#### <a name="to-verify-the-site-collection-feature"></a><span data-ttu-id="5c1a8-120">サイト コレクション機能を確認するには</span><span class="sxs-lookup"><span data-stu-id="5c1a8-120">To verify the Site collection Feature</span></span>  
  
1.  <span data-ttu-id="5c1a8-121">サイトの設定の **[サイト コレクションの管理]** で **[サイト コレクションの機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-121">In site settings, click **Site collection Features** in the **Site Collection Administration** group.</span></span>  
  
2.  <span data-ttu-id="5c1a8-122">**[レポート サーバーの統合機能]** がアクティブであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-122">Verify the **Report Server Integration Feature** is active.</span></span>  
  
#### <a name="to-verify-reporting-server-content-types"></a><span data-ttu-id="5c1a8-123">レポート サーバー コンテンツの種類を確認するには</span><span class="sxs-lookup"><span data-stu-id="5c1a8-123">To Verify Reporting Server content types</span></span>  
  
1.  <span data-ttu-id="5c1a8-124">レポートサーバーのコンテンツの種類を確認または追加するには [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、「 [SharePoint 統合モードでのレポートサーバーコンテンツタイプのライブラリへの追加 &#40;Reporting Services」&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-124">To verify or add [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server content types, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
#### <a name="to-verify-you-can-launch-report-builder"></a><span data-ttu-id="5c1a8-125">レポート ビルダーが起動できることを確認するには</span><span class="sxs-lookup"><span data-stu-id="5c1a8-125">To verify you can launch Report Builder</span></span>  
  
1.  <span data-ttu-id="5c1a8-126">ドキュメント ライブラリから、SharePoint リボンの **[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-126">From a document library, click **Documents** in the SharePoint ribbon.</span></span>  
  
2.  <span data-ttu-id="5c1a8-127">**[新しいドキュメント]** をクリックし、 **[レポート ビルダー レポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-127">Click **New Document** and click **Report Builder Report**.</span></span> <span data-ttu-id="5c1a8-128">このオプションが表示されない場合は、レポート サーバー コンテンツの種類をライブラリに追加するための前の手順を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-128">If you do not see this option, review the previous procedure on adding the report server content types to a library.</span></span>  
  
#### <a name="create-a-basic-report"></a><span data-ttu-id="5c1a8-129">基本的なレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="5c1a8-129">Create a basic report</span></span>  
  
1.  <span data-ttu-id="5c1a8-130">SharePoint ドキュメント ライブラリ内で、タイトルなどに使用するテキスト ボックスのみを含む基本的な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-130">In a SharePoint document library, create a basic [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that only contains a text box, for example a title.</span></span> <span data-ttu-id="5c1a8-131">このレポートには、データ ソースやデータセットは何も含めません。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-131">The report does not contain any data sources or datasets.</span></span> <span data-ttu-id="5c1a8-132">目標は、レポート ビルダーを開いて基本的なレポートをプレビューできることの確認です。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-132">The goal is to verify you can open Report Builder and a basic report will preview.</span></span>  
  
2.  <span data-ttu-id="5c1a8-133">レポートをドキュメント ライブラリに保存し、ライブラリからレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-133">Save the report to the document library and the run the report from the library.</span></span> <span data-ttu-id="5c1a8-134">レポート ビルダーでレポートを作成する方法の詳細については、「 [レポート ビルダーの起動 (レポート ビルダー)](https://technet.microsoft.com/library/ms159221.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-134">For more information on creating reports with Report Builder, see [Start Report Builder (Report Builder)](https://technet.microsoft.com/library/ms159221.aspx).</span></span>  
  
#### <a name="reporting-services-samples"></a><span data-ttu-id="5c1a8-135">Reporting Services のサンプル</span><span class="sxs-lookup"><span data-stu-id="5c1a8-135">Reporting Services samples</span></span>  
  
1.  <span data-ttu-id="5c1a8-136">Reporting Services のチュートリアルのいずれかを完了します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-136">Complete one of the Reporting Services tutorials.</span></span> <span data-ttu-id="5c1a8-137">詳細については、「[Reporting Services のチュートリアル (SSRS)](../reporting-services-tutorials-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-137">For more information, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="5c1a8-138">CodePlex から AdventureWorks の作業のサンプル データベースと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サンプル レポートをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-138">Download the Adventure works sample database and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sample reports from CodePlex.</span></span> <span data-ttu-id="5c1a8-139">詳細については、「 [AdventureWorks レポート サンプル](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-139">For more information, see [AdventureWorks Report Samples](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home).</span></span>  
  
##  <a name="verify-a-native-mode-installation"></a><a name="bkmk_nativemode"></a><span data-ttu-id="5c1a8-140">ネイティブモードのインストールの確認</span><span class="sxs-lookup"><span data-stu-id="5c1a8-140">Verify a Native Mode Installation</span></span>  
 <span data-ttu-id="5c1a8-141">既定の構成を使用してネイティブ モードでレポート サーバーをインストールする場合、セットアップでサーバーをインストールし、配置します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-141">When you install a Native mode report server using the default configuration, Setup installs and deploys the server.</span></span> <span data-ttu-id="5c1a8-142">いくつかの簡単なテストを行うことで、レポート サーバーが正常に配置されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-142">You can verify whether Setup deployed the report server by performing a few simple tests.</span></span> <span data-ttu-id="5c1a8-143">これらの手順を実行するには、ローカル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-143">You must be a local administrator to perform these steps.</span></span> <span data-ttu-id="5c1a8-144">他のユーザーがテストを実行する場合は、そのユーザーがレポート サーバーにアクセスできるように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-144">To enable other users to perform testing, you must configure report server access for those users.</span></span>  
  
#### <a name="to-verify-that-the-report-server-is-installed-and-running"></a><span data-ttu-id="5c1a8-145">レポート サーバーが正常にインストールされ、実行されていることを確認するには</span><span class="sxs-lookup"><span data-stu-id="5c1a8-145">To verify that the report server is installed and running</span></span>  
  
1.  <span data-ttu-id="5c1a8-146">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを実行し、インストールしたレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-146">Run the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you just installed.</span></span> <span data-ttu-id="5c1a8-147">[Web サービス URL] ページには、レポート サーバー Web サービスへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-147">The Web Service URL page includes a link to the Report Server Web service.</span></span> <span data-ttu-id="5c1a8-148">このリンクをクリックして、サーバーにアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-148">Click the link to verify you can access the server.</span></span> <span data-ttu-id="5c1a8-149">レポート サーバー データベースが構成されていない場合は、リンクをクリックする前にレポート サーバー データベースを構成してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-149">If the report server database is not configured, do that first before clicking the link.</span></span>  
  
2.  <span data-ttu-id="5c1a8-150">Services コンソール アプリケーションを開き、レポート サーバー サービスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-150">Open the Services console applications and verify that the Report Server service is running.</span></span> <span data-ttu-id="5c1a8-151">レポート サーバー サービスの状態を表示するには、 **[スタート]** ボタンをクリックし、 **[コントロール パネル]** をポイントして、 **[管理ツール]** をダブルクリックします。次に、 **[サービス]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-151">To view the status of the Report Server service, click **Start**, point to **Control Panel**, double-click **Administrative Tools**, and then double-click **Services**.</span></span> <span data-ttu-id="5c1a8-152">サービスの一覧が表示されたら、 **[Report Server (MSSQLSERVER)]** までスクロールします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-152">When the list of services appears, scroll to **Report Server (MSSQLSERVER)**.</span></span> <span data-ttu-id="5c1a8-153">状態が **[開始]** になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-153">The status should be **Started**.</span></span>  
  
3.  <span data-ttu-id="5c1a8-154">ブラウザーを開き、アドレス バーにレポート サーバーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-154">Open a browser and type the report server URL in the address bar.</span></span> <span data-ttu-id="5c1a8-155">アドレスは、セットアップ時にレポート サーバーに指定したサーバー名と仮想ディレクトリ名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-155">The address consists of the server name and the virtual directory name that you specified for the report server during setup.</span></span> <span data-ttu-id="5c1a8-156">既定では、レポート サーバーの仮想ディレクトリ名は **ReportServer**です。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-156">By default, the report server virtual directory is named **ReportServer**.</span></span> <span data-ttu-id="5c1a8-157">次の URL を使用して、レポートサーバーのインストールを確認できます: http:// *\<computer name>* /ReportServer *\<_instance name>* 。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-157">You can use the following URL to verify report server installation: http://*\<computer name>*/ReportServer*\<_instance name>*.</span></span> <span data-ttu-id="5c1a8-158">レポート サーバーを名前付きインスタンスとしてインストールした場合、URL は異なります。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-158">The URL will be different if you installed the report server as a named instance.</span></span> <span data-ttu-id="5c1a8-159">URL 形式の詳細については、「[レポート サーバー URL の構成 (SSRS 構成マネージャー)](configure-report-server-urls-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-159">For more information about the URL format, see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md).</span></span> <span data-ttu-id="5c1a8-160">Windows Vista または Windows Server 2008 上のローカル管理者である場合は、「[ローカル管理用のネイティブ モードのレポート サーバー (SSRS) の構成](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-160">If you are a local administrator on Windows Vista or Windows Server 2008, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="5c1a8-161">レポートを実行して、レポート サーバーの動作をテストします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-161">Run reports to test report server operations.</span></span> <span data-ttu-id="5c1a8-162">この手順では、チュートリアルからサンプル レポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-162">For this step, you can create a sample report from a tutorial.</span></span> <span data-ttu-id="5c1a8-163">詳細については、「[基本的なテーブル レポートの作成 (SSRS チュートリアル)](../create-a-basic-table-report-ssrs-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-163">For more information, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md).</span></span>  
  
#### <a name="to-verify-that-report-manager-is-installed-and-running"></a><span data-ttu-id="5c1a8-164">レポート マネージャーが正常にインストールされ、実行されていることを確認するには</span><span class="sxs-lookup"><span data-stu-id="5c1a8-164">To verify that Report Manager is installed and running</span></span>  
  
1.  <span data-ttu-id="5c1a8-165">ブラウザーを開き、アドレス バーにレポート マネージャーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-165">Open a browser and type the Report Manager URL in the address bar.</span></span> <span data-ttu-id="5c1a8-166">このアドレスは、セットアップ時または Reporting Services 構成ツールの [レポート マネージャー URL] ページでレポート マネージャーに対して指定したサーバー名と仮想ディレクトリ名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-166">The address consists of the server name and the virtual directory name that you specified for the Report Manager during setup or in the Report Manager URL page in the Reporting Services Configuration tool.</span></span> <span data-ttu-id="5c1a8-167">既定では、レポート マネージャーの仮想ディレクトリは **Reports**です。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-167">By default, the Report Manager virtual directory is **Reports**.</span></span> <span data-ttu-id="5c1a8-168">次の URL を使用して、レポート マネージャーのインストール状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-168">You can use the following URL to verify Report Manager installation:</span></span>  
  
     <span data-ttu-id="5c1a8-169">http:// *\<computer name>* /Reports *\<_instance name>* 。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-169">http://*\<computer name>*/Reports*\<_instance name>*.</span></span>  
  
2.  <span data-ttu-id="5c1a8-170">レポート サーバー データベースに定義が戻されるかどうかをテストするため、レポート マネージャーを使用して新しいフォルダーを作成するか、ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-170">Use Report Manager to create a new folder or upload a file to test whether definitions are passed back to the report server database.</span></span> <span data-ttu-id="5c1a8-171">操作が成功した場合、接続は正しく機能しています。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-171">If these operations are successful, the connection is functional.</span></span>  
  
     <span data-ttu-id="5c1a8-172">詳細については、「[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-172">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
#### <a name="to-verify-that-report-designer-is-installed-and-running"></a><span data-ttu-id="5c1a8-173">レポート デザイナーが正常にインストールされ、実行されていることを確認するには</span><span class="sxs-lookup"><span data-stu-id="5c1a8-173">To verify that Report Designer is installed and running</span></span>  
  
1.  <span data-ttu-id="5c1a8-174">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を開き、レポート サーバーのプロジェクトの種類に基づいて新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-174">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and create a new project based on a Report Server project type.</span></span> <span data-ttu-id="5c1a8-175">レポート サーバー プロジェクト ウィザードの使用方法の詳細については、SQL Server オンライン ブックの「[SQL Server データ ツールの Reporting Services (SSDT)](../tools/reporting-services-in-sql-server-data-tools-ssdt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-175">For more information on using the Report Server Project Wizard, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](../tools/reporting-services-in-sql-server-data-tools-ssdt.md) in SQL Server Books Online.</span></span>  
  
2.  <span data-ttu-id="5c1a8-176">サンプル レポートをインストールした場合は、サンプル レポート プロジェクト ファイルを開き、レポート サーバーにレポートをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="5c1a8-176">If you installed report samples, open the sample report project files and publish the reports to a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1a8-177">参照</span><span class="sxs-lookup"><span data-stu-id="5c1a8-177">See Also</span></span>  
 <span data-ttu-id="5c1a8-178">[Reporting Services インストールのトラブルシューティング](troubleshoot-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="5c1a8-178">[Troubleshoot a Reporting Services Installation](troubleshoot-a-reporting-services-installation.md) </span></span>  
 [<span data-ttu-id="5c1a8-179">Reporting Services エラーの原因と解決方法</span><span class="sxs-lookup"><span data-stu-id="5c1a8-179">Cause and Resolution of Reporting Services Errors</span></span>](../troubleshooting/cause-and-resolution-of-reporting-services-errors.md)  
  
  
