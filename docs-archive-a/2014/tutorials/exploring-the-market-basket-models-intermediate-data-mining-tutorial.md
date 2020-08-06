---
title: マーケットバスケットモデルの調査 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: da1c9cb7-6c32-4b9b-96ec-ecea772aeb77
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6246aa9330042f0e8033b6f2633a3ed24331ba7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720493"
---
# <a name="exploring-the-market-basket-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="2aad4-102">マーケット バスケット モデルの検証 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="2aad4-102">Exploring the Market Basket Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="2aad4-103">モデルの作成が完了したので、 `Association` [!INCLUDE[msCoName](../includes/msconame-md.md)] データマイニングデザイナーの [**マイニングモデルビューアー** ] タブにある [関連付けビューアー] を使用してモデルを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-103">Now that you have built the `Association` model, you can explore it by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer in the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="2aad4-104">このチュートリアルでは、ビューアーを使用してアイテム間の関係を検証する方法を、順を追って学習します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-104">This tutorial walks you through using the viewer to explore relationships between items.</span></span> <span data-ttu-id="2aad4-105">ビューアーを使用すると、どの製品とどの製品がよく一緒に表示されるかが一目でわかるほか、新たなパターンの概観も可能です。</span><span class="sxs-lookup"><span data-stu-id="2aad4-105">The viewer helps you see at a glance which products tend to appear together, and get a general idea of the emerging patterns.</span></span>  
  
 <span data-ttu-id="2aad4-106">アソシエーションビューアーには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] **ルール**、**アイテムセット**、および**依存関係ネットワーク**の3つのタブがあります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-106">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer contains three tabs: **Rules**, **Itemsets**, and **Dependency Network**.</span></span> <span data-ttu-id="2aad4-107">これらのタブにはデータがそれぞれ少しずつ異なる形で表示されるため、モデルを検証する際には、異なるペインの間を何度も切り替えながら調査を進めるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="2aad4-107">Because each tab reveals a slightly different view of the data, when you are exploring a model, you will typically switch back and forth between the different panes several times as you pursue insights.</span></span>  
  
-   <span data-ttu-id="2aad4-108">[[依存関係ネットワーク] タブ](#bkmk_DepNet)</span><span class="sxs-lookup"><span data-stu-id="2aad4-108">[Dependency Network tab](#bkmk_DepNet)</span></span>  
  
-   <span data-ttu-id="2aad4-109">[[アイテムセット] タブ](#bkmk_Itemsets)</span><span class="sxs-lookup"><span data-stu-id="2aad4-109">[Itemsets tab](#bkmk_Itemsets)</span></span>  
  
-   <span data-ttu-id="2aad4-110">[[規則] タブ](#bkmk_Rules)</span><span class="sxs-lookup"><span data-stu-id="2aad4-110">[Rules tab](#bkmk_Rules)</span></span>  
  
-   [<span data-ttu-id="2aad4-111">汎用コンテンツ ツリー ビューアー</span><span class="sxs-lookup"><span data-stu-id="2aad4-111">Generic Content View</span></span>](#bkmk_ContentViewer)  
  
 <span data-ttu-id="2aad4-112">このチュートリアルでは、[**依存関係ネットワーク**] タブから開始し、[**ルール**] タブと [**アイテムセット**] タブを使用して、ビューアーに表示されるリレーションシップについて理解を深めます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-112">For this tutorial, you will start on the **Dependency Network** tab, and then use the **Rules** tab and **Itemsets** tab to deepen your understanding of the relationships revealed in the viewer.</span></span> <span data-ttu-id="2aad4-113">また、 **Microsoft 汎用コンテンツツリービューアー**を使用して、個々のルールまたはアイテムセットの詳細な統計情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-113">You will also use the **Microsoft Generic Content Tree Viewer** to retrieve detailed statistics for individual rules or itemsets.</span></span>  
  
##  <a name="dependency-network-tab"></a><a name="bkmk_DepNet"></a><span data-ttu-id="2aad4-114">[依存関係ネットワーク] タブ</span><span class="sxs-lookup"><span data-stu-id="2aad4-114">Dependency Network Tab</span></span>  
 <span data-ttu-id="2aad4-115">[**依存関係ネットワーク**] タブでは、モデル内のさまざまな項目の相互作用を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-115">With the **Dependency Network** tab, you can investigate the interaction of the different items in the model.</span></span> <span data-ttu-id="2aad4-116">ビューアーの各ノードはアイテムを表し、アイテム間を結ぶ線はルールを表します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-116">Each node in the viewer represents an item, while the lines between them represent rules.</span></span> <span data-ttu-id="2aad4-117">ノードを選択すると、選択したアイテムが他のどのノードによって予測されるか、また現在のアイテムがどのアイテムを予測するかがわかります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-117">By selecting a node, you can see which other nodes predict the selected item, or which items the current item predicts.</span></span> <span data-ttu-id="2aad4-118">アイテム間に双方向の関係がある (つまり同一トランザクション内に発生する可能性が高い) 場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-118">In some cases, there is a two-way association between items, meaning that they often appear in the same transaction.</span></span> <span data-ttu-id="2aad4-119">タブの下部にある色の凡例を参照すると、関係の方向を確認できます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-119">You can refer to the color legend at the bottom of the tab to determine the direction of the association.</span></span>  
  
 <span data-ttu-id="2aad4-120">2 つのアイテムを結ぶ線は、それらのアイテムが同じトランザクションに含まれる可能性が高いことを示しています。</span><span class="sxs-lookup"><span data-stu-id="2aad4-120">A line connecting two items means that these items are likely to appear in a transaction together.</span></span> <span data-ttu-id="2aad4-121">つまり、顧客がそれらのアイテムをまとめて購入する可能性が高いということになります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-121">In other words, customers are likely to buy these items together.</span></span> <span data-ttu-id="2aad4-122">スライダーはルールの確率に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="2aad4-122">The slider is associated with the probability of the rule.</span></span> <span data-ttu-id="2aad4-123">スライダーを下方向に移動すると、緊密な関係 (確率の高いルール) のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-123">Move the slider up or down to filter out weak associations, meaning rules with low probability.</span></span>  
  
 <span data-ttu-id="2aad4-124">依存関係ネットワークグラフには、ペアの規則が表示されます。これは、論理的に->B として表すことができます。つまり、製品 A を購入した場合は、製品 B が使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-124">The dependency network graph shows pairwise rules, which can be represented logically as A->B, meaning if Product A is purchased, then Product B is likely.</span></span> <span data-ttu-id="2aad4-125">グラフでは、型 AB->C の規則を表示できません。</span><span class="sxs-lookup"><span data-stu-id="2aad4-125">The graph cannot show rules of the type AB->C.</span></span> <span data-ttu-id="2aad4-126">すべてのルールが表示される位置までスライダーを動かしてもグラフに線が表示されない場合は、アルゴリズム パラメーターの条件を満たす 1 対 1 のルールが存在しないことになります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-126">If you move the slider to show all rules but still do not see any lines in the graph, it means that there were no pairwise rules that met the criteria of the algorithm parameters.</span></span>  
  
 <span data-ttu-id="2aad4-127">属性名の最初の数文字を入力してノードを名前で検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-127">You can also find nodes by name, by typing the first letters of the attribute name.</span></span> <span data-ttu-id="2aad4-128">詳細については、「[[ノードの検索] ダイアログ ボックス (マイニング モデル ビューアー)](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aad4-128">For more information, see [Find Node Dialog Box &#40;Mining Model Viewer&#41;](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md).</span></span>  
  
#### <a name="to-open-the-association-mode-in-the-microsoft-assocaition-rules-viewer"></a><span data-ttu-id="2aad4-129">Microsoft アソシエーション ルール ビューアーで Association モデルを開くには</span><span class="sxs-lookup"><span data-stu-id="2aad4-129">To open the Association mode in the Microsoft Assocaition Rules Viewer</span></span>  
  
1.  <span data-ttu-id="2aad4-130">**ソリューションエクスプローラー**で、Association 構造をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-130">In **Solution Explorer**, double-click the Association structure.</span></span>  
  
2.  <span data-ttu-id="2aad4-131">データ マイニング デザイナーで、 **[マイニング モデル ビューアー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-131">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="2aad4-132">[**マイニングモデル**] ボックスの一覧で、マイニングモデルの一覧から [関連付け] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-132">Select Association from the list of mining models in the **Mining Model** dropdown list.</span></span>  
  
#### <a name="to-navigate-the-dependency-graph-and-locate-specific-nodes"></a><span data-ttu-id="2aad4-133">依存関係のグラフを操作して特定のノードを見つけるには</span><span class="sxs-lookup"><span data-stu-id="2aad4-133">To navigate the dependency graph and locate specific nodes</span></span>  
  
1.  <span data-ttu-id="2aad4-134">[**マイニングモデルビューアー** ] タブで、[**依存関係ネットワーク**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-134">In the **Mining Model Viewer** tab, click the **Dependency Network** tab.</span></span>  
  
2.  <span data-ttu-id="2aad4-135">各ノードのラベルを簡単に表示できるようにするには、[**拡大**] を何度かクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-135">Click **Zoom In** several times, until you can easily view the labels for each node.</span></span>  
  
     <span data-ttu-id="2aad4-136">既定では、すべてのノードが見えるようにグラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-136">By default, the graph displays with all nodes visible.</span></span> <span data-ttu-id="2aad4-137">複雑なモデルでは、ノードの数が多いためにそれぞれのノードが非常に小さくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-137">In a complex model, there may be many nodes, making each node quite small.</span></span>  
  
3.  <span data-ttu-id="2aad4-138">**+** ビューアーの右下隅にある符号をクリックし、マウスボタンを押しながらグラフをパンします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-138">Click the **+** sign in the lower right-hand corner of the viewer and hold down the mouse button to pan around the graph.</span></span>  
  
4.  <span data-ttu-id="2aad4-139">ビューアーの左側で、スライダーをドラッグして、[**すべてのリンク**] (既定) からスライダーコントロールの下部に移動します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-139">On the left side of the viewer, drag the slider down, moving it from **All Links** (the default) to the bottom of the slider control.</span></span>  
  
5.  <span data-ttu-id="2aad4-140">グラフが更新されて、最も強いアソシエーション (Touring Tire と Touring Tire Tube の間のアソシエーション) のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-140">The viewer updates the graph to now show only the strongest association, between the Touring Tire and Touring Tire Tube items.</span></span>  
  
6.  <span data-ttu-id="2aad4-141">[**ツーリングタイヤチューブ = Existing**] というラベルの付いたノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-141">Click the node labeled **Touring Tire Tube = Existing**.</span></span>  
  
     <span data-ttu-id="2aad4-142">グラフが更新されて、このアイテムとの間に強い関連があるアイテムのみが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-142">The graph is updated to highlight only items that are strongly related to this item.</span></span> <span data-ttu-id="2aad4-143">2 つのアイテム間の矢印の向きに注目してください。</span><span class="sxs-lookup"><span data-stu-id="2aad4-143">Note the direction of the arrow between the two items.</span></span>  
  
7.  <span data-ttu-id="2aad4-144">ビューアーの左側で、スライダーをドラッグして一番下から真ん中あたりまで戻します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-144">On the left side of the viewer, drag the slider up again, moving it from the bottom to around the middle.</span></span>  
  
     <span data-ttu-id="2aad4-145">2 つのアイテムを結ぶ矢印の変化に注目してください。</span><span class="sxs-lookup"><span data-stu-id="2aad4-145">Note the changes in the arrow that connects the two items.</span></span>  
  
8.  <span data-ttu-id="2aad4-146">[依存関係ネットワーク] ウィンドウの上部にあるドロップダウンリストから [**属性名のみ表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-146">Select **Show attribute name only** from the dropdown list at the top of the Dependency Network pane.</span></span>  
  
     <span data-ttu-id="2aad4-147">グラフのテキスト ラベルが更新されて、モデル名のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-147">The text labels in the graph are updated to show only the model name.</span></span>  
  
 [<span data-ttu-id="2aad4-148">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="2aad4-148">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="itemsets-tab"></a><a name="bkmk_Itemsets"></a><span data-ttu-id="2aad4-149">[アイテムセット] タブ</span><span class="sxs-lookup"><span data-stu-id="2aad4-149">Itemsets Tab</span></span>  
 <span data-ttu-id="2aad4-150">次に、Touring Tire と Touring Tire Tube という 2 つの製品についてモデルによって生成された、ルールとアイテムセットの詳細を調べます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-150">Next, you will learn more about the rules and itemsets generated by the model for the Touring Tire and Touring Tire Tube products.</span></span> <span data-ttu-id="2aad4-151">[**アイテムセット**] タブには、アソシエーションアルゴリズムによって検出されたアイテムセットに関連する3つの重要な情報が表示され [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-151">The **Itemsets** tab displays three important pieces of information that relate to the itemsets that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm discovers:</span></span>  
  
-   <span data-ttu-id="2aad4-152">**サポート:** アイテムセットが発生するトランザクションの数。</span><span class="sxs-lookup"><span data-stu-id="2aad4-152">**Support:** The number of transactions in which the itemset occurs.</span></span>  
  
-   <span data-ttu-id="2aad4-153">**サイズ:** アイテムセット内のアイテムの数。</span><span class="sxs-lookup"><span data-stu-id="2aad4-153">**Size:** The number of items in the itemset.</span></span>  
  
-   <span data-ttu-id="2aad4-154">**項目:** 各アイテムセットに含まれるアイテムの一覧です。</span><span class="sxs-lookup"><span data-stu-id="2aad4-154">**Items:** A list of the items included in each itemset.</span></span>  
  
 <span data-ttu-id="2aad4-155">アルゴリズム パラメーターの設定方法によっては、多数のアイテムセットが生成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-155">Depending on how the algorithm parameters are set, the algorithm might generate many itemsets.</span></span> <span data-ttu-id="2aad4-156">ビューアーに返される各アイテムセットは、アイテムが販売されたトランザクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-156">Each itemset that is returned in the viewer represents transactions in which the item was sold.</span></span> <span data-ttu-id="2aad4-157">[**アイテムセット**] タブの上部にあるコントロールを使用して、指定した最小のサポートとアイテムセットのサイズを含むアイテムセットだけを表示するようにビューアーをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-157">By using the controls at the top of the **Itemsets** tab, you can filter the viewer to show only the itemsets that contain a specified minimum support and itemset size.</span></span>  
  
 <span data-ttu-id="2aad4-158">別のマイニング モデルを使用していてアイテムセットが表示されない場合、それは、アルゴリズム パラメーターの条件を満たすアイテムセットが存在しないからです。</span><span class="sxs-lookup"><span data-stu-id="2aad4-158">If you are working with a different mining model and no itemsets are listed, it is because no itemsets met the criteria of the algorithm parameters.</span></span> <span data-ttu-id="2aad4-159">そのような場合は、サポートの値がもっと低いアイテムセットが許可されるようにアルゴリズム パラメーターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-159">In such a scenario, you can change the algorithm parameters to allow itemsets that have lower support.</span></span>  
  
#### <a name="to-filter-the-itemsets-that-are-shown-in-the-viewer-by-name"></a><span data-ttu-id="2aad4-160">ビューアーに表示されるアイテムセットを名前で絞り込むには</span><span class="sxs-lookup"><span data-stu-id="2aad4-160">To filter the itemsets that are shown in the viewer by name</span></span>  
  
1.  <span data-ttu-id="2aad4-161">ビューアーの [**アイテムセット**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-161">Click the **Itemsets** tab of the viewer.</span></span>  
  
2.  <span data-ttu-id="2aad4-162">[アイテムセットの**フィルター** ] ボックスに「」と入力し、 `Touring Tire` ボックスの外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-162">In the **Filter Itemset** box, type `Touring Tire`, and then click outside the box.</span></span>  
  
     <span data-ttu-id="2aad4-163">その文字列を含むすべてのアイテムが返されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-163">The filter returns all items that contain this string.</span></span>  
  
3.  <span data-ttu-id="2aad4-164">[**表示**] ボックスの一覧で、[**属性名のみ表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-164">In the **Show** list, select **Show attribute name only**.</span></span>  
  
4.  <span data-ttu-id="2aad4-165">[**長い名前を表示する**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-165">Select the **Show long name** check box.</span></span>  
  
     <span data-ttu-id="2aad4-166">アイテムセットの一覧が更新されて、"Touring Tire" という文字列を含むアイテムセットのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-166">The list of itemsets is updated to show only the itemsets that contain the string Touring Tire.</span></span> <span data-ttu-id="2aad4-167">アイテムセットの長い名前には、各アイテムの属性と値を含むテーブルの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-167">The long name of the itemset includes the name of the table that contains the attribute and value for each item.</span></span>  
  
5.  <span data-ttu-id="2aad4-168">[**長い名前を表示する**] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-168">Clear the **Show long name** check box.</span></span>  
  
     <span data-ttu-id="2aad4-169">アイテムセットの一覧が更新されて、短い名前のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-169">The list of itemsets is updated to show only the short name.</span></span>  
  
 <span data-ttu-id="2aad4-170">**サポート**列の値は、各アイテムセットのトランザクションの数を示します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-170">The values in the **Support** column indicate the number of transactions for each itemset.</span></span> <span data-ttu-id="2aad4-171">アイテムセットのトランザクションとは、アイテムセット内のすべてのアイテムを含む購入のことです。</span><span class="sxs-lookup"><span data-stu-id="2aad4-171">A transaction for an itemset means a purchase that included all the items in the itemset.</span></span>  
  
 <span data-ttu-id="2aad4-172">既定では、アイテムセットはサポートの降順でビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-172">By default, the viewer lists the itemsets in descending order by support.</span></span> <span data-ttu-id="2aad4-173">列のヘッダーをクリックすると、アイテムセットを別の列 (アイテムセットのサイズや名前など) で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-173">You can click on the column headers to sort by a different column, such as the itemset size or name.</span></span> <span data-ttu-id="2aad4-174">アイテムセットに含まれる個々のトランザクションの詳細に関心がある場合は、アイテムセットから個々のケースにドリルスルーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-174">If you are interested in learning more about the individual transactions that are included in an itemset, you can drill through from the itemsets to the individual cases.</span></span> <span data-ttu-id="2aad4-175">ドリルスルーの結果には、モデルでは使用されなかった顧客の収入レベルと顧客 ID の構造列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-175">The structure columns in the drillthrough results are the customer's income level and customer ID, which were not used in the model.</span></span>  
  
#### <a name="to-view-details-for-an-itemset"></a><span data-ttu-id="2aad4-176">アイテムセットの詳細を表示するには</span><span class="sxs-lookup"><span data-stu-id="2aad4-176">To view details for an itemset</span></span>  
  
1.  <span data-ttu-id="2aad4-177">アイテムセットの一覧で、[**アイテム**セット] 列見出しをクリックして、名前で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-177">In the list of itemsets, click the **Itemset** column heading to sort by name.</span></span>  
  
2.  <span data-ttu-id="2aad4-178">`Touring Tire`(2 番目の項目を含まない) 項目を探します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-178">Locate the item, `Touring Tire` (with no second item).</span></span>  
  
3.  <span data-ttu-id="2aad4-179">項目を右クリックし、[ドリルスルー] をクリックして、[ `Touring Tire` **モデル列と構造列**] を選択します。 **Drill Through**</span><span class="sxs-lookup"><span data-stu-id="2aad4-179">Right-click the item, `Touring Tire`, select **Drill Through**, and then select **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="2aad4-180">[**ドリル**スルー] ダイアログボックスには、このアイテムセットのサポートとして使用される個々のトランザクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-180">The **Drill Through** dialog box displays the individual transactions used as support for this itemset.</span></span>  
  
4.  <span data-ttu-id="2aad4-181">入れ子になったテーブル vAssocSeqLineItems を展開して、トランザクションの実際の購入の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-181">Expand the nested table, vAssocSeqLineItems, to view the actual list of purchases in the transaction.</span></span>  
  
#### <a name="to-filter-itemsets-by-support-or-size"></a><span data-ttu-id="2aad4-182">アイテムセットをサポートまたはサイズで絞り込むには</span><span class="sxs-lookup"><span data-stu-id="2aad4-182">To filter itemsets by support or size</span></span>  
  
1.  <span data-ttu-id="2aad4-183">[アイテムセットの**フィルター** ] ボックスに表示されるテキストをクリアします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-183">Clear any text that might be in the **Filter Itemset** box.</span></span> <span data-ttu-id="2aad4-184">テキスト フィルターと数値フィルターを同時に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2aad4-184">You cannot use a text filter together with a numeric filter.</span></span>  
  
2.  <span data-ttu-id="2aad4-185">[**最小サポート**] ボックスに「100」と入力し、ビューアーの背景をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-185">In the **Minimum support** box, type 100, and then click the background of the viewer.</span></span>  
  
     <span data-ttu-id="2aad4-186">アイテムセットの一覧が更新されて、サポートが 100 以上のアイテムセットのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-186">The list of itemsets is updated to show only itemsets with support of at least 100.</span></span>  
  
 [<span data-ttu-id="2aad4-187">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="2aad4-187">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="rules-tab"></a><a name="bkmk_Rules"></a><span data-ttu-id="2aad4-188">[規則] タブ</span><span class="sxs-lookup"><span data-stu-id="2aad4-188">Rules Tab</span></span>  
 <span data-ttu-id="2aad4-189">[**ルール**] タブには、アルゴリズムによって検出されたルールに関連する次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-189">The **Rules** tab displays the following information that is related to the rules that the algorithm finds.</span></span>  
  
-   <span data-ttu-id="2aad4-190">**確率:** 左辺の項目が指定された場合に、右側の項目の確率として定義*されるルールの確率*。</span><span class="sxs-lookup"><span data-stu-id="2aad4-190">**Probability:** The *likelihood* of a rule, defined as the probability of the right-hand item given the left-hand side item.</span></span>  
  
-   <span data-ttu-id="2aad4-191">**重要度:** ルールの有用性の尺度。</span><span class="sxs-lookup"><span data-stu-id="2aad4-191">**Importance:** A measure of the usefulness of a rule.</span></span> <span data-ttu-id="2aad4-192">この値が大きいほどルールの有効性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-192">A greater value means a better rule.</span></span>  
  
     <span data-ttu-id="2aad4-193">ルールの有効性を判断するための基準として重要度が用意されているのは、確率だけでは誤った判断を招く可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="2aad4-193">Importance is provided to help you gauge the usefulness of a rule, because probability alone can be misleading.</span></span> <span data-ttu-id="2aad4-194">たとえば、プロモーションの一環として各顧客のカートに自動的に水筒が追加される場合は、すべてのトランザクションに水筒が含まれるため、水筒の確率を 1 として予測するルールがモデルによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-194">For example, if every transaction contains a water bottle--perhaps the water bottle is added to each customer's cart automatically as part of a promotion--the model would create a rule predicting that water bottle has a probability of 1.</span></span> <span data-ttu-id="2aad4-195">このルールは、確率に基づく限りはきわめて正確ですが、有用な情報にはなりません。</span><span class="sxs-lookup"><span data-stu-id="2aad4-195">Based on probability alone, this rule is very accurate, but it does not provide useful information.</span></span>  
  
-   <span data-ttu-id="2aad4-196">**ルール:** ルールの定義。</span><span class="sxs-lookup"><span data-stu-id="2aad4-196">**Rule:** The definition of the rule.</span></span> <span data-ttu-id="2aad4-197">マーケット バスケット モデルのルールでは、アイテムの特定の組み合わせを記述します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-197">For a market basket model, a rule describes a specific combination of items.</span></span>  
  
 <span data-ttu-id="2aad4-198">各ルールを使用すると、他のアイテムが存在するかどうかに基づいて、あるアイテムがトランザクションに含まれるかどうかを予測することができます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-198">Each rule can be used to predict the presence of an item in a transaction based on the presence of other items.</span></span> <span data-ttu-id="2aad4-199">[**アイテムセット**] タブと同様に、最も関心のあるルールのみが表示されるようにルールをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-199">Just like in the **Itemsets** tab, you can filter the rules so that only the most interesting rules are shown.</span></span> <span data-ttu-id="2aad4-200">使用しているマイニング モデルにルールが 1 つもない場合は、アルゴリズム パラメーターを変更して、ルールの確率のしきい値を下げることができます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-200">If you are working with a mining model that does not have any rules, you might want to change the algorithm parameters to lower the probability threshold for rules.</span></span>  
  
#### <a name="to-see-only-rules-that-include-the-mountain-200-bicycle"></a><span data-ttu-id="2aad4-201">Mountain-200 という自転車を含むルールのみを表示するには</span><span class="sxs-lookup"><span data-stu-id="2aad4-201">To see only rules that include the Mountain-200 bicycle</span></span>  
  
1.  <span data-ttu-id="2aad4-202">[**マイニングモデルビューアー** ] タブで、[**ルール**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-202">In the **Mining Model Viewer** tab, click the **Rules** tab.</span></span>  
  
2.  <span data-ttu-id="2aad4-203">[**ルールのフィルター** ] ボックスに、「」と入力し `Mountain-200` ます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-203">In the **Filter Rule** box, enter `Mountain-200`.</span></span>  
  
     <span data-ttu-id="2aad4-204">[**長い名前を表示する**] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-204">Clear the **Show long name** check box.</span></span>  
  
3.  <span data-ttu-id="2aad4-205">[**表示**] ボックスの一覧から [**属性名のみ表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-205">From the **Show** list, select **Show attribute name only**.</span></span>  
  
     <span data-ttu-id="2aad4-206">ビューアーには、"" という単語を含む規則のみが表示され `Mountain-200` ます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-206">The viewer will then display only the rules that contain the words "`Mountain-200`".</span></span> <span data-ttu-id="2aad4-207">ルールの確率によって、他のユーザーが自転車を購入したときに、 `Mountain-200` 他の製品も購入される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2aad4-207">The probability of the rule tells you how likely it is that when someone buys a `Mountain-200` bicycle, that person will also buy the other listed product.</span></span>  
  
 <span data-ttu-id="2aad4-208">ルールは確率の降順で表示されますが、列見出しをクリックして並べ替え順を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-208">The rules are ordered by probability in descending order, but you can click the column headings to change the sort order.</span></span> <span data-ttu-id="2aad4-209">特定のルールの詳細に関心がある場合は、ドリルスルーを使用して、そのルールをサポートするケースを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-209">If you are interested in finding out more details about a particular rule, you can use drillthrough to view the supporting cases.</span></span>  
  
#### <a name="to-view-cases-that-support-a-particular-rule"></a><span data-ttu-id="2aad4-210">特定のルールをサポートするケースを表示するには</span><span class="sxs-lookup"><span data-stu-id="2aad4-210">To view cases that support a particular rule</span></span>  
  
1.  <span data-ttu-id="2aad4-211">[**ルール**] タブで、表示するルールを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-211">In the **Rules** tab, right-click the rule that you want to view.</span></span>  
  
2.  <span data-ttu-id="2aad4-212">[**ドリルスルー**] を選択し、[**モデル列のみ**] または [**モデル列と構造列**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-212">Select **Drill Through**, and then select **Model Columns Only**, or **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="2aad4-213">[**ドリルスルー** ] ダイアログボックスには、ウィンドウの上部にあるルールの概要と、ルールのサポートデータとして使用されたすべてのケースの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-213">The **Drill Through** dialog box provides a summary of the rule at the top of the pane, and a list of all cases that were used as supporting data for the rule.</span></span>  
  
 [<span data-ttu-id="2aad4-214">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="2aad4-214">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_ContentViewer"></a><span data-ttu-id="2aad4-215">汎用コンテンツツリービューアー</span><span class="sxs-lookup"><span data-stu-id="2aad4-215">Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="2aad4-216">このビューアーは、アルゴリズムやモデルの種類に関係なく、すべてのモデルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-216">This viewer can be used for all models, regardless of the algorithm or model type.</span></span> <span data-ttu-id="2aad4-217">**Microsoft 汎用コンテンツツリービューアー**は、[**ビューアー** ] ドロップダウンリストから使用できます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-217">The **Microsoft Generic Content Tree Viewer** is available from the **Viewer** drop-down list.</span></span>  
  
 <span data-ttu-id="2aad4-218">コンテンツ ツリーは、マイニング モデルを一連のノードで表したものです。各ノードは、データのサブセットに関する学習済みの知識を表します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-218">A content tree is a representation of a mining model as a series of nodes, where each node represents learned knowledge about some subset of the data.</span></span> <span data-ttu-id="2aad4-219">ノードには、いくつかの特徴が共通するパターン、一連のルール、クラスター、または日付範囲の定義を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-219">The node can contain a pattern, a set of rules, a cluster, or the definition of a range of dates that share some characteristics.</span></span> <span data-ttu-id="2aad4-220">ノードの正確な内容はアルゴリズムや予測可能な属性の種類に応じて変わりますが、内容の全体的な表示は同じです。</span><span class="sxs-lookup"><span data-stu-id="2aad4-220">The exact content of the node differs depending on the algorithm and the type of the predictable attribute, but the general representation of the content is the same.</span></span> <span data-ttu-id="2aad4-221">各ノードを展開して、より詳細なレベルで表示したり、任意のノードの内容をクリップボードにコピーしたりできます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-221">You can expand each node to see increasing levels of detail, and copy the content of any node to the Clipboard.</span></span>  
  
#### <a name="to-view-details-about-the-rule-by-using-the-content-viewer"></a><span data-ttu-id="2aad4-222">コンテンツ ビューアーを使用してルールの詳細を表示するには</span><span class="sxs-lookup"><span data-stu-id="2aad4-222">To view details about the rule by using the content viewer</span></span>  
  
1.  <span data-ttu-id="2aad4-223">[**マイニングモデルビューアー** ] タブで、[**ビューアー** ] ボックスの一覧から [ **Microsoft 汎用コンテンツツリービューアー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-223">In the **Mining Model Viewer** tab, select **Microsoft Generic Content Tree Viewer** from the **Viewer** list.</span></span>  
  
2.  <span data-ttu-id="2aad4-224">[ノードのキャプション] ペインで、一覧を一番下までスクロールして最後のノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2aad4-224">In the Node Caption pane, scroll to the bottom of the list, and click the last node.</span></span>  
  
     <span data-ttu-id="2aad4-225">ビューアーでは、最初にアイテムセット、次にルールが表示されますが、グループ化はされていません。</span><span class="sxs-lookup"><span data-stu-id="2aad4-225">The viewer shows itemsets first and rules next, but does not group them.</span></span> <span data-ttu-id="2aad4-226">特定のノードを見つけるには、コンテンツ クエリを作成するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="2aad4-226">The easiest way to find a specific node is to create a content query.</span></span> <span data-ttu-id="2aad4-227">詳細については、「 [結合モデルのクエリ例](../../2014/analysis-services/data-mining/association-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aad4-227">For more information, see [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).</span></span>  
  
3.  <span data-ttu-id="2aad4-228">[ノードの詳細] ペインで、NODE_TYPE と NODE_DESCRIPTION の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-228">In the Node Details pane, review the value for NODE_TYPE and NODE_DESCRIPTION.</span></span>  
  
     <span data-ttu-id="2aad4-229">ルールのノードの種類は 8 で、アイテムセットのノードの種類は 7 です。</span><span class="sxs-lookup"><span data-stu-id="2aad4-229">A node type of 8 is a rule, and a node type of 7 is an itemset.</span></span> <span data-ttu-id="2aad4-230">ルールの NODE_DESCRIPTION の値は、ルールを構成する条件を表します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-230">For a rule, the value of NODE_DESCRIPTION tells you the conditions that make up the rule.</span></span> <span data-ttu-id="2aad4-231">アイテムセットの NODE_DESCRIPTION の値は、アイテムセットに含まれるアイテムを表します。</span><span class="sxs-lookup"><span data-stu-id="2aad4-231">For an itemset, the value of NODE_DESCRIPTION tells you the items included in the itemset.</span></span>  
  
 <span data-ttu-id="2aad4-232">コンテンツ クエリを作成してルールの詳細な統計情報を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="2aad4-232">You can also create a content query to obtain detailed statistics about the rules.</span></span> <span data-ttu-id="2aad4-233">マイニングモデルコンテンツとその解釈方法の詳細については、「[アソシエーションモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aad4-233">For more information about mining model content and how to interpret it, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="2aad4-234">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="2aad4-234">Back to Top</span></span>](#bkmk_DepNet)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2aad4-235">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="2aad4-235">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2aad4-236">マイニングモデルでの入れ子になったテーブルのフィルター処理 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="2aad4-236">Filtering a Nested Table in a Mining Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="2aad4-237">参照</span><span class="sxs-lookup"><span data-stu-id="2aad4-237">See Also</span></span>  
 <span data-ttu-id="2aad4-238">[レッスン 3: マーケットバスケットシナリオの構築 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="2aad4-238">[Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="2aad4-239">[レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2aad4-239">[Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md) </span></span>  
 <span data-ttu-id="2aad4-240">[Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="2aad4-240">[Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="2aad4-241">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="2aad4-241">Microsoft Association Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)  
  
  
