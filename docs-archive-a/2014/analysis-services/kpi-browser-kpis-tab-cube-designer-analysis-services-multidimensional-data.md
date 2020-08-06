---
title: KPI ブラウザー (キューブデザイナーの [Kpi] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 591dfb7c27842e365b78484153dbbde3713b452e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633410"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="0f069-102">KPI ブラウザー (キューブ デザイナーの [KPI] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="0f069-102">KPI Browser (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="0f069-103">キューブ デザイナーの **[KPI]** タブの **[KPI ブラウザー]** ペインを使用すると、主要業績評価指標 (KPI) の結果を表示およびテストできます。</span><span class="sxs-lookup"><span data-stu-id="0f069-103">Use the **KPI Browser** pane on the **KPIs** tab in Cube Designer to view and test the results of Key Performance Indicators (KPIs).</span></span> <span data-ttu-id="0f069-104">Kpi は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 参照する前に最初にインスタンスに配置する必要があり [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="0f069-104">KPIs must first be deployed to a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance before browsing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f069-105">このペインは、ブラウザー ビューでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-105">This pane is displayed only in browser view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0f069-106">Options</span><span class="sxs-lookup"><span data-stu-id="0f069-106">Options</span></span>  
 <span data-ttu-id="0f069-107">**サブキューブ グリッド**</span><span class="sxs-lookup"><span data-stu-id="0f069-107">**Subcube grid**</span></span>  
 <span data-ttu-id="0f069-108">サブキューブを定義し、 **[結果]** ペインに表示する KPI の結果を制限するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0f069-108">Use to define a subcube and restrict the results of the KPIs to be displayed in the **Results** pane.</span></span> <span data-ttu-id="0f069-109">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0f069-109">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="0f069-110">**ディメンション**</span><span class="sxs-lookup"><span data-stu-id="0f069-110">**Dimension**</span></span>  
 <span data-ttu-id="0f069-111">このフィルターを適用するディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0f069-111">Select the dimension to which this filter applies.</span></span>  
  
 <span data-ttu-id="0f069-112">**Hierarchy**</span><span class="sxs-lookup"><span data-stu-id="0f069-112">**Hierarchy**</span></span>  
 <span data-ttu-id="0f069-113">このフィルターを適用する階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="0f069-113">Select the hierarchy to which this filter applies.</span></span>  
  
 <span data-ttu-id="0f069-114">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="0f069-114">**Operator**</span></span>  
 <span data-ttu-id="0f069-115">**[フィルター式]** の式を、選択した階層に適用する方法を定義する演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="0f069-115">Select the operator that defines how the expression in **Filter Expression** is applied to the selected hierarchy.</span></span> <span data-ttu-id="0f069-116">次の表では、使用可能な演算子について説明しています。</span><span class="sxs-lookup"><span data-stu-id="0f069-116">The following table describes the available operators.</span></span>  
  
|<span data-ttu-id="0f069-117">値</span><span class="sxs-lookup"><span data-stu-id="0f069-117">Value</span></span>|<span data-ttu-id="0f069-118">説明</span><span class="sxs-lookup"><span data-stu-id="0f069-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0f069-119">**Equal**</span><span class="sxs-lookup"><span data-stu-id="0f069-119">**Equal**</span></span>|<span data-ttu-id="0f069-120">結果は **[フィルター式]** で定義された設定に制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-120">The results are restricted to the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="0f069-121">**等しくない**</span><span class="sxs-lookup"><span data-stu-id="0f069-121">**Not Equal**</span></span>|<span data-ttu-id="0f069-122">結果は **[フィルター式]** で定義された設定によって除外されたメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-122">The results are restricted to the members excluded by the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="0f069-123">**In**</span><span class="sxs-lookup"><span data-stu-id="0f069-123">**In**</span></span>|<span data-ttu-id="0f069-124">結果は **[フィルター式]** で選択された名前付きセットに制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-124">The results are restricted to the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="0f069-125">**含まれない**</span><span class="sxs-lookup"><span data-stu-id="0f069-125">**Not In**</span></span>|<span data-ttu-id="0f069-126">結果は **[フィルター式]** で選択された名前付きセットによって除外されたメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-126">The results are restricted to the members excluded by the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="0f069-127">**Contains**</span><span class="sxs-lookup"><span data-stu-id="0f069-127">**Contains**</span></span>|<span data-ttu-id="0f069-128">結果は **[フィルター式]** にある文字列をメンバー名に含むメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-128">The results are restricted to members whose member names contain the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="0f069-129">**で始まる**</span><span class="sxs-lookup"><span data-stu-id="0f069-129">**Begins With**</span></span>|<span data-ttu-id="0f069-130">結果は **[フィルター式]** にある文字列で始まるメンバー名を持つメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-130">The results are restricted to members whose member names begin with the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="0f069-131">**[範囲 (包含)]**</span><span class="sxs-lookup"><span data-stu-id="0f069-131">**Range (Inclusive)**</span></span>|<span data-ttu-id="0f069-132">結果は **[フィルター式]** で選択された範囲に制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-132">The results are restricted to the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="0f069-133">**[範囲 (排他)]**</span><span class="sxs-lookup"><span data-stu-id="0f069-133">**Range (Exclusive)**</span></span>|<span data-ttu-id="0f069-134">結果は **[フィルター式]** で選択された範囲によって除外されたメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-134">The results are restricted to the members excluded by the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="0f069-135">**MDX**</span><span class="sxs-lookup"><span data-stu-id="0f069-135">**MDX**</span></span>|<span data-ttu-id="0f069-136">結果は **[フィルター式]** で設定された多次元式 (MDX) に制限されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-136">The results are restricted to the Multidimensional Expressions (MDX) expression set in **Filter Expression**.</span></span>|  
  
 <span data-ttu-id="0f069-137">**[フィルター式]**</span><span class="sxs-lookup"><span data-stu-id="0f069-137">**Filter Expression**</span></span>  
 <span data-ttu-id="0f069-138">参照する KPI 結果を制限する **[演算子]** によって評価される式を入力します。</span><span class="sxs-lookup"><span data-stu-id="0f069-138">Type the expression that is to be evaluated by **Operator**, which restricts the KPI results to be browsed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f069-139">このフィールドは、動的データの入力要素であり、選択された演算子に必要なデータの型を反映して表示内容が変わります。</span><span class="sxs-lookup"><span data-stu-id="0f069-139">This field is a dynamic data entry element, changing appearance to reflect the types of data necessary for the selected operator.</span></span>  
  
 <span data-ttu-id="0f069-140">**結果グリッド**</span><span class="sxs-lookup"><span data-stu-id="0f069-140">**Results grid**</span></span>  
 <span data-ttu-id="0f069-141">**[フィルター グリッド]** に定義されたフィルターに基づいて、KPI の評価された値、目標、状態、および傾向を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-141">Displays the evaluated value, goal, status, and trend for the KPIs, based on the filter defined in **Filter grid**.</span></span> <span data-ttu-id="0f069-142">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0f069-142">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="0f069-143">**[構造の表示]**</span><span class="sxs-lookup"><span data-stu-id="0f069-143">**Display Structure**</span></span>  
 <span data-ttu-id="0f069-144">各 KPI の **[フォルダーの表示]** または **[親 KPI]** の値に従って階層化された、キューブに含まれる KPI を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-144">Displays the KPIs contained by the cube, hierarchically organized according to the **Display folder** or **Parent KPI** values for each KPI.</span></span>  
  
 <span data-ttu-id="0f069-145">**Value**</span><span class="sxs-lookup"><span data-stu-id="0f069-145">**Value**</span></span>  
 <span data-ttu-id="0f069-146">KPI の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-146">Displays the value of the KPI.</span></span>  
  
 <span data-ttu-id="0f069-147">**目標**</span><span class="sxs-lookup"><span data-stu-id="0f069-147">**Goal**</span></span>  
 <span data-ttu-id="0f069-148">KPI の目標値を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-148">Displays the goal value of the KPI.</span></span>  
  
 <span data-ttu-id="0f069-149">**状態**</span><span class="sxs-lookup"><span data-stu-id="0f069-149">**Status**</span></span>  
 <span data-ttu-id="0f069-150">KPI の状態マークを表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-150">Displays the status graphic of the KPI.</span></span>  
  
 <span data-ttu-id="0f069-151">**傾向**</span><span class="sxs-lookup"><span data-stu-id="0f069-151">**Trend**</span></span>  
 <span data-ttu-id="0f069-152">KPI の傾向マークを表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-152">Displays the trend graphic of the KPI.</span></span>  
  
 <span data-ttu-id="0f069-153">**Weight**</span><span class="sxs-lookup"><span data-stu-id="0f069-153">**Weight**</span></span>  
 <span data-ttu-id="0f069-154">KPI の重み係数を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-154">Displays the weight factor of the KPI.</span></span>  
  
 <span data-ttu-id="0f069-155">**記述**</span><span class="sxs-lookup"><span data-stu-id="0f069-155">**(Description)**</span></span>  
 <span data-ttu-id="0f069-156">KPI の説明が定義されている場合は、情報アイコンを表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-156">Displays an information icon if a description is provided for a KPI.</span></span>  
  
 <span data-ttu-id="0f069-157">情報アイコン上にカーソルを配置すると、KPI を説明するツールヒントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f069-157">Hover the mouse over the information icon to display a ToolTip containing the description for the KPI.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f069-158">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンス上で KPI の計算中にエラーが発生した場合、このオプションは、エラーに関連付けられている情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f069-158">If an error occurs while calculating a KPI on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, this option displays information associated with the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f069-159">参照</span><span class="sxs-lookup"><span data-stu-id="0f069-159">See Also</span></span>  
 [<span data-ttu-id="0f069-160">Kpi &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="0f069-160">KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
