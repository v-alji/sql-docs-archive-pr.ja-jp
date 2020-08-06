---
title: 'チュートリアル : Reporting Services ツールを検索および開始する方法 (SSRS) | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder 1.0, locating and starting tool
- Reporting Services, tutorials
- Reporting Services, tools
- Reporting Services Configuration tool
- Business Intelligence Development Studio, locating and starting tool
- Model Designer [Reporting Services], locating and starting tool
- Report Designer [Reporting Services], tutorials
- tools [Reporting Services]
- tutorials [Reporting Services]
- Report Manager [Reporting Services]
ms.assetid: 51ad69d8-fe92-4662-a7cd-d235692f0c03
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b7a981a53378ea6b37959e891cac8bd891c2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721003"
---
# <a name="tutorial-how-to-locate-and-start-reporting-services-tools-ssrs"></a><span data-ttu-id="f1f94-102">チュートリアル : Reporting Services ツールを検索および開始する方法 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="f1f94-102">Tutorial: How to Locate and Start Reporting Services Tools (SSRS)</span></span>
  <span data-ttu-id="f1f94-103">このチュートリアルでは、レポート サーバーの設定、レポート サーバーのコンテンツと動作の管理、レポートの作成とパブリッシュに使用できるツールを紹介します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-103">This tutorial introduces the tools used to configure a report server, manage report server content and operations, and create and publish reports.</span></span> <span data-ttu-id="f1f94-104">このチュートリアルの目的は、ツールを初めて使用する場合にそれぞれのツールをすぐに見つけて起動できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="f1f94-104">The purpose of this tutorial is to help new users understand how to find and open each tool.</span></span> <span data-ttu-id="f1f94-105">既にツールを使用している場合は、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]を使用するときの重要なスキルを学ぶことができるその他のチュートリアルへお進みください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-105">If you are already familiar with the tools, you can move on to other tutorials that can help you learn important skills for using [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="f1f94-106">その他のチュートリアルの詳細については、「 [Reporting Services チュートリアル &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-106">For more information about other tutorials, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).</span></span>  
  
 <span data-ttu-id="f1f94-107">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="f1f94-107">In this topic:</span></span>  
  
-   [<span data-ttu-id="f1f94-108">Reporting Services 構成マネージャー (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="f1f94-108">Reporting Services Configuration Manager (Native Mode)</span></span>](#bkmk_configuration_manager)  
  
-   [<span data-ttu-id="f1f94-109">レポート マネージャー (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="f1f94-109">Report Manager (Native Mode)</span></span>](#bkmk_report_manager)  
  
-   [<span data-ttu-id="f1f94-110">Management Studio</span><span class="sxs-lookup"><span data-stu-id="f1f94-110">Management Studio</span></span>](#bkmk_managements_studio)  
  
-   [<span data-ttu-id="f1f94-111">レポートデザイナーおよびレポートウィザードを使用した SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="f1f94-111">SQL Server Data Tools with Report Designer and Report Wizard</span></span>](#bkmk_ssdt)  
  
-   [<span data-ttu-id="f1f94-112">レポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="f1f94-112">Report Builder</span></span>](#bkmk_report_builder)  
  
##  <a name="reporting-services-configuration-manager-native-mode"></a><a name="bkmk_configuration_manager"></a><span data-ttu-id="f1f94-113">Reporting Services Configuration Manager (ネイティブモード)</span><span class="sxs-lookup"><span data-stu-id="f1f94-113">Reporting Services Configuration Manager (Native Mode)</span></span>  
 <span data-ttu-id="f1f94-114">ネイティブ モードの構成マネージャーを使用して、次の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="f1f94-114">Use the Native mode configuration manager to complete the following:, , , , , and.</span></span>  
  
-   <span data-ttu-id="f1f94-115">サービス アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-115">Specify the service account.</span></span>  
  
-   <span data-ttu-id="f1f94-116">レポート サーバー データベースを作成またはアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-116">Create or upgrade the report server database.</span></span>  
  
-   <span data-ttu-id="f1f94-117">接続プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-117">Modify the connection properties.</span></span>  
  
-   <span data-ttu-id="f1f94-118">URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-118">Specify URLs.</span></span>  
  
-   <span data-ttu-id="f1f94-119">暗号化キーを管理します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-119">Manage encryption keys.</span></span>  
  
-   <span data-ttu-id="f1f94-120">自動レポート処理および電子メールによるレポート配信を構成します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-120">Configure unattended report processing and e-mail report delivery.</span></span>  
  
 <span data-ttu-id="f1f94-121">**インストール:** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成マネージャーは、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ネイティブ モードのインストール時にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-121">**Installation:** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Configuration Manager is installed when you install [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode.</span></span> <span data-ttu-id="f1f94-122">詳細については、「 [Reporting Services ネイティブ モードのレポート サーバーのインストール](../install-windows/install-reporting-services-native-mode-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-122">For more information, see [Install Reporting Services Native Mode Report Server](../install-windows/install-reporting-services-native-mode-report-server.md)</span></span>  
  
#### <a name="to-start-the-reporting-services-configuration-manager"></a><span data-ttu-id="f1f94-123">Reporting Services 構成マネージャーを起動するには</span><span class="sxs-lookup"><span data-stu-id="f1f94-123">To start the Reporting Services Configuration Manager</span></span>  
  
1.  <span data-ttu-id="f1f94-124">Windows のスタート画面で、「」と入力し、 `reporting` **アプリ**の検索結果で [ **Reporting Services Configuration Manager**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-124">On the Windows start screen, type `reporting` and in the **Apps** search results, click **Reporting Services Configuration Manager**.</span></span>  
  
     <span data-ttu-id="f1f94-125">![Reporting Services 構成マネージャーの起動](../media/bi-ssrs-configmanager-win8-startscreen.gif "Reporting Services 構成マネージャーの起動")</span><span class="sxs-lookup"><span data-stu-id="f1f94-125">![reporting services configuration manager on start](../media/bi-ssrs-configmanager-win8-startscreen.gif "reporting services configuration manager on start")</span></span>  
  
     <span data-ttu-id="f1f94-126">**Or**</span><span class="sxs-lookup"><span data-stu-id="f1f94-126">**Or**</span></span>  
  
     <span data-ttu-id="f1f94-127">**[スタート]** ボタンをクリックして、 **[プログラム]** をクリックし、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[構成ツール]**、 **[Reporting Services 構成マネージャー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-127">Click **Start**, then click **Programs**, then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], then click **Configuration Tools**, and then click **Reporting Services Configuration Manager**.</span></span>  
  
     <span data-ttu-id="f1f94-128">**[レポート サーバー インスタンスの選択]** ダイアログ ボックスが表示されます。このダイアログ ボックスでは構成するレポート サーバー インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-128">The **Report Server Installation Instance Selection** dialog box appears so that you can select the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="f1f94-129">**[サーバー名]** ボックスに、レポート サーバー インスタンスがインストールされているコンピューターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-129">In **Server Name**, specify the name of the computer on which the report server instance is installed.</span></span> <span data-ttu-id="f1f94-130">既定ではローカル コンピューターの名前が設定されていますが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のリモート インスタンスの名前を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-130">The name of the local computer is specified by default, but you can also type the name of a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="f1f94-131">リモート コンピューターを指定する場合は、 **[検索]** をクリックして接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-131">If you specify a remote computer, click **Find** to establish a connection.</span></span> <span data-ttu-id="f1f94-132">ここで指定するレポート サーバーは、リモートで管理するための構成が事前に行われている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1f94-132">The report server must be configured for remote administration in advance.</span></span> <span data-ttu-id="f1f94-133">詳細については、「 [リモート管理用のレポート サーバーの構成](../report-server/configure-a-report-server-for-remote-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-133">For more information, see [Configure a Report Server for Remote Administration](../report-server/configure-a-report-server-for-remote-administration.md).</span></span>  
  
3.  <span data-ttu-id="f1f94-134">**[インスタンス名]** で、構成する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-134">In **Instance Name**, choose the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span> <span data-ttu-id="f1f94-135">この一覧には [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、および [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のレポート サーバー インスタンスのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-135">Only [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server instances appear in the list.</span></span> <span data-ttu-id="f1f94-136">以前のバージョンの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="f1f94-136">You cannot configure earlier versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="f1f94-137">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-137">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="f1f94-138">ツールが起動したかどうかを確認するには、次の図と比較します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-138">To verify that you launched the tool, compare your results to the following image:</span></span>  
  
     <span data-ttu-id="f1f94-139">![Reporting Services 構成ツール](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services 構成ツール")</span><span class="sxs-lookup"><span data-stu-id="f1f94-139">![Reporting Services Configuration tool](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services Configuration tool")</span></span>  
  
 <span data-ttu-id="f1f94-140">**次の手順: 「** [レポート サーバーを構成および管理する (SSRS ネイティブ モード)](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)」、「[Reporting Services 構成マネージャー (ネイティブ モード)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)</span><span class="sxs-lookup"><span data-stu-id="f1f94-140">**Next Steps:** [Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) and [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
##  <a name="report-manager-native-mode"></a><a name="bkmk_report_manager"></a><span data-ttu-id="f1f94-141">レポートマネージャー (ネイティブモード)</span><span class="sxs-lookup"><span data-stu-id="f1f94-141">Report Manager (Native Mode)</span></span>  
 <span data-ttu-id="f1f94-142">[レポートマネージャー &#40;SSRS ネイティブモード&#41;](../report-manager-ssrs-native-mode.md)を使用して、権限の設定、サブスクリプションとスケジュールの管理、およびレポートの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f1f94-142">Use [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) to set permissions, manage subscriptions and schedules, and work with reports.</span></span> <span data-ttu-id="f1f94-143">また、レポート マネージャーを使ってレポートを閲覧することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-143">You can also use Report Manager to view reports.</span></span>  
  
 <span data-ttu-id="f1f94-144">**インストール:** ネイティブモードをインストールするとレポートマネージャーがインストールされ [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ます。 [Reporting Services ネイティブモードのレポートサーバーをインストール](../install-windows/install-reporting-services-native-mode-report-server.md)する</span><span class="sxs-lookup"><span data-stu-id="f1f94-144">**Installation:** Report Manager Is installed when you install [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode: [Install Reporting Services Native Mode Report Server](../install-windows/install-reporting-services-native-mode-report-server.md)</span></span>  
  
 <span data-ttu-id="f1f94-145">レポート マネージャーを起動するには適切なアクセス許可が必要です。初期状態では、レポート マネージャーの機能へのアクセス許可は、ローカルの管理者グループのメンバーにのみ与えられています。</span><span class="sxs-lookup"><span data-stu-id="f1f94-145">Before you can open Report Manager, you must have sufficient permissions (initially, only members of the local Administrators group have permissions that provide access to Report Manager features).</span></span> <span data-ttu-id="f1f94-146">レポート マネージャーに表示されるページとオプションは、現在のユーザーに割り当てられているロールによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f1f94-146">Report Manager provides different pages and options depending on the role assignments of the current user.</span></span> <span data-ttu-id="f1f94-147">アクセス許可のないユーザーには空白のページが表示され、</span><span class="sxs-lookup"><span data-stu-id="f1f94-147">Users who have no permissions will get an empty page.</span></span> <span data-ttu-id="f1f94-148">レポート閲覧用のアクセス許可が与えられているユーザーにはリンクが表示されます。このユーザーはリンクをクリックしてレポートを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-148">Users with permissions to view reports will get links that they can click to open the reports.</span></span> <span data-ttu-id="f1f94-149">アクセス許可の詳細については、「[ロールと権限 &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-149">To learn more about permissions, see [Roles and Permissions &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).</span></span>  
  
#### <a name="to-start-report-manager"></a><span data-ttu-id="f1f94-150">レポート マネージャーを起動するには</span><span class="sxs-lookup"><span data-stu-id="f1f94-150">To start Report Manager</span></span>  
  
1.  <span data-ttu-id="f1f94-151">ブラウザーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-151">Open your browser.</span></span> <span data-ttu-id="f1f94-152">サポートされているブラウザーとブラウザーのバージョンについては、「 [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-152">For information on supported browsers and browser versions, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
2.  <span data-ttu-id="f1f94-153">Web ブラウザーのアドレス バーに、レポート マネージャーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-153">In the address bar of the Web browser, type the Report Manager URL.</span></span> <span data-ttu-id="f1f94-154">既定では、URL は**http:// \<serverName> /reports**です。</span><span class="sxs-lookup"><span data-stu-id="f1f94-154">By default, the URL is **http://\<serverName>/reports**.</span></span> <span data-ttu-id="f1f94-155">Reporting Services 構成ツールを使用して、サーバー名と URL を確認できます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-155">You can use the Reporting Services Configuration tool to confirm the server name and URL.</span></span> <span data-ttu-id="f1f94-156">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] で使用される URL の詳細については、「[レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-156">For more information about URLs used in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="f1f94-157">レポート マネージャーがブラウザー ウィンドウ内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-157">Report Manager opens in the browser window.</span></span> <span data-ttu-id="f1f94-158">最初のページは [ホーム] フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="f1f94-158">The startup page is the Home folder.</span></span> <span data-ttu-id="f1f94-159">アクセス許可に応じて、最初のページにその他のフォルダー、レポートへのハイパーリンク、リソース ファイルなどが表示される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f1f94-159">Depending on permissions, you might see additional folders, hyperlinks to reports, and resource files within the startup page.</span></span> <span data-ttu-id="f1f94-160">ツール バーに追加のボタンやコマンドが表示される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f1f94-160">You might also see additional buttons and commands on the toolbar.</span></span>  
  
4.  <span data-ttu-id="f1f94-161">ローカルレポートサーバーでレポートマネージャーを実行する場合は、「[ローカル管理用のネイティブモードのレポートサーバーの構成 &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-161">If you run Report Manager on the local report server, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
 <span data-ttu-id="f1f94-162">**次のステップ:** [レポートマネージャー &#40;ネイティブモード&#41;を構成](../report-server/configure-web-portal.md)します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-162">**Next Steps:** [Configure Report Manager &#40;Native Mode&#41;](../report-server/configure-web-portal.md).</span></span>  
  
##  <a name="management-studio"></a><a name="bkmk_managements_studio"></a> <span data-ttu-id="f1f94-163">Management Studio</span><span class="sxs-lookup"><span data-stu-id="f1f94-163">Management Studio</span></span>  
 <span data-ttu-id="f1f94-164">レポート サーバー管理者は、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して、レポート サーバーと共に他の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コンポーネント サーバーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-164">Report server administrators can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to manage a report server alongside other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] component servers.</span></span> <span data-ttu-id="f1f94-165">詳細については、「 [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-165">For more information, see [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-start-sql-server-management-studio"></a><span data-ttu-id="f1f94-166">SQL Server Management Studio を起動するには</span><span class="sxs-lookup"><span data-stu-id="f1f94-166">To Start SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="f1f94-167">Windows のスタート画面で「 `sql server` 」と入力し、**アプリ**の検索結果で [ **SQL Server Management Studio**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-167">From the Windows Start Screen type `sql server` and in the **Apps** search results, click **SQL Server Management Studio**.</span></span>  
  
     <span data-ttu-id="f1f94-168">![Windows のスタート画面の Management Studio](../media/bi-ssms-win8-startscreen.gif "Windows のスタート画面の Management Studio")</span><span class="sxs-lookup"><span data-stu-id="f1f94-168">![managment studio from windows start screen](../media/bi-ssms-win8-startscreen.gif "managment studio from windows start screen")</span></span>  
  
     <span data-ttu-id="f1f94-169">**Or**</span><span class="sxs-lookup"><span data-stu-id="f1f94-169">**Or**</span></span>  
  
     <span data-ttu-id="f1f94-170">**[スタート]**、 **[すべてのプログラム]** とクリックし、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[SQL Server Management Studio]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-170">Click **Start**, then click **All Programs**, then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span> <span data-ttu-id="f1f94-171">**[サーバーに接続]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-171">The **Connect to Server** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="f1f94-172">**[サーバーへの接続]** ダイアログ ボックスが表示されない場合は、 **[オブジェクト エクスプローラー]** で **[接続]** をクリックし、 **[Reporting Services]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-172">If the **Connect to Server** dialog box does not appear, in **Object Explorer**, click **Connect** and then select **Reporting Services**.</span></span>  
  
3.  <span data-ttu-id="f1f94-173">**[サーバーの種類]** ボックスの一覧で、 **[Reporting Services]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-173">In the **Server type** list, select **Reporting Services**.</span></span> <span data-ttu-id="f1f94-174">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] が一覧に表示されない場合、Reporting Services はインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="f1f94-174">If [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is not on the list, it is not installed.</span></span>  
  
4.  <span data-ttu-id="f1f94-175">**[サーバー名]** ボックスの一覧で、レポート サーバーのインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-175">In the **Server name** list, select a report server instance.</span></span> <span data-ttu-id="f1f94-176">一覧にはローカル インスタンスが表示されますが、</span><span class="sxs-lookup"><span data-stu-id="f1f94-176">Local instances appear in the list.</span></span> <span data-ttu-id="f1f94-177">リモートの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-177">You can also type the name of a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="f1f94-178">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-178">Click **Connect**.</span></span> <span data-ttu-id="f1f94-179">ルート ノードを展開して、サーバーのプロパティを設定したり、ロールの定義を変更したり、レポート サーバー機能をオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-179">You can expand the root node to set server properties, modify role definitions, or turn off report server features.</span></span>  
  
##  <a name="sql-server-data-tools-with-report-designer-and-report-wizard"></a><a name="bkmk_ssdt"></a> <span data-ttu-id="f1f94-180">レポート デザイナーとレポート ウィザードが統合された SQL Server データ ツール</span><span class="sxs-lookup"><span data-stu-id="f1f94-180">SQL Server Data Tools with Report Designer and Report Wizard</span></span>  
 <span data-ttu-id="f1f94-181">レポート デザイナーは、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] - Business Intelligence for Visual Studio 2012 で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-181">Report Designer is available within [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] - Business Intelligence for Visual Studio 2012.</span></span> <span data-ttu-id="f1f94-182">このツールのデザイン画面にはタブ付きウィンドウ、ウィザード、メニューが用意されており、これらを使ってレポートの作成機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-182">The design surface in the tool includes tabbed windows, wizards, and menus used to access report authoring features.</span></span> <span data-ttu-id="f1f94-183">レポート デザイナー ツールは、レポート サーバー プロジェクトまたはレポート サーバー ウィザードのテンプレートを選択すると使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="f1f94-183">The report designer tool becomes available when you choose a Report Server Project or a Report Server Wizard template.</span></span> <span data-ttu-id="f1f94-184">詳細については、「[SQL Server データ ツールの Reporting Services (SSDT)](reporting-services-in-sql-server-data-tools-ssdt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-184">To learn more, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).</span></span>  
  
#### <a name="to-start-report-designer"></a><span data-ttu-id="f1f94-185">レポート デザイナーを起動するには</span><span class="sxs-lookup"><span data-stu-id="f1f94-185">To start Report Designer</span></span>  
  
1.  <span data-ttu-id="f1f94-186">Windows のスタート画面から「 **data** 」と入力し、 **[アプリ]** の検索結果で **[SQL Server Data Tools for Visual Studio 2012]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-186">From the Windows start screen, type **data** and in the **Apps** search results, click **SQL Server Data Tools for Visual Studio 2012**.</span></span>  
  
     <span data-ttu-id="f1f94-187">**Or**</span><span class="sxs-lookup"><span data-stu-id="f1f94-187">**Or**</span></span>  
  
     <span data-ttu-id="f1f94-188">[**スタート**] をクリックし、[**すべてのプログラム**]、[] の順にポイントして、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] **SQL Server Data Tools] (SSDT)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-188">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], and then click **SQL Server Data Tools (SSDT)**.</span></span>  
  
2.  <span data-ttu-id="f1f94-189">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-189">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="f1f94-190">**[プロジェクトの種類]** ボックスの一覧で、 **[ビジネス インテリジェンス プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-190">In the **Project Types** list, click **Business Intelligence Projects**.</span></span>  
  
4.  <span data-ttu-id="f1f94-191">**[テンプレート]** ボックスの一覧で、 **[レポート サーバー プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-191">In the **Templates** list, click **Report Server Project**.</span></span> <span data-ttu-id="f1f94-192">次の図は、プロジェクトのテンプレートがダイアログ ボックスに表示された状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="f1f94-192">The following diagram shows how the project templates appear in the dialog box:</span></span>  
  
     <span data-ttu-id="f1f94-193">![新しいプロジェクト テンプレートのダイアログ ボックス](../media/rs-ui-newrsproject.gif "新しいプロジェクト テンプレートのダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="f1f94-193">![New Project template dialog box](../media/rs-ui-newrsproject.gif "New Project template dialog box")</span></span>  
  
5.  <span data-ttu-id="f1f94-194">プロジェクトの名前と場所を入力するか、 **[参照]** ボタンをクリックして場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-194">Type a name and location for the project, or click **Browse** and select a location.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]<span data-ttu-id="f1f94-195">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]スタートページが表示さ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-195">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] opens with the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] start page.</span></span> <span data-ttu-id="f1f94-196">ソリューション エクスプローラーには、レポートとデータ ソースがそれぞれカテゴリとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-196">Solution Explorer provides categories for creating reports and data sources.</span></span> <span data-ttu-id="f1f94-197">これらのカテゴリを使用して、新しいレポートとデータ ソースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-197">You can use these categories to create new reports and data sources.</span></span> <span data-ttu-id="f1f94-198">タブ付きウィンドウは、レポート定義を作成すると表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-198">Tabbed windows appear when you create a report definition.</span></span> <span data-ttu-id="f1f94-199">このウィンドウは [データ]、[レイアウト]、[プレビュー] の 3 つのタブで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-199">The tabbed windows are Data, Layout, and Preview..</span></span>  
  
 <span data-ttu-id="f1f94-200">初めてレポートを作成する場合は、「[基本的なテーブル レポートの作成 &#40;SSRS チュートリアル&#41;](../create-a-basic-table-report-ssrs-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-200">To get started on your first report, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md).</span></span> <span data-ttu-id="f1f94-201">レポートデザイナー内で使用できるクエリデザイナーの詳細については、[レポートデザイナー SQL Server Data Tools &#40;SSRS&#41;のクエリデザインツール](../report-data/query-design-tools-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-201">To learn more about query designers you can use within Report Designer, see [Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md).</span></span>  
  
##  <a name="report-builder"></a><a name="bkmk_report_builder"></a> <span data-ttu-id="f1f94-202">レポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="f1f94-202">Report Builder</span></span>  
 <span data-ttu-id="f1f94-203">Office と同様の作成環境でレポートを作成するには、[レポートビルダー &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md)を使用し [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-203">Use [Report Builder &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md) to create reports in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office-like authoring environment.</span></span> <span data-ttu-id="f1f94-204">レポート デザイナーで作成したレポートであっても、以前のバージョンのレポート ビルダーでデザインしたレポートであっても、あらゆる既存レポートのカスタマイズおよび更新が可能です。</span><span class="sxs-lookup"><span data-stu-id="f1f94-204">You can customize and update all existing reports, regardless of whether they were created in Report Designer or in the previous versions of Report Builder.</span></span> <span data-ttu-id="f1f94-205">レポート ビルダーをローカル コンピューターにインストールするために実行する ReportBuilder3.msi ファイルの場所については、管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="f1f94-205">Contact your administrator for the location of the ReportBuilder3.msi file that you run to install Report Builder on your local computer.</span></span>  
  
 <span data-ttu-id="f1f94-206">**インストール:** レポートビルダーのクリック時バージョンは、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ネイティブモードまたは SharePoint モードでインストールされます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-206">**Installation:** The click-once version of report builder is installed by either [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode or SharePoint mode.</span></span> <span data-ttu-id="f1f94-207">レポート ビルダーのスタンドアロン バージョンは別のダウンロードです。</span><span class="sxs-lookup"><span data-stu-id="f1f94-207">The Stand-alone version of Report Builder is a separate download.</span></span>  <span data-ttu-id="f1f94-208">「[レポートビルダー &#40;レポートビルダーのスタンドアロンバージョンのインストール](../install-windows/install-report-builder.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="f1f94-208">See [Install the Stand-Alone Version of Report Builder &#40;Report Builder&#41;](../install-windows/install-report-builder.md)</span></span>  
  
#### <a name="to-start-report-builder-clickonce-from-report-manager-native-mode"></a><span data-ttu-id="f1f94-209">レポート マネージャーからレポート ビルダー ClickOnce を起動するには (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="f1f94-209">To start Report Builder ClickOnce from Report Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="f1f94-210">Web ブラウザーで、レポート マネージャーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-210">In your Web browser, type the Report Manager URL for your report server.</span></span> <span data-ttu-id="f1f94-211">既定では、URL は http:// \<*servername*> /レポートです。</span><span class="sxs-lookup"><span data-stu-id="f1f94-211">By default, the URL is http://\<*servername*>/reports.</span></span> <span data-ttu-id="f1f94-212">レポート マネージャーが開きます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-212">Report Manager opens.</span></span>  
  
2.  <span data-ttu-id="f1f94-213">**[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-213">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="f1f94-214">レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-214">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-clickonce-using-a-url"></a><span data-ttu-id="f1f94-215">URL を使用してレポート ビルダー ClickOnce を起動するには</span><span class="sxs-lookup"><span data-stu-id="f1f94-215">To start Report Builder ClickOnce using a URL</span></span>  
  
1.  <span data-ttu-id="f1f94-216">Web ブラウザーでアドレス バーに次の URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-216">In your Web browser, type the following URL in the address bar:</span></span>  
  
     <span data-ttu-id="f1f94-217">**http:// \<servername> /reportserver/reportbuilder/ReportBuilder_3_0_0_0**</span><span class="sxs-lookup"><span data-stu-id="f1f94-217">**http://\<servername>/reportserver/reportbuilder/ReportBuilder_3_0_0_0.application**</span></span>  
  
2.  <span data-ttu-id="f1f94-218">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-218">Press ENTER.</span></span>  
  
     <span data-ttu-id="f1f94-219">レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-219">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-clickonce-in-reporting-services-sharepoint-mode"></a><span data-ttu-id="f1f94-220">レポート ビルダー ClickOnce を Reporting Services SharePoint モードで起動するには</span><span class="sxs-lookup"><span data-stu-id="f1f94-220">To start Report Builder ClickOnce in Reporting Services SharePoint mode</span></span>  
  
1.  <span data-ttu-id="f1f94-221">新しいレポートを作成するライブラリがあるサイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="f1f94-221">Navigate to the site that contains the library where you want to create a new report.</span></span>  
  
2.  <span data-ttu-id="f1f94-222">ライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-222">Open the library.</span></span>  
  
3.  <span data-ttu-id="f1f94-223">**[新規作成]** メニューの **[レポート ビルダー レポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-223">On the **New** menu, click **Report Builder Report**.</span></span>  
  
     <span data-ttu-id="f1f94-224">レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-224">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-stand-alone"></a><span data-ttu-id="f1f94-225">レポート ビルダー スタンドアロンを起動するには</span><span class="sxs-lookup"><span data-stu-id="f1f94-225">To start Report Builder Stand-alone</span></span>  
  
1.  <span data-ttu-id="f1f94-226">Windows のスタート画面から、「 **report builder** 」と入力し、 **[レポート ビルダー 3.0]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-226">From the Windows start screen, type **report builder** and then click **Report Builder 3.0**.</span></span>  
  
     <span data-ttu-id="f1f94-227">**Or**</span><span class="sxs-lookup"><span data-stu-id="f1f94-227">**Or**</span></span>  
  
     <span data-ttu-id="f1f94-228">[スタート] メニューの **[すべてのプログラム]** をクリックして、 **[Microsoft SQL Server 2014 レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-228">On the Start menu, click **All Programs**, and then click **Microsoft SQL Server 2014 Report Builder**.</span></span>  
  
2.  <span data-ttu-id="f1f94-229">**[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-229">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="f1f94-230">レポート ビルダーが開き、レポートを作成したり、レポートを開いたりできます。</span><span class="sxs-lookup"><span data-stu-id="f1f94-230">Report Builder opens and you can create or open a report.</span></span>  
  
3.  <span data-ttu-id="f1f94-231">レポート ビルダーに関するドキュメントを開くには、 **[Report Builder ヘルプ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1f94-231">Click **Report Builder Help** to open the documentation for Report Builder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f94-232">参照</span><span class="sxs-lookup"><span data-stu-id="f1f94-232">See Also</span></span>  
 <span data-ttu-id="f1f94-233">[インストール、アンインストール、およびレポートビルダーサポート](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="f1f94-233">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="f1f94-234">[Sharepoint モードのインストール Reporting Services sharepoint 2010 および SharePoint 2013&#41;&#40;](../install-windows/install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f1f94-234">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](../install-windows/install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="f1f94-235">[レポートサーバーの Reporting Services](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="f1f94-235">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="f1f94-236">[レポートデザイナー SQL Server Data Tools のクエリデザインツール &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f1f94-236">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md) </span></span>  
 [<span data-ttu-id="f1f94-237">Reporting Services チュートリアル &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f1f94-237">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
