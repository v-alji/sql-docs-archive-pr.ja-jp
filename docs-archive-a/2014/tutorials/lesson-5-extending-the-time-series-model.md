---
title: 'レッスン 5: タイムシリーズモデルの拡張 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7aad4946-c903-4e25-88b9-b087c20cb67d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2716e985897f8115d189d9410b7cdb13fb1af291
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634176"
---
# <a name="lesson-5-extending-the-time-series-model"></a><span data-ttu-id="2cd20-102">レッスン 5 : 時系列モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="2cd20-102">Lesson 5: Extending the Time Series Model</span></span>
  <span data-ttu-id="2cd20-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise Edition では、時系列モデルに新しいデータを追加し、モデルに新しいデータを自動的に組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-103">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise, you can add new data to a time series model and automatically incorporate the new data into the model.</span></span> <span data-ttu-id="2cd20-104">次の 2 つの方法のいずれかで、時系列マイニング モデルに新しいデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-104">You add new data to a time series mining model in one of two ways:</span></span>  
  
-   <span data-ttu-id="2cd20-105">PREDICTION JOIN を使用してトレーニング データに外部ソースのデータを結合します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-105">Use a PREDICTION JOIN to join data in an external source to the training data.</span></span>  
  
-   <span data-ttu-id="2cd20-106">単一予測クエリを使用してデータにスライスを 1 つずつ指定します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-106">Use a singleton prediction query to provide data one slice at a time.</span></span>  
  
 <span data-ttu-id="2cd20-107">たとえば、数か月前に既存の売上データでマイニング モデルをトレーニングしたとします。</span><span class="sxs-lookup"><span data-stu-id="2cd20-107">For example, assume that you trained the mining model on existing sales data some months ago.</span></span> <span data-ttu-id="2cd20-108">新たな売上があったときに、新しいデータを組み込んで売上予測を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cd20-108">When you get new sales, you might want to update the sales predictions to incorporate the new data.</span></span> <span data-ttu-id="2cd20-109">この処理は 1 回の操作で実行できます。具体的には、新しい売上数値を入力データとして指定し、複合データセットに基づいて新しい予測を生成します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-109">You can do this in one step, by supplying the new sales figures as input data and generating new predictions based on the composite data set.</span></span>  
  
## <a name="making-predictions-with-extend_model_cases"></a><span data-ttu-id="2cd20-110">EXTEND_MODEL_CASES を使用した予測の作成</span><span class="sxs-lookup"><span data-stu-id="2cd20-110">Making Predictions with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="2cd20-111">次に示すのは、EXTEND_MODEL_CASES を使用する時系列予測の汎用例です。</span><span class="sxs-lookup"><span data-stu-id="2cd20-111">The following are generic examples of a time series prediction using EXTEND_MODEL_CASES.</span></span> <span data-ttu-id="2cd20-112">最初の例では、元のモデルの最後の時間ステップから始まる予測の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-112">The first example enables you to specify the number of predictions starting from the last time step of the original model:</span></span>  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>]  
```  
  
 <span data-ttu-id="2cd20-113">2 番目の例では、予測を開始する時間ステップと予測を終了する時間ステップを指定します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-113">The second example enables you to specify the time step where predictions should start, and where they should end.</span></span> <span data-ttu-id="2cd20-114">既定では、予測クエリに使用される時間ステップが常に元の系列の末尾から開始されるため、モデル ケースを拡張する場合はこのオプションが重要となります。</span><span class="sxs-lookup"><span data-stu-id="2cd20-114">This option is important when you extend the model cases because, by default, the time steps used for prediction queries always start at the end of the original series.</span></span>  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n-start, n-end, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>}  
```  
  
 <span data-ttu-id="2cd20-115">このチュートリアルでは、両方の種類のクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-115">In this tutorial, you will create both kinds of queries.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query-on-a-time-series-model"></a><span data-ttu-id="2cd20-116">時系列モデルに対する単一予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="2cd20-116">To create a singleton prediction query on a time series model</span></span>  
  
1.  <span data-ttu-id="2cd20-117">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cd20-117">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="2cd20-118">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-118">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="2cd20-119">上の単一ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="2cd20-119">Copy the generic example of the singleton statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="2cd20-120">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-120">Replace the following:</span></span>  
  
    ```  
    SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
    ```  
  
     <span data-ttu-id="2cd20-121">with:</span><span class="sxs-lookup"><span data-stu-id="2cd20-121">with:</span></span>  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    ```  
  
     <span data-ttu-id="2cd20-122">最初の行では、系列を識別する値がモデルから取得されます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-122">The first line retrieves a value from the model that identifies the series.</span></span>  
  
     <span data-ttu-id="2cd20-123">2 行目には、Quantity に関する 6 つの予測を取得する予測関数が示されています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-123">The second line contains the prediction function, which gets 6 predictions for Quantity.</span></span> <span data-ttu-id="2cd20-124">予測結果の列には、結果をわかりやすくするために `PredictQty` という別名が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-124">An alias, `PredictQty`, is assigned to the prediction result column to make it easier to understand the results.</span></span>  
  
4.  <span data-ttu-id="2cd20-125">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-125">Replace the following:</span></span>  
  
    ```  
    FROM <mining model>  
    ```  
  
     <span data-ttu-id="2cd20-126">with:</span><span class="sxs-lookup"><span data-stu-id="2cd20-126">with:</span></span>  
  
    ```  
    FROM [Forecasting_MIXED]  
    ```  
  
5.  <span data-ttu-id="2cd20-127">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-127">Replace the following:</span></span>  
  
    ```  
    PREDICTION JOIN <source query>  
    ```  
  
     <span data-ttu-id="2cd20-128">with:</span><span class="sxs-lookup"><span data-stu-id="2cd20-128">with:</span></span>  
  
    ```  
    NATURAL PREDICTION JOIN   
    (  
       SELECT 1 AS [Reporting Date],  
       '10' AS [Quantity],  
       'M200 Europe' AS [Model Region]  
       UNION SELECT  
       2 AS [Reporting Date],  
       15 AS [Quantity]),  
       'M200 Europe' AS [Model Region]  
    ) AS t  
    ```  
  
6.  <span data-ttu-id="2cd20-129">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-129">Replace the following:</span></span>  
  
    ```  
    [WHERE <criteria>]  
    ```  
  
     <span data-ttu-id="2cd20-130">with:</span><span class="sxs-lookup"><span data-stu-id="2cd20-130">with:</span></span>  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     <span data-ttu-id="2cd20-131">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2cd20-131">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    FROM  
       [Forecasting_MIXED]  
    NATURAL PREDICTION JOIN   
       SELECT 1 AS [ReportingDate],  
      '10' AS [Quantity],  
      'M200 Europe' AS [ModelRegion]  
    UNION SELECT  
      2 AS [ReportingDate],  
      15 AS [Quantity]),  
      'M200 Europe' AS [ModelRegion]  
    ) AS t  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
7.  <span data-ttu-id="2cd20-132">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cd20-132">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="2cd20-133">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Singleton_TimeSeries_Query.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-133">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Singleton_TimeSeries_Query.dmx`.</span></span>  
  
9. <span data-ttu-id="2cd20-134">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cd20-134">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="2cd20-135">クエリから、ヨーロッパ地域および太平洋地域での M200 自転車の販売数量の予測が返されます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-135">The query returns predictions of sales quantity for the M200 bicycle in the Europe and Pacific regions.</span></span>  
  
## <a name="understanding-prediction-start-with-extend_model_cases"></a><span data-ttu-id="2cd20-136">EXTEND_MODEL_CASES を使用した予測の開始について</span><span class="sxs-lookup"><span data-stu-id="2cd20-136">Understanding Prediction Start with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="2cd20-137">元のモデルを基に新しいデータで予測を作成しました。次に、結果を比較して、売上データの更新が予測に与える影響を確認します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-137">Now that you have created predictions based on the original model, and with new data, you can compare the results to see how updating the sales data affects the predictions.</span></span> <span data-ttu-id="2cd20-138">その前に、作成したコードを確認し、次の点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="2cd20-138">Before you do so, review the code that you just created, and notice the following:</span></span>  
  
-   <span data-ttu-id="2cd20-139">ヨーロッパ地域についてのみ新しいデータを指定しています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-139">You supplied new data for only the Europe region.</span></span>  
  
-   <span data-ttu-id="2cd20-140">新しいデータは 2 か月分のみ指定しています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-140">You supplied only two months' worth of new data.</span></span>  
  
 <span data-ttu-id="2cd20-141">"M200 Europe" に対して指定した新しい値が予測に与える影響を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-141">The following table shows how the new values supplied for M200 Europe affect predictions.</span></span> <span data-ttu-id="2cd20-142">太平洋地域の M200 製品には新しいデータを指定していませんが、比較のためにこの系列も示されています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-142">You did not provide any new data for the M200 product in the Pacific region, but this series is presented for comparison:</span></span>  
  
 <span data-ttu-id="2cd20-143">**製品と地域: M200 ヨーロッパ**</span><span class="sxs-lookup"><span data-stu-id="2cd20-143">**Product and Region: M200 Europe**</span></span>  
  
|||||  
|-|-|-|-|  
|||<span data-ttu-id="2cd20-144">既存のモデル (`PredictTimeSeries`)</span><span class="sxs-lookup"><span data-stu-id="2cd20-144">Existing model (`PredictTimeSeries`)</span></span>|<span data-ttu-id="2cd20-145">更新された売上データを使用するモデル (`PredictTimeSeries` が指定された `EXTEND_MODEL_CASES`)</span><span class="sxs-lookup"><span data-stu-id="2cd20-145">Model with updated sales data (`PredictTimeSeries` with `EXTEND_MODEL_CASES`)</span></span>|  
|<span data-ttu-id="2cd20-146">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-146">M200 Europe</span></span>|<span data-ttu-id="2cd20-147">7/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-147">7/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-148">77</span><span class="sxs-lookup"><span data-stu-id="2cd20-148">77</span></span>|<span data-ttu-id="2cd20-149">10</span><span class="sxs-lookup"><span data-stu-id="2cd20-149">10</span></span>|  
|<span data-ttu-id="2cd20-150">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-150">M200 Europe</span></span>|<span data-ttu-id="2cd20-151">8/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-151">8/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-152">64</span><span class="sxs-lookup"><span data-stu-id="2cd20-152">64</span></span>|<span data-ttu-id="2cd20-153">15</span><span class="sxs-lookup"><span data-stu-id="2cd20-153">15</span></span>|  
|<span data-ttu-id="2cd20-154">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-154">M200 Europe</span></span>|<span data-ttu-id="2cd20-155">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-155">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-156">59</span><span class="sxs-lookup"><span data-stu-id="2cd20-156">59</span></span>|<span data-ttu-id="2cd20-157">72</span><span class="sxs-lookup"><span data-stu-id="2cd20-157">72</span></span>|  
|<span data-ttu-id="2cd20-158">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-158">M200 Europe</span></span>|<span data-ttu-id="2cd20-159">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-159">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-160">56</span><span class="sxs-lookup"><span data-stu-id="2cd20-160">56</span></span>|<span data-ttu-id="2cd20-161">69</span><span class="sxs-lookup"><span data-stu-id="2cd20-161">69</span></span>|  
|<span data-ttu-id="2cd20-162">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-162">M200 Europe</span></span>|<span data-ttu-id="2cd20-163">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-163">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-164">56</span><span class="sxs-lookup"><span data-stu-id="2cd20-164">56</span></span>|<span data-ttu-id="2cd20-165">68</span><span class="sxs-lookup"><span data-stu-id="2cd20-165">68</span></span>|  
|<span data-ttu-id="2cd20-166">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-166">M200 Europe</span></span>|<span data-ttu-id="2cd20-167">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-167">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-168">74</span><span class="sxs-lookup"><span data-stu-id="2cd20-168">74</span></span>|<span data-ttu-id="2cd20-169">89</span><span class="sxs-lookup"><span data-stu-id="2cd20-169">89</span></span>|  
  
 <span data-ttu-id="2cd20-170">**製品と地域: M200 太平洋**</span><span class="sxs-lookup"><span data-stu-id="2cd20-170">**Product and Region: M200 Pacific**</span></span>  
  
|||||  
|-|-|-|-|  
|||<span data-ttu-id="2cd20-171">既存のモデル (`PredictTimeSeries`)</span><span class="sxs-lookup"><span data-stu-id="2cd20-171">Existing model (`PredictTimeSeries`)</span></span>|<span data-ttu-id="2cd20-172">更新された売上データを使用するモデル (`PredictTimeSeries` が指定された `EXTEND_MODEL_CASES`)</span><span class="sxs-lookup"><span data-stu-id="2cd20-172">Model with updated sales data (`PredictTimeSeries` with `EXTEND_MODEL_CASES`)</span></span>|  
|<span data-ttu-id="2cd20-173">M200 太平洋</span><span class="sxs-lookup"><span data-stu-id="2cd20-173">M200 Pacific</span></span>|<span data-ttu-id="2cd20-174">7/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-174">7/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-175">41</span><span class="sxs-lookup"><span data-stu-id="2cd20-175">41</span></span>|<span data-ttu-id="2cd20-176">41</span><span class="sxs-lookup"><span data-stu-id="2cd20-176">41</span></span>|  
|<span data-ttu-id="2cd20-177">M200 太平洋</span><span class="sxs-lookup"><span data-stu-id="2cd20-177">M200 Pacific</span></span>|<span data-ttu-id="2cd20-178">8/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-178">8/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-179">44</span><span class="sxs-lookup"><span data-stu-id="2cd20-179">44</span></span>|<span data-ttu-id="2cd20-180">44</span><span class="sxs-lookup"><span data-stu-id="2cd20-180">44</span></span>|  
|<span data-ttu-id="2cd20-181">M200 太平洋</span><span class="sxs-lookup"><span data-stu-id="2cd20-181">M200 Pacific</span></span>|<span data-ttu-id="2cd20-182">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-182">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-183">38</span><span class="sxs-lookup"><span data-stu-id="2cd20-183">38</span></span>|<span data-ttu-id="2cd20-184">38</span><span class="sxs-lookup"><span data-stu-id="2cd20-184">38</span></span>|  
|<span data-ttu-id="2cd20-185">M200 太平洋</span><span class="sxs-lookup"><span data-stu-id="2cd20-185">M200 Pacific</span></span>|<span data-ttu-id="2cd20-186">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-186">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-187">41</span><span class="sxs-lookup"><span data-stu-id="2cd20-187">41</span></span>|<span data-ttu-id="2cd20-188">41</span><span class="sxs-lookup"><span data-stu-id="2cd20-188">41</span></span>|  
|<span data-ttu-id="2cd20-189">M200 太平洋</span><span class="sxs-lookup"><span data-stu-id="2cd20-189">M200 Pacific</span></span>|<span data-ttu-id="2cd20-190">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-190">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-191">36</span><span class="sxs-lookup"><span data-stu-id="2cd20-191">36</span></span>|<span data-ttu-id="2cd20-192">36</span><span class="sxs-lookup"><span data-stu-id="2cd20-192">36</span></span>|  
|<span data-ttu-id="2cd20-193">M200 太平洋</span><span class="sxs-lookup"><span data-stu-id="2cd20-193">M200 Pacific</span></span>|<span data-ttu-id="2cd20-194">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-194">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-195">39</span><span class="sxs-lookup"><span data-stu-id="2cd20-195">39</span></span>|<span data-ttu-id="2cd20-196">39</span><span class="sxs-lookup"><span data-stu-id="2cd20-196">39</span></span>|  
  
 <span data-ttu-id="2cd20-197">これらの結果から、次の 2 つのことがわかります。</span><span class="sxs-lookup"><span data-stu-id="2cd20-197">From these results, you can see two things:</span></span>  
  
-   <span data-ttu-id="2cd20-198">M200 Europe 系列に対する最初の 2 つの予測は、指定した新しいデータとまったく同じです。</span><span class="sxs-lookup"><span data-stu-id="2cd20-198">The first two predictions for the M200 Europe series are exactly the same as the new data you supplied.</span></span> <span data-ttu-id="2cd20-199">Analysis Services の仕様では、予測を作成するのではなく実際の新しいデータ ポイントが返されます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-199">By design, Analysis Services returns the actual new data points instead of making a prediction.</span></span> <span data-ttu-id="2cd20-200">これは、モデル ケースを拡張する際に、予測クエリに使用される時間ステップが常に元の系列の末尾から開始されるためです。</span><span class="sxs-lookup"><span data-stu-id="2cd20-200">That is because when you extend the model cases, the time steps used for prediction queries always start at the end of the original series.</span></span> <span data-ttu-id="2cd20-201">このため、2 つの新しいデータ ポイントを追加すると、返される最初の 2 つの予測が新しいデータと重複します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-201">Therefore, if you add two new data points, the first two predictions returned overlap with the new data.</span></span>  
  
-   <span data-ttu-id="2cd20-202">新しいデータ ポイントがすべて使用された後に、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で更新されたモデルに基づいて予測が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-202">After all the new data points are used up, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] makes predictions based on the updated model.</span></span> <span data-ttu-id="2cd20-203">このため、2005 年 9 月以降は、左の列に示された元のモデルの M200 Europe と右の列に示された EXTEND_MODEL_CASES を使用するモデルとで予測が異なっています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-203">Therefore, starting in September 2005, you can see the difference between predictions for M200 Europe from the original model, in the left-hand column, and the model that uses EXTEND_MODEL_CASES, in the right-hand column.</span></span> <span data-ttu-id="2cd20-204">予測が異なっているのは、モデルが新しいデータで更新されたためです。</span><span class="sxs-lookup"><span data-stu-id="2cd20-204">The predictions are different because the model has been updated with the new data.</span></span>  
  
## <a name="using-start-and-end-time-steps-to-control-predictions"></a><span data-ttu-id="2cd20-205">開始および終了時間ステップを使用した予測の制御</span><span class="sxs-lookup"><span data-stu-id="2cd20-205">Using Start and End Time Steps to Control Predictions</span></span>  
 <span data-ttu-id="2cd20-206">モデルを拡張すると、新しいデータは常に系列の末尾に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-206">When you extend a model, the new data is always attached to the end of the series.</span></span> <span data-ttu-id="2cd20-207">ただし、予測の目的から、予測クエリに使用されるタイム スライスは元の系列の末尾から開始されます。</span><span class="sxs-lookup"><span data-stu-id="2cd20-207">However, for the purpose of prediction, the time slices used for prediction queries start at the end of the original series.</span></span> <span data-ttu-id="2cd20-208">新しいデータを追加する場合に新しい予測のみを取得するには、開始位置をタイム スライスの番号で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cd20-208">If you want to obtain only the new predictions when you add the new data, you must specify the starting point as a number of time slices.</span></span> <span data-ttu-id="2cd20-209">たとえば、2 つの新しいデータ ポイントを追加して 4 つの新しい予測を作成するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2cd20-209">For example, if you are adding two new data points and want to make four new predictions, you would do the following:</span></span>  
  
-   <span data-ttu-id="2cd20-210">時系列モデルに PREDICTION JOIN を作成し、2 か月分の新しいデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="2cd20-210">Create a PREDICTION JOIN on a time series model, and specify two months of new data.</span></span>  
  
-   <span data-ttu-id="2cd20-211">4 つのタイム スライスについて予測を要求します。この場合、開始位置がタイム スライス 3、終了位置がタイム スライス 6 です。</span><span class="sxs-lookup"><span data-stu-id="2cd20-211">Request predictions for four time slices, where the starting point is 3, and the ending point is time slice 6.</span></span>  
  
 <span data-ttu-id="2cd20-212">つまり、新しいデータに n 個のタイムスライスが含まれていて、時間ステップ 1 ~ n の予測を要求した場合、予測は新しいデータと同じ期間になります。</span><span class="sxs-lookup"><span data-stu-id="2cd20-212">In other words, if your new data contains n time slices, and you request predictions for time steps 1 through n, the predictions will coincide with the same period as the new data.</span></span> <span data-ttu-id="2cd20-213">データに含まれていない期間の新しい予測を取得するには、新しいデータ系列後のタイム スライス n+1 から予測を開始するか、他のタイム スライスの要求を行うようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cd20-213">To get new predictions for a time periods not covered by your data, you must either start predictions at the time slice n+1 after the new data series, or make sure that you request additional time slices.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2cd20-214">新しいデータを追加するときは履歴予測を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="2cd20-214">You cannot make historical predictions when you add new data.</span></span>  
  
 <span data-ttu-id="2cd20-215">次の例は、前の例の 2 つの系列に対する新しい予測のみを取得する DMX ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-215">The following example shows the DMX statement that lets you get only the new predictions for the two series in the previous example.</span></span>  
  
```  
SELECT [Model Region],  
PredictTimeSeries([Quantity],3,6, EXTEND_MODEL_CASES) AS PredictQty  
FROM  
   [Forecasting_MIXED]  
NATURAL PREDICTION JOIN   
   SELECT 1 AS [ReportingDate],  
  '10' AS [Quantity],  
  'M200 Europe' AS [ModelRegion]  
UNION SELECT  
  2 AS [ReportingDate],  
  15 AS [Quantity]),  
  'M200 Europe' AS [ModelRegion]  
) AS t  
WHERE [ModelRegion] = 'M200 Europe'  
```  
  
 <span data-ttu-id="2cd20-216">予測結果はタイム スライス 3、つまり指定した 2 か月分の新しいデータの後から開始しています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-216">The prediction results start at time slice 3, which is after the 2 months of new data that you supplied.</span></span>  
  
 <span data-ttu-id="2cd20-217">**製品と地域: M200 ヨーロッパ**</span><span class="sxs-lookup"><span data-stu-id="2cd20-217">**Product and Region: M200 Europe**</span></span>  
  
 <span data-ttu-id="2cd20-218">更新されたデータを使用するモデル (EXTEND_MODEL_CASES を指定した PredictTimeSeries)</span><span class="sxs-lookup"><span data-stu-id="2cd20-218">Model with updated data (PredictTimeSeries with EXTEND_MODEL_CASES)</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="2cd20-219">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-219">M200 Europe</span></span>|<span data-ttu-id="2cd20-220">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-220">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-221">72</span><span class="sxs-lookup"><span data-stu-id="2cd20-221">72</span></span>|  
|<span data-ttu-id="2cd20-222">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-222">M200 Europe</span></span>|<span data-ttu-id="2cd20-223">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-223">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-224">69</span><span class="sxs-lookup"><span data-stu-id="2cd20-224">69</span></span>|  
|<span data-ttu-id="2cd20-225">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-225">M200 Europe</span></span>|<span data-ttu-id="2cd20-226">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-226">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-227">68</span><span class="sxs-lookup"><span data-stu-id="2cd20-227">68</span></span>|  
|<span data-ttu-id="2cd20-228">M200 ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="2cd20-228">M200 Europe</span></span>|<span data-ttu-id="2cd20-229">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="2cd20-229">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="2cd20-230">89</span><span class="sxs-lookup"><span data-stu-id="2cd20-230">89</span></span>|  
  
## <a name="making-predictions-with-replace_model_cases"></a><span data-ttu-id="2cd20-231">REPLACE_MODEL_CASES を使用した予測の作成</span><span class="sxs-lookup"><span data-stu-id="2cd20-231">Making Predictions with REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="2cd20-232">1 セットのケースでモデルをトレーニングし、そのモデルを別のデータ系列に適用するときは、モデル ケースの置換が便利です。</span><span class="sxs-lookup"><span data-stu-id="2cd20-232">Replacing the model cases is useful when you want to train a model on one set of cases and then apply that model to a different data series.</span></span> <span data-ttu-id="2cd20-233">このシナリオの詳細なチュートリアルについては、 [「レッスン 2: 予測シナリオの構築 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)」で説明されています。</span><span class="sxs-lookup"><span data-stu-id="2cd20-233">A detailed walkthrough of this scenario is presented in [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd20-234">参照</span><span class="sxs-lookup"><span data-stu-id="2cd20-234">See Also</span></span>  
 <span data-ttu-id="2cd20-235">[タイムシリーズモデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="2cd20-235">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="2cd20-236">PredictTimeSeries &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="2cd20-236">PredictTimeSeries &#40;DMX&#41;</span></span>](/sql/dmx/predicttimeseries-dmx)  
  
  
