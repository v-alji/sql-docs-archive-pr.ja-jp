---
title: データベース ミラーリングの一時停止と再開 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- sessions [SQL Server], database mirroring
- resuming database mirroring
- database mirroring [SQL Server], pausing
- database mirroring [SQL Server], resuming
- pausing database mirroring
ms.assetid: c67802c6-ee8c-4cbd-a6d4-f7b80413a4ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c231876b11303992e0e3300c9cb73c0cf53b3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716793"
---
# <a name="pausing-and-resuming-database-mirroring-sql-server"></a><span data-ttu-id="a06b7-102">データベース ミラーリングの一時停止と再開 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a06b7-102">Pausing and Resuming Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="a06b7-103">データベースの所有者は、データベース ミラーリング セッションを任意の時点で一時停止し、後から再開できます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-103">The database owner can pause and later resume a database mirroring session at any time.</span></span> <span data-ttu-id="a06b7-104">一時停止では、ミラーリングは中断しますが、セッションの状態は保たれます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-104">Pausing preserves the session state while suspending mirroring.</span></span> <span data-ttu-id="a06b7-105">一時停止は、ボトルネックの発生中にプリンシパル サーバーのパフォーマンスを向上させる場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-105">During bottlenecks, pausing might be useful to improve performance on the principal server.</span></span>  
  
 <span data-ttu-id="a06b7-106">セッションが一時停止されても、プリンシパル データベースは引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-106">When a session is paused, the principal database remains available.</span></span> <span data-ttu-id="a06b7-107">一時停止によりミラーリング セッションの状態が一時中断に設定されるので、ミラー データベースがプリンシパル データベースの最新状態を反映しなくなり、プリンシパル データベースが危険に曝されることになります。</span><span class="sxs-lookup"><span data-stu-id="a06b7-107">Pausing sets the state of the mirroring session to SUSPENDED, and the mirror database no longer keeps up with the principal database, causing the principal database to run exposed.</span></span>  
  
 <span data-ttu-id="a06b7-108">一時停止したセッションはすぐに再開することをお勧めします。データベース ミラーリング セッションが一時停止している間は、トランザクション ログの切り捨てが実行されないからです。</span><span class="sxs-lookup"><span data-stu-id="a06b7-108">We recommend that you resume a paused session quickly, because as long as a database mirroring session remains paused, the transaction log cannot be truncated.</span></span> <span data-ttu-id="a06b7-109">したがって、データベース ミラーリング セッションが長時間一時停止になっていると、トランザクション ログがいっぱいになり、データベースを利用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a06b7-109">Therefore, if a database mirroring session is paused for too long, the transaction log fills up, making the database unavailable.</span></span> <span data-ttu-id="a06b7-110">原因の詳細については、このトピックの「一時停止および再開がログ切り捨てに与える影響」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a06b7-110">For an explanation of why this happens, see "How Pausing and Resuming Affect Log Truncation," later in this topic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a06b7-111">強制されたサービスに続いて元のプリンシパル サーバーが再接続されると、ミラーリングが中断されます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-111">Following a forced service, when the original principal server reconnects mirroring is suspended.</span></span> <span data-ttu-id="a06b7-112">この状況でミラーリングを再開すると、元のプリンシパル サーバーのデータが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a06b7-112">Resuming mirroring in this situation could possibly cause data loss on the original principal server.</span></span> <span data-ttu-id="a06b7-113">データ損失の可能性への対処の詳細については、「 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a06b7-113">For information about managing the potential data loss, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="a06b7-114">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a06b7-114">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="a06b7-115">一時停止および再開がログ切り捨てに与える影響</span><span class="sxs-lookup"><span data-stu-id="a06b7-115">How Pausing and Resuming Affect Log Truncation</span></span>](#EffectOnLogTrunc)  
  
-   [<span data-ttu-id="a06b7-116">トランザクション ログがいっぱいになった状態の回避</span><span class="sxs-lookup"><span data-stu-id="a06b7-116">Avoid a Full Transaction Log</span></span>](#AvoidFullLog)  
  
-   [<span data-ttu-id="a06b7-117">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a06b7-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="how-pausing-and-resuming-affect-log-truncation"></a><a name="EffectOnLogTrunc"></a> <span data-ttu-id="a06b7-118">一時停止および再開がログ切り捨てに与える影響</span><span class="sxs-lookup"><span data-stu-id="a06b7-118">How Pausing and Resuming Affect Log Truncation</span></span>  
 <span data-ttu-id="a06b7-119">通常、データベースで自動チェックポイントが実行されている場合は、次のログ バックアップの後、そのチェックポイントまでトランザクション ログが切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-119">Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup.</span></span> <span data-ttu-id="a06b7-120">データベース ミラーリング セッションが一時停止している間は、プリンシパル サーバーがミラー サーバーへのログ レコードの送信待ち状態になるため、現在のログ レコードがすべてアクティブなまま保持されます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-120">While a database mirroring session remains paused, all of the current log records remain active because the principal server is waiting to send them to the mirror server.</span></span> <span data-ttu-id="a06b7-121">セッションが再開されてプリンシパル サーバーがログ レコードをミラー サーバーに送信するまでの間、未送信のログ レコードがプリンシパル データベースのトランザクション ログに蓄積されます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-121">The unsent log records accumulate in the transaction log of the principal database until the session resumes and the principal server has sent the log records to the mirror server.</span></span>  
  
 <span data-ttu-id="a06b7-122">セッションが再開されると、プリンシパル サーバーは蓄積されたログ レコードを直ちにミラー サーバーに送信し始めます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-122">When the session is resumed, the principal server immediately begins sending the accumulated log records to the mirror server.</span></span> <span data-ttu-id="a06b7-123">ミラー サーバーが最も古い自動チェックポイントに対応するログ レコードをキューに格納したことを確認したら、プリンシパル サーバーはプリンシパル データベースのログをそのチェックポイントまで切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-123">After the mirror server confirms that it has queued the log record corresponding to the oldest automatic checkpoint, the principal server truncates the log of the principal database to that checkpoint.</span></span> <span data-ttu-id="a06b7-124">ミラー サーバーは同じログ レコードの再実行キューを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-124">The mirror server truncates the redo queue at the same log record.</span></span> <span data-ttu-id="a06b7-125">連続する各チェックポイントでこのプロセスが繰り返されるため、チェックポイントごとに段階的にログが切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-125">As this process is repeated for each successive checkpoint, the log is truncated in stages, checkpoint by checkpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a06b7-126">チェックポイントおよびログ切り捨ての詳細については、「[データベース チェックポイント &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a06b7-126">For more information about the checkpoints and log truncation, see [Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md).</span></span>  
  
##  <a name="avoid-a-full-transaction-log"></a><a name="AvoidFullLog"></a> <span data-ttu-id="a06b7-127">トランザクション ログがいっぱいになった状態の回避</span><span class="sxs-lookup"><span data-stu-id="a06b7-127">Avoid a Full Transaction Log</span></span>  
 <span data-ttu-id="a06b7-128">最大サイズに到達したか、サーバー インスタンスの領域が不足して、ログがいっぱいになると、データベースではそれ以上の更新を実行できません。</span><span class="sxs-lookup"><span data-stu-id="a06b7-128">If the log fills up (either because it reaches its maximum size or the server instance runs out of space), the database cannot perform any more updates.</span></span> <span data-ttu-id="a06b7-129">この問題を防ぐには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="a06b7-129">To avoid this problem, you have two alternatives:</span></span>  
  
-   <span data-ttu-id="a06b7-130">ログがいっぱいになる前に、データベース ミラーリング セッションを再開します。またはログ領域を増やします。</span><span class="sxs-lookup"><span data-stu-id="a06b7-130">Resume the database mirroring session before the log fills up, or add more log space.</span></span> <span data-ttu-id="a06b7-131">データベース ミラーリングを再開すると、累積されたアクティブなログがプリンシパル サーバーからミラー サーバーに送信され、ミラー データベースが同期中の状態になります。</span><span class="sxs-lookup"><span data-stu-id="a06b7-131">Resuming database mirroring lets the principal server send its accumulated active log to the mirror server and puts the mirror database in the SYNCHRONIZING state.</span></span> <span data-ttu-id="a06b7-132">次に、ミラー サーバーがログをディスクに固定し、再実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="a06b7-132">The mirror server can then harden the log to disk and start to redo it.</span></span>  
  
-   <span data-ttu-id="a06b7-133">ミラー化を解除して、データベース ミラーリング セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="a06b7-133">Stop the database mirroring session by removing mirroring.</span></span>  
  
     <span data-ttu-id="a06b7-134">セッションの一時停止とは異なり、ミラー化を解除することにより、ミラーリング セッションに関するすべての情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-134">Unlike pausing a session, removing mirroring drops all information about the mirroring session.</span></span> <span data-ttu-id="a06b7-135">各パートナー サーバー インスタンスでは、データベースの独自のコピーが保持されます。</span><span class="sxs-lookup"><span data-stu-id="a06b7-135">Each partner server instance retains its own copy of the database.</span></span> <span data-ttu-id="a06b7-136">以前のミラー コピーを復旧した場合、そのコピーは以前のプリンシパル コピーから派生し、セッションが一時停止されてから経過した時間だけ遅延が生じたものになります。</span><span class="sxs-lookup"><span data-stu-id="a06b7-136">If the former mirror copy is recovered, it will have diverged from the former principal copy and be behind by the amount of time that has elapsed since the session was paused.</span></span> <span data-ttu-id="a06b7-137">詳細については、「 [データベース ミラーリングの削除 &#40;SQL Server&#41;](database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a06b7-137">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a06b7-138">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a06b7-138">Related Tasks</span></span>  
 <span data-ttu-id="a06b7-139">**データベース ミラーリングを一時停止または再開するには**</span><span class="sxs-lookup"><span data-stu-id="a06b7-139">**To pause or resume database mirroring**</span></span>  
  
-   [<span data-ttu-id="a06b7-140">データベース ミラーリング セッションを一時停止または再開する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a06b7-140">Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;</span></span>](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
 <span data-ttu-id="a06b7-141">**データベース ミラーリングを停止するには**</span><span class="sxs-lookup"><span data-stu-id="a06b7-141">**To stop database mirroring**</span></span>  
  
-   [<span data-ttu-id="a06b7-142">データベース ミラーリングを削除する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a06b7-142">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="a06b7-143">参照</span><span class="sxs-lookup"><span data-stu-id="a06b7-143">See Also</span></span>  
 <span data-ttu-id="a06b7-144">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a06b7-144">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="a06b7-145">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a06b7-145">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="a06b7-146">データベース ミラーリングの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a06b7-146">Removing Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
