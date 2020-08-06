---
title: 可用性レプリカのプロパティの表示 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- ', policies'
ms.assetid: 14fed3c4-8ecc-4e1c-931d-a7ec1e9f9e90
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ca7b0508907b4d86c9ee627438a3f18e1b01fdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716829"
---
# <a name="view-availability-replica-properties-sql-server"></a><span data-ttu-id="7e0d7-102">可用性レプリカのプロパティの表示 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7e0d7-102">View Availability Replica Properties (SQL Server)</span></span>
  <span data-ttu-id="7e0d7-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)] または [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して、AlwaysOn 可用性グループの可用性レプリカのプロパティを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-103">This topic describes how to view the properties of an availability replica for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7e0d7-104">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7e0d7-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="7e0d7-105">**可用性レプリカのプロパティを表示および変更するには**</span><span class="sxs-lookup"><span data-stu-id="7e0d7-105">**To view and change properties an availability replica**</span></span>  
  
1.  <span data-ttu-id="7e0d7-106">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="7e0d7-107">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="7e0d7-108">可用性レプリカが属する可用性グループを展開し、[ **可用性レプリカ** ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-108">Expand the availability group to which the availability replica belongs, and expand the **Availability Replicas** node.</span></span>  
  
4.  <span data-ttu-id="7e0d7-109">プロパティを表示する可用性レプリカを右クリックし、[ **プロパティ** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-109">Right-click the availability replica whose properties you want to view, and select the **Properties** command.</span></span>  
  
5.  <span data-ttu-id="7e0d7-110">[ **可用性レプリカ プロパティ** ] ダイアログ ボックスで、[ **全般** ] ページを使用して、このレプリカのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-110">In the **Availability Replica Properties** dialog box, use the **General** page to view the properties of this replica.</span></span> <span data-ttu-id="7e0d7-111">プライマリ レプリカに接続している場合に変更できるプロパティは、可用性モード、フェールオーバー モード、プライマリ ロールの接続アクセス、セカンダリ ロールの読み取りアクセス (読み取り可能なセカンダリ)、およびセッション タイムアウトの値です。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-111">If you are connected to the primary replica, you can change the following properties: availability mode, failover mode, connection access for the primary role, read-access for the secondary role (readable-secondary), and the session-timeout value.</span></span> <span data-ttu-id="7e0d7-112">詳細については、「[可用性レプリカのプロパティ &#40;全般ページ&#41;](availability-replica-properties-general-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-112">For more information, see  [Availability Replica Properties &#40;General Page&#41;](availability-replica-properties-general-page.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7e0d7-113">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7e0d7-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="7e0d7-114">**可用性レプリカのプロパティおよび状態を表示するには**</span><span class="sxs-lookup"><span data-stu-id="7e0d7-114">**To view properties and states of availability replicas**</span></span>  
  
 <span data-ttu-id="7e0d7-115">可用性レプリカのプロパティおよび状態を表示するには、次のビューとシステム関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-115">To view the properties and states of availability replicas, use the following views and system function:</span></span>  
  
 [<span data-ttu-id="7e0d7-116">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="7e0d7-116">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 <span data-ttu-id="7e0d7-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスが可用性レプリカをホストしている各可用性グループ内の可用性レプリカごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-117">Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span>  
  
 <span data-ttu-id="7e0d7-118">**列名:** replica_id、group_id、replica_metadata_id、replica_server_name、owner_sid、endpoint_url、availability_mode、availability_mode_desc、failover_mode、failover_mode_desc、session_timeout、primary_role_allow_connections、primary_role_allow_connections_desc、secondary_role_allow_connections、secondary_role_allow_connections_desc、create_date、modify_date、backup_priority、read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="7e0d7-118">**Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span></span>  
  
 [<span data-ttu-id="7e0d7-119">sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="7e0d7-119">sys.availability_read_only_routing_lists</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 <span data-ttu-id="7e0d7-120">WSFC フェールオーバー クラスター内の AlwaysOn 可用性グループにある各可用性レプリカの読み取り専用ルーティング リストに対する行を返します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-120">Returns a row for the read only routing list of each availability replica in an AlwaysOn availability group in the WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="7e0d7-121">**列名:** replica_id、routing_priority、read_only_replica_id</span><span class="sxs-lookup"><span data-stu-id="7e0d7-121">**Column names:** replica_id, routing_priority, read_only_replica_id</span></span>  
  
 [<span data-ttu-id="7e0d7-122">可用性レプリカの監視</span><span class="sxs-lookup"><span data-stu-id="7e0d7-122">sys.dm_hadr_availability_replica_cluster_nodes</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 <span data-ttu-id="7e0d7-123">Windows Server フェールオーバー クラスタリング (WSFC) クラスター内の AlwaysOn 可用性グループの可用性レプリカ (結合状態に関係なく) ごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-123">Returns a row for every availability replica (regardless of join state) of the AlwaysOn availability groups in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="7e0d7-124">**列名:** group_name、replica_server_name、node_name</span><span class="sxs-lookup"><span data-stu-id="7e0d7-124">**Column names:** group_name, replica_server_name, node_name</span></span>  
  
 [<span data-ttu-id="7e0d7-125">sys.dm_hadr_availability_replica_cluster_nodes</span><span class="sxs-lookup"><span data-stu-id="7e0d7-125">sys.dm_hadr_availability_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 <span data-ttu-id="7e0d7-126">Windows Server フェールオーバー クラスタリング (WSFC) クラスター内のすべての AlwaysOn 可用性グループ (レプリカの場所に関係なく) のレプリカ (結合状態に関係なく) ごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-126">Returns a row for each replica (regardless of join state) of all AlwaysOn availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="7e0d7-127">**列名:** replica_id、replica_server_name、group_id、join_state、join_state_desc</span><span class="sxs-lookup"><span data-stu-id="7e0d7-127">**Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span></span>  
  
 [<span data-ttu-id="7e0d7-128">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="7e0d7-128">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 <span data-ttu-id="7e0d7-129">各ローカル可用性レプリカの状態を示す 1 行のデータと、同じ可用性グループに含まれるリモート可用性グループごとの 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-129">Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.</span></span>  
  
 <span data-ttu-id="7e0d7-130">**列名:** replica_id、group_id、is_local、role、role_desc、operational_state、operational_state_desc、connected_state、connected_state_desc、recovery_health、recovery_health_desc、synchronization_health、synchronization_health_desc、last_connect_error_number、last_connect_error_description、last_connect_error_timestamp</span><span class="sxs-lookup"><span data-stu-id="7e0d7-130">**Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp</span></span>  
  
 [<span data-ttu-id="7e0d7-131">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="7e0d7-131">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 <span data-ttu-id="7e0d7-132">現在のレプリカが推奨されるバックアップ レプリカであるかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-132">Determines whether the current replica is the preferred backup replica.</span></span> <span data-ttu-id="7e0d7-133">現在のサーバー インスタンス上のデータベースが推奨されるレプリカの場合は 1 を返します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-133">Returns 1 if the database on the current server instance is the preferred replica.</span></span> <span data-ttu-id="7e0d7-134">それ以外の場合は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-134">Otherwise, it returns 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e0d7-135">可用性レプリカのパフォーマンス カウンター ( **SQLServer:可用性レプリカ**  パフォーマンス オブジェクト) の詳細については、「 [SQL Server、可用性レプリカ](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e0d7-135">For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7e0d7-136">関連タスク</span><span class="sxs-lookup"><span data-stu-id="7e0d7-136">Related Tasks</span></span>  
 <span data-ttu-id="7e0d7-137">**可用性グループに関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="7e0d7-137">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="7e0d7-138">可用性グループのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-138">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-139">可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-139">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-140">AlwaysOn 可用性グループ &#40;SQL Server での運用上の問題のための AlwaysOn ポリシー&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-140">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="7e0d7-141">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-141">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="7e0d7-142">可用性グループの監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-142">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="7e0d7-143">**可用性レプリカを管理するには**</span><span class="sxs-lookup"><span data-stu-id="7e0d7-143">**To manage availability replicas**</span></span>  
  
-   [<span data-ttu-id="7e0d7-144">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-144">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-145">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-145">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-146">可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-146">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-147">可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-147">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-148">可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-148">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-149">可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-149">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-150">可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-150">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="7e0d7-151">**可用性データベースを管理するには**</span><span class="sxs-lookup"><span data-stu-id="7e0d7-151">**To manage an availability database**</span></span>  
  
-   [<span data-ttu-id="7e0d7-152">可用性グループへのデータベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-152">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="7e0d7-153">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-153">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-154">可用性データベースの中断 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-154">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-155">可用性データベースの再開 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-155">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-156">可用性グループからのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-156">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="7e0d7-157">可用性グループからのプライマリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-157">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="7e0d7-158">参照</span><span class="sxs-lookup"><span data-stu-id="7e0d7-158">See Also</span></span>  
 <span data-ttu-id="7e0d7-159">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e0d7-159">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="7e0d7-160">[Transact-sql&#41;&#40;可用性グループの監視](monitor-availability-groups-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="7e0d7-160">[Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) </span></span>  
 <span data-ttu-id="7e0d7-161">[AlwaysOn 可用性グループ &#40;SQL Server での運用上の問題のための AlwaysOn ポリシー&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="7e0d7-161">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 [<span data-ttu-id="7e0d7-162">可用性グループ &#40;SQL Server の管理&#41;</span><span class="sxs-lookup"><span data-stu-id="7e0d7-162">Administration of an Availability Group &#40;SQL Server&#41;</span></span>](administration-of-an-availability-group-sql-server.md)  
  
  
