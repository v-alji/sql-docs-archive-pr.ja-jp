---
title: 'レッスン 4: DMX を使用した時系列予測の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 772e5f5f71ca82dd18fec48730522c80e907414f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711177"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a><span data-ttu-id="daba9-102">レッスン 4: DMX を使用した時系列予測の作成</span><span class="sxs-lookup"><span data-stu-id="daba9-102">Lesson 4: Creating Time Series Predictions Using DMX</span></span>
  <span data-ttu-id="daba9-103">このレッスンと次のレッスンでは、データマイニング拡張機能 (DMX) を使用して、 [「レッスン 1: 時系列マイニングモデルとマイニング構造の作成](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)」で作成したタイムシリーズモデルに基づいてさまざまな種類の予測を作成し、「[レッスン 2: 時系列マイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="daba9-103">In this lesson and the following lesson, you will use Data Mining Extensions (DMX) to create different types of predictions based on the time series models that you created in [Lesson 1: Creating a Time Series Mining Model and Mining Structure](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md) and [Lesson 2: Adding Mining Models to the Time Series Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md).</span></span>  
  
 <span data-ttu-id="daba9-104">時系列モデルでは、さまざまな方法で予測を作成できます。</span><span class="sxs-lookup"><span data-stu-id="daba9-104">With a time series model, you have many options for making predictions:</span></span>  
  
-   <span data-ttu-id="daba9-105">マイニング モデル内の既存のパターンとデータを使用する。</span><span class="sxs-lookup"><span data-stu-id="daba9-105">Use the existing patterns and data in the mining model</span></span>  
  
-   <span data-ttu-id="daba9-106">マイニング モデル内の既存のパターンを使用し、データは新たに供給する。</span><span class="sxs-lookup"><span data-stu-id="daba9-106">Use the existing patterns in the mining model but supply new data</span></span>  
  
-   <span data-ttu-id="daba9-107">モデルに新しいデータを追加するか、モデルを更新する。</span><span class="sxs-lookup"><span data-stu-id="daba9-107">Add new data to the model or update the model.</span></span>  
  
 <span data-ttu-id="daba9-108">このような予測を作成するための構文を以下にまとめます。</span><span class="sxs-lookup"><span data-stu-id="daba9-108">The syntax for making these prediction types is summarized below:</span></span>  
  
 <span data-ttu-id="daba9-109">既定の時系列予測</span><span class="sxs-lookup"><span data-stu-id="daba9-109">Default time series prediction</span></span>  
 <span data-ttu-id="daba9-110">[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)を使用して、トレーニング済みのマイニングモデルから指定された数の予測を返します。</span><span class="sxs-lookup"><span data-stu-id="daba9-110">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) to return the specified number of predictions from the trained mining model.</span></span>  
  
 <span data-ttu-id="daba9-111">例については、「 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)または[タイムシリーズモデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="daba9-111">For example, see [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) or [Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="daba9-112">EXTEND_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="daba9-112">EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="daba9-113">新しいデータの追加、系列の拡張、および更新されたマイニングモデルに基づく予測の作成を行うには、 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)を EXTEND_MODEL_CASES 引数と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="daba9-113">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) with the EXTEND_MODEL_CASES argument to add new data, extend the series, and create predictions based on the updated mining model.</span></span>  
  
 <span data-ttu-id="daba9-114">このチュートリアルには、EXTEND_MODEL_CASES の使用例が示されています。</span><span class="sxs-lookup"><span data-stu-id="daba9-114">This tutorial contains an example of how to use EXTEND_MODEL_CASES.</span></span>  
  
 <span data-ttu-id="daba9-115">REPLACE_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="daba9-115">REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="daba9-116">[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)を REPLACE_MODEL_CASES 引数と共に使用して元のデータを新しいデータ系列に置き換え、マイニングモデルのパターンを新しいデータ系列に適用することに基づいて予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="daba9-116">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) with the REPLACE_MODEL_CASES argument to replace the original data with a new data series, and then create predictions based on applying the patterns in the mining model to the new data series.</span></span>  
  
 <span data-ttu-id="daba9-117">REPLACE_MODEL_CASES の使用方法の例については、「[レッスン 2: 予測シナリオの作成 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="daba9-117">For an example of how to use REPLACE_MODEL_CASES, see [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="daba9-118">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="daba9-118">Lesson Tasks</span></span>  
 <span data-ttu-id="daba9-119">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="daba9-119">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="daba9-120">既存のデータに基づいて既定の予測を取得するクエリの作成</span><span class="sxs-lookup"><span data-stu-id="daba9-120">Create a query to get the default predictions based on existing data.</span></span>  
  
 <span data-ttu-id="daba9-121">この次のレッスンでは、関連する次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="daba9-121">In the following lesson you will perform the following related tasks:</span></span>  
  
-   <span data-ttu-id="daba9-122">新しいデータを提供して更新された予測を取得するクエリの作成</span><span class="sxs-lookup"><span data-stu-id="daba9-122">Create a query to supply new data and get updated predictions.</span></span>  
  
 <span data-ttu-id="daba9-123">DMX を使用して手動でクエリを作成する以外に、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で予測クエリ ビルダーを使用して予測を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="daba9-123">In addition to creating queries manually by using DMX, you can also create predictions by using the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="simple-time-series-prediction-query"></a><span data-ttu-id="daba9-124">簡単な時系列予測クエリ</span><span class="sxs-lookup"><span data-stu-id="daba9-124">Simple Time Series Prediction Query</span></span>  
 <span data-ttu-id="daba9-125">最初の手順では、`SELECT FROM` ステートメントを `PredictTimeSeries` 関数と共に使用して時系列予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="daba9-125">The first step is to use the `SELECT FROM` statement together with the `PredictTimeSeries` function to create time series predictions.</span></span> <span data-ttu-id="daba9-126">時系列モデルでは、予測を作成するための簡略化された構文がサポートされます。入力データを提供する必要ありませんが、作成する予測の数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="daba9-126">Time series models support a simplified syntax for creating predictions: you do not need to supply any inputs, but only have to specify the number of predictions to create.</span></span> <span data-ttu-id="daba9-127">使用するステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="daba9-127">The following is a generic example of the statement you will use:</span></span>  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 <span data-ttu-id="daba9-128">選択リストには、モデルの列を含めることができます。たとえば、予測を作成している製品ラインの名前や、タイムシリーズマイニングモデルに特化した[&#40;dmx&#41;](/sql/dmx/lag-dmx)や[PredictTimeSeries &#40;dmx&#41;](/sql/dmx/predicttimeseries-dmx)などの予測関数などです。</span><span class="sxs-lookup"><span data-stu-id="daba9-128">The select list can contain columns from the model, such as the name of the product line that you are creating the predictions for, or prediction functions, such as [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) or [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx), which are specifically for time series mining models.</span></span>  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a><span data-ttu-id="daba9-129">簡単な時系列予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="daba9-129">To create a simple time series prediction query</span></span>  
  
1.  <span data-ttu-id="daba9-130">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="daba9-130">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="daba9-131">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="daba9-131">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="daba9-132">ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="daba9-132">Copy the generic example of the statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="daba9-133">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="daba9-133">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="daba9-134">with:</span><span class="sxs-lookup"><span data-stu-id="daba9-134">with:</span></span>  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     <span data-ttu-id="daba9-135">最初の行では、系列を識別する値をマイニング モデルから取得します。</span><span class="sxs-lookup"><span data-stu-id="daba9-135">The first line retrieves a value from the mining model that identifies the series.</span></span>  
  
     <span data-ttu-id="daba9-136">2 行目と 3 行目では、`PredictTimeSeries` 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="daba9-136">The second and third lines use the `PredictTimeSeries` function.</span></span> <span data-ttu-id="daba9-137">各行で別々の属性 (`[Quantity]` または `[Amount]`) が予測されます。</span><span class="sxs-lookup"><span data-stu-id="daba9-137">Each line predicts a different attribute, `[Quantity]` or `[Amount]`.</span></span> <span data-ttu-id="daba9-138">予測可能な属性の名前の後の数値は、予測する時間ステップの数を示します。</span><span class="sxs-lookup"><span data-stu-id="daba9-138">The numbers after the names of the predictable attributes specify the number of time steps to predict.</span></span>  
  
     <span data-ttu-id="daba9-139">`AS` 句は、各予測関数から返される列の名前を指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="daba9-139">The `AS` clause is used to provide a name for the column that is returned by each prediction function.</span></span> <span data-ttu-id="daba9-140">別名を指定しない場合は、既定で両方の列が `Expression` というラベルで返されます。</span><span class="sxs-lookup"><span data-stu-id="daba9-140">If you do not supply an alias, by default both columns are returned with the label, `Expression`.</span></span>  
  
4.  <span data-ttu-id="daba9-141">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="daba9-141">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="daba9-142">with:</span><span class="sxs-lookup"><span data-stu-id="daba9-142">with:</span></span>  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  <span data-ttu-id="daba9-143">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="daba9-143">Replace the following:</span></span>  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     <span data-ttu-id="daba9-144">with:</span><span class="sxs-lookup"><span data-stu-id="daba9-144">with:</span></span>  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     <span data-ttu-id="daba9-145">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="daba9-145">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  <span data-ttu-id="daba9-146">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="daba9-146">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="daba9-147">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `SimpleTimeSeriesPrediction.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="daba9-147">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SimpleTimeSeriesPrediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="daba9-148">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="daba9-148">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="daba9-149">クエリから、`WHERE` 句で指定した製品と地域の 2 とおりの組み合わせごとに 6 つの予測が返されます。</span><span class="sxs-lookup"><span data-stu-id="daba9-149">The query returns 6 predictions for each of the two combinations of product and region that are specified in the `WHERE` clause.</span></span>  
  
 <span data-ttu-id="daba9-150">次のレッスンでは、モデルに新しいデータを提供するクエリを作成し、その予測結果をここで作成した予測と比較します。</span><span class="sxs-lookup"><span data-stu-id="daba9-150">In the next lesson, you will create a query that supplies new data to the model, and compare the results of that prediction with the one you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="daba9-151">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="daba9-151">Next Task in Lesson</span></span>  
 [<span data-ttu-id="daba9-152">レッスン 5 : 時系列モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="daba9-152">Lesson 5: Extending the Time Series Model</span></span>](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="daba9-153">参照</span><span class="sxs-lookup"><span data-stu-id="daba9-153">See Also</span></span>  
 <span data-ttu-id="daba9-154">[DMX&#41;&#40;PredictTimeSeries](/sql/dmx/predicttimeseries-dmx) </span><span class="sxs-lookup"><span data-stu-id="daba9-154">[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) </span></span>  
 <span data-ttu-id="daba9-155">[DMX&#41;&#40;Lag](/sql/dmx/lag-dmx) </span><span class="sxs-lookup"><span data-stu-id="daba9-155">[Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) </span></span>  
 <span data-ttu-id="daba9-156">[タイムシリーズモデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="daba9-156">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="daba9-157">レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="daba9-157">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
