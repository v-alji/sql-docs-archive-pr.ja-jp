---
title: 縦棒グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae8c138b-e356-4ad8-862c-a4a8d0c04149
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6ebada49e65d44a2294228a3840bf4951140812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742834"
---
# <a name="column-charts-report-builder-and-ssrs"></a><span data-ttu-id="6e7ac-102">Column Charts (Report Builder and SSRS)</span><span class="sxs-lookup"><span data-stu-id="6e7ac-102">Column Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6e7ac-103">縦棒グラフでは、カテゴリ別にグループ化された縦棒のセットとして系列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-103">A column chart displays a series as a set of vertical bars that are grouped by category.</span></span> <span data-ttu-id="6e7ac-104">縦棒グラフは、時間の経過に伴うデータの変化を示す場合やアイテム間の比較を示す場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-104">Column charts are useful for showing data changes over a period of time or for illustrating comparisons among items.</span></span> <span data-ttu-id="6e7ac-105">一般的な縦棒グラフは、横棒グラフおよび範囲縦棒グラフと密接な関係にあります。横棒グラフでは、横棒のセットとして系列が表示され、範囲縦棒グラフでは、始点と終点が異なる縦棒のセットとして系列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-105">The plain column chart is closely related to the bar chart, which displays series as sets of horizontal bars, and the range column chart, which displays series as sets of vertical bars with varying beginning and end points.</span></span> <span data-ttu-id="6e7ac-106">詳細については、「 [横棒グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) 」と「 [範囲グラフ &#40;レポート ビルダーおよび SSRS&#41;](range-charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-106">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) and [Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="6e7ac-107">3 つの系列では共通の期間が共有され、有効な比較が可能になるため、このデータには縦棒グラフが適しています。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-107">The column chart is well suited for this data because all three series share a common time period, allowing for valid comparisons to be made.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations-of-a-column-chart"></a><span data-ttu-id="6e7ac-108">縦棒グラフの種類</span><span class="sxs-lookup"><span data-stu-id="6e7ac-108">Variations of a Column Chart</span></span>  
  
-   <span data-ttu-id="6e7ac-109">**積み上げ**:</span><span class="sxs-lookup"><span data-stu-id="6e7ac-109">**Stacked**.</span></span> <span data-ttu-id="6e7ac-110">複数の系列が垂直方向に積み上げられた縦棒グラフ。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-110">A column chart where multiple series are stacked vertically.</span></span> <span data-ttu-id="6e7ac-111">グラフに系列が 1 つしかない場合、積み上げ縦棒グラフでも、縦棒グラフと同じように表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-111">If there is only one series in your chart, the stacked column chart will display the same as a column chart.</span></span>  
  
-   <span data-ttu-id="6e7ac-112">**100% 積み上げ**:</span><span class="sxs-lookup"><span data-stu-id="6e7ac-112">**Percent stacked**.</span></span> <span data-ttu-id="6e7ac-113">複数の系列がグラフ領域で 100% になるように垂直方向に積み上げられた縦棒グラフ。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-113">A column chart where multiple series are stacked vertically to fit 100% of the chart area.</span></span> <span data-ttu-id="6e7ac-114">グラフに系列が 1 つしかない場合、すべての縦棒はグラフ領域で 100% になります。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-114">If there is only one series in your chart, all the column bars will fit to 100% of the chart area.</span></span>  
  
-   <span data-ttu-id="6e7ac-115">**3-D 集合**:</span><span class="sxs-lookup"><span data-stu-id="6e7ac-115">**3D clustered**.</span></span> <span data-ttu-id="6e7ac-116">各系列を 3-D グラフの個別の行で表す縦棒グラフ。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-116">A column chart that shows individual series in separate rows on a 3D chart.</span></span>  
  
-   <span data-ttu-id="6e7ac-117">**3-D 円柱**:</span><span class="sxs-lookup"><span data-stu-id="6e7ac-117">**3D cylinder**.</span></span> <span data-ttu-id="6e7ac-118">3-D グラフで棒が円柱のような形をしている縦棒グラフ。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-118">A column chart whose bars are shaped like cylinders on a 3D chart.</span></span>  
  
-   <span data-ttu-id="6e7ac-119">`Histogram`.</span><span class="sxs-lookup"><span data-stu-id="6e7ac-119">`Histogram`.</span></span> <span data-ttu-id="6e7ac-120">グラフの棒が正規分布で配置されるように計算されている縦棒グラフ。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-120">A column chart which the chart calculates so that its bars are arranged in a normal distribution.</span></span>  
  
-   <span data-ttu-id="6e7ac-121">`Pareto`.</span><span class="sxs-lookup"><span data-stu-id="6e7ac-121">`Pareto`.</span></span> <span data-ttu-id="6e7ac-122">棒が最も高い方から順に配置されている縦棒グラフ。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-122">A column chart whose bars are arranged from highest to lowest.</span></span>  
  
## <a name="data-considerations-for-a-column-chart"></a><span data-ttu-id="6e7ac-123">縦棒グラフのデータに関する注意点</span><span class="sxs-lookup"><span data-stu-id="6e7ac-123">Data Considerations for a Column Chart</span></span>  
  
-   <span data-ttu-id="6e7ac-124">横棒グラフおよび縦棒グラフは、主に、グループ間の比較を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-124">Bar and column charts are most commonly used to show comparisons between groups.</span></span> <span data-ttu-id="6e7ac-125">グラフに 4 つ以上の系列が存在する場合は、積み上げ横棒グラフまたは積み上げ縦棒グラフの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-125">If more than three series are present on the chart, consider using a stacked bar or column chart.</span></span> <span data-ttu-id="6e7ac-126">また、グラフに複数の系列がある場合は、積み上げ横棒グラフまたは積み上げ縦棒グラフを複数のグループにまとめることもできます。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-126">You can also collect stacked bar or column charts into multiple groups if you have several series on your chart.</span></span> <span data-ttu-id="6e7ac-127">詳細については、「[棒グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md)および*縦棒グラフ*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-127">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) and *Column Charts*.</span></span>  
  
-   <span data-ttu-id="6e7ac-128">縦棒グラフでは、カテゴリ軸のラベルを横方向に表示するための十分な領域がありません。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-128">In a column chart, you have less space for category axis labels to display horizontally.</span></span> <span data-ttu-id="6e7ac-129">カテゴリのラベルが長い場合は、横棒グラフを使用するか、ラベルの回転角度を変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-129">If you have longer category labels, consider using a bar chart or changing the rotation angle of the label.</span></span>  
  
-   <span data-ttu-id="6e7ac-130">縦棒グラフの各棒に特殊な描画スタイルを追加して、視覚的な効果を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-130">You can add special drawing styles to the individual bars on a column chart to increase its visual impact.</span></span> <span data-ttu-id="6e7ac-131">描画スタイルには、くさび形、エンボス、円柱、およびグラデーションがあります。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-131">Drawing styles include wedge, emboss, cylinder and light-to-dark.</span></span> <span data-ttu-id="6e7ac-132">これらの効果は、2D グラフを見やすくするためにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-132">These effects are designed to improve the appearance of your 2D chart.</span></span> <span data-ttu-id="6e7ac-133">3D グラフを使用している場合でも描画スタイルを適用できますが、同じ効果を得られないことがあります。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-133">If you are using a 3D chart, the drawing styles will still be applied, but may not have the same effect.</span></span> <span data-ttu-id="6e7ac-134">横棒グラフに描画スタイルを追加する方法の詳細については、「 [グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 &#40;レポート ビルダーおよび SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-134">For more information about how to add a drawing style to a bar chart, see [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).</span></span>  
  
-   <span data-ttu-id="6e7ac-135">グラフをヒストグラムまたはパレート グラフとして表示する機能は、縦棒グラフ固有の機能です。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-135">Unique to column charts is the ability to show your chart as a histogram or Pareto chart.</span></span> <span data-ttu-id="6e7ac-136">これを行うには、Showの Nas プロパティをに設定する `Histogram` か、 `Pareto` プロパティウィンドウでをに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="6e7ac-136">To do so, set the ShowColumnAs property to `Histogram` or `Pareto` in the Properties window to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7ac-137">参照</span><span class="sxs-lookup"><span data-stu-id="6e7ac-137">See Also</span></span>  
 <span data-ttu-id="6e7ac-138">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e7ac-138">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e7ac-139">[グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e7ac-139">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e7ac-140">[横棒グラフ (レポート ビルダーおよび SSRS)](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e7ac-140">[Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e7ac-141">[範囲グラフ &#40;レポート ビルダーおよび SSRS&#41;](range-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e7ac-141">[Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e7ac-142">[チュートリアル: レポートへの横棒グラフの追加 &#40;レポート ビルダー&#41;](../tutorial-add-a-bar-chart-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="6e7ac-142">[Tutorial: Add a Bar Chart to Your Report &#40;Report Builder&#41;](../tutorial-add-a-bar-chart-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="6e7ac-143">グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="6e7ac-143">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
