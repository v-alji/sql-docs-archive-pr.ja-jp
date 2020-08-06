---
title: キューブ構造 (キューブデザイナー) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilderview.f1
ms.assetid: 00f0b605-5352-4b42-84f5-bd6c3e42d3d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 857dd87c1d638a29adfa11c7de5a4d9f2d006314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643649"
---
# <a name="cube-structure-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="a7ebc-102">[キューブ構造] (キューブ デザイナー) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="a7ebc-102">Cube Structure (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a7ebc-103">**で** キューブ デザイナー **の** [キューブ構造] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] タブを使用すると、メジャー グループやメジャーを作成、変更、キューブ ディメンションを追加、キューブに含まれているオブジェクトを関連するデータ ソース ビューから表示する操作ができます。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-103">Use the **Cube Structure** tab in **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create and modify measure groups and measures, add cube dimensions, and display the objects included in the cube from the associated data source view.</span></span>  
  
 <span data-ttu-id="a7ebc-104">**[キューブ構造]** タブには、次のペインがあります。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-104">The **Cube Structure** tab contains the following panes:</span></span>  
  
## <a name="panes"></a><span data-ttu-id="a7ebc-105">ペイン</span><span class="sxs-lookup"><span data-stu-id="a7ebc-105">Panes</span></span>  
  
|<span data-ttu-id="a7ebc-106">ペイン</span><span class="sxs-lookup"><span data-stu-id="a7ebc-106">Pane</span></span>|<span data-ttu-id="a7ebc-107">定義</span><span class="sxs-lookup"><span data-stu-id="a7ebc-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="a7ebc-108">**ツール バー**</span><span class="sxs-lookup"><span data-stu-id="a7ebc-108">**Toolbar**</span></span>|<span data-ttu-id="a7ebc-109">ツールバーを使用して、このタブで一般的な操作を実行します。このペインの詳細については、「[ツールバー &#40;[キューブ構造] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-109">Use the toolbar to perform common actions in this tab. For more information about this pane, see [Toolbar &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="a7ebc-110">**直径**</span><span class="sxs-lookup"><span data-stu-id="a7ebc-110">**Measures**</span></span>|<span data-ttu-id="a7ebc-111">**[メジャー]** ペインを使用して、選択したキューブのメジャー グループやメジャーを作成、変更します。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-111">Use the **Measures** pane to create and modify measure groups and measures for the selected cube.</span></span> <span data-ttu-id="a7ebc-112">このペインの詳細については、「[[メジャー] (キューブ デザイナーの [キューブ構造] タブ) (Analysis Services - 多次元データ)](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-112">For more information about this pane, see [Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="a7ebc-113">**Dimensions**</span><span class="sxs-lookup"><span data-stu-id="a7ebc-113">**Dimensions**</span></span>|<span data-ttu-id="a7ebc-114">**[ディメンション]** ペインを使用して、選択したキューブのキューブ ディメンションを保持、変更します。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-114">Use the **Dimensions** pane to include and modify cube dimensions for the selected cube.</span></span> <span data-ttu-id="a7ebc-115">このペインの詳細については、「[[ディメンション] (キューブ デザイナーの [キューブ構造] タブ) (Analysis Services - 多次元データ)](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-115">For more information about this pane, see [Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="a7ebc-116">**データソースビュー**</span><span class="sxs-lookup"><span data-stu-id="a7ebc-116">**Data Source View**</span></span>|<span data-ttu-id="a7ebc-117">**[データ ソース ビュー]** ペインを使用して、選択したキューブに関連付けられたデータ ソース ビューを表示、編集します。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-117">Use the **Data Source View** pane to view and edit the data source view associated with the selected cube.</span></span> <span data-ttu-id="a7ebc-118">このペインの詳細については、「[[データ ソース ビュー] (キューブ デザイナーの [キューブ構造] タブ) (Analysis Services - 多次元データ)](data-source-view-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7ebc-118">For more information about this pane, see [Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7ebc-119">参照</span><span class="sxs-lookup"><span data-stu-id="a7ebc-119">See Also</span></span>  
 <span data-ttu-id="a7ebc-120">[論理アーキテクチャ &#40;Analysis Services-多次元データ&#41;](multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebc-120">[Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md) </span></span>  
 <span data-ttu-id="a7ebc-121">[多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebc-121">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="a7ebc-122">[メジャーのプロパティの構成](multidimensional-models/configure-measure-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebc-122">[Configure Measure Properties](multidimensional-models/configure-measure-properties.md) </span></span>  
 <span data-ttu-id="a7ebc-123">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebc-123">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a7ebc-124">[多次元モデルのデータソースビュー](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebc-124">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="a7ebc-125">キューブデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="a7ebc-125">Cube Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-designer-analysis-services-multidimensional-data.md)  
  
  
