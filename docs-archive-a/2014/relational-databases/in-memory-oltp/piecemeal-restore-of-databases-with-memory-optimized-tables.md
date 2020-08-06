---
title: メモリ最適化テーブルを持つデータベースの段階的な部分復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 732c9721-8dd4-481d-8ff9-1feaaa63f84f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ed23f08d40e23b1d43c1b642f4089fe77646b675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738376"
---
# <a name="piecemeal-restore-of-databases-with-memory-optimized-tables"></a><span data-ttu-id="54e6d-102">メモリ最適化テーブルを持つデータベースの段階的な部分復元</span><span class="sxs-lookup"><span data-stu-id="54e6d-102">Piecemeal Restore of Databases With Memory-Optimized Tables</span></span>
  <span data-ttu-id="54e6d-103">段階的な部分復元は、次に説明する 1 つの制限を除き、メモリ最適化テーブルを持つデータベースでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="54e6d-103">Piecemeal restore is supported on databases with memory-optimized tables except for one restriction described below.</span></span> <span data-ttu-id="54e6d-104">段階的なバックアップと部分復元の詳細については、「[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)」および「 [段階的な部分復元 &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e6d-104">For more information about piecemeal backup and restore, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [Piecemeal Restores &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).</span></span>  
  
 <span data-ttu-id="54e6d-105">メモリ最適化ファイル グループは、プライマリ ファイル グループと共にバックアップおよび復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e6d-105">A memory-optimized filegroup must be backed up and restored together with the primary filegroup:</span></span>  
  
-   <span data-ttu-id="54e6d-106">プライマリ ファイル グループをバックアップ (または復元) するときは、メモリ最適化ファイル グループを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e6d-106">If you back up (or restore) the primary filegroup you must specify the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="54e6d-107">メモリ最適化ファイル グループをバックアップ (または復元) するときは、プライマリ ファイル グループを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e6d-107">If you backup (or restore) the memory-optimized filegroup you must specify the primary filegroup.</span></span>  
  
 <span data-ttu-id="54e6d-108">段階的なバックアップと部分復元に関する主要なシナリオは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54e6d-108">Key scenarios for piecemeal backup and restore are,</span></span>  
  
-   <span data-ttu-id="54e6d-109">段階的なバックアップを使用すると、バックアップのサイズを小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="54e6d-109">Piecemeal backup allows you to reduce the size of backup.</span></span> <span data-ttu-id="54e6d-110">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="54e6d-110">Some examples:</span></span>  
  
    -   <span data-ttu-id="54e6d-111">異なる時刻または日にデータベースのバックアップを実行するように構成し、ワークロードに及ぼす影響を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="54e6d-111">Configure the database backup to occur at different times or days to minimize the impact on the workload.</span></span> <span data-ttu-id="54e6d-112">1 つの例は、割り当てられるデータベースのメンテナンス時間内にデータベースの完全バックアップを完了することができない、非常に大規模なデータベース (1 TB 以上) です。</span><span class="sxs-lookup"><span data-stu-id="54e6d-112">One example is a very large database (greater than 1 TB) where a full database backup cannot complete in the time allocated for database maintenance.</span></span> <span data-ttu-id="54e6d-113">この状況では、段階的なバックアップを使用し、データベース全体を分割して複数の段階的なバックアップの対象にすることができます。</span><span class="sxs-lookup"><span data-stu-id="54e6d-113">In that situation, you can use piecemeal backup to backup the full database in multiple piecemeal backups.</span></span>  
  
    -   <span data-ttu-id="54e6d-114">ファイル グループに読み取り専用のマークが付けられている場合は、読み取り専用というマークを付けられた時点より後のトランザクション ログをバックアップする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="54e6d-114">If a filegroup is marked read-only, it does not require a transaction log backup after it was marked read-only.</span></span> <span data-ttu-id="54e6d-115">読み取り専用というマークが付けられた後、そのファイル グループを 1 回だけバックアップする方針を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="54e6d-115">You can choose to back up the filegroup only once after marking it read-only.</span></span>  
  
-   <span data-ttu-id="54e6d-116">段階的な部分復元</span><span class="sxs-lookup"><span data-stu-id="54e6d-116">Piecemeal restore.</span></span>  
  
    -   <span data-ttu-id="54e6d-117">段階的な部分復元の目標は、すべてのデータを待つことなく、データベースの重要な部分のみをオンライン状態にすることです。</span><span class="sxs-lookup"><span data-stu-id="54e6d-117">The goal of a piecemeal restore is to bring the critical parts of database online without waiting for all the data.</span></span> <span data-ttu-id="54e6d-118">1 つの例は、データベース内にパーティション化されたデータが存在していて、古いパーティションはほとんど使用されていない状況です。</span><span class="sxs-lookup"><span data-stu-id="54e6d-118">One example is if a database has partitioned data, such that older partitions are only used rarely.</span></span> <span data-ttu-id="54e6d-119">そのようなパーティションは、必要な場合のみ復元することができます。</span><span class="sxs-lookup"><span data-stu-id="54e6d-119">You can restore them only on an as-needed basis.</span></span> <span data-ttu-id="54e6d-120">同様に、履歴データを含むファイル グループもこれに似ています。</span><span class="sxs-lookup"><span data-stu-id="54e6d-120">Similar for filegroups that contain, for example, historical data.</span></span>  
  
    -   <span data-ttu-id="54e6d-121">ページ修復機能を使用して、特定のページを復元することにより、ページ破損を修正することもできます。</span><span class="sxs-lookup"><span data-stu-id="54e6d-121">Using page repair, you can fix page corruption by specifically restoring the page.</span></span> <span data-ttu-id="54e6d-122">詳細については、「[ページ復元 &#40;SQL Server&#41;](../backup-restore/restore-pages-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e6d-122">For more information, see [Restore Pages &#40;SQL Server&#41;](../backup-restore/restore-pages-sql-server.md).</span></span>  
  
## <a name="samples"></a><span data-ttu-id="54e6d-123">サンプル</span><span class="sxs-lookup"><span data-stu-id="54e6d-123">Samples</span></span>  
 <span data-ttu-id="54e6d-124">次の例では、以下のスキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="54e6d-124">The examples use the following schema:</span></span>  
  
```  
CREATE DATABASE imoltp  
ON PRIMARY (name = imoltp_primary1, filename = 'c:\data\imoltp_data1.mdf')  
LOG ON (name = imoltp_log, filename = 'c:\data\imoltp_log.ldf')  
GO  
  
ALTER DATABASE imoltp ADD FILE (name = imoltp_primary2, filename = 'c:\data\imoltp_data2.ndf')  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_secondary  
ALTER DATABASE imoltp ADD FILE (name = imoltp_secondary, filename = 'c:\data\imoltp_secondary.ndf') TO FILEGROUP imoltp_secondary  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod2', filename='c:\data\imoltp_mod2') TO FILEGROUP imoltp_mod   
GO  
```  
  
### <a name="backup"></a><span data-ttu-id="54e6d-125">バックアップ</span><span class="sxs-lookup"><span data-stu-id="54e6d-125">Backup</span></span>  
 <span data-ttu-id="54e6d-126">このサンプルでは、プライマリ ファイル グループとメモリ最適化ファイル グループをバックアップする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="54e6d-126">This sample shows how to backup the primary filegroup and the memory-optimized filegroup.</span></span> <span data-ttu-id="54e6d-127">プライマリ ファイル グループとメモリ最適化ファイル グループの両方を共に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e6d-127">You must specify both primary and memory-optimized filegroup together.</span></span>  
  
```  
backup database imoltp filegroup='primary', filegroup='imoltp_mod' to disk='c:\data\imoltp.dmp' with init  
```  
  
 <span data-ttu-id="54e6d-128">次のサンプルでは、プライマリ ファイル グループとメモリ最適化ファイル グループのどちらでもないファイル グループのバックアップが、メモリ最適化テーブルの存在しないデータベースを操作する状況に似ていることを示します。</span><span class="sxs-lookup"><span data-stu-id="54e6d-128">The following sample shows that a back up of filegroup(s) other than primary and memory-optimized filegroup works similar to the databases without memory-optimized tables.</span></span> <span data-ttu-id="54e6d-129">次のコマンドを使用して、セカンダリ ファイル グループをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="54e6d-129">The following command backups up the secondary filegroup</span></span>  
  
```  
backup database imoltp filegroup='imoltp_secondary' to disk='c:\data\imoltp_secondary.dmp' with init  
```  
  
### <a name="restore"></a><span data-ttu-id="54e6d-130">復元</span><span class="sxs-lookup"><span data-stu-id="54e6d-130">Restore</span></span>  
 <span data-ttu-id="54e6d-131">次のサンプルでは、プライマリ ファイル グループとメモリ最適化ファイル グループを共に復元する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="54e6d-131">The following sample shows how to restore the primary filegroup and memory-optimized filegroup together.</span></span>  
  
```  
restore database imoltp filegroup = 'primary', filegroup = 'imoltp_mod'   
from disk='c:\data\imoltp.dmp' with partial, norecovery  
  
--restore the transaction log  
 RESTORE LOG [imoltp] FROM DISK = N'c:\data\imoltp_log.dmp' WITH  FILE = 1,  NOUNLOAD,  STATS = 10  
GO  
```  
  
 <span data-ttu-id="54e6d-132">次のサンプルでは、プライマリ ファイル グループとメモリ最適化ファイル グループのどちらでもないファイル グループの復元が、メモリ最適化テーブルの存在しないデータベースを操作する状況に似ていることを示します。</span><span class="sxs-lookup"><span data-stu-id="54e6d-132">The next sample shows that restoring filegroup(s) other than the primary and memory-optimized filegroup works similar to the databases without memory-optimized tables</span></span>  
  
```  
RESTORE DATABASE [imoltp] FILE = N'imoltp_secondary'   
FROM  DISK = N'c:\data\imoltp_secondary.dmp' WITH  FILE = 1,  RECOVERY,  NOUNLOAD,  STATS = 10  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="54e6d-133">参照</span><span class="sxs-lookup"><span data-stu-id="54e6d-133">See Also</span></span>  
 [<span data-ttu-id="54e6d-134">メモリ最適化テーブルのバックアップ、復元、復旧</span><span class="sxs-lookup"><span data-stu-id="54e6d-134">Backup, Restore, and Recovery of Memory-Optimized Tables</span></span>](../../database-engine/backup-restore-and-recovery-of-memory-optimized-tables.md)  
  
  
