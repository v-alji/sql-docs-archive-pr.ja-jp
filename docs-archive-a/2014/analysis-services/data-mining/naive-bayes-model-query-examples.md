---
title: Naive Bayes モデルのクエリ例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- naive bayes model [Analysis Services]
- naive bayes algorithms [Analysis Services]
- content queries [DMX]
ms.assetid: e642bd7d-5afa-4dfb-8cca-4f84aadf61b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9694826bf2f74daef7b6d024e51e31d4ee448671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712638"
---
# <a name="naive-bayes-model-query-examples"></a><span data-ttu-id="c817d-102">Naive Bayes モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="c817d-102">Naive Bayes Model Query Examples</span></span>
  <span data-ttu-id="c817d-103">データ マイニング モデルに対するクエリを作成する際には、コンテンツ クエリを作成することも、予測クエリを作成することもできます。コンテンツ クエリでは、分析で検出されたパターンの詳細情報を取得できます。予測クエリでは、モデル内のパターンを使用して新しいデータについての予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c817d-103">When you create a query against a data mining model, you can create either a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="c817d-104">データ マイニング スキーマ行セットに対するクエリによって、モデルに関するメタデータを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c817d-104">You can also retrieve metadata about the model by using a query against the data mining schema rowset.</span></span> <span data-ttu-id="c817d-105">ここでは、Microsoft Naive Bayes アルゴリズムに基づくモデルに対するクエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c817d-105">This section explains how to create these queries for models that are based on the Microsoft Naive Bayes algorithm.</span></span>  
  
 <span data-ttu-id="c817d-106">**コンテンツ クエリ**</span><span class="sxs-lookup"><span data-stu-id="c817d-106">**Content Queries**</span></span>  
  
 [<span data-ttu-id="c817d-107">DMX を使用したモデルメタデータの取得</span><span class="sxs-lookup"><span data-stu-id="c817d-107">Getting model metadata by using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="c817d-108">トレーニング データの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="c817d-108">Retrieving a summary of training data</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="c817d-109">属性に関する詳細情報を検索する</span><span class="sxs-lookup"><span data-stu-id="c817d-109">Finding more information about attributes</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="c817d-110">システムストアドプロシージャの使用</span><span class="sxs-lookup"><span data-stu-id="c817d-110">Using system stored procedures</span></span>](#bkmk_Query4)  
  
 <span data-ttu-id="c817d-111">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="c817d-111">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="c817d-112">単一クエリを使用して結果を予測する</span><span class="sxs-lookup"><span data-stu-id="c817d-112">Predicting outcomes using a singleton query</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="c817d-113">確率およびサポート値付きの予測を取得する</span><span class="sxs-lookup"><span data-stu-id="c817d-113">Getting predictions with probability and support values</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="c817d-114">アソシエーションの予測</span><span class="sxs-lookup"><span data-stu-id="c817d-114">Predicting associations</span></span>](#bkmk_Query7)  
  
## <a name="finding-information-about-a-naive-bayes-model"></a><span data-ttu-id="c817d-115">Naive Bayes モデルに関する情報の入手</span><span class="sxs-lookup"><span data-stu-id="c817d-115">Finding Information about a Naive Bayes Model</span></span>  
 <span data-ttu-id="c817d-116">Naive Bayes モデルのモデル コンテンツは、トレーニング データの値の分布に関する集計情報です。</span><span class="sxs-lookup"><span data-stu-id="c817d-116">The model content of a Naive Bayes model provides aggregated information about the distribution of values in the training data.</span></span> <span data-ttu-id="c817d-117">データ マイニング スキーマ行セットに対するクエリを作成することによって、モデルのメタデータに関する情報を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c817d-117">You can also retrieve information about the metadata of the model by creating queries against the data mining schema rowsets.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="c817d-118">サンプル クエリ 1: DMX を使用してモデル メタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="c817d-118">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="c817d-119">データ マイニング スキーマ行セットに対してクエリを実行すると、モデルにのメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="c817d-119">By querying the data mining schema rowset, you can find metadata for the model.</span></span> <span data-ttu-id="c817d-120">このメタデータには、モデルが作成された日時、モデルが最後に処理された日時、モデルの基になるマイニング構造の名前、予測可能な属性として使用されている列の名前などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c817d-120">This might include when the model was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the columns used as the predictable attribute.</span></span> <span data-ttu-id="c817d-121">モデルが作成されたときに使用されたパラメーターを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c817d-121">You can also return the parameters that were used when the model was created.</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, DATE_CREATED, LAST_PROCESSED,  
SERVICE_NAME, PREDICTION_ENTITY, FILTER  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_NaiveBayes_Filtered'  
```  
  
 <span data-ttu-id="c817d-122">サンプルの結果 :</span><span class="sxs-lookup"><span data-stu-id="c817d-122">Sample results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c817d-123">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c817d-123">MODEL_CATALOG</span></span>|<span data-ttu-id="c817d-124">AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="c817d-124">AdventureWorks</span></span>|  
|<span data-ttu-id="c817d-125">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="c817d-125">MODEL_NAME</span></span>|<span data-ttu-id="c817d-126">TM_NaiveBayes_Filtered</span><span class="sxs-lookup"><span data-stu-id="c817d-126">TM_NaiveBayes_Filtered</span></span>|  
|<span data-ttu-id="c817d-127">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c817d-127">DATE_CREATED</span></span>|<span data-ttu-id="c817d-128">3/1/2008 19:15</span><span class="sxs-lookup"><span data-stu-id="c817d-128">3/1/2008 19:15</span></span>|  
|<span data-ttu-id="c817d-129">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="c817d-129">LAST_PROCESSED</span></span>|<span data-ttu-id="c817d-130">3/2/2008 20:00</span><span class="sxs-lookup"><span data-stu-id="c817d-130">3/2/2008 20:00</span></span>|  
|<span data-ttu-id="c817d-131">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="c817d-131">SERVICE_NAME</span></span>|<span data-ttu-id="c817d-132">Microsoft_Naive_Bayes</span><span class="sxs-lookup"><span data-stu-id="c817d-132">Microsoft_Naive_Bayes</span></span>|  
|<span data-ttu-id="c817d-133">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="c817d-133">PREDICTION_ENTITY</span></span>|<span data-ttu-id="c817d-134">Bike Buyer,Yearly Income</span><span class="sxs-lookup"><span data-stu-id="c817d-134">Bike Buyer,Yearly Income</span></span>|  
|<span data-ttu-id="c817d-135">FILTER</span><span class="sxs-lookup"><span data-stu-id="c817d-135">FILTER</span></span>|<span data-ttu-id="c817d-136">[Region] = 'Europe' OR [Region] = 'North America'</span><span class="sxs-lookup"><span data-stu-id="c817d-136">[Region] = 'Europe' OR [Region] = 'North America'</span></span>|  
  
 <span data-ttu-id="c817d-137">この例で使用するモデルは、「 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)」で作成した Naive Bayes モデルを基にしていますが、予測可能な属性をもう 1 つ追加し、トレーニング データにフィルターを適用するという修正を加えています。</span><span class="sxs-lookup"><span data-stu-id="c817d-137">The model used for this example is based on the Naive Bayes model you create in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md), but was modified by adding a second predictable attribute and applying a filter to the training data.</span></span>  
  
###  <a name="sample-query-2-retrieving-a-summary-of-training-data"></a><a name="bkmk_Query2"></a> <span data-ttu-id="c817d-138">サンプル クエリ 2: トレーニング データの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="c817d-138">Sample Query 2: Retrieving a Summary of Training Data</span></span>  
 <span data-ttu-id="c817d-139">Naive Bayes モデルでは、マージナル統計ノードにトレーニング データの値の分布に関する集計情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="c817d-139">In a Naive Bayes model, the marginal statistics node stores aggregated information about the distribution of values in the training data.</span></span> <span data-ttu-id="c817d-140">この一覧はトレーニング データに対する SQL クエリと同じ情報が得られるので、SQL クエリを作成しなくて済むため便利です。</span><span class="sxs-lookup"><span data-stu-id="c817d-140">This summary is convenient and saves you from having to create SQL queries against the training data to find the same information.</span></span>  
  
 <span data-ttu-id="c817d-141">次の例は、DMX コンテンツ クエリを使用してノード (NODE_TYPE = 24) からデータを取得しています。</span><span class="sxs-lookup"><span data-stu-id="c817d-141">The following example uses a DMX content query to retrieve the data from the node (NODE_TYPE = 24).</span></span> <span data-ttu-id="c817d-142">統計は入れ子になったテーブルに格納されており、結果を見やすくするために FLATTENED キーワードが使用されています。</span><span class="sxs-lookup"><span data-stu-id="c817d-142">Because the statistics are stored in a nested table, the FLATTENED keyword is used to make the results easier to view.</span></span>  
  
```  
SELECT FLATTENED MODEL_NAME,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE FROM NODE_DISTRIBUTION) AS t  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 26  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c817d-143">SUPPORT および PROBABILITY という列名は、多次元式 (MDX) の同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c817d-143">You must enclose the name of the columns, SUPPORT and PROBABILITY, in brackets to distinguish them from the Multidimensional Expressions (MDX) reserved keywords of the same names.</span></span>  
  
 <span data-ttu-id="c817d-144">結果の一部 :</span><span class="sxs-lookup"><span data-stu-id="c817d-144">Partial results:</span></span>  
  
|<span data-ttu-id="c817d-145">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="c817d-145">MODEL_NAME</span></span>|<span data-ttu-id="c817d-146">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="c817d-146">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="c817d-147">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="c817d-147">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="c817d-148">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="c817d-148">t.SUPPORT</span></span>|<span data-ttu-id="c817d-149">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="c817d-149">t.PROBABILITY</span></span>|<span data-ttu-id="c817d-150">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="c817d-150">t.VALUETYPE</span></span>|  
|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="c817d-151">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="c817d-151">TM_NaiveBayes</span></span>|<span data-ttu-id="c817d-152">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="c817d-152">Bike Buyer</span></span>|<span data-ttu-id="c817d-153">Missing</span><span class="sxs-lookup"><span data-stu-id="c817d-153">Missing</span></span>|<span data-ttu-id="c817d-154">0</span><span class="sxs-lookup"><span data-stu-id="c817d-154">0</span></span>|<span data-ttu-id="c817d-155">0</span><span class="sxs-lookup"><span data-stu-id="c817d-155">0</span></span>|<span data-ttu-id="c817d-156">1</span><span class="sxs-lookup"><span data-stu-id="c817d-156">1</span></span>|  
|<span data-ttu-id="c817d-157">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="c817d-157">TM_NaiveBayes</span></span>|<span data-ttu-id="c817d-158">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="c817d-158">Bike Buyer</span></span>|<span data-ttu-id="c817d-159">0</span><span class="sxs-lookup"><span data-stu-id="c817d-159">0</span></span>|<span data-ttu-id="c817d-160">8869</span><span class="sxs-lookup"><span data-stu-id="c817d-160">8869</span></span>|<span data-ttu-id="c817d-161">0.507263784</span><span class="sxs-lookup"><span data-stu-id="c817d-161">0.507263784</span></span>|<span data-ttu-id="c817d-162">4</span><span class="sxs-lookup"><span data-stu-id="c817d-162">4</span></span>|  
|<span data-ttu-id="c817d-163">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="c817d-163">TM_NaiveBayes</span></span>|<span data-ttu-id="c817d-164">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="c817d-164">Bike Buyer</span></span>|<span data-ttu-id="c817d-165">1</span><span class="sxs-lookup"><span data-stu-id="c817d-165">1</span></span>|<span data-ttu-id="c817d-166">8615</span><span class="sxs-lookup"><span data-stu-id="c817d-166">8615</span></span>|<span data-ttu-id="c817d-167">0.492736216</span><span class="sxs-lookup"><span data-stu-id="c817d-167">0.492736216</span></span>|<span data-ttu-id="c817d-168">4</span><span class="sxs-lookup"><span data-stu-id="c817d-168">4</span></span>|  
|<span data-ttu-id="c817d-169">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="c817d-169">TM_NaiveBayes</span></span>|<span data-ttu-id="c817d-170">性別</span><span class="sxs-lookup"><span data-stu-id="c817d-170">Gender</span></span>|<span data-ttu-id="c817d-171">Missing</span><span class="sxs-lookup"><span data-stu-id="c817d-171">Missing</span></span>|<span data-ttu-id="c817d-172">0</span><span class="sxs-lookup"><span data-stu-id="c817d-172">0</span></span>|<span data-ttu-id="c817d-173">0</span><span class="sxs-lookup"><span data-stu-id="c817d-173">0</span></span>|<span data-ttu-id="c817d-174">1</span><span class="sxs-lookup"><span data-stu-id="c817d-174">1</span></span>|  
|<span data-ttu-id="c817d-175">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="c817d-175">TM_NaiveBayes</span></span>|<span data-ttu-id="c817d-176">性別</span><span class="sxs-lookup"><span data-stu-id="c817d-176">Gender</span></span>|<span data-ttu-id="c817d-177">F</span><span class="sxs-lookup"><span data-stu-id="c817d-177">F</span></span>|<span data-ttu-id="c817d-178">8656</span><span class="sxs-lookup"><span data-stu-id="c817d-178">8656</span></span>|<span data-ttu-id="c817d-179">0.495081217</span><span class="sxs-lookup"><span data-stu-id="c817d-179">0.495081217</span></span>|<span data-ttu-id="c817d-180">4</span><span class="sxs-lookup"><span data-stu-id="c817d-180">4</span></span>|  
|<span data-ttu-id="c817d-181">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="c817d-181">TM_NaiveBayes</span></span>|<span data-ttu-id="c817d-182">性別</span><span class="sxs-lookup"><span data-stu-id="c817d-182">Gender</span></span>|<span data-ttu-id="c817d-183">M</span><span class="sxs-lookup"><span data-stu-id="c817d-183">M</span></span>|<span data-ttu-id="c817d-184">8828</span><span class="sxs-lookup"><span data-stu-id="c817d-184">8828</span></span>|<span data-ttu-id="c817d-185">0.504918783</span><span class="sxs-lookup"><span data-stu-id="c817d-185">0.504918783</span></span>|<span data-ttu-id="c817d-186">4</span><span class="sxs-lookup"><span data-stu-id="c817d-186">4</span></span>|  
  
 <span data-ttu-id="c817d-187">たとえば、これらの結果は各不連続値に対するトレーニング ケースの数 (VALUETYPE = 4) と計算された確率、不足値の調整 (VALUETYPE = 1) を示しています。</span><span class="sxs-lookup"><span data-stu-id="c817d-187">For example, these results tell you the number of training cases for each discrete value (VALUETYPE = 4), together with the computed probability, adjusted for missing values (VALUETYPE = 1).</span></span>  
  
 <span data-ttu-id="c817d-188">Naive Bayes モデルの NODE_DISTRIBUTION テーブルに指定される値の定義については、「 [Naive Bayes モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c817d-188">For a definition of the values provided in the NODE_DISTRIBUTION table in a Naive Bayes model, see [Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md).</span></span> <span data-ttu-id="c817d-189">サポートと確率の計算がどのように不足値の影響を受けるかについては、「[不足値 &#40;Analysis Services - データ マイニング&#41;](missing-values-analysis-services-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c817d-189">For more information about how support and probability calculations are affected by missing values, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-3-finding-more-information-about-attributes"></a><a name="bkmk_Query3"></a> <span data-ttu-id="c817d-190">サンプル クエリ 3: 属性に関する詳細情報を検索する</span><span class="sxs-lookup"><span data-stu-id="c817d-190">Sample Query 3: Finding More Information about Attributes</span></span>  
 <span data-ttu-id="c817d-191">Naive Bayes モデルには、多くの場合さまざまな属性間のリレーションシップに関する複雑な情報が含まれていますが、このリレーションシップを最も簡単に表示するには、 [Microsoft Naive Bayes ビューアー](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c817d-191">Because a Naive Bayes model often contains complex information about the relationships among different attributes, the easiest way to view these relationships is to use the [Microsoft Naive Bayes Viewer](browse-a-model-using-the-microsoft-naive-bayes-viewer.md).</span></span> <span data-ttu-id="c817d-192">また、データを返す DMX クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c817d-192">However, you can create DMX queries to return the data.</span></span>  
  
 <span data-ttu-id="c817d-193">次の例は、モデルから特定の属性 `Region`に関する情報を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c817d-193">The following example shows how to return information from the model about a particular attribute, `Region`.</span></span>  
  
```  
SELECT NODE_TYPE, NODE_CAPTION,   
NODE_PROBABILITY, NODE_SUPPORT, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE ATTRIBUTE_NAME = 'Region'  
```  
  
 <span data-ttu-id="c817d-194">このクエリは、入力属性を表すノード (NODE_TYPE = 10) と属性のそれぞれの値に対応するノード (NODE_TYPE = 11) の 2 種類のノードを返します。</span><span class="sxs-lookup"><span data-stu-id="c817d-194">This query returns two types of nodes: the node that represents the input attribute (NODE_TYPE = 10), and nodes for each value of the attribute (NODE_TYPE = 11).</span></span> <span data-ttu-id="c817d-195">ノードのキャプションは属性の名前と値の両方を示すため、ノード名の代わりに、ノードを識別するために使用します。</span><span class="sxs-lookup"><span data-stu-id="c817d-195">The node caption is used to identify the node, rather than the node name, because the caption shows both the attribute name and attribute value.</span></span>  
  
|<span data-ttu-id="c817d-196">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c817d-196">NODE_TYPE</span></span>|<span data-ttu-id="c817d-197">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="c817d-197">NODE_CAPTION</span></span>|<span data-ttu-id="c817d-198">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="c817d-198">NODE_PROBABILITY</span></span>|<span data-ttu-id="c817d-199">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="c817d-199">NODE_SUPPORT</span></span>|<span data-ttu-id="c817d-200">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="c817d-200">MSOLAP_NODE_SCORE</span></span>|<span data-ttu-id="c817d-201">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c817d-201">NODE_TYPE</span></span>|  
|----------------|-------------------|-----------------------|-------------------|-------------------------|----------------|  
|<span data-ttu-id="c817d-202">10</span><span class="sxs-lookup"><span data-stu-id="c817d-202">10</span></span>|<span data-ttu-id="c817d-203">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="c817d-203">Bike Buyer -> Region</span></span>|<span data-ttu-id="c817d-204">1</span><span class="sxs-lookup"><span data-stu-id="c817d-204">1</span></span>|<span data-ttu-id="c817d-205">17484</span><span class="sxs-lookup"><span data-stu-id="c817d-205">17484</span></span>|<span data-ttu-id="c817d-206">84.51555875</span><span class="sxs-lookup"><span data-stu-id="c817d-206">84.51555875</span></span>|<span data-ttu-id="c817d-207">10</span><span class="sxs-lookup"><span data-stu-id="c817d-207">10</span></span>|  
|<span data-ttu-id="c817d-208">11</span><span class="sxs-lookup"><span data-stu-id="c817d-208">11</span></span>|<span data-ttu-id="c817d-209">Bike Buyer -> Region = Missing</span><span class="sxs-lookup"><span data-stu-id="c817d-209">Bike Buyer -> Region = Missing</span></span>|<span data-ttu-id="c817d-210">0</span><span class="sxs-lookup"><span data-stu-id="c817d-210">0</span></span>|<span data-ttu-id="c817d-211">0</span><span class="sxs-lookup"><span data-stu-id="c817d-211">0</span></span>|<span data-ttu-id="c817d-212">0</span><span class="sxs-lookup"><span data-stu-id="c817d-212">0</span></span>|<span data-ttu-id="c817d-213">11</span><span class="sxs-lookup"><span data-stu-id="c817d-213">11</span></span>|  
|<span data-ttu-id="c817d-214">11</span><span class="sxs-lookup"><span data-stu-id="c817d-214">11</span></span>|<span data-ttu-id="c817d-215">Bike Buyer -> Region = North America</span><span class="sxs-lookup"><span data-stu-id="c817d-215">Bike Buyer -> Region = North America</span></span>|<span data-ttu-id="c817d-216">0.508236102</span><span class="sxs-lookup"><span data-stu-id="c817d-216">0.508236102</span></span>|<span data-ttu-id="c817d-217">8886</span><span class="sxs-lookup"><span data-stu-id="c817d-217">8886</span></span>|<span data-ttu-id="c817d-218">0</span><span class="sxs-lookup"><span data-stu-id="c817d-218">0</span></span>|<span data-ttu-id="c817d-219">11</span><span class="sxs-lookup"><span data-stu-id="c817d-219">11</span></span>|  
|<span data-ttu-id="c817d-220">11</span><span class="sxs-lookup"><span data-stu-id="c817d-220">11</span></span>|<span data-ttu-id="c817d-221">Bike Buyer -> Region = Pacific</span><span class="sxs-lookup"><span data-stu-id="c817d-221">Bike Buyer -> Region = Pacific</span></span>|<span data-ttu-id="c817d-222">0.193891558</span><span class="sxs-lookup"><span data-stu-id="c817d-222">0.193891558</span></span>|<span data-ttu-id="c817d-223">3390</span><span class="sxs-lookup"><span data-stu-id="c817d-223">3390</span></span>|<span data-ttu-id="c817d-224">0</span><span class="sxs-lookup"><span data-stu-id="c817d-224">0</span></span>|<span data-ttu-id="c817d-225">11</span><span class="sxs-lookup"><span data-stu-id="c817d-225">11</span></span>|  
|<span data-ttu-id="c817d-226">11</span><span class="sxs-lookup"><span data-stu-id="c817d-226">11</span></span>|<span data-ttu-id="c817d-227">Bike Buyer -> Region = Europe</span><span class="sxs-lookup"><span data-stu-id="c817d-227">Bike Buyer -> Region = Europe</span></span>|<span data-ttu-id="c817d-228">0.29787234</span><span class="sxs-lookup"><span data-stu-id="c817d-228">0.29787234</span></span>|<span data-ttu-id="c817d-229">5208</span><span class="sxs-lookup"><span data-stu-id="c817d-229">5208</span></span>|<span data-ttu-id="c817d-230">0</span><span class="sxs-lookup"><span data-stu-id="c817d-230">0</span></span>|<span data-ttu-id="c817d-231">11</span><span class="sxs-lookup"><span data-stu-id="c817d-231">11</span></span>|  
  
 <span data-ttu-id="c817d-232">ノードに格納されている列の一部は、ノードの確率スコアやノードのサポート値など、マージナル統計ノードから取得できるものと同じです。</span><span class="sxs-lookup"><span data-stu-id="c817d-232">Some of the columns stored in the nodes are the same that you can get from the marginal statistics nodes, such as the node probability score and the node support values.</span></span> <span data-ttu-id="c817d-233">ただし、MSOLAP_NODE_SCORE は、入力属性ノードにのみ与えられる特殊な値で、モデル内でのこの属性の相対的な重要度を示します。</span><span class="sxs-lookup"><span data-stu-id="c817d-233">However, the MSOLAP_NODE_SCORE is a special value provided only for the input attribute nodes, and indicates the relative importance of this attribute in the model.</span></span> <span data-ttu-id="c817d-234">ビューアーの [依存関係ネットワーク] ペインで同じ情報を参照できますが、ビューアーにはスコアが表示されません。</span><span class="sxs-lookup"><span data-stu-id="c817d-234">You can see much the same information in the Dependency Network pane of the viewer; however, the viewer does not provide scores.</span></span>  
  
 <span data-ttu-id="c817d-235">次のクエリはモデル内のすべての属性の重要度スコアを返します。</span><span class="sxs-lookup"><span data-stu-id="c817d-235">The following query returns the importance scores of all attributes in the model:</span></span>  
  
```  
SELECT NODE_CAPTION, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
ORDER BY MSOLAP_NODE_SCORE DESC  
```  
  
 <span data-ttu-id="c817d-236">サンプルの結果 :</span><span class="sxs-lookup"><span data-stu-id="c817d-236">Sample results:</span></span>  
  
|<span data-ttu-id="c817d-237">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="c817d-237">NODE_CAPTION</span></span>|<span data-ttu-id="c817d-238">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="c817d-238">MSOLAP_NODE_SCORE</span></span>|  
|-------------------|-------------------------|  
|<span data-ttu-id="c817d-239">Bike Buyer -> Total Children</span><span class="sxs-lookup"><span data-stu-id="c817d-239">Bike Buyer -> Total Children</span></span>|<span data-ttu-id="c817d-240">181.3654836</span><span class="sxs-lookup"><span data-stu-id="c817d-240">181.3654836</span></span>|  
|<span data-ttu-id="c817d-241">Bike Buyer -> Commute Distance</span><span class="sxs-lookup"><span data-stu-id="c817d-241">Bike Buyer -> Commute Distance</span></span>|<span data-ttu-id="c817d-242">179.8419482</span><span class="sxs-lookup"><span data-stu-id="c817d-242">179.8419482</span></span>|  
|<span data-ttu-id="c817d-243">Bike Buyer -> English Education</span><span class="sxs-lookup"><span data-stu-id="c817d-243">Bike Buyer -> English Education</span></span>|<span data-ttu-id="c817d-244">156.9841928</span><span class="sxs-lookup"><span data-stu-id="c817d-244">156.9841928</span></span>|  
|<span data-ttu-id="c817d-245">Bike Buyer -> Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="c817d-245">Bike Buyer -> Number Children At Home</span></span>|<span data-ttu-id="c817d-246">111.8122599</span><span class="sxs-lookup"><span data-stu-id="c817d-246">111.8122599</span></span>|  
|<span data-ttu-id="c817d-247">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="c817d-247">Bike Buyer -> Region</span></span>|<span data-ttu-id="c817d-248">84.51555875</span><span class="sxs-lookup"><span data-stu-id="c817d-248">84.51555875</span></span>|  
|<span data-ttu-id="c817d-249">Bike Buyer -> Marital Status</span><span class="sxs-lookup"><span data-stu-id="c817d-249">Bike Buyer -> Marital Status</span></span>|<span data-ttu-id="c817d-250">23.13297354</span><span class="sxs-lookup"><span data-stu-id="c817d-250">23.13297354</span></span>|  
|<span data-ttu-id="c817d-251">Bike Buyer -> English Occupation</span><span class="sxs-lookup"><span data-stu-id="c817d-251">Bike Buyer -> English Occupation</span></span>|<span data-ttu-id="c817d-252">2.832069191</span><span class="sxs-lookup"><span data-stu-id="c817d-252">2.832069191</span></span>|  
  
 <span data-ttu-id="c817d-253">[Microsoft 汎用コンテンツ ツリー ビューアー](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)でモデル コンテンツを参照すると、どの統計が興味深いかがわかります。</span><span class="sxs-lookup"><span data-stu-id="c817d-253">By browsing the model content in the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md), you will get a better idea of what statistics might be interesting.</span></span> <span data-ttu-id="c817d-254">ここでは簡単な例をいくつか示しています。複数のクエリの実行や、結果を格納した後のクライアント上での処理が必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c817d-254">Some simple examples were demonstrated here; more often you may need to execute multiple queries or store the results and process them on the client.</span></span>  
  
###  <a name="sample-query-4-using-system-stored-procedures"></a><a name="bkmk_Query4"></a> <span data-ttu-id="c817d-255">サンプル クエリ 4: システム ストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="c817d-255">Sample Query 4: Using System Stored Procedures</span></span>  
 <span data-ttu-id="c817d-256">独自のコンテンツ クエリを記述することに加え、Analysis Services システム ストアド プロシージャを使用して結果を検証できます。</span><span class="sxs-lookup"><span data-stu-id="c817d-256">In addition to writing your own content queries, you can use some Analysis Services system stored procedures to explore the results.</span></span> <span data-ttu-id="c817d-257">システム ストアド プロシージャを使用するには、ストアド プロシージャ名に CALL キーワードのプレフィックスを付けます。</span><span class="sxs-lookup"><span data-stu-id="c817d-257">To use a system stored procedure, prefix the stored procedure name with the CALL keyword:</span></span>  
  
```  
CALL GetPredictableAttributes ('TM_NaiveBayes')  
```  
  
 <span data-ttu-id="c817d-258">結果の一部 :</span><span class="sxs-lookup"><span data-stu-id="c817d-258">Partial results:</span></span>  
  
|<span data-ttu-id="c817d-259">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="c817d-259">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="c817d-260">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="c817d-260">NODE_UNIQUE_NAME</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="c817d-261">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="c817d-261">Bike Buyer</span></span>|<span data-ttu-id="c817d-262">100000001</span><span class="sxs-lookup"><span data-stu-id="c817d-262">100000001</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c817d-263">これらのシステム ストアド プロシージャは、Analysis Services のサーバーとクライアントの間での内部通信用で、マイニング モデルの開発とテストを容易にするためにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="c817d-263">These system stored procedures are for internal communication between the Analysis Services server and the client and should only be used for convenience when developing and testing mining models.</span></span> <span data-ttu-id="c817d-264">実稼働システムのクエリを作成するときには、常に DMX を使用して独自のクエリを作成してください。</span><span class="sxs-lookup"><span data-stu-id="c817d-264">When you create queries for a production system, you should always write your own queries by using DMX.</span></span>  
  
 <span data-ttu-id="c817d-265">Analysis Services システム ストアド プロシージャの詳細については、「[データ マイニングのストアド プロシージャ &#40;Analysis Services - データ マイニング&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c817d-265">For more information about Analysis Services system stored procedures, see [Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).</span></span>  
  
## <a name="using-a-naive-bayes-model-to-make-predictions"></a><span data-ttu-id="c817d-266">Naive Bayes モデルを使用して予測を作成する</span><span class="sxs-lookup"><span data-stu-id="c817d-266">Using a Naive Bayes Model to Make Predictions</span></span>  
 <span data-ttu-id="c817d-267">Microsoft Naive Bayes アルゴリズムは、通常、予測に使用するよりも、入力属性と予測可能な属性の間のリレーションシップの検証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c817d-267">The Microsoft Naive Bayes algorithm is typically used less for prediction than it is for exploration of relationships among the input and predictable attributes.</span></span> <span data-ttu-id="c817d-268">ただし、モデルでは予測とアソシエーションの両方に予測関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c817d-268">However, the model supports the use of prediction functions for both prediction and association.</span></span>  
  
###  <a name="sample-query-5-predicting-outcomes-using-a-singleton-query"></a><a name="bkmk_Query5"></a> <span data-ttu-id="c817d-269">サンプル クエリ 5: 単一クエリを使用して結果を予測する</span><span class="sxs-lookup"><span data-stu-id="c817d-269">Sample Query 5: Predicting Outcomes using a Singleton Query</span></span>  
 <span data-ttu-id="c817d-270">次のクエリでは、単一クエリを使用して、新しい値を指定し、モデルに基づいてこれらの特性を持つ顧客が自転車を購入するかどうかを予測します。</span><span class="sxs-lookup"><span data-stu-id="c817d-270">The following query uses a singleton query to provide a new value and predict, based on the model, whether a customer with these characteristics is likely to buy a bike.</span></span> <span data-ttu-id="c817d-271">回帰モデルで単一クエリを作成する最も簡単な方法は、 **[単一クエリ入力]** ダイアログ ボックスを使用することです。</span><span class="sxs-lookup"><span data-stu-id="c817d-271">The easiest way to create a singleton query on a regression model is by using the **Singleton Query Input** dialog box.</span></span> <span data-ttu-id="c817d-272">たとえば、次の DMX クエリを作成するには、 `TM_NaiveBayes` モデルを選択し、 **[単一クエリ]** をクリックして、 `[Commute Distance]` および `Gender`のドロップダウン リストから値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c817d-272">For example, you can build the following DMX query by selecting the `TM_NaiveBayes` model, choosing **Singleton Query**, and selecting values from the dropdown lists for `[Commute Distance]` and `Gender`.</span></span>  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="c817d-273">結果の例:</span><span class="sxs-lookup"><span data-stu-id="c817d-273">Example results:</span></span>  
  
|<span data-ttu-id="c817d-274">式</span><span class="sxs-lookup"><span data-stu-id="c817d-274">Expression</span></span>|  
|----------------|  
|<span data-ttu-id="c817d-275">0</span><span class="sxs-lookup"><span data-stu-id="c817d-275">0</span></span>|  
  
 <span data-ttu-id="c817d-276">予測関数は、最も可能性の高い値を返します。この場合は 0 で、この種類の顧客は自転車を購入する可能性が低いことを表します。</span><span class="sxs-lookup"><span data-stu-id="c817d-276">The prediction function returns the most likely value, in this case, 0, which means this type of customer is unlikely to purchase a bike.</span></span>  
  
###  <a name="sample-query-6-getting-predictions-with-probability-and-support-values"></a><a name="bkmk_Query6"></a><span data-ttu-id="c817d-277">サンプルクエリ 6: 確率およびサポートの値を使用して予測を取得する</span><span class="sxs-lookup"><span data-stu-id="c817d-277">Sample Query 6: Getting Predictions with Probability and Support Values</span></span>  
 <span data-ttu-id="c817d-278">結果の予測に加えて、予測の信頼性の高さを調べることもあります。</span><span class="sxs-lookup"><span data-stu-id="c817d-278">In addition to predicting an outcome, you often want to know how strong the prediction is.</span></span> <span data-ttu-id="c817d-279">次のクエリでは、前の例と同じ単一クエリを使用しますが、予測関数 [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx) を追加し、予測の裏付けとなる統計を含む入れ子になったテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="c817d-279">The following query uses the same singleton query as the previous example, but adds the prediction function, [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), to return a nested table that contains statistics in support of the prediction.</span></span>  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer]),  
  PredictHistogram([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="c817d-280">結果の例:</span><span class="sxs-lookup"><span data-stu-id="c817d-280">Example results:</span></span>  
  
|<span data-ttu-id="c817d-281">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="c817d-281">Bike Buyer</span></span>|<span data-ttu-id="c817d-282">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="c817d-282">$SUPPORT</span></span>|<span data-ttu-id="c817d-283">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="c817d-283">$PROBABILITY</span></span>|<span data-ttu-id="c817d-284">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="c817d-284">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="c817d-285">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="c817d-285">$VARIANCE</span></span>|<span data-ttu-id="c817d-286">$STDEV</span><span class="sxs-lookup"><span data-stu-id="c817d-286">$STDEV</span></span>|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="c817d-287">0</span><span class="sxs-lookup"><span data-stu-id="c817d-287">0</span></span>|<span data-ttu-id="c817d-288">10161.5714</span><span class="sxs-lookup"><span data-stu-id="c817d-288">10161.5714</span></span>|<span data-ttu-id="c817d-289">0.581192599</span><span class="sxs-lookup"><span data-stu-id="c817d-289">0.581192599</span></span>|<span data-ttu-id="c817d-290">0.010530981</span><span class="sxs-lookup"><span data-stu-id="c817d-290">0.010530981</span></span>|<span data-ttu-id="c817d-291">0</span><span class="sxs-lookup"><span data-stu-id="c817d-291">0</span></span>|<span data-ttu-id="c817d-292">0</span><span class="sxs-lookup"><span data-stu-id="c817d-292">0</span></span>|  
|<span data-ttu-id="c817d-293">1</span><span class="sxs-lookup"><span data-stu-id="c817d-293">1</span></span>|<span data-ttu-id="c817d-294">7321.428768</span><span class="sxs-lookup"><span data-stu-id="c817d-294">7321.428768</span></span>|<span data-ttu-id="c817d-295">0.418750215</span><span class="sxs-lookup"><span data-stu-id="c817d-295">0.418750215</span></span>|<span data-ttu-id="c817d-296">0.008945684</span><span class="sxs-lookup"><span data-stu-id="c817d-296">0.008945684</span></span>|<span data-ttu-id="c817d-297">0</span><span class="sxs-lookup"><span data-stu-id="c817d-297">0</span></span>|<span data-ttu-id="c817d-298">0</span><span class="sxs-lookup"><span data-stu-id="c817d-298">0</span></span>|  
||<span data-ttu-id="c817d-299">0.999828444</span><span class="sxs-lookup"><span data-stu-id="c817d-299">0.999828444</span></span>|<span data-ttu-id="c817d-300">5.72E-05</span><span class="sxs-lookup"><span data-stu-id="c817d-300">5.72E-05</span></span>|<span data-ttu-id="c817d-301">5.72E-05</span><span class="sxs-lookup"><span data-stu-id="c817d-301">5.72E-05</span></span>|<span data-ttu-id="c817d-302">0</span><span class="sxs-lookup"><span data-stu-id="c817d-302">0</span></span>|<span data-ttu-id="c817d-303">0</span><span class="sxs-lookup"><span data-stu-id="c817d-303">0</span></span>|  
  
 <span data-ttu-id="c817d-304">テーブルの最後の行は、不足値のサポートと確率に対する調整を示します。</span><span class="sxs-lookup"><span data-stu-id="c817d-304">The final row in the table shows the adjustments to support and probability for the missing value.</span></span> <span data-ttu-id="c817d-305">Naive Bayes モデルは連続値をモデリングできないため、分散値と標準偏差値は常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="c817d-305">Variance and standard deviation values are always 0, because Naive Bayes models cannot model continuous values.</span></span>  
  
###  <a name="sample-query-7-predicting-associations"></a><a name="bkmk_Query7"></a><span data-ttu-id="c817d-306">サンプルクエリ 7: アソシエーションを予測する</span><span class="sxs-lookup"><span data-stu-id="c817d-306">Sample Query 7: Predicting Associations</span></span>  
 <span data-ttu-id="c817d-307">予測可能な属性をキーとして持つ入れ子になったテーブルがマイニング構造に含まれる場合、Microsoft Naive Bayes アルゴリズムをアソシエーション分析に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c817d-307">The Microsoft Naive Bayes algorithm can be used for association analysis, if the mining structure contains a nested table with the predictable attribute as the key.</span></span> <span data-ttu-id="c817d-308">たとえば、データ マイニング チュートリアルの「[レッスン 3: マーケット バスケット シナリオの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)」で作成したマイニング構造を使用して、Naive Bayes モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c817d-308">For example, you could build a Naive Bayes model by using the mining structure created in [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) of the data mining tutorial.</span></span> <span data-ttu-id="c817d-309">この例で使用したモデルは、ケース テーブルに収入および顧客の地域に関する情報を加えるよう変更されています。</span><span class="sxs-lookup"><span data-stu-id="c817d-309">The model used in this example was modified to add information about income and customer region in the case table.</span></span>  
  
 <span data-ttu-id="c817d-310">次のクエリの例では、製品 `'Road Tire Tube'`の購入に関連する製品を予測する単一クエリを示します。</span><span class="sxs-lookup"><span data-stu-id="c817d-310">The following query example shows a singleton query that predicts products that are related to purchases of the product, `'Road Tire Tube'`.</span></span> <span data-ttu-id="c817d-311">この情報は、特定の種類の顧客に製品を勧めるために使用できます。</span><span class="sxs-lookup"><span data-stu-id="c817d-311">You might use this information to recommend products to a specific type of customer.</span></span>  
  
```  
SELECT   PredictAssociation([Association].[v Assoc Seq Line Items])  
FROM [Association_NB]  
NATURAL PREDICTION JOIN  
(SELECT 'High' AS [Income Group],  
  'Europe' AS [Region],  
  (SELECT 'Road Tire Tube' AS [Model])   
AS [v Assoc Seq Line Items])   
AS t  
```  
  
 <span data-ttu-id="c817d-312">結果の一部 :</span><span class="sxs-lookup"><span data-stu-id="c817d-312">Partial results:</span></span>  
  
|<span data-ttu-id="c817d-313">モデル</span><span class="sxs-lookup"><span data-stu-id="c817d-313">Model</span></span>|  
|-----------|  
|<span data-ttu-id="c817d-314">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="c817d-314">Women's Mountain Shorts</span></span>|  
|<span data-ttu-id="c817d-315">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="c817d-315">Water Bottle</span></span>|  
|<span data-ttu-id="c817d-316">Touring-3000</span><span class="sxs-lookup"><span data-stu-id="c817d-316">Touring-3000</span></span>|  
|<span data-ttu-id="c817d-317">Touring-2000</span><span class="sxs-lookup"><span data-stu-id="c817d-317">Touring-2000</span></span>|  
|<span data-ttu-id="c817d-318">Touring 1000</span><span class="sxs-lookup"><span data-stu-id="c817d-318">Touring-1000</span></span>|  
  
## <a name="function-list"></a><span data-ttu-id="c817d-319">関数一覧</span><span class="sxs-lookup"><span data-stu-id="c817d-319">Function List</span></span>  
 <span data-ttu-id="c817d-320">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c817d-320">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="c817d-321">ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、次の表のような追加の関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c817d-321">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c817d-322">予測関数</span><span class="sxs-lookup"><span data-stu-id="c817d-322">Prediction Function</span></span>|<span data-ttu-id="c817d-323">使用法</span><span class="sxs-lookup"><span data-stu-id="c817d-323">Usage</span></span>|  
|[<span data-ttu-id="c817d-324">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c817d-324">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="c817d-325">あるノードがモデル内の別のノードの子であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c817d-325">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="c817d-326">Predict &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c817d-326">Predict &#40;DMX&#41;</span></span>](/sql/dmx/predict-dmx)|<span data-ttu-id="c817d-327">指定された列に対して、予測された値、または値のセットを返します。</span><span class="sxs-lookup"><span data-stu-id="c817d-327">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="c817d-328">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c817d-328">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="c817d-329">重み付け確率を返します。</span><span class="sxs-lookup"><span data-stu-id="c817d-329">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="c817d-330">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c817d-330">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="c817d-331">結合データセットのメンバーシップを予測します。</span><span class="sxs-lookup"><span data-stu-id="c817d-331">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="c817d-332">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c817d-332">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="c817d-333">各ケースの Node_ID を返します。</span><span class="sxs-lookup"><span data-stu-id="c817d-333">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="c817d-334">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c817d-334">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="c817d-335">予測値の確率を返します。</span><span class="sxs-lookup"><span data-stu-id="c817d-335">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="c817d-336">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="c817d-336">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="c817d-337">指定された状態に対するサポート値を返します。</span><span class="sxs-lookup"><span data-stu-id="c817d-337">Returns the support value for a specified state.</span></span>|  
  
 <span data-ttu-id="c817d-338">特定の関数の構文については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c817d-338">To see  the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c817d-339">参照</span><span class="sxs-lookup"><span data-stu-id="c817d-339">See Also</span></span>  
 <span data-ttu-id="c817d-340">[Microsoft Naive Bayes アルゴリズムテクニカルリファレンス](microsoft-naive-bayes-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c817d-340">[Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="c817d-341">[Microsoft Naive Bayes アルゴリズム](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c817d-341">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 [<span data-ttu-id="c817d-342">Naive Bayes モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="c817d-342">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
