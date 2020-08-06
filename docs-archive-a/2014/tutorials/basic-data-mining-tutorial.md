---
title: 基本的なデータマイニングチュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ed557ffb5b8592be4d4375aca40e461d699d6ba7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720529"
---
# <a name="basic-data-mining-tutorial"></a><span data-ttu-id="c9e69-102">基本的なデータ マイニング チュートリアル</span><span class="sxs-lookup"><span data-stu-id="c9e69-102">Basic Data Mining Tutorial</span></span>
  <span data-ttu-id="c9e69-103">「 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 基本的なデータマイニングチュートリアル」へようこそ。</span><span class="sxs-lookup"><span data-stu-id="c9e69-103">Welcome to the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Basic Data Mining Tutorial.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="c9e69-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]には、データマイニングモデルを作成し、予測を行うための統合環境が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c9e69-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides an integrated environment for creating data mining models and making predictions.</span></span> <span data-ttu-id="c9e69-105">このチュートリアルでは、機械学習を使用して顧客の購買行動を分析および予測することで、絞り込みメール配信キャンペーンのためのシナリオを完成させます。</span><span class="sxs-lookup"><span data-stu-id="c9e69-105">In this tutorial, you will complete a scenario for a targeted mailing campaign in which you use machine learning to analyze and predict customer purchasing behavior.</span></span> <span data-ttu-id="c9e69-106">このチュートリアルでは、クラスタリング、デシジョン ツリー、Naive Bayes (ナイーブ ベイズ) という非常に重要な 3 つのデータ マイニング アルゴリズムを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-106">The tutorial demonstrates how to use three of the most important data mining algorithms: clustering, decision trees, and Naive Bayes.</span></span> <span data-ttu-id="c9e69-107">また、マイニングモデルビューアーを使用して結果を分析する方法や、に含まれるデータマイニングツールを使用して予測と精度チャートを作成する方法についても説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c9e69-107">You will also learn how to analyze your findings using the mining model viewers, and to create predictions and accuracy charts using the data mining tools that are included in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c9e69-108">すべての例で、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-108">The fictitious company, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], is used for all examples.</span></span>  
  
 <span data-ttu-id="c9e69-109">データマイニングツールを使い慣れている場合は、「[中間データマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」も完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c9e69-109">When you are comfortable using the data mining tools, we recommend that you also complete the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="c9e69-110">これらのレッスンでは、予測、マーケット バスケット分析、タイム シリーズ (時系列)、アソシエーション モデル、入れ子になったテーブル、およびシーケンス クラスターの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-110">The lessons demonstrate how to use forecasting, market basket analysis, time series, association models, nested tables, and sequence clustering.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="c9e69-111">チュートリアルのシナリオ</span><span class="sxs-lookup"><span data-stu-id="c9e69-111">Tutorial Scenario</span></span>  
 <span data-ttu-id="c9e69-112">このチュートリアルでは、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 購入履歴に基づいて会社の顧客の詳細を学習し、その履歴データを使用してマーケティングで使用できる予測を作成した従業員の従業員です。</span><span class="sxs-lookup"><span data-stu-id="c9e69-112">In this tutorial, you are an employee of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] who has been tasked with learning more about the company's customers based on historical purchases, and then using that historical data to make predictions that can be used in marketing.</span></span> <span data-ttu-id="c9e69-113">会社はこれまでデータ マイニングを行ったことがなかったので、データ マイニング専用の新しいデータベースを作成し、データ マイニング モデルを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9e69-113">The company has never done data mining before, so you must create a new database specifically for data mining and set up several data mining models.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="c9e69-114">学習する内容</span><span class="sxs-lookup"><span data-stu-id="c9e69-114">What You Will Learn</span></span>  
 <span data-ttu-id="c9e69-115">このチュートリアルでは、さまざまな種類の機械学習メソッドの作成方法と使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-115">This tutorial teaches you how to create and work with several different types of machine learning methods.</span></span> <span data-ttu-id="c9e69-116">また、マイニング モデルのコピーを作成し、入力データにフィルターを適用してさまざまな結果を取得する方法も学習します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-116">You will also learn how to create a copy of a mining model, and apply a filter to the input data to get different results.</span></span> <span data-ttu-id="c9e69-117">その後、リフト チャートを使用して、両方のモデルの結果を比較できます。</span><span class="sxs-lookup"><span data-stu-id="c9e69-117">Afterwards you can compare the results of both models using a lift chart.</span></span> <span data-ttu-id="c9e69-118">最後に、ドリルスルーを使用して、基になるマイニング構造から詳細なデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-118">Finally, you will use drillthrough to retrieve additional data from the underlying mining structure.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="c9e69-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データマイニングには、複数の予測モデルを簡単に開発して比較し、結果に対してアクションを実行するために役立つ次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="c9e69-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Data Mining includes the following features that help you easily develop and compare multiple predictive models and then take actions on the results :</span></span>  
  
-   <span data-ttu-id="c9e69-120">*予約テストセット-* マイニング構造を作成するときに、マイニング構造のデータをトレーニングセットとテストセットに分割できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c9e69-120">*Holdout Test Sets -* When you create a mining structure, you can now divide the data in the mining structure into training and testing sets.</span></span> <span data-ttu-id="c9e69-121">これにより、類似のデータ セットに対してモデルをテストし、関連するモデルの精度を比較できます。</span><span class="sxs-lookup"><span data-stu-id="c9e69-121">This lets you test models on similar data sets, and compare the accuracy of related models.</span></span>  
  
-   <span data-ttu-id="c9e69-122">*マイニングモデルフィルター-* これで、フィルターをマイニングモデルにアタッチし、トレーニングとテストの両方でフィルターを適用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c9e69-122">*Mining model filters -* You can now attach filters to a mining model, and apply the filter during both training and testing.</span></span> <span data-ttu-id="c9e69-123">これにより、データの異なるサブセットに対して関連モデルを簡単に構築できます。</span><span class="sxs-lookup"><span data-stu-id="c9e69-123">This lets you easily build related models on different subsets of the data.</span></span>  
  
-   <span data-ttu-id="c9e69-124">*構造ケースおよび構造列へのドリルスルー-* マイニングモデルの一般的なパターンから、データソース内の実用的な詳細に簡単に移動できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c9e69-124">*Drillthrough to Structure Cases and Structure Columns -* You can now easily move from the general patterns in the mining model to actionable detail in the data source.</span></span>  
  
 <span data-ttu-id="c9e69-125">このチュートリアルは次のレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c9e69-125">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="c9e69-126">レッスン 1: Analysis Services データベースの準備 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="c9e69-126">Lesson 1: Preparing the Analysis Services Database &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 <span data-ttu-id="c9e69-127">このレッスンでは、新しい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを作成する方法、データ ソースとデータ ソース ビューを追加する方法、およびデータ マイニングで使用する新しいデータベースを準備する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-127">In this lesson, you will learn how to create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, add a data source and data source view, and prepare the new database to be used with data mining.</span></span>  
  
 [<span data-ttu-id="c9e69-128">レッスン 2: &#40;の基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="c9e69-128">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 <span data-ttu-id="c9e69-129">このレッスンでは、絞り込みメール配信シナリオの一部として使用できるマイニング モデル構造の作成方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-129">In this lesson, you will learn how to create a mining model structure that can be used as part of a targeted mailing scenario.</span></span>  
  
 [<span data-ttu-id="c9e69-130">レッスン 3: モデルの追加と処理</span><span class="sxs-lookup"><span data-stu-id="c9e69-130">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 <span data-ttu-id="c9e69-131">このレッスンでは、構造にモデルを追加する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-131">In this lesson you will learn how to add models to a structure.</span></span> <span data-ttu-id="c9e69-132">モデルの作成には、次のアルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-132">The models you create are built with the following algorithms:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="c9e69-133">デシジョンツリー</span><span class="sxs-lookup"><span data-stu-id="c9e69-133">Decision Trees</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="c9e69-134">クラスター</span><span class="sxs-lookup"><span data-stu-id="c9e69-134">Clustering</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="c9e69-135">Naive Bayes</span><span class="sxs-lookup"><span data-stu-id="c9e69-135">Naive Bayes</span></span>  
  
 [<span data-ttu-id="c9e69-136">レッスン 4: 「基本的なデータマイニングチュートリアル」 &#40;対象を絞ったメーリングモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="c9e69-136">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 <span data-ttu-id="c9e69-137">このレッスンでは、ビューアーを使用して各モデルの結果を調査および解釈する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-137">In this lesson you will learn how to explore and interpret the findings of each model using the Viewers.</span></span>  
  
 [<span data-ttu-id="c9e69-138">レッスン 5: モデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="c9e69-138">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 <span data-ttu-id="c9e69-139">このレッスンでは、いずれかの絞り込みメール配信モデルのコピーを作成し、トレーニング データを制限するためのマイニング モデル フィルターを特定の顧客のセットに追加し、モデルの実行可能性を評価します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-139">In this lesson, you make a copy of one of the targeted mailing models, add a mining model filter to restrict the training data to a particular set of customers, and then assess the viability of the model.</span></span>  
  
 [<span data-ttu-id="c9e69-140">レッスン 6: 予測の作成と操作 &#40;基本的なデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="c9e69-140">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 <span data-ttu-id="c9e69-141">「基本的なデータ マイニング チュートリアル」の最後のレッスンでは、モデルを使用して、自転車を購入する可能性が最も高い顧客を予測します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-141">In this final lesson of the Basic Data Mining Tutorial, you use the model to predict which customers are most likely to purchase a bike.</span></span> <span data-ttu-id="c9e69-142">次に、基になるケースをドリルスルーして連絡先情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="c9e69-142">You then drill through to the underlying cases to obtain contact information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e69-143">必要条件</span><span class="sxs-lookup"><span data-stu-id="c9e69-143">Requirements</span></span>  
 <span data-ttu-id="c9e69-144">次のソフトウェアがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c9e69-144">Make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="c9e69-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9e69-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="c9e69-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元モードで</span><span class="sxs-lookup"><span data-stu-id="c9e69-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in multidimensional mode</span></span>  
  
-   <span data-ttu-id="c9e69-147">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース。</span><span class="sxs-lookup"><span data-stu-id="c9e69-147">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="c9e69-148">セキュリティ強化のため、サンプル データベースは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と一緒にインストールされません。</span><span class="sxs-lookup"><span data-stu-id="c9e69-148">To enhance security, the sample databases are not installed with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c9e69-149">の公式データベースをインストールするには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Microsoft SQL サンプルデータベース](https://go.microsoft.com/fwlink/?LinkId=88417)のページにアクセスし、を選択して [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="c9e69-149">To install the official databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visit the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page and select [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9e69-150">チュートリアルを通じて作業する場合、ドキュメントビューアーのツールバーに**次のトピック**と**前のトピック**のボタンを追加すると、手順を前後に移動しやすくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="c9e69-150">When you are working through a tutorial, you might find it easier to move back and forth between the steps if you add the **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e69-151">参照</span><span class="sxs-lookup"><span data-stu-id="c9e69-151">See Also</span></span>  
 <span data-ttu-id="c9e69-152">[データマイニングソリューション](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="c9e69-152">[Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span></span>  
 <span data-ttu-id="c9e69-153">[マイニングモデルタスクと操作方法](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="c9e69-153">[Mining Model Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="c9e69-154">DMX を使用したデータ マイニング モデルの作成とクエリ : チュートリアル &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="c9e69-154">Creating and Querying Data Mining Models with DMX: Tutorials &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  
