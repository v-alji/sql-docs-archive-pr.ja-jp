---
title: '[Excel で分析] (キューブデザイナーの [ブラウザー] タブ) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.datapane.f1
- sql12.asvs.ssms.analyzeinexcel.f1
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9fa27ae291d40b7f5637e3968438fcaec1de03d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633644"
---
# <a name="analyze-in-excel-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="49fa7-102">[Excel で分析] (キューブ デザイナーの [ブラウザー] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="49fa7-102">Analyze in Excel (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="49fa7-103">キューブ開発者は、プロジェクトがエンド ユーザーにどのように表示されるかを **"Excel で分析"** で簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-103">**Analyze in Excel** provides the cube developer with a way to quickly review how a project would look to the end user.</span></span> <span data-ttu-id="49fa7-104">**"Excel で分析"** 機能によって Microsoft Excel が開き、モデル ワークスペース データベースへのデータ ソース接続が作成され、自動的にピボットテーブルがワークシートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-104">The **Analyze in Excel** feature opens Microsoft Excel, creates a data source connection to the workspace database, and automatically adds a PivotTable to the worksheet.</span></span> <span data-ttu-id="49fa7-105">この機能は、以前のリリースで [ブラウザー] タブに組み込みのピボットテーブルを提供していた Office Web コントロールに替わるものです。</span><span class="sxs-lookup"><span data-stu-id="49fa7-105">This feature replaces the Office Web Control that provided an embedded PivotTable in the Browser tab in previous releases.</span></span>  
  
 <span data-ttu-id="49fa7-106">**キューブ データを表示するには:**</span><span class="sxs-lookup"><span data-stu-id="49fa7-106">**To view cube data:**</span></span>  
  
1.  <span data-ttu-id="49fa7-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]のソリューション エクスプローラーでキューブをダブルクリックすると、キューブ デザイナーでそのキューブが開きます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in Solution Explorer, double-click a cube to open it in Cube Designer.</span></span>  
  
2.  <span data-ttu-id="49fa7-108">**[ブラウザー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="49fa7-108">Click the **Browser** tab.</span></span>  
  
3.  <span data-ttu-id="49fa7-109">**[再接続]** をクリックして、接続を検証します。</span><span class="sxs-lookup"><span data-stu-id="49fa7-109">Click **Reconnect** to validate the connection.</span></span>  
  
4.  <span data-ttu-id="49fa7-110">メニュー バーの Excel アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="49fa7-110">Click the Excel icon in the menu bar.</span></span>  
  
5.  <span data-ttu-id="49fa7-111">データ接続の有効化を求めるメッセージが表示されたら、 **[有効]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49fa7-111">When asked to enable data connections, click **Enable**.</span></span> <span data-ttu-id="49fa7-112">現在のデータ接続を使用して Excel が開かれ、ワークシートにはピボットテーブルが追加されて、データの参照が可能になります。</span><span class="sxs-lookup"><span data-stu-id="49fa7-112">Excel opens using the current data connection, adding a PivotTable to the worksheet so that you can begin browsing your data.</span></span>  
  
 <span data-ttu-id="49fa7-113">これで、メジャーをファクト テーブルから値領域にドラッグしたり、ディメンション属性を行領域や列領域にドラッグしたりして、ピボットテーブルを対話的に構築できます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-113">You can now build a PivotTable interactively by dragging measures from the fact table to the Values area, and dimension attributes to the Row and Column areas.</span></span> <span data-ttu-id="49fa7-114">階層がある場合は、行領域または列領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="49fa7-114">If you have hierarchies, add them to Rows or Column areas.</span></span> <span data-ttu-id="49fa7-115">階層をロール アップまたはドリル ダウンして、異なるレベルのファクト データを参照できます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-115">You can roll up or drill down the hierarchy to browse fact data at different levels.</span></span>  
  
 <span data-ttu-id="49fa7-116">オブジェクトとデータは、有効なユーザーまたはロールおよびパースペクティブのコンテキスト内で表示されます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-116">Objects and data are viewed within the context of the effective user or role and perspective.</span></span> <span data-ttu-id="49fa7-117">Excel を使用している場合、クエリ実行時のデータ ソースへの接続には、 **[権限借用情報]** ページで指定された資格情報ではなく、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-117">When using Excel, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49fa7-118">"Excel で分析" 機能を使用するには、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]と同じコンピューターに Excel がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="49fa7-118">To use the Analyze in Excel feature, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="49fa7-119">Excel が同じコンピューターにインストールされていない場合は、別のコンピューターの Excel を使用して、データ ソースとしてキューブに接続できます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-119">If Excel is not installed on the same computer, you can use Excel on another computer and connect to the cube as a data source.</span></span> <span data-ttu-id="49fa7-120">これにより、ピボットテーブルをワークシートに手動で追加することができます。</span><span class="sxs-lookup"><span data-stu-id="49fa7-120">You can then manually add a PivotTable to the worksheet.</span></span> <span data-ttu-id="49fa7-121">モデル オブジェクト (テーブル、列、メジャー、および KPI) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="49fa7-121">Model objects (tables, columns, measures, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
 <span data-ttu-id="49fa7-122">**"Excel で分析"** 機能の詳細については、以下のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="49fa7-122">For more information about the **Analyze in Excel** feature, see these resources:</span></span>  
  
 [<span data-ttu-id="49fa7-123">Excel で分析 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="49fa7-123">Analyze in Excel &#40;SSAS Tabular&#41;</span></span>](tabular-models/analyze-in-excel-ssas-tabular.md)  
  
 [<span data-ttu-id="49fa7-124">Excel でのテーブル モデルの分析 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="49fa7-124">Analyze a Tabular Model in Excel &#40;SSAS Tabular&#41;</span></span>](tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)  
  
 [<span data-ttu-id="49fa7-125">キューブ内のデータおよびメタデータの参照</span><span class="sxs-lookup"><span data-stu-id="49fa7-125">Browse data and metadata in Cube</span></span>](multidimensional-models/browse-data-and-metadata-in-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="49fa7-126">参照</span><span class="sxs-lookup"><span data-stu-id="49fa7-126">See Also</span></span>  
 <span data-ttu-id="49fa7-127">[ブラウザー &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="49fa7-127">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="49fa7-128">[ツールバー &#40;[ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="49fa7-128">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="49fa7-129">[[メタデータ &#40;ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="49fa7-129">[Metadata &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="49fa7-130">[キューブデザイナーの [&#40;ブラウザー] タブの [クエリとフィルター]&#41; &#40;Analysis Services-多次元データ&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="49fa7-130">[Query and Filter &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
