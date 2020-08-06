---
title: データベースの完全バックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backups [SQL Server], database
- backing up databases [SQL Server], full backups
- estimating database backup size
- backing up [SQL Server], size of backup
- database backups [SQL Server], full backups
- size [SQL Server], backups
- database backups [SQL Server], about backing up databases
ms.assetid: 4d933d19-8d21-4aa1-8153-d230cb3a3f99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ee871b6cabbe6c2b2cb4f444fd1e2d42d711dfbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715438"
---
# <a name="full-database-backups-sql-server"></a><span data-ttu-id="ff450-102">データベースの完全バックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ff450-102">Full Database Backups (SQL Server)</span></span>
  <span data-ttu-id="ff450-103">データベースの完全バックアップでは、データベース全体をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="ff450-103">A full database backup backs up the whole database.</span></span> <span data-ttu-id="ff450-104">このバックアップにはトランザクション ログの一部が含まれるため、データベースの完全バックアップを復元した後に、データベース全体を復旧することができます。</span><span class="sxs-lookup"><span data-stu-id="ff450-104">This includes part of the transaction log so that the full database can be recovered after a full database backup is restored.</span></span> <span data-ttu-id="ff450-105">データベースの完全バックアップは、バックアップが完了した時点でのデータベースを表します。</span><span class="sxs-lookup"><span data-stu-id="ff450-105">Full database backups represent the database at the time the backup finished.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="ff450-106">データベース サイズが大きくなると、データベースの完全バックアップにかかる時間は長くなり、必要な記憶領域も増加します。</span><span class="sxs-lookup"><span data-stu-id="ff450-106">As a database increases in size full database backups take more time to finish and require more storage space.</span></span> <span data-ttu-id="ff450-107">このため、大きなデータベースの場合は、データベースの完全バックアップを一連の *差分データベース バックアップ*で補完することができます。</span><span class="sxs-lookup"><span data-stu-id="ff450-107">Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*.</span></span> <span data-ttu-id="ff450-108">詳細については、「 [差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff450-108">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ff450-109">データベースをバックアップすると、TRUSTWORTHY は OFF に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff450-109">TRUSTWORTHY is set to OFF on a database backup.</span></span> <span data-ttu-id="ff450-110">TRUSTWORTHY を ON に設定する方法については「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff450-110">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="ff450-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ff450-111">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="ff450-112">単純復旧モデルでのデータベース バックアップ</span><span class="sxs-lookup"><span data-stu-id="ff450-112">Database Backups Under the Simple Recovery Model</span></span>](#DbBuRMs)  
  
-   [<span data-ttu-id="ff450-113">完全復旧モデルでのデータベース バックアップ</span><span class="sxs-lookup"><span data-stu-id="ff450-113">Database Backups Under the Full Recovery Model</span></span>](#DbBuRMf)  
  
-   [<span data-ttu-id="ff450-114">データベースの完全バックアップを使用したデータベースの復元</span><span class="sxs-lookup"><span data-stu-id="ff450-114">Use a Full Database Backup to Restore the Database</span></span>](#RestoreDbBu)  
  
-   [<span data-ttu-id="ff450-115">関連タスク</span><span class="sxs-lookup"><span data-stu-id="ff450-115">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="database-backups-under-the-simple-recovery-model"></a><a name="DbBuRMs"></a> <span data-ttu-id="ff450-116">単純復旧モデルでのデータベース バックアップ</span><span class="sxs-lookup"><span data-stu-id="ff450-116">Database Backups Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="ff450-117">単純復旧モデルでは、データベースをバックアップした後に障害が発生すると、その間の作業内容が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff450-117">Under the simple recovery model, after each backup, the database is exposed to potential work loss if a disaster were to occur.</span></span> <span data-ttu-id="ff450-118">作業損失の可能性は、次のバックアップまで、データを更新するたびに増加します。次の完全バックアップで作業損失の可能性はゼロに戻り、そこから再び増加していきます。</span><span class="sxs-lookup"><span data-stu-id="ff450-118">The work-loss exposure increases with each update until the next backup, when the work-loss exposure returns to zero and a new cycle of work-loss exposure starts.</span></span> <span data-ttu-id="ff450-119">作業損失の可能性は、バックアップ間の時間が増加します。</span><span class="sxs-lookup"><span data-stu-id="ff450-119">Work-loss exposure increases over time between backups.</span></span> <span data-ttu-id="ff450-120">次の図に、データベースの完全バックアップのみを使用するバックアップ方法における作業損失の可能性を示します。</span><span class="sxs-lookup"><span data-stu-id="ff450-120">The following illustration shows the work-loss exposure for a backup strategy that uses only full database backups.</span></span>  
  
 <span data-ttu-id="ff450-121">![データベース バックアップ間での作業損失の可能性](../../database-engine/media/bnr-rmsimple-1-fulldb-backups.gif "データベース バックアップ間での作業損失の可能性")</span><span class="sxs-lookup"><span data-stu-id="ff450-121">![Shows work-loss exposure between database backups](../../database-engine/media/bnr-rmsimple-1-fulldb-backups.gif "Shows work-loss exposure between database backups")</span></span>  
  
### <a name="example--tsql"></a><span data-ttu-id="ff450-122">例 ([!INCLUDE[tsql](../../../includes/tsql-md.md)])</span><span class="sxs-lookup"><span data-stu-id="ff450-122">Example ( [!INCLUDE[tsql](../../../includes/tsql-md.md)])</span></span>  
 <span data-ttu-id="ff450-123">次の例では、WITH FORMAT を使用してデータベースの完全バックアップを作成することにより、既存のバックアップを上書きして新しいメディア セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff450-123">The following example shows how to create a full database backup by using WITH FORMAT to overwrite any existing backups and create a new media set.</span></span>  
  
```  
-- Back up the AdventureWorks2012 database to new media set.  
BACKUP DATABASE AdventureWorks2012  
    TO DISK = 'Z:\SQLServerBackups\AdventureWorksSimpleRM.bak'   
    WITH FORMAT;  
GO  
```  
  
##  <a name="database-backups-under-the-full-recovery-model"></a><a name="DbBuRMf"></a> <span data-ttu-id="ff450-124">完全復旧モデルでのデータベース バックアップ</span><span class="sxs-lookup"><span data-stu-id="ff450-124">Database Backups Under the Full Recovery Model</span></span>  
 <span data-ttu-id="ff450-125">完全復旧と一括ログ復旧を使用するデータベースには、データベース バックアップが必要です。ただし、それだけでは十分とは言えません。</span><span class="sxs-lookup"><span data-stu-id="ff450-125">For databases that use full and bulk-logged recovery, database backups are necessary but not sufficient.</span></span> <span data-ttu-id="ff450-126">トランザクション ログのバックアップも必要です。</span><span class="sxs-lookup"><span data-stu-id="ff450-126">Transaction log backups are also required.</span></span> <span data-ttu-id="ff450-127">次の図に、完全復旧モデルで可能な限り単純化したバックアップ方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ff450-127">The following illustration shows the least complex backup strategy that is possible under the full recovery model.</span></span>  
  
 <span data-ttu-id="ff450-128">![一連の完全データベース バックアップとログ バックアップ](../../database-engine/media/bnr-rmfull-1-fulldb-log-backups.gif "一連の完全データベース バックアップとログ バックアップ")</span><span class="sxs-lookup"><span data-stu-id="ff450-128">![Series of full database backups and log backups](../../database-engine/media/bnr-rmfull-1-fulldb-log-backups.gif "Series of full database backups and log backups")</span></span>  
  
 <span data-ttu-id="ff450-129">ログのバックアップを作成する方法については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff450-129">For information about how to create log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
### <a name="example--tsql"></a><span data-ttu-id="ff450-130">例 ([!INCLUDE[tsql](../../../includes/tsql-md.md)])</span><span class="sxs-lookup"><span data-stu-id="ff450-130">Example ( [!INCLUDE[tsql](../../../includes/tsql-md.md)])</span></span>  
 <span data-ttu-id="ff450-131">次の例では、WITH FORMAT を使用してデータベースの完全バックアップを作成することにより、既存のバックアップを上書きして新しいメディア セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff450-131">The following example shows how to create a full database backup by using WITH FORMAT to overwrite any existing backups and create a new media set.</span></span> <span data-ttu-id="ff450-132">その後、トランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="ff450-132">Then, the example backs up the transaction log.</span></span> <span data-ttu-id="ff450-133">実際の状況では、一連の定期的なログ バックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff450-133">In a real-life situation, you would have to perform a series of regular log backups.</span></span> <span data-ttu-id="ff450-134">この例では、完全復旧モデルが使用されるように [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="ff450-134">For this example, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database is set to use the full recovery model.</span></span>  
  
```  
USE master;  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
GO  
-- Back up the AdventureWorks2012 database to new media set (backup set 1).  
BACKUP DATABASE AdventureWorks2012  
  TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012FullRM.bak'   
  WITH FORMAT;  
GO  
--Create a routine log backup (backup set 2).  
BACKUP LOG AdventureWorks2012 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012FullRM.bak';  
GO  
```  
  
##  <a name="use-a-full-database-backup-to-restore-the-database"></a><a name="RestoreDbBu"></a> <span data-ttu-id="ff450-135">データベースの完全バックアップを使用したデータベースの復元</span><span class="sxs-lookup"><span data-stu-id="ff450-135">Use a Full Database Backup to Restore the Database</span></span>  
 <span data-ttu-id="ff450-136">データベースを復元することによって、データベースの完全バックアップからワン ステップで任意の場所にデータベース全体を再作成できます。</span><span class="sxs-lookup"><span data-stu-id="ff450-136">You can re-create a whole database in one step by restoring the database from a full database backup to any location.</span></span> <span data-ttu-id="ff450-137">データベースの完全バックアップには、バックアップ完了時までデータベースを復旧するのに十分なトランザクション ログが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ff450-137">Enough of the transaction log is included in the backup to let you recover the database to the time when the backup finished.</span></span> <span data-ttu-id="ff450-138">復元されたデータベースは、データベース バックアップが完了した時点の元のデータベースの状態から、コミットされていないトランザクションを差し引いた状態と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff450-138">The restored database matches the state of the original database when the database backup finished, minus any uncommitted transactions.</span></span> <span data-ttu-id="ff450-139">完全復旧モデルでは、さらに、後続のすべてのトランザクション ログ バックアップを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff450-139">Under the full recovery model, you should then restore all subsequent transaction log backups.</span></span> <span data-ttu-id="ff450-140">データベースが復旧されると、コミットされていないトランザクションはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="ff450-140">When the database is recovered, uncommitted transactions are rolled back.</span></span>  
  
 <span data-ttu-id="ff450-141">詳細については、「[データベースの全体復元 &#40;単純復旧モデル&#41;](complete-database-restores-simple-recovery-model.md)」または「[データベースの全体復元 &#40;完全復旧モデル&#41;](complete-database-restores-full-recovery-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff450-141">For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) or [Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ff450-142">関連タスク</span><span class="sxs-lookup"><span data-stu-id="ff450-142">Related Tasks</span></span>  
 <span data-ttu-id="ff450-143">**データベースの完全バックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="ff450-143">**To create a full database backup**</span></span>  
  
-   [<span data-ttu-id="ff450-144">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff450-144">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   <span data-ttu-id="ff450-145"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="ff450-145"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
 <span data-ttu-id="ff450-146">**バックアップ ジョブのスケジュールを設定するには**</span><span class="sxs-lookup"><span data-stu-id="ff450-146">**To schedule backup jobs**</span></span>  
  
 [<span data-ttu-id="ff450-147">メンテナンス プラン ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="ff450-147">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="ff450-148">参照</span><span class="sxs-lookup"><span data-stu-id="ff450-148">See Also</span></span>  
 <span data-ttu-id="ff450-149">[SQL Server データベースのバックアップと復元](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="ff450-149">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="ff450-150">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ff450-150">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="ff450-151">Analysis Services データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="ff450-151">Backup and Restore of Analysis Services Databases</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
  
