---
title: 可用性グループに対するセカンダリ データベースの手動準備 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.configsecondarydbs.f1
- sql12.swb.availabilitygroup.preparedbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 9f2feb3c-ea9b-4992-8202-2aeed4f9a6dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3da3f7332bdabce65785b2844157dd4639389254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634646"
---
# <a name="manually-prepare-a-secondary-database-for-an-availability-group-sql-server"></a><span data-ttu-id="e5552-102">可用性グループに対するセカンダリ データベースの手動準備 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e5552-102">Manually Prepare a Secondary Database for an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="e5552-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、または PowerShell を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]で AlwaysOn 可用性グループのセカンダリ データベースを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5552-103">This topic describes how to prepare a secondary database for an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="e5552-104">セカンダリ データベースを準備するには、2 つの手順を実行する必要があります。まず、RESTORE WITH NORECOVERY を使用して、プライマリ データベースの最新のバックアップとそれ以降のログ バックアップを、セカンダリ レプリカをホストする各サーバー インスタンスに復元します。次に、復元したデータベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="e5552-104">Preparing a secondary database requires two steps: (1) restoring a recent database backup of the primary database and subsequent log backups onto each server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY, and (2) joining the restored database to the availability group.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="e5552-105">既存のログ配布構成がある場合は、ログ配布プライマリ データベースとその 1 つ以上のセカンダリ データベースを、AlwaysOn プライマリ データベースと 1 つ以上の AlwaysOn セカンダリ データベースに変換できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-105">If you have an existing log shipping configuration, you might be able to convert the log shipping primary database along with one or more of its secondary databases to an AlwaysOn primary database and one or more AlwaysOn secondary databases.</span></span> <span data-ttu-id="e5552-106">詳細については、「[ログ配布から AlwaysOn 可用性グループ &#40;SQL Server&#41;への移行の前提条件](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-106">For more information, see [Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="e5552-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e5552-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e5552-108">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="e5552-108">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="e5552-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="e5552-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="e5552-110">Security</span><span class="sxs-lookup"><span data-stu-id="e5552-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e5552-111">**以下を使用してセカンダリ データベースを準備するには:**</span><span class="sxs-lookup"><span data-stu-id="e5552-111">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="e5552-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e5552-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e5552-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e5552-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="e5552-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5552-114">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="e5552-115">関連するバックアップおよび復元のタスク</span><span class="sxs-lookup"><span data-stu-id="e5552-115">Related Backup and Restore Tasks</span></span>](#RelatedTasks)  
  
-   <span data-ttu-id="e5552-116">**補足情報:** [セカンダリ データベースを準備した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="e5552-116">**Follow Up:** [After Preparing a Secondary Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e5552-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="e5552-117">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="e5552-118">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="e5552-118">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="e5552-119">データベースを配置するシステムのディスク ドライブに、セカンダリ データベース用に十分な空き領域があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e5552-119">Make sure that the system where you plan to place database possesses a disk drive with sufficient space for the secondary databases.</span></span>  
  
-   <span data-ttu-id="e5552-120">セカンダリ データベースの名前は、プライマリ データベースの名前と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-120">The name of the secondary database must be the same as the name of the primary database.</span></span>  
  
-   <span data-ttu-id="e5552-121">すべて復元操作に RESTORE WITH NORECOVERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5552-121">Use RESTORE WITH NORECOVERY for every restore operation.</span></span>  
  
-   <span data-ttu-id="e5552-122">セカンダリ データベースをプライマリ データベースとは異なるファイル パス (ドライブ文字を含む) に配置する必要がある場合は、復元コマンドでデータベース ファイルごとに WITH MOVE オプションも使用して、それらのファイルをセカンダリ データベースのパスに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-122">If the secondary database needs to reside on a different file path (including the drive letter) than the primary database, the restore command must also use the WITH MOVE option for each of the database files to specify them to the path of the secondary database.</span></span>  
  
-   <span data-ttu-id="e5552-123">データベースのファイル グループをファイル グループごとに復元する場合は、必ずデータベース全体を復元してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-123">If you restore the database filegroup by filegroup, be sure to restore the whole database.</span></span>  
  
-   <span data-ttu-id="e5552-124">データベースの復元後、復元された最後のデータ バックアップの後に作成されたすべてのログ バックアップを復元する必要があります (WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="e5552-124">After restoring the database, you must restore (WITH NORECOVERY) every log backup created since the last restored data backup.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e5552-125">推奨事項</span><span class="sxs-lookup"><span data-stu-id="e5552-125">Recommendations</span></span>  
  
-   <span data-ttu-id="e5552-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のスタンドアロン インスタンスでは、可能であれば、特定のセカンダリ データベースのファイル パス (ドライブ文字を含む) は、対応するプライマリ データベースのパスと一致させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5552-126">On stand-alone instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], we recommend that, if possible, the file path (including the drive letter) of a given secondary database be identical to the path of the corresponding primary database.</span></span> <span data-ttu-id="e5552-127">セカンダリ データベースの作成時にデータベース ファイルを移動し、その後でセカンダリ データベースにファイルを追加しようとした場合、ファイルの追加操作が失敗し、セカンダリ データベースが中断される可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="e5552-127">This is because if you move the database files when creating a secondary database, a later add-file operation might fail on the secondary database and cause the secondary database to be suspended.</span></span>  
  
-   <span data-ttu-id="e5552-128">セカンダリ データベースを準備する場合は、セカンダリ レプリカの初期化が完了するまでの間、可用性グループ内のデータベースでスケジュールされているログ パックアップを一時停止することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5552-128">Before preparing your secondary databases, we strongly recommend that you suspend scheduled log backups on the databases in the availability group until the initialization of secondary replicas has completed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e5552-129">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e5552-129">Security</span></span>  
 <span data-ttu-id="e5552-130">データベースがバックアップされると、 ["信頼できるデータベース" プロパティ](../../../relational-databases/security/trustworthy-database-property.md)が [オフ] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e5552-130">When a database is backed up, the [TRUSTWORTHY database property](../../../relational-databases/security/trustworthy-database-property.md) is set to OFF.</span></span> <span data-ttu-id="e5552-131">したがって、新たに復元されたデータベースでは TRUSTWORTHY は常に OFF です。</span><span class="sxs-lookup"><span data-stu-id="e5552-131">Therefore, TRUSTWORTHY is always OFF on a newly restored database.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e5552-132">Permissions</span><span class="sxs-lookup"><span data-stu-id="e5552-132">Permissions</span></span>  
 <span data-ttu-id="e5552-133">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="e5552-133">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span> <span data-ttu-id="e5552-134">詳細については、「 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-134">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
 <span data-ttu-id="e5552-135">復元するデータベースがサーバー インスタンスに存在しない場合、RESTORE ステートメントに CREATE DATABASE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e5552-135">When the database being restored does not exist on the server instance, the RESTORE statement requires CREATE DATABASE permissions.</span></span> <span data-ttu-id="e5552-136">詳細については、「 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)で復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="e5552-136">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e5552-137">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e5552-137">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5552-138"> バックアップ ファイルと復元ファイルのパスが、プライマリ レプリカをホストするサーバー インスタンスと、セカンダリ レプリカをホストする各インスタンスとで同じ場合は、 [新しい可用性グループ ウィザード](use-the-availability-group-wizard-sql-server-management-studio.md)、 [可用性グループへのレプリカ追加ウィザード](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)、または [可用性グループへのデータベース追加ウィザード](availability-group-add-database-to-group-wizard.md)を使用して、セカンダリ データベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e5552-138">If the backup and restore file paths are identical between the server instance that hosts the primary replica and every instance that hosts a secondary replica, you should be able create secondary databases by using [New Availability Group Wizard](use-the-availability-group-wizard-sql-server-management-studio.md), [Add Replica to Availability Group Wizard](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md), or [Add Database to Availability Group Wizard](availability-group-add-database-to-group-wizard.md).</span></span>  
  
 <span data-ttu-id="e5552-139">**セカンダリ データベースを準備するには**</span><span class="sxs-lookup"><span data-stu-id="e5552-139">**To prepare a secondary database**</span></span>  
  
1.  <span data-ttu-id="e5552-140">プライマリ データベースの最新のバックアップがない場合は、データベースの新しい完全バックアップか差分バックアップを作成してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-140">Unless you already have a recent database backup of the primary database, create a new full or differential database backup.</span></span> <span data-ttu-id="e5552-141">このバックアップとそれ以降のすべてのログ バックアップは、推奨されるネットワーク共有に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5552-141">As a best practice, place this backup and any subsequent log backups onto the recommended network share.</span></span>  
  
2.  <span data-ttu-id="e5552-142">プライマリ データベースの新しいログ バックアップを 1 つ以上作成します。</span><span class="sxs-lookup"><span data-stu-id="e5552-142">Create at least one new log backup of the primary database.</span></span>  
  
3.  <span data-ttu-id="e5552-143">セカンダリ レプリカをホストするサーバー インスタンスで、プライマリ データベースの完全バックアップ (および必要に応じて差分バックアップ)、それ以降のすべてのログ バックアップの順で復元します。</span><span class="sxs-lookup"><span data-stu-id="e5552-143">On the server instance that hosts the secondary replica, restore the full database backup of the primary database (and optionally a differential backup) followed by any subsequent log backups.</span></span>  
  
     <span data-ttu-id="e5552-144">**[RESTORE DATABASE オプション]** ページで、 **[データベースは操作不可状態のままで、コミットされていないトランザクションはロールバックしない。別のトランザクション ログは復元できます ] (RESTORE WITH NORECOVERY)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e5552-144">On the **RESTORE DATABASEOptions** page, select **Leave the database non-operational, and do not roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**.</span></span>  
  
     <span data-ttu-id="e5552-145">プライマリ データベースとセカンダリ データベースのファイル パスが異なる場合、たとえばプライマリ データベースはドライブ "F:" にあり、セカンダリ レプリカをホストするサーバー インスタンスに F: ドライブがない場合は、WITH 句に MOVE オプションを含めてください。</span><span class="sxs-lookup"><span data-stu-id="e5552-145">If the file paths of the primary database and the secondary database differ, for example, if the primary database is on drive 'F:' but the server instance that hosts the secondary replica lacks an F: drive, include the MOVE option in your WITH clause.</span></span>  
  
4.  <span data-ttu-id="e5552-146">セカンダリ データベースの構成を完了するには、セカンダリ データベースを可用性グループに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-146">To complete configuration of the secondary database, you need to join the secondary database to the availability group.</span></span> <span data-ttu-id="e5552-147">詳細については、「[可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-147">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5552-148"> これらのバックアップ操作および復元操作の実行方法については、このセクションの「 [関連するバックアップと復元のタスク](#RelatedTasks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-148">For information about how to perform these backup and restore operations, see [Related Backup and Restore Tasks](#RelatedTasks), later in this section.</span></span>  
  
###  <a name="related-backup-and-restore-tasks"></a><a name="RelatedTasks"></a><span data-ttu-id="e5552-149">関連するバックアップと復元のタスク</span><span class="sxs-lookup"><span data-stu-id="e5552-149">Related Backup and Restore Tasks</span></span>  
 <span data-ttu-id="e5552-150">**データベースのバックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="e5552-150">**To create a database backup**</span></span>  
  
-   [<span data-ttu-id="e5552-151">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e5552-151">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="e5552-152">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e5552-152">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="e5552-153">**ログ バックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="e5552-153">**To create a log backup**</span></span>  
  
-   [<span data-ttu-id="e5552-154">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e5552-154">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 <span data-ttu-id="e5552-155">**バックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="e5552-155">**To restore backups**</span></span>  
  
-   [<span data-ttu-id="e5552-156">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e5552-156">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="e5552-157">データベースの差分バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e5552-157">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="e5552-158">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e5552-158">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="e5552-159">データベースを新しい場所に復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e5552-159">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e5552-160">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e5552-160">Using Transact-SQL</span></span>  
 <span data-ttu-id="e5552-161">**セカンダリ データベースを準備するには**</span><span class="sxs-lookup"><span data-stu-id="e5552-161">**To prepare a secondary database**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5552-162">この手順の例については、このトピックの「 [例 (Transact-SQL)](#ExampleTsql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-162">For an example of this procedure, see [Example (Transact-SQL)](#ExampleTsql), earlier in this topic.</span></span>  
  
1.  <span data-ttu-id="e5552-163">プライマリ データベースの最新の完全バックアップがない場合は、プライマリ レプリカをホストするサーバー インスタンスに接続し、データベースの完全バックアップを作成してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-163">Unless you have a recent full backup of the primary database, connect to the server instance that hosts the primary replica and create a full database backup.</span></span> <span data-ttu-id="e5552-164">このバックアップとそれ以降のすべてのログ バックアップは、推奨されるネットワーク共有に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5552-164">As a best practice, place this backup and any subsequent log backups onto the recommended network share.</span></span>  
  
2.  <span data-ttu-id="e5552-165">セカンダリ レプリカをホストするサーバー インスタンスで、プライマリ データベースの完全バックアップ (および必要に応じて差分バックアップ)、それ以降のすべてのログ バックアップの順で復元します。</span><span class="sxs-lookup"><span data-stu-id="e5552-165">On the server instance that hosts the secondary replica, restore the full database backup of the primary database (and optionally a differential backup) followed by all subsequent log backups.</span></span> <span data-ttu-id="e5552-166">すべて復元操作に WITH NORECOVERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5552-166">Use WITH NORECOVERY for every restore operation.</span></span>  
  
     <span data-ttu-id="e5552-167">プライマリ データベースとセカンダリ データベースのファイル パスが異なる場合、たとえばプライマリ データベースはドライブ "F:" にあり、セカンダリ レプリカをホストするサーバー インスタンスに F: ドライブがない場合は、WITH 句に MOVE オプションを含めてください。</span><span class="sxs-lookup"><span data-stu-id="e5552-167">If the file paths of the primary database and the secondary database differ, for example, if the primary database is on drive 'F:' but the server instance that hosts the secondary replica lacks an F: drive, include the MOVE option in your WITH clause.</span></span>  
  
3.  <span data-ttu-id="e5552-168">必要なログ バックアップ以降にプライマリ データベースのログ バックアップを作成した場合は、それらのログ バックアップもセカンダリ レプリカをホストするサーバー インスタンスにコピーして、各ログ バックアップをセカンダリ データベースに適用する必要があります。その際には古いものから順に適用し、毎回 RESTORE WITH NORECOVERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5552-168">If any log backups have been taken on the primary database since the required log backup, you must also copy these to the server instance that hosts the secondary replica and apply each of those log backups to the secondary database, starting with the earliest and always using RESTORE WITH NORECOVERY.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5552-169">プライマリ データベースを作成したばかりでログ バックアップがまだ作成されていない場合や、復旧モデルを単純から完全に変更したばかりの場合には、ログ バックアップが存在しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-169">A log backup would not exist if the primary database has just been created and no log backup has been taken yet or if the recovery model has just been changed from simple to full.</span></span>  
  
4.  <span data-ttu-id="e5552-170">セカンダリ データベースの構成を完了するには、セカンダリ データベースを可用性グループに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-170">To complete configuration of the secondary database, you need to join the secondary database to the availability group.</span></span> <span data-ttu-id="e5552-171">詳細については、「[可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-171">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5552-172"> これらのバックアップ操作および復元操作の実行方法については、このトピックの「 [関連するバックアップと復元のタスク](#RelatedTasks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-172">For information about how to perform these backup and restore operations, see [Related Backup and Restore Tasks](#RelatedTasks), later in this topic.</span></span>  
  
###  <a name="transact-sql-example"></a><a name="ExampleTsql"></a><span data-ttu-id="e5552-173">Transact-sql の例</span><span class="sxs-lookup"><span data-stu-id="e5552-173">Transact-SQL Example</span></span>  
 <span data-ttu-id="e5552-174">次の例では、セカンダリ データベースを準備します。</span><span class="sxs-lookup"><span data-stu-id="e5552-174">The following example prepares a secondary database.</span></span> <span data-ttu-id="e5552-175">この例では、既定で単純復旧モデルを使用する [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5552-175">This example uses the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database, which uses the simple recovery model by default.</span></span>  
  
1.  <span data-ttu-id="e5552-176">[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] データベースを使用するには、完全復旧モデルが使用されるように変更します。</span><span class="sxs-lookup"><span data-stu-id="e5552-176">To use the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database, modify it to use the full recovery model:</span></span>  
  
    ```sql
    USE master;  
    GO  
    ALTER DATABASE MyDB1   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  <span data-ttu-id="e5552-177">データベースの復旧モデルを SIMPLE から FULL に変更した後は、完全バックアップを作成します。作成した完全バックアップはセカンダリ データベースの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="e5552-177">After modifying the recovery model of the database from SIMPLE to FULL, create a full backup, which can be used to create the secondary database.</span></span> <span data-ttu-id="e5552-178">復旧モデルを変更した直後なので、新しいメディア セットを作成するには WITH FORMAT オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e5552-178">Because the recovery model has just been changed, the WITH FORMAT option is specified to create a new media set.</span></span> <span data-ttu-id="e5552-179">これにより、完全復旧モデルのバックアップを、単純復旧モデルで作成された以前のバックアップと分離できます。</span><span class="sxs-lookup"><span data-stu-id="e5552-179">This is useful to separate the backups under the full recovery model from any previous backups made under the simple recovery model.</span></span> <span data-ttu-id="e5552-180">この例では、バックアップ ファイル (C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak) をデータベースと同じドライブに作成します。</span><span class="sxs-lookup"><span data-stu-id="e5552-180">For the purpose of this example, the backup file (C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak) is created on the same drive as the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5552-181">運用データベースを使用する場合は、必ず別のデバイスにバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="e5552-181">For a production database, you should always back up to a separate device.</span></span>  
  
     <span data-ttu-id="e5552-182">プライマリ レプリカをホストするサーバー インスタンス (`INSTANCE01`) 上で、次のとおりプライマリ データベースの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5552-182">On the server instance that hosts the primary replica (`INSTANCE01`), create a full backup of the primary database as follows:</span></span>  
  
    ```sql
    BACKUP DATABASE MyDB1   
        TO DISK = 'C:\MyDB1.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  <span data-ttu-id="e5552-183">セカンダリ レプリカをホストするサーバー インスタンスに完全バックアップをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e5552-183">Copy the full backup to the server instance that hosts the secondary replica.</span></span>  
  
4.  <span data-ttu-id="e5552-184">RESTORE WITH NORECOVERY を使用して、セカンダリ レプリカをホストするサーバー インスタンスに完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="e5552-184">Restore the full backup, using RESTORE WITH NORECOVERY, onto the server instance that hosts the secondary replica.</span></span> <span data-ttu-id="e5552-185">復元コマンドは、プライマリ データベースとセカンダリ データベースのパスが同じかどうかによって変わります。</span><span class="sxs-lookup"><span data-stu-id="e5552-185">The restore command depends on whether the paths of primary and secondary databases are identical.</span></span>  
  
    -   <span data-ttu-id="e5552-186">**パスが同じ場合は、次のようにします。**</span><span class="sxs-lookup"><span data-stu-id="e5552-186">**If the paths are identical:**</span></span>  
  
         <span data-ttu-id="e5552-187">セカンダリ レプリカをホストするコンピューターで、次のとおり完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="e5552-187">On the computer that hosts the secondary replica, restore the full backup as follows:</span></span>  
  
        ```sql
        RESTORE DATABASE MyDB1   
            FROM DISK = 'C:\MyDB1.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   <span data-ttu-id="e5552-188">**パスが異なる場合は、次のようにします。**</span><span class="sxs-lookup"><span data-stu-id="e5552-188">**If the paths differ:**</span></span>  
  
         <span data-ttu-id="e5552-189">セカンダリ データベースのパスがプライマリ データベースのパスと異なる (たとえば、ドライブ文字が異なる) 場合、セカンダリ データベースを作成するには、復元操作に MOVE 句が必要です。</span><span class="sxs-lookup"><span data-stu-id="e5552-189">If the path of the secondary database differs from the path of the primary database (for instance, their drive letters differ), creating the secondary database requires that the restore operation include a MOVE clause.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="e5552-190">プライマリ データベースとセカンダリ データベースのパス名が異なる場合は、ファイルを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="e5552-190">If the path names of the primary and secondary databases differ, you cannot add a file.</span></span> <span data-ttu-id="e5552-191">ファイル追加操作のログの受信時に、セカンダリ レプリカのサーバー インスタンスがプライマリ データベースで使用されるのと同じパスに新しいファイルを配置しようとするためです。</span><span class="sxs-lookup"><span data-stu-id="e5552-191">This is because on receiving the log for the add file operation, the server instance of the secondary replica attempts to place the new file in the same path as used by the primary database.</span></span>  
  
         <span data-ttu-id="e5552-192">たとえば、次のコマンドは、既定の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]インスタンスのデータ ディレクトリ (C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA) に存在するプライマリ データベースのバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="e5552-192">For example, the following command restores a backup of a primary database that resides in the data directory of the default instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA.</span></span> <span data-ttu-id="e5552-193">データベースの復元操作では、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 別のクラスターノードのセカンダリレプリカをホストするという名前の (*AlwaysOn1*) のリモートインスタンスのデータディレクトリにデータベースを移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-193">The restore database operation must move the database to the data directory of a remote instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] named  (*AlwaysOn1*), which hosts the secondary replica on another cluster node.</span></span> <span data-ttu-id="e5552-194">そこで、データファイルとログファイルが C:\Program are *SQL Server\MSSQL12. に復元されます。ALWAYSON1\MSSQL\DATA*ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="e5552-194">There, the data and log files are restored to the *C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA* directory .</span></span> <span data-ttu-id="e5552-195">この復元操作では WITH NORECOVERY を使用してセカンダリ データベースを復元するデータベースに残します。</span><span class="sxs-lookup"><span data-stu-id="e5552-195">The restore operation uses WITH NORECOVERY, to leave the secondary database in the restoring database.</span></span>  
  
        ```sql
        RESTORE DATABASE MyDB1  
          FROM DISK='C:\MyDB1.bak'  
         WITH NORECOVERY,   
            MOVE 'MyDB1_Data' TO   
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.mdf',   
            MOVE 'MyDB1_Log' TO  
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.ldf';  
        GO  
        ```  
  
5.  <span data-ttu-id="e5552-196">完全バックアップを復元した後、プライマリ データベースでログ バックアップを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-196">After you restore the full backup, you must create a log backup on the primary database.</span></span> <span data-ttu-id="e5552-197">たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、ログを *E:\MyDB1_log.bak*というバックアップ ファイルにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="e5552-197">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement backs up the log to the a backup file named *E:\MyDB1_log.bak*:</span></span>  
  
    ```sql
    BACKUP LOG MyDB1   
      TO DISK = 'E:\MyDB1_log.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="e5552-198">データベースをセカンダリ レプリカに参加させるには、必要なログ バックアップ (およびそれ以降のすべてのログ バックアップ) を事前に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-198">Before you can join the database to the secondary replica, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="e5552-199">たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、最初のログを *C:\MyDB1.bak*から復元します。</span><span class="sxs-lookup"><span data-stu-id="e5552-199">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement restores the first log from *C:\MyDB1.bak*:</span></span>  
  
    ```sql
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="e5552-200">データベースをセカンダリ レプリカに参加させる前に追加のログ バックアップが行われた場合は、RESTORE WITH NORECOVERY を使用して、それらすべてのログ バックアップもセカンダリ レプリカをホストするサーバー インスタンスに順番に復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-200">If any additional log backups occur before the database joins the secondary replica, you must also restore all of those log backups, in sequence, to the server instance that hosts the secondary replica using RESTORE WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="e5552-201">たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、2 つの追加のログを *E:\MyDB1_log.bak*から復元します。</span><span class="sxs-lookup"><span data-stu-id="e5552-201">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement restores two additional logs from *E:\MyDB1_log.bak*:</span></span>  
  
    ```sql
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="e5552-202">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="e5552-202">Using PowerShell</span></span>  
 <span data-ttu-id="e5552-203">**セカンダリ データベースを準備するには**</span><span class="sxs-lookup"><span data-stu-id="e5552-203">**To prepare a secondary database**</span></span>  
  
1.  <span data-ttu-id="e5552-204">プライマリ データベースの最新のバックアップを作成する必要がある場合は、プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更します (`cd`)。</span><span class="sxs-lookup"><span data-stu-id="e5552-204">If you need to create a recent backup of the primary database, change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e5552-205">`Backup-SqlDatabase` コマンドレットを使用して各バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5552-205">Use the `Backup-SqlDatabase` cmdlet to create each of the backups.</span></span>  
  
3.  <span data-ttu-id="e5552-206">ディレクトリ変更コマンド (`cd`) を使用して、セカンダリ レプリカをホストするサーバー インスタンスに移動します。</span><span class="sxs-lookup"><span data-stu-id="e5552-206">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
4.  <span data-ttu-id="e5552-207">各プライマリ データベースのデータベースおよびログ バックアップを復元するには、`restore-SqlDatabase` コマンドレットを使用して、`NoRecovery` 復元パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="e5552-207">To restore the database and log backups of each primary database, use the `restore-SqlDatabase` cmdlet, specifying the `NoRecovery` restore parameter.</span></span> <span data-ttu-id="e5552-208">プライマリ レプリカをホストするコンピューターとターゲット セカンダリ レプリカをホストするコンピューターとでファイル パスが異なる場合は、`RelocateFile` 復元パラメーターも使用します。</span><span class="sxs-lookup"><span data-stu-id="e5552-208">If the file paths differ between the computers that host the primary replica and the target secondary replica, also use the `RelocateFile` restore parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5552-209">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5552-209">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="e5552-210">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-210">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
5.  <span data-ttu-id="e5552-211">セカンダリ データベースの構成を完了するには、セカンダリ データベースを可用性グループに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-211">To complete configuration of the secondary database, you need to join it to the availability group.</span></span> <span data-ttu-id="e5552-212">詳細については、「[可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5552-212">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="e5552-213">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="e5552-213">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="e5552-214">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="e5552-214">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="sample-backup-and-restore-script-and-command"></a><a name="ExamplePSscript"></a><span data-ttu-id="e5552-215">バックアップと復元のスクリプトとコマンドのサンプル</span><span class="sxs-lookup"><span data-stu-id="e5552-215">Sample Backup and Restore Script and Command</span></span>  
 <span data-ttu-id="e5552-216">次の PowerShell コマンドは、データベースの完全バックアップとトランザクション ログをネットワーク共有にバックアップし、その共有からこれらのバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="e5552-216">The following PowerShell commands back up a full database backup and transaction log to a network share and restore those backups from that share.</span></span> <span data-ttu-id="e5552-217">この例では、データベースの復元先のファイル パスとデータベースがバックアップされたファイル パスが同じであると想定しています。</span><span class="sxs-lookup"><span data-stu-id="e5552-217">This example assumes that the file path to which the database is restored is the same as the file path on which the database was backed up.</span></span>  
  
```powershell
# Create database backup  
Backup-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -ServerInstance "SourceMachine\Instance"  
# Create log backup  
Backup-SqlDatabase -Database "MyDB1" -BackupAction "Log" -BackupFile "\\share\backups\MyDB1.trn" -ServerInstance "SourceMachine\Instance"  
# Restore database backup
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -NoRecovery -ServerInstance "DestinationMachine\Instance"  
# Restore log backup
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.trn" -RestoreAction "Log" -NoRecovery -ServerInstance "DestinationMachine\Instance"
```  
  
##  <a name="follow-up-after-preparing-a-secondary-database"></a><a name="FollowUp"></a><span data-ttu-id="e5552-218">補足情報: セカンダリデータベースを準備した後</span><span class="sxs-lookup"><span data-stu-id="e5552-218">Follow Up: After Preparing a Secondary Database</span></span>  
 <span data-ttu-id="e5552-219">セカンダリ データベースの構成を完了するには、新たに復元したデータベースを可用性グループに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5552-219">To complete configuration of the secondary database, join the newly restored database to the availability group.</span></span> <span data-ttu-id="e5552-220">詳細については、「 [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5552-220">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5552-221">参照</span><span class="sxs-lookup"><span data-stu-id="e5552-221">See Also</span></span>  
 <span data-ttu-id="e5552-222">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e5552-222">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e5552-223">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e5552-223">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="e5552-224">[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e5552-224">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="e5552-225">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e5552-225">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="e5552-226">失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="e5552-226">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
