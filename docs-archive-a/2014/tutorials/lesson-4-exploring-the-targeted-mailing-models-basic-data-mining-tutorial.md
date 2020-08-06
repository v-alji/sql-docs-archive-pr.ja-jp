---
title: 'レッスン 4: 絞り込みメール配信モデルの調査 (基本的なデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e00c5b9-a9f8-4503-99ee-377c9cc02d7f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8659350b126164e06550acdbecec04bb07499c55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720469"
---
# <a name="lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial"></a><span data-ttu-id="eee7b-102">レッスン 4: 絞り込みメール配信モデルの検証 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="eee7b-102">Lesson 4: Exploring the Targeted Mailing Models (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="eee7b-103">プロジェクト内のモデルを処理した後、そのモデルを検証して、興味深い傾向を探すことができます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-103">After the models in your project have been processed, you can explore them to look for interesting trends.</span></span> <span data-ttu-id="eee7b-104">パターンは複雑で、単純に数値を観察するだけでは見つけにくいことがあるため、SQL Server データ マイニング機能は、データを調査する目的、およびアルゴリズムがデータ内で見つけたルールとリレーションシップを理解する目的で役立つビジュアル ツールを用意しています。</span><span class="sxs-lookup"><span data-stu-id="eee7b-104">Because patterns can be complex and difficult simply by looking at numbers, SQL Server Data Mining provides some visual tools that help you investigate the data and understand the rules and relationships that the algorithms have discovered within the data.</span></span> <span data-ttu-id="eee7b-105">また、さまざまな精度テストを使用してデータセットを検証し、モデルを配置する前にどのモデルが最も適切に機能するかを判断することができます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-105">You can also use a variety of accuracy tests to validate your dataset or discover which model performs best before you deploy it.</span></span>  
  
 <span data-ttu-id="eee7b-106">を使用し [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] てモデルを探索すると、作成した各モデルが、データマイニングデザイナーの [**マイニングモデルビューアー** ] タブに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-106">When you use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to explore your models, each model you created is listed in the **Mining Model Viewer** tab in Data Mining Designer.</span></span> <span data-ttu-id="eee7b-107">各種のビューアーを使用して、モデルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-107">You can use the viewers to explore the models.</span></span> <span data-ttu-id="eee7b-108">これらのビューアーは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-108">These viewers are also available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="eee7b-109">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のどのアルゴリズムを使用してモデルを作成したかによって、それぞれ結果が異なります。</span><span class="sxs-lookup"><span data-stu-id="eee7b-109">Each algorithm that you used to build a model in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] returns a different type of result.</span></span> <span data-ttu-id="eee7b-110">したがって、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、機械学習モデルの種類ごとにカスタム ビューアーを用意しています。</span><span class="sxs-lookup"><span data-stu-id="eee7b-110">Therefore, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides custom viewers for each type of machine learning model.</span></span>  
  
 <span data-ttu-id="eee7b-111">詳細については、「 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **汎用コンテンツツリービューアー**」と呼ばれる HTML ビューアーも用意されています。これにより、モデルデータと、検出されたパターンに関する詳細情報が半表形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-111">If you want to get into details, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] also provides an HTML viewer, called the **Generic Content Tree Viewer**, that displays detailed information about the model data and any patterns that were found, in a semi-tabular format.</span></span> <span data-ttu-id="eee7b-112">詳細については、「 [Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eee7b-112">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="eee7b-113">このレッスンでは、3 つのモデルを使用して結果を観察します。</span><span class="sxs-lookup"><span data-stu-id="eee7b-113">In this lesson you will look at the results from your three models.</span></span> <span data-ttu-id="eee7b-114">モデルの種類ごとに、基になるアルゴリズムが異なり、データの検証方法も異なります。</span><span class="sxs-lookup"><span data-stu-id="eee7b-114">Each model type is based on a different algorithm and provides different insights into the data.</span></span>  
  
-   <span data-ttu-id="eee7b-115">デシジョン ツリー モデルでは、自転車の購入に影響を与える要因がわかります。</span><span class="sxs-lookup"><span data-stu-id="eee7b-115">The Decision Tree model tells you about factors that influence bike buying.</span></span>  
  
-   <span data-ttu-id="eee7b-116">クラスター モデルでは、自転車の購買行動を含む属性やその他の任意の属性ごとに顧客をグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-116">The Clustering model groups your customers by attributes that include their bike buying behavior and other selected attributes.</span></span>  
  
-   <span data-ttu-id="eee7b-117">Naive Bayes モデルでは、さまざまな属性間のリレーションシップを検証できます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-117">The Naive Bayes model enables you to explore the relationship between different attributes.</span></span>  
  
 <span data-ttu-id="eee7b-118">各マイニング モデル ビューアーの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eee7b-118">See the following topics to learn more about each of the mining model viewers.</span></span>  
  
-   [<span data-ttu-id="eee7b-119">デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="eee7b-119">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="eee7b-120">「基本的なデータマイニングチュートリアル」 &#40;クラスターモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="eee7b-120">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="eee7b-121">Naive Bayes Model &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="eee7b-121">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="eee7b-122">**汎用コンテンツツリービューアー**を使用して3つすべてのモデルを表示し、数式やデータ値などを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="eee7b-122">All three models can be viewed using the **Generic Content Tree Viewer**, to extract formulas, data values, and so forth.</span></span>  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="eee7b-123">このレッスンの最初の作業</span><span class="sxs-lookup"><span data-stu-id="eee7b-123">First Task in Lesson</span></span>  
 [<span data-ttu-id="eee7b-124">デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="eee7b-124">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="eee7b-125">前のレッスン</span><span class="sxs-lookup"><span data-stu-id="eee7b-125">Previous Lesson</span></span>  
 [<span data-ttu-id="eee7b-126">レッスン 3: モデルの追加と処理</span><span class="sxs-lookup"><span data-stu-id="eee7b-126">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="eee7b-127">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="eee7b-127">Next Lesson</span></span>  
 [<span data-ttu-id="eee7b-128">レッスン 5: モデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="eee7b-128">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="eee7b-129">参照</span><span class="sxs-lookup"><span data-stu-id="eee7b-129">See Also</span></span>  
 <span data-ttu-id="eee7b-130">[マイニングモデルビューアーのタスクと操作方法](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="eee7b-130">[Mining Model Viewer Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="eee7b-131">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="eee7b-131">Data Mining Model Viewers</span></span>](../../2014/analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
