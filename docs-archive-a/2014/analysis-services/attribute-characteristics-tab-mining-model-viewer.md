---
title: '[属性の特性] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
ms.openlocfilehash: b29ba482c21bb674a10bc4c9e6c6eccdf30905dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633634"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="648c9-102">[属性の特性] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="648c9-102">Attribute Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="648c9-103">Naïve Bayes モデルの結果と入力属性との関係を調べるには、 **[属性の特性]** ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="648c9-103">Use the **Attribute Characteristics** pane to explore the relationships between outcomes and input attributes in a Naïve Bayes model.</span></span> <span data-ttu-id="648c9-104">対象となる属性の値を選択した後、結果に対する影響が最も大きい入力属性の一覧を確認できます。</span><span class="sxs-lookup"><span data-stu-id="648c9-104">You can choose the value of the target attribute, and then see a list of the input attributes that have the strongest effect on the outcomes.</span></span>  
  
 <span data-ttu-id="648c9-105">**詳細:** [Microsoft Naive Bayes アルゴリズム](data-mining/microsoft-naive-bayes-algorithm.md)、 [Microsoft Naive Bayes ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="648c9-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="648c9-106">Options</span><span class="sxs-lookup"><span data-stu-id="648c9-106">Options</span></span>  
 <span data-ttu-id="648c9-107">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="648c9-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="648c9-108">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="648c9-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="648c9-109">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="648c9-109">**Mining Model**</span></span>  
 <span data-ttu-id="648c9-110">現在のマイニング構造に含まれているマイニング モデルから、表示するものを選択します。</span><span class="sxs-lookup"><span data-stu-id="648c9-110">Choose a mining model to view, from the models in the current mining structure.</span></span> <span data-ttu-id="648c9-111">選択した種類のマイニング モデルに最適のカスタム ビューアーが開いてモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="648c9-111">The mining model will automatically open in a custom viewer that is best for the particular type of model you chose.</span></span>  
  
 <span data-ttu-id="648c9-112">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="648c9-112">**Viewer**</span></span>  
 <span data-ttu-id="648c9-113">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="648c9-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="648c9-114">モデルごとに、カスタム ビューアーまたは [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="648c9-114">For each model, you have the choice of a custom viewer, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="648c9-115">利用可能な場合、プラグイン ビューアーもリストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="648c9-115">Plug-in viewers also appear in this list if available.</span></span>  
  
 <span data-ttu-id="648c9-116">**属性**</span><span class="sxs-lookup"><span data-stu-id="648c9-116">**Attribute**</span></span>  
 <span data-ttu-id="648c9-117">分析する予測可能な属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="648c9-117">Choose the predictable attribute that you want to analyze.</span></span>  
  
 <span data-ttu-id="648c9-118">**Value**</span><span class="sxs-lookup"><span data-stu-id="648c9-118">**Value**</span></span>  
 <span data-ttu-id="648c9-119">**[属性]** に設定する予測可能な属性の状態を選択します。</span><span class="sxs-lookup"><span data-stu-id="648c9-119">Choose a state for the predictable attribute that you set in **Attribute**.</span></span> <span data-ttu-id="648c9-120">Naive Bayes モデルは連続変数をサポートしないため、すべての対象となる属性は、不連続結果または分離された結果になります。</span><span class="sxs-lookup"><span data-stu-id="648c9-120">Because Naïve Bayes models do not support continuous variables, all target attributes have discrete or discretized outcomes.</span></span> <span data-ttu-id="648c9-121">不明属性は、常に自動的にリストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="648c9-121">The Missing attribute is always automatically added to the list.</span></span>  
  
 <span data-ttu-id="648c9-122">**の特性\<predictable state>**</span><span class="sxs-lookup"><span data-stu-id="648c9-122">**Characteristics for \<predictable state>**</span></span>  
 <span data-ttu-id="648c9-123">グラフには、入力属性の状態が、選択した予測可能な属性の状態とどのように関係するかを記述する次の列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="648c9-123">The graph contains the following columns, which describe how states of the input attributes are related to the selected predictable attribute state.</span></span>  
  
|<span data-ttu-id="648c9-124">値</span><span class="sxs-lookup"><span data-stu-id="648c9-124">Value</span></span>|<span data-ttu-id="648c9-125">説明</span><span class="sxs-lookup"><span data-stu-id="648c9-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="648c9-126">**変数**</span><span class="sxs-lookup"><span data-stu-id="648c9-126">**Variable**</span></span>|<span data-ttu-id="648c9-127">マイニング モデルの入力属性を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="648c9-127">Lists the input attributes in the mining model.</span></span>|  
|<span data-ttu-id="648c9-128">**値**</span><span class="sxs-lookup"><span data-stu-id="648c9-128">**Values**</span></span>|<span data-ttu-id="648c9-129">**[変数]** の入力属性の状態を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="648c9-129">Lists each state of the input attribute in **Variable**.</span></span>|  
|<span data-ttu-id="648c9-130">**確率**</span><span class="sxs-lookup"><span data-stu-id="648c9-130">**Probability**</span></span>|<span data-ttu-id="648c9-131">バーは、その行の属性と値が、予測可能な属性の選択した状態に関連付けられている確率を表します。</span><span class="sxs-lookup"><span data-stu-id="648c9-131">The bar represents the probability that the attribute and value in that row are associated with the selected state of the predictable attribute.</span></span> <span data-ttu-id="648c9-132">パーセントで表される確率を表示するには、バーの上にマウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="648c9-132">Hover the mouse over the bar to view the probability as a percentage.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="648c9-133">参照</span><span class="sxs-lookup"><span data-stu-id="648c9-133">See Also</span></span>  
 <span data-ttu-id="648c9-134">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="648c9-134">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="648c9-135">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="648c9-135">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="648c9-136">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="648c9-136">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
