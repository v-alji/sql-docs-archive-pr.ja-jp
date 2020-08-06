---
title: '[ルール] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.rules.f1
ms.assetid: 705d5492-b58f-45d9-94d7-ed57b7025823
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0d86931865fd9352074669de93b14dacfc84537
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633383"
---
# <a name="rules-tab-mining-model-viewer"></a><span data-ttu-id="8cd0b-102">[ルール] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="8cd0b-102">Rules Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="8cd0b-103">アルゴリズムによってデータから抽出されたルールを表示するには、関連モデルの **[ルール]** ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-103">Use the **Rules** pane in an association model to view the rules that the algorithm extracted from the data.</span></span> <span data-ttu-id="8cd0b-104">ルールは、アイテムが互いにどのように関連しているのかを記述し、推奨を作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-104">Rules describe how items are related to each other, and can be used to create recommendations.</span></span>  
  
 <span data-ttu-id="8cd0b-105">ビューアーでオプションを使用して、ビューアーに表示されるルールの数をフィルタリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-105">You can use the options in the viewer to filter the number of rules that are displayed in the viewer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8cd0b-106">既定では、 **[最小の確率]** に定義された確率のしきい値を上回るルールだけがビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-106">By default, only the rules that are above the probability threshold defined in **Minimum probability** are displayed in the viewer.</span></span> <span data-ttu-id="8cd0b-107">ルールの出力に対する確率のしきい値はモデルの作成時に決定されるので、ビューアーでこの値を小さくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-107">You cannot make this value any smaller by using the viewer, because the probability threshold for rule output is determined when the model is created.</span></span> <span data-ttu-id="8cd0b-108">詳細については、「 [Microsoft アソシエーション アルゴリズム テクニカル リファレンス](data-mining/microsoft-association-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-108">For more information, see [Microsoft Association Algorithm Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="8cd0b-109">**詳細:** [Microsoft アソシエーション アルゴリズムム](data-mining/microsoft-association-algorithm.md)、 [Microsoft アソシエーション ルール ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="8cd0b-109">**For More Information:** [Microsoft Association Algorithm](data-mining/microsoft-association-algorithm.md), [Browse a Model Using the Microsoft Association Rules Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="8cd0b-110">Options</span><span class="sxs-lookup"><span data-stu-id="8cd0b-110">Options</span></span>  
 <span data-ttu-id="8cd0b-111">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-111">**Refresh viewer content**</span></span>  
 <span data-ttu-id="8cd0b-112">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-112">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="8cd0b-113">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-113">**Mining Model**</span></span>  
 <span data-ttu-id="8cd0b-114">現在のマイニング構造に含まれているマイニング モデルから、表示するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-114">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="8cd0b-115">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-115">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="8cd0b-116">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-116">**Viewer**</span></span>  
 <span data-ttu-id="8cd0b-117">選択したマイニング モデルを表示するために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-117">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="8cd0b-118">各マイニング モデル用のカスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー ビューアー**を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-118">You can use the custom viewer for each mining model, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="8cd0b-119">利用可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-119">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="8cd0b-120">**[最小の確率]**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-120">**Minimum probability**</span></span>  
 <span data-ttu-id="8cd0b-121">ビューアーにルールを表示するために必要な最小の確率を設定するには、この値を変更します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-121">Change this value to set the minimum probability required for a rule to be displayed in the viewer.</span></span> <span data-ttu-id="8cd0b-122">確率の値を大きくすると、表示されるルールの数が減ります。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-122">Increasing the value for probability will reduce the number of rules that are displayed.</span></span>  
  
 <span data-ttu-id="8cd0b-123">**[最小の重要度]**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-123">**Minimum importance**</span></span>  
 <span data-ttu-id="8cd0b-124">ビューアーにルールを表示するために必要な最小の重要度を設定するには、この値を変更します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-124">Change this value to set the minimum importance required for a rule to be displayed in the viewer.</span></span> <span data-ttu-id="8cd0b-125">重要度の値を大きくすると、表示されるルールの数が減ります。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-125">Increasing the value for importance will reduce the number of rules that are displayed.</span></span>  
  
 <span data-ttu-id="8cd0b-126">**[ルールのフィルター]**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-126">**Filter Rule**</span></span>  
 <span data-ttu-id="8cd0b-127">ビューアーに表示するルールの数をフィルタリングするための文字列値を入力します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-127">Type a string value to filter the number of rules that appear in the viewer.</span></span>  
  
 <span data-ttu-id="8cd0b-128">フィルター条件として、.NET 正規表現を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-128">You can also type .NET regular expressions as filter criteria.</span></span> <span data-ttu-id="8cd0b-129">たとえば、次の式を入力すると、左辺に 'Road Bottle Cage' を含むすべてのルールが返されます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-129">For example, the following expression returns all rules that contain 'Road Bottle Cage' on the left side of the rule:</span></span>  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*->.*`  
  
 <span data-ttu-id="8cd0b-130">フィルター条件の適用結果を表示するには、更新が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-130">Note that you might need to refresh the view to see the filter criteria apply.</span></span> <span data-ttu-id="8cd0b-131">**[長い名前を表示する]** オプションのオンとオフを切り替えて、リストを更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-131">You can also toggle the **Show long name** option on and off to refresh the list.</span></span>  
  
 <span data-ttu-id="8cd0b-132">既定では、フィルター条件は属性のフルネームと値の組み合わせに適用されます。したがって、属性名だけを表示している場合は、フィルター条件が適切に適用されたかどうかはっきりしないことがあります。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-132">By default the filter criteria applies to the full name of the attribute-value combination; therefore, if you are viewing the attribute name only, it might not be obvious that the filter criteria has applied correctly.</span></span> <span data-ttu-id="8cd0b-133">**[表示]** ボックスの一覧の **[属性の名前と値を表示]** をクリックして、アイテムセットの一覧が適切にフィルター処理されたことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-133">Use the **Show** dropdown list to select **Show attribute name and value**, and verify that the list of itemsets is filtered correctly.</span></span>  
  
 <span data-ttu-id="8cd0b-134">**表示**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-134">**Show**</span></span>  
 <span data-ttu-id="8cd0b-135">ビューアーにルールを表示する方法を調整します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-135">Adjust the way that the rule is displayed in the viewer.</span></span> <span data-ttu-id="8cd0b-136">次の 3 つのオプションのいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-136">You can select one of the three following options:</span></span>  
  
-   <span data-ttu-id="8cd0b-137">[属性の名前と値を表示]</span><span class="sxs-lookup"><span data-stu-id="8cd0b-137">Show the attribute name and value</span></span>  
  
-   <span data-ttu-id="8cd0b-138">[属性値のみ表示]</span><span class="sxs-lookup"><span data-stu-id="8cd0b-138">Show the attribute value only</span></span>  
  
-   <span data-ttu-id="8cd0b-139">[属性名のみ表示]</span><span class="sxs-lookup"><span data-stu-id="8cd0b-139">Show the attribute name only</span></span>  
  
 <span data-ttu-id="8cd0b-140">**[長い名前を表示する]**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-140">**Show long name**</span></span>  
 <span data-ttu-id="8cd0b-141">マイニング モデル コンテンツに表示されるルールのフル ネームを表示します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-141">Show the full name of the rule as it appears in the mining model content.</span></span>  
  
 <span data-ttu-id="8cd0b-142">**[最大行数]**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-142">**Maximum rows**</span></span>  
 <span data-ttu-id="8cd0b-143">ビューアーに表示するルールの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-143">Limit the number of rules that are displayed in the viewer.</span></span>  
  
 <span data-ttu-id="8cd0b-144">**確率**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-144">**Probability**</span></span>  
 <span data-ttu-id="8cd0b-145">グラフのこの列には、各ルールの確率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-145">This column in the chart displays the probability for each rule.</span></span>  
  
 <span data-ttu-id="8cd0b-146">列見出しをクリックすることで、確率順に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-146">You can click the column heading to sort by probability.</span></span>  
  
 <span data-ttu-id="8cd0b-147">**重要度**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-147">**Importance**</span></span>  
 <span data-ttu-id="8cd0b-148">グラフのこの列には、各ルールの重要度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-148">This column in the chart displays the importance for each rule.</span></span>  
  
 <span data-ttu-id="8cd0b-149">列見出しをクリックすることで、重要度順に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-149">You can click the column heading to sort by importance.</span></span>  
  
 <span data-ttu-id="8cd0b-150">**Rule**</span><span class="sxs-lookup"><span data-stu-id="8cd0b-150">**Rule**</span></span>  
 <span data-ttu-id="8cd0b-151">グラフのこの列には、 **[表示]** オプションと **[長い名前を表示する]** オプションを使用して指定した書式に応じて、各ルールの説明テキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-151">This column in the chart displays the text description for each rule, according to the format specified by using the options, **Show** and **Show long name**.</span></span>  
  
 <span data-ttu-id="8cd0b-152">列見出しをクリックすることで、ルールのテキストで並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8cd0b-152">You can click the column heading to sort by the text of the rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd0b-153">参照</span><span class="sxs-lookup"><span data-stu-id="8cd0b-153">See Also</span></span>  
 <span data-ttu-id="8cd0b-154">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8cd0b-154">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8cd0b-155">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="8cd0b-155">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="8cd0b-156">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="8cd0b-156">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
