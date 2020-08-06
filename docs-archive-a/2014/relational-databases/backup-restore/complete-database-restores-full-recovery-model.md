---
title: データベースの全体復元 (完全復旧モデル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- restoring [SQL Server], database
- full recovery model [SQL Server], performing restores
- log backups [SQL Server[
ms.assetid: 5b4c471c-b972-498e-aba9-92cf7a0ea881
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea6ec9f196acd0a64a0b785024bd6426cd6a5381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645687"
---
# <a name="complete-database-restores-full-recovery-model"></a><span data-ttu-id="6eb89-102">データベースの全体復元 (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="6eb89-102">Complete Database Restores (Full Recovery Model)</span></span>
  <span data-ttu-id="6eb89-103">データベースの全体復元の目的は、データベース全体を復元することです。</span><span class="sxs-lookup"><span data-stu-id="6eb89-103">In a complete database restore, the goal is to restore the whole database.</span></span> <span data-ttu-id="6eb89-104">復元の実行中は、データベース全体がオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="6eb89-104">The whole database is offline for the duration of the restore.</span></span> <span data-ttu-id="6eb89-105">データベースの各部がオンラインになる前に、すべてのデータが一貫性のある状態に復旧されます。一貫性のある状態とは、データベースのすべての部分が同じ時点にあり、コミットされていないトランザクションが存在しない状態を示します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-105">Before any part of the database can come online, all data is recovered to a consistent point in which all parts of the database are at the same point in time and no uncommitted transactions exist.</span></span>  
  
 <span data-ttu-id="6eb89-106">完全復旧モデルでは、1 つまたは複数のデータ バックアップを復元した後、それ以降のトランザクション ログ バックアップをすべて復元してから、データベースを復旧する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6eb89-106">Under the full recovery model, after you restore your data backup or backups, you must restore all subsequent transaction log backups and then recover the database.</span></span> <span data-ttu-id="6eb89-107">そのいずれかのログ バックアップ内の特定の *復旧ポイント* までデータベースを復元することができます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-107">You can restore a database to a specific *recovery point* within one of these log backups.</span></span> <span data-ttu-id="6eb89-108">復旧ポイントとは、特定の日時、マークされたトランザクション、またはログ シーケンス番号 (LSN) を指します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-108">The recovery point can be a specific date and time, a marked transaction, or a log sequence number (LSN).</span></span>  
  
 <span data-ttu-id="6eb89-109">特に完全復旧モデルと一括ログ復旧モデルでは、データベースを復元するときに、単一の復元シーケンスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6eb89-109">When restoring a database, particularly under the full recovery model or bulk-logged recovery model, you should use a single restore sequence.</span></span> <span data-ttu-id="6eb89-110">*復元シーケンス* は、1 つ以上の復元フェーズによってデータを移動する、1 つ以上の復元操作で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-110">A *restore sequence* consists of one or more restore operations that move data through one or more of the phases of restore.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6eb89-111">不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6eb89-111">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="6eb89-112">そのようなデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更することによりエラーを発生させる悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6eb89-112">These databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="6eb89-113">不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-113">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
 <span data-ttu-id="6eb89-114">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6eb89-114">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="6eb89-115">障害発生時点へのデータベースの復元</span><span class="sxs-lookup"><span data-stu-id="6eb89-115">Restoring a Database to the Point of Failure</span></span>](#PointOfFailure)  
  
-   [<span data-ttu-id="6eb89-116">ログバックアップ内の特定の時点へのデータベースの復元</span><span class="sxs-lookup"><span data-stu-id="6eb89-116">Restoring a Database to a Point Within a Log Backup</span></span>](#PointWithinBackup)  
  
-   [<span data-ttu-id="6eb89-117">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6eb89-117">Related Tasks</span></span>](#RelatedTasks)  
  
> [!NOTE]  
>  <span data-ttu-id="6eb89-118">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からのバックアップに対するサポートの情報については、「 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)」の「互換性サポート」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eb89-118">For information about support for backups from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the "Compatibility Support" section of [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="restoring-a-database-to-the-point-of-failure"></a><a name="PointOfFailure"></a> <span data-ttu-id="6eb89-119">障害発生時点へのデータベースの復旧</span><span class="sxs-lookup"><span data-stu-id="6eb89-119">Restoring a Database to the Point of Failure</span></span>  
 <span data-ttu-id="6eb89-120">通常、障害が発生した時点までデータベースを復旧するには、次の基本的な手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="6eb89-120">Typically, recovering a database to the point of failure involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="6eb89-121">アクティブなトランザクション ログ (ログの末尾と呼ばれます) をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="6eb89-121">Back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="6eb89-122">これにより、ログ末尾のバックアップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-122">This creates a tail-log backup.</span></span> <span data-ttu-id="6eb89-123">アクティブなトランザクション ログを使用できない場合は、そのログ部分にあるすべてのトランザクションが失われます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-123">If the active transaction log is unavailable, all transactions in that part of the log are lost.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6eb89-124">一括ログ復旧モデルで、一括ログ操作が含まれるすべてのログをバックアップするには、データベース内のすべてのデータ ファイルへのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="6eb89-124">Under the bulk-logged recovery model, backing up any log that contains bulk-logged operations requires access to all data files in the database.</span></span> <span data-ttu-id="6eb89-125">データ ファイルにアクセスできないと、トランザクション ログをバックアップできません。</span><span class="sxs-lookup"><span data-stu-id="6eb89-125">If the data files cannot be accessed, the transaction log cannot be backed up.</span></span> <span data-ttu-id="6eb89-126">その場合は、最新のログ バックアップ以降に加えられたすべての変更を手動で再実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6eb89-126">In that case, you have to manually redo all changes that were made since the most recent log backup.</span></span>  
  
     <span data-ttu-id="6eb89-127">詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](tail-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eb89-127">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="6eb89-128">データベースの最新の完全バックアップが復元されますが、データベースは復旧されません (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="6eb89-128">Restore the most recent full database backup without recovering the database (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span></span>  
  
3.  <span data-ttu-id="6eb89-129">差分バックアップが存在する場合は、データベースを復旧しないで最新の差分バックアップを復元します (RESTORE DATABASE *database_name* FROM *differential_backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="6eb89-129">If differential backups exist, restore the most recent one without recovering the database (RESTORE DATABASE *database_name* FROM *differential_backup_device* WITH NORECOVERY).</span></span>  
  
     <span data-ttu-id="6eb89-130">最新の差分バックアップを復元した方が、復元する必要のあるログ バックアップの数が少なくて済みます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-130">Restoring the most recent differential backup reduces the number of log backups that must be restored.</span></span>  
  
4.  <span data-ttu-id="6eb89-131">バックアップを復元した直後に作成された、最初のトランザクション ログのバックアップから順番に、NORECOVERY を指定してログを復元します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-131">Starting with the first transaction log backup that was created after the backup you just restored, restore the logs in sequence with NORECOVERY.</span></span>  
  
5.  <span data-ttu-id="6eb89-132">データベースを復旧します (RESTORE DATABASE *database_name* WITH RECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="6eb89-132">Recover the database (RESTORE DATABASE *database_name* WITH RECOVERY).</span></span> <span data-ttu-id="6eb89-133">または、この手順を最後のログ バックアップの復元と組み合わせることもできます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-133">Alternatively, this step can be combined with restoring the last log backup.</span></span>  
  
 <span data-ttu-id="6eb89-134">次の図に、この復元シーケンスを示します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-134">The following illustration shows this restore sequence.</span></span> <span data-ttu-id="6eb89-135">(1) 障害が発生した後、(2) ログ末尾のバックアップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-135">After a failure occurs (1), a tail-log backup is created (2).</span></span> <span data-ttu-id="6eb89-136">次に、データベースが障害発生時点まで復元されます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-136">Next, the database is restored to the point of the failure.</span></span> <span data-ttu-id="6eb89-137">このときに、データベース バックアップと、それ以降の差分バックアップ、および、ログ末尾のバックアップを含め、差分バックアップ後に作成されたすべてのログ バックアップが復元されます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-137">This involves restoring a database backup, a subsequent differential backup, and every log backup taken after the differential backup, including the tail-log backup.</span></span>  
  
 <span data-ttu-id="6eb89-138">![障害発生時点へのデータベースの全体復元](../../database-engine/media/bnrr-rmfull1-db-failure-pt.gif "障害発生時点へのデータベースの全体復元")</span><span class="sxs-lookup"><span data-stu-id="6eb89-138">![Complete database restore to the time of a failure](../../database-engine/media/bnrr-rmfull1-db-failure-pt.gif "Complete database restore to the time of a failure")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6eb89-139">データベースのバックアップを別のサーバー インスタンスに復元する場合は、「 [バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eb89-139">When you restore a database backup onto a different server instance, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> <span data-ttu-id="6eb89-140">基本的な Transact-SQL RESTORE 構文</span><span class="sxs-lookup"><span data-stu-id="6eb89-140">Basic Transact-SQL RESTORE Syntax</span></span>  
 <span data-ttu-id="6eb89-141">前の図に示した復元シーケンスの基本的な [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6eb89-141">The basic [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for the restore sequence in the preceding illustration is as follows:</span></span>  
  
1.  <span data-ttu-id="6eb89-142">RESTORE DATABASE *database* FROM *full database backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="6eb89-142">RESTORE DATABASE *database* FROM *full database backup* WITH NORECOVERY;</span></span>  
  
2.  <span data-ttu-id="6eb89-143">RESTORE DATABASE *database* FROM *full_differential_backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="6eb89-143">RESTORE DATABASE *database* FROM *full_differential_backup* WITH NORECOVERY;</span></span>  
  
3.  <span data-ttu-id="6eb89-144">RESTORE LOG *database* FROM *log_backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="6eb89-144">RESTORE LOG *database* FROM *log_backup* WITH NORECOVERY;</span></span>  
  
     <span data-ttu-id="6eb89-145">このログの復元手順を、追加のログ バックアップごとに繰り返します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-145">Repeat this restore-log step for each additional log backup.</span></span>  
  
4.  <span data-ttu-id="6eb89-146">RESTORE DATABASE *database* WITH RECOVERY;</span><span class="sxs-lookup"><span data-stu-id="6eb89-146">RESTORE DATABASE *database* WITH RECOVERY;</span></span>  
  
###  <a name="example-recovering-to-the-point-of-failure-transact-sql"></a><a name="ExampleToPoFTsql"></a> <span data-ttu-id="6eb89-147">例: 障害発生時点への復元 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6eb89-147">Example: Recovering to the Point of Failure (Transact-SQL)</span></span>  
 <span data-ttu-id="6eb89-148">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] の例は、データベースを障害発生時点まで復元する復元シーケンスに不可欠なオプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="6eb89-148">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] example shows the essential options in a restore sequence that restores the database to the point of failure.</span></span> <span data-ttu-id="6eb89-149">この例では、データベースのログ末尾のバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-149">The example creates a tail-log backup of the database.</span></span> <span data-ttu-id="6eb89-150">次に、データベースの完全バックアップとログ バックアップを復元してから、ログ末尾のバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-150">Next, the example restores a full database backup and log backup and then restores the tail-log backup.</span></span> <span data-ttu-id="6eb89-151">最後に、別の手順でデータベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-151">The example recovers the database in a separate, final step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6eb89-152">この例では、「 [データベースの完全バックアップ &#40;SQL Server&#41;](full-database-backups-sql-server.md)」の「互換性サポート」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eb89-152">This example uses a database backup and log backup that is created in the "Using Database Backups Under the Full Recovery Model" section in [Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md).</span></span> <span data-ttu-id="6eb89-153">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースは完全復旧モデルを使用するように、データベースのバックアップ前に設定されています。</span><span class="sxs-lookup"><span data-stu-id="6eb89-153">Before the database backup, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database was set to use the full recovery model.</span></span>  
  
```  
USE master;  
--Create tail-log backup.  
BACKUP LOG AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'    
   WITH NORECOVERY;   
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'   
  WITH FILE=1,   
    NORECOVERY;  
  
--Restore the regular log backup (from backup set 2).  
RESTORE LOG AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'   
  WITH FILE=2,   
    NORECOVERY;  
  
--Restore the tail-log backup (from backup set 3).  
RESTORE LOG AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'  
  WITH FILE=3,   
    NORECOVERY;  
GO  
--recover the database:  
RESTORE DATABASE AdventureWorks2012 WITH RECOVERY;  
GO  
```  
  
##  <a name="restoring-a-database-to-a-point-within-a-log-backup"></a><a name="PointWithinBackup"></a> <span data-ttu-id="6eb89-154">ログ バックアップ内の特定の時点へのデータベースの復元</span><span class="sxs-lookup"><span data-stu-id="6eb89-154">Restoring a Database to a Point Within a Log Backup</span></span>  
 <span data-ttu-id="6eb89-155">一般に、完全復旧モデルでは、データベースの全体復元によって、特定の時点、マークされたトランザクション、またはログ バックアップ内の特定の LSN まで復元することができます。</span><span class="sxs-lookup"><span data-stu-id="6eb89-155">Under the full recovery model, a complete database restore can usually be recovered to a point of time, a marked transaction, or an LSN within a log backup.</span></span> <span data-ttu-id="6eb89-156">ただし、一括ログ復旧モデルの場合は、一括ログ操作による変更がログ バックアップに含まれていると、特定の時点への復旧はできません。</span><span class="sxs-lookup"><span data-stu-id="6eb89-156">However, under the bulk-logged recovery model, if the log backup contains bulk-logged changes, point-in-time recovery is not possible.</span></span>  
  
### <a name="sample-point-in-time-restore-scenarios"></a><span data-ttu-id="6eb89-157">特定の時点への復元のサンプル シナリオ</span><span class="sxs-lookup"><span data-stu-id="6eb89-157">Sample Point-in-Time Restore Scenarios</span></span>  
 <span data-ttu-id="6eb89-158">ミッションクリティカルなデータベース システムで、データベースの完全バックアップを毎晩午前 0 時に作成し、データベースの差分バックアップを月曜日から土曜日まで 1 時間ごとに作成し、トランザクション ログのバックアップを 1 日中 10 分間隔で作成するとします。</span><span class="sxs-lookup"><span data-stu-id="6eb89-158">The following example assumes a mission-critical database system for which a full database backup is created daily at midnight, a differential database backup is created on the hour, Monday through Saturday, and transaction log backups are created every 10 minutes throughout the day.</span></span> <span data-ttu-id="6eb89-159">データベースを水曜日の午前 5 時 19 分の状態に復元するには、</span><span class="sxs-lookup"><span data-stu-id="6eb89-159">To restore the database to the state is was in at 5:19 A.M.</span></span> <span data-ttu-id="6eb89-160">次のようにします。</span><span class="sxs-lookup"><span data-stu-id="6eb89-160">Wednesday, do the following:</span></span>  
  
1.  <span data-ttu-id="6eb89-161">火曜日の午前 0 時に作成したデータベースの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-161">Restore the full database backup that was created Tuesday at midnight.</span></span>  
  
2.  <span data-ttu-id="6eb89-162">午前 5 時に作成したデータベースの差分バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-162">Restore the differential database backup that was created at 5:00 A.M.</span></span> <span data-ttu-id="6eb89-163">適用します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-163">on Wednesday.</span></span>  
  
3.  <span data-ttu-id="6eb89-164">水曜日の午前 5 時 10 分に作成したトランザクション ログのバックアップを</span><span class="sxs-lookup"><span data-stu-id="6eb89-164">Apply the transaction log backup that was created at 5:10 A.M.</span></span> <span data-ttu-id="6eb89-165">適用します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-165">on Wednesday.</span></span>  
  
4.  <span data-ttu-id="6eb89-166">水曜日の午前 5 時 20 分に作成したトランザクション ログのバックアップを適用し、</span><span class="sxs-lookup"><span data-stu-id="6eb89-166">Apply the transaction log backup that was created 5:20 A.M.</span></span> <span data-ttu-id="6eb89-167">午前 5 時 19 分までに発生したトランザクションにだけ復旧処理を適用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-167">on Wednesday, specifying that the recovery process applies only to transactions that occurred before 5:19 A.M.</span></span>  
  
 <span data-ttu-id="6eb89-168">データベースを木曜日の午前 3 時 4 分の状態に復元する必要があり、</span><span class="sxs-lookup"><span data-stu-id="6eb89-168">Alternatively, if the database needs to be restored to its state at 3:04 A.M.</span></span> <span data-ttu-id="6eb89-169">木曜日の午前 3 時に作成したデータベースの差分バックアップがない場合は、</span><span class="sxs-lookup"><span data-stu-id="6eb89-169">Thursday, but the differential database backup that was created at 3:00 A.M.</span></span> <span data-ttu-id="6eb89-170">次のようにします。</span><span class="sxs-lookup"><span data-stu-id="6eb89-170">Thursday is unavailable, do the following:</span></span>  
  
1.  <span data-ttu-id="6eb89-171">水曜日の午前 0 時に作成したデータベース バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-171">Restore the database backup that was created Wednesday at midnight.</span></span>  
  
2.  <span data-ttu-id="6eb89-172">木曜日の午前 2 時に作成したデータベースの差分バックアップを</span><span class="sxs-lookup"><span data-stu-id="6eb89-172">Restore the differential database backup that was created at 2:00 A.M.</span></span> <span data-ttu-id="6eb89-173">適用します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-173">on Thursday.</span></span>  
  
3.  <span data-ttu-id="6eb89-174">木曜日の午前 2 時 10 分から 3 時までに作成したすべての</span><span class="sxs-lookup"><span data-stu-id="6eb89-174">Apply all the transaction log backups created from 2:10 A.M.</span></span> <span data-ttu-id="6eb89-175">トランザクション ログのバックアップを</span><span class="sxs-lookup"><span data-stu-id="6eb89-175">to 3:00 A.M.</span></span> <span data-ttu-id="6eb89-176">適用します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-176">on Thursday.</span></span>  
  
4.  <span data-ttu-id="6eb89-177">木曜日の午前 3 時 10 分に作成したトランザクション ログ バックアップを適用し、</span><span class="sxs-lookup"><span data-stu-id="6eb89-177">Apply the transaction log backup that was created at 3:10 A.M.</span></span> <span data-ttu-id="6eb89-178">復旧処理を午前 3 時 4 分で停止します。</span><span class="sxs-lookup"><span data-stu-id="6eb89-178">on Thursday, stopping the recovery process at 3:04 A.M.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6eb89-179">特定の時点への復元の例については、「 [SQL Server データベースを特定の時点に復元する方法 &#40;完全復旧モデル&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)」の「互換性サポート」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eb89-179">For an example of a point-in-time restore, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6eb89-180">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6eb89-180">Related Tasks</span></span>  
 <span data-ttu-id="6eb89-181">**データベースの完全バックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="6eb89-181">**To restore a full database backup**</span></span>  
  
-   [<span data-ttu-id="6eb89-182">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6eb89-182">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="6eb89-183">データベースを新しい場所に復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6eb89-183">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
 <span data-ttu-id="6eb89-184">**データベースの差分バックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="6eb89-184">**To restore a differential database backup**</span></span>  
  
-   [<span data-ttu-id="6eb89-185">データベースの差分バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6eb89-185">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="6eb89-186">**トランザクション ログ バックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="6eb89-186">**To restore a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="6eb89-187">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6eb89-187">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
 <span data-ttu-id="6eb89-188">**SQL Server 管理オブジェクト (SMO) を使用してバックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="6eb89-188">**To restore a backup by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
 <span data-ttu-id="6eb89-189">**ログ バックアップ内の特定の時点までデータベースを復元するには**</span><span class="sxs-lookup"><span data-stu-id="6eb89-189">**To restore a database to a point within a log backup**</span></span>  
  
-   [<span data-ttu-id="6eb89-190">SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="6eb89-190">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="6eb89-191">マークされたトランザクションを含む関連データベースの復旧</span><span class="sxs-lookup"><span data-stu-id="6eb89-191">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [<span data-ttu-id="6eb89-192">ログ シーケンス番号への復旧 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6eb89-192">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="6eb89-193">参照</span><span class="sxs-lookup"><span data-stu-id="6eb89-193">See Also</span></span>  
 <span data-ttu-id="6eb89-194">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6eb89-194">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="6eb89-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6eb89-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="6eb89-196">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6eb89-196">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="6eb89-197">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6eb89-197">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="6eb89-198">[データベースの完全バックアップ &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6eb89-198">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="6eb89-199">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6eb89-199">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="6eb89-200">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6eb89-200">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="6eb89-201">復元と復旧の概要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6eb89-201">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
