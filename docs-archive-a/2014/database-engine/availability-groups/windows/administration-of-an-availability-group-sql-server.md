---
title: 可用性グループの管理 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], managing
ms.assetid: 0b7542fa-235e-413d-81bf-3eff9ee07480
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2cac9a34fe71c11f71ec47bbb6d690199869fef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632713"
---
# <a name="administration-of-an-availability-group-sql-server"></a><span data-ttu-id="3c593-102">可用性グループの管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3c593-102">Administration of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="3c593-103">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の既存の AlwaysOn 可用性グループの管理には、次のタスクが 1 つ以上含まれます。</span><span class="sxs-lookup"><span data-stu-id="3c593-103">Managing an existing AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] involves one or more of the following tasks:</span></span>  
  
-   <span data-ttu-id="3c593-104">既存の可用性レプリカのプロパティを変更する。たとえば、読み取り可能なセカンダリ レプリカを構成するためにクライアント接続アクセスを変更する場合は、フェールオーバー モード、可用性モード、またはセッション タイムアウトの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="3c593-104">Altering the properties of an existing availability replica, for example to change client connection access (for configuring readable secondary replicas), changing its failover mode, availability mode, or session timeout setting.</span></span>  
  
-   <span data-ttu-id="3c593-105">セカンダリ レプリカを追加または削除する。</span><span class="sxs-lookup"><span data-stu-id="3c593-105">Adding or removing secondary replicas.</span></span>  
  
-   <span data-ttu-id="3c593-106">データベースを追加または削除する。</span><span class="sxs-lookup"><span data-stu-id="3c593-106">Adding or removing a database.</span></span>  
  
-   <span data-ttu-id="3c593-107">データベースを中断または再開する。</span><span class="sxs-lookup"><span data-stu-id="3c593-107">Suspending or resuming a database.</span></span>  
  
-   <span data-ttu-id="3c593-108">計画的な手動フェールオーバー ( *手動フェールオーバー*) または強制手動フェールオーバー ( *強制フェールオーバー*) を実行する。</span><span class="sxs-lookup"><span data-stu-id="3c593-108">Performing a planned manual failover (a *manual failover*) or a forced manual failover (a *forced failover*).</span></span>  
  
-   <span data-ttu-id="3c593-109">可用性グループ リスナーを作成または構成する。</span><span class="sxs-lookup"><span data-stu-id="3c593-109">Creating or configuring an availability group listener.</span></span>  
  
-   <span data-ttu-id="3c593-110">可用性グループの [読み取り可能なセカンダリ レプリカ](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) を管理する。</span><span class="sxs-lookup"><span data-stu-id="3c593-110">Managing [readable secondary replicas](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) for a given availability group.</span></span> <span data-ttu-id="3c593-111">セカンダリ ロールで実行されているときに読み取り専用アクセスを行うように 1 つ以上のレプリカを構成し、読み取り専用ルーティングを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c593-111">This involves configuring one or more replicas to read-only access when running under the secondary role, and configuring read-only routing.</span></span>  
  
-   <span data-ttu-id="3c593-112">可用性グループの [セカンダリ レプリカでのバックアップ](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) を管理する。</span><span class="sxs-lookup"><span data-stu-id="3c593-112">Managing [backups on secondary replicas](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) for a given availability group.</span></span> <span data-ttu-id="3c593-113">バックアップ ジョブを優先的に実行する場所を構成し、バックアップ設定を実装するためにバックアップ ジョブのスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c593-113">This involves configuring where you prefer that backup jobs run and then scripting backup jobs to implement your backup preference.</span></span> <span data-ttu-id="3c593-114">可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のすべてのインスタンスで、可用性グループの各データベースのバックアップ ジョブのスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c593-114">you need to script backup jobs for every database in the availability group on every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica.</span></span>  
  
-   <span data-ttu-id="3c593-115">可用性グループを削除する。</span><span class="sxs-lookup"><span data-stu-id="3c593-115">Deleting an availability group.</span></span>  
  
-   <span data-ttu-id="3c593-116">OS アップグレードのための AlwaysOn 可用性グループのクラスター間での移行</span><span class="sxs-lookup"><span data-stu-id="3c593-116">Cross-cluster migration of AlwaysOn Availability Groups for OS upgrade</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3c593-117">関連タスク</span><span class="sxs-lookup"><span data-stu-id="3c593-117">Related Tasks</span></span>  
 <span data-ttu-id="3c593-118">**既存の可用性グループを構成するには**</span><span class="sxs-lookup"><span data-stu-id="3c593-118">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="3c593-119">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-119">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-120">可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-120">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-121">可用性グループへのデータベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-121">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="3c593-122">可用性グループからのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-122">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-123">可用性グループからのプライマリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-123">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-124">自動フェールオーバー &#40;AlwaysOn 可用性グループの条件を制御する柔軟なフェールオーバーポリシーを構成&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-124">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover &#40;AlwaysOn Availability Groups&#41;</span></span>](configure-flexible-automatic-failover-policy.md)  
  
 <span data-ttu-id="3c593-125">**可用性グループを管理するには**</span><span class="sxs-lookup"><span data-stu-id="3c593-125">**To manage an availability group**</span></span>  
  
-   [<span data-ttu-id="3c593-126">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-126">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="3c593-127">可用性グループの計画的な手動フェールオーバーの実行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-127">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-128">可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-128">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-129">可用性グループの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-129">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="3c593-130">**可用性レプリカを管理するには**</span><span class="sxs-lookup"><span data-stu-id="3c593-130">**To manage an availability replica**</span></span>  
  
-   [<span data-ttu-id="3c593-131">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-131">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-132">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-132">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-133">可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-133">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-134">可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-134">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="3c593-135">可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-135">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="3c593-136">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-136">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="3c593-137">可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-137">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="3c593-138">可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-138">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-139">可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-139">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="3c593-140">**可用性データベースを管理するには**</span><span class="sxs-lookup"><span data-stu-id="3c593-140">**To manage an availability database**</span></span>  
  
-   [<span data-ttu-id="3c593-141">可用性グループへのデータベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-141">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="3c593-142">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-142">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-143">可用性グループからのプライマリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-143">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-144">可用性グループからのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-144">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3c593-145">可用性データベースの中断 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-145">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="3c593-146">可用性データベースの再開 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-146">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
 <span data-ttu-id="3c593-147">**可用性グループを監視するには**</span><span class="sxs-lookup"><span data-stu-id="3c593-147">**To monitor an availability group**</span></span>  
  
-   [<span data-ttu-id="3c593-148">可用性グループの監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-148">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
 <span data-ttu-id="3c593-149">**新しい WSFC クラスターへの可用性グループの移行 (クラスター間での移行) をサポートするには**</span><span class="sxs-lookup"><span data-stu-id="3c593-149">**To support migrating availability groups to a new WSFC cluster (cross-cluster migration)**</span></span>  
  
-   [<span data-ttu-id="3c593-150">サーバー インスタンスの HADR クラスター コンテキストの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-150">Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;</span></span>](change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
-   [<span data-ttu-id="3c593-151">可用性グループをオフラインにする &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-151">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="3c593-152">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="3c593-152">Related Content</span></span>  
  
-   <span data-ttu-id="3c593-153">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="3c593-153">**Blogs:**</span></span>  
  
     [<span data-ttu-id="3c593-154">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="3c593-154">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="3c593-155">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="3c593-155">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="3c593-156">**ビデオ:**</span><span class="sxs-lookup"><span data-stu-id="3c593-156">**Videos:**</span></span>  
  
     [<span data-ttu-id="3c593-157">Microsoft SQL Server コード ネーム "Denali" AlwaysOn シリーズ パート 1: 次世代の高可用性ソリューションの概要</span><span class="sxs-lookup"><span data-stu-id="3c593-157">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="3c593-158">Microsoft SQL Server コードネーム "Denali" AlwaysOn シリーズ パート 2: AlwaysOn を使用したミッション クリティカルな高可用性ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="3c593-158">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="3c593-159">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="3c593-159">**White papers:**</span></span>  
  
     [<span data-ttu-id="3c593-160">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="3c593-160">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="3c593-161">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="3c593-161">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
  
## <a name="see-also"></a><span data-ttu-id="3c593-162">参照</span><span class="sxs-lookup"><span data-stu-id="3c593-162">See Also</span></span>  
 <span data-ttu-id="3c593-163">[AlwaysOn 可用性グループ &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-163">[AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="3c593-164">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-164">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="3c593-165">AlwaysOn 可用性グループ &#40;SQL Server のサーバーインスタンスの構成&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-165">Configuration of a Server Instance for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="3c593-166">[可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-166">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="3c593-167">[アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ &#40;AlwaysOn 可用性グループ&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-167">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="3c593-168">アクティブなセカンダリ: セカンダリレプリカでのバックアップ &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-168">Active Secondaries: Backup on Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
 <span data-ttu-id="3c593-169">[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-169">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="3c593-170">[AlwaysOn 可用性グループ &#40;SQL Server での運用上の問題のための AlwaysOn ポリシー&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-170">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="3c593-171">[可用性グループの監視 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-171">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="3c593-172">[AlwaysOn 可用性グループ: 相互運用性 &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-172">[AlwaysOn Availability Groups: Interoperability &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 <span data-ttu-id="3c593-173">[AlwaysOn 可用性グループ &#40;SQL Server の Transact-sql ステートメントの概要&#41;](transact-sql-statements-for-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="3c593-173">[Overview of Transact-SQL Statements for AlwaysOn Availability Groups &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="3c593-174">AlwaysOn 可用性グループ &#40;SQL Server の PowerShell コマンドレットの概要&#41;</span><span class="sxs-lookup"><span data-stu-id="3c593-174">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
