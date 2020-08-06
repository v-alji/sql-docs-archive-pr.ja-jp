---
title: 予測モデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- forecasting [data mining]
- mining models, viewing
- mining model, time series
- time series [data mining]
ms.assetid: ad35a528-1949-4048-8678-3b9760c1c88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d0b188c4ed6fba9bc5b1082725b17c99081c1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633571"
---
# <a name="browsing-a-forecasting-model"></a><span data-ttu-id="261d1-102">予測モデルの参照</span><span class="sxs-lookup"><span data-stu-id="261d1-102">Browsing a Forecasting Model</span></span>
  <span data-ttu-id="261d1-103">[**参照**] を使用して予測モデルを開くと、のタイムシリーズモデルビューアーに似た対話型ビューアーにモデルが表示され [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="261d1-103">When you open a forecasting model using **Browse**, the model is displayed in an interactive viewer, similar to the time series model viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="261d1-104">ビューアーは、傾向の調査、系列の比較、予測の作成、およびモデルと基になるデータに関する情報の取得に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="261d1-104">The viewer helps you explore trends, compare series, create predictions, and get information about the model and the underlying data.</span></span>  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a><span data-ttu-id="261d1-105">モデルの調査</span><span class="sxs-lookup"><span data-stu-id="261d1-105">Explore the Model</span></span>  
 <span data-ttu-id="261d1-106">予測モデルの**参照**ビューアーには、時間の経過に伴う傾向を示すグラフビューが用意されています。また、予測を作成できます。また、時系列をデシジョンツリーまたは回帰ツリーとして表すモデルビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-106">The **Browse** viewer for forecasting models provides a chart view, which shows the trends over time and lets you create predictions, and a model view, which represents the time series as a decision tree or a regression tree.</span></span>  
  
-   [<span data-ttu-id="261d1-107">グラフ ビュー</span><span class="sxs-lookup"><span data-stu-id="261d1-107">Chart view</span></span>](#bkmk_charts)  
  
-   [<span data-ttu-id="261d1-108">モデル ビュー</span><span class="sxs-lookup"><span data-stu-id="261d1-108">Model view</span></span>](#bkmk_Model)  
  
 <span data-ttu-id="261d1-109">予測モデルを試してみるには、サンプルデータブックの [予測] タブにあるサンプルデータを使用し、[**データマイニング**] リボンの [ [Excel 用データマイニングアドイン] &#40;](forecast-wizard-data-mining-add-ins-for-excel.md) [予測ウィザード] を使用してタイムシリーズモデルを作成するか、または [**分析**] リボンの [ [&#41;excel 用テーブル分析ツールを予測 &#40;](forecast-table-analysis-tools-for-excel.md)&#41;ます。</span><span class="sxs-lookup"><span data-stu-id="261d1-109">To experiment with a forecasting model, you can use the sample data on the Forecast tab of the sample data workbook, and build a time series model using the [Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) in the **Data Mining** ribbon, or [Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) in the **Analyze** ribbon.</span></span>  
  
###  <a name="chart"></a><a name="bkmk_charts"></a><span data-ttu-id="261d1-110">グラフ</span><span class="sxs-lookup"><span data-stu-id="261d1-110">Chart</span></span>  
 <span data-ttu-id="261d1-111">[**グラフ**] タブには、データ系列の傾向が予測値と共に時系列で表示されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-111">The **Chart** tab displays the trend in your data series over time, together with the predicted values.</span></span> <span data-ttu-id="261d1-112">グラフの縦軸は時系列の値を表し、横軸は時間を表します。</span><span class="sxs-lookup"><span data-stu-id="261d1-112">The vertical axis of the chart represents the values of the series, and the horizontal axis represents time.</span></span>  
  
##### <a name="explore-the-forecasting-chart"></a><span data-ttu-id="261d1-113">予測チャートの調査</span><span class="sxs-lookup"><span data-stu-id="261d1-113">Explore the forecasting chart</span></span>  
  
1.  <span data-ttu-id="261d1-114">このモデルには複数の時系列が含まれていますが、グラフを見やすくするために、時系列を 1 つだけ表示することも、数個の関連系列だけを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="261d1-114">This model contains multiple time series, but to simplify the chart, you can display a single series, or just a few related series.</span></span>  
  
     <span data-ttu-id="261d1-115">![予測モデルの履歴予測](media/dm13-forecast-chart-historicpredictions.gif "予測モデルの履歴予測")</span><span class="sxs-lookup"><span data-stu-id="261d1-115">![historical predictions in the forecasting model](media/dm13-forecast-chart-historicpredictions.gif "historical predictions in the forecasting model")</span></span>  
  
     <span data-ttu-id="261d1-116">チェック ボックスを使用して、北米のみと売上高のみの予測を選択します。</span><span class="sxs-lookup"><span data-stu-id="261d1-116">Use the check boxes to select the forecast for just North America, and just for sales Amount.</span></span>  
  
2.  <span data-ttu-id="261d1-117">[**予測ステップ**] をクリックし、新しい値を入力して、グラフに表示する将来の時刻の値の数を制御します。</span><span class="sxs-lookup"><span data-stu-id="261d1-117">Click **Prediction Steps** and type a new value to control how many future time values you want to see in the chart.</span></span>  
  
     <span data-ttu-id="261d1-118">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="261d1-118">The default is 5.</span></span>  
  
3.  <span data-ttu-id="261d1-119">[履歴] または [未来] のいずれかの行の任意のポイントをクリックすると、その時点の正確な値が [**マイニング凡例**] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-119">Click any point in the line, either historical or future, to see the exact values for that point in time, displayed in the **Mining Legend**.</span></span>  
  
4.  <span data-ttu-id="261d1-120">グラフには、履歴データと将来のデータの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-120">The chart displays both historical and future data.</span></span> <span data-ttu-id="261d1-121">背景に影の付いた点線に注目します。</span><span class="sxs-lookup"><span data-stu-id="261d1-121">Note the dotted line, with a shaded background.</span></span> <span data-ttu-id="261d1-122">これらの値は、モデルに基づいた将来の予測です。</span><span class="sxs-lookup"><span data-stu-id="261d1-122">These values are the future predictions, based on the model.</span></span>  
  
     <span data-ttu-id="261d1-123">(モデルの作成に使用した) 履歴データがグラフの左側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-123">The historical data (which you used to build the model) is shown in the left side of the chart.</span></span>  
  
5.  <span data-ttu-id="261d1-124">時系列の安定性を把握するには、[**履歴予測を表示**する] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="261d1-124">Select the **Show historic predictions** option to get a sense for the stability of the time series.</span></span>  
  
     <span data-ttu-id="261d1-125">![モデル内の 1 つの系列の予測](media/dm13-forecast-chart-singleseries.gif "モデル内の 1 つの系列の予測")</span><span class="sxs-lookup"><span data-stu-id="261d1-125">![forecasts for a single series in the model](media/dm13-forecast-chart-singleseries.gif "forecasts for a single series in the model")</span></span>  
  
     <span data-ttu-id="261d1-126">履歴予測は、実際の履歴値と比較される、その時点への系列に基づいて予測された値です。</span><span class="sxs-lookup"><span data-stu-id="261d1-126">Historical predictions are values predicted based on the series to that point, which are compared to actual historical values.</span></span> <span data-ttu-id="261d1-127">点線 (予測値) が実線 (実際の値) から大きくかけ離れている場合は、系列の最初の部分で後に続く値が正確に予測されていないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="261d1-127">If the dotted line (with the predicted values) is far apart from the solid line (the actual values), it means the first part of the series perhaps does not accurately predict the later values.</span></span> <span data-ttu-id="261d1-128">さらに多くのデータが必要になるか、サイクルの変動率を示すだけになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="261d1-128">You might need more data, or it might simply be an indicator of volatility in the cycle.</span></span>  
  
6.  <span data-ttu-id="261d1-129">グラフに誤差の棒を表示するには、[**偏差の表示**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="261d1-129">Select the **Show Deviations** option to display error bars in the chart.</span></span>  
  
     <span data-ttu-id="261d1-130">誤差範囲により、予測のばらつきを視覚的に評価できます。</span><span class="sxs-lookup"><span data-stu-id="261d1-130">The error bars let you visually assess the variability of the predictions.</span></span> <span data-ttu-id="261d1-131">予測の品質は、ソース データによって異なりますが、予測期間の数が増えるにつれて、偏差が徐々に大きくなることがわかります。</span><span class="sxs-lookup"><span data-stu-id="261d1-131">The quality of predictions varies depending on your source data, but as you increase the number of prediction steps, you should see the deviations steadily increase.</span></span>  
  
 <span data-ttu-id="261d1-132">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="261d1-132">**Tips**</span></span>  
  
-   <span data-ttu-id="261d1-133">[**マイニング凡例**] の表示を切り替えるには、グラフ内の任意のポイントを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="261d1-133">To toggle display of the **Mining Legend**, right-click any point in the chart.</span></span>  
  
     <span data-ttu-id="261d1-134">特定の時間範囲を表示するには、グラフをクリックし、グラフ上で時間の選択をドラッグし、再びクリックして選択した範囲を拡大します。</span><span class="sxs-lookup"><span data-stu-id="261d1-134">You can view a specific time range by clicking the chart, dragging a time selection across the chart, and then clicking again to zoom in on the selected range.</span></span>  
  
-   <span data-ttu-id="261d1-135">現在のグラフのコピーを取得するには、[ **excel にコピー**] をクリックし、excel のワークシートをクリックします。</span><span class="sxs-lookup"><span data-stu-id="261d1-135">To get a copy of the current chart, click **Copy to Excel**, then click a worksheet in Excel.</span></span> <span data-ttu-id="261d1-136">設定したすべてのオプション (凡例など) を使用して、シートにグラフィックが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-136">A graphic is inserted in the sheet using all the options you had set, including a legend.</span></span>  
  
     <span data-ttu-id="261d1-137">ただし、このグラフィックは静的なので、凡例を編集したり、基になるデータを表示したりすることはできません。より対話的なグラフビューが必要な場合は、 [Visio ビューアー](viewing-data-mining-models-in-visio-data-mining-add-ins.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="261d1-137">However, this graphic is static so you cannot edit the legend or view the underlying data; if you need a more interactive chart view, use the [Visio viewers](viewing-data-mining-models-in-visio-data-mining-add-ins.md).</span></span>  
  
-   <span data-ttu-id="261d1-138">絶対曲線と相対曲線を切り替えるには、ビューアーのメニューバーで [ **Abs** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="261d1-138">Click **Abs** in the viewer menu bar to toggle between absolute and relative curves.</span></span>  
  
     <span data-ttu-id="261d1-139">このオプションは、グラフに複数のモデルが含まれている場合に役立ちますが、各モデルのデータのスケールが大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="261d1-139">This option is useful if your chart contains multiple models, but the scale of the data for each model is very different.</span></span>  
  
     <span data-ttu-id="261d1-140">たとえば、太平洋地域の店舗が新規オープンして売上が低かった場合や、絶対値が使用されている場合、他のモデルはより標準的なスケールで表示されますが、大西洋地域の売上を示す線は平坦になり、実際の変化がわかりにくくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="261d1-140">For example, if the Pacific region stores were new and sales were low, and if absolute values are used, the line showing Pacific sales might appear flat, making it difficult to see actual changes, whereas the other models would be displayed at a more normal scale.</span></span>  
  
     <span data-ttu-id="261d1-141">相対値を使用するようにビューを切り替えると、異なるモデルのスケールを正規化し、違いを変化の割合として表示できます。</span><span class="sxs-lookup"><span data-stu-id="261d1-141">By switching the view to use relative values, you can normalize the scale of different models, and display differences as a percent of change.</span></span> <span data-ttu-id="261d1-142">変化が各モデルに対して相対的である場合、これらのモデルを大きな歪みがない状態で同じグラフに表示できます。</span><span class="sxs-lookup"><span data-stu-id="261d1-142">When change is relative to each model, they can be displayed in the same graph without significant distortion.</span></span>  
  
 [<span data-ttu-id="261d1-143">モデルの調査</span><span class="sxs-lookup"><span data-stu-id="261d1-143">Explore the Model</span></span>](#bkmk_Top)  
  
###  <a name="model"></a><a name="bkmk_Model"></a><span data-ttu-id="261d1-144">型</span><span class="sxs-lookup"><span data-stu-id="261d1-144">Model</span></span>  
 <span data-ttu-id="261d1-145">予測モデルはデシジョン ツリーとして表すこともできます。また、系列がほぼ直線状の場合は、回帰モデルとして表すことができます。</span><span class="sxs-lookup"><span data-stu-id="261d1-145">A forecasting model can also be represented as a decision tree, or, if the series is mostly linear, a regression model.</span></span>  
  
 <span data-ttu-id="261d1-146">たとえば、このモデルでは、特定の条件に基づく回帰式に違いがあるため、ツリーは、それぞれ回帰式が異なる 2 つの分岐に分かれます。</span><span class="sxs-lookup"><span data-stu-id="261d1-146">For example, in this model, there is a difference in the regression formula based on a certain condition, so the tree splits into two branches, each with a different regression formula.</span></span>  
  
 <span data-ttu-id="261d1-147">![予測モデル内の 1 つの系列をフィルター処理](media/dm13-forecast-model-northamerica.gif "予測モデル内の 1 つの系列をフィルター処理")</span><span class="sxs-lookup"><span data-stu-id="261d1-147">![Filter single series in the forecasting model](media/dm13-forecast-model-northamerica.gif "Filter single series in the forecasting model")</span></span>  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a><span data-ttu-id="261d1-148">予測モデルのツリーとしての調査</span><span class="sxs-lookup"><span data-stu-id="261d1-148">Explore the forecasting model as a tree</span></span>  
  
1.  <span data-ttu-id="261d1-149">[**ツリー** ] ボックスの一覧をクリックし、表示するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="261d1-149">Click the **Tree** dropdown list and choose a model to display.</span></span>  
  
     <span data-ttu-id="261d1-150">予測可能な属性ごとに個別のツリーまたは回帰ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-150">A separate tree or regression node is displayed for each predictable attribute.</span></span> <span data-ttu-id="261d1-151">たとえば、データにヨーロッパ、北米、および太平洋の売上が含まれている場合は、3 つの異なるモデル (データ系列ごとに 1 つ) が存在します。</span><span class="sxs-lookup"><span data-stu-id="261d1-151">For example, if your data contains sales for Europe, North America, and the Pacific, there would three different models, one for each data series.</span></span>  
  
2.  <span data-ttu-id="261d1-152">[**レベルの表示]** スライダーをドラッグしてツリーの下位レベルを除外し、最も重要な分割に焦点を当てます。</span><span class="sxs-lookup"><span data-stu-id="261d1-152">Drag the **Show Level** slider to filter out lower levels of the tree, and focus on the most important splits.</span></span>  
  
3.  <span data-ttu-id="261d1-153">各ノードをクリックすると、[**マイニング凡例**] に説明的な統計情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-153">Click each node to view some descriptive statistics in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="261d1-154">ノードの上にマウス ポインターを置くと、ツールヒントにも、同様の統計情報に加えて、そのノードを説明する完全な式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="261d1-154">As you pause over a node with the mouse, a ToolTip also displays the same statistics, as well as the full formula describing that node.</span></span>  
  
4.  <span data-ttu-id="261d1-155">[**マイニング凡例**] の情報をコピーする場合は、[**マイニング凡例**] を右クリックし、[**コピー**] を選択して、Excel ワークシート内をクリックします。</span><span class="sxs-lookup"><span data-stu-id="261d1-155">If you want to copy the information in the **Mining Legend**, right-click the **Mining Legend**, select **Copy**, and click inside your Excel worksheet.</span></span> <span data-ttu-id="261d1-156">[ **Excel にコピー** ] オプションを選択すると、統計情報ではなくグラフがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="261d1-156">The **Copy to Excel** option copies the graph, not the statistics.</span></span>  
  
 [<span data-ttu-id="261d1-157">モデルの調査</span><span class="sxs-lookup"><span data-stu-id="261d1-157">Explore the Model</span></span>](#bkmk_Top)  
  
## <a name="see-also"></a><span data-ttu-id="261d1-158">参照</span><span class="sxs-lookup"><span data-stu-id="261d1-158">See Also</span></span>  
 [<span data-ttu-id="261d1-159">Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;</span><span class="sxs-lookup"><span data-stu-id="261d1-159">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
