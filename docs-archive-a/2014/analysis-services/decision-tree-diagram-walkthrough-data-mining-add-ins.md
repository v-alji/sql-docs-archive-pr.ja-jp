---
title: デシジョンツリーダイアグラムのチュートリアル (データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- shapes, data mining
- diagram, decision tree
- Visio shapes, decision tree
- decision tree [data mining]
ms.assetid: 9566f6a2-c750-4125-ba5e-42c7251a78c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: bbe54db1ab3d00d074917db770a9a731f884f49a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639780"
---
# <a name="decision-tree-diagram-walkthrough--data-mining-add-ins"></a><span data-ttu-id="41a6d-102">デシジョンツリーダイアグラムのチュートリアル (データマイニングアドイン)</span><span class="sxs-lookup"><span data-stu-id="41a6d-102">Decision Tree Diagram Walkthrough  (Data Mining Add-ins)</span></span>
  <span data-ttu-id="41a6d-103">デシジョン ツリー モデルを作成した場合、デシジョン ツリー図形または依存関係ネットワーク図形を使用して、カスタマイズしたダイアグラムを Visio で作成できます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-103">If you have created a decision tree model, you can create a customized diagram in Visio by using either the Decision Tree shape or the Dependency Network shape.</span></span> <span data-ttu-id="41a6d-104">このトピックでは、**デシジョンツリー**図形とこれらのコントロールを使用して実行できるカスタマイズについて説明します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-104">This topic describes the customizations you can perform using the **Decision Tree** shape and these controls:</span></span>  
  
-   <span data-ttu-id="41a6d-105">デシジョン ツリー ダイアグラムの描画コントロール</span><span class="sxs-lookup"><span data-stu-id="41a6d-105">Rendering controls for the decision tree diagram</span></span>  
  
     <span data-ttu-id="41a6d-106">これらのオプションは、Visio ワークスペースに図形をドロップしたときに起動される**デシジョンツリーウィザード**の一部です。</span><span class="sxs-lookup"><span data-stu-id="41a6d-106">These options are part of the **Decision Tree Wizard** that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="41a6d-107">**データマイニングレイアウト**ツールバー</span><span class="sxs-lookup"><span data-stu-id="41a6d-107">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="41a6d-108">これは、図形の操作に役立つように Visio ワークスペースに追加されます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-108">These options are added to the Visio workspace to help you interact with the shape.</span></span>  
  
## <a name="build-a-decision-tree-diagram"></a><span data-ttu-id="41a6d-109">デシジョン ツリー ダイアグラムの作成</span><span class="sxs-lookup"><span data-stu-id="41a6d-109">Build a Decision Tree Diagram</span></span>  
 <span data-ttu-id="41a6d-110">デシジョンツリー図形を Visio ページにドロップして、 **Visio デシジョンツリー図形ウィザード**を起動し、ダイアグラムのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-110">You drop the Decision Tree shape onto the Visio page to launch the **Decision Tree Visio Shape Wizard** and set diagram options.</span></span>  
  
#### <a name="use-the-decision-tree-wizard"></a><span data-ttu-id="41a6d-111">デシジョン ツリー ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="41a6d-111">Use the Decision Tree Wizard</span></span>  
  
1.  <span data-ttu-id="41a6d-112">[**図形**] ボックスの一覧に [ **Microsoft データマイニング図形**] が表示されない場合は、[**その他の図形**] をクリックし、[**ステンシルを開く**] を選択して、既定のインストール場所からテンプレートを開きます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-112">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="41a6d-113">\<drive>: \Microsoft files (x85) SQL Server 2012 DM アドイン</span><span class="sxs-lookup"><span data-stu-id="41a6d-113">\<drive>:\Program files (x85)\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="41a6d-114">[**デシジョンツリー** ] 図形をページにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="41a6d-114">Drag the **Decision Tree** shape onto the page.</span></span>  
  
3.  <span data-ttu-id="41a6d-115">**Visio デシジョンツリー図形ウィザード**の [ようこそ] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41a6d-115">On the welcome page of the **Decision Tree Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="41a6d-116">**クラスターウィザード**の [**データソースの選択**] ページで、視覚化する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] モデルがあるサーバーへの接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-116">On the **Select a Data Source** page of the **Cluster Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that has the model you want to visualize.</span></span>  
  
5.  <span data-ttu-id="41a6d-117">適切なマイニングモデルを選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41a6d-117">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="41a6d-118">この図の種類は、デシジョンツリーまたは線形回帰アルゴリズムを使用して作成されたモデルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="41a6d-118">This diagram type supports models created using the Decision Trees or Linear Regression algorithm.</span></span>  
  
6.  <span data-ttu-id="41a6d-119">**[デシジョンツリーの選択**] ページで、表示する個々のツリーを選択します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-119">On the **Select Decision Tree** page, choose an individual tree to display.</span></span>  
  
     <span data-ttu-id="41a6d-120">ツリーは、モデル化された特定の結果につながる相互作用をモデル化します。したがって、モデルに複数の結果が含まれている場合でも、一度に表示できるツリーは1つだけです。</span><span class="sxs-lookup"><span data-stu-id="41a6d-120">A tree models the interactions that lead to a particular outcome you've modeled; therefore, even if your model contains multiple outcomes, you can display only one tree at a time.</span></span>  
  
7.  <span data-ttu-id="41a6d-121">**[デシジョンツリーの選択**] ダイアログボックスでは、次の表示オプションを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-121">In the **Select Decision Tree** dialog box, you can also set these rendering options:</span></span>  
  
     <span data-ttu-id="41a6d-122">**[表示する最大の深さ]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-122">**Maximum Rendering Depth**</span></span>  
     <span data-ttu-id="41a6d-123">表示するノードの数を制御するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-123">Use this option to control how many nodes are displayed.</span></span>  
  
     <span data-ttu-id="41a6d-124">デシジョン ツリーは分岐が非常に深くなり、作成したダイアグラムがページに収まらなくなることもあります。</span><span class="sxs-lookup"><span data-stu-id="41a6d-124">A decision tree might go very deep, creating a diagram that does not fit on the page.</span></span> <span data-ttu-id="41a6d-125">重要性の高い左側のノードに注目するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-125">Use this control to focus on the leftmost nodes, which are more important.</span></span>  
  
     <span data-ttu-id="41a6d-126">既定値は 3 レベルのノードです。</span><span class="sxs-lookup"><span data-stu-id="41a6d-126">The default is three levels of nodes.</span></span>  
  
     <span data-ttu-id="41a6d-127">**[値の色と表示テキストを選択します]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-127">**Select color and display text for values**</span></span>  
     <span data-ttu-id="41a6d-128">結果のそれぞれを表す色を選択します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-128">Choose the color that will represent each one of the outcomes.</span></span> <span data-ttu-id="41a6d-129">色を指定しない場合、色は現在のビデオ テーマの色を使用して自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-129">If you do not specify colors, they are automatically generated using the current video theme colors.</span></span>  
  
8.  <span data-ttu-id="41a6d-130">[**詳細設定**] をクリックして、デシジョンツリーダイアグラムの各ノードについて、次のオプションをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="41a6d-130">Click **Advanced** to customize the following options for each of the nodes in the decision tree diagram.</span></span>  
  
     <span data-ttu-id="41a6d-131">**シェーディング変数**と**状態**</span><span class="sxs-lookup"><span data-stu-id="41a6d-131">**Shading Variable** and **State**</span></span>  
     <span data-ttu-id="41a6d-132">ツリー ダイアグラムに表示する目標の結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-132">Choose the target outcome that you want to show in the tree diagram.</span></span>  
  
     <span data-ttu-id="41a6d-133">**[ヒストグラムを表示する]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-133">**Show Histogram**</span></span>  
     <span data-ttu-id="41a6d-134">各ノードにグラフを追加して、そのノードを定義するルールを示します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-134">Adds a chart to each node that shows the rules that define that node.</span></span>  
  
     <span data-ttu-id="41a6d-135">**[ラベルを表示する]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-135">**Show Label**</span></span>  
     <span data-ttu-id="41a6d-136">ヒストグラムに列名を追加します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-136">Adds column names to the histogram.</span></span>  
  
     <span data-ttu-id="41a6d-137">**[確率を表示する]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-137">**Show Probability**</span></span>  
     <span data-ttu-id="41a6d-138">各値の確率を表示します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-138">Displays the probability of each value.</span></span>  
  
     <span data-ttu-id="41a6d-139">**[サポートを表示する]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-139">**Show Support**</span></span>  
     <span data-ttu-id="41a6d-140">各値のサポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-140">Displays the support for each value.</span></span>  
  
     <span data-ttu-id="41a6d-141">**[フッターを表示する]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-141">**Show Footer**</span></span>  
     <span data-ttu-id="41a6d-142">表示されているすべての値を合計するフッターを追加します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-142">Adds a footer that sums all displayed values.</span></span>  
  
     <span data-ttu-id="41a6d-143">**[ヘッダーを表示する]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-143">**Show Header**</span></span>  
     <span data-ttu-id="41a6d-144">列見出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-144">Adds column headings.</span></span>  
  
     <span data-ttu-id="41a6d-145">**[サポートされない状態を表示する]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-145">**Show states with zero support**</span></span>  
     <span data-ttu-id="41a6d-146">不足値を表示します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-146">Lets you display missing values.</span></span>  
  
9. <span data-ttu-id="41a6d-147">[**完了**] をクリックしてグラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-147">Click **Finish** to create the graph.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="41a6d-148">一部の環境では、グラフのコネクタが Office 2013 で表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="41a6d-148">In some environments, connectors in the chart might fail to render in Office 2013.</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="41a6d-149">完成したダイアグラムの調査と変更</span><span class="sxs-lookup"><span data-stu-id="41a6d-149">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="41a6d-150">**Visio デシジョンツリー図形ウィザード**を完了すると、ページにツリーダイアグラムが作成され、予測結果につながるルールがグラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-150">After you have completed the **Decision Tree Visio Shape Wizard**, Visio creates a tree diagram on the page that graphically displays the rules that lead to the predicted outcome.</span></span>  
  
 <span data-ttu-id="41a6d-151">以下に挙げるデシジョン ツリー ダイアグラムのコントロールを使用して、引き続き図形を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-151">You can continue to modify the shape by using the following controls for decision tree diagrams:</span></span>  
  
#### <a name="using-the-decision-tree-option-menus"></a><span data-ttu-id="41a6d-152">デシジョン ツリーのオプション メニューの使用</span><span class="sxs-lookup"><span data-stu-id="41a6d-152">Using the decision tree option menus</span></span>  
  
1.  <span data-ttu-id="41a6d-153">[**アドイン**] リボンをクリックし、データマイニングダイアグラムを操作するために使用するカスタムツールバーの1つを表示します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-153">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="41a6d-154">**レイアウト**</span><span class="sxs-lookup"><span data-stu-id="41a6d-154">**Layout**</span></span>  
     <span data-ttu-id="41a6d-155">ツリーを並べ替えて現在のページに収まるように最適化します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-155">Optimizes the arrangement of the tree to fit the current page.</span></span>  
  
     <span data-ttu-id="41a6d-156">**[ページのサイズ変更]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-156">**Resize Page**</span></span>  
     <span data-ttu-id="41a6d-157">このコントロールは、HTML の以前のバージョンを対象としたものです。</span><span class="sxs-lookup"><span data-stu-id="41a6d-157">This control was intended for earlier HTML versions.</span></span> <span data-ttu-id="41a6d-158">代わりに、Visio ページのサイズ変更コントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-158">Use the Visio page resizing controls instead,</span></span>  
  
     <span data-ttu-id="41a6d-159">**説明**</span><span class="sxs-lookup"><span data-stu-id="41a6d-159">**Description**</span></span>  
     <span data-ttu-id="41a6d-160">ツリーのノードが選択されている状態でこのオプションをクリックすると、ノードのケースに関する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-160">When a node of the tree is selected, click this option to display details about the cases in the node.</span></span>  
  
2.  <span data-ttu-id="41a6d-161">Visio の [**デザイン**] リボンの [**再レイアウトページ**] オプションを使用すると、さまざまなツリーレイアウトを試すことができます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-161">Use the **Re-Layout Page** option in the Visio **Design** ribbon to experiment with different tree layouts.</span></span>  
  
3.  <span data-ttu-id="41a6d-162">ツリー内のノード間で使用されるコネクタを変更するには、[**デザイン**] タブの [**コネクタ**] オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-162">Use the **Connectors** option on the **Design** tab to change the connectors used between nodes in the tree.</span></span>  
  
4.  <span data-ttu-id="41a6d-163">Visio**ビュー**リボンの [**タスクペイン**] 領域にある [**パンとズーム**] コントロールを使用すると、ダイアグラムの特定の領域に焦点を当てることができます。</span><span class="sxs-lookup"><span data-stu-id="41a6d-163">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a particular area of the diagram.</span></span>  
  
5.  <span data-ttu-id="41a6d-164">ツリーのノードを右クリックし、デシジョン ツリー ダイアグラムに特有のショートカット メニュー オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-164">Right-click any node in the tree, and choose from these shortcut menu options specific to decision tree diagrams:</span></span>  
  
     <span data-ttu-id="41a6d-165">**[ページ レイアウトの改善]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-165">**Improve Page Layout**</span></span>  
     <span data-ttu-id="41a6d-166">ページ上にノードを均等に分散し、すべてのノードが表示されるようにページ表示を調整します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-166">Distributes the nodes evenly on the page and adjusts the page view to see all nodes.</span></span>  
  
     <span data-ttu-id="41a6d-167">**[子を新しいページに移動]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-167">**Move Children to New Page**</span></span>  
     <span data-ttu-id="41a6d-168">現在選択しているノードの子を新しいページに移動します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-168">Moves the children of the currently selected node to a new page.</span></span>  
  
     <span data-ttu-id="41a6d-169">**[子ノードの折りたたみ]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-169">**Collapse Child Nodes**</span></span>  
     <span data-ttu-id="41a6d-170">現在選択しているノードの子を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="41a6d-170">Hides the children of the currently selected node.</span></span>  
  
     <span data-ttu-id="41a6d-171">**[子ノードの展開]**</span><span class="sxs-lookup"><span data-stu-id="41a6d-171">**Expand Child Nodes**</span></span>  
     <span data-ttu-id="41a6d-172">現在選択しているノードの子を表示します。</span><span class="sxs-lookup"><span data-stu-id="41a6d-172">Displays the children of the currently selected node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a6d-173">参照</span><span class="sxs-lookup"><span data-stu-id="41a6d-173">See Also</span></span>  
 [<span data-ttu-id="41a6d-174">データマイニングアドインの &#40;SQL Server Visio データマイニングダイアグラムのトラブルシューティング&#41;</span><span class="sxs-lookup"><span data-stu-id="41a6d-174">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
