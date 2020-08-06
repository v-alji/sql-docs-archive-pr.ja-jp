---
title: Kpi (キューブデザイナー) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpisview.f1
ms.assetid: 3cd99acc-368d-4e21-ad18-298fff056acd
author: minewiskan
ms.author: owend
ms.openlocfilehash: d7a655fbceed25c78f9795165e6140a033ae634a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633405"
---
# <a name="kpis-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="5baad-102">[KPI] (キューブ デザイナー) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="5baad-102">KPIs (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5baad-103">キューブ デザイナーの **[KPI]** タブを使用すると、選択したキューブの主要業績評価指標 (KPI) を表示したり編集したりできます。</span><span class="sxs-lookup"><span data-stu-id="5baad-103">Use the **KPIs** tab in Cube Designer to view and edit Key Performance Indicators (KPIs) for the selected cube.</span></span>  
  
## <a name="form-view-and-browser-view"></a><span data-ttu-id="5baad-104">フォーム ビューとブラウザー ビュー</span><span class="sxs-lookup"><span data-stu-id="5baad-104">Form View and Browser View</span></span>  
 <span data-ttu-id="5baad-105">**[KPI]** タブで KPI の表示や編集をする際には、次の 2 種類のビューがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5baad-105">The **KPIs** tab supports two different views when viewing or editing KPIs:</span></span>  
  
-   <span data-ttu-id="5baad-106">フォーム ビュー</span><span class="sxs-lookup"><span data-stu-id="5baad-106">Form view</span></span>  
  
     <span data-ttu-id="5baad-107">このビューでは、キューブに含まれている KPI が整理されて表示されます。フォーム エディターによって KPI の表示と編集ができるだけでなく、キューブで利用できるメタデータ、関数、ツールも表示されます。</span><span class="sxs-lookup"><span data-stu-id="5baad-107">This view displays an organized view of the KPIs contained by the cube and provides a form editor to view and edit a KPI, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
-   <span data-ttu-id="5baad-108">ブラウザー ビュー</span><span class="sxs-lookup"><span data-stu-id="5baad-108">Browser view</span></span>  
  
     <span data-ttu-id="5baad-109">このビューには、キューブに含まれている KPI の結果がブラウザーに表示されます。KPI の結果を表示する際のフィルター条件も指定できます。</span><span class="sxs-lookup"><span data-stu-id="5baad-109">This view displays the results of the KPIs contained by the cube in a browser, with the capability to provide filter criteria when viewing KPI results.</span></span>  
  
## <a name="panes"></a><span data-ttu-id="5baad-110">ペイン</span><span class="sxs-lookup"><span data-stu-id="5baad-110">Panes</span></span>  
  
|<span data-ttu-id="5baad-111">ペイン</span><span class="sxs-lookup"><span data-stu-id="5baad-111">Pane</span></span>|<span data-ttu-id="5baad-112">定義</span><span class="sxs-lookup"><span data-stu-id="5baad-112">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="5baad-113">**ツール バー**</span><span class="sxs-lookup"><span data-stu-id="5baad-113">**Toolbar**</span></span>|<span data-ttu-id="5baad-114">フォームビューとブラウザービューの両方のツールバーを使用して、このタブで一般的な操作を実行します。このペインの詳細については、「[ツールバー &#40;[Kpi] タブ」、「キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5baad-114">Use the toolbar in both form view and browser view to perform common operations on this tab. For more information about this pane, see [Toolbar &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="5baad-115">**[KPI オーガナイザー]**</span><span class="sxs-lookup"><span data-stu-id="5baad-115">**KPI Organizer**</span></span>|<span data-ttu-id="5baad-116">フォーム ビューの **[KPI オーガナイザー]** ペインでは、キューブに含まれている KPI が一覧形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="5baad-116">Use the **KPI Organizer** pane in form view to display the KPIs contained by the cube in an ordered format.</span></span> <span data-ttu-id="5baad-117">このペインの詳細については、[「KPI Organizer (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)」](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) (KPI オーガナイザー (キューブ デザイナーの [KPI] タブ) (Analysis Services - 多次元データ)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5baad-117">For more information about this pane, see [KPI Organizer &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="5baad-118">**[計算ツール]**</span><span class="sxs-lookup"><span data-stu-id="5baad-118">**Calculation Tools**</span></span>|<span data-ttu-id="5baad-119">フォーム ビューの **[計算ツール]** ペインには、キューブで使用できるメタデータ、関数、およびツールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5baad-119">Use the **Calculation Tools** pane in form view to display metadata, functions, and tools available to the cube.</span></span> <span data-ttu-id="5baad-120">このペインの詳細については、「[Calculation Tools (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)](calculation-tools-kpis-cube-designer-analysis-services-multidimensional-data.md)」 ([計算ツール] (キューブ デザイナーの [KPI] タブ) (Analysis Services - 多次元データ)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5baad-120">For more information about this pane, see [Calculation Tools &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-kpis-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="5baad-121">**KPI フォーム エディター**</span><span class="sxs-lookup"><span data-stu-id="5baad-121">**KPI Form Editor**</span></span>|<span data-ttu-id="5baad-122">フォーム ビューの KPI フォーム エディター ペインでは、キューブに含まれている KPI を編集できます。</span><span class="sxs-lookup"><span data-stu-id="5baad-122">Use the KPI Form Editor pane in form view to edit KPIs contained by the cube.</span></span> <span data-ttu-id="5baad-123">このペインの詳細については、「[KPI Form Editor (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)」 ([KPI フォーム エディター] (キューブ デザイナーの [KPI] タブ) (Analysis Services - 多次元データ)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5baad-123">For more information about this pane, see [KPI Form Editor &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="5baad-124">**[KPI ブラウザー]**</span><span class="sxs-lookup"><span data-stu-id="5baad-124">**KPI Browser**</span></span>|<span data-ttu-id="5baad-125">ブラウザー ビューの [KPI ブラウザー] ペインには、キューブに含まれている KPI の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5baad-125">Use the KPI Browser pane in browser view to view the results of the KPIs contained by the cube.</span></span> <span data-ttu-id="5baad-126">このペインの詳細については、「[KPI Browser (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)」 ([KPI ブラウザー] (キューブ デザイナーの [KPI] タブ) (Analysis Services - 多次元データ)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5baad-126">For more information about this pane, see [KPI Browser &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5baad-127">参照</span><span class="sxs-lookup"><span data-stu-id="5baad-127">See Also</span></span>  
 <span data-ttu-id="5baad-128">[多次元モデルの Kpi&#41; &#40;主要業績評価指標](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="5baad-128">[Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="5baad-129">[MDX スクリプティングの基礎 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="5baad-129">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="5baad-130">キューブデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="5baad-130">Cube Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-designer-analysis-services-multidimensional-data.md)  
  
  
