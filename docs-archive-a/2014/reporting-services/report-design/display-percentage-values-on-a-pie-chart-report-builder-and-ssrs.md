---
title: 円グラフへのパーセンテージの表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2dee9017d34f2751b790b2e4928571160b597f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640697"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="ca17a-102">円グラフへのパーセンテージの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ca17a-102">Display Percentage Values on a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ca17a-103">既定では、それぞれの値を識別するために、カテゴリが凡例に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca17a-103">By default, categories are shown in the legend to identify each value.</span></span> <span data-ttu-id="ca17a-104">カテゴリ ラベルを使用して円グラフにラベルを付けた場合、凡例にパーセンテージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ca17a-104">If you have labeled the pie chart using category labels, you may want show percentages in the legend.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a><span data-ttu-id="ca17a-105">円グラフにパーセンテージをラベルとして表示するには</span><span class="sxs-lookup"><span data-stu-id="ca17a-105">To display percentage values as labels on a pie chart</span></span>  
  
1.  <span data-ttu-id="ca17a-106">レポートに円グラフを追加します。</span><span class="sxs-lookup"><span data-stu-id="ca17a-106">Add a pie chart to your report.</span></span> <span data-ttu-id="ca17a-107">詳細については、「[レポートへのグラフの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca17a-107">For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="ca17a-108">デザイン画面で、円グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca17a-108">On the design surface, right-click on the pie and select **Show Data Labels**.</span></span> <span data-ttu-id="ca17a-109">円グラフの各スライス内にデータ ラベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca17a-109">The data labels should appear within each slice on the pie chart.</span></span>  
  
3.  <span data-ttu-id="ca17a-110">デザイン画面で、ラベルを右クリックし、 **[系列ラベルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca17a-110">On the design surface, right-click on the labels and select **Series Label Properties**.</span></span> <span data-ttu-id="ca17a-111">**[系列ラベルのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca17a-111">The **Series Label Properties** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="ca17a-112">`#PERCENT`[**ラベルデータ**] オプションに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ca17a-112">Type `#PERCENT` for the **Label data** option.</span></span>  
  
5.  <span data-ttu-id="ca17a-113">(省略可) ラベルに表示する小数点以下桁数を指定するには、「#PERCENT{P*n*}」と入力します。ここで、 *n* は、表示する小数点以下桁数を表します。</span><span class="sxs-lookup"><span data-stu-id="ca17a-113">(Optional) To specify how many decimal places the label shows, type "#PERCENT{P*n*}" where *n* is the number of decimal places to display.</span></span> <span data-ttu-id="ca17a-114">たとえば、小数点以下を表示しない場合は「#PERCENT{P0}」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ca17a-114">For example, to display no decimal places, type "#PERCENT{P0}".</span></span>  
  
### <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a><span data-ttu-id="ca17a-115">円グラフの凡例にパーセンテージを表示するには</span><span class="sxs-lookup"><span data-stu-id="ca17a-115">To display percentage values in the legend of a pie chart</span></span>  
  
1.  <span data-ttu-id="ca17a-116">デザイン画面で、円グラフを右クリックし、 **[系列のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca17a-116">On the design surface, right-click on the pie chart and select **Series Properties**.</span></span> <span data-ttu-id="ca17a-117">**[系列のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca17a-117">The **Series Properties** dialog box displays.</span></span>  
  
2.  <span data-ttu-id="ca17a-118">[**凡例**] に、[ `#PERCENT` **凡例のカスタムテキスト**] プロパティに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ca17a-118">In **Legend**, type `#PERCENT` for the **Custom legend text** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca17a-119">参照</span><span class="sxs-lookup"><span data-stu-id="ca17a-119">See Also</span></span>  
 <span data-ttu-id="ca17a-120">[レポートビルダーおよび SSRS&#41;&#40;円グラフ](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ca17a-120">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ca17a-121">[グラフの凡例の書式設定 &#40;レポートビルダーと SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ca17a-121">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="ca17a-122">[レポートビルダーおよび SSRS&#41;&#40;円グラフの外側にデータポイントラベルを表示する](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ca17a-122">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ca17a-123">円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ca17a-123">Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
