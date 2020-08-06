---
title: 絞り込みメール配信構造でのモデルの処理 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d8233bb-117e-4563-9302-8a5a8ad1fae2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b8fb7b9f601f351520c3f611cc3c520614ed8ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714925"
---
# <a name="processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="bfaa3-102">絞り込みメール配信構造でのモデルの処理 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="bfaa3-102">Processing Models in the Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="bfaa3-103">作成したマイニング モデルを参照したり操作したりする前に、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを配置し、マイニング構造とマイニング モデルを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-103">Before you can browse or work with the mining models that you have created, you must deploy the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project and process the mining structure and mining models.</span></span>  
  
-   <span data-ttu-id="bfaa3-104">*配置*によってサーバーにプロジェクトが送信され、サーバー上のそのプロジェクトにオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-104">*Deploying* sends the project to a server and creates any objects in that project on the server.</span></span>  
  
-   <span data-ttu-id="bfaa3-105">*処理* [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、リレーショナルデータソースのデータをオブジェクトに格納します。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-105">*Processing* populates [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects with data from relational data sources.</span></span>  
  
 <span data-ttu-id="bfaa3-106">モデルを使用するには、事前にそのモデルを配置して処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-106">Models cannot be used until they have been deployed and processed.</span></span> <span data-ttu-id="bfaa3-107">また、新しいデータの追加などにより、モデルに変更を加えた場合は、モデルを再配置して再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-107">Also, when you make any changes to the model, such as adding new data, you must redeploy and reprocess the models.</span></span>  
  
## <a name="ensuring-consistency-with-holdoutseed"></a><span data-ttu-id="bfaa3-108">HoldoutSeed との一貫性の確保</span><span class="sxs-lookup"><span data-stu-id="bfaa3-108">Ensuring Consistency with HoldoutSeed</span></span>  
 <span data-ttu-id="bfaa3-109">プロジェクトを配置し、構造とモデルを処理すると、データ構造内の個々の行が数値型のシード値に基づいてトレーニング セットまたはテスト セットに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-109">When you deploy a project and process the structure and models, individual rows in your data structure are assigned to either the training set or testing set based on a numerical seed value.</span></span> <span data-ttu-id="bfaa3-110">既定では、数値型のシード値は、データ構造の属性に基づいて計算されます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-110">By default, the numerical seed value is computed based on attributes of the data structure.</span></span> <span data-ttu-id="bfaa3-111">ただし、モデルの特定の側面を変更すると、シード値も変更されるため、微妙に異なる結果につながります。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-111">However, if you ever change some aspects of your model, the seed value would change, leading to subtly different results.</span></span> <span data-ttu-id="bfaa3-112">したがって、ここで説明した結果が同じであることを確認するために、では固定提示*シード*を任意に割り当て `12` ます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-112">Therefore, in order to ensure that your results are the same as described here, we will arbitrarily assign a fixed *holdout seed* of `12`.</span></span> <span data-ttu-id="bfaa3-113">提示されたシードは、サンプリング アルゴリズムの初期化に使用され、すべてのマイニング構造とそのモデルで同じ方法でデータが分割されるようにします。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-113">The holdout seed is used to initialize the sampling algorithm, and ensures that the data is partitioned in roughly the same way for all mining structures and their models.</span></span>  
  
 <span data-ttu-id="bfaa3-114">この値は、トレーニング セット内に含まれるケースの数に影響しません。単純に、モデルを構築するたびに、同じ分割方法が使用されることを保証します。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-114">This value does not affect the number of cases in the training set; it simply ensures that the same partitioning method will be used each time you build the model.</span></span>  
  
 <span data-ttu-id="bfaa3-115">提示されたシードの詳細については、「[データセットのトレーニングとテスト](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-115">For more information on holdout seed, see [Training and Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).</span></span>  
  
#### <a name="to-set-the-holdout-seed"></a><span data-ttu-id="bfaa3-116">提示されたシードを設定するには</span><span class="sxs-lookup"><span data-stu-id="bfaa3-116">To set the Holdout Seed</span></span>  
  
1.  <span data-ttu-id="bfaa3-117">のデータマイニングデザイナーで、[**マイニング構造**] タブまたは [**マイニングモデル**] タブをクリックし [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-117">Click on the **Mining Structure** tab or the **Mining Models** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="bfaa3-118">**絞り込みメール配信 MiningStructure**が**プロパティ**ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-118">**Targeted Mailing MiningStructure** displays in the **Properties** pane.</span></span>  
  
2.  <span data-ttu-id="bfaa3-119">**F4**キーを押して、[**プロパティ**] ウィンドウが開いていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-119">Ensure that the **Properties** pane is open by pressing **F4**.</span></span>  
  
3.  <span data-ttu-id="bfaa3-120">**Cachemode**が**KeepTrainingCases**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-120">Ensure that **CacheMode** is set to **KeepTrainingCases**.</span></span>  
  
4.  <span data-ttu-id="bfaa3-121">「 `12` For **HoldoutSeed**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-121">Enter `12` for **HoldoutSeed**.</span></span>  
  
## <a name="deploying-and-processing-the-models"></a><span data-ttu-id="bfaa3-122">モデルの配置と処理</span><span class="sxs-lookup"><span data-stu-id="bfaa3-122">Deploying and Processing the Models</span></span>  
 <span data-ttu-id="bfaa3-123">データマイニングデザイナーでは、モデルまたは基になるデータに対して行った変更のスコープに応じて、どのオブジェクトを処理するかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-123">In Data Mining Designer, you can decide which objects to process, depending on the scope of changes you've made to your model or the underlying data:</span></span>  
  
 <span data-ttu-id="bfaa3-124">ここでは、既存の設定に変更を加えるのではなく、新しいデータと新しいモデルを使用するため、構造とすべてのモデルを同時に処理します。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-124">For this task, because the data and the models are new, you will process the structure and all the models at the same time.</span></span>  
  
#### <a name="to-deploy-the-project-and-process-all-the-mining-models"></a><span data-ttu-id="bfaa3-125">プロジェクトを配置してすべてのマイニング モデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="bfaa3-125">To deploy the project and process all the mining models</span></span>  
  
1.  <span data-ttu-id="bfaa3-126">[**マイニングモデル**] メニューで、[**マイニング構造とすべてのモデルの処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-126">In the **Mining Model** menu, select **Process Mining Structure and All Models**.</span></span>  
  
     <span data-ttu-id="bfaa3-127">マイニング構造に変更を加えた場合は、マイニング モデルを処理する前にプロジェクトをビルドして配置するように求められます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-127">If you made changes to the structure, you will be prompted to build and deploy the project before processing the models.</span></span> <span data-ttu-id="bfaa3-128">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-128">Click **Yes**.</span></span>  
  
2.  <span data-ttu-id="bfaa3-129">[**マイニング構造の処理-対象メーリング**] ダイアログボックスで [**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-129">Click **Run** in the **Processing Mining Structure - Targeted Mailing** dialog box.</span></span>  
  
     <span data-ttu-id="bfaa3-130">**[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-130">The **Process Progress** dialog box opens to display the details of model processing.</span></span> <span data-ttu-id="bfaa3-131">使用するコンピューターによっては、モデル処理に多少時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-131">Model processing might take some time, depending on your computer.</span></span>  
  
3.  <span data-ttu-id="bfaa3-132">モデルの処理が完了したら、 **[処理の進行状況]** ダイアログ ボックスの **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-132">Click **Close** in the **Process Progress** dialog box after the models have completed processing.</span></span>  
  
4.  <span data-ttu-id="bfaa3-133">[**マイニング構造の処理- \<structure> \*\* ] ダイアログボックスで [**閉じる\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfaa3-133">Click **Close** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="bfaa3-134">このレッスンの前の作業</span><span class="sxs-lookup"><span data-stu-id="bfaa3-134">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="bfaa3-135">&#40;基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造への新しいモデルの追加&#41;</span><span class="sxs-lookup"><span data-stu-id="bfaa3-135">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="bfaa3-136">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="bfaa3-136">Next Lesson</span></span>  
 [<span data-ttu-id="bfaa3-137">レッスン 4: 「基本的なデータマイニングチュートリアル」 &#40;対象を絞ったメーリングモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="bfaa3-137">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="bfaa3-138">参照</span><span class="sxs-lookup"><span data-stu-id="bfaa3-138">See Also</span></span>  
 [<span data-ttu-id="bfaa3-139">処理の要件および注意事項 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="bfaa3-139">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
