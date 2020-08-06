---
title: 面グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 245b236d-1d55-4744-b752-80bd133502aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f401efa0abd5eac8ab39e511bc6b16a4f381ebdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717499"
---
# <a name="area-charts-report-builder-and-ssrs"></a><span data-ttu-id="f6cc6-102">面グラフ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="f6cc6-102">Area Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f6cc6-103">面グラフでは、線で結ばれた点のセットとして系列が表示され、線の下の領域はすべて塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-103">An area chart displays a series as a set of points connected by a line, with all the area filled in below the line.</span></span> <span data-ttu-id="f6cc6-104">面グラフにデータを追加する方法の詳細については、「 [グラフ (レポート ビルダーおよび SSRS)](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-104">For more information on how to add data to an area chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f6cc6-105">次の図は、積み上げ面グラフの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-105">The following illustration shows an example of a stacked area chart.</span></span> <span data-ttu-id="f6cc6-106">このデータは積み上げ面グラフでの表示に適しています。このグラフでは、すべての系列の合計に加え、各系列が全体に占める割合も表示できるためです。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-106">The data is well suited for display on a stacked area chart because the chart can display totals for all series as well as the proportion that each series contributes to the total.</span></span>  
  
 <span data-ttu-id="f6cc6-107">![面グラフ](../media/areachart.gif "面グラフ")</span><span class="sxs-lookup"><span data-stu-id="f6cc6-107">![Area chart](../media/areachart.gif "Area chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="f6cc6-108">バリエーション</span><span class="sxs-lookup"><span data-stu-id="f6cc6-108">Variations</span></span>  
  
-   <span data-ttu-id="f6cc6-109">**積み上げ面**:</span><span class="sxs-lookup"><span data-stu-id="f6cc6-109">**Stacked area**.</span></span> <span data-ttu-id="f6cc6-110">複数の系列が垂直方向に積み上げられた面グラフ。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-110">An area chart where multiple series are stacked vertically.</span></span> <span data-ttu-id="f6cc6-111">グラフに系列が 1 つしかない場合、積み上げ面グラフでも、面グラフと同じように表示されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-111">If there is only one series in your chart, the stacked area chart will display the same as an area chart.</span></span>  
  
-   <span data-ttu-id="f6cc6-112">**100% 積み上げ面**:</span><span class="sxs-lookup"><span data-stu-id="f6cc6-112">**Percent stacked area**.</span></span> <span data-ttu-id="f6cc6-113">複数の系列がグラフ領域全体を占めるように垂直方向に積み上げられた面グラフ。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-113">An area chart where multiple series are stacked vertically to fit the entire chart area.</span></span> <span data-ttu-id="f6cc6-114">グラフに系列が 1 つしかない場合、積み上げ面グラフでも、面グラフと同じように表示されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-114">If there is only one series in your chart, the stacked area chart will display the same as an area chart.</span></span>  
  
-   <span data-ttu-id="f6cc6-115">**平滑面**:</span><span class="sxs-lookup"><span data-stu-id="f6cc6-115">**Smooth area**.</span></span> <span data-ttu-id="f6cc6-116">データ ポイントが直線ではなく平滑線で結ばれている面グラフ。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-116">An area chart where the data points are connected by a smooth line instead of a regular line.</span></span> <span data-ttu-id="f6cc6-117">個々のデータ ポイントの値を表示するよりも傾向を表示することに関心がある場合は、面グラフではなく平滑面グラフを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-117">Use a smooth area chart instead of an area chart when you are more concerned with displaying trends than with displaying the values of individual data points.</span></span>  
  
## <a name="data-considerations-for-area-charts"></a><span data-ttu-id="f6cc6-118">面グラフのデータに関する注意点</span><span class="sxs-lookup"><span data-stu-id="f6cc6-118">Data Considerations for Area Charts</span></span>  
  
-   <span data-ttu-id="f6cc6-119">折れ線グラフと同様に、面グラフはデータを連続的に表示するグラフの種類の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-119">Along with the line chart, the area chart is the only chart type that displays data contiguously.</span></span> <span data-ttu-id="f6cc6-120">このため、面グラフは、継続的に発生するデータを表す場合によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-120">For this reason, an area chart is commonly used to represent data that occurs over a continuous period of time.</span></span>  
  
-   <span data-ttu-id="f6cc6-121">100% 積み上げ面グラフは、時間の経過と共に発生するデータの割合を表す場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-121">A percent stacked area chart is useful for showing proportional data that occurs over time.</span></span>  
  
-   <span data-ttu-id="f6cc6-122">系列が 1 つしかない場合、積み上げ面グラフでも、面グラフのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-122">If there is only one series, a stacked area chart will be drawn as an area chart.</span></span>  
  
-   <span data-ttu-id="f6cc6-123">一般的な面グラフでは、複数の系列の値が同じ場合、面が重なり、データ ポイントの重要な値がわかりにくくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-123">In a plain area chart, if the values in multiple series are similar, the areas may overlap, obscuring important data point values.</span></span> <span data-ttu-id="f6cc6-124">この問題を解決するには、グラフの種類を積み上げ面グラフに変更します。積み上げ面グラフは、面グラフで複数の系列を示すようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-124">You can resolve this issue by changing the chart type to a stacked area chart, which is designed to show multiple series on an area chart.</span></span>  
  
-   <span data-ttu-id="f6cc6-125">積み上げ面グラフ内にギャップがある場合は、データセットに空の値が含まれている可能性があります。空の値は、積み上げ面グラフ上に空白部分として表示されます。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-125">If your stacked area chart contains gaps, it is possible that your dataset includes empty values, which will be shown as a vacant section on a stacked area chart.</span></span> <span data-ttu-id="f6cc6-126">データセット内に空の値がある場合は、グラフ上に空のポイントを挿入することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-126">If your dataset includes empty values, consider inserting empty points on the chart.</span></span> <span data-ttu-id="f6cc6-127">空のポイントを追加すると、グラフ上の空白領域が、NULL 値または 0 を示す別の色で塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-127">Adding empty points will fill in the empty areas on the chart with a different color to indicate null or zero values.</span></span> <span data-ttu-id="f6cc6-128">詳細については、「[空のポイントをグラフに追加する &#40;レポートビルダーと SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-128">For more information, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="f6cc6-129">面グラフの動作は、縦棒グラフや折れ線グラフとよく似ています。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-129">Area chart types are very similar to column and line charts in behavior.</span></span> <span data-ttu-id="f6cc6-130">複数の系列間の比較を行う場合は、縦棒グラフの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-130">If you are making a comparison between multiple series, consider using a column chart instead.</span></span> <span data-ttu-id="f6cc6-131">一定期間の傾向を分析する場合は、折れ線グラフの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f6cc6-131">If you are analyzing trends over a period of time, consider using a line chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6cc6-132">参照</span><span class="sxs-lookup"><span data-stu-id="f6cc6-132">See Also</span></span>  
 <span data-ttu-id="f6cc6-133">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6cc6-133">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f6cc6-134">[グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6cc6-134">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f6cc6-135">[折れ線グラフ &#40;レポート ビルダーおよび SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6cc6-135">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f6cc6-136">[グラフの種類の変更 &#40;レポート ビルダーおよび SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6cc6-136">[Change a Chart Type &#40;Report Builder and SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f6cc6-137">グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="f6cc6-137">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
