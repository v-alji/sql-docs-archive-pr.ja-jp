---
title: テーブル以外のものを使用してクエリを作成する方法 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], queries
- queries [SQL Server], creating
ms.assetid: 8e4a1f0a-8a42-4733-be8d-e21d6dbddb33
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0444c20fe10080949930f23623d5699f7fd3712c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631458"
---
# <a name="create-queries-using-something-besides-a-table-visual-database-tools"></a><span data-ttu-id="ea980-102">テーブル以外のアイテムを使用したクエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ea980-102">Create Queries using Something Besides a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="ea980-103">検索クエリを作成するときは常に、必要な列、必要な行、およびクエリ プロセッサが基になるデータを検索する場所を明示します。</span><span class="sxs-lookup"><span data-stu-id="ea980-103">Whenever you write a retrieval query, you articulate what columns you want, what rows you want, and where the query processor should find the original data.</span></span> <span data-ttu-id="ea980-104">通常、この基になるデータは 1 つのテーブル、または相互に結合された複数のテーブルで構成されています。</span><span class="sxs-lookup"><span data-stu-id="ea980-104">Typically, this original data consists of a table or several tables joined together.</span></span> <span data-ttu-id="ea980-105">ただし、基になるデータは、テーブル以外のソースを使用してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="ea980-105">But the original data can come from sources other than tables.</span></span> <span data-ttu-id="ea980-106">実際、ビュー、クエリ、シノニム、またはテーブルを返すユーザー定義関数のデータを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-106">In fact, it can come from views, queries, synonyms, or user-defined functions that return a table.</span></span>  
  
## <a name="using-a-view-in-place-of-a-table"></a><span data-ttu-id="ea980-107">テーブルに代わるビューの使用</span><span class="sxs-lookup"><span data-stu-id="ea980-107">Using a View in Place of a Table</span></span>  
 <span data-ttu-id="ea980-108">ビューから行を選択できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-108">You can select rows from a view.</span></span> <span data-ttu-id="ea980-109">たとえば、"ExpensiveBooks" という名前のビューを含むデータベースがあり、このビューの各行には価格が $19.99 を超える書籍の書名が格納されているものとします。</span><span class="sxs-lookup"><span data-stu-id="ea980-109">For example, suppose the database includes a view called "ExpensiveBooks," in which each row describes a title whose price exceeds 19.99.</span></span> <span data-ttu-id="ea980-110">ビューの定義は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea980-110">The view definition might look like this:</span></span>  
  
```  
SELECT *  
FROM titles  
WHERE price > 19.99  
  
```  
  
 <span data-ttu-id="ea980-111">ExpensiveBooks ビューから心理学の本を選択するだけで、高価な心理学の本を選択できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-111">You can select the expensive psychology books merely by selecting the psychology books from the ExpensiveBooks view.</span></span> <span data-ttu-id="ea980-112">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea980-112">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *  
FROM ExpensiveBooks  
WHERE type = 'psychology'  
  
```  
  
 <span data-ttu-id="ea980-113">同様に、JOIN 演算でビューを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-113">Similarly, a view can participate in a JOIN operation.</span></span> <span data-ttu-id="ea980-114">たとえば、 テーブルと  ビューを結合するだけで、高価な書籍の販売状況を検索できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-114">For example, you can find the sales of expensive books merely by joining the sales table to the ExpensiveBooks view.</span></span> <span data-ttu-id="ea980-115">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea980-115">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *  
FROM sales   
         INNER JOIN   
         ExpensiveBooks   
         ON sales.title_id   
         =  ExpensiveBooks.title_id  
  
```  
  
 <span data-ttu-id="ea980-116">ビューをクエリに追加する方法については、「[クエリへのテーブルの追加 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea980-116">For more information about adding a view to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="using-a-query-in-place-of-a-table"></a><span data-ttu-id="ea980-117">テーブルに代わるクエリの使用</span><span class="sxs-lookup"><span data-stu-id="ea980-117">Using a Query in Place of a Table</span></span>  
 <span data-ttu-id="ea980-118">クエリから行を選択できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-118">You can select rows from a query.</span></span> <span data-ttu-id="ea980-119">たとえば、共著本、つまり複数の著者によって書かれた本の署名と識別子を取得するクエリが、既に作成されているとします。</span><span class="sxs-lookup"><span data-stu-id="ea980-119">For example, suppose you have already written a query retrieving titles and identifiers of the coauthored books - the books with more than one author.</span></span> <span data-ttu-id="ea980-120">SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea980-120">The SQL might look like this:</span></span>  
  
```  
SELECT   
     titles.title_id, title, type  
FROM   
     titleauthor   
         INNER JOIN  
         titles   
         ON titleauthor.title_id   
         =  titles.title_id   
GROUP BY   
     titles.title_id, title, type  
HAVING COUNT(*) > 1  
  
```  
  
 <span data-ttu-id="ea980-121">この結果を利用する別のクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-121">You can then write another query that builds on this result.</span></span> <span data-ttu-id="ea980-122">たとえば、心理学の共著本を取得するクエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-122">For example, you can write a query that retrieves the coauthored psychology books.</span></span> <span data-ttu-id="ea980-123">新しいクエリのデータの参照元として、既存のクエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-123">To write this new query, you can use the existing query as the source of the new query's data.</span></span> <span data-ttu-id="ea980-124">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea980-124">The resulting SQL might look like this:</span></span>  
  
```  
SELECT   
    title  
FROM   
    (  
    SELECT   
        titles.title_id,   
        title,   
        type  
    FROM   
        titleauthor   
            INNER JOIN  
            titles   
            ON titleauthor.title_id   
            =  titles.title_id   
    GROUP BY   
        titles.title_id,   
        title,   
        type  
    HAVING COUNT(*) > 1  
    )   
    co_authored_books  
WHERE     type = 'psychology'  
  
```  
  
 <span data-ttu-id="ea980-125">太字で表されたテキストは、新しいクエリでデータの参照元として使用される既存のクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="ea980-125">The emphasized text shows the existing query used as the source of the new query's data.</span></span> <span data-ttu-id="ea980-126">新しいクエリでは、既存のクエリに対するエイリアスとして "co_authored_books" を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ea980-126">Note that the new query uses an alias ("co_authored_books") for the existing query.</span></span> <span data-ttu-id="ea980-127">エイリアスの詳細については、「[テーブルの別名の作成 (Visual Database Tools)](create-table-aliases-visual-database-tools.md)」と「[列の別名の作成 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea980-127">For more information about aliases, see [Create Table Aliases &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) and [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="ea980-128">同様に、JOIN 処理でクエリを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ea980-128">Similarly, a query can participate in a JOIN operation.</span></span> <span data-ttu-id="ea980-129">たとえば、ExpensiveBooks ビューと共著本を取得するクエリを結合するだけで、高価な共著本の売り上げ情報を検索できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-129">For example, you can find the sales of expensive coauthored books merely by joining the ExpensiveBooks view to the query retrieving the coauthored books.</span></span> <span data-ttu-id="ea980-130">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea980-130">The resulting SQL might look like this:</span></span>  
  
```  
SELECT   
    ExpensiveBooks.title  
FROM   
    ExpensiveBooks   
        INNER JOIN  
        (  
        SELECT   
            titles.title_id,   
            title,   
            type  
        FROM   
            titleauthor   
                INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
        GROUP BY   
            titles.title_id,   
            title,   
            type  
        HAVING COUNT(*) > 1  
        )  
```  
  
 <span data-ttu-id="ea980-131">クエリをクエリに追加する方法については、「[クエリへのテーブルの追加 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea980-131">For more information about adding a query to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="using-a-user-defined-function-in-place-of-a-table"></a><span data-ttu-id="ea980-132">テーブルに代わるユーザー定義関数の使用</span><span class="sxs-lookup"><span data-stu-id="ea980-132">Using a User-Defined Function in Place of a Table</span></span>  
 <span data-ttu-id="ea980-133">SQL Server 2000 以降では、テーブルを返すユーザー定義関数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-133">In SQL Server 2000 or higher, you can create a user-defined function that returns a table.</span></span> <span data-ttu-id="ea980-134">この種の関数は、複雑な論理または手順論理を実行するときに役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="ea980-134">Such functions are useful for performing complex or procedural logic.</span></span>  
  
 <span data-ttu-id="ea980-135">たとえば、employee テーブルに employee.manager_emp_id という列があり、manager_emp_id から employee.emp_id への外部キーが存在するものとします。</span><span class="sxs-lookup"><span data-stu-id="ea980-135">For example, suppose the employee table contains an additional column, employee.manager_emp_id, and that a foreign key exists from manager_emp_id to employee.emp_id.</span></span> <span data-ttu-id="ea980-136">employee テーブルの各行の manager_emp_id 列は従業員の上司を示します。</span><span class="sxs-lookup"><span data-stu-id="ea980-136">Within each row of the employee table, the manager_emp_id column indicates the employee's boss.</span></span> <span data-ttu-id="ea980-137">正確に言えば、manager_emp_id 列は従業員の上司の emp_id を示しているということになります。</span><span class="sxs-lookup"><span data-stu-id="ea980-137">More precisely, it indicates the employee's boss's emp_id.</span></span> <span data-ttu-id="ea980-138">これを利用すると、特定の上級管理者の組織階層に所属する各従業員に一対一で対応する行を含むテーブルを返す、ユーザー定義関数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-138">You can create a user-defined function that returns a table containing one row for each employee working within a particular high-level manager's organizational hierarchy.</span></span> <span data-ttu-id="ea980-139">この関数に fn_GetWholeTeam という名前を付け、組織の情報を取得する管理者の emp_id を入力変数として取るように関数をデザインします。</span><span class="sxs-lookup"><span data-stu-id="ea980-139">You might call the function fn_GetWholeTeam, and design it to take an input variable - the emp_id of the manager whose team you want to retrieve.</span></span>  
  
 <span data-ttu-id="ea980-140">データの参照元として fn_GetWholeTeam 関数を使用するクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ea980-140">You can write a query that uses the fn_GetWholeTeam function as a source of data.</span></span> <span data-ttu-id="ea980-141">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea980-141">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *   
FROM   
     fn_GetWholeTeam ('VPA30890F')  
  
```  
  
 <span data-ttu-id="ea980-142">"VPA30890F" は、取得の対象となる組織の管理者の emp_id を示しています。</span><span class="sxs-lookup"><span data-stu-id="ea980-142">"VPA30890F" is the emp_id of the manager whose organization you want to retrieve.</span></span> <span data-ttu-id="ea980-143">ユーザー定義関数をクエリに追加する方法については、「[クエリへのテーブルの追加 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea980-143">For more information about adding a user-defined function to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="ea980-144">ユーザー定義関数の詳しい説明については、「 [ユーザー定義関数](../../relational-databases/user-defined-functions/user-defined-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea980-144">For a complete description of user-defined functions, see [User-Defined Functions](../../relational-databases/user-defined-functions/user-defined-functions.md).</span></span>  
  
  
