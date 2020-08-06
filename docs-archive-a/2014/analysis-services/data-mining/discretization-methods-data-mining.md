---
title: 分離メソッド (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- discretization [Analysis Services]
- columns [data mining], discretization
- THRESHOLDS method
- CLUSTERS method
- DiscretizationBuckets property
- AUTOMATIC method
- EQUAL_AREAS method
- coding [Data Mining]
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
author: minewiskan
ms.author: owend
ms.openlocfilehash: feca59697c1c78a08e629b62856053f2d2ce6d6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644226"
---
# <a name="discretization-methods-data-mining"></a><span data-ttu-id="9858d-102">分離メソッド (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9858d-102">Discretization Methods (Data Mining)</span></span>
  <span data-ttu-id="9858d-103">でデータマイニングモデルを作成するために使用される一部のアルゴリズムでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 正しく機能するために特定のコンテンツの種類が必要です。</span><span class="sxs-lookup"><span data-stu-id="9858d-103">Some algorithms that are used to create data mining models in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] require specific content types in order to function correctly.</span></span> <span data-ttu-id="9858d-104">たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、連続列を入力として使用したり、連続する値を予測したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9858d-104">For example, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm cannot use continuous columns as input and cannot predict continuous values.</span></span> <span data-ttu-id="9858d-105">また、一部の列に含まれている値が多すぎるため、データ マイニング モデルの作成元となるデータ内の対象パターンをアルゴリズムで容易に識別できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9858d-105">Additionally, some columns may contain so many values that the algorithm cannot easily identify interesting patterns in the data from which to create a model.</span></span>  
  
 <span data-ttu-id="9858d-106">このような場合、アルゴリズムを使用してマイニング モデルを生成できるように、列内のデータを分離できます。</span><span class="sxs-lookup"><span data-stu-id="9858d-106">In these cases, you can discretize the data in the columns to enable the use of the algorithms to produce a mining model.</span></span> <span data-ttu-id="9858d-107">*分離* とは、値をバケットに分割して、限定された数の可能な状態を生成するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="9858d-107">*Discretization* is the process of putting values into buckets so that there are a limited number of possible states.</span></span> <span data-ttu-id="9858d-108">バケット自体は、順序付きの不連続の値として処理されます。</span><span class="sxs-lookup"><span data-stu-id="9858d-108">The buckets themselves are treated as ordered and discrete values.</span></span> <span data-ttu-id="9858d-109">数値と文字列の両方の列を分離できます。</span><span class="sxs-lookup"><span data-stu-id="9858d-109">You can discretize both numeric and string columns.</span></span>  
  
 <span data-ttu-id="9858d-110">データを分離するためのいくつかのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="9858d-110">There are several methods that you can use to discretize data.</span></span> <span data-ttu-id="9858d-111">データ マイニング ソリューションでリレーショナル データを使用する場合は、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> property プロパティの値を設定して、データのグループ化に使用するバケットの数を制御できます。</span><span class="sxs-lookup"><span data-stu-id="9858d-111">If your data mining solution uses relational data, you can control the number of buckets to use for grouping data by setting the value of the <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> property.</span></span> <span data-ttu-id="9858d-112">既定のバケット数は 5 です。</span><span class="sxs-lookup"><span data-stu-id="9858d-112">The default number of buckets is 5.</span></span>  
  
 <span data-ttu-id="9858d-113">データ マイニング ソリューションでオンライン分析処理 (OLAP) キューブのデータを使用する場合、データ マイニング アルゴリズムでは生成するバケットの数が次の式を使用して自動的に計算されます。ここで、n は列のデータの個別の値の数です。</span><span class="sxs-lookup"><span data-stu-id="9858d-113">If your data mining solution uses data from an Online Analytical Processing (OLAP) cube, the data mining algorithm automatically computes the number of buckets to generate by using the following equation, where n is the number of distinct values of data in the column:</span></span>  
  
 `Number of Buckets = sqrt(n)`  
  
 <span data-ttu-id="9858d-114">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でバケットの数を計算しない場合は、<xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> プロパティを使用して、バケットの数を手動で指定できます。</span><span class="sxs-lookup"><span data-stu-id="9858d-114">If you do not want [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to calculate the number of buckets, you can use the <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> property to manually specify the number of buckets.</span></span>  
  
 <span data-ttu-id="9858d-115">次の表では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でデータを分離するときに使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9858d-115">The following table describes the methods that you can use to discretize data in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="9858d-116">分離メソッド</span><span class="sxs-lookup"><span data-stu-id="9858d-116">Discretization method</span></span>|<span data-ttu-id="9858d-117">説明</span><span class="sxs-lookup"><span data-stu-id="9858d-117">Description</span></span>|  
|---------------------------|-----------------|  
|`AUTOMATIC`|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="9858d-118">によって、使用する分離メソッドが決定されます。</span><span class="sxs-lookup"><span data-stu-id="9858d-118">determines which discretization method to use.</span></span>|  
|`CLUSTERS`|<span data-ttu-id="9858d-119">このアルゴリズムは、トレーニング データをサンプリングして多数のランダム ポイントに初期化し、Expectation Maximization (EM) クラスター化アルゴリズムを使用して Microsoft クラスタリング アルゴリズムを何度か繰り返し実行することによって、データをグループに分割します。</span><span class="sxs-lookup"><span data-stu-id="9858d-119">The algorithm divides the data into groups by sampling the training data, initializing to a number of random points, and then running several iterations of the Microsoft Clustering algorithm using the Expectation Maximization (EM) clustering method.</span></span> <span data-ttu-id="9858d-120">`CLUSTERS` メソッドは、どのような分布曲線にも使用できるので便利です。</span><span class="sxs-lookup"><span data-stu-id="9858d-120">The `CLUSTERS` method is useful because it works on any distribution curve.</span></span> <span data-ttu-id="9858d-121">ただし、その他の分離メソッドよりも処理時間は長くなります。</span><span class="sxs-lookup"><span data-stu-id="9858d-121">However, it requires more processing time than the other discretization methods.</span></span><br /><br /> <span data-ttu-id="9858d-122">このメソッドは数値列でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9858d-122">This method can only be used with numeric columns.</span></span>|  
|`EQUAL_AREAS`|<span data-ttu-id="9858d-123">このアルゴリズムは、同数の値が含まれているグループにデータを分割します。</span><span class="sxs-lookup"><span data-stu-id="9858d-123">The algorithm divides the data into groups that contain an equal number of values.</span></span> <span data-ttu-id="9858d-124">このメソッドは正規分布曲線に最適ですが、連続データの小さなグループに多数の値が含まれている分布の場合は適切に機能しません。</span><span class="sxs-lookup"><span data-stu-id="9858d-124">This method is best used for normal distribution curves, but does not work well if the distribution includes a large number of values that occur in a narrow group in the continuous data.</span></span> <span data-ttu-id="9858d-125">たとえば、品目の半数のコストが 0 である場合、データの半数は曲線の 1 点の下に位置します。</span><span class="sxs-lookup"><span data-stu-id="9858d-125">For example, if one-half of the items have a cost of 0, one-half the data will occur under a single point in the curve.</span></span> <span data-ttu-id="9858d-126">このような分布の場合、このメソッドはデータを分割するときに、複数の領域に均等に分離しようとします。</span><span class="sxs-lookup"><span data-stu-id="9858d-126">In such a distribution, this method breaks the data up in an effort to establish equal discretization into multiple areas.</span></span> <span data-ttu-id="9858d-127">これにより、データが不適切に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9858d-127">This produces an inaccurate representation of the data.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9858d-128">解説</span><span class="sxs-lookup"><span data-stu-id="9858d-128">Remarks</span></span>  
  
-   <span data-ttu-id="9858d-129">`EQUAL_AREAS` メソッドを使用すると、文字列を分離できます。</span><span class="sxs-lookup"><span data-stu-id="9858d-129">You can use the `EQUAL_AREAS` method to discretize strings.</span></span>  
  
-   <span data-ttu-id="9858d-130">`CLUSTERS` メソッドでは、ランダム サンプルとして 1,000 個のレコードを使用してデータの分離が行われます。</span><span class="sxs-lookup"><span data-stu-id="9858d-130">The `CLUSTERS` method uses a random sample of 1000 records to discretize data.</span></span> <span data-ttu-id="9858d-131">アルゴリズムでデータをサンプリングしない場合は、`EQUAL_AREAS` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9858d-131">Use the `EQUAL_AREAS` method if you do not want the algorithm to sample data.</span></span>  
  
-   <span data-ttu-id="9858d-132">ニューラル ネットワーク マイニング モデルのチュートリアルには、分離をカスタマイズする例が示されています。</span><span class="sxs-lookup"><span data-stu-id="9858d-132">The neural network mining model tutorial provides an example of how discretization can be customized.</span></span> <span data-ttu-id="9858d-133">詳細については、「[レッスン 5: ニューラルネットワークとロジスティック回帰モデルの構築 &#40;中級者向けデータマイニングチュートリアル&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9858d-133">For more information, see [Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9858d-134">参照</span><span class="sxs-lookup"><span data-stu-id="9858d-134">See Also</span></span>  
 <span data-ttu-id="9858d-135">[コンテンツの種類 &#40;データマイニング&#41;](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9858d-135">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="9858d-136">[DMX&#41;&#40;コンテンツの種類](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="9858d-136">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="9858d-137">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9858d-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="9858d-138">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9858d-138">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="9858d-139">[データマイニング&#41;&#40;データ型](data-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9858d-139">[Data Types &#40;Data Mining&#41;](data-types-data-mining.md) </span></span>  
 <span data-ttu-id="9858d-140">[マイニング構造列](mining-structure-columns.md) </span><span class="sxs-lookup"><span data-stu-id="9858d-140">[Mining Structure Columns](mining-structure-columns.md) </span></span>  
 [<span data-ttu-id="9858d-141">列の分布 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="9858d-141">Column Distributions &#40;Data Mining&#41;</span></span>](column-distributions-data-mining.md)  
  
  
