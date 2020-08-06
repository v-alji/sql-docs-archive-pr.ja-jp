---
title: 系列のグラフ領域の指定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10157"
- sql12.rtp.rptdesigner.chartareaproperties.alignment.f1
ms.assetid: dc3c365b-c263-402a-bf6f-c2a7081db073
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483bc6d2fa4aa079c95e9dbd03e18c71d7b13abf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631529"
---
# <a name="specify-a-chart-area-for-a-series-report-builder-and-ssrs"></a><span data-ttu-id="0a7bd-102">系列のグラフ領域の指定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="0a7bd-102">Specify a Chart Area for a Series (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0a7bd-103">グラフは、外側の境界、グラフのタイトル、および凡例を含んでいる最上位レベルのコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-103">The chart is the top-level container that includes the outer border, the chart title, and the legend.</span></span> <span data-ttu-id="0a7bd-104">既定では、グラフには既定のグラフ領域が 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-104">By default, the chart contains one default chart area.</span></span> <span data-ttu-id="0a7bd-105">グラフ領域はグラフの表面上に見えませんが、グラフ領域を 1 つまたは複数の系列の軸ラベル、軸タイトル、およびプロット エリアのみを含んでいるコンテナーと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-105">The chart area is not visible on the chart surface, but you can think of the chart area as a container that encompasses only the axis labels, the axis title and the plotting area of one or more series.</span></span> <span data-ttu-id="0a7bd-106">次の図は、1 つのグラフ内にあるグラフ領域の概念を示しています。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-106">The following illustration shows the concept of chart areas within a single chart.</span></span>  
  
 <span data-ttu-id="0a7bd-107">![グラフ領域の図](../media/chartareasdiagram.gif "グラフ領域の図")</span><span class="sxs-lookup"><span data-stu-id="0a7bd-107">![Shows a diagram of a chart area](../media/chartareasdiagram.gif "Shows a diagram of a chart area")</span></span>  
  
 <span data-ttu-id="0a7bd-108">既定では、すべての系列が既定のグラフ領域に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-108">By default, all series are added to the default chart area.</span></span> <span data-ttu-id="0a7bd-109">面グラフ、縦棒グラフ、折れ線グラフ、散布図を使用する場合は、これらの系列を組み合わて同じグラフ領域上に表示できます。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-109">When using area, column, line, and scatter charts, any combination of these series can be displayed on the same chart area.</span></span> <span data-ttu-id="0a7bd-110">同じグラフ領域に複数の系列があると、グラフが読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-110">If you have several series in the same chart area, the readability of the chart is reduced.</span></span> <span data-ttu-id="0a7bd-111">グラフの種類を複数のグラフ領域に分割することができます。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-111">You may want to separate the chart types into multiple chart areas.</span></span> <span data-ttu-id="0a7bd-112">複数のグラフ領域を使用すると、読みやすさが向上して比較が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-112">Using multiple chart areas will increase readability for easier comparisons.</span></span> <span data-ttu-id="0a7bd-113">たとえば、価格と売上高の株価グラフは値の範囲が異なることがありますが、同じ期間の価格と売上高のデータを比較することができます。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-113">For example, price-volume stock charts often have different ranges of values, but comparisons can be made between the price and volume data over the same period of time.</span></span>  
  
 <span data-ttu-id="0a7bd-114">棒、極座標、または図形の系列は、同じグラフ領域内の同じグラフの種類の系列とのみ組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-114">The bar, polar, or shape series can only be combined with series of the same chart types in the same chart area.</span></span> <span data-ttu-id="0a7bd-115">極座標グラフまたは図形グラフを使用している場合は、表示するフィールドごとに異なるグラフ データ領域を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-115">If you are using a Polar or Shape chart, consider using a separate chart data region for each field that you wish to show.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-series-with-a-new-chart-area"></a><span data-ttu-id="0a7bd-116">系列を新しいグラフ領域に関連付けるには</span><span class="sxs-lookup"><span data-stu-id="0a7bd-116">To associate a series with a new chart area</span></span>  
  
1.  <span data-ttu-id="0a7bd-117">グラフ上の任意の場所を右クリックし、 **[新しいグラフ領域の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-117">Right-click anywhere on the chart and select **Add New Chart Area**.</span></span> <span data-ttu-id="0a7bd-118">新しい空のグラフ領域がグラフに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-118">A new, blank chart area appears on the chart.</span></span>  
  
2.  <span data-ttu-id="0a7bd-119">グラフの系列を右クリックするか、グラフ データ ペイン内の適切な領域にある系列またはデータ フィールドを右クリックして、 **[系列のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-119">Right-click the series on the chart or right-click a series or data field in the appropriate area in the Chart Data pane, and then click **Series Properties**.</span></span>  
  
3.  <span data-ttu-id="0a7bd-120">**[軸とグラフ領域]** で、系列を表示するグラフ領域を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-120">In **Axes and Chart Areas**, select the chart area that you want the series to be shown in.</span></span>  
  
4.  <span data-ttu-id="0a7bd-121">(省略可) グラフ領域を垂直に揃えます。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-121">(Optional) Align the chart areas vertically.</span></span> <span data-ttu-id="0a7bd-122">これを行うには、グラフを右クリックし、表示されるオプションから **[グラフ領域のプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-122">To do this, right-click the chart and select **Chart Area Properties**.</span></span> <span data-ttu-id="0a7bd-123">**[配置]** で、選択したグラフ領域に揃える別のグラフ領域を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a7bd-123">In **Alignment**, select another chart area that you want to align the selected chart area with.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7bd-124">参照</span><span class="sxs-lookup"><span data-stu-id="0a7bd-124">See Also</span></span>  
 <span data-ttu-id="0a7bd-125">[グラフ上の複数の系列 &#40;レポート ビルダーおよび SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a7bd-125">[Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0a7bd-126">[グラフでのデータ ポイントの書式設定 (レポート ビルダーおよび SSRS)](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a7bd-126">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0a7bd-127">[パレットを使用したグラフの色の定義 &#40;レポート ビルダーおよび SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a7bd-127">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0a7bd-128">[極座標グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a7bd-128">[Polar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0a7bd-129">[図形グラフ &#40;レポート ビルダーおよび SSRS&#41;](shape-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a7bd-129">[Shape Charts &#40;Report Builder and SSRS&#41;](shape-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0a7bd-130">円グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0a7bd-130">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](pie-charts-report-builder-and-ssrs.md)  
  
  
