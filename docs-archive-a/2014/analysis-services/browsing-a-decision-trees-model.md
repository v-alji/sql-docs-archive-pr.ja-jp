---
title: デシジョンツリーモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- tree viewer
- mining model, decision tree
- decision tree [data mining]
- dependency network
ms.assetid: 6b3dd1ae-caff-41c3-817b-802dc020ff88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 809d2e494cfa7a6c4078acf95c2c70a0e68c188d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633574"
---
# <a name="browsing-a-decision-trees-model"></a><span data-ttu-id="bb798-102">デシジョン ツリー モデルの参照</span><span class="sxs-lookup"><span data-stu-id="bb798-102">Browsing a Decision Trees Model</span></span>
  <span data-ttu-id="bb798-103">[**参照**] を使用して分類モデルを開くと、のデシジョンツリービューアーと同様に、モデルが対話型のデシジョンツリービューアーに表示され [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="bb798-103">When you open a classification model using **Browse**, the model is displayed in an interactive decision tree viewer, similar to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="bb798-104">ビューアーは、あるデータ グループを別のデータ グループから区別する条件を強調するグラフとして分類結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="bb798-104">The viewer displays the results of classification as a graph that is designed to highlight the criteria that differentiate one group of data from another.</span></span> <span data-ttu-id="bb798-105">ツリーの個々のサブセットにドリルダウンして、基になるデータを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb798-105">You can also drill down into individual subsets of the tree and retrieve the underlying data.</span></span>  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a><span data-ttu-id="bb798-106">モデルの調査</span><span class="sxs-lookup"><span data-stu-id="bb798-106">Explore the Model</span></span>  
 <span data-ttu-id="bb798-107">デシジョン ツリー アルゴリズムに基づくモデルは、興味深い情報を多数持っています。</span><span class="sxs-lookup"><span data-stu-id="bb798-107">Models based on the Decision Trees algorithm have lots of interesting information to explore.</span></span> <span data-ttu-id="bb798-108">[**参照**] ウィンドウには、次のタブとペインがあり、グラフを使用してパターンを学習し、結果を予測するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bb798-108">The **Browse** window includes the following tabs and panes to help you learn the patterns and predict outcomes using the graph:</span></span>  
  
-   [<span data-ttu-id="bb798-109">デシジョン ツリー</span><span class="sxs-lookup"><span data-stu-id="bb798-109">Decision Tree</span></span>](#BKMK_DecisionTree)  
  
-   [<span data-ttu-id="bb798-110">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="bb798-110">Dependency Network</span></span>](#BKMK_DNetwork)  
  
 <span data-ttu-id="bb798-111">デシジョン ツリー モデルをテストするには、サンプル データ ブックの [トレーニング データ] (または [ソース データ]) タブにあるサンプル データを使用して、Bike Buyer を予測可能な属性としてデシジョン ツリー モデルを構築します。</span><span class="sxs-lookup"><span data-stu-id="bb798-111">To experiment with a decision trees model, you can use the sample data on the Training Data (or Source Data) tab of the sample data workbook, and build a decision tree model using Bike Buyer as the predictable attribute.</span></span>  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a><span data-ttu-id="bb798-112">デシジョンツリー</span><span class="sxs-lookup"><span data-stu-id="bb798-112">Decision Tree</span></span>  
 <span data-ttu-id="bb798-113">このビューの目的は、結果につながる要因の理解と調査に役立てることです。</span><span class="sxs-lookup"><span data-stu-id="bb798-113">This view is intended to help you understand and explore the factors that lead to an outcome.</span></span>  
  
 <span data-ttu-id="bb798-114">デシジョン ツリー グラフは、左から右に次のように読むことができます。</span><span class="sxs-lookup"><span data-stu-id="bb798-114">The decision tree graph can be read from left to right as follows:</span></span>  
  
-   <span data-ttu-id="bb798-115">*ノード*と呼ばれる四角形は、データのサブセットを含みます。</span><span class="sxs-lookup"><span data-stu-id="bb798-115">The rectangles, which are referred to as *nodes*, contain subsets of the data.</span></span> <span data-ttu-id="bb798-116">ノードのラベルはそのサブセットの定義特性を示します。</span><span class="sxs-lookup"><span data-stu-id="bb798-116">The label on the node tells you the defining characteristics of that subset.</span></span>  
  
-   <span data-ttu-id="bb798-117">左端のノード (**すべて**) は、完全なデータセットを表します。</span><span class="sxs-lookup"><span data-stu-id="bb798-117">The leftmost node, labeled **All**, represents the complete data set.</span></span> <span data-ttu-id="bb798-118">後続のすべてのノードは、データのサブセットを表します。</span><span class="sxs-lookup"><span data-stu-id="bb798-118">All subsequent nodes represent subsets of the data.</span></span>  
  
-   <span data-ttu-id="bb798-119">デシジョンツリーには、多くの分割が含まれています。また、属性に基づいてデータが複数のセットに*分割*される場所もあります。</span><span class="sxs-lookup"><span data-stu-id="bb798-119">A decision tree contains many *splits*, or places where the data diverges into multiple sets based on attributes.</span></span>  
  
     <span data-ttu-id="bb798-120">たとえば、サンプル モデルの最初の分割は、データセットを年齢別に 3 つのグループに分割します。</span><span class="sxs-lookup"><span data-stu-id="bb798-120">For example, the first split in the sample model divides the dataset into three groups by age.</span></span>  
  
-   <span data-ttu-id="bb798-121">[**すべて**のノードの直後に分割することは、このデータセットを分割するプライマリ条件を示すため、最も重要です。</span><span class="sxs-lookup"><span data-stu-id="bb798-121">The split immediately after the **All** node is most important because it shows the primary condition that divides this dataset.</span></span>  
  
     <span data-ttu-id="bb798-122">その他の分割は右側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-122">Additional splits occur to the right.</span></span> <span data-ttu-id="bb798-123">こうして、ツリーのさまざまなセグメントを分析することで、どの属性が購入行動に最も大きな影響を及ぼすかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="bb798-123">Thus, by analyzing different segments of the tree, you can learn which attributes had the most influence on purchasing behavior.</span></span>  
  
 <span data-ttu-id="bb798-124">![アソシエーション モデルの依存関係ネットワーク グラフ](media/dm13-dec-tree-split-definition.gif "アソシエーション モデルの依存関係ネットワーク グラフ")</span><span class="sxs-lookup"><span data-stu-id="bb798-124">![Dependency network graph for an association model](media/dm13-dec-tree-split-definition.gif "Dependency network graph for an association model")</span></span>  
  
 <span data-ttu-id="bb798-125">この情報を使用すると、購入を勧めるだけで実際に購入する可能性が高い顧客に対して重点的にマーケティング キャンペーンを実施することができます。</span><span class="sxs-lookup"><span data-stu-id="bb798-125">Using this information, you might focus a marketing campaign on customers that might simply need encouragement to make a purchase.</span></span>  
  
##### <a name="explore-the-decision-tree"></a><span data-ttu-id="bb798-126">デシジョン ツリーの調査</span><span class="sxs-lookup"><span data-stu-id="bb798-126">Explore the decision tree</span></span>  
  
1.  <span data-ttu-id="bb798-127">[**すべて**] ノードをクリックし、[**マイニング凡例**] を確認します。</span><span class="sxs-lookup"><span data-stu-id="bb798-127">Click the **All** node, and look at the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="bb798-128">トレーニング データ セット内のケースの正確な数と、結果の内訳が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-128">It displays the exact count of cases in the training data set, as well as a breakdown of the outcomes.</span></span>  
  
     <span data-ttu-id="bb798-129">ノードの上にマウス カーソルを置くと、ツールヒントにも同じ情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-129">You can view the same information in a tooltip if you pause the mouse over a node.</span></span>  
  
2.  <span data-ttu-id="bb798-130">各ノードの横にあるプラス記号とマイナス記号をクリックして、ツリーを展開し折りたたみます。</span><span class="sxs-lookup"><span data-stu-id="bb798-130">Click the plus and minus signs next to each node to expand or collapse the tree.</span></span>  
  
     <span data-ttu-id="bb798-131">[**レベルの表示]** スライダーを使用して、ツリーを展開または縮小することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb798-131">You can also use the **Show Level** slider to expand or shrink the tree.</span></span>  
  
3.  <span data-ttu-id="bb798-132">ノードには濃淡の差があります。</span><span class="sxs-lookup"><span data-stu-id="bb798-132">Notice that some nodes are darker than others?</span></span>  
  
     <span data-ttu-id="bb798-133">既定では、**母集団**はシェーディング変数として使用されます。つまり、色の輝度によって、どのノードで最もサポートされているかがわかります。</span><span class="sxs-lookup"><span data-stu-id="bb798-133">By default, **Population** is used as the shading variable, which means that the intensity of the color shows you which nodes have the most support.</span></span>  
  
     <span data-ttu-id="bb798-134">したがって、データセット全体を含む一番左端のノードの色が最も濃くなります。</span><span class="sxs-lookup"><span data-stu-id="bb798-134">Therefore the leftmost node is darkest, because it contains the entire dataset.</span></span>  
  
4.  <span data-ttu-id="bb798-135">[**背景**] の値を [**すべてのケース**] から **[はい]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="bb798-135">Change the value for **Background** from **All Cases** to **Yes**.</span></span>  
  
     <span data-ttu-id="bb798-136">![購入者を強調表示するようにデシジョン ツリー グラフを変更](media/dm13-dectreeshadedbuyer.gif "購入者を強調表示するようにデシジョン ツリー グラフを変更")</span><span class="sxs-lookup"><span data-stu-id="bb798-136">![changing decision tree graph to highlight buyers](media/dm13-dectreeshadedbuyer.gif "changing decision tree graph to highlight buyers")</span></span>  
  
5.  <span data-ttu-id="bb798-137">これで、色の濃さによって各ノードの顧客が自転車を購入した人数が示されるようになります。それが興味の対象となっている購入行動です。</span><span class="sxs-lookup"><span data-stu-id="bb798-137">Now the intensity of the color tells you how many customers in each node purchased a bike, which is the behavior you are interested in.</span></span>  
  
     <span data-ttu-id="bb798-138">各ノードには色分けされたバーがあります。</span><span class="sxs-lookup"><span data-stu-id="bb798-138">Notice the colored bars within each node.</span></span> <span data-ttu-id="bb798-139">これは、このデータのサブセット内で結果の分布を示すヒストグラムです。</span><span class="sxs-lookup"><span data-stu-id="bb798-139">This is a histogram that shows the distribution of outcomes within this subset of data.</span></span> <span data-ttu-id="bb798-140">たとえば、サンプルの自転車購入者デシジョンツリーでは、色分けされたバーに自転車 (Yes 値) を購入した顧客の割合と、(値のない) ユーザーの比率が示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-140">For example, in the sample Bike Buyer decision tree, the colored bar shows the proportion of customers who bought bikes (Yes values) vs. those who did not (No values).</span></span> <span data-ttu-id="bb798-141">正確な値を取得するには、ノードをクリックして [**マイニング凡例**] を表示します。</span><span class="sxs-lookup"><span data-stu-id="bb798-141">To get the exact values, you can click the node and view the **Mining Legend**.</span></span>  
  
6.  <span data-ttu-id="bb798-142">グラフを調べると、データの各サブセットがより小さなグループにさらに分解されていて、どの属性が結果の予測に最も役立つかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="bb798-142">By following the graph, you can see how each subset of data is further decomposed into smaller groups, and which attributes are most useful in predicting an outcome.</span></span>  
  
     <span data-ttu-id="bb798-143">網掛けの濃さを見るだけで、いくつかのグループに注目して、その詳細データを比較することができます。</span><span class="sxs-lookup"><span data-stu-id="bb798-143">Just by looking at the intensity of the shading, you can focus on a couple groups of interest, and get more detailed data on them for comparison.</span></span> <span data-ttu-id="bb798-144">たとえば、次のようなグループは自転車を購入する確率がかなり高くなっています。</span><span class="sxs-lookup"><span data-stu-id="bb798-144">For example, these groups have a fairly high probability of buying bikes:</span></span>  
  
    -   <span data-ttu-id="bb798-145">Age >= 32、 \< 53 and Yearly Income > = 26000、および Children = 0</span><span class="sxs-lookup"><span data-stu-id="bb798-145">Age >= 32 and \< 53 and Yearly Income >= 26000 and Children = 0</span></span>  
  
         <span data-ttu-id="bb798-146">ケースの合計: 1150</span><span class="sxs-lookup"><span data-stu-id="bb798-146">Total cases: 1150</span></span>  
  
         <span data-ttu-id="bb798-147">自転車購入者の確率: 18%</span><span class="sxs-lookup"><span data-stu-id="bb798-147">Bike buyer probability: 18%</span></span>  
  
    -   <span data-ttu-id="bb798-148">Age >= 32、 \< 53 and Yearly Income > = 26000、子 not = 0 および配偶の状態 = ' Single '</span><span class="sxs-lookup"><span data-stu-id="bb798-148">Age >= 32 and \< 53 and Yearly Income >= 26000 and Children not = 0 and Marital Status = 'Single'</span></span>  
  
         <span data-ttu-id="bb798-149">ケースの合計: 402</span><span class="sxs-lookup"><span data-stu-id="bb798-149">Total cases: 402</span></span>  
  
         <span data-ttu-id="bb798-150">自転車購入確率: 16%</span><span class="sxs-lookup"><span data-stu-id="bb798-150">Bike buyer probability: 16%</span></span>  
  
7.  <span data-ttu-id="bb798-151">[**背景**] の値を **[はい] から [** **いいえ**] に変更し、グラフがどのように変化するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb798-151">Change the value for **Background** from **Yes** to **No** and see how the graph changes.</span></span>  
  
     <span data-ttu-id="bb798-152">![アソシエーション モデルの依存関係ネットワーク グラフ](media/dm13-dec-tree-background-no.gif "アソシエーション モデルの依存関係ネットワーク グラフ")</span><span class="sxs-lookup"><span data-stu-id="bb798-152">![Dependency network graph for an association model](media/dm13-dec-tree-background-no.gif "Dependency network graph for an association model")</span></span>  
  
 <span data-ttu-id="bb798-153">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="bb798-153">**Tips**</span></span>  
  
-   <span data-ttu-id="bb798-154">データを複数のシリーズに分割できる場合、モデル化するデータ セットごとに異なるモデルが構築されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-154">If your data can be divided into multiple series, a different model is built for each set of data that you want to model.</span></span>  
  
-   <span data-ttu-id="bb798-155">サンプルデータモデルには、予測可能な結果が1つだけ含まれています。ただし、顧客がサービスプランを購入したかどうかや、それを予測する必要があるかどうかに関する情報があるとします。</span><span class="sxs-lookup"><span data-stu-id="bb798-155">In the sample data model, there is only one predictable outcome - Bike Buyer - but suppose you had information about whether the customer purchased a service plan and wanted to predict that as well.</span></span> <span data-ttu-id="bb798-156">その場合、そのデータを別の列に保持して、モデルに 2 つの予測可能な属性を含めます。</span><span class="sxs-lookup"><span data-stu-id="bb798-156">In that case you would have that data in a separate column, and include two predictable attributes in the model.</span></span>  
  
     <span data-ttu-id="bb798-157">[デシジョンツリー] ペインの左上隅にある [**ヒストグラム**] オプションをクリックして、ツリーのヒストグラムに表示できる状態の最大数を変更します。</span><span class="sxs-lookup"><span data-stu-id="bb798-157">Click the **Histogram** option, in the upper left corner of the Decision Tree pane, to change the maximum number of states that can appear in the histograms in the tree.</span></span> <span data-ttu-id="bb798-158">これは、予測可能な属性に多数の状態が含まれている場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="bb798-158">This is useful if the predictable attribute has many states.</span></span> <span data-ttu-id="bb798-159">ヒストグラムには、状態がポピュラリティ順に左から右に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-159">The states appear in a histogram in order of popularity from left to right.</span></span>  
  
-   <span data-ttu-id="bb798-160">[**デシジョンツリー** ] タブのオプションを使用して、ツリーの表示方法に影響を与えることもできます。これには、ウィンドウを拡大または縮小したり、グラフのサイズを変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="bb798-160">You can also use the options on the **Decision Tree** tab to affect how the tree is displayed, by zooming in or out, or sizing the graph to fit the window.</span></span>  
  
-   <span data-ttu-id="bb798-161">モデル内のすべてのツリーに表示される既定のレベル数を設定するには、 **[既定の展開]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="bb798-161">Use **Default Expansion** to set the default number of levels that are displayed for all trees in the model.</span></span>  
  
-   <span data-ttu-id="bb798-162">[**長い名前を表示**する] を選択すると、データソースを含む属性の完全な名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-162">Select **Show long name** to display the full name of the attribute, including the data source.</span></span> <span data-ttu-id="bb798-163">各ケースの属性と異なるデータ ソースからケースが取得されている場合を除いて、短い名前と長い名前は同じになります。</span><span class="sxs-lookup"><span data-stu-id="bb798-163">Short names and long names are the same unless your cases are obtained from a different data source than the attributes for each case.</span></span>  
  
 [<span data-ttu-id="bb798-164">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="bb798-164">Back To Top</span></span>](#bkmk_Top)  
  
###  <a name="dependency-network"></a><a name="BKMK_DNetwork"></a><span data-ttu-id="bb798-165">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="bb798-165">Dependency Network</span></span>  
 <span data-ttu-id="bb798-166">[**依存関係ネットワーク**] ビューには、モデル内の入力属性と予測可能属性の間の接続が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-166">The **Dependency Network** view displays the connections between the input attributes and the predictable attributes in the model.</span></span>  
  
1.  <span data-ttu-id="bb798-167">ビューアーの左側にあるスライダーをクリックしてドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bb798-167">Click and drag the slider at the left of the viewer</span></span>  
  
     <span data-ttu-id="bb798-168">一番上の位置では、すべての接続が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-168">At the top position, all connections are shown.</span></span> <span data-ttu-id="bb798-169">スライダーをドラッグして下げると、最も強いリンクだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-169">When you drag the slider down, only the strongest links are shown in the viewer.</span></span>  
  
2.  <span data-ttu-id="bb798-170">ここで [Bike Buyer] (自転車購入者) ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb798-170">Now click the Bike Buyer node.</span></span>  
  
     <span data-ttu-id="bb798-171">![デシジョン ツリーの依存関係ネットワーク ビュー](media/dm13-dectree-depnet.gif "デシジョン ツリーの依存関係ネットワーク ビュー")</span><span class="sxs-lookup"><span data-stu-id="bb798-171">![Dependency network view for decision trees](media/dm13-dectree-depnet.gif "Dependency network view for decision trees")</span></span>  
  
     <span data-ttu-id="bb798-172">ノードを選択すると、そのノードに固有の依存関係が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-172">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="bb798-173">この場合、ビューアーでは、結果の予測に役立つ各ノードが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-173">In this case, the viewer highlights each node that helps predict the outcome.</span></span>  
  
3.  <span data-ttu-id="bb798-174">ビューアーに多数のノードが含まれている場合は、[ノードの**検索**] ボタンを使用して特定のノードを検索できます。</span><span class="sxs-lookup"><span data-stu-id="bb798-174">If the viewer contains many nodes, you can search for specific nodes by using the **Find Node** button.</span></span> <span data-ttu-id="bb798-175">**[ノードの検索]** をクリックすると、 **[ノードの検索]** ダイアログ ボックスが開き、フィルターを使用して特定のノードを検索して選択できます。</span><span class="sxs-lookup"><span data-stu-id="bb798-175">Clicking **Find Node** opens the **Find Node** dialog box, in which you can use a filter to search for and select specific nodes.</span></span>  
  
4.  <span data-ttu-id="bb798-176">ビューアーの下部にある凡例は、グラフ内の依存関係の種類に色を関連付けています。</span><span class="sxs-lookup"><span data-stu-id="bb798-176">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="bb798-177">たとえば、予測可能なノードを選択すると、予測可能なノードが水色で網掛けされ、選択したノードを予測するノードがオレンジ色で網掛けされます。</span><span class="sxs-lookup"><span data-stu-id="bb798-177">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="bb798-178">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="bb798-178">Back To Top</span></span>](#bkmk_Top)  
  
### <a name="drill-through-to-underlying-data"></a><span data-ttu-id="bb798-179">基になるデータへのドリルスルー</span><span class="sxs-lookup"><span data-stu-id="bb798-179">Drill through to Underlying Data</span></span>  
 <span data-ttu-id="bb798-180">いくつかの種類のモデルでは、モデルから基になるケースデータにドリルスルーする機能がサポートされ*て*います。</span><span class="sxs-lookup"><span data-stu-id="bb798-180">Several types of models support the ability to *drill through* from the model to the underlying case data.</span></span> <span data-ttu-id="bb798-181">これは、特定のセグメントの顧客にコンタクトする場合や、データを取り出してさらに分析を実行する場合に、非常に便利な機能です。</span><span class="sxs-lookup"><span data-stu-id="bb798-181">This can be very useful if you want to contact customers in a particular segment or pull out the data to perform further analysis.</span></span>  
  
##### <a name="get-case-data"></a><span data-ttu-id="bb798-182">ケース データの取得</span><span class="sxs-lookup"><span data-stu-id="bb798-182">Get case data</span></span>  
  
1.  <span data-ttu-id="bb798-183">目的のデータを含むノードを右クリックし、以下のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="bb798-183">Right-click the node in the tree that contains the desired data and select one of these options:</span></span>  
  
    -   <span data-ttu-id="bb798-184">**モデルのドリル**スルー。</span><span class="sxs-lookup"><span data-stu-id="bb798-184">**Drill Through Model**.</span></span> <span data-ttu-id="bb798-185">このオプションは、選択したノードに属するケースを取得して、Excel のテーブルに保存します。</span><span class="sxs-lookup"><span data-stu-id="bb798-185">This option gets the cases that belong to the selected node, and saves them to a table in Excel.</span></span> <span data-ttu-id="bb798-186">モデルの構築に実際に使用されたデータ列のみが取り出されます。</span><span class="sxs-lookup"><span data-stu-id="bb798-186">You get back only the columns of data that were actually used in building the model.</span></span>  
  
    -   <span data-ttu-id="bb798-187">**構造列をドリル**スルーします。</span><span class="sxs-lookup"><span data-stu-id="bb798-187">**Drill Through Structure Columns**.</span></span> <span data-ttu-id="bb798-188">このオプションは、選択したノードに属するケースを取得して、Excel のテーブルに保存します。</span><span class="sxs-lookup"><span data-stu-id="bb798-188">This option gets the cases that belong to the selected node, and saves them to a table in Excel.</span></span> <span data-ttu-id="bb798-189">モデルで使用されていない列でも、基になるデータで使用できるすべての情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="bb798-189">You get all information that was available in the underlying data when you built it, even of a column wasn't used in the model.</span></span> <span data-ttu-id="bb798-190">たとえば、分析には役立たないため顧客の住所と郵便番号をモデルから除外して、構造には残していた場合です。</span><span class="sxs-lookup"><span data-stu-id="bb798-190">For example, you might have excluded the customer address and zip code because those fields are not useful with analysis, but left them in the structure.</span></span>  
  
     <span data-ttu-id="bb798-191">Excel に戻ってデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="bb798-191">Return to Excel to view your data.</span></span> <span data-ttu-id="bb798-192">参照ビューアーを使って、クエリを実行し、新しいワークシートのテーブルにデータを保存し、結果にラベルを付けます。</span><span class="sxs-lookup"><span data-stu-id="bb798-192">The Browse viewer runs a query, saves the data to a table in a new worksheet, and labels the results.</span></span>  
  
     <span data-ttu-id="bb798-193">![ドリルスルーの結果を Excel に保存](media/dm13-dectree-drillthroughresults.gif "ドリルスルーの結果を Excel に保存")</span><span class="sxs-lookup"><span data-stu-id="bb798-193">![results of drillthrough are saved to Excel](media/dm13-dectree-drillthroughresults.gif "results of drillthrough are saved to Excel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb798-194">参照</span><span class="sxs-lookup"><span data-stu-id="bb798-194">See Also</span></span>  
 [<span data-ttu-id="bb798-195">Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;</span><span class="sxs-lookup"><span data-stu-id="bb798-195">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
