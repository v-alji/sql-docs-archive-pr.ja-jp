---
title: 複数の図形グラフでの一貫した色の指定 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d52f68e9-2ba7-4bff-9053-4089e5164ab4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c2c89f0f8cda3b7d6ef6b2acbd0de66c87170357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631525"
---
# <a name="specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs"></a><span data-ttu-id="6a418-102">複数の図形グラフでの色の統一 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="6a418-102">Specify Consistent Colors across Multiple Shape Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6a418-103">図形以外のグラフでは、グラフ内の系列のインデックスに基づいてパレットから新しい色が選択されます。</span><span class="sxs-lookup"><span data-stu-id="6a418-103">On non-shape charts, a new color is selected from the palette based on the index of series in the chart.</span></span> <span data-ttu-id="6a418-104">たとえば、グラフの最初の系列は、パレット内の最初の色にマップされます。</span><span class="sxs-lookup"><span data-stu-id="6a418-104">For example, the first series on your chart will be mapped to the first color in the palette.</span></span> <span data-ttu-id="6a418-105">しかし、この動作は図形グラフでは異なります。</span><span class="sxs-lookup"><span data-stu-id="6a418-105">However, this behavior differs for shape charts.</span></span> <span data-ttu-id="6a418-106">図形グラフの場合、パレットの各色は、データセット内のデータ ポイントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="6a418-106">On shape charts, each color in the palette is mapped to a data point in the dataset.</span></span> <span data-ttu-id="6a418-107">たとえば、データ ポイント 1 はパレットの最初の色にマップされ、データ ポイント 2 は 2 番目の色にマップされます。</span><span class="sxs-lookup"><span data-stu-id="6a418-107">For example, data point 1 is mapped to the first color in the palette, data point 2 is mapped to the second color palette and so on.</span></span>  
  
 <span data-ttu-id="6a418-108">値がないデータ ポイントは、図形グラフに表示されません。</span><span class="sxs-lookup"><span data-stu-id="6a418-108">If a data point has no value, it is omitted from display on a shape chart.</span></span> <span data-ttu-id="6a418-109">したがって、そのデータ ポイントへの色のマッピングはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="6a418-109">This means that the data point is skipped from being colored.</span></span> <span data-ttu-id="6a418-110">たとえば、ポイント 2 の値が 0 の場合、ポイント 1 にパレットの最初の色がマップされ、ポイント 3 にパレットの 2 番目の色がマップされます。</span><span class="sxs-lookup"><span data-stu-id="6a418-110">For example, if point 2 has a value of zero, point 1 will be mapped to the first color in the palette, and point 3 will be mapped to the second color in the palette.</span></span> <span data-ttu-id="6a418-111">空のポイントを描画する必要がない場合、円グラフのデータセットの空のポイントにパレット色を使用する必要はないので、この方法は便利です。</span><span class="sxs-lookup"><span data-stu-id="6a418-111">This approach is useful because the empty points in the dataset of a pie chart do not unnecessarily use a palette color when the empty point does not need to be drawn.</span></span>  
  
 <span data-ttu-id="6a418-112">その弊害として、1 つのレポートに複数の円グラフを表示する場合、同じカテゴリ グループのデータ ポイントが異なる色で表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="6a418-112">As a side effect, when multiple pie charts are displayed in a report, the pie charts may display different colors for data points that have the same category grouping.</span></span> <span data-ttu-id="6a418-113">この問題を解決するには、個々のデータ値ではなく、カテゴリ グループにマップするように個々の色を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a418-113">To resolve this, you need to define individual colors that map to a category group instead of individual data values.</span></span> <span data-ttu-id="6a418-114">この方法は、図形グラフがテーブルまたはマトリックスのスパークラインであるか、レポート自体の図形グラフであるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="6a418-114">How you do this depends on if the shape charts are sparklines in a table or matrix, or if they are shape charts in the report itself.</span></span>  
  
 <span data-ttu-id="6a418-115">凡例は系列に接続されるので、系列に指定した色が自動的に凡例に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a418-115">The legend is connected to the series, so any color you specify for the series will automatically be shown on the legend.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-consistent-colors-across-multiple-sparkline-shape-charts-in-a-table-or-matrix"></a><span data-ttu-id="6a418-116">テーブルまたはマトリックス内の複数のスパークライン図形グラフで色を統一するには</span><span class="sxs-lookup"><span data-stu-id="6a418-116">To specify consistent colors across multiple sparkline shape charts in a table or matrix</span></span>  
  
1.  <span data-ttu-id="6a418-117">グラフをクリックして、グラフ データ ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="6a418-117">Click the chart to display the Chart Data pane.</span></span>  
  
2.  <span data-ttu-id="6a418-118">**[カテゴリ グループ]** 領域内のカテゴリを右クリックし、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a418-118">In the **Category Groups** area, right-click a category and click **Category Group Properties**.</span></span>  
  
3.  <span data-ttu-id="6a418-119">[全般] タブの **[グループの同期]** ボックスで、色を同期させるカテゴリの名前をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a418-119">On the General tab, in the **Synchronize groups in** box, click the name of the category for which you would like to synchronize colors, and then click **OK**.</span></span>  
  
### <a name="to-specify-consistent-colors-across-multiple-shape-charts"></a><span data-ttu-id="6a418-120">複数の図形グラフで色を統一するには</span><span class="sxs-lookup"><span data-stu-id="6a418-120">To specify consistent colors across multiple shape charts</span></span>  
  
1.  <span data-ttu-id="6a418-121">レポート本文の外側を右クリックし、 **[レポートのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6a418-121">Right-click outside the body of the report, and select **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="6a418-122">**[コード]** のテキスト ボックスに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="6a418-122">In **Code**, type the following code into the textbox.</span></span>  
  
    ```  
    Private colorPalette As String() = {"Color1", "Color2", "Color3"}  
    Private count As Integer = 0  
    Private mapping As New System.Collections.Hashtable()  
    Public Function GetColor(ByVal groupingValue As String) As String  
        If mapping.ContainsKey(groupingValue) Then  
            Return mapping(groupingValue)  
        End If  
        Dim c As String = colorPalette(count Mod colorPalette.Length)  
        count = count + 1  
        mapping.Add(groupingValue, c)  
        Return c  
    End Function  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="6a418-123">"Color1" という文字列を目的の色で置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a418-123">You will need to replace the "Color1" strings with your own colors.</span></span> <span data-ttu-id="6a418-124">"Red" などの名前付きの色を使用することも、"#FFFFFF" (黒) などの色を表す 6 桁の 16 進数値を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6a418-124">You can use named colors, for example "Red", or you can use six-digit hexadecimal value that represent the color, such as "#FFFFFF" for black.</span></span> <span data-ttu-id="6a418-125">3 色以上定義する場合、配列内の色の数が図形グラフのポイントの数に一致するように色の配列を拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a418-125">If you have more than three colors defined, you will need to extend the array of colors so that the number of colors in the array matches the number of points in your shape chart.</span></span> <span data-ttu-id="6a418-126">名前付きの色または色の 16 進数表現を含む文字列値のコンマ区切りリストを指定して、配列に新しい色を追加できます。</span><span class="sxs-lookup"><span data-stu-id="6a418-126">You can add new colors to the array by specifying a comma-separated list of string values that contain named colors or hexadecimal representations of colors.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="6a418-127">図形グラフ上を右クリックし、 **[系列のプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6a418-127">Right-click on the shape chart and select **Series Properties**.</span></span>  
  
5.  <span data-ttu-id="6a418-128">**[塗りつぶし]** の **式** ( *[fx]* ) ボタンをクリックして、 **Color** プロパティの式を編集します。</span><span class="sxs-lookup"><span data-stu-id="6a418-128">In **Fill**, click the **Expression** (*fx*) button to edit the expression for the **Color** property.</span></span>  
  
6.  <span data-ttu-id="6a418-129">次の式を入力します。ここで、"MyCategoryField" は、 **[カテゴリ グループ]** 領域に表示されるフィールドです。</span><span class="sxs-lookup"><span data-stu-id="6a418-129">Type the following expression, where "MyCategoryField" is the field that is displayed in the **Category Groups** area:</span></span>  
  
    ```  
    =Code.GetColor(Fields!MyCategoryField)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6a418-130">参照</span><span class="sxs-lookup"><span data-stu-id="6a418-130">See Also</span></span>  
 <span data-ttu-id="6a418-131">[グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a418-131">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6a418-132">[グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 &#40;レポート ビルダーおよび SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="6a418-132">[Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span></span>  
 <span data-ttu-id="6a418-133">[パレットを使用したグラフの色の定義 &#40;レポート ビルダーおよび SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a418-133">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6a418-134">[グラフ &#40;レポートビルダーと SSRS&#41;に空のポイントを追加します。](add-empty-points-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a418-134">[Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6a418-135">[図形グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a418-135">[Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6a418-136">[同じデータセットへの複数のデータ領域のリンク &#40;レポート ビルダーおよび SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a418-136">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6a418-137">[入れ子になったデータ領域 (レポート ビルダーおよび SSRS)](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6a418-137">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6a418-138">スパークラインとデータ バー (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="6a418-138">Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
