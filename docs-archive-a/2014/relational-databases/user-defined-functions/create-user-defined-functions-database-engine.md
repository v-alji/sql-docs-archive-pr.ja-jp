---
title: ユーザー定義関数の作成 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SCHEMABINDING clause
- schema-bound functions [SQL Server]
- user-defined functions [SQL Server], creating
- CREATE FUNCTION statement
- valid statements [SQL Server]
ms.assetid: f0d5dd10-73fd-4e05-9177-07f56552bdf7
author: rothja
ms.author: jroth
ms.openlocfilehash: 790fa1b969f933890e050311173fcde3f12c37ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644872"
---
# <a name="create-user-defined-functions-database-engine"></a><span data-ttu-id="657b4-102">ユーザー定義関数の作成 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="657b4-102">Create User-defined Functions (Database Engine)</span></span>
  <span data-ttu-id="657b4-103">このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してユーザー定義関数を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="657b4-103">This topic describes how to create a user-defined function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="657b4-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="657b4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="657b4-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="657b4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="657b4-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="657b4-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="657b4-107">Security</span><span class="sxs-lookup"><span data-stu-id="657b4-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="657b4-108">**ユーザー定義関数を作成するには:**</span><span class="sxs-lookup"><span data-stu-id="657b4-108">**To create a user-defined function:**</span></span>  
  
     [<span data-ttu-id="657b4-109">スカラー関数の作成</span><span class="sxs-lookup"><span data-stu-id="657b4-109">Create a Scalar Function</span></span>](#Scalar)  
  
     [<span data-ttu-id="657b4-110">テーブル値関数の作成</span><span class="sxs-lookup"><span data-stu-id="657b4-110">Create a Table-valued Function</span></span>](#TVF)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="657b4-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="657b4-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="657b4-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="657b4-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="657b4-113">ユーザー定義関数は、データベースの状態を変更するアクションの実行に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="657b4-113">User-defined functions cannot be used to perform actions that modify the database state.</span></span>  
  
-   <span data-ttu-id="657b4-114">出力先がテーブルである OUTPUT INTO 句をユーザー定義関数に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="657b4-114">User-defined functions cannot contain an OUTPUT INTO clause that has a table as its target.</span></span>  
  
-   <span data-ttu-id="657b4-115">ユーザー定義関数では複数の結果セットは返せません。</span><span class="sxs-lookup"><span data-stu-id="657b4-115">User-defined functions can not return multiple result sets.</span></span> <span data-ttu-id="657b4-116">複数の結果セットを返す必要がある場合は、ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="657b4-116">Use a stored procedure if you need to return multiple result sets.</span></span>  
  
-   <span data-ttu-id="657b4-117">エラー処理は、ユーザー定義の関数では制限されます。</span><span class="sxs-lookup"><span data-stu-id="657b4-117">Error handling is restricted in a user-defined function.</span></span> <span data-ttu-id="657b4-118">UDF は試行をサポートしていません...CATCH @ERROR または RAISERROR。</span><span class="sxs-lookup"><span data-stu-id="657b4-118">A UDF does not support TRY...CATCH, @ERROR or RAISERROR.</span></span>  
  
-   <span data-ttu-id="657b4-119">ユーザー定義関数はストアド プロシージャを呼び出すことができませんが、拡張ストアド プロシージャを呼び出すことはできます。</span><span class="sxs-lookup"><span data-stu-id="657b4-119">User-defined functions cannot call a stored procedure, but can call an extended stored procedure.</span></span>  
  
-   <span data-ttu-id="657b4-120">ユーザー定義関数では、動的 SQL または一時テーブルを利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="657b4-120">User-defined functions cannot make use of dynamic SQL or temp tables.</span></span> <span data-ttu-id="657b4-121">テーブル変数は使用できます。</span><span class="sxs-lookup"><span data-stu-id="657b4-121">Table variables are allowed.</span></span>  
  
-   <span data-ttu-id="657b4-122">SET ステートメントはユーザー定義関数では使用できません。</span><span class="sxs-lookup"><span data-stu-id="657b4-122">SET statements are not allowed in a user-defined function.</span></span>  
  
-   <span data-ttu-id="657b4-123">FOR XML 句は使用できません。</span><span class="sxs-lookup"><span data-stu-id="657b4-123">The FOR XML clause is not allowed</span></span>  
  
-   <span data-ttu-id="657b4-124">ユーザー定義関数は入れ子にすることができます。つまり、1 つのユーザー定義関数で、別のユーザー定義関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="657b4-124">User-defined functions can be nested; that is, one user-defined function can call another.</span></span> <span data-ttu-id="657b4-125">呼び出された関数が実行を開始すると入れ子レベルが 1 つ上がり、呼び出された関数が実行を終了するとレベルが 1 つ下がります。</span><span class="sxs-lookup"><span data-stu-id="657b4-125">The nesting level is incremented when the called function starts execution, and decremented when the called function finishes execution.</span></span> <span data-ttu-id="657b4-126">ユーザー定義関数は、32 レベルまで入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="657b4-126">User-defined functions can be nested up to 32 levels.</span></span> <span data-ttu-id="657b4-127">入れ子レベルが最大値を超えると、関数チェーン全体の呼び出しが失敗します。</span><span class="sxs-lookup"><span data-stu-id="657b4-127">Exceeding the maximum levels of nesting causes the whole calling function chain to fail.</span></span> <span data-ttu-id="657b4-128">Transact-SQL ユーザー定義関数からマネージド コードへの参照は、32 レベルの入れ子制限のうちの 1 レベルとカウントします。</span><span class="sxs-lookup"><span data-stu-id="657b4-128">Any reference to managed code from a Transact-SQL user-defined function counts as one level against the 32-level nesting limit.</span></span> <span data-ttu-id="657b4-129">マネージド コード内から呼び出されたメソッドは、この制限としてはカウントされません。</span><span class="sxs-lookup"><span data-stu-id="657b4-129">Methods invoked from within managed code do not count against this limit.</span></span>  
  
-   <span data-ttu-id="657b4-130">以下の Service Broker ステートメントは、Transact-SQL ユーザー定義関数の定義に含めることができません。</span><span class="sxs-lookup"><span data-stu-id="657b4-130">The following Service Broker statements cannot be included in the definition of a Transact-SQL user-defined function:</span></span>  
  
    -   <span data-ttu-id="657b4-131">BEGIN DIALOG CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="657b4-131">BEGIN DIALOG CONVERSATION</span></span>  
  
    -   <span data-ttu-id="657b4-132">END CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="657b4-132">END CONVERSATION</span></span>  
  
    -   <span data-ttu-id="657b4-133">GET CONVERSATION GROUP</span><span class="sxs-lookup"><span data-stu-id="657b4-133">GET CONVERSATION GROUP</span></span>  
  
    -   <span data-ttu-id="657b4-134">MOVE CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="657b4-134">MOVE CONVERSATION</span></span>  
  
    -   <span data-ttu-id="657b4-135">RECEIVE</span><span class="sxs-lookup"><span data-stu-id="657b4-135">RECEIVE</span></span>  
  
    -   <span data-ttu-id="657b4-136">SEND</span><span class="sxs-lookup"><span data-stu-id="657b4-136">SEND</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="657b4-137">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="657b4-137">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="657b4-138">Permissions</span><span class="sxs-lookup"><span data-stu-id="657b4-138">Permissions</span></span>  
 <span data-ttu-id="657b4-139">データベースの CREATE FUNCTION 権限と、関数を作成するスキーマの ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="657b4-139">Requires CREATE FUNCTION permission in the database and ALTER permission on the schema in which the function is being created.</span></span> <span data-ttu-id="657b4-140">関数でユーザー定義型が指定されている場合は、その型に対する EXECUTE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="657b4-140">If the function specifies a user-defined type, requires EXECUTE permission on the type.</span></span>  
  
##  <a name="scalar-functions"></a><a name="Scalar"></a><span data-ttu-id="657b4-141">スカラー関数</span><span class="sxs-lookup"><span data-stu-id="657b4-141">Scalar Functions</span></span>  
 <span data-ttu-id="657b4-142">次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースに複数ステートメントのスカラー関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="657b4-142">The following example creates a multistatement scalar function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="657b4-143">この関数は、1 つの入力値 `ProductID`を受け取り、単一のデータ値 (在庫品目中の指定された製品に関する集計量) を返します。</span><span class="sxs-lookup"><span data-stu-id="657b4-143">The function takes one input value, a `ProductID`, and returns a single data value, the aggregated quantity of the specified product in inventory.</span></span>  
  
```  
IF OBJECT_ID (N'dbo.ufnGetInventoryStock', N'FN') IS NOT NULL  
    DROP FUNCTION ufnGetInventoryStock;  
GO  
CREATE FUNCTION dbo.ufnGetInventoryStock(@ProductID int)  
RETURNS int   
AS   
-- Returns the stock level for the product.  
BEGIN  
    DECLARE @ret int;  
    SELECT @ret = SUM(p.Quantity)   
    FROM Production.ProductInventory p   
    WHERE p.ProductID = @ProductID   
        AND p.LocationID = '6';  
     IF (@ret IS NULL)   
        SET @ret = 0;  
    RETURN @ret;  
END;  
GO  
  
```  
  
 <span data-ttu-id="657b4-144">次に、 `ufnGetInventoryStock` 関数を使用して、 `ProductModelID` が 75 ～ 80 の製品の現在の在庫量を返す例を示します。</span><span class="sxs-lookup"><span data-stu-id="657b4-144">The following example uses the `ufnGetInventoryStock` function to return the current inventory quantity for products that have a `ProductModelID` between 75 and 80.</span></span>  
  
```  
SELECT ProductModelID, Name, dbo.ufnGetInventoryStock(ProductID)AS CurrentSupply  
FROM Production.Product  
WHERE ProductModelID BETWEEN 75 and 80;  
  
```  
  
##  <a name="table-valued-functions"></a><a name="TVF"></a><span data-ttu-id="657b4-145">テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="657b4-145">Table-Valued Functions</span></span>  
 <span data-ttu-id="657b4-146">次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースにインライン テーブル値関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="657b4-146">The following example creates an inline table-valued function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="657b4-147">この関数は、入力パラメーターとして 1 つの顧客 (商店) ID を受け取り、 `ProductID`列と `Name`列、および過去 1 年間の集計である `YTD Total` を商店に販売した製品ごとに返します。</span><span class="sxs-lookup"><span data-stu-id="657b4-147">The function takes one input parameter, a customer (store) ID, and returns the columns `ProductID`, `Name`, and the aggregate of year-to-date sales as `YTD Total` for each product sold to the store.</span></span>  
  
```  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
  
```  
  
 <span data-ttu-id="657b4-148">次の例では、この関数を呼び出して顧客 ID 602 を指定します。</span><span class="sxs-lookup"><span data-stu-id="657b4-148">The following example invokes the function and specifies customer ID 602.</span></span>  
  
```  
SELECT * FROM Sales.ufn_SalesByStore (602);  
  
```  
  
 <span data-ttu-id="657b4-149">次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースにテーブル値関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="657b4-149">The following example creates a table-valued function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="657b4-150">この関数は、単一の入力パラメーター `EmployeeID` を受け取り、指定された従業員の直接または間接の部下であるすべての従業員の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="657b4-150">The function takes a single input parameter, an `EmployeeID` and returns a list of all the employees who report to the specified employee directly or indirectly.</span></span> <span data-ttu-id="657b4-151">関数が呼び出され、従業員 ID 109 を指定します。</span><span class="sxs-lookup"><span data-stu-id="657b4-151">The function is then invoked specifying employee ID 109.</span></span>  
  
```  
IF OBJECT_ID (N'dbo.ufn_FindReports', N'TF') IS NOT NULL  
    DROP FUNCTION dbo.ufn_FindReports;  
GO  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0 -- Get the initial list of Employees for Manager n  
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1 -- Join recursive member to anchor  
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="657b4-152">参照</span><span class="sxs-lookup"><span data-stu-id="657b4-152">See Also</span></span>  
 <span data-ttu-id="657b4-153">[ユーザー定義関数](user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="657b4-153">[User-Defined Functions](user-defined-functions.md) </span></span>  
 [<span data-ttu-id="657b4-154">CREATE FUNCTION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="657b4-154">CREATE FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-function-transact-sql)  
  
  
