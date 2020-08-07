---
title: 'レッスン 5: 予測クエリの実行 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0037bd2f-aa2d-464b-bf86-b0210f0438b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5f4d6dd79f62541e207df688349f694680e2421
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719076"
---
# <a name="lesson-5-executing-prediction-queries"></a><span data-ttu-id="ec7d1-102">レッスン 5: 予測クエリの実行</span><span class="sxs-lookup"><span data-stu-id="ec7d1-102">Lesson 5: Executing Prediction Queries</span></span>
  <span data-ttu-id="ec7d1-103">このレッスンでは、SELECT ステートメントの[SELECT FROM \<model> 予測結合 (DMX)](/sql/dmx/select-from-model-cases-dmx)形式を使用して、「[レッスン 2: アソシエーションマイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)」で作成したデシジョンツリーモデルに基づいて、2つの異なる種類の予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-103">In this lesson, you will use the [SELECT FROM \<model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) form of the SELECT statement to create two different types of predictions based on the decision tree model you created in [Lesson 2: Adding Mining Models to the Association Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="ec7d1-104">作成する予測の種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-104">These prediction types are defined below.</span></span>  
  
 <span data-ttu-id="ec7d1-105">単一クエリ</span><span class="sxs-lookup"><span data-stu-id="ec7d1-105">Singleton Query</span></span>  
 <span data-ttu-id="ec7d1-106">予測を行う際にアドホック値を提供するには、単一クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-106">Use a singleton query to provide ad hoc values when making predictions.</span></span> <span data-ttu-id="ec7d1-107">たとえば、顧客の通勤距離、市外局番、または子供の数などをクエリに入力して、1 人の顧客が自転車を購入するかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-107">For example, you can determine whether a single customer is likely to be a bike buyer, by passing inputs to the query such as the commute distance, the area code, or the number of children of the customer.</span></span> <span data-ttu-id="ec7d1-108">単一クエリは、これらの入力に基づいてこの顧客が自転車を購入する可能性を示す値を返します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-108">The singleton query returns a value that indicates how likely the person is to purchase a bicycle based on those inputs.</span></span>  
  
 <span data-ttu-id="ec7d1-109">バッチ クエリ</span><span class="sxs-lookup"><span data-stu-id="ec7d1-109">Batch Query</span></span>  
 <span data-ttu-id="ec7d1-110">複数の潜在顧客が含まれるテーブルの中から、自転車を購入する可能性がある人物を特定するには、バッチ クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-110">Use a batch query to determine who in a table of potential customers is likely to purchase a bicycle.</span></span> <span data-ttu-id="ec7d1-111">たとえば、マーケティング部門から顧客と顧客の属性の一覧が提供された場合、バッチ予測を使用して、テーブルの中で自転車を購入する可能性が高い人物を特定できます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-111">For example, if your marketing department provides you with a list of customers and customer attributes, then you can use a batch prediction to determine who from the table is likely to purchase a bicycle.</span></span>  
  
 <span data-ttu-id="ec7d1-112">Select [FROM \<model> 予測結合 (DMX)](/sql/dmx/select-from-model-cases-dmx)形式の select ステートメントには、次の3つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-112">The [SELECT FROM \<model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) form of the SELECT statement contains three parts:</span></span>  
  
-   <span data-ttu-id="ec7d1-113">結果で返される、マイニング モデル列と予測関数の一覧。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-113">A list of the mining model columns and prediction functions that are returned in the results.</span></span> <span data-ttu-id="ec7d1-114">結果にはソース データからの入力列を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-114">The results can also contain input columns from the source data.</span></span>  
  
-   <span data-ttu-id="ec7d1-115">予測の作成に使用するデータを定義しているソース クエリ。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-115">The source query defining the data that is being used to create a prediction.</span></span> <span data-ttu-id="ec7d1-116">たとえば、バッチ クエリの場合は顧客の一覧などが該当します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-116">For example, in a batch query this could be a list of customers.</span></span>  
  
-   <span data-ttu-id="ec7d1-117">マイニング モデル列とソース データ間のマッピング。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-117">A mapping between the mining model columns and the source data.</span></span> <span data-ttu-id="ec7d1-118">これらの名前が同じ場合は、NATURAL 構文を使用して列マッピングを省略できます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-118">If these names match, then you can use NATURAL syntax and leave out the column mappings.</span></span>  
  
 <span data-ttu-id="ec7d1-119">予測関数を使用すると、さらにクエリを改良できます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-119">You can further enhance the query by using prediction functions.</span></span> <span data-ttu-id="ec7d1-120">予測関数では、予測が発生する可能性など追加の情報と、トレーニング データセットでの予測サポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-120">Prediction functions provide additional information, such as the probability of a prediction occurring, and provide support for the prediction in the training dataset.</span></span> <span data-ttu-id="ec7d1-121">予測関数の詳細については、「 [functions &#40;DMX&#41;](/sql/dmx/functions-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-121">For more information about prediction functions, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
 <span data-ttu-id="ec7d1-122">このチュートリアルの予測は、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプル データベースの ProspectiveBuyer テーブルに基づくものです。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-122">The predictions in this tutorial are based on the ProspectiveBuyer table in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database.</span></span> <span data-ttu-id="ec7d1-123">ProspectiveBuyer テーブルには、潜在顧客と、それらの顧客に関連付けられている特性の一覧が格納されています。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-123">The ProspectiveBuyer table contains a list of potential customers and their associated characteristics.</span></span> <span data-ttu-id="ec7d1-124">このテーブルに格納されている顧客は、デシジョン ツリー マイニング モデルの作成で使用した顧客とは異なります。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-124">The customers in this table are independent of the customers that were used to create the decision tree mining model.</span></span>  
  
 <span data-ttu-id="ec7d1-125">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] の予測クエリ ビルダーを使用して予測を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-125">You can also create predictions by using the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="ec7d1-126">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="ec7d1-126">Lesson Tasks</span></span>  
 <span data-ttu-id="ec7d1-127">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-127">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="ec7d1-128">特定の顧客が自転車を購入するかどうかを特定する単一クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-128">Create a singleton query to determine whether a specific customer is likely to purchase a bicycle.</span></span>  
  
-   <span data-ttu-id="ec7d1-129">複数の顧客が含まれるテーブルの中から、自転車を購入する可能性がある顧客を特定するバッチ クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-129">Create a batch query to determine which customers, listed in a table of customers, are likely to purchase a bicycle.</span></span>  
  
## <a name="singleton-query"></a><span data-ttu-id="ec7d1-130">単一クエリ</span><span class="sxs-lookup"><span data-stu-id="ec7d1-130">Singleton Query</span></span>  
 <span data-ttu-id="ec7d1-131">最初の手順では、 [SELECT FROM &#60;モデル&#62; 予測結合](/sql/dmx/select-from-model-cases-dmx)を使用して、単一予測クエリで DMX&#41;&#40;します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-131">The first step is to use the [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) in a singleton prediction query.</span></span> <span data-ttu-id="ec7d1-132">単一ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-132">The following is a generic example of the singleton statement:</span></span>  
  
```  
SELECT <select list> FROM [<mining model name>]   
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
```  
  
 <span data-ttu-id="ec7d1-133">コードの最初の行では、クエリで返されるマイニング モデルの列を定義し、予測の生成に使用するマイニング モデルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-133">The first line of the code defines the columns from the mining model that the query should return, and specifies the mining model that is used to generate the prediction:</span></span>  
  
```  
SELECT <select list> FROM [<mining model name>]   
```  
  
 <span data-ttu-id="ec7d1-134">コードの次の行では、予測の作成に使用する顧客の特性を定義します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-134">The next lines of the code define the characteristics of the customer that you use to create a prediction:</span></span>  
  
```  
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
ORDER BY <expression>  
```  
  
 <span data-ttu-id="ec7d1-135">NATURAL PREDICTION JOIN を指定した場合、サーバーでは、モデルの各列と入力された列が列名に基づいて照合されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-135">If you specify NATURAL PREDICTION JOIN, the server matches each column from the model to a column from the input, based on column names.</span></span> <span data-ttu-id="ec7d1-136">列名が一致しない場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-136">If column names do not match, the columns are ignored.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query"></a><span data-ttu-id="ec7d1-137">単一予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="ec7d1-137">To create a singleton prediction query</span></span>  
  
1.  <span data-ttu-id="ec7d1-138">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-138">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="ec7d1-139">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-139">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="ec7d1-140">上の単一ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-140">Copy the generic example of the singleton statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="ec7d1-141">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-141">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="ec7d1-142">with:</span><span class="sxs-lookup"><span data-stu-id="ec7d1-142">with:</span></span>  
  
    ```  
    [Bike Buyer] AS Buyer, PredictHistogram([Bike Buyer]) AS Statistics  
    ```  
  
     <span data-ttu-id="ec7d1-143">AS ステートメントは、クエリで返される列に別名を付けるために使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-143">The AS statement is used to alias columns returned by the query.</span></span> <span data-ttu-id="ec7d1-144">[PredictHistogram](/sql/dmx/predicthistogram-dmx)関数は、確率やサポートなど、予測に関する統計を返します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-144">The [PredictHistogram](/sql/dmx/predicthistogram-dmx) function returns statistics about the prediction, including the probability and the support.</span></span> <span data-ttu-id="ec7d1-145">予測ステートメントで使用できる関数の詳細については、「 [functions &#40;DMX&#41;](/sql/dmx/functions-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-145">For more information about the functions that can be used in a prediction statement, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
4.  <span data-ttu-id="ec7d1-146">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-146">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="ec7d1-147">with:</span><span class="sxs-lookup"><span data-stu-id="ec7d1-147">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="ec7d1-148">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-148">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column name>], ...)  AS t  
    ```  
  
     <span data-ttu-id="ec7d1-149">with:</span><span class="sxs-lookup"><span data-stu-id="ec7d1-149">with:</span></span>  
  
    ```  
    (SELECT 35 AS [Age],  
      '5-10 Miles' AS [Commute Distance],  
      '1' AS [House Owner Flag],  
      2 AS [Number Cars Owned],  
      2 AS [Total Children]) AS t  
    ```  
  
     <span data-ttu-id="ec7d1-150">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-150">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
       [Bike Buyer] AS Buyer,  
       PredictHistogram([Bike Buyer]) AS Statistics  
    FROM  
       [Decision Tree]  
    NATURAL PREDICTION JOIN  
    (SELECT 35 AS [Age],  
       '5-10 Miles' AS [Commute Distance],  
       '1' AS [House Owner Flag],  
       2 AS [Number Cars Owned],  
       2 AS [Total Children]) AS t  
    ```  
  
6.  <span data-ttu-id="ec7d1-151">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-151">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="ec7d1-152">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Singleton_Query.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-152">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Singleton_Query.dmx`.</span></span>  
  
8.  <span data-ttu-id="ec7d1-153">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-153">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="ec7d1-154">クエリが実行され、指定した特性の顧客が自転車を購入するかどうかの予測と、予測に関する統計が返されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-154">The query returns a prediction about whether a customer with the specified characteristics will purchase a bicycle, as well as statistics about that prediction.</span></span>  
  
## <a name="batch-query"></a><span data-ttu-id="ec7d1-155">バッチ クエリ</span><span class="sxs-lookup"><span data-stu-id="ec7d1-155">Batch Query</span></span>  
 <span data-ttu-id="ec7d1-156">次の手順では、 [SELECT FROM &#60;モデル&#62; 予測結合 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx)をバッチ予測クエリで使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-156">The next step is to use the [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) in a batch prediction query.</span></span> <span data-ttu-id="ec7d1-157">バッチ ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-157">The following is a generic example of a batch statement:</span></span>  
  
```  
SELECT TOP <number> <select list>   
FROM [<mining model name>]  
PREDICTION JOIN  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
ON <on clause, mapping,>  
WHERE <where clause, boolean expression,>  
ORDER BY <expression>  
```  
  
 <span data-ttu-id="ec7d1-158">単一クエリと同様に、コードの最初の 2 行では、クエリで返されるマイニング モデルの列と、予測の生成に使用するマイニング モデルの名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-158">As in the singleton query, the first two lines of the code define the columns from mining model that the query returns, as well as the name of the mining model that is used to generate the prediction.</span></span> <span data-ttu-id="ec7d1-159">TOP ステートメントは、 \<number> クエリがで指定された数値または結果のみを返すことを指定し \<number> ます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-159">The TOP \<number> statement specifies that the query will only return the number or the results specified by \<number>.</span></span>  
  
 <span data-ttu-id="ec7d1-160">コードの次の数行では、予測の基になるソース データを定義します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-160">The next lines of the code define the source data that the predictions are based on:</span></span>  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
```  
  
 <span data-ttu-id="ec7d1-161">ソース データを取得するにはいくつかの方法がありますが、このチュートリアルでは OPENQUERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-161">You have several options for the method of retrieving the source data, but in this tutorial, you will use OPENQUERY.</span></span> <span data-ttu-id="ec7d1-162">使用可能なオプションの詳細については、「 [&#60;source data query&#62;](/sql/dmx/source-data-query)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-162">For more information about the options available, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
 <span data-ttu-id="ec7d1-163">次の行では、マイニング モデルのソース列とソース データの列間のマッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-163">The next line defines the mapping between the source columns in the mining model and the columns in the source data:</span></span>  
  
```  
ON <column mappings>  
```  
  
 <span data-ttu-id="ec7d1-164">WHERE 句は、予測クエリで返される結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-164">The WHERE clause filters the results returned by the prediction query:</span></span>  
  
```  
WHERE <where clause, boolean expression,>  
```  
  
 <span data-ttu-id="ec7d1-165">コードの最後の省略可能な行では、結果の列の順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-165">The last and optional line of the code specifies the column that the results will be ordered by:</span></span>  
  
```  
ORDER BY <expression> [DESC|ASC]  
```  
  
 <span data-ttu-id="ec7d1-166">ORDER BY を TOP ステートメントと組み合わせて使用して、 \<number> 返される結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-166">Use ORDER BY in combination with the TOP \<number> statement, to filter the results that are returned.</span></span> <span data-ttu-id="ec7d1-167">たとえば、今回の予測では上位 10 人の自転車購入者が返され、結果は予測の精度が高い順序で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-167">For example, in this prediction you will return the top ten bike buyers, ordered by the probability of the prediction being correct.</span></span> <span data-ttu-id="ec7d1-168">[DESC|ASC] 構文を使用すると、結果を表示する順序を制御できます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-168">You can use [DESC|ASC] syntax to control the order in which the results are displayed.</span></span>  
  
#### <a name="to-create-a-batch-prediction-query"></a><span data-ttu-id="ec7d1-169">バッチ予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="ec7d1-169">To create a batch prediction query</span></span>  
  
1.  <span data-ttu-id="ec7d1-170">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-170">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="ec7d1-171">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-171">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="ec7d1-172">上のバッチ ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-172">Copy the generic example of the batch statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="ec7d1-173">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-173">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="ec7d1-174">with:</span><span class="sxs-lookup"><span data-stu-id="ec7d1-174">with:</span></span>  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    ```  
  
     <span data-ttu-id="ec7d1-175">TOP 10 句を指定すると、クエリによって上位 10 個の結果だけが返されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-175">The TOP 10 clause specifies that only the top ten results will be returned by the query.</span></span> <span data-ttu-id="ec7d1-176">このクエリの ORDER BY ステートメントでは、予測の精度が高い順序で結果が並べ替えられ、可能性が高い上位 10 件の結果だけが返されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-176">The ORDER BY statement in this query orders the results by the probability of the prediction being correct, so only the ten most likely results will be returned.</span></span>  
  
4.  <span data-ttu-id="ec7d1-177">次のプレースホルダーを置換します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-177">Replace the following placeholder:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="ec7d1-178">置換後はモデルの名前になります。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-178">With the name of the model:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="ec7d1-179">次の一般的な OPENQUERY ステートメントを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-179">Replace the following generic OPENQUERY statement:</span></span>  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     <span data-ttu-id="ec7d1-180">置換後は、AdventureWork の現在のデータ ウェアハウスを参照するステートメントであり、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-180">With a statement that references the current Adventureworks data warehouse, such as:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW 2014],  
      'SELECT  
        [LastName],  
        [FirstName],  
        [MaritalStatus],  
        [Gender],  
        [YearlyIncome],  
        [TotalChildren],  
        [NumberChildrenAtHome],  
        [Education],  
        [Occupation],  
        [HouseOwnerFlag],  
        [NumberCarsOwned]  
      FROM  
        [dbo].[ProspectiveBuyer]  
      ') AS t  
    ```  
  
6.  <span data-ttu-id="ec7d1-181">次の一般的な構文を置換します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-181">Replace the following generic syntax:</span></span>  
  
    ```  
    <ON clause, mapping,>   
    WHERE <where clause, boolean expression,>  
    ORDER BY <expression>  
    ```  
  
     <span data-ttu-id="ec7d1-182">置換後は、このモデルと入力データ セットで必要とされる列のマッピングになります。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-182">With the column mappings needed for this model and input data set:</span></span>  
  
    ```  
    [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
     <span data-ttu-id="ec7d1-183">可能性の高い順に結果が一覧されるように、`DESC` を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-183">Specify `DESC` in order to list the results with the highest probability first.</span></span>  
  
     <span data-ttu-id="ec7d1-184">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-184">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    FROM  
      [Decision Tree]  
    PREDICTION JOIN  
      OPENQUERY([Adventure Works DW 2014],  
        'SELECT  
          [LastName],  
          [FirstName],  
          [MaritalStatus],  
          [Gender],  
          [YearlyIncome],  
          [TotalChildren],  
          [NumberChildrenAtHome],  
          [Education],  
          [Occupation],  
          [HouseOwnerFlag],  
          [NumberCarsOwned]  
        FROM  
          [dbo].[ProspectiveBuyer]  
        ') AS t  
    ON  
      [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
7.  <span data-ttu-id="ec7d1-185">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-185">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="ec7d1-186">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Batch_Prediction.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-186">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Batch_Prediction.dmx`.</span></span>  
  
9. <span data-ttu-id="ec7d1-187">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-187">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="ec7d1-188">クエリが実行され、顧客名、各顧客が自転車を購入するかどうかの予測、予測の精度を含むテーブルが返されます。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-188">The query returns a table containing customer names, a prediction of whether each customer will purchase a bicycle, and the probability of the prediction.</span></span>  
  
 <span data-ttu-id="ec7d1-189">以上で Bike Buyer チュートリアルは終了です。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-189">This is the last step in the Bike Buyer tutorial.</span></span> <span data-ttu-id="ec7d1-190">これで、顧客の類似性を特定し、潜在顧客が自転車を購入するかどうかを予測するために使用できるマイニング モデルのセットが完成しました。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-190">You now have a set of mining models that you can use to explore similarities between you customers and predict whether potential customers will purchase a bicycle.</span></span>  
  
 <span data-ttu-id="ec7d1-191">マーケットバスケットシナリオで DMX を使用する方法については、「[マーケットバスケット dmx のチュートリアル](../../2014/tutorials/market-basket-dmx-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec7d1-191">To learn how to use DMX in a Market Basket scenario, see [Market Basket DMX Tutorial](../../2014/tutorials/market-basket-dmx-tutorial.md).</span></span>  
  
  
