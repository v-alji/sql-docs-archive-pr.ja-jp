---
title: クエリ結果内の行のグループ化 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing table subsets
- grouping rows
- grouping query results
ms.assetid: b07082d5-4d55-4903-9af9-4c470554c6d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52de25c86425d95f5917d89c8a3f4fec8939fb16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641944"
---
# <a name="group-rows-in-query-results-visual-database-tools"></a><span data-ttu-id="f53e0-102">クエリ結果内の行のグループ化 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f53e0-102">Group Rows in Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="f53e0-103">小計を作成したり、テーブルのサブセットの他の集計情報を表示したりする場合は、集計クエリを使用してグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-103">If you want to create subtotals or show other summary information for subsets of a table, you create groups using an aggregate query.</span></span> <span data-ttu-id="f53e0-104">各グループは、テーブルで同じ値を持つすべての行のデータを集計します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-104">Each group summarizes the data for all the rows in the table that have the same value.</span></span>  
  
 <span data-ttu-id="f53e0-105">たとえば、 `titles` テーブルの本の平均価格を出版社ごとに分類して表示するとします。</span><span class="sxs-lookup"><span data-stu-id="f53e0-105">For example, you might want to see the average price of a book in the `titles` table, but break the results down by publisher.</span></span> <span data-ttu-id="f53e0-106">そのためには、クエリを出版社 (たとえば、 `pub_id`) でグループ化します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-106">To do so, you group the query by publisher (for example, `pub_id`).</span></span> <span data-ttu-id="f53e0-107">クエリの出力結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f53e0-107">The resulting query output might look like this:</span></span>  
  
 <span data-ttu-id="f53e0-108">![クエリ結果: パブリッシャーごとにグループ化された平均価格](../../database-engine/media//dv3w9e1.gif "クエリ結果: パブリッシャーごとにグループ化された平均価格")</span><span class="sxs-lookup"><span data-stu-id="f53e0-108">![Query results: average price grouped by publisher](../../database-engine/media//dv3w9e1.gif "Query results: average price grouped by publisher")</span></span>  
  
 <span data-ttu-id="f53e0-109">データをグループ化すると、次のように集計データまたはグループ化データだけを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-109">When you group data, you can display only summary or grouped data, such as:</span></span>  
  
-   <span data-ttu-id="f53e0-110">グループ化された列 (GROUP BY 句に表示される列) の値。</span><span class="sxs-lookup"><span data-stu-id="f53e0-110">The values of the grouped columns (those that appear in the GROUP BY clause).</span></span> <span data-ttu-id="f53e0-111">上記の例では、 `pub_id` がグループ化された列です。</span><span class="sxs-lookup"><span data-stu-id="f53e0-111">In the example above, `pub_id` is the grouped column.</span></span>  
  
-   <span data-ttu-id="f53e0-112">SUM( ) や AVG( ) などの集計関数によって生成される値。</span><span class="sxs-lookup"><span data-stu-id="f53e0-112">Values produced by aggregate functions such as SUM( ) and AVG( ).</span></span> <span data-ttu-id="f53e0-113">上記の例にある 2 番目の列は、 `price` 列に AVG( ) 関数を使用して生成された列です。</span><span class="sxs-lookup"><span data-stu-id="f53e0-113">In the example above, the second column is produced by using the AVG( ) function with the `price` column.</span></span>  
  
 <span data-ttu-id="f53e0-114">各列の値は表示できません。</span><span class="sxs-lookup"><span data-stu-id="f53e0-114">You cannot display values from individual rows.</span></span> <span data-ttu-id="f53e0-115">たとえば、出版社だけでグループ化する場合は、クエリに書名は表示できません。</span><span class="sxs-lookup"><span data-stu-id="f53e0-115">For example, if you group only by publisher, you cannot also display individual titles in the query.</span></span> <span data-ttu-id="f53e0-116">そのため、クエリ出力に列を追加すると、 [クエリおよびビュー デザイナー](visual-database-tools.md) により、 [SQL ペイン](sql-pane-visual-database-tools.md)のステートメントの GROUP BY 句に列が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-116">Therefore, if you add columns to the query output, the [Query and View Designer](visual-database-tools.md) automatically adds them to the GROUP BY clause of the statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span> <span data-ttu-id="f53e0-117">1 つの列だけを集計する場合は、その列に集計関数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-117">If you want a column to be aggregated instead, you can specify an aggregate function for that column.</span></span>  
  
 <span data-ttu-id="f53e0-118">複数の列をグループ化する場合、クエリの各グループには、グループ化された列のすべての集計値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-118">If you group by more than one column, each group in the query shows the aggregate values for all grouping columns.</span></span>  
  
 <span data-ttu-id="f53e0-119">たとえば、 `titles` テーブルに対する次のクエリは、出版社 (`pub_id`) と本の種類 (`type`) の両方でグループ化されています。</span><span class="sxs-lookup"><span data-stu-id="f53e0-119">For example, the following query against the `titles` table groups by publisher (`pub_id`) and also by book type (`type`).</span></span> <span data-ttu-id="f53e0-120">クエリ結果は出版社別に並べ替えられ、出版社が発行する本の種類別に集計情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-120">The query results are ordered by publisher and show summary information for each different type of book that the publisher produces:</span></span>  
  
```  
SELECT pub_id, type, SUM(price) Total_price  
FROM titles  
GROUP BY pub_id, type  
```  
  
 <span data-ttu-id="f53e0-121">出力結果は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f53e0-121">The resulting output might look like this:</span></span>  
  
 <span data-ttu-id="f53e0-122">![クエリ結果: パブリッシャーおよび種類ごとにグループ化された価格](../../database-engine/media//dv3w9e2.gif "クエリ結果: パブリッシャーおよび種類ごとにグループ化された価格")</span><span class="sxs-lookup"><span data-stu-id="f53e0-122">![Query results: price grouped by publisher and type](../../database-engine/media//dv3w9e2.gif "Query results: price grouped by publisher and type")</span></span>  
  
### <a name="to-group-rows"></a><span data-ttu-id="f53e0-123">列をグループ化するには</span><span class="sxs-lookup"><span data-stu-id="f53e0-123">To group rows</span></span>  
  
1.  <span data-ttu-id="f53e0-124">集計するテーブルをダイアグラム ペインに追加して、クエリの作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-124">Start the query by adding the tables you want to summarize to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="f53e0-125">ダイアグラム ペインの背景を右クリックし、ショートカット メニューの **[グループ化を追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-125">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="f53e0-126">クエリおよびビュー デザイナーにより、抽出条件ペインのグリッドに **[グループ化]** 列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-126">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="f53e0-127">グループ化する列を抽出条件ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-127">Add the column or columns you want to group to the Criteria pane.</span></span> <span data-ttu-id="f53e0-128">クエリ出力に列を表示する場合は、出力に対して **[出力]** 列のチェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-128">If you want the column to appear in the query output, be sure that the **Output** column is selected for output.</span></span>  
  
     <span data-ttu-id="f53e0-129">SQL ペインのステートメントに GROUP BY 句が追加されます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-129">The Query and View Designer adds a GROUP BY clause to the statement in the SQL pane.</span></span> <span data-ttu-id="f53e0-130">たとえば、SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f53e0-130">For example, the SQL statement might look like this:</span></span>  
  
    ```  
    SELECT pub_id  
    FROM titles  
    GROUP BY pub_id  
    ```  
  
4.  <span data-ttu-id="f53e0-131">集計する列を抽出条件ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-131">Add the column or columns you want to aggregate to the Criteria pane.</span></span> <span data-ttu-id="f53e0-132">この列の [出力] 列がマークされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-132">Be sure that the column is marked for output.</span></span>  
  
5.  <span data-ttu-id="f53e0-133">集計する列の **[グループ化]** グリッド セルで、該当する集計関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="f53e0-133">In the **Group By** grid cell for the column that is going to be aggregated, select the appropriate aggregate function.</span></span>  
  
     <span data-ttu-id="f53e0-134">集計する列に別名が自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-134">The Query and View Designer automatically assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="f53e0-135">この自動的に割り当てられた別名は、わかりやすい名前に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="f53e0-135">You can replace this automatically generated alias with a more meaningful one.</span></span> <span data-ttu-id="f53e0-136">詳細については、「[列の別名の作成 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f53e0-136">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="f53e0-137">![クエリ結果セットへの列の別名の追加](../../database-engine/media//dv3w9e3.gif "クエリ結果セットへの列の別名の追加")</span><span class="sxs-lookup"><span data-stu-id="f53e0-137">![Adding a column alias to the query result set](../../database-engine/media//dv3w9e3.gif "Adding a column alias to the query result set")</span></span>  
  
     <span data-ttu-id="f53e0-138">**SQL** ペインのステートメントは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f53e0-138">The corresponding statement in the **SQL** pane might look like this:</span></span>  
  
    ```  
    SELECT   pub_id, SUM(price) AS Totalprice  
    FROM     titles  
    GROUP BY pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f53e0-139">参照</span><span class="sxs-lookup"><span data-stu-id="f53e0-139">See Also</span></span>  
 [<span data-ttu-id="f53e0-140">クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f53e0-140">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
