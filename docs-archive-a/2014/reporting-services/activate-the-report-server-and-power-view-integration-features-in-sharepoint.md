---
title: SharePoint でレポートサーバーと Power View 統合機能をアクティブ化する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af5f544e959c039b0bdb85d63d0b94917254d78a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644346"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a><span data-ttu-id="90277-102">SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化</span><span class="sxs-lookup"><span data-stu-id="90277-102">Activate the Report Server and Power View Integration Features in SharePoint</span></span>
  <span data-ttu-id="90277-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]サイトコレクション機能は、通常、SharePoint 製品用アドインをインストールした後で、既定でアクティブに [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] なります。</span><span class="sxs-lookup"><span data-stu-id="90277-103">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features are usually activated by default after you install the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span> <span data-ttu-id="90277-104">場合によっては、この機能を手動でアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90277-104">In some situations you will need to manually activate the features.</span></span>  
  
 <span data-ttu-id="90277-105">SharePoint 製品のインストール後に SharePoint 2010 製品用の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインをインストールした場合、レポート サーバーの統合機能と Power View の統合機能はルート サイト コレクションでのみアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="90277-105">If you install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010 Products after the installation of the SharePoint product, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="90277-106">他のサイト コレクションについては、この機能を手動でアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90277-106">For other site collections, you will need to manually activate the features.</span></span> <span data-ttu-id="90277-107">たとえば、 **http://[my server name]/sites/[site collection name]** というサイト コレクションが存在する場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のサイト コレクション機能を手動でアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90277-107">For example if you have a site collection of **http://[my server name]/sites/[site collection name]** you will need to manually activate the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features.</span></span>  
  
 <span data-ttu-id="90277-108">ルート サイト コレクションがない場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインによって、次のようなメッセージがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="90277-108">When there is no root site collection, the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in will log a message similar to the following.</span></span>  
  
 <span data-ttu-id="90277-109">"SharePoint Web アプリケーション 80 にはルート サイト コレクションがありません"</span><span class="sxs-lookup"><span data-stu-id="90277-109">"SharePoint web app 80 does not have root site collection"</span></span>  
  
 <span data-ttu-id="90277-110">このメッセージは、"RS_SP_ # .log" という名前のアドインインストールログに記録されます。 # はインクリメントされた数値です。</span><span class="sxs-lookup"><span data-stu-id="90277-110">The message will be found in the add-in installation log, named "RS_SP_#.log" where # is an incrementing number.</span></span> <span data-ttu-id="90277-111">ログファイルは、現在のユーザーの Temp フォルダー (たとえば、C:\Users \\ [user name] \appdata\local\temp)) にあります。アドインのログオプションの詳細については、「sharepoint [2010 および sharepoint 2013&#41;&#40;の Reporting Services アドインのインストールまたはアンインストール](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90277-111">The log file will be found in the current users Temp folder, for example C:\Users\\[user name]\AppData\Local\Temp. For more information on logging options with the add-in, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="90277-112">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="90277-112">In this topic:</span></span>  
  
-   [<span data-ttu-id="90277-113">レポート サーバーと Power View の統合サイト コレクション機能をアクティブ化するには</span><span class="sxs-lookup"><span data-stu-id="90277-113">To Activate the Report Server and Power View Integration Site Collection Features:</span></span>](#bkmk_features)  
  
-   [<span data-ttu-id="90277-114">Reporting Services の全体管理のサイト コレクション機能をアクティブ化または非アクティブ化するには</span><span class="sxs-lookup"><span data-stu-id="90277-114">To Activate or Deactivate Reporting Services Central Administration Site Collection Feature:</span></span>](#bkmk_centraladmin)  
  
##  <a name="to-activate-the-report-server-and-power-view-integration-site-collection-features"></a><a name="bkmk_features"></a><span data-ttu-id="90277-115">レポートサーバーと Power View 統合サイトコレクション機能をアクティブ化するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="90277-115">To Activate the Report Server and Power View Integration Site Collection Features:</span></span>  
  
1.  <span data-ttu-id="90277-116">ブラウザーで、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の機能をアクティブ化するサイトを開きます。</span><span class="sxs-lookup"><span data-stu-id="90277-116">Open your browser to the site where you want the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features active.</span></span>  
  
2.  <span data-ttu-id="90277-117">**[サイトの操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90277-117">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="90277-118">**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90277-118">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="90277-119">[サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90277-119">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="90277-120">一覧で **[レポート サーバーの統合機能]** または **[Power View 統合機能]** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="90277-120">Find **Report Server Integration Feature** or **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="90277-121">**[アクティブ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90277-121">Click **Activate**.</span></span>  
  
 <span data-ttu-id="90277-122">機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90277-122">To deactivate the features, you can use the same procedure, but click **Deactivate** rather than **Activate.**</span></span>  
  
##  <a name="to-activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a><a name="bkmk_centraladmin"></a><span data-ttu-id="90277-123">Reporting Services の中央管理サイトコレクション機能をアクティブ化または非アクティブ化するには:</span><span class="sxs-lookup"><span data-stu-id="90277-123">To Activate or Deactivate Reporting Services Central Administration Site Collection Feature:</span></span>  
  
1.  <span data-ttu-id="90277-124">ブラウザーで SharePoint サーバーの全体管理を開きます。</span><span class="sxs-lookup"><span data-stu-id="90277-124">Open your browser to SharePoint Central Administration.</span></span>  
  
2.  <span data-ttu-id="90277-125">**[サイトの操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90277-125">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="90277-126">**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90277-126">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="90277-127">[サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90277-127">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="90277-128">一覧で **[レポート サーバーの全体管理機能]** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="90277-128">Find **Report Server Central Administration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="90277-129">**[アクティブ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90277-129">Click **Activate**.</span></span>  
  
 <span data-ttu-id="90277-130">機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90277-130">To deactivate the feature, you can use the same procedure, but click **Deactivate** rather than **Activate.**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="90277-131">次の手順</span><span class="sxs-lookup"><span data-stu-id="90277-131">Next Steps</span></span>  
 <span data-ttu-id="90277-132">機能をアクティブ化した後、サーバーの統合を続行できます。</span><span class="sxs-lookup"><span data-stu-id="90277-132">After the feature is activated, you can continue with server integration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90277-133">参照</span><span class="sxs-lookup"><span data-stu-id="90277-133">See Also</span></span>  
 [<span data-ttu-id="90277-134">Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;</span><span class="sxs-lookup"><span data-stu-id="90277-134">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
