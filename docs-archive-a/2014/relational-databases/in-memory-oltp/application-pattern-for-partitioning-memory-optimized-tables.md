---
title: メモリ最適化テーブルのパーティション分割に関するアプリケーションのパターン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 3f867763-a8e6-413a-b015-20e9672cc4d1
author: rothja
ms.author: jroth
ms.openlocfilehash: d2633cdf1b631a1d9209adf26f4773e27c4c44c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632466"
---
# <a name="application-pattern-for-partitioning-memory-optimized-tables"></a><span data-ttu-id="69bc5-102">メモリ最適化テーブルのパーティション分割に関するアプリケーションのパターン</span><span class="sxs-lookup"><span data-stu-id="69bc5-102">Application Pattern for Partitioning Memory-Optimized Tables</span></span>
  [!INCLUDE[hek_2](../../includes/hek-2-md.md)] <span data-ttu-id="69bc5-103">は、限られた量のアクティブなデータがメモリ最適化テーブルに保持される一方、アクセス頻度の低いデータはディスクで処理される、というパターンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="69bc5-103">supports a pattern where a limited amount of active data is kept in a memory-optimized table, while less-frequently accessed data is processed on disk.</span></span> <span data-ttu-id="69bc5-104">通常、これはデータが `datetime` キーに基づいて格納されるシナリオです。</span><span class="sxs-lookup"><span data-stu-id="69bc5-104">Typically, this would be a scenario where data is stored based on a `datetime` key.</span></span>  
  
 <span data-ttu-id="69bc5-105">パーティション テーブルとメモリ最適化テーブルを共通のスキーマで維持することで、メモリ最適化テーブルでパーティション テーブルをエミュレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="69bc5-105">You can emulate partitioned tables with memory-optimized tables by maintaining a partitioned table and a memory-optimized table with a common schema.</span></span> <span data-ttu-id="69bc5-106">アクセス頻度の少ないデータが従来のパーティション テーブルに保持される一方、現在のデータはメモリ最適化テーブルに挿入されて更新されます。</span><span class="sxs-lookup"><span data-stu-id="69bc5-106">Current data would be inserted and updated in the memory-optimized table, while less-frequently accessed data would be maintained in the traditional partitioned table.</span></span>  
  
 <span data-ttu-id="69bc5-107">アクティブなデータがメモリ最適化テーブルに存在することを認識するアプリケーションは、ネイティブ コンパイル ストアド プロシージャを使用してデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="69bc5-107">An application that knows that the active data is in a memory-optimized table can use natively compiled stored procedures to access the data.</span></span> <span data-ttu-id="69bc5-108">データの範囲全体にアクセスする必要がある操作、つまりどのテーブルに関連データが保持されているかを認識できない操作では、解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、メモリ最適化テーブルとパーティション テーブルが結合されます。</span><span class="sxs-lookup"><span data-stu-id="69bc5-108">Operations that need to access the entire span of data, or which may not know which table holds relevant data, use interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] to join the memory-optimized table with the partitioned table.</span></span>  
  
 <span data-ttu-id="69bc5-109">このパーティション切り替えは、次のように行われます。</span><span class="sxs-lookup"><span data-stu-id="69bc5-109">This partition switch is described as follows:</span></span>  
  
-   <span data-ttu-id="69bc5-110">場合によっては基準日を使用して、インメモリ OLTP テーブルのデータをステージング テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="69bc5-110">Insert data from the In-Memory OLTP table into a staging table, possibly using a cutoff date.</span></span>  
  
-   <span data-ttu-id="69bc5-111">メモリ最適化テーブルから同じデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="69bc5-111">Delete the same data from the memory-optimized table.</span></span>  
  
-   <span data-ttu-id="69bc5-112">ステージング テーブルでスワップします。</span><span class="sxs-lookup"><span data-stu-id="69bc5-112">Swap in the staging table.</span></span>  
  
-   <span data-ttu-id="69bc5-113">アクティブなパーティションを追加します。</span><span class="sxs-lookup"><span data-stu-id="69bc5-113">Add the active partition.</span></span>  
  
 <span data-ttu-id="69bc5-114">![パーティションの切り替え](../../database-engine/media/hekaton-partitioned-tables.gif "パーティションの切り替え")</span><span class="sxs-lookup"><span data-stu-id="69bc5-114">![Partition switch.](../../database-engine/media/hekaton-partitioned-tables.gif "Partition switch.")</span></span>  
<span data-ttu-id="69bc5-115">アクティブなデータの管理</span><span class="sxs-lookup"><span data-stu-id="69bc5-115">Active Data Maintenance</span></span>  
  
 <span data-ttu-id="69bc5-116">ActiveOrders の削除で始まる操作は、データの削除とステージング テーブルでの切り替えの間のクエリのデータ欠落を回避するために、メンテナンス期間中に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bc5-116">The actions starting with Deleting ActiveOrders need to be done during a maintenance window to avoid queries missing data during the time between deleting data and switching in the staging table.</span></span>  
  
 <span data-ttu-id="69bc5-117">関連サンプルについては、「 [アプリケーション レベルのパーティション分割](application-level-partitioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69bc5-117">For a related sample, see [Application-Level Partitioning](application-level-partitioning.md).</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="69bc5-118">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="69bc5-118">Code Sample</span></span>  
 <span data-ttu-id="69bc5-119">次の例は、メモリ最適化テーブルとディスク ベースのパーティション テーブルの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="69bc5-119">The following sample shows how to use a memory-optimized table with a partitioned disk-based table.</span></span> <span data-ttu-id="69bc5-120">頻繁に使用されるデータはメモリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="69bc5-120">Frequently-used data is stored in memory.</span></span> <span data-ttu-id="69bc5-121">ディスクにデータを保存するには、新しいパーティションを作成し、パーティション テーブルにデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="69bc5-121">To save the data to disk, create a new partition and copy the data to the partitioned table.</span></span>  
  
 <span data-ttu-id="69bc5-122">このサンプルの最初の部分では、データベースおよび必要なオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="69bc5-122">The first part of this sample creates the database and necessary objects.</span></span> <span data-ttu-id="69bc5-123">サンプルの 2 番目の部分では、メモリ最適化テーブルからパーティション テーブルにデータを移動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="69bc5-123">The second part of the sample shows how to move data from a memory-optimized table into a partitioned table.</span></span>  
  
```sql  
CREATE DATABASE partitionsample;  
GO  
  
-- enable for In-Memory OLTP - change file path as needed  
ALTER DATABASE partitionsample ADD FILEGROUP partitionsample_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE partitionsample ADD FILE( NAME = 'partitionsample_mod' , FILENAME = 'c:\data\partitionsample_mod') TO FILEGROUP partitionsample_mod;  
GO  
  
USE partitionsample;  
GO  
  
-- frequently used portion of the SalesOrders - memory-optimized  
  
CREATE TABLE dbo.SalesOrders_hot (  
   so_id INT IDENTITY PRIMARY KEY NONCLUSTERED,  
   cust_id INT NOT NULL,  
   so_date DATETIME2 NOT NULL INDEX ix_date NONCLUSTERED,  
   so_total MONEY NOT NULL,  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- cold portion of the SalesOrders - partitioned disk-based table  
CREATE PARTITION FUNCTION [ByDatePF](datetime2) AS RANGE RIGHT   
   FOR VALUES();  
GO  
  
CREATE PARTITION SCHEME [ByDateRange]   
   AS PARTITION [ByDatePF]   
   ALL TO ([PRIMARY]);  
GO  
  
CREATE TABLE dbo.SalesOrders_cold (  
   so_id INT NOT NULL,  
   cust_id INT NOT NULL,  
   so_date DATETIME2 NOT NULL,  
   so_total MONEY NOT NULL,  
   CONSTRAINT PK_SalesOrders_cold PRIMARY KEY (so_id, so_date),  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)  
) ON [ByDateRange](so_date)  
GO  
  
-- table for temporary partitions  
CREATE TABLE dbo.SalesOrders_cold_staging (  
   so_id INT NOT NULL,  
   cust_id INT NOT NULL,  
   so_date datetime2 NOT NULL,  
   so_total MONEY NOT NULL,  
   CONSTRAINT PK_SalesOrders_cold_staging PRIMARY KEY (so_id, so_date),  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc),  
   CONSTRAINT CHK_SalesOrders_cold_staging CHECK (so_date >= '1900-01-01')  
)  
GO  
  
-- aggregate view of the hot and cold data  
CREATE VIEW dbo.SalesOrders  
AS SELECT so_id,  
   cust_id,  
   so_date,  
   so_total,  
   1 AS 'is_hot'  
   FROM dbo.SalesOrders_hot  
   UNION ALL  
   SELECT so_id,  
          cust_id,  
          so_date,  
          so_total,  
          0 AS 'is_hot'  
          FROM dbo.SalesOrders_cold;  
GO  
  
-- move all sales orders up to the split date to cold storage  
CREATE PROCEDURE dbo.usp_SalesOrdersOffloadToCold @splitdate datetime2  
   AS  
   BEGIN  
      BEGIN TRANSACTION;  
      -- create new heap based on the hot data to be moved to cold storage  
      INSERT INTO dbo.SalesOrders_cold_staging WITH( TABLOCKX)  
      SELECT so_id , cust_id , so_date , so_total  
         FROM dbo.SalesOrders_hot WITH ( serializable)  
         WHERE so_date <= @splitdate;  
  
      -- remove moved data  
      DELETE FROM dbo.SalesOrders_hot WITH( SERIALIZABLE)  
         WHERE so_date <= @splitdate;  
  
      -- update partition function, and switch in new partition  
      ALTER PARTITION SCHEME [ByDateRange] NEXT USED [PRIMARY];  
  
      DECLARE @p INT = ( SELECT MAX( partition_number) FROM sys.partitions WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold'));  
      EXEC sp_executesql N'alter table dbo.SalesOrders_cold_staging  
         SWITCH TO dbo.SalesOrders_cold partition @i' , N'@i int' , @i = @p;  
  
      ALTER PARTITION FUNCTION [ByDatePF]()  
      SPLIT RANGE( @splitdate);  
  
      -- modify constraint on staging table to align with new partition  
      ALTER TABLE dbo.SalesOrders_cold_staging DROP CONSTRAINT CHK_SalesOrders_cold_staging;  
  
      DECLARE @s nvarchar( 100) = CONVERT( nvarchar( 100) , @splitdate , 121);  
      DECLARE @sql nvarchar( 1000) = N'alter table dbo.SalesOrders_cold_staging   
         add constraint CHK_SalesOrders_cold_staging check (so_date > ''' + @s + ''')';  
      PRINT @sql;  
      EXEC sp_executesql @sql;  
  
      COMMIT;  
END;  
GO  
  
-- insert sample values in the hot table  
INSERT INTO dbo.SalesOrders_hot VALUES(1,SYSDATETIME(), 1);   
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);  
GO  
  
-- verify contents of the table  
SELECT *  FROM dbo.SalesOrders;  
GO  
  
-- offload all sales orders to date to cold storage  
DECLARE  @t datetime2 = SYSDATETIME();  
EXEC dbo.usp_SalesOrdersOffloadToCold @t;  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- verify partitions  
SELECT OBJECT_NAME( object_id) , * FROM sys.dm_db_partition_stats ps  
   WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold');  
  
-- insert more rows in the hot table  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- offload all sales orders to date to cold storage  
DECLARE @t datetime2 = SYSDATETIME();  
EXEC dbo.usp_SalesOrdersOffloadToCold @t;  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- verify partitions  
SELECT OBJECT_NAME( object_id) , partition_number , row_count  FROM sys.dm_db_partition_stats ps  
  WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold') AND index_id = 1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="69bc5-124">参照</span><span class="sxs-lookup"><span data-stu-id="69bc5-124">See Also</span></span>  
 [<span data-ttu-id="69bc5-125">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="69bc5-125">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
