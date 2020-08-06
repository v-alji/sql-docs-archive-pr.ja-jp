---
title: Microsoft アソシエーションルールビューアーを使用したモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- mining models [Analysis Services], associations
- mining model content, viewing
- rules [Data Mining]
- Association Rules Viewer [Analysis Services]
- market basket analysis [Analysis Services]
- associations [Analysis Services]
- Microsoft Association Rules Viewer
- dependencies [Analysis Services]
ms.assetid: 538fc01b-8eb1-467a-9b66-3cd57cf7489f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75bcefde30cb81cc00d8ad971756c68dedf670ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645289"
---
# <a name="browse-a-model-using-the-microsoft-association-rules-viewer"></a><span data-ttu-id="d93b6-102">Microsoft アソシエーション ルール ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="d93b6-102">Browse a Model Using the Microsoft Association Rules Viewer</span></span>
  <span data-ttu-id="d93b6-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]のアソシエーションルールビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] アソシエーションアルゴリズムを使用して作成されたマイニングモデルが表示され [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm.</span></span> <span data-ttu-id="d93b6-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムは、マーケット バスケット分析に使用できるデータ マイニング モデルを作成するときに使用するアソシエーション アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="d93b6-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm is an association algorithm for use in creating data mining models that you can use for market basket analysis.</span></span> <span data-ttu-id="d93b6-105">このアルゴリズムの詳細については、「 [Microsoft Association Algorithm](microsoft-association-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93b6-105">For more information about this algorithm, see [Microsoft Association Algorithm](microsoft-association-algorithm.md).</span></span>  
  
 <span data-ttu-id="d93b6-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムを使用する主な理由は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d93b6-106">Following are the primary reasons for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm:</span></span>  
  
-   <span data-ttu-id="d93b6-107">トランザクション内で通常同時に検出されるアイテムについて説明するアイテムセットを検出する。</span><span class="sxs-lookup"><span data-stu-id="d93b6-107">To find itemsets that describe items that are typically found together in a transaction.</span></span>  
  
-   <span data-ttu-id="d93b6-108">既存のアイテムに基づいて、トランザクション内の他のアイテムの存在を予測するルールを発見する。</span><span class="sxs-lookup"><span data-stu-id="d93b6-108">To discover rules that predict the presence of other items in a transaction based on existing items.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d93b6-109">モデルで使用された式と、検出されたパターンの詳細情報を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d93b6-109">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="d93b6-110">詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](../microsoft-generic-content-tree-viewer-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93b6-110">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
 <span data-ttu-id="d93b6-111">アソシエーション マイニング モデルの作成、調査、使用のチュートリアルについては、「[Lesson 3: Building a Market Basket Scenario (Intermediate Data Mining Tutorial)](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)」(レッスン 3 : マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93b6-111">For a walkthrough of how to create, explore, and use an association mining model, see [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="d93b6-112">ビューアーのタブ</span><span class="sxs-lookup"><span data-stu-id="d93b6-112">Viewer Tabs</span></span>  
 <span data-ttu-id="d93b6-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-113">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="d93b6-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール ビューアーには、次のタブがあります。</span><span class="sxs-lookup"><span data-stu-id="d93b6-114">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer includes the following tabs:</span></span>  
  
-   [<span data-ttu-id="d93b6-115">アイテムセット</span><span class="sxs-lookup"><span data-stu-id="d93b6-115">Itemsets</span></span>](#BKMK_Itemsets)  
  
-   [<span data-ttu-id="d93b6-116">ルール</span><span class="sxs-lookup"><span data-stu-id="d93b6-116">Rules</span></span>](#BKMK_Rules)  
  
-   [<span data-ttu-id="d93b6-117">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="d93b6-117">Dependency Net</span></span>](#BKMK_Dependency)  
  
 <span data-ttu-id="d93b6-118">各タブには **[長い名前を表示する]** チェック ボックスがあります。このチェック ボックスを使用して、ルールまたはアイテムセットでアイテムセットの元のテーブルを表示するか非表示にするかを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-118">Each tab contains the **Show long name** check box, which you can use to show or hide the table from which the itemset originates in the rule or itemset.</span></span>  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a><span data-ttu-id="d93b6-119">アイテムセット</span><span class="sxs-lookup"><span data-stu-id="d93b6-119">Itemsets</span></span>  
 <span data-ttu-id="d93b6-120">**[アイテムセット]** タブには、同時に検出されることが多いとモデルで判断されたアイテムセットの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-120">The **Itemsets** tab displays the list of itemsets that the model identified as frequently found together.</span></span> <span data-ttu-id="d93b6-121">このタブには、 **[サポート]**、 **[サイズ]**、および **[アイテムセット]** 列を持つグリッドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-121">The tab displays a grid with the following columns: **Support**, **Size**, and **Itemset**.</span></span> <span data-ttu-id="d93b6-122">サポートの詳細については、「 [Microsoft Association Algorithm](microsoft-association-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93b6-122">For more information about support, see [Microsoft Association Algorithm](microsoft-association-algorithm.md).</span></span> <span data-ttu-id="d93b6-123">**[サイズ]** 列には、アイテムセット内のアイテム数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-123">The **Size** column displays the number of items in the itemset.</span></span> <span data-ttu-id="d93b6-124">**[アイテムセット]** 列には、モデルで検出された実際のアイテムセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-124">The **Itemset** column displays the actual itemset that the model discovered.</span></span> <span data-ttu-id="d93b6-125">**[表示]** の一覧を使用してアイテムセットの形式を指定できます。この一覧では、次のオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-125">You can control the format of the itemset by using the **Show** list, which you can set to the following options:</span></span>  
  
-   <span data-ttu-id="d93b6-126">**[属性の名前と値を表示]**</span><span class="sxs-lookup"><span data-stu-id="d93b6-126">**Show attribute name and value**</span></span>  
  
-   <span data-ttu-id="d93b6-127">**[属性値のみ表示]**</span><span class="sxs-lookup"><span data-stu-id="d93b6-127">**Show attribute value only**</span></span>  
  
-   <span data-ttu-id="d93b6-128">**[属性名のみ表示]**</span><span class="sxs-lookup"><span data-stu-id="d93b6-128">**Show attribute name only**</span></span>  
  
 <span data-ttu-id="d93b6-129">**[最小のサポート]** および **[最小のアイテムセットのサイズ]** を使用して、タブに表示されるアイテムセットの数をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-129">You can filter the number of itemsets that are displayed in the tab by using **Minimum support** and **Minimum itemset size**.</span></span> <span data-ttu-id="d93b6-130">さらに、 **[アイテムセットのフィルター]** を使用し、残す必要のあるアイテムセットの特性を入力して、表示されるアイテムセットの数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-130">You can limit the number of displayed itemsets even more by using **Filter Itemset** and entering an itemset characteristic that must exist.</span></span> <span data-ttu-id="d93b6-131">たとえば、「Water Bottle = existing」と入力すると、アイテムセットを water bottle が含まれているもののみに限定できます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-131">For example, if you type "Water Bottle = existing", you can limit the itemsets to only those that contain a water bottle.</span></span> <span data-ttu-id="d93b6-132">**[アイテムセットのフィルター]** オプションでは、以前に使用したフィルターの一覧も表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-132">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
 <span data-ttu-id="d93b6-133">列見出しをクリックすると、グリッド内の行を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-133">You can sort the rows in the grid by clicking a column heading.</span></span>  
  
 [<span data-ttu-id="d93b6-134">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="d93b6-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a><span data-ttu-id="d93b6-135">ロジック</span><span class="sxs-lookup"><span data-stu-id="d93b6-135">Rules</span></span>  
 <span data-ttu-id="d93b6-136">**[ルール]** タブには、アソシエーション アルゴリズムで発見されたルールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-136">The **Rules** tab displays the rules that the association algorithm discovered.</span></span> <span data-ttu-id="d93b6-137">**[ルール]** タブには、 **[確率]** 列、 **[重要度]** 列、および **[ルール]** 列で構成されたグリッドがあります。</span><span class="sxs-lookup"><span data-stu-id="d93b6-137">The **Rules** tab includes a grid that contains the following columns: **Probability**, **Importance**, and **Rule**.</span></span> <span data-ttu-id="d93b6-138">確率は、ルールの結果が発生する可能性を示します。</span><span class="sxs-lookup"><span data-stu-id="d93b6-138">The probability describes how likely the result of a rule is to occur.</span></span> <span data-ttu-id="d93b6-139">重要度では、ルールの有用性が測定されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-139">The importance is designed to measure the usefulness of a rule.</span></span> <span data-ttu-id="d93b6-140">ルールが発生する確率が高くても、ルールの有用性自体は低い場合があります。</span><span class="sxs-lookup"><span data-stu-id="d93b6-140">Although the probability that a rule will occur may be high, the usefulness of the rule may in itself be unimportant.</span></span> <span data-ttu-id="d93b6-141">[重要度] 列は、これに対処しています。</span><span class="sxs-lookup"><span data-stu-id="d93b6-141">The importance column addresses this.</span></span> <span data-ttu-id="d93b6-142">たとえば、すべてのアイテムセットに特定の状態の属性が含まれている場合、確率が非常に高くても、状態を予測するルールはあまり意味がありません。</span><span class="sxs-lookup"><span data-stu-id="d93b6-142">For example, if every itemset contains a specific state of an attribute, a rule that predicts state is trivial, even though the probability is very high.</span></span> <span data-ttu-id="d93b6-143">重要度が高いほど、ルールはより重要になります。</span><span class="sxs-lookup"><span data-stu-id="d93b6-143">The greater the importance, the more important the rule is.</span></span>  
  
 <span data-ttu-id="d93b6-144">[**アイテムセット**] タブで行うことができるフィルター処理と同様に、[**最小の確率**] と [**最小の重要度**] を使用してルールをフィルター処理できます。**フィルタールール**を使用して、含まれている属性の状態に基づいてルールをフィルター処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-144">You can use **Minimum probability** and **Minimum importance** to filter the rules, similar to the filtering you can do on the **Itemsets** tab. You can also use **Filter Rule** to filter a rule based on the states of the attributes that it contains.</span></span>  
  
 <span data-ttu-id="d93b6-145">列見出しをクリックすると、グリッド内の行を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-145">You can sort the rows in the grid by clicking a column heading.</span></span>  
  
 [<span data-ttu-id="d93b6-146">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="d93b6-146">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="dependency-net"></a><a name="BKMK_Dependency"></a><span data-ttu-id="d93b6-147">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="d93b6-147">Dependency Net</span></span>  
 <span data-ttu-id="d93b6-148">**[依存関係ネットワーク]** タブには依存関係ネットワーク ビューアーがあります。</span><span class="sxs-lookup"><span data-stu-id="d93b6-148">The **Dependency Net** tab includes a dependency network viewer.</span></span> <span data-ttu-id="d93b6-149">ビューアーの各ノードは、"state = WA" などのアイテムを表します。</span><span class="sxs-lookup"><span data-stu-id="d93b6-149">Each node in the viewer represents an item, such as "state = WA".</span></span> <span data-ttu-id="d93b6-150">ノード間の矢印は、アイテム間の関連を表します。</span><span class="sxs-lookup"><span data-stu-id="d93b6-150">The arrow between nodes represents the association between items.</span></span> <span data-ttu-id="d93b6-151">矢印の方向は、アルゴリズムが発見したルールに従ってアイテム間の関連を示します。</span><span class="sxs-lookup"><span data-stu-id="d93b6-151">The direction of the arrow dictates the association between the items according to the rules that the algorithm discovered.</span></span> <span data-ttu-id="d93b6-152">たとえば、ビューアーに A、B、C という3つの項目が含まれており、C が A と B によって予測されている場合、ノード C を選択すると、ノード C-A から C、B から C に向かう2つの矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-152">For example, if the viewer contains three items, A, B, and C, and C is predicted by A and B, if you select node C, two arrows point toward node C - A to C and B to C.</span></span>  
  
 <span data-ttu-id="d93b6-153">ビューアーの左側にあるスライダーは、ルールの確率に関連付けられたフィルターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="d93b6-153">The slider at the left of the viewer acts as a filter that is tied to the probability of the rules.</span></span> <span data-ttu-id="d93b6-154">スライダーを小さく設定すると、緊密なリンクのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-154">Lowering the slider shows only the strongest links.</span></span>  
  
 [<span data-ttu-id="d93b6-155">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="d93b6-155">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="d93b6-156">参照</span><span class="sxs-lookup"><span data-stu-id="d93b6-156">See Also</span></span>  
 <span data-ttu-id="d93b6-157">[Microsoft アソシエーションアルゴリズム](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="d93b6-157">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="d93b6-158">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="d93b6-158">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="d93b6-159">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="d93b6-159">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="d93b6-160">[データマイニングツール](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d93b6-160">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="d93b6-161">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="d93b6-161">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
