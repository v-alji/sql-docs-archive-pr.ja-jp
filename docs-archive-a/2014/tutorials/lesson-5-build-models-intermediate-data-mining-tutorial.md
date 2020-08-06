---
title: 'レッスン 5: ニューラルネットワークとロジスティック回帰モデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- data mining [Analysis Services], tutorials
- neural networks
- tutorials [Data Mining]
- neural network model [Analysis Services]
ms.assetid: 42c3701a-1fd2-44ff-b7de-377345bbbd6b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a8c9fcf0380582f15fa2bf30d6fdeb97bb2ab1fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639828"
---
# <a name="lesson-5-building-neural-network-and-logistic-regression-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="bd6ca-102">レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="bd6ca-102">Lesson 5: Building Neural Network and Logistic Regression Models (Intermediate Data Mining Tutorial)</span></span>
  
  
 <span data-ttu-id="bd6ca-103">[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] のオペレーション部門では、コール センターの顧客満足度を向上させるためのプロジェクトが進行中です。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-103">The Operations department of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] is engaged in a project to improve customer satisfaction with their call center.</span></span> <span data-ttu-id="bd6ca-104">この部門では、コール センターを管理すると共にコール センターの有効性に関する基準をレポートするためにベンダーを雇っています。ここであなたは、ベンダーから提供されたいくつかの予備データの分析を求められました。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-104">They hired a vendor to manage the call center and to report metrics on call center effectiveness, and have asked you to analyze some preliminary data provided by the vendor.</span></span> <span data-ttu-id="bd6ca-105">彼らは、興味深い発見があるかどうかを知りたがっています。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-105">They want to know if there are any interesting findings.</span></span> <span data-ttu-id="bd6ca-106">彼らは特に、人員の配置上の問題を示唆するデータや、顧客満足の改善に役立つと思われるデータに関する情報を求めています。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-106">In particular, they would like to know if the data suggests any staffing problems with staffing or ways to improve customer satisfaction.</span></span>  
  
 <span data-ttu-id="bd6ca-107">データセットは小さなもので、コール センターでのオペレーションの 30 日分しかカバーしていません。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-107">The data set is small and covers only a 30-day period in the operation of the call center.</span></span> <span data-ttu-id="bd6ca-108">このデータは、シフトごとの未経験のオペレーターと経験を積んだオペレーターの人数、問い合わせの電話の件数、注文の件数と解決する必要がある案件の件数、および顧客からの電話に対する平均応答時間を追跡しています。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-108">The data tracks the number of new and experienced operators in each shift, the number of incoming calls, the number of orders as well as issues that must be resolved, and the average time a customer waits for someone to respond to a call.</span></span> <span data-ttu-id="bd6ca-109">さらに、顧客の不満を表す 1 つの指標である *電話放棄呼率*に基づくサービス品質基準も含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-109">The data also includes a service quality metric based on *abandon rate*, which is an indicator of customer frustration.</span></span>  
  
 <span data-ttu-id="bd6ca-110">データが何を示すかについての事前予測情報がないので、ご自身はニューラル ネットワーク モデルを使用して有効な相関関係を探すことに決めました。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-110">Because you do not have any prior expectations about what the data will show, you decide to use a neural network model to explore possible correlations.</span></span> <span data-ttu-id="bd6ca-111">ニューラル ネットワーク モデルは、多くの入力と出力の間の複雑な関係を分析できるため、データ探索によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-111">Neural network models are often used for exploration because they can analyze complex relationships between many inputs and outputs.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="bd6ca-112">学習する内容</span><span class="sxs-lookup"><span data-stu-id="bd6ca-112">What You Will Learn</span></span>  
 <span data-ttu-id="bd6ca-113">このレッスンでは、データに含まれる傾向を理解するために、ニューラル ネットワーク アルゴリズムを使用して、ご自身とオペレーション チームが使用できるモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-113">In this lesson, you will use the neural network algorithm to build a model that you and the Operations team can use to understand the trends in the data.</span></span> <span data-ttu-id="bd6ca-114">このレッスンの一部として、次の質問に回答してください。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-114">As part of this lesson, you will try to answer the following questions:</span></span>  
  
-   <span data-ttu-id="bd6ca-115">顧客満足に影響する要因には何がありますか。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-115">What factors affect customer satisfaction?</span></span>  
  
-   <span data-ttu-id="bd6ca-116">コール センターのサービス品質を向上させるにはどのような方法がありますか。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-116">What can the call center do to improve service quality?</span></span>  
  
 <span data-ttu-id="bd6ca-117">結果に基づいて、予測に使用できるロジスティック回帰モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-117">Based on the results, you will then build a logistic regression model that you can use for predictions.</span></span> <span data-ttu-id="bd6ca-118">予測は、コール センターのオペレーションの計画に役立てるためにオペレーション チームによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-118">The predictions will be used by the Operations team as an aid in planning call center operation.</span></span>  
  
 <span data-ttu-id="bd6ca-119">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bd6ca-119">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="bd6ca-120">呼び出しセンターデータのデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-120">Adding a Data Source View for Call Center Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="bd6ca-121">「中級者向けデータマイニングチュートリアル &#40;ニューラルネットワーク構造とモデルの作成」チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-121">Creating a Neural Network Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="bd6ca-122">「&#40;中級者向けデータマイニングチュートリアル」のコールセンターモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-122">Exploring the Call Center Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="bd6ca-123">呼び出しセンター構造へのロジスティック回帰モデルの追加 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-123">Adding a Logistic Regression Model to the Call Center Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="bd6ca-124">「中級者向けデータマイニングチュートリアル &#40;コールセンターモデルの予測の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-124">Creating Predictions for the Call Center Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bd6ca-125">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="bd6ca-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bd6ca-126">呼び出しセンターデータのデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-126">Adding a Data Source View for Call Center Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="bd6ca-127">すべてのレッスン</span><span class="sxs-lookup"><span data-stu-id="bd6ca-127">All Lessons</span></span>  
 [<span data-ttu-id="bd6ca-128">レッスン 1: 中級者向けデータマイニングソリューションの作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-128">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="bd6ca-129">レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-129">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="bd6ca-130">レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="bd6ca-130">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="bd6ca-131">レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-131">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 <span data-ttu-id="bd6ca-132">レッスン 5: ニューラル ネットワークとロジスティック回帰のシナリオ (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="bd6ca-132">Lesson 5: Neural Network and Logistic Regression Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6ca-133">参照</span><span class="sxs-lookup"><span data-stu-id="bd6ca-133">See Also</span></span>  
 <span data-ttu-id="bd6ca-134">[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="bd6ca-134">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="bd6ca-135">中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="bd6ca-135">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
