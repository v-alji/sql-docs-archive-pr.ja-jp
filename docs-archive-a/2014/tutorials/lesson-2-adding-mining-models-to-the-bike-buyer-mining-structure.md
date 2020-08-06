---
title: 'レッスン 2: 自転車購入者マイニング構造へのマイニングモデルの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: de65fb7a85154f607cd8f266faec4621cdc41476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717108"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a><span data-ttu-id="d4e6d-102">レッスン 2: Bike Buyer マイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="d4e6d-102">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="d4e6d-103">このレッスンでは、「[レッスン 1: 自転車購入者マイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)」で作成した自転車購入者マイニング構造に2つのマイニングモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-103">In this lesson, you will add two mining models to the Bike Buyer mining structure that you created [Lesson 1: Creating the Bike Buyer Mining Structure](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md).</span></span> <span data-ttu-id="d4e6d-104">これら 2 つのマイニング モデルを追加すると、一方のモデルでデータを調査でき、もう一方のモデルで予測を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-104">These mining models will allow you to explore the data using one model, and to create predictions using another.</span></span>  
  
 <span data-ttu-id="d4e6d-105">潜在的な顧客がその特性によってどのように分類されるかを調べるには、 [Microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)に基づいてマイニングモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-105">To explore how potential customers can be categorized by their characteristics, you will create a mining model based on the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).</span></span> <span data-ttu-id="d4e6d-106">後のレッスンでは、類似した特性を持つ顧客グループがこのアルゴリズムでどのように特定されるかについて学習します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-106">In a later lesson, you will explore how this algorithm finds clusters of customers who share similar characteristics.</span></span> <span data-ttu-id="d4e6d-107">たとえば、ある特定の顧客グループは、住居が近く、自転車で通勤し、学歴が類似しているといった情報を得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-107">For example, you might find that certain customers tend to live close to each other, commute by bicycle, and have similar education backgrounds.</span></span> <span data-ttu-id="d4e6d-108">このような分類を基にさまざまな顧客の関連性を把握し、この情報を使用して特定顧客をターゲットとしたマーケティング戦略を立てることができます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-108">You can use these clusters to better understand how different customers are related, and to use the information to create a marketing strategy that targets specific customers.</span></span>  
  
 <span data-ttu-id="d4e6d-109">潜在顧客が自転車を購入する可能性があるかどうかを予測するには、 [Microsoft デシジョンツリーアルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)に基づいてマイニングモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-109">To predict whether a potential customer is likely to buy a bicycle, you will create a mining model based on the [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md).</span></span> <span data-ttu-id="d4e6d-110">このアルゴリズムではそれぞれの潜在顧客に関連付けられている情報を基に、自転車を購入するかどうかの予測に役立つ特性を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-110">This algorithm looks through the information that is associated with each potential customer, and finds characteristics that are useful in predicting if they will buy a bicycle.</span></span> <span data-ttu-id="d4e6d-111">特性が見つかったら、以前自転車を購入した顧客と新しい潜在顧客の特性値を比較して、新しい潜在顧客が自転車を購入する可能性を判定することができます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-111">It then compares the values of the characteristics of previous bike buyers against new potential customers to determine whether the new potential customers are likely to buy a bicycle.</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="d4e6d-112">ALTER MINING STRUCTURE ステートメント</span><span class="sxs-lookup"><span data-stu-id="d4e6d-112">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="d4e6d-113">マイニングモデルをマイニング構造に追加するには、 [ALTER マイニング構造 &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-113">In order to add a mining model to the mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="d4e6d-114">ステートメント内のコードは、次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-114">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="d4e6d-115">マイニング構造の指定</span><span class="sxs-lookup"><span data-stu-id="d4e6d-115">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="d4e6d-116">マイニング モデルの名前指定</span><span class="sxs-lookup"><span data-stu-id="d4e6d-116">Naming the mining model</span></span>  
  
-   <span data-ttu-id="d4e6d-117">キー列の定義</span><span class="sxs-lookup"><span data-stu-id="d4e6d-117">Defining the key column</span></span>  
  
-   <span data-ttu-id="d4e6d-118">入力列と予測可能列の定義</span><span class="sxs-lookup"><span data-stu-id="d4e6d-118">Defining the input and predictable columns</span></span>  
  
-   <span data-ttu-id="d4e6d-119">アルゴリズムとパラメーターの変更の特定</span><span class="sxs-lookup"><span data-stu-id="d4e6d-119">Identifying the algorithm and parameter changes</span></span>  
  
 <span data-ttu-id="d4e6d-120">ALTER MINING MODEL ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-120">The following is a generic example of the ALTER MINING MODEL statement:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
(  
    [<key column>],  
    <mining model columns>,  
) USING <algorithm name>( <algorithm parameters> )  
WITH FILTER (<expression>)  
```  
  
 <span data-ttu-id="d4e6d-121">コードの最初の行では、マイニングモデルを追加する既存のマイニング構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-121">The first line of the code identifies the existing mining structure to which the mining models will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="d4e6d-122">コードの次の行では、マイニング構造に追加するマイニング モデルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-122">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="d4e6d-123">DMX でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-123">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="d4e6d-124">コードの次の数行では、マイニング モデルで使用するマイニング構造の列を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-124">The next lines of the code define columns from the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key column>],  
<mining model columns>  
```  
  
 <span data-ttu-id="d4e6d-125">使用できるのは、マイニング構造内に既に存在する列だけです。一覧の最初の列は、マイニング構造のキー列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-125">You can only use columns that already exist in the mining structure, and the first column in the list must be the key column from the mining structure.</span></span>  
  
 <span data-ttu-id="d4e6d-126">コードの次の行では、マイニング モデルを生成するマイニング アルゴリズムと、アルゴリズムに設定できるアルゴリズム パラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-126">The next line of the code defines the mining algorithm that generates the mining model and the algorithm parameters that you can set on the algorithm:</span></span>  
  
```  
) USING <algorithm name>( <algorithm parameters> )  
```  
  
 <span data-ttu-id="d4e6d-127">調整できるアルゴリズムパラメーターの詳細については、「 [Microsoft デシジョンツリーアルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)」および「 [microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-127">For more information about the algorithm parameters that you can adjust, see [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) and [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).</span></span>  
  
 <span data-ttu-id="d4e6d-128">次の構文で、マイニング モデルの列を予測に使用するよう指定できます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-128">You can specify that a column in the mining model be used for prediction by using the following syntax:</span></span>  
  
```  
<mining model column> PREDICT  
```  
  
 <span data-ttu-id="d4e6d-129">コードの最後の行 (省略可能) では、モデルの学習およびテストを行う際に適用するフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-129">The final line of the code, which is optional, defines a filter that is applied when training and testing the model.</span></span> <span data-ttu-id="d4e6d-130">マイニングモデルにフィルターを適用する方法の詳細については、「 [Analysis Services データマイニング&#41;&#40;マイニングモデルのフィルター ](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-130">For more information about how to apply filters to mining models, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="d4e6d-131">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="d4e6d-131">Lesson Tasks</span></span>  
 <span data-ttu-id="d4e6d-132">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-132">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="d4e6d-133">[!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムを使用して、デシジョン ツリー マイニング モデルを Bike Buyer 構造に追加。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-133">Add a decision tree mining model to the Bike Buyer structure by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm</span></span>  
  
-   <span data-ttu-id="d4e6d-134">[!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムを使用して、クラスタリング マイニング モデルを Bike Buyer 構造に追加。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-134">Add a clustering mining model to the Bike Buyer structure by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm</span></span>  
  
-   <span data-ttu-id="d4e6d-135">すべてのケースの結果を表示する必要があるため、どちらのモデルにもまだフィルターを追加しません。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-135">Because you want to see results for all cases, you will not yet add a filter to either model.</span></span>  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a><span data-ttu-id="d4e6d-136">構造へのデシジョンツリーマイニングモデルの追加</span><span class="sxs-lookup"><span data-stu-id="d4e6d-136">Adding a Decision Tree Mining Model to the Structure</span></span>  
 <span data-ttu-id="d4e6d-137">最初に、[!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムに基づくマイニング モデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-137">The first step is to add a mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
#### <a name="to-add-a-decision-tree-mining-model"></a><span data-ttu-id="d4e6d-138">デシジョン ツリー マイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="d4e6d-138">To add a decision tree mining model</span></span>  
  
1.  <span data-ttu-id="d4e6d-139">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックしてクエリエディターと、新しい空のクエリを開きます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-139">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="d4e6d-140">上の ALTER MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-140">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="d4e6d-141">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-141">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="d4e6d-142">with:</span><span class="sxs-lookup"><span data-stu-id="d4e6d-142">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="d4e6d-143">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-143">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="d4e6d-144">with:</span><span class="sxs-lookup"><span data-stu-id="d4e6d-144">with:</span></span>  
  
    ```  
    Decision Tree  
    ```  
  
5.  <span data-ttu-id="d4e6d-145">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-145">Replace the following:</span></span>  
  
    ```  
    <mining model columns>,  
    ```  
  
     <span data-ttu-id="d4e6d-146">with:</span><span class="sxs-lookup"><span data-stu-id="d4e6d-146">with:</span></span>  
  
    ```  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ```  
  
     <span data-ttu-id="d4e6d-147">この場合、`[Bike Buyer]` 列は PREDICT 列として指定されています。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-147">In this case, the `[Bike Buyer]` column has been designated as the PREDICT column.</span></span>  
  
6.  <span data-ttu-id="d4e6d-148">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-148">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )   
    ```  
  
     <span data-ttu-id="d4e6d-149">with:</span><span class="sxs-lookup"><span data-stu-id="d4e6d-149">with:</span></span>  
  
    ```  
    Using Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="d4e6d-150">WITH DRILLTHROUGH ステートメントを指定すると、マイニング モデルの構築に使用されたケースを閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-150">The WITH DRILLTHROUGH statement allows you to explore the cases that were used to build the mining model.</span></span>  
  
     <span data-ttu-id="d4e6d-151">これで、ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-151">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Decision Tree]  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ) USING Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
7.  <span data-ttu-id="d4e6d-152">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="d4e6d-153">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `DT_Model.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `DT_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="d4e6d-154">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-154">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a><span data-ttu-id="d4e6d-155">構造へのクラスター マイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="d4e6d-155">Adding a Clustering Mining Model to the Structure</span></span>  
 <span data-ttu-id="d4e6d-156">次に、[!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムに基づくマイニング モデルを、Bike Buyer マイニング構造に追加します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-156">You can now add a mining model to the Bike Buyer mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="d4e6d-157">クラスター マイニング モデルでは、マイニング構造に定義されている列をすべて使用します。したがって、マイニング列の定義を省略して、この構造にモデルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-157">Because the clustering mining model will use all the columns defined in the mining structure, you can use a shortcut to add the model to the structure by omitting the definition of the mining columns.</span></span>  
  
#### <a name="to-add-a-clustering-mining-model"></a><span data-ttu-id="d4e6d-158">クラスター マイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="d4e6d-158">To add a Clustering mining model</span></span>  
  
1.  <span data-ttu-id="d4e6d-159">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックすると、クエリエディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-159">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor opens and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="d4e6d-160">上の ALTER MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-160">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="d4e6d-161">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-161">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="d4e6d-162">with:</span><span class="sxs-lookup"><span data-stu-id="d4e6d-162">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="d4e6d-163">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-163">Replace the following:</span></span>  
  
    ```  
    <mining model>   
    ```  
  
     <span data-ttu-id="d4e6d-164">with:</span><span class="sxs-lookup"><span data-stu-id="d4e6d-164">with:</span></span>  
  
    ```  
    Clustering Model  
    ```  
  
5.  <span data-ttu-id="d4e6d-165">次の部分を削除します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-165">Delete the following:</span></span>  
  
    ```  
    (  
        [<key column>],  
        <mining model columns>,  
    )  
    ```  
  
6.  <span data-ttu-id="d4e6d-166">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-166">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="d4e6d-167">with:</span><span class="sxs-lookup"><span data-stu-id="d4e6d-167">with:</span></span>  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     <span data-ttu-id="d4e6d-168">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-168">The complete statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  <span data-ttu-id="d4e6d-169">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-169">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="d4e6d-170">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Clustering_Model.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-170">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Clustering_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="d4e6d-171">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-171">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="d4e6d-172">次のレッスンでは、モデルとマイニング構造を処理します。</span><span class="sxs-lookup"><span data-stu-id="d4e6d-172">In the next lesson, you will process the models and the mining structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="d4e6d-173">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="d4e6d-173">Next Lesson</span></span>  
 [<span data-ttu-id="d4e6d-174">レッスン 3: Bike Buyer マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="d4e6d-174">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
