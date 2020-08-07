---
title: デシジョンツリーモデルの調査 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2e1472c2-3f3e-4dae-acb3-62fca374d397
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a2c7f063d7cb73cdc431fb1bc94188c9266c10c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719118"
---
# <a name="exploring-the-decision-tree-model-basic-data-mining-tutorial"></a><span data-ttu-id="35763-102">デシジョン ツリー モデルの検証 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="35763-102">Exploring the Decision Tree Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="35763-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムは、自転車の購入に影響する列をトレーニング セットのその他の列に基づいて予測します。</span><span class="sxs-lookup"><span data-stu-id="35763-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm predicts which columns influence the decision to purchase a bike based upon the remaining columns in the training set.</span></span>  
  

  
##  <a name="decision-tree-tab"></a><a name="Decision_Tree_Tab"></a><span data-ttu-id="35763-104">[デシジョンツリー] タブ</span><span class="sxs-lookup"><span data-stu-id="35763-104">Decision Tree Tab</span></span>  
 <span data-ttu-id="35763-105">[**デシジョンツリー** ] タブでは、データセット内の予測可能な属性ごとにデシジョンツリーを表示できます。</span><span class="sxs-lookup"><span data-stu-id="35763-105">On the **Decision Tree** tab, you can view decision trees for every predictable attribute in the dataset.</span></span>  
  
 <span data-ttu-id="35763-106">この場合、モデルでは自転車購入者が1つだけ予測されるため、表示できるツリーは1つだけです。</span><span class="sxs-lookup"><span data-stu-id="35763-106">In this case, the model predicts only one column, Bike Buyer, so there is only one tree to view.</span></span> <span data-ttu-id="35763-107">複数のツリーがある場合は、[**ツリー** ] ボックスを使用して別のツリーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="35763-107">If there were more trees, you could use the **Tree** box to choose another tree.</span></span>  
  
 <span data-ttu-id="35763-108">`TM_Decision_Tree`デシジョンツリービューアーでモデルを表示すると、グラフの左側に最も重要な属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="35763-108">As you view the `TM_Decision_Tree` model in the Decision Tree viewer, you can see the most important attributes at the left side of the chart.</span></span> <span data-ttu-id="35763-109">"最も重要" とは、これらの属性が結果に最大の影響を与えることを意味します。</span><span class="sxs-lookup"><span data-stu-id="35763-109">"Most important" means that these attributes have the greatest influence on the outcome.</span></span> <span data-ttu-id="35763-110">ツリーの下寄り (グラフの右側) にある属性は、あまり大きな効果を及ぼしません。</span><span class="sxs-lookup"><span data-stu-id="35763-110">Attributes further down the tree (to the right of the chart) have less of an effect.</span></span>  
  
 <span data-ttu-id="35763-111">この例では、自転車購入の予測にとって最も重要な要素は年齢です。</span><span class="sxs-lookup"><span data-stu-id="35763-111">In this example, age is the single most important factor in predicting bike buying.</span></span> <span data-ttu-id="35763-112">このモデルは顧客を年齢でグループ化し、年齢グループごとに、次に重要な属性を示します。</span><span class="sxs-lookup"><span data-stu-id="35763-112">The model groups customers by age, and then shows the next more important attribute for each age group.</span></span> <span data-ttu-id="35763-113">たとえば、34 歳から 40 歳の顧客グループでは、年齢の次に強い予測子は所有している自動車の台数です。</span><span class="sxs-lookup"><span data-stu-id="35763-113">For example, in the group of customers aged 34 to 40, the number of cars owned is the strongest predictor after age.</span></span>  
  
#### <a name="to-explore-the-model-in-the-decision-tree-tab"></a><span data-ttu-id="35763-114">[デシジョン ツリー] タブでモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="35763-114">To explore the model in the Decision Tree tab</span></span>  
  
1.  <span data-ttu-id="35763-115">**データマイニングデザイナー**で [**マイニングモデルビューアー** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="35763-115">Select the **Mining Model Viewer** tab in **Data Mining Designer**.</span></span>  
  
     <span data-ttu-id="35763-116">既定では、構造に追加された最初のモデル (この場合は) に対してデザイナーが開き `TM_Decision_Tree` ます。</span><span class="sxs-lookup"><span data-stu-id="35763-116">By default, the designer opens to the first model that was added to the structure -- in this case, `TM_Decision_Tree`.</span></span>  
  
2.  <span data-ttu-id="35763-117">虫眼鏡ボタンを使用してツリーの表示サイズを調整します。</span><span class="sxs-lookup"><span data-stu-id="35763-117">Use the magnifying glass buttons to adjust the size of the tree display.</span></span>  
  
     <span data-ttu-id="35763-118">既定では、ツリーの上位 3 レベルのみが [!INCLUDE[msCoName](../includes/msconame-md.md)] ツリー ビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="35763-118">By default, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Tree Viewer shows only the first three levels of the tree.</span></span> <span data-ttu-id="35763-119">ツリーの階層が 3 レベル未満の場合は、既存のすべてのレベルがビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="35763-119">If the tree contains fewer than three levels, the viewer shows only the existing levels.</span></span> <span data-ttu-id="35763-120">さらに多くのレベルを表示するには、[**レベルの表示]** スライダーまたは**既定の展開**の一覧を使用します。</span><span class="sxs-lookup"><span data-stu-id="35763-120">You can view more levels by using the **Show Level** slider or the **Default Expansion** list.</span></span>  
  
3.  <span data-ttu-id="35763-121">4番目のバーにスライドショーの**レベル**を移動します。</span><span class="sxs-lookup"><span data-stu-id="35763-121">Slide **Show Level** to the fourth bar.</span></span>  
  
4.  <span data-ttu-id="35763-122">[**背景**値をに変更 `1` します。</span><span class="sxs-lookup"><span data-stu-id="35763-122">Change the **Background** value to `1`.</span></span>  
  
     <span data-ttu-id="35763-123">[**背景**] の設定を変更すると、[自転車購入者] の対象の値を持つ各ノードのケース数をすばやく確認でき `1` ます。</span><span class="sxs-lookup"><span data-stu-id="35763-123">By changing the **Background** setting, you can quickly see the number of cases in each node that have the target value of `1` for [Bike Buyer].</span></span> <span data-ttu-id="35763-124">このシナリオでは、各ケースが顧客を表すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="35763-124">Remember that in this particular scenario, each case represents a customer.</span></span> <span data-ttu-id="35763-125">この値は、 `1` 顧客が以前に自転車を購入したことを示します。値**0**は、顧客が自転車を購入していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="35763-125">The value `1` indicates that the customer previously purchased a bike; the value **0** indicates that the customer has not purchased a bike.</span></span> <span data-ttu-id="35763-126">ノードの色が濃いほど、対象の値を持つケースの割合が高いことを示します。</span><span class="sxs-lookup"><span data-stu-id="35763-126">The darker the shading of the node, the higher the percentage of cases in the node that have the target value.</span></span>  
  
5.  <span data-ttu-id="35763-127">"**すべて**" というラベルが付いたノードの上にカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="35763-127">Place your cursor over the node labeled **All**.</span></span> <span data-ttu-id="35763-128">ツールヒントに次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="35763-128">An tooltip will display the following information:</span></span>  
  
    -   <span data-ttu-id="35763-129">ケースの総数</span><span class="sxs-lookup"><span data-stu-id="35763-129">Total number of cases</span></span>  
  
    -   <span data-ttu-id="35763-130">自転車を購入していないケースの数</span><span class="sxs-lookup"><span data-stu-id="35763-130">Number of non bike buyer cases</span></span>  
  
    -   <span data-ttu-id="35763-131">自転車を購入したケースの数</span><span class="sxs-lookup"><span data-stu-id="35763-131">Number of bike buyer cases</span></span>  
  
    -   <span data-ttu-id="35763-132">[Bike Buyer] の値がないケースの数</span><span class="sxs-lookup"><span data-stu-id="35763-132">Number of cases with missing values for [Bike Buyer]</span></span>  
  
     <span data-ttu-id="35763-133">そのほか、ツリーの任意のノードの上にカーソルを置いて、直前のノードからそのノードに到達するために必要な条件を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="35763-133">Alternately, place your cursor over any node in the tree to see the condition that is required to reach that node from the node that comes before it.</span></span> <span data-ttu-id="35763-134">また、[**マイニング凡例**] でも同じ情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="35763-134">You can also view this same information in the **Mining Legend**.</span></span>  
  
6.  <span data-ttu-id="35763-135">**Age >= 34、< 41**のノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="35763-135">Click on the node for **Age >=34 and < 41**.</span></span> <span data-ttu-id="35763-136">ノード上の細い横棒としてヒストグラムが表示されます。ヒストグラムは、その年齢層の顧客の、以前に自転車を購入した顧客 (ピンク) と購入していない顧客 (青) の分布を表します。</span><span class="sxs-lookup"><span data-stu-id="35763-136">The histogram is displayed as a thin horizontal bar across the node and represents the distribution of customers in this age range who previously did (pink) and did not (blue) purchase a bike.</span></span> <span data-ttu-id="35763-137">ビューアーからは、車の所有台数が 0 ～ 1 台の 34 ～ 40 歳の顧客が自転車を購入する可能性が高いことがわかります。</span><span class="sxs-lookup"><span data-stu-id="35763-137">The Viewer shows us that customers between the ages of 34 and 40 with one or no cars are likely to purchase a bike.</span></span> <span data-ttu-id="35763-138">さらに詳しく見ると、顧客の年齢が 38 ～ 40 歳の場合にはその可能性がさらに高くなることもわかります。</span><span class="sxs-lookup"><span data-stu-id="35763-138">Taking it one step further, we find that the likelihood to purchase a bike increases if the customer is actually age 38 to 40.</span></span>  
  
 <span data-ttu-id="35763-139">ここでは、構造とモデルを作成したときにドリルスルーを有効にしてあるため、モデル ケースやマイニング構造から詳細情報を取得することができます。これには、マイニング モデルには含まれていなかった列 (emailAddress や FirstName など) も含まれます。</span><span class="sxs-lookup"><span data-stu-id="35763-139">Because you enabled drillthrough when you created the structure and model, you can retrieve detailed information from the model cases and mining structure, including those columns that were not included in the mining model (e.g., emailAddress, FirstName).</span></span>  
  
 <span data-ttu-id="35763-140">詳細については、「 [ドリルスルー クエリ (データ マイニング)](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="35763-140">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-drill-through-to-case-data"></a><span data-ttu-id="35763-141">ケース データにドリルスルーするには</span><span class="sxs-lookup"><span data-stu-id="35763-141">To drill through to case data</span></span>  
  
1.  <span data-ttu-id="35763-142">ノードを右クリックし、[**ドリルスルー** ]、[**モデル列のみ**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="35763-142">Right-click a node, and select **Drill Through** then **Model Columns Only**.</span></span>  
  
     <span data-ttu-id="35763-143">各トレーニング ケースの詳細がスプレッドシート形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="35763-143">The details for each training case are displayed in spreadsheet format.</span></span> <span data-ttu-id="35763-144">これらの詳細は、マイニング構造を作成するときにケース テーブルとして選択した vTargetMail ビューから取得されています。</span><span class="sxs-lookup"><span data-stu-id="35763-144">These details come from the vTargetMail view that you selected as the case table when building the mining structure.</span></span>  
  
2.  <span data-ttu-id="35763-145">ノードを右クリックし、[**ドリルスルー** ]、[**モデルおよび構造列**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="35763-145">Right-click a node, and select **Drill Through** then **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="35763-146">同じスプレッドシートの末尾に構造列が追加されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="35763-146">The same spreadsheet displays with the structure columns appended to the end.</span></span>  
  
  
###  <a name="dependency-network-tab"></a><a name="Dependency_Network_Tab"></a><span data-ttu-id="35763-147">[依存関係ネットワーク] タブ</span><span class="sxs-lookup"><span data-stu-id="35763-147">Dependency Network Tab</span></span>  
 <span data-ttu-id="35763-148">[**依存関係ネットワーク**] タブには、マイニングモデルの予測機能に寄与する属性間のリレーションシップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="35763-148">The **Dependency Network** tab displays the relationships between the attributes that contribute to the predictive ability of the mining model.</span></span> <span data-ttu-id="35763-149">依存関係ネットワーク ビューアーを使用すると、自転車の購入の予測において Age と Region が重要な要素になるという先ほどの調査結果が補強されます。</span><span class="sxs-lookup"><span data-stu-id="35763-149">The Dependency Network viewer reinforces our findings that Age and Region are important factors in predicting bike buying.</span></span>  
  
##### <a name="to-explore-the-model-in-the-dependency-network-tab"></a><span data-ttu-id="35763-150">[依存関係ネットワーク] タブでモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="35763-150">To explore the model in the Dependency Network tab</span></span>  
  
1.  <span data-ttu-id="35763-151">ノードをクリックすると、 `Bike Buyer` その依存関係が識別されます。</span><span class="sxs-lookup"><span data-stu-id="35763-151">Click the `Bike Buyer` node to identify its dependencies.</span></span>  
  
     <span data-ttu-id="35763-152">依存関係ネットワークの中央ノードは、 `Bike Buyer` マイニングモデル内の予測可能な属性を表します。</span><span class="sxs-lookup"><span data-stu-id="35763-152">The center node for the dependency network, `Bike Buyer`, represents the predictable attribute in the mining model.</span></span> <span data-ttu-id="35763-153">このグラフでは、予測可能な属性に影響を及ぼす、接続しているすべてのノードが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="35763-153">The graph highlights any connected nodes that have an effect on the predictable attribute.</span></span>  
  
2.  <span data-ttu-id="35763-154">[**すべてのリンク**スライダーを調整して、最も影響の多い属性を特定します。</span><span class="sxs-lookup"><span data-stu-id="35763-154">Adjust the **All Links** slider to identify the most influential attribute.</span></span>  
  
     <span data-ttu-id="35763-155">スライダーをドラッグすると、[自転車の購入者] 列に弱い効果しかない属性がグラフから削除されます。</span><span class="sxs-lookup"><span data-stu-id="35763-155">As you drag down the slider, attributes that have only a weak effect on the [Bike Buyer] column are removed from the graph.</span></span> <span data-ttu-id="35763-156">スライダーを調整すると、顧客が自転車を購入するかどうかの予測は、年齢と地域に最も大きく左右されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="35763-156">By adjusting the slider, you can discover that Age and Region are the greatest factors in predicting whether someone is a bike buyer.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="35763-157">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="35763-157">Related Tasks</span></span>  
 <span data-ttu-id="35763-158">他の種類のモデルを使用してデータを探索するには、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="35763-158">See these topics to explore the data using the other kinds of models.</span></span>  
  
-   [<span data-ttu-id="35763-159">「基本的なデータマイニングチュートリアル」 &#40;クラスターモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="35763-159">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="35763-160">Naive Bayes Model &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="35763-160">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="35763-161">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="35763-161">Next Task in Lesson</span></span>  
 [<span data-ttu-id="35763-162">「基本的なデータマイニングチュートリアル」 &#40;クラスターモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="35763-162">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="35763-163">参照</span><span class="sxs-lookup"><span data-stu-id="35763-163">See Also</span></span>  
 <span data-ttu-id="35763-164">[マイニングモデルビューアーのタスクと操作方法](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="35763-164">[Mining Model Viewer Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="35763-165">[[デシジョンツリー] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="35763-165">[Decision Tree Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="35763-166">[[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="35763-166">[Dependency Network Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md) </span></span>  
 [<span data-ttu-id="35763-167">Microsoft ツリー ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="35763-167">Browse a Model Using the Microsoft Tree Viewer</span></span>](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
  
