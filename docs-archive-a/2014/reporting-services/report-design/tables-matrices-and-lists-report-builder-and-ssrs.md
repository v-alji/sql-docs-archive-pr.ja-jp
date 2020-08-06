---
title: テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.tablix.visibility.f1
- sql12.rtp.rptdesigner.groupproperties.advanced.f1
- "10045"
- sql12.rtp.rptdesigner.groupproperties.filters.f1
- "10039"
- "10104"
- sql12.rtp.rptdesigner.tablixgroup.f1
- sql12.rtp.rptdesigner.tablix.general.f1
- "10047"
- "10044"
- "10046"
- sql12.rtp.rptdesigner.groupproperties.visibility.f1
- "10101"
- sql12.rtp.rptdesigner.groupproperties.sort.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.general.f1
- "10042"
- sql12.rtp.rptdesigner.tablix.sort.f1
- "10041"
- sql12.rtp.rptdesigner.groupproperties.pagebreaks.f1
- "10102"
- "10103"
- "10043"
- sql12.rtp.rptdesigner.tablix.filter.f1
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03384009b0e51c081f0906ef0a768dafa180be7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640637"
---
# <a name="tables-matrices-and-lists-report-builder-and-ssrs"></a><span data-ttu-id="ddacd-102">テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ddacd-102">Tables, Matrices, and Lists (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ddacd-103">テーブル、マトリックス、および一覧は、行と列で構成されたセルにレポート データを表示するデータ領域です。</span><span class="sxs-lookup"><span data-stu-id="ddacd-103">Tables, matrices, and lists are data regions that display report data in cells that are organized into rows and columns.</span></span> <span data-ttu-id="ddacd-104">セルには通常、テキスト、日付、数字などのテキスト データが含まれていますが、ゲージ、グラフ、または画像などのレポート アイテムも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-104">The cells typically contain text data such as text, dates, and numbers but they can also contain gauges, charts, or report items such as images.</span></span> <span data-ttu-id="ddacd-105">テーブル、マトリックス、および一覧をまとめて Tablix データ領域と呼ぶことがあります。</span><span class="sxs-lookup"><span data-stu-id="ddacd-105">Collectively, tables, matrices, and lists are frequently referred to as tablix data regions.</span></span>  
  
 <span data-ttu-id="ddacd-106">テーブル、マトリックス、および一覧のテンプレートは、セルにデータを表示できる柔軟なグリッドである Tablix データ領域に基づいて構築されます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-106">The table, matrix, and list templates are built on the tablix data region, which is a flexible grid that can display data in cells.</span></span> <span data-ttu-id="ddacd-107">テーブルおよびマトリックスのテンプレートでは、セルは行と列で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-107">In the table and matrix templates, cells are organized into rows and columns.</span></span> <span data-ttu-id="ddacd-108">テンプレートは基になる汎用の Tablix データ領域の一種であるため、レポートの作成時に、テンプレート形式を組み合わせてデータを表示し、テーブル、マトリックス、または一覧を変更して別のデータ領域の機能を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-108">Because templates are variations of the underlying generic tablix data region, you can display can display data in combination of template formats and change the table, matrix, or list on to include the features of another data region as you develop your report.</span></span> <span data-ttu-id="ddacd-109">たとえば、追加したテーブルがニーズに合わない場合は、列グループを追加してテーブルをマトリックスに変更できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-109">For example, if you add a table and find it does not serve your needs, you can add column groups to make the table a matrix.</span></span>  
  
 <span data-ttu-id="ddacd-110">テーブルとマトリックスのデータ領域では、入れ子になったテーブル、マトリックス、一覧、グラフ、およびゲージを含めることで、データの複雑なリレーションシップを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-110">The table and matrix data regions can display complex data relationships by including nested tables, matrices, lists, charts and gauges.</span></span> <span data-ttu-id="ddacd-111">テーブルとマトリックスには表形式のレイアウトがあり、各データは 1 つのデータ ソースに基づいて構築された 1 つのデータセットから取得されます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-111">Tables and matrices have a tabular layout and their data comes from a single dataset, built on a single data source.</span></span> <span data-ttu-id="ddacd-112">テーブルとマトリックスの重要な違いとして、テーブルに含めることができるのは行グループのみであるのに対し、マトリックスには行グループと列グループを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-112">The key difference between tables and matrices is that tables can include only row groups, where as matrices have row groups and column groups.</span></span>  
  
 <span data-ttu-id="ddacd-113">一覧はこれとは多少異なります。</span><span class="sxs-lookup"><span data-stu-id="ddacd-113">Lists are a little different.</span></span> <span data-ttu-id="ddacd-114">一覧は、自由形式のレイアウトをサポートし、異なるデータセットのデータを使用した複数のピア テーブルまたはマトリックスを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-114">They support a free-layout that and can include multiple peer tables or matrices, each using data from a different dataset.</span></span> <span data-ttu-id="ddacd-115">一覧は、請求書などのフォームにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-115">Lists can also be used for forms, such as invoices.</span></span>  
  
 <span data-ttu-id="ddacd-116">次の図は、テーブル、マトリックス、または一覧を含んだ簡単なレポートを示しています。</span><span class="sxs-lookup"><span data-stu-id="ddacd-116">The following pictures show simple reports with a table, matrix, or list.</span></span>  
  
 <span data-ttu-id="ddacd-117">![RS_TableMatrixList](../media/rs-tablematrixlist.gif "RS_TableMatrixList")</span><span class="sxs-lookup"><span data-stu-id="ddacd-117">![RS_TableMatrixList](../media/rs-tablematrixlist.gif "RS_TableMatrixList")</span></span>  
  
 <span data-ttu-id="ddacd-118">テーブル、マトリックス、および一覧をすぐに使用するには、「[チュートリアル: 基本的な表レポートの作成 &#40;レポート ビルダー&#41;](../tutorial-creating-a-basic-table-report-report-builder.md)」、「[チュートリアル: マトリックス レポートの作成 &#40;レポート ビルダー&#41;](../tutorial-creating-a-matrix-report-report-builder.md)」、および「[チュートリアル: 自由形式のレポートの作成 &#40;レポート ビルダー&#41;](../tutorial-creating-a-free-form-report-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddacd-118">To quickly get started with tables, matrices, and lists, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../tutorial-creating-a-basic-table-report-report-builder.md), [Tutorial: Creating a Matrix Report &#40;Report Builder&#41;](../tutorial-creating-a-matrix-report-report-builder.md), and [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../tutorial-creating-a-free-form-report-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddacd-119">テーブル、マトリックス、および一覧は、レポート パーツとしてレポートとは別にパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-119">You can publish tables, matrices, and lists separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="table"></a><a name="Table"></a><span data-ttu-id="ddacd-120">一覧</span><span class="sxs-lookup"><span data-stu-id="ddacd-120">Table</span></span>  
 <span data-ttu-id="ddacd-121">テーブルを使用すると詳細データの表示やデータの行グループへの編成、またはその両方が可能です。</span><span class="sxs-lookup"><span data-stu-id="ddacd-121">Use a table to display detail data, organize the data in row groups, or both.</span></span> <span data-ttu-id="ddacd-122">テーブル テンプレートには、テーブル ヘッダー行およびデータの詳細行と共に、3 つの列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-122">The Table template contains three columns with a table header row and a details row for data.</span></span> <span data-ttu-id="ddacd-123">次の図では、デザイン画面で初期のテーブル テンプレートが選択されています。</span><span class="sxs-lookup"><span data-stu-id="ddacd-123">The following figure shows the initial table template, selected on the design surface:</span></span>  
  
 <span data-ttu-id="ddacd-124">![デザイン画面上のテーブル テンプレート、選択](../media/rs-tabletemplatenewselected.gif "デザイン画面上のテーブル テンプレート、選択")</span><span class="sxs-lookup"><span data-stu-id="ddacd-124">![Table template on design surface, selected](../media/rs-tabletemplatenewselected.gif "Table template on design surface, selected")</span></span>  
  
 <span data-ttu-id="ddacd-125">データは、1 つのフィールドまたは複数のフィールドでグループ化することも、独自の式を記述してグループ化することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-125">You can group data by a single field, by multiple fields, or by writing your own expression.</span></span> <span data-ttu-id="ddacd-126">入れ子になったグループや独立した隣接するグループの作成、グループ化されたデータの集計値の表示、グループへの合計の追加などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-126">You can create nested groups or independent, adjacent groups and display aggregated values for grouped data, or add totals to groups.</span></span> <span data-ttu-id="ddacd-127">たとえば、テーブルに [Category] という名前の行グループがある場合は、各グループの小計とレポートの総計を追加できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-127">For example, if your table has a row group called [Category], you can add a subtotal for each group as well as a grand total for the report.</span></span> <span data-ttu-id="ddacd-128">テーブルを見やすくし、強調するデータを強調表示するには、セルを結合し、書式をデータとテーブルの見出しに適用します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-128">To improve the appearance of the table and highlight data you want to emphasize, you can merge cells and apply formatting to data and table headings.</span></span>  
  
 <span data-ttu-id="ddacd-129">最初は詳細データまたはグループ化されたデータを非表示にして、ユーザーが表示するデータを対話的に選択できるドリルダウンの切り替えを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-129">You can initially hide detail or grouped data, and include drilldown toggles to enable a user to interactively choose how much data to show.</span></span>  
  
 <span data-ttu-id="ddacd-130">詳細については、「[テーブル &#40;レポート ビルダーおよび SSRS& #41;](tables-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddacd-130">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="matrix"></a><a name="Matrix"></a><span data-ttu-id="ddacd-131">一覧</span><span class="sxs-lookup"><span data-stu-id="ddacd-131">Matrix</span></span>  
 <span data-ttu-id="ddacd-132">PivotTable またはクロス集計と同様に、マトリックスは、行と列にグループ化した集計データ サマリの表示に使用します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-132">Use a matrix to display aggregated data summaries, grouped in rows and columns, similar to a PivotTable or crosstab.</span></span> <span data-ttu-id="ddacd-133">グループの行と列の数は、各行グループおよび列グループに含まれている一意の値の数によって決定します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-133">The number of rows and columns for groups is determined by the number of unique values for each row and column groups.</span></span> <span data-ttu-id="ddacd-134">次の図では、デザイン画面で初期のマトリックス テンプレートが選択されています。</span><span class="sxs-lookup"><span data-stu-id="ddacd-134">The following figure shows the initial matrix template, selected on the design surface:</span></span>  
  
 <span data-ttu-id="ddacd-135">![ツールボックスから追加された新しいマトリックス、選択済み](../media/rs-matrixtemplatenewselected.gif "ツールボックスから追加された新しいマトリックス、選択済み")</span><span class="sxs-lookup"><span data-stu-id="ddacd-135">![New Matrix added from Toolbox, selected](../media/rs-matrixtemplatenewselected.gif "New Matrix added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="ddacd-136">データは、複数のフィールドまたは式によって、行グループと列グループにグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-136">You can group data by multiple fields or expressions in row and column groups.</span></span> <span data-ttu-id="ddacd-137">実行時にレポート データとデータ領域が組み合わされると、列グループに列、行グループに行がそれぞれ追加され、マトリックスはページ上で縦横に拡大されます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-137">At run time, when the report data and data regions are combined, a matrix grows horizontally and vertically on the page as columns for column groups and rows for row groups are added.</span></span> <span data-ttu-id="ddacd-138">マトリックス セルには、そのセルが所属する行グループと列グループの交差部分にスコープを設定した集計値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-138">The matrix cells display aggregate values that are scoped to the intersection of the row and column groups to which the cell belongs.</span></span> <span data-ttu-id="ddacd-139">たとえば、マトリックスに行グループ (Category) と売上の合計を表示する 2 つの列グループ (Territory および Year) がある場合、レポートには Category グループ内の各値に対して売上の合計を含む 2 つのセルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-139">For example, if your matrix has a row group (Category) and two column groups (Territory and Year) that display the sum of sales, the report displays two cells with sums of sales for each value in the Category group.</span></span> <span data-ttu-id="ddacd-140">セルのスコープは 2 つの交差部分 (Category および Territory と Category および Year) です。</span><span class="sxs-lookup"><span data-stu-id="ddacd-140">The scope of the cells are the two intersections are: Category and Territory and Category and Year.</span></span> <span data-ttu-id="ddacd-141">マトリックスには、入れ子になったグループと隣接するグループを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-141">The matrix can include nested and adjacent groups.</span></span> <span data-ttu-id="ddacd-142">入れ子になったグループには親子リレーションシップ、隣接するグループにはピア リレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="ddacd-142">Nested groups have a parent-child relationship and adjacent groups a peer relationship.</span></span> <span data-ttu-id="ddacd-143">マトリックス内には、入れ子になった行および列グループの任意のレベルの小計や、すべてのレベルの小計が追加できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-143">You can add subtotals for any and all levels of nested row and column groups within the matrix.</span></span>  
  
 <span data-ttu-id="ddacd-144">マトリックス データを読みやすくし、強調するデータを強調表示するには、セルを結合するか、水平方向および垂直方向に分割し、書式をデータとグループの見出しに適用します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-144">To make the matrix data more readable and highlight the data you want to emphasize, you can merge cells or split horizontally and vertically and apply formatting to data and group headings.</span></span>  
  
 <span data-ttu-id="ddacd-145">ドリルダウン トグルを含めて、最初は詳細データを非表示にすることもできます。ユーザーは、トグルをクリックすることにより、表示するデータの量を調整できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-145">You can also include drilldown toggles that initially hide detail data; the user can then click the toggles to display more or less detail as needed.</span></span>  
  
 <span data-ttu-id="ddacd-146">詳細については、「[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddacd-146">For more information, see [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="list"></a><a name="List"></a><span data-ttu-id="ddacd-147">表</span><span class="sxs-lookup"><span data-stu-id="ddacd-147">List</span></span>  
 <span data-ttu-id="ddacd-148">一覧は、自由形式のレイアウトの作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-148">Use a list to create a free-form layout.</span></span> <span data-ttu-id="ddacd-149">グリッド レイアウトのみに制限されず、フィールドは一覧内に自由に配置できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-149">You are not limited to a grid layout, but can place fields freely inside the list.</span></span> <span data-ttu-id="ddacd-150">一覧は、多数のデータセット フィールドを表示するフォームの設計に使用したり、グループ化されたデータの場合は、複数のデータ領域を並列に表示するコンテナーとして使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-150">You can use a list to design a form for displaying many dataset fields or as a container to display multiple data regions side by side for grouped data.</span></span> <span data-ttu-id="ddacd-151">たとえば、一覧にグループを定義し、テーブル、グラフ、およびイメージを追加し、従業員や患者のレコードを表示する際と同様に、各グループ値についてテーブルまたはグラフィック形式で値を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-151">For example, you can define a group for a list; add a table, chart, and image; and display values in table and graphic form for each group value, as you might for an employee or patient record.</span></span>  
  
 <span data-ttu-id="ddacd-152">![ツールボックスから追加された新しい一覧、選択](../media/rs-listtemplatenewselected.gif "ツールボックスから追加された新しい一覧、選択")</span><span class="sxs-lookup"><span data-stu-id="ddacd-152">![New List added from Toolbox, selected](../media/rs-listtemplatenewselected.gif "New List added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="ddacd-153">詳細については、「 [&#40;レポートビルダーと SSRS&#41;の一覧](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddacd-153">For more information, see [Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="preparing-data"></a><a name="PreparingData"></a><span data-ttu-id="ddacd-154">データの準備</span><span class="sxs-lookup"><span data-stu-id="ddacd-154">Preparing Data</span></span>  
 <span data-ttu-id="ddacd-155">テーブル、マトリックス、および一覧のデータ領域には、データセットのデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-155">A table, matrix, and list data regions display data from a dataset.</span></span> <span data-ttu-id="ddacd-156">データセットのデータを取得するクエリのデータを準備することも、テーブル、マトリックス、または一覧でプロパティを設定してデータを準備することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-156">You can prepare the data in the query that retrieves the data for the dataset or by setting properties in the table, matrix, or list.</span></span>  
  
 <span data-ttu-id="ddacd-157">レポート データセットのデータを取得するのに使用する、 [!INCLUDE[tsql](../../includes/tsql-md.md)]などのクエリ言語でデータを準備するには、データのサブセットのみを含むようにフィルターを適用し、レポートが読みやすくなるように NULL 値や空白を定数に置き換え、データの並べ替えやグループ化を行います。</span><span class="sxs-lookup"><span data-stu-id="ddacd-157">The query languages such as [!INCLUDE[tsql](../../includes/tsql-md.md)], that you use to retrieve the data for the report datasets can prepare the data by applying filters to include only a subset of the data, replacing null values or blanks with constants that make the report more readable, and sorting and grouping data.</span></span>  
  
 <span data-ttu-id="ddacd-158">レポートのテーブル、マトリックス、または一覧のデータ領域でデータを準備する場合は、データ領域またはデータ領域内のセルのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-158">If you choose to prepare the data in the table, matrix, or list data region of a report, you set properties on the data region or cells within the data region.</span></span> <span data-ttu-id="ddacd-159">データのフィルター処理または並べ替えを行うには、データ領域のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-159">If you want to filter or sort the data, set the properties on the data region.</span></span> <span data-ttu-id="ddacd-160">たとえば、データを並べ替えるには、並べ替える列と並べ替えの方向を指定します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-160">For example, to sort the data you specify the columns to sort on and the sort direction.</span></span> <span data-ttu-id="ddacd-161">フィールドに別の値を表示する場合は、フィールドを表示するセル テキストの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-161">If you want to provide an alternative value for a field, you set the values of the cell text that displays the field.</span></span> <span data-ttu-id="ddacd-162">たとえば、フィールドが空または NULL である場合に Blank と表示するには、式を使用して値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-162">For example, to display Blank when a field is empty or null, you use an expression to set the value.</span></span>  
  
 <span data-ttu-id="ddacd-163">詳細については、「[Tablix データ領域に表示するデータの準備 &#40;レポート ビルダーおよび SSRS&#41;](preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddacd-163">For more information, see [Preparing Data for Display in a Tablix Data Region &#40;Report Builder and SSRS&#41;](preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="building-and-configuring-a-table-matrix-or-list"></a><a name="BuildingConfiguringTableMatrixList"></a><span data-ttu-id="ddacd-164">テーブル、マトリックス、または一覧の構築と構成</span><span class="sxs-lookup"><span data-stu-id="ddacd-164">Building and Configuring a Table, Matrix, or List</span></span>  
 <span data-ttu-id="ddacd-165">テーブルまたはマトリックスをレポートに追加する場合は、テーブルまたはマトリックス ウィザードを使用するか、レポート ビルダーおよびレポート デザイナーに用意されたテンプレートから手動で構築できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-165">When you add tables or matrices to your report, you can use the Table and Matrix Wizard or build them manually from the templates that Report Builder and Report Designer provide.</span></span> <span data-ttu-id="ddacd-166">一覧は、一覧のテンプレートから手動で構築します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-166">Lists are built manually from the list template.</span></span>  
  
 <span data-ttu-id="ddacd-167">ウィザードを使用すると、手順に従ってテーブルやマトリックスを簡単に構築および構成できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-167">The wizard guides you through the steps to quickly build and configure a table or matrix.</span></span> <span data-ttu-id="ddacd-168">ウィザードを完了した後、または Tablix データ領域を最初から構築する場合、さらに詳細に構成および調整できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-168">After you complete the wizard or if you build the tablix data regions from scratch, you can further configure and refine them.</span></span> <span data-ttu-id="ddacd-169">データ領域の右クリック メニューで表示されるダイアログ ボックスで、改ページ、ヘッダーとフッターの繰り返しと表示設定、表示オプション、フィルター、並べ替えなどの一般的に使用するプロパティを簡単に設定できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-169">The dialog boxes, available from the right-click menus on the data regions, make it easy to set the most commonly used properties for page breaks, repeatability and visibility of headers and footers, display options, filters, and sorting.</span></span> <span data-ttu-id="ddacd-170">ただし、Tablix データ領域にはレポート ビルダーのプロパティ ペインでのみ設定できる追加のプロパティも多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="ddacd-170">But the tablix data region provides a wealth of additional properties, which you can set only in the Properties pane of Report Builder.</span></span> <span data-ttu-id="ddacd-171">たとえば、テーブル、マトリックス、または一覧のデータセットが空の場合にメッセージを表示するには、プロパティ ペインの NoRowsMessage Tablix プロパティでメッセージ テキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-171">For example, if you want to display a message when the dataset for a table, matrix, or list is empty, you specify the message text in the NoRowsMessage tablix property in the Properties pane.</span></span>  
  

  
##  <a name="changing-between-tablix-templates"></a><a name="ChangingBetweenTablixTemplates"></a><span data-ttu-id="ddacd-172">Tablix テンプレート間の変更</span><span class="sxs-lookup"><span data-stu-id="ddacd-172">Changing Between Tablix Templates</span></span>  
 <span data-ttu-id="ddacd-173">最初に選択した Tablix テンプレートによる制限はありません。</span><span class="sxs-lookup"><span data-stu-id="ddacd-173">You are not limited by your initial tablix template choice.</span></span> <span data-ttu-id="ddacd-174">グループ、合計、ラベルなどの追加に伴い、Tablix デザインを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-174">As you add groups, totals, and labels, you might want to modify your tablix design.</span></span> <span data-ttu-id="ddacd-175">たとえば、テーブルから開始し、その後詳細行を削除したり、列グループを追加したりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="ddacd-175">For example, you might start with a table and then delete the details row and add column groups.</span></span> <span data-ttu-id="ddacd-176">詳細については、「[Tablix データ領域の柔軟性について &#40;レポート ビルダーおよび SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddacd-176">For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ddacd-177">Tablix 機能を追加することで、テーブル、マトリックス、または一覧の改良を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-177">You can continue to develop a table, matrix, or list by adding any tablix feature.</span></span> <span data-ttu-id="ddacd-178">Tablix 機能には、詳細データやグループ化されたデータの集計を行および列に表示する機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-178">Tablix features include displaying detail data or aggregates for grouped data on rows and columns.</span></span> <span data-ttu-id="ddacd-179">入れ子構造のグループ、独立した隣接するグループ、または再帰的なグループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-179">You can create nested groups, independent adjacent groups, or recursive groups.</span></span> <span data-ttu-id="ddacd-180">グループ データのフィルター処理や並べ替えが可能なほか、複数のグループ式をグループ定義に含めることにより、グループを簡単に組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-180">You can filter and sort grouped data, and easily combine groups by including multiple group expressions in a group definition</span></span>  
  
 <span data-ttu-id="ddacd-181">さらに、グループの合計、またはデータ領域の総合計を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-181">You can also add totals for a group or grand totals for the data region.</span></span> <span data-ttu-id="ddacd-182">行や列を非表示にしてレポートを簡潔化し、ドリルダウン レポートのように非表示のデータ表示をユーザーが切り替えることができるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ddacd-182">You can hide rows or columns to simplify a report and enable the user to toggle the display of the hidden data, as in a drilldown report.</span></span> <span data-ttu-id="ddacd-183">詳細については、「 [レポート ページでの Tablix データ領域の表示の制御 &#40;レポート ビルダーおよび SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddacd-183">For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="ddacd-184">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="ddacd-184">How-To Topics</span></span>  
 <span data-ttu-id="ddacd-185">このセクションでは、レポートでテーブル、マトリックス、および一覧を使用する手順について説明しているトピックの一覧を紹介します。具体的には、行と列のデータの表示、列の追加と削除、セルの結合、および行および列グループの小計を含める方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-185">This section lists procedures that show you, step by step, how to work with work with tables, matrices and lists in your reports; how to display data in rows and columns, add and delete columns, merge cells, and include subtotals for row and column groups.</span></span>  
  
-   [<span data-ttu-id="ddacd-186">詳細グループの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-186">Add a Details Group &#40;Report Builder and SSRS&#41;</span></span>](add-a-details-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-187">グループまたは Tablix データ領域への合計の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-187">Add a Total to a Group or Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-188">セル内のアイテムの変更 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-188">Change an Item Within a Cell &#40;Report Builder and SSRS&#41;</span></span>](change-an-item-within-a-cell-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-189">行の高さまたは列の幅の変更 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-189">Change Row Height or Column Width &#40;Report Builder and SSRS&#41;</span></span>](change-row-height-or-column-width-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-190">列の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-190">Insert or Delete a Column &#40;Report Builder and SSRS&#41;</span></span>](insert-or-delete-a-column-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-191">行の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-191">Insert or Delete a Row &#40;Report Builder and SSRS&#41;</span></span>](insert-or-delete-a-row-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-192">データ領域内のセルの結合 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-192">Merge Cells in a Data Region &#40;Report Builder and SSRS&#41;</span></span>](merge-cells-in-a-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-193">再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-193">Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;</span></span>](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-194">データ領域でのグループの追加または削除 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-194">Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;</span></span>](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-195">グループ単位でのヘッダーとフッターの表示 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-195">Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;</span></span>](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-196">階段状レポートの作成 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-196">Create a Stepped Report &#40;Report Builder and SSRS&#41;</span></span>](create-a-stepped-report-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="ddacd-197">テーブル、マトリックス、または一覧の追加、移動、または削除 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-197">Add, Move, or Delete a Table, Matrix, or List &#40;Report Builder and SSRS&#41;</span></span>](add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs.md)  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="ddacd-198">トピックの内容</span><span class="sxs-lookup"><span data-stu-id="ddacd-198">In This Section</span></span>  
 <span data-ttu-id="ddacd-199">次の各トピックでは、Tablix データ領域の使用に関する追加情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-199">The following topics provide additional information about working with the tablix data region.</span></span>  
  
 [<span data-ttu-id="ddacd-200">Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-200">Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](../tablix-data-region-report-builder-and-ssrs.md)  
 <span data-ttu-id="ddacd-201">Tablix データ、詳細データ、およびグループ化されたデータの領域、列グループおよび行グループ、静的および動的な行と列など、Tablix データ領域に関連する主な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-201">Explains key concepts related to the tablix data region such as areas of the tablix, detail and grouped data, column and row groups, and static and dynamic rows and columns.</span></span>  
  
 [<span data-ttu-id="ddacd-202">Tablix データ領域へのデータの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-202">Adding Data to a Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](adding-data-to-a-tablix-data-region-report-builder-and-ssrs.md)  
 <span data-ttu-id="ddacd-203">Tablix データ領域に詳細データ、グループ化されたデータ、小計と総計、およびラベルを追加する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-203">Provides detailed information about adding detail and grouped data, subtotals and totals, and labels to a tablix data region.</span></span>  
  
 [<span data-ttu-id="ddacd-204">レポート ページでの Tablix データ領域の表示の制御 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-204">Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;</span></span>](controlling-the-tablix-data-region-display-on-a-report-page.md)  
 <span data-ttu-id="ddacd-205">レポートに表示したときの Tablix データ領域の表示方法を変更するための Tablix データ領域のプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-205">Describes properties for a tablix data region that you can modify to change the way a tablix data region appears when you view it in a report.</span></span>  
  
 [<span data-ttu-id="ddacd-206">行見出しと列見出しの制御 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-206">Controlling Row and Column Headings &#40;Report Builder and SSRS&#41;</span></span>](controlling-row-and-column-headings-report-builder-and-ssrs.md)  
 <span data-ttu-id="ddacd-207">テーブル、マトリックス、または一覧のデータ領域が上下または左右の複数のページにわたる場合、行見出しおよび列見出しの表示を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-207">Describes how to control row and column headings when a table, matrix, or list data region cans span multiple pages horizontally or vertically.</span></span>  
  
 [<span data-ttu-id="ddacd-208">複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-208">Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;</span></span>](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)  
 <span data-ttu-id="ddacd-209">親子間のリレーションシップがデータセットのフィールドで表されている再帰型データを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-209">Describes how to display recursive data where the relationship between parent and child is represented by fields in the dataset.</span></span>  
  
 [<span data-ttu-id="ddacd-210">グループについて &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddacd-210">Understanding Groups &#40;Report Builder and SSRS&#41;</span></span>](understanding-groups-report-builder-and-ssrs.md)  
 <span data-ttu-id="ddacd-211">グループの概要、グループを使用する状況、およびさまざまな Tablix データ領域に使用できるグループについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ddacd-211">Explains what groups are and when you use them and describes the groups available for the different tablix data regions.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="ddacd-212">参照</span><span class="sxs-lookup"><span data-stu-id="ddacd-212">See Also</span></span>  
 <span data-ttu-id="ddacd-213">[データセットフィルター、データ領域フィルター、およびグループフィルターを追加 &#40;レポートビルダーと SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="ddacd-213">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="ddacd-214">[入れ子になったデータ領域 &#40;レポートビルダーと SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddacd-214">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ddacd-215">[同じデータセットへの複数のデータ領域のリンク &#40;レポートビルダーと SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddacd-215">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ddacd-216">[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddacd-216">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ddacd-217">[データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddacd-217">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ddacd-218">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="ddacd-218">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="ddacd-219">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddacd-219">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ddacd-220">ゲージ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ddacd-220">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
