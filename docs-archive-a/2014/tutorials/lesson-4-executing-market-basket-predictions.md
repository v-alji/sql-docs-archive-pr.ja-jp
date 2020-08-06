---
title: 'レッスン 4: マーケットバスケット予測の実行 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b49fc242eb8b2242269c5af33cc094937bbe0de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639837"
---
# <a name="lesson-4-executing-market-basket-predictions"></a><span data-ttu-id="f2fd7-102">レッスン 4: マーケット バスケット予測の実行</span><span class="sxs-lookup"><span data-stu-id="f2fd7-102">Lesson 4: Executing Market Basket Predictions</span></span>
  <span data-ttu-id="f2fd7-103">このレッスンでは、DMX ステートメントを使用して、 `SELECT` [「レッスン 2: マーケットバスケットマイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)」で作成したアソシエーションモデルに基づいて予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-103">In this lesson, you will use the DMX `SELECT` statement to create predictions based on the association models you created in [Lesson 2: Adding Mining Models to the Market Basket Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="f2fd7-104">DMX の `SELECT` ステートメントを使用して、`PREDICTION JOIN` 句を追加することにより、予測クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-104">A prediction query is created by using the DMX `SELECT` statement and adding a `PREDICTION JOIN` clause.</span></span> <span data-ttu-id="f2fd7-105">予測結合の構文の詳細については、「 [SELECT FROM &#60;model&#62; DMX&#41;&#40;の予測結合](/sql/dmx/select-from-model-cases-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-105">For more information about the syntax of a prediction join, see [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx).</span></span>  
  
 <span data-ttu-id="f2fd7-106">ステートメントの**SELECT FROM \<model> 予測結合**フォームには、 `SELECT` 次の3つの部分が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-106">The **SELECT FROM \<model> PREDICTION JOIN** form of the `SELECT` statement contains three parts:</span></span>  
  
-   <span data-ttu-id="f2fd7-107">結果セットで返される、マイニング モデル列と予測関数の一覧。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-107">A list of the mining model columns and prediction functions that are returned in the result set.</span></span> <span data-ttu-id="f2fd7-108">この一覧にはソース データからの入力列を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-108">This list can also contain input columns from the source data.</span></span>  
  
-   <span data-ttu-id="f2fd7-109">予測の作成に使用するデータを定義するソース クエリ。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-109">A source query that defines the data that is being used to create a prediction.</span></span> <span data-ttu-id="f2fd7-110">たとえば、多数の予測をバッチで作成する場合、ソース クエリで顧客の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-110">For example, if you are creating many predictions in a batch, the source query could retrieve a list of customers.</span></span>  
  
-   <span data-ttu-id="f2fd7-111">マイニング モデル列とソース データ間のマッピング。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-111">A mapping between the mining model columns and the source data.</span></span> <span data-ttu-id="f2fd7-112">列の名前が同じ場合は、`NATURAL PREDICTION JOIN` 構文を使用して列マッピングを省略できます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-112">If the columns names match, you can use the `NATURAL PREDICTION JOIN` syntax and omit the column mappings.</span></span>  
  
 <span data-ttu-id="f2fd7-113">予測関数を使用すると、クエリを改良できます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-113">You can enhance the query by using prediction functions.</span></span> <span data-ttu-id="f2fd7-114">予測関数では、予測が発生する可能性などの追加の情報や、トレーニング データセットでの予測サポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-114">Prediction functions provide additional information, such as the probability of a prediction occurring, or the support for a prediction in the training dataset.</span></span> <span data-ttu-id="f2fd7-115">予測関数の詳細については、「 [functions &#40;DMX&#41;](/sql/dmx/functions-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-115">For more information about prediction functions, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
 <span data-ttu-id="f2fd7-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で予測クエリ ビルダーを使用して、予測クエリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-116">You can also use the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create prediction queries.</span></span>  
  
## <a name="singleton-prediction-join-statement"></a><span data-ttu-id="f2fd7-117">単一 PREDICTION JOIN ステートメント</span><span class="sxs-lookup"><span data-stu-id="f2fd7-117">Singleton PREDICTION JOIN Statement</span></span>  
 <span data-ttu-id="f2fd7-118">最初の手順では、 **SELECT FROM \<model> 予測結合**構文を使用し、入力として1つの値セットを指定することによって、単一クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-118">The first step is to create a singleton query, by using the **SELECT FROM \<model> PREDICTION JOIN** syntax and supplying a single set of values as input.</span></span> <span data-ttu-id="f2fd7-119">単一ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-119">The following is a generic example of the singleton statement:</span></span>  
  
```  
SELECT <select list>  
    FROM [<mining model>]   
[NATURAL] PREDICTION JOIN  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
AS [<input alias>]  
```  
  
 <span data-ttu-id="f2fd7-120">コードの最初の行では、クエリで返されるマイニング モデルの列を定義し、予測の生成に使用するマイニング モデルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-120">The first line of the code defines the columns from the mining model that the query returns, and specifies the name of the mining model used to generate the prediction:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>]   
```  
  
 <span data-ttu-id="f2fd7-121">コードの次の行は、実行する操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-121">The next line of the code indicates the operation to perform.</span></span> <span data-ttu-id="f2fd7-122">各列に値を指定し、モデルと正確に一致するように列名を入力するため、`NATURAL PREDICTION JOIN` 構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-122">Because you will specify values for each of the columns and type the column names exactly so as to match the model, you can use the `NATURAL PREDICTION JOIN` syntax.</span></span> <span data-ttu-id="f2fd7-123">ただし、列名が異なる場合は、`ON` 句を追加して、モデルの列と新しいデータの列の間のマッピングを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-123">However, if the column names were different, you would have to specify mappings between the columns in the model and the columns in the new data by adding an `ON` clause.</span></span>  
  
```  
[NATURAL] PREDICTION JOIN  
```  
  
 <span data-ttu-id="f2fd7-124">次の行では、追加購入される製品の予測に使用する、ショッピング カート内の製品を定義します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-124">The next lines of the code define the products in the shopping cart that will be used to predict additional products that a customer will add:</span></span>  
  
```  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="f2fd7-125">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="f2fd7-125">Lesson Tasks</span></span>  
 <span data-ttu-id="f2fd7-126">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-126">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="f2fd7-127">買い物かごに既に存在する商品に基づいて、顧客が購入する可能性のある他のアイテムを予測するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-127">Create a query that predicts what other items a customer will likely purchase, based on items already existing in their shopping cart.</span></span> <span data-ttu-id="f2fd7-128">このクエリは、既定の*MINIMUM_PROBABILITY*を持つマイニングモデルを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-128">You will create this query by using the mining model with the default *MINIMUM_PROBABILITY*.</span></span>  
  
-   <span data-ttu-id="f2fd7-129">既にショッピング カートに入っている製品に基づいて、他に購入される可能性のある製品を予測するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-129">Create a query that predicts what other items a customer will likely purchase based on items already existing in their shopping cart.</span></span> <span data-ttu-id="f2fd7-130">このクエリは、 *MINIMUM_PROBABILITY*が0.01 に設定されている別のモデルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-130">This query is based on a different model, in which *MINIMUM_PROBABILITY* has been set to 0.01.</span></span> <span data-ttu-id="f2fd7-131">アソシエーションモデルの*MINIMUM_PROBABILITY*の既定値は0.3 なので、このモデルのクエリでは、既定のモデルのクエリよりも多くの項目が返されます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-131">Because the default value for *MINIMUM_PROBABILITY* in association models is 0.3, the query on this model should return more possible items than the query on the default model.</span></span>  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimum_probability"></a><span data-ttu-id="f2fd7-132">既定の MINIMUM_PROBABILITY が設定されたモデルを使用した予測の作成</span><span class="sxs-lookup"><span data-stu-id="f2fd7-132">Create a Prediction by Using a Model with the Default MINIMUM_PROBABILITY</span></span>  
  
#### <a name="to-create-an-association-query"></a><span data-ttu-id="f2fd7-133">アソシエーション クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="f2fd7-133">To create an association query</span></span>  
  
1.  <span data-ttu-id="f2fd7-134">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックしてクエリエディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-134">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="f2fd7-135">`PREDICTION JOIN` ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-135">Copy the generic example of the `PREDICTION JOIN` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="f2fd7-136">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-136">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="f2fd7-137">with:</span><span class="sxs-lookup"><span data-stu-id="f2fd7-137">with:</span></span>  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     <span data-ttu-id="f2fd7-138">列名 [Products] を含めることもできますが、 [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx)関数を使用すると、アルゴリズムによって返される製品の数を3つに制限することができます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-138">You could just include the column name [Products], but by using the [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) function, you can limit the number of products that are returned by the algorithm to three.</span></span> <span data-ttu-id="f2fd7-139">さらに、`INCLUDE_STATISTICS` を使用して、製品ごとのサポート、確率、および調整済みの確率を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-139">You can also use `INCLUDE_STATISTICS`, which returns the support, probability, and adjusted probability for each product.</span></span> <span data-ttu-id="f2fd7-140">これらの統計は、予測の精度を評価するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-140">These statistics help you rate the accuracy of the prediction.</span></span>  
  
4.  <span data-ttu-id="f2fd7-141">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-141">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="f2fd7-142">with:</span><span class="sxs-lookup"><span data-stu-id="f2fd7-142">with:</span></span>  
  
    ```  
    [Default Association]  
    ```  
  
5.  <span data-ttu-id="f2fd7-143">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-143">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     <span data-ttu-id="f2fd7-144">with:</span><span class="sxs-lookup"><span data-stu-id="f2fd7-144">with:</span></span>  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     <span data-ttu-id="f2fd7-145">このステートメントでは、`UNION` ステートメントを使用して、予測された製品と共にショッピング カートに含まれる 3 つの製品を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-145">This statement uses the `UNION` statement to specify three products that must be included in the shopping cart together with the predicted products.</span></span> <span data-ttu-id="f2fd7-146">`SELECT` ステートメント内の Model 列は、入れ子になった製品テーブル内のモデル列に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-146">The Model column in the `SELECT` statement corresponds to the model column that is contained in the nested products table.</span></span>  
  
     <span data-ttu-id="f2fd7-147">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-147">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Default Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  <span data-ttu-id="f2fd7-148">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-148">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="f2fd7-149">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Association Prediction.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-149">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Association Prediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="f2fd7-150">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-150">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="f2fd7-151">クエリによって、HL Mountain Tire、Fender Set - Mountain、ML Mountain Tire の 3 つの製品が含まれたテーブルが返されます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-151">The query returns a table that contains three products: HL Mountain Tire, Fender Set - Mountain, and ML Mountain Tire.</span></span> <span data-ttu-id="f2fd7-152">テーブルには、返された製品が確率の順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-152">The table lists these returned products in order of probability.</span></span> <span data-ttu-id="f2fd7-153">返された製品のうち、クエリで指定した 3 つの製品と同じショッピング カートに入っている可能性の最も高いものが、テーブルの一番上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-153">The returned product that is most likely to be included in the same shopping cart as the three products specified in the query appears at the top of the table.</span></span> <span data-ttu-id="f2fd7-154">続いて表示される 2 つは、ショッピング カートに入っている可能性が次に高い製品です。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-154">The two products that follow are the next most likely to be included in the shopping cart.</span></span> <span data-ttu-id="f2fd7-155">さらに、このテーブルには、予測の精度を表す統計も含まれます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-155">The table also contains statistics describing the accuracy of the prediction.</span></span>  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimum_probability-of-001"></a><span data-ttu-id="f2fd7-156">MINIMUM_PROBABILITY が 0.01 に設定されたマイニング モデルを使用した予測の作成</span><span class="sxs-lookup"><span data-stu-id="f2fd7-156">Create a Prediction by Using a Model with a MINIMUM_PROBABILITY of 0.01</span></span>  
  
#### <a name="to-create-an-association-query"></a><span data-ttu-id="f2fd7-157">アソシエーション クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="f2fd7-157">To create an association query</span></span>  
  
1.  <span data-ttu-id="f2fd7-158">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックしてクエリエディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-158">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="f2fd7-159">`PREDICTION JOIN` ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-159">Copy the generic example of the `PREDICTION JOIN` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="f2fd7-160">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-160">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="f2fd7-161">with:</span><span class="sxs-lookup"><span data-stu-id="f2fd7-161">with:</span></span>  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  <span data-ttu-id="f2fd7-162">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-162">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="f2fd7-163">with:</span><span class="sxs-lookup"><span data-stu-id="f2fd7-163">with:</span></span>  
  
    ```  
    [Modified Association]  
    ```  
  
5.  <span data-ttu-id="f2fd7-164">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-164">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     <span data-ttu-id="f2fd7-165">with:</span><span class="sxs-lookup"><span data-stu-id="f2fd7-165">with:</span></span>  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     <span data-ttu-id="f2fd7-166">このステートメントでは、`UNION` ステートメントを使用して、予測された製品と共にショッピング カートに含まれる 3 つの製品を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-166">This statement uses the `UNION` statement to specify three products that must be included in the shopping cart together with the predicted products.</span></span> <span data-ttu-id="f2fd7-167">`SELECT` ステートメント内の `[Model]` 列は、入れ子になった製品テーブル内の列に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-167">The `[Model]` column in the `SELECT` statement corresponds to the column in the nested products table.</span></span>  
  
     <span data-ttu-id="f2fd7-168">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-168">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Modified Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  <span data-ttu-id="f2fd7-169">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-169">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="f2fd7-170">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Modified Association Prediction.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-170">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Modified Association Prediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="f2fd7-171">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-171">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="f2fd7-172">クエリによって、HL Mountain Tire、Water Bottle、Fender Set - Mountain の 3 つの製品が含まれたテーブルが返されます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-172">The query returns a table that contains three products: HL Mountain Tire, Water Bottle, and Fender Set - Mountain.</span></span> <span data-ttu-id="f2fd7-173">テーブルには、これらの製品が確率の順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-173">The table lists these products in order of probability.</span></span> <span data-ttu-id="f2fd7-174">テーブルの一番上に表示されるのは、クエリで指定した 3 つの製品と同じショッピング カートに入っている可能性の最も高い製品です。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-174">The product that appears at the top of the table is the product that is most likely to be included in the same shopping cart as the three products specified in the query.</span></span> <span data-ttu-id="f2fd7-175">それ以外は、ショッピング カートに入っている可能性が次に高い製品です。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-175">The remaining products are the next most likely to be included in the shopping cart.</span></span> <span data-ttu-id="f2fd7-176">このテーブルには、予測の精度を示す統計も含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-176">The table also contains statistics that describe the accuracy of the prediction.</span></span>  
  
     <span data-ttu-id="f2fd7-177">このクエリの結果から、 *MINIMUM_PROBABILITY*パラメーターの値がクエリによって返される結果に影響することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-177">You can see from the results of this query that the value of the *MINIMUM_PROBABILITY* parameter affects the results returned by the query.</span></span>  
  
 <span data-ttu-id="f2fd7-178">これで、マーケット バスケットのチュートリアルの最後の手順が終了します。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-178">This is the last step in the Market Basket tutorial.</span></span> <span data-ttu-id="f2fd7-179">このチュートリアルでは、同時に購入される可能性がある製品を予測するときに使用できる、モデルのセットを作成しました。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-179">You now have a set of models that you can use to predict the products that customers might purchase at the same time.</span></span>  
  
 <span data-ttu-id="f2fd7-180">別の予測シナリオで DMX を使用する方法については、「[自転車購入者向け Dmx チュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2fd7-180">To learn how to use DMX in another predictive scenario, see [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2fd7-181">参照</span><span class="sxs-lookup"><span data-stu-id="f2fd7-181">See Also</span></span>  
 <span data-ttu-id="f2fd7-182">[アソシエーションモデルのクエリ例](../../2014/analysis-services/data-mining/association-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="f2fd7-182">[Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md) </span></span>  
 [<span data-ttu-id="f2fd7-183">データ マイニング クエリ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2fd7-183">Data Mining Query Interfaces</span></span>](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
