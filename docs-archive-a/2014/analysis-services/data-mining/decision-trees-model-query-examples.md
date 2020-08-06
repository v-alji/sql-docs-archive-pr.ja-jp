---
title: デシジョンツリーモデルのクエリ例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- decision tree algorithms [Analysis Services]
- content queries [DMX]
- decision trees [Analysis Services]
ms.assetid: ceaf1370-9dd1-4d1a-a143-7f89a723ef80
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7a6b158a42c9ca90bf2cfd2e9b981a1e2a735ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713646"
---
# <a name="decision-trees-model-query-examples"></a><span data-ttu-id="6f3db-102">デシジョン ツリー モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="6f3db-102">Decision Trees Model Query Examples</span></span>
  <span data-ttu-id="6f3db-103">データ マイニング モデルに対するクエリを作成する際には、コンテンツ クエリを作成することも、予測クエリを作成することもできます。コンテンツ クエリでは、分析で検出されたパターンの詳細情報を取得できます。予測クエリでは、モデル内のパターンを使用して新しいデータについての予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="6f3db-104">たとえば、デシジョン ツリー モデルでコンテンツ クエリを使用すると、ツリーの各レベルのケースの数に関する統計や、ケースを区別するルールを取得できます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-104">For example, a content query for a decision trees model might provide statistics about the number of cases at each level of the tree, or the rules that differentiate between cases.</span></span> <span data-ttu-id="6f3db-105">一方、予測クエリを使用すると、モデルを新しいデータにマップして、提案や分類などを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-105">Alternatively, a prediction query maps the model to new data in order to generate recommendations, classifications, and so forth.</span></span> <span data-ttu-id="6f3db-106">クエリを使用してモデルに関するメタデータを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-106">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="6f3db-107">ここでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムに基づくモデルに対するクエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-107">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
 <span data-ttu-id="6f3db-108">**コンテンツ クエリ**</span><span class="sxs-lookup"><span data-stu-id="6f3db-108">**Content Queries**</span></span>  
  
 [<span data-ttu-id="6f3db-109">データ マイニング スキーマ行セットからモデル パラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-109">Retrieving Model Parameters from the Data Mining Schema Rowset</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="6f3db-110">DMX を使用してモデルのツリーについての詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-110">Getting Details about Trees in the Model by Using DMX</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="6f3db-111">モデルからサブツリーを取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-111">Retrieving Subtrees from the Model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="6f3db-112">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="6f3db-112">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="6f3db-113">確率付きの予測を取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-113">Returning Predictions with Probabilities</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="6f3db-114">デシジョン ツリー モデルからアソシエーションを予測する</span><span class="sxs-lookup"><span data-stu-id="6f3db-114">Predicting Associations from a Decision Trees Model</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="6f3db-115">デシジョン ツリー モデルから回帰式を取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-115">Retrieving a Regression Formula from a Decision Trees Model</span></span>](#bkmk_Query6)  
  
##  <a name="finding-information-about-a-decision-trees-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="6f3db-116">デシジョン ツリー モデルに関する情報の入手</span><span class="sxs-lookup"><span data-stu-id="6f3db-116">Finding Information about a Decision Trees Model</span></span>  
 <span data-ttu-id="6f3db-117">デシジョン ツリー モデルのコンテンツに対して意味のあるクエリを作成するには、モデル コンテンツの構造や、各種類のノードに格納されている情報の種類を把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-117">To create meaningful queries on the content of a decision trees model, you should understand the structure of the model content, and which node types store what kind of information.</span></span> <span data-ttu-id="6f3db-118">詳細については、「 [デシジョン ツリー モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f3db-118">For more information, see [Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-1-retrieving-model-parameters-from-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a> <span data-ttu-id="6f3db-119">サンプル クエリ 1: データ マイニング スキーマ行セットからモデル パラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-119">Sample Query 1: Retrieving Model Parameters from the Data Mining Schema Rowset</span></span>  
 <span data-ttu-id="6f3db-120">データ マイニング スキーマ行セットに対してクエリを実行すると、モデルに関するメタデータを取得できます (作成された日時、最後に処理された日時、基になるマイニング構造の名前、予測可能な属性として使用されている列の名前など)。</span><span class="sxs-lookup"><span data-stu-id="6f3db-120">By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute.</span></span> <span data-ttu-id="6f3db-121">モデルが最初に作成されたときに使用されたパラメーターを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-121">You can also return the parameters that were used when the model was first created.</span></span>  
  
```  
select MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Decision Tree'  
```  
  
 <span data-ttu-id="6f3db-122">サンプルの結果 :</span><span class="sxs-lookup"><span data-stu-id="6f3db-122">Sample results:</span></span>  
  
 <span data-ttu-id="6f3db-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6f3db-123">MINING_PARAMETERS</span></span>  
  
 <span data-ttu-id="6f3db-124">COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=</span><span class="sxs-lookup"><span data-stu-id="6f3db-124">COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=</span></span>  
  
###  <a name="sample-query-2-returning-details-about-the-model-content-by-using-dmx"></a><a name="bkmk_Query2"></a> <span data-ttu-id="6f3db-125">サンプル クエリ 2: DMX を使用してモデル コンテンツに関する詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-125">Sample Query 2: Returning Details about the Model Content by Using DMX</span></span>  
 <span data-ttu-id="6f3db-126">次のクエリは、「 [基本的なデータ マイニング チュートリアル](../../tutorials/basic-data-mining-tutorial.md)」でモデルを構築したときに作成したデシジョン ツリーに関する基本的な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-126">The following query returns some basic information about the decision trees that were created when you built the model in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="6f3db-127">各ツリー構造は、それ自体のノードに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-127">Each tree structure is stored in its own node.</span></span> <span data-ttu-id="6f3db-128">このモデルに含まれている予測可能な属性は 1 つなので、ツリー ノードは 1 つしかありません。</span><span class="sxs-lookup"><span data-stu-id="6f3db-128">Because this model contains a single predictable attribute, there is only one tree node.</span></span> <span data-ttu-id="6f3db-129">しかし、デシジョン ツリー アルゴリズムを使用してアソシエーション モデルを作成した場合は、各製品に 1 つずつ、何百ものツリーがあることもあります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-129">However, if you create an association model by using the Decision Trees algorithm, there might be hundreds of trees, one for each product.</span></span>  
  
 <span data-ttu-id="6f3db-130">このクエリでは、種類が 2 のノード (特定の予測可能な属性を表すツリーの最上位のノード) がすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-130">This query returns all the nodes of type 2, which are the top level nodes of a tree that represents a particular predictable attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f3db-131">`CHILDREN_CARDINALITY` という列は、MDX の同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-131">The column, `CHILDREN_CARDINALITY`, must be enclosed in brackets to distinguish it from the MDX reserved keyword of the same name.</span></span>  
  
```  
SELECT MODEL_NAME, NODE_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY]  
FROM TM_DecisionTrees.CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 <span data-ttu-id="6f3db-132">結果の例:</span><span class="sxs-lookup"><span data-stu-id="6f3db-132">Example results:</span></span>  
  
|<span data-ttu-id="6f3db-133">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="6f3db-133">MODEL_NAME</span></span>|<span data-ttu-id="6f3db-134">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="6f3db-134">NODE_NAME</span></span>|<span data-ttu-id="6f3db-135">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="6f3db-135">NODE_CAPTION</span></span>|<span data-ttu-id="6f3db-136">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="6f3db-136">NODE_SUPPORT</span></span>|<span data-ttu-id="6f3db-137">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="6f3db-137">CHILDREN_CARDINALITY</span></span>|  
|-----------------|----------------|-------------------|-------------------|---------------------------|  
|<span data-ttu-id="6f3db-138">TM_DecisionTree</span><span class="sxs-lookup"><span data-stu-id="6f3db-138">TM_DecisionTree</span></span>|<span data-ttu-id="6f3db-139">000000001</span><span class="sxs-lookup"><span data-stu-id="6f3db-139">000000001</span></span>|<span data-ttu-id="6f3db-140">All</span><span class="sxs-lookup"><span data-stu-id="6f3db-140">All</span></span>|<span data-ttu-id="6f3db-141">12939</span><span class="sxs-lookup"><span data-stu-id="6f3db-141">12939</span></span>|<span data-ttu-id="6f3db-142">5</span><span class="sxs-lookup"><span data-stu-id="6f3db-142">5</span></span>|  
  
 <span data-ttu-id="6f3db-143">この結果からわかることは何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="6f3db-143">What do these results tell you?</span></span> <span data-ttu-id="6f3db-144">デシジョン ツリー モデルの特定のノードのカーディナリティは、そのノードの直接の子の数を表します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-144">In a decision trees model, the cardinality of a particular node tells you how many immediate children that node has.</span></span> <span data-ttu-id="6f3db-145">このノードのカーディナリティは 5 なので、このモデルでは、対象になる母集団 (自転車を購入する可能性がある顧客) が 5 つのサブグループに分割されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-145">The cardinality for this node is 5, meaning that the model divided the target population of potential bike buyers into 5 subgroups.</span></span>  
  
 <span data-ttu-id="6f3db-146">次の関連するクエリは、この 5 つのサブグループの子を、子ノードの属性と値の分布と共に返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-146">The following related query returns the children for these five subgroups, together with the distribution of attributes and values in the child nodes.</span></span> <span data-ttu-id="6f3db-147">サポート、確率、分散などの統計は、`NODE_DISTRIBUTION` という入れ子になったテーブルに格納されているため、この例では、入れ子になったテーブル列を出力するために `FLATTENED` キーワードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-147">Because statistics such as support, probability, and variance are stored in the nested table, `NODE_DISTRIBUTION`, this example uses the `FLATTENED` keyword to output the nested table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f3db-148">入れ子になったテーブル列である `SUPPORT` は、同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-148">The nested table column, `SUPPORT`, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT]  
FROM NODE_DISTRIBUTION) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE [PARENT_UNIQUE_NAME] = '000000001'  
```  
  
 <span data-ttu-id="6f3db-149">結果の例:</span><span class="sxs-lookup"><span data-stu-id="6f3db-149">Example results:</span></span>  
  
|<span data-ttu-id="6f3db-150">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="6f3db-150">NODE_NAME</span></span>|<span data-ttu-id="6f3db-151">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="6f3db-151">NODE_CAPTION</span></span>|<span data-ttu-id="6f3db-152">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="6f3db-152">T.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="6f3db-153">T.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="6f3db-153">T.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="6f3db-154">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="6f3db-154">SUPPORT</span></span>|  
|----------------|-------------------|-----------------------|------------------------|-------------|  
|<span data-ttu-id="6f3db-155">00000000100</span><span class="sxs-lookup"><span data-stu-id="6f3db-155">00000000100</span></span>|<span data-ttu-id="6f3db-156">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="6f3db-156">Number Cars Owned = 0</span></span>|<span data-ttu-id="6f3db-157">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6f3db-157">Bike Buyer</span></span>|<span data-ttu-id="6f3db-158">Missing</span><span class="sxs-lookup"><span data-stu-id="6f3db-158">Missing</span></span>|<span data-ttu-id="6f3db-159">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-159">0</span></span>|  
|<span data-ttu-id="6f3db-160">00000000100</span><span class="sxs-lookup"><span data-stu-id="6f3db-160">00000000100</span></span>|<span data-ttu-id="6f3db-161">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="6f3db-161">Number Cars Owned = 0</span></span>|<span data-ttu-id="6f3db-162">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6f3db-162">Bike Buyer</span></span>|<span data-ttu-id="6f3db-163">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-163">0</span></span>|<span data-ttu-id="6f3db-164">1067</span><span class="sxs-lookup"><span data-stu-id="6f3db-164">1067</span></span>|  
|<span data-ttu-id="6f3db-165">00000000100</span><span class="sxs-lookup"><span data-stu-id="6f3db-165">00000000100</span></span>|<span data-ttu-id="6f3db-166">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="6f3db-166">Number Cars Owned = 0</span></span>|<span data-ttu-id="6f3db-167">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6f3db-167">Bike Buyer</span></span>|<span data-ttu-id="6f3db-168">1</span><span class="sxs-lookup"><span data-stu-id="6f3db-168">1</span></span>|<span data-ttu-id="6f3db-169">1875</span><span class="sxs-lookup"><span data-stu-id="6f3db-169">1875</span></span>|  
|<span data-ttu-id="6f3db-170">00000000101</span><span class="sxs-lookup"><span data-stu-id="6f3db-170">00000000101</span></span>|<span data-ttu-id="6f3db-171">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="6f3db-171">Number Cars Owned = 3</span></span>|<span data-ttu-id="6f3db-172">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6f3db-172">Bike Buyer</span></span>|<span data-ttu-id="6f3db-173">Missing</span><span class="sxs-lookup"><span data-stu-id="6f3db-173">Missing</span></span>|<span data-ttu-id="6f3db-174">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-174">0</span></span>|  
|<span data-ttu-id="6f3db-175">00000000101</span><span class="sxs-lookup"><span data-stu-id="6f3db-175">00000000101</span></span>|<span data-ttu-id="6f3db-176">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="6f3db-176">Number Cars Owned = 3</span></span>|<span data-ttu-id="6f3db-177">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6f3db-177">Bike Buyer</span></span>|<span data-ttu-id="6f3db-178">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-178">0</span></span>|<span data-ttu-id="6f3db-179">678</span><span class="sxs-lookup"><span data-stu-id="6f3db-179">678</span></span>|  
|<span data-ttu-id="6f3db-180">00000000101</span><span class="sxs-lookup"><span data-stu-id="6f3db-180">00000000101</span></span>|<span data-ttu-id="6f3db-181">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="6f3db-181">Number Cars Owned = 3</span></span>|<span data-ttu-id="6f3db-182">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6f3db-182">Bike Buyer</span></span>|<span data-ttu-id="6f3db-183">1</span><span class="sxs-lookup"><span data-stu-id="6f3db-183">1</span></span>|<span data-ttu-id="6f3db-184">473</span><span class="sxs-lookup"><span data-stu-id="6f3db-184">473</span></span>|  
  
 <span data-ttu-id="6f3db-185">これらの結果から、自転車を購入した顧客 ( `[Bike Buyer]` = 1)、1067のお客様が車を0台、473のお客様が3車を持っていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-185">From these results, you can tell that of the customers who bought a bike (`[Bike Buyer]` = 1), 1067 customers had 0 cars and 473 customers had 3 cars.</span></span>  
  
###  <a name="sample-query-3-retrieving-subtrees-from-the-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="6f3db-186">サンプル クエリ 3: モデルからサブツリーを取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-186">Sample Query 3: Retrieving Subtrees from the Model</span></span>  
 <span data-ttu-id="6f3db-187">実際に自転車を購入した顧客についてさらに調査する場合は、</span><span class="sxs-lookup"><span data-stu-id="6f3db-187">Suppose you wanted to discover more about the customers who did buy a bike.</span></span> <span data-ttu-id="6f3db-188">次の例のようにクエリで [IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx) 関数を使用すると、任意のサブツリーについて追加の詳細を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-188">You can view additional detail for any of the sub-trees by using the [IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx) function in the query, as shown in the following example.</span></span> <span data-ttu-id="6f3db-189">次のクエリは、42 歳以上の顧客を含むツリーのリーフ ノード (NODE_TYPE = 4) を取得して、自転車を購入した顧客の数を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-189">The query returns the count of bike purchasers by retrieving leaf nodes (NODE_TYPE = 4) from the tree that contains customers who are over 42 years of age.</span></span> <span data-ttu-id="6f3db-190">このクエリでは、入れ子になったテーブルの行が Bike Buyer = 1 の行のみに制限されています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-190">The query restricts rows from the nested table to those where Bike Buyer = 1.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,NODE_TYPE,  
(  
SELECT [SUPPORT] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Bike Buyer' AND ATTRIBUTE_VALUE = '1'  
) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE ISDESCENDANT('0000000010001')  
AND NODE_TYPE = 4  
```  
  
 <span data-ttu-id="6f3db-191">結果の例:</span><span class="sxs-lookup"><span data-stu-id="6f3db-191">Example results:</span></span>  
  
|<span data-ttu-id="6f3db-192">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="6f3db-192">NODE_NAME</span></span>|<span data-ttu-id="6f3db-193">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="6f3db-193">NODE_CAPTION</span></span>|<span data-ttu-id="6f3db-194">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="6f3db-194">t.SUPPORT</span></span>|  
|----------------|-------------------|---------------|  
|<span data-ttu-id="6f3db-195">000000001000100</span><span class="sxs-lookup"><span data-stu-id="6f3db-195">000000001000100</span></span>|<span data-ttu-id="6f3db-196">Yearly Income >= 26000 and < 42000</span><span class="sxs-lookup"><span data-stu-id="6f3db-196">Yearly Income >= 26000 and < 42000</span></span>|<span data-ttu-id="6f3db-197">266</span><span class="sxs-lookup"><span data-stu-id="6f3db-197">266</span></span>|  
|<span data-ttu-id="6f3db-198">00000000100010100</span><span class="sxs-lookup"><span data-stu-id="6f3db-198">00000000100010100</span></span>|<span data-ttu-id="6f3db-199">Total Children = 3</span><span class="sxs-lookup"><span data-stu-id="6f3db-199">Total Children = 3</span></span>|<span data-ttu-id="6f3db-200">75</span><span class="sxs-lookup"><span data-stu-id="6f3db-200">75</span></span>|  
|<span data-ttu-id="6f3db-201">0000000010001010100</span><span class="sxs-lookup"><span data-stu-id="6f3db-201">0000000010001010100</span></span>|<span data-ttu-id="6f3db-202">Number Children At Home = 1</span><span class="sxs-lookup"><span data-stu-id="6f3db-202">Number Children At Home = 1</span></span>|<span data-ttu-id="6f3db-203">75</span><span class="sxs-lookup"><span data-stu-id="6f3db-203">75</span></span>|  
  
## <a name="making-predictions-using-a-decision-trees-model"></a><span data-ttu-id="6f3db-204">デシジョン ツリー モデルを使用して予測を作成する</span><span class="sxs-lookup"><span data-stu-id="6f3db-204">Making Predictions using a Decision Trees Model</span></span>  
 <span data-ttu-id="6f3db-205">デシジョン ツリーは、分類、回帰、アソシエーションなど、さまざまなタスクに使用できるため、デシジョン ツリー モデルに対する予測クエリを作成する際にはさまざまな選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-205">Because decision trees can be used for various tasks, including classification, regression, and even association, when you create a prediction query on a decision tree model you have many options available to you.</span></span> <span data-ttu-id="6f3db-206">予測の結果を理解するには、モデルが作成された目的を把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-206">You must understand the purpose for which the model was created to understand the results of prediction.</span></span> <span data-ttu-id="6f3db-207">以下のクエリ サンプルでは、次の 3 つのシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-207">The following query samples illustrate three different scenarios:</span></span>  
  
-   <span data-ttu-id="6f3db-208">分類モデルの予測を、その予測が正しい確率と共に取得して、その確率で結果をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="6f3db-208">Returning a prediction for a classification model, together with the probability of the prediction being correct, and then filtering the results by the probability;</span></span>  
  
-   <span data-ttu-id="6f3db-209">単一クエリを作成してアソシエーションを予測する</span><span class="sxs-lookup"><span data-stu-id="6f3db-209">Creating a singleton query to predict associations;</span></span>  
  
-   <span data-ttu-id="6f3db-210">入力と出力が直線関係にあるデシジョン ツリーの部分の回帰式を取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-210">Retrieving the regression formula for a part of a decision tree where the relationship between the input and output is linear.</span></span>  
  
###  <a name="sample-query-4-returning-predictions-with-probabilities"></a><a name="bkmk_Query4"></a> <span data-ttu-id="6f3db-211">サンプル クエリ 4: 確率付きの予測を取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-211">Sample Query 4: Returning Predictions with Probabilities</span></span>  
 <span data-ttu-id="6f3db-212">次のサンプル クエリでは、「 [基本的なデータ マイニング チュートリアル](../../tutorials/basic-data-mining-tutorial.md)」で作成したデシジョン ツリー モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-212">The following sample query uses the decision tree model that was created in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="6f3db-213">クエリは [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW のテーブル dbo.ProspectiveBuyers にあるサンプル データの新しいセットを渡して、新しいデータ セット内のどの顧客が自転車を購入するかを予測します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-213">The query passes in a new set of sample data, from the table dbo.ProspectiveBuyers in [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW, to predict which of the customers in the new data set will purchase a bike.</span></span>  
  
 <span data-ttu-id="6f3db-214">このクエリでは、予測関数 [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)を使用しています。この関数は、モデルで検出された確率に関する有用な情報を含む入れ子になったテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-214">The query uses the prediction function [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), which returns a nested table that contains useful information about the probabilities discovered by the model.</span></span> <span data-ttu-id="6f3db-215">クエリの最後の WHERE 句は結果をフィルター処理して、自転車を購入する確率が 0% より大きいと予測された顧客のみを返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-215">The final WHERE clause of the query filters the results to return only those customers who are predicted as likely to buy a bike, with a probability greater than 0%.</span></span>  
  
```  
SELECT  
  [TM_DecisionTree].[Bike Buyer],  
  PredictHistogram([Bike Buyer]) as Results  
From  
  [TM_DecisionTree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [FirstName],  
      [LastName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM_DecisionTree].[First Name] = t.[FirstName] AND  
  [TM_DecisionTree].[Last Name] = t.[LastName] AND  
  [TM_DecisionTree].[Marital Status] = t.[MaritalStatus] AND  
  [TM_DecisionTree].[Gender] = t.[Gender] AND  
  [TM_DecisionTree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM_DecisionTree].[Total Children] = t.[TotalChildren] AND  
  [TM_DecisionTree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM_DecisionTree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM_DecisionTree].[Number Cars Owned] = t.[NumberCarsOwned]  
WHERE [Bike Buyer] = 1  
AND PredictProbability([Bike Buyer]) >'.05'  
```  
  
 <span data-ttu-id="6f3db-216">既定では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、入れ子になったテーブルを列ラベル **[Expression]** を使用して返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-216">By default, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns nested tables with the column label, **Expression**.</span></span> <span data-ttu-id="6f3db-217">このラベルを変更するには、返される列に別名を付けます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-217">You can change this label by aliasing the column that is returned.</span></span> <span data-ttu-id="6f3db-218">その別名 (この例の場合は **Results**) は、列見出しと、入れ子になったテーブルの値の両方に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-218">If you do this, the alias (in this case, **Results**) is used as both the column heading and as the value in the nested table.</span></span> <span data-ttu-id="6f3db-219">結果を表示するには、入れ子になったテーブルを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-219">You must expand the nested table to see the results.</span></span>  
  
 <span data-ttu-id="6f3db-220">自転車購入者 = 1 の場合の結果の例:</span><span class="sxs-lookup"><span data-stu-id="6f3db-220">Example results where Bike Buyer = 1:</span></span>  
  
|<span data-ttu-id="6f3db-221">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6f3db-221">Bike Buyer</span></span>|<span data-ttu-id="6f3db-222">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="6f3db-222">$SUPPORT</span></span>|<span data-ttu-id="6f3db-223">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="6f3db-223">$PROBABILITY</span></span>|<span data-ttu-id="6f3db-224">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="6f3db-224">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="6f3db-225">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="6f3db-225">$VARIANCE</span></span>|<span data-ttu-id="6f3db-226">$STDEV</span><span class="sxs-lookup"><span data-stu-id="6f3db-226">$STDEV</span></span>|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="6f3db-227">1</span><span class="sxs-lookup"><span data-stu-id="6f3db-227">1</span></span>|<span data-ttu-id="6f3db-228">2540</span><span class="sxs-lookup"><span data-stu-id="6f3db-228">2540</span></span>|<span data-ttu-id="6f3db-229">0.634849242045644</span><span class="sxs-lookup"><span data-stu-id="6f3db-229">0.634849242045644</span></span>|<span data-ttu-id="6f3db-230">0.013562168281562</span><span class="sxs-lookup"><span data-stu-id="6f3db-230">0.013562168281562</span></span>|<span data-ttu-id="6f3db-231">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-231">0</span></span>|<span data-ttu-id="6f3db-232">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-232">0</span></span>|  
|<span data-ttu-id="6f3db-233">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-233">0</span></span>|<span data-ttu-id="6f3db-234">1460</span><span class="sxs-lookup"><span data-stu-id="6f3db-234">1460</span></span>|<span data-ttu-id="6f3db-235">0.364984174579377</span><span class="sxs-lookup"><span data-stu-id="6f3db-235">0.364984174579377</span></span>|<span data-ttu-id="6f3db-236">0.00661336932550915</span><span class="sxs-lookup"><span data-stu-id="6f3db-236">0.00661336932550915</span></span>|<span data-ttu-id="6f3db-237">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-237">0</span></span>|<span data-ttu-id="6f3db-238">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-238">0</span></span>|  
||<span data-ttu-id="6f3db-239">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-239">0</span></span>|<span data-ttu-id="6f3db-240">0.000166583374979177</span><span class="sxs-lookup"><span data-stu-id="6f3db-240">0.000166583374979177</span></span>|<span data-ttu-id="6f3db-241">0.000166583374979177</span><span class="sxs-lookup"><span data-stu-id="6f3db-241">0.000166583374979177</span></span>|<span data-ttu-id="6f3db-242">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-242">0</span></span>|<span data-ttu-id="6f3db-243">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-243">0</span></span>|  
  
 <span data-ttu-id="6f3db-244">使用しているプロバイダーが、ここに示されているような階層的な行セットをサポートしていない場合は、クエリで FLATTENED キーワードを使用すると、繰り返される列値の代わりに NULL を含むテーブルとして結果を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-244">If your provider does not support hierarchical rowsets, such as those shown here, you can use the FLATTENED keyword in the query to return the results as a table that contains nulls in place of the repeated column values.</span></span> <span data-ttu-id="6f3db-245">詳細については、「[入れ子になったテーブル &#40;Analysis Services - データ マイニング&#41;](nested-tables-analysis-services-data-mining.md)」または「[DMX 選択ステートメントについて](/sql/dmx/understanding-the-dmx-select-statement)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f3db-245">For more information, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](nested-tables-analysis-services-data-mining.md) or [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement).</span></span>  
  
###  <a name="sample-query-5-predicting-associations-from-a-decision-trees-model"></a><a name="bkmk_Query5"></a> <span data-ttu-id="6f3db-246">サンプル クエリ 5: デシジョン ツリー モデルからアソシエーションを予測する</span><span class="sxs-lookup"><span data-stu-id="6f3db-246">Sample Query 5: Predicting Associations from a Decision Trees Model</span></span>  
 <span data-ttu-id="6f3db-247">次のサンプル クエリは、Association マイニング構造に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-247">The following sample query is based on the Association mining structure.</span></span> <span data-ttu-id="6f3db-248">このサンプルに従って作業するために、このマイニング構造に新しいモデルを追加し、アルゴリズムとして Microsoft デシジョン ツリーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-248">To follow along with this example, you can add a new model to this mining structure, and select Microsoft Decision Trees as the algorithm.</span></span> <span data-ttu-id="6f3db-249">アソシエーション マイニング モデルの作成方法の詳細については、「[レッスン 3 : マーケット バスケット シナリオの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f3db-249">For more information on how to create the Association mining structure, see [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
 <span data-ttu-id="6f3db-250">次のサンプル クエリは単一クエリです。このクエリは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でフィールドを選択し、それらのフィールドの値をドロップダウン リストから選択するだけで簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-250">The following sample query is a singleton query, which you can create easily in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] by choosing fields and then selecting values for those fields from a drop-down list.</span></span>  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
FROM  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Patch kit' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 <span data-ttu-id="6f3db-251">期待される結果:</span><span class="sxs-lookup"><span data-stu-id="6f3db-251">Expected results:</span></span>  
  
|<span data-ttu-id="6f3db-252">モデル</span><span class="sxs-lookup"><span data-stu-id="6f3db-252">Model</span></span>|  
|-----------|  
|<span data-ttu-id="6f3db-253">Mountain-200</span><span class="sxs-lookup"><span data-stu-id="6f3db-253">Mountain-200</span></span>|  
|<span data-ttu-id="6f3db-254">Mountain Tire Tube</span><span class="sxs-lookup"><span data-stu-id="6f3db-254">Mountain Tire Tube</span></span>|  
|<span data-ttu-id="6f3db-255">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="6f3db-255">Touring Tire Tube</span></span>|  
  
 <span data-ttu-id="6f3db-256">この結果から、Patch Kit という製品を購入した顧客に提案するのに最適な 3 つの製品がわかります。</span><span class="sxs-lookup"><span data-stu-id="6f3db-256">The results tell you the three best products to recommend to customers who have purchased the Patch Kit product.</span></span> <span data-ttu-id="6f3db-257">提案を行う際に複数の製品を入力として指定することもできます。そのためには、値を入力するか、 **[単一クエリ入力]** ダイアログ ボックスを使用して値を追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-257">You can also provide multiple products as input when you make recommendations, either by typing in values, or by using the **Singleton Query Input** dialog box and adding or removing values.</span></span> <span data-ttu-id="6f3db-258">次のサンプル クエリは、複数の値を指定して予測を行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-258">The following sample query shows how the multiple values are provided, upon which to make a prediction.</span></span> <span data-ttu-id="6f3db-259">値は、入力値を定義する SELECT ステートメント内の UNION 句で接続されています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-259">Values are connected by a UNION clause in the SELECT statement that defines the input values.</span></span>  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
From  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Racing Socks' AS [Model]  
  UNION SELECT 'Women''s Mountain Shorts' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 <span data-ttu-id="6f3db-260">期待される結果:</span><span class="sxs-lookup"><span data-stu-id="6f3db-260">Expected results:</span></span>  
  
|<span data-ttu-id="6f3db-261">モデル</span><span class="sxs-lookup"><span data-stu-id="6f3db-261">Model</span></span>|  
|-----------|  
|<span data-ttu-id="6f3db-262">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="6f3db-262">Long-Sleeve Logo Jersey</span></span>|  
|<span data-ttu-id="6f3db-263">Mountain-400-W</span><span class="sxs-lookup"><span data-stu-id="6f3db-263">Mountain-400-W</span></span>|  
|<span data-ttu-id="6f3db-264">Classic Vest</span><span class="sxs-lookup"><span data-stu-id="6f3db-264">Classic Vest</span></span>|  
  
###  <a name="sample-query-6-retrieving-a-regression-formula-from-a-decision-trees-model"></a><a name="bkmk_Query6"></a> <span data-ttu-id="6f3db-265">サンプル クエリ 6: デシジョン ツリー モデルから回帰式を取得する</span><span class="sxs-lookup"><span data-stu-id="6f3db-265">Sample Query 6: Retrieving a Regression Formula from a Decision Trees Model</span></span>  
 <span data-ttu-id="6f3db-266">連続属性の回帰を含むデシジョン ツリー モデルを作成すると、回帰式を使用して予測を行ったり、回帰式に関する情報を抽出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-266">When you create a decision tree model that contains a regression on a continuous attribute, you can use the regression formula to make predictions, or you can extract information about the regression formula.</span></span> <span data-ttu-id="6f3db-267">回帰モデルに対するクエリの詳細については、「 [線形回帰モデルのクエリ例](linear-regression-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f3db-267">For more information about queries on regression models, see [Linear Regression Model Query Examples](linear-regression-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="6f3db-268">デシジョン ツリー モデルに回帰ノードと、不連続属性や範囲で分割されるノードが混在している場合は、回帰ノードのみを返すクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6f3db-268">If a decision trees model contains a mixture of regression nodes and nodes that split on discrete attributes or ranges, you can create a query that returns only the regression node.</span></span> <span data-ttu-id="6f3db-269">NODE_DISTRIBUTION テーブルには、回帰式の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-269">The NODE_DISTRIBUTION table contains the details of the regression formula.</span></span> <span data-ttu-id="6f3db-270">この例では、見やすくするために列をフラット化して、NODE_DISTRIBUTION テーブルに別名を付けています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-270">In this example, the columns are flattened and the NODE_DISTRIBUTION table is aliased for easier viewing.</span></span> <span data-ttu-id="6f3db-271">しかし、このモデルでは、Income を他の連続属性に関連付けるためのリグレッサーは検出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="6f3db-271">However, in this model, no regressors were found to relate Income with other continuous attributes.</span></span> <span data-ttu-id="6f3db-272">このような場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、その属性の平均値とモデル内の全分散を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-272">In such cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns the mean value of the attribute and the total variance in the model for that attribute.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM DT_Predict. CONTENT  
WHERE NODE_TYPE = 25  
```  
  
 <span data-ttu-id="6f3db-273">結果の例:</span><span class="sxs-lookup"><span data-stu-id="6f3db-273">Example results:</span></span>  
  
|<span data-ttu-id="6f3db-274">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="6f3db-274">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="6f3db-275">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="6f3db-275">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="6f3db-276">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="6f3db-276">t.SUPPORT</span></span>|<span data-ttu-id="6f3db-277">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="6f3db-277">t.PROBABILITY</span></span>|<span data-ttu-id="6f3db-278">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="6f3db-278">t.VARIANCE</span></span>|<span data-ttu-id="6f3db-279">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="6f3db-279">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="6f3db-280">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="6f3db-280">Yearly Income</span></span>|<span data-ttu-id="6f3db-281">Missing</span><span class="sxs-lookup"><span data-stu-id="6f3db-281">Missing</span></span>|<span data-ttu-id="6f3db-282">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-282">0</span></span>|<span data-ttu-id="6f3db-283">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="6f3db-283">0.000457142857142857</span></span>|<span data-ttu-id="6f3db-284">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-284">0</span></span>|<span data-ttu-id="6f3db-285">1</span><span class="sxs-lookup"><span data-stu-id="6f3db-285">1</span></span>|  
|<span data-ttu-id="6f3db-286">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="6f3db-286">Yearly Income</span></span>|<span data-ttu-id="6f3db-287">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="6f3db-287">57220.8876687257</span></span>|<span data-ttu-id="6f3db-288">17484</span><span class="sxs-lookup"><span data-stu-id="6f3db-288">17484</span></span>|<span data-ttu-id="6f3db-289">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="6f3db-289">0.999542857142857</span></span>|<span data-ttu-id="6f3db-290">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="6f3db-290">1041275619.52776</span></span>|<span data-ttu-id="6f3db-291">3</span><span class="sxs-lookup"><span data-stu-id="6f3db-291">3</span></span>|  
||<span data-ttu-id="6f3db-292">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="6f3db-292">57220.8876687257</span></span>|<span data-ttu-id="6f3db-293">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-293">0</span></span>|<span data-ttu-id="6f3db-294">0</span><span class="sxs-lookup"><span data-stu-id="6f3db-294">0</span></span>|<span data-ttu-id="6f3db-295">1041216662.54387</span><span class="sxs-lookup"><span data-stu-id="6f3db-295">1041216662.54387</span></span>|<span data-ttu-id="6f3db-296">11</span><span class="sxs-lookup"><span data-stu-id="6f3db-296">11</span></span>|  
  
 <span data-ttu-id="6f3db-297">回帰モデルで使用される値型と統計の詳細については、「[線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f3db-297">For more information about the value types and the statistics used in regression models, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="6f3db-298">予測関数の一覧</span><span class="sxs-lookup"><span data-stu-id="6f3db-298">List of Prediction Functions</span></span>  
 <span data-ttu-id="6f3db-299">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-299">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="6f3db-300">ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムでは、次の表のような追加の関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6f3db-300">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f3db-301">予測関数</span><span class="sxs-lookup"><span data-stu-id="6f3db-301">Prediction Function</span></span>|<span data-ttu-id="6f3db-302">使用法</span><span class="sxs-lookup"><span data-stu-id="6f3db-302">Usage</span></span>|  
|[<span data-ttu-id="6f3db-303">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-303">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="6f3db-304">あるノードがモデル内の別のノードの子であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-304">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="6f3db-305">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-305">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="6f3db-306">指定されたノードが現在のケースを含んでいるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-306">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="6f3db-307">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-307">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="6f3db-308">重み付け確率を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-308">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="6f3db-309">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-309">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="6f3db-310">結合データセットのメンバーシップを予測します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-310">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="6f3db-311">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-311">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="6f3db-312">現在の予測値に関連する値のテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-312">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="6f3db-313">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-313">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="6f3db-314">各ケースの Node_ID を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-314">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="6f3db-315">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-315">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="6f3db-316">予測値の確率を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-316">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="6f3db-317">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-317">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="6f3db-318">指定された列に対して、予測された標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-318">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="6f3db-319">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-319">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="6f3db-320">指定された状態に対するサポート値を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-320">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="6f3db-321">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6f3db-321">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="6f3db-322">指定された列の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="6f3db-322">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="6f3db-323">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムに共通の関数の一覧については、「[一般的な予測関数 (DMX)](/sql/dmx/general-prediction-functions-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f3db-323">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="6f3db-324">特定の関数の構文については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f3db-324">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3db-325">参照</span><span class="sxs-lookup"><span data-stu-id="6f3db-325">See Also</span></span>  
 <span data-ttu-id="6f3db-326">[データマイニングクエリ](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="6f3db-326">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="6f3db-327">[Microsoft デシジョンツリーアルゴリズム](microsoft-decision-trees-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="6f3db-327">[Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md) </span></span>  
 <span data-ttu-id="6f3db-328">[Microsoft デシジョンツリーアルゴリズムテクニカルリファレンス](microsoft-decision-trees-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6f3db-328">[Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="6f3db-329">デシジョン ツリー モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="6f3db-329">Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)  
  
  
