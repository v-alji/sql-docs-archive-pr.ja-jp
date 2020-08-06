---
title: 'レッスン 6: 予測の作成と操作 (基本的なデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b213cb58-2c40-4c89-b08b-d3c36a4afad3
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d0a8bfdf83e96622a19ac72490e8602d12afc9df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634169"
---
# <a name="lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial"></a><span data-ttu-id="cf014-102">レッスン 6: 予測の作成と操作 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="cf014-102">Lesson 6: Creating and Working with Predictions (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="cf014-103">作成したデータ マイニング モデルのトレーニング、テスト、および検証を行ってきました。</span><span class="sxs-lookup"><span data-stu-id="cf014-103">You have trained, tested, and explored the data mining models you created.</span></span> <span data-ttu-id="cf014-104">このモデルを使用して、新しい絞り込みメール配信キャンペーンに反応する可能性が最も高い顧客を識別する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="cf014-104">Now you are ready to use the models to identify the people most likely to respond to the new targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="cf014-105">このレッスンでは、クエリを作成して、自転車を購入する可能性が最も高い顧客を予測します。</span><span class="sxs-lookup"><span data-stu-id="cf014-105">In this lesson you will create a query to predict which customers are most likely to purchase a bike.</span></span> <span data-ttu-id="cf014-106">また、予測が正しい*確率*を取得して、マーケティング部門が予測を使用するかどうかを決定できるかどうかを判断することができます。</span><span class="sxs-lookup"><span data-stu-id="cf014-106">You will also retrieve the *probability* that the prediction is correct, so the marketing department can decide whether to you can decide whether to use the prediction or not.</span></span>  
  
 <span data-ttu-id="cf014-107">自転車を購入する確率が高い顧客を特定したら、マイニング モデルのケースの詳細へのドリルスルーを行い、特定した顧客の名前や連絡先情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="cf014-107">Once you have identified customers with a high probability of purchasing a bike, you will drill through to the details of the cases in the mining model to retrieve names and contact information for these customers.</span></span>  
  
 <span data-ttu-id="cf014-108">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cf014-108">This lesson contains the following topics:</span></span>  
  
 [<span data-ttu-id="cf014-109">予測の作成 &#40;基本的なデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="cf014-109">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="cf014-110">構造データでのドリルスルーの使用 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="cf014-110">Using Drillthrough on Structure Data &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="cf014-111">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="cf014-111">Next Lesson</span></span>  
 [<span data-ttu-id="cf014-112">中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="cf014-112">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="cf014-113">前のレッスン</span><span class="sxs-lookup"><span data-stu-id="cf014-113">Previous Lesson</span></span>  
 [<span data-ttu-id="cf014-114">レッスン 5: モデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="cf014-114">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="cf014-115">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="cf014-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="cf014-116">予測の作成 &#40;基本的なデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="cf014-116">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="cf014-117">参照</span><span class="sxs-lookup"><span data-stu-id="cf014-117">See Also</span></span>  
 <span data-ttu-id="cf014-118">[デシジョンツリーモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="cf014-118">[Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="cf014-119">予測クエリ ビルダーを使用した予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="cf014-119">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
