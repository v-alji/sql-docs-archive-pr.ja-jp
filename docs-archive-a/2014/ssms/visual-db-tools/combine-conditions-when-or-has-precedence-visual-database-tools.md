---
title: OR が優先する場合の条件の結合 (Visual Database Tools) | Microsoft Docs
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
- OR operator
ms.assetid: b30f5ac9-25e7-4163-80ed-44e4bccb455d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8be0d2f783c28662eb01f6bf191dc24d339534f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711482"
---
# <a name="combine-conditions-when-or-has-precedence-visual-database-tools"></a><span data-ttu-id="8258e-102">OR が優先する場合の条件の結合 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8258e-102">Combine Conditions When OR Has Precedence (Visual Database Tools)</span></span>
  <span data-ttu-id="8258e-103">AND で結合した条件よりも OR で結合した条件を優先させるには、各 OR 条件に対して AND 条件を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8258e-103">To link conditions with OR and give them precedence over conditions linked with AND, you must repeat the AND condition for each OR condition.</span></span>  
  
 <span data-ttu-id="8258e-104">たとえば、5 年以上前に入社した従業員のうち、初級レベルの仕事に従事している従業員または退職した従業員を検索すると仮定します。</span><span class="sxs-lookup"><span data-stu-id="8258e-104">For example, imagine that you want to find all employees who have been with the company more than five years and have lower-level jobs or are retired.</span></span> <span data-ttu-id="8258e-105">このクエリには、次の 3 つの条件が必要であり、その中の 2 つの条件に対して 1 つの条件を AND で結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8258e-105">This query requires three conditions, a single condition linked to two additional conditions with AND:</span></span>  
  
-   <span data-ttu-id="8258e-106">入社日が 5 年以上前の従業員であり、</span><span class="sxs-lookup"><span data-stu-id="8258e-106">Employees with a hire date earlier than five years ago, and</span></span>  
  
-   <span data-ttu-id="8258e-107">職務レベルが 100 または状態が "R" (退職者を示す) の従業員</span><span class="sxs-lookup"><span data-stu-id="8258e-107">Employees with a job level of 100 or whose status is "R" (for retired).</span></span>  
  
 <span data-ttu-id="8258e-108">抽出条件ペインでこの種のクエリを作成する方法を次の手順で説明します。</span><span class="sxs-lookup"><span data-stu-id="8258e-108">The following procedure illustrates how to create this type of query in the Criteria pane.</span></span>  
  
### <a name="to-combine-conditions-when-or-has-precedence"></a><span data-ttu-id="8258e-109">OR が優先する場合に条件を結合するには</span><span class="sxs-lookup"><span data-stu-id="8258e-109">To combine conditions when OR has precedence</span></span>  
  
1.  <span data-ttu-id="8258e-110">[抽出条件ペイン](visual-database-tools.md)に検索するデータ列を追加します。</span><span class="sxs-lookup"><span data-stu-id="8258e-110">In the [Criteria pane](visual-database-tools.md), add the data columns you want to search.</span></span> <span data-ttu-id="8258e-111">AND で結合された複数の条件を使用して同じ列を検索する場合は、検索する値ごとにデータ列名をグリッドに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8258e-111">If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.</span></span>  
  
2.  <span data-ttu-id="8258e-112">複数の条件を OR で結合するには、最初の条件を **[フィルター]** グリッド列に、2 番目の条件を別の **[または...]** 列に入力します。3 番目以降の条件も同様に入力します。</span><span class="sxs-lookup"><span data-stu-id="8258e-112">Create the conditions to be linked with OR by entering the first one into the **Filter** grid column and the second (and subsequent ones) into separate **Or...** columns.</span></span> <span data-ttu-id="8258e-113">たとえば、 `job_lvl` 列の条件と `status` 列の条件を OR で結合して検索するには、 `= 100` の **[フィルター]** 列に「 `job_lvl` 」、 `= 'R'` の **[または...]** 列に「 `status`」のように値を入力します。</span><span class="sxs-lookup"><span data-stu-id="8258e-113">For example, to link conditions with OR that search the `job_lvl` and `status` columns, enter `= 100` in the **Filter** column for `job_lvl` and `= 'R'` in the **Or...** column for `status`.</span></span>  
  
     <span data-ttu-id="8258e-114">グリッドに値を入力すると、SQL ペインでステートメントの WHERE 句が次のように作成されます。</span><span class="sxs-lookup"><span data-stu-id="8258e-114">Entering these values in the grid produces the following WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (job_lvl = 100) OR (status = 'R')  
    ```  
  
3.  <span data-ttu-id="8258e-115">各 OR 条件に 1 つずつ AND 条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="8258e-115">Create the AND condition by entering it once for each OR condition.</span></span> <span data-ttu-id="8258e-116">該当する OR 条件と同じグリッド列に各 AND 条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="8258e-116">Place each entry in the same grid column as the OR condition it corresponds to.</span></span> <span data-ttu-id="8258e-117">たとえば、 `hire_date` 列を検索し、両方の OR 条件に適用される AND 条件を追加するには、[条件] 列と `< '1/1/91'` [または...] **列の両方に「** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8258e-117">For example, to add an AND condition that searches the `hire_date` column and applies to both OR conditions, enter `< '1/1/91'` in both the Criteria column and the **Or...** column.</span></span>  
  
     <span data-ttu-id="8258e-118">グリッドに値を入力すると、SQL ペインでステートメントの WHERE 句が次のように作成されます。</span><span class="sxs-lookup"><span data-stu-id="8258e-118">Entering these values in the grid produces the following WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (job_lvl = 100) AND   
      (hire_date < '01/01/91' ) OR  
      (status = 'R') AND   
      (hire_date < '01/01/91' )  
    ```  
  
    > [!TIP]  
    >  <span data-ttu-id="8258e-119">AND 条件を 1 回追加した後で、 **[編集]** メニューの **[切り取り]** および **[貼り付け]** をクリックすると、他の OR 条件に対しても同じ AND 条件を繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="8258e-119">You can repeat an AND condition by adding it once, and then using the **Cut** and **Paste** commands from the **Edit** menu to repeat it for other OR conditions.</span></span>  
  
 <span data-ttu-id="8258e-120">クエリおよびビュー デザイナーによって作成される WHERE 句は、かっこを使用して OR が AND より優先することを示す次の WHERE 句と同じです。</span><span class="sxs-lookup"><span data-stu-id="8258e-120">The WHERE clause created by the Query and View Designer is equivalent to the following WHERE clause, which uses parentheses to specify the precedence of OR over AND:</span></span>  
  
```  
WHERE (job_lvl = 100 OR status = 'R') AND  
   (hire_date < '01/01/91')  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8258e-121">[SQL ペイン](sql-pane-visual-database-tools.md)に上の形式で検索条件を入力した後でダイアグラム ペインまたは抽出条件ペインでクエリを変更した場合、クエリおよびビュー デザイナーで再度作成される SQL ステートメントの形式は、両方の OR 条件に AND 条件が明示的に適用される形式になります。</span><span class="sxs-lookup"><span data-stu-id="8258e-121">If you enter the search conditions in the format shown immediately above in the [SQL Pane](sql-pane-visual-database-tools.md), but then make a change to the query in the Diagram or Criteria panes, the Query and View Designer recreates the SQL statement to match the form with the AND condition explicitly distributed to both OR conditions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8258e-122">参照</span><span class="sxs-lookup"><span data-stu-id="8258e-122">See Also</span></span>  
 <span data-ttu-id="8258e-123">[抽出条件ペインで検索条件を組み合わせる場合の規則 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8258e-123">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="8258e-124">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8258e-124">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
