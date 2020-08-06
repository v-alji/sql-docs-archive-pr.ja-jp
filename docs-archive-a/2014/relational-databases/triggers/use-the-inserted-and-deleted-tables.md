---
title: inserted テーブルと deleted テーブルの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserted tables
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- INSTEAD OF triggers
- deleted tables
- INSERT statement [SQL Server], DML triggers
- DML triggers, deleted or inserted tables
ms.assetid: ed84567f-7b91-4b44-b5b2-c400bda4590d
author: rothja
ms.author: jroth
ms.openlocfilehash: facc534177113bd93e56e50fca3ae14c3e6b2cfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644875"
---
# <a name="use-the-inserted-and-deleted-tables"></a><span data-ttu-id="25f7d-102">inserted テーブルと deleted テーブルの使用</span><span class="sxs-lookup"><span data-stu-id="25f7d-102">Use the inserted and deleted Tables</span></span>
  <span data-ttu-id="25f7d-103">DML トリガー ステートメントでは、deleted テーブルおよび inserted テーブルという 2 つの特殊なテーブルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-103">DML trigger statements use two special tables: the deleted table and the inserted tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="25f7d-104">では、これらのテーブルを自動的に作成および管理します。</span><span class="sxs-lookup"><span data-stu-id="25f7d-104">automatically creates and manages these tables.</span></span> <span data-ttu-id="25f7d-105">これらの一時的なメモリ常駐型のテーブルを使用して、特定のデータ変更の影響をテストしたり、DML トリガー操作に条件を設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-105">You can use these temporary, memory-resident tables to test the effects of certain data modifications and to set conditions for DML trigger actions.</span></span> <span data-ttu-id="25f7d-106">これらのテーブル内のデータを直接変更したり、これらのテーブルに対して CREATE INDEX などのデータ定義言語 (DDL) 操作を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="25f7d-106">You cannot directly modify the data in the tables or perform data definition language (DDL) operations on the tables, such as CREATE INDEX.</span></span>  
  
 <span data-ttu-id="25f7d-107">DML トリガーでは、inserted テーブルと deleted テーブルは主に次のことを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-107">In DML triggers, the inserted and deleted tables are primarily used to perform the following:</span></span>  
  
-   <span data-ttu-id="25f7d-108">テーブル間の参照整合性の拡張。</span><span class="sxs-lookup"><span data-stu-id="25f7d-108">Extend referential integrity between tables.</span></span>  
  
-   <span data-ttu-id="25f7d-109">ビューを構成するベース テーブルでのデータの挿入または更新。</span><span class="sxs-lookup"><span data-stu-id="25f7d-109">Insert or update data in base tables underlying a view.</span></span>  
  
-   <span data-ttu-id="25f7d-110">エラーのテストとエラー内容に基づく動作の実行。</span><span class="sxs-lookup"><span data-stu-id="25f7d-110">Test for errors and take action based on the error.</span></span>  
  
-   <span data-ttu-id="25f7d-111">データ変更前と変更後のテーブルの状態の違いを検出し、その違いに基づいた動作の実行。</span><span class="sxs-lookup"><span data-stu-id="25f7d-111">Find the difference between the state of a table before and after a data modification and take actions based on that difference.</span></span>  
  
 <span data-ttu-id="25f7d-112">deleted テーブルには、DELETE ステートメントと UPDATE ステートメントの実行で影響を受けた行のコピーが格納されます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-112">The deleted table stores copies of the affected rows during DELETE and UPDATE statements.</span></span> <span data-ttu-id="25f7d-113">DELETE ステートメントまたは UPDATE ステートメントの実行中、行はトリガー テーブルから削除され、deleted テーブルに転送されます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-113">During the execution of a DELETE or UPDATE statement, rows are deleted from the trigger table and transferred to the deleted table.</span></span> <span data-ttu-id="25f7d-114">通常、deleted テーブルとトリガー テーブルには共通する行はありません。</span><span class="sxs-lookup"><span data-stu-id="25f7d-114">The deleted table and the trigger table ordinarily have no rows in common.</span></span>  
  
 <span data-ttu-id="25f7d-115">inserted テーブルには、INSERT ステートメントおよび UPDATE ステートメントの実行で影響を受けた行のコピーが格納されます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-115">The inserted table stores copies of the affected rows during INSERT and UPDATE statements.</span></span> <span data-ttu-id="25f7d-116">挿入トランザクションまたは更新トランザクションの実行時には、新しい行が inserted テーブルとトリガー テーブルの両方に追加されます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-116">During an insert or update transaction, new rows are added to both the inserted table and the trigger table.</span></span> <span data-ttu-id="25f7d-117">inserted テーブルの行はトリガー テーブルの新しい行のコピーです。</span><span class="sxs-lookup"><span data-stu-id="25f7d-117">The rows in the inserted table are copies of the new rows in the trigger table.</span></span>  
  
 <span data-ttu-id="25f7d-118">更新トランザクションは、削除処理とそれに続く挿入処理の組み合わせと考えることができます。まず、deleted テーブルに古い行がコピーされ、その後、新しい行がトリガー テーブルと inserted テーブルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-118">An update transaction is similar to a delete operation followed by an insert operation; the old rows are copied to the deleted table first, and then the new rows are copied to the trigger table and to the inserted table.</span></span>  
  
 <span data-ttu-id="25f7d-119">トリガーの条件を設定するときには、トリガーを起動した操作に合わせて inserted テーブルと deleted テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="25f7d-119">When you set trigger conditions, use the inserted and deleted tables appropriately for the action that fired the trigger.</span></span> <span data-ttu-id="25f7d-120">INSERT ステートメントをテストするときに deleted テーブルを参照したり、DELETE ステートメントをテストするときに inserted テーブルを参照してもエラーは発生しませんが、このような場合は、これらのトリガー テスト用テーブルには行が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="25f7d-120">Although referencing the deleted table when testing an INSERT or the inserted table when testing a DELETE does not cause any errors, these trigger test tables do not contain any rows in these cases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25f7d-121">トリガーの動作が、データ変更の影響のある行の数に依存する場合、複数行データ変更 (SELECT ステートメントに基づく INSERT、DELETE、または UPDATE) に @@ROWCOUNT の検査などのテストを使用し、適切な動作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-121">If trigger actions depend on the number of rows a data modification effects, use tests (such as an examination of @@ROWCOUNT) for multirow data modifications (an INSERT, DELETE, or UPDATE based on a SELECT statement), and take appropriate actions.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="25f7d-122">では、AFTER トリガー用の inserted テーブルおよび deleted テーブル内で `text` 列、`ntext` 列、または `image` 列を参照することを禁止しています。</span><span class="sxs-lookup"><span data-stu-id="25f7d-122">does not allow for `text`, `ntext`, or `image` column references in the inserted and deleted tables for AFTER triggers.</span></span> <span data-ttu-id="25f7d-123">これらのデータ型は旧バージョンとの互換性のためだけに用意されているものです。</span><span class="sxs-lookup"><span data-stu-id="25f7d-123">However, these data types are included for backward compatibility purposes only.</span></span> <span data-ttu-id="25f7d-124">大量のデータのストレージには、`varchar(max)` データ型、`nvarchar(max)` データ型、および `varbinary(max)` データ型を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="25f7d-124">The preferred storage for large data is to use the `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types.</span></span> <span data-ttu-id="25f7d-125">AFTER トリガーと INSTEAD OF トリガーでは両方とも、inserted および deleted テーブルの `varchar(max)`、`nvarchar(max)`、および `varbinary(max)` 型のデータがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-125">Both AFTER and INSTEAD OF triggers support `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data in the inserted and deleted tables.</span></span> <span data-ttu-id="25f7d-126">詳細については、「[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25f7d-126">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
 <span data-ttu-id="25f7d-127">**トリガーで inserted テーブルを使用してビジネス ルールを適用する例**</span><span class="sxs-lookup"><span data-stu-id="25f7d-127">**An Example of Using the inserted Table in a Trigger to Enforce Business Rules**</span></span>  
  
 <span data-ttu-id="25f7d-128">CHECK 制約で参照できるのは、列レベルまたはテーブル レベルの制約が定義されている列のみであるため、テーブル間にまたがる制約 (ここでは、ビジネス ルール) はすべてトリガーとして定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-128">Because CHECK constraints can reference only the columns on which the column-level or table-level constraint is defined, any cross-table constraints (in this case, business rules) must be defined as triggers.</span></span>  
  
 <span data-ttu-id="25f7d-129">次の例では、DML トリガーを作成します。</span><span class="sxs-lookup"><span data-stu-id="25f7d-129">The following example creates a DML trigger.</span></span> <span data-ttu-id="25f7d-130">このトリガーでは、 `PurchaseOrderHeader` テーブルに新しい発注を挿入しようとしたときに、ベンダーの信用格付けが良好であるかどうかがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-130">This trigger checks to make sure the credit rating for the vendor is good when an attempt is made to insert a new purchase order into the `PurchaseOrderHeader` table.</span></span> <span data-ttu-id="25f7d-131">挿入した発注に対応するベンダーの信用格付けを取得するには、 `Vendor` テーブルを参照し、inserted テーブルと結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-131">To obtain the credit rating of the vendor corresponding to the purchase order that was just inserted, the `Vendor` table must be referenced and joined with the inserted table.</span></span> <span data-ttu-id="25f7d-132">信用格付けが低い場合は、メッセージが表示され、挿入は実行されません。</span><span class="sxs-lookup"><span data-stu-id="25f7d-132">If the credit rating is too low, a message is displayed and the insertion does not execute.</span></span> <span data-ttu-id="25f7d-133">この例では、複数行のデータの変更を許可していません。</span><span class="sxs-lookup"><span data-stu-id="25f7d-133">Note that this example does not allow for multirow data modifications.</span></span> <span data-ttu-id="25f7d-134">詳細については、「 [複数行のデータを処理するための DML トリガーの作成](../triggers/create-dml-triggers-to-handle-multiple-rows-of-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25f7d-134">For more information, see [Create DML Triggers to Handle Multiple Rows of Data](../triggers/create-dml-triggers-to-handle-multiple-rows-of-data.md).</span></span>  
  
 [!code-sql[TriggerDDL#CreateTrigger3](../../snippets/tsql/SQL14/tsql/triggerddl/transact-sql/snippet_create_alter_drop_trigger.sql#createtrigger3)]  
  
## <a name="using-the-inserted-and-deleted-tables-in-instead-of-triggers"></a><span data-ttu-id="25f7d-135">INSTEAD OF トリガー内での inserted テーブルと deleted テーブルの使用</span><span class="sxs-lookup"><span data-stu-id="25f7d-135">Using the inserted and deleted Tables in INSTEAD OF Triggers</span></span>  
 <span data-ttu-id="25f7d-136">テーブルに定義された INSTEAD OF トリガーへ渡される inserted テーブルおよび deleted テーブルは、AFTER トリガーに渡される inserted テーブルおよび deleted テーブルと同じルールに従います。</span><span class="sxs-lookup"><span data-stu-id="25f7d-136">The inserted and deleted tables passed to INSTEAD OF triggers defined on tables follow the same rules as the inserted and deleted tables passed to AFTER triggers.</span></span> <span data-ttu-id="25f7d-137">inserted テーブルと deleted テーブルのフォーマットは、INSTEAD OF トリガーを定義したテーブルのフォーマットと同じです。</span><span class="sxs-lookup"><span data-stu-id="25f7d-137">The format of the inserted and deleted tables is the same as the format of the table on which the INSTEAD OF trigger is defined.</span></span> <span data-ttu-id="25f7d-138">inserted テーブルおよび deleted テーブルの各列は、ベース テーブルの列に直接マップされます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-138">Each column in the inserted and deleted tables maps directly to a column in the base table.</span></span>  
  
 <span data-ttu-id="25f7d-139">INSTEAD OF トリガーを含むテーブルを参照する INSERT ステートメントまたは UPDATE ステートメントで、列に値を指定するときに適用されるルールは、次に示すように、INSTEAD OF トリガーのないテーブルに適用されるルールと同じです。</span><span class="sxs-lookup"><span data-stu-id="25f7d-139">The following rules regarding when an INSERT or UPDATE statement referencing a table with an INSTEAD OF trigger must supply values for columns are the same as if the table did not have an INSTEAD OF trigger:</span></span>  
  
-   <span data-ttu-id="25f7d-140">計算列または `timestamp` データ型の列の場合、値は指定できません。</span><span class="sxs-lookup"><span data-stu-id="25f7d-140">Values cannot be specified for computed columns or columns with a `timestamp` data type.</span></span>  
  
-   <span data-ttu-id="25f7d-141">IDENTITY プロパティを持つ列の場合、そのテーブルに対して IDENTITY_INSERT が ON になっていない限り、値は指定できません。</span><span class="sxs-lookup"><span data-stu-id="25f7d-141">Values cannot be specified for columns with an IDENTITY property, unless IDENTITY_INSERT is ON for that table.</span></span> <span data-ttu-id="25f7d-142">IDENTITY_INSERT が ON になっている場合は、INSERT ステートメントで値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-142">When IDENTITY_INSERT is ON, INSERT statements must supply a value.</span></span>  
  
-   <span data-ttu-id="25f7d-143">INSERT ステートメントでは、DEFAULT 制約のないすべての NOT NULL 列に対して値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-143">INSERT statements must supply values for all NOT NULL columns that do not have DEFAULT constraints.</span></span>  
  
-   <span data-ttu-id="25f7d-144">計算列、ID 列、または `timestamp` 型の列以外で、NULL 値を許容する列、または DEFAULT 定義を持つ NOT NULL 列については、値の指定を省略できます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-144">For any columns except computed, identity, or `timestamp` columns, values are optional for any column that allows nulls, or any NOT NULL column that has a DEFAULT definition.</span></span>  
  
 <span data-ttu-id="25f7d-145">INSERT、UPDATE、または DELETE の各ステートメントが INSTEAD OF トリガーを含むビューを参照する場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、どのテーブルに対しても直接に動作を実行するのではなく、そのトリガーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25f7d-145">When an INSERT, UPDATE, or DELETE statement references a view that has an INSTEAD OF trigger, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] calls the trigger instead of taking any direct action against any table.</span></span> <span data-ttu-id="25f7d-146">呼び出されたトリガーは、inserted テーブルおよび deleted テーブルの情報を使用して、ベース テーブルで要求された動作を実装するために必要なステートメントを作成する必要があります。その際、ビューに作成された inserted テーブルおよび deleted テーブルの情報の形式がベース テーブルのデータ形式と異なっていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="25f7d-146">The trigger must use the information presented in the inserted and deleted tables to build any statements required to implement the requested action in the base tables, even when the format of the information in the inserted and deleted tables built for the view is different from the format of the data in the base tables.</span></span>  
  
 <span data-ttu-id="25f7d-147">ビューに定義された INSTEAD OF トリガーに渡される inserted テーブルおよび deleted テーブルの形式は、ビューに定義された SELECT ステートメントの選択リストに一致します。</span><span class="sxs-lookup"><span data-stu-id="25f7d-147">The format of the inserted and deleted tables passed to an INSTEAD OF trigger defined on a view matches the select list of the SELECT statement defined for the view.</span></span> <span data-ttu-id="25f7d-148">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="25f7d-148">For example:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.EmployeeNames (BusinessEntityID, LName, FName)  
AS  
SELECT e.BusinessEntityID, p.LastName, p.FirstName  
FROM HumanResources.Employee AS e   
JOIN Person.Person AS p  
ON e.BusinessEntityID = p.BusinessEntityID;  
```  
  
 <span data-ttu-id="25f7d-149">このビューの結果セットには 3 列があり、1 つは `int` 列で、後の 2 つは `nvarchar` 列です。</span><span class="sxs-lookup"><span data-stu-id="25f7d-149">The result set for this view has three columns: an `int` column and two `nvarchar` columns.</span></span> <span data-ttu-id="25f7d-150">ビューで定義された INSTEAD OF トリガーに渡される inserted テーブルと deleted テーブルには、`BusinessEntityID` という名前の `int` 列、`LName` という名前の `nvarchar` 列、および `FName` という名前の `nvarchar` 列があります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-150">The inserted and deleted tables passed to an INSTEAD OF trigger defined on the view also have an `int` column named `BusinessEntityID`, an `nvarchar` column named `LName`, and an `nvarchar` column named `FName`.</span></span>  
  
 <span data-ttu-id="25f7d-151">ビューの選択リストには、単一のベース テーブルの列に直接マップされない式を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-151">The select list of a view can also contain expressions that do not directly map to a single base-table column.</span></span> <span data-ttu-id="25f7d-152">ビューの式の中には、定数や関数の呼び出しなど、列を参照しない可能性があり、無視できるものがあります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-152">Some view expressions, such as a constant or function invocation, may not reference any columns and can be ignored.</span></span> <span data-ttu-id="25f7d-153">複合式を使用して複数の列を参照できます。ただし、inserted テーブルおよび deleted テーブルでは、挿入された行ごとに 1 つの値のみを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="25f7d-153">Complex expressions can reference multiple columns, yet the inserted and deleted tables have only one value for each inserted row.</span></span> <span data-ttu-id="25f7d-154">このことは、複合式を持つ計算列を参照するビューの単純式にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-154">The same issues apply to simple expressions in a view if they reference a computed column that has a complex expression.</span></span> <span data-ttu-id="25f7d-155">このような種類の式は、ビューの INSTEAD OF トリガーが処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25f7d-155">An INSTEAD OF trigger on the view must handle these types of expressions.</span></span>  
  
  
