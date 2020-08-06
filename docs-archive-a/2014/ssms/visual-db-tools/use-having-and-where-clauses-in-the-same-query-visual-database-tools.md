---
title: 同じクエリ内で HAVING 句と WHERE 句を使用する方法 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- search conditions [SQL Server], HAVING clause
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- HAVING clause, search criteria
- search conditions [SQL Server], WHERE clause
- WHERE clause, search criteria
- excluding rows
ms.assetid: 1e07cf56-b4b7-4c49-8ddd-c276812a7148
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20f6b471a60bf225ee61bdbbf0ecec30f21a92cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712686"
---
# <a name="use-having-and-where-clauses-in-the-same-query-visual-database-tools"></a><span data-ttu-id="485f5-102">同一クエリ内で HAVING 句および WHERE 句を使用する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="485f5-102">Use HAVING and WHERE Clauses in the Same Query (Visual Database Tools)</span></span>
  <span data-ttu-id="485f5-103">場合によっては、HAVING を使用してグループ全体に条件を適用する前に、WHERE 句を使用してグループから個別の行を除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="485f5-103">In some instances, you might want to exclude individual rows from groups (using a WHERE clause) before applying a condition to groups as a whole (using a HAVING clause).</span></span>  
  
 <span data-ttu-id="485f5-104">HAVING 句は WHERE 句に似ていますが、適用先はグループ全体だけであり、グループを示す結果セット内の行だけが対象になります。一方、WHERE 句は個々の行に適用されます。</span><span class="sxs-lookup"><span data-stu-id="485f5-104">A HAVING clause is like a WHERE clause, but applies only to groups as a whole (that is, to the rows in the result set representing groups), whereas the WHERE clause applies to individual rows.</span></span> <span data-ttu-id="485f5-105">1 つのクエリに WHERE 句と HAVING 句の両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="485f5-105">A query can contain both a WHERE clause and a HAVING clause.</span></span> <span data-ttu-id="485f5-106">そのような場合は、次の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="485f5-106">In that case:</span></span>  
  
-   <span data-ttu-id="485f5-107">最初に、ダイアグラム ペインのテーブルまたはテーブル値オブジェクトの各行に WHERE 句が適用されます。</span><span class="sxs-lookup"><span data-stu-id="485f5-107">The WHERE clause is applied first to the individual rows in the tables or table-valued objects in the Diagram pane.</span></span> <span data-ttu-id="485f5-108">WHERE 句の条件を満たす行だけがグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="485f5-108">Only the rows that meet the conditions in the WHERE clause are grouped.</span></span>  
  
-   <span data-ttu-id="485f5-109">その結果セットに含まれている行に、HAVING 句が適用されます。</span><span class="sxs-lookup"><span data-stu-id="485f5-109">The HAVING clause is then applied to the rows in the result set.</span></span> <span data-ttu-id="485f5-110">HAVING 句の条件を満たすグループだけがクエリ出力に表示されます。</span><span class="sxs-lookup"><span data-stu-id="485f5-110">Only the groups that meet the HAVING conditions appear in the query output.</span></span> <span data-ttu-id="485f5-111">HAVING 句は、GROUP BY 句または集計関数にも使用されている列にだけ適用できます。</span><span class="sxs-lookup"><span data-stu-id="485f5-111">You can apply a HAVING clause only to columns that also appear in the GROUP BY clause or in an aggregate function.</span></span>  
  
 <span data-ttu-id="485f5-112">たとえば、 `titles` テーブルと `publishers` テーブルを結合して、出版社全体の本の平均価格を表示するクエリを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="485f5-112">For example, imagine that you are joining the `titles` and `publishers` tables to create a query showing the average book price for a set of publishers.</span></span> <span data-ttu-id="485f5-113">ここでは、カリフォルニア州の出版社など、特定の出版社グループの平均価格だけを表示するとします。</span><span class="sxs-lookup"><span data-stu-id="485f5-113">You want to see the average price for only a specific set of publishers - perhaps only the publishers in the state of California.</span></span> <span data-ttu-id="485f5-114">さらに、$10.00 を超える平均価格だけを表示するとします。</span><span class="sxs-lookup"><span data-stu-id="485f5-114">And even then, you want to see the average price only if it is over $10.00.</span></span>  
  
 <span data-ttu-id="485f5-115">平均価格を計算する前に、カリフォルニア州以外の出版社を除外するために、WHERE 句で最初の条件を設定します。</span><span class="sxs-lookup"><span data-stu-id="485f5-115">You can establish the first condition by including a WHERE clause, which discards any publishers that are not in California, before calculating average prices.</span></span> <span data-ttu-id="485f5-116">2 番目の条件は、データのグループ化および集計の結果に基づくため、HAVING 句で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="485f5-116">The second condition requires a HAVING clause, because the condition is based on the results of grouping and summarizing the data.</span></span> <span data-ttu-id="485f5-117">結果として作成される SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="485f5-117">The resulting SQL statement might look like this:</span></span>  
  
```  
SELECT titles.pub_id, AVG(titles.price)  
FROM titles INNER JOIN publishers  
   ON titles.pub_id = publishers.pub_id  
WHERE publishers.state = 'CA'  
GROUP BY titles.pub_id  
HAVING AVG(price) > 10  
```  
  
 <span data-ttu-id="485f5-118">HAVING 句および WHERE 句は、どちらも抽出条件ペインで作成できます。</span><span class="sxs-lookup"><span data-stu-id="485f5-118">You can create both HAVING and WHERE clauses in the Criteria pane.</span></span> <span data-ttu-id="485f5-119">既定では、列の検索条件を指定すると、条件が HAVING 句の一部になります。</span><span class="sxs-lookup"><span data-stu-id="485f5-119">By default, if you specify a search condition for a column, the condition becomes part of the HAVING clause.</span></span> <span data-ttu-id="485f5-120">ただし、条件を WHERE 句に変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="485f5-120">However, you can change the condition to be a WHERE clause.</span></span>  
  
 <span data-ttu-id="485f5-121">同じ列を含む WHERE 句および HAVING 句を作成することも可能です。</span><span class="sxs-lookup"><span data-stu-id="485f5-121">You can create a WHERE clause and HAVING clause involving the same column.</span></span> <span data-ttu-id="485f5-122">これには、抽出条件ペインに列を 2 回作成し、一方を HAVING 句の一部として、他方を WHERE 句の一部として指定します。</span><span class="sxs-lookup"><span data-stu-id="485f5-122">To do so, you must add the column twice to the Criteria pane, then specify one instance as part of the HAVING clause and the other instance as part of the WHERE clause.</span></span>  
  
### <a name="to-specify-a-where-condition-in-an-aggregate-query"></a><span data-ttu-id="485f5-123">集計クエリで WHERE 条件を指定するには</span><span class="sxs-lookup"><span data-stu-id="485f5-123">To specify a WHERE condition in an aggregate query</span></span>  
  
1.  <span data-ttu-id="485f5-124">検索するグループを指定します。</span><span class="sxs-lookup"><span data-stu-id="485f5-124">Specify the groups for your query.</span></span> <span data-ttu-id="485f5-125">詳しくは、「[クエリ結果内の行のグループ化 (Visual Database Tools)](visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="485f5-125">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="485f5-126">WHERE 条件の基準とする列が抽出条件ペインにまだない場合は、抽出条件ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="485f5-126">If it is not already in the Criteria pane, add the column on which you want to base the WHERE condition.</span></span>  
  
3.  <span data-ttu-id="485f5-127">データ列が GROUP BY 句または集計関数に含まれていない場合は、 **[出力]** 列をオフにします。</span><span class="sxs-lookup"><span data-stu-id="485f5-127">Clear the **Output** column unless the data column is part of the GROUP BY clause or included in an aggregate function.</span></span>  
  
4.  <span data-ttu-id="485f5-128">**[フィルター]** 列で WHERE 条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="485f5-128">In the **Filter** column, specify the WHERE condition.</span></span> <span data-ttu-id="485f5-129">SQL ステートメントの HAVING 句に、指定した条件が追加されます。</span><span class="sxs-lookup"><span data-stu-id="485f5-129">The Query and View Designer adds the condition to the HAVING clause of the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="485f5-130">上の手順の例では、クエリで 2 つのテーブル `titles` および `publishers`を結合しています。</span><span class="sxs-lookup"><span data-stu-id="485f5-130">The query shown in the example for this procedure joins two tables, `titles` and `publishers`.</span></span>  
  
     <span data-ttu-id="485f5-131">クエリのこの時点で、SQL ステートメントには HAVING 句が次のように含まれています。</span><span class="sxs-lookup"><span data-stu-id="485f5-131">At this point in the query, the SQL statement contains a HAVING clause:</span></span>  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    GROUP BY titles.pub_id  
    HAVING publishers.state = 'CA'  
    ```  
  
5.  <span data-ttu-id="485f5-132">**[グループ化]** 列で、グループおよび集計のオプションの一覧の **[Where 条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="485f5-132">In the **Group By** column, select **Where** from the list of group and summary options.</span></span> <span data-ttu-id="485f5-133">SQL ステートメントの HAVING 句から条件が削除され、WHERE 句に条件が追加されます。</span><span class="sxs-lookup"><span data-stu-id="485f5-133">The Query and View Designer removes the condition from the HAVING clause in the SQL statement and adds it to the WHERE clause.</span></span>  
  
     <span data-ttu-id="485f5-134">SQL ステートメントは、WHERE 句を含むように次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="485f5-134">The SQL statement changes to include a WHERE clause instead:</span></span>  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    WHERE publishers.state = 'CA'  
    GROUP BY titles.pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="485f5-135">参照</span><span class="sxs-lookup"><span data-stu-id="485f5-135">See Also</span></span>  
 <span data-ttu-id="485f5-136">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="485f5-136">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="485f5-137">クエリ結果の要約 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="485f5-137">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
