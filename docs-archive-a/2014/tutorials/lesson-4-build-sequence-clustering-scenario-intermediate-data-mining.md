---
title: 'レッスン 4: シーケンスクラスターシナリオの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0f417c685d8af898de7c66ffe82045fa76b582e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711178"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="59304-102">レッスン 4: シーケンス クラスター シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="59304-102">Lesson 4: Building a Sequence Clustering Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="59304-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のマーケティング部門は、顧客が [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] Web サイトをどのように閲覧するのかを把握しようとしています。</span><span class="sxs-lookup"><span data-stu-id="59304-103">The marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to understand how customers move through the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] Web site.</span></span> <span data-ttu-id="59304-104">同社は、顧客が製品を買い物かごに入れる順序に一定のパターンがあるのではないかと推測しています。</span><span class="sxs-lookup"><span data-stu-id="59304-104">The company suspects that there is a pattern to the order in which customers put products into their shopping baskets.</span></span> <span data-ttu-id="59304-105">マーケティング部門は、顧客がどのような場合に関連商品を買い物かごに追加するかを把握するために、購入順序を分析しようとしています。</span><span class="sxs-lookup"><span data-stu-id="59304-105">They want to analyze the order of purchase sequences to learn how customers add related items to their baskets.</span></span> <span data-ttu-id="59304-106">この情報を使用すると、Web サイトのフローを効率化し、別の製品も購入するように顧客を導くことができます。</span><span class="sxs-lookup"><span data-stu-id="59304-106">They can then use this information to streamline the flow of the Web site so that it leads customers to purchase additional products.</span></span>  
  
 <span data-ttu-id="59304-107">このレッスンを完了すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して顧客が次に買い物かごに入れる商品を予測するマイニング モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="59304-107">After you complete the tasks in this lesson, you will have created a mining model that uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm to predict the next item that customers will put into their shopping baskets.</span></span> <span data-ttu-id="59304-108">次に、2 つのバージョンのモデルを検証します。1 つは、顧客が買い物かごに商品を入れる順序のみを分析するモデルで、もう 1 つは、クラスタリングのための追加の顧客の人口統計を含むモデルです。</span><span class="sxs-lookup"><span data-stu-id="59304-108">You will experiment with two versions of the model: one that analyzes only the order of products in the basket, and one that contains some additional customer demographics for clustering.</span></span> <span data-ttu-id="59304-109">最後に、これらのモデルを使用して、顧客に商品を勧めるために使用できる予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="59304-109">Finally, you will use the models to create predictions that you can use to recommend products to customers.</span></span>  
  
 <span data-ttu-id="59304-110">このレッスンのタスクを完了するには、「[レッスン 3: マーケットバスケットシナリオの構築](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)」で作成したマーケットバスケットマイニング構造を使用して&#41;&#40;中級者向けデータマイニングチュートリアルを使用します。</span><span class="sxs-lookup"><span data-stu-id="59304-110">To complete the tasks in the lesson, you will use the market basket mining structure that you created in [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="59304-111">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="59304-111">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="59304-112">シーケンスクラスターマイニングモデル構造の作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-112">Creating a Sequence Clustering Mining Model Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="59304-113">シーケンス クラスター モデルの処理</span><span class="sxs-lookup"><span data-stu-id="59304-113">Processing the Sequence Clustering Model</span></span>](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [<span data-ttu-id="59304-114">シーケンスクラスターモデル &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-114">Exploring the Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="59304-115">関連するシーケンスクラスターモデルの作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-115">Creating a Related Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="59304-116">シーケンスクラスターモデルでの予測の作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-116">Creating Predictions on a Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="59304-117">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="59304-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="59304-118">シーケンスクラスターマイニングモデル構造の作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-118">Creating a Sequence Clustering Mining Model Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="59304-119">すべてのレッスン</span><span class="sxs-lookup"><span data-stu-id="59304-119">All Lessons</span></span>  
 [<span data-ttu-id="59304-120">レッスン 1: 中級者向けデータマイニングソリューションの作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-120">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="59304-121">レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-121">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="59304-122">レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="59304-122">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="59304-123">レッスン 4: シーケンス クラスター シナリオ (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="59304-123">Lesson 4: Sequence Clustering Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="59304-124">レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-124">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="59304-125">参照</span><span class="sxs-lookup"><span data-stu-id="59304-125">See Also</span></span>  
 <span data-ttu-id="59304-126">[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="59304-126">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="59304-127">中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="59304-127">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
