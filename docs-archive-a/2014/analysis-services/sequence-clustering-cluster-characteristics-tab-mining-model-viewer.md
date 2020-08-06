---
title: シーケンスクラスターの [クラスターの特性] タブ (マイニングモデルビューアー)Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.characteristics.f1
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
author: minewiskan
ms.author: owend
ms.openlocfilehash: c991005cb4daa436c86d09037ef523499add84e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741349"
---
# <a name="sequence-clustering-cluster-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="ceebc-102">シーケンス クラスターの [クラスターの特性] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="ceebc-102">Sequence Clustering Cluster Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="ceebc-103">**Microsoft シーケンス クラスター ビューアー** の **[クラスターの特性]** タブには、シーケンス クラスターを定義する属性の詳細な一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-103">The **Cluster Characteristics** tab in the **Microsoft Sequence Clustering Viewer** provides a detailed list of the characteristics that define a sequence cluster.</span></span> <span data-ttu-id="ceebc-104">これらの特性には、単純な属性と値のペアと、状態間の遷移が含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ceebc-104">Those characteristics can include simple attribute-value pairs as well as transitions between states.</span></span>  
  
 <span data-ttu-id="ceebc-105">クラスターの内容をドリル ダウンし、クラスターの代表となるシーケンスを確認するには、シーケンス クラスター モデルのこのビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="ceebc-105">Use this view of a sequence clustering model to drill down into the cluster contents, and see the sequences that are representative of a cluster.</span></span>  
  
 <span data-ttu-id="ceebc-106">**詳細:** [Microsoft シーケンス クラスター アルゴリズム](data-mining/microsoft-sequence-clustering-algorithm.md)、 [Microsoft シーケンス クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="ceebc-106">**For More Information:** [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="ceebc-107">Options</span><span class="sxs-lookup"><span data-stu-id="ceebc-107">Options</span></span>  
 <span data-ttu-id="ceebc-108">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="ceebc-108">**Refresh viewer content**</span></span>  
 <span data-ttu-id="ceebc-109">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="ceebc-109">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="ceebc-110">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="ceebc-110">**Mining Model**</span></span>  
 <span data-ttu-id="ceebc-111">現在のマイニング構造に含まれているマイニング モデルから、表示するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="ceebc-111">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="ceebc-112">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-112">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="ceebc-113">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="ceebc-113">**Viewer**</span></span>  
 <span data-ttu-id="ceebc-114">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="ceebc-114">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="ceebc-115">カスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー ビューアー**を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-115">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="ceebc-116">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-116">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="ceebc-117">**クラスター**</span><span class="sxs-lookup"><span data-stu-id="ceebc-117">**Cluster**</span></span>  
 <span data-ttu-id="ceebc-118">表示するクラスターを選択します。</span><span class="sxs-lookup"><span data-stu-id="ceebc-118">Choose the cluster you want to view.</span></span>  
  
 <span data-ttu-id="ceebc-119">**の特性\<Cluster>**</span><span class="sxs-lookup"><span data-stu-id="ceebc-119">**Characteristics for \<Cluster>**</span></span>  
 <span data-ttu-id="ceebc-120">このテーブルは、現在のクラスターに割り当てられたシーケンスを、確率順に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ceebc-120">This table provides a list of the sequences that were assigned to the current cluster, ordered by probability.</span></span> <span data-ttu-id="ceebc-121">シーケンスは基本的には 1 組の属性と値のペアであり、後ろに 1 組または複数組の属性と値のペアが追加されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-121">Remember that a sequence is basically one attribute-value pair, followed by one or more additional attribute-value pairs.</span></span> <span data-ttu-id="ceebc-122">各クラスターの特性は、シーケンスと確率の組み合わせによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-122">The combination of sequences and their probabilities are the defining characteristics of each cluster.</span></span>  
  
 <span data-ttu-id="ceebc-123">たとえば、マーケット バスケット分析に基づくシーケンス クラスター モデルでは、特売品の選択後、他の商品を購入せずに取引を終了する顧客を最上位特性とするクラスターが考えられます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-123">For example, in a sequence clustering model based on market basket analysis, one cluster might have as its top characteristic a customer choosing the sale item and then ending the transaction without purchasing anything more.</span></span> <span data-ttu-id="ceebc-124">サーバー障害の解析を目的とするシーケンス クラスター モデルでは、クラスターの第 1 の特性は、発生頻度の高いエラー イベントになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ceebc-124">In a sequence clustering model that seeks to analyze server failures, the primary characteristics of a cluster might be a series of high frequency error events.</span></span>  
  
|<span data-ttu-id="ceebc-125">値</span><span class="sxs-lookup"><span data-stu-id="ceebc-125">Value</span></span>|<span data-ttu-id="ceebc-126">説明</span><span class="sxs-lookup"><span data-stu-id="ceebc-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ceebc-127">**変数**</span><span class="sxs-lookup"><span data-stu-id="ceebc-127">**Variable**</span></span>|<span data-ttu-id="ceebc-128">この列は、特性が値であるか遷移であるかを示します。</span><span class="sxs-lookup"><span data-stu-id="ceebc-128">This column indicates whether the characteristic is a value, or a transition.</span></span><br /><br /> <span data-ttu-id="ceebc-129">特性が値の場合、[**変数**] 列には属性名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-129">If the characteristic is a value, the **Variable** column contains the attribute name.</span></span><br /><br /> <span data-ttu-id="ceebc-130">特性が状態遷移を表している場合、[**変数**] 列には "遷移" というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-130">If the characteristic represents a state transition, the **Variable** column contains the text "Transitions".</span></span>|  
|<span data-ttu-id="ceebc-131">**値**</span><span class="sxs-lookup"><span data-stu-id="ceebc-131">**Values**</span></span>|<span data-ttu-id="ceebc-132">この列の値は、特性が単純な属性と値のペアであるか、アイテムまたはイベントの一般的なシーケンスを表す状態遷移であるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ceebc-132">The value of this column depends on whether the characteristic is a simple attribute-value pair, or a state transition representing a common sequence of items or events.</span></span><br /><br /> <span data-ttu-id="ceebc-133">特性が値の場合、[**値**] 列には状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-133">If the characteristic is a value, the **Value** column contains the state.</span></span><br /><br /> <span data-ttu-id="ceebc-134">特性が状態遷移を表す場合、[**値**] 列には状態遷移の説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-134">If the characteristic represents a state transition, the **Value** column contains the description of the state transition.</span></span>|  
|<span data-ttu-id="ceebc-135">**確率**</span><span class="sxs-lookup"><span data-stu-id="ceebc-135">**Probability**</span></span>|<span data-ttu-id="ceebc-136">この列には、特性 (単純な属性と値のペアまたは状態の組み合わせ) が現在のクラスターのメンバーである相対的確率を示すバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-136">This column displays a bar that indicates the relative probability that this characteristic (either a simple attribute-value pair, or some combination of states) are members of the current cluster.</span></span><br /><br /> <span data-ttu-id="ceebc-137">バーの上にマウスを移動することで、特性の頻度の値を表示できます。</span><span class="sxs-lookup"><span data-stu-id="ceebc-137">You can hover the mouse over the par to display the frequency value of the characteristic.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceebc-138">参照</span><span class="sxs-lookup"><span data-stu-id="ceebc-138">See Also</span></span>  
 <span data-ttu-id="ceebc-139">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ceebc-139">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="ceebc-140">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="ceebc-140">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="ceebc-141">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="ceebc-141">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
