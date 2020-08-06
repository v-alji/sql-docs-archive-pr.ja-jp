---
title: ロジスティック回帰モデルのマイニングモデルコンテンツ (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- mining model content, logistic regression models
- regression algorithms [Analysis Services]
ms.assetid: 69cc0b86-e8bc-4d6c-903e-85724f5c0396
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84964c59a63d41f0985001a2ae384fa298096927
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643632"
---
# <a name="mining-model-content-for-logistic-regression-models-analysis-services---data-mining"></a><span data-ttu-id="0e57e-102">ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="0e57e-102">Mining Model Content for Logistic Regression Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="0e57e-103">このトピックでは、Microsoft ロジスティック回帰アルゴリズムを使用するモデルに固有のマイニング モデル コンテンツについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0e57e-103">This topic describes mining model content that is specific to models that use the Microsoft Logistic Regression algorithm.</span></span> <span data-ttu-id="0e57e-104">すべてのモデルの種類に共通の統計および構造を解釈する方法の説明、およびマイニング モデル コンテンツに関連する用語の一般的な定義については、「 [マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e57e-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-logistic-regression-model"></a><span data-ttu-id="0e57e-105">ロジスティック回帰モデルの構造について</span><span class="sxs-lookup"><span data-stu-id="0e57e-105">Understanding the Structure of a Logistic Regression Model</span></span>  
 <span data-ttu-id="0e57e-106">ロジスティック回帰モデルは、Microsoft ニューラル ネットワーク アルゴリズムで、非表示ノードを取り除くようモデルを制約するパラメーターを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-106">A logistic regression model is created by using the Microsoft Neural Network algorithm with parameters that constrain the model to eliminate the hidden node.</span></span> <span data-ttu-id="0e57e-107">そのため、ロジスティック回帰モデルの全体的な構造は、ニューラル ネットワークの全体的な構造とほぼ同じです。各モデルには、モデルとそのメタデータを表す 1 つの親ノードと、モデルで使用される入力に関する説明的な統計情報を提供する特殊なマージナル統計ノード (NODE_TYPE = 24) があります。</span><span class="sxs-lookup"><span data-stu-id="0e57e-107">Therefore, the overall structure of a logistic regression model is almost identical to that of a neural network: each model has a single parent node that represents the model and its metadata, and a special marginal statistics node (NODE_TYPE = 24) that provides descriptive statistics about the inputs used in the model.</span></span>  
  
 <span data-ttu-id="0e57e-108">また、モデルには、予測可能な属性ごとにサブネットワーク (NODE_TYPE = 17) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-108">Additionally, the model contains a subnetwork (NODE_TYPE = 17) for each predictable attribute.</span></span> <span data-ttu-id="0e57e-109">ニューラル ネットワーク モデルの場合と同様、各サブネットワークには常に 2 つの分岐があります。1 つは入力層の分岐で、もう 1 つは、ネットワークの非表示層 (NODE_TYPE = 19) と出力層 (NODE_TYPE = 20) を含む分岐です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-109">Just like in a neural network model, each subnetwork always contains two branches: one for the input layer, and another branch that contains the hidden layer (NODE_TYPE = 19) and the output layer (NODE_TYPE = 20) for the network.</span></span> <span data-ttu-id="0e57e-110">複数の属性が予測のみとして指定されている場合、同じサブネットワークがそれらの属性で使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="0e57e-110">The same subnetwork may be used for multiple attributes if they are specified as predict-only.</span></span> <span data-ttu-id="0e57e-111">入力でもある予測可能な属性を同じサブネットワークに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="0e57e-111">Predictable attributes that are also inputs may not appear in the same subnetwork.</span></span>  
  
 <span data-ttu-id="0e57e-112">ただし、ロジスティック回帰モデルでは、非表示層を表すノードは空であり、子はありません。</span><span class="sxs-lookup"><span data-stu-id="0e57e-112">However, in a logistic regression model, the node that represents the hidden layer is empty, and has no children.</span></span> <span data-ttu-id="0e57e-113">したがって、モデルには、個々の出力 (NODE_TYPE = 23) と個々の入力 (NODE_TYPE = 21) を表すノードが含まれますが、個々の非表示ノードは含まれません。</span><span class="sxs-lookup"><span data-stu-id="0e57e-113">Therefore the model contains nodes that represent individual outputs (NODE_TYPE = 23) and individual inputs (NODE_TYPE = 21) but no individual hidden nodes.</span></span>  
  
 <span data-ttu-id="0e57e-114">![ロジスティック回帰モデルのコンテンツの構造](../media/skt-modelcontentstructure-logregc.gif "ロジスティック回帰モデルのコンテンツの構造")</span><span class="sxs-lookup"><span data-stu-id="0e57e-114">![structure of content for logisitc regression model](../media/skt-modelcontentstructure-logregc.gif "structure of content for logisitc regression model")</span></span>  
  
 <span data-ttu-id="0e57e-115">既定では、ロジスティック回帰モデルは **Microsoft ニューラル ネットワーク ビューアー**に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-115">By default, a logistic regression model is displayed in the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="0e57e-116">このカスタム ビューアーを使用して、入力属性およびその値をフィルター処理したり、出力への影響をグラフィカルに表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-116">With this custom viewer, you can filter on input attributes and their values, and graphically see how they affect the outputs.</span></span> <span data-ttu-id="0e57e-117">このビューアーのツールヒントには、入力値と出力値の各ペアに関連付けられている確率とリフトが示されます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-117">The tooltips in the viewer show you the probability and lift associated with each pair of inputs and output values.</span></span> <span data-ttu-id="0e57e-118">詳細については、「 [Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-neural-network-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e57e-118">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="0e57e-119">入力およびサブネットワークの構造を参照したり、詳細な統計情報を表示したりするには、Microsoft 汎用コンテンツ ツリー ビューアーを使用します。</span><span class="sxs-lookup"><span data-stu-id="0e57e-119">To explore the structure of the inputs and subnetworks, and to see detailed statistics, you can use the Microsoft Generic Content Tree viewer.</span></span> <span data-ttu-id="0e57e-120">任意のノードをクリックして展開すると、子ノードを表示できます。ノードに含まれている重みやその他の統計情報を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-120">You can click on any node to expand it and see the child nodes, or view the weights and other statistics contained in the node.</span></span>  
  
## <a name="model-content-for-a-logistic-regression-model"></a><span data-ttu-id="0e57e-121">ロジスティック回帰モデルのモデル コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0e57e-121">Model Content for a Logistic Regression Model</span></span>  
 <span data-ttu-id="0e57e-122">ここでは、マイニング モデル コンテンツの列のうち、ロジスティック回帰に関連する列についてのみ詳細と例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="0e57e-122">This section provides detail and examples only for those columns in the mining model content that have particular relevance for logistic regression.</span></span> <span data-ttu-id="0e57e-123">このモデル コンテンツはニューラル ネットワーク モデルのものとほぼ同じなので、便宜上、この表にも、ニューラル ネットワーク モデルに当てはまる説明が記載されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0e57e-123">The model content is almost identical to that of a neural network model, but descriptions that apply to neural network models may be repeated in this table for convenience.</span></span>  
  
 <span data-ttu-id="0e57e-124">ここに記載されていないスキーマ行セットの汎用の列 (MODEL_CATALOG や MODEL_NAME など) の詳細や、マイニング モデルの用語の説明については、「 [マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e57e-124">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="0e57e-125">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e57e-125">MODEL_CATALOG</span></span>  
 <span data-ttu-id="0e57e-126">モデルが格納されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="0e57e-126">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="0e57e-127">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="0e57e-127">MODEL_NAME</span></span>  
 <span data-ttu-id="0e57e-128">モデルの名前。</span><span class="sxs-lookup"><span data-stu-id="0e57e-128">Name of the model.</span></span>  
  
 <span data-ttu-id="0e57e-129">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e57e-129">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="0e57e-130">このノードに対応する属性の名前。</span><span class="sxs-lookup"><span data-stu-id="0e57e-130">The names of the attribute that corresponds to this node.</span></span>  
  
|<span data-ttu-id="0e57e-131">Node</span><span class="sxs-lookup"><span data-stu-id="0e57e-131">Node</span></span>|<span data-ttu-id="0e57e-132">コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0e57e-132">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0e57e-133">モデル ルート</span><span class="sxs-lookup"><span data-stu-id="0e57e-133">Model root</span></span>|<span data-ttu-id="0e57e-134">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-134">Blank</span></span>|  
|<span data-ttu-id="0e57e-135">マージナル統計</span><span class="sxs-lookup"><span data-stu-id="0e57e-135">Marginal statistics</span></span>|<span data-ttu-id="0e57e-136">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-136">Blank</span></span>|  
|<span data-ttu-id="0e57e-137">入力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-137">Input layer</span></span>|<span data-ttu-id="0e57e-138">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-138">Blank</span></span>|  
|<span data-ttu-id="0e57e-139">入力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-139">Input node</span></span>|<span data-ttu-id="0e57e-140">入力属性名</span><span class="sxs-lookup"><span data-stu-id="0e57e-140">Input attribute name</span></span>|  
|<span data-ttu-id="0e57e-141">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0e57e-141">Hidden layer</span></span>|<span data-ttu-id="0e57e-142">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-142">Blank</span></span>|  
|<span data-ttu-id="0e57e-143">出力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-143">Output layer</span></span>|<span data-ttu-id="0e57e-144">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-144">Blank</span></span>|  
|<span data-ttu-id="0e57e-145">出力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-145">Output node</span></span>|<span data-ttu-id="0e57e-146">出力属性名</span><span class="sxs-lookup"><span data-stu-id="0e57e-146">Output attribute name</span></span>|  
  
 <span data-ttu-id="0e57e-147">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e57e-147">NODE_NAME</span></span>  
 <span data-ttu-id="0e57e-148">ノード名。</span><span class="sxs-lookup"><span data-stu-id="0e57e-148">The name of the node.</span></span> <span data-ttu-id="0e57e-149">現在、この列には NODE_UNIQUE_NAME と同じ値が格納されていますが、将来のリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0e57e-149">Currently, this column contains the same value as NODE_UNIQUE_NAME, though this may change in future releases.</span></span>  
  
 <span data-ttu-id="0e57e-150">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e57e-150">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="0e57e-151">ノードの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="0e57e-151">The unique name of the node.</span></span>  
  
 <span data-ttu-id="0e57e-152">モデルに関して名前と ID が表す構造情報の詳細については、「 [ノードの名前と ID の使用](#bkmk_NodeIDs)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e57e-152">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="0e57e-153">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e57e-153">NODE_TYPE</span></span>  
 <span data-ttu-id="0e57e-154">ロジスティック回帰モデルでは、次のノードの種類が出力されます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-154">A logistic regression model outputs the following node types:</span></span>  
  
|<span data-ttu-id="0e57e-155">ノードの種類の ID</span><span class="sxs-lookup"><span data-stu-id="0e57e-155">Node Type ID</span></span>|<span data-ttu-id="0e57e-156">説明</span><span class="sxs-lookup"><span data-stu-id="0e57e-156">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="0e57e-157">1</span><span class="sxs-lookup"><span data-stu-id="0e57e-157">1</span></span>|<span data-ttu-id="0e57e-158">モデル。</span><span class="sxs-lookup"><span data-stu-id="0e57e-158">Model.</span></span>|  
|<span data-ttu-id="0e57e-159">17</span><span class="sxs-lookup"><span data-stu-id="0e57e-159">17</span></span>|<span data-ttu-id="0e57e-160">サブネットワークのオーガナイザー ノード。</span><span class="sxs-lookup"><span data-stu-id="0e57e-160">Organizer node for the subnetwork.</span></span>|  
|<span data-ttu-id="0e57e-161">18</span><span class="sxs-lookup"><span data-stu-id="0e57e-161">18</span></span>|<span data-ttu-id="0e57e-162">入力層のオーガナイザー ノード。</span><span class="sxs-lookup"><span data-stu-id="0e57e-162">Organizer node for the input layer.</span></span>|  
|<span data-ttu-id="0e57e-163">19</span><span class="sxs-lookup"><span data-stu-id="0e57e-163">19</span></span>|<span data-ttu-id="0e57e-164">非表示層のオーガナイザー ノード。</span><span class="sxs-lookup"><span data-stu-id="0e57e-164">Organizer node for the hidden layer.</span></span> <span data-ttu-id="0e57e-165">非表示層は空です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-165">The hidden layer is empty.</span></span>|  
|<span data-ttu-id="0e57e-166">20</span><span class="sxs-lookup"><span data-stu-id="0e57e-166">20</span></span>|<span data-ttu-id="0e57e-167">出力層のオーガナイザー ノード。</span><span class="sxs-lookup"><span data-stu-id="0e57e-167">Organizer node for the output layer.</span></span>|  
|<span data-ttu-id="0e57e-168">21</span><span class="sxs-lookup"><span data-stu-id="0e57e-168">21</span></span>|<span data-ttu-id="0e57e-169">入力属性ノード。</span><span class="sxs-lookup"><span data-stu-id="0e57e-169">Input attribute node.</span></span>|  
|<span data-ttu-id="0e57e-170">23</span><span class="sxs-lookup"><span data-stu-id="0e57e-170">23</span></span>|<span data-ttu-id="0e57e-171">出力属性ノード。</span><span class="sxs-lookup"><span data-stu-id="0e57e-171">Output attribute node.</span></span>|  
|<span data-ttu-id="0e57e-172">24</span><span class="sxs-lookup"><span data-stu-id="0e57e-172">24</span></span>|<span data-ttu-id="0e57e-173">マージナル統計ノード。</span><span class="sxs-lookup"><span data-stu-id="0e57e-173">Marginal statistics node.</span></span>|  
  
 <span data-ttu-id="0e57e-174">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="0e57e-174">NODE_CAPTION</span></span>  
 <span data-ttu-id="0e57e-175">ノードに関連付けられたラベルまたはキャプション。</span><span class="sxs-lookup"><span data-stu-id="0e57e-175">A label or a caption associated with the node.</span></span> <span data-ttu-id="0e57e-176">ロジスティック回帰モデルでは常に空白です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-176">In logistic regression models, always blank.</span></span>  
  
 <span data-ttu-id="0e57e-177">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0e57e-177">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="0e57e-178">ノードの子の推定数。</span><span class="sxs-lookup"><span data-stu-id="0e57e-178">An estimate of the number of children that the node has.</span></span>  
  
|<span data-ttu-id="0e57e-179">Node</span><span class="sxs-lookup"><span data-stu-id="0e57e-179">Node</span></span>|<span data-ttu-id="0e57e-180">コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0e57e-180">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0e57e-181">モデル ルート</span><span class="sxs-lookup"><span data-stu-id="0e57e-181">Model root</span></span>|<span data-ttu-id="0e57e-182">子ノードの数を示します。1 つ以上のネットワーク、1 つの必須マージナル ノード、および 1 つの必須入力層が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-182">Indicates the count of child nodes, which includes at least 1 network, 1 required marginal node, and 1 required input layer.</span></span> <span data-ttu-id="0e57e-183">たとえば、値が 5 の場合はサブネットワークが 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="0e57e-183">For example, if the value is 5, there are 3 subnetworks.</span></span>|  
|<span data-ttu-id="0e57e-184">マージナル統計</span><span class="sxs-lookup"><span data-stu-id="0e57e-184">Marginal statistics</span></span>|<span data-ttu-id="0e57e-185">常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-185">Always 0.</span></span>|  
|<span data-ttu-id="0e57e-186">入力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-186">Input layer</span></span>|<span data-ttu-id="0e57e-187">モデルで使用された入力属性と値のペアの数を示します。</span><span class="sxs-lookup"><span data-stu-id="0e57e-187">Indicates the number of input attribute-values pairs that were used by the model.</span></span>|  
|<span data-ttu-id="0e57e-188">入力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-188">Input node</span></span>|<span data-ttu-id="0e57e-189">常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-189">Always 0.</span></span>|  
|<span data-ttu-id="0e57e-190">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0e57e-190">Hidden layer</span></span>|<span data-ttu-id="0e57e-191">ロジスティック回帰モデルでは常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-191">In a logistic regression model, always 0.</span></span>|  
|<span data-ttu-id="0e57e-192">出力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-192">Output layer</span></span>|<span data-ttu-id="0e57e-193">出力値の数を示します。</span><span class="sxs-lookup"><span data-stu-id="0e57e-193">Indicates the number of output values.</span></span>|  
|<span data-ttu-id="0e57e-194">出力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-194">Output node</span></span>|<span data-ttu-id="0e57e-195">常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-195">Always 0.</span></span>|  
  
 <span data-ttu-id="0e57e-196">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e57e-196">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="0e57e-197">ノードの親の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-197">The unique name of the node's parent.</span></span> <span data-ttu-id="0e57e-198">ルート レベルのノードには NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="0e57e-198">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="0e57e-199">モデルに関して名前と ID が表す構造情報の詳細については、「 [ノードの名前と ID の使用](#bkmk_NodeIDs)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e57e-199">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="0e57e-200">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e57e-200">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="0e57e-201">ノードについてのわかりやすい説明。</span><span class="sxs-lookup"><span data-stu-id="0e57e-201">A user-friendly description of the node.</span></span>  
  
|<span data-ttu-id="0e57e-202">Node</span><span class="sxs-lookup"><span data-stu-id="0e57e-202">Node</span></span>|<span data-ttu-id="0e57e-203">コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0e57e-203">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0e57e-204">モデル ルート</span><span class="sxs-lookup"><span data-stu-id="0e57e-204">Model root</span></span>|<span data-ttu-id="0e57e-205">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-205">Blank</span></span>|  
|<span data-ttu-id="0e57e-206">マージナル統計</span><span class="sxs-lookup"><span data-stu-id="0e57e-206">Marginal statistics</span></span>|<span data-ttu-id="0e57e-207">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-207">Blank</span></span>|  
|<span data-ttu-id="0e57e-208">入力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-208">Input layer</span></span>|<span data-ttu-id="0e57e-209">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-209">Blank</span></span>|  
|<span data-ttu-id="0e57e-210">入力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-210">Input node</span></span>|<span data-ttu-id="0e57e-211">入力属性名</span><span class="sxs-lookup"><span data-stu-id="0e57e-211">Input attribute name</span></span>|  
|<span data-ttu-id="0e57e-212">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0e57e-212">Hidden layer</span></span>|<span data-ttu-id="0e57e-213">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-213">Blank</span></span>|  
|<span data-ttu-id="0e57e-214">出力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-214">Output layer</span></span>|<span data-ttu-id="0e57e-215">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-215">Blank</span></span>|  
|<span data-ttu-id="0e57e-216">出力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-216">Output node</span></span>|<span data-ttu-id="0e57e-217">出力属性が連続属性の場合は、出力属性名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-217">If the output attribute is continuous, contains the name of the output attribute.</span></span><br /><br /> <span data-ttu-id="0e57e-218">出力属性が不連続属性または分離された属性の場合は、出力属性名と値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-218">If the output attribute is discrete or discretized, contains the name of the attribute and the value.</span></span>|  
  
 <span data-ttu-id="0e57e-219">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="0e57e-219">NODE_RULE</span></span>  
 <span data-ttu-id="0e57e-220">ノードに埋め込まれたルールの XML による記述。</span><span class="sxs-lookup"><span data-stu-id="0e57e-220">An XML description of the rule that is embedded in the node.</span></span>  
  
|<span data-ttu-id="0e57e-221">Node</span><span class="sxs-lookup"><span data-stu-id="0e57e-221">Node</span></span>|<span data-ttu-id="0e57e-222">コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0e57e-222">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0e57e-223">モデル ルート</span><span class="sxs-lookup"><span data-stu-id="0e57e-223">Model root</span></span>|<span data-ttu-id="0e57e-224">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-224">Blank</span></span>|  
|<span data-ttu-id="0e57e-225">マージナル統計</span><span class="sxs-lookup"><span data-stu-id="0e57e-225">Marginal statistics</span></span>|<span data-ttu-id="0e57e-226">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-226">Blank</span></span>|  
|<span data-ttu-id="0e57e-227">入力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-227">Input layer</span></span>|<span data-ttu-id="0e57e-228">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-228">Blank</span></span>|  
|<span data-ttu-id="0e57e-229">入力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-229">Input node</span></span>|<span data-ttu-id="0e57e-230">NODE_DESCRIPTION 列と同じ情報が含まれている XML フラグメント。</span><span class="sxs-lookup"><span data-stu-id="0e57e-230">An XML fragment containing the same information as the NODE_DESCRIPTION column.</span></span>|  
|<span data-ttu-id="0e57e-231">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0e57e-231">Hidden layer</span></span>|<span data-ttu-id="0e57e-232">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-232">Blank</span></span>|  
|<span data-ttu-id="0e57e-233">出力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-233">Output layer</span></span>|<span data-ttu-id="0e57e-234">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-234">Blank</span></span>|  
|<span data-ttu-id="0e57e-235">出力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-235">Output node</span></span>|<span data-ttu-id="0e57e-236">NODE_DESCRIPTION 列と同じ情報が含まれている XML フラグメント。</span><span class="sxs-lookup"><span data-stu-id="0e57e-236">An XML fragment containing the same information as the NODE_DESCRIPTION column.</span></span>|  
  
 <span data-ttu-id="0e57e-237">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="0e57e-237">MARGINAL_RULE</span></span>  
 <span data-ttu-id="0e57e-238">ロジスティック回帰モデルでは常に空白です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-238">For logistic regression models, always blank.</span></span>  
  
 <span data-ttu-id="0e57e-239">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="0e57e-239">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="0e57e-240">このノードに関連付けられている確率。</span><span class="sxs-lookup"><span data-stu-id="0e57e-240">The probability associated with this node.</span></span> <span data-ttu-id="0e57e-241">ロジスティック回帰モデルでは常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-241">For logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="0e57e-242">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="0e57e-242">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="0e57e-243">親ノードからノードに到達する確率です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-243">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="0e57e-244">ロジスティック回帰モデルでは常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-244">For logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="0e57e-245">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="0e57e-245">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="0e57e-246">ノードの統計情報を含む入れ子になったテーブル。</span><span class="sxs-lookup"><span data-stu-id="0e57e-246">A nested table that contains statistical information for the node.</span></span> <span data-ttu-id="0e57e-247">このテーブルのノードの種類ごとの内容の詳細については、「 [ニューラル ネットワーク モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e57e-247">For detailed information about the contents of this table for each node type, see the section, Understanding the NODE_DISTRIBUTION Table, in [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="0e57e-248">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="0e57e-248">NODE_SUPPORT</span></span>  
 <span data-ttu-id="0e57e-249">ロジスティック回帰モデルでは常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-249">For logistic regression models, always 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e57e-250">この種類のモデルの出力は確率論的でないため、サポート確率は常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-250">Support probabilities are always 0 because the output of this model type is not probabilistic.</span></span> <span data-ttu-id="0e57e-251">このアルゴリズムで意味を持つのは重みだけです。したがって、確率、サポート、および分散は計算されません。</span><span class="sxs-lookup"><span data-stu-id="0e57e-251">The only thing that is meaningful for the algorithm is the weights; therefore, the algorithm does not compute probability, support, or variance.</span></span>  
  
 <span data-ttu-id="0e57e-252">特定の値に対するトレーニング ケースでのサポートについて情報を得るには、マージナル統計ノードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e57e-252">To get information about the support in the training cases for specific values, see the marginal statistics node.</span></span>  
  
 <span data-ttu-id="0e57e-253">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="0e57e-253">MSOLAP_MODEL_COLUMN</span></span>  
 |<span data-ttu-id="0e57e-254">Node</span><span class="sxs-lookup"><span data-stu-id="0e57e-254">Node</span></span>|<span data-ttu-id="0e57e-255">コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0e57e-255">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="0e57e-256">モデル ルート</span><span class="sxs-lookup"><span data-stu-id="0e57e-256">Model root</span></span>|<span data-ttu-id="0e57e-257">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-257">Blank</span></span>|  
|<span data-ttu-id="0e57e-258">マージナル統計</span><span class="sxs-lookup"><span data-stu-id="0e57e-258">Marginal statistics</span></span>|<span data-ttu-id="0e57e-259">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-259">Blank</span></span>|  
|<span data-ttu-id="0e57e-260">入力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-260">Input layer</span></span>|<span data-ttu-id="0e57e-261">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-261">Blank</span></span>|  
|<span data-ttu-id="0e57e-262">入力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-262">Input node</span></span>|<span data-ttu-id="0e57e-263">入力属性名。</span><span class="sxs-lookup"><span data-stu-id="0e57e-263">Input attribute name.</span></span>|  
|<span data-ttu-id="0e57e-264">hidden layer</span><span class="sxs-lookup"><span data-stu-id="0e57e-264">Hidden layer</span></span>|<span data-ttu-id="0e57e-265">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-265">Blank</span></span>|  
|<span data-ttu-id="0e57e-266">出力層</span><span class="sxs-lookup"><span data-stu-id="0e57e-266">Output layer</span></span>|<span data-ttu-id="0e57e-267">新規</span><span class="sxs-lookup"><span data-stu-id="0e57e-267">Blank</span></span>|  
|<span data-ttu-id="0e57e-268">出力ノード</span><span class="sxs-lookup"><span data-stu-id="0e57e-268">Output node</span></span>|<span data-ttu-id="0e57e-269">入力属性名。</span><span class="sxs-lookup"><span data-stu-id="0e57e-269">Input attribute name.</span></span>|  
  
 <span data-ttu-id="0e57e-270">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="0e57e-270">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="0e57e-271">ロジスティック回帰モデルでは常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-271">In logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="0e57e-272">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="0e57e-272">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="0e57e-273">ロジスティック回帰モデルでは常に空白です。</span><span class="sxs-lookup"><span data-stu-id="0e57e-273">In logistic regression models, always blank.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_NodeIDs"></a><span data-ttu-id="0e57e-274">ノード名と Id の使用</span><span class="sxs-lookup"><span data-stu-id="0e57e-274">Using Node Names and IDs</span></span>  
 <span data-ttu-id="0e57e-275">ロジスティック回帰モデルのノードの名前付けでは、モデル内のノード間のリレーションシップに関する追加情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="0e57e-275">The naming of the nodes in a logistic regression model provides additional information about the relationships between nodes in the model.</span></span> <span data-ttu-id="0e57e-276">次の表に、各層のノードに割り当てられる ID の規則を示します。</span><span class="sxs-lookup"><span data-stu-id="0e57e-276">The following table shows the conventions for the IDs that are assigned to nodes in each layer.</span></span>  
  
|<span data-ttu-id="0e57e-277">ノードの種類</span><span class="sxs-lookup"><span data-stu-id="0e57e-277">Node Type</span></span>|<span data-ttu-id="0e57e-278">ノード ID の規則</span><span class="sxs-lookup"><span data-stu-id="0e57e-278">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="0e57e-279">モデル ルート (1)</span><span class="sxs-lookup"><span data-stu-id="0e57e-279">Model root (1)</span></span>|<span data-ttu-id="0e57e-280">00000000000000000.</span><span class="sxs-lookup"><span data-stu-id="0e57e-280">00000000000000000.</span></span>|  
|<span data-ttu-id="0e57e-281">マージナル統計ノード (24)</span><span class="sxs-lookup"><span data-stu-id="0e57e-281">Marginal statistics node (24)</span></span>|<span data-ttu-id="0e57e-282">10000000000000000</span><span class="sxs-lookup"><span data-stu-id="0e57e-282">10000000000000000</span></span>|  
|<span data-ttu-id="0e57e-283">入力層 (18)</span><span class="sxs-lookup"><span data-stu-id="0e57e-283">Input layer (18)</span></span>|<span data-ttu-id="0e57e-284">30000000000000000</span><span class="sxs-lookup"><span data-stu-id="0e57e-284">30000000000000000</span></span>|  
|<span data-ttu-id="0e57e-285">入力ノード (21)</span><span class="sxs-lookup"><span data-stu-id="0e57e-285">Input node (21)</span></span>|<span data-ttu-id="0e57e-286">60000000000000000 から開始</span><span class="sxs-lookup"><span data-stu-id="0e57e-286">Starts at 60000000000000000</span></span>|  
|<span data-ttu-id="0e57e-287">サブネットワーク (17)</span><span class="sxs-lookup"><span data-stu-id="0e57e-287">Subnetwork (17)</span></span>|<span data-ttu-id="0e57e-288">20000000000000000</span><span class="sxs-lookup"><span data-stu-id="0e57e-288">20000000000000000</span></span>|  
|<span data-ttu-id="0e57e-289">非表示層 (19)</span><span class="sxs-lookup"><span data-stu-id="0e57e-289">Hidden layer (19)</span></span>|<span data-ttu-id="0e57e-290">40000000000000000</span><span class="sxs-lookup"><span data-stu-id="0e57e-290">40000000000000000</span></span>|  
|<span data-ttu-id="0e57e-291">出力層 (20)</span><span class="sxs-lookup"><span data-stu-id="0e57e-291">Output layer (20)</span></span>|<span data-ttu-id="0e57e-292">50000000000000000</span><span class="sxs-lookup"><span data-stu-id="0e57e-292">50000000000000000</span></span>|  
|<span data-ttu-id="0e57e-293">出力ノード (23)</span><span class="sxs-lookup"><span data-stu-id="0e57e-293">Output node (23)</span></span>|<span data-ttu-id="0e57e-294">80000000000000000 から開始</span><span class="sxs-lookup"><span data-stu-id="0e57e-294">Starts at 80000000000000000</span></span>|  
  
 <span data-ttu-id="0e57e-295">出力属性が特定の入力層属性にどのように関連付けられているかをこれらの ID によって確認するには、出力ノードの NODE_DISTRIBUTION テーブルを表示します。</span><span class="sxs-lookup"><span data-stu-id="0e57e-295">You can use these IDs to determine how output attributes are related to specific input layer attributes, by viewing the NODE_DISTRIBUTION table of the output node.</span></span> <span data-ttu-id="0e57e-296">NODE_DISTRIBUTION テーブルの各行には、特定の入力属性ノードを指す ID が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e57e-296">Each row in that table contains an ID that points back to a specific input attribute node.</span></span> <span data-ttu-id="0e57e-297">NODE_DISTRIBUTION テーブルには、その入力と出力のペアの係数も含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e57e-297">The NODE_DISTRIBUTION table also contains the coefficient for that input-output pair.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e57e-298">参照</span><span class="sxs-lookup"><span data-stu-id="0e57e-298">See Also</span></span>  
 <span data-ttu-id="0e57e-299">[Microsoft ロジスティック回帰アルゴリズム](microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="0e57e-299">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="0e57e-300">[ニューラルネットワークモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0e57e-300">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="0e57e-301">[ロジスティック回帰モデルのクエリ例](logistic-regression-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="0e57e-301">[Logistic Regression Model Query Examples](logistic-regression-model-query-examples.md) </span></span>  
 [<span data-ttu-id="0e57e-302">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="0e57e-302">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)  
  
  
