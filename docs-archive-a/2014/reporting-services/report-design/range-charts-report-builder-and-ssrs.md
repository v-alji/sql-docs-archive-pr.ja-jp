---
title: 範囲グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 48e351d3-ac5b-4eda-a4bd-32a0de206a30
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 76a9723bc55030da59d22c945a40ce4418b84ab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717463"
---
# <a name="range-charts-report-builder-and-ssrs"></a><span data-ttu-id="7a442-102">範囲グラフ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7a442-102">Range Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7a442-103">範囲グラフでは、同じカテゴリの複数の値によってそれぞれ定義された、一連のデータ ポイントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a442-103">A range chart type displays a set of data points that are each defined by multiple values for the same category.</span></span> <span data-ttu-id="7a442-104">値は、マーカーの高さ (値軸) で表されます。</span><span class="sxs-lookup"><span data-stu-id="7a442-104">Values are represented by the height of the marker as measured by the value axis.</span></span> <span data-ttu-id="7a442-105">カテゴリのラベルは、カテゴリ軸に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a442-105">Category labels are displayed on the category axis.</span></span> <span data-ttu-id="7a442-106">一般的な範囲グラフでは、各データ ポイントの最高値と最低値の間の領域が設定されます。</span><span class="sxs-lookup"><span data-stu-id="7a442-106">The plain range chart fills in the area between the top and bottom value for each data point.</span></span>  
  
 <span data-ttu-id="7a442-107">次の図は、3 つの系列の一般的な範囲グラフを示しています。</span><span class="sxs-lookup"><span data-stu-id="7a442-107">The following illustration shows a plain range chart with three series.</span></span>  
  
 <span data-ttu-id="7a442-108">![範囲グラフ](../media/rs-rangechart.gif "範囲グラフ")</span><span class="sxs-lookup"><span data-stu-id="7a442-108">![Range chart](../media/rs-rangechart.gif "Range chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="7a442-109">バリエーション</span><span class="sxs-lookup"><span data-stu-id="7a442-109">Variations</span></span>  
  
-   <span data-ttu-id="7a442-110">**平滑範囲**:</span><span class="sxs-lookup"><span data-stu-id="7a442-110">**Smooth range**.</span></span> <span data-ttu-id="7a442-111">平滑範囲グラフでは、直線ではなく曲線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a442-111">A smooth range chart displays curved lines rather than straight.</span></span>  
  
-   <span data-ttu-id="7a442-112">**範囲縦棒**:</span><span class="sxs-lookup"><span data-stu-id="7a442-112">**Column range**.</span></span> <span data-ttu-id="7a442-113">範囲縦棒グラフでは、領域ではなく縦棒を使用して範囲を表示します。</span><span class="sxs-lookup"><span data-stu-id="7a442-113">A column range chart uses columns instead of areas to display the ranges.</span></span>  
  
-   <span data-ttu-id="7a442-114">**範囲横棒**:</span><span class="sxs-lookup"><span data-stu-id="7a442-114">**Bar range**.</span></span> <span data-ttu-id="7a442-115">範囲横棒グラフでは、領域ではなく横棒を使用して範囲を表示します。</span><span class="sxs-lookup"><span data-stu-id="7a442-115">A bar range chart uses bars instead of areas to display the ranges.</span></span>  
  
## <a name="data-considerations-for-range-charts"></a><span data-ttu-id="7a442-116">範囲グラフのデータに関する注意点</span><span class="sxs-lookup"><span data-stu-id="7a442-116">Data Considerations for Range Charts</span></span>  
  
-   <span data-ttu-id="7a442-117">範囲グラフでは、データ ポイントごとに 2 つの値が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a442-117">Range chart types require two values per data point.</span></span> <span data-ttu-id="7a442-118">これらの値は、各データ ポイントの範囲を定義する高値および低値に対応しています。</span><span class="sxs-lookup"><span data-stu-id="7a442-118">These values correspond with a high value and a low value that defines the range for each data point.</span></span>  
  
-   <span data-ttu-id="7a442-119">範囲グラフが分析に役立つのは、最高値が常に最低値より大きい場合のみです。</span><span class="sxs-lookup"><span data-stu-id="7a442-119">Range charts are useful for analysis only if the top values are always higher than the bottom values.</span></span> <span data-ttu-id="7a442-120">そうでない場合は、折れ線グラフの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="7a442-120">If this is not the case, consider using a line chart.</span></span> <span data-ttu-id="7a442-121">高値が低値より低い場合、範囲グラフでは、この 2 つの値の差の絶対値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a442-121">If the high value is lower the low value, the range chart will display the absolute value of the difference between these values.</span></span>  
  
-   <span data-ttu-id="7a442-122">値が 1 つしか指定されていない場合、範囲グラフは、各データ ポイントに 1 つの値を持つ、標準の面グラフのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a442-122">If only one value is specified, the range chart will display as if it were a regular area chart, with one value per data point.</span></span>  
  
-   <span data-ttu-id="7a442-123">範囲グラフは、データセット内の各カテゴリ グループの最小値および最大値を含むデータをグラフ化する場合によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a442-123">Range charts are often used to graph data that contains minimum and maximum values for each category group in the dataset.</span></span>  
  
-   <span data-ttu-id="7a442-124">範囲グラフでは、各データ ポイントでマーカーを表示することがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7a442-124">Displaying markers on each data point is not supported on the range chart.</span></span>  
  
-   <span data-ttu-id="7a442-125">一般的な範囲グラフでは、面グラフと同様に、複数の系列の値が同じ場合、系列が重なります。</span><span class="sxs-lookup"><span data-stu-id="7a442-125">Like the area chart, in a plain range chart, if the values in multiple series are similar, the series will overlap.</span></span> <span data-ttu-id="7a442-126">このシナリオでは、一般的な範囲グラフではなく、範囲縦棒グラフまたは範囲横棒グラフを使用することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a442-126">In this scenario, you may want to use a column range or bar range chart instead of a plain range chart.</span></span>  
  
-   <span data-ttu-id="7a442-127">ガント チャートは、範囲横棒グラフを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="7a442-127">Gantt charts can be created using a range bar chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a442-128">参照</span><span class="sxs-lookup"><span data-stu-id="7a442-128">See Also</span></span>  
 <span data-ttu-id="7a442-129">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7a442-129">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7a442-130">[グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7a442-130">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7a442-131">グラフの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7a442-131">Formatting a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
