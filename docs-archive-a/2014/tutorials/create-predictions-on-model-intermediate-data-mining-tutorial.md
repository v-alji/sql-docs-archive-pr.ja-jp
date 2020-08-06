---
title: シーケンスクラスターモデルでの予測の作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 2402c28a564502df9ce12c5e3f97b9d19590cfea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630725"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="dc168-102">シーケンス クラスター モデルでの予測の作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="dc168-102">Creating Predictions on a Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="dc168-103">ビューアーでシーケンスクラスターモデルを参照して理解した後、データマイニングデザイナーの [**マイニングモデル予測**] タブで予測クエリビルダーを使用して、予測クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dc168-103">After you understand the sequence clustering model better by browsing it in the viewer, you can create prediction queries by using Prediction Query Builder on the **Mining Model Prediction** tab in Data Mining Designer.</span></span> <span data-ttu-id="dc168-104">予測を作成するには、まずシーケンス クラスター モデルを選択し、次に入力データを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-104">To create a prediction, you first select the sequence clustering model, and then select the input data.</span></span> <span data-ttu-id="dc168-105">入力については、外部データ ソースを使用するか、単一クエリを作成してダイアログ ボックスで値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="dc168-105">For inputs, you can use either an external data source, or you can build a singleton query and provide values in a dialog box.</span></span>  
  
 <span data-ttu-id="dc168-106">このレッスンでは、予測クエリ ビルダーの使用方法について理解していることを前提に、シーケンス クラスター モデルに固有のクエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc168-106">This lesson assumes that you are already familiar with how to use the prediction query builder and want to learn how to build queries that are specific to a sequence clustering model.</span></span> <span data-ttu-id="dc168-107">予測クエリビルダーの使用方法に関する一般的な情報については、「データマイニング[クエリインターフェイス](../../2014/analysis-services/data-mining/data-mining-query-tools.md)」、または「基本的なデータマイニングチュートリアル」の「[予測の作成 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc168-107">For general information about how to use Prediction Query Builder, see [Data Mining Query Interfaces](../../2014/analysis-services/data-mining/data-mining-query-tools.md) or the section of the Basic Data Mining tutorial, [Creating Predictions &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).</span></span>  
  
## <a name="creating-predictions-on-the-regional-model"></a><span data-ttu-id="dc168-108">地域モデルでの予測の作成</span><span class="sxs-lookup"><span data-stu-id="dc168-108">Creating Predictions on the Regional Model</span></span>  
 <span data-ttu-id="dc168-109">このシナリオでは、まずいくつかの単一予測クエリを作成し、予測が地域ごとにどのように異なるかについて確認します。</span><span class="sxs-lookup"><span data-stu-id="dc168-109">For this scenario, you will first create some singleton prediction queries, to get an idea of how predictions might be different by region.</span></span>  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a><span data-ttu-id="dc168-110">シーケンス クラスター モデルに対する単一クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="dc168-110">To create a singleton query on a sequence clustering model</span></span>  
  
1.  <span data-ttu-id="dc168-111">データマイニングデザイナーの [**マイニングモデル予測**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-111">Click the **Mining Model Prediction** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="dc168-112">[**マイニングモデル**列] メニューの [**単一クエリ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-112">In the **Mining Model** column menu, select **Singleton Query**.</span></span>  
  
     <span data-ttu-id="dc168-113">[**マイニングモデル**] ペインと [**単一クエリ入力**] ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-113">The **Mining Model** pane and **Singleton Query Input** pane appear.</span></span>  
  
3.  <span data-ttu-id="dc168-114">[**マイニングモデル**] ペインで、[**モデルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-114">In the **Mining Model** pane, click **Select Model**.</span></span> <span data-ttu-id="dc168-115">(既にシーケンス クラスター モデルが選択されている場合は、この手順を省略します)。</span><span class="sxs-lookup"><span data-stu-id="dc168-115">(You can skip this step if the sequence clustering mode is already selected.)</span></span>  
  
     <span data-ttu-id="dc168-116">**[マイニングモデルの選択**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-116">The **Select Mining Model** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="dc168-117">[マイニング構造]**シーケンスクラスター**を表すノードを [リージョン] で展開し、[**リージョンを含むモデルシーケンスクラスター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-117">Expand the node that represents the mining structure **Sequence Clustering with Region**, and select the model **Sequence Clustering with Region**.</span></span> <span data-ttu-id="dc168-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-118">Click **OK**.</span></span> <span data-ttu-id="dc168-119">ここでは、入力ペインは無視します。入力は予測関数の設定後に指定します。</span><span class="sxs-lookup"><span data-stu-id="dc168-119">For now, ignore the input pane; you will specify the inputs after you have set up the prediction functions.</span></span>  
  
5.  <span data-ttu-id="dc168-120">グリッドで、[**ソース**] の下の空のセルをクリックし、[予測関数] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="dc168-120">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="dc168-121">[**フィールド**] の下のセルで、[ **PredictSequence**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-121">In the cell under **Field**, select **PredictSequence**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc168-122">また、 **Predict**関数を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc168-122">You can also use the **Predict** function.</span></span> <span data-ttu-id="dc168-123">この場合、テーブル列を引数として受け取る**Predict**関数のバージョンを選択してください。</span><span class="sxs-lookup"><span data-stu-id="dc168-123">If you do, be sure to choose the version of the **Predict** function that takes a table column as argument..</span></span>  
  
6.  <span data-ttu-id="dc168-124">[**マイニングモデル**] ペインで、入れ子になったテーブルを選択し、グリッド内の `v Assoc Seq Line Items` **PredictSequence**関数の [**条件と引数**] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="dc168-124">In the **Mining Model** pane, select the nested table `v Assoc Seq Line Items`, and drag it into the grid, to the **Criteria/Argument** box for the **PredictSequence** function.</span></span>  
  
     <span data-ttu-id="dc168-125">テーブル名と列名をドラッグアンドドロップすると、構文エラーを発生させずに複雑なステートメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dc168-125">Dragging and dropping table and column names enables you to build complex statements without syntax errors.</span></span> <span data-ttu-id="dc168-126">ただし、セルの現在の内容は置き換えられます。これには、 **PredictSequence**関数のその他の省略可能な引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc168-126">However, it replaces the current contents of the cell, which include other optional arguments for the **PredictSequence** function.</span></span> <span data-ttu-id="dc168-127">その他の引数を表示するには、関数の 2 番目のインスタンスを参照用として一時的にグリッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="dc168-127">To view the other arguments, you can temporarily add a second instance of the function to the grid for reference.</span></span>  
  
7.  <span data-ttu-id="dc168-128">予測クエリビルダーの上隅にある [**結果**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-128">Click the **Result** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="dc168-129">期待される結果には、見出し**式**を含む1つの列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc168-129">The expected results contain a single column with the heading **Expression**.</span></span> <span data-ttu-id="dc168-130">**式**列には、次の3つの列を含む入れ子になったテーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc168-130">The **Expression** column contains a nested table with three columns as follows:</span></span>  
  
|<span data-ttu-id="dc168-131">$SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="dc168-131">$SEQUENCE</span></span>|<span data-ttu-id="dc168-132">Line Number</span><span class="sxs-lookup"><span data-stu-id="dc168-132">Line Number</span></span>|<span data-ttu-id="dc168-133">モデル</span><span class="sxs-lookup"><span data-stu-id="dc168-133">Model</span></span>|  
|---------------|-----------------|-----------|  
|<span data-ttu-id="dc168-134">1</span><span class="sxs-lookup"><span data-stu-id="dc168-134">1</span></span>||<span data-ttu-id="dc168-135">Mountain-200</span><span class="sxs-lookup"><span data-stu-id="dc168-135">Mountain-200</span></span>|  
  
 <span data-ttu-id="dc168-136">この結果からわかることは何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="dc168-136">What do these results mean?</span></span> <span data-ttu-id="dc168-137">入力を指定していないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dc168-137">Remember that you did not specify any inputs.</span></span> <span data-ttu-id="dc168-138">予測はケースの母集団全体に対して作成され、Analysis Services からは最も可能性の高い全体的な予測が返されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-138">Therefore, the prediction is made against the entire population of cases, and Analysis Services returns the most likely prediction overall.</span></span>  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a><span data-ttu-id="dc168-139">単一予測クエリへの入力の追加</span><span class="sxs-lookup"><span data-stu-id="dc168-139">Adding Inputs to a Singleton Prediction Query</span></span>  
 <span data-ttu-id="dc168-140">この時点では、まだ入力を指定していません。</span><span class="sxs-lookup"><span data-stu-id="dc168-140">Until now, you have not specified any inputs.</span></span> <span data-ttu-id="dc168-141">次のタスクでは、[**単一クエリ入力**] ペインを使用してクエリへの入力を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc168-141">In the next task, you will use the **Singleton Query Input** pane to specify some inputs to the query.</span></span> <span data-ttu-id="dc168-142">まず、予測されたシーケンスがすべての地域で同じかどうかを判断するために、地域シーケンス クラスター モデルへの入力として [Region] を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc168-142">First, you will use [Region] as an input to the regional sequence clustering model, to determine whether the predicted sequences are the same for all regions.</span></span> <span data-ttu-id="dc168-143">次に、各予測の確率を追加するようにクエリを変更し、結果をフラット化して見やすくする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc168-143">You will then learn how to modify the query to add the probability for each prediction, and flatten the results to make them easier to view.</span></span>  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a><span data-ttu-id="dc168-144">特定の顧客グループの予測を生成するには</span><span class="sxs-lookup"><span data-stu-id="dc168-144">To generate predictions for a specific customer group</span></span>  
  
1.  <span data-ttu-id="dc168-145">予測クエリビルダーの左上隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc168-145">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="dc168-146">[**単一クエリ入力**] ダイアログボックスで、の [**値**] ボックスをクリック `Region` し、[**ヨーロッパ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-146">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select **Europe**.</span></span>  
  
3.  <span data-ttu-id="dc168-147">[**結果**] ボタンをクリックすると、ヨーロッパの顧客の予測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-147">Click the **Result** button to view predictions for customers in Europe.</span></span>  
  
4.  <span data-ttu-id="dc168-148">予測クエリビルダーの左上隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc168-148">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
5.  <span data-ttu-id="dc168-149">[**単一クエリ入力**] ダイアログボックスで、の [**値**] ボックスをクリック `Region` し、[**北米**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-149">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select **North America**.</span></span>  
  
6.  <span data-ttu-id="dc168-150">北米の顧客の予測を表示するには、[**結果**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-150">Click the **Result** button to view predictions for customers in North America.</span></span>  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a><span data-ttu-id="dc168-151">カスタム式を使用した確率の追加</span><span class="sxs-lookup"><span data-stu-id="dc168-151">Adding Probabilities by Using a Custom Expression</span></span>  
 <span data-ttu-id="dc168-152">確率は予測の属性であり、入れ子になったテーブルとして出力されるので、各予測の確率を出力するのはやや複雑です。</span><span class="sxs-lookup"><span data-stu-id="dc168-152">To output the probability for each prediction is slightly more complicated, because the probability is an attribute of the prediction and is output as a nested table.</span></span> <span data-ttu-id="dc168-153">データ マイニング拡張機能 (DMX) に慣れている場合は、入れ子になったテーブルに対する下位選択ステートメントを追加するようにクエリを簡単に変更できます。</span><span class="sxs-lookup"><span data-stu-id="dc168-153">If you are familiar with Data Mining Extensions (DMX), you can easily alter the query to add a sub-select statement on the nested table.</span></span> <span data-ttu-id="dc168-154">また、予測クエリ ビルダーでカスタム式を追加して下位選択ステートメントを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc168-154">However, you can also create a sub-select statement in the Prediction Query Builder by adding a custom expression.</span></span>  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a><span data-ttu-id="dc168-155">カスタム式を使用して予測されたシーケンスの確率を出力するには</span><span class="sxs-lookup"><span data-stu-id="dc168-155">To output probabilities for a predicted sequence by using a custom expression</span></span>  
  
1.  <span data-ttu-id="dc168-156">予測クエリビルダーの左上隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc168-156">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="dc168-157">グリッドの [**ソース**] で、新しい行をクリックし、[**カスタム式**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-157">In the grid, under **Source**, click a new row, and select **Custom Expression**.</span></span>  
  
3.  <span data-ttu-id="dc168-158">[**フィールド**] の下のボックスは空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="dc168-158">Leave the box under **Field** blank.</span></span>  
  
4.  <span data-ttu-id="dc168-159">[**別名**] に「」と入力 `t` します。</span><span class="sxs-lookup"><span data-stu-id="dc168-159">For **Alias**, type `t`.</span></span>  
  
5.  <span data-ttu-id="dc168-160">[**条件と引数**] ボックスに、次のコード例に示すように、完全なサブ選択ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="dc168-160">In the **Criteria/Argument** box, type the complete sub-select statement as shown in the following code sample.</span></span> <span data-ttu-id="dc168-161">必ず開始かっこと終了かっこも入力してください。</span><span class="sxs-lookup"><span data-stu-id="dc168-161">Be sure to include the starting and ending parentheses.</span></span>  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  <span data-ttu-id="dc168-162">[**結果**] ボタンをクリックすると、ヨーロッパの顧客の予測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-162">Click the **Result** button to view predictions for customers in Europe.</span></span>  
  
 <span data-ttu-id="dc168-163">結果に、2 つの入れ子になったテーブルが含まれるようになります。一方のテーブルには予測、もう一方のテーブルには予測の確率が示されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-163">The results now contain two nested tables, one with the prediction, and one with the probability for the prediction.</span></span> <span data-ttu-id="dc168-164">クエリが機能しない場合は、クエリ デザイン ビューに切り替えて、次のようなクエリ ステートメント全体を確認できます。</span><span class="sxs-lookup"><span data-stu-id="dc168-164">If the query does not work, you can switch to query design view and review the complete query statement, which should be as follows:</span></span>  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a><span data-ttu-id="dc168-165">結果の操作</span><span class="sxs-lookup"><span data-stu-id="dc168-165">Working with Results</span></span>  
 <span data-ttu-id="dc168-166">結果に多数の入れ子になったテーブルが含まれている場合は、結果をフラット化して見やすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="dc168-166">When there are many nested tables in the results, you might want to flatten the results for easier viewing.</span></span> <span data-ttu-id="dc168-167">そのためには、クエリを手動で変更し、`FLATTENED` キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc168-167">To do this, you can manually modify the query and add the `FLATTENED` keyword.</span></span>  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a><span data-ttu-id="dc168-168">予測クエリで入れ子になった行セットをフラット化するには</span><span class="sxs-lookup"><span data-stu-id="dc168-168">To flatten nested rowsets in a prediction query</span></span>  
  
1.  <span data-ttu-id="dc168-169">予測クエリビルダーの隅にある [**クエリ**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-169">Click the **Query** button in the corner of the Prediction Query Builder.</span></span>  
  
     <span data-ttu-id="dc168-170">グリッドが開いたペインに変わり、予測クエリ ビルダーで作成された DMX ステートメントを表示および変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="dc168-170">The grid changes to an open pane where you can view and modify the DMX statement that was created by the Prediction Query Builder.</span></span>  
  
2.  <span data-ttu-id="dc168-171">`SELECT` キーワードの後に、「`FLATTENED`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dc168-171">After the `SELECT` keyword, type `FLATTENED`.</span></span>  
  
     <span data-ttu-id="dc168-172">クエリの完全なテキストは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dc168-172">The complete text of the query should be similar to the following:</span></span>  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  <span data-ttu-id="dc168-173">予測クエリビルダーの上隅にある [**結果**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-173">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="dc168-174">クエリを手動で編集した後、デザイン ビューに戻ると変更は失われます。</span><span class="sxs-lookup"><span data-stu-id="dc168-174">After you have manually edited a query, you will not be able to switch back to Design view without losing the changes.</span></span> <span data-ttu-id="dc168-175">ただし、手動で作成した DMX ステートメントをテキスト ファイルに保存してからデザイン ビューに戻ることはできます。</span><span class="sxs-lookup"><span data-stu-id="dc168-175">You can, however, save the DMX statement that you created manually to a text file, and then change back to Design view.</span></span> <span data-ttu-id="dc168-176">この場合、クエリはデザイン ビューで有効であった最後のバージョンに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc168-176">When you do so, the query is reverted to the last version that was valid in Design view.</span></span>  
  
## <a name="creating-predictions-on-the-related-model"></a><span data-ttu-id="dc168-177">関連モデルでの予測の作成</span><span class="sxs-lookup"><span data-stu-id="dc168-177">Creating Predictions on the Related Model</span></span>  
 <span data-ttu-id="dc168-178">ここまでの例では、モデルで地域間の違いが見られたかどうかを確認するために、ケース テーブル列 [地域] を単一予測クエリへの入力として使用しました。</span><span class="sxs-lookup"><span data-stu-id="dc168-178">The previous examples used a case table column, Region, as the input to the singleton prediction query, because you were interested in knowing whether the model had found any differences between regions.</span></span> <span data-ttu-id="dc168-179">ただし、モデルの調査後に、その違いは地域ごとに製品の提案をカスタマイズするほど顕著なものではないと判断しました。</span><span class="sxs-lookup"><span data-stu-id="dc168-179">However, after exploring the model, you decided that the differences are not strong enough to justify customizing product recommendations by region.</span></span> <span data-ttu-id="dc168-180">実際に予測する必要があるのは顧客が選択するアイテムです。</span><span class="sxs-lookup"><span data-stu-id="dc168-180">What you are really interested in predicting is the items that customers select.</span></span> <span data-ttu-id="dc168-181">したがって、次のクエリでは、地域を含まないシーケンス クラスター モデルを使用して、すべての顧客に対する提案を生成します。</span><span class="sxs-lookup"><span data-stu-id="dc168-181">Therefore, in the queries that follow, you will use the sequence clustering model that does not include Region, to generate recommendations for all customers.</span></span>  
  
### <a name="using-nested-table-columns-as-input"></a><span data-ttu-id="dc168-182">入力としての入れ子になったテーブル列の使用</span><span class="sxs-lookup"><span data-stu-id="dc168-182">Using Nested Table Columns as Input</span></span>  
 <span data-ttu-id="dc168-183">まず、単一のアイテムを入力として受け取り、次に選択される可能性が高いアイテムを返す単一予測クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc168-183">First you will create a singleton prediction query that takes a single item as input and returns the next most likely item.</span></span> <span data-ttu-id="dc168-184">このような予測を得るには、入力値として入れ子になったテーブル列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc168-184">To get a prediction of this kind, you have to use a nested table column as the input value.</span></span> <span data-ttu-id="dc168-185">これは、予測する属性 "モデル" が入れ子になったテーブルの一部であるためです。</span><span class="sxs-lookup"><span data-stu-id="dc168-185">This is because the attribute that you are predicting, Model, is part of a nested table.</span></span> <span data-ttu-id="dc168-186">Analysis Services には、入れ子になったテーブルの属性に対する予測クエリを簡単に作成できるように、[**入れ子になったテーブルの入力**] ダイアログボックスが用意されています。予測クエリビルダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc168-186">Analysis Services provides the **Nested Table Input** dialog box to help you easily create prediction queries on nested table attributes, by using the Prediction Query Builder.</span></span>  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a><span data-ttu-id="dc168-187">入れ子になったテーブルを予測への入力として使用するには</span><span class="sxs-lookup"><span data-stu-id="dc168-187">To use a nested table as input to a prediction</span></span>  
  
1.  <span data-ttu-id="dc168-188">予測クエリビルダーの左上隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc168-188">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="dc168-189">[**単一クエリ入力**] ダイアログボックスで、の [**値**] ボックスをクリックし、空の行を選択して、 `Region` このフィールドの入力をクリアします。</span><span class="sxs-lookup"><span data-stu-id="dc168-189">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select the empty row to clear the input for this field.</span></span>  
  
3.  <span data-ttu-id="dc168-190">[**単一クエリ入力**] ダイアログボックスで、の [**値**] ボックスをクリックし、[... `vAssocSeqLineItems` ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-190">In the **Singleton Query Input** dialog box, click the **Value** box for `vAssocSeqLineItems`, and then click the (...) button.</span></span>  
  
4.  <span data-ttu-id="dc168-191">[**入れ子になったテーブルの入力**] ダイアログボックスで、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-191">In the **Nested Table Input** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="dc168-192">新しい行で、の下のボックスをクリックし、 `Model` 一覧から [ツーリング Tire] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-192">In the new row, click the box under `Model`, and select Touring Tire from the list.</span></span> <span data-ttu-id="dc168-193">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-193">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="dc168-194">[**結果**] ボタンをクリックすると、予測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-194">Click the **Result** button to view the predictions.</span></span>  
  
 <span data-ttu-id="dc168-195">最初のアイテムとして Touring Tire を選択したすべての顧客に、次のアイテムとして以下のものがモデルによって提案されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-195">The model recommends the following next items for all customers who choose the Touring Tire as the first item.</span></span> <span data-ttu-id="dc168-196">モデルの調査によって、顧客が Touring Tire 製品と Touring Tire Tube 製品を一緒に購入することが多いとわかっているので、この提案は適切です。</span><span class="sxs-lookup"><span data-stu-id="dc168-196">You already know from exploring the model that customers frequently purchase the products Touring Tire and Touring Tire Tube together, so these recommendations look good.</span></span>  
  
|<span data-ttu-id="dc168-197">$SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="dc168-197">$SEQUENCE</span></span>|<span data-ttu-id="dc168-198">Line Number</span><span class="sxs-lookup"><span data-stu-id="dc168-198">Line Number</span></span>|<span data-ttu-id="dc168-199">モデル</span><span class="sxs-lookup"><span data-stu-id="dc168-199">Model</span></span>|  
|---------------|-----------------|-----------|  
|<span data-ttu-id="dc168-200">1</span><span class="sxs-lookup"><span data-stu-id="dc168-200">1</span></span>||<span data-ttu-id="dc168-201">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="dc168-201">Touring Tire Tube</span></span>|  
|<span data-ttu-id="dc168-202">2</span><span class="sxs-lookup"><span data-stu-id="dc168-202">2</span></span>||<span data-ttu-id="dc168-203">Sport-100</span><span class="sxs-lookup"><span data-stu-id="dc168-203">Sport-100</span></span>|  
|<span data-ttu-id="dc168-204">3</span><span class="sxs-lookup"><span data-stu-id="dc168-204">3</span></span>||<span data-ttu-id="dc168-205">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="dc168-205">Long-Sleeve Logo Jersey</span></span>|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="dc168-206">入れ子になったテーブルの入力を使用する一括予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="dc168-206">Creating a Bulk Prediction Query using Nested Table Inputs</span></span>  
 <span data-ttu-id="dc168-207">提案に使用できる予測がモデルによって作成されることを確認したので、次は外部データ ソースにマップされる予測クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc168-207">Now that you are satisfied that the model creates the kind of predictions that you can use in making recommendations, you will create a prediction query that is mapped to an external data source.</span></span> <span data-ttu-id="dc168-208">そのデータ ソースは、現在の製品を表す値を提供します。</span><span class="sxs-lookup"><span data-stu-id="dc168-208">That data source will provide values representing current products.</span></span> <span data-ttu-id="dc168-209">顧客 ID と製品一覧を入力として提供する予測クエリを作成することが目的であるため、ケース テーブルとして顧客テーブルを、入れ子になったテーブルとして購入記録テーブルをそれぞれ追加します。</span><span class="sxs-lookup"><span data-stu-id="dc168-209">Because you are interested in creating a prediction query that provides Customer ID and a list of products as input, you will add the customer table as the case table, and the purchases table as the nested table.</span></span> <span data-ttu-id="dc168-210">その後、提案を作成したときと同様に予測関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="dc168-210">Then you will add prediction functions as you did previously to create recommendations.</span></span>  
  
 <span data-ttu-id="dc168-211">この手順は、レッスン 3 でマーケット バスケット シナリオ用の予測を作成したときと同じ手順です。ただし、シーケンス クラスター モデルの予測では、入力として注文も必要になります。</span><span class="sxs-lookup"><span data-stu-id="dc168-211">This is the same procedure that you use to create predictions for the market basket scenario in Lesson 3; however, in a sequence clustering model predictions also need the order as input.</span></span>  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="dc168-212">入れ子になったテーブルの入力を使用する予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="dc168-212">To create a prediction query using nested table inputs</span></span>  
  
1.  <span data-ttu-id="dc168-213">[**マイニングモデル**] ペインで、シーケンスクラスターモデルを選択します (まだ選択されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="dc168-213">In the **Mining Model** pane, select the Sequence Clustering model, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="dc168-214">[**入力テーブルの選択**] ダイアログボックスで、[**ケーステーブルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-214">In the **Select Input Table(s)** dialog box, click **Select Case Table**.</span></span>  
  
3.  <span data-ttu-id="dc168-215">**[テーブルの選択**] ダイアログボックスの [データソース] で、[注文] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-215">In the **Select Table** dialog box, for Data Source, select Orders.</span></span> <span data-ttu-id="dc168-216">[**テーブル名またはビュー名**] ボックスの一覧で [vAssocSeqOrders] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-216">In the **Table/View Name** list, select vAssocSeqOrders, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="dc168-217">[**入力テーブルの選択**] ダイアログボックスで、[**入れ子になったテーブルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-217">In the **Select Input Table(s)** dialog box, click **Select Nested Table**.</span></span>  
  
5.  <span data-ttu-id="dc168-218">**[テーブルの選択**] ダイアログボックスの [**データソース**] で、[注文] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-218">In the **Select Table** dialog box, for **Data Source**, select Orders.</span></span> <span data-ttu-id="dc168-219">[**テーブル名またはビュー名**] ボックスの一覧で [vAssocSeqLineItems] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc168-219">In the **Table/View name** list, select vAssocSeqLineItems, and then click **OK**.</span></span>  
  
     <span data-ttu-id="dc168-220">Analysis Services でリレーションシップの検出が試行され、データ型が一致して列名が類似している場合は、リレーションシップが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-220">Analysis Services will try to detect relationships and create them automatically if the data types match and the column names are similar.</span></span> <span data-ttu-id="dc168-221">作成したリレーションシップが正しくない場合は、結合線を右クリックし、[**接続の変更**] を選択して列マッピングを編集するか、結合線を右クリックして [**削除**] を選択すると、リレーションシップが完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-221">If the relationships that it creates are wrong, you can right-click the join line and select **Modify Connections** to edit the column mapping, or you can right-click the join line and select **Delete** to remove the relationship completely.</span></span> <span data-ttu-id="dc168-222">この場合、テーブルがデータ ソース ビューで既に結合されているため、これらのリレーションシップはデザイン ペインに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-222">In this case, because the tables were already joined in the data source view, those relationships are automatically added to the design pane.</span></span>  
  
6.  <span data-ttu-id="dc168-223">グリッドに新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="dc168-223">Add a new row to the grid.</span></span> <span data-ttu-id="dc168-224">[**ソース**] で [vAssocSeqOrders] を選択し、[**フィールド**] で [顧客キー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-224">For **Source**, select vAssocSeqOrders, and for **Field**, select CustomerKey.</span></span>  
  
7.  <span data-ttu-id="dc168-225">グリッドに新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="dc168-225">Add a new row to the grid.</span></span> <span data-ttu-id="dc168-226">[**ソース**] で [**予測関数**] を選択し、[**フィールド**] で [ **PredictSequence**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc168-226">For **Source**, select **Prediction Function**, and for **Field**, select **PredictSequence**.</span></span>  
  
8.  <span data-ttu-id="dc168-227">VAssocSeqLineItems を [**条件と引数**] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="dc168-227">Drag vAssocSeqLineItems, into the **Criteria/Argument** box.</span></span> <span data-ttu-id="dc168-228">[**条件と引数**] ボックスの末尾をクリックし、次の引数を入力します `2` 。</span><span class="sxs-lookup"><span data-stu-id="dc168-228">Click at the end of the **Criteria/Argument** box and then type the following arguments: `2`.</span></span>  
  
     <span data-ttu-id="dc168-229">[**条件と引数**] ボックスの完全なテキストは次のようになります。`[Sequence Clustering].[v Assoc Seq Line Items],2`</span><span class="sxs-lookup"><span data-stu-id="dc168-229">The complete text in the **Criteria/Argument** box should be: `[Sequence Clustering].[v Assoc Seq Line Items],2`</span></span>  
  
9. <span data-ttu-id="dc168-230">[**結果**] ボタンをクリックすると、各顧客の予測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc168-230">Click the **Result** button to view the predictions for each customer.</span></span>  
  
 <span data-ttu-id="dc168-231">これで、シーケンス クラスター モデルのチュートリアルは完了です。</span><span class="sxs-lookup"><span data-stu-id="dc168-231">You have completed the tutorial on sequence clustering models.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="dc168-232">次の手順</span><span class="sxs-lookup"><span data-stu-id="dc168-232">Next Steps</span></span>  
 <span data-ttu-id="dc168-233">「中級者向け[データマイニングチュートリアル &#40;Analysis Services データ&#41;マイニングのチュートリアル](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」に記載されているすべてのセクションを完了している場合は、次の手順として、データマイニング拡張機能 (DMX) ステートメントを使用してモデルを作成し、予測を生成する方法について学習することができます。</span><span class="sxs-lookup"><span data-stu-id="dc168-233">If you have finished all the sections in the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md), the next step might be to learn to use Data Mining Extensions (DMX) statements to build models and generate predictions.</span></span> <span data-ttu-id="dc168-234">詳細については、「 [DMX を使用したデータマイニングモデルの作成とクエリ: チュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc168-234">For more information, see [Creating and Querying Data Mining Models with DMX: Tutorials &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).</span></span>  
  
 <span data-ttu-id="dc168-235">プログラミングの概念について理解している場合は、分析管理オブジェクト (AMO) を使用してデータ マイニング オブジェクトをプログラムで操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc168-235">If you are familiar with programming concepts, you can also use Analysis Management Objects (AMO) to programmatically work with data mining objects.</span></span> <span data-ttu-id="dc168-236">詳細については、「 [AMO データ マイニング クラス](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc168-236">For more information, see [AMO Data Mining Classes](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc168-237">参照</span><span class="sxs-lookup"><span data-stu-id="dc168-237">See Also</span></span>  
 <span data-ttu-id="dc168-238">[シーケンスクラスターモデルのクエリ例](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="dc168-238">[Sequence Clustering Model Query Examples](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="dc168-239">シーケンス クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="dc168-239">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
