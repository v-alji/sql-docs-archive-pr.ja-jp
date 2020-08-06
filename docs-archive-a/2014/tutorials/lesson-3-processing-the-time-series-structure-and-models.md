---
title: 'レッスン 3: タイムシリーズの構造とモデルの処理 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717090"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a><span data-ttu-id="a8a78-102">レッスン 3: 時系列構造と時系列モデルの処理</span><span class="sxs-lookup"><span data-stu-id="a8a78-102">Lesson 3: Processing the Time Series Structure and Models</span></span>
  <span data-ttu-id="a8a78-103">このレッスンでは、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用して、作成した時系列マイニング構造とマイニングモデルを処理します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-103">In this lesson, you will use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement to process the time series mining structures and mining models that you created.</span></span>  
  
 <span data-ttu-id="a8a78-104">マイニング構造の処理では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でソース データが読み込まれ、マイニング モデルをサポートする構造が構築されます。</span><span class="sxs-lookup"><span data-stu-id="a8a78-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="a8a78-105">マイニング モデルとマイニング構造は、最初に作成したときに必ず処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8a78-105">You always have to process a mining model and structure when you first create it.</span></span> <span data-ttu-id="a8a78-106">INSERT INTO を使用する場合、マイニング構造を指定すると、ステートメントによってマイニング構造とそれに関連するすべてのマイニング モデルが処理されます。</span><span class="sxs-lookup"><span data-stu-id="a8a78-106">If you specify the mining structure when using INSERT INTO, the statement processes the mining structure and all its associated mining models.</span></span>  
  
 <span data-ttu-id="a8a78-107">処理済みのマイニング構造にマイニング モデルを追加する場合は、`INSERT INTO MINING MODEL` ステートメントを使用することにより、既存のデータを使用して新しいマイニング モデルのみを処理できます。</span><span class="sxs-lookup"><span data-stu-id="a8a78-107">When you add a mining model to a mining structure that has already been processed, you can use the `INSERT INTO MINING MODEL` statement to process just the new mining model by using the existing data.</span></span>  
  
 <span data-ttu-id="a8a78-108">マイニングモデルの処理の詳細については、「[データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8a78-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
## <a name="insert-into-statement"></a><span data-ttu-id="a8a78-109">INSERT INTO ステートメント</span><span class="sxs-lookup"><span data-stu-id="a8a78-109">INSERT INTO Statement</span></span>  
 <span data-ttu-id="a8a78-110">タイムシリーズマイニング構造とそれに関連付けられているすべてのマイニングモデルをトレーニングするには、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-110">In order to train the time series mining structure and all its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="a8a78-111">ステートメントのコードは次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="a8a78-111">The code in the statement can be broken into the following parts.</span></span>  
  
-   <span data-ttu-id="a8a78-112">マイニング構造の指定</span><span class="sxs-lookup"><span data-stu-id="a8a78-112">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="a8a78-113">マイニング構造の列の一覧</span><span class="sxs-lookup"><span data-stu-id="a8a78-113">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="a8a78-114">トレーニング データの定義</span><span class="sxs-lookup"><span data-stu-id="a8a78-114">Defining the training data</span></span>  
  
 <span data-ttu-id="a8a78-115">`INSERT INTO` ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-115">The following is a generic example of the `INSERT INTO` statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 <span data-ttu-id="a8a78-116">コードの最初の行では、トレーニングするマイニング構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-116">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="a8a78-117">コードの次の数行では、マイニング構造で定義される列を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-117">The next lines of the code specify the columns that are defined by the mining structure.</span></span> <span data-ttu-id="a8a78-118">ここではマイニング構造の各列を指定する必要があります。各列はソース クエリ データ内の列にマップされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8a78-118">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span>  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 <span data-ttu-id="a8a78-119">コードの最後の行では、マイニング構造のトレーニングに使用されるデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-119">The final lines of the code define the data that will be used to train the mining structure.</span></span>  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 <span data-ttu-id="a8a78-120">このレッスンでは、`OPENQUERY` を使用してソース データを定義します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-120">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="a8a78-121">ソースデータに対するクエリを定義するその他の方法の詳細については、「 [&#60;source data query&#62;](/sql/dmx/source-data-query)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8a78-121">For more information about other methods of defining a query on the source data, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="a8a78-122">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="a8a78-122">Lesson Tasks</span></span>  
 <span data-ttu-id="a8a78-123">このレッスンでは、次の作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-123">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="a8a78-124">マイニング構造 Forecasting_MIXED_Structure の処理</span><span class="sxs-lookup"><span data-stu-id="a8a78-124">Process the mining structure Forecasting_MIXED_Structure</span></span>  
  
-   <span data-ttu-id="a8a78-125">関連するマイニング モデル Forecasting_MIXED、Forecasting_ARIMA、および Forecasting_ARTXP の処理</span><span class="sxs-lookup"><span data-stu-id="a8a78-125">Process the related mining models Forecasting_MIXED, Forecasting_ARIMA, and Forecasting_ARTXP</span></span>  
  
## <a name="processing-the-time-series-mining-structure"></a><span data-ttu-id="a8a78-126">時系列マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="a8a78-126">Processing the Time Series Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a><span data-ttu-id="a8a78-127">INSERT INTO を使用してマイニング構造とそれに関連するマイニング モデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="a8a78-127">To process the mining structure and related mining models by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="a8a78-128">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8a78-128">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="a8a78-129">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8a78-129">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="a8a78-130">上の INSERT INTO ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8a78-130">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="a8a78-131">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-131">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]  
    ```  
  
     <span data-ttu-id="a8a78-132">with:</span><span class="sxs-lookup"><span data-stu-id="a8a78-132">with:</span></span>  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  <span data-ttu-id="a8a78-133">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-133">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    ```  
  
     <span data-ttu-id="a8a78-134">with:</span><span class="sxs-lookup"><span data-stu-id="a8a78-134">with:</span></span>  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  <span data-ttu-id="a8a78-135">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-135">Replace the following:</span></span>  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     <span data-ttu-id="a8a78-136">with:</span><span class="sxs-lookup"><span data-stu-id="a8a78-136">with:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     <span data-ttu-id="a8a78-137">ソースクエリは、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] IntermediateTutorial サンプルプロジェクトで定義されているデータソースを参照します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-137">The source query references the  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source defined in the IntermediateTutorial sample project.</span></span> <span data-ttu-id="a8a78-138">ソース クエリはこのデータ ソースを使用して、vTimeSeries ビューにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="a8a78-138">It uses this data source to access the view vTimeSeries.</span></span> <span data-ttu-id="a8a78-139">このビューには、マイニング モデルのトレーニングに使用されるソース データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a8a78-139">This view contains the source data that will be used to train the mining model.</span></span> <span data-ttu-id="a8a78-140">このプロジェクトまたはこのビューに慣れていない場合は、「[レッスン 2: 予測シナリオの構築」 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8a78-140">If you are not familiar with this project or this views, see[Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
     <span data-ttu-id="a8a78-141">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a8a78-141">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  <span data-ttu-id="a8a78-142">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8a78-142">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="a8a78-143">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `ProcessForecastingAll.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="a8a78-143">In the **Save As** dialog box, browse to the appropriate folder, and name the file `ProcessForecastingAll.dmx`.</span></span>  
  
8.  <span data-ttu-id="a8a78-144">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8a78-144">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="a8a78-145">クエリの実行が終了したら、処理済みのマイニング モデルを使用して予測を作成できます。</span><span class="sxs-lookup"><span data-stu-id="a8a78-145">After the query has finished running, you can create predictions by using the processed mining models.</span></span> <span data-ttu-id="a8a78-146">次のレッスンでは、作成したマイニング モデルに基づいて、いくつかの予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8a78-146">In the next lesson, you will create several predictions based on the mining models that you created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="a8a78-147">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="a8a78-147">Next Lesson</span></span>  
 [<span data-ttu-id="a8a78-148">レッスン 4: DMX を使用した時系列予測の作成</span><span class="sxs-lookup"><span data-stu-id="a8a78-148">Lesson 4: Creating Time Series Predictions Using DMX</span></span>](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a><span data-ttu-id="a8a78-149">参照</span><span class="sxs-lookup"><span data-stu-id="a8a78-149">See Also</span></span>  
 <span data-ttu-id="a8a78-150">[データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a8a78-150">[Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) </span></span>  
 <span data-ttu-id="a8a78-151">[&#60;ソースデータクエリ&#62;](/sql/dmx/source-data-query) </span><span class="sxs-lookup"><span data-stu-id="a8a78-151">[&#60;source data query&#62;](/sql/dmx/source-data-query) </span></span>  
 [<span data-ttu-id="a8a78-152">OPENQUERY &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a8a78-152">OPENQUERY &#40;DMX&#41;</span></span>](/sql/dmx/source-data-query-openquery)  
  
  
