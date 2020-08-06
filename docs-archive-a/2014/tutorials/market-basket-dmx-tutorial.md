---
title: マーケットバスケット DMX のチュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- market basket analysis [Analysis Services]
- tutorials [Data Mining]
- tutorials [DMX]
ms.assetid: 6e262a1d-c89e-4033-8368-46cf25168ef5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe12f1c4ca1c0946572c61e89f4f4edb8ba9a762
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720463"
---
# <a name="market-basket-dmx-tutorial"></a><span data-ttu-id="84cd6-102">マーケット バスケット DMX のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="84cd6-102">Market Basket DMX Tutorial</span></span>
  <span data-ttu-id="84cd6-103">このチュートリアルでは、データマイニング拡張機能 (DMX) クエリ言語を使用して、マイニングモデルを作成、トレーニング、および調査する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-103">In this tutorial, you will learn how to create, train, and explore mining models by using the Data Mining Extensions (DMX) query language.</span></span> <span data-ttu-id="84cd6-104">その後、このマイニング モデルを使用して、同時に購入される傾向が高い製品を示す予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-104">You will then use these mining models to create predictions that describe which products tend to be purchased at the same time.</span></span>  
  
 <span data-ttu-id="84cd6-105">マイニング モデルは、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプル データベース内のデータから作成します。このサンプル データベースには、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のデータが格納されています。</span><span class="sxs-lookup"><span data-stu-id="84cd6-105">The mining models will be created from the data contained in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="84cd6-106">は、多国籍の大規模な製造企業です。</span><span class="sxs-lookup"><span data-stu-id="84cd6-106">is a large, multinational manufacturing company.</span></span> <span data-ttu-id="84cd6-107">北米、ヨーロッパ、およびアジアの市場向けに、金属製自転車や複合材製自転車の製造および販売を行っています。</span><span class="sxs-lookup"><span data-stu-id="84cd6-107">The company manufactures and sells metal and composite bicycles to North American, European, and Asian commercial markets.</span></span> <span data-ttu-id="84cd6-108">企業の拠点は従業員 290 人を擁する米国ワシントン州ボセルで、また各国の市場の拠点として、複数の地域販売チームが配置されています。</span><span class="sxs-lookup"><span data-stu-id="84cd6-108">Its base operation is located in Bothell, Washington, with 290 employees, and it has several regional sales teams are located throughout their international market base.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="84cd6-109">チュートリアルのシナリオ</span><span class="sxs-lookup"><span data-stu-id="84cd6-109">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="84cd6-110">は、データ マイニング機能を用いたカスタム アプリケーションを作成して、同時に購入する傾向が高い製品の種類を予測することにしました。</span><span class="sxs-lookup"><span data-stu-id="84cd6-110">has decided to create a custom application that employs data mining functionality to predict what types of products their customers tend to purchase at the same time.</span></span> <span data-ttu-id="84cd6-111">このカスタム アプリケーションの目標は、一連の製品を指定できるようにし、指定した製品と共に購入される追加製品を予測できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="84cd6-111">The goal for the custom application is to be able to specify a set of products, and predict what additional products will be purchased with the specified products.</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="84cd6-112">はこれらの情報を使用して、企業の Web サイトで "お勧め" の製品を表示すると共に、顧客によりわかりやすく情報を表示したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="84cd6-112">will then use this information to add a "suggest" feature to their website, and also to better organize the way that they present information to their customers.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="84cd6-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、このタスクを実行するために使用できるいくつかのツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="84cd6-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish this task:</span></span>  
  
-   <span data-ttu-id="84cd6-114">DMX クエリ言語</span><span class="sxs-lookup"><span data-stu-id="84cd6-114">The DMX query language</span></span>  
  
-   <span data-ttu-id="84cd6-115">[Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="84cd6-115">The [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)</span></span>  
  
-   <span data-ttu-id="84cd6-116">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディター</span><span class="sxs-lookup"><span data-stu-id="84cd6-116">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="84cd6-117">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で提供されるデータ マイニング拡張機能 (DMX) は、マイニング モデルの作成と作業に使用できるクエリ言語です。</span><span class="sxs-lookup"><span data-stu-id="84cd6-117">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create and work with mining models.</span></span> <span data-ttu-id="84cd6-118">アソシエーションアルゴリズムによって、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 一緒に購入される可能性のある製品を予測できるモデルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-118">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm creates models that can predict the products that are likely to be purchased together.</span></span>  
  
 <span data-ttu-id="84cd6-119">このチュートリアルの目標は、カスタム アプリケーションで使用する DMX クエリを設定することです。</span><span class="sxs-lookup"><span data-stu-id="84cd6-119">The goal of this tutorial is to provide the DMX queries that will be used in the custom application.</span></span>  
  
 <span data-ttu-id="84cd6-120">**詳細については、「** [データマイニングソリューション](../../2014/analysis-services/data-mining/data-mining-solutions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84cd6-120">**For more information:** [Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span></span>  
  
## <a name="mining-structure-and-mining-models"></a><span data-ttu-id="84cd6-121">マイニング構造とマイニングモデル</span><span class="sxs-lookup"><span data-stu-id="84cd6-121">Mining Structure and Mining Models</span></span>  
 <span data-ttu-id="84cd6-122">DMX ステートメントを作成するにあたっては、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がマイニング モデルの作成に使用する主なオブジェクトを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="84cd6-122">Before you begin to create DMX statements, it is important to understand the main objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="84cd6-123">*マイニング構造*は、マイニングモデルの作成元のデータドメインを定義するデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="84cd6-123">The *mining structure* is a data structure that defines the data domain from which mining models are built.</span></span> <span data-ttu-id="84cd6-124">1つのマイニング構造には、同じドメインを共有する複数の*マイニングモデル*を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-124">A single mining structure can contain multiple *mining models* that share the same domain.</span></span> <span data-ttu-id="84cd6-125">マイニング モデルは、マイニング構造によって表されるデータにマイニング モデル アルゴリズムを適用します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-125">A mining model applies a mining model algorithm to the data, which is represented by a mining structure.</span></span>  
  
 <span data-ttu-id="84cd6-126">マイニング構造の構成要素は、データ ソースに格納されているデータについて記述したマイニング構造列です。</span><span class="sxs-lookup"><span data-stu-id="84cd6-126">The building blocks of the mining structure are the mining structure columns, which describe the data that the data source contains.</span></span> <span data-ttu-id="84cd6-127">マイニング構造列には、データ型、コンテンツの種類、データの配布方法などの情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-127">These columns contain information such as data type, content type, and how the data is distributed.</span></span>  
  
 <span data-ttu-id="84cd6-128">マイニング モデルには、マイニング構造で記述されたキー列と、残りの列のサブセットが含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="84cd6-128">Mining models must contain the key column described in the mining structure, as well as a subset of the remaining columns.</span></span> <span data-ttu-id="84cd6-129">マイニング モデルでは、各列の使用法と、マイニング モデルの作成に使用するアルゴリズムを定義します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-129">The mining model defines the usage for each column and defines the algorithm that is used to create the mining model.</span></span> <span data-ttu-id="84cd6-130">たとえば、DMX では列がキー列または PREDICT 列であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-130">For example, in DMX you can specify that a column is a Key column or a PREDICT column.</span></span> <span data-ttu-id="84cd6-131">指定されない列は入力列として扱われます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-131">If a column is left unspecified, it is assumed to be an input column.</span></span>  
  
 <span data-ttu-id="84cd6-132">DMX でマイニング モデルを作成するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="84cd6-132">In DMX, there are two ways to create mining models.</span></span> <span data-ttu-id="84cd6-133">1 つは、`CREATE MINING MODEL` ステートメントを使用して、マイニング構造とそれに関連するマイニング モデルを一度に作成する方法です。もう 1 つは、最初に `CREATE MINING STRUCTURE` ステートメントを使用してマイニング構造を作成し、`ALTER STRUCTURE` ステートメントを使用してマイニング モデルを追加する方法です。</span><span class="sxs-lookup"><span data-stu-id="84cd6-133">You can either create the mining structure and associated mining model together by using the `CREATE MINING MODEL` statement, or you can first create a mining structure by using the `CREATE MINING STRUCTURE` statement, and then add a mining model to the structure by using the `ALTER STRUCTURE` statement.</span></span> <span data-ttu-id="84cd6-134">これらの方法について次に説明します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-134">These methods are described below.</span></span>  
  
 `CREATE MINING MODEL`  
 <span data-ttu-id="84cd6-135">このステートメントを使用すると、マイニング構造とそれに関連するマイニング モデルを一度に、同じ名前を使って作成できます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-135">Use this statement to create a mining structure and associated mining model together using the same name.</span></span> <span data-ttu-id="84cd6-136">マイニング構造と区別するため、マイニング モデルの名前には "Structure" という文字列が付加されます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-136">The mining model name is appended with "Structure" to differentiate it from the mining structure.</span></span>  
  
 <span data-ttu-id="84cd6-137">このステートメントは、1 つのマイニング モデルを含むマイニング構造を作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="84cd6-137">This statement is useful if you are creating a mining structure that will contain a single mining model.</span></span>  
  
 <span data-ttu-id="84cd6-138">詳細については、「[CREATE MINING MODEL (DMX)](/sql/dmx/create-mining-model-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84cd6-138">For more information, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span>  
  
 <span data-ttu-id="84cd6-139">CREATE MINING STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="84cd6-139">CREATE MINING STRUCTURE</span></span>  
 <span data-ttu-id="84cd6-140">新しいマイニング構造をモデルなしで作成するには、このステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-140">Use this statement to create a new mining structure without any models.</span></span>  
  
 <span data-ttu-id="84cd6-141">CREATE MINING STRUCTURE を使用すると、予約データ セットも作成できます。予約データ セットは、同一のマイニング構造に基づくすべてのモデルをテストするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-141">When you use CREATE MINING STRUCTURE, you can also create a holdout data set that can be used for testing any models that are based on the same mining structure.</span></span>  
  
 <span data-ttu-id="84cd6-142">詳細については、「[CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84cd6-142">For more information, see [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).</span></span>  
  
 `ALTER MINING STRUCTURE`  
 <span data-ttu-id="84cd6-143">このステートメントを使用すると、サーバー上に既に存在するマイニング構造にマイニング モデルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-143">Use this statement to add a mining model to a mining structure that already exists on the server.</span></span>  
  
 <span data-ttu-id="84cd6-144">1 つのマイニング構造に複数のマイニング モデルを追加すると、いくつかの作業に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-144">There are several reasons that you would want to add more than one mining model in a single mining structure.</span></span> <span data-ttu-id="84cd6-145">たとえば、異なるアルゴリズムを使用して複数のマイニング モデルを作成し、最適なアルゴリズムを見つけ出すことができます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-145">For example, you might create several mining models using different algorithms to see which one works best.</span></span> <span data-ttu-id="84cd6-146">または、同じアルゴリズムを使用して複数のマイニングモデルを作成することもできますが、パラメーターの設定はマイニングモデルごとに異なるため、パラメーターに最適な設定を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="84cd6-146">Alternatively, you might create several mining models using the same algorithm, but with a parameter set differently for each mining model to find the best setting for that parameter.</span></span>  
  
 <span data-ttu-id="84cd6-147">詳細については、「 [ALTER マイニング STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84cd6-147">For more information, see [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).</span></span>  
  
 <span data-ttu-id="84cd6-148">このチュートリアルでは複数のマイニング モデルを含むマイニング構造を作成します。したがって、2 つ目の方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-148">Because you will create a mining structure that contains several mining models, you will use the second method in this tutorial.</span></span>  
  
 <span data-ttu-id="84cd6-149">**詳細情報**</span><span class="sxs-lookup"><span data-stu-id="84cd6-149">**For More Information**</span></span>  
  
 <span data-ttu-id="84cd6-150">Dmx [&#41; リファレンス &#40;データマイニング拡張機能](/sql/dmx/data-mining-extensions-dmx-reference)、Dmx の[Select ステートメント](/sql/dmx/understanding-the-dmx-select-statement)、[構造、および Dmx 予測クエリの使用方法](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)について説明します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-150">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference), [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement), [Structure and Usage of DMX Prediction Queries](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="84cd6-151">学習する内容</span><span class="sxs-lookup"><span data-stu-id="84cd6-151">What You Will Learn</span></span>  
 <span data-ttu-id="84cd6-152">このチュートリアルは次のレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="84cd6-152">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="84cd6-153">レッスン 1: Market Basket マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="84cd6-153">Lesson 1: Creating the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)  
 <span data-ttu-id="84cd6-154">このレッスンでは、`CREATE` ステートメントを使用して、マイニング構造を作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-154">In this lesson, you will learn how to use the `CREATE` statement to create mining structures.</span></span>  
  
 [<span data-ttu-id="84cd6-155">レッスン 2: Market Basket マイニング構造へのマイニング モデルの追加</span><span class="sxs-lookup"><span data-stu-id="84cd6-155">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
 <span data-ttu-id="84cd6-156">このレッスンでは、`ALTER` ステートメントを使用して、マイニング モデルをマイニング構造に追加する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-156">In this lesson, you will learn how to use the `ALTER` statement to add mining models to a mining structure.</span></span>  
  
 [<span data-ttu-id="84cd6-157">レッスン 3: Market Basket マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="84cd6-157">Lesson 3: Processing the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
 <span data-ttu-id="84cd6-158">このレッスンでは、ステートメントを使用して、 `INSERT INTO` マイニング構造とそれに関連付けられているマイニングモデルを処理する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-158">In this lesson, you will learn how to use the `INSERT INTO` statement to process mining structures and their associated mining models.</span></span>  
  
 [<span data-ttu-id="84cd6-159">レッスン 4: マーケット バスケット予測の実行</span><span class="sxs-lookup"><span data-stu-id="84cd6-159">Lesson 4: Executing Market Basket Predictions</span></span>](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
 <span data-ttu-id="84cd6-160">このレッスンでは、`PREDICTION JOIN` ステートメントを使用して、マイニング モデルに対する予測を作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-160">In this lesson, you will learn how to use the `PREDICTION JOIN` statement to create predictions against mining models.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84cd6-161">必要条件</span><span class="sxs-lookup"><span data-stu-id="84cd6-161">Requirements</span></span>  
 <span data-ttu-id="84cd6-162">このチュートリアルを行う前に、次のソフトウェアがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="84cd6-162">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="84cd6-163">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84cd6-163">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="84cd6-164">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84cd6-164">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="84cd6-165">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース</span><span class="sxs-lookup"><span data-stu-id="84cd6-165">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database</span></span>  
  
 <span data-ttu-id="84cd6-166">セキュリティ強化のため、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="84cd6-166">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="84cd6-167">の公式サンプルデータベースをインストールするに [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、 [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) 「」の「Microsoft SQL Server のサンプルとコミュニティプロジェクト」のホームページにアクセスして Microsoft SQL Server 製品サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="84cd6-167">To install the official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], go to [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) or on the Microsoft SQL Server Samples and Community Projects home page in the section Microsoft SQL Server Product Samples.</span></span> <span data-ttu-id="84cd6-168">[**データベース**] をクリックし、[**リリース**] タブをクリックして、目的のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="84cd6-168">Click **Databases**, then click the **Releases** tab and select the databases that you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84cd6-169">チュートリアルを確認するときは、ドキュメントビューアーのツールバーに**次のトピック**と**前のトピック**のボタンを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="84cd6-169">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cd6-170">参照</span><span class="sxs-lookup"><span data-stu-id="84cd6-170">See Also</span></span>  
 <span data-ttu-id="84cd6-171">[自転車購入者 DMX チュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="84cd6-171">[Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span></span>  
 <span data-ttu-id="84cd6-172">[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="84cd6-172">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="84cd6-173">レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="84cd6-173">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
