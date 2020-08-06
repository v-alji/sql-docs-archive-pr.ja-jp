---
title: Naive Bayes モデルのマイニングモデルコンテンツ (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- mining model content, naive bayes models
ms.assetid: 63fa15b0-e00c-4aa3-aa49-335f5572ff7e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 52e5da80e109828722d56fada19b019d1cfa51f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643627"
---
# <a name="mining-model-content-for-naive-bayes-models-analysis-services---data-mining"></a><span data-ttu-id="07bc3-102">Naive Bayes モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="07bc3-102">Mining Model Content for Naive Bayes Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="07bc3-103">このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムを使用するモデルに固有のマイニング モデル コンテンツについて説明します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span> <span data-ttu-id="07bc3-104">すべてのモデルの種類に共通の統計および構造を解釈する方法の説明、およびマイニング モデル コンテンツに関連する用語の一般的な定義については、「 [マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-naive-bayes-model"></a><span data-ttu-id="07bc3-105">Naive Bayes モデルの構造について</span><span class="sxs-lookup"><span data-stu-id="07bc3-105">Understanding the Structure of a Naive Bayes Model</span></span>  
 <span data-ttu-id="07bc3-106">Naive Bayes モデルには、モデルとそのメタデータを表す 1 つの親ノードがあり、その親ノードの下に、選択した予測可能な属性を表す任意の数の独立したツリーがあります。</span><span class="sxs-lookup"><span data-stu-id="07bc3-106">A Naive Bayes model has a single parent node that represents the model and its metadata, and underneath that parent node, any number of independent trees that represent the predictable attributes that you selected.</span></span> <span data-ttu-id="07bc3-107">属性のツリーに加え、各モデルに 1 つ、トレーニング ケースのセットに関する説明的な統計情報を提供するマージナル統計ノード (NODE_TYPE = 26) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-107">In addition to trees for the attributes, each model contains one marginal statistics node (NODE_TYPE = 26) that provides descriptive statistics about the set of training cases.</span></span> <span data-ttu-id="07bc3-108">詳細については、「 [マージナル統計ノードの情報](#bkmk_margstats)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-108">For more information, see [Information in the Marginal Statistics Node](#bkmk_margstats).</span></span>  
  
 <span data-ttu-id="07bc3-109">予測可能な属性および値ごとに、モデルでは、さまざまな入力列が特定の予測可能な属性の結果にどのように影響したかを示す情報を含むツリーが出力されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-109">For each predictable attribute and value, the model outputs a tree that contains information describing how the various input columns affected the outcome of that particular predictable.</span></span> <span data-ttu-id="07bc3-110">各ツリーには、予測可能な属性とその値 (NODE_TYPE = 9) が含まれ、さらに入力属性を表す一連のノード (NODE_TYPE = 10) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-110">Each tree contains the predictable attribute and its value (NODE_TYPE = 9), and then a series of nodes that represent the input attributes (NODE_TYPE = 10).</span></span> <span data-ttu-id="07bc3-111">一般に入力属性には複数の値が含まれるため、各入力属性 (NODE_TYPE = 10) には、属性の特定の状態にそれぞれ対応する複数の子ノード (NODE_TYPE = 11) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-111">Because the input attributes typically have multiple values, each input attribute (NODE_TYPE = 10) may have multiple child nodes (NODE_TYPE = 11), each for a specific state of the attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07bc3-112">Naive Bayes モデルでは、連続するデータ型が許可されないため、入力列のすべての値が不連続値または分離された値として処理されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-112">Because a Naive Bayes model does not permit continuous data types, all the values of the input columns are treated as discrete or discretized.</span></span> <span data-ttu-id="07bc3-113">値を分離する方法は指定できます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-113">You can specify how a value is discretized.</span></span> <span data-ttu-id="07bc3-114">詳細については、「 [マイニング モデルでの列の分離の変更](change-the-discretization-of-a-column-in-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-114">For more information, [Change the Discretization of a Column in a Mining Model](change-the-discretization-of-a-column-in-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="07bc3-115">![naive bayes のモデル コンテンツの構造](../media/modelcontentstructure-nb.gif "naive bayes のモデル コンテンツの構造")</span><span class="sxs-lookup"><span data-stu-id="07bc3-115">![structure of model content for naive bayes](../media/modelcontentstructure-nb.gif "structure of model content for naive bayes")</span></span>  
  
## <a name="model-content-for-a-naive-bayes-model"></a><span data-ttu-id="07bc3-116">Naive Bayes モデルのモデル コンテンツ</span><span class="sxs-lookup"><span data-stu-id="07bc3-116">Model Content for a Naive Bayes Model</span></span>  
 <span data-ttu-id="07bc3-117">ここでは、マイニング モデル コンテンツの列のうち、Naive Bayes モデルに関連する列についてのみ詳細と例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-117">This section provides detail and examples only for those columns in the mining model content that have particular relevance for Naive Bayes models.</span></span>  
  
 <span data-ttu-id="07bc3-118">ここに記載されていないスキーマ行セットの汎用の列 (MODEL_CATALOG や MODEL_NAME など) の詳細や、マイニング モデルの用語の説明については、「 [マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-118">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="07bc3-119">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07bc3-119">MODEL_CATALOG</span></span>  
 <span data-ttu-id="07bc3-120">モデルが格納されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-120">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="07bc3-121">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-121">MODEL_NAME</span></span>  
 <span data-ttu-id="07bc3-122">モデルの名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-122">Name of the model.</span></span>  
  
 <span data-ttu-id="07bc3-123">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-123">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="07bc3-124">このノードに対応する属性の名前です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-124">The names of the attributes that correspond to this node.</span></span>  
  
 <span data-ttu-id="07bc3-125">**モデル ルート** 予測可能な属性の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-125">**Model root** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="07bc3-126">**マージナル統計** 適用なし。</span><span class="sxs-lookup"><span data-stu-id="07bc3-126">**Marginal statistics** Not applicable</span></span>  
  
 <span data-ttu-id="07bc3-127">**予測可能な属性** 予測可能な属性の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-127">**Predictable attribute** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="07bc3-128">**入力属性** 入力属性の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-128">**Input attribute** The name of the input attribute.</span></span>  
  
 <span data-ttu-id="07bc3-129">**入力属性の状態** 入力属性の名前のみ。</span><span class="sxs-lookup"><span data-stu-id="07bc3-129">**Input attribute state** The name of the input attribute only.</span></span> <span data-ttu-id="07bc3-130">状態を取得するには、MSOLAP_NODE_SHORT_CAPTION を使用します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-130">To get the state, use MSOLAP_NODE_SHORT_CAPTION.</span></span>  
  
 <span data-ttu-id="07bc3-131">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-131">NODE_NAME</span></span>  
 <span data-ttu-id="07bc3-132">ノード名。</span><span class="sxs-lookup"><span data-stu-id="07bc3-132">The name of the node.</span></span>  
  
 <span data-ttu-id="07bc3-133">この列には NODE_UNIQUE_NAME と同じ値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-133">This column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="07bc3-134">ノードの名前付け規則の詳細については、「 [ノードの名前と ID の使用](#bkmk_nodenames)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-134">For more information about node naming conventions, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="07bc3-135">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-135">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="07bc3-136">ノードの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-136">The unique name of the node.</span></span> <span data-ttu-id="07bc3-137">一意の名前は、ノード間のリレーションシップに関する情報を示す規則に従って割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-137">The unique names are assigned according to a convention that provides information about the relationships among the nodes.</span></span> <span data-ttu-id="07bc3-138">ノードの名前付け規則の詳細については、「 [ノードの名前と ID の使用](#bkmk_nodenames)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-138">For more information about node naming conventions, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="07bc3-139">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07bc3-139">NODE_TYPE</span></span>  
 <span data-ttu-id="07bc3-140">Naive Bayes モデルでは、次のノードの種類が出力されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-140">A Naive Bayes model outputs the following node types:</span></span>  
  
|<span data-ttu-id="07bc3-141">ノードの種類の ID</span><span class="sxs-lookup"><span data-stu-id="07bc3-141">Node Type ID</span></span>|<span data-ttu-id="07bc3-142">説明</span><span class="sxs-lookup"><span data-stu-id="07bc3-142">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="07bc3-143">26 (マージナル統計ノード)</span><span class="sxs-lookup"><span data-stu-id="07bc3-143">26 (NaiveBayesMarginalStatNode)</span></span>|<span data-ttu-id="07bc3-144">モデルのトレーニング ケースのセット全体を表す統計が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-144">Contains statistics that describes the entire set of training cases for the model.</span></span>|  
|<span data-ttu-id="07bc3-145">9 (予測可能な属性)</span><span class="sxs-lookup"><span data-stu-id="07bc3-145">9 (Predictable attribute)</span></span>|<span data-ttu-id="07bc3-146">予測可能な属性の名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-146">Contains the name of the predictable-attribute.</span></span>|  
|<span data-ttu-id="07bc3-147">10 (入力属性)</span><span class="sxs-lookup"><span data-stu-id="07bc3-147">10 (Input attribute)</span></span>|<span data-ttu-id="07bc3-148">入力属性列の名前、および属性の値を含む子ノードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-148">Contains the name of an input attribute column, and child nodes that contains the values for the attribute.</span></span>|  
|<span data-ttu-id="07bc3-149">11 (入力属性の状態)</span><span class="sxs-lookup"><span data-stu-id="07bc3-149">11 (Input attribute state)</span></span>|<span data-ttu-id="07bc3-150">特定の出力属性と対になったすべての入力属性の値または分離された値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-150">Contains the values or discretized values of all input attributes that were paired with a particular output attribute.</span></span>|  
  
 <span data-ttu-id="07bc3-151">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="07bc3-151">NODE_CAPTION</span></span>  
 <span data-ttu-id="07bc3-152">ノードに関連付けられたラベルまたはキャプション。</span><span class="sxs-lookup"><span data-stu-id="07bc3-152">The label or a caption associated with the node.</span></span> <span data-ttu-id="07bc3-153">このプロパティは、主に表示を目的としています。</span><span class="sxs-lookup"><span data-stu-id="07bc3-153">This property is primarily for display purposes.</span></span>  
  
 <span data-ttu-id="07bc3-154">**モデル ルート** 空白。</span><span class="sxs-lookup"><span data-stu-id="07bc3-154">**Model root** blank</span></span>  
  
 <span data-ttu-id="07bc3-155">**統計の限界**なし</span><span class="sxs-lookup"><span data-stu-id="07bc3-155">**Marginal statistics** blank</span></span>  
  
 <span data-ttu-id="07bc3-156">**予測可能な属性** 予測可能な属性の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-156">**Predictable attribute** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="07bc3-157">**入力属性** 予測可能な属性と現在の入力属性の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-157">**Input attribute** The name of the predictable attribute and the current input attribute.</span></span> <span data-ttu-id="07bc3-158">例:</span><span class="sxs-lookup"><span data-stu-id="07bc3-158">Ex:</span></span>  
  
 <span data-ttu-id="07bc3-159">Bike Buyer -> Age</span><span class="sxs-lookup"><span data-stu-id="07bc3-159">Bike Buyer -> Age</span></span>  
  
 <span data-ttu-id="07bc3-160">**入力属性の状態** 予測可能な属性と現在の入力属性の名前、および入力値。</span><span class="sxs-lookup"><span data-stu-id="07bc3-160">**Input attribute state** The name of the predictable attribute and the current input attribute, plus the value of the input.</span></span> <span data-ttu-id="07bc3-161">例:</span><span class="sxs-lookup"><span data-stu-id="07bc3-161">Ex:</span></span>  
  
 <span data-ttu-id="07bc3-162">Bike Buyer -> Age = Missing</span><span class="sxs-lookup"><span data-stu-id="07bc3-162">Bike Buyer -> Age = Missing</span></span>  
  
 <span data-ttu-id="07bc3-163">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="07bc3-163">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="07bc3-164">ノードが持つ子の数です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-164">The number of children that the node has.</span></span>  
  
 <span data-ttu-id="07bc3-165">**モデル ルート** モデル内の予測可能な属性の数に 1 (マージナル統計ノードの分) を加算した数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-165">**Model root** Count of predictable attributes in the model plus 1 for the marginal statistics node.</span></span>  
  
 <span data-ttu-id="07bc3-166">**マージナル統計** 定義上、子はありません。</span><span class="sxs-lookup"><span data-stu-id="07bc3-166">**Marginal statistics** By definition has no children.</span></span>  
  
 <span data-ttu-id="07bc3-167">**予測可能な属性**  現在の予測可能な属性に関連付けられた入力属性の数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-167">**Predictable attribute**  Count of the input attributes that were related to the current predictable attribute.</span></span>  
  
 <span data-ttu-id="07bc3-168">**入力属性** 現在の入力属性の不連続値または分離された値の数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-168">**Input attribute** Count of the discrete or discretized values for the current input attribute.</span></span>  
  
 <span data-ttu-id="07bc3-169">**入力属性の状態** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-169">**Input attribute state** Always 0.</span></span>  
  
 <span data-ttu-id="07bc3-170">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-170">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="07bc3-171">親ノードの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-171">The unique name of the parent node.</span></span> <span data-ttu-id="07bc3-172">親ノードと子ノードの関連付けの詳細については、「 [ノードの名前と ID の使用](#bkmk_nodenames)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-172">For more information about relating parent and child nodes, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="07bc3-173">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="07bc3-173">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="07bc3-174">ノードのキャプションと同じです。</span><span class="sxs-lookup"><span data-stu-id="07bc3-174">The same as the node caption.</span></span>  
  
 <span data-ttu-id="07bc3-175">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="07bc3-175">NODE_RULE</span></span>  
 <span data-ttu-id="07bc3-176">ノードのキャプションの XML 表現。</span><span class="sxs-lookup"><span data-stu-id="07bc3-176">An XML representation of the node caption.</span></span>  
  
 <span data-ttu-id="07bc3-177">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="07bc3-177">MARGINAL_RULE</span></span>  
 <span data-ttu-id="07bc3-178">ノード ルールと同じです。</span><span class="sxs-lookup"><span data-stu-id="07bc3-178">The same as the node rule.</span></span>  
  
 <span data-ttu-id="07bc3-179">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="07bc3-179">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="07bc3-180">このノードに関連付けられている確率。</span><span class="sxs-lookup"><span data-stu-id="07bc3-180">The probability associated with this node.</span></span>  
  
 <span data-ttu-id="07bc3-181">**モデル ルート** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-181">**Model root** Always 0.</span></span>  
  
 <span data-ttu-id="07bc3-182">**マージナル統計** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-182">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="07bc3-183">**予測可能な属性**  常に 1 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-183">**Predictable attribute**  Always 1.</span></span>  
  
 <span data-ttu-id="07bc3-184">**入力属性** 常に 1 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-184">**Input attribute** Always 1.</span></span>  
  
 <span data-ttu-id="07bc3-185">**入力属性の状態** 現在の値の確率を表す小数値。</span><span class="sxs-lookup"><span data-stu-id="07bc3-185">**Input attribute state** A decimal number that represents the probability of the current value.</span></span> <span data-ttu-id="07bc3-186">親入力属性ノードの下にあるすべての入力属性の状態の値を合計すると 1 になります。</span><span class="sxs-lookup"><span data-stu-id="07bc3-186">Values for all input attribute states under the parent input attribute node sum to 1.</span></span>  
  
 <span data-ttu-id="07bc3-187">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="07bc3-187">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="07bc3-188">ノードの確率と同じです。</span><span class="sxs-lookup"><span data-stu-id="07bc3-188">The same as the node probability.</span></span>  
  
 <span data-ttu-id="07bc3-189">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="07bc3-189">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="07bc3-190">ノードの確率ヒストグラムが含まれているテーブル。</span><span class="sxs-lookup"><span data-stu-id="07bc3-190">A table that contains the probability histogram for the node.</span></span> <span data-ttu-id="07bc3-191">詳細については、「 [NODE_DISTRIBUTION テーブル](#bkmk_nodedist)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-191">For more information, see [NODE_DISTRIBUTION Table](#bkmk_nodedist).</span></span>  
  
 <span data-ttu-id="07bc3-192">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="07bc3-192">NODE_SUPPORT</span></span>  
 <span data-ttu-id="07bc3-193">このノードをサポートするケースの数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-193">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="07bc3-194">**モデル ルート** トレーニング データ内のすべてのケースの数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-194">**Model root** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="07bc3-195">**マージナル統計** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-195">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="07bc3-196">**予測可能な属性** トレーニング データ内のすべてのケースの数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-196">**Predictable attribute** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="07bc3-197">**入力属性** トレーニング データ内のすべてのケースの数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-197">**Input attribute** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="07bc3-198">**入力属性の状態** トレーニング データ内のケースのうち、この特定の値のみを含むケースの数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-198">**Input attribute state** Count of cases in training data that contain only this particular value.</span></span>  
  
 <span data-ttu-id="07bc3-199">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="07bc3-199">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="07bc3-200">表示目的で使用されるラベル。</span><span class="sxs-lookup"><span data-stu-id="07bc3-200">A label used for display purposes.</span></span> <span data-ttu-id="07bc3-201">通常、ATTRIBUTE_NAME と同じです。</span><span class="sxs-lookup"><span data-stu-id="07bc3-201">Usually the same as ATTRIBUTE_NAME.</span></span>  
  
 <span data-ttu-id="07bc3-202">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="07bc3-202">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="07bc3-203">モデル内の属性または値の重要度を表します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-203">Represents the importance of the attribute or value within the model.</span></span>  
  
 <span data-ttu-id="07bc3-204">**モデル ルート** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-204">**Model root** Always 0.</span></span>  
  
 <span data-ttu-id="07bc3-205">**マージナル統計** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-205">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="07bc3-206">**予測可能な属性**  常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-206">**Predictable attribute**  Always 0.</span></span>  
  
 <span data-ttu-id="07bc3-207">**入力属性** 現在の予測可能な属性との関連における現在の入力属性の興味深さのスコア。</span><span class="sxs-lookup"><span data-stu-id="07bc3-207">**Input attribute** Interestingness score for the current input attribute in relation to the current predictable attribute.</span></span>  
  
 <span data-ttu-id="07bc3-208">**入力属性の状態** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-208">**Input attribute state** Always 0.</span></span>  
  
 <span data-ttu-id="07bc3-209">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="07bc3-209">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="07bc3-210">列の名前または値を表すテキスト文字列。</span><span class="sxs-lookup"><span data-stu-id="07bc3-210">A text string that represents the name or the value of a column.</span></span>  
  
 <span data-ttu-id="07bc3-211">**モデルルート**省略</span><span class="sxs-lookup"><span data-stu-id="07bc3-211">**Model root** Blank</span></span>  
  
 <span data-ttu-id="07bc3-212">**マージナル統計** 空白。</span><span class="sxs-lookup"><span data-stu-id="07bc3-212">**Marginal statistics** Blank</span></span>  
  
 <span data-ttu-id="07bc3-213">**予測可能な属性** 予測可能な属性の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-213">**Predictable attribute**  The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="07bc3-214">**入力属性** 入力属性の名前。</span><span class="sxs-lookup"><span data-stu-id="07bc3-214">**Input attribute** The name of the input attribute.</span></span>  
  
 <span data-ttu-id="07bc3-215">**入力属性の状態** 入力属性の値または分離された値。</span><span class="sxs-lookup"><span data-stu-id="07bc3-215">**Input attribute state** The value or discretized value of the input attribute.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_nodenames"></a><span data-ttu-id="07bc3-216">ノード名と Id の使用</span><span class="sxs-lookup"><span data-stu-id="07bc3-216">Using Node Names and IDs</span></span>  
 <span data-ttu-id="07bc3-217">Naive Bayes モデルのノードの名前付けでは、モデル内の情報間のリレーションシップをわかりやすくするために、ノードの種類に関する追加情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-217">The naming of the nodes in a Naive Bayes model provides additional information about the type of node, to make it easier to understand the relationships among the information in the model.</span></span> <span data-ttu-id="07bc3-218">次の表に、さまざまなノードの種類に割り当てられる ID の規則を示します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-218">The following table shows the convention for the IDs that are assigned to different node types.</span></span>  
  
|<span data-ttu-id="07bc3-219">ノードの種類</span><span class="sxs-lookup"><span data-stu-id="07bc3-219">Node Type</span></span>|<span data-ttu-id="07bc3-220">ノード ID の規則</span><span class="sxs-lookup"><span data-stu-id="07bc3-220">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="07bc3-221">モデル ルート (1)</span><span class="sxs-lookup"><span data-stu-id="07bc3-221">Model root (1)</span></span>|<span data-ttu-id="07bc3-222">常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-222">Always 0.</span></span>|  
|<span data-ttu-id="07bc3-223">マージナル統計ノード (26)</span><span class="sxs-lookup"><span data-stu-id="07bc3-223">Marginal statistics node (26)</span></span>|<span data-ttu-id="07bc3-224">任意の ID 値。</span><span class="sxs-lookup"><span data-stu-id="07bc3-224">An arbitrary ID value.</span></span>|  
|<span data-ttu-id="07bc3-225">予測可能な属性 (9)</span><span class="sxs-lookup"><span data-stu-id="07bc3-225">Predictable attribute (9)</span></span>|<span data-ttu-id="07bc3-226">10000000 で始まる 16 進数。</span><span class="sxs-lookup"><span data-stu-id="07bc3-226">Hexadecimal number beginning with 10000000</span></span><br /><br /> <span data-ttu-id="07bc3-227">例 :100000001、10000000b</span><span class="sxs-lookup"><span data-stu-id="07bc3-227">Example: 100000001, 10000000b</span></span>|  
|<span data-ttu-id="07bc3-228">入力属性 (10)</span><span class="sxs-lookup"><span data-stu-id="07bc3-228">Input attribute (10)</span></span>|<span data-ttu-id="07bc3-229">2 つの部分で構成される 16 進数。最初の部分は常に 20000000 であり、2 番目の部分は関連する予測可能な属性の 16 進数の識別子で始まります。</span><span class="sxs-lookup"><span data-stu-id="07bc3-229">A two-part hexadecimal number where the first part is always 20000000, and the second part starts with the hexadecimal identifier of the related predictable attribute.</span></span><br /><br /> <span data-ttu-id="07bc3-230">例 :20000000b00000000</span><span class="sxs-lookup"><span data-stu-id="07bc3-230">Example: 20000000b00000000</span></span><br /><br /> <span data-ttu-id="07bc3-231">この場合、関連する予測可能な属性は 10000000b です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-231">In this case, the related predictable attribute is 10000000b.</span></span>|  
|<span data-ttu-id="07bc3-232">入力属性の状態 (11)</span><span class="sxs-lookup"><span data-stu-id="07bc3-232">Input attribute state (11)</span></span>|<span data-ttu-id="07bc3-233">3 つの部分で構成される 16 進数。最初の部分は常に 30000000 であり、2 番目の部分は関連する予測可能な属性の 16 進数の識別子で始まります。3 番目の部分は値の識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-233">A three-part hexadecimal number where the first part is always 30000000, the second part starts with the hexadecimal identifier of the related predictable attribute, and the third part represents the identifier of the value.</span></span><br /><br /> <span data-ttu-id="07bc3-234">例 :30000000b00000000200000000</span><span class="sxs-lookup"><span data-stu-id="07bc3-234">Example: 30000000b00000000200000000</span></span><br /><br /> <span data-ttu-id="07bc3-235">この場合、関連する予測可能な属性は 10000000b です。</span><span class="sxs-lookup"><span data-stu-id="07bc3-235">In this case, the related predictable attribute is 10000000b.</span></span>|  
  
 <span data-ttu-id="07bc3-236">これらの ID を使用すると、入力属性と状態を予測可能な属性に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-236">You can use the IDs to relate input attributes and states to a predictable attribute.</span></span> <span data-ttu-id="07bc3-237">たとえば、次のクエリでは、 `TM_NaiveBayes`というモデルについて、入力属性と予測可能な属性の考えられる組み合わせを表すノードの名前とキャプションが返されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-237">For example, the following query returns the names and captions for nodes that represent the possible combinations of input and predictable attributes for the model, `TM_NaiveBayes`.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
```  
  
 <span data-ttu-id="07bc3-238">期待される結果:</span><span class="sxs-lookup"><span data-stu-id="07bc3-238">Expected results:</span></span>  
  
|<span data-ttu-id="07bc3-239">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-239">NODE_NAME</span></span>|<span data-ttu-id="07bc3-240">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="07bc3-240">NODE_CAPTION</span></span>|  
|----------------|-------------------|  
|<span data-ttu-id="07bc3-241">20000000000000001</span><span class="sxs-lookup"><span data-stu-id="07bc3-241">20000000000000001</span></span>|<span data-ttu-id="07bc3-242">Bike Buyer -> Commute Distance</span><span class="sxs-lookup"><span data-stu-id="07bc3-242">Bike Buyer -> Commute Distance</span></span>|  
|<span data-ttu-id="07bc3-243">20000000000000002</span><span class="sxs-lookup"><span data-stu-id="07bc3-243">20000000000000002</span></span>|<span data-ttu-id="07bc3-244">Bike Buyer -> English Education</span><span class="sxs-lookup"><span data-stu-id="07bc3-244">Bike Buyer -> English Education</span></span>|  
|<span data-ttu-id="07bc3-245">20000000000000003</span><span class="sxs-lookup"><span data-stu-id="07bc3-245">20000000000000003</span></span>|<span data-ttu-id="07bc3-246">Bike Buyer -> English Occupation</span><span class="sxs-lookup"><span data-stu-id="07bc3-246">Bike Buyer -> English Occupation</span></span>|  
|<span data-ttu-id="07bc3-247">20000000000000009</span><span class="sxs-lookup"><span data-stu-id="07bc3-247">20000000000000009</span></span>|<span data-ttu-id="07bc3-248">Bike Buyer -> Marital Status</span><span class="sxs-lookup"><span data-stu-id="07bc3-248">Bike Buyer -> Marital Status</span></span>|  
|<span data-ttu-id="07bc3-249">2000000000000000a</span><span class="sxs-lookup"><span data-stu-id="07bc3-249">2000000000000000a</span></span>|<span data-ttu-id="07bc3-250">Bike Buyer -> Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="07bc3-250">Bike Buyer -> Number Children At Home</span></span>|  
|<span data-ttu-id="07bc3-251">2000000000000000b</span><span class="sxs-lookup"><span data-stu-id="07bc3-251">2000000000000000b</span></span>|<span data-ttu-id="07bc3-252">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="07bc3-252">Bike Buyer -> Region</span></span>|  
|<span data-ttu-id="07bc3-253">2000000000000000c</span><span class="sxs-lookup"><span data-stu-id="07bc3-253">2000000000000000c</span></span>|<span data-ttu-id="07bc3-254">Bike Buyer -> Total Children</span><span class="sxs-lookup"><span data-stu-id="07bc3-254">Bike Buyer -> Total Children</span></span>|  
  
 <span data-ttu-id="07bc3-255">また、親ノードの ID を使用して子ノードを取得できます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-255">You can then use the IDs of the parent nodes to retrieve the child nodes.</span></span> <span data-ttu-id="07bc3-256">次のクエリでは、 `Marital Status` 属性の値を含むノードを、各ノードの確率と共に取得します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-256">The following query retrieves the nodes that contain values for the `Marital Status` attribute, together with the probability of each node.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION, NODE_PROBABILITY  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 11  
AND [PARENT_UNIQUE_NAME] = '20000000000000009'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="07bc3-257">PARENT_UNIQUE_NAME という列の名前は、同名の予約済みキーワードと区別するために角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="07bc3-257">The name of the column, PARENT_UNIQUE_NAME, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="07bc3-258">期待される結果:</span><span class="sxs-lookup"><span data-stu-id="07bc3-258">Expected results:</span></span>  
  
|<span data-ttu-id="07bc3-259">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-259">NODE_NAME</span></span>|<span data-ttu-id="07bc3-260">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="07bc3-260">NODE_CAPTION</span></span>|<span data-ttu-id="07bc3-261">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="07bc3-261">NODE_PROBABILITY</span></span>|  
|----------------|-------------------|-----------------------|  
|<span data-ttu-id="07bc3-262">3000000000000000900000000</span><span class="sxs-lookup"><span data-stu-id="07bc3-262">3000000000000000900000000</span></span>|<span data-ttu-id="07bc3-263">Bike Buyer -> Marital Status = Missing</span><span class="sxs-lookup"><span data-stu-id="07bc3-263">Bike Buyer -> Marital Status = Missing</span></span>|<span data-ttu-id="07bc3-264">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-264">0</span></span>|  
|<span data-ttu-id="07bc3-265">3000000000000000900000001</span><span class="sxs-lookup"><span data-stu-id="07bc3-265">3000000000000000900000001</span></span>|<span data-ttu-id="07bc3-266">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="07bc3-266">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="07bc3-267">0.457504004</span><span class="sxs-lookup"><span data-stu-id="07bc3-267">0.457504004</span></span>|  
|<span data-ttu-id="07bc3-268">3000000000000000900000002</span><span class="sxs-lookup"><span data-stu-id="07bc3-268">3000000000000000900000002</span></span>|<span data-ttu-id="07bc3-269">Bike Buyer -> Marital Status = M</span><span class="sxs-lookup"><span data-stu-id="07bc3-269">Bike Buyer -> Marital Status = M</span></span>|<span data-ttu-id="07bc3-270">0.542495996</span><span class="sxs-lookup"><span data-stu-id="07bc3-270">0.542495996</span></span>|  
  
##  <a name="node_distribution-table"></a><a name="bkmk_nodedist"></a><span data-ttu-id="07bc3-271">NODE_DISTRIBUTION テーブル</span><span class="sxs-lookup"><span data-stu-id="07bc3-271">NODE_DISTRIBUTION Table</span></span>  
 <span data-ttu-id="07bc3-272">入れ子になったテーブル列である NODE_DISTRIBUTION には、通常、ノード内の値の分布に関する統計が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-272">The nested table column, NODE_DISTRIBUTION, typically contains statistics about the distribution of values in the node.</span></span> <span data-ttu-id="07bc3-273">Naive Bayes モデルでは、このテーブルは次のノードに対してのみ作成されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-273">In a Naive Bayes model, this table is populated only for the following nodes:</span></span>  
  
|<span data-ttu-id="07bc3-274">ノードの種類</span><span class="sxs-lookup"><span data-stu-id="07bc3-274">Node Type</span></span>|<span data-ttu-id="07bc3-275">入れ子になったテーブルの内容</span><span class="sxs-lookup"><span data-stu-id="07bc3-275">Content of nested table</span></span>|  
|---------------|-----------------------------|  
|<span data-ttu-id="07bc3-276">モデル ルート (1)</span><span class="sxs-lookup"><span data-stu-id="07bc3-276">Model root (1)</span></span>|<span data-ttu-id="07bc3-277">空白。</span><span class="sxs-lookup"><span data-stu-id="07bc3-277">Blank.</span></span>|  
|<span data-ttu-id="07bc3-278">マージナル統計ノード (24)</span><span class="sxs-lookup"><span data-stu-id="07bc3-278">Marginal statistics node (24)</span></span>|<span data-ttu-id="07bc3-279">トレーニング データのセット全体についてのすべての予測可能な属性および入力属性の概要情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-279">Contains summary information for all predictable attributes and input attributes, for entire set of training data.</span></span>|  
|<span data-ttu-id="07bc3-280">予測可能な属性 (9)</span><span class="sxs-lookup"><span data-stu-id="07bc3-280">Predictable attribute (9)</span></span>|<span data-ttu-id="07bc3-281">空白。</span><span class="sxs-lookup"><span data-stu-id="07bc3-281">Blank.</span></span>|  
|<span data-ttu-id="07bc3-282">入力属性 (10)</span><span class="sxs-lookup"><span data-stu-id="07bc3-282">Input attribute (10)</span></span>|<span data-ttu-id="07bc3-283">空白。</span><span class="sxs-lookup"><span data-stu-id="07bc3-283">Blank.</span></span>|  
|<span data-ttu-id="07bc3-284">入力属性の状態 (11)</span><span class="sxs-lookup"><span data-stu-id="07bc3-284">Input attribute state (11)</span></span>|<span data-ttu-id="07bc3-285">予測可能な値と入力属性値のこの特定の組み合わせについてのトレーニング データ内の値の分布を表す統計が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-285">Contains statistics that describe the distribution of values in the training data for this particular combination of a predictable value and input attribute value.</span></span>|  
  
 <span data-ttu-id="07bc3-286">ノード ID またはノードのキャプションを使用すると、より詳細な情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-286">You can use the node IDs or node captions to retrieve increasing levels of detail.</span></span> <span data-ttu-id="07bc3-287">たとえば、次のクエリでは、値 `'Marital Status = S'`に関連付けられた入力属性ノードのみについて、NODE_DISTRIBUTION テーブルから特定の列を取得します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-287">For example, the following query retrieves specific columns from the NODE_DISTRIBUTION table for only those input attribute nodes that are related to the value, `'Marital Status = S'`.</span></span>  
  
```  
SELECT FLATTENED NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM TM_NaiveBayes.content  
WHERE NODE_TYPE = 11  
AND NODE_CAPTION = 'Bike Buyer -> Marital Status = S'  
```  
  
 <span data-ttu-id="07bc3-288">期待される結果:</span><span class="sxs-lookup"><span data-stu-id="07bc3-288">Expected results:</span></span>  
  
|<span data-ttu-id="07bc3-289">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="07bc3-289">NODE_CAPTION</span></span>|<span data-ttu-id="07bc3-290">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-290">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="07bc3-291">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="07bc3-291">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="07bc3-292">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="07bc3-292">t.SUPPORT</span></span>|<span data-ttu-id="07bc3-293">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="07bc3-293">t.PROBABILITY</span></span>|<span data-ttu-id="07bc3-294">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="07bc3-294">t.VALUETYPE</span></span>|  
|-------------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="07bc3-295">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="07bc3-295">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="07bc3-296">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="07bc3-296">Bike Buyer</span></span>|<span data-ttu-id="07bc3-297">Missing</span><span class="sxs-lookup"><span data-stu-id="07bc3-297">Missing</span></span>|<span data-ttu-id="07bc3-298">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-298">0</span></span>|<span data-ttu-id="07bc3-299">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-299">0</span></span>|<span data-ttu-id="07bc3-300">1</span><span class="sxs-lookup"><span data-stu-id="07bc3-300">1</span></span>|  
|<span data-ttu-id="07bc3-301">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="07bc3-301">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="07bc3-302">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="07bc3-302">Bike Buyer</span></span>|<span data-ttu-id="07bc3-303">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-303">0</span></span>|<span data-ttu-id="07bc3-304">3783</span><span class="sxs-lookup"><span data-stu-id="07bc3-304">3783</span></span>|<span data-ttu-id="07bc3-305">0.472934117</span><span class="sxs-lookup"><span data-stu-id="07bc3-305">0.472934117</span></span>|<span data-ttu-id="07bc3-306">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-306">4</span></span>|  
|<span data-ttu-id="07bc3-307">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="07bc3-307">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="07bc3-308">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="07bc3-308">Bike Buyer</span></span>|<span data-ttu-id="07bc3-309">1</span><span class="sxs-lookup"><span data-stu-id="07bc3-309">1</span></span>|<span data-ttu-id="07bc3-310">4216</span><span class="sxs-lookup"><span data-stu-id="07bc3-310">4216</span></span>|<span data-ttu-id="07bc3-311">0.527065883</span><span class="sxs-lookup"><span data-stu-id="07bc3-311">0.527065883</span></span>|<span data-ttu-id="07bc3-312">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-312">4</span></span>|  
  
 <span data-ttu-id="07bc3-313">これらの結果の SUPPORT 列の値は、指定した結婚歴に当てはまる顧客のうち、自転車を購入した顧客の数を示します。</span><span class="sxs-lookup"><span data-stu-id="07bc3-313">In these results, the value of the SUPPORT column tells you the count of customers with the specified marital status who purchased a bike.</span></span> <span data-ttu-id="07bc3-314">PROBABILITY 列には、このノードのみについて計算された各属性値の確率が格納されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-314">The PROBABILITY column contains the probability of each attribute value, as calculated for this node only.</span></span> <span data-ttu-id="07bc3-315">NODE_DISTRIBUTION テーブルで使用される用語の一般的な定義については、「 [マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-315">For general definitions of terms used in the NODE_DISTRIBUTION table, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
###  <a name="information-in-the-marginal-statistics-node"></a><a name="bkmk_margstats"></a><span data-ttu-id="07bc3-316">[最低限の統計情報ノードの情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc3-316">Information in the Marginal Statistics Node</span></span>  
 <span data-ttu-id="07bc3-317">Naive Bayes モデルでは、マージナル統計ノードの入れ子になったテーブルに、トレーニング データのセット全体の値の分布が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-317">In a Naive Bayes model, the nested table for the marginal statistics node contains the distribution of values for the entire set of training data.</span></span> <span data-ttu-id="07bc3-318">たとえば、次の表は、 `TM_NaiveBayes`モデルの入れ子になった NODE_DISTRIBUTION テーブルに含まれる統計の一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="07bc3-318">For example, the following table contains a partial list of the statistics in the nested NODE_DISTRIBUTION table for the model, `TM_NaiveBayes`:</span></span>  
  
|<span data-ttu-id="07bc3-319">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="07bc3-319">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="07bc3-320">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="07bc3-320">ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="07bc3-321">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="07bc3-321">SUPPORT</span></span>|<span data-ttu-id="07bc3-322">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="07bc3-322">PROBABILITY</span></span>|<span data-ttu-id="07bc3-323">variance</span><span class="sxs-lookup"><span data-stu-id="07bc3-323">VARIANCE</span></span>|<span data-ttu-id="07bc3-324">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="07bc3-324">VALUETYPE</span></span>|  
|---------------------|----------------------|-------------|-----------------|--------------|---------------|  
|<span data-ttu-id="07bc3-325">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="07bc3-325">Bike Buyer</span></span>|<span data-ttu-id="07bc3-326">Missing</span><span class="sxs-lookup"><span data-stu-id="07bc3-326">Missing</span></span>|<span data-ttu-id="07bc3-327">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-327">0</span></span>|<span data-ttu-id="07bc3-328">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-328">0</span></span>|<span data-ttu-id="07bc3-329">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-329">0</span></span>|<span data-ttu-id="07bc3-330">1</span><span class="sxs-lookup"><span data-stu-id="07bc3-330">1</span></span>|  
|<span data-ttu-id="07bc3-331">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="07bc3-331">Bike Buyer</span></span>|<span data-ttu-id="07bc3-332">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-332">0</span></span>|<span data-ttu-id="07bc3-333">8869</span><span class="sxs-lookup"><span data-stu-id="07bc3-333">8869</span></span>|<span data-ttu-id="07bc3-334">0.507263784</span><span class="sxs-lookup"><span data-stu-id="07bc3-334">0.507263784</span></span>|<span data-ttu-id="07bc3-335">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-335">0</span></span>|<span data-ttu-id="07bc3-336">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-336">4</span></span>|  
|<span data-ttu-id="07bc3-337">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="07bc3-337">Bike Buyer</span></span>|<span data-ttu-id="07bc3-338">1</span><span class="sxs-lookup"><span data-stu-id="07bc3-338">1</span></span>|<span data-ttu-id="07bc3-339">8615</span><span class="sxs-lookup"><span data-stu-id="07bc3-339">8615</span></span>|<span data-ttu-id="07bc3-340">0.492736216</span><span class="sxs-lookup"><span data-stu-id="07bc3-340">0.492736216</span></span>|<span data-ttu-id="07bc3-341">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-341">0</span></span>|<span data-ttu-id="07bc3-342">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-342">4</span></span>|  
|<span data-ttu-id="07bc3-343">Marital Status</span><span class="sxs-lookup"><span data-stu-id="07bc3-343">Marital Status</span></span>|<span data-ttu-id="07bc3-344">Missing</span><span class="sxs-lookup"><span data-stu-id="07bc3-344">Missing</span></span>|<span data-ttu-id="07bc3-345">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-345">0</span></span>|<span data-ttu-id="07bc3-346">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-346">0</span></span>|<span data-ttu-id="07bc3-347">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-347">0</span></span>|<span data-ttu-id="07bc3-348">1</span><span class="sxs-lookup"><span data-stu-id="07bc3-348">1</span></span>|  
|<span data-ttu-id="07bc3-349">Marital Status</span><span class="sxs-lookup"><span data-stu-id="07bc3-349">Marital Status</span></span>|<span data-ttu-id="07bc3-350">S</span><span class="sxs-lookup"><span data-stu-id="07bc3-350">S</span></span>|<span data-ttu-id="07bc3-351">7999</span><span class="sxs-lookup"><span data-stu-id="07bc3-351">7999</span></span>|<span data-ttu-id="07bc3-352">0.457504004</span><span class="sxs-lookup"><span data-stu-id="07bc3-352">0.457504004</span></span>|<span data-ttu-id="07bc3-353">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-353">0</span></span>|<span data-ttu-id="07bc3-354">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-354">4</span></span>|  
|<span data-ttu-id="07bc3-355">Marital Status</span><span class="sxs-lookup"><span data-stu-id="07bc3-355">Marital Status</span></span>|<span data-ttu-id="07bc3-356">M</span><span class="sxs-lookup"><span data-stu-id="07bc3-356">M</span></span>|<span data-ttu-id="07bc3-357">9485</span><span class="sxs-lookup"><span data-stu-id="07bc3-357">9485</span></span>|<span data-ttu-id="07bc3-358">0.542495996</span><span class="sxs-lookup"><span data-stu-id="07bc3-358">0.542495996</span></span>|<span data-ttu-id="07bc3-359">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-359">0</span></span>|<span data-ttu-id="07bc3-360">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-360">4</span></span>|  
|<span data-ttu-id="07bc3-361">Total Children</span><span class="sxs-lookup"><span data-stu-id="07bc3-361">Total Children</span></span>|<span data-ttu-id="07bc3-362">Missing</span><span class="sxs-lookup"><span data-stu-id="07bc3-362">Missing</span></span>|<span data-ttu-id="07bc3-363">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-363">0</span></span>|<span data-ttu-id="07bc3-364">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-364">0</span></span>|<span data-ttu-id="07bc3-365">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-365">0</span></span>|<span data-ttu-id="07bc3-366">1</span><span class="sxs-lookup"><span data-stu-id="07bc3-366">1</span></span>|  
|<span data-ttu-id="07bc3-367">Total Children</span><span class="sxs-lookup"><span data-stu-id="07bc3-367">Total Children</span></span>|<span data-ttu-id="07bc3-368">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-368">0</span></span>|<span data-ttu-id="07bc3-369">4865</span><span class="sxs-lookup"><span data-stu-id="07bc3-369">4865</span></span>|<span data-ttu-id="07bc3-370">0.278254404</span><span class="sxs-lookup"><span data-stu-id="07bc3-370">0.278254404</span></span>|<span data-ttu-id="07bc3-371">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-371">0</span></span>|<span data-ttu-id="07bc3-372">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-372">4</span></span>|  
|<span data-ttu-id="07bc3-373">Total Children</span><span class="sxs-lookup"><span data-stu-id="07bc3-373">Total Children</span></span>|<span data-ttu-id="07bc3-374">3</span><span class="sxs-lookup"><span data-stu-id="07bc3-374">3</span></span>|<span data-ttu-id="07bc3-375">2093</span><span class="sxs-lookup"><span data-stu-id="07bc3-375">2093</span></span>|<span data-ttu-id="07bc3-376">0.119709449</span><span class="sxs-lookup"><span data-stu-id="07bc3-376">0.119709449</span></span>|<span data-ttu-id="07bc3-377">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-377">0</span></span>|<span data-ttu-id="07bc3-378">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-378">4</span></span>|  
|<span data-ttu-id="07bc3-379">Total Children</span><span class="sxs-lookup"><span data-stu-id="07bc3-379">Total Children</span></span>|<span data-ttu-id="07bc3-380">1</span><span class="sxs-lookup"><span data-stu-id="07bc3-380">1</span></span>|<span data-ttu-id="07bc3-381">3406</span><span class="sxs-lookup"><span data-stu-id="07bc3-381">3406</span></span>|<span data-ttu-id="07bc3-382">0.19480668</span><span class="sxs-lookup"><span data-stu-id="07bc3-382">0.19480668</span></span>|<span data-ttu-id="07bc3-383">0</span><span class="sxs-lookup"><span data-stu-id="07bc3-383">0</span></span>|<span data-ttu-id="07bc3-384">4</span><span class="sxs-lookup"><span data-stu-id="07bc3-384">4</span></span>|  
  
 <span data-ttu-id="07bc3-385">マージナル統計ノードには常に予測可能な属性とその取り得る値の説明が含まれるため、`Bike Buyer` 列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-385">The `Bike Buyer` column is included because the marginal statistics node always contains a description of the predictable attribute and its possible values.</span></span> <span data-ttu-id="07bc3-386">表中のその他の列はすべて入力属性を表し、モデルで使用された値と共に表示されています。</span><span class="sxs-lookup"><span data-stu-id="07bc3-386">All other columns that are listed represent input attributes, together with the values that were used in the model.</span></span> <span data-ttu-id="07bc3-387">値は不足値、不連続値、または分離された値のみになります。</span><span class="sxs-lookup"><span data-stu-id="07bc3-387">Values can only be missing, discrete or discretized.</span></span>  
  
 <span data-ttu-id="07bc3-388">Naive Bayes モデルでは、連続属性を含めることはできないため、数値データはすべて不連続値 (VALUE_TYPE = 4) または分離された値 (VALUE_TYPE = 5) として表されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-388">In a Naive Bayes model, there can be no continuous attributes; therefore, all numeric data is represented as either discrete (VALUE_TYPE = 4) or discretized (VALUE_TYPE = 5).</span></span>  
  
 <span data-ttu-id="07bc3-389">トレーニング データには存在しなかった有効な値を表すために、すべての入力属性と出力属性に `Missing` 値 (VALUE_TYPE = 1) が追加されます。</span><span class="sxs-lookup"><span data-stu-id="07bc3-389">A `Missing` value (VALUE_TYPE = 1) is added to every input and output attribute to represent potential values that were not present in the training data.</span></span> <span data-ttu-id="07bc3-390">"missing" という文字列と既定の `Missing` 値を区別するように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07bc3-390">You must be careful to distinguish between "missing" as a string and the default `Missing` value.</span></span> <span data-ttu-id="07bc3-391">詳細については、「 [不足値 &#40;Analysis Services - データ マイニング&#41;](missing-values-analysis-services-data-mining.md)であらかじめ定義されているフラグに加えて他のモデリング フラグがある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="07bc3-391">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07bc3-392">参照</span><span class="sxs-lookup"><span data-stu-id="07bc3-392">See Also</span></span>  
 <span data-ttu-id="07bc3-393">[マイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="07bc3-393">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="07bc3-394">[データマイニングモデルビューアー](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="07bc3-394">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 <span data-ttu-id="07bc3-395">[データマイニングクエリ](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="07bc3-395">[Data Mining Queries](data-mining-queries.md) </span></span>  
 [<span data-ttu-id="07bc3-396">Microsoft Naive Bayes アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="07bc3-396">Microsoft Naive Bayes Algorithm</span></span>](microsoft-naive-bayes-algorithm.md)  
  
  
