---
title: ニューラルネットワーク (マイニングモデルビューアー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.neuralnet.f1
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 39ca8d3cd9f2a327abd8558b13a018ceda27968d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639687"
---
# <a name="neural-network-mining-model-viewer"></a><span data-ttu-id="fdb24-102">ニューラル ネットワーク (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="fdb24-102">Neural Network (Mining Model Viewer)</span></span>
  <span data-ttu-id="fdb24-103">**ニューラル ネットワーク** ビューアーを使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムまたは [!INCLUDE[msCoName](../includes/msconame-md.md)] ロジスティック回帰アルゴリズムに基づくマイニング モデルを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="fdb24-103">Use the **Neural Net** viewer to explore mining models that are based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network algorithm or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="fdb24-104">**詳細:** [Microsoft ニューラル ネットワーク アルゴリズム](data-mining/microsoft-neural-network-algorithm.md)、 [Microsoft ロジスティック回帰アルゴリズム](data-mining/microsoft-logistic-regression-algorithm.md)、[Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="fdb24-104">**For More Information:** [Microsoft Neural Network Algorithm](data-mining/microsoft-neural-network-algorithm.md), [Microsoft Logistic Regression Algorithm](data-mining/microsoft-logistic-regression-algorithm.md),[Browse a Model Using the Microsoft Neural Network Viewer](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="fdb24-105">Options</span><span class="sxs-lookup"><span data-stu-id="fdb24-105">Options</span></span>  
 <span data-ttu-id="fdb24-106">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="fdb24-106">**Refresh viewer content**</span></span>  
 <span data-ttu-id="fdb24-107">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="fdb24-107">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="fdb24-108">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="fdb24-108">**Mining Model**</span></span>  
 <span data-ttu-id="fdb24-109">現在のマイニング構造に含まれているマイニング モデルから、表示するものを選択します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-109">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="fdb24-110">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdb24-110">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="fdb24-111">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="fdb24-111">**Viewer**</span></span>  
 <span data-ttu-id="fdb24-112">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-112">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="fdb24-113">カスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー ビューアー**を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fdb24-113">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="fdb24-114">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="fdb24-114">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="fdb24-115">**入力**</span><span class="sxs-lookup"><span data-stu-id="fdb24-115">**Input**</span></span>  
 <span data-ttu-id="fdb24-116">この領域で入力属性と値を選択します。選択した属性と値が結果にどのように影響するかを後で調べることができます。</span><span class="sxs-lookup"><span data-stu-id="fdb24-116">Use this area to choose input attributes and values, so that you can later explore how these affect the outcome.</span></span>  
  
|<span data-ttu-id="fdb24-117">値</span><span class="sxs-lookup"><span data-stu-id="fdb24-117">Value</span></span>|<span data-ttu-id="fdb24-118">説明</span><span class="sxs-lookup"><span data-stu-id="fdb24-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fdb24-119">**属性**</span><span class="sxs-lookup"><span data-stu-id="fdb24-119">**Attribute**</span></span>|<span data-ttu-id="fdb24-120">一覧から入力属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-120">Choose an input attribute from the list.</span></span> <span data-ttu-id="fdb24-121">選択範囲を既定値のままにした場合、 **\<All>** グラフには、予測可能な属性に対する影響によって順位付けされたすべての入力属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdb24-121">If you leave the selection as the default, **\<All>**, the chart shows a list of all input attributes, ranked by their impact on the predictable attribute.</span></span>|  
|<span data-ttu-id="fdb24-122">**Value**</span><span class="sxs-lookup"><span data-stu-id="fdb24-122">**Value**</span></span>|<span data-ttu-id="fdb24-123">入力属性の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-123">Choose a value for the input attribute.</span></span>|  
  
 <span data-ttu-id="fdb24-124">**出力**</span><span class="sxs-lookup"><span data-stu-id="fdb24-124">**Output**</span></span>  
 <span data-ttu-id="fdb24-125">分析して棒グラフで比較する予測可能な属性と値を選択するには、次のコントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-125">Use these controls to choose a predictable attribute and value to analyze and compare in the bar graph.</span></span> <span data-ttu-id="fdb24-126">選択を変更しなかった場合、棒グラフでは上位 2 つの結果状態を比較します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-126">If you do not change the selections, the bar graph compares the top two outcome states.</span></span>  
  
|<span data-ttu-id="fdb24-127">値</span><span class="sxs-lookup"><span data-stu-id="fdb24-127">Value</span></span>|<span data-ttu-id="fdb24-128">説明</span><span class="sxs-lookup"><span data-stu-id="fdb24-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fdb24-129">**[出力属性]**</span><span class="sxs-lookup"><span data-stu-id="fdb24-129">**Output Attribute**</span></span>|<span data-ttu-id="fdb24-130">予測可能な属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-130">Choose a predictable attribute.</span></span> <span data-ttu-id="fdb24-131">モデルの作成時に列を予測可能と定義しなかった場合、この時点でそれを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="fdb24-131">If you did not define the column as a predictable one when you created the model, you cannot add it here.</span></span>|  
|<span data-ttu-id="fdb24-132">**値1**</span><span class="sxs-lookup"><span data-stu-id="fdb24-132">**Value 1**</span></span>|<span data-ttu-id="fdb24-133">**[値 2]** に指定された状態と比較する予測可能な属性の状態を選択します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-133">Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.</span></span><br /><br /> <span data-ttu-id="fdb24-134">2 つの不連続値または分離された値を比較できます。ただし、他のビューでは可能な、値とその補数との比較は実行できません。</span><span class="sxs-lookup"><span data-stu-id="fdb24-134">You can compare any two discrete or discretized values; however, you cannot compare a value to its complement, as you can in other viewers.</span></span>|  
|<span data-ttu-id="fdb24-135">**値2**</span><span class="sxs-lookup"><span data-stu-id="fdb24-135">**Value 2**</span></span>|<span data-ttu-id="fdb24-136">**[値 1]** に指定された状態と比較する予測可能な属性の状態を選択します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-136">Select a state of the predictable attribute to compare to the state that is contained in **Value 1**.</span></span>|  
  
 <span data-ttu-id="fdb24-137">**変数**</span><span class="sxs-lookup"><span data-stu-id="fdb24-137">**Variables**</span></span>  
 <span data-ttu-id="fdb24-138">**[ニューラル ネットワーク]** タブのこの部分には、選択した入力属性と結果属性に応じて変化する対話型棒グラフが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fdb24-138">This part of the **Neural Network** tab contains an interactive bar graph, which responds to the selections that you made for input and outcome attributes.</span></span> <span data-ttu-id="fdb24-139">ニューラル ネットワークでは特定の値が特定の結果に与える影響の可能性が計算されるので、入力を自由に組み合わせて選択できます。棒グラフには、選択した組み合わせが比較中の結果のペアにどのように影響するかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdb24-139">Because a neural network calculates the likelihood that a particular value influences a particular outcome, you can choose any combination of inputs, and the bar chart will display how that combination affects the pair of outcomes that you are comparing.</span></span>  
  
|<span data-ttu-id="fdb24-140">値</span><span class="sxs-lookup"><span data-stu-id="fdb24-140">Value</span></span>|<span data-ttu-id="fdb24-141">説明</span><span class="sxs-lookup"><span data-stu-id="fdb24-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fdb24-142">**属性**</span><span class="sxs-lookup"><span data-stu-id="fdb24-142">**Attribute**</span></span>|<span data-ttu-id="fdb24-143">**[属性]** で選択した入力属性の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-143">Shows the name of the input attribute you selected in **Attribute**.</span></span>|  
|<span data-ttu-id="fdb24-144">**Value**</span><span class="sxs-lookup"><span data-stu-id="fdb24-144">**Value**</span></span>|<span data-ttu-id="fdb24-145">選択した入力属性の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-145">Shows the value for the selected input attribute.</span></span>|  
|<span data-ttu-id="fdb24-146">**ライター\<Value 1>**</span><span class="sxs-lookup"><span data-stu-id="fdb24-146">**Favors \<Value 1>**</span></span>|<span data-ttu-id="fdb24-147">選択した属性と値の組み合わせが **[値 1]** で選択した対象となる結果にどの程度影響しているかを示す棒を表示します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-147">Displays a bar that indicates how much this particular attribute-value combination affects the target outcome chosen in **Value 1**.</span></span>|  
|<span data-ttu-id="fdb24-148">**ライター\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="fdb24-148">**Favors \<Value 2>**</span></span>|<span data-ttu-id="fdb24-149">選択した属性と値の組み合わせが **[値 2]** で選択した対象となる結果にどの程度影響しているかを示す棒を表示します。</span><span class="sxs-lookup"><span data-stu-id="fdb24-149">Displays a bar that indicates how much this particular attribute-value combination affects the target outcome chosen in **Value 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdb24-150">参照</span><span class="sxs-lookup"><span data-stu-id="fdb24-150">See Also</span></span>  
 <span data-ttu-id="fdb24-151">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="fdb24-151">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="fdb24-152">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="fdb24-152">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="fdb24-153">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="fdb24-153">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
