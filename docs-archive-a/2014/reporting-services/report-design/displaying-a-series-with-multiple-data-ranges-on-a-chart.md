---
title: グラフ上の複数のデータ範囲を持つ系列の表示 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 45da3d39-278e-4760-a4b3-9932c9547cf2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dfe378f3fb5aa50ddf02f95b2b4be04dd1ae6ac5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632899"
---
# <a name="displaying-a-series-with-multiple-data-ranges-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="dc661-102">グラフ上で複数のデータ範囲を持つ系列の表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="dc661-102">Displaying a Series with Multiple Data Ranges on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dc661-103">グラフでは、軸のスケールを計算するために、系列の最小値と最大値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="dc661-103">Chart will use the minimum and maximum values of a series to calculate the axis scale.</span></span> <span data-ttu-id="dc661-104">グラフ上の系列に複数のデータ範囲が含まれていると、データ ポイントが重なり合って、少数のデータ ポイントしかグラフ上ではっきりと見えない場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc661-104">When a series on your chart contains more than one range of data, the data points can become obscured, and only a few data points to be seen easily on the chart.</span></span> <span data-ttu-id="dc661-105">たとえば、毎日の売上合計を 30 日分表示するレポートがあるとします。</span><span class="sxs-lookup"><span data-stu-id="dc661-105">For example, suppose a report displays daily sales totals over a period of 30 days.</span></span>  
  
 <span data-ttu-id="dc661-106">![複数のデータ範囲のグラフ](../media/rs-multipledatarangeschart.gif "複数のデータ範囲のグラフ")</span><span class="sxs-lookup"><span data-stu-id="dc661-106">![Chart with multiple data ranges](../media/rs-multipledatarangeschart.gif "Chart with multiple data ranges")</span></span>  
  
 <span data-ttu-id="dc661-107">この月のほとんどの日の売上は 10 ～ 40 です。</span><span class="sxs-lookup"><span data-stu-id="dc661-107">For most of the month, the sales are between 10 and 40.</span></span> <span data-ttu-id="dc661-108">しかし、1 週間実施されたセールス マーケティング キャンペーンのおかげで、売上は 4 月の初めに急増しました。</span><span class="sxs-lookup"><span data-stu-id="dc661-108">However, a one-week sales marketing campaign has caused a sudden sales increase at the beginning of April.</span></span> <span data-ttu-id="dc661-109">売上データがこのように変化したため、データ ポイントの分布が不均一になり、グラフが全般的に読みにくくなっています。</span><span class="sxs-lookup"><span data-stu-id="dc661-109">This change in sales data produces an uneven distribution of data points that reduces the overall readability of the chart.</span></span>  
  
 <span data-ttu-id="dc661-110">グラフの読みやすさは、以下のいずれかの方法で向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="dc661-110">There are different ways to improve readability:</span></span>  
  
-   <span data-ttu-id="dc661-111">**スケールの区切り線を有効にする**:</span><span class="sxs-lookup"><span data-stu-id="dc661-111">**Enable scale breaks**.</span></span> <span data-ttu-id="dc661-112">データが 2 つ以上のデータ範囲を形成している場合は、スケール区切りを使用して、範囲間のすきまを削除します。</span><span class="sxs-lookup"><span data-stu-id="dc661-112">If your data forms two or more sets of data ranges, use a scale break to remove the gap between the ranges.</span></span> <span data-ttu-id="dc661-113">スケール区切りは、プロット エリアに描画される線であり、系列の高値と低値の間の区切りを示します。</span><span class="sxs-lookup"><span data-stu-id="dc661-113">A scale break is a stripe drawn across the plotting area to denote a break between the high and low values of a series.</span></span>  
  
-   <span data-ttu-id="dc661-114">**不要な値を除外する**:</span><span class="sxs-lookup"><span data-stu-id="dc661-114">**Filter out unnecessary values**.</span></span> <span data-ttu-id="dc661-115">グラフ上に表示する必要のある重要なデータ範囲を覆っているデータ ポイントがある場合は、レポート フィルターを使用して、不要なポイントを削除します。</span><span class="sxs-lookup"><span data-stu-id="dc661-115">If you have data points that are obscuring the important data range to be displayed on the chart, remove the unwanted points using a report filter.</span></span> <span data-ttu-id="dc661-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のグラフにフィルターを追加する方法の詳細については、｢[データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc661-116">For information on how to add a filter to the chart in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
-   <span data-ttu-id="dc661-117">**各データ範囲を複数の系列を比較するための別々の系列としてプロットする**:</span><span class="sxs-lookup"><span data-stu-id="dc661-117">**Plot each data range as a separate series for multiple series comparison**.</span></span> <span data-ttu-id="dc661-118">データ範囲が 3 つ以上ある場合は、各データ範囲を別々の系列に分離すると効果的です。</span><span class="sxs-lookup"><span data-stu-id="dc661-118">If you have more than two data ranges, consider separating the data ranges into separate series.</span></span> <span data-ttu-id="dc661-119">詳細については、「 [グラフ上の複数の系列 (レポート ビルダーおよび SSRS)](multiple-series-on-a-chart-report-builder-and-ssrs.md):</span><span class="sxs-lookup"><span data-stu-id="dc661-119">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-multiple-data-ranges-using-scale-breaks"></a><span data-ttu-id="dc661-120">スケール区切りを使用した複数のデータ範囲の表示</span><span class="sxs-lookup"><span data-stu-id="dc661-120">Displaying Multiple Data Ranges Using Scale Breaks</span></span>  
 <span data-ttu-id="dc661-121">スケール区切りを有効にすると、グラフ内のどこに区切り線を描画するかが自動的に計算されます。</span><span class="sxs-lookup"><span data-stu-id="dc661-121">When you enable a scale break, the chart calculates where to draw a line across the chart.</span></span> <span data-ttu-id="dc661-122">データ範囲間の距離がスケール区切りを描画するのに十分であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="dc661-122">You must have sufficient separation between ranges to draw a scale break.</span></span> <span data-ttu-id="dc661-123">既定では、スケール区切りを追加できるのは、データ範囲間の距離がグラフ全体の 25% 以上である場合のみです。</span><span class="sxs-lookup"><span data-stu-id="dc661-123">By default, a scale break can be added only if there is a separation between the data ranges of at least 25% of the chart.</span></span>  
  
 <span data-ttu-id="dc661-124">![スケール区切り付きのグラフ](../media/rs-multipledatarangeschart-scalebreak.gif "スケール区切り付きのグラフ")</span><span class="sxs-lookup"><span data-stu-id="dc661-124">![Chart with scale break](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc661-125">グラフ上でスケール区切りを配置する場所を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="dc661-125">You cannot specify where to place a scale break on a chart.</span></span> <span data-ttu-id="dc661-126">ただし、このトピックで後述するように、スケール区切りの計算方法は変更できます。</span><span class="sxs-lookup"><span data-stu-id="dc661-126">You can, however, modify how the scale break is calculated, described later in this topic.</span></span>  
  
 <span data-ttu-id="dc661-127">スケール区切りを有効にし、データ範囲間の距離が十分であるにもかかわらず、スケール区切りが表示されない場合は、CollapsibleSpaceThreshold プロパティを 25 未満の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="dc661-127">If you enable a scale break but it does not appear, even though there is sufficient distance between the data ranges, you can set the CollapsibleSpaceThreshold property to a value less than 25.</span></span> <span data-ttu-id="dc661-128">CollapsibleSpaceThreshold には、データ範囲間に必要な縮小可能領域の割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc661-128">The CollapsibleSpaceThreshold specifies the percent of collapsible space required between the data ranges.</span></span> <span data-ttu-id="dc661-129">詳細については、「[空のポイントのグラフへの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc661-129">For more information, see [Add Scale Breaks to a Chart &#40;Report Builder and SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="dc661-130">グラフ 1 つあたり最大 5 個のスケール区切りがサポートされています。ただし、複数のスケール区切りを表示すると、グラフが読みにくくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc661-130">Charts support up to five scale breaks per chart; however, displaying more than one scale break can cause the chart to become unreadable.</span></span> <span data-ttu-id="dc661-131">データ範囲が 3 つ以上ある場合は、別の方法でデータを表示することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="dc661-131">If you have more than two data ranges, consider using a different method for displaying this data.</span></span> <span data-ttu-id="dc661-132">詳細については、「 [グラフ上の複数の系列 (レポート ビルダーおよび SSRS)](multiple-series-on-a-chart-report-builder-and-ssrs.md):</span><span class="sxs-lookup"><span data-stu-id="dc661-132">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="unsupported-scale-break-scenarios"></a><span data-ttu-id="dc661-133">サポートされていないスケール区切りのシナリオ</span><span class="sxs-lookup"><span data-stu-id="dc661-133">Unsupported Scale Break Scenarios</span></span>  
 <span data-ttu-id="dc661-134">以下の場合はスケール区切りを使用できません。</span><span class="sxs-lookup"><span data-stu-id="dc661-134">Scale breaks are not supported in the following chart scenarios:</span></span>  
  
-   <span data-ttu-id="dc661-135">グラフで 3-D が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="dc661-135">The chart is 3-D enabled.</span></span>  
  
-   <span data-ttu-id="dc661-136">軸の値として対数が指定されている場合</span><span class="sxs-lookup"><span data-stu-id="dc661-136">A logarithmic value axis has been specified.</span></span>  
  
-   <span data-ttu-id="dc661-137">値軸の最大値または最小値が明示的に設定されている場合</span><span class="sxs-lookup"><span data-stu-id="dc661-137">The value axis minimum or maximum has been explicitly set.</span></span>  
  
-   <span data-ttu-id="dc661-138">グラフの種類が極座標グラフ、レーダー グラフ、円グラフ、ドーナツ グラフ、じょうごグラフ、ピラミッド グラフ、または積み上げグラフである場合</span><span class="sxs-lookup"><span data-stu-id="dc661-138">The chart type is polar, radar, pie, doughnut, funnel, pyramid, or any stacked chart.</span></span>  
  
 <span data-ttu-id="dc661-139">スケール区切り付きのグラフについては、サンプル レポートに例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc661-139">An example of chart with scale breaks is available as a sample report.</span></span> <span data-ttu-id="dc661-140">このサンプルレポートのダウンロードの詳細については、「 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [サンプルレポートのレポートビルダーとレポートデザイナー](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc661-140">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc661-141">参照</span><span class="sxs-lookup"><span data-stu-id="dc661-141">See Also</span></span>  
 <span data-ttu-id="dc661-142">[グラフ上の複数の系列 &#40;レポートビルダーと SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc661-142">[Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dc661-143">[グラフの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc661-143">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dc661-144">[グラフに対する3D、傾斜、およびその他の効果 &#40;レポートビルダーと SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="dc661-144">[3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span></span>  
 <span data-ttu-id="dc661-145">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc661-145">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dc661-146">[[軸のオプション] ([軸のプロパティ] ダイアログボックス) &#40;レポートビルダーと SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc661-146">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dc661-147">円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="dc661-147">Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
