---
title: アソシエーションモデルのクエリ例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- rules [Data Mining]
- association rules
- content queries [DMX]
ms.assetid: 68b39f5c-c439-44ac-8046-6f2d36649059
author: minewiskan
ms.author: owend
ms.openlocfilehash: a19eb2302639c7f13d48a8778969bbeca4fee18d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644711"
---
# <a name="association-model-query-examples"></a><span data-ttu-id="8130e-102">結合モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="8130e-102">Association Model Query Examples</span></span>
  <span data-ttu-id="8130e-103">データ マイニング モデルに対するクエリを作成する際には、コンテンツ クエリを作成することも、予測クエリを作成することもできます。コンテンツ クエリでは、分析の間に検出されたルールやアイテムセットの詳細情報を取得できます。予測クエリでは、データ内で検出されたアソシエーションを使用して予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8130e-103">When you create a query against a data mining model, you can create either a content query, which provides details about the rules and itemsets discovered during analysis, or you can create a prediction query, which uses the associations discovered in the data to make predictions.</span></span> <span data-ttu-id="8130e-104">アソシエーション モデルの場合、予測はルールに基づいて行われるのが一般的で、提案を行うために使用できます。一方、コンテンツ クエリではアイテムセット間の関係を調べるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="8130e-104">For an association model, predictions typically are based on rules, and can be used to make recommendations, whereas queries on content typically explore the relationship among itemsets.</span></span> <span data-ttu-id="8130e-105">モデルに関するメタデータを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="8130e-105">You can also retrieve metadata about the model.</span></span>  
  
 <span data-ttu-id="8130e-106">ここでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムに基づくモデルに対してこれらの種類のクエリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8130e-106">This section explains how to create these kinds of queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span>  
  
 <span data-ttu-id="8130e-107">**コンテンツ クエリ**</span><span class="sxs-lookup"><span data-stu-id="8130e-107">**Content Queries**</span></span>  
  
 [<span data-ttu-id="8130e-108">DMX を使用してモデル メタデータ データを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-108">Getting model metadata data by using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="8130e-109">スキーマ行セットからメタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-109">Getting metadata from the schema rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="8130e-110">モデルの元のパラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-110">Retrieving the original parameters for the model</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="8130e-111">アイテムセットと製品のリストを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-111">Retrieving a list of itemsets and products</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="8130e-112">上位 10 個のアイテムセットを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-112">Returning the top 10 itemsets</span></span>](#bkmk_Query5)  
  
 <span data-ttu-id="8130e-113">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="8130e-113">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="8130e-114">関連のあるアイテムを予測する</span><span class="sxs-lookup"><span data-stu-id="8130e-114">Predicting associated items</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="8130e-115">関連するアイテムセットの信頼度を特定する</span><span class="sxs-lookup"><span data-stu-id="8130e-115">Determining confidence for related itemsets</span></span>](#bkmk_Query7)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="8130e-116">モデルに関する情報の入手</span><span class="sxs-lookup"><span data-stu-id="8130e-116">Finding Information about the Model</span></span>  
 <span data-ttu-id="8130e-117">すべてのマイニング モデルでは、アルゴリズムによって学習されたコンテンツが、標準化されたスキーマに従って公開されます。このスキーマを、マイニング モデル スキーマ行セットと呼びます。</span><span class="sxs-lookup"><span data-stu-id="8130e-117">All mining models expose the content learned by the algorithm according to a standardized schema, which is named the mining model schema rowset.</span></span> <span data-ttu-id="8130e-118">マイニング モデル スキーマ行セットに対するクエリは、データ マイニング拡張機能 (DMX) ステートメントか [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ストアド プロシージャを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="8130e-118">You can create queries against the mining model schema rowset either by using Data Mining Extensions (DMX) statements, or by using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stored procedures.</span></span> <span data-ttu-id="8130e-119">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、SQL に似た構文を使用して、スキーマ行セットに対して直接、システム テーブルとしてクエリを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="8130e-119">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can also query the schema rowsets directly as system tables, by using a SQL-like syntax.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="8130e-120">サンプル クエリ 1: DMX を使用してモデル メタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-120">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="8130e-121">次のクエリは、アソシエーション モデル `Association`に関する基本的なメタデータ (モデルの名前、モデルが格納されているデータベース、モデルの子ノードの数など) を返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-121">The following query returns basic metadata about the association model, `Association`, such as the name of the model, the database where the model is stored, and the number of child nodes in the model.</span></span> <span data-ttu-id="8130e-122">このクエリでは、DMX コンテンツ クエリを使用してモデルの親ノードからメタデータを取得しています。</span><span class="sxs-lookup"><span data-stu-id="8130e-122">This query uses a DMX content query to retrieve the metadata from the parent node of the model:</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8130e-123">CHILDREN_CARDINALITY という列名は、MDX の同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="8130e-123">You must enclose the name of the column, CHILDREN_CARDINALITY, in brackets to distinguish it from the MDX reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="8130e-124">結果の例:</span><span class="sxs-lookup"><span data-stu-id="8130e-124">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8130e-125">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8130e-125">MODEL_CATALOG</span></span>|<span data-ttu-id="8130e-126">Association Test</span><span class="sxs-lookup"><span data-stu-id="8130e-126">Association Test</span></span>|  
|<span data-ttu-id="8130e-127">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="8130e-127">MODEL_NAME</span></span>|<span data-ttu-id="8130e-128">関連付け</span><span class="sxs-lookup"><span data-stu-id="8130e-128">Association</span></span>|  
|<span data-ttu-id="8130e-129">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8130e-129">NODE_CAPTION</span></span>|<span data-ttu-id="8130e-130">Association Rules Model</span><span class="sxs-lookup"><span data-stu-id="8130e-130">Association Rules Model</span></span>|  
|<span data-ttu-id="8130e-131">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8130e-131">NODE_SUPPORT</span></span>|<span data-ttu-id="8130e-132">14879</span><span class="sxs-lookup"><span data-stu-id="8130e-132">14879</span></span>|  
|<span data-ttu-id="8130e-133">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8130e-133">CHILDREN_CARDINALITY</span></span>|<span data-ttu-id="8130e-134">942</span><span class="sxs-lookup"><span data-stu-id="8130e-134">942</span></span>|  
|<span data-ttu-id="8130e-135">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8130e-135">NODE_DESCRIPTION</span></span>|<span data-ttu-id="8130e-136">Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523</span><span class="sxs-lookup"><span data-stu-id="8130e-136">Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523</span></span>|  
  
 <span data-ttu-id="8130e-137">アソシエーション モデル内でのこれらの列の意味については、「 [アソシエーション モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-association-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8130e-137">For a definition of what these columns mean in an association model, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="8130e-138">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8130e-138">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-2-getting-additional-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a> <span data-ttu-id="8130e-139">サンプル クエリ 2: スキーマ行セットから追加のメタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-139">Sample Query 2: Getting Additional Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="8130e-140">データ マイニング スキーマ行セットに対してクエリを実行すると、DMX コンテンツ クエリで返されたのと同じ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="8130e-140">By querying the data mining schema rowset, you can find the same information that is returned in a DMX content query.</span></span> <span data-ttu-id="8130e-141">ただし、スキーマ行セットから返される情報にはいくつかの追加の列があります (モデルが最後に処理された日、マイニング構造、予測可能な属性として使用されている列の名前など)。</span><span class="sxs-lookup"><span data-stu-id="8130e-141">However, the schema rowset provides some additional columns, such as the date the model was last processed, the mining structure, and the name of the column used as the predictable attribute.</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, SERVICE_NAME, PREDICTION_ENTITY,   
MINING_STRUCTURE, LAST_PROCESSED  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 <span data-ttu-id="8130e-142">結果の例:</span><span class="sxs-lookup"><span data-stu-id="8130e-142">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8130e-143">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8130e-143">MODEL_CATALOG</span></span>|<span data-ttu-id="8130e-144">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="8130e-144">Adventure Works DW Multidimensional 2012</span></span>|  
|<span data-ttu-id="8130e-145">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="8130e-145">MODEL_NAME</span></span>|<span data-ttu-id="8130e-146">関連付け</span><span class="sxs-lookup"><span data-stu-id="8130e-146">Association</span></span>|  
|<span data-ttu-id="8130e-147">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="8130e-147">SERVICE_NAME</span></span>|<span data-ttu-id="8130e-148">Association Rules Model</span><span class="sxs-lookup"><span data-stu-id="8130e-148">Association Rules Model</span></span>|  
|<span data-ttu-id="8130e-149">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="8130e-149">PREDICTION_ENTITY</span></span>|<span data-ttu-id="8130e-150">v Assoc Seq Line Items</span><span class="sxs-lookup"><span data-stu-id="8130e-150">v Assoc Seq Line Items</span></span>|  
|<span data-ttu-id="8130e-151">MINING_STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="8130e-151">MINING_STRUCTURE</span></span>|<span data-ttu-id="8130e-152">関連付け</span><span class="sxs-lookup"><span data-stu-id="8130e-152">Association</span></span>|  
|<span data-ttu-id="8130e-153">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="8130e-153">LAST_PROCESSED</span></span>|<span data-ttu-id="8130e-154">9/29/2007 10:21:24 PM</span><span class="sxs-lookup"><span data-stu-id="8130e-154">9/29/2007 10:21:24 PM</span></span>|  
  
 [<span data-ttu-id="8130e-155">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8130e-155">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-3-retrieving-original-parameters-for-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="8130e-156">サンプル クエリ 3: モデルの元のパラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-156">Sample Query 3: Retrieving Original Parameters for Model</span></span>  
 <span data-ttu-id="8130e-157">次のクエリは、モデルの作成時に使用されたパラメーター設定の詳細を含む 1 つの列を返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-157">The following query returns a single column that contains details about the parameter settings that were used when the model was created.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 <span data-ttu-id="8130e-158">結果の例:</span><span class="sxs-lookup"><span data-stu-id="8130e-158">Example results:</span></span>  
  
 <span data-ttu-id="8130e-159">MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4</span><span class="sxs-lookup"><span data-stu-id="8130e-159">MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4</span></span>  
  
 [<span data-ttu-id="8130e-160">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8130e-160">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="finding-information-about-rules-and-itemsets"></a><span data-ttu-id="8130e-161">ルールとアイテムセットに関する情報の入手</span><span class="sxs-lookup"><span data-stu-id="8130e-161">Finding Information about Rules and Itemsets</span></span>  
 <span data-ttu-id="8130e-162">アソシエーション モデルの用途としては、頻度の高いアイテムセットに関する情報の検出と、特定のルールやアイテムセットに関する詳細の抽出の 2 つが一般的です。</span><span class="sxs-lookup"><span data-stu-id="8130e-162">There are two common uses of an association model: to discover information about frequent itemsets, and to extract details about particular rules and itemsets.</span></span> <span data-ttu-id="8130e-163">たとえば、スコアによって特に興味深いとされたルールのリストを抽出したり、最も一般的なアイテムセットのリストを作成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8130e-163">For example, you might want to extract a list of rules that were scored as being especially interesting, or create a list of the most common itemsets.</span></span> <span data-ttu-id="8130e-164">このような情報を取得するには、DMX コンテンツ クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="8130e-164">You retrieve such information by using a DMX content query.</span></span> <span data-ttu-id="8130e-165">**Microsoft アソシエーション ビューアー**を使用してこの情報を参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="8130e-165">You can also browse this information by using the **Microsoft Association Viewer**.</span></span>  
  
###  <a name="sample-query-4-retrieving-list-of-itemsets-and-products"></a><a name="bkmk_Query4"></a> <span data-ttu-id="8130e-166">サンプル クエリ 4: アイテムセットと製品のリストを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-166">Sample Query 4: Retrieving List of Itemsets and Products</span></span>  
 <span data-ttu-id="8130e-167">次のクエリは、すべてのアイテムセットを、各アイテムセットに含まれる製品のリストから成る入れ子になったテーブルと共に取得します。</span><span class="sxs-lookup"><span data-stu-id="8130e-167">The following query retrieves all of the itemsets, together with a nested table that lists the products included in each itemset.</span></span> <span data-ttu-id="8130e-168">NODE_NAME 列にはモデル内のアイテムセットの一意の ID が、NODE_CAPTION 列にはアイテムの説明テキストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8130e-168">The NODE_NAME column contains the unique ID of the itemset within the model, whereas the NODE_CAPTION provides a text description of the items.</span></span> <span data-ttu-id="8130e-169">この例では、入れ子になったテーブルがフラット化されているため、アイテムセットに 2 つの製品が含まれている場合は結果に 2 つの行が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8130e-169">In this example, the nested table is flattened, so that an itemset that contains two products generates two rows in the results.</span></span> <span data-ttu-id="8130e-170">使用しているクライアントが階層データをサポートしている場合は FLATTENED キーワードを省略できます。</span><span class="sxs-lookup"><span data-stu-id="8130e-170">You can omit the FLATTENED keyword if your client supports hierarchical data.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
NODE_PROBABILITY, NODE_SUPPORT,  
(SELECT ATTRIBUTE_NAME FROM NODE_DISTRIBUTION) as PurchasedProducts  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="8130e-171">結果の例:</span><span class="sxs-lookup"><span data-stu-id="8130e-171">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8130e-172">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="8130e-172">NODE_NAME</span></span>|<span data-ttu-id="8130e-173">37</span><span class="sxs-lookup"><span data-stu-id="8130e-173">37</span></span>|  
|<span data-ttu-id="8130e-174">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8130e-174">NODE_CAPTION</span></span>|<span data-ttu-id="8130e-175">Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="8130e-175">Sport-100 = Existing</span></span>|  
|<span data-ttu-id="8130e-176">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8130e-176">NODE_PROBABILITY</span></span>|<span data-ttu-id="8130e-177">0.291283016331743</span><span class="sxs-lookup"><span data-stu-id="8130e-177">0.291283016331743</span></span>|  
|<span data-ttu-id="8130e-178">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8130e-178">NODE_SUPPORT</span></span>|<span data-ttu-id="8130e-179">4334</span><span class="sxs-lookup"><span data-stu-id="8130e-179">4334</span></span>|  
|<span data-ttu-id="8130e-180">PURCHASEDPRODUCTS.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="8130e-180">PURCHASEDPRODUCTS.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="8130e-181">v Assoc Seq Line Items(Sport-100)</span><span class="sxs-lookup"><span data-stu-id="8130e-181">v Assoc Seq Line Items(Sport-100)</span></span>|  
  
 [<span data-ttu-id="8130e-182">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8130e-182">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-5-returning-top-10-itemsets"></a><a name="bkmk_Query5"></a> <span data-ttu-id="8130e-183">サンプル クエリ 5: 上位 10 個のアイテムセットを取得する</span><span class="sxs-lookup"><span data-stu-id="8130e-183">Sample Query 5: Returning Top 10 Itemsets</span></span>  
 <span data-ttu-id="8130e-184">この例は、DMX に既定で用意されているグループ化と順序付けの関数の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8130e-184">This example demonstrates how to use some of the grouping and ordering functions that DMX provides by default.</span></span> <span data-ttu-id="8130e-185">このクエリでは、各ノードのサポートで順序付けした場合の上位 10 個のアイテムセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="8130e-185">The query returns the top 10 itemsets when ordered by the support for each node.</span></span> <span data-ttu-id="8130e-186">Transact-SQL の場合のように結果を明示的にグループ化する必要はなく、各クエリで集計関数を 1 つ使用するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="8130e-186">Note that you do not need to explicitly group the results, as you would in Transact-SQL; however, you can use only one aggregate function in each query.</span></span>  
  
```  
SELECT TOP 10 (NODE_SUPPORT),NODE_NAME, NODE_CAPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="8130e-187">結果の例:</span><span class="sxs-lookup"><span data-stu-id="8130e-187">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8130e-188">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8130e-188">NODE_SUPPORT</span></span>|<span data-ttu-id="8130e-189">4334</span><span class="sxs-lookup"><span data-stu-id="8130e-189">4334</span></span>|  
|<span data-ttu-id="8130e-190">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="8130e-190">NODE_NAME</span></span>|<span data-ttu-id="8130e-191">37</span><span class="sxs-lookup"><span data-stu-id="8130e-191">37</span></span>|  
|<span data-ttu-id="8130e-192">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8130e-192">NODE_CAPTION</span></span>|<span data-ttu-id="8130e-193">Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="8130e-193">Sport-100 = Existing</span></span>|  
  
 [<span data-ttu-id="8130e-194">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8130e-194">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a><span data-ttu-id="8130e-195">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="8130e-195">Making Predictions using the Model</span></span>  
 <span data-ttu-id="8130e-196">アソシエーション ルール モデルは、アイテムセットで検出された相関関係に基づく提案を生成するためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="8130e-196">An association rules model is often used to generate recommendations, which are based on correlations discovered in the itemsets.</span></span> <span data-ttu-id="8130e-197">したがって、アソシエーション ルール モデルに基づく予測クエリを作成する際には、そのモデルのルールを使用して新しいデータに基づく推測を行うのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="8130e-197">Therefore, when you create a prediction query based on an association rules model, you are typically using the rules in the model to make guesses based on new data.</span></span>  <span data-ttu-id="8130e-198">[PredictAssociation (DMX)](/sql/dmx/predictassociation-dmx) は提案を返す関数であり、クエリ結果をカスタマイズするために使用できるいくつかの引数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="8130e-198">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) is the function that returns recommendations, and has several arguments that you can use to customize the query results.</span></span>  
  
 <span data-ttu-id="8130e-199">アソシエーション モデルに対するクエリは、そのほか、異なるクロスセル戦略の効果を比較できるようにさまざまなルールやアイテムセットの信頼度を取得するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="8130e-199">Another example of where queries on an association model might be useful is to return the confidence for various rules and itemsets so that you can compare the effectiveness of different cross-sell strategies.</span></span> <span data-ttu-id="8130e-200">以降の例は、このようなクエリの作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8130e-200">The following examples illustrate how to create such queries.</span></span>  
  
###  <a name="sample-query-6-predicting-associated-items"></a><a name="bkmk_Query6"></a> <span data-ttu-id="8130e-201">サンプル クエリ 6: 関連のあるアイテムを予測する</span><span class="sxs-lookup"><span data-stu-id="8130e-201">Sample Query 6: Predicting Associated Items</span></span>  
 <span data-ttu-id="8130e-202">この例では、「[中級者向けデータ マイニング チュートリアル (Analysis Services - データ マイニング)](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」で作成したアソシエーション モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="8130e-202">This example uses the Association model created in the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="8130e-203">この例は、特定の製品を購入した顧客に対してどの製品を提案すればよいかを示す予測クエリの作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8130e-203">It demonstrates how to create a prediction query that tells you what products to recommend to a customer who has purchased a particular product.</span></span> <span data-ttu-id="8130e-204">このクエリのように、`SELECT...UNION` ステートメントでモデルに値を渡す種類のクエリを、単一クエリと呼びます。</span><span class="sxs-lookup"><span data-stu-id="8130e-204">This type of query, where you provide values to the model in a `SELECT...UNION` statement, is called a singleton query.</span></span> <span data-ttu-id="8130e-205">新しい値に対応する予測可能なモデル列は入れ子になったテーブルであるため、1 つの `SELECT` 句を使用して新しい値を入れ子になったテーブル列 (`[Model]`) にマップし、もう 1 つの `SELECT` 句を使用して入れ子になったテーブルの列をケース レベルの列 (`[v Assoc Seq Line Items]`) にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8130e-205">Because the predictable model column that corresponds to the new values is a nested table, you must use one `SELECT` clause to map the new value to the nested table column, `[Model]`, and another `SELECT` clause to map the nested table column to the case-level column, `[v Assoc Seq Line Items]`.</span></span> <span data-ttu-id="8130e-206">キーワード INCLUDE-STATISTICS をクエリに追加すると、提案の確率とサポートも確認できます。</span><span class="sxs-lookup"><span data-stu-id="8130e-206">Adding the keyword INCLUDE-STATISTICS to the query lets you see the probability and support for the recommendations.</span></span>  
  
```  
SELECT PredictAssociation([Association].[vAssocSeqLineItems],INCLUDE_STATISTICS, 3)  
FROM [Association]  
NATURAL PREDICTION JOIN   
(SELECT  
(SELECT 'Classic Vest' as [Model])  
AS [v Assoc Seq Line Items])  
AS t  
```  
  
 <span data-ttu-id="8130e-207">結果の例:</span><span class="sxs-lookup"><span data-stu-id="8130e-207">Example results:</span></span>  
  
|<span data-ttu-id="8130e-208">モデル</span><span class="sxs-lookup"><span data-stu-id="8130e-208">Model</span></span>|<span data-ttu-id="8130e-209">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8130e-209">$SUPPORT</span></span>|<span data-ttu-id="8130e-210">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8130e-210">$PROBABILITY</span></span>|<span data-ttu-id="8130e-211">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8130e-211">$ADJUSTEDPROBABILITY</span></span>|  
|-----------|--------------|------------------|--------------------------|  
|<span data-ttu-id="8130e-212">Sport-100</span><span class="sxs-lookup"><span data-stu-id="8130e-212">Sport-100</span></span>|<span data-ttu-id="8130e-213">4334</span><span class="sxs-lookup"><span data-stu-id="8130e-213">4334</span></span>|<span data-ttu-id="8130e-214">0.291283</span><span class="sxs-lookup"><span data-stu-id="8130e-214">0.291283</span></span>|<span data-ttu-id="8130e-215">0.252696</span><span class="sxs-lookup"><span data-stu-id="8130e-215">0.252696</span></span>|  
|<span data-ttu-id="8130e-216">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="8130e-216">Water Bottle</span></span>|<span data-ttu-id="8130e-217">2866</span><span class="sxs-lookup"><span data-stu-id="8130e-217">2866</span></span>|<span data-ttu-id="8130e-218">0.19262</span><span class="sxs-lookup"><span data-stu-id="8130e-218">0.19262</span></span>|<span data-ttu-id="8130e-219">0.175205</span><span class="sxs-lookup"><span data-stu-id="8130e-219">0.175205</span></span>|  
|<span data-ttu-id="8130e-220">Patch kit</span><span class="sxs-lookup"><span data-stu-id="8130e-220">Patch kit</span></span>|<span data-ttu-id="8130e-221">2113</span><span class="sxs-lookup"><span data-stu-id="8130e-221">2113</span></span>|<span data-ttu-id="8130e-222">0.142012</span><span class="sxs-lookup"><span data-stu-id="8130e-222">0.142012</span></span>|<span data-ttu-id="8130e-223">0.132389</span><span class="sxs-lookup"><span data-stu-id="8130e-223">0.132389</span></span>|  
  
 [<span data-ttu-id="8130e-224">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8130e-224">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-7-determining-confidence-for-related-itemsets"></a><a name="bkmk_Query7"></a> <span data-ttu-id="8130e-225">サンプル クエリ 7: 関連するアイテムセットの信頼度を特定する</span><span class="sxs-lookup"><span data-stu-id="8130e-225">Sample Query 7: Determining Confidence for Related Itemsets</span></span>  
 <span data-ttu-id="8130e-226">提案を生成するにはルールが便利ですが、データセット内のパターンをより深く分析するためにはアイテムセットの方が興味深い対象であると言えます。</span><span class="sxs-lookup"><span data-stu-id="8130e-226">Whereas rules are useful for generating recommendations, itemsets are more interesting for deeper analysis of the patterns in the data set.</span></span> <span data-ttu-id="8130e-227">たとえば、前のサンプル クエリで返された提案が満足できるものでなかった場合、Product A を含む他のアイテムセットを調べると、Product A があらゆる種類の製品と一緒に購入されるような付属品なのか、それとも特定の製品の購入との間に強い相関関係があるのかがわかります。</span><span class="sxs-lookup"><span data-stu-id="8130e-227">For example, if you were not satisfied with the recommendation that are returned by the previous sample query, you could examine other itemsets that contain Product A, to can get a better idea of whether Product A is an accessory that people tend to buy with all kinds of products, or whether A is strongly correlated with purchases of particular products.</span></span> <span data-ttu-id="8130e-228">これらの関係は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ビューアーでアイテムセットにフィルターを適用することによって簡単に調べることができますが、同じ情報をクエリで取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="8130e-228">The easiest way to explore these relationships is by filtering the itemsets in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Viewer; however, you can retrieve the same information with a query.</span></span>  
  
 <span data-ttu-id="8130e-229">次のサンプル クエリは、Water Bottle というアイテムを含むすべてのアイテムセットを、単一のアイテムの Water Bottle も含めて返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-229">The following sample query returns all itemsets that include the Water Bottle item, including the single item Water bottle.</span></span>  
  
```  
SELECT TOP 100 FROM   
(  
SELECT FLATTENED NODE_CAPTION, NODE_SUPPORT,   
(SELECT ATTRIBUTE_NAME from NODE_DISTRIBUTION  
WHERE ATTRIBUTE_NAME = 'v Assoc Seq Line Items(Water Bottle)') as D  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
) AS Items  
WHERE [D.ATTRIBUTE_NAME] <> NULL  
ORDER BY NODE_SUPPORT DESC  
```  
  
 <span data-ttu-id="8130e-230">結果の例:</span><span class="sxs-lookup"><span data-stu-id="8130e-230">Example results:</span></span>  
  
|<span data-ttu-id="8130e-231">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8130e-231">NODE_CAPTION</span></span>|<span data-ttu-id="8130e-232">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8130e-232">NODE_SUPPORT</span></span>|<span data-ttu-id="8130e-233">D.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="8130e-233">D.ATTRIBUTE_NAME</span></span>|  
|-------------------|-------------------|-----------------------|  
|<span data-ttu-id="8130e-234">Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="8130e-234">Water Bottle = Existing</span></span>|<span data-ttu-id="8130e-235">2866</span><span class="sxs-lookup"><span data-stu-id="8130e-235">2866</span></span>|<span data-ttu-id="8130e-236">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="8130e-236">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="8130e-237">Mountain Bottle Cage = Existing, Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="8130e-237">Mountain Bottle Cage = Existing, Water Bottle = Existing</span></span>|<span data-ttu-id="8130e-238">1136</span><span class="sxs-lookup"><span data-stu-id="8130e-238">1136</span></span>|<span data-ttu-id="8130e-239">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="8130e-239">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="8130e-240">Road Bottle Cage = Existing, Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="8130e-240">Road Bottle Cage = Existing, Water Bottle = Existing</span></span>|<span data-ttu-id="8130e-241">1068</span><span class="sxs-lookup"><span data-stu-id="8130e-241">1068</span></span>|<span data-ttu-id="8130e-242">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="8130e-242">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="8130e-243">Water Bottle = Existing, Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="8130e-243">Water Bottle = Existing, Sport-100 = Existing</span></span>|<span data-ttu-id="8130e-244">734</span><span class="sxs-lookup"><span data-stu-id="8130e-244">734</span></span>|<span data-ttu-id="8130e-245">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="8130e-245">v Assoc Seq Line Items(Water Bottle)</span></span>|  
  
 <span data-ttu-id="8130e-246">このクエリでは、条件に一致した入れ子になったテーブルの行と、外部テーブル (ケース テーブル) のすべての行が返されます。</span><span class="sxs-lookup"><span data-stu-id="8130e-246">This query returns both the rows from the nested table that match the criteria, and all the rows from the outside or case table.</span></span> <span data-ttu-id="8130e-247">したがって、対象の属性名が NULL 値になっているケース テーブル行を除外する条件を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8130e-247">Therefore, you must add a condition that eliminates the case table rows that have a null value for the target attribute name.</span></span>  
  
 [<span data-ttu-id="8130e-248">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8130e-248">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="function-list"></a><span data-ttu-id="8130e-249">関数一覧</span><span class="sxs-lookup"><span data-stu-id="8130e-249">Function List</span></span>  
 <span data-ttu-id="8130e-250">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8130e-250">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="8130e-251">ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムでは、次の表のような追加の関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8130e-251">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8130e-252">予測関数</span><span class="sxs-lookup"><span data-stu-id="8130e-252">Prediction Function</span></span>|<span data-ttu-id="8130e-253">使用法</span><span class="sxs-lookup"><span data-stu-id="8130e-253">Usage</span></span>|  
|[<span data-ttu-id="8130e-254">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-254">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="8130e-255">あるノードがニューラル ネットワーク グラフ内の別のノードの子であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8130e-255">Determines whether one node is a child of another node in the neural network graph.</span></span>|  
|[<span data-ttu-id="8130e-256">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-256">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="8130e-257">指定されたノードが現在のケースを含んでいるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8130e-257">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="8130e-258">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-258">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="8130e-259">重み付け確率を返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-259">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="8130e-260">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-260">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="8130e-261">結合データセットのメンバーシップを予測します。</span><span class="sxs-lookup"><span data-stu-id="8130e-261">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="8130e-262">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-262">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="8130e-263">現在の予測値に関連する値のテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-263">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="8130e-264">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-264">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="8130e-265">各ケースの Node_ID を返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-265">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="8130e-266">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-266">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="8130e-267">予測値の確率を返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-267">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="8130e-268">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-268">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="8130e-269">指定された状態に対するサポート値を返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-269">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="8130e-270">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-270">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="8130e-271">予測値の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="8130e-271">Returns variance for the predicted value.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8130e-272">参照</span><span class="sxs-lookup"><span data-stu-id="8130e-272">See Also</span></span>  
 <span data-ttu-id="8130e-273">[Microsoft アソシエーションアルゴリズム](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="8130e-273">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="8130e-274">[Microsoft アソシエーションアルゴリズムテクニカルリファレンス](microsoft-association-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8130e-274">[Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="8130e-275">アソシエーション モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="8130e-275">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
