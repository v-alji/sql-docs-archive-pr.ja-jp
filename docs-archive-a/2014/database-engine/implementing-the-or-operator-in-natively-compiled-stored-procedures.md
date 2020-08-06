---
title: ネイティブコンパイルストアドプロシージャでの OR 演算子の実装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2528e74-2b1c-48cb-861b-c4e57b51ac35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ed762e062cbc6831eb46784ef71fc7889850676
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718711"
---
# <a name="implementing-the-or-operator-in-natively-compiled-stored-procedures"></a><span data-ttu-id="64e1e-102">ネイティブ コンパイル ストアド プロシージャでの OR 演算子の実装</span><span class="sxs-lookup"><span data-stu-id="64e1e-102">Implementing the OR Operator in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="64e1e-103">ネイティブ コンパイル ストアド プロシージャ内のクエリ述語では、OR 演算子はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="64e1e-103">OR operators are not supported in query predicates in natively compiled stored procedures.</span></span> <span data-ttu-id="64e1e-104">ネイティブ コンパイル ストアド プロシージャ内のクエリ述語では NOT 演算子もサポートされていないため、同等の論理演算子を単独で使用しても、OR 演算子の効果をシミュレートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="64e1e-104">Because NOT operators are also not supported in query predicates in natively compiled stored procedures, the effects of OR operators cannot be simulated through the use of equivalent logical operators alone.</span></span> <span data-ttu-id="64e1e-105">ただし、OR 演算子の効果は、メモリ最適化テーブル変数を使用してシミュレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="64e1e-105">However, the effects of an OR operator may be simulated with memory-optimized table variables.</span></span>  
  
## <a name="or-operator-in-where-clause"></a><span data-ttu-id="64e1e-106">WHERE 句での OR 演算子</span><span class="sxs-lookup"><span data-stu-id="64e1e-106">OR Operator in WHERE Clause</span></span>  
 <span data-ttu-id="64e1e-107">WHERE 句に OR 演算子が含まれている場合は、次の方法で動作をシミュレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="64e1e-107">If you have an OR operator in a WHERE clause, you can use the following approach to simulate its behavior:</span></span>  
  
1.  <span data-ttu-id="64e1e-108">適切なスキーマを使用して、メモリ最適化テーブル変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-108">Create a memory-optimized table variable with the appropriate schema.</span></span> <span data-ttu-id="64e1e-109">これには、定義済みのメモリ最適化テーブル型が必要になります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-109">This requires a predefined memory-optimized table type.</span></span>  
  
2.  <span data-ttu-id="64e1e-110">OR 演算子によって結合されている述語に従って WHERE 句を 2 つに分割します (最上位レベルの OR 演算子からこの手順を行います)。</span><span class="sxs-lookup"><span data-stu-id="64e1e-110">Starting with the top level OR operator, separate the WHERE clause into two parts according to the predicates joined by the OR operator.</span></span> <span data-ttu-id="64e1e-111">WHERE 句に複数の OR 演算子が含まれている場合は、この手順を複数回行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-111">If you have more than one OR operator in a WHERE clause, you may need to do this more than once.</span></span> <span data-ttu-id="64e1e-112">最後の OR 演算子まで、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-112">Repeat this step until no OR operators remain.</span></span> <span data-ttu-id="64e1e-113">たとえば、次のような述語があるとします。</span><span class="sxs-lookup"><span data-stu-id="64e1e-113">For example, if you have the following predicate:</span></span>  
  
    ```  
    pred1 OR (pred2 AND (pred3 OR pred4)) OR (pred5 AND pred6)  
    ```  
  
     <span data-ttu-id="64e1e-114">この手順を行うと、次のような述語に分割されます。</span><span class="sxs-lookup"><span data-stu-id="64e1e-114">After this step, you should have the following predicates:</span></span>  
  
    ```  
    pred1  
    pred5 AND pred6  
    pred2 AND pred3  
    pred2 AND pred4  
    ```  
  
3.  <span data-ttu-id="64e1e-115">手順 2. で分割された 2 つの部分で構成される各ペアを述語としてを使用しクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-115">Execute a query with each of the two parts found in Step 2 as the predicate.</span></span> <span data-ttu-id="64e1e-116">手順 1. で作成したメモリ最適化テーブル変数に各クエリの結果を挿入します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-116">Insert the result for each query into the memory-optimized table variable created in Step 1.</span></span>  
  
4.  <span data-ttu-id="64e1e-117">必要に応じて、メモリ最適化テーブル変数から重複する結果を削除します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-117">If necessary, remove duplicates from the memory-optimized table variable.</span></span>  
  
5.  <span data-ttu-id="64e1e-118">メモリ最適化テーブル変数の内容をクエリの結果として使用します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-118">Use the content of the memory-optimized table variable as the result from the query.</span></span>  
  
 <span data-ttu-id="64e1e-119">次の例では、[!INCLUDE[hek_2](../includes/hek-2-md.md)] 用に更新された AdventureWorks2012 データベースのテーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-119">The following sample uses tables from the AdventureWorks2012 database that were updated for [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="64e1e-120">このサンプルのファイルをダウンロードするには、 [AdventureWorks Databases-2012、2008R2、および 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587)に移動します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-120">To download the files for this sample, goto [AdventureWorks Databases - 2012, 2008R2 and 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587).</span></span> <span data-ttu-id="64e1e-121">AdventureWorks2012 にコードサンプルを適用するには [!INCLUDE[hek_2](../includes/hek-2-md.md)] 、 [SQL Server 2014 のインメモリ OLTP サンプル](https://msftdbprodsamples.codeplex.com/releases/view/114491)にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="64e1e-121">To apply [!INCLUDE[hek_2](../includes/hek-2-md.md)] code sample to AdventureWorks2012, go to [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="64e1e-122">データベースに、次のストアド プロシージャを追加します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-122">Add the following stored procedure to the database.</span></span> <span data-ttu-id="64e1e-123">ここでは、ネイティブ コンパイルを使用するように、このストアド プロシージャを変換します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-123">We will convert this stored procedure to use native compilation.</span></span>  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_ondisk  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
AS BEGIN  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  WHERE  s.SalesOrderId = @SalesOrderId  
      OR s.SalesOrderDetailId = @SalesOrderDetailId  
      OR s.CarrierTrackingNumber = @CarrierTrackingNumber  
      OR s.ProductID = @ProductId  
      OR (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
END  
GO  
```  
  
 <span data-ttu-id="64e1e-124">変換後のテーブルとストアド プロシージャのスキーマは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-124">After conversion, the table and stored procedure schema is as follows,</span></span>  
  
```  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesOrderDetailType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailTempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  recordcount int not null  
  INDEX ix_fuzzySearchSalesOrderDetailTempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_inmem  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.fuzzySearchSalesOrderDetailType  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderId = @SalesOrderId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderDetailId = @SalesOrderDetailId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.CarrierTrackingNumber COLLATE Latin1_General_BIN2 = @CarrierTrackingNumber COLLATE Latin1_General_BIN2   
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.ProductID = @ProductId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
  
  -- After the above statements, there will be duplicates inside @retValue  
  -- Delete the duplicates from @retValue  
  DECLARE @duplicates Sales.fuzzySearchSalesOrderDetailTempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, recordcount)   
  SELECT SalesOrderId, SalesOrderDetailId, COUNT(*) AS recordCount  
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId  
  
  -- Now we have one row per pair  
  -- clear and rebuild the result set  
  DELETE FROM @retValue  
  
  INSERT INTO @retValue  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates d ON s.SalesOrderId = d.SalesOrderId AND s.SalesOrderDetailId = d.SalesOrderDetailId  
  
  -- After this every pair of (SalesOrderId, SalesOrderDetailId) in @retValue should be unique.  
  SELECT SalesorderId, SalesOrderDetailId, ModifiedDate FROM @retValue  
END  
GO  
```  
  
## <a name="or-operator-in-join-condition"></a><span data-ttu-id="64e1e-125">結合 (JOIN) 条件での OR 演算子</span><span class="sxs-lookup"><span data-stu-id="64e1e-125">OR Operator in JOIN Condition</span></span>  
 <span data-ttu-id="64e1e-126">SELECT ステートメントの JOIN 条件に OR 演算子が含まれている場合は、次の方法で動作をシミュレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="64e1e-126">If you have an OR operator in a JOIN condition of a SELECT statement, you may use the following approach to simulate its behavior.</span></span> <span data-ttu-id="64e1e-127">JOIN 条件に複数の OR 演算子が含まれている場合、または OR 演算子を使用した JOIN 条件が複数ある場合は、この手順を複数回行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-127">If you have more than one OR operator in a JOIN condition or you have multiple JOIN condition with OR operators, you may need to do this more than once.</span></span>  
  
 <span data-ttu-id="64e1e-128">OUTER JOIN 条件がある場合は、ここで示す回避策と OUTER JOIN 条件用の回避策を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="64e1e-128">If you have OUTER JOIN conditions, you may combine this workaround with the workaround for OUTER JOIN conditions.</span></span>  
  
1.  <span data-ttu-id="64e1e-129">適切なスキーマを使用して、メモリ最適化テーブル変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-129">Create a memory-optimized table variable with the appropriate schema.</span></span> <span data-ttu-id="64e1e-130">これには、定義済みのメモリ最適化テーブル型が必要になります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-130">This requires a predefined memory-optimized table type.</span></span>  
  
2.  <span data-ttu-id="64e1e-131">OR 演算子によって結合されている述語に従って、JOIN 条件内の述語を 2 つに分割します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-131">Separate the predicate in the JOIN condition into two parts according to the predicates joined by the OR operator.</span></span> <span data-ttu-id="64e1e-132">複数の JOIN 条件がある場合は、各 JOIN 条件に対してこの手順を行い、結果のフラグメントの組み合わせを作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-132">If you have multiple JOIN conditions, you may need to do this for each JOIN condition and then create a set of combinations of the resulting fragments.</span></span> <span data-ttu-id="64e1e-133">たとえば、3 つの JOIN 条件があり、各 JOIN 条件には 1 つの OR 演算子が含まれている場合は、8 個 (2x2x2) の述語を作成できます。</span><span class="sxs-lookup"><span data-stu-id="64e1e-133">For example, if you have three JOIN conditions with one OR operator in each JOIN condition, you may have 2x2x2=8 predicates.</span></span>  
  
3.  <span data-ttu-id="64e1e-134">手順 2. で作成された各述語に対して、手順 1. で作成したメモリ最適化テーブル変数に結果を挿入するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-134">For each predicate produced by Step 2, create a query that will insert its result into the memory-optimized table variable created in Step 1.</span></span>  
  
4.  <span data-ttu-id="64e1e-135">必要に応じて、メモリ最適化テーブル変数から重複する結果を削除します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-135">If necessary, remove duplicates from the memory-optimized table variable.</span></span>  
  
5.  <span data-ttu-id="64e1e-136">メモリ最適化テーブル変数の内容をクエリの結果として使用します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-136">Use the content of the memory-optimized table variable as the result from the query.</span></span>  
  
 <span data-ttu-id="64e1e-137">次の例では、[!INCLUDE[hek_2](../includes/hek-2-md.md)] 用に更新された AdventureWorks2012 データベースのテーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-137">The following sample uses tables from the AdventureWorks2012 database that were updated for [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="64e1e-138">このサンプルのファイルをダウンロードするには、 [AdventureWorks Databases-2012、2008R2、および 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587)に移動します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-138">To download the files for this sample, goto [AdventureWorks Databases - 2012, 2008R2 and 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587).</span></span> <span data-ttu-id="64e1e-139">AdventureWorks2012 にコードサンプルを適用するには [!INCLUDE[hek_2](../includes/hek-2-md.md)] 、 [SQL Server 2014 のインメモリ OLTP サンプル](https://msftdbprodsamples.codeplex.com/releases/view/114491)にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="64e1e-139">To apply [!INCLUDE[hek_2](../includes/hek-2-md.md)] code sample to AdventureWorks2012, go to [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="64e1e-140">データベースに、次のストアド プロシージャを追加します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-140">Add the following stored procedure to the database.</span></span> <span data-ttu-id="64e1e-141">ここでは、ネイティブ コンパイルを使用するように、このストアド プロシージャを変換します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-141">We will convert this stored procedure to use native compilation.</span></span> <span data-ttu-id="64e1e-142">この例では、INNER JOIN 条件を使用します。</span><span class="sxs-lookup"><span data-stu-id="64e1e-142">This sample uses INNER JOIN conditions.</span></span>  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_ondisk  
  @SpecialOfferId int  
AS BEGIN  
  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  JOIN Sales.SpecialOffer_onDisk offer   
    ON s.SpecialOfferID = offer.SpecialOfferID   
    OR s.ProductID IN (SELECT ProductId FROM Sales.SpecialOfferProduct sop WHERE sop.SpecialOfferID = @SpecialOfferId)  
END  
```  
  
 <span data-ttu-id="64e1e-143">変換後のテーブルとストアド プロシージャのスキーマは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-143">After conversion, the table and stored procedure schema is as follows,</span></span>  
  
```  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_Type AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesSpecialOffers_Type NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_TempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  recordcount int null  
  INDEX ix_fuzzySearchSalesSpecialOffers_TempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_inmem  
  @SpecialOfferId int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.FuzzySearchSalesSpecialOffers_Type  
  
  -- Find all special offers matching the conditions  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOffer_inmem offer   
    ON s.SpecialOfferID = offer.SpecialOfferID  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOfferProduct_inmem sop   
    ON sop.SpecialOfferId = @SpecialOfferId AND s.ProductID = sop.ProductId  
  
  -- Now we need to remove the duplicates from @matchingSpecialOffers  
  DECLARE @duplicates Sales.fuzzySearchSalesSpecialOffers_TempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, SpecialOfferid, recordcount)  
  SELECT SalesOrderId, SalesOrderDetailId, SpecialOfferId, COUNT(*)   
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId, SpecialOfferId  
  
  -- now there should be no duplicates within @duplicate  
  -- use @duplicate for join.  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates offer   
    ON    s.SalesOrderId = offer.SalesOrderId   
      AND s.SalesOrderDetailId = offer.SalesOrderDetailID   
      AND s.SpecialOfferId = offer.SpecialOfferId  
END  
GO  
```  
  
## <a name="side-effects"></a><span data-ttu-id="64e1e-144">副作用</span><span class="sxs-lookup"><span data-stu-id="64e1e-144">Side Effects</span></span>  
 <span data-ttu-id="64e1e-145">WHERE 句や JOIN 条件に複数の OR 演算子が含まれている場合は、動作をシミュレートするために実行する必要があるクエリの数は、指数関数的に増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-145">If you have more than one OR operator in the WHERE clause or JOIN condition, the number of queries you need to execute to simulate the behavior may increase exponentially.</span></span> <span data-ttu-id="64e1e-146">その結果、メモリ最適化テーブル変数の使用が原因で、クエリのパフォーマンスが低下し、メモリの使用量が増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64e1e-146">This may slow down query performance and may increase memory usage due to the need to use memory-optimized table variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e1e-147">参照</span><span class="sxs-lookup"><span data-stu-id="64e1e-147">See Also</span></span>  
 [<span data-ttu-id="64e1e-148">ネイティブ コンパイル ストアド プロシージャの移行に関する問題</span><span class="sxs-lookup"><span data-stu-id="64e1e-148">Migration Issues for Natively Compiled Stored Procedures</span></span>](../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
  
