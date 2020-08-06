---
title: シーケンスクラスターの [クラスターの切り替え] タブ (マイニングモデルビューアー)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.transition.f1
ms.assetid: 40aef457-d69f-4905-a2d3-924c37bd3d97
author: minewiskan
ms.author: owend
ms.openlocfilehash: f777e48c2f69911e61420fd3b7a0a137a04e7c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743517"
---
# <a name="sequence-clustering-cluster-transition-tab-mining-model-viewer"></a><span data-ttu-id="e9c05-102">シーケンス クラスターの [状態遷移] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="e9c05-102">Sequence Clustering Cluster Transition Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="e9c05-103">**Microsoft シーケンス クラスター ビューアー** の **[状態遷移]** タブでは、選択したクラスターにおける属性と値のペア間または状態間の遷移を詳細に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="e9c05-103">The **State Transitions** tab in the **Microsoft Sequence Clustering Viewer** provides a closer look at the transitions between attribute-value pairs, or states, in the selected cluster.</span></span>  
  
 <span data-ttu-id="e9c05-104">パターンを表示するには、シーケンス クラスタリング モデルのこのビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-104">Use this view of a sequence clustering model to view patterns.</span></span> <span data-ttu-id="e9c05-105">ダイアグラム内のリンクは遷移の確率を表し、ノードはシーケンスの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-105">In the diagram, a link represents the probability of a transition, and a node represents a sequence state.</span></span>  
  
 <span data-ttu-id="e9c05-106">**詳細:** [Microsoft シーケンス クラスター アルゴリズム](data-mining/microsoft-sequence-clustering-algorithm.md)、 [Microsoft シーケンス クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="e9c05-106">**For More Information:** [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="e9c05-107">Options</span><span class="sxs-lookup"><span data-stu-id="e9c05-107">Options</span></span>  
 <span data-ttu-id="e9c05-108">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="e9c05-108">**Refresh viewer content**</span></span>  
 <span data-ttu-id="e9c05-109">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="e9c05-109">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="e9c05-110">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="e9c05-110">**Mining Model**</span></span>  
 <span data-ttu-id="e9c05-111">現在のマイニング構造に含まれているマイニング モデルから、表示するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-111">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="e9c05-112">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9c05-112">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="e9c05-113">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="e9c05-113">**Viewer**</span></span>  
 <span data-ttu-id="e9c05-114">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-114">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="e9c05-115">カスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー ビューアー**を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9c05-115">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="e9c05-116">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e9c05-116">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="e9c05-117">**拡大**</span><span class="sxs-lookup"><span data-stu-id="e9c05-117">**Zoom In**</span></span>  
 <span data-ttu-id="e9c05-118">ダイアグラムをズーム アウトして、状態を詳しく表示します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-118">Zoom in to the diagram, to see the states better.</span></span>  
  
 <span data-ttu-id="e9c05-119">**縮小**</span><span class="sxs-lookup"><span data-stu-id="e9c05-119">**Zoom Out**</span></span>  
 <span data-ttu-id="e9c05-120">ダイアグラムを縮小して、クラスター内の状態の全体的なビューを取得します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-120">Zoom out from the diagram, to get an overall view of the states in the cluster.</span></span>  
  
 <span data-ttu-id="e9c05-121">**[グラフ ビューのコピー]**</span><span class="sxs-lookup"><span data-stu-id="e9c05-121">**Copy Graph View**</span></span>  
 <span data-ttu-id="e9c05-122">ダイアグラムで表示されている部分をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e9c05-122">Copy the visible section of the diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="e9c05-123">**[グラフ全体のコピー]**</span><span class="sxs-lookup"><span data-stu-id="e9c05-123">**Copy Entire Graph**</span></span>  
 <span data-ttu-id="e9c05-124">ダイアグラム全体をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e9c05-124">Copy the complete diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="e9c05-125">**クラスター**</span><span class="sxs-lookup"><span data-stu-id="e9c05-125">**Cluster**</span></span>  
 <span data-ttu-id="e9c05-126">ビューアーに表示するクラスターを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-126">Choose a cluster to display in the viewer.</span></span> <span data-ttu-id="e9c05-127">既定値として **[母集団 (すべて)]** が選択されています。これは、モデル全体の状態と遷移がグラフに含まれることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-127">By default, **Population (All)** is selected, which means that states and transitions from the entire model are included in the graph.</span></span> <span data-ttu-id="e9c05-128">特定のクラスターを選択すると、選択したクラスターに含まれる状態と遷移だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9c05-128">When you choose a particular cluster, only the states and transitions that are in that cluster are displayed.</span></span>  
  
 <span data-ttu-id="e9c05-129">**ヒント:** クラスターの名前を変更するには、[**クラスターダイアグラム**] タブを使用します。クラスターを選択し、右クリックして、[**名前の変更**] を選択するだけです。</span><span class="sxs-lookup"><span data-stu-id="e9c05-129">**Tip:** You can rename clusters by using the **Cluster Diagram** tab. Just select a cluster, right-click, and select **Rename**.</span></span> <span data-ttu-id="e9c05-130">クラスターをわかりやすい名前に変更すると、 **[状態遷移]** タブでクラスターを簡単に比較できます。</span><span class="sxs-lookup"><span data-stu-id="e9c05-130">Renaming clusters with a more descriptive label makes it easier to compare clusters in the **State Transitions** tab.</span></span>  
  
 <span data-ttu-id="e9c05-131">**[線のラベルを表示する]**</span><span class="sxs-lookup"><span data-stu-id="e9c05-131">**Show Edge Labels**</span></span>  
 <span data-ttu-id="e9c05-132">遷移の確率を示すグラフに各エッジの番号を表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-132">Select this option to display numbers on each edge in the graph that denote the probability of the transition.</span></span>  
  
 <span data-ttu-id="e9c05-133">**リンク**</span><span class="sxs-lookup"><span data-stu-id="e9c05-133">**Links**</span></span>  
 <span data-ttu-id="e9c05-134">スライダーを使用して、グラフに表示される状態と遷移の数を制御します。</span><span class="sxs-lookup"><span data-stu-id="e9c05-134">Use the slider to control the number of states and transitions that are displayed in the chart.</span></span> <span data-ttu-id="e9c05-135">スライダーを下に移動すると、確率が最も高い状態と遷移だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9c05-135">Lowering the slider shows only the states and transitions with the highest probability.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c05-136">参照</span><span class="sxs-lookup"><span data-stu-id="e9c05-136">See Also</span></span>  
 <span data-ttu-id="e9c05-137">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e9c05-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e9c05-138">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e9c05-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="e9c05-139">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="e9c05-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
