---
title: ファイルの完全バックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backing up [SQL Server], files or filegroups
- backups [SQL Server], files or filegroups
- full recovery model [SQL Server], full file backups
- file backups [SQL Server], full
- files [SQL Server], backing up
- filegroups [SQL Server], backing up
- file backups [SQL Server]
ms.assetid: a716bf8d-0c5a-490d-aadd-597b3b0fac0c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e2e45dc68afa4d464aa3931075a1c1b3be792e6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643449"
---
# <a name="full-file-backups-sql-server"></a><span data-ttu-id="8990c-102">ファイルの完全バックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8990c-102">Full File Backups (SQL Server)</span></span>
  <span data-ttu-id="8990c-103">このトピックは、複数のファイルまたはファイル グループが含まれている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8990c-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="8990c-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース内のファイルは、個別にバックアップおよび復元できます。</span><span class="sxs-lookup"><span data-stu-id="8990c-104">The files in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database can be backed up and restored individually.</span></span> <span data-ttu-id="8990c-105">また、構成する各ファイルを個別に指定する代わりにファイル グループ全体を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8990c-105">Also, you can specify a whole filegroup instead of specifying each constituent file individually.</span></span> <span data-ttu-id="8990c-106">ファイル グループにオフラインのファイルが含まれている場合 (たとえば、ファイルが復元中である場合)、ファイル グループ全体がオフラインになり、バックアップできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8990c-106">Note that if any file in a filegroup is offline (for example, because the file is being restored), the whole filegroup is offline and cannot be backed up.</span></span>  
  
 <span data-ttu-id="8990c-107">読み取り専用ファイル グループのファイル バックアップは、部分バックアップと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="8990c-107">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="8990c-108">部分バックアップには、読み取りと書き込みが可能なファイル グループすべて、および必要に応じて 1 つ以上の読み取り専用ファイル グループが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8990c-108">Partial backups include all the read/write filegroups and, optionally, one or more read-only filegroups.</span></span> <span data-ttu-id="8990c-109">詳細については、「[部分バックアップ &#40;SQL Server&#41;](partial-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8990c-109">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="8990c-110">ファイル バックアップは、ファイルの差分バックアップの *差分ベース* として使用できます。</span><span class="sxs-lookup"><span data-stu-id="8990c-110">A file backup can serve as the *differential base* for differential file backups.</span></span> <span data-ttu-id="8990c-111">詳細については、「 [差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8990c-111">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8990c-112">ファイルの完全バックアップは、通常、 *ファイルの差分バックアップ*と明確に区別する場合を除き、 *ファイル バックアップ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8990c-112">Full file backups are typically called *file backups*, except when they are being explicitly compared with *differential file backups*.</span></span>  
  
 <span data-ttu-id="8990c-113">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="8990c-113">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="8990c-114">ファイル バックアップの利点</span><span class="sxs-lookup"><span data-stu-id="8990c-114">Benefits of File Backups</span></span>](#Benefits)  
  
-   [<span data-ttu-id="8990c-115">ファイル バックアップの欠点</span><span class="sxs-lookup"><span data-stu-id="8990c-115">Disadvantages of File Backups</span></span>](#Disadvantages)  
  
-   [<span data-ttu-id="8990c-116">ファイル バックアップの概要</span><span class="sxs-lookup"><span data-stu-id="8990c-116">Overview of File Backups</span></span>](#Overview)  
  
-   [<span data-ttu-id="8990c-117">関連タスク</span><span class="sxs-lookup"><span data-stu-id="8990c-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits-of-file-backups"></a><a name="Benefits"></a> <span data-ttu-id="8990c-118">ファイル バックアップの利点</span><span class="sxs-lookup"><span data-stu-id="8990c-118">Benefits of File Backups</span></span>  
 <span data-ttu-id="8990c-119">ファイル バックアップは、データベース バックアップよりも次の点で優れています。</span><span class="sxs-lookup"><span data-stu-id="8990c-119">File backups offer the following advantages over database backups:</span></span>  
  
-   <span data-ttu-id="8990c-120">ファイル バックアップを使用すると、残りのデータベースを復元しないで損傷したファイルだけを復元できるので、復旧を高速化できます。</span><span class="sxs-lookup"><span data-stu-id="8990c-120">Using file backups can increase the speed of recovery by letting you restore only damaged files, without restoring the rest of the database.</span></span>  
  
     <span data-ttu-id="8990c-121">たとえば、異なるディスクに配置されている複数のファイルからデータベースが構成されていて、1 つのディスクに障害が発生した場合は、障害が発生したディスク上のファイルだけを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8990c-121">For example, if a database consists of several files that are located on different disks and one disk fails, only the file on the failed disk has to be restored.</span></span> <span data-ttu-id="8990c-122">破損したファイルを高速に復元し、データベース全体を復元するよりも速く復旧できます。</span><span class="sxs-lookup"><span data-stu-id="8990c-122">The damaged file can be quickly restored, and recovery is faster than it would be for an entire database.</span></span>  
  
-   <span data-ttu-id="8990c-123">ファイル バックアップでは、データベースの完全バックアップよりもスケジュール設定とメディア処理を柔軟に行うことができます。非常に大規模なデータベースの場合、データベースの完全バックアップは管理しきれません。</span><span class="sxs-lookup"><span data-stu-id="8990c-123">File backups increase flexibility in scheduling and media handling over full database backups, which for very large databases can become unmanageable.</span></span> <span data-ttu-id="8990c-124">柔軟性に優れたファイルまたはファイル グループのバックアップは、さまざまな更新特性を備えたデータを含む大規模なデータベースでも役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="8990c-124">The increased flexibility of file or filegroup backups is also useful for large databases that contain data that has varying update characteristics.</span></span>  
  
##  <a name="disadvantages-of-file-backups"></a><a name="Disadvantages"></a> <span data-ttu-id="8990c-125">ファイル バックアップの欠点</span><span class="sxs-lookup"><span data-stu-id="8990c-125">Disadvantages of File Backups</span></span>  
  
-   <span data-ttu-id="8990c-126">データベースの完全バックアップと比較した場合のファイル バックアップの大きな欠点は、管理の複雑さです。</span><span class="sxs-lookup"><span data-stu-id="8990c-126">The primary disadvantage of file backups compared to full database backups is the additional administrative complexity.</span></span> <span data-ttu-id="8990c-127">これらのバックアップの完全なセットを保持および追跡するタスクは、データベースの完全バックアップの領域要件よりも重要な、時間のかかるタスクであることがあります。</span><span class="sxs-lookup"><span data-stu-id="8990c-127">Maintaining and keeping track of a complete set of these backups can be a time-consuming task that might outweigh the space requirements of full database backups.</span></span>  
  
-   <span data-ttu-id="8990c-128">破損したファイルのバックアップがない場合、メディア障害が発生したときに、データベース全体を復旧できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8990c-128">A media failure can make a complete database unrecoverable if a damaged file lacks a backup.</span></span> <span data-ttu-id="8990c-129">したがって、ファイル バックアップの完全なセットを保持しておく必要があります。また、完全復旧モデルまたは一括ログ復旧モデルの場合は、1 つ以上のログ バックアップが、最低でも、最初のファイルの完全バックアップと最新のファイルの完全バックアップの間に対応している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8990c-129">You must therefore maintain a complete set of file backups, and, for the full/bulk-logged recovery model, one or more log backups covering minimally the interval between the first full file backup and last full file backup.</span></span>  
  
##  <a name="overview-of-file-backups"></a><a name="Overview"></a> <span data-ttu-id="8990c-130">ファイル バックアップの概要</span><span class="sxs-lookup"><span data-stu-id="8990c-130">Overview of File Backups</span></span>  
 <span data-ttu-id="8990c-131">ファイルの完全バックアップでは、1 つ以上のファイルまたはファイル グループに含まれるすべてのデータがバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="8990c-131">A full file backup backs up all the data in one or more files or filegroups.</span></span> <span data-ttu-id="8990c-132">ファイル バックアップには、バックアップ操作の最後までロール フォワードできる十分なログ レコードが既定で含まれています。</span><span class="sxs-lookup"><span data-stu-id="8990c-132">By default, file backups contain enough log records to roll forward the file to the end of the backup operation.</span></span>  
  
 <span data-ttu-id="8990c-133">読み取り専用ファイルまたはファイル グループのバックアップはすべての復旧モデルで同じです。</span><span class="sxs-lookup"><span data-stu-id="8990c-133">Backing up a read-only file or filegroup is the same for every recovery model.</span></span> <span data-ttu-id="8990c-134">完全復旧モデルでは、ファイルの完全バックアップの完全なセットと、ファイル バックアップのすべての範囲に対応したログ バックアップを併用することで、データベースの完全バックアップに等しくなります。</span><span class="sxs-lookup"><span data-stu-id="8990c-134">Under the full recovery model, a complete set of full file backups, together with enough log backups to span all the file backups, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="8990c-135">ファイル バックアップ操作は、一度に 1 回のみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="8990c-135">Only one file backup operation can occur at a time.</span></span> <span data-ttu-id="8990c-136">1 回の操作で複数のファイルをバックアップできますが、ファイルを 1 つだけ復元する必要がある場合でも、復旧に時間がかかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8990c-136">You can back up multiple files in one operation, but this might extend the recovery time if you only have to restore a single file.</span></span> <span data-ttu-id="8990c-137">これは、対象のファイルを探すために、バックアップ全体が読み取られるためです。</span><span class="sxs-lookup"><span data-stu-id="8990c-137">This is because to locate that file, the whole backup is read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8990c-138">個別のファイルは、データベース バックアップから復元できますが、データベース バックアップからファイルの検索と復元を行うと、ファイル バックアップから行う場合よりも時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="8990c-138">Individual files can be restored from a database backup; however, locating and restoring a file takes longer from a database backup than from a file backup.</span></span>  
  
### <a name="file-backups-and-the-simple-recovery-model"></a><span data-ttu-id="8990c-139">ファイル バックアップと単純復旧モデル</span><span class="sxs-lookup"><span data-stu-id="8990c-139">File Backups and the Simple Recovery Model</span></span>  
 <span data-ttu-id="8990c-140">単純復旧モデルでは、読み取りと書き込みが可能なファイルはすべてまとめてバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8990c-140">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="8990c-141">これにより、データベースを一貫性のある時点に復元できます。</span><span class="sxs-lookup"><span data-stu-id="8990c-141">This makes sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="8990c-142">読み取りと書き込みが可能なファイルまたはファイル グループを個別に指定するのではなく、READ_WRITE_FILEGROUPS オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="8990c-142">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="8990c-143">このオプションにより、読み取りと書き込みが可能なすべてのファイル グループがデータベースにバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="8990c-143">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="8990c-144">READ_WRITE_FILEGROUPS を指定して作成されたファイル グループは、部分バックアップと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8990c-144">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a partial backup.</span></span> <span data-ttu-id="8990c-145">詳細については、「[部分バックアップ &#40;SQL Server&#41;](partial-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8990c-145">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
### <a name="file-backups-and-the-full-recovery-model"></a><span data-ttu-id="8990c-146">ファイル バックアップと完全復旧モデル</span><span class="sxs-lookup"><span data-stu-id="8990c-146">File Backups and the Full Recovery Model</span></span>  
 <span data-ttu-id="8990c-147">完全復旧モデルでは、バックアップ ストラテジの残りの部分に関係なく、トランザクション ログをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8990c-147">Under the full recovery model, you must back up the transaction log, regardless of the rest of your backup strategy.</span></span> <span data-ttu-id="8990c-148">ファイルの完全バックアップの完全なセットと、ファイル バックアップのすべての範囲に対応したログ バックアップを併用することで、データベースの完全バックアップに等しくなります。</span><span class="sxs-lookup"><span data-stu-id="8990c-148">A complete set of full file backups, together with enough log backups to span all the file backups from the start of the first file backup, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="8990c-149">ファイル バックアップとログ バックアップだけを使用したデータベースの復元は、複雑になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8990c-149">Restoring a database using just file and log backups can be complex.</span></span> <span data-ttu-id="8990c-150">したがって、可能であれば、データベースの完全バックアップを実行して、最初のファイル バックアップの前にログ バックアップを開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8990c-150">Therefore, if it is possible, it is a best practice to perform a full database backup and start the log backups before the first file backup.</span></span> <span data-ttu-id="8990c-151">次の図は、データベースが作成された直後 (時間 t0) に、データベースの完全バックアップを行う (時間 t1) という方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8990c-151">The following illustration shows a strategy in which a full database backup is taken (at time t1) soon after the database is created (at time t0).</span></span> <span data-ttu-id="8990c-152">この最初のデータベース バックアップによって、トランザクション ログのバックアップを開始できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8990c-152">This first database backup enables transaction log backups to start.</span></span> <span data-ttu-id="8990c-153">トランザクション ログのバックアップは、設定された間隔で実行するようにスケジュールが設定されています。</span><span class="sxs-lookup"><span data-stu-id="8990c-153">Transaction log backups are scheduled to occur at set intervals.</span></span> <span data-ttu-id="8990c-154">ファイル バックアップは、データベースに対するビジネス要件を最もよく満たす間隔で実行されます。</span><span class="sxs-lookup"><span data-stu-id="8990c-154">File backups occur at whatever interval best meets the business requirements for the database.</span></span> <span data-ttu-id="8990c-155">この図は、一度に 1 つずつバックアップされる 4 つのファイル グループのそれぞれを示します。</span><span class="sxs-lookup"><span data-stu-id="8990c-155">This illustration shows each of the four filegroups being backed up one at a time.</span></span> <span data-ttu-id="8990c-156">バックアップされる順序 (A、C、B、A) は、データベースのビジネス要件を反映しています。</span><span class="sxs-lookup"><span data-stu-id="8990c-156">The order in which they are backed up (A, C, B, A) reflects the business requirements of the database.</span></span>  
  
 <span data-ttu-id="8990c-157">![データベース、ファイル、ログのバックアップを結合する方法](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "データベース、ファイル、ログのバックアップを結合する方法")</span><span class="sxs-lookup"><span data-stu-id="8990c-157">![Strategy combining database, file, and log backups](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "Strategy combining database, file, and log backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8990c-158">完全復旧モデルで読み取り/書き込みファイルのバックアップを復元する際には、そのファイルとデータベースのそれ以外の部分との一貫性を確保するために、トランザクション ログをロールフォワードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8990c-158">Under the full recovery model, you must roll forward the transaction log when restoring a read/write file backup to make sure that the file is consistent with the rest of the database.</span></span> <span data-ttu-id="8990c-159">トランザクション ログのバックアップをロールフォワードする数が多くなりすぎないようにするには、ファイルの差分バックアップの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="8990c-159">To avoid rolling forward a lot of transaction log backups, consider using differential file backups.</span></span> <span data-ttu-id="8990c-160">詳細については、「 [差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8990c-160">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8990c-161">関連タスク</span><span class="sxs-lookup"><span data-stu-id="8990c-161">Related Tasks</span></span>  
 <span data-ttu-id="8990c-162">**ファイルまたはファイル グループのバックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="8990c-162">**To create a file or filegroup backup**</span></span>  
  
-   [<span data-ttu-id="8990c-163">ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8990c-163">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="8990c-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="8990c-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8990c-165">ファイル バックアップはメンテナンス プラン ウィザードでサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8990c-165">File backups are not supported by the Maintenance Plan Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8990c-166">参照</span><span class="sxs-lookup"><span data-stu-id="8990c-166">See Also</span></span>  
 <span data-ttu-id="8990c-167">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8990c-167">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="8990c-168">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8990c-168">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="8990c-169">[バックアップと復元: 相互運用性と共存 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8990c-169">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="8990c-170">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8990c-170">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="8990c-171">[ファイルの復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="8990c-171">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="8990c-172">[ファイルの復元 &#40;完全復旧モデル&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="8990c-172">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="8990c-173">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8990c-173">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="8990c-174">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8990c-174">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
