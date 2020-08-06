---
title: '[モデル] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.timeseries.decisiontree.f1
ms.assetid: 50570bb4-fcac-411e-b530-0398437efda7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 656468b2b850502ff4be32fbdbe501c775f7a3b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720385"
---
# <a name="model-tab-mining-model-viewers"></a><span data-ttu-id="29be4-102">[モデル] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="29be4-102">Model Tab (Mining Model Viewers)</span></span>
  <span data-ttu-id="29be4-103">Microsoft タイム シリーズ ビューアーの **[モデル]** タブは、タイム シリーズの表現をグラフのノードとして表示します。これは、デシジョン ツリー モデルで使用されるものに似ています。</span><span class="sxs-lookup"><span data-stu-id="29be4-103">The **Model** tab in the Microsoft Time Series Viewer displays a representation of a time series as a node in a graph, similar to those used in decision tree models.</span></span>  
  
 <span data-ttu-id="29be4-104">時系列分析に関する有用な情報を抽出するには、グラフの式、ARIMA 期間、および係数を含むタイム シリーズ モデルのこのビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="29be4-104">Use this view of a time series model to extract useful information about the time series analysis, including the equation for the graph, the ARIMA terms, and the coefficients.</span></span>  
  
 <span data-ttu-id="29be4-105">**詳細情報:** [Microsoft Time Series アルゴリズム](data-mining/microsoft-time-series-algorithm.md)、 [Microsoft タイム シリーズ ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)、 [Microsoft Time Series アルゴリズム](data-mining/microsoft-time-series-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="29be4-105">**For More Information:** [Microsoft Time Series Algorithm](data-mining/microsoft-time-series-algorithm.md), [Browse a Model Using the Microsoft Time Series Viewer](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md), [Microsoft Time Series Algorithm](data-mining/microsoft-time-series-algorithm.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="29be4-106">Options</span><span class="sxs-lookup"><span data-stu-id="29be4-106">Options</span></span>  
 <span data-ttu-id="29be4-107">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="29be4-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="29be4-108">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="29be4-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="29be4-109">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="29be4-109">**Mining Model**</span></span>  
 <span data-ttu-id="29be4-110">表示するマイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="29be4-110">Choose a mining model to view.</span></span> <span data-ttu-id="29be4-111">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="29be4-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="29be4-112">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="29be4-112">**Viewer**</span></span>  
 <span data-ttu-id="29be4-113">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="29be4-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="29be4-114">このモデルの種類用のカスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー** ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="29be4-114">You can use the custom viewer for this model type, or the **Microsoft Generic Content Tree** viewer.</span></span> <span data-ttu-id="29be4-115">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="29be4-115">You can also use plug-in viewers, if available.</span></span>  
  
 <span data-ttu-id="29be4-116">**拡大**</span><span class="sxs-lookup"><span data-stu-id="29be4-116">**Zoom In**</span></span>  
 <span data-ttu-id="29be4-117">ダイアグラムを拡大します。</span><span class="sxs-lookup"><span data-stu-id="29be4-117">Zoom in to the diagram.</span></span>  
  
 <span data-ttu-id="29be4-118">**縮小**</span><span class="sxs-lookup"><span data-stu-id="29be4-118">**Zoom Out**</span></span>  
 <span data-ttu-id="29be4-119">グラフを縮小します。</span><span class="sxs-lookup"><span data-stu-id="29be4-119">Zoom out from the diagram.</span></span>  
  
 <span data-ttu-id="29be4-120">**[グラフ ビューのコピー]**</span><span class="sxs-lookup"><span data-stu-id="29be4-120">**Copy Graph View**</span></span>  
 <span data-ttu-id="29be4-121">ダイアグラムで表示されている部分をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="29be4-121">Copy the visible section of the diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="29be4-122">**[グラフ全体のコピー]**</span><span class="sxs-lookup"><span data-stu-id="29be4-122">**Copy Entire Graph**</span></span>  
 <span data-ttu-id="29be4-123">ダイアグラム全体をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="29be4-123">Copy the complete diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="29be4-124">**[サイズの自動調整]**</span><span class="sxs-lookup"><span data-stu-id="29be4-124">**Scale diagram to fit window**</span></span>  
 <span data-ttu-id="29be4-125">画面の大きさに合うようにダイアグラム全体を縮小します。</span><span class="sxs-lookup"><span data-stu-id="29be4-125">Zoom out from the diagram until the whole diagram fits within the screen.</span></span>  
  
 <span data-ttu-id="29be4-126">**ツリー**</span><span class="sxs-lookup"><span data-stu-id="29be4-126">**Tree**</span></span>  
 <span data-ttu-id="29be4-127">ビューアーに表示するツリーをドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="29be4-127">Select a tree from the dropdown list to show in the viewer</span></span>  
  
 <span data-ttu-id="29be4-128">タイム シリーズ モデルに複数のシリーズが含まれている場合、各シリーズは個別のツリーで表されます。</span><span class="sxs-lookup"><span data-stu-id="29be4-128">If the time series model includes multiple series, each series is represented as a separate tree.</span></span> <span data-ttu-id="29be4-129">たとえば、[Quantity] と [Sales Amount] の両方に対して期間の予測を作成した場合、予測可能な属性ごとにシリーズが作成されます。</span><span class="sxs-lookup"><span data-stu-id="29be4-129">For example, if you created predictions over time for both [Quantity] and [Sales Amount], a separate series is created for each predictable attribute.</span></span>  
  
 <span data-ttu-id="29be4-130">リストで強調表示される色の長さは、ツリーのレベル数を示します。</span><span class="sxs-lookup"><span data-stu-id="29be4-130">The length of the color highlighting in the list indicates the number of levels in the tree.</span></span> <span data-ttu-id="29be4-131">つまり、単一のノードで表すことができるタイム シリーズ モデルには傾向を記述する式が 1 つだけ存在し、色分けされたバーの長さは非常に短くなります</span><span class="sxs-lookup"><span data-stu-id="29be4-131">That is, a time series model that can be represented by a single node would have a single equation to describe the trend and the colored bar would be very short.</span></span> <span data-ttu-id="29be4-132">(言うまでもなく、モデルが MIXED モデルの場合、ノードには ARIMA 式と ARTXP 式の両方が含まれます)。</span><span class="sxs-lookup"><span data-stu-id="29be4-132">(Of course, if the model is a MIXED model, the node will contain both an ARIMA and an ARTXP equation.)</span></span>  
  
 <span data-ttu-id="29be4-133">ドロップダウン リストに表示されるツリーの色分けされたバーが長い場合は、モデルのツリーに多数の分岐が存在します。</span><span class="sxs-lookup"><span data-stu-id="29be4-133">If the tree shown in the dropdown list has a longer colored bar, it means the model has many branches in the tree.</span></span> <span data-ttu-id="29be4-134">分岐は、回帰がより複雑であり、各ノードで異なる式 (または式のペア) を使用してモデルを複数のセグメントに分割する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="29be4-134">Branching means the regression is more complex and the model has to be broken into multiple segments, with a different equation (or pair of equations) in each node.</span></span>  
  
 <span data-ttu-id="29be4-135">**背景**</span><span class="sxs-lookup"><span data-stu-id="29be4-135">**Background**</span></span>  
 <span data-ttu-id="29be4-136">このコントロールを使用して、各ノードの背景色によって表される状態を選択します。</span><span class="sxs-lookup"><span data-stu-id="29be4-136">Use this control to select the state that is represented by the background color in each node.</span></span>  
  
 <span data-ttu-id="29be4-137">**既定の展開**</span><span class="sxs-lookup"><span data-stu-id="29be4-137">**Default Expansion**</span></span>  
 <span data-ttu-id="29be4-138">モデル内のすべてのツリーに対して表示される、レベルの既定の数を調整します。</span><span class="sxs-lookup"><span data-stu-id="29be4-138">Adjust the default number of levels that are displayed for all trees in the model.</span></span>  
  
 <span data-ttu-id="29be4-139">**[表示レベル]**</span><span class="sxs-lookup"><span data-stu-id="29be4-139">**Show Level**</span></span>  
 <span data-ttu-id="29be4-140">ツリーに表示されるレベルの数を変更します。</span><span class="sxs-lookup"><span data-stu-id="29be4-140">Change the number of levels that are shown in the tree.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29be4-141">参照</span><span class="sxs-lookup"><span data-stu-id="29be4-141">See Also</span></span>  
 <span data-ttu-id="29be4-142">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="29be4-142">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="29be4-143">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="29be4-143">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="29be4-144">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="29be4-144">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
