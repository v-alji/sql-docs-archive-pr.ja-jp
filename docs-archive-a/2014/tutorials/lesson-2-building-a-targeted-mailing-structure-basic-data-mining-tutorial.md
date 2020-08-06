---
title: 'レッスン 2: 絞り込みメール配信構造の作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d0d6ceb-49b5-47c7-9ee6-464da43cc1f6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 005baa09e802a9ffe98f87239070401f170ddfa9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631422"
---
# <a name="lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="6587e-102">レッスン 2: 絞り込みメール配信構造の作成 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="6587e-102">Lesson 2: Building a Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="6587e-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のマーケティング部門は、売上増大を図るため、対象顧客を絞り込んでメーリング キャンペーンを実施することにしました。</span><span class="sxs-lookup"><span data-stu-id="6587e-103">The Marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to increase sales by targeting specific customers for a mailing campaign.</span></span> <span data-ttu-id="6587e-104">同社のデータベースには、以前に製品を購入した顧客のリストと、新しい見込み顧客のリストが保存されています。</span><span class="sxs-lookup"><span data-stu-id="6587e-104">The company's database contains a list of past customers and a list of potential new customers.</span></span> <span data-ttu-id="6587e-105">同社では、以前の顧客の属性を調査して購買パターンを特定し、そのパターンが見込み顧客に適用できることを希望しています。</span><span class="sxs-lookup"><span data-stu-id="6587e-105">By investigating the attributes of previous customers, the company hopes to discover patterns that they can then apply to potential customers.</span></span> <span data-ttu-id="6587e-106">たとえば、過去の傾向を使用して、自転車を購入する可能性が最も高い顧客を予測し [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] たり、将来のマーケティングキャンペーンのための顧客セグメントを作成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6587e-106">For example, they might use past trends to predict which potential customers are most likely to purchase a bike from [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], or create customer segments for future marketing campaigns.</span></span>  
  
 <span data-ttu-id="6587e-107">このレッスンでは、**データマイニングウィザード**を使用して、対象となるメーリングの構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="6587e-107">In this lesson you will use the **Data Mining Wizard** to create the targeted mailing structure.</span></span> <span data-ttu-id="6587e-108">このレッスンを完了すると、1 つのマイニング モデルを含むマイニング構造を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6587e-108">After you complete the tasks in this lesson, you will have a mining structure with a single model.</span></span> <span data-ttu-id="6587e-109">構造の作成には多数の手順と重要な概念がかかわってくるため、構造の作成プロセスを次の 3 つの作業に分割しました。</span><span class="sxs-lookup"><span data-stu-id="6587e-109">Because there are many steps and important concepts involved in creating a structure, we have separated this process into the following three tasks:</span></span>  
  
 [<span data-ttu-id="6587e-110">「基本的なデータマイニングチュートリアル」 &#40;「対象のメーリングマイニングモデル構造の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="6587e-110">Creating a Targeted Mailing Mining Model Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="6587e-111">データ型とコンテンツの種類の指定 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="6587e-111">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="6587e-112">構造 &#40;基本的なデータマイニングチュートリアルのテストデータセットの指定&#41;</span><span class="sxs-lookup"><span data-stu-id="6587e-112">Specifying a Testing Data Set for the Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="6587e-113">このレッスンの最初の作業</span><span class="sxs-lookup"><span data-stu-id="6587e-113">First Task in Lesson</span></span>  
 [<span data-ttu-id="6587e-114">「基本的なデータマイニングチュートリアル」 &#40;「対象のメーリングマイニングモデル構造の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="6587e-114">Creating a Targeted Mailing Mining Model Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="6587e-115">前のレッスン</span><span class="sxs-lookup"><span data-stu-id="6587e-115">Previous Lesson</span></span>  
 [<span data-ttu-id="6587e-116">レッスン 1: Analysis Services データベースの準備 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="6587e-116">Lesson 1: Preparing the Analysis Services Database &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
  
## <a name="next--lesson"></a><span data-ttu-id="6587e-117">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="6587e-117">Next  Lesson</span></span>  
 [<span data-ttu-id="6587e-118">レッスン 3: モデルの追加と処理</span><span class="sxs-lookup"><span data-stu-id="6587e-118">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="6587e-119">参照</span><span class="sxs-lookup"><span data-stu-id="6587e-119">See Also</span></span>  
 <span data-ttu-id="6587e-120">[データマイニング構造 &#40;データマイニングウィザードの作成&#41;](../../2014/analysis-services/create-the-data-mining-structure-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="6587e-120">[Create the Data Mining Structure &#40;Data Mining Wizard&#41;](../../2014/analysis-services/create-the-data-mining-structure-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="6587e-121">Create a Relational Mining Structure</span><span class="sxs-lookup"><span data-stu-id="6587e-121">Create a Relational Mining Structure</span></span>](../../2014/analysis-services/data-mining/create-a-relational-mining-structure.md)  
  
  
