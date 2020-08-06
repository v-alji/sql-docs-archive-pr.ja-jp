---
title: シーケンスクラスターモデルの検証 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f8a485d5-47ed-4dd5-bb66-ef4d6d463845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bac603d2480ec1f344d14351757027de749f8c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720492"
---
# <a name="exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="0c73e-102">シーケンス クラスター モデルの検証 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="0c73e-102">Exploring the Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="0c73e-103">ここまでで、リージョンモデル**を使用してシーケンスクラスター**を構築しました。次は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] データマイニングデザイナーの [**マイニングモデルビューアー** ] タブにあるシーケンスクラスタービューアーを使用して、シーケンスクラスターを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-103">Now that you have built the **Sequence Clustering with Region** model, you can explore it by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering Viewer in the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="0c73e-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]シーケンスクラスタービューアーには、**クラスターダイアグラム**、クラスターの**プロファイル**、**クラスターの特性**、 **clusterdiscrimination**、**状態遷移**の5つのタブがあります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Cluster Viewer contains five tabs: **Cluster Diagram**, **Cluster Profiles**, **Cluster Characteristics**, **ClusterDiscrimination**, and **State Transitions**.</span></span> <span data-ttu-id="0c73e-105">このビューアーの使用方法の詳細については、「 [Microsoft シーケンスクラスタービューアーを使用したモデルの参照](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c73e-105">For more information about how to use this viewer, see [Browse a Model Using the Microsoft Sequence Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md).</span></span>  
  
-   <span data-ttu-id="0c73e-106">[[クラスターダイアグラム] タブ](#bkmk_CDiagram)</span><span class="sxs-lookup"><span data-stu-id="0c73e-106">[Cluster Diagram tab](#bkmk_CDiagram)</span></span>  
  
-   <span data-ttu-id="0c73e-107">[[クラスターのプロファイル] タブ](#bkmk_CProfiles)</span><span class="sxs-lookup"><span data-stu-id="0c73e-107">[Cluster Profiles tab](#bkmk_CProfiles)</span></span>  
  
-   <span data-ttu-id="0c73e-108">[[クラスターの特性] タブ](#bkmk_CChars)</span><span class="sxs-lookup"><span data-stu-id="0c73e-108">[Cluster Characteristics tab](#bkmk_CChars)</span></span>  
  
-   <span data-ttu-id="0c73e-109">[[クラスターの識別] タブ](#bkmk_CDiscrim2)</span><span class="sxs-lookup"><span data-stu-id="0c73e-109">[Cluster Discrimination tab](#bkmk_CDiscrim2)</span></span>  
  
-   <span data-ttu-id="0c73e-110">[[状態遷移] タブ](#bkmk_StateTran)</span><span class="sxs-lookup"><span data-stu-id="0c73e-110">[State Transitions tab](#bkmk_StateTran)</span></span>  
  
-   [<span data-ttu-id="0c73e-111">汎用コンテンツ ツリー ビューアー</span><span class="sxs-lookup"><span data-stu-id="0c73e-111">Generic Content View</span></span>](#bkmk_Generic)  
  
##  <a name="cluster-diagram-tab"></a><a name="bkmk_CDiagram"></a><span data-ttu-id="0c73e-112">[クラスターダイアグラム] タブ</span><span class="sxs-lookup"><span data-stu-id="0c73e-112">Cluster Diagram Tab</span></span>  
 <span data-ttu-id="0c73e-113">[**クラスターダイアグラム**] タブには、アルゴリズムによってデータベースで検出されたクラスターがグラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-113">The **Cluster Diagram** tab graphically displays the clusters that the algorithm discovered in the database.</span></span> <span data-ttu-id="0c73e-114">ダイアグラムのレイアウトは、類似するクラスターを緊密にグループ化したクラスターのリレーションシップを表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-114">The layout in the diagram represents the relationships of the clusters, with similar clusters grouped close together.</span></span> <span data-ttu-id="0c73e-115">既定では、各ノードの色の濃さはクラスターに存在するケースの密度を表し、ノード色が濃くなるほど多数のケースが存在することになります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-115">By default, the shade of each node represents the density of all cases in the cluster: the darker the shade of the node, the more cases it contains.</span></span> <span data-ttu-id="0c73e-116">ノードの色の濃さが各クラスター内の属性や状態のサポートを表すように、設定を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-116">You can change the meaning of the shading of the nodes so that it represents support, within each cluster, for an attribute and a state.</span></span>  
  
 <span data-ttu-id="0c73e-117">目的のクラスターを簡単に識別したり操作したりできるようにクラスターの名前を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-117">You can also rename the clusters, to make it easier to identify and work with target clusters.</span></span> <span data-ttu-id="0c73e-118">このチュートリアルでは、太平洋地域の顧客の割合が最も高いクラスターと全体のケースの数が最も多いクラスターの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-118">For this tutorial, you will rename the cluster that has the highest percentage of customers from the Pacific region, and the cluster that has the most cases overall.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c73e-119">データとモデル パラメーターによっては、モデルを再処理したときに、特定のクラスターに割り当てられたケースが変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-119">The cases that are assigned to specific clusters might change when you reprocess the model, depending on the data and the model parameters.</span></span> <span data-ttu-id="0c73e-120">また、クラスターの名前を変更した場合、それらの名前は、マイニング モデルを再処理すると失われます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-120">Also, if you rename clusters, the names will be lost when you reprocess the mining model.</span></span>  
  
#### <a name="to-change-the-attribute-used-for-highlighting-clusters"></a><span data-ttu-id="0c73e-121">クラスターを強調表示するために使用される属性を変更するには</span><span class="sxs-lookup"><span data-stu-id="0c73e-121">To change the attribute used for highlighting clusters</span></span>  
  
1.  <span data-ttu-id="0c73e-122">[**シェーディング変数**] ボックスの一覧で、[**モデル**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-122">In the **Shading Variable** list, select **Model**.</span></span>  
  
2.  <span data-ttu-id="0c73e-123">[**状態**] ボックスの一覧で [**サイクルの上限**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-123">Select **Cycling Cap** in the **State** list.</span></span>  
  
     <span data-ttu-id="0c73e-124">ダイアグラムが更新されて、選択した製品の各クラスターにおける集中度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-124">The diagram updates to show the concentration of the selected product in each of the clusters.</span></span> <span data-ttu-id="0c73e-125">最も色の濃いクラスターに、サイクリング キャップが最も高い密度で含まれます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-125">The cluster that has the darkest shading contains the highest density of cycling caps.</span></span> <span data-ttu-id="0c73e-126">任意の入力列の任意の状態を使用するように、シェーディング変数を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-126">You can change the shading variable to use any state of any input column.</span></span>  
  
3.  <span data-ttu-id="0c73e-127">[**網掛け変数**] の一覧で、[**母集団**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-127">In the **Shading Variable** list, select **Population**.</span></span>  
  
     <span data-ttu-id="0c73e-128">シェーディング変数を母集団に変更すると、ダイアグラムが更新されて、クラスターがサイズで比較されるようになります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-128">When you change the shading variable to population, the diagram updates to compare the clusters by size.</span></span> <span data-ttu-id="0c73e-129">最も色の濃いクラスターに最も多くのケースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c73e-129">The cluster that has the darkest shading contains more cases than the other clusters.</span></span>  
  
#### <a name="to-rename-nodes-in-the-model"></a><span data-ttu-id="0c73e-130">モデルのノードの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="0c73e-130">To rename nodes in the model</span></span>  
  
1.  <span data-ttu-id="0c73e-131">**シェーディング変数**をに変更 `Region` し、 **State**を**太平洋**に設定します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-131">Change **Shading Variable** to `Region`, and set **State** to **Pacific**.</span></span>  
  
2.  <span data-ttu-id="0c73e-132">グラフで最も色の濃いノードを強調表示させます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-132">Highlight the darkest node in the graph.</span></span>  
  
3.  <span data-ttu-id="0c73e-133">このクラスターを右クリックし、[**クラスター名の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-133">Right-click this cluster and select **Rename Cluster.**</span></span>  
  
4.  <span data-ttu-id="0c73e-134">「太平洋クラスター」という名前を入力し**ます。**</span><span class="sxs-lookup"><span data-stu-id="0c73e-134">Type the name**Pacific Cluster.**</span></span>  
  
5.  <span data-ttu-id="0c73e-135">[**シェーディング変数**の値を**母集団**に変更します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-135">Change the value of **Shading Variable** to **Population**.</span></span>  
  
6.  <span data-ttu-id="0c73e-136">更新されたグラフで、最も色の濃いクラスター (最も大きなクラスター) を見つけます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-136">In the updated graph, locate the darkest cluster, which should be the largest cluster.</span></span> <span data-ttu-id="0c73e-137">色の濃さからはどのクラスターが最も大きいか判断できない場合は、各クラスターの上にマウス ポインターを置いてツールヒントを確認し、最も多くのケースが含まれているクラスターを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-137">If you cannot tell by the shading which cluster is largest, pause the mouse over each cluster and view the ToolTip, and then choose the cluster that contains the most cases.</span></span>  
  
7.  <span data-ttu-id="0c73e-138">このクラスターを右クリックし、[**クラスター名の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-138">Right-click this cluster and select **Rename Cluster**.</span></span> <span data-ttu-id="0c73e-139">新しい名前を入力し `Largest Cluster` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-139">Type the new name, `Largest Cluster`.</span></span>  
  
 <span data-ttu-id="0c73e-140">クラスターを表すノードからドリルスルーして、各クラスター内のケースの詳細を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-140">You can drill through from the node that represents the cluster to view details of the cases that are in each cluster.</span></span> <span data-ttu-id="0c73e-141">たとえば、顧客に電子メールを送信するなど、分析の結果に対して操作を実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="0c73e-141">This can be useful if you want to take action on the results of your analysis, such as sending e-mail to a customer.</span></span> <span data-ttu-id="0c73e-142">構造には含まれているがモデルでは使用されていない、ケースのその他の属性を参照することもできます (Region や IncomeGroup など)。</span><span class="sxs-lookup"><span data-stu-id="0c73e-142">You can also browse the other attributes of the cases that you included in the structure but did not use in the model, such as Region and IncomeGroup.</span></span> <span data-ttu-id="0c73e-143">マイニングモデルから基になるケースへのドリルスルーの詳細については、「[データマイニング&#41;&#40;のドリルスルークエリ](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c73e-143">For more information about drilling through from mining models to the underlying cases, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-drill-through-to-details-from-the-cluster-diagram"></a><span data-ttu-id="0c73e-144">クラスター ダイアグラムから詳細情報にドリルスルーするには</span><span class="sxs-lookup"><span data-stu-id="0c73e-144">To drill through to details from the Cluster diagram</span></span>  
  
1.  <span data-ttu-id="0c73e-145">右クリックし `Pacific Cluster` て [**ドリルスルー**] を選択し、[**モデルおよび構造列**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-145">Right-click `Pacific Cluster`, select **Drill Through**, and then select **Model and Structure columns**.</span></span>  
  
     <span data-ttu-id="0c73e-146">[**ドリルスルー** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-146">The **Drill Through** dialog box opens.</span></span> <span data-ttu-id="0c73e-147">モデルで使用されていないが、クエリに使用できる列には、**構造体**がプレフィックスとして付けられます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-147">Columns that are not used in the model but that are available for querying are prefixed with **Structure**.</span></span>  
  
     <span data-ttu-id="0c73e-148">このクラスターに含まれている顧客はほとんどが太平洋地域の顧客で、その他の地域の顧客はごくわずかであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-148">You can see that this cluster contains mostly customers from the Pacific region, with only a few customers from other regions.</span></span>  
  
2.  <span data-ttu-id="0c73e-149">入れ子になった列 v Assoc Seq Line Items のプラス記号をクリックして、特定の顧客注文のアイテムのシーケンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-149">Click the plus sign in the nested column v Assoc Seq Line Items to view the sequence of items in a particular customer order.</span></span>  
  
3.  <span data-ttu-id="0c73e-150">[**ドリルスルー** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-150">Close the **Drill Through** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c73e-151">[**再生**] ボタンを使用すると、データを再クエリできます。ただし、他のプロセスによってバックグラウンドで動的に更新されていない限り、再クエリを行っても、表示されるデータは変更されません。</span><span class="sxs-lookup"><span data-stu-id="0c73e-151">The **Play** button enables you to requery the data; however, requerying does not change the data that is displayed, unless the model has been dynamically updated in the background by some other process.</span></span>  
  
 [<span data-ttu-id="0c73e-152">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0c73e-152">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-profiles-tab"></a><a name="bkmk_CProfiles"></a><span data-ttu-id="0c73e-153">[クラスターのプロファイル] タブ</span><span class="sxs-lookup"><span data-stu-id="0c73e-153">Cluster Profiles Tab</span></span>  
 <span data-ttu-id="0c73e-154">[**クラスターのプロファイル**] タブには、各クラスター内のシーケンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-154">The **Cluster Profiles** tab displays the sequences that are in each cluster.</span></span> <span data-ttu-id="0c73e-155">クラスターは、[ **States (状態**)」列の右側にある個々の列に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-155">The clusters are listed in individual columns to the right of the **States** column.</span></span>  
  
 <span data-ttu-id="0c73e-156">ビューアーでは、**モデル**の行にはクラスター内の項目の全体的な分布が記述され、[**サンプル**] 行には項目のシーケンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-156">In the viewer, the **Model** row describes the overall distribution of items in a cluster, and the **Model.samples** row contains sequences of the items.</span></span> <span data-ttu-id="0c73e-157">モデルの各セルのカラーシーケンスの各行。サンプル行は、クラスター内でランダムに選択されたユーザーの動作を表し**ます。**</span><span class="sxs-lookup"><span data-stu-id="0c73e-157">Each line of the color sequences in each cell of the **Model.samples** row represents the behavior of a randomly selected user in the cluster.</span></span>  
  
 <span data-ttu-id="0c73e-158">シーケンス ヒストグラムでは、各製品モデルがそれぞれ異なる色で示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-158">Each color in an individual sequence histogram represents a product model.</span></span> <span data-ttu-id="0c73e-159">マイニング凡例は、色分けと製品モデル名の両方を使用して製品のシーケンスを表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-159">The Mining Legend shows you the sequences of products by using both color-coding and the product model names.</span></span> <span data-ttu-id="0c73e-160">クラスターのモデルにその他の列 (Region や Income Group など) を追加した場合は、各列に対応する追加の行がビューアーに含まれます。それらの行には、各クラスター内のそれらの値の分布が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-160">If you have added other columns to the model for clustering, such as Region or Income Group, the viewer will contain an additional row for each column that shows the distribution of these values within each cluster.</span></span>  
  
#### <a name="to-view-the-sequences-that-are-most-common-in-a-cluster"></a><span data-ttu-id="0c73e-161">クラスターで最も一般的なシーケンスを表示するには</span><span class="sxs-lookup"><span data-stu-id="0c73e-161">To view the sequences that are most common in a cluster</span></span>  
  
1.  <span data-ttu-id="0c73e-162">クラスターの列の**モデル**行を右クリック `Largest Cluster` し、[凡例の**表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-162">Right-click the **Model** row in the column for the cluster `Largest Cluster`, and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="0c73e-163">**Color**列には、シーケンス内で見つかった項目の頻度を示す、網掛けされたバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c73e-163">The **Color** column contains a shaded bar that indicates the frequency of items found in sequences.</span></span> <span data-ttu-id="0c73e-164">各アイテムがそれぞれ異なる色で表されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-164">Each item is represented by a different color.</span></span> <span data-ttu-id="0c73e-165">[**意味**列には、各色の製品モデル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-165">The **Meaning** column lists the product model names for each color.</span></span> <span data-ttu-id="0c73e-166">[**分布**] 列には、この項目がシーケンスに含まれていたケースの割合が示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-166">The **Distribution** column tells you the percentage of cases that contained this item in a sequence.</span></span>  
  
2.  <span data-ttu-id="0c73e-167">[**マイニング凡例**] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-167">Close the **Mining Legend**.</span></span>  
  
3.  <span data-ttu-id="0c73e-168">列の [母集団] 行を右クリックし、[**人口\*\*\*\*凡例**] を選択します **。**</span><span class="sxs-lookup"><span data-stu-id="0c73e-168">Right-click the **Model.samples** row in the column with the heading, **Population,** and select **Show Legend**.</span></span>  
  
4.  <span data-ttu-id="0c73e-169">モデル全体のシーケンスの一覧をスキャンする`.`</span><span class="sxs-lookup"><span data-stu-id="0c73e-169">Scan the list of sequences in the overall model`.`</span></span>  
  
     <span data-ttu-id="0c73e-170">マイニング凡例では最も一般的なシーケンスが最初に表示されるため、多くのシーケンスで Mountain Tire Tube が最初のアイテムになっていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-170">The Mining Legend lists the most common sequences first, so you can see that Mountain Tire Tube is the first item in many sequences.</span></span> <span data-ttu-id="0c73e-171">これは、Mountain Tire Tube を最初に買い物かごに入れる顧客が多いことを示しています。</span><span class="sxs-lookup"><span data-stu-id="0c73e-171">This means that a customer is very likely to put the Mountain Tire Tube in the shopping basket first.</span></span>  
  
#### <a name="to-drill-through-to-cases-from-the-cluster-viewer"></a><span data-ttu-id="0c73e-172">クラスター ビューアーからケースにドリルスルーするには</span><span class="sxs-lookup"><span data-stu-id="0c73e-172">To drill through to cases from the cluster viewer</span></span>  
  
1.  <span data-ttu-id="0c73e-173">属性の行が見つかるまで、[属性] ペインを下にスクロールし `Region` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-173">Scroll down in the Attribute pane until you find the row for the `Region` attribute.</span></span>  
  
     <span data-ttu-id="0c73e-174">この行には、モデル内の各クラスターのヒストグラムに加えて、モデルで使用されたケースのセット全体を表す、**母集団**のヒストグラムが1つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c73e-174">The row contains a histogram for each cluster in the model, plus one additional histogram for **Population**, meaning the entire set of cases used in the model.</span></span> <span data-ttu-id="0c73e-175">ヒストグラムとは、さまざまな色を含むバーで、それぞれの色が属性を表し、色の付いた部分のサイズがその色の属性を持つケースの割合を表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-175">A histogram is a bar with different colors in it, where each color represents an attribute, and the size of the colored section for that attribute represents the percentage of cases with that attribute.</span></span>  
  
2.  <span data-ttu-id="0c73e-176">名前を変更したクラスターとのヒストグラムを比較し `Pacific Cluster` `Largest Cluster` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-176">Compare the histograms for the clusters that you renamed `Pacific Cluster` and `Largest Cluster`.</span></span> <span data-ttu-id="0c73e-177">各クラスターはそれぞれ異なる列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-177">Each cluster appears in a different column.</span></span>  
  
     <span data-ttu-id="0c73e-178">どちらも単色に見えますが、同じ色ではありません。</span><span class="sxs-lookup"><span data-stu-id="0c73e-178">Both look like solid colors, but the colors are different.</span></span>  
  
3.  <span data-ttu-id="0c73e-179">行内で `Region` 、の色分けされたヒストグラムの上にマウスポインターを置き `Largest Cluster` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-179">In the `Region` row, pause the mouse over the colored histogram for `Largest Cluster`.</span></span>  
  
     <span data-ttu-id="0c73e-180">各地域のケースの実際の割合を示す値がツールヒントに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-180">The ToolTip displays values that show the actual percentages of cases from each region.</span></span>  
  
4.  <span data-ttu-id="0c73e-181">の行で色分けされたヒストグラムを右クリックし `Region` `Pacific Cluster` 、[**ドリルスルー**] を選択して、[**モデル列のみ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-181">Right-click the colored histogram in the `Region` row for `Pacific Cluster`, select **Drill Through**, and then select **Model Columns Only**.</span></span>  
  
5.  <span data-ttu-id="0c73e-182">スクロール バーを動かして、このクラスターのすべての顧客を調べます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-182">Move the scroll bar to review all of the customers in this cluster.</span></span>  
  
     <span data-ttu-id="0c73e-183">詳細情報にドリルスルーした結果からは、クラスターに含まれている注文のほとんどが太平洋地域からの注文であっても、北米地域やヨーロッパ地域からの注文もわずかに含まれていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-183">Again, from drilling through to the details you can see that the cluster contains mostly orders from the Pacific region but also a few from the North America and Europe regions.</span></span>  
  
6.  <span data-ttu-id="0c73e-184">[**ドリルスルー** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-184">Close the **Drill Through** dialog box.</span></span>  
  
 [<span data-ttu-id="0c73e-185">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0c73e-185">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-characteristics-tab"></a><a name="bkmk_CChars"></a><span data-ttu-id="0c73e-186">[クラスターの特性] タブ</span><span class="sxs-lookup"><span data-stu-id="0c73e-186">Cluster Characteristics Tab</span></span>  
 <span data-ttu-id="0c73e-187">[**クラスターの特性**] タブには、選択したクラスターの属性値の重要度を視覚的に表す棒グラフが表示され、クラスター内の状態間の遷移が要約されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-187">The **Cluster Characteristics** tab summarizes the transitions between states in a cluster by displaying bars that visually represent the importance of the attribute value for the selected cluster.</span></span> <span data-ttu-id="0c73e-188">[**変数**] 列には、選択したクラスターまたは母集団にとって重要なモデル (特定の値または*遷移*と呼ばれる値間のリレーションシップ) が示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-188">The **Variables** column tells you what the model found to be important for the selected cluster or population: either a particular value or the relationship between values, known as *transition*.</span></span> <span data-ttu-id="0c73e-189">[**値**] 列には、値または遷移の詳細が表示され、[**確率**] 列はこの属性または遷移の重みを視覚的に表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-189">The **Values** column provides more detail about the value or transition, and the **Probability** column visually represents the weight of this attribute or transition.</span></span>  
  
#### <a name="to-view-the-important-attributes-for-a-cluster"></a><span data-ttu-id="0c73e-190">クラスターの重要な属性を表示するには</span><span class="sxs-lookup"><span data-stu-id="0c73e-190">To view the important attributes for a cluster</span></span>  
  
1.  <span data-ttu-id="0c73e-191">[**クラスター** ] ボックスの一覧で、を選択し `Pacific Cluster` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-191">In the **Cluster** dropdown list, select `Pacific Cluster`.</span></span>  
  
     <span data-ttu-id="0c73e-192">一覧が更新され、名前を変更したクラスターの特性が表示され `Pacific Cluster` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-192">The list updates to show the characteristics of the cluster that you renamed `Pacific Cluster`.</span></span> <span data-ttu-id="0c73e-193">このクラスターで最も重要な特性は `Region` です。</span><span class="sxs-lookup"><span data-stu-id="0c73e-193">In this cluster, the most important characteristic is `Region`.</span></span>  
  
2.  <span data-ttu-id="0c73e-194">の行の網掛けされたバーの上にマウスポインターを置き `Region` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-194">Pause the mouse over the shaded bar in the row for `Region`.</span></span>  
  
     <span data-ttu-id="0c73e-195">値が Pacific である確率が非常に高いことがわかります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-195">The probability of the value being Pacific is very high.</span></span> <span data-ttu-id="0c73e-196">これらの値を解釈する方法の詳細については、「 [Microsoft シーケンスクラスターアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c73e-196">For more information about how to interpret these values, see [Microsoft Sequence Clustering Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md).</span></span>  
  
3.  <span data-ttu-id="0c73e-197">最初の遷移行が見つかるまでクラスターの特性の一覧を調べていきます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-197">Look through the list of characteristics for the cluster until you find the first transition row.</span></span>  
  
4.  <span data-ttu-id="0c73e-198">遷移行には、[**変数**] 列のテキストの切り替えと、[**値**] 列のシーケンシャル属性値の組み合わせが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-198">A transition row contains the text Transition in the **Variables** column, and some combination of sequential attribute values in the **Value** column.</span></span> <span data-ttu-id="0c73e-199">[Start] や missing がシーケンスに含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-199">The sequence can also contain starting points and missing values.</span></span>  
  
     <span data-ttu-id="0c73e-200">たとえば、遷移の値が [Start]-> 道路タイヤチューブであるとします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-200">For example, suppose the transition has the value, [Start] -> Road Tire Tube.</span></span> <span data-ttu-id="0c73e-201">そのクラスターの顧客がよく Road Tire Tube を最初に買い物かごに入れているということになります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-201">This means that customers in this cluster frequently put the Road Tire Tube in their shopping basket first.</span></span> <span data-ttu-id="0c73e-202">これは、その製品が顧客によって最初に探される人気のアイテムであることを示している場合もあれば、その製品がその購入サイトで見つけやすいということを示しているだけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-202">This might signify that the product is a popular item that customers seek out first, or it might only indicate that the product is easy to find on the purchasing site.</span></span>  
  
5.  <span data-ttu-id="0c73e-203">**[Start]** がないか、または**見つから**ない最初の遷移が見つかるまで、一覧をスクロールします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-203">Scroll through the list until you find the first transition that does not have **[Start]** or **missing** in it.</span></span>  
  
     <span data-ttu-id="0c73e-204">たとえば、移行、**ツーリングタイヤ、ツーリングタイヤチューブ**を見つけたとします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-204">For example, suppose you find the transition, **Touring Tire, Touring Tire Tube**.</span></span> <span data-ttu-id="0c73e-205">そのクラスターの顧客がこれらのアイテムをよくこの順序で一緒に購入していることになります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-205">This means that customers in this cluster frequently purchased these items together, in exactly this order.</span></span>  
  
6.  <span data-ttu-id="0c73e-206">この遷移の色付きのバーの上にマウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-206">Pause the mouse over the shaded bar for this transition.</span></span>  
  
     <span data-ttu-id="0c73e-207">この遷移の確率がパーセントで表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-207">The probability of this transition is displayed as a percentage.</span></span>  
  
7.  <span data-ttu-id="0c73e-208">[**クラスター** ] ボックスの一覧で、[**母集団 (すべて)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-208">In the **Cluster** dropdown list, select **Population (All)**.</span></span>  
  
     <span data-ttu-id="0c73e-209">属性の一覧が更新されて、モデルの作成に使用されたすべての注文の特性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-209">The list of attributes updates to show the characteristics of all orders used to create the model.</span></span> <span data-ttu-id="0c73e-210">このマイニングモデルでは、クラスターを区別するための最も重要な特性は `Region` で、値は**北米**です。</span><span class="sxs-lookup"><span data-stu-id="0c73e-210">In this mining model, the most important characteristic for distinguishing between clusters is `Region`, with a value of **North America**.</span></span>  
  
 <span data-ttu-id="0c73e-211">以上の作業から、2 つのことがわかりました。</span><span class="sxs-lookup"><span data-stu-id="0c73e-211">After reviewing these tasks, you realize two things.</span></span> <span data-ttu-id="0c73e-212">1 つは、意味のある数の組み合わせを得るためには大量のデータが必要であるということです。</span><span class="sxs-lookup"><span data-stu-id="0c73e-212">The first is that you need a lot of data to obtain a meaningful number of combinations.</span></span> <span data-ttu-id="0c73e-213">たとえば、確率が最も高いシーケンスには、 **[Start]** または**Missing**状態が含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-213">For example, the sequences with the highest probabilities are likely to include a **[Start]** or **Missing** state.</span></span>  
  
 <span data-ttu-id="0c73e-214">2つ目の方法は、の属性に対して強力なクラスタリング効果があることです。これにより、 `Region` シーケンスのグループを確認するのが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-214">The second is that there is a strong clustering effect on attributes for `Region`, which makes it more difficult to see the groups of sequences.</span></span> <span data-ttu-id="0c73e-215">したがって、地域や収入の列を含まない、シーケンスのみを使用する別のモデルを作成することにします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-215">Therefore, you decide to create another model that uses sequences only, and does not include the columns for region or income.</span></span>  
  
 [<span data-ttu-id="0c73e-216">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0c73e-216">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-discrimination-tab"></a><a name="bkmk_CDiscrim2"></a><span data-ttu-id="0c73e-217">[クラスターの識別] タブ</span><span class="sxs-lookup"><span data-stu-id="0c73e-217">Cluster Discrimination Tab</span></span>  
 <span data-ttu-id="0c73e-218">[**クラスターの識別**] タブを使用すると、2つのクラスターを比較して、特定のクラスターを別のクラスターと区別する属性を特定できます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-218">The **Cluster Discrimination** tab helps you compare two clusters, to determine which attributes distinguish a particular cluster from another cluster.</span></span> <span data-ttu-id="0c73e-219">このタブには、[**変数**]、[**値**]、[**クラスター 1**]、[**クラスター 2**] の4つの列があります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-219">The tab contains four columns: **Variables**, **Values**, **Cluster 1**, and **Cluster 2**.</span></span>  <span data-ttu-id="0c73e-220">クラスター **1**と**クラスター 2**として使用する任意のクラスターを選択できます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-220">You can choose any cluster to use as **Cluster 1** and **Cluster 2**.</span></span>  
  
 <span data-ttu-id="0c73e-221">[**変数**] 列には、属性の名前が表示されます。これは、列名または列名と単語の組み合わせのいずれか**になります**。</span><span class="sxs-lookup"><span data-stu-id="0c73e-221">The **Variables** column tells you the name of the attribute, which can either be a column name or combination of column name and the word **transition**.</span></span> <span data-ttu-id="0c73e-222">[**値**列には、属性または遷移の正確な値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-222">The **Values** column shows the exact value of the attribute or the transition.</span></span> <span data-ttu-id="0c73e-223">**クラスター 1**と**クラスター 2**の列の網掛けされたバーは、比較しているクラスター内の属性の強度を示します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-223">The shaded bars in the columns for **Cluster 1** and **Cluster 2** indicate the strength of the attribute in the clusters that you are comparing.</span></span> <span data-ttu-id="0c73e-224">バーが長いほど、その属性を持つケースがクラスターに含まれる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-224">The longer the bar, the more the cluster is likely to include cases with that attribute.</span></span>  
  
#### <a name="to-compare-two-clusters-by-using-the-cluster-discrimination-tab"></a><span data-ttu-id="0c73e-225">[クラスターの識別] タブを使用して 2 つのクラスターを比較するには</span><span class="sxs-lookup"><span data-stu-id="0c73e-225">To compare two clusters by using the Cluster Discrimination tab</span></span>  
  
1.  <span data-ttu-id="0c73e-226">[**クラスターの識別**] タブで、[**クラスター 1**] にを選択し `Pacific Cluster` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-226">In the **Cluster Discrimination** tab, for **Cluster 1**, select `Pacific Cluster`.</span></span>  
  
     <span data-ttu-id="0c73e-227">既定では、[**クラスター 2** ] の選択は、**太平洋標準クラスターの補数**に変わります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-227">By default, the selection for **Cluster 2** changes to **Complement of Pacific Cluster**.</span></span>  
  
     <span data-ttu-id="0c73e-228">他のすべてのケースと区別する最上位の属性 `Pacific Cluster` は、領域です。</span><span class="sxs-lookup"><span data-stu-id="0c73e-228">The top attribute that distinguishes `Pacific Cluster` from all other cases is the region.</span></span> <span data-ttu-id="0c73e-229">地域がクラスター化のための属性として強力すぎるために、他の属性がわかりにくくなっています。</span><span class="sxs-lookup"><span data-stu-id="0c73e-229">Region is such a strong attribute for clustering that it obscures other attributes.</span></span> <span data-ttu-id="0c73e-230">この影響を回避するために、いくつかの小さなクラスターを互いに比較してみます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-230">To avoid this effect, try comparing several of the smaller clusters to each other.</span></span> <span data-ttu-id="0c73e-231">そうすれば、属性の一覧が変更されて、モデル間の遷移がより多く含まれるようになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-231">When you do so, the list of attributes changes and might include more transitions between models.</span></span>  
  
2.  <span data-ttu-id="0c73e-232">遷移行を見つけて、色付きのバーの上にマウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-232">Locate a transition row, and pause the mouse over the shaded bar.</span></span>  
  
     <span data-ttu-id="0c73e-233">[**値**] 列の項目には、状態と遷移の両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-233">The items in the **Values** column can include both states and transitions.</span></span> <span data-ttu-id="0c73e-234">各アイテムの色は識別スコアを表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-234">The shading for each item indicates the discrimination score.</span></span> <span data-ttu-id="0c73e-235">さまざまなスコアの意味の詳細については、「 [Analysis Services データマイニング&#41;&#40;シーケンスクラスターモデルのマイニングモデルコンテンツ](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c73e-235">To learn more about the meaning of different scores, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
 [<span data-ttu-id="0c73e-236">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0c73e-236">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="state-transitions-tab"></a><a name="bkmk_StateTran"></a><span data-ttu-id="0c73e-237">[状態遷移] タブ</span><span class="sxs-lookup"><span data-stu-id="0c73e-237">State Transitions Tab</span></span>  
 <span data-ttu-id="0c73e-238">[**状態遷移**] タブでは、クラスターを選択し、その状態遷移を参照できます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-238">On the **State Transitions** tab, you can select a cluster and browse through its state transitions.</span></span> <span data-ttu-id="0c73e-239">[クラスター] ドロップダウンリストから [**母集団 (すべて)** ] を選択した場合、ダイアグラムには、マイニングモデル全体の状態の分布が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-239">If you select **Population (All)** from the cluster drop-down list, the diagram shows the distribution of states for the whole mining model.</span></span>  
  
 <span data-ttu-id="0c73e-240">グラフの各ノードは、分析しようとしているシーケンスの状態または使用可能な値を表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-240">Each node in the graph represents a state, or possible value, of the sequences that you are trying to analyze.</span></span> <span data-ttu-id="0c73e-241">ノードの背景色は、その状態の頻度を表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-241">The background color of the nodes represents the frequency of that state.</span></span> <span data-ttu-id="0c73e-242">一部の状態を結ぶ線は、状態間の遷移を表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-242">Lines connect some states, indicating a transition between states.</span></span> <span data-ttu-id="0c73e-243">スライダーを上下に動かして、遷移の確率のしきい値を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-243">You can move the slider up or down to change the probability threshold for the transitions.</span></span> <span data-ttu-id="0c73e-244">一部のノードに関連付けられている数値は、その状態の確率を表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-244">Numbers are associated with some nodes, indicating the probability of that state.</span></span>  
  
#### <a name="to-explore-the-relationships-in-the-state-transition-tab"></a><span data-ttu-id="0c73e-245">[状態遷移] タブで関係を調査するには</span><span class="sxs-lookup"><span data-stu-id="0c73e-245">To explore the relationships in the State Transition tab</span></span>  
  
1.  <span data-ttu-id="0c73e-246">マイニングモデルビューアーの [**状態遷移**] タブで、 `Pacific Cluster` クラスターの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-246">In the **State Transitions** tab of the Mining Model viewer, select `Pacific Cluster` from the list of clusters.</span></span> <span data-ttu-id="0c73e-247">[**エッジラベルの表示**] オプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-247">Ensure that the **Show Edge Labels** option is selected.</span></span>  
  
     <span data-ttu-id="0c73e-248">グラフが更新されて、このクラスターで最も一般的な遷移が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-248">The graph updates to show the transitions that are most common in this cluster.</span></span>  
  
2.  <span data-ttu-id="0c73e-249">別のノードと線で結ばれている任意のノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-249">Click any node that is connected by a line to another node.</span></span>  
  
     <span data-ttu-id="0c73e-250">グラフが更新されて、関連するノードが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-250">The graph is updated and highlights the related nodes.</span></span> <span data-ttu-id="0c73e-251">線の横の数値はその遷移の確率を表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-251">The numeric value next to the line indicates the probability of the transition.</span></span>  
  
3.  <span data-ttu-id="0c73e-252">スライダーを [すべての**リンク**] まで上げて、グラフに含まれる切り替え効果の数を増やします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-252">Raise the slider up to **All Links**, to increase the number of transitions included in the graph.</span></span>  
  
4.  <span data-ttu-id="0c73e-253">**クラスター**から [**母集団 (すべて)** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-253">Select **Population (All)** from **Cluster**.</span></span>  
  
     <span data-ttu-id="0c73e-254">別のクラスターを読み込むとグラフが既定の表示設定にリセットされるため、スライダー コントロールが中央の位置に戻ります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-254">Note that when you load a different cluster, the graph resets to the default display settings, so the slider control is reset to the middle position.</span></span>  
  
5.  <span data-ttu-id="0c73e-255">グラフの最も暗いノードをクリックします。これは、"**スポーツ-100**" になります。</span><span class="sxs-lookup"><span data-stu-id="0c73e-255">Click the darkest node in the graph, which should be **Sport-100**.</span></span>  
  
     <span data-ttu-id="0c73e-256">この製品を他の製品と結ぶ線はありません。</span><span class="sxs-lookup"><span data-stu-id="0c73e-256">Note that there are no lines connecting this product to other products.</span></span>  
  
6.  <span data-ttu-id="0c73e-257">スライダーを 1 段階上に動かして、グラフに含まれる遷移の数を増やします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-257">Raise the slider up one step, to increase the number of transitions included in the graph.</span></span> <span data-ttu-id="0c73e-258">**すべてのリンク**にまだアクセスしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0c73e-258">Do not go all the way to **All Links** yet.</span></span>  
  
     <span data-ttu-id="0c73e-259">グラフが更新されていくつかの遷移が追加されますが、Sport-100 モデルを含む遷移はありません。</span><span class="sxs-lookup"><span data-stu-id="0c73e-259">The graph is updated by adding several more transitions to the graph, but none that include the Sport-100 model.</span></span>  
  
7.  <span data-ttu-id="0c73e-260">スライダーコントロールをすべての**リンク**に移動します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-260">Move the slider control all the way to **All Links**.</span></span> <span data-ttu-id="0c73e-261">まだ選択されていない場合は、Sport-100 ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c73e-261">Click the Sport-100 node if it is not already selected.</span></span>  
  
     <span data-ttu-id="0c73e-262">グラフが更新されて、Sport-100 という製品を含む多数の遷移が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-262">The graph updates to show many transitions that include the Sport-100 product.</span></span> <span data-ttu-id="0c73e-263">ノードを結ぶ線の矢印の向きは、Sport-100 がペアの 1 つ目のアイテムとして選択されたか 2 つ目のアイテムとして選択されたかを表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-263">The direction of the arrow on the connecting line tells you whether the Sport-100 item was selected as the first item or the second item in the pair.</span></span>  
  
8.  <span data-ttu-id="0c73e-264">Touring Tire のノードをクリックし、スライダー コントロールを中央の位置まで戻します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-264">Clicking the node for Touring Tire and move the slider control back down to the middle position.</span></span>  
  
     <span data-ttu-id="0c73e-265">最初に、ツーリングタイヤを他の製品に接続する多くの遷移線がありますが、確率のしきい値を上げると、遷移、ツーリングタイヤ > ツーリングタイヤチューブだけを残して、グラフからの移行が減少します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-265">At first, there are many transition lines connecting Touring Tire to other products, but when you raise the probability threshold, the less likely transitions are eliminated from the graph, leaving just the transition, Touring Tire > Touring Tire Tube.</span></span> <span data-ttu-id="0c73e-266">この遷移は、顧客が Touring Tire を買い物かごに入れた場合、その次に Touring Tire Tube をかごに入れる確率が高いことを示しています。</span><span class="sxs-lookup"><span data-stu-id="0c73e-266">This transition means that if a customer puts a Touring Tire into the shopping basket, there is a strong probability that the customer will next put a Touring Tire Tube into the basket.</span></span>  
  
 [<span data-ttu-id="0c73e-267">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0c73e-267">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_Generic"></a><span data-ttu-id="0c73e-268">汎用コンテンツツリービューアー</span><span class="sxs-lookup"><span data-stu-id="0c73e-268">Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="0c73e-269">このビューアーは、アルゴリズムやモデルの種類に関係なく、すべてのモデルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-269">This viewer can be used for all models, regardless of the algorithm or model type.</span></span> <span data-ttu-id="0c73e-270">**Microsoft 汎用コンテンツツリービューアー**は、[**ビューアー** ] ドロップダウンリストから使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-270">The **MicrosoftGeneric Content Tree Viewer** is available from the **Viewer** drop-down list.</span></span>  
  
 <span data-ttu-id="0c73e-271">コンテンツ ツリーは、マイニング モデルを一連のノードで表したものです。各ノードは、トレーニング データに関する学習済みの知識を表します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-271">A content tree is a representation of any mining model as a series of nodes, wherein each node represents learned knowledge about the training data.</span></span> <span data-ttu-id="0c73e-272">ノードには、いくつかの属性が共通するパターン、一連のルール、クラスター、または日付範囲の定義を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-272">The node can contain a pattern, a set of rules, a cluster, or the definition of a range of dates that share some attributes.</span></span> <span data-ttu-id="0c73e-273">ノードの正確な内容はアルゴリズムや予測可能な属性に応じて変わりますが、内容の全体的な表示は同じです。</span><span class="sxs-lookup"><span data-stu-id="0c73e-273">The exact content of the node differs depending on the algorithm and the predictable attribute, but the general representation of the content is the same.</span></span>  
  
 <span data-ttu-id="0c73e-274">各ノードを展開して、より詳細なレベルで表示したり、任意のノードの内容をクリップボードにコピーしたりできます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-274">You can expand each node to see increasing levels of detail, and copy the content of any node to the Clipboard.</span></span> <span data-ttu-id="0c73e-275">詳細については、「 [Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0c73e-275">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
#### <a name="to-view-details-for-a-sequence-clustering-model-by-using-the-generic-content-tree-viewer"></a><span data-ttu-id="0c73e-276">汎用コンテンツ ツリー ビューアーを使用してシーケンス クラスター モデルの詳細を表示するには</span><span class="sxs-lookup"><span data-stu-id="0c73e-276">To view details for a sequence clustering model by using the Generic Content Tree Viewer</span></span>  
  
1.  <span data-ttu-id="0c73e-277">[**マイニングモデルビューアー** ] タブで、[**ビューアー** ] ボックスの一覧をクリックし、[ **Microsoft 汎用コンテンツツリービューアー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-277">In the **Mining Model Viewer** tab, click the **Viewer** list, and select **Microsoft Generic Content Tree viewer**.</span></span>  
  
2.  <span data-ttu-id="0c73e-278">[**ノードのキャプション**] ペインで、[] をクリックし `Pacific Cluster (1)` ます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-278">In the **Node Caption** pane, click `Pacific Cluster (1)`.</span></span>  
  
     <span data-ttu-id="0c73e-279">このノードの名前には、クラスターに割り当てた表示名と、基になるノード ID の両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c73e-279">The name for this node contains both the friendly name that you assigned to the cluster and the underlying node ID.</span></span> <span data-ttu-id="0c73e-280">ノード ID を使用してモデルの詳細にドリル ダウンできます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-280">You can use the node IDs to drill down into additional detail in the model.</span></span>  
  
3.  <span data-ttu-id="0c73e-281">最初の子ノード ([**クラスター1のシーケンスレベル**]) を展開します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-281">Expand the first child node, named **Sequence level for cluster 1**.</span></span>  
  
     <span data-ttu-id="0c73e-282">クラスターのシーケンス レベル ノードには、そのクラスターに含まれる状態と遷移の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c73e-282">The sequence level node for a cluster contains details about the states and transitions that are included in that cluster.</span></span> <span data-ttu-id="0c73e-283">これらの詳細 (NODE_DISTRIBUTION 列に表示されます) を使用して、各クラスターまたはモデル全体のシーケンスと状態を調査することができます。</span><span class="sxs-lookup"><span data-stu-id="0c73e-283">You can use these details, available in the NODE_DISTRIBUTION column, to explore the sequences and the states for each cluster or for the model as a while.</span></span>  
  
4.  <span data-ttu-id="0c73e-284">ノードをさらに展開して、HTML ビューアー ペインに詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="0c73e-284">Continue to expand nodes and view the details in the HTML viewer pane.</span></span>  
  
 <span data-ttu-id="0c73e-285">マイニングモデルコンテンツの詳細およびビューアーでの詳細の使用方法については、「 [Analysis Services データ&#41;マイニングモデル &#40;シーケンスクラスターモデルのマイニングモデルコンテンツ](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c73e-285">For more information about the mining model content, and how to use the details in the viewer, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
 [<span data-ttu-id="0c73e-286">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0c73e-286">Back to Top</span></span>](#bkmk_CDiagram)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="0c73e-287">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="0c73e-287">Next Task in Lesson</span></span>  
 [<span data-ttu-id="0c73e-288">関連するシーケンスクラスターモデルの作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="0c73e-288">Creating a Related Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c73e-289">参照</span><span class="sxs-lookup"><span data-stu-id="0c73e-289">See Also</span></span>  
 <span data-ttu-id="0c73e-290">[Microsoft シーケンスクラスターアルゴリズム](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="0c73e-290">[Microsoft Sequence Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="0c73e-291">Sequence Clustering Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="0c73e-291">Sequence Clustering Model Query Examples</span></span>](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)  
  
  
