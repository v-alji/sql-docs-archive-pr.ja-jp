---
title: 線形回帰モデルのマイニングモデルコンテンツ (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- mining model content, linear regression models
- regression algorithms [Analysis Services]
ms.assetid: a6abcb75-524e-4e0a-a375-c10475ac0a9d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cb41cf0053f236b4bda8d4520030603a391d1c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717037"
---
# <a name="mining-model-content-for-linear-regression-models-analysis-services---data-mining"></a><span data-ttu-id="b8924-102">線形回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="b8924-102">Mining Model Content for Linear Regression Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="b8924-103">このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを使用するモデルに固有のマイニング モデル コンテンツについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b8924-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span> <span data-ttu-id="b8924-104">すべての種類のモデルのマイニング モデル コンテンツの一般的な説明については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」 (マイニング モデル コンテンツ (Analysis Services - データ マイニング)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8924-104">For a general explanation of mining model content for all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-linear-regression-model"></a><span data-ttu-id="b8924-105">線形回帰モデルの構造について</span><span class="sxs-lookup"><span data-stu-id="b8924-105">Understanding the Structure of a Linear Regression Model</span></span>  
 <span data-ttu-id="b8924-106">線形回帰モデルの構造は非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="b8924-106">A linear regression model has an extremely simple structure.</span></span> <span data-ttu-id="b8924-107">各モデルには、モデルとそのメタデータを表す1つの親ノードと、予測可能な各属性の回帰式を含む回帰ツリーノード (NODE_TYPE = 25) があります。</span><span class="sxs-lookup"><span data-stu-id="b8924-107">Each model has a single parent node that represents the model and its metadata, and a regression tree node (NODE_TYPE = 25) that contains the regression formula for each predictable attribute.</span></span>  
  
 <span data-ttu-id="b8924-108">![線形回帰のモデルの構造](../media/modelcontentstructure-linreg.gif "線形回帰のモデルの構造")</span><span class="sxs-lookup"><span data-stu-id="b8924-108">![Structure of model for linear regression](../media/modelcontentstructure-linreg.gif "Structure of model for linear regression")</span></span>  
  
 <span data-ttu-id="b8924-109">線形回帰モデルでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリーと同じアルゴリズムが使用されますが、ツリーを制約するために使用されるパラメーターが異なっており、また連続属性のみが入力として受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="b8924-109">Linear regression models use the same algorithm as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees, but different parameters are used to constrain the tree, and only continuous attributes are accepted as inputs.</span></span> <span data-ttu-id="b8924-110">ただし、線形回帰モデルは [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムに基づいているため、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー ビューアーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="b8924-110">However, because linear regression models are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm, linear regression models are displayed by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Tree Viewer.</span></span> <span data-ttu-id="b8924-111">詳細については、「 [Microsoft ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-tree-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8924-111">For information, see [Browse a Model Using the Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="b8924-112">次のセクションでは、回帰式ノードの情報を解釈する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8924-112">The next section explains how to interpret information in the regression formula node.</span></span> <span data-ttu-id="b8924-113">この情報は、線形回帰モデルだけでなく、ツリーの一部に回帰を含むデシジョン ツリー モデルにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-113">This information applies not only to linear regression models, but also to decision trees models that contain regressions in a portion of the tree.</span></span>  
  
## <a name="model-content-for-a-linear-regression-model"></a><span data-ttu-id="b8924-114">線形回帰モデルのモデル コンテンツ</span><span class="sxs-lookup"><span data-stu-id="b8924-114">Model Content for a Linear Regression Model</span></span>  
 <span data-ttu-id="b8924-115">ここでは、マイニング モデル コンテンツの列のうち、線形回帰に関連する列についてのみ詳細と例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="b8924-115">This section provides detail and examples only for those columns in the mining model content that have particular relevance for linear regression.</span></span>  
  
 <span data-ttu-id="b8924-116">スキーマ行セットの汎用の列の詳細については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」(マイニング モデル コンテンツ (Analysis Services - データ マイニング)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8924-116">For information about general-purpose columns in the schema rowset, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="b8924-117">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b8924-117">MODEL_CATALOG</span></span>  
 <span data-ttu-id="b8924-118">モデルが格納されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="b8924-118">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="b8924-119">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="b8924-119">MODEL_NAME</span></span>  
 <span data-ttu-id="b8924-120">モデルの名前。</span><span class="sxs-lookup"><span data-stu-id="b8924-120">Name of the model.</span></span>  
  
 <span data-ttu-id="b8924-121">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="b8924-121">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="b8924-122">**ルート ノード :** 空白。</span><span class="sxs-lookup"><span data-stu-id="b8924-122">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="b8924-123">**回帰ノード :** 予測可能な属性の名前。</span><span class="sxs-lookup"><span data-stu-id="b8924-123">**Regression node:** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="b8924-124">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="b8924-124">NODE_NAME</span></span>  
 <span data-ttu-id="b8924-125">常に NODE_UNIQUE_NAME と同じです。</span><span class="sxs-lookup"><span data-stu-id="b8924-125">Always same as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="b8924-126">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="b8924-126">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="b8924-127">モデル内のノードの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="b8924-127">A unique identifier for the node within the model.</span></span> <span data-ttu-id="b8924-128">この値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="b8924-128">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="b8924-129">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b8924-129">NODE_TYPE</span></span>  
 <span data-ttu-id="b8924-130">線形回帰モデルでは次の種類のノードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-130">A linear regression model outputs the following node types:</span></span>  
  
|<span data-ttu-id="b8924-131">ノードの種類の ID</span><span class="sxs-lookup"><span data-stu-id="b8924-131">Node Type ID</span></span>|<span data-ttu-id="b8924-132">Type</span><span class="sxs-lookup"><span data-stu-id="b8924-132">Type</span></span>|<span data-ttu-id="b8924-133">説明</span><span class="sxs-lookup"><span data-stu-id="b8924-133">Description</span></span>|  
|------------------|----------|-----------------|  
|<span data-ttu-id="b8924-134">25</span><span class="sxs-lookup"><span data-stu-id="b8924-134">25</span></span>|<span data-ttu-id="b8924-135">回帰ツリーのルート</span><span class="sxs-lookup"><span data-stu-id="b8924-135">Regression tree root</span></span>|<span data-ttu-id="b8924-136">入力変数と出力変数のリレーションシップを表す数式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8924-136">Contains the formula that describes the relationship between the input and output variable.</span></span>|  
  
 <span data-ttu-id="b8924-137">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="b8924-137">NODE_CAPTION</span></span>  
 <span data-ttu-id="b8924-138">ノードに関連付けられたラベルまたはキャプション。</span><span class="sxs-lookup"><span data-stu-id="b8924-138">A label or a caption associated with the node.</span></span> <span data-ttu-id="b8924-139">このプロパティは、主に表示を目的としています。</span><span class="sxs-lookup"><span data-stu-id="b8924-139">This property is primarily for display purposes.</span></span>  
  
 <span data-ttu-id="b8924-140">**ルート ノード :** 空白。</span><span class="sxs-lookup"><span data-stu-id="b8924-140">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="b8924-141">**回帰ノード :** すべて。</span><span class="sxs-lookup"><span data-stu-id="b8924-141">**Regression node:** All.</span></span>  
  
 <span data-ttu-id="b8924-142">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="b8924-142">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="b8924-143">ノードの子の推定数。</span><span class="sxs-lookup"><span data-stu-id="b8924-143">An estimate of the number of children that the node has.</span></span>  
  
 <span data-ttu-id="b8924-144">**ルート ノード :** 回帰ノードの数を示します。</span><span class="sxs-lookup"><span data-stu-id="b8924-144">**Root node:** Indicates the number of regression nodes.</span></span> <span data-ttu-id="b8924-145">モデルの予測可能な属性ごとに 1 つの回帰ノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-145">One regression node is created for each predictable attribute in the model.</span></span>  
  
 <span data-ttu-id="b8924-146">**回帰ノード :** 常に 0。</span><span class="sxs-lookup"><span data-stu-id="b8924-146">**Regression node:** Always 0.</span></span>  
  
 <span data-ttu-id="b8924-147">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="b8924-147">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="b8924-148">ノードの親の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="b8924-148">The unique name of the node's parent.</span></span> <span data-ttu-id="b8924-149">ルート レベルのノードには NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="b8924-149">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="b8924-150">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b8924-150">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="b8924-151">ノードの説明です。</span><span class="sxs-lookup"><span data-stu-id="b8924-151">A description of the node.</span></span>  
  
 <span data-ttu-id="b8924-152">**ルート ノード :** 空白。</span><span class="sxs-lookup"><span data-stu-id="b8924-152">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="b8924-153">**回帰ノード :** すべて。</span><span class="sxs-lookup"><span data-stu-id="b8924-153">**Regression node:** All.</span></span>  
  
 <span data-ttu-id="b8924-154">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="b8924-154">NODE_RULE</span></span>  
 <span data-ttu-id="b8924-155">線形回帰モデルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="b8924-155">Not used for linear regression models.</span></span>  
  
 <span data-ttu-id="b8924-156">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="b8924-156">MARGINAL_RULE</span></span>  
 <span data-ttu-id="b8924-157">線形回帰モデルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="b8924-157">Not used for linear regression models.</span></span>  
  
 <span data-ttu-id="b8924-158">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b8924-158">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="b8924-159">このノードに関連付けられている確率。</span><span class="sxs-lookup"><span data-stu-id="b8924-159">The probability associated with this node.</span></span>  
  
 <span data-ttu-id="b8924-160">**ルート ノード :** 0</span><span class="sxs-lookup"><span data-stu-id="b8924-160">**Root node:** 0</span></span>  
  
 <span data-ttu-id="b8924-161">**回帰ノード :** 1</span><span class="sxs-lookup"><span data-stu-id="b8924-161">**Regression node:** 1</span></span>  
  
 <span data-ttu-id="b8924-162">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b8924-162">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="b8924-163">親ノードからノードに到達する確率です。</span><span class="sxs-lookup"><span data-stu-id="b8924-163">The probability of reaching the node from the parent node.</span></span>  
  
 <span data-ttu-id="b8924-164">**ルート ノード :** 0</span><span class="sxs-lookup"><span data-stu-id="b8924-164">**Root node:** 0</span></span>  
  
 <span data-ttu-id="b8924-165">**回帰ノード :** 1</span><span class="sxs-lookup"><span data-stu-id="b8924-165">**Regression node:** 1</span></span>  
  
 <span data-ttu-id="b8924-166">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="b8924-166">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="b8924-167">ノード内の値に関する統計情報を提供する、入れ子になったテーブル。</span><span class="sxs-lookup"><span data-stu-id="b8924-167">A nested table that provides statistics about the values in the node.</span></span>  
  
 <span data-ttu-id="b8924-168">**ルート ノード :** 0</span><span class="sxs-lookup"><span data-stu-id="b8924-168">**Root node:** 0</span></span>  
  
 <span data-ttu-id="b8924-169">**回帰ノード :** 回帰式の作成に使用される要素を含むテーブル。</span><span class="sxs-lookup"><span data-stu-id="b8924-169">**Regression node:** A table that contains the elements used to build the regression formula.</span></span> <span data-ttu-id="b8924-170">回帰ノードには、次の値型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8924-170">A regression node contains the following value types:</span></span>  
  
|<span data-ttu-id="b8924-171">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="b8924-171">VALUETYPE</span></span>|  
|---------------|  
|<span data-ttu-id="b8924-172">1 (Missing: 不足)</span><span class="sxs-lookup"><span data-stu-id="b8924-172">1 (Missing)</span></span>|  
|<span data-ttu-id="b8924-173">3 (Continuous: 連続)</span><span class="sxs-lookup"><span data-stu-id="b8924-173">3 (Continuous)</span></span>|  
|<span data-ttu-id="b8924-174">7 (Coefficient: 係数)</span><span class="sxs-lookup"><span data-stu-id="b8924-174">7 (Coefficient)</span></span>|  
|<span data-ttu-id="b8924-175">8 (Score Gain: スコア ゲイン)</span><span class="sxs-lookup"><span data-stu-id="b8924-175">8 (Score Gain)</span></span>|  
|<span data-ttu-id="b8924-176">9 (Statistics: 統計)</span><span class="sxs-lookup"><span data-stu-id="b8924-176">9 (Statistics)</span></span>|  
|<span data-ttu-id="b8924-177">11 (Intercept: 切片)</span><span class="sxs-lookup"><span data-stu-id="b8924-177">11 (Intercept)</span></span>|  
  
 <span data-ttu-id="b8924-178">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="b8924-178">NODE_SUPPORT</span></span>  
 <span data-ttu-id="b8924-179">このノードをサポートするケースの数。</span><span class="sxs-lookup"><span data-stu-id="b8924-179">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="b8924-180">**ルート ノード :** 0</span><span class="sxs-lookup"><span data-stu-id="b8924-180">**Root node:** 0</span></span>  
  
 <span data-ttu-id="b8924-181">**回帰ノード :** トレーニング ケースの数。</span><span class="sxs-lookup"><span data-stu-id="b8924-181">**Regression node:** Count of training cases.</span></span>  
  
 <span data-ttu-id="b8924-182">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="b8924-182">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="b8924-183">予測可能な属性の名前。</span><span class="sxs-lookup"><span data-stu-id="b8924-183">Name of predictable attribute.</span></span>  
  
 <span data-ttu-id="b8924-184">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="b8924-184">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="b8924-185">NODE_PROBABILITY と同じ。</span><span class="sxs-lookup"><span data-stu-id="b8924-185">Same as NODE_PROBABILITY</span></span>  
  
 <span data-ttu-id="b8924-186">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="b8924-186">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="b8924-187">表示目的で使用されるラベル。</span><span class="sxs-lookup"><span data-stu-id="b8924-187">Label used for display purposes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8924-188">解説</span><span class="sxs-lookup"><span data-stu-id="b8924-188">Remarks</span></span>  
 <span data-ttu-id="b8924-189">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを使用してモデルを作成すると、データ マイニング エンジンにより、デシジョン ツリー モデルの特殊なインスタンスが作成され、1 つのノードにすべてのトレーニング データを格納するようにツリーを制約するパラメーターが設定されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-189">When you create a model by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, the data mining engine creates a special instance of a decision trees model and supplies parameters that constrain the tree to contain all the training data in a single node.</span></span> <span data-ttu-id="b8924-190">連続する入力はすべて、リグレッサー候補としてフラグが付けられ、評価されます。ただし、リグレッサーとして最終的なモデルに保持されるのは、データに適合するリグレッサーだけです。</span><span class="sxs-lookup"><span data-stu-id="b8924-190">All continuous inputs are flagged and evaluated as potential regressors, but only those regressors that fit the data are retained as regressors in the final model.</span></span> <span data-ttu-id="b8924-191">分析では、リグレッサーごとに 1 つの回帰式が生成されるか、回帰式がまったく生成されないかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="b8924-191">The analysis produces either a single regression formula for each regressor or no regression formula at all.</span></span>  
  
 <span data-ttu-id="b8924-192">**Microsoft ツリー ビューアー**で **[(すべて)]** ノードをクリックすると、完全な回帰式が [[マイニング凡例]](browse-a-model-using-the-microsoft-tree-viewer.md)に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-192">You can view the complete regression formula in the **Mining Legend**, by clicking the **(All)** node in the [Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="b8924-193">また、連続する予測可能な属性を含むデシジョン ツリー モデルを作成した場合、回帰ツリー ノードのプロパティを共有する回帰ノードがツリーに含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="b8924-193">Also, when you create a decision trees model that includes a continuous predictable attribute, sometimes the tree has regression nodes that share the properties of regression tree nodes.</span></span>  
  
##  <a name="node-distribution-for-continuous-attributes"></a><a name="NodeDist_Regression"></a> <span data-ttu-id="b8924-194">連続属性のノード分布</span><span class="sxs-lookup"><span data-stu-id="b8924-194">Node Distribution for Continuous Attributes</span></span>  
 <span data-ttu-id="b8924-195">回帰ノードの重要な情報の大部分は、NODE_DISTRIBUTION テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-195">Most of the important information in a regression node is contained in the NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="b8924-196">次の例は、NODE_DISTRIBUTION  テーブルのレイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="b8924-196">The following example illustrates the layout of the NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="b8924-197">この例では、Targeted Mailing マイニング構造を使用して、年齢に基づいて顧客の収入を予測する線形回帰モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8924-197">In this example, the Targeted Mailing mining structure has been used to create a linear regression model that predicts customer income based on age.</span></span> <span data-ttu-id="b8924-198">このモデルは単に説明をわかりやすくするためのものであり、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] の既存のサンプル データとマイニング構造を使用して簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="b8924-198">The model is for the purpose of illustration only, because it can be built easily using the existing [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample data and mining structure.</span></span>  
  
|<span data-ttu-id="b8924-199">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="b8924-199">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="b8924-200">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="b8924-200">ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="b8924-201">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="b8924-201">SUPPORT</span></span>|<span data-ttu-id="b8924-202">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="b8924-202">PROBABILITY</span></span>|<span data-ttu-id="b8924-203">variance</span><span class="sxs-lookup"><span data-stu-id="b8924-203">VARIANCE</span></span>|<span data-ttu-id="b8924-204">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="b8924-204">VALUETYPE</span></span>|  
|---------------------|----------------------|-------------|-----------------|--------------|---------------|  
|<span data-ttu-id="b8924-205">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="b8924-205">Yearly Income</span></span>|<span data-ttu-id="b8924-206">Missing</span><span class="sxs-lookup"><span data-stu-id="b8924-206">Missing</span></span>|<span data-ttu-id="b8924-207">0</span><span class="sxs-lookup"><span data-stu-id="b8924-207">0</span></span>|<span data-ttu-id="b8924-208">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="b8924-208">0.000457142857142857</span></span>|<span data-ttu-id="b8924-209">0</span><span class="sxs-lookup"><span data-stu-id="b8924-209">0</span></span>|<span data-ttu-id="b8924-210">1</span><span class="sxs-lookup"><span data-stu-id="b8924-210">1</span></span>|  
|<span data-ttu-id="b8924-211">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="b8924-211">Yearly Income</span></span>|<span data-ttu-id="b8924-212">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="b8924-212">57220.8876687257</span></span>|<span data-ttu-id="b8924-213">17484</span><span class="sxs-lookup"><span data-stu-id="b8924-213">17484</span></span>|<span data-ttu-id="b8924-214">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="b8924-214">0.999542857142857</span></span>|<span data-ttu-id="b8924-215">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="b8924-215">1041275619.52776</span></span>|<span data-ttu-id="b8924-216">3</span><span class="sxs-lookup"><span data-stu-id="b8924-216">3</span></span>|  
|<span data-ttu-id="b8924-217">年齢</span><span class="sxs-lookup"><span data-stu-id="b8924-217">Age</span></span>|<span data-ttu-id="b8924-218">471.687717702463</span><span class="sxs-lookup"><span data-stu-id="b8924-218">471.687717702463</span></span>|<span data-ttu-id="b8924-219">0</span><span class="sxs-lookup"><span data-stu-id="b8924-219">0</span></span>|<span data-ttu-id="b8924-220">0</span><span class="sxs-lookup"><span data-stu-id="b8924-220">0</span></span>|<span data-ttu-id="b8924-221">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="b8924-221">126.969442359327</span></span>|<span data-ttu-id="b8924-222">7</span><span class="sxs-lookup"><span data-stu-id="b8924-222">7</span></span>|  
|<span data-ttu-id="b8924-223">年齢</span><span class="sxs-lookup"><span data-stu-id="b8924-223">Age</span></span>|<span data-ttu-id="b8924-224">234.680904692439</span><span class="sxs-lookup"><span data-stu-id="b8924-224">234.680904692439</span></span>|<span data-ttu-id="b8924-225">0</span><span class="sxs-lookup"><span data-stu-id="b8924-225">0</span></span>|<span data-ttu-id="b8924-226">0</span><span class="sxs-lookup"><span data-stu-id="b8924-226">0</span></span>|<span data-ttu-id="b8924-227">0</span><span class="sxs-lookup"><span data-stu-id="b8924-227">0</span></span>|<span data-ttu-id="b8924-228">8</span><span class="sxs-lookup"><span data-stu-id="b8924-228">8</span></span>|  
|<span data-ttu-id="b8924-229">年齢</span><span class="sxs-lookup"><span data-stu-id="b8924-229">Age</span></span>|<span data-ttu-id="b8924-230">45.4269617936399</span><span class="sxs-lookup"><span data-stu-id="b8924-230">45.4269617936399</span></span>|<span data-ttu-id="b8924-231">0</span><span class="sxs-lookup"><span data-stu-id="b8924-231">0</span></span>|<span data-ttu-id="b8924-232">0</span><span class="sxs-lookup"><span data-stu-id="b8924-232">0</span></span>|<span data-ttu-id="b8924-233">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="b8924-233">126.969442359327</span></span>|<span data-ttu-id="b8924-234">9</span><span class="sxs-lookup"><span data-stu-id="b8924-234">9</span></span>|  
||<span data-ttu-id="b8924-235">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="b8924-235">35793.5477381267</span></span>|<span data-ttu-id="b8924-236">0</span><span class="sxs-lookup"><span data-stu-id="b8924-236">0</span></span>|<span data-ttu-id="b8924-237">0</span><span class="sxs-lookup"><span data-stu-id="b8924-237">0</span></span>|<span data-ttu-id="b8924-238">1012968919.28372</span><span class="sxs-lookup"><span data-stu-id="b8924-238">1012968919.28372</span></span>|<span data-ttu-id="b8924-239">11</span><span class="sxs-lookup"><span data-stu-id="b8924-239">11</span></span>|  
  
 <span data-ttu-id="b8924-240">NODE_DISTRIBUTION テーブルには複数の行が格納されており、各行は変数でグループ化されています。</span><span class="sxs-lookup"><span data-stu-id="b8924-240">The NODE_DISTRIBUTION table contains multiple rows, each grouped by a variable.</span></span> <span data-ttu-id="b8924-241">最初の 2 行は、値型が常に 1 と 3 で、対象の属性を表します。</span><span class="sxs-lookup"><span data-stu-id="b8924-241">The first two rows are always value types 1 and 3, and describe the target attribute.</span></span> <span data-ttu-id="b8924-242">3 行目以降の行は、特定の *リグレッサー*の数式に関する詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="b8924-242">The succeeding rows provide details about the formula for a particular *regressor*.</span></span> <span data-ttu-id="b8924-243">リグレッサーは、出力変数との間に線形のリレーションシップがある入力変数です。</span><span class="sxs-lookup"><span data-stu-id="b8924-243">A regressor is an input variable that has a linear relationship with the output variable.</span></span> <span data-ttu-id="b8924-244">リグレッサーは複数作成することができ、各リグレッサーには、係数 (VALUETYPE = 7)、スコア ゲイン (VALUETYPE = 8)、および統計 (VALUETYPE = 9) が格納される個別の行が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-244">You can have multiple regressors, and each regressor will have a separate row for the coefficient (VALUETYPE = 7), score gain (VALUETYPE = 8), and statistics (VALUETYPE = 9).</span></span> <span data-ttu-id="b8924-245">さらに、テーブルには、式の切片 (VALUETYPE = 11) が格納される行も含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8924-245">Finally, the table has a row that contains the intercept of the equation (VALUETYPE = 11).</span></span>  
  
### <a name="elements-of-the-regression-formula"></a><span data-ttu-id="b8924-246">回帰式の要素</span><span class="sxs-lookup"><span data-stu-id="b8924-246">Elements of the Regression Formula</span></span>  
 <span data-ttu-id="b8924-247">入れ子になった NODE_DISTRIBUTION テーブルでは、回帰式の各要素が個別の行に格納されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-247">The nested NODE_DISTRIBUTION table contains each element of the regression formula in a separate row.</span></span> <span data-ttu-id="b8924-248">例の結果に含まれるデータの最初の 2 行には、従属変数を表す予測可能な属性である **Yearly Income**に関する情報が格納されています。</span><span class="sxs-lookup"><span data-stu-id="b8924-248">The first two rows of data in the example results contain information about the predictable attribute, **Yearly Income**, which models the dependent variable.</span></span> <span data-ttu-id="b8924-249">SUPPORT 列には、この属性の 2 つの状態 ( **Yearly Income** 値が使用できたことを示す状態と **Yearly Income** 値が不測していたことを示す状態) をサポートするケースの数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-249">The SUPPORT column shows the count of cases in support of the two states of this attribute: either a **Yearly Income** value was available, or the **Yearly Income** value was missing.</span></span>  
  
 <span data-ttu-id="b8924-250">VARIANCE 列には、予測可能な属性の計算された分散が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-250">The VARIANCE column tells you the computed variance of the predictable attribute.</span></span> <span data-ttu-id="b8924-251">*分散* は、予想される分布でサンプル内の値がどのぐらい分散しているかを示す尺度です。</span><span class="sxs-lookup"><span data-stu-id="b8924-251">*Variance* is a measure of how scattered the values are in a sample, given an expected distribution.</span></span> <span data-ttu-id="b8924-252">ここでは、平均値からの偏差の 2 乗の平均を取ることで分散を算出しています。</span><span class="sxs-lookup"><span data-stu-id="b8924-252">Variance here is calculated by taking the average of the squared deviation from the mean.</span></span> <span data-ttu-id="b8924-253">分散の平方根は標準偏差とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b8924-253">The square root of the variance is also known as standard deviation.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="b8924-254">では標準偏差は提供されませんが、簡単に計算することができます。</span><span class="sxs-lookup"><span data-stu-id="b8924-254">does not provide the standard deviation but you can easily calculate it.</span></span>  
  
 <span data-ttu-id="b8924-255">リグレッサーごとに 3 つの行が出力されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-255">For each regressor, three rows are output.</span></span> <span data-ttu-id="b8924-256">これらの行には、係数、スコア ゲイン、およびリグレッサーの統計が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-256">They contain the coefficient, score gain, and regressor statistics.</span></span>  
  
 <span data-ttu-id="b8924-257">テーブルの最後の行には、式の切片 (VALUETYPE = 11) が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-257">Finally, the table contains a row that provides the intercept for the equation.</span></span>  
  
#### <a name="coefficient"></a><span data-ttu-id="b8924-258">Coefficient</span><span class="sxs-lookup"><span data-stu-id="b8924-258">Coefficient</span></span>  
 <span data-ttu-id="b8924-259">リグレッサーごとに係数 (VALUETYPE = 7) が計算されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-259">For each regressor, a coefficient (VALUETYPE = 7) is calculated.</span></span> <span data-ttu-id="b8924-260">係数自体は ATTRIBUTE_VALUE 列に表示されますが、係数の分散は VARIANCE 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-260">The coefficient itself appears in the ATTRIBUTE_VALUE column, whereas the VARIANCE column tells you the variance for the coefficient.</span></span> <span data-ttu-id="b8924-261">係数は、線形性が最も高くなるように計算されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-261">The coefficients are calculated so as to maximize linearity.</span></span>  
  
#### <a name="score-gain"></a><span data-ttu-id="b8924-262">スコア ゲイン</span><span class="sxs-lookup"><span data-stu-id="b8924-262">Score Gain</span></span>  
 <span data-ttu-id="b8924-263">各リグレッサーのスコア ゲイン (VALUETYPE = 8) は、属性の興味深さのスコアを表します。</span><span class="sxs-lookup"><span data-stu-id="b8924-263">The score gain (VALUETYPE = 8) for each regressor represents the interestingness score of the attribute.</span></span> <span data-ttu-id="b8924-264">この値を使用すると、複数のリグレッサーの有用性を評価できます。</span><span class="sxs-lookup"><span data-stu-id="b8924-264">You can use this value to estimate the usefulness of multiple regressors.</span></span>  
  
#### <a name="statistics"></a><span data-ttu-id="b8924-265">統計</span><span class="sxs-lookup"><span data-stu-id="b8924-265">Statistics</span></span>  
 <span data-ttu-id="b8924-266">リグレッサー統計 (VALUETYPE = 9) は、値があるケースの属性の平均値です。</span><span class="sxs-lookup"><span data-stu-id="b8924-266">The regressor statistic (VALUETYPE = 9) is the mean for the attribute for cases that have a value.</span></span> <span data-ttu-id="b8924-267">平均値自体は ATTRIBUTE_VALUE 列に表示されますが、平均値からの偏差の合計は VARIANCE 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-267">The ATTRIBUTE_VALUE column contains the mean itself, whereas the VARIANCE column contains the sum of deviations from the mean.</span></span>  
  
#### <a name="intercept"></a><span data-ttu-id="b8924-268">Intercept</span><span class="sxs-lookup"><span data-stu-id="b8924-268">Intercept</span></span>  
 <span data-ttu-id="b8924-269">通常、回帰式の *切片* (VALUETYPE = 11) または *残余* は、入力属性が 0 の位置にあるときの予測可能な属性の値を示します。</span><span class="sxs-lookup"><span data-stu-id="b8924-269">Normally, the *intercept* (VALUETYPE = 11) or *residual* in a regression equation tells you the value of the predictable attribute, at the point where the input attribute, is 0.</span></span> <span data-ttu-id="b8924-270">入力属性が 0 になることは通常はありません。0 になった場合、直観に反する結果が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="b8924-270">In many cases, this might not happen, and could lead to counterintuitive results.</span></span>  
  
 <span data-ttu-id="b8924-271">たとえば、年齢に基づいて収入を予測するモデルでは、年齢が 0 のときの収入がわかっても役には立ちません。</span><span class="sxs-lookup"><span data-stu-id="b8924-271">For example, in a model that predicts income based on age, it is useless to learn the income at age 0.</span></span> <span data-ttu-id="b8924-272">実際には、平均値に対する線の挙動を知る方が通常は役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b8924-272">In real-life, it is typically more useful to know about the behavior of the line with respect to average values.</span></span> <span data-ttu-id="b8924-273">したがって、は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 平均値とのリレーションシップで各リグレッサーを表すようにインターセプトを変更します。</span><span class="sxs-lookup"><span data-stu-id="b8924-273">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] modifies the intercept to express each regressor in a relationship with the mean.</span></span>  
  
 <span data-ttu-id="b8924-274">この変更は、マイニング モデル コンテンツで確認するのは困難ですが、 **Microsoft ツリー ビューアー** の **[マイニング凡例]** で完全な回帰式を表示するとすぐにわかります。</span><span class="sxs-lookup"><span data-stu-id="b8924-274">This adjustment is difficult to see in the mining model content, but is apparent if you view the completed equation in the **Mining Legend** of the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="b8924-275">回帰式が 0 を表す位置から平均値を表す位置へとシフトしています。</span><span class="sxs-lookup"><span data-stu-id="b8924-275">The regression formula is shifted away from the 0 point to the point that represents the mean.</span></span> <span data-ttu-id="b8924-276">これにより、現在のデータがより直感的にわかりやすい形で表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8924-276">This presents a view that is more intuitive given the current data.</span></span>  
  
 <span data-ttu-id="b8924-277">したがって、平均年齢が 45 歳前後である場合、回帰式の切片 (VALUETYPE = 11) は平均収入を示します。</span><span class="sxs-lookup"><span data-stu-id="b8924-277">Therefore, assuming that the mean age is around 45, the intercept (VALUETYPE = 11) for the regression formula tells you the mean income.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8924-278">参照</span><span class="sxs-lookup"><span data-stu-id="b8924-278">See Also</span></span>  
 <span data-ttu-id="b8924-279">[マイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b8924-279">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b8924-280">[Microsoft 線形回帰アルゴリズム](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="b8924-280">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="b8924-281">[Microsoft 線形回帰アルゴリズムテクニカルリファレンス](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b8924-281">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="b8924-282">線形回帰モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="b8924-282">Linear Regression Model Query Examples</span></span>](linear-regression-model-query-examples.md)  
  
  
