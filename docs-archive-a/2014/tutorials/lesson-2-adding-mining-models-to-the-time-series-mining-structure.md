---
title: 'レッスン 2: タイムシリーズマイニング構造へのマイニングモデルの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75c2a74b-21ce-44fb-a26b-68be4c685c12
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ae0bb91fafb53c0c077a4e0d82558b550d0e6070
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631434"
---
# <a name="lesson-2-adding-mining-models-to-the-time-series-mining-structure"></a><span data-ttu-id="28f19-102">レッスン 2: 時系列マイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="28f19-102">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>
  <span data-ttu-id="28f19-103">このレッスンでは、「[レッスン 1: タイムシリーズマイニングモデルとマイニング構造の作成](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)」で作成したマイニング構造に新しいマイニングモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="28f19-103">In this lesson, you will add a new mining model to the mining structure that you just created in [Lesson 1: Creating a Time Series Mining Model and Mining Structure](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md).</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="28f19-104">ALTER MINING STRUCTURE ステートメント</span><span class="sxs-lookup"><span data-stu-id="28f19-104">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="28f19-105">新しいマイニングモデルを既存のマイニング構造に追加するには、 [ALTER マイニング構造 &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="28f19-105">In order to add a new mining model to an existing mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="28f19-106">ステートメント内のコードは、次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="28f19-106">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="28f19-107">マイニング構造の指定</span><span class="sxs-lookup"><span data-stu-id="28f19-107">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="28f19-108">マイニング モデルの名前指定</span><span class="sxs-lookup"><span data-stu-id="28f19-108">Naming the mining model</span></span>  
  
-   <span data-ttu-id="28f19-109">キー列の定義</span><span class="sxs-lookup"><span data-stu-id="28f19-109">Defining the key column</span></span>  
  
-   <span data-ttu-id="28f19-110">予測可能列の定義</span><span class="sxs-lookup"><span data-stu-id="28f19-110">Defining the predictable columns</span></span>  
  
-   <span data-ttu-id="28f19-111">アルゴリズムとパラメーター変更の指定</span><span class="sxs-lookup"><span data-stu-id="28f19-111">Specifying the algorithm and any parameter changes</span></span>  
  
 <span data-ttu-id="28f19-112">ALTER MINING STRUCTURE ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="28f19-112">The following is a generic example of the ALTER MINING STRUCTURE statement:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
   ([<key columns>],  
    <mining model columns>  
   )  
USING <algorithm name>([<algorithm parameters>])  
[WITH DRILLTHROUGH]  
```  
  
 <span data-ttu-id="28f19-113">コードの最初の行では、マイニングモデルを追加する既存のマイニング構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="28f19-113">The first line of the code identifies the existing mining structure to which the mining models will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="28f19-114">コードの次の行では、マイニング構造に追加するマイニング モデルを指定します。</span><span class="sxs-lookup"><span data-stu-id="28f19-114">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="28f19-115">DMX でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f19-115">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="28f19-116">コードの次の数行では、マイニング モデルで使用するマイニング構造の列を定義します。</span><span class="sxs-lookup"><span data-stu-id="28f19-116">The next lines of the code define columns from the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key columns>],  
<mining model columns>  
```  
  
 <span data-ttu-id="28f19-117">使用できるのは、マイニング構造内に既に存在する列だけです。一覧の最初の列は、マイニング構造のキー列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="28f19-117">You can only use columns that already exist in the mining structure, and the first column in the list must be the key column from the mining structure.</span></span>  
  
 <span data-ttu-id="28f19-118">コードの次の行では、マイニング モデルを生成するマイニング アルゴリズムと、アルゴリズムに設定できるアルゴリズム パラメーターを定義し、マイニング モデルからトレーニング ケースの詳細データの表示にドリル ダウンできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="28f19-118">The next lines of the code defines the mining algorithm that generates the mining model and the algorithm parameters that you can set on the algorithm, and specify whether you can drill down from the mining model into view detailed data in the training cases:</span></span>  
  
```  
USING <algorithm name>([<algorithm parameters>])  
WITH DRILLTHROUGH  
```  
  
 <span data-ttu-id="28f19-119">調整できるアルゴリズムパラメーターの詳細については、「 [Microsoft タイムシリーズアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f19-119">For more information about the algorithm parameters that you can adjust, see [Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="28f19-120">次の構文で、マイニング モデルの列を予測に使用するよう指定できます。</span><span class="sxs-lookup"><span data-stu-id="28f19-120">You can specify that a column in the mining model be used for prediction by using the following syntax:</span></span>  
  
```  
<mining model column> PREDICT  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="28f19-121">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="28f19-121">Lesson Tasks</span></span>  
 <span data-ttu-id="28f19-122">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="28f19-122">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="28f19-123">新しい時系列マイニング モデルを構造に追加します。</span><span class="sxs-lookup"><span data-stu-id="28f19-123">Add a new time series mining model to the structure.</span></span>  
  
-   <span data-ttu-id="28f19-124">異なる分析方法と予測方法を使用するようにアルゴリズム パラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="28f19-124">Change the algorithm parameters to use a different method of analysis and prediction</span></span>  
  
## <a name="adding-an-arima-time-series-model-to-the-structure"></a><span data-ttu-id="28f19-125">構造への ARIMA 時系列モデルの追加</span><span class="sxs-lookup"><span data-stu-id="28f19-125">Adding an ARIMA Time Series Model to the Structure</span></span>  
 <span data-ttu-id="28f19-126">まず、新しい予測マイニング モデルを既存の構造に追加します。</span><span class="sxs-lookup"><span data-stu-id="28f19-126">The first step is to add a new forecasting mining model to the existing structure.</span></span> <span data-ttu-id="28f19-127">既定では、[!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムは、ARIMA および ARTXP の 2 つのアルゴリズムを使用し、その結果を組み合わせて時系列マイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="28f19-127">By default, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm creates time series mining models by using two algorithms, ARIMA and ARTXP, and blending the results.</span></span> <span data-ttu-id="28f19-128">ただし、アルゴリズムを 1 つだけ使用するように指定することも、正確なアルゴリズムの組み合わせを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="28f19-128">However, you can specify a single algorithm to use, or you can specify the exact blend of algorithms.</span></span> <span data-ttu-id="28f19-129">この手順では、ARIMA アルゴリズムのみを使用する新しいモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="28f19-129">In this step, you will add a new model that uses only the ARIMA algorithm.</span></span> <span data-ttu-id="28f19-130">このアルゴリズムは、長期的な予測に適しています。</span><span class="sxs-lookup"><span data-stu-id="28f19-130">This algorithm is optimized for long-term prediction.</span></span>  
  
#### <a name="to-add-an-arima-time-series-mining-model"></a><span data-ttu-id="28f19-131">ARIMA 時系列マイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="28f19-131">To add an ARIMA time series mining model</span></span>  
  
1.  <span data-ttu-id="28f19-132">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、[**新しいクエリ**] をポイントします。次に、[ **DMX** ] をクリックしてクエリエディターと、新しい空のクエリを開きます。</span><span class="sxs-lookup"><span data-stu-id="28f19-132">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="28f19-133">上の ALTER MINING STRUCTURE ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="28f19-133">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="28f19-134">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="28f19-134">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="28f19-135">with:</span><span class="sxs-lookup"><span data-stu-id="28f19-135">with:</span></span>  
  
    ```  
    [Forecasting_MIXED_Structure]  
    ```  
  
4.  <span data-ttu-id="28f19-136">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="28f19-136">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="28f19-137">with:</span><span class="sxs-lookup"><span data-stu-id="28f19-137">with:</span></span>  
  
    ```  
    Forecasting_ARIMA  
    ```  
  
5.  <span data-ttu-id="28f19-138">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="28f19-138">Replace the following:</span></span>  
  
    ```  
    <key columns>,  
    ```  
  
     <span data-ttu-id="28f19-139">with:</span><span class="sxs-lookup"><span data-stu-id="28f19-139">with:</span></span>  
  
    ```  
    [ReportingDate],  
    [ModelRegion]  
    ```  
  
     <span data-ttu-id="28f19-140">CREATE MINING MODEL ステートメントで指定したデータ型やコンテンツの種類に関する情報は、マイニング構造に既に保存されているため、繰り返し指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="28f19-140">Note that you do not need to repeat any of the date type or content type information that you provided in the CREATE MINING MODEL statement, because this information is already stored in the mining structure.</span></span>  
  
6.  <span data-ttu-id="28f19-141">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="28f19-141">Replace the following:</span></span>  
  
    ```  
    <mining model columns>  
    ```  
  
     <span data-ttu-id="28f19-142">with:</span><span class="sxs-lookup"><span data-stu-id="28f19-142">with:</span></span>  
  
    ```  
    ([Quantity] PREDICT,  
    [Amount] PREDICT  
    )  
    ```  
  
7.  <span data-ttu-id="28f19-143">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="28f19-143">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>([<algorithm parameters>])   
    [WITH DRILLTHROUGH]  
    ```  
  
     <span data-ttu-id="28f19-144">with:</span><span class="sxs-lookup"><span data-stu-id="28f19-144">with:</span></span>  
  
    ```  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="28f19-145">これで、ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="28f19-145">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARIMA]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
8.  <span data-ttu-id="28f19-146">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28f19-146">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
9. <span data-ttu-id="28f19-147">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Forecasting_ARIMA.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="28f19-147">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_ARIMA.dmx`.</span></span>  
  
10. <span data-ttu-id="28f19-148">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="28f19-148">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-an-artxp-time-series-model-to-the-structure"></a><span data-ttu-id="28f19-149">構造への ARTXP 時系列モデルの追加</span><span class="sxs-lookup"><span data-stu-id="28f19-149">Adding an ARTXP Time Series Model to the Structure</span></span>  
 <span data-ttu-id="28f19-150">ARTXP アルゴリズムは、SQL Server 2005 の既定のタイム シリーズ アルゴリズムで、短期の予測に適しています。</span><span class="sxs-lookup"><span data-stu-id="28f19-150">The ARTXP algorithm was the default time series algorithm in SQL Server 2005 and is optimized for short-term prediction.</span></span> <span data-ttu-id="28f19-151">3 つのアルゴリズムをすべて使用して予測を比較するために、ARTXP アルゴリズムに基づくモデルをもう 1 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="28f19-151">To compare predictions by using all three time series algorithms, you will add one more model that is based on the ARTXP algorithm.</span></span>  
  
#### <a name="to-add-an-artxp-time-series-mining-model"></a><span data-ttu-id="28f19-152">ARTXP 時系列マイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="28f19-152">To add an ARTXP time series mining model</span></span>  
  
1.  <span data-ttu-id="28f19-153">空のクエリ ウィンドウに次のコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="28f19-153">Copy the following code into a blank query window.</span></span>  
  
     <span data-ttu-id="28f19-154">変更する必要があるのは、新しいマイニング モデルの名前と FORECAST_METHOD パラメーターの値だけです。</span><span class="sxs-lookup"><span data-stu-id="28f19-154">Note that you do not need to change anything except the name of the new mining model, and the value of the FORECAST_METHOD parameter.</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARTXP]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARTXP')  
    WITH DRILLTHROUGH  
    ```  
  
2.  <span data-ttu-id="28f19-155">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28f19-155">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
3.  <span data-ttu-id="28f19-156">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Forecasting_ARTXP.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="28f19-156">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_ARTXP.dmx`.</span></span>  
  
4.  <span data-ttu-id="28f19-157">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="28f19-157">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="28f19-158">次のレッスンでは、すべてのモデルとマイニング構造を処理します。</span><span class="sxs-lookup"><span data-stu-id="28f19-158">In the next lesson, you will process all of the models and the mining structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="28f19-159">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="28f19-159">Next Lesson</span></span>  
 [<span data-ttu-id="28f19-160">レッスン 3: 時系列構造と時系列モデルの処理</span><span class="sxs-lookup"><span data-stu-id="28f19-160">Lesson 3: Processing the Time Series Structure and Models</span></span>](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="28f19-161">参照</span><span class="sxs-lookup"><span data-stu-id="28f19-161">See Also</span></span>  
 <span data-ttu-id="28f19-162">[Microsoft タイムシリーズアルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="28f19-162">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 [<span data-ttu-id="28f19-163">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="28f19-163">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
