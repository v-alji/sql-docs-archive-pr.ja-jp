---
title: テーブル内のすべての行の値を集計または集計する (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- aggregate functions [SQL Server], summarizing query results
ms.assetid: f5af876e-f937-4110-ba09-07999c35a699
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c4d80c8ab2b811b8e796f0a37b2180a2866c332
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720727"
---
# <a name="summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools"></a><span data-ttu-id="3b1d6-102">テーブルにあるすべての行の値の要約または集計 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3b1d6-102">Summarize or Aggregate Values for All Rows in a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="3b1d6-103">集計関数を使用すると、テーブルのすべての値の要約を作成できます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-103">Using an aggregate function, you can create a summary for all the values in a table.</span></span> <span data-ttu-id="3b1d6-104">たとえば、 `titles` テーブルの本の総額を表示するには、次のようなクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-104">For example, you can create a query such as the following to display the total price for all books in the `titles` table:</span></span>  
  
```  
SELECT SUM(price)  
FROM titles  
```  
  
 <span data-ttu-id="3b1d6-105">複数の列に対する集計関数を使用して、同じクエリで複数の集計を作成できます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-105">You can create multiple aggregations in the same query by using aggregate functions with more than one column.</span></span> <span data-ttu-id="3b1d6-106">たとえば、 `price` 列の合計と `discount` 列の平均を計算するクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-106">For example, you can create a query that calculates the total of the `price` column and the average of the `discount` column.</span></span>  
  
 <span data-ttu-id="3b1d6-107">同じクエリで同じ列を合計、カウント、平均などの異なる方法で集計することもできます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-107">You can also aggregate the same column in different ways (such as totaling, counting, and averaging) in the same query.</span></span> <span data-ttu-id="3b1d6-108">たとえば、次のクエリは、 `price` テーブルから `titles` 列の平均および合計を求めます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-108">For example, the following query averages and summarizes the `price` column from the `titles` table:</span></span>  
  
```  
SELECT AVG(price), SUM(price)  
FROM titles  
```  
  
 <span data-ttu-id="3b1d6-109">検索条件を追加すると、条件を満たす行のサブセットを集計できます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-109">If you add a search condition, you can aggregate the subset of rows that meet that condition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b1d6-110">行のカウントは、テーブルのすべての行と、特定の条件を満たす行のどちらでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-110">You can also count all the rows in the table or the ones that meet a specific condition.</span></span> <span data-ttu-id="3b1d6-111">詳しくは、「[テーブルの行数のカウント (Visual Database Tools)](visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-111">For details, see [Count Rows in a Table &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="3b1d6-112">テーブルのすべての行に対して 1 つの集計値を作成すると、集計値だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-112">When you create a single aggregation value for all rows in a table, you display only the aggregate values themselves.</span></span> <span data-ttu-id="3b1d6-113">たとえば、 `price` テーブルの `titles` 列の値の合計を求める場合、書名、出版社名などは表示されません。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-113">For example, if you are totaling the value of the `price` column of the `titles` table, you would not also display individual titles, publisher names, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b1d6-114">小計を求める、つまりグループを作成する場合は、グループごとに列の値を表示できます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-114">If you are subtotaling - that is, creating groups - you can display column values for each group.</span></span> <span data-ttu-id="3b1d6-115">詳しくは、「[クエリ結果内の行のグループ化 (Visual Database Tools)](group-rows-in-query-results-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-115">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).</span></span>  
  
### <a name="to-aggregate-values-for-all-rows"></a><span data-ttu-id="3b1d6-116">すべての行の値を集計するには</span><span class="sxs-lookup"><span data-stu-id="3b1d6-116">To aggregate values for all rows</span></span>  
  
1.  <span data-ttu-id="3b1d6-117">集計するテーブルが既にダイアグラム ペインに存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-117">Be sure the table you want to aggregate is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="3b1d6-118">ダイアグラム ペインの背景を右クリックし、ショートカット メニューの **[グループ化を追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-118">Right-click the background of the Diagram pane, then choose **Group By** from the shortcut menu.</span></span> <span data-ttu-id="3b1d6-119">[クエリおよびビューデザイナー](query-and-view-designer-tools-visual-database-tools.md)により、抽出条件ペインのグリッドに [**グループ化]** 列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-119">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="3b1d6-120">集計する列を抽出条件ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-120">Add the column you want to aggregate to the Criteria pane.</span></span> <span data-ttu-id="3b1d6-121">この列の [出力] 列がマークされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-121">Be sure that the column is marked for output.</span></span>  
  
     <span data-ttu-id="3b1d6-122">集計する列に別名が自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-122">The Query and View Designer automatically assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="3b1d6-123">この別名は、わかりやすい名前に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-123">You can replace this alias with a more meaningful one.</span></span> <span data-ttu-id="3b1d6-124">詳しくは、「[列の別名の作成 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-124">For details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="3b1d6-125">**[グループ化]** グリッド列で、**[合計]**、**[平均]**、**[最小]**、**[最大]**、**[カウント]** などの該当する集計関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-125">In the **Group By** grid column, select the appropriate aggregate function, such as: **Sum**, **Avg**, **Min**, **Max**, **Count**.</span></span> <span data-ttu-id="3b1d6-126">結果セットの一意の行だけを集計する場合は、 **[個別の最小値]** など、DISTINCT オプションのある集計関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-126">If you want to aggregate only unique rows in the result set, choose an aggregate function with the DISTINCT options, such as **Min Distinct**.</span></span> <span data-ttu-id="3b1d6-127">**[グループ化]**、 **[式]**、または **[Where 条件]** は、すべての行を集計するときには適用されないため、これらのオプションはクリックしないでください。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-127">Do not choose **Group By**, **Expression**, or **Where**, because those options do not apply when you are aggregating all rows.</span></span>  
  
     <span data-ttu-id="3b1d6-128">クエリおよびビュー デザイナーにより、 [SQL ペイン](sql-pane-visual-database-tools.md) のステートメントの列名は、指定した集計関数に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-128">The Query and View Designer replaces the column name in the statement in the [SQL pane](sql-pane-visual-database-tools.md) with the aggregate function that you specify.</span></span> <span data-ttu-id="3b1d6-129">たとえば、SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-129">For example, the SQL statement might look like this:</span></span>  
  
    ```  
    SELECT SUM(price)  
    FROM titles  
    ```  
  
5.  <span data-ttu-id="3b1d6-130">クエリで複数の集計を作成する場合は、手順 3. および手順 4. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-130">If you want to create more than one aggregation in the query, repeat steps 3 and 4.</span></span>  
  
     <span data-ttu-id="3b1d6-131">クエリ出力リストまたは並べ替えリストに他の列を追加すると、グリッドの **[グループ化]** 列に **[グループ化]** という語句が、クエリおよびビュー デザイナーにより自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-131">When you add another column to the query output list or order by list, the Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span> <span data-ttu-id="3b1d6-132">適切な集計関数を選択してください。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-132">Select the appropriate aggregate function.</span></span>  
  
6.  <span data-ttu-id="3b1d6-133">集計する行のサブセットを指定する検索条件がある場合は、検索条件も追加します。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-133">Add search conditions, if any, to specify the subset of rows you want to summarize.</span></span>  
  
 <span data-ttu-id="3b1d6-134">クエリを実行すると、結果ペインに指定した集計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-134">When you execute the query, the Results pane displays the aggregations that you specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b1d6-135">[グループ化] モードを明示的にオフにするまで、集計関数は SQL ペイン内に SQL ステートメントの一部として保持されます。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-135">The Query and View Designer maintains aggregate functions as part of the SQL statement in the SQL pane until you explicitly turn off Group By mode.</span></span> <span data-ttu-id="3b1d6-136">そのため、クエリの種類を変更したり、ダイアグラム ペインに表示されるテーブルまたはテーブル値オブジェクトを変更したりすると、作成されるクエリに無効な集計関数が含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3b1d6-136">Therefore, if you modify your query by changing its type or by changing which tables or table-valued objects are present in the Diagram pane, the resulting query might include invalid aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1d6-137">参照</span><span class="sxs-lookup"><span data-stu-id="3b1d6-137">See Also</span></span>  
 <span data-ttu-id="3b1d6-138">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3b1d6-138">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3b1d6-139">クエリ結果の要約 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3b1d6-139">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
