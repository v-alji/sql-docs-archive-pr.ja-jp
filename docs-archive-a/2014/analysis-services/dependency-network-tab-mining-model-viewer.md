---
title: '[依存関係ネットワーク] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.dependencynetwork.f1
ms.assetid: e58ce1b7-20d6-42cb-ade5-916da8471e09
author: minewiskan
ms.author: owend
ms.openlocfilehash: 94ce82524445ffb8999c671c736087362ef0adfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712614"
---
# <a name="dependency-network-tab-mining-model-viewer"></a><span data-ttu-id="48060-102">[依存関係ネットワーク] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="48060-102">Dependency Network Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="48060-103">**[依存関係ネットワーク]** タブでは、マイニング モデルに含まれるすべての属性のグラフィカル ビューが表示され、属性がどのように関連しているかが示されます。</span><span class="sxs-lookup"><span data-stu-id="48060-103">The **Dependency Net** tab provides a graphical view of all attributes that the mining model contains, and shows how the attributes are related.</span></span>  
  
 <span data-ttu-id="48060-104">**[依存関係ネットワーク]**  タブは、Naïve Bayes モデル、デシジョン ツリー モデル、アソシエーション モデルなどのさまざまな種類のマイニング モデルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="48060-104">The **Dependency Net**  tab is used for several types of mining models, including Naïve Bayes models, decision tree models, and association models.</span></span> <span data-ttu-id="48060-105">これらのモデルのコンテキストにおける **[依存関係ネットワーク]**  タブの内容の解釈方法については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48060-105">For more information about how to interpret the contents of the **Dependency Net**  tab in the context of these models, see the following links:</span></span>  
  
 [<span data-ttu-id="48060-106">Microsoft ツリー ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="48060-106">Browse a Model Using the Microsoft Tree Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
 [<span data-ttu-id="48060-107">Microsoft Naive Bayes ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="48060-107">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
 [<span data-ttu-id="48060-108">Microsoft アソシエーション ルール ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="48060-108">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a><span data-ttu-id="48060-109">Options</span><span class="sxs-lookup"><span data-stu-id="48060-109">Options</span></span>  
 <span data-ttu-id="48060-110">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="48060-110">**Refresh viewer content**</span></span>  
 <span data-ttu-id="48060-111">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="48060-111">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="48060-112">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="48060-112">**Mining Model**</span></span>  
 <span data-ttu-id="48060-113">現在のマイニング構造に含まれているマイニング モデルから、表示するものを選択します。</span><span class="sxs-lookup"><span data-stu-id="48060-113">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="48060-114">マイニング モデルがカスタム ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="48060-114">The mining model will open in a custom viewer.</span></span> <span data-ttu-id="48060-115">各モデルで使用されるカスタム ビューアーの種類は、モデルの作成時に使用したアルゴリズムによって決まります。</span><span class="sxs-lookup"><span data-stu-id="48060-115">The type of custom viewer that is used for each model is determined by the algorithm that you used to create the model.</span></span>  
  
 <span data-ttu-id="48060-116">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="48060-116">**Viewer**</span></span>  
 <span data-ttu-id="48060-117">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="48060-117">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="48060-118">モデルごとに、各マイニング モデル用に用意されているカスタム ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="48060-118">For each model, you can use either the custom viewer is provided for each mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="48060-119">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="48060-119">You can also use plug-in viewers if available.</span></span> <span data-ttu-id="48060-120">Microsoft コンテンツ ツリー ビューアーはすべてのモデルで使用でき、モデルの内容を HTML テーブルで表現します。</span><span class="sxs-lookup"><span data-stu-id="48060-120">The Microsoft Content Tree Viewer can be used with all models, and represents the model content in an HTML table.</span></span>  
  
 <span data-ttu-id="48060-121">**拡大**</span><span class="sxs-lookup"><span data-stu-id="48060-121">**Zoom In**</span></span>  
 <span data-ttu-id="48060-122">属性の詳細を見ることができるように、図を拡大します。</span><span class="sxs-lookup"><span data-stu-id="48060-122">Zoom in to the diagram, so that you can see the attributes in more detail.</span></span>  
  
 <span data-ttu-id="48060-123">**縮小**</span><span class="sxs-lookup"><span data-stu-id="48060-123">**Zoom Out**</span></span>  
 <span data-ttu-id="48060-124">多くの属性とリンクが表示されるように、図を拡大します。</span><span class="sxs-lookup"><span data-stu-id="48060-124">Zoom out from the diagram, so that you can see more attributes and the links between them.</span></span>  
  
 <span data-ttu-id="48060-125">**[グラフ ビューのコピー]**</span><span class="sxs-lookup"><span data-stu-id="48060-125">**Copy Graph View**</span></span>  
 <span data-ttu-id="48060-126">ダイアグラムで表示されている部分をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="48060-126">Copy the visible section of the diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="48060-127">**[グラフ全体のコピー]**</span><span class="sxs-lookup"><span data-stu-id="48060-127">**Copy Entire Graph**</span></span>  
 <span data-ttu-id="48060-128">ダイアグラム全体をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="48060-128">Copy the complete diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="48060-129">**リンク**</span><span class="sxs-lookup"><span data-stu-id="48060-129">**Links**</span></span>  
 <span data-ttu-id="48060-130">属性の右側のスライダーを調整することにより、ビューアーに表示するリンク (エッジ) とノードの数を調整します。</span><span class="sxs-lookup"><span data-stu-id="48060-130">Adjust how many links (edges) and nodes the viewer shows by adjusting the slider to the right of the attributes.</span></span> <span data-ttu-id="48060-131">スライダーを下方にドラッグするとしきい値が大きくなり、最も強いリンクだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48060-131">Dragging the slider bar down increases the threshold value, so that only the strongest links are shown.</span></span> <span data-ttu-id="48060-132">モデルの種類ごとに、グラフのリンクを表すために使用される値は多少異なります。</span><span class="sxs-lookup"><span data-stu-id="48060-132">For each model type, a slightly different value is used to represent the links in the graph:</span></span>  
  
-   <span data-ttu-id="48060-133">**デシジョン ツリー** モデルでは、エッジは接続の予測強度を表します。その一部は分割スコアによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="48060-133">In a **decision tree** model, the edges represent the predictive strength of the connection, determined partly by the split score.</span></span>  
  
-   <span data-ttu-id="48060-134">**Naïve Bayes** モデルでは、2 つのノード間のリンクは双方向です。つまり、ノード A がノード B を予測でき、逆も可能です。</span><span class="sxs-lookup"><span data-stu-id="48060-134">In a **Naïve Bayes** model, the links between two nodes can go either way: that is, node A can predict the node B, and vice versa.</span></span> <span data-ttu-id="48060-135">エッジに関連付けられているスコアは、接続の予測強度を表します。</span><span class="sxs-lookup"><span data-stu-id="48060-135">The score associated with the edge represents the predictive strength of the connection.</span></span>  
  
-   <span data-ttu-id="48060-136">**アソシエーション モデル**では、ノード間のエッジは、2 つのアイテムセットを接続するルールの重要度スコアを表します。</span><span class="sxs-lookup"><span data-stu-id="48060-136">In an **association model**, the edges between nodes represent the importance score of the rule that connects two itemsets.</span></span>  
  
 <span data-ttu-id="48060-137">すべてのモデルに適用される一般的なルールとして、リンクが強ければ強いほど、2 つの属性間の予測関係も強くなります。</span><span class="sxs-lookup"><span data-stu-id="48060-137">A general rule for all model types is that the stronger the link, the stronger the predictive relationship between the two attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48060-138">参照</span><span class="sxs-lookup"><span data-stu-id="48060-138">See Also</span></span>  
 <span data-ttu-id="48060-139">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="48060-139">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="48060-140">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="48060-140">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="48060-141">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="48060-141">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
