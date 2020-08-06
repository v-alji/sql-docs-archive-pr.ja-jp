---
title: 1つの列に対して複数の検索条件を指定する方法 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 2c006e36-56b1-4992-89b4-c6c0b19808f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a07322120bd3b3f543e6f54fa50cdf75aa32be59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640316"
---
# <a name="specify-multiple-search-conditions-for-one-column-visual-database-tools"></a><span data-ttu-id="428b2-102">1 つの列に対して複数の検索条件を指定する方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="428b2-102">Specify Multiple Search Conditions for One Column (Visual Database Tools)</span></span>
  <span data-ttu-id="428b2-103">場合によっては、同じデータ列に複数の検索条件を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="428b2-103">In some instances, you might want to apply a number of search conditions to the same data column.</span></span> <span data-ttu-id="428b2-104">たとえば、次の場合です。</span><span class="sxs-lookup"><span data-stu-id="428b2-104">For example, you might want to:</span></span>  
  
-   <span data-ttu-id="428b2-105">`employee` テーブルから複数の従業員名を検索したり、異なる給与範囲の従業員を検索したりする場合。</span><span class="sxs-lookup"><span data-stu-id="428b2-105">Search for several different names in an `employee` table or for employees who are in different salary ranges.</span></span> <span data-ttu-id="428b2-106">この種の検索には OR 条件を使用します。</span><span class="sxs-lookup"><span data-stu-id="428b2-106">This type of search requires an OR condition.</span></span>  
  
-   <span data-ttu-id="428b2-107">"The" で始まり、"Cook" を含む書名を検索する場合。</span><span class="sxs-lookup"><span data-stu-id="428b2-107">Search for a book title that both starts with the word "The" and contains the word "Cook."</span></span> <span data-ttu-id="428b2-108">この種の検索には AND 条件を使用します。</span><span class="sxs-lookup"><span data-stu-id="428b2-108">This type of search requires an AND condition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="428b2-109">このトピックの内容は、クエリの WHERE 句および HAVING 句の検索条件に該当します。</span><span class="sxs-lookup"><span data-stu-id="428b2-109">The information in this topic applies to search conditions in both the WHERE and HAVING clauses of a query.</span></span> <span data-ttu-id="428b2-110">例では WHERE 句の作成を取り扱いますが、どちらの句の検索条件にも同じ原則が当てはまります。</span><span class="sxs-lookup"><span data-stu-id="428b2-110">The examples focus on creating WHERE clauses, but the principles apply to both types of search conditions.</span></span>  
  
 <span data-ttu-id="428b2-111">同じデータ列で代替値を検索するには、OR 条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="428b2-111">To search for alternative values in the same data column, you specify an OR condition.</span></span> <span data-ttu-id="428b2-112">複数の条件を満たす値を検索するには、AND 条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="428b2-112">To search for values that meet several conditions, you specify an AND condition.</span></span>  
  
## <a name="specifying-an-or-condition"></a><span data-ttu-id="428b2-113">OR 条件の指定</span><span class="sxs-lookup"><span data-stu-id="428b2-113">Specifying an OR Condition</span></span>  
 <span data-ttu-id="428b2-114">OR 条件を使用すると、1 つの列に対して複数の代替値を検索条件として指定できます。</span><span class="sxs-lookup"><span data-stu-id="428b2-114">Using an OR condition enables you to specify several alternative values to search for in a column.</span></span> <span data-ttu-id="428b2-115">この方法では検索範囲が広くなるため、1 つの値を検索した場合に比べて、検索結果として返される行数が多くなります。</span><span class="sxs-lookup"><span data-stu-id="428b2-115">This option expands the scope of the search and can return more rows than searching for a single value.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="428b2-116">同じデータ列で複数の値を検索する代わりに、IN 演算子を使用する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="428b2-116">You can often use the IN operator instead to search for multiple values in the same data column.</span></span>  
  
#### <a name="to-specify-an-or-condition"></a><span data-ttu-id="428b2-117">OR 条件を指定するには</span><span class="sxs-lookup"><span data-stu-id="428b2-117">To specify an OR condition</span></span>  
  
1.  <span data-ttu-id="428b2-118">[抽出条件ペイン](visual-database-tools.md)に検索する列を追加します。</span><span class="sxs-lookup"><span data-stu-id="428b2-118">In the [Criteria Pane](visual-database-tools.md), add the column to search.</span></span>  
  
2.  <span data-ttu-id="428b2-119">追加したデータ列の **[フィルター]** 列に最初の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="428b2-119">In the **Filter** column for the data column you just added, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="428b2-120">同じデータ列の **[または...]** 列に、2 番目の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="428b2-120">In the **Or...** column for the same data column, specify the second condition.</span></span>  
  
 <span data-ttu-id="428b2-121">クエリおよびビュー デザイナーは、OR 条件を含む WHERE 句を次のように作成します。</span><span class="sxs-lookup"><span data-stu-id="428b2-121">The Query and View Designer creates a WHERE clause that contains an OR condition such as the following:</span></span>  
  
```  
SELECT fname, lname  
FROM employees  
WHERE (salary < 30000) OR (salary > 100000)  
```  
  
## <a name="specifying-an-and-condition"></a><span data-ttu-id="428b2-122">AND 条件の指定</span><span class="sxs-lookup"><span data-stu-id="428b2-122">Specifying an AND Condition</span></span>  
 <span data-ttu-id="428b2-123">AND 条件を使用すると、複数の条件を満たす列の値だけが、結果セットの行に含まれるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="428b2-123">Using an AND condition enables you to specify that values in a column must meet two (or more) conditions for the row to be included in the result set.</span></span> <span data-ttu-id="428b2-124">この方法では検索範囲が狭くなるため、通常は、1 つの値を検索した場合よりも、検索結果として返される行数が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="428b2-124">This option narrows the scope of the search and usually returns fewer rows than searching for a single value.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="428b2-125">一定の範囲の値を検索する場合は、2 つの条件を AND で結合する代わりに、BETWEEN 演算子を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="428b2-125">If you are searching for a range of values, you can use the BETWEEN operator instead of linking two conditions with AND.</span></span>  
  
#### <a name="to-specify-an-and-condition"></a><span data-ttu-id="428b2-126">AND 条件を指定するには</span><span class="sxs-lookup"><span data-stu-id="428b2-126">To specify an AND condition</span></span>  
  
1.  <span data-ttu-id="428b2-127">抽出条件ペインに検索する列を追加します。</span><span class="sxs-lookup"><span data-stu-id="428b2-127">In the Criteria pane, add the column to search.</span></span>  
  
2.  <span data-ttu-id="428b2-128">追加したデータ列の **[フィルター]** 列に最初の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="428b2-128">In the **Filter** column for the data column you just added, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="428b2-129">抽出条件ペインのグリッドの空白行に再度同じデータ列を追加します。</span><span class="sxs-lookup"><span data-stu-id="428b2-129">Add the same data column to the Criteria pane again, placing it in an empty row of the grid.</span></span>  
  
4.  <span data-ttu-id="428b2-130">2 番目のデータ列の **[フィルター]** 列に 2 番目の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="428b2-130">In the **Filter** column for the second instance of the data column, specify the second condition.</span></span>  
  
 <span data-ttu-id="428b2-131">クエリ デザイナーは、AND 条件を含む WHERE 句を次のように作成します。</span><span class="sxs-lookup"><span data-stu-id="428b2-131">The Query Designer creates a WHERE clause that contains an AND condition such as the following:</span></span>  
  
```  
SELECT title_id, title  
FROM titles  
WHERE (title LIKE '%Cook%') AND   
  (title LIKE '%Recipe%')  
```  
  
## <a name="see-also"></a><span data-ttu-id="428b2-132">参照</span><span class="sxs-lookup"><span data-stu-id="428b2-132">See Also</span></span>  
 <span data-ttu-id="428b2-133">[抽出条件ペインで検索条件を組み合わせる場合の規則 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="428b2-133">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="428b2-134">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="428b2-134">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
