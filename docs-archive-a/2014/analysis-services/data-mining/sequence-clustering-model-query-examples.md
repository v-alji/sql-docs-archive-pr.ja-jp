---
title: シーケンスクラスターモデルのクエリ例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- sequence clustering algorithms [Analysis Services]
- content queries [DMX]
- sequence [Analysis Services]
ms.assetid: 64bebcdc-70ab-43fb-8d40-57672a126602
author: minewiskan
ms.author: owend
ms.openlocfilehash: d56924f27f7986861895cf4fff21fa758cc47070
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631347"
---
# <a name="sequence-clustering-model-query-examples"></a><span data-ttu-id="a5f6d-102">Sequence Clustering Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="a5f6d-102">Sequence Clustering Model Query Examples</span></span>
  <span data-ttu-id="a5f6d-103">データ マイニング モデルに対するクエリを作成する際には、コンテンツ クエリを作成することも、予測クエリを作成することもできます。コンテンツ クエリでは、モデルに格納されている情報の詳細を取得できます。予測クエリでは、モデル内のパターンを使用して、指定した新しいデータに基づく予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-103">When you create a query against a data mining model, you can create either a content query, which provides details about the information stored in the model, or you can create a prediction query, which uses the patterns in the model to make predictions based on new data that you provide.</span></span> <span data-ttu-id="a5f6d-104">シーケンス クラスター モデルでコンテンツ クエリを使用すると、一般に、検出されたクラスターやクラスター内の遷移に関する追加情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-104">For a sequence clustering model, content queries typically provide additional details about the clusters that were found, or the transitions within those clusters.</span></span> <span data-ttu-id="a5f6d-105">クエリを使用してモデルに関するメタデータを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="a5f6d-106">シーケンス クラスター モデルで予測クエリを使用すると、一般に、シーケンスと遷移、モデル内の非シーケンス属性、またはシーケンス属性と非シーケンス属性の組み合わせに基づく提案が行われます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-106">Prediction queries on a sequence clustering model typically make recommendations based either on the sequences and transitions, on non-sequence attributes that were included in the model, or on a combination of sequence and non-sequence attributes.</span></span>  
  
 <span data-ttu-id="a5f6d-107">ここでは、Microsoft シーケンス クラスター アルゴリズムに基づいたモデルに対するクエリの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-107">This section explains how to create queries for models that are based on the Microsoft Sequence Clustering algorithm.</span></span> <span data-ttu-id="a5f6d-108">クエリの作成に関する一般的な情報については、「 [データ マイニング クエリ](data-mining-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-108">For general information about creating queries, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
 <span data-ttu-id="a5f6d-109">**コンテンツ クエリ**</span><span class="sxs-lookup"><span data-stu-id="a5f6d-109">**Content Queries**</span></span>  
  
 [<span data-ttu-id="a5f6d-110">データ マイニング スキーマ行セットを使用してモデル パラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="a5f6d-110">Using the Data Mining Schema Rowset to return model parameters</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="a5f6d-111">状態に対するシーケンス一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="a5f6d-111">Getting a list of sequences for a state</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="a5f6d-112">システムストアドプロシージャの使用</span><span class="sxs-lookup"><span data-stu-id="a5f6d-112">Using system stored procedures</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="a5f6d-113">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="a5f6d-113">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="a5f6d-114">次の状態を予測する</span><span class="sxs-lookup"><span data-stu-id="a5f6d-114">Predict next state or states</span></span>](#bkmk_Query4)  
  
##  <a name="finding-information-about-the-sequence-clustering-model"></a><a name="bkmk_ContentQueries"></a><span data-ttu-id="a5f6d-115">シーケンスクラスターモデルに関する情報の検索</span><span class="sxs-lookup"><span data-stu-id="a5f6d-115">Finding Information about the Sequence Clustering Model</span></span>  
 <span data-ttu-id="a5f6d-116">マイニング モデルのコンテンツに対して意味のあるクエリを作成するには、モデル コンテンツの構造や、各種類のノードに格納されている情報の種類を把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-116">To create meaningful queries on the content of a mining model, you must understand the structure of the model content, and which node types store what kind of information.</span></span> <span data-ttu-id="a5f6d-117">詳細については、「 [シーケンス クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-sequence-clustering-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-117">For more information, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-return-model-parameters"></a><a name="bkmk_Query1"></a><span data-ttu-id="a5f6d-118">サンプルクエリ 1: データマイニングスキーマ行セットを使用してモデルパラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="a5f6d-118">Sample Query 1: Using the Data Mining Schema Rowset to Return Model Parameters</span></span>  
 <span data-ttu-id="a5f6d-119">データ マイニング スキーマ行セットに対してクエリを実行すると、モデルに関する各種の情報を取得できます (基本的なメタデータ、モデルが作成された日時、モデルが最後に処理された日時、基になるマイニング構造の名前、予測可能な属性として使用されている列など)。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-119">By querying the data mining schema rowset, you can find various kinds of information about the model, including basic metadata, the date and time that the model was created and last processed, the name of the mining structure that the model is based on, and the column used as the predictable attribute.</span></span>  
  
 <span data-ttu-id="a5f6d-120">次のクエリでは、 `[Sequence Clustering]`モデルの作成とトレーニングに使用されたパラメーターが返されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-120">The following query returns the parameters that were used to build and train the model, `[Sequence Clustering]`.</span></span> <span data-ttu-id="a5f6d-121">このモデルは、「 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)」のレッスン 5 で作成できます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-121">You can create this model in Lesson 5 of the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Sequence Clustering'  
```  
  
 <span data-ttu-id="a5f6d-122">結果の例:</span><span class="sxs-lookup"><span data-stu-id="a5f6d-122">Example results:</span></span>  
  
|<span data-ttu-id="a5f6d-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a5f6d-123">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="a5f6d-124">CLUSTER_COUNT=15,MINIMUM_SUPPORT=10,MAXIMUM_STATES=100,MAXIMUM_SEQUENCE_STATES=64</span><span class="sxs-lookup"><span data-stu-id="a5f6d-124">CLUSTER_COUNT=15,MINIMUM_SUPPORT=10,MAXIMUM_STATES=100,MAXIMUM_SEQUENCE_STATES=64</span></span>|  
  
 <span data-ttu-id="a5f6d-125">このモデルは、CLUSTER_COUNT の既定値 10 を使用して作成されています。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-125">Note that this model was built by using the default value of 10 for CLUSTER_COUNT.</span></span> <span data-ttu-id="a5f6d-126">CLUSTER_COUNT にゼロ以外のクラスター数を指定した場合、アルゴリズムで取得するクラスターの概数のヒントとして、この数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-126">When you specify a non-zero number of clusters for CLUSTER_COUNT, the algorithm treats this number as a hint for the approximate number of clusters to find.</span></span> <span data-ttu-id="a5f6d-127">ただし、アルゴリズムによる分析処理時に取得されるクラスター数は、これより上下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-127">However, in the process of analysis, the algorithm may find more or fewer clusters.</span></span> <span data-ttu-id="a5f6d-128">ここでは、アルゴリズムによって、15 個のクラスターがトレーニング データに対し最適であると判断されました。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-128">In this case, the algorithm found that 15 clusters best fit the training data.</span></span> <span data-ttu-id="a5f6d-129">したがって、完成したモデルのパラメーター値の一覧では、モデルの作成時に渡された値ではなく、アルゴリズムによって決定されたクラスター数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-129">Therefore, the list of parameter values for the completed model reports the count of clusters as determined by the algorithm, not the value passed in when creating the model.</span></span>  
  
 <span data-ttu-id="a5f6d-130">最適なクラスター数をアルゴリズムで決定する場合と、この動作はどのように違うのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-130">How does this behavior differ from letting the algorithm determine the best number of clusters?</span></span> <span data-ttu-id="a5f6d-131">試しに、同じデータを使用する別のクラスター モデルを作成し、CLUSTER_COUNT を 0 に設定してみます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-131">As an experiment, you can create another clustering model that uses this same data, but set CLUSTER_COUNT to 0.</span></span> <span data-ttu-id="a5f6d-132">この場合、アルゴリズムでは 32 個のクラスターが検出されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-132">When you do this, the algorithm detects 32 clusters.</span></span> <span data-ttu-id="a5f6d-133">したがって、CLUSTER_COUNT の既定値 10 を使用することによって、結果の数が制限されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-133">Therefore, by using the default value of 10 for CLUSTER_COUNT, you constrain the number of results.</span></span>  
  
 <span data-ttu-id="a5f6d-134">既定値として 10 が使用されているのは、多くの人にとって、クラスター数が少ない方が、データのグループ化を参照および理解しやすいためです。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-134">The value of 10 is used by default because reducing the number of clusters makes it easier for most people to browse and understand groupings in the data.</span></span> <span data-ttu-id="a5f6d-135">ただし、それぞれのモデルとデータのセットは異なります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-135">However, each model and set of data is different.</span></span> <span data-ttu-id="a5f6d-136">クラスター数を増減してみて、最も正確なモデルが作成されるパラメーター値を探すようお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-136">You may wish to experiment with different numbers of clusters to see which parameter value yields the most accurate model.</span></span>  
  
###  <a name="sample-query-2-getting-a-list-of-sequences-for-a-state"></a><a name="bkmk_Query2"></a><span data-ttu-id="a5f6d-137">サンプルクエリ 2: 状態のシーケンスの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="a5f6d-137">Sample Query 2: Getting a List of Sequences for a State</span></span>  
 <span data-ttu-id="a5f6d-138">マイニング モデル コンテンツには、トレーニング データで検出されたシーケンスが、最初の状態とそれに関連する 2 番目の状態の一覧の組み合わせとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-138">The mining model content stores the sequences that are found in the training data as a first state coupled with a list of all related second states.</span></span> <span data-ttu-id="a5f6d-139">最初の状態がシーケンスのラベルとして使用され、関連する 2 番目の状態は遷移と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-139">The first state is used as the label for the sequence, and the related second states are called transitions.</span></span>  
  
 <span data-ttu-id="a5f6d-140">たとえば、次のクエリでは、モデルにある最初の状態の完全な一覧が返された後、シーケンスがクラスターにグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-140">For example, the following query returns the complete list of first states in the model, before the sequences are grouped into clusters.</span></span>  <span data-ttu-id="a5f6d-141">この一覧を取得するには、モデルのルート ノードを親 (PARENT_UNIQUE_NAME = 0) とするシーケンスの一覧 (NODE_TYPE = 13) を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-141">You can get this list by returning the list of sequences (NODE_TYPE = 13) that have the model root node as parent (PARENT_UNIQUE_NAME = 0).</span></span> <span data-ttu-id="a5f6d-142">FLATTENED キーワードによって、結果が読み取りやすくなります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-142">The FLATTENED keyword makes the results easier to read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5f6d-143">PARENT_UNIQUE_NAME、Support、Probability の各列名は、同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-143">The name of the columns, PARENT_UNIQUE_NAME, Support, and Probability must be enclosed in brackets to distinguish them from the reserved keywords of the same name.</span></span>  
  
```  
SELECT FLATTENED NODE_UNIQUE_NAME,  
(SELECT ATTRIBUTE_VALUE AS [Product 1],  
[Support] AS [Sequence Support],   
[Probability] AS [Sequence Probability]  
FROM NODE_DISTRIBUTION) AS t  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_TYPE = 13  
AND [PARENT_UNIQUE_NAME] = 0  
```  
  
 <span data-ttu-id="a5f6d-144">結果の一部 :</span><span class="sxs-lookup"><span data-stu-id="a5f6d-144">Partial results:</span></span>  
  
|<span data-ttu-id="a5f6d-145">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a5f6d-145">NODE_UNIQUE_NAME</span></span>|<span data-ttu-id="a5f6d-146">製品 1</span><span class="sxs-lookup"><span data-stu-id="a5f6d-146">Product 1</span></span>|<span data-ttu-id="a5f6d-147">シーケンス サポート</span><span class="sxs-lookup"><span data-stu-id="a5f6d-147">Sequence Support</span></span>|<span data-ttu-id="a5f6d-148">シーケンス確率</span><span class="sxs-lookup"><span data-stu-id="a5f6d-148">Sequence Probability</span></span>|  
|------------------------|---------------|----------------------|--------------------------|  
|<span data-ttu-id="a5f6d-149">1081327</span><span class="sxs-lookup"><span data-stu-id="a5f6d-149">1081327</span></span>|<span data-ttu-id="a5f6d-150">Missing</span><span class="sxs-lookup"><span data-stu-id="a5f6d-150">Missing</span></span>|<span data-ttu-id="a5f6d-151">0</span><span class="sxs-lookup"><span data-stu-id="a5f6d-151">0</span></span>|#######|  
|<span data-ttu-id="a5f6d-152">1081327</span><span class="sxs-lookup"><span data-stu-id="a5f6d-152">1081327</span></span>|<span data-ttu-id="a5f6d-153">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="a5f6d-153">All-Purpose Bike Stand</span></span>|<span data-ttu-id="a5f6d-154">17</span><span class="sxs-lookup"><span data-stu-id="a5f6d-154">17</span></span>|<span data-ttu-id="a5f6d-155">0.00111</span><span class="sxs-lookup"><span data-stu-id="a5f6d-155">0.00111</span></span>|  
|<span data-ttu-id="a5f6d-156">1081327</span><span class="sxs-lookup"><span data-stu-id="a5f6d-156">1081327</span></span>|<span data-ttu-id="a5f6d-157">Bike Wash</span><span class="sxs-lookup"><span data-stu-id="a5f6d-157">Bike Wash</span></span>|<span data-ttu-id="a5f6d-158">64</span><span class="sxs-lookup"><span data-stu-id="a5f6d-158">64</span></span>|<span data-ttu-id="a5f6d-159">0.00418</span><span class="sxs-lookup"><span data-stu-id="a5f6d-159">0.00418</span></span>|  
|<span data-ttu-id="a5f6d-160">1081327</span><span class="sxs-lookup"><span data-stu-id="a5f6d-160">1081327</span></span>|<span data-ttu-id="a5f6d-161">(行 4 ～ 36 は省略)</span><span class="sxs-lookup"><span data-stu-id="a5f6d-161">(rows 4-36 omitted)</span></span>|||  
|<span data-ttu-id="a5f6d-162">1081327</span><span class="sxs-lookup"><span data-stu-id="a5f6d-162">1081327</span></span>|<span data-ttu-id="a5f6d-163">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="a5f6d-163">Women's Mountain Shorts</span></span>|<span data-ttu-id="a5f6d-164">506</span><span class="sxs-lookup"><span data-stu-id="a5f6d-164">506</span></span>|<span data-ttu-id="a5f6d-165">0.03307</span><span class="sxs-lookup"><span data-stu-id="a5f6d-165">0.03307</span></span>|  
  
 <span data-ttu-id="a5f6d-166">モデル内のシーケンスの一覧は、常にアルファベットの昇順で表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-166">The list of sequences in the model is always sorted alphabetically in ascending order.</span></span> <span data-ttu-id="a5f6d-167">シーケンスの順序番号によって関連する遷移を検索するため、シーケンスの順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-167">The ordering of the sequences is important because you can find the related transitions by looking at the order number of the sequence.</span></span> <span data-ttu-id="a5f6d-168">`Missing` の値は常に遷移 0 です。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-168">The `Missing` value is always transition 0.</span></span>  
  
 <span data-ttu-id="a5f6d-169">たとえば、上の結果のモデルでは、製品 "Women's Mountain Shorts" のシーケンス番号が 37 です。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-169">For example, in the previous results, the product "Women's Mountain Shorts" is the sequence number 37 in the model.</span></span> <span data-ttu-id="a5f6d-170">この情報を使用して、"Women's Mountain Shorts" の後に購入されたすべての製品を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-170">You can use that information to view all of the products that were ever purchased after "Women's Mountain Shorts."</span></span>  
  
 <span data-ttu-id="a5f6d-171">そのためには、まず、上のクエリで NODE_UNIQUE_NAME に対して返された値を参照し、モデルのすべてのシーケンスを含むノードの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-171">To do this, first, you reference the value returned for NODE_UNIQUE_NAME in the previous query, to get the ID of the node that contains all sequences for the model.</span></span> <span data-ttu-id="a5f6d-172">この値を親ノードの ID としてクエリに渡し、このノードに含まれている遷移だけを取得します。このノードには、モデルのすべてのシーケンスの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-172">You pass this value to the query as the ID of the parent node, to get only the transitions included in this node, which happens to contain a list of al sequences for the model.</span></span> <span data-ttu-id="a5f6d-173">一方、特定のクラスターの遷移の一覧を表示するには、クラスター ノードの ID を渡します。これにより、そのクラスターに関連するシーケンスだけを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-173">However, if you wanted to see the list of transitions for a specific cluster, you could pass in the ID of the cluster node, and see only the sequences associated with that cluster.</span></span>  
  
```  
SELECT NODE_UNIQUE_NAME  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_DESCRIPTION = 'Transition row for sequence state 37'  
AND [PARENT_UNIQUE_NAME] = '1081327'  
```  
  
 <span data-ttu-id="a5f6d-174">結果の例:</span><span class="sxs-lookup"><span data-stu-id="a5f6d-174">Example results:</span></span>  
  
|<span data-ttu-id="a5f6d-175">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a5f6d-175">NODE_UNIQUE_NAME</span></span>|  
|------------------------|  
|<span data-ttu-id="a5f6d-176">1081365</span><span class="sxs-lookup"><span data-stu-id="a5f6d-176">1081365</span></span>|  
  
 <span data-ttu-id="a5f6d-177">この ID のノードには、製品 "Women's Mountain Shorts" に続くシーケンス、およびサポートと確率の値の一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-177">The node represented by this ID contains a list of the sequences that follow the "Women's Mountain Shorts" product, together with the support and probability values.</span></span>  
  
```  
SELECT FLATTENED  
(SELECT ATTRIBUTE_VALUE AS Product2,  
[Support] AS [P2 Support],  
[Probability] AS [P2 Probability]  
FROM NODE_DISTRIBUTION) AS t  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_UNIQUE_NAME = '1081365'  
```  
  
 <span data-ttu-id="a5f6d-178">結果の例:</span><span class="sxs-lookup"><span data-stu-id="a5f6d-178">Example results:</span></span>  
  
|<span data-ttu-id="a5f6d-179">t.Product2</span><span class="sxs-lookup"><span data-stu-id="a5f6d-179">t.Product2</span></span>|<span data-ttu-id="a5f6d-180">t.P2 サポート</span><span class="sxs-lookup"><span data-stu-id="a5f6d-180">t.P2 Support</span></span>|<span data-ttu-id="a5f6d-181">t.P2 確率</span><span class="sxs-lookup"><span data-stu-id="a5f6d-181">t.P2 Probability</span></span>|  
|----------------|------------------|----------------------|  
|<span data-ttu-id="a5f6d-182">Missing</span><span class="sxs-lookup"><span data-stu-id="a5f6d-182">Missing</span></span>|<span data-ttu-id="a5f6d-183">230.7419</span><span class="sxs-lookup"><span data-stu-id="a5f6d-183">230.7419</span></span>|<span data-ttu-id="a5f6d-184">0.456012</span><span class="sxs-lookup"><span data-stu-id="a5f6d-184">0.456012</span></span>|  
|<span data-ttu-id="a5f6d-185">Classic Vest</span><span class="sxs-lookup"><span data-stu-id="a5f6d-185">Classic Vest</span></span>|<span data-ttu-id="a5f6d-186">8.16129</span><span class="sxs-lookup"><span data-stu-id="a5f6d-186">8.16129</span></span>|<span data-ttu-id="a5f6d-187">0.016129</span><span class="sxs-lookup"><span data-stu-id="a5f6d-187">0.016129</span></span>|  
|<span data-ttu-id="a5f6d-188">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="a5f6d-188">Cycling Cap</span></span>|<span data-ttu-id="a5f6d-189">60.83871</span><span class="sxs-lookup"><span data-stu-id="a5f6d-189">60.83871</span></span>|<span data-ttu-id="a5f6d-190">0.120235</span><span class="sxs-lookup"><span data-stu-id="a5f6d-190">0.120235</span></span>|  
|<span data-ttu-id="a5f6d-191">Half-Finger Gloves</span><span class="sxs-lookup"><span data-stu-id="a5f6d-191">Half-Finger Gloves</span></span>|<span data-ttu-id="a5f6d-192">30.41935</span><span class="sxs-lookup"><span data-stu-id="a5f6d-192">30.41935</span></span>|<span data-ttu-id="a5f6d-193">0.060117</span><span class="sxs-lookup"><span data-stu-id="a5f6d-193">0.060117</span></span>|  
|<span data-ttu-id="a5f6d-194">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="a5f6d-194">Long-Sleeve Logo Jersey</span></span>|<span data-ttu-id="a5f6d-195">86.80645</span><span class="sxs-lookup"><span data-stu-id="a5f6d-195">86.80645</span></span>|<span data-ttu-id="a5f6d-196">0.171554</span><span class="sxs-lookup"><span data-stu-id="a5f6d-196">0.171554</span></span>|  
|<span data-ttu-id="a5f6d-197">Racing Socks</span><span class="sxs-lookup"><span data-stu-id="a5f6d-197">Racing Socks</span></span>|<span data-ttu-id="a5f6d-198">28.93548</span><span class="sxs-lookup"><span data-stu-id="a5f6d-198">28.93548</span></span>|<span data-ttu-id="a5f6d-199">0.057185</span><span class="sxs-lookup"><span data-stu-id="a5f6d-199">0.057185</span></span>|  
|<span data-ttu-id="a5f6d-200">Short-Sleeve Classic Jersey</span><span class="sxs-lookup"><span data-stu-id="a5f6d-200">Short-Sleeve Classic Jersey</span></span>|<span data-ttu-id="a5f6d-201">60.09677</span><span class="sxs-lookup"><span data-stu-id="a5f6d-201">60.09677</span></span>|<span data-ttu-id="a5f6d-202">0.118768</span><span class="sxs-lookup"><span data-stu-id="a5f6d-202">0.118768</span></span>|  
  
 <span data-ttu-id="a5f6d-203">このモデルでは、"Women's Mountain Shorts" に関連するさまざまなシーケンスに対するサポートが 506 です。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-203">Note that support for the various sequences related to Women's Mountain Shorts is 506 in the model.</span></span> <span data-ttu-id="a5f6d-204">遷移に対するサポートの値も 506 まで加算されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-204">The support values for the transitions also add up to 506.</span></span> <span data-ttu-id="a5f6d-205">ただし、これらの数は整数ではありません。サポートが単に各遷移を含むケースの数を表すと考えると、少々変な感じがするかもしれません。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-205">However, the numbers are not whole numbers, which seems a bit odd if you expect support to simply represent a count of cases that contain each transition.</span></span> <span data-ttu-id="a5f6d-206">しかし、クラスターを作成する方法では部分的なメンバーシップが計算されるため、クラスター内の任意の遷移の可能性は、その特定のクラスターに属する可能性によって重み付けされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-206">However, because the method for creating clusters calculates partial membership, the probability of any transition within a cluster must be weighted by its probability of belonging to that particular cluster.</span></span>  
  
 <span data-ttu-id="a5f6d-207">たとえば、クラスターが 4 つある場合、あるシーケンスがクラスター 1 に属する可能性は 40%、クラスター 2 に属する可能性は 30%、クラスター 3 に属する可能性は 20%、クラスター 4 に属する可能性は 10% です。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-207">For example, if there are four clusters, a particular sequence might have a 40% chance of belonging to cluster 1, a 30% chance of belonging to cluster 2, a 20% chance of belonging to cluster 3, and a 10% chance of belonging to cluster 4.</span></span> <span data-ttu-id="a5f6d-208">アルゴリズムでは、遷移が属する可能性が最も高いクラスターが特定された後、クラスター内での確率がクラスターの事前確率によって重み付けされます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-208">After the algorithm determines the cluster that the transition is mostly likely to belong to, it weights the probabilities within the cluster by the cluster prior probability.</span></span>  
  
###  <a name="sample-query-3-using-system-stored-procedures"></a><a name="bkmk_Query3"></a><span data-ttu-id="a5f6d-209">サンプルクエリ 3: システムストアドプロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="a5f6d-209">Sample Query 3: Using System Stored Procedures</span></span>  
 <span data-ttu-id="a5f6d-210">これらのクエリ サンプルから、モデルに格納された情報が複雑であることと、必要な情報を取得するために複数のクエリを作成する必要が生じる場合があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-210">You can see from these query samples that the information stored in the model is complex, and that you might need to create multiple queries to get the information that you need.</span></span> <span data-ttu-id="a5f6d-211">ただし、Microsoft シーケンス クラスター ビューアーには、シーケンス クラスター モデルに含まれている情報をグラフィカルに表示する、一連の強力なツールが用意されています。このビューアーを使用して、モデルにクエリやドリル ダウンを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-211">However, the Microsoft Sequence Clustering viewer provides a powerful set of tools for graphically browsing the information contained in a sequence clustering model, and you can also use the viewer to query and drill down into the model.</span></span>  
  
 <span data-ttu-id="a5f6d-212">Microsoft シーケンス クラスター ビューアーに表示される情報は、ほとんどの場合、モデルにクエリを実行する Analysis Services システム ストアド プロシージャを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-212">In most cases, the information that is presented in the Microsoft Sequence Clustering viewer is created by using Analysis Services system stored procedures to query the model.</span></span> <span data-ttu-id="a5f6d-213">モデル コンテンツに対するデータ マイニング拡張機能 (DMX) クエリを記述することによっても、同じ情報を取得できますが、Analysis Services システム ストアド プロシージャを使用すると、探索やモデルのテストをすばやく行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-213">You can write Data Mining Extensions (DMX) queries against the model content to retrieve the same information, but the Analysis Services system stored procedures provide a convenient shortcut when for exploration or for testing models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5f6d-214">システム ストアド プロシージャは、Analysis Services サーバーによって、また Analysis Services サーバーとの対話用に Microsoft が提供するクライアントによって、内部処理に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-214">System stored procedures are used for internal processing by the server and by the clients that Microsoft provides for interacting with the Analysis Services server.</span></span> <span data-ttu-id="a5f6d-215">したがって、Microsoft はこれらを随時変更する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-215">Therefore, Microsoft reserves the right to change them at any time.</span></span> <span data-ttu-id="a5f6d-216">ここでは便宜上、これらについて説明しますが、運用環境での使用はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-216">Although they are described here for your convenience, we do not support their use in a production environment.</span></span> <span data-ttu-id="a5f6d-217">運用環境での安定性と互換性を保つには、常に DMX を使用してクエリを記述してください。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-217">To ensure stability and compatibility in a production environment, you should always write your own queries by using DMX.</span></span>  
  
 <span data-ttu-id="a5f6d-218">ここでは、シーケンス クラスター モデルに対するクエリを作成するシステム ストアド プロシージャの使用例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-218">This section provides some samples of how to use the system stored procedures to create queries against a sequence clustering model:</span></span>  
  
#### <a name="cluster-profiles-and-sample-cases"></a><span data-ttu-id="a5f6d-219">クラスターのプロファイルとサンプル ケース</span><span class="sxs-lookup"><span data-stu-id="a5f6d-219">Cluster Profiles and Sample Cases</span></span>  
 <span data-ttu-id="a5f6d-220">[クラスターのプロファイル] タブには、モデル内のクラスターの一覧、各クラスターのサイズ、およびクラスターに含まれる状態を示すヒストグラムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-220">The Cluster Profiles tab shows you a list of the clusters in the model, the size of each cluster, and a histogram that indicates the states included in the cluster.</span></span> <span data-ttu-id="a5f6d-221">同様の情報を取得するクエリで使用できるシステム ストアド プロシージャには、次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-221">There are two system stored procedures that you can use in queries to retrieve similar information:</span></span>  
  
-   <span data-ttu-id="a5f6d-222">`GetClusterProfile` では、クラスターの特性と、クラスターの NODE_DISTRIBUTION テーブルにあるすべての情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-222">`GetClusterProfile` returns the characteristics of the cluster, with all the information that is found in the NODE_DISTRIBUTION table for the cluster.</span></span>  
  
-   <span data-ttu-id="a5f6d-223">`GetNodeGraph` では、[シーケンス クラスター] ビューの最初のタブに表示される、クラスターの数学グラフ表現の作成に使用できるノードとエッジが返されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-223">`GetNodeGraph` returns nodes and edges that can be used to construct a mathematical graph representation of the clusters, corresponding to what you see on the first tab of the Sequence Clustering view.</span></span> <span data-ttu-id="a5f6d-224">ノードがクラスターを、エッジが重み (強さ) を表します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-224">The nodes are clusters, and the edges represent weights or strength.</span></span>  
  
 <span data-ttu-id="a5f6d-225">次の例は、システム ストアド プロシージャ `GetClusterProfiles`を使用して、モデル内のすべてのクラスターとそのプロファイルを取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-225">The following example illustrates how to use the system stored procedure, `GetClusterProfiles`, to return all of the clusters in the model, with their respective profiles.</span></span> <span data-ttu-id="a5f6d-226">このストアド プロシージャは、モデル内のプロファイルの完全なセットを返す、一連の DMX ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-226">This stored procedure executes a series of DMX statements that return the complete set of profiles in the model.</span></span> <span data-ttu-id="a5f6d-227">ただし、このストアド プロシージャを使用するには、モデルのアドレスを知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-227">However, to use this stored procedure you must know the address of the model.</span></span>  
  
 `CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterProfiles('Sequence Clustering', 2147483647, 0)`  
  
 <span data-ttu-id="a5f6d-228">次の例は、システム ストアド プロシージャ `GetNodeGraph`でクラスター ID を指定して、特定のクラスター (クラスター 12) のプロファイルを取得する方法を示しています。クラスター ID は、通常、クラスター名に含まれる番号と同じです。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-228">The following example illustrates how to retrieve the profile for a specific cluster, Cluster 12, by using the system stored procedure `GetNodeGraph`, and specifying the cluster ID, which is usually the same as the number in the cluster name.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetNodeGraph('Sequence Clustering','12',0)  
```  
  
 <span data-ttu-id="a5f6d-229">次のクエリに示すようにクラスター ID を省略した場合、 `GetNodeGraph` では、すべてのクラスター プロファイルの順序付けされフラット化された一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-229">If you omit the cluster ID, as shown in the following query, `GetNodeGraph` returns an ordered, flattened list of all cluster profiles:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetNodeGraph('Sequence Clustering','',0)  
```  
  
 <span data-ttu-id="a5f6d-230">**[クラスターのプロファイル]** タブには、モデルのサンプル ケースのヒストグラムも表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-230">The **Cluster Profile** tab also displays a histogram of model sample cases.</span></span> <span data-ttu-id="a5f6d-231">これらのサンプル ケースは、モデルの理想的なケースを表しています。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-231">These sample cases represent the idealized cases for the model.</span></span> <span data-ttu-id="a5f6d-232">これらのケースは、トレーニング データと同じようにはモデルに格納されません。モデルのサンプル ケースを取得するには、特別な構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-232">These cases are not stored in the model the same way that the training data is; you must use a special syntax to retrieve the sample cases for the model.</span></span>  
  
```  
SELECT * FROM [Sequence Clustering].SAMPLE_CASES WHERE IsInNode('12')  
```  
  
 <span data-ttu-id="a5f6d-233">詳細については、「[SELECT FROM &#60;model&#62;.SAMPLE_CASES (DMX)](/sql/dmx/select-from-model-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-233">For more information, see [SELECT FROM &#60;model&#62;.SAMPLE_CASES &#40;DMX&#41;](/sql/dmx/select-from-model-dmx).</span></span>  
  
#### <a name="cluster-characteristics-and-cluster-discrimination"></a><span data-ttu-id="a5f6d-234">クラスターの特性とクラスターの識別</span><span class="sxs-lookup"><span data-stu-id="a5f6d-234">Cluster Characteristics and Cluster Discrimination</span></span>  
 <span data-ttu-id="a5f6d-235">**[クラスターの特性]** タブには、各クラスターの主要な属性が、確率で順位付けされて表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-235">The **Cluster Characteristics** tab summarizes the main attributes of each cluster, ranked by probability.</span></span> <span data-ttu-id="a5f6d-236">クラスターに属するケースの数と、クラスター内のケースの分布について確認できます。各特性には、特定のサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-236">You can find out how many cases belong to a cluster, and what the distribution of cases is like in the cluster: Each characteristic has certain support.</span></span> <span data-ttu-id="a5f6d-237">特定のクラスターの特性を確認するには、クラスターの ID を知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-237">To see the characteristics of a particular cluster, you must know the ID of the cluster.</span></span>  
  
 <span data-ttu-id="a5f6d-238">次の例では、システム ストアド プロシージャ `GetClusterCharacteristics`を使用して、確率スコアが指定したしきい値 0.0005 よりも高い、クラスター 12 の特性をすべて取得します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-238">The following examples uses the system stored procedure, `GetClusterCharacteristics`, to return all the characteristics of Cluster 12 that have a probability score over the specified threshold of 0.0005.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('Sequence Clustering','12',0.0005)  
```  
  
 <span data-ttu-id="a5f6d-239">すべてのクラスターの特性を取得するには、クラスターの ID を空のままにします。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-239">To return the characteristics of all clusters, you can leave the cluster ID empty.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('Sequence Clustering','',0.0005)  
```  
  
 <span data-ttu-id="a5f6d-240">次の例では、システム ストアド プロシージャ `GetClusterDiscrimination` を呼び出して、クラスター 1 とクラスター 12 の特性を比較します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-240">The following example calls the system stored procedure `GetClusterDiscrimination` to compare the characteristics of Cluster 1 and Cluster 12.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('Sequence Clustering','1','12',0.0005,true)  
```  
  
 <span data-ttu-id="a5f6d-241">独自のクエリを DMX で記述して、2 つのクラスターの比較や、あるクラスターと他のすべてのクラスターとの比較を行う場合、まず一方のセットの特性を取得してから、対象の特定クラスターの特性を取得して、2 つのセットを比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-241">If you want to write your own query in DMX to compare two clusters, or compare a cluster with its complement, you must first retrieve one set of characteristics, and then retrieve the characteristics for the specific cluster that you are interested in, and compare the two sets.</span></span> <span data-ttu-id="a5f6d-242">このシナリオは比較的複雑で、通常、クライアント処理を必要とします。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-242">This scenario is more complicated and typically requires some client processing.</span></span>  
  
#### <a name="states-and-transitions"></a><span data-ttu-id="a5f6d-243">状態と遷移</span><span class="sxs-lookup"><span data-stu-id="a5f6d-243">States and Transitions</span></span>  
 <span data-ttu-id="a5f6d-244">Microsoft シーケンス クラスターの **[状態遷移]** タブでは、さまざまなクラスターに関する統計情報を取得および比較する複雑なクエリを、バックエンドで実行します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-244">The **State Transitions** tab of the Microsoft Sequence Clustering performs complicated queries on the back end to retrieve and compare the statistics for different clusters.</span></span> <span data-ttu-id="a5f6d-245">これらの結果を再現するには、比較的複雑なクエリとクライアント処理とを必要とします。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-245">To reproduce these results requires a more complex query and some client processing.</span></span>  
  
 <span data-ttu-id="a5f6d-246">ただし、 [このセクション](#bkmk_ContentQueries)のサンプル クエリ 2 で説明した DMX クエリを使用すると、シーケンスまたは個々の遷移の確率と状態を取得できます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-246">However, you can use the DMX queries described in Example 2 of the section, [Content Queries](#bkmk_ContentQueries), to retrieve probabilities and states for sequences or for individual transitions.</span></span>  
  
## <a name="using-the-model-to-make-predictions"></a><span data-ttu-id="a5f6d-247">モデルを使用した予測</span><span class="sxs-lookup"><span data-stu-id="a5f6d-247">Using the Model to Make Predictions</span></span>  
 <span data-ttu-id="a5f6d-248">シーケンス クラスター モデルの予測クエリでは、他のクラスター モデルで使用される予測関数の多くを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-248">Prediction queries on a sequence clustering model can use many of the prediction functions that are used with other clustering models.</span></span> <span data-ttu-id="a5f6d-249">さらに、特別な予測関数 [PredictSequence (DMX)](/sql/dmx/predictsequence-dmx)を使用すると、提案や次の状態についての予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-249">In addition, you can use the special prediction function, [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx), to make recommendations or to predict next states.</span></span>  
  
###  <a name="sample-query-4-predict-next-state-or-states"></a><a name="bkmk_Query4"></a><span data-ttu-id="a5f6d-250">サンプルクエリ 4: 次の状態を予測する</span><span class="sxs-lookup"><span data-stu-id="a5f6d-250">Sample Query 4: Predict Next State or States</span></span>  
 <span data-ttu-id="a5f6d-251">[PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) 関数を使用すると、ある値に対して、最も可能性の高い次の状態を予測できます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-251">You can use the [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) function to predict the next most likely state, given a value.</span></span> <span data-ttu-id="a5f6d-252">また、複数の次の状態を予測することもできます。たとえば、顧客が購入する可能性のある上位 3 製品の一覧を取得して、推奨製品一覧を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-252">You can also predict multiple next states: for example, you can return a list of the top three products that a customer is likely to purchase, to present a list of recommendations.</span></span>  
  
 <span data-ttu-id="a5f6d-253">次のサンプル クエリは、上位 5 つの予測とその確率を返す単一予測クエリです。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-253">The following sample query is a singleton prediction query that returns the top five predictions, together with their probability.</span></span> <span data-ttu-id="a5f6d-254">入れ子になったテーブルがモデルに含まれているため、予測の実行時には、入れ子になったテーブル `[v Assoc Seq Line Items]`を列参照として使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-254">Because the model includes a nested table, you must use the nested table, `[v Assoc Seq Line Items]`, as the column reference when making predictions.</span></span> <span data-ttu-id="a5f6d-255">また、入れ子になった SELECT ステートメントに示されているように、入力として値を指定するときは、ケース テーブルと入れ子になったテーブルの両方の列を結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-255">Also, when you supply values as input, you must join both the case table and the nested table columns, as shown by the nested SELECT statements.</span></span>  
  
```  
SELECT FLATTENED PredictSequence([v Assoc Seq Line Items], 7)  
FROM [Sequence Clustering]  
NATURAL PREDICTION JOIN  
(SELECT  (SELECT 1 as [Line Number],  
   'All-Purpose Bike Stand' as [Model]) AS [v Assoc Seq Line Items])   
AS t  
```  
  
 <span data-ttu-id="a5f6d-256">結果の例:</span><span class="sxs-lookup"><span data-stu-id="a5f6d-256">Example results:</span></span>  
  
|<span data-ttu-id="a5f6d-257">Expression.$Sequence</span><span class="sxs-lookup"><span data-stu-id="a5f6d-257">Expression.$Sequence</span></span>|<span data-ttu-id="a5f6d-258">Expression.Line 番号</span><span class="sxs-lookup"><span data-stu-id="a5f6d-258">Expression.Line Number</span></span>|<span data-ttu-id="a5f6d-259">Expression.Model</span><span class="sxs-lookup"><span data-stu-id="a5f6d-259">Expression.Model</span></span>|  
|--------------------------|----------------------------|----------------------|  
|<span data-ttu-id="a5f6d-260">1</span><span class="sxs-lookup"><span data-stu-id="a5f6d-260">1</span></span>||<span data-ttu-id="a5f6d-261">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="a5f6d-261">Cycling Cap</span></span>|  
|<span data-ttu-id="a5f6d-262">2</span><span class="sxs-lookup"><span data-stu-id="a5f6d-262">2</span></span>||<span data-ttu-id="a5f6d-263">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="a5f6d-263">Cycling Cap</span></span>|  
|<span data-ttu-id="a5f6d-264">3</span><span class="sxs-lookup"><span data-stu-id="a5f6d-264">3</span></span>||<span data-ttu-id="a5f6d-265">Sport-100</span><span class="sxs-lookup"><span data-stu-id="a5f6d-265">Sport-100</span></span>|  
|<span data-ttu-id="a5f6d-266">4</span><span class="sxs-lookup"><span data-stu-id="a5f6d-266">4</span></span>||<span data-ttu-id="a5f6d-267">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="a5f6d-267">Long-Sleeve logo Jersey</span></span>|  
|<span data-ttu-id="a5f6d-268">5</span><span class="sxs-lookup"><span data-stu-id="a5f6d-268">5</span></span>||<span data-ttu-id="a5f6d-269">Half-Finger Gloves</span><span class="sxs-lookup"><span data-stu-id="a5f6d-269">Half-Finger Gloves</span></span>|  
|<span data-ttu-id="a5f6d-270">6</span><span class="sxs-lookup"><span data-stu-id="a5f6d-270">6</span></span>||<span data-ttu-id="a5f6d-271">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="a5f6d-271">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a5f6d-272">7</span><span class="sxs-lookup"><span data-stu-id="a5f6d-272">7</span></span>||<span data-ttu-id="a5f6d-273">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="a5f6d-273">All-Purpose Bike Stand</span></span>|  
  
 <span data-ttu-id="a5f6d-274">1 列だけを予期したにもかかわらず、結果には 3 列が含まれています。これは、クエリが常にケース テーブルに対する列を返すためです。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-274">There are three columns in the results, even though you might only expect one column, because the query always returns a column for the case table.</span></span> <span data-ttu-id="a5f6d-275">ここでは結果がフラット化されています。フラット化しないと、クエリは、入れ子になったテーブル列 2 列を含む 1 つの列を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-275">Here the results are flattened; otherwise, the query would return a single column that contains two nested table columns.</span></span>  
  
 <span data-ttu-id="a5f6d-276">$sequence 列は、予測結果を並べ替えるために、 `PredictSequence` 関数から既定で返される列です。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-276">The column $sequence is a column returned by default by the `PredictSequence` function to order the prediction results.</span></span> <span data-ttu-id="a5f6d-277">`[Line Number]`列は、モデルのシーケンス キーに一致させる必要がありますが、これらのキーは出力ではありません。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-277">The column, `[Line Number]`, is required to match the sequence keys in the model, but the keys are not output.</span></span>  
  
 <span data-ttu-id="a5f6d-278">興味深いことに、All-Purpose Bike Stand の後の最上位に予測されたシーケンスは、Cycling Cap と Cycling Cap です。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-278">Interestingly, the top predicted sequences after All-Purpose Bike Stand are Cycling Cap and Cycling Cap.</span></span> <span data-ttu-id="a5f6d-279">これはエラーではありません。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-279">This is not an error.</span></span> <span data-ttu-id="a5f6d-280">顧客に対するデータの提示方法や、モデルのトレーニング時のグループ化方法によっては、このようなシーケンスが返されることは珍しくありません。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-280">Depending on how the data is presented to the customer, and how it is grouped when training the model, it is very possible to have sequences of this kind.</span></span> <span data-ttu-id="a5f6d-281">たとえば、1 人の顧客がサイクリング キャップ (赤) の次にもう 1 つサイクリング キャップ (青) を購入することがあります。また、数を指定する方法がない場合、2 つを連続して購入することもあります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-281">For example, a customer might purchase a cycling cap (red) and then another cycling cap (blue), or purchase two in a row if there were no way to specify quantity.</span></span>  
  
 <span data-ttu-id="a5f6d-282">行 6 と行 7 の値はプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-282">The values in rows 6 and 7 are placeholders.</span></span> <span data-ttu-id="a5f6d-283">可能な遷移のチェーンの最後に達しても、予測結果が終了されることはなく、入力として渡された値が結果に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-283">When you reach the end of the chain of possible transitions, rather than terminating the prediction results, the value that was passed as an input is added to the results.</span></span> <span data-ttu-id="a5f6d-284">たとえば、予測の数を 20 に増やした場合、行 6 ～ 20 の値はすべて同じ All-Purpose Bike Stand となります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-284">For example, if you increased the number of predictions to 20, the values for rows 6-20 would all be the same, All-Purpose Bike Stand.</span></span>  
  
## <a name="function-list"></a><span data-ttu-id="a5f6d-285">関数一覧</span><span class="sxs-lookup"><span data-stu-id="a5f6d-285">Function List</span></span>  
 <span data-ttu-id="a5f6d-286">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-286">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="a5f6d-287">ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムでは、次の表に示す追加の関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-287">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5f6d-288">予測関数</span><span class="sxs-lookup"><span data-stu-id="a5f6d-288">Prediction Function</span></span>|<span data-ttu-id="a5f6d-289">使用法</span><span class="sxs-lookup"><span data-stu-id="a5f6d-289">Usage</span></span>|  
|[<span data-ttu-id="a5f6d-290">Cluster &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-290">Cluster &#40;DMX&#41;</span></span>](/sql/dmx/cluster-dmx)|<span data-ttu-id="a5f6d-291">入力したケースを含む可能性の最も高いクラスターを返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-291">Returns the cluster that is most likely to contain the input case</span></span>|  
|[<span data-ttu-id="a5f6d-292">ClusterDistance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-292">ClusterDistance &#40;DMX&#41;</span></span>](/sql/dmx/clusterdistance-dmx)|<span data-ttu-id="a5f6d-293">指定されたクラスターと入力したケース間の距離を返します。ただしクラスターが指定されていない場合は、最も可能性の高いクラスターと入力したケース間の距離を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-293">Returns the distance of the input case from the specified cluster, or if no cluster is specified, the distance of the input case from the most likely cluster.</span></span><br /><br /> <span data-ttu-id="a5f6d-294">この関数は任意の種類のクラスター モデル (EM、K-Means など) と共に使用できますが、結果はアルゴリズムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-294">This function can be used with any kind of clustering model (EM, K-Means, etc.), but the results differ depending on the algorithm.</span></span>|  
|[<span data-ttu-id="a5f6d-295">ClusterProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-295">ClusterProbability &#40;DMX&#41;</span></span>](/sql/dmx/clusterprobability-dmx)|<span data-ttu-id="a5f6d-296">入力ケースが指定されたクラスターに所属する確率を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-296">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="a5f6d-297">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-297">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="a5f6d-298">指定されたノードが現在のケースを含んでいるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-298">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="a5f6d-299">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-299">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="a5f6d-300">指定された状態の調整済みの確率を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-300">Returns the adjusted probability of a specified state.</span></span>|  
|[<span data-ttu-id="a5f6d-301">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-301">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="a5f6d-302">結合メンバーシップを予測します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-302">Predicts associative membership.</span></span>|  
|[<span data-ttu-id="a5f6d-303">PredictCaseLikelihood &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-303">PredictCaseLikelihood &#40;DMX&#41;</span></span>](/sql/dmx/predictcaselikelihood-dmx)|<span data-ttu-id="a5f6d-304">入力したケースが既存のモデル内に収まる確率値を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-304">Returns the likelihood that an input case will fit in the existing model.</span></span>|  
|[<span data-ttu-id="a5f6d-305">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-305">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="a5f6d-306">指定された列の予測のためのヒストグラムを表すテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-306">Returns a table that represents a histogram for the prediction of a given column.</span></span>|  
|[<span data-ttu-id="a5f6d-307">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-307">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="a5f6d-308">ケースが分類されるノードの Node_ID を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-308">Returns the Node_ID of the node to which the case is classified.</span></span>|  
|[<span data-ttu-id="a5f6d-309">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-309">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="a5f6d-310">指定された状態の確率を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-310">Returns the probability for a specified state.</span></span>|  
|[<span data-ttu-id="a5f6d-311">PredictSequence (DMX)</span><span class="sxs-lookup"><span data-stu-id="a5f6d-311">PredictSequence &#40;DMX&#41;</span></span>](/sql/dmx/predictsequence-dmx)|<span data-ttu-id="a5f6d-312">指定された一連のシーケンス データに対して予測される将来のシーケンス値です。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-312">Predicts future sequence values for a specified set of sequence data.</span></span>|  
|[<span data-ttu-id="a5f6d-313">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-313">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="a5f6d-314">指定された列に対して、予測された標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-314">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="a5f6d-315">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-315">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="a5f6d-316">指定された状態に対するサポート値を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-316">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="a5f6d-317">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a5f6d-317">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="a5f6d-318">指定された列の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-318">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="a5f6d-319">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムに共通の関数の一覧については、「[一般的な予測関数 (DMX)](/sql/dmx/general-prediction-functions-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-319">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="a5f6d-320">特定の関数の構文については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5f6d-320">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f6d-321">参照</span><span class="sxs-lookup"><span data-stu-id="a5f6d-321">See Also</span></span>  
 <span data-ttu-id="a5f6d-322">[データマイニングクエリ](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="a5f6d-322">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="a5f6d-323">[Microsoft シーケンスクラスターアルゴリズムテクニカルリファレンス](microsoft-sequence-clustering-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a5f6d-323">[Microsoft Sequence Clustering Algorithm Technical Reference](microsoft-sequence-clustering-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="a5f6d-324">[Microsoft シーケンスクラスターアルゴリズム](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a5f6d-324">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="a5f6d-325">シーケンス クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="a5f6d-325">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)  
  
  
