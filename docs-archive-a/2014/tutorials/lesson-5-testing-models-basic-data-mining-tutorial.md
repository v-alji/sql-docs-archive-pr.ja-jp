---
title: 'レッスン 5: モデルのテスト (基本的なデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fcfd9a9e90d9c6800af4dfd1599bbdd62d9520ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719065"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a><span data-ttu-id="7b380-102">レッスン 5: モデルのテスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="7b380-102">Lesson 5: Testing Models (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="7b380-103">絞り込みメール配信シナリオのトレーニング セットを使用してモデルを処理したので、テスト セットに対してモデルをテストします。</span><span class="sxs-lookup"><span data-stu-id="7b380-103">Now that you have processed the model by using the targeted mailing scenario training set, you will test your models against the testing set.</span></span> <span data-ttu-id="7b380-104">検証は、データ マイニング プロセスにおける重要な手順です。</span><span class="sxs-lookup"><span data-stu-id="7b380-104">Validation is an important step in the data mining process.</span></span> <span data-ttu-id="7b380-105">運用環境に配置する前に、実際のデータに対する絞り込みメール配信マイニング モデルの性能を把握しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="7b380-105">Knowing how well your targeted mailing mining models perform against real data is important before you deploy the models into a production environment.</span></span>  
  
 <span data-ttu-id="7b380-106">テスト セット内のデータには自転車購入に関する既知の値が既に含まれているため、モデルの予測が正しいかどうかを簡単に判断できます。</span><span class="sxs-lookup"><span data-stu-id="7b380-106">Because the data in the testing set already contains known values for bike buying, it is easy to determine whether the model's predictions are correct.</span></span> <span data-ttu-id="7b380-107">最高のを実行するモデルは、マーケティング部門によって、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 対象となるメーリングキャンペーンの顧客を識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b380-107">The model that performs the best will be used by the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department to identify the customers for their targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="7b380-108">このレッスンでは、複数の手法を使用してモデルを検証します。</span><span class="sxs-lookup"><span data-stu-id="7b380-108">In this lesson you will validate your models using multiple methods:</span></span>  
  
1.  <span data-ttu-id="7b380-109">テストセットに対して予測を作成し、既知の結果に対するモデルの精度を確認します。</span><span class="sxs-lookup"><span data-stu-id="7b380-109">You'll make predictions against the testing set to see how accurate the model is on known results.</span></span> <span data-ttu-id="7b380-110">*リフトチャート*を使用して、その効果を測定します。</span><span class="sxs-lookup"><span data-stu-id="7b380-110">You'll use a *lift chart* to measure its effectiveness.</span></span>  
  
     [<span data-ttu-id="7b380-111">リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="7b380-111">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  <span data-ttu-id="7b380-112">フィルター選択されたデータ サブセットを対象にしてモデルをテストします。</span><span class="sxs-lookup"><span data-stu-id="7b380-112">You will test your models on a filtered subset of the data.</span></span> <span data-ttu-id="7b380-113">同じリフト チャート内で複数のモデルを比較できます。</span><span class="sxs-lookup"><span data-stu-id="7b380-113">You can compare multiple models in the same lift chart.</span></span>  
  
     [<span data-ttu-id="7b380-114">フィルター選択されたモデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="7b380-114">Testing a Filtered Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="7b380-115">モデルの検証全般の詳細については、「[データマイニングの概念](../../2014/analysis-services/data-mining/data-mining-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b380-115">For more information about how model validation in general, see [Data Mining Concepts](../../2014/analysis-services/data-mining/data-mining-concepts.md).</span></span>  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="7b380-116">このレッスンの最初の作業</span><span class="sxs-lookup"><span data-stu-id="7b380-116">First Task in Lesson</span></span>  
 [<span data-ttu-id="7b380-117">リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="7b380-117">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="7b380-118">前のレッスン</span><span class="sxs-lookup"><span data-stu-id="7b380-118">Previous Lesson</span></span>  
 [<span data-ttu-id="7b380-119">レッスン 4: 「基本的なデータマイニングチュートリアル」 &#40;対象を絞ったメーリングモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="7b380-119">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="7b380-120">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="7b380-120">Next Lesson</span></span>  
 [<span data-ttu-id="7b380-121">レッスン 6: 予測の作成と操作 &#40;基本的なデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="7b380-121">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="7b380-122">参照</span><span class="sxs-lookup"><span data-stu-id="7b380-122">See Also</span></span>  
 <span data-ttu-id="7b380-123">[[リフトチャート] タブ &#40;マイニング精度チャートビュー&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md) </span><span class="sxs-lookup"><span data-stu-id="7b380-123">[Lift Chart Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md) </span></span>  
 <span data-ttu-id="7b380-124">[リフトチャート &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7b380-124">[Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7b380-125">[データマイニング&#41;のテストと検証 &#40;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7b380-125">[Testing and Validation &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md) </span></span>  
 <span data-ttu-id="7b380-126">[[分類マトリックス] タブ &#40;マイニング精度チャートビュー&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md) </span><span class="sxs-lookup"><span data-stu-id="7b380-126">[Classification Matrix Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md) </span></span>  
 [<span data-ttu-id="7b380-127">分類マトリックス &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="7b380-127">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  
