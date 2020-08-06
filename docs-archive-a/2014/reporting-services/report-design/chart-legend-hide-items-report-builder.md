---
title: グラフの凡例項目を非表示にする (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 20444432f580ffaf1c5f4de1320b06319f973a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644321"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a><span data-ttu-id="4cf8f-102">グラフの凡例項目を非表示にする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4cf8f-102">Hide Legend Items on the Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4cf8f-103">既定では、図形グラフ以外のグラフに追加した系列は、凡例の項目として使用されます。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-103">By default, any series added to a non-Shape chart will be added as an item in the legend.</span></span> <span data-ttu-id="4cf8f-104">円グラフ、ドーナツ グラフ、じょうごグラフ、およびピラミッド グラフでは、グラフに系列を追加すると、凡例に個々のデータ ポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-104">For pie, doughnut, funnel, and pyramid charts, any series added to the chart will add individual data points in the legend.</span></span>  
  
 <span data-ttu-id="4cf8f-105">凡例の任意の項目を非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-105">You can hide any item on the legend.</span></span> <span data-ttu-id="4cf8f-106">凡例の項目を非表示にした場合も、グラフには表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-106">When you hide a legend item, it will still appear in the chart.</span></span> <span data-ttu-id="4cf8f-107">これは、グラフに追加した系列の詳細な情報を表示したくないときに便利です。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-107">This is useful in situations where you do not want to show more information for a series that is added to the chart.</span></span> <span data-ttu-id="4cf8f-108">たとえば、移動平均のような計算系列をグラフに追加した場合、凡例のこのエントリを非表示にし、元の系列の詳細な情報のみを表示できます。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-108">For example, if you have added a calculated series like a moving average to the chart, you may want to hide this entry in the legend so that more information is only shown for the original series.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a><span data-ttu-id="4cf8f-109">凡例の項目を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="4cf8f-109">To hide an item from display in the legend</span></span>  
  
1.  <span data-ttu-id="4cf8f-110">非表示にする系列を右クリックし、 **[系列のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-110">Right-click on the series you want to hide and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="4cf8f-111">**[凡例]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-111">Click **Legend**.</span></span> <span data-ttu-id="4cf8f-112">**[凡例内の次の系列を非表示にする]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-112">Select the **Do not show this series in a legend** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf8f-113">あるグループの系列を非表示にし、他のグループの系列を表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-113">You cannot hide a series for one group and not for the others.</span></span> <span data-ttu-id="4cf8f-114">**[系列グループ]** 領域にフィールドを追加している場合、このグループに属するすべての系列は非表示になります。</span><span class="sxs-lookup"><span data-stu-id="4cf8f-114">If you have added a field to the **Series Groups** area, all series belonging to this group will be hidden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf8f-115">参照</span><span class="sxs-lookup"><span data-stu-id="4cf8f-115">See Also</span></span>  
 <span data-ttu-id="4cf8f-116">[グラフの凡例の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4cf8f-116">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="4cf8f-117">[グラフでのデータ ポイントの書式設定 (レポート ビルダーおよび SSRS)](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4cf8f-117">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4cf8f-118">[凡例アイテムのテキストの変更 &#40;レポート ビルダーおよび SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4cf8f-118">[Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span></span>  
 <span data-ttu-id="4cf8f-119">[グラフへの移動平均の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4cf8f-119">[Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4cf8f-120">[[全般] ([凡例のプロパティ] ダイアログ ボックス) &#40;レポート ビルダーおよび SSRS&#41;](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="4cf8f-120">[Legend Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)</span></span>  
  
  
