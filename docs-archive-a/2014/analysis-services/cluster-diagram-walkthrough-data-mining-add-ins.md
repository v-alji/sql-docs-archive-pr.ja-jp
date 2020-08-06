---
title: クラスターダイアグラムのチュートリアル (データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, cluster
- diagram, cluster
- shapes, data mining
- shapes, cluster
- data mining layout toolbar
ms.assetid: 761bef6a-37d4-4b19-944e-f2aadc75a242
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ee8cce3cd2498d765c9b69e7f352b49cb0f115
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634146"
---
# <a name="cluster-diagram-walkthrough-data-mining-add-ins"></a><span data-ttu-id="fc7b9-102">クラスター ダイアグラムのチュートリアル (データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="fc7b9-102">Cluster Diagram Walkthrough (Data Mining Add-ins)</span></span>
  <span data-ttu-id="fc7b9-103">クラスターモデルを作成した後は、**クラスター**図形を使用して Visio にインポートして、レイアウトのカスタマイズと拡張を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-103">After you have created a clustering model, you can import it into Visio using the **Cluster** shape and then continue to customize and enhance the layout.</span></span> <span data-ttu-id="fc7b9-104">**Visio 用のデータマイニング図形**には、データマイニングダイアグラムを操作するための次のカスタムコントロールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-104">The **Data Mining Shapes for Visio** include the following custom controls for working with data mining diagrams:</span></span>  
  
-   <span data-ttu-id="fc7b9-105">クラスター ダイアグラムの描画コントロール</span><span class="sxs-lookup"><span data-stu-id="fc7b9-105">Rendering controls for the cluster diagram</span></span>  
  
     <span data-ttu-id="fc7b9-106">これらのオプションは、Visio ワークスペースに図形をドロップしたときに起動される**クラスターウィザード**の一部です。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-106">These options are part of the **Cluster Wizard** that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="fc7b9-107">**データマイニングレイアウト**ツールバー</span><span class="sxs-lookup"><span data-stu-id="fc7b9-107">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="fc7b9-108">これは、データ マイニング図形の操作に役立つように Visio ワークスペースに追加されます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-108">These options are added to the Visio workspace to help you interact with the data mining shape.</span></span> <span data-ttu-id="fc7b9-109">オプションは、使用しているデータ マイニング モデルの種類に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-109">The options are different depending on which type of data mining model you are using.</span></span>  
  
## <a name="build-a-cluster-diagram"></a><span data-ttu-id="fc7b9-110">クラスター ダイアグラムの作成</span><span class="sxs-lookup"><span data-stu-id="fc7b9-110">Build a Cluster Diagram</span></span>  
 <span data-ttu-id="fc7b9-111">このチュートリアルでは、Visio でクラスター図を作成してカスタマイズする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-111">This walkthrough demonstrates how to build and customize a clustering diagram in Visio.</span></span>  
  
 <span data-ttu-id="fc7b9-112">続行するには、使用可能なクラスター モデルが既に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-112">To follow along, you should have a clustering model already available.</span></span> <span data-ttu-id="fc7b9-113">モデルがない場合は、[クラスターウィザード &#40;&#41;Excel 用データマイニングアドイン](cluster-wizard-data-mining-add-ins-for-excel.md)ウィザードを使用して、サンプルブックのトレーニングデータセットを使用して、すべての既定値を使用してモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-113">If you do not have a model, use the [Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) wizard and create a model using the Training data set in the sample workbook, using all the defaults.</span></span>  
  
#### <a name="use-the-cluster-visio-shape-wizard"></a><span data-ttu-id="fc7b9-114">Visio クラスター図形ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="fc7b9-114">Use the Cluster Visio Shape Wizard</span></span>  
  
1.  <span data-ttu-id="fc7b9-115">[**図形**] ボックスの一覧に [ **Microsoft データマイニング図形**] が表示されない場合は、[**その他の図形**] をクリックし、[**ステンシルを開く**] を選択して、既定のインストール場所からテンプレートを開きます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-115">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="fc7b9-116">\<drive>: SQL Server 2012 DM アドイン</span><span class="sxs-lookup"><span data-stu-id="fc7b9-116">\<drive>:\Program files\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="fc7b9-117">**クラスター**図形をページにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-117">Drag the **Cluster** shape onto the page.</span></span>  
  
3.  <span data-ttu-id="fc7b9-118">**Visio クラスター図形ウィザード**の [ようこそ] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-118">On the welcome page of the **Cluster Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="fc7b9-119">**クラスターウィザード**の [**データソースの選択**] ページで、視覚化する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データマイニングモデルが含まれているサーバーへの接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-119">On the **Select a Data Source** page of the **Cluster Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that contains the data mining models you want to visualize.</span></span>  
  
5.  <span data-ttu-id="fc7b9-120">適切なマイニングモデルを選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-120">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="fc7b9-121">クラスターモデルを選択していることを確認するには、[**プロパティ**] ウィンドウで説明を確認します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-121">To make sure you choose a clustering model, review the description in the **Properties** pane.</span></span>  
  
6.  <span data-ttu-id="fc7b9-122">接続に成功した場合は、[**クラスターダイアグラムのオプション**] ページで、Visio プレゼンテーションに含めるクラスターダイアグラムの種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-122">If the connection is successful, on the page, **Options for cluster diagram**, you decide which type of cluster diagram to include in your Visio presentation:</span></span>  
  
     <span data-ttu-id="fc7b9-123">**[クラスター図形のみを表示する]**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-123">**Show cluster shapes only**</span></span>  
     <span data-ttu-id="fc7b9-124">選択した四角形などの図形で各クラスターが表現される単純なクラスター ダイアグラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-124">This option creates a simple cluster diagram, with each cluster represented by a rectangle or other shape you choose</span></span>  
  
     <span data-ttu-id="fc7b9-125">**[特性グラフと共にクラスターを表示する]**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-125">**Show clusters with characteristics chart**</span></span>  
     <span data-ttu-id="fc7b9-126">上と同じグラフを作成しますが、図形の内部にクラスターの特性を表すヒストグラムを表示します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-126">This option creates the same chart as above, but inside the shapes are histograms that describe the characteristics of the cluster.</span></span>  
  
     <span data-ttu-id="fc7b9-127">![Visio のクラスター特性グラフの例](media/dm13-visio-cluster-samplecharshape.gif "Visio のクラスター特性グラフの例")</span><span class="sxs-lookup"><span data-stu-id="fc7b9-127">![Example of cluster characteristics chart in Visio](media/dm13-visio-cluster-samplecharshape.gif "Example of cluster characteristics chart in Visio")</span></span>  
  
     <span data-ttu-id="fc7b9-128">**[識別グラフと共にクラスターを表示する]**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-128">**Show clusters with discrimination chart**</span></span>  
     <span data-ttu-id="fc7b9-129">クラスター ダイアグラムと同じ図を作成しますが、他のクラスターとの区別に最も役立つ現在のクラスターの特性を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-129">This option creates the same chart as the cluster diagram, but instead lists the characteristics of the current cluster that most strongly distinguish it from other clusters.</span></span>  
  
     <span data-ttu-id="fc7b9-130">ウィザードがダイアグラムを作成した後、クラスターを右クリックして、新しいグラフの種類を選択すると、別の種類のグラフに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-130">You can switch to another chart type after the wizard has built the diagram, by right-clicking a cluster and selecting a new chart type.</span></span> <span data-ttu-id="fc7b9-131">ここでは、[**特性グラフを含むクラスターを表示する**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-131">For now, choose the option, **Show clusters with characteristics chart**.</span></span>  
  
7.  <span data-ttu-id="fc7b9-132">[**グラフ内の行数**] オプションは5のままにします。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-132">Leave the option, **Number of rows in the chart**, as 5.</span></span>  
  
     <span data-ttu-id="fc7b9-133">このオプションは、モデル内のクラスターの数を変更しません。各クラスターの特徴として表示できる属性の数を制限するだけです。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-133">This option doesn't change the number of clusters in the model; it simply limits the number of attributes that can be displayed as features of each cluster.</span></span>  
  
     <span data-ttu-id="fc7b9-134">ただし、このオプションはグラフデータに対するフィルターとして機能するため、後で項目の数を増やすことはできません。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-134">However, the option acts as a filter on the chart data, so you can't increase the number of items later.</span></span>  
  
8.  <span data-ttu-id="fc7b9-135">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-135">Click **Advanced**.</span></span>  
  
     <span data-ttu-id="fc7b9-136">[**クラスターのオプション**] ダイアログボックスでは、ダイアグラムで使用される図形の外観をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-136">The **Cluster Options** dialog box is where you customize the visual appearance of shapes used in the diagram.</span></span> <span data-ttu-id="fc7b9-137">グラフで使用する色と、クラスターに使用する図形を変更できます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-137">You can change the colors used in the graph, and the shape used for clusters.</span></span>  
  
     <span data-ttu-id="fc7b9-138">**シェーディング変数**コントロールは、Office 2013 では機能しません。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-138">The **Shading Variable** control does not work in Office 2013.</span></span>  
  
     <span data-ttu-id="fc7b9-139">![図形の色を選択するには [詳細設定] をクリック](media/dm13-visio-clusteroptions-advanced.gif "図形の色を選択するには [詳細設定] をクリック")</span><span class="sxs-lookup"><span data-stu-id="fc7b9-139">![click Advanced to choose shape colors](media/dm13-visio-clusteroptions-advanced.gif "click Advanced to choose shape colors")</span></span>  
  
     <span data-ttu-id="fc7b9-140">**ヒント:** 一部の色は、後で Visio のテーマと図形の編集コントロールを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-140">**Tip:** Some colors can be altered later by using Visio themes and shape editing controls.</span></span> <span data-ttu-id="fc7b9-141">ただし、Visio の配色テーマは選択した色の一部をオーバーライドするため、最初は既定の色で使い、徐々に変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-141">However, Visio themes will also override some of these color selections, so we recommend starting with the default colors and gradually applying changes.</span></span>  
  
9. <span data-ttu-id="fc7b9-142">[**完了**] をクリックしてグラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-142">Click **Finish** to create the graph.</span></span>  
  
     <span data-ttu-id="fc7b9-143">ウィザードがデータ マイニング モデルから情報を取得して図形を描画し、各クラスターに属性と値を設定します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-143">The wizard retrieves information from the data mining model, renders the shapes, and populates each cluster with attributes and values.</span></span>  
  
     <span data-ttu-id="fc7b9-144">![依存関係ネットワーク](media/dm13-visiodepnet-defaultgraph.gif "依存関係ネットワーク")</span><span class="sxs-lookup"><span data-stu-id="fc7b9-144">![a dependency network](media/dm13-visiodepnet-defaultgraph.gif "a dependency network")</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="fc7b9-145">完成したダイアグラムの調査と変更</span><span class="sxs-lookup"><span data-stu-id="fc7b9-145">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="fc7b9-146">ダイアグラムの完成後、次の例に示すように、引き続き Visio コントロールを使用して外観をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-146">After the diagram is complete, you can continue to customize the appearance using the Visio controls, as shown in the following example.</span></span>  
  
 <span data-ttu-id="fc7b9-147">![Visio を使用してカスタマイズしたクラスター ダイアグラム](media/dm13-visio-clustercomplete1.gif "Visio を使用してカスタマイズしたクラスター ダイアグラム")</span><span class="sxs-lookup"><span data-stu-id="fc7b9-147">![cluster diagram customized using Visio](media/dm13-visio-clustercomplete1.gif "cluster diagram customized using Visio")</span></span>  
  
 <span data-ttu-id="fc7b9-148">基本的なクラスター図形はすべて、ウィザードによって生成されます。ダイアグラムの更新とカスタマイズには、以下のツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-148">All of the basic cluster shapes are generated by the wizard; use the following tools to update and personalize the diagram:</span></span>  
  
1.  <span data-ttu-id="fc7b9-149">[**クラスターオプション**] コントロールのスライダーをドラッグして、弱い関係を除外し、図を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-149">Drag the slider in the **Cluster Options** control, to filter out weaker relationships and simplify the diagram.</span></span>  
  
2.  <span data-ttu-id="fc7b9-150">Visio の [**再レイアウト] ページ**オプションを使用すると、さまざまなクラスターレイアウトを試すことができます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-150">Use the Visio **Re-Layout Page** option to experiment with different cluster layouts.</span></span>  
  
3.  <span data-ttu-id="fc7b9-151">[**デザイン**] タブの [**コネクタ**] オプションを使用して、コネクタのスタイルを変更し、行がクラスター上で交差しないようにします。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-151">Use the **Connectors** option on the **Design** tab to change the connector style to keep lines from crossing over clusters.</span></span>  
  
4.  <span data-ttu-id="fc7b9-152">[**アドイン**] リボンをクリックし、データマイニングダイアグラムを操作するために使用するカスタムツールバーの1つを表示します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-152">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="fc7b9-153">**レイアウト**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-153">**Layout**</span></span>  
     <span data-ttu-id="fc7b9-154">クラスターを並べ替えて現在のページに収まるように最適化します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-154">Optimizes the arrangement of clusters to fit in the current page.</span></span>  
  
     <span data-ttu-id="fc7b9-155">**[ページのサイズ変更]**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-155">**Resize Page**</span></span>  
     <span data-ttu-id="fc7b9-156">このコントロールは、HTML の以前のバージョンを対象としたものです。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-156">This control was intended for earlier HTML versions.</span></span> <span data-ttu-id="fc7b9-157">代わりに、Visio のページのサイズ変更コントロールを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-157">Use the Visio page resizing controls instead.</span></span>  
  
     <span data-ttu-id="fc7b9-158">**説明**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-158">**Description**</span></span>  
     <span data-ttu-id="fc7b9-159">クラスターが選択されている場合、このオプションをクリックすると、クラスターに関する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-159">If a cluster is selected, click this option to display details about the cluster.</span></span>  
  
     <span data-ttu-id="fc7b9-160">![クラスターの詳細を参照するには [説明] をクリック](media/dm13-visio-cluster-description-control.gif "クラスターの詳細を参照するには [説明] をクリック")</span><span class="sxs-lookup"><span data-stu-id="fc7b9-160">![click Description to get details about the cluster](media/dm13-visio-cluster-description-control.gif "click Description to get details about the cluster")</span></span>  
  
     <span data-ttu-id="fc7b9-161">**[枠の太さ]**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-161">**Edge Strength**</span></span>  
     <span data-ttu-id="fc7b9-162">クラスターを結ぶ線の信頼スコアが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-162">Displays confidence scores on the lines connecting clusters.</span></span>  
  
     <span data-ttu-id="fc7b9-163">ただし、背景も含めて、ウィザードが生成した既定値以外の特殊な書式設定を適用した場合は、この数字が表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-163">However, if you apply any special formatting other than the default generated by the wizard, including some backgrounds, these numbers might not be visible.</span></span>  
  
     <span data-ttu-id="fc7b9-164">**Slider**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-164">**Slider**</span></span>  
     <span data-ttu-id="fc7b9-165">クラスターを結ぶ線を絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-165">Filters the lines between clusters.</span></span> <span data-ttu-id="fc7b9-166">スライダーを上へ移動すると、最も重要な関連付けだけを残して、すべての線が削除されます。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-166">Moving the slider up removes all but the most important associations.</span></span>  
  
     <span data-ttu-id="fc7b9-167">**[網掛け]**</span><span class="sxs-lookup"><span data-stu-id="fc7b9-167">**Shading**</span></span>  
     <span data-ttu-id="fc7b9-168">このコントロールは、Office 2013 では機能しません。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-168">This control does not work in Office 2013.</span></span>  
  
5.  <span data-ttu-id="fc7b9-169">Visio**ビュー**リボンの [**タスクペイン**] 領域にある [**パンとズーム**] コントロールを使用して、一連のクラスターにフォーカスを移動し、ダイアグラム内を移動します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-169">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a set of clusters and move around the diagram.</span></span>  
  
6.  <span data-ttu-id="fc7b9-170">クラスターを右クリックして、クラスター図形に固有のオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-170">Right-click any cluster to see options specific to the cluster shape:</span></span>  
  
    -   <span data-ttu-id="fc7b9-171">グラフの種類を変更します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-171">Change the chart style.</span></span>  
  
    -   <span data-ttu-id="fc7b9-172">クラスター特性グラフを追加します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-172">Add a cluster characteristics chart.</span></span>  
  
    -   <span data-ttu-id="fc7b9-173">クラスター識別グラフを追加します。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-173">Add a cluster discrimination chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc7b9-174">参照</span><span class="sxs-lookup"><span data-stu-id="fc7b9-174">See Also</span></span>  
 [<span data-ttu-id="fc7b9-175">データマイニングアドインの &#40;SQL Server Visio データマイニングダイアグラムのトラブルシューティング&#41;</span><span class="sxs-lookup"><span data-stu-id="fc7b9-175">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
