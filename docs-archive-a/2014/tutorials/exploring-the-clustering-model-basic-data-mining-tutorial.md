---
title: クラスターモデルの調査 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cca9d395fece59f607c8faf209128b9d32663a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742721"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a><span data-ttu-id="3d25f-102">クラスター モデルの検証 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="3d25f-102">Exploring the Clustering Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="3d25f-103">クラスタリングアルゴリズムでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 類似した特性を含むクラスターにケースがグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm groups cases into clusters that contain similar characteristics.</span></span> <span data-ttu-id="3d25f-104">このグループ化は、データの探索、データの異常の特定、および予測の作成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-104">These groupings are useful for exploring data, identifying anomalies in the data, and creating predictions.</span></span>  
  
 <span data-ttu-id="3d25f-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] クラスター ビューアーには、クラスタリング マイニング モデルを調べるための次のタブがあります。</span><span class="sxs-lookup"><span data-stu-id="3d25f-105">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Cluster Viewer provides the following tabs for use in exploring clustering mining models:</span></span>  
  

  
##  <a name="cluster-diagram-tab"></a><a name="ClusterDiagramTab"></a><span data-ttu-id="3d25f-106">[クラスターダイアグラム] タブ</span><span class="sxs-lookup"><span data-stu-id="3d25f-106">Cluster Diagram Tab</span></span>  
 <span data-ttu-id="3d25f-107">[クラスター ダイアグラム] タブには、マイニング モデル内のすべてのクラスターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-107">The Cluster Diagram tab displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="3d25f-108">クラスター間を結ぶ線は "緊密度" を表しており、緊密度が高いほど濃い線で表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-108">The lines between the clusters represent "closeness" and are shaded based on how similar the clusters are.</span></span> <span data-ttu-id="3d25f-109">各クラスター本体の色は、クラスター内の変数の頻度と状態を表します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-109">The actual color of each cluster represents the frequency of the variable and the state in the cluster.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a><span data-ttu-id="3d25f-110">[クラスター ダイアグラム] タブでモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="3d25f-110">To explore the model in the Cluster Diagram tab</span></span>  
  
1.  <span data-ttu-id="3d25f-111">[**マイニングモデルビューアー** ] タブの上部にある [**マイニングモデル**] ボックスの一覧を使用すると、モデルに切り替えることが `TM_Clustering` できます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-111">Use the **Mining Model** list at the top of the **Mining Model Viewer** tab to switch to the `TM_Clustering` model.</span></span>  
  
2.  <span data-ttu-id="3d25f-112">[**ビューアー** ] ボックスの一覧で、[ **Microsoft クラスタービューアー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-112">In the **Viewer** list, select **Microsoft Cluster Viewer**.</span></span>  
  
3.  <span data-ttu-id="3d25f-113">[**シェーディング変数**] ボックスで、[**自転車購入**者] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-113">In the **Shading Variable** box, select **Bike Buyer**.</span></span>  
  
     <span data-ttu-id="3d25f-114">既定の変数は**母集団**ですが、モデル内の任意の属性に変更して、必要な属性を持つメンバーを含むクラスターを検出することができます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-114">The default variable is **Population**, but you can change this to any attribute in the model, to discover which clusters contain members that have the attributes you want.</span></span>  
  
4.  <span data-ttu-id="3d25f-115">[**状態**] ボックスで [ **1** ] を選択すると、自転車が購入されたケースを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-115">Select **1** in the **State** box to explore those cases where a bike was purchased.</span></span>  
  
     <span data-ttu-id="3d25f-116">[**密度**] 凡例には、[シェーディング変数] と [状態] で選択した属性の状態の組み合わせの密度が示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-116">The **Density** legend describes the density of the attribute state pair selected in the Shading Variable and the State.</span></span> <span data-ttu-id="3d25f-117">この例では、最も暗い網掛けのある clusterwith 自転車購入者の割合の最高値を示しています。</span><span class="sxs-lookup"><span data-stu-id="3d25f-117">In this example it tells us that the clusterwith the darkest shading has the highest percentage of bike buyers.</span></span>  
  
5.  <span data-ttu-id="3d25f-118">最も色の濃いクラスター上にマウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-118">Pause your mouse over the cluster with the darkest shading.</span></span>  
  
     <span data-ttu-id="3d25f-119">ツールヒントに、属性が `Bike Buyer = 1` であるケースの割合が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-119">A tooltip displays the percentage of cases that have the attribute, `Bike Buyer = 1`.</span></span>  
  
6.  <span data-ttu-id="3d25f-120">密度が最も高いクラスターを選択し、クラスターを右クリックして、[**クラスター名の変更**] を選択し、後で識別できるように「**自転車購入者高**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-120">Select the cluster that has the highest density, right-click the cluster, select **Rename Cluster** and type **Bike Buyers High** for later identification.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="3d25f-121">最も色の薄い (最も密度の低い) クラスターを見つけます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-121">Find the cluster that has the lightest shading (and the lowest density).</span></span> <span data-ttu-id="3d25f-122">クラスターを右クリックし、[**クラスター名の変更**] を選択して、「**自転車購入者低**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-122">Right-click the cluster, select **Rename Cluster** and type **Bike Buyers Low**.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="3d25f-123">[**自転車購入**者率高] クラスターをクリックして、他のクラスターへの接続を明確に表示するペインの領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3d25f-123">Click the **Bike Buyers High** cluster and drag it to an area of the pane that will give you a clear view of its connections to the other clusters.</span></span>  
  
     <span data-ttu-id="3d25f-124">クラスターを選択すると、そのクラスターと別のクラスターをつなぐ線が強調表示され、このクラスターに対するすべての関係を簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-124">When you select a cluster, the lines that connect this cluster to other clusters are highlighted, so that you can easily see all the relationships for this cluster.</span></span> <span data-ttu-id="3d25f-125">クラスターが選択されていないときは、ダイアグラム内にあるすべてのクラスター間の相互関係の度合いを、線の濃さによって確認できます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-125">When the cluster is not selected, you can tell by the darkness of the lines how strong the relationships are amongst all the clusters in the diagram.</span></span> <span data-ttu-id="3d25f-126">網掛けが薄いか存在しない場合は、クラスターがあまり似ていません。</span><span class="sxs-lookup"><span data-stu-id="3d25f-126">If the shading is light or nonexistent, the clusters are not very similar.</span></span>  
  
9. <span data-ttu-id="3d25f-127">ネットワークの左側にあるスライダーを使用して、緊密度の低いリンクを非表示にし、緊密な関係にあるクラスターだけを表示します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-127">Use the slider to the left of the network, to filter out the weaker links and find the clusters with the closest relationships.</span></span> <span data-ttu-id="3d25f-128">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のマーケティング部門は、絞り込みメール配信に最適な方法を決定する際に、類似するクラスターをまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-128">The [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department might want to combine similar clusters together when determining the best method for delivering the targeted mailing.</span></span>  
  

  
##  <a name="cluster-profiles-tab"></a><a name="ClusterProfilesTab"></a><span data-ttu-id="3d25f-129">[クラスターのプロファイル] タブ</span><span class="sxs-lookup"><span data-stu-id="3d25f-129">Cluster Profiles Tab</span></span>  
 <span data-ttu-id="3d25f-130">[**クラスターのプロファイル**] タブには、モデルの全体的なビューが表示され `TM_Clustering` ます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-130">The **Cluster Profiles** tab provides an overall view of the `TM_Clustering` model.</span></span> <span data-ttu-id="3d25f-131">[**クラスターのプロファイル**] タブには、モデル内の各クラスターの列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-131">The **Cluster Profiles** tab contains a column for each cluster in the model.</span></span> <span data-ttu-id="3d25f-132">一番左側の列には、少なくとも 1 つのクラスターに関連付けられているすべての属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-132">The first column lists the attributes that are associated with at least one cluster.</span></span> <span data-ttu-id="3d25f-133">その他の部分には、それぞれのクラスターについて、各属性の状態の分布状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-133">The rest of the viewer contains the distribution of the states of an attribute for each cluster.</span></span> <span data-ttu-id="3d25f-134">離散変数の分布は色分けされたバーとして表示され、最大数のバーが [**ヒストグラム] バー**の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-134">The distribution of a discrete variable is shown as a colored bar with the maximum number of bars displayed in the **Histogram bars** list.</span></span> <span data-ttu-id="3d25f-135">連続属性はダイヤモンド グラフで示されます。このグラフでは、各クラスターの平均と標準偏差を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-135">Continuous attributes are displayed with a diamond chart, which represents the mean and standard deviation in each cluster.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a><span data-ttu-id="3d25f-136">[クラスターのプロファイル] タブでモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="3d25f-136">To explore the model in the Cluster Profiles tab</span></span>  
  
1.  <span data-ttu-id="3d25f-137">**ヒストグラム**バーを**5**に設定します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-137">Set **Histogram** bars to **5**.</span></span>  
  
     <span data-ttu-id="3d25f-138">このモデルでは、1 つの変数に対する状態の最大数が 5 になります。</span><span class="sxs-lookup"><span data-stu-id="3d25f-138">In our model, 5 is the maximum number of states for any one variable.</span></span>  
  
2.  <span data-ttu-id="3d25f-139">[**マイニング凡例**] で**属性プロファイル**の表示がブロックされている場合は、そのまま移動します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-139">If the **Mining Legend** blocks the display of the **Attribute profiles**, move it out of the way.</span></span>  
  
3.  <span data-ttu-id="3d25f-140">[**自転車購入**者率高] 列を選択し、[**母集団**] 列の右側にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3d25f-140">Select the **Bike Buyers High** column and drag it to the right of the **Population** column.</span></span>  
  
4.  <span data-ttu-id="3d25f-141">[**自転車購入**者率低] 列を選択し、[**自転車購入**者率高] 列の右側にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3d25f-141">Select the **Bike Buyers Low** column and drag it to the right of the **Bike Buyers High** column.</span></span>  
  
5.  <span data-ttu-id="3d25f-142">[**自転車購入**者率高] 列をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d25f-142">Click the **Bike Buyers High** column.</span></span>  
  
     <span data-ttu-id="3d25f-143">[**変数**列は、そのクラスターの重要度順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-143">The **Variables** column is sorted in order of importance for that cluster.</span></span> <span data-ttu-id="3d25f-144">列をスクロールし、[自転車購入者率高] クラスターの特性を確認します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-144">Scroll through the column and review characteristics of the Bike Buyer High cluster.</span></span> <span data-ttu-id="3d25f-145">たとえば、多くの場合、このクラスターに属する人は通勤距離が短い傾向にあります。</span><span class="sxs-lookup"><span data-stu-id="3d25f-145">For example, they are more likely to have a short commute.</span></span>  
  
6.  <span data-ttu-id="3d25f-146">[**自転車購入**者率高] 列の [ **Age** ] セルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d25f-146">Double-click the **Age** cell in the **Bike Buyers High** column.</span></span>  
  
     <span data-ttu-id="3d25f-147">[**マイニング凡例**] には、より詳細なビューが表示されます。また、これらの顧客の年齢範囲と平均年齢も表示できます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-147">The **Mining Legend** displays a more detailed view and you can see the age range of these customers as well as the mean age.</span></span>  
  
7.  <span data-ttu-id="3d25f-148">[**自転車購入**者率低] 列を右クリックし、[**列の非表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-148">Right-click the **Bike Buyers Low** column and select **Hide Column**.</span></span>  
  

  
##  <a name="cluster-characteristics-tab"></a><a name="ClusterCharacteristicsTab"></a><span data-ttu-id="3d25f-149">[クラスターの特性] タブ</span><span class="sxs-lookup"><span data-stu-id="3d25f-149">Cluster Characteristics Tab</span></span>  
 <span data-ttu-id="3d25f-150">[**クラスターの特性**] タブでは、クラスターを構成する特性の詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-150">With the **Cluster Characteristics** tab, you can examine in more detail the characteristics that make up a cluster.</span></span> <span data-ttu-id="3d25f-151">([クラスターのプロファイル] タブのように) すべてのクラスターの特性を比較するのではなく、一度に 1 つのクラスターを検証することができます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-151">Instead of comparing the characteristics of all of the clusters (as in the Cluster Profiles tab), you can explore one cluster at a time.</span></span> <span data-ttu-id="3d25f-152">たとえば、[**クラスター** ] ボックスの一覧から [**自転車購入**者率高] を選択した場合、このクラスターの顧客の特性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-152">For example, if you select **Bike Buyers High** from the **Cluster** list, you can see the characteristics of the customers in this cluster.</span></span> <span data-ttu-id="3d25f-153">[クラスターのプロファイル] ビューアーとは表示が異なりますが、結果は同じです。</span><span class="sxs-lookup"><span data-stu-id="3d25f-153">Though the display is different from the Cluster Profiles viewer, the findings are the same.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d25f-154">**Holdoutseed**の初期値を設定しない限り、結果はモデルを処理するたびに変わります。</span><span class="sxs-lookup"><span data-stu-id="3d25f-154">Unless you set an initial value for **holdoutseed**, results will vary each time you process the model.</span></span> <span data-ttu-id="3d25f-155">詳細については、「 [HoldoutSeed 要素](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d25f-155">For more information, see [HoldoutSeed Element](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)</span></span>  
  

  
##  <a name="cluster-discrimination-tab"></a><a name="ClusterDiscriminationTab"></a><span data-ttu-id="3d25f-156">[クラスターの識別] タブ</span><span class="sxs-lookup"><span data-stu-id="3d25f-156">Cluster Discrimination Tab</span></span>  
 <span data-ttu-id="3d25f-157">[**クラスターの識別**] タブでは、あるクラスターと別のクラスターを区別する特性を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-157">With the **Cluster Discrimination** tab, you can explore the characteristics that distinguish one cluster from another.</span></span> <span data-ttu-id="3d25f-158">**クラスター 1**の一覧から2つのクラスターを選択し、クラスター **2**の一覧からクラスターを選択すると、ビューアーによってクラスター間の相違が計算され、クラスターを最もよく区別する属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-158">After you select two clusters, one from the **Cluster 1** list, and one from the **Cluster 2** list, the viewer calculates the differences between the clusters and displays a list of the attributes that distinguish the clusters most.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a><span data-ttu-id="3d25f-159">[クラスターの識別] タブでモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="3d25f-159">To explore the model in the Cluster Discrimination tab</span></span>  
  
1.  <span data-ttu-id="3d25f-160">[**クラスター 1** ] ボックスで、[**自転車購入**者率高] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-160">In the **Cluster 1** box, select **Bike Buyers High**.</span></span>  
  
2.  <span data-ttu-id="3d25f-161">[**クラスター 2** ] ボックスで、[**自転車購入者低**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3d25f-161">In the **Cluster 2** box, select **Bike Buyers Low**.</span></span>  
  
3.  <span data-ttu-id="3d25f-162">[**変数**] をクリックしてアルファベット順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="3d25f-162">Click **Variables** to sort alphabetically.</span></span>  
  
     <span data-ttu-id="3d25f-163">**自転車購入者低**および**自転車購入**者の高いクラスターでは、年齢、車の所有権、子供の数、地域など、より大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="3d25f-163">Some of the more substantial differences among the customers in the **Bike Buyers Low** and **Bike Buyers High** clusters include age, car ownership, number of children, and region.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3d25f-164">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3d25f-164">Related Tasks</span></span>  
 <span data-ttu-id="3d25f-165">他のマイニング モデルを探索するには、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d25f-165">See the following topics to explore the other mining models.</span></span>  
  
-   [<span data-ttu-id="3d25f-166">デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="3d25f-166">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="3d25f-167">Naive Bayes Model &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="3d25f-167">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3d25f-168">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="3d25f-168">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3d25f-169">Naive Bayes Model &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="3d25f-169">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="3d25f-170">このレッスンの前の作業</span><span class="sxs-lookup"><span data-stu-id="3d25f-170">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="3d25f-171">デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="3d25f-171">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="3d25f-172">参照</span><span class="sxs-lookup"><span data-stu-id="3d25f-172">See Also</span></span>  
 <span data-ttu-id="3d25f-173">[Microsoft クラスタービューアーを使用したモデルの参照](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="3d25f-173">[Browse a Model Using the Microsoft Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md) </span></span>  
 <span data-ttu-id="3d25f-174">[[クラスターの識別] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="3d25f-174">[Cluster Discrimination Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="3d25f-175">[[クラスターのプロファイル] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="3d25f-175">[Cluster Profiles Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="3d25f-176">[[クラスターの特性] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="3d25f-176">[Cluster Characteristics Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="3d25f-177">[[クラスターダイアグラム] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="3d25f-177">[Cluster Diagram Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)</span></span>  
  
  
