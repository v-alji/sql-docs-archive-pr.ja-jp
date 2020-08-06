---
title: AND が優先する場合の条件を結合する (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], combining
- precedence [SQL Server], Criteria pane
- search criteria [SQL Server], combining conditions
- combining search conditions
- AND, Criteria pane
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 917d5381bc83083ee1fa3c07375945c0908da521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711489"
---
# <a name="combine-conditions-when-and-has-precedence-visual-database-tools"></a><span data-ttu-id="09ae7-102">AND が優先する場合の条件を結合する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="09ae7-102">Combine Conditions When AND Has Precedence (Visual Database Tools)</span></span>
  <span data-ttu-id="09ae7-103">AND で条件を結合するには、クエリに対して列を 2 回 (各条件について 1 回ずつ) 追加します。</span><span class="sxs-lookup"><span data-stu-id="09ae7-103">To combine conditions with AND, you add the column to the query twice--once for each condition.</span></span> <span data-ttu-id="09ae7-104">OR で条件を結合するには、[フィルター] 列で最初の条件を指定し、次の条件を **[または...]** 列で指定します。</span><span class="sxs-lookup"><span data-stu-id="09ae7-104">To combine conditions with OR, you put the first one in the Filter column and additional conditions into an **Or...** column.</span></span>  
  
 <span data-ttu-id="09ae7-105">たとえば、初級レベルの仕事に従事している勤続 5 年以上の従業員、または入社日に関係なく中級レベルの仕事に従事している従業員を検索するとします。</span><span class="sxs-lookup"><span data-stu-id="09ae7-105">For example, imagine that you want to find either employees who have been with the company for more than five years in lower-level jobs or employees with middle-level jobs regardless of their hire date.</span></span> <span data-ttu-id="09ae7-106">このクエリには、3 つの条件が必要であり、その中の 2 つの条件を AND で結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09ae7-106">This query requires three conditions, two of them linked with AND:</span></span>  
  
-   <span data-ttu-id="09ae7-107">入社日が 5 年以上前で、かつ職務レベルが 100 の従業員</span><span class="sxs-lookup"><span data-stu-id="09ae7-107">Employees with a hire date earlier than five years ago AND with a job level of 100.</span></span>  
  
     <span data-ttu-id="09ae7-108">または</span><span class="sxs-lookup"><span data-stu-id="09ae7-108">-or-</span></span>  
  
-   <span data-ttu-id="09ae7-109">職務レベルが 200 の従業員</span><span class="sxs-lookup"><span data-stu-id="09ae7-109">Employees with a job level of 200.</span></span>  
  
### <a name="to-combine-conditions-when-and-has-precedence"></a><span data-ttu-id="09ae7-110">AND が優先する場合に条件を結合するには</span><span class="sxs-lookup"><span data-stu-id="09ae7-110">To combine conditions when AND has precedence</span></span>  
  
1.  <span data-ttu-id="09ae7-111">[抽出条件ペイン](visual-database-tools.md)に検索するデータ列を追加します。</span><span class="sxs-lookup"><span data-stu-id="09ae7-111">In the [Criteria pane](visual-database-tools.md), add the data columns you want to search.</span></span> <span data-ttu-id="09ae7-112">AND で結合された複数の条件を使用して同じ列を検索する場合は、検索する値ごとにデータ列名をグリッドに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09ae7-112">If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.</span></span>  
  
2.  <span data-ttu-id="09ae7-113">**[フィルター]** 列に、AND で結合する条件をすべて入力します。</span><span class="sxs-lookup"><span data-stu-id="09ae7-113">In the **Filter** column, enter all the conditions that you want to link with AND.</span></span> <span data-ttu-id="09ae7-114">たとえば、 `hire_date` 列の条件と `job_lvl` 列の条件を AND で結合して検索するには、対応する [フィルター] 列にそれぞれ `< '1/1/91'` および `= 100`と入力します。</span><span class="sxs-lookup"><span data-stu-id="09ae7-114">For example, to link conditions with AND that search the `hire_date` and `job_lvl` columns, enter the values `< '1/1/91'` and `= 100`, respectively, in the Filter column.</span></span>  
  
     <span data-ttu-id="09ae7-115">上のようにグリッドに値を入力すると、 [SQL ペイン](sql-pane-visual-database-tools.md)でステートメントの WHERE 句が次のように作成されます。</span><span class="sxs-lookup"><span data-stu-id="09ae7-115">These grid entries produce the following WHERE clause in the statement in the [SQL Pane](sql-pane-visual-database-tools.md):</span></span>  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  <span data-ttu-id="09ae7-116">**[または...]** グリッド列に OR で結合する条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="09ae7-116">In the **Or...** grid column, enter conditions that you want to link with OR.</span></span> <span data-ttu-id="09ae7-117">たとえば、 `job_lvl` 列の別の値を検索条件として追加するには、 **[または...]** 列に `= 200`などの値を追加入力します。</span><span class="sxs-lookup"><span data-stu-id="09ae7-117">For example, to add a condition that searches for another value in the `job_lvl` column, enter an additional value in the **Or...** column, such as `= 200`.</span></span>  
  
     <span data-ttu-id="09ae7-118">**[または...]** 列に値を追加すると、SQL ペインでは次のようにステートメントの WHERE 句に条件が追加されます。</span><span class="sxs-lookup"><span data-stu-id="09ae7-118">Adding a value in the **Or...** column adds another condition to the WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="09ae7-119">参照</span><span class="sxs-lookup"><span data-stu-id="09ae7-119">See Also</span></span>  
 <span data-ttu-id="09ae7-120">[Visual Database Tools &#40;またはが優先される場合に条件を結合&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="09ae7-120">[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="09ae7-121">[抽出条件ペインで検索条件を組み合わせる場合の規則 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="09ae7-121">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 <span data-ttu-id="09ae7-122">[Visual Database Tools &#40;検索値を入力するための規則&#41;](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="09ae7-122">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="09ae7-123">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="09ae7-123">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
