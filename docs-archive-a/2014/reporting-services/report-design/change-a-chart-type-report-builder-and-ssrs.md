---
title: グラフの種類の変更 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fff24978-e3bd-4fac-8cd7-d6aa81f3cc25
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb466bed475b27206bf6837a60d0867f5fb745be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711726"
---
# <a name="change-a-chart-type-report-builder-and-ssrs"></a><span data-ttu-id="43bce-102">グラフの種類の変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="43bce-102">Change a Chart Type (Report Builder and SSRS)</span></span>
  <span data-ttu-id="43bce-103">レポートにグラフを初めて挿入すると、 **[グラフの種類の選択**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43bce-103">When you first insert a chart into a report, the **Select Chart Type** dialog appears.</span></span> <span data-ttu-id="43bce-104">このダイアログ ボックスを取り消すと、縦棒グラフというグラフの種類が既定で追加されます。</span><span class="sxs-lookup"><span data-stu-id="43bce-104">If you cancel this dialog, a Column chart type is added by default.</span></span>  
  
 <span data-ttu-id="43bce-105">グラフの種類は、レポートをデザインする過程でいつでも、レポートに適した別の種類に変更できます。</span><span class="sxs-lookup"><span data-stu-id="43bce-105">At any point when designing the report, you can change the chart type to something more suitable to the report.</span></span> <span data-ttu-id="43bce-106">データが正しく解釈されるようにするには、そのデータに適したグラフの種類を選択することが重要です。</span><span class="sxs-lookup"><span data-stu-id="43bce-106">It is important to select the correct chart type for your data so that it can be interpreted correctly.</span></span> <span data-ttu-id="43bce-107">どのグラフの種類がデータに最も適しているかを判断できるように、各グラフの種類の特徴を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="43bce-107">You should understand each chart type's characteristics to determine what chart type is best suited for your data.</span></span> <span data-ttu-id="43bce-108">詳細については、「 [グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43bce-108">For more information, see [Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="43bce-109">グラフ上に複数の系列が表示されている場合は、個々の系列のグラフの種類を変更する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="43bce-109">When multiple series are displayed on a chart, you may want to change the chart type of an individual series.</span></span> <span data-ttu-id="43bce-110">個々の系列のグラフの種類を変更できるのは、グラフの種類が面グラフ、縦棒グラフ、折れ線グラフ、または散布図の場合だけです。</span><span class="sxs-lookup"><span data-stu-id="43bce-110">You can only change the chart type of an individual series if the chart type is Area, Column, Line, or Scatter.</span></span> <span data-ttu-id="43bce-111">その他のグラフの種類の場合は、グラフ内のすべての系列が、選択したグラフの種類に変更されます。</span><span class="sxs-lookup"><span data-stu-id="43bce-111">For all other chart types, all series in your chart will be changed to the selected chart type.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-chart-type"></a><span data-ttu-id="43bce-112">グラフの種類を変更するには</span><span class="sxs-lookup"><span data-stu-id="43bce-112">To change the chart type</span></span>  
  
1.  <span data-ttu-id="43bce-113">デザイン ビューで、グラフを右クリックし、 **[グラフの種類の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43bce-113">In Design view, right-click the chart and then click **Change Chart Type**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="43bce-114">グラフ上に複数の系列がある場合は、グラフではなく、変更する系列を右クリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43bce-114">When there are multiple series on a chart, you must right-click on the series, not the chart, which you want to change.</span></span>  
  
2.  <span data-ttu-id="43bce-115">**[グラフの種類を選択]** ダイアログ ボックスで、一覧からグラフの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="43bce-115">In the **SelectChart Type** dialog box, select a chart type from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43bce-116">参照</span><span class="sxs-lookup"><span data-stu-id="43bce-116">See Also</span></span>  
 <span data-ttu-id="43bce-117">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="43bce-117">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="43bce-118">[ゲージ &#40;レポート ビルダーおよび SSRS&#41;](gauges-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="43bce-118">[Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="43bce-119">レポートへのグラフの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="43bce-119">Add a Chart to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
  
