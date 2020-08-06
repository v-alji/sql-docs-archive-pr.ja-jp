---
title: メモリ最適化テーブルを持つデータベースのリソース プールへのバインド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f222b1d5-d2fa-4269-8294-4575a0e78636
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cd163c5d3bc7a2cd9051b8d37b8127a1cc88c30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646150"
---
# <a name="bind-a-database-with-memory-optimized-tables-to-a-resource-pool"></a><span data-ttu-id="b499f-102">メモリ最適化テーブルを持つデータベースのリソース プールへのバインド</span><span class="sxs-lookup"><span data-stu-id="b499f-102">Bind a Database with Memory-Optimized Tables to a Resource Pool</span></span>
  <span data-ttu-id="b499f-103">リソース プールは、管理できる物理リソースのサブセットを表します。</span><span class="sxs-lookup"><span data-stu-id="b499f-103">A resource pool represents a subset of physical resources that can be governed.</span></span> <span data-ttu-id="b499f-104">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースは既定のリソース プールにバインドされてリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="b499f-104">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases are bound to and consume the resources of the default resource pool.</span></span> <span data-ttu-id="b499f-105">1 つ以上のメモリ最適化テーブルによって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリソースが消費されたり、メモリ最適化テーブルに必要なメモリが他のメモリ ユーザーによって消費されたりするのを防ぐために、別のリソース プールを作成して、メモリ最適化テーブルを持つデータベースのメモリ消費量を管理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b499f-105">To protect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from having its resources consumed by one or more memory-optimized tables, and to prevent other memory users from consuming memory needed by memory-optimized tables, you should create a separate resource pool to manage memory consumption for the database with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="b499f-106">1 つのデータベースをバインドできるのは、1 つのリソース プールだけです。</span><span class="sxs-lookup"><span data-stu-id="b499f-106">A database can be bound on only one resource pool.</span></span> <span data-ttu-id="b499f-107">ただし、同じプールに複数のデータベースをバインドすることは可能です。</span><span class="sxs-lookup"><span data-stu-id="b499f-107">However, you can bind multiple databases to the same pool.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b499f-108">では、メモリ最適化テーブルを持たないデータベースをリソース プールにバインドすることはできますが、バインドしても何も効果はありません。</span><span class="sxs-lookup"><span data-stu-id="b499f-108">allows binding a database without memory-optimized tables to a resource pool but it has no effect.</span></span> <span data-ttu-id="b499f-109">将来的にデータベースにメモリ最適化テーブルを作成する可能性がある場合は、データベースを名前付きリソース プールにバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="b499f-109">You may want to bind a database to a named resource pool if, in future, you may want to create memory-optimized tables in the database.</span></span>  
  
 <span data-ttu-id="b499f-110">データベースをリソース プールにバインドするには、事前にデータベースとリソース プールの両方が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b499f-110">Before you can bind a database to a resource pool both the database and the resource pool must exist.</span></span> <span data-ttu-id="b499f-111">バインドは、データベースが次にオンラインになったときに有効になります。</span><span class="sxs-lookup"><span data-stu-id="b499f-111">The binding takes effect the next time the database is brought online.</span></span> <span data-ttu-id="b499f-112">詳細については、「 [データベースの状態](../databases/database-states.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b499f-112">See [Database States](../databases/database-states.md) for more information.</span></span>  
  
 <span data-ttu-id="b499f-113">リソース プールについては、「 [リソース ガバナー リソース プール](../resource-governor/resource-governor-resource-pool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b499f-113">For information about resource pools, see [Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md).</span></span>  
  
  
## <a name="create-the-database-and-resource-pool"></a><span data-ttu-id="b499f-114">データベースとリソース プールを作成する</span><span class="sxs-lookup"><span data-stu-id="b499f-114">Create the database and resource pool</span></span>  
 <span data-ttu-id="b499f-115">データベースとリソース プールは、任意の順序で作成できます。</span><span class="sxs-lookup"><span data-stu-id="b499f-115">You can create the database and resource pool in any order.</span></span> <span data-ttu-id="b499f-116">重要なのは、データベースをリソース プールにバインドする前に、両方が存在することです。</span><span class="sxs-lookup"><span data-stu-id="b499f-116">What matters is that they both exist prior to binding the database to the resource pool.</span></span>  
  
### <a name="create-the-database"></a><span data-ttu-id="b499f-117">データベースの作成</span><span class="sxs-lookup"><span data-stu-id="b499f-117">Create the database</span></span>  
 <span data-ttu-id="b499f-118">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、IMOLTP_DB という名前のデータベースを作成します。このデータベースに、1 つ以上のメモリ最適化テーブルを格納します。</span><span class="sxs-lookup"><span data-stu-id="b499f-118">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] creates a database named IMOLTP_DB which will contain one or more memory-optimized tables.</span></span> <span data-ttu-id="b499f-119">パス \<driveAndPath> は、このコマンドを実行する前に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b499f-119">The path \<driveAndPath> must exist prior to running this command.</span></span>  
  
```sql  
CREATE DATABASE IMOLTP_DB  
GO  
ALTER DATABASE IMOLTP_DB ADD FILEGROUP IMOLTP_DB_fg CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP_DB ADD FILE( NAME = 'IMOLTP_DB_fg' , FILENAME = 'c:\data\IMOLTP_DB_fg') TO FILEGROUP IMOLTP_DB_fg;  
GO  
```  
  
### <a name="determine-the-minimum-value-for-min_memory_percent-and-max_memory_percent"></a><span data-ttu-id="b499f-120">MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の最小値の決定</span><span class="sxs-lookup"><span data-stu-id="b499f-120">Determine the minimum value for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT</span></span>  
 <span data-ttu-id="b499f-121">メモリ最適化テーブルに必要なメモリを確認したら、使用可能なメモリの何パーセントが必要になるかを特定し、メモリの割合をその値以上に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b499f-121">Once you determine the memory needs for your memory-optimized tables, you need to determine what percentage of available memory you need, and set the memory percentages to that value or higher.</span></span>  
  
 <span data-ttu-id="b499f-122">**例:**  </span><span class="sxs-lookup"><span data-stu-id="b499f-122">**Example:** </span></span>  
<span data-ttu-id="b499f-123">この例では、計算の結果、メモリ最適化テーブルおよびインデックスに 16 GB のメモリが必要であると確認されたものとします。</span><span class="sxs-lookup"><span data-stu-id="b499f-123">For this example we will assume that from your calculations you determined that your memory-optimized tables and indexes need 16 GB of memory.</span></span> <span data-ttu-id="b499f-124">また、使用できるメモリとして 32 GB がコミットされていると想定します。</span><span class="sxs-lookup"><span data-stu-id="b499f-124">Assume that you have 32 GB of memory committed for your use.</span></span>  
  
 <span data-ttu-id="b499f-125">一見すると、MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT は 50 (16 は 32 の 50%) に設定する必要があるように思われます。</span><span class="sxs-lookup"><span data-stu-id="b499f-125">At first glance it could seem that you need to set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to 50 (16 is 50% of 32).</span></span>  <span data-ttu-id="b499f-126">しかし、それではメモリ最適化テーブルに十分なメモリが与えられません。</span><span class="sxs-lookup"><span data-stu-id="b499f-126">However, that would not give your memory-optimized tables sufficient memory.</span></span> <span data-ttu-id="b499f-127">後に示す表 (「[メモリ最適化テーブルおよびインデックスで使用可能なメモリの割合](#percent-of-memory-available-for-memory-optimized-tables-and-indexes)」) によると、コミットされたメモリが 32 GB の場合、メモリ最適化テーブルとインデックスで使用できるのはその 80% だけです。</span><span class="sxs-lookup"><span data-stu-id="b499f-127">Looking at the table below ([Percent of memory available for memory-optimized tables and indexes](#percent-of-memory-available-for-memory-optimized-tables-and-indexes)) we see that if there is 32 GB of committed memory, only 80% of that is available for memory-optimized tables and indexes.</span></span>  <span data-ttu-id="b499f-128">このため、最小と最大の割合は、コミットされたメモリではなく使用可能なメモリに基づいて計算します。</span><span class="sxs-lookup"><span data-stu-id="b499f-128">Therefore, we calculate the min and max percentages based upon the available memory, not the committed memory.</span></span>  
  
 `memoryNeedeed = 16`   
 `memoryCommitted = 32`   
 `availablePercent = 0.8`   
 `memoryAvailable = memoryCommitted * availablePercent`   
 `percentNeeded = memoryNeeded / memoryAvailable`  
  
 <span data-ttu-id="b499f-129">実際の数値の算出:</span><span class="sxs-lookup"><span data-stu-id="b499f-129">Plugging in real numbes:</span></span>   
`percentNeeded = 16 / (32 * 0.8) = 16 / 25.6 = 0.625`  
  
 <span data-ttu-id="b499f-130">したがって、メモリ最適化テーブルとインデックスに 16 GB という要件を満たすには、使用可能なメモリの少なくとも 62.5% が必要です。</span><span class="sxs-lookup"><span data-stu-id="b499f-130">Thus you need at least 62.5% of the available memory to meet the 16 GB requirement of your memory-optimized tables and indexes.</span></span>  <span data-ttu-id="b499f-131">MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の値は整数にする必要があるため、少なくとも 63% として設定します。</span><span class="sxs-lookup"><span data-stu-id="b499f-131">Since the values for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT must be integers, we set them to at least 63%.</span></span>  
  
### <a name="create-a-resource-pool-and-configure-memory"></a><span data-ttu-id="b499f-132">リソース プールの作成とメモリの構成</span><span class="sxs-lookup"><span data-stu-id="b499f-132">Create a resource pool and configure memory</span></span>  
 <span data-ttu-id="b499f-133">メモリ最適化テーブルのメモリを構成するときは、MAX_MEMORY_PERCENT ではなく MIN_MEMORY_PERCENT に基づいてキャパシティ プランニングを実施する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b499f-133">When configuring memory for memory-optimized tables, the capacity planning should be done based on MIN_MEMORY_PERCENT, not on MAX_MEMORY_PERCENT.</span></span>  <span data-ttu-id="b499f-134">MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT については、「[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b499f-134">See [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) for information on MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span> <span data-ttu-id="b499f-135">この結果、メモリ最適化テーブルが使用できるメモリをより適切に予測することができます。MIN_MEMORY_PERCENT を指定すると、他のリソース プールにメモリの制約を加えて、この値に応じたメモリが確保されるためです。</span><span class="sxs-lookup"><span data-stu-id="b499f-135">This provides more predictable memory availability for memory-optimized tables as MIN_MEMORY_PERCENT causes memory pressure to other resource pools to make sure it is honored.</span></span> <span data-ttu-id="b499f-136">メモリを確実に使用できるようにし、さらにメモリ不足が発生しないようにするには、MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT を同じ値にします。</span><span class="sxs-lookup"><span data-stu-id="b499f-136">To ensure that memory is available and help avoid out-of-memory conditions, the values for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT should be the same.</span></span> <span data-ttu-id="b499f-137">コミットされたメモリの量に対してメモリ最適化テーブルで使用できるメモリの割合については、後の「 [メモリ最適化テーブルおよびインデックスで使用可能なメモリの割合](#percent-of-memory-available-for-memory-optimized-tables-and-indexes) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b499f-137">See [Percent of memory available for memory-optimized tables and indexes](#percent-of-memory-available-for-memory-optimized-tables-and-indexes) below for the percent of memory available for memory-optimized tables based on the amount of committed memory.</span></span>  
  
 <span data-ttu-id="b499f-138">VM 環境での操作の詳細については、「[ベスト プラクティス: VM 環境でのインメモリ OLTP の使用](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b499f-138">See [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information when working in a VM environment.</span></span>  
  
 <span data-ttu-id="b499f-139">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コードでは、使用可能なメモリを 50% に指定して、Pool_IMOLTP という名前のリソース プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="b499f-139">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a resource pool named Pool_IMOLTP with half of the memory available for its use.</span></span>  <span data-ttu-id="b499f-140">プールが作成された後、Pool_IMOLTP が含まれるようにリソース ガバナーが再構成されます。</span><span class="sxs-lookup"><span data-stu-id="b499f-140">After the pool is created Resource Governor is reconfigured to include Pool_IMOLTP.</span></span>  
  
```sql  
-- set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value  
CREATE RESOURCE POOL Pool_IMOLTP   
  WITH   
    ( MIN_MEMORY_PERCENT = 63,   
    MAX_MEMORY_PERCENT = 63 );  
GO  
  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="bind-the-database-to-the-pool"></a><span data-ttu-id="b499f-141">データベースをプールにバインドする</span><span class="sxs-lookup"><span data-stu-id="b499f-141">Bind the database to the pool</span></span>  
 <span data-ttu-id="b499f-142">システム関数 `sp_xtp_bind_db_resource_pool` を使用して、データベースをリソース プールにバインドします。</span><span class="sxs-lookup"><span data-stu-id="b499f-142">Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool.</span></span> <span data-ttu-id="b499f-143">この関数は、パラメーターとしてデータベース名とリソース プール名を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b499f-143">The function takes two parameters: the database name and the resource pool name.</span></span>  
  
 <span data-ttu-id="b499f-144">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] では、リソース プール Pool_IMOLTP へのデータベース IMOLTP_DB のバインドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="b499f-144">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] defines a binding of the database IMOLTP_DB to the resource pool Pool_IMOLTP.</span></span> <span data-ttu-id="b499f-145">このバインドは、データベースをオンラインにするまで有効になりません。</span><span class="sxs-lookup"><span data-stu-id="b499f-145">The binding does not become effective until you bring the database online.</span></span>  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
 <span data-ttu-id="b499f-146">システム関数 sp_xtp_bind_db_resourece_pool は、2 つの文字列パラメーター (database_name と pool_name) を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b499f-146">The system function sp_xtp_bind_db_resourece_pool takes two string parameters: database_name and pool_name.</span></span>  
  
## <a name="confirm-the-binding"></a><span data-ttu-id="b499f-147">バインドを確認する</span><span class="sxs-lookup"><span data-stu-id="b499f-147">Confirm the binding</span></span>  
 <span data-ttu-id="b499f-148">バインドを確認します。このとき、IMOLTP_DB のリソース プール ID に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b499f-148">Confirm the binding, noting the resource pool id for IMOLTP_DB.</span></span> <span data-ttu-id="b499f-149">NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b499f-149">It should not be NULL.</span></span>  
  
```sql  
SELECT d.database_id, d.name, d.resource_pool_id  
FROM sys.databases d  
GO  
```  
  
## <a name="make-the-binding-effective"></a><span data-ttu-id="b499f-150">バインドを有効にする</span><span class="sxs-lookup"><span data-stu-id="b499f-150">Make the binding effective</span></span>  
 <span data-ttu-id="b499f-151">バインドを有効にするには、リソース プールにバインドした後で、データベースをいったんオフラインにしてからオンラインに戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b499f-151">You must take the database offline and back online after binding it to the resource pool for binding to take effect.</span></span> <span data-ttu-id="b499f-152">データベースが以前に別のプールにバインドされていた場合は、これによって以前のリソース プールから割り当て済みのメモリが削除され、新しくデータベースにバインドされたリソース プールから、メモリ最適化テーブルおよびインデックス用のメモリが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b499f-152">If your database was bound to an a different pool earlier, this removes the allocated memory from the previous resource pool and memory allocations for your memory-optimized table and indexes will now come from the resource pool newly bound with the database.</span></span>  
  
```sql  
USE master  
GO  
  
ALTER DATABASE IMOLTP_DB SET OFFLINE  
GO  
ALTER DATABASE IMOLTP_DB SET ONLINE  
GO  
  
USE IMOLTP_DB  
GO  
```  
  
 <span data-ttu-id="b499f-153">これで、データベースがリソース プールにバインドされました。</span><span class="sxs-lookup"><span data-stu-id="b499f-153">And now, the database is bound to the resource pool.</span></span>  
  
## <a name="change-min-memory-percent-and-max-memory-percent-on-an-existing-pool"></a><span data-ttu-id="b499f-154">既存のプールの最小メモリの割合と最大メモリの割合を変更する</span><span class="sxs-lookup"><span data-stu-id="b499f-154">Change MIN MEMORY PERCENT and MAX MEMORY PERCENT on an existing pool</span></span>  
 <span data-ttu-id="b499f-155">サーバーにメモリを追加した場合や、メモリ最適化テーブルに必要なメモリの量が変わった場合は、MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の値を変更する必要があることがあります。</span><span class="sxs-lookup"><span data-stu-id="b499f-155">If you add additional memory to the server or the amount of memory needed for your memory-optimized tables changes, you may need to alter the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span> <span data-ttu-id="b499f-156">次の手順では、リソース プールで MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の値を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b499f-156">The following steps show you how to alter the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on a resource pool.</span></span> <span data-ttu-id="b499f-157">MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT に使用する値については、以下のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b499f-157">See the section below, for guidance on what values to use for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span>  <span data-ttu-id="b499f-158">詳細については、「[ベストプラクティス: VM 環境でのインメモリ OLTP の使用](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b499f-158">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
1.  <span data-ttu-id="b499f-159">`ALTER RESOURCE POOL` を使用して MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の両方の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="b499f-159">Use `ALTER RESOURCE POOL` to change the value of both MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span>  
  
2.  <span data-ttu-id="b499f-160">新しい値を使用してリソース ガバナーを再構成するには、 `ALTER RESURCE GOVERNOR` を使用します。</span><span class="sxs-lookup"><span data-stu-id="b499f-160">Use `ALTER RESURCE GOVERNOR` to reconfigure the Resource Governor with the new values.</span></span>  
  
 <span data-ttu-id="b499f-161">**サンプル コード**</span><span class="sxs-lookup"><span data-stu-id="b499f-161">**Sample Code**</span></span>  
  
```sql  
ALTER RESOURCE POOL Pool_IMOLTP  
WITH  
     ( MIN_MEMORY_PERCENT = 70,  
       MAX_MEMORY_PERCENT = 70 )   
GO  
  
-- reconfigure the Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
```  
  
## <a name="percent-of-memory-available-for-memory-optimized-tables-and-indexes"></a><span data-ttu-id="b499f-162">メモリ最適化テーブルおよびインデックスで使用可能なメモリの割合</span><span class="sxs-lookup"><span data-stu-id="b499f-162">Percent of memory available for memory-optimized tables and indexes</span></span>  
 <span data-ttu-id="b499f-163">メモリ最適化テーブルを持つデータベースと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ワークロードを同じリソース プールにマップした場合は、プールのユーザー間でプール使用に関する競合が生じないように、リソース ガバナーによって [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 用の内部しきい値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="b499f-163">If you map a database with memory-optimized tables and a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] workload to the same resource pool, the Resource Governor sets an internal threshold for [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] use so that the users of the pool do not have conflicts over pool usage.</span></span> <span data-ttu-id="b499f-164">一般に、 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 用のしきい値はプールの約 80% です。</span><span class="sxs-lookup"><span data-stu-id="b499f-164">Generally speaking, the threshold for [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] use is about 80% of the pool.</span></span> <span data-ttu-id="b499f-165">さまざまなメモリ サイズに対する実際のしきい値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b499f-165">The following table shows actual thresholds for various memory sizes.</span></span>  
  
 <span data-ttu-id="b499f-166">[!INCLUDE[hek_2](../../../includes/hek-2-md.md)] データベースの専用リソース プールを作成するときは、行のバージョンとデータの増加を確認した後で、インメモリ テーブルに必要な物理メモリ量を推定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b499f-166">When you create a dedicated resource pool for the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] database, you need to estimate how much physical memory you need for the in-memory tables after accounting for row versions and data growth.</span></span> <span data-ttu-id="b499f-167">必要なメモリ量を推定したら、DMV の `sys.dm_os_sys_info` の列 "committed_target_kb" を反映する SQL インスタンスのコミット ターゲット メモリの割合でリソース プールを作成します ([sys.dm_os_sys_info](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql) を参照)。</span><span class="sxs-lookup"><span data-stu-id="b499f-167">Once estimate the memory needed, you create a resource pool with a percent of the commit target memory for SQL Instance as reflected by column 'committed_target_kb' in the DMV `sys.dm_os_sys_info` (see [sys.dm_os_sys_info](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql)).</span></span> <span data-ttu-id="b499f-168">たとえば、インスタンスで使用できる合計メモリ量の 40% を含むリソース プール P1 を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b499f-168">For example, you can create a resource pool P1 with 40% of the total memory available to the instance.</span></span> <span data-ttu-id="b499f-169">この 40% から、 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] エンジンは [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] データを格納するためにこれより少ない割合のメモリを取得します。</span><span class="sxs-lookup"><span data-stu-id="b499f-169">Out of this 40%, the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine gets a smaller percent to store [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] data.</span></span>  <span data-ttu-id="b499f-170">この処理は、 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] がこのプールのすべてのメモリを消費しないようにするために行います。</span><span class="sxs-lookup"><span data-stu-id="b499f-170">This is done to make sure [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] does not consume all the memory from this pool.</span></span>  <span data-ttu-id="b499f-171">この少ない割合の値は、ターゲットのコミット済みメモリによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b499f-171">This value of the smaller percent depends upon the Target committed Memory.</span></span> <span data-ttu-id="b499f-172">次の表に、OOM のエラーが発生する前にリソース プール (既定または名前付き) の [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] データベースに使用可能なメモリを示します。</span><span class="sxs-lookup"><span data-stu-id="b499f-172">The following table describes memory available to [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] database in a resource pool (named or default) before an OOM error is raised.</span></span>  
  
|<span data-ttu-id="b499f-173">ターゲットのコミット済みメモリ</span><span class="sxs-lookup"><span data-stu-id="b499f-173">Target Committed Memory</span></span>|<span data-ttu-id="b499f-174">インメモリ テーブルで使用可能な割合</span><span class="sxs-lookup"><span data-stu-id="b499f-174">Percent available for in-memory tables</span></span>|  
|-----------------------------|---------------------------------------------|  
|<span data-ttu-id="b499f-175"><= 8 GB</span><span class="sxs-lookup"><span data-stu-id="b499f-175"><= 8 GB</span></span>|<span data-ttu-id="b499f-176">70%</span><span class="sxs-lookup"><span data-stu-id="b499f-176">70%</span></span>|  
|<span data-ttu-id="b499f-177"><= 16 GB</span><span class="sxs-lookup"><span data-stu-id="b499f-177"><= 16 GB</span></span>|<span data-ttu-id="b499f-178">75%</span><span class="sxs-lookup"><span data-stu-id="b499f-178">75%</span></span>|  
|<span data-ttu-id="b499f-179"><= 32 GB</span><span class="sxs-lookup"><span data-stu-id="b499f-179"><= 32 GB</span></span>|<span data-ttu-id="b499f-180">80%</span><span class="sxs-lookup"><span data-stu-id="b499f-180">80%</span></span>|  
|<span data-ttu-id="b499f-181">\<= 96 GB</span><span class="sxs-lookup"><span data-stu-id="b499f-181">\<= 96 GB</span></span>|<span data-ttu-id="b499f-182">85%</span><span class="sxs-lookup"><span data-stu-id="b499f-182">85%</span></span>|  
|<span data-ttu-id="b499f-183">>96 GB</span><span class="sxs-lookup"><span data-stu-id="b499f-183">>96 GB</span></span>|<span data-ttu-id="b499f-184">90%</span><span class="sxs-lookup"><span data-stu-id="b499f-184">90%</span></span>|  
  
 <span data-ttu-id="b499f-185">たとえば、"ターゲットのコミット済みメモリ" が 100 GB で、メモリ最適化テーブルおよびインデックスに 60 GB のメモリが必要であると推定した場合は、MAX_MEMORY_PERCENT = 67 (必要な 60 GB/0.90 = 66.667 GB – 67 GB に切り上げ、67 GB/インストール済みの 100 GB = 67%) でリソース プールを作成して、[!INCLUDE[hek_2](../../../includes/hek-2-md.md)] オブジェクトで必要な 60 GB を確実に使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b499f-185">For example, if your 'target committed memory' is 100 GB, and you estimate your memory-optimized tables and indexes need 60GBof memory, then you can create a resource pool with MAX_MEMORY_PERCENT = 67 (60GB needed / 0.90 = 66.667GB - round up to 67GB; 67GB / 100GB installed = 67%) to ensure that your [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] objects have the 60GB they need.</span></span>  
  
 <span data-ttu-id="b499f-186">データベースが名前付きリソース プールにバインドされている場合は、次のクエリを使用して異なるリソース プールにわたるメモリ割り当てを確認します。</span><span class="sxs-lookup"><span data-stu-id="b499f-186">Once a database has been bound to a named resource pool, use the following query to see memory allocations across different resource pools.</span></span>  
  
```sql  
SELECT pool_id  
     , Name  
     , min_memory_percent  
     , max_memory_percent  
     , max_memory_kb/1024 AS max_memory_mb  
     , used_memory_kb/1024 AS used_memory_mb   
     , target_memory_kb/1024 AS target_memory_mb  
   FROM sys.dm_resource_governor_resource_pools  
```  
  
 <span data-ttu-id="b499f-187">このサンプル出力は、メモリ最適化オブジェクトによって使用されたメモリがリソース プール、PoolIMOLTP の 1356 MB であり、上限が 2307 MB であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="b499f-187">This sample output shows that the memory taken by memory-optimized objects is 1356 MB in resource pool, PoolIMOLTP, with an upper bound of 2307 MB.</span></span> <span data-ttu-id="b499f-188">この上限によって、ユーザーとこのプールにマップされるシステムのメモリ最適化オブジェクトが使用できるメモリの合計が制御されます。</span><span class="sxs-lookup"><span data-stu-id="b499f-188">This upper bound controls the total memory that can be taken by user and system memory-optimized objects mapped to this pool.</span></span>  
  
 <span data-ttu-id="b499f-189">**サンプル出力** </span><span class="sxs-lookup"><span data-stu-id="b499f-189">**Sample Output** </span></span>  
<span data-ttu-id="b499f-190">この出力は、上で作成したデータベースおよびテーブルからのものです。</span><span class="sxs-lookup"><span data-stu-id="b499f-190">This output is from the database and tables we created above.</span></span>  
  
```  
pool_id     Name        min_memory_percent max_memory_percent max_memory_mb used_memory_mb target_memory_mb  
----------- ----------- ------------------ ------------------ ------------- -------------- ----------------   
1           internal    0                  100                3845          125            3845  
2           default     0                  100                3845          32             3845  
259         PoolIMOLTP 0                  100                3845          1356           2307  
```  
  
 <span data-ttu-id="b499f-191">詳細については、「 [sys.dm_resource_governor_resource_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b499f-191">For more information see [sys.dm_resource_governor_resource_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql).</span></span>  
  
 <span data-ttu-id="b499f-192">ご利用のデータベースを名前付きリソース プールにバインドしない場合、そのデータベースは "既定の" プールにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="b499f-192">If you do not bind your database to a named resource pool, it is bound to the 'default' pool.</span></span> <span data-ttu-id="b499f-193">既定のリソース プールは他のほとんどの割り当ての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用されるため、正確に対象のデータベースに対して DMV sys.dm_resource_governor_resource_pools を使用して、メモリ最適化テーブルで消費されたメモリを監視することはできません。</span><span class="sxs-lookup"><span data-stu-id="b499f-193">Since default resource pool is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for most other allocations, you will not be able to monitor memory consumed by memory-optimized tables using the DMV sys.dm_resource_governor_resource_pools accurately for the database of interest.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b499f-194">参照</span><span class="sxs-lookup"><span data-stu-id="b499f-194">See Also</span></span>  
 <span data-ttu-id="b499f-195">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b499f-195">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="b499f-196">[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b499f-196">[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="b499f-197">[リソース ガバナー](../resource-governor/resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="b499f-197">[Resource Governor](../resource-governor/resource-governor.md) </span></span>  
 <span data-ttu-id="b499f-198">[リソース ガバナー リソース プール](../resource-governor/resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="b499f-198">[Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="b499f-199">[リソース プールの作成](../resource-governor/create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="b499f-199">[Create a Resource Pool](../resource-governor/create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="b499f-200">[リソース プールの設定の変更](../resource-governor/change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="b499f-200">[Change Resource Pool Settings](../resource-governor/change-resource-pool-settings.md) </span></span>  
 [<span data-ttu-id="b499f-201">リソース プールの削除</span><span class="sxs-lookup"><span data-stu-id="b499f-201">Delete a Resource Pool</span></span>](../resource-governor/delete-a-resource-pool.md)  
  
  
