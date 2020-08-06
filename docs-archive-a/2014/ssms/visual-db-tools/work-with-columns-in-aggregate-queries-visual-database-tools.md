---
title: 集計クエリにおける列の使用 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query summary results
- GROUP BY clause, query summary results
- aggregate queries [SQL Server]
- WHERE clause, query summary results
ms.assetid: 1b82681f-3d4f-4b9a-bb1d-2060e44f2577
author: stevestein
ms.author: sstein
ms.openlocfilehash: 880f7529cebd7f51951e62952e3b5f13190f99b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711394"
---
# <a name="work-with-columns-in-aggregate-queries-visual-database-tools"></a><span data-ttu-id="8089d-102">集計クエリにおける列の使用 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8089d-102">Work with Columns in Aggregate Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="8089d-103">集計クエリを作成する場合、 [クエリおよびビュー デザイナー](visual-database-tools.md) は有効なクエリを構築できるように一定の仮説に基づいた処理を行います。</span><span class="sxs-lookup"><span data-stu-id="8089d-103">When you create aggregate queries the [Query and View Designer](visual-database-tools.md) makes certain assumptions so that it can construct a valid query.</span></span> <span data-ttu-id="8089d-104">たとえば、集計クエリを作成するときに、あるデータ列を出力するように指定した場合、その列は自動的に GROUP BY 句に含められ、個別の行の内容が誤って要約に表示されるのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="8089d-104">For example, if you are creating an aggregate query and mark a data column for output, the Query and View Designer automatically makes the column part of the GROUP BY clause so that you do not inadvertently attempt to display the contents of an individual row in a summary.</span></span>  
  
## <a name="using-group-by"></a><span data-ttu-id="8089d-105">GROUP BY の使用</span><span class="sxs-lookup"><span data-stu-id="8089d-105">Using Group By</span></span>  
 <span data-ttu-id="8089d-106">クエリおよびビュー デザイナーは、次のガイドラインに従って列を処理します。</span><span class="sxs-lookup"><span data-stu-id="8089d-106">The Query and View Designer uses the following guidelines for working with columns:</span></span>  
  
-   <span data-ttu-id="8089d-107">[グループ化] オプションを選択したり、クエリに集計関数を追加したりすると、出力が指定されている列または並べ替えの対象となる列はすべて、自動的に GROUP BY 句に追加されます。</span><span class="sxs-lookup"><span data-stu-id="8089d-107">When you choose the Group By option or add an aggregate function to a query, all columns marked for output or used for sorting are automatically added to the GROUP BY clause.</span></span> <span data-ttu-id="8089d-108">既に集計関数の一部になっている列は、自動的に GROUP BY 句に追加されることはありません。</span><span class="sxs-lookup"><span data-stu-id="8089d-108">Columns are not automatically added to the GROUP BY clause if they are already part of an aggregate function.</span></span>  
  
     <span data-ttu-id="8089d-109">特定の列を GROUP BY 句に含めないようにするには、抽出条件ペインの [グループ化] 列で別のオプションを選択し、手動で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8089d-109">If you do not want a particular column to be part of the GROUP BY clause, you must manually change it by selecting a different option in the Group By column of the Criteria pane.</span></span> <span data-ttu-id="8089d-110">ただし、オプションを選択した結果、クエリが実行できなくなる場合もあります。クエリおよびビュー デザイナーでは、これが回避されません。</span><span class="sxs-lookup"><span data-stu-id="8089d-110">However, the Query and View Designer will not prevent you from choosing an option that can result in a query that will not run.</span></span>  
  
-   <span data-ttu-id="8089d-111">抽出条件ペインまたは SQL ペインで集計関数にクエリ出力列を手動で追加した場合でも、他の出力列がクエリから自動的に削除されることはありません。</span><span class="sxs-lookup"><span data-stu-id="8089d-111">If you manually add a query output column to an aggregate function in either the Criteria or SQL pane, the Query and View Designer does not automatically remove other output columns from the query.</span></span> <span data-ttu-id="8089d-112">したがって、残りの列をクエリ出力から削除するか、GROUP BY 句または集計関数の一部にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8089d-112">Therefore, you must remove the remaining columns from the query output or make them part of the GROUP BY clause or of an aggregate function.</span></span>  
  
 <span data-ttu-id="8089d-113">抽出条件ペインの [フィルター] 列に検索条件を入力すると、クエリおよびビュー デザイナーは次の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="8089d-113">When you enter a search condition into the Filter column of the Criteria pane, the Query and View Designer follows these rules:</span></span>  
  
-   <span data-ttu-id="8089d-114">集計クエリを指定していないためにグリッドの **[グループ化]** 列が表示されていない場合、検索条件は WHERE 句に配置されます。</span><span class="sxs-lookup"><span data-stu-id="8089d-114">If the **Group By** column of the grid is not displayed (because you have not yet specified an aggregate query), the search condition is placed into the WHERE clause.</span></span>  
  
-   <span data-ttu-id="8089d-115">既に集計クエリを指定していて、 **[グループ化]** 列の **[Where]** オプションを選択している場合、検索条件は WHERE 句に配置されます。</span><span class="sxs-lookup"><span data-stu-id="8089d-115">If you are already in an aggregate query and have selected the option **Where** in the **Group By** column, the search condition is placed into the WHERE clause.</span></span>  
  
-   <span data-ttu-id="8089d-116">**[グループ化]** 列に **[Where]** 以外の値が指定されている場合、検索条件は HAVING 句に配置されます。</span><span class="sxs-lookup"><span data-stu-id="8089d-116">If the **Group By** column contains any value other than **Where**, the search condition is placed in the HAVING clause.</span></span>  
  
## <a name="using-the-having-and-where-clauses"></a><span data-ttu-id="8089d-117">HAVING 句と WHERE 句の使用</span><span class="sxs-lookup"><span data-stu-id="8089d-117">Using the HAVING and WHERE Clauses</span></span>  
 <span data-ttu-id="8089d-118">次の原則は、検索条件で集計クエリの列を参照する方法を説明したものです。</span><span class="sxs-lookup"><span data-stu-id="8089d-118">The following principles describe how you can reference columns in an aggregate query in search conditions.</span></span> <span data-ttu-id="8089d-119">通常、検索条件に列を使用すると、集約する行をフィルターで選択したり (WHERE 句)、最終出力に表示されるグループ化の結果を決定したり (HAVING 句) できます。</span><span class="sxs-lookup"><span data-stu-id="8089d-119">In general, you can use a column in a search condition to filter the rows that should be summarized (a WHERE clause) or to determine which grouped results appear in the final output (a HAVING clause).</span></span>  
  
-   <span data-ttu-id="8089d-120">個別のデータ列は、クエリ内の他の場所でどのように使われているかよって、WHERE 句または HAVING 句に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8089d-120">Individual data columns can appear in either the WHERE or HAVING clause, depending on how they are used elsewhere in the query.</span></span>  
  
-   <span data-ttu-id="8089d-121">WHERE 句は、集計およびグループ化する行のサブセットを選択するために使用されるので、グループ化の前に適用されます。</span><span class="sxs-lookup"><span data-stu-id="8089d-121">WHERE clauses are used to select a subset of rows for summarizing and grouping and are thus applied before any grouping is done.</span></span> <span data-ttu-id="8089d-122">したがって、データ列が GROUP BY 句の一部でない場合や、集計関数に含まれていない場合でも、WHERE 句で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8089d-122">Therefore, you can use a data column in a WHERE clause even if it is not part of the GROUP BY clause or contained in an aggregate function.</span></span> <span data-ttu-id="8089d-123">たとえば、次のステートメントでは、価格が $10.00 を超えるすべての書名を選択し、平均価格を計算します。</span><span class="sxs-lookup"><span data-stu-id="8089d-123">For example, the following statement selects all titles that cost more than $10.00 and averages the price:</span></span>  
  
    ```  
    SELECT AVG(price)  
    FROM titles  
    WHERE price > 10  
    ```  
  
-   <span data-ttu-id="8089d-124">GROUP BY 句または集計関数で使われている列を含めて検索条件を作成する場合、検索条件は WHERE 句または HAVING 句として使用できます。どちらを使用するはその条件の作成時に決定できます。</span><span class="sxs-lookup"><span data-stu-id="8089d-124">If you create a search condition that involves a column also used in a GROUP BY clause or aggregate function, the search condition can appear as either a WHERE clause or a HAVING clause - you can decide which when you create the condition.</span></span> <span data-ttu-id="8089d-125">たとえば、次のステートメントでは、出版社ごとに本の平均価格を計算し、$10.00 を超える出版社の平均価格を表示します。</span><span class="sxs-lookup"><span data-stu-id="8089d-125">For example, the following statement creates an average price for the titles for each publisher, then displays the average for the publishers in which the average price is greater than $10.00:</span></span>  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
    ```  
  
-   <span data-ttu-id="8089d-126">検索条件の中で集計関数を使う場合は、条件に集計を含むことになるため、HAVING 句に入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8089d-126">If you use an aggregate function in a search condition, the condition involves a summary and must therefore be part of the HAVING clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8089d-127">参照</span><span class="sxs-lookup"><span data-stu-id="8089d-127">See Also</span></span>  
 <span data-ttu-id="8089d-128">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8089d-128">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="8089d-129">クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8089d-129">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
