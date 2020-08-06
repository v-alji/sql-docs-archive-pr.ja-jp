---
title: マイニングモデルビューアー (データマイニングモデルデザイナー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.viewers.f1
ms.assetid: 4ba391d5-c97b-4848-ba7c-7d096fa4b7dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4cc1c9d72a08ef49ed2f4f466953d2ba61394178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740566"
---
# <a name="mining-model-viewers-data-mining-model-designer"></a><span data-ttu-id="26e20-102">マイニング モデル ビューアー (データ マイニング モデル デザイナー)</span><span class="sxs-lookup"><span data-stu-id="26e20-102">Mining Model Viewers (Data Mining Model Designer)</span></span>
  <span data-ttu-id="26e20-103">**[マイニング モデル ビューアー]** タブでは、マイニング構造に含まれているマイニング モデルを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="26e20-103">Use the **Mining Model Viewer** tab to explore the mining models that a mining structure contains.</span></span>

 <span data-ttu-id="26e20-104">最初にマイニング モデルを選択してから、ビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="26e20-104">First you select the mining model and then you select a viewer.</span></span> <span data-ttu-id="26e20-105">各モデルでは、常に、複数のタブを表示できるカスタム ビューアーと汎用ビューアーの 2 種類のビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="26e20-105">Each model always has two viewers available: a custom viewer, which can include multiple tabs, and the generic viewer.</span></span>

 <span data-ttu-id="26e20-106">各ビューアーの使用方法に関するチュートリアルについては、「 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e20-106">For a walkthrough of how to use each viewer, see [Data Mining Model Viewers](data-mining/data-mining-model-viewers.md).</span></span>

## <a name="common-options"></a><span data-ttu-id="26e20-107">共通オプション</span><span class="sxs-lookup"><span data-stu-id="26e20-107">Common Options</span></span>
 <span data-ttu-id="26e20-108">**[ビューアーのコンテンツを最新状態に更新]** ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="26e20-108">**Refresh viewer content** Reload the mining model in the viewer.</span></span>

 <span data-ttu-id="26e20-109">**マイニングモデル**現在のマイニング構造に含まれている、表示するマイニングモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="26e20-109">**Mining Model** Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="26e20-110">まず、関連付けられているカスタム ビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="26e20-110">The mining model will first open in its associated custom viewer.</span></span>

 <span data-ttu-id="26e20-111">**[ビューアー]** 選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="26e20-111">**Viewer** Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="26e20-112">この一覧には、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 各マイニングモデル、 [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニングコンテンツビューアー、およびすべてのプラグインビューアーに用意されているビューアーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="26e20-112">This list includes the viewers that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides for each mining model, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer, and any plug-in viewers.</span></span>

 <span data-ttu-id="26e20-113">次の図は、同じモデルに対するカスタム ビューアーと汎用ビューアーを示しています。</span><span class="sxs-lookup"><span data-stu-id="26e20-113">The following diagram shows a custom viewer and the generic viewer for the same model.</span></span>

-   <span data-ttu-id="26e20-114">上の図では、Microsoft Time Series アルゴリズムに基づくマイニング モデルのビューアーを示しています。</span><span class="sxs-lookup"><span data-stu-id="26e20-114">The upper diagram shows the viewer for a mining model based on the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="26e20-115">この特定のカスタム ビューアーによってタイム シリーズのグラフが自動的に作成され、5 つの予測が提供されます。</span><span class="sxs-lookup"><span data-stu-id="26e20-115">This particular custom viewer automatically creates a graph of the time series and provides five predictions.</span></span>

-   <span data-ttu-id="26e20-116">下の図では、 **Microsoft 汎用コンテンツ ツリー ビューアー**を使用して表示される同じモデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="26e20-116">The lower diagram shows the same model displayed using the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="26e20-117">このビューアーは、標準スキーマに従ってマイニング モデルのコンテンツを表示します。</span><span class="sxs-lookup"><span data-stu-id="26e20-117">This viewer presents the contents of the mining model according to a standardized schema.</span></span> <span data-ttu-id="26e20-118">詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](microsoft-generic-content-tree-viewer-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e20-118">For more information, see [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](microsoft-generic-content-tree-viewer-data-mining.md).</span></span>

 <span data-ttu-id="26e20-119">![マイニング モデル デザイナーの概要](media/generic-mining-model-tab1.gif "マイニング モデル デザイナーの概要")</span><span class="sxs-lookup"><span data-stu-id="26e20-119">![Overview of mining model designer](media/generic-mining-model-tab1.gif "Overview of mining model designer")</span></span>

## <a name="viewers-and-their-components"></a><span data-ttu-id="26e20-120">ビューアーとそのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="26e20-120">Viewers and Their Components</span></span>
 <span data-ttu-id="26e20-121">選択されたデータ マイニング モデルの作成に使用したアルゴリズムに合わせて調整されるため、選択したモデルに応じて表示されるカスタム ビューアーは異なります。</span><span class="sxs-lookup"><span data-stu-id="26e20-121">Depending on the model that you select, you will see a different custom viewer, tailored to the algorithm that you used to create the selected data mining model.</span></span> <span data-ttu-id="26e20-122">各カスタム ビューアーには、モデルの統計とパターンの調査に役立つさまざまなツールやダイアログ ボックスがあります。</span><span class="sxs-lookup"><span data-stu-id="26e20-122">Each custom viewer has a variety of tools and dialog boxes for helping you explore the statistics and patterns in the model.</span></span>

 <span data-ttu-id="26e20-123">カスタム ビューアーの各部分の説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26e20-123">The following list describes the options in each of the custom viewers.</span></span>

### <a name="microsoft-association-rules-algorithm"></a><span data-ttu-id="26e20-124">Microsoft アソシエーション ルール アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="26e20-124">Microsoft Association Rules Algorithm</span></span>

-   [<span data-ttu-id="26e20-125">Microsoft アソシエーション ルール ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="26e20-125">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)

    -   <span data-ttu-id="26e20-126">[[アイテムセット] タブ &#40;マイニングモデルビューアー&#41;](itemsets-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-126">[Itemsets Tab &#40;Mining Model Viewer&#41;](itemsets-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-127">[[ルール] タブ &#40;マイニングモデルビューアー&#41;](rules-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-127">[Rules Tab &#40;Mining Model Viewer&#41;](rules-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-128">[[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-128">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

### <a name="microsoft-clustering-algorithm"></a><span data-ttu-id="26e20-129">Microsoft クラスタリング アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="26e20-129">Microsoft Clustering Algorithm</span></span>

-   [<span data-ttu-id="26e20-130">「Microsoft クラスター ビューアーを使用したモデルの参照」</span><span class="sxs-lookup"><span data-stu-id="26e20-130">Browse a Model Using the Microsoft Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)

    -   <span data-ttu-id="26e20-131">[[クラスターダイアグラム] タブ &#40;マイニングモデルビューアー&#41;](cluster-diagram-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-131">[Cluster Diagram Tab &#40;Mining Model Viewer&#41;](cluster-diagram-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-132">[[クラスターのプロファイル] タブ &#40;マイニングモデルビューアー&#41;](cluster-profiles-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-132">[Cluster Profiles Tab &#40;Mining Model Viewer&#41;](cluster-profiles-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-133">[[クラスターの特性] タブ &#40;マイニングモデルビューアー&#41;](cluster-characteristics-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-133">[Cluster Characteristics Tab &#40;Mining Model Viewer&#41;](cluster-characteristics-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-134">[[クラスターの識別] タブ &#40;マイニングモデルビューアー&#41;](cluster-discrimination-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-134">[Cluster Discrimination Tab &#40;Mining Model Viewer&#41;](cluster-discrimination-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-135">[[マイニング凡例] ダイアログボックス &#40;マイニングモデルビューアー&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-135">[Mining Legend Dialog Box &#40;Mining Model Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span></span>

### <a name="microsoft-decision-tree-algorithm"></a><span data-ttu-id="26e20-136">Microsoft デシジョン ツリー アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="26e20-136">Microsoft Decision Tree Algorithm</span></span>

-   [<span data-ttu-id="26e20-137">Microsoft ツリー ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="26e20-137">Browse a Model Using the Microsoft Tree Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)

    -   <span data-ttu-id="26e20-138">[[デシジョンツリー] タブ &#40;マイニングモデルビューアー&#41;](decision-tree-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-138">[Decision Tree Tab &#40;Mining Model Viewer&#41;](decision-tree-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-139">[[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-139">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-140">[[マイニング凡例] ダイアログボックス &#40;マイニングモデルビューアー&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-140">[Mining Legend Dialog Box &#40;Mining Model Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span></span>

### <a name="microsoft-linear-regression-algorithm"></a><span data-ttu-id="26e20-141">Microsoft 線形回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="26e20-141">Microsoft Linear Regression Algorithm</span></span>

-   [<span data-ttu-id="26e20-142">Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="26e20-142">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   <span data-ttu-id="26e20-143">[[デシジョンツリー] タブ &#40;マイニングモデルビューアー&#41;](decision-tree-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-143">[Decision Tree Tab &#40;Mining Model Viewer&#41;](decision-tree-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-144">[[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-144">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-145">[[マイニング凡例] ダイアログボックス &#40;マイニングモデルビューアー&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-145">[Mining Legend Dialog Box &#40;Mining Model Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span></span>

### <a name="microsoft-logistic-regression-algorithm"></a><span data-ttu-id="26e20-146">Microsoft ロジスティック回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="26e20-146">Microsoft Logistic Regression Algorithm</span></span>

-   [<span data-ttu-id="26e20-147">Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="26e20-147">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

### <a name="microsoft-nave-bayes-algorithm"></a><span data-ttu-id="26e20-148">Microsoft Na&#239;</ph>ve Bayes アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="26e20-148">Microsoft Naïve Bayes Algorithm</span></span>

-   [<span data-ttu-id="26e20-149">Microsoft Naive Bayes ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="26e20-149">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)

    -   <span data-ttu-id="26e20-150">[[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-150">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-151">[[属性のプロファイル] タブ &#40;マイニングモデルビューアー&#41;](attribute-profiles-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-151">[Attribute Profiles Tab &#40;Mining Model Viewer&#41;](attribute-profiles-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-152">[[属性の特性] タブ &#40;マイニングモデルビューアー&#41;](attribute-characteristics-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-152">[Attribute Characteristics Tab &#40;Mining Model Viewer&#41;](attribute-characteristics-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-153">[[属性の識別] タブ &#40;マイニングモデルビューアー&#41;](attribute-discrimination-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-153">[Attribute Discrimination Tab &#40;Mining Model Viewer&#41;](attribute-discrimination-tab-mining-model-viewer.md)</span></span>

### <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="26e20-154">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="26e20-154">Microsoft Neural Network Algorithm</span></span>

-   [<span data-ttu-id="26e20-155">Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="26e20-155">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   <span data-ttu-id="26e20-156">[[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-156">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

    -   [<span data-ttu-id="26e20-157">ニューラルネットワーク &#40;マイニングモデルビューアー&#41;</span><span class="sxs-lookup"><span data-stu-id="26e20-157">Neural Network &#40;Mining Model Viewer&#41;</span></span>](neural-network-mining-model-viewer.md)

    -   <span data-ttu-id="26e20-158">[[ノードの検索] ダイアログボックス &#40;マイニングモデルビューアー&#41;](find-node-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-158">[Find Node Dialog Box &#40;Mining Model Viewer&#41;](find-node-dialog-box-mining-model-viewer.md)</span></span>

### <a name="microsoft-sequence-clustering-algorithm"></a><span data-ttu-id="26e20-159">「Microsoft シーケンス クラスター アルゴリズム」</span><span class="sxs-lookup"><span data-stu-id="26e20-159">Microsoft Sequence Clustering Algorithm</span></span>

-   [<span data-ttu-id="26e20-160">Microsoft シーケンス クラスター ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="26e20-160">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)

    -   <span data-ttu-id="26e20-161">[シーケンスクラスターの [クラスターダイアグラム] タブ &#40;マイニングモデルビューアー](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-161">[Sequence Clustering Cluster Diagram Tab &#40;Mining Model Viewer](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-162">[マイニングモデルビューアー &#40;シーケンスクラスターの [クラスターのプロファイル] タブ](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-162">[Sequence Clustering Cluster Profiles Tab &#40;Mining Model Viewer](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-163">[マイニングモデルビューアー &#40;のシーケンスクラスターの [クラスターの特性] タブ&#41;](sequence-clustering-cluster-characteristics-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-163">[Sequence Clustering Cluster Characteristics Tab &#40;Mining Model Viewer&#41;](sequence-clustering-cluster-characteristics-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-164">[マイニングモデルビューアー &#40;のシーケンスクラスターの [クラスターの識別] タブ&#41;](sequence-clustering-cluster-discrimination-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-164">[Sequence Clustering Cluster Discrimination Tab &#40;Mining Model Viewer&#41;](sequence-clustering-cluster-discrimination-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="26e20-165">[マイニングモデルビューアー &#40;のシーケンスクラスターの [遷移] タブ&#41;](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-165">[Sequence Clustering Cluster Transition Tab &#40;Mining Model Viewer&#41;](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)</span></span>

### <a name="microsoft-time-series-algorithm"></a><span data-ttu-id="26e20-166">Microsoft Time Series アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="26e20-166">Microsoft Time Series Algorithm</span></span>

-   [<span data-ttu-id="26e20-167">Microsoft タイム シリーズ ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="26e20-167">Browse a Model Using the Microsoft Time Series Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)

    -   <span data-ttu-id="26e20-168">[[モデル] タブ &#40;マイニングモデルビューアー&#41;](model-tab-mining-model-viewers.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-168">[Model Tab &#40;Mining Model Viewers&#41;](model-tab-mining-model-viewers.md)</span></span>

    -   <span data-ttu-id="26e20-169">[[グラフ] タブ &#40;マイニングモデルビューアー&#41;](chart-tab-mining-model-viewers.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-169">[Chart Tab &#40;Mining Model Viewers&#41;](chart-tab-mining-model-viewers.md)</span></span>

    -   <span data-ttu-id="26e20-170">[[マイニング凡例] ダイアログボックス &#40;マイニングモデルビューアー&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="26e20-170">[Mining Legend Dialog Box &#40;Mining Model Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="26e20-171">参照</span><span class="sxs-lookup"><span data-stu-id="26e20-171">See Also</span></span>
 <span data-ttu-id="26e20-172">マイニング[モデルビュー &#40;データマイニングモデルデザイナー&#41;](mining-models-view-data-mining-model-designer.md) [マイニング構造ビュー &#40;データマイニングモデルデザイナー&#41;](mining-structure-view-data-mining-model-designer.md) [マイニング精度チャートデザイナー &#40;データマイニング&#41;](mining-accuracy-chart-designer-data-mining.md) [予測クエリビルダー &#40;データマイニング](prediction-query-builder-data-mining.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="26e20-172">[Mining Models View &#40;Data Mining Model Designer&#41;](mining-models-view-data-mining-model-designer.md) [Mining Structure View &#40;Data Mining Model Designer&#41;](mining-structure-view-data-mining-model-designer.md) [Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) [Prediction Query Builder &#40;Data Mining&#41;](prediction-query-builder-data-mining.md)</span></span>


