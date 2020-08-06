---
title: Microsoft ニューラルネットワークビューアーを使用したモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model content, viewing
- classification mining model [Analysis Services]
- Microsoft Neural Network Viewer
- regression algorithms [Analysis Services]
- Neural Network Viewer [Analysis Services]
- neural network model [Analysis Services]
ms.assetid: 2343d746-c4f4-499b-9d3c-17d63310a9a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 77e08955d09b7995e34ac94b75f809a303ca0d2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645944"
---
# <a name="browse-a-model-using-the-microsoft-neural-network-viewer"></a><span data-ttu-id="1adb5-102">Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="1adb5-102">Browse a Model Using the Microsoft Neural Network Viewer</span></span>
  <span data-ttu-id="1adb5-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]のニューラルネットワークビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ニューラルネットワークアルゴリズムを使用して作成されたマイニングモデルが表示され [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="1adb5-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムでは、複数の入力と出力を分析できる分類および回帰マイニング モデルを作成します。このアルゴリズムは、制限のない分析と探索に非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates classification and regression mining models that can analyze multiple inputs and outputs, and is very useful for open-ended analyses and exploration.</span></span> <span data-ttu-id="1adb5-105">このアルゴリズムの詳細については、「 [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1adb5-105">For more information about this algorithm, see [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md).</span></span>  
  
 <span data-ttu-id="1adb5-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク ビューアーを使用してモデルを調べる場合、通常は対象の属性と状態を選択してから、ビューアーを使用して入力属性が結果に与える影響を確認します。</span><span class="sxs-lookup"><span data-stu-id="1adb5-106">When you explore a model using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer, you typically pick some target attribute and state, and then use the viewer to see how input attributes affect the outcome</span></span>  
  
 <span data-ttu-id="1adb5-107">たとえば、潜在的な顧客のクラスについて次の事実がわかっているとします。</span><span class="sxs-lookup"><span data-stu-id="1adb5-107">For example, suppose you know these facts about a class of potential customers:</span></span>  
  
-   <span data-ttu-id="1adb5-108">中高年 (40 ～ 50 歳)。</span><span class="sxs-lookup"><span data-stu-id="1adb5-108">Middle aged (40 to 50 years old).</span></span>  
  
-   <span data-ttu-id="1adb5-109">持ち家所有。</span><span class="sxs-lookup"><span data-stu-id="1adb5-109">Owns a home.</span></span>  
  
-   <span data-ttu-id="1adb5-110">2 人の子供と同居。</span><span class="sxs-lookup"><span data-stu-id="1adb5-110">Has two children who still live at home.</span></span>  
  
 <span data-ttu-id="1adb5-111">これらの属性を顧客が購入する可能性とどのように関連付けることができるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="1adb5-111">How can you correlate these attributes with the likelihood that the customer will make a purchase?</span></span>  
  
 <span data-ttu-id="1adb5-112">購入行動を対象となる結果として使用してニューラル ネットワーク モデルを作成することにより、高所得などの顧客属性の複数の組み合わせを調べ、購入行動に影響する可能性が最も高い属性の組み合わせを検出できます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-112">By building a neural network model using purchasing behavior as the target outcome, you can explore multiple combinations on customer attributes, such as high income, and discover which combination of attributes is most likely to influence purchasing behavior.</span></span> <span data-ttu-id="1adb5-113">たとえば、決定要因が通勤距離であることを検出できます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-113">For example, you might discover that the determining factor is the distance that they commute to work.</span></span>  
  
 <span data-ttu-id="1adb5-114">検出された各パターンを表す式などの詳細情報をさらに表示する必要がある場合は、ビューを切り替えて [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-114">If you need to more view detailed information, such as the equations that represent each pattern that was discovered, you can switch views and use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="1adb5-115">詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](../microsoft-generic-content-tree-viewer-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1adb5-115">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="1adb5-116">ビューアーのタブ</span><span class="sxs-lookup"><span data-stu-id="1adb5-116">Viewer Tabs</span></span>  
 <span data-ttu-id="1adb5-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-117">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="1adb5-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク ビューアーには、ニューラル ネットワーク マイニング モデルを調べるための次のタブがあります。</span><span class="sxs-lookup"><span data-stu-id="1adb5-118">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer provides the following tabs for use in exploring neural network mining models:</span></span>  
  
-   [<span data-ttu-id="1adb5-119">入力</span><span class="sxs-lookup"><span data-stu-id="1adb5-119">Inputs</span></span>](#BKMK_Inputs)  
  
-   [<span data-ttu-id="1adb5-120">出力</span><span class="sxs-lookup"><span data-stu-id="1adb5-120">Outputs</span></span>](#BKMK_Outputs)  
  
-   [<span data-ttu-id="1adb5-121">変数</span><span class="sxs-lookup"><span data-stu-id="1adb5-121">Variables</span></span>](#BKMK_Characteristics)  
  
###  <a name="inputs"></a><a name="BKMK_Inputs"></a><span data-ttu-id="1adb5-122">Inputaccel</span><span class="sxs-lookup"><span data-stu-id="1adb5-122">Inputs</span></span>  
 <span data-ttu-id="1adb5-123">**[入力]** タブを使用して、モデルの入力として使用される属性と属性値を選択します。</span><span class="sxs-lookup"><span data-stu-id="1adb5-123">Use the **Inputs** tab to choose the attributes and values that the model used as inputs.</span></span> <span data-ttu-id="1adb5-124">既定では、ビューアーはすべての属性が含まれた状態で開きます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-124">By default, the viewer opens with all attributes included.</span></span> <span data-ttu-id="1adb5-125">この既定のビューでは、表示する最も重要な属性値がモデルによって選択されます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-125">In this default view, the model chooses which attribute values are the most important to display.</span></span>  
  
 <span data-ttu-id="1adb5-126">入力属性を選択するには、 **[入力]** グリッドの **[属性]** 列内をクリックし、一覧から属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="1adb5-126">To select an input attribute, click inside the **Attribute** column of the **Input** grid, and select an attribute from the drop-down list.</span></span> <span data-ttu-id="1adb5-127">(モデルに含まれている属性のみが一覧に表示されます)。</span><span class="sxs-lookup"><span data-stu-id="1adb5-127">(Only attributes that are included in the model are included in the list.)</span></span>  
  
 <span data-ttu-id="1adb5-128">**[値]** 列の下に、最初の個別の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-128">The first distinct value appears under the **Value** column.</span></span> <span data-ttu-id="1adb5-129">既定値をクリックすると、関連する属性で考えられるすべての状態が含まれた一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-129">Clicking the default value reveals a list that contains all the possible states of the associated attribute.</span></span> <span data-ttu-id="1adb5-130">調査する状態を選択できます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-130">You can select the state that you want to investigate.</span></span> <span data-ttu-id="1adb5-131">属性はいくつでも選択できます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-131">You can select as many attributes as you want.</span></span>  
  
 [<span data-ttu-id="1adb5-132">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="1adb5-132">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="outputs"></a><a name="BKMK_Outputs"></a><span data-ttu-id="1adb5-133">出力</span><span class="sxs-lookup"><span data-stu-id="1adb5-133">Outputs</span></span>  
 <span data-ttu-id="1adb5-134">**[出力]** タブを使用して、調査対象の結果属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="1adb5-134">Use the **Outputs** tab to choose the outcome attribute to investigate.</span></span> <span data-ttu-id="1adb5-135">モデルの作成時に列が予測可能な属性として定義されたことを前提として、比較する 2 つの結果状態を選択できます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-135">You can choose any two outcome states to compare, assuming the columns were defined as predictable attributes when the model was created.</span></span>  
  
 <span data-ttu-id="1adb5-136">**[出力属性]** 一覧を使用して、属性を選びます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-136">Use the **OutputAttribute** list to select an attribute.</span></span> <span data-ttu-id="1adb5-137">**[値 1]** 一覧と **[値 2]** 一覧から、属性に関連付けられている 2 つの状態を選択できます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-137">You can then select two states that are associated with the attribute from the **Value 1** and **Value 2** lists.</span></span> <span data-ttu-id="1adb5-138">出力属性のこれらの 2 つの状態は、 **[変数]** ペインで比較されます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-138">These two states of the output attribute will be compared in the **Variables** pane.</span></span>  
  
 [<span data-ttu-id="1adb5-139">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="1adb5-139">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="variables"></a><a name="BKMK_Characteristics"></a><span data-ttu-id="1adb5-140">環境</span><span class="sxs-lookup"><span data-stu-id="1adb5-140">Variables</span></span>  
 <span data-ttu-id="1adb5-141">**[変数]** タブのグリッドには、 **[属性]**、 **[値]**、 **[[値 1] を優先]**、および **[[値 2] を優先]** という列があります。</span><span class="sxs-lookup"><span data-stu-id="1adb5-141">The grid in the **Variables** tab contains the following columns: **Attribute**, **Value**, **Favors [value 1]**, and **Favors [value 2]**.</span></span> <span data-ttu-id="1adb5-142">既定では、列は **[[値 1] を優先]** の強度によって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-142">By default, the columns are sorted by the strength of **Favors [value 1]**.</span></span> <span data-ttu-id="1adb5-143">列見出しをクリックすると、並べ替え順が選択した列に変わります。</span><span class="sxs-lookup"><span data-stu-id="1adb5-143">Clicking a column heading changes the sort order to the selected column.</span></span>  
  
 <span data-ttu-id="1adb5-144">属性の右側のバーには、指定した入力属性の状態によって優先される出力属性の状態が示されます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-144">A bar to the right of the attribute shows which state of the output attribute the specified input attribute state favors.</span></span> <span data-ttu-id="1adb5-145">バーのサイズで、出力の状態によって入力の状態が優先される強度が示されます。</span><span class="sxs-lookup"><span data-stu-id="1adb5-145">The size of the bar shows how strongly the output state favors the input state.</span></span>  
  
 [<span data-ttu-id="1adb5-146">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="1adb5-146">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="1adb5-147">参照</span><span class="sxs-lookup"><span data-stu-id="1adb5-147">See Also</span></span>  
 <span data-ttu-id="1adb5-148">[Microsoft ニューラルネットワークアルゴリズム](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="1adb5-148">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="1adb5-149">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="1adb5-149">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="1adb5-150">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="1adb5-150">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="1adb5-151">[データマイニングツール](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1adb5-151">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="1adb5-152">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="1adb5-152">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
