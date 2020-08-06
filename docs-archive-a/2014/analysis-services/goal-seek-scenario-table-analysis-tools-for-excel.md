---
title: ゴールシークシナリオ (Excel 用のテーブル分析ツール) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b3b4df4f78a2d3652b1dac3c566e66507b523ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634718"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a><span data-ttu-id="92097-102">ゴール シーク シナリオ (Excel 用のテーブル分析ツール)</span><span class="sxs-lookup"><span data-stu-id="92097-102">Goal Seek Scenario (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="92097-103">![[テーブル分析ツール] の [ゴール シーク] ボタン](media/tat-goalseek.gif "[テーブル分析ツール] の [ゴール シーク] ボタン")</span><span class="sxs-lookup"><span data-stu-id="92097-103">![Goal Seek button in Table Analysis tools](media/tat-goalseek.gif "Goal Seek button in Table Analysis tools")</span></span>  
  
 <span data-ttu-id="92097-104">**ゴールシーク**シナリオツールは、 [What If](what-if-scenario-table-analysis-tools-for-excel.md)シナリオツールを補完するものです。</span><span class="sxs-lookup"><span data-stu-id="92097-104">The **Goal Seek** scenario tool is complementary to the [What If](what-if-scenario-table-analysis-tools-for-excel.md) scenario tool.</span></span> <span data-ttu-id="92097-105">**What-if**ツールを使用すると、変更の影響を確認できます。一方、**ゴールシーク**ツールでは、必要な結果を得るために変更する必要がある基になる要因がわかります。</span><span class="sxs-lookup"><span data-stu-id="92097-105">The **What-If** tool tells you the impact of making a change, whereas the **Goal Seek** tool tells you the underlying factors that must change to achieve a desired result.</span></span>  
  
 <span data-ttu-id="92097-106">たとえば、顧客満足度を向上させることが目標であるとします。</span><span class="sxs-lookup"><span data-stu-id="92097-106">For example, let's say your goal is to increase customer satisfaction.</span></span> <span data-ttu-id="92097-107">**ゴールシーク**分析を使用して、顧客満足度を高める要因を判断し、それらの変更がコスト効率に優れているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="92097-107">You can use **Goal Seek** analysis to determine which factors would be most likely to increase customer satisfaction, and decide whether those changes are cost-effective.</span></span>  
  
 <span data-ttu-id="92097-108">分析が完了すると、ソース データ テーブルに 2 つの新しい列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="92097-108">When the tool finishes its analysis, it creates two new columns in the source data table.</span></span> <span data-ttu-id="92097-109">これらの列には、対象となる結果を達成できる*確率*と、推奨される変更 (存在する場合) が示されます。</span><span class="sxs-lookup"><span data-stu-id="92097-109">These columns show the *likelihood* that the targeted outcome can be achieved, and the recommended change, if any.</span></span>  
  
 <span data-ttu-id="92097-110">このツールでは、データのセットを分析し、そのセット全体を対象に予測を作成できます。また、分析を作成してから、シナリオを 1 つずつテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="92097-110">The tool can analyze a set of data and make predictions for the entire set, or you can create the analysis and then test scenarios one at a time.</span></span>  
  
## <a name="using-the-goal-seek-scenario-tool"></a><span data-ttu-id="92097-111">ゴール シーク シナリオ ツールの使用</span><span class="sxs-lookup"><span data-stu-id="92097-111">Using the Goal Seek Scenario Tool</span></span>  
  
1.  <span data-ttu-id="92097-112">Excel テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="92097-112">Open an Excel table.</span></span>  
  
2.  <span data-ttu-id="92097-113">[**シナリオ**] をクリックし、[**ゴールシーク**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="92097-113">Click **Scenarios**, and select **Goal Seek**.</span></span>  
  
3.  <span data-ttu-id="92097-114">[**シナリオ分析: ゴールシーク**] ダイアログボックスで、一覧から対象の値を含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="92097-114">In the **Scenario Analysis: Goal Seek** dialog box, select the column that contains the target value from the list.</span></span>  
  
4.  <span data-ttu-id="92097-115">達成しようとする値を指定します。</span><span class="sxs-lookup"><span data-stu-id="92097-115">Specify the value that you want to achieve.</span></span>  
  
     <span data-ttu-id="92097-116">列の目標が連続する数値である場合は、目標とする値の増減を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="92097-116">If the column goal contains continuous numeric values, you can also specify a desired increase or decrease in the value.</span></span> <span data-ttu-id="92097-117">たとえば、列として**Sales**を選択し、ターゲットが120% の増加であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="92097-117">For example, you might choose **Sales** as the column and specify that the target is an increase of 120%.</span></span>  
  
     <span data-ttu-id="92097-118">または、上限と下限を入力して、値の範囲で目標を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="92097-118">Or, you can specify the goal as a range of values, by typing a lower and upper limit.</span></span>  
  
5.  <span data-ttu-id="92097-119">変更する値を含む列を指定します。</span><span class="sxs-lookup"><span data-stu-id="92097-119">Specify the column that contains the values you will change.</span></span> <span data-ttu-id="92097-120">つまり、目的の結果を得るために操作する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="92097-120">In other words, pick the column that will be manipulated to produce the desired result.</span></span>  
  
6.  <span data-ttu-id="92097-121">必要に応じて、[**分析に使用する列の選択**] をクリックし、役に立つ情報が含まれている列を選択します。</span><span class="sxs-lookup"><span data-stu-id="92097-121">Optionally, click **Choose columns to be used for analysis**, and select columns that contain useful information.</span></span> <span data-ttu-id="92097-122">分析に貢献しない列の選択は解除します。</span><span class="sxs-lookup"><span data-stu-id="92097-122">Deselect columns that will not contribute to the analysis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="92097-123">目標または変更に使用する列の選択は解除しないでください。</span><span class="sxs-lookup"><span data-stu-id="92097-123">Do not deselect columns that you will use for either the goal or the change.</span></span> <span data-ttu-id="92097-124">これらの列は必須です。</span><span class="sxs-lookup"><span data-stu-id="92097-124">These columns are required.</span></span>  
  
7.  <span data-ttu-id="92097-125">テーブル全体を対象に予測するか、選択した行のみを対象に予測するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="92097-125">Specify whether you want to make predictions for the entire table, or for only the selected row.</span></span>  
  
8.  <span data-ttu-id="92097-126">[**テーブル全体**] オプションを選択した場合、2つの新しい列のソーステーブルに予測が追加されます。</span><span class="sxs-lookup"><span data-stu-id="92097-126">If you selected the **Entire table** option, the tool adds the predictions to the source table in two new columns.</span></span>  
  
9. <span data-ttu-id="92097-127">**この行で**オプションを選択した場合、分析の結果がダイアログボックスに出力され、確認できます。</span><span class="sxs-lookup"><span data-stu-id="92097-127">If you selected the option **On this row**, the results of analysis are output to the dialog box for review.</span></span> <span data-ttu-id="92097-128">さまざまな値や目標を引き続きテストすることができるように、このダイアログ ボックスは開いたままになります。</span><span class="sxs-lookup"><span data-stu-id="92097-128">The dialog box stays open so that you can continue trying out different values and goals.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="92097-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="92097-129">Requirements</span></span>  
 <span data-ttu-id="92097-130">このツールでは、数値または不連続値を処理できる Microsoft ロジスティック回帰アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="92097-130">This tool uses the Microsoft Logistic Regression algorithm, which can process either numeric or discrete values.</span></span>  
  
 <span data-ttu-id="92097-131">予測を複数回実行し、そのたびに異なる列を選択することもできますが、目標と変更の複数の組み合わせを同時に計算することはできません。</span><span class="sxs-lookup"><span data-stu-id="92097-131">You can run the prediction multiple times, and select different columns later, but each combination of a goal and a change must be calculated separately.</span></span>  
  
 <span data-ttu-id="92097-132">関連性の高い列を選択して分析を実行すると、より正確な結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="92097-132">You can achieve better results if you select columns for analysis that contain useful information.</span></span> <span data-ttu-id="92097-133">ただし、対象となる列が少なすぎると、結果を得ることが難しくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="92097-133">However, if you include too few columns, it might be difficult to obtain a result.</span></span>  
  
 <span data-ttu-id="92097-134">予測を 1 つずつ作成する場合は、目的の結果がまだ格納されていない行を選択してください。そうしないと、エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="92097-134">When you create predictions one at a time, be sure to select a row that does not already contain the desired result, or you may get an error.</span></span> <span data-ttu-id="92097-135">つまり、ゴール シークの目的が、自転車の購入動機となる要因を特定することである場合は、自転車を購入していない顧客だけを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="92097-135">In other words, if the purpose of goal seeking is to determine factors that encourage bike purchases, you should only include customers who did not purchase a bike.</span></span>  
  
## <a name="understanding-the-results-of-goal-seek-analysis"></a><span data-ttu-id="92097-136">ゴール シーク分析の結果について</span><span class="sxs-lookup"><span data-stu-id="92097-136">Understanding the Results of Goal Seek Analysis</span></span>  
 <span data-ttu-id="92097-137">ゴール シーク シナリオを作成すると、このツールによって次の 3 つ処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="92097-137">When you create a goal seeking scenario, the tool does three things:</span></span>  
  
-   <span data-ttu-id="92097-138">テーブル内のデータに関する主要な要因を格納するデータ マイニング構造を作成する。</span><span class="sxs-lookup"><span data-stu-id="92097-138">Creates a data mining structure that stores key facts about the data in your table.</span></span>  
  
-   <span data-ttu-id="92097-139">データに基づいて、ロジスティック回帰マイニング モデルを作成する。</span><span class="sxs-lookup"><span data-stu-id="92097-139">Creates a logistic regression mining model based on the data.</span></span>  
  
-   <span data-ttu-id="92097-140">指定された個々の値について予測を作成する。</span><span class="sxs-lookup"><span data-stu-id="92097-140">Creates a prediction for each value that you specify.</span></span>  
  
 <span data-ttu-id="92097-141">ゴール シーク シナリオを 1 つずつテストする場合、結果を対話的に表示できます。</span><span class="sxs-lookup"><span data-stu-id="92097-141">If you test goal-seeking scenarios one at a time, you can view the results interactively.</span></span> <span data-ttu-id="92097-142">これは、*単一予測クエリ*を作成することと同じです。</span><span class="sxs-lookup"><span data-stu-id="92097-142">This is the same as creating a *singleton prediction query*.</span></span>  
  
 <span data-ttu-id="92097-143">このツールを実行すると、目的の目標を達成するシナリオが正常に検出されたかどうかにかかわらず、ダイアログボックスの [**結果**] ウィンドウにレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92097-143">The tool reports in the **Results** pane of the dialog box whether it was successful in finding a scenario that achieves the desired goal.</span></span> <span data-ttu-id="92097-144">適切な解決策が見つかった場合は、必要な変更を示す提案も生成されます。</span><span class="sxs-lookup"><span data-stu-id="92097-144">If a successful solution was found, the tool also generates a recommendation that tells you the required change.</span></span> <span data-ttu-id="92097-145">たとえば、**ゴールシーク**ツールを使用すると、通勤距離を5マイル未満にする必要があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="92097-145">For example, the **Goal Seek** tool might tell you that the commuting distance should be less than 5 miles.</span></span>  
  
 <span data-ttu-id="92097-146">結果の例:</span><span class="sxs-lookup"><span data-stu-id="92097-146">Example results:</span></span>  
  
 <span data-ttu-id="92097-147">**Interest in Buying のゴール シークで解が見つかりました。**</span><span class="sxs-lookup"><span data-stu-id="92097-147">**Goal Seeking for Interest in Buying has found a solution.**</span></span>  
  
 <span data-ttu-id="92097-148">**'Commute distance' を '2-5 miles' に変更することで、最も近い一致を得ました。**</span><span class="sxs-lookup"><span data-stu-id="92097-148">**Closest match obtained by changing 'Commute distance' to '2-5 miles'.**</span></span>  
  
 <span data-ttu-id="92097-149">この結果は、データ テーブルの既存の行に基づいて作成されています。つまり、特定の顧客について、他のすべての条件はそのままで、通勤距離だけを 2 ～ 5 マイルに減らした場合、その顧客は自転車を購入する可能性が高くなることを示しています。</span><span class="sxs-lookup"><span data-stu-id="92097-149">Because this result is based on an existing row in the data table, it means that, for a particular customer, if all else about the customer stayed the same but the customer's commute was reduced to 2-5 miles, the customer would be somewhat more likely buy a bicycle.</span></span>  
  
 <span data-ttu-id="92097-150">**テーブル全体**を指定して、Excel テーブル内のすべての行に対してゴールシークの予測を作成すると、元のデータテーブルに2つの新しい列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="92097-150">If you create goal-seeking predictions for all the rows in the Excel table by specifying **Entire table**, thetool creates two new columns in the original data table.</span></span> <span data-ttu-id="92097-151">テーブルに追加される 1 つ目の列には、目標を満たすことが可能であれば、緑色の円にチェック マークが表示されます。また、どう変更しても目標を達成できない場合は、赤色の円に X 印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="92097-151">The first column that is added to the table contains either a check mark in a green circle, to indicate that the goal can be met, or an X mark in a red circle, to indicate that no changes can be made that will enable the goal.</span></span>  
  
 <span data-ttu-id="92097-152">2 つ目の列には、推奨される変更が表示されます。</span><span class="sxs-lookup"><span data-stu-id="92097-152">The second column contains the recommended change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92097-153">推奨値の信頼度と予測の可否はアルゴリズムによってあらかじめ定義され、変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="92097-153">The confidence level for the recommendation and its success are predetermined by the algorithm and cannot be changed.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="92097-154">関連ツール</span><span class="sxs-lookup"><span data-stu-id="92097-154">Related Tools</span></span>  
 <span data-ttu-id="92097-155">より高度なデータ マイニング機能を備えた別のアドインとして、Excel 用のデータ マイニング クライアントがあります。Excel 用のデータ マイニング クライアントには、行動を予測するデータ マイニング モデルを作成するためのウィザードが備わっています。</span><span class="sxs-lookup"><span data-stu-id="92097-155">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, includes wizards for creating data mining models that predict behavior.</span></span> <span data-ttu-id="92097-156">詳細については、「[データマイニングモデルの作成](creating-a-data-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92097-156">For more information, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>  
  
 <span data-ttu-id="92097-157">**ゴールシーク**シナリオツールで使用されるアルゴリズムの詳細については、オンラインブックの「Microsoft ロジスティック回帰アルゴリズム」を参照してください [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="92097-157">For more information about the algorithm used by the **Goal Seek** scenario tool, see the topic "Microsoft Logistic Regression Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92097-158">参照</span><span class="sxs-lookup"><span data-stu-id="92097-158">See Also</span></span>  
 [<span data-ttu-id="92097-159">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="92097-159">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
