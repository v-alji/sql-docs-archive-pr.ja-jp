---
title: 凡例アイテムのテキストの変更 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d0bb721aa0ff03a5211065111c98605cd86e971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644328"
---
# <a name="change-the-text-of-a-legend-item-report-builder-and-ssrs"></a><span data-ttu-id="c5e2b-102">凡例アイテムのテキストの変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c5e2b-102">Change the Text of a Legend Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c5e2b-103">グラフの [値] 領域にフィールドを配置すると、このフィールドの名前を含む凡例アイテムが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-103">When a field is placed in the Values area of the chart, a legend item is automatically generated that contains the name of this field.</span></span> <span data-ttu-id="c5e2b-104">すべての凡例アイテムは、グラフ上の個々の系列に接続されています。ただし、図形グラフの場合は例外で、凡例は個々の系列ではなく個々のデータ ポイントに接続されています。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-104">Every legend item is connected to an individual series on the chart, with the exception of shape charts, where the legend is connected to individual data points instead of individual series.</span></span>  
  
 <span data-ttu-id="c5e2b-105">図形グラフで、凡例アイテムのテキストを変更して個々のデータ ポイントの詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-105">On shape charts, you can change the text of a legend item to show more information about the individual data points.</span></span> <span data-ttu-id="c5e2b-106">たとえば、データ ポイントの値を凡例にパーセンテージで表示する場合、`#PERCENT` などのキーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-106">For example, if you want to show the values of the data points as percentages in the legend, you can use a keyword such as `#PERCENT`.</span></span> <span data-ttu-id="c5e2b-107">.NET Framework 形式のコードをキーワードと組み合わせて追加し、数値と日付の形式を適用できます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-107">You can append .NET Framework format codes in conjunction with keywords to apply numeric and date formats.</span></span> <span data-ttu-id="c5e2b-108">キーワードの詳細については、「[グラフでのデータ ポイントの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-108">For more information about keywords, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c5e2b-109">![シャープ チャート](../media/sharpchart.png "シャープ チャート")</span><span class="sxs-lookup"><span data-stu-id="c5e2b-109">![Sharp Chart](../media/sharpchart.png "Sharp Chart")</span></span>  
  
 <span data-ttu-id="c5e2b-110">図形以外のグラフで、凡例アイテムのテキストを変更できます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-110">On non-shape charts, you can change the text of a legend item.</span></span> <span data-ttu-id="c5e2b-111">たとえば、系列名が "Series1" の場合、"Sales for 2008" などわかりやすい名前に変更できます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-111">For example, if your series name is "Series1", you may want to change the text to something more descriptive like "Sales for 2008".</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a><span data-ttu-id="c5e2b-112">図形グラフの凡例に表示されるテキストを変更するには</span><span class="sxs-lookup"><span data-stu-id="c5e2b-112">To modify the text that appears in the legend on a Shape chart</span></span>  
  
1.  <span data-ttu-id="c5e2b-113">系列を右クリックするか、 **[値]** 領域のフィールドを右クリックし、 **[系列のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-113">Right-click on a series, or right-click on a field in the **Values** area, and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="c5e2b-114">**[凡例]** をクリックし、 **[凡例のユーザー定義テキスト]** ボックス内をクリックして、キーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-114">Click **Legend** and in the **Custom legend text** box, type a keyword.</span></span>  
  
 <span data-ttu-id="c5e2b-115">次の表は、 **[凡例のユーザー定義テキスト]** プロパティに使用するグラフに固有のキーワードの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-115">The following table provides examples of chart-specific keywords to use for the **Custom Legend Text** property.</span></span> <span data-ttu-id="c5e2b-116">キーワードの詳細については、「[グラフでのデータ ポイントの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-116">For more information about keywords, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
|<span data-ttu-id="c5e2b-117">Keyword</span><span class="sxs-lookup"><span data-stu-id="c5e2b-117">Keyword</span></span>|<span data-ttu-id="c5e2b-118">説明</span><span class="sxs-lookup"><span data-stu-id="c5e2b-118">Description</span></span>|<span data-ttu-id="c5e2b-119">凡例のテキストとして表示される内容の例</span><span class="sxs-lookup"><span data-stu-id="c5e2b-119">Example of what appears as text in the legend</span></span>|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|<span data-ttu-id="c5e2b-120">合計値のパーセンテージを小数点以下 1 桁に表示します。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-120">Displays the percentage of the total value to one decimal place.</span></span>|<span data-ttu-id="c5e2b-121">85.0%</span><span class="sxs-lookup"><span data-stu-id="c5e2b-121">85.0%</span></span>|  
|`#VALY`|<span data-ttu-id="c5e2b-122">データ フィールドの実際の数値を表示します。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-122">Displays the actual numeric value of the data field.</span></span>|<span data-ttu-id="c5e2b-123">17000</span><span class="sxs-lookup"><span data-stu-id="c5e2b-123">17000</span></span>|  
|`#VALY{C2}`|<span data-ttu-id="c5e2b-124">データ フィールドの実際の数値を小数点以下 2 桁の通貨として表示します。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-124">Displays the actual numeric value of the data field as a currency to two decimal places.</span></span>|<span data-ttu-id="c5e2b-125">$17000.00</span><span class="sxs-lookup"><span data-stu-id="c5e2b-125">$17000.00</span></span>|  
|`#AXISLABEL (#PERCENT{P0})`|<span data-ttu-id="c5e2b-126">カテゴリ フィールドのテキスト表現が表示され、後ろに各カテゴリのグラフに対するパーセンテージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-126">Displays the text representation of the category field, followed by the percentage that each category displays on the chart.</span></span>|<span data-ttu-id="c5e2b-127">Michael Blythe (85%)</span><span class="sxs-lookup"><span data-stu-id="c5e2b-127">Michael Blythe (85%)</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c5e2b-128">**[系列グループ]** 領域にフィールドが指定されていない場合、#AXISLABEL キーワードは実行時にのみ評価されます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-128">The #AXISLABEL keyword can only be evaluated at run time when there is not a field specified in the **Series Groups** area.</span></span>  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a><span data-ttu-id="c5e2b-129">図形以外のグラフで凡例に表示されるテキストを変更するには</span><span class="sxs-lookup"><span data-stu-id="c5e2b-129">To modify the text that appears in the legend on a non-Shape chart</span></span>  
  
1.  <span data-ttu-id="c5e2b-130">系列を右クリックするか、 **[値]** 領域のフィールドを右クリックし、 **[系列のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-130">Right-click on a series, or right-click on a field in the **Values** area, and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="c5e2b-131">**[凡例]** をクリックし、 **[凡例のユーザー定義テキスト]** ボックス内をクリックして、凡例ラベルを入力します。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-131">Click **Legend** and in the **Custom legend text** box, type a legend label.</span></span> <span data-ttu-id="c5e2b-132">シリーズは、テキストで更新されます。</span><span class="sxs-lookup"><span data-stu-id="c5e2b-132">The series is updated with your text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e2b-133">参照</span><span class="sxs-lookup"><span data-stu-id="c5e2b-133">See Also</span></span>  
 <span data-ttu-id="c5e2b-134">[グラフの凡例の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2b-134">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="c5e2b-135">[グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2b-135">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c5e2b-136">グラフの凡例項目を非表示にする &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c5e2b-136">Hide Legend Items on the Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-hide-items-report-builder.md)  
  
  
