---
title: '[属性の識別] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.discrimination.f1
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: a8b0d4bc99b1c8f1c5de0269312f02eeb09df022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633629"
---
# <a name="attribute-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="8cf84-102">[属性の識別] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="8cf84-102">Attribute Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="8cf84-103">入力属性の状態を比較して、それが結果属性とどのように関連しているかを確認するには、 **[属性の識別]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="8cf84-103">Use the **Attribute Discrimination** tab to compare the states of the input attributes and see how they are related to the outcome attribute.</span></span> <span data-ttu-id="8cf84-104">2 つの選択された予測可能属性の間で最も違いの大きい属性値が、一覧の先頭に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cf84-104">The attribute values that make the most difference between the two selected predictable attribute states are listed first.</span></span>  
  
 <span data-ttu-id="8cf84-105">**詳細:** [Microsoft Naive Bayes アルゴリズム](data-mining/microsoft-naive-bayes-algorithm.md)、 [Microsoft Naive Bayes ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="8cf84-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="8cf84-106">Options</span><span class="sxs-lookup"><span data-stu-id="8cf84-106">Options</span></span>  
 <span data-ttu-id="8cf84-107">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="8cf84-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="8cf84-108">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="8cf84-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="8cf84-109">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="8cf84-109">**Mining Model**</span></span>  
 <span data-ttu-id="8cf84-110">現在のマイニング構造に含まれているマイニング モデルから選択します。</span><span class="sxs-lookup"><span data-stu-id="8cf84-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="8cf84-111">マイニング モデルは、自動的に適切なカスタム ビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cf84-111">The mining model automatically opens in the correct custom viewer.</span></span>  
  
 <span data-ttu-id="8cf84-112">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="8cf84-112">**Viewer**</span></span>  
 <span data-ttu-id="8cf84-113">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="8cf84-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="8cf84-114">モデルごとに、カスタム ビューアーまたは [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーのいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8cf84-114">For each model, you can choose either the custom viewer, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="8cf84-115">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8cf84-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="8cf84-116">**属性**</span><span class="sxs-lookup"><span data-stu-id="8cf84-116">**Attribute**</span></span>  
 <span data-ttu-id="8cf84-117">予測可能な属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="8cf84-117">Choose a predictable attribute.</span></span>  
  
 <span data-ttu-id="8cf84-118">**値1**</span><span class="sxs-lookup"><span data-stu-id="8cf84-118">**Value 1**</span></span>  
 <span data-ttu-id="8cf84-119">**[値 2]** に指定された状態と比較する予測可能な属性の状態を選択します。</span><span class="sxs-lookup"><span data-stu-id="8cf84-119">Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.</span></span>  
  
 <span data-ttu-id="8cf84-120">**値2**</span><span class="sxs-lookup"><span data-stu-id="8cf84-120">**Value 2**</span></span>  
 <span data-ttu-id="8cf84-121">**[値 1]** に指定された状態と比較する予測可能な属性の状態を選択します。</span><span class="sxs-lookup"><span data-stu-id="8cf84-121">Select a state of the predictable attribute to compare to the state that is contained in **Value 1**.</span></span> <span data-ttu-id="8cf84-122">[**その他のすべての状態**] を選択して、**値 1**の値とその補数 (値1以外のすべての値) を比較することもできます。</span><span class="sxs-lookup"><span data-stu-id="8cf84-122">You can also select **All Other States** to compare the value in **Value 1** with its complement-that is, all other values except Value 1.</span></span>  
  
 <span data-ttu-id="8cf84-123">**との識別スコア \<Value 1>\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="8cf84-123">**Discrimination scores for \<Value 1> and \<Value 2>**</span></span>  
 <span data-ttu-id="8cf84-124">グラフには、対象となる属性が入力属性の特定の状態とどのように関係するかを記述する次の列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8cf84-124">The graph contains the following columns, which describe how the target attribute is related to specific states of the input attribute.</span></span>  
  
|<span data-ttu-id="8cf84-125">値</span><span class="sxs-lookup"><span data-stu-id="8cf84-125">Value</span></span>|<span data-ttu-id="8cf84-126">説明</span><span class="sxs-lookup"><span data-stu-id="8cf84-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cf84-127">**属性**</span><span class="sxs-lookup"><span data-stu-id="8cf84-127">**Attributes**</span></span>|<span data-ttu-id="8cf84-128">マイニング モデルの入力属性です。</span><span class="sxs-lookup"><span data-stu-id="8cf84-128">An input attribute in the mining model.</span></span>|  
|<span data-ttu-id="8cf84-129">**値**</span><span class="sxs-lookup"><span data-stu-id="8cf84-129">**Values**</span></span>|<span data-ttu-id="8cf84-130">**[属性]** に表示される属性の状態です。</span><span class="sxs-lookup"><span data-stu-id="8cf84-130">A state of the attribute that is listed in **Attributes**.</span></span>|  
|<span data-ttu-id="8cf84-131">**ライター\<Value 1>**</span><span class="sxs-lookup"><span data-stu-id="8cf84-131">**Favors \<Value 1>**</span></span>|<span data-ttu-id="8cf84-132">バーは、現在の属性と値が、**[値 1]** で選択した対象となる結果を優先するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8cf84-132">The bar indicates whether the current attribute and value favor the target outcome selected in **Value 1**.</span></span>|  
|<span data-ttu-id="8cf84-133">**ライター\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="8cf84-133">**Favors \<Value 2>**</span></span>|<span data-ttu-id="8cf84-134">バーは、現在の属性と値が、**[値 2]** で選択した対象となる結果を優先するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8cf84-134">The bar indicates whether the current attribute and value favor the target outcome selected in **Value 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cf84-135">参照</span><span class="sxs-lookup"><span data-stu-id="8cf84-135">See Also</span></span>  
 <span data-ttu-id="8cf84-136">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8cf84-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8cf84-137">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="8cf84-137">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="8cf84-138">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="8cf84-138">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
