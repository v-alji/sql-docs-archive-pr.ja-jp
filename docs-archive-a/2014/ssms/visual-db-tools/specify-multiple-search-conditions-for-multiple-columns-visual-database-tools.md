---
title: 複数の列に対して複数の検索条件を指定する方法 (Visual Database Tools) |Microsoft Docs
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
ms.assetid: 06617729-0d0b-4da2-9890-b7e2f5cdbc7b
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccf08a98d39d4ab808b7c2df794164b341be363a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634196"
---
# <a name="specify-multiple-search-conditions-for-multiple-columns-visual-database-tools"></a><span data-ttu-id="23b56-102">複数の列に対して複数の検索条件を指定する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="23b56-102">Specify Multiple Search Conditions for Multiple Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="23b56-103">検索条件に複数のデータ列を指定して、クエリの範囲を広くしたり狭くしたりできます。</span><span class="sxs-lookup"><span data-stu-id="23b56-103">You can expand or narrow the scope of your query by including several data columns as part of your search condition.</span></span> <span data-ttu-id="23b56-104">たとえば、次の場合です。</span><span class="sxs-lookup"><span data-stu-id="23b56-104">For example, you might want to:</span></span>  
  
-   <span data-ttu-id="23b56-105">勤続年数が 5 年以上の従業員または特定の職務を担当している従業員を検索する場合</span><span class="sxs-lookup"><span data-stu-id="23b56-105">Search for employees who either have worked more than five years at the company or who hold certain jobs.</span></span>  
  
-   <span data-ttu-id="23b56-106">特定の出版社によって出版された、料理に関する本を検索する場合</span><span class="sxs-lookup"><span data-stu-id="23b56-106">Search for a book that is both published by a specific publisher and pertains to cooking.</span></span>  
  
 <span data-ttu-id="23b56-107">複数列のいずれかで値を検索するクエリを作成するには、OR 条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="23b56-107">To create a query that searches for values in either of two (or more) columns, you specify an OR condition.</span></span> <span data-ttu-id="23b56-108">複数列ですべての条件を満たすクエリを作成するには、AND 条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="23b56-108">To create a query that must meet all conditions in two (or more) columns, you specify an AND condition.</span></span>  
  
## <a name="specifying-an-or-condition"></a><span data-ttu-id="23b56-109">OR 条件の指定</span><span class="sxs-lookup"><span data-stu-id="23b56-109">Specifying an OR Condition</span></span>  
 <span data-ttu-id="23b56-110">複数の条件を OR で結合するには、各条件を抽出条件ペインの個別の列で指定します。</span><span class="sxs-lookup"><span data-stu-id="23b56-110">To create multiple conditions linked with OR, you put each separate condition in a different column of the Criteria pane.</span></span>  
  
#### <a name="to-specify-an-or-condition-for-two-different-columns"></a><span data-ttu-id="23b56-111">2 つの異なる列に OR 条件を指定するには</span><span class="sxs-lookup"><span data-stu-id="23b56-111">To specify an OR condition for two different columns</span></span>  
  
1.  <span data-ttu-id="23b56-112">[抽出条件ペイン](visual-database-tools.md)に検索する列を追加します。</span><span class="sxs-lookup"><span data-stu-id="23b56-112">In the [Criteria Pane](visual-database-tools.md), add the columns you want to search.</span></span>  
  
2.  <span data-ttu-id="23b56-113">最初に検索する列の **[フィルター]** 列に最初の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="23b56-113">In the **Filter** column for the first column to search, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="23b56-114">2 番目に検索するデータ列の **[または...]** 列に 2 番目の条件を指定し、 **[フィルター]** 列は空白にしておきます。</span><span class="sxs-lookup"><span data-stu-id="23b56-114">In the **Or...** column for the second data column to search, specify the second condition, leaving the **Filter** column blank.</span></span>  
  
     <span data-ttu-id="23b56-115">クエリおよびビュー デザイナーは、OR 条件を含む WHERE 句を次のように作成します。</span><span class="sxs-lookup"><span data-stu-id="23b56-115">The Query and View Designer creates a WHERE clause that contains an OR condition such as the following:</span></span>  
  
    ```  
    SELECT job_lvl, hire_date  
    FROM employee  
    WHERE (job_lvl >= 200) OR   
      (hire_date < '01/01/1998')  
    ```  
  
4.  <span data-ttu-id="23b56-116">条件を追加するたびに、手順 2. および手順 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="23b56-116">Repeat Steps 2 and 3 for each additional condition you want to add.</span></span> <span data-ttu-id="23b56-117">新しい条件には、それぞれ別の **[または]** 列を使用します。</span><span class="sxs-lookup"><span data-stu-id="23b56-117">Use a different **Or...** column for each new condition.</span></span>  
  
## <a name="specifying-an-and-condition"></a><span data-ttu-id="23b56-118">AND 条件の指定</span><span class="sxs-lookup"><span data-stu-id="23b56-118">Specifying an AND Condition</span></span>  
 <span data-ttu-id="23b56-119">条件を AND で結合して複数のデータ列を検索するには、グリッドの **[フィルター]** 列にすべての条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="23b56-119">To search different data columns using conditions linked with AND, you put all the conditions in the **Filter** column of the grid.</span></span>  
  
#### <a name="to-specify-an-and-condition-for-two-different-columns"></a><span data-ttu-id="23b56-120">AND 条件を指定して 2 つの異なる列を検索するには</span><span class="sxs-lookup"><span data-stu-id="23b56-120">To specify an AND condition for two different columns</span></span>  
  
1.  <span data-ttu-id="23b56-121">[抽出条件ペイン](visual-database-tools.md)に検索する列を追加します。</span><span class="sxs-lookup"><span data-stu-id="23b56-121">In the [Criteria Pane](visual-database-tools.md), add the columns you want to search.</span></span>  
  
2.  <span data-ttu-id="23b56-122">最初に検索するデータ列の **[フィルター]** 列に最初の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="23b56-122">In the **Filter** column for the first data column to search, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="23b56-123">2 番目のデータ列の **[フィルター]** 列に 2 番目の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="23b56-123">In the **Filter** column for the second data column, specify the second condition.</span></span>  
  
     <span data-ttu-id="23b56-124">クエリおよびビュー デザイナーは、AND 条件を含む WHERE 句を次のように作成します。</span><span class="sxs-lookup"><span data-stu-id="23b56-124">The Query and View Designer creates a WHERE clause that contains an AND condition such as the following:</span></span>  
  
    ```  
    SELECT pub_id, title  
    FROM titles  
    WHERE (pub_id = '0877') AND (title LIKE '%Cook%')  
    ```  
  
4.  <span data-ttu-id="23b56-125">条件を追加するたびに、手順 2. および手順 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="23b56-125">Repeat Steps 2 and 3 for each additional condition you want to add.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b56-126">参照</span><span class="sxs-lookup"><span data-stu-id="23b56-126">See Also</span></span>  
 <span data-ttu-id="23b56-127">[Visual Database Tools &#40;とが優先される場合の条件の結合&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="23b56-127">[Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="23b56-128">[Visual Database Tools &#40;またはが優先される場合に条件を結合&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="23b56-128">[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="23b56-129">[抽出条件ペインで検索条件を組み合わせる場合の規則 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="23b56-129">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="23b56-130">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="23b56-130">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
