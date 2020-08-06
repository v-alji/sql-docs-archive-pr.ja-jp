---
title: ログ末尾のバックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], tail of log
- transaction log backups [SQL Server], tail-log backups
- NO_TRUNCATE clause
- backups [SQL Server], log backups
- tail-log backups
- backups [SQL Server], tail-log backups
ms.assetid: 313ddaf6-ec54-4a81-a104-7ffa9533ca58
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd7c505701a4edb1f66ca516d06179b2eb1a222d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632527"
---
# <a name="tail-log-backups-sql-server"></a><span data-ttu-id="7add9-102">ログ末尾のバックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7add9-102">Tail-Log Backups (SQL Server)</span></span>
  <span data-ttu-id="7add9-103">このトピックは、完全復旧モデルまたは一括ログ復旧モデルを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップと復元のみに関連しています。</span><span class="sxs-lookup"><span data-stu-id="7add9-103">This topic is relevant only for backup and restore of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="7add9-104">*ログ末尾のバックアップ* は、まだバックアップされていないすべてのログ レコード ( *ログの末尾*) をキャプチャし、作業内容の消失を防いで、ログ チェーンの完全性を維持します。</span><span class="sxs-lookup"><span data-stu-id="7add9-104">A *tail-log backup* captures any log records that have not yet been backed up (the *tail of the log*) to prevent work loss and to keep the log chain intact.</span></span> <span data-ttu-id="7add9-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをその最新の時点まで復元するには、トランザクション ログの末尾をあらかじめバックアップしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7add9-105">Before you can recover a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to its latest point in time, you must back up the tail of its transaction log.</span></span> <span data-ttu-id="7add9-106">ログ末尾のバックアップは、データベースの復旧プランの対象になる最後のバックアップとなります。</span><span class="sxs-lookup"><span data-stu-id="7add9-106">The tail-log backup will be the last backup of interest in the recovery plan for the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7add9-107">ログ末尾のバックアップは、すべての復元シナリオで必要となるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="7add9-107">Not all restore scenarios require a tail-log backup.</span></span> <span data-ttu-id="7add9-108">復旧ポイントが、それより前のログ バックアップに含まれているのであれば、ログ末尾のバックアップは不要です。</span><span class="sxs-lookup"><span data-stu-id="7add9-108">You do not need a tail-log backup if the recovery point is contained in an earlier log backup.</span></span> <span data-ttu-id="7add9-109">また、データベースを移動するか置き換えて (上書きして) いる場合、ログ末尾のバックアップは不要であり、最新のバックアップ以降の特定の時点に復元する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="7add9-109">Also, a tail-log backup is unnecessary if you are moving or replacing (overwriting) a database and do not need to restore it to a point of time after its most recent backup.</span></span>  
  
 
  
##  <a name="scenarios-that-require-a-tail-log-backup"></a><a name="TailLogScenarios"></a> <span data-ttu-id="7add9-110">ログ末尾のバックアップが必要となるシナリオ</span><span class="sxs-lookup"><span data-stu-id="7add9-110">Scenarios That Require a Tail-Log Backup</span></span>  
 <span data-ttu-id="7add9-111">以下に示すシナリオでは、ログ末尾のバックアップをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7add9-111">We recommend that you take a tail-log backup in the following scenarios:</span></span>  
  
-   <span data-ttu-id="7add9-112">データベースがオンライン状態であり、データベースに対して復元操作を実行する予定がある場合に、ログ末尾のバックアップを最初に行う。</span><span class="sxs-lookup"><span data-stu-id="7add9-112">If the database is online and you plan to perform a restore operation on the database, begin by backing up the tail of the log.</span></span> <span data-ttu-id="7add9-113">オンラインデータベースでエラーが発生しないようにするには、...[BACKUP](/sql/t-sql/statements/backup-transact-sql)ステートメントの with NORECOVERY オプション [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7add9-113">To avoid an error for an online database, you must use the ... WITH NORECOVERY option of the [BACKUP](/sql/t-sql/statements/backup-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
-   <span data-ttu-id="7add9-114">データベースがオフラインで起動できず、データベースを復元する必要がある場合に、まずログの末尾をバックアップする。</span><span class="sxs-lookup"><span data-stu-id="7add9-114">If a database is offline and fails to start and you need to restore the database, first back up the tail of the log.</span></span> <span data-ttu-id="7add9-115">このとき、トランザクションは発生しないので、WITH NORECOVERY の指定は省略できます。</span><span class="sxs-lookup"><span data-stu-id="7add9-115">Because no transactions can occur at this time, using the WITH NORECOVERY is optional.</span></span>  
  
-   <span data-ttu-id="7add9-116">データベースが破損したとき、BACKUP ステートメントの WITH CONTINUE_AFTER_ERROR オプションを使用してログ末尾のバックアップを試す。</span><span class="sxs-lookup"><span data-stu-id="7add9-116">If a database is damaged, try to take a tail-log backup by using the WITH CONTINUE_AFTER_ERROR option of the BACKUP statement.</span></span>  
  
     <span data-ttu-id="7add9-117">破損しているデータベースでログ末尾のバックアップが成功するのは、ログ ファイルが破損しておらず、データベースがログ末尾のバックアップをサポートしている状態であり、一括ログ記録された変更がデータベースに含まれていない場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="7add9-117">On a damaged database backing up the tail of the log can succeed only if the log files are undamaged, the database is in a state that supports tail-log backups, and the database does not contain any bulk-logged changes.</span></span> <span data-ttu-id="7add9-118">ログ末尾のバックアップを作成できない場合、最新のログ バックアップの後にコミットされたトランザクションはすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="7add9-118">If a tail-log backup cannot be created, any transactions committed after the latest log backup are lost.</span></span>  
  
 <span data-ttu-id="7add9-119">次の表は、BACKUP NORECOVERY と CONTINUE_AFTER_ERROR オプションをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="7add9-119">The following table summarizes the BACKUP NORECOVERY and CONTINUE_AFTER_ERROR options.</span></span>  
  
|<span data-ttu-id="7add9-120">BACKUP LOG オプション</span><span class="sxs-lookup"><span data-stu-id="7add9-120">BACKUP LOG option</span></span>|<span data-ttu-id="7add9-121">説明</span><span class="sxs-lookup"><span data-stu-id="7add9-121">Comments</span></span>|  
|-----------------------|--------------|  
|<span data-ttu-id="7add9-122">NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="7add9-122">NORECOVERY</span></span>|<span data-ttu-id="7add9-123">データベースの復元操作を続行する場合は、必ず NORECOVERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="7add9-123">Use NORECOVERY whenever you intend to continue with a restore operation on the database.</span></span> <span data-ttu-id="7add9-124">NORECOVERY を指定すると、データベースは復元中の状態になります。</span><span class="sxs-lookup"><span data-stu-id="7add9-124">NORECOVERY takes the database into the restoring state.</span></span> <span data-ttu-id="7add9-125">これにより、ログ末尾のバックアップの後にデータベースが変化しないことが保障されます。</span><span class="sxs-lookup"><span data-stu-id="7add9-125">This guarantees that the database does not change after the tail-log backup.</span></span>  <span data-ttu-id="7add9-126">NO_TRUNCATE オプションまたは COPY_ONLY オプションも指定されていない限り、ログは切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="7add9-126">The log is truncated unless the NO_TRUNCATE option or COPY_ONLY option is also specified.</span></span><br /><br /> <span data-ttu-id="7add9-127">重要データベースが破損している場合を除き、NO_TRUNCATE を使用しないことをお勧めします。 \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="7add9-127">**\*\* Important \*\*** We recommend that you avoid using NO_TRUNCATE, except when the database is damaged.</span></span>|  
|<span data-ttu-id="7add9-128">CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="7add9-128">CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="7add9-129">破損したデータベースの末尾をバックアップする場合に限り、CONTINUE_AFTER_ERROR を使用します。</span><span class="sxs-lookup"><span data-stu-id="7add9-129">Use CONTINUE_AFTER_ERROR only if you are backing up the tail of a damaged database.</span></span><br /><br /> <span data-ttu-id="7add9-130">注: 破損したデータベースでログの末尾のバックアップを使用すると、通常はログバックアップでキャプチャされたメタデータの一部が使用できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7add9-130">Note: When you use back up the tail of the log on a damaged database, some of the metadata ordinarily captured in log backups might be unavailable.</span></span> <span data-ttu-id="7add9-131">詳細については、後の「[不完全なバックアップ メタデータが含まれたログ末尾のバックアップ](#IncompleteMetadata)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7add9-131">For more information, see [Tail-Log Backups That Have Incomplete Backup Metadata](#IncompleteMetadata), later in this topic.</span></span>|  
  
##  <a name="tail-log-backups-that-have-incomplete-backup-metadata"></a><a name="IncompleteMetadata"></a><span data-ttu-id="7add9-132">不完全なバックアップメタデータが含まれるログ末尾のバックアップ</span><span class="sxs-lookup"><span data-stu-id="7add9-132">Tail-Log Backups That Have Incomplete Backup Metadata</span></span>  
 <span data-ttu-id="7add9-133">データベースがオフラインである場合、データベースが破損している場合、またはデータ ファイルが欠落している場合でも、ログ末尾のバックアップではログの末尾がキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="7add9-133">Tail log backups capture the tail of the log even if the database is offline, damaged, or missing data files.</span></span> <span data-ttu-id="7add9-134">これが原因で、復元情報コマンドや **msdb**のメタデータが不完全になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7add9-134">This might cause incomplete metadata from the restore information commands and **msdb**.</span></span> <span data-ttu-id="7add9-135">ただし、メタデータが不完全なだけで、キャプチャされたログは完全であり、使用できます。</span><span class="sxs-lookup"><span data-stu-id="7add9-135">However, only the metadata is incomplete; the captured log is complete and usable.</span></span>  
  
 <span data-ttu-id="7add9-136">ログ末尾のバックアップに不完全なメタデータが含まれている場合は、 [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) テーブルの **has_incomplete_metadata** が **1**に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7add9-136">If a tail-log backup has incomplete metadata, in the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) table, **has_incomplete_metadata** is set to **1**.</span></span> <span data-ttu-id="7add9-137">また、 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)の出力で **HasIncompleteMetadata** が **1**に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7add9-137">Also, in the output of [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql), **HasIncompleteMetadata** is set to **1**.</span></span>  
  
 <span data-ttu-id="7add9-138">ログ末尾のバックアップのメタデータが不完全な場合、ログ末尾のバックアップ時に、ファイル グループに関する情報の大部分が [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) テーブルから欠落します。</span><span class="sxs-lookup"><span data-stu-id="7add9-138">If the metadata in a tail-log backup is incomplete, the [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) table will be missing most of the information about filegroups at the time of the tail-log backup.</span></span> <span data-ttu-id="7add9-139">**backupfilegroup** テーブルのほとんどの列は NULL になり、意味を持つ列は次の列のみです。</span><span class="sxs-lookup"><span data-stu-id="7add9-139">Most of the **backupfilegroup** table columns are NULL; the only meaningful columns are as follows:</span></span>  
  
-   <span data-ttu-id="7add9-140">**backup_set_id**</span><span class="sxs-lookup"><span data-stu-id="7add9-140">**backup_set_id**</span></span>  
  
-   <span data-ttu-id="7add9-141">**filegroup_id**</span><span class="sxs-lookup"><span data-stu-id="7add9-141">**filegroup_id**</span></span>  
  
-   <span data-ttu-id="7add9-142">**type**</span><span class="sxs-lookup"><span data-stu-id="7add9-142">**type**</span></span>  
  
-   <span data-ttu-id="7add9-143">**type_desc**</span><span class="sxs-lookup"><span data-stu-id="7add9-143">**type_desc**</span></span>  
  
-   <span data-ttu-id="7add9-144">**is_readonly**</span><span class="sxs-lookup"><span data-stu-id="7add9-144">**is_readonly**</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7add9-145">関連タスク</span><span class="sxs-lookup"><span data-stu-id="7add9-145">Related Tasks</span></span>  
 <span data-ttu-id="7add9-146">ログ末尾のバックアップを作成するには、「[データベースが破損したときのトランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7add9-146">To create a tail-log backup, see [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).</span></span>  
  
 <span data-ttu-id="7add9-147">トランザクション ログ バックアップを復元するには、「[トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7add9-147">To restore a transaction log backup, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7add9-148">参照</span><span class="sxs-lookup"><span data-stu-id="7add9-148">See Also</span></span>  
 <span data-ttu-id="7add9-149">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7add9-149">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="7add9-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7add9-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="7add9-151">[SQL Server データベースのバックアップと復元](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="7add9-151">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="7add9-152">[コピーのみのバックアップ &#40;SQL Server&#41;](copy-only-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7add9-152">[Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md) </span></span>  
 <span data-ttu-id="7add9-153">[トランザクション ログのバックアップ &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7add9-153">[Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="7add9-154">トランザクション ログ バックアップの適用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7add9-154">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](apply-transaction-log-backups-sql-server.md)  
  
  
