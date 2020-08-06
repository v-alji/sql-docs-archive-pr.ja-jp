---
title: レポート サーバーの構成 (Reporting Services ネイティブ モード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report server configuration
- report servers [Reporting Services], configuring
ms.assetid: ef84ce9d-9156-48e9-8073-7e0535476932
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 64c63f52c373e034f0242101de0a27ee775920ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642561"
---
# <a name="configure-a-report-server-reporting-services-native-mode"></a><span data-ttu-id="0f26c-102">レポート サーバーの構成 (Reporting Services ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="0f26c-102">Configure a Report Server (Reporting Services Native Mode)</span></span>
  <span data-ttu-id="0f26c-103">インストール中に選択したオプションによっては、レポート サーバーを使用する前に追加の構成が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f26c-103">Depending on options you selected during installation, the Report Server might require additional configuration before you can use it.</span></span> <span data-ttu-id="0f26c-104">少なくともレポート サーバーの構成には以下が必要です。</span><span class="sxs-lookup"><span data-stu-id="0f26c-104">At a minimum, a report server configuration consists of the following:</span></span>  
  
-   <span data-ttu-id="0f26c-105">レポート サーバー サービス アカウント (インストール中に設定される)</span><span class="sxs-lookup"><span data-stu-id="0f26c-105">A Report Server service account (configured during installation).</span></span>  
  
-   <span data-ttu-id="0f26c-106">レポート サーバーへのアクセスを提供する Web サービス URL</span><span class="sxs-lookup"><span data-stu-id="0f26c-106">A Web service URL that provides access to the report server.</span></span>  
  
-   <span data-ttu-id="0f26c-107">アプリケーション データ、レポート、およびその他のアイテムを格納するレポート サーバー データベース</span><span class="sxs-lookup"><span data-stu-id="0f26c-107">A report server database that stores application data, reports, and other items.</span></span>  
  
 <span data-ttu-id="0f26c-108">ネイティブ モードの既定の構成または SharePoint 統合モードの既定の構成のいずれかのインストール オプションを選択した場合は、セットアップによって最小の設定が構成されます。</span><span class="sxs-lookup"><span data-stu-id="0f26c-108">Setup configures the minimum settings if you select either of the following installation options: Native mode default configuration or SharePoint integrated mode default configuration.</span></span> <span data-ttu-id="0f26c-109">レポート サーバーをファイルのみのモードでインストールした場合 (インストール ウィザードで **[サーバーを構成せずにインストールする]** オプションを選択した場合) は、サービス アカウントのみ構成されます。</span><span class="sxs-lookup"><span data-stu-id="0f26c-109">If you installed the report server in files-only mode (this is the **Install but do not configure** option in the Installation wizard), only the service account is configured.</span></span> <span data-ttu-id="0f26c-110">Web サービス URL とレポート サーバー データベースは、セットアップの完了後に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f26c-110">The Web service URL and report server database must be configured after Setup is finished.</span></span>  
  
 <span data-ttu-id="0f26c-111">レポート マネージャーは、ネイティブ モードのレポート サーバーのオプション機能ですが、レポート サーバーへのアクセス権をユーザーに付与したり、レポート サーバーのコンテンツを管理したりできるようにレポート マネージャーを構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0f26c-111">Report Manager is an optional feature for a native mode report server, but it is recommended that you configure Report Manager so that you can grant user access to the report server and manage report server content.</span></span> <span data-ttu-id="0f26c-112">SharePoint 統合モードでレポート サーバーを配置した場合、SharePoint サーバーの Web フロントエンドを使用してアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="0f26c-112">If you deploy a report server in SharePoint integrated mode, use the Web front-end of a SharePoint server to grant access.</span></span>  
  
 <span data-ttu-id="0f26c-113">レポート サーバーの電子メールや自動実行アカウントなどの追加の機能は、必要に応じて構成できます。</span><span class="sxs-lookup"><span data-stu-id="0f26c-113">Additional features, such as report server e-mail and the unattended execution account, can be configured as needed.</span></span> <span data-ttu-id="0f26c-114">詳細については、「 [Reporting Services ネイティブ モードのレポート サーバーの管理](manage-a-reporting-services-native-mode-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f26c-114">For more information, see [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="0f26c-115">レポート サーバーを構成するには、Reporting Services 構成ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f26c-115">To configure a report server, use the Reporting Services Configuration tool.</span></span>  
  
### <a name="to-minimally-configure-a-report-server-installation"></a><span data-ttu-id="0f26c-116">レポート サーバー インストールの最小構成を行うには</span><span class="sxs-lookup"><span data-stu-id="0f26c-116">To minimally configure a report server installation</span></span>  
  
1.  <span data-ttu-id="0f26c-117">Reporting Services 構成マネージャーを起動して、レポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0f26c-117">Start the Reporting Services Configuration Manager and connect to the report server instance.</span></span> <span data-ttu-id="0f26c-118">手順については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f26c-118">For instructions, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="0f26c-119">**[Web サービス URL]** をクリックして、レポート サーバーの URL を構成するページを開きます。</span><span class="sxs-lookup"><span data-stu-id="0f26c-119">Click **Web Service URL** to open the page for configuring a URL for the report server.</span></span> <span data-ttu-id="0f26c-120">URL を定義する方法については、「[URL の構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f26c-120">For instructions on how to define the URL, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="0f26c-121">**[データベース]** をクリックして、レポート サーバー データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="0f26c-121">Click **Database** to create the report server database.</span></span> <span data-ttu-id="0f26c-122">手順については、「[ネイティブ モード レポート サーバー データベースの作成 &#40;SSRS 構成マネージャー&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f26c-122">For instructions, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
4.  <span data-ttu-id="0f26c-123">**[Web サービス URL]** ページに戻り、URL をクリックして機能するかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="0f26c-123">Go back to the **Web Service URL** page and click the URL to verify it works.</span></span>  
  
5.  <span data-ttu-id="0f26c-124">「次の手順」の指示に従って配置を完了します。</span><span class="sxs-lookup"><span data-stu-id="0f26c-124">Follow the instructions in "Next Steps" to complete your deployment.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0f26c-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="0f26c-125">Next Steps</span></span>  
 <span data-ttu-id="0f26c-126">配置を完了するには、レポート マネージャーまたは SharePoint 統合を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f26c-126">To complete your deployment, you should configure Report Manager or SharePoint integration.</span></span> <span data-ttu-id="0f26c-127">詳細については、「[レポート マネージャーの構成 (ネイティブ モード)](configure-web-portal.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f26c-127">For more information, see [Configure Report Manager &#40;Native Mode&#41;](configure-web-portal.md).</span></span>  
  
 <span data-ttu-id="0f26c-128">Windows ファイアウォールが有効になっている場合、レポート サーバーで使用するように構成されているポートは閉じられる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="0f26c-128">If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed.</span></span> <span data-ttu-id="0f26c-129">ポートが閉じられている場合は、たとえばリモート クライアント コンピューターからレポート マネージャーを開こうとすると、空のページが返されます。</span><span class="sxs-lookup"><span data-stu-id="0f26c-129">One indication that a port might be closed is a blank page when you attempt to open Report Manager from a remote client computer.</span></span> <span data-ttu-id="0f26c-130">ファイアウォールの構成の詳細については、「 [レポート サーバー アクセスに対するファイアウォールの構成](configure-a-firewall-for-report-server-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f26c-130">For information on configuring the firewall, see [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
 <span data-ttu-id="0f26c-131">Windows Vista または Windows Server 2008 を使用している場合は、レポート マネージャーをローカルで開く前に追加の手順が必要になります。</span><span class="sxs-lookup"><span data-stu-id="0f26c-131">If you are using Windows Vista or Windows Server 2008, additional steps are required before you can open Report Manager locally.</span></span> <span data-ttu-id="0f26c-132">詳細については、「 [ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f26c-132">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
 <span data-ttu-id="0f26c-133">フォルダーを作成し、アイテムをアップロードし、レポートを実行してインストール状況を確認します。</span><span class="sxs-lookup"><span data-stu-id="0f26c-133">Verify your installation by creating folders, uploading items, and running reports.</span></span> <span data-ttu-id="0f26c-134">インストール状況を確認するには、「 [Reporting Services のインストール状態の検証](../install-windows/verify-a-reporting-services-installation.md) 」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0f26c-134">Follow the instructions in [Verify a Reporting Services Installation](../install-windows/verify-a-reporting-services-installation.md) to verify your installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f26c-135">参照</span><span class="sxs-lookup"><span data-stu-id="0f26c-135">See Also</span></span>  
 <span data-ttu-id="0f26c-136">[Reporting Services ネイティブ モードのレポート サーバーの管理](manage-a-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0f26c-136">[Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="0f26c-137">[レポート サーバー アクセスに対するファイアウォールの構成](configure-a-firewall-for-report-server-access.md) </span><span class="sxs-lookup"><span data-stu-id="0f26c-137">[Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md) </span></span>  
 <span data-ttu-id="0f26c-138">[ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](configure-a-native-mode-report-server-for-local-administration-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0f26c-138">[Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md) </span></span>  
 <span data-ttu-id="0f26c-139">[リモート管理用のレポート サーバーの構成](configure-a-report-server-for-remote-administration.md) </span><span class="sxs-lookup"><span data-stu-id="0f26c-139">[Configure a Report Server for Remote Administration](configure-a-report-server-for-remote-administration.md) </span></span>  
 [<span data-ttu-id="0f26c-140">Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="0f26c-140">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
