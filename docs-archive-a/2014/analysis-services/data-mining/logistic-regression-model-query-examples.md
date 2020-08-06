---
title: ロジスティック回帰モデルのクエリ例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- content queries [DMX]
ms.assetid: 7c8e13a3-5c67-46c2-abfa-4881e6ef9c62
author: minewiskan
ms.author: owend
ms.openlocfilehash: d432d38794e65e8b8bea69608479e330649ee395
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631361"
---
# <a name="logistic-regression-model-query-examples"></a><span data-ttu-id="b8816-102">ロジスティック回帰モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="b8816-102">Logistic Regression Model Query Examples</span></span>
  <span data-ttu-id="b8816-103">データ マイニング モデルに対するクエリを作成する際には、コンテンツ クエリを作成することも、予測クエリを作成することもできます。コンテンツ クエリでは、分析で検出されたパターンの詳細情報を取得できます。予測クエリでは、モデル内のパターンを使用して新しいデータによる予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b8816-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions using new data.</span></span>  
  
 <span data-ttu-id="b8816-104">ここでは、Microsoft ロジスティック回帰アルゴリズムに基づいたモデルに対するクエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8816-104">This section explains how to create queries for models that are based on the Microsoft Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="b8816-105">**コンテンツ クエリ**</span><span class="sxs-lookup"><span data-stu-id="b8816-105">**Content Queries**</span></span>  
  
 [<span data-ttu-id="b8816-106">データ マイニング スキーマ行セットを使用してモデル パラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="b8816-106">Retrieving Model Parameters by Using the Data Mining Schema Rowset</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="b8816-107">DMX を使用してモデルに関する追加の詳細情報を検索する</span><span class="sxs-lookup"><span data-stu-id="b8816-107">Finding Additional Detail about the Model by Using DMX</span></span>](#bkmk_Query2)  
  
 <span data-ttu-id="b8816-108">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="b8816-108">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="b8816-109">連続値の予測を作成する</span><span class="sxs-lookup"><span data-stu-id="b8816-109">Making Predictions for a Continuous Value</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="b8816-110">不連続値の予測を作成する</span><span class="sxs-lookup"><span data-stu-id="b8816-110">Making Predictions for a Discrete Value</span></span>](#bkmk_Query4)  
  
##  <a name="getting-information-about-the-logistic-regression-model"></a><a name="bkmk_top"></a><span data-ttu-id="b8816-111">ロジスティック回帰モデルに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="b8816-111">Getting Information about the Logistic Regression Model</span></span>  
 <span data-ttu-id="b8816-112">ロジスティック回帰モデルは、Microsoft ニューラル ネットワーク アルゴリズムでパラメーターの特殊なセットを使用して作成されます。そのため、ロジスティック回帰モデルには、ニューラル ネットワーク モデルと同じ情報がいくつか含まれますが、ニューラル ネットワーク モデルほど複雑ではありません。</span><span class="sxs-lookup"><span data-stu-id="b8816-112">Logistic regression models are created by using the Microsoft Neural Network algorithm with a special set of parameters; therefore, a logistic regression model has some of the same information as a neural networks model, but is less complex.</span></span> <span data-ttu-id="b8816-113">モデル コンテンツの構造および各種類のノードに格納されている情報の種類については、「 [ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-logistic-regression-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8816-113">To understand the structure of the model content, and which node types store what kind of information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
 <span data-ttu-id="b8816-114">クエリ シナリオを理解するために、中級者向けデータ マイニング チュートリアル「 [レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 (中級者向けデータ マイニング チュートリアル)](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8816-114">To follow along in the query scenarios, you can create a logistic regression model as described in the following section of the Intermediate Data Mining Tutorial: [Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span>  
  
 <span data-ttu-id="b8816-115">また、「 [基本的なデータ マイニング チュートリアル](../../tutorials/basic-data-mining-tutorial.md)」のマイニング構造 Targeted Mailing を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8816-115">You can also use the mining structure, Targeted Mailing, from the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
```  
ALTER MINING STRUCTURE [Targeted Mailing]  
ADD MINING MODEL [TM_Logistic Regression]  
([Customer Key],  
[Age],  
[Bike Buyer] PREDICT,  
[Yearly Income] PREDICT,  
[Commute Distance],  
[English Education],  
Gender,  
[House Owner Flag],  
[Marital Status],  
[Number Cars Owned],  
[Number Children At Home],  
[Region],  
[Total Children]  
)  
USING Microsoft_Logistic_Regression  
```  
  
###  <a name="sample-query-1-retrieving-model-parameters-by-using-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a><span data-ttu-id="b8816-116">サンプルクエリ 1: データマイニングスキーマ行セットを使用してモデルパラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="b8816-116">Sample Query 1: Retrieving Model Parameters by Using the Data Mining Schema Rowset</span></span>  
 <span data-ttu-id="b8816-117">データ マイニング スキーマ行セットに対してクエリを実行すると、モデルに関するメタデータを取得できます (作成された日時、最後に処理された日時、基になるマイニング構造の名前、予測可能な属性として使用されている列の名前など)。</span><span class="sxs-lookup"><span data-stu-id="b8816-117">By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute.</span></span> <span data-ttu-id="b8816-118">次の例では、モデルが最初に作成されたときに使用されたパラメーター、モデルの名前と種類、およびモデルが作成された日付が返されます。</span><span class="sxs-lookup"><span data-stu-id="b8816-118">The following example returns the parameters that were used when the model was first created, together with the name and type of the model, and the date that it was created.</span></span>  
  
```  
SELECT MODEL_NAME, SERVICE_NAME, DATE_CREATED, MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center_LR'  
```  
  
 <span data-ttu-id="b8816-119">サンプルの結果 :</span><span class="sxs-lookup"><span data-stu-id="b8816-119">Sample results:</span></span>  
  
|<span data-ttu-id="b8816-120">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="b8816-120">MODEL_NAME</span></span>|<span data-ttu-id="b8816-121">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="b8816-121">SERVICE_NAME</span></span>|<span data-ttu-id="b8816-122">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b8816-122">DATE_CREATED</span></span>|<span data-ttu-id="b8816-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8816-123">MINING_PARAMETERS</span></span>|  
|-----------------|-------------------|-------------------|------------------------|  
|<span data-ttu-id="b8816-124">Call Center_LR</span><span class="sxs-lookup"><span data-stu-id="b8816-124">Call Center_LR</span></span>|<span data-ttu-id="b8816-125">Microsoft_Logistic_Regression</span><span class="sxs-lookup"><span data-stu-id="b8816-125">Microsoft_Logistic_Regression</span></span>|<span data-ttu-id="b8816-126">04/07/2009 20:38:33</span><span class="sxs-lookup"><span data-stu-id="b8816-126">04/07/2009 20:38:33</span></span>|<span data-ttu-id="b8816-127">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000</span><span class="sxs-lookup"><span data-stu-id="b8816-127">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000</span></span>|  
  
###  <a name="sample-query-2-finding-additional-detail-about-the-model-by-using-dmx"></a><a name="bkmk_Query2"></a><span data-ttu-id="b8816-128">サンプルクエリ 2: DMX を使用してモデルに関する追加の詳細情報を検索する</span><span class="sxs-lookup"><span data-stu-id="b8816-128">Sample Query 2: Finding Additional Detail about the Model by Using DMX</span></span>  
 <span data-ttu-id="b8816-129">次のクエリは、ロジスティック回帰モデルに関する基本的な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="b8816-129">The following query returns some basic information about the logistic regression model.</span></span> <span data-ttu-id="b8816-130">ロジスティック回帰モデルは、入力として使用される値を表すマージナル統計ノード (NODE_TYPE = 24) がある点など、多くの点でニューラル ネットワーク モデルに似ています。</span><span class="sxs-lookup"><span data-stu-id="b8816-130">A logistic regression model is similar to a neural network model in many ways, including the presence of a marginal statistic node (NODE_TYPE = 24) that describes the values used as inputs.</span></span> <span data-ttu-id="b8816-131">このサンプル クエリでは、Targeted Mailing モデルを使用し、入れ子になったテーブル NODE_DISTRIBUTION から入力値を取得することにより、すべての入力値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b8816-131">This example query uses the Targeted Mailing model, and gets the values of all the inputs by retrieving them from the nested table, NODE_DISTRIBUTION.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM [TM_Logistic Regression].CONTENT   
```  
  
 <span data-ttu-id="b8816-132">結果の一部 :</span><span class="sxs-lookup"><span data-stu-id="b8816-132">Partial results:</span></span>  
  
|<span data-ttu-id="b8816-133">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="b8816-133">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="b8816-134">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="b8816-134">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="b8816-135">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="b8816-135">t.SUPPORT</span></span>|<span data-ttu-id="b8816-136">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b8816-136">t.PROBABILITY</span></span>|<span data-ttu-id="b8816-137">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="b8816-137">t.VARIANCE</span></span>|<span data-ttu-id="b8816-138">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="b8816-138">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="b8816-139">年齢</span><span class="sxs-lookup"><span data-stu-id="b8816-139">Age</span></span>|<span data-ttu-id="b8816-140">Missing</span><span class="sxs-lookup"><span data-stu-id="b8816-140">Missing</span></span>|<span data-ttu-id="b8816-141">0</span><span class="sxs-lookup"><span data-stu-id="b8816-141">0</span></span>|<span data-ttu-id="b8816-142">0</span><span class="sxs-lookup"><span data-stu-id="b8816-142">0</span></span>|<span data-ttu-id="b8816-143">0</span><span class="sxs-lookup"><span data-stu-id="b8816-143">0</span></span>|<span data-ttu-id="b8816-144">1</span><span class="sxs-lookup"><span data-stu-id="b8816-144">1</span></span>|  
|<span data-ttu-id="b8816-145">年齢</span><span class="sxs-lookup"><span data-stu-id="b8816-145">Age</span></span>|<span data-ttu-id="b8816-146">45.43491192</span><span class="sxs-lookup"><span data-stu-id="b8816-146">45.43491192</span></span>|<span data-ttu-id="b8816-147">17484</span><span class="sxs-lookup"><span data-stu-id="b8816-147">17484</span></span>|<span data-ttu-id="b8816-148">1</span><span class="sxs-lookup"><span data-stu-id="b8816-148">1</span></span>|<span data-ttu-id="b8816-149">126.9544114</span><span class="sxs-lookup"><span data-stu-id="b8816-149">126.9544114</span></span>|<span data-ttu-id="b8816-150">3</span><span class="sxs-lookup"><span data-stu-id="b8816-150">3</span></span>|  
|<span data-ttu-id="b8816-151">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="b8816-151">Bike Buyer</span></span>|<span data-ttu-id="b8816-152">Missing</span><span class="sxs-lookup"><span data-stu-id="b8816-152">Missing</span></span>|<span data-ttu-id="b8816-153">0</span><span class="sxs-lookup"><span data-stu-id="b8816-153">0</span></span>|<span data-ttu-id="b8816-154">0</span><span class="sxs-lookup"><span data-stu-id="b8816-154">0</span></span>|<span data-ttu-id="b8816-155">0</span><span class="sxs-lookup"><span data-stu-id="b8816-155">0</span></span>|<span data-ttu-id="b8816-156">1</span><span class="sxs-lookup"><span data-stu-id="b8816-156">1</span></span>|  
|<span data-ttu-id="b8816-157">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="b8816-157">Bike Buyer</span></span>|<span data-ttu-id="b8816-158">0</span><span class="sxs-lookup"><span data-stu-id="b8816-158">0</span></span>|<span data-ttu-id="b8816-159">8869</span><span class="sxs-lookup"><span data-stu-id="b8816-159">8869</span></span>|<span data-ttu-id="b8816-160">0.507263784</span><span class="sxs-lookup"><span data-stu-id="b8816-160">0.507263784</span></span>|<span data-ttu-id="b8816-161">0</span><span class="sxs-lookup"><span data-stu-id="b8816-161">0</span></span>|<span data-ttu-id="b8816-162">4</span><span class="sxs-lookup"><span data-stu-id="b8816-162">4</span></span>|  
|<span data-ttu-id="b8816-163">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="b8816-163">Bike Buyer</span></span>|<span data-ttu-id="b8816-164">1</span><span class="sxs-lookup"><span data-stu-id="b8816-164">1</span></span>|<span data-ttu-id="b8816-165">8615</span><span class="sxs-lookup"><span data-stu-id="b8816-165">8615</span></span>|<span data-ttu-id="b8816-166">0.492736216</span><span class="sxs-lookup"><span data-stu-id="b8816-166">0.492736216</span></span>|<span data-ttu-id="b8816-167">0</span><span class="sxs-lookup"><span data-stu-id="b8816-167">0</span></span>|<span data-ttu-id="b8816-168">4</span><span class="sxs-lookup"><span data-stu-id="b8816-168">4</span></span>|  
|<span data-ttu-id="b8816-169">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="b8816-169">Commute Distance</span></span>|<span data-ttu-id="b8816-170">Missing</span><span class="sxs-lookup"><span data-stu-id="b8816-170">Missing</span></span>|<span data-ttu-id="b8816-171">0</span><span class="sxs-lookup"><span data-stu-id="b8816-171">0</span></span>|<span data-ttu-id="b8816-172">0</span><span class="sxs-lookup"><span data-stu-id="b8816-172">0</span></span>|<span data-ttu-id="b8816-173">0</span><span class="sxs-lookup"><span data-stu-id="b8816-173">0</span></span>|<span data-ttu-id="b8816-174">1</span><span class="sxs-lookup"><span data-stu-id="b8816-174">1</span></span>|  
|<span data-ttu-id="b8816-175">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="b8816-175">Commute Distance</span></span>|<span data-ttu-id="b8816-176">5-10 Miles</span><span class="sxs-lookup"><span data-stu-id="b8816-176">5-10 Miles</span></span>|<span data-ttu-id="b8816-177">3033</span><span class="sxs-lookup"><span data-stu-id="b8816-177">3033</span></span>|<span data-ttu-id="b8816-178">0.173472889</span><span class="sxs-lookup"><span data-stu-id="b8816-178">0.173472889</span></span>|<span data-ttu-id="b8816-179">0</span><span class="sxs-lookup"><span data-stu-id="b8816-179">0</span></span>|<span data-ttu-id="b8816-180">4</span><span class="sxs-lookup"><span data-stu-id="b8816-180">4</span></span>|  
  
 <span data-ttu-id="b8816-181">実際のクエリではさらに多くの行が返されますが、このサンプルでは、入力に関して提供される情報の種類の例を示しています。</span><span class="sxs-lookup"><span data-stu-id="b8816-181">The actual query returns many more rows; however, this sample illustrates the type of information that is provided about the inputs.</span></span> <span data-ttu-id="b8816-182">不連続入力については、可能性のある各値を表に示しています。</span><span class="sxs-lookup"><span data-stu-id="b8816-182">For discrete inputs, each possible value is listed in the table.</span></span> <span data-ttu-id="b8816-183">Age などの連続値入力については、完全な一覧を示すことはできないので、入力を平均として分離しています。</span><span class="sxs-lookup"><span data-stu-id="b8816-183">For continuous-value inputs such as Age, a complete listing is impossible, so the input is discretized as a mean.</span></span> <span data-ttu-id="b8816-184">マージナル統計ノードでの情報の使用方法の詳細については、「 [ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-logistic-regression-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8816-184">For more information about how to use the information in the marginal statistics node, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8816-185">結果は見やすくするためにフラット化されていますが、プロバイダーが階層的な行セットをサポートしている場合は、1 つの列で入れ子になったテーブルを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="b8816-185">The results have been flattened for easier viewing, but you can return the nested table in a single column if your provider supports hierarchical rowsets.</span></span>  
  
## <a name="prediction-queries-on-a-logistic-regression-model"></a><span data-ttu-id="b8816-186">ロジスティック回帰モデルに対する予測クエリ</span><span class="sxs-lookup"><span data-stu-id="b8816-186">Prediction Queries on a Logistic Regression Model</span></span>  
 <span data-ttu-id="b8816-187">すべての種類のマイニング モデルで [Predict (DMX)](/sql/dmx/predict-dmx) 関数を使用して、モデルに新しいデータを提供し、新しい値に基づいて予測を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b8816-187">You can use the [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) function with every kind of mining model to provide new data to the model and make predictions based on the new values.</span></span> <span data-ttu-id="b8816-188">また、予測が正しい確率など、予測に関する追加情報を返す関数も使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8816-188">You can also use functions to return additional information about the prediction, such as the probability that a prediction is correct.</span></span> <span data-ttu-id="b8816-189">ここでは、ロジスティック回帰モデルでの予測クエリの例をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="b8816-189">This section provides some examples of prediction queries on a logistic regression model.</span></span>  
  
###  <a name="sample-query-3-making-predictions-for-a-continuous-value"></a><a name="bkmk_Query3"></a><span data-ttu-id="b8816-190">サンプルクエリ 3: 連続値の予測を作成する</span><span class="sxs-lookup"><span data-stu-id="b8816-190">Sample Query 3: Making Predictions for a Continuous Value</span></span>  
 <span data-ttu-id="b8816-191">ロジスティック回帰は入力と予測の両方について連続属性の使用をサポートしているため、データ内のさまざまな要素を相互に関連付けるモデルを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="b8816-191">Because logistic regression supports the use of continuous attributes for both input and prediction, it is easy to create models that correlate various factors in your data.</span></span> <span data-ttu-id="b8816-192">予測クエリを使用して、これらの要素間のリレーションシップを調査できます。</span><span class="sxs-lookup"><span data-stu-id="b8816-192">You can use prediction queries to explore the relationship among these factors.</span></span>  
  
 <span data-ttu-id="b8816-193">次のサンプル クエリは、中級者向けチュートリアルの Call Center モデルに基づいており、金曜日の午前のシフトについてのサービス グレードを予測する単一クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8816-193">The following query sample is based on the Call Center model, from the Intermediate Tutorial, and creates a singleton query that predicts service grade for the Friday AM shift.</span></span> <span data-ttu-id="b8816-194">[PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) 関数は入れ子になったテーブルを返します。このテーブルには、予測される値の有効性の理解に関連する統計が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8816-194">The [PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) function returns a nested table that provides statistics relevant to understanding the validity of the predicted value.</span></span>  
  
```  
SELECT  
  Predict([Call Center_LR].[Service Grade]) as Predicted ServiceGrade,  
  PredictHistogram([Call Center_LR].[Service Grade]) as [Results],  
FROM  
  [Call Center_LR]  
NATURAL PREDICTION JOIN  
(SELECT 'Friday' AS [Day Of Week],  
  'AM' AS [Shift]) AS t  
```  
  
 <span data-ttu-id="b8816-195">サンプルの結果 :</span><span class="sxs-lookup"><span data-stu-id="b8816-195">Sample results:</span></span>  
  
 <span data-ttu-id="b8816-196">**予測されるサービスグレード**: 0.102601830123659</span><span class="sxs-lookup"><span data-stu-id="b8816-196">**Predicted Service Grade**: 0.102601830123659</span></span>  
  
 <span data-ttu-id="b8816-197">**結果**</span><span class="sxs-lookup"><span data-stu-id="b8816-197">**Results**</span></span>  
  
|<span data-ttu-id="b8816-198">Service Grade</span><span class="sxs-lookup"><span data-stu-id="b8816-198">Service Grade</span></span>|<span data-ttu-id="b8816-199">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="b8816-199">$SUPPORT</span></span>|<span data-ttu-id="b8816-200">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b8816-200">$PROBABILITY</span></span>|<span data-ttu-id="b8816-201">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b8816-201">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="b8816-202">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="b8816-202">$VARIANCE</span></span>|<span data-ttu-id="b8816-203">$STDEV</span><span class="sxs-lookup"><span data-stu-id="b8816-203">$STDEV</span></span>|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="b8816-204">0.102601830123659</span><span class="sxs-lookup"><span data-stu-id="b8816-204">0.102601830123659</span></span>|<span data-ttu-id="b8816-205">83.0232558139535</span><span class="sxs-lookup"><span data-stu-id="b8816-205">83.0232558139535</span></span>|<span data-ttu-id="b8816-206">0.988372093023256</span><span class="sxs-lookup"><span data-stu-id="b8816-206">0.988372093023256</span></span>|<span data-ttu-id="b8816-207">0</span><span class="sxs-lookup"><span data-stu-id="b8816-207">0</span></span>|<span data-ttu-id="b8816-208">0.00120552660600087</span><span class="sxs-lookup"><span data-stu-id="b8816-208">0.00120552660600087</span></span>|<span data-ttu-id="b8816-209">0.034720694203902</span><span class="sxs-lookup"><span data-stu-id="b8816-209">0.034720694203902</span></span>|  
||<span data-ttu-id="b8816-210">0.976744186046512</span><span class="sxs-lookup"><span data-stu-id="b8816-210">0.976744186046512</span></span>|<span data-ttu-id="b8816-211">0.0116279069767442</span><span class="sxs-lookup"><span data-stu-id="b8816-211">0.0116279069767442</span></span>|<span data-ttu-id="b8816-212">0.0116279069767442</span><span class="sxs-lookup"><span data-stu-id="b8816-212">0.0116279069767442</span></span>|<span data-ttu-id="b8816-213">0</span><span class="sxs-lookup"><span data-stu-id="b8816-213">0</span></span>|<span data-ttu-id="b8816-214">0</span><span class="sxs-lookup"><span data-stu-id="b8816-214">0</span></span>|  
  
 <span data-ttu-id="b8816-215">入れ子になった NODE_DISTRIBUTION テーブルの確率、サポート、および標準偏差値の詳細については、「 [ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-logistic-regression-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8816-215">For more information about the probability, support, and standard deviation values in the nested NODE_DISTRIBUTION table, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
###  <a name="sample-query-4-making-predictions-for-a-discrete-value"></a><a name="bkmk_Query4"></a><span data-ttu-id="b8816-216">サンプルクエリ 4: 不連続値の予測を作成する</span><span class="sxs-lookup"><span data-stu-id="b8816-216">Sample Query 4: Making Predictions for a Discrete Value</span></span>  
 <span data-ttu-id="b8816-217">ロジスティック回帰は、バイナリ結果を構成する要素を分析するシナリオでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8816-217">Logistic regression is typically used in scenarios where you want to analyze the factors that contribute to a binary outcome.</span></span> <span data-ttu-id="b8816-218">チュートリアルで使用されているモデルは連続値 **ServiceGrade**を予測しますが、現実のシナリオでは、サービス グレードがいくつかの分離した目標値を満たすかどうかを予測するモデルを設定することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="b8816-218">Although the model used in the tutorial predicts a continuous value, **ServiceGrade**, in a real-life scenario you might want to set up the model to predict whether service grade met some discretized target value.</span></span> <span data-ttu-id="b8816-219">または、連続値を使用して予測を出力し、後で予測された出力を **Good**、 **Fair**、または **Poor**にグループ化することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8816-219">Alternatively, you could output the predictions using a continuous value but later group the predicted outcomes into **Good**, **Fair**, or **Poor**.</span></span>  
  
 <span data-ttu-id="b8816-220">次のサンプルは、予測可能な属性をグループ化する方法をどのように変更するかを示しています。</span><span class="sxs-lookup"><span data-stu-id="b8816-220">The following sample illustrates how to change the way that the predictable attribute is grouped.</span></span> <span data-ttu-id="b8816-221">これを行うには、マイニング構造のコピーを作成し、目的の列の分離方法を変更して、値が連続的ではなく、グループ化されるようにします。</span><span class="sxs-lookup"><span data-stu-id="b8816-221">To do this, you create a copy of the mining structure and then change the discretization method of the target column so that the values are grouped rather than continuous.</span></span>  
  
 <span data-ttu-id="b8816-222">次の手順は、Call Center データの Service Grade 値のグループ化を変更する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b8816-222">The following procedure describes how to change the grouping of Service Grade values in the Call Center data.</span></span>  
  
##### <a name="to-create-a-discretized-version-of-the-call-center-mining-structure-and-models"></a><span data-ttu-id="b8816-223">Call Center のマイニング構造およびモデルの分離バージョンを作成するには</span><span class="sxs-lookup"><span data-stu-id="b8816-223">To create a discretized version of the Call Center mining structure and models</span></span>  
  
1.  <span data-ttu-id="b8816-224">の [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ソリューションエクスプローラーで、[**マイニング構造**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="b8816-224">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, expand **Mining Structures**.</span></span>  
  
2.  <span data-ttu-id="b8816-225">Call Center.dmm を右クリックして、 **[コピー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b8816-225">Right-click Call Center.dmm and select **Copy**.</span></span>  
  
3.  <span data-ttu-id="b8816-226">**[マイニング構造]** を右クリックし、 **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8816-226">Right click **Mining Structures** and select **Paste**.</span></span> <span data-ttu-id="b8816-227">Call Center 1 という名前の新しいマイニング構造が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b8816-227">A new mining structure iss added, named Call Center 1.</span></span>  
  
4.  <span data-ttu-id="b8816-228">新しいマイニング構造を右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8816-228">Right-click the new mining structure and select **Rename**.</span></span> <span data-ttu-id="b8816-229">新しい名前として「 **Call Center Discretized**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b8816-229">Type the new name, **Call Center Discretized**.</span></span>  
  
5.  <span data-ttu-id="b8816-230">新しいマイニング構造をダブルクリックしてデザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="b8816-230">Double-click the new mining structure to open it in the designer.</span></span> <span data-ttu-id="b8816-231">すべてのマイニング モデルがコピーされ、拡張子 1 が付いていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="b8816-231">Notice that the mining models have all been copied as well, and all have the extension 1.</span></span> <span data-ttu-id="b8816-232">ここでは、名前をそのままにします。</span><span class="sxs-lookup"><span data-stu-id="b8816-232">Leave the names as is for now.</span></span>  
  
6.  <span data-ttu-id="b8816-233">**[マイニング構造]** タブで、Service Grade の列を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8816-233">In the **Mining Structure** tab, right-click the column for Service Grade, and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="b8816-234">プロパティを `Content` **Continuous**から**分離**に変更します。</span><span class="sxs-lookup"><span data-stu-id="b8816-234">Change the `Content` property from **Continuous** to **Discretized**.</span></span> <span data-ttu-id="b8816-235">プロパティを `DiscretizationMethod` **クラスター**に変更します。</span><span class="sxs-lookup"><span data-stu-id="b8816-235">Change the `DiscretizationMethod` property to **Clusters**.</span></span> <span data-ttu-id="b8816-236">Discretization BucketCount に「 **3**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b8816-236">For Discretization BucketCount, type **3**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b8816-237">これらのパラメーターは、プロセスを説明するために使用されており、有効なモデルを生成するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b8816-237">These parameters are just used for illustrating the process, and do not necessarily produce a valid model,</span></span>  
  
8.  <span data-ttu-id="b8816-238">**[マイニング モデル]** メニューの **[構造および全モデルの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8816-238">From the **Mining Model** menu, select **Process structure and all models**.</span></span>  
  
 <span data-ttu-id="b8816-239">次のサンプル クエリは、この分離モデルに基づいており、指定した曜日のサービス グレードと、各予測出力の確率を予測します。</span><span class="sxs-lookup"><span data-stu-id="b8816-239">The following sample query is based on this discretized model, and predicts the service grade for the specified day of the week, together with the probabilities for each predicted outcome.</span></span>  
  
```  
SELECT  
  (PredictHistogram([Call Center_LR 1].[Service Grade])) as [Predictions]  
FROM  
  [Call Center_LR 1]  
NATURAL PREDICTION JOIN  
(SELECT 'Saturday' AS [Day Of Week]) AS t    
```  
  
 <span data-ttu-id="b8816-240">期待される結果:</span><span class="sxs-lookup"><span data-stu-id="b8816-240">Expected results:</span></span>  
  
 <span data-ttu-id="b8816-241">**予測**</span><span class="sxs-lookup"><span data-stu-id="b8816-241">**Predictions**</span></span>  
  
|<span data-ttu-id="b8816-242">Service Grade</span><span class="sxs-lookup"><span data-stu-id="b8816-242">Service Grade</span></span>|<span data-ttu-id="b8816-243">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="b8816-243">$SUPPORT</span></span>|<span data-ttu-id="b8816-244">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b8816-244">$PROBABILITY</span></span>|<span data-ttu-id="b8816-245">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b8816-245">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="b8816-246">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="b8816-246">$VARIANCE</span></span>|<span data-ttu-id="b8816-247">$STDEV</span><span class="sxs-lookup"><span data-stu-id="b8816-247">$STDEV</span></span>|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="b8816-248">0.10872718383125</span><span class="sxs-lookup"><span data-stu-id="b8816-248">0.10872718383125</span></span>|<span data-ttu-id="b8816-249">35.7246504770641</span><span class="sxs-lookup"><span data-stu-id="b8816-249">35.7246504770641</span></span>|<span data-ttu-id="b8816-250">0.425293458060287</span><span class="sxs-lookup"><span data-stu-id="b8816-250">0.425293458060287</span></span>|<span data-ttu-id="b8816-251">0.0170168360030293</span><span class="sxs-lookup"><span data-stu-id="b8816-251">0.0170168360030293</span></span>|<span data-ttu-id="b8816-252">0</span><span class="sxs-lookup"><span data-stu-id="b8816-252">0</span></span>|<span data-ttu-id="b8816-253">0</span><span class="sxs-lookup"><span data-stu-id="b8816-253">0</span></span>|  
|<span data-ttu-id="b8816-254">0.05855769230625</span><span class="sxs-lookup"><span data-stu-id="b8816-254">0.05855769230625</span></span>|<span data-ttu-id="b8816-255">31.7098880800703</span><span class="sxs-lookup"><span data-stu-id="b8816-255">31.7098880800703</span></span>|<span data-ttu-id="b8816-256">0.377498667619885</span><span class="sxs-lookup"><span data-stu-id="b8816-256">0.377498667619885</span></span>|<span data-ttu-id="b8816-257">0.020882020060454</span><span class="sxs-lookup"><span data-stu-id="b8816-257">0.020882020060454</span></span>|<span data-ttu-id="b8816-258">0</span><span class="sxs-lookup"><span data-stu-id="b8816-258">0</span></span>|<span data-ttu-id="b8816-259">0</span><span class="sxs-lookup"><span data-stu-id="b8816-259">0</span></span>|  
|<span data-ttu-id="b8816-260">0.170169491525</span><span class="sxs-lookup"><span data-stu-id="b8816-260">0.170169491525</span></span>|<span data-ttu-id="b8816-261">15.6109159883202</span><span class="sxs-lookup"><span data-stu-id="b8816-261">15.6109159883202</span></span>|<span data-ttu-id="b8816-262">0.185844237956192</span><span class="sxs-lookup"><span data-stu-id="b8816-262">0.185844237956192</span></span>|<span data-ttu-id="b8816-263">0.0661386571386049</span><span class="sxs-lookup"><span data-stu-id="b8816-263">0.0661386571386049</span></span>|<span data-ttu-id="b8816-264">0</span><span class="sxs-lookup"><span data-stu-id="b8816-264">0</span></span>|<span data-ttu-id="b8816-265">0</span><span class="sxs-lookup"><span data-stu-id="b8816-265">0</span></span>|  
||<span data-ttu-id="b8816-266">0.954545454545455</span><span class="sxs-lookup"><span data-stu-id="b8816-266">0.954545454545455</span></span>|<span data-ttu-id="b8816-267">0.0113636363636364</span><span class="sxs-lookup"><span data-stu-id="b8816-267">0.0113636363636364</span></span>|<span data-ttu-id="b8816-268">0.0113636363636364</span><span class="sxs-lookup"><span data-stu-id="b8816-268">0.0113636363636364</span></span>|<span data-ttu-id="b8816-269">0</span><span class="sxs-lookup"><span data-stu-id="b8816-269">0</span></span>|<span data-ttu-id="b8816-270">0</span><span class="sxs-lookup"><span data-stu-id="b8816-270">0</span></span>|  
  
 <span data-ttu-id="b8816-271">予測結果は、指定どおりに 3 つのカテゴリにグループ化されています。ただし、このグループ化は、データの実際の値のクラスタリングに基づくものであり、ビジネスの目標として設定できる任意の値に基づくものではありません。</span><span class="sxs-lookup"><span data-stu-id="b8816-271">Note that the predicted outcomes have been grouped into three categories as specified; however, these groupings are based on the clustering of actual values in the data, not arbitrary values that you might set as business goals.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="b8816-272">予測関数の一覧</span><span class="sxs-lookup"><span data-stu-id="b8816-272">List of Prediction Functions</span></span>  
 <span data-ttu-id="b8816-273">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b8816-273">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="b8816-274">これに加え、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ロジスティック回帰アルゴリズムでは、次の表に示す関数もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b8816-274">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8816-275">予測関数</span><span class="sxs-lookup"><span data-stu-id="b8816-275">Prediction Function</span></span>|<span data-ttu-id="b8816-276">使用法</span><span class="sxs-lookup"><span data-stu-id="b8816-276">Usage</span></span>|  
|[<span data-ttu-id="b8816-277">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="b8816-277">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="b8816-278">あるノードがモデル内の別のノードの子であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8816-278">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="b8816-279">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="b8816-279">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="b8816-280">指定された状態の調整済みの確率を返します。</span><span class="sxs-lookup"><span data-stu-id="b8816-280">Returns the adjusted probability of a specified state.</span></span>|  
|[<span data-ttu-id="b8816-281">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="b8816-281">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="b8816-282">指定された列に対して、予測された値、または値のセットを返します。</span><span class="sxs-lookup"><span data-stu-id="b8816-282">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="b8816-283">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="b8816-283">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="b8816-284">指定された状態の確率を返します。</span><span class="sxs-lookup"><span data-stu-id="b8816-284">Returns the probability for a specified state.</span></span>|  
|[<span data-ttu-id="b8816-285">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="b8816-285">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="b8816-286">予測された値の標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="b8816-286">Returns standard deviation for the predicted value.</span></span>|  
|[<span data-ttu-id="b8816-287">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="b8816-287">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="b8816-288">指定された状態に対するサポート値を返します。</span><span class="sxs-lookup"><span data-stu-id="b8816-288">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="b8816-289">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="b8816-289">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="b8816-290">指定された列の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="b8816-290">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="b8816-291">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムに共通の関数の一覧については、「[一般的な予測関数 (DMX)](/sql/dmx/general-prediction-functions-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8816-291">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="b8816-292">特定の関数の構文については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8816-292">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8816-293">ニューラル ネットワーク モデルとロジスティック回帰モデルの場合、 [PredictSupport (DMX)](/sql/dmx/predictsupport-dmx) 関数はモデル全体のトレーニング セットのサイズを表す 1 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="b8816-293">For neural network and logistic regression models, the [PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx) function returns a single value that represents the size of the training set for the entire model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8816-294">参照</span><span class="sxs-lookup"><span data-stu-id="b8816-294">See Also</span></span>  
 <span data-ttu-id="b8816-295">[データマイニングクエリ](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="b8816-295">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="b8816-296">[Microsoft ロジスティック回帰アルゴリズム](microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="b8816-296">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="b8816-297">[Microsoft ロジスティック回帰アルゴリズムテクニカルリファレンス](microsoft-logistic-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b8816-297">[Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="b8816-298">[ロジスティック回帰モデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](mining-model-content-for-logistic-regression-models.md) </span><span class="sxs-lookup"><span data-stu-id="b8816-298">[Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) </span></span>  
 [<span data-ttu-id="b8816-299">レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="b8816-299">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
