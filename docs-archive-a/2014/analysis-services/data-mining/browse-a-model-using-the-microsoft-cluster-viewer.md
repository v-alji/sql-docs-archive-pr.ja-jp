---
title: Microsoft クラスタービューアーを使用したモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clusters [Analysis Services]
- discrimination [Analysis Services]
- names [Analysis Services], clusters
- Microsoft Cluster Viewer
- mining model content, viewing
- comparing clusters
- viewing clusters
- displaying clusters
- data mining [Analysis Services], clusters
- Cluster Viewer [Analysis Services]
- mining models [Analysis Services], clusters
ms.assetid: 591fe30b-d88f-4a71-94d4-4a3907fc275d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d3597c97ad285d8ddc40b398723f6d3ec652ceb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645288"
---
# <a name="browse-a-model-using-the-microsoft-cluster-viewer"></a><span data-ttu-id="23327-102">「Microsoft クラスター ビューアーを使用したモデルの参照」</span><span class="sxs-lookup"><span data-stu-id="23327-102">Browse a Model Using the Microsoft Cluster Viewer</span></span>
  <span data-ttu-id="23327-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]のクラスタービューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] クラスタリングアルゴリズムを使用して作成されたマイニングモデルが表示され [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="23327-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="23327-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムは、データの異常を特定したり予測を作成したりするときにデータを調べるための分割アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="23327-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm is a segmentation algorithm for use in exploring data to identify anomalies in the data and to create predictions.</span></span> <span data-ttu-id="23327-105">このアルゴリズムの詳細については、「 [Microsoft クラスタリング アルゴリズム](microsoft-clustering-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23327-105">For more information about this algorithm, see [Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23327-106">モデルで使用された式と、検出されたパターンの詳細情報を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用します。</span><span class="sxs-lookup"><span data-stu-id="23327-106">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="23327-107">詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](../microsoft-generic-content-tree-viewer-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23327-107">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="23327-108">ビューアーのタブ</span><span class="sxs-lookup"><span data-stu-id="23327-108">Viewer Tabs</span></span>  
 <span data-ttu-id="23327-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-109">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="23327-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスター ビューアーには、クラスタリング マイニング モデルを調べるための次のタブがあります。</span><span class="sxs-lookup"><span data-stu-id="23327-110">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer provides the following tabs for use in exploring clustering mining models:</span></span>  
  
-   [<span data-ttu-id="23327-111">クラスター ダイアグラム</span><span class="sxs-lookup"><span data-stu-id="23327-111">Cluster Diagram</span></span>](#BKMK_Diagram)  
  
-   [<span data-ttu-id="23327-112">クラスターのプロファイル</span><span class="sxs-lookup"><span data-stu-id="23327-112">Cluster Profiles</span></span>](#BKMK_Profile)  
  
-   [<span data-ttu-id="23327-113">クラスターの特性</span><span class="sxs-lookup"><span data-stu-id="23327-113">Cluster Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="23327-114">クラスターの識別</span><span class="sxs-lookup"><span data-stu-id="23327-114">Cluster Discrimination</span></span>](#BKMK_Discrimination)  
  
###  <a name="cluster-diagram"></a><a name="BKMK_Diagram"></a><span data-ttu-id="23327-115">クラスターダイアグラム</span><span class="sxs-lookup"><span data-stu-id="23327-115">Cluster Diagram</span></span>  
 <span data-ttu-id="23327-116">**クラスター ビューアーの** [クラスター ダイアグラム] [!INCLUDE[msCoName](../../includes/msconame-md.md)] タブには、マイニング モデル内のすべてのクラスターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-116">The **Cluster Diagram** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="23327-117">クラスター間を結ぶ線の網掛けは、クラスターの類似性の強度を表します。</span><span class="sxs-lookup"><span data-stu-id="23327-117">The shading of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="23327-118">網掛けが薄いか存在しない場合は、クラスターがあまり似ていません。</span><span class="sxs-lookup"><span data-stu-id="23327-118">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="23327-119">線の網掛けが濃くなるほど、リンクの類似性も強くなります。</span><span class="sxs-lookup"><span data-stu-id="23327-119">As the line becomes darker, the similarity of the links becomes stronger.</span></span> <span data-ttu-id="23327-120">ビューアーに表示される線の数は、クラスターの右側のスライダーを使用して調整できます。</span><span class="sxs-lookup"><span data-stu-id="23327-120">You can adjust how many lines the viewer shows by adjusting the slider to the right of the clusters.</span></span> <span data-ttu-id="23327-121">スライダーを小さく設定すると、緊密なリンクのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-121">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="23327-122">既定では、網掛けはクラスターの母集団を表します。</span><span class="sxs-lookup"><span data-stu-id="23327-122">By default, the shade represents the population of the cluster.</span></span> <span data-ttu-id="23327-123">**ShadingVariable**および**state**オプションを使用すると、網掛けによって表される属性と状態の組み合わせを選択できます。</span><span class="sxs-lookup"><span data-stu-id="23327-123">By using the **ShadingVariable** and **State** options, you can select which attribute and state pair the shading represents.</span></span> <span data-ttu-id="23327-124">網掛けが濃いほど、対応する状態の属性分布は広くなります。</span><span class="sxs-lookup"><span data-stu-id="23327-124">The darker the shading, the greater the attribute distribution is for a specific state.</span></span> <span data-ttu-id="23327-125">網掛けが薄くなるほど、分布は狭くなります。</span><span class="sxs-lookup"><span data-stu-id="23327-125">The distribution decreases as the shading gets lighter.</span></span>  
  
 <span data-ttu-id="23327-126">クラスターの名前を変更するには、そのノードを右クリックして **[クラスター名の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="23327-126">To rename a cluster, right-click its node and select **Rename Cluster**.</span></span> <span data-ttu-id="23327-127">新しい名前はサーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="23327-127">The new name is persisted to the server.</span></span>  
  
 <span data-ttu-id="23327-128">ダイアグラムの表示部分をクリップボードにコピーするには、 **[グラフ ビューのコピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23327-128">To copy the visible section of the diagram to the Clipboard, click **Copy Graph View**.</span></span> <span data-ttu-id="23327-129">ダイアグラム全体をコピーするには、 **[グラフ全体のコピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23327-129">To copy the complete diagram, click **Copy Entire Graph**.</span></span> <span data-ttu-id="23327-130">**[拡大]** と **[縮小]** を使用してダイアグラムを拡大または縮小することも、 **[ウィンドウに合わせてダイアグラムの倍率を変更します]** を使用してダイアグラムを画面に合わせて調整することもできます。</span><span class="sxs-lookup"><span data-stu-id="23327-130">You can also zoom in and out by using **Zoom In** and **Zoom Out**, or you can fit the diagram to the screen by using **Scale Diagram to Fit in Window**.</span></span>  
  
 [<span data-ttu-id="23327-131">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="23327-131">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_Profile"></a> <span data-ttu-id="23327-132">クラスターのプロファイル</span><span class="sxs-lookup"><span data-stu-id="23327-132">Cluster Profiles</span></span>  
 <span data-ttu-id="23327-133">**[クラスターのプロファイル]** タブには、モデルのアルゴリズムによって作成されるクラスターの概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-133">The **Cluster Profiles** tab provides an overall view of the clusters that the algorithm in your model creates.</span></span> <span data-ttu-id="23327-134">このビューには、各クラスター内の属性の分布と共に各属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-134">This view displays each attribute, together with the distribution of the attribute in each cluster.</span></span> <span data-ttu-id="23327-135">各セルのヒントには分布統計が表示され、各列見出しのヒントにはクラスターの母集団が表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-135">An InfoTip for each cell displays the distribution statistics, and an InfoTip for each column heading displays the cluster population.</span></span> <span data-ttu-id="23327-136">不連続属性は色分けされたバーとして表示され、連続属性は各クラスター内の平均偏差および標準偏差を表すダイヤモンド チャートとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-136">Discrete attributes are shown as colored bars, and continuous attributes are shown as a diamond chart that represents the mean and standard deviation in each cluster.</span></span> <span data-ttu-id="23327-137">**[ヒストグラム バー]** オプションでは、ヒストグラムに表示されるバーの数を制御します。</span><span class="sxs-lookup"><span data-stu-id="23327-137">The **Histogram bars** option controls the number of bars that are visible in the histogram.</span></span> <span data-ttu-id="23327-138">指定した数よりも多くのバーが存在する場合は、重要度が最も高いバーが保持され、残りのバーは灰色のバケットにまとめられます。</span><span class="sxs-lookup"><span data-stu-id="23327-138">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into a gray bucket.</span></span>  
  
 <span data-ttu-id="23327-139">クラスターの既定の名前は、よりわかりやすい名前に変更できます。</span><span class="sxs-lookup"><span data-stu-id="23327-139">You can change the default names of the clusters, to make the names more descriptive.</span></span> <span data-ttu-id="23327-140">クラスター名を変更するには、クラスターの列見出しを右クリックして、 **[クラスター名の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="23327-140">Rename a cluster by right-clicking its column heading and selecting **Rename cluster**.</span></span> <span data-ttu-id="23327-141">**[列の非表示]** を選択すると、クラスターを非表示にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="23327-141">You can also hide clusters by selecting **Hide column**.</span></span>  
  
 <span data-ttu-id="23327-142">より広範かつ詳細なクラスターのビューをウィンドウで開くには、 **[状態]** 列のセルまたはビューアーのヒストグラムをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="23327-142">To open a window that provides a larger, more detailed view of the clusters, double-click either a cell in the **States** column or a histogram in the viewer.</span></span>  
  
 <span data-ttu-id="23327-143">そのクラスターの属性を重要度順に並べ替えるには、列見出しをクリックします。</span><span class="sxs-lookup"><span data-stu-id="23327-143">Click a column heading to sort the attributes in order of importance for that cluster.</span></span> <span data-ttu-id="23327-144">列をドラッグして、ビューアーでの順序を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="23327-144">You can also drag columns to reorder them in the viewer.</span></span>  
  
 [<span data-ttu-id="23327-145">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="23327-145">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_Characteristics"></a> <span data-ttu-id="23327-146">クラスターの特性</span><span class="sxs-lookup"><span data-stu-id="23327-146">Cluster Characteristics</span></span>  
 <span data-ttu-id="23327-147">**[クラスターの特性]** タブを使用するには、 **[クラスター]** 一覧でクラスターを選択します。</span><span class="sxs-lookup"><span data-stu-id="23327-147">To use the **Cluster Characteristics** tab, select a cluster from the **Cluster** list.</span></span> <span data-ttu-id="23327-148">クラスターを選択した後、そのクラスターを構成する特性を検証することができます。</span><span class="sxs-lookup"><span data-stu-id="23327-148">After you select a cluster, you can examine the characteristics that make up that specific cluster.</span></span> <span data-ttu-id="23327-149">クラスターに含まれている属性は **[変数]** 列に表示され、属性の状態は **[値]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-149">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span> <span data-ttu-id="23327-150">属性の状態は、それがクラスターに表示される確率によって表され、重要度の順に並んでいます。</span><span class="sxs-lookup"><span data-stu-id="23327-150">Attribute states are listed in order of importance, described by the probability that they will appear in the cluster.</span></span> <span data-ttu-id="23327-151">確率は **[確率]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-151">The probability is shown in the **Probability** column.</span></span>  
  
 [<span data-ttu-id="23327-152">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="23327-152">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_Discrimination"></a><span data-ttu-id="23327-153">クラスターの識別</span><span class="sxs-lookup"><span data-stu-id="23327-153">Cluster Discrimination</span></span>  
 <span data-ttu-id="23327-154">**[クラスターの識別]** タブを使用すると、2 つのクラスター間で属性を比較できます。</span><span class="sxs-lookup"><span data-stu-id="23327-154">You can use the **Cluster Discrimination** tab to compare attributes between two clusters.</span></span> <span data-ttu-id="23327-155">**[クラスター 1]** と **[クラスター 2]** の一覧を使用して、比較するクラスターを選択します。</span><span class="sxs-lookup"><span data-stu-id="23327-155">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span> <span data-ttu-id="23327-156">クラスター間の最も重要な差異がビューアーによって決定され、その差異に関連付けられた属性の状態が重要度順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="23327-156">The viewer determines the most important differences between the clusters, and displays the attribute states that are associated with the differences, in order of importance.</span></span> <span data-ttu-id="23327-157">属性の右側のバーには、どのクラスターがその状態で優先されているかが示され、その状態がクラスターを優先する度合いがバーのサイズによって表されます。</span><span class="sxs-lookup"><span data-stu-id="23327-157">A bar to the right of the attribute shows which cluster the state favors, and the size of the bar shows how strongly the state favors the cluster.</span></span>  
  
 [<span data-ttu-id="23327-158">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="23327-158">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="23327-159">参照</span><span class="sxs-lookup"><span data-stu-id="23327-159">See Also</span></span>  
 <span data-ttu-id="23327-160">[Microsoft クラスタリングアルゴリズム](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="23327-160">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="23327-161">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="23327-161">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="23327-162">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="23327-162">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="23327-163">[データマイニングツール](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="23327-163">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="23327-164">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="23327-164">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
