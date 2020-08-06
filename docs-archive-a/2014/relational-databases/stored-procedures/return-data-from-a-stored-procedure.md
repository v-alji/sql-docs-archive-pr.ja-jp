---
title: ストアド プロシージャからデータを返す | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], returning data
- returning data from stored procedure
ms.assetid: 7a428ffe-cd87-4f42-b3f1-d26aa8312bf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 472ca5cf27f7e7ea2b18daa961c19faadcf2251f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646115"
---
# <a name="return-data-from-a-stored-procedure"></a><span data-ttu-id="c9fa2-102">ストアド プロシージャからデータを返す</span><span class="sxs-lookup"><span data-stu-id="c9fa2-102">Return Data from a Stored Procedure</span></span>
  <span data-ttu-id="c9fa2-103">結果セットやプロシージャからのデータを呼び出し元のプログラムに返す手段には、出力パラメーターとリターン コードの 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-103">There are two ways of returning result sets or data from a procedure to a calling program: output parameters and return codes.</span></span> <span data-ttu-id="c9fa2-104">このトピックでは、両方のアプローチについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-104">This topic provides information on both approaches.</span></span>  
  
## <a name="returning-data-using-an-output-parameter"></a><span data-ttu-id="c9fa2-105">出力パラメーターを使用してデータを返す処理</span><span class="sxs-lookup"><span data-stu-id="c9fa2-105">Returning Data Using an Output Parameter</span></span>  
 <span data-ttu-id="c9fa2-106">プロシージャの定義でパラメーターに OUTPUT キーワードを指定すると、プロシージャの終了時に、そのパラメーターの現在値を呼び出し元のプログラムに返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-106">If you specify the OUTPUT keyword for a parameter in the procedure definition, the procedure can return the current value of the parameter to the calling program when the procedure exits.</span></span> <span data-ttu-id="c9fa2-107">呼び出し元のプログラムで使用できる変数にパラメーターの値を保存するには、呼び出し元のプログラムがプロシージャを実行する際に OUTPUT キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-107">To save the value of the parameter in a variable that can be used in the calling program, the calling program must use the OUTPUT keyword when executing the procedure.</span></span> <span data-ttu-id="c9fa2-108">出力パラメーターとして使用できるデータ型の詳細については、「[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-108">For more information about what data types can be used as output parameters, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
### <a name="examples-of-output-parameter"></a><span data-ttu-id="c9fa2-109">出力パラメーターの例</span><span class="sxs-lookup"><span data-stu-id="c9fa2-109">Examples of Output Parameter</span></span>  
 <span data-ttu-id="c9fa2-110">次の例では、入力パラメーターと出力パラメーターを使用するプロシージャを示します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-110">The following example shows a procedure with an input and an output parameter.</span></span> <span data-ttu-id="c9fa2-111">`@SalesPerson` パラメーターは、呼び出し元のプログラムによって指定された入力値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-111">The `@SalesPerson` parameter would receive an input value specified by the calling program.</span></span> <span data-ttu-id="c9fa2-112">SELECT ステートメントは、入力パラメーターに渡された値を使用して、適切な `SalesYTD` 値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-112">The SELECT statement uses the value passed into the input parameter to obtain the correct `SalesYTD` value.</span></span> <span data-ttu-id="c9fa2-113">また、SELECT ステートメントは、その値を `@SalesYTD` 出力パラメーターに代入します。これにより、プロシージャの終了時にその値が呼び出し元のプログラムに返されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-113">The SELECT statement also assigns the value to the `@SalesYTD` output parameter, which returns the value to the calling program when the procedure exits.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetEmployeeSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetEmployeeSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetEmployeeSalesYTD  
@SalesPerson nvarchar(50),  
@SalesYTD money OUTPUT  
AS    
  
    SET NOCOUNT ON;  
    SELECT @SalesYTD = SalesYTD  
    FROM Sales.SalesPerson AS sp  
    JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
    WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 <span data-ttu-id="c9fa2-114">次の例では、最初の例で作成したプロシージャを呼び出し、そのプロシージャから返された出力値を `@SalesYTD` 変数に保存します。これは、呼び出し元のプログラムに対してローカルです。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-114">The following example calls the procedure created in the first example and saves the output value returned from the called procedure in the `@SalesYTD` variable, which is local to the calling program.</span></span>  
  
```  
-- Declare the variable to receive the output value of the procedure.  
DECLARE @SalesYTDBySalesPerson money;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTDBySalesPerson  
EXECUTE Sales.uspGetEmployeeSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDBySalesPerson OUTPUT;  
-- Display the value returned by the procedure.  
PRINT 'Year-to-date sales for this employee is ' +   
    convert(varchar(10),@SalesYTDBySalesPerson);  
GO  
  
```  
  
 <span data-ttu-id="c9fa2-115">プロシージャを実行する際に、OUTPUT パラメーターに対する入力値を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-115">Input values can also be specified for OUTPUT parameters when the procedure is executed.</span></span> <span data-ttu-id="c9fa2-116">これにより、プロシージャは、呼び出し元のプログラムから値を受け取って、その値を変更するかその値を使用して操作を実行してから、新しい値を呼び出し元のプログラムに返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-116">This allows the procedure to receive a value from the calling program, change or perform operations with the value, and then return the new value to the calling program.</span></span> <span data-ttu-id="c9fa2-117">前の例では、プログラムによって `@SalesYTDBySalesPerson` プロシージャが呼び出される前に、 `Sales.uspGetEmployeeSalesYTD` 変数に値を代入できます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-117">In the previous example, the `@SalesYTDBySalesPerson` variable can be assigned a value before the program calls the `Sales.uspGetEmployeeSalesYTD` procedure.</span></span> <span data-ttu-id="c9fa2-118">実行ステートメントは、 `@SalesYTDBySalesPerson` 変数の値を `@SalesYTD` OUTPUT パラメーターに渡します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-118">The execute statement would pass the `@SalesYTDBySalesPerson` variable value into the `@SalesYTD` OUTPUT parameter.</span></span> <span data-ttu-id="c9fa2-119">その後、プロシージャの本体で、新しい値を生成する計算にその値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-119">Then in the procedure body, the value could be used for calculations that generate a new value.</span></span> <span data-ttu-id="c9fa2-120">新しい値は OUTPUT パラメーターを通じてプロシージャから戻され、プロシージャの終了時に `@SalesYTDBySalesPerson` 変数の値が更新されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-120">The new value would be passed back out of the procedure through the OUTPUT parameter, updating the value in the `@SalesYTDBySalesPerson` variable when the procedure exits.</span></span> <span data-ttu-id="c9fa2-121">これは通常、パラメーターの "参照渡し機能" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-121">This is often referred to as "pass-by-reference capability."</span></span>  
  
 <span data-ttu-id="c9fa2-122">プロシージャを呼び出す際にパラメーターに OUTPUT を指定した場合は、そのパラメーターがプロシージャの定義で OUTPUT を使用して定義されていないと、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-122">If you specify OUTPUT for a parameter when you call a procedure and that parameter is not defined by using OUTPUT in the procedure definition, you get an error message.</span></span> <span data-ttu-id="c9fa2-123">ただし、プロシージャに出力パラメーターを定義しておき、OUTPUT を指定せずにこのプロシージャを実行することも可能です。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-123">However, you can execute a procedure with output parameters and not specify OUTPUT when executing the procedure.</span></span> <span data-ttu-id="c9fa2-124">エラーは返されませんが、呼び出し側のプログラムで出力値を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-124">No error is returned, but you cannot use the output value in the calling program.</span></span>  
  
### <a name="using-the-cursor-data-type-in-output-parameters"></a><span data-ttu-id="c9fa2-125">OUTPUT パラメーターでの cursor データ型の使用</span><span class="sxs-lookup"><span data-stu-id="c9fa2-125">Using the Cursor Data Type in OUTPUT Parameters</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)]<span data-ttu-id="c9fa2-126">プロシージャでは、 `cursor` 出力パラメーターにのみデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-126">procedures can use the `cursor` data type only for OUTPUT parameters.</span></span> <span data-ttu-id="c9fa2-127">`cursor`パラメーターにデータ型が指定されている場合は、プロシージャの定義でそのパラメーターに対して VARYING キーワードと OUTPUT キーワードの両方を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-127">If the `cursor` data type is specified for a parameter, both the VARYING and OUTPUT keywords must be specified for that parameter in the procedure definition.</span></span> <span data-ttu-id="c9fa2-128">パラメーターは出力のみとして指定できますが、VARYING キーワードがパラメーター宣言で指定されている場合、データ型はである必要があり、 `cursor` output キーワードも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-128">A parameter can be specified as only OUTPUT but if the VARYING keyword is specified in the parameter declaration, the data type must be `cursor` and the OUTPUT keyword must also be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9fa2-129">`cursor` データ型は OLE DB、ODBC、ADO、DB-Library などのデータベース API からアプリケーション変数にバインドすることができません。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-129">The `cursor` data type cannot be bound to application variables through the database APIs such as OLE DB, ODBC, ADO, and DB-Library.</span></span> <span data-ttu-id="c9fa2-130">アプリケーションでプロシージャを実行するには OUTPUT パラメーターがバインドされている必要があるので、`cursor` 型の OUTPUT パラメーターを指定したプロシージャはデータベース API から呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-130">Because OUTPUT parameters must be bound before an application can execute a procedure, procedures with `cursor` OUTPUT parameters cannot be called from the database APIs.</span></span> <span data-ttu-id="c9fa2-131">そのようなプロシージャは、`cursor` 型の OUTPUT 変数を [!INCLUDE[tsql](../../../includes/tsql-md.md)] の `cursor` 型のローカル変数に代入したときのみ、[!INCLUDE[tsql](../../../includes/tsql-md.md)] バッチ、プロシージャ、またはトリガーから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-131">These procedures can be called from [!INCLUDE[tsql](../../../includes/tsql-md.md)] batches, procedures, or triggers only when the `cursor` OUTPUT variable is assigned to a [!INCLUDE[tsql](../../../includes/tsql-md.md)] local `cursor` variable.</span></span>  
  
### <a name="rules-for-cursor-output-parameters"></a><span data-ttu-id="c9fa2-132">cursor 出力パラメーターに関する規則</span><span class="sxs-lookup"><span data-stu-id="c9fa2-132">Rules for Cursor Output Parameters</span></span>  
 <span data-ttu-id="c9fa2-133">プロシージャの実行時には、次の規則が `cursor` 出力パラメーターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-133">The following rules pertain to `cursor` output parameters when the procedure is executed:</span></span>  
  
-   <span data-ttu-id="c9fa2-134">順方向専用カーソルの場合、カーソルの結果セットとして返される行は、プロシージャの実行が終了したときにカーソルがあった位置以降の行に限られます。たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-134">For a forward-only cursor, the rows returned in the cursor's result set are only those rows at and beyond the position of the cursor at the conclusion of the procedure execution, for example:</span></span>  
  
    -   <span data-ttu-id="c9fa2-135">RS という名前の 100 行から構成される結果セットに対するプロシージャ内で、スクロールできないカーソルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-135">A nonscrollable cursor is opened in a procedure on a result set named RS of 100 rows.</span></span>  
  
    -   <span data-ttu-id="c9fa2-136">プロシージャにより結果セット RS の最初の 5 行がフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-136">The procedure fetches the first 5 rows of result set RS.</span></span>  
  
    -   <span data-ttu-id="c9fa2-137">プロシージャが呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-137">The procedure returns to its caller.</span></span>  
  
    -   <span data-ttu-id="c9fa2-138">呼び出し元に返される結果セット RS は RS の 6 行目から 100 行目までで構成され、呼び出し元のカーソルは RS の 1 行目の前に置かれます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-138">The result set RS returned to the caller consists of rows from 6 through 100 of RS, and the cursor in the caller is positioned before the first row of RS.</span></span>  
  
-   <span data-ttu-id="c9fa2-139">順方向専用カーソルの場合、プロシージャが終了した時点でカーソルが 1 行目の前にあれば、呼び出し元のバッチ、プロシージャ、またはトリガーには結果セット全体が返されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-139">For a forward-only cursor, if the cursor is positioned before the first row when the procedure exits, the entire result set is returned to the calling batch, procedure, or trigger.</span></span> <span data-ttu-id="c9fa2-140">結果セットが返されるとき、カーソル位置は 1 行目の前に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-140">When returned, the cursor position is set before the first row.</span></span>  
  
-   <span data-ttu-id="c9fa2-141">順方向専用カーソルの場合、プロシージャが終了した時点でカーソルが最後の行の後にあれば、呼び出し元のバッチ、プロシージャ、またはトリガーには空の結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-141">For a forward-only cursor, if the cursor is positioned beyond the end of the last row when the procedure exits, an empty result set is returned to the calling batch, procedure, or trigger.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9fa2-142">空の結果セットは、NULL 値と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-142">An empty result set is not the same as a null value.</span></span>  
  
-   <span data-ttu-id="c9fa2-143">スクロール可能なカーソルの場合、プロシージャが終了した時点で、呼び出し元のバッチ、プロシージャ、またはトリガーに結果セット内のすべての行が返されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-143">For a scrollable cursor, all the rows in the result set are returned to the calling batch, procedure, or trigger when the procedure exits.</span></span> <span data-ttu-id="c9fa2-144">結果セットが返されるとき、カーソル位置はプロシージャで最後にフェッチを行った位置のままです。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-144">When returned, the cursor position is left at the position of the last fetch executed in the procedure.</span></span>  
  
-   <span data-ttu-id="c9fa2-145">カーソルがクローズしている場合は、カーソルの種類にかかわらず、呼び出し元のバッチ、プロシージャ、またはトリガーには null 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-145">For any type of cursor, if the cursor is closed, then a null value is passed back to the calling batch, procedure, or trigger.</span></span> <span data-ttu-id="c9fa2-146">カーソルがパラメーターに割り当てられていて、そのカーソルが一度も開かれない場合も、同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-146">This will also be the case if a cursor is assigned to a parameter, but that cursor is never opened.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9fa2-147">カーソルがクローズしているかどうかが問題になるのは、結果セットが返される時点のみです。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-147">The closed state matters only at return time.</span></span> <span data-ttu-id="c9fa2-148">たとえば、プロシージャの途中でカーソルを閉じ、その後で再び開いて、そのカーソルの結果セットを呼び出し元のバッチ、プロシージャ、またはトリガーに返すのは有効な操作です。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-148">For example, it is valid to close a cursor part of the way through the procedure, to open it again later in the procedure, and return that cursor's result set to the calling batch, procedure, or trigger.</span></span>  
  
### <a name="examples-of-cursor-output-parameters"></a><span data-ttu-id="c9fa2-149">cursor 出力パラメーターの例</span><span class="sxs-lookup"><span data-stu-id="c9fa2-149">Examples of Cursor Output Parameters</span></span>  
 <span data-ttu-id="c9fa2-150">次の例では、 `@currency` `cursor` データ型を使用して、出力パラメーター _ を指定したプロシージャを作成し `cursor` ます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-150">In the following example, a procedure is created that specified an output parameter, `@currency`_`cursor` using the `cursor` data type.</span></span> <span data-ttu-id="c9fa2-151">作成したプロシージャはバッチで呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-151">The procedure is then called in a batch.</span></span>  
  
 <span data-ttu-id="c9fa2-152">まず、Currency テーブルに対してカーソルを宣言し、そのカーソルを開くプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-152">First, create the procedure that declares and then opens a cursor on the Currency table.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspCurrencyCursor', 'P' ) IS NOT NULL  
    DROP PROCEDURE dbo.uspCurrencyCursor;  
GO  
CREATE PROCEDURE dbo.uspCurrencyCursor   
    @CurrencyCursor CURSOR VARYING OUTPUT  
AS  
    SET NOCOUNT ON;  
    SET @CurrencyCursor = CURSOR  
    FORWARD_ONLY STATIC FOR  
      SELECT CurrencyCode, Name  
      FROM Sales.Currency;  
    OPEN @CurrencyCursor;  
GO  
  
```  
  
 <span data-ttu-id="c9fa2-153">次に、cursor 型のローカル変数を宣言し、そのローカル変数にカーソルを代入するプロシージャを実行し、代入したカーソルから行をフェッチするというバッチを実行します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-153">Next, execute a batch that declares a local cursor variable, executes the procedure to assign the cursor to the local variable, and then fetches the rows from the cursor.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyCursor CURSOR;  
EXEC dbo.uspCurrencyCursor @CurrencyCursor = @MyCursor OUTPUT;  
WHILE (@@FETCH_STATUS = 0)  
BEGIN;  
     FETCH NEXT FROM @MyCursor;  
END;  
CLOSE @MyCursor;  
DEALLOCATE @MyCursor;  
GO  
  
```  
  
## <a name="returning-data-using-a-return-code"></a><span data-ttu-id="c9fa2-154">リターン コードを使用してデータを返す処理</span><span class="sxs-lookup"><span data-stu-id="c9fa2-154">Returning Data Using a Return Code</span></span>  
 <span data-ttu-id="c9fa2-155">プロシージャは、リターン コードという整数値を返してプロシージャの実行状態を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-155">A procedure can return an integer value called a return code to indicate the execution status of a procedure.</span></span> <span data-ttu-id="c9fa2-156">プロシージャのリターン コードを指定するには、RETURN ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-156">You specify the return code for a procedure using the RETURN statement.</span></span> <span data-ttu-id="c9fa2-157">OUTPUT パラメーターと同様に、呼び出し元のプログラムでリターン コード値を使用するには、プロシージャの実行時にリターン コードを変数に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-157">As with OUTPUT parameters, you must save the return code in a variable when the procedure is executed in order to use the return code value in the calling program.</span></span> <span data-ttu-id="c9fa2-158">たとえば、 `@result` データ型の代入変数は、 `int` 次のように、プロシージャからのリターンコードを格納するために使用され `my_proc` ます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-158">For example, the assignment variable `@result` of data type `int` is used to store the return code from the procedure `my_proc`, such as:</span></span>  
  
```  
DECLARE @result int;  
EXECUTE @result = my_proc;  
```  
  
 <span data-ttu-id="c9fa2-159">リターン コードは、可能性のあるエラー状態ごとにリターン コードの値を設定するために、プロシージャのフロー制御ブロックの中でよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-159">Return codes are commonly used in control-of-flow blocks within procedures to set the return code value for each possible error situation.</span></span> <span data-ttu-id="c9fa2-160">[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントの後で @@ERROR 関数を使用すると、ステートメントの実行中にエラーが発生したかどうかを検出できます。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-160">You can use the @@ERROR function after a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement to detect whether an error occurred during the execution of the statement.</span></span>  
  
### <a name="examples-of-return-codes"></a><span data-ttu-id="c9fa2-161">リターン コードの例</span><span class="sxs-lookup"><span data-stu-id="c9fa2-161">Examples of Return Codes</span></span>  
 <span data-ttu-id="c9fa2-162">次の例では、さまざまなエラーに特別なリターン コード値を設定するエラー処理を含む `usp_GetSalesYTD` プロシージャを示します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-162">The following example shows the `usp_GetSalesYTD` procedure with error handling that sets special return code values for various errors.</span></span> <span data-ttu-id="c9fa2-163">次の表では、可能性のある各エラーに対してプロシージャによって割り当てられる整数値と、各値に相当する意味を示します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-163">The following table shows the integer value that is assigned by the procedure to each possible error, and the corresponding meaning for each value.</span></span>  
  
|<span data-ttu-id="c9fa2-164">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="c9fa2-164">Return code value</span></span>|<span data-ttu-id="c9fa2-165">意味</span><span class="sxs-lookup"><span data-stu-id="c9fa2-165">Meaning</span></span>|  
|-----------------------|-------------|  
|<span data-ttu-id="c9fa2-166">0</span><span class="sxs-lookup"><span data-stu-id="c9fa2-166">0</span></span>|<span data-ttu-id="c9fa2-167">実行に成功しました。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-167">Successful execution.</span></span>|  
|<span data-ttu-id="c9fa2-168">1</span><span class="sxs-lookup"><span data-stu-id="c9fa2-168">1</span></span>|<span data-ttu-id="c9fa2-169">必要なパラメーター値が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-169">Required parameter value is not specified.</span></span>|  
|<span data-ttu-id="c9fa2-170">2</span><span class="sxs-lookup"><span data-stu-id="c9fa2-170">2</span></span>|<span data-ttu-id="c9fa2-171">指定されたパラメーター値が無効です。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-171">Specified parameter value is not valid.</span></span>|  
|<span data-ttu-id="c9fa2-172">3</span><span class="sxs-lookup"><span data-stu-id="c9fa2-172">3</span></span>|<span data-ttu-id="c9fa2-173">売上高の値を取得中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-173">Error has occurred getting sales value.</span></span>|  
|<span data-ttu-id="c9fa2-174">4</span><span class="sxs-lookup"><span data-stu-id="c9fa2-174">4</span></span>|<span data-ttu-id="c9fa2-175">販売員の売上高の値に NULL 値が検出されました。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-175">NULL sales value found for the salesperson.</span></span>|  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.usp_GetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.usp_GetSalesYTD;  
GO  
CREATE PROCEDURE Sales.usp_GetSalesYTD  
@SalesPerson nvarchar(50) = NULL,  -- NULL default value  
@SalesYTD money = NULL OUTPUT  
AS    
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
   BEGIN  
       PRINT 'ERROR: You must specify a last name for the sales person.'  
       RETURN(1)  
   END  
ELSE  
   BEGIN  
   -- Make sure the value is valid.  
   IF (SELECT COUNT(*) FROM HumanResources.vEmployee  
          WHERE LastName = @SalesPerson) = 0  
      RETURN(2)  
   END  
-- Get the sales for the specified name and   
-- assign it to the output parameter.  
SELECT @SalesYTD = SalesYTD   
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
-- Check for SQL Server errors.  
IF @@ERROR <> 0   
   BEGIN  
      RETURN(3)  
   END  
ELSE  
   BEGIN  
   -- Check to see if the ytd_sales value is NULL.  
     IF @SalesYTD IS NULL  
       RETURN(4)   
     ELSE  
      -- SUCCESS!!  
        RETURN(0)  
   END  
-- Run the stored procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the stored procedure with an input value.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTD  
EXECUTE Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
PRINT N'Year-to-date sales for this employee is ' +  
    CONVERT(varchar(10), @SalesYTDForSalesPerson);  
  
```  
  
 <span data-ttu-id="c9fa2-176">次の例では、 `usp_GetSalesYTD` プロシージャから返されるリターン コードを処理するプログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9fa2-176">The following example creates a program to handle the return codes that are returned from the `usp_GetSalesYTD` procedure.</span></span>  
  
```  
-- Declare the variables to receive the output value and return code   
-- of the procedure.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
  
-- Execute the procedure with a title_id value  
-- and save the output value and return code in variables.  
EXECUTE @ret_code = Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
--  Check the return codes.  
IF @ret_code = 0  
BEGIN  
   PRINT 'Procedure executed successfully'  
   -- Display the value returned by the procedure.  
   PRINT 'Year-to-date sales for this employee is ' + CONVERT(varchar(10),@SalesYTDForSalesPerson)  
END  
ELSE IF @ret_code = 1  
   PRINT 'ERROR: You must specify a last name for the sales person.'  
ELSE IF @ret_code = 2   
   PRINT 'EERROR: You must enter a valid last name for the sales person.'  
ELSE IF @ret_code = 3  
   PRINT 'ERROR: An error occurred getting sales value.'  
ELSE IF @ret_code = 4  
   PRINT 'ERROR: No sales recorded for this employee.'     
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9fa2-177">参照</span><span class="sxs-lookup"><span data-stu-id="c9fa2-177">See Also</span></span>  
 <span data-ttu-id="c9fa2-178">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9fa2-178">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="c9fa2-179">[PRINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/print-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9fa2-179">[PRINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/print-transact-sql) </span></span>  
 <span data-ttu-id="c9fa2-180">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9fa2-180">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="c9fa2-181">[カーソル](../cursors.md) </span><span class="sxs-lookup"><span data-stu-id="c9fa2-181">[Cursors](../cursors.md) </span></span>  
 <span data-ttu-id="c9fa2-182">[RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9fa2-182">[RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql) </span></span>  
 [<span data-ttu-id="c9fa2-183">@@ERROR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c9fa2-183">@@ERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/error-transact-sql)  
  
  
