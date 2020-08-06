---
title: 予測モデルの調査 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 86bd6371a8d32c53c68351aaff36a317f7433ef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720499"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="01d0a-102">予測モデルの検証 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="01d0a-102">Exploring the Forecasting Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="01d0a-103">予測マイニングモデルを作成したので、データマイニングデザイナーの [**マイニングモデルビューアー** ] タブを使用して結果を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-103">Now that you have built the forecasting mining model, you can explore the results by using the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="01d0a-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]タイムシリーズビューアーには、**グラフ**と**モデル**の2つのタブがあります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer contains two tabs: **Charts** and **Model**.</span></span>  
  
 <span data-ttu-id="01d0a-105">また、すべてのモデルで Microsoft 汎用ツリー ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-105">Additionally, you can use the Microsoft Generic Tree Viewer with all models.</span></span> <span data-ttu-id="01d0a-106">それぞれのビューに、時系列モデルの情報が少しずつ異なる方法で表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-106">Each view presents a slightly different picture of the information in the time series model.</span></span>  
  
-   <span data-ttu-id="01d0a-107">[[グラフ] タブ](#bkmk_Charts)</span><span class="sxs-lookup"><span data-stu-id="01d0a-107">[Charts Tab](#bkmk_Charts)</span></span>  
  
-   <span data-ttu-id="01d0a-108">[[モデル] タブ](#bkmk_Model)</span><span class="sxs-lookup"><span data-stu-id="01d0a-108">[Model Tab](#bkmk_Model)</span></span>  
  
-   [<span data-ttu-id="01d0a-109">Microsoft 汎用コンテンツ ビューアー</span><span class="sxs-lookup"><span data-stu-id="01d0a-109">Microsoft Generic Content Viewer</span></span>](#bkmk_Content)  
  
##  <a name="charts-tab"></a><a name="bkmk_Charts"></a><span data-ttu-id="01d0a-110">[グラフ] タブ</span><span class="sxs-lookup"><span data-stu-id="01d0a-110">Charts Tab</span></span>  
 <span data-ttu-id="01d0a-111">タイムシリーズビューアーの [**グラフ**] タブには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 履歴データと予測を含む各系列がグラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-111">The **Charts** tab of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer graphically shows you each of the series, including historical data and predictions.</span></span> <span data-ttu-id="01d0a-112">時系列グラフのそれぞれの線は、製品、地域、および予測可能な属性の一意の組み合わせを表します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-112">Each line in the time series graph represents a unique combination of product, region, and predictable attribute.</span></span>  
  
 <span data-ttu-id="01d0a-113">ビューアーの右側の凡例には、ドロップダウン リストでの選択に基づいて、選択可能なすべての時系列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-113">The legend on the right side of the viewer lists the time series that available, based on the selections in the drop-down list.</span></span> <span data-ttu-id="01d0a-114">凡例で、これらのチェック ボックスをオンまたはオフにして、グラフに表示する時系列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-114">You can select and clear the check boxes in the legend to control which time series displays in the graph.</span></span>  
  
 <span data-ttu-id="01d0a-115">各時系列に対して使用する色などの表示オプション、またはグラフの点に値を表示するかどうかを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-115">You can also change the display options, such as the colors used for each time series, or whether values are displayed at points in the chart.</span></span>  
  
#### <a name="to-select-a-time-series"></a><span data-ttu-id="01d0a-116">時系列を選択するには</span><span class="sxs-lookup"><span data-stu-id="01d0a-116">To select a time series</span></span>  
  
1.  <span data-ttu-id="01d0a-117">[**マイニングモデルビューアー** ] タブが表示されていない場合は、[**グラフ**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-117">Click the **Charts** tab of the **Mining Model Viewer** tab, if it is not visible.</span></span>  
  
2.  <span data-ttu-id="01d0a-118">グラフ ビューの右側にあるドロップダウン リストをクリックし、すべてのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-118">Click the drop-down list to the right of the chart view, and select all the check boxes.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="01d0a-119">グラフに 24 本の異なる系列線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-119">The chart should now contain 24 different series lines.</span></span>  
  
3.  <span data-ttu-id="01d0a-120">グラフの右側にあるチェックボックスをオフにして、金額に基づくすべての系列の線を一時的に非表示にします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-120">In the check boxes to the right of the chart, clear the boxes to temporarily hide the lines for all series that are based on Amount.</span></span>  
  
     <span data-ttu-id="01d0a-121">次に、R750 と R250 という自転車に関連するチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-121">Now, clear the check boxes related to the R750 and R250 bicycles.</span></span>  
  
     <span data-ttu-id="01d0a-122">これで、グラフに含まれる系列線は次の 6 つだけになるため、M200 と T1000 という自転車の傾向を比較しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-122">The chart now contains just the following six series lines, so that can you more easily compare trends for the M200 and T1000 bicycles.</span></span>  
  
    -   <span data-ttu-id="01d0a-123">**M200 Europe: Quantity**</span><span class="sxs-lookup"><span data-stu-id="01d0a-123">**M200 Europe: Quantity**</span></span>  
  
    -   <span data-ttu-id="01d0a-124">**M200 North America: Quantity**</span><span class="sxs-lookup"><span data-stu-id="01d0a-124">**M200 North America: Quantity**</span></span>  
  
    -   <span data-ttu-id="01d0a-125">**M200 Pacific: Quantity**</span><span class="sxs-lookup"><span data-stu-id="01d0a-125">**M200 Pacific: Quantity**</span></span>  
  
    -   <span data-ttu-id="01d0a-126">**T1000 Europe: Quantity**</span><span class="sxs-lookup"><span data-stu-id="01d0a-126">**T1000 Europe: Quantity**</span></span>  
  
    -   <span data-ttu-id="01d0a-127">**T1000 North America: Quantity**</span><span class="sxs-lookup"><span data-stu-id="01d0a-127">**T1000 North America: Quantity**</span></span>  
  
    -   <span data-ttu-id="01d0a-128">**T1000 Pacific: Quantity**</span><span class="sxs-lookup"><span data-stu-id="01d0a-128">**T1000 Pacific: Quantity**</span></span>  
  
 <span data-ttu-id="01d0a-129">![M200 および T1000 の数量を予測するシリーズ](../../2014/tutorials/media/6series-defaultforecasting.gif "M200 および T1000 の数量を予測するシリーズ")</span><span class="sxs-lookup"><span data-stu-id="01d0a-129">![Series predicting M200 and T1000 quantity](../../2014/tutorials/media/6series-defaultforecasting.gif "Series predicting M200 and T1000 quantity")</span></span>  
  
 <span data-ttu-id="01d0a-130">このビューアーに表示されるグラフには、履歴データと予測データの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-130">The chart that is displayed in this viewer includes both historical and predicted data.</span></span> <span data-ttu-id="01d0a-131">履歴データと区別できるよう、予測データの部分は網掛けされています。</span><span class="sxs-lookup"><span data-stu-id="01d0a-131">Predicted data is shaded to differentiate it from historical data.</span></span> <span data-ttu-id="01d0a-132">個々の系列を比較しやすくするために、グラフのそれぞれの線に関連付けられている色を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-132">To make it easier to compare different series, you can also change the colors associated with each line in the graph.</span></span> <span data-ttu-id="01d0a-133">詳細については、「 [データ マイニング ビューアーで使用する色の変更](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01d0a-133">For more information, see [Change the Colors Used in the Data Mining Viewer](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md).</span></span>  
  
 <span data-ttu-id="01d0a-134">これらの傾向線からは、どの地域でも総売上がしだいに増加しており、12 か月目 (つまり 12 月) でピークに達していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-134">From the trend lines, you can see that total sales for all regions are generally increasing, with a peak every 12 months in December.</span></span> <span data-ttu-id="01d0a-135">またグラフから、T1000 という自転車のデータが他の製品系列のデータより大幅に遅れて始まっていることもわかります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-135">From the chart, you can also see that the data for the T1000 bicycle starts much later than the data for the other product series.</span></span> <span data-ttu-id="01d0a-136">これは、この製品が新しい製品であるためです。この系列については、基になるデータが十分でないため、正確な予測が得られない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-136">That is because it is a newer product, but because this series is based on much less data, the predictions might not be as accurate.</span></span>  
  
 <span data-ttu-id="01d0a-137">既定では、各時系列について、5 つの予測期間分の予測が点線で表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-137">By default, five prediction steps are shown for each time series, displayed as dotted lines.</span></span> <span data-ttu-id="01d0a-138">この値を変更して、表示する予測を増減することもできます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-138">You can change this value to view more or fewer predictions.</span></span> <span data-ttu-id="01d0a-139">グラフに誤差帯を追加することで、予測の標準偏差をグラフィカルに表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-139">You can also graphically view the standard deviation for the predictions by adding error bars to the chart.</span></span>  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a><span data-ttu-id="01d0a-140">グラフ ビューの予測オプションと表示オプションを変更するには</span><span class="sxs-lookup"><span data-stu-id="01d0a-140">To change prediction and display options in the Chart view</span></span>  
  
1.  <span data-ttu-id="01d0a-141">**予測手順**の値を徐々に変更し、 **5**から**10**に増やしてから**6**に戻します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-141">Try changing the value for **Prediction Steps** gradually, increasing it from **5** to **10**, and then back to **6**.</span></span>  
  
     <span data-ttu-id="01d0a-142">履歴データの変動幅が大きい場合は、予測の数を増やすと変動が繰り返される傾向にあり、増幅されることもあります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-142">When the historical data has large fluctuations, the fluctuations tend to be repeated or even amplified as you increase the number of predictions.</span></span> <span data-ttu-id="01d0a-143">多くの場合、この時点である程度の調査が必要になります。この調査で、履歴データの大幅な増加の原因を特定し、それらの結果をそのまま使用するか、ソース データに修正する箇所がないかどうかを探すか、モデルの線をいずれかの方法で滑らかにするかを判断することになります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-143">You probably need to do some research at this point, to understand the cause of the big increase in the historical data and then decide whether to accept these results, seek some kind of correction in the source data, or apply some kind of smoothing in the model.</span></span>  
  
2.  <span data-ttu-id="01d0a-144">[**偏差の表示**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-144">Select the **Show Deviations** check box.</span></span>  
  
     <span data-ttu-id="01d0a-145">このオプションをオンにすると、それぞれの予測値について、推定される誤差が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-145">This option displays the estimated error for each predicted value.</span></span>  
  
3.  <span data-ttu-id="01d0a-146">X 軸のスケールを確認します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-146">Note the scale of the X-axis.</span></span> <span data-ttu-id="01d0a-147">履歴データと予測データの変化はどちらも常に比率で表されますが、実際の値はグラフにすべての値が表示されるように自動的に調整されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-147">The changes over both historical and predicted data are always expressed as a percentage, but the actual values are adjusted automatically to fit all values onto the graph.</span></span> <span data-ttu-id="01d0a-148">そのため、モデルを比較するときは、視覚的な見た目だけに頼らないように注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="01d0a-148">Therefore you need to be careful when comparing models to not rely on visuals alone.</span></span> <span data-ttu-id="01d0a-149">正確な値、または予測の増加率と値の割合を取得するには、点線または実線の上にマウスポインターを置くか、線をクリックして [**マイニング凡例**] の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-149">To get the exact value, or the percentage increase and value for predictions, pause the mouse over the dotted line or solid lines, or click the lines to view the values in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="01d0a-150">**ヒント**: [**マイニング凡例**] が表示されていない場合は、**モデル**ビューに切り替え、任意のノードを右クリックして、[**凡例の表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-150">**Tip**: If the **Mining Legend** is not visible, switch to **Model** view, right-click any node, and select **Show Legend**.</span></span>  
  
 <span data-ttu-id="01d0a-151">これらの傾向を見て、一部の系列のデータが十分でないことが気になるときは、モデル別の売上の平均 (地域別の売上の平均など) を求めて予測の信頼性を高めることもできます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-151">From looking at these trends, you are concerned about the lack of data for some of the series, and wonder if you might get more reliable predictions by averaging sales by model, or perhaps averaging sales by region.</span></span> <span data-ttu-id="01d0a-152">この方法については、このチュートリアルのレッスンで後ほど説明します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-152">You will explore this approach in a later lesson in this tutorial.</span></span>  
  
 [<span data-ttu-id="01d0a-153">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="01d0a-153">Back to Top</span></span>](#bkmk_Charts)  
  
##  <a name="model-tab"></a><a name="bkmk_Model"></a><span data-ttu-id="01d0a-154">[モデル] タブ</span><span class="sxs-lookup"><span data-stu-id="01d0a-154">Model Tab</span></span>  
 <span data-ttu-id="01d0a-155">データマイニングデザイナーのタイムシリーズビューアーの [**モデル**] タブでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 予測モデルをツリーグラフの形式で表示できます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-155">The **Model** tab of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer in Data Mining Designer lets you view the forecasting model in the form of a tree graph.</span></span>  
  
 <span data-ttu-id="01d0a-156">最初に注目する点は、ここで使用しているデータでは、複数の製品ライン (T1000 など) について、売上を示すメジャーがそれぞれ 2 つ (Amount と Quantity) あり、地域がそれぞれ 3 つ (ヨーロッパ、北米、および太平洋) に分かれているため、作成したモデルは実質的に 24 個のツリーで構成されているということです。それらの各ツリーが、地域、製品、および予測可能な属性の組み合わせがそれぞれ異なる売上パターンのモデルを表しています。</span><span class="sxs-lookup"><span data-stu-id="01d0a-156">First, notice that because your data describes two different measures (Amount and Quantity) for sales of multiple product lines (T1000, etc.) in three different regions (Europe, North America, and Pacific), the model that you built actually contains 24 different trees, each tree representing a model of the sales patterns for a different combination of region, product, and predictable attribute.</span></span>  
  
 <span data-ttu-id="01d0a-157">[**モデル**] タブの [**ツリー** ] ボックスの一覧から系列を選択すると、表示する製品ライン、地域、および販売メトリックの組み合わせを選択できます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-157">You can choose which combination of product line, region, and sales metric you want to view by selecting a series from the **Tree** dropdown list on the **Model** tab.</span></span>  
  
 <span data-ttu-id="01d0a-158">ここで、モデルをツリーとして表示すると何がわかるか考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="01d0a-158">So what can you learn from viewing the model as a tree?</span></span> <span data-ttu-id="01d0a-159">例として、2つのモデルを比較してみましょう。1つはツリー内に複数のレベルを持ち、もう1つは1つのノードを持つモデルです。</span><span class="sxs-lookup"><span data-stu-id="01d0a-159">As an example, let's compare two models, one that has several levels in the tree, and one that has a single node.</span></span>  
  
-   <span data-ttu-id="01d0a-160">ツリー グラフのノードが 1 つだけの場合は、モデルで検出された傾向が時間の経過によってほとんど変化しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-160">When a tree graph contains a single node, it means the trend found in the model is mostly homogenous over time.</span></span> <span data-ttu-id="01d0a-161">この1つのノードである [**すべて**] を使用すると、入力変数と結果の関係を示す式を表示できます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-161">You can use this single node, labeled **All**, to view the formula that describes the relationship between the input variables and the outcome.</span></span>  
  
-   <span data-ttu-id="01d0a-162">時系列のツリー グラフに複数の分岐がある場合は、検出された時系列が複雑すぎて、1 つの式では表せないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-162">When a tree graph for a time series has multiple branches, it means the time series that was detected is too complex to be represented as a single equation.</span></span> <span data-ttu-id="01d0a-163">代わりに、ツリーグラフに複数の分岐が含まれている可能性があります。各分岐には、ツリーが*分割*される原因となった条件がラベル付けされています。</span><span class="sxs-lookup"><span data-stu-id="01d0a-163">Instead, the tree graph might contain multiple branches, each branch labeled with the conditions that caused the tree to *split*.</span></span> <span data-ttu-id="01d0a-164">ツリーが分割されている場合、各分岐はそれぞれの時間の単位を表し、その時間単位ごとに 1 つの式で傾向を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-164">When the tree splits, each branch represents a different segment of time, inside which the trend can be described as a single equation.</span></span>  
  
     <span data-ttu-id="01d0a-165">たとえば、グラフグラフを見ているときに、9月に開始された売上ボリュームの急激なジャンプと、年の終わりの休日を確認すると、**モデル**ビューに切り替えて、傾向が変更された正確な日付を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-165">For example, if you look at the chart graph and see a sudden jump in sales volume starting sometime in September and continuing through a year-end holiday, you can switch to the **Model** view to see the exact date where the trend changed.</span></span> <span data-ttu-id="01d0a-166">"9 月前" と "9 月以降" を表すツリー内の分岐には、さまざまな数式が含まれます。たとえば、分割までの売上傾向を計算する数式と、年9月から年末の休日までの売上傾向を示すもう1つの数式があります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-166">The branches in the tree that represent "before September" and "after September" would contain different formulas: one formula that mathematically describes the sales trends up to the split, and another formula that describes sales trends for September through the year-end holiday.</span></span>  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a><span data-ttu-id="01d0a-167">時系列モデルに対応するデシジョン ツリーを調査するには</span><span class="sxs-lookup"><span data-stu-id="01d0a-167">To explore the decision tree for a time series model</span></span>  
  
1.  <span data-ttu-id="01d0a-168">ビューアーの [**モデル**] タブの [**ツリー** ] ボックスの一覧で、[ **T1000 欧州: Amount** ] 系列を選択します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-168">In the **Tree** list on the **Model** tab of the viewer, select the **T1000 Europe: Amount** series.</span></span>  
  
     <span data-ttu-id="01d0a-169">[**すべて**] というラベルの付いたノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-169">Click the node labeled **All**.</span></span>  
  
     <span data-ttu-id="01d0a-170">**すべて**のノードについて、表示されるツールヒントには、系列全体のケースの数、データの分析から得られた時系列式などの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-170">For an **All** node, the ToolTip that appears includes information such as, the number of cases in the entire series, and time series equations derived from analysis of the data.</span></span>  
  
2.  <span data-ttu-id="01d0a-171">[**マイニング凡例**] が表示されていない場合は、ノードを右クリックし、[**凡例の表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-171">If the **Mining Legend** is not visible, right-click the node and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="01d0a-172">**マイニング凡例**には、ツールヒントに表示される情報とほぼ同じ情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-172">The **Mining Legend** provides much the same information that is in the Tooltip.</span></span> <span data-ttu-id="01d0a-173">不連続な独立変数がある場合は、ノード内の変数の分布を示すヒストグラムも表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-173">If any of your independent variables are discrete, you will also see a histogram that shows the distribution of variables in the node.</span></span>  
  
3.  <span data-ttu-id="01d0a-174">次に、別の時系列を選択して表示します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-174">Now select a different time series to view.</span></span> <span data-ttu-id="01d0a-175">ビューアーの [**モデル**] タブにある**ツリー**リストを使用して、[ **M200 北米: Amount** ] 系列を選択します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-175">Using the **Tree** list on the **Model** tab of the viewer, select the **M200 North America: Amount** series.</span></span>  
  
     <span data-ttu-id="01d0a-176">ツリーグラフには、**すべて**のノードと2つの子ノードが含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="01d0a-176">The tree graph now contains an **All** node and two child nodes.</span></span> <span data-ttu-id="01d0a-177">子ノードのラベルから、どの時点で傾向線が変化したか確認できます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-177">By looking at the labels on the child nodes, you can understand at what point the trend line changed.</span></span>  
  
     <span data-ttu-id="01d0a-178">各子ノードについて、**マイニング凡例**の説明には、ツリーの各分岐のケースの数も含まれます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-178">For each child node, the description in the **Mining Legend** also includes the count of cases in each branch of the tree.</span></span>  
  
 <span data-ttu-id="01d0a-179">ツリー ビューアーには、ほかにも次のような機能があります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-179">The following list describes some additional features in the tree viewer:</span></span>  
  
-   <span data-ttu-id="01d0a-180">グラフに表示される変数は、**背景**コントロールを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-180">You can change the variable that is represented in the chart by using the **Background** control.</span></span> <span data-ttu-id="01d0a-181">既定では、[**背景**] の値が [**母集団**] に設定されているため、暗いノードにはより多くのケースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-181">By default, nodes that are darker contain more cases, because the value of **Background** is set to **Population**.</span></span> <span data-ttu-id="01d0a-182">ノードに存在するケースの数を確認するには、ノード上でマウスポインターをポイントし、表示されたツールヒントを表示するか、ノードをクリックして [**ノードの凡例**] ウィンドウで数値を表示します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-182">To see just how many cases there are in a node, pause the mouse over a node and view the ToolTip that appears, or click the node and view the numbers in the **Node Legend** window.</span></span>  
  
-   <span data-ttu-id="01d0a-183">ツールヒントにはノードの回帰式も表示されます。これについても、ノードをクリックして確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-183">The regression formula for the node can also be viewed in the ToolTip, or by clicking the node.</span></span> <span data-ttu-id="01d0a-184">混合モデルを作成した場合は、ARIMA の式 (リーフ ノード内) と ARTXP の式 (ツリーのルート ノード内) の 2 つが表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-184">If you have created a mixed model, you can see two formulas, one for ARTXP (in the leaf nodes) and one for ARIMA (in the root node of the tree).</span></span>  
  
-   <span data-ttu-id="01d0a-185">ノードでは、連続する数値が小さなひし形で表されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-185">The little diamonds are used in nodes that represent continuous numbers.</span></span> <span data-ttu-id="01d0a-186">属性の範囲は、そのひし形が示されたバーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-186">The range of the attributes is shown in the bar on which the diamond rests.</span></span> <span data-ttu-id="01d0a-187">このひし形はノードの中間にあり、ひし形の幅がそのノードの属性の分散を表します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-187">The diamond is centered on the mean for the node, and the width of the diamond represents the variance of the attribute at that node.</span></span>  
  
 [<span data-ttu-id="01d0a-188">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="01d0a-188">Back to Top</span></span>](#bkmk_Charts)  
  
##  <a name="optional-generic-content-tree-viewer"></a><a name="bkmk_Content"></a><span data-ttu-id="01d0a-189">Optional汎用コンテンツツリービューアー</span><span class="sxs-lookup"><span data-stu-id="01d0a-189">(Optional) Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="01d0a-190">タイムシリーズのカスタムビューアーに加えて、には、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] すべてのデータマイニングモデルで使用するための**Microsoft 汎用コンテンツツリービューアー**が用意されています。</span><span class="sxs-lookup"><span data-stu-id="01d0a-190">In addition to the custom viewer for time series, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides the **MicrosoftGeneric Content Tree Viewer** for use with all data mining models.</span></span> <span data-ttu-id="01d0a-191">このビューアーには、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-191">This viewer provides some advantages:</span></span>  
  
-   <span data-ttu-id="01d0a-192">**Microsoft タイムシリーズビューアー**: このビューでは、2つのアルゴリズムの結果がマージされます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-192">**Microsoft Time Series Viewer**: This view merges the results of the two algorithms.</span></span> <span data-ttu-id="01d0a-193">各系列を別々に表示することもできますが、その場合、各アルゴリズムの結果がどのように結合されたかを判別できません。</span><span class="sxs-lookup"><span data-stu-id="01d0a-193">Although you can view each series separately, you cannot determine how the results of each algorithm were combined.</span></span> <span data-ttu-id="01d0a-194">また、このビューでは、ツールチップと [マイニング凡例] に重要な統計情報だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-194">Also, in this view, the Tooltips and Mining Legend show only the most important statistics.</span></span>  
  
-   <span data-ttu-id="01d0a-195">**汎用コンテンツツリービューアー**: モデルで一度に使用されたすべてのデータ系列を参照および表示できます。また、混合モデルを作成した場合は、ARIMA ツリーと artxp ツリーの両方が同じグラフに表示されます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-195">**Generic Content Tree Viewer**: Lets you browse and view all of the data series that were used in the model at one time, and if you have created a mixed model, both the ARIMA and ARTXP trees are displayed in the same graph.</span></span>  
  
     <span data-ttu-id="01d0a-196">このビューアーを使用すると、両方のアルゴリズムからすべての統計情報を取得できるだけでなく、値の分布も確認できます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-196">You can use this viewer to get all the statistics from both algorithms, as well as distributions of the values.</span></span>  
  
     <span data-ttu-id="01d0a-197">ARIMA と ARTXP の分析について詳しく調べたい場合など、データ マイニングの上級ユーザー向けのビューアーです。</span><span class="sxs-lookup"><span data-stu-id="01d0a-197">Recommended for expert users of data mining who want to know more about the ARIMA and ARTXP analyses.</span></span>  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a><span data-ttu-id="01d0a-198">汎用コンテンツ ビューアーで特定のデータ系列の詳細を表示するには</span><span class="sxs-lookup"><span data-stu-id="01d0a-198">To view details for a particular data series in the generic content viewer</span></span>  
  
1.  <span data-ttu-id="01d0a-199">[**マイニングモデルビューアー** ] タブで、[**ビューアー** ] ボックスの一覧から [ **Microsoft 汎用コンテンツツリービューアー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-199">In the **Mining Model Viewer** tab, select **Microsoft Generic Content Tree Viewer** from the **Viewer** drop-down list.</span></span>  
  
2.  <span data-ttu-id="01d0a-200">[**ノードのキャプション**] ペインで、最上位の [すべて] ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-200">In the **Node Caption** pane, click the topmost (All) node.</span></span>  
  
3.  <span data-ttu-id="01d0a-201">[**ノードの詳細**] ペインで、[ATTRIBUTE_NAME] の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-201">In the **Node Details** pane, view the value for ATTRIBUTE_NAME.</span></span>  
  
     <span data-ttu-id="01d0a-202">この値から、このノードにどの系列 (製品と地域の組み合わせ) が含まれているかがわかります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-202">This value shows you which series, or combination of product and region, is contained in this node.</span></span> <span data-ttu-id="01d0a-203">AdventureWorks の例では、最上位ノードは M200 Europe 系列のノードです。</span><span class="sxs-lookup"><span data-stu-id="01d0a-203">In the AdventureWorks example, the topmost node is for the M200 Europe series.</span></span>  
  
4.  <span data-ttu-id="01d0a-204">[**ノードのキャプション**] ペインで、子ノードを持つ最初のノードを見つけます。</span><span class="sxs-lookup"><span data-stu-id="01d0a-204">In the **Node Caption** pane, locate the first node that has child nodes.</span></span>  
  
     <span data-ttu-id="01d0a-205">系列ノードに子がある場合、Microsoft タイムシリーズビューアーの [**モデル**] タブに表示されるツリービューにも分岐構造があります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-205">If a series node has children, the tree view that appears on the **Model** tab of the Microsoft Time Series Viewer will also have a branching structure.</span></span>  
  
5.  <span data-ttu-id="01d0a-206">ノードを展開し、いずれかの子ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="01d0a-206">Expand the node and click one of the child nodes.</span></span>  
  
     <span data-ttu-id="01d0a-207">スキーマの NODE_DESCRIPTION 列に、ツリーが分割される原因になった条件が含まれています。</span><span class="sxs-lookup"><span data-stu-id="01d0a-207">The NODE_DESCRIPTION column of the schema contains the condition that caused the tree to split.</span></span>  
  
6.  <span data-ttu-id="01d0a-208">[**ノードのキャプション**] ペインで、最上位の ARIMA ノードをクリックし、すべての子ノードが表示されるまでノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-208">In the **Node Caption** pane, click the topmost ARIMA node, and expand the node until all child nodes are visible.</span></span>  
  
7.  <span data-ttu-id="01d0a-209">[**ノードの詳細**] ペインで、[ATTRIBUTE_NAME] の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="01d0a-209">In the **Node Details** pane, view the value for ATTRIBUTE_NAME.</span></span>  
  
     <span data-ttu-id="01d0a-210">この値から、このノードに含まれている時系列がわかります。</span><span class="sxs-lookup"><span data-stu-id="01d0a-210">This value tells you which time series is contained in this node.</span></span> <span data-ttu-id="01d0a-211">ARIMA セクションの最上位ノードは [(すべて)] セクションの最上位ノードと一致するはずです。</span><span class="sxs-lookup"><span data-stu-id="01d0a-211">The topmost node in the ARIMA section should match the topmost node in the (All) section.</span></span> <span data-ttu-id="01d0a-212">AdventureWorks の例では、このノードには M200 Europe 系列に対する ARIMA 分析が含まれています。</span><span class="sxs-lookup"><span data-stu-id="01d0a-212">In the AdventureWorks example, this node contains the ARIMA analysis for the series, M200 Europe.</span></span>  
  
 <span data-ttu-id="01d0a-213">詳細については、「[タイム シリーズ モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01d0a-213">For more information, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="01d0a-214">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="01d0a-214">Back to Top</span></span>](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="01d0a-215">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="01d0a-215">Next Task in Lesson</span></span>  
 [<span data-ttu-id="01d0a-216">タイムシリーズ予測の作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="01d0a-216">Creating Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="01d0a-217">参照</span><span class="sxs-lookup"><span data-stu-id="01d0a-217">See Also</span></span>  
 <span data-ttu-id="01d0a-218">[タイムシリーズモデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="01d0a-218">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="01d0a-219">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="01d0a-219">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
