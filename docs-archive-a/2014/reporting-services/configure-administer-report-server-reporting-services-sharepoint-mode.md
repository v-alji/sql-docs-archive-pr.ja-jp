---
title: レポートサーバーの構成と管理 (SharePoint モード Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 846e86d0-fbbb-426c-97f9-f179cd42b390
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ce7c1f524eec4785ddbc25d95c641d070ecbf408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739559"
---
# <a name="configuration-and-administration-of-a-report-server-reporting-services-sharepoint-mode"></a><span data-ttu-id="8f887-102">レポート サーバーの構成と管理 (Reporting Services SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="8f887-102">Configuration and Administration of a Report Server (Reporting Services SharePoint Mode)</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="8f887-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] は、サーバーベースのレポートプラットフォームであり、組織のレポートの作成、展開、管理に役立つツールやサービスを提供します。また、レポート機能の拡張とカスタマイズを可能にするプログラミング機能も用意されています。</span><span class="sxs-lookup"><span data-stu-id="8f887-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] is a server-based reporting platform that provides a full range of ready-to-use tools and services to help you create, deploy, and manage reports for your organization, as well as programming features that enable you to extend and customize your reporting functionality.</span></span> <span data-ttu-id="8f887-104">レポート環境を SharePoint 製品と統合すると、SharePoint サイトによって提供されるコラボレーション環境を使用するメリットを実感できます。</span><span class="sxs-lookup"><span data-stu-id="8f887-104">You can integrate your reporting environment with a SharePoint product to experience the benefits of using the collaborative environment provided by SharePoint sites.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f887-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8f887-105">In this section</span></span>  
 <span data-ttu-id="8f887-106">次のセクションでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 環境と SharePoint 製品またはテクノロジとの統合に関する概念、配置シナリオ、手順などについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8f887-106">Use the following sections to help you understand concepts, deployment scenarios, procedures, and more for integrating your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] environment with a SharePoint product or technology:</span></span>  
  
-   <span data-ttu-id="8f887-107">SharePoint ドキュメント ライブラリのメニュー オプション</span><span class="sxs-lookup"><span data-stu-id="8f887-107">Menu options in a SharePoint document library</span></span>  
  
    -   [<span data-ttu-id="8f887-108">SharePoint ユーザー用のデータ警告マネージャー</span><span class="sxs-lookup"><span data-stu-id="8f887-108">Data Alert Manager for SharePoint Users</span></span>](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md)  
  
    -   [<span data-ttu-id="8f887-109">SharePoint モード レポート サーバーのサブスクリプションの作成と管理</span><span class="sxs-lookup"><span data-stu-id="8f887-109">Create and Manage Subscriptions for SharePoint Mode Report Servers</span></span>](subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
  
    -   [<span data-ttu-id="8f887-110">レポート データ ソース内の資格情報を SharePoint サイトから更新する</span><span class="sxs-lookup"><span data-stu-id="8f887-110">Update Credentials in Report Data Sources from a SharePoint Site</span></span>](report-data/update-credentials-in-report-data-sources-from-a-sharepoint-site.md)  
  
    -   [<span data-ttu-id="8f887-111">共有データセットを管理する</span><span class="sxs-lookup"><span data-stu-id="8f887-111">Manage Shared Datasets</span></span>](report-data/manage-shared-datasets.md)  
  
    -   [<span data-ttu-id="8f887-112">パブリッシュ済みレポートのパラメーターの設定 &#40;Reporting Services の SharePoint 統合モード&#41;</span><span class="sxs-lookup"><span data-stu-id="8f887-112">Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)  
  
    -   [<span data-ttu-id="8f887-113">処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;</span><span class="sxs-lookup"><span data-stu-id="8f887-113">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
    -   <span data-ttu-id="8f887-114">[[キャッシュ更新オプション] &#40;レポート マネージャー&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="8f887-114">[Cache Refresh Options &#40;Report Manager&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md)</span></span>  
  
-   [<span data-ttu-id="8f887-115">Reporting Services サイトコレクションの機能</span><span class="sxs-lookup"><span data-stu-id="8f887-115">Reporting Services Site Collection Features</span></span>](../../2014/reporting-services/reporting-services-site-collection-features.md)  
  
-   [<span data-ttu-id="8f887-116">SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化</span><span class="sxs-lookup"><span data-stu-id="8f887-116">Activate the Report Server and Power View Integration Features in SharePoint</span></span>](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  
  
-   [<span data-ttu-id="8f887-117">Reporting Services のサイト設定とサイト機能 &#40;SharePoint モード&#41;</span><span class="sxs-lookup"><span data-stu-id="8f887-117">Reporting Services Site Settings and Site Features&#40;SharePoint Mode&#41;</span></span>](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)  
  
-   [<span data-ttu-id="8f887-118">SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする</span><span class="sxs-lookup"><span data-stu-id="8f887-118">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
-   [<span data-ttu-id="8f887-119">SharePoint 統合モードの &#40;Reporting Services ライブラリにレポートサーバーのコンテンツの種類を追加&#41;</span><span class="sxs-lookup"><span data-stu-id="8f887-119">Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
-   [<span data-ttu-id="8f887-120">レポート ビューアーでのローカル モードと接続モードのレポート &#40;Reporting Services の SharePoint モード&#41;</span><span class="sxs-lookup"><span data-stu-id="8f887-120">Local Mode vs. Connected Mode Reports in the Report Viewer &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)  
  
-   [<span data-ttu-id="8f887-121">SharePoint ライブラリへのドキュメントのアップロード (Reporting Services の SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="8f887-121">Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../../2014/reporting-services/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
-   [<span data-ttu-id="8f887-122">処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;</span><span class="sxs-lookup"><span data-stu-id="8f887-122">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
 <span data-ttu-id="8f887-123">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] に関する一般的な情報については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックの「[Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f887-123">For more general information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="8f887-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のコンポーネント、ツール、およびリソースについては、 [SQL Server オンライン ブック](../index.yml)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f887-124">For information about other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components, tools, and resources, see [SQL Server Books Online](../index.yml).</span></span>  
  
  
