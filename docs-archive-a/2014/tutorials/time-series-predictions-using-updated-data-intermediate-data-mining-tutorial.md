---
title: 更新されたデータを使用した時系列予測 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2017defaba74071b1a12bee14a5d8907e4c71cda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631382"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a><span data-ttu-id="3162f-102">時系列予測での更新後のデータの使用 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="3162f-102">Time Series Predictions using Updated Data (Intermediate Data Mining Tutorial)</span></span>
    
## <a name="creating-predictions-using-the-extended-sales-data"></a><span data-ttu-id="3162f-103">拡張売上データを使用した予測の作成</span><span class="sxs-lookup"><span data-stu-id="3162f-103">Creating Predictions using the Extended Sales Data</span></span>  
 <span data-ttu-id="3162f-104">このレッスンでは、モデルに新しい売上データを追加する予測クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3162f-104">In this lesson, you will create a prediction query that adds the new sales data to the model.</span></span> <span data-ttu-id="3162f-105">新しいデータでモデルを拡張することにより、最新のデータ ポイントを含む現時点での予測を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3162f-105">By extending the model with new data, you can get up-to-date predictions that include the newest data points.</span></span>  
  
 <span data-ttu-id="3162f-106">新しいデータを使用する時系列予測を作成するのは簡単です。 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)関数にパラメーター EXTEND_MODEL_CASES を追加し、新しいデータのソースを指定して、取得する予測の数を指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="3162f-106">Creating time series predictions that use new data is easy: you simply add the parameter EXTEND_MODEL_CASES to the [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) function, specify the source of the new data, and specify how many predictions you want to get.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="3162f-107">パラメーター EXTEND_MODEL_CASES は省略可能です。既定では、入力として新しいデータを結合して時系列予測クエリを作成するたびに、モデルが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="3162f-107">The parameter EXTEND_MODEL_CASES is optional; by default the model is extended any time that you create a time series prediction query by joining new data as inputs.</span></span>  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a><span data-ttu-id="3162f-108">予測クエリを作成して新しいデータを追加するには</span><span class="sxs-lookup"><span data-stu-id="3162f-108">To build the prediction query and add new data</span></span>  
  
1.  <span data-ttu-id="3162f-109">モデルがまだ開いていない場合は、予測構造をダブルクリックし、データマイニングデザイナーで [**マイニングモデル予測**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3162f-109">If the model is not already open, double-click the Forecasting structure, and in Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="3162f-110">[**マイニングモデル**] ペインで、モデルの予測を選択しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="3162f-110">In the **Mining Model** pane, the model Forecasting should already be selected.</span></span> <span data-ttu-id="3162f-111">選択されていない場合は、[**モデルの選択**] をクリックし、モデルの予測を選択します。</span><span class="sxs-lookup"><span data-stu-id="3162f-111">If it is not selected, click **Select Model**, and then select the model, Forecasting.</span></span>  
  
3.  <span data-ttu-id="3162f-112">[**入力テーブルの選択**] ペインで、[**ケーステーブルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3162f-112">In the **Select Input Table(s)** pane, click **Select Case Table**.</span></span>  
  
4.  <span data-ttu-id="3162f-113">**[テーブルの選択**] ダイアログボックスで、データソースを選択し [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3162f-113">In the **Select Table** dialog box, select the data source, [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span>  
  
     <span data-ttu-id="3162f-114">データソースビューの一覧から [NewSalesData] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3162f-114">From the list of data source views, select NewSalesData and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="3162f-115">デザイン領域の画面を右クリックし、[**接続の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3162f-115">Right-click the surface of the design area and select **Modify Connections**.</span></span>  
  
6.  <span data-ttu-id="3162f-116">[**マッピングの変更**] ダイアログボックスを使用して、次のように、モデル内の列を外部データの列にマップします。</span><span class="sxs-lookup"><span data-stu-id="3162f-116">Using the **Modify Mapping** dialog box, map the columns in the model to the columns in the external data as follows:</span></span>  
  
    -   <span data-ttu-id="3162f-117">マイニングモデルの ReportingDate 列を入力データの NewDate 列にマップします。</span><span class="sxs-lookup"><span data-stu-id="3162f-117">Map the ReportingDate column in the mining model to the NewDate column in the input data.</span></span>  
  
    -   <span data-ttu-id="3162f-118">マイニングモデルの Amount 列を入力データの NewAmount 列にマップします。</span><span class="sxs-lookup"><span data-stu-id="3162f-118">Map the Amount column in the mining model to the NewAmount column in the input data.</span></span>  
  
    -   <span data-ttu-id="3162f-119">マイニングモデルの Quantity 列を入力データの NewQty 列にマップします。</span><span class="sxs-lookup"><span data-stu-id="3162f-119">Map the Quantity column in the mining model to the NewQty column in the input data.</span></span>  
  
    -   <span data-ttu-id="3162f-120">マイニングモデルの ModelRegion 列を入力データの系列列にマップします。</span><span class="sxs-lookup"><span data-stu-id="3162f-120">Map the ModelRegion column in the mining model to the Series column in the input data.</span></span>  
  
7.  <span data-ttu-id="3162f-121">ここで、予測クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3162f-121">Now you will build the prediction query.</span></span>  
  
     <span data-ttu-id="3162f-122">最初に、列を予測クエリに追加し、予測を適用する系列を出力します。</span><span class="sxs-lookup"><span data-stu-id="3162f-122">First, add a column to the prediction query to output the series the prediction applies to.</span></span>  
  
    1.  <span data-ttu-id="3162f-123">グリッドで、[**ソース**] の下の最初の空の行をクリックし、[予測] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3162f-123">In the grid, click the first empty row, under **Source**, and then select Forecasting.</span></span>  
  
    2.  <span data-ttu-id="3162f-124">[**フィールド**] 列で [モデル領域] を選択し、[**別名**] に「」と入力 `Model Region` します。</span><span class="sxs-lookup"><span data-stu-id="3162f-124">In the **Field** column, select Model Region and for **Alias**, type `Model Region`.</span></span>  
  
8.  <span data-ttu-id="3162f-125">次に、予測関数を追加して編集します。</span><span class="sxs-lookup"><span data-stu-id="3162f-125">Next, add and edit the prediction function.</span></span>  
  
    1.  <span data-ttu-id="3162f-126">空の行をクリックし、[**ソース**] で [**予測関数**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3162f-126">Click an empty row, and under **Source**, select **Prediction Function**.</span></span>  
  
    2.  <span data-ttu-id="3162f-127">[**フィールド**] で [ **PredictTimeSeries**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3162f-127">For **Field**, select **PredictTimeSeries**.</span></span>  
  
    3.  <span data-ttu-id="3162f-128">[**別名**] に「予測される**値**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3162f-128">For **Alias**, type **Predicted Values**.</span></span>  
  
    4.  <span data-ttu-id="3162f-129">[**マイニングモデル**] ペインの [Quantity] フィールドを [**条件と引数**] 列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3162f-129">Drag the field Quantity from the **Mining Model** pane into the **Criteria/Argument** column.</span></span>  
  
    5.  <span data-ttu-id="3162f-130">[**条件と引数**] 列で、フィールド名の後に次のテキストを入力します: **5, EXTEND_MODEL_CASES**</span><span class="sxs-lookup"><span data-stu-id="3162f-130">In the **Criteria/Argument** column, after the field name, type the following text:  **5,EXTEND_MODEL_CASES**</span></span>  
  
         <span data-ttu-id="3162f-131">[**条件と引数**] テキストボックスの完全なテキストは次のようになります。`[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`</span><span class="sxs-lookup"><span data-stu-id="3162f-131">The complete text of the **Criteria/Argument** text box should be as follows: `[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`</span></span>  
  
9. <span data-ttu-id="3162f-132">[**結果**] をクリックし、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="3162f-132">Click **Results** and review the results.</span></span>  
  
     <span data-ttu-id="3162f-133">予測は 7 月 (元のデータが終了した後の最初のタイム スライス) から開始し、11 月 (元のデータが終了した後の 5 番目のタイム スライス) で終了しています。</span><span class="sxs-lookup"><span data-stu-id="3162f-133">The predictions begin in July (the first time slice after the end of the original data) and end at November (the fifth time slice after the end of the original data).</span></span>  
  
 <span data-ttu-id="3162f-134">この種の予測クエリを効率よく使用するには、古いデータがいつ終了し、新しいデータにタイム スライスがいくつあるかを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="3162f-134">You can see that to use this type of prediction query effectively, you need to know when the old data ends, as well as how many time slices there are in the new data.</span></span>  
  
 <span data-ttu-id="3162f-135">たとえば、このモデルでは、元のデータ系列は 6 月に終了し、データは 7 月、8 月、9 月のものになります。</span><span class="sxs-lookup"><span data-stu-id="3162f-135">For example, in this model, the original data series ended in June, and the data is for the months of July, August, and September.</span></span>  
  
 <span data-ttu-id="3162f-136">EXTEND_MODEL_CASES を使用する予測は常に、元のデータ系列の終了から開始します。</span><span class="sxs-lookup"><span data-stu-id="3162f-136">Predictions that use EXTEND_MODEL_CASES always begin at the end of the original data series.</span></span> <span data-ttu-id="3162f-137">そのため、不明の月の予測のみを取得するには、予測の開始位置と終了位置を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3162f-137">Therefore, if you want to get only the predictions for the unknown months, you need to specify the starting point and the end point for prediction.</span></span> <span data-ttu-id="3162f-138">どちらの値も、古いデータの終わりから始まるタイム スライスの数として指定されます。</span><span class="sxs-lookup"><span data-stu-id="3162f-138">Both values are specified as a number of time slices starting at the end of the old data.</span></span>  
  
 <span data-ttu-id="3162f-139">次の手順は、これを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3162f-139">The following procedure demonstrates how to do this.</span></span>  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a><span data-ttu-id="3162f-140">予測の開始位置と終了位置を変更します。</span><span class="sxs-lookup"><span data-stu-id="3162f-140">Change the start and end points of the predictions</span></span>  
  
1.  <span data-ttu-id="3162f-141">[予測クエリビルダーで、[**クエリ**] をクリックして DMX ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="3162f-141">In Prediction Query Builder, click **Query** to switch to DMX view.</span></span>  
  
2.  <span data-ttu-id="3162f-142">PredictTimeSeries 関数が含まれている DMX ステートメントを見つけて、次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="3162f-142">Locate the DMX statement that contains the PredictTimeSeries function and change it as follows:</span></span>  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  <span data-ttu-id="3162f-143">[**結果**] をクリックし、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="3162f-143">Click **Results** and review the results.</span></span>  
  
     <span data-ttu-id="3162f-144">予測が 10 月 (元のデータが終了してから 4 番目のタイム スライス) から開始し、12 月 (元のデータが終了してから 6 番目のタイム スライス) で終了するようになります。</span><span class="sxs-lookup"><span data-stu-id="3162f-144">Now the predictions begin at October (the fourth time slice, counting from the end of the original data) and end at December (the sixth time slice, counting from the end of the original data).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3162f-145">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="3162f-145">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3162f-146">交換データ &#40;中間データマイニングチュートリアル&#41;を使用した時系列予測</span><span class="sxs-lookup"><span data-stu-id="3162f-146">Time Series Predictions using Replacement Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="3162f-147">参照</span><span class="sxs-lookup"><span data-stu-id="3162f-147">See Also</span></span>  
 <span data-ttu-id="3162f-148">[Microsoft タイムシリーズアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3162f-148">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="3162f-149">タイム シリーズ モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="3162f-149">Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
