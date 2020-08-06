---
title: 散布図 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2520ae24-0609-4890-807d-3267018aba8e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 93f9b31089eb8399c7fdfd201d3c799608f2e91e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717468"
---
# <a name="scatter-charts-report-builder-and-ssrs"></a><span data-ttu-id="4b719-102">散布図 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4b719-102">Scatter Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4b719-103">散布図では、点のセットとして系列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b719-103">A scatter chart displays a series as a set of points.</span></span> <span data-ttu-id="4b719-104">値は、グラフ上の点の位置によって表されます。</span><span class="sxs-lookup"><span data-stu-id="4b719-104">Values are represented by the position of the points on the chart.</span></span> <span data-ttu-id="4b719-105">カテゴリは、グラフ上のさまざまなマーカーによって表されます。</span><span class="sxs-lookup"><span data-stu-id="4b719-105">Categories are represented by different markers on the chart.</span></span> <span data-ttu-id="4b719-106">散布図は、通常、カテゴリ全体の集計データを比較するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b719-106">Scatter charts are typically used to compare aggregated data across categories.</span></span> <span data-ttu-id="4b719-107">散布図にデータを追加する方法の詳細については、「 [グラフ (レポート ビルダーおよび SSRS)](charts-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="4b719-107">For more information on how to add data to a scatter chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md)</span></span>  
  
 <span data-ttu-id="4b719-108">次の図は、散布図の例を示しています。</span><span class="sxs-lookup"><span data-stu-id="4b719-108">The following illustration shows an example of a scatter chart.</span></span>  
  
 <span data-ttu-id="4b719-109">![散布図](../media/rs-scatterchart.gif "散布図")</span><span class="sxs-lookup"><span data-stu-id="4b719-109">![Scatter chart](../media/rs-scatterchart.gif "Scatter chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="4b719-110">バリエーション</span><span class="sxs-lookup"><span data-stu-id="4b719-110">Variations</span></span>  
  
-   <span data-ttu-id="4b719-111">**バブル。**</span><span class="sxs-lookup"><span data-stu-id="4b719-111">**Bubble.**</span></span> <span data-ttu-id="4b719-112">: バブル チャートでは、1 つのデータ ポイントの 2 つの値の差を、バブルのサイズに基づいて表示します。</span><span class="sxs-lookup"><span data-stu-id="4b719-112">Bubble charts display the difference between two values of a data point based on the size of the bubble.</span></span> <span data-ttu-id="4b719-113">バブルが大きいほど、2 つの値の差が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="4b719-113">The larger the bubble, the larger the difference between the two values.</span></span>  
  
-   <span data-ttu-id="4b719-114">**3-D バブル**:</span><span class="sxs-lookup"><span data-stu-id="4b719-114">**3-D Bubble**.</span></span> <span data-ttu-id="4b719-115">バブル チャートが 3D で表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b719-115">A bubble chart displayed in 3-D.</span></span>  
  
## <a name="data-considerations-for-a-scatter-chart"></a><span data-ttu-id="4b719-116">散布図のデータに関する注意点</span><span class="sxs-lookup"><span data-stu-id="4b719-116">Data Considerations for a Scatter Chart</span></span>  
  
-   <span data-ttu-id="4b719-117">散布図は、一般的に、科学、統計、工学のデータなど、数値を表示して比較する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b719-117">Scatter charts are commonly used for displaying and comparing numeric values, such as scientific, statistical, and engineering data.</span></span>  
  
-   <span data-ttu-id="4b719-118">時間に関係なく多数のデータ ポイントを比較する場合は、散布図を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b719-118">Use the scatter chart when you want to compare large numbers of data points without regard to time.</span></span> <span data-ttu-id="4b719-119">散布図に含まれるデータが多いほど、比較しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="4b719-119">The more data that you include in a scatter chart, the better the comparisons that you can make.</span></span>  
  
-   <span data-ttu-id="4b719-120">バブル チャートでは、データ ポイントごとに 2 つの値 (最高値と最低値) が必要になります。</span><span class="sxs-lookup"><span data-stu-id="4b719-120">The bubble chart requires two values (top and bottom) per data point.</span></span>  
  
-   <span data-ttu-id="4b719-121">散布図は、データ ポイントの値および集合の分布を処理する場合に理想的です。</span><span class="sxs-lookup"><span data-stu-id="4b719-121">Scatter charts are ideal for handling the distribution of values and clusters of data points.</span></span> <span data-ttu-id="4b719-122">数千個のポイントなど、データセットに含まれるポイントが多い場合、これは最適なグラフです。</span><span class="sxs-lookup"><span data-stu-id="4b719-122">This is the best chart type if your dataset contains many points (for example, several thousand points).</span></span> <span data-ttu-id="4b719-123">複数の系列を散布図上に表示するとデータが複雑で見づらくなるため、このような表示は避けるようにします。</span><span class="sxs-lookup"><span data-stu-id="4b719-123">Displaying multiple series on a point chart is visually distracting and should be avoided.</span></span> <span data-ttu-id="4b719-124">この場合は、折れ線グラフの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="4b719-124">In this scenario, consider using a line chart.</span></span>  
  
-   <span data-ttu-id="4b719-125">散布図では、既定で、データ ポイントが円として表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b719-125">By default, scatter charts display data points as circles.</span></span> <span data-ttu-id="4b719-126">散布図に複数の系列がある場合は、各ポイントのマーカーの形状を、四角形、三角形、ひし形など別の形に変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="4b719-126">If you have multiple series on a scatter chart, consider changing the marker shape of each point to be square, triangle, diamond, or another shape.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b719-127">参照</span><span class="sxs-lookup"><span data-stu-id="4b719-127">See Also</span></span>  
 <span data-ttu-id="4b719-128">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b719-128">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b719-129">[グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b719-129">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b719-130">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b719-130">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4b719-131">折れ線グラフ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4b719-131">Line Charts &#40;Report Builder and SSRS&#41;</span></span>](line-charts-report-builder-and-ssrs.md)  
  
  
