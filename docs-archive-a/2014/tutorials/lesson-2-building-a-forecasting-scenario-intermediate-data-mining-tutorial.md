---
title: 'レッスン 2: 予測シナリオの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c81d5846df0a37c2b4182cb92fea86ce6f3417a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631431"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="63a78-102">レッスン 2: 予測シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="63a78-102">Lesson 2: Building a Forecasting Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="63a78-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]のセールス アナリストであるあなたは、翌年の製品売上を予測するよう依頼されました。</span><span class="sxs-lookup"><span data-stu-id="63a78-103">As the sales analyst for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], you have been asked to forecast the sales of products for the next year.</span></span> <span data-ttu-id="63a78-104">具体的には、さまざまな地域および製品ラインの売上予測を比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63a78-104">In particular, you have been asked to compare forecasts for the different regions and product lines.</span></span> <span data-ttu-id="63a78-105">さらに、各製品の売上が一年を通じてどのように変化するかも調べなければなりません。</span><span class="sxs-lookup"><span data-stu-id="63a78-105">Additionally, you have been asked to determine whether sales of different products vary depending on the time of the year.</span></span>  
  
 <span data-ttu-id="63a78-106">依頼された情報を得るため、このレッスンでは、同社の売上データを月別に集計します。また、これらの販売成績をヨーロッパ、北米、太平洋の 3 つの地域別に集計します。</span><span class="sxs-lookup"><span data-stu-id="63a78-106">To find the requested information, in this lesson you will summarize the company's sales data at the monthly level, and you will also summarize sales figures by three regions: Europe, North America, and the Pacific.</span></span>  
  
 <span data-ttu-id="63a78-107">このレッスンのタスクを完了すると、次の情報を取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="63a78-107">After you complete the tasks in this lesson, you will be able to answer the following questions:</span></span>  
  
-   <span data-ttu-id="63a78-108">各種の自転車の売上の時系列における変化。</span><span class="sxs-lookup"><span data-stu-id="63a78-108">How do the sales of different bike models change over time?</span></span>  
  
-   <span data-ttu-id="63a78-109">3 つの地域での売上パターンに違いがあるかどうか。</span><span class="sxs-lookup"><span data-stu-id="63a78-109">Are there differences between the patterns for sales in the three regions?</span></span>  
  
-   <span data-ttu-id="63a78-110">売上高が最も多い時期を予測できるか。</span><span class="sxs-lookup"><span data-stu-id="63a78-110">Can we forecast sales peaks?</span></span>  
  
 <span data-ttu-id="63a78-111">レッスンは、2 つに分けて行うことができます。</span><span class="sxs-lookup"><span data-stu-id="63a78-111">The lesson can be completed in two parts:</span></span>  
  
-   <span data-ttu-id="63a78-112">第 1 部では、タイム シリーズ モデルを作成および使用する方法の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="63a78-112">Part One introduces the basics of how to create and use a time series model.</span></span>  
  
-   <span data-ttu-id="63a78-113">第 2 部では、すべての地域に基づいた汎用的なタイム シリーズ モデルを作成する方法を、順をおって説明します。</span><span class="sxs-lookup"><span data-stu-id="63a78-113">Part Two walks you through creation of a general time series model, based on all regions.</span></span> <span data-ttu-id="63a78-114">*クロス予測*にこの一般的なモデルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="63a78-114">You can use this general model for *cross-prediction*.</span></span>  
  
 <span data-ttu-id="63a78-115">このレッスンのタスクを完了するには、「レッスン 1: 中級者向けデータ [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] [マイニングソリューションの作成 &#40;中間データマイニングチュートリアル&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)」で作成したデータソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="63a78-115">To complete the tasks in this lesson, which are listed below, you will use the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source that you created in [Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="63a78-116">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] サンプル データベース内の日付は、このリリース用に更新されています。</span><span class="sxs-lookup"><span data-stu-id="63a78-116">The dates in the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] sample database have been updated for this release.</span></span> <span data-ttu-id="63a78-117">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]の以前のバージョンを使用する場合は、ここでの手順に従ってモデルを構築することはできますが、異なる結果が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="63a78-117">If you use an earlier version of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], you can build the model following these steps, but you might see different results.</span></span>  
  
 <span data-ttu-id="63a78-118">**簡単な予測モデルの作成**</span><span class="sxs-lookup"><span data-stu-id="63a78-118">**Creating a Simple Forecasting Model**</span></span>  
  
-   [<span data-ttu-id="63a78-119">予測のためのデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-119">Adding a Data Source View for Forecasting &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="63a78-120">中間データマイニングチュートリアル &#40;予測構造とモデルの作成&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-120">Creating a Forecasting Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="63a78-121">中間データマイニングチュートリアル &#40;予測構造の変更&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-121">Modifying the Forecasting Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="63a78-122">予測モデルのカスタマイズと処理 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-122">Customizing and Processing the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="63a78-123">予測モデル &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-123">Exploring the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="63a78-124">タイムシリーズ予測の作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-124">Creating Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="63a78-125">**クロス予測のための一般的な予測モデルの作成**</span><span class="sxs-lookup"><span data-stu-id="63a78-125">**Creating a General Forecasting Model for Cross-Prediction**</span></span>  
  
-   [<span data-ttu-id="63a78-126">高度な時系列予測 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-126">Advanced Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="63a78-127">更新されたデータを使用した時系列予測 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-127">Time Series Predictions using Updated Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="63a78-128">交換データ &#40;中間データマイニングチュートリアル&#41;を使用した時系列予測</span><span class="sxs-lookup"><span data-stu-id="63a78-128">Time Series Predictions using Replacement Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="63a78-129">予測モデルの予測の比較 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-129">Comparing Predictions for Forecasting Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="63a78-130">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="63a78-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="63a78-131">予測のためのデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-131">Adding a Data Source View for Forecasting &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="63a78-132">タイムシリーズモデルの要件について &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-132">Understanding the Requirements for a Time Series Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="63a78-133">すべてのレッスン</span><span class="sxs-lookup"><span data-stu-id="63a78-133">All Lessons</span></span>  
 [<span data-ttu-id="63a78-134">レッスン 1: 中級者向けデータマイニングソリューションの作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-134">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="63a78-135">レッスン 2: 予測シナリオ (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="63a78-135">Lesson 2: Forecasting Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="63a78-136">レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="63a78-136">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="63a78-137">レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-137">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [<span data-ttu-id="63a78-138">レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="63a78-138">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="63a78-139">参照</span><span class="sxs-lookup"><span data-stu-id="63a78-139">See Also</span></span>  
 <span data-ttu-id="63a78-140">[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="63a78-140">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="63a78-141">[中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="63a78-141">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="63a78-142">Microsoft Time Series アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="63a78-142">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
