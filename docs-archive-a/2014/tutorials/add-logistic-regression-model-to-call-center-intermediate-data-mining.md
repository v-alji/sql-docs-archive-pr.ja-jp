---
title: コールセンター構造へのロジスティック回帰モデルの追加 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7d0100313d1ea5a1af5f729249bc2d743a730222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720559"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="45a34-102">コール センター構造へのロジスティック回帰モデルの追加 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="45a34-102">Adding a Logistic Regression Model to the Call Center Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="45a34-103">コール センターの業務に影響する可能性のある要因を分析すると共に、スタッフのサービス品質を向上させるための具体的な改善案を提出するように求められました。</span><span class="sxs-lookup"><span data-stu-id="45a34-103">In addition to analyzing the factors that might affect call center operations, you were also asked to provide some specific recommendations on how the staff can improve service quality.</span></span> <span data-ttu-id="45a34-104">ここでは、調査モデルの構築に使用したものと同じマイニング構造を使用し、予測作成用のマイニング モデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="45a34-104">In this task, you will use the same mining structure that you used to build the exploratory model and add a mining model that will be used for creating predictions.</span></span>  
  
 <span data-ttu-id="45a34-105">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のロジスティック回帰モデルは、ニューラル ネットワークのアルゴリズムを基礎としているため、ニューラル ネットワーク モデルと同等の柔軟性と機能を備えながらも、</span><span class="sxs-lookup"><span data-stu-id="45a34-105">In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], a logistic regression model is based on the neural networks algorithm, and therefore provides the same flexibility and power as a neural network model.</span></span> <span data-ttu-id="45a34-106">バイナリ結果を予測するという目的に特に適したモデルと言えます。</span><span class="sxs-lookup"><span data-stu-id="45a34-106">However, logistic regression is particularly well-suited for predicting binary outcomes.</span></span>  
  
 <span data-ttu-id="45a34-107">このシナリオでは、ニューラル ネットワーク モデルに使用したものと同じマイニング構造を使用します。</span><span class="sxs-lookup"><span data-stu-id="45a34-107">For this scenario, you will use the same mining structure that you used for the neural network model.</span></span> <span data-ttu-id="45a34-108">ただし、新しいモデルを実務上の目的に合わせてカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="45a34-108">However, you will customize the new model to target your business questions.</span></span> <span data-ttu-id="45a34-109">ここでは、サービス品質を向上させることと、経験を積んだオペレーターが何人必要かを特定することが目的であるため、それらの値を予測するモデルを設定します。</span><span class="sxs-lookup"><span data-stu-id="45a34-109">You are interested in improving service quality and determining how many experienced operators you need, so you will set up your model to predict those values.</span></span>  
  
 <span data-ttu-id="45a34-110">コール センター データに基づくすべてのモデルの類似性をできる限り確保するために、前の作業と同じシード パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="45a34-110">To ensure that all the models based on the call center data are as similar as possible, you will use the same seed value as before.</span></span> <span data-ttu-id="45a34-111">シード パラメーターを設定すると、モデルでのデータ処理の開始位置が同じになり、データのアーティファクトによるバリエーションを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="45a34-111">Setting the seed parameter ensures that the model processes the data from the same starting point, and minimizes variations caused by artifacts in the data.</span></span>  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a><span data-ttu-id="45a34-112">コール センターのマイニング構造に新しいマイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="45a34-112">To add a new mining model to the call center mining structure</span></span>  
  
1.  <span data-ttu-id="45a34-113">のソリューションエクスプローラーで、[ [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] マイニング構造] を右クリックし、[**コールセンター**] ビンをクリックして、[**デザイナーを開く**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45a34-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, right-click the mining structure, **Call Center Binned**, and select **Open Designer**.</span></span>  
  
2.  <span data-ttu-id="45a34-114">データマイニングデザイナーで、[**マイニングモデル**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45a34-114">In Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="45a34-115">[**関連マイニングモデルの作成] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="45a34-115">Click **Create a related mining model**.</span></span>  
  
4.  <span data-ttu-id="45a34-116">[**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に、「」と入力 `Call Center - LR` します。</span><span class="sxs-lookup"><span data-stu-id="45a34-116">In the **New Mining Model** dialog box, for **Model name**, type `Call Center - LR`.</span></span>  <span data-ttu-id="45a34-117">[**アルゴリズム名**] で、[ **Microsoft ロジスティック回帰**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45a34-117">For **Algorithm name**, select **Microsoft Logistic Regression**.</span></span>  
  
5.  <span data-ttu-id="45a34-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45a34-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="45a34-119">新しいマイニングモデルが [**マイニングモデル**] タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="45a34-119">The new mining model is displayed in the **Mining Models** tab.</span></span>  
  
### <a name="to-customize-the-logistic-regression-model"></a><span data-ttu-id="45a34-120">ロジスティック回帰モデルをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="45a34-120">To customize the logistic regression model</span></span>  
  
1.  <span data-ttu-id="45a34-121">新しいマイニングモデルの列で、 `Call Center - LR` ファクト CallCenter ID をキーとして残します。</span><span class="sxs-lookup"><span data-stu-id="45a34-121">In the column for the new mining model, `Call Center - LR`, leave Fact CallCenter ID as the key.</span></span>  
  
2.  <span data-ttu-id="45a34-122">ServiceGrade の値とレベル2の演算子を**Predict**に変更します。</span><span class="sxs-lookup"><span data-stu-id="45a34-122">Change the value of ServiceGrade and Level Two Operators to **Predict**.</span></span>  
  
     <span data-ttu-id="45a34-123">これらの列は、入力および予測の両方に使用されます。</span><span class="sxs-lookup"><span data-stu-id="45a34-123">These columns will be used both as input and for prediction.</span></span> <span data-ttu-id="45a34-124">本質的には、同じデータについて、2 つの別個のモデルを作成していることになります。ここでは、オペレーターの数を予測するモデルとサービス グレードを予測するモデルを作成しています。</span><span class="sxs-lookup"><span data-stu-id="45a34-124">In essence, you are creating two separate models on the same data: one that predicts the number of operators, and one that predicts the service grade.</span></span>  
  
3.  <span data-ttu-id="45a34-125">他のすべての列を**入力**に変更します。</span><span class="sxs-lookup"><span data-stu-id="45a34-125">Change all other columns to **Input**.</span></span>  
  
### <a name="to-specify-the-seed-and-process-the-models"></a><span data-ttu-id="45a34-126">シードを指定してモデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="45a34-126">To specify the seed and process the models</span></span>  
  
1.  <span data-ttu-id="45a34-127">[**マイニングモデル**] タブで、Call CENTER-LR という名前のモデルの列を右クリックし、[**アルゴリズムパラメーターの設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45a34-127">In the **Mining Model** tab, right-click the column for the model named Call Center - LR, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="45a34-128">HOLDOUT_SEED パラメーターの行で、[**値**] の下の空のセルをクリックし、「」と入力し `1` ます。</span><span class="sxs-lookup"><span data-stu-id="45a34-128">In the row for the HOLDOUT_SEED parameter, click the empty cell under **Value**, and type `1`.</span></span> <span data-ttu-id="45a34-129">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45a34-129">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45a34-130">関連するすべてのモデルで同じシードを使用する限り、シードとしてどのような値を選択するかは特に重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="45a34-130">The value that you choose as the seed does not matter, as long as you use the same seed for all related models.</span></span>  
  
3.  <span data-ttu-id="45a34-131">[**マイニングモデル**] メニューで、[**マイニング構造とすべてのモデルの処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45a34-131">In the **Mining Models** menu, select **Process Mining Structure and All Models**.</span></span> <span data-ttu-id="45a34-132">[**はい**] をクリックして、更新されたデータマイニングプロジェクトをサーバーに配置します。</span><span class="sxs-lookup"><span data-stu-id="45a34-132">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
4.  <span data-ttu-id="45a34-133">[**マイニングモデルの処理**] ダイアログボックスで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45a34-133">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
5.  <span data-ttu-id="45a34-134">[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じ、[**マイニングモデルの処理**] ダイアログボックスでもう一度 [**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45a34-134">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="45a34-135">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="45a34-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="45a34-136">「中級者向けデータマイニングチュートリアル &#40;コールセンターモデルの予測の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="45a34-136">Creating Predictions for the Call Center Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="45a34-137">参照</span><span class="sxs-lookup"><span data-stu-id="45a34-137">See Also</span></span>  
 [<span data-ttu-id="45a34-138">処理の要件および注意事項 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="45a34-138">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
