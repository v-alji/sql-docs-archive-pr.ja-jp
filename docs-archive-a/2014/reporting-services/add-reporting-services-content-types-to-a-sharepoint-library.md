---
title: レポートサーバーのコンテンツの種類をライブラリに追加する (SharePoint 統合モードの Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ac9136c8-9ef4-484c-8e9d-05008a186db5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e0ee56c235a54920fba5389a61f300eeaa65329
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739606"
---
# <a name="add-report-server-content-types-to-a-library-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="fa7a9-102">レポート サーバー コンテンツの種類をライブラリに追加する (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-102">Add Report Server Content Types to a Library (Reporting Services in SharePoint Integrated Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="fa7a9-103">では、共有データ ソース (.rsds) ファイル、レポート モデル (.smdl)、レポート ビルダーのレポート定義 (.rdl) ファイルを管理する際に使用するコンテンツの種類が、あらかじめ定義されています。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-103">provides predefined SharePoint content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="fa7a9-104">コンテンツの種類として、 **[レポート ビルダー レポート]**、 **[レポート モデル]**、および **[レポート データ ソース]** をライブラリに追加すると、 **[新規作成]** コマンドが有効になり、その種類のドキュメントを新規作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-104">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span>  
  
 <span data-ttu-id="fa7a9-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="fa7a9-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
 <span data-ttu-id="fa7a9-106">コンテンツの種類をライブラリに追加するには、サイトの管理者であるか、またはフル コントロール レベルの権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-106">To add content types to a library, you must be a site administrator or have Full Control level of permission.</span></span>  
  
 <span data-ttu-id="fa7a9-107">次の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ビジネス インテリジェンス センター **サイト テンプレートから作成された既存のサイト コレクションのすべてのドキュメント ライブラリで** コンテンツの種類およびコンテンツの種類の管理が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-107">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types and content type management will automatically be enabled in all document libraries for existing site collections created from the following **Business Intelligence Center** site template.</span></span>  
  
 <span data-ttu-id="fa7a9-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 統合後に作成されたサイトでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のコンテンツの種類が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-108">Sites created after the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integration will not have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types enabled.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="fa7a9-109">以前にライブラリのコンテンツの種類を構成して **いない** 場合は、コンテンツの種類の管理を有効にしてから、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のコンテンツの種類を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-109">If you have **not** previously configured content types for a library, first enable management of content types, then enable the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types.</span></span> <span data-ttu-id="fa7a9-110">単一のドキュメント ライブラリでコンテンツの種類の管理を有効にするための手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-110">See the procedures on enabling content type management in a single document library.</span></span>  
  
 <span data-ttu-id="fa7a9-111">**短いビデオ:** [(SSRS) Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w)。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-111">**Short video:** [(SSRS) Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w).</span></span>  
  
 <span data-ttu-id="fa7a9-112">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="fa7a9-112">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="fa7a9-113">既存の BI センターのすべてのドキュメントライブラリでコンテンツの種類を有効にする</span><span class="sxs-lookup"><span data-stu-id="fa7a9-113">Enable content types in all document libraries in an existing BI center</span></span>](#bkmk_enable_all)  
  
-   [<span data-ttu-id="fa7a9-114">1 つのドキュメント ライブラリでコンテンツの種類の管理を有効にするには (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-114">To enable content type management for a single document library (SharePoint 2013)</span></span>](#bkmk_enable_content_management)  
  
-   [<span data-ttu-id="fa7a9-115">コンテンツの種類 Reporting Services を追加するには (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-115">To add Reporting Services content types (SharePoint 2013)</span></span>](#bkmk_add_single)  
  
-   [<span data-ttu-id="fa7a9-116">1 つのドキュメント ライブラリでコンテンツの種類の管理を有効にするには (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-116">To enable content type management for a single document library (SharePoint 2010)</span></span>](#bkmk_enable_content_management_2010)  
  
-   [<span data-ttu-id="fa7a9-117">レポート サーバーのコンテンツの種類を追加するには (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-117">To add report server content types (SharePoint 2010)</span></span>](#bkmk_add_single_2010)  
  
-   [<span data-ttu-id="fa7a9-118">複数の BI サイトのコンテンツの種類とコンテンツ管理を有効にするには</span><span class="sxs-lookup"><span data-stu-id="fa7a9-118">To enable Content types and content management for multiple BI sites</span></span>](#bkmk_enable_multiple_sites)  
  
##  <a name="enable-content-types-in-all-document-libraries-in-an-existing-bi-center"></a><a name="bkmk_enable_all"></a> <span data-ttu-id="fa7a9-119">既存のビジネス インテリジェント センターのすべてのドキュメント ライブラリでコンテンツの種類を有効にする</span><span class="sxs-lookup"><span data-stu-id="fa7a9-119">Enable content types in all document libraries in an existing BI center</span></span>  
  
1.  <span data-ttu-id="fa7a9-120">既存の **ビジネス インテリジェント センター** サイトのすべてのドキュメント ライブラリでコンテンツの種類とコンテンツ管理を有効にするには、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 統合機能を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-120">To enable the content types and content management in all document libraries in an existing **Business Intelligence Center** site, you can toggle the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integration feature.</span></span>  
  
2.  <span data-ttu-id="fa7a9-121">**[サイトの設定]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-121">Go to **Site settings**.</span></span>  
  
    -   <span data-ttu-id="fa7a9-122">SharePoint 2013 の場合、 **[設定]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-122">In SharePoint 2013, click the **Settings** icon.</span></span> <span data-ttu-id="fa7a9-123">![SharePoint の設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-123">![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings")</span></span>  
  
    -   <span data-ttu-id="fa7a9-124">SharePoint 2010 の場合、 **[サイトの操作]** をクリックし、 **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-124">In SharePoint 2010, click **Site Actions**, then click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="fa7a9-125">[**サイトコレクションの機能**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-125">Click **Site collection features**.</span></span>  
  
4.  <span data-ttu-id="fa7a9-126">**[レポート サーバーの統合機能]** を見つけて **[非アクティブ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-126">Find the **Report Server Integration Feature** and click **Deactivate**.</span></span>  
  
     <span data-ttu-id="fa7a9-127">![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-127">![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")</span></span>  
  
5.  <span data-ttu-id="fa7a9-128">ブラウザーを更新します。 **[レポート サーバーの統合機能]** の **[アクティブ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-128">Refresh the browser then click **Activate** for the **Report Server Integration Feature**.</span></span>  
  
    <span data-ttu-id="fa7a9-129">![非アクティブ化](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-129">![Deactivate](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")</span></span>  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2013"></a><a name="bkmk_enable_content_management"></a><span data-ttu-id="fa7a9-130">1つのドキュメントライブラリに対してコンテンツの種類の管理を有効にするには (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-130">To enable content type management for a single document library (SharePoint 2013)</span></span>  
  
1.  <span data-ttu-id="fa7a9-131">複数のコンテンツの種類を有効にする対象ライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-131">Open the library for which you want to enable multiple content types.</span></span>  
  
2.  <span data-ttu-id="fa7a9-132">リボンで、 **[ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-132">Click **Library** in the ribbon.</span></span>  
  
     <span data-ttu-id="fa7a9-133">![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-133">![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")</span></span>  
  
3.  <span data-ttu-id="fa7a9-134">**[ライブラリ]** リボンで、 **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-134">On the **Library** ribbon, click **Library Settings**.</span></span> <span data-ttu-id="fa7a9-135">**[ライブラリの設定]** が表示されない場合やボタンが無効になっている場合は、コンテンツの種類を含むライブラリ設定を構成する権限がありません。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-135">If you do not see **Library Settings** or the button is disabled, you do not have permission to configure library settings, including content types.</span></span>  
  
     <span data-ttu-id="fa7a9-136">![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-136">![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")</span></span>  
  
4.  <span data-ttu-id="fa7a9-137">**[全般設定]** セクションの **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-137">In the **General Settings** section, click **Advanced settings**.</span></span>  
  
     <span data-ttu-id="fa7a9-138">![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-138">![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")</span></span>  
  
5.  <span data-ttu-id="fa7a9-139">コンテンツの種類を管理できるようにするには、 **[コンテンツ タイプ]** の **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-139">In the **Content Types** section, select **Yes** to allow management of content types.</span></span>  
  
6.  <span data-ttu-id="fa7a9-140">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-140">Click **OK**.</span></span>  
  
##  <a name="to-add-reporting-services-content-types-sharepoint-2013"></a><a name="bkmk_add_single"></a> <span data-ttu-id="fa7a9-141">Reporting Services のコンテンツの種類を追加するには (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-141">To add Reporting Services content types (SharePoint 2013)</span></span>  
  
1.  <span data-ttu-id="fa7a9-142">Reporting Services のコンテンツの種類を追加する対象のライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-142">Open the library for which you want to add Reporting Services content types.</span></span>  
  
2.  <span data-ttu-id="fa7a9-143">リボンで、 **[ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-143">On the ribbon, click **Library**.</span></span>  
  
3.  <span data-ttu-id="fa7a9-144">**[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-144">Click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="fa7a9-145">**[コンテンツ タイプ]** の **[既存のサイト コンテンツ タイプから追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-145">Under **Content Types**, click **Add from existing site content types**.</span></span>  
  
5.  <span data-ttu-id="fa7a9-146">**[サイト コンテンツ タイプの選択元]** で、 **[SQL Server Reporting Services のコンテンツの種類]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-146">In **Select site content types from**, select **SQL Server Reporting Services Content Types**.</span></span>  
  
6.  <span data-ttu-id="fa7a9-147">**[利用可能なサイト コンテンツ タイプ]** ボックスの一覧で **[レポート ビルダー]** をクリックし、 **[追加]** をクリックして、選択したコンテンツ タイプを **[追加するコンテンツ タイプ]** ボックスの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-147">In the **Available Site Content Types** list, click **Report Builder**, and then click **Add** to move the selected content type to the **Content types to add** list.</span></span>  
  
7.  <span data-ttu-id="fa7a9-148">コンテンツの種類として **[レポート モデル]** および **[レポート データ ソース]** を追加するには、前の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-148">To add **Report Model** and **Report Data Source** content types, repeat the previous step.</span></span>  
  
8.  <span data-ttu-id="fa7a9-149">コンテンツの種類の追加操作が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-149">When you finish adding content types, click **OK**.</span></span>  
  
9. > [!NOTE]  
    >  <span data-ttu-id="fa7a9-150">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] コンテンツの種類のグループ **[SQL Server Reporting Services のコンテンツの種類]** が **[コンテンツ タイプの追加]** ページに表示されない場合は、次のいずれかの状況に該当しています。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-150">If the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content type group **SQL Server Reporting Services Content Types** is not visible on the **Add Content Types** page, one of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="fa7a9-151">SharePoint 製品用の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインがインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-151">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products has not been installed.</span></span> <span data-ttu-id="fa7a9-152">詳細については、「sharepoint [&#40;sharepoint 2010 および sharepoint 2013&#41;の Reporting Services アドインのインストールまたはアンインストール](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-152">For more information, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span> <span data-ttu-id="fa7a9-153">このトピックには、アドインのインストール方法、アドインのファイルのみのインストールをステップ実行して問題に対処する方法が記載されています。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-153">The topic includes information on installing the add-in and stepping through a files only installation of the add-in to work around issues.</span></span>  
  
    -   <span data-ttu-id="fa7a9-154">アドインはインストールされていますが、サイト コレクション機能 **[レポート サーバーの統合機能]** がアクティブになっていません。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-154">The add-in is installed but the site collection feature **Report Server Integration Feature** is not active.</span></span> <span data-ttu-id="fa7a9-155">**[サイトの設定]** でサイト コレクション機能を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-155">Verify the site collection feature in **Site Settings**.</span></span>  
  
    -   <span data-ttu-id="fa7a9-156">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のすべてのコンテンツの種類が既にライブラリに追加されています。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-156">All of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types have already been added to the library.</span></span> <span data-ttu-id="fa7a9-157">すべてのコンテンツの種類がライブラリの一部である場合、このグループは **[コンテンツ タイプの追加]** ページから削除されます。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-157">If all the content types are part of a library, then the group is removed from the **Add Content Types** page.</span></span> <span data-ttu-id="fa7a9-158">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の 1 つまたは複数のコンテンツの種類を削除すると、 **[SQL Server Reporting Services のコンテンツの種類]** グループが **[コンテンツ タイプの追加]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-158">If you delete one or more of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types, then the group **SQL Server Reporting Services Content Types** will be visible on the **Add Content Types** page.</span></span>  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2010"></a><a name="bkmk_enable_content_management_2010"></a><span data-ttu-id="fa7a9-159">1つのドキュメントライブラリに対してコンテンツの種類の管理を有効にするには (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-159">To enable content type management for a single document library (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="fa7a9-160">複数のコンテンツの種類を有効にする対象ライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-160">Open the library for which you want to enable multiple content types.</span></span> <span data-ttu-id="fa7a9-161">ライブラリ メニュー バーに表示されるメニューは、 **[新規作成]**、 **[アップロード]**、 **[アクション]**、および **[設定]** です。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-161">On the library menu bar, you should see the following menus: **New**, **Upload**, **Actions**, and **Settings**.</span></span> <span data-ttu-id="fa7a9-162">コンテンツの種類を追加する権限を持っていない場合は、 **[設定]** が表示されません。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-162">If you do not see **Settings**, you do not have permission to add a content type.</span></span>  
  
2.  <span data-ttu-id="fa7a9-163">**[ライブラリ ツール]** リボンで、 **[ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-163">On the **Library Tools** ribbon, click **Library**.</span></span>  
  
     <span data-ttu-id="fa7a9-164">![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-164">![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")</span></span>  
  
3.  <span data-ttu-id="fa7a9-165">**[設定]** リボン グループの **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-165">On the **Settings** ribbon group, click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="fa7a9-166">**[全般設定]** の **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-166">Under **General Settings**, click **Advanced settings**.</span></span>  
  
5.  <span data-ttu-id="fa7a9-167">コンテンツの種類を管理できるようにするには、 **[コンテンツ タイプ]** の **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-167">In the **Content Types** section, select **Yes** to allow management of content types.</span></span>  
  
6.  <span data-ttu-id="fa7a9-168">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-168">Click **OK**.</span></span>  
  
##  <a name="to-add-report-server-content-types-sharepoint-2010"></a><a name="bkmk_add_single_2010"></a><span data-ttu-id="fa7a9-169">レポートサーバーのコンテンツの種類を追加するには (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="fa7a9-169">To add report server content types (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="fa7a9-170">Reporting Services のコンテンツの種類を追加する対象のライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-170">Open the library for which you want to add Reporting Services content types.</span></span>  
  
2.  <span data-ttu-id="fa7a9-171">**[ライブラリ ツール]** リボン タブで **[ライブラリ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-171">On the **Library Tools** ribbon tabs, click the **Library tab**.</span></span>  
  
3.  <span data-ttu-id="fa7a9-172">**[設定]** リボン グループの **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-172">On the **Settings** ribbon group, click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="fa7a9-173">**[コンテンツ タイプ]** の **[既存のサイト コンテンツ タイプから追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-173">Under **Content Types**, click **Add from existing site content types**.</span></span>  
  
5.  <span data-ttu-id="fa7a9-174">**[コンテンツ タイプの選択]** セクションの **[サイト コンテンツ タイプの選択元]** で、矢印をクリックして **[SQL Server Reporting Services のコンテンツの種類]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-174">In the **Select Content Types** section, in **Select site content types from**, click the arrow to select **SQL Server Reporting Services Content Types**.</span></span>  
  
6.  <span data-ttu-id="fa7a9-175">**[利用可能なサイト コンテンツ タイプ]** ボックスの一覧で **[レポート ビルダー]** をクリックし、 **[追加]** をクリックして、選択したコンテンツ タイプを **[追加するコンテンツ タイプ]** ボックスの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-175">In the **Available Site Content Types** list, click **Report Builder**, and then click **Add** to move the selected content type to the **Content types to add** list.</span></span>  
  
7.  <span data-ttu-id="fa7a9-176">コンテンツの種類として **[レポート モデル]** および **[レポート データ ソース]** を追加するには、前の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-176">To add **Report Model** and **Report Data Source** content types, repeat the previous step.</span></span>  
  
8.  <span data-ttu-id="fa7a9-177">コンテンツの種類の追加操作が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-177">When you finish adding content types, click **OK**.</span></span>  
  
##  <a name="to-enable-content-types-and-content-management-for-multiple-bi-sites"></a><a name="bkmk_enable_multiple_sites"></a><span data-ttu-id="fa7a9-178">複数の BI サイトのコンテンツの種類とコンテンツ管理を有効にするには</span><span class="sxs-lookup"><span data-stu-id="fa7a9-178">To enable Content types and content management for multiple BI sites</span></span>  
  
1.  <span data-ttu-id="fa7a9-179">SQL Server Reporting Services 2008 および 2008 R2 レポート サーバーの場合は、複数のビジネス インテリジェンス センター サイトのコンテンツの種類とコンテンツ管理を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-179">For SQL Server Reporting Services 2008 and 2008 R2 report servers, you can enable content types and content management for multiple Business Intelligence Center sites:</span></span>  
  
2.  <span data-ttu-id="fa7a9-180">SharePoint サーバーの全体管理で **[アプリケーションの全般設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-180">In SharePoint Central Administration, click **General Applications settings**.</span></span> <span data-ttu-id="fa7a9-181">**[SQL Server Reporting Services (2008 および 2008 R2)]** セクションで、 **[Reporting Services 統合]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-181">In the **SQL Server Reporting Services (2008 and 2008 R2)** section, click **Reporting Services Integration**.</span></span>  
  
     <span data-ttu-id="fa7a9-182">![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-182">![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")</span></span>  
  
3.  <span data-ttu-id="fa7a9-183">**[すべての既存のサイト コレクションで機能をアクティブ化する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-183">Click **Activate feature in all exciting site collections**.</span></span>  
  
     <span data-ttu-id="fa7a9-184">![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")</span><span class="sxs-lookup"><span data-stu-id="fa7a9-184">![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")</span></span>  
  
4.  <span data-ttu-id="fa7a9-185">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa7a9-185">Click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7a9-186">参照</span><span class="sxs-lookup"><span data-stu-id="fa7a9-186">See Also</span></span>  
 <span data-ttu-id="fa7a9-187">[レポートサーバーアイテムの SharePoint サイトおよびリスト権限のリファレンス](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="fa7a9-187">[SharePoint Site and List Permission Reference for Report Server Items](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span></span>  
 [<span data-ttu-id="fa7a9-188">&#40;レポートビルダーを開始レポートビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="fa7a9-188">Start Report Builder &#40;Report Builder&#41;</span></span>](report-builder/start-report-builder.md)  
  
  
