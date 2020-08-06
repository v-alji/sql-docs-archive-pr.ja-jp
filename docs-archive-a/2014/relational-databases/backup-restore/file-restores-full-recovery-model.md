---
title: ファイル復元 (完全復旧モデル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- full recovery model [SQL Server], performing restores
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- file restores [SQL Server], full recovery model
- restoring files [SQL Server], full recovery model
- Transact-SQL restore sequence
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: d2236a2a-4cf1-4c3f-b542-f73f6096e15c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 488515ec900867f13d33580402e36a3f98747bb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715442"
---
# <a name="file-restores-full-recovery-model"></a><span data-ttu-id="d3152-102">ファイル復元 (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="d3152-102">File Restores (Full Recovery Model)</span></span>
  <span data-ttu-id="d3152-103">このトピックは、複数のファイルまたはファイル グループが含まれている、完全復旧モデルまたは一括読み込み復旧モデルを使用するデータベースだけに関連しています。</span><span class="sxs-lookup"><span data-stu-id="d3152-103">This topic is relevant only for databases that contain multiple files or filegroups under the full or bulk-load recovery model.</span></span>  
  
 <span data-ttu-id="d3152-104">ファイル復元の目標は、データベース全体を復元することなく 1 つ以上の破損したファイルを復元することです。</span><span class="sxs-lookup"><span data-stu-id="d3152-104">In a file restore, the goal is to restore one or more damaged files without restoring the whole database.</span></span> <span data-ttu-id="d3152-105">ファイル復元シナリオは、適切なデータをコピーし、ロールフォワードして、復旧する単一の復元シーケンスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="d3152-105">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data</span></span>  
  
 <span data-ttu-id="d3152-106">復元中のファイル グループが読み取り/書き込み可能である場合、最後に実行されたデータ バックアップまたは差分バックアップを復元した後、チェーンが途切れていないログ バックアップを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3152-106">If the filegroup that is being restored is read/write, an unbroken chain of log backups must be applied after the last data or differential backup is restored.</span></span> <span data-ttu-id="d3152-107">これにより、ログ ファイル内の現在アクティブなログ レコードの状態がファイル グループに反映されます。</span><span class="sxs-lookup"><span data-stu-id="d3152-107">This brings the filegroup forward to the log records in the current active log records in the log file.</span></span> <span data-ttu-id="d3152-108">復旧ポイントは通常ログの末尾付近にありますが、必ずというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d3152-108">The recovery point is typically near the end of log, but not necessarily.</span></span>  
  
 <span data-ttu-id="d3152-109">復元中のファイル グループが読み取り専用の場合、通常はログ バックアップを適用する必要がないため、スキップされます。</span><span class="sxs-lookup"><span data-stu-id="d3152-109">If the filegroup that is being restored is read-only, usually applying log backups is unnecessary and is skipped.</span></span> <span data-ttu-id="d3152-110">ファイルが読み取り専用になった後でバックアップが行われた場合、それが復元する最後のバックアップになります。</span><span class="sxs-lookup"><span data-stu-id="d3152-110">If the backup was taken after the file became read-only, that is the last backup to restore.</span></span> <span data-ttu-id="d3152-111">ロールフォワードは、目的の時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="d3152-111">Roll forward stops at the target point.</span></span>  
  
 <span data-ttu-id="d3152-112">これらのファイル復元のシナリオは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d3152-112">The file-restore scenarios are as follows:</span></span>  
  
-   <span data-ttu-id="d3152-113">オフライン ファイル復元</span><span class="sxs-lookup"><span data-stu-id="d3152-113">Offline file restore</span></span>  
  
     <span data-ttu-id="d3152-114">*オフライン ファイル復元*では、破損したファイルまたはファイル グループを復元する間、データベースはオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="d3152-114">In an *offline file restore*, the database is offline while damaged files or filegroups are restored.</span></span> <span data-ttu-id="d3152-115">データベースは、復元シーケンスの最後にオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="d3152-115">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="d3152-116">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ではすべてのエディションで、オフラインのファイル復元がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d3152-116">All editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support offline file restore.</span></span>  
  
-   <span data-ttu-id="d3152-117">オンライン ファイル復元</span><span class="sxs-lookup"><span data-stu-id="d3152-117">Online file restore</span></span>  
  
     <span data-ttu-id="d3152-118">*オンライン ファイル復元*では、復元中にデータベースがオンラインであれば、データベースをオンラインにしたままファイル復元を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d3152-118">In an *online file restore*, if database is online at restore time, it remains online during the file restore.</span></span> <span data-ttu-id="d3152-119">ただし、復元操作時は、ファイルが復元される各ファイル グループがオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="d3152-119">However, each filegroup in which a file is being restored is offline during the restore operation.</span></span> <span data-ttu-id="d3152-120">オフライン ファイル グループ内のすべてのファイルが復旧されると、そのファイル グループは自動的にオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="d3152-120">After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.</span></span>  
  
     <span data-ttu-id="d3152-121">オンライン ページおよびファイルの復元に対するサポートの詳細については、「[SQL Server 2014 の各エディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3152-121">For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="d3152-122">オンライン復元の詳細については、「[オンライン復元 &#40;SQL Server&#41;](online-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3152-122">For more information about online restores, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="d3152-123">ファイル復元のためにデータベースをオフラインにする場合は、次の [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) ステートメントを実行して復元シーケンスを開始する前に、データベースをオフラインにしてください。ALTER DATABASE *database_name* SET OFFLINE。</span><span class="sxs-lookup"><span data-stu-id="d3152-123">If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement: ALTER DATABASE *database_name* SET OFFLINE.</span></span>  
  
  
  
##  <a name="restoring-damaged-files-from-file-backups"></a><a name="Overview"></a> <span data-ttu-id="d3152-124">破損したファイルのファイル バックアップからの復元</span><span class="sxs-lookup"><span data-stu-id="d3152-124">Restoring Damaged Files from File Backups</span></span>  
  
1.  <span data-ttu-id="d3152-125">1 つ以上の破損したファイルを復元するには、 [ログ末尾のバックアップ](tail-log-backups-sql-server.md)を作成してください。</span><span class="sxs-lookup"><span data-stu-id="d3152-125">Before restoring one or more damaged files, attempt to create a [tail-log backup](tail-log-backups-sql-server.md).</span></span>  
  
     <span data-ttu-id="d3152-126">ログが破損したためにログ末尾のバックアップを作成できない場合は、データベース全体を復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3152-126">If the log has been damaged, a tail-log backup cannot be created, and you must restore the whole database.</span></span>  
  
     <span data-ttu-id="d3152-127">トランザクション ログのバックアップ方法の詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3152-127">For information about how to back up a transaction log, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d3152-128">オフライン ファイル復元では、必ずファイルの復元前にログ末尾のバックアップを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3152-128">For an offline file restore, you must always take a tail-log backup before the file restore.</span></span> <span data-ttu-id="d3152-129">オンライン ファイル復元では、必ずファイルの復元後にログ バックアップを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3152-129">For an online file restore, you must always take the log backup after the file restore.</span></span> <span data-ttu-id="d3152-130">ファイルを他のデータベースと一貫性のある状態に復旧できるようにする必要があるため、このログ バックアップが必要になります。</span><span class="sxs-lookup"><span data-stu-id="d3152-130">This log backup is necessary to allow for the file to be recovered to a state consistent with the rest of the database.</span></span>  
  
2.  <span data-ttu-id="d3152-131">破損したファイルについては、そのファイルの最新のファイル バックアップから復元します。</span><span class="sxs-lookup"><span data-stu-id="d3152-131">Restore each damaged file from the most recent file backup of that file.</span></span>  
  
3.  <span data-ttu-id="d3152-132">差分バックアップがある場合は、復元したファイルごとに最新のファイルの差分バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="d3152-132">Restore the most recent differential file backup, if any, for each restored file.</span></span>  
  
4.  <span data-ttu-id="d3152-133">トランザクション バックアップを順番に復元します。復元したファイルの中で最も古いファイルに対応するバックアップの復元から始め、最後に手順 1. で作成したログ末尾のバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="d3152-133">Restore transaction log backups in sequence, starting with the backup that covers the oldest of the restored files and ending with the tail-log backup created in step 1.</span></span>  
  
     <span data-ttu-id="d3152-134">データベースを一貫性のある状態にするには、ファイル バックアップより後に作成されたトランザクション ログ バックアップを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3152-134">You must restore the transaction log backups that were created after the file backups to bring the database to a consistent state.</span></span> <span data-ttu-id="d3152-135">トランザクション ログ バックアップは、復元するファイルに関連のある変更のみが適用されるので、すばやくロールフォワードできます。</span><span class="sxs-lookup"><span data-stu-id="d3152-135">The transaction log backups can be rolled forward quickly, because only the changes that apply to the restored files are applied.</span></span> <span data-ttu-id="d3152-136">破損していないファイルに関しては、コピーされずにロールフォワードが行われるので、データベース全体の復元より個別のファイルの復元の方が適している場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3152-136">Restoring individual files can be better than restoring the whole database, because undamaged files are not copied and then rolled forward.</span></span> <span data-ttu-id="d3152-137">ただし、ログ バックアップのチェーンは、全体を読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3152-137">However, the whole chain of log backups still has to be read.</span></span>  
  
5.  <span data-ttu-id="d3152-138">データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="d3152-138">Recover the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3152-139">ファイル バックアップを使用して、データベースを以前の時点の状態に復元することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3152-139">File backups can be used to restore the database to an earlier point in time.</span></span> <span data-ttu-id="d3152-140">この操作を行うには、ファイル バックアップの完全なセットを復元してから、一番最近に復元されたファイル バックアップの後の時点までのトランザクション ログ バックアップを順番に復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3152-140">To do this, you must restore a complete set of file backups, and then restore transaction log backups in sequence to reach a target point that is after the end of the most recent restored file backup.</span></span> <span data-ttu-id="d3152-141">特定の時点への復旧の詳細については、「[SQL Server データベースを特定の時点に復元する方法 &#40;完全復旧モデル&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3152-141">For more information about point-in-time recovery, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
## <a name="transact-sql-restore-sequence-for-an-offline-file-restore-full-recovery-model"></a><span data-ttu-id="d3152-142">オフラインのファイル復元用の Transact-SQL 復元シーケンス (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="d3152-142">Transact-SQL Restore Sequence for an Offline File Restore (Full Recovery Model)</span></span>  
 <span data-ttu-id="d3152-143">ファイル復元シナリオは、適切なデータをコピーし、ロールフォワードして、復旧する単一の復元シーケンスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="d3152-143">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data.</span></span>  
  
 <span data-ttu-id="d3152-144">ここでは、ファイル復元シーケンスに必要な [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) オプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="d3152-144">This section shows the essential [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) options for a file-restore sequence.</span></span> <span data-ttu-id="d3152-145">説明の目的に関係しない構文や詳細は、省略しています。</span><span class="sxs-lookup"><span data-stu-id="d3152-145">Syntax and details that are not relevant to this purpose are omitted.</span></span>  
  
 <span data-ttu-id="d3152-146">このサンプル復元シーケンスでは、WITH NORECOVERY を使用した 2 つのセカンダリ ファイル ( `A` と `B`) のオフライン復元を示します。</span><span class="sxs-lookup"><span data-stu-id="d3152-146">The following sample restore sequence shows an offline restore of two secondary files, `A` and `B`, using WITH NORECOVERY.</span></span> <span data-ttu-id="d3152-147">次に、NORECOVERY を使用して 2 つのログ バックアップを適用してから、WITH RECOVERY を使用してログ末尾のバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="d3152-147">Next, two log backups are applied with NORECOVERY, followed with the tail-log backup, and this is restored using WITH RECOVERY.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3152-148">このサンプル復元シーケンスでは、まず、ファイルをオフラインにしてからログ末尾のバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3152-148">The following sample restore sequence starts by taking the file offline and then creates a tail-log backup.</span></span>  
  
```  
--Take the file offline.  
ALTER DATABASE database_name MODIFY FILE SET OFFLINE;  
-- Back up the currently active transaction log.  
BACKUP LOG database_name  
   TO <tail_log_backup>  
   WITH NORECOVERY;  
GO   
-- Restore the files.  
RESTORE DATABASE database_name FILE=name   
   FROM <file_backup_of_file_A>   
   WITH NORECOVERY;  
RESTORE DATABASE database_name FILE=<name> ......  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
-- Restore the log backups.  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <tail_log_backup>   
   WITH RECOVERY;  
```  
  
## <a name="examples"></a><span data-ttu-id="d3152-149">例</span><span class="sxs-lookup"><span data-stu-id="d3152-149">Examples</span></span>  
  
-   [<span data-ttu-id="d3152-150">例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="d3152-150">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="d3152-151">例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="d3152-151">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="d3152-152">例: プライマリ ファイル グループと他のファイル グループを 1 つオフラインで復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="d3152-152">Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;</span></span>](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d3152-153">関連タスク</span><span class="sxs-lookup"><span data-stu-id="d3152-153">Related Tasks</span></span>  
 <span data-ttu-id="d3152-154">**ファイルおよびファイル グループを復元するには**</span><span class="sxs-lookup"><span data-stu-id="d3152-154">**To restore files and filegroups**</span></span>  
  
-   [<span data-ttu-id="d3152-155">新しい場所へのファイルの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d3152-155">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="d3152-156">ファイルおよびファイル グループの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d3152-156">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="d3152-157"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="d3152-157"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="d3152-158">参照</span><span class="sxs-lookup"><span data-stu-id="d3152-158">See Also</span></span>  
 <span data-ttu-id="d3152-159">[バックアップと復元: 相互運用性と共存 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3152-159">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="d3152-160">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3152-160">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d3152-161">[ファイルの完全バックアップ &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3152-161">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d3152-162">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3152-162">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="d3152-163">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3152-163">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="d3152-164">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d3152-164">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="d3152-165">[データベースの全体復元 &#40;単純復旧モデル&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d3152-165">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="d3152-166">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d3152-166">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
