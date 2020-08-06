---
title: 'レッスン 2: マーケットバスケットマイニング構造へのマイニングモデルの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d96a7a7d-35d7-4b34-abb5-f0822c256253
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b9573d9359983e33cf23533787c26039572710ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717097"
---
# <a name="lesson-2-adding-mining-models-to-the-market-basket-mining-structure"></a><span data-ttu-id="08bf3-102">レッスン 2: Market Basket マイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="08bf3-102">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>
  <span data-ttu-id="08bf3-103">このレッスンでは、「[レッスン 1: マーケットバスケットマイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)」で作成したマーケットバスケットマイニング構造に2つのマイニングモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-103">In this lesson, you will add two mining models to the Market Basket mining structure that you created in [Lesson 1: Creating the Market Basket Mining Structure](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="08bf3-104">これらのマイニング モデルを使用すると、予測を作成できます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-104">These mining models will allow you to create predictions.</span></span>  
  
 <span data-ttu-id="08bf3-105">顧客が同時に購入する傾向のある製品の種類を予測するには、 [Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)を使用して2つのマイニングモデルを作成し、 *MINIMUM_PROBABILTY*パラメーターに2つの異なる値を指定します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-105">To predict the types of products that customers tend to purchase at the same time, you will create two mining models using the [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) and two different values for the *MINIMUM_PROBABILTY* parameter.</span></span>  
  
 <span data-ttu-id="08bf3-106">*MINIMUM_PROBABILTY*は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] ルールに必要な最小の確率を指定することによって、マイニングモデルに含まれるルールの数を決定するために使用されるアソシエーションアルゴリズムパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="08bf3-106">*MINIMUM_PROBABILTY* is a [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm parameter that helps to determine the number of rules that a mining model will contain by specifying the minimum probability that a rule must have.</span></span> <span data-ttu-id="08bf3-107">たとえば、この値を 0.4 に設定すると、ルールで記述する製品の組み合わせの発生確率が 40% 以上である場合にのみ、ルールが生成されます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-107">For example, setting this value to 0.4 specifies that a rule can be generated only if the combination of products that the rule describes has at least a forty percent probability of occurring.</span></span>  
  
 <span data-ttu-id="08bf3-108">後のレッスンでは、 *MINIMUM_PROBABILTY*パラメーターを変更した場合の影響を確認します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-108">You will view the effect of changing the *MINIMUM_PROBABILTY* parameter in a later lesson.</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="08bf3-109">ALTER MINING STRUCTURE ステートメント</span><span class="sxs-lookup"><span data-stu-id="08bf3-109">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="08bf3-110">入れ子になったテーブルを含むマイニングモデルをマイニング構造に追加するには、 [ALTER マイニング構造 &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-110">To add a mining model that contains a nested table to a mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="08bf3-111">ステートメント内のコードは、次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-111">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="08bf3-112">マイニング構造の指定</span><span class="sxs-lookup"><span data-stu-id="08bf3-112">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="08bf3-113">マイニング モデルの名前指定</span><span class="sxs-lookup"><span data-stu-id="08bf3-113">Naming the mining model</span></span>  
  
-   <span data-ttu-id="08bf3-114">キー列の定義</span><span class="sxs-lookup"><span data-stu-id="08bf3-114">Defining the key column</span></span>  
  
-   <span data-ttu-id="08bf3-115">入力列と予測可能列の定義</span><span class="sxs-lookup"><span data-stu-id="08bf3-115">Defining the input and predictable columns</span></span>  
  
-   <span data-ttu-id="08bf3-116">入れ子になったテーブル列の定義</span><span class="sxs-lookup"><span data-stu-id="08bf3-116">Defining the nested table columns</span></span>  
  
-   <span data-ttu-id="08bf3-117">アルゴリズムとパラメーターの変更の特定</span><span class="sxs-lookup"><span data-stu-id="08bf3-117">Identifying the algorithm and parameter changes</span></span>  
  
 <span data-ttu-id="08bf3-118">入れ子になったテーブル列を含む構造にマイニング モデルを追加する `ALTER MINING STRUCTURE` ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-118">The following is a generic example of the `ALTER MINING STRUCTURE` statement that adds a mining model to a structure that includes nested table columns:</span></span>  
  
```  
ALTER MINING STRUCTURE [<Mining Structure Name>]  
ADD MINING MODEL [<Mining Model Name>]  
(  
    [<key column>],  
    <mining model column> <usage>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
) USING <algorithm>( <algorithm parameters> )  
```  
  
 <span data-ttu-id="08bf3-119">コードの最初の行では、マイニング モデルの追加先となる既存のマイニング構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-119">The first line of the code identifies the existing mining structure to which the mining model will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="08bf3-120">コードの次の行では、マイニング構造に追加するマイニング モデルを指定します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-120">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="08bf3-121">データマイニング拡張機能 (DMX) でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08bf3-121">For information about naming an object in Data Mining Extensions (DMX), see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="08bf3-122">コードの次の行では、マイニングモデルによって使用されるマイニング構造の列を定義します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-122">The next lines of the code define the columns in the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key column>],  
<mining model columns> <usage>,  
```  
  
 <span data-ttu-id="08bf3-123">使用できるのは、マイニング構造内に既に存在する列だけです。</span><span class="sxs-lookup"><span data-stu-id="08bf3-123">You can only use columns that already exist in the mining structure.</span></span>  
  
 <span data-ttu-id="08bf3-124">マイニング モデル列の一覧の最初の列は、マイニング構造のキー列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="08bf3-124">The first column in the list of mining model columns must be the key column in the mining structure.</span></span> <span data-ttu-id="08bf3-125">ただし、 `KEY` 使用法を指定するためにキー列の後に入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="08bf3-125">However, you do not have to type `KEY` after the key column to specify usage.</span></span> <span data-ttu-id="08bf3-126">マイニング構造の作成時に、この列をキーとして定義済みであるためです。</span><span class="sxs-lookup"><span data-stu-id="08bf3-126">That is because you have already defined the column as a key when you created the mining structure.</span></span>  
  
 <span data-ttu-id="08bf3-127">残りの行では、新しいマイニング モデルにおける列の使用法を指定します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-127">The remaining lines specify the usage of the columns in the new mining model.</span></span> <span data-ttu-id="08bf3-128">次の構文を使用して、マイニングモデルの列が予測に使用されるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-128">You can specify that a column in the mining model will be used for prediction by using the following syntax:</span></span>  
  
```  
<column name> PREDICT,  
```  
  
 <span data-ttu-id="08bf3-129">使用法を指定しない場合は、データ マイニング構造列を一覧に含める必要がありません。</span><span class="sxs-lookup"><span data-stu-id="08bf3-129">If you do not specify usage, you do not have to include a data mining structure column in the list.</span></span> <span data-ttu-id="08bf3-130">参照されたデータ マイニング構造で使用されているすべての列が、その構造に基づくマイニング モデルで自動的に使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="08bf3-130">All columns that are used by the referenced data mining structure are automatically available for use by the mining models that are based on that structure.</span></span> <span data-ttu-id="08bf3-131">ただし、使用法を指定していない列は、モデルのトレーニングに使用されません。</span><span class="sxs-lookup"><span data-stu-id="08bf3-131">However, the model will not use the columns for training unless you specify the usage.</span></span>  
  
 <span data-ttu-id="08bf3-132">コードの最後の行では、マイニング モデルの生成に使用するアルゴリズムとアルゴリズム パラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-132">The last line in the code defines the algorithm and algorithm parameters that will be used to generate the mining model.</span></span>  
  
```  
) USING <algorithm>( <algorithm parameters> )  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="08bf3-133">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="08bf3-133">Lesson Tasks</span></span>  
 <span data-ttu-id="08bf3-134">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-134">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="08bf3-135">既定の確率を使用して、アソシエーション マイニング モデルを構造に追加します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-135">Add an association mining model to the structure using the default probability</span></span>  
  
-   <span data-ttu-id="08bf3-136">変更した確率を使用して、アソシエーション マイニング モデルを構造に追加します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-136">Add an association mining model to the structure using a modified probability</span></span>  
  
## <a name="adding-an-association-mining-model-to-the-structure-using-the-default-minimum_probability"></a><span data-ttu-id="08bf3-137">既定の MINIMUM_PROBABILITY を使用した、構造への Association マイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="08bf3-137">Adding an Association Mining Model to the Structure Using the Default MINIMUM_PROBABILITY</span></span>  
 <span data-ttu-id="08bf3-138">最初のタスクでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] *MINIMUM_PROBABILITY*の既定値を使用して、アソシエーションアルゴリズムに基づいて新しいマイニングモデルをマーケットバスケットマイニング構造に追加します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-138">The first task is to add a new mining model to the Market Basket mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm using the default value for *MINIMUM_PROBABILITY*.</span></span>  
  
#### <a name="to-add-an-association-mining-model"></a><span data-ttu-id="08bf3-139">Association マイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="08bf3-139">To add an Association mining model</span></span>  
  
1.  <span data-ttu-id="08bf3-140">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-140">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="08bf3-141">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-141">Query Editor opens and contains a new, blank query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08bf3-142">特定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに対する DMX クエリを作成するには、インスタンスではなくデータベースを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-142">To create a DMX query against a specific [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, right-click the database instead of the instance.</span></span>  
  
2.  <span data-ttu-id="08bf3-143">`ALTER MINING STRUCTURE` ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-143">Copy the generic example of the `ALTER MINING STRUCTURE` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="08bf3-144">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-144">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="08bf3-145">with:</span><span class="sxs-lookup"><span data-stu-id="08bf3-145">with:</span></span>  
  
    ```  
    [Market Basket]  
    ```  
  
4.  <span data-ttu-id="08bf3-146">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-146">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="08bf3-147">with:</span><span class="sxs-lookup"><span data-stu-id="08bf3-147">with:</span></span>  
  
    ```  
    [Default Association]  
    ```  
  
5.  <span data-ttu-id="08bf3-148">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-148">Replace the following:</span></span>  
  
    ```  
    [<key column>],  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     <span data-ttu-id="08bf3-149">with:</span><span class="sxs-lookup"><span data-stu-id="08bf3-149">with:</span></span>  
  
    ```  
    OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     <span data-ttu-id="08bf3-150">この場合、`[Products]` テーブルは予測可能列として指定されています。`.`また、`[Model]` 列は入れ子になったテーブルのキー列であるため、入れ子になったテーブル列の一覧に含まれています。</span><span class="sxs-lookup"><span data-stu-id="08bf3-150">In this case, the `[Products]` table has been designated as the predictable column`.` Also, the `[Model]` column is included in the list of nested table columns because it is the key column of the nested table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08bf3-151">入れ子になったキーは、ケース キーとは異なります。</span><span class="sxs-lookup"><span data-stu-id="08bf3-151">Remember that a nested key is different from a case key.</span></span> <span data-ttu-id="08bf3-152">Case キーは、大文字小文字を区別する一意の識別子ですが、入れ子になったキーはモデル化する属性です。</span><span class="sxs-lookup"><span data-stu-id="08bf3-152">A case key is a unique identifier of the case, whereas the nested key is an attribute that you want to model.</span></span>  
  
6.  <span data-ttu-id="08bf3-153">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-153">Replace the following:</span></span>  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="08bf3-154">with:</span><span class="sxs-lookup"><span data-stu-id="08bf3-154">with:</span></span>  
  
    ```  
    Using Microsoft_Association_Rules  
    ```  
  
     <span data-ttu-id="08bf3-155">これで、ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="08bf3-155">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Default Association]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    Using Microsoft_Association_Rules  
    ```  
  
7.  <span data-ttu-id="08bf3-156">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-156">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="08bf3-157">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Default_Association_Model.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-157">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Default_Association_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="08bf3-158">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-158">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-an-association-mining-model-to-the-structure-changing-the-default-minimum_probability"></a><span data-ttu-id="08bf3-159">既定の MINIMUM_PROBABILITY を変更した値による、構造への Association マイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="08bf3-159">Adding an Association Mining Model to the Structure Changing the Default MINIMUM_PROBABILITY</span></span>  
 <span data-ttu-id="08bf3-160">次に、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムに基づいて、Market Basket マイニング構造に別のマイニング モデルを追加します。このとき、MINIMUM_PROBABILITY の既定値を 0.01 に変更します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-160">The next task is to add a new mining model to the Market Basket mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm, and change the default value for MINIMUM_PROBABILITY to 0.01.</span></span> <span data-ttu-id="08bf3-161">パラメーターを変更すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムによってさらに多くのルールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-161">Changing the parameter will cause the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm to create more rules.</span></span>  
  
#### <a name="to-add-an-association-mining-model"></a><span data-ttu-id="08bf3-162">Association マイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="08bf3-162">To add an Association mining model</span></span>  
  
1.  <span data-ttu-id="08bf3-163">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-163">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="08bf3-164">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-164">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="08bf3-165">`ALTER MINING STRUCTURE` ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-165">Copy the generic example of the `ALTER MINING STRUCTURE` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="08bf3-166">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-166">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="08bf3-167">with:</span><span class="sxs-lookup"><span data-stu-id="08bf3-167">with:</span></span>  
  
    ```  
    Market Basket  
    ```  
  
4.  <span data-ttu-id="08bf3-168">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-168">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="08bf3-169">with:</span><span class="sxs-lookup"><span data-stu-id="08bf3-169">with:</span></span>  
  
    ```  
    [Modified Association]  
    ```  
  
5.  <span data-ttu-id="08bf3-170">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-170">Replace the following:</span></span>  
  
    ```  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     <span data-ttu-id="08bf3-171">with:</span><span class="sxs-lookup"><span data-stu-id="08bf3-171">with:</span></span>  
  
    ```  
    OrderNumber,  
    [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     <span data-ttu-id="08bf3-172">この場合、`[Products]` テーブルは予測可能列として指定されています。</span><span class="sxs-lookup"><span data-stu-id="08bf3-172">In this case, the `[Products]` table has been designated as the predictable column.</span></span> <span data-ttu-id="08bf3-173">また、`[MODEL]` 列は入れ子になったテーブルのキー列であるため、一覧に含まれています。</span><span class="sxs-lookup"><span data-stu-id="08bf3-173">Also, the `[MODEL]` column is included in the list because it is the key column in the nested table.</span></span>  
  
6.  <span data-ttu-id="08bf3-174">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-174">Replace the following:</span></span>  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="08bf3-175">with:</span><span class="sxs-lookup"><span data-stu-id="08bf3-175">with:</span></span>  
  
    ```  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
     <span data-ttu-id="08bf3-176">これで、ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="08bf3-176">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Modified Assocation]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
7.  <span data-ttu-id="08bf3-177">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-177">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="08bf3-178">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Modified Association_Model.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="08bf3-178">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Modified Association_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="08bf3-179">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="08bf3-179">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="08bf3-180">次のレッスンでは、Market Basket マイニング構造とそれに関連するマイニング モデルを処理します。</span><span class="sxs-lookup"><span data-stu-id="08bf3-180">In this next lesson you will process the Market Basket mining structure together with its associated mining models.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="08bf3-181">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="08bf3-181">Next Lesson</span></span>  
 [<span data-ttu-id="08bf3-182">レッスン 3: Market Basket マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="08bf3-182">Lesson 3: Processing the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
  
  
