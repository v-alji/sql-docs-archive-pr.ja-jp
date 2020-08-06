---
title: Microsoft Naive Bayes Viewer を使用したモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discrimination [Analysis Services]
- naive bayes model [Analysis Services]
- Bayesian classifiers
- mining model content, viewing
- predictive modeling [Analysis Services]
- Naive Bayes Viewer [Analysis Services]
- data mining [Analysis Services], predictive modeling
- Microsoft Naive Bayes Viewer
- histograms [Analysis Services]
- mining models [Analysis Services], predictive modeling
- dependencies [Analysis Services]
ms.assetid: 19743095-63c1-4486-8c1d-2efc143243be
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03469e73d82a389426f91d8757630f50fe78fc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645947"
---
# <a name="browse-a-model-using-the-microsoft-naive-bayes-viewer"></a><span data-ttu-id="73a84-102">Microsoft Naive Bayes ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="73a84-102">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>
  <span data-ttu-id="73a84-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]の Naive Bayes ビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Naive Bayes アルゴリズムを使用して作成されたマイニングモデルが表示され [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="73a84-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span> <span data-ttu-id="73a84-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムは、予測モデリング タスクに非常に適した分類アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="73a84-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm that is highly adaptable to predictive modeling tasks.</span></span> <span data-ttu-id="73a84-105">このアルゴリズムの詳細については、「 [Microsoft Naive Bayes アルゴリズム](microsoft-naive-bayes-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73a84-105">For more information about this algorithm, see [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md).</span></span>  
  
 <span data-ttu-id="73a84-106">Naive Bayes モデルの主な目的の 1 つはデータセット内のデータを短時間で調査できるようにすることなので、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes ビューアーには、予測可能属性および入力属性の相互関係を表示するための手段がいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="73a84-106">Because one of the main purposes of a naive Bayes model is to provide a way to quickly explore the data in a dataset, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer provides several methods for displaying the interaction between predictable attributes and input attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73a84-107">モデルで使用された式と、検出されたパターンの詳細情報を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="73a84-107">If you want to view detailed information about the equations used in the model and the patterns that were discovered, you can switch to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="73a84-108">詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](../microsoft-generic-content-tree-viewer-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73a84-108">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="73a84-109">ビューアーのタブ</span><span class="sxs-lookup"><span data-stu-id="73a84-109">Viewer Tabs</span></span>  
 <span data-ttu-id="73a84-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-110">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="73a84-111">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes ビューアーには、データを調査するための次のタブがあります。</span><span class="sxs-lookup"><span data-stu-id="73a84-111">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer provides the following tabs for exploring data:</span></span>  
  
-   [<span data-ttu-id="73a84-112">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="73a84-112">Dependency Network</span></span>](#BKMK_Dependency)  
  
-   [<span data-ttu-id="73a84-113">属性のプロファイル</span><span class="sxs-lookup"><span data-stu-id="73a84-113">Attribute Profiles</span></span>](#BKMK_Profiles)  
  
-   [<span data-ttu-id="73a84-114">属性の特性</span><span class="sxs-lookup"><span data-stu-id="73a84-114">Attribute Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="73a84-115">属性の識別</span><span class="sxs-lookup"><span data-stu-id="73a84-115">Attribute Discrimination</span></span>](#BKMK_Discrimination)  
  
##  <a name="dependency-network"></a><a name="BKMK_Dependency"></a><span data-ttu-id="73a84-116">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="73a84-116">Dependency Network</span></span>  
 <span data-ttu-id="73a84-117">**[依存関係ネットワーク]** タブには、モデル内にある入力属性と予測可能属性の間の依存関係が表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-117">The **Dependency Network** tab displays the dependencies between the input attributes and the predictable attributes in a model.</span></span> <span data-ttu-id="73a84-118">ビューアーの左側にあるスライダーは、依存関係の強さに関連付けられたフィルターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="73a84-118">The slider at the left of the viewer acts as a filter that is tied to the strengths of the dependencies.</span></span> <span data-ttu-id="73a84-119">スライダーを小さく設定すると、緊密なリンクのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-119">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="73a84-120">ノードを選択すると、そのノードに固有の依存関係が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-120">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="73a84-121">たとえば、予測可能なノードを選択した場合は、その予測可能なノードの予測に役立つ各ノードも強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-121">For example, if you choose a predictable node, the viewer also highlights each node that helps predict the predictable node.</span></span>  
  
 <span data-ttu-id="73a84-122">ビューアーの下部にある凡例は、グラフ内の依存関係の種類に色を関連付けています。</span><span class="sxs-lookup"><span data-stu-id="73a84-122">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="73a84-123">たとえば、予測可能なノードを選択すると、予測可能なノードが水色で網掛けされ、選択したノードを予測するノードがオレンジ色で網掛けされます。</span><span class="sxs-lookup"><span data-stu-id="73a84-123">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="73a84-124">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="73a84-124">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-profiles"></a><a name="BKMK_Profiles"></a> <span data-ttu-id="73a84-125">属性のプロファイル</span><span class="sxs-lookup"><span data-stu-id="73a84-125">Attribute Profiles</span></span>  
 <span data-ttu-id="73a84-126">**[属性のプロファイル]** タブでは、グリッドにヒストグラムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-126">The **Attribute Profiles** tab displays histograms in a grid.</span></span> <span data-ttu-id="73a84-127">このグリッドを使用すると、 **[予測可能]** ボックスで選択した予測可能属性を、モデル内の他のすべての属性と比較できます。</span><span class="sxs-lookup"><span data-stu-id="73a84-127">You can use this grid to compare the predictable attribute that you select in the **Predictable** box to all other attributes that are in the model.</span></span> <span data-ttu-id="73a84-128">タブ内の各列は、予測可能属性の状態を表します。</span><span class="sxs-lookup"><span data-stu-id="73a84-128">Each column in the tab represents a state of the predictable attribute.</span></span> <span data-ttu-id="73a84-129">予測可能属性に多くの状態がある場合は、 **[ヒストグラム バー]** を調整して、ヒストグラムに表示される状態の数を変更できます。</span><span class="sxs-lookup"><span data-stu-id="73a84-129">If the predictable attribute has many states, you can change the number of states that appear in the histogram by adjusting the **Histogram bars**.</span></span> <span data-ttu-id="73a84-130">選択した数が属性内の状態の総数よりも少ない場合、状態はサポートされている順に一覧表示され、残りの状態は 1 つの灰色のバケットにまとめられます。</span><span class="sxs-lookup"><span data-stu-id="73a84-130">If the number you choose is less than the total number of states in the attribute, the states are listed in order of support, with the remaining states collected into a single gray bucket.</span></span>  
  
 <span data-ttu-id="73a84-131">ヒストグラムの色を属性の状態に関連付けるマイニング凡例を表示するには、 **[凡例の表示]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="73a84-131">To display a Mining Legend that relates the colors of the histogram to the states of an attribute, click the **Show Legend** check box.</span></span> <span data-ttu-id="73a84-132">マイニング凡例には、選択した属性と値の各ペアに関するケースの分布も表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-132">The Mining Legend also displays the distribution of cases for each attribute-value pair that you select.</span></span>  
  
 <span data-ttu-id="73a84-133">グリッドの内容を HTML テーブルとしてクリップボードにコピーするには、 **[属性のプロファイル]** タブを右クリックして **[コピー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="73a84-133">To copy the contents of the grid to the Clipboard as an HTML table, right-click the **Attribute Profiles** tab and select **Copy**.</span></span>  
  
 [<span data-ttu-id="73a84-134">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="73a84-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-characteristics"></a><a name="BKMK_Characteristics"></a><span data-ttu-id="73a84-135">属性の特性</span><span class="sxs-lookup"><span data-stu-id="73a84-135">Attribute Characteristics</span></span>  
 <span data-ttu-id="73a84-136">**[属性の特性]** タブを使用するには、 **[属性]** 一覧から予測可能属性を選択し、選択した属性の状態を **[値]** 一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="73a84-136">To use the **Attribute Characteristics** tab, select a predictable attribute from the **Attribute** list and select a state of the selected attribute from the **Value** list.</span></span> <span data-ttu-id="73a84-137">これらの変数を設定すると、選択した属性の選択したケースに関連付けられている属性の状態が **[属性の特性]** タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-137">When you set these variables, the **Attribute Characteristics** tab displays the states of the attributes that are associated with the selected case of the selected attribute.</span></span> <span data-ttu-id="73a84-138">属性は、重要なものから順番に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="73a84-138">The attributes are sorted by importance.</span></span>  
  
 [<span data-ttu-id="73a84-139">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="73a84-139">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-discrimination"></a><a name="BKMK_Discrimination"></a><span data-ttu-id="73a84-140">属性の識別</span><span class="sxs-lookup"><span data-stu-id="73a84-140">Attribute Discrimination</span></span>  
 <span data-ttu-id="73a84-141">**[属性の識別]** タブを使用するには、予測可能属性を選択し、 **[属性]**、 **[値 1]**、および **[値 2]** の一覧から属性の状態を 2 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="73a84-141">To use the **Attribute Discrimination** tab, select a predictable attribute and two of its states from the **Attribute**, **Value 1**, and **Value 2** lists.</span></span> <span data-ttu-id="73a84-142">**[属性の識別]** タブのグリッドの列に、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-142">The grid on the **Attribute Discrimination** tab then displays the following information in columns:</span></span>  
  
 <span data-ttu-id="73a84-143">**属性**</span><span class="sxs-lookup"><span data-stu-id="73a84-143">**Attribute**</span></span>  
 <span data-ttu-id="73a84-144">予測可能属性の 1 つの状態を優先する状態が含まれているデータセット内の別の属性が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-144">Lists other attributes in the dataset that contain a state that highly favors one state of the predictable attribute.</span></span>  
  
 <span data-ttu-id="73a84-145">**値**</span><span class="sxs-lookup"><span data-stu-id="73a84-145">**Values**</span></span>  
 <span data-ttu-id="73a84-146">**[属性]** 列の属性の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-146">Shows the value of the attribute in the **Attribute** column.</span></span>  
  
 <span data-ttu-id="73a84-147">**ライター\<value 1>**</span><span class="sxs-lookup"><span data-stu-id="73a84-147">**Favors \<value 1>**</span></span>  
 <span data-ttu-id="73a84-148">**[値 1]** の予測可能な属性値が優先される度合いを示す、色分けされたバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-148">Shows a colored bar that indicates how strongly the attribute value favors the predictable attribute value shown in **Value 1**.</span></span>  
  
 <span data-ttu-id="73a84-149">**ライター\<value 2>**</span><span class="sxs-lookup"><span data-stu-id="73a84-149">**Favors \<value 2>**</span></span>  
 <span data-ttu-id="73a84-150">**[値 2]** の予測可能な属性値が優先される度合いを示す、色分けされたバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="73a84-150">Shows a colored bar that indicates how strongly the attribute value favors the predictable attribute value shown in **Value 2**.</span></span>  
  
 [<span data-ttu-id="73a84-151">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="73a84-151">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="73a84-152">参照</span><span class="sxs-lookup"><span data-stu-id="73a84-152">See Also</span></span>  
 <span data-ttu-id="73a84-153">[Microsoft Naive Bayes アルゴリズム](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="73a84-153">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 <span data-ttu-id="73a84-154">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="73a84-154">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="73a84-155">[データマイニングツール](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="73a84-155">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="73a84-156">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="73a84-156">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
