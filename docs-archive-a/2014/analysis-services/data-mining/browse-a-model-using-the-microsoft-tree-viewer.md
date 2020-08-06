---
title: Microsoft ツリービューアーを使用したモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Tree Viewer [Analysis Services]
- predictions [Analysis Services], discrete attributes
- mining model content, viewing
- predictions [Analysis Services], continuous attributes
- mining legend [Analysis Services]
- discrete attributes [Analysis Services]
- Microsoft Decision Trees algorithm [Analysis Services]
- decision tree algorithms [Analysis Services]
- Microsoft Tree Viewer
- decision trees [Analysis Services]
- dependencies [Analysis Services]
- continuous attributes
ms.assetid: 0c96d518-ed20-40b7-8d62-b26ad6244287
author: minewiskan
ms.author: owend
ms.openlocfilehash: cebe1e05435fad453757b4f747ae809f379c410f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645942"
---
# <a name="browse-a-model-using-the-microsoft-tree-viewer"></a><span data-ttu-id="9ae39-102">Microsoft ツリー ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="9ae39-102">Browse a Model Using the Microsoft Tree Viewer</span></span>
  <span data-ttu-id="9ae39-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]のツリービューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] デシジョンツリーアルゴリズムを使用して作成されたデシジョンツリーが表示され [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays decision trees that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="9ae39-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムは、分類と回帰の両方をサポートする複合的なデシジョン ツリー アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="9ae39-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is a hybrid decision tree algorithm that supports both classification and regression.</span></span> <span data-ttu-id="9ae39-105">したがって、このビューアーには [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムに基づくモデルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-105">Therefore, you can also use this viewer to view models based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span> <span data-ttu-id="9ae39-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムは、不連続属性と連続属性の両方の予測モデリングに使用します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-106">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is used for predictive modeling of both discrete and continuous attributes.</span></span> <span data-ttu-id="9ae39-107">このアルゴリズムの詳細については、「 [Microsoft デシジョン ツリー アルゴリズム](microsoft-decision-trees-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ae39-107">For more information about this algorithm, see [Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ae39-108">モデルで使用された式と、検出されたパターンの詳細情報を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-108">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="9ae39-109">詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](../microsoft-generic-content-tree-viewer-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ae39-109">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_TabsPanes"></a><span data-ttu-id="9ae39-110">ビューアーのタブ</span><span class="sxs-lookup"><span data-stu-id="9ae39-110">Viewer Tabs</span></span>  
 <span data-ttu-id="9ae39-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-111">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="9ae39-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ツリー ビューアーには、次のタブとペインがあります。</span><span class="sxs-lookup"><span data-stu-id="9ae39-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer includes the following tabs and panes:</span></span>  
  
-   [<span data-ttu-id="9ae39-113">デシジョン ツリー</span><span class="sxs-lookup"><span data-stu-id="9ae39-113">Decision Tree</span></span>](#BKMK_DecisionTree)  
  
-   [<span data-ttu-id="9ae39-114">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="9ae39-114">Dependency Network</span></span>](#BKMK_DependencyNetwork)  
  
-   [<span data-ttu-id="9ae39-115">マイニング凡例</span><span class="sxs-lookup"><span data-stu-id="9ae39-115">Mining Legend</span></span>](#BKMK_MiningLegend)  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a><span data-ttu-id="9ae39-116">デシジョンツリー</span><span class="sxs-lookup"><span data-stu-id="9ae39-116">Decision Tree</span></span>  
 <span data-ttu-id="9ae39-117">デシジョン ツリー モデルを作成すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって、予測可能な属性ごとにツリーが個別に作成されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-117">When you build a decision tree model, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] builds a separate tree for each predictable attribute.</span></span> <span data-ttu-id="9ae39-118">個別のツリーを表示するには、ビューアーの **[デシジョン ツリー]** タブにある **[ツリー]** 一覧から表示するツリーを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-118">You can view an individual tree by selecting it from the **Tree** list on the **Decision Tree** tab of the viewer.</span></span>  
  
 <span data-ttu-id="9ae39-119">デシジョン ツリーは一連の分割で構成されており、アルゴリズムによって最も重要と判別された分割は、ビューアーの左側にある **[すべて]** ノードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-119">A decision tree is composed of a series of splits, with the most important split, as determined by the algorithm, at the left of the viewer in the **All** node.</span></span> <span data-ttu-id="9ae39-120">その他の分割は右側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-120">Additional splits occur to the right.</span></span> <span data-ttu-id="9ae39-121">**[すべて]** ノード内の分割は最も重要です。なぜなら、データセット内で最も強い分割発生条件が含まれており、その結果として最初の分割が発生したからです。</span><span class="sxs-lookup"><span data-stu-id="9ae39-121">The split in the **All** node is most important because it contains the strongest split-causing conditional in the dataset, and therefore it caused the first split.</span></span>  
  
 <span data-ttu-id="9ae39-122">ツリー内の個々のノードを展開したり折りたたんだりすると、各ノードの後にある分割を表示または非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-122">You can expand or collapse individual nodes in the tree to show or hide the splits that occur after each node.</span></span> <span data-ttu-id="9ae39-123">また、 **[デシジョン ツリー]** タブのオプションを使用して、ツリーの表示方法を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-123">You can also use the options on the **Decision Tree** tab to affect how the tree is displayed.</span></span> <span data-ttu-id="9ae39-124">ツリーに表示されるレベルの数を調整するには、 **[表示レベル]** スライダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-124">Use the **Show Level** slider to adjust the number of levels that are shown in the tree.</span></span> <span data-ttu-id="9ae39-125">モデル内のすべてのツリーに表示される既定のレベル数を設定するには、 **[既定の展開]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-125">Use **Default Expansion** to set the default number of levels that are displayed for all trees in the model.</span></span>  
  
#### <a name="predicting-discrete-attributes"></a><span data-ttu-id="9ae39-126">不連続属性の予測</span><span class="sxs-lookup"><span data-stu-id="9ae39-126">Predicting Discrete Attributes</span></span>  
 <span data-ttu-id="9ae39-127">予測可能な不連続属性を使用してツリーを作成した場合、ビューアーにはツリーの各ノードに関する次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-127">When a tree is built with a discrete predictable attribute, the viewer displays the following on each node in the tree:</span></span>  
  
-   <span data-ttu-id="9ae39-128">分割が発生した条件</span><span class="sxs-lookup"><span data-stu-id="9ae39-128">The condition that caused the split.</span></span>  
  
-   <span data-ttu-id="9ae39-129">ポピュラリティ順に並べられた、予測可能な属性の状態の分布を表すヒストグラム</span><span class="sxs-lookup"><span data-stu-id="9ae39-129">A histogram that represents the distribution of the states of the predictable attribute, ordered by popularity.</span></span>  
  
 <span data-ttu-id="9ae39-130">**[ヒストグラム]** オプションを使用すると、ツリーのヒストグラムに表示される状態の数を変更できます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-130">You can use the **Histogram** option to change the number of states that appear in the histograms in the tree.</span></span> <span data-ttu-id="9ae39-131">これは、予測可能な属性に多数の状態が含まれている場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="9ae39-131">This is useful if the predictable attribute has many states.</span></span> <span data-ttu-id="9ae39-132">ヒストグラムには、状態がポピュラリティ順に左から右に表示されます。表示するように選択した状態の数が属性内の状態の総数よりも少ない場合は、最も一般的でない状態がまとめて灰色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-132">The states appear in a histogram in order of popularity from left to right; if the number of states that you choose to display is fewer than the total number of states in the attribute, the least popular states are displayed collectively in gray.</span></span> <span data-ttu-id="9ae39-133">ノードの各状態の正確な数を表示するには、ノードにポインターを合わせてヒントを表示するか、またはノードを選択して **[マイニング凡例]** に詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-133">To see the exact count for each state for a node, pause the pointer over the node to view an InfoTip, or select the node to view its details in the **Mining Legend**.</span></span>  
  
 <span data-ttu-id="9ae39-134">各ノードの背景色は、 **[背景]** オプションを使用して選択した特定の属性状態のケースの集中度を表しています。</span><span class="sxs-lookup"><span data-stu-id="9ae39-134">The background color of each node represents the concentration of cases of the particular attribute state that you select by using the **Background** option.</span></span> <span data-ttu-id="9ae39-135">このオプションを使用して、関心のある特定の対象が含まれたノードを強調表示できます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-135">You can use this option to highlight nodes that contain a particular target in which you are interested.</span></span>  
  
#### <a name="predicting-continuous-attributes"></a><span data-ttu-id="9ae39-136">連続属性の予測</span><span class="sxs-lookup"><span data-stu-id="9ae39-136">Predicting Continuous Attributes</span></span>  
 <span data-ttu-id="9ae39-137">予測可能な連続属性を使用してツリーを作成した場合、ビューアーにはヒストグラムの代わりにツリーの各ノードのダイヤモンド チャートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-137">When a tree is built with a continuous predictable attribute, the viewer displays a diamond chart, instead of a histogram, for each node in the tree.</span></span> <span data-ttu-id="9ae39-138">ダイヤモンド チャートには、属性の範囲を表す線があります。</span><span class="sxs-lookup"><span data-stu-id="9ae39-138">The diamond chart has a line that represents the range of the attribute.</span></span> <span data-ttu-id="9ae39-139">ダイヤモンドはノードの中間にあり、ダイヤモンドの幅がそのノードの属性の分散を表します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-139">The diamond is located at the mean for the node, and the width of the diamond represents the variance of the attribute at that node.</span></span> <span data-ttu-id="9ae39-140">ダイヤモンドの幅が狭いほど、そのノードでより正確な予測を作成できることを示します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-140">A thinner diamond indicates that the node can create a more accurate prediction.</span></span> <span data-ttu-id="9ae39-141">また、ビューアーには、ノード内の分割を決定するために使用される回帰式も表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-141">The viewer also displays the regression equation, which is used to determine the split in the node.</span></span>  
  
#### <a name="additional-decision-tree-display-options"></a><span data-ttu-id="9ae39-142">その他のデシジョン ツリー表示オプション</span><span class="sxs-lookup"><span data-stu-id="9ae39-142">Additional Decision Tree Display Options</span></span>  
 <span data-ttu-id="9ae39-143">デシジョン ツリー モデルのドリルスルーが有効な場合は、ツリーでノードを右クリックして **[ドリルスルー]** を選択すると、ノードをサポートするトレーニング ケースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-143">When drill through is enabled for a decision tree model, you can access the training cases that support a node by right-clicking the node in the tree and selecting **Drill Through**.</span></span> <span data-ttu-id="9ae39-144">ドリルスルーを有効にするには、データ マイニング ウィザード内で設定するか、または **[マイニング モデル]** タブでマイニング モデルのドリルスルー プロパティを調整します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-144">You can enable drill through within the Data Mining Wizard, or by adjusting the drill through property on the mining model in the **Mining Models** tab.</span></span>  
  
 <span data-ttu-id="9ae39-145">**[デシジョン ツリー]** タブのズーム オプションを使用すると、ツリーを拡大または縮小できます。 **[サイズの自動調整]** を使用すると、モデル全体をビューアー画面に合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-145">You can use the zoom options on the **Decision Tree** tab to zoom in or out of a tree, or use **Size to Fit** to fit the whole model in the viewer screen.</span></span> <span data-ttu-id="9ae39-146">ツリーが大きすぎて画面に合うようにサイズを調整できない場合は、 **[ナビゲーション]** オプションを使用してツリー内を移動できます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-146">If a tree is too large to be sized to fit the screen, you can use the **Navigation**option to navigate through the tree.</span></span> <span data-ttu-id="9ae39-147">**[ナビゲーション]** をクリックすると、表示するモデルのセクションを選択できる別のナビゲーション ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-147">Clicking **Navigation** opens a separate navigation window that you can use to select sections of the model to display.</span></span>  
  
 <span data-ttu-id="9ae39-148">ツリー ビューの画像をクリップボードにコピーして、ドキュメントや画像操作ソフトウェアに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-148">You can also copy the tree view image to the Clipboard, so that you can paste it into documents or into image manipulation software.</span></span> <span data-ttu-id="9ae39-149">ビューアーに表示されているツリーのセクションだけをコピーするには、 **[グラフ ビューのコピー]** を使用します。ツリーで展開されているすべてのノードをコピーするには、 **[グラフ全体のコピー]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-149">Use **Copy Graph View** to copy only the section of the tree that is visible in the viewer, or use **Copy Entire Graph** to copy all the expanded nodes in the tree.</span></span>  
  
 [<span data-ttu-id="9ae39-150">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="9ae39-150">Back to Top</span></span>](#BKMK_TabsPanes)  
  
###  <a name="dependency-network"></a><a name="BKMK_DependencyNetwork"></a><span data-ttu-id="9ae39-151">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="9ae39-151">Dependency Network</span></span>  
 <span data-ttu-id="9ae39-152">**[依存関係ネットワーク]** には、モデル内にある入力属性と予測可能属性の間の依存関係が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-152">The **Dependency Network** displays the dependencies between the input attributes and the predictable attributes in the model.</span></span> <span data-ttu-id="9ae39-153">ビューアーの左側にあるスライダーは、依存関係の強さに関連付けられたフィルターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="9ae39-153">The slider at the left of the viewer acts as a filter that is tied to the strengths of the dependencies.</span></span> <span data-ttu-id="9ae39-154">スライダーを下げると、最も強いリンクだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-154">If you lower the slider, only the strongest links are shown in the viewer.</span></span>  
  
 <span data-ttu-id="9ae39-155">ノードを選択すると、そのノードに固有の依存関係が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-155">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="9ae39-156">たとえば、予測可能なノードを選択した場合は、その予測可能なノードの予測に役立つ各ノードも強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-156">For example, if you choose a predictable node, the viewer also highlights each node that helps predict the predictable node.</span></span>  
  
 <span data-ttu-id="9ae39-157">ビューアーに多数のノードがある場合は、 **[ノードの検索]** ボタンを使用して特定のノードを検索できます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-157">If the viewer contains numerous nodes, you can search for specific nodes by using the **Find Node** button.</span></span> <span data-ttu-id="9ae39-158">**[ノードの検索]** をクリックすると、 **[ノードの検索]** ダイアログ ボックスが開き、フィルターを使用して特定のノードを検索して選択できます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-158">Clicking **Find Node** opens the **Find Node** dialog box, in which you can use a filter to search for and select specific nodes.</span></span>  
  
 <span data-ttu-id="9ae39-159">ビューアーの下部にある凡例は、グラフ内の依存関係の種類に色を関連付けています。</span><span class="sxs-lookup"><span data-stu-id="9ae39-159">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="9ae39-160">たとえば、予測可能なノードを選択すると、予測可能なノードが水色で網掛けされ、選択したノードを予測するノードがオレンジ色で網掛けされます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-160">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="9ae39-161">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="9ae39-161">Back to Top</span></span>](#BKMK_TabsPanes)  
  
###  <a name="mining-legend"></a><a name="BKMK_MiningLegend"></a><span data-ttu-id="9ae39-162">マイニング凡例</span><span class="sxs-lookup"><span data-stu-id="9ae39-162">Mining Legend</span></span>  
 <span data-ttu-id="9ae39-163">デシジョン ツリー モデルでノードを選択すると、 **[マイニング凡例]** に次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-163">The **Mining Legend** displays the following information when you select a node in the decision tree model:</span></span>  
  
-   <span data-ttu-id="9ae39-164">予測可能な属性の状態によって分類された、ノード内のケースの数。</span><span class="sxs-lookup"><span data-stu-id="9ae39-164">The number of cases in the node, broken down by the states of the predictable attribute.</span></span>  
  
-   <span data-ttu-id="9ae39-165">ノードの予測可能な属性の各ケースの確率。</span><span class="sxs-lookup"><span data-stu-id="9ae39-165">The probability of each case of the predictable attribute for the node.</span></span>  
  
-   <span data-ttu-id="9ae39-166">予測可能な属性の各状態の数が含まれたヒストグラム。</span><span class="sxs-lookup"><span data-stu-id="9ae39-166">A histogram that includes a count for each state of the predictable attribute.</span></span>  
  
-   <span data-ttu-id="9ae39-167">特定のノードに到達するために必要な条件。" *ノード パス*" としても知られています。</span><span class="sxs-lookup"><span data-stu-id="9ae39-167">The conditions that are required to reach a specific node, also known as the *node path*.</span></span>  
  
-   <span data-ttu-id="9ae39-168">線形回帰モデルの回帰式。</span><span class="sxs-lookup"><span data-stu-id="9ae39-168">For linear regression models, the regression formula.</span></span>  
  
 <span data-ttu-id="9ae39-169">ソリューション エクスプローラーと同様の方法で **[マイニング凡例]** をドッキングして操作できます。</span><span class="sxs-lookup"><span data-stu-id="9ae39-169">You can dock and work with the **Mining Legend** in a similar manner as with Solution Explorer.</span></span>  
  
 [<span data-ttu-id="9ae39-170">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="9ae39-170">Back to Top</span></span>](#BKMK_TabsPanes)  
  
## <a name="see-also"></a><span data-ttu-id="9ae39-171">参照</span><span class="sxs-lookup"><span data-stu-id="9ae39-171">See Also</span></span>  
 <span data-ttu-id="9ae39-172">[Microsoft デシジョンツリーアルゴリズム](microsoft-decision-trees-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="9ae39-172">[Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md) </span></span>  
 <span data-ttu-id="9ae39-173">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](../mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="9ae39-173">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](../mining-model-viewers-data-mining-model-designer.md) </span></span>  
 <span data-ttu-id="9ae39-174">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="9ae39-174">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="9ae39-175">[データマイニングツール](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9ae39-175">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="9ae39-176">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="9ae39-176">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
