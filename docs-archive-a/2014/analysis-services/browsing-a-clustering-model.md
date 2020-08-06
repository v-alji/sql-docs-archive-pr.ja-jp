---
title: クラスターモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d508603acd29fde981bddc5642b54ca9413f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633589"
---
# <a name="browsing-a-clustering-model"></a><span data-ttu-id="b6d7f-102">クラスター モデルの参照</span><span class="sxs-lookup"><span data-stu-id="b6d7f-102">Browsing a Clustering Model</span></span>
  <span data-ttu-id="b6d7f-103">**参照**を使用してクラスターモデルを開くと、のクラスタービューアーに似た対話型ビューアーにモデルが表示され [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-103">When you open a clustering model using **Browse**, the model is displayed in an interactive viewer, similar to the clustering viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b6d7f-104">ビューアーは、作成されたクラスターを調査して、クラスターの特性を把握するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-104">The viewer helps you explore the clusters that were created, and understand cluster characteristics.</span></span> <span data-ttu-id="b6d7f-105">また、個々のセグメントを他のセグメントや母集団と比較対照することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-105">You can also compare and contrast individual segments with other segments or with the population.</span></span>  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="b6d7f-106">モデルの調査</span><span class="sxs-lookup"><span data-stu-id="b6d7f-106">Explore the Model</span></span>  
 <span data-ttu-id="b6d7f-107">[**参照**] ウィンドウには、クラスターモデルを理解し、基になるデータグループの属性を調べるのに役立つ次のツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-107">The **Browse** window includes the following tools to help you understand your clustering model and explore the attributes of the underlying data groups:</span></span>  
  
-   [<span data-ttu-id="b6d7f-108">クラスター ダイアグラム</span><span class="sxs-lookup"><span data-stu-id="b6d7f-108">Cluster Diagram</span></span>](#BKMK_ClusterDiagram)  
  
-   [<span data-ttu-id="b6d7f-109">クラスターのプロファイル</span><span class="sxs-lookup"><span data-stu-id="b6d7f-109">Cluster Profiles</span></span>](#BKMK_ClusterProfiles)  
  
-   [<span data-ttu-id="b6d7f-110">クラスターの特性</span><span class="sxs-lookup"><span data-stu-id="b6d7f-110">Cluster Characteristics</span></span>](#BKMK_ClusterCharacteristics)  
  
-   [<span data-ttu-id="b6d7f-111">クラスターの識別</span><span class="sxs-lookup"><span data-stu-id="b6d7f-111">Cluster Discrimination</span></span>](#BKMK_ClusterDiscrimination)  
  
 <span data-ttu-id="b6d7f-112">クラスターモデルを試してみるには、サンプルデータブックの [トレーニング] タブにあるサンプルデータを使用して、[クラスターウィザード &#40;Excel 用データマイニングアドイン&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)およびすべての既定値を使用してクラスターモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-112">To experiment with a clustering model, you can use the sample data on the Training tab of the sample data workbook, and build a clustering model using [Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) and all the defaults.</span></span>  
  
###  <a name="cluster-diagram"></a><a name="BKMK_ClusterDiagram"></a><span data-ttu-id="b6d7f-113">クラスターダイアグラム</span><span class="sxs-lookup"><span data-stu-id="b6d7f-113">Cluster Diagram</span></span>  
 <span data-ttu-id="b6d7f-114">[**クラスターダイアグラム**] タブには、マイニングモデル内のすべてのクラスターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-114">The **Cluster Diagram** tab displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="b6d7f-115">データセットに見つかった異なるグループの数、および、互いにどれぐらい近いか遠いかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-115">Here you can see how many different groupings were found in your data set, and how near or far they are from each other.</span></span>  
  
##### <a name="explore-the-cluster-diagram"></a><span data-ttu-id="b6d7f-116">クラスター ダイアグラムの調査</span><span class="sxs-lookup"><span data-stu-id="b6d7f-116">Explore the cluster diagram</span></span>  
  
1.  <span data-ttu-id="b6d7f-117">ダイアグラムの [クラスター 1] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-117">Click Cluster 1 in the diagram.</span></span>  
  
     <span data-ttu-id="b6d7f-118">すべてのクラスターを接続する灰色の線が変化して、選択したクラスターにつながる線が明るい青色で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-118">Note how the gray lines connecting all clusters change so that lines leading to the selected cluster are highlighted in bright blue.</span></span>  
  
     <span data-ttu-id="b6d7f-119">![クラスター ダイアグラムの紹介](media/dm13-cluster-diagram-intro.gif "クラスター ダイアグラムの紹介")</span><span class="sxs-lookup"><span data-stu-id="b6d7f-119">![cluster diagram intro](media/dm13-cluster-diagram-intro.gif "cluster diagram intro")</span></span>  
  
     <span data-ttu-id="b6d7f-120">クラスターを結ぶ線の濃さは、クラスターの類似性の強度を表します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-120">The intensity of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="b6d7f-121">網掛けが薄いか存在しない場合は、クラスターがあまり似ていません。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-121">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="b6d7f-122">線が濃くなるほど、2 つのクラスターの類似性が強いことを表します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-122">As the line becomes darker, it indicates that the similarity between the two clusters is stronger.</span></span>  
  
2.  <span data-ttu-id="b6d7f-123">クラスター ダイアグラムの左側にあるスライダーをドラッグすると、ビューアーに表示される線の数を調整できます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-123">Click and drag the slider to the left of the cluster diagram, to adjust how many lines the viewer shows.</span></span>  
  
     <span data-ttu-id="b6d7f-124">スライダーをドラッグして下げると、クラスター間で最も強いリンクだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-124">When you drag the slider down, only the strongest links between clusters are shown.</span></span> <span data-ttu-id="b6d7f-125">これは関連のあるグループを目立たせるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-125">This helps you focus on related groups.</span></span>  
  
3.  <span data-ttu-id="b6d7f-126">**クラスターダイアグラム**ウィンドウの右上隅にある [**網掛け変数**] コントロールに注目してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-126">Notice the **Shading Variable** control in the upper right corner of the **Cluster Diagram** window.</span></span>  
  
     <span data-ttu-id="b6d7f-127">既定では、[**母集団**] に設定されています。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-127">By default, it is set to **Population**.</span></span> <span data-ttu-id="b6d7f-128">つまり、クラスターの色が濃くなるほど、サポートが多いということです。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-128">What this means is that the darker clusters have greater support.</span></span>  
  
4.  <span data-ttu-id="b6d7f-129">クラスターの上にマウス カーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-129">Pause over any cluster with the cursor.</span></span>  
  
     <span data-ttu-id="b6d7f-130">そのクラスターの母集団を含むツールヒントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-130">A ToolTip is displayed that contains the population of that cluster.</span></span>  
  
5.  <span data-ttu-id="b6d7f-131">次に、[**シェーディング変数**] ボックスの一覧をクリックし、 **Age**変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-131">Now, click the **Shading Variable** dropdown list and choose the **Age** variable.</span></span> <span data-ttu-id="b6d7f-132">これを行うと、[**状態**] ボックスに値の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-132">As you do so, a list of values appears in the **State** text box.</span></span>  
  
     <span data-ttu-id="b6d7f-133">このモデルへの入力として使用される Age 列には、連続する数値が含まれていますが、クラスタリングのために、アルゴリズムによって常に数値が分離されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-133">The Age column used as input to this model contains continuous numeric values, but for the purpose of clustering, the algorithm always discretizes numbers.</span></span> <span data-ttu-id="b6d7f-134">ここでは、"非常に低い (= 63)" など、アルゴリズムによって作成されたビンまたはグループを確認でき \<=27)" and "Very High (> ます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-134">Here you can see the bins, or groups that the algorithm created, such as "Very Low (\<=27)" and "Very High (>=63)".</span></span>  
  
6.  <span data-ttu-id="b6d7f-135">[**状態**] ドロップダウンリストから [**非常に高い**] を選択し、ダイアグラムがどのように変化するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-135">From the **State** dropdown lists, select **Very High** and see how the diagram changes.</span></span>  
  
     <span data-ttu-id="b6d7f-136">網掛け変数を変更することで、どのクラスターがこの対象の年齢層を多数含んでいるか、どのクラスターにこの年齢層の顧客が少ないかがひとめでわかります。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-136">By changing the shading variable, you can see at a glance which clusters contain more of this targeted age group, and which clusters contain very few customers in this age group.</span></span>  
  
     <span data-ttu-id="b6d7f-137">![年齢を表示するようにクラスター ダイアグラムを変更](media/dm13-cluster-diagramshadebyage.gif "年齢を表示するようにクラスター ダイアグラムを変更")</span><span class="sxs-lookup"><span data-stu-id="b6d7f-137">![Modify the cluster diagram to show age](media/dm13-cluster-diagramshadebyage.gif "Modify the cluster diagram to show age")</span></span>  
  
     <span data-ttu-id="b6d7f-138">網掛けが濃いほど、そのクラスターの対象属性の比率と値の分布が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-138">The darker the shading, the larger the proportion of the target attribute and value distribution that cluster.</span></span>  
  
7.  <span data-ttu-id="b6d7f-139">**シェーディング変数**が Age >65 に設定されている場合は、影が最も暗いクラスターを見つけます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-139">Locate the cluster that is shaded darkest when the **Shading Variable** is set to Age >65.</span></span>  
  
     <span data-ttu-id="b6d7f-140">そのクラスターの上にマウス カーソルを合わせます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-140">Hover the mouse over the cluster.</span></span>  
  
     <span data-ttu-id="b6d7f-141">ツールヒントに表示される値は、このクラスターで 65 歳を超える顧客の人数です。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-141">The value displayed in the ToolTip now shows you the population of customers in this cluster who are over 65.</span></span>  
  
8.  <span data-ttu-id="b6d7f-142">クラスターを右クリックし、[**クラスター名の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-142">Right-click the cluster and select **Rename Cluster**.</span></span> <span data-ttu-id="b6d7f-143">「 **65 を超える**」など、わかりやすい新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-143">Type a new name that is descriptive, such as **Over 65**.</span></span> <span data-ttu-id="b6d7f-144">新しい名前はモデルと共にサーバーに保存され、他のクラスター ビューでクラスターを識別するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-144">The new name is saved with the model to the server and can be used for identifying the cluster in the other clustering views.</span></span>  
  
 [<span data-ttu-id="b6d7f-145">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="b6d7f-145">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_ClusterProfiles"></a> <span data-ttu-id="b6d7f-146">クラスターのプロファイル</span><span class="sxs-lookup"><span data-stu-id="b6d7f-146">Cluster Profiles</span></span>  
 <span data-ttu-id="b6d7f-147">[**クラスターのプロファイル**] タブでは、すべてのクラスターの作成を一目で比較できます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-147">The **Cluster Profiles** tab lets you compare the makeup of all clusters at a glance.</span></span> <span data-ttu-id="b6d7f-148">モデルに慣れる過程では、この機能から始めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-148">This is a good place to start when you are getting familiar with the model.</span></span> <span data-ttu-id="b6d7f-149">このビューは後で、特定のクラスターの調査中に関連クラスターを見つける必要が生じた場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-149">This view is also useful later on, if you have been exploring a particular cluster and decide you need to find related ones.</span></span>  
  
 <span data-ttu-id="b6d7f-150">**クラスターのプロファイル**では、クラスターが相互にどのように異なるかについての概要もわかります。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-150">**Cluster Profiles** also gives you a good overview of how the clusters are different from each other.</span></span> <span data-ttu-id="b6d7f-151">そこで、このビューを使用して、各クラスターにわかりやすい名前を付けると便利です。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-151">Therefore, you might find it convenient to use this view to give each cluster a descriptive name.</span></span>  
  
##### <a name="explore-the-cluster-profiles"></a><span data-ttu-id="b6d7f-152">クラスターのプロファイルの調査</span><span class="sxs-lookup"><span data-stu-id="b6d7f-152">Explore the cluster profiles</span></span>  
  
1.  <span data-ttu-id="b6d7f-153">[**状態**] 列の職業のセルをクリックすると、職業のすべての値の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-153">Click the cell for Occupations, in the **States** column, to see the list of all values for Occupation.</span></span>  
  
2.  <span data-ttu-id="b6d7f-154">クラスターのプロファイルで [Occupation] (職業) の上にマウス カーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-154">Now move the cursor over Occupation in the cluster profiles.</span></span>  
  
     <span data-ttu-id="b6d7f-155">ツールヒントに、そのクラスターの職業分布が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-155">The ToolTip shows the distribution of occupations in that cluster.</span></span>  
  
     <span data-ttu-id="b6d7f-156">![ツール ヒントまたは凡例に詳細な値を表示](media/dm13-cluster-profile-age-tooltip.gif "ツール ヒントまたは凡例に詳細な値を表示")</span><span class="sxs-lookup"><span data-stu-id="b6d7f-156">![View detailed values in Tooltips or in Legend](media/dm13-cluster-profile-age-tooltip.gif "View detailed values in Tooltips or in Legend")</span></span>  
  
     <span data-ttu-id="b6d7f-157">クラスターによっては (グラフィックのようなものもあります)、職業のリストが完全ではなく、一部の職業がラベルである [**その他**] に置き換えられていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-157">Notice that, in some clusters (such as the one in the graphic), the list of occupations is not complete, and some occupations are replaced with the label, **Other**.</span></span>  
  
     <span data-ttu-id="b6d7f-158">これは仕様です。ヒストグラムで多数の小さなバーを区別するのは難しいためです。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-158">This is by design, because it can be hard to tell the difference between many small bars in a histogram.</span></span> <span data-ttu-id="b6d7f-159">既定では、重要度が最も高いバーだけが保持され、残りのバーは灰色**の他**のバケットにまとめられます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-159">By default only the bars of highest importance are retained, and the remaining bars are grouped together into a gray **Other** bucket.</span></span>  
  
     <span data-ttu-id="b6d7f-160">ヒストグラムに表示されるバーの数を変更するには、[**ヒストグラムバー**] オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-160">To change the number of bars that are visible in any histogram, use the option **Histogram bars**.</span></span>  
  
3.  <span data-ttu-id="b6d7f-161">**Age**列は他の列とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-161">Note that the **Age** column looks different from the others.</span></span> <span data-ttu-id="b6d7f-162">グラフで Age を表すダイヤモンドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-162">Click the diamond in the chart used to represent Age.</span></span>  
  
     <span data-ttu-id="b6d7f-163">Age 列はもともと連続する数値のみを含んでいました。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-163">The column Age originally contained only continuous numbers.</span></span> <span data-ttu-id="b6d7f-164">クラスター アルゴリズムでは不連続値が必要であるため、Age 列の数値は、値の分布に基づいて限られた数の年齢層にグループ分けされています。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-164">The clustering algorithm requires discrete values, so it grouped the numeric values in the Age column into a limited number of age groups, based on the distribution of values.</span></span>  
  
4.  <span data-ttu-id="b6d7f-165">クラスターのプロファイルでダイヤモンド グラフの 1 つをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-165">Click one of the diamond charts in a cluster profile.</span></span>  
  
     <span data-ttu-id="b6d7f-166">これらのダイヤモンド グラフは、ソース データが連続する数値を使用する場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-166">These diamond charts are displayed only when the source data uses continuous numeric values.</span></span> <span data-ttu-id="b6d7f-167">ダイヤモンド グラフは、各クラスターでのその値の平均値と標準偏差など、便利な統計情報を示します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-167">The diamond charts provide some useful descriptive statistics, including the mean and standard deviation for that value in each cluster:</span></span>  
  
    -   <span data-ttu-id="b6d7f-168">ダイヤモンド グラフの線は、属性の値の範囲を表します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-168">The line in the diamond chart represents the range of values for the attribute.</span></span> <span data-ttu-id="b6d7f-169">値は、**プロファイル**グラフの左側にある [**状態**列にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-169">The values are also shown in the **States** column at the left of the **Profiles** chart.</span></span>  
  
    -   <span data-ttu-id="b6d7f-170">ダイヤモンドの中心は、ノードの平均値に配置されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-170">The center of the diamond is positioned at the mean for the node.</span></span>  
  
    -   <span data-ttu-id="b6d7f-171">ダイヤモンドの幅は、そのノードにおける属性の分散を表します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-171">The width of the diamond represents the variance of the attribute at that node.</span></span> <span data-ttu-id="b6d7f-172">そのため、ダイヤモンドの幅が狭いほど、そのノードでより正確な予測を作成できることを示します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-172">Therefore, a thinner diamond indicates that the node can create a more accurate prediction.</span></span>  
  
5.  <span data-ttu-id="b6d7f-173">グラフの領域を増やすには、すぐに表示する必要のないクラスターを右クリックし、[**列の非表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-173">To make more room in the graph, right-click a cluster you don't need to view right away, and select **Hide Column**.</span></span> <span data-ttu-id="b6d7f-174">これによってモデルから削除されることはありません。列を一時的に折りたたんでください。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-174">This doesn't delete it from the model, just collapses the column temporarily.</span></span>  
  
     <span data-ttu-id="b6d7f-175">非表示にしたクラスターを表示するには、列の端をクリックしてドラッグする**か、クラスター**の一覧からクラスター名を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-175">To view clusters that you've hidden, you can click and drag the column edge, or select the cluster name from the list, **More clusters**.</span></span>  
  
6.  <span data-ttu-id="b6d7f-176">属性一覧をスクロールして [Bike Buyer] (自転車購入者) を見つけ、[Yes] (はい) の値の割合が最も高いクラスターを見つけます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-176">Scroll down the attribute list till you find Bike Buyer, and then find the cluster that has the highest percentage of Yes values.</span></span>  
  
     <span data-ttu-id="b6d7f-177">名前を変更するクラスターの列見出しを右クリックし、[**クラスター名の変更**] を選択して、「**自転車購入**者」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-177">Right-click the column heading for the cluster that you want to rename, select **Rename cluster**, and type **Bike Buyers**.</span></span>  
  
     <span data-ttu-id="b6d7f-178">新しいクラスター名は、モデルを再処理するまで、すべてのビューとサーバーで保持されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-178">The new cluster name is persisted in all views, and on the server, until you reprocess the model.</span></span>  
  
     <span data-ttu-id="b6d7f-179">![クラスター名を変更してグラフの使いやすさを向上](media/dm13-cluster-rename.gif "クラスター名を変更してグラフの使いやすさを向上")</span><span class="sxs-lookup"><span data-stu-id="b6d7f-179">![Rename clusters to make chart easier to use](media/dm13-cluster-rename.gif "Rename clusters to make chart easier to use")</span></span>  
  
 <span data-ttu-id="b6d7f-180">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="b6d7f-180">**Tips**</span></span>  
  
-   <span data-ttu-id="b6d7f-181">そのクラスターの属性を重要度順に並べ替えるには、列見出しをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-181">Click a column heading to sort the attributes in order of importance for that cluster.</span></span>  
  
-   <span data-ttu-id="b6d7f-182">ビューアーで列の順序を変更するには、列をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-182">Drag columns to reorder them in the viewer.</span></span>  
  
-   <span data-ttu-id="b6d7f-183">[**マイニング凡例**] の詳細な統計情報を表示するには、プロファイルグラフの任意のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-183">Click any cell in the profiles chart to view detailed statistics in the **Mining Legend**.</span></span>  
  
-   <span data-ttu-id="b6d7f-184">任意のセルを右クリックして [**ドリルスルーモデル列**] を選択すると、基になるデータが Excel の新しいワークシートに出力されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-184">Right-click any cell and select **Drillthrough model columns** to output the underlying data to a new worksheet in Excel.</span></span>  
  
-   <span data-ttu-id="b6d7f-185">クラスターの列見出しを右クリックし、[**構造データへのドリルスルー** ] を選択して、モデルに含まれていないクラスターメンバーに関する詳細情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-185">Right-click the cluster's column heading and select **Drillthrough to structure data** to get detailed information about the cluster members that wasn't included in the model.</span></span>  
  
     <span data-ttu-id="b6d7f-186">たとえば、顧客をプロファイリングする場合、基になるデータ (マイニング構造) に連絡先情報を残しておくことはできますが、モデルには含まれません。これは、分析には役立たないためです。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-186">For example, if you are profiling customers, you might leave the contact information in the underlying data (the mining structure) but not include it in the model, because it's not useful for analysis.</span></span> <span data-ttu-id="b6d7f-187">しかし、顧客がクラスターに割り当てられた後は、ドリルスルーを使用して詳細データを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-187">However, after customers have been assigned to clusters, you can view the detailed data by using drillthrough.</span></span>  
  
 [<span data-ttu-id="b6d7f-188">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="b6d7f-188">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_ClusterCharacteristics"></a> <span data-ttu-id="b6d7f-189">クラスターの特性</span><span class="sxs-lookup"><span data-stu-id="b6d7f-189">Cluster Characteristics</span></span>  
 <span data-ttu-id="b6d7f-190">[クラスターの特性] ビューでは、単一のクラスターを本格的に調査して、どの属性がこのデータ グループの最も強い特性となっているかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-190">The Cluster Characteristics view lets you really explore a single cluster, to find which attributes most strongly characterize this group of data.</span></span>  
  
##### <a name="explore-the-cluster-characteristics"></a><span data-ttu-id="b6d7f-191">クラスターの特性の調査</span><span class="sxs-lookup"><span data-stu-id="b6d7f-191">Explore the cluster characteristics</span></span>  
  
1.  <span data-ttu-id="b6d7f-192">[**クラスター** ] ボックスの一覧から [**超過 65**クラスター] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-192">Select the **Over 65** cluster from the **Cluster** list.</span></span>  
  
     <span data-ttu-id="b6d7f-193">クラスターを選択した後、そのクラスターを構成する特性を詳細に確認することができます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-193">After you select a cluster, you can see in detail the characteristics that make up that specific cluster.</span></span>  
  
     <span data-ttu-id="b6d7f-194">クラスターに含まれている属性は **[変数]** 列に表示され、属性の状態は **[値]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-194">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span>  
  
     <span data-ttu-id="b6d7f-195">属性の状態は、[確率] の順に一覧表示され、このクラスターの確率と共に [**確率**] 列に色付きのバーとして表されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-195">Attribute states are listed in order of importance, accompanied by their probability in this cluster, represented as a colored bar in the **Probability** column.</span></span>  
  
     <span data-ttu-id="b6d7f-196">![クラスター モデルの特性](media/dm13-cluster-characteristics.gif "クラスター モデルの特性")</span><span class="sxs-lookup"><span data-stu-id="b6d7f-196">![Characteristics of a clustering model](media/dm13-cluster-characteristics.gif "Characteristics of a clustering model")</span></span>  
  
2.  <span data-ttu-id="b6d7f-197">[**変数**] 列をクリックして、属性で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-197">Click the **Variables** column to sort by attribute.</span></span>  
  
     <span data-ttu-id="b6d7f-198">並べ替え変数を変更すると、収入や自動車所有のような変数について、グループ内での値の分布状況を簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-198">By changing the sort variable, you can more easily see how values for variables such as income or car ownership are distributed in the group.</span></span>  
  
3.  <span data-ttu-id="b6d7f-199">[ **Excel にコピー] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-199">Click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="b6d7f-200">新しいワークシートが、選択したクラスターの特性を含むブックに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-200">A new worksheet is added to your workbook that contains the characteristics of the selected cluster.</span></span>  
  
4.  <span data-ttu-id="b6d7f-201">次に、[**自転車購入**者] ボックスの一覧から別のクラスターを選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-201">Now choose a different cluster from the list, **Bike Buyers**.</span></span>  
  
5.  <span data-ttu-id="b6d7f-202">[ **Excel にコピー] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-202">Click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="b6d7f-203">新しいクラスター特性グラフは、独自のワークシートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-203">Note that the new cluster characteristics chart is added on its own worksheet.</span></span> <span data-ttu-id="b6d7f-204">他のプロファイルと同じワークシートに移動して、比較しやすくすることができます。これは、次の手順で行います。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-204">You can move it onto the same worksheet as the other profile to make it easier to compare them, which you'll do in the next step.</span></span>  
  
 <span data-ttu-id="b6d7f-205">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="b6d7f-205">**Tips**</span></span>  
  
-   <span data-ttu-id="b6d7f-206">65クラスターでは、顧客が製品を購入しないという主な特性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-206">Note that the primary characteristic of the customer in the Over 65 cluster is that they don't buy your product!</span></span> <span data-ttu-id="b6d7f-207">この理由を知るには、クラスターを参照してグループを比較します。または、デシジョン ツリー モデルや Naïve Bayes モデルなど、因果関係の調査に適したアルゴリズムを使用して関連モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-207">If you want to know why this is so, you can browse clusters and compare groups, or you might create a related model using an algorithm that is good at exploring causes and outcomes, such as a decision tree model or a Naïve Bayes model.</span></span>  
  
-   <span data-ttu-id="b6d7f-208">このクラスター (またはすべてのクラスター) の属性と確率の完全な一覧を取得するには、クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-208">If you want to get a complete list of attributes and probabilities for this cluster (or all clusters) you can create a query.</span></span> <span data-ttu-id="b6d7f-209">クラスターモデルのクエリの例については、「[クラスタリングモデルのクエリ例](data-mining/clustering-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-209">For examples of queries on clustering models, see [Clustering Model Query Examples](data-mining/clustering-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="b6d7f-210">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="b6d7f-210">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_ClusterDiscrimination"></a><span data-ttu-id="b6d7f-211">クラスターの識別</span><span class="sxs-lookup"><span data-stu-id="b6d7f-211">Cluster Discrimination</span></span>  
 <span data-ttu-id="b6d7f-212">[クラスターの**識別**] タブを使用すると、2つのクラスター間、またはクラスターと、データセット内の他のすべてのケースの間で属性を比較できます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-212">You use the **Cluster Discrimination** tab to compare attributes between two clusters, or between a cluster and all the other cases in the data set.</span></span>  
  
 <span data-ttu-id="b6d7f-213">このビューアーの機能を強調表示するには、[**クラスターの特性**] ビューに基づいて作成した Excel のサイドバイサイドのテーブルと比較します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-213">To highlight the features of this viewer, we'll compare it to the side-by-side tables in Excel that you created based on the **Cluster Characteristics** view.</span></span>  
  
##### <a name="explore-cluster-discrimination"></a><span data-ttu-id="b6d7f-214">クラスターの識別の調査</span><span class="sxs-lookup"><span data-stu-id="b6d7f-214">Explore cluster discrimination</span></span>  
  
1.  <span data-ttu-id="b6d7f-215">**[クラスター 1]** と **[クラスター 2]** の一覧を使用して、比較するクラスターを選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-215">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span>  
  
    -   <span data-ttu-id="b6d7f-216">[クラスター 1] ボックスでは [Over 65] (65 歳超) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-216">For Cluster 1, select Over 65.</span></span>  
  
    -   <span data-ttu-id="b6d7f-217">[クラスター 2] ボックスでは、[Bike Buyers] (自転車購入者) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-217">For Cluster 2, select Bike Buyers.</span></span>  
  
     <span data-ttu-id="b6d7f-218">比較結果は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-218">The comparison should look similar to the following graphic.</span></span>  
  
     <span data-ttu-id="b6d7f-219">![モデル内のクラスターの比較](media/dm13-cluster-compareclusters.gif "モデル内のクラスターの比較")</span><span class="sxs-lookup"><span data-stu-id="b6d7f-219">![comparing clusters in a model](media/dm13-cluster-compareclusters.gif "comparing clusters in a model")</span></span>  
  
     <span data-ttu-id="b6d7f-220">内部的には、**クラスター識別**ビューアーは複雑なクエリをデータマイニングサーバーに送信し、2つのグループを区別するために最も重要な属性を抽出して、2つの顧客のセットを比較しやすくします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-220">Note that, under the covers, the **Cluster Discrimination** viewer sends complex queries to the data mining server, to extract the attributes that are most important in distinguishing between the two groups, making it easier to compare two sets of customers.</span></span>  
  
2.  <span data-ttu-id="b6d7f-221">[**優先**] 列のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-221">Click either of the **Favors...** columns.</span></span>  
  
     <span data-ttu-id="b6d7f-222">属性と値一覧の右側にあるバーは、選択したクラスターの特性として、どの特徴または値が最も重要かを示しています。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-222">The bar to the right of the attribute and value list shows which features or values are most important as a characteristic of the selected cluster.</span></span>  
  
3.  <span data-ttu-id="b6d7f-223">今度は Excel で一覧を比較します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-223">Now compare the lists in Excel.</span></span>  
  
     <span data-ttu-id="b6d7f-224">![アソシエーション モデルの依存関係ネットワーク グラフ](media/dm13-comparing-profiles-in-excel.gif "アソシエーション モデルの依存関係ネットワーク グラフ")</span><span class="sxs-lookup"><span data-stu-id="b6d7f-224">![Dependency network graph for an association model](media/dm13-comparing-profiles-in-excel.gif "Dependency network graph for an association model")</span></span>  
  
     <span data-ttu-id="b6d7f-225">ビューアーで画像の作成に使用された基になる統計は、テーブルとして Excel に保存されるため、フィルターと並べ替え、実際の確率値の表示ができます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-225">Because the underlying statistics that were used to build the image in the viewer are saved to Excel as tables, you can filter and sort, and view the actual probability values.</span></span>  
  
     <span data-ttu-id="b6d7f-226">Excel の使用に加えて、Visio 用のクラスター ビューアーを試すことをお勧めします。データ ポイントを表示できる他に、グラフを全面的に変更し強化することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-226">In addition to using Excel, we recommend that you try the cluster viewer for Visio, which also allows you to not just view data points but also extensively modify and enhance the graph.</span></span> <span data-ttu-id="b6d7f-227">詳細については、「[クラスターダイアグラムのチュートリアル &#40;データマイニングアドイン&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-227">For more information, see [Cluster Diagram Walkthrough &#40;Data Mining Add-ins&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).</span></span>  
  
 <span data-ttu-id="b6d7f-228">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="b6d7f-228">**Tips**</span></span>  
  
 <span data-ttu-id="b6d7f-229">いくつかの洞察を顧客のグループに提供した後、What-if シナリオ &#40;使用して、excel[用のテーブル分析ツール&#41;](what-if-scenario-table-analysis-tools-for-excel.md)またはゴールシークシナリオを使用して、 [excel&#41;ツールのテーブル分析ツールを &#40;](goal-seek-scenario-table-analysis-tools-for-excel.md)して、結果に影響を与えるように変更される可能性のある要素を調査します。</span><span class="sxs-lookup"><span data-stu-id="b6d7f-229">After getting some insights into groups of customers, try using the [What-If Scenario &#40;Table Analysis Tools for Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md) or [Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md) tools, to explore factors in the model that might be changed to affect the outcome.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d7f-230">参照</span><span class="sxs-lookup"><span data-stu-id="b6d7f-230">See Also</span></span>  
 <span data-ttu-id="b6d7f-231">[Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="b6d7f-231">[Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="b6d7f-232">クラスターウィザード &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="b6d7f-232">Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
