---
title: トランザクション ログのバックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], transaction logs
- transaction log backups [SQL Server], creating
- log backups [SQL Server[
- transaction log backups [SQL Server], sequencing
ms.assetid: f4a44a35-0f44-4a42-91d5-d73ac658a3b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 752447d6c38a2df0fcbdce72fbba12edd7a9eeb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718315"
---
# <a name="transaction-log-backups-sql-server"></a><span data-ttu-id="6b3e1-102">トランザクション ログのバックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6b3e1-102">Transaction Log Backups (SQL Server)</span></span>
  <span data-ttu-id="6b3e1-103">このトピックは、完全復旧モデルまたは一括ログ復旧モデルを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのみに関連しています。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-103">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span> <span data-ttu-id="6b3e1-104">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのトランザクション ログのバックアップについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-104">This topic discusses backing up the transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="6b3e1-105">少なくとも 1 つの完全バックアップを作成しておかなければ、ログ バックアップを作成できません。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-105">Minimally, you must have created at least one full backup before you can create any log backups.</span></span> <span data-ttu-id="6b3e1-106">完全バックアップを作成しておくと、いつでもトランザクション ログをバックアップできます。ただし、そのログのバックアップが既に進行中である場合、バックアップを開始できません。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-106">After that, the transaction log can be backed up at any time unless the log is already being backed up.</span></span> <span data-ttu-id="6b3e1-107">作業損失の可能性を最小限に抑え、トランザクション ログを切り捨てられるように、ログ バックアップを頻繁に行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-107">We recommend that you take log backups frequently, both to minimize work loss exposure and to truncate the transaction log.</span></span> <span data-ttu-id="6b3e1-108">一般的に、データベース管理者は完全バックアップを定期的に (たとえば週 1 回) 作成しますが、必要に応じて短い間隔で (たとえば 1 日 1 回) 差分データベース バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-108">Typically, a database administrator creates a full database backup occasionally, such as weekly, and, optionally, creates a series of differential database backup at a shorter interval, such as daily.</span></span> <span data-ttu-id="6b3e1-109">データベース バックアップとは別に、トランザクション ログのバックアップを頻繁に (たとえば 10 分おきに) 作成します。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-109">Independently of the database backups, the database administrator backs up the transaction log at frequent intervals, such as every 10 minutes.</span></span> <span data-ttu-id="6b3e1-110">最適なバックアップ間隔は、バックアップの種類に応じて、データの重要度、データベースのサイズ、サーバーの作業負荷などの要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-110">For a given type of backup, the optimal interval depends on factors such as the importance of the data, the size of the database, and the workload of the server.</span></span>  
  
 <span data-ttu-id="6b3e1-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6b3e1-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="6b3e1-112">一連のログバックアップの動作</span><span class="sxs-lookup"><span data-stu-id="6b3e1-112">How a Sequence of Log Backups Works</span></span>](#LogBackupSequence)  
  
-   [<span data-ttu-id="6b3e1-113">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="6b3e1-113">Recommendations</span></span>](#Recommendations)  
  
-   [<span data-ttu-id="6b3e1-114">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6b3e1-114">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="6b3e1-115">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6b3e1-115">Related Content</span></span>](#RelatedContent)  
  
##  <a name="how-a-sequence-of-log-backups-works"></a><a name="LogBackupSequence"></a><span data-ttu-id="6b3e1-116">一連のログバックアップの動作</span><span class="sxs-lookup"><span data-stu-id="6b3e1-116">How a Sequence of Log Backups Works</span></span>  
 <span data-ttu-id="6b3e1-117">トランザクション ログのバックアップの *ログ チェーン* のシーケンスは、データのバックアップとは関連がありません。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-117">The sequence of transaction log backups *log chain* is independent of data backups.</span></span> <span data-ttu-id="6b3e1-118">たとえば、次の一連のイベントが発生したとします。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-118">For example, assume the following sequence of events.</span></span>  
  
|<span data-ttu-id="6b3e1-119">Time</span><span class="sxs-lookup"><span data-stu-id="6b3e1-119">Time</span></span>|<span data-ttu-id="6b3e1-120">Event</span><span class="sxs-lookup"><span data-stu-id="6b3e1-120">Event</span></span>|  
|----------|-----------|  
|<span data-ttu-id="6b3e1-121">午前 8 時</span><span class="sxs-lookup"><span data-stu-id="6b3e1-121">8:00 A.M.</span></span>|<span data-ttu-id="6b3e1-122">データベースのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-122">Back up database.</span></span>|  
|<span data-ttu-id="6b3e1-123">正午</span><span class="sxs-lookup"><span data-stu-id="6b3e1-123">Noon</span></span>|<span data-ttu-id="6b3e1-124">トランザクション ログのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-124">Back up transaction log.</span></span>|  
|<span data-ttu-id="6b3e1-125">午後 4 時</span><span class="sxs-lookup"><span data-stu-id="6b3e1-125">4:00 P.M.</span></span>|<span data-ttu-id="6b3e1-126">トランザクション ログのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-126">Back up transaction log.</span></span>|  
|<span data-ttu-id="6b3e1-127">午後 6 時</span><span class="sxs-lookup"><span data-stu-id="6b3e1-127">6:00 P.M.</span></span>|<span data-ttu-id="6b3e1-128">データベースのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-128">Back up database.</span></span>|  
|<span data-ttu-id="6b3e1-129">午後 8 時</span><span class="sxs-lookup"><span data-stu-id="6b3e1-129">8:00 P.M.</span></span>|<span data-ttu-id="6b3e1-130">トランザクション ログのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-130">Back up transaction log.</span></span>|  
  
 <span data-ttu-id="6b3e1-131">午後 8 時に作成されたトランザクション ログ バックアップには、</span><span class="sxs-lookup"><span data-stu-id="6b3e1-131">The transaction log backup created at 8:00 P.M.</span></span> <span data-ttu-id="6b3e1-132">午後 4 時から午後 8 時までのトランザクション ログ レコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-132">contains transaction log records from 4:00 P.M.</span></span> <span data-ttu-id="6b3e1-133">その間、午後 6 時に、データベースの完全バックアップが作成されています。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-133">through 8:00 P.M., spanning the time when the full database backup was created at 6:00 P.M.</span></span> <span data-ttu-id="6b3e1-134">トランザクション ログ バックアップのシーケンスは、午前 8 時に最初にデータベースの完全バックアップが作成されて以降、</span><span class="sxs-lookup"><span data-stu-id="6b3e1-134">The sequence of transaction log backups is continuous from the initial full database backup created at 8:00 A.M.</span></span> <span data-ttu-id="6b3e1-135">午後 8 時に作成された最後のトランザクション ログ バックアップまで継続しています。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-135">to the last transaction log backup created at 8:00 P.M.</span></span> <span data-ttu-id="6b3e1-136">これらのログ バックアップを適用する方法の詳細については、「 [トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)」の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-136">For information about how to apply these log backups, see the example in [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6b3e1-137">推奨事項</span><span class="sxs-lookup"><span data-stu-id="6b3e1-137">Recommendations</span></span>  
  
-   <span data-ttu-id="6b3e1-138">トランザクション ログが破損すると、前回の有効なバックアップ以降に行われた作業が失われます。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-138">If a transaction log is damaged, work that is performed since the most recent valid backup is lost.</span></span> <span data-ttu-id="6b3e1-139">そのため、ログ ファイルはフォールト トレランス ストレージに置くことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-139">Therefore we strongly recommend that you put your log files on fault-tolerant storage.</span></span>  
  
-   <span data-ttu-id="6b3e1-140">データベースが破損した場合、またはデータベースを復元する場合は、 [ログ末尾のバックアップ](tail-log-backups-sql-server.md) を作成して、データベースを現在の状態に復元できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-140">If a database is damaged or you are about to restore the database, we recommend that you create a [tail-log backup](tail-log-backups-sql-server.md) to enable you to restore the database to the current point in time.</span></span>  
  
-   <span data-ttu-id="6b3e1-141">既定では、バックアップ操作が成功するたびに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにエントリが 1 つ追加されます。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-141">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="6b3e1-142">ログを頻繁にバックアップすると、これらの成功メッセージがすぐに蓄積され、他のメッセージを探すのが困難になるほどエラー ログが大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-142">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="6b3e1-143">そのような場合、これらのエントリに依存するスクリプトがなければ、トレース フラグ 3226 を使用することによってこれらのログ エントリを除外できます。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-143">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="6b3e1-144">詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-144">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6b3e1-145">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6b3e1-145">Related Tasks</span></span>  
 <span data-ttu-id="6b3e1-146">**トランザクション ログのバックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="6b3e1-146">**To create a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="6b3e1-147">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6b3e1-147">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   <span data-ttu-id="6b3e1-148"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="6b3e1-148"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
 <span data-ttu-id="6b3e1-149">バックアップ ジョブのスケジュールを設定するには、「 [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b3e1-149">To schedule backup jobs, see [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="6b3e1-150">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6b3e1-150">Related Content</span></span>  
 <span data-ttu-id="6b3e1-151">[なし] :</span><span class="sxs-lookup"><span data-stu-id="6b3e1-151">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b3e1-152">参照</span><span class="sxs-lookup"><span data-stu-id="6b3e1-152">See Also</span></span>  
 <span data-ttu-id="6b3e1-153">[トランザクション ログ &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b3e1-153">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="6b3e1-154">[SQL Server データベースのバックアップと復元](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="6b3e1-154">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="6b3e1-155">[ログ末尾のバックアップ &#40;SQL Server&#41;](tail-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b3e1-155">[Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="6b3e1-156">トランザクション ログ バックアップの適用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6b3e1-156">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](transaction-log-backups-sql-server.md)  
  
  
