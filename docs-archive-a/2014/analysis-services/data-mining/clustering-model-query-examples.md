---
title: クラスタリングモデルのクエリ例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [Data Mining]
- content queries [DMX]
- clustering algorithms [Analysis Services]
ms.assetid: bf2ba332-9bc6-411a-a3af-b919c52432c8
author: minewiskan
ms.author: owend
ms.openlocfilehash: fe12b82ce2d237acd060b1e387e7a6dfbf958851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645937"
---
# <a name="clustering-model-query-examples"></a><span data-ttu-id="131ef-102">クラスタリング モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="131ef-102">Clustering Model Query Examples</span></span>
  <span data-ttu-id="131ef-103">データ マイニング モデルに対するクエリを作成すると、モデルに関するメタデータを取得できます。また、分析で検出されたパターンに関する詳細を取得するためのコンテンツ クエリも作成できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-103">When you create a query against a data mining model, you can retrieve metadata about the model, or create a content query that provides details about the patterns discovered in analysis.</span></span> <span data-ttu-id="131ef-104">モデル内のパターンを使用して新しいデータの予測を行う予測クエリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-104">Alternatively, you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="131ef-105">取得できる情報は、クエリの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="131ef-105">Each type of query will provide different information.</span></span> <span data-ttu-id="131ef-106">たとえばコンテンツ クエリを使用すると、検出されたクラスターに関する追加情報を取得できるのに対し、予測クエリを使用すると、新しいデータ ポイントが所属する可能性が高いクラスターを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="131ef-106">For example, a content query might provide additional details about the clusters that were found, whereas a prediction query might tell you in which cluster a new data point is most likely to belong.</span></span>  
  
 <span data-ttu-id="131ef-107">ここでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムに基づいたモデルに対するクエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="131ef-107">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
 <span data-ttu-id="131ef-108">**コンテンツ クエリ**</span><span class="sxs-lookup"><span data-stu-id="131ef-108">**Content Queries**</span></span>  
  
 [<span data-ttu-id="131ef-109">DMX を使用してモデル メタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-109">Getting Model Metadata by Using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="131ef-110">スキーマ行セットからモデル メタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-110">Retrieving Model Metadata from the Schema Rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="131ef-111">クラスターまたはクラスターのリストを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-111">Returning a Cluster or a List of Clusters</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="131ef-112">クラスターの属性を取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-112">Returning Attributes for a Cluster</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="131ef-113">システム ストアド プロシージャを使用してクラスターのプロファイルを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-113">Returning a Cluster Profile Using System Stored Procedures</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="131ef-114">クラスターの識別要因を取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-114">Finding Discriminating Factors for a Cluster</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="131ef-115">クラスターに属するケースを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-115">Returning Cases that Belong to a Cluster</span></span>](#bkmk_Query7)  
  
 <span data-ttu-id="131ef-116">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="131ef-116">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="131ef-117">クラスター モデルの結果を予測する</span><span class="sxs-lookup"><span data-stu-id="131ef-117">Predicting Outcomes from a Clustering Model</span></span>](#bkmk_Query8)  
  
 [<span data-ttu-id="131ef-118">クラスター メンバーシップを確認する</span><span class="sxs-lookup"><span data-stu-id="131ef-118">Determining Cluster Membership</span></span>](#bkmk_Query9)  
  
 [<span data-ttu-id="131ef-119">すべての可能なクラスターを確率および距離と共に取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-119">Returning All Possible Clusters with Probability and Distance</span></span>](#bkmk_Query10)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="131ef-120">モデルに関する情報の入手</span><span class="sxs-lookup"><span data-stu-id="131ef-120">Finding Information about the Model</span></span>  
 <span data-ttu-id="131ef-121">すべてのマイニング モデルでは、アルゴリズムによる学習内容が、正規化されたスキーマ (マイニング モデル スキーマ行セット) に従って公開されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-121">All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset.</span></span> <span data-ttu-id="131ef-122">マイニング モデル スキーマ行セットに対するクエリは、データ マイニング拡張機能 (DMX) ステートメントを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-122">You can create queries against the mining model schema rowset by using Data Mining Extension (DMX) statements.</span></span> <span data-ttu-id="131ef-123">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、スキーマ行セットに対して直接、システム テーブルとしてクエリを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-123">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can also query the schema rowsets directly as system tables.</span></span>  
  
 [<span data-ttu-id="131ef-124">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-124">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="131ef-125">サンプル クエリ 1: DMX を使用してモデル メタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-125">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="131ef-126">次のクエリは、「基本的なデータ マイニング チュートリアル」で作成したクラスター モデル `TM_Clustering`に関する基本的なメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-126">The following query returns basic metadata about the clustering model, `TM_Clustering`, that you created in the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="131ef-127">クラスター モデルの親ノードで利用可能なメタデータには、モデルの名前、モデルが格納されているデータベース、モデルの子ノードの数などがあります。</span><span class="sxs-lookup"><span data-stu-id="131ef-127">The metadata available in the parent node of a clustering model includes the name of the model, the database where the model is stored, and the number of child nodes in the model.</span></span> <span data-ttu-id="131ef-128">このクエリでは、DMX コンテンツ クエリを使用してモデルの親ノードからメタデータを取得しています。</span><span class="sxs-lookup"><span data-stu-id="131ef-128">This query uses a DMX content query to retrieve the metadata from the parent node of the model:</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM TM_Clustering.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="131ef-129">CHILDREN_CARDINALITY という列名は、多次元式 (MDX) の同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="131ef-129">You must enclose the name of the column, CHILDREN_CARDINALITY, in brackets to distinguish it from the Multidimensional Expressions (MDX) reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="131ef-130">結果の例:</span><span class="sxs-lookup"><span data-stu-id="131ef-130">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="131ef-131">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="131ef-131">MODEL_CATALOG</span></span>|<span data-ttu-id="131ef-132">TM_Clustering</span><span class="sxs-lookup"><span data-stu-id="131ef-132">TM_Clustering</span></span>|  
|<span data-ttu-id="131ef-133">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="131ef-133">MODEL_NAME</span></span>|<span data-ttu-id="131ef-134">Adventure Works DW</span><span class="sxs-lookup"><span data-stu-id="131ef-134">Adventure Works DW</span></span>|  
|<span data-ttu-id="131ef-135">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="131ef-135">NODE_CAPTION</span></span>|<span data-ttu-id="131ef-136">Cluster Model</span><span class="sxs-lookup"><span data-stu-id="131ef-136">Cluster Model</span></span>|  
|<span data-ttu-id="131ef-137">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="131ef-137">NODE_SUPPORT</span></span>|<span data-ttu-id="131ef-138">12939</span><span class="sxs-lookup"><span data-stu-id="131ef-138">12939</span></span>|  
|<span data-ttu-id="131ef-139">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="131ef-139">CHILDREN_CARDINALITY</span></span>|<span data-ttu-id="131ef-140">10</span><span class="sxs-lookup"><span data-stu-id="131ef-140">10</span></span>|  
|<span data-ttu-id="131ef-141">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="131ef-141">NODE_DESCRIPTION</span></span>|<span data-ttu-id="131ef-142">All</span><span class="sxs-lookup"><span data-stu-id="131ef-142">All</span></span>|  
  
 <span data-ttu-id="131ef-143">アソシエーション モデル内でのこれらの列の意味については、「[クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="131ef-143">For a definition of what these columns mean in a clustering model, see [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="131ef-144">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-144">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-2-retrieving-model-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a><span data-ttu-id="131ef-145">サンプルクエリ 2: スキーマ行セットからモデルメタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-145">Sample Query 2: Retrieving Model Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="131ef-146">データ マイニング スキーマ行セットに対してクエリを実行すると、DMX コンテンツ クエリで返されたのと同じ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-146">By querying the data mining schema rowset, you can find the same information that is returned in a DMX content query.</span></span> <span data-ttu-id="131ef-147">ただし、スキーマ行セットから返される情報にはいくつかの追加の列があります</span><span class="sxs-lookup"><span data-stu-id="131ef-147">However, the schema rowset provides some additional columns.</span></span> <span data-ttu-id="131ef-148">(モデルの作成時に使用されたパラメーター、モデルが最後に処理された日時、モデルの所有者など)。</span><span class="sxs-lookup"><span data-stu-id="131ef-148">These include the parameters that were used when the model was created, the date and time that the model was last processed, and the owner of the model.</span></span>  
  
 <span data-ttu-id="131ef-149">次の例では、モデルが作成された日、変更された日、最後に処理された日、モデルの作成に使用されたクラスタリング パラメーター、およびトレーニング セットのサイズが返されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-149">The following example returns the date the model was created, modified, and last processed, together with the clustering parameters that were used to build the model, and the size of the training set.</span></span> <span data-ttu-id="131ef-150">この情報は、モデルのドキュメントを作成する場合や、既存のモデルの作成に使用されたクラスタリング オプションを特定する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-150">This information can be useful for documenting the model, or for determining which of the clustering options were used to create an existing model.</span></span>  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Clustering'  
```  
  
 <span data-ttu-id="131ef-151">結果の例:</span><span class="sxs-lookup"><span data-stu-id="131ef-151">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="131ef-152">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="131ef-152">MODEL_NAME</span></span>|<span data-ttu-id="131ef-153">TM_Clustering</span><span class="sxs-lookup"><span data-stu-id="131ef-153">TM_Clustering</span></span>|  
|<span data-ttu-id="131ef-154">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="131ef-154">DATE_CREATED</span></span>|<span data-ttu-id="131ef-155">10/12/2007 7:42:51 PM</span><span class="sxs-lookup"><span data-stu-id="131ef-155">10/12/2007 7:42:51 PM</span></span>|  
|<span data-ttu-id="131ef-156">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="131ef-156">LAST_PROCESSED</span></span>|<span data-ttu-id="131ef-157">10/12/2007 8:09:54 PM</span><span class="sxs-lookup"><span data-stu-id="131ef-157">10/12/2007 8:09:54 PM</span></span>|  
|<span data-ttu-id="131ef-158">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="131ef-158">PREDICTION_ENTITY</span></span>|<span data-ttu-id="131ef-159">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="131ef-159">Bike Buyer</span></span>|  
|<span data-ttu-id="131ef-160">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="131ef-160">MINING_PARAMETERS</span></span>|<span data-ttu-id="131ef-161">CLUSTER_COUNT=10,</span><span class="sxs-lookup"><span data-stu-id="131ef-161">CLUSTER_COUNT=10,</span></span><br /><br /> <span data-ttu-id="131ef-162">CLUSTER_SEED=0,</span><span class="sxs-lookup"><span data-stu-id="131ef-162">CLUSTER_SEED=0,</span></span><br /><br /> <span data-ttu-id="131ef-163">CLUSTERING_METHOD=1,</span><span class="sxs-lookup"><span data-stu-id="131ef-163">CLUSTERING_METHOD=1,</span></span><br /><br /> <span data-ttu-id="131ef-164">MAXIMUM_INPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="131ef-164">MAXIMUM_INPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="131ef-165">MAXIMUM_STATES=100,</span><span class="sxs-lookup"><span data-stu-id="131ef-165">MAXIMUM_STATES=100,</span></span><br /><br /> <span data-ttu-id="131ef-166">MINIMUM_SUPPORT=1,</span><span class="sxs-lookup"><span data-stu-id="131ef-166">MINIMUM_SUPPORT=1,</span></span><br /><br /> <span data-ttu-id="131ef-167">MODELLING_CARDINALITY=10,</span><span class="sxs-lookup"><span data-stu-id="131ef-167">MODELLING_CARDINALITY=10,</span></span><br /><br /> <span data-ttu-id="131ef-168">SAMPLE_SIZE=50000,</span><span class="sxs-lookup"><span data-stu-id="131ef-168">SAMPLE_SIZE=50000,</span></span><br /><br /> <span data-ttu-id="131ef-169">STOPPING_TOLERANCE=10</span><span class="sxs-lookup"><span data-stu-id="131ef-169">STOPPING_TOLERANCE=10</span></span>|  
  
 [<span data-ttu-id="131ef-170">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-170">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="finding-information-about-clusters"></a><span data-ttu-id="131ef-171">クラスターに関する情報の入手</span><span class="sxs-lookup"><span data-stu-id="131ef-171">Finding Information about Clusters</span></span>  
 <span data-ttu-id="131ef-172">一般に、クラスター モデルに対する最も便利なコンテンツ クエリでは、 **クラスター ビューアー**を使用して参照できるのと同じ種類の情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-172">The most useful content queries on clustering models generally return the same type of information that you can browse by using the **Cluster Viewer**.</span></span> <span data-ttu-id="131ef-173">こうした情報には、クラスターのプロファイル、クラスターの特性、クラスターの識別などがあります。</span><span class="sxs-lookup"><span data-stu-id="131ef-173">This includes cluster profiles, cluster characteristics, and cluster discrimination.</span></span> <span data-ttu-id="131ef-174">ここでは、この情報を取得するクエリの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="131ef-174">This section provides examples of queries that retrieve this information.</span></span>  
  
###  <a name="sample-query-3-returning-a-cluster-or-list-of-clusters"></a><a name="bkmk_Query3"></a> <span data-ttu-id="131ef-175">サンプル クエリ 3: クラスターまたはクラスターのリストを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-175">Sample Query 3: Returning a Cluster or List of Clusters</span></span>  
 <span data-ttu-id="131ef-176">すべてのクラスターはノードの種類が 5 であるため、モデル コンテンツに対してその種類のノードのみのクエリを実行することによって、簡単にクラスターのリストを取得できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-176">Because all clusters have a node type of 5, you can easily retrieve a list of the clusters by querying the model content for only the nodes of that type.</span></span> <span data-ttu-id="131ef-177">この例のように、返されるノードを確率やサポートでフィルター処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-177">You can also filter the nodes that are returned by probability or by support, as shown in this example.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION ,NODE_SUPPORT, NODE_DESCRIPTION  
FROM TM_Clustering.CONTENT  
WHERE NODE_TYPE = 5 AND NODE_SUPPORT > 1000  
```  
  
 <span data-ttu-id="131ef-178">結果の例:</span><span class="sxs-lookup"><span data-stu-id="131ef-178">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="131ef-179">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="131ef-179">NODE_NAME</span></span>|<span data-ttu-id="131ef-180">002</span><span class="sxs-lookup"><span data-stu-id="131ef-180">002</span></span>|  
|<span data-ttu-id="131ef-181">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="131ef-181">NODE_CAPTION</span></span>|<span data-ttu-id="131ef-182">Cluster 2</span><span class="sxs-lookup"><span data-stu-id="131ef-182">Cluster 2</span></span>|  
|<span data-ttu-id="131ef-183">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="131ef-183">NODE_SUPPORT</span></span>|<span data-ttu-id="131ef-184">1649</span><span class="sxs-lookup"><span data-stu-id="131ef-184">1649</span></span>|  
|<span data-ttu-id="131ef-185">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="131ef-185">NODE_DESCRIPTION</span></span>|<span data-ttu-id="131ef-186">English Education=Graduate Degree , 32 <=Age <=48 , Number Cars Owned=0 , 35964.0771121808 <=Yearly Income <=97407.7163393957 , English Occupation=Professional , Commute Distance=2-5 Miles , Region=North America , Bike Buyer=1 , Number Children At Home=0 , Number Cars Owned=1 , Commute Distance=0-1 Miles , English Education=Bachelors , Total Children=1 , Number Children At Home=2 , English Occupation=Skilled Manual , Marital Status=S , Total Children=0 , House Owner Flag=0 , Gender=F , Total Children=2 , Region=Pacific</span><span class="sxs-lookup"><span data-stu-id="131ef-186">English Education=Graduate Degree , 32 <=Age <=48 , Number Cars Owned=0 , 35964.0771121808 <=Yearly Income <=97407.7163393957 , English Occupation=Professional , Commute Distance=2-5 Miles , Region=North America , Bike Buyer=1 , Number Children At Home=0 , Number Cars Owned=1 , Commute Distance=0-1 Miles , English Education=Bachelors , Total Children=1 , Number Children At Home=2 , English Occupation=Skilled Manual , Marital Status=S , Total Children=0 , House Owner Flag=0 , Gender=F , Total Children=2 , Region=Pacific</span></span>|  
  
 <span data-ttu-id="131ef-187">クラスターを定義する属性は、データ マイニング スキーマ行セットの 2 つの列に含まれています。</span><span class="sxs-lookup"><span data-stu-id="131ef-187">The attributes that define the cluster can be found in two columns in the data mining schema rowset.</span></span>  
  
-   <span data-ttu-id="131ef-188">NODE_DESCRIPTION 列には、属性のコンマ区切りのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="131ef-188">The NODE_DESCRIPTION column contains a comma-separated list of attributes.</span></span> <span data-ttu-id="131ef-189">この属性のリストは、表示のために省略されることもあります。</span><span class="sxs-lookup"><span data-stu-id="131ef-189">Note that the list of attributes might be abbreviated for display purposes.</span></span>  
  
-   <span data-ttu-id="131ef-190">NODE_DISTRIBUTION 列の入れ子になったテーブルには、クラスターのすべての属性のリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="131ef-190">The nested table in the NODE_DISTRIBUTION column contains the full list of attributes for the cluster.</span></span> <span data-ttu-id="131ef-191">使用しているクライアントで階層的な行セットがサポートされていない場合は、SELECT 列リストの前に FLATTENED キーワードを追加することによって、入れ子になったテーブルを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="131ef-191">If your client does not support hierarchical rowsets, you can return the nested table by adding the FLATTENED keyword before the SELECT column list.</span></span> <span data-ttu-id="131ef-192">FLATTENED キーワードの使用方法の詳細については、「[SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="131ef-192">For more information about the use of the FLATTENED keyword, see [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx).</span></span>  
  
 [<span data-ttu-id="131ef-193">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-193">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-4-returning-attributes-for-a-cluster"></a><a name="bkmk_Query4"></a> <span data-ttu-id="131ef-194">サンプル クエリ 4: クラスターの属性を取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-194">Sample Query 4: Returning Attributes for a Cluster</span></span>  
 <span data-ttu-id="131ef-195">**クラスター ビューアー** には、すべてのクラスターについて、属性とその値の一覧を含むプロファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-195">For every cluster, the **Cluster Viewer** displays a profile that lists the attributes and their values.</span></span> <span data-ttu-id="131ef-196">そのほか、モデル内のケースの母集団全体の値の分布を示すヒストグラムも表示されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-196">The viewer also displays a histogram that shows the distribution of values for the whole population of cases in the model.</span></span> <span data-ttu-id="131ef-197">ビューアーでモデルを参照する場合は、このヒストグラムをマイニング凡例からコピーして、簡単に Excel や Word のドキュメントに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="131ef-197">If you are browsing the model in the viewer, you can easily copy the histogram from the Mining Legend and then paste it to Excel or a Word document.</span></span> <span data-ttu-id="131ef-198">また、ビューアーの [クラスターの特性] ペインを使用して、異なるクラスターの属性をグラフィカルに比較することもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-198">You can also use the Cluster Characteristics pane of the viewer to graphically compare the attributes of different clusters.</span></span>  
  
 <span data-ttu-id="131ef-199">ただし、一度に複数のクラスターの値を取得する必要がある場合は、モデルに対してクエリを実行する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="131ef-199">However, if you must obtain values for more than one cluster at a time, it is easier to query the model.</span></span> <span data-ttu-id="131ef-200">たとえば、モデルを参照していて、上位 2 つのクラスターは `Number Cars Owned`という属性が異なっていることに気付いた場合、</span><span class="sxs-lookup"><span data-stu-id="131ef-200">For example, when you browse the model, you might notice that the top two clusters differ with regard to one attribute, `Number Cars Owned`.</span></span> <span data-ttu-id="131ef-201">それぞれのクラスターの値を抽出することができます。</span><span class="sxs-lookup"><span data-stu-id="131ef-201">Therefore, you want to extract the values for each cluster.</span></span>  
  
```  
SELECT TOP 2 NODE_NAME,   
(SELECT ATTRIBUTE_VALUE, [PROBABILITY] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Number Cars Owned')  
AS t  
FROM [TM_Clustering].CONTENT  
WHERE NODE_TYPE = 5  
```  
  
 <span data-ttu-id="131ef-202">コードの最初の行で、上位 2 つのクラスターのみを対象とすることを指定しています。</span><span class="sxs-lookup"><span data-stu-id="131ef-202">The first line of the code specifies that you want only the top two clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="131ef-203">既定では、クラスターはサポートで順序付けされます。</span><span class="sxs-lookup"><span data-stu-id="131ef-203">By default, the clusters are ordered by support.</span></span> <span data-ttu-id="131ef-204">したがって、NODE_SUPPORT 列は省略できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-204">Therefore, the NODE_SUPPORT column can be omitted.</span></span>  
  
 <span data-ttu-id="131ef-205">コードの 2 行目では、入れ子になったテーブル列の特定の列のみを返す下位選択ステートメントを追加しています。</span><span class="sxs-lookup"><span data-stu-id="131ef-205">The second line of the code adds a sub-select statement that returns only certain columns from the nested table column.</span></span> <span data-ttu-id="131ef-206">さらに、入れ子になったテーブルの行を、対象の属性 ( `Number Cars Owned`) に関連する行のみに制限しています。</span><span class="sxs-lookup"><span data-stu-id="131ef-206">Furthermore, it restricts the rows from the nested table to those related to the target attribute, `Number Cars Owned`.</span></span> <span data-ttu-id="131ef-207">また、表示を簡略化するために、入れ子になったテーブルに別名を付けています。</span><span class="sxs-lookup"><span data-stu-id="131ef-207">To simplify the display, the nested table is aliased.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="131ef-208">入れ子になったテーブル列である `PROBABILITY`は、MDX の予約済みキーワードと同じ名前であるため、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="131ef-208">The nested table column, `PROBABILITY`, must be enclosed in brackets because it is also the name of a reserved MDX keyword.</span></span>  
>   
>  <span data-ttu-id="131ef-209">結果の例:</span><span class="sxs-lookup"><span data-stu-id="131ef-209">Example results:</span></span>  
  
|<span data-ttu-id="131ef-210">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="131ef-210">NODE_NAME</span></span>|<span data-ttu-id="131ef-211">T.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="131ef-211">T.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="131ef-212">T.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="131ef-212">T.PROBABILITY</span></span>|  
|----------------|------------------------|-------------------|  
|<span data-ttu-id="131ef-213">001</span><span class="sxs-lookup"><span data-stu-id="131ef-213">001</span></span>|<span data-ttu-id="131ef-214">2</span><span class="sxs-lookup"><span data-stu-id="131ef-214">2</span></span>|<span data-ttu-id="131ef-215">0.829207754</span><span class="sxs-lookup"><span data-stu-id="131ef-215">0.829207754</span></span>|  
|<span data-ttu-id="131ef-216">001</span><span class="sxs-lookup"><span data-stu-id="131ef-216">001</span></span>|<span data-ttu-id="131ef-217">1</span><span class="sxs-lookup"><span data-stu-id="131ef-217">1</span></span>|<span data-ttu-id="131ef-218">0.109354156</span><span class="sxs-lookup"><span data-stu-id="131ef-218">0.109354156</span></span>|  
|<span data-ttu-id="131ef-219">001</span><span class="sxs-lookup"><span data-stu-id="131ef-219">001</span></span>|<span data-ttu-id="131ef-220">3</span><span class="sxs-lookup"><span data-stu-id="131ef-220">3</span></span>|<span data-ttu-id="131ef-221">0.034481552</span><span class="sxs-lookup"><span data-stu-id="131ef-221">0.034481552</span></span>|  
|<span data-ttu-id="131ef-222">001</span><span class="sxs-lookup"><span data-stu-id="131ef-222">001</span></span>|<span data-ttu-id="131ef-223">4</span><span class="sxs-lookup"><span data-stu-id="131ef-223">4</span></span>|<span data-ttu-id="131ef-224">0.013503302</span><span class="sxs-lookup"><span data-stu-id="131ef-224">0.013503302</span></span>|  
|<span data-ttu-id="131ef-225">001</span><span class="sxs-lookup"><span data-stu-id="131ef-225">001</span></span>|<span data-ttu-id="131ef-226">0</span><span class="sxs-lookup"><span data-stu-id="131ef-226">0</span></span>|<span data-ttu-id="131ef-227">0.013453236</span><span class="sxs-lookup"><span data-stu-id="131ef-227">0.013453236</span></span>|  
|<span data-ttu-id="131ef-228">001</span><span class="sxs-lookup"><span data-stu-id="131ef-228">001</span></span>|<span data-ttu-id="131ef-229">Missing</span><span class="sxs-lookup"><span data-stu-id="131ef-229">Missing</span></span>|<span data-ttu-id="131ef-230">0</span><span class="sxs-lookup"><span data-stu-id="131ef-230">0</span></span>|  
|<span data-ttu-id="131ef-231">002</span><span class="sxs-lookup"><span data-stu-id="131ef-231">002</span></span>|<span data-ttu-id="131ef-232">0</span><span class="sxs-lookup"><span data-stu-id="131ef-232">0</span></span>|<span data-ttu-id="131ef-233">0.576980023</span><span class="sxs-lookup"><span data-stu-id="131ef-233">0.576980023</span></span>|  
|<span data-ttu-id="131ef-234">002</span><span class="sxs-lookup"><span data-stu-id="131ef-234">002</span></span>|<span data-ttu-id="131ef-235">1</span><span class="sxs-lookup"><span data-stu-id="131ef-235">1</span></span>|<span data-ttu-id="131ef-236">0.406623939</span><span class="sxs-lookup"><span data-stu-id="131ef-236">0.406623939</span></span>|  
|<span data-ttu-id="131ef-237">002</span><span class="sxs-lookup"><span data-stu-id="131ef-237">002</span></span>|<span data-ttu-id="131ef-238">2</span><span class="sxs-lookup"><span data-stu-id="131ef-238">2</span></span>|<span data-ttu-id="131ef-239">0.016380082</span><span class="sxs-lookup"><span data-stu-id="131ef-239">0.016380082</span></span>|  
|<span data-ttu-id="131ef-240">002</span><span class="sxs-lookup"><span data-stu-id="131ef-240">002</span></span>|<span data-ttu-id="131ef-241">3</span><span class="sxs-lookup"><span data-stu-id="131ef-241">3</span></span>|<span data-ttu-id="131ef-242">1.60E-05</span><span class="sxs-lookup"><span data-stu-id="131ef-242">1.60E-05</span></span>|  
|<span data-ttu-id="131ef-243">002</span><span class="sxs-lookup"><span data-stu-id="131ef-243">002</span></span>|<span data-ttu-id="131ef-244">4</span><span class="sxs-lookup"><span data-stu-id="131ef-244">4</span></span>|<span data-ttu-id="131ef-245">0</span><span class="sxs-lookup"><span data-stu-id="131ef-245">0</span></span>|  
|<span data-ttu-id="131ef-246">002</span><span class="sxs-lookup"><span data-stu-id="131ef-246">002</span></span>|<span data-ttu-id="131ef-247">Missing</span><span class="sxs-lookup"><span data-stu-id="131ef-247">Missing</span></span>|<span data-ttu-id="131ef-248">0</span><span class="sxs-lookup"><span data-stu-id="131ef-248">0</span></span>|  
  
 [<span data-ttu-id="131ef-249">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-249">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-5-return-a-cluster-profile-using-system-stored-procedures"></a><a name="bkmk_Query5"></a> <span data-ttu-id="131ef-250">サンプル クエリ 5: システム ストアド プロシージャを使用してクラスターのプロファイルを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-250">Sample Query 5: Return a Cluster Profile Using System Stored Procedures</span></span>  
 <span data-ttu-id="131ef-251">DMX を使用して独自にクエリを作成する代わりに、より簡単な方法として、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でクラスターの操作に使用されるシステム ストアド プロシージャを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-251">As a shortcut, rather than writing your own queries by using DMX, you can also call the system stored procedures that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to work with clusters.</span></span> <span data-ttu-id="131ef-252">次の例は、内部ストアド プロシージャを使用して、ID が 002 のクラスターのプロファイルを取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="131ef-252">The following example illustrates how to use the internal stored procedures to return the profile for a cluster with the ID of 002.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterProfiles('TM_Clustering", '002',0.0005  
```  
  
 <span data-ttu-id="131ef-253">同様に、システム ストアド プロシージャを使用して、次の例のように特定のクラスターの特性を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-253">Similarly, you can use a system stored procedure to return the characteristics of a specific cluster, as shown in the following example:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('TM_Clustering", '009',0.0005  
```  
  
 <span data-ttu-id="131ef-254">結果の例:</span><span class="sxs-lookup"><span data-stu-id="131ef-254">Example results:</span></span>  
  
|<span data-ttu-id="131ef-255">属性</span><span class="sxs-lookup"><span data-stu-id="131ef-255">Attributes</span></span>|<span data-ttu-id="131ef-256">値</span><span class="sxs-lookup"><span data-stu-id="131ef-256">Values</span></span>|<span data-ttu-id="131ef-257">頻度</span><span class="sxs-lookup"><span data-stu-id="131ef-257">Frequency</span></span>|<span data-ttu-id="131ef-258">サポート</span><span class="sxs-lookup"><span data-stu-id="131ef-258">Support</span></span>|  
|----------------|------------|---------------|-------------|  
|<span data-ttu-id="131ef-259">Number Children at Home</span><span class="sxs-lookup"><span data-stu-id="131ef-259">Number Children at Home</span></span>|<span data-ttu-id="131ef-260">0</span><span class="sxs-lookup"><span data-stu-id="131ef-260">0</span></span>|<span data-ttu-id="131ef-261">0.999999829076798</span><span class="sxs-lookup"><span data-stu-id="131ef-261">0.999999829076798</span></span>|<span data-ttu-id="131ef-262">899</span><span class="sxs-lookup"><span data-stu-id="131ef-262">899</span></span>|  
|<span data-ttu-id="131ef-263">リージョン</span><span class="sxs-lookup"><span data-stu-id="131ef-263">Region</span></span>|<span data-ttu-id="131ef-264">北米</span><span class="sxs-lookup"><span data-stu-id="131ef-264">North America</span></span>|<span data-ttu-id="131ef-265">0.999852875241508</span><span class="sxs-lookup"><span data-stu-id="131ef-265">0.999852875241508</span></span>|<span data-ttu-id="131ef-266">899</span><span class="sxs-lookup"><span data-stu-id="131ef-266">899</span></span>|  
|<span data-ttu-id="131ef-267">Total Children</span><span class="sxs-lookup"><span data-stu-id="131ef-267">Total Children</span></span>|<span data-ttu-id="131ef-268">0</span><span class="sxs-lookup"><span data-stu-id="131ef-268">0</span></span>|<span data-ttu-id="131ef-269">0.993860958572323</span><span class="sxs-lookup"><span data-stu-id="131ef-269">0.993860958572323</span></span>|<span data-ttu-id="131ef-270">893</span><span class="sxs-lookup"><span data-stu-id="131ef-270">893</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="131ef-271">データ マイニング システム ストアド プロシージャは内部で使用するためのものであり、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、これらを必要に応じて変更する場合があります。</span><span class="sxs-lookup"><span data-stu-id="131ef-271">The data mining system stored procedures are for internal use and [!INCLUDE[msCoName](../../includes/msconame-md.md)] reserves the right to change them as needed.</span></span> <span data-ttu-id="131ef-272">実際の運用では、DMX、AMO、または XMLA を使用してクエリを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="131ef-272">For production use, we recommend that you create queries by using DMX, AMO, or XMLA.</span></span>  
  
 [<span data-ttu-id="131ef-273">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-273">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-6-find-discriminating-factors-for-a-cluster"></a><a name="bkmk_Query6"></a> <span data-ttu-id="131ef-274">サンプル クエリ 6: クラスターの識別要因を取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-274">Sample Query 6: Find Discriminating Factors for a Cluster</span></span>  
 <span data-ttu-id="131ef-275">**クラスター ビューアー** の **[クラスターの識別]** タブを使用すると、クラスターを簡単に別のクラスターと比較したり、他のすべてのケース (そのクラスターを除く全クラスター) と比較したりできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-275">The **Cluster Discrimination** tab of the **Cluster Viewer** enables you to easily compare a cluster with another cluster, or compare a cluster with all remaining cases (the complement of the cluster).</span></span>  
  
 <span data-ttu-id="131ef-276">一方、この情報を返すクエリを作成するのは簡単ではなく、一時的な結果を格納して複数のクエリの結果を比較する追加の処理がクライアント側で必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="131ef-276">However, creating queries to return this information can be complex, and you might need some additional processing on the client to store the temporary results and compare the results of two or more queries.</span></span> <span data-ttu-id="131ef-277">より簡単な方法として、システム ストアド プロシージャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-277">As a shortcut, you can use the system stored procedures.</span></span>  
  
 <span data-ttu-id="131ef-278">次のクエリは、ノード ID が 009 と 007 の 2 つのクラスターの主な識別要因を示す 1 つのテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-278">The following query returns a single table that indicates the primary discriminating factors between the two clusters that have the node IDs of 009 and 007.</span></span> <span data-ttu-id="131ef-279">正の値を持つ属性ではクラスター 009 が優先され、負の値を持つ属性ではクラスター 007 が優先されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-279">Attributes with positive values favor cluster 009, whereas attributes with negative values favor cluster 007.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('TM_Clustering','009','007',0.0005,true)  
```  
  
 <span data-ttu-id="131ef-280">結果の例:</span><span class="sxs-lookup"><span data-stu-id="131ef-280">Example results:</span></span>  
  
|<span data-ttu-id="131ef-281">属性</span><span class="sxs-lookup"><span data-stu-id="131ef-281">Attributes</span></span>|<span data-ttu-id="131ef-282">値</span><span class="sxs-lookup"><span data-stu-id="131ef-282">Values</span></span>|<span data-ttu-id="131ef-283">Score</span><span class="sxs-lookup"><span data-stu-id="131ef-283">Score</span></span>|  
|----------------|------------|-----------|  
|<span data-ttu-id="131ef-284">リージョン</span><span class="sxs-lookup"><span data-stu-id="131ef-284">Region</span></span>|<span data-ttu-id="131ef-285">北米</span><span class="sxs-lookup"><span data-stu-id="131ef-285">North America</span></span>|<span data-ttu-id="131ef-286">100</span><span class="sxs-lookup"><span data-stu-id="131ef-286">100</span></span>|  
|<span data-ttu-id="131ef-287">English Occupation</span><span class="sxs-lookup"><span data-stu-id="131ef-287">English Occupation</span></span>|<span data-ttu-id="131ef-288">Skilled Manual</span><span class="sxs-lookup"><span data-stu-id="131ef-288">Skilled Manual</span></span>|<span data-ttu-id="131ef-289">94.9003803898654</span><span class="sxs-lookup"><span data-stu-id="131ef-289">94.9003803898654</span></span>|  
|<span data-ttu-id="131ef-290">リージョン</span><span class="sxs-lookup"><span data-stu-id="131ef-290">Region</span></span>|<span data-ttu-id="131ef-291">ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="131ef-291">Europe</span></span>|<span data-ttu-id="131ef-292">-72.5041051379789</span><span class="sxs-lookup"><span data-stu-id="131ef-292">-72.5041051379789</span></span>|  
|<span data-ttu-id="131ef-293">English Occupation</span><span class="sxs-lookup"><span data-stu-id="131ef-293">English Occupation</span></span>|<span data-ttu-id="131ef-294">マニュアル</span><span class="sxs-lookup"><span data-stu-id="131ef-294">Manual</span></span>|<span data-ttu-id="131ef-295">-69.6503163202722</span><span class="sxs-lookup"><span data-stu-id="131ef-295">-69.6503163202722</span></span>|  
  
 <span data-ttu-id="131ef-296">この情報は、 **[クラスターの識別]** タブの 1 つ目のドロップダウン リストでクラスター 9 を選択し、2 つ目のドロップダウン リストでクラスター 7 を選択した場合にグラフに表示されるのと同じ情報です。</span><span class="sxs-lookup"><span data-stu-id="131ef-296">This is the same information that is presented in the chart of the **Cluster Discrimination** viewer if you select Cluster 9 from the first drop-down list and Cluster 7 from the second drop-down list.</span></span> <span data-ttu-id="131ef-297">クラスター 9 を他のすべてのクラスターと比較するには、次のように、2 つ目のパラメーターで空の文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="131ef-297">To compare cluster 9 with its complement, you use the empty string in the second parameter, as shown in the following example:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('TM_Clustering','009','',0.0005,true)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="131ef-298">データ マイニング システム ストアド プロシージャは内部で使用するためのものであり、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、これらを必要に応じて変更する場合があります。</span><span class="sxs-lookup"><span data-stu-id="131ef-298">The data mining system stored procedures are for internal use and [!INCLUDE[msCoName](../../includes/msconame-md.md)] reserves the right to change them as needed.</span></span> <span data-ttu-id="131ef-299">実際の運用では、DMX、AMO、または XMLA を使用してクエリを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="131ef-299">For production use, we recommend that you create queries by using DMX, AMO, or XMLA.</span></span>  
  
 [<span data-ttu-id="131ef-300">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-300">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-7-returning-cases-that-belong-to-a-cluster"></a><a name="bkmk_Query7"></a> <span data-ttu-id="131ef-301">サンプル クエリ 7: クラスターに属するケースを取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-301">Sample Query 7: Returning Cases that Belong to a Cluster</span></span>  
 <span data-ttu-id="131ef-302">マイニング モデルでドリルスルーが有効になっている場合は、モデルで使用されたケースに関する詳細情報を返すクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-302">If drillthrough has been enabled on the mining model, you can create queries that return detailed information about the cases used in the model.</span></span> <span data-ttu-id="131ef-303">さらに、マイニング構造でドリルスルーが有効になっている場合は、[StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 関数を使用して、基になる構造の列を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-303">Moreover, if drillthrough has been enabled on the mining structure, you can include columns from the underlying structure by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
 <span data-ttu-id="131ef-304">次の例は、モデルで使用された 2 つの列 (Age および Region) と、モデルで使用されなかったもう 1 つの列 (First Name) を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-304">The following example returns two columns that were used in the model, Age and Region, and one more column, First Name, that was not used in the model.</span></span> <span data-ttu-id="131ef-305">このクエリで返されるのは、クラスター 1 に分類されたケースだけです。</span><span class="sxs-lookup"><span data-stu-id="131ef-305">The query returns only cases that were classified into Cluster 1.</span></span>  
  
```  
SELECT [Age], [Region], StructureColumn('First Name')  
FROM [TM_Clustering].CASES  
WHERE IsInNode('001')  
```  
  
 <span data-ttu-id="131ef-306">クラスターに属するケースを取得するには、そのクラスターの ID がわかっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="131ef-306">To return the cases that belong to a cluster, you must know the ID of the cluster.</span></span> <span data-ttu-id="131ef-307">クラスターの ID は、いずれかのビューアーでモデルを参照することによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-307">You can obtain the ID of the cluster by browsing the model in one of the viewers.</span></span> <span data-ttu-id="131ef-308">また、簡単に参照できるようにクラスターの名前を変更することもできます。名前を変更した後は、その名前を ID 番号の代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="131ef-308">Or, you can rename a cluster for easier reference, after which you could use the name in place of an ID number.</span></span> <span data-ttu-id="131ef-309">ただし、クラスターに割り当てた名前はモデルを再処理すると失われるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="131ef-309">However, know that the names that you assign to a cluster will be lost if the model is reprocessed.</span></span>  
  
 [<span data-ttu-id="131ef-310">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-310">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a><span data-ttu-id="131ef-311">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="131ef-311">Making Predictions using the Model</span></span>  
 <span data-ttu-id="131ef-312">クラスターは、データの説明や把握のために使用されるのが一般的ですが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] の実装では、クラスター メンバーシップに関する予測を行って、その予測に関連する確率を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-312">Although clustering is typically used for describing and understanding data, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] implementation also lets you make prediction about cluster membership, and return probabilities associated with the prediction.</span></span> <span data-ttu-id="131ef-313">ここでは、クラスター モデルに対する予測クエリを作成する方法の例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="131ef-313">This section provides examples of how to create prediction queries on clustering models.</span></span> <span data-ttu-id="131ef-314">表形式のデータ ソースを指定して複数のケースの予測を行うことも、単一クエリを作成して一度に 1 つずつ新しい値を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-314">You can make predictions for multiple cases, by specifying a tabular data source, or you can provide new values on at a time by creating a singleton query.</span></span> <span data-ttu-id="131ef-315">このセクションの例は、わかりやすくするためにすべて単一クエリになっています。</span><span class="sxs-lookup"><span data-stu-id="131ef-315">For clarity the examples in this section are all singleton queries.</span></span>  
  
 <span data-ttu-id="131ef-316">DMX を使用した予測クエリの作成方法の詳細については、「[データマイニングクエリインターフェイス](data-mining-query-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="131ef-316">For more information about how to create prediction queries using DMX, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
 [<span data-ttu-id="131ef-317">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-317">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-8-predicting-outcomes-from-a-clustering-model"></a><a name="bkmk_Query8"></a> <span data-ttu-id="131ef-318">サンプル クエリ 8: クラスター モデルの結果を予測する</span><span class="sxs-lookup"><span data-stu-id="131ef-318">Sample Query 8: Predicting Outcomes from a Clustering Model</span></span>  
 <span data-ttu-id="131ef-319">作成したクラスター モデルに予測可能な属性が含まれている場合は、そのモデルを使用して結果に関する予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="131ef-319">If the clustering model you create contains a predictable attribute, you can use the model to make predictions about outcomes.</span></span> <span data-ttu-id="131ef-320">ただし、予測可能列を `Predict` に設定するか `PredictOnly` に設定するかによって、モデルによる予測可能な属性の処理方法が異なります。</span><span class="sxs-lookup"><span data-stu-id="131ef-320">However, the model handles the predictable attribute differently depending on whether you set the predictable column to `Predict` or `PredictOnly`.</span></span> <span data-ttu-id="131ef-321">列の使用法を `Predict` に設定すると、その属性の値がクラスター モデルに追加され、完成したモデルに属性として表示されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-321">If you set the usage of the column to `Predict`, the values for that attribute are added to the clustering model and appear as attributes in the finished model.</span></span> <span data-ttu-id="131ef-322">一方、列の使用法を `PredictOnly` に設定すると、その値はクラスターの作成には使用されません。</span><span class="sxs-lookup"><span data-stu-id="131ef-322">However, if you set the usage of the column to `PredictOnly`, the values are not used to create clusters.</span></span> <span data-ttu-id="131ef-323">代わりに、モデルが完成した後に、各ケースが属するクラスターに基づいて `PredictOnly` 属性の新しい値がクラスタリング アルゴリズムによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-323">Instead, after the mode is completed, the clustering algorithm creates new values for the `PredictOnly` attribute based on the clusters to which each case belongs.</span></span>  
  
 <span data-ttu-id="131ef-324">次のクエリでは、モデルに新しいケースを 1 つ渡しています。このケースに関する情報は Age と Gender だけです。</span><span class="sxs-lookup"><span data-stu-id="131ef-324">The following query provides a single new case to the model, where the only information about the case is the age and gender.</span></span> <span data-ttu-id="131ef-325">SELECT ステートメントでは、関心のある予測可能な属性と値のペアを指定しています。 [PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx) 関数は、それらの属性を持つケースの結果が対象の結果になる確率を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-325">The SELECT statement specifies the predictable attribute/value pair that you are interested in, and the [PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx) function tells you the probability that a case with those attributes will have the targeted outcome.</span></span>  
  
```  
SELECT  
  [TM_Clustering].[Bike Buyer], PredictProbability([Bike Buyer],1)  
FROM  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="131ef-326">使用法を `Predict` に設定した場合の結果の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="131ef-326">Example of results when usage is set to `Predict`:</span></span>  
  
|<span data-ttu-id="131ef-327">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="131ef-327">Bike Buyer</span></span>|<span data-ttu-id="131ef-328">式</span><span class="sxs-lookup"><span data-stu-id="131ef-328">Expression</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="131ef-329">1</span><span class="sxs-lookup"><span data-stu-id="131ef-329">1</span></span>|<span data-ttu-id="131ef-330">0.592924735740338</span><span class="sxs-lookup"><span data-stu-id="131ef-330">0.592924735740338</span></span>|  
  
 <span data-ttu-id="131ef-331">使用法を `PredictOnly` に設定し、モデルを再処理した場合の結果の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="131ef-331">Example of results when the usage is set to `PredictOnly` and the model is reprocessed:</span></span>  
  
|<span data-ttu-id="131ef-332">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="131ef-332">Bike Buyer</span></span>|<span data-ttu-id="131ef-333">式</span><span class="sxs-lookup"><span data-stu-id="131ef-333">Expression</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="131ef-334">1</span><span class="sxs-lookup"><span data-stu-id="131ef-334">1</span></span>|<span data-ttu-id="131ef-335">0.55843544003102</span><span class="sxs-lookup"><span data-stu-id="131ef-335">0.55843544003102</span></span>|  
  
 <span data-ttu-id="131ef-336">この例ではモデルに大きな違いはありませんが、</span><span class="sxs-lookup"><span data-stu-id="131ef-336">In this example, the difference in the model is not significant.</span></span> <span data-ttu-id="131ef-337">値の実際の分布とモデルの予測との違いを検出することが重要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="131ef-337">However, sometimes it can be important to detect differences between the actual distribution of values and what the model predicts.</span></span> <span data-ttu-id="131ef-338">そのような場合は、 [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) 関数を使用できます。この関数は、特定のモデルについてケースの確率を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-338">The [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) function is useful in this scenario, because it tells you how likely a case is, given the model.</span></span>  
  
 <span data-ttu-id="131ef-339">PredictCaseLikelihood 関数によって返される数値は確率であるため、常に 0 と 1 の間になります。値 .5 はランダムな結果を表します。</span><span class="sxs-lookup"><span data-stu-id="131ef-339">The number that is returned by the PredictCaseLikelihood function is a probability, and therefore is always between 0 and 1, with a value of .5 representing random outcome.</span></span> <span data-ttu-id="131ef-340">したがって、スコアが .5 より小さい場合は、予測されたケースがそのモデルではあり得そうにないことを示し、.5 より大きい場合は、おそらくモデルに収まることを示します。</span><span class="sxs-lookup"><span data-stu-id="131ef-340">Therefore, a score less than .5 means that the predicted case is unlikely, given the model, and a score over.5 indicates that the predicted case is more likely than not to fit the model.</span></span>  
  
 <span data-ttu-id="131ef-341">たとえば次のクエリは、新しいサンプル ケースの可能性を表す 2 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-341">For example, the following query returns two values that characterize the likelihood of a new sample case.</span></span> <span data-ttu-id="131ef-342">正規化されていない値は、現在のモデルでの確率を表します。</span><span class="sxs-lookup"><span data-stu-id="131ef-342">The non-normalized value represents the probability given the current model.</span></span> <span data-ttu-id="131ef-343">NORMALIZED キーワードを使用すると、この関数によって返される可能性スコアが、"モデルを使用した場合の確率" を "モデル使用しない場合の確率" で割って調整されます。</span><span class="sxs-lookup"><span data-stu-id="131ef-343">When you use the NORMALIZED keyword, the likelihood score that is returned by the function is adjusted by dividing "probability with the model" by "probability without the model".</span></span>  
  
```  
SELECT  
PredictCaseLikelihood(NORMALIZED) AS [NormalizedValue], PredictCaseLikelihood(NONNORMALIZED) AS [NonNormalizedValue]  
FROM  
  [TM_Clustering_PredictOnly]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="131ef-344">結果の例:</span><span class="sxs-lookup"><span data-stu-id="131ef-344">Example results:</span></span>  
  
|<span data-ttu-id="131ef-345">NormalizedValue</span><span class="sxs-lookup"><span data-stu-id="131ef-345">NormalizedValue</span></span>|<span data-ttu-id="131ef-346">NonNormalizedValue</span><span class="sxs-lookup"><span data-stu-id="131ef-346">NonNormalizedValue</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="131ef-347">5.56438372679893E-11</span><span class="sxs-lookup"><span data-stu-id="131ef-347">5.56438372679893E-11</span></span>|<span data-ttu-id="131ef-348">8.65459953145182E-68</span><span class="sxs-lookup"><span data-stu-id="131ef-348">8.65459953145182E-68</span></span>|  
  
 <span data-ttu-id="131ef-349">これらの結果の数値は科学的表記法で表されています。</span><span class="sxs-lookup"><span data-stu-id="131ef-349">Note that the numbers in these results are expressed in scientific notation.</span></span>  
  
 [<span data-ttu-id="131ef-350">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-350">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-9-determining-cluster-membership"></a><a name="bkmk_Query9"></a> <span data-ttu-id="131ef-351">サンプル クエリ 9: クラスター メンバーシップを確認する</span><span class="sxs-lookup"><span data-stu-id="131ef-351">Sample Query 9: Determining Cluster Membership</span></span>  
 <span data-ttu-id="131ef-352">この例では、 [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) 関数を使用して、新しいケースが属する可能性が最も高いクラスターを取得し、 [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx) 関数を使用して、そのクラスターに属する確率を取得しています。</span><span class="sxs-lookup"><span data-stu-id="131ef-352">This example uses the [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) function to return the cluster to which the new case is most likely to belong, and uses the [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx) function to return the probability for membership in that cluster.</span></span>  
  
```  
SELECT Cluster(), ClusterProbability()  
FROM  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender],  
  'S' AS [Marital Status]) AS t  
```  
  
 <span data-ttu-id="131ef-353">結果の例:</span><span class="sxs-lookup"><span data-stu-id="131ef-353">Example results:</span></span>  
  
|<span data-ttu-id="131ef-354">$CLUSTER</span><span class="sxs-lookup"><span data-stu-id="131ef-354">$CLUSTER</span></span>|<span data-ttu-id="131ef-355">式</span><span class="sxs-lookup"><span data-stu-id="131ef-355">Expression</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="131ef-356">Cluster 2</span><span class="sxs-lookup"><span data-stu-id="131ef-356">Cluster 2</span></span>|<span data-ttu-id="131ef-357">0.397918596951617</span><span class="sxs-lookup"><span data-stu-id="131ef-357">0.397918596951617</span></span>|  
  
 <span data-ttu-id="131ef-358">**メモ**既定では、 `ClusterProbability` 関数は最も可能性の高いクラスターの確率を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-358">**Note** By default, the `ClusterProbability` function returns the probability of the most likely cluster.</span></span> <span data-ttu-id="131ef-359">ただし、 `ClusterProbability('cluster name')`という構文を使用して別のクラスターを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-359">However, you can specify a different cluster by using the syntax `ClusterProbability('cluster name')`.</span></span> <span data-ttu-id="131ef-360">その場合は、この 2 つの予測関数の結果は互いに無関係であるため、</span><span class="sxs-lookup"><span data-stu-id="131ef-360">If you do this, be aware that the results from each prediction function are independent of the other results.</span></span> <span data-ttu-id="131ef-361">2 番目の列の確率スコアが、1 番目の列のクラスターとは別のクラスターのものになる場合もあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="131ef-361">Therefore, the probability score in the second column could refer to a different cluster than the cluster named in the first column.</span></span>  
  
 [<span data-ttu-id="131ef-362">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-362">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-10-returning-all-possible-clusters-with-probability-and-distance"></a><a name="bkmk_Query10"></a> <span data-ttu-id="131ef-363">サンプル クエリ 10: すべての可能なクラスターを確率および距離と共に取得する</span><span class="sxs-lookup"><span data-stu-id="131ef-363">Sample Query 10: Returning All Possible Clusters with Probability and Distance</span></span>  
 <span data-ttu-id="131ef-364">前の例の確率スコアはあまり高くありませんでした。</span><span class="sxs-lookup"><span data-stu-id="131ef-364">In the previous example, the probability score was not very high.</span></span> <span data-ttu-id="131ef-365">より適したクラスターがあるかどうかを調べるには、 [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx) 関数を [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) 関数と共に使用して、すべての可能なクラスターと、各クラスターに新しいケースが属する確率を含む、入れ子になったテーブルを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="131ef-365">To determine if there is a better cluster, you can use the [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx) function together with the [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) function to return a nested table that includes all possible clusters, together with the probability that the new case that belongs to each cluster.</span></span> <span data-ttu-id="131ef-366">ここでは、結果を見やすくするために、FLATTENED キーワードを使用して階層的な行セットをフラット テーブルに変更しています。</span><span class="sxs-lookup"><span data-stu-id="131ef-366">The FLATTENED keyword is used to change the hierarchical rowset into a flat table for easier viewing.</span></span>  
  
```  
SELECT FLATTENED PredictHistogram(Cluster())  
From  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender],  
  'S' AS [Marital Status])  
```  
  
|<span data-ttu-id="131ef-367">Expression.$CLUSTER</span><span class="sxs-lookup"><span data-stu-id="131ef-367">Expression.$CLUSTER</span></span>|<span data-ttu-id="131ef-368">Expression.$DISTANCE</span><span class="sxs-lookup"><span data-stu-id="131ef-368">Expression.$DISTANCE</span></span>|<span data-ttu-id="131ef-369">Expression.$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="131ef-369">Expression.$PROBABILITY</span></span>|  
|-------------------------|--------------------------|-----------------------------|  
|<span data-ttu-id="131ef-370">Cluster 2</span><span class="sxs-lookup"><span data-stu-id="131ef-370">Cluster 2</span></span>|<span data-ttu-id="131ef-371">0.602081403048383</span><span class="sxs-lookup"><span data-stu-id="131ef-371">0.602081403048383</span></span>|<span data-ttu-id="131ef-372">0.397918596951617</span><span class="sxs-lookup"><span data-stu-id="131ef-372">0.397918596951617</span></span>|  
|<span data-ttu-id="131ef-373">Cluster 10</span><span class="sxs-lookup"><span data-stu-id="131ef-373">Cluster 10</span></span>|<span data-ttu-id="131ef-374">0.719691686785675</span><span class="sxs-lookup"><span data-stu-id="131ef-374">0.719691686785675</span></span>|<span data-ttu-id="131ef-375">0.280308313214325</span><span class="sxs-lookup"><span data-stu-id="131ef-375">0.280308313214325</span></span>|  
|<span data-ttu-id="131ef-376">Cluster 4</span><span class="sxs-lookup"><span data-stu-id="131ef-376">Cluster 4</span></span>|<span data-ttu-id="131ef-377">0.867772590378791</span><span class="sxs-lookup"><span data-stu-id="131ef-377">0.867772590378791</span></span>|<span data-ttu-id="131ef-378">0.132227409621209</span><span class="sxs-lookup"><span data-stu-id="131ef-378">0.132227409621209</span></span>|  
|<span data-ttu-id="131ef-379">Cluster 5</span><span class="sxs-lookup"><span data-stu-id="131ef-379">Cluster 5</span></span>|<span data-ttu-id="131ef-380">0.931039872200985</span><span class="sxs-lookup"><span data-stu-id="131ef-380">0.931039872200985</span></span>|<span data-ttu-id="131ef-381">0.0689601277990149</span><span class="sxs-lookup"><span data-stu-id="131ef-381">0.0689601277990149</span></span>|  
|<span data-ttu-id="131ef-382">Cluster 3</span><span class="sxs-lookup"><span data-stu-id="131ef-382">Cluster 3</span></span>|<span data-ttu-id="131ef-383">0.942359230072167</span><span class="sxs-lookup"><span data-stu-id="131ef-383">0.942359230072167</span></span>|<span data-ttu-id="131ef-384">0.0576407699278328</span><span class="sxs-lookup"><span data-stu-id="131ef-384">0.0576407699278328</span></span>|  
|<span data-ttu-id="131ef-385">クラスター 6</span><span class="sxs-lookup"><span data-stu-id="131ef-385">Cluster 6</span></span>|<span data-ttu-id="131ef-386">0.958973668972756</span><span class="sxs-lookup"><span data-stu-id="131ef-386">0.958973668972756</span></span>|<span data-ttu-id="131ef-387">0.0410263310272437</span><span class="sxs-lookup"><span data-stu-id="131ef-387">0.0410263310272437</span></span>|  
|<span data-ttu-id="131ef-388">Cluster 7</span><span class="sxs-lookup"><span data-stu-id="131ef-388">Cluster 7</span></span>|<span data-ttu-id="131ef-389">0.979081275926724</span><span class="sxs-lookup"><span data-stu-id="131ef-389">0.979081275926724</span></span>|<span data-ttu-id="131ef-390">0.0209187240732763</span><span class="sxs-lookup"><span data-stu-id="131ef-390">0.0209187240732763</span></span>|  
|<span data-ttu-id="131ef-391">クラスター 1</span><span class="sxs-lookup"><span data-stu-id="131ef-391">Cluster 1</span></span>|<span data-ttu-id="131ef-392">0.999169044818624</span><span class="sxs-lookup"><span data-stu-id="131ef-392">0.999169044818624</span></span>|<span data-ttu-id="131ef-393">0.000830955181376364</span><span class="sxs-lookup"><span data-stu-id="131ef-393">0.000830955181376364</span></span>|  
|<span data-ttu-id="131ef-394">Cluster 9</span><span class="sxs-lookup"><span data-stu-id="131ef-394">Cluster 9</span></span>|<span data-ttu-id="131ef-395">0.999831227795894</span><span class="sxs-lookup"><span data-stu-id="131ef-395">0.999831227795894</span></span>|<span data-ttu-id="131ef-396">0.000168772204105754</span><span class="sxs-lookup"><span data-stu-id="131ef-396">0.000168772204105754</span></span>|  
|<span data-ttu-id="131ef-397">Cluster 8</span><span class="sxs-lookup"><span data-stu-id="131ef-397">Cluster 8</span></span>|<span data-ttu-id="131ef-398">1</span><span class="sxs-lookup"><span data-stu-id="131ef-398">1</span></span>|<span data-ttu-id="131ef-399">0</span><span class="sxs-lookup"><span data-stu-id="131ef-399">0</span></span>|  
  
 <span data-ttu-id="131ef-400">既定では、結果は確率で順位付けされます。</span><span class="sxs-lookup"><span data-stu-id="131ef-400">By default, the results are ranked by probability.</span></span> <span data-ttu-id="131ef-401">この結果から、Cluster 2 は、確率はかなり低いとはいえ、新しいデータ ポイントに最適なクラスターであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="131ef-401">The results tell you that, even though the probability for Cluster 2 is fairly low, Cluster 2 is still the best fit for the new data point.</span></span>  
  
 <span data-ttu-id="131ef-402">**注:** 追加の列の `$DISTANCE`は、データ ポイントからクラスターまでの距離を表します。</span><span class="sxs-lookup"><span data-stu-id="131ef-402">**Note** The additional column, `$DISTANCE`, represents the distance from the data point to the cluster.</span></span> <span data-ttu-id="131ef-403">[!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムでは、既定でスケーラブル EM クラスタリングが使用されます。スケーラブル EM クラスタリングでは、各データ ポイントに複数のクラスターが割り当てられて、可能なクラスターが順位付けされます。</span><span class="sxs-lookup"><span data-stu-id="131ef-403">By default, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering Algorithm uses scalable EM clustering, which assigns multiple clusters to each data point and ranks the possible clusters.</span></span>  <span data-ttu-id="131ef-404">一方、K-Means アルゴリズムを使用してクラスター モデルを作成した場合は、各データ ポイントに 1 つしかクラスターを割り当てることができないため、このクエリで返される行は 1 行だけになります。</span><span class="sxs-lookup"><span data-stu-id="131ef-404">However, if you create your clustering model using the K-means algorithm, only one cluster can be assigned to each data point, and this query would return only one row.</span></span> <span data-ttu-id="131ef-405">[PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) 関数を使用して、基になる構造の列を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="131ef-405">Understanding these differences is necessary to interpret the results of the [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) function.</span></span> <span data-ttu-id="131ef-406">EM クラスタリングと K-Means クラスタリングの相違点の詳細については、「 [Microsoft クラスタリング アルゴリズム テクニカル リファレンス](microsoft-clustering-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="131ef-406">For more information about the differences between EM and K-means clustering, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>  
  
 [<span data-ttu-id="131ef-407">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="131ef-407">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="function-list"></a><span data-ttu-id="131ef-408">関数一覧</span><span class="sxs-lookup"><span data-stu-id="131ef-408">Function List</span></span>  
 <span data-ttu-id="131ef-409">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="131ef-409">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="131ef-410">ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムを使用して作成されたモデルでは、次の表のような追加の関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="131ef-410">However, models that are built by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm support the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="131ef-411">予測関数</span><span class="sxs-lookup"><span data-stu-id="131ef-411">Prediction Function</span></span>|<span data-ttu-id="131ef-412">使用法</span><span class="sxs-lookup"><span data-stu-id="131ef-412">Usage</span></span>|  
|[<span data-ttu-id="131ef-413">Cluster &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-413">Cluster &#40;DMX&#41;</span></span>](/sql/dmx/cluster-dmx)|<span data-ttu-id="131ef-414">入力ケースを含んでいる可能性が最も高いクラスターを返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-414">Returns the cluster that is most likely to contain the input case.</span></span>|  
|[<span data-ttu-id="131ef-415">ClusterDistance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-415">ClusterDistance &#40;DMX&#41;</span></span>](/sql/dmx/clusterdistance-dmx)|<span data-ttu-id="131ef-416">指定されたクラスターと入力したケース間の距離を返します。ただしクラスターが指定されていない場合は、最も可能性の高いクラスターと入力したケース間の距離を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-416">Returns the distance of the input case from the specified cluster, or if no cluster is specified, the distance of the input case from the most likely cluster.</span></span><br /><br /> <span data-ttu-id="131ef-417">入力ケースが指定されたクラスターに所属する確率を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-417">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="131ef-418">ClusterProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-418">ClusterProbability &#40;DMX&#41;</span></span>](/sql/dmx/clusterprobability-dmx)|<span data-ttu-id="131ef-419">入力ケースが指定されたクラスターに所属する確率を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-419">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="131ef-420">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-420">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="131ef-421">あるノードがモデル内の別のノードの子であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="131ef-421">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="131ef-422">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-422">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="131ef-423">指定されたノードが現在のケースを含んでいるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="131ef-423">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="131ef-424">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-424">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="131ef-425">重み付け確率を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-425">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="131ef-426">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-426">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="131ef-427">結合データセットのメンバーシップを予測します。</span><span class="sxs-lookup"><span data-stu-id="131ef-427">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="131ef-428">PredictCaseLikelihood &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-428">PredictCaseLikelihood &#40;DMX&#41;</span></span>](/sql/dmx/predictcaselikelihood-dmx)|<span data-ttu-id="131ef-429">入力したケースが既存のモデル内に収まる確率値を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-429">Returns the likelihood that an input case will fit in the existing model.</span></span>|  
|[<span data-ttu-id="131ef-430">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-430">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="131ef-431">現在の予測値に関連する値のテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-431">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="131ef-432">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-432">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="131ef-433">各ケースの Node_ID を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-433">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="131ef-434">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-434">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="131ef-435">予測値の確率を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-435">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="131ef-436">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-436">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="131ef-437">指定された列に対して、予測された標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-437">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="131ef-438">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-438">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="131ef-439">指定された状態に対するサポート値を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-439">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="131ef-440">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="131ef-440">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="131ef-441">指定された列の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="131ef-441">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="131ef-442">特定の関数の構文については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="131ef-442">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131ef-443">参照</span><span class="sxs-lookup"><span data-stu-id="131ef-443">See Also</span></span>  
 <span data-ttu-id="131ef-444">[データマイニングクエリ](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="131ef-444">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="131ef-445">[Microsoft クラスタリングアルゴリズムテクニカルリファレンス](microsoft-clustering-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="131ef-445">[Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="131ef-446">Microsoft クラスタリングアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="131ef-446">Microsoft Clustering Algorithm</span></span>](microsoft-clustering-algorithm.md)  
  
  
