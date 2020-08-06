---
title: Fill From 例 (Excel 用のテーブル分析ツール) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- fill from example
ms.assetid: dac57d8f-1c65-4878-8ea0-9c680df5e4fb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69ff9f554c51240eb6f9151718d30677bfb57996
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715874"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a><span data-ttu-id="55264-102">自動推論 (Excel 用のテーブル分析ツール)</span><span class="sxs-lookup"><span data-stu-id="55264-102">Fill From Example (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="55264-103">![テーブル分析ツールの [自動推論] ボタン](media/tat-fillex.gif "テーブル分析ツールの [自動推論] ボタン")</span><span class="sxs-lookup"><span data-stu-id="55264-103">![Fill From Example button in Table Analysis Tools](media/tat-fillex.gif "Fill From Example button in Table Analysis Tools")</span></span>  
  
 <span data-ttu-id="55264-104">**Fill From サンプル**ツールを使用すると、既存の値に基づいて新しいデータ列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="55264-104">The **Fill From Example** tool helps you build new columns of data based on existing values.</span></span>  
  
 <span data-ttu-id="55264-105">たとえば、データに**購入金額**列、 **Orders Quantity**列、および他の列を使用するいくつかの数式に基づく**プレミア Customer**列が含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="55264-105">For example, suppose your data contains a **Purchase Amount** column, an **Orders Quantity** column, and a **Premier Customer** column that is based on some formula using the other columns.</span></span> <span data-ttu-id="55264-106">**プレミアカスタマー**列に多数の空白行が含まれている場合は、**購入金額**列と**注文数量**列を入力として使用して、欠損値を推論できます。</span><span class="sxs-lookup"><span data-stu-id="55264-106">If the  **Premier Customer** column contains many blank rows, you could use the **Purchase Amount** and **Orders Quantity** columns as the inputs, to infer the missing values.</span></span> <span data-ttu-id="55264-107">このツールは、データ内の既存のパターンを、ユーザーが入力したサンプルと組み合わせて分析し、各顧客にどのカテゴリを割り当てるかを予測します。</span><span class="sxs-lookup"><span data-stu-id="55264-107">The tool analyzes existing patterns in the data together with the examples you entered, and predicts which category to assign to each customer.</span></span>  
  
 <span data-ttu-id="55264-108">結果に満足できない場合は、より多くのサンプルを入力することにより、結果の精度を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="55264-108">If you are not satisfied with the results, you can refine the results by providing more examples.</span></span>  
  
## <a name="using-the-fill-from-example-tool"></a><span data-ttu-id="55264-109">自動推論ツールの使用</span><span class="sxs-lookup"><span data-stu-id="55264-109">Using the Fill From Example Tool</span></span>  
  
1.  <span data-ttu-id="55264-110">[**分析**] リボンで、[**例からの塗りつぶし**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55264-110">In the **Analyze** ribbon, click **Fill From Example**.</span></span>  
  
2.  <span data-ttu-id="55264-111">挿入対象となる列は、データの分析に基づいて自動的に選択されますが、それを受け入れるか、別の列を選択するかはユーザーが判断できます。</span><span class="sxs-lookup"><span data-stu-id="55264-111">The tool will automatically pick a column to fill based on analysis of the data, and you can either accept or override this suggestion.</span></span>  
  
3.  <span data-ttu-id="55264-112">新しいデータの列を作成し、予測したいデータのサンプルを入力します。</span><span class="sxs-lookup"><span data-stu-id="55264-112">Create a column for the new data, and type in examples of the data that you want to predict.</span></span> <span data-ttu-id="55264-113">予測する値ごとに、少なくとも 1 つのサンプル データが必要です。</span><span class="sxs-lookup"><span data-stu-id="55264-113">Make sure that there is at least one example for every value that you want to predict.</span></span> <span data-ttu-id="55264-114">既存の列にデータを挿入する場合は、欠損値の存在する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="55264-114">If you are filling in data in an existing column, select the column that has missing values.</span></span>  
  
4.  <span data-ttu-id="55264-115">必要に応じて、[**分析に使用する列の選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55264-115">Optionally, click **Choose columns to be used in analysis**.</span></span> <span data-ttu-id="55264-116">**[高度な列の選択**] ダイアログボックスで、欠損データを入力するときに使用する可能性が最も高い列を指定します。</span><span class="sxs-lookup"><span data-stu-id="55264-116">In the **Advanced Columns Selection** dialog box, specify the columns that are most likely to be useful when filling in the missing data.</span></span>  
  
     <span data-ttu-id="55264-117">たとえば、欠損値の存在する列との間に因果効果のある列が経験的にわかっている場合は、他の列の選択を解除することによって、より精度の高い結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="55264-117">For example, if you know from experience that there is a causal effect between one column and the column that has missing values, you can deselect other columns to get better results.</span></span>  
  
     <span data-ttu-id="55264-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55264-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="55264-119">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55264-119">Click **Run**.</span></span>  
  
     <span data-ttu-id="55264-120">分析が完了すると、分析の結果を含む新しい**パターン**ワークシートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="55264-120">When analysis is complete, the tool creates a new **Patterns** worksheet that contains the results of analysis.</span></span> <span data-ttu-id="55264-121">レポートには、見つかったルール (主要な影響元) が一覧表示され、各ルールの確率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="55264-121">The report lists the rules, or key influencers, that were found, and shows the probability for each rule.</span></span>  
  
     <span data-ttu-id="55264-122">また、新しい値を含む列が、元のデータ テーブルに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="55264-122">The tool also automatically adds a column that contains the new values to the original data table.</span></span> <span data-ttu-id="55264-123">挿入された値を元の状態と比較しながら確認できます。</span><span class="sxs-lookup"><span data-stu-id="55264-123">You can review the values and compare them against the original.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="55264-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="55264-124">Requirements</span></span>  
 <span data-ttu-id="55264-125">処理できるのは、列方向に格納されたデータだけです。</span><span class="sxs-lookup"><span data-stu-id="55264-125">You can only work with data in columns.</span></span> <span data-ttu-id="55264-126">自動推論によって挿入する一連のデータが行として格納されている場合は、Excel の Paste、Transpose 関数を使用して、データを列形式に変換できます。</span><span class="sxs-lookup"><span data-stu-id="55264-126">If the series that you want to fill is stored in a row, you can use the Paste, Transpose function in Excel to change the data to a columnar format.</span></span>  
  
## <a name="understanding-the-pattern-report"></a><span data-ttu-id="55264-127">パターン レポートについて</span><span class="sxs-lookup"><span data-stu-id="55264-127">Understanding the Pattern Report</span></span>  
 <span data-ttu-id="55264-128">[**サンプルからの塗りつぶし**] ツールを実行すると、検出されたパターンに関する詳細情報を提供するレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="55264-128">When you run the **Fill From Example** tool, a report is created that provides more information about the patterns that were detected.</span></span> <span data-ttu-id="55264-129">これらのパターンは、新しいデータ値を推定するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="55264-129">These patterns are used for extrapolating new data values.</span></span>  
  
 <span data-ttu-id="55264-130">パターン レポートには、予測された値ごとに主要な影響元が示されます。</span><span class="sxs-lookup"><span data-stu-id="55264-130">The Pattern Report shows the key influencers for each value that was predicted.</span></span> <span data-ttu-id="55264-131">個々の影響元 (ルール) は、列とその値、および、そのルールの予測に対する相対的影響として表されます。</span><span class="sxs-lookup"><span data-stu-id="55264-131">Each influencer or rule is described as a combination of a column, the value in that column, and the relative impact of the rule on the prediction.</span></span>  
  
 <span data-ttu-id="55264-132">たとえば、注文の配送距離が記されたワークシートに対してデータを挿入しようとする場合、配送距離に強く影響するのは、配送先となる目的地です。</span><span class="sxs-lookup"><span data-stu-id="55264-132">For example, if you were trying to fill in a worksheet that shows the shipping distance for orders, you might logically expect the destination to have a strong impact on the value for shipping distance.</span></span> <span data-ttu-id="55264-133">この場合、レポートには、次のような行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="55264-133">In this case, the report might contain the following row:</span></span>  
  
|<span data-ttu-id="55264-134">列</span><span class="sxs-lookup"><span data-stu-id="55264-134">Column</span></span>|<span data-ttu-id="55264-135">値</span><span class="sxs-lookup"><span data-stu-id="55264-135">Value</span></span>|<span data-ttu-id="55264-136">ライター</span><span class="sxs-lookup"><span data-stu-id="55264-136">Favors</span></span>|<span data-ttu-id="55264-137">相対的影響</span><span class="sxs-lookup"><span data-stu-id="55264-137">Relative Impact</span></span>|  
|------------|-----------|------------|---------------------|  
|<span data-ttu-id="55264-138">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="55264-138">StateProvinceCode</span></span>|<span data-ttu-id="55264-139">AB</span><span class="sxs-lookup"><span data-stu-id="55264-139">AB</span></span>|<span data-ttu-id="55264-140">>500 キロメートル</span><span class="sxs-lookup"><span data-stu-id="55264-140">>500 kilometers</span></span>|<span data-ttu-id="55264-141">80%</span><span class="sxs-lookup"><span data-stu-id="55264-141">80%</span></span>|  
  
 <span data-ttu-id="55264-142">これは、 **StateProvinceCode**列の値 AB が >500 キロメートルの出荷距離を強く予測することを意味します。</span><span class="sxs-lookup"><span data-stu-id="55264-142">This means that the value AB in the **StateProvinceCode** column strongly predicts a shipping distance of >500 kilometers.</span></span>  
  
 <span data-ttu-id="55264-143">通常、ここで示した例よりも、はるかに複雑なパターンに基づいて予測が行われます。したがって、予測ごとに出力されるルールの行数も、もっと多くなります。</span><span class="sxs-lookup"><span data-stu-id="55264-143">Typically, predictions are based on patterns that are far more complex than this example, and the report may contain many rows of rules for each prediction.</span></span> <span data-ttu-id="55264-144">予測値は、こうしたすべてのルールの影響を組み合わせることによって導かれます。</span><span class="sxs-lookup"><span data-stu-id="55264-144">The effect of all the rules are combined to derive the predicted value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55264-145">**相対影響**は、網掛けされたバーとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="55264-145">**Relative Impact** is shown as a shaded bar.</span></span> <span data-ttu-id="55264-146">棒グラフが長いほど、そのルールが、適切な挿入値を予測できる確率が高いことを示します。</span><span class="sxs-lookup"><span data-stu-id="55264-146">The longer the bar, the greater the probability that this rule is predictive of the filled-in value.</span></span>  
  
 <span data-ttu-id="55264-147">また、このツールは、元のデータテーブルに Extended という名前の新しい列を追加し \<column name> ます。</span><span class="sxs-lookup"><span data-stu-id="55264-147">The tool also adds a new column to the original data table, named \<column name> Extended.</span></span>  
  
 <span data-ttu-id="55264-148">元のデータ列に値が存在した場合、その値が、この新しい列にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="55264-148">If the original data column contained a value, that value is copied into the new column.</span></span> <span data-ttu-id="55264-149">ただし、元の列が空白セルであった場合、新しい列には、ウィザードによって予測された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="55264-149">However, if the original column contained a blank cell, the new column contains the value that was predicted by the wizard.</span></span>  
  
## <a name="related-tools-and-information"></a><span data-ttu-id="55264-150">関連ツールと情報</span><span class="sxs-lookup"><span data-stu-id="55264-150">Related Tools and Information</span></span>  
 <span data-ttu-id="55264-151">Excel 用のデータマイニングクライアントに用意されている[データの探索](explore-data-sql-server-data-mining-add-ins.md)ウィザードを使用して、excel の列の値の分布を調べることもできます。</span><span class="sxs-lookup"><span data-stu-id="55264-151">You can also use the [Explore Data](explore-data-sql-server-data-mining-add-ins.md) wizard, available in the Data Mining Client for Excel, to examine the distribution of values in an Excel column.</span></span> <span data-ttu-id="55264-152">詳細については、「[データの探索とクリーニング](exploring-and-cleaning-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55264-152">For more information, see [Exploring and Cleaning Data](exploring-and-cleaning-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55264-153">参照</span><span class="sxs-lookup"><span data-stu-id="55264-153">See Also</span></span>  
 [<span data-ttu-id="55264-154">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="55264-154">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
