---
title: 'レッスン 3: モデルの追加と処理 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cc29927a-c368-4b8a-bbd0-af89a9f54dc9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5da034089d8bbe7f1a967258d195a56ddbf13c03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632205"
---
# <a name="lesson-3-adding-and-processing-models"></a><span data-ttu-id="d29bd-102">レッスン 3: モデルの追加と処理</span><span class="sxs-lookup"><span data-stu-id="d29bd-102">Lesson 3: Adding and Processing Models</span></span>
  <span data-ttu-id="d29bd-103">前のレッスンで作成したマイニング構造には、[!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムに基づくマイニング モデルが 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="d29bd-103">The mining structure that you created in the previous lesson contains a single mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="d29bd-104">ターゲット メーリング キャンペーンのための顧客を識別するために、このモデルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d29bd-104">You can use this model to identify customers for the targeted mailing campaign.</span></span> <span data-ttu-id="d29bd-105">ただし、徹底的な分析を行うには、異なるアルゴリズムを使用して関連モデルを作成し、それらの結果を比較する方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="d29bd-105">However, to ensure that your analysis is thorough, it is a common practice to create related models using different algorithms and compare their results.</span></span> <span data-ttu-id="d29bd-106">これにより、さまざまな洞察を得ることもできます。</span><span class="sxs-lookup"><span data-stu-id="d29bd-106">That way you can get different insights as well.</span></span> <span data-ttu-id="d29bd-107">このため、追加の 2 つのモデルを作成し、それらのモデルを処理および配置します。</span><span class="sxs-lookup"><span data-stu-id="d29bd-107">Therefore, you will create two additional models, then process and deploy the models.</span></span>  
  
 <span data-ttu-id="d29bd-108">このレッスンでは、見込み顧客のリストの中から、製品を購入する可能性の高い顧客を予測するマイニング モデルのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="d29bd-108">In this lesson, you will create a set of mining models that will suggest the most likely customers from a list of potential customers.</span></span>  
  
 <span data-ttu-id="d29bd-109">このレッスンのタスクを完了するには、 [Microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)と[Microsoft Naive Bayes アルゴリズム](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="d29bd-109">To complete the tasks in this lesson, you will use the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) and the [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md).</span></span>  
  
 <span data-ttu-id="d29bd-110">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d29bd-110">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="d29bd-111">&#40;基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造への新しいモデルの追加&#41;</span><span class="sxs-lookup"><span data-stu-id="d29bd-111">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="d29bd-112">「&#40;基本的なデータマイニングチュートリアル」では、対象となるメーリングの構造でのモデルの処理&#41;</span><span class="sxs-lookup"><span data-stu-id="d29bd-112">Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="d29bd-113">このレッスンの最初の作業</span><span class="sxs-lookup"><span data-stu-id="d29bd-113">First Task in Lesson</span></span>  
 [<span data-ttu-id="d29bd-114">&#40;基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造への新しいモデルの追加&#41;</span><span class="sxs-lookup"><span data-stu-id="d29bd-114">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="d29bd-115">前のレッスン</span><span class="sxs-lookup"><span data-stu-id="d29bd-115">Previous Lesson</span></span>  
 [<span data-ttu-id="d29bd-116">レッスン 2: &#40;の基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="d29bd-116">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="d29bd-117">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="d29bd-117">Next Lesson</span></span>  
 [<span data-ttu-id="d29bd-118">レッスン 4: 「基本的なデータマイニングチュートリアル」 &#40;対象を絞ったメーリングモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="d29bd-118">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="d29bd-119">参照</span><span class="sxs-lookup"><span data-stu-id="d29bd-119">See Also</span></span>  
 [<span data-ttu-id="d29bd-120">マイニング モデルを構造に追加する &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="d29bd-120">Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)  
  
  
