---
title: 'レッスン 1: タイムシリーズマイニングモデルとマイニング構造の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b201f2b8-9ab5-425b-9ff3-fe321a60a7b7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2513bc3837dd224f6561eb0015ced538ea3add8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632853"
---
# <a name="lesson-1-creating-a-time-series-mining-model-and-mining-structure"></a><span data-ttu-id="4c8a5-102">レッスン 1: 時系列マイニング モデルおよびマイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="4c8a5-102">Lesson 1: Creating a Time Series Mining Model and Mining Structure</span></span>
  <span data-ttu-id="4c8a5-103">このレッスンでは、履歴データを基に時間の経過に応じて値を予測するためのマイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-103">In this lesson, you will create a mining model that allows you to predict values over time, based on historical data.</span></span> <span data-ttu-id="4c8a5-104">モデルを作成すると、基になる構造が自動的に生成され、追加のマイニング モデルのベースとして使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-104">When you create the model, the underlying structure will be generated automatically and can be used as the basis for additional mining models.</span></span>  
  
 <span data-ttu-id="4c8a5-105">このレッスンは、予測モデルおよび Microsoft Time Series アルゴリズムの要件について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-105">This lesson assumes that you are familiar with forecasting models and with the requirements of the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="4c8a5-106">詳細については、「 [Microsoft Time Series アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-106">For more information, see [Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md).</span></span>  
  
## <a name="create-mining-model-statement"></a><span data-ttu-id="4c8a5-107">CREATE マイニングモデルステートメント</span><span class="sxs-lookup"><span data-stu-id="4c8a5-107">CREATE MINING MODEL Statement</span></span>  
 <span data-ttu-id="4c8a5-108">マイニングモデルを直接作成し、基になるマイニング構造を自動的に生成するには、 [CREATE マイニング model &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-108">In order to create a mining model directly and automatically generate the underlying mining structure, you use the [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx) statement.</span></span> <span data-ttu-id="4c8a5-109">ステートメント内のコードは、次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-109">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="4c8a5-110">モデルの名前指定</span><span class="sxs-lookup"><span data-stu-id="4c8a5-110">Naming the model</span></span>  
  
-   <span data-ttu-id="4c8a5-111">タイム スタンプの定義</span><span class="sxs-lookup"><span data-stu-id="4c8a5-111">Defining the time stamp</span></span>  
  
-   <span data-ttu-id="4c8a5-112">省略可能な系列キー列の定義</span><span class="sxs-lookup"><span data-stu-id="4c8a5-112">Defining the optional series key column</span></span>  
  
-   <span data-ttu-id="4c8a5-113">予測可能な属性の定義</span><span class="sxs-lookup"><span data-stu-id="4c8a5-113">Defining the predictable attribute or attributes</span></span>  
  
 <span data-ttu-id="4c8a5-114">CREATE MINING MODEL ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-114">The following is a generic example of the CREATE MINING MODEL statement:</span></span>  
  
```  
CREATE MINING MODEL [<Mining Structure Name>]  
(  
   <key columns>,  
   <predictable attribute columns>  
)  
USING <algorithm name>([parameter list])  
WITH DRILLTHROUGH  
```  
  
 <span data-ttu-id="4c8a5-115">コードの 1 行目では、マイニング モデルの名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-115">The first line of the code defines the name of the mining model:</span></span>  
  
```  
CREATE MINING MODEL [Mining Model Name]  
```  
  
 <span data-ttu-id="4c8a5-116">Analysis Services では、基になる構造に対し、モデル名の後に「_structure」を追加した名前が自動的に生成されます。これにより、構造名がモデル名と重複しないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-116">Analysis Services automatically generates a name for the underlying structure, by appending "_structure" to the model name, which ensures that the structure name is unique from the model name.</span></span> <span data-ttu-id="4c8a5-117">DMX でのオブジェクトの名前付けの詳細については、「 [dmx&#41;&#40;の識別子](/sql/dmx/identifiers-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-117">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="4c8a5-118">コードの次の行では、マイニング モデルのキー列を定義します。キー列は、時系列モデルでソース データの時間ステップを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-118">The next line of the code defines the key column for the mining model, which in the case of a time series model uniquely identifies a time step in the source data.</span></span> <span data-ttu-id="4c8a5-119">Time ステップは、 `KEY TIME` 列名とデータ型の後にあるキーワードを使用して識別されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-119">The time step is identified with the `KEY TIME` keywords after the column name and data types.</span></span> <span data-ttu-id="4c8a5-120">時系列モデルに別の系列キーが含まれている場合は、`KEY` キーワードでそのキーが識別されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-120">If the time series model has a separate series key, it is identified by using the `KEY` keyword.</span></span>  
  
```  
<key columns>  
```  
  
 <span data-ttu-id="4c8a5-121">コードの次の行では、予測対象となるモデル内の列を定義します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-121">The next line of the code is used to define the columns in the model that will be predicted.</span></span> <span data-ttu-id="4c8a5-122">1 つのマイニング モデルに複数の予測可能な属性を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-122">You can have multiple predictable attributes in a single mining model.</span></span> <span data-ttu-id="4c8a5-123">予測可能な属性が複数ある場合は、Microsoft Time Series アルゴリズムによって系列ごとに個別に分析が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-123">When there are multiple predictable attributes, the Microsoft Time Series algorithm generates a separate analysis for each series:</span></span>  
  
```  
<predictable attribute columns>  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="4c8a5-124">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="4c8a5-124">Lesson Tasks</span></span>  
 <span data-ttu-id="4c8a5-125">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-125">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="4c8a5-126">新しい空のクエリの作成</span><span class="sxs-lookup"><span data-stu-id="4c8a5-126">Create a new blank query</span></span>  
  
-   <span data-ttu-id="4c8a5-127">マイニング モデルを作成するためのクエリの変更</span><span class="sxs-lookup"><span data-stu-id="4c8a5-127">Alter the query to create the mining model</span></span>  
  
-   <span data-ttu-id="4c8a5-128">クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="4c8a5-128">Execute the query</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="4c8a5-129">クエリの作成</span><span class="sxs-lookup"><span data-stu-id="4c8a5-129">Creating the Query</span></span>  
 <span data-ttu-id="4c8a5-130">最初の手順では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のインスタンスに接続して新しい DMX クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-130">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="4c8a5-131">SQL Server Management Studio で新しい DMX クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="4c8a5-131">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="4c8a5-132">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-132">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="4c8a5-133">[**サーバーへの接続**] ダイアログボックスの [**サーバーの種類**] で、[ **Analysis Services**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-133">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="4c8a5-134">[**サーバー名**] に、 `LocalHost` このレッスンで接続するのインスタンスの名前またはを入力し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-134">In **Server name**, type `LocalHost`, or the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="4c8a5-135">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-135">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="4c8a5-136">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-136">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="4c8a5-137">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-137">Query Editor opens and contains a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="4c8a5-138">クエリの変更</span><span class="sxs-lookup"><span data-stu-id="4c8a5-138">Altering the Query</span></span>  
 <span data-ttu-id="4c8a5-139">次の手順では、CREATE MINING MODEL ステートメントを変更して、予測に使用されるマイニング モデルがその基になるマイニング構造と共に作成されるようにします。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-139">The next step is to modify the CREATE MINING MODEL statement to create the mining model used for forecasting, together with its underlying mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-model-statement"></a><span data-ttu-id="4c8a5-140">CREATE MINING MODEL ステートメントをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="4c8a5-140">To customize the CREATE MINING MODEL statement</span></span>  
  
1.  <span data-ttu-id="4c8a5-141">クエリ エディターで、CREATE MINING MODEL ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-141">In Query Editor, copy the generic example of the CREATE MINING MODEL statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="4c8a5-142">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-142">Replace the following:</span></span>  
  
    ```  
    [mining model name]   
    ```  
  
     <span data-ttu-id="4c8a5-143">with:</span><span class="sxs-lookup"><span data-stu-id="4c8a5-143">with:</span></span>  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
3.  <span data-ttu-id="4c8a5-144">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-144">Replace the following:</span></span>  
  
    ```  
    <key columns>  
    ```  
  
     <span data-ttu-id="4c8a5-145">with:</span><span class="sxs-lookup"><span data-stu-id="4c8a5-145">with:</span></span>  
  
    ```  
    [Reporting Date] DATE KEY TIME,  
    [Model Region] TEXT KEY  
    ```  
  
     <span data-ttu-id="4c8a5-146">`TIME KEY` キーワードは、ReportingDate 列に値を順に並べるための時間ステップ値が含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-146">The `TIME KEY` keyword indicates that the ReportingDate column contains the time step values used to order the values.</span></span> <span data-ttu-id="4c8a5-147">時間ステップのデータ型は、値が一意でデータの並べ替えが可能であれば、日付/時刻型、整数型、任意の順序付きデータ型のどれでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-147">Time steps can be dates and times, integers, or any ordered data type, so long as the values are unique and the data is sorted.</span></span>  
  
     <span data-ttu-id="4c8a5-148">`TEXT` キーワードと `KEY` キーワードは、ModelRegion 列に追加の系列キーが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-148">The `TEXT` and `KEY` keywords indicate that the ModelRegion column contains an additional series key.</span></span> <span data-ttu-id="4c8a5-149">使用できる系列キーは 1 つに限られており、列内の値は一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-149">You can have only one series key, and the values in the column must be distinct.</span></span>  
  
4.  <span data-ttu-id="4c8a5-150">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-150">Replace the following:</span></span>  
  
    ```  
    < predictable attribute columns> )  
    ```  
  
     <span data-ttu-id="4c8a5-151">with:</span><span class="sxs-lookup"><span data-stu-id="4c8a5-151">with:</span></span>  
  
    ```  
    [Quantity] LONG CONTINUOUS PREDICT,  
    [Amount] DOUBLE CONTINUOUS PREDICT  
    )  
    ```  
  
5.  <span data-ttu-id="4c8a5-152">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-152">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>([parameter list])  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="4c8a5-153">with:</span><span class="sxs-lookup"><span data-stu-id="4c8a5-153">with:</span></span>  
  
    ```  
    USING Microsoft_Time_Series(AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="4c8a5-154">アルゴリズム パラメーター `AUTO_DETECT_PERIODICITY` = 0.8 では、アルゴリズムでデータの周期を検出するように指定しています。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-154">The algorithm parameter, `AUTO_DETECT_PERIODICITY` = 0.8, indicates that you want the algorithm to detect cycles in the data.</span></span> <span data-ttu-id="4c8a5-155">1 に近い値を設定すると、多数のパターンを検出できますが、処理に時間がかかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-155">Setting this value closer to 1 favors the discovery of many patterns but can slow processing.</span></span>  
  
     <span data-ttu-id="4c8a5-156">アルゴリズム パラメーター `FORECAST_METHOD` では、ARTXP、ARIMA、ARTXP と ARIMA の両方のうち、どれを使用してデータを分析するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-156">The algorithm parameter, `FORECAST_METHOD`, indicates whether you want the data to be analyzed using ARTXP, ARIMA, or a mixture of both.</span></span>  
  
     <span data-ttu-id="4c8a5-157">キーワード `WITH DRILLTHROUGH` では、モデルが完成した後にソース データの詳細な統計を表示できるようにすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-157">The keyword, `WITH DRILLTHROUGH`, specify that you want to be able to view detailed statistics in the source data after the model is complete.</span></span> <span data-ttu-id="4c8a5-158">Microsoft タイム シリーズ ビューアーでモデルを参照する場合は、この句を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-158">You must add this clause if you want to browse the model by using the Microsoft Time Series Viewer.</span></span> <span data-ttu-id="4c8a5-159">予測にはこの句は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-159">It is not required for prediction.</span></span>  
  
     <span data-ttu-id="4c8a5-160">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-160">The complete statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING MODEL [Forecasting_MIXED]  
         (  
        [Reporting Date] DATE KEY TIME,  
        [Model Region] TEXT KEY,  
        [Quantity] LONG CONTINUOUS PREDICT,  
        [Amount] DOUBLE CONTINUOUS PREDICT  
        )  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
  
    ```  
  
6.  <span data-ttu-id="4c8a5-161">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-161">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="4c8a5-162">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Forecasting_MIXED.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-162">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_MIXED.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="4c8a5-163">クエリの実行</span><span class="sxs-lookup"><span data-stu-id="4c8a5-163">Executing the Query</span></span>  
 <span data-ttu-id="4c8a5-164">最後の手順では、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-164">The final step is to execute the query.</span></span> <span data-ttu-id="4c8a5-165">クエリを作成して保存したら、そのクエリを実行してサーバーにマイニング モデルとそのマイニング構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-165">After a query is created and saved, it needs to be executed to create the mining model and its mining structure on the server.</span></span> <span data-ttu-id="4c8a5-166">クエリエディターでのクエリの実行の詳細については、「[データベースエンジンクエリエディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-166">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="4c8a5-167">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="4c8a5-167">To execute the query</span></span>  
  
-   <span data-ttu-id="4c8a5-168">クエリエディターのツールバーで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-168">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="4c8a5-169">クエリの状態は、ステートメントの実行が完了した後、クエリエディターの下部にある [**メッセージ**] タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-169">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="4c8a5-170">この場合次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-170">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="4c8a5-171">**Forecasting_MIXED_Structure**という名前の新しい構造が、関連するマイニングモデル**Forecasting_MIXED**と共にサーバーに存在するようになりました。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-171">A new structure named **Forecasting_MIXED_Structure** now exists on the server, together with the related mining model **Forecasting_MIXED**.</span></span>  
  
 <span data-ttu-id="4c8a5-172">次のレッスンでは、作成した**Forecasting_MIXED**マイニング構造にマイニングモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="4c8a5-172">In the next lesson, you will add a mining model to the **Forecasting_MIXED** mining structure that you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="4c8a5-173">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="4c8a5-173">Next Lesson</span></span>  
 [<span data-ttu-id="4c8a5-174">レッスン 2: 時系列マイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="4c8a5-174">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
  
## <a name="see-also"></a><span data-ttu-id="4c8a5-175">参照</span><span class="sxs-lookup"><span data-stu-id="4c8a5-175">See Also</span></span>  
 <span data-ttu-id="4c8a5-176">[タイムシリーズモデルのマイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="4c8a5-176">[Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="4c8a5-177">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4c8a5-177">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
