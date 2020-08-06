---
title: 外れ値 (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92dddf3338d15e700576a13476ee364696bfd274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743534"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a><span data-ttu-id="c1faa-102">外れ値 (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="c1faa-102">Outliers (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="c1faa-103">![[データ マイニング] リボンの外れ値ウィザード](media/dmc-outliers.gif "[データ マイニング] リボンの外れ値ウィザード")</span><span class="sxs-lookup"><span data-stu-id="c1faa-103">![Outliers wizard in Data Mining ribbon](media/dmc-outliers.gif "Outliers wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="c1faa-104">*外れ値*は、次のいずれかの理由で問題となるデータ値を意味します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-104">An *outlier* means a data value that is problematic for any one of the following reasons:</span></span>  
  
-   <span data-ttu-id="c1faa-105">値が予想される範囲を逸脱している。</span><span class="sxs-lookup"><span data-stu-id="c1faa-105">Value is outside the expected range.</span></span>  
  
-   <span data-ttu-id="c1faa-106">データが不正確に入力された。</span><span class="sxs-lookup"><span data-stu-id="c1faa-106">Data might have been entered incorrectly.</span></span>  
  
-   <span data-ttu-id="c1faa-107">値が不足している。</span><span class="sxs-lookup"><span data-stu-id="c1faa-107">Value is missing.</span></span>  
  
-   <span data-ttu-id="c1faa-108">データがスペースや NULL 文字列で構成されている。</span><span class="sxs-lookup"><span data-stu-id="c1faa-108">Data consists of a space or other null string.</span></span>  
  
-   <span data-ttu-id="c1faa-109">値は正確だが、分布から大きく外れているため、モデルに深刻な影響を与える可能性がある。</span><span class="sxs-lookup"><span data-stu-id="c1faa-109">Value is accurate, but is so far outside the distribution that it can significantly affect the model.</span></span>  
  
 <span data-ttu-id="c1faa-110">Excel 用のデータ マイニング クライアントを使用すると、このようなデータを検出し、値を更新したり非表示にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-110">The Data Mining Client for Excel helps you detect this data, and then update the values or suppress them.</span></span> <span data-ttu-id="c1faa-111">たとえば、外れ値を数値計算による平均値に置き換えたり、誤っている可能性がある値を含む行を削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-111">For example, you can replace outliers with an arithmetic mean, or you can delete rows that contain potentially wrong values.</span></span>  
  
## <a name="handling-outliers"></a><span data-ttu-id="c1faa-112">外れ値の処理</span><span class="sxs-lookup"><span data-stu-id="c1faa-112">Handling Outliers</span></span>  
 <span data-ttu-id="c1faa-113">外れ値の**削除**ウィザードには、外れ値を適切に処理するためのツールがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="c1faa-113">The **Remove Outliers** wizard gives you several tools to handle outliers appropriately:</span></span>  
  
-   <span data-ttu-id="c1faa-114">まず、データを調べて、値の分布や、外れ値と他のデータの関係を把握できます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-114">First, you can explore the data to better understand the distribution of values and the relationship of the outliers to other data.</span></span>  
  
     <span data-ttu-id="c1faa-115">たとえば、[**データの探索**] タスクを使用して、値を確認し、修正することができます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-115">For example, you can use the **Explore Data** task to review and fix the values.</span></span> <span data-ttu-id="c1faa-116">外れ値の**削除**ウィザードでは、すべての値の分布を理解するのに役立つグラフ (折れ線グラフまたは横棒グラフ) も表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-116">The **Remove Outliers** wizard also displays a graph, either a line or a bar chart, to help you understand the distribution of all values.</span></span>  
  
-   <span data-ttu-id="c1faa-117">次に、**外れ**値ウィザードを使用して外れ値を削除または変更できます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-117">Next, you can use the **Outliers** wizard to remove or change outliers.</span></span> <span data-ttu-id="c1faa-118">使用する方法は、値が不連続値か連続値かによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c1faa-118">The method that you use depends on whether the values are discrete or continuous.</span></span>  
  
     <span data-ttu-id="c1faa-119">このウィザードでは不連続値は横棒グラフで表示されます。横棒グラフの各横棒はデータの特定の値を表し、横棒の長さは各値のケース数を表します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-119">The wizard displays discrete values in a bar chart, where each bar represents a specific value, and the height of the bar indicates the number of cases for each value.</span></span> <span data-ttu-id="c1faa-120">グラフのしきい値コントロールをスライドすると、極端な値や誤っている可能性がある値のグループを表す横棒を削除できます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-120">By sliding the threshold control on the chart, you can cut off bars that represent groups of extreme or potentially bad values.</span></span>  
  
-   <span data-ttu-id="c1faa-121">連続値は、横棒グラフまたは折れ線グラフで表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-121">The wizard displays continuous values either on a bar chart or line chart.</span></span> <span data-ttu-id="c1faa-122">折れ線グラフの場合、X 軸が値を表し、Y 軸が値の数を表します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-122">On the line chart, the value is represented on the x-axis and the count of values on the y-axis.</span></span>  
  
     <span data-ttu-id="c1faa-123">**最小**値と**最大**値を変更するか、横棒をスライドさせることで、グラフの最低値と最高値を削除するか、維持するかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-123">You can control whether to remove or keep values at the low and high ends of the chart by changing the **Minimum** and **Maximum** values, or sliding the bars.</span></span> <span data-ttu-id="c1faa-124">最小値および最大値の設定を変更すると、非表示になるデータにグラフ上で網掛けが付けられます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-124">As you change the minimum and maximum value settings, the data that will be suppressed is shown by shading in the graph.</span></span>  
  
 <span data-ttu-id="c1faa-125">処理する外れ値を選択した後で、その外れ値の処理方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-125">After you have selected which outliers to work with, you tell the wizard how to handle the outliers.</span></span> <span data-ttu-id="c1faa-126">外れ値を含む行を削除するか、平均値、NULL、または選択したその他の値など、置換値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-126">You can either delete the rows that contain the outlier values, or you can specify a replacement value, such as a mean, a null, or another value of your choice.</span></span>  
  
 <span data-ttu-id="c1faa-127">最後に、新しいデータの表示方法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-127">Finally, the wizard gives you some options for displaying the new data.</span></span> <span data-ttu-id="c1faa-128">元データを新しい値で置き換えたり、新しい値が格納されている新しい列をテーブルに追加したり、更新されたデータが格納されている新しいワークシートを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-128">You can replace the original data with the new values, add a new column to the table that contains the new values, or create a new worksheet that contains the updated data.</span></span>  
  
### <a name="using-the-outlier-wizard"></a><span data-ttu-id="c1faa-129">外れ値の削除ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="c1faa-129">Using the Outlier Wizard</span></span>  
  
1.  <span data-ttu-id="c1faa-130">[**データマイニング**] リボンで、[**データの消去**] をクリックし、[**外れ**値] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-130">In the **Data Mining** ribbon, click **Clean Data**, and select **Outliers**.</span></span>  
  
2.  <span data-ttu-id="c1faa-131">[**ソースデータの選択**] ダイアログボックスで、Excel データテーブルまたはセルの範囲を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1faa-131">In the **Select Source Data** dialog box, select an Excel data table, or a range of cells, and click **Next**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="c1faa-132">外部データに対して**外れ**値ウィザードを使用することはできません。最初に Excel にコピーする場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-132">You cannot use the **Outliers** wizard on external data, unless you copy it to Excel first.</span></span>  
  
3.  <span data-ttu-id="c1faa-133">**[列の選択**] ダイアログボックスで、 **1 つ**の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-133">In the **Select Column** dialog box, select a **single** column.</span></span>  
  
     <span data-ttu-id="c1faa-134">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1faa-134">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="c1faa-135">[**しきい値の指定**] ダイアログボックスで、データの分布を確認します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-135">In the **Specify Thresholds** dialog box, review the distribution of data.</span></span>  
  
    -   <span data-ttu-id="c1faa-136">列に不連続値が含まれている場合は、各不連続値の件数を記載したヒストグラムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-136">If the column contains discrete values, the wizard displays a histogram containing the count for each discrete value.</span></span>  
  
         <span data-ttu-id="c1faa-137">外れ値がまれな値であると仮定すると、**最小**値を変更することでフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-137">Assuming that outliers are rare values, you can filter them out by changing the **Minimum** value.</span></span>  
  
    -   <span data-ttu-id="c1faa-138">列に数値データが含まれている場合は、[**不連続として表示**] ボタンまたは [**数値と**して表示] ボタンをクリックして、横棒グラフまたは折れ線グラフの値の表示を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-138">If the column contains numeric data, you can click the **View as Discrete** button or the **View as Numeric** button to toggle between viewing the values in a bar chart or line chart.</span></span>  
  
5.  <span data-ttu-id="c1faa-139">[**しきい値の指定**] ダイアログボックスで、最小値と最大値を入力するか、スライダーバーをドラッグして、保持するデータの範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-139">In the **Specify Thresholds** dialog box, choose the range of data you want to keep by typing a minimum and maximum value, or by dragging the slider bars.</span></span> <span data-ttu-id="c1faa-140">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1faa-140">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="c1faa-141">[**外れ値の処理**] ダイアログボックスで、値を削除するか置換するかを指定し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1faa-141">In the **Outlier Handling** dialog box, specify whether you want the values to be deleted or replaced, and click **Next**.</span></span>  
  
7.  <span data-ttu-id="c1faa-142">**[変換先の選択**] ダイアログボックスで、新しいデータを保存する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-142">In the **Select Destination** dialog box, specify where you want the new data to be saved.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="c1faa-143">関連オプション</span><span class="sxs-lookup"><span data-stu-id="c1faa-143">Related Options</span></span>  
 <span data-ttu-id="c1faa-144">ウィザードには次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="c1faa-144">The wizard provides these options:</span></span>  
  
|<span data-ttu-id="c1faa-145">**Options**</span><span class="sxs-lookup"><span data-stu-id="c1faa-145">**Options**</span></span>|<span data-ttu-id="c1faa-146">**コメント**</span><span class="sxs-lookup"><span data-stu-id="c1faa-146">**Comment**</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c1faa-147">**列の選択**</span><span class="sxs-lookup"><span data-stu-id="c1faa-147">**Select Column**</span></span>|<span data-ttu-id="c1faa-148">一度に 1 つの列のみを操作できます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-148">You can work with only one column at a time.</span></span>|  
|<span data-ttu-id="c1faa-149">**しきい値の処理方法の指定**</span><span class="sxs-lookup"><span data-stu-id="c1faa-149">**Specify Thresholds Handling**</span></span>|<span data-ttu-id="c1faa-150">**最小**値を使用してしきい値を設定し、しきい値よりも少ない行数で検出された値を除外します。</span><span class="sxs-lookup"><span data-stu-id="c1faa-150">Set a threshold using **Minimum** to exclude values that are found in fewer rows than the threshold value.</span></span><br /><br /> <span data-ttu-id="c1faa-151">初期状態では、**最小**値は行が最も少ない値と等しく、最小値をその値より小さくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c1faa-151">Initially the value in **Minimum** is equal to the value with the fewest rows, and you cannot make the minimum lower than that value.</span></span>|  
|<span data-ttu-id="c1faa-152">**外れ値の処理**</span><span class="sxs-lookup"><span data-stu-id="c1faa-152">**Outlier Handling**</span></span>|<span data-ttu-id="c1faa-153">外れ値を削除する場合、現在のワークシート内のデータを変更することも、新しいワークシートにデータのコピーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c1faa-153">If you decide to delete outliers, you can either change the data in the current worksheet, or create a copy of the data in a new worksheet.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1faa-154">参照</span><span class="sxs-lookup"><span data-stu-id="c1faa-154">See Also</span></span>  
 [<span data-ttu-id="c1faa-155">データ &#40;SQL Server データマイニングアドインの探索&#41;</span><span class="sxs-lookup"><span data-stu-id="c1faa-155">Explore Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](explore-data-sql-server-data-mining-add-ins.md)  
  
  
