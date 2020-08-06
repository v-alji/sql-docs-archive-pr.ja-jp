---
title: '[クラスターの特性] タブ (マイニングモデルビューアー)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 959d94767b6cb27d9ebb6e06c592034fca20ac89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633523"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="d4e84-102">[クラスターの特性] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="d4e84-102">Cluster Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="d4e84-103">**[クラスターの特性]** タブを使用して、クラスター モデル内のクラスター特性またはモデル内のすべてのケースのセットを調査できます。</span><span class="sxs-lookup"><span data-stu-id="d4e84-103">The **Cluster Characteristics** tab lets you explore the characteristics of a cluster in a clustering model, or the set of all cases in the model.</span></span> <span data-ttu-id="d4e84-104">クラスターを定義する特性としての各属性と値のペアの重要度が、他のクラスターと比較したグラフとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4e84-104">The graph shows the importance of each attribute-value pair as a characteristic that defines the cluster, in comparison with other clusters.</span></span>  
  
 <span data-ttu-id="d4e84-105">**詳細:** [Microsoft クラスター アルゴリズム](data-mining/microsoft-clustering-algorithm.md)、 [Microsoft クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="d4e84-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="d4e84-106">Options</span><span class="sxs-lookup"><span data-stu-id="d4e84-106">Options</span></span>  
 <span data-ttu-id="d4e84-107">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="d4e84-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="d4e84-108">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="d4e84-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="d4e84-109">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="d4e84-109">**Mining Model**</span></span>  
 <span data-ttu-id="d4e84-110">現在のマイニング構造に含まれているマイニング モデルから選択します。</span><span class="sxs-lookup"><span data-stu-id="d4e84-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="d4e84-111">マイニング モデルがカスタム ビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4e84-111">The mining model will open in the custom viewer.</span></span>  
  
 <span data-ttu-id="d4e84-112">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="d4e84-112">**Viewer**</span></span>  
 <span data-ttu-id="d4e84-113">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4e84-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="d4e84-114">モデルの種類に関連付けられたカスタム ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4e84-114">You can use the custom viewer associated with this model type, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="d4e84-115">利用可能な任意のプラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4e84-115">You can also use any plug-in viewers that are available.</span></span>  
  
 <span data-ttu-id="d4e84-116">**クラスター**</span><span class="sxs-lookup"><span data-stu-id="d4e84-116">**Cluster**</span></span>  
 <span data-ttu-id="d4e84-117">表示するクラスターを選択するか、**[母集団 (すべて)]** を選択して、全体としてのモデルの属性の分布を確認します。</span><span class="sxs-lookup"><span data-stu-id="d4e84-117">Choose the cluster you want to view, or choose **Population (All)** to see the distribution of attributes for the model as a whole.</span></span>  
  
 <span data-ttu-id="d4e84-118">**の特性\<cluster>**</span><span class="sxs-lookup"><span data-stu-id="d4e84-118">**Characteristics for \<cluster>**</span></span>  
 <span data-ttu-id="d4e84-119">選択したクラスターの特性を記述する次の列がグラフに含まれます。</span><span class="sxs-lookup"><span data-stu-id="d4e84-119">The graph contains the following columns, which describe the characteristics of the selected cluster.</span></span>  
  
|<span data-ttu-id="d4e84-120">値</span><span class="sxs-lookup"><span data-stu-id="d4e84-120">Value</span></span>|<span data-ttu-id="d4e84-121">説明</span><span class="sxs-lookup"><span data-stu-id="d4e84-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4e84-122">**変数**</span><span class="sxs-lookup"><span data-stu-id="d4e84-122">**Variable**</span></span>|<span data-ttu-id="d4e84-123">選択したクラスターで見つかったマイニング モデルの属性を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d4e84-123">Lists the attributes from the mining model that are found in the selected cluster.</span></span>|  
|<span data-ttu-id="d4e84-124">**値**</span><span class="sxs-lookup"><span data-stu-id="d4e84-124">**Values**</span></span>|<span data-ttu-id="d4e84-125">現在選択されているクラスターで見つかった現在の属性の値を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d4e84-125">Lists the values of the current attributes that are found in the currently selected cluster.</span></span>|  
|<span data-ttu-id="d4e84-126">**確率**</span><span class="sxs-lookup"><span data-stu-id="d4e84-126">**Probability**</span></span>|<span data-ttu-id="d4e84-127">属性と値のペアの強度が、クラスターの特徴としてバーで示されます。</span><span class="sxs-lookup"><span data-stu-id="d4e84-127">The bar indicates the strength of the attribute-value pair as a distinguishing feature of this cluster.</span></span> <span data-ttu-id="d4e84-128">バーの上にマウス ポインターを置くことで、パーセントで表現された確率値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d4e84-128">If you hover the mouse over the bar, you can see the probability value, represented as a percentage.</span></span> <span data-ttu-id="d4e84-129">この値は、この属性と値の組み合わせが特定のケースで発生する場合、そのようなケースがこのクラスターに属する確率がどの程度あるかを示します。</span><span class="sxs-lookup"><span data-stu-id="d4e84-129">What this indicates is, given this attribute and value combination in any particular case, what is the probability that the case would belong in this cluster.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4e84-130">参照</span><span class="sxs-lookup"><span data-stu-id="d4e84-130">See Also</span></span>  
 <span data-ttu-id="d4e84-131">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d4e84-131">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="d4e84-132">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="d4e84-132">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="d4e84-133">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="d4e84-133">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
