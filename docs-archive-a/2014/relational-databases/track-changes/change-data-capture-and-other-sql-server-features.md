---
title: 変更データ キャプチャとその他の SQL Server 機能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], other SQL Server features and
ms.assetid: 7dfcb362-1904-4578-8274-da16681a960e
author: rothja
ms.author: jroth
ms.openlocfilehash: acafd5ba49bec92fd4c6b93c4163affaa42ab7f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642649"
---
# <a name="change-data-capture-and-other-sql-server-features"></a><span data-ttu-id="3be04-102">変更データ キャプチャとその他の SQL Server 機能</span><span class="sxs-lookup"><span data-stu-id="3be04-102">Change Data Capture and Other SQL Server Features</span></span>
  <span data-ttu-id="3be04-103">このトピックでは、次の機能と変更データ キャプチャとの連携について説明します。</span><span class="sxs-lookup"><span data-stu-id="3be04-103">This topic describes how the following features interact with change data capture:</span></span>  
  
-   [<span data-ttu-id="3be04-104">Change tracking</span><span class="sxs-lookup"><span data-stu-id="3be04-104">Change tracking</span></span>](#ChangeTracking)  
  
-   [<span data-ttu-id="3be04-105">データベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="3be04-105">Database mirroring</span></span>](#DatabaseMirroring)  
  
-   [<span data-ttu-id="3be04-106">トランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="3be04-106">Transactional replication</span></span>](#TransReplication)  
  
-   [<span data-ttu-id="3be04-107">変更データ キャプチャが有効になっているデータベースの復元またはアタッチ</span><span class="sxs-lookup"><span data-stu-id="3be04-107">Restoring or Attaching a Database Enabled for Change Data Capture</span></span>](#RestoreOrAttach)  
  
##  <a name="change-tracking"></a><a name="ChangeTracking"></a> <span data-ttu-id="3be04-108">変更の追跡</span><span class="sxs-lookup"><span data-stu-id="3be04-108">Change Tracking</span></span>  
 <span data-ttu-id="3be04-109">変更データ キャプチャと [変更の追跡](about-change-tracking-sql-server.md) は、同じデータベースで有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3be04-109">Change data capture and [change tracking](about-change-tracking-sql-server.md) can be enabled on the same database.</span></span> <span data-ttu-id="3be04-110">特に注意が必要な点はありません。</span><span class="sxs-lookup"><span data-stu-id="3be04-110">No special considerations are required.</span></span> <span data-ttu-id="3be04-111">詳細については、「[変更の追跡のしくみ &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3be04-111">For more information, see [Work with Change Tracking &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md).</span></span>  
  
##  <a name="database-mirroring"></a><a name="DatabaseMirroring"></a> <span data-ttu-id="3be04-112">データベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="3be04-112">Database Mirroring</span></span>  
 <span data-ttu-id="3be04-113">変更データ キャプチャが有効になっているデータベースをミラー化できます。</span><span class="sxs-lookup"><span data-stu-id="3be04-113">A database that is enabled for change data capture can be mirrored.</span></span> <span data-ttu-id="3be04-114">フェールオーバー後にキャプチャとクリーンアップが自動的に行われるようにするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3be04-114">To ensure that capture and cleanup happen automatically after a failover, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3be04-115">新しいプリンシパル サーバー インスタンスで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3be04-115">Ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running on the new principal server instance.</span></span>  
  
2.  <span data-ttu-id="3be04-116">新しいプリンシパル データベース (以前のミラー データベース) にキャプチャ ジョブとクリーンアップ ジョブを作成します。</span><span class="sxs-lookup"><span data-stu-id="3be04-116">Create the capture job and cleanup job on the new principal database (the former mirror database).</span></span> <span data-ttu-id="3be04-117">ジョブを作成するには、 [sp_cdc_add_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql) ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="3be04-117">To create the jobs, use the [sp_cdc_add_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql) stored procedure.</span></span>  
  
 <span data-ttu-id="3be04-118">クリーンアップまたはキャプチャ ジョブの現在の構成を表示するには、新しいプリンシパル サーバー インスタンスで [sys.sp_cdc_help_jobs](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql) ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="3be04-118">To view the current configuration of a cleanup or capture job, use the [sys.sp_cdc_help_jobs](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql) stored procedure on the new principal server instance.</span></span> <span data-ttu-id="3be04-119">特定のデータベースに対し、キャプチャ ジョブの名前は cdc.*database_name*_capture に、クリーンアップ ジョブの名前は cdc.*database_name*_cleanup になります ( *database_name* はデータベースの名前)。</span><span class="sxs-lookup"><span data-stu-id="3be04-119">For a given database, the capture job is named cdc.*database_name*_capture, and the cleanup job is named cdc.*database_name*_cleanup, where *database_name* is the name of the database.</span></span>  
  
 <span data-ttu-id="3be04-120">ジョブの構成を変更するには、 [sys.sp_cdc_change_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql) ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="3be04-120">To change the configuration of a job, use the [sys.sp_cdc_change_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql) stored procedure.</span></span>  
  
 <span data-ttu-id="3be04-121">データベース ミラーリングの詳細については、「[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3be04-121">For information about database mirroring, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
##  <a name="transactional-replication"></a><a name="TransReplication"></a><span data-ttu-id="3be04-122">トランザクションレプリケーション</span><span class="sxs-lookup"><span data-stu-id="3be04-122">Transactional Replication</span></span>  
 <span data-ttu-id="3be04-123">変更データ キャプチャとトランザクション レプリケーションは、同じデータベースで共存できます。ただし、両方の機能が有効になっている場合、変更テーブルが異なる方法で作成されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-123">Change data capture and transactional replication can coexist in the same database, but population of the change tables is handled differently when both features are enabled.</span></span> <span data-ttu-id="3be04-124">変更データ キャプチャとトランザクション レプリケーションでは、トランザクション ログから変更を読み取る際に、常に同じプロシージャ ( [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql)) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-124">Change data capture and transactional replication always use the same procedure, [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql), to read changes from the transaction log.</span></span> <span data-ttu-id="3be04-125">変更データキャプチャがそれ自体で有効になっている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントジョブはを呼び出し `sp_replcmds` ます。</span><span class="sxs-lookup"><span data-stu-id="3be04-125">When change data capture is enabled on its own, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job calls `sp_replcmds`.</span></span> <span data-ttu-id="3be04-126">同じデータベースで両方の機能が有効になっている場合、ログリーダーエージェントはを呼び出し `sp_replcmds` ます。</span><span class="sxs-lookup"><span data-stu-id="3be04-126">When both features are enabled on the same database, the Log Reader Agent calls `sp_replcmds`.</span></span> <span data-ttu-id="3be04-127">このエージェントは、変更テーブルとディストリビューション データベース テーブルの両方を作成します。</span><span class="sxs-lookup"><span data-stu-id="3be04-127">This agent populates both the change tables and the distribution database tables.</span></span> <span data-ttu-id="3be04-128">詳細については、「 [Replication Log Reader Agent](../replication/agents/replication-log-reader-agent.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3be04-128">For more information, see [Replication Log Reader Agent](../replication/agents/replication-log-reader-agent.md).</span></span>  
  
 <span data-ttu-id="3be04-129">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで変更データ キャプチャが有効になっており、2 つのテーブルでキャプチャが有効になっているシナリオについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="3be04-129">Consider a scenario in which change data capture is enabled on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and two tables are enabled for capture.</span></span> <span data-ttu-id="3be04-130">変更テーブルを作成するために、キャプチャ ジョブによって `sp_replcmds` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-130">To populate the change tables, the capture job calls `sp_replcmds`.</span></span> <span data-ttu-id="3be04-131">データベースでトランザクション レプリケーションが有効になり、パブリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-131">The database is enabled for transactional replication, and a publication is created.</span></span> <span data-ttu-id="3be04-132">次に、ログ リーダー エージェントがデータベースに対して作成され、キャプチャ ジョブが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-132">Now, the Log Reader Agent is created for the database and the capture job is deleted.</span></span> <span data-ttu-id="3be04-133">ログ リーダー エージェントは、変更テーブルにコミットされた最後のログ シーケンス番号からログのスキャンを続行します。</span><span class="sxs-lookup"><span data-stu-id="3be04-133">The Log Reader Agent continues to scan the log from the last log sequence number that was committed to the change table.</span></span> <span data-ttu-id="3be04-134">これにより、変更テーブル内のデータの一貫性が確保されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-134">This ensures data consistency in the change tables.</span></span> <span data-ttu-id="3be04-135">このデータベースでトランザクション レプリケーションが無効になっている場合、ログ リーダー エージェントが削除され、キャプチャ ジョブが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-135">If transactional replication is disabled in this database, the Log Reader Agent is removed and the capture job is re-created.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3be04-136">変更データ キャプチャとトランザクション レプリケーションの両方でログ リーダー エージェントを使用している場合、レプリケートされた変更が最初にディストリビューション データベースに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="3be04-136">When the Log Reader Agent is used for both change data capture and transactional replication, replicated changes are first written to the distribution database.</span></span> <span data-ttu-id="3be04-137">次に、キャプチャされた変更が変更テーブルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="3be04-137">Then, captured changes are written to the change tables.</span></span> <span data-ttu-id="3be04-138">両方の操作は同時にコミットされます。</span><span class="sxs-lookup"><span data-stu-id="3be04-138">Both operations are committed together.</span></span> <span data-ttu-id="3be04-139">ディストリビューション データベースへの書き込みの際に遅延が生じた場合、変更テーブルに変更が表示される前に、それに対応する遅延が発生します。</span><span class="sxs-lookup"><span data-stu-id="3be04-139">If there is any latency in writing to the distribution database, there will be a corresponding latency before changes appear in the change tables.</span></span>  
  
 <span data-ttu-id="3be04-140">変更データ キャプチャが有効な場合、トランザクション レプリケーションの **proc exec** オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="3be04-140">The **proc exec** option of transactional replication is not available when change data capture is enabled.</span></span>  
  
##  <a name="restoring-or-attaching-a-database-enabled-for-change-data-capture"></a><a name="RestoreOrAttach"></a><span data-ttu-id="3be04-141">変更データキャプチャが有効になっているデータベースの復元またはアタッチ</span><span class="sxs-lookup"><span data-stu-id="3be04-141">Restoring or Attaching a Database Enabled for Change Data Capture</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3be04-142">では、データベースが復元またはアタッチされた後に変更データ キャプチャを有効のままにするかどうかを、次のロジックに従って判断します。</span><span class="sxs-lookup"><span data-stu-id="3be04-142">uses the following logic to determine if change data capture remains enabled after a database is restored or attached:</span></span>  
  
-   <span data-ttu-id="3be04-143">データベースを同じサーバーに同じデータベース名で復元した場合、変更データ キャプチャは有効のままです。</span><span class="sxs-lookup"><span data-stu-id="3be04-143">If a database is restored to the same server with the same database name, change data capture remains enabled.</span></span>  
  
-   <span data-ttu-id="3be04-144">データベースを別のサーバーに復元した場合、既定では変更データ キャプチャが無効になり、関連するメタデータがすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-144">If a database is restored to another server, by default change data capture is disabled and all related metadata is deleted.</span></span>  
  
     <span data-ttu-id="3be04-145">変更データ キャプチャを保持するには、データベースを復元する際に `KEEP_CDC` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3be04-145">To retain change data capture, use the `KEEP_CDC` option when restoring the database.</span></span> <span data-ttu-id="3be04-146">このオプションの詳細については、「 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3be04-146">For more information about this option, see [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
-   <span data-ttu-id="3be04-147">データベースをデタッチしてから、同じサーバーまたは別のサーバーにアタッチした場合、変更データ キャプチャは有効のままです。</span><span class="sxs-lookup"><span data-stu-id="3be04-147">If a database is detached and attached to the same server or another server, change data capture remains enabled.</span></span>  
  
-   <span data-ttu-id="3be04-148">Enterprise 以外のエディションに対してオプションを使用してデータベースがアタッチまたは復元された場合 `KEEP_CDC` 、この操作はブロックされます。これは、変更データキャプチャが enterprise を必要とするためです [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3be04-148">If a database is attached or restored with the `KEEP_CDC` option to any edition other than Enterprise, the operation is blocked because change data capture requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="3be04-149">エラー メッセージ 934 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3be04-149">Error message 934 is displayed:</span></span>  
  
     `SQL Server cannot load database '%.*ls' because change data capture is enabled. The currently installed edition of SQL Server does not support change data capture. Either disable change data capture in the database by using a supported edition of SQL Server, or upgrade the instance to one that supports change data capture.`  
  
 <span data-ttu-id="3be04-150">[sys.sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) を使用すると、復元またはアタッチされたデータベースから変更データ キャプチャを削除できます。</span><span class="sxs-lookup"><span data-stu-id="3be04-150">You can use [sys.sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) to remove change data capture from a restored or attached database.</span></span>  
  
## <a name="change-data-capture-and-alwayson"></a><span data-ttu-id="3be04-151">変更データ キャプチャと AlwaysON</span><span class="sxs-lookup"><span data-stu-id="3be04-151">Change Data Capture and AlwaysON</span></span>  
 <span data-ttu-id="3be04-152">AlwaysON を使用する場合、セカンダリ レプリケーションに対して変更の列挙を行うことにより、プライマリへのディスク負荷を減らす必要があります。</span><span class="sxs-lookup"><span data-stu-id="3be04-152">When you use AlwaysON, change enumeration should be done on the Secondary replication to reduce the disk load on the primary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be04-153">参照</span><span class="sxs-lookup"><span data-stu-id="3be04-153">See Also</span></span>  
 [<span data-ttu-id="3be04-154">変更データ キャプチャの管理と監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3be04-154">Administer and Monitor Change Data Capture &#40;SQL Server&#41;</span></span>](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  