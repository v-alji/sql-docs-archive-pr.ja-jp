---
title: ニューラルネットワークモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- mining model, neural network
- neural networks
- dependency network
ms.assetid: e4224cb7-115b-4889-ac07-03f096fb55fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab2673d5b1881f74c2bc146b084d2efc7b06d69b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633563"
---
# <a name="browsing-a-neural-network-model"></a><span data-ttu-id="8ee26-102">ニューラル ネットワーク モデルの参照</span><span class="sxs-lookup"><span data-stu-id="8ee26-102">Browsing a Neural Network Model</span></span>
  <span data-ttu-id="8ee26-103">**[参照]** を使用してニューラル ネットワークまたはロジスティック回帰モデルを開くと、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のニューラル ネットワーク モデル ビューアーに似た対話型ビューアーにモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-103">When you open a neural network or logistic regression model using **Browse**, the model is displayed in an interactive viewer, similar to the neural network model viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8ee26-104">ビューアーは、相関関係の調査、およびモデルと基になるデータのパターンに関する情報の取得に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-104">The viewer helps you explore correlations, and get information about the patterns in the model and the underlying data.</span></span>

##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="8ee26-105">モデルの調査</span><span class="sxs-lookup"><span data-stu-id="8ee26-105">Explore the Model</span></span>
 <span data-ttu-id="8ee26-106">[!INCLUDE[msCoName](../includes/msconame-md.md)] ニューラル ネットワークまたはロジスティック回帰アルゴリズムに基づいたモデルは、既知の入力と出力を接続したものとしてデータを分析するという点で似ています。</span><span class="sxs-lookup"><span data-stu-id="8ee26-106">Models that are based on [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network or Logistic Regression algorithms are similar in that they analyze data as a set of connections among known inputs and outputs.</span></span> <span data-ttu-id="8ee26-107">**[参照]** ビューアーは、次のコントロールを使用して、接続を探索できます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-107">The **Browse** viewer helps you to explore those connections, using the following controls:</span></span>

-   [<span data-ttu-id="8ee26-108">変数</span><span class="sxs-lookup"><span data-stu-id="8ee26-108">Variables</span></span>](#BKMK_Variables)

-   [<span data-ttu-id="8ee26-109">入力</span><span class="sxs-lookup"><span data-stu-id="8ee26-109">Inputs</span></span>](#BKMK_Inputs)

-   [<span data-ttu-id="8ee26-110">出力</span><span class="sxs-lookup"><span data-stu-id="8ee26-110">Outputs</span></span>](#BKMK_Outputs)

 <span data-ttu-id="8ee26-111">このビューアーを使ってテストする場合は、[分類ウィザード &#40;Excel 用データ マイニング アドイン&#41;](classify-wizard-data-mining-add-ins-for-excel.md) ウィザードを使用してモデルを作成し、**[詳細設定]** オプションを使用して、**[アルゴリズム パラメーター]** ダイアログ ボックスでアルゴリズムを Microsoft ロジスティック回帰に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-111">If you want to experiment with this viewer, you can create a model using the [Classify Wizard &#40;Data Mining Add-ins for Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) wizard, and use the **Advanced** option to change the algorithm to Microsoft Logistic Regression in the **Algorithm Parameters** dialog box.</span></span>

###  <a name="variables"></a><a name="BKMK_Variables"></a><span data-ttu-id="8ee26-112">環境</span><span class="sxs-lookup"><span data-stu-id="8ee26-112">Variables</span></span>
 <span data-ttu-id="8ee26-113">**[変数]** ペインには、モデルに対する影響度の順に入力変数の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-113">The **Variables** pane displays a list of input variables in order of their effect on the model.</span></span> <span data-ttu-id="8ee26-114">**[入力]** および **[出力]** コントロールを使用してモデルをフィルター処理し、表示される変数と順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-114">You use the **Input** and **Output** controls to filter the model, affecting the variables that are displayed, as well as their order.</span></span>

 <span data-ttu-id="8ee26-115">このビューアーを使用すると、顧客が自転車購入者と非購入者のどちらのカテゴリに属する可能性が高いか判断する際に最も重要な要因を調査できます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-115">Using this viewer, you can explore the factors that are most important in determining whether a customer more likely belongs to the bike buyer category or the non-buyer category.</span></span>

 <span data-ttu-id="8ee26-116">![選択した属性の結果に対する影響のテスト](media/dm13-neuralnet-agebuyer1.gif "選択した属性の結果に対する影響のテスト")</span><span class="sxs-lookup"><span data-stu-id="8ee26-116">![Testing effect on outcome of selected attributes](media/dm13-neuralnet-agebuyer1.gif "Testing effect on outcome of selected attributes")</span></span>

##### <a name="explore-variables"></a><span data-ttu-id="8ee26-117">変数の調査</span><span class="sxs-lookup"><span data-stu-id="8ee26-117">Explore variables</span></span>

1.  <span data-ttu-id="8ee26-118">**[変数]** ペインは最初は、現在のフィルターに従って、重要な属性から順番に並べられています。</span><span class="sxs-lookup"><span data-stu-id="8ee26-118">Initially, the **Variables** pane is sorted in order of the most important attributes, given the current filters.</span></span> <span data-ttu-id="8ee26-119">バーの長さは、その要因の強さを示します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-119">The length of the bar indicates the strength of the factor.</span></span>

     <span data-ttu-id="8ee26-120">例では、収入が最も影響を与える要因であり、地域がそれに続くことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-120">In the example, you can see that income is the most influential factor, followed by region.</span></span> <span data-ttu-id="8ee26-121">一方で、多くの自動車と多くの子供を持つ顧客が自転車を購入する可能性はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="8ee26-121">On the other hand, customers with many cars and many children are highly unlikely to buy a bike.</span></span>

2.  <span data-ttu-id="8ee26-122">**[変数]** ペインで、**[属性]** の列見出しをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ee26-122">In the **Variables** pane, click the column heading for **Attribute**.</span></span>

     <span data-ttu-id="8ee26-123">属性を並べ替えることによって、入力列ごとに作成されたビンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-123">By sorting on attribute, you can see the bins that were created for each of the input columns.</span></span> <span data-ttu-id="8ee26-124">職業などの不連続な値を持つ列は、リテラル値によって*ビン分割*されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-124">Columns with discrete values, such as occupation, are *binned* by the literal values.</span></span>

3.  <span data-ttu-id="8ee26-125">**[Age]** (年齢) と **[Income]** (収入) で検出された値の範囲に注目してください。</span><span class="sxs-lookup"><span data-stu-id="8ee26-125">Notice the ranges of values that were found for **Age** and **Income**.</span></span>

     <span data-ttu-id="8ee26-126">入力列が数値 (つまり、データ列全体が連続する数値データ型) の場合、数値は不連続な範囲にバケット化 (ビン分割) されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-126">If any of your input columns are numbers (that is, the entire column of data is a continuous numeric data type), the numbers are bucketed, or binned, into discrete ranges.</span></span>

     <span data-ttu-id="8ee26-127">Income 列の場合、78.4-154.06 (最上位の収入範囲) のようなグループに細分されています。</span><span class="sxs-lookup"><span data-stu-id="8ee26-127">For Income, the column has been subdivided into groupings such as 78.4-154.06 (for the uppermost income range).</span></span>

     <span data-ttu-id="8ee26-128">![並べ替えて変数がどのようにビン分割されたかを表示](media/dm13-nn-bucketing-variables.gif "並べ替えて変数がどのようにビン分割されたかを表示")</span><span class="sxs-lookup"><span data-stu-id="8ee26-128">![sort to view how variables were binned](media/dm13-nn-bucketing-variables.gif "sort to view how variables were binned")</span></span>

     <span data-ttu-id="8ee26-129">異なるグループ分けが必要な場合は、[ラベルの変更 &#40;SQL Server データ マイニング アドイン&#41;](relabel-sql-server-data-mining-add-ins.md) ツールまたは Excel 関数を使用して、モデルを構築する前に新しい収入カテゴリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ee26-129">If you want different groupings, you should use the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool, or Excel functions, to create new income categories before building the model.</span></span>

4.  <span data-ttu-id="8ee26-130">**[Yes を優先]** をクリックして、グラフを既定のビューに戻します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-130">Click **Favors Yes** to restore the graph to the default view.</span></span>

     <span data-ttu-id="8ee26-131">既定では、ビューは最初の結果値の **[～を優先]** の値によって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-131">By default, the view is sorted by the value of **Favors** for the first outcome value.</span></span> <span data-ttu-id="8ee26-132">**[出力]** の **[値 1]** および **[値 2]** で新しい値を選択すると、1 番目の列と 2 番目の列に割り当てられる結果を変更できます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-132">You can change which outcomes are assigned to the first and second columns by choosing a new value for **Value 1** and **Value 2** in **Output**.</span></span>

5.  <span data-ttu-id="8ee26-133">グラフの最上位の色分けされたバーの上にマウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-133">Pause the mouse over the topmost colored bar in the chart.</span></span>

     <span data-ttu-id="8ee26-134">*重要度*スコア、1 対の*確率*スコア、および 1 対の*リフト*値がツールヒントに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-134">A ToolTip appears that includes an *importance* score, a pair of *probability* scores, and a pair of *lift* values.</span></span>

    -   <span data-ttu-id="8ee26-135">**重要度**は、データセット全体を対象として計算され、すべてを入力した場合に、目標の結果と最も相関性が高い属性を識別します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-135">**Importance** is calculated across the entire dataset, and identifies the attribute that, given all inputs, is most correlated with the target outcome.</span></span> <span data-ttu-id="8ee26-136">ビューアーでは、重要度スコア順にグラフの値が並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-136">The viewer sorts the values in the chart by the importance scores.</span></span>

    -   <span data-ttu-id="8ee26-137">**確率**は、データ セット全体を対象として、属性と値のペアごとに目標の結果について計算されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-137">**Probability** is calculated for each set of attribute-value pairs, for the target outcomes, across the entire data set.</span></span>

    -   <span data-ttu-id="8ee26-138">**リフト**は、この特定の属性と値のペアが結果の昇格にどの程度有益かを示します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-138">**Lift** tells you how useful this particular attribute-value pair is for promoting one outcome or another.</span></span>

     <span data-ttu-id="8ee26-139">注: どの列にマウス ポインターを置いた場合でも、ツールヒントには同じ情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-139">Note: The ToolTip contains the same information no matter whether you position the mouse over one column or the other.</span></span>

 [<span data-ttu-id="8ee26-140">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8ee26-140">Back To Top</span></span>](#BKMK_Tabs)

###  <a name="inputs"></a><a name="BKMK_Inputs"></a><span data-ttu-id="8ee26-141">Inputaccel</span><span class="sxs-lookup"><span data-stu-id="8ee26-141">Inputs</span></span>
 <span data-ttu-id="8ee26-142">**[入力]** ペインでは、入力を選択して、それをモデルに対するフィルターとして適用することができます。これにより、トレーニング データを基準として、選択した入力が結果に及ぼす影響を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-142">The **Inputs** pane lets you choose a set of inputs and apply that as a filter to the model, which lets you see the influence of those choices on the outcome, based on the training data</span></span>

##### <a name="explore-inputs"></a><span data-ttu-id="8ee26-143">入力の調査</span><span class="sxs-lookup"><span data-stu-id="8ee26-143">Explore inputs</span></span>

1.  <span data-ttu-id="8ee26-144">特定のグループを対象として、そのグループで購入に最も大きく影響する要因を確認するとします。</span><span class="sxs-lookup"><span data-stu-id="8ee26-144">Suppose you want to target a particular group, and see the factors that most influence purchasing in that group.</span></span>

     <span data-ttu-id="8ee26-145">**入力**ペインで、[属性] の下のセルをクリックし、[ **\<All>** **年齢**] **Attribute**を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-145">In the **Input** pane, click the **\<All>** cell under **Attribute**, and select **Age**.</span></span>

     <span data-ttu-id="8ee26-146">**[値]** で、最も若い年齢のカテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-146">For **Value**, select the youngest age category.</span></span>

2.  <span data-ttu-id="8ee26-147">特定の年齢層をフィルター選択した場合でも、太平洋地域が一覧のほぼ最上位にきます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-147">Notice that even when you filter on a particular age group, the Pacific region comes to near the top of the list.</span></span> <span data-ttu-id="8ee26-148">これは太平洋地域の顧客が他の地域の顧客よりも自転車を購入する可能性がはるかに高いためです。</span><span class="sxs-lookup"><span data-stu-id="8ee26-148">This is because customers in the Pacific region are far more likely to buy a bike than customers in other regions.</span></span>

     <span data-ttu-id="8ee26-149">地域は影響を及ぼすことができるものではないので、この変数を除外して他の要因を表示するために、入力を再び変更します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-149">Since region is not something you can influence, to remove this variable from consideration and see other factors, you can change the inputs again.</span></span>

     <span data-ttu-id="8ee26-150">**[入力]** ペインで、**[Age]** の空白のセルをクリックし、**[Region]** (地域) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ee26-150">In the **Input** pane, click the empty cell under **Age**, and select **Region**.</span></span>

     <span data-ttu-id="8ee26-151">**[値]** で **[Europe]** (欧州) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ee26-151">For **Value**, select **Europe**.</span></span>

3.  <span data-ttu-id="8ee26-152">引き続き入力フィルターを追加して、特に興味深いグループに絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-152">Continue adding input filters to focus on a group of particular interest.</span></span>

     <span data-ttu-id="8ee26-153">たとえば、入力属性として **[Gender]** (性別) を追加し、値として **[Female]** (女性) を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-153">For example, for the input attribute, add **Gender**, and select **Female** as the value.</span></span>

     <span data-ttu-id="8ee26-154">![選択した属性の結果に対する影響のテスト](media/dm13-neuralnet-agebuyer2.gif "選択した属性の結果に対する影響のテスト")</span><span class="sxs-lookup"><span data-stu-id="8ee26-154">![Testing effect on outcome of selected attributes](media/dm13-neuralnet-agebuyer2.gif "Testing effect on outcome of selected attributes")</span></span>

     <span data-ttu-id="8ee26-155">変数の一覧がどのように変化するか確認してください。</span><span class="sxs-lookup"><span data-stu-id="8ee26-155">Notice how the list of variables changes.</span></span> <span data-ttu-id="8ee26-156">現在は **[Income]** が、目標の結果を予測するうえで最も重要な変数です。</span><span class="sxs-lookup"><span data-stu-id="8ee26-156">Now **Income** is the variable that is most important in predicting the target outcome.</span></span>

     <span data-ttu-id="8ee26-157">入力フィルターを適用する順序は結果には影響しません。</span><span class="sxs-lookup"><span data-stu-id="8ee26-157">The order in which you apply the input filters does not affect the results.</span></span>

 [<span data-ttu-id="8ee26-158">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8ee26-158">Back To Top</span></span>](#BKMK_Tabs)

###  <a name="outputs"></a><a name="BKMK_Outputs"></a><span data-ttu-id="8ee26-159">出力</span><span class="sxs-lookup"><span data-stu-id="8ee26-159">Outputs</span></span>
 <span data-ttu-id="8ee26-160">**[出力]** ペインで、興味のある結果を選択できます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-160">In the **Outputs** pane, you can choose the outcome that you are interested in.</span></span> <span data-ttu-id="8ee26-161">ニューラル ネットワークでは、結果列をいくつでも指定できます。ただし、出力を追加するほど、モデルが複雑になるため、処理時間が大幅に長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8ee26-161">Neural networks let you specify as many outcome columns as you like, although adding more outputs adds to the complexity of the model and may require a much longer time to process.</span></span>

 <span data-ttu-id="8ee26-162">2 つの出力を比較するには、出力を **[予測]** または **[予測のみ]** 列として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ee26-162">To compare two outputs, they must have been designated as **Predict** or **Predict Only** columns.</span></span>

##### <a name="explore-outputs"></a><span data-ttu-id="8ee26-163">出力の調査</span><span class="sxs-lookup"><span data-stu-id="8ee26-163">Explore outputs</span></span>

1.  <span data-ttu-id="8ee26-164">**[出力属性]** 一覧を使用して、属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-164">Use the **Output Attribute** list to select an attribute.</span></span>

2.  <span data-ttu-id="8ee26-165">[値 1] ボックスと [値 2] ボックスで 2 つの結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-165">Select two outcomes from the Value 1 and Value 2 lists.</span></span> <span data-ttu-id="8ee26-166">出力属性のこれらの 2 つの状態は、 **[変数]** ペインで比較されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-166">These two states of the output attribute will be compared in the **Variables** pane.</span></span>

 [<span data-ttu-id="8ee26-167">トップに戻る</span><span class="sxs-lookup"><span data-stu-id="8ee26-167">Back To Top</span></span>](#BKMK_Tabs)

## <a name="more-about-neural-network-models"></a><span data-ttu-id="8ee26-168">ニューラル ネットワーク モデルの詳細</span><span class="sxs-lookup"><span data-stu-id="8ee26-168">More About Neural Network Models</span></span>
 <span data-ttu-id="8ee26-169">ビューアーに表示される情報は、このモデルの種類専用のストアド プロシージャである System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores を使用してサーバーから取得されます。</span><span class="sxs-lookup"><span data-stu-id="8ee26-169">The information in the viewer is retrieved from the server using a stored procedure specific to this model type: System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores.</span></span>

 <span data-ttu-id="8ee26-170">アドインを使用して予測可能な属性を複数持つモデルを作成する場合は、**[詳細設定]** モデリング オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ee26-170">If you want to create a model with multiple predictable attributes using the add-ins, use the **Advanced** modeling options.</span></span>

 <span data-ttu-id="8ee26-171">詳細については、「[マイニング構造の作成 &#40;SQL Server データ マイニング アドイン&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)」および「[構造へのモデルの追加 &#40;Excel 用データ マイニング アドイン&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee26-171">For more information, see [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) and [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ee26-172">参照</span><span class="sxs-lookup"><span data-stu-id="8ee26-172">See Also</span></span>
 [<span data-ttu-id="8ee26-173">Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;</span><span class="sxs-lookup"><span data-stu-id="8ee26-173">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)


