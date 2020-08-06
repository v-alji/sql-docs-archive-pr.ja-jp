---
title: 'レッスン 4: 自転車購入者マイニングモデルの参照 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8de3c500-f881-42da-a096-b6c03300d58d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 709df371d840d4b24e420b4fcd08750fd31e8075
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639842"
---
# <a name="lesson-4-browsing-the-bike-buyer-mining-models"></a><span data-ttu-id="7a531-102">レッスン 4: Bike Buyer マイニング モデルの参照</span><span class="sxs-lookup"><span data-stu-id="7a531-102">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>
  <span data-ttu-id="7a531-103">このレッスンでは、 [select (DMX)](/sql/dmx/select-dmx)ステートメントを使用して、「[レッスン 2: 予測マイニング構造へのマイニングモデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)」で作成したデシジョンツリーおよびクラスターマイニングモデルの内容を調査します。</span><span class="sxs-lookup"><span data-stu-id="7a531-103">In this lesson, you will use the [SELECT (DMX)](/sql/dmx/select-dmx) statement to explore the content in the decision tree and clustering mining models that you created in [Lesson 2: Adding Mining Models to the Predictive Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).</span></span>  
  
 <span data-ttu-id="7a531-104">マイニング モデルに含まれる列は、マイニング構造で定義されている列ではなく、アルゴリズムによって検出された傾向とパターンを記述している、特定の列のセットです。</span><span class="sxs-lookup"><span data-stu-id="7a531-104">The columns contained in a mining model are not the columns defined by the mining structure, but instead are a specific set of columns that describe the trends and patterns that are found by the algorithm.</span></span> <span data-ttu-id="7a531-105">これらのマイニングモデル列については、「 [DMSCHEMA_MINING_MODEL_CONTENT 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)スキーマ行セット」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a531-105">These mining model columns are described in the [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset) schema rowset.</span></span> <span data-ttu-id="7a531-106">たとえば、コンテンツ スキーマ行セットの MODEL_NAME 列には、マイニング モデルの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a531-106">For example, the MODEL_NAME column in the content schema rowset contains the name of the mining model.</span></span> <span data-ttu-id="7a531-107">クラスター マイニング モデルの場合、NODE_CAPTION 列には各クラスターの名前が含まれ、NODE_DESCRIPTION 列には各クラスターの特性の説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a531-107">For a clustering mining model, the NODE_CAPTION column contains the name of each cluster, and the NODE_DESCRIPTION column contains a description of the characteristics of each cluster.</span></span> <span data-ttu-id="7a531-108">これらの列を参照するには、[FROM FROM] を使用し \<model> ます。DMX の CONTENT ステートメント。</span><span class="sxs-lookup"><span data-stu-id="7a531-108">You can browse these columns by using the SELECT FROM \<model>.CONTENT statement in DMX.</span></span> <span data-ttu-id="7a531-109">このステートメントを使用すると、マイニング モデルの作成に使用されたデータを調査することもできます。</span><span class="sxs-lookup"><span data-stu-id="7a531-109">You can also use this statement to explore the data that was used to create the mining model.</span></span> <span data-ttu-id="7a531-110">このステートメントを使用するには、マイニング構造上でドリルスルーを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a531-110">Drillthrough must be enabled on the mining structure in order to use this statement.</span></span> <span data-ttu-id="7a531-111">ステートメントの詳細については、「 [SELECT FROM &#60;model&#62;」を参照してください。DMX&#41;&#40;ケース](/sql/dmx/select-from-model-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="7a531-111">For more information about the statement, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
 <span data-ttu-id="7a531-112">SELECT DISTINCT ステートメントを使用することにより、不連続列のすべての状態を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="7a531-112">You can also return all the states of a discrete column by using the SELECT DISTINCT statement.</span></span> <span data-ttu-id="7a531-113">たとえば、性別の列でこの操作を実行すると、クエリでは `male` と `female` が返されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-113">For example, if you perform this operation on a gender column, the query will return `male` and `female`.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="7a531-114">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="7a531-114">Lesson Tasks</span></span>  
 <span data-ttu-id="7a531-115">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="7a531-115">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="7a531-116">マイニング モデルに含まれる内容の調査</span><span class="sxs-lookup"><span data-stu-id="7a531-116">Explore the content contained within the mining models</span></span>  
  
-   <span data-ttu-id="7a531-117">マイニング モデルのトレーニングに使用されたソース データからケースを返す</span><span class="sxs-lookup"><span data-stu-id="7a531-117">Return the cases from the source data that was used to train the mining models</span></span>  
  
-   <span data-ttu-id="7a531-118">特定の不連続列に対して可能な状態の調査</span><span class="sxs-lookup"><span data-stu-id="7a531-118">Explore the different states available for a specific discrete column</span></span>  
  
## <a name="returning-the-content-of-a-mining-model"></a><span data-ttu-id="7a531-119">マイニング モデルの内容を返す</span><span class="sxs-lookup"><span data-stu-id="7a531-119">Returning the Content of a Mining Model</span></span>  
 <span data-ttu-id="7a531-120">このレッスンでは、 [SELECT FROM &#60;model&#62; を使用します。コンテンツ &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx)ステートメントによって、クラスターモデルの内容が返されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-120">In this lesson, you use the [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx) statement to return the contents of the clustering model.</span></span>  
  
 <span data-ttu-id="7a531-121">SELECT FROM の一般的な例を次に示し \<model> ます。コンテンツステートメント:</span><span class="sxs-lookup"><span data-stu-id="7a531-121">The following is a generic example of the SELECT FROM \<model>.CONTENT statement:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>].CONTENT  
WHERE <where clause>  
```  
  
 <span data-ttu-id="7a531-122">コードの 1 行目では、マイニング モデルの内容から返す列と、それらの列が関連付けられているマイニング モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="7a531-122">The first line of the code defines the columns to return from the mining model content, and the mining model they are associated with:</span></span>  
  
```  
SELECT <select list> FROM [<mining model].CONTENT  
```  
  
 <span data-ttu-id="7a531-123">マイニング モデル名の後の .CONTENT 句は、マイニング モデルから内容を返すことを示します。</span><span class="sxs-lookup"><span data-stu-id="7a531-123">The .CONTENT clause next to the name of the mining model specifies that you are returning content from the mining model.</span></span> <span data-ttu-id="7a531-124">マイニングモデルに含まれる列の詳細については、「 [DMSCHEMA_MINING_MODEL_CONTENT 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a531-124">For more information about the columns contained in the mining model, see [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
 <span data-ttu-id="7a531-125">コードの最終行では、ステートメントで返される結果をフィルター選択します。この行は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7a531-125">You can optionally use the final line of the code to filter the results returned by the statement:</span></span>  
  
```  
WHERE <where clause>  
```  
  
 <span data-ttu-id="7a531-126">たとえば、クエリの結果を制限して、多数のケースが含まれるクラスターのみを返すようにする場合は、SELECT ステートメントに次の WHERE 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="7a531-126">For example, if you want to restrict the results of the query to only the clusters that contain a high number of cases, you can add the following WHERE clause to the SELECT statement:</span></span>  
  
```  
WHERE NODE_SUPPORT > 100  
```  
  
 <span data-ttu-id="7a531-127">WHERE ステートメントの使用方法の詳細については、「 [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a531-127">For more information about using the WHERE statement, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
#### <a name="to-return-the-content-of-the-clustering-mining-model"></a><span data-ttu-id="7a531-128">クラスター マイニング モデルの内容を返すには</span><span class="sxs-lookup"><span data-stu-id="7a531-128">To return the content of the clustering mining model</span></span>  
  
1.  <span data-ttu-id="7a531-129">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-129">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="7a531-130">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-130">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="7a531-131">SELECT のジェネリックな例をコピー \<model> します。空のクエリに CONTENT ステートメントを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a531-131">Copy the generic example of the SELECT FROM \<model>.CONTENT statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="7a531-132">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="7a531-132">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="7a531-133">with:</span><span class="sxs-lookup"><span data-stu-id="7a531-133">with:</span></span>  
  
    ```  
    *  
    ```  
  
     <span data-ttu-id="7a531-134">また、\* を[DMSCHEMA_MINING_MODEL_CONTENT 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)内に含まれる任意の列の一覧に置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="7a531-134">You can also replace \* with a list of any of the columns contained within the [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
4.  <span data-ttu-id="7a531-135">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="7a531-135">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="7a531-136">with:</span><span class="sxs-lookup"><span data-stu-id="7a531-136">with:</span></span>  
  
    ```  
    [Clustering]  
    ```  
  
     <span data-ttu-id="7a531-137">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7a531-137">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT * FROM [Clustering].CONTENT  
    ```  
  
5.  <span data-ttu-id="7a531-138">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-138">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="7a531-139">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `SELECT_CONTENT.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="7a531-139">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_CONTENT.dmx`.</span></span>  
  
7.  <span data-ttu-id="7a531-140">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-140">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="7a531-141">クエリが実行され、マイニング モデルの内容が返されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-141">The query returns the content of the mining model.</span></span>  
  
## <a name="use-drillthrough"></a><span data-ttu-id="7a531-142">ドリルスルーの使用</span><span class="sxs-lookup"><span data-stu-id="7a531-142">Use Drillthrough</span></span>  
 <span data-ttu-id="7a531-143">次の手順では、ドリルスルー ステートメントを使用して、デシジョン ツリー マイニング モデルのトレーニングに使用されたケースの一部を返します。</span><span class="sxs-lookup"><span data-stu-id="7a531-143">The next step is to use the drillthrough statement to return a sampling of the cases that were used to train the decision tree mining model.</span></span> <span data-ttu-id="7a531-144">このレッスンでは、 [SELECT FROM &#60;model&#62; を使用します。](/sql/dmx/select-from-model-content-dmx)デシジョンツリーモデルの内容を返す DMX&#41;ステートメント &#40;ケース。</span><span class="sxs-lookup"><span data-stu-id="7a531-144">In this lesson, you use the [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) statement to return the contents of the decision tree model.</span></span>  
  
 <span data-ttu-id="7a531-145">SELECT FROM の一般的な例を次に示し \<model> ます。CASE ステートメント:</span><span class="sxs-lookup"><span data-stu-id="7a531-145">The following is a generic example of the SELECT FROM \<model>.CASES statement:</span></span>  
  
```  
SELECT <select list>   
FROM [<mining model>].CASES  
WHERE IsInNode('<node id>')  
```  
  
 <span data-ttu-id="7a531-146">コードの 1 行目では、ソース データから返す列と、それらの列が含まれるマイニング モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="7a531-146">The first line of the code defines the columns to return from the source data, and the mining model they are contained within:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>].CASES  
```  
  
 <span data-ttu-id="7a531-147">.CASES 句は、ドリルスルー クエリを実行することを示します。</span><span class="sxs-lookup"><span data-stu-id="7a531-147">The .CASES clause specifies that you are performing a drillthrough query.</span></span> <span data-ttu-id="7a531-148">ドリルスルーを使用するには、マイニング モデルの作成時にドリルスルーを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a531-148">In order to use drillthrough you must enable drillthrough when you create the mining model.</span></span>  
  
 <span data-ttu-id="7a531-149">コードの最終行では、ケースを要求するマイニング モデル内のノードを指定します。この行は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7a531-149">The final line of the code is optional and specifies the node in the mining model that you are requesting cases from:</span></span>  
  
```  
WHERE IsInNode('<node id>')  
```  
  
 <span data-ttu-id="7a531-150">WHERE ステートメントを IsInNode と共に使用する方法の詳細については、「 [SELECT FROM &#60;model&#62;」を参照してください。DMX&#41;&#40;ケース](/sql/dmx/select-from-model-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="7a531-150">For more information about using the WHERE statement with IsInNode, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
#### <a name="to-return-the-cases-that-were-used-to-train-the-mining-model"></a><span data-ttu-id="7a531-151">マイニング モデルのトレーニングに使用されたケースを返すには</span><span class="sxs-lookup"><span data-stu-id="7a531-151">To return the cases that were used to train the mining model</span></span>  
  
1.  <span data-ttu-id="7a531-152">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-152">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="7a531-153">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-153">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="7a531-154">SELECT のジェネリックな例をコピー \<model> します。空のクエリに CASE ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="7a531-154">Copy the generic example of the SELECT FROM \<model>.CASES statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="7a531-155">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="7a531-155">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="7a531-156">with:</span><span class="sxs-lookup"><span data-stu-id="7a531-156">with:</span></span>  
  
    ```  
    *  
    ```  
  
     <span data-ttu-id="7a531-157">\* は、ソース データ内に含まれる任意の列の一覧 ([Bike Buyer] など) に置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="7a531-157">You can also replace \* with a list of any of the columns contained within the source data (such as [Bike Buyer]).</span></span>  
  
4.  <span data-ttu-id="7a531-158">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="7a531-158">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="7a531-159">with:</span><span class="sxs-lookup"><span data-stu-id="7a531-159">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
     <span data-ttu-id="7a531-160">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7a531-160">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT *   
    FROM [Decision Tree].CASES  
    ```  
  
5.  <span data-ttu-id="7a531-161">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-161">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="7a531-162">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `SELECT_DRILLTHROUGH.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="7a531-162">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_DRILLTHROUGH.dmx`.</span></span>  
  
7.  <span data-ttu-id="7a531-163">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-163">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="7a531-164">クエリが実行され、デシジョン ツリー マイニング モデルのトレーニングに使用されたソース データが返されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-164">The query returns the source data that was used to train the decision tree mining model.</span></span>  
  
## <a name="return-the-states-of-a-discrete-mining-model-column"></a><span data-ttu-id="7a531-165">マイニング モデルの不連続列の状態を返す</span><span class="sxs-lookup"><span data-stu-id="7a531-165">Return the States of a Discrete Mining Model Column</span></span>  
 <span data-ttu-id="7a531-166">次の手順では、SELECT DISTINCT ステートメントを使用して、指定されたマイニング モデル列に対して可能な状態を返します。</span><span class="sxs-lookup"><span data-stu-id="7a531-166">The next step is to use the SELECT DISTINCT statement to return the different possible states in the specified mining model column.</span></span>  
  
 <span data-ttu-id="7a531-167">SELECT DISTINCT ステートメントの汎用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7a531-167">The following is a generic example of the SELECT DISTINCT statement:</span></span>  
  
```  
SELECT DISTINCT [<column>]   
FROM [<mining model>]  
```  
  
 <span data-ttu-id="7a531-168">コードの 1 行目では、状態を返すマイニング モデル列を定義します。</span><span class="sxs-lookup"><span data-stu-id="7a531-168">The first line of the code defines the mining model columns for which the states are returned:</span></span>  
  
```  
SELECT DISTINCT [<column>]   
```  
  
 <span data-ttu-id="7a531-169">列のすべての状態を返すには、DISTINCT を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a531-169">You must include DISTINCT in order to return all of the states of the column.</span></span> <span data-ttu-id="7a531-170">DISTINCT を指定しない場合は、ステートメント全体が予測用のショートカットとなり、指定した列で最も可能性の高い状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-170">If you exclude DISTINCT, then the full statement becomes a shortcut for a prediction and returns the most likely state of the specified column.</span></span> <span data-ttu-id="7a531-171">詳細については、「[SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a531-171">For more information, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
#### <a name="to-return-the-states-of-a-discrete-column"></a><span data-ttu-id="7a531-172">不連続列の状態を返すには</span><span class="sxs-lookup"><span data-stu-id="7a531-172">To return the states of a discrete column</span></span>  
  
1.  <span data-ttu-id="7a531-173">**オブジェクトエクスプローラー**で、のインスタンスを右クリックし、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **新しいクエリ**] をポイントして [ **DMX**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-173">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="7a531-174">クエリ エディターが開き、新しい空のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-174">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="7a531-175">上の SELECT Distinct ステートメントの汎用例を空のクエリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7a531-175">Copy the generic example of the SELECT Distinct statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="7a531-176">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="7a531-176">Replace the following:</span></span>  
  
    ```  
    [<column,name>   
    ```  
  
     <span data-ttu-id="7a531-177">with:</span><span class="sxs-lookup"><span data-stu-id="7a531-177">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="7a531-178">次の部分を探します。</span><span class="sxs-lookup"><span data-stu-id="7a531-178">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="7a531-179">with:</span><span class="sxs-lookup"><span data-stu-id="7a531-179">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
     <span data-ttu-id="7a531-180">最終的なステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7a531-180">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT DISTINCT [Bike Buyer]   
    FROM [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="7a531-181">[**ファイル**] メニューの [**名前を付けて DMXQuery1 を保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-181">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="7a531-182">[名前を**付けて保存**] ダイアログボックスで、適切なフォルダーを参照し、ファイル名を指定し `SELECT_DISCRETE.dmx` ます。</span><span class="sxs-lookup"><span data-stu-id="7a531-182">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_DISCRETE.dmx`.</span></span>  
  
7.  <span data-ttu-id="7a531-183">ツールバーの [**実行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a531-183">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="7a531-184">クエリが実行され、Bike Buyer 列の可能な状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="7a531-184">The query returns the possible states of the Bike Buyer column.</span></span>  
  
 <span data-ttu-id="7a531-185">次のレッスンでは、デシジョン ツリー マイニング モデルを使用して、潜在顧客が自転車の購入者になるかどうかを予測します。</span><span class="sxs-lookup"><span data-stu-id="7a531-185">In the next lesson, you will predict whether potential customers will be bike buyers by using the decision tree mining model.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="7a531-186">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="7a531-186">Next Lesson</span></span>  
 [<span data-ttu-id="7a531-187">レッスン 5: 予測クエリの実行</span><span class="sxs-lookup"><span data-stu-id="7a531-187">Lesson 5: Executing Prediction Queries</span></span>](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
  
  
