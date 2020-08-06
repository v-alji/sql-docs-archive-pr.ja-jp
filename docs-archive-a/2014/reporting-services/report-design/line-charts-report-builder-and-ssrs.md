---
title: 折れ線グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 194e6679-890d-4a3e-a756-130d32ef7e29
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 44e7a011186e66e6b8bdc8b5dd31939c883e320b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739270"
---
# <a name="line-charts-report-builder-and-ssrs"></a><span data-ttu-id="e0b3e-102">折れ線グラフ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e0b3e-102">Line Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e0b3e-103">折れ線グラフでは、1 本の線で結ばれた点のセットとして系列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-103">A line chart displays a series as a set of points connected by a single line.</span></span> <span data-ttu-id="e0b3e-104">折れ線グラフは、継続的に発生する大量のデータを表す場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-104">Line charts are used to representing large amounts of data that occur over a continuous period of time.</span></span> <span data-ttu-id="e0b3e-105">折れ線グラフにデータを追加する方法の詳細については、「 [グラフ (レポート ビルダーおよび SSRS)](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-105">For more information about how to add data to a line chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e0b3e-106">次の図は、3 つの系列を含む折れ線グラフを示しています。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-106">The following illustration shows a line chart that contains three series.</span></span>  
  
 <span data-ttu-id="e0b3e-107">![折れ線グラフ](../media/rs-linechart.gif "折れ線グラフ")</span><span class="sxs-lookup"><span data-stu-id="e0b3e-107">![Line chart](../media/rs-linechart.gif "Line chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="e0b3e-108">バリエーション</span><span class="sxs-lookup"><span data-stu-id="e0b3e-108">Variations</span></span>  
  
-   <span data-ttu-id="e0b3e-109">**平滑線**:</span><span class="sxs-lookup"><span data-stu-id="e0b3e-109">**Smooth line**.</span></span> <span data-ttu-id="e0b3e-110">直線ではなく曲線を使用した折れ線グラフ。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-110">A line chart that uses a curved line instead of a regular line.</span></span>  
  
-   <span data-ttu-id="e0b3e-111">**階段状折れ線**:</span><span class="sxs-lookup"><span data-stu-id="e0b3e-111">**Stepped line**.</span></span> <span data-ttu-id="e0b3e-112">直線ではなく階段状折れ線を使用した折れ線グラフ。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-112">A line chart that uses a stepped line instead of a regular line.</span></span> <span data-ttu-id="e0b3e-113">階段状折れ線は、はしごや階段の段のように見える線を使用して点を結びます。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-113">The stepped line connects points by using a line that makes it look like steps on a ladder or staircase.</span></span>  
  
-   <span data-ttu-id="e0b3e-114">**スパークライン グラフ**:</span><span class="sxs-lookup"><span data-stu-id="e0b3e-114">**Sparkline charts**.</span></span> <span data-ttu-id="e0b3e-115">折れ線グラフの一種で、テーブルまたはマトリックスのセルに線系列のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-115">Variations of the line chart that show only the line series in the cell of a table or matrix.</span></span> <span data-ttu-id="e0b3e-116">詳細については、「 [スパークラインとデータ バー (レポート ビルダーおよび SSRS)](sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-116">For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="data-considerations-for-line-charts"></a><span data-ttu-id="e0b3e-117">折れ線グラフのデータに関する注意点</span><span class="sxs-lookup"><span data-stu-id="e0b3e-117">Data Considerations for Line Charts</span></span>  
  
-   <span data-ttu-id="e0b3e-118">既定の折れ線グラフの視覚的な効果を高めるには、系列の罫線の幅を 3 に変更したり、影のオフセットを 1 にしたりすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-118">To improve the visual impact of the default line chart, consider changing the width of the series border to 3, and adding a shadow offset of 1.</span></span> <span data-ttu-id="e0b3e-119">こうすると、太い折れ線グラフが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-119">This will create a much bolder line chart.</span></span> <span data-ttu-id="e0b3e-120">グラフの種類を折れ線グラフから他の種類に変更する場合は、これらのプロパティを元の値に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-120">You will need to revert these properties to their original values if you change the chart type from Line to another type.</span></span>  
  
-   <span data-ttu-id="e0b3e-121">データセット内に空の値がある場合、折れ線グラフでは、グラフ上で連続性を維持するために、プレースホルダーの線の形式で空のポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-121">If your dataset includes empty values, the line chart will add empty points, in the form of placeholder lines, in order to maintain continuity on the chart.</span></span> <span data-ttu-id="e0b3e-122">この線が表示されないようにする場合は、横棒グラフや縦棒グラフなど、連続性のない種類のグラフを使用してデータセットを表示することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-122">If you would rather not see these lines, consider displaying your dataset using a non-contiguous chart type such as a bar or column chart.</span></span>  
  
-   <span data-ttu-id="e0b3e-123">折れ線グラフでは、線を描画するために少なくとも 2 つのポイントが必要です。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-123">A line chart requires at least two points to draw a line.</span></span>  <span data-ttu-id="e0b3e-124">データセットにデータ ポイントが 1 つしかない場合、折れ線グラフは 1 つのデータ ポイント マーカーとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-124">If your dataset has only one data point, the line chart will display as a single data point marker.</span></span>  
  
-   <span data-ttu-id="e0b3e-125">線で描画される系列は、グラフ領域内であまり場所を取りません。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-125">A series that is drawn as a line will not take up much space within a chart area.</span></span>  <span data-ttu-id="e0b3e-126">そのため、折れ線グラフは、縦棒グラフなどの他の種類のグラフと組み合わせることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-126">For this reason, line charts are frequently combined with other chart types such as column charts.</span></span> <span data-ttu-id="e0b3e-127">ただし、折れ線グラフは、横棒、極座標、円、または図形のグラフと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="e0b3e-127">However, you cannot combine a line chart with bar, polar, pie or shape chart types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b3e-128">参照</span><span class="sxs-lookup"><span data-stu-id="e0b3e-128">See Also</span></span>  
 <span data-ttu-id="e0b3e-129">[横棒グラフ (レポート ビルダーおよび SSRS)](bar-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0b3e-129">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e0b3e-130">[縦棒グラフ &#40;レポート ビルダーおよび SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0b3e-130">[Column Charts &#40;Report Builder and SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e0b3e-131">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0b3e-131">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e0b3e-132">[グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0b3e-132">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e0b3e-133">[面グラフ &#40;レポート ビルダーおよび SSRS&#41;](area-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0b3e-133">[Area Charts &#40;Report Builder and SSRS&#41;](area-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e0b3e-134">[グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS)](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0b3e-134">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e0b3e-135">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e0b3e-135">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
