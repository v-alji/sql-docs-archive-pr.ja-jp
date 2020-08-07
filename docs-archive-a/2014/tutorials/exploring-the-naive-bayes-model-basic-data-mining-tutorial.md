---
title: Naive Bayes モデルの調査 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a26fa972e1ed50e2f4107026210a5935fcb86d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719112"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a><span data-ttu-id="1ff49-102">Naive Bayes モデルの検証 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="1ff49-102">Exploring the Naive Bayes Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="1ff49-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes アルゴリズムには、自転車の購入と入力属性の間の相互作用を表示するためのいくつかの方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="1ff49-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm provides several methods for displaying the interaction between bike buying and the input attributes.</span></span>  
  
 <span data-ttu-id="1ff49-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes ビューアーには、Naive Bayes マイニングモデルの調査に使用できる次のタブが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1ff49-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes Viewer provides the following tabs for use in exploring Naive Bayes mining models:</span></span>  
  
 
  
##  <a name="dependency-network"></a><a name="DependencyNetwork"></a><span data-ttu-id="1ff49-105">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="1ff49-105">Dependency Network</span></span>  
 <span data-ttu-id="1ff49-106">[**依存関係ネットワーク**] タブは、ツリービューアーの [**依存関係ネットワーク**] タブと同じように動作し [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-106">The **Dependency Network** tab works in the same way as the **Dependency Network** tab for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Tree Viewer.</span></span> <span data-ttu-id="1ff49-107">ビューアーの各ノードは属性を表し、ノード間を結ぶ線は関係を表します。</span><span class="sxs-lookup"><span data-stu-id="1ff49-107">Each node in the viewer represents an attribute, and the lines between nodes represent relationships.</span></span> <span data-ttu-id="1ff49-108">このビューアーでは、予測可能属性 Bike Buyer の状態に影響を与えるすべての属性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-108">In the viewer, you can see all the attributes that affect the state of the predictable attribute, Bike Buyer.</span></span>  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a><span data-ttu-id="1ff49-109">[依存関係ネットワーク] タブでモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="1ff49-109">To explore the model in the Dependency Network tab</span></span>  
  
1.  <span data-ttu-id="1ff49-110">[**マイニングモデルビューアー** ] タブの上部にある [**マイニングモデル**] ボックスの一覧を使用すると、モデルに切り替えることが `TM_NaiveBayes` できます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-110">Use the **Mining Model** list at the top of the **Mining Model Viewer** tab to switch to the `TM_NaiveBayes` model.</span></span>  
  
2.  <span data-ttu-id="1ff49-111">[**ビューアー** ] ボックスの一覧を使用して、 **Microsoft Naive Bayes Viewer**に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-111">Use the **Viewer** list to switch to **Microsoft Naive Bayes Viewer**.</span></span>  
  
3.  <span data-ttu-id="1ff49-112">ノードをクリックすると、 `Bike Buyer` その依存関係が識別されます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-112">Click the `Bike Buyer` node to identify its dependencies.</span></span>  
  
     <span data-ttu-id="1ff49-113">ピンクの網掛けは、すべての属性が自転車の購入に影響を与えることを表します。</span><span class="sxs-lookup"><span data-stu-id="1ff49-113">The pink shading indicates that all of the attributes have an effect on bike buying.</span></span>  
  
4.  <span data-ttu-id="1ff49-114">スライダーを調整して、最も影響の大きい属性を特定します。</span><span class="sxs-lookup"><span data-stu-id="1ff49-114">Adjust the slider to identify the most influential attribute.</span></span>  
  
     <span data-ttu-id="1ff49-115">スライダーを下方向に動かすと、[Bike Buyer] 列に最も大きな影響を与える属性のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-115">As you lower the slider, only the attributes that have the greatest effect on the [Bike Buyer] column remain.</span></span> <span data-ttu-id="1ff49-116">スライダーを調整することにより、所有する車の台数、通勤距離、子供の数などが影響の大きい属性であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1ff49-116">By adjusting the slider, you can discover that a few of the most influential attributes are: number of cars owned, commute distance, and total number of children.</span></span>  
 
  
##  <a name="attribute-profiles"></a><a name="AttributeProfiles"></a> <span data-ttu-id="1ff49-117">属性のプロファイル</span><span class="sxs-lookup"><span data-stu-id="1ff49-117">Attribute Profiles</span></span>  
 <span data-ttu-id="1ff49-118">[**属性のプロファイル**] タブでは、入力属性のさまざまな状態が予測可能な属性の結果にどのように影響するかを説明します。</span><span class="sxs-lookup"><span data-stu-id="1ff49-118">The **Attribute Profiles** tab describes how different states of the input attributes affect the outcome of the predictable attribute.</span></span>  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a><span data-ttu-id="1ff49-119">[属性のプロファイル] タブでモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="1ff49-119">To explore the model in the Attribute Profiles tab</span></span>  
  
1.  <span data-ttu-id="1ff49-120">[**予測可能**] ボックスで、が選択されていることを確認し `Bike Buyer` ます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-120">In the **Predictable** box, verify that `Bike Buyer` is selected.</span></span>  
  
2.  <span data-ttu-id="1ff49-121">[**マイニング凡例**] が**属性プロファイル**の表示をブロックしている場合は、そのまま移動します。</span><span class="sxs-lookup"><span data-stu-id="1ff49-121">If the **Mining Legend** is blocking display of the **Attribute profiles**, move it out of the way.</span></span>  
  
3.  <span data-ttu-id="1ff49-122">[**ヒストグラム**バー] ボックスで、[ **5**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1ff49-122">In the **Histogram** bars box, select **5**.</span></span>  
  
     <span data-ttu-id="1ff49-123">このモデルでは、1 つの変数に対する状態の最大数が 5 になります。</span><span class="sxs-lookup"><span data-stu-id="1ff49-123">In our model, 5 is the maximum number of states for any one variable.</span></span>  
  
     <span data-ttu-id="1ff49-124">この予測可能属性の状態に影響を与える属性の一覧が表示されます。さらに、それぞれの入力属性について、各状態の値、および予測可能属性の各状態に対する影響分布も表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-124">The attributes that affect the state of this predictable attribute are listed together with the values of each state of the input attributes and their distributions in each state of the predictable attribute.</span></span>  
  
4.  <span data-ttu-id="1ff49-125">[**属性**] 列で、**車が所有**している数値を検索します。</span><span class="sxs-lookup"><span data-stu-id="1ff49-125">In the **Attributes** column, find **Number Cars Owned**.</span></span>  <span data-ttu-id="1ff49-126">自転車の購入者 (1 のラベルが付けられた列) と非購入者 (0 のラベルが付けられた列) について、ヒストグラムで違いを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-126">Notice the differences in the histograms for bike buyers (column labeled 1) and non-buyers (column labeled 0).</span></span> <span data-ttu-id="1ff49-127">車の台数が 0 または 1 の人は、自転車を購入する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="1ff49-127">A person with zero or one car is much more likely to buy a bike.</span></span>  
  
5.  <span data-ttu-id="1ff49-128">自転車の購入者 (列ラベルが 1) のセル**番号**をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ff49-128">Double-click the **Number Cars Owned** cell in the bike buyer (column labeled 1) column.</span></span>  
  
     <span data-ttu-id="1ff49-129">[**マイニング凡例**] には、より詳細なビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-129">The **Mining Legend** displays a more detailed view.</span></span>  
  
  
##  <a name="attribute-characteristics"></a><a name="AttributeCharacteristics"></a><span data-ttu-id="1ff49-130">属性の特性</span><span class="sxs-lookup"><span data-stu-id="1ff49-130">Attribute Characteristics</span></span>  
 <span data-ttu-id="1ff49-131">[**属性の特性**] タブでは、属性と値を選択して、選択した値のケースで他の属性の値がどの程度の頻度で表示されるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-131">With the **Attribute Characteristics** tab, you can select an attribute and value to see how frequently values for other attributes appear in the selected value cases.</span></span>  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a><span data-ttu-id="1ff49-132">[属性の特性] タブでモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="1ff49-132">To explore the model in the Attribute Characteristics tab</span></span>  
  
1.  <span data-ttu-id="1ff49-133">[**属性**] ボックスの一覧で、が選択されていることを確認し `Bike Buyer` ます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-133">In the **Attribute** list, verify that `Bike Buyer` is selected.</span></span>  
  
2.  <span data-ttu-id="1ff49-134">**値**を**1**に設定します。</span><span class="sxs-lookup"><span data-stu-id="1ff49-134">Set the **Value** to **1**.</span></span>  
  
     <span data-ttu-id="1ff49-135">このビューアーで見ると、自転車を購入する可能性が高いのは、北米地域に在住し、子供と同居しておらず、通勤距離が短い顧客であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1ff49-135">In the viewer, you will see that customers who have no children at home, short commutes, and live in the North America region are more likely to buy a bike.</span></span>  
  
  
##  <a name="attribute-discrimination"></a><a name="AttributeDiscrimination"></a><span data-ttu-id="1ff49-136">属性の識別</span><span class="sxs-lookup"><span data-stu-id="1ff49-136">Attribute Discrimination</span></span>  
 <span data-ttu-id="1ff49-137">[**属性の識別**] タブでは、自転車の購入とその他の属性値の2つの不連続値の関係を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="1ff49-137">With the **Attribute Discrimination** tab, you can investigate the relationship between two discrete values of bike buying and other attribute values.</span></span> <span data-ttu-id="1ff49-138">モデルに `TM_NaiveBayes` は1と0の2つの状態しかないため、ビューアーを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1ff49-138">Because the `TM_NaiveBayes` model has only two states, 1 and 0, you do not have to make any changes to the viewer.</span></span>  
  
 <span data-ttu-id="1ff49-139">このビューアーでは、車を所有していない人が自転車を購入する傾向にあり、車を 2 台所有している人は自転車を購入しない傾向にあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1ff49-139">In the viewer, you can see that people who do not own cars tend to buy bicycles, and people who own two cars tend not to buy bicycles.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1ff49-140">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1ff49-140">Related Tasks</span></span>  
 <span data-ttu-id="1ff49-141">他のマイニング モデルを探索するには、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ff49-141">See the following topics to explore the other mining models.</span></span>  
  
-   [<span data-ttu-id="1ff49-142">デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="1ff49-142">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="1ff49-143">「基本的なデータマイニングチュートリアル」 &#40;クラスターモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="1ff49-143">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="1ff49-144">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="1ff49-144">Next Lesson</span></span>  
 [<span data-ttu-id="1ff49-145">レッスン 5: モデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="1ff49-145">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="1ff49-146">このレッスンの前の作業</span><span class="sxs-lookup"><span data-stu-id="1ff49-146">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="1ff49-147">「基本的なデータマイニングチュートリアル」 &#40;クラスターモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="1ff49-147">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ff49-148">参照</span><span class="sxs-lookup"><span data-stu-id="1ff49-148">See Also</span></span>  
 <span data-ttu-id="1ff49-149">[Microsoft Naive Bayes ビューアーを使用したモデルの参照](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="1ff49-149">[Browse a Model Using the Microsoft Naive Bayes Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md) </span></span>  
 <span data-ttu-id="1ff49-150">[[属性の識別] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="1ff49-150">[Attribute Discrimination Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="1ff49-151">[[属性のプロファイル] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="1ff49-151">[Attribute Profiles Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="1ff49-152">[[属性の特性] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="1ff49-152">[Attribute Characteristics Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="1ff49-153">[[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="1ff49-153">[Dependency Network Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)</span></span>  
  
  
