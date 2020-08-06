---
title: 'レッスン 3: マーケットバスケットシナリオの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a281aa62fbf08393c95f12ded9886ac212b3165f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720481"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="d8b6e-102">レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="d8b6e-102">Lesson 3: Building a Market Basket Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="d8b6e-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のマーケティング部門は、クロスセルを促進するため自社の Web サイトを改善しようとしています。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-103">The marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to improve the company Web site to promote cross-selling.</span></span> <span data-ttu-id="d8b6e-104">サイトの更新に伴い、顧客の買い物かごの中に入っている他製品に基づいてその顧客が購入する可能性がある製品を予測できるようにしたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-104">As part of the site update, they would like the ability to predict products that a customer might want to purchase, based on the other products that are already in the customer's online shopping basket.</span></span> <span data-ttu-id="d8b6e-105">さらに、顧客の購入行動をより深く理解して、一緒に購入される可能性があるアイテムが同時に表示されるように Web サイトを設計したいとも考えています。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-105">The marketing department also wants to understand customer purchasing behavior better, so that they can design the Web site so that the items that tend to be purchased together appear together.</span></span> <span data-ttu-id="d8b6e-106">彼らはこの種の *マーケット バスケット分析* にはデータ マイニングが非常に効果的であることを理解しており、あなたにデータ マイニング モデルの開発を依頼してきました。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-106">They have learned that data mining is especially useful for this kind of *market basket analysis* and have asked you to develop a data mining model.</span></span>  
  
 <span data-ttu-id="d8b6e-107">このレッスンを完了すると、顧客のトランザクション履歴から商品のグループを表示する完全なマイニング モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-107">After you complete the tasks in this lesson, you will have a mining model that shows groups of items from historical customer transactions.</span></span> <span data-ttu-id="d8b6e-108">さらに、このマイニング モデルを使用して、顧客が追加購入する可能性がある商品を予測できます。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-108">Additionally, you can use the mining model to predict additional items that a customer may want to purchase.</span></span>  
  
 <span data-ttu-id="d8b6e-109">このレッスンのタスクを完了するには、「中級者向け[データマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」の最初のレッスンで作成したソリューションとデータソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-109">To complete the tasks in this lesson, you will use the solution and data source that you created in the first lesson of the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="d8b6e-110">顧客関連のテーブル (顧客の購入情報が格納される入れ子になったテーブルなど) を含むデータ ソース ビューを追加することで、このソリューションを変更します。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-110">You will modify this solution by adding a data source view that contains tables about the customer, including a nested table of customer purchases.</span></span>  <span data-ttu-id="d8b6e-111">次に、マーケット バスケット シナリオに適した Microsoft アソシエーション ルール アルゴリズムを使用するマイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-111">You will then build a mining model that uses the Microsoft Association Rules algorithm, which is suited to market basket scenarios.</span></span>  
  
 <span data-ttu-id="d8b6e-112">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d8b6e-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="d8b6e-113">入れ子になったテーブルを含むデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-113">Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="d8b6e-114">&#40;中級者向けデータマイニングチュートリアルの作成&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-114">Creating a Market Basket Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="d8b6e-115">「中級者向けデータマイニングチュートリアル &#40;のマーケットバスケットモデルの変更と処理&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-115">Modifying and Processing the Market Basket Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="d8b6e-116">&#40;中級者向けデータマイニングチュートリアルに関するマーケットバスケットモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-116">Exploring the Market Basket Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="d8b6e-117">マイニングモデルでの入れ子になったテーブルのフィルター処理 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-117">Filtering a Nested Table in a Mining Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="d8b6e-118">&#41;の関連付けの予測 &#40;中級者向けデータマイニングチュートリアル</span><span class="sxs-lookup"><span data-stu-id="d8b6e-118">Predicting Associations &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d8b6e-119">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="d8b6e-119">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d8b6e-120">入れ子になったテーブルを含むデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-120">Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="d8b6e-121">すべてのレッスン</span><span class="sxs-lookup"><span data-stu-id="d8b6e-121">All Lessons</span></span>  
 [<span data-ttu-id="d8b6e-122">レッスン 1: 中級者向けデータマイニングソリューションの作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-122">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="d8b6e-123">レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-123">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="d8b6e-124">レッスン 3: マーケット バスケット シナリオ (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="d8b6e-124">Lesson 3: Market Basket Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="d8b6e-125">レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-125">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [<span data-ttu-id="d8b6e-126">レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-126">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="d8b6e-127">参照</span><span class="sxs-lookup"><span data-stu-id="d8b6e-127">See Also</span></span>  
 <span data-ttu-id="d8b6e-128">[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="d8b6e-128">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="d8b6e-129">[レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="d8b6e-129">[Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="d8b6e-130">レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="d8b6e-130">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
