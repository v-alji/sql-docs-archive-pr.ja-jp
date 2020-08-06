---
title: コンテンツクエリ (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4f4a5a8-a230-4222-bece-9d563501f65f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44b162c34f5f505462a713205d8434484473afa4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645926"
---
# <a name="content-queries-data-mining"></a><span data-ttu-id="cc067-102">コンテンツ クエリ (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="cc067-102">Content Queries (Data Mining)</span></span>
  <span data-ttu-id="cc067-103">コンテンツ クエリは、マイニング モデルの内部の統計および構造に関する情報を抽出するための手段です。</span><span class="sxs-lookup"><span data-stu-id="cc067-103">A content query is a way of extracting information about the internal statistics and structure of the mining model.</span></span> <span data-ttu-id="cc067-104">コンテンツ クエリを使用すると、ビューアーでは簡単に得られない詳細な情報がわかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc067-104">Sometimes a content query can provide details that are not readily available in the viewer.</span></span> <span data-ttu-id="cc067-105">また、コンテンツ クエリの結果を利用して、他の用途のためにプログラムで情報を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-105">You can also use the results of a content query to extract information programmatically for other uses.</span></span>  
  
 <span data-ttu-id="cc067-106">ここでは、コンテンツ クエリを使用して取得できる情報の種類に関する一般的な情報と、コンテンツ クエリの一般的な DMX 構文を紹介します。</span><span class="sxs-lookup"><span data-stu-id="cc067-106">This section provides general information about the types of information that you can retrieve by using a content query, and the general DMX syntax for content queries.</span></span>  
  
 [<span data-ttu-id="cc067-107">基本的なコンテンツ クエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-107">Basic Content Queries</span></span>](#bkmk_ContentQuery)  
  
-   [<span data-ttu-id="cc067-108">構造およびケースデータに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-108">Queries on Structure and Case Data</span></span>](#bkmk_Structure)  
  
-   [<span data-ttu-id="cc067-109">モデル パターンに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-109">Queries on Model Patterns</span></span>](#bkmk_Patterns)  
  
 [<span data-ttu-id="cc067-110">使用例</span><span class="sxs-lookup"><span data-stu-id="cc067-110">Examples</span></span>](#bkmk_Examples)  
  
-   [<span data-ttu-id="cc067-111">アソシエーション モデルに対するコンテンツ クエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-111">Content Query on an Association Model</span></span>](#bkmk_Assoc)  
  
-   [<span data-ttu-id="cc067-112">デシジョン ツリー モデルに対するコンテンツ クエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-112">Content Query on a Decision Trees Model</span></span>](#bkmk_DecTree)  
  
 [<span data-ttu-id="cc067-113">クエリ結果の操作</span><span class="sxs-lookup"><span data-stu-id="cc067-113">Working with the Query Results</span></span>](#bkmk_Results)  
  
##  <a name="basic-content-queries"></a><a name="bkmk_ContentQuery"></a><span data-ttu-id="cc067-114">基本的なコンテンツクエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-114">Basic Content Queries</span></span>  
 <span data-ttu-id="cc067-115">コンテンツ クエリは、予測クエリ ビルダーを使用しても作成できます。SQL Server Management Studio で提供される DMX コンテンツ クエリ テンプレートを使用するか、DMX に直接クエリを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="cc067-115">You can create content queries by using the Prediction Query Builder, use the DMX content query templates that are provided in SQL Server Management Studio, or write queries directly in DMX.</span></span> <span data-ttu-id="cc067-116">コンテンツ クエリは、予測クエリと異なり、外部データを結合する必要がないため、簡単に書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cc067-116">Unlike prediction queries you do not need to join external data, so content queries are easy to write.</span></span>  
  
 <span data-ttu-id="cc067-117">ここでは、作成できるコンテンツ クエリの種類の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc067-117">This section provides an overview of the types of content queries you can create.</span></span>  
  
-   <span data-ttu-id="cc067-118">マイニング構造またはケース データに対するクエリでは、トレーニングに使用された詳細なデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-118">Queries on the mining structure or case data let you view the detailed data that was used for training.</span></span>  
  
-   <span data-ttu-id="cc067-119">モデルに対するクエリでは、パターン、属性一覧、数式などが返されます。</span><span class="sxs-lookup"><span data-stu-id="cc067-119">Queries on the model can return patterns, lists of attributes, formulas, and so forth.</span></span>  
  
###  <a name="queries-on-structure-and-case-data"></a><a name="bkmk_Structure"></a> <span data-ttu-id="cc067-120">構造およびケース データに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-120">Queries on Structure and Case Data</span></span>  
 <span data-ttu-id="cc067-121">DMX では、マイニング構造およびモデルの構築に使用されるキャッシュ データに対するクエリをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="cc067-121">DMX supports queries on the cached data that is used to build mining structures and models.</span></span> <span data-ttu-id="cc067-122">既定では、このキャッシュは、マイニング構造が定義されると作成され、構造またはモデルが処理されると値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="cc067-122">By default, this cache is created when you define the mining structure, and is populated when you process the structure or model.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="cc067-123">データをトレーニング セットとテスト セットに分割する必要がある場合は、このキャッシュを消去または削除できません。</span><span class="sxs-lookup"><span data-stu-id="cc067-123">This cache cannot be cleared or deleted if you need to separate data into training and testing sets.</span></span> <span data-ttu-id="cc067-124">キャッシュを消去すると、ケース データに対するクエリを実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cc067-124">If the cache is cleared, you cannot query the case data.</span></span>  
  
 <span data-ttu-id="cc067-125">次の例は、ケース データに対するクエリ、またはマイニング構造のデータに対するクエリを作成するときに共通するパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="cc067-125">The following examples show the common patterns for creating queries on the case data, or queries on the data in the mining structure:</span></span>  
  
 <span data-ttu-id="cc067-126">**モデルのすべてのケースを取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-126">**Get all the cases for a model**</span></span>  
 `SELECT FROM <model>.CASES`  
  
 <span data-ttu-id="cc067-127">このステートメントを使用すると、モデルの構築に使用されたケース データから指定した列を所得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-127">Use this statement to retrieve specified columns from the case data used to build a model.</span></span> <span data-ttu-id="cc067-128">このクエリを実行するには、モデルのドリルスルー権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc067-128">You must have drillthrough permissions on the model to run this query.</span></span>  
  
 <span data-ttu-id="cc067-129">**構造に含まれているすべてのデータを表示する**</span><span class="sxs-lookup"><span data-stu-id="cc067-129">**View all the data that is included in the structure**</span></span>  
 `SELECT FROM <structure>.CASES`  
  
 <span data-ttu-id="cc067-130">このステートメントを使用すると、特定のマイニング モデルには含まれていない列も含め、構造に含まれているデータをすべて表示できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-130">Use this statement to view all the data that is included in the structure, including columns that are not included in a particular mining model.</span></span> <span data-ttu-id="cc067-131">マイニング構造からデータを取得するには、モデルと構造の両方に対するドリルスルー権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc067-131">You must have drillthrough permissions on the model, as well as on the structure, to retrieve data from the mining structure.</span></span>  
  
 <span data-ttu-id="cc067-132">**値の範囲を取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-132">**Get range of values**</span></span>  
 `SELECT DISTINCT RangeMin(<column>), RangeMax(<column>) FROM <model>`  
  
 <span data-ttu-id="cc067-133">このステートメントを使用すると、連続列または DISCRETIZED 列のバケットの最小値、最大値、および平均を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-133">Use this statement to find the minimum value, maximum value, and mean of a continuous column, or of the buckets of a DISCRETIZED column.</span></span>  
  
 <span data-ttu-id="cc067-134">**個別の値を取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-134">**Get distinct values**</span></span>  
 `SELECT DISTINCT <column>FROM <model>`  
  
 <span data-ttu-id="cc067-135">このステートメントを使用すると、DISCRETE 列のすべての値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-135">Use this statement to retrieve all the values of a DISCRETE column.</span></span>  <span data-ttu-id="cc067-136">DISCRETIZED 列に対してはこのステートメントを使用せずに、`RangeMin` 関数および `RangeMax` 関数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="cc067-136">Do not use this statement for DISCRETIZED columns; use the `RangeMin` and `RangeMax` functions instead.</span></span>  
  
 <span data-ttu-id="cc067-137">**モデルまたは構造のトレーニングに使用されたケースを取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-137">**Find the cases that were used to train a model or structure**</span></span>  
 `SELECT  FROM <mining structure.CASES WHERE IsTrainingCase()`  
  
 <span data-ttu-id="cc067-138">このステートメントを使用すると、モデルのトレーニングに使用されたデータの完全なセットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-138">Use this statement to get the complete set of data that was used in a training a model.</span></span>  
  
 <span data-ttu-id="cc067-139">**モデルまたは構造のテストに使用されたケースを取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-139">**Find the cases that are used for testing a model or structure**</span></span>  
 `SELECT  FROM <mining structure.CASES WHERE IsTestingCase()`  
  
 <span data-ttu-id="cc067-140">このステートメントを使用すると、特定の構造に関連するマイニング モデルのテスト用に確保されているデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-140">Use this statement to get the data that has been set aside for testing mining models related to a specific structure.</span></span>  
  
 <span data-ttu-id="cc067-141">**特定のモデル パターンから基になるケース データにドリルスルーする**</span><span class="sxs-lookup"><span data-stu-id="cc067-141">**Drillthrough from a specific model pattern to underlying case data**</span></span>  
 `SELECT FROM <model>.CASESWHERE IsTrainingCase() AND IsInNode(<node>)`  
  
 <span data-ttu-id="cc067-142">このステートメントを使用すると、トレーニング済みのモデルから詳細なケース データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-142">Use this statement to retrieve detailed case data from a trained model.</span></span> <span data-ttu-id="cc067-143">特定のノードを指定する必要があります。たとえば、クラスターのノード ID、デシジョン ツリーの特定の分岐などを認識している必要があります。また、このクエリを実行するには、モデルのドリルスルー権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc067-143">You must specify a specific node: for example, you must know the node ID of the cluster, the specific branch of the decision tree, etc. Moreover, you must have drillthrough permissions on the model to run this query.</span></span>  
  
###  <a name="queries-on-model-patterns-statistics-and-attributes"></a><a name="bkmk_Patterns"></a><span data-ttu-id="cc067-144">モデルパターン、統計、および属性に対するクエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-144">Queries on Model Patterns, Statistics, and Attributes</span></span>  
 <span data-ttu-id="cc067-145">データ マイニング モデルのコンテンツは、多くの目的で役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="cc067-145">The content of a data mining model is useful for many purposes.</span></span> <span data-ttu-id="cc067-146">モデル コンテンツのクエリを使用すると、以下の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-146">With a model content query, you can:</span></span>  
  
-   <span data-ttu-id="cc067-147">独自の計算を行うために式または確率を抽出します。</span><span class="sxs-lookup"><span data-stu-id="cc067-147">Extract formulas or probabilities for making your own calculations.</span></span>  
  
-   <span data-ttu-id="cc067-148">アソシエーション モデルでは、予測の生成に使用される規則を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc067-148">For an association model, retrieve the rules that are used to generate a prediction.</span></span>  
  
-   <span data-ttu-id="cc067-149">特定のルールをカスタム アプリケーションで使用できるようにそのルールの説明を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc067-149">Retrieve the descriptions of specific rules so that you can use the rules in a custom application.</span></span>  
  
-   <span data-ttu-id="cc067-150">時系列モデルで検出された移動平均を表示します。</span><span class="sxs-lookup"><span data-stu-id="cc067-150">View the moving averages detected by a time series model.</span></span>  
  
-   <span data-ttu-id="cc067-151">傾向線のセグメントの回帰式を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc067-151">Obtain the regression formula for some segment of the trend line.</span></span>  
  
-   <span data-ttu-id="cc067-152">特定のクラスターの一部として識別された顧客に関する実用的な情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc067-152">Retrieve actionable information about customers identified as being part of a specific cluster.</span></span>  
  
 <span data-ttu-id="cc067-153">次の例は、モデル コンテンツに対するクエリの作成に共通するパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="cc067-153">The following examples show some of the common patterns for creating queries on the model content:</span></span>  
  
 <span data-ttu-id="cc067-154">**モデルからパターンを取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-154">**Get patterns from the model**</span></span>  
 `SELECT FROM <model>.CONTENT`  
  
 <span data-ttu-id="cc067-155">このステートメントを使用すると、モデル内の特定のノードに関する詳細情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-155">Use this statement to retrieve detailed information about specific nodes in the model.</span></span> <span data-ttu-id="cc067-156">ノードには、アルゴリズムの種類に応じて、ルールと式、サポート、分散の統計情報などが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc067-156">Depending on the algorithm type, the node can contain rules and formulas, support and variance statistics, and so forth.</span></span>  
  
 <span data-ttu-id="cc067-157">**トレーニング済みのモデルで使用された属性を取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-157">**Retrieve attributes used in a trained model**</span></span>  
 `CALL System.GetModelAttributes(<model>)`  
  
 <span data-ttu-id="cc067-158">このストアド プロシージャを使用すると、モデルによって使用された属性の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-158">Use this stored procedure to retrieve the list of attributes that were used by a model.</span></span> <span data-ttu-id="cc067-159">たとえば、この情報は、機能を選択したために除外された属性を特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cc067-159">This information is useful for determining attributes that were eliminated as a result of feature selection, for example.</span></span>  
  
 <span data-ttu-id="cc067-160">**データ マイニング ディメンションに格納されているコンテンツを取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-160">**Retrieve content stored in a data mining dimension**</span></span>  
 `SELECT FROM <model>.DIMENSIONCONTENT`  
  
 <span data-ttu-id="cc067-161">このステートメントを使用すると、データ マイニング ディメンションからデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-161">Use this statement to retrieve the data from a data mining dimension.</span></span>  
  
 <span data-ttu-id="cc067-162">この種類のクエリは主に、内部で使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="cc067-162">This query type is principally for internal use.</span></span> <span data-ttu-id="cc067-163">ただし、この機能はすべてのアルゴリズムでサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="cc067-163">However, not all algorithms support this functionality.</span></span> <span data-ttu-id="cc067-164">サポートされているかどうかは、MINING_SERVICES スキーマ行セット内のフラグで示されます。</span><span class="sxs-lookup"><span data-stu-id="cc067-164">Support is indicated by a flag in the MINING_SERVICES schema rowset.</span></span>  
  
 <span data-ttu-id="cc067-165">独自のプラグイン アルゴリズムを開発する場合は、このステートメントを使用してテスト用のモデルのコンテンツを確認できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-165">If you develop your own plug-in algorithm, you might use this statement to verify the content of your model for testing.</span></span>  
  
 <span data-ttu-id="cc067-166">**モデルの PMML 表現を取得する**</span><span class="sxs-lookup"><span data-stu-id="cc067-166">**Get the PMML representation of a model**</span></span>  
 `SELECT * FROM <model>.PMML`  
  
 <span data-ttu-id="cc067-167">PMML 形式でモデルを表す XML ドキュメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc067-167">Gets an XML document that represents the model in PMML format.</span></span> <span data-ttu-id="cc067-168">すべてのモデルの種類がサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="cc067-168">Not all model types are supported.</span></span>  
  
##  <a name="examples"></a><a name="bkmk_Examples"></a> <span data-ttu-id="cc067-169">使用例</span><span class="sxs-lookup"><span data-stu-id="cc067-169">Examples</span></span>  
 <span data-ttu-id="cc067-170">すべてのアルゴリズムに対して標準であるようなモデル コンテンツもありますが、一部のコンテンツは、そのモデルの構築に使用したアルゴリズムによってかなり異なります。</span><span class="sxs-lookup"><span data-stu-id="cc067-170">Although some model content is standard across algorithms, some parts of the content vary greatly depending on the algorithm that you used to build the model.</span></span> <span data-ttu-id="cc067-171">したがって、コンテンツ クエリを作成する際には、特定のモデルに関してどのような情報が最も有用であるかを把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc067-171">Therefore, when you create a content query, you must understand what information in the model is most useful to your specific model.</span></span>  
  
 <span data-ttu-id="cc067-172">ここでは、アルゴリズムの選択がモデルに保存されている情報の種類にどのように影響するかを、例を使用して説明します。</span><span class="sxs-lookup"><span data-stu-id="cc067-172">A few examples are provided in this section to illustrate how the choice of algorithm affects the kind of information that is stored in the model.</span></span> <span data-ttu-id="cc067-173">マイニング モデル コンテンツ、および各種のモデルに特有のコンテンツの詳細については、「[マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc067-173">For more information about mining model content, and the content that is specific to each model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
###  <a name="example-1-content-query-on-an-association-model"></a><a name="bkmk_Assoc"></a> <span data-ttu-id="cc067-174">例 1: アソシエーション モデルに対するコンテンツ クエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-174">Example 1: Content Query on an Association Model</span></span>  
 <span data-ttu-id="cc067-175">`SELECT FROM <model>.CONTENT`ステートメントは、クエリの対象となるモデルの種類に応じてさまざまな種類の情報を返します。</span><span class="sxs-lookup"><span data-stu-id="cc067-175">The statement, `SELECT FROM <model>.CONTENT`, returns different kinds of information, depending on the type of model you are querying.</span></span> <span data-ttu-id="cc067-176">アソシエーション モデルの場合、重要な情報は *ノード型*です。</span><span class="sxs-lookup"><span data-stu-id="cc067-176">For an association model, a key piece of information is the *node type*.</span></span> <span data-ttu-id="cc067-177">ノードは、モデル コンテンツの情報のコンテナーのようなものです。</span><span class="sxs-lookup"><span data-stu-id="cc067-177">Nodes are like containers for information in the model content.</span></span> <span data-ttu-id="cc067-178">アソシエーション モデルでは、ルールを表すノードは NODE_TYPE の値が 8 で、アイテムセットを表すノードは NODE_TYPE の値が 7 です。</span><span class="sxs-lookup"><span data-stu-id="cc067-178">In an association model, nodes that represent rules have a NODE_TYPE value of 8, whereas nodes that represent itemsets have a NODE_TYPE value of 7.</span></span>  
  
 <span data-ttu-id="cc067-179">したがって、次のクエリでは、サポートで順位付けされた (既定の順序) 上位 10 個のアイテムセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="cc067-179">Thus, the following query returns the top 10 itemsets, ranked by support (the default ordering).</span></span>  
  
```  
SELECT TOP 10 NODE_DESCRIPTION, NODE_PROBABILITY, SUPPORT  
FROM <model>.CONTENT WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="cc067-180">次のクエリはこの情報に対して構築されます。</span><span class="sxs-lookup"><span data-stu-id="cc067-180">The following query builds on this information.</span></span> <span data-ttu-id="cc067-181">このクエリでは、ノードの ID、完全なルール、およびアイテムセットの右辺の製品 (アイテムセットの一部として他の製品に関連付けられていることが予測された製品) の3つの列が返されます。</span><span class="sxs-lookup"><span data-stu-id="cc067-181">The query returns three columns: the ID of the node, the complete rule, and the product on the right-hand side of the itemset-that is, the product that is predicted to be associated with some other products as part of an itemset.</span></span>  
  
```  
SELECT FLATTENED NODE_UNIQUE_NAME, NODE_DESCRIPTION,  
     (SELECT RIGHT(ATTRIBUTE_NAME, (LEN(ATTRIBUTE_NAME)-LEN('Association model name')))   
FROM NODE_DISTRIBUTION  
WHERE LEN(ATTRIBUTE_NAME)>2  
)   
AS RightSideProduct  
FROM [<Association model name>].CONTENT  
WHERE NODE_TYPE = 8   
ORDER BY NODE_SUPPORT DESC  
```  
  
 <span data-ttu-id="cc067-182">FLATTENED キーワードは、入れ子になった行セットをフラット テーブルに変換することを示します。</span><span class="sxs-lookup"><span data-stu-id="cc067-182">The FLATTENED keyword indicates that the nested rowset should be converted into a flattened table.</span></span> <span data-ttu-id="cc067-183">ルールの右辺の製品を表す属性は、NODE_DISTRIBUTION テーブルに含まれています。したがって、長さが 2 より大きいという要件を追加して、属性名を含む行のみを取得しています。</span><span class="sxs-lookup"><span data-stu-id="cc067-183">The attribute that represents the product on the right-hand side of the rule is contained in the NODE_DISTRIBUTION table; therefore, we retrieve only the row that contains an attribute name, by adding a requirement that the length be greater than 2.</span></span>  
  
 <span data-ttu-id="cc067-184">また、単純な文字列関数を使用して、3 番目の列からモデルの名前を削除しています</span><span class="sxs-lookup"><span data-stu-id="cc067-184">A simple string function is used to remove the name of the model from the third column.</span></span> <span data-ttu-id="cc067-185">(通常、モデル名は入れ子になった列の値の先頭に含まれています)。</span><span class="sxs-lookup"><span data-stu-id="cc067-185">(Usually the model name is prefixed to the values of nested columns.)</span></span>  
  
 <span data-ttu-id="cc067-186">WHERE 句で NODE_TYPE の値を 8 として指定して、ルールのみを取得しています。</span><span class="sxs-lookup"><span data-stu-id="cc067-186">The WHERE clause specifies that the value of NODE_TYPE should be 8, to retrieve only rules.</span></span>  
  
 <span data-ttu-id="cc067-187">例については、「 [結合モデルのクエリ例](association-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc067-187">For more examples, see [Association Model Query Examples](association-model-query-examples.md).</span></span>  
  
###  <a name="example-2-content-query-on-a-decision-trees-model"></a><a name="bkmk_DecTree"></a> <span data-ttu-id="cc067-188">例 2: デシジョン ツリー モデルに対するコンテンツ クエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-188">Example 2: Content Query on a Decision Trees Model</span></span>  
 <span data-ttu-id="cc067-189">デシジョン ツリー モデルは、予測や分類のために使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-189">A decision tree model can be used for prediction as well as for classification.</span></span>  <span data-ttu-id="cc067-190">この例では、結果を予測するためにモデルを使用していますが、結果の分類に使用できる要因またはルールを見つけることもできます。</span><span class="sxs-lookup"><span data-stu-id="cc067-190">This example assumes that you are using the model to predict an outcome, but you also want to find out which factors or rules can be used to classify the outcome.</span></span>  
  
 <span data-ttu-id="cc067-191">デシジョン ツリー モデルでは、ノードはツリーとリーフ ノードの両方を表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc067-191">In a decision tree model, nodes are used to represent both trees and leaf nodes.</span></span> <span data-ttu-id="cc067-192">各ノードのキャプションに結果へのパスの説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc067-192">The caption for each node contains the description of the path to the outcome.</span></span> <span data-ttu-id="cc067-193">したがって、特定の結果のパスをトレースするには、そのパスを含むノードを識別して、そのノードの詳細を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc067-193">Therefore, to trace the path for any particular outcome, you need to identify the node that contains it, and get the details for that node.</span></span>  
  
 <span data-ttu-id="cc067-194">予測クエリでは、次の例のように、予測関数 [PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx) を追加して関連するノードの ID を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-194">In your prediction query, you add the prediction function [PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx), to get the ID of the related node, as shown in the following example:</span></span>  
  
```  
SELECT  Predict([Bike Buyer]), PredictNodeID([Bike Buyer])   
FROM [<decision tree model name>]  
PREDICTION JOIN   
<input rowset>   
```  
  
 <span data-ttu-id="cc067-195">結果を含むノードの ID がわかれば、次のように NODE_CAPTION を含むコンテンツ クエリを作成して、その予測を説明するルール (パス) を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc067-195">Once you have the ID of the node that contains the outcome, you can retrieve the rule or path that explains the prediction by creating a content query that includes the NODE_CAPTION, as follows:</span></span>  
  
```  
SELECT NODE_CAPTION  
FROM [<decision tree model name>]   
WHERE NODE_UNIQUE_NAME= '<node id>'  
```  
  
 <span data-ttu-id="cc067-196">例については、「 [デシジョン ツリー モデルのクエリ例](decision-trees-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc067-196">For more examples, see [Decision Trees Model Query Examples](decision-trees-model-query-examples.md).</span></span>  
  
##  <a name="working-with-the-query-results"></a><a name="bkmk_Results"></a><span data-ttu-id="cc067-197">クエリ結果の操作</span><span class="sxs-lookup"><span data-stu-id="cc067-197">Working with the Query Results</span></span>  
 <span data-ttu-id="cc067-198">例が示すように、多くの場合、コンテンツ クエリは表形式の行セットを返しますが、入れ子になった列からの情報も含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc067-198">As the examples demonstrate, content queries mostly return tabular rowsets, but can also include information from nested columns.</span></span> <span data-ttu-id="cc067-199">返された行セットはフラット化できますが、結果の操作が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="cc067-199">You can flatten the rowset that is returned, but this can make working with results more complex.</span></span> <span data-ttu-id="cc067-200">特に、NODE_DISTRIBUTION ノードのコンテンツはネスト化されていますが、モデルに関して非常に興味深い情報を含みます。</span><span class="sxs-lookup"><span data-stu-id="cc067-200">The content of the NODE_DISTRIBUTION node in particular is nested, but contains much interesting information about the model.</span></span>  
  
 <span data-ttu-id="cc067-201">階層的な行セットの操作方法の詳細については、MSDN で OLEDB の仕様を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc067-201">For more information about how to work with hierarchical rowsets, see the OLEDB specification on MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc067-202">参照</span><span class="sxs-lookup"><span data-stu-id="cc067-202">See Also</span></span>  
 <span data-ttu-id="cc067-203">[DMX Select ステートメントについて](/sql/dmx/understanding-the-dmx-select-statement) </span><span class="sxs-lookup"><span data-stu-id="cc067-203">[Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement) </span></span>  
 [<span data-ttu-id="cc067-204">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="cc067-204">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
