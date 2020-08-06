---
title: 抽出条件ペインで検索条件を組み合わせる場合の規則 (Visual Database Tools) |Microsoft Docs
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
- multiple OR clauses
- combining search conditions
- OR operator
- AND, Criteria pane
- multiple AND clauses
ms.assetid: d4859be5-ff5b-48b2-a101-ad40c6dbcc68
author: stevestein
ms.author: sstein
ms.openlocfilehash: 684521baa87d5325366a0e18296cd35342a0e947
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711486"
---
# <a name="conventions-for-combining-search-conditions-in-the-criteria-pane-visual-database-tools"></a><span data-ttu-id="7759a-102">抽出条件ペインで検索条件を組み合わせる場合の規則 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7759a-102">Conventions for Combining Search Conditions in the Criteria Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="7759a-103">クエリを作成する際には、任意の数の AND および OR 演算子で結合して任意の数の検索条件を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7759a-103">You can create queries that include any number of search conditions, linked with any number of AND and OR operators.</span></span> <span data-ttu-id="7759a-104">AND 句と OR 句を組み合わせたクエリは複雑になる場合があるため、そのようなクエリを実行したときにどのように解釈されるのか、およびそのようなクエリが[抽出条件ペイン](visual-database-tools.md)と [SQL ペイン](sql-pane-visual-database-tools.md)でどのように表現されるのかについて理解しておくと役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="7759a-104">A query with a combination of AND and OR clauses can become complex, so it is helpful to understand how such a query is interpreted when you execute it, and how such a query is represented in the [Criteria Pane](visual-database-tools.md) and [SQL Pane](sql-pane-visual-database-tools.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7759a-105">AND 演算子または OR 演算子を 1 つだけ含む検索条件の詳細については、「[1 つの列に対して複数の検索条件を指定する (Visual Database Tools)](specify-multiple-search-conditions-for-one-column-visual-database-tools.md)」および「[複数の列に対して複数の検索条件を指定する (Visual Database Tools)](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7759a-105">For details about search conditions that contain only one AND or OR operator, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md) and [Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="7759a-106">ここでは、以下について説明します。</span><span class="sxs-lookup"><span data-stu-id="7759a-106">Below you will find information about:</span></span>  
  
-   <span data-ttu-id="7759a-107">AND と OR の両方を含むクエリでの AND と OR の優先順位。</span><span class="sxs-lookup"><span data-stu-id="7759a-107">The precedence of AND and OR in queries that contain both.</span></span>  
  
-   <span data-ttu-id="7759a-108">AND 句と OR 句の条件の論理的な関係。</span><span class="sxs-lookup"><span data-stu-id="7759a-108">How the conditions in AND and OR clauses relate logically to one another.</span></span>  
  
-   <span data-ttu-id="7759a-109">クエリおよびビュー デザイナーの抽出条件ペインで、AND と OR の両方を含むクエリがどのように表現されるか。</span><span class="sxs-lookup"><span data-stu-id="7759a-109">How the Query and View Designer represents in the Criteria Pane queries that contain both AND and OR.</span></span>  
  
 <span data-ttu-id="7759a-110">以降の説明を理解しやすくするために、 `employee` テーブルに `hire_date`、 `job_lvl`、および `status`という列が含まれる場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="7759a-110">To help you understand the discussion below, imagine that you are working with an `employee` table containing the columns `hire_date`, `job_lvl`, and `status`.</span></span> <span data-ttu-id="7759a-111">以降の例では、各従業員がどのくらい長く会社に勤めているか (つまり、従業員が雇用された日付)、どのような種類の仕事をしているか (仕事のレベル)、従業員のステータス (退職など) などの情報が必要であると仮定しています。</span><span class="sxs-lookup"><span data-stu-id="7759a-111">The examples assume that you need to know information such as how long an employee has worked with the company (that is, what the employee's hire date is), what type of job the employee performs (what the job level is), and the employee's status (for example, retired).</span></span>  
  
## <a name="precedence-of-and-and-or"></a><span data-ttu-id="7759a-112">AND と OR の優先順位</span><span class="sxs-lookup"><span data-stu-id="7759a-112">Precedence of AND and OR</span></span>  
 <span data-ttu-id="7759a-113">クエリが実行されると、AND で結合された句が最初に評価され、次に OR で結合された句が評価されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-113">When a query is executed, it evaluates first the clauses linked with AND, and then those linked with OR.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7759a-114">NOT 演算子は AND と OR のいずれよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-114">The NOT operator takes precedence over both AND and OR.</span></span>  
  
 <span data-ttu-id="7759a-115">たとえば、初級レベルの仕事に 5 年以上勤務している従業員か、雇用された日付に関係なく中級レベルの仕事をしている従業員のいずれかを検索する場合は、次のような WHERE 句を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7759a-115">For example, to find either employees who have been with the company for more than five years in lower-level jobs or employees with middle-level jobs without regard for their hire date, you can construct a WHERE clause such as the following:</span></span>  
  
```  
WHERE   
   hire_date < '01/01/95' AND   
   job_lvl = 100 OR  
   job_lvl = 200  
  
```  
  
 <span data-ttu-id="7759a-116">AND が OR に優先する既定の優先順位をオーバーライドする場合は、SQL ペインで特定の条件をかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="7759a-116">To override the default precedence of AND over OR, you can put parentheses around specific conditions in the SQL pane.</span></span> <span data-ttu-id="7759a-117">かっこで囲まれた条件は常に最初に評価されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-117">Conditions in parentheses are always evaluated first.</span></span> <span data-ttu-id="7759a-118">たとえば、初級レベルまたは中級レベルの仕事に 5 年以上勤務している従業員をすべて検索する場合は、次のような WHERE 句を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7759a-118">For example, to find all employees who have been with the company more than five years in either lower or middle-level jobs, you can construct a WHERE clause such as the following:</span></span>  
  
```  
WHERE   
   hire_date < '01/01/95' AND   
   (job_lvl = 100 OR job_lvl = 200)  
```  
  
> [!TIP]  
>  <span data-ttu-id="7759a-119">わかりやすくするために、AND 句と OR 句を組み合わせるときは既定の優先順位を利用する代わりに、常にかっこを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7759a-119">It is recommended that, for clarity, you always include parentheses when combining AND and OR clauses instead of relying on the default precedence.</span></span>  
  
## <a name="how-and-works-with-multiple-or-clauses"></a><span data-ttu-id="7759a-120">複数の OR 句に対する AND の解釈</span><span class="sxs-lookup"><span data-stu-id="7759a-120">How AND Works with Multiple OR Clauses</span></span>  
 <span data-ttu-id="7759a-121">AND 句と OR 句を組み合わせたときのそれぞれの関係について把握すると、クエリおよびビュー デザイナーで複雑なクエリを作成し、それを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7759a-121">Understanding how AND and OR clauses are related when combined can help you construct and understand complex queries in the Query and View Designer.</span></span>  
  
 <span data-ttu-id="7759a-122">AND を使用して複数の条件を結合した場合、AND で結合された最初の条件のセットは、2 番目のセットの条件すべてに適用されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-122">If you link multiple conditions using AND, the first set of conditions linked with AND applies to all the conditions in the second set.</span></span> <span data-ttu-id="7759a-123">つまり、AND によって他の条件に結合された条件は、2 番目のセット内のすべての条件に分配されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-123">In other words, a condition linked with AND to another condition is distributed to all the conditions in the second set.</span></span> <span data-ttu-id="7759a-124">たとえば、次の概略表現は、OR 条件のセットに結合された AND 条件を示しています。</span><span class="sxs-lookup"><span data-stu-id="7759a-124">For example, the following schematic representation shows an AND condition linked to a set of OR conditions:</span></span>  
  
```  
A AND (B OR C)  
```  
  
 <span data-ttu-id="7759a-125">この表現は、次の概略表現と論理的に等価です。ここでは、AND 条件が 2 番目の条件のセットにどのように分配されるかが示されています。</span><span class="sxs-lookup"><span data-stu-id="7759a-125">The representation above is logically equivalent to the following schematic representation, which shows how the AND condition is distributed to the second set of conditions:</span></span>  
  
```  
(A AND B) OR (A AND C)  
```  
  
 <span data-ttu-id="7759a-126">この分散法則は、クエリおよびビュー デザイナーの使用方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="7759a-126">This distributive principle affects how you use the Query and View Designer.</span></span> <span data-ttu-id="7759a-127">たとえば、初級レベルまたは中級レベルの仕事に 5 年以上勤務している従業員をすべて検索する場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="7759a-127">For example, imagine that you are looking for all employees who have been with the company more than five years in either lower or middle-level jobs.</span></span> <span data-ttu-id="7759a-128">SQL ペインで次の WHERE 句をステートメントに入力します。</span><span class="sxs-lookup"><span data-stu-id="7759a-128">You enter the following WHERE clause into the statement in the SQL pane:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
   (job_lvl = 100 OR job_lvl = 200)  
```  
  
 <span data-ttu-id="7759a-129">AND で結合されている句は、OR で結合されている両方の句に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-129">The clause linked with AND applies to both clauses linked with OR.</span></span> <span data-ttu-id="7759a-130">これを明確に表現する方法は、OR 句の各条件に対して 1 回ずつ AND 条件を繰り返すことです。</span><span class="sxs-lookup"><span data-stu-id="7759a-130">An explicit way to express this is to repeat the AND condition once for each condition in the OR clause.</span></span> <span data-ttu-id="7759a-131">次のステートメントは上記のステートメントよりも明確であると同時に長くなっていますが、論理的には等価です。</span><span class="sxs-lookup"><span data-stu-id="7759a-131">The following statement is more explicit (and longer) than the previous statement, but is logically equivalent to it:</span></span>  
  
```  
WHERE    (hire_date < '01/01/95' ) AND  
  (job_lvl = 100) OR   
  (hire_date < '01/01/95' ) AND   
  (job_lvl = 200)  
```  
  
 <span data-ttu-id="7759a-132">結合されている OR 句に AND 句を分配する法則は、含まれるそれぞれの条件の数に関係なく適用されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-132">The principle of distributing AND clauses to linked OR clauses applies no matter how many individual conditions are involved.</span></span> <span data-ttu-id="7759a-133">たとえば、5 年以上勤務しているか、または退職した上級レベルまたは中級レベルの従業員を検索する場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="7759a-133">For example, imagine that you want to find higher or middle-level employees who have been with the company more than five years or are retired.</span></span> <span data-ttu-id="7759a-134">WHERE 句は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7759a-134">The WHERE clause might look like this:</span></span>  
  
```  
WHERE   
   (job_lvl = 200 OR job_lvl = 300) AND  
   (hire_date < '01/01/95' ) OR (status = 'R')  
```  
  
 <span data-ttu-id="7759a-135">AND で結合された条件を分配すると、WHERE 句は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7759a-135">After the conditions linked with AND have been distributed, the WHERE clause will look like this:</span></span>  
  
```  
WHERE   
   (job_lvl = 200 AND hire_date < '01/01/95' ) OR  
   (job_lvl = 200 AND status = 'R') OR  
   (job_lvl = 300 AND hire_date < '01/01/95' ) OR  
   (job_lvl = 300 AND status = 'R')   
```  
  
## <a name="how-multiple-and-and-or-clauses-are-represented-in-the-criteria-pane"></a><span data-ttu-id="7759a-136">抽出条件ペインでの複数の AND 句および OR 句の表示</span><span class="sxs-lookup"><span data-stu-id="7759a-136">How Multiple AND and OR Clauses Are Represented in the Criteria Pane</span></span>  
 <span data-ttu-id="7759a-137">クエリおよびビュー デザイナーは、検索条件を [抽出条件ペイン](visual-database-tools.md)に表示します。</span><span class="sxs-lookup"><span data-stu-id="7759a-137">The Query and View Designer represents your search conditions in the [Criteria Pane](visual-database-tools.md).</span></span> <span data-ttu-id="7759a-138">ただし、AND および OR で結合された複数の句が含まれていると、抽出条件ペインで期待どおりに表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7759a-138">However, in some cases that involve multiple clauses linked with AND and OR, the representation in the Criteria Pane might not be what you expect.</span></span> <span data-ttu-id="7759a-139">また、抽出条件ペインや [ダイアグラム ペイン](diagram-pane-visual-database-tools.md)でクエリを変更すると、SQL ステートメントの入力時の内容も変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="7759a-139">In addition, if you modify your query in the Criteria Pane or [Diagram Pane](diagram-pane-visual-database-tools.md), you might find that your SQL statement has been changed from what you entered.</span></span>  
  
 <span data-ttu-id="7759a-140">一般に、AND 句と OR 句が抽出条件ペインでどのように表示されるかは、次の規則に基づいています。</span><span class="sxs-lookup"><span data-stu-id="7759a-140">In general, these rules dictate how AND and OR clauses appear in the Criteria Pane:</span></span>  
  
-   <span data-ttu-id="7759a-141">AND で結合された条件はすべて、 **[フィルター]** グリッド列または同じ **[または...]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-141">All conditions linked with AND appear in the **Filter** grid column or in the same **Or...** column.</span></span>  
  
-   <span data-ttu-id="7759a-142">OR で結合された条件はすべて、別の **[または...]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-142">All conditions linked with OR appear in separate **Or...** columns.</span></span>  
  
-   <span data-ttu-id="7759a-143">AND 句と OR 句の組み合わせの論理的結果として AND がいくつかの OR 句に分配される場合、抽出条件ペインでは、AND 句を必要な数だけ繰り返すことによりこれを明確に表します。</span><span class="sxs-lookup"><span data-stu-id="7759a-143">If the logical result of a combination of AND and OR clauses is that the AND is distributed into several OR clauses, the Criteria Pane represents this explicitly by repeating the AND clause as many times as necessary.</span></span>  
  
 <span data-ttu-id="7759a-144">たとえば、SQL ペインで次のような検索条件を作成する場合を考えます。ここで、AND で結合された 2 つの句は OR で結合された 3 つ目の句よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-144">For example, in the SQL pane you might create a search condition such as the following, in which two clauses linked with AND take precedence over a third one linked with OR:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  (job_lvl = 100) OR   
  (status = 'R')  
```  
  
 <span data-ttu-id="7759a-145">クエリおよびビュー デザイナーは、この WHERE 句を次のように抽出条件ペインに表示します。</span><span class="sxs-lookup"><span data-stu-id="7759a-145">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="7759a-146">![[条件] ペインの OR 句の優先順位](../../database-engine/media//vs-criteriapane1.gif "[条件] ペインの OR 句の優先順位")</span><span class="sxs-lookup"><span data-stu-id="7759a-146">![OR clause precedence in the Criteria Pane](../../database-engine/media//vs-criteriapane1.gif "OR clause precedence in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="7759a-147">ただし、結合されている OR 句が AND 句よりも優先される場合は、各 OR 句に対して AND 句が繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-147">However, if the linked OR clauses take precedence over an AND clause, the AND clause is repeated for each OR clause.</span></span> <span data-ttu-id="7759a-148">その結果、AND 句が各 OR 句に分配されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-148">This causes the AND clause to be distributed to each OR clause.</span></span> <span data-ttu-id="7759a-149">たとえば、SQL ペインで次のような WHERE 句を作成したとします。</span><span class="sxs-lookup"><span data-stu-id="7759a-149">For example, in the SQL pane you might create a WHERE clause such as the following:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  ( (job_lvl = 100) OR   
  (status = 'R') )  
```  
  
 <span data-ttu-id="7759a-150">クエリおよびビュー デザイナーは、この WHERE 句を次のように抽出条件ペインに表示します。</span><span class="sxs-lookup"><span data-stu-id="7759a-150">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="7759a-151">![[条件] ペインの複数の AND 句と OR 句](../../database-engine/media//vs-criteriapane2.gif "[条件] ペインの複数の AND 句と OR 句")</span><span class="sxs-lookup"><span data-stu-id="7759a-151">![Multiple AND and OR clauses in the Criteria Pane](../../database-engine/media//vs-criteriapane2.gif "Multiple AND and OR clauses in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="7759a-152">結合された OR 句にデータ列が 1 つしか含まれない場合、クエリおよびビュー デザイナーはその OR 句全体をグリッドの 1 つのセルに配置することができるため、AND 句を繰り返さずに済みます。</span><span class="sxs-lookup"><span data-stu-id="7759a-152">If the linked OR clauses involve only one data column, the Query and View Designer can place the entire OR clause into a single cell of the grid, avoiding the need to repeat the AND clause.</span></span> <span data-ttu-id="7759a-153">たとえば、SQL ペインで次のような WHERE 句を作成したとします。</span><span class="sxs-lookup"><span data-stu-id="7759a-153">For example, in the SQL pane you might create a WHERE clause such as the following:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  ((status = 'R') OR (status = 'A'))  
```  
  
 <span data-ttu-id="7759a-154">クエリおよびビュー デザイナーは、この WHERE 句を次のように抽出条件ペインに表示します。</span><span class="sxs-lookup"><span data-stu-id="7759a-154">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="7759a-155">![[条件] ペインで定義されているリンク付き OR 句](../../database-engine/media//vs-criteriapane3.gif "[条件] ペインで定義されているリンク付き OR 句")</span><span class="sxs-lookup"><span data-stu-id="7759a-155">![Linked OR clauses defined in the Criteria Pane](../../database-engine/media//vs-criteriapane3.gif "Linked OR clauses defined in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="7759a-156">抽出条件ペインで値の 1 つを変更するなど、クエリに変更を加えると、クエリおよびビュー デザイナーによって SQL ペインの SQL ステートメントが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="7759a-156">If you make a change to the query (such as changing one of the values in the Criteria Pane), the Query and View Designer recreates the SQL statement in the SQL pane.</span></span> <span data-ttu-id="7759a-157">再作成された SQL ステートメントは、元のステートメントよりも抽出条件ペインの表示内容の方に近くなります。</span><span class="sxs-lookup"><span data-stu-id="7759a-157">The recreated SQL statement will resemble the Criteria Pane display rather than your original statement.</span></span> <span data-ttu-id="7759a-158">たとえば、抽出条件ペインに分配された AND 句が含まれる場合、SQL ペインで再作成されるステートメントには明示的に分配された AND 句が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7759a-158">For example, if the Criteria Pane contains distributed AND clauses, the resulting statement in the SQL pane will be recreated with explicit distributed AND clauses.</span></span> <span data-ttu-id="7759a-159">詳細については、このトピックの前の方にある「複数の OR 句に対する AND の解釈」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7759a-159">For details, see "How AND Works with Multiple OR Clauses" earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7759a-160">参照</span><span class="sxs-lookup"><span data-stu-id="7759a-160">See Also</span></span>  
 [<span data-ttu-id="7759a-161">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7759a-161">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
