---
title: アソシエーションモデルのマイニングモデルコンテンツ (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- mining model content, association models
- rules [Data Mining]
- associations [Analysis Services]
ms.assetid: d5849bcb-4b8f-4f71-9761-7dc5bb465224
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8904ce155526aee595db19094fd2bad48770e83e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639797"
---
# <a name="mining-model-content-for-association-models-analysis-services---data-mining"></a><span data-ttu-id="79c8f-102">アソシエーション モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="79c8f-102">Mining Model Content for Association Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="79c8f-103">このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムを使用するモデルに固有のマイニング モデル コンテンツについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span> <span data-ttu-id="79c8f-104">すべてのモデルの種類に適用されるマイニング モデル コンテンツに関連する一般用語と統計用語の説明については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79c8f-104">For an explanation of general and statistical terminology related to mining model content that applies to all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-an-association-model"></a><span data-ttu-id="79c8f-105">アソシエーション モデルの構造について</span><span class="sxs-lookup"><span data-stu-id="79c8f-105">Understanding the Structure of an Association Model</span></span>  
 <span data-ttu-id="79c8f-106">アソシエーション モデルの構造は単純です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-106">An association model has a simple structure.</span></span> <span data-ttu-id="79c8f-107">モデルとそのメタデータを表す 1 つの親ノードが各モデルにあり、各親ノードにはアイテムセットとルールのフラット リストがあります。</span><span class="sxs-lookup"><span data-stu-id="79c8f-107">Each model has a single parent node that represents the model and its metadata, and each parent node has a flat list of itemsets and rules.</span></span> <span data-ttu-id="79c8f-108">アイテムセットとルールはツリーを構成していません。次の図のように、最初がアイテムセット、次がルールという順に並んでいます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-108">The itemsets and rules are not organized in trees, they are ordered with itemsets first and rules next as shown in the following diagram.</span></span>  
  
 <span data-ttu-id="79c8f-109">![アソシエーション モデルのモデル コンテンツの構造](../media/modelcontentstructure-assoc.gif "アソシエーション モデルのモデル コンテンツの構造")</span><span class="sxs-lookup"><span data-stu-id="79c8f-109">![structure of model content for association models](../media/modelcontentstructure-assoc.gif "structure of model content for association models")</span></span>  
  
 <span data-ttu-id="79c8f-110">各アイテムセットはそれぞれ固有のノードに含まれています (NODE_TYPE = 7)。</span><span class="sxs-lookup"><span data-stu-id="79c8f-110">Each itemset is contained in its own node (NODE_TYPE = 7).</span></span> <span data-ttu-id="79c8f-111">" *ノード* " には、アイテムセットの定義、そのアイテムセットを含むケースの数、およびその他の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="79c8f-111">The *node* includes the definition of the itemset, the number of cases that contain this itemset, and other information.</span></span>  
  
 <span data-ttu-id="79c8f-112">ルールもそれぞれ固有のノードに含まれています (NODE_TYPE = 8)。</span><span class="sxs-lookup"><span data-stu-id="79c8f-112">Each rule is also contained in its own node (NODE_TYPE = 8).</span></span> <span data-ttu-id="79c8f-113">" *ルール* " は、アイテムがどのように関連付けられるかを示す一般的なパターンを記述します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-113">A *rule* describes a general pattern for how items are associated.</span></span> <span data-ttu-id="79c8f-114">ルールは IF-THEN ステートメントに似ています。</span><span class="sxs-lookup"><span data-stu-id="79c8f-114">A rule is like an IF-THEN statement.</span></span> <span data-ttu-id="79c8f-115">ルールの左辺は、既存の条件または条件のセットを表します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-115">The left-hand side of the rule shows an existing condition or set of conditions.</span></span> <span data-ttu-id="79c8f-116">ルールの右辺は、左辺の条件に通常関連付けられるデータセット内のアイテムを表します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-116">The right-hand side of the rule shows the item in your data set that is usually associated with the conditions on the left side.</span></span>  
  
 <span data-ttu-id="79c8f-117">**注** ルールやアイテムセットを抽出するには、クエリを使用して必要な種類のノードのみを取得します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-117">**Note** If you want to extract either the rules or the itemsets, you can use a query to return only the node types that you want.</span></span> <span data-ttu-id="79c8f-118">詳細については、「 [結合モデルのクエリ例](association-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79c8f-118">For more information, see [Association Model Query Examples](association-model-query-examples.md).</span></span>  
  
## <a name="model-content-for-an-association-model"></a><span data-ttu-id="79c8f-119">アソシエーション モデルのモデル コンテンツ</span><span class="sxs-lookup"><span data-stu-id="79c8f-119">Model Content for an Association Model</span></span>  
 <span data-ttu-id="79c8f-120">ここでは、マイニング モデル コンテンツの列のうち、アソシエーション モデルに関連する列についてのみ詳細と例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-120">This section provides detail and examples only for those columns in the mining model content that are relevant for association models.</span></span>  
  
 <span data-ttu-id="79c8f-121">スキーマ行セットの汎用の列 (MODEL_CATALOG や MODEL_NAME など) の詳細については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79c8f-121">For information about the general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="79c8f-122">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="79c8f-122">MODEL_CATALOG</span></span>  
 <span data-ttu-id="79c8f-123">モデルが格納されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="79c8f-123">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="79c8f-124">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="79c8f-124">MODEL_NAME</span></span>  
 <span data-ttu-id="79c8f-125">モデルの名前。</span><span class="sxs-lookup"><span data-stu-id="79c8f-125">Name of the model.</span></span>  
  
 <span data-ttu-id="79c8f-126">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="79c8f-126">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="79c8f-127">このノードに対応する属性の名前です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-127">The names of the attributes that correspond to this node.</span></span>  
  
 <span data-ttu-id="79c8f-128">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="79c8f-128">NODE_NAME</span></span>  
 <span data-ttu-id="79c8f-129">ノード名。</span><span class="sxs-lookup"><span data-stu-id="79c8f-129">The name of the node.</span></span> <span data-ttu-id="79c8f-130">アソシエーション モデルの場合、この列には NODE_UNIQUE_NAME と同じ値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-130">For an association model, this column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="79c8f-131">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="79c8f-131">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="79c8f-132">ノードの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="79c8f-132">The unique name of the node.</span></span>  
  
 <span data-ttu-id="79c8f-133">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="79c8f-133">NODE_TYPE</span></span>  
 <span data-ttu-id="79c8f-134">アソシエーション モデルでは次のノード型のみが出力されます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-134">A association model outputs only the following node types:</span></span>  
  
|<span data-ttu-id="79c8f-135">ノードの種類の ID</span><span class="sxs-lookup"><span data-stu-id="79c8f-135">Node Type ID</span></span>|<span data-ttu-id="79c8f-136">Type</span><span class="sxs-lookup"><span data-stu-id="79c8f-136">Type</span></span>|  
|------------------|----------|  
|<span data-ttu-id="79c8f-137">1 (モデル)</span><span class="sxs-lookup"><span data-stu-id="79c8f-137">1 (Model)</span></span>|<span data-ttu-id="79c8f-138">ルート ノード (親ノード)。</span><span class="sxs-lookup"><span data-stu-id="79c8f-138">Root or parent node.</span></span>|  
|<span data-ttu-id="79c8f-139">7 (アイテムセット)</span><span class="sxs-lookup"><span data-stu-id="79c8f-139">7 (Itemset)</span></span>|<span data-ttu-id="79c8f-140">アイテムセット (属性と値のペアのコレクション)。</span><span class="sxs-lookup"><span data-stu-id="79c8f-140">An itemset, or collection of attribute-value pairs.</span></span> <span data-ttu-id="79c8f-141">例 :</span><span class="sxs-lookup"><span data-stu-id="79c8f-141">Examples:</span></span><br /><br /> `Product 1 = Existing, Product 2 = Existing`<br /><br /> <span data-ttu-id="79c8f-142">or</span><span class="sxs-lookup"><span data-stu-id="79c8f-142">or</span></span><br /><br /> <span data-ttu-id="79c8f-143">`Gender = Male`.</span><span class="sxs-lookup"><span data-stu-id="79c8f-143">`Gender = Male`.</span></span>|  
|<span data-ttu-id="79c8f-144">8 (ルール)</span><span class="sxs-lookup"><span data-stu-id="79c8f-144">8 (Rule)</span></span>|<span data-ttu-id="79c8f-145">アイテムが互いにどのように関連付けられるかを定義するルール。</span><span class="sxs-lookup"><span data-stu-id="79c8f-145">A rule defining how items relate to each other.</span></span><br /><br /> <span data-ttu-id="79c8f-146">例:</span><span class="sxs-lookup"><span data-stu-id="79c8f-146">Example:</span></span><br /><br /> <span data-ttu-id="79c8f-147">`Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.</span><span class="sxs-lookup"><span data-stu-id="79c8f-147">`Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.</span></span>|  
  
 <span data-ttu-id="79c8f-148">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="79c8f-148">NODE_CAPTION</span></span>  
 <span data-ttu-id="79c8f-149">ノードに関連付けられたラベルまたはキャプション。</span><span class="sxs-lookup"><span data-stu-id="79c8f-149">A label or a caption associated with the node.</span></span>  
  
 <span data-ttu-id="79c8f-150">**アイテムセット ノード** アイテムのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="79c8f-150">**Itemset node** A comma-separated list of items.</span></span>  
  
 <span data-ttu-id="79c8f-151">**ルール ノード** ルールの左辺と右辺が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-151">**Rule node** Contains the left and right-hand sides of the rule.</span></span>  
  
 <span data-ttu-id="79c8f-152">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="79c8f-152">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="79c8f-153">現在のノードの子の数を示します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-153">Indicates the number of children of the current node.</span></span>  
  
 <span data-ttu-id="79c8f-154">**親ノード** アイテムセットおよびルールの合計数を示します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-154">**Parent node** Indicates the total number of itemsets plus rules.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79c8f-155">アイテムセットとルールの数の内訳は、モデルのルート ノードの NODE_DESCRIPTION で確認できます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-155">To get a breakdown of the count for itemsets and rules, see the NODE_DESCRIPTION for the root node of the model.</span></span>  
  
 <span data-ttu-id="79c8f-156">**アイテムセット ノードまたはルール ノード** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-156">**Itemset or rule node** Always 0.</span></span>  
  
 <span data-ttu-id="79c8f-157">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="79c8f-157">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="79c8f-158">ノードの親の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-158">The unique name of the node's parent.</span></span>  
  
 <span data-ttu-id="79c8f-159">**親ノード**常に NULL です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-159">**Parent node** Always NULL.</span></span>  
  
 <span data-ttu-id="79c8f-160">**アイテムセット ノードまたはルール ノード** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-160">**Itemset or rule node** Always 0.</span></span>  
  
 <span data-ttu-id="79c8f-161">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="79c8f-161">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="79c8f-162">ノードのコンテンツについてのわかりやすい説明。</span><span class="sxs-lookup"><span data-stu-id="79c8f-162">A user-friendly description of the contents of the node.</span></span>  
  
 <span data-ttu-id="79c8f-163">**親ノード** モデルに関する次の情報のコンマ区切りのリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-163">**Parent node** Includes a comma-separated list of the following information about the model:</span></span>  
  
|<span data-ttu-id="79c8f-164">Item</span><span class="sxs-lookup"><span data-stu-id="79c8f-164">Item</span></span>|<span data-ttu-id="79c8f-165">説明</span><span class="sxs-lookup"><span data-stu-id="79c8f-165">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="79c8f-166">ITEMSET_COUNT</span><span class="sxs-lookup"><span data-stu-id="79c8f-166">ITEMSET_COUNT</span></span>|<span data-ttu-id="79c8f-167">モデル内のすべてのアイテムセットの数。</span><span class="sxs-lookup"><span data-stu-id="79c8f-167">Count of all itemsets in model.</span></span>|  
|<span data-ttu-id="79c8f-168">RULE_COUNT</span><span class="sxs-lookup"><span data-stu-id="79c8f-168">RULE_COUNT</span></span>|<span data-ttu-id="79c8f-169">モデル内のすべてのルールの数。</span><span class="sxs-lookup"><span data-stu-id="79c8f-169">Count of all rules in model.</span></span>|  
|<span data-ttu-id="79c8f-170">MIN_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="79c8f-170">MIN_SUPPORT</span></span>|<span data-ttu-id="79c8f-171">任意の 1 つのアイテムセットに対して検出された最小のサポート。</span><span class="sxs-lookup"><span data-stu-id="79c8f-171">The minimum support found for any single itemset.</span></span><br /><br /> <span data-ttu-id="79c8f-172">**注** この値は、 *MINIMUM _SUPPORT* パラメーターに設定した値とは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="79c8f-172">**Note** This value might differ from the value that you set for the *MINIMUM _SUPPORT* parameter.</span></span>|  
|<span data-ttu-id="79c8f-173">MAX_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="79c8f-173">MAX_SUPPORT</span></span>|<span data-ttu-id="79c8f-174">任意の 1 つのアイテムセットに対して検出された最大のサポート。</span><span class="sxs-lookup"><span data-stu-id="79c8f-174">The maximum support found for any single itemset.</span></span><br /><br /> <span data-ttu-id="79c8f-175">**注** この値は、 *MAXIMUM_SUPPORT* パラメーターに設定した値とは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="79c8f-175">**Note** This value might differ from the value that you set for the *MAXIMUM_SUPPORT* parameter.</span></span>|  
|<span data-ttu-id="79c8f-176">MIN_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="79c8f-176">MIN_ITEMSET_SIZE</span></span>|<span data-ttu-id="79c8f-177">アイテムの数として表される最小のアイテムセットのサイズ。</span><span class="sxs-lookup"><span data-stu-id="79c8f-177">The size of the smallest itemset, represented as a count of items.</span></span><br /><br /> <span data-ttu-id="79c8f-178">値 0 は、`Missing` 状態が独立したアイテムとして扱われたことを示します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-178">A value of 0 indicates that the `Missing` state was treated as an independent item.</span></span><br /><br /> <span data-ttu-id="79c8f-179">\**注\*\*\*MINIMUM_ITEMSET_SIZE* パラメーターの既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-179">**Note** The default value of the *MINIMUM_ITEMSET_SIZE* parameter is 1.</span></span>|  
|<span data-ttu-id="79c8f-180">MAX_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="79c8f-180">MAX_ITEMSET_SIZE</span></span>|<span data-ttu-id="79c8f-181">検出された最大のアイテムセットのサイズを示します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-181">Indicates the size of the largest itemset that was found.</span></span><br /><br /> <span data-ttu-id="79c8f-182">**注** この値は、モデルの作成時に *MAX_ITEMSET_SIZE* パラメーターに設定した値によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-182">**Note** This value is constrained by the value that you set for the *MAX_ITEMSET_SIZE* parameter when you created the model.</span></span> <span data-ttu-id="79c8f-183">その値を超えることはありませんが、その値より小さくなることはあります。</span><span class="sxs-lookup"><span data-stu-id="79c8f-183">This value can never exceed that value; however, it can be less.</span></span> <span data-ttu-id="79c8f-184">既定値は、3 です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-184">The default value is 3.</span></span>|  
|<span data-ttu-id="79c8f-185">MIN_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="79c8f-185">MIN_PROBABILITY</span></span>|<span data-ttu-id="79c8f-186">モデル内の任意の 1 つのアイテムセットまたはルールに対して検出された最小の確率。</span><span class="sxs-lookup"><span data-stu-id="79c8f-186">The minimum probability detected for any single itemset or rule in the model.</span></span><br /><br /> <span data-ttu-id="79c8f-187">例: 0.400390625</span><span class="sxs-lookup"><span data-stu-id="79c8f-187">Example: 0.400390625</span></span><br /><br /> <span data-ttu-id="79c8f-188">**注** アイテムセットの場合、この値は常に、モデルの作成時に *MINIMUM_PROBABILITY* パラメーターに設定した値より大きくなります。</span><span class="sxs-lookup"><span data-stu-id="79c8f-188">**Note** For itemsets, this value is always greater than the value that you set for the *MINIMUM_PROBABILITY* parameter when you created the model.</span></span>|  
|<span data-ttu-id="79c8f-189">MAX_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="79c8f-189">MAX_PROBABILITY</span></span>|<span data-ttu-id="79c8f-190">モデル内の任意の 1 つのアイテムセットまたはルールに対して検出された最大の確率。</span><span class="sxs-lookup"><span data-stu-id="79c8f-190">The maximum probability detected for any single itemset or rule in the model.</span></span><br /><br /> <span data-ttu-id="79c8f-191">例: 1</span><span class="sxs-lookup"><span data-stu-id="79c8f-191">Example: 1</span></span><br /><br /> <span data-ttu-id="79c8f-192">**注** アイテムセットの最大確率を制限するパラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="79c8f-192">**Note** There is no parameter to constrain maximum probability of itemsets.</span></span> <span data-ttu-id="79c8f-193">頻度が高すぎるアイテムを除外するには、代わりに *MAXIMUM_SUPPORT* パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="79c8f-193">If you want to eliminate items that are too frequent, use the *MAXIMUM_SUPPORT* parameter instead.</span></span>|  
|<span data-ttu-id="79c8f-194">MIN_LIFT</span><span class="sxs-lookup"><span data-stu-id="79c8f-194">MIN_LIFT</span></span>|<span data-ttu-id="79c8f-195">モデルによって任意のアイテムセットに対して提供されているリフトの最小量。</span><span class="sxs-lookup"><span data-stu-id="79c8f-195">The minimum amount of lift that is provided by the model for any itemset.</span></span><br /><br /> <span data-ttu-id="79c8f-196">例 : 0.14309369632511</span><span class="sxs-lookup"><span data-stu-id="79c8f-196">Example: 0.14309369632511</span></span><br /><br /> <span data-ttu-id="79c8f-197">注: 最小リフトがわかると、特定のアイテムセットのリフトが大きいかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-197">Note: Knowing the minimum lift can help you determine whether the lift for any one itemset is significant.</span></span>|  
|<span data-ttu-id="79c8f-198">MAX_LIFT</span><span class="sxs-lookup"><span data-stu-id="79c8f-198">MAX_LIFT</span></span>|<span data-ttu-id="79c8f-199">モデルによって任意のアイテムセットに対して提供されているリフトの最大量。</span><span class="sxs-lookup"><span data-stu-id="79c8f-199">The maximum amount of lift that is provided by the model for any itemset.</span></span><br /><br /> <span data-ttu-id="79c8f-200">例 : 1.95758227647523 **注** 最大リフトがわかると、特定のアイテムセットのリフトが大きいかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-200">Example: 1.95758227647523 **Note** Knowing the maximum lift can help you determine whether the lift for any one itemset is significant.</span></span>|  
  
 <span data-ttu-id="79c8f-201">**アイテムセット ノード** アイテムセット ノードには、コンマ区切りのテキスト文字列として表示されるアイテムのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="79c8f-201">**Itemset node** Itemset nodes contain a list of the items, displayed as a comma-separated text string.</span></span>  
  
 <span data-ttu-id="79c8f-202">例:</span><span class="sxs-lookup"><span data-stu-id="79c8f-202">Example:</span></span>  
  
 `Touring Tire = Existing, Water Bottle = Existing`  
  
 <span data-ttu-id="79c8f-203">これは、Touring Tire と Water Bottle が一緒に購入されたことを表しています。</span><span class="sxs-lookup"><span data-stu-id="79c8f-203">This means touring tires and water bottles were purchased together.</span></span>  
  
 <span data-ttu-id="79c8f-204">**ルール ノード** ルール ノードには、矢印で区切られたルールの左辺と右辺が含まれています。</span><span class="sxs-lookup"><span data-stu-id="79c8f-204">**Rule node** Rule nodes contains a left-hand and right-hand side of the rule, separated by an arrow.</span></span>  
  
 <span data-ttu-id="79c8f-205">例: `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`</span><span class="sxs-lookup"><span data-stu-id="79c8f-205">Example: `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`</span></span>  
  
 <span data-ttu-id="79c8f-206">これは、Touring Tire と Water Bottle を購入した顧客は Cycling Cap も購入する傾向があることを表しています。</span><span class="sxs-lookup"><span data-stu-id="79c8f-206">This means that if someone bought a touring tire and a water bottle, they were also likely to buy a cycling cap.</span></span>  
  
 <span data-ttu-id="79c8f-207">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="79c8f-207">NODE_RULE</span></span>  
 <span data-ttu-id="79c8f-208">ノードに埋め込まれたルールまたはアイテムセットを記述する XML フラグメント。</span><span class="sxs-lookup"><span data-stu-id="79c8f-208">An XML fragment that describes the rule or itemset that is embedded in the node.</span></span>  
  
 <span data-ttu-id="79c8f-209">**親ノード** 空白。</span><span class="sxs-lookup"><span data-stu-id="79c8f-209">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="79c8f-210">**アイテムセット ノード** 空白。</span><span class="sxs-lookup"><span data-stu-id="79c8f-210">**Itemset node** Blank.</span></span>  
  
 <span data-ttu-id="79c8f-211">**ルール ノード** ルールに関する有用な追加情報 (サポート、信頼度、アイテムの数など) と、ルールの左辺を表すノードの ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-211">**Rule node** The XML fragment includes additional useful information about the rule, such as support, confidence, and the number of items, and the ID of the node that represents the left-hand side of the rule.</span></span>  
  
 <span data-ttu-id="79c8f-212">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="79c8f-212">MARGINAL_RULE</span></span>  
 <span data-ttu-id="79c8f-213">空白。</span><span class="sxs-lookup"><span data-stu-id="79c8f-213">Blank.</span></span>  
  
 <span data-ttu-id="79c8f-214">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="79c8f-214">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="79c8f-215">アイテムセットまたはルールに関連付けられている確率または信頼スコア。</span><span class="sxs-lookup"><span data-stu-id="79c8f-215">A probability or confidence score associated with the itemset or rule.</span></span>  
  
 <span data-ttu-id="79c8f-216">**親ノード** 常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-216">**Parent node** Always 0.</span></span>  
  
 <span data-ttu-id="79c8f-217">**アイテムセット ノード** アイテムセットの確率です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-217">**Itemset node** Probability of the itemset.</span></span>  
  
 <span data-ttu-id="79c8f-218">**ルール ノード** ルールの信頼度の値です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-218">**Rule node** Confidence value for the rule.</span></span>  
  
 <span data-ttu-id="79c8f-219">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="79c8f-219">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="79c8f-220">NODE_PROBABILITY と同じです。</span><span class="sxs-lookup"><span data-stu-id="79c8f-220">Same as NODE_PROBABILITY.</span></span>  
  
 <span data-ttu-id="79c8f-221">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="79c8f-221">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="79c8f-222">このテーブルに含まれる情報は、ノードがアイテムセットかルールかによって大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="79c8f-222">The table contains very different information, depending on whether the node is an itemset or a rule.</span></span>  
  
 <span data-ttu-id="79c8f-223">**親ノード** 空白。</span><span class="sxs-lookup"><span data-stu-id="79c8f-223">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="79c8f-224">**アイテムセット ノード** アイテムセット内の各アイテムと、その確率およびサポートの値の一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-224">**Itemset node** Lists each item in the itemset together with a probability and support value.</span></span> <span data-ttu-id="79c8f-225">たとえば、アイテムセットに 2 つの製品が含まれている場合は、各製品の名前と、その製品を含むケースの数の一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-225">For example, if the itemset contains two products, the name of each product is listed, together with the count of cases that include each product.</span></span>  
  
 <span data-ttu-id="79c8f-226">**ルール ノード** 2 つの行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-226">**Rule node** Contains two rows.</span></span> <span data-ttu-id="79c8f-227">1 つ目の行には、ルールの右辺の属性 (予測されたアイテム) が信頼スコアと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-227">The first row shows the attribute from the right-hand side of the rule, which is the predicted item, together with a confidence score.</span></span>  
  
 <span data-ttu-id="79c8f-228">2 つ目の行はアソシエーション モデルに固有の行で、ルールの右辺のアイテムセットへのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="79c8f-228">The second row is unique to association models; it contains a pointer to the itemset on the right-hand side of the rule.</span></span> <span data-ttu-id="79c8f-229">このポインターは、ATTRIBUTE_VALUE 列で、右辺のアイテムのみを含むアイテムセットの ID として表されます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-229">The pointer is represented in the ATTRIBUTE_VALUE column as the ID of the itemset that contains only the right-hand item.</span></span>  
  
 <span data-ttu-id="79c8f-230">たとえば、 `If {A,B} Then {C}`というルールの場合は、アイテム `{C}`の名前と、アイテム C のアイテムセットを含むノードの ID がテーブルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-230">For example, if the rule is `If {A,B} Then {C}`, the table contains the name of the item `{C}`, and the ID of the node that contains the itemset for item C.</span></span>  
  
 <span data-ttu-id="79c8f-231">アイテムセット ノードからは、右辺の製品を含むケースの合計数を特定できるため、このポインターは便利です。</span><span class="sxs-lookup"><span data-stu-id="79c8f-231">This pointer is useful because you can determine from the itemset node how many cases in all include the right-hand side product.</span></span> <span data-ttu-id="79c8f-232">ルール `If {A,B} Then {C}` が当てはまるケースは、 `{C}`のアイテムセットに含まれるケースのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="79c8f-232">The cases that are subject to the rule `If {A,B} Then {C}` are a subset of the cases listed in the itemset for `{C}`.</span></span>  
  
 <span data-ttu-id="79c8f-233">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="79c8f-233">NODE_SUPPORT</span></span>  
 <span data-ttu-id="79c8f-234">このノードをサポートするケースの数。</span><span class="sxs-lookup"><span data-stu-id="79c8f-234">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="79c8f-235">**親ノード** モデル内のケースの数。</span><span class="sxs-lookup"><span data-stu-id="79c8f-235">**Parent node** Number of cases in the model.</span></span>  
  
 <span data-ttu-id="79c8f-236">**アイテムセット ノード** アイテムセット内のすべてのアイテムを含むケースの数。</span><span class="sxs-lookup"><span data-stu-id="79c8f-236">**Itemset node** Number of cases that contains all items in the itemset.</span></span>  
  
 <span data-ttu-id="79c8f-237">**ルール ノード** ルールに含まれるすべてのアイテムを含むケースの数。</span><span class="sxs-lookup"><span data-stu-id="79c8f-237">**Rule node** The number of cases that contain all items included in the rule.</span></span>  
  
 <span data-ttu-id="79c8f-238">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="79c8f-238">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="79c8f-239">ノードがアイテムセットかルールかによって異なる情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-239">Contains different information depending on whether the node is an itemset or rule.</span></span>  
  
 <span data-ttu-id="79c8f-240">**親ノード** 空白。</span><span class="sxs-lookup"><span data-stu-id="79c8f-240">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="79c8f-241">**アイテムセット ノード** 空白。</span><span class="sxs-lookup"><span data-stu-id="79c8f-241">**Itemset node** Blank.</span></span>  
  
 <span data-ttu-id="79c8f-242">**ルール ノード** ルールの左辺のアイテムを含むアイテムセットの ID。</span><span class="sxs-lookup"><span data-stu-id="79c8f-242">**Rule node** The ID of the itemset that contains the items in the left-hand side of the rule.</span></span> <span data-ttu-id="79c8f-243">たとえば、 `If {A,B} Then {C}`というルールの場合は、 `{A,B}`のみを含むアイテムセットの ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79c8f-243">For example, if the rule is `If {A,B} Then {C}`, this column contains the ID of the itemset that contains only `{A,B}`.</span></span>  
  
 <span data-ttu-id="79c8f-244">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="79c8f-244">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="79c8f-245">**親ノード** 空白。</span><span class="sxs-lookup"><span data-stu-id="79c8f-245">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="79c8f-246">**アイテムセット ノード** アイテムセットの重要度スコア。</span><span class="sxs-lookup"><span data-stu-id="79c8f-246">**Itemset node** Importance score for the itemset.</span></span>  
  
 <span data-ttu-id="79c8f-247">**ルール ノード** ルールの重要度スコア。</span><span class="sxs-lookup"><span data-stu-id="79c8f-247">**Rule node** Importance score for the rule.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79c8f-248">重要度の計算方法はアイテムセットとルールで異なります。</span><span class="sxs-lookup"><span data-stu-id="79c8f-248">Importance is calculated differently for itemsets and rules.</span></span> <span data-ttu-id="79c8f-249">詳細については、「 [Microsoft アソシエーション アルゴリズム テクニカル リファレンス](microsoft-association-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79c8f-249">For more information, see [Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="79c8f-250">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="79c8f-250">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="79c8f-251">空白。</span><span class="sxs-lookup"><span data-stu-id="79c8f-251">Blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c8f-252">参照</span><span class="sxs-lookup"><span data-stu-id="79c8f-252">See Also</span></span>  
 <span data-ttu-id="79c8f-253">[マイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="79c8f-253">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="79c8f-254">[Microsoft アソシエーションアルゴリズム](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="79c8f-254">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="79c8f-255">結合モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="79c8f-255">Association Model Query Examples</span></span>](association-model-query-examples.md)  
  
  
