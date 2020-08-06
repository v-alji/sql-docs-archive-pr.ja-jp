---
title: 絞り込みメール配信構造への新しいモデルの追加 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b83dfc6c9e218eecf3f2abe636b8c24d69d1b507
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720541"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="8c162-102">絞り込みメール配信構造への新しいモデルの追加 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="8c162-102">Adding New Models to the Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="8c162-103">このタスクでは、データマイニングデザイナーの [**マイニングモデル**] タブを使用して、2つの追加のモデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="8c162-103">In this task, you will define two additional models by using the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="8c162-104">モデルの作成には、Microsoft クラスタリング アルゴリズムと Microsoft Naive Bayes アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c162-104">You will use the Microsoft Clustering and Microsoft Naive Bayes algorithms to create the models.</span></span> <span data-ttu-id="8c162-105">この 2 つのアルゴリズムを選択する理由は、不連続値 (自転車の購入) を予測できるためです。</span><span class="sxs-lookup"><span data-stu-id="8c162-105">These two algorithms are selected because of their ability to predict a discrete value (i.e., bike purchase).</span></span> <span data-ttu-id="8c162-106">これらのアルゴリズムの詳細については、「 [Microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)」と「 [Microsoft Naive Bayes algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c162-106">For more information about these algorithms, see [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) and [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)</span></span>  
  
### <a name="to-create-a-clustering-mining-model"></a><span data-ttu-id="8c162-107">クラスター マイニング モデルを作成するには</span><span class="sxs-lookup"><span data-stu-id="8c162-107">To create a clustering mining model</span></span>  
  
1.  <span data-ttu-id="8c162-108">のデータマイニングデザイナーで [**マイニングモデル**] タブに切り替え [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8c162-108">Switch to the **Mining Models** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="8c162-109">デザイナーには、マイニング構造用と、 `TM_Decision_Tree` 前のレッスンで作成したマイニングモデル用の2つの列が表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8c162-109">Notice that the designer displays two columns, one for the mining structure and one for the `TM_Decision_Tree` mining model, which you created in the previous lesson.</span></span>  
  
2.  <span data-ttu-id="8c162-110">[**構造**] 列を右クリックし、[**新しいマイニングモデル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c162-110">Right-click the **Structure** column and select **New Mining Model**.</span></span>  
  
3.  <span data-ttu-id="8c162-111">[**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に「」と入力 `TM_Clustering` します。</span><span class="sxs-lookup"><span data-stu-id="8c162-111">In the **New Mining Model** dialog box, in **Model name**, type `TM_Clustering`.</span></span>  
  
4.  <span data-ttu-id="8c162-112">[**アルゴリズム名**] で、[ **Microsoft クラスタリング**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c162-112">In **Algorithm name**, select **Microsoft Clustering**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="8c162-113">データマイニングデザイナーの [**マイニングモデル**] タブに新しいモデルが表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8c162-113">The new model now appears in the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="8c162-114">クラスタリングアルゴリズムを使用して構築されたこのモデルで [!INCLUDE[msCoName](../includes/msconame-md.md)] は、類似した特性を持つ顧客をクラスターにグループ化し、各クラスターの自転車の購入を予測します。</span><span class="sxs-lookup"><span data-stu-id="8c162-114">This model, built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm, groups customers with similar characteristics into clusters and predicts bike buying for each cluster.</span></span> <span data-ttu-id="8c162-115">新しいモデルの列の使用法とプロパティを変更することはできますが、 `TM_Clustering` このチュートリアルではモデルを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8c162-115">Although you can modify the column usage and properties for the new model, no changes to the `TM_Clustering` model are necessary for this tutorial.</span></span>  
  
### <a name="to-create-a-naive-bayes-mining-model"></a><span data-ttu-id="8c162-116">Naive Bayes マイニング モデルを作成するには</span><span class="sxs-lookup"><span data-stu-id="8c162-116">To create a Naive Bayes mining model</span></span>  
  
1.  <span data-ttu-id="8c162-117">データマイニングデザイナーの [**マイニングモデル**] タブで、[**構造**列] を右クリックし、[**新しいマイニングモデル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c162-117">In the **Mining Models** tab of Data Mining Designer, right-clickthe **Structure** column, and select **New Mining Model**.</span></span>  
  
2.  <span data-ttu-id="8c162-118">[**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に「」と入力 `TM_NaiveBayes` します。</span><span class="sxs-lookup"><span data-stu-id="8c162-118">In the **New Mining Model** dialog box, under **Model name**, type `TM_NaiveBayes`.</span></span>  
  
3.  <span data-ttu-id="8c162-119">[**アルゴリズム名**] で [ **Microsoft Naive Bayes**] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c162-119">In **Algorithm name**, select **Microsoft Naive Bayes**, then click **OK**.</span></span>  
  
     <span data-ttu-id="8c162-120">[!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes アルゴリズムでは、継続している**Age**と**年収**の列がサポートされていないことを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c162-120">A message appears stating that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm does not support the **Age** and **Yearly Income** columns, which are continuous.</span></span>  
  
4.  <span data-ttu-id="8c162-121">[**はい**] をクリックしてメッセージを確認し、続行します。</span><span class="sxs-lookup"><span data-stu-id="8c162-121">Click **Yes** to acknowledge the message and continue.</span></span>  
  
 <span data-ttu-id="8c162-122">データマイニングデザイナーの [**マイニングモデル**] タブに新しいモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c162-122">A new model appears in the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="8c162-123">このタブでは、すべてのモデルの列の使用法とプロパティを変更できますが、このチュートリアルではモデルを変更する必要はありません `TM_NaiveBayes` 。</span><span class="sxs-lookup"><span data-stu-id="8c162-123">Although you can modify the column usage and properties for all the models in this tab, no changes to the `TM_NaiveBayes` model are necessary for this tutorial.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8c162-124">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="8c162-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8c162-125">「&#40;基本的なデータマイニングチュートリアル」では、対象となるメーリングの構造でのモデルの処理&#41;</span><span class="sxs-lookup"><span data-stu-id="8c162-125">Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c162-126">参照</span><span class="sxs-lookup"><span data-stu-id="8c162-126">See Also</span></span>  
 <span data-ttu-id="8c162-127">[Analysis Services データマイニング &#40;構造へのマイニングモデルの追加&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8c162-127">[Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8c162-128">[データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="8c162-128">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="8c162-129">データ マイニング オブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="8c162-129">Moving Data Mining Objects</span></span>](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  
