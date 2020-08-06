---
title: 結果の挿入クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- result sets [SQL Server], queries
- results [SQL Server], query
- Insert Results query
- queries [SQL Server], results
ms.assetid: 8770d630-09cc-47ec-a0e9-e9de2d7bbc89
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02643c2cf3295debe740a696941f8730d4417254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714966"
---
# <a name="create-insert-results-queries-visual-database-tools"></a><span data-ttu-id="352e4-102">結果の挿入クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="352e4-102">Create Insert Results Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="352e4-103">結果の挿入クエリを使用すると、テーブル間またはテーブル内で行をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="352e4-103">You can copy rows from one table to another or within a table using an Insert Results query.</span></span> <span data-ttu-id="352e4-104">たとえば、 `titles` テーブルで結果の挿入クエリを使用すると、特定の出版社のすべての書名に関する情報を別のテーブルにコピーして、その出版社に提供できます。</span><span class="sxs-lookup"><span data-stu-id="352e4-104">For example, in a `titles` table, you can use an Insert Results query to copy information about all the titles for one publisher to a second table that you can make available to that publisher.</span></span> <span data-ttu-id="352e4-105">結果の挿入クエリは、テーブルの作成と似ていますが、既存のテーブルに行をコピーする点が異なります。</span><span class="sxs-lookup"><span data-stu-id="352e4-105">An Insert Results query is similar to Make Table Queries, but copies rows into an existing table.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="352e4-106">テーブル間の行のコピーは、カット アンド ペーストを使用して行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="352e4-106">You can also copy rows from one table to another using cut and paste.</span></span> <span data-ttu-id="352e4-107">これにはまず、各テーブルに対するクエリを作成して実行します。</span><span class="sxs-lookup"><span data-stu-id="352e4-107">Create a query for each table and run the queries.</span></span> <span data-ttu-id="352e4-108">次に、必要な行を結果グリッドから別の結果グリッドにコピーします。</span><span class="sxs-lookup"><span data-stu-id="352e4-108">Copy the rows you want from one results grid to the other.</span></span>  
  
 <span data-ttu-id="352e4-109">結果の挿入クエリを作成するときは、次の項目を指定します。</span><span class="sxs-lookup"><span data-stu-id="352e4-109">When you create an Insert Results query, you specify:</span></span>  
  
-   <span data-ttu-id="352e4-110">行のコピー先のデータベース テーブル (コピー先テーブル)。</span><span class="sxs-lookup"><span data-stu-id="352e4-110">The database table to copy rows to (the destination table).</span></span>  
  
-   <span data-ttu-id="352e4-111">行のコピー元として使用するテーブル (コピー元テーブル)。</span><span class="sxs-lookup"><span data-stu-id="352e4-111">The table or tables to copy rows from (the source table).</span></span> <span data-ttu-id="352e4-112">コピー元テーブルはサブクエリの一部となります。</span><span class="sxs-lookup"><span data-stu-id="352e4-112">The source table or tables become part of a subquery.</span></span> <span data-ttu-id="352e4-113">同じテーブル内にコピーする場合、コピー元とコピー先は同じテーブルです。</span><span class="sxs-lookup"><span data-stu-id="352e4-113">If you are copying within a table, the source table is the same as the destination table.</span></span>  
  
-   <span data-ttu-id="352e4-114">内容をコピーするコピー元テーブルの列。</span><span class="sxs-lookup"><span data-stu-id="352e4-114">The columns in the source table whose contents you want to copy.</span></span>  
  
-   <span data-ttu-id="352e4-115">データのコピー先となるコピー先テーブルの列。</span><span class="sxs-lookup"><span data-stu-id="352e4-115">The target columns in the destination table to copy the data to.</span></span>  
  
-   <span data-ttu-id="352e4-116">コピーする行を定義する検索条件。</span><span class="sxs-lookup"><span data-stu-id="352e4-116">Search conditions to define the rows you want to copy.</span></span>  
  
-   <span data-ttu-id="352e4-117">行を特定の順序でコピーする場合は、並べ替え順序。</span><span class="sxs-lookup"><span data-stu-id="352e4-117">Sort order, if you want to copy the rows in a particular order.</span></span>  
  
-   <span data-ttu-id="352e4-118">集計情報だけをコピーする場合は、[グループ化] オプション。</span><span class="sxs-lookup"><span data-stu-id="352e4-118">Group By options, if you want to copy only summary information.</span></span>  
  
 <span data-ttu-id="352e4-119">たとえば、次のクエリでは、 `titles` テーブルの書名情報を `archivetitles`というアーカイブ テーブルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="352e4-119">For example, the following query copies title information from the `titles` table to an archive table called `archivetitles`.</span></span> <span data-ttu-id="352e4-120">このクエリでは、特定の出版社のすべての書名に関する 4 つの列の内容をコピーします。</span><span class="sxs-lookup"><span data-stu-id="352e4-120">The query copies the contents of four columns for all titles belonging to a particular publisher:</span></span>  
  
```  
INSERT INTO archivetitles   
   (title_id, title, type, pub_id)  
SELECT title_id, title, type, pub_id  
FROM titles  
WHERE (pub_id = '0766')  
```  
  
> [!NOTE]  
>  <span data-ttu-id="352e4-121">新しい行に値を挿入するには、値挿入クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="352e4-121">To insert values into a new row, use an Insert Values query.</span></span>  
  
 <span data-ttu-id="352e4-122">行の特定の列の内容をコピーする方法と、行のすべての列の内容をコピーする方法があります。</span><span class="sxs-lookup"><span data-stu-id="352e4-122">You can copy the contents of selected columns or of all columns in a row.</span></span> <span data-ttu-id="352e4-123">どちらの方法でも、コピー元のデータには、コピー先の行の列との互換性が必要です。</span><span class="sxs-lookup"><span data-stu-id="352e4-123">In either case, the data you are copying must be compatible with the columns in the rows you are copying to.</span></span> <span data-ttu-id="352e4-124">たとえば、 `price`などの列の内容をコピーする場合、コピー先の行の列には、小数点を含む数値データを入力できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="352e4-124">For example, if you copy the contents of a column such as `price`, the column in the row you are copying to must accept numeric data with decimal places.</span></span> <span data-ttu-id="352e4-125">行全体をコピーする場合、コピー先テーブルには、互換性のある列がコピー元テーブルと同じ順序で存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="352e4-125">If you are copying an entire row, the destination table must have compatible columns in the same physical position as the source table.</span></span>  
  
 <span data-ttu-id="352e4-126">結果の挿入クエリを作成すると、データのコピーに使用できるオプションが抽出条件ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="352e4-126">When you create an Insert Results query, the Criteria pane changes to reflect options available for copying data.</span></span> <span data-ttu-id="352e4-127">また、データのコピー先となる列を指定できるように、[追加] 列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="352e4-127">An Append column is added to allow you to specify the columns into which data should be copied.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="352e4-128">結果の挿入クエリの実行アクションを元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="352e4-128">You cannot undo the action of executing an Insert Results query.</span></span> <span data-ttu-id="352e4-129">念のため、クエリを実行する前にデータをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="352e4-129">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-insert-results-query"></a><span data-ttu-id="352e4-130">結果の挿入クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="352e4-130">To create an Insert Results query</span></span>  
  
1.  <span data-ttu-id="352e4-131">新しいクエリを作成して、行のコピー元となるテーブル (コピー元テーブル) を追加します。</span><span class="sxs-lookup"><span data-stu-id="352e4-131">Create a new query and add the table from which you want to copy rows (the source table).</span></span> <span data-ttu-id="352e4-132">同じテーブル内で行をコピーする場合は、コピー先テーブルと同じコピー元テーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="352e4-132">If you are copying rows within a table, you can add the source table as a destination table.</span></span>  
  
2.  <span data-ttu-id="352e4-133">**[クエリ デザイナー]** メニューの **[クエリ タイプの変更]** をポイントし、 **[結果の挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="352e4-133">From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.</span></span>  
  
3.  <span data-ttu-id="352e4-134">[[挿入先のテーブル選択] ダイアログ ボックス](visual-database-tools.md)で、行のコピー先となるテーブル (コピー先テーブル) を選択します。</span><span class="sxs-lookup"><span data-stu-id="352e4-134">In the [Choose Target Table for Insert Results Dialog Box](visual-database-tools.md), select the table to copy rows to (the destination table).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="352e4-135">クエリおよびビュー デザイナーは、更新できるテーブルおよびビューを事前に判別できません。</span><span class="sxs-lookup"><span data-stu-id="352e4-135">The Query and View Designer cannot determine in advance which tables and views you can update.</span></span> <span data-ttu-id="352e4-136">そのため、 **[挿入先のテーブル選択]** ダイアログ ボックスの **[テーブル名]** ボックスには、クエリを実行するデータ接続で使用できるテーブルおよびビューがすべて表示されます。行をコピーできないテーブルおよびビューも表示されます。</span><span class="sxs-lookup"><span data-stu-id="352e4-136">Therefore, the **Table Name** list in the **Choose Table for Insert From Query** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.</span></span>  
  
4.  <span data-ttu-id="352e4-137">テーブルまたはテーブル値オブジェクトを示す四角形で、内容をコピーする列の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="352e4-137">In the rectangle representing the table or table-valued object, choose the names of the columns whose contents you want to copy.</span></span> <span data-ttu-id="352e4-138">行全体をコピーするには、[ \*\* \* (すべての列)\*\*] を選択します。</span><span class="sxs-lookup"><span data-stu-id="352e4-138">To copy entire rows, choose **\* (All Columns)**.</span></span>  
  
     <span data-ttu-id="352e4-139">選択した列が、抽出条件ペインの **[列]** 列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="352e4-139">The Query and View Designer adds the columns you choose to the **Column** column of the Criteriapane.</span></span>  
  
5.  <span data-ttu-id="352e4-140">抽出条件ペインの **[追加]** 列で、コピーする各列に対してコピー先テーブルの目的の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="352e4-140">In the **Append** column of the Criteria pane, select a target column in the destination table for each column you are copying.</span></span> <span data-ttu-id="352e4-141">行全体をコピーする場合は、[tablename] を選択し\*ます \* \* 。</span><span class="sxs-lookup"><span data-stu-id="352e4-141">Choose *tablename.\** if you are copying entire rows.</span></span> <span data-ttu-id="352e4-142">コピー先テーブルの列は、コピー元テーブルの列と同じデータ型か、互換性のあるデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="352e4-142">The columns in the destination table must have the same (or compatible) data types as the columns in the source table.</span></span>  
  
6.  <span data-ttu-id="352e4-143">特定の順序で行をコピーする場合は、並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="352e4-143">If you want to copy rows in a particular order, specify a sort order.</span></span> <span data-ttu-id="352e4-144">詳細については、「[クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)](sort-and-group-query-results-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="352e4-144">For details, see [Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md).</span></span>  
  
7.  <span data-ttu-id="352e4-145">コピーする行を指定するために、 **[フィルター]** 列に検索条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="352e4-145">Specify the rows to copy by entering search conditions in the **Filter** column.</span></span> <span data-ttu-id="352e4-146">詳細については、「[検索基準の指定 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="352e4-146">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="352e4-147">検索条件を指定しなかった場合は、コピー元テーブルのすべての行がコピー先テーブルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="352e4-147">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="352e4-148">検索する列を抽出条件ペインに追加すると、コピーする列の一覧にその列も追加されます。</span><span class="sxs-lookup"><span data-stu-id="352e4-148">When you add a column to search to the Criteria pane, the Query and View Designer also adds it to the list of columns to copy.</span></span> <span data-ttu-id="352e4-149">検索に使用する列をコピーしない場合は、テーブルまたはテーブル値オブジェクトを示す四角形内の列名の横のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="352e4-149">If you want to use a column for searching but not copy it, clear the check box next to the column name in the rectangle representing the table or table-valued object.</span></span>  
  
8.  <span data-ttu-id="352e4-150">集計情報をコピーする場合は、[グループ化] オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="352e4-150">If you want to copy summary information, specify Group By options.</span></span> <span data-ttu-id="352e4-151">詳細については、「[クエリ結果の要約 (Visual Database Tools)](summarize-query-results-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="352e4-151">For details, see [Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="352e4-152">結果の挿入クエリを実行しても、 [結果ペイン](results-pane-visual-database-tools.md)に結果は表示されません。</span><span class="sxs-lookup"><span data-stu-id="352e4-152">When you execute an Insert Results query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="352e4-153">代わりに、コピーされた行数を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="352e4-153">Instead, a message appears indicating how many rows were copied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352e4-154">参照</span><span class="sxs-lookup"><span data-stu-id="352e4-154">See Also</span></span>  
 <span data-ttu-id="352e4-155">[Visual Database Tools &#40;クエリの種類&#41;](types-of-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="352e4-155">[Types of Queries &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="352e4-156">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="352e4-156">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
