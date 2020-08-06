---
title: '実証: インメモリ OLTP によるパフォーマンスの向上 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c6def45d-d2d4-4d24-8068-fab4cd94d8cc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4858e4c35263ab3dd1d9fdcf55a2b136dd8eeaf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640943"
---
# <a name="demonstration-performance-improvement-of-in-memory-oltp"></a><span data-ttu-id="7a5d7-102">実証: インメモリ OLTP によるパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="7a5d7-102">Demonstration: Performance Improvement of In-Memory OLTP</span></span>
  <span data-ttu-id="7a5d7-103">この例では、インメモリ OLTP を使用した場合のパフォーマンスの向上を取り上げます。メモリ最適化テーブルと従来のディスク ベースのテーブルとに対してまったく同じ Transact-SQL クエリを実行したときの応答時間の違いを比較します。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-103">This example shows performance improvements when using In-Memory OLTP by comparing differences in response times when running an identical Transact-SQL query against memory-optimized and traditional disk-based tables.</span></span> <span data-ttu-id="7a5d7-104">応答時間は一般に、ネイティブ コンパイル ストアド プロシージャでメモリ最適化テーブルを照会したときに最短となります。そこで、ネイティブにコンパイルされたストアド プロシージャも (同じクエリに基づいて) 作成、実行して、その点を実証することにします。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-104">Additionally, a natively-compiled stored procedure is also created (based on the same query) and then run to demonstrate that you typically get the best response times when querying a memory-optimized table with a natively-compiled stored procedure.</span></span> <span data-ttu-id="7a5d7-105">このサンプルを通じて証明されるのは、メモリ最適化テーブルのデータにアクセスしたときに得られるパフォーマンス向上の一面 (挿入操作時のデータ アクセス効率) だけです。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-105">This sample only shows one aspect of performance improvements when accessing data in memory-optimized tables; data access efficiency when performing inserts.</span></span> <span data-ttu-id="7a5d7-106">このサンプルはシングル スレッドで、インメモリ OLTP のコンカレンシーの利点を利用していません。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-106">This sample is single-threaded and does not take advantage of the concurrency benefits of In-Memory OLTP.</span></span> <span data-ttu-id="7a5d7-107">コンカレンシーを使用するワークロードでは、さらにパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-107">A workload that uses concurrency will see a greater performance gain.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a5d7-108">メモリ最適化テーブルをデモンストレーションするもう1つの例については[、SQL Server 2014 のインメモリ OLTP サンプル](https://msftdbprodsamples.codeplex.com/releases/view/114491)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-108">Another sample demonstrating memory-optimized tables is available at [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="7a5d7-109">このサンプルを実行するために、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-109">To complete this sample you will perform the following:</span></span>  
  
1.  <span data-ttu-id="7a5d7-110">**Imoltp**という名前のデータベースを作成し、そのファイルの詳細を変更してインメモリ OLTP を使用するように設定します。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-110">Create a database named **imoltp** and alter its file details to set it up for using In-Memory OLTP.</span></span>  
  
2.  <span data-ttu-id="7a5d7-111">サンプルに必要なデータベース オブジェクトとして、3 つのテーブルと 1 つのネイティブ コンパイル ストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-111">Create the database objects for our sample: three tables and a natively-compiled stored procedure.</span></span>  
  
3.  <span data-ttu-id="7a5d7-112">各種のクエリを実行して、クエリごとの応答時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-112">Run the different queries and display the response times for each query.</span></span>  
  
 <span data-ttu-id="7a5d7-113">この例で**imoltp**データベースを設定するには、最初に空のフォルダー **c:\ imoltp_data**を作成し、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-113">To setup the **imoltp** database for our example, first create an empty folder: **c:\imoltp_data**, and then run the following code:</span></span>  
  
```sql  
USE master  
GO  
  
-- Create a new database.  
CREATE DATABASE imoltp  
GO  
  
-- Prepare the database for In-Memory OLTP by  
-- adding a memory-optimized filegroup to the database.  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_file_group  
    CONTAINS MEMORY_OPTIMIZED_DATA;  
  
-- Add a file (to hold the memory-optimized data) to the new filegroup.  
ALTER DATABASE imoltp ADD FILE (name='imoltp_file', filename='c:\imoltp_data\imoltp_file')  
    TO FILEGROUP imoltp_file_group;  
GO  
  
```  
  
 <span data-ttu-id="7a5d7-114">次に、各種のデータ アクセス手法をデモンストレーションする目的で使用するディスク ベースのテーブルと 2 つのメモリ最適化テーブル、ネイティブ コンパイル ストアド プロシージャを、以下のコードを実行して作成します。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-114">Next, run the following code to create the disk-based table, two (2) memory-optimized tables, and the natively-compiled stored procedure that will be used to demonstrate the different data access methods:</span></span>  
  
```sql  
USE imoltp  
GO  
  
-- If the tables or stored procedure already exist, drop them to start clean.  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'DiskBasedTable')  
   DROP TABLE [dbo].[DiskBasedTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'InMemTable')  
   DROP TABLE [dbo].[InMemTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'InMemTable2')  
   DROP TABLE [dbo].[InMemTable2]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'usp_InsertData')  
   DROP PROCEDURE [dbo].[usp_InsertData]  
GO  
  
-- Create a traditional disk-based table.  
CREATE TABLE [dbo].[DiskBasedTable] (  
  c1 INT NOT NULL PRIMARY KEY,  
  c2 NCHAR(48) NOT NULL  
)  
GO  
  
-- Create a memory-optimized table.  
CREATE TABLE [dbo].[InMemTable] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a 2nd memory-optimized table.  
CREATE TABLE [dbo].[InMemTable2] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a natively-compiled stored procedure.  
CREATE PROCEDURE [dbo].[usp_InsertData]   
  @rowcount INT,  
  @c NCHAR(48)  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS   
  BEGIN ATOMIC   
  WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @i INT = 1;  
  WHILE @i <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[inMemTable2](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
END  
GO  
  
```  
  
 <span data-ttu-id="7a5d7-115">これでセットアップは完了です。クエリを実行する準備が整いました。クエリで応答時間を表示し、データ アクセス手法ごとのパフォーマンスを比較することができます。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-115">The setup is complete and we are ready to execute the queries that will display the response times comparing the performance between the data access methods.</span></span>  
  
 <span data-ttu-id="7a5d7-116">この例の目的上、次のコードを複数回実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-116">To complete the example run the following code multiple times.</span></span> <span data-ttu-id="7a5d7-117">初回実行時の結果は、初期メモリ割り当てによるマイナスの影響を含んでいるため、無視してください。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-117">Ignore the results from the first run which is negatively affected by initial memory allocation.</span></span>  
  
```sql  
SET STATISTICS TIME OFF;  
SET NOCOUNT ON;  
  
-- Delete data from all tables to reset the example.  
DELETE FROM [dbo].[DiskBasedTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[inMemTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[InMemTable2]   
    WHERE [c1]>0  
GO  
  
-- Declare parameters for the test queries.  
DECLARE @i INT = 1;  
DECLARE @rowcount INT = 100000;  
DECLARE @c NCHAR(48) = N'12345678901234567890123456789012345678';  
DECLARE @timems INT;  
DECLARE @starttime datetime2 = sysdatetime();  
  
-- Disk-based table queried with interpreted Transact-SQL.  
BEGIN TRAN  
  WHILE @I <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[DiskBasedTable](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (disk-based table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with interpreted Transact-SQL.  
SET @i = 1;  
SET @starttime = sysdatetime();  
  
BEGIN TRAN  
  WHILE @i <= @rowcount  
    BEGIN  
      INSERT INTO [dbo].[InMemTable](c1,c2) VALUES (@i, @c);  
      SET @i += 1;  
    END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with a natively-compiled stored procedure.  
SET @starttime = sysdatetime();  
  
EXEC usp_InsertData @rowcount, @c;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with natively-compiled stored procedure).';  
  
```  
  
 <span data-ttu-id="7a5d7-118">実際の応答時間を比較すると、メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャを用いた手法の方が、従来型のディスク ベースのテーブルに対して同じワークロードを実行した場合よりも一貫して応答時間が短いことがわかります。</span><span class="sxs-lookup"><span data-stu-id="7a5d7-118">The expected results provide actual response times showing how using memory-optimized tables and natively-compiled stored procedures typically provides consistently faster response times than the same workloads running against traditional disk-based tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a5d7-119">参照</span><span class="sxs-lookup"><span data-stu-id="7a5d7-119">See Also</span></span>  
 <span data-ttu-id="7a5d7-120">[インメモリ OLTP を示す AdventureWorks の拡張機能](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="7a5d7-120">[Extensions to AdventureWorks to Demonstrate In-Memory OLTP](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="7a5d7-121">[インメモリ OLTP &#40;インメモリ最適化&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="7a5d7-121">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 <span data-ttu-id="7a5d7-122">[メモリ最適化テーブル](memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="7a5d7-122">[Memory-Optimized Tables](memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="7a5d7-123">[ネイティブ コンパイル ストアド プロシージャ](natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7a5d7-123">[Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md) </span></span>  
 <span data-ttu-id="7a5d7-124">[メモリ最適化テーブルを使用するための要件](requirements-for-using-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="7a5d7-124">[Requirements for Using Memory-Optimized Tables](requirements-for-using-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="7a5d7-125">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a5d7-125">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="7a5d7-126">[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span><span class="sxs-lookup"><span data-stu-id="7a5d7-126">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span></span>  
 [<span data-ttu-id="7a5d7-127">プロシージャおよびメモリ最適化テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="7a5d7-127">CREATE PROCEDURE and Memory-Optimized Tables</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
