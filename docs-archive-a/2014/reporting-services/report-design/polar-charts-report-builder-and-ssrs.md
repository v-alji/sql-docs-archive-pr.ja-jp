---
title: 極座標グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c9402d8f-202a-4cdf-949e-50f5b1d2b885
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b8c4dd9394fab3e076c4a714375954a616e081f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711614"
---
# <a name="polar-charts-report-builder-and-ssrs"></a><span data-ttu-id="c1116-102">極座標グラフ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c1116-102">Polar Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c1116-103">極座標グラフでは、カテゴリ別にグループ化されたポイントのセットとして、360°の円上に系列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-103">A polar chart displays a series as a set of points that are grouped by category on a 360-degree circle.</span></span> <span data-ttu-id="c1116-104">値は、円の中心からポイントまでの距離で表されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-104">Values are represented by the length of the point as measured from the center of the circle.</span></span> <span data-ttu-id="c1116-105">ポイントが中心から遠いほど、その値は大きくなります。</span><span class="sxs-lookup"><span data-stu-id="c1116-105">The farther the point is from the center, the greater its value.</span></span> <span data-ttu-id="c1116-106">カテゴリのラベルは、グラフの周囲に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-106">Category labels are displayed on the perimeter of the chart.</span></span> <span data-ttu-id="c1116-107">極座標グラフにデータを追加する方法の詳細については、「 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1116-107">For more information on how to add data to a polar chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="c1116-108">バリエーション</span><span class="sxs-lookup"><span data-stu-id="c1116-108">Variations</span></span>  
  
-   <span data-ttu-id="c1116-109">**レーダー チャート**:</span><span class="sxs-lookup"><span data-stu-id="c1116-109">**Radar chart**.</span></span> <span data-ttu-id="c1116-110">レーダー チャートでは、系列が円形の線または領域で表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-110">A radar chart displays a series as a circular line or area.</span></span> <span data-ttu-id="c1116-111">極座標グラフとは異なり、レーダー チャートでは、極座標の観点ではデータが表示されません。</span><span class="sxs-lookup"><span data-stu-id="c1116-111">Unlike the polar chart, the radar chart does not display data in terms of polar coordinates.</span></span>  
  
## <a name="data-considerations-for-polar-charts"></a><span data-ttu-id="c1116-112">極座標グラフのデータに関する注意点</span><span class="sxs-lookup"><span data-stu-id="c1116-112">Data Considerations for Polar Charts</span></span>  
  
-   <span data-ttu-id="c1116-113">レーダー チャートは、複数の系列のカテゴリ データを比較する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c1116-113">The radar chart is useful for comparisons between multiple series of category data.</span></span>  
  
-   <span data-ttu-id="c1116-114">極座標グラフは、極データをグラフ化する際に最もよく使用されます。ここでは、各データ ポイントが角度や距離によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c1116-114">Polar charts are most commonly used to graph polar data, where each data point is determined by an angle and a distance.</span></span>  
  
-   <span data-ttu-id="c1116-115">極座標グラフは、同じグラフ領域内で他の種類のグラフと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="c1116-115">Polar charts cannot be combined with any other chart type in the same chart area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1116-116">例</span><span class="sxs-lookup"><span data-stu-id="c1116-116">Example</span></span>  
 <span data-ttu-id="c1116-117">次の例では、レーダー チャートの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1116-117">The following example shows how a radar chart can be used.</span></span> <span data-ttu-id="c1116-118">次の表は、チャートのサンプル データを示しています。</span><span class="sxs-lookup"><span data-stu-id="c1116-118">The table below provides sample data for the chart.</span></span>  
  
|<span data-ttu-id="c1116-119">Name</span><span class="sxs-lookup"><span data-stu-id="c1116-119">Name</span></span>|<span data-ttu-id="c1116-120">売上</span><span class="sxs-lookup"><span data-stu-id="c1116-120">Sales</span></span>|  
|----------|-----------|  
|<span data-ttu-id="c1116-121">低木</span><span class="sxs-lookup"><span data-stu-id="c1116-121">Shrubs</span></span>|<span data-ttu-id="c1116-122">61</span><span class="sxs-lookup"><span data-stu-id="c1116-122">61</span></span>|  
|<span data-ttu-id="c1116-123">種</span><span class="sxs-lookup"><span data-stu-id="c1116-123">Seeds</span></span>|<span data-ttu-id="c1116-124">78</span><span class="sxs-lookup"><span data-stu-id="c1116-124">78</span></span>|  
|<span data-ttu-id="c1116-125">球根</span><span class="sxs-lookup"><span data-stu-id="c1116-125">Bulbs</span></span>|<span data-ttu-id="c1116-126">60</span><span class="sxs-lookup"><span data-stu-id="c1116-126">60</span></span>|  
|<span data-ttu-id="c1116-127">ツリー</span><span class="sxs-lookup"><span data-stu-id="c1116-127">Trees</span></span>|<span data-ttu-id="c1116-128">38</span><span class="sxs-lookup"><span data-stu-id="c1116-128">38</span></span>|  
|<span data-ttu-id="c1116-129">花</span><span class="sxs-lookup"><span data-stu-id="c1116-129">Flowers</span></span>|<span data-ttu-id="c1116-130">81</span><span class="sxs-lookup"><span data-stu-id="c1116-130">81</span></span>|  
  
 <span data-ttu-id="c1116-131">この例では、名前フィールドがカテゴリ グループ領域に配置されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-131">In this example, the Name field is placed in the Category Groups area.</span></span> <span data-ttu-id="c1116-132">売上フィールドは値領域に配置されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-132">The Sales field is placed in the Values area.</span></span> <span data-ttu-id="c1116-133">売上フィールドをドロップすると、グラフの売上フィールドが自動的に計算されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-133">The Sales field is automatically aggregated for the chart when you drop it.</span></span> <span data-ttu-id="c1116-134">レーダー チャートでは、売上フィールド内の値の数に基づいて、ラベルを配置する場所が計算されます。ここでは、5 つの値が含まれているため、円周上で等間隔に設定された 5 つの点にラベルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-134">The radar chart calculates where to place the labels based on the number of values in the Sales field, which contains five values and places labels at five equidistant points on a circle.</span></span> <span data-ttu-id="c1116-135">売上フィールドに 3 つの値が含まれている場合、円周上で等間隔に設定された 3 つの点にラベルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="c1116-135">If the Sales field contained three values, the labels would be placed at three equidistant points on a circle.</span></span>  
  
 <span data-ttu-id="c1116-136">次の図は、提示されたデータに基づくレーダー チャートの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="c1116-136">The following illustration shows an example of a radar chart based on the data presented.</span></span>  
  
 <span data-ttu-id="c1116-137">![レーダー チャート](../media/rs-radarchart.gif "レーダー チャート")</span><span class="sxs-lookup"><span data-stu-id="c1116-137">![Radar chart](../media/rs-radarchart.gif "Radar chart")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1116-138">参照</span><span class="sxs-lookup"><span data-stu-id="c1116-138">See Also</span></span>  
 <span data-ttu-id="c1116-139">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c1116-139">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c1116-140">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c1116-140">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c1116-141">[グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c1116-141">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c1116-142">[折れ線グラフ &#40;レポート ビルダーおよび SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c1116-142">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c1116-143">グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c1116-143">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
