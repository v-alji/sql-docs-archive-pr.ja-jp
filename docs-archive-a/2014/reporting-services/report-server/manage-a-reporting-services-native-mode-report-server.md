---
title: Reporting Services ネイティブ モードのレポート サーバーの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d44a9329074a20c04f878c055674ea563b297f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642540"
---
# <a name="manage-a-reporting-services-native-mode-report-server"></a><span data-ttu-id="95b76-102">Reporting Services ネイティブ モードのレポート サーバーの管理</span><span class="sxs-lookup"><span data-stu-id="95b76-102">Manage a Reporting Services Native Mode Report Server</span></span>
  <span data-ttu-id="95b76-103">ここでは、Reporting Services 構成マネージャーを使用してネイティブ モードのレポート サーバー インスタンスを構成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-103">This section contains procedures for configuring a native mode report server instance using the Reporting Services Configuration Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95b76-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="95b76-104">In This Section</span></span>  
 <span data-ttu-id="95b76-105">このセクションのトピックは、必要な手順をより簡単に見つけることができるようにカテゴリ別に分類されています。</span><span class="sxs-lookup"><span data-stu-id="95b76-105">The topics in this section are organized into categories so that you can more easily find the instructions you want.</span></span> <span data-ttu-id="95b76-106">最初のセクションでは、ネイティブ モードのレポート サーバーの基本的な構成タスクに関するトピックについて紹介します。</span><span class="sxs-lookup"><span data-stu-id="95b76-106">The first section contains topics for basic configuration tasks for a native mode report server.</span></span> <span data-ttu-id="95b76-107">2 番目のセクションでは、詳細な構成に関するトピックについて紹介します。</span><span class="sxs-lookup"><span data-stu-id="95b76-107">The second section contains advanced configuration topics.</span></span> <span data-ttu-id="95b76-108">3 番目のセクションでは、SharePoint 統合モードで実行されるレポート サーバーの構成に関するトピックについて紹介します。</span><span class="sxs-lookup"><span data-stu-id="95b76-108">The third section contains topics for configuring a report server to run in SharePoint integrated mode.</span></span>  
  
### <a name="basic-configuration"></a><span data-ttu-id="95b76-109">基本構成</span><span class="sxs-lookup"><span data-stu-id="95b76-109">Basic Configuration</span></span>  
 [<span data-ttu-id="95b76-110">Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="95b76-110">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
 <span data-ttu-id="95b76-111">Reporting Services の構成ツールを開始するための手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-111">Provides steps for starting the Reporting Services Configuration tool.</span></span>  
  
 [<span data-ttu-id="95b76-112">サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="95b76-112">Configure a Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="95b76-113">レポート サーバー サービス用のアカウントとパスワードの情報を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-113">Explains how to specify account and password information for the Report Server service.</span></span>  
  
 [<span data-ttu-id="95b76-114">レポート サーバーのサービス プリンシパル名 (SPN) の登録</span><span class="sxs-lookup"><span data-stu-id="95b76-114">Register a Service Principal Name &#40;SPN&#41; for a Report Server</span></span>](register-a-service-principal-name-spn-for-a-report-server.md)  
 <span data-ttu-id="95b76-115">Kerberos 認証を使用するネットワーク上でドメイン ユーザー アカウントで実行されるレポート サーバーの SPN を手動で登録する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-115">Explains how to manually register an SPN for a report server that runs under a domain user account on a network that uses Kerberos authentication.</span></span>  
  
 [<span data-ttu-id="95b76-116">URL の構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="95b76-116">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-a-url-ssrs-configuration-manager.md)  
 <span data-ttu-id="95b76-117">レポート サーバー Web サービスおよびレポート マネージャーへのアクセスに使用する 1 つ以上の URL の設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-117">Explains how to establish one or more URLs used to access the Report Server Web service and Report Manager.</span></span>  
  
 [<span data-ttu-id="95b76-118">ネイティブ モード レポート サーバー データベースの作成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="95b76-118">Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 <span data-ttu-id="95b76-119">レポート サーバー データベースを作成するための手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-119">Provides steps for creating a report server database.</span></span> <span data-ttu-id="95b76-120">この手順は、Reporting Services のインストールの配置に必要です。</span><span class="sxs-lookup"><span data-stu-id="95b76-120">This step is required for deploying a Reporting Services installation.</span></span>  
  
### <a name="advanced-or-optional-configuration"></a><span data-ttu-id="95b76-121">詳細な構成または省略可能な構成</span><span class="sxs-lookup"><span data-stu-id="95b76-121">Advanced or Optional Configuration</span></span>  
 [<span data-ttu-id="95b76-122">ネイティブ モード レポート サーバーのスケールアウト配置の構成 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="95b76-122">Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 <span data-ttu-id="95b76-123">レポート サーバー データベースを共有するための複数のレポート サーバーの構成手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-123">Provides steps for configuring multiple report servers to share a report server database.</span></span>  
  
 [<span data-ttu-id="95b76-124">SSRS Configuration Manager &#40;電子メール配信用にレポートサーバーを構成&#41;</span><span class="sxs-lookup"><span data-stu-id="95b76-124">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 <span data-ttu-id="95b76-125">電子メール配信用のレポート サーバーを構成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-125">Provides steps for configuring a report server for e-mail distribution.</span></span>  
  
 [<span data-ttu-id="95b76-126">レポート サーバー アクセスに対するファイアウォールの構成</span><span class="sxs-lookup"><span data-stu-id="95b76-126">Configure a Firewall for Report Server Access</span></span>](configure-a-firewall-for-report-server-access.md)  
 <span data-ttu-id="95b76-127">レポート サーバーの要求の受信と応答の送信に使用されるポートを開く方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-127">Explains how to open ports used for inbound requests and outbound responses from a report server.</span></span>  
  
 [<span data-ttu-id="95b76-128">ローカル管理用のネイティブ モードのレポート サーバー (SSRS) の構成</span><span class="sxs-lookup"><span data-stu-id="95b76-128">Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;</span></span>](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 <span data-ttu-id="95b76-129">http://localhost を使用してレポート マネージャーまたはレポート サーバーに接続するために必要な追加手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-129">Describes additional steps required to connect to Report Manager or a report server using http://localhost.</span></span>  
  
 [<span data-ttu-id="95b76-130">リモート管理用のレポート サーバーの構成</span><span class="sxs-lookup"><span data-stu-id="95b76-130">Configure a Report Server for Remote Administration</span></span>](configure-a-report-server-for-remote-administration.md)  
 <span data-ttu-id="95b76-131">リモートのレポート サーバー インスタンスに接続したり別のコンピューターから構成したりすることができるようにインスタンスを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-131">Explains how to configure a remote report server instance so that you can connect to and configure it from a different computer.</span></span>  
  
 [<span data-ttu-id="95b76-132">Reporting Services 機能の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="95b76-132">Turn Reporting Services Features On or Off</span></span>](turn-reporting-services-features-on-or-off.md)  
 <span data-ttu-id="95b76-133">使用しない機能を Reporting Services から削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-133">Explains how to remove unused features in a Reporting Services installation.</span></span>  
  
 [<span data-ttu-id="95b76-134">リモート エラーの有効化 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="95b76-134">Enable Remote Errors &#40;Reporting Services&#41;</span></span>](enable-remote-errors-reporting-services.md)  
 <span data-ttu-id="95b76-135">リモート サーバーで発生するエラー状態に関する追加情報を返すように、レポート サーバーのサーバー プロパティを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95b76-135">Explains how to set server properties on a report server to return additional information about error conditions that occur on remote servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b76-136">参照</span><span class="sxs-lookup"><span data-stu-id="95b76-136">See Also</span></span>  
 <span data-ttu-id="95b76-137">[レポート サーバーを構成および管理する &#40;SSRSネイティブ モード&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="95b76-137">[Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="95b76-138">レポート サーバーの構成と管理 &#40;Reporting Services SharePoint モード&#41;</span><span class="sxs-lookup"><span data-stu-id="95b76-138">Configuration and Administration of a Report Server &#40;Reporting Services SharePoint Mode&#41;</span></span>](../configure-administer-report-server-reporting-services-sharepoint-mode.md)  
  
  
