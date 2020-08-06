---
title: セカンダリ軸へのデータのプロット (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cec58820e0373bb1e9ef2d50d022e5b4ef7e962b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711613"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a><span data-ttu-id="01ea1-102">セカンダリ軸へのデータのプロット (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="01ea1-102">Plot Data on a Secondary Axis (Report Builder and SSRS)</span></span>
  <span data-ttu-id="01ea1-103">グラフには、プライマリ軸とセカンダリ軸という 2 種類の軸があります。</span><span class="sxs-lookup"><span data-stu-id="01ea1-103">The chart has two axis types: primary and secondary.</span></span> <span data-ttu-id="01ea1-104">セカンダリ軸は、2 つの値セットを、共通のカテゴリを共有する 2 つの異なるデータ範囲と比較する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="01ea1-104">The secondary axis is useful when comparing two value sets with two distinct data ranges that share a common category.</span></span>  
  
 <span data-ttu-id="01ea1-105">たとえば、2008 年の収益と税の比較を計算するグラフがあるとします。</span><span class="sxs-lookup"><span data-stu-id="01ea1-105">For example, suppose you have a chart that calculates Revenue vs. Tax for the year 2008.</span></span> <span data-ttu-id="01ea1-106">この場合、2008 年という期間は両方の値セットに共通しています。</span><span class="sxs-lookup"><span data-stu-id="01ea1-106">In this case, the 2008 time period is common to both value sets.</span></span> <span data-ttu-id="01ea1-107">ただし、両方の系列が同じ Y 軸にプロットされると、Y 軸のスケールはデータセット内の最大の値に対して最適化されるため、有効な比較を行うことができません。</span><span class="sxs-lookup"><span data-stu-id="01ea1-107">However, when both series are plotted on the same y-axis, we cannot make a useful comparison because the scale of the y-axis is optimized for the largest values in the dataset.</span></span> <span data-ttu-id="01ea1-108">収益をプライマリ軸に示し、税をセカンダリ軸に示すと、各系列は、独自の Y 軸に独自の値のスケールを使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="01ea1-108">If we show Revenue on the primary axis, and Tax on the secondary axis, we can display each series on its own y-axis with its own scale of values.</span></span> <span data-ttu-id="01ea1-109">これらの系列では、引き続き共通の X 軸が使用されます。</span><span class="sxs-lookup"><span data-stu-id="01ea1-109">The series still share a common x-axis.</span></span>  
  
 <span data-ttu-id="01ea1-110">比較する系列が 3 つ以上ある場合は、グラフ内で複数の系列を比較して表示する際に別の方法を検討します。</span><span class="sxs-lookup"><span data-stu-id="01ea1-110">In situations where there are more than two series to be compared, consider a different approach for comparing and displaying multiple series in a chart.</span></span> <span data-ttu-id="01ea1-111">詳細については、「 [グラフ上の複数の系列 (レポート ビルダーおよび SSRS)](multiple-series-on-a-chart-report-builder-and-ssrs.md):</span><span class="sxs-lookup"><span data-stu-id="01ea1-111">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="01ea1-112">このグラフについては、サンプル レポートに例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="01ea1-112">An example of this chart is available as a sample report.</span></span> <span data-ttu-id="01ea1-113">このサンプルレポートのダウンロードの詳細については、「 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [サンプルレポートのレポートビルダーとレポートデザイナー](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01ea1-113">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a><span data-ttu-id="01ea1-114">セカンダリ軸に系列をプロットするには</span><span class="sxs-lookup"><span data-stu-id="01ea1-114">To plot a series on the secondary axis</span></span>  
  
1.  <span data-ttu-id="01ea1-115">グラフ内の系列を右クリックするか、セカンダリ軸に表示する **[値]** 領域内のフィールドを右クリックして、 **[系列のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01ea1-115">Right-click the series in the chart or right-click on a field in the **Values** area that you want to display on the secondary axis and click **Series Properties**.</span></span> <span data-ttu-id="01ea1-116">**[系列のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="01ea1-116">The **Series Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="01ea1-117">**[軸とグラフ領域]** をクリックし、値軸とカテゴリ軸のうち、有効にするセカンダリ軸を選択します。</span><span class="sxs-lookup"><span data-stu-id="01ea1-117">Click **Axes and Chart Area**, and select which of the secondary axes you want to enable, the value axis or the category axis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ea1-118">参照</span><span class="sxs-lookup"><span data-stu-id="01ea1-118">See Also</span></span>  
 <span data-ttu-id="01ea1-119">[グラフの軸ラベルの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01ea1-119">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="01ea1-120">軸の間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="01ea1-120">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
