---
title: モデルへの予測関数の適用 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Model Prediction [Analysis Services], selecting mining models
ms.assetid: cf9a97e2-c249-441b-af12-c977c1a91c44
author: minewiskan
ms.author: owend
ms.openlocfilehash: fde9de00adaa1712a9db6e18aabc6a83dd660efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632188"
---
# <a name="apply-prediction-functions-to-a-model"></a><span data-ttu-id="c11a0-102">モデルへの予測関数の適用</span><span class="sxs-lookup"><span data-stu-id="c11a0-102">Apply Prediction Functions to a Model</span></span>
  <span data-ttu-id="c11a0-103">予測クエリを作成するには、クエリの基になるマイニング モデルを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c11a0-103">To create a prediction query, you must first select the mining model on which the query will be based.</span></span> <span data-ttu-id="c11a0-104">現在のプロジェクトに存在するマイニング モデルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-104">You can select any mining model that exists in the current project.</span></span>  
  
 <span data-ttu-id="c11a0-105">モデルを選択した後は、クエリに " *予測関数* " を追加します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-105">After you have selected a model, add a *prediction function* to the query.</span></span> <span data-ttu-id="c11a0-106">これは、予測関数がさまざまな目的で使用されることを理解するためにインポートされています。また、値を予測することもできますが、関連する統計や、予測の生成に使用された情報を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-106">It is import to understand that prediction functions are used for many purposes-yes, you can predict values, but you can also get related statistics, as well as information that was used in generating the prediction.</span></span> <span data-ttu-id="c11a0-107">予測関数は、次の種類の値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-107">Prediction functions can return the following types of values:</span></span>  
  
-   <span data-ttu-id="c11a0-108">予測可能な属性の名前と、予測された値。</span><span class="sxs-lookup"><span data-stu-id="c11a0-108">The name of the predictable attribute, and the value that is predicted.</span></span>  
  
-   <span data-ttu-id="c11a0-109">予測値の分布と分散に関する統計。</span><span class="sxs-lookup"><span data-stu-id="c11a0-109">Statistics about the distribution and variance of the predicted values.</span></span>  
  
-   <span data-ttu-id="c11a0-110">指定した結果、またはすべての可能な結果の確率。</span><span class="sxs-lookup"><span data-stu-id="c11a0-110">The probability of a specified outcome, or of all possible outcomes.</span></span>  
  
-   <span data-ttu-id="c11a0-111">トップ (最高) またはボトム (最低) のスコアまたは値。</span><span class="sxs-lookup"><span data-stu-id="c11a0-111">The top or bottom scores or values.</span></span>  
  
-   <span data-ttu-id="c11a0-112">指定したノード、オブジェクト、または属性に関連付けられた値。</span><span class="sxs-lookup"><span data-stu-id="c11a0-112">Values associated with a specified node, object, or attribute.</span></span>  
  
 <span data-ttu-id="c11a0-113">使用できる予測関数は多種多様ですが、作成したモデルの種類に適した関数を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c11a0-113">There is a wide variety of prediction functions that you can use, but you must choose the function that suits the type of model you created.</span></span> <span data-ttu-id="c11a0-114">通常、この選択は、モデルの作成に使用したアルゴリズムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c11a0-114">Usually this choice depends on the algorithm used to create the model.</span></span>  
  
-   <span data-ttu-id="c11a0-115">ほぼすべてのモデルの種類でサポートされている予測関数の一覧については、「[一般的な予測関数 &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c11a0-115">For a list of the prediction functions that are supported for almost all model types, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span>  
  
-   <span data-ttu-id="c11a0-116">さらに、個々のアルゴリズムは、さまざまな特別な関数をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c11a0-116">Additionally, individual algorithms support a variety of specialized functions.</span></span> <span data-ttu-id="c11a0-117">たとえば、Microsoft クラスタリング アルゴリズムに基づくマイニング モデルを作成する場合は、クラスターに関する情報 (データ値からクラスター重心までの距離など) を取得するための特別な予測関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-117">For example, if you create a mining model based on the Microsoft Clustering algorithm, you can use specialized prediction functions to find information about the clusters, such as the distance from a data value to the cluster centroid.</span></span>  
  
     <span data-ttu-id="c11a0-118">特定の種類のマイニング モデルに対するクエリの実行方法の例については、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md)」のアルゴリズム リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c11a0-118">For examples of how to query a specific type of mining model, see the algorithm reference topic, in [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
### <a name="choose-a-mining-model-to-use-for-prediction"></a><span data-ttu-id="c11a0-119">予測に使用するマイニング モデルの選択</span><span class="sxs-lookup"><span data-stu-id="c11a0-119">Choose a mining model to use for prediction</span></span>  
  
1.  <span data-ttu-id="c11a0-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でモデルを右クリックし、 **[予測クエリの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-120">From [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the model, and select **Build Prediction Query**.</span></span>  
  
     <span data-ttu-id="c11a0-121">-- または --</span><span class="sxs-lookup"><span data-stu-id="c11a0-121">--OR --</span></span>  
  
     <span data-ttu-id="c11a0-122">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[マイニング モデル予測]** タブをクリックし、 **[マイニング モデル]** テーブルの  **[モデルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c11a0-122">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the tab, **Mining Model Prediction**, and then click **Select Model** in the  **Mining Model** table.</span></span>  
  
2.  <span data-ttu-id="c11a0-123">**[マイニング モデルの選択]** ダイアログ ボックスでマイニング モデルを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c11a0-123">In the **Select Mining Model** dialog box, select a mining model, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c11a0-124">現在の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内の任意のモデルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-124">You can choose any model within the current [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="c11a0-125">別のデータベース内のモデルを使用してクエリを作成するには、そのデータベースのコンテキストで新しいクエリ ウィンドウを開くか、そのモデルを含んでいるソリューション ファイルを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="c11a0-125">To create a query using a model in a different database, you must either open a new query window in the context of that database, or open the solution file that contains that model.</span></span>  
  
### <a name="add-prediction-functions-to-a-query"></a><span data-ttu-id="c11a0-126">クエリへの予測関数の追加</span><span class="sxs-lookup"><span data-stu-id="c11a0-126">Add prediction functions to a query</span></span>  
  
1.  <span data-ttu-id="c11a0-127">**[予測クエリ ビルダー]** で、 **[単一クエリ入力]** ダイアログ ボックスで値を指定するか、モデルを外部データ ソースにマップして、予測に使用する入力データを構成します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-127">In the **Prediction Query Builder**, configure the input data used for prediction, either by providing values in the **Singleton Query Input** dialog box, or by mapping the model to an external data source.</span></span>  
  
     <span data-ttu-id="c11a0-128">詳細については、「 [予測クエリの入力データの選択およびマップ](choose-and-map-input-data-for-a-prediction-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c11a0-128">For more information, see [Choose and Map Input Data for a Prediction Query](choose-and-map-input-data-for-a-prediction-query.md).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="c11a0-129">予測を生成するための入力を用意する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c11a0-129">It is not required that you provide inputs to generate predictions.</span></span> <span data-ttu-id="c11a0-130">入力がない場合は、通常、アルゴリズムがすべての可能な入力を通じて最も可能性の高い予測値を返します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-130">When there is no input, the algorithm will typically return the mostly likely predicted value across all possible inputs.</span></span>  
  
2.  <span data-ttu-id="c11a0-131">**[ソース]** 列をクリックし、一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-131">Click the **Source** column, and choose a value from the list:</span></span>  
  
    |||  
    |-|-|  
    |**\<model name>**|<span data-ttu-id="c11a0-132">このオプションを選択すると、マイニング モデルの値が結果に含められます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-132">Select this option to include values from the mining model in the output.</span></span> <span data-ttu-id="c11a0-133">予測可能な列のみを追加できます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-133">You can only add predictable columns.</span></span><br /><br /> <span data-ttu-id="c11a0-134">モデルから列を追加すると、返される結果はその列の値の個別でないリストになります。</span><span class="sxs-lookup"><span data-stu-id="c11a0-134">When you add a column from the model, the result returned is the non-distinct list of values in that column.</span></span><br /><br /> <span data-ttu-id="c11a0-135">このオプションで追加する列は、作成される DMX ステートメントの SELECT 部分に含まれます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-135">The columns that you add with this option are included in the SELECT portion of the resulting DMX statement.</span></span>|  
    |<span data-ttu-id="c11a0-136">**Prediction Function**</span><span class="sxs-lookup"><span data-stu-id="c11a0-136">**Prediction Function**</span></span>|<span data-ttu-id="c11a0-137">このオプションを選択すると、予測関数の一覧を参照できます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-137">Select this option to browse a list of prediction functions.</span></span><br /><br /> <span data-ttu-id="c11a0-138">選択した値または関数は、作成される DMX ステートメントの SELECT 部分に追加されます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-138">The values or functions you select are added to the SELECT portion of the resulting DMX statement.</span></span><br /><br /> <span data-ttu-id="c11a0-139">予測関数の一覧が、選択したモデルの種類によってフィルター処理や制限を受けることはありません。</span><span class="sxs-lookup"><span data-stu-id="c11a0-139">The list of prediction functions is not filtered or constrained by the type of model you have selected.</span></span> <span data-ttu-id="c11a0-140">そのため、現在のモデルの種類で関数がサポートされていることが確実でない場合は、関数を一覧に追加して、エラーが起きないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-140">Therefore, if you have any doubt about whether the function is supported for the current model type, you can just add the function to the list and see if there is an error.</span></span><br /><br /> <span data-ttu-id="c11a0-141">$ で始まる一覧の項目 ($AdjustedProbability など) は、関数の `PredictHistogram` を使用した場合の結果である、入れ子になったテーブルの列を表しています。</span><span class="sxs-lookup"><span data-stu-id="c11a0-141">List items that are preceded by $ (such as $AdjustedProbability) represent columns from the nested table that is output when you use the function, `PredictHistogram`.</span></span> <span data-ttu-id="c11a0-142">これらは、入れ子になったテーブルの代わりに単一の列を返すために使用できるショートカットです。</span><span class="sxs-lookup"><span data-stu-id="c11a0-142">These are shortcuts that you can use to return a single column and not a nested table.</span></span>|  
    |<span data-ttu-id="c11a0-143">**カスタム式**</span><span class="sxs-lookup"><span data-stu-id="c11a0-143">**Custom Expression**</span></span>|<span data-ttu-id="c11a0-144">このオプションを選択すると、カスタム式を入力し、結果に別名を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-144">Select this option to type a custom expression and then assign an alias to the output.</span></span><br /><br /> <span data-ttu-id="c11a0-145">カスタム式は、作成される DMX 予測クエリの SELECT 部分に追加されます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-145">The custom expression is added to the SELECT portion of the resulting DMX prediction query.</span></span><br /><br /> <span data-ttu-id="c11a0-146">このオプションは、各行で結果のためのテキストを追加して、VB 関数やカスタム ストアド プロシージャを呼び出す場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c11a0-146">This option is useful if you want to add text for output with each row, to call VB functions, or to call custom stored procedures.</span></span><br /><br /> <span data-ttu-id="c11a0-147">DMX から VBA および Excel 関数を使用する方法の詳細については、「 [MDX および DAX での VBA 関数](/sql/mdx/vba-functions-in-mdx-and-dax)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c11a0-147">For information about using VBA and Excel functions from DMX, see [VBA functions in MDX and DAX](/sql/mdx/vba-functions-in-mdx-and-dax).</span></span>|  
  
3.  <span data-ttu-id="c11a0-148">各関数または式の追加後は、DMX ビューに切り替えて、関数がどのように DMX ステートメント内に追加されたかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-148">After adding each function or expression, switch to DMX view to see how the function is added within the DMX statement.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="c11a0-149">予測クエリ ビルダーでは、 **[結果]** をクリックするまで、DMX は検証されません。</span><span class="sxs-lookup"><span data-stu-id="c11a0-149">The Prediction Query Builder does not validate the DMX until you click **Results**.</span></span> <span data-ttu-id="c11a0-150">クエリ ビルダーによって生成された式は、有効な DMX でないことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="c11a0-150">Often, you will find that the expression that is produced by the query builder is not valid DMX.</span></span> <span data-ttu-id="c11a0-151">主な原因は、予測可能列に関連付けられていない列の参照や、入れ子になったテーブル内の列の予測 (サブ SELECT ステートメントが必要) です。</span><span class="sxs-lookup"><span data-stu-id="c11a0-151">Typical causes are referencing a column that is not related to the predictable column, or trying to predict a column in a nested table, which requires a sub-SELECT statement.</span></span> <span data-ttu-id="c11a0-152">この時点で、DMX ビューに切り替えて、ステートメントの編集を続行できます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-152">At this point, you can switch to DMX view and continue editing the statement.</span></span>  
  
### <a name="example-create-a-query-on-a-clustering-model"></a><span data-ttu-id="c11a0-153">例: クラスター モデルに対するクエリの作成</span><span class="sxs-lookup"><span data-stu-id="c11a0-153">Example: Create a query on a clustering model</span></span>  
  
1.  <span data-ttu-id="c11a0-154">このサンプル クエリを作成するために使用できるクラスター モデルがない場合は、 [基本的なデータ マイニング チュートリアル](../../tutorials/basic-data-mining-tutorial.md)を使用して、モデルの [TM_Clustering] を作成してください。</span><span class="sxs-lookup"><span data-stu-id="c11a0-154">If you do not have a clustering model available for building this sample query, create the model, [TM_Clustering], using the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="c11a0-155">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でモデルの [TM_Clustering] を右クリックし、 **[予測クエリの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-155">From [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the model, [TM_Clustering], and select **Build Prediction Query**.</span></span>  
  
3.  <span data-ttu-id="c11a0-156">**[マイニング モデル]** メニューの **[単一クエリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-156">From the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
4.  <span data-ttu-id="c11a0-157">**[単一クエリ入力]** ダイアログ ボックスで、入力として次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-157">In the **Singleton Query Input** dialog box, set the following values as inputs:</span></span>  
  
    -   <span data-ttu-id="c11a0-158">Gender = M</span><span class="sxs-lookup"><span data-stu-id="c11a0-158">Gender = M</span></span>  
  
    -   <span data-ttu-id="c11a0-159">Commute Distance = 5-10 miles</span><span class="sxs-lookup"><span data-stu-id="c11a0-159">Commute Distance = 5-10 miles</span></span>  
  
5.  <span data-ttu-id="c11a0-160">クエリ グリッドの **[ソース]** で TM_Clustering マイニング モデルを選択し、列の [Bike Buyer] を追加します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-160">In the query grid, for **Source**, select TM_Clustering mining model, and add the column, [Bike Buyer].</span></span>  
  
6.  <span data-ttu-id="c11a0-161">[**ソース**] で [**予測関数**] を選択し、関数を追加し `Cluster` ます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-161">For **Source**, select **Prediction Function**, and add the function, `Cluster`.</span></span>  
  
7.  <span data-ttu-id="c11a0-162">[**ソース**] で [**予測関数**] を選択し、関数を追加 `PredictSupport` して、モデル列 [自転車購入者] を [**条件と引数**] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c11a0-162">For **Source**, select **Prediction Function**, add the function, `PredictSupport`, and drag the model column [Bike Buyer] into the **Criteria/Argument** box.</span></span> <span data-ttu-id="c11a0-163">**[別名]** 列に「 **Support** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-163">Type **Support** in the **Alias** column.</span></span>  
  
     <span data-ttu-id="c11a0-164">予測関数を表す式および列参照を **[条件と引数]** ボックスからコピーします。</span><span class="sxs-lookup"><span data-stu-id="c11a0-164">Copy the expression representing the prediction function and column reference from the **Criteria/Argument** box.</span></span>  
  
8.  <span data-ttu-id="c11a0-165">**[ソース]** で **[カスタム式]** を選択し、別名を入力してから、次の構文を使用して Excel の CEILING 関数を参照します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-165">For **Source**, select **Custom Expression**, type an alias, and then reference the Excel CEILING function by using the following syntax:</span></span>  
  
    ```  
    Excel![CEILING](<arguments) as <return type>  
    ```  
  
     <span data-ttu-id="c11a0-166">関数の引数として列参照を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-166">Paste the column reference in as the argument to the function.</span></span>  
  
     <span data-ttu-id="c11a0-167">たとえば、次の式ではサポート値の CEILING が返されます。</span><span class="sxs-lookup"><span data-stu-id="c11a0-167">For example, the following expression returns the CEILING of the support value:</span></span>  
  
    ```  
    EXCEL!CEILING(PredictSupport([TM_Clustering].[Bike Buyer]),2)  
    ```  
  
     <span data-ttu-id="c11a0-168">**[別名]** 列に「CEILING」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-168">Type CEILING in the **Alias** column.</span></span>  
  
9. <span data-ttu-id="c11a0-169">**[クエリ テキスト ビューに切り替え]** をクリックして、生成された DMX ステートメントを確認してから、 **[クエリ結果ビューに切り替え]** をクリックして、予測クエリによって出力された列を表示します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-169">Click **Switch to query text view** to review the DMX statement that was generated, and then click **Switch to query result view** to see the columns output by the prediction query.</span></span>  
  
     <span data-ttu-id="c11a0-170">予想される結果を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c11a0-170">The following table shows the expected results:</span></span>  
  
    |<span data-ttu-id="c11a0-171">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="c11a0-171">Bike Buyer</span></span>|<span data-ttu-id="c11a0-172">$Cluster</span><span class="sxs-lookup"><span data-stu-id="c11a0-172">$Cluster</span></span>|<span data-ttu-id="c11a0-173">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="c11a0-173">SUPPORT</span></span>|<span data-ttu-id="c11a0-174">CEILING</span><span class="sxs-lookup"><span data-stu-id="c11a0-174">CEILING</span></span>|  
    |----------------|--------------|-------------|-------------|  
    |<span data-ttu-id="c11a0-175">0</span><span class="sxs-lookup"><span data-stu-id="c11a0-175">0</span></span>|<span data-ttu-id="c11a0-176">Cluster 8</span><span class="sxs-lookup"><span data-stu-id="c11a0-176">Cluster 8</span></span>|<span data-ttu-id="c11a0-177">954</span><span class="sxs-lookup"><span data-stu-id="c11a0-177">954</span></span>|<span data-ttu-id="c11a0-178">953.948638926372</span><span class="sxs-lookup"><span data-stu-id="c11a0-178">953.948638926372</span></span>|  
  
 <span data-ttu-id="c11a0-179">ステートメントの他の場所に他の句を追加する必要がある場合 (たとえば、WHERE 句を追加する場合)、グリッドを使用して追加することはできません。最初に DMX ビューに切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="c11a0-179">If you want to add other clauses elsewhere in the statement-for example, if you want to add a WHERE clause-you cannot add it by using the grid; you must switch to DMX view first.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c11a0-180">参照</span><span class="sxs-lookup"><span data-stu-id="c11a0-180">See Also</span></span>  
 [<span data-ttu-id="c11a0-181">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="c11a0-181">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
