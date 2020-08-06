---
title: テストと検証 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- testing data mining models
- comparing mining models
- continuous attribute charts
- data mining [Analysis Services], models
- charts [Analysis Services]
- predictive modeling [Analysis Services]
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- confidence scores [data mining]
- displaying mining accuracy
- predictions [Analysis Services], comparing mining models
- scoring [data mining]
- lift charts [Analysis Services]
- classification matrix [Analysis Services]
- CRISP-DM
- accuracy testing [data mining]
ms.assetid: 197144f5-21ed-4009-b448-fe412fb3916c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c12f0215daed0c3308c63f36df0ba323152ec8d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631337"
---
# <a name="testing-and-validation-data-mining"></a><span data-ttu-id="d502a-102">テストおよび検証 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="d502a-102">Testing and Validation (Data Mining)</span></span>
  <span data-ttu-id="d502a-103">検証とは、実際のデータに対するマイニング モデルの性能を評価するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="d502a-103">Validation is the process of assessing how well your mining models perform against real data.</span></span> <span data-ttu-id="d502a-104">運用環境に配置する前に品質や特性を理解してマイニング モデルを検証しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="d502a-104">It is important that you validate your mining models by understanding their quality and characteristics before you deploy them into a production environment.</span></span>  
  
 <span data-ttu-id="d502a-105">このセクションでは、モデルの品質に関するいくつかの基本的な概念を紹介し、で提供されるモデル検証の方法について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d502a-105">This section introduces some basic concepts related to model quality, and describes the strategies for model validation that are provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d502a-106">大規模なデータ マイニング プロセス内でモデルの検証がどのように位置付けられているかの概要については、「 [データ マイニング ソリューション](data-mining-solutions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d502a-106">For an overview of how model validation fits into the larger data mining process, see [Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
## <a name="methods-for-testing-and-validation-of-data-mining-models"></a><span data-ttu-id="d502a-107">データ マイニング モデルのテストと検証の方法</span><span class="sxs-lookup"><span data-stu-id="d502a-107">Methods for Testing and Validation of Data Mining Models</span></span>  
 <span data-ttu-id="d502a-108">データ マイニング モデルの品質や特性を評価する方法は多数あります。</span><span class="sxs-lookup"><span data-stu-id="d502a-108">There are many approaches for assessing the quality and characteristics of a data mining model.</span></span>  
  
-   <span data-ttu-id="d502a-109">統計的妥当性の各種メジャーを使用して、データまたはモデルに問題があるかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="d502a-109">Use various measures of statistical validity to determine whether there are problems in the data or in the model.</span></span>  
  
-   <span data-ttu-id="d502a-110">データをトレーニング セットとテスト セットに分割して、予測の精度をテストします。</span><span class="sxs-lookup"><span data-stu-id="d502a-110">Separate the data into training and testing sets to test the accuracy of predictions.</span></span>  
  
-   <span data-ttu-id="d502a-111">発見されたパターンが目標とするビジネス シナリオにおいて有意であるかどうか、ビジネスの専門家にデータ マイニング モデルの結果を評価してもらいます。</span><span class="sxs-lookup"><span data-stu-id="d502a-111">Ask business experts to review the results of the data mining model to determine whether the discovered patterns have meaning in the targeted business scenario</span></span>  
  
 <span data-ttu-id="d502a-112">これらの方法はすべてデータ マイニング手法として有用であり、特定の問題に対応するためにモデルの作成、テスト、および調整を行うときに繰り返し使用されます。</span><span class="sxs-lookup"><span data-stu-id="d502a-112">All of these methods are useful in data mining methodology and are used iteratively as you create, test, and refine models to answer a specific problem.</span></span> <span data-ttu-id="d502a-113">モデルが満足できるものであること、または十分なデータがあることを単独で示すことができる包括的な規則はありません。</span><span class="sxs-lookup"><span data-stu-id="d502a-113">No single comprehensive rule can tell you when a model is good enough, or when you have enough data.</span></span>  
  
## <a name="definition-of-criteria-for-validating-data-mining-models"></a><span data-ttu-id="d502a-114">データ マイニング モデルを検証するための基準の定義</span><span class="sxs-lookup"><span data-stu-id="d502a-114">Definition of Criteria for Validating Data Mining Models</span></span>  
 <span data-ttu-id="d502a-115">通常、データ マイニングの評価基準は、精度、信頼性、および実用性に分類されます。</span><span class="sxs-lookup"><span data-stu-id="d502a-115">Measures of data mining generally fall into the categories of accuracy, reliability, and usefulness.</span></span>  
  
 <span data-ttu-id="d502a-116">*精度* は、モデルの結果が提供されたデータ内の属性と密接な関係があるかどうかを示すメジャーです。</span><span class="sxs-lookup"><span data-stu-id="d502a-116">*Accuracy* is a measure of how well the model correlates an outcome with the attributes in the data that has been provided.</span></span> <span data-ttu-id="d502a-117">精度のメジャーは各種ありますが、精度のメジャーはすべて、使用されるデータに依存します。</span><span class="sxs-lookup"><span data-stu-id="d502a-117">There are various measures of accuracy, but all measures of accuracy are dependent on the data that is used.</span></span> <span data-ttu-id="d502a-118">実際には、値が不足していたり概算値であったり、複数のプロセスによってデータが変更されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d502a-118">In reality, values might be missing or approximate, or the data might have been changed by multiple processes.</span></span> <span data-ttu-id="d502a-119">特に調査と開発のフェーズでは、データの特性がきわめて均一である場合は特に、データ内に一定量のエラーを認める必要があります。</span><span class="sxs-lookup"><span data-stu-id="d502a-119">Particularly in the phase of exploration and development, you might decide to accept a certain amount of error in the data, especially if the data is fairly uniform in its characteristics.</span></span> <span data-ttu-id="d502a-120">たとえば、過去の売上に基づいて特定の店舗の売上を予測するモデルは、その店舗で継続的に誤った会計手続きが行われていたとしても、密接な相関関係を持ち非常に正確なモデルになります。</span><span class="sxs-lookup"><span data-stu-id="d502a-120">For example, a model that predicts sales for a particular store based on past sales can be strongly correlated and very accurate, even if that store consistently used the wrong accounting method.</span></span> <span data-ttu-id="d502a-121">したがって、精度の測定は、信頼性の評価とのバランスを取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="d502a-121">Therefore, measurements of accuracy must be balanced by assessments of reliability.</span></span>  
  
 <span data-ttu-id="d502a-122">*信頼性* は、異なるデータセットに対するデータ マイニング モデルの性能を示します。</span><span class="sxs-lookup"><span data-stu-id="d502a-122">*Reliability* assesses the way that a data mining model performs on different data sets.</span></span> <span data-ttu-id="d502a-123">提供されるテスト データに関係なく同じ種類の予測が生成される場合や同種の一般的パターンが発見される場合、データ マイニング モデルは信頼性が高いと見なされます。</span><span class="sxs-lookup"><span data-stu-id="d502a-123">A data mining model is reliable if it generates the same type of predictions or finds the same general kinds of patterns regardless of the test data that is supplied.</span></span> <span data-ttu-id="d502a-124">たとえば、誤った会計手続きが行われていた店舗に対して生成されたモデルは、他の店舗用にはうまく一般化できず、信頼性がないことになります。</span><span class="sxs-lookup"><span data-stu-id="d502a-124">For example, the model that you generate for the store that used the wrong accounting method would not generalize well to other stores, and therefore would not be reliable.</span></span>  
  
 <span data-ttu-id="d502a-125">*実用性* には、モデルによって有用な情報が提供されるかどうかを示す各種のメトリックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d502a-125">*Usefulness* includes various metrics that tell you whether the model provides useful information.</span></span> <span data-ttu-id="d502a-126">たとえば、店舗の場所と売上の相関関係を求めるデータ マイニング モデルの場合、高い精度と信頼性を持つと評価される一方で、同じ場所にさらに店舗を追加してその結果を一般化することができないという理由で実用的でない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d502a-126">For example, a data mining model that correlates store location with sales might be both accurate and reliable, but might not be useful, because you cannot generalize that result by adding more stores at the same location.</span></span> <span data-ttu-id="d502a-127">さらに、このデータ マイニング モデルでは、特定の場所でなぜ売上が多いのかという基本的な業務上の疑問点に対する回答が示されません。</span><span class="sxs-lookup"><span data-stu-id="d502a-127">Moreover, it does not answer the fundamental business question of why certain locations have more sales.</span></span> <span data-ttu-id="d502a-128">また、モデルはデータ内の相互相関に基づいているので、モデルが成果を挙げているように見えても実際は無意味である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d502a-128">You might also find that a model that appears successful in fact is meaningless, because it is based on cross-correlations in the data.</span></span>  
  
## <a name="tools-for-testing-and-validation-of-mining-models"></a><span data-ttu-id="d502a-129">マイニング モデルのテストと検証のツール</span><span class="sxs-lookup"><span data-stu-id="d502a-129">Tools for Testing and Validation of Mining Models</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d502a-130">では、データ マイニング ソリューションを検証するための複数の方法をサポートすると共に、データ マイニング テスト手法のすべてのフェーズをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d502a-130">supports multiple approaches to validation of data mining solutions, supporting all phases of the data mining test methodology.</span></span>  
  
-   <span data-ttu-id="d502a-131">テスト セットとトレーニング セットへのデータのパーティション分割。</span><span class="sxs-lookup"><span data-stu-id="d502a-131">Partitioning data into testing and training sets.</span></span>  
  
-   <span data-ttu-id="d502a-132">同じソース データの異なる組み合わせでトレーニングおよびテストを行うためのモデルのフィルター処理。</span><span class="sxs-lookup"><span data-stu-id="d502a-132">Filtering models to train and test different combinations of the same source data.</span></span>  
  
-   <span data-ttu-id="d502a-133">*リフト* と *ゲイン*の測定。</span><span class="sxs-lookup"><span data-stu-id="d502a-133">Measuring *lift* and *gain*.</span></span> <span data-ttu-id="d502a-134">*リフト チャート* は、ランダムな推測と比較したときにデータ マイニング モデルを使用したことによる改善を視覚化するための方法です。</span><span class="sxs-lookup"><span data-stu-id="d502a-134">A *lift chart* is a method of visualizing the improvement that you get from using a data mining model, when you compare it to random guessing.</span></span>  
  
-   <span data-ttu-id="d502a-135">データセットの *相互検証* の実行</span><span class="sxs-lookup"><span data-stu-id="d502a-135">Performing *cross-validation* of data sets</span></span>  
  
-   <span data-ttu-id="d502a-136">*分類マトリックス*の生成。</span><span class="sxs-lookup"><span data-stu-id="d502a-136">Generating *classification matrices*.</span></span> <span data-ttu-id="d502a-137">これらのチャートでは、良い推量と悪い推量をテーブルに並べ替えて、モデルによるターゲット値の予測精度を簡単に評価できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d502a-137">These charts sort good and bad guesses into a table so that you can quickly and easily gauge how accurately the model predicts the target value.</span></span>  
  
-   <span data-ttu-id="d502a-138">回帰式の適合性を評価するための *散布図* の作成。</span><span class="sxs-lookup"><span data-stu-id="d502a-138">Creating *scatter plots* to assess the fit of a regression formula.</span></span>  
  
-   <span data-ttu-id="d502a-139">推奨設定の価値を評価するために財務的利益またはコストをマイニング モデルの使用に関連付ける *利益チャート* の作成。</span><span class="sxs-lookup"><span data-stu-id="d502a-139">Creating *profit charts* that associate financial gain or costs with the use of a mining model, so that you can assess the value of the recommendations.</span></span>  
  
 <span data-ttu-id="d502a-140">これらの基準は、データ マイニング モデルが業務上の質問に答えるものであるかを判断するためのものではなく、予測分析でデータの信頼性を評価するため、および開発プロセスで特定の繰り返し処理を使用するかどうかの決定を導きだすために使用できる客観的な測定値を提供するものです。</span><span class="sxs-lookup"><span data-stu-id="d502a-140">These metrics do not aim to answer the question of whether the data mining model answers your business question; rather, these metrics provide objective measurements that you can use to assess the reliability of your data for predictive analytics, and to guide your decision of whether to use a particular iterate on the development process.</span></span>  
  
 <span data-ttu-id="d502a-141">このセクションのトピックでは、各方法の概要を説明すると共に、SQL Server のデータ マイニングを使用して作成したモデルの精度を測定するプロセスの手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="d502a-141">The topics in this section provide an overview of each method and walk you through the process of measuring the accuracy of models that you build using SQL Server Data Mining.</span></span>  
  
### <a name="related-topics"></a><span data-ttu-id="d502a-142">関連トピック</span><span class="sxs-lookup"><span data-stu-id="d502a-142">Related Topics</span></span>  
  
|<span data-ttu-id="d502a-143">トピック</span><span class="sxs-lookup"><span data-stu-id="d502a-143">Topics</span></span>|<span data-ttu-id="d502a-144">リンク</span><span class="sxs-lookup"><span data-stu-id="d502a-144">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="d502a-145">ウィザードまたは DMX コマンドを使用してテスト用データ セットを設定する方法を学ぶ</span><span class="sxs-lookup"><span data-stu-id="d502a-145">Learn how to set up a testing data set using a wizard or DMX commands</span></span>|[<span data-ttu-id="d502a-146">トレーニング データ セットとテスト データ セット</span><span class="sxs-lookup"><span data-stu-id="d502a-146">Training and Testing Data Sets</span></span>](training-and-testing-data-sets.md)|  
|<span data-ttu-id="d502a-147">マイニング構造内のデータの分布と代表性をテストする方法を学ぶ</span><span class="sxs-lookup"><span data-stu-id="d502a-147">Learn how to test the distribution and representativeness of the data in a mining structure</span></span>|[<span data-ttu-id="d502a-148">相互検証 &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="d502a-148">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="d502a-149">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]で用意されている精度チャートの種類について学ぶ</span><span class="sxs-lookup"><span data-stu-id="d502a-149">Learn about the accuracy chart types provided in [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span>|[<span data-ttu-id="d502a-150">リフト チャート &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="d502a-150">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="d502a-151">利益チャート (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="d502a-151">Profit Chart &#40;Analysis Services - Data Mining&#41;</span></span>](profit-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="d502a-152">散布図 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="d502a-152">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="d502a-153">真陽性、偽陽性、真陰性、および偽陰性の実際の数値を評価する分類マトリックス (混同マトリックスと呼ばれることもある) の作成方法について学びます。</span><span class="sxs-lookup"><span data-stu-id="d502a-153">Learn how to create a classification matrix, sometimes called a confusion matrix, for assessing the number of true and false positives and negatives.</span></span>|[<span data-ttu-id="d502a-154">分類マトリックス &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="d502a-154">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="d502a-155">参照</span><span class="sxs-lookup"><span data-stu-id="d502a-155">See Also</span></span>  
 <span data-ttu-id="d502a-156">[データマイニングツール](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d502a-156">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="d502a-157">[データマイニングソリューション](data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="d502a-157">[Data Mining Solutions](data-mining-solutions.md) </span></span>  
 [<span data-ttu-id="d502a-158">テストおよび検証タスク、および操作方法 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="d502a-158">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
