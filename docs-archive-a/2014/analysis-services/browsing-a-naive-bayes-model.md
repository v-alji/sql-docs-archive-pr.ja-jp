---
title: Naive Bayes Model | の参照Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3b0d18cd74e71f1ef18bffd6b0998e0b326e887a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633567"
---
# <a name="browsing-a-naive-bayes-model"></a><span data-ttu-id="623e0-102">Naive Bayes モデルの参照</span><span class="sxs-lookup"><span data-stu-id="623e0-102">Browsing a Naive Bayes Model</span></span>
  <span data-ttu-id="623e0-103">**参照**を使用して単純な Bayes モデルを開くと、4つの異なるペインを含む対話型ビューアーにモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="623e0-103">When you open a Naïve Bayes model using **Browse**, the model is displayed in an interactive viewer with four different panes.</span></span> <span data-ttu-id="623e0-104">ビューアーを使用して、相関関係を調査し、モデルと基になるデータに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="623e0-104">Use the viewer to explore correlations, and get information about the model and the underlying data.</span></span>  
  
-   [<span data-ttu-id="623e0-105">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="623e0-105">Dependency Network</span></span>](#bkmk_DepNet)  
  
-   [<span data-ttu-id="623e0-106">属性のプロファイル</span><span class="sxs-lookup"><span data-stu-id="623e0-106">Attribute Profiles</span></span>](#bkmk_AttProf)  
  
-   [<span data-ttu-id="623e0-107">属性の特性</span><span class="sxs-lookup"><span data-stu-id="623e0-107">Attribute Characteristics</span></span>](#bkmk_AttChar)  
  
-   [<span data-ttu-id="623e0-108">属性の識別</span><span class="sxs-lookup"><span data-stu-id="623e0-108">Attribute Discrimination</span></span>](#bkmk_AttDisc)  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="623e0-109">モデルの調査</span><span class="sxs-lookup"><span data-stu-id="623e0-109">Explore the Model</span></span>  
 <span data-ttu-id="623e0-110">ビューアーの目的は、[!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes モデルで検出された入力属性と出力属性 (入力と従属変数) の相互作用を調査することです。</span><span class="sxs-lookup"><span data-stu-id="623e0-110">The purpose of the viewer is to help you explore the interaction between input and output attributes (inputs and dependent variables) that were discovered by the [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes model.</span></span>  
  
 <span data-ttu-id="623e0-111">単純な Bayes ビューアーを試してみる場合は、[データマイニング] リボンの [ [Excel 用データマイニングアドインの &#40;データマイニングアドイン]&#41;](classify-wizard-data-mining-add-ins-for-excel.md)ウィザードを使用して、[**詳細設定**] オプションをクリックし、単純な Bayes アルゴリズムを使用するようにアルゴリズムを変更します。</span><span class="sxs-lookup"><span data-stu-id="623e0-111">If you want to experiment with the Naïve Bayes viewer, use the [Classify Wizard &#40;Data Mining Add-ins for Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) wizard in the Data Mining ribbon, click the **Advanced** option, and change the algorithm to use the Naïve Bayes algorithm</span></span>  
  
 <span data-ttu-id="623e0-112">これらの例では、サンプルブックのソースデータを使用して、**年収**の列を、**非常に低い**から**非常に高い**5 つの収入グループにグループ化しています。</span><span class="sxs-lookup"><span data-stu-id="623e0-112">For these examples, we used the Source data in the sample workbook, and grouped the column, **Yearly Income**, into five income groups, from **Very Low** to **Very High**.</span></span> <span data-ttu-id="623e0-113">その後、Naïve Bayes モデルを使って、各収入カテゴリと相関関係を持つ要因を分析しました。</span><span class="sxs-lookup"><span data-stu-id="623e0-113">The Naïve Bayes model then analyzed the factors correlated with each income category.</span></span>  
  
###  <a name="dependency-network"></a><a name="bkmk_DepNet"></a><span data-ttu-id="623e0-114">依存関係ネットワーク</span><span class="sxs-lookup"><span data-stu-id="623e0-114">Dependency Network</span></span>  
 <span data-ttu-id="623e0-115">最初に使用するウィンドウは、**依存関係ネットワーク**です。</span><span class="sxs-lookup"><span data-stu-id="623e0-115">The first window you'll use is the **Dependency Network**.</span></span> <span data-ttu-id="623e0-116">どの入力が選択した結果と密接に関連しているかがひとめでわかります。</span><span class="sxs-lookup"><span data-stu-id="623e0-116">It shows you at a glance which inputs are closely correlated to the selected outcome.</span></span>  
  
 <span data-ttu-id="623e0-117">![Naive Bayes ビューアーに表示された依存関係ネットワーク](media/dm13-nb.gif "Naive Bayes ビューアーに表示された依存関係ネットワーク")</span><span class="sxs-lookup"><span data-stu-id="623e0-117">![dependency network in Naive Bayes viewer](media/dm13-nb.gif "dependency network in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-the-dependency-network"></a><span data-ttu-id="623e0-118">依存関係ネットワークの調査</span><span class="sxs-lookup"><span data-stu-id="623e0-118">Explore the dependency network</span></span>  
  
1.  <span data-ttu-id="623e0-119">最初に、目標の結果 (**年収**) をクリックします。これは、グラフのノードとして表されます。</span><span class="sxs-lookup"><span data-stu-id="623e0-119">First, click the target outcome, **Yearly Income**, which is represented as a node in the graph.</span></span>  
  
     <span data-ttu-id="623e0-120">目標の変数を囲む強調表示されたノードは、この結果と統計的に相関関係のあるノードです。</span><span class="sxs-lookup"><span data-stu-id="623e0-120">The highlighted nodes surrounding the target variable are those that are statistically correlated with this outcome.</span></span> <span data-ttu-id="623e0-121">関係の特性を理解するには、ビューアーの下部にある凡例を使用します。</span><span class="sxs-lookup"><span data-stu-id="623e0-121">Use the legend at the bottom of the viewer to understand the nature of the relationship.</span></span>  
  
2.  <span data-ttu-id="623e0-122">ビューアーの左側にあるスライダーをクリックして下へドラッグします。</span><span class="sxs-lookup"><span data-stu-id="623e0-122">Click the slider at the left of the viewer and drag it downward.</span></span>  
  
     <span data-ttu-id="623e0-123">このコントロールは、依存関係の強さに基づいて、独立変数をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="623e0-123">This control filters the independent variables, based on the strengths of the dependencies.</span></span> <span data-ttu-id="623e0-124">スライダーをドラッグして下げると、関係が最も強いリンクだけがグラフに表示されます。</span><span class="sxs-lookup"><span data-stu-id="623e0-124">When you drag the slider down, only the strongest links remain in the graph.</span></span>  
  
3.  <span data-ttu-id="623e0-125">グラフをフィルター処理した後、[**グラフビューのコピー**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="623e0-125">After you have filtered the graph, click the button, **Copy Graph View**.</span></span> <span data-ttu-id="623e0-126">Excel でワークシートを選択し、Ctrl キーを押しながら V キーを押します。</span><span class="sxs-lookup"><span data-stu-id="623e0-126">Then select a worksheet in Excel, and press Ctrl+V.</span></span>  
  
     <span data-ttu-id="623e0-127">これで、選択したビューが、フィルターと強調表示も含めて、コピーされます。</span><span class="sxs-lookup"><span data-stu-id="623e0-127">This option copies the view that you have selected, including filters and highlighting.</span></span>  
  
 [<span data-ttu-id="623e0-128">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="623e0-128">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-profiles"></a><a name="bkmk_AttProf"></a> <span data-ttu-id="623e0-129">属性のプロファイル</span><span class="sxs-lookup"><span data-stu-id="623e0-129">Attribute Profiles</span></span>  
 <span data-ttu-id="623e0-130">[**属性プロファイル**ウィンドウには、他のすべての変数が個々の結果にどのように関連しているかが視覚的に示されます。</span><span class="sxs-lookup"><span data-stu-id="623e0-130">The **Attribute Profiles** windows gives you a visual indication of how all other variables are related to the individual outcomes.</span></span>  
  
##### <a name="explore-the-profiles"></a><span data-ttu-id="623e0-131">プロファイルの調査</span><span class="sxs-lookup"><span data-stu-id="623e0-131">Explore the profiles</span></span>  
  
1.  <span data-ttu-id="623e0-132">結果を簡単に比較できるように、いくつかの値を非表示にするには、列見出しを別の列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="623e0-132">To hide some values so that you can more easily compare outcomes, click the column heading and drag it under another column.</span></span>  
  
     <span data-ttu-id="623e0-133">![Naive Bayes ビューアーに表示された属性のプロファイル](media/dm13-nb-attprof.gif "Naive Bayes ビューアーに表示された属性のプロファイル")</span><span class="sxs-lookup"><span data-stu-id="623e0-133">![attribute profiles in Naive Bayes viewer](media/dm13-nb-attprof.gif "attribute profiles in Naive Bayes viewer")</span></span>  
  
2.  <span data-ttu-id="623e0-134">任意のセルをクリックすると、[**マイニング凡例**] の値の分布が表示されます。</span><span class="sxs-lookup"><span data-stu-id="623e0-134">Click in any cell to view the distribution of values in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="623e0-135">異なる結果に関連付けられた属性は異なる表示になるため、地域別の収入の分布など、興味のある相関関係をすばやく見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="623e0-135">Because the attributes associated with different outcomes are displayed visually, it is easy to spot interesting correlations, such as how incomes are distributed by region.</span></span>  
  
3.  <span data-ttu-id="623e0-136">このビューの基になるデータを取得するには、[ **Excel にコピー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="623e0-136">To obtain the data underlying this view, click **Copy to Excel**.</span></span> <span data-ttu-id="623e0-137">個々の属性と結果との相関関係を示す新しいテーブルがワークシートに生成されます。</span><span class="sxs-lookup"><span data-stu-id="623e0-137">A table is generated in a new worksheet that shows the correlations among individual attributes and outcomes.</span></span> <span data-ttu-id="623e0-138">この Excel テーブルでは、簡単に列の非表示やフィルター処理ができます。</span><span class="sxs-lookup"><span data-stu-id="623e0-138">In this Excel table you can easily hide or filter columns.</span></span>  
  
 [<span data-ttu-id="623e0-139">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="623e0-139">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-characteristics"></a><a name="bkmk_AttChar"></a><span data-ttu-id="623e0-140">属性の特性</span><span class="sxs-lookup"><span data-stu-id="623e0-140">Attribute Characteristics</span></span>  
 <span data-ttu-id="623e0-141">**属性特性**ビューは、特定の結果変数および関与する要因の詳細な調査に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="623e0-141">The **Attribute Characteristics** view is useful for in-depth examination of a particular outcome variable and the contributing factors.</span></span>  
  
 <span data-ttu-id="623e0-142">![Naive Bayes ビューアーに表示された属性の特性](media/dm13-nb-viewer.gif "Naive Bayes ビューアーに表示された属性の特性")</span><span class="sxs-lookup"><span data-stu-id="623e0-142">![attribute characteristics in Naive Bayes viewer](media/dm13-nb-viewer.gif "attribute characteristics in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-the-attribute-characteristics"></a><span data-ttu-id="623e0-143">属性の特性の調査</span><span class="sxs-lookup"><span data-stu-id="623e0-143">Explore the attribute characteristics</span></span>  
  
1.  <span data-ttu-id="623e0-144">[**値**] をクリックし、**値**から項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="623e0-144">Click **Value** and select an item from the **Value**.</span></span>  
  
     <span data-ttu-id="623e0-145">目標の結果を選択すると、グラフが更新されて、その結果との関連性が最も強い要素が重要度順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="623e0-145">As you select a target outcome, the graph updates to show the factors that are most strongly associated with the outcome, sorted by importance.</span></span>  
  
     <span data-ttu-id="623e0-146">[ [&#40;テーブル分析ツール]&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)オプションを使用してモデルを作成する場合は、複数の予測可能な属性を持つモデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="623e0-146">Note that if you create a model using the [Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md) option, you can create models that have more than one predictable attribute.</span></span> <span data-ttu-id="623e0-147">ただし、データ マイニング アドインのその他のウィザードはすべて、予測可能な属性が 1 つに制限されています。</span><span class="sxs-lookup"><span data-stu-id="623e0-147">However, all other wizards in the Data Mining add-ins limit you to one predictable attribute.</span></span>  
  
2.  <span data-ttu-id="623e0-148">新しいワークシートにテーブルを作成するには、[ **Excel にコピー** ] をクリックします。これにより、選択したターゲットの結果に関連するすべての属性のスコアが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="623e0-148">Click **Copy to Excel** to create a table, in a new worksheet, listing the scores for all attributes that are related to the selected target outcome.</span></span>  
  
 [<span data-ttu-id="623e0-149">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="623e0-149">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-discrimination"></a><a name="bkmk_AttDisc"></a><span data-ttu-id="623e0-150">属性の識別</span><span class="sxs-lookup"><span data-stu-id="623e0-150">Attribute Discrimination</span></span>  
 <span data-ttu-id="623e0-151">**属性の識別**ビューは、2つの結果、または1つの結果と他のすべての結果を比較するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="623e0-151">The **Attribute Discrimination** view helps compare two outcomes, or one outcome vs. all other outcomes.</span></span>  
  
 <span data-ttu-id="623e0-152">![Naive Bayes ビューアーに表示された属性の識別](media/dm13-nb-attdisc.gif "Naive Bayes ビューアーに表示された属性の識別")</span><span class="sxs-lookup"><span data-stu-id="623e0-152">![attribute discrimination in Naive Bayes viewer](media/dm13-nb-attdisc.gif "attribute discrimination in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-attribute-discrimination"></a><span data-ttu-id="623e0-153">属性の識別の調査</span><span class="sxs-lookup"><span data-stu-id="623e0-153">Explore attribute discrimination</span></span>  
  
1.  <span data-ttu-id="623e0-154">比較する結果を選択するには、[**値 1** ] と [**値 2**] のコントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="623e0-154">Use the controls, **Value 1** and **Value 2**, to select the outcomes that you want to compare.</span></span>  
  
     <span data-ttu-id="623e0-155">たとえば、このモデルでは、低所得グループにいくつかの興味深い属性があったので、最初のドロップダウンリストで最も低い収入グループを選択し、2番目のドロップダウンリストで [**その他のすべての状態**] を選択しました。</span><span class="sxs-lookup"><span data-stu-id="623e0-155">For example, in this model there were some interesting attributes in the low income group, so we chose the lowest income group in the first dropdown list, and chose **All other states** in the second dropdown list.</span></span>  
  
     <span data-ttu-id="623e0-156">属性は、重要度順に並べ替えられます (重要度はトレーニング データに基づいて計算)。</span><span class="sxs-lookup"><span data-stu-id="623e0-156">The attributes are sorted by order of importance (calculated based on the training data).</span></span> <span data-ttu-id="623e0-157">したがって、職業が最も密接に収入との相関関係がある要因です (少なくともこの対象グループの場合)。</span><span class="sxs-lookup"><span data-stu-id="623e0-157">Therefore, occupation is the factor most closely correlated with income (for this target group, at least),</span></span>  
  
     <span data-ttu-id="623e0-158">正確な数値を表示するには、色分けされたバーをクリックし、[**マイニング凡例**] を表示します。</span><span class="sxs-lookup"><span data-stu-id="623e0-158">To see the exact figures, click the colored bar and view the **Mining Legend**.</span></span>  
  
2.  <span data-ttu-id="623e0-159">低収入は、ヨーロッパ地域とも相関関係があります。</span><span class="sxs-lookup"><span data-stu-id="623e0-159">Note that lower incomes are also correlated with the Europe region.</span></span>  
  
     <span data-ttu-id="623e0-160">Naïve Bayes モデルではドリルダウンはサポートされていません。ただし、この結果グループに関連付けられたケースを調査する場合は、クエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="623e0-160">The Naïve Bayes model does not support drilldown; however, if you wanted to investigate the cases associated with this outcome group, you could use a query.</span></span> <span data-ttu-id="623e0-161">この種類のモデルに対するクエリの詳細については、「 [Naive Bayes model のクエリ例](data-mining/naive-bayes-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="623e0-161">For information about queries on this type of model, see [Naive Bayes Model Query Examples](data-mining/naive-bayes-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="623e0-162">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="623e0-162">Back To Top</span></span>](#BKMK_Tabs)  
  
## <a name="see-also"></a><span data-ttu-id="623e0-163">参照</span><span class="sxs-lookup"><span data-stu-id="623e0-163">See Also</span></span>  
 [<span data-ttu-id="623e0-164">Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;</span><span class="sxs-lookup"><span data-stu-id="623e0-164">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
