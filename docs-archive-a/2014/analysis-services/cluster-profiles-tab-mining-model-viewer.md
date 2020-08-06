---
title: '[クラスターのプロファイル] タブ (マイニングモデルビューアー)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.profiles.f1
ms.assetid: 1ebafa1f-74e9-4c05-b278-a690fa8543bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7ec1ce5b5204ae81a9313ca7b7e5df58c98c5da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634143"
---
# <a name="cluster-profiles-tab-mining-model-viewer"></a><span data-ttu-id="80785-102">[クラスターのプロファイル] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="80785-102">Cluster Profiles Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="80785-103">**[クラスターのプロファイル]** タブを使用すると、アルゴリズムによってクラスター モデル内で検出されたクラスターの概要を表示できます。</span><span class="sxs-lookup"><span data-stu-id="80785-103">Use the **Cluster Profiles** tab for an overall view of the clusters that the algorithm discovered within a clustering model.</span></span> <span data-ttu-id="80785-104">タブには、各クラスターの属性と、その属性の分布が表示されます。</span><span class="sxs-lookup"><span data-stu-id="80785-104">The tab displays each attribute, together with the distribution of the attribute in each cluster.</span></span>  
  
 <span data-ttu-id="80785-105">**詳細:** [Microsoft クラスター アルゴリズム](data-mining/microsoft-clustering-algorithm.md)、 [Microsoft クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="80785-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="80785-106">Options</span><span class="sxs-lookup"><span data-stu-id="80785-106">Options</span></span>  
 <span data-ttu-id="80785-107">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="80785-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="80785-108">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="80785-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="80785-109">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="80785-109">**Mining Model**</span></span>  
 <span data-ttu-id="80785-110">現在のマイニング構造に含まれているマイニング モデルから選択します。</span><span class="sxs-lookup"><span data-stu-id="80785-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="80785-111">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80785-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="80785-112">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="80785-112">**Viewer**</span></span>  
 <span data-ttu-id="80785-113">選択したマイニング モデルを表示するために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="80785-113">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="80785-114">マイニング モデル用のカスタム ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="80785-114">You can use the custom viewer for the mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="80785-115">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="80785-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="80785-116">**[凡例の表示]**</span><span class="sxs-lookup"><span data-stu-id="80785-116">**Show Legend**</span></span>  
 <span data-ttu-id="80785-117">ビューアーの色と **[状態]** 列の値との対応を示すキーを表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="80785-117">Select this option to display a key that shows the mapping of colors in the viewer to values in the **States** column.</span></span>  
  
 <span data-ttu-id="80785-118">**[ヒストグラム バー]**</span><span class="sxs-lookup"><span data-stu-id="80785-118">**Histogram Bars**</span></span>  
 <span data-ttu-id="80785-119">各ヒストグラムに含まれる状態の数を制御するには、この値を変更します。</span><span class="sxs-lookup"><span data-stu-id="80785-119">Change this value to control how many states are included in each histogram.</span></span> <span data-ttu-id="80785-120">選択した状態の数よりも多くの状態が存在する場合、確率が最も高い状態が保持され、それ以外の状態は **[その他]** にまとめられます。</span><span class="sxs-lookup"><span data-stu-id="80785-120">If there are more states than you choose to display, the states with the highest probability are shown in the histogram, and the remaining states are grouped together into **Other**.</span></span>  
  
 <span data-ttu-id="80785-121">**属性**</span><span class="sxs-lookup"><span data-stu-id="80785-121">**Attributes**</span></span>  
 <span data-ttu-id="80785-122">クラスター モデルに含まれる列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="80785-122">Lists the columns that are in the clustering model.</span></span> <span data-ttu-id="80785-123">各属性のヒストグラムは、アルゴリズムによって識別されるクラスター間での属性の分布を示します。</span><span class="sxs-lookup"><span data-stu-id="80785-123">The histograms for each attribute show how the attribute is distributed among the clusters identified by the algorithm.</span></span>  
  
 <span data-ttu-id="80785-124">**状態**</span><span class="sxs-lookup"><span data-stu-id="80785-124">**States**</span></span>  
 <span data-ttu-id="80785-125">対応するクラスター行での各状態の色、または連続する数値の分布を示すひし形付きのスライダーのいずれかを示すキーを表示します。</span><span class="sxs-lookup"><span data-stu-id="80785-125">Provides a key that either denotes what color represents each state in the corresponding row of clusters, or a slider with diamond that indicates the distribution of continuous numeric values.</span></span> <span data-ttu-id="80785-126">この列は、 **[凡例]** チェック ボックスを使用して、表示/非表示を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="80785-126">You can show or hide this column by using the **Show Legend** check box.</span></span>  
  
 <span data-ttu-id="80785-127">**クラスターのプロファイル**</span><span class="sxs-lookup"><span data-stu-id="80785-127">**Cluster Profiles**</span></span>  
 <span data-ttu-id="80785-128">このセクションには、モデル内の各クラスターに対応する列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="80785-128">This section contains a column for each cluster in the model.</span></span> <span data-ttu-id="80785-129">各属性に対して、各クラスターにおける属性の値の分布を示すヒストグラムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80785-129">For each attribute, the histogram shows the distribution of the values in the attribute for just that cluster.</span></span> <span data-ttu-id="80785-130">グラフには **[母集団]** 列も含まれます。ここでも、ヒストグラムを使用して各属性の値の分布が表示されますが、モデルのすべてが対象になります。</span><span class="sxs-lookup"><span data-stu-id="80785-130">The chart also has a column for **Population**, which also uses histograms to display the distribution of values for each attribute, but for all cases in the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80785-131">参照</span><span class="sxs-lookup"><span data-stu-id="80785-131">See Also</span></span>  
 <span data-ttu-id="80785-132">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="80785-132">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="80785-133">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="80785-133">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="80785-134">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="80785-134">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
