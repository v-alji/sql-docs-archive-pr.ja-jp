---
title: 'レッスン 1: 自転車購入者マイニング構造の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719095"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a><span data-ttu-id="efa65-102">レッスン 1: Bike Buyer マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="efa65-102">Lesson 1: Creating the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="efa65-103">このレッスンでは、[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の潜在顧客が自転車を購入するかどうかを予測するためのマイニング構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="efa65-103">In this lesson, you will create a mining structure that allows you to predict whether a potential customer of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] will purchase a bicycle.</span></span> <span data-ttu-id="efa65-104">データマイニングでのマイニング構造とそのロールの詳細については、「[マイニング構造 &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efa65-104">If you are unfamiliar with mining structures and their role in data mining, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="efa65-105">このレッスンで作成する自転車購入者マイニング構造は、microsoft[クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft デシジョンツリーアルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)に基づくマイニングモデルの追加をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="efa65-105">The Bike Buyer mining structure that you will create in this lesson supports adding mining models based on the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md).</span></span> <span data-ttu-id="efa65-106">後のレッスンでは、クラスター マイニング モデルを使用して顧客をグループ化するさまざまな方法を確認し、デシジョン ツリー マイニング モデルを使用して潜在顧客が自転車を購入するかどうかを予測します。</span><span class="sxs-lookup"><span data-stu-id="efa65-106">In later lessons, you will use the clustering mining models to explore the different ways in which customers can be grouped, and will use decision tree mining models to predict whether or not a potential customer will purchase a bicycle.</span></span>  
  
## <a name="create-mining-structure-statement"></a><span data-ttu-id="efa65-107">CREATE マイニング構造ステートメント</span><span class="sxs-lookup"><span data-stu-id="efa65-107">CREATE MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="efa65-108">マイニング構造を作成するには、 [CREATE マイニング structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="efa65-108">To create a mining structure, you use the [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span> <span data-ttu-id="efa65-109">ステートメント内のコードは、次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="efa65-109">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="efa65-110">構造に名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="efa65-110">Naming the structure.</span></span>  
  
-   <span data-ttu-id="efa65-111">キー列を定義しています。</span><span class="sxs-lookup"><span data-stu-id="efa65-111">Defining the key column.</span></span>  
  
-   <span data-ttu-id="efa65-112">マイニング列の定義</span><span class="sxs-lookup"><span data-stu-id="efa65-112">Defining the mining columns.</span></span>  
  
-   <span data-ttu-id="efa65-113">省略可能なテスト データセットの定義</span><span class="sxs-lookup"><span data-stu-id="efa65-113">Defining an optional testing data set.</span></span>  
  
 <span data-ttu-id="efa65-114">CREATE MINING STRUCTURE ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="efa65-114">The following is a generic example of the CREATE MINING STRUCTURE statement:</span></span>  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 <span data-ttu-id="efa65-115">コードの 1 行目では、構造の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="efa65-115">The first line of the code defines the name of the structure:</span></span>  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="efa65-116">データマイニング拡張機能 (DMX) でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efa65-116">For information about naming an object in Data Mining Extensions (DMX), see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="efa65-117">コードの次の行では、マイニング構造のキー列を定義します。キー列は、ソース データ内のエンティティを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="efa65-117">The next line of the code defines the key column for the mining structure, which uniquely identifies an entity in the source data:</span></span>  
  
```  
<key column>,  
```  
  
 <span data-ttu-id="efa65-118">作成するマイニング構造では、顧客の識別子 `CustomerKey` でソース データ内のエンティティが定義されます。</span><span class="sxs-lookup"><span data-stu-id="efa65-118">In the mining structure you will create, the customer identifier, `CustomerKey`, defines an entity in the source data.</span></span>  
  
 <span data-ttu-id="efa65-119">その次の行では、マイニング構造に関連付けられたマイニング モデルで使用される、マイニング列を定義します。</span><span class="sxs-lookup"><span data-stu-id="efa65-119">The next line of the code is used to define the mining columns that will be used by the mining models associated with the mining structure:</span></span>  
  
```  
<mining structure columns>  
```  
  
 <span data-ttu-id="efa65-120">内の分離関数を使用すると、 \<mining structure columns> 次の構文を使用して連続列を分離できます。</span><span class="sxs-lookup"><span data-stu-id="efa65-120">You can use the DISCRETIZE function within \<mining structure columns> to discretize continuous columns by using the following syntax:</span></span>  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 <span data-ttu-id="efa65-121">分離列の詳細については、「[データマイニング&#41;&#40;分離メソッド](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efa65-121">For more information about discretizing columns, see [Discretization Methods &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).</span></span> <span data-ttu-id="efa65-122">定義できるマイニング構造列の種類の詳細については、「[マイニング構造列](../../2014/analysis-services/data-mining/mining-structure-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efa65-122">For more information about the types of mining structure columns that you can define, see [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md).</span></span>  
  
 <span data-ttu-id="efa65-123">コードの最後の行では、マイニング構造の省略可能なパーティションを定義します。</span><span class="sxs-lookup"><span data-stu-id="efa65-123">The final line of the code defines an optional partition in the mining structure:</span></span>  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 <span data-ttu-id="efa65-124">構造に関連するマイニング モデルのテストに使用するためにデータの一部を指定し、残りのデータはモデルのトレーニングに使用します。</span><span class="sxs-lookup"><span data-stu-id="efa65-124">You specify some portion of the data to use for testing mining models that are related to the structure, and the remaining data is used for training the models.</span></span> <span data-ttu-id="efa65-125">既定では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって、全ケース データの 30% から成るテスト データセットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="efa65-125">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates a test data set that contains 30 percent of all case data.</span></span> <span data-ttu-id="efa65-126">テスト データセットがケースの 30% になるように指定を追加します (最大 1000 ケース)。</span><span class="sxs-lookup"><span data-stu-id="efa65-126">You will add the specification that the test data set should contain 30 percent of the cases up to a maximum of 1000 cases.</span></span> <span data-ttu-id="efa65-127">ケースの 30% が 1000 より小さい場合、テスト データセットの量はもっと少なくなります。</span><span class="sxs-lookup"><span data-stu-id="efa65-127">If 30 percent of the cases is less than 1000, the test data set will contain the smaller amount.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="efa65-128">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="efa65-128">Lesson Tasks</span></span>  
 <span data-ttu-id="efa65-129">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="efa65-129">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="efa65-130">新しい空のクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="efa65-130">Create a new blank query.</span></span>  
  
-   <span data-ttu-id="efa65-131">マイニング構造を作成するようにクエリを変更します。</span><span class="sxs-lookup"><span data-stu-id="efa65-131">Alter the query to create the mining structure.</span></span>  
  
-   <span data-ttu-id="efa65-132">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="efa65-132">Execute the query.</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="efa65-133">クエリの作成</span><span class="sxs-lookup"><span data-stu-id="efa65-133">Creating the Query</span></span>  
 <span data-ttu-id="efa65-134">最初の手順では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のインスタンスに接続して新しい DMX クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="efa65-134">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="efa65-135">SQL Server Management Studio で新しい DMX クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="efa65-135">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="efa65-136">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="efa65-136">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="efa65-137">[**サーバーへの接続**] ダイアログボックスの [**サーバーの種類**] で、[ **Analysis Services**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="efa65-137">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="efa65-138">[**サーバー名**] に `LocalHost` 、このレッスンで接続するのインスタンスの名前を入力するか、入力し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="efa65-138">In **Server name**, type `LocalHost`, or type the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="efa65-139">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="efa65-139">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="efa65-140">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックして**クエリエディター**を開き、新しい空のクエリをクリックします。</span><span class="sxs-lookup"><span data-stu-id="efa65-140">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the **Query Editor** and a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="efa65-141">クエリの変更</span><span class="sxs-lookup"><span data-stu-id="efa65-141">Altering the Query</span></span>  
 <span data-ttu-id="efa65-142">次の手順では、上の CREATE MINING STRUCTURE ステートメントを変更し、Bike Buyer マイニング構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="efa65-142">The next step is to modify the CREATE MINING STRUCTURE statement described above to create the Bike Buyer mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a><span data-ttu-id="efa65-143">CREATE MINING STRUCTURE ステートメントをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="efa65-143">To customize the CREATE MINING STRUCTURE statement</span></span>  
  
1.  <span data-ttu-id="efa65-144">クエリ エディターで、CREATE MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="efa65-144">In the Query Editor, copy the generic example of the CREATE MINING STRUCTURE statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="efa65-145">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="efa65-145">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]   
    ```  
  
     <span data-ttu-id="efa65-146">with:</span><span class="sxs-lookup"><span data-stu-id="efa65-146">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  <span data-ttu-id="efa65-147">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="efa65-147">Replace the following:</span></span>  
  
    ```  
    <key column>   
    ```  
  
     <span data-ttu-id="efa65-148">with:</span><span class="sxs-lookup"><span data-stu-id="efa65-148">with:</span></span>  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  <span data-ttu-id="efa65-149">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="efa65-149">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>   
    ```  
  
     <span data-ttu-id="efa65-150">with:</span><span class="sxs-lookup"><span data-stu-id="efa65-150">with:</span></span>  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  <span data-ttu-id="efa65-151">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="efa65-151">Replace the following:</span></span>  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     <span data-ttu-id="efa65-152">with:</span><span class="sxs-lookup"><span data-stu-id="efa65-152">with:</span></span>  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     <span data-ttu-id="efa65-153">最終的なマイニング構造のステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="efa65-153">The complete mining structure statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  <span data-ttu-id="efa65-154">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="efa65-154">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="efa65-155">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Bike Buyer Structure.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="efa65-155">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Bike Buyer Structure.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="efa65-156">クエリの実行</span><span class="sxs-lookup"><span data-stu-id="efa65-156">Executing the Query</span></span>  
 <span data-ttu-id="efa65-157">最後の手順では、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="efa65-157">The final step is to execute the query.</span></span> <span data-ttu-id="efa65-158">クエリを作成して保存したら、そのクエリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efa65-158">After a query is created and saved, it needs to be executed.</span></span> <span data-ttu-id="efa65-159">つまり、サーバーでマイニング構造を作成するには、ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efa65-159">That is, the statement needs to be run in order to create the mining structure on the server.</span></span> <span data-ttu-id="efa65-160">クエリエディターでのクエリの実行の詳細については、「[データベースエンジンクエリエディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efa65-160">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="efa65-161">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="efa65-161">To execute the query</span></span>  
  
1.  <span data-ttu-id="efa65-162">クエリエディターのツールバーで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="efa65-162">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="efa65-163">クエリの状態は、ステートメントの実行が完了した後、クエリエディターの下部にある [**メッセージ**] タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="efa65-163">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="efa65-164">この場合次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="efa65-164">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="efa65-165">**自転車購入**者という名前の新しい構造がサーバーに存在するようになりました。</span><span class="sxs-lookup"><span data-stu-id="efa65-165">A new structure named **Bike Buyer** now exists on the server.</span></span>  
  
 <span data-ttu-id="efa65-166">次のレッスンでは、作成した構造にマイニング モデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="efa65-166">In the next lesson, you will add mining models to the structure you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="efa65-167">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="efa65-167">Next Lesson</span></span>  
 [<span data-ttu-id="efa65-168">レッスン 2: Bike Buyer マイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="efa65-168">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
