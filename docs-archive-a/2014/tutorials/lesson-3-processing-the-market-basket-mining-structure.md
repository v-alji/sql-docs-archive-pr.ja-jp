---
title: 'レッスン 3: マーケットバスケットマイニング構造の処理 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce2c2e6944d524a38edc331d2cd128ca7cf7d419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711198"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a><span data-ttu-id="5f4a3-102">レッスン 3: Market Basket マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="5f4a3-102">Lesson 3: Processing the Market Basket Mining Structure</span></span>
  <span data-ttu-id="5f4a3-103">このレッスンでは、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用し、サンプルデータベースの VAssocSeqLineItems と vAssocSeqOrders を使用して、「 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] [レッスン 1: マーケットバスケットマイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)」および「[レッスン 2: マーケットバスケットマイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)」で作成したマイニング構造とマイニングモデルを処理します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-103">In this lesson, you will use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement and the vAssocSeqLineItems and vAssocSeqOrders from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database to process the mining structures and mining models that you created in [Lesson 1: Creating the Market Basket Mining Structure](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) and [Lesson 2: Adding Mining Models to the Market Basket Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span>  
  
 <span data-ttu-id="5f4a3-104">マイニング構造の処理では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でソース データが読み込まれ、マイニング モデルをサポートする構造が構築されます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="5f4a3-105">マイニングモデルを処理する場合、マイニング構造によって定義されるデータは、選択したデータマイニングアルゴリズムによって渡されます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-105">When you process a mining model, the data defined by the mining structure is passed through the data mining algorithm that you chose.</span></span> <span data-ttu-id="5f4a3-106">このアルゴリズムでは傾向とパターンが検索され、結果の情報がマイニング モデルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-106">The algorithm searches for trends and patterns, and then stores this information in the mining model.</span></span> <span data-ttu-id="5f4a3-107">したがって、マイニング モデルには、実際のソース データではなく、アルゴリズムで検出された情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-107">The mining model, therefore, does not contain the actual source data, but instead contains the information that was discovered by the algorithm.</span></span> <span data-ttu-id="5f4a3-108">マイニングモデルの処理の詳細については、「[データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
 <span data-ttu-id="5f4a3-109">マイニング構造の再処理は、構造列またはソース データを変更した場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-109">You only have to reprocess a mining structure if you change a structure column or change the source data.</span></span> <span data-ttu-id="5f4a3-110">処理済みのマイニング構造にマイニング モデルを追加する場合は、`INSERT INTO MINING MODEL` ステートメントを使用して既存のデータに対して新しいマイニング モデルをトレーニングできます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-110">If you add a mining model to a mining structure that has already been processed, you can use the `INSERT INTO MINING MODEL` statement to train the new mining model on the existing data.</span></span>  
  
 <span data-ttu-id="5f4a3-111">Market Basket マイニング構造には入れ子になったテーブルが含まれるため、入れ子になったテーブル構造でトレーニングするようにマイニング列を定義する必要があります。また、`SHAPE` コマンドを使用して、ソース テーブルからトレーニング データを抽出するクエリを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-111">Because the Market Basket mining structure contains a nested table, you will have to define the mining columns to be trained using the nested table structure, and use the `SHAPE` command to define the queries that pull the training data from the source tables.</span></span>  
  
## <a name="insert-into-statement"></a><span data-ttu-id="5f4a3-112">INSERT INTO ステートメント</span><span class="sxs-lookup"><span data-stu-id="5f4a3-112">INSERT INTO Statement</span></span>  
 <span data-ttu-id="5f4a3-113">マーケットバスケットのマイニング構造とそれに関連付けられているマイニングモデルをトレーニングするには、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-113">In order to train the Market Basket mining structure and its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="5f4a3-114">ステートメントのコードは次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-114">The code in the statement can be broken into the following parts.</span></span>  
  
-   <span data-ttu-id="5f4a3-115">マイニング構造の指定</span><span class="sxs-lookup"><span data-stu-id="5f4a3-115">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="5f4a3-116">マイニング構造の列の一覧</span><span class="sxs-lookup"><span data-stu-id="5f4a3-116">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="5f4a3-117">`SHAPE` によるトレーニング データの定義</span><span class="sxs-lookup"><span data-stu-id="5f4a3-117">Defining the training data using `SHAPE`</span></span>  
  
 <span data-ttu-id="5f4a3-118">`INSERT INTO` ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-118">The following is a generic example of the `INSERT INTO` statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],'<nested SELECT statement>')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 <span data-ttu-id="5f4a3-119">コードの最初の行では、トレーニングするマイニング構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-119">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="5f4a3-120">コードの次の数行では、マイニング構造で定義される列を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-120">The next lines of the code specify the columns that are defined by the mining structure.</span></span> <span data-ttu-id="5f4a3-121">ここではマイニング構造の各列を指定する必要があります。各列はソース クエリ データ内の列にマップされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-121">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span> <span data-ttu-id="5f4a3-122">`SKIP` を使用すると、ソース データに存在するがマイニング構造に存在しない列を無視できます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-122">You can use `SKIP` to ignore columns that exist in the source data but do not exist in the mining structure.</span></span> <span data-ttu-id="5f4a3-123">の使用方法の詳細について `SKIP` は、「 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-123">For more information about how to use `SKIP`, see [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx).</span></span>  
  
```  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
```  
  
 <span data-ttu-id="5f4a3-124">コードの最後の行では、マイニング構造のトレーニングに使用されるデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-124">The final lines of the code define the data that will be used to train the mining structure.</span></span> <span data-ttu-id="5f4a3-125">ソース データは 2 つのテーブルに格納されているため、`SHAPE` を使用してテーブルを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-125">Because the source data is contained within two tables, you will use `SHAPE` to relate the tables.</span></span>  
  
```  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],''<nested SELECT statement>'')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 <span data-ttu-id="5f4a3-126">このレッスンでは、`OPENQUERY` を使用してソース データを定義します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-126">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="5f4a3-127">ソースデータに対するクエリを定義するその他の方法については、「 [&#60;source data query&#62;](/sql/dmx/source-data-query)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-127">For information about other methods of defining a query on the source data, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="5f4a3-128">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="5f4a3-128">Lesson Tasks</span></span>  
 <span data-ttu-id="5f4a3-129">このレッスンでは、次の作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-129">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="5f4a3-130">マーケットバスケットのマイニング構造を処理する</span><span class="sxs-lookup"><span data-stu-id="5f4a3-130">Process the Market Basket mining structure</span></span>  
  
## <a name="processing-the-market-basket-mining-structure"></a><span data-ttu-id="5f4a3-131">Market Basket マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="5f4a3-131">Processing the Market Basket Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a><span data-ttu-id="5f4a3-132">INSERT INTO を使用してマイニング構造を処理するには</span><span class="sxs-lookup"><span data-stu-id="5f4a3-132">To process the mining structure by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="5f4a3-133">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-133">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="5f4a3-134">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-134">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="5f4a3-135">上の INSERT INTO ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-135">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="5f4a3-136">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-136">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]  
    ```  
  
     <span data-ttu-id="5f4a3-137">with:</span><span class="sxs-lookup"><span data-stu-id="5f4a3-137">with:</span></span>  
  
    ```  
    Market Basket  
    ```  
  
4.  <span data-ttu-id="5f4a3-138">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-138">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     <span data-ttu-id="5f4a3-139">with:</span><span class="sxs-lookup"><span data-stu-id="5f4a3-139">with:</span></span>  
  
    ```  
    [OrderNumber],  
    [Products]   
    (SKIP, [Model])  
    ```  
  
     <span data-ttu-id="5f4a3-140">このステートメントでは、`Products` は SHAPE ステートメントで定義される Products テーブルを参照します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-140">In the statement, `Products` refers to the Products table defined by the SHAPE statement.</span></span> <span data-ttu-id="5f4a3-141">`SKIP` は、ソース データにキーとして存在する Model 列を無視するために使用します。マイニング構造に対しては使用できません。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-141">`SKIP` is used to ignore the Model column, which exists in the source data as a key, but is not used by the mining structure.</span></span>  
  
5.  <span data-ttu-id="5f4a3-142">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-142">Replace the following:</span></span>  
  
    ```  
    SHAPE {  
      OPENQUERY([<datasource>],'<SELECT statement>') }  
    APPEND  
    (   
      {OPENQUERY([<datasource>],'<nested SELECT statement>')  
    }  
    RELATE [<case key>] TO [<foreign key>]  
    ) AS [<nested table>]  
    ```  
  
     <span data-ttu-id="5f4a3-143">with:</span><span class="sxs-lookup"><span data-stu-id="5f4a3-143">with:</span></span>  
  
    ```  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
     <span data-ttu-id="5f4a3-144">ソースクエリは、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプルプロジェクトで定義されているデータソースを参照し [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-144">The source query references the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source defined in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample project.</span></span> <span data-ttu-id="5f4a3-145">ソース クエリはこのデータ ソースを使用して、vAssocSeqLineItems ビューと vAssocSeqOrders ビューにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-145">It uses this data source to access the vAssocSeqLineItems and vAssocSeqOrders views.</span></span> <span data-ttu-id="5f4a3-146">これら 2 つのビューには、マイニング モデルのトレーニングに使用されるソース データが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-146">These views contain the source data that will be used to train the mining model.</span></span> <span data-ttu-id="5f4a3-147">このプロジェクトまたはこれらのビューを作成していない場合は、「[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-147">If you have not created this project or these views, see [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span>  
  
     <span data-ttu-id="5f4a3-148">`SHAPE` コマンド内では、`OPENQUERY` を使用して 2 つのクエリを定義します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-148">Within the `SHAPE` command, you will use `OPENQUERY` to define two queries.</span></span> <span data-ttu-id="5f4a3-149">最初のクエリでは親テーブルを定義し、2 つ目のクエリでは入れ子になったテーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-149">The first query defines the parent table, and the second query defines the nested table.</span></span> <span data-ttu-id="5f4a3-150">2 つのテーブルは、両方のテーブルに存在する OrderNumber 列を使用して関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-150">The two tables are related using the OrderNumber column, which exists in both tables.</span></span>  
  
     <span data-ttu-id="5f4a3-151">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-151">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Market Basket]  
    (  
       [OrderNumber],[Products] (SKIP, [Model])  
    )  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
6.  <span data-ttu-id="5f4a3-152">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="5f4a3-153">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Process Market Basket.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Process Market Basket.dmx`.</span></span>  
  
8.  <span data-ttu-id="5f4a3-154">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-154">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="5f4a3-155">クエリの実行終了後、見つかったパターンとアイテムセットを表示したり、関連付けを表示したり、アイテムセット、確率、または重要度でフィルタリングしたりできます。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-155">After the query has finished running, you can view the patterns and itemsets that were found, view associations, or filter by itemset, probability, or importance.</span></span> <span data-ttu-id="5f4a3-156">この情報を表示するには、で [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] データモデルの名前を右クリックし、[**参照**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-156">To view this information, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click the name of the data model, and then click **Browse**.</span></span>  
  
 <span data-ttu-id="5f4a3-157">次のレッスンでは、Market Basket 構造に追加したマイニング モデルに基づいて、いくつかの予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="5f4a3-157">In the next lesson, you will create several predictions based on the mining models that you added to the Market Basket structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="5f4a3-158">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="5f4a3-158">Next Lesson</span></span>  
 [<span data-ttu-id="5f4a3-159">レッスン 4: マーケット バスケット予測の実行</span><span class="sxs-lookup"><span data-stu-id="5f4a3-159">Lesson 4: Executing Market Basket Predictions</span></span>](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
