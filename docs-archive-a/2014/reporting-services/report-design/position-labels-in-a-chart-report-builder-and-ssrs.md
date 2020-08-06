---
title: グラフへのラベルの配置 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e90cbf04e0282454658e6324f0ba6600a99cb718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711609"
---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="31448-102">グラフへのラベルの配置 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="31448-102">Position Labels in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="31448-103">グラフはその種類によって形状が異なるので、グラフが見やすい位置にデータ ポイント ラベルを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31448-103">Because each chart type has a different shape, data point labels are placed in an optimal location so as not to interfere on the chart.</span></span> <span data-ttu-id="31448-104">ラベルの既定の位置は、グラフの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="31448-104">The default position of the labels depends varies with the chart type:</span></span>  
  
-   <span data-ttu-id="31448-105">積み上げグラフでは、ラベルは系列内にのみ配置できます。</span><span class="sxs-lookup"><span data-stu-id="31448-105">On stacked charts, labels can only be positioned inside the series.</span></span>  
  
-   <span data-ttu-id="31448-106">じょうごグラフまたはピラミッド グラフでは、ラベルがグラフの外側に縦一列に配置されます。</span><span class="sxs-lookup"><span data-stu-id="31448-106">On funnel or pyramid charts, labels are placed on the outside in a column.</span></span>  
  
-   <span data-ttu-id="31448-107">円グラフでは、ラベルはグラフ上の個々のスライスの内側に配置されます。</span><span class="sxs-lookup"><span data-stu-id="31448-107">On pie charts, labels are placed inside the individual slices on a pie chart.</span></span>  
  
-   <span data-ttu-id="31448-108">横棒グラフでは、ラベルは、データ ポイントを表すバーの外側に配置されます。</span><span class="sxs-lookup"><span data-stu-id="31448-108">On bar charts, labels are placed outside of the bars that represent data points.</span></span>  
  
-   <span data-ttu-id="31448-109">極座標グラフでは、データ ポイントを表す円形領域の外側にラベルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="31448-109">On polar charts, labels are placed outside of the circular area that represents data points.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a><span data-ttu-id="31448-110">円グラフ内のポイント ラベルの場所を変更するには</span><span class="sxs-lookup"><span data-stu-id="31448-110">To change the position of point labels in a Pie chart</span></span>  
  
1.  <span data-ttu-id="31448-111">円グラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="31448-111">Create a pie chart.</span></span>  
  
2.  <span data-ttu-id="31448-112">デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-112">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="31448-113">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="31448-113">Open the Properties pane.</span></span> <span data-ttu-id="31448-114">**[表示]** タブの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-114">On the **View** tab, click **Properties**.</span></span>  
  
4.  <span data-ttu-id="31448-115">デザイン画面で、グラフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-115">On the design surface, click the chart.</span></span> <span data-ttu-id="31448-116">グラフのプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="31448-116">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="31448-117">**[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="31448-117">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="31448-118">円グラフの属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31448-118">A list of attributes for the pie chart is displayed.</span></span>  
  
6.  <span data-ttu-id="31448-119">PieLabelStyle プロパティの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="31448-119">Select a value for the PieLabelStyle property.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a><span data-ttu-id="31448-120">じょうごグラフまたはピラミッド グラフ内のポイント ラベルの場所を変更するには</span><span class="sxs-lookup"><span data-stu-id="31448-120">To change the position of point labels in a Funnel or Pyramid chart</span></span>  
  
1.  <span data-ttu-id="31448-121">じょうごグラフまたはピラミッド グラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="31448-121">Create a funnel or pyramid chart.</span></span>  
  
2.  <span data-ttu-id="31448-122">デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-122">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="31448-123">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="31448-123">Open the Properties pane.</span></span> <span data-ttu-id="31448-124">**[表示]** タブの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-124">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="31448-125">デザイン画面で、グラフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-125">On the design surface, click the chart.</span></span> <span data-ttu-id="31448-126">グラフのプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="31448-126">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="31448-127">**[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="31448-127">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="31448-128">じょうごグラフの属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31448-128">A list of attributes for the funnel chart is displayed.</span></span>  
  
6.  <span data-ttu-id="31448-129">じょうごグラフの場合は、FunnelLabelStyle プロパティの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="31448-129">For a funnel chart, select a value for the FunnelLabelStyle property.</span></span> <span data-ttu-id="31448-130">ピラミッド グラフの場合は、PyramidLabelStyle プロパティの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="31448-130">For a pyramid chart, select a value for the PyramidLabelStyle property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31448-131">このプロパティを `OutsideInColumn` という値に設定した場合、ラベルは縦一列に描画されます。</span><span class="sxs-lookup"><span data-stu-id="31448-131">When this property is set to a value `OutsideInColumn`, the labels are drawn in a vertical column.</span></span> <span data-ttu-id="31448-132">列の位置を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="31448-132">There is no way to change the position of the column.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a><span data-ttu-id="31448-133">横棒グラフ内のポイント ラベルの場所を変更するには</span><span class="sxs-lookup"><span data-stu-id="31448-133">To change the position of point labels in a Bar chart</span></span>  
  
1.  <span data-ttu-id="31448-134">横棒グラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="31448-134">Create a bar chart.</span></span>  
  
2.  <span data-ttu-id="31448-135">デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-135">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="31448-136">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="31448-136">Open the Properties pane.</span></span> <span data-ttu-id="31448-137">**[表示]** タブの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-137">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="31448-138">デザイン画面で、グラフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-138">On the design surface, click the chart.</span></span> <span data-ttu-id="31448-139">グラフのプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="31448-139">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="31448-140">**[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="31448-140">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="31448-141">横棒グラフの属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31448-141">A list of attributes for the bar chart is displayed.</span></span>  
  
6.  <span data-ttu-id="31448-142">BarLabelStyle プロパティの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="31448-142">Select a value for the BarLabelStyle property.</span></span>  
  
 <span data-ttu-id="31448-143">バーのラベル スタイルが `Outside` に設定されている場合、ラベルがグラフ領域内に収まる範囲内でバーの外側に配置されます。</span><span class="sxs-lookup"><span data-stu-id="31448-143">When the bar label style is set to `Outside`, the labels will be placed outside of the bar, as long as it fits in the chart area.</span></span> <span data-ttu-id="31448-144">ラベルをバーの外側に置くことで、グラフ領域からはみ出る場合は、ラベルがバーの内側の終端部分に近接する位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="31448-144">If the label cannot be placed outside of the bar but inside of the chart area, the label is placed inside the bar at the position closest to the end of the bar.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a><span data-ttu-id="31448-145">面グラフ、縦棒グラフ、折れ線グラフ、または散布図内のポイント ラベルの場所を変更するには</span><span class="sxs-lookup"><span data-stu-id="31448-145">To change the position of point labels in an Area, Column, Line or Scatter chart</span></span>  
  
1.  <span data-ttu-id="31448-146">面グラフ、縦棒グラフ、折れ線グラフ、または散布図を作成します。</span><span class="sxs-lookup"><span data-stu-id="31448-146">Create an Area, Column, Line or Scatter chart.</span></span>  
  
2.  <span data-ttu-id="31448-147">デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-147">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="31448-148">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="31448-148">Open the Properties pane.</span></span> <span data-ttu-id="31448-149">**[表示]** タブの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-149">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="31448-150">デザイン画面で、系列をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31448-150">On the design surface, click the series.</span></span> <span data-ttu-id="31448-151">系列のプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="31448-151">The properties for the series are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="31448-152">**[データ]** セクションで、 **[DataPoint]** ノードを展開し、 **[Label]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="31448-152">In the **Data** section, expand the **DataPoint** node, then expand the **Label**node.</span></span>  
  
6.  <span data-ttu-id="31448-153">Position プロパティの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="31448-153">Select a value for the Position property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31448-154">参照</span><span class="sxs-lookup"><span data-stu-id="31448-154">See Also</span></span>  
 <span data-ttu-id="31448-155">[円グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31448-155">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31448-156">[横棒グラフ (レポート ビルダーおよび SSRS)](bar-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31448-156">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31448-157">[グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31448-157">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31448-158">[日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31448-158">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31448-159">[円グラフの外側へのデータ ポイント ラベルの表示 (レポート ビルダーおよび SSRS)](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31448-159">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="31448-160">グラフでのデータ ポイントの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="31448-160">Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  
