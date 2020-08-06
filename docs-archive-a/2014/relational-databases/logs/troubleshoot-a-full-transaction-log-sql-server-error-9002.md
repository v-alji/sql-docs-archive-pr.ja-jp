---
title: 満杯になったトランザクション ログのトラブルシューティング (SQL Server エラー 9002) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], full
- troubleshooting [SQL Server], full transaction log
- 9002 (Database Engine error)
- transaction logs [SQL Server], truncation
- backing up transaction logs [SQL Server], full logs
- transaction logs [SQL Server], full log
- full transaction logs [SQL Server]
ms.assetid: 0f23aa84-475d-40df-bed3-c923f8c1b520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d03e259bd0aff8fce02558dbe08efb56748493c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631893"
---
# <a name="troubleshoot-a-full-transaction-log-sql-server-error-9002"></a><span data-ttu-id="cdc4e-102">満杯になったトランザクション ログのトラブルシューティング (SQL Server エラー 9002)</span><span class="sxs-lookup"><span data-stu-id="cdc4e-102">Troubleshoot a Full Transaction Log (SQL Server Error 9002)</span></span>
  <span data-ttu-id="cdc4e-103">このトピックでは、トランザクション ログが満杯になった場合の対処法について説明し、今後トランザクション ログが満杯になるのを防ぐ方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-103">This topic discusses possible responses to a full transaction log and suggests how to avoid it in the future.</span></span> <span data-ttu-id="cdc4e-104">トランザクション ログが満杯になると、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]から 9002 エラーが発行されます。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-104">When the transaction log becomes full, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] issues a 9002 error.</span></span> <span data-ttu-id="cdc4e-105">データベースがオンラインまたは復旧中の場合、ログが満杯になることがあります。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-105">The log can fill when the database is online or in recovery.</span></span> <span data-ttu-id="cdc4e-106">データベースがオンラインのときにログ ファイルがいっぱいになった場合、データベースはオンラインのままです。ただし、更新はできず、読み取りだけが可能です。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-106">If the log fills while the database is online, the database remains online but can only be read, not updated.</span></span> <span data-ttu-id="cdc4e-107">復旧中にログが満杯になった場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によりデータベースが RESOURCE PENDING としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-107">If the log fills during recovery, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] marks the database as RESOURCE PENDING.</span></span> <span data-ttu-id="cdc4e-108">いずれの場合も、ログ領域を使用可能にするためのユーザー操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-108">In either case, user action is required to make log space available.</span></span>  
  
## <a name="responding-to-a-full-transaction-log"></a><span data-ttu-id="cdc4e-109">トランザクション ログが満杯になった場合の対処法</span><span class="sxs-lookup"><span data-stu-id="cdc4e-109">Responding to a Full Transaction Log</span></span>  
 <span data-ttu-id="cdc4e-110">トランザクション ログが満杯になった状況によっては、適切な対処法が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-110">The appropriate response to a full transaction log depends partly on what condition or conditions caused the log to fill.</span></span> <span data-ttu-id="cdc4e-111">特定の条件でログの切り捨てができなくなっている原因を見つけるには、**sys.database** カタログ ビューの **log_reuse_wait** 列と **log_reuse_wait_desc** 列を使用します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-111">To discover what is preventing log truncation in a given case, use the **log_reuse_wait** and **log_reuse_wait_desc** columns of the **sys.database** catalog view.</span></span> <span data-ttu-id="cdc4e-112">詳細については、「[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-112">For more information, see [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).</span></span> <span data-ttu-id="cdc4e-113">ログの切り捨てが遅れる要因については、「[トランザクション ログ &#40;SQL Server&#41;](the-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-113">For descriptions of factors that can delay log truncation, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cdc4e-114">データベースの復旧中に 9002 エラーが発生した場合、問題を解決した後で ALTER DATABASE *database_name* SET ONLINE ステートメントを使用してデータベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-114">If the database was in recovery when the 9002 error occurred, after resolving the problem, recover the database by using ALTER DATABASE *database_name* SET ONLINE.</span></span>  
  
 <span data-ttu-id="cdc4e-115">満杯になったトランザクション ログのその他の対処法には、以下があります。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-115">Alternatives for responding to a full transaction log include:</span></span>  
  
-   <span data-ttu-id="cdc4e-116">ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-116">Backing up the log.</span></span>  
  
-   <span data-ttu-id="cdc4e-117">ディスク領域を解放して、ログが自動的に拡張できるようにします。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-117">Freeing disk space so that the log can automatically grow.</span></span>  
  
-   <span data-ttu-id="cdc4e-118">十分な空き領域があるディスク ドライブにログ ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-118">Moving the log file to a disk drive with sufficient space.</span></span>  
  
-   <span data-ttu-id="cdc4e-119">ログ ファイルのサイズを増やします。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-119">Increasing the size of a log file.</span></span>  
  
-   <span data-ttu-id="cdc4e-120">別のディスクにログ ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-120">Adding a log file on a different disk.</span></span>  
  
-   <span data-ttu-id="cdc4e-121">実行時間の長いトランザクションを完了または強制終了します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-121">Completing or killing a long-running transaction.</span></span>  
  
 <span data-ttu-id="cdc4e-122">これらの対処法については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-122">These alternatives are discussed in the following sections.</span></span> <span data-ttu-id="cdc4e-123">状況に最も適した対処法を選択してください。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-123">Choose a response that fits your situation best.</span></span>  
  
### <a name="backing-up-the-log"></a><span data-ttu-id="cdc4e-124">ログのバックアップ</span><span class="sxs-lookup"><span data-stu-id="cdc4e-124">Backing up the Log</span></span>  
 <span data-ttu-id="cdc4e-125">完全復旧モデルまたは一括ログ復旧モデルでは、トランザクション ログを長期間バックアップしていないと、バックアップによりログの切り捨てが妨げられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-125">Under the full recovery model or bulk-logged recovery model, if the transaction log has not been backed up recently, backup might be what is preventing log truncation.</span></span> <span data-ttu-id="cdc4e-126">これまでにログのバックアップをまったく行っていない場合は、2 つのログ バックアップを作成して、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が最後にバックアップされた時点までログを切り捨てられるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-126">If the log has never been backed up, you must create two log backups to permit the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to truncate the log to the point of the last backup.</span></span> <span data-ttu-id="cdc4e-127">ログを切り捨てると新しいログ レコード用の領域が解放されます。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-127">Truncating the log frees space for new log records.</span></span> <span data-ttu-id="cdc4e-128">ログが再び満杯にならないようにするには、ログを頻繁にバックアップするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-128">To keep the log from filling up again, take log backups frequently.</span></span>  
  
 <span data-ttu-id="cdc4e-129">**トランザクション ログのバックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="cdc4e-129">**To create a transaction log backup**</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cdc4e-130">データベースが破損している場合、「[ログ末尾のバックアップ &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-130">If the database is damaged, see [Tail-Log Backups &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="cdc4e-131">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cdc4e-131">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   <span data-ttu-id="cdc4e-132"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="cdc4e-132"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
### <a name="freeing-disk-space"></a><span data-ttu-id="cdc4e-133">ディスク領域の解放</span><span class="sxs-lookup"><span data-stu-id="cdc4e-133">Freeing Disk Space</span></span>  
 <span data-ttu-id="cdc4e-134">他のファイルを削除または移動することによって、データベースのトランザクション ログ ファイルが保存されているディスク ドライブのディスク領域を解放できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-134">You might be able to free disk space on the disk drive that contains the transaction log file for the database by deleting or moving other files.</span></span> <span data-ttu-id="cdc4e-135">ディスク領域を解放すると、ログ ファイルは自動的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-135">The freed disk space allows the recovery system to enlarge the log file automatically.</span></span>  
  
### <a name="moving-the-log-file-to-a-different-disk"></a><span data-ttu-id="cdc4e-136">別のディスクへのログ ファイルの移動</span><span class="sxs-lookup"><span data-stu-id="cdc4e-136">Moving the Log File to a Different Disk</span></span>  
 <span data-ttu-id="cdc4e-137">現在ログ ファイルが保存されているドライブでディスク領域を十分に解放できない場合は、十分な空き領域がある別のドライブにファイルを移動することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-137">If you cannot free enough disk space on the drive that currently contains the log file, consider moving the file to another drive with sufficient space.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cdc4e-138">ログ ファイルは、圧縮されたファイル システムには配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-138">Log files should never be placed on compressed file systems.</span></span>  
  
 <span data-ttu-id="cdc4e-139">**ログ ファイルを移動するには**</span><span class="sxs-lookup"><span data-stu-id="cdc4e-139">**To move a log file**</span></span>  
  
-   [<span data-ttu-id="cdc4e-140">データベース ファイルの移動</span><span class="sxs-lookup"><span data-stu-id="cdc4e-140">Move Database Files</span></span>](../databases/move-database-files.md)  
  
### <a name="increasing-the-size-of-a-log-file"></a><span data-ttu-id="cdc4e-141">ログ ファイルのサイズの拡張</span><span class="sxs-lookup"><span data-stu-id="cdc4e-141">Increasing the Size of a Log File</span></span>  
 <span data-ttu-id="cdc4e-142">ログ ディスク上に使用可能な領域がある場合、ログ ファイルのサイズを増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-142">If space is available on the log disk, you can increase the size of the log file.</span></span> <span data-ttu-id="cdc4e-143">各ログ ファイルの最大サイズは、2 テラバイト (TB) です。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-143">The maximum size for log files is two terabytes (TB) per log file.</span></span>  
  
 <span data-ttu-id="cdc4e-144">**ファイル サイズを増やすには**</span><span class="sxs-lookup"><span data-stu-id="cdc4e-144">**To increase the file size**</span></span>  
  
 <span data-ttu-id="cdc4e-145">自動拡張が無効に設定されており、データベースがオンラインで、ディスク上に十分な空き領域がある場合、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-145">If autogrow is disabled, the database is online, and sufficient space is available on the disk, either:</span></span>  
  
-   <span data-ttu-id="cdc4e-146">ファイル サイズを手動で増やし、単一の拡張増分値を作成します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-146">Manually increase the file size to produce a single growth increment.</span></span>  
  
-   <span data-ttu-id="cdc4e-147">ALTER DATABASE ステートメントを使用して自動拡張を有効にし、FILEGROWTH オプションに 0 以外の拡張増分値を設定します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-147">Turn on autogrow by using the ALTER DATABASE statement to set a non-zero growth increment for the FILEGROWTH option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cdc4e-148">いずれの場合も、現在のサイズ制限に達している場合は、MAXSIZE 値を増やします。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-148">In either case, if the current size limit has been reached, increase the MAXSIZE value.</span></span>  
  
### <a name="adding-a-log-file-on-a-different-disk"></a><span data-ttu-id="cdc4e-149">別のディスクへのログ ファイルの追加</span><span class="sxs-lookup"><span data-stu-id="cdc4e-149">Adding a Log File on a Different Disk</span></span>  
 <span data-ttu-id="cdc4e-150">ALTER DATABASE <database_name> ADD LOG FILE ステートメントを使用して、十分な領域がある別のディスク上のデータベースに新しいログ ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="cdc4e-150">Add a new log file to the database on a different disk that has sufficient space by using ALTER DATABASE <database_name> ADD LOG FILE.</span></span>  
  
 <span data-ttu-id="cdc4e-151">**ログ ファイルを追加するには**</span><span class="sxs-lookup"><span data-stu-id="cdc4e-151">**To add a log file**</span></span>  
  
-   [<span data-ttu-id="cdc4e-152">データベースに対するデータ ファイルまたはログ ファイルの追加</span><span class="sxs-lookup"><span data-stu-id="cdc4e-152">Add Data or Log Files to a Database</span></span>](../databases/add-data-or-log-files-to-a-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="cdc4e-153">参照</span><span class="sxs-lookup"><span data-stu-id="cdc4e-153">See Also</span></span>  
 <span data-ttu-id="cdc4e-154">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cdc4e-154">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="cdc4e-155">[トランザクション ログ ファイルのサイズの管理](manage-the-size-of-the-transaction-log-file.md) </span><span class="sxs-lookup"><span data-stu-id="cdc4e-155">[Manage the Size of the Transaction Log File](manage-the-size-of-the-transaction-log-file.md) </span></span>  
 <span data-ttu-id="cdc4e-156">[トランザクション ログのバックアップ &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cdc4e-156">[Transaction Log Backups &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="cdc4e-157">sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cdc4e-157">sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql)  
  
  
