---
title: 図形グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8404c1-aa89-4350-8bd6-203bc0446ee4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8940f23c0c2b1fdabadec62de4c214c98d60b1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641449"
---
# <a name="shape-charts-report-builder-and-ssrs"></a><span data-ttu-id="e1d04-102">図形グラフ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e1d04-102">Shape Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e1d04-103">図形グラフでは、全体に占める割合 (パーセント) として値データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-103">A shape chart displays value data as percentages of a whole.</span></span> <span data-ttu-id="e1d04-104">図形グラフは、通常、セット内の異なる値間での相対的な比較を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-104">Shape charts are typically used to show proportional comparisons between different values in a set.</span></span> <span data-ttu-id="e1d04-105">カテゴリは、図形の個々のセグメントによって表されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-105">Categories are represented by individual segments of the shape.</span></span> <span data-ttu-id="e1d04-106">セグメントのサイズは、値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="e1d04-106">The size of the segment is determined by the value.</span></span> <span data-ttu-id="e1d04-107">図形グラフは円グラフに用途が似ていますが、カテゴリは大きい方から順に並べられます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-107">Shape charts are similar in use to pie charts, except that they order categories from largest to smallest.</span></span>  
  
 <span data-ttu-id="e1d04-108">じょうごグラフでは、徐々に面積が小さくなるように値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-108">A funnel chart displays values as progressively decreasing proportions.</span></span> <span data-ttu-id="e1d04-109">領域のサイズは、系列値がすべての値の合計に占める割合で決まります。</span><span class="sxs-lookup"><span data-stu-id="e1d04-109">The size of the area is determined by the series value as a percentage of the total of all values.</span></span> <span data-ttu-id="e1d04-110">たとえば、じょうごグラフを使用して、Web サイト閲覧者の傾向を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-110">For example, you might use a funnel chart to display Web site visitor trends.</span></span> <span data-ttu-id="e1d04-111">じょうごグラフでは、最上部に広い領域が表示されてホームページのヒット数を示し、他の領域はそれに比例して小さくなります。</span><span class="sxs-lookup"><span data-stu-id="e1d04-111">It is likely that the funnel chart will display a wide area at the top, indicating visitor page hits to the homepage, and the other areas will be proportionally smaller.</span></span> <span data-ttu-id="e1d04-112">じょうごグラフにデータを追加する方法の詳細については、「 [グラフ (レポート ビルダーおよび SSRS)](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1d04-112">For more information about how to add data to a funnel chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e1d04-113">次の図は、じょうごグラフの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="e1d04-113">The following illustration shows an example of a funnel chart.</span></span>  
  
 <span data-ttu-id="e1d04-114">![じょうごグラフ](../media/rs-funnelchart.gif "じょうごグラフ")</span><span class="sxs-lookup"><span data-stu-id="e1d04-114">![Funnel chart](../media/rs-funnelchart.gif "Funnel chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="e1d04-115">バリエーション</span><span class="sxs-lookup"><span data-stu-id="e1d04-115">Variations</span></span>  
  
-   <span data-ttu-id="e1d04-116">**ピラミッド**:</span><span class="sxs-lookup"><span data-stu-id="e1d04-116">**Pyramid**.</span></span> <span data-ttu-id="e1d04-117">ピラミッド グラフでは、相対的なデータが表示されるため、グラフはピラミッドのようになります。</span><span class="sxs-lookup"><span data-stu-id="e1d04-117">A pyramid chart displays proportional data so that the chart looks like a pyramid.</span></span>  
  
## <a name="data-considerations-for-shape-charts"></a><span data-ttu-id="e1d04-118">図形グラフのデータに関する注意点</span><span class="sxs-lookup"><span data-stu-id="e1d04-118">Data Considerations for Shape Charts</span></span>  
  
-   <span data-ttu-id="e1d04-119">図形グラフは、その視覚的な効果が理由で、レポートでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-119">Shape charts are popular in reports because of their visual impact.</span></span> <span data-ttu-id="e1d04-120">ただし、図形グラフは、非常に単純な種類のグラフであるため、データを最適に表すことができない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1d04-120">However, shape charts are a very simplified chart type that may not best represent your data.</span></span> <span data-ttu-id="e1d04-121">7 個以下のデータ ポイントでデータを集計した場合のみ、図形グラフの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="e1d04-121">Consider using a shape chart only once the data has been aggregated to seven data points or less.</span></span> <span data-ttu-id="e1d04-122">通常、各データ領域にカテゴリを 1 つだけ表示する場合に、図形グラフを使用します。</span><span class="sxs-lookup"><span data-stu-id="e1d04-122">In general, use the shape chart to display only one category per data region.</span></span>  
  
-   <span data-ttu-id="e1d04-123">図形グラフでは、各データ グループがグラフの個別のセグメントとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-123">Shape charts display each data group as a separate segment of the chart.</span></span> <span data-ttu-id="e1d04-124">少なくとも 1 つのデータ フィールドと 1 つのカテゴリ フィールドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1d04-124">You must add at least one data field and one category field.</span></span> <span data-ttu-id="e1d04-125">複数のデータ フィールドが図形グラフに追加されると、図形グラフでは、両方のデータ フィールドが同じグラフ内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-125">If more than one data field is added to a shape chart, the shape chart will display both data fields in the same chart.</span></span>  
  
-   <span data-ttu-id="e1d04-126">図形グラフは、全体に占める比率を整然とした順序で表現したときに最も効果を発揮します。</span><span class="sxs-lookup"><span data-stu-id="e1d04-126">Shape charts are most effective for showing proportional percentages in sorted order.</span></span> <span data-ttu-id="e1d04-127">ただし、一貫性を維持するために、既定では、データセット内の値の並べ替えが行われません。</span><span class="sxs-lookup"><span data-stu-id="e1d04-127">However, in order to maintain consistency, the chart does not sort the values in your dataset by default.</span></span> <span data-ttu-id="e1d04-128">じょうごグラフやピラミッド グラフでデータをできるだけ正確に表現するには、大きい方から順に値を並べ替えることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e1d04-128">Consider ordering your values from highest to lowest to most accurately represent your data as a funnel or a pyramid.</span></span> <span data-ttu-id="e1d04-129">詳細については、「 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1d04-129">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="e1d04-130">比率を計算する場合、NULL、空、負、および 0 の各値は無効です。</span><span class="sxs-lookup"><span data-stu-id="e1d04-130">Null, empty, negative and zero values have no effect when calculating ratios.</span></span> <span data-ttu-id="e1d04-131">このため、これらの値は図形グラフに表示されません。</span><span class="sxs-lookup"><span data-stu-id="e1d04-131">For this reason, these values are not shown on a shape chart.</span></span> <span data-ttu-id="e1d04-132">このような値をグラフ上に表示する必要がある場合は、グラフの種類を図形グラフ以外のグラフに変更してください。</span><span class="sxs-lookup"><span data-stu-id="e1d04-132">If you want to visually indicate these types of values on your chart, change the chart type to be something other than a shape chart.</span></span> <span data-ttu-id="e1d04-133">図形以外のグラフに空のポイントを追加する方法の詳細については、「[空のポイントをグラフに追加する &#40;レポートビルダーと SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1d04-133">For more information about how to add empty points to a non-shape chart, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="e1d04-134">図形グラフでカスタム パレットを使用して独自の色を定義している場合は、各データ ポイントを独自の色で強調表示するのに十分な色がパレットにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e1d04-134">If you are defining your own colors on a shape chart using a custom palette, be sure that you have enough colors in your palette to highlight each data point with its own unique color.</span></span> <span data-ttu-id="e1d04-135">詳細については、「 [グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1d04-135">For more information, see [Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="e1d04-136">図形グラフでは、その他すべてのグラフの種類と異なり、個々のデータ ポイントが凡例に表示されます。個々の系列は表示されません。</span><span class="sxs-lookup"><span data-stu-id="e1d04-136">Unlike all other chart types, a shape chart will display individual data points, and not individual series, in its legend.</span></span>  
  
-   <span data-ttu-id="e1d04-137">じょうごグラフでは、値軸およびカテゴリ軸の設定が無視されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-137">Settings for the value and category axis are ignored for funnel charts.</span></span> <span data-ttu-id="e1d04-138">複数のカテゴリ グループまたは系列グループがある場合は、グラフの凡例にグループのラベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-138">If you have multiple category or series groups, the group labels are displayed in the chart legend.</span></span>  
  
-   <span data-ttu-id="e1d04-139">図形グラフは、同じグラフ領域内で他の種類のグラフと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="e1d04-139">Shape chart types cannot be combined with any other chart type in the same chart area.</span></span> <span data-ttu-id="e1d04-140">図形グラフに表示されるデータと、他の種類のグラフに表示されるデータとの比較を示す必要がある場合は、2 つ目のグラフ領域を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1d04-140">If you have to show comparisons between data displayed on a shape chart, and data displayed on another chart type, you will need to add a second chart area.</span></span>  
  
-   <span data-ttu-id="e1d04-141">3-D 効果を追加すると、図形グラフの全体的な外観が大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="e1d04-141">Adding 3-D effects significantly improves the overall appearance of a shape chart type.</span></span>  
  
-   <span data-ttu-id="e1d04-142">視覚的な効果を高めるために、円グラフおよびドーナツ グラフに追加で描画スタイルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="e1d04-142">You can apply additional drawing styles to pie and doughnut charts for increased visual impact.</span></span> <span data-ttu-id="e1d04-143">詳細については、「[グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1d04-143">See [Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d04-144">参照</span><span class="sxs-lookup"><span data-stu-id="e1d04-144">See Also</span></span>  
 <span data-ttu-id="e1d04-145">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e1d04-145">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e1d04-146">[グラフの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e1d04-146">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e1d04-147">[グラフ内の空のデータポイントおよび Null データポイント &#40;レポートビルダーと SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e1d04-147">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e1d04-148">レポートビルダーおよび SSRS&#41;&#40;円グラフ</span><span class="sxs-lookup"><span data-stu-id="e1d04-148">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](pie-charts-report-builder-and-ssrs.md)  
  
  
