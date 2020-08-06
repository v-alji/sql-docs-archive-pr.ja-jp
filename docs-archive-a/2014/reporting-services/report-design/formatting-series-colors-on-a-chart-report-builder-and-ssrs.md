---
title: グラフの系列の色の書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10245"
- "10252"
- sql12.rtp.rptdesigner.serieslabelproperties.borders.f1
- sql12.rtp.rptdesigner.seriesproperties.borders.f1
ms.assetid: fe541501-cac5-47b1-b95f-c410db789190
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0e4f526e32ba38b94c5707c1ce3acc3cd073626
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711677"
---
# <a name="formatting-series-colors-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="4b63c-102">グラフの系列の色の書式設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4b63c-102">Formatting Series Colors on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4b63c-103">Reporting Services にはグラフ用にいくつかの組み込みパレットが用意されていますが、カスタム パレットを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-103">Reporting Services provides several built-in palettes for charts, or you can define a custom palette.</span></span> <span data-ttu-id="4b63c-104">既定では、グラフは組み込みの**BrightPastel**カラーパレットを使用して各系列を塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="4b63c-104">By default, charts use the built-in **BrightPastel** color palette to fill each series.</span></span> <span data-ttu-id="4b63c-105">これらの色は、凡例にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-105">These colors also appear in the legend.</span></span> <span data-ttu-id="4b63c-106">複数の系統をグラフに追加すると、グラフでは、パレットで定義されている色の順序で系統に色が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-106">When multiple series are added to the chart, the chart assigns the series a color in the order that the colors have been defined in the palette.</span></span>  
  
 <span data-ttu-id="4b63c-107">パレットにある色の数より系統の数が多い場合、グラフで色が再利用され、2 つの系統で同じ色が使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="4b63c-107">If there are a greater number of series than there are colors in the palette, the chart will begin reusing colors, and two series may have the same color.</span></span> <span data-ttu-id="4b63c-108">このような状態は、各データ ポイントにパレットから色が割り当てられる、図形グラフを使用する場合に頻繁に起こります。</span><span class="sxs-lookup"><span data-stu-id="4b63c-108">This frequently occurs if you are using a Shape chart, where each data point is assigned a color from the palette.</span></span> <span data-ttu-id="4b63c-109">混同を避けるために、グラフの系列数と少なくとも同じ数の色を使用してカスタム パレットを定義してください。</span><span class="sxs-lookup"><span data-stu-id="4b63c-109">To avoid confusion, define a custom palette with at least the same number of colors as you have series on your chart.</span></span>  
  
 <span data-ttu-id="4b63c-110">新しいパレットを選択することも、プロパティ ペインからカスタム パレットを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-110">You can select a new palette or define a custom palette from the Properties pane.</span></span> <span data-ttu-id="4b63c-111">詳細については、「[パレットを使用したグラフの色の定義 &#40;レポート ビルダーおよび SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b63c-111">For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-built-in-palettes"></a><span data-ttu-id="4b63c-112">組み込みパレットの使用</span><span class="sxs-lookup"><span data-stu-id="4b63c-112">Using Built-In Palettes</span></span>  
 <span data-ttu-id="4b63c-113">Reporting Services には、定義済みの組み込みパレットの一覧が用意されています。この組み込みパレットを使用して、グラフの系統に設定する色を定義できます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-113">Reporting Services provides a list of predefined, built-in palettes that you can use to define a color set for series on your chart.</span></span> <span data-ttu-id="4b63c-114">すべての組み込みパレットには、10 ～ 16 色の値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b63c-114">All built-in palettes contain between 10 and 16 color values.</span></span> <span data-ttu-id="4b63c-115">組み込みパレットを拡張してさらに色を追加することはできません。このため、17 色以上が必要な場合は、カスタム パレットを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b63c-115">You cannot extend the built-in palette to include more colors, so if you need more than 16 colors, you must define a custom palette.</span></span>  
  
 <span data-ttu-id="4b63c-116">レポートを印刷する場合、 **[グレースケール]** パレットの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="4b63c-116">If you are printing a report, consider using the **Greyscale** palette.</span></span> <span data-ttu-id="4b63c-117">このパレットでは、白と黒の影を使用してグラフの各系統を表します。</span><span class="sxs-lookup"><span data-stu-id="4b63c-117">This palette uses shades of black and white to represent each series in a chart.</span></span>  
  
 <span data-ttu-id="4b63c-118">以前のバージョンの Reporting Services では、[既定] という名前のパレットが既定のグラフ パレットとして使用されていました。</span><span class="sxs-lookup"><span data-stu-id="4b63c-118">The palette named Default was used as the default chart palette in earlier versions of Reporting Services.</span></span> <span data-ttu-id="4b63c-119">既定のグラフ パレットは同じ名前で維持され、一貫性が保たれています。</span><span class="sxs-lookup"><span data-stu-id="4b63c-119">It has been maintained with the same name for consistency.</span></span> <span data-ttu-id="4b63c-120">グラフは、[既定] パレットを使用してシームレスにアップグレードされますが、アップグレード後は名前を変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4b63c-120">Charts will upgrade seamlessly using the Default palette, but after upgrading, you might consider changing it.</span></span>  
  
## <a name="using-custom-palettes"></a><span data-ttu-id="4b63c-121">カスタム パレットの使用</span><span class="sxs-lookup"><span data-stu-id="4b63c-121">Using Custom Palettes</span></span>  
 <span data-ttu-id="4b63c-122">グラフに独自の色を適用する場合は、カスタム パレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b63c-122">If you want to apply your own colors to the chart, use a custom palette.</span></span> <span data-ttu-id="4b63c-123">カスタム パレットを使用すると、グラフに表示される順序で独自の色を追加できます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-123">A custom palette let you add your own colors in the order you want them to appear on the chart.</span></span> <span data-ttu-id="4b63c-124">カスタム パレットは、グラフの系列の数がデザイン時に不明な場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-124">A custom palette is especially helpful if the number of series in your chart is unknown at design time.</span></span> <span data-ttu-id="4b63c-125">詳細については、「[パレットを使用したグラフの色の定義 &#40;レポート ビルダーおよび SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b63c-125">For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-a-color-fill-on-each-series"></a><span data-ttu-id="4b63c-126">各系統での塗りつぶしの使用</span><span class="sxs-lookup"><span data-stu-id="4b63c-126">Using a Color Fill on Each Series</span></span>  
 <span data-ttu-id="4b63c-127">グラフの各系統に色を指定して、グラフに独自の色を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-127">You can also define your own colors on the chart by specifying a color for each series on the chart.</span></span> <span data-ttu-id="4b63c-128">この操作を行うには、 **[系列のプロパティ]** ダイアログ ボックスを開き、 **Color** プロパティを **[塗りつぶし]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="4b63c-128">To do this, open the **Series Properties** dialog box and set the **Color** property for **Fill**.</span></span> <span data-ttu-id="4b63c-129">この方法により、定義されたすべてのパレットがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="4b63c-129">This approach will override all defined palettes.</span></span> <span data-ttu-id="4b63c-130">一般的に、データセットの系統の数はレポート処理の段階まで不明な場合があるため、カスタム パレットを使用して独自の色を定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4b63c-130">Generally, it is better to use a custom palette to define your own colors because the number of series in your dataset may not be known until report processing.</span></span>  
  
 <span data-ttu-id="4b63c-131">この方法は、式を基に系統の色を条件に応じて設定する場合に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="4b63c-131">This approach is best suited when you want to conditionally set the color of the series based on an expression.</span></span>  <span data-ttu-id="4b63c-132">詳細については、「 [グラフでのデータ ポイントの書式設定 (レポート ビルダーおよび SSRS)](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b63c-132">For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b63c-133">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4b63c-133">In This Section</span></span>  
 [<span data-ttu-id="4b63c-134">複数の図形グラフでの色の統一 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4b63c-134">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
 <span data-ttu-id="4b63c-135">[パレットを使用したグラフの色の定義 &#40;レポート ビルダーおよび SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="4b63c-135">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md))</span></span>  
  
 [<span data-ttu-id="4b63c-136">ストリップ ラインの追加によるグラフのデータの強調表示 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4b63c-136">Highlight Chart Data by Adding Strip Lines &#40;Report Builder and SSRS&#41;</span></span>](highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="4b63c-137">参照</span><span class="sxs-lookup"><span data-stu-id="4b63c-137">See Also</span></span>  
 <span data-ttu-id="4b63c-138">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b63c-138">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b63c-139">[グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 &#40;レポート ビルダーおよび SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4b63c-139">[Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span></span>  
 <span data-ttu-id="4b63c-140">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b63c-140">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4b63c-141">グラフの凡例の書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4b63c-141">Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-formatting-report-builder.md)  
  
  
