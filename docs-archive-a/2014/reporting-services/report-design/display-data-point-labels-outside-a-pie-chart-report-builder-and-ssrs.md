---
title: 円グラフの外側へのデータ ポイント ラベルの表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dd4f38f24d2729acacfa3520635b93d8af2e9433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721182"
---
# <a name="display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="e81d7-102">円グラフの外側へのデータ ポイント ラベルの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e81d7-102">Display Data Point Labels Outside a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e81d7-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、円グラフのラベル付けは、データのいくつかのスライスのみにラベルが表示されるように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="e81d7-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], pie chart labeling is optimized to display labels on only several slices of data.</span></span> <span data-ttu-id="e81d7-104">円グラフに含まれるスライスが多すぎると、ラベルが重なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e81d7-104">Labels may overlap if the pie chart contains too many slices.</span></span> <span data-ttu-id="e81d7-105">1 つの解決策として、円グラフの外側にラベルを表示する方法があります。これにより、長いデータ ラベル用に領域を確保できます。</span><span class="sxs-lookup"><span data-stu-id="e81d7-105">One solution is to display the labels outside the pie chart, which may create more room for longer data labels.</span></span> <span data-ttu-id="e81d7-106">ラベルがまだ重なっていることが判明した場合は、3D を有効にすることでラベル用の領域をさらに確保することができます。</span><span class="sxs-lookup"><span data-stu-id="e81d7-106">If you find that your labels still overlap, you can create more space for them by enabling 3D.</span></span> <span data-ttu-id="e81d7-107">これにより、円グラフの直径が小さくなり、グラフの周囲でさらに領域が確保されます。</span><span class="sxs-lookup"><span data-stu-id="e81d7-107">This reduces the diameter of the pie chart, creating more space around the chart.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-data-point-labels-inside-a-pie-chart"></a><span data-ttu-id="e81d7-108">円グラフの内側にデータ ポイント ラベルを表示するには</span><span class="sxs-lookup"><span data-stu-id="e81d7-108">To display data point labels inside a pie chart</span></span>  
  
1.  <span data-ttu-id="e81d7-109">レポートに円グラフを追加します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-109">Add a pie chart to your report.</span></span> <span data-ttu-id="e81d7-110">詳細については、「[レポートへのグラフの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e81d7-110">For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="e81d7-111">デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e81d7-111">On the design surface, right-click on the chart and select **Show Data Labels**.</span></span>  
  
### <a name="to-display-data-point-labels-outside-a-pie-chart"></a><span data-ttu-id="e81d7-112">円グラフの外側にデータ ポイント ラベルを表示するには</span><span class="sxs-lookup"><span data-stu-id="e81d7-112">To display data point labels outside a pie chart</span></span>  
  
1.  <span data-ttu-id="e81d7-113">円グラフを作成し、データ ラベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-113">Create a pie chart and display the data labels.</span></span>  
  
2.  <span data-ttu-id="e81d7-114">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="e81d7-114">Open the Properties pane.</span></span>  
  
3.  <span data-ttu-id="e81d7-115">デザイン画面で、円グラフをクリックしてプロパティ ペインの **[カテゴリ]** プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-115">On the design surface, click on the pie itself to display the **Category** properties in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="e81d7-116">**[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-116">Expand the **CustomAttributes** node.</span></span> <span data-ttu-id="e81d7-117">円グラフの属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e81d7-117">A list of attributes for the pie chart is displayed.</span></span>  
  
5.  <span data-ttu-id="e81d7-118">**[PieLabelStyle]** プロパティを **Outside**に設定します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-118">Set the **PieLabelStyle** property to **Outside**.</span></span>  
  
6.  <span data-ttu-id="e81d7-119">プロパティを `PieLineColor` **Black**に設定します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-119">Set the `PieLineColor` property to **Black**.</span></span> <span data-ttu-id="e81d7-120">PieLineColor プロパティでは、各データ ポイント ラベルの引き出し線を定義します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-120">The PieLineColor property defines callout lines for each data point label.</span></span>  
  
### <a name="to-prevent-overlapping-labels-displayed-outside-a-pie-chart"></a><span data-ttu-id="e81d7-121">円グラフの外側に表示されるラベルの重なりを防ぐには</span><span class="sxs-lookup"><span data-stu-id="e81d7-121">To prevent overlapping labels displayed outside a pie chart</span></span>  
  
1.  <span data-ttu-id="e81d7-122">外側にラベルを設定した円グラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-122">Create a pie chart with external labels.</span></span>  
  
2.  <span data-ttu-id="e81d7-123">デザイン画面で、円グラフの外側でグラフの罫線の内側を右クリックし、 **[グラフ領域のプロパティ]** をクリックします。 **[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e81d7-123">On the design surface, right-click outside the pie chart but inside the chart borders and select **Chart Area Properties**.The **Chart AreaProperties** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="e81d7-124">**[3D オプション]** タブで、 **[3D の有効化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-124">On the **3D Options** tab, select **Enable 3D**.</span></span>  
  
4.  <span data-ttu-id="e81d7-125">ラベル用の領域を確保するようにグラフを 2 次元で表示する場合は、 **[回転]** プロパティと **[傾斜]** プロパティを **0**に設定します。</span><span class="sxs-lookup"><span data-stu-id="e81d7-125">If you want the chart to have more room for labels but still appear two-dimensional, set the **Rotation** and **Inclination** properties to **0**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e81d7-126">参照</span><span class="sxs-lookup"><span data-stu-id="e81d7-126">See Also</span></span>  
 <span data-ttu-id="e81d7-127">[円グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e81d7-127">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e81d7-128">[円グラフの小さいスライスをまとめる &#40;レポート ビルダーおよび SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e81d7-128">[Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e81d7-129">円グラフへのパーセンテージの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e81d7-129">Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
