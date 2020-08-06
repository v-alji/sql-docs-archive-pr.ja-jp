---
title: Microsoft Naive Bayes アルゴリズムテクニカルリファレンス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_DEPENDENCY_PROBABILITY parameter
- MAXIMUM_INPUT_ATTRIBUTES parameter
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
ms.assetid: a4cd47fe-2127-4930-b18f-3edd17ee9a65
author: minewiskan
ms.author: owend
ms.openlocfilehash: b03f77f1e7299ef073f0e01775d879ee0ce57f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645260"
---
# <a name="microsoft-naive-bayes-algorithm-technical-reference"></a><span data-ttu-id="754ff-102">Microsoft Naive Bayes アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="754ff-102">Microsoft Naive Bayes Algorithm Technical Reference</span></span>
  <span data-ttu-id="754ff-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]Naive Bayes アルゴリズムは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 予測モデリングで使用するためにによって提供される分類アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="754ff-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm provided by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for use in predictive modeling.</span></span> <span data-ttu-id="754ff-104">このアルゴリズムでは、各列に依存関係がないと仮定して、入力列と予測可能列の条件付き確率が計算されます。</span><span class="sxs-lookup"><span data-stu-id="754ff-104">The algorithm calculates the conditional probability between input and predictable columns, and assumes that the columns are independent.</span></span> <span data-ttu-id="754ff-105">この非依存性の仮定が、Naive Bayes という名前の由来です。</span><span class="sxs-lookup"><span data-stu-id="754ff-105">This assumption of independence leads to the name Naive Bayes.</span></span>  
  
## <a name="implementation-of-the-microsoft-naive-bayes-algorithm"></a><span data-ttu-id="754ff-106">Microsoft Naive Bayes アルゴリズムの実装</span><span class="sxs-lookup"><span data-stu-id="754ff-106">Implementation of the Microsoft Naive Bayes Algorithm</span></span>  
 <span data-ttu-id="754ff-107">このアルゴリズムは、他の [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムよりも計算量が少ないので、入力列と予測可能列のリレーションシップを見つけるためのマイニング モデルを短時間で生成できます。</span><span class="sxs-lookup"><span data-stu-id="754ff-107">This algorithm is less computationally intense than other [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, and therefore is useful for quickly generating mining models to discover relationships between input columns and predictable columns.</span></span> <span data-ttu-id="754ff-108">このアルゴリズムは、入力属性値と出力属性値の各ペアを考慮します。</span><span class="sxs-lookup"><span data-stu-id="754ff-108">The algorithm considers each pair of input attribute values and output attribute values.</span></span>  
  
 <span data-ttu-id="754ff-109">Bayes の定理については、このドキュメントでは説明しません。詳細については、Microsoft Research の「 [ベイジアン ネットワークの学習: 知識と統計データの組み合わせ](https://go.microsoft.com/fwlink/?LinkId=207029)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="754ff-109">A description of the mathematical properties of Bayes Theorem is beyond the scope of this documentation; for more information, see the paper by Microsoft Research titled [Learning Bayesian Networks: The Combination of Knowledge and Statistical Data](https://go.microsoft.com/fwlink/?LinkId=207029).</span></span>  
  
 <span data-ttu-id="754ff-110">すべてのモデルにおいて可能性のある不足値を考慮するように確率を調整する方法については、「[Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md)」(不足値 &#40;Analysis Services - データ マイニング&#41;) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="754ff-110">For a description of how probabilities in all models are adjusted to account for potential missing values, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
### <a name="feature-selection"></a><span data-ttu-id="754ff-111">特徴選択</span><span class="sxs-lookup"><span data-stu-id="754ff-111">Feature Selection</span></span>  
 <span data-ttu-id="754ff-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、モデルを構築するときに考慮される値の数を制限するための自動的な機能選択が行われます。</span><span class="sxs-lookup"><span data-stu-id="754ff-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm performs automatic feature selection to limit the number of values that are considered when building the model.</span></span> <span data-ttu-id="754ff-113">詳細については、「[機能の選択 &#40;データ マイニング&#41;](feature-selection-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="754ff-113">For more information, see [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>  
  
|<span data-ttu-id="754ff-114">アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="754ff-114">Algorithm</span></span>|<span data-ttu-id="754ff-115">分析の方法</span><span class="sxs-lookup"><span data-stu-id="754ff-115">Method of analysis</span></span>|<span data-ttu-id="754ff-116">説明</span><span class="sxs-lookup"><span data-stu-id="754ff-116">Comments</span></span>|  
|---------------|------------------------|--------------|  
|<span data-ttu-id="754ff-117">Naive Bayes</span><span class="sxs-lookup"><span data-stu-id="754ff-117">Naive Bayes</span></span>|<span data-ttu-id="754ff-118">Shannon のエントロピー</span><span class="sxs-lookup"><span data-stu-id="754ff-118">Shannon's Entropy</span></span><br /><br /> <span data-ttu-id="754ff-119">K2 事前分布を指定したベイズ定理</span><span class="sxs-lookup"><span data-stu-id="754ff-119">Bayesian with K2 Prior</span></span><br /><br /> <span data-ttu-id="754ff-120">均一な事前分布を指定したベイズ ディリクレ等式 (既定値)</span><span class="sxs-lookup"><span data-stu-id="754ff-120">Bayesian Dirichlet with uniform prior (default)</span></span>|<span data-ttu-id="754ff-121">Naive Bayes で使用できる属性は、不連続属性と分離された属性だけです。したがって、興味深さのスコアは使用できません。</span><span class="sxs-lookup"><span data-stu-id="754ff-121">Naive Bayes only accepts discrete or discretized attributes; therefore, it cannot use the interestingness score.</span></span>|  
  
 <span data-ttu-id="754ff-122">このアルゴリズムは、処理時間が最短になり、最も重要な属性を効率よく選択できるように設計されています。ただし、次のようにパラメーターを設定することで、アルゴリズムが使用するデータを制御できます。</span><span class="sxs-lookup"><span data-stu-id="754ff-122">The algorithm is designed to minimize processing time and efficiently select the attributes that have the greatest importance; however, you can control the data that is used by the algorithm by setting parameters as follows:</span></span>  
  
-   <span data-ttu-id="754ff-123">入力として使用される値を制限するには、MAXIMUM_INPUT_ATTRIBUTES の値を小さくします。</span><span class="sxs-lookup"><span data-stu-id="754ff-123">To limit the values that are used as inputs, decrease the value of MAXIMUM_INPUT_ATTRIBUTES.</span></span>  
  
-   <span data-ttu-id="754ff-124">モデルで分析される属性の数を制限するには、MAXIMUM_OUTPUT_ATTRIBUTES の値を小さくします。</span><span class="sxs-lookup"><span data-stu-id="754ff-124">To limit the number of attributes analyzed by the model, decrease the value of MAXIMUM_OUTPUT_ATTRIBUTES.</span></span>  
  
-   <span data-ttu-id="754ff-125">任意の 1 つの属性について考慮できる値の数を制限するには、MINIMUM_STATES の値を小さくします。</span><span class="sxs-lookup"><span data-stu-id="754ff-125">To limit the number of values that can be considered for any one attribute, decrease the value of MINIMUM_STATES.</span></span>  
  
## <a name="customizing-the-naive-bayes-algorithm"></a><span data-ttu-id="754ff-126">Naive Bayes アルゴリズムのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="754ff-126">Customizing the Naive Bayes Algorithm</span></span>  
 <span data-ttu-id="754ff-127">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、結果として得られるマイニング モデルの動作、パフォーマンス、および精度に影響を与えるいくつかのパラメーターがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="754ff-127">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="754ff-128">モデル列にモデリング フラグを設定してデータの処理方法を制御することも、マイニング構造にフラグを設定して不足値または NULL 値の処理方法を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="754ff-128">You can also set modeling flags on the model columns to control how data is processed, or set flags on the mining structure to specify how missing values or nulls should be handled.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="754ff-129">アルゴリズム パラメーターの設定</span><span class="sxs-lookup"><span data-stu-id="754ff-129">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="754ff-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、結果として得られるマイニング モデルのパフォーマンスおよび精度に影響を与えるいくつかのパラメーターがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="754ff-130">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports several parameters that affect the performance and accuracy of the resulting mining model.</span></span> <span data-ttu-id="754ff-131">次の表では、各パラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="754ff-131">The following table describes each parameter.</span></span>  
  
 <span data-ttu-id="754ff-132">*MAXIMUM_INPUT_ATTRIBUTES*</span><span class="sxs-lookup"><span data-stu-id="754ff-132">*MAXIMUM_INPUT_ATTRIBUTES*</span></span>  
 <span data-ttu-id="754ff-133">選択した機能を呼び出す前にアルゴリズムが処理できる入力属性の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="754ff-133">Specifies the maximum number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="754ff-134">この値を 0 に設定すると、入力属性に対する機能の選択が無効になります。</span><span class="sxs-lookup"><span data-stu-id="754ff-134">Setting this value to 0 disables feature selection for input attributes.</span></span>  
  
 <span data-ttu-id="754ff-135">既定値は 255 です。</span><span class="sxs-lookup"><span data-stu-id="754ff-135">The default is 255.</span></span>  
  
 <span data-ttu-id="754ff-136">*MAXIMUM_OUTPUT_ATTRIBUTES*</span><span class="sxs-lookup"><span data-stu-id="754ff-136">*MAXIMUM_OUTPUT_ATTRIBUTES*</span></span>  
 <span data-ttu-id="754ff-137">選択した機能を呼び出す前にアルゴリズムが処理できる出力属性の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="754ff-137">Specifies the maximum number of output attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="754ff-138">この値を 0 に設定すると、出力属性に対する機能の選択が無効になります。</span><span class="sxs-lookup"><span data-stu-id="754ff-138">Setting this value to 0 disables feature selection for output attributes.</span></span>  
  
 <span data-ttu-id="754ff-139">既定値は 255 です。</span><span class="sxs-lookup"><span data-stu-id="754ff-139">The default is 255.</span></span>  
  
 <span data-ttu-id="754ff-140">*MINIMUM_DEPENDENCY_PROBABILITY*</span><span class="sxs-lookup"><span data-stu-id="754ff-140">*MINIMUM_DEPENDENCY_PROBABILITY*</span></span>  
 <span data-ttu-id="754ff-141">入力属性と出力属性間の依存関係の最小確率を指定します。</span><span class="sxs-lookup"><span data-stu-id="754ff-141">Specifies the minimum dependency probability between input and output attributes.</span></span> <span data-ttu-id="754ff-142">この値は、アルゴリズムによって生成されるコンテンツのサイズを制限するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="754ff-142">This value is used to limit the size of the content that is generated by the algorithm.</span></span> <span data-ttu-id="754ff-143">このプロパティは 0 ～ 1 の範囲で設定できます。</span><span class="sxs-lookup"><span data-stu-id="754ff-143">This property can be set from 0 to 1.</span></span> <span data-ttu-id="754ff-144">値を大きくすると、モデルのコンテンツの属性数が減ります。</span><span class="sxs-lookup"><span data-stu-id="754ff-144">Larger values reduce the number of attributes in the content of the model.</span></span>  
  
 <span data-ttu-id="754ff-145">既定値は 0.5 です。</span><span class="sxs-lookup"><span data-stu-id="754ff-145">The default is 0.5.</span></span>  
  
 <span data-ttu-id="754ff-146">*MAXIMUM_STATES*</span><span class="sxs-lookup"><span data-stu-id="754ff-146">*MAXIMUM_STATES*</span></span>  
 <span data-ttu-id="754ff-147">アルゴリズムによってサポートされる属性状態の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="754ff-147">Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="754ff-148">属性の状態の数が状態の最大数よりも大きい場合、アルゴリズムでは属性の最も一般的な状態が使用され、残りの状態は存在しないものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="754ff-148">If the number of states that an attribute has is greater than the maximum number of states, the algorithm uses the attribute's most popular states and treats the remaining states as missing.</span></span>  
  
 <span data-ttu-id="754ff-149">既定値は、100 です。</span><span class="sxs-lookup"><span data-stu-id="754ff-149">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="754ff-150">ModelingFlags</span><span class="sxs-lookup"><span data-stu-id="754ff-150">Modeling Flags</span></span>  
 <span data-ttu-id="754ff-151">[!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムでは、次のモデリング フラグがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="754ff-151">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm supports the following modeling flags.</span></span> <span data-ttu-id="754ff-152">モデリング フラグは、マイニング構造やマイニング モデルを作成するときに定義し、分析時に各列の値をどのように処理するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="754ff-152">When you create the mining structure or mining model, you define modeling flags to specify how values in each column are handled during analysis.</span></span> <span data-ttu-id="754ff-153">詳細については、「[モデリング フラグ &#40;データ マイニング&#41;](modeling-flags-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="754ff-153">For more information, see [Modeling Flags &#40;Data Mining&#41;](modeling-flags-data-mining.md).</span></span>  
  
|<span data-ttu-id="754ff-154">モデリング フラグ</span><span class="sxs-lookup"><span data-stu-id="754ff-154">Modeling Flag</span></span>|<span data-ttu-id="754ff-155">説明</span><span class="sxs-lookup"><span data-stu-id="754ff-155">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="754ff-156">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="754ff-156">MODEL_EXISTENCE_ONLY</span></span>|<span data-ttu-id="754ff-157">列が、Missing および Existing の 2 つの可能な状態を持つ列として扱われることを示します。</span><span class="sxs-lookup"><span data-stu-id="754ff-157">Means that the column will be treated as having two possible states: Missing and Existing.</span></span> <span data-ttu-id="754ff-158">NULL は Missing 値になります。</span><span class="sxs-lookup"><span data-stu-id="754ff-158">A null is a missing value.</span></span><br /><br /> <span data-ttu-id="754ff-159">マイニング モデル列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="754ff-159">Applies to mining model column.</span></span>|  
|<span data-ttu-id="754ff-160">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="754ff-160">NOT NULL</span></span>|<span data-ttu-id="754ff-161">列に NULL を含めることはできないことを示します。</span><span class="sxs-lookup"><span data-stu-id="754ff-161">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="754ff-162">モデルのトレーニング中に NULL が検出された場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="754ff-162">An error will result if Analysis Services encounters a null during model training.</span></span><br /><br /> <span data-ttu-id="754ff-163">マイニング構造列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="754ff-163">Applies to mining structure column.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="754ff-164">必要条件</span><span class="sxs-lookup"><span data-stu-id="754ff-164">Requirements</span></span>  
 <span data-ttu-id="754ff-165">Naive Bayes ツリー モデルには、キー列、少なくとも 1 つの予測可能属性、および少なくとも 1 つの入力属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="754ff-165">A Naive Bayes tree model must contain a key column, at least one predictable attribute, and at least one input attribute.</span></span> <span data-ttu-id="754ff-166">属性を連続にすることはできません。データに連続する数値データが含まれる場合は、無視または分離されます。</span><span class="sxs-lookup"><span data-stu-id="754ff-166">No attribute can be continuous; if your data contains continuous numeric data, it will be ignored or discretized.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="754ff-167">入力列と予測可能列</span><span class="sxs-lookup"><span data-stu-id="754ff-167">Input and Predictable Columns</span></span>  
 <span data-ttu-id="754ff-168">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、次の表に示す特定の入力列と予測可能列がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="754ff-168">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="754ff-169">マイニング モデルにおけるコンテンツの種類の意味については、「[コンテンツの種類 &#40;データ マイニング&#41;](content-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="754ff-169">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="754ff-170">列</span><span class="sxs-lookup"><span data-stu-id="754ff-170">Column</span></span>|<span data-ttu-id="754ff-171">コンテンツの種類</span><span class="sxs-lookup"><span data-stu-id="754ff-171">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="754ff-172">入力属性</span><span class="sxs-lookup"><span data-stu-id="754ff-172">Input attribute</span></span>|<span data-ttu-id="754ff-173">Cyclical、Discrete、Discretized、Key、Table、Ordered</span><span class="sxs-lookup"><span data-stu-id="754ff-173">Cyclical, Discrete, Discretized, Key, Table, and Ordered</span></span>|  
|<span data-ttu-id="754ff-174">予測可能な属性</span><span class="sxs-lookup"><span data-stu-id="754ff-174">Predictable attribute</span></span>|<span data-ttu-id="754ff-175">Cyclical、Discrete、Discretized、Table、Ordered</span><span class="sxs-lookup"><span data-stu-id="754ff-175">Cyclical, Discrete, Discretized, Table, and Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="754ff-176">コンテンツの種類 Cyclical および Ordered はサポートされますが、アルゴリズムはこれらを不連続の値として扱い、特別な処理は行いません。</span><span class="sxs-lookup"><span data-stu-id="754ff-176">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754ff-177">参照</span><span class="sxs-lookup"><span data-stu-id="754ff-177">See Also</span></span>  
 <span data-ttu-id="754ff-178">[Microsoft Naive Bayes アルゴリズム](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="754ff-178">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 <span data-ttu-id="754ff-179">[Naive Bayes モデルのクエリ例](naive-bayes-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="754ff-179">[Naive Bayes Model Query Examples](naive-bayes-model-query-examples.md) </span></span>  
 [<span data-ttu-id="754ff-180">Naive Bayes モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="754ff-180">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
