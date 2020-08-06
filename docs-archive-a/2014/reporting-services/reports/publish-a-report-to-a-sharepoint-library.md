---
title: SharePoint ライブラリへのレポートのパブリッシュ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23b74ffb04bf1e13523dcf6ec5d774089d80f73b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712726"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a><span data-ttu-id="b59db-102">SharePoint ライブラリへのレポートのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="b59db-102">Publish a Report to a SharePoint Library</span></span>
  <span data-ttu-id="b59db-103">SharePoint 統合用に構成されている SharePoint サイトにレポートをパブリッシュするには、レポート デザイナーでレポート プロジェクトのプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b59db-103">To publish a report to a SharePoint site configured for SharePoint integration, you must set the project properties in Report Designer.</span></span> <span data-ttu-id="b59db-104">プロジェクトのプロパティでは、サーバー、レポート、および共有データ ソースへの参照はすべて、完全修飾 URL で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b59db-104">In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.</span></span> <span data-ttu-id="b59db-105">レポート定義では、サブレポートや詳細レポートへの参照、および Web ベースの画像などのリソースへの参照はすべて完全修飾 URL で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b59db-105">In the report definition, all references to subreports, drillthrough reports, and resources such as Web-based images, must be fully qualified URLS.</span></span>  
  
 <span data-ttu-id="b59db-106">プロジェクトにプロパティを設定するには、SharePoint サイトの **メンバー** 権限または **所有者** 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b59db-106">You must have **Member** or **Owner** permission on the SharePoint site to set the properties on the project.</span></span> <span data-ttu-id="b59db-107">詳細については、「 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b59db-107">For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a><span data-ttu-id="b59db-108">レポートを SharePoint サイトにパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="b59db-108">To publish a report to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="b59db-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で既存または新規のレポート サーバー プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b59db-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open an existing or new Report Server project.</span></span>  
  
2.  <span data-ttu-id="b59db-110">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b59db-110">From the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="b59db-111">[ _\<project>_ **プロパティページ**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b59db-111">The _\<project>_**Property Pages** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b59db-112">**[構成]** ボックスで、レポートのビルドとパブリッシュに使用するソリューション ビルド構成の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="b59db-112">In the **Configuration** list, select the name of a solution build configuration to use to build and publish your report.</span></span> <span data-ttu-id="b59db-113">現在の構成が**アクティブ**() として表示され *\<configuration>* ます。</span><span class="sxs-lookup"><span data-stu-id="b59db-113">The current configuration is listed as **Active**(*\<configuration>*).</span></span>  
  
4.  <span data-ttu-id="b59db-114">プロジェクトの共有データ ソースをパブリッシュし、以前にパブリッシュされた共有データ ソースを上書きするには、 **[OverwriteDataSources]** を **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="b59db-114">If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.</span></span>  
  
5.  <span data-ttu-id="b59db-115">Optional[ **Targetdatasourcefolder**] に、SharePoint ライブラリまたはライブラリフォルダーの URL (など) を入力し *http://TestServer/TestSite/Documents/DataSources)* ます。</span><span class="sxs-lookup"><span data-stu-id="b59db-115">(Optional) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder (for example, *http://TestServer/TestSite/Documents/DataSources)*.</span></span>  
  
     <span data-ttu-id="b59db-116">値を指定しない場合は、 **[TargetReportFolder]** の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b59db-116">If you do not specify a value, the **TargetReportFolder** value is used.</span></span>  
  
6.  <span data-ttu-id="b59db-117">[ **Targetreportfolder**] に、ライブラリまたはライブラリフォルダーの URL (など) を入力し *http://TestServer/TestSite/Documents/Reports)* ます。</span><span class="sxs-lookup"><span data-stu-id="b59db-117">For **TargetReportFolder**, type a URL to a library or library folder (for example, *http://TestServer/TestSite/Documents/Reports)*.</span></span>  
  
7.  <span data-ttu-id="b59db-118">**[TargetServerURL]** に、SharePoint トップレベル サイトまたはサブサイトの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="b59db-118">For **TargetServerURL**, type a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="b59db-119">サイトを指定しない場合は、既定のトップレベルサイトが使用されます (たとえば、、 *http://servername* *http://servername/site* 、または *http://servername/site/subsite* )。</span><span class="sxs-lookup"><span data-stu-id="b59db-119">If you do not specify a site, the default top-level site is used (for example, *http://servername*, *http://servername/site*, or *http://servername/site/subsite*).</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="b59db-120">ソリューション エクスプローラーで、パブリッシュするレポートを右クリックし、 **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b59db-120">In Solution Explorer, right-click the report you want to publish, and click **Deploy**.</span></span> <span data-ttu-id="b59db-121">これで、 **[TargetReportFolder]** で指定した場所にレポートがパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="b59db-121">The report is published to the location specified in **TargetReportFolder**.</span></span> <span data-ttu-id="b59db-122">配置エラーは出力ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b59db-122">Deployment errors appear in the Output window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59db-123">参照</span><span class="sxs-lookup"><span data-stu-id="b59db-123">See Also</span></span>  
 <span data-ttu-id="b59db-124">[[プロジェクトプロパティページ] ダイアログボックス](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="b59db-124">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="b59db-125">[展開プロパティを設定 &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="b59db-125">[Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span></span>  
 <span data-ttu-id="b59db-126">[レポートサーバーへのレポートのパブリッシュ](publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="b59db-126">[Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md) </span></span>  
 <span data-ttu-id="b59db-127">[SharePoint モードのレポートサーバー上のパブリッシュされたレポートアイテムの URL の例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="b59db-127">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 [<span data-ttu-id="b59db-128">レポートで Office Data Connection &#40;.odc&#41; を使用する &#40;Reporting Services の SharePoint 統合モード&#41;</span><span class="sxs-lookup"><span data-stu-id="b59db-128">Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
