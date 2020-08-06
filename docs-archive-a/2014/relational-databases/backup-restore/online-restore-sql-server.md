---
title: オンライン復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- online restores [SQL Server]
- online restores [SQL Server], about online restores
ms.assetid: 7982a687-980a-4eb8-8e9f-6894148e7d8c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4db4d5b5ce08c50646857099d82964bb944bc8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643444"
---
# <a name="online-restore-sql-server"></a><span data-ttu-id="fb612-102">オンライン復元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fb612-102">Online Restore (SQL Server)</span></span>
  <span data-ttu-id="fb612-103">オンライン復元は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fb612-103">Online restore is supported only on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition.</span></span> <span data-ttu-id="fb612-104">このエディションの既定で、ファイル復元、ページ復元、または段階的な部分復元はオンラインで行われます。</span><span class="sxs-lookup"><span data-stu-id="fb612-104">In this edition, a file, page, or piecemeal restore is online by default.</span></span> <span data-ttu-id="fb612-105">このトピックの内容は、複数のファイルまたはファイル グループを含むデータベース (単純復旧モデルでは、読み取り専用ファイル グループのみ) に関連しています。</span><span class="sxs-lookup"><span data-stu-id="fb612-105">This topic is relevant for databases that contain multiple files or filegroups (and, under the simple recovery model, only for read-only filegroups).</span></span>  
  
 <span data-ttu-id="fb612-106">データベースがオンラインのときにデータを復元する処理を *オンライン復元*といいます。</span><span class="sxs-lookup"><span data-stu-id="fb612-106">Restoring data while the database is online is called an *online restore*.</span></span> <span data-ttu-id="fb612-107">プライマリ ファイル グループがオンラインの場合、1 つ以上のセカンダリ ファイル グループがオフラインでも、そのデータベースはオンラインと見なされます。</span><span class="sxs-lookup"><span data-stu-id="fb612-107">A database is considered to be online whenever the primary filegroup is online, even if one or more of its secondary filegroups are offline.</span></span> <span data-ttu-id="fb612-108">どの復旧モデルでも、データベースがオンラインであれば、オフラインのファイルを復元できます。</span><span class="sxs-lookup"><span data-stu-id="fb612-108">Under any recovery model, you can restore a file that is offline while the database is online.</span></span> <span data-ttu-id="fb612-109">完全復旧モデルでは、データベースがオンラインであれば、ページも復元できます。</span><span class="sxs-lookup"><span data-stu-id="fb612-109">Under the full recovery model, you can also restore pages while the database is online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb612-110">オンライン復元は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise で自動的に実行されるため、ユーザーが操作を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fb612-110">Online restore occurs automatically on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise and requires no user action.</span></span> <span data-ttu-id="fb612-111">オンライン復元を使用しない場合は、復元を開始する前にデータベースをオフラインにできます。</span><span class="sxs-lookup"><span data-stu-id="fb612-111">If you do not want to use online restore, you can take a database offline before you start a restore.</span></span> <span data-ttu-id="fb612-112">詳細については、このトピックの「 [データベースまたはファイルのオフライン化](#taking_db_or_file_offline)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb612-112">For more information, see [Taking a Database or File Offline](#taking_db_or_file_offline), later in this topic.</span></span>  
  
 <span data-ttu-id="fb612-113">オンライン ファイル復元では、復元するファイルとそのファイル グループがオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="fb612-113">During an online file restore, any file being restored and its filegroup are offline.</span></span> <span data-ttu-id="fb612-114">オンライン復元を開始するときに、復元するいずれかのファイルがオンラインの場合、そのファイルのファイル グループは最初の復元ステートメントによってオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="fb612-114">If any of these files is online when an online restore starts, the first restore statement takes the filegroup of the file offline.</span></span> <span data-ttu-id="fb612-115">一方、オンラインのページ復元では、ページのみがオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="fb612-115">In contrast, during an online page restore, only the page is offline.</span></span>  
  
 <span data-ttu-id="fb612-116">オンライン復元シナリオには、次の基本的な手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fb612-116">Every online restore scenario involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="fb612-117">データを復元します。</span><span class="sxs-lookup"><span data-stu-id="fb612-117">Restore the data.</span></span>  
  
2.  <span data-ttu-id="fb612-118">最後のログの復元に WITH RECOVERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="fb612-118">Restore the log by using WITH RECOVERY for the last log restore.</span></span> <span data-ttu-id="fb612-119">この操作により、復元したデータがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="fb612-119">This brings the restored data online.</span></span>  
  
 <span data-ttu-id="fb612-120">場合によっては、ロールバックに必要なデータが起動時にオフラインになっているために、コミットされていないトランザクションをロールバックできないことがあります。</span><span class="sxs-lookup"><span data-stu-id="fb612-120">Occasionally, an uncommitted transaction cannot be rolled back because the data that is required by rollback is offline during startup.</span></span> <span data-ttu-id="fb612-121">このような場合は、トランザクションの処理が遅延されます。</span><span class="sxs-lookup"><span data-stu-id="fb612-121">In this case, the transaction is deferred.</span></span> <span data-ttu-id="fb612-122">詳細については、「 [遅延トランザクション &#40;SQL Server&#41;](deferred-transactions-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb612-122">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb612-123">データベースで一括ログ復旧モデルを使用している場合は、完全復旧モデルに切り替えてからオンライン復元を開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fb612-123">If the database is currently using the bulk-logged recovery model, we recommend that you switch to the full recovery model before you start an online restore.</span></span> <span data-ttu-id="fb612-124">詳細については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb612-124">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fb612-125">サーバーに接続された複数のデバイス使用してバックアップを行った場合は、オンライン復元時に同じ数のデバイスを使用できるようにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb612-125">If the backups were taken with multiple devices that were attached to the server, the same number of devices must be available during an online restore.</span></span>  
  
## <a name="log-backups-for-online-restore"></a><span data-ttu-id="fb612-126">オンライン復元のログ バックアップ</span><span class="sxs-lookup"><span data-stu-id="fb612-126">Log Backups for Online Restore</span></span>  
 <span data-ttu-id="fb612-127">オンライン復元の場合、復旧ポイントとは、復元しているデータがオフラインになった時点、または前回読み取り専用に設定された時点です。</span><span class="sxs-lookup"><span data-stu-id="fb612-127">In an online restore, the recovery point is the point when the data being restored was taken offline or made read-only for the last time.</span></span> <span data-ttu-id="fb612-128">復旧ポイントに至るまでのトランザクション ログ バックアップ、およびこの復旧ポイントを含むトランザクション ログ バックアップが、すべて使用可能になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb612-128">The transaction log backups leading up to and including this recovery point must all be available.</span></span> <span data-ttu-id="fb612-129">通常、ファイルの復旧ポイントに対応するには、復旧ポイント以降のログ バックアップが必要です。</span><span class="sxs-lookup"><span data-stu-id="fb612-129">Generally, a log backup is required after that point to cover the recovery point for the file.</span></span> <span data-ttu-id="fb612-130">唯一の例外は、データが読み取り専用になった後に作成されたデータ バックアップから、読み取り専用データのオンライン復元を実行する場合です。</span><span class="sxs-lookup"><span data-stu-id="fb612-130">The only exception is during an online restore of read-only data from a data backup that was taken after the data became read-only.</span></span> <span data-ttu-id="fb612-131">この場合、ログ バックアップは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="fb612-131">In this case, you do not have to have a log backup.</span></span>  
  
 <span data-ttu-id="fb612-132">通常、データベースがオンラインの間は、復元シーケンスを開始した後でも、トランザクション ログ バックアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="fb612-132">Generally, you may take transaction log backups while the database is online, even after the start of the restore sequence.</span></span> <span data-ttu-id="fb612-133">最後のログ バックアップのタイミングは、復元されるファイルのプロパティによって異なります。</span><span class="sxs-lookup"><span data-stu-id="fb612-133">The timing of the last log backup depends on the properties of the file being restored:</span></span>  
  
-   <span data-ttu-id="fb612-134">読み取り専用のオンライン ファイルの場合、最初の復元シーケンスの前または最中に、復旧に必要な最後のログ バックアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="fb612-134">For an online read-only file, you can take the last log backup that is required for recovery before or during the first restore sequence.</span></span> <span data-ttu-id="fb612-135">読み取り専用ファイル グループでは、ファイル グループが読み取り専用になった後にデータ バックアップまたは差分バックアップが実行された場合、ログ バックアップは不要です。</span><span class="sxs-lookup"><span data-stu-id="fb612-135">A read-only filegroup may not require log backups if a data or differential backup was taken after the filegroup became read-only.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fb612-136">上記の情報は、オフライン ファイルにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="fb612-136">The preceding information also applies to every offline file.</span></span>  
  
-   <span data-ttu-id="fb612-137">最初の復元ステートメントが実行された時点でオンラインになっていた読み取りと書き込みが可能なファイル、またはその復元ステートメントで自動的にオフラインになった読み取りと書き込みが可能なファイルは、特殊なケースです。</span><span class="sxs-lookup"><span data-stu-id="fb612-137">A special case exists for a read/write file that was online when the first restore statement was issued and that was then automatically taken offline by that restore statement.</span></span> <span data-ttu-id="fb612-138">この場合、最初の *復元シーケンス* (復元、ロールフォワード、およびデータの復旧を行う、1 つ以上の RESTORE ステートメントのシーケンス) の間にログ バックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb612-138">In this case, you must take a log backup during the first *restore sequence* (the sequence of one or more RESTORE statements that restore, roll forward, and recover data).</span></span> <span data-ttu-id="fb612-139">通常、このログ バックアップは、すべての完全バックアップの復元後かつデータ復旧の前に行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb612-139">Generally, this log backup must occur after you restore all the full backups and before you recover the data.</span></span> <span data-ttu-id="fb612-140">ただし、特定のファイル グループに対して複数のファイル バックアップが存在する場合、ログ バックアップの最小復旧ポイントはそのファイル グループがオフラインになった後の時点になります。</span><span class="sxs-lookup"><span data-stu-id="fb612-140">However, if there are multiple file backups for a specific filegroup, the minimal point of log backup is the time after the filegroup is offline.</span></span> <span data-ttu-id="fb612-141">このデータ復元後のログ バックアップにより、ファイルがオフラインになった時点がキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="fb612-141">This post-data-restore log backup captures the point at which the file was taken offline.</span></span> <span data-ttu-id="fb612-142">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ではオンライン復元のオンライン ログを使用できないので、データ復元後のログ バックアップが必要です。</span><span class="sxs-lookup"><span data-stu-id="fb612-142">The post-data-restore log backup is necessary because the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot use online log for an online restore.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fb612-143">または、復元シーケンスの前に手動でファイルをオフラインにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="fb612-143">Alternatively, you can manually take the file offline before the restore sequence.</span></span> <span data-ttu-id="fb612-144">詳細については、このトピックの「データベースまたはファイルのオフライン化」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb612-144">For more information, see "Taking a Database or File Offline" later in this topic.</span></span>  
  
##  <a name="taking-a-database-or-file-offline"></a><a name="taking_db_or_file_offline"></a> <span data-ttu-id="fb612-145">データベースまたはファイルのオフライン化</span><span class="sxs-lookup"><span data-stu-id="fb612-145">Taking a Database or File Offline</span></span>  
 <span data-ttu-id="fb612-146">オンライン復元を使用しない場合、次のいずれかの方法で、復元シーケンスを開始する前にデータベースをオフラインにできます。</span><span class="sxs-lookup"><span data-stu-id="fb612-146">If you do not want to use online restore, you can take the database offline before you start the restore sequence by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="fb612-147">どの復旧モデルでも、次の [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) ステートメントを使用することにより、データベースをオフラインにできます。</span><span class="sxs-lookup"><span data-stu-id="fb612-147">Under any recovery model, you can take the database offline by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
     <span data-ttu-id="fb612-148">ALTER DATABASE *database_name* SET OFFLINE</span><span class="sxs-lookup"><span data-stu-id="fb612-148">ALTER DATABASE *database_name* SET OFFLINE</span></span>  
  
-   <span data-ttu-id="fb612-149">完全復旧モデルでは、次の [BACKUP LOG](/sql/t-sql/statements/backup-transact-sql) ステートメントを使用してデータベースを復元状態にすることにより、ファイル復元またはページ復元を強制的にオフラインで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="fb612-149">Alternatively, under the full recovery model, you can force a file or page restore to be offline, by using the following [BACKUP LOG](/sql/t-sql/statements/backup-transact-sql) statement put the database in to the restoring state:</span></span>  
  
     <span data-ttu-id="fb612-150">BACKUP LOG *database_name* WITH NORECOVERY.</span><span class="sxs-lookup"><span data-stu-id="fb612-150">BACKUP LOG *database_name* WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="fb612-151">データベースがオフライン状態の間、すべての復元処理はオフライン復元になります。</span><span class="sxs-lookup"><span data-stu-id="fb612-151">As long as a database remains offline, all restores are offline restores.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fb612-152">例</span><span class="sxs-lookup"><span data-stu-id="fb612-152">Examples</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb612-153">オンライン復元シーケンスでは、オフライン復元シーケンスと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fb612-153">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
-   [<span data-ttu-id="fb612-154">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-154">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="fb612-155">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-155">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="fb612-156">例: 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-156">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="fb612-157">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-157">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="fb612-158">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-158">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="fb612-159">例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-159">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="fb612-160">例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-160">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fb612-161">関連タスク</span><span class="sxs-lookup"><span data-stu-id="fb612-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="fb612-162">ファイルおよびファイル グループの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-162">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="fb612-163">ページ復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-163">Restore Pages &#40;SQL Server&#41;</span></span>](restore-pages-sql-server.md)  
  
-   [<span data-ttu-id="fb612-164">suspect_pages テーブルの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-164">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](manage-the-suspect-pages-table-sql-server.md)  
  
-   [<span data-ttu-id="fb612-165">データを復元しないデータベースの復旧 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-165">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  
-   [<span data-ttu-id="fb612-166">機能していないファイル グループの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-166">Remove Defunct Filegroups &#40;SQL Server&#41;</span></span>](remove-defunct-filegroups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="fb612-167">参照</span><span class="sxs-lookup"><span data-stu-id="fb612-167">See Also</span></span>  
 <span data-ttu-id="fb612-168">[ファイルの復元 &#40;完全復旧モデル&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="fb612-168">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="fb612-169">[ファイルの復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="fb612-169">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="fb612-170">[ページ復元 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb612-170">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="fb612-171">[段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb612-171">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 [<span data-ttu-id="fb612-172">復元と復旧の概要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb612-172">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
