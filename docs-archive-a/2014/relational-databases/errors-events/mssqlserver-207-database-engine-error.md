---
title: MSSQLSERVER_207 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 207 (Database Engine error)
ms.assetid: d1ab00c7-0331-437a-84fe-bae53b82feec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd6044c08ecd5a73f539bfbc1139d6257c2db9d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714394"
---
# <a name="mssqlserver_207"></a><span data-ttu-id="7a481-102">MSSQLSERVER_207</span><span class="sxs-lookup"><span data-stu-id="7a481-102">MSSQLSERVER_207</span></span>
    
## <a name="details"></a><span data-ttu-id="7a481-103">詳細</span><span class="sxs-lookup"><span data-stu-id="7a481-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7a481-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7a481-104">Product Name</span></span>|<span data-ttu-id="7a481-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7a481-105">SQL Server</span></span>|  
|<span data-ttu-id="7a481-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7a481-106">Event ID</span></span>|<span data-ttu-id="7a481-107">207</span><span class="sxs-lookup"><span data-stu-id="7a481-107">207</span></span>|  
|<span data-ttu-id="7a481-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7a481-108">Event Source</span></span>|<span data-ttu-id="7a481-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7a481-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7a481-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7a481-110">Component</span></span>|<span data-ttu-id="7a481-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7a481-111">SQLEngine</span></span>|  
|<span data-ttu-id="7a481-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="7a481-112">Symbolic Name</span></span>|<span data-ttu-id="7a481-113">SQ_BADCOL</span><span class="sxs-lookup"><span data-stu-id="7a481-113">SQ_BADCOL</span></span>|  
|<span data-ttu-id="7a481-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7a481-114">Message Text</span></span>|<span data-ttu-id="7a481-115">列名 '%.\*ls' が無効です。</span><span class="sxs-lookup"><span data-stu-id="7a481-115">Invalid column name '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7a481-116">説明</span><span class="sxs-lookup"><span data-stu-id="7a481-116">Explanation</span></span>  
 <span data-ttu-id="7a481-117">このクエリ エラーは次のいずれかの問題が原因で生じている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a481-117">This query error can be caused by one of the following problems.</span></span>  
  
-   <span data-ttu-id="7a481-118">列名にスペルミスがあるか、指定されたテーブルにその列が存在しません。</span><span class="sxs-lookup"><span data-stu-id="7a481-118">The column name is misspelled or the column does not exist in any of the specified tables.</span></span>  
  
-   <span data-ttu-id="7a481-119">データベースの照合順序で大文字と小文字が区別され、クエリで指定された列名の大文字と小文字がテーブルで定義された列のものと一致していません。</span><span class="sxs-lookup"><span data-stu-id="7a481-119">The collation of the database is case-sensitive and the case of the column name specified in the query does not match the case of the column defined in the table.</span></span> <span data-ttu-id="7a481-120">たとえば、データベースの照合順序で大文字と小文字が区別され、テーブルで列が **LastName** と定義されている場合、クエリで **Lastname** または **lastname** と指定してその列を参照すると、エラー 207 が返されます。これは列名が一致しないためです。</span><span class="sxs-lookup"><span data-stu-id="7a481-120">For example, when a column is defined in a table as **LastName** and the database uses a case-sensitive collation, queries that refer to the column as **Lastname** or **lastname** will cause error 207 to return because the column name does not match.</span></span>  
  
-   <span data-ttu-id="7a481-121">列の別名 (SELECT 句で定義) が、WHERE、GROUP BY 句などの別の句で参照されています。</span><span class="sxs-lookup"><span data-stu-id="7a481-121">A column alias, defined in the SELECT clause, is referenced in another clause such as a WHERE or GROUP BY clause.</span></span> <span data-ttu-id="7a481-122">たとえば、次のクエリでは SELECT 句で列の別名 `Year` が定義されており、GROUP BY 句で参照されています。</span><span class="sxs-lookup"><span data-stu-id="7a481-122">For example, the following query defines the column alias `Year` in the SELECT clause and refers to it in the GROUP BY clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year, SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY Year;  
    ```  
  
     <span data-ttu-id="7a481-123">クエリの各句が論理的に処理される順序に基づいて、この例ではエラー 207 が返されます。</span><span class="sxs-lookup"><span data-stu-id="7a481-123">Due to the order in which query clauses are logically processed, the example returns error 207.</span></span> <span data-ttu-id="7a481-124">この処理の順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7a481-124">The processing order is as follows:</span></span>  
  
    1.  <span data-ttu-id="7a481-125">FROM</span><span class="sxs-lookup"><span data-stu-id="7a481-125">FROM</span></span>  
  
    2.  <span data-ttu-id="7a481-126">ON</span><span class="sxs-lookup"><span data-stu-id="7a481-126">ON</span></span>  
  
    3.  <span data-ttu-id="7a481-127">JOIN</span><span class="sxs-lookup"><span data-stu-id="7a481-127">JOIN</span></span>  
  
    4.  <span data-ttu-id="7a481-128">WHERE</span><span class="sxs-lookup"><span data-stu-id="7a481-128">WHERE</span></span>  
  
    5.  <span data-ttu-id="7a481-129">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="7a481-129">GROUP BY</span></span>  
  
    6.  <span data-ttu-id="7a481-130">WITH CUBE または WITH ROLLUP</span><span class="sxs-lookup"><span data-stu-id="7a481-130">WITH CUBE or WITH ROLLUP</span></span>  
  
    7.  <span data-ttu-id="7a481-131">HAVING</span><span class="sxs-lookup"><span data-stu-id="7a481-131">HAVING</span></span>  
  
    8.  <span data-ttu-id="7a481-132">SELECT</span><span class="sxs-lookup"><span data-stu-id="7a481-132">SELECT</span></span>  
  
    9. <span data-ttu-id="7a481-133">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="7a481-133">DISTINCT</span></span>  
  
    10. <span data-ttu-id="7a481-134">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="7a481-134">ORDER BY</span></span>  
  
    11. <span data-ttu-id="7a481-135">TOP</span><span class="sxs-lookup"><span data-stu-id="7a481-135">TOP</span></span>  
  
     <span data-ttu-id="7a481-136">列の別名は SELECT 句が処理されるまでは定義されないため、GROUP BY 句が処理される時点では別名が不明になってしまいます。</span><span class="sxs-lookup"><span data-stu-id="7a481-136">Because a column alias is not defined until the SELECT clause is processed, the alias name is unknown when the GROUP BY clause is processed.</span></span>  
  
-   <span data-ttu-id="7a481-137">*<merge_matched>* 句がソース テーブルの列を参照していて、WHEN NOT MATCHED BY SOURCE 句でソース テーブルから行が返されない場合、MERGE ステートメントでこのエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7a481-137">The MERGE statement raises this error when the *<merge_matched>* clause references columns in the source table but no rows are returned by the source table in the WHEN NOT MATCHED BY SOURCE clause.</span></span> <span data-ttu-id="7a481-138">このエラーは、クエリに行が返されないと、ソース テーブルの列にアクセスできないために発生します。</span><span class="sxs-lookup"><span data-stu-id="7a481-138">The error occurs because the columns in the source table cannot be accessed when no rows are returned to the query.</span></span> <span data-ttu-id="7a481-139">たとえば、ソース テーブルの `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` にアクセスできないと、`Col1` 句によってステートメントが失敗することになります。</span><span class="sxs-lookup"><span data-stu-id="7a481-139">For example, the clause `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` may cause the statement to fail if `Col1` in the source table is inaccessible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7a481-140">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7a481-140">User Action</span></span>  
 <span data-ttu-id="7a481-141">次の情報を確認し、必要に応じてステートメントを修正します。</span><span class="sxs-lookup"><span data-stu-id="7a481-141">Verify the following information and correct the statement as appropriate.</span></span>  
  
-   <span data-ttu-id="7a481-142">列名がテーブルに存在し、スペルも正しい。</span><span class="sxs-lookup"><span data-stu-id="7a481-142">The column name exists in the table and is spelled correctly.</span></span> <span data-ttu-id="7a481-143">次の例では **sys.columns** カタログ ビューに対するクエリが実行され、指定されたテーブルのすべての列名が返されます。</span><span class="sxs-lookup"><span data-stu-id="7a481-143">The following example queries the **sys.columns** catalog view to return all column names for a given table.</span></span>  
  
    ```  
    SELECT name FROM sys.columns WHERE object_id = OBJECT_ID('schema_name.table_name');  
    ```  
  
-   <span data-ttu-id="7a481-144">データベースの照合順序で大文字と小文字が区別されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="7a481-144">The case sensitivity of the database collation.</span></span> <span data-ttu-id="7a481-145">次のステートメントでは、指定されたデータベースの照合順序が返されます。</span><span class="sxs-lookup"><span data-stu-id="7a481-145">The following statement returns the collation of the specified database.</span></span>  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     <span data-ttu-id="7a481-146">照合順序名に含まれる省略形 CS は、照合順序で大文字と小文字が区別されることを示します。</span><span class="sxs-lookup"><span data-stu-id="7a481-146">The abbreviation CS in the collation name indicates the collation is case-sensitive.</span></span> <span data-ttu-id="7a481-147">たとえば、Latin1_General_CS_AS は、大文字と小文字およびアクセントが区別される照合順序です。</span><span class="sxs-lookup"><span data-stu-id="7a481-147">For example, Latin1_General_CS_AS is a case-sensitive and accent-sensitive collation.</span></span> <span data-ttu-id="7a481-148">テーブルで定義されている列名の大文字と小文字に一致するように、列名を変更してください。</span><span class="sxs-lookup"><span data-stu-id="7a481-148">Modify the column name to match the case of the column name as it is defined in the table.</span></span>  
  
-   <span data-ttu-id="7a481-149">列の別名が不適切に参照されている。</span><span class="sxs-lookup"><span data-stu-id="7a481-149">A column alias is referenced incorrectly.</span></span> <span data-ttu-id="7a481-150">適切な句の中で、別名を定義する式を再度記述するか、派生テーブルを使って、ステートメントを変更してください。</span><span class="sxs-lookup"><span data-stu-id="7a481-150">Modify the statement by repeating the expression that defines the alias in the appropriate clause or by using a derived table.</span></span> <span data-ttu-id="7a481-151">次の例では、GROUP BY 句の中で、別名 `Year` を定義する式を再度記述しています。</span><span class="sxs-lookup"><span data-stu-id="7a481-151">The following example repeats the expressions that define the `Year` alias in the GROUP BY clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year ,SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY DATEPART(yyyy,OrderDate);  
    ```  
  
     <span data-ttu-id="7a481-152">次の例では、派生テーブルを使って、別名をクエリ内の他の句でも使用できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="7a481-152">The following example uses a derived table to make the alias name available to other clauses in the query.</span></span> <span data-ttu-id="7a481-153">別名 `Year` は FROM 句内で定義されており、これが最初に処理されるため、この別名はクエリ内の他の句でも使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7a481-153">Notice that the alias `Year` is defined in the FROM clause, which is processed first, and so makes the alias available for use in other clauses in the query.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT d.Year, SUM(TotalDue) AS Total  
    FROM (SELECT DATEPART(yyyy,OrderDate) AS Year, TotalDue  
          FROM Sales.SalesOrderHeader)AS d  
    GROUP BY Year;  
    ```  
  
-   <span data-ttu-id="7a481-154">MERGE ステートメントの WHEN NOT MATCHED BY SOURCE 句が、アクセスできる値を参照している。</span><span class="sxs-lookup"><span data-stu-id="7a481-154">The WHEN NOT MATCHED BY SOURCE clause in the MERGE statement refers to a value that can be accessed.</span></span> <span data-ttu-id="7a481-155">WHEN NOT MATCHED BY SOURCE 句でソース テーブルから少なくとも 1 行が返されるように MERGE ステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="7a481-155">Modify the MERGE statement so that at least one row is returned by the source table in the WHEN NOT MATCHED BY SOURCE clause.</span></span> <span data-ttu-id="7a481-156">たとえば、この句に指定した検索条件を追加または変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a481-156">For example, you might need to add or revise the search condition specified for the clause.</span></span> <span data-ttu-id="7a481-157">または、句を変更して、ソース テーブルを参照しない値を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a481-157">Alternatively, you can modify the clause to specify a value that does not reference the source table.</span></span> <span data-ttu-id="7a481-158">たとえば、「 `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="7a481-158">For example, `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a481-159">参照</span><span class="sxs-lookup"><span data-stu-id="7a481-159">See Also</span></span>  
 <span data-ttu-id="7a481-160">[MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a481-160">[MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql) </span></span>  
 <span data-ttu-id="7a481-161">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a481-161">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span></span>  
 <span data-ttu-id="7a481-162">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a481-162">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="7a481-163">UPDATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7a481-163">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
