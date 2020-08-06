---
title: 依存関係ネットワークダイアグラムのチュートリアル (データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, dependency network
- shapes, data mining
- shapes, network
- dependencies
- diagram, dependency network
- data mining layout toolbar
- dependency network
ms.assetid: aac732a8-5262-4649-b7d7-3ccf6f9cfa8b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07f97dac7ffb0211f0ff1e1b58c2e0792d026174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644691"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a><span data-ttu-id="ff41a-102">依存関係ネットワーク ダイアグラムのチュートリアル (データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="ff41a-102">Dependency Network Diagram Walkthrough (Data Mining Add-ins)</span></span>
  <span data-ttu-id="ff41a-103">データ マイニング モデルのいくつかの種類では、データのリレーションシップを調査する方法としてネットワーク グラフを使用します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-103">Several different types of data mining models use a network graph as a way of exploring relationships in the data.</span></span> <span data-ttu-id="ff41a-104">これらのモデルを Visio に**依存関係ネットワーク**図形を使用してインポートした後、レイアウトのカスタマイズと拡張を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-104">You can import these models into Visio using the **Dependency Network** shape and then continue to customize and enhance the layout.</span></span> <span data-ttu-id="ff41a-105">**Visio のデータマイニング図形**には、依存関係ネットワーク図を操作するための次のカスタムコントロールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ff41a-105">The **Data Mining Shapes for Visio** include the following custom controls for working with dependency network diagrams:</span></span>  
  
-   <span data-ttu-id="ff41a-106">ネットワーク グラフの描画コントロール</span><span class="sxs-lookup"><span data-stu-id="ff41a-106">Rendering controls for the network graph</span></span>  
  
     <span data-ttu-id="ff41a-107">これは、Visio ワークスペースに図形をドロップすると起動されるウィザードの一部です。</span><span class="sxs-lookup"><span data-stu-id="ff41a-107">These options are part of the wizard that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="ff41a-108">**データマイニングレイアウト**ツールバー</span><span class="sxs-lookup"><span data-stu-id="ff41a-108">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="ff41a-109">これは、依存関係ネットワーク グラフの操作に役立つように Visio ワークスペースに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-109">These options are added to the Visio workspace to help you interact with the dependency network graph.</span></span>  
  
## <a name="build-a-dependency-network-graph"></a><span data-ttu-id="ff41a-110">依存関係ネットワーク グラフの作成</span><span class="sxs-lookup"><span data-stu-id="ff41a-110">Build a Dependency Network Graph</span></span>  
 <span data-ttu-id="ff41a-111">Visio のページに図形をドロップして、 **Visio 依存関係ネットワーク図形ウィザード**を起動し、ダイアグラムのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-111">You drop a shape onto the Visio page to launch the **Dependency Net Visio Shape Wizard** and set diagram options.</span></span>  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a><span data-ttu-id="ff41a-112">Visio 依存関係ネットワーク図形ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="ff41a-112">Use the Dependency Net Visio Shape Wizard</span></span>  
  
1.  <span data-ttu-id="ff41a-113">[**図形**] ボックスの一覧に [ **Microsoft データマイニング図形**] が表示されない場合は、[**その他の図形**] をクリックし、[**ステンシルを開く**] を選択して、既定のインストール場所からテンプレートを開きます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-113">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="ff41a-114">\<drive>: \Microsoft files (x85) SQL Server 2012 DM アドイン</span><span class="sxs-lookup"><span data-stu-id="ff41a-114">\<drive>:\Program files (x85)\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="ff41a-115">ページに [**依存関係ネットワーク**] 図形をドラッグして、ウィザードを開始します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-115">Drag the **Dependency Network** shape onto the page to start the wizard.</span></span> <span data-ttu-id="ff41a-116">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff41a-116">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="ff41a-117">**Visio 依存関係ネットワーク図形ウィザード**の [ようこそ] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff41a-117">On the welcome page of the **Dependency Network Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="ff41a-118">**Visio 依存関係ネットワーク図形ウィザード**の [**データソースの選択**] ページで、視覚化する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] モデルがあるサーバーへの接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-118">On the **Select a Data Source** page of the **Dependency Network Visio Shape Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that has the model you want to visualize.</span></span>  
  
5.  <span data-ttu-id="ff41a-119">適切なマイニングモデルを選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff41a-119">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="ff41a-120">適切なモデルを選択するには、[**プロパティ**] ペインでデータの名前、説明、列、および種類を確認します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-120">To select an appropriate model, you can review the name, description, columns, and type of data in the **Properties** pane.</span></span>  
  
     <span data-ttu-id="ff41a-121">この図形は以下の方法で作成されたモデルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ff41a-121">This shape supports models created by using these algorithms:</span></span>  
  
    -   <span data-ttu-id="ff41a-122">Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="ff41a-122">Naïve Bayes</span></span>  
  
    -   <span data-ttu-id="ff41a-123">デシジョン ツリー</span><span class="sxs-lookup"><span data-stu-id="ff41a-123">Decision Trees</span></span>  
  
    -   <span data-ttu-id="ff41a-124">アソシエーションルール</span><span class="sxs-lookup"><span data-stu-id="ff41a-124">Association Rules</span></span>  
  
6.  <span data-ttu-id="ff41a-125">ページで、**表示するノードを選択**し、グラフのサイズをカスタマイズします。必要に応じて、特定のノードのみが含まれるようにフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-125">On the page, **Select Nodes to Render**, customize the size of the graph, and optionally filter to only include certain nodes.</span></span>  
  
     <span data-ttu-id="ff41a-126">大規模なデータセットの場合、依存関係グラフは大きくなる可能性があり、*ノード*として表される多くの関連オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ff41a-126">With a large dataset, a dependency graph can become huge, and contain many related objects, represented as *nodes*.</span></span> <span data-ttu-id="ff41a-127">このダイアログ ボックスを使うと、興味のあるノードだけを含むカスタム ネットワーク グラフを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-127">By using this dialog box, you can create a custom network graph that includes only the nodes of interest.</span></span>  
  
     <span data-ttu-id="ff41a-128">[アートプレースホルダー]</span><span class="sxs-lookup"><span data-stu-id="ff41a-128">[art placeholder]</span></span>  
  
     <span data-ttu-id="ff41a-129">**[フェッチするノード数]**</span><span class="sxs-lookup"><span data-stu-id="ff41a-129">**Number of nodes to fetch**</span></span>  
     <span data-ttu-id="ff41a-130">モデルに含まれているノードの数が指定したノードの数より少ない場合、この設定は機能しません。</span><span class="sxs-lookup"><span data-stu-id="ff41a-130">If the model contains fewer than the specified number of nodes, this setting has no effect.</span></span> <span data-ttu-id="ff41a-131">モデルに含まれているノードの数が指定したノードの数より多い場合は、関連性の強いノードだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-131">If the model contains more nodes than the specified number, only the strongest nodes are displayed.</span></span>  
  
     <span data-ttu-id="ff41a-132">**[名前に含まれる文字列]**</span><span class="sxs-lookup"><span data-stu-id="ff41a-132">**Name contains**</span></span>  
     <span data-ttu-id="ff41a-133">このボックスを空白のままにして緑色の矢印をクリックすると、モデル内のすべてのノードが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-133">Leave this box blank and click the green arrow to retrieve all nodes in the model.</span></span>  
  
     <span data-ttu-id="ff41a-134">文字列を入力して、緑色の矢印をクリックすると、指定した文字列を含むノードだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-134">Or, type a string and click the green arrow to return only those nodes that contain the specified string.</span></span>  
  
     <span data-ttu-id="ff41a-135">サンプル データから作成できるモデルの大半は大きくありません。そのため、この例の場合、ノード数を 10 に増やして緑色の矢印をクリックすると、クエリが実行されて、すべてのノードの一覧が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-135">Most of the models that you can create with the sample data are not big, so for this example, increase the number of nodes to 10, and then click the green arrow to run a query and get the list of all nodes.</span></span>  
  
7.  <span data-ttu-id="ff41a-136">[**詳細**設定] をクリックして、グラフの網掛けおよび形状のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-136">Click **Advanced** to set shading and shape options for the graph.</span></span>  
  
8.  <span data-ttu-id="ff41a-137">[**閉じる**] をクリックして [**詳細**オプション] ダイアログボックスを閉じ、[**完了**] をクリックしてグラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-137">Click **Close** to exit the **Advanced** options dialog box, and then click **Finish** to create the graph.</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="ff41a-138">完成したダイアグラムの調査と変更</span><span class="sxs-lookup"><span data-stu-id="ff41a-138">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="ff41a-139">ネットワークの依存グラフが作成された後も、Visio の機能を使用して引き続きグラフを変更し強化することができます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-139">After Visio has created the network dependency graph, you can continue to modify and enhance the graph by using the features in Visio.</span></span>  
  
 <span data-ttu-id="ff41a-140">次の図は、依存関係ネットワーク グラフの既定のレイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="ff41a-140">The following graphic shows the default layout of a dependency network graph.</span></span>  
  
 <span data-ttu-id="ff41a-141">[アートプレースホルダー]</span><span class="sxs-lookup"><span data-stu-id="ff41a-141">[art placeholder]</span></span>  
  
1.  <span data-ttu-id="ff41a-142">Visio**ビュー**リボンの [**タスクペイン**] 領域にある [**パンとズーム**] コントロールを使用して、グラフのセクションにフォーカスを移動し、ダイアグラム内を移動します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-142">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a section of the graph and move around the diagram.</span></span>  
  
2.  <span data-ttu-id="ff41a-143">Visio の [**ページの再レイアウト**] オプションで提供されるさまざまなグラフレイアウトを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="ff41a-143">Experiment with different graph layouts provided by the Visio **Re-Layout Page** option.</span></span>  
  
3.  <span data-ttu-id="ff41a-144">[**アドイン**] リボンをクリックし、データマイニングダイアグラムを操作するために使用するカスタムツールバーの1つを表示します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-144">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="ff41a-145">**レイアウト**</span><span class="sxs-lookup"><span data-stu-id="ff41a-145">**Layout**</span></span>  
     <span data-ttu-id="ff41a-146">ページ上のノードのレイアウトを最適化し、すべてのノードが表示されるように表示を変更します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-146">Optimizes the layout of nodes on the page, and changes the view so that all nodes are visible.</span></span>  
  
     <span data-ttu-id="ff41a-147">**[ページのサイズ変更]**</span><span class="sxs-lookup"><span data-stu-id="ff41a-147">**Resize Page**</span></span>  
     <span data-ttu-id="ff41a-148">すべてのノードが表示されるように、ページのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-148">Changes the size of the page so that all nodes are visible.</span></span>  
  
     <span data-ttu-id="ff41a-149">**[枠の太さ]**</span><span class="sxs-lookup"><span data-stu-id="ff41a-149">**Edge Strength**</span></span>  
     <span data-ttu-id="ff41a-150">グラフ全体の枠の太さの表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-150">Toggles display of edge strength for the entire graph.</span></span> <span data-ttu-id="ff41a-151">枠とは、ノード間の接続です。</span><span class="sxs-lookup"><span data-stu-id="ff41a-151">An edge is a connection between nodes.</span></span> <span data-ttu-id="ff41a-152">スライダー コントロールを使用すると、強度が低い接続をフィルターで除外できます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-152">You can use the slider control to filter out connections that are not strong.</span></span>  
  
     <span data-ttu-id="ff41a-153">**Slider**</span><span class="sxs-lookup"><span data-stu-id="ff41a-153">**Slider**</span></span>  
     <span data-ttu-id="ff41a-154">**スライダー**を使用すると、依存関係ネットワークダイアグラムに表示されるリレーションシップの強度を制御できます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-154">The **Slider** helps you control the strength of the relationships that are displayed in the dependency network diagram.</span></span>  
  
     <span data-ttu-id="ff41a-155">グラフ内の各ノードは状態を表します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-155">Each node in the graph represents a state.</span></span> <span data-ttu-id="ff41a-156">矢印は、2 つの状態間の遷移とその遷移に関連付けられた確率を表します。</span><span class="sxs-lookup"><span data-stu-id="ff41a-156">An arrow represents a transition between two states and the probability that is associated with the transition.</span></span> <span data-ttu-id="ff41a-157">グラフに表示されるノードの数を減らすには、スライダー バーを上方向に動かします。</span><span class="sxs-lookup"><span data-stu-id="ff41a-157">To reduce the number of nodes in the graph, move the slider bar up.</span></span>  
  
     <span data-ttu-id="ff41a-158">グラフに表示されるノードの数を増やすには、スライダー バーを下方向に動かします。</span><span class="sxs-lookup"><span data-stu-id="ff41a-158">To increase the number of nodes in the graph, move the slider bar down.</span></span>  
  
     <span data-ttu-id="ff41a-159">**項目の追加**</span><span class="sxs-lookup"><span data-stu-id="ff41a-159">**Add Items**</span></span>  
     <span data-ttu-id="ff41a-160">[**表示するノードの選択**] ダイアログボックスを開きます。これにより、グラフに追加する新しいノードを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-160">Opens the **Select Nodes to Render** dialog box so that you can select new nodes to add to the graph.</span></span>  
  
4.  <span data-ttu-id="ff41a-161">モデルに接続した状態のまま、好みに応じてグラフを単純または詳細にし、注釈を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="ff41a-161">You can make the graphs as simple or elaborate as you like, and add annotations, while staying connected to the model.</span></span>  
  
     <span data-ttu-id="ff41a-162">[図のプレースホルダー]</span><span class="sxs-lookup"><span data-stu-id="ff41a-162">[ art placeholder]</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ff41a-163">アドインの以前のバージョンで使用できた依存ノードの強調表示などのショートカット メニュー オプションは、Office 2013 では機能しません。</span><span class="sxs-lookup"><span data-stu-id="ff41a-163">Highlighting of dependent nodes and other shortcut menu options that were available in previous versions of the Add-Ins do not work in Office 2013.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff41a-164">参照</span><span class="sxs-lookup"><span data-stu-id="ff41a-164">See Also</span></span>  
 [<span data-ttu-id="ff41a-165">データマイニングアドインの &#40;SQL Server Visio データマイニングダイアグラムのトラブルシューティング&#41;</span><span class="sxs-lookup"><span data-stu-id="ff41a-165">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
