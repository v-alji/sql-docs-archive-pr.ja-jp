---
title: Visio でのデータマイニングモデルの表示 (データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- diagram, modifying
- templates [Visio]
- shapes, data mining
- diagram
ms.assetid: 5841adea-6650-4fae-8526-26af33edbede
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3c1e63c058295b93e2562c64a6df90a30273a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634653"
---
# <a name="viewing-data-mining-models-in-visio-data-mining-add-ins"></a><span data-ttu-id="70a11-102">Visio でのデータ マイニング モデルの参照 (データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="70a11-102">Viewing Data Mining Models in Visio (Data Mining Add-ins)</span></span>
  <span data-ttu-id="70a11-103">データ マイニング用 Visio 図形は、サーバーに接続して、既存のデータ マイニング モデルを表すダイアグラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="70a11-103">The Visio shapes for data mining let you connect to a server and create a diagram representing an existing data mining model.</span></span> <span data-ttu-id="70a11-104">ダイアグラムは、Visio のコントロールを使用してカスタマイズできますが、データのドリル ダウン、基になる統計の公開、基になるモデルの操作もすることができます。</span><span class="sxs-lookup"><span data-stu-id="70a11-104">The diagrams can then be customized using Visio controls, but you can also drill down into data, expose some of the underlying statistics, and work with the underlying model.</span></span>  
  
## <a name="building-a-model-diagram"></a><span data-ttu-id="70a11-105">モデル ダイアグラムの作成</span><span class="sxs-lookup"><span data-stu-id="70a11-105">Building a Model Diagram</span></span>  
 <span data-ttu-id="70a11-106">データマイニングの Visio 図形を含むファイルを開くと、[**図形**] ペインに次の図形が表示されます。</span><span class="sxs-lookup"><span data-stu-id="70a11-106">When you open the file containing the Visio shapes for data mining, the **Shapes** pane shows the following shapes.</span></span>  
  
 <span data-ttu-id="70a11-107">Visio を開いたときにデータ マイニング図形が表示されない場合は、インストール フォルダーにあるテンプレート ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="70a11-107">If you do not see the data mining shapes when you open Visio, open the template file from the installation folder.</span></span>  
  
 <span data-ttu-id="70a11-108">![DM](media/dm-stencil.gif "DM")</span><span class="sxs-lookup"><span data-stu-id="70a11-108">![DM](media/dm-stencil.gif "DM")</span></span>  
  
 <span data-ttu-id="70a11-109">図形を使用するには、図形をページにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="70a11-109">To use a shape, drag it to the page.</span></span> <span data-ttu-id="70a11-110">図形ごとに異なるウィザードが起動されます。ウィザードに従って、ソース データを選択し、そのダイアグラムに必要なオプションを設定します。さらに、網掛けやその他の表示オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="70a11-110">Each of the shapes opens a different wizard, which helps you select source data, set options for the specific diagram type, and specify shading and other display options.</span></span>  
  
 <span data-ttu-id="70a11-111">次の表は、ダイアグラムの種類とそれぞれに使用できるモデルの種類を示しています。</span><span class="sxs-lookup"><span data-stu-id="70a11-111">The following table lists the types of models that you can use with each type of diagram.</span></span>  
  
|<span data-ttu-id="70a11-112">Visio 図形</span><span class="sxs-lookup"><span data-stu-id="70a11-112">Visio shape</span></span>|<span data-ttu-id="70a11-113">サポートされているモデル</span><span class="sxs-lookup"><span data-stu-id="70a11-113">Supported models</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="70a11-114">意思決定ツリー</span><span class="sxs-lookup"><span data-stu-id="70a11-114">Decision Tree</span></span>|<span data-ttu-id="70a11-115">この図形はデシジョン ツリー アルゴリズムまたは線形回帰アルゴリズムに基づくモデルに使用します。</span><span class="sxs-lookup"><span data-stu-id="70a11-115">Use this shape for models based on the decision tree or linear regression algorithms.</span></span>|  
|<span data-ttu-id="70a11-116">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="70a11-116">Dependency Network</span></span>|<span data-ttu-id="70a11-117">この図形は Naive Bayes、デシジョン ツリー、アソシエーション ルールのいずれかのアルゴリズムに基づくモデルに使用します。</span><span class="sxs-lookup"><span data-stu-id="70a11-117">Use this shape for models based on any of the following algorithms: Naive Bayes, Decision Trees, or Association Rules.</span></span>|  
|<span data-ttu-id="70a11-118">クラスター</span><span class="sxs-lookup"><span data-stu-id="70a11-118">Cluster</span></span>|<span data-ttu-id="70a11-119">この図形はクラスタリング アルゴリズムに基づくモデルに使用します。</span><span class="sxs-lookup"><span data-stu-id="70a11-119">Use this shape for models based on clustering algorithms.</span></span>|  
  
 <span data-ttu-id="70a11-120">マイニング モデルのデータの種類に応じて、ウィザードに表示されるオプションも異なります。</span><span class="sxs-lookup"><span data-stu-id="70a11-120">Depending on the type of data in your mining model, the wizard may offer different options.</span></span> <span data-ttu-id="70a11-121">たとえば、連続する数値を含む列はカテゴリ変数とは異なる方法で視覚化されます。</span><span class="sxs-lookup"><span data-stu-id="70a11-121">For example, columns that contain continuous numbers are visualized differently than categorical variables.</span></span>  
  
## <a name="working-with-completed-shapes"></a><span data-ttu-id="70a11-122">完成した図形の操作</span><span class="sxs-lookup"><span data-stu-id="70a11-122">Working with Completed Shapes</span></span>  
 <span data-ttu-id="70a11-123">ダイアグラムが完成したら、それを使用してデータ マイニング モデルを参照したり、プレゼンテーションで使用できるように強化したりできます。</span><span class="sxs-lookup"><span data-stu-id="70a11-123">After the diagram is complete, you can use it to browse the data mining model or enhance the diagram for use in presentations.</span></span>  
  
### <a name="visio-menus"></a><span data-ttu-id="70a11-124">Visio のメニュー</span><span class="sxs-lookup"><span data-stu-id="70a11-124">Visio Menus</span></span>  
 <span data-ttu-id="70a11-125">Visio には、ダイアグラムの強化に役立つさまざまな描画コントロール、配色テーマ、ショートカット メニューが用意されています。</span><span class="sxs-lookup"><span data-stu-id="70a11-125">Visio provides a variety of rendering controls, themes, and shortcut menus to help enhance a diagram.</span></span>  
  
-   <span data-ttu-id="70a11-126">Visio のテーマを使用してダイアグラムの色を変更します。</span><span class="sxs-lookup"><span data-stu-id="70a11-126">Use Visio themes to alter diagram colors.</span></span>  
  
-   <span data-ttu-id="70a11-127">コネクタまたはダイアグラムのレイアウトを変更します。</span><span class="sxs-lookup"><span data-stu-id="70a11-127">Change connectors or diagram layout.</span></span>  
  
### <a name="data-mining-menus"></a><span data-ttu-id="70a11-128">データ マイニングのメニュー</span><span class="sxs-lookup"><span data-stu-id="70a11-128">Data Mining Menus</span></span>  
 <span data-ttu-id="70a11-129">これらのツール バーとメニュー項目は、各図形またはモデルの種類に固有のアドインによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="70a11-129">These toolbars and menu items are provided by the add-ins that are specific to each shape or model type</span></span>  
  
-   <span data-ttu-id="70a11-130">それぞれのダイアグラムの種類には図形のショートカット メニューがあり、これを使用すると特殊なオプションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="70a11-130">Each diagram type has a shortcut menu for the shape that lets you access special options.</span></span> <span data-ttu-id="70a11-131">このメニューには、すべての Visio 図形に共通するオプションが多数ありますが、一部のオプションはデータマイニングテンプレートに固有です。</span><span class="sxs-lookup"><span data-stu-id="70a11-131">Although many options in this menu are common to all Visio shapes, some options are unique to the data mining templates</span></span>  
  
     <span data-ttu-id="70a11-132">たとえば、デシジョン ツリー ダイアグラムにおいて、個々のノードをクリックし、その子ノードを折りたたむと、ダイアグラムを単純化できます。また、子ノードを別のページに移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="70a11-132">For example, in a decision tree diagram, you can click an individual node and then collapse the child nodes to make the diagram simpler, or move child nodes to a separate page.</span></span>  
  
-   <span data-ttu-id="70a11-133">図形はモデル データにバインドされているため、ダイアグラムを使用してある程度の操作も実行できます。</span><span class="sxs-lookup"><span data-stu-id="70a11-133">Because the shape is bound to the model data, you can also do some amount of exploration using the diagram:</span></span>  
  
     <span data-ttu-id="70a11-134">表示されるノードをフィルター処理する、グラフのツリーのレベルまたは深さを変更する。</span><span class="sxs-lookup"><span data-stu-id="70a11-134">Filter the nodes that are displayed, or change the level of the tree or depth of the graph.</span></span>  
  
     <span data-ttu-id="70a11-135">特定のセクションを拡大する、特定の属性を含んでいるノードを検索する、または依存グラフをそのエッジ (確率) でフィルター処理する。</span><span class="sxs-lookup"><span data-stu-id="70a11-135">Zoom in on specific sections, search for nodes that contain a certain attribute, or filter a dependency graph by its edges (probability).</span></span>  
  
## <a name="walkthroughs"></a><span data-ttu-id="70a11-136">チュートリアル</span><span class="sxs-lookup"><span data-stu-id="70a11-136">Walkthroughs</span></span>  
 <span data-ttu-id="70a11-137">完成したダイアグラムを操作および解釈する方法の例については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="70a11-137">For examples of how to work with and interpret a completed diagram, see these topics:</span></span>  
  
 [<span data-ttu-id="70a11-138">クラスター ダイアグラムのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="70a11-138">Cluster Diagram Walkthrough</span></span>](cluster-diagram-walkthrough-data-mining-add-ins.md)  
  
 [<span data-ttu-id="70a11-139">依存関係ネットワーク ダイアグラムのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="70a11-139">Dependency Net Diagram Walkthrough</span></span>](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
 [<span data-ttu-id="70a11-140">デシジョン ツリー ダイアグラムのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="70a11-140">Decision Tree Diagram Walkthrough</span></span>](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
## <a name="see-also"></a><span data-ttu-id="70a11-141">参照</span><span class="sxs-lookup"><span data-stu-id="70a11-141">See Also</span></span>  
 [<span data-ttu-id="70a11-142">Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;</span><span class="sxs-lookup"><span data-stu-id="70a11-142">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
