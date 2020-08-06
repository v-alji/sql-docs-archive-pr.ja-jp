---
title: テーブルの作成クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- table creation [SQL Server], Make Table query
- inserting tables
- Make Table query
- adding tables
ms.assetid: 4493cffa-7b2d-4c24-8ef0-d49329198972
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91c4a3bf45935053789d6e884b1af5b338b4c7c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714965"
---
# <a name="create-make-table-queries-visual-database-tools"></a><span data-ttu-id="f54a0-102">テーブルの作成クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f54a0-102">Create Make Table Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="f54a0-103">テーブルの作成クエリを使用すると、新しいテーブルに行をコピーできます。これは、処理するデータのサブセットを作成したり、データベース間でテーブルの内容をコピーしたりするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f54a0-103">You can copy rows into a new table using a Make Table query, which is useful for creating subsets of data to work with or copying the contents of a table from one database to another.</span></span> <span data-ttu-id="f54a0-104">テーブルの作成クエリは結果の挿入クエリと似ていますが、新しいテーブルを作成してそこに行をコピーする点で異なります。</span><span class="sxs-lookup"><span data-stu-id="f54a0-104">A Make Table query is similar to an Insert Results query but creates a new table to copy rows into.</span></span>  
  
 <span data-ttu-id="f54a0-105">テーブルの作成クエリを作成するときは、次の項目を指定します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-105">When you create a Make Table query, you specify:</span></span>  
  
-   <span data-ttu-id="f54a0-106">新しいデータベース テーブル (コピー先テーブル) の名前。</span><span class="sxs-lookup"><span data-stu-id="f54a0-106">The name of the new database table (the destination table).</span></span>  
  
-   <span data-ttu-id="f54a0-107">行のコピー元として使用するテーブル (コピー元テーブル)。</span><span class="sxs-lookup"><span data-stu-id="f54a0-107">The table or tables to copy rows from (the source table).</span></span> <span data-ttu-id="f54a0-108">1 つのテーブルまたは結合テーブルのいずれからでもコピーできます。</span><span class="sxs-lookup"><span data-stu-id="f54a0-108">You can copy from a single table or from joined tables.</span></span>  
  
-   <span data-ttu-id="f54a0-109">内容をコピーするコピー元テーブルの列。</span><span class="sxs-lookup"><span data-stu-id="f54a0-109">The columns in the source table whose contents you want to copy.</span></span>  
  
-   <span data-ttu-id="f54a0-110">行を特定の順序でコピーする場合は、並べ替え順序。</span><span class="sxs-lookup"><span data-stu-id="f54a0-110">Sort order, if you want to copy the rows in a particular order.</span></span>  
  
-   <span data-ttu-id="f54a0-111">コピーする行を定義する検索条件。</span><span class="sxs-lookup"><span data-stu-id="f54a0-111">Search conditions to define the rows you want to copy.</span></span>  
  
-   <span data-ttu-id="f54a0-112">集計情報だけをコピーする場合は、[グループ化] オプション。</span><span class="sxs-lookup"><span data-stu-id="f54a0-112">Group By options, if you want to copy only summary information.</span></span>  
  
 <span data-ttu-id="f54a0-113">たとえば、次のクエリでは、新しく作成した `uk`_`customers` というテーブルに `customers` テーブルの情報をコピーします。</span><span class="sxs-lookup"><span data-stu-id="f54a0-113">For example, the following query creates a new table called `uk`_`customers` and copies information from the `customers` table to it:</span></span>  
  
```  
SELECT *   
INTO uk_customers  
FROM customers  
WHERE country = 'UK'  
```  
  
 <span data-ttu-id="f54a0-114">テーブルの作成クエリを正しく使用するには、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="f54a0-114">In order to use a Make Table query successfully:</span></span>  
  
-   <span data-ttu-id="f54a0-115">データベースが SELECT...INTO 構文をサポートしている。</span><span class="sxs-lookup"><span data-stu-id="f54a0-115">Your database must support the SELECT...INTO syntax.</span></span>  
  
-   <span data-ttu-id="f54a0-116">目的のデータベースにテーブルを作成する権限がある。</span><span class="sxs-lookup"><span data-stu-id="f54a0-116">You must have permission to create a table in the target database.</span></span>  
  
### <a name="to-create-a-make-table-query"></a><span data-ttu-id="f54a0-117">テーブルの作成クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="f54a0-117">To create a Make Table query</span></span>  
  
1.  <span data-ttu-id="f54a0-118">ダイアグラム ペインにコピー元テーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-118">Add the source table or tables to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="f54a0-119">**[クエリ デザイナー]** メニューの **[クエリ タイプの変更]** をポイントし、 **[テーブルの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f54a0-119">From the **Query Designer** menu, point to **Change Type**, and then click **Make Table**.</span></span>  
  
3.  <span data-ttu-id="f54a0-120">**[テーブルの作成]** ダイアログ ボックスで、コピー先テーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-120">In the **Make Table** dialog box, type the name of the destination table.</span></span> <span data-ttu-id="f54a0-121">クエリおよびビュー デザイナーでは、名前が既に使用されているかどうかや、テーブルを作成する権限があるかどうかなどの確認は行われません。</span><span class="sxs-lookup"><span data-stu-id="f54a0-121">The Query and View Designer does not check whether the name is already in use or whether you have permission to create the table.</span></span>  
  
     <span data-ttu-id="f54a0-122">他のデータベースにコピー先テーブルを作成するには、目的のデータベース名、所有者 (必要な場合)、およびテーブル名を含む完全なテーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-122">To create a destination table in another database, specify a fully qualified table name including the name of the target database, the owner (if required), and the name of the table.</span></span>  
  
4.  <span data-ttu-id="f54a0-123">コピーする列を指定するために、クエリに列を追加します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-123">Specify the columns to copy by adding them to the query.</span></span> <span data-ttu-id="f54a0-124">詳しくは、「[クエリに列を追加する方法 (Visual Database Tools)](visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f54a0-124">For details, see [Add Columns to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="f54a0-125">クエリに追加した列だけがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f54a0-125">Columns will be copied only if you add them to the query.</span></span> <span data-ttu-id="f54a0-126">行全体をコピーするには、[ \*\* \* (すべての列)\*\*] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-126">To copy entire rows, choose **\* (All Columns)**.</span></span>  
  
     <span data-ttu-id="f54a0-127">クエリおよびビュー デザイナーにより、選択した列が、抽出条件ペインの **[列]** 列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f54a0-127">The Query and View Designer adds the columns you choose to the **Column** column of the Criteria pane.</span></span>  
  
5.  <span data-ttu-id="f54a0-128">特定の順序で行をコピーする場合は、並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-128">If you want to copy rows in a particular order, specify a sort order.</span></span> <span data-ttu-id="f54a0-129">詳しくは、「 **クエリ結果の並べ替えおよびグループ化**」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f54a0-129">For details, see **Sorting and Grouping Query Results**.</span></span>  
  
6.  <span data-ttu-id="f54a0-130">コピーする行を指定するために、検索条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-130">Specify the rows to copy by entering search conditions.</span></span> <span data-ttu-id="f54a0-131">詳細については、「[検索基準の指定 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f54a0-131">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="f54a0-132">検索条件を指定しなかった場合は、コピー元テーブルのすべての行がコピー先テーブルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f54a0-132">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f54a0-133">検索する列を抽出条件ペインに追加すると、コピーする列の一覧にその列も追加されます。</span><span class="sxs-lookup"><span data-stu-id="f54a0-133">When you add a column to search to the Criteria pane, the Query and View Designer also adds it to the list of columns to copy.</span></span> <span data-ttu-id="f54a0-134">検索に使用する列をコピーしない場合は、テーブルまたはテーブル構造オブジェクトを示す四角形内の列名の横のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="f54a0-134">If you want to use a column for searching but not copy it, clear the check box next to the column name in the rectangle representing the table or table-structured object.</span></span>  
  
7.  <span data-ttu-id="f54a0-135">集計情報をコピーする場合は、[グループ化] オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f54a0-135">If you want to copy summary information, specify Group By options.</span></span> <span data-ttu-id="f54a0-136">詳細については、「[クエリ結果の要約 (Visual Database Tools)](summarize-query-results-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f54a0-136">For details, see [Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="f54a0-137">テーブルの作成クエリを実行しても、 [結果ペイン](results-pane-visual-database-tools.md)には結果が表示されません。</span><span class="sxs-lookup"><span data-stu-id="f54a0-137">When you execute a Make Table query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="f54a0-138">代わりに、コピーされた行数を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f54a0-138">Instead, a message appears indicating how many rows were copied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f54a0-139">参照</span><span class="sxs-lookup"><span data-stu-id="f54a0-139">See Also</span></span>  
 <span data-ttu-id="f54a0-140">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f54a0-140">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="f54a0-141">クエリの種類 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f54a0-141">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
  
  
