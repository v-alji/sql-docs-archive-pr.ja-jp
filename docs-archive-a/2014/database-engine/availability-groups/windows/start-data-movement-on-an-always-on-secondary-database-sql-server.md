---
title: AlwaysOn セカンダリデータベースでのデータ移動の開始 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], databases
ms.assetid: 498eb3fb-6a43-434d-ad95-68a754232c45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ce4f80b456244cd6e024377383abe75e002057a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741290"
---
# <a name="start-data-movement-on-an-alwayson-secondary-database-sql-server"></a><span data-ttu-id="d0ff9-102">AlwaysOn セカンダリ データベース上のデータ移動の開始 (SQLServer)</span><span class="sxs-lookup"><span data-stu-id="d0ff9-102">Start Data Movement on an AlwaysOn Secondary Database (SQL Server)</span></span>
  <span data-ttu-id="d0ff9-103">このトピックでは、AlwaysOn 可用性グループにデータベースを追加した後、データの同期を開始する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-103">This topic contains information about how to start data synchronization after you add a database to an AlwaysOn availability group.</span></span> <span data-ttu-id="d0ff9-104">新しい各プライマリ レプリカに対して、セカンダリ レプリカをホストするサーバー インスタンス上でセカンダリ データベースを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-104">For each new primary replica, secondary databases must be prepared on the server instances that host the secondary replicas.</span></span> <span data-ttu-id="d0ff9-105">その後、各セカンダリ データベースを手動で可用性グループに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-105">Then each of these secondary databases must be manually joined to the availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0ff9-106">可用性グループの可用性レプリカをホストするすべてのサーバー インスタンス上のファイル パスが同じである場合は、 [新しい可用性グループ ウィザード](use-the-availability-group-wizard-sql-server-management-studio.md)、 [可用性グループへのレプリカ追加ウィザード](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)、または [可用性グループへのデータベース追加ウィザード](availability-group-add-database-to-group-wizard.md) を使用してデータ同期を自動的に開始できます。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-106">If the file paths are identical on every server instance that hosts an availability replica for an availability group, the [New Availability Group Wizard](use-the-availability-group-wizard-sql-server-management-studio.md), [Add Replica to Availability Group Wizard](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md), or [Add Database to Availability Group Wizard](availability-group-add-database-to-group-wizard.md) might be able to automatically start data synchronization for you.</span></span>  
  
 <span data-ttu-id="d0ff9-107">データ同期を手動で開始するには、可用性グループのセカンダリ レプリカをホストする各サーバー インスタンスに接続し、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-107">To start data synchronization manually, you need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:</span></span>  
  
1.  <span data-ttu-id="d0ff9-108">各プライマリ データベースとそのトランザクション ログの最新のバックアップを復元します (RESTORE WITH NORECOVERY を使用)。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-108">Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY).</span></span> <span data-ttu-id="d0ff9-109">次のいずれかの代替方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-109">You can use either of the following alternative approaches:</span></span>  
  
    -   <span data-ttu-id="d0ff9-110">RESTORE WITH NORECOVERY を使用してプライマリ データベースの最新のデータベース バックアップを手動で復元し、その後、RESTORE WITH NORECOVERY を使用して後続のログ バックアップを復元する。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-110">Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="d0ff9-111">可用性グループのセカンダリ レプリカをホストする各サーバー インスタンスで、この復元シーケンスを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-111">Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.</span></span>  
  
         <span data-ttu-id="d0ff9-112">**詳細情報:**</span><span class="sxs-lookup"><span data-stu-id="d0ff9-112">**For more information:**</span></span>  
  
         [<span data-ttu-id="d0ff9-113">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d0ff9-113">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
    -   <span data-ttu-id="d0ff9-114">可用性グループに 1 つ以上のログ配布プライマリ データベースを追加する場合は、対応する 1 つ以上のセカンダリ データベースをログ配布から AlwaysOn 可用性グループに移行できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-114">If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to AlwaysOn Availability Groups.</span></span> <span data-ttu-id="d0ff9-115">ログ配布セカンダリ データベースを移行するには、それがプライマリ データベースと同じデータベース名を使用していて、可用性グループのセカンダリ レプリカをホストしているサーバー インスタンス上に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-115">Migrating a log shipping secondary database requires that it use the same database name as the primary database and that it reside on a server instance that is hosting a secondary replica for the availability group.</span></span> <span data-ttu-id="d0ff9-116">さらに、可用性グループを、プライマリ レプリカがバックアップ用に推奨され、バックアップの実行の候補になるように構成する (つまり、バックアップの優先順位を >0 にする) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-116">Furthermore, the availability group must be configured so that the primary replica is preferred for backups and is a candidate for performing backups (that is, that has a backup priority that is >0).</span></span> <span data-ttu-id="d0ff9-117">バックアップ ジョブをプライマリ データベース上で実行した後は、バックアップ ジョブを無効にし、復元ジョブを特定のセカンダリ データベース上で実行した後は、復元ジョブを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-117">Once the backup job has run on the primary database, you will need to disable the backup job, and once the restore job has run on a given secondary database, you will need to disable the restore job.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d0ff9-118">可用性グループのすべてのセカンダリ データベースを作成した後、セカンダリ レプリカにバックアップを実行する場合は、可用性グループの自動バックアップ設定を再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-118">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.</span></span>  
  
         <span data-ttu-id="d0ff9-119">**詳細情報:**</span><span class="sxs-lookup"><span data-stu-id="d0ff9-119">**For more information:**</span></span>  
  
         [<span data-ttu-id="d0ff9-120">ログ配布から AlwaysOn 可用性グループ &#40;SQL Server への移行の前提条件&#41;</span><span class="sxs-lookup"><span data-stu-id="d0ff9-120">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
         [<span data-ttu-id="d0ff9-121">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d0ff9-121">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
2.  <span data-ttu-id="d0ff9-122">新しく準備された各セカンダリ データベースを可用性グループにできるだけ早く参加させます。</span><span class="sxs-lookup"><span data-stu-id="d0ff9-122">As soon as possible, join each newly prepared secondary database to the availability group.</span></span>  
  
     <span data-ttu-id="d0ff9-123">**詳細情報:**</span><span class="sxs-lookup"><span data-stu-id="d0ff9-123">**For more information:**</span></span>  
  
     [<span data-ttu-id="d0ff9-124">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d0ff9-124">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> <span data-ttu-id="d0ff9-125">関連タスク</span><span class="sxs-lookup"><span data-stu-id="d0ff9-125">Related Tasks</span></span>  
  
-   <span data-ttu-id="d0ff9-126">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="d0ff9-126">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="d0ff9-127">可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d0ff9-127">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="d0ff9-128">可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d0ff9-128">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="d0ff9-129">参照</span><span class="sxs-lookup"><span data-stu-id="d0ff9-129">See Also</span></span>  
 [<span data-ttu-id="d0ff9-130">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="d0ff9-130">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
