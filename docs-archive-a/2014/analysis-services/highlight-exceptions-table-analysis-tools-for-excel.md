---
title: 例外の強調表示 (Excel 用のテーブル分析ツール) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97e8197fc76f431cf9740c5c6fbd7ac44d8204a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740591"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a><span data-ttu-id="00130-102">例外の強調表示 (Excel 用のテーブル分析ツール)</span><span class="sxs-lookup"><span data-stu-id="00130-102">Highlight Exceptions (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="00130-103">![リボンの [例外の強調表示] ボタン](media/tat-highlightex.gif "リボンの [例外の強調表示] ボタン")</span><span class="sxs-lookup"><span data-stu-id="00130-103">![Highlight Exceptions button in ribbon](media/tat-highlightex.gif "Highlight Exceptions button in ribbon")</span></span>  
  
 <span data-ttu-id="00130-104">時には、データに例外的な値が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="00130-104">Sometimes your data might contain peculiar values.</span></span> <span data-ttu-id="00130-105">たとえば、住宅所有者の年齢が "5 歳" と表示されているとします。</span><span class="sxs-lookup"><span data-stu-id="00130-105">For example, a homeowner's age might be listed as five years old.</span></span> <span data-ttu-id="00130-106">これらの値 (多くの場合、*外れ*値と呼ばれます) は、データ入力エラーのために間違っているか、異常な傾向を示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00130-106">These values, often called *outliers*, might be wrong because of a data input error, or they might indicate unusual trends.</span></span> <span data-ttu-id="00130-107">どちらにしても、例外は分析の質に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00130-107">Either way, exceptions can affect the quality of your analysis.</span></span> <span data-ttu-id="00130-108">[**例外の強調表示**] ツールを使用すると、これらの値を見つけて、さらにアクションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="00130-108">The **Highlight Exceptions** tool helps you find these values and review them for further action.</span></span>  
  
 <span data-ttu-id="00130-109">**例外の強調表示**ツールは、Excel データテーブル内のデータの範囲全体を操作できます。または、少数の列のみを選択できます。</span><span class="sxs-lookup"><span data-stu-id="00130-109">The **Highlight Exceptions** tool can work with the entire range of data in an Excel data table, or you can select only a few columns.</span></span> <span data-ttu-id="00130-110">しきい値を変更してデータの揺れを考慮し、検出する例外の数を調整することもできます。</span><span class="sxs-lookup"><span data-stu-id="00130-110">You can also adjust a threshold that controls the variability of data, to find more or fewer exceptions.</span></span>  
  
 <span data-ttu-id="00130-111">例外の強調表示ツールでは分析が完了すると新しいワークシートが作成され、分析対象の各列に見つかった外れ値の数を示すサマリー レポートが出力されます。</span><span class="sxs-lookup"><span data-stu-id="00130-111">When the tool completes its analysis, it creates a new worksheet that contains a summary report of how many outliers were found in each of the columns that you analyzed.</span></span> <span data-ttu-id="00130-112">また、元のデータ テーブルに存在する例外も強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="00130-112">The tool also highlights the exceptions in the original data table.</span></span> <span data-ttu-id="00130-113">このツールでは、全体の傾向が分析されるため、特定の行のほとんどの値は通常値で、その行の単一のセルだけが強調表示される、ということもあります。</span><span class="sxs-lookup"><span data-stu-id="00130-113">Because the tool analyzes overall trends, it might find that most of the values in a row are normal, and highlight only one cell in that row.</span></span> <span data-ttu-id="00130-114">上記の住宅所有者の例では、 **Age**列だけが強調表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="00130-114">In the homeowner example above, only the **Age** column might be highlighted.</span></span>  
  
 <span data-ttu-id="00130-115">また、**概要レポート**で**例外のしきい**値を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="00130-115">You can also change the **Exception threshold** value in the **Summary Report**.</span></span> <span data-ttu-id="00130-116">この値は、特定のセルに外れ値が含まれる確率を示します。</span><span class="sxs-lookup"><span data-stu-id="00130-116">This value indicates the probability that a particular cell contains an abnormal value.</span></span> <span data-ttu-id="00130-117">したがって、しきい値を上げることにより、外れ値として強調表示される値の数が減ります。</span><span class="sxs-lookup"><span data-stu-id="00130-117">Therefore, if you increase the value, fewer values will be highlighted as outliers.</span></span> <span data-ttu-id="00130-118">逆に、しきい値を下げた場合、強調表示されるセルの数は増えます。</span><span class="sxs-lookup"><span data-stu-id="00130-118">Conversely, when you decrease the value, you will see more highlighted cells.</span></span>  
  
## <a name="using-the-highlight-exceptions-tool"></a><span data-ttu-id="00130-119">例外の強調表示ツールの使用</span><span class="sxs-lookup"><span data-stu-id="00130-119">Using the Highlight Exceptions Tool</span></span>  
  
1.  <span data-ttu-id="00130-120">Excel テーブルを開き、[**例外の強調表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00130-120">Open an Excel table and click **Highlight Exceptions**.</span></span>  
  
2.  <span data-ttu-id="00130-121">分析する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="00130-121">Specify the columns to analyze.</span></span>  
  
3.  <span data-ttu-id="00130-122">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00130-122">Click **Run**.</span></span>  
  
4.  <span data-ttu-id="00130-123">外れ値というタイトルのワークシートを開いて、 \<table name> 検出された外れ値の概要を表示します。</span><span class="sxs-lookup"><span data-stu-id="00130-123">Open the worksheet titled \<table name> Outliers to view a summary of the outliers that were found.</span></span>  
  
5.  <span data-ttu-id="00130-124">ハイライトの数を変更するには、[例外の**強調表示] レポート**の [**例外のしきい値**] 行にある上下の矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00130-124">To change the number of highlights, click the up and down arrows in the **Exception Threshold** row of the **Highlight Exceptions Report**.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="00130-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="00130-125">Requirements</span></span>  
 <span data-ttu-id="00130-126">外れ値が含まれていない列でも、その値が他の行の予測に貢献するのであれば、検出対象に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="00130-126">You can include columns that do not contain bad values if these values contain information that might be useful in predicting other rows.</span></span> <span data-ttu-id="00130-127">しかし、欠損値をあまりにも多く含む列については、選択を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00130-127">However, you should deselect columns that have many missing or zero values.</span></span>  
  
 <span data-ttu-id="00130-128">選択したすべての列が、一般的なパターンの作成に使用されるので、次のような適切でない情報を含む入力列は使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="00130-128">Because all of the selected columns are used to create a general pattern, you should avoid using input columns that you know to have poor information, such as the following:</span></span>  
  
-   <span data-ttu-id="00130-129">ID などの一意な値を含む列。</span><span class="sxs-lookup"><span data-stu-id="00130-129">Columns that contain unique values such as IDs.</span></span>  
  
-   <span data-ttu-id="00130-130">間違った値の割合が高い列。</span><span class="sxs-lookup"><span data-stu-id="00130-130">Columns that contain a high percentage of wrong values.</span></span>  
  
-   <span data-ttu-id="00130-131">欠損値が多い列。</span><span class="sxs-lookup"><span data-stu-id="00130-131">Columns with many missing values.</span></span>  
  
     <span data-ttu-id="00130-132">欠損値が多い列を入力列として含めると有効な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="00130-132">Note that there are some cases where it is useful to include input columns that have many missing values.</span></span> <span data-ttu-id="00130-133">たとえば、小売り店で顧客が買い物をしたときに必ず住所フィールドの値が欠落する場合は、データ マイニング アルゴリズムはこの情報を使用して他の類似の顧客を識別することができます。</span><span class="sxs-lookup"><span data-stu-id="00130-133">For example, if the value of the address field is always missing when the customer buys through a retailer, the data mining algorithm can use this information to identify other similar customers.</span></span> <span data-ttu-id="00130-134">データが省略によって欠落しているのか、それとも欠落状態に意味があるのかを、ケースごとに判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00130-134">You must determine on a case-by-case basis whether data is missing by omission or because the Missing state is meaningful.</span></span>  
  
-   <span data-ttu-id="00130-135">パターンの作成にほとんど役立たない列。</span><span class="sxs-lookup"><span data-stu-id="00130-135">Columns that are unlikely to be useful in creating a pattern.</span></span> <span data-ttu-id="00130-136">たとえば、すべての行の値が同じである列は、パターンの作成に役立つ情報となりません。</span><span class="sxs-lookup"><span data-stu-id="00130-136">For example, a column that has the same value in every row adds no information that would be useful in building patterns.</span></span>  
  
## <a name="understanding-the-highlight-exceptions-report"></a><span data-ttu-id="00130-137">例外の強調表示レポートについて</span><span class="sxs-lookup"><span data-stu-id="00130-137">Understanding the Highlight Exceptions Report</span></span>  
 <span data-ttu-id="00130-138">[実行] をクリックすると、次の3つの処理が**実行**されます。</span><span class="sxs-lookup"><span data-stu-id="00130-138">When you click **Run**, the tool does three things:</span></span>  
  
-   <span data-ttu-id="00130-139">テーブル内の最新のデータに基づいてデータ マイニング構造を作成する。</span><span class="sxs-lookup"><span data-stu-id="00130-139">Creates a data mining structure based on the current data in the table.</span></span>  
  
-   <span data-ttu-id="00130-140">[!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムを使って新しいデータ マイニング モデルを作成する。</span><span class="sxs-lookup"><span data-stu-id="00130-140">Creates a new data mining model by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
-   <span data-ttu-id="00130-141">パターンに基づく予測クエリを作成し、ワークシートに、あり得ない値が存在するかどうかを調べる。</span><span class="sxs-lookup"><span data-stu-id="00130-141">Creates a prediction query based on the patterns to determine whether any values in the worksheet are improbable.</span></span>  
  
 <span data-ttu-id="00130-142">例外のしきい値の初期値は常に 75 になります (つまり、75% の確率でデータに誤りがあるとアルゴリズムが計算した場合に、そのデータが強調表示されます)。</span><span class="sxs-lookup"><span data-stu-id="00130-142">The initial value for the exception threshold is always 75, meaning that the algorithm calculated there is a 75% chance that the highlighted data is wrong.</span></span> <span data-ttu-id="00130-143">初回分析パスについては、このしきい値が自動的に設定されますが、レポートで値を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="00130-143">The tool automatically sets this threshold for the initial analysis pass, but you can change the value in the report.</span></span>  
  
 <span data-ttu-id="00130-144">[**例外の強調表示**] ツールは、元のデータテーブルの疑わしいデータを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="00130-144">The **Highlight Exceptions** tool highlights cells in the original data table that are suspicious.</span></span> <span data-ttu-id="00130-145">注意を要する行は、濃い色で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="00130-145">Dark highlighting means the row needs attention.</span></span> <span data-ttu-id="00130-146">特定のセルの値が異常値として検出された場合は、明るい色で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="00130-146">Bright highlighting means the value in that particular cell was identified as suspect.</span></span> <span data-ttu-id="00130-147">例外のしきい値を変更すると、それに応じて強調表示される値も変わります。</span><span class="sxs-lookup"><span data-stu-id="00130-147">If you change the threshold for the exceptions, the highlighted values will change accordingly.</span></span>  
  
 <span data-ttu-id="00130-148">サマリー グラフには、例外のしきい値を超えたセルの数が列単位で表示されます。</span><span class="sxs-lookup"><span data-stu-id="00130-148">The summary chart shows the number of cells in each column that were above the exception threshold.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="00130-149">関連ツール</span><span class="sxs-lookup"><span data-stu-id="00130-149">Related Tools</span></span>  
 <span data-ttu-id="00130-150">データ マイニングに備えてデータを消去または確認する段階で、Excel 用のデータ マイニング クライアントのデータ探索機能を利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="00130-150">When you are cleaning or reviewing data in preparation for data mining, you might also try the data exploration features in the Data Mining Client for Excel.</span></span> <span data-ttu-id="00130-151">このアドインには、外れ値を検出したり、データのラベルを変更したり、データの分布を確認したりするための、より高度なツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="00130-151">This add-in provides more advanced tools to help you find outliers, relabel data, or view the distribution of data.</span></span> <span data-ttu-id="00130-152">Excel 用のデータマイニングクライアントのデータ探索ツールの詳細については、「[データの探索とクリーンアップ](exploring-and-cleaning-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00130-152">For more information about data exploration tools in the Data Mining Client for Excel, see [Exploring and Cleaning Data](exploring-and-cleaning-data.md).</span></span>  
  
 <span data-ttu-id="00130-153">**例外の強調表示**ツールでは、クラスタリングアルゴリズムが使用され [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="00130-153">The **Highlight Exceptions** tool uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="00130-154">クラスター モデルにより、似た特性を共有する行グループが検出されます。</span><span class="sxs-lookup"><span data-stu-id="00130-154">A clustering model detects groups of rows that share similar characteristics.</span></span> <span data-ttu-id="00130-155">Excel 用のデータマイニングクライアントには、グラフと特性プロファイルを使用して、クラスタリングによって作成されたデータマイニングモデルを調べるための [**参照**] ウィンドウが用意されています。</span><span class="sxs-lookup"><span data-stu-id="00130-155">The Data Mining Client for Excel provides a **Browse** window that uses graphs and characteristic profiles to let you explore data mining models created by clustering.</span></span> <span data-ttu-id="00130-156">[**例外の強調表示**] ツールによって作成されたクラスターモデルを参照する方法については、「[モデルの参照 (Excel 用データマイニングクライアント)](highlight-exceptions-table-analysis-tools-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00130-156">For information about how to browse the clustering model created by the **Highlight Exceptions** tool, see [Browse Models (Data Mining Client for Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).</span></span>  
  
 <span data-ttu-id="00130-157">[!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムの詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックの「Microsoft クラスタリング アルゴリズム」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00130-157">For more information about the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm, see the topic "Microsoft Clustering Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00130-158">参照</span><span class="sxs-lookup"><span data-stu-id="00130-158">See Also</span></span>  
 [<span data-ttu-id="00130-159">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="00130-159">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
