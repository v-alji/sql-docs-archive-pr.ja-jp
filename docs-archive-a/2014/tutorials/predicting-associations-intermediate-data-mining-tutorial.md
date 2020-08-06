---
title: アソシエーションの予測 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9140c5f2-b340-45a6-9c27-d870d15aafea
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bee5ca4ded1b2fd5cbda0712cb766c825b9d0318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631414"
---
# <a name="predicting-associations-intermediate-data-mining-tutorial"></a><span data-ttu-id="77055-102">アソシエーションの予測 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="77055-102">Predicting Associations (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="77055-103">モデルの処理が完了したら、モデルに格納されているアソシエーションに関する情報を使用して予測を作成できます。</span><span class="sxs-lookup"><span data-stu-id="77055-103">After the models have been processed, you can use the information about associations stored in the model to create predictions.</span></span> <span data-ttu-id="77055-104">このレッスンの最後の作業では、作成したアソシエーション モデルに対して予測クエリを作成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="77055-104">In the final task of this lesson, you learn how to build prediction queries against the association models that you created.</span></span> <span data-ttu-id="77055-105">このレッスンは、予測クエリ ビルダーの使用方法について理解していることを前提に、アソシエーション モデルに対する予測クエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="77055-105">This lesson assumes that you are familiar with how to use the Prediction Query Builder and want to learn how to build prediction queries against association models.</span></span> <span data-ttu-id="77055-106">予測クエリビルダーの使用方法の詳細については、「[データマイニングクエリインターフェイス](../../2014/analysis-services/data-mining/data-mining-query-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77055-106">For more information how to use Prediction Query Builder, see [Data Mining Query Interfaces](../../2014/analysis-services/data-mining/data-mining-query-tools.md).</span></span>  
  
## <a name="creating-a-singleton-prediction-query"></a><span data-ttu-id="77055-107">単一予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="77055-107">Creating a Singleton Prediction Query</span></span>  
 <span data-ttu-id="77055-108">アソシエーション モデルに対する予測クエリは、次のようなときに、非常に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="77055-108">Prediction queries on an association model can be very useful:</span></span>  
  
-   <span data-ttu-id="77055-109">以前の購入または関連する購入に基づいて、製品を顧客に勧める。</span><span class="sxs-lookup"><span data-stu-id="77055-109">Recommend items to a customer, based on prior or related purchases</span></span>  
  
-   <span data-ttu-id="77055-110">関連するイベントを検索する。</span><span class="sxs-lookup"><span data-stu-id="77055-110">Find related events.</span></span>  
  
-   <span data-ttu-id="77055-111">取引のセット内の、またはそれらにまたがる関係を識別する。</span><span class="sxs-lookup"><span data-stu-id="77055-111">Identify relationships in or across sets of transactions.</span></span>  
  
 <span data-ttu-id="77055-112">予測クエリを作成するには、まず使用するアソシエーション モデルを選択し、次に入力データを指定します。</span><span class="sxs-lookup"><span data-stu-id="77055-112">To build a prediction query, you first select the association model you want to use, and then you specify the input data.</span></span> <span data-ttu-id="77055-113">値の一覧などの外部データ ソースから入力を得ることも、単一クエリを作成して値を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="77055-113">Inputs can come from an external data source, such as a list of values, or you can build a singleton query and provide values as you go.</span></span>  
  
 <span data-ttu-id="77055-114">このシナリオでは、まずいくつかの単一予測クエリを作成して、予測がどのように機能するかについて確認します。</span><span class="sxs-lookup"><span data-stu-id="77055-114">For this scenario, you will first create some singleton prediction queries, to get an idea of how prediction works.</span></span> <span data-ttu-id="77055-115">次に、顧客の現在の購入状況に基づいて提案を行う場合に使用するバッチ予測用のクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="77055-115">Then you will create a query for batch predictions that you could use for making recommendations based on a customer's current purchases.</span></span>  
  
#### <a name="to-create-a-prediction-query-on-an-association-model"></a><span data-ttu-id="77055-116">アソシエーション モデルに対する予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="77055-116">To create a prediction query on an association model</span></span>  
  
1.  <span data-ttu-id="77055-117">データマイニングデザイナーの [**マイニングモデル予測**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-117">Click the **Mining Model Prediction** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="77055-118">[**マイニングモデル**] ペインで、[**モデルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-118">In the **Mining Model** pane, click **Select Model**.</span></span> <span data-ttu-id="77055-119">(適切なモデルが既に選択されている場合は、この手順と次の手順をスキップできます)。</span><span class="sxs-lookup"><span data-stu-id="77055-119">(You can skip this step and the next step if the correct model is already selected.)</span></span>  
  
3.  <span data-ttu-id="77055-120">**[マイニングモデルの選択**] ダイアログボックスで、マイニング構造の**関連付け**を表すノードを展開し、モデルの**関連付け**を選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-120">In the **Select Mining Model** dialog box, expand the node that represents the mining structure **Association**, and select the model **Association**.</span></span> <span data-ttu-id="77055-121">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="77055-122">ここでは、入力ペインは無視します。</span><span class="sxs-lookup"><span data-stu-id="77055-122">For now, you can ignore the input pane.</span></span>  
  
4.  <span data-ttu-id="77055-123">グリッドで、[**ソース**] の下の空のセルをクリックし、[予測関数] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="77055-123">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="77055-124">[**フィールド**] の下のセルで、を選択し `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-124">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
     <span data-ttu-id="77055-125">また、 **predict**関数を使用してアソシエーションを予測することもできます。</span><span class="sxs-lookup"><span data-stu-id="77055-125">You can also use the **Predict** function to predict associations.</span></span> <span data-ttu-id="77055-126">この場合、テーブル列を引数として受け取る、 **Predict**関数のバージョンを選択してください。</span><span class="sxs-lookup"><span data-stu-id="77055-126">If you do, be sure to choose the version of the **Predict** function that takes a table column as argument.</span></span>  
  
5.  <span data-ttu-id="77055-127">[**マイニングモデル**] ペインで、入れ子になったテーブルを選択し、グリッド内の `vAssocSeqLineItems` 関数の [**条件と引数**] ボックスにドラッグし `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-127">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span>  
  
     <span data-ttu-id="77055-128">テーブル名と列名をドラッグ アンド ドロップすると、構文エラーを発生させずに複雑なステートメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="77055-128">Dragging and dropping table and column names lets you build complex statements without syntax errors.</span></span> <span data-ttu-id="77055-129">ただし、これにより、セルの現在の内容が置き換えられます。これには、関数の他の省略可能な引数が含まれ `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-129">However, it replaces the current contents of the cell, which include other optional arguments for the `PredictAssociation` function.</span></span> <span data-ttu-id="77055-130">その他の引数を表示するには、関数の 2 番目のインスタンスを参照用として一時的にグリッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="77055-130">To view the other arguments, you can temporarily add a second instance of the function to the grid for reference.</span></span>  
  
6.  <span data-ttu-id="77055-131">[**条件と引数**] ボックスをクリックし、テーブル名の後に次のテキストを入力します。`,3`</span><span class="sxs-lookup"><span data-stu-id="77055-131">Click the **Criteria/Argument** box and type the following text after the table name: `,3`</span></span>  
  
     <span data-ttu-id="77055-132">[**条件と引数**] ボックスの完全なテキストは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="77055-132">The complete text in the **Criteria/Argument** box should be as follows:</span></span>  
  
     `[Association].[v Assoc Seq Line Items],3`  
  
7.  <span data-ttu-id="77055-133">予測クエリビルダーの上隅にある [**結果**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-133">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="77055-134">期待される結果には、見出し**式**を含む1つの列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="77055-134">The expected results contain a single column with the heading **Expression**.</span></span> <span data-ttu-id="77055-135">[**式**] 列には、1つの列と次の3つの行を含む入れ子になったテーブルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="77055-135">The **Expression** column contains a nested table with a single column and the following three rows.</span></span> <span data-ttu-id="77055-136">入力値を指定していないため、これらの予測は、モデル全体で最も可能性の高い製品のアソシエーションを表します。</span><span class="sxs-lookup"><span data-stu-id="77055-136">Because you did not specify an input value, these predictions represent the most likely product associations for the model as a whole.</span></span>  
  
|<span data-ttu-id="77055-137">モデル</span><span class="sxs-lookup"><span data-stu-id="77055-137">Model</span></span>|  
|-----------|  
|<span data-ttu-id="77055-138">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="77055-138">Women's Mountain Shorts</span></span>|  
|<span data-ttu-id="77055-139">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="77055-139">Water Bottle</span></span>|  
|<span data-ttu-id="77055-140">Touring-3000</span><span class="sxs-lookup"><span data-stu-id="77055-140">Touring-3000</span></span>|  
  
 <span data-ttu-id="77055-141">次に、[**単一クエリ入力**] ペインを使用してクエリへの入力として製品を指定し、そのアイテムに関連付けられている可能性が最も高い製品を表示します。</span><span class="sxs-lookup"><span data-stu-id="77055-141">Next, you will use the **Singleton Query Input** pane to specify a product as input to the query, and view the products that are most likely associated with that item.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query-with-nested-table-inputs"></a><span data-ttu-id="77055-142">入れ子になったテーブルの入力を使用する単一予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="77055-142">To create a singleton prediction query with nested table inputs</span></span>  
  
1.  <span data-ttu-id="77055-143">予測クエリビルダーの隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。</span><span class="sxs-lookup"><span data-stu-id="77055-143">Click the **Design** button in the corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="77055-144">[**マイニングモデル**] メニューの [**単一クエリ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-144">On the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
3.  <span data-ttu-id="77055-145">[**マイニングモデル**] ダイアログボックスで、**アソシエーション**モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-145">In the **Mining Model** dialog box, select the **Association** model.</span></span>  
  
4.  <span data-ttu-id="77055-146">グリッドで、[**ソース**] の下の空のセルをクリックし、[予測関数] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="77055-146">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="77055-147">[**フィールド**] の下のセルで、を選択し `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-147">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
5.  <span data-ttu-id="77055-148">[**マイニングモデル**] ペインで、入れ子になったテーブルを選択し、グリッド内の `vAssocSeqLineItems` 関数の [**条件と引数**] ボックスにドラッグし `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-148">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span> <span data-ttu-id="77055-149">`,3`前の手順と同様に、入れ子になったテーブル名の後に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="77055-149">Type `,3` after the nested table name just as in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="77055-150">[**単一クエリ入力**] ダイアログボックスで、[ **vassoc Seq 行項目**] の横にある [**値**] ボックスをクリックし、[ **..** .] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-150">In the **Singleton Query Input** dialog box, click the **Value** box next to **vAssoc Seq Line Items**, and then click the **(...)** button.</span></span>  
  
7.  <span data-ttu-id="77055-151">[**入れ子になったテーブルの入力**] ダイアログボックスの [ `Touring Tire` **キー列**] ペインでを選択し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-151">In the **Nested Table Input** dialog box, select `Touring Tire` in the **Key column** pane, and then click **Add**.</span></span>  
  
8.  <span data-ttu-id="77055-152">[**結果**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-152">Click the **Results** button.</span></span>  
  
 <span data-ttu-id="77055-153">Touring Tire との関連が最も高い製品の予測が結果として表示されます。</span><span class="sxs-lookup"><span data-stu-id="77055-153">The results now show the predictions for products that are most likely associated with the Touring Tire.</span></span>  
  
|<span data-ttu-id="77055-154">モデル</span><span class="sxs-lookup"><span data-stu-id="77055-154">Model</span></span>|  
|-----------|  
|<span data-ttu-id="77055-155">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="77055-155">Touring Tire Tube</span></span>|  
|<span data-ttu-id="77055-156">Sport-100</span><span class="sxs-lookup"><span data-stu-id="77055-156">Sport-100</span></span>|  
|<span data-ttu-id="77055-157">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="77055-157">Water Bottle</span></span>|  
  
 <span data-ttu-id="77055-158">ただし、Touring Tire Tube が Touring Tire と一緒に購入されることが多いのは、モデルの調査から既にわかっています。それよりも関心があるのは、これらの製品を同時に購入した顧客にどの製品を提案できるかということです。</span><span class="sxs-lookup"><span data-stu-id="77055-158">However, you already know from exploring the model that the Touring Tire Tube is frequently purchased with the Touring Tire; you are more interested in knowing what products you can recommend to customers who purchase these items together.</span></span> <span data-ttu-id="77055-159">買い物かごに入っている 2 つの商品を基に関連する製品を予測するように、クエリを変更します。</span><span class="sxs-lookup"><span data-stu-id="77055-159">You will change the query so that it predicts related products based on two items in the basket.</span></span> <span data-ttu-id="77055-160">また、予測された製品ごとに確率を追加するようにクエリを変更します。</span><span class="sxs-lookup"><span data-stu-id="77055-160">You will also modify the query to add the probability for each predicted product.</span></span>  
  
#### <a name="to-add-inputs-and-probabilities-to-the-singleton-prediction-query"></a><span data-ttu-id="77055-161">単一予測クエリに入力と確率を追加するには</span><span class="sxs-lookup"><span data-stu-id="77055-161">To add inputs and probabilities to the singleton prediction query</span></span>  
  
1.  <span data-ttu-id="77055-162">予測クエリビルダーの隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。</span><span class="sxs-lookup"><span data-stu-id="77055-162">Click the **Design** button in the corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="77055-163">[**単一クエリ入力**] ダイアログボックスで、[ **vassoc Seq 行項目**] の横にある [**値**] ボックスをクリックし、[ **..** .] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-163">In the **Singleton Query Input** dialog box, click the **Value** box next to **vAssoc Seq Line Items**, and then click the **(...)** button.</span></span>  
  
3.  <span data-ttu-id="77055-164">[**キー列**] ペインで、[] を選択し、 `Touring Tire` [**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-164">In the **Key column** pane, select `Touring Tire`, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="77055-165">グリッドで、[**ソース**] の下の空のセルをクリックし、[予測関数] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="77055-165">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="77055-166">[**フィールド**] の下のセルで、を選択し `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-166">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
5.  <span data-ttu-id="77055-167">[**マイニングモデル**] ペインで、入れ子になったテーブルを選択し、グリッド内の `vAssocSeqLineItems` 関数の [**条件と引数**] ボックスにドラッグし `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-167">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span> <span data-ttu-id="77055-168">`,3`前の手順と同様に、入れ子になったテーブル名の後に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="77055-168">Type `,3` after the nested table name just as in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="77055-169">[**入れ子になったテーブルの入力**] ダイアログボックスの [ `Touring Tire Tube` **キー列**] ペインでを選択し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-169">In the **Nested Table Input** dialog box, select `Touring Tire Tube` in the **Key column** pane, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="77055-170">グリッドで、関数の行の `PredictAssociation` [**条件と引数**] ボックスをクリックし、引数を変更して引数を追加し INCLUDE_STATISTICS します。</span><span class="sxs-lookup"><span data-stu-id="77055-170">In the grid, in the row for the `PredictAssociation` function, click the **Criteria/Argument** box, and change the arguments to add the argument, INCLUDE_STATISTICS.</span></span>  
  
     <span data-ttu-id="77055-171">[**条件と引数**] ボックスの完全なテキストは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="77055-171">The complete text in the **Criteria/Argument** box should be as follows:</span></span>  
  
     `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
8.  <span data-ttu-id="77055-172">[**結果**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-172">Click the **Results** button.</span></span>  
  
 <span data-ttu-id="77055-173">入れ子になったテーブル内の結果が変更され、予測がサポートおよび確率と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="77055-173">The results in the nested table now change to show the predictions, together with support and probability.</span></span> <span data-ttu-id="77055-174">これらの値を解釈する方法の詳細については、「 [&#40;Analysis Services データマイニング&#41;のアソシエーションモデルのマイニングモデルコンテンツ](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77055-174">For more information about how to interpret these values, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
|<span data-ttu-id="77055-175">モデル</span><span class="sxs-lookup"><span data-stu-id="77055-175">Model</span></span>|<span data-ttu-id="77055-176">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="77055-176">$SUPPORT</span></span>|<span data-ttu-id="77055-177">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="77055-177">$PROBABILITY</span></span>|<span data-ttu-id="77055-178">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="77055-178">$ADJUSTEDPROBABILITY</span></span>|  
|-----------|--------------|------------------|--------------------------|  
|<span data-ttu-id="77055-179">Sport-100</span><span class="sxs-lookup"><span data-stu-id="77055-179">Sport-100</span></span>|<span data-ttu-id="77055-180">4334</span><span class="sxs-lookup"><span data-stu-id="77055-180">4334</span></span>|<span data-ttu-id="77055-181">0.291...</span><span class="sxs-lookup"><span data-stu-id="77055-181">0.291...</span></span>|<span data-ttu-id="77055-182">0.252...</span><span class="sxs-lookup"><span data-stu-id="77055-182">0.252...</span></span>|  
|<span data-ttu-id="77055-183">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="77055-183">Water Bottle</span></span>|<span data-ttu-id="77055-184">2866</span><span class="sxs-lookup"><span data-stu-id="77055-184">2866</span></span>|<span data-ttu-id="77055-185">0.192...</span><span class="sxs-lookup"><span data-stu-id="77055-185">0.192...</span></span>|<span data-ttu-id="77055-186">0.175...</span><span class="sxs-lookup"><span data-stu-id="77055-186">0.175...</span></span>|  
|<span data-ttu-id="77055-187">Patch Kit</span><span class="sxs-lookup"><span data-stu-id="77055-187">Patch Kit</span></span>|<span data-ttu-id="77055-188">2113</span><span class="sxs-lookup"><span data-stu-id="77055-188">2113</span></span>|<span data-ttu-id="77055-189">0.142...</span><span class="sxs-lookup"><span data-stu-id="77055-189">0.142...</span></span>|<span data-ttu-id="77055-190">0.132</span><span class="sxs-lookup"><span data-stu-id="77055-190">0.132</span></span>|  
  
## <a name="working-with-results"></a><span data-ttu-id="77055-191">結果の操作</span><span class="sxs-lookup"><span data-stu-id="77055-191">Working with Results</span></span>  
 <span data-ttu-id="77055-192">結果に多数の入れ子になったテーブルが含まれている場合は、結果をフラット化して見やすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="77055-192">When there are many nested tables in the results, you might want to flatten the results for easier viewing.</span></span> <span data-ttu-id="77055-193">そのためには、クエリを手動で変更し、`FLATTENED` キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="77055-193">To do this, you can manually modify the query and add the `FLATTENED` keyword.</span></span>  
  
#### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a><span data-ttu-id="77055-194">予測クエリで入れ子になった行セットをフラット化するには</span><span class="sxs-lookup"><span data-stu-id="77055-194">To flatten nested rowsets in a prediction query</span></span>  
  
1.  <span data-ttu-id="77055-195">予測クエリビルダーの隅にある [ **SQL** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-195">Click the **SQL** button in the corner of the Prediction Query Builder.</span></span>  
  
     <span data-ttu-id="77055-196">グリッドが開いたペインに変わり、予測クエリ ビルダーで作成された DMX ステートメントを表示および変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="77055-196">The grid changes to an open pane where you can view and modify the DMX statement that was created by the Prediction Query Builder.</span></span>  
  
2.  <span data-ttu-id="77055-197">`SELECT` キーワードの後に、「`FLATTENED`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="77055-197">After the `SELECT` keyword, type `FLATTENED`.</span></span>  
  
     <span data-ttu-id="77055-198">クエリの全テキストは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="77055-198">The complete text of the query should be as follows:</span></span>  
  
    ```  
    SELECT FLATTENED  
      PredictAssociation([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,3)  
    FROM  
      [Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Touring Tire' AS [Model]  
      UNION SELECT 'Touring Tire Tube' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
    ```  
  
3.  <span data-ttu-id="77055-199">予測クエリビルダーの上隅にある [**結果**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-199">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="77055-200">クエリを手動で編集した後に [デザイン] ビューに戻ると、変更が失われることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="77055-200">Note that after you have manually edited a query, you will not be able to switch back to Design view without losing the changes.</span></span> <span data-ttu-id="77055-201">クエリを保存する場合は、手動で作成した DMX ステートメントをテキスト ファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="77055-201">If you wish to save the query, you can copy the DMX statement that you created manually to a text file.</span></span> <span data-ttu-id="77055-202">[デザイン] ビューに戻ると、クエリが [デザイン] ビューで有効であった最後のバージョンに戻ります。</span><span class="sxs-lookup"><span data-stu-id="77055-202">When you change back to Design view, the query is reverted to the last version that was valid in Design view.</span></span>  
  
## <a name="creating-multiple-predictions"></a><span data-ttu-id="77055-203">複数の予測の作成</span><span class="sxs-lookup"><span data-stu-id="77055-203">Creating Multiple Predictions</span></span>  
 <span data-ttu-id="77055-204">過去の購入記録を基に、各顧客に対して最も精度の高い予測を作成するとします。</span><span class="sxs-lookup"><span data-stu-id="77055-204">Suppose you want to know the best predictions for individual customers, based on past purchases.</span></span> <span data-ttu-id="77055-205">予測クエリには、顧客 ID と最近購入した製品が記録されているテーブルなどの外部データを入力として使用できます。</span><span class="sxs-lookup"><span data-stu-id="77055-205">You can use external data as input to the prediction query, such as tables containing the customer ID and the most recent product purchases.</span></span> <span data-ttu-id="77055-206">その場合は、データ テーブルが Analysis Services データ ソース ビューとして既に定義されていることが条件となります。さらにモデルで使用されているものと同様のケース テーブルと入れ子になったテーブルが入力データに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="77055-206">The requirements are that the data tables be already defined as an Analysis Services data source view; moreover, the input data must contain case and nested tables like those used in the model.</span></span> <span data-ttu-id="77055-207">テーブル名が同じである必要はありませんが、構造は類似している必要があります。</span><span class="sxs-lookup"><span data-stu-id="77055-207">They need not have the same names, but the structure must be similar.</span></span> <span data-ttu-id="77055-208">このチュートリアルでは、モデルのトレーニングが行われた元のテーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="77055-208">For the purpose of this tutorial, you will use the original tables on which the model was trained.</span></span>  
  
#### <a name="to-change-the-input-method-for-the-prediction-query"></a><span data-ttu-id="77055-209">予測クエリの入力方法を変更するには</span><span class="sxs-lookup"><span data-stu-id="77055-209">To change the input method for the prediction query</span></span>  
  
1.  <span data-ttu-id="77055-210">[**マイニングモデル**] メニューで、[**単一クエリ**] をもう一度選択してチェックマークをオフにします。</span><span class="sxs-lookup"><span data-stu-id="77055-210">In the **Mining Model** menu, select **Singleton Query** again, to clear the check mark.</span></span>  
  
2.  <span data-ttu-id="77055-211">単一クエリが失われることを警告するエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="77055-211">An error message appears warning that your singleton query will be lost.</span></span> <span data-ttu-id="77055-212">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-212">Click **Yes**.</span></span>  
  
     <span data-ttu-id="77055-213">入力ダイアログボックスの名前が **[入力テーブルの選択**] に変わります。</span><span class="sxs-lookup"><span data-stu-id="77055-213">The name of the input dialog box changes to **Select Input Table(s)**.</span></span>  
  
 <span data-ttu-id="77055-214">顧客 ID と製品一覧を入力として提供する予測クエリを作成することが目的であるため、ケース テーブルとして顧客テーブルを、入れ子になったテーブルとして購入記録テーブルをそれぞれ追加します。</span><span class="sxs-lookup"><span data-stu-id="77055-214">Because you are interested in creating a prediction query that provides Customer ID and a list of products as input, you will add the customer table as the case table, and the purchases table as the nested table.</span></span> <span data-ttu-id="77055-215">その後に、提案を作成するための予測関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="77055-215">Then you will add prediction functions to create recommendations.</span></span>  
  
#### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="77055-216">入れ子になったテーブルの入力を使用する予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="77055-216">To create a prediction query using nested table inputs</span></span>  
  
1.  <span data-ttu-id="77055-217">[マイニング モデル] ペインで、[Association Filtered] モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-217">In the Mining Model pane, select the Association Filtered model.</span></span>  
  
2.  <span data-ttu-id="77055-218">[**入力テーブルの選択**] ダイアログボックスで、[**ケーステーブルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-218">In the **Select Input Table(s)** dialog box, click **Select Case Table**.</span></span>  
  
3.  <span data-ttu-id="77055-219">**[テーブルの選択**] ダイアログボックスの [**データソース**] で、[AdventureWorksDW2008] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-219">In the **Select Table** dialog box, for **Data Source**, select AdventureWorksDW2008.</span></span> <span data-ttu-id="77055-220">[**テーブル名またはビュー名**] ボックスの一覧で [vAssocSeqOrders] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-220">In the **Table/View Name** list, select vAssocSeqOrders, and then click **OK**.</span></span>  
  
     <span data-ttu-id="77055-221">テーブル vAssocSeqOrders がペインに追加されます。</span><span class="sxs-lookup"><span data-stu-id="77055-221">The table vAssocSeqOrders is added to the pane.</span></span>  
  
4.  <span data-ttu-id="77055-222">[**入力テーブルの選択**] ダイアログボックスで、[**入れ子になったテーブルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-222">In the **Select Input Table(s)** dialog box, click **Select Nested Table**.</span></span>  
  
5.  <span data-ttu-id="77055-223">**[テーブルの選択**] ダイアログボックスの [**データソース**] で、[AdventureWorksDW2008] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-223">In the **Select Table** dialog box, for **Data Source**, select AdventureWorksDW2008.</span></span> <span data-ttu-id="77055-224">[**テーブル名またはビュー名**] ボックスの一覧で [vAssocSeqLineItems] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-224">In the **Table/View name** list, select vAssocSeqLineItems, and then click **OK**.</span></span>  
  
     <span data-ttu-id="77055-225">テーブル vAssocSeqLineItems がペインに追加されます。</span><span class="sxs-lookup"><span data-stu-id="77055-225">The table vAssocSeqLineItems is added to the pane.</span></span>  
  
6.  <span data-ttu-id="77055-226">[**入れ子になった結合の指定**] ダイアログボックスで、ケーステーブルの [ordernumber] フィールドをドラッグし、入れ子になったテーブルの [ordernumber] フィールドにドロップします。</span><span class="sxs-lookup"><span data-stu-id="77055-226">In the **Specify Nested Join** dialog box, drag the OrderNumber field from the case table and drop it onto the OrderNumber field in the nested table.</span></span>  
  
     <span data-ttu-id="77055-227">[**リレーションシップの追加**] をクリックして、一覧から列を選択してリレーションシップを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="77055-227">You can also click **Add Relationship** and create the relationship by selecting columns from a list.</span></span>  
  
7.  <span data-ttu-id="77055-228">[**リレーションシップの指定**] ダイアログボックスで、[ordernumber] フィールドが正しくマップされていることを確認し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77055-228">In the **Specify Relationship** dialog box, verify that the OrderNumber fields are mapped correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="77055-229">[ **OK** ] をクリックして [**入れ子になった結合の指定**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="77055-229">Click **OK** to close the **Specify Nested Join** dialog box.</span></span>  
  
     <span data-ttu-id="77055-230">ケース テーブルと入れ子になったテーブルがデザイン ペインで更新され、外部データの列とモデル内の列を結ぶ結合が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77055-230">The case and nested tables are updated in the design pane to show the joins connecting the external data columns to the columns in the model.</span></span> <span data-ttu-id="77055-231">リレーションシップが正しくない場合は、結合線を右クリックし、[**接続の変更**] を選択して列マッピングを編集するか、結合線を右クリックして [**削除**] を選択すると、リレーションシップが完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="77055-231">If the relationships are wrong, you can right-click the join line and select **Modify Connections** to edit the column mapping, or you can right-click the join line and select **Delete** to remove the relationship completely.</span></span>  
  
9. <span data-ttu-id="77055-232">グリッドに新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="77055-232">Add a new row to the grid.</span></span> <span data-ttu-id="77055-233">[**ソース**] で、[ **vAssocSeqOrders table**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-233">For **Source**, select **vAssocSeqOrders table**.</span></span> <span data-ttu-id="77055-234">[**フィールド**] で [顧客キー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-234">For **Field**, select CustomerKey.</span></span>  
  
10. <span data-ttu-id="77055-235">グリッドに新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="77055-235">Add a new row to the grid.</span></span> <span data-ttu-id="77055-236">[**ソース**] で、[ **vAssocSeqOrders table**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-236">For **Source**, select **vAssocSeqOrders table**.</span></span> <span data-ttu-id="77055-237">[**フィールド**] で [Region] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77055-237">For **Field**, select Region.</span></span>  
  
11. <span data-ttu-id="77055-238">グリッドに新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="77055-238">Add a new row to the grid.</span></span> <span data-ttu-id="77055-239">[**ソース**] で [**予測関数**] を選択し、[**フィールド**] でを選択し `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-239">For **Source**, select **Prediction Function**, and for **Field**, select `PredictAssociation`.</span></span>  
  
12. <span data-ttu-id="77055-240">VAssocSeqLineItems を行の [**条件と引数**] ボックスにドラッグし `PredictAssociation` ます。</span><span class="sxs-lookup"><span data-stu-id="77055-240">Drag vAssocSeqLineItems, into the **Criteria/Argument** box of the `PredictAssociation` row.</span></span> <span data-ttu-id="77055-241">[**条件と引数**] ボックスの末尾をクリックし、次のテキストを入力します。`INCLUDE_STATISTICS,3`</span><span class="sxs-lookup"><span data-stu-id="77055-241">Click at the end of the **Criteria/Argument** box and then type the following text: `INCLUDE_STATISTICS,3`</span></span>  
  
     <span data-ttu-id="77055-242">[**条件と引数**] ボックスの完全なテキストは次のようになります。`[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`</span><span class="sxs-lookup"><span data-stu-id="77055-242">The complete text in the **Criteria/Argument** box should be: `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`</span></span>  
  
13. <span data-ttu-id="77055-243">[**結果**] ボタンをクリックすると、各顧客の予測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77055-243">Click the **Result** button to view the predictions for each customer.</span></span>  
  
 <span data-ttu-id="77055-244">同様の予測クエリを複数のモデルに対して作成し、フィルター処理によって予測結果が変わるかどうかを確認してみてください。</span><span class="sxs-lookup"><span data-stu-id="77055-244">You might try creating a similar prediction query on the multiple models, to see whether filtering changes the prediction results.</span></span> <span data-ttu-id="77055-245">予測およびその他の種類のクエリの作成の詳細については、「[アソシエーションモデルのクエリ例](../../2014/analysis-services/data-mining/association-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77055-245">For more information about creating predictions and other types of queries, see [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77055-246">参照</span><span class="sxs-lookup"><span data-stu-id="77055-246">See Also</span></span>  
 <span data-ttu-id="77055-247">[アソシエーションモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="77055-247">[Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="77055-248">[DMX&#41;&#40;PredictAssociation](/sql/dmx/predictassociation-dmx) </span><span class="sxs-lookup"><span data-stu-id="77055-248">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) </span></span>  
 [<span data-ttu-id="77055-249">予測クエリ ビルダーを使用した予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="77055-249">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
