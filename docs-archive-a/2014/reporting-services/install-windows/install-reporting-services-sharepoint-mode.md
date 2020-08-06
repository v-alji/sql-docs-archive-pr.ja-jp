---
title: SharePoint モードのインストールの Reporting Services (SharePoint 2010 および SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c27b6f9fbeebcc896b1a6097cb51e8d2e15924bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632293"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="386b7-102">Reporting Services SharePoint モードのインストール (SharePoint 2010 および SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="386b7-102">Reporting Services SharePoint Mode Installation (SharePoint 2010 and SharePoint 2013)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="386b7-103">SharePoint モードのは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および sharepoint 製品に基づいて、レポートの生成と配信を提供するサーバーコンポーネントのコレクションです [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="386b7-103">in SharePoint mode is a collection of server components that provide report generation and delivery, based on [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint products.</span></span>  
  
 <span data-ttu-id="386b7-104">SharePoint モードで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を実行すると、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] とデータの警告機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="386b7-104">Running [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode provides the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] and data alerting features.</span></span> <span data-ttu-id="386b7-105">SharePoint モードの機能の詳細については、 [Reporting Services レポートサーバー](../reporting-services-report-server.md)の「機能のサポートと動作の違い」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="386b7-105">For more information regarding features in SharePoint mode, see the section "Feature Support and Behavior Differences by Server Mode" in [Reporting Services Report Server](../reporting-services-report-server.md)</span></span>  
  
 <span data-ttu-id="386b7-106">SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に必要な基本的なインストールは 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="386b7-106">There are two fundamental installations needed for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode:</span></span>  
  
|<span data-ttu-id="386b7-107">インストール</span><span class="sxs-lookup"><span data-stu-id="386b7-107">Installation</span></span>|<span data-ttu-id="386b7-108">説明</span><span class="sxs-lookup"><span data-stu-id="386b7-108">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="386b7-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 製品用アドイン。</span><span class="sxs-lookup"><span data-stu-id="386b7-109">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>|<span data-ttu-id="386b7-110">アドインでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ユーザー インターフェイス (UI) ページと機能を SharePoint Web フロントエンド サーバーにインストールします。</span><span class="sxs-lookup"><span data-stu-id="386b7-110">The add-in installs the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] user interface (UI) pages and features on a SharePoint web front-end server.</span></span> <span data-ttu-id="386b7-111">UI 機能には、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SharePoint サーバーの全体管理の管理ページ、SharePoint ドキュメント ライブラリ内で使用される機能ページ、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ警告ページが含まれます。</span><span class="sxs-lookup"><span data-stu-id="386b7-111">The UI features include [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], administration pages in SharePoint Central Administration, feature pages used within SharePoint document libraries, and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Data Alerting pages.</span></span>|  
|<span data-ttu-id="386b7-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードでインストールされたレポートサーバー</span><span class="sxs-lookup"><span data-stu-id="386b7-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server installed in SharePoint Mode</span></span>|<span data-ttu-id="386b7-113">レポート サーバーは、データとレポートの処理と表示に加え、サブスクリプションとデータ警告処理も処理します。</span><span class="sxs-lookup"><span data-stu-id="386b7-113">The report server handles the data and report processing and rendering as well subscription and Data Alert processing.</span></span> <span data-ttu-id="386b7-114">SharePoint モードのレポート サーバーは、SharePoint 共有サービスとして構築、インストールされています。</span><span class="sxs-lookup"><span data-stu-id="386b7-114">The SharePoint mode report server is architected and installed as a SharePoint Shared Service.</span></span>|  
  
 <span data-ttu-id="386b7-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールするには、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール メディアを使用します。</span><span class="sxs-lookup"><span data-stu-id="386b7-115">To install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media.</span></span>  
  
 <span data-ttu-id="386b7-116">高度な展開シナリオの手順については、「[配置のチェックリスト: Reporting Services、Power View、および PowerPivot for SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)および[配置のチェックリスト: 既存の SharePoint ファームへの Reporting Services のインストール](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="386b7-116">For instructions on advanced deployment scenarios, see [Deployment Checklist: Reporting Services, Power View, and PowerPivot for SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) and [Deployment Checklist: Install Reporting Services into an Existing SharePoint Farm](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="386b7-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="386b7-117">In This Section</span></span>  
 [<span data-ttu-id="386b7-118">サポートされている SharePoint と Reporting Services Server およびアドイン &#40;SQL Server 2014 の組み合わせ&#41;</span><span class="sxs-lookup"><span data-stu-id="386b7-118">Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2014&#41;</span></span>](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [<span data-ttu-id="386b7-119">SharePoint 2013 用 Reporting Services の SharePoint モードのインストール</span><span class="sxs-lookup"><span data-stu-id="386b7-119">Install Reporting Services SharePoint Mode for SharePoint 2013</span></span>](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [<span data-ttu-id="386b7-120">SharePoint 2010 用 Reporting Services SharePoint モードのインストール</span><span class="sxs-lookup"><span data-stu-id="386b7-120">Install Reporting Services SharePoint Mode for SharePoint 2010</span></span>](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [<span data-ttu-id="386b7-121">Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;</span><span class="sxs-lookup"><span data-stu-id="386b7-121">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [<span data-ttu-id="386b7-122">SharePoint 製品用 Reporting Services アドインの検索場所</span><span class="sxs-lookup"><span data-stu-id="386b7-122">Where to find the Reporting Services add-in for SharePoint Products</span></span>](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [<span data-ttu-id="386b7-123">ファームへのレポート サーバーの追加 &#40;SSRS スケールアウト&#41;</span><span class="sxs-lookup"><span data-stu-id="386b7-123">Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;</span></span>](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [<span data-ttu-id="386b7-124">ファームへの Reporting Services Web フロントエンドの追加</span><span class="sxs-lookup"><span data-stu-id="386b7-124">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [<span data-ttu-id="386b7-125">Reporting Services サービス アプリケーションの電子メールの構成 (SharePoint 2010 および SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="386b7-125">Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [<span data-ttu-id="386b7-126">SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備</span><span class="sxs-lookup"><span data-stu-id="386b7-126">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [<span data-ttu-id="386b7-127">Windows トークンサービスに対するクレーム &#40;C2WTS&#41; と Reporting Services</span><span class="sxs-lookup"><span data-stu-id="386b7-127">Claims to Windows Token Service &#40;C2WTS&#41; and Reporting Services</span></span>](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="386b7-128">参照</span><span class="sxs-lookup"><span data-stu-id="386b7-128">See Also</span></span>  
 <span data-ttu-id="386b7-129">[データ警告のアーキテクチャとワークフロー](../reporting-services-data-alerts.md#AlertingWF) </span><span class="sxs-lookup"><span data-stu-id="386b7-129">[Data Alerts Architecture and Workflow](../reporting-services-data-alerts.md#AlertingWF) </span></span>  
 [<span data-ttu-id="386b7-130">警告管理者用のデータ警告マネージャー</span><span class="sxs-lookup"><span data-stu-id="386b7-130">Data Alert Manager for Alerting Administrators</span></span>](../data-alert-manager-for-alerting-administrators.md)  
  
  
