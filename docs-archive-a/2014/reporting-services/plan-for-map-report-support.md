---
title: マップレポートのサポートを計画する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3d1e1774e44ae879b8c01e66289cefd4d42ee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739498"
---
# <a name="plan-for-map-report-support"></a><span data-ttu-id="bdab2-102">マップ レポートのサポートを計画する</span><span class="sxs-lookup"><span data-stu-id="bdab2-102">Plan for Map Report Support</span></span>
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]<span data-ttu-id="bdab2-103">では、空間データソースを使用するマップレポートがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bdab2-103">supports map reports that use spatial data sources.</span></span> <span data-ttu-id="bdab2-104">空間データは、SQL Server データベース、ESRI シェープファイル、または Reporting Services かレポート ビルダーを使用してインストールされたマップ ギャラリーから取得できます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-104">Spatial data can come from SQL Server databases, from ESRI Shapefiles, or from the Map Gallery that is installed with either Reporting Services or Report Builder.</span></span> <span data-ttu-id="bdab2-105">また、マップには Bing のマップ タイルの背景も表示できます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-105">A map can also display a background of Bing map tiles.</span></span> <span data-ttu-id="bdab2-106">レポートの作成者は、空間データまたは Bing のマップ タイルが動的であり実行時に取得されるか、静的でありレポート定義に埋め込まれるかを指定してレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-106">A report author can create a report that specifies spatial data or Bing map tiles as dynamic and retrieved at run time or as static and embedded in the report definition.</span></span>  
  
## <a name="support-for-bing-maps"></a><span data-ttu-id="bdab2-107">Bing Maps のサポート</span><span class="sxs-lookup"><span data-stu-id="bdab2-107">Support for Bing Maps</span></span>  
 <span data-ttu-id="bdab2-108">マップには、Bing のマップ タイルを表示する背景レイヤーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-108">Maps can include a background layer that displays Bing map tiles.</span></span> <span data-ttu-id="bdab2-109">マップ タイル レイヤーを含むパブリッシュ済みレポートを表示するには、Bing Maps Web サービスからタイルを取得するようにレポート サーバーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdab2-109">To view a published report that has a map tile layer, the report server must be configured to retrieve tiles from Bing Maps Web Services.</span></span> <span data-ttu-id="bdab2-110">詳しくは、「 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bdab2-110">For more information, see [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="bdab2-111">各レポートについて、レポート作成者は、タイル サーバーからタイルを取得する際に SSL (Secure Sockets Layer) 接続を使用するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-111">In each report, report authors can specify whether to use a Secure Sockets Layer (SSL) connection to retrieve tiles from the tile server.</span></span> <span data-ttu-id="bdab2-112">この操作を行うには、タイルレイヤーの [プロパティ] ペインで、ブール型プロパティの UseSecureConnection をに設定する必要があり `true` ます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-112">To do this, in the Properties pane for the tile layer, they must set the Boolean property UseSecureConnection to `true`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdab2-113">レポート内での Bing のマップ タイルの使用については、「 [追加使用条件](https://go.microsoft.com/fwlink/?LinkId=151371) 」および「 [プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=151372)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdab2-113">For more information about the use of Bing map tiles in your report, see [Additional Terms of Use](https://go.microsoft.com/fwlink/?LinkId=151371) and [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=151372).</span></span>  
  
## <a name="report-design-recommendations"></a><span data-ttu-id="bdab2-114">レポートのデザインに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="bdab2-114">Report Design Recommendations</span></span>  
 <span data-ttu-id="bdab2-115">マップ レポートを適切にデザインするには、静的な空間データと動的な空間データのトレードオフを評価し、レポートのユーザーにとって最適なバランスを見極める必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdab2-115">Good report design for map reports requires that the report author assess the trade-offs between static and dynamic spatial data and find a balance that serves the report users.</span></span> <span data-ttu-id="bdab2-116">マップ要素を埋め込んだ場合、レポート定義のサイズが著しく増加しますが、レポート内でマップを表示するために要する時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-116">Embedded map elements can significantly increase the size of the report definition, but reduce the time that is required to view the map report.</span></span> <span data-ttu-id="bdab2-117">動的なマップ要素の場合、レポート定義のサイズが小さくなりますが、マップを処理して表示するために要する時間が増加します。</span><span class="sxs-lookup"><span data-stu-id="bdab2-117">Dynamic map elements reduce the report definition size but increase the time that is required to process and view the map.</span></span> <span data-ttu-id="bdab2-118">レポートの作成者は、この相反する要因の間で適切にバランスをとる必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdab2-118">The report author must find the right balance between these opposing issues.</span></span>  
  
 <span data-ttu-id="bdab2-119">レポート定義のサイズが問題となる場合、レポート サーバーの管理者は、レポートの設計者にレポート定義の空間データの量を削減するように促してもよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="bdab2-119">When report definition size is an issue, as report server administrator, you can encourage report designers to reduce the amount of spatial data in a report definition.</span></span>  
  
 <span data-ttu-id="bdab2-120">次のような場合には、マップ要素がレポート定義に埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-120">Under the following conditions, map elements are embedded in the report definition:</span></span>  
  
-   <span data-ttu-id="bdab2-121">レポートの作成時に、空間データ ソースがローカルのファイル システムに置かれている。</span><span class="sxs-lookup"><span data-stu-id="bdab2-121">When the report is created, the spatial data source is on the local file system.</span></span> <span data-ttu-id="bdab2-122">これには、ローカルにインストールされた ESRI シェープファイルまたはマップ ギャラリーからの空間データも含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-122">This includes spatial data from the Map Gallery or ESRI Shapefiles that have been installed locally.</span></span> <span data-ttu-id="bdab2-123">既定で、マップ ウィザードおよびマップ レイヤー ウィザードでは、ローカル ファイル システム上のデータ ソースに由来する空間データが埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-123">By default, the map wizard and map layer wizard embed spatial data from data sources on the local file system.</span></span>  
  
-   <span data-ttu-id="bdab2-124">レポートの作成者が、レポートに空間データを手動で埋め込むオプションを選択した。</span><span class="sxs-lookup"><span data-stu-id="bdab2-124">The report author chooses the option to embed spatial data manually in the report.</span></span>  
  
 <span data-ttu-id="bdab2-125">マップを含むレポート定義のサイズを削減するには、次の選択肢を 1 つ以上実行します。</span><span class="sxs-lookup"><span data-stu-id="bdab2-125">To help reduce the size of report definitions that have maps, report authors can use one or more of the following options:</span></span>  
  
-   <span data-ttu-id="bdab2-126">のレポートデザイナーから [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 、ESRI シェープファイルの空間データソースをレポートサーバープロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="bdab2-126">From Report Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], add spatial data sources that are ESRI Shapefiles to the report server project.</span></span> <span data-ttu-id="bdab2-127">プロジェクトの配置時に、レポートに加えて ESRI シェープファイルがレポート サーバーにパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="bdab2-127">When you deploy the project, the ESRI Shapefiles are published to the report server in addition to the report.</span></span> <span data-ttu-id="bdab2-128">マップ ウィザードを実行する際に、レポート サーバー プロジェクトの空間データ ソースを指定すると、既定でマップ要素はレポート定義に埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="bdab2-128">When the report author runs the Map wizard, they can specify a spatial data source from the Report Server project, and the map elements are not embedded in the report definitions by default.</span></span>  
  
-   <span data-ttu-id="bdab2-129">レポートビルダーから、レポートサーバーからシェープファイルを選択して、ESRI シェープファイルの空間データソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="bdab2-129">From Report Builder, add spatial data sources that are ESRI Shapefiles by selecting Shapefiles from the report server.</span></span> <span data-ttu-id="bdab2-130">マップ ウィザードを実行する際に、レポート サーバーの空間データ ソースを参照して指定すると、既定でマップ要素はレポート定義に埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="bdab2-130">When the report author runs the Map wizard, they can browse to and select a spatial data source from the report server, and the map elements are not embedded in the report definitions by default.</span></span>  
  
-   <span data-ttu-id="bdab2-131">マップ データを埋め込みマップ データにする必要がある場合、ビューポートの中心位置とズーム レベルを調整して、レポートに必要なマップ データのみが含まれるようにする。</span><span class="sxs-lookup"><span data-stu-id="bdab2-131">When map data must be embedded map data, adjust the viewport center and zoom level to include just the map data that is needed for the report.</span></span>  
  
 <span data-ttu-id="bdab2-132">詳細については、 [&#40;レポートビルダーと SSRS&#41;をマップ](report-design/maps-report-builder-and-ssrs.md)します。</span><span class="sxs-lookup"><span data-stu-id="bdab2-132">For more information, [Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdab2-133">参照</span><span class="sxs-lookup"><span data-stu-id="bdab2-133">See Also</span></span>  
 [<span data-ttu-id="bdab2-134">レポートのトラブルシューティング: マップ レポート &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bdab2-134">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
