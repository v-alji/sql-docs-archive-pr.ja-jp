---
title: 計算 (キューブデザイナー) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.f1
ms.assetid: 46e2fbe2-bb41-4eaa-91f8-eb2bd3b8d00d
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdbc35a8e47557923b90cda4e72280c3cca940dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634167"
---
# <a name="calculations-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="3c5d3-102">[計算] (キューブ デザイナー) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="3c5d3-102">Calculations (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="3c5d3-103">キューブ デザイナーの **[計算]** タブを使用すると、選択されているキューブの、計算されるメンバー、名前付きセット、および多次元式 (MDX) スクリプト コマンドなどの計算を表示したり編集したりできます。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-103">Use the **Calculations** tab in Cube Designer to view and edit calculations, including calculated members, named sets, and Multidimensional Expressions (MDX) script commands for the selected cube.</span></span>  
  
## <a name="form-view-and-script-view"></a><span data-ttu-id="3c5d3-104">フォーム ビューとスクリプト ビュー</span><span class="sxs-lookup"><span data-stu-id="3c5d3-104">Form View and Script View</span></span>  
 <span data-ttu-id="3c5d3-105">**[計算]** タブでは、計算を表示または編集するときに 2 つの異なるビューをサポートします。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-105">The **Calculations** tab supports two different views when viewing or editing calculations:</span></span>  
  
-   <span data-ttu-id="3c5d3-106">フォーム ビュー</span><span class="sxs-lookup"><span data-stu-id="3c5d3-106">Form view</span></span>  
  
     <span data-ttu-id="3c5d3-107">このビューには、キューブに関連付けられている MDX スクリプトに含まれる、計算されるメンバー、名前付きセット、およびスクリプト コマンドが分類されて表示されます。計算されるメンバーおよび名前付きセットを表示および編集するためのフォーム エディターが用意され、キューブで使用できるメタデータ、関数、およびツールも表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-107">This view displays an organized view of the calculated members, named sets, and script commands contained in the MDX script associated with the cube and provides form editors to view and edit calculated members and named sets, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
-   <span data-ttu-id="3c5d3-108">スクリプト ビュー</span><span class="sxs-lookup"><span data-stu-id="3c5d3-108">Script view</span></span>  
  
     <span data-ttu-id="3c5d3-109">上級ユーザー向けに、このビューには、キューブに関連付けられている MDX スクリプト全体が表示されます。また、キューブで使用できるメタデータ、関数、およびツールも表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-109">For advanced users, this view displays the entire MDX script associated with the cube, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
## <a name="panes"></a><span data-ttu-id="3c5d3-110">ペイン</span><span class="sxs-lookup"><span data-stu-id="3c5d3-110">Panes</span></span>  
 <span data-ttu-id="3c5d3-111">**ツール バー**</span><span class="sxs-lookup"><span data-stu-id="3c5d3-111">**Toolbar**</span></span>  
 <span data-ttu-id="3c5d3-112">フォームビューとスクリプトビューの両方のツールバーを使用して、このタブで一般的な操作を実行します。このペインの詳細については、「[ツールバー &#40;の計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-112">Use the toolbar in both form view and script view to perform common operations on this tab. For more information about this pane, see [Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="3c5d3-113">**[スクリプト オーガナイザー]**</span><span class="sxs-lookup"><span data-stu-id="3c5d3-113">**Script Organizer**</span></span>  
 <span data-ttu-id="3c5d3-114">フォーム ビューの **[スクリプト オーガナイザー]** ペインでは、キューブ スクリプトの内容を一定の順に並べ替えて表示できます。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-114">Use the **Script Organizer** pane in form view to display the contents of the cube script in an ordered format.</span></span> <span data-ttu-id="3c5d3-115">このペインの詳細については、「[[スクリプト オーガナイザー] (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)](script-organizer-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-115">For more information about this pane, see [Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="3c5d3-116">**[計算ツール]**</span><span class="sxs-lookup"><span data-stu-id="3c5d3-116">**Calculation Tools**</span></span>  
 <span data-ttu-id="3c5d3-117">フォーム ビューとスクリプト ビューのどちらにも用意されている **[計算ツール]** ペインには、キューブで使用できるメタデータ、関数、およびツールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-117">Use the **Calculation Tools** pane in both form view and script view to display metadata, functions, and tools available to the cube.</span></span> <span data-ttu-id="3c5d3-118">このペインの詳細については、「[計算ツール (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)](calculation-tools-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-118">For more information about this pane, see [Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="3c5d3-119">**スクリプト エディター**</span><span class="sxs-lookup"><span data-stu-id="3c5d3-119">**Script Editor**</span></span>  
 <span data-ttu-id="3c5d3-120">スクリプト ビューの **[スクリプト エディター]** ペインでは、キューブ スクリプト全体を編集できます。フォーム ビューの [スクリプト エディター] ペインでは、キューブ スクリプトに含まれるスクリプト コマンドを編集できます。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-120">Use the **Script Editor** pane in script view to edit the entire cube script and in form view to edit script commands contained in the cube script.</span></span> <span data-ttu-id="3c5d3-121">このペインの詳細については、「[スクリプト エディター (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-121">For more information about this pane, see [Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="3c5d3-122">**計算されるメンバー フォーム エディター**</span><span class="sxs-lookup"><span data-stu-id="3c5d3-122">**Calculated Member Form Editor**</span></span>  
 <span data-ttu-id="3c5d3-123">フォーム ビューの**計算されるメンバー フォーム エディター** ペインでは、キューブ スクリプトに含まれる、計算されるメンバーを編集できます。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-123">Use the **Calculated Member Form Editor** pane in form view to edit calculated members in the cube script.</span></span> <span data-ttu-id="3c5d3-124">このペインの詳細については、「[計算されるメンバー フォーム エディター (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-124">For more information about this pane, see [Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="3c5d3-125">**名前付きセット フォーム エディター**</span><span class="sxs-lookup"><span data-stu-id="3c5d3-125">**Named Set Form Editor**</span></span>  
 <span data-ttu-id="3c5d3-126">フォーム ビューの**名前付きセット フォーム エディター** ペインでは、キューブ スクリプトに含まれる名前付きセットを編集できます。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-126">Use the **Named Set Form Editor** pane in form view to edit named sets in the cube script.</span></span> <span data-ttu-id="3c5d3-127">このペインの詳細については、「[名前付きセット フォーム エディター (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c5d3-127">For more information about this pane, see [Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5d3-128">参照</span><span class="sxs-lookup"><span data-stu-id="3c5d3-128">See Also</span></span>  
 <span data-ttu-id="3c5d3-129">[キューブオブジェクト &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3c5d3-129">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="3c5d3-130">[Custom](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="3c5d3-130">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="3c5d3-131">[MDX スクリプティングの基礎 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3c5d3-131">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="3c5d3-132">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3c5d3-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="3c5d3-133">名前付きセットの作成</span><span class="sxs-lookup"><span data-stu-id="3c5d3-133">Create Named Sets</span></span>](multidimensional-models/create-named-sets.md)  
  
  
