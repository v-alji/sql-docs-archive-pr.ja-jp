---
title: '[軸のオプション] ([軸のプロパティ] ダイアログボックス) (レポートビルダーおよび SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.axisproperties.axisoptions.f1
- "10138"
ms.assetid: b276e210-7a12-48ae-971b-7dabae51df11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a94c4de6487d111417ef7ad3cee53a4172b5d275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640779"
---
# <a name="axis-properties-dialog-box-axis-options-report-builder-and-ssrs"></a><span data-ttu-id="eff52-102">[軸のオプション] ([軸のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="eff52-102">Axis Properties Dialog Box, Axis Options (Report Builder and SSRS)</span></span>
  <span data-ttu-id="eff52-103">[**横軸**の**プロパティ**] ダイアログボックスの [**軸のオプション**] を選択すると、グラフの指定した軸の外観を定義できます。</span><span class="sxs-lookup"><span data-stu-id="eff52-103">Select **Axis Options** on the **Horizontal** or **VerticalAxis Properties** dialog box to define the appearance of the specified axis of the chart.</span></span> <span data-ttu-id="eff52-104">以前のバージョンの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]では、既定でグラフの X 軸上にすべてのラベルが表示されていました。</span><span class="sxs-lookup"><span data-stu-id="eff52-104">In previous versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the chart displayed all labels on the x-axis by default.</span></span> <span data-ttu-id="eff52-105">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008 では、グラフ内の画像を見やすくし、ラベルの重なりを回避するために、ラベルは省略されます。</span><span class="sxs-lookup"><span data-stu-id="eff52-105">However, in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008, the chart skips labels in order to produce a cleaner image on the chart and avoid labeling collisions.</span></span> <span data-ttu-id="eff52-106">詳細については、「[グラフの軸ラベルの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eff52-106">For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="eff52-107">Options</span><span class="sxs-lookup"><span data-stu-id="eff52-107">Options</span></span>  
 <span data-ttu-id="eff52-108">**[スケールの区切り線を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="eff52-108">**Enable scale breaks**</span></span>  
 <span data-ttu-id="eff52-109">必要に応じてグラフでスケールの区切り線を描画できるようにする場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="eff52-109">Select this option to enable the chart to draw a scale breaks when it is deemed necessary.</span></span> <span data-ttu-id="eff52-110">このチェック ボックスがオンの場合、データセット内の高い点と低い点の差異がスケールの区切り線を描画するのに十分であるかどうかが自動的に判断されます。</span><span class="sxs-lookup"><span data-stu-id="eff52-110">When this option is enabled, the chart will automatically calculate whether there is sufficient difference between the high and low points in the dataset to draw a scale break.</span></span>  
  
 <span data-ttu-id="eff52-111">**[方向を反転する]**</span><span class="sxs-lookup"><span data-stu-id="eff52-111">**Reverse direction**</span></span>  
 <span data-ttu-id="eff52-112">グラフの方向を反転させる場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="eff52-112">Select this option to reverse the direction of the chart.</span></span> <span data-ttu-id="eff52-113">たとえば、既定の縦棒グラフでは、グラフの左側に Y 軸が表示され、左から右にカテゴリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eff52-113">For example, by default, a column chart displays the y-axis on the left side of the chart and categories from left to right.</span></span> <span data-ttu-id="eff52-114">このチェック ボックスをオンにすると、グラフの右側に Y 軸が表示され、右から左にカテゴリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eff52-114">When this option is selected, the chart displays the y-axis on the right side of the chart and categories from right to left.</span></span>  
  
 <span data-ttu-id="eff52-115">**[インターレース色を使用する]**</span><span class="sxs-lookup"><span data-stu-id="eff52-115">**Use interlacing color**</span></span>  
 <span data-ttu-id="eff52-116">グラフにストリップ ラインを追加した後、色を選択したり式を入力したりするには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="eff52-116">Select this option to add strip lines to the chart, and then select a color or type an expression.</span></span> <span data-ttu-id="eff52-117">ストリップ ラインはグラフ領域上の影付きの帯であり、グリッド線の間で明るい領域と暗い領域を交互に適用する効果を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="eff52-117">Strip lines are shaded bands on the chart area that give the effect of alternating light and dark areas between gridlines.</span></span> <span data-ttu-id="eff52-118">これらのストリップ ラインは、軸上でのパターンの繰り返しを強調表示する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="eff52-118">These strip lines are useful for highlighting repeating patterns on an axis.</span></span>  
  
 <span data-ttu-id="eff52-119">**[常に 0 を含む]**</span><span class="sxs-lookup"><span data-stu-id="eff52-119">**Always include zero**</span></span>  
 <span data-ttu-id="eff52-120">軸のスケールで常に 0 を含める場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="eff52-120">Select this option to always include zero on the axis scale.</span></span> <span data-ttu-id="eff52-121">このオプションが有効でない場合、グラフの軸には値 0 というラベルが付きません。</span><span class="sxs-lookup"><span data-stu-id="eff52-121">If this option is not enabled, the chart will not label the zero value on the axis.</span></span> <span data-ttu-id="eff52-122">データセットに負の値や 0 が含まれている場合は、0 を含めると役立ちます。</span><span class="sxs-lookup"><span data-stu-id="eff52-122">Including zero values is useful when the dataset includes negative or zero values.</span></span>  
  
 <span data-ttu-id="eff52-123">**スカラー軸**</span><span class="sxs-lookup"><span data-stu-id="eff52-123">**Scalar axis**</span></span>  
 <span data-ttu-id="eff52-124">一連の軸の値を連続して表示する場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="eff52-124">Select this option to display a set of axis values on a continuous scale.</span></span> <span data-ttu-id="eff52-125">たとえば、データセットに 1 月、3 月、および 11 月のデータが含まれている場合は、非スカラー軸にはこれらの月だけが表示されますが、スカラー軸には 1 年のすべての月が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eff52-125">For example, if the dataset contains data for January, March, and November, a non-scalar axis displays only those months, whereas a scalar axis displays all of the months in the year.</span></span>  
  
 <span data-ttu-id="eff52-126">**対数スケールを使用する**</span><span class="sxs-lookup"><span data-stu-id="eff52-126">**Use logarithmic scale**</span></span>  
 <span data-ttu-id="eff52-127">軸のスケールが対数であることを示す場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="eff52-127">Select this option to indicate that the axis scale is logarithmic.</span></span> <span data-ttu-id="eff52-128">このチェック ボックスを Y 軸で使用できるのは、Y 軸に正の数値が含まれている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="eff52-128">This option is available only on the y-axis if the axis contains positive numeric values.</span></span>  
  
 <span data-ttu-id="eff52-129">ボックスには、対数スケールを使用するように軸が設定されている場合に使用する対数の底を入力します。</span><span class="sxs-lookup"><span data-stu-id="eff52-129">In the box, type the logarithmic base to use when the axis is set to use a logarithmic scale.</span></span> <span data-ttu-id="eff52-130">既定では、軸の対数スケールに使用される底は 10 です。</span><span class="sxs-lookup"><span data-stu-id="eff52-130">By default, the chart uses a base of 10 for the logarithmic scale of an axis.</span></span> <span data-ttu-id="eff52-131">このオプションを Y 軸で使用できるのは、Y 軸が数値を表している場合のみです。</span><span class="sxs-lookup"><span data-stu-id="eff52-131">This option is available only on the y-axis if the axis is numeric.</span></span>  
  
 <span data-ttu-id="eff52-132">**最小**</span><span class="sxs-lookup"><span data-stu-id="eff52-132">**Minimum**</span></span>  
 <span data-ttu-id="eff52-133">X 軸の最小値を示す式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="eff52-133">Type an expression or a value for the minimum value for the x-axis.</span></span> <span data-ttu-id="eff52-134">省略した場合、最小値はデータセットから返されるデータによって決まります。</span><span class="sxs-lookup"><span data-stu-id="eff52-134">If omitted, the minimum value is determined by the data returned by the dataset.</span></span>  
  
 <span data-ttu-id="eff52-135">**[最大]**</span><span class="sxs-lookup"><span data-stu-id="eff52-135">**Maximum**</span></span>  
 <span data-ttu-id="eff52-136">X 軸の最大値を示す式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="eff52-136">Type an expression or a value for the maximum value for the x-axis.</span></span> <span data-ttu-id="eff52-137">省略した場合、最大値はデータセットから返されるデータによって決まります。</span><span class="sxs-lookup"><span data-stu-id="eff52-137">If omitted, the maximum value is determined by the data returned by the dataset.</span></span>  
  
 <span data-ttu-id="eff52-138">**間隔**</span><span class="sxs-lookup"><span data-stu-id="eff52-138">**Interval**</span></span>  
 <span data-ttu-id="eff52-139">軸ラベルの間の間隔を示す式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="eff52-139">Type an expression or value for the interval between axis labels.</span></span> <span data-ttu-id="eff52-140">たとえば、軸上に各カテゴリ ラベルを表示するには、「1」と入力します。</span><span class="sxs-lookup"><span data-stu-id="eff52-140">For example, type 1 to display each category label on the axis.</span></span> <span data-ttu-id="eff52-141">カテゴリ ラベルを 1 つおきに表示するには、「2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="eff52-141">Type 2 to display every other category label.</span></span> <span data-ttu-id="eff52-142">省略した場合、ラベルは、データセットの値に基づいて自動的に計算されます。</span><span class="sxs-lookup"><span data-stu-id="eff52-142">If omitted, the labels are calculated automatically based on the values in the dataset.</span></span>  
  
 <span data-ttu-id="eff52-143">**[間隔の種類]**</span><span class="sxs-lookup"><span data-stu-id="eff52-143">**Interval type**</span></span>  
 <span data-ttu-id="eff52-144">指定した間隔の種類を表す式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="eff52-144">Type an expression or a value for the interval type of the interval specified.</span></span> <span data-ttu-id="eff52-145">たとえば、間隔を 2 日間にする場合は、間隔に「 **2** 」を指定し、間隔の種類に「 **日** 」を指定します。</span><span class="sxs-lookup"><span data-stu-id="eff52-145">For example, if you want the interval to be two days, you will specify **2** for interval and **Days** for interval type.</span></span>  
  
 <span data-ttu-id="eff52-146">**[横余白]**</span><span class="sxs-lookup"><span data-stu-id="eff52-146">**Side margins**</span></span>  
 <span data-ttu-id="eff52-147">グラフ要素とグラフの横の間にある余白を追加または削除するための式を入力するかまたは値を選択します。</span><span class="sxs-lookup"><span data-stu-id="eff52-147">Type an expression or select a value to add or remove a margin between the chart elements and the sides of the chart.</span></span> <span data-ttu-id="eff52-148">このオプションが **[自動]** に設定されている場合、横の余白が追加されます。</span><span class="sxs-lookup"><span data-stu-id="eff52-148">If this option is set to **Auto**, a side margins are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff52-149">参照</span><span class="sxs-lookup"><span data-stu-id="eff52-149">See Also</span></span>  
 <span data-ttu-id="eff52-150">[グラフの軸ラベルの書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eff52-150">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eff52-151">[グラフ &#40;レポートビルダーと SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eff52-151">[Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eff52-152">[グラフの系列の色の書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eff52-152">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eff52-153">[レポートビルダーと SSRS &#40;軸の間隔を指定し&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eff52-153">[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eff52-154">[日付または通貨として軸ラベルを書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eff52-154">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eff52-155">[セカンダリ軸 &#40;レポートビルダーおよび SSRS&#41;にデータをプロットする](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eff52-155">[Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eff52-156">[スパークラインとデータバー &#40;レポートビルダーと SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eff52-156">[Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="eff52-157">グラフの余白の追加または削除 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="eff52-157">Add or Remove Margins from a Chart &#40;Report Builder and SSRS&#41;</span></span>](report-design/add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
  
