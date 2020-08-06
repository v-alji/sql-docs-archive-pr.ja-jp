---
title: ミラーリングのためのミラー データベースの準備 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], preparing for mirroring
- logins [SQL Server], database mirroring
- mirror database [SQL Server]
ms.assetid: 8676f9d8-c451-419b-b934-786997d46c2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf46b4f6fd8e7af55e1930ef6063c4754673fa79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716785"
---
# <a name="prepare-a-mirror-database-for-mirroring-sql-server"></a><span data-ttu-id="14eef-102">ミラーリングのためのミラー データベースの準備 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="14eef-102">Prepare a Mirror Database for Mirroring (SQL Server)</span></span>
  <span data-ttu-id="14eef-103">データベース ミラーリング セッションを開始する前に、データベース所有者またはシステム管理者は、ミラー データベースを作成し、ミラーリング用に準備しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-103">Before a database mirroring session can start, the database owner or system administrator must make sure that the mirror database has been created and is ready for mirroring.</span></span> <span data-ttu-id="14eef-104">新しいミラー データベースを作成するには、少なくとも、プリンシパル データベースの完全バックアップとそれ以降のログ バックアップを作成し、その両方をミラー サーバーのインスタンスに (WITH NORECOVERY を使用して) 復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-104">Creating a new mirror database minimally requires taking a full backup of the principal database and a subsequent log backup and restoring them both onto the mirror server instance, using WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="14eef-105">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でミラー データベースを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14eef-105">This topic describes how to prepare a mirror database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="14eef-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="14eef-106">Before You Begin</span></span>  
  
###  <a name="requirements"></a><a name="Requirements"></a> <span data-ttu-id="14eef-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="14eef-107">Requirements</span></span>  
  
-   <span data-ttu-id="14eef-108">プリンシパル サーバー インスタンスとミラー サーバー インスタンスは、同じバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-108">The principal and mirror server instances must be running on the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="14eef-109">ミラー サーバーで SQL Server の新しいバージョンを実行することはできますが、この構成は慎重に計画されたアップグレード プロセスにおいてのみ推奨されます。</span><span class="sxs-lookup"><span data-stu-id="14eef-109">While it is possible for the mirror server to have a higher version of SQL Server, this configuration is only recommended during a carefully planned upgrade process.</span></span> <span data-ttu-id="14eef-110">そのような構成では、自動フェールオーバーが発生したときに SQL Server の古いバージョンにデータを移動できず、データの移動が自動的に保留される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-110">In such a configuration, you run the risk of an automatic failover, in which data movement is automatically suspended because data cannot move to a lower version of SQL Server.</span></span> <span data-ttu-id="14eef-111">詳しくは、「 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="14eef-111">For more information, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).</span></span>  
  
-   <span data-ttu-id="14eef-112">プリンシパル サーバー インスタンスとミラー サーバー インスタンスは、同じエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-112">The principal and mirror server instances must be running on the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="14eef-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でのデータベース ミラーリングのサポートについては、「[SQL Server 2014 の各エディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14eef-113">For information about support for database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="14eef-114">このデータベースは、完全復旧モデルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-114">The database must use the full recovery model.</span></span>  
  
     <span data-ttu-id="14eef-115">詳細については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)」または「[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)」と「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14eef-115">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) or [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) and [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="14eef-116">ミラー データベースの名前は、プリンシパル データベースと同じ名前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-116">The name of the mirror database must be the same as the name of the principal database.</span></span>  
  
-   <span data-ttu-id="14eef-117">ミラーリングが機能するには、ミラー データベースは RESTORING 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-117">The mirror database must be in the RESTORING state for mirroring to work.</span></span> <span data-ttu-id="14eef-118">ミラー データベースを準備する際には、すべての復元操作で RESTORE WITH NORECOVERY を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-118">When preparing a mirror database, you must use RESTORE WITH NORECOVERY for every restore operation.</span></span> <span data-ttu-id="14eef-119">少なくとも、WITH NORECOVERY を指定して、プリンシパル データベースの完全バックアップと、以降のすべてのログ バックアップを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-119">Minimally, you will need to restore WITH NORECOVERY a full backup of the principal database, followed by all subsequent log backups.</span></span>  
  
-   <span data-ttu-id="14eef-120">ミラー データベースを作成するシステムのディスク ドライブに、ミラー データベースを保持するのに十分な空き領域を確保する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-120">The system where you plan to create the mirror database must possesses a disk drive with sufficient space to hold the mirror database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="14eef-121">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="14eef-121">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="14eef-122">**master**、 **msdb**、 **temp**、および **model** の各システム データベースはミラー化できません。</span><span class="sxs-lookup"><span data-stu-id="14eef-122">You cannot mirror the **master**, **msdb**, **temp**, or **model** system databases.</span></span>  
  
-   <span data-ttu-id="14eef-123">[AlwaysOn 可用性グループ (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md)に属しているデータベースをミラー化することはできません。</span><span class="sxs-lookup"><span data-stu-id="14eef-123">You cannot mirror a database that belongs to an [AlwaysOn Availability Groups (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="14eef-124">推奨事項</span><span class="sxs-lookup"><span data-stu-id="14eef-124">Recommendations</span></span>  
  
-   <span data-ttu-id="14eef-125">プリンシパル データベースの最新の完全データベース バックアップまたは差分データベース バックアップを使用します。</span><span class="sxs-lookup"><span data-stu-id="14eef-125">Use a very recent full database backup or a recent differential database backup of the principal database.</span></span>  
  
-   <span data-ttu-id="14eef-126">ログ バックアップ ジョブをプリンシパル データベースで非常に頻繁に実行するようにスケジュールすると、ミラーリングが開始されるまでバックアップ ジョブを無効にする必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-126">If a log backup job is scheduled to run very frequently on the principal database, you might have to disable the backup job until mirroring has started.</span></span>  
  
-   <span data-ttu-id="14eef-127">可能であれば、ミラー データベースのパス (ドライブ文字を含む) を、プリンシパル データベースと同一のパスにします。</span><span class="sxs-lookup"><span data-stu-id="14eef-127">If possible, the path (including the drive letter) of the mirror database should be identical to the path of the principal database.</span></span>  
  
     <span data-ttu-id="14eef-128">ファイルのパスが異なる場合、たとえば、プリンシパル データベースが "F:" ドライブに存在する一方で、ミラー システムに "F:" ドライブがない場合には、RESTORE ステートメントに MOVE オプションを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-128">If the file paths must differ, for example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive, you must include the MOVE option in the RESTORE STATEMENT.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="14eef-129">ミラーリング セッション中に、セッションに影響を与えずにファイルを追加するには、追加するファイルのパスが両方のサーバーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-129">Adding a file during a mirroring session without impacting the session requires that the path of the file exists on both servers.</span></span> <span data-ttu-id="14eef-130">したがって、ミラー データベースの作成時にデータベース ファイルを移動し、その後でミラー データベースにファイルを追加しようとした場合、ファイルの追加操作が失敗し、ミラーリングが中断されることがあります。</span><span class="sxs-lookup"><span data-stu-id="14eef-130">Therefore, if you move the database files when creating the mirror database, a later add-file operation might fail on the mirror database and cause mirroring to be suspended.</span></span> <span data-ttu-id="14eef-131">ファイル作成操作の失敗に対処する方法については、「[データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14eef-131">For information about dealing with a failed create-file operation, see [Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md).</span></span>  
  
-   <span data-ttu-id="14eef-132">プリンシパル データベースにフルテキスト カタログが含まれている場合は、「[データベース ミラーリングとフルテキスト カタログ &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md)」を参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="14eef-132">If the principal database has any full-text catalogs, we recommend that you see [Database Mirroring and Full-Text Catalogs &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md).</span></span>  
  
-   <span data-ttu-id="14eef-133">運用データベースを使用する場合は、必ず別のデバイスにバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="14eef-133">For a production database, always back up to a separate device.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="14eef-134">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="14eef-134">Security</span></span>  
 <span data-ttu-id="14eef-135">データベースがバックアップされている場合、TRUSTWORTHY は OFF に設定されます。</span><span class="sxs-lookup"><span data-stu-id="14eef-135">TRUSTWORTHY is set to OFF when a database is backed up.</span></span> <span data-ttu-id="14eef-136">したがって、新しいミラー データベースでは TRUSTWORTHY は常に OFF です。</span><span class="sxs-lookup"><span data-stu-id="14eef-136">Therefore, TRUSTWORTHY is always OFF on a new mirror database.</span></span> <span data-ttu-id="14eef-137">フェールオーバー後にデータベースを信頼可能にする必要がある場合は、追加の設定作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="14eef-137">If the database needs to be trustworthy after a failover, additional setup steps are necessary.</span></span> <span data-ttu-id="14eef-138">詳細については、「 [TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)でミラー データベースを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14eef-138">For more information, see [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).</span></span>  
  
 <span data-ttu-id="14eef-139">データベース マスター キーの自動暗号化解除を有効にする方法については、「 [暗号化されたミラー データベースの設定](set-up-an-encrypted-mirror-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14eef-139">For information about enabling automatic decryption of the database master key of a mirror database, see [Set Up an Encrypted Mirror Database](set-up-an-encrypted-mirror-database.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="14eef-140">Permissions</span><span class="sxs-lookup"><span data-stu-id="14eef-140">Permissions</span></span>  
 <span data-ttu-id="14eef-141">データベース所有者またはシステム管理者。</span><span class="sxs-lookup"><span data-stu-id="14eef-141">Database owner or system administrator.</span></span>  
  
##  <a name="to-prepare-an-existing-mirror-database-to-restart-mirroring"></a><a name="PrepareToRestartMirroring"></a> <span data-ttu-id="14eef-142">ミラーリングを再開するために既存のミラー データベースを準備するには</span><span class="sxs-lookup"><span data-stu-id="14eef-142">To Prepare an Existing Mirror Database to Restart Mirroring</span></span>  
 <span data-ttu-id="14eef-143">ミラーリングを削除してもミラー データベースが RECOVERING 状態のままである場合、ミラーリングを再開することができます。</span><span class="sxs-lookup"><span data-stu-id="14eef-143">If mirroring has been removed and the mirror database is still in the RECOVERING state, you can restart mirroring.</span></span>  
  
1.  <span data-ttu-id="14eef-144">プリンシパル データベースで 1 つ以上のログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="14eef-144">Take at least one log backup on the principal database.</span></span> <span data-ttu-id="14eef-145">詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14eef-145">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="14eef-146">ミラー データベースで、RESTORE WITH NORECOVERY を使用して、ミラーリングの削除後にプリンシパル データベースで作成されたすべてのログ バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="14eef-146">On the mirror database, use RESTORE WITH NORECOVERY to restore all log backups taken on the principal database since mirroring was removed.</span></span> <span data-ttu-id="14eef-147">詳細については、「 [トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)でミラー データベースを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14eef-147">For more information, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
##  <a name="to-prepare-a-new-mirror-database"></a><a name="CombinedProcedure"></a> <span data-ttu-id="14eef-148">新しいミラー データベースを準備するには</span><span class="sxs-lookup"><span data-stu-id="14eef-148">To Prepare a New Mirror Database</span></span>  
 <span data-ttu-id="14eef-149">**ミラー データベースを準備するには**</span><span class="sxs-lookup"><span data-stu-id="14eef-149">**To prepare a mirror database**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14eef-150">この手順の [!INCLUDE[tsql](../../includes/tsql-md.md)] の例については、このセクションの後半の「 [例 (Transact-SQL)](#TsqlExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14eef-150">For a [!INCLUDE[tsql](../../includes/tsql-md.md)] example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="14eef-151">プリンシパル サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="14eef-151">Connect to principal server instance.</span></span>  
  
2.  <span data-ttu-id="14eef-152">プリンシパル データベースの完全バックアップまたは差分バックアップのいずれかを作成します。</span><span class="sxs-lookup"><span data-stu-id="14eef-152">Create either a full database backup or a differential database backup of the principal database.</span></span>  
  
    -   [<span data-ttu-id="14eef-153">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-153">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
    -   <span data-ttu-id="14eef-154">[データベースの差分バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="14eef-154">[Create a Differential Database Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="14eef-155">通常、プリンシパル データベースで 1 つ以上のログ バックアップを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-155">Typically, you need to take at least one log backup on the principal database.</span></span> <span data-ttu-id="14eef-156">ただし、データベースを作成したばかりでログ バックアップがまだ作成されていない場合や、復旧モデルを SIMPLE から FULL に変更したばかりの場合など、ログ バックアップが不要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="14eef-156">However, a log backup might be unnecessary, if the database has just been created and no log backup has been taken yet, or if the recovery model has just been changed from SIMPLE to FULL.</span></span>  
  
    -   [<span data-ttu-id="14eef-157">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-157">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
4.  <span data-ttu-id="14eef-158">両方のシステムからアクセスできるネットワーク ドライブにバックアップがある場合を除いて、データベース バックアップとログ バックアップは、ミラー サーバー インスタンスをホストするシステムにコピーします。</span><span class="sxs-lookup"><span data-stu-id="14eef-158">Unless the backups are on a network drive that is accessible from both systems, copy the database and log backups to the system that will host the mirror server instance.</span></span>  
  
5.  <span data-ttu-id="14eef-159">ミラー サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="14eef-159">Connect to mirror server instance.</span></span>  
  
6.  <span data-ttu-id="14eef-160">RESTORE WITH NORECOVERY を使用する場合、ミラー サーバー インスタンスにデータベースの完全バックアップと、必要に応じて、データベースの最新の差分バックアップを復元することで、ミラー データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="14eef-160">Using RESTORE WITH NORECOVERY, create the mirror database by restoring the full database backup and, optionally, the most recent differential database backup, onto the mirror server instance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="14eef-161">データベースのファイル グループをファイル グループごとに復元する場合は、必ずデータベース全体を復元してください。</span><span class="sxs-lookup"><span data-stu-id="14eef-161">If you restore the database filegroup by filegroup, be sure to restore the whole database.</span></span>  
  
    -   [<span data-ttu-id="14eef-162">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-162">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
    -   <span data-ttu-id="14eef-163">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 」と「 [RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)でミラー データベースを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14eef-163">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
7.  <span data-ttu-id="14eef-164">RESTORE WITH NORECOVERY を使用して、未処理のログ バックアップをミラー データベースに適用します。</span><span class="sxs-lookup"><span data-stu-id="14eef-164">Using RESTORE WITH NORECOVERY, apply any outstanding log backup or backups to the mirror database.</span></span>  
  
    -   [<span data-ttu-id="14eef-165">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-165">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="14eef-166">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="14eef-166">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="14eef-167">データベース ミラーリング セッションを開始する前に、ミラー データベースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-167">Before you can start a database mirroring session, you must create the mirror database.</span></span> <span data-ttu-id="14eef-168">ミラー データベースは、ミラーリング セッションを開始する直前に作成してください。</span><span class="sxs-lookup"><span data-stu-id="14eef-168">You should do this just before starting the mirroring session.</span></span>  
  
 <span data-ttu-id="14eef-169">この例では、既定で単純復旧モデルを使用する [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="14eef-169">This example uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database, which uses the simple recovery model by default.</span></span>  
  
1.  <span data-ttu-id="14eef-170">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースでデータベース ミラーリングを使用するには、完全復旧モデルが使用されるように変更します。</span><span class="sxs-lookup"><span data-stu-id="14eef-170">To use database mirroring with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, modify it to use the full recovery model:</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  <span data-ttu-id="14eef-171">データベースの復旧モデルを SIMPLE から FULL へ変更した後は、完全バックアップを作成します。作成した完全バックアップはミラー データベースの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="14eef-171">After modifying the recovery model of the database from SIMPLE to FULL, create a full backup, which can be used to create the mirror database.</span></span> <span data-ttu-id="14eef-172">復旧モデルを変更した直後なので、新しいメディア セットを作成するには WITH FORMAT オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="14eef-172">Because the recovery model has just been changed, the WITH FORMAT option is specified to create a new media set.</span></span> <span data-ttu-id="14eef-173">これにより、完全復旧モデルのバックアップを、単純復旧モデルで作成された以前のバックアップと分離できます。</span><span class="sxs-lookup"><span data-stu-id="14eef-173">This is useful to separate the backups under the full recovery model from any previous backups made under the simple recovery model.</span></span> <span data-ttu-id="14eef-174">この例では、バックアップ ファイル (`C:\AdventureWorks.bak`) をデータベースと同じドライブに作成します。</span><span class="sxs-lookup"><span data-stu-id="14eef-174">For the purpose of this example, the backup file (`C:\AdventureWorks.bak`) is created on the same drive as the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="14eef-175">運用データベースを使用する場合は、必ず別のデバイスにバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="14eef-175">For a production database, you should always back up to a separate device.</span></span>  
  
     <span data-ttu-id="14eef-176">プリンシパル サーバー インスタンス ( `PARTNERHOST1`) で、次のようにプリンシパル データベースの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="14eef-176">On the principal server instance (on `PARTNERHOST1`), create a full backup of the principal database as follows:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  <span data-ttu-id="14eef-177">完全バックアップをミラー サーバーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="14eef-177">Copy the full backup to the mirror server.</span></span>  
  
4.  <span data-ttu-id="14eef-178">RESTORE WITH NORECOVERY を使用して、ミラー サーバー インスタンスに完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="14eef-178">Using RESTORE WITH NORECOVERY, restore the full backup onto the mirror server instance.</span></span> <span data-ttu-id="14eef-179">復元コマンドは、プリンシパル データベースとミラー データベースのパスが同じかどうかによって変わります。</span><span class="sxs-lookup"><span data-stu-id="14eef-179">The restore command depends on whether the paths of principal and mirror databases are identical.</span></span>  
  
    -   <span data-ttu-id="14eef-180">**パスが同じ場合は、次のようにします。**</span><span class="sxs-lookup"><span data-stu-id="14eef-180">**If the paths are identical:**</span></span>  
  
         <span data-ttu-id="14eef-181">ミラー サーバー インスタンス ( `PARTNERHOST5`) で、次のように完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="14eef-181">On the mirror server instance (on `PARTNERHOST5`), restore the full backup as follows:</span></span>  
  
        ```  
        RESTORE DATABASE AdventureWorks   
            FROM DISK = 'C:\AdventureWorks.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   <span data-ttu-id="14eef-182">**パスが異なる場合は、次のようにします。**</span><span class="sxs-lookup"><span data-stu-id="14eef-182">**If the paths differ:**</span></span>  
  
         <span data-ttu-id="14eef-183">ミラー データベースのパスがプリンシパル データベースのパスと異なる (たとえば、ドライブ文字が異なる) 場合、ミラー データベースを作成するには、復元操作に MOVE 句が必要です。</span><span class="sxs-lookup"><span data-stu-id="14eef-183">If the path of the mirror database differs from the path of the principal database (for instance, their drive letters differ), creating the mirror database requires that the restore operation include a MOVE clause.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="14eef-184">プリンシパル データベースとミラー データベースのパス名が異なる場合は、ファイルを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="14eef-184">If the path names of the principal and mirror databases differ, you cannot add a file.</span></span> <span data-ttu-id="14eef-185">これは、ミラーリング サーバー インスタンスでファイル追加操作のログが受信されると、プリンシパル データベースで使用される場所に新しいファイルの追加が試行されるためです。</span><span class="sxs-lookup"><span data-stu-id="14eef-185">This is because on receiving the log for the add file operation, the mirror server instance attempts to place the new file in the location used by the principal database.</span></span>  
  
         <span data-ttu-id="14eef-186">たとえば次のコマンドは、C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\ にあるプリンシパル データベースのバックアップを、D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`という別の場所 (ミラー データベースが配置される場所) に復元します。</span><span class="sxs-lookup"><span data-stu-id="14eef-186">For example, the following command restores a backup of a principal database residing in C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\ to a different location, D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`, where the mirror database is to reside.</span></span>  
  
        ```  
        RESTORE DATABASE AdventureWorks  
           FROM DISK='C:\AdventureWorks.bak'  
           WITH NORECOVERY,   
              MOVE 'AdventureWorks_Data' TO   
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Data.mdf',   
              MOVE 'AdventureWorks_Log' TO  
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Log.ldf';  
        GO  
        ```  
  
5.  <span data-ttu-id="14eef-187">完全バックアップを作成した後、プリンシパル データベースでログ バックアップを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-187">After you create the full backup, you must create a log backup on the principal database.</span></span> <span data-ttu-id="14eef-188">たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、前回の完全バックアップで使用したものと同じファイルにログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="14eef-188">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement backs up the log to the same file used by the preceding full backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="14eef-189">ミラーリングを開始する前に、必要なログ バックアップ (および、それ以降のログ バックアップ) を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14eef-189">Before you can start mirroring, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="14eef-190">たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、最初のログを `C:\AdventureWorks.bak`から復元します。</span><span class="sxs-lookup"><span data-stu-id="14eef-190">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores the first log from `C:\AdventureWorks.bak`:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="14eef-191">ミラーリングを開始する前に追加のログ バックアップが作成された場合は、それらのログ バックアップもすべて復元する必要があります。すべてのログ バックアップを順番に、WITH NORECOVERY を使用して、ミラー サーバーに復元します。</span><span class="sxs-lookup"><span data-stu-id="14eef-191">If any additional log backups occur before you start mirroring, you must also restore all of those log backups, in sequence, to the mirror server using WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="14eef-192">たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、2 つの追加のログを `C:\AdventureWorks.bak`から復元します。</span><span class="sxs-lookup"><span data-stu-id="14eef-192">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores two additional logs from `C:\AdventureWorks.bak`:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
 <span data-ttu-id="14eef-193">データベース ミラーリングの設定、セキュリティの設定、ミラー データベースの準備、パートナーの設定、およびミラーリング監視サーバーの追加をすべて含む例については、「 [データベース ミラーリングの設定 &#40;SQL Server&#41;](database-mirroring-sql-server.md)でミラー データベースを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14eef-193">For a complete example of setting up database mirroring, showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-preparing-a-mirror-database"></a><a name="FollowUp"></a><span data-ttu-id="14eef-194">補足情報: ミラー データベースを準備した後</span><span class="sxs-lookup"><span data-stu-id="14eef-194">Follow Up: After Preparing a Mirror Database</span></span>  
  
1.  <span data-ttu-id="14eef-195">最新の RESTORE LOG 操作の後、ログ バックアップを採取している場合は、ミラーリングを開始する前に、採取したすべてのログ バックアップを手動で適用する必要があります (WITH NORECOVERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="14eef-195">If any additional log backups have been taken since your most recent RESTORE LOG operation, you must manually apply every additional log backup, using RESTORE WITH NORECOVERY.</span></span>  
  
2.  <span data-ttu-id="14eef-196">ミラーリング セッションを再開します。</span><span class="sxs-lookup"><span data-stu-id="14eef-196">Start the mirroring session.</span></span> <span data-ttu-id="14eef-197">詳細については、「 [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) を使用して、 [Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)でミラー データベースを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14eef-197">For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) or [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md).</span></span>  
  
3.  <span data-ttu-id="14eef-198">プリンシパル データベースのバックアップ ジョブを無効にする場合は、ジョブを再度有効にします。</span><span class="sxs-lookup"><span data-stu-id="14eef-198">If you disabled the backup job on the principal database, reenable the job.</span></span>  
  
4.  <span data-ttu-id="14eef-199">フェールオーバー後にデータベースを信頼可能にする必要がある場合は、ミラーリングを開始した後で追加の設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="14eef-199">If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.</span></span> <span data-ttu-id="14eef-200">詳細については、「 [TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)でミラー データベースを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14eef-200">For more information, see [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="14eef-201">関連タスク</span><span class="sxs-lookup"><span data-stu-id="14eef-201">Related Tasks</span></span>  
  
-   [<span data-ttu-id="14eef-202">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-202">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="14eef-203">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-203">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="14eef-204">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-204">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="14eef-205">Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-205">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="14eef-206">暗号化されたミラー データベースの設定</span><span class="sxs-lookup"><span data-stu-id="14eef-206">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
-   [<span data-ttu-id="14eef-207">TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-207">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="14eef-208">参照</span><span class="sxs-lookup"><span data-stu-id="14eef-208">See Also</span></span>  
 <span data-ttu-id="14eef-209">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14eef-209">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="14eef-210">[データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="14eef-210">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="14eef-211">[データベース ミラーリングの設定 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14eef-211">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="14eef-212">[フルテキスト カタログとフルテキスト インデックスのバックアップおよび復元](../../relational-databases/indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="14eef-212">[Back Up and Restore Full-Text Catalogs and Indexes](../../relational-databases/indexes/indexes.md) </span></span>  
 <span data-ttu-id="14eef-213">[データベース ミラーリングとフルテキスト カタログ &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14eef-213">[Database Mirroring and Full-Text Catalogs &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md) </span></span>  
 <span data-ttu-id="14eef-214">[データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14eef-214">[Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span></span>  
 <span data-ttu-id="14eef-215">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="14eef-215">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="14eef-216">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="14eef-216">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="14eef-217">RESTORE の引数 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="14eef-217">RESTORE Arguments &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-arguments-transact-sql)  
  
  
