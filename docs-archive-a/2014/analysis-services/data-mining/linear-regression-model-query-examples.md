---
title: 線形回帰モデルのクエリ例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- content queries [DMX]
ms.assetid: fd3cf312-57a1-44b6-b772-fce6fc1c26d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02d4b7309d7b5ea3d6295089f0fb2e778b1c9b4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645271"
---
# <a name="linear-regression-model-query-examples"></a><span data-ttu-id="c3f1c-102">線形回帰モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="c3f1c-102">Linear Regression Model Query Examples</span></span>
  <span data-ttu-id="c3f1c-103">データ マイニング モデルに対するクエリを作成する際には、コンテンツ クエリを作成することも、予測クエリを作成することもできます。コンテンツ クエリでは、分析で検出されたパターンの詳細情報を取得できます。予測クエリでは、モデル内のパターンを使用して新しいデータについての予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="c3f1c-104">たとえばコンテンツ クエリを使用すると、回帰式に関する追加情報を取得できるのに対し、予測クエリを使用すると、新しいデータ ポイントがモデルに適合するかどうかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-104">For example, a content query might provide additional details about the regression formula, while a prediction query might tell you if a new data point fits the model.</span></span> <span data-ttu-id="c3f1c-105">クエリを使用してモデルに関するメタデータを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="c3f1c-106">ここでは、Microsoft 線形回帰アルゴリズムに基づいたモデルに対するクエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-106">This section explains how to create queries for models that are based on the Microsoft Linear Regression algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3f1c-107">線形回帰アルゴリズムは、Microsoft デシジョン ツリー アルゴリズムの特殊なケースに基づいているため、これと多くの類似点があります。また、連続する予測可能属性を使用する一部のデシジョン ツリーには、回帰式を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-107">Because linear regression is based on a special case of the Microsoft Decision Trees algorithm, there are many similarities, and some decision tree models that use continuous predictable attributes can contain regression formulas.</span></span> <span data-ttu-id="c3f1c-108">詳細については、「 [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](microsoft-decision-trees-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-108">For more information, see [Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="c3f1c-109">**コンテンツクエリ**</span><span class="sxs-lookup"><span data-stu-id="c3f1c-109">**Content queries**</span></span>  
  
 [<span data-ttu-id="c3f1c-110">データ マイニング スキーマ行セットを使用してモデルに対して使用されたパラメーターを特定する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-110">Using the Data Mining Schema Rowset to determine parameters used for a model</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="c3f1c-111">DMX を使用してモデルの回帰式を取得する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-111">Using DMX to return the regression formula for the model</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="c3f1c-112">モデルの係数のみを取得する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-112">Returning only the coefficient for the model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="c3f1c-113">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="c3f1c-113">**Prediction queries**</span></span>  
  
 [<span data-ttu-id="c3f1c-114">単一クエリを使用して収入を予測する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-114">Predicting income using a singleton query</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="c3f1c-115">回帰モデルで予測関数を使用する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-115">Using prediction functions with a regression model</span></span>](#bkmk_Query5)  
  
##  <a name="finding-information-about-the-linear-regression-model"></a><a name="bkmk_top"></a><span data-ttu-id="c3f1c-116">線形回帰モデルに関する情報の検索</span><span class="sxs-lookup"><span data-stu-id="c3f1c-116">Finding Information about the Linear Regression Model</span></span>  
 <span data-ttu-id="c3f1c-117">線形回帰モデルの構造は非常に単純であり、マイニング モデルではデータを単一のノードとして表現されます。このノードは回帰式を定義します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-117">The structure of a linear regression model is extremely simple: the mining model represents the data as a single node, which defines the regression formula.</span></span> <span data-ttu-id="c3f1c-118">詳細については、「 [ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-logistic-regression-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-118">For more information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
 [<span data-ttu-id="c3f1c-119">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="c3f1c-119">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-determine-parameters-used-for-a-model"></a><a name="bkmk_Query1"></a><span data-ttu-id="c3f1c-120">サンプルクエリ 1: データマイニングスキーマ行セットを使用してモデルに使用されるパラメーターを特定する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-120">Sample Query 1: Using the Data Mining Schema Rowset to Determine Parameters Used for a Model</span></span>  
 <span data-ttu-id="c3f1c-121">データ マイニング スキーマ行セットに対してクエリを実行すると、モデルに関するメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-121">By querying the data mining schema rowset, you can find metadata about the model.</span></span> <span data-ttu-id="c3f1c-122">このメタデータには、モデルが作成された日時、モデルが最後に処理された日時、モデルの基になるマイニング構造の名前、予測可能な属性として使用されている列の名前などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-122">This might include when the model was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column designated as the predictable attribute.</span></span> <span data-ttu-id="c3f1c-123">モデルが最初に作成されたときに使用されたパラメーターを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-123">You can also return the parameters that were used when the model was first created.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_PredictIncome'  
```  
  
 <span data-ttu-id="c3f1c-124">サンプルの結果 :</span><span class="sxs-lookup"><span data-stu-id="c3f1c-124">Sample results:</span></span>  
  
|<span data-ttu-id="c3f1c-125">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3f1c-125">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="c3f1c-126">COMPLEXITY_PENALTY=0.9,</span><span class="sxs-lookup"><span data-stu-id="c3f1c-126">COMPLEXITY_PENALTY=0.9,</span></span><br /><br /> <span data-ttu-id="c3f1c-127">MAXIMUM_INPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="c3f1c-127">MAXIMUM_INPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="c3f1c-128">MAXIMUM_OUTPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="c3f1c-128">MAXIMUM_OUTPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="c3f1c-129">MINIMUM_SUPPORT=10,</span><span class="sxs-lookup"><span data-stu-id="c3f1c-129">MINIMUM_SUPPORT=10,</span></span><br /><br /> <span data-ttu-id="c3f1c-130">SCORE_METHOD=4,</span><span class="sxs-lookup"><span data-stu-id="c3f1c-130">SCORE_METHOD=4,</span></span><br /><br /> <span data-ttu-id="c3f1c-131">SPLIT_METHOD=3,</span><span class="sxs-lookup"><span data-stu-id="c3f1c-131">SPLIT_METHOD=3,</span></span><br /><br /> <span data-ttu-id="c3f1c-132">FORCE_REGRESSOR=</span><span class="sxs-lookup"><span data-stu-id="c3f1c-132">FORCE_REGRESSOR=</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c3f1c-133">パラメーター設定 "`FORCE_REGRESSOR =` " は、FORCE_REGRESSOR パラメーターの現在の値が NULL であることを示します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-133">The parameter setting, "`FORCE_REGRESSOR =` ", indicates that the current value for the FORCE_REGRESSOR parameter is null.</span></span>  
  
 [<span data-ttu-id="c3f1c-134">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="c3f1c-134">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-2-retrieving-the-regression-formula-for-the-model"></a><a name="bkmk_Query2"></a><span data-ttu-id="c3f1c-135">サンプルクエリ 2: モデルの回帰式を取得する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-135">Sample Query 2: Retrieving the Regression Formula for the Model</span></span>  
 <span data-ttu-id="c3f1c-136">次のクエリでは、「 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)」で使用したものと同じ Targeted Mailing データ ソースを使用して作成された線形回帰モデルのマイニング モデル コンテンツを返します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-136">The following query returns the mining model content for a linear regression model that was built by using the same Targeted Mailing data source that was used in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="c3f1c-137">このモデルでは、年齢に基づいて顧客の収入を予測します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-137">This model predicts customer income based on age.</span></span>  
  
 <span data-ttu-id="c3f1c-138">このクエリは、回帰式を含むノードのコンテンツを返します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-138">The query returns the contents of the node that contains the regression formula.</span></span> <span data-ttu-id="c3f1c-139">各変数と係数は、入れ子になった NODE_DISTRIBUTION テーブルの個別の行に保存されます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-139">Each variable and coefficient is stored in a separate row of the nested NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="c3f1c-140">完全な回帰式を表示する場合は、 [Microsoft ツリー ビューアー](browse-a-model-using-the-microsoft-tree-viewer.md)を使用します。 **[(すべて)]** ノードをクリックして **[マイニング凡例]** を開くと表示されます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-140">If you want to view the complete regression formula, use the [Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md), click the **(All)** node, and open the **Mining Legend**.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION as t  
FROM LR_PredictIncome.CONTENT  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c3f1c-141">`SELECT <column name> from NODE_DISTRIBUTION`のようなクエリを使用して入れ子になったテーブルの個々の列を参照する場合、 **SUPPORT** や **PROBABILITY**などの一部の列名は、同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-141">If you reference individual columns of the nested table by using a query such as `SELECT <column name> from NODE_DISTRIBUTION`, some columns, such as **SUPPORT** or **PROBABILITY**, must be enclosed in brackets to distinguish them from reserved keywords of the same name.</span></span>  
  
 <span data-ttu-id="c3f1c-142">期待される結果:</span><span class="sxs-lookup"><span data-stu-id="c3f1c-142">Expected results:</span></span>  
  
|<span data-ttu-id="c3f1c-143">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="c3f1c-143">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="c3f1c-144">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="c3f1c-144">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="c3f1c-145">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="c3f1c-145">t.SUPPORT</span></span>|<span data-ttu-id="c3f1c-146">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="c3f1c-146">t.PROBABILITY</span></span>|<span data-ttu-id="c3f1c-147">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="c3f1c-147">t.VARIANCE</span></span>|<span data-ttu-id="c3f1c-148">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="c3f1c-148">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="c3f1c-149">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="c3f1c-149">Yearly Income</span></span>|<span data-ttu-id="c3f1c-150">Missing</span><span class="sxs-lookup"><span data-stu-id="c3f1c-150">Missing</span></span>|<span data-ttu-id="c3f1c-151">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-151">0</span></span>|<span data-ttu-id="c3f1c-152">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="c3f1c-152">0.000457142857142857</span></span>|<span data-ttu-id="c3f1c-153">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-153">0</span></span>|<span data-ttu-id="c3f1c-154">1</span><span class="sxs-lookup"><span data-stu-id="c3f1c-154">1</span></span>|  
|<span data-ttu-id="c3f1c-155">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="c3f1c-155">Yearly Income</span></span>|<span data-ttu-id="c3f1c-156">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="c3f1c-156">57220.8876687257</span></span>|<span data-ttu-id="c3f1c-157">17484</span><span class="sxs-lookup"><span data-stu-id="c3f1c-157">17484</span></span>|<span data-ttu-id="c3f1c-158">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="c3f1c-158">0.999542857142857</span></span>|<span data-ttu-id="c3f1c-159">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="c3f1c-159">1041275619.52776</span></span>|<span data-ttu-id="c3f1c-160">3</span><span class="sxs-lookup"><span data-stu-id="c3f1c-160">3</span></span>|  
|<span data-ttu-id="c3f1c-161">年齢</span><span class="sxs-lookup"><span data-stu-id="c3f1c-161">Age</span></span>|<span data-ttu-id="c3f1c-162">471.687717702463</span><span class="sxs-lookup"><span data-stu-id="c3f1c-162">471.687717702463</span></span>|<span data-ttu-id="c3f1c-163">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-163">0</span></span>|<span data-ttu-id="c3f1c-164">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-164">0</span></span>|<span data-ttu-id="c3f1c-165">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="c3f1c-165">126.969442359327</span></span>|<span data-ttu-id="c3f1c-166">7</span><span class="sxs-lookup"><span data-stu-id="c3f1c-166">7</span></span>|  
|<span data-ttu-id="c3f1c-167">年齢</span><span class="sxs-lookup"><span data-stu-id="c3f1c-167">Age</span></span>|<span data-ttu-id="c3f1c-168">234.680904692439</span><span class="sxs-lookup"><span data-stu-id="c3f1c-168">234.680904692439</span></span>|<span data-ttu-id="c3f1c-169">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-169">0</span></span>|<span data-ttu-id="c3f1c-170">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-170">0</span></span>|<span data-ttu-id="c3f1c-171">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-171">0</span></span>|<span data-ttu-id="c3f1c-172">8</span><span class="sxs-lookup"><span data-stu-id="c3f1c-172">8</span></span>|  
|<span data-ttu-id="c3f1c-173">年齢</span><span class="sxs-lookup"><span data-stu-id="c3f1c-173">Age</span></span>|<span data-ttu-id="c3f1c-174">45.4269617936399</span><span class="sxs-lookup"><span data-stu-id="c3f1c-174">45.4269617936399</span></span>|<span data-ttu-id="c3f1c-175">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-175">0</span></span>|<span data-ttu-id="c3f1c-176">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-176">0</span></span>|<span data-ttu-id="c3f1c-177">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="c3f1c-177">126.969442359327</span></span>|<span data-ttu-id="c3f1c-178">9</span><span class="sxs-lookup"><span data-stu-id="c3f1c-178">9</span></span>|  
||<span data-ttu-id="c3f1c-179">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="c3f1c-179">35793.5477381267</span></span>|<span data-ttu-id="c3f1c-180">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-180">0</span></span>|<span data-ttu-id="c3f1c-181">0</span><span class="sxs-lookup"><span data-stu-id="c3f1c-181">0</span></span>|<span data-ttu-id="c3f1c-182">1012968919.28372</span><span class="sxs-lookup"><span data-stu-id="c3f1c-182">1012968919.28372</span></span>|<span data-ttu-id="c3f1c-183">11</span><span class="sxs-lookup"><span data-stu-id="c3f1c-183">11</span></span>|  
  
 <span data-ttu-id="c3f1c-184">一方、 **[マイニング凡例]** では、回帰式は次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-184">In comparison, in the **Mining Legend**, the regression formula appears as follows:</span></span>  
  
 <span data-ttu-id="c3f1c-185">Yearly Income = 57,220.919 + 471.688 \* (Age - 45.427)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-185">Yearly Income = 57,220.919 + 471.688 \* (Age - 45.427)</span></span>  
  
 <span data-ttu-id="c3f1c-186">**[マイニング凡例]** ではいくつかの数字が丸められますが、NODE_DISTRIBUTION テーブルと **[マイニング凡例]** には基本的に同じ値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-186">You can see that in the **Mining Legend**, some numbers are rounded; however, the NODE_DISTRIBUTION table and the **Mining Legend** essentially contain the same values.</span></span>  
  
 <span data-ttu-id="c3f1c-187">VALUETYPE 列の値を参照すると、各行に含まれている情報の種類がわかるため、結果をプログラムで処理する場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-187">The values in the VALUETYPE column tell you what kind of information is contained in each row, which is useful if you are processing the results programmatically.</span></span> <span data-ttu-id="c3f1c-188">次の表に、線形回帰式の出力となる値の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-188">The following table shows the value types that are output for a linear regression formula.</span></span>  
  
|<span data-ttu-id="c3f1c-189">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="c3f1c-189">VALUETYPE</span></span>|  
|---------------|  
|<span data-ttu-id="c3f1c-190">1 (Missing: 不足)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-190">1 (Missing)</span></span>|  
|<span data-ttu-id="c3f1c-191">3 (Continuous: 連続)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-191">3 (Continuous)</span></span>|  
|<span data-ttu-id="c3f1c-192">7 (Coefficient: 係数)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-192">7 (Coefficient)</span></span>|  
|<span data-ttu-id="c3f1c-193">8 (Score Gain: スコア ゲイン)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-193">8 (Score Gain)</span></span>|  
|<span data-ttu-id="c3f1c-194">9 (Statistics: 統計)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-194">9 (Statistics)</span></span>|  
|<span data-ttu-id="c3f1c-195">7 (Coefficient: 係数)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-195">7 (Coefficient)</span></span>|  
|<span data-ttu-id="c3f1c-196">8 (Score Gain: スコア ゲイン)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-196">8 (Score Gain)</span></span>|  
|<span data-ttu-id="c3f1c-197">9 (Statistics: 統計)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-197">9 (Statistics)</span></span>|  
|<span data-ttu-id="c3f1c-198">11 (Intercept: 切片)</span><span class="sxs-lookup"><span data-stu-id="c3f1c-198">11 (Intercept)</span></span>|  
  
 <span data-ttu-id="c3f1c-199">回帰モデルの各値の種類の意味については、「 [線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-199">For more information about the meaning of each value type for regression models, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="c3f1c-200">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="c3f1c-200">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-3-returning-only-the-coefficient-for-the-model"></a><a name="bkmk_Query3"></a><span data-ttu-id="c3f1c-201">サンプルクエリ 3: モデルの係数のみを取得する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-201">Sample Query 3: Returning Only the Coefficient for the Model</span></span>  
 <span data-ttu-id="c3f1c-202">VALUETYPE 列挙を使用すると、次のクエリに示すように回帰式の係数のみを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-202">By using the VALUETYPE enumeration, you can return only the coefficient for the regression equation, as shown in the following query:</span></span>  
  
```  
SELECT FLATTENED MODEL_NAME,  
    (SELECT ATTRIBUTE_VALUE, VALUETYPE  
     FROM NODE_DISTRIBUTION  
     WHERE VALUETYPE = 11)   
AS t  
FROM LR_PredictIncome.CONTENT  
```  
  
 <span data-ttu-id="c3f1c-203">このクエリでは、マイニング モデル コンテンツの行と、係数を含む入れ子になったテーブルの行の 2 つの行が返されます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-203">This query returns two rows, one from the mining model content, and the row from the nested table that contains the coefficient.</span></span> <span data-ttu-id="c3f1c-204">ATTRIBUTE_NAME 列は、係数に対して常に空であるためここには含まれていません。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-204">The ATTRIBUTE_NAME column is not included here because it is always blank for the coefficient.</span></span>  
  
|<span data-ttu-id="c3f1c-205">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="c3f1c-205">MODEL_NAME</span></span>|<span data-ttu-id="c3f1c-206">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="c3f1c-206">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="c3f1c-207">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="c3f1c-207">t.VALUETYPE</span></span>|  
|-----------------|------------------------|-----------------|  
|<span data-ttu-id="c3f1c-208">LR_PredictIncome</span><span class="sxs-lookup"><span data-stu-id="c3f1c-208">LR_PredictIncome</span></span>|||  
|<span data-ttu-id="c3f1c-209">LR_PredictIncome</span><span class="sxs-lookup"><span data-stu-id="c3f1c-209">LR_PredictIncome</span></span>|<span data-ttu-id="c3f1c-210">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="c3f1c-210">35793.5477381267</span></span>|<span data-ttu-id="c3f1c-211">11</span><span class="sxs-lookup"><span data-stu-id="c3f1c-211">11</span></span>|  
  
 [<span data-ttu-id="c3f1c-212">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="c3f1c-212">Return to Top</span></span>](#bkmk_top)  
  
## <a name="making-predictions-from-a-linear-regression-model"></a><span data-ttu-id="c3f1c-213">線形回帰モデルから予測を作成する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-213">Making Predictions from a Linear Regression Model</span></span>  
 <span data-ttu-id="c3f1c-214">データ マイニング デザイナーの [マイニング モデル予測] タブを使用して、線形回帰モデルに対する予測クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-214">You can build prediction queries on linear regression models by using the Mining Model Prediction tab in Data Mining Designer.</span></span> <span data-ttu-id="c3f1c-215">予測クエリ ビルダーは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-215">The prediction query builder is available in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3f1c-216">また、Excel 用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データ マイニング アドインまたは Excel 用 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] データ マイニング アドインを使用して回帰モデルに対するクエリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-216">You can also create queries on regression models by using the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Data Mining Add-ins for Excel or the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Data Mining Add-ins for Excel.</span></span> <span data-ttu-id="c3f1c-217">Excel 用 データ マイニング アドインでは回帰モデルが作成されませんが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに格納されているマイニング モデルを参照したり、照会したりすることはできます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-217">Even though the Data Mining Add-ins for Excel do not create regression models, you can browse and query any mining model that is stored on an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="c3f1c-218">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="c3f1c-218">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-4-predicting-income-using-a-singleton-query"></a><a name="bkmk_Query4"></a> <span data-ttu-id="c3f1c-219">サンプル クエリ 4: 単一クエリを使用して収入を予測する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-219">Sample Query 4: Predicting Income using a Singleton Query</span></span>  
 <span data-ttu-id="c3f1c-220">回帰モデルで単一クエリを作成する最も簡単な方法は、 **[単一クエリ入力]** ダイアログ ボックスを使用することです。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-220">The easiest way to create a single query on a regression model is by using the **Singleton Query Input** dialog box.</span></span> <span data-ttu-id="c3f1c-221">たとえば、次の DMX クエリを作成するには、適切な回帰モデルを選択し、[**単一クエリ**] を選択して、 `20` **Age**の値として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-221">For example, you can build the following DMX query by selecting the appropriate regression model, choosing **Singleton Query**, and then typing `20` as the value for **Age**.</span></span>  
  
```  
SELECT [LR_PredictIncome].[Yearly Income]  
From   [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 <span data-ttu-id="c3f1c-222">サンプルの結果 :</span><span class="sxs-lookup"><span data-stu-id="c3f1c-222">Sample results:</span></span>  
  
|<span data-ttu-id="c3f1c-223">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="c3f1c-223">Yearly Income</span></span>|  
|-------------------|  
|<span data-ttu-id="c3f1c-224">45227.302092176</span><span class="sxs-lookup"><span data-stu-id="c3f1c-224">45227.302092176</span></span>|  
  
 [<span data-ttu-id="c3f1c-225">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="c3f1c-225">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-5-using-prediction-functions-with-a-regression-model"></a><a name="bkmk_Query5"></a><span data-ttu-id="c3f1c-226">サンプルクエリ 5: 回帰モデルで予測関数を使用する</span><span class="sxs-lookup"><span data-stu-id="c3f1c-226">Sample Query 5: Using Prediction Functions with a Regression Model</span></span>  
 <span data-ttu-id="c3f1c-227">線形回帰モデルでは多くの標準の予測関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-227">You can use many of the standard prediction functions with linear regression models.</span></span> <span data-ttu-id="c3f1c-228">次の例は、予測クエリの結果にいくつかの説明的な統計情報を追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-228">The following example illustrates how to add some descriptive statistics to the prediction query results.</span></span> <span data-ttu-id="c3f1c-229">これらの結果から、このモデルの平均からの偏差が相当あることがわかります。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-229">From these results, you can see that there is considerable deviation from the mean for this model.</span></span>  
  
```  
SELECT  
  ([LR_PredictIncome].[Yearly Income]) as [PredIncome],  
  (PredictStdev([LR_PredictIncome].[Yearly Income])) as [StDev1]  
From  
  [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 <span data-ttu-id="c3f1c-230">サンプルの結果 :</span><span class="sxs-lookup"><span data-stu-id="c3f1c-230">Sample results:</span></span>  
  
|<span data-ttu-id="c3f1c-231">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="c3f1c-231">Yearly Income</span></span>|<span data-ttu-id="c3f1c-232">StDev1</span><span class="sxs-lookup"><span data-stu-id="c3f1c-232">StDev1</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="c3f1c-233">45227.302092176</span><span class="sxs-lookup"><span data-stu-id="c3f1c-233">45227.302092176</span></span>|<span data-ttu-id="c3f1c-234">31827.1726561396</span><span class="sxs-lookup"><span data-stu-id="c3f1c-234">31827.1726561396</span></span>|  
  
 [<span data-ttu-id="c3f1c-235">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="c3f1c-235">Return to Top</span></span>](#bkmk_top)  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="c3f1c-236">予測関数の一覧</span><span class="sxs-lookup"><span data-stu-id="c3f1c-236">List of Prediction Functions</span></span>  
 <span data-ttu-id="c3f1c-237">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-237">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="c3f1c-238">これに加え、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムでは、次の表に示す関数もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-238">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3f1c-239">予測関数</span><span class="sxs-lookup"><span data-stu-id="c3f1c-239">Prediction Function</span></span>|<span data-ttu-id="c3f1c-240">使用法</span><span class="sxs-lookup"><span data-stu-id="c3f1c-240">Usage</span></span>|  
|[<span data-ttu-id="c3f1c-241">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c3f1c-241">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="c3f1c-242">あるノードがモデル内の別のノードの子であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-242">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="c3f1c-243">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c3f1c-243">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="c3f1c-244">指定されたノードが現在のケースを含んでいるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-244">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="c3f1c-245">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c3f1c-245">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="c3f1c-246">指定された列に対して、予測された値、または値のセットを返します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-246">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="c3f1c-247">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c3f1c-247">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="c3f1c-248">各ケースの Node_ID を返します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-248">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="c3f1c-249">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c3f1c-249">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="c3f1c-250">予測された値の標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-250">Returns standard deviation for the predicted value.</span></span>|  
|[<span data-ttu-id="c3f1c-251">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c3f1c-251">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="c3f1c-252">指定された状態に対するサポート値を返します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-252">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="c3f1c-253">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c3f1c-253">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="c3f1c-254">指定された列の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-254">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="c3f1c-255">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムに共通する関数の一覧は、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-255">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span> <span data-ttu-id="c3f1c-256">これらの関数の使用方法については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3f1c-256">For more information about how to use these functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f1c-257">参照</span><span class="sxs-lookup"><span data-stu-id="c3f1c-257">See Also</span></span>  
 <span data-ttu-id="c3f1c-258">[Microsoft 線形回帰アルゴリズム](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c3f1c-258">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="c3f1c-259">[データマイニングクエリ](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="c3f1c-259">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="c3f1c-260">[Microsoft 線形回帰アルゴリズムテクニカルリファレンス](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c3f1c-260">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="c3f1c-261">線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="c3f1c-261">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
