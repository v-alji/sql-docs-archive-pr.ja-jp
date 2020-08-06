---
title: データマイニングプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ed1c47faafeb0c680e6afb6f8e509c426760da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743509"
---
# <a name="data-mining-properties"></a><span data-ttu-id="9136b-102">データ マイニング プロパティ</span><span class="sxs-lookup"><span data-stu-id="9136b-102">Data Mining Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="9136b-103">では、次の表に示すデータ マイニング サーバー プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9136b-103">supports the data mining server properties listed in the following tables.</span></span> <span data-ttu-id="9136b-104">その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9136b-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="9136b-105">**適用対象:** 多次元サーバーモードのみ</span><span class="sxs-lookup"><span data-stu-id="9136b-105">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="non-specific-category"></a><span data-ttu-id="9136b-106">不特定カテゴリ</span><span class="sxs-lookup"><span data-stu-id="9136b-106">Non-Specific Category</span></span>  
 `AllowSessionMiningModels`  
 <span data-ttu-id="9136b-107">セッション マイニング モデルを作成できるかどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-107">A Boolean property that indicates whether session mining models can be created.</span></span>  
  
 <span data-ttu-id="9136b-108">このプロパティの既定値は False であり、セッション マイニング モデルを作成できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="9136b-108">The default value for this property is false, which indicates that session mining models cannot be created.</span></span>  
  
 `AllowAdHocOpenRowsetQueries`  
 <span data-ttu-id="9136b-109">開かれた行セットのアドホック クエリを許可するかどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-109">A Boolean property that indicates whether adhoc open rowset queries are allowed.</span></span>  
  
 <span data-ttu-id="9136b-110">このプロパティの既定値は False であり、開かれた行セットのクエリがセッション中に許可されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="9136b-110">The default value for this property is false, which indicates that open rowset queries are not allowed during a session.</span></span>  
  
 `AllowedProvidersInOpenRowset`  
 <span data-ttu-id="9136b-111">開かれた行セットで許可されるプロバイダーを識別する文字列プロパティです。コンマまたはセミコロンで区切られたプロバイダー ProgID の一覧または [All] で構成されます。</span><span class="sxs-lookup"><span data-stu-id="9136b-111">A string property that identifies which providers are allowed in an open rowset, consisting of a comma/semi-colon separated list of provider ProgIDs, or else [All].</span></span>  
  
 `MaxConcurrentPredictionQueries`  
 <span data-ttu-id="9136b-112">同時予測クエリの最大数を定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-112">A signed 32-bit integer property that defines the maximum number of concurrent prediction queries.</span></span>  
  
## <a name="algorithms-category"></a><span data-ttu-id="9136b-113">アルゴリズム カテゴリ</span><span class="sxs-lookup"><span data-stu-id="9136b-113">Algorithms Category</span></span>  
 `Microsoft_Association_Rules\ Enabled`  
 <span data-ttu-id="9136b-114">Microsoft_Association_Rules アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-114">A Boolean property that indicates whether the Microsoft_Association_Rules algorithm is enabled.</span></span>  
  
 `Microsoft_Clustering\ Enabled`  
 <span data-ttu-id="9136b-115">Microsoft_Clustering algorithm アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-115">A Boolean property that indicates whether the Microsoft_Clustering algorithm is enabled.</span></span>  
  
 `Microsoft_Decision_Trees\ Enabled`  
 <span data-ttu-id="9136b-116">Microsoft_DecisionTrees アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-116">A Boolean property that indicates whether the Microsoft_DecisionTrees algorithm is enabled.</span></span>  
  
 `Microsoft_Naive_Bayes\ Enabled`  
 <span data-ttu-id="9136b-117">Microsoft_Naive_Bayes アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-117">A Boolean property that indicates whether the Microsoft_ Naive_Bayes algorithm is enabled.</span></span>  
  
 `Microsoft_Neural_Network\ Enabled`  
 <span data-ttu-id="9136b-118">Microsoft_Neural_Network アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-118">A Boolean property that indicates whether the Microsoft_Neural_Network algorithm is enabled.</span></span>  
  
 `Microsoft_Sequence_Clustering\ Enabled`  
 <span data-ttu-id="9136b-119">Microsoft_Sequence_Clustering アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-119">A Boolean property that indicates whether the Microsoft_Sequence_Clustering algorithm is enabled.</span></span>  
  
 `Microsoft_Time_Series\ Enabled`  
 <span data-ttu-id="9136b-120">Microsoft_Time_Series アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-120">A Boolean property that indicates whether the Microsoft_Time_Series algorithm is enabled.</span></span>  
  
 `Microsoft_Linear_Regression\ Enabled`  
 <span data-ttu-id="9136b-121">Microsoft_Linear_Regression アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-121">A Boolean property that indicates whether the Microsoft_Linear_Regression algorithm is enabled.</span></span>  
  
 `Microsoft_Logistic_Regression\ Enabled`  
 <span data-ttu-id="9136b-122">Microsoft_Logistic_Regression アルゴリズムが有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9136b-122">A Boolean property that indicates whether the Microsoft_Logistic_Regression algorithm is enabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9136b-123">サーバー上で使用可能なデータ マイニング サービスを定義するプロパティ以外に、特定のアルゴリズムの動作を定義するデータ マイニング プロパティが存在します。</span><span class="sxs-lookup"><span data-stu-id="9136b-123">In addition to properties that define the data mining services available on the server, there are data mining properties that define the behavior of specific algorithms.</span></span> <span data-ttu-id="9136b-124">データ マイニング モデルをサーバー レベルでなく、個々に作成する場合は、これらのプロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="9136b-124">You configure these properties when you create an individual data mining model, not at the server level.</span></span> <span data-ttu-id="9136b-125">詳しくは、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9136b-125">For more information, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9136b-126">参照</span><span class="sxs-lookup"><span data-stu-id="9136b-126">See Also</span></span>  
 <span data-ttu-id="9136b-127">[物理アーキテクチャ &#40;Analysis Services-データマイニング&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9136b-127">[Physical Architecture &#40;Analysis Services - Data Mining&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="9136b-128">[Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9136b-128">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="9136b-129">Analysis Services インスタンスのサーバー モードの決定</span><span class="sxs-lookup"><span data-stu-id="9136b-129">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
