---
title: ファイルの復元 (単純復旧モデル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- simple recovery model [SQL Server]
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- Transact-SQL restore sequence
- restoring files [SQL Server], simple recovery model
- file restores [SQL Server], simple recovery model
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ed48f48f531e727de5d6e1403ef47f5399f874d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715441"
---
# <a name="file-restores-simple-recovery-model"></a><span data-ttu-id="f10bd-102">ファイルの復元 (単純復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="f10bd-102">File Restores (Simple Recovery Model)</span></span>
  <span data-ttu-id="f10bd-103">このトピックは、1 つ以上の読み取り専用セカンダリ ファイル グループが含まれている単純復旧モデルのデータベースのみに関連しています。</span><span class="sxs-lookup"><span data-stu-id="f10bd-103">This topic is relevant only for simple-model databases that contain at least one read-only secondary filegroup.</span></span>  
  
 <span data-ttu-id="f10bd-104">ファイル復元の目標は、データベース全体を復元することなく 1 つ以上の破損したファイルを復元することです。</span><span class="sxs-lookup"><span data-stu-id="f10bd-104">In a file restore, the goal is to restore one or more damaged files without restoring the whole database.</span></span> <span data-ttu-id="f10bd-105">単純復旧モデルでは、読み取り専用ファイルだけにファイル バックアップがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f10bd-105">Under the simple recovery model, file backups are supported only for read-only files.</span></span> <span data-ttu-id="f10bd-106">プライマリ ファイル グループと読み取り/書き込みセカンダリ ファイル グループは、データベース バックアップまたは部分バックアップを復元することで、常に一緒に復元されます。</span><span class="sxs-lookup"><span data-stu-id="f10bd-106">The primary filegroup and read/write secondary filegroups are always restored together, by restoring a database or partial backup.</span></span>  
  
 <span data-ttu-id="f10bd-107">これらのファイル復元のシナリオは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f10bd-107">The file-restore scenarios are as follows:</span></span>  
  
-   <span data-ttu-id="f10bd-108">オフライン ファイル復元</span><span class="sxs-lookup"><span data-stu-id="f10bd-108">Offline file restore</span></span>  
  
     <span data-ttu-id="f10bd-109">*オフライン ファイル復元*では、破損したファイルまたはファイル グループを復元する間、データベースはオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="f10bd-109">In an *offline file restore*, the database is offline while damaged files or filegroups are restored.</span></span> <span data-ttu-id="f10bd-110">データベースは、復元シーケンスの最後にオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="f10bd-110">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="f10bd-111">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ではすべてのエディションで、オフラインのファイル復元がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f10bd-111">All editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support offline file restore.</span></span>  
  
-   <span data-ttu-id="f10bd-112">オンライン ファイル復元</span><span class="sxs-lookup"><span data-stu-id="f10bd-112">Online file restore</span></span>  
  
     <span data-ttu-id="f10bd-113">*オンライン ファイル復元*では、復元中にデータベースがオンラインであれば、データベースをオンラインにしたままファイル復元を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f10bd-113">In an *online file restore*, if database is online at restore time, it remains online during the file restore.</span></span> <span data-ttu-id="f10bd-114">ただし、復元操作時は、ファイルが復元される各ファイル グループがオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="f10bd-114">However, each filegroup in which a file is being restored is offline during the restore operation.</span></span> <span data-ttu-id="f10bd-115">オフライン ファイル グループ内のすべてのファイルが復旧されると、そのファイル グループは自動的にオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="f10bd-115">After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.</span></span>  
  
     <span data-ttu-id="f10bd-116">オンライン ページおよびファイルの復元に対するサポートの詳細については、「[SQL Server 2014 の各エディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f10bd-116">For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="f10bd-117">オンライン復元の詳細については、「[オンライン復元 &#40;SQL Server&#41;](online-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f10bd-117">For more information about online restores, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="f10bd-118">ファイル復元のためにデータベースをオフラインにする場合は、次の [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) ステートメントを実行して復元シーケンスを開始する前に、データベースをオフラインにしてください。ALTER DATABASE *database_name* SET OFFLINE。</span><span class="sxs-lookup"><span data-stu-id="f10bd-118">If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement: ALTER DATABASE *database_name* SET OFFLINE.</span></span>  
  

  
##  <a name="overview-of-file-and-filegroup-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> <span data-ttu-id="f10bd-119">単純復旧モデルでのファイルとファイル グループの復元の概要</span><span class="sxs-lookup"><span data-stu-id="f10bd-119">Overview of File and Filegroup Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="f10bd-120">ファイル復元のシナリオは、次に示すように、適切なデータをコピーし、ロールフォワードして、復旧する単一の復元シーケンスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f10bd-120">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data as follows:</span></span>  
  
1.  <span data-ttu-id="f10bd-121">破損した各ファイルを最新のファイル バックアップから復元します。</span><span class="sxs-lookup"><span data-stu-id="f10bd-121">Restore each damaged file from its most recent file backup.</span></span>  
  
2.  <span data-ttu-id="f10bd-122">復元されたファイルごとに最新のファイルの差分バックアップを復元し、データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="f10bd-122">Restore the most recent differential file backup for each restored file and recover the database.</span></span>  
  
### <a name="transact-sql-steps-for-file-restore-sequence-simple-recovery-model"></a><span data-ttu-id="f10bd-123">ファイル復元シーケンス用の Transact-SQL 手順 (単純復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="f10bd-123">Transact-SQL Steps for File Restore Sequence (Simple Recovery Model)</span></span>  
 <span data-ttu-id="f10bd-124">ここでは、単純ファイル復元シーケンスに必要な [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) オプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="f10bd-124">This section shows the essential [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) options for a simple file-restore sequence.</span></span> <span data-ttu-id="f10bd-125">説明の目的に関係しない構文や詳細は、省略しています。</span><span class="sxs-lookup"><span data-stu-id="f10bd-125">Syntax and details that are not relevant to this purpose are omitted.</span></span>  
  
 <span data-ttu-id="f10bd-126">復元シーケンスには、2 つの [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントだけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f10bd-126">The restore sequence contains only two [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="f10bd-127">1 つ目のステートメントは `A`というセカンダリ ファイルを復元します。このファイルは、WITH NORECOVERY を指定して復元されます。</span><span class="sxs-lookup"><span data-stu-id="f10bd-127">The first statement restores a secondary file, file `A`, which is restored using WITH NORECOVERY.</span></span> <span data-ttu-id="f10bd-128">2 つ目の操作では、 `B` と `C` という他の 2 つのファイルを復元します。これらのファイルは、WITH RECOVERY を使用して異なるバックアップ デバイスから復元します。</span><span class="sxs-lookup"><span data-stu-id="f10bd-128">The second operation restores two other files, `B` and `C` which are restored using WITH RECOVERY from a different backup device:</span></span>  
  
1.  <span data-ttu-id="f10bd-129">RESTORE DATABASE *database* FILE **=** _name_of_file_A_</span><span class="sxs-lookup"><span data-stu-id="f10bd-129">RESTORE DATABASE *database* FILE **=**_name_of_file_A_</span></span>  
  
     <span data-ttu-id="f10bd-130">FROM *file_backup_of_file_A*</span><span class="sxs-lookup"><span data-stu-id="f10bd-130">FROM *file_backup_of_file_A*</span></span>  
  
     <span data-ttu-id="f10bd-131">WITH NORECOVERY **;**</span><span class="sxs-lookup"><span data-stu-id="f10bd-131">WITH NORECOVERY **;**</span></span>  
  
2.  <span data-ttu-id="f10bd-132">RESTORE DATABASE *database* FILE **=** _name_of_file_B_ **,** _name_of_file_C_</span><span class="sxs-lookup"><span data-stu-id="f10bd-132">RESTORE DATABASE *database* FILE **=**_name_of_file_B_**,**_name_of_file_C_</span></span>  
  
     <span data-ttu-id="f10bd-133">FROM *file_backup_of_files_B_and_C*</span><span class="sxs-lookup"><span data-stu-id="f10bd-133">FROM *file_backup_of_files_B_and_C*</span></span>  
  
     <span data-ttu-id="f10bd-134">WITH RECOVERY **;**</span><span class="sxs-lookup"><span data-stu-id="f10bd-134">WITH RECOVERY **;**</span></span>  
  
### <a name="examples"></a><span data-ttu-id="f10bd-135">例</span><span class="sxs-lookup"><span data-stu-id="f10bd-135">Examples</span></span>  
  
-   [<span data-ttu-id="f10bd-136">例: 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="f10bd-136">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="f10bd-137">例: プライマリ ファイル グループと他のファイル グループを 1 つオフラインで復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="f10bd-137">Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;</span></span>](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f10bd-138">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f10bd-138">Related Tasks</span></span>  
 <span data-ttu-id="f10bd-139">**ファイルおよびファイル グループを復元するには**</span><span class="sxs-lookup"><span data-stu-id="f10bd-139">**To restore files and filegroups**</span></span>  
  
-   [<span data-ttu-id="f10bd-140">既存のファイルにファイルとファイル グループを復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f10bd-140">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="f10bd-141">ファイルおよびファイル グループの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f10bd-141">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="f10bd-142">ファイルおよびファイル グループの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f10bd-142">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="f10bd-143"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="f10bd-143"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="f10bd-144">参照</span><span class="sxs-lookup"><span data-stu-id="f10bd-144">See Also</span></span>  
 <span data-ttu-id="f10bd-145">[バックアップと復元: 相互運用性と共存 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f10bd-145">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="f10bd-146">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f10bd-146">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="f10bd-147">[ファイルの完全バックアップ &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f10bd-147">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="f10bd-148">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f10bd-148">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="f10bd-149">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f10bd-149">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="f10bd-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f10bd-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="f10bd-151">[データベースの全体復元 &#40;単純復旧モデル&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="f10bd-151">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="f10bd-152">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f10bd-152">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
