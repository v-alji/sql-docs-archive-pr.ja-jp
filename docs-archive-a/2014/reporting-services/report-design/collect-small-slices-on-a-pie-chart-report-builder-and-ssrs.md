---
title: 円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2302217843864115847aeb544d1c64727b8ad3a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641463"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="02dab-102">円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="02dab-102">Collect Small Slices on a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="02dab-103">円グラフに表示されるデータ ポイントが多すぎると、円グラフの外観が煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="02dab-103">When pie charts display too many points of data, they begin to look cluttered.</span></span> <span data-ttu-id="02dab-104">この問題を解決するため、特定の値を下回るすべてのデータを、円グラフ上の 1 つのスライスとして表示できます。</span><span class="sxs-lookup"><span data-stu-id="02dab-104">To resolve this issue, you can show all data that falls beneath a certain value as one slice on the pie chart.</span></span>  
  
 <span data-ttu-id="02dab-105">小さいスライスを 1 つのスライスにまとめるには、まず小さいスライスを収集するためのしきい値を円グラフに対する比率と固定値のどちらで表すかを決定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-105">To collect small slices into one slice, first decide whether your threshold for collecting small slices is measured as a percentage of the pie chart or as a fixed value.</span></span> <span data-ttu-id="02dab-106">次に、[CollectedThreshold] と [CollectedThresholdUsePercent] プロパティを設定します。[CollectedThreshold] プロパティを、収集する値が必ず下回るグラフのパーセンテージ、またはコレクションの実際のしきい値データの値のいずれかに設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-106">Then set the CollectedThreshold and CollectedThresholdUsePercent properties.Set the CollectedThreshold property to either the percentage of the chart that a value must fall below to be collected, or the actual threshold data value for collection.</span></span> <span data-ttu-id="02dab-107">パーセントを使用するか、実際の値を使用するには、Collectedthresholdusepercent] プロパティをに設定し `True` `False` ます。</span><span class="sxs-lookup"><span data-stu-id="02dab-107">Set the CollectedThresholdUsePercent property to `True` to use a percentage or `False` to use an actual value.</span></span>  
  
 <span data-ttu-id="02dab-108">小さいスライスは、1 つ目の円グラフでまとめられたスライスから切り離し、2 つ目の円グラフにまとめることもできます。</span><span class="sxs-lookup"><span data-stu-id="02dab-108">You can also collect small slices into a second pie chart that is called out from a collected slice of the first pie chart.</span></span> <span data-ttu-id="02dab-109">2 つ目の円グラフは元の円グラフの右側に描画されます。</span><span class="sxs-lookup"><span data-stu-id="02dab-109">The second pie chart is drawn to the right of the original pie chart.</span></span>  
  
 <span data-ttu-id="02dab-110">じょうごグラフまたはピラミッド グラフのスライスを 1 つのスライスに結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="02dab-110">You cannot combine slices of funnel or pyramid charts into one slice.</span></span>  
  
 <span data-ttu-id="02dab-111">このグラフについては、サンプル レポートに例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="02dab-111">An example of this chart is available as a sample report.</span></span> <span data-ttu-id="02dab-112">このサンプルレポートのダウンロードの詳細については、「 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [サンプルレポートのレポートビルダーとレポートデザイナー](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02dab-112">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a><span data-ttu-id="02dab-113">円グラフの小さいスライスを 1 つのスライスにまとめるには</span><span class="sxs-lookup"><span data-stu-id="02dab-113">To collect small slices into a single slice on a pie chart</span></span>  
  
1.  <span data-ttu-id="02dab-114">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="02dab-114">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="02dab-115">デザイン画面で、円グラフの任意のスライスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="02dab-115">On the design surface, click on any slice of the pie chart.</span></span> <span data-ttu-id="02dab-116">系列のプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="02dab-116">The properties for the series are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="02dab-117">**[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="02dab-117">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="02dab-118">[CollectedStyle] プロパティを **[SingleSlice]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-118">Set the CollectedStyle property to **SingleSlice**.</span></span>  
  
5.  <span data-ttu-id="02dab-119">収集されるしきい値としきい値の種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-119">Set the collected threshold value and type of threshold.</span></span> <span data-ttu-id="02dab-120">次の例は、収集されるしきい値を設定する一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="02dab-120">The following examples are common ways of setting collected thresholds.</span></span>  
  
    -   <span data-ttu-id="02dab-121">**比率で設定します。**</span><span class="sxs-lookup"><span data-stu-id="02dab-121">**By percentage.**</span></span> <span data-ttu-id="02dab-122">たとえば、円グラフ上の 10% 未満の小さいスライスを 1 つのスライスにまとめるには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="02dab-122">For example, to collect any slice on your pie chart that is less than 10% into a single slice:</span></span>  
  
         <span data-ttu-id="02dab-123">Collectedthresholdusepercent] プロパティをに設定し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="02dab-123">Set the CollectedThresholdUsePercent property to `True`.</span></span>  
  
         <span data-ttu-id="02dab-124">[CollectedThreshold] プロパティを **10**に設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-124">Set the CollectedThreshold property to **10**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="02dab-125">[Collectedstyle] を **[singleslice]** に設定し、CollectedThreshold を**100**より大きい値に設定し、collectedthresholdusepercent] がである場合、 `True` グラフではパーセンテージを計算できないため、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="02dab-125">If you set CollectedStyle to **SingleSlice**, CollectedThreshold to a value greater than **100**, and CollectedThresholdUsePercent is `True`, the chart will throw an exception because it cannot calculate a percentage.</span></span> <span data-ttu-id="02dab-126">この問題を解決するには、[CollectedThreshold] を **100** 未満の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-126">To resolve this issue, set the CollectedThreshold to a value less than **100**.</span></span>  
  
    -   <span data-ttu-id="02dab-127">**データ値で設定します。**</span><span class="sxs-lookup"><span data-stu-id="02dab-127">**By data value.**</span></span> <span data-ttu-id="02dab-128">たとえば、円グラフ上の 5,000 未満の小さいスライスを 1 つのスライスにまとめるには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="02dab-128">For example, to collect any slice on your pie chart that is less than 5000 into a single slice:</span></span>  
  
         <span data-ttu-id="02dab-129">Collectedthresholdusepercent] プロパティをに設定し `False` ます。</span><span class="sxs-lookup"><span data-stu-id="02dab-129">Set the CollectedThresholdUsePercent property to `False`.</span></span>  
  
         <span data-ttu-id="02dab-130">[CollectedThreshold] プロパティを **5000**に設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-130">Set the CollectedThreshold property to **5000**.</span></span>  
  
6.  <span data-ttu-id="02dab-131">[CollectedLabel] プロパティを、収集されたスライスに表示されるテキスト ラベルを表す文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-131">Set the CollectedLabel property to a string that represents the text label that will be shown on the collected slice.</span></span>  
  
7.  <span data-ttu-id="02dab-132">(省略可) CollectedSliceExploded、CollectedColor、CollectedLegendText および CollectedToolTip の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-132">(Optional) Set the CollectedSliceExploded, CollectedColor, CollectedLegendText and CollectedToolTip properties.</span></span> <span data-ttu-id="02dab-133">これらのプロパティでは、1 つのスライスの外観、色、ラベルのテキスト、凡例のテキスト、およびツールヒントを変更します。</span><span class="sxs-lookup"><span data-stu-id="02dab-133">These properties change the appearance, color, label text, legend text and tooltip aspects of the single slice.</span></span>  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a><span data-ttu-id="02dab-134">小さいスライスをまとめた 2 つ目の円グラフにするには</span><span class="sxs-lookup"><span data-stu-id="02dab-134">To collect small slices into a secondary, callout pie chart</span></span>  
  
1.  <span data-ttu-id="02dab-135">上記の手順 1. ～ 3. を実行します。</span><span class="sxs-lookup"><span data-stu-id="02dab-135">Follow Steps 1-3 from above.</span></span>  
  
2.  <span data-ttu-id="02dab-136">[CollectedStyle] プロパティを **[CollectedPie]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-136">Set the CollectedStyle property to **CollectedPie**.</span></span>  
  
3.  <span data-ttu-id="02dab-137">[CollectedThreshold] プロパティを、小さいスライスを 1 つのスライスにまとめる基準となるしきい値を表す値に設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-137">Set the CollectedThresholdproperty to a value that represents the threshold at which small slices will be collected into one slice.</span></span> <span data-ttu-id="02dab-138">[Collectedstyle] プロパティが**CollectedPie**に設定されている場合、CollectedThresholdUsePercentproperty は常にに設定され、 `True` 収集されるしきい値は常に比率で計測されます。</span><span class="sxs-lookup"><span data-stu-id="02dab-138">When the CollectedStyle property is set to **CollectedPie**, the CollectedThresholdUsePercentproperty is always set to `True`, and the collected threshold is always measured in percent.</span></span>  
  
4.  <span data-ttu-id="02dab-139">(省略可) CollectedColor、CollectedLabel、CollectedLegendText および CollectedToolTip の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="02dab-139">(Optional) Set the CollectedColor, CollectedLabel, CollectedLegendText and CollectedToolTip properties.</span></span> <span data-ttu-id="02dab-140">"Collected" という名前を持つその他すべてのプロパティは、まとめられた円に適用されません。</span><span class="sxs-lookup"><span data-stu-id="02dab-140">All other properties named "Collected" do not apply to the collected pie.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02dab-141">2 つ目の円グラフは、データの中の小さいスライスに基づいて計算され、プレビューのみに表示されます。</span><span class="sxs-lookup"><span data-stu-id="02dab-141">The secondary pie chart is calculated based on the small slices in your data so it will only appear in Preview.</span></span> <span data-ttu-id="02dab-142">この円グラフはデザイン画面には表示されません。</span><span class="sxs-lookup"><span data-stu-id="02dab-142">It does not appear on the design surface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02dab-143">2 つ目の円グラフの書式は設定できません。</span><span class="sxs-lookup"><span data-stu-id="02dab-143">You cannot format the secondary pie chart.</span></span> <span data-ttu-id="02dab-144">このため、円スライスを収集する際は最初の方法を使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="02dab-144">For this reason, it is strongly recommended to use the first approach when collecting pie slices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02dab-145">参照</span><span class="sxs-lookup"><span data-stu-id="02dab-145">See Also</span></span>  
 <span data-ttu-id="02dab-146">[レポートビルダーおよび SSRS&#41;&#40;円グラフ](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02dab-146">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="02dab-147">[グラフ上のデータポイントの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02dab-147">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="02dab-148">[レポートビルダーおよび SSRS&#41;&#40;円グラフの外側にデータポイントラベルを表示する](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02dab-148">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="02dab-149">[レポートビルダーおよび SSRS&#41;&#40;円グラフにパーセンテージ値を表示する](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02dab-149">[Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="02dab-150">グラフへの 3D 効果の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="02dab-150">Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-3d-effects-report-builder.md)  
  
  
