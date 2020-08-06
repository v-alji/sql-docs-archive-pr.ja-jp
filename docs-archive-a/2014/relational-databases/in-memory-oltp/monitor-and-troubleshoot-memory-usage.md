---
title: メモリ使用量の監視とトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 7a458b9c-3423-4e24-823d-99573544c877
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5805ed06ad78040dbdf6c8557e5f548ad57f618b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742078"
---
# <a name="monitor-and-troubleshoot-memory-usage"></a><span data-ttu-id="3eebb-102">メモリ使用量の監視とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3eebb-102">Monitor and Troubleshoot Memory Usage</span></span>
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="3eebb-103">は、ディスク ベース テーブルとは異なるパターンでメモリを消費します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-103">consumes memory in different patterns than disk-based tables.</span></span> <span data-ttu-id="3eebb-104">メモリおよびガベージ コレクション サブシステムに提供される DMV またはパフォーマンス カウンターを使用して、データベース内のメモリ最適化テーブルとインデックス向けに割り当てられて使用されているメモリの量を監視できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-104">You can monitor the amount of memory allocated and used by memory-optimized tables and indexes in your database using the DMVs or performance counters provided for memory and the garbage collection subsystem.</span></span>  <span data-ttu-id="3eebb-105">これによって、システム レベルとデータベース レベルの両方で状況を表示でき、メモリの枯渇による問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-105">This gives you visibility at both the system and database level and lets you prevent problems due to memory exhaustion.</span></span>

 <span data-ttu-id="3eebb-106">このトピックでは、 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] のメモリ使用量の監視について説明します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-106">This topic covers monitoring your [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] memory usage.</span></span>


##  <a name="create-a-sample-database-with-memory-optimized-tables"></a><a name="bkmk_CreateDB"></a> <span data-ttu-id="3eebb-107">メモリ最適化テーブルが含まれるサンプル データベースの作成</span><span class="sxs-lookup"><span data-stu-id="3eebb-107">Create a sample database with memory-optimized tables</span></span>
 <span data-ttu-id="3eebb-108">既にメモリ最適化テーブルが含まれるデータベースがある場合は、このセクションを省略できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-108">You can skip this section if you already have a database with memory-optimized tables.</span></span>

 <span data-ttu-id="3eebb-109">以下の手順では、このトピックの残りのセクションで使用する、3 つのメモリ最適化テーブルが含まれるデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-109">The following steps create a database with three memory-optimized tables that you can use in the remainder of this topic.</span></span> <span data-ttu-id="3eebb-110">例では、メモリ最適化テーブルで使用できるメモリの量を制御できるように、データベースをリソース プールにマップしました。</span><span class="sxs-lookup"><span data-stu-id="3eebb-110">In the example, we mapped the database to a resource pool so that we can control how much memory can be taken by memory-optimized tables.</span></span>

1.  <span data-ttu-id="3eebb-111">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を起動します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-111">Launch [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>

2.  <span data-ttu-id="3eebb-112">**[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3eebb-112">Click **New Query**.</span></span>

3.  <span data-ttu-id="3eebb-113">次のコードを新しいクエリ ウィンドウに貼り付け、各セクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-113">Paste this code into the new query window and execute each section.</span></span>

    ```
    -- create a database to be used
    CREATE DATABASE IMOLTP_DB
    GO

    ALTER DATABASE IMOLTP_DB ADD FILEGROUP IMOLTP_DB_xtp_fg CONTAINS MEMORY_OPTIMIZED_DATA
    ALTER DATABASE IMOLTP_DB ADD FILE( NAME = 'IMOLTP_DB_xtp' , FILENAME = 'C:\Data\IMOLTP_DB_xtp') TO FILEGROUP IMOLTP_DB_xtp_fg;
    GO

    USE IMOLTP_DB
    GO

    -- create the resoure pool
    CREATE RESOURCE POOL PoolIMOLTP WITH (MAX_MEMORY_PERCENT = 60);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    GO

    -- bind the database to a resource pool
    EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'PoolIMOLTP'

    -- you can query the binding using the catalog view as described here
    SELECT d.database_id
         , d.name
         , d.resource_pool_id
    FROM sys.databases d
    GO

    -- take database offline/online to finalize the binding to the resource pool
    USE master
    GO

    ALTER DATABASE IMOLTP_DB SET OFFLINE
    GO
    ALTER DATABASE IMOLTP_DB SET ONLINE
    GO

    -- create some tables
    USE IMOLTP_DB
    GO

    -- create table t1
    CREATE TABLE dbo.t1 (
           c1 int NOT NULL CONSTRAINT [pk_t1_c1] PRIMARY KEY NONCLUSTERED
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO

    -- load t1 150K rows
    DECLARE @i int = 0
    BEGIN TRAN
    WHILE (@i <= 150000)
       BEGIN
          INSERT t1 VALUES (@i, 'a', replicate ('b', 8000))
          SET @i += 1;
       END
    Commit
    GO

    -- Create another table, t2
    CREATE TABLE dbo.t2 (
           c1 int NOT NULL CONSTRAINT [pk_t2_c1] PRIMARY KEY NONCLUSTERED
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO

    -- Create another table, t3 
    CREATE TABLE dbo.t3 (
           c1 int NOT NULL CONSTRAINT [pk_t3_c1] PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 1000000)
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO
    ```

##  <a name="monitoring-memory-usage"></a><span data-ttu-id="3eebb-114">メモリ使用率の監視</span><span class="sxs-lookup"><span data-stu-id="3eebb-114">Monitoring Memory Usage</span></span>

###  <a name="using-ssmanstudiofull"></a><span data-ttu-id="3eebb-115">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の使用</span><span class="sxs-lookup"><span data-stu-id="3eebb-115">Using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="3eebb-116">には、インメモリ テーブルによって消費されるメモリを監視するための標準レポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="3eebb-116">ships with built-in standard reports to monitor the memory consumed by in-memory tables.</span></span> <span data-ttu-id="3eebb-117">これらのレポートには、オブジェクト エクスプローラーを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-117">You can access these reports using Object Explorer.</span></span> <span data-ttu-id="3eebb-118">オブジェクト エクスプローラーを使用すると、個々のメモリ最適化テーブルで消費されるメモリも監視できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-118">You can also use the object explorer to monitor memory consumed by individual memory-optimized tables.</span></span>

#### <a name="consumption-at-the-database-level"></a><span data-ttu-id="3eebb-119">データベース レベルでの消費量</span><span class="sxs-lookup"><span data-stu-id="3eebb-119">Consumption at the database level</span></span>
 <span data-ttu-id="3eebb-120">次のように、データベース レベルでのメモリ使用を監視できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-120">You can monitor memory use at the database level as follows.</span></span>

1.  <span data-ttu-id="3eebb-121">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を起動し、サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-121">Launch [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and connect to a server.</span></span>

2.  <span data-ttu-id="3eebb-122">オブジェクト エクスプローラーで、レポートが必要なデータベースを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="3eebb-122">In Object Explorer, right-click the database you want reports on.</span></span>

3.  <span data-ttu-id="3eebb-123">コンテキスト メニューで、 **[レポート]**  -> **Standard [レポート]**  ->  **[メモリ最適化オブジェクトによるメモリ使用量]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3eebb-123">In the context menu select, **Reports** -> **Standard Reports** -> **Memory Usage By Memory Optimized Objects**</span></span>

 <span data-ttu-id="3eebb-124">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuse.gif "HK_MM_SSMS")</span><span class="sxs-lookup"><span data-stu-id="3eebb-124">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuse.gif "HK_MM_SSMS")</span></span>

 <span data-ttu-id="3eebb-125">このレポートは、上で作成したデータベースによるメモリ消費を示します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-125">This report shows memory consumption by the database we created above.</span></span>

 <span data-ttu-id="3eebb-126">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuserpt.gif "HK_MM_SSMS")</span><span class="sxs-lookup"><span data-stu-id="3eebb-126">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuserpt.gif "HK_MM_SSMS")</span></span>

###  <a name="using-dmvs"></a><span data-ttu-id="3eebb-127">DMV の使用</span><span class="sxs-lookup"><span data-stu-id="3eebb-127">Using DMVs</span></span>
 <span data-ttu-id="3eebb-128">メモリ最適化テーブル、インデックス、システム オブジェクト、およびランタイム構造によって消費されるメモリを監視するために、いくつかの DMV を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-128">There are a number of DMVs available to monitor memory consumed by memory-optimized tables, indexes, system objects, and by run-time structures.</span></span>

#### <a name="memory-consumption-by-memory-optimized-tables-and-indexes"></a><span data-ttu-id="3eebb-129">メモリ最適化テーブルおよびインデックスによるメモリ消費</span><span class="sxs-lookup"><span data-stu-id="3eebb-129">Memory consumption by memory-optimized tables and indexes</span></span>
 <span data-ttu-id="3eebb-130">次に示すように、 `sys.dm_db_xtp_table_memory_stats` にクエリを実行することで、すべてのユーザー テーブル、インデックス、およびシステム オブジェクトのメモリ消費を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-130">You can find memory consumption for all user tables, indexes, and system objects by querying `sys.dm_db_xtp_table_memory_stats` as shown here.</span></span>

```sql
SELECT object_name(object_id) AS Name
     , *
   FROM sys.dm_db_xtp_table_memory_stats
```

 <span data-ttu-id="3eebb-131">**サンプル出力**</span><span class="sxs-lookup"><span data-stu-id="3eebb-131">**Sample Output**</span></span>

```
Name       object_id   memory_allocated_for_table_kb memory_used_by_table_kb memory_allocated_for_indexes_kb memory_used_by_indexes_kb
---------- ----------- ----------------------------- ----------------------- ------------------------------- -------------------------
t3         629577281   0                             0                       128                             0
t1         565577053   1372928                       1200008                 7872                            1942
t2         597577167   0                             0                       128                             0
NULL       -6          0                             0                       2                               2
NULL       -5          0                             0                       24                              24
NULL       -4          0                             0                       2                               2
NULL       -3          0                             0                       2                               2
NULL       -2          192                           25                      16                              16
```

 <span data-ttu-id="3eebb-132">詳細については、「 [sys. dm_db_xtp_table_memory_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql?view=sql-server-2016)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3eebb-132">For more information, see [sys.dm_db_xtp_table_memory_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql?view=sql-server-2016).</span></span>

#### <a name="memory-consumption-by-internal-system-structures"></a><span data-ttu-id="3eebb-133">内部システム構造によるメモリ消費</span><span class="sxs-lookup"><span data-stu-id="3eebb-133">Memory consumption by internal system structures</span></span>
 <span data-ttu-id="3eebb-134">メモリは、トランザクション構造、データ ファイルとデルタ ファイルのバッファー、ガベージ コレクション構造などのシステム オブジェクトによっても消費されます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-134">Memory is also consumed by system objects, such as, transactional structures, buffers for data and delta files, garbage collection structures, and more.</span></span> <span data-ttu-id="3eebb-135">次に示すように、 `sys.dm_xtp_system_memory_consumers` にクエリを実行することで、これらのシステム オブジェクトに使用されるメモリを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-135">You can find the memory used for these system objects by querying `sys.dm_xtp_system_memory_consumers` as shown here.</span></span>

```sql
SELECT memory_consumer_desc
     , allocated_bytes/1024 AS allocated_bytes_kb
     , used_bytes/1024 AS used_bytes_kb
     , allocation_count
   FROM sys.dm_xtp_system_memory_consumers
```

 <span data-ttu-id="3eebb-136">**サンプル出力**</span><span class="sxs-lookup"><span data-stu-id="3eebb-136">**Sample Output**</span></span>

```
memory_consumer_ desc allocated_bytes_kb   used_bytes_kb        allocation_count
------------------------- -------------------- -------------------- ----------------
VARHEAP                   0                    0                    0
VARHEAP                   384                  0                    0
DBG_GC_OUTSTANDING_T      64                   64                   910
ACTIVE_TX_MAP_LOOKAS      0                    0                    0
RECOVERY_TABLE_CACHE      0                    0                    0
RECENTLY_USED_ROWS_L      192                  192                  261
RANGE_CURSOR_LOOKSID      0                    0                    0
HASH_CURSOR_LOOKASID      128                  128                  455
SAVEPOINT_LOOKASIDE       0                    0                    0
PARTIAL_INSERT_SET_L      192                  192                  351
CONSTRAINT_SET_LOOKA      192                  192                  646
SAVEPOINT_SET_LOOKAS      0                    0                    0
WRITE_SET_LOOKASIDE       192                  192                  183
SCAN_SET_LOOKASIDE        64                   64                   31
READ_SET_LOOKASIDE        0                    0                    0
TRANSACTION_LOOKASID      448                  448                  156
PGPOOL:256K               768                  768                  3
PGPOOL: 64K               0                    0                    0
PGPOOL:  4K               0                    0                    0
```

 <span data-ttu-id="3eebb-137">詳細については、「[sys.dm_xtp_system_memory_consumers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3eebb-137">For more information see [sys.dm_xtp_system_memory_consumers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql).</span></span>


#### <a name="memory-consumption-at-run-time-when-accessing-memory-optimized-tables"></a><span data-ttu-id="3eebb-138">メモリ最適化テーブルにアクセスするときの実行時のメモリ消費</span><span class="sxs-lookup"><span data-stu-id="3eebb-138">Memory consumption at run-time when accessing memory-optimized tables</span></span>
 <span data-ttu-id="3eebb-139">次のクエリを使用して、プロシージャ キャッシュなどのランタイム構造で消費されたメモリを確認できます。このクエリを実行して、プロシージャ キャッシュ用などのランタイム構造で使用されたメモリの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-139">You can determine the memory consumed by run time structures, such as the procedure cache with the following query: run this query to get the memory used by run-time structures such as for the procedure cache.</span></span> <span data-ttu-id="3eebb-140">すべてのランタイム構造は XTP でタグ付けされます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-140">All run-time structures are tagged with XTP.</span></span>

```sql
SELECT memory_object_address
     , pages_in_bytes
     , bytes_used
     , type
   FROM sys.dm_os_memory_objects WHERE type LIKE '%xtp%'
```

 <span data-ttu-id="3eebb-141">**サンプル出力**</span><span class="sxs-lookup"><span data-stu-id="3eebb-141">**Sample Output**</span></span>

```
memory_object_address pages_ in_bytes bytes_used type
--------------------- ------------------- ---------- ----
0x00000001F1EA8040    507904              NULL       MEMOBJ_XTPDB
0x00000001F1EAA040    68337664            NULL       MEMOBJ_XTPDB
0x00000001FD67A040    16384               NULL       MEMOBJ_XTPPROCCACHE
0x00000001FD68C040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD284040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD302040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD382040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD402040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD482040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD502040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD67E040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001F813C040    8192                NULL       MEMOBJ_XTPBLOCKALLOC
0x00000001F813E040    16842752            NULL       MEMOBJ_XTPBLOCKALLOC
```

 <span data-ttu-id="3eebb-142">詳細については、「 [dm_os_memory_objects (transact-sql)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3eebb-142">For more information, see [sys.dm_os_memory_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql).</span></span>

#### <a name="memory-consumed-by-hek_2-engine-across-the-instance"></a><span data-ttu-id="3eebb-143">インスタンス全体で [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] エンジンによって消費されるメモリ</span><span class="sxs-lookup"><span data-stu-id="3eebb-143">Memory consumed by [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine across the instance</span></span>
 <span data-ttu-id="3eebb-144">[!INCLUDE[hek_2](../../../includes/hek-2-md.md)] エンジンとメモリ最適化オブジェクトに割り当てられたメモリは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の他のメモリ コンシューマーと同様に管理されます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-144">Memory allocated to the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine and the memory-optimized objects is managed the same way as any other memory consumer within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="3eebb-145">MEMORYCLERK_XTP 型のクラークによって、 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] エンジンに割り当てられたすべてのメモリについて確認できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-145">The clerks of type MEMORYCLERK_XTP accounts for all the memory allocated to [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine.</span></span> <span data-ttu-id="3eebb-146">次のクエリを使用して、 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] エンジンによって使用されるすべてのメモリを確認します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-146">Use the following query to find all the memory used by the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine.</span></span>

```sql
-- this DMV accounts for all memory used by the hek_2 engine
SELECT type
     , name
     , memory_node_id
     , pages_kb/1024 AS pages_MB 
   FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'
```

 <span data-ttu-id="3eebb-147">このサンプル出力は、割り当てられた合計メモリが、システム レベルのメモリ消費 18 MB と、データベース ID が 5 のデータベースに割り当てられた 1358 MB であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="3eebb-147">The sample output shows that the total memory allocated is 18 MB system-level memory consumption and 1358MB allocated to database id of 5.</span></span> <span data-ttu-id="3eebb-148">このデータベースは専用のリソース プールにマップされるため、このメモリはそのリソース プールに反映されます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-148">Since this database is mapped to a dedicated resource pool, this memory is accounted for in that resource pool.</span></span>

 <span data-ttu-id="3eebb-149">**サンプル出力**</span><span class="sxs-lookup"><span data-stu-id="3eebb-149">**Sample Output**</span></span>

```
type                 name       memory_node_id pages_MB
-------------------- ---------- -------------- --------------------
MEMORYCLERK_XTP      Default    0              18
MEMORYCLERK_XTP      DB_ID_5    0              1358
MEMORYCLERK_XTP      Default    64             0
```

 <span data-ttu-id="3eebb-150">詳細については、「 [dm_os_memory_clerks (transact-sql)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3eebb-150">For more information, see [sys.dm_os_memory_clerks (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql).</span></span>

##   <a name="managing-memory-consumed-by-memory-optimized-objects"></a><span data-ttu-id="3eebb-151">メモリ最適化オブジェクトに消費されるメモリの管理</span><span class="sxs-lookup"><span data-stu-id="3eebb-151">Managing memory consumed by memory-optimized objects</span></span>
 <span data-ttu-id="3eebb-152">トピック「 [メモリ最適化テーブルを持つデータベースのリソース プールへのバインド](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)」で説明しているように、名前付きリソース プールにバインドすることでメモリ最適化テーブルによって消費されるメモリの合計を制御できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-152">You can control the total memory consumed by memory-optimized tables by binding it to a named resource pool as described in the topic [Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md).</span></span>

##  <a name="troubleshooting-memory-issues"></a><span data-ttu-id="3eebb-153">メモリに関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3eebb-153">Troubleshooting Memory Issues</span></span>
 <span data-ttu-id="3eebb-154">メモリに関する問題のトラブルシューティングは、次の 3 つの手順で行います。</span><span class="sxs-lookup"><span data-stu-id="3eebb-154">Troubleshooting memory issues is a three step process:</span></span>

1.  <span data-ttu-id="3eebb-155">データベースまたはインスタンスのオブジェクトによって消費されているメモリ量を特定します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-155">Identify how much memory is being consumed by the objects in your database or instance.</span></span> <span data-ttu-id="3eebb-156">前に説明したように、メモリ最適化テーブルで使用可能な豊富な監視ツール セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-156">You can use a rich set of monitoring tools available for memory-optimized tables as described earlier.</span></span>  <span data-ttu-id="3eebb-157">たとえば、DMV の `sys.dm_db_xtp_table_memory_stats` または `sys.dm_os_memory_clerks`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-157">For example the DMVs `sys.dm_db_xtp_table_memory_stats` or `sys.dm_os_memory_clerks`.</span></span>

2.  <span data-ttu-id="3eebb-158">メモリ消費がどのように拡大し、どれぐらいの余裕が残されているかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-158">Determine how memory consumption is growing and how much head room you have left.</span></span> <span data-ttu-id="3eebb-159">メモリ消費を定期的に監視することで、メモリの使用がどのように拡大しているかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-159">By monitoring the memory consumption periodically, you can know how the memory use is growing.</span></span> <span data-ttu-id="3eebb-160">たとえば、名前付きリソース プールにデータベースをマップしている場合は、パフォーマンス カウンターの Used Memory (KB) を監視して、メモリの使用量がどのように拡大しているかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="3eebb-160">For example, if you have mapped the database to a named resource pool, you can monitor the performance counter Used Memory (KB) to see how memory usage is growing.</span></span>

3.  <span data-ttu-id="3eebb-161">発生する可能性があるメモリの問題を軽減するアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3eebb-161">Take action to mitigate the potential memory issues.</span></span> <span data-ttu-id="3eebb-162">詳細については、「[メモリ不足の問題の解決](resolve-out-of-memory-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3eebb-162">For more information, see [Resolve Out Of Memory Issues](resolve-out-of-memory-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3eebb-163">参照</span><span class="sxs-lookup"><span data-stu-id="3eebb-163">See Also</span></span>
 <span data-ttu-id="3eebb-164">[メモリ最適化テーブルを含むデータベースをリソースプール](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)の[変更 MIN_MEMORY_PERCENT にバインドし、既存のプールに MAX_MEMORY_PERCENT](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)する</span><span class="sxs-lookup"><span data-stu-id="3eebb-164">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)</span></span>


