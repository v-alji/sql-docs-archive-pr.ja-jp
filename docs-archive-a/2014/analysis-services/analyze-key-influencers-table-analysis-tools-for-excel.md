---
title: 主要な影響元の分析 (Excel 用のテーブル分析ツール) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
ms.openlocfilehash: f60eb5144059b0976d52eec2329f27553132146c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633641"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a><span data-ttu-id="1b972-102">主要な影響元の分析 (Excel 用のテーブル分析ツール)</span><span class="sxs-lookup"><span data-stu-id="1b972-102">Analyze Key Influencers (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="1b972-103">![リボンの [主要な影響元の分析] ボタン](media/tat-aki.gif "リボンの [主要な影響元の分析] ボタン")</span><span class="sxs-lookup"><span data-stu-id="1b972-103">![Analyze Key Influencers button in ribbon](media/tat-aki.gif "Analyze Key Influencers button in ribbon")</span></span>  
  
 <span data-ttu-id="1b972-104">主要な**影響**元の分析ツールでは、ターゲットの結果を含む列を選択すると、その結果に最も強い影響を与える要因がアルゴリズムによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="1b972-104">With the **Analyze Key Influencers** tool, you choose a column that contains a target outcome, and the algorithm determines which factors had the strongest influence on the outcome.</span></span>  
  
 <span data-ttu-id="1b972-105">このツールで作成される新規データ テーブルでは、個別の結果に関連付けられた要因が報告され、関係の可能性がグラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b972-105">The tool creates new data tables that report the factors associated with each outcome and graphically displays the probability of the relationship.</span></span> <span data-ttu-id="1b972-106">さまざまな要因および結果によってテーブルをフィルタリングして、結果を詳しく調べることができます。</span><span class="sxs-lookup"><span data-stu-id="1b972-106">You can filter the tables by different factors and outcomes to explore the results in more depth.</span></span>  
  
 <span data-ttu-id="1b972-107">可能性のある結果のペアを選択して比較することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b972-107">You can also select a pair of possible outcomes and compare them.</span></span> <span data-ttu-id="1b972-108">たとえば、可能な意思決定要因を特定するために、異なる消費者グループを比較します。</span><span class="sxs-lookup"><span data-stu-id="1b972-108">For example, you might compare different groups of consumers to determine possible decision-making factors.</span></span>  
  
## <a name="using-the-analyze-key-influencers-tool"></a><span data-ttu-id="1b972-109">主要な影響元の分析ツールの使用</span><span class="sxs-lookup"><span data-stu-id="1b972-109">Using the Analyze Key Influencers Tool</span></span>  
  
1.  <span data-ttu-id="1b972-110">Excel データ テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1b972-110">Open an Excel data table.</span></span>  
  
2.  <span data-ttu-id="1b972-111">[**テーブルツール**] の [**分析**] リボンで、[主要影響元の分析] をクリックし**ます。**</span><span class="sxs-lookup"><span data-stu-id="1b972-111">In **Table Tools**, on the **Analyze** ribbon, click **Analyze Key Influencers.**</span></span>  
  
3.  <span data-ttu-id="1b972-112">分析のターゲットとして 1 つの列を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b972-112">Select the single column that is the target of analysis.</span></span>  
  
4.  <span data-ttu-id="1b972-113">必要に応じ**て、[分析に使用する列の選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b972-113">Optionally, click **Choose columns to be used for analysis**.</span></span> <span data-ttu-id="1b972-114">**[高度な列の選択**] ダイアログボックスで、関連するデータを格納する可能性が最も高い列を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b972-114">In the **Advanced Columns Selection** dialog box, choose the columns that are most likely to contain relevant data.</span></span> <span data-ttu-id="1b972-115">高いパフォーマンスと精度を確保するため、ID や名前などのパターン分析に重要ではない列を選択解除します。</span><span class="sxs-lookup"><span data-stu-id="1b972-115">To improve performance and accuracy, deselect columns such as ID or name that are unimportant for pattern analysis.</span></span> <span data-ttu-id="1b972-116">[ **OK** ] をクリックして、[**高度な列の選択**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1b972-116">Click **OK** to close the **Advanced Columns Selection** dialog box.</span></span>  
  
5.  <span data-ttu-id="1b972-117">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b972-117">Click **Run**.</span></span>  
  
     <span data-ttu-id="1b972-118">**主要な影響**元の分析ツールは、データの分析を行い、最適な設定を決定し、すべてのパラメーターを自動的に設定します。</span><span class="sxs-lookup"><span data-stu-id="1b972-118">The **Analyze Key Influencers** tool conducts an analysis of the data to determine the optimum settings, and sets all parameters automatically.</span></span>  
  
6.  <span data-ttu-id="1b972-119">パターンが検出されなかった場合は、問題の説明を含む新しいワークシートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1b972-119">If no patterns were detected, the wizard creates a new worksheet that contains a description of the problem.</span></span>  
  
7.  <span data-ttu-id="1b972-120">パターンが検出されると、新しいワークシートにレポートが作成されて、そのパターンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b972-120">If patterns are detected, the wizard creates a report on a new worksheet that shows the patterns.</span></span> <span data-ttu-id="1b972-121">このレポートには、**の主要 \<column> な影響**元という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="1b972-121">The report is named **Key Influencers for \<column>**.</span></span> <span data-ttu-id="1b972-122">この後の手順に従ってレポートをカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1b972-122">You can customize the report as described in the following procedure.</span></span>  
  
#### <a name="create-a-custom-report"></a><span data-ttu-id="1b972-123">カスタム レポートの作成</span><span class="sxs-lookup"><span data-stu-id="1b972-123">Create a custom report</span></span>  
  
1.  <span data-ttu-id="1b972-124">**[主要な影響元に基づく識別**] ダイアログボックスで、[**値 1** ] と [**値 2** ] のドロップダウンリストから比較する2つの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b972-124">In the **Discrimination based on key influencers** dialog box, choose the two values that you want to compare by selecting them from the **Value 1** and **Value 2** dropdown lists.</span></span> <span data-ttu-id="1b972-125">たとえば、購入者と非購入者を比較できます。</span><span class="sxs-lookup"><span data-stu-id="1b972-125">For example, you might compare buyers to non-buyers.</span></span>  
  
2.  <span data-ttu-id="1b972-126">[**レポートの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b972-126">Click **Add Report**.</span></span>  
  
     <span data-ttu-id="1b972-127">このウィザードは、新規ワークシートを作成し、主要な要因の比較の各ペアに対するテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="1b972-127">The wizard creates a new worksheet and adds a table for each pair of key factor comparisons.</span></span>  
  
3.  <span data-ttu-id="1b972-128">比較が完了したら、[**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b972-128">When you are done making comparisons, click **Close**.</span></span>  
  
## <a name="understanding-the-key-influencers-report"></a><span data-ttu-id="1b972-129">主要な影響元レポートについて</span><span class="sxs-lookup"><span data-stu-id="1b972-129">Understanding the Key Influencers Report</span></span>  
 <span data-ttu-id="1b972-130">データモデルが作成されると、主要な影響元の**分析**ツールによってレポートが作成され、主要な影響元を調査して比較するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1b972-130">After the data model has been created, the **Analyze Key Influencers** tool creates reports that help you explore and compare key influencers.</span></span>  
  
-   <span data-ttu-id="1b972-131">左側にあるレポートは、既定で生成されるレポートです。</span><span class="sxs-lookup"><span data-stu-id="1b972-131">The report on the left side is the one generated by default.</span></span> <span data-ttu-id="1b972-132">結果の列 (従属変数) で最も強力な予測子を示します。</span><span class="sxs-lookup"><span data-stu-id="1b972-132">It shows the strongest predictors of the outcome column (the dependent variable).</span></span>  
  
-   <span data-ttu-id="1b972-133">右側にあるレポートはオプションで、2 つの特定の結果値を比較することで作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b972-133">The report on the right side is optional, which you can create by comparing two specific outcome values.</span></span> <span data-ttu-id="1b972-134">このレポートは、購入者と非購入者を比較します。</span><span class="sxs-lookup"><span data-stu-id="1b972-134">This report compares buyers and non-buyers.</span></span>  
  
-   <span data-ttu-id="1b972-135">作成したレポートごとに新しいワークシートが追加されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1b972-135">Note that a new worksheet is added for each report that you create.</span></span> <span data-ttu-id="1b972-136">テーブルは作成後に移動することができます。ここでは、比較のためにテーブルを並べて配置しています。</span><span class="sxs-lookup"><span data-stu-id="1b972-136">You can move the tables after they are created; we placed them side by side for comparison.</span></span>  
  
 <span data-ttu-id="1b972-137">![DM13](media/dm13-tat-aki-report.gif "DM13")</span><span class="sxs-lookup"><span data-stu-id="1b972-137">![DM13](media/dm13-tat-aki-report.gif "DM13")</span></span>  
  
 <span data-ttu-id="1b972-138">**相対的影響**</span><span class="sxs-lookup"><span data-stu-id="1b972-138">**Relative Impact**</span></span>  
 <span data-ttu-id="1b972-139">最初のレポートの網掛けされたバーは、この属性と結果とのアソシエーションの強さを示します。</span><span class="sxs-lookup"><span data-stu-id="1b972-139">The shaded bar in the first report indicates the strength of the association of this attribute with the outcome.</span></span>  
  
 <span data-ttu-id="1b972-140">バーの長さは、要因が結果に影響する可能性を示しており、網掛けされたバーが長いほど、アソシエーションが強いことを表しています。</span><span class="sxs-lookup"><span data-stu-id="1b972-140">The length of the bar indicates the probability that the factor contributes to the outcome; therefore, the longer the shaded bar, the stronger the association.</span></span>  
  
 <span data-ttu-id="1b972-141">**ライター**</span><span class="sxs-lookup"><span data-stu-id="1b972-141">**Favors**</span></span>  
 <span data-ttu-id="1b972-142">2 つ目のレポートでは、比較するターゲット値が 2 列に表示され、関連要因が信頼スコアの降順に並べられます。</span><span class="sxs-lookup"><span data-stu-id="1b972-142">In the second report, the target values that you compare are listed in two columns, with the related factors listed in order of descending confidence.</span></span>  
  
-   <span data-ttu-id="1b972-143">**青色**のバーは、結果に寄与する属性を示します。 "No" (= は購入されませんでした)。</span><span class="sxs-lookup"><span data-stu-id="1b972-143">The **blue** bar shows attributes contributing to the outcome, "No" (=did not purchase).</span></span>  
  
-   <span data-ttu-id="1b972-144">**赤色**のバーは、"Yes" (自転車を購入) という結果に貢献する属性を示しています。</span><span class="sxs-lookup"><span data-stu-id="1b972-144">The **red** bar shows attributes contributing to the outcome, "Yes" (=purchased a bike).</span></span>  
  
 <span data-ttu-id="1b972-145">網掛けされたバーの色は任意です。</span><span class="sxs-lookup"><span data-stu-id="1b972-145">The colors in the shading bar are arbitrary.</span></span> <span data-ttu-id="1b972-146">Excel でテーブル デザインのオプションを設定すると色を変更できます。</span><span class="sxs-lookup"><span data-stu-id="1b972-146">You can change these colors by setting the options for table design in Excel.</span></span>  
  
 <span data-ttu-id="1b972-147">2 つの値を比較するレポートの場合、その 2 つ目のレポートでは、ターゲット値に対する影響の強さで主要な影響元が順位付けされます。</span><span class="sxs-lookup"><span data-stu-id="1b972-147">In a report that contrasts two values, the second report ranks the key influencers by the amount of impact on the target values.</span></span>  
  
 <span data-ttu-id="1b972-148">すべてのグラフは Excel のテーブルを基にしているため、フィルター処理と並べ替えによって特定の要因または結果に注目することができます。</span><span class="sxs-lookup"><span data-stu-id="1b972-148">Because all the charts are based on Excel tables, you can filter and sort to focus on specific factors or outcomes.</span></span>  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a><span data-ttu-id="1b972-149">主要な影響元の分析ツールの詳細</span><span class="sxs-lookup"><span data-stu-id="1b972-149">More About the Analyze Key Influencers Tool</span></span>  
 <span data-ttu-id="1b972-150">**主要影響**元の分析ツールによってデータが分析されると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1b972-150">When the **Analyze Key Influencers** tool analyzes your data, it does the following:</span></span>  
  
-   <span data-ttu-id="1b972-151">データの分布に関する主要な情報を格納するデータ構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="1b972-151">Creates a data structure that stores key information about the distribution of your data.</span></span>  
  
-   <span data-ttu-id="1b972-152">Microsoft Na&amp;#239;&lt;/ph&gt;ve Bayes アルゴリズムを使用して、モデルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1b972-152">Creates a model using the Microsoft Naïve Bayes algorithm.</span></span>  
  
-   <span data-ttu-id="1b972-153">データの各列を指定した結果に関連付ける予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="1b972-153">Creates predictions that correlates each column of data with the specified outcome.</span></span>  
  
-   <span data-ttu-id="1b972-154">予測ごとの信頼スコアを使用して、目標の結果を得るうえで最も影響を与える要因を識別します。</span><span class="sxs-lookup"><span data-stu-id="1b972-154">Uses the confidence score for each of the predictions to identify the factors that are the most influential in producing the targeted outcome.</span></span>  
  
-   <span data-ttu-id="1b972-155">信頼スコア順に並べ替えて、主要な影響元を記述したレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b972-155">Creates a report describing the key influencers, ordered by confidence scores.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="1b972-156">必要条件</span><span class="sxs-lookup"><span data-stu-id="1b972-156">Requirements</span></span>  
 <span data-ttu-id="1b972-157">ターゲット列に連続する数値が含まれている場合、このツールは自動的に数値をグループにセグメント化します。</span><span class="sxs-lookup"><span data-stu-id="1b972-157">If the target column contains continuous numeric values, the tool automatically segments the numeric values into groups.</span></span> <span data-ttu-id="1b972-158">これらのグループは、類似の特性を持つケースのクラスターを表します。</span><span class="sxs-lookup"><span data-stu-id="1b972-158">These groupings represent clusters of cases that have similar characteristics.</span></span> <span data-ttu-id="1b972-159">ただし、ユーザーにとってわかりやすいグループになるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="1b972-159">However, numeric values might not be divided into user-friendly groups.</span></span> <span data-ttu-id="1b972-160">たとえば、レポートに "12.85701" などのグループが含まれているとし \< ます。一方、通常、レポートユーザーは、10-19、20-29 など、整数を使用するグループを表示します。</span><span class="sxs-lookup"><span data-stu-id="1b972-160">For example, the report might contain a grouping such as "\<12.85701", whereas report users typically like to see groupings that use whole numbers, such as 10-19, 20-29, and so on.</span></span>  
  
 <span data-ttu-id="1b972-161">数値データを異なる方法でグループ化する場合は、分析を作成する前にデータを必要な形にセグメント化しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b972-161">If you want to group numeric data in a different way, you must segment the data the way you want before creating the analysis.</span></span> <span data-ttu-id="1b972-162">たとえば、Excel 用のデータマイニングクライアントのラベルの[書き換え](relabel-sql-server-data-mining-add-ins.md)ツールを使用して、別の列に新しいグループ化ラベルを作成し、その新しい列のみを分析で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1b972-162">For example, you can use the [Relabel](relabel-sql-server-data-mining-add-ins.md) tool in the Data Mining Client for Excel to create a new grouping label in a separate column, and then use only that new column in analysis.</span></span>  
  
### <a name="related-tools"></a><span data-ttu-id="1b972-163">関連ツール</span><span class="sxs-lookup"><span data-stu-id="1b972-163">Related Tools</span></span>  
 <span data-ttu-id="1b972-164">[**データマイニング**] リボンには、データマイニングモデルをカスタマイズする機能など、より高度なツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1b972-164">The **Data Mining** ribbon provides more advanced tools, including the ability to customize data mining models</span></span>  
  
 <span data-ttu-id="1b972-165">**主要な影響**元の分析ツールを使用してモデルを保存する場合は、データマイニングクライアントを使用して、モデルを参照し、リレーションシップを詳細に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="1b972-165">If you save your model by using the **Analyze Key Influencers** tool, you can use the Data Mining Client to browse the model and explore relationships in more detail.</span></span> <span data-ttu-id="1b972-166">詳細については、「 [Excel でのモデルの参照 &#40;SQL Server データマイニングアドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b972-166">For information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span> <span data-ttu-id="1b972-167">Microsoft Office Visio を使用し、関係をクラスターまたは依存関係ネットワークとして示すグラフおよびダイアグラムを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b972-167">You can also use Microsoft Office Visio to create charts and diagrams that display the relationships as cluster or as dependency networks.</span></span> <span data-ttu-id="1b972-168">詳細については、「 [SQL Server データマイニングアドイン&#41;&#40;Visio データマイニング図のトラブルシューティング](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b972-168">For more information, see [Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b972-169">テーブル分析ツールを使用しているときに作成されたモデルは、ワークシートを閉じたとき、または、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーとの接続を終了したときに削除されます。</span><span class="sxs-lookup"><span data-stu-id="1b972-169">The models that are created when you use the Table Analysis Tools are deleted when you close your worksheet or terminate the connection with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="1b972-170">したがって、それらのモデルを参照できるのは、接続が開いている間だけです。</span><span class="sxs-lookup"><span data-stu-id="1b972-170">Therefore, you can only browse the models as long as the connection remains open.</span></span> <span data-ttu-id="1b972-171">接続を閉じたりワークシートを閉じたりすると、モデルを Visio で表示することもできなくなります。</span><span class="sxs-lookup"><span data-stu-id="1b972-171">You cannot render the models in Visio if you close the connection or close the worksheet.</span></span>  
  
 <span data-ttu-id="1b972-172">**主要な影響**元の分析ツールで使用されるアルゴリズムの詳細については、SQL Server オンラインブックの「Microsoft の単純な Bayes アルゴリズム」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b972-172">For more information about the algorithm used by the **Analyze Key Influencers** tool, see "Microsoft Naïve Bayes Algorithm" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b972-173">参照</span><span class="sxs-lookup"><span data-stu-id="1b972-173">See Also</span></span>  
 <span data-ttu-id="1b972-174">[Excel 用のテーブル分析ツール](table-analysis-tools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="1b972-174">[Table Analysis Tools for Excel](table-analysis-tools-for-excel.md) </span></span>  
 [<span data-ttu-id="1b972-175">データ マイニング モデルの作成</span><span class="sxs-lookup"><span data-stu-id="1b972-175">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
