---
title: 軸の間隔の指定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b64b824933753a8482360f193ca4ccf71e8d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631526"
---
# <a name="specify-an-axis-interval-report-builder-and-ssrs"></a><span data-ttu-id="8406d-102">軸の間隔の指定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="8406d-102">Specify an Axis Interval (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8406d-103">軸の間隔により、軸上のラベルおよび付随する目盛りの数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="8406d-103">The axis interval defines the number of labels and accompanying tick marks on an axis.</span></span> <span data-ttu-id="8406d-104">値軸では、軸の間隔により、グラフ上のデータ ポイントに一貫性のある基準が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8406d-104">On the value axis, axis intervals provide a consistent measure of the data points on the chart.</span></span> <span data-ttu-id="8406d-105">ただしカテゴリ軸では、この機能により、軸ラベルなしでカテゴリが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8406d-105">However, on the category axis, this functionality can cause categories to appear without axis labels.</span></span> <span data-ttu-id="8406d-106">軸の Interval プロパティで、必要な間隔の数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8406d-106">You can specify the number of intervals you want in the axis Interval property.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8406d-107">では、実行時に、結果セットのデータに基づいて間隔の数が計算されます。</span><span class="sxs-lookup"><span data-stu-id="8406d-107">calculates the number of intervals at run time, based on the data in the result set.</span></span> <span data-ttu-id="8406d-108">軸の間隔を計算する方法の詳細については、「[グラフの軸ラベルの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8406d-108">For more information about how axis intervals are calculated, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8406d-109">このトピックは、カテゴリ軸の日付または時刻の値には適用されません。</span><span class="sxs-lookup"><span data-stu-id="8406d-109">This topic is not applicable for date or time values on the category axis.</span></span> <span data-ttu-id="8406d-110">既定では、`DateTime` 値は日として表示されます。</span><span class="sxs-lookup"><span data-stu-id="8406d-110">Be default, `DateTime` values appear as days.</span></span> <span data-ttu-id="8406d-111">月や期間など、別の日付または期間を指定するには、軸ラベルの書式を設定し、`DateTime` 型ではなく `String` 型のインスタンスが表示されるように軸を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8406d-111">To specify a different date or time interval, such as a month or time interval, you must format the axis labels and set the axis to display instances of `DateTime` types instead of `String` types.</span></span> <span data-ttu-id="8406d-112">また、Interval プロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8406d-112">In addition, you must set the Interval property.</span></span> <span data-ttu-id="8406d-113">詳細については、「[日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8406d-113">For more information, see [Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8406d-114">このトピックは、円グラフ、ドーナツ グラフ、じょうごグラフ、ピラミッド グラフなど、軸のないグラフには当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="8406d-114">This topic does not apply to pie, doughnut, funnel or pyramid charts, which do not have axes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8406d-115">カテゴリ軸は、通常、横軸 (X 軸) です。</span><span class="sxs-lookup"><span data-stu-id="8406d-115">The category axis is usually the horizontal or x-axis.</span></span> <span data-ttu-id="8406d-116">ただし、横棒グラフの場合は、縦軸 (Y 軸) です。</span><span class="sxs-lookup"><span data-stu-id="8406d-116">However, for bar charts, the category axis is the vertical or y-axis.</span></span>  
  
 <span data-ttu-id="8406d-117">異なる軸の間隔を指定するグラフについては、サンプル レポートに例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8406d-117">An example of a chart specifying different axis intervals is available as a sample report.</span></span> <span data-ttu-id="8406d-118">このサンプルレポートのダウンロードの詳細については、「 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [サンプルレポートのレポートビルダーとレポートデザイナー](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8406d-118">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-show-all-category-labels-on-the-x-axis"></a><span data-ttu-id="8406d-119">X 軸のすべてのカテゴリのラベルを表示するには</span><span class="sxs-lookup"><span data-stu-id="8406d-119">To show all category labels on the x-axis</span></span>  
  
1.  <span data-ttu-id="8406d-120">カテゴリ軸を右クリックし、 **[軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8406d-120">Right-click the category axis and click **Axis Properties**.</span></span> <span data-ttu-id="8406d-121">**[軸のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8406d-121">The **Axis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8406d-122">[**軸のオプション**] で、を `Interval` **1**に設定します。</span><span class="sxs-lookup"><span data-stu-id="8406d-122">In **Axis Options**, set `Interval` to **1**.</span></span> <span data-ttu-id="8406d-123">すべてのカテゴリ グループのラベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8406d-123">Every category group label is displayed.</span></span> <span data-ttu-id="8406d-124">X 軸でカテゴリ グループのラベルを交互に表示する場合は、「 **2**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8406d-124">If you want to show every other category group label on the x-axis, type **2**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="8406d-125">軸の間隔が設定されている場合、ラベルの自動調整機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="8406d-125">When an axis interval is set, all automatic labeling is disabled.</span></span> <span data-ttu-id="8406d-126">軸の間隔に値を指定すると、カテゴリ軸のカテゴリ数によって、予期しないラベル付け動作が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="8406d-126">If you specify a value for the axis interval, you may experience unpredictable labeling behavior depending on how many categories are on the category axis.</span></span>  
  
### <a name="to-enable-a-variable-interval-calculation-on-an-axis"></a><span data-ttu-id="8406d-127">軸の可変間隔の計算を有効にするには</span><span class="sxs-lookup"><span data-stu-id="8406d-127">To enable a variable interval calculation on an axis</span></span>  
  
1.  <span data-ttu-id="8406d-128">変更するグラフ軸を右クリックし、 **[軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8406d-128">Right-click the chart axis that you want to change, and then click **Axis Properties**.</span></span> <span data-ttu-id="8406d-129">**[軸のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8406d-129">The **Axis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8406d-130">[**軸のオプション**] で、[ `Interval` **自動**] に設定します。グラフには、軸に沿って表示できるカテゴリラベルの最適な数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8406d-130">In **Axis Options**, set `Interval` to **Auto**. The chart will display the optimal number of category labels that can fit along the axis.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8406d-131">参照</span><span class="sxs-lookup"><span data-stu-id="8406d-131">See Also</span></span>  
 <span data-ttu-id="8406d-132">[グラフの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8406d-132">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8406d-133">[グラフ上のデータポイントの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8406d-133">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8406d-134">[データ領域内のデータの並べ替え &#40;レポートビルダーと SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8406d-134">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8406d-135">[[軸のオプション] ([軸のプロパティ] ダイアログボックス) &#40;レポートビルダーと SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8406d-135">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8406d-136">[レポートビルダーと SSRS の対数スケール &#40;を指定し&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8406d-136">[Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8406d-137">セカンダリ軸へのデータのプロット &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8406d-137">Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;</span></span>](plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  
