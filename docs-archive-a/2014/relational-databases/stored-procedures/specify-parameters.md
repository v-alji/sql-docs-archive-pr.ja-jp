---
title: パラメーターの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], stored procedures
- stored procedures [SQL Server], parameters
- output parameters [SQL Server]
- input parameters [SQL Server]
ms.assetid: 902314fe-5f9c-4d0d-a0b7-27e67c9c70ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: d93a04281839c4db26cbab16ac166af3cdb7c9a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646114"
---
# <a name="specify-parameters"></a><span data-ttu-id="af420-102">パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="af420-102">Specify Parameters</span></span>
  <span data-ttu-id="af420-103">プロシージャのパラメーターを指定することで、呼び出し元のプログラムからプロシージャの本体に値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="af420-103">By specifying procedure parameters, calling programs are able to pass values into the body of the procedure.</span></span> <span data-ttu-id="af420-104">これらの値は、プロシージャの実行中にさまざまな目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="af420-104">Those values can be used for a variety of purposes during procedure execution.</span></span> <span data-ttu-id="af420-105">プロシージャ パラメーターも、パラメーターが OUTPUT パラメーターとしてマークされている場合は、呼び出し元のプログラムに値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="af420-105">Procedure parameters can also return values to the calling program if the parameter is marked as an OUTPUT parameter.</span></span>  
  
 <span data-ttu-id="af420-106">プロシージャには最大 2,100 個のパラメーターを指定できます。各パラメーターには、名前、データ型、および方向が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="af420-106">A procedure can have a maximum of 2100 parameters; each assigned a name, data type, and direction.</span></span> <span data-ttu-id="af420-107">パラメーターには、必要に応じて既定値を割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="af420-107">Optionally, parameters can be assigned default values.</span></span>  
  
 <span data-ttu-id="af420-108">次のセクションでは、パラメーターに値を渡す処理と、プロシージャ呼び出しで各パラメーター属性を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="af420-108">The following section provides information about passing values into parameters and about how each of the parameter attributes is used during a procedure call.</span></span>  
  
## <a name="passing-values-into-parameters"></a><span data-ttu-id="af420-109">パラメーターに値を渡す処理</span><span class="sxs-lookup"><span data-stu-id="af420-109">Passing Values into Parameters</span></span>  
 <span data-ttu-id="af420-110">プロシージャ呼び出しで指定されるパラメーター値は、定数か変数である必要があります。関数名をパラメーター値として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="af420-110">The parameter values supplied with a procedure call must be constants or a variable; a function name cannot be used as a parameter value.</span></span> <span data-ttu-id="af420-111">変数には、ユーザー定義変数や \@\@spid などのシステム変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="af420-111">Variables can be user-defined or system variables such as \@\@spid.</span></span>  
  
 <span data-ttu-id="af420-112">次の例は、パラメーター値をプロシージャ `uspGetWhereUsedProductID`に渡す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="af420-112">The following examples demonstrate passing parameter values to the procedure `uspGetWhereUsedProductID`.</span></span> <span data-ttu-id="af420-113">この例では、定数および変数としてパラメーターを渡す方法のほか、変数を使用して関数の値を渡す方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="af420-113">They illustrate how to pass parameters as constants and variables and also how to use a variable to pass the value of a function.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
-- Passing values as constants.  
EXEC dbo.uspGetWhereUsedProductID 819, '20050225';  
GO  
-- Passing values as variables.  
DECLARE @ProductID int, @CheckDate datetime;  
SET @ProductID = 819;  
SET @CheckDate = '20050225';  
EXEC dbo.uspGetWhereUsedProductID @ProductID, @CheckDate;  
GO  
-- Try to use a function as a parameter value.  
-- This produces an error message.  
EXEC dbo.uspGetWhereUsedProductID 819, GETDATE();  
GO  
-- Passing the function value as a variable.  
DECLARE @CheckDate datetime;  
SET @CheckDate = GETDATE();  
EXEC dbo.uspGetWhereUsedProductID 819, @CheckDate;  
GO  
```  
  
## <a name="specifying-parameter-names"></a><span data-ttu-id="af420-114">パラメーター名の指定</span><span class="sxs-lookup"><span data-stu-id="af420-114">Specifying Parameter Names</span></span>  
 <span data-ttu-id="af420-115">プロシージャを作成してパラメーター名を宣言する際には、パラメーター名の先頭を 1 つの \@ 文字にし、そのプロシージャのスコープ内でパラメーター名が一意になるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="af420-115">When creating a procedure and declaring a parameter name, the parameter name must begin with a single \@ character and must be unique in the scope of the procedure.</span></span>  
  
 <span data-ttu-id="af420-116">パラメーターに明示的に名前を付け、プロシージャ呼び出しで各パラメーターに適切な値を代入することで、パラメーターを任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="af420-116">Explicitly naming the parameters and assigning the appropriate values to each parameter in a procedure call allows the parameters to be supplied in any order.</span></span> <span data-ttu-id="af420-117">たとえば、**my_proc** というプロシージャが **\@first**、 **\@second**、および **\@third** という 3 つのパラメーターを必要とする場合、プロシージャに渡される値は、`EXECUTE my_proc @second = 2, @first = 1, @third = 3;` ようにパラメーター名に代入できます。</span><span class="sxs-lookup"><span data-stu-id="af420-117">For example, if the procedure **my_proc** expects three parameters named **\@first**, **\@second**, and **\@third**, the values passed to the procedure can be assigned to the parameter names, such as: `EXECUTE my_proc @second = 2, @first = 1, @third = 3;`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af420-118">1 つのパラメーター値を **\@parameter =** _value_ の形式で指定した場合は、後続のパラメーターもすべてこの形式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af420-118">If one parameter value is supplied in the form **\@parameter =**_value_, all subsequent parameters must be supplied in this manner.</span></span> <span data-ttu-id="af420-119">パラメーター値を **\@parameter =** _value_ の形式で渡さない場合は、CREATE PROCEDURE ステートメント内のパラメーターと同じ順序 (左から右) で値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af420-119">If the parameter values are not passed in the form **\@parameter =**_value_, the values must be supplied in the identical order (left to right) as the parameters are listed in the CREATE PROCEDURE statement.</span></span>  
> 
> [!WARNING]
>  <span data-ttu-id="af420-120">**\@parameter =** _value_ の形式で渡すパラメーターのスペルが間違っていると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってエラーが生成され、プロシージャは実行されません。</span><span class="sxs-lookup"><span data-stu-id="af420-120">Any parameter passed in the form **\@parameter =**_value_ with the parameter misspelled, will cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate an error and prevent procedure execution.</span></span>  
  
## <a name="specifying-parameter-data-types"></a><span data-ttu-id="af420-121">パラメーターのデータ型の指定</span><span class="sxs-lookup"><span data-stu-id="af420-121">Specifying Parameter Data Types</span></span>  
 <span data-ttu-id="af420-122">パラメーターを CREATE PROCEDURE ステートメントで宣言する場合は、パラメーターのデータ型を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af420-122">Parameters must be defined with a data type when they are declared in a CREATE PROCEDURE statement.</span></span> <span data-ttu-id="af420-123">パラメーターのデータ型により、プロシージャの呼び出し時にパラメーターとして指定できる値の型と範囲が決まります。</span><span class="sxs-lookup"><span data-stu-id="af420-123">The data type of a parameter determines the type and range of values that are accepted for the parameter when the procedure is called.</span></span> <span data-ttu-id="af420-124">たとえば、`tinyint` データ型のパラメーターを定義した場合は、そのパラメーターに渡す値として 0 ～ 255 の範囲の数値だけを指定できます。</span><span class="sxs-lookup"><span data-stu-id="af420-124">For example, if you define a parameter with a `tinyint` data type, only numeric values ranging from 0 to 255 are accepted when passed into that parameter.</span></span> <span data-ttu-id="af420-125">指定したデータ型と互換性がない値を使用してプロシージャを実行すると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="af420-125">An error is returned if a procedure is executed with a value incompatible with the data type.</span></span>  
  
## <a name="specifying-parameter-default-values"></a><span data-ttu-id="af420-126">パラメーターの既定値の指定</span><span class="sxs-lookup"><span data-stu-id="af420-126">Specifying Parameter Default Values</span></span>  
 <span data-ttu-id="af420-127">宣言時にパラメーターに既定値が指定されていると、そのパラメーターは省略可能と見なされます。</span><span class="sxs-lookup"><span data-stu-id="af420-127">A parameter is considered optional if the parameter has a default value specified when it is declared.</span></span> <span data-ttu-id="af420-128">プロシージャ呼び出しで省略可能なパラメーターに値を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="af420-128">It is not necessary to provide a value for an optional parameter in a procedure call.</span></span>  
  
 <span data-ttu-id="af420-129">パラメーターの既定値は次の場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="af420-129">The default value of a parameter is used when:</span></span>  
  
-   <span data-ttu-id="af420-130">プロシージャ呼び出しでパラメーターの値が指定されていない場合</span><span class="sxs-lookup"><span data-stu-id="af420-130">No value for the parameter is specified in the procedure call.</span></span>  
  
-   <span data-ttu-id="af420-131">プロシージャ呼び出しで値として DEFAULT キーワードが指定されている場合</span><span class="sxs-lookup"><span data-stu-id="af420-131">The DEFAULT keyword is specified as the value in the procedure call.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af420-132">既定値が空白または句読点を含む文字列の場合、または数字で始まる場合 (たとえば 6xxx)、単一引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="af420-132">If the default value is a character string that contains embedded blanks or punctuation, or if it starts with a number (for example, 6xxx), it must be enclosed in single, straight quotation marks.</span></span>  
  
 <span data-ttu-id="af420-133">パラメーターに対して既定値として適切に値を指定できない場合は、NULL を既定値として指定してください。</span><span class="sxs-lookup"><span data-stu-id="af420-133">If no value can be specified appropriately as a default for the parameter, specify NULL as the default.</span></span> <span data-ttu-id="af420-134">パラメーターの値なしでプロシージャを実行する場合は、プロシージャからカスタマイズされたメッセージが返されるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="af420-134">It is a good idea to have the procedure return a customized message if the procedure is executed without a value for the parameter.</span></span>  
  
 <span data-ttu-id="af420-135">次の例で、 `usp_GetSalesYTD` という 1 つの入力パラメーターを伴う `@SalesPerson`プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="af420-135">The following example creates the `usp_GetSalesYTD` procedure with one input parameter, `@SalesPerson`.</span></span> <span data-ttu-id="af420-136">このパラメーターには既定値として NULL が割り当てられています。 `@SalesPerson` パラメーターに値を指定せずにプロシージャを実行した場合にカスタム エラー メッセージを返すエラー処理ステートメントで NULL を使用します。</span><span class="sxs-lookup"><span data-stu-id="af420-136">NULL is assigned as the default value for the parameter and is used in error handling statements to return a custom error message for cases when the procedure is executed without a value for the `@SalesPerson` parameter.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetSalesYTD  
@SalesPerson nvarchar(50) = NULL  -- NULL default value  
AS   
    SET NOCOUNT ON;   
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
BEGIN  
   PRINT 'ERROR: You must specify the last name of the sales person.'  
   RETURN  
END  
-- Get the sales for the specified sales person and   
-- assign it to the output parameter.  
SELECT SalesYTD  
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 <span data-ttu-id="af420-137">次の例では、プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="af420-137">The following example executes the procedure.</span></span> <span data-ttu-id="af420-138">最初のステートメントは、入力値を指定せずにプロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="af420-138">The first statement executes the procedure without specifying an input value.</span></span> <span data-ttu-id="af420-139">その結果、プロシージャのエラー処理ステートメントによってカスタム エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="af420-139">This causes the error handling statements in the procedure to return the custom error message.</span></span> <span data-ttu-id="af420-140">2 番目のステートメントでは入力値を渡し、予期した結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="af420-140">The second statement supplies an input value and returns the expected result set.</span></span>  
  
```  
-- Run the procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the procedure with an input value.  
EXEC Sales.usp_GetSalesYTD N'Blythe';  
GO  
```  
  
 <span data-ttu-id="af420-141">既定値が指定されているパラメーターは省略できますが、パラメーターの一覧を切り捨てることしかできません。</span><span class="sxs-lookup"><span data-stu-id="af420-141">Although parameters for which defaults have been supplied can be omitted, the list of parameters can only be truncated.</span></span> <span data-ttu-id="af420-142">たとえば、プロシージャに 5 つのパラメーターがある場合は、4 番目と 5 番目のパラメーターを両方とも省略できます。</span><span class="sxs-lookup"><span data-stu-id="af420-142">For example, if a procedure has five parameters, both the fourth and the fifth parameters can be omitted.</span></span> <span data-ttu-id="af420-143">ただし、 **\@parameter =** _value_ の形式でパラメーターを指定しない限り、4 番目のパラメーターを省略して 5 番目のパラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="af420-143">However the fourth parameter cannot be skipped as long as the fifth parameter is included, unless the parameters are supplied in the form **\@parameter =**_value_.</span></span>  
  
## <a name="specifying-parameter-direction"></a><span data-ttu-id="af420-144">パラメーターの方向の指定</span><span class="sxs-lookup"><span data-stu-id="af420-144">Specifying Parameter Direction</span></span>  
 <span data-ttu-id="af420-145">パラメーターの方向は、入力または出力です。入力の場合は、値がプロシージャの本体に渡されます。出力の場合は、プロシージャが呼び出し元のプログラムに値を返します。</span><span class="sxs-lookup"><span data-stu-id="af420-145">The direction of a parameter is either input, a value is passed into the body of the procedure, or output, the procedure returns a value to the calling program.</span></span> <span data-ttu-id="af420-146">既定値は入力パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="af420-146">The default is an input parameter.</span></span>  
  
 <span data-ttu-id="af420-147">出力パラメーターを指定するには、CREATE PROCEDURE ステートメントでパラメーターの定義に OUTPUT キーワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af420-147">To specify an output parameter, the OUTPUT keyword must be specified in the definition of the parameter in the CREATE PROCEDURE statement.</span></span> <span data-ttu-id="af420-148">プロシージャは終了時に、呼び出し元のプログラムに現在の出力パラメーターの値を返します。</span><span class="sxs-lookup"><span data-stu-id="af420-148">The procedure returns the current value of the output parameter to the calling program when the procedure exits.</span></span> <span data-ttu-id="af420-149">呼び出し元のプログラムも、そのプログラムで使用できる変数にパラメーターの値を保存するために、プロシージャの実行時に OUTPUT キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af420-149">The calling program must also use the OUTPUT keyword when executing the procedure to save the parameter's value in a variable that can be used in the calling program.</span></span>  
  
 <span data-ttu-id="af420-150">次の例では、指定した価格を超えない製品の一覧を返す `Production.usp`_`GetList` プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="af420-150">The following example creates the `Production.usp`_`GetList` procedure, which returns a list of products that have prices that do not exceed a specified amount.</span></span> <span data-ttu-id="af420-151">ここでは、複数の SELECT ステートメントと複数の OUTPUT パラメーターを使用する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="af420-151">The example shows using multiple SELECT statements and multiple OUTPUT parameters.</span></span> <span data-ttu-id="af420-152">外部プロシージャ、バッチ、または複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、OUTPUT パラメーターを使用して、プロシージャの実行中に設定された値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="af420-152">OUTPUT parameters allow an external procedure, a batch, or more than one [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to access a value set during the procedure execution.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'Production.uspGetList', 'P' ) IS NOT NULL   
    DROP PROCEDURE Production.uspGetList;  
GO  
CREATE PROCEDURE Production.uspGetList @Product varchar(40)   
    , @MaxPrice money   
    , @ComparePrice money OUTPUT  
    , @ListPrice money OUT  
AS  
    SET NOCOUNT ON;  
    SELECT p.[Name] AS Product, p.ListPrice AS 'List Price'  
    FROM Production.Product AS p  
    JOIN Production.ProductSubcategory AS s   
      ON p.ProductSubcategoryID = s.ProductSubcategoryID  
    WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice;  
-- Populate the output variable @ListPprice.  
SET @ListPrice = (SELECT MAX(p.ListPrice)  
        FROM Production.Product AS p  
        JOIN  Production.ProductSubcategory AS s   
          ON p.ProductSubcategoryID = s.ProductSubcategoryID  
        WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice);  
-- Populate the output variable @compareprice.  
SET @ComparePrice = @MaxPrice;  
GO  
  
```  
  
 <span data-ttu-id="af420-153">`usp_GetList` を実行し、原価が $700 未満である [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 製品 (自転車) の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="af420-153">Execute `usp_GetList` to return a list of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] products (Bikes) that cost less than $700.</span></span> <span data-ttu-id="af420-154">ここではフロー制御言語と共に OUTPUT パラメーターの **\@cost** および **\@compareprices** を使用して、 **[メッセージ]** ウィンドウにメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="af420-154">The OUTPUT parameters **\@cost** and **\@compareprices** are used with control-of-flow language to return a message in the **Messages** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af420-155">プロシージャの作成中にも変数の使用中にも、OUTPUT 変数を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af420-155">The OUTPUT variable must be defined during the procedure creation and also during the use of the variable.</span></span> <span data-ttu-id="af420-156">パラメーター名と変数名が一致する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="af420-156">The parameter name and variable name do not have to match.</span></span> <span data-ttu-id="af420-157">ただし、データ型とパラメーターの位置は一致する必要があります ( **\@listprice=** _variable_ が使用されている場合は除きます)。</span><span class="sxs-lookup"><span data-stu-id="af420-157">However, the data type and parameter positioning must match (unless **\@listprice=** _variable_ is used).</span></span>  
  
```  
DECLARE @ComparePrice money, @Cost money ;  
EXECUTE Production.uspGetList '%Bikes%', 700,   
    @ComparePrice OUT,   
    @Cost OUTPUT  
IF @Cost <= @ComparePrice   
BEGIN  
    PRINT 'These products can be purchased for less than   
    $'+RTRIM(CAST(@ComparePrice AS varchar(20)))+'.'  
END  
ELSE  
    PRINT 'The prices for all products in this category exceed   
    $'+ RTRIM(CAST(@ComparePrice AS varchar(20)))+'.';  
  
```  
  
 <span data-ttu-id="af420-158">次に結果セットの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="af420-158">Here is the partial result set:</span></span>  
  
```  
Product                                            List Price  
-------------------------------------------------- ------------------  
Road-750 Black, 58                                 539.99  
Mountain-500 Silver, 40                            564.99  
Mountain-500 Silver, 42                            564.99  
...  
Road-750 Black, 48                                 539.99  
Road-750 Black, 52                                 539.99  
  
(14 row(s) affected)  
  
These items can be purchased for less than $700.00.  
```  
  
## <a name="see-also"></a><span data-ttu-id="af420-159">参照</span><span class="sxs-lookup"><span data-stu-id="af420-159">See Also</span></span>  
 [<span data-ttu-id="af420-160">CREATE PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af420-160">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
