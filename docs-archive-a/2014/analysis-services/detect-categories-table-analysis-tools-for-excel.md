---
title: カテゴリの検出 (Excel 用のテーブル分析ツール) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4874c85d7e4ab65716741e8ae9433406dfb08b74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737182"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a><span data-ttu-id="f48c7-102">カテゴリの検出 (Excel 用のテーブル分析ツール)</span><span class="sxs-lookup"><span data-stu-id="f48c7-102">Detect Categories (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="f48c7-103">![リボンの [カテゴリの検出] ボタン](media/tat-detectcat.gif "リボンの [カテゴリの検出] ボタン")</span><span class="sxs-lookup"><span data-stu-id="f48c7-103">![Detect Categories button in ribbon](media/tat-detectcat.gif "Detect Categories button in ribbon")</span></span>

 <span data-ttu-id="f48c7-104">**カテゴリの検出**ツールは、類似した特性を持つテーブル内の行を自動的に検出します。</span><span class="sxs-lookup"><span data-stu-id="f48c7-104">The **Detect Categories** tool automatically finds rows in a table that have similar characteristics.</span></span>

 <span data-ttu-id="f48c7-105">このツールの処理が完了すると、検出されたカテゴリおよびその特徴を示すレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-105">When the tool finishes, it creates a report that lists the categories it found, together with their distinguishing characteristics.</span></span> <span data-ttu-id="f48c7-106">既定では、データの行ごとに、検出されたカテゴリを含む新しい列がデータ テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-106">By default, it adds a new column to the data table that contains the proposed category for each row of your data.</span></span> <span data-ttu-id="f48c7-107">後でそのカテゴリを確認し、名前を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-107">You can then review the categories and rename them.</span></span>

## <a name="using-the-detect-categories-tool"></a><span data-ttu-id="f48c7-108">カテゴリの検出ツールの使用</span><span class="sxs-lookup"><span data-stu-id="f48c7-108">Using the Detect Categories Tool</span></span>

1.  <span data-ttu-id="f48c7-109">Excel テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-109">Open an Excel table.</span></span>

2.  <span data-ttu-id="f48c7-110">[**カテゴリの検出**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f48c7-110">Click **Detect Categories**.</span></span>

3.  <span data-ttu-id="f48c7-111">分析に使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="f48c7-111">Specify the columns to use in analysis.</span></span> <span data-ttu-id="f48c7-112">個人名やレコード ID などの一意な値を含む列は分析に役立たないため、選択を外すことができます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-112">You can deselect columns that have distinct values, such as personal names or record IDs, because these columns might not be useful for analysis.</span></span>

4.  <span data-ttu-id="f48c7-113">作成するカテゴリの最大数を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-113">Optionally, specify the maximum number of categories to create.</span></span> <span data-ttu-id="f48c7-114">既定では、検出された数のカテゴリが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-114">By default, the tool automatically creates as many categories as it finds.</span></span>

5.  <span data-ttu-id="f48c7-115">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f48c7-115">Click **Run**.</span></span>

6.  <span data-ttu-id="f48c7-116">カテゴリとその特性の一覧が記載された "カテゴリのレポート" という名前の新規ワークシートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-116">The tool creates a new worksheet, named Categories Report, which contains the list of categories and their characteristics.</span></span>

 <span data-ttu-id="f48c7-117">ツールのオプションを指定する方法の詳細については、「[[カテゴリの検出] ダイアログボックス (Excel 用のテーブル分析ツール)](detect-categories-table-analysis-tools-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f48c7-117">For more information about how to specify options for the tool, see [Detect Categories Dialog Box (Table Analysis Tools for Excel)](detect-categories-table-analysis-tools-for-excel.md).</span></span>

## <a name="understanding-the-categories-report"></a><span data-ttu-id="f48c7-118">カテゴリのレポートについて</span><span class="sxs-lookup"><span data-stu-id="f48c7-118">Understanding the Categories Report</span></span>
 <span data-ttu-id="f48c7-119">**カテゴリレポート**には、**カテゴリ一覧**とカテゴリ**特性**の2つのテーブルと**カテゴリプロファイル**グラフが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f48c7-119">The **Categories Report** contains two tables, **Category List** and **Category Characteristics**, and a **Category Profiles** chart.</span></span>

### <a name="category-list"></a><span data-ttu-id="f48c7-120">カテゴリの一覧</span><span class="sxs-lookup"><span data-stu-id="f48c7-120">Category List</span></span>
 <span data-ttu-id="f48c7-121">最初のテーブルは、検出されたカテゴリを示します。</span><span class="sxs-lookup"><span data-stu-id="f48c7-121">The first table lists the categories that were found.</span></span> <span data-ttu-id="f48c7-122">[**行数**] 列には、各カテゴリに割り当てられたデータ行の数が示されます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-122">The **Row Count** column indicates how many rows of data were assigned to each category.</span></span>

 <span data-ttu-id="f48c7-123">モデルは、各カテゴリに対応する一時的な名前を作成しますが、カテゴリを好みの名前に変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-123">The model creates temporary names for each category, but you can rename the categories as you like.</span></span> <span data-ttu-id="f48c7-124">たとえば、次の例では、最初のカテゴリの名前が **"低"** に変更されています。これは、クラスターの最上位の属性であるためです。</span><span class="sxs-lookup"><span data-stu-id="f48c7-124">For example, in the following example, the first category has been renamed **Low Income**, because that was the top attribute of the cluster.</span></span>

 <span data-ttu-id="f48c7-125">![カテゴリの検出ツールによって作成されたレポート](media/dm13-tat-detectcat-report1.gif "カテゴリの検出ツールによって作成されたレポート")</span><span class="sxs-lookup"><span data-stu-id="f48c7-125">![report created by Detect Categories tool](media/dm13-tat-detectcat-report1.gif "report created by Detect Categories tool")</span></span>

 <span data-ttu-id="f48c7-126">新しいラベルを入力するとすぐに、その他のすべてのグラフのほかに、ソース データのワークシートに追加されたカテゴリの一覧にも反映されます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-126">As soon as you type the new label, the change is propagated to all the other charts as well as to the category list added in the source data worksheet.</span></span>

### <a name="category-characteristics"></a><span data-ttu-id="f48c7-127">カテゴリの特性</span><span class="sxs-lookup"><span data-stu-id="f48c7-127">Category Characteristics</span></span>
 <span data-ttu-id="f48c7-128">2番目のテーブル [**カテゴリの特性**] には、各カテゴリの種類の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-128">The second table, **Category Characteristics**, shows details about the makeup of each category.</span></span> <span data-ttu-id="f48c7-129">[**カテゴリ**] 列の上部にある [**フィルター** ] ボタンをクリックして、1つまたは少数のカテゴリにフォーカスを移動します。</span><span class="sxs-lookup"><span data-stu-id="f48c7-129">Click the **Filter** button at the top of the **Category** column to see focus on one or just a few categories.</span></span>

 <span data-ttu-id="f48c7-130">![カテゴリの検出ツールによって作成されたレポート](media/dm13-tat-detectcat-report2.gif "カテゴリの検出ツールによって作成されたレポート")</span><span class="sxs-lookup"><span data-stu-id="f48c7-130">![report created by Detect Categories tool](media/dm13-tat-detectcat-report2.gif "report created by Detect Categories tool")</span></span>

 <span data-ttu-id="f48c7-131">列の網掛け (**相対的な重要度**) は、属性と値の組み合わせが区別要因としてどの程度重要であるかを示します。</span><span class="sxs-lookup"><span data-stu-id="f48c7-131">The shading in the column, **Relative Importance**, indicates how important that combination of attribute and value is as a distinguishing factor.</span></span> <span data-ttu-id="f48c7-132">バーが長いほど、そのカテゴリの代表的な属性である可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="f48c7-132">The longer the bar, the more likely it is that this attribute is strongly representative of this category.</span></span>

### <a name="categories-profile-chart"></a><span data-ttu-id="f48c7-133">カテゴリ プロファイル グラフ</span><span class="sxs-lookup"><span data-stu-id="f48c7-133">Categories Profile Chart</span></span>
 <span data-ttu-id="f48c7-134">**カテゴリレポート**ワークシートの最後のグラフである "**カテゴリプロファイル**" は対話型の**ピボットグラフ**であり、フィールドの並べ替えと非表示、値のフィルター処理、およびグラフの外観のカスタマイズに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-134">The final chart in the **Categories Report** worksheet, **Category Profiles**, is an interactive **Pivot Chart** that you can use to rearrange and hide fields, filter on values, and customize the chart's appearance.</span></span>

 <span data-ttu-id="f48c7-135">Excel 2013 では、グラフのデザインを簡単に改善するための**グラフのスタイル**と**グラフ要素**のコントロールがデザイン画面に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f48c7-135">Excel 2013 now provides **Chart Styles** and **Chart Elements** controls right in the design surface that make it easy to improve the chart design.</span></span>

 <span data-ttu-id="f48c7-136">![カテゴリの検出ツールによって作成されたレポート](media/dm13-tat-detectcat-report3.gif "カテゴリの検出ツールによって作成されたレポート")</span><span class="sxs-lookup"><span data-stu-id="f48c7-136">![report created by Detect Categories tool](media/dm13-tat-detectcat-report3.gif "report created by Detect Categories tool")</span></span>

## <a name="requirements"></a><span data-ttu-id="f48c7-137">必要条件</span><span class="sxs-lookup"><span data-stu-id="f48c7-137">Requirements</span></span>
 <span data-ttu-id="f48c7-138">**カテゴリの検出**ツールには、データの量や種類に関する要件はありません。</span><span class="sxs-lookup"><span data-stu-id="f48c7-138">The **Detect Categories** tool has no requirements for the amount or type of data.</span></span>

> [!NOTE]
>  <span data-ttu-id="f48c7-139">[**カテゴリの検出**] ツールを使用すると、元のデータテーブルに新しい列 Category が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-139">When you use the **Detect Categories** tool, it creates a new column, Category, in the original data table.</span></span> <span data-ttu-id="f48c7-140">データ テーブルにこの列を残したままデータ マイニング処理を実行すると、この列が結果に影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="f48c7-140">If you leave this column in the data table and then perform subsequent data mining operations, the presence of this column could influence your results.</span></span> <span data-ttu-id="f48c7-141">他の処理に影響を及ぼさないようにするために、他のデータ マイニング ツールを使用する前に "カテゴリ" 列を含まないデータ テーブルのコピーを作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f48c7-141">To ensure that this does not affect other operations, you should make a copy of the data table without the Category column before using other data mining tools.</span></span>

## <a name="related-tools"></a><span data-ttu-id="f48c7-142">関連ツール</span><span class="sxs-lookup"><span data-stu-id="f48c7-142">Related Tools</span></span>
 <span data-ttu-id="f48c7-143">カテゴリの**検出**ツールによってデータが分析されると、クラスタリングアルゴリズムを使用してデータマイニング構造とデータマイニングモデルが作成さ [!INCLUDE[msCoName](../includes/msconame-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-143">When the **Detect Categories** tool analyzes your data, it creates a data mining structure and data mining model by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span>

 <span data-ttu-id="f48c7-144">**主要な影響**元の分析ツールを使用してデータマイニングモデルを作成した後は、Excel 用のデータマイニングクライアントを使用して、モデルを参照し、リレーションシップを詳細に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="f48c7-144">After you have created a data mining model by using the **Analyze Key Influencers** tool, you can use the Data Mining Client for Excel to browse the model and explore relationships in more detail.</span></span> <span data-ttu-id="f48c7-145">Excel 用のデータ マイニング クライアントは、より詳細なデータ マイニング機能を備えた独立したアドインです。</span><span class="sxs-lookup"><span data-stu-id="f48c7-145">The Data Mining Client for Excel is a separate add-in that provides more advanced data mining functionality.</span></span> <span data-ttu-id="f48c7-146">詳細については、「 [Excel でのモデルの参照 &#40;SQL Server データマイニングアドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f48c7-146">For information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>

 <span data-ttu-id="f48c7-147">Excel 用のデータマイニングクライアントのデータモデリング機能の使用方法の詳細については、「[データマイニングモデルの作成](creating-a-data-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f48c7-147">For more information about using the data modeling capabilities in the Data Mining Client for Excel, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>

 <span data-ttu-id="f48c7-148">**カテゴリの検出**ツールによって使用されるアルゴリズムの詳細については、オンラインブックの「Microsoft クラスタリングアルゴリズム」を参照してください [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f48c7-148">For more information about the algorithm used by the **Detect Categories** tool, see the topic "Microsoft Clustering Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>

## <a name="see-also"></a><span data-ttu-id="f48c7-149">参照</span><span class="sxs-lookup"><span data-stu-id="f48c7-149">See Also</span></span>
 [<span data-ttu-id="f48c7-150">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="f48c7-150">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)


