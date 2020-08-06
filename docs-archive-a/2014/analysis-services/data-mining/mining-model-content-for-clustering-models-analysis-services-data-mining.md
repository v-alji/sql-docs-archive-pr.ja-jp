---
title: クラスターモデルのマイニングモデルコンテンツ (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nearest neighbor [Data Mining]
- clustering [Data Mining]
- mining model content, clustering models
- clustering algorithms [Analysis Services]
ms.assetid: aed1b7d3-8f20-4eeb-b156-0229f942cefd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 400575d5c6ce8094b67500d15a86137302282fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639799"
---
# <a name="mining-model-content-for-clustering-models-analysis-services---data-mining"></a><span data-ttu-id="b2e81-102">クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="b2e81-102">Mining Model Content for Clustering Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="b2e81-103">このトピックでは、Microsoft クラスタリング アルゴリズムを使用するモデルに固有のマイニング モデル コンテンツについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-103">This topic describes mining model content that is specific to models that use the Microsoft Clustering algorithm.</span></span> <span data-ttu-id="b2e81-104">すべての種類のモデルのマイニング モデル コンテンツの一般的な説明については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」 (マイニング モデル コンテンツ (Analysis Services - データ マイニング)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2e81-104">For a general explanation of mining model content for all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-clustering-model"></a><span data-ttu-id="b2e81-105">クラスター モデルの構造について</span><span class="sxs-lookup"><span data-stu-id="b2e81-105">Understanding the Structure of a Clustering Model</span></span>  
 <span data-ttu-id="b2e81-106">クラスター モデルの構造は単純です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-106">A clustering model has a simple structure.</span></span> <span data-ttu-id="b2e81-107">モデルとそのメタデータを表す 1 つの親ノードが各モデルにあり、各親ノードにはクラスターのフラット リストがあります (NODE_TYPE = 5)。</span><span class="sxs-lookup"><span data-stu-id="b2e81-107">Each model has a single parent node that represents the model and its metadata, and each parent node has a flat list of clusters (NODE_TYPE = 5).</span></span> <span data-ttu-id="b2e81-108">この組織は次の図に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-108">This organization is shown in the following image.</span></span>  
  
 <span data-ttu-id="b2e81-109">![クラスターのモデル コンテンツの構造](../media/modelcontentstructure-clust.gif "クラスターのモデル コンテンツの構造")</span><span class="sxs-lookup"><span data-stu-id="b2e81-109">![structure of model content for clustering](../media/modelcontentstructure-clust.gif "structure of model content for clustering")</span></span>  
  
 <span data-ttu-id="b2e81-110">各子ノードは 1 つのクラスターを表し、そのクラスター内のケースの属性に関する詳細な統計を格納しています</span><span class="sxs-lookup"><span data-stu-id="b2e81-110">Each child node represents a single cluster and contains detailed statistics about the attributes of the cases in that cluster.</span></span> <span data-ttu-id="b2e81-111">(クラスター内のケースの数や、クラスターを他のクラスターから区別する値の分布など)。</span><span class="sxs-lookup"><span data-stu-id="b2e81-111">This includes a count of the number of cases in the cluster, and the distribution of values that distinguish the cluster from other clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2e81-112">クラスターのカウントや説明を取得するためにノードを反復処理する必要はありません。クラスターのカウントと一覧はモデルの親ノードにも含まれています。</span><span class="sxs-lookup"><span data-stu-id="b2e81-112">You do not need to iterate through the nodes to get a count or description of the clusters; the model parent node also counts and lists the clusters.</span></span>  
  
 <span data-ttu-id="b2e81-113">親ノードには、すべてのトレーニング ケースの実際の分布を表す便利な統計も含まれています。</span><span class="sxs-lookup"><span data-stu-id="b2e81-113">The parent node contains useful statistics that describe the actual distribution of all the training cases.</span></span> <span data-ttu-id="b2e81-114">これらの統計は、入れ子になったテーブル列である NODE_DISTRIBUTION に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b2e81-114">These statistics are found in the nested table column, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="b2e81-115">たとえば次の表は、「 `TM_Clustering`基本的なデータ マイニング チュートリアル [」で作成したクラスター モデル (](../../tutorials/basic-data-mining-tutorial.md)) の顧客の人口統計の分布を表す NODE_DISTRIBUTION テーブルのいくつかの行を示しています。</span><span class="sxs-lookup"><span data-stu-id="b2e81-115">For example, the following table shows several rows from the NODE_DISTRIBUTION table that describe the distribution of customer demographics for the clustering model, `TM_Clustering`, that you create in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md):</span></span>  
  
|<span data-ttu-id="b2e81-116">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="b2e81-116">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="b2e81-117">ATRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="b2e81-117">ATRIBUTE_VALUE</span></span>|<span data-ttu-id="b2e81-118">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="b2e81-118">SUPPORT</span></span>|<span data-ttu-id="b2e81-119">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b2e81-119">PROBABILITY</span></span>|<span data-ttu-id="b2e81-120">variance</span><span class="sxs-lookup"><span data-stu-id="b2e81-120">VARIANCE</span></span>|<span data-ttu-id="b2e81-121">VALUE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b2e81-121">VALUE_TYPE</span></span>|  
|---------------------|---------------------|-------------|-----------------|--------------|-----------------|  
|<span data-ttu-id="b2e81-122">年齢</span><span class="sxs-lookup"><span data-stu-id="b2e81-122">Age</span></span>|<span data-ttu-id="b2e81-123">Missing</span><span class="sxs-lookup"><span data-stu-id="b2e81-123">Missing</span></span>|<span data-ttu-id="b2e81-124">0</span><span class="sxs-lookup"><span data-stu-id="b2e81-124">0</span></span>|<span data-ttu-id="b2e81-125">0</span><span class="sxs-lookup"><span data-stu-id="b2e81-125">0</span></span>|<span data-ttu-id="b2e81-126">0</span><span class="sxs-lookup"><span data-stu-id="b2e81-126">0</span></span>|<span data-ttu-id="b2e81-127">1 (Missing: 不足)</span><span class="sxs-lookup"><span data-stu-id="b2e81-127">1 (Missing)</span></span>|  
|<span data-ttu-id="b2e81-128">年齢</span><span class="sxs-lookup"><span data-stu-id="b2e81-128">Age</span></span>|<span data-ttu-id="b2e81-129">44.9016152716593</span><span class="sxs-lookup"><span data-stu-id="b2e81-129">44.9016152716593</span></span>|<span data-ttu-id="b2e81-130">12939</span><span class="sxs-lookup"><span data-stu-id="b2e81-130">12939</span></span>|<span data-ttu-id="b2e81-131">1</span><span class="sxs-lookup"><span data-stu-id="b2e81-131">1</span></span>|<span data-ttu-id="b2e81-132">125.663453102554</span><span class="sxs-lookup"><span data-stu-id="b2e81-132">125.663453102554</span></span>|<span data-ttu-id="b2e81-133">3 (Continuous: 連続)</span><span class="sxs-lookup"><span data-stu-id="b2e81-133">3 (Continuous)</span></span>|  
|<span data-ttu-id="b2e81-134">性別</span><span class="sxs-lookup"><span data-stu-id="b2e81-134">Gender</span></span>|<span data-ttu-id="b2e81-135">Missing</span><span class="sxs-lookup"><span data-stu-id="b2e81-135">Missing</span></span>|<span data-ttu-id="b2e81-136">0</span><span class="sxs-lookup"><span data-stu-id="b2e81-136">0</span></span>|<span data-ttu-id="b2e81-137">0</span><span class="sxs-lookup"><span data-stu-id="b2e81-137">0</span></span>|<span data-ttu-id="b2e81-138">0</span><span class="sxs-lookup"><span data-stu-id="b2e81-138">0</span></span>|<span data-ttu-id="b2e81-139">1 (Missing: 不足)</span><span class="sxs-lookup"><span data-stu-id="b2e81-139">1 (Missing)</span></span>|  
|<span data-ttu-id="b2e81-140">性別</span><span class="sxs-lookup"><span data-stu-id="b2e81-140">Gender</span></span>|<span data-ttu-id="b2e81-141">F</span><span class="sxs-lookup"><span data-stu-id="b2e81-141">F</span></span>|<span data-ttu-id="b2e81-142">6350</span><span class="sxs-lookup"><span data-stu-id="b2e81-142">6350</span></span>|<span data-ttu-id="b2e81-143">0.490764355823479</span><span class="sxs-lookup"><span data-stu-id="b2e81-143">0.490764355823479</span></span>|<span data-ttu-id="b2e81-144">0</span><span class="sxs-lookup"><span data-stu-id="b2e81-144">0</span></span>|<span data-ttu-id="b2e81-145">4 (Discrete: 不連続)</span><span class="sxs-lookup"><span data-stu-id="b2e81-145">4 (Discrete)</span></span>|  
|<span data-ttu-id="b2e81-146">性別</span><span class="sxs-lookup"><span data-stu-id="b2e81-146">Gender</span></span>|<span data-ttu-id="b2e81-147">M</span><span class="sxs-lookup"><span data-stu-id="b2e81-147">M</span></span>|<span data-ttu-id="b2e81-148">6589</span><span class="sxs-lookup"><span data-stu-id="b2e81-148">6589</span></span>|<span data-ttu-id="b2e81-149">0.509235644176521</span><span class="sxs-lookup"><span data-stu-id="b2e81-149">0.509235644176521</span></span>|<span data-ttu-id="b2e81-150">0</span><span class="sxs-lookup"><span data-stu-id="b2e81-150">0</span></span>|<span data-ttu-id="b2e81-151">4 (Discrete: 不連続)</span><span class="sxs-lookup"><span data-stu-id="b2e81-151">4 (Discrete)</span></span>|  
  
 <span data-ttu-id="b2e81-152">これらの結果から、モデルの作成に 12939 個のケースが使用されたこと、男女の比率がほぼ半々であること、および平均年齢が 44 歳であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="b2e81-152">From these results, you can see that there were 12939 cases used to build the model, that the ratio of males to females was about 50-50, and that the mean age was 44.</span></span> <span data-ttu-id="b2e81-153">説明的な統計情報は、レポートされる属性が連続する数値データ型 (年齢など) か不連続値型 (性別など) かによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b2e81-153">The descriptive statistics vary depending on whether the attribute being reported is a continuous numeric data type, such as age, or a discrete value type, such as gender.</span></span> <span data-ttu-id="b2e81-154">統計的尺度の *平均* および *分散* は連続するデータ型に対して計算され、 *確率* および *サポート* は不連続のデータ型に対して計算されます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-154">The statistical measures *mean* and *variance* are computed for continuous data types, whereas *probability* and *support* are computed for discrete data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2e81-155">分散は、クラスターの全分散を表します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-155">The variance represents the total variance for the cluster.</span></span> <span data-ttu-id="b2e81-156">分散の値が小さい場合は、その列のほとんどの値が平均にきわめて近いことになります。</span><span class="sxs-lookup"><span data-stu-id="b2e81-156">When the value for variance is small, it indicates that most values in the column were fairly close to the mean.</span></span> <span data-ttu-id="b2e81-157">標準偏差を得るには、分散の平方根を計算します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-157">To obtain the standard deviation, calculate the square root of the variance.</span></span>  
  
 <span data-ttu-id="b2e81-158">各属性の `Missing` という値の型は、その属性のデータがなかったケースの数を示します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-158">Note that for each of the attributes there is a `Missing` value type that tells you how many cases had no data for that attribute.</span></span> <span data-ttu-id="b2e81-159">Missing のデータが重要になる場合もあります。このデータが計算に与える影響は、データ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b2e81-159">Missing data can be significant and affects calculations in different ways, depending on the data type.</span></span> <span data-ttu-id="b2e81-160">詳細については、「 [不足値 &#40;Analysis Services - データ マイニング&#41;](missing-values-analysis-services-data-mining.md)であらかじめ定義されているフラグに加えて他のモデリング フラグがある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b2e81-160">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="model-content-for-a-clustering-model"></a><span data-ttu-id="b2e81-161">クラスター モデルのモデル コンテンツ</span><span class="sxs-lookup"><span data-stu-id="b2e81-161">Model Content for a Clustering Model</span></span>  
 <span data-ttu-id="b2e81-162">ここでは、マイニング モデル コンテンツの列のうち、クラスター モデルに関連する列についてのみ詳細と例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-162">This section provides detail and examples only for those columns in the mining model content that are relevant for clustering models.</span></span>  
  
 <span data-ttu-id="b2e81-163">スキーマ行セットの汎用の列 (MODEL_CATALOG や MODEL_NAME など) の詳細については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2e81-163">For information about the general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="b2e81-164">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b2e81-164">MODEL_CATALOG</span></span>  
 <span data-ttu-id="b2e81-165">モデルが格納されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="b2e81-165">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="b2e81-166">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="b2e81-166">MODEL_NAME</span></span>  
 <span data-ttu-id="b2e81-167">モデルの名前。</span><span class="sxs-lookup"><span data-stu-id="b2e81-167">Name of the model.</span></span>  
  
 <span data-ttu-id="b2e81-168">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="b2e81-168">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="b2e81-169">クラスター モデルでは、予測可能な属性がないため常に空白になります。</span><span class="sxs-lookup"><span data-stu-id="b2e81-169">Always blank in clustering models because there is no predictable attribute in the mode.</span></span>  
  
 <span data-ttu-id="b2e81-170">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="b2e81-170">NODE_NAME</span></span>  
 <span data-ttu-id="b2e81-171">常に NODE_UNIQUE_NAME と同じです。</span><span class="sxs-lookup"><span data-stu-id="b2e81-171">Always same as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="b2e81-172">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="b2e81-172">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="b2e81-173">モデル内のノードの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="b2e81-173">A unique identifier for the node within the model.</span></span> <span data-ttu-id="b2e81-174">この値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="b2e81-174">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="b2e81-175">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b2e81-175">NODE_TYPE</span></span>  
 <span data-ttu-id="b2e81-176">クラスター モデルでは次のノード型が出力されます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-176">A clustering model outputs the following node types:</span></span>  
  
|<span data-ttu-id="b2e81-177">ノード ID とノード名</span><span class="sxs-lookup"><span data-stu-id="b2e81-177">Node ID and Name</span></span>|<span data-ttu-id="b2e81-178">説明</span><span class="sxs-lookup"><span data-stu-id="b2e81-178">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="b2e81-179">1 (モデル)</span><span class="sxs-lookup"><span data-stu-id="b2e81-179">1 (Model)</span></span>|<span data-ttu-id="b2e81-180">モデルのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="b2e81-180">Root node for model.</span></span>|  
|<span data-ttu-id="b2e81-181">5 (クラスター)</span><span class="sxs-lookup"><span data-stu-id="b2e81-181">5 (Cluster)</span></span>|<span data-ttu-id="b2e81-182">クラスター内のケースの数および特性と、クラスター内の値を説明する統計が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-182">Contains a count of cases in the cluster, the characteristics of cases in the cluster, and statistics that describe the values in the cluster.</span></span>|  
  
 <span data-ttu-id="b2e81-183">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="b2e81-183">NODE_CAPTION</span></span>  
 <span data-ttu-id="b2e81-184">表示名。</span><span class="sxs-lookup"><span data-stu-id="b2e81-184">A friendly name for display purposes.</span></span> <span data-ttu-id="b2e81-185">モデルを作成すると、NODE_UNIQUE_NAME の値が自動的にキャプションとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-185">When you create a model, the value of NODE_UNIQUE_NAME is automatically used as the caption.</span></span> <span data-ttu-id="b2e81-186">ただし、NODE_CAPTION の値を変更してクラスターの表示名を更新することもできます。この値は、プログラムで変更することも、ビューアーを使用して変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-186">However, you can change the value for NODE_CAPTION to update the display name for the cluster, either programmatically or by using the viewer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2e81-187">モデルを再処理すると、すべての名前変更が新しい値で上書きされます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-187">When you reprocess the model, all name changes will be overwritten by the new values.</span></span> <span data-ttu-id="b2e81-188">モデル内の名前を固定したり、クラスター メンバーシップの変更をモデルの異なるバージョンの間で追跡したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b2e81-188">You cannot persist names in the model, or track changes in cluster membership between different versions of a model.</span></span>  
  
 <span data-ttu-id="b2e81-189">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="b2e81-189">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="b2e81-190">ノードの子の推定数。</span><span class="sxs-lookup"><span data-stu-id="b2e81-190">An estimate of the number of children that the node has.</span></span>  
  
 <span data-ttu-id="b2e81-191">**親ノード** モデル内のクラスターの数を示します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-191">**Parent node** Indicates the number of clusters in the model.</span></span>  
  
 <span data-ttu-id="b2e81-192">**クラスター ノード** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-192">**Cluster nodes** Always 0.</span></span>  
  
 <span data-ttu-id="b2e81-193">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="b2e81-193">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="b2e81-194">ノードの親の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-194">The unique name of the node's parent.</span></span>  
  
 <span data-ttu-id="b2e81-195">**親ノード** 常に NULL です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-195">**Parent node** Always NULL</span></span>  
  
 <span data-ttu-id="b2e81-196">**クラスター ノード** 通常は 000 です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-196">**Cluster nodes** Usually 000.</span></span>  
  
 <span data-ttu-id="b2e81-197">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b2e81-197">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="b2e81-198">ノードの説明です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-198">A description of the node.</span></span>  
  
 <span data-ttu-id="b2e81-199">**親ノード** 常に **(すべて)** です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-199">**Parent node** Always **(All)**.</span></span>  
  
 <span data-ttu-id="b2e81-200">**クラスター ノード** クラスターを他のクラスターから区別する主な属性のコンマ区切りのリストです。</span><span class="sxs-lookup"><span data-stu-id="b2e81-200">**Cluster nodes** A comma-separated list of the primary attributes that distinguish the cluster from other clusters.</span></span>  
  
 <span data-ttu-id="b2e81-201">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="b2e81-201">NODE_RULE</span></span>  
 <span data-ttu-id="b2e81-202">クラスター モデルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="b2e81-202">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="b2e81-203">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="b2e81-203">MARGINAL_RULE</span></span>  
 <span data-ttu-id="b2e81-204">クラスター モデルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="b2e81-204">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="b2e81-205">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b2e81-205">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="b2e81-206">このノードに関連付けられている確率。</span><span class="sxs-lookup"><span data-stu-id="b2e81-206">The probability associated with this node.</span></span> <span data-ttu-id="b2e81-207">**親ノード** 常に 1 です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-207">**Parent node** Always 1.</span></span>  
  
 <span data-ttu-id="b2e81-208">**クラスター ノード** 属性の合成確率を表します。クラスター モデルの作成に使用されたアルゴリズムに応じて何らかの調整が加えられます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-208">**Cluster nodes** The probability represents the compound probability of the attributes, with some adjustments depending on the algorithm used to create the clustering model.</span></span>  
  
 <span data-ttu-id="b2e81-209">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b2e81-209">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="b2e81-210">親ノードからノードに到達する確率です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-210">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="b2e81-211">クラスター モデルでは常に NODE_PROBABILITY と同じです。</span><span class="sxs-lookup"><span data-stu-id="b2e81-211">In a clustering model, the marginal probability is always the same as the node probability.</span></span>  
  
 <span data-ttu-id="b2e81-212">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="b2e81-212">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="b2e81-213">ノードの確率ヒストグラムが含まれているテーブル。</span><span class="sxs-lookup"><span data-stu-id="b2e81-213">A table that contains the probability histogram of the node.</span></span>  
  
 <span data-ttu-id="b2e81-214">**親ノード** このトピックの最初のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2e81-214">**Parent node** See the Introduction to this topic.</span></span>  
  
 <span data-ttu-id="b2e81-215">**クラスター ノード** そのクラスターに含まれているケースの属性と値の分布を表します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-215">**Cluster nodes** Represents the distribution of attributes and values for cases that are included in this cluster.</span></span>  
  
 <span data-ttu-id="b2e81-216">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="b2e81-216">NODE_SUPPORT</span></span>  
 <span data-ttu-id="b2e81-217">このノードをサポートするケースの数。</span><span class="sxs-lookup"><span data-stu-id="b2e81-217">The number of cases that support this node.</span></span> <span data-ttu-id="b2e81-218">**親ノード** モデル全体のトレーニング ケースの数を示します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-218">**Parent node** Indicates the number of training cases for the entire model.</span></span>  
  
 <span data-ttu-id="b2e81-219">**クラスター ノード** クラスターのサイズをケースの数として示します。</span><span class="sxs-lookup"><span data-stu-id="b2e81-219">**Cluster nodes** Indicates the size of the cluster as a number of cases.</span></span>  
  
 <span data-ttu-id="b2e81-220">**注** モデルで K-Means クラスタリングが使用されている場合、各ケースが所属できるクラスターは 1 つだけですが、</span><span class="sxs-lookup"><span data-stu-id="b2e81-220">**Note** If the model uses K-Means clustering, each case can belong to only one cluster.</span></span> <span data-ttu-id="b2e81-221">モデルで EM クラスタリングが使用されている場合は、各ケースが異なるクラスターに所属することができ、所属するクラスターごとに重み付きの距離が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-221">However, if the model uses EM clustering, each case can belong to different cluster, and the case is assigned a weighted distance for each cluster to which it belongs.</span></span> <span data-ttu-id="b2e81-222">したがって、EM モデルの場合は、個々のクラスターのサポートの合計がモデル全体のサポートより大きくなります。</span><span class="sxs-lookup"><span data-stu-id="b2e81-222">Therefore, for EM models the sum of support for an individual cluster is greater than support for the overall model.</span></span>  
  
 <span data-ttu-id="b2e81-223">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="b2e81-223">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="b2e81-224">クラスター モデルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="b2e81-224">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="b2e81-225">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="b2e81-225">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="b2e81-226">ノードに関連付けられたスコアが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-226">Displays a score associated with the node.</span></span>  
  
 <span data-ttu-id="b2e81-227">**親ノード** クラスター モデルの Bayesian Information Criterion (BIC) スコアです。</span><span class="sxs-lookup"><span data-stu-id="b2e81-227">**Parent node** The Bayesian Information Criterion (BIC) score for the clustering model.</span></span>  
  
 <span data-ttu-id="b2e81-228">**クラスター ノード** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-228">**Cluster nodes** Always 0.</span></span>  
  
 <span data-ttu-id="b2e81-229">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="b2e81-229">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="b2e81-230">表示目的で使用されるラベル。</span><span class="sxs-lookup"><span data-stu-id="b2e81-230">A label used for display purposes.</span></span> <span data-ttu-id="b2e81-231">変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="b2e81-231">You cannot change this caption.</span></span>  
  
 <span data-ttu-id="b2e81-232">**親ノード** モデルの種類 (クラスター モデル) です。</span><span class="sxs-lookup"><span data-stu-id="b2e81-232">**Parent node** The type of model: Cluster model</span></span>  
  
 <span data-ttu-id="b2e81-233">**クラスター ノード** クラスターの名前です</span><span class="sxs-lookup"><span data-stu-id="b2e81-233">**Cluster nodes** The name of the cluster.</span></span> <span data-ttu-id="b2e81-234">(Cluster 1 など)。</span><span class="sxs-lookup"><span data-stu-id="b2e81-234">Example: Cluster 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2e81-235">解説</span><span class="sxs-lookup"><span data-stu-id="b2e81-235">Remarks</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="b2e81-236">には、クラスター モデルを作成するための方法が複数用意されています。</span><span class="sxs-lookup"><span data-stu-id="b2e81-236">provides multiple methods for creating a clustering model.</span></span> <span data-ttu-id="b2e81-237">使用しているモデルがどの方法で作成されたかわからない場合は、モデルのメタデータを取得します。モデルのメタデータは、ADOMD クライアントや AMO を使用してプログラムで取得することも、データ マイニング スキーマ行セットに対してクエリを実行して取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="b2e81-237">If you do not know which method was used to create the model that you are working with, you can retrieve the model metadata programmatically, by using an ADOMD client or AMO, or by querying the data mining schema rowset.</span></span> <span data-ttu-id="b2e81-238">詳細については、「 [マイニング モデルの作成に使用されたパラメーターのクエリ](query-the-parameters-used-to-create-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2e81-238">For more information, see [Query the Parameters Used to Create a Mining Model](query-the-parameters-used-to-create-a-mining-model.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2e81-239">使用するクラスタリング手法やパラメーターが違っても、モデルの構造とコンテンツは変わりません。</span><span class="sxs-lookup"><span data-stu-id="b2e81-239">The structure and content of the model stay the same, regardless of which clustering method or parameters you use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e81-240">参照</span><span class="sxs-lookup"><span data-stu-id="b2e81-240">See Also</span></span>  
 <span data-ttu-id="b2e81-241">[マイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b2e81-241">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b2e81-242">[データマイニングモデルビューアー](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="b2e81-242">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 <span data-ttu-id="b2e81-243">[Microsoft クラスタリングアルゴリズム](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="b2e81-243">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="b2e81-244">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="b2e81-244">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
