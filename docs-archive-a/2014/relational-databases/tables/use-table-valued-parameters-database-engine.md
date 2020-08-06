---
title: テーブル値パラメーターの使用 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- DECLARE
- CREATE TYPE
helpviewer_keywords:
- table-valued parameters
- table-valued parameters, about table-valued parameters
- parameters [SQL Server], table-valued
- TVP See table-valued parameters
ms.assetid: 5e95a382-1e01-4c74-81f5-055612c2ad99
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa7013fddc6b2ce12ad9ad0f9fcb511d93915e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640824"
---
# <a name="use-table-valued-parameters-database-engine"></a><span data-ttu-id="f0040-102">テーブル値パラメーターの使用 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="f0040-102">Use Table-Valued Parameters (Database Engine)</span></span>
  <span data-ttu-id="f0040-103">テーブル値パラメーターは、ユーザー定義テーブル型を使用して宣言されます。</span><span class="sxs-lookup"><span data-stu-id="f0040-103">Table-valued parameters are declared by using user-defined table types.</span></span> <span data-ttu-id="f0040-104">テーブル値パラメーターを使用すると、一時テーブルまたは多数のパラメーターを作成せずに、ストアド プロシージャや関数などの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはルーチンに複数行のデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="f0040-104">You can use table-valued parameters to send multiple rows of data to a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a routine, such as a stored procedure or function, without creating a temporary table or many parameters.</span></span>  
  
 <span data-ttu-id="f0040-105">テーブル値パラメーターは OLE DB や ODBC のパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。</span><span class="sxs-lookup"><span data-stu-id="f0040-105">Table-valued parameters are like parameter arrays in OLE DB and ODBC, but offer more flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f0040-106">テーブル値パラメーターには、セットベースの操作に使用できるという利点もあります。</span><span class="sxs-lookup"><span data-stu-id="f0040-106">Table-valued parameters also have the benefit of being able to participate in set-based operations.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="f0040-107">では、入力データのコピーが作成されないようにするために、テーブル値パラメーターがルーチンに参照渡しされます。</span><span class="sxs-lookup"><span data-stu-id="f0040-107">passes table-valued parameters to routines by reference to avoid making a copy of the input data.</span></span> <span data-ttu-id="f0040-108">テーブル値パラメーターを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] ルーチンを作成して実行し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] コード、および任意のマネージド言語のマネージド クライアントとネイティブ クライアントから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f0040-108">You can create and execute [!INCLUDE[tsql](../../includes/tsql-md.md)] routines with table-valued parameters, and call them from [!INCLUDE[tsql](../../includes/tsql-md.md)] code, managed and native clients in any managed language.</span></span>  
  
 <span data-ttu-id="f0040-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f0040-109">**In This Topic:**</span></span>  
  
 [<span data-ttu-id="f0040-110">メリット</span><span class="sxs-lookup"><span data-stu-id="f0040-110">Benefits</span></span>](#Benefits)  
  
 [<span data-ttu-id="f0040-111">制限事項</span><span class="sxs-lookup"><span data-stu-id="f0040-111">Restrictions</span></span>](#Restrictions)  
  
 [<span data-ttu-id="f0040-112">テーブル値パラメーターと BULK INSERT 操作</span><span class="sxs-lookup"><span data-stu-id="f0040-112">Table-Valued Parameters vs. BULK INSERT Operations</span></span>](#BulkInsert)  
  
 [<span data-ttu-id="f0040-113">例</span><span class="sxs-lookup"><span data-stu-id="f0040-113">Example</span></span>](#Example)  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="f0040-114">利点</span><span class="sxs-lookup"><span data-stu-id="f0040-114">Benefits</span></span>  
 <span data-ttu-id="f0040-115">テーブル値パラメーターの対象範囲はストアド プロシージャ、関数、または動的な [!INCLUDE[tsql](../../includes/tsql-md.md)] テキストで、他のパラメーターと同じです。</span><span class="sxs-lookup"><span data-stu-id="f0040-115">A table-valued parameter is scoped to the stored procedure, function, or dynamic [!INCLUDE[tsql](../../includes/tsql-md.md)] text, exactly like other parameters.</span></span> <span data-ttu-id="f0040-116">同様に、テーブル型の変数の対象範囲も、DECLARE ステートメントを使用して作成される他のローカル変数と同じです。</span><span class="sxs-lookup"><span data-stu-id="f0040-116">Similarly, a variable of table type has scope like any other local variable that is created by using a DECLARE statement.</span></span> <span data-ttu-id="f0040-117">テーブル値変数は、動的な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内で宣言でき、テーブル値パラメーターとしてストアド プロシージャおよび関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f0040-117">You can declare table-valued variables within dynamic [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and pass these variables as table-valued parameters to stored procedures and functions.</span></span>  
  
 <span data-ttu-id="f0040-118">テーブル値パラメーターは柔軟性が高く、一時テーブルやその他の方法でパラメーターの一覧を渡す場合よりもパフォーマンスが向上することもあります。</span><span class="sxs-lookup"><span data-stu-id="f0040-118">Table-valued parameters offer more flexibility and in some cases better performance than temporary tables or other ways to pass a list of parameters.</span></span> <span data-ttu-id="f0040-119">テーブル値パラメーターには、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="f0040-119">Table-valued parameters offer the following benefits:</span></span>  
  
-   <span data-ttu-id="f0040-120">クライアントからのデータを最初に設定する際にロックを取得しません。</span><span class="sxs-lookup"><span data-stu-id="f0040-120">Do not acquire locks for the initial population of data from a client.</span></span>  
  
-   <span data-ttu-id="f0040-121">単純なプログラミング モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="f0040-121">Provide a simple programming model.</span></span>  
  
-   <span data-ttu-id="f0040-122">複雑なビジネス ロジックを 1 つのルーチンに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f0040-122">Enable you to include complex business logic in a single routine.</span></span>  
  
-   <span data-ttu-id="f0040-123">サーバーへのラウンド トリップが減少します。</span><span class="sxs-lookup"><span data-stu-id="f0040-123">Reduce round trips to the server.</span></span>  
  
-   <span data-ttu-id="f0040-124">カーディナリティが異なるテーブル構造を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f0040-124">Can have a table structure of different cardinality.</span></span>  
  
-   <span data-ttu-id="f0040-125">厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="f0040-125">Are strongly typed.</span></span>  
  
-   <span data-ttu-id="f0040-126">クライアントで並べ替え順序と一意キーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f0040-126">Enable the client to specify sort order and unique keys.</span></span>  
  
-   <span data-ttu-id="f0040-127">ストアド プロシージャで使用すると、一時テーブルのようにキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="f0040-127">Are cached like a temp table when used in a stored procedure.</span></span> <span data-ttu-id="f0040-128">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降では、テーブル値パラメーターはパラメーター化クエリ用にもキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="f0040-128">Starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], table-valued parameters are also cached for parameterized queries.</span></span>  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f0040-129">制限</span><span class="sxs-lookup"><span data-stu-id="f0040-129">Restrictions</span></span>  
 <span data-ttu-id="f0040-130">テーブル値パラメーターには、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="f0040-130">Table-valued parameters have the following restrictions:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f0040-131">でテーブル値パラメーターの列の統計が保持されません。</span><span class="sxs-lookup"><span data-stu-id="f0040-131">does not maintain statistics on columns of table-valued parameters.</span></span>  
  
-   <span data-ttu-id="f0040-132">テーブル値パラメーターは、READONLY 入力パラメーターとして [!INCLUDE[tsql](../../includes/tsql-md.md)] ルーチンに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0040-132">Table-valued parameters must be passed as input READONLY parameters to [!INCLUDE[tsql](../../includes/tsql-md.md)] routines.</span></span> <span data-ttu-id="f0040-133">ルーチン本体でテーブル値パラメーターに対して UPDATE、DELETE、INSERT などの DML 操作を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="f0040-133">You cannot perform DML operations such as UPDATE, DELETE, or INSERT on a table-valued parameter in the body of a routine.</span></span>  
  
-   <span data-ttu-id="f0040-134">SELECT INTO または INSERT EXEC ステートメントの対象としてテーブル値パラメーターを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f0040-134">You cannot use a table-valued parameter as target of a SELECT INTO or INSERT EXEC statement.</span></span> <span data-ttu-id="f0040-135">テーブル値パラメーターは、SELECT INTO の FROM 句か、INSERT EXEC 文字列またはストアド プロシージャに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f0040-135">A table-valued parameter can be in the FROM clause of SELECT INTO or in the INSERT EXEC string or stored procedure.</span></span>  
  
##  <a name="table-valued-parameters-vs-bulk-insert-operations"></a><a name="BulkInsert"></a><span data-ttu-id="f0040-136">テーブル値パラメーターと BULK INSERT 操作</span><span class="sxs-lookup"><span data-stu-id="f0040-136">Table-Valued Parameters vs. BULK INSERT Operations</span></span>  
 <span data-ttu-id="f0040-137">テーブル値パラメーターの使用はセットベースの変数を使用するその他の方法に似ていますが、多くの場合、大規模なデータセットを処理するときは、テーブル値パラメーターを使用する方が短時間で済みます。</span><span class="sxs-lookup"><span data-stu-id="f0040-137">Using table-valued parameters is comparable to other ways of using set-based variables; however, using table-valued parameters frequently can be faster for large data sets.</span></span> <span data-ttu-id="f0040-138">テーブル値パラメーターよりもスタートアップ コストがかかる一括操作と比較すると、1,000 行未満の行を挿入する場合は、テーブル値パラメーターの方がパフォーマンスが高くなります。</span><span class="sxs-lookup"><span data-stu-id="f0040-138">Compared to bulk operations that have a greater startup cost than table-valued parameters, table-valued parameters perform well for inserting less than 1000 rows.</span></span>  
  
 <span data-ttu-id="f0040-139">再利用されるテーブル値パラメーターの場合、一時テーブル キャッシュを使用するとメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="f0040-139">Table-valued parameters that are reused benefit from temporary table caching.</span></span> <span data-ttu-id="f0040-140">このテーブル キャッシュを使用すると、同等の BULK INSERT 操作よりもスケーラビリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="f0040-140">This table caching enables better scalability than equivalent BULK INSERT operations.</span></span> <span data-ttu-id="f0040-141">少数の行の挿入操作では、BULK INSERT 操作またはテーブル値パラメーターではなく、パラメーター一覧またはバッチにまとめられたステートメントを使用すると、パフォーマンス上の利点が多少得られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0040-141">By using small row-insert operations a small performance benefit might be gained by using parameter lists or batched statements instead of BULK INSERT operations or table-valued parameters.</span></span> <span data-ttu-id="f0040-142">ただし、これらの方法はプログラミングが容易ではなく、行が増えるとすぐにパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="f0040-142">However, these methods are less convenient to program, and performance decreases quickly as rows increase.</span></span>  
  
 <span data-ttu-id="f0040-143">テーブル値パラメーターは、同等のパラメーター配列の実装と同様またはそれ以上のパフォーマンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="f0040-143">Table-valued parameters perform equally well or better than an equivalent parameter array implementation.</span></span>  
  
##  <a name="example"></a><a name="Example"></a> <span data-ttu-id="f0040-144">例</span><span class="sxs-lookup"><span data-stu-id="f0040-144">Example</span></span>  
 <span data-ttu-id="f0040-145">次の例では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、テーブル値パラメーターの型を作成してその型を参照する変数を宣言し、パラメーター一覧を入力して値をストアド プロシージャに渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f0040-145">The following example uses [!INCLUDE[tsql](../../includes/tsql-md.md)] and shows you how to create a table-valued parameter type, declare a variable to reference it, fill the parameter list, and then pass the values to a stored procedure.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
/* Create a table type. */  
CREATE TYPE LocationTableType AS TABLE   
( LocationName VARCHAR(50)  
, CostRate INT );  
GO  
  
/* Create a procedure to receive data for the table-valued parameter. */  
CREATE PROCEDURE dbo. usp_InsertProductionLocation  
    @TVP LocationTableType READONLY  
    AS   
    SET NOCOUNT ON  
    INSERT INTO AdventureWorks2012.Production.Location  
           (Name  
           ,CostRate  
           ,Availability  
           ,ModifiedDate)  
        SELECT *, 0, GETDATE()  
        FROM  @TVP;  
        GO  
  
/* Declare a variable that references the type. */  
DECLARE @LocationTVP AS LocationTableType;  
  
/* Add data to the table variable. */  
INSERT INTO @LocationTVP (LocationName, CostRate)  
    SELECT Name, 0.00  
    FROM AdventureWorks2012.Person.StateProvince;  
  
/* Pass the table variable data to a stored procedure. */  
EXEC usp_InsertProductionLocation @LocationTVP;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0040-146">参照</span><span class="sxs-lookup"><span data-stu-id="f0040-146">See Also</span></span>  
 <span data-ttu-id="f0040-147">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f0040-147">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) </span></span>  
 <span data-ttu-id="f0040-148">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f0040-148">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="f0040-149">[sys &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f0040-149">[sys.types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql) </span></span>  
 <span data-ttu-id="f0040-150">[Transact-sql&#41;&#40;のパラメーター](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f0040-150">[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql) </span></span>  
 <span data-ttu-id="f0040-151">[parameter_type_usages &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f0040-151">[sys.parameter_type_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql) </span></span>  
 <span data-ttu-id="f0040-152">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f0040-152">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 [<span data-ttu-id="f0040-153">CREATE FUNCTION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f0040-153">CREATE FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-function-transact-sql)  
  
  
