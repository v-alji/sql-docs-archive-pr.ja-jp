---
title: SharePoint ライブラリへの共有データ ソースのパブリッシュ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], publishing to a SharePoint library
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77ee25535ccb98638ae02ca64e3bcbfc88291c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712722"
---
# <a name="publish-a-shared-data-source-to-a-sharepoint-library"></a><span data-ttu-id="17297-102">SharePoint ライブラリへの共有データ ソースのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="17297-102">Publish a Shared Data Source to a SharePoint Library</span></span>
  <span data-ttu-id="17297-103">SharePoint 統合モードで実行されているレポート サーバーに共有データ ソースをパブリッシュするには、レポート デザイナーでレポート プロジェクトのプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17297-103">To publish a shared data source to a report server that is running in SharePoint integrated mode, you must set the report project properties in Report Designer.</span></span> <span data-ttu-id="17297-104">プロジェクトのプロパティでは、サーバー、レポート、および共有データ ソースへの参照はすべて、完全修飾 URL で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17297-104">In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.</span></span>  
  
 <span data-ttu-id="17297-105">また、SharePoint サイトの **メンバー** 権限または **所有者** 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="17297-105">You must have **Member** or **Owner** permission on the SharePoint site.</span></span> <span data-ttu-id="17297-106">詳細については、「 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17297-106">For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-publish-a-shared-data-source-to-a-sharepoint-site"></a><span data-ttu-id="17297-107">SharePoint サイトに共有データ ソースをパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="17297-107">To publish a shared data source to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="17297-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、既存または新規のレポート サーバー プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="17297-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open your existing or new Report Server project.</span></span>  
  
2.  <span data-ttu-id="17297-109">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17297-109">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="17297-110">[ _\<project>_ **プロパティページ**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17297-110">The _\<project>_**Property Pages** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="17297-111">SharePoint サイトへのパブリッシュに使用する **[構成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17297-111">Choose the **Configuration** you use to publish to a SharePoint site.</span></span>  
  
4.  <span data-ttu-id="17297-112">プロジェクトの共有データ ソースをパブリッシュし、以前にパブリッシュされた共有データ ソースを上書きするには、 **[OverwriteDataSources]** を **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="17297-112">If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.</span></span>  
  
5.  <span data-ttu-id="17297-113">(省略可) **[TargetDataSourceFolder]** には、SharePoint ライブラリまたはライブラリ フォルダーへの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="17297-113">(Optional) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder.</span></span> <span data-ttu-id="17297-114">たとえば、 *http://TestServer/TestSite/Documents/DataSources* です。</span><span class="sxs-lookup"><span data-stu-id="17297-114">For example, *http://TestServer/TestSite/Documents/DataSources*.</span></span>  
  
     <span data-ttu-id="17297-115">値を指定しない場合は、 **[TargetReportFolder]** の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="17297-115">If you do not specify a value, the **TargetReportFolder** value is used.</span></span>  
  
6.  <span data-ttu-id="17297-116">**[TargetReportFolder]** に、ライブラリまたはライブラリ フォルダーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="17297-116">For **TargetReportFolder**, type a URL to a library or library folder.</span></span> <span data-ttu-id="17297-117">たとえば、「http:*//TestServer/TestSite/Documents/Reports*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="17297-117">For example, http:*//TestServer/TestSite/Documents/Reports*.</span></span>  
  
7.  <span data-ttu-id="17297-118">**[TargetServerURL]** に、SharePoint トップレベル サイトまたはサブサイトの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="17297-118">For **TargetServerURL**, type a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="17297-119">サイトを指定しなかった場合は、既定のトップレベル サイトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="17297-119">If you do not specify a site, the default top-level site is used.</span></span> <span data-ttu-id="17297-120">たとえば、「http://*servername*」、「http://*servername*/*site*」、または「http://*servername*/*site*/*subsite*」のように指定します。</span><span class="sxs-lookup"><span data-stu-id="17297-120">For example, http://*servername*, http://*servername*/*site*, or http://*servername*/*site*/*subsite*.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="17297-121">ソリューション エクスプローラーで、パブリッシュする共有データ ソースを右クリックし、 **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17297-121">In Solution Explorer, right-click the shared data source you want to publish, and click **Deploy**.</span></span> <span data-ttu-id="17297-122">これで、 **[TargetDataSourceFolder]** で指定した場所にデータ ソースがパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="17297-122">The data source is published to the location specified in **TargetDataSourceFolder**.</span></span> <span data-ttu-id="17297-123">配置エラーは出力ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="17297-123">Deployment errors appear in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="17297-124">共有データ ソースを SharePoint サイトにパブリッシュすると、ファイル名拡張子が .rsds に変更されます。</span><span class="sxs-lookup"><span data-stu-id="17297-124">After you publish a shared data source to a SharePoint site, the file name extension is changed to .rsds.</span></span> <span data-ttu-id="17297-125">共有データ ソースの編集と管理は、SharePoint サイト上で直接行うことができます。</span><span class="sxs-lookup"><span data-stu-id="17297-125">You can edit and manage a shared data source directly on the SharePoint site.</span></span> <span data-ttu-id="17297-126">詳細については、「[共有データ ソースを作成および管理する &#40;Reporting Services の SharePoint 統合モード&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17297-126">For more information, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17297-127">参照</span><span class="sxs-lookup"><span data-stu-id="17297-127">See Also</span></span>  
 <span data-ttu-id="17297-128">[SharePoint ライブラリへのレポートのパブリッシュ](publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="17297-128">[Publish a Report to a SharePoint Library](publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="17297-129">[SharePoint モードのレポートサーバー上のパブリッシュされたレポートアイテムの URL の例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="17297-129">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="17297-130">[[プロジェクトプロパティページ] ダイアログボックス](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="17297-130">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="17297-131">[展開プロパティを設定 &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="17297-131">[Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span></span>  
 <span data-ttu-id="17297-132">[レポートサーバーへのレポートのパブリッシュ](publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="17297-132">[Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md) </span></span>  
 [<span data-ttu-id="17297-133">レポートで Office Data Connection &#40;.odc&#41; を使用する &#40;Reporting Services の SharePoint 統合モード&#41;</span><span class="sxs-lookup"><span data-stu-id="17297-133">Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
