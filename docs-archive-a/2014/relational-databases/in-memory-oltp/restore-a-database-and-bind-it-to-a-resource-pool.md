---
title: データベースの復元とリソース プールへのバインド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0b518c93ca9d5e7157ceaa20d9548d7b6061017d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631021"
---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a><span data-ttu-id="bcc5a-102">データベースの復元とリソース プールへのバインド</span><span class="sxs-lookup"><span data-stu-id="bcc5a-102">Restore a Database and Bind it to a Resource Pool</span></span>
  <span data-ttu-id="bcc5a-103">メモリ最適化テーブルが含まれるデータベースを復元するためのメモリが十分にある場合も、ベスト プラクティスに従って名前付きリソース プールにデータベースをバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-103">Even though you have enough memory to restore a database with memory-optimized tables, you want to follow best practices and bind the database to a named resource pool.</span></span> <span data-ttu-id="bcc5a-104">データベースをプールにバインドする前に、そのデータベースが存在する必要があるため、データベースを復元するプロセスには複数のステップが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-104">Since the database must exist before you can bind it to the pool restoring your database is a multi-step process.</span></span> <span data-ttu-id="bcc5a-105">このトピックでは、そのプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-105">This topic walks you through that process.</span></span>  
  
##  <a name="restore-with-norecovery"></a><span data-ttu-id="bcc5a-106">NORECOVERY を指定して復元を行う</span><span class="sxs-lookup"><span data-stu-id="bcc5a-106">Restore with NORECOVERY</span></span>  
 <span data-ttu-id="bcc5a-107">データベースを復元するときに、NORECOVERY ではメモリを使用せずにデータベースが作成され、ディスク イメージが復元されます。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-107">When you restore a database, NORECOVERY causes the database to be created and the disk image restored without consuming memory.</span></span>  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
##  <a name="create-the-resource-pool"></a><span data-ttu-id="bcc5a-108">リソース プールを作成する</span><span class="sxs-lookup"><span data-stu-id="bcc5a-108">Create the resource pool</span></span>  
 <span data-ttu-id="bcc5a-109">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] では、使用可能なメモリを 50% に指定して、Pool_IMOLTP という名前のリソース プールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-109">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] creates a resource pool named Pool_IMOLTP with 50% of memory available for its use.</span></span>  <span data-ttu-id="bcc5a-110">プールが作成された後、Pool_IMOLTP が含まれるようにリソース ガバナーが再構成されます。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-110">After the pool is created, the Resource Governor is reconfigured to include Pool_IMOLTP.</span></span>  
  
```sql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
##  <a name="bind-the-database-and-resource-pool"></a><span data-ttu-id="bcc5a-111">データベースとリソース プールをバインドする</span><span class="sxs-lookup"><span data-stu-id="bcc5a-111">Bind the database and resource pool</span></span>  
 <span data-ttu-id="bcc5a-112">システム関数 `sp_xtp_bind_db_resource_pool` を使用して、データベースをリソース プールにバインドします。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-112">Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool.</span></span> <span data-ttu-id="bcc5a-113">この関数は、パラメーターとしてデータベース名とリソース プール名をこの順序で受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-113">The function takes two parameters: the database name followed by the resource pool name.</span></span>  
  
 <span data-ttu-id="bcc5a-114">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] では、リソース プール Pool_IMOLTP へのデータベース IMOLTP_DB のバインドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-114">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] defines a binding of the database IMOLTP_DB to the resource pool Pool_IMOLTP.</span></span> <span data-ttu-id="bcc5a-115">このバインドは、次の手順を完了するまで有効になりません。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-115">The binding does not become effective until you complete the next step.</span></span>  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
##  <a name="restore-with-recovery"></a><span data-ttu-id="bcc5a-116">RECOVERY を指定して復元を行う</span><span class="sxs-lookup"><span data-stu-id="bcc5a-116">Restore with RECOVERY</span></span>  
 <span data-ttu-id="bcc5a-117">RECOVERY を指定してデータベースを復元すると、データベースがオンラインになり、すべてのデータが復元されます。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-117">When you restore the database with recovery the database is brought online and all the data restored.</span></span>  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
##  <a name="monitor-the-resource-pool-performance"></a><span data-ttu-id="bcc5a-118">リソース プール パフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="bcc5a-118">Monitor the resource pool performance</span></span>  
 <span data-ttu-id="bcc5a-119">データベースが名前付きリソース プールにバインドされ、RECOVERY を指定して復元されたら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Resource Pool Stats オブジェクトを監視します。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-119">Once the database is bound to the named resource pool and restored with recovery, monitor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Resource Pool Stats Object.</span></span> <span data-ttu-id="bcc5a-120">詳細については、「 [SQL Server、Resource Pool Stats オブジェクト](../performance-monitor/sql-server-resource-pool-stats-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcc5a-120">For more information see [SQL Server, Resource Pool Stats Object](../performance-monitor/sql-server-resource-pool-stats-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc5a-121">参照</span><span class="sxs-lookup"><span data-stu-id="bcc5a-121">See Also</span></span>  
 <span data-ttu-id="bcc5a-122">[データベースを作成してリソース プールにバインドする方法については、「](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="bcc5a-122">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span></span>  
 <span data-ttu-id="bcc5a-123">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bcc5a-123">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="bcc5a-124">[SQLServer:Resource Pool Stats オブジェクト](../performance-monitor/sql-server-resource-pool-stats-object.md) </span><span class="sxs-lookup"><span data-stu-id="bcc5a-124">[SQL Server, Resource Pool Stats Object](../performance-monitor/sql-server-resource-pool-stats-object.md) </span></span>  
 [<span data-ttu-id="bcc5a-125">sys.dm_resource_governor_resource_pools</span><span class="sxs-lookup"><span data-stu-id="bcc5a-125">sys.dm_resource_governor_resource_pools</span></span>](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)  
  
  
