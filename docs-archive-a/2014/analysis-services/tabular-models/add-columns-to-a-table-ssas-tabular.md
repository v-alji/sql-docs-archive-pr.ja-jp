---
title: テーブルへの列の追加 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5974a3cc-caf8-4558-8836-6e3c24b1ee23
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5f329150e3b679e67ee65570efbca904a0570786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634683"
---
# <a name="add-columns-to-a-table-ssas-tabular"></a><span data-ttu-id="362c3-102">列のテーブルへの追加 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="362c3-102">Add Columns to a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="362c3-103">このトピックでは、既存のテーブルに列を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="362c3-103">This topic describes how to add columns to an existing table.</span></span>  
  
## <a name="add-columns-from-the-data-source"></a><span data-ttu-id="362c3-104">データ ソースからの列の追加</span><span class="sxs-lookup"><span data-stu-id="362c3-104">Add Columns from the Data Source</span></span>  
 <span data-ttu-id="362c3-105">テーブルのインポート ウィザードを使用してデータ ソース テーブルからデータをインポートすると、ソース テーブル内のすべての列を含むテーブルがモデルに新しく作成されます。ただし、[プレビュー] 機能および [フィルター] 機能を使用して特定の列を除外した場合は、このテーブルには選択したフィルター処理済みのデータのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="362c3-105">When using the Table Import Wizard to import data from a data source table, a new table is created in the model which includes all of the columns in the source table, or if you choose to filter out certain columns by using the Preview and Filter feature, only those columns and filtered data you select.</span></span> <span data-ttu-id="362c3-106">また、インポートする特定の列のみを指定する SQL クエリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="362c3-106">You can also write a SQL Query that specifies only certain columns to import.</span></span> <span data-ttu-id="362c3-107">ただし、モデル テーブルに追加したいその他の列がソース テーブルにあることが後で判明する場合や DAX 式で算定された値を含む計算列を追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="362c3-107">You may, however, later determine a source table has additional columns that you want to add to the model table, or you need to add a calculated column with values derived from a DAX formula.</span></span>  
  
 <span data-ttu-id="362c3-108">たとえば、データ ソースから最初にインポートしたときに、テーブルのインポート ウィザードのプレビューおよびフィルター機能を使用して、ソース テーブルから限定された数の列を選択し、後でソース テーブルに存在するがモデル テーブルにはまだ存在しない別の列を追加する必要があると判断したとします。</span><span class="sxs-lookup"><span data-stu-id="362c3-108">If, for example, when you initially imported from a data source, you used the Preview and Filter feature in the Table Import Wizard to select a limited number of columns from the source table, you later determine that you need to add another column that exists at the source table, but does not yet exist in the model table.</span></span> <span data-ttu-id="362c3-109">または、データ ソースで FactSales テーブルに AdjustedProfit  列が追加され、モデル内の Sales テーブルにも同じ AdjustedProfit 列とデータを追加したいとします。</span><span class="sxs-lookup"><span data-stu-id="362c3-109">Or, for example, a new AdjustedProfit column was added to the FactSales table at the data source, and you now want to add the same AdjustedProfit column and data to the Sales table in the model.</span></span>  
  
 <span data-ttu-id="362c3-110">これらの場合、[テーブルのプロパティの編集] ダイアログ ボックスを使用すると、ソース テーブルから列を選択して、モデル テーブルに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="362c3-110">In these cases, you can use the Edit Table Properties dialog box to select columns from the source table and add them to the model table.</span></span> <span data-ttu-id="362c3-111">[テーブルのプロパティの編集] ダイアログ ボックスには、テーブル プレビュー ウィンドウが含まれています。</span><span class="sxs-lookup"><span data-stu-id="362c3-111">The Edit Table Properties dialog box includes the table preview window.</span></span> <span data-ttu-id="362c3-112">テーブル プレビュー ウィンドウには、ソースのテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="362c3-112">The table preview window displays the table at the source.</span></span> <span data-ttu-id="362c3-113">既にモデル テーブル定義に含まれている列は、チェックされています。</span><span class="sxs-lookup"><span data-stu-id="362c3-113">Columns that are already included in the model table definition are already checked.</span></span> <span data-ttu-id="362c3-114">モデル テーブル定義に含まれていない列は、チェックされていません。</span><span class="sxs-lookup"><span data-stu-id="362c3-114">Those columns that are not already included in the model table definition are not checked.</span></span> <span data-ttu-id="362c3-115">列を選択して [OK] をクリックすることで、ソースからモデル テーブル定義に列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="362c3-115">You can add columns from the source to the model table definition by selecting the column and clicking OK.</span></span> <span data-ttu-id="362c3-116">[テーブルのプロパティの編集] ダイアログ ボックスのテーブル プレビュー ウィンドウには、テーブルのインポート ウィザードの [プレビューとフィルター] ページのテーブル プレビュー ウィンドウと同じビューと機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="362c3-116">The table preview window in the Edit Table Properties dialog box provides the same view and features as the table preview window in the Preview and Filter page of the Table Import Wizard.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="362c3-117">複数のパーティションを含むテーブルに列を追加する場合は、[テーブルのプロパティの編集] ダイアログ ボックスを使用してテーブル定義に列を追加する前に、まずパーティション マネージャーを使用して定義済みのすべてのパーティションにその列を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="362c3-117">When adding a column to a table that contains two or more partitions, before adding the column to the table definition by using the Edit Table Properties dialog box, you must first use Partition Manager to add the column to all defined partitions.</span></span> <span data-ttu-id="362c3-118">定義されたパーティションに列を追加したら、[テーブルのプロパティの編集] ダイアログ ボックスを使用してテーブル定義に同じ列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="362c3-118">After you have added the column to the defined partitions, you can then add the same column to the table definition by using the Edit Table Properties dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="362c3-119">テーブルのインポート ウィザードを最初に使用してデータをインポートしたときに、SQL クエリを使用してテーブルと列を選択した場合、モデル テーブルに列を追加するには、[テーブルのプロパティの編集] ダイアログ ボックスで再度 SQL クエリを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="362c3-119">If you used a SQL Query to select tables and columns when you initially used the Table Import Wizard to import data, you must again use a SQL Query in the Edit Table Properties dialog box to add columns to the model table.</span></span>  
  
#### <a name="to-add-a-column-from-the-data-source-by-using-the-edit-table-properties-dialog-box"></a><span data-ttu-id="362c3-120">[テーブルのプロパティの編集] ダイアログ ボックスを使用してデータ ソースから列を追加するには</span><span class="sxs-lookup"><span data-stu-id="362c3-120">To add a column from the data source by using the Edit Table Properties dialog box</span></span>  
  
1.  <span data-ttu-id="362c3-121">モデル デザイナーで列を追加するテーブルをクリックし、 **[テーブル]** メニュー、  **[テーブルのプロパティ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="362c3-121">In the model designer, click on the table you want to add a column to, then click the **Table** menu, and then click  **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="362c3-122">**[テーブルのプロパティの編集]** ダイアログ ボックスのテーブル プレビュー ウィンドウで、追加するソース列を選択してから、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="362c3-122">In the **Edit Table Properties** dialog box, in the table preview window, select the source column you want to add, and then click OK.</span></span> <span data-ttu-id="362c3-123">既にテーブル定義に含まれている列はチェックされています。</span><span class="sxs-lookup"><span data-stu-id="362c3-123">Columns already included in the table definition will already be checked.</span></span>  
  
## <a name="add-a-calculated-column"></a><span data-ttu-id="362c3-124">計算列の追加</span><span class="sxs-lookup"><span data-stu-id="362c3-124">Add a Calculated Column</span></span>  
 <span data-ttu-id="362c3-125">計算列では、各行の値の定義に DAX 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="362c3-125">In a calculated column, a DAX formula is used to define a value for each row.</span></span> <span data-ttu-id="362c3-126">たとえば、各行に 1 を加算する単純な数式 (=1) を使用した計算列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="362c3-126">For example, you can create a calculated column with a simple formula (=1) that adds a value of 1 to each row.</span></span> <span data-ttu-id="362c3-127">計算列には、モデル内のその他のデータに基づき値を計算する複雑な式が含まれることもあります。</span><span class="sxs-lookup"><span data-stu-id="362c3-127">Calculated columns can also have more complex formulas that calculate values based on other data in the model.</span></span> <span data-ttu-id="362c3-128">計算列については、他のトピックで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="362c3-128">Calculated columns are covered in more detail in other topics.</span></span> <span data-ttu-id="362c3-129">詳細については、「 [計算列 &#40;SSAS テーブル&#41;](ssas-calculated-columns.md)で作成したテーブル モデル プロジェクトでの利用を想定して取り上げます。</span><span class="sxs-lookup"><span data-stu-id="362c3-129">For more information, see [Calculated Columns &#40;SSAS Tabular&#41;](ssas-calculated-columns.md).</span></span>  
  
#### <a name="to-create-a-calculated-column"></a><span data-ttu-id="362c3-130">計算列を作成するには</span><span class="sxs-lookup"><span data-stu-id="362c3-130">To create a calculated column</span></span>  
  
1.  <span data-ttu-id="362c3-131">モデル デザイナーのデータ ビューで、新しい空白の計算列を追加するテーブルを選択し、右端の列にスクロールするか、 **[列]** メニューをクリックしてから **[列の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="362c3-131">In the model designer, in Data View, select the table to which you want to add a new, blank calculated column, scroll to the right-most column, or click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="362c3-132">2 つの既存の列の間に新しい列を作成するには、既存の列をクリックしてから **[列の挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="362c3-132">To create a new column between two existing columns, right-click on an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="362c3-133">各行の属性を追加するには、数式バーに DAX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="362c3-133">In the formula bar, type a DAX formula to add attributes for each row.</span></span>  
  
## <a name="add-a-blank-column"></a><span data-ttu-id="362c3-134">空白列の追加</span><span class="sxs-lookup"><span data-stu-id="362c3-134">Add a Blank Column</span></span>  
 <span data-ttu-id="362c3-135">モデル テーブルに名前付きの空白列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="362c3-135">You can create a named, blank column in a model table.</span></span> <span data-ttu-id="362c3-136">空白の列は、別のソースのデータを貼り付ける場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="362c3-136">Blank columns can be useful if you want to paste data from another source.</span></span> <span data-ttu-id="362c3-137">貼り付けたデータは、インポートされたデータとは異なる方法で保存されることに留意してください。</span><span class="sxs-lookup"><span data-stu-id="362c3-137">Keep in-mind that pasted data is stored differently than imported data.</span></span> <span data-ttu-id="362c3-138">詳細については、「[ &#40;SSAS テーブル&#41;](../copy-and-paste-data-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="362c3-138">For more information, see [Copy and Paste Data &#40;SSAS Tabular&#41;](../copy-and-paste-data-ssas-tabular.md).</span></span>  
  
#### <a name="to-create-a-named-blank-column"></a><span data-ttu-id="362c3-139">名前付きの空白列を作成するには</span><span class="sxs-lookup"><span data-stu-id="362c3-139">To create a named, blank column</span></span>  
  
1.  <span data-ttu-id="362c3-140">モデル デザイナーのデータ ビューで、空白列を追加するテーブルを選択し、右端の列にスクロールするか、 **[列]** メニューをクリックしてから **[列の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="362c3-140">In the model designer, in Data View, select the table to which you want to add a blank column, scroll to the right-most column, or click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="362c3-141">2 つの既存の列の間に新しい列を作成するには、既存の列をクリックしてから **[列の挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="362c3-141">To create a new column between two existing columns, right-click an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="362c3-142">一番上のセルをクリックし、名前を入力してから Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="362c3-142">Click on the top cell, then type a name, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="362c3-143">参照</span><span class="sxs-lookup"><span data-stu-id="362c3-143">See Also</span></span>  
 <span data-ttu-id="362c3-144">[[テーブルのプロパティの編集] ダイアログボックス &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="362c3-144">[Edit Table Properties Dialog Box &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md) </span></span>  
 [<span data-ttu-id="362c3-145">テーブル、列、または行のフィルターのマッピングの変更 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="362c3-145">Change table, column, or row filter mappings &#40;SSAS Tabular&#41;</span></span>](change-table-column-or-row-filter-mappings-ssas-tabular.md)  
  
  
