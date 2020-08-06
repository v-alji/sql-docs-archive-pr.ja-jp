---
title: 時系列予測 DMX のチュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fbc9a0640767b3fbae04cebb9a047c2ec2b669b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632828"
---
# <a name="time-series-prediction-dmx-tutorial"></a><span data-ttu-id="bcab8-102">時系列予測の DMX のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="bcab8-102">Time Series Prediction DMX Tutorial</span></span>
  <span data-ttu-id="bcab8-103">このチュートリアルでは、時系列マイニング構造を作成し、3 つのカスタム時系列マイニング モデルを作成し、それらのモデルを使用して予測を行う方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="bcab8-103">In this tutorial, you will learn how to create a time series mining structure, create three custom time series mining models, and then make predictions by using those models.</span></span>  
  
 <span data-ttu-id="bcab8-104">マイニング モデルの作成は、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプル データベース内のデータに基づいて行います。このサンプル データベースには、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のデータが格納されています。</span><span class="sxs-lookup"><span data-stu-id="bcab8-104">The mining models are based on the data contained in the  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="bcab8-105">は、多国籍の大規模な製造企業です。</span><span class="sxs-lookup"><span data-stu-id="bcab8-105">is a large, multinational manufacturing company.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="bcab8-106">チュートリアルのシナリオ</span><span class="sxs-lookup"><span data-stu-id="bcab8-106">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="bcab8-107">は、データ マイニングを使用して売上予測を生成することにしました。</span><span class="sxs-lookup"><span data-stu-id="bcab8-107">has decided to use data mining to generate sales projections.</span></span> <span data-ttu-id="bcab8-108">既にいくつかのリージョン予測モデルが構築されています。詳細については、「[レッスン 2: 予測シナリオの作成」 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcab8-108">They have already built some regional forecasting models; for more information, see [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="bcab8-109">営業部門で、そのデータ マイニング モデルを新しい売上データで定期的に更新できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcab8-109">However, the Sales Department needs to be able to periodically update the data mining model with new sales data.</span></span> <span data-ttu-id="bcab8-110">また、さまざまな予測が得られるようにモデルをカスタマイズしたいとも考えています。</span><span class="sxs-lookup"><span data-stu-id="bcab8-110">They also want to customize the models to provide different projections.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="bcab8-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、このタスクを実行するために使用できるいくつかのツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="bcab8-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish this task:</span></span>  
  
-   <span data-ttu-id="bcab8-112">データ マイニング拡張機能 (DMX) クエリ言語</span><span class="sxs-lookup"><span data-stu-id="bcab8-112">The Data Mining Extensions (DMX) query language</span></span>  
  
-   <span data-ttu-id="bcab8-113">Microsoft タイムシリーズアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="bcab8-113">The Microsoft Time Series Algorithm</span></span>  
  
-   <span data-ttu-id="bcab8-114">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディター</span><span class="sxs-lookup"><span data-stu-id="bcab8-114">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="bcab8-115">[!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムでは、時間に関するデータの予測に使用できるモデルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bcab8-115">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm creates models that can be used for prediction of time-related data.</span></span> <span data-ttu-id="bcab8-116">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で提供されるデータ マイニング拡張機能 (DMX) は、マイニング モデルと予測クエリの作成に使用できるクエリ言語です。</span><span class="sxs-lookup"><span data-stu-id="bcab8-116">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create mining models and prediction queries.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="bcab8-117">学習する内容</span><span class="sxs-lookup"><span data-stu-id="bcab8-117">What You Will Learn</span></span>  
 <span data-ttu-id="bcab8-118">このチュートリアルでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でマイニング モデルを作成するために使用するオブジェクトについて理解していることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="bcab8-118">This tutorial assumes that you are already familiar with the objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="bcab8-119">DMX を使用してマイニング構造またはマイニングモデルをまだ作成していない場合は、「[自転車購入者向け Dmx チュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcab8-119">If you have not previously created a mining structure or mining model by using DMX, see [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).</span></span>  
  
 <span data-ttu-id="bcab8-120">このチュートリアルは次のレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="bcab8-120">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="bcab8-121">レッスン 1: 時系列マイニング モデルおよびマイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="bcab8-121">Lesson 1: Creating a Time Series Mining Model and Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 <span data-ttu-id="bcab8-122">このレッスンでは、`CREATE MINING MODEL` ステートメントを使用して、新しい予測モデルと関連マイニング モデルを追加する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="bcab8-122">In this lesson, you will learn how to use the `CREATE MINING MODEL` statement to add a new forecasting model and a related mining model.</span></span>  
  
 [<span data-ttu-id="bcab8-123">レッスン 2: 時系列マイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="bcab8-123">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 <span data-ttu-id="bcab8-124">このレッスンでは、ALTER MINING STRUCTURE ステートメントを使用して、新しいマイニング モデルを時系列構造に追加する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="bcab8-124">In this lesson, you will learn how to use the ALTER MINING STRUCTURE statement to add new mining models to the time series structure.</span></span> <span data-ttu-id="bcab8-125">また、時系列の分析に使用されるアルゴリズムをカスタマイズする方法も学習します。</span><span class="sxs-lookup"><span data-stu-id="bcab8-125">You will also learn how to customize the algorithm used for analyzing a time series.</span></span>  
  
 [<span data-ttu-id="bcab8-126">レッスン 3: 時系列構造と時系列モデルの処理</span><span class="sxs-lookup"><span data-stu-id="bcab8-126">Lesson 3: Processing the Time Series Structure and Models</span></span>](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 <span data-ttu-id="bcab8-127">このレッスンでは、`INSERT INTO` ステートメントを使用して [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベースのデータを構造に取り込むことによってモデルをトレーニングする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="bcab8-127">In this lesson, you will learn how to train the models by using the `INSERT INTO` statement and populating the structure with data from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 [<span data-ttu-id="bcab8-128">レッスン 4: DMX を使用した時系列予測の作成</span><span class="sxs-lookup"><span data-stu-id="bcab8-128">Lesson 4: Creating Time Series Predictions Using DMX</span></span>](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 <span data-ttu-id="bcab8-129">このレッスンでは、時系列予測を作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="bcab8-129">In this lesson, you will learn how to create time series predictions.</span></span>  
  
 [<span data-ttu-id="bcab8-130">レッスン 5 : 時系列モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="bcab8-130">Lesson 5: Extending the Time Series Model</span></span>](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 <span data-ttu-id="bcab8-131">このレッスンでは、`EXTEND_MODEL_CASES` パラメーターを使用して、予測を行うときに新しいデータでモデルを更新する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="bcab8-131">In this lesson, you will learn how to use the `EXTEND_MODEL_CASES` parameter to update the model with new data when you make predictions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcab8-132">必要条件</span><span class="sxs-lookup"><span data-stu-id="bcab8-132">Requirements</span></span>  
 <span data-ttu-id="bcab8-133">このチュートリアルを行う前に、次のソフトウェアがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bcab8-133">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="bcab8-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcab8-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="bcab8-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcab8-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="bcab8-136">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース</span><span class="sxs-lookup"><span data-stu-id="bcab8-136">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database</span></span>  
  
 <span data-ttu-id="bcab8-137">セキュリティ強化のため、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="bcab8-137">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="bcab8-138">の公式サンプルデータベースをインストールするに [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、 [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) 「」の「Microsoft SQL Server のサンプルとコミュニティプロジェクト」のホームページにアクセスして Microsoft SQL Server 製品サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcab8-138">To install the official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], go to [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) or on the Microsoft SQL Server Samples and Community Projects home page in the section Microsoft SQL Server Product Samples.</span></span> <span data-ttu-id="bcab8-139">[**データベース**] をクリックし、[**リリース**] タブをクリックして、目的のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="bcab8-139">Click **Databases**, then click the **Releases** tab and select the databases that you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcab8-140">チュートリアルを確認するときは、ドキュメントビューアーのツールバーに**次のトピック**と**前のトピック**のボタンを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bcab8-140">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcab8-141">参照</span><span class="sxs-lookup"><span data-stu-id="bcab8-141">See Also</span></span>  
 <span data-ttu-id="bcab8-142">[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="bcab8-142">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="bcab8-143">中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="bcab8-143">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
