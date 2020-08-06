---
title: クエリとフィルター (キューブデザイナーの [ブラウザー] タブ) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.filterpane.f1
ms.assetid: f5cf0bb1-3afb-4856-a2ef-614deb4e7e49
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66bd299e210b3d00384395177cdd6e89d1c00183
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634705"
---
# <a name="query-and-filter-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="ecb57-102">クエリとフィルター (キューブ デザイナーの [ブラウザー] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="ecb57-102">Query and Filter (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="ecb57-103">キューブ デザイナーの **[ブラウザー]** タブのこの領域には、参照目的で使用するデータやクエリに使用するデータをキューブから簡単に選択できるクエリ/フィルター領域があります。</span><span class="sxs-lookup"><span data-stu-id="ecb57-103">This area of the **Browser** tab in Cube Designer contains a query and filter area, to help you choose data from the cube to use in browsing or in queries.</span></span> <span data-ttu-id="ecb57-104">キューブ オブジェクトは必要に応じていくつでも追加でき、その結果をデータ領域で確認することができます。また、"Excel で分析" を使用して結果をレポートにエクスポートすることにより、エンド ユーザーから見たデータの体裁を視覚的に確認することができます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-104">You can add as many cube objects as you want, and then view the results in the data area, or export the results to a report using Analyze in Excel to visualize how the data would be viewed by end users.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ecb57-105">この領域でデータを扱うときは、 **[ブラウザー]** が既定でグラフィカル デザイン モードになります。</span><span class="sxs-lookup"><span data-stu-id="ecb57-105">When you are working with data in this area, by default the **Browser** uses the graphical design mode.</span></span> <span data-ttu-id="ecb57-106">ただし、 **[デザイン モード]** 切り替えボタンをクリックすると、MDX を使用して直接クエリを編集できます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-106">However, you can edit the query directly using MDX, by clicking the **Design Mode** toggle button.</span></span> <span data-ttu-id="ecb57-107">この場合、ディメンションに対するフィルターをデザインするためのペインは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="ecb57-107">When you do so, the pane that lets you design filters on dimensions disappears.</span></span> <span data-ttu-id="ecb57-108">フィルターを追加する必要がある場合は、再度グラフィカル デザイン モードに切り替えてください。</span><span class="sxs-lookup"><span data-stu-id="ecb57-108">If you want to add a filter, you can switch back to graphical design mode.</span></span>  
  
 <span data-ttu-id="ecb57-109">既定では、クエリの実行時、データ ソースへの接続には、 **[権限借用情報]** ページで指定された資格情報ではなく、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-109">By default, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.</span></span> <span data-ttu-id="ecb57-110">ただし、 **ツール バー** の **[ユーザーの変更]** をクリックすることによって、クエリまたはレポートのユーザー コンテキストを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-110">However, you can also change the user context for the query or report by clicking **Change User** on the **Toolbar**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ecb57-111">Options</span><span class="sxs-lookup"><span data-stu-id="ecb57-111">Options</span></span>  
 <span data-ttu-id="ecb57-112">**ディメンション**</span><span class="sxs-lookup"><span data-stu-id="ecb57-112">**Dimension**</span></span>  
 <span data-ttu-id="ecb57-113">サブキューブをスライスするディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="ecb57-113">Select the dimension on which to slice the subcube.</span></span>  
  
 <span data-ttu-id="ecb57-114">**Hierarchy**</span><span class="sxs-lookup"><span data-stu-id="ecb57-114">**Hierarchy**</span></span>  
 <span data-ttu-id="ecb57-115">サブキューブをスライスする階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="ecb57-115">Select the hierarchy on which to slice the subcube.</span></span>  
  
 <span data-ttu-id="ecb57-116">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="ecb57-116">**Operator**</span></span>  
 <span data-ttu-id="ecb57-117">**[フィルター式]** の式を、選択した階層に適用する方法を定義する演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="ecb57-117">Select the operator that defines how the expression in **Filter Expression** is applied to the selected hierarchy.</span></span> <span data-ttu-id="ecb57-118">次の表では、使用可能な演算子について説明しています。</span><span class="sxs-lookup"><span data-stu-id="ecb57-118">The following table describes the available operators.</span></span>  
  
|<span data-ttu-id="ecb57-119">値</span><span class="sxs-lookup"><span data-stu-id="ecb57-119">Value</span></span>|<span data-ttu-id="ecb57-120">説明</span><span class="sxs-lookup"><span data-stu-id="ecb57-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecb57-121">**Equal**</span><span class="sxs-lookup"><span data-stu-id="ecb57-121">**Equal**</span></span>|<span data-ttu-id="ecb57-122">結果は **[フィルター式]** で定義された設定に制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-122">The results are restricted to the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="ecb57-123">**等しくない**</span><span class="sxs-lookup"><span data-stu-id="ecb57-123">**Not Equal**</span></span>|<span data-ttu-id="ecb57-124">結果は **[フィルター式]** で定義された設定によって除外されたメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-124">The results are restricted to the members excluded by the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="ecb57-125">**In**</span><span class="sxs-lookup"><span data-stu-id="ecb57-125">**In**</span></span>|<span data-ttu-id="ecb57-126">結果は **[フィルター式]** で選択された名前付きセットに制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-126">The results are restricted to the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="ecb57-127">**含まれない**</span><span class="sxs-lookup"><span data-stu-id="ecb57-127">**Not In**</span></span>|<span data-ttu-id="ecb57-128">結果は **[フィルター式]** で選択された名前付きセットによって除外されたメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-128">The results are restricted to the members excluded by the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="ecb57-129">**Contains**</span><span class="sxs-lookup"><span data-stu-id="ecb57-129">**Contains**</span></span>|<span data-ttu-id="ecb57-130">結果は **[フィルター式]** にある文字列をメンバー名に含むメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-130">The results are restricted to members whose member names contain the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="ecb57-131">**で始まる**</span><span class="sxs-lookup"><span data-stu-id="ecb57-131">**Begins With**</span></span>|<span data-ttu-id="ecb57-132">結果は **[フィルター式]** にある文字列で始まるメンバー名を持つメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-132">The results are restricted to members whose member names begin with the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="ecb57-133">**[範囲 (包含)]**</span><span class="sxs-lookup"><span data-stu-id="ecb57-133">**Range (Inclusive)**</span></span>|<span data-ttu-id="ecb57-134">結果は **[フィルター式]** で選択された範囲に制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-134">The results are restricted to the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="ecb57-135">**[範囲 (排他)]**</span><span class="sxs-lookup"><span data-stu-id="ecb57-135">**Range (Exclusive)**</span></span>|<span data-ttu-id="ecb57-136">結果は **[フィルター式]** で選択された範囲によって除外されたメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-136">The results are restricted to the members excluded by the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="ecb57-137">**MDX**</span><span class="sxs-lookup"><span data-stu-id="ecb57-137">**MDX**</span></span>|<span data-ttu-id="ecb57-138">結果は **[フィルター式]** で設定された多次元式 (MDX) に制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-138">The results are restricted to the Multidimensional Expressions (MDX) expression set in **Filter Expression**.</span></span>|  
  
 <span data-ttu-id="ecb57-139">**[フィルター式]**</span><span class="sxs-lookup"><span data-stu-id="ecb57-139">**Filter Expression**</span></span>  
 <span data-ttu-id="ecb57-140">**[演算子]** によって評価される式を入力します。この式により、参照される結果が制限されます。</span><span class="sxs-lookup"><span data-stu-id="ecb57-140">Type the expression that is to be evaluated by **Operator**, which restricts the results to be browsed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecb57-141">このフィールドは、動的データの入力要素であり、選択された演算子に必要なデータの型を反映して表示内容が変わります。</span><span class="sxs-lookup"><span data-stu-id="ecb57-141">This field is a dynamic data entry element, changing appearance to reflect the types of data necessary for the selected operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb57-142">参照</span><span class="sxs-lookup"><span data-stu-id="ecb57-142">See Also</span></span>  
 <span data-ttu-id="ecb57-143">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ecb57-143">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="ecb57-144">[ブラウザー &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ecb57-144">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="ecb57-145">[ツールバー &#40;[ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ecb57-145">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="ecb57-146">[[Excel で分析] &#40;[ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ecb57-146">[Analyze in Excel &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="ecb57-147">[[メタデータ &#40;ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="ecb57-147">[Metadata &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
