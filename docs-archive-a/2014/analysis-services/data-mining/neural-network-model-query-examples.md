---
title: ニューラルネットワークモデルのクエリ例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- neural network algorithms [Analysis Services]
- content queries [DMX]
- neural network model [Analysis Services]
ms.assetid: 81b06183-620f-4e0c-bc10-532e6a1f0829
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7154ce0ad66346634225734fe829c36e7bf3ad58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718987"
---
# <a name="neural-network-model-query-examples"></a><span data-ttu-id="68dfb-102">Neural Network Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="68dfb-102">Neural Network Model Query Examples</span></span>
  <span data-ttu-id="68dfb-103">データ マイニング モデルに対するクエリを作成する際には、コンテンツ クエリを作成することも、予測クエリを作成することもできます。コンテンツ クエリでは、分析で検出されたパターンの詳細情報を取得できます。予測クエリでは、モデル内のパターンを使用して新しいデータについての予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="68dfb-104">たとえば、ニューラル ネットワーク モデルのコンテンツ クエリでは、非表示層の数などのモデル メタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-104">For example, a content query for a neural network model might retrieve model metadata such as the number of hidden layers.</span></span> <span data-ttu-id="68dfb-105">また、予測クエリでは、入力に基づいて分類を提示し、必要に応じて各分類の確率を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-105">Alternatively, a prediction query might suggest classifications based on an input and optionally provide probabilities for each classification.</span></span>  
  
 <span data-ttu-id="68dfb-106">ここでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムに基づくモデルに対するクエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-106">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span>  
  
 <span data-ttu-id="68dfb-107">**コンテンツクエリ**</span><span class="sxs-lookup"><span data-stu-id="68dfb-107">**Content queries**</span></span>  
  
 [<span data-ttu-id="68dfb-108">DMX を使用してモデル メタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="68dfb-108">Getting Model Metadata by Using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="68dfb-109">スキーマ行セットからモデル メタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="68dfb-109">Retrieving Model Metadata from the Schema Rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="68dfb-110">モデルの入力属性を取得する</span><span class="sxs-lookup"><span data-stu-id="68dfb-110">Retrieving the Input Attributes for the Model</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="68dfb-111">非表示層から重みを取得する</span><span class="sxs-lookup"><span data-stu-id="68dfb-111">Retrieving Weights from the Hidden Layer</span></span>](#bkmk_Query4)  
  
 <span data-ttu-id="68dfb-112">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="68dfb-112">**Prediction queries**</span></span>  
  
 [<span data-ttu-id="68dfb-113">単一予測を作成する</span><span class="sxs-lookup"><span data-stu-id="68dfb-113">Creating a Singleton Prediction</span></span>](#bkmk_Query5)  
  
## <a name="finding-information-about-a-neural-network-model"></a><span data-ttu-id="68dfb-114">ニューラル ネットワーク モデルに関する情報の入手</span><span class="sxs-lookup"><span data-stu-id="68dfb-114">Finding Information about a Neural Network Model</span></span>  
 <span data-ttu-id="68dfb-115">すべてのマイニング モデルでは、アルゴリズムによる学習内容が、正規化されたスキーマ (マイニング モデル スキーマ行セット) に従って公開されます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-115">All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset.</span></span> <span data-ttu-id="68dfb-116">この情報から、基本的なメタデータ、分析で検出された構造、処理の際に使用されたパラメーターなど、モデルに関する詳細情報を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-116">This information provides details about the model and includes the basic metadata, structures discovered in analysis, and parameters that are used when processing.</span></span> <span data-ttu-id="68dfb-117">モデル コンテンツに対するクエリは、データ マイニング拡張機能 (DMX) ステートメントを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-117">You can create queries against the model content by using Data Mining Extension (DMX) statements.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="68dfb-118">サンプル クエリ 1: DMX を使用してモデル メタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="68dfb-118">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="68dfb-119">次のクエリは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムを使用して作成されたモデルに関するいくつかの基本的なメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-119">The following query returns some basic metadata about a model that was built by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="68dfb-120">ニューラル ネットワーク モデルの親ノードには、モデルの名前、モデルが格納されているデータベースの名前、および子ノードの数だけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-120">In a neural network model, the parent node of the model contains only the name of the model, the name of the database where the model is stored, and the number of child nodes.</span></span> <span data-ttu-id="68dfb-121">ただし、マージナル統計ノード (NODE_TYPE = 24) によって、この基本的なメタデータと、モデルで使用される入力列に関するいくつかの派生した統計が提供されます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-121">However, the marginal statistics node (NODE_TYPE = 24) provides both this basic metadata and some derived statistics about the input columns used in the model.</span></span>  
  
 <span data-ttu-id="68dfb-122">次のサンプル クエリは、「 [中級者向けデータ マイニング チュートリアル](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)」で作成した `Call Center Default NN`というマイニング モデルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-122">The following sample query is based on the mining model that you create in the [Intermediate Data Mining Tutorial](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md), named `Call Center Default NN`.</span></span> <span data-ttu-id="68dfb-123">このモデルは、コール センターからのデータを使用して、人員配置と電話/注文/案件数との間に存在する可能性がある相関関係を探索します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-123">The model uses data from a call center to explore possible correlations between staffing and the number of calls, orders, and issues.</span></span> <span data-ttu-id="68dfb-124">この DMX ステートメントは、ニューラル ネットワーク モデルのマージナル統計ノードからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-124">The DMX statement retrieves data from the marginal statistics node of the neural network model.</span></span> <span data-ttu-id="68dfb-125">関心のある入力属性の統計が入れ子になったテーブル NODE_DISTRIBUTION に格納されているため、このクエリには FLATTENED キーワードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-125">The query includes the FLATTENED keyword, because the input attribute statistics of interest are stored in a nested table, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="68dfb-126">ただし、使用しているクエリ プロバイダーが階層的な行セットをサポートしている場合は、FLATTENED キーワードを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="68dfb-126">However, if your query provider supports hierarchical rowsets you do not need to use the FLATTENED keyword.</span></span>  
  
```  
SELECT FLATTENED MODEL_CATALOG, MODEL_NAME,   
(    SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE,  
     [SUPPORT], [PROBABILITY], VALUETYPE   
     FROM NODE_DISTRIBUTION  
) AS t  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 24  
```  
  
> [!NOTE]  
>  <span data-ttu-id="68dfb-127">入れ子になったテーブル列の名前 `[SUPPORT]` および `[PROBABILITY]` は、同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="68dfb-127">You must enclose the name of the nested table columns `[SUPPORT]` and `[PROBABILITY]` in brackets to distinguish them from the reserved keywords of the same name.</span></span>  
  
 <span data-ttu-id="68dfb-128">結果の例:</span><span class="sxs-lookup"><span data-stu-id="68dfb-128">Example results:</span></span>  
  
|<span data-ttu-id="68dfb-129">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="68dfb-129">MODEL_CATALOG</span></span>|<span data-ttu-id="68dfb-130">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="68dfb-130">MODEL_NAME</span></span>|<span data-ttu-id="68dfb-131">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="68dfb-131">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="68dfb-132">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="68dfb-132">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="68dfb-133">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="68dfb-133">t.SUPPORT</span></span>|<span data-ttu-id="68dfb-134">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="68dfb-134">t.PROBABILITY</span></span>|<span data-ttu-id="68dfb-135">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="68dfb-135">t.VALUETYPE</span></span>|  
|--------------------|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="68dfb-136">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="68dfb-136">Adventure Works DW Multidimensional 2012</span></span>|<span data-ttu-id="68dfb-137">Call Center NN</span><span class="sxs-lookup"><span data-stu-id="68dfb-137">Call Center NN</span></span>|<span data-ttu-id="68dfb-138">案件あたりの平均時間</span><span class="sxs-lookup"><span data-stu-id="68dfb-138">Average Time Per Issue</span></span>|<span data-ttu-id="68dfb-139">Missing</span><span class="sxs-lookup"><span data-stu-id="68dfb-139">Missing</span></span>|<span data-ttu-id="68dfb-140">0</span><span class="sxs-lookup"><span data-stu-id="68dfb-140">0</span></span>|<span data-ttu-id="68dfb-141">0</span><span class="sxs-lookup"><span data-stu-id="68dfb-141">0</span></span>|<span data-ttu-id="68dfb-142">1</span><span class="sxs-lookup"><span data-stu-id="68dfb-142">1</span></span>|  
|<span data-ttu-id="68dfb-143">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="68dfb-143">Adventure Works DW Multidimensional 2012</span></span>|<span data-ttu-id="68dfb-144">Call Center NN</span><span class="sxs-lookup"><span data-stu-id="68dfb-144">Call Center NN</span></span>|<span data-ttu-id="68dfb-145">案件あたりの平均時間</span><span class="sxs-lookup"><span data-stu-id="68dfb-145">Average Time Per Issue</span></span>|<span data-ttu-id="68dfb-146">< 64.7094100096</span><span class="sxs-lookup"><span data-stu-id="68dfb-146">< 64.7094100096</span></span>|<span data-ttu-id="68dfb-147">11</span><span class="sxs-lookup"><span data-stu-id="68dfb-147">11</span></span>|<span data-ttu-id="68dfb-148">0.407407407</span><span class="sxs-lookup"><span data-stu-id="68dfb-148">0.407407407</span></span>|<span data-ttu-id="68dfb-149">5</span><span class="sxs-lookup"><span data-stu-id="68dfb-149">5</span></span>|  
  
 <span data-ttu-id="68dfb-150">ニューラル ネットワーク モデルのコンテキストにおけるスキーマ行セットの列の意味については、「 [ニューラル ネットワーク モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)というマイニング モデルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-150">For a definition of what the columns in the schema rowset mean in the context of a neural network model, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-2-retrieving-model-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a><span data-ttu-id="68dfb-151">サンプルクエリ 2: スキーマ行セットからモデルメタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="68dfb-151">Sample Query 2: Retrieving Model Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="68dfb-152">データ マイニング スキーマ行セットに対してクエリを実行すると、DMX コンテンツ クエリで返されたのと同じ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-152">You can find the same information that is returned in a DMX content query by querying the data mining schema rowset.</span></span> <span data-ttu-id="68dfb-153">ただし、スキーマ行セットから返される情報にはいくつかの追加の列があります</span><span class="sxs-lookup"><span data-stu-id="68dfb-153">However, the schema rowset provides some additional columns.</span></span> <span data-ttu-id="68dfb-154">次のサンプル クエリは、モデルが作成された日、変更された日、および最後に処理された日を返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-154">The following sample query returns the date that the model was created, the date it was modified, and the date that the model was last processed.</span></span> <span data-ttu-id="68dfb-155">また、予測可能列 (モデル コンテンツから簡単に取得することはできません)、およびモデルの作成に使用されたパラメーターも返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-155">The query also returns the predictable columns, which are not easily available from the model content, and the parameters that were used to build the model.</span></span> <span data-ttu-id="68dfb-156">この情報は、モデルのドキュメントを作成する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-156">This information can be useful for documenting the model.</span></span>  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center Default NN'  
```  
  
 <span data-ttu-id="68dfb-157">結果の例:</span><span class="sxs-lookup"><span data-stu-id="68dfb-157">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68dfb-158">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="68dfb-158">MODEL_NAME</span></span>|<span data-ttu-id="68dfb-159">Call Center Default NN</span><span class="sxs-lookup"><span data-stu-id="68dfb-159">Call Center Default NN</span></span>|  
|<span data-ttu-id="68dfb-160">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="68dfb-160">DATE_CREATED</span></span>|<span data-ttu-id="68dfb-161">1/10/2008 5:07:38 PM</span><span class="sxs-lookup"><span data-stu-id="68dfb-161">1/10/2008 5:07:38 PM</span></span>|  
|<span data-ttu-id="68dfb-162">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="68dfb-162">LAST_PROCESSED</span></span>|<span data-ttu-id="68dfb-163">1/10/2008 5:24:02 PM</span><span class="sxs-lookup"><span data-stu-id="68dfb-163">1/10/2008 5:24:02 PM</span></span>|  
|<span data-ttu-id="68dfb-164">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="68dfb-164">PREDICTION_ENTITY</span></span>|<span data-ttu-id="68dfb-165">Average Time Per Issue,</span><span class="sxs-lookup"><span data-stu-id="68dfb-165">Average Time Per Issue,</span></span><br /><br /> <span data-ttu-id="68dfb-166">Grade Of Service,</span><span class="sxs-lookup"><span data-stu-id="68dfb-166">Grade Of Service,</span></span><br /><br /> <span data-ttu-id="68dfb-167">Number Of Orders</span><span class="sxs-lookup"><span data-stu-id="68dfb-167">Number Of Orders</span></span>|  
|<span data-ttu-id="68dfb-168">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="68dfb-168">MINING_PARAMETERS</span></span>|<span data-ttu-id="68dfb-169">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=0,</span><span class="sxs-lookup"><span data-stu-id="68dfb-169">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=0,</span></span><br /><br /> <span data-ttu-id="68dfb-170">MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="68dfb-170">MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="68dfb-171">MAXIMUM_STATES=100, SAMPLE_SIZE=10000, HIDDEN_NODE_RATIO=4</span><span class="sxs-lookup"><span data-stu-id="68dfb-171">MAXIMUM_STATES=100, SAMPLE_SIZE=10000, HIDDEN_NODE_RATIO=4</span></span>|  
  
###  <a name="sample-query-3-retrieving-the-input-attributes-for-the-model"></a><a name="bkmk_Query3"></a><span data-ttu-id="68dfb-172">サンプルクエリ 3: モデルの入力属性を取得する</span><span class="sxs-lookup"><span data-stu-id="68dfb-172">Sample Query 3: Retrieving the Input Attributes for the Model</span></span>  
 <span data-ttu-id="68dfb-173">モデルの作成に使用された入力属性と値のペアを取得するには、入力層 (NODE_TYPE = 18) の子ノード (NODE_TYPE = 20) に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-173">You can retrieve the input attribute-value pairs that were used to create the model by querying the child nodes (NODE_TYPE = 20) of the input layer (NODE_TYPE = 18).</span></span> <span data-ttu-id="68dfb-174">次のクエリは、ノード記述から入力属性の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-174">The following query returns a list of input attributes from the node descriptions.</span></span>  
  
```  
SELECT NODE_DESCRIPTION  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 <span data-ttu-id="68dfb-175">結果の例:</span><span class="sxs-lookup"><span data-stu-id="68dfb-175">Example results:</span></span>  
  
|<span data-ttu-id="68dfb-176">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="68dfb-176">NODE_DESCRIPTION</span></span>|  
|-----------------------|  
|<span data-ttu-id="68dfb-177">Average Time Per Issue=64.7094100096 - 77.4002099712</span><span class="sxs-lookup"><span data-stu-id="68dfb-177">Average Time Per Issue=64.7094100096 - 77.4002099712</span></span>|  
|<span data-ttu-id="68dfb-178">Day Of Week=Fri.</span><span class="sxs-lookup"><span data-stu-id="68dfb-178">Day Of Week=Fri.</span></span>|  
|<span data-ttu-id="68dfb-179">Level 1 Operators</span><span class="sxs-lookup"><span data-stu-id="68dfb-179">Level 1 Operators</span></span>|  
  
 <span data-ttu-id="68dfb-180">ここでは結果からいくつかの代表的な行のみを示していますが、</span><span class="sxs-lookup"><span data-stu-id="68dfb-180">Only a few representative rows from the results are shown here.</span></span> <span data-ttu-id="68dfb-181">NODE_DESCRIPTION で提供される情報が入力属性のデータ型によって少しずつ異なることがわかります。</span><span class="sxs-lookup"><span data-stu-id="68dfb-181">However, you can see that the NODE_DESCRIPTION provides slightly different information depending on the data type of the input attribute.</span></span>  
  
-   <span data-ttu-id="68dfb-182">属性が不連続値または分離された値の場合は、属性とその値または分離された範囲が返されます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-182">If the attribute is a discrete or discretized value, the attribute and either its value or its discretized range are returned.</span></span>  
  
-   <span data-ttu-id="68dfb-183">属性が連続する数値データ型の場合は、NODE_DESCRIPTION に属性名のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-183">If the attribute is a continuous numeric data type, the NODE_DESCRIPTION contains only the attribute name.</span></span> <span data-ttu-id="68dfb-184">ただし、入れ子になった NODE_DISTRIBUTION テーブルを取得して平均を求めたり、NODE_RULE を返して数値範囲の最小値と最大値を取得したりすることは可能です。</span><span class="sxs-lookup"><span data-stu-id="68dfb-184">However, you can retrieve the nested NODE_DISTRIBUTION table to obtain the mean, or return the NODE_RULE to obtain the minimum and maximum values of the numeric range.</span></span>  
  
 <span data-ttu-id="68dfb-185">次のクエリは、入れ子になった NODE_DISTRIBUTION テーブルに対してクエリを実行して、属性とその値を別々の列に返す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-185">The following query shows how to query the nested NODE_DISTRIBUTION table to return the attributes in one column, and their values in another column.</span></span> <span data-ttu-id="68dfb-186">連続属性の場合、属性の値は平均で表されます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-186">For continuous attributes, the value of the attribute is represented by its mean.</span></span>  
  
```  
SELECT FLATTENED   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE  
FROM NODE_DISTRIBUTION) as t  
FROM [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 21  
```  
  
 <span data-ttu-id="68dfb-187">結果の例:</span><span class="sxs-lookup"><span data-stu-id="68dfb-187">Example results:</span></span>  
  
|<span data-ttu-id="68dfb-188">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="68dfb-188">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="68dfb-189">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="68dfb-189">t.ATTRIBUTE_VALUE</span></span>|  
|-----------------------|------------------------|  
|<span data-ttu-id="68dfb-190">案件あたりの平均時間</span><span class="sxs-lookup"><span data-stu-id="68dfb-190">Average Time Per Issue</span></span>|<span data-ttu-id="68dfb-191">64.7094100096 - 77.4002099712</span><span class="sxs-lookup"><span data-stu-id="68dfb-191">64.7094100096 - 77.4002099712</span></span>|  
|<span data-ttu-id="68dfb-192">Day Of Week</span><span class="sxs-lookup"><span data-stu-id="68dfb-192">Day Of Week</span></span>|<span data-ttu-id="68dfb-193">Fri.</span><span class="sxs-lookup"><span data-stu-id="68dfb-193">Fri.</span></span>|  
|<span data-ttu-id="68dfb-194">Level 1 Operators</span><span class="sxs-lookup"><span data-stu-id="68dfb-194">Level 1 Operators</span></span>|<span data-ttu-id="68dfb-195">3.2962962962963</span><span class="sxs-lookup"><span data-stu-id="68dfb-195">3.2962962962963</span></span>|  
  
 <span data-ttu-id="68dfb-196">範囲の最小値と最大値は NODE_RULE 列に格納され、次の例のように XML フラグメントとして表現されます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-196">The minimum and maximum range values are stored in the NODE_RULE column, and are represented as an XML fragment, as shown in the following example:</span></span>  
  
```  
<NormContinuous field="Level 1 Operators">    
  <LinearNorm orig="2.83967303681711" norm="-1" />    
  <LinearNorm orig="3.75291955577548" norm="1" />    
</NormContinuous>    
```  
  
###  <a name="sample-query-4-retrieving-weights-from-the-hidden-layer"></a><a name="bkmk_Query4"></a> <span data-ttu-id="68dfb-197">サンプル クエリ 4: 非表示層から重みを取得する</span><span class="sxs-lookup"><span data-stu-id="68dfb-197">Sample Query 4: Retrieving Weights from the Hidden Layer</span></span>  
 <span data-ttu-id="68dfb-198">ニューラル ネットワーク モデルのモデル コンテンツは、ネットワーク内の任意のノードに関する詳細を取得しやすい構造になっています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-198">The model content of a neural network model is structured in a way that makes it easy to retrieve details about any node in the network.</span></span> <span data-ttu-id="68dfb-199">さらに、ノードの ID 番号の情報からも、ノードの種類間のリレーションシップを識別できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-199">Moreover, the ID numbers of the nodes provide information that helps you identify relationships among the node types.</span></span>  
  
 <span data-ttu-id="68dfb-200">次のクエリは、非表示層の特定のノードに格納された係数を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-200">The following query demonstrates how to retrieve the coefficients that are stored under a particular node of the hidden layer.</span></span> <span data-ttu-id="68dfb-201">非表示層は、メタデータのみを含むオーガナイザー ノード (NODE_TYPE = 19)、および属性と値のさまざまな組み合わせの係数を含む複数の子ノード (NODE_TYPE = 22) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-201">The hidden layer consists of an organizer node (NODE_TYPE = 19), which contains only metadata, and multiple child nodes (NODE_TYPE = 22), which contain the coefficients for the various combinations of attributes and values.</span></span> <span data-ttu-id="68dfb-202">このクエリは、係数のノードだけを返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-202">This query returns only the coefficient nodes.</span></span>  
  
```  
SELECT FLATTENED TOP 1 NODE_UNIQUE_NAME,   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM  [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 22  
AND [PARENT_UNIQUE_NAME] = '40000000200000000' FROM [Call Center Default NN].CONTENT  
```  
  
 <span data-ttu-id="68dfb-203">結果の例:</span><span class="sxs-lookup"><span data-stu-id="68dfb-203">Example results:</span></span>  
  
|<span data-ttu-id="68dfb-204">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="68dfb-204">NODE_UNIQUE_NAME</span></span>|<span data-ttu-id="68dfb-205">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="68dfb-205">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="68dfb-206">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="68dfb-206">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="68dfb-207">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="68dfb-207">t.VALUETYPE</span></span>|  
|------------------------|-----------------------|------------------------|-----------------|  
|<span data-ttu-id="68dfb-208">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="68dfb-208">70000000200000000</span></span>|<span data-ttu-id="68dfb-209">6000000000000000a</span><span class="sxs-lookup"><span data-stu-id="68dfb-209">6000000000000000a</span></span>|<span data-ttu-id="68dfb-210">-0.178616518</span><span class="sxs-lookup"><span data-stu-id="68dfb-210">-0.178616518</span></span>|<span data-ttu-id="68dfb-211">7</span><span class="sxs-lookup"><span data-stu-id="68dfb-211">7</span></span>|  
|<span data-ttu-id="68dfb-212">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="68dfb-212">70000000200000000</span></span>|<span data-ttu-id="68dfb-213">6000000000000000b</span><span class="sxs-lookup"><span data-stu-id="68dfb-213">6000000000000000b</span></span>|<span data-ttu-id="68dfb-214">-0.267561918</span><span class="sxs-lookup"><span data-stu-id="68dfb-214">-0.267561918</span></span>|<span data-ttu-id="68dfb-215">7</span><span class="sxs-lookup"><span data-stu-id="68dfb-215">7</span></span>|  
|<span data-ttu-id="68dfb-216">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="68dfb-216">70000000200000000</span></span>|<span data-ttu-id="68dfb-217">6000000000000000c</span><span class="sxs-lookup"><span data-stu-id="68dfb-217">6000000000000000c</span></span>|<span data-ttu-id="68dfb-218">0.11069497</span><span class="sxs-lookup"><span data-stu-id="68dfb-218">0.11069497</span></span>|<span data-ttu-id="68dfb-219">7</span><span class="sxs-lookup"><span data-stu-id="68dfb-219">7</span></span>|  
|<span data-ttu-id="68dfb-220">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="68dfb-220">70000000200000000</span></span>|<span data-ttu-id="68dfb-221">6000000000000000d</span><span class="sxs-lookup"><span data-stu-id="68dfb-221">6000000000000000d</span></span>|<span data-ttu-id="68dfb-222">0.123757712</span><span class="sxs-lookup"><span data-stu-id="68dfb-222">0.123757712</span></span>|<span data-ttu-id="68dfb-223">7</span><span class="sxs-lookup"><span data-stu-id="68dfb-223">7</span></span>|  
|<span data-ttu-id="68dfb-224">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="68dfb-224">70000000200000000</span></span>|<span data-ttu-id="68dfb-225">6000000000000000e</span><span class="sxs-lookup"><span data-stu-id="68dfb-225">6000000000000000e</span></span>|<span data-ttu-id="68dfb-226">0.294565343</span><span class="sxs-lookup"><span data-stu-id="68dfb-226">0.294565343</span></span>|<span data-ttu-id="68dfb-227">7</span><span class="sxs-lookup"><span data-stu-id="68dfb-227">7</span></span>|  
|<span data-ttu-id="68dfb-228">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="68dfb-228">70000000200000000</span></span>|<span data-ttu-id="68dfb-229">6000000000000000f</span><span class="sxs-lookup"><span data-stu-id="68dfb-229">6000000000000000f</span></span>|<span data-ttu-id="68dfb-230">0.22245318</span><span class="sxs-lookup"><span data-stu-id="68dfb-230">0.22245318</span></span>|<span data-ttu-id="68dfb-231">7</span><span class="sxs-lookup"><span data-stu-id="68dfb-231">7</span></span>|  
|<span data-ttu-id="68dfb-232">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="68dfb-232">70000000200000000</span></span>||<span data-ttu-id="68dfb-233">0.188805045</span><span class="sxs-lookup"><span data-stu-id="68dfb-233">0.188805045</span></span>|<span data-ttu-id="68dfb-234">7</span><span class="sxs-lookup"><span data-stu-id="68dfb-234">7</span></span>|  
  
 <span data-ttu-id="68dfb-235">ここに示した結果の一部は、ニューラル ネットワーク モデルのコンテンツで非表示ノードが入力ノードにどのように関係しているかを示しています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-235">The partial results shown here demonstrate how the neural network model content relates the hidden node to the input nodes.</span></span>  
  
-   <span data-ttu-id="68dfb-236">非表示層のノードの一意な名前は、常に 70000000 で始まります。</span><span class="sxs-lookup"><span data-stu-id="68dfb-236">The unique names of nodes in the hidden layer always begin with 70000000.</span></span>  
  
-   <span data-ttu-id="68dfb-237">入力層のノードの一意な名前は、常に 60000000 で始まります。</span><span class="sxs-lookup"><span data-stu-id="68dfb-237">The unique names of nodes in the input layer always begin with 60000000.</span></span>  
  
 <span data-ttu-id="68dfb-238">したがって、これらの結果から、ID 70000000200000000 で表されるノードには 6 つの異なる係数 (VALUETYPE = 7) が渡されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="68dfb-238">Thus, these results tell you that the node denoted by the ID 70000000200000000 had six different coefficients (VALUETYPE = 7) passed to it.</span></span> <span data-ttu-id="68dfb-239">係数の値は、ATTRIBUTE_VALUE 列に含まれています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-239">The values of the coefficients are in the ATTRIBUTE_VALUE column.</span></span> <span data-ttu-id="68dfb-240">どの入力属性の係数かは、ATTRIBUTE_NAME 列のノード ID を使用して判断できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-240">You can determine exactly which input attribute the coefficient is for by using the node ID in the ATTRIBUTE_NAME column.</span></span> <span data-ttu-id="68dfb-241">たとえば、ノード ID 6000000000000000a は、入力属性と値を参照します。 `Day of Week = 'Tue.'` ノード ID を使用してクエリを作成したり、 [Microsoft 汎用コンテンツ ツリー ビューアー](../microsoft-generic-content-tree-viewer-data-mining.md)を使用してノードを参照したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-241">For example, the node ID 6000000000000000a refers to input attribute and value, `Day of Week = 'Tue.'` You can use the node ID to create a query, or you can browse to the node by using the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
 <span data-ttu-id="68dfb-242">同様に、出力層 (NODE_TYPE = 23) のノードの NODE_DISTRIBUTION テーブルに対してクエリを実行すると、各出力値の係数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-242">Similarly, if you query the NODE_DISTRIBUTION table of the nodes in the output layer (NODE_TYPE = 23), you can see the coefficients for each output value.</span></span> <span data-ttu-id="68dfb-243">ただし、出力層では、ポインターが非表示層のノードを参照します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-243">However, in the output layer, the pointers refer back to the nodes of the hidden layer.</span></span> <span data-ttu-id="68dfb-244">詳細については、「 [ニューラル ネットワーク モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)というマイニング モデルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-244">For more information, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="using-a-neural-network-model-to-make-predictions"></a><span data-ttu-id="68dfb-245">ニューラル ネットワーク モデルを使用した予測の作成</span><span class="sxs-lookup"><span data-stu-id="68dfb-245">Using a Neural Network Model to Make Predictions</span></span>  
 <span data-ttu-id="68dfb-246">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムでは、分類と回帰の両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-246">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm supports both classification and regression.</span></span> <span data-ttu-id="68dfb-247">これらのモデルで予測関数を使用して、新しいデータを提供したり、単一予測またはバッチ予測を作成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-247">You can use prediction functions with these models to provide new data and create either singleton or batch predictions.</span></span>  
  
###  <a name="sample-query-5-creating-a-singleton-prediction"></a><a name="bkmk_Query5"></a><span data-ttu-id="68dfb-248">サンプルクエリ 5: 単一予測を作成する</span><span class="sxs-lookup"><span data-stu-id="68dfb-248">Sample Query 5: Creating a Singleton Prediction</span></span>  
 <span data-ttu-id="68dfb-249">ニューラル ネットワーク モデルに対する予測クエリを作成する最も簡単な方法は、予測クエリ ビルダーを使用することです。このビルダーは、 **および** のデータ マイニング デザイナーの [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [マイニング予測] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで使用できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-249">The easiest way to build a prediction query on a neural network model is to use the Prediction Query Builder, available on the **Mining Prediction** tab of Data Mining Designer in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="68dfb-250">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク ビューアーでモデルを参照し、関心のある属性をフィルター選択して傾向を表示します。その後、 **[マイニング予測]** タブに切り替えて、クエリを作成し、それらの傾向について新しい値を予測できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-250">You can browse the model in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer to filter attributes of interest and view trends, and then switch to the **Mining Prediction** tab to create a query and predict new values for those trends.</span></span>  
  
 <span data-ttu-id="68dfb-251">たとえば、コール センター モデルを参照して、注文数とその他の属性の相関関係を表示できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-251">For example, you can browse the call center model to view correlations between the order volumes and other attributes.</span></span> <span data-ttu-id="68dfb-252">これを行うには、ビューアーでモデルを開き、[**入力**] でを選択し **\<All>** ます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-252">To do this, open the model in the viewer, and for **Input**, select **\<All>**.</span></span>  <span data-ttu-id="68dfb-253">次に、 **[出力]** で **[注文数]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-253">Next, for **Output**, select **Number of Orders**.</span></span> <span data-ttu-id="68dfb-254">**[値 1]** で最も注文が多い範囲を選択し、 **[値 2]** で最も注文が少ない範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-254">For **Value 1**, select the range that represents the most orders, and for **Value 2**, select the range that represents the fewest orders.</span></span> <span data-ttu-id="68dfb-255">これにより、モデルで注文数と相関関係があるすべての属性がひとめでわかります。</span><span class="sxs-lookup"><span data-stu-id="68dfb-255">You can then see at a glance all the attributes that the model correlates with order volume.</span></span>  
  
 <span data-ttu-id="68dfb-256">ビューアーで結果を参照すると、特定の曜日に注文数が少ないこと、およびオペレーターの増員と売上の向上に相関関係がありそうなことがわかります。</span><span class="sxs-lookup"><span data-stu-id="68dfb-256">By browsing the results in the viewer, you find that certain days of the week have low order volumes, and that an increase in the number of operators seems to be correlated with higher sales.</span></span> <span data-ttu-id="68dfb-257">この場合、モデルに対する予測クエリを使用して "what if" 仮説を試し、注文数が少ない曜日にレベル 2 のオペレーターを増員すると注文が増加するかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-257">You could then use a prediction query on the model to test a "what if" hypothesis and ask if increasing the number of level 2 operators on a low-volume day would increase orders.</span></span> <span data-ttu-id="68dfb-258">これを行うには、次のようなクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-258">To do this, create a query such as the following:</span></span>  
  
```  
SELECT Predict([Call Center Default NN].[Number of Orders]) AS [Predicted Orders],  
PredictProbability([Call Center Default NN].[Number of Orders]) AS [Probability]  
FROM [Call Center Default NN]  
NATURAL PREDICTION JOIN   
(SELECT 'Tue.' AS [Day of Week],  
13 AS [Level 2 Operators]) AS t  
```  
  
 <span data-ttu-id="68dfb-259">結果の例:</span><span class="sxs-lookup"><span data-stu-id="68dfb-259">Example results:</span></span>  
  
|<span data-ttu-id="68dfb-260">Predicted Orders</span><span class="sxs-lookup"><span data-stu-id="68dfb-260">Predicted Orders</span></span>|<span data-ttu-id="68dfb-261">確率</span><span class="sxs-lookup"><span data-stu-id="68dfb-261">Probability</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="68dfb-262">364</span><span class="sxs-lookup"><span data-stu-id="68dfb-262">364</span></span>|<span data-ttu-id="68dfb-263">0.9532...</span><span class="sxs-lookup"><span data-stu-id="68dfb-263">0.9532...</span></span>|  
  
 <span data-ttu-id="68dfb-264">この予測された売上高は火曜日の現在の売上高の範囲より高くなり、予測の確率は非常に高い値を示しています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-264">The predicted sales volume is higher than the current range of sales for Tuesday, and the probability of the prediction is very high.</span></span> <span data-ttu-id="68dfb-265">ただし、バッチ処理を使用して複数の予測を作成し、モデルに対してさまざまな仮説を試す必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="68dfb-265">However, you might want to create multiple predictions by using a batch process to test a variety of hypotheses on the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68dfb-266">Excel 2007 用データ マイニング アドインで提供されるロジスティック回帰ウィザードを使用すると、サービス グレードを特定のシフトのターゲット レベルまで引き上げるにはレベル 2 のオペレーターが何人必要になるかなど、複雑な質問に対する回答を簡単に求めることができます。</span><span class="sxs-lookup"><span data-stu-id="68dfb-266">The Data Mining Add-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be needed to improve service grade to a target level for a specific shift.</span></span> <span data-ttu-id="68dfb-267">データ マイニング アドインは、無料でダウンロードできます。これらのアドインには、ニューラル ネットワークまたはロジスティック回帰アルゴリズムに基づいたウィザードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-267">The data mining add-ins are a free download, and include wizards that are based on the neural network and/or logistic regression algorithms.</span></span> <span data-ttu-id="68dfb-268">詳細については、「 [Office 2007 用データ マイニング アドイン](https://go.microsoft.com/fwlink/?LinkID=117790) 」の Web サイトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="68dfb-268">For more information, see the [Data Mining Add-ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790) Web site.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="68dfb-269">予測関数の一覧</span><span class="sxs-lookup"><span data-stu-id="68dfb-269">List of Prediction Functions</span></span>  
 <span data-ttu-id="68dfb-270">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-270">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="68dfb-271">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムでは、このアルゴリズムに固有の予測関数はありませんが、次の表のような関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="68dfb-271">There are no prediction functions that are specific to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm; however, the algorithm supports the functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68dfb-272">予測関数</span><span class="sxs-lookup"><span data-stu-id="68dfb-272">Prediction Function</span></span>|<span data-ttu-id="68dfb-273">使用方法</span><span class="sxs-lookup"><span data-stu-id="68dfb-273">Usage</span></span>|  
|[<span data-ttu-id="68dfb-274">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="68dfb-274">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="68dfb-275">あるノードがニューラル ネットワーク グラフ内の別のノードの子であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-275">Determines whether one node is a child of another node in the neural network graph.</span></span>|  
|[<span data-ttu-id="68dfb-276">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="68dfb-276">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="68dfb-277">重み付け確率を返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-277">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="68dfb-278">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="68dfb-278">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="68dfb-279">現在の予測値に関連する値のテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-279">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="68dfb-280">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="68dfb-280">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="68dfb-281">予測値の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-281">Returns variance for the predicted value.</span></span>|  
|[<span data-ttu-id="68dfb-282">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="68dfb-282">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="68dfb-283">予測値の確率を返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-283">Returns probability  for the predicted value.</span></span>|  
|[<span data-ttu-id="68dfb-284">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="68dfb-284">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="68dfb-285">予測された値の標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-285">Returns the standard deviance for the predicted value.</span></span>|  
|[<span data-ttu-id="68dfb-286">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="68dfb-286">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="68dfb-287">ニューラル ネットワーク モデルとロジスティック回帰モデルの場合、モデル全体のトレーニング セットのサイズを表す 1 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="68dfb-287">For neural network and logistic regression models, returns a single value that represents the size of the training set for the entire model.</span></span>|  
  
 <span data-ttu-id="68dfb-288">特定の関数の構文については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68dfb-288">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dfb-289">参照</span><span class="sxs-lookup"><span data-stu-id="68dfb-289">See Also</span></span>  
 <span data-ttu-id="68dfb-290">[Microsoft ニューラルネットワークアルゴリズム](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="68dfb-290">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="68dfb-291">[Microsoft ニューラルネットワークアルゴリズムテクニカルリファレンス](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="68dfb-291">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="68dfb-292">[ニューラルネットワークモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="68dfb-292">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="68dfb-293">レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="68dfb-293">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
