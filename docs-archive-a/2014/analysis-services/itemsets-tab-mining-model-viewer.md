---
title: '[アイテムセット] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.itemsets.f1
ms.assetid: 95b2b805-b142-4064-9c80-4b1b3fe2fe63
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b99b62b01b196fd62e1ef264e530487018f6a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633417"
---
# <a name="itemsets-tab-mining-model-viewer"></a><span data-ttu-id="d7f25-102">[アイテムセット] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="d7f25-102">Itemsets Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="d7f25-103">**[アイテムセット]** ペインを使用すると、アソシエーション ルール マイニング モデルに含まれる、よく使用されるアイテムセットを表示できます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-103">You can use the **Itemsets** pane to view the frequent itemsets that an association rules mining model contains.</span></span> <span data-ttu-id="d7f25-104">アソシエーション モデルには多数のアイテムセットが含まれる可能性があるので、ビューアーには、ビューアーに表示するアイテムセットを絞り込むためのコントロールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d7f25-104">Because an association model can contain many itemsets, controls are provided in the viewer to help you filter the itemsets that are displayed in the viewer.</span></span>  
  
 <span data-ttu-id="d7f25-105">**詳細:** [Microsoft アソシエーション アルゴリズムム](data-mining/microsoft-association-algorithm.md)、 [Microsoft アソシエーション ルール ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="d7f25-105">**For More Information:** [Microsoft Association Algorithm](data-mining/microsoft-association-algorithm.md), [Browse a Model Using the Microsoft Association Rules Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="d7f25-106">Options</span><span class="sxs-lookup"><span data-stu-id="d7f25-106">Options</span></span>  
 <span data-ttu-id="d7f25-107">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="d7f25-108">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="d7f25-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="d7f25-109">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-109">**Mining Model**</span></span>  
 <span data-ttu-id="d7f25-110">現在のマイニング構造に含まれているマイニング モデルから、表示するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-110">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="d7f25-111">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="d7f25-112">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="d7f25-112">**Viewer**</span></span>  
 <span data-ttu-id="d7f25-113">選択したマイニング モデルを表示するために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-113">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="d7f25-114">アソシエーション モデル用のカスタム ビューアーまたは [!INCLUDE[msCoName](../includes/msconame-md.md)] Microsoft 汎用コンテンツ ツリー ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-114">You can use either the custom viewer for association models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="d7f25-115">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="d7f25-116">**[最小のサポート]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-116">**Minimum support**</span></span>  
 <span data-ttu-id="d7f25-117">アイテムセットをビューアーに表示するために必要な最小のサポートを設定するには、この値を変更します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-117">Change this value to set the minimum support that an itemset must contain to appear in the viewer.</span></span> <span data-ttu-id="d7f25-118">モデルを初めて開いたときに表示される既定値はモデルによって計算されますが、値を変更することで、表示するアイテムセットの数を増減できます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-118">The default value that is displayed when you first open the model is calculated by the model, but you can change it to see more or fewer itemsets.</span></span>  
  
 <span data-ttu-id="d7f25-119">**[最小のアイテムセットのサイズ]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-119">**Minimum itemset size**</span></span>  
 <span data-ttu-id="d7f25-120">アイテムセットをビューアーに表示するために必要なアイテムの最小数を設定するには、この値を変更します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-120">Change this value to set the minimum number of items that must be included in an itemset before the itemset can be displayed in the viewer.</span></span>  
  
 <span data-ttu-id="d7f25-121">**[アイテムセットのフィルター]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-121">**Filter Itemset**</span></span>  
 <span data-ttu-id="d7f25-122">ビューアーに表示するアイテムセットの数を絞り込むための文字列値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-122">Type a string value to filter the number of itemsets that appear in the viewer.</span></span>  
  
 <span data-ttu-id="d7f25-123">フィルター条件として、.NET 正規表現を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-123">You can also type .NET regular expressions as filter criteria.</span></span> <span data-ttu-id="d7f25-124">たとえば、次の式を入力すると、'Road Bottle Cage' を含むすべてのアイテムセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-124">For example, the following expression returns all itemsets that contain 'Road Bottle Cage':</span></span>  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*`  
  
 <span data-ttu-id="d7f25-125">フィルター条件の適用結果を表示するには、更新が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="d7f25-125">Note that you might need to refresh the view to see the filter criteria apply.</span></span> <span data-ttu-id="d7f25-126">**[長い名前を表示する]** オプションのオンとオフを切り替えて、リストを更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-126">You can also toggle the **Show long name** option on and off to refresh the list.</span></span>  
  
 <span data-ttu-id="d7f25-127">既定では、フィルター条件は属性のフルネームと値の組み合わせに適用されます。したがって、属性名だけを表示している場合は、フィルター条件が適切に適用されたかどうかはっきりしないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d7f25-127">By default the filter criteria applies to the full name of the attribute-value combination; therefore, if you are viewing the attribute name only, it might not be obvious that the filter criteria has applied correctly.</span></span> <span data-ttu-id="d7f25-128">**[表示]** ボックスの一覧の **[属性の名前と値を表示]** をクリックして、アイテムセットの一覧が適切にフィルター処理されたことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d7f25-128">Use the **Show** dropdown list to select **Show attribute name and value**, and verify that the list of itemsets is filtered correctly.</span></span>  
  
 <span data-ttu-id="d7f25-129">**表示**</span><span class="sxs-lookup"><span data-stu-id="d7f25-129">**Show**</span></span>  
 <span data-ttu-id="d7f25-130">アイテムセットをどのようにビューアーに表示するかを調整します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-130">Adjust how the itemset is displayed in the viewer.</span></span> <span data-ttu-id="d7f25-131">次の 3 つのオプションのいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-131">You can select one of the three following options:</span></span>  
  
-   <span data-ttu-id="d7f25-132">[属性の名前と値を表示]</span><span class="sxs-lookup"><span data-stu-id="d7f25-132">Show attribute name and value</span></span>  
  
-   <span data-ttu-id="d7f25-133">[属性値のみ表示]</span><span class="sxs-lookup"><span data-stu-id="d7f25-133">Show attribute value only</span></span>  
  
-   <span data-ttu-id="d7f25-134">[属性名のみ表示]</span><span class="sxs-lookup"><span data-stu-id="d7f25-134">Show attribute name only</span></span>  
  
 <span data-ttu-id="d7f25-135">このオプションはモデルのクエリを再実行しません。表示される属性または値を絞り込むだけです。</span><span class="sxs-lookup"><span data-stu-id="d7f25-135">Note that this option does not requery the model; it only filters the attributes or values that are displayed.</span></span>  
  
 <span data-ttu-id="d7f25-136">**[長い名前を表示する]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-136">**Show long name**</span></span>  
 <span data-ttu-id="d7f25-137">マイニング モデルの内容に含まれるアイテムセットのフルネームを表示するには、このオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-137">Select this option to display the full name of the itemset as it appears in the mining model content.</span></span>  
  
 <span data-ttu-id="d7f25-138">**[最大行数]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-138">**Maximum rows**</span></span>  
 <span data-ttu-id="d7f25-139">ビューアーに表示されるアイテムセットの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-139">Limit the number of itemsets that are displayed in the viewer.</span></span> <span data-ttu-id="d7f25-140">既定では、アイテムセットはサポートの降順に表示されるので、この値を小さくすると、最も一般的なアイテムセットだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-140">By default, itemsets are ordered by support in descending order, so lowering this value restricts the list to the most common itemsets.</span></span>  
  
 <span data-ttu-id="d7f25-141">**サポート**</span><span class="sxs-lookup"><span data-stu-id="d7f25-141">**Support**</span></span>  
 <span data-ttu-id="d7f25-142">各アイテムセットのサポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-142">Displays the support for each itemset.</span></span>  
  
 <span data-ttu-id="d7f25-143">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-143">**Size**</span></span>  
 <span data-ttu-id="d7f25-144">各アイテムセットに存在するアイテムの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-144">Displays the number of items that exist in each itemset.</span></span>  
  
 <span data-ttu-id="d7f25-145">**[アイテムセット]**</span><span class="sxs-lookup"><span data-stu-id="d7f25-145">**Itemset**</span></span>  
 <span data-ttu-id="d7f25-146">各アイテムセットの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="d7f25-146">Displays the description of each itemset.</span></span> <span data-ttu-id="d7f25-147">既定では、アイテムセットは、属性とその値のコンマ区切りの一覧として表されます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-147">By default, itemsets are presented as a comma-delimited list of attributes and their values.</span></span> <span data-ttu-id="d7f25-148">**[表示]** オプションを使用して、表示方法を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d7f25-148">You can change the way they are displayed by using the **Show** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f25-149">参照</span><span class="sxs-lookup"><span data-stu-id="d7f25-149">See Also</span></span>  
 <span data-ttu-id="d7f25-150">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d7f25-150">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="d7f25-151">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="d7f25-151">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="d7f25-152">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="d7f25-152">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
