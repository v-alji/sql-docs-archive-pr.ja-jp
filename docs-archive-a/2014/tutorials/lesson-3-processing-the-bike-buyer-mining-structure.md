---
title: 'レッスン 3: 自転車購入者マイニング構造の処理 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719077"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a><span data-ttu-id="b9f51-102">レッスン 3: Bike Buyer マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="b9f51-102">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="b9f51-103">このレッスンでは、サンプルデータベースの INSERT INTO ステートメントと vTargetMail ビューを使用して、「 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] [レッスン 1: 自転車の購入者マイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)」と「[レッスン 2: 自転車購入者マイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)」で作成したマイニング構造とマイニングモデルを処理します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-103">In this lesson, you will use the INSERT INTO statement and the vTargetMail view from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database to process the mining structures and mining models that you created in [Lesson 1: Creating the Bike Buyer Mining Structure](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) and [Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).</span></span>  
  
 <span data-ttu-id="b9f51-104">マイニング構造の処理では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でソース データが読み込まれ、マイニング モデルをサポートする構造が構築されます。</span><span class="sxs-lookup"><span data-stu-id="b9f51-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="b9f51-105">マイニング モデルの処理では、マイニング構造で定義されたデータが、選択したデータ マイニング アルゴリズムを介して受け渡されます。</span><span class="sxs-lookup"><span data-stu-id="b9f51-105">When you process a mining model, the data defined by the mining structure is passed through the data mining algorithm that you choose.</span></span> <span data-ttu-id="b9f51-106">このアルゴリズムでは傾向とパターンが検索され、結果の情報がマイニング モデルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b9f51-106">The algorithm searches for trends and patterns, and then stores this information in the mining model.</span></span> <span data-ttu-id="b9f51-107">したがって、マイニング モデルには、実際のソース データではなく、アルゴリズムで検出された情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9f51-107">The mining model, therefore, does not contain the actual source data, but instead contains the information that was discovered by the algorithm.</span></span> <span data-ttu-id="b9f51-108">マイニングモデルの処理の詳細については、「[データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9f51-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
 <span data-ttu-id="b9f51-109">マイニング構造の再処理は、構造列またはソース データを変更した場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="b9f51-109">You need to reprocess a mining structure only if you change a structure column or change the source data.</span></span> <span data-ttu-id="b9f51-110">処理済みのマイニング構造にマイニング モデルを追加する場合は、INSERT INTO MINING MODEL ステートメントを使用して新しいマイニング モデルをトレーニングできます。</span><span class="sxs-lookup"><span data-stu-id="b9f51-110">If you add a mining model to a mining structure that has already been processed, you can use the INSERT INTO MINING MODEL statement to train the new mining model.</span></span>  
  
## <a name="train-structure-template"></a><span data-ttu-id="b9f51-111">構造テンプレートのトレーニング</span><span class="sxs-lookup"><span data-stu-id="b9f51-111">Train Structure Template</span></span>  
 <span data-ttu-id="b9f51-112">マイニング構造とそれに関連付けられているマイニングモデルをトレーニングするには、 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-112">In order to train the mining structure and its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="b9f51-113">ステートメント内のコードは、次の部分に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="b9f51-113">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="b9f51-114">マイニング構造の指定</span><span class="sxs-lookup"><span data-stu-id="b9f51-114">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="b9f51-115">マイニング構造の列の一覧</span><span class="sxs-lookup"><span data-stu-id="b9f51-115">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="b9f51-116">トレーニング データの定義</span><span class="sxs-lookup"><span data-stu-id="b9f51-116">Defining the training data</span></span>  
  
 <span data-ttu-id="b9f51-117">INSERT INTO ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-117">The following is a generic example of the INSERT INTO statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 <span data-ttu-id="b9f51-118">コードの最初の行では、トレーニングするマイニング構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-118">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="b9f51-119">コードの次の行では、マイニング構造で定義される列を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-119">The next line of the code specifies the columns that are defined by the mining structure.</span></span> <span data-ttu-id="b9f51-120">ここではマイニング構造の各列を指定する必要があります。各列はソース クエリ データ内の列にマップされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f51-120">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span>  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 <span data-ttu-id="b9f51-121">コードの最後の行では、マイニング構造のトレーニングに使用するデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-121">The final line of the code defines the data that will be used to train the mining structure:</span></span>  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 <span data-ttu-id="b9f51-122">このレッスンでは、`OPENQUERY` を使用してソース データを定義します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-122">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="b9f51-123">ソースクエリを定義するその他の方法については、「 [&#60;source data query&#62;](/sql/dmx/source-data-query)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9f51-123">For information about other methods of defining the source query, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="b9f51-124">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="b9f51-124">Lesson Tasks</span></span>  
 <span data-ttu-id="b9f51-125">このレッスンでは、次の作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-125">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="b9f51-126">Bike Buyer マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="b9f51-126">Process the Bike Buyer mining structure</span></span>  
  
## <a name="processing-the-predictive-mining-structure"></a><span data-ttu-id="b9f51-127">予測マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="b9f51-127">Processing the Predictive Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a><span data-ttu-id="b9f51-128">INSERT INTO を使用してマイニング構造を処理するには</span><span class="sxs-lookup"><span data-stu-id="b9f51-128">To process the mining structure by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="b9f51-129">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f51-129">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="b9f51-130">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9f51-130">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="b9f51-131">上の INSERT INTO ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b9f51-131">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="b9f51-132">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-132">Replace the following:</span></span>  
  
    ```  
    [<mining structure name>]   
    ```  
  
     <span data-ttu-id="b9f51-133">with:</span><span class="sxs-lookup"><span data-stu-id="b9f51-133">with:</span></span>  
  
    ```  
    Bike Buyer  
    ```  
  
4.  <span data-ttu-id="b9f51-134">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-134">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    ```  
  
     <span data-ttu-id="b9f51-135">with:</span><span class="sxs-lookup"><span data-stu-id="b9f51-135">with:</span></span>  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
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
  
5.  <span data-ttu-id="b9f51-136">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-136">Replace the following:</span></span>  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     <span data-ttu-id="b9f51-137">with:</span><span class="sxs-lookup"><span data-stu-id="b9f51-137">with:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     <span data-ttu-id="b9f51-138">OPENQUERY ステートメントは、[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] データ ソースを参照して、vTargetMail ビューにアクセスしています。</span><span class="sxs-lookup"><span data-stu-id="b9f51-138">The OPENQUERY statement references the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source to access the view vTargetMail.</span></span> <span data-ttu-id="b9f51-139">ビューには、マイニングモデルのトレーニングに使用されるソースデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9f51-139">The view contains the source data that will be used to train the mining models.</span></span>  
  
     <span data-ttu-id="b9f51-140">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b9f51-140">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
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
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  <span data-ttu-id="b9f51-141">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f51-141">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="b9f51-142">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `Process Bike Buyer Structure.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="b9f51-142">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Process Bike Buyer Structure.dmx`.</span></span>  
  
8.  <span data-ttu-id="b9f51-143">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f51-143">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="b9f51-144">次のレッスンでは、このレッスンでマイニング構造に追加したマイニング モデルの内容を調査します。</span><span class="sxs-lookup"><span data-stu-id="b9f51-144">In the next lesson, you will explore content in the mining models you added to the mining structure in this lesson.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="b9f51-145">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="b9f51-145">Next Lesson</span></span>  
 [<span data-ttu-id="b9f51-146">レッスン 4: Bike Buyer マイニング モデルの参照</span><span class="sxs-lookup"><span data-stu-id="b9f51-146">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
