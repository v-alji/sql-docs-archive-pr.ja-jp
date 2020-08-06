---
title: ストリップ ラインの追加によるグラフのデータの強調表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: addd6137-4b6e-4e88-a7e8-9600fcd1ccce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01b0bb41a71daf9ac558ce8d8bb84480426870c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632897"
---
# <a name="highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs"></a><span data-ttu-id="f01ce-102">ストリップ ラインの追加によるグラフのデータの強調表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="f01ce-102">Highlight Chart Data by Adding Strip Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f01ce-103">ストリップ ライン (ストリップ) は、一定の間隔またはカスタムの間隔でグラフの背景を網掛け表示にする、横方向または縦方向の帯です。</span><span class="sxs-lookup"><span data-stu-id="f01ce-103">Strip lines, or strips, are horizontal or vertical ranges that shade the background of the chart in regular or custom intervals.</span></span> <span data-ttu-id="f01ce-104">ストリップ ラインを使用すると、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="f01ce-104">You can use strip lines to:</span></span>  
  
-   <span data-ttu-id="f01ce-105">グラフ上の個々の値を調べるために見やすくする。</span><span class="sxs-lookup"><span data-stu-id="f01ce-105">Improve readability for looking up individual values on the chart.</span></span> <span data-ttu-id="f01ce-106">一定の間隔でストリップ ラインを指定すると、グラフを読む際にデータ ポイントを区別しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="f01ce-106">Specify strip lines at regular intervals to help separate data points when reading the chart.</span></span>  
  
-   <span data-ttu-id="f01ce-107">一定の間隔の日付を強調する。</span><span class="sxs-lookup"><span data-stu-id="f01ce-107">Highlight dates that occur at regular intervals.</span></span> <span data-ttu-id="f01ce-108">たとえば、売上レポートでは、ストリップ ラインを使用して週末のデータ ポイントを識別することができます。</span><span class="sxs-lookup"><span data-stu-id="f01ce-108">For example, in a sales report you might use strip lines to identify weekend data points.</span></span>  
  
-   <span data-ttu-id="f01ce-109">特定のキー範囲を強調する。</span><span class="sxs-lookup"><span data-stu-id="f01ce-109">Highlight a specific key range.</span></span> <span data-ttu-id="f01ce-110">上記の例を使用すると、1 本のストリップ ラインを使用して、売上高が最も高い範囲 (80 ～ 100 ドル) を強調できます。</span><span class="sxs-lookup"><span data-stu-id="f01ce-110">Using the previous example, you can use one strip line to highlight the highest range of sales that is between $80-100.</span></span>  
  
 <span data-ttu-id="f01ce-111">ストリップ ラインは、図形グラフや極座標グラフには適用できません。</span><span class="sxs-lookup"><span data-stu-id="f01ce-111">Strip lines are not applicable to Shape or Polar chart types.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-interlaced-strip-lines-at-regular-intervals-on-a-chart"></a><span data-ttu-id="f01ce-112">インターレース ストリップ ラインを一定間隔でグラフに表示するには</span><span class="sxs-lookup"><span data-stu-id="f01ce-112">To display interlaced strip lines at regular intervals on a chart</span></span>  
  
1.  <span data-ttu-id="f01ce-113">横方向のストリップ ラインを表示するには、グラフの縦軸を右クリックし、 **[縦軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f01ce-113">To show horizontal strip lines, right-click the vertical chart axis and click **VerticalAxis Properties**.</span></span>  
  
     <span data-ttu-id="f01ce-114">縦方向のストリップ ラインを表示するには、グラフの横軸を右クリックし、 **[横軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f01ce-114">To show vertical strip lines, right-click the horizontal chart axis and click **Horizontal Axis Properties**.</span></span>  
  
2.  <span data-ttu-id="f01ce-115">**[インターレースを使用する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f01ce-115">Select the **Use interlacing** option.</span></span> <span data-ttu-id="f01ce-116">グラフにグレーのストリップ ラインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f01ce-116">Grey strip lines will appear on your chart.</span></span>  
  
3.  <span data-ttu-id="f01ce-117">(省略可) 隣接する **[色]** ボックスの一覧を使用して、ストリップ ラインの色を指定します。</span><span class="sxs-lookup"><span data-stu-id="f01ce-117">(Optional) Specify a color for the strip lines using the adjacent **Color** drop-down list.</span></span>  
  
### <a name="to-display-interlaced-strip-lines-at-custom-intervals-on-a-chart"></a><span data-ttu-id="f01ce-118">インターレース ストリップ ラインをカスタムの間隔でグラフに表示するには</span><span class="sxs-lookup"><span data-stu-id="f01ce-118">To display interlaced strip lines at custom intervals on a chart</span></span>  
  
1.  <span data-ttu-id="f01ce-119">横方向のストリップ ラインを表示するには、グラフの縦軸を右クリックし、 **[縦軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f01ce-119">To show horizontal strip lines, right-click the vertical chart axis and click **VerticalAxis Properties**.</span></span>  
  
     <span data-ttu-id="f01ce-120">縦方向のストリップ ラインを表示するには、グラフの横軸を右クリックし、 **[横軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f01ce-120">To show vertical strip lines, right-click the horizontal chart axis and click **Horizontal Axis Properties**.</span></span>  
  
     <span data-ttu-id="f01ce-121">軸のプロパティが [プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f01ce-121">The axis properties are displayed in the Properties window.</span></span>  
  
2.  <span data-ttu-id="f01ce-122">[プロパティ] ウィンドウの **[外観]** セクションで、StripLines プロパティのコレクションの編集ボタン [...] をクリックし、**ChartStripLine コレクション エディター**を開きます。</span><span class="sxs-lookup"><span data-stu-id="f01ce-122">In the **Appearance** section of the Properties pane, for the StripLines property, click the Edit Collection (...) button to open the **ChartStripLine Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="f01ce-123">**[追加]** をクリックし、新しいストリップ ラインをコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="f01ce-123">Click **Add** to add a new strip line to the collection.</span></span>  
  
4.  <span data-ttu-id="f01ce-124">StripWidth をクリックして、レポート上のストリップ ラインの幅 (インチ単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="f01ce-124">Click StripWidth to specify the width of the strip line, measured in inches on the report.</span></span> <span data-ttu-id="f01ce-125">日付や時刻を強調する場合は、StripWidthType をクリックし、期間を選択します。</span><span class="sxs-lookup"><span data-stu-id="f01ce-125">If you are highlighting dates or times, click StripWidthType and select a time interval.</span></span>  
  
5.  <span data-ttu-id="f01ce-126">Interval を表す値または式を入力し、ストリップ ラインが繰り返される間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="f01ce-126">Type a value or expression for the Interval to specify how often the strip line will repeat.</span></span>  <span data-ttu-id="f01ce-127">たとえば、間隔に 10 を指定し、ストリップ ラインの幅が 5 である場合、ストリップ ラインは、値が 0 ～ 5、15 ～ 20、30 ～ 35 などの場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f01ce-127">For example, if you specify an interval of 10, and your strip line width is 5, strip lines will display at values of 0 to 5, 15 to 20, 30 to 35, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f01ce-128">既定では、Interval は Auto に設定されます。つまり、グラフでは、カスタム ストリップ ラインの間隔が計算されません。</span><span class="sxs-lookup"><span data-stu-id="f01ce-128">By default, Interval is set to Auto, which means the chart will not calculate an interval for custom strip lines.</span></span> <span data-ttu-id="f01ce-129">グラフでは、間隔値が設定されている場合のみ、ストリップ ラインの間隔が計算されます。</span><span class="sxs-lookup"><span data-stu-id="f01ce-129">The chart only calculates intervals for strip lines if an interval value is set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f01ce-130">参照</span><span class="sxs-lookup"><span data-stu-id="f01ce-130">See Also</span></span>  
 <span data-ttu-id="f01ce-131">[グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f01ce-131">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f01ce-132">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f01ce-132">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f01ce-133">グラフへの移動平均の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f01ce-133">Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
  
  
