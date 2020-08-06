---
title: 遅延トランザクション (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- I/O [SQL Server], database recovery
- restoring pages [SQL Server]
- deferred transactions
- modifying transaction deferred state
ms.assetid: 6fc0f9b6-d3ea-4971-9f27-d0195d1ff718
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 188a0409fbad3f12283adacafbfcb5f176650b72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640102"
---
# <a name="deferred-transactions-sql-server"></a><span data-ttu-id="7cb32-102">遅延トランザクション (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7cb32-102">Deferred Transactions (SQL Server)</span></span>
  <span data-ttu-id="7cb32-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise では、ロールバック (元に戻す) に必要なデータがデータベースの起動時にオフラインになっている場合、損傷したトランザクションが遅延することがあります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise, a corrupted transaction can become deferred if data required by rollback (undo) is offline during database startup.</span></span> <span data-ttu-id="7cb32-104">*遅延トランザクション* は、ロールフォワード フェーズの完了時にコミットされておらず、ロールバックを妨げるエラーが発生しているトランザクションです。</span><span class="sxs-lookup"><span data-stu-id="7cb32-104">A *deferred transaction* is a transaction that is uncommitted when the roll forward phase finishes and that has encountered an error that prevents it from being rolled back.</span></span> <span data-ttu-id="7cb32-105">トランザクションはロールバックできないので、遅延します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-105">Because the transaction cannot be rolled back, it is deferred.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7cb32-106">損傷したトランザクションが遅延するのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise の場合のみです。</span><span class="sxs-lookup"><span data-stu-id="7cb32-106">Corrupted transactions are deferred only in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="7cb32-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のエディションでは、損傷したトランザクションが原因で起動に失敗します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-107">In other editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a corrupted transaction causes startup to fail.</span></span>  
  
 <span data-ttu-id="7cb32-108">通常、遅延トランザクションが発生する原因は、データベースがロールフォワードされている間に、I/O エラーによってトランザクションに必要なページを読み取れなくなったことにあります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-108">Generally, a deferred transaction occurs because, while the database was being rolled forward, an I/O error prevented reading a page that was required by the transaction.</span></span> <span data-ttu-id="7cb32-109">ただし、ファイル レベルのエラーによって遅延トランザクションが発生する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-109">However, an error at the file level can also cause deferred transactions.</span></span> <span data-ttu-id="7cb32-110">また、トランザクションのロールバックが必要な時点で部分復元シーケンスが停止し、トランザクションがオフラインになっているデータを必要とする場合にも、遅延トランザクションが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-110">A deferred transaction can also occur when a partial restore sequence stops at a point at which transaction rollback is necessary and a transaction requires data that is offline.</span></span>  
  
 <span data-ttu-id="7cb32-111">ユーザー トランザクションのロールバック中に I/O エラーが発生すると、データベース全体がオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-111">User transactions that are rolling back and hit an I/O error cause the whole database to go offline.</span></span> <span data-ttu-id="7cb32-112">データベースがオンラインに戻ると、データベースに保持されていたすべてのロックが再実行フェーズで再度取得され、コミットされていないすべてのトランザクションのロールバックが試みられます。</span><span class="sxs-lookup"><span data-stu-id="7cb32-112">When the database is brought back online, the redo reacquires all the locks it had and tries to roll back all the uncommitted transactions.</span></span> <span data-ttu-id="7cb32-113">トランザクションにより変更されるすべてのデータには、トランザクションをロールバックできるまで適切なロックが設定されます。</span><span class="sxs-lookup"><span data-stu-id="7cb32-113">All data modified by a transaction remains appropriately locked until the transaction can roll back.</span></span> <span data-ttu-id="7cb32-114">ロールバックできないトランザクションでロックが解除されるのは、破損が修復されデータベースが再起動されたとき、またはオンライン復元後に、データベースをオンラインにした状態で遅延トランザクションが解決されたときです。</span><span class="sxs-lookup"><span data-stu-id="7cb32-114">Transactions that cannot be rolled back will give up their locks when the corruption is fixed and the database restarted or, after an online restore, when the deferred transactions are resolved while the database remains online.</span></span> <span data-ttu-id="7cb32-115">そのときまで、遅延トランザクションは、ロックを保持することで、データベース全体に対する特定の操作を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="7cb32-115">Until that point, a deferred transaction can hold locks that prevent certain operations on the database as a whole.</span></span> <span data-ttu-id="7cb32-116">たとえば、遅延トランザクションに CREATE TABLE 命令が含まれる場合、遅延トランザクションが解決するまでユーザーはテーブルを作成できません。</span><span class="sxs-lookup"><span data-stu-id="7cb32-116">For example, if a deferred transaction contains a CREATE TABLE instruction, no user can create a table until the deferred transaction has been resolved.</span></span>  
  
 <span data-ttu-id="7cb32-117">また、段階的な部分復元によってデータベースが復旧された時点で、まだ復元されていないオフラインのファイル グループに 1 つ以上のアクティブなトランザクションが影響していることが原因で、遅延トランザクションが発生する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-117">Deferred transaction can also occur because a piecemeal restore recovers a database to a point at which one or more active transactions are affecting a filegroup that has not yet been restored and is offline.</span></span> <span data-ttu-id="7cb32-118">これらのトランザクションはロールバックできないため、遅延トランザクションになります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-118">Because the transactions cannot be rolled back, they become deferred.</span></span>  
  
 <span data-ttu-id="7cb32-119">次の表に、データベースで復旧を引き起こす操作および I/O に問題が発生した場合の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-119">The following table lists the actions that cause a database to perform recovery and the outcome if an I/O problem occurs.</span></span>  
  
|<span data-ttu-id="7cb32-120">アクション</span><span class="sxs-lookup"><span data-stu-id="7cb32-120">Action</span></span>|<span data-ttu-id="7cb32-121">解決方法 (I/O の問題が発生する場合または必要なデータがオフラインの場合)</span><span class="sxs-lookup"><span data-stu-id="7cb32-121">Resolution (if I/O problems occur or required data is offline)</span></span>|  
|------------|-----------------------------------------------------------------------|  
|<span data-ttu-id="7cb32-122">サーバーの起動</span><span class="sxs-lookup"><span data-stu-id="7cb32-122">Server start</span></span>|<span data-ttu-id="7cb32-123">遅延トランザクション</span><span class="sxs-lookup"><span data-stu-id="7cb32-123">Deferred transaction</span></span>|  
|<span data-ttu-id="7cb32-124">復元</span><span class="sxs-lookup"><span data-stu-id="7cb32-124">Restore</span></span>|<span data-ttu-id="7cb32-125">遅延トランザクション</span><span class="sxs-lookup"><span data-stu-id="7cb32-125">Deferred transaction</span></span>|  
|<span data-ttu-id="7cb32-126">Attach</span><span class="sxs-lookup"><span data-stu-id="7cb32-126">Attach</span></span>|<span data-ttu-id="7cb32-127">アタッチの失敗</span><span class="sxs-lookup"><span data-stu-id="7cb32-127">Attach fails</span></span>|  
|<span data-ttu-id="7cb32-128">Autorestart</span><span class="sxs-lookup"><span data-stu-id="7cb32-128">Autorestart</span></span>|<span data-ttu-id="7cb32-129">遅延トランザクション</span><span class="sxs-lookup"><span data-stu-id="7cb32-129">Deferred transaction</span></span>|  
|<span data-ttu-id="7cb32-130">データベースまたはデータベース スナップショットの作成</span><span class="sxs-lookup"><span data-stu-id="7cb32-130">Create database or database snapshot</span></span>|<span data-ttu-id="7cb32-131">作成の失敗</span><span class="sxs-lookup"><span data-stu-id="7cb32-131">Creation fails</span></span>|  
|<span data-ttu-id="7cb32-132">データベース ミラーリングの再実行</span><span class="sxs-lookup"><span data-stu-id="7cb32-132">Redo on database mirroring</span></span>|<span data-ttu-id="7cb32-133">遅延トランザクション</span><span class="sxs-lookup"><span data-stu-id="7cb32-133">Deferred transaction</span></span>|  
|<span data-ttu-id="7cb32-134">ファイル グループのオフライン化</span><span class="sxs-lookup"><span data-stu-id="7cb32-134">Filegroup is offline</span></span>|<span data-ttu-id="7cb32-135">遅延トランザクション</span><span class="sxs-lookup"><span data-stu-id="7cb32-135">Deferred transaction</span></span>|  
  
## <a name="moving-a-transaction-out-of-the-deferred-state"></a><span data-ttu-id="7cb32-136">トランザクションの DEFERRED 状態の解決</span><span class="sxs-lookup"><span data-stu-id="7cb32-136">Moving a Transaction Out of the DEFERRED State</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7cb32-137">遅延トランザクションにより、トランザクション ログはアクティブなままになります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-137">Deferred transactions keep the transaction log active.</span></span> <span data-ttu-id="7cb32-138">遅延トランザクションを保持する仮想ログ ファイルは、これらのトランザクションが遅延状態ではなくなるまで、切り捨てることができません。</span><span class="sxs-lookup"><span data-stu-id="7cb32-138">A virtual log file that contains any deferred transactions cannot be truncated until those transactions are moved out of the deferred state.</span></span> <span data-ttu-id="7cb32-139">ログの切り捨ての詳細については、「[トランザクション ログ &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cb32-139">For more information about log truncation, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="7cb32-140">トランザクションの遅延を解決するには、I/O エラーのない状態でデータベースを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-140">To move the transaction out of the deferred state, the database must start cleanly without any I/O errors.</span></span> <span data-ttu-id="7cb32-141">遅延トランザクションが存在する場合は、I/O エラーの原因を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-141">If deferred transactions exist, you must fix the source of the I/O errors.</span></span> <span data-ttu-id="7cb32-142">利用可能な解決策を、通常で行われる順序で記載すると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-142">The available solutions, listed in the order in which they are typically tried, are as follows:</span></span>  
  
-   <span data-ttu-id="7cb32-143">データベースを再起動します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-143">Restart the database.</span></span> <span data-ttu-id="7cb32-144">問題が一時的なものである場合、遅延トランザクションが発生することなくデータベースが起動します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-144">If the problem was transient, the database should start without deferred transactions.</span></span>  
  
-   <span data-ttu-id="7cb32-145">ファイル グループがオフラインになっていたためにトランザクションが遅延した場合、ファイル グループをオンラインに戻します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-145">If the transactions were deferred because a filegroup was offline, bring the filegroup back online.</span></span>  
  
     <span data-ttu-id="7cb32-146">オフラインのファイル グループをオンラインに戻すには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-146">To bring an offline filegroup back online, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    RESTORE DATABASE database_name FILEGROUP=<filegroup_name>  
    ```  
  
-   <span data-ttu-id="7cb32-147">データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-147">Restore the database.</span></span> <span data-ttu-id="7cb32-148">オフライン復元後は、すべての遅延トランザクションが解決されます。</span><span class="sxs-lookup"><span data-stu-id="7cb32-148">After an online restore, any deferred transactions are resolved.</span></span>  
  
     <span data-ttu-id="7cb32-149">完全復旧モデルまたは一括ログ復旧モデルでは、少数の破損したページによって遅延トランザクションが発生した場合、オンライン ページ復元によってエラーが解決することがあります (サポートされている場合)。</span><span class="sxs-lookup"><span data-stu-id="7cb32-149">Under the full or bulk-logged recovery model, if the deferred transactions were caused by only a few corrupted pages, an online page restore might resolve the errors (where supported).</span></span>  
  
-   <span data-ttu-id="7cb32-150">遅延トランザクションの原因となっているオフライン状態のファイル グループが不要になった場合は、これらのファイル グループが機能しないようにします。</span><span class="sxs-lookup"><span data-stu-id="7cb32-150">If you are no longer require a filegroup whose offline status is causing deferred transactions, make the offline filegroup defunct.</span></span> <span data-ttu-id="7cb32-151">ファイル グループがオフラインであったことが原因で遅延されたトランザクションは、ファイル グループを機能していない状態にすると、遅延状態ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="7cb32-151">Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7cb32-152">機能していないファイル グループを復旧することはできません。</span><span class="sxs-lookup"><span data-stu-id="7cb32-152">A defunct filegroup can never be recovered.</span></span>  
  
     <span data-ttu-id="7cb32-153">詳細については、「 [機能していないファイル グループの削除 &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cb32-153">For more information, see [Remove Defunct Filegroups &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="7cb32-154">不適切なページが原因でトランザクションが遅延し、適切なデータベースのバックアップが存在しない場合、データベースを修復するには、次のプロセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7cb32-154">If transactions were deferred because of a bad page and if a good backup of the database does not exist, use the following process to repair the database:</span></span>  
  
    -   <span data-ttu-id="7cb32-155">最初に、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行して、データベースを緊急モードにします。</span><span class="sxs-lookup"><span data-stu-id="7cb32-155">First put the database into emergency mode by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
        ```  
        ALTER DATABASE <database_name> SET EMERGENCY  
        ```  
  
         <span data-ttu-id="7cb32-156">緊急モードの詳細については、「 [データベースの状態](../databases/database-states.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cb32-156">For information about emergency mode, see [Database States](../databases/database-states.md).</span></span>  
  
    -   <span data-ttu-id="7cb32-157">次に、下記の DBCC ステートメントのいずれかで DBCC REPAIR_ALLOW_DATA_LOSS オプションを使用してデータベースを修復します: [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)、[DBCC CHECKALLOC](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)、または [DBCC CHECKTABLE](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7cb32-157">Then, repair the database by using the DBCC REPAIR_ALLOW_DATA_LOSS option in one of the following DBCC statements: [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql), [DBCC CHECKALLOC](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql), or [DBCC CHECKTABLE](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql).</span></span>  
  
         <span data-ttu-id="7cb32-158">DBCC では、不適切なページが検出されると、そのページの割り当てが解除され、関連するすべてのエラーが修復されます。</span><span class="sxs-lookup"><span data-stu-id="7cb32-158">When DBCC encounters the bad page, DBCC deallocates it and repairs any related errors.</span></span> <span data-ttu-id="7cb32-159">この方法を使用すると、物理的に一貫性のある状態でデータベースをオンラインに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="7cb32-159">This approach enables the database to be brought back online in a physically consistent state.</span></span> <span data-ttu-id="7cb32-160">ただし、追加されたデータが失われる場合もあるため、この方法は最後の手段として使用してください。</span><span class="sxs-lookup"><span data-stu-id="7cb32-160">However, additional data might also be lost; therefore, this approach should be used as a last resort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb32-161">参照</span><span class="sxs-lookup"><span data-stu-id="7cb32-161">See Also</span></span>  
 <span data-ttu-id="7cb32-162">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7cb32-162">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="7cb32-163">[機能していないファイル グループの削除 &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7cb32-163">[Remove Defunct Filegroups &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="7cb32-164">[ファイルの復元 &#40;完全復旧モデル&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="7cb32-164">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="7cb32-165">[ファイルの復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="7cb32-165">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="7cb32-166">[ページ復元 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7cb32-166">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="7cb32-167">[段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7cb32-167">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="7cb32-168">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7cb32-168">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="7cb32-169">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7cb32-169">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
