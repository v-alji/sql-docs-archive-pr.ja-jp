---
title: 'レッスン 1: マーケットバスケットのマイニング構造を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719100"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a><span data-ttu-id="91231-102">レッスン 1: Market Basket マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="91231-102">Lesson 1: Creating the Market Basket Mining Structure</span></span>
  <span data-ttu-id="91231-103">このレッスンでは、同時に購入される可能性が高い [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の製品を予測するためのマイニング構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="91231-103">In this lesson, you will create a mining structure that allows you to predict what [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] products a customer tends to purchase at the same time.</span></span> <span data-ttu-id="91231-104">データマイニングでのマイニング構造とそのロールの詳細については、「[マイニング構造 &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91231-104">If you are unfamiliar with mining structures and their role in data mining, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="91231-105">このレッスンで作成するアソシエーションマイニング構造では、 [Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)に基づくマイニングモデルの追加をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="91231-105">The association mining structure that you will create in this lesson supports adding mining models based on the [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md).</span></span> <span data-ttu-id="91231-106">後のレッスンでは、マイニング モデルを使用して、同時に購入される可能性が高い製品の種類を予測します。これはマーケット バスケット分析と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="91231-106">In later lessons, you will use the mining models to predict the type of products a customer tends to purchase at the same time, which is called a market basket analysis.</span></span> <span data-ttu-id="91231-107">たとえば、この予測で、マウンテン バイクとタイヤ、およびヘルメットが同時に購入される傾向にあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="91231-107">For example, you may find that customers tend to buy mountain bikes, bike tires, and helmets at the same time.</span></span>  
  
 <span data-ttu-id="91231-108">このレッスンでは、入れ子になったテーブルを使用してマイニング構造を定義します。</span><span class="sxs-lookup"><span data-stu-id="91231-108">In this lesson, the mining structure is defined by using nested tables.</span></span> <span data-ttu-id="91231-109">入れ子になったテーブルを使用するのは、マイニング構造で定義するデータ ドメインが、2 つの異なるソース テーブル内に含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="91231-109">Nested tables are used because the data domain that will be defined by the structure is contained within two different source tables.</span></span> <span data-ttu-id="91231-110">入れ子になったテーブルの詳細については、「[入れ子になったテーブル &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91231-110">For more information on nested tables, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
## <a name="create-mining-structure-statement"></a><span data-ttu-id="91231-111">CREATE マイニング構造ステートメント</span><span class="sxs-lookup"><span data-stu-id="91231-111">CREATE MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="91231-112">入れ子になったテーブルを含むマイニング構造を作成するには、 [CREATE マイニング structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="91231-112">In order to create a mining structure containing a nested table, you use the [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span> <span data-ttu-id="91231-113">ステートメント内のコードは、次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="91231-113">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="91231-114">構造の名前指定</span><span class="sxs-lookup"><span data-stu-id="91231-114">Naming the structure</span></span>  
  
-   <span data-ttu-id="91231-115">キー列の定義</span><span class="sxs-lookup"><span data-stu-id="91231-115">Defining the key column</span></span>  
  
-   <span data-ttu-id="91231-116">マイニング列の定義</span><span class="sxs-lookup"><span data-stu-id="91231-116">Defining the mining columns</span></span>  
  
-   <span data-ttu-id="91231-117">入れ子になったテーブル列の定義</span><span class="sxs-lookup"><span data-stu-id="91231-117">Defining the nested table columns</span></span>  
  
 <span data-ttu-id="91231-118">CREATE MINING STRUCTURE ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="91231-118">The following is a generic example of the CREATE MINING STRUCTURE statement:</span></span>  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 <span data-ttu-id="91231-119">コードの 1 行目では、構造の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="91231-119">The first line of the code defines the name of the structure:</span></span>  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 <span data-ttu-id="91231-120">DMX でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91231-120">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="91231-121">コードの次の行では、マイニング構造のキー列を定義します。キー列は、ソース データ内のエンティティを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="91231-121">The next line of the code defines the key column for the mining structure, which uniquely identifies an entity in the source data:</span></span>  
  
```  
<key column>  
```  
  
 <span data-ttu-id="91231-122">その次の行では、マイニング構造に関連付けられたマイニング モデルで使用される、マイニング列を定義します。</span><span class="sxs-lookup"><span data-stu-id="91231-122">The next line of the code is used to define the mining columns that will be used by the mining models associated with the mining structure:</span></span>  
  
```  
<mining structure columns>  
```  
  
 <span data-ttu-id="91231-123">コードの次の行では、入れ子になったテーブル列を定義します。</span><span class="sxs-lookup"><span data-stu-id="91231-123">The next lines of the code define the nested table columns:</span></span>  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 <span data-ttu-id="91231-124">定義できるマイニング構造列の種類の詳細については、「[マイニング構造列](../../2014/analysis-services/data-mining/mining-structure-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91231-124">For information about the types of mining structure columns that you can define, see [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91231-125">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、既定で、マイニング構造ごとに 30% の予約データ セットが作成されます。ただし、DMX を使用してマイニング構造を作成する場合は、必要に応じて予約データ セットを手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91231-125">By default, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] creates a 30 percent holdout data set for each mining structure; however, when you use DMX to create a mining structure, you must manually add the holdout data set, if desired.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="91231-126">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="91231-126">Lesson Tasks</span></span>  
 <span data-ttu-id="91231-127">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="91231-127">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="91231-128">新しい空のクエリの作成</span><span class="sxs-lookup"><span data-stu-id="91231-128">Create a new blank query</span></span>  
  
-   <span data-ttu-id="91231-129">マイニング構造を作成するためのクエリの変更</span><span class="sxs-lookup"><span data-stu-id="91231-129">Alter the query to create the mining structure</span></span>  
  
-   <span data-ttu-id="91231-130">クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="91231-130">Execute the query</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="91231-131">クエリの作成</span><span class="sxs-lookup"><span data-stu-id="91231-131">Creating the Query</span></span>  
 <span data-ttu-id="91231-132">最初の手順では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のインスタンスに接続して新しい DMX クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="91231-132">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="91231-133">SQL Server Management Studio で新しい DMX クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="91231-133">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="91231-134">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="91231-134">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="91231-135">[**サーバーへの接続**] ダイアログボックスの [**サーバーの種類**] で、[ **Analysis Services**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="91231-135">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="91231-136">[**サーバー名**] に、 `LocalHost` このレッスンで接続するのインスタンスの名前またはを入力し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="91231-136">In **Server name**, type `LocalHost`, or the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="91231-137">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="91231-137">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="91231-138">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="91231-138">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="91231-139">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="91231-139">Query Editor opens and contains a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="91231-140">クエリの変更</span><span class="sxs-lookup"><span data-stu-id="91231-140">Altering the Query</span></span>  
 <span data-ttu-id="91231-141">次の手順では、上の CREATE MINING STRUCTURE ステートメントを変更し、Market Basket マイニング構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="91231-141">The next step is to modify the CREATE MINING STRUCTURE statement described above to create the Market Basket mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a><span data-ttu-id="91231-142">CREATE MINING STRUCTURE ステートメントをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="91231-142">To customize the CREATE MINING STRUCTURE statement</span></span>  
  
1.  <span data-ttu-id="91231-143">クエリエディターで、CREATE マイニング STRUCTURE ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="91231-143">In Query Editor, copy the generic example of the CREATE MINING STRUCTURE statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="91231-144">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="91231-144">Replace the following:</span></span>  
  
    ```  
    [mining structure name]   
    ```  
  
     <span data-ttu-id="91231-145">with:</span><span class="sxs-lookup"><span data-stu-id="91231-145">with:</span></span>  
  
    ```  
    [Market Basket]  
    ```  
  
3.  <span data-ttu-id="91231-146">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="91231-146">Replace the following:</span></span>  
  
    ```  
    <key column>  
    ```  
  
     <span data-ttu-id="91231-147">with:</span><span class="sxs-lookup"><span data-stu-id="91231-147">with:</span></span>  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  <span data-ttu-id="91231-148">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="91231-148">Replace the following:</span></span>  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     <span data-ttu-id="91231-149">with:</span><span class="sxs-lookup"><span data-stu-id="91231-149">with:</span></span>  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     <span data-ttu-id="91231-150">TEXT KEY 言語は、Model 列が入れ子になったテーブルのキー列であることを示します。</span><span class="sxs-lookup"><span data-stu-id="91231-150">The TEXT KEY language specifies that the Model column is the key column for the nested table.</span></span>  
  
     <span data-ttu-id="91231-151">最終的なマイニング構造のステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="91231-151">The complete mining structure statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  <span data-ttu-id="91231-152">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="91231-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="91231-153">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Market Basket Structure.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="91231-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Market Basket Structure.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="91231-154">クエリの実行</span><span class="sxs-lookup"><span data-stu-id="91231-154">Executing the Query</span></span>  
 <span data-ttu-id="91231-155">最後の手順では、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="91231-155">The final step is to execute the query.</span></span> <span data-ttu-id="91231-156">クエリを作成して保存したら、サーバー上にマイニング構造を作成するためクエリを実行 (ステートメントを実行) します。</span><span class="sxs-lookup"><span data-stu-id="91231-156">After a query is created and saved, it needs to be executed (that is, the statement needs to be run) in order to create the mining structure on the server.</span></span> <span data-ttu-id="91231-157">クエリエディターでのクエリの実行の詳細については、「[データベースエンジンクエリエディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91231-157">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="91231-158">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="91231-158">To execute the query</span></span>  
  
-   <span data-ttu-id="91231-159">クエリエディターのツールバーで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="91231-159">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="91231-160">クエリの状態は、ステートメントの実行が完了した後、クエリエディターの下部にある [**メッセージ**] タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="91231-160">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="91231-161">この場合次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="91231-161">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="91231-162">**マーケットバスケット**という名前の新しい構造がサーバーに存在するようになりました。</span><span class="sxs-lookup"><span data-stu-id="91231-162">A new structure named **Market Basket** now exists on the server.</span></span>  
  
 <span data-ttu-id="91231-163">次のレッスンでは、作成した Market Basket マイニング構造にマイニング モデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="91231-163">In the next lesson, you will add mining models to the Market Basket mining structure you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="91231-164">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="91231-164">Next Lesson</span></span>  
 [<span data-ttu-id="91231-165">レッスン 2: Market Basket マイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="91231-165">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
