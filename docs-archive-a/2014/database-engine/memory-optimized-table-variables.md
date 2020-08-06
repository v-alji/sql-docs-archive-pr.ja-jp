---
title: メモリ最適化テーブル変数 |Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: bd102e95-53e2-4da6-9b8b-0e4f02d286d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: bec720c53c257240ee92274a6391ebc3f17faa25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641842"
---
# <a name="memory-optimized-table-variables"></a><span data-ttu-id="eae44-102">メモリ最適化テーブル変数</span><span class="sxs-lookup"><span data-stu-id="eae44-102">Memory-Optimized Table Variables</span></span>
  <span data-ttu-id="eae44-103">メモリ最適化テーブル (効率的なデータ アクセスのため) とネイティブ コンパイル ストアド プロシージャ (効率的なクエリ処理とビジネス ロジックの実行のため) に加えて、[!INCLUDE[hek_2](../includes/hek-2-md.md)] では、3 つ目のオブジェクトの種類としてメモリ最適化テーブル型が導入されます。</span><span class="sxs-lookup"><span data-stu-id="eae44-103">In addition to memory-optimized tables (for efficient data access) and natively compiled stored procedures (for efficient query processing and business logic execution) [!INCLUDE[hek_2](../includes/hek-2-md.md)] introduces a third kind of object: the memory-optimized table type.</span></span> <span data-ttu-id="eae44-104">メモリ最適化テーブル型を使用して作成されたテーブル変数は、メモリ最適化テーブル変数です。</span><span class="sxs-lookup"><span data-stu-id="eae44-104">A table variable created using a memory-optimized table type is a memory-optimized table variable.</span></span>  
  
 <span data-ttu-id="eae44-105">メモリ最適化テーブル変数には、ディスク ベース テーブル変数と比べて次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="eae44-105">Memory-optimized table variables offer the following advantages when compared to disk-based table variables:</span></span>  
  
-   <span data-ttu-id="eae44-106">変数はメモリにしか格納されません。</span><span class="sxs-lookup"><span data-stu-id="eae44-106">The variables are only stored in memory.</span></span> <span data-ttu-id="eae44-107">メモリ最適化テーブル型では、メモリ最適化テーブルで使用されるものと同じメモリ最適化アルゴリズムとデータ構造が使用されるため、データ アクセスがさらに効率的になります。特に、変数をネイティブ コンパイル ストアド プロシージャで使用するときに効率的です。</span><span class="sxs-lookup"><span data-stu-id="eae44-107">Data access is more efficient because memory-optimized table type use the same memory-optimized algorithm and data structures used for memory-optimized tables, especially when the variables are used in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="eae44-108">メモリ最適化テーブル変数を使用する場合、tempdb は使用しません。</span><span class="sxs-lookup"><span data-stu-id="eae44-108">With memory-optimized table variables, there is no tempdb utilization.</span></span> <span data-ttu-id="eae44-109">テーブル変数は tempdb に保存されず、tempdb 内のリソースを使用しません。</span><span class="sxs-lookup"><span data-stu-id="eae44-109">Table variables are not stored in tempdb and do not use any resources in tempdb.</span></span>  
  
 <span data-ttu-id="eae44-110">メモリ最適化テーブル変数の一般的な使用シナリオは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eae44-110">The typical usage scenarios for memory-optimized table variables are:</span></span>  
  
-   <span data-ttu-id="eae44-111">中間結果を保存し、ネイティブ コンパイル ストアド プロシージャの複数のクエリに基づいて単一の結果セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="eae44-111">Storing intermediate results and creating single result sets based on multiple queries in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="eae44-112">ネイティブ コンパイル ストアド プロシージャおよびインタープリターで処理されるストアド プロシージャに、テーブル値パラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="eae44-112">Passing table-valued parameters into natively compiled stored procedures and interpreted stored procedures.</span></span>  
  
-   <span data-ttu-id="eae44-113">ディスク ベース テーブル変数を置き換え、場合によっては、ストアド プロシージャに対してローカルな #temp テーブルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="eae44-113">Replacing disk-based table variables, and in some cases #temp tables that are local to a stored procedure.</span></span> <span data-ttu-id="eae44-114">これは、システムに多くの tempdb の競合がある場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="eae44-114">This is particularly useful if there is a lot of tempdb contention in the system.</span></span>  
  
-   <span data-ttu-id="eae44-115">テーブル変数を使用して、ネイティブ コンパイル ストアド プロシージャのカーソルをシミュレートすることができ、その結果、ネイティブ コンパイル ストアド プロシージャの対象領域の制限を回避できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eae44-115">Table variables can be used to simulate cursors in natively compiled stored procedures, which can help you work around surface area limitations in natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="eae44-116">メモリ最適化テーブルと同様に、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によってメモリ最適化テーブル型ごとに DLL が生成されます</span><span class="sxs-lookup"><span data-stu-id="eae44-116">Like memory-optimized tables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] generates a DLL for each memory-optimized table type.</span></span> <span data-ttu-id="eae44-117">(メモリ最適化テーブル変数の作成に使用されるときではなく、メモリ最適化テーブル型が作成されるときにコンパイルが呼び出されます)。この DLL には、インデックスにアクセスし、テーブル変数からデータを取得するための関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="eae44-117">(Compilation is invoked when the memory-optimized table type is created and not when used to create memory-optimized table variables.) This DLL includes the functions for accessing indexes and retrieving data from the table variables.</span></span> <span data-ttu-id="eae44-118">メモリ最適化テーブル変数がテーブル型に基づいて宣言されると、テーブルとテーブル型に対応するインデックス構造のインスタンスがユーザー セッションで作成されます。</span><span class="sxs-lookup"><span data-stu-id="eae44-118">When a memory-optimized table variable is declared based on the table type, an instance of the table and index structures corresponding to the table type is created in the user session.</span></span> <span data-ttu-id="eae44-119">その後、テーブル変数をディスク ベース テーブル変数と同じ方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="eae44-119">The table variable can then be used in the same way as disk-based table variables.</span></span> <span data-ttu-id="eae44-120">テーブル変数の行を挿入、更新、および削除でき、 [!INCLUDE[tsql](../includes/tsql-md.md)] クエリで変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="eae44-120">You can insert, update, and delete rows in the table variable, and you can use the variables in [!INCLUDE[tsql](../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="eae44-121">また、ネイティブ コンパイル ストアド プロシージャと、インタープリターによって処理されるストアド プロシージャに、テーブル値パラメーター (TVP) として変数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="eae44-121">You can also pass the variables into natively compiled and interpreted stored procedures, as table-valued parameters (TVP).</span></span>  
  
 <span data-ttu-id="eae44-122">次のサンプルでは、AdventureWorks ベースのインメモリ OLTP サンプルのメモリ最適化テーブル型を示します ([SQL Server 2014 インメモリ Oltp サンプル](https://msftdbprodsamples.codeplex.com/releases/view/114491))。</span><span class="sxs-lookup"><span data-stu-id="eae44-122">The following sample shows a memory-optimized table type from the AdventureWorks-based In-Memory OLTP sample ([SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491)).</span></span>  
  
```sql
CREATE TYPE Sales.SalesOrderDetailType_inmem
   AS TABLE
(
   OrderQty         smallint   NOT NULL,
   ProductID        int        NOT NULL,

   SpecialOfferID   int        NOT NULL
      INDEX  IX_SpecialOfferID  NONCLUSTERED,

   LocalID          int        NOT NULL,

   INDEX IX_ProductID HASH (ProductID)
      WITH ( BUCKET_COUNT = 8 )
)
WITH ( MEMORY_OPTIMIZED = ON );
```  
  
 <span data-ttu-id="eae44-123">このサンプルは、メモリ最適化テーブル型の構文がディスク ベース テーブル型に類似していることを示しています。ただし、次の例外を除きます。</span><span class="sxs-lookup"><span data-stu-id="eae44-123">The sample shows that the syntax of memory-optimized table types is similar to disk-based table types, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="eae44-124">`MEMORY_OPTIMIZED=ON` は、テーブル型がメモリ最適化であることを示します。</span><span class="sxs-lookup"><span data-stu-id="eae44-124">`MEMORY_OPTIMIZED=ON` indicates that the table type is memory-optimized.</span></span>  
  
-   <span data-ttu-id="eae44-125">型には少なくとも 1 つのインデックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="eae44-125">The type must have at least one index.</span></span> <span data-ttu-id="eae44-126">メモリ最適化テーブルの場合と同様に、ハッシュ インデックスと非クラスター化インデックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="eae44-126">As with memory-optimized tables, you can use hash and nonclustered indexes.</span></span>  
  
     <span data-ttu-id="eae44-127">ハッシュ インデックスの場合、バケット数は予想される一意のキーの数からその 2 倍の数ぐらいまでの範囲にしてください。</span><span class="sxs-lookup"><span data-stu-id="eae44-127">For a hash index, the bucket count should be about one to two times the number of expected unique index keys.</span></span> <span data-ttu-id="eae44-128">詳細については、「 [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eae44-128">For more information, see [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="eae44-129">メモリ最適化テーブルのデータ型および制約の制限は、メモリ最適化テーブル型にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="eae44-129">The data type and constraint restrictions on memory-optimized tables also apply to memory-optimized table types.</span></span> <span data-ttu-id="eae44-130">たとえば、[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] では既定の制約はサポートされますが、CHECK 制約はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="eae44-130">For example, in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] default constraints are supported, but check constraints are not.</span></span>  
  
 <span data-ttu-id="eae44-131">メモリ最適化テーブルと同様に、メモリ最適化テーブル変数には次のことが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="eae44-131">Like memory-optimized tables, memory-optimized table variables,</span></span>  
  
-   <span data-ttu-id="eae44-132">並列プランはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="eae44-132">Do not support parallel plans.</span></span>  
  
-   <span data-ttu-id="eae44-133">メモリに収まる必要があるため、ディスク リソースを使用しません。</span><span class="sxs-lookup"><span data-stu-id="eae44-133">Must fit in memory and do not use disk resources.</span></span>  
  
 <span data-ttu-id="eae44-134">ディスク ベース テーブル変数は tempdb 内に存在します。</span><span class="sxs-lookup"><span data-stu-id="eae44-134">Disk-based table variables exist in tempdb.</span></span> <span data-ttu-id="eae44-135">メモリ最適化テーブル変数は、ユーザー データベース内に存在します (ただし、ストレージを消費せず、復旧もされません)。</span><span class="sxs-lookup"><span data-stu-id="eae44-135">Memory-optimized table variables exist in the user database (but they do not consume storage and are not recovered).</span></span>  
  
 <span data-ttu-id="eae44-136">インライン構文を使用して、メモリ最適化テーブル変数を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="eae44-136">You cannot create a memory-optimized table variable using in-line syntax.</span></span> <span data-ttu-id="eae44-137">ディスク ベース テーブル変数とは異なり、最初に型を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eae44-137">Unlike disk-based table variables, you must create a type first.</span></span>  
  
## <a name="table-valued-parameters"></a><span data-ttu-id="eae44-138">テーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="eae44-138">Table-Valued Parameters</span></span>  
 <span data-ttu-id="eae44-139">次のサンプル スクリプトでは、メモリ最適化テーブル型 `Sales.SalesOrderDetailType_inmem` としてテーブル変数を宣言し、変数に 3 つの行を挿入し、変数を TVP として `Sales.usp_InsertSalesOrder_inmem` に渡します。</span><span class="sxs-lookup"><span data-stu-id="eae44-139">The following sample script shows the declaration of a table variable as the memory-optimized table type `Sales.SalesOrderDetailType_inmem`, the insert of three rows into the variable, and passing the variable as a TVP into `Sales.usp_InsertSalesOrder_inmem`.</span></span>  
  
```sql  
DECLARE @od Sales.SalesOrderDetailType_inmem,  
  @SalesOrderID uniqueidentifier,  
  @DueDate datetime2 = SYSDATETIME()  
  
INSERT @od (LocalID, ProductID, OrderQty, SpecialOfferID) VALUES  
  (1, 888, 2, 1),  
  (2, 450, 13, 1),  
  (3, 841, 1, 1)  
  
EXEC Sales.usp_InsertSalesOrder_inmem  
  @SalesOrderID = @SalesOrderID,  
  @DueDate = @DueDate,  
 @OnlineOrderFlag = 1,  
  @SalesOrderDetails = @od  
```  
  
 <span data-ttu-id="eae44-140">メモリ最適化テーブル型は、ストアド プロシージャのテーブル値パラメーター (TVP) の型として使用でき、ディスク ベース テーブル型および TVP とまったく同じようにクライアントから参照できます。</span><span class="sxs-lookup"><span data-stu-id="eae44-140">Memory-optimized table types can be used as the type for stored procedure table-valued parameters (TVPs) and can be referenced by clients exactly the same as disk-based table types and TVPs.</span></span> <span data-ttu-id="eae44-141">したがって、メモリ最適化 TVP が含まれるストアド プロシージャ、およびネイティブ コンパイル ストアド プロシージャの呼び出しは、ディスク ベース TVP が含まれる、インタープリターによって解釈されるストアド プロシージャの呼び出しとまったく同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="eae44-141">Therefore, the invocation of stored procedures with memory-optimized TVPs, and natively compiled stored procedures works exactly the same as the invocation of interpreted stored procedures with disk-based TVPs.</span></span>  
  
## <a name="temp-table-replacement"></a><span data-ttu-id="eae44-142">#temp テーブルの置換</span><span class="sxs-lookup"><span data-stu-id="eae44-142">#temp Table Replacement</span></span>  
 <span data-ttu-id="eae44-143">次のサンプルは、ストアド プロシージャに対してローカルな #temp のテーブルの代わりとしてのメモリ最適化テーブル型およびテーブル変数を示しています。</span><span class="sxs-lookup"><span data-stu-id="eae44-143">The following sample shows memory-optimized table types and table variables as a replacement for #temp tables that are local to a stored procedure.</span></span>  
  
```sql  
-- Using SQL procedure and temp table  
CREATE TABLE #tempTable (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
  
CREATE PROCEDURE sqlProc  
AS  
BEGIN  
  TRUNCATE TABLE #tempTable  
  
  INSERT #tempTable VALUES (1)  
  INSERT #tempTable VALUES (2)  
  INSERT #tempTable VALUES (3)  
  SELECT * FROM #tempTable  
END  
GO  
  
-- Using natively compiled stored procedure and table variable  
CREATE TYPE TT AS TABLE (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
GO  
  
CREATE PROCEDURE NCSPProc  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @tableVariable TT  
  INSERT @tableVariable VALUES (1)  
  INSERT @tableVariable VALUES (2)  
  INSERT @tableVariable VALUES (3)  
  SELECT c FROM @tableVariable  
END  
GO  
```  
  
## <a name="creating-a-single-result-set"></a><span data-ttu-id="eae44-144">単一結果セットの作成</span><span class="sxs-lookup"><span data-stu-id="eae44-144">Creating a Single Result Set</span></span>  
 <span data-ttu-id="eae44-145">次のサンプルでは、中間結果を保存し、ネイティブ コンパイル ストアド プロシージャの複数のクエリに基づいて単一の結果セットを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eae44-145">The following sample shows how to store intermediate results and create single result sets based on multiple queries in natively compiled stored procedures.</span></span> <span data-ttu-id="eae44-146">ここでは、UNION 演算子を使用した `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2` を計算しています。</span><span class="sxs-lookup"><span data-stu-id="eae44-146">The sample is computing the union `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`.</span></span>  
  
```sql  
CREATE DATABASE hk  
GO  
ALTER DATABASE hk ADD FILEGROUP hk_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE hk ADD FILE( NAME = 'hk_mod' , FILENAME = 'c:\data\hk_mod') TO FILEGROUP hk_mod;  
  
USE hk  
GO  
  
CREATE TYPE tab1 AS TABLE (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON)  
  
CREATE TABLE dbo.t1 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
CREATE TABLE dbo.t2 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
  
INSERT INTO dbo.t1 VALUES (1), (2)  
INSERT INTO dbo.t2 VALUES (3), (4)  
GO  
  
CREATE PROCEDURE dbo.p1  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS  
  BEGIN ATOMIC WITH ( TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english' )  
  
    DECLARE @t dbo.tab1  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t1;  
  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t2;  
  
    SELECT c1 FROM @t;  
  END  
GO  
  
EXEC dbo.p1  
GO  
```  
  
## <a name="memory-consumption-for-table-variables"></a><span data-ttu-id="eae44-147">テーブル変数によるメモリ消費</span><span class="sxs-lookup"><span data-stu-id="eae44-147">Memory Consumption for Table Variables</span></span>  
 <span data-ttu-id="eae44-148">テーブル変数によるメモリ消費は、非クラスター化インデックスを除き、メモリ最適化テーブルに似ています。</span><span class="sxs-lookup"><span data-stu-id="eae44-148">Memory consumption for table variables is similar to memory-optimized tables, with the exception of nonclustered indexes.</span></span> <span data-ttu-id="eae44-149">非クラスター化インデックスを使用してメモリ最適化テーブル変数に多数の行を挿入する場合に、インデックス キーが大きいと、これらのテーブル変数では過剰な量のメモリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="eae44-149">If you insert a lot of rows into memory-optimized table variables with nonclustered indexes and if the index keys are large, these table variables will use a disproportionate amount of memory.</span></span> <span data-ttu-id="eae44-150">大きなテーブル変数を対象とする非クラスター化インデックスは、非クラスター化インデックス テーブルが同じ数の行を挿入する場合に比べて多くのメモリ (インデックス ページ内のより多くメモリ) を必要とします。</span><span class="sxs-lookup"><span data-stu-id="eae44-150">Nonclustered indexes on large table variables require proportionately more memory than a nonclustered index would require for the same number of rows inserted into a table (more memory in the index pages).</span></span>  
  
 <span data-ttu-id="eae44-151">テーブル変数のメモリは、データベースのリソース ガバナー リソース プールから取得されます。</span><span class="sxs-lookup"><span data-stu-id="eae44-151">Memory for table variables comes from the database's Resource Governor resource pool.</span></span>  
  
 <span data-ttu-id="eae44-152">メモリ最適化テーブルとは異なり、テーブル変数によって消費された (削除された行を含む) メモリは、テーブル変数がスコープ外になると解放されます。</span><span class="sxs-lookup"><span data-stu-id="eae44-152">Unlike memory-optimized tables, the memory consumed (including deleted rows) by table variables is freed when the table variable goes out of scope.</span></span>  
  
 <span data-ttu-id="eae44-153">メモリは、データベースの単一 PGPOOL メモリ コンシューマーの一部として説明されます。</span><span class="sxs-lookup"><span data-stu-id="eae44-153">Memory is accounted for as part of the single PGPOOL memory consumer of the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae44-154">参照</span><span class="sxs-lookup"><span data-stu-id="eae44-154">See Also</span></span>  
 [<span data-ttu-id="eae44-155">Transact-SQL によるインメモリ OLTP のサポート</span><span class="sxs-lookup"><span data-stu-id="eae44-155">Transact-SQL Support for In-Memory OLTP</span></span>](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
