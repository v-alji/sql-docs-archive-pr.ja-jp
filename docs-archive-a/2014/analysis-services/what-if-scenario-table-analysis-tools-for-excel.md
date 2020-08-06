---
title: What-if シナリオ (Excel 用のテーブル分析ツール) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4bb5c5e866c1320c297fb4f2760bca58623f6601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743469"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a><span data-ttu-id="28180-102">What-If シナリオ (Excel 用のテーブル分析ツール)</span><span class="sxs-lookup"><span data-stu-id="28180-102">What-If Scenario (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="28180-103">![テーブル分析ツールの [What If シナリオ] ボタン](media/tat-whatif.gif "テーブル分析ツールの [What If シナリオ] ボタン")</span><span class="sxs-lookup"><span data-stu-id="28180-103">![What If Scenario button in Table Analysis tools](media/tat-whatif.gif "What If Scenario button in Table Analysis tools")</span></span>

 <span data-ttu-id="28180-104">**What-if**シナリオツールは、既存のデータのパターンを分析し、1つの列の変更が別の列の値に与える影響を評価できるようにします。</span><span class="sxs-lookup"><span data-stu-id="28180-104">The **What-If** scenario tool analyzes patterns in existing data, and then enables you to evaluate the effect that changes in one column would have on the value of a different column.</span></span>

 <span data-ttu-id="28180-105">たとえば、品目の値上げがその売上合計に与える影響を調べる場合などに使用します。</span><span class="sxs-lookup"><span data-stu-id="28180-105">For example, you could explore the effect of raising the price of an item on its total sales.</span></span>

 <span data-ttu-id="28180-106">このツールで作成される予測の数は、ユーザーが適宜選択できます。</span><span class="sxs-lookup"><span data-stu-id="28180-106">The tool is flexible about the number of predictions you can create.</span></span> <span data-ttu-id="28180-107">初期分析の実行後に、テーブル内の全データを対象に変化を予測するか、テスト値を逐一入力するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="28180-107">After the initial analysis is complete, you can either predict changes for all the data in the table, or enter test values one at a time.</span></span>

## <a name="using-the-what-if-scenario-tool"></a><span data-ttu-id="28180-108">What-If シナリオ ツールの使用</span><span class="sxs-lookup"><span data-stu-id="28180-108">Using the What-If Scenario Tool</span></span>

1.  <span data-ttu-id="28180-109">Excel データ テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="28180-109">Open an Excel data table.</span></span>

2.  <span data-ttu-id="28180-110">[**シナリオ**] をクリックし、[ **what-if**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="28180-110">Click **Scenarios**, and then select **What-If**.</span></span>

3.  <span data-ttu-id="28180-111">[**シナリオ**] ボックスで、変更する値が含まれている列を選択し、変更を特定の値として指定するか、または現在の値に対する変更の割合 (増加または減少) として指定します。</span><span class="sxs-lookup"><span data-stu-id="28180-111">In the **Scenario** box, select the column that contains the value you will change, and specify the change either as a specific value or as a percentage of change (either increased or decreased) on the current values.</span></span>

4.  <span data-ttu-id="28180-112">[**処理の対象**] ボックスで、効果を評価する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="28180-112">In the **What happens to** box, specify the column for which you want to assess the effect.</span></span>

5.  <span data-ttu-id="28180-113">必要に応じて、[**分析に使用する列の選択**] をクリックして、予測の作成に役立つ可能性のある列を選択します。</span><span class="sxs-lookup"><span data-stu-id="28180-113">Optionally, click **Choose columns to be used for analysis** to select columns that are likely to be useful in making the prediction.</span></span> <span data-ttu-id="28180-114">行の ID や名前など、パターンの検出に貢献しない列については、選択を解除することもできます。</span><span class="sxs-lookup"><span data-stu-id="28180-114">You can also deselect columns that are likely to be of little use in detecting patterns, such as row IDs or names.</span></span>

6.  <span data-ttu-id="28180-115">[**行またはテーブルの指定**] ボックスで、現在選択されている行に対してのみ、またはテーブル内の完全なデータセットの影響を評価するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="28180-115">In the **Specify row or table** box, choose whether you want the impact assessed for the currently selected row only, or for the complete set of data in the table.</span></span>

7.  <span data-ttu-id="28180-116">**この行**を選択すると、ダイアログボックスに結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="28180-116">If you select **On this row**, the tool displays the result in the dialog box.</span></span> <span data-ttu-id="28180-117">このダイアログ ボックスを開いたまま、選択を変更して他のシナリオをテストできます。</span><span class="sxs-lookup"><span data-stu-id="28180-117">While the dialog box remains open, you can modify your selections to test other scenarios.</span></span>

8.  <span data-ttu-id="28180-118">[**テーブル全体**] を選択すると、ダイアログボックスにステータスメッセージが表示され、元のデータテーブルに2つの新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="28180-118">If you select **Entire table**, the tool displays a status message in the dialog box, and adds two new columns to the original data table.</span></span> <span data-ttu-id="28180-119">ワークシート内の完全な結果を表示するには、[**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28180-119">Click **Close** to view the complete results in the worksheet.</span></span>

### <a name="requirements"></a><span data-ttu-id="28180-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="28180-120">Requirements</span></span>
 <span data-ttu-id="28180-121">このツールでは、数値または不連続値の予測をサポートする Microsoft ロジスティック回帰アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="28180-121">This tool uses the Microsoft Logistic Regression algorithm, which supports prediction of either numeric or discrete values.</span></span> <span data-ttu-id="28180-122">ただし、最適な結果を得るために、次のベスト プラクティスに従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="28180-122">However, to achieve the best results, we suggest the following best practices:</span></span>

-   <span data-ttu-id="28180-123">有用な情報を含む列を分析対象として選択します。</span><span class="sxs-lookup"><span data-stu-id="28180-123">Select columns for analysis that contain useful information.</span></span>

-   <span data-ttu-id="28180-124">対象となる列が少なすぎると、結果を得ることが難しくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="28180-124">If you include too few columns it may be difficult to obtain a result.</span></span>

-   <span data-ttu-id="28180-125">[**値の指定**] オプションを使用する場合は、ボックスに値を入力するか、一覧から値を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28180-125">If you use the **To value** option, you must type a value in the box or select a value from the list.</span></span>

-   <span data-ttu-id="28180-126">[**パーセント**] オプションを使用する場合は、[増減の割合] で変更を設定します。</span><span class="sxs-lookup"><span data-stu-id="28180-126">If you use the **Percentage** option, set the change as a percentage increase or decrease.</span></span> <span data-ttu-id="28180-127">既定値は 120% (現在の値の 20% 増) です。</span><span class="sxs-lookup"><span data-stu-id="28180-127">The default is 120%, meaning a 20% increase over the current value.</span></span>

> [!NOTE]
>  <span data-ttu-id="28180-128">値を設定しないと、エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="28180-128">If you do not set a value, you might receive an error.</span></span>

## <a name="understanding-the-results-of-what-if-analysis"></a><span data-ttu-id="28180-129">What-If 分析の結果について</span><span class="sxs-lookup"><span data-stu-id="28180-129">Understanding the Results of What-If Analysis</span></span>
 <span data-ttu-id="28180-130">**What-if**シナリオを作成すると、ツールによって次の3つの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="28180-130">When you create a **What-If** scenario, the tool does three things:</span></span>

-   <span data-ttu-id="28180-131">テーブル内のデータに関する主要な要因を格納するデータ マイニング構造を作成する。</span><span class="sxs-lookup"><span data-stu-id="28180-131">Creates a data mining structure that stores key facts about the data in your table.</span></span>

-   <span data-ttu-id="28180-132">データに基づいて、ロジスティック回帰マイニング モデルを作成する。</span><span class="sxs-lookup"><span data-stu-id="28180-132">Creates a logistic regression mining model based on the data.</span></span>

-   <span data-ttu-id="28180-133">指定された個々の値について予測クエリを作成する。</span><span class="sxs-lookup"><span data-stu-id="28180-133">Creates a prediction query for each of the values you specify.</span></span>

 <span data-ttu-id="28180-134">**テーブル全体**を指定することにより、すべての予測を一度に出力できます。</span><span class="sxs-lookup"><span data-stu-id="28180-134">You can output all the predictions at one time by specifying **Entire table**.</span></span> <span data-ttu-id="28180-135">この場合、元のデータ テーブルに 2 つの新しい列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="28180-135">The tool then creates two new columns in the original data table.</span></span>

 <span data-ttu-id="28180-136">テーブルに追加された列には、それぞれ、変更に対する予測値と、その信頼度という 2 種類の情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="28180-136">The columns that are added to the table contain two types of information: the predicted value given the change, and its confidence.</span></span> <span data-ttu-id="28180-137">信頼度は、予測が正しいかどうかの確率のことです。</span><span class="sxs-lookup"><span data-stu-id="28180-137">Confidence means the probability that the prediction is correct.</span></span>

 <span data-ttu-id="28180-138">変更する値をダイアログ ボックスに逐一入力し、予測を対話形式で確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="28180-138">You can also enter change values one by one in the dialog box, and view the predictions interactively.</span></span> <span data-ttu-id="28180-139">これは、*単一予測クエリ*を作成することと同じです。</span><span class="sxs-lookup"><span data-stu-id="28180-139">This is the same as creating a *singleton prediction query*.</span></span> <span data-ttu-id="28180-140">予測クエリの結果は、予測の可否、予測された値、および信頼度を伴って出力されます。</span><span class="sxs-lookup"><span data-stu-id="28180-140">The results of the prediction query are output with the following information: the success or failure of prediction, the predicted value, and the confidence level.</span></span> <span data-ttu-id="28180-141">信頼度は、点線を含むバーとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="28180-141">The confidence level is shown as a bar that contains a dotted line.</span></span> <span data-ttu-id="28180-142">点線が長いほど、結果の信頼度が高いことを意味します。</span><span class="sxs-lookup"><span data-stu-id="28180-142">The longer the dotted line, the higher the confidence in the result.</span></span>

 <span data-ttu-id="28180-143">たとえば、顧客の購入時期に顧客の年齢を増加させ、顧客の年齢を25に上げることによる影響を判断しようとしている場合、 **what-if**ツールはデータマイニングモデルにクエリを実行し、次の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="28180-143">For example, if you are trying to determine the effect of increasing the customer's age on the customer's willingness to buy, and increase the customer's age to 25, the **What-If** tool queries the data mining model and returns the following result:</span></span>

 <span data-ttu-id="28180-144">**Purchases Bicycle の What-If 分析で解決策が見つかりました。**</span><span class="sxs-lookup"><span data-stu-id="28180-144">**What-If Analysis for Purchases Bicycle has found a solution.**</span></span>

 <span data-ttu-id="28180-145">**'Purchases Bicycle' = yes**</span><span class="sxs-lookup"><span data-stu-id="28180-145">**'Purchases Bicycle' = yes**</span></span>

 <span data-ttu-id="28180-146">**信頼度: 普通**</span><span class="sxs-lookup"><span data-stu-id="28180-146">**Confidence: Fair**</span></span>

 <span data-ttu-id="28180-147">この結果は、データ テーブルの既存の行に基づいて作成されています。つまり、特定の顧客について、他のすべての条件はそのままで、年齢だけを 25 歳に変更した場合、その顧客は自転車を購入する可能性が高いことを示しています。</span><span class="sxs-lookup"><span data-stu-id="28180-147">Because this result is based on an existing row in the data table, it means that, for a particular customer, if all else about the customer stayed the same but the customer's age was increased to 25, the customer would likely buy a bicycle.</span></span>

 <span data-ttu-id="28180-148">予測を元のデータ テーブルに出力すると、その予測の実用性を判断しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="28180-148">Outputting the predictions to the original data table might make it easier to determine whether the predictions are useful.</span></span>

## <a name="related-tools"></a><span data-ttu-id="28180-149">関連ツール</span><span class="sxs-lookup"><span data-stu-id="28180-149">Related Tools</span></span>
 <span data-ttu-id="28180-150">より高度なデータ マイニング機能を備えた別のアドインとして、Excel 用のデータ マイニング クライアントがあります。Excel 用のデータ マイニング クライアントには、行動を予測するデータ マイニング モデルを作成するためのウィザードが備わっています。</span><span class="sxs-lookup"><span data-stu-id="28180-150">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, includes wizards for creating data mining models that predict behavior.</span></span> <span data-ttu-id="28180-151">詳細については、「[データマイニングモデルの作成](creating-a-data-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28180-151">For more information, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>

 <span data-ttu-id="28180-152">**What-if**シナリオツールで使用されるアルゴリズムの詳細については、SQL Server オンラインブックの「Microsoft ロジスティック回帰アルゴリズム」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28180-152">For more information about the algorithm used by the **What-If** scenario tool, see the topic "Microsoft Logistic Regression Algorithm" in SQL Server Books Online.</span></span>

## <a name="see-also"></a><span data-ttu-id="28180-153">参照</span><span class="sxs-lookup"><span data-stu-id="28180-153">See Also</span></span>
 [<span data-ttu-id="28180-154">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="28180-154">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)


