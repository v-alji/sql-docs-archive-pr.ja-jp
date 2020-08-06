---
title: SharePoint サーバーの全体管理でレポートサーバーの File Sync 機能をアクティブにする |Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: 55feac69da85c7287ea56f4b8245350dd7e69565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642627"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a><span data-ttu-id="1f379-102">SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする</span><span class="sxs-lookup"><span data-stu-id="1f379-102">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>

<span data-ttu-id="1f379-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバー ファイル同期機能では、SharePoint イベント ハンドラーを利用して、レポート サーバー カタログをドキュメント ライブラリのアイテムと同期します。</span><span class="sxs-lookup"><span data-stu-id="1f379-103">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Server File Sync feature utilizes SharePoint event handlers to synchronize the report server catalog with items in document libraries.</span></span> <span data-ttu-id="1f379-104">この機能は、ユーザーがパブリッシュされたレポート アイテムを SharePoint ドキュメント ライブラリに頻繁に直接アップロードする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1f379-104">This feature is beneficial when users frequently upload published report items directly to SharePoint document libraries.</span></span> <span data-ttu-id="1f379-105">ファイル同期機能がアクティブ化されていない場合でも、コンテンツは同期されますが、頻繁には同期されません。</span><span class="sxs-lookup"><span data-stu-id="1f379-105">If the file Sync feature isn't activated, content will still be synchronized but not as frequently.</span></span>  
  
<span data-ttu-id="1f379-106">ファイル同期機能は、SharePoint 製品用 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] アドインをインストールしてから SharePoint サイトの管理でアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="1f379-106">The File Sync feature can be activated in SharePoint Site Administration after you install the [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span>  
  
<span data-ttu-id="1f379-107">この機能は、サイトごとに手動でアクティブ化および非アクティブ化できますが、サイト コレクション レベルではアクティブ化および非アクティブ化することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f379-107">This feature can be manually activated and deactivated per site but not at the site collection level.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1f379-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="1f379-108">Prerequisites</span></span>  
 <span data-ttu-id="1f379-109">SharePoint 用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f379-109">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in for SharePoint must be installed.</span></span> <span data-ttu-id="1f379-110">アドインがインストールされていない場合、ファイル同期機能はサイト機能の一覧に表示されません。</span><span class="sxs-lookup"><span data-stu-id="1f379-110">If the add-in isn't installed, the file sync feature won't be visible in the site feature list.</span></span>  
  
 <span data-ttu-id="1f379-111">インストールを確認するには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows の **コントロール パネル**でインストール済みアプリケーションの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="1f379-111">To verify installation, view the list of installed applications in [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **Control Panel**.</span></span> <span data-ttu-id="1f379-112">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインがインストールされている場合は、このトピックの手順に従ってレポート サーバー ファイル同期機能をアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="1f379-112">If the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in is installed, follow the instructions in this topic to activate the report server file sync feature.</span></span>  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a><span data-ttu-id="1f379-113">サイトの Reporting Services ファイル同期機能をアクティブ化または非アクティブ化するには</span><span class="sxs-lookup"><span data-stu-id="1f379-113">To activate or deactivate the Reporting Services File Sync feature on a Site</span></span>  
  
1.  <span data-ttu-id="1f379-114">サイトのメインページで、[**サイトの操作**] メニューをクリックし、[**サイトの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f379-114">From the main page of your site, click the **Site Actions** menu and click **Site Settings**.</span></span>  
  
2.  <span data-ttu-id="1f379-115">[**サイトの操作**] で、[サイトの**機能の管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f379-115">In the **Site Actions**, click **Manage Site Features**.</span></span>  
  
3.  <span data-ttu-id="1f379-116">一覧で **[レポート サーバー ファイル同期]** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1f379-116">Find **Report Server File Sync** in the list.</span></span>  
  
4.  <span data-ttu-id="1f379-117">**[アクティブ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f379-117">Click **Activate**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f379-118">レポート サーバー ファイル同期機能を非アクティブ化するには、 **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1f379-118">To deactivate the Report Server file sync feature, you can use the same procedure but click **Deactivate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f379-119">参照</span><span class="sxs-lookup"><span data-stu-id="1f379-119">See Also</span></span>  
 <span data-ttu-id="1f379-120">[レポートパーツ &#40;レポートビルダーと SSRS&#41;のトラブルシューティング](report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1f379-120">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1f379-121">[SharePoint でのレポートサーバーと Power View の統合機能のアクティブ化](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="1f379-121">[Activate the Report Server and Power View Integration Features in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span></span>  
 <span data-ttu-id="1f379-122">[Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="1f379-122">[Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="1f379-123">Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;</span><span class="sxs-lookup"><span data-stu-id="1f379-123">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
