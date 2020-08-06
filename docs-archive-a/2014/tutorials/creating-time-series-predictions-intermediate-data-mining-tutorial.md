---
title: 時系列予測の作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fb22cffa-ac99-4d34-ac4a-9c93068e33e8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1175cdffd1512e0cb876b9565dd0727a9f094c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633701"
---
# <a name="creating-time-series-predictions-intermediate-data-mining-tutorial"></a><span data-ttu-id="2574f-102">時系列予測の作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="2574f-102">Creating Time Series Predictions (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="2574f-103">このレッスンの前の作業では、時系列モデルを作成し、結果を検証しました。</span><span class="sxs-lookup"><span data-stu-id="2574f-103">In the previous tasks in this lesson, you created a time series model and explored the results.</span></span> <span data-ttu-id="2574f-104">既定では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって常に時系列モデルの 5 つの予測のセットが作成され、予測された値が予測グラフの一部として表示されます。</span><span class="sxs-lookup"><span data-stu-id="2574f-104">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] always creates a set of five (5) predictions for a time series model and displays the predicted values as part of the forecasting chart.</span></span> <span data-ttu-id="2574f-105">ただし、データ マイニング拡張機能 (DMX) の予測クエリを作成することによって、予測を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2574f-105">However, you can also create forecasts by building Data Mining Extensions (DMX) prediction queries.</span></span>  
  
 <span data-ttu-id="2574f-106">この作業では、ビューアーに表示された予測と同じ予測を生成する予測クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="2574f-106">In this task, you will create a prediction query that generates the same predictions that you saw in the viewer.</span></span> <span data-ttu-id="2574f-107">「基本的なデータ マイニング チュートリアル」のレッスンが完了し、予測クエリ ビルダーの使用方法について理解していることを前提とします。</span><span class="sxs-lookup"><span data-stu-id="2574f-107">This task assumes that you have already completed the lessons in the Basic Data Mining Tutorial and are familiar with how to use Prediction Query Builder.</span></span> <span data-ttu-id="2574f-108">ここでは、時系列モデルに固有のクエリを作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="2574f-108">You will now learn how to create queries specific to time series models.</span></span>  
  
## <a name="creating-time-series-predictions"></a><span data-ttu-id="2574f-109">時系列予測の作成</span><span class="sxs-lookup"><span data-stu-id="2574f-109">Creating Time Series Predictions</span></span>  
 <span data-ttu-id="2574f-110">通常、予測クエリを作成するには、まず、マイニング モデルと入力テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2574f-110">Typically, the first step in creating a prediction query is to select a mining model and input table.</span></span> <span data-ttu-id="2574f-111">ただし、時系列モデルでは、通常の予測では必要な追加の入力が必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2574f-111">However, a time series model does not require additional input for a regular prediction.</span></span> <span data-ttu-id="2574f-112">したがって、モデルにデータを追加したり、データを置き換えたりする場合以外は、予測を行うときに新しいデータ ソースを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2574f-112">Therefore, you do not need to specify a new source of data when making predictions, unless you are adding data to the model or replacing the data.</span></span>  
  
 <span data-ttu-id="2574f-113">このレッスンでは、予測期間の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2574f-113">For this lesson, you must specify the number of prediction steps.</span></span> <span data-ttu-id="2574f-114">系列名を指定して、製品と地域の特定の組み合わせに対する予測を取得できます。</span><span class="sxs-lookup"><span data-stu-id="2574f-114">You can specify the series name, to get a prediction for a particular combination of a product and a region.</span></span>  
  
#### <a name="to-select-a-model-and-input-table"></a><span data-ttu-id="2574f-115">モデルと入力テーブルを選択するには</span><span class="sxs-lookup"><span data-stu-id="2574f-115">To select a model and input table</span></span>  
  
1.  <span data-ttu-id="2574f-116">データマイニングデザイナーの [**マイニングモデル予測**] タブで、[**マイニングモデル**] ボックスの [**モデルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2574f-116">On the **Mining Model Prediction** tab of the Data Mining Designer, in the **Mining Model** box, click **Select Model**.</span></span>  
  
2.  <span data-ttu-id="2574f-117">**[マイニングモデルの選択**] ダイアログボックスで、予測構造を展開し、一覧から**予測**モデルを選択して、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2574f-117">In the **Select Mining Model** dialog box, expand the Forecasting structure, select the **Forecasting** model from the list, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2574f-118">**[入力テーブルの選択**] ボックスは無視します。</span><span class="sxs-lookup"><span data-stu-id="2574f-118">Ignore the **Select Input Table(s)** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2574f-119">時系列モデルでは、クロス予測を実行する場合以外は、個別の入力を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2574f-119">For a time series model, you do not need to specify a separate input unless you are doing cross-prediction.</span></span>  
  
4.  <span data-ttu-id="2574f-120">[**基**になる列] の [**マイニングモデル予測**] タブのグリッドで、最初の空白行のセルをクリックし、[**マイニングモデルの予測**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2574f-120">In the **Source** column, in the grid on the **Mining Model Prediction** tab, click the cell in the first empty row, and then select **Forecasting mining model**.</span></span>  
  
5.  <span data-ttu-id="2574f-121">[**フィールド]** 列で [**モデル領域**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2574f-121">In the **Field** column, select **Model Region**.</span></span>  
  
     <span data-ttu-id="2574f-122">この操作により、予測クエリに系列の識別子が追加され、予測が適用されるモデルと地域の組み合わせが指定されます。</span><span class="sxs-lookup"><span data-stu-id="2574f-122">This action adds the series identifier to the prediction query to indicate the combination of model and region to which the prediction applies.</span></span>  
  
6.  <span data-ttu-id="2574f-123">[**基**になる列] で次の空白行をクリックし、[**予測関数**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2574f-123">Click the next empty row in the **Source** column, and then select **Prediction Function**.</span></span>  
  
7.  <span data-ttu-id="2574f-124">[**フィールド]** 列で、[ **PredictTimeSeries**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2574f-124">In the **Field** column, select **PredictTimeSeries**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2574f-125">`Predict`関数をタイムシリーズモデルと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2574f-125">You can also use the `Predict` function with time series models.</span></span> <span data-ttu-id="2574f-126">ただし、既定では、Predict 関数を使用すると、系列ごとに 1 つしか予測が作成されません。</span><span class="sxs-lookup"><span data-stu-id="2574f-126">However, by default, the Predict function creates only one prediction for each series.</span></span> <span data-ttu-id="2574f-127">したがって、複数の予測ステップを指定するには、 **PredictTimeSeries**関数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2574f-127">Therefore, to specify multiple prediction steps, you must use the **PredictTimeSeries** function.</span></span>  
  
8.  <span data-ttu-id="2574f-128">[**マイニングモデル**] ペインで、[マイニングモデル] 列に [Amount] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="2574f-128">In the **Mining Model** pane, select the mining model column, **Amount.**</span></span> <span data-ttu-id="2574f-129">[Amount] を、前に追加した**PredictTimeSeries**関数の [**条件と引数**] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2574f-129">Drag Amount to the **Criteria/Arguments** box for the **PredictTimeSeries** function that you added earlier.</span></span>  
  
9. <span data-ttu-id="2574f-130">[**条件と引数**] ボックスをクリックし、フィールド名の後にコンマを入力し、続けて「 **5**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2574f-130">Click the **Criteria/Arguments** box, and type a comma, followed by **5**, after the field name.</span></span>  
  
     <span data-ttu-id="2574f-131">[**条件と引数**] ボックスのテキストに、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="2574f-131">The text in the **Criteria/Arguments** box should now display the following:</span></span>  
  
     `[Forecasting].[Amount],5`  
  
10. <span data-ttu-id="2574f-132">[**別名**] 列に「」と入力 `PredictAmount` します。</span><span class="sxs-lookup"><span data-stu-id="2574f-132">In the **Alias** column, type `PredictAmount`.</span></span>  
  
11. <span data-ttu-id="2574f-133">[**ソース**] 列の次の空白行をクリックし、[**予測関数**] を再度選択します。</span><span class="sxs-lookup"><span data-stu-id="2574f-133">Click the next empty row in the **Source** column, and then select **Prediction Function** again.</span></span>  
  
12. <span data-ttu-id="2574f-134">[**フィールド]** 列で、[ **PredictTimeSeries**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2574f-134">In the **Field** column, select **PredictTimeSeries**.</span></span>  
  
13. <span data-ttu-id="2574f-135">[**マイニングモデル**] ペインで、[Quantity] 列を選択し、2番目の**PredictTimeSeries**関数の [**条件と引数**] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2574f-135">In the **Mining Model** pane, select the column Quantity, and then drag it into the **Criteria/Arguments** box for the second **PredictTimeSeries** function.</span></span>  
  
14. <span data-ttu-id="2574f-136">[**条件と引数**] ボックスをクリックし、フィールド名の後にコンマを入力し、続けて「 **5**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2574f-136">Click the **Criteria/Arguments** box, and type a comma, followed by **5**, after the field name.</span></span>  
  
     <span data-ttu-id="2574f-137">[**条件と引数**] ボックスのテキストに、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="2574f-137">The text in the **Criteria/Arguments** box should now display the following:</span></span>  
  
     `[Forecasting].[ Quantity],5`  
  
15. <span data-ttu-id="2574f-138">[**別名**] 列に「」と入力 `PredictQuantity` します。</span><span class="sxs-lookup"><span data-stu-id="2574f-138">In the **Alias** column, type `PredictQuantity`.</span></span>  
  
16. <span data-ttu-id="2574f-139">[**クエリ結果ビューに切り替え] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="2574f-139">Click **Switch to query result view**.</span></span>  
  
     <span data-ttu-id="2574f-140">クエリの結果が表形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2574f-140">The results of the query are displayed in tabular format.</span></span>  
  
 <span data-ttu-id="2574f-141">クエリ ビルダーで 3 種類の異なる結果を作成したことに注意してください。列の値を使用した結果が 1 つと、予測関数から予測値を取得した結果が 2 つです。</span><span class="sxs-lookup"><span data-stu-id="2574f-141">Remember that you created three different types of results in the query builder, one that uses values from a column, and two that get predicted values from a prediction function.</span></span> <span data-ttu-id="2574f-142">したがって、クエリの結果には 3 つの異なる列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2574f-142">Therefore, the results of the query contain three separate columns.</span></span> <span data-ttu-id="2574f-143">最初の列には、製品と地域の組み合わせの一覧が格納されます。</span><span class="sxs-lookup"><span data-stu-id="2574f-143">The first column contains the list of product and region combinations.</span></span> <span data-ttu-id="2574f-144">2 番目と 3 番目の列には、それぞれ、予測結果の入れ子になったテーブルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="2574f-144">The second and third columns each contain a nested table of prediction results.</span></span> <span data-ttu-id="2574f-145">入れ子になった各テーブルには、次の表のような時間ステップと予測された値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2574f-145">Each nested table contains the time step and predicted values, such as the following table:</span></span>  
  
 <span data-ttu-id="2574f-146">例の結果 (金額は小数点以下 2 桁に切り捨てられます):</span><span class="sxs-lookup"><span data-stu-id="2574f-146">Example results (amounts are truncated to two decimal places):</span></span>  
  
 <span data-ttu-id="2574f-147">**M200 ヨーロッパ PredictAmount**</span><span class="sxs-lookup"><span data-stu-id="2574f-147">**M200 Europe PredictAmount**</span></span>  
  
|<span data-ttu-id="2574f-148">$TIME</span><span class="sxs-lookup"><span data-stu-id="2574f-148">$TIME</span></span>|<span data-ttu-id="2574f-149">Amount (金額)</span><span class="sxs-lookup"><span data-stu-id="2574f-149">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="2574f-150">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-150">7/25/2008</span></span>|<span data-ttu-id="2574f-151">99978.00</span><span class="sxs-lookup"><span data-stu-id="2574f-151">99978.00</span></span>|  
|<span data-ttu-id="2574f-152">8/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-152">8/25/2008</span></span>|<span data-ttu-id="2574f-153">145575.07</span><span class="sxs-lookup"><span data-stu-id="2574f-153">145575.07</span></span>|  
|<span data-ttu-id="2574f-154">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-154">9/25/2008</span></span>|<span data-ttu-id="2574f-155">116835.19</span><span class="sxs-lookup"><span data-stu-id="2574f-155">116835.19</span></span>|  
|<span data-ttu-id="2574f-156">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-156">10/25/2008</span></span>|<span data-ttu-id="2574f-157">116537.38</span><span class="sxs-lookup"><span data-stu-id="2574f-157">116537.38</span></span>|  
|<span data-ttu-id="2574f-158">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-158">11/25/2008</span></span>|<span data-ttu-id="2574f-159">107760.55</span><span class="sxs-lookup"><span data-stu-id="2574f-159">107760.55</span></span>|  
  
 <span data-ttu-id="2574f-160">**M200 ヨーロッパ PredictQuantity**</span><span class="sxs-lookup"><span data-stu-id="2574f-160">**M200 Europe PredictQuantity**</span></span>  
  
|<span data-ttu-id="2574f-161">$TIME</span><span class="sxs-lookup"><span data-stu-id="2574f-161">$TIME</span></span>|<span data-ttu-id="2574f-162">Quantity</span><span class="sxs-lookup"><span data-stu-id="2574f-162">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="2574f-163">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-163">7/25/2008</span></span>|<span data-ttu-id="2574f-164">52</span><span class="sxs-lookup"><span data-stu-id="2574f-164">52</span></span>|  
|<span data-ttu-id="2574f-165">8/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-165">8/25/2008</span></span>|<span data-ttu-id="2574f-166">67</span><span class="sxs-lookup"><span data-stu-id="2574f-166">67</span></span>|  
|<span data-ttu-id="2574f-167">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-167">9/25/2008</span></span>|<span data-ttu-id="2574f-168">58</span><span class="sxs-lookup"><span data-stu-id="2574f-168">58</span></span>|  
|<span data-ttu-id="2574f-169">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-169">10/25/2008</span></span>|<span data-ttu-id="2574f-170">57</span><span class="sxs-lookup"><span data-stu-id="2574f-170">57</span></span>|  
|<span data-ttu-id="2574f-171">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-171">11/25/2008</span></span>|<span data-ttu-id="2574f-172">54</span><span class="sxs-lookup"><span data-stu-id="2574f-172">54</span></span>|  
  
 <span data-ttu-id="2574f-173">**M200 北米-PredictAmount**</span><span class="sxs-lookup"><span data-stu-id="2574f-173">**M200 North America - PredictAmount**</span></span>  
  
|<span data-ttu-id="2574f-174">$TIME</span><span class="sxs-lookup"><span data-stu-id="2574f-174">$TIME</span></span>|<span data-ttu-id="2574f-175">Amount (金額)</span><span class="sxs-lookup"><span data-stu-id="2574f-175">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="2574f-176">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-176">7/25/2008</span></span>|<span data-ttu-id="2574f-177">348533.93</span><span class="sxs-lookup"><span data-stu-id="2574f-177">348533.93</span></span>|  
|<span data-ttu-id="2574f-178">8/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-178">8/25/2008</span></span>|<span data-ttu-id="2574f-179">340097.98</span><span class="sxs-lookup"><span data-stu-id="2574f-179">340097.98</span></span>|  
|<span data-ttu-id="2574f-180">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-180">9/25/2008</span></span>|<span data-ttu-id="2574f-181">257986.19</span><span class="sxs-lookup"><span data-stu-id="2574f-181">257986.19</span></span>|  
|<span data-ttu-id="2574f-182">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-182">10/25/2008</span></span>|<span data-ttu-id="2574f-183">374658.24</span><span class="sxs-lookup"><span data-stu-id="2574f-183">374658.24</span></span>|  
|<span data-ttu-id="2574f-184">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-184">11/25/2008</span></span>|<span data-ttu-id="2574f-185">379241.44</span><span class="sxs-lookup"><span data-stu-id="2574f-185">379241.44</span></span>|  
  
 <span data-ttu-id="2574f-186">**M200 北米-PredictQuantity**</span><span class="sxs-lookup"><span data-stu-id="2574f-186">**M200 North America - PredictQuantity**</span></span>  
  
|<span data-ttu-id="2574f-187">$TIME</span><span class="sxs-lookup"><span data-stu-id="2574f-187">$TIME</span></span>|<span data-ttu-id="2574f-188">Quantity</span><span class="sxs-lookup"><span data-stu-id="2574f-188">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="2574f-189">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-189">7/25/2008</span></span>|<span data-ttu-id="2574f-190">272</span><span class="sxs-lookup"><span data-stu-id="2574f-190">272</span></span>|  
|<span data-ttu-id="2574f-191">8/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-191">8/25/2008</span></span>|<span data-ttu-id="2574f-192">152</span><span class="sxs-lookup"><span data-stu-id="2574f-192">152</span></span>|  
|<span data-ttu-id="2574f-193">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-193">9/25/2008</span></span>|<span data-ttu-id="2574f-194">250</span><span class="sxs-lookup"><span data-stu-id="2574f-194">250</span></span>|  
|<span data-ttu-id="2574f-195">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-195">10/25/2008</span></span>|<span data-ttu-id="2574f-196">181</span><span class="sxs-lookup"><span data-stu-id="2574f-196">181</span></span>|  
|<span data-ttu-id="2574f-197">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="2574f-197">11/25/2008</span></span>|<span data-ttu-id="2574f-198">290</span><span class="sxs-lookup"><span data-stu-id="2574f-198">290</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="2574f-199">サンプル データベースで使用されている日付は、このリリース用に更新されています。</span><span class="sxs-lookup"><span data-stu-id="2574f-199">The dates that are used in the sample database have changed for this release.</span></span> <span data-ttu-id="2574f-200">以前のバージョンのサンプル データを使用している場合は、異なる結果が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2574f-200">If you are using an earlier version of the sample data, you might see different results.</span></span>  
  
## <a name="saving-the-prediction-results"></a><span data-ttu-id="2574f-201">予測結果の保存</span><span class="sxs-lookup"><span data-stu-id="2574f-201">Saving the Prediction Results</span></span>  
 <span data-ttu-id="2574f-202">いくつかの方法で予測結果を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2574f-202">You have several different options for using the prediction results.</span></span> <span data-ttu-id="2574f-203">結果をフラット化し、結果ビューのデータをコピーして、Excel ワークシートなどのファイルに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="2574f-203">You can flatten the results, copy the data from the Results view, and paste it into an Excel worksheet or other file.</span></span>  
  
 <span data-ttu-id="2574f-204">結果を保存するプロセスを簡単にするため、データ マイニング デザイナーではデータをデータ ソース ビューに保存する機能も提供されています。</span><span class="sxs-lookup"><span data-stu-id="2574f-204">To simplify the process of saving results, Data Mining Designer also provides the ability to save the data to a data source view.</span></span> <span data-ttu-id="2574f-205">結果をデータ ソース ビューに保存する機能は、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] だけで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2574f-205">The functionality for saving results to a data source view is available only in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="2574f-206">結果はフラット化された形式でのみ格納できます。</span><span class="sxs-lookup"><span data-stu-id="2574f-206">The results can only be stored in a flattened format.</span></span>  
  
#### <a name="to-flatten-the-results-in-the-results-pane"></a><span data-ttu-id="2574f-207">結果ペインで結果をフラット化するには</span><span class="sxs-lookup"><span data-stu-id="2574f-207">To flatten the results in the Results pane</span></span>  
  
1.  <span data-ttu-id="2574f-208">[予測クエリビルダーで、[**クエリデザインビューに切り替え**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2574f-208">In the Prediction Query Builder, click **Switch to query design view**.</span></span>  
  
     <span data-ttu-id="2574f-209">ビューが切り替わり、DMX クエリ テキストを手動で編集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2574f-209">The view changes to allow manual editing of the DMX query text.</span></span>  
  
2.  <span data-ttu-id="2574f-210">`FLATTENED` キーワードの後に、`SELECT` キーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="2574f-210">Type the `FLATTENED` keyword after the `SELECT` keyword.</span></span> <span data-ttu-id="2574f-211">最終的なクエリ テキストは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2574f-211">The complete query text should be as follows:</span></span>  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    ```  
  
3.  <span data-ttu-id="2574f-212">必要に応じて、次の例のように、結果を制限するための句を入力できます。</span><span class="sxs-lookup"><span data-stu-id="2574f-212">Optionally, you can type a clause to restrict the results, such as the following example:</span></span>  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    WHERE [Forecasting].[Model Region] = 'M200 North America'   
    OR [Forecasting].[Model Region] = 'M200 Europe'  
  
    ```  
  
4.  <span data-ttu-id="2574f-213">[**クエリ結果ビューに切り替え] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="2574f-213">Click **Switch to query result view**.</span></span>  
  
#### <a name="to-export-prediction-query-results"></a><span data-ttu-id="2574f-214">予測クエリの結果をエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="2574f-214">To export prediction query results</span></span>  
  
1.  <span data-ttu-id="2574f-215">[**クエリ結果の保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2574f-215">Click **Save query results**.</span></span>  
  
2.  <span data-ttu-id="2574f-216">[**データマイニングのクエリ結果の保存**] ダイアログボックスの [**データソース**] で、[] を選択し [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2574f-216">In the **Save Data Mining Query Result** dialog box, for **Data Source**, select [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span> <span data-ttu-id="2574f-217">データを別のリレーショナル データベースに保存する場合は、データ ソースを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2574f-217">You can also create a data source if you want to save the data to a different relational database.</span></span>  
  
3.  <span data-ttu-id="2574f-218">[**テーブル名**] 列に、「**テスト予測**」など、新しい一時テーブル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="2574f-218">In the **Table Name** column, type a new temporary table name, such as **Test Predictions**.</span></span>  
  
4.  <span data-ttu-id="2574f-219">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2574f-219">Click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2574f-220">作成したテーブルを表示するには、データを保存したインスタンスのデータベース エンジンに対する接続を作成し、クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="2574f-220">To view the table that you created, create a connection to the database engine of the instance where you saved the data, and create a query.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="2574f-221">まとめ</span><span class="sxs-lookup"><span data-stu-id="2574f-221">Conclusion</span></span>  
 <span data-ttu-id="2574f-222">基本的な時系列モデルを作成し、予測を解釈し、予測を作成する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="2574f-222">You have learned how to build a basic time series model, interpret the forecasts, and create predictions.</span></span>  
  
 <span data-ttu-id="2574f-223">このチュートリアルの残りのタスクは省略可能であり、高度な時系列予測について説明します。</span><span class="sxs-lookup"><span data-stu-id="2574f-223">The remaining tasks in this tutorial are optional, and describe advanced time series predictions.</span></span> <span data-ttu-id="2574f-224">さらにチュートリアルを続けると、モデルに新しいデータを追加し、拡張系列で予測を作成する方法について学習できます。</span><span class="sxs-lookup"><span data-stu-id="2574f-224">If you decide to go on, you will learn how to add new data to your model and create predictions on the extended series.</span></span> <span data-ttu-id="2574f-225">また、モデルの傾向を使用し、データを新しい系列に置き換えることで、クロス予測を実行する方法についても学習します。</span><span class="sxs-lookup"><span data-stu-id="2574f-225">You will also learn how to perform cross-prediction, by using the trend in the model but replacing the data with a new series of data.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="2574f-226">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="2574f-226">Next Lesson</span></span>  
 [<span data-ttu-id="2574f-227">高度な時系列予測 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="2574f-227">Advanced Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="2574f-228">参照</span><span class="sxs-lookup"><span data-stu-id="2574f-228">See Also</span></span>  
 [<span data-ttu-id="2574f-229">Time Series Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="2574f-229">Time Series Model Query Examples</span></span>](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
