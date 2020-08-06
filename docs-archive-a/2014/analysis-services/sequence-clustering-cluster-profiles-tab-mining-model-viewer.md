---
title: シーケンスクラスターの [クラスターのプロファイル] タブ (マイニングモデルビューアー)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.profiles.f1
ms.assetid: 44230895-0a42-4032-8d6c-0cdb8a2dbb8c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5d5746b1fbee6571af1d2321eec01c099d8dd0ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743518"
---
# <a name="sequence-clustering-cluster-profiles-tab-mining-model-viewer"></a><span data-ttu-id="aefc5-102">シーケンス クラスターの [クラスターのプロファイル] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="aefc5-102">Sequence Clustering Cluster Profiles Tab (Mining Model Viewer</span></span>
  <span data-ttu-id="aefc5-103">**Microsoft シーケンス クラスター ビューアー** の **[クラスターのプロファイル]** タブでは、各クラスターに含まれるシーケンスの色分けされたビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-103">The **Cluster Profiles** tab in the **Microsoft Sequence Clustering Viewer** provides a color-coded view of sequences that are included in each cluster.</span></span>  
  
 <span data-ttu-id="aefc5-104">モデルによって検出されたシーケンスがどのようにグループ化されるかを簡単に確認するには、シーケンス クラスター モデルのこのビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="aefc5-104">Use this view of a sequence clustering model to get a quick view of how the sequences found by the model are grouped.</span></span> <span data-ttu-id="aefc5-105">長いシーケンスと短いシーケンスをひとめで確認できます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-105">You can see at a glance how many sequences are long and how many are short.</span></span> <span data-ttu-id="aefc5-106">クラスターをクリックして **[マイニング凡例]** を表示することで、各シーケンスの色が表している状態を正確に知ることもできます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-106">You can also click a cluster and display the **Mining Legend** to see exactly which states the colors in each sequence represent.</span></span>  
  
 <span data-ttu-id="aefc5-107">**詳細:**  [Microsoft シーケンス クラスター アルゴリズム](data-mining/microsoft-sequence-clustering-algorithm.md)、 [Microsoft シーケンス クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="aefc5-107">**For More Information:**  [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="aefc5-108">Options</span><span class="sxs-lookup"><span data-stu-id="aefc5-108">Options</span></span>  
 <span data-ttu-id="aefc5-109">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="aefc5-109">**Refresh viewer content**</span></span>  
 <span data-ttu-id="aefc5-110">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="aefc5-110">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="aefc5-111">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="aefc5-111">**Mining Model**</span></span>  
 <span data-ttu-id="aefc5-112">現在のマイニング構造に含まれているマイニング モデルから、表示するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="aefc5-112">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="aefc5-113">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-113">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="aefc5-114">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="aefc5-114">**Viewer**</span></span>  
 <span data-ttu-id="aefc5-115">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="aefc5-115">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="aefc5-116">カスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー ビューアー**を使用できます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-116">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="aefc5-117">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-117">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="aefc5-118">**[凡例の表示]**</span><span class="sxs-lookup"><span data-stu-id="aefc5-118">**Show Legend**</span></span>  
 <span data-ttu-id="aefc5-119">クラスターのプロファイルに表示されている色と状態のテキスト値との相関関係を示す凡例を表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="aefc5-119">Select this option to display a legend that shows the correlation between the colors displayed in the cluster profiles and the text values of the states.</span></span>  
  
 <span data-ttu-id="aefc5-120">**[ヒストグラム バー]**</span><span class="sxs-lookup"><span data-stu-id="aefc5-120">**Histogram Bars**</span></span>  
 <span data-ttu-id="aefc5-121">ヒストグラムに表示される色分けされたバーの数を変更するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="aefc5-121">Use this option to change the number of colored bars that are included in the histogram.</span></span> <span data-ttu-id="aefc5-122">選択したバーの数よりも多くのバーが存在する場合、重要度が最も高いバーが保持され、それ以外のバーは **[その他]** にまとめられます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-122">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into the **Other**.</span></span>  
  
 <span data-ttu-id="aefc5-123">**属性** と **クラスターのプロファイル**</span><span class="sxs-lookup"><span data-stu-id="aefc5-123">**Attributes** and **Cluster Profiles**</span></span>  
 <span data-ttu-id="aefc5-124">グラフのこのセクションには、モデル内で検出されたシーケンスのクラスターが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-124">This section of the graph chart lists the clusters of sequences that were found in the model.</span></span>  
  
 <span data-ttu-id="aefc5-125">各シーケンス クラスターは、 **[ヒストグラム バー]** オプションで選択した数の状態を使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-125">Each sequence cluster is displayed using the number of states you selected in the option, **Histogram bars**.</span></span>  
  
 <span data-ttu-id="aefc5-126">モデルのクラスターごとに 2 セットのヒストグラムが表示されます。各セットはグラフの異なる行を対象とします。</span><span class="sxs-lookup"><span data-stu-id="aefc5-126">Two sets of histograms are displayed for each cluster in the model, each on a different row in the graph:</span></span>  
  
-   <span data-ttu-id="aefc5-127">\*\* \<attribute name> サンプル\*\*: この行のヒストグラムは、各クラスターの代表となる項目のシーケンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="aefc5-127">**\<attribute name>.samples**: The histograms in this row show the sequences of items that are representative of each cluster.</span></span> <span data-ttu-id="aefc5-128">DMX 用語では、これらは各クラスターのサンプル ケースです。</span><span class="sxs-lookup"><span data-stu-id="aefc5-128">In DMX terms, these are the sample cases for each cluster.</span></span>  
  
-   <span data-ttu-id="aefc5-129">**\<attribute name>**: この行のヒストグラムは、クラスターに含まれるすべての項目とその全体的な分布を表します。</span><span class="sxs-lookup"><span data-stu-id="aefc5-129">**\<attribute name>**: The histograms in this row describe all the items that the cluster contains and their overall distribution.</span></span> <span data-ttu-id="aefc5-130">**[マイニング凡例]** が表示されているときにヒストグラムをクリックすると、それぞれの数値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-130">Click a histogram when the **Mining Legend** is visible and you can see the numeric values for each</span></span>  
  
 <span data-ttu-id="aefc5-131">**状態**</span><span class="sxs-lookup"><span data-stu-id="aefc5-131">**States**</span></span>  
 <span data-ttu-id="aefc5-132">グラフのこの列はオプションです。 **[凡例の表示]** をクリックすることで、表示または削除できます。</span><span class="sxs-lookup"><span data-stu-id="aefc5-132">This column in the chart is optional, and can be displayed or removed by selecting the **Show Legend** option.</span></span> <span data-ttu-id="aefc5-133">**[状態]** 列は、どの状態が対応するクラスターのヒストグラム内のどの色で表現されているかを示すガイドとなります。</span><span class="sxs-lookup"><span data-stu-id="aefc5-133">The **States** column provides a guide as to which state is represented by which color in the corresponding clusters histogram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefc5-134">参照</span><span class="sxs-lookup"><span data-stu-id="aefc5-134">See Also</span></span>  
 <span data-ttu-id="aefc5-135">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="aefc5-135">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="aefc5-136">[Microsoft シーケンスクラスターアルゴリズム](data-mining/microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="aefc5-136">[Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="aefc5-137">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="aefc5-137">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 <span data-ttu-id="aefc5-138">[データマイニングモデルビューアー](data-mining/data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="aefc5-138">[Data Mining Model Viewers](data-mining/data-mining-model-viewers.md) </span></span>  
 [<span data-ttu-id="aefc5-139">Microsoft シーケンス クラスター ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="aefc5-139">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
  
