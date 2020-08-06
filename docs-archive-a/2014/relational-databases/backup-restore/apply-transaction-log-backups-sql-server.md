---
title: トランザクション ログ バックアップの適用 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], log backups
- transaction log backups [SQL Server], applying backups
- online restores [SQL Server], log backups
- transaction log backups [SQL Server], quantity needed for restore sequence
- backups [SQL Server], log backups
ms.assetid: 9b12be51-5469-46f9-8e86-e938e10aa3a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54c91106f8ca6f15539b4103220860143882c3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640104"
---
# <a name="apply-transaction-log-backups-sql-server"></a><span data-ttu-id="69c01-102">トランザクション ログ バックアップの適用 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="69c01-102">Apply Transaction Log Backups (SQL Server)</span></span>
  <span data-ttu-id="69c01-103">このトピックは完全復旧モデルと一括ログ復旧モデルのみに関連します。</span><span class="sxs-lookup"><span data-stu-id="69c01-103">The topic is relevant only for the full recovery model or bulk-logged recovery model.</span></span>  
  
 <span data-ttu-id="69c01-104">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの復元の一環として行う、トランザクション ログ バックアップの適用について説明します。</span><span class="sxs-lookup"><span data-stu-id="69c01-104">This topic describes applying transaction log backups as part of restoring a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="69c01-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="69c01-105">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="69c01-106">トランザクションログバックアップを復元するための要件</span><span class="sxs-lookup"><span data-stu-id="69c01-106">Requirements for Restoring Transaction Log Backups</span></span>](#Requirements)  
  
-   [<span data-ttu-id="69c01-107">復旧とトランザクションログ</span><span class="sxs-lookup"><span data-stu-id="69c01-107">Recovery and Transaction Logs</span></span>](#RecoveryAndTlogs)  
  
-   [<span data-ttu-id="69c01-108">ログ バックアップを使用した障害発生時までの復元</span><span class="sxs-lookup"><span data-stu-id="69c01-108">Using Log Backups to Restore to the Point of Failure</span></span>](#PITrestore)  
  
-   [<span data-ttu-id="69c01-109">関連タスク</span><span class="sxs-lookup"><span data-stu-id="69c01-109">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="requirements-for-restoring-transaction-log-backups"></a><a name="Requirements"></a><span data-ttu-id="69c01-110">トランザクションログバックアップを復元するための要件</span><span class="sxs-lookup"><span data-stu-id="69c01-110">Requirements for Restoring Transaction Log Backups</span></span>  
 <span data-ttu-id="69c01-111">トランザクション ログ バックアップを適用するには、次の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c01-111">To apply a transaction log backup, the following requirements must be met:</span></span>  
  
-   <span data-ttu-id="69c01-112">**復元シーケンスに必要なログ バックアップの保持:** 復元シーケンスを完了できるだけのログ レコードがバックアップされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c01-112">**Enough Log Backups for a Restore Sequence :** You must have enough log records backed up to complete a restore sequence.</span></span> <span data-ttu-id="69c01-113">復元シーケンスを開始する前に、必要なログ バックアップ (必要な場合は [ログ末尾のバックアップ](tail-log-backups-sql-server.md) も含む) が用意されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c01-113">The necessary log backups, including the [tail-log backup](tail-log-backups-sql-server.md) where required, must be available before the start of the restore sequence.</span></span>  
  
-   <span data-ttu-id="69c01-114">**正しい復元順序:** 先に、データベースの前回の完全バックアップまたは差分バックアップを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c01-114">**Correct restore order:**  The immediately previous full database backup or differential database backup must be restored first.</span></span> <span data-ttu-id="69c01-115">次に、その完全バックアップまたは差分バックアップの後に作成されたすべてのトランザクション ログを日時順に復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c01-115">Then, all transaction logs that are created after that full or differential database backup must be restored in chronological order.</span></span> <span data-ttu-id="69c01-116">このログ チェーン内のトランザクション ログ バックアップが失われたかまたは損傷している場合は、失われたトランザクション ログよりも前のトランザクション ログのみを復元できます。</span><span class="sxs-lookup"><span data-stu-id="69c01-116">If a transaction log backup in this log chain is lost or damaged, you can restore only transaction logs before the missing transaction log.</span></span>  
  
-   <span data-ttu-id="69c01-117">**データベースはまだ復旧されていない:** データベースは、最後のトランザクション ログが適用されるまで復旧できません。</span><span class="sxs-lookup"><span data-stu-id="69c01-117">**Database not yet recovered:**  The database cannot be recovered until after the final transaction log has been applied.</span></span> <span data-ttu-id="69c01-118">いずれかの中間トランザクション ログ バックアップを復元した後 (ログ チェーンが終わる前) にデータベースを復旧する場合、その時点以降にデータベースを復元するには、データベースの完全バックアップから復元シーケンス全体を再度開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c01-118">If you recover the database after restoring one of the intermediate transaction log backups, that before the end of the log chain, you cannot restore the database past that point without restarting the complete restore sequence, starting with the full database backup.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="69c01-119">すべてのログ バックアップを復元することをお勧めします (RESTORE LOG *database_name* WITH NORECOVERY) 。</span><span class="sxs-lookup"><span data-stu-id="69c01-119">A best practice is to restore all the log backups (RESTORE LOG *database_name* WITH NORECOVERY).</span></span> <span data-ttu-id="69c01-120">最後のログ バックアップを復元した後、別の操作でデータベースを復旧します (RESTORE DATABASE *database_name* WITH RECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="69c01-120">Then, after restoring the last log backup, recover the database in a separate operation (RESTORE DATABASE *database_name* WITH RECOVERY).</span></span>  
  
##  <a name="recovery-and-transaction-logs"></a><a name="RecoveryAndTlogs"></a><span data-ttu-id="69c01-121">復旧とトランザクションログ</span><span class="sxs-lookup"><span data-stu-id="69c01-121">Recovery and Transaction Logs</span></span>  
 <span data-ttu-id="69c01-122">復元操作を完了してデータベースを復旧すると、すべての不完全なトランザクションがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="69c01-122">When you finish the restore operation and recover the database, recovery rolls back all incomplete transactions.</span></span> <span data-ttu-id="69c01-123">これを *元に戻すフェーズ*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="69c01-123">This is known as the *undo phase*.</span></span> <span data-ttu-id="69c01-124">データベースの整合性を復元するためにロールバックが必要です。</span><span class="sxs-lookup"><span data-stu-id="69c01-124">Rolling back is required to restore the integrity of the database.</span></span> <span data-ttu-id="69c01-125">ロールバック後、データベースはオンラインになり、そのデータベースにそれ以上のトランザクション ログ バックアップを適用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="69c01-125">After rollback, the database goes online, and no more transaction log backups can be applied to the database.</span></span>  
  
 <span data-ttu-id="69c01-126">たとえば、一連のトランザクション ログ バックアップに、実行時間が長いトランザクションが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="69c01-126">For example, a series of transaction log backups contain a long-running transaction.</span></span> <span data-ttu-id="69c01-127">トランザクションの開始は最初のトランザクション ログ バックアップに記録されていますが、トランザクションの終了は 2 番目のトランザクション ログ バックアップに記録されています。</span><span class="sxs-lookup"><span data-stu-id="69c01-127">The start of the transaction is recorded in the first transaction log backup, but the end of the transaction is recorded in the second transaction log backup.</span></span> <span data-ttu-id="69c01-128">最初のトランザクション ログ バックアップには、コミットやロールバック操作は記録されていません。</span><span class="sxs-lookup"><span data-stu-id="69c01-128">There is no record of a commit or rollback operation in the first transaction log backup.</span></span> <span data-ttu-id="69c01-129">最初のトランザクション ログ バックアップが適用されたときに復旧操作を実行すると、実行時間が長いトランザクションは不完全だと見なされ、そのトランザクションに関して最初のトランザクション ログ バックアップに記録されたデータ変更がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="69c01-129">If a recovery operation runs when the first transaction log backup is applied, the long-running transaction is treated as incomplete, and data modifications recorded in the first transaction log backup for the transaction are rolled back.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="69c01-130">では、この時点より後で 2 番目のトランザクション ログ バックアップを適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="69c01-130">does not allow for the second transaction log backup to be applied after this point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69c01-131">状況によっては、ログの復元中にファイルを明示的に追加できます。</span><span class="sxs-lookup"><span data-stu-id="69c01-131">In some circumstances, you can explicitly add a file during log restore.</span></span>  
  
##  <a name="using-log-backups-to-restore-to-the-point-of-failure"></a><a name="PITrestore"></a><span data-ttu-id="69c01-132">ログバックアップを使用して障害発生時点まで復元する</span><span class="sxs-lookup"><span data-stu-id="69c01-132">Using Log Backups to Restore to the Point of Failure</span></span>  
 <span data-ttu-id="69c01-133">次のような一連のイベントが発生したとします。</span><span class="sxs-lookup"><span data-stu-id="69c01-133">Assume the following sequence of events.</span></span>  
  
|<span data-ttu-id="69c01-134">Time</span><span class="sxs-lookup"><span data-stu-id="69c01-134">Time</span></span>|<span data-ttu-id="69c01-135">Event</span><span class="sxs-lookup"><span data-stu-id="69c01-135">Event</span></span>|  
|----------|-----------|  
|<span data-ttu-id="69c01-136">午前 8 時</span><span class="sxs-lookup"><span data-stu-id="69c01-136">8:00 A.M.</span></span>|<span data-ttu-id="69c01-137">データベースの完全バックアップを作成するために、データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="69c01-137">Back up database to create a full database backup.</span></span>|  
|<span data-ttu-id="69c01-138">正午</span><span class="sxs-lookup"><span data-stu-id="69c01-138">Noon</span></span>|<span data-ttu-id="69c01-139">トランザクション ログのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="69c01-139">Back up transaction log.</span></span>|  
|<span data-ttu-id="69c01-140">午後 4 時</span><span class="sxs-lookup"><span data-stu-id="69c01-140">4:00 P.M.</span></span>|<span data-ttu-id="69c01-141">トランザクション ログのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="69c01-141">Back up transaction log.</span></span>|  
|<span data-ttu-id="69c01-142">午後 6 時</span><span class="sxs-lookup"><span data-stu-id="69c01-142">6:00 P.M.</span></span>|<span data-ttu-id="69c01-143">データベースの完全バックアップを作成するために、データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="69c01-143">Back up database to create a full database backup.</span></span>|  
|<span data-ttu-id="69c01-144">午後 8 時</span><span class="sxs-lookup"><span data-stu-id="69c01-144">8:00 P.M.</span></span>|<span data-ttu-id="69c01-145">トランザクション ログのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="69c01-145">Back up transaction log.</span></span>|  
|<span data-ttu-id="69c01-146">午後 9 時 45 分</span><span class="sxs-lookup"><span data-stu-id="69c01-146">9:45 P.M.</span></span>|<span data-ttu-id="69c01-147">障害が発生します。</span><span class="sxs-lookup"><span data-stu-id="69c01-147">Failure occurs.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="69c01-148">この一連のバックアップの例の詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69c01-148">For an explanation of this example sequence of backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="69c01-149">午後 9時 45分の状態にデータベースを復元するには</span><span class="sxs-lookup"><span data-stu-id="69c01-149">To restore the database to its state at 9:45 P.M.</span></span> <span data-ttu-id="69c01-150">(障害の時点)、次の代替手順のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="69c01-150">(the point of failure), either of the following alternative procedures can be used:</span></span>  
  
 <span data-ttu-id="69c01-151">**代替手順 1: データベースの最新の完全バックアップを使用したデータベースの復元**</span><span class="sxs-lookup"><span data-stu-id="69c01-151">**Alternative 1: Restore the database by using the most recent full database backup**</span></span>  
  
1.  <span data-ttu-id="69c01-152">障害発生時点にアクティブなトランザクション ログのログ末尾のバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="69c01-152">Create a tail-log backup of the currently active transaction log as of the point of failure.</span></span>  
  
2.  <span data-ttu-id="69c01-153">午前 8 時に作成した</span><span class="sxs-lookup"><span data-stu-id="69c01-153">Do not restore the 8:00 A.M.</span></span> <span data-ttu-id="69c01-154">復元よりも処理に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="69c01-154">full database backup.</span></span> <span data-ttu-id="69c01-155">代わりに、より近い時刻の午後 6 時の</span><span class="sxs-lookup"><span data-stu-id="69c01-155">Instead, restore the more recent 6:00 P.M.</span></span> <span data-ttu-id="69c01-156">データベースの完全バックアップを復元してから、午後 8 時の</span><span class="sxs-lookup"><span data-stu-id="69c01-156">full database backup, and then apply the 8:00 P.M.</span></span> <span data-ttu-id="69c01-157">ログ バックアップとログ末尾のバックアップを適用します。</span><span class="sxs-lookup"><span data-stu-id="69c01-157">log backup and the tail-log backup.</span></span>  
  
 <span data-ttu-id="69c01-158">**代替手順 2: データベースの以前の完全バックアップを使用したデータベースの復元**</span><span class="sxs-lookup"><span data-stu-id="69c01-158">**Alternative 2: Restore the database by using an earlier full database backup**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69c01-159">この代替手順は、問題が生じて午後 6 時の</span><span class="sxs-lookup"><span data-stu-id="69c01-159">This alternative process is useful if a problem prevents you from using the 6:00 P.M.</span></span> <span data-ttu-id="69c01-160">復元よりも処理に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="69c01-160">full database backup.</span></span> <span data-ttu-id="69c01-161">この方法では、午後 6 時のデータベースの完全バックアップからの</span><span class="sxs-lookup"><span data-stu-id="69c01-161">This process takes longer than restoring from the 6:00 P.M.</span></span> <span data-ttu-id="69c01-162">復元よりも処理に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="69c01-162">full database backup.</span></span>  
  
1.  <span data-ttu-id="69c01-163">障害発生時点にアクティブなトランザクション ログのログ末尾のバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="69c01-163">Create a tail-log backup of the currently active transaction log as of the point of failure.</span></span>  
  
2.  <span data-ttu-id="69c01-164">午前 8 時に作成した</span><span class="sxs-lookup"><span data-stu-id="69c01-164">Restore the 8:00 A.M.</span></span> <span data-ttu-id="69c01-165">データベースの完全バックアップを復元し、4 つすべてのトランザクション ログ バックアップを順に復元します。</span><span class="sxs-lookup"><span data-stu-id="69c01-165">full database backup, and then restore all four transaction log backups in sequence.</span></span> <span data-ttu-id="69c01-166">これにより、午後 9 時 45 分までに完了したすべてのトランザクションがロールフォワードされます。</span><span class="sxs-lookup"><span data-stu-id="69c01-166">This rolls forward all completed transactions up to 9:45 P.M.</span></span>  
  
     <span data-ttu-id="69c01-167">この代替手順は、一連のデータベースの完全バックアップにまたがるトランザクション ログ バックアップのチェーンを保持することにより、冗長性を伴うセキュリティが提供されることになります。</span><span class="sxs-lookup"><span data-stu-id="69c01-167">This alternative points out the redundant security offered by maintaining a chain of transaction log backups across a series of full database backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69c01-168">場合によっては、トランザクション ログを使用して特定の時点までデータベースを復元することもできます。</span><span class="sxs-lookup"><span data-stu-id="69c01-168">In some cases, you can also use transaction logs to restore a database to a specific point in time.</span></span> <span data-ttu-id="69c01-169">詳細については、「 [SQL Server データベースを特定の時点に復元する方法 &#40;完全復旧モデル&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69c01-169">For more information, [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="69c01-170">関連タスク</span><span class="sxs-lookup"><span data-stu-id="69c01-170">Related Tasks</span></span>  
 <span data-ttu-id="69c01-171">**トランザクション ログのバックアップを適用するには**</span><span class="sxs-lookup"><span data-stu-id="69c01-171">**To apply a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="69c01-172">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69c01-172">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
 <span data-ttu-id="69c01-173">**復旧ポイントまで復元するには**</span><span class="sxs-lookup"><span data-stu-id="69c01-173">**To restore to your recovery point**</span></span>  
  
-   [<span data-ttu-id="69c01-174">完全復旧モデルで障害発生時点までデータベースを復元する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69c01-174">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="69c01-175">SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="69c01-175">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   <span data-ttu-id="69c01-176"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="69c01-176"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  
-   [<span data-ttu-id="69c01-177">マークされたトランザクションを含む関連データベースの復旧</span><span class="sxs-lookup"><span data-stu-id="69c01-177">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [<span data-ttu-id="69c01-178">ログ シーケンス番号への復旧 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69c01-178">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
 <span data-ttu-id="69c01-179">**WITH NORECOVERY を使用してバックアップを復元した後、データベースを回復するには**</span><span class="sxs-lookup"><span data-stu-id="69c01-179">**To recover a database after restoring backups using WITH NORECOVERY**</span></span>  
  
-   [<span data-ttu-id="69c01-180">データを復元しないデータベースの復旧 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69c01-180">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="69c01-181">参照</span><span class="sxs-lookup"><span data-stu-id="69c01-181">See Also</span></span>  
 [<span data-ttu-id="69c01-182">トランザクション ログ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69c01-182">The Transaction Log &#40;SQL Server&#41;</span></span>](../logs/the-transaction-log-sql-server.md)  
  
  
