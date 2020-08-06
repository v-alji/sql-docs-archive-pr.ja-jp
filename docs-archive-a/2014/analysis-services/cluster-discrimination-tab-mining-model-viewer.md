---
title: '[クラスターの識別] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.discrimination.f1
ms.assetid: ae7cfff7-ab1c-4cf5-9a91-97b21d15d85f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 35435736bcdf1b1962de6babace2def953bbfff0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634147"
---
# <a name="cluster-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="6bec3-102">[クラスターの識別] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="6bec3-102">Cluster Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="6bec3-103">**[クラスターの識別]** タブを使用すると、クラスター モデルに存在する 2 つのクラスターを比較できます。</span><span class="sxs-lookup"><span data-stu-id="6bec3-103">Use the **Cluster Discrimination** tab to compare two clusters that exist in a clustering model.</span></span> <span data-ttu-id="6bec3-104">異なる属性と値の組み合わせが、クラスター内でどのように表されているかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6bec3-104">You can see how different combinations of attributes and values are represented within the clusters.</span></span>  
  
 <span data-ttu-id="6bec3-105">**詳細:** [Microsoft クラスター アルゴリズム](data-mining/microsoft-clustering-algorithm.md)、 [Microsoft クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="6bec3-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="6bec3-106">Options</span><span class="sxs-lookup"><span data-stu-id="6bec3-106">Options</span></span>  
 <span data-ttu-id="6bec3-107">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="6bec3-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="6bec3-108">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="6bec3-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="6bec3-109">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="6bec3-109">**Mining Model**</span></span>  
 <span data-ttu-id="6bec3-110">現在のマイニング構造に含まれているマイニング モデルから選択します。</span><span class="sxs-lookup"><span data-stu-id="6bec3-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="6bec3-111">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bec3-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="6bec3-112">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="6bec3-112">**Viewer**</span></span>  
 <span data-ttu-id="6bec3-113">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="6bec3-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="6bec3-114">クラスター モデル用のカスタム ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bec3-114">You can use the custom viewer for clustering models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="6bec3-115">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6bec3-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="6bec3-116">**クラスター 1**</span><span class="sxs-lookup"><span data-stu-id="6bec3-116">**Cluster 1**</span></span>  
 <span data-ttu-id="6bec3-117">クラスターを選択して、別のクラスターと比較できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6bec3-117">Select a cluster, so that you can compare it to another cluster.</span></span>  
  
 <span data-ttu-id="6bec3-118">**Cluster 2**</span><span class="sxs-lookup"><span data-stu-id="6bec3-118">**Cluster 2**</span></span>  
 <span data-ttu-id="6bec3-119">**[クラスター 1]** と比較するために、マイニング モデルのクラスター リストから別のクラスターを選択します。</span><span class="sxs-lookup"><span data-stu-id="6bec3-119">Select a second cluster from the list of clusters in the mining model, to compare to **Cluster 1**.</span></span> <span data-ttu-id="6bec3-120">クラスターは、その補集合 (選択したクラスター内のケースを除くモデル内のすべてのケース) と比較することもできます。</span><span class="sxs-lookup"><span data-stu-id="6bec3-120">You can also compare a cluster to its complement, meaning all cases in the model except those in the selected cluster.</span></span>  
  
 <span data-ttu-id="6bec3-121">**との識別スコア \<cluster 1>\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="6bec3-121">**Discrimination scores for \<cluster 1> and \<cluster 2>**</span></span>  
 <span data-ttu-id="6bec3-122">グラフの列は、選択した 2 つのクラスターに対して属性と値の各ペアがどのように関係しているかに関する情報を示します。</span><span class="sxs-lookup"><span data-stu-id="6bec3-122">The columns in the graph provide information about how each attribute-value pair is related to the two selected clusters.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6bec3-123">**変数**</span><span class="sxs-lookup"><span data-stu-id="6bec3-123">**Variables**</span></span>|<span data-ttu-id="6bec3-124">マイニング モデルの属性です。</span><span class="sxs-lookup"><span data-stu-id="6bec3-124">An attribute in the mining model.</span></span>|  
|<span data-ttu-id="6bec3-125">**値**</span><span class="sxs-lookup"><span data-stu-id="6bec3-125">**Values**</span></span>|<span data-ttu-id="6bec3-126">**[変数]** で選択された属性の値。</span><span class="sxs-lookup"><span data-stu-id="6bec3-126">A value of the attribute selected in **Variables**.</span></span>|  
|<span data-ttu-id="6bec3-127">**ライター\<cluster 1>**</span><span class="sxs-lookup"><span data-stu-id="6bec3-127">**Favors \<cluster 1>**</span></span>|<span data-ttu-id="6bec3-128">左側の棒グラフは、選択した属性と値のペアが、**[クラスター 1]** で選択したクラスターの代表である確率を表します。</span><span class="sxs-lookup"><span data-stu-id="6bec3-128">The bar graph on the left represents the probability that the selected attribute-value pair is representative of the cluster selected in **Cluster 1**.</span></span> <span data-ttu-id="6bec3-129">バーの上にマウス ポインターを置くことで、パーセントで表現された値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6bec3-129">You can pause the mouse over the bar to see the value, represented as a percentage.</span></span> <span data-ttu-id="6bec3-130">値がゼロの場合でも、属性値がクラスターに存在しないことを意味するわけではありません。つまり、分散によって1つのクラスターが互いに優先されるというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="6bec3-130">Note that even if the value is zero, it doesn't mean the attribute-value is necessarily missing from the cluster, just that the distribution strongly favors one cluster over the other.</span></span>|  
|<span data-ttu-id="6bec3-131">**ライター\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="6bec3-131">**Favors \<cluster 2>**</span></span>|<span data-ttu-id="6bec3-132">右側の棒グラフは、選択した属性と値のペアが、**[クラスター 2]** で選択したクラスターの代表である確率を表します。</span><span class="sxs-lookup"><span data-stu-id="6bec3-132">The bar graph on the right represents the probability that the selected attribute-value pair is representative of the cluster selected in **Cluster 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bec3-133">参照</span><span class="sxs-lookup"><span data-stu-id="6bec3-133">See Also</span></span>  
 <span data-ttu-id="6bec3-134">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="6bec3-134">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="6bec3-135">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="6bec3-135">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="6bec3-136">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="6bec3-136">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
