---
title: グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10148"
- sql12.rtp.rptdesigner.calculatedseriesproperties.axeschartareas.f1
- "10142"
- sql12.rtp.rptdesigner.axisproperties.minortickmarks.f1
- "10143"
- sql12.rtp.rptdesigner.axisproperties.labels.f1
- "10145"
- sql12.rtp.rptdesigner.axistitleproperties.font.f1
- "10139"
- sql12.rtp.rptdesigner.axisproperties.labelfont.f1
- "10140"
- sql12.rtp.rptdesigner.axisproperties.majortickmarks.f1
- sql12.rtp.rptdesigner.axisproperties.line.f1
- "10141"
helpviewer_keywords:
- "10140"
ms.assetid: ddf50dd5-5314-42ff-97f4-c3a4a17cfcdd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8811e4562681767ec53d65d869e642dfeafedae9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721147"
---
# <a name="formatting-axis-labels-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="2bdf8-102">グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2bdf8-102">Formatting Axis Labels on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2bdf8-103">座標ベースのグラフ (縦棒グラフ、横棒グラフ、面グラフ、散布図、線グラフ、および範囲グラフ) では、2 本の軸を使用してデータ間の関係を分類および表示します。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-103">Coordinate-based chart types (column, bar, area, point, line, and range) have two axes that are used to categorize and display data relationships.</span></span> <span data-ttu-id="2bdf8-104">それぞれの軸には、異なる書式が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-104">Different types of formatting will be applied to each axis.</span></span>

 <span data-ttu-id="2bdf8-105">軸の書式設定を行うには、 **[軸のプロパティ]** ダイアログ ボックスを使用するか、[プロパティ] ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-105">You can format axes by using the **Axis Properties** dialog box or by using the Properties pane.</span></span> <span data-ttu-id="2bdf8-106">書式を設定する軸を右クリックして、 **[軸のプロパティ]** をクリックし、軸のテキスト、数値と日付の形式、目盛りと補助目盛り、ラベルの自動調整、および軸線の幅、色、スタイルに関する値を変更します。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-106">Right-click the axis you want to format and click **Axis Properties** to change values for the axis text, numeric and date formats, major and minor tick marks, auto-fitting for labels, and the thickness, color, and style of the axis line.</span></span> <span data-ttu-id="2bdf8-107">軸のタイトルの値を変更するには、軸のタイトルを右クリックして、 **[軸のタイトルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-107">To change values for the axis title, right-click the axis title, and click **Axis Title Properties**.</span></span>

 <span data-ttu-id="2bdf8-108">軸ラベルによって、グラフのグリッド線の間隔が指定されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-108">Axis labels identify major intervals on the chart.</span></span> <span data-ttu-id="2bdf8-109">既定では、テキストが重ならないようラベルを軸上で適切に配置する方法を決定するためのアルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-109">By default, the chart uses an algorithm to determine how the labels should be optimally placed on the axis to avoid overlapping text.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

## <a name="types-of-axes"></a><span data-ttu-id="2bdf8-110">軸の種類</span><span class="sxs-lookup"><span data-stu-id="2bdf8-110">Types of Axes</span></span>
 <span data-ttu-id="2bdf8-111">グラフには、値軸とカテゴリ軸という 2 本の主軸があります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-111">The chart has two primary axes: the value axis and the category axis.</span></span>

 <span data-ttu-id="2bdf8-112">![グラフのカテゴリ軸と値軸](../media/rsaxes-categorical-vs-value.gif "グラフのカテゴリ軸と値軸")</span><span class="sxs-lookup"><span data-stu-id="2bdf8-112">![Chart categorical and value axes](../media/rsaxes-categorical-vs-value.gif "Chart categorical and value axes")</span></span>

 <span data-ttu-id="2bdf8-113">データセットのフィールドをグラフ上にドラッグすると、グラフでは、そのフィールドがカテゴリ軸と値軸のどちらに属するかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-113">When you drag a field from your dataset onto the chart surface, the chart will determine whether this field belongs on the category or value axis.</span></span>

 <span data-ttu-id="2bdf8-114">値軸は、通常、グラフの縦軸 (Y 軸) です。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-114">The value axis is usually the vertical axis, or y-axis, of the chart.</span></span> <span data-ttu-id="2bdf8-115">これは、グラフ化される数値データの値を表示するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-115">It is used to display numeric data values that are being charted.</span></span> <span data-ttu-id="2bdf8-116">データ フィールドの領域にドラッグされたフィールドは、値軸にプロットされます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-116">A field that is dragged into the data fields region will be plotted on the value axis.</span></span> <span data-ttu-id="2bdf8-117">カテゴリ軸は、通常、グラフの横軸 (X 軸) です。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-117">The category axis is usually the horizontal axis, or x-axis, of the chart.</span></span> <span data-ttu-id="2bdf8-118">横棒グラフの場合、これらの軸は逆になります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-118">For bar charts, these axes are reversed.</span></span> <span data-ttu-id="2bdf8-119">横棒グラフでは、カテゴリ軸が縦軸、値軸が横軸になります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-119">In bar chart types, the category axis is the vertical axis and the value axis is the horizontal axis.</span></span> <span data-ttu-id="2bdf8-120">詳細については、「 [横棒グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-120">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>

## <a name="how-the-chart-calculates-axis-label-intervals"></a><span data-ttu-id="2bdf8-121">グラフで軸ラベルの間隔を計算する方法</span><span class="sxs-lookup"><span data-stu-id="2bdf8-121">How the Chart Calculates Axis Label Intervals</span></span>
 <span data-ttu-id="2bdf8-122">軸ラベルの書式を設定する前に、グラフで軸ラベルの間隔がどのように計算されるかを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-122">Before you format axis labels, you should understand how the chart calculates axis label intervals.</span></span> <span data-ttu-id="2bdf8-123">これにより、目的とする軸のラベル付け動作を実現するのに必要なプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-123">This will enable you to set the properties necessary to achieve the axis labeling behavior that you want.</span></span>

 <span data-ttu-id="2bdf8-124">軸のスケールは、軸上に表示するデータ範囲を定義するための最小値と最大値によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-124">The axis scale is bound by a minimum and a maximum value that define the data range to be displayed along the axis.</span></span> <span data-ttu-id="2bdf8-125">グラフでは、結果セットの値に基づいて各軸の最小値と最大値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-125">The chart calculates the minimum and maximum value along each axis based on the values in your result set.</span></span> <span data-ttu-id="2bdf8-126">値軸では、スケールは常に値フィールドの最大値と最小値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-126">On the value axis, the scale will always be determined by the smallest and largest number in the value field.</span></span> <span data-ttu-id="2bdf8-127">カテゴリ軸では、最小値と最大値の型がカテゴリ フィールドの型に応じて決まります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-127">On the category axis, the minimum and maximum value types are determined depending on the type of your category field.</span></span> <span data-ttu-id="2bdf8-128">データセット内のすべてのフィールドは、カテゴリ フィールドの 3 つの型のいずれかに分類できます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-128">Any field in a dataset can be categorized into one of three category field types.</span></span> <span data-ttu-id="2bdf8-129">次の表では、カテゴリ フィールドの 3 つの型を説明しています。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-129">The following table illustrates these three types of category fields.</span></span>

|<span data-ttu-id="2bdf8-130">カテゴリ フィールドの型</span><span class="sxs-lookup"><span data-stu-id="2bdf8-130">Category Field Type</span></span>|<span data-ttu-id="2bdf8-131">説明</span><span class="sxs-lookup"><span data-stu-id="2bdf8-131">Description</span></span>|<span data-ttu-id="2bdf8-132">例</span><span class="sxs-lookup"><span data-stu-id="2bdf8-132">Example</span></span>|
|-------------------------|-----------------|-------------|
|<span data-ttu-id="2bdf8-133">数値</span><span class="sxs-lookup"><span data-stu-id="2bdf8-133">Numeric</span></span>|<span data-ttu-id="2bdf8-134">カテゴリは、X 軸に数値順にプロットされます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-134">Categories are plotted in numeric order along the x-axis.</span></span>|<span data-ttu-id="2bdf8-135">従業員の ID 番号別の売上レポートでは、従業員の ID 番号が X 軸に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-135">A sales report by employee identification number displays the employee identification numbers along the x-axis.</span></span>|
|<span data-ttu-id="2bdf8-136">Date/time</span><span class="sxs-lookup"><span data-stu-id="2bdf8-136">Date/time</span></span>|<span data-ttu-id="2bdf8-137">カテゴリは、X 軸に日時順にプロットされます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-137">Categories are plotted in chronological order along the x-axis.</span></span>|<span data-ttu-id="2bdf8-138">月別の売上レポートでは、書式設定された日付が X 軸に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-138">A sales report by month displays formatted dates along the x-axis.</span></span>|
|<span data-ttu-id="2bdf8-139">文字列</span><span class="sxs-lookup"><span data-stu-id="2bdf8-139">Strings</span></span>|<span data-ttu-id="2bdf8-140">カテゴリは、データ ソースで最初に出現した順序で X 軸にプロットされます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-140">Categories are plotted in the order it first appears in the data source along the x-axis.</span></span>|<span data-ttu-id="2bdf8-141">地域別の売上レポートでは、地域名が X 軸に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-141">A sales report by region displays region names along the x-axis.</span></span>|

 <span data-ttu-id="2bdf8-142">2 本の軸を使用するすべての種類のグラフは、カテゴリの数が多すぎて収まらない場合に、一部の軸ラベルを非表示にするようにデザインされています。これにより、グラフ内の画像が見やすくなり、ラベルの重なりが回避されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-142">All chart types with two axes are designed to suppress some axis labels when there are too many categories to fit in order to produce a cleaner image on the chart and avoid label collisions.</span></span>

 <span data-ttu-id="2bdf8-143">アプリケーションでは、次の手順に従って、軸上のラベルの位置が計算されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-143">The application calculates where labels are placed on an axis according to the following steps:</span></span>

1.  <span data-ttu-id="2bdf8-144">結果セットの値に基づいて、最小値と最大値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-144">Minimum and maximum values are identified based on the values in the result set.</span></span>

2.  <span data-ttu-id="2bdf8-145">指定された最小値と最大値に基づいて、等間隔に設定された、軸の間隔の数 (通常 4 ～ 6) が計算されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-145">An equidistant number of axis intervals, usually between four and six, are calculated based on these minimum and maximum values.</span></span>

3.  <span data-ttu-id="2bdf8-146">軸ラベルのプロパティに基づいて、ラベルがその間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-146">Based on the axis label properties, labels are displayed at these intervals.</span></span> <span data-ttu-id="2bdf8-147">ラベルの配置に影響するプロパティには、フォント サイズ、ラベルが表示される角度、およびテキストの折り返しのプロパティなどがあります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-147">Properties that affect label placement include font size, the angle at which the labels are displayed, and text wrapping properties.</span></span> <span data-ttu-id="2bdf8-148">このような軸ラベル自動調整オプションは変更できます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-148">These axis label auto-fit options can be changed.</span></span>

### <a name="example-of-how-the-chart-calculates-axis-labels"></a><span data-ttu-id="2bdf8-149">グラフの軸ラベルの計算方法の例</span><span class="sxs-lookup"><span data-stu-id="2bdf8-149">Example of How the Chart Calculates Axis Labels</span></span>
 <span data-ttu-id="2bdf8-150">次の表には、縦棒グラフにプロットされる売上データのサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-150">The table shown here contains sample sales data to be plotted on a column chart.</span></span> <span data-ttu-id="2bdf8-151">Name フィールドは [カテゴリ グループ] 領域に追加され、Quantity フィールドは [値] 領域に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-151">The Name field is added to the Category Groups area, and the Quantity field is added to the Values area.</span></span>

|<span data-ttu-id="2bdf8-152">Name</span><span class="sxs-lookup"><span data-stu-id="2bdf8-152">Name</span></span>|<span data-ttu-id="2bdf8-153">Quantity</span><span class="sxs-lookup"><span data-stu-id="2bdf8-153">Quantity</span></span>|
|----------|--------------|
|<span data-ttu-id="2bdf8-154">Michael Blythe</span><span class="sxs-lookup"><span data-stu-id="2bdf8-154">Michael Blythe</span></span>|<span data-ttu-id="2bdf8-155">229</span><span class="sxs-lookup"><span data-stu-id="2bdf8-155">229</span></span>|
|<span data-ttu-id="2bdf8-156">Jae Pak</span><span class="sxs-lookup"><span data-stu-id="2bdf8-156">Jae Pak</span></span>|<span data-ttu-id="2bdf8-157">112</span><span class="sxs-lookup"><span data-stu-id="2bdf8-157">112</span></span>|
|<span data-ttu-id="2bdf8-158">Ranjit Varkey Chudukatil</span><span class="sxs-lookup"><span data-stu-id="2bdf8-158">Ranjit Varkey Chudukatil</span></span>|<span data-ttu-id="2bdf8-159">494</span><span class="sxs-lookup"><span data-stu-id="2bdf8-159">494</span></span>|
|<span data-ttu-id="2bdf8-160">Jillian Carson</span><span class="sxs-lookup"><span data-stu-id="2bdf8-160">Jillian Carson</span></span>|<span data-ttu-id="2bdf8-161">247</span><span class="sxs-lookup"><span data-stu-id="2bdf8-161">247</span></span>|
|<span data-ttu-id="2bdf8-162">Linda Mitchell</span><span class="sxs-lookup"><span data-stu-id="2bdf8-162">Linda Mitchell</span></span>|<span data-ttu-id="2bdf8-163">339</span><span class="sxs-lookup"><span data-stu-id="2bdf8-163">339</span></span>|
|<span data-ttu-id="2bdf8-164">Rachel Valdez</span><span class="sxs-lookup"><span data-stu-id="2bdf8-164">Rachel Valdez</span></span>|<span data-ttu-id="2bdf8-165">194</span><span class="sxs-lookup"><span data-stu-id="2bdf8-165">194</span></span>|

 <span data-ttu-id="2bdf8-166">Quantity フィールドは値軸にプロットされます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-166">The Quantity field is plotted along the value -axis.</span></span> <span data-ttu-id="2bdf8-167">最小値は 112、最大値は 494 になります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-167">The lowest value is 112 and the highest value is 494.</span></span> <span data-ttu-id="2bdf8-168">この場合、スケールは 0 から始まり 500 で終わるように計算されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-168">In this case, the chart calculates the scale to start at 0 and end at 500.</span></span> <span data-ttu-id="2bdf8-169">また、等間隔に設定された 5 つの間隔が 100 と計算され、0、100、200、300、400、および 500 にラベルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-169">The chart also calculates five equidistant intervals of 100, and creates labels at 0, 100, 200, 300, 400, and 500.</span></span>

 <span data-ttu-id="2bdf8-170">Name フィールドはカテゴリ軸にプロットされます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-170">The Name field is plotted along the category axis.</span></span> <span data-ttu-id="2bdf8-171">グラフでは、4 ～ 6 個のラベルが計算され、ラベルが重ならないようにカテゴリ軸でラベルを調整する方法を決定する自動調整設定が計算されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-171">The chart calculates between four and six labels and it calculates auto-fit settings to determine how the labels can fit on the category axis without causing label collisions.</span></span> <span data-ttu-id="2bdf8-172">その結果、一部のカテゴリ ラベルは省略される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-172">As a result, some category labels might be omitted.</span></span> <span data-ttu-id="2bdf8-173">各軸の自動調整オプションを個別にオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-173">You can override auto-fitting options for each axis independently.</span></span>

## <a name="displaying-all-labels-on-the-category-axis"></a><span data-ttu-id="2bdf8-174">カテゴリ軸のすべてのラベルの表示</span><span class="sxs-lookup"><span data-stu-id="2bdf8-174">Displaying All Labels on the Category Axis</span></span>
 <span data-ttu-id="2bdf8-175">値軸では、軸の間隔により、グラフ上のデータ ポイントに一貫性のある基準が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-175">On the value axis, axis intervals provide a consistent measure of the data points on the chart.</span></span> <span data-ttu-id="2bdf8-176">ただしカテゴリ軸では、この機能により、軸ラベルなしでカテゴリが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-176">However, on the category axis, this functionality can cause categories to appear without axis labels.</span></span> <span data-ttu-id="2bdf8-177">ところが、カテゴリにはすべてラベルを付けるのが普通です。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-177">Typically, you want all categories to be labeled.</span></span> <span data-ttu-id="2bdf8-178">間隔数を 1 に設定すると、すべてのカテゴリを表示できます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-178">You can set the number of intervals to 1 to show all categories.</span></span>  <span data-ttu-id="2bdf8-179">詳細については、「 [軸の間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-179">For more information, see [Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="2bdf8-180">ラベルの自動調整機能を使用せずに手動で軸の間隔を設定した場合、これに応じてグラフでは、他のすべての要素をサイズ変更する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-180">By superseding the automatic labeling features with a manual interval on an axis, the chart must resize all other elements appropriately.</span></span> <span data-ttu-id="2bdf8-181">その結果、ラベルのサイズと配置、またはグラフ上の他の要素のサイズに関して、予期しない結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-181">As a result, you may encounter unpredictable results with the sizing and positioning of the labels, or the size of other elements on the chart.</span></span>

## <a name="variable-axis-intervals"></a><span data-ttu-id="2bdf8-182">軸の可変間隔</span><span class="sxs-lookup"><span data-stu-id="2bdf8-182">Variable Axis Intervals</span></span>
 <span data-ttu-id="2bdf8-183">グラフでは、グラフのサイズに関係なく、約 5 個の軸ラベルの間隔が計算されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-183">The chart calculates approximately five axis label intervals regardless of the size of the chart.</span></span> <span data-ttu-id="2bdf8-184">幅の広いグラフや高さのあるグラフでは、軸上にラベルが 5 個しかない場合、各ラベル間の空白部分が大きくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-184">On wider or taller charts, if you show only five labels on an axis, large gaps can appear between each label.</span></span> <span data-ttu-id="2bdf8-185">このような場合、軸に対して各データ ポイントの値を特定することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-185">This makes it more difficult to identify the value of each data point against the axis.</span></span> <span data-ttu-id="2bdf8-186">幅の広いグラフや高さのあるグラフでこの状況を回避するには、軸の可変間隔を設定できます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-186">To avoid this behavior on wider or taller charts, you can set a variable axis interval.</span></span> <span data-ttu-id="2bdf8-187">グラフでは、対応する軸に応じ、グラフの幅または高さに基づいて、軸に表示されるラベルの最適な数が計算されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-187">The chart will calculate the optimal number of labels that can appear on the axis based on the width or height of the chart, depending on the corresponding axis.</span></span> <span data-ttu-id="2bdf8-188">詳細については、「 [軸の間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-188">For more information, see [Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md).</span></span>

## <a name="sorting-axis-values"></a><span data-ttu-id="2bdf8-189">軸の値の並べ替え</span><span class="sxs-lookup"><span data-stu-id="2bdf8-189">Sorting Axis Values</span></span>
 <span data-ttu-id="2bdf8-190">カテゴリは、結果セットに出現する順序で X 軸に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-190">Categories appear along the x-axis in the order that they appear in the result set.</span></span> <span data-ttu-id="2bdf8-191">グループの順序を変更するには、SORT コマンドをクエリに追加するか、式を使用してデータセットを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-191">You can change the group order by adding a SORT command to the query or by sorting the dataset using an expression.</span></span> <span data-ttu-id="2bdf8-192">グラフ データ領域は、その他のすべてのデータ領域と同じように並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-192">Chart data regions are sorted the same as all other data regions.</span></span> <span data-ttu-id="2bdf8-193">データを並べ替える方法の詳細については、「[データ領域内のデータの並べ替え &#40;レポート ビルダーおよび SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-193">For more information about how to sort data, see [Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md).</span></span>

## <a name="specifying-scalar-values-on-the-category-axis"></a><span data-ttu-id="2bdf8-194">カテゴリ軸でのスカラー値の指定</span><span class="sxs-lookup"><span data-stu-id="2bdf8-194">Specifying Scalar Values on the Category Axis</span></span>
 <span data-ttu-id="2bdf8-195">既定では、グラフに表示されるのは、有効な値が含まれているデータセット内のデータ ポイントに対する軸ラベルだけです。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-195">By default, the chart will only display axis labels for data points in the dataset that contain valid values.</span></span> <span data-ttu-id="2bdf8-196">たとえば、カテゴリ軸に 1、2、6 という値を設定した場合、グラフには 1、2、6 というカテゴリのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-196">For example, if you have values of 1, 2, and 6 on the category axis, the chart will only show categories 1, 2, and 6.</span></span> <span data-ttu-id="2bdf8-197">カテゴリ値のスケールを保つために、グラフでスカラー軸が使用されるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-197">To maintain the scale of category values, you can specify the chart to use a scalar axis.</span></span> <span data-ttu-id="2bdf8-198">この場合は、データセットに 3 ～ 5 の値が含まれていなくても、グラフの X 軸に 1 ～ 6 のラベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-198">In this scenario, the chart will show labels for 1-6 on the x-axis of the chart, even though your dataset does not contain values for 3-5.</span></span>

 <span data-ttu-id="2bdf8-199">スカラー軸を設定するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-199">There are two ways to set a scalar axis:</span></span>

-   <span data-ttu-id="2bdf8-200">**[軸のプロパティ]** ダイアログ ボックスの **[スカラー軸]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-200">Select the **Scalar axis** option in the **Axis Properties** dialog box.</span></span> <span data-ttu-id="2bdf8-201">これにより軸上で、データをグループ化する値が存在しない箇所に、数値または日付/時刻値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-201">This will add numeric or date/time values to the axis where no data grouping values exist.</span></span> <span data-ttu-id="2bdf8-202">詳細については、「[[軸のプロパティ] ダイアログ ボックス、[軸のオプション] &#40;レポート ビルダーおよび SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-202">For more information, see [Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md).</span></span>

-   <span data-ttu-id="2bdf8-203">**[系列のプロパティ]** ダイアログ ボックスの **[カテゴリ フィールド]** オプションで、フィールドを選択するか、式を入力します。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-203">Select a field or type an expression for the **Category field** option in the **Series Properties** dialog box.</span></span> <span data-ttu-id="2bdf8-204">グラフでは、指定したカテゴリ フィールドのすべての値に対して軸の間隔が追加されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-204">The chart will add axis intervals for all values in the category field you specified.</span></span>

## <a name="adding-or-removing-side-margins-from-the-category-axis"></a><span data-ttu-id="2bdf8-205">カテゴリ軸の横余白の追加または削除</span><span class="sxs-lookup"><span data-stu-id="2bdf8-205">Adding or Removing Side Margins from the Category Axis</span></span>
 <span data-ttu-id="2bdf8-206">横棒グラフ、縦棒グラフ、および散布図では、横余白が X 軸の両端に自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-206">In Bar, Column and Scatter chart types, the chart automatically adds side margins on the ends of the x-axis.</span></span> <span data-ttu-id="2bdf8-207">余白のサイズは変更できません。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-207">You cannot change the size of the margin.</span></span> <span data-ttu-id="2bdf8-208">その他すべての種類のグラフでは、横余白は追加されません。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-208">In all other chart types, the chart does not add side margins.</span></span> <span data-ttu-id="2bdf8-209">詳細については、「 [グラフの余白の追加または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2bdf8-209">For more information, see [Add or Remove Margins from a Chart &#40;Report Builder and SSRS&#41;](add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2bdf8-210">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2bdf8-210">In This Section</span></span>
 [<span data-ttu-id="2bdf8-211">日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2bdf8-211">Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;</span></span>](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)

 [<span data-ttu-id="2bdf8-212">グラフへのラベルの配置 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2bdf8-212">Position Labels in a Chart &#40;Report Builder and SSRS&#41;</span></span>](position-labels-in-a-chart-report-builder-and-ssrs.md)

 [<span data-ttu-id="2bdf8-213">軸の間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2bdf8-213">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)

 [<span data-ttu-id="2bdf8-214">グラフの余白の追加または削除 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2bdf8-214">Add or Remove Margins from a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)

 [<span data-ttu-id="2bdf8-215">対数スケールの指定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2bdf8-215">Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;</span></span>](specify-a-logarithmic-scale-report-builder-and-ssrs.md)

## <a name="see-also"></a><span data-ttu-id="2bdf8-216">参照</span><span class="sxs-lookup"><span data-stu-id="2bdf8-216">See Also</span></span>
 <span data-ttu-id="2bdf8-217">[グラフの書式設定 &#40;レポートビルダーと ssrs&#41;](formatting-a-chart-report-builder-and-ssrs.md)グラフ[&#40;レポートビルダーと](charts-report-builder-and-ssrs.md)ssrs&#41;[グラフでのデータポイントの書式設定 &#40;レポートビルダーと ssrs&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="2bdf8-217">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)</span></span>

