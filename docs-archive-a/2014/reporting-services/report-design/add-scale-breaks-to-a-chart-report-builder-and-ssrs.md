---
title: グラフへのスケール区切りの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c081debd1e0a84158615edebdb6b84705c10e5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719574"
---
# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="177d3-102">グラフへのスケール区切りの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="177d3-102">Add Scale Breaks to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="177d3-103">スケール区切りは、グラフのプロット エリアに描画される線であり、値軸 (通常は縦軸、つまり Y 軸) 上の最高値と最低値の間の区切りを示します。</span><span class="sxs-lookup"><span data-stu-id="177d3-103">A scale break is a stripe drawn across the plotting area of a chart to denote a break in continuity between the high and low values on a value axis (usually the vertical, or y-axis).</span></span> <span data-ttu-id="177d3-104">スケール区切りを使用すると、同じグラフ領域内で 2 つの異なる範囲を表示できます。</span><span class="sxs-lookup"><span data-stu-id="177d3-104">Use a scale break to display two distinct ranges in the same chart area.</span></span>  
  
 <span data-ttu-id="177d3-105">![スケール区切り付きのグラフ](../media/rs-multipledatarangeschart-scalebreak.gif "スケール区切り付きのグラフ")</span><span class="sxs-lookup"><span data-stu-id="177d3-105">![Chart with scale break](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="177d3-106">グラフ上でスケール区切りを配置する場所を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="177d3-106">You cannot specify where to place a scale break on your chart.</span></span> <span data-ttu-id="177d3-107">グラフでは、データセット内の値に基づいた独自の計算で、実行時に値軸 (Y 軸) 上にスケール区切りを描画するためにデータ範囲の間が十分に離れているかどうかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="177d3-107">The chart uses its own calculations based on the values in your dataset to determine whether there is sufficient separation between data ranges to draw a scale break on the value axis (y-axis) at run time.</span></span>  
  
 <span data-ttu-id="177d3-108">スケール区切り付きのグラフについては、サンプル レポートに例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="177d3-108">An example of a chart with scale breaks is available as a sample report.</span></span> <span data-ttu-id="177d3-109">このサンプルレポートのダウンロードの詳細については、「 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [サンプルレポートのレポートビルダーとレポートデザイナー](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="177d3-109">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a><span data-ttu-id="177d3-110">グラフ上のスケール区切りを有効にするには</span><span class="sxs-lookup"><span data-stu-id="177d3-110">To enable scale breaks on the chart</span></span>  
  
1.  <span data-ttu-id="177d3-111">縦軸を右クリックし、 **[軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="177d3-111">Right-click the vertical axis and then click **Axis Properties**.</span></span> <span data-ttu-id="177d3-112">**[縦軸のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="177d3-112">The **VerticalAxis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="177d3-113">**[スケールの区切り線を有効にする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="177d3-113">Select the **Enable scale breaks** check box.</span></span>  
  
### <a name="to-change-the-style-of-the-scale-break"></a><span data-ttu-id="177d3-114">スケール区切りのスタイルを変更するには</span><span class="sxs-lookup"><span data-stu-id="177d3-114">To change the style of the scale break</span></span>  
  
1.  <span data-ttu-id="177d3-115">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="177d3-115">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="177d3-116">デザイン画面で、グラフの Y 軸を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="177d3-116">On the design surface, right-click on the y-axis of the chart.</span></span> <span data-ttu-id="177d3-117">Y 軸オブジェクト (既定の名前は "グラフ軸") のプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="177d3-117">The properties for the y-axis object (named Chart Axis by default) are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="177d3-118">**[スケール]** セクションで、ScaleBreakStyle プロパティを展開します。</span><span class="sxs-lookup"><span data-stu-id="177d3-118">In the **Scale** section, expand the ScaleBreakStyle property.</span></span>  
  
4.  <span data-ttu-id="177d3-119">BreakLineType や Spacing など、ScaleBreakStyle のプロパティの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="177d3-119">Change the values for ScaleBreakStyle properties, such as BreakLineType and Spacing.</span></span> <span data-ttu-id="177d3-120">スケール区切りプロパティの詳細については、「[グラフ上で複数のデータ範囲を持つ系列の表示 &#40;レポート ビルダーおよび SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="177d3-120">For more information about scale break properties, see [Displaying a Series with Multiple Data Ranges on a Chart &#40;Report Builder and SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177d3-121">参照</span><span class="sxs-lookup"><span data-stu-id="177d3-121">See Also</span></span>  
 <span data-ttu-id="177d3-122">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="177d3-122">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="177d3-123">[グラフの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="177d3-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="177d3-124">[[軸のオプション] ([軸のプロパティ] ダイアログ ボックス) &#40;レポート ビルダーおよび SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="177d3-124">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)</span></span>  
  
  
