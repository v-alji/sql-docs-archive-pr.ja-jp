---
title: 可用性グループの監視 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- dynamic management views [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], databases
- catalog views [SQL Server], AlwaysOn Availability Groups
ms.assetid: 881a34de-8461-4811-8c62-322bf7226bed
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 103dd8eef782dfa7a4d13929b0b832dba9bc46e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634645"
---
# <a name="monitor-availability-groups-transact-sql"></a><span data-ttu-id="15192-102">可用性グループの監視 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="15192-102">Monitor Availability Groups (Transact-SQL)</span></span>
  <span data-ttu-id="15192-103">[!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して可用性グループ、可用性レプリカ、および関連付けられているデータベースを監視できるように、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] には、一連のカタログ ビュー、動的管理ビュー、およびサーバー プロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="15192-103">For monitoring availability groups and replicas and the associated databases by using [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] provides a set of catalog and dynamic management views and server properties.</span></span> <span data-ttu-id="15192-104">[!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT ステートメントを使用すると、これらのビューで、可用性グループや、そのレプリカおよびデータベースを監視できます。</span><span class="sxs-lookup"><span data-stu-id="15192-104">Using [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT statements, you can use the views to monitor availability groups and their replicas and databases.</span></span> <span data-ttu-id="15192-105">特定の可用性グループに対して返される情報は、接続している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにプライマリ レプリカとセカンダリ レプリカのどちらがホストされているかによって変わります。</span><span class="sxs-lookup"><span data-stu-id="15192-105">The information returned for a given availability group depends on whether you are connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting the primary replica or a secondary replica.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="15192-106">これらのビューの多くは ID 列を使用して結合可能であり、1 つのクエリで複数のビューの情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="15192-106">Many of these views can be joined using their ID columns to return information from multiple views in a single query.</span></span>  
  
 
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="15192-107">Permissions</span><span class="sxs-lookup"><span data-stu-id="15192-107">Permissions</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="15192-108">カタログ ビューでは、サーバー インスタンスに対する VIEW ANY DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="15192-108">catalog views require VIEW ANY DEFINITION permission on the server instance.</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="15192-109">動的管理ビューでは、サーバーに対する VIEW SERVER STATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="15192-109">dynamic management views require VIEW SERVER STATE permission on the server.</span></span>  
  
##  <a name="monitoring-the-alwayson-availability-groups-feature-on-a-server-instance"></a><a name="AoAgFeatureOnSI"></a><span data-ttu-id="15192-110">サーバーインスタンスの AlwaysOn 可用性グループ機能の監視</span><span class="sxs-lookup"><span data-stu-id="15192-110">Monitoring the AlwaysOn Availability Groups Feature on a Server Instance</span></span>  
 <span data-ttu-id="15192-111">サーバー インスタンス上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能を監視するには、次の組み込み関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="15192-111">To monitor the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on a server instance, use the following built-in function:</span></span>  
  
 <span data-ttu-id="15192-112">[SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) 関数</span><span class="sxs-lookup"><span data-stu-id="15192-112">[SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) function</span></span>  
 <span data-ttu-id="15192-113">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] が有効かどうかと、それが有効な場合はサーバー インスタンスで開始されているかどうかに関するサーバー プロパティ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="15192-113">Returns server property information about whether [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is enabled and, if so, whether it has started on the server instance.</span></span>  
  
 <span data-ttu-id="15192-114">**列名:** IsHadrEnabled、HadrManagerStatus</span><span class="sxs-lookup"><span data-stu-id="15192-114">**Column names:** IsHadrEnabled, HadrManagerStatus</span></span>  
  
##  <a name="monitoring-availability-groups-on-the-wsfc-cluster"></a><a name="WSFC"></a><span data-ttu-id="15192-115">WSFC クラスターの可用性グループの監視</span><span class="sxs-lookup"><span data-stu-id="15192-115">Monitoring Availability Groups on the WSFC Cluster</span></span>  
 <span data-ttu-id="15192-116">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]に対応したローカル サーバー インスタンスをホストする Windows Server フェールオーバー クラスタリング (WSFC) クラスターを監視するには、次のビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="15192-116">To monitor the Windows Server Failover Clustering (WSFC) cluster that hosts a local server instance that is enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], use the following views:</span></span>  
  
 [<span data-ttu-id="15192-117">sys.dm_hadr_cluster</span><span class="sxs-lookup"><span data-stu-id="15192-117">sys.dm_hadr_cluster</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
 <span data-ttu-id="15192-118">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に対応した SQL Server のインスタンスをホストする Windows Server フェールオーバー クラスタリング (WSFC) ノードに WSFC のクォーラムが存在する場合、 **sys.dm_hadr_cluster** は、クラスター名とクォーラムに関する情報を公開する行を返します。</span><span class="sxs-lookup"><span data-stu-id="15192-118">If the Windows Server Failover Clustering (WSFC) node that hosts an instance of SQL Server with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] enabled has WSFC quorum, **sys.dm_hadr_cluster** returns a row that exposes the cluster name and information about the quorum.</span></span> <span data-ttu-id="15192-119">WSFC ノードにクォーラムが存在しない場合、行は返されません。</span><span class="sxs-lookup"><span data-stu-id="15192-119">If the WSFC node has no quorum, no rows are returned.</span></span>  
  
 <span data-ttu-id="15192-120">**列名:** cluster_name、quorum_type、quorum_type_desc、quorum_state、quorum_state_desc</span><span class="sxs-lookup"><span data-stu-id="15192-120">**Column names:** cluster_name, quorum_type, quorum_type_desc, quorum_state, quorum_state_desc</span></span>  
  
 [<span data-ttu-id="15192-121">sys.dm_hadr_cluster_members</span><span class="sxs-lookup"><span data-stu-id="15192-121">sys.dm_hadr_cluster_members</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
 <span data-ttu-id="15192-122">AlwaysOn が有効な SQL Server のローカル インスタンスをホストする WSFC ノードに WSFC クォーラムが存在する場合は、クォーラムを構成するメンバーごとに 1 行のデータと、各メンバーの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="15192-122">If the WSFC node that hosts the local AlwaysOn-enabled instance of SQL Server has WSFC quorum, returns a row for each of the members that constitute the quorum and the state of each of them.</span></span>  
  
 <span data-ttu-id="15192-123">**列名:** member_name、member_type、member_type_desc、member_state、member_state_desc、number_of_quorum_votes</span><span class="sxs-lookup"><span data-stu-id="15192-123">**Column names:** member_name, member_type, member_type_desc, member_state, member_state_desc, number_of_quorum_votes</span></span>  
  
 [<span data-ttu-id="15192-124">sys.dm_hadr_cluster_networks</span><span class="sxs-lookup"><span data-stu-id="15192-124">sys.dm_hadr_cluster_networks</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
 <span data-ttu-id="15192-125">可用性グループのサブネット構成に参加しているメンバーごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-125">Returns a row for every member that is participating in an availability group's subnet configuration.</span></span> <span data-ttu-id="15192-126">この動的管理ビューを使用して、可用性レプリカごとに構成されているネットワーク仮想 IP を検証できます。</span><span class="sxs-lookup"><span data-stu-id="15192-126">You can use this dynamic management view to validate the network virtual IP that is configured for each availability replica.</span></span>  
  
 <span data-ttu-id="15192-127">**列名:** member_name、network_subnet_ip、network_subnet_ipv4_mask、network_subnet_prefix_length、is_public、is_ipv4</span><span class="sxs-lookup"><span data-stu-id="15192-127">**Column names:** member_name, network_subnet_ip, network_subnet_ipv4_mask, network_subnet_prefix_length, is_public, is_ipv4</span></span>  
  
 <span data-ttu-id="15192-128">**主キー:** member_name + network_subnet_IP + network_subnet_prefix_length</span><span class="sxs-lookup"><span data-stu-id="15192-128">**Primary key:** member_name + network_subnet_IP + network_subnet_prefix_length</span></span>  
  
 [<span data-ttu-id="15192-129">sys.dm_hadr_instance_node_map</span><span class="sxs-lookup"><span data-stu-id="15192-129">sys.dm_hadr_instance_node_map</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
 <span data-ttu-id="15192-130">AlwaysOn 可用性グループに参加させる可用性レプリカをホストする SQL Server のすべてのインスタンスに対して、サーバー インスタンスをホストする Windows Server フェールオーバー クラスタリング (WSFC) ノードの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="15192-130">For every instance of SQL Server that hosts an availability replica that is joined to its AlwaysOn availability group, returns the name of the Windows Server Failover Clustering (WSFC) node that hosts the server instance.</span></span> <span data-ttu-id="15192-131">この動的管理ビューには、次の用途があります。</span><span class="sxs-lookup"><span data-stu-id="15192-131">This dynamic management view has the following uses:</span></span>  
  
-   <span data-ttu-id="15192-132">この動的管理ビューは、同一の WSFC ノードでホストされている複数の可用性レプリカを持つ可用性グループを検出するために役に立ちます。これはサポート外の構成であり、可用性グループが間違って構成されているときに FCI フェールオーバーが発生した場合にこの状態になることがあります。</span><span class="sxs-lookup"><span data-stu-id="15192-132">This dynamic management view is useful for detecting an availability group with multiple availability replicas that are hosted on the same WSFC node, which is an unsupported configuration that could occur after an FCI failover if the availability group is incorrectly configured.</span></span>  
  
-   <span data-ttu-id="15192-133">複数の SQL Server インスタンスが同一の WSFC ノードでホストされている場合、Resource DLL はこの動的管理ビューを使用して接続先の SQL Server インスタンスを決定します。</span><span class="sxs-lookup"><span data-stu-id="15192-133">When multiple SQL Server instances are hosted on the same WSFC node, the Resource DLL uses this dynamic management view to determine the instance of SQL Server to connect to.</span></span>  
  
 <span data-ttu-id="15192-134">**列名:** ag_resource_id、instance_name、node_name</span><span class="sxs-lookup"><span data-stu-id="15192-134">**Column names:** ag_resource_id, instance_name, node_name</span></span>  
  
 [<span data-ttu-id="15192-135">sys.dm_hadr_name_id_map</span><span class="sxs-lookup"><span data-stu-id="15192-135">sys.dm_hadr_name_id_map</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
 <span data-ttu-id="15192-136">SQL Server の現在のインスタンスが参加する AlwaysOn 可用性グループの、可用性グループ ID、WSFC リソース ID、および WSFC グループ ID という 3 つの一意の ID に対するマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="15192-136">Shows the mapping of AlwaysOn availability groups that the current instance of SQL Server has joined to three unique IDs: an availability group ID, a WSFC resource ID, and a WSFC Group ID.</span></span> <span data-ttu-id="15192-137">このマッピングの目的は、WSFC リソースまたは WSFC グループの名前が変更されるシナリオを処理することです。</span><span class="sxs-lookup"><span data-stu-id="15192-137">The purpose of this mapping is to handle the scenario in which the WSFC resource/group is renamed.</span></span>  
  
 <span data-ttu-id="15192-138">**列名:** ag_name、ag_id、ag_resource_id、ag_group_id</span><span class="sxs-lookup"><span data-stu-id="15192-138">**Column names:** ag_name, ag_id, ag_resource_id, ag_group_id</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15192-139">このトピックの「[可用性レプリカの監視](#AvReplicas)」セクションの **sys.dm_hadr_availability_replica_cluster_nodes** と **sys.dm_hadr_availability_replica_cluster_states** 、および「[可用性データベースの監視](#AvDbs)」セクションの **sys.availability_databases_cluster** と **sys.dm_hadr_database_replica_cluster_states** も参照してください。</span><span class="sxs-lookup"><span data-stu-id="15192-139">Also see **sys.dm_hadr_availability_replica_cluster_nodes** and **sys.dm_hadr_availability_replica_cluster_states** in the [Monitoring Availability Replicas](#AvReplicas) section and **sys.availability_databases_cluster** and **sys.dm_hadr_database_replica_cluster_states** in the [Monitoring Availability Databases](#AvDbs) section, later in this topic.</span></span>  
  
 <span data-ttu-id="15192-140">WSFC クラスターとの詳細について [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] は、「 [Windows Server フェールオーバークラスタリング &#40;wsfc&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)および[フェールオーバークラスタリング」および「AlwaysOn 可用性グループ &#40;](failover-clustering-and-always-on-availability-groups-sql-server.md)SQL Server&#41;」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15192-140">For information about WSFC clusters and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) and [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="monitoring-availability-groups"></a><a name="AvGroups"></a> <span data-ttu-id="15192-141">可用性グループの監視</span><span class="sxs-lookup"><span data-stu-id="15192-141">Monitoring Availability Groups</span></span>  
 <span data-ttu-id="15192-142">サーバー インスタンスが可用性レプリカをホストしている可用性グループを監視するには、次のビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="15192-142">To monitor the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="15192-143">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="15192-143">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="15192-144">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスが可用性レプリカをホストしている各可用性グループの行を返します。</span><span class="sxs-lookup"><span data-stu-id="15192-144">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="15192-145">各行には、可用性グループ メタデータのキャッシュされたコピーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="15192-145">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="15192-146">**列名:** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="15192-146">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="15192-147">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="15192-147">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="15192-148">WSFC クラスター内の可用性グループごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-148">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="15192-149">各行には、Windows Server フェールオーバー クラスタリング (WSFC) クラスターからの可用性グループ メタデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="15192-149">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="15192-150">**列名:** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="15192-150">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="15192-151">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="15192-151">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="15192-152">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のローカル インスタンスで可用性レプリカを保持する可用性グループごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-152">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15192-153">各行には、特定の可用性グループの正常性を定義する状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="15192-153">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="15192-154">**列名:** group_id、primary_replica、primary_recovery_health、primary_recovery_health_desc、secondary_recovery_health、secondary_recovery_health_desc、synchronization_health、synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="15192-154">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  
##  <a name="monitoring-availability-replicas"></a><a name="AvReplicas"></a><span data-ttu-id="15192-155">可用性レプリカの監視</span><span class="sxs-lookup"><span data-stu-id="15192-155">Monitoring Availability Replicas</span></span>  
 <span data-ttu-id="15192-156">可用性レプリカを監視するには、次のビューとシステム関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="15192-156">To monitor availability replicas, use the following views and system function:</span></span>  
  
 [<span data-ttu-id="15192-157">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="15192-157">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 <span data-ttu-id="15192-158">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスが可用性レプリカをホストしている各可用性グループ内の可用性レプリカごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-158">Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span>  
  
 <span data-ttu-id="15192-159">**列名:** replica_id、group_id、replica_metadata_id、replica_server_name、owner_sid、endpoint_url、availability_mode、availability_mode_desc、failover_mode、failover_mode_desc、session_timeout、primary_role_allow_connections、primary_role_allow_connections_desc、secondary_role_allow_connections、secondary_role_allow_connections_desc、create_date、modify_date、backup_priority、read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="15192-159">**Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span></span>  
  
 [<span data-ttu-id="15192-160">sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="15192-160">sys.availability_read_only_routing_lists</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 <span data-ttu-id="15192-161">WSFC フェールオーバー クラスター内の AlwaysOn 可用性グループにある各可用性レプリカの読み取り専用ルーティング リストに対する行を返します。</span><span class="sxs-lookup"><span data-stu-id="15192-161">Returns a row for the read only routing list of each availability replica in an AlwaysOn availability group in the WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="15192-162">**列名:** replica_id、routing_priority、read_only_replica_id</span><span class="sxs-lookup"><span data-stu-id="15192-162">**Column names:** replica_id, routing_priority, read_only_replica_id</span></span>  
  
 [<span data-ttu-id="15192-163">可用性レプリカの監視</span><span class="sxs-lookup"><span data-stu-id="15192-163">sys.dm_hadr_availability_replica_cluster_nodes</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 <span data-ttu-id="15192-164">Windows Server フェールオーバー クラスタリング (WSFC) クラスター内の AlwaysOn 可用性グループの可用性レプリカ (結合状態に関係なく) ごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-164">Returns a row for every availability replica (regardless of join state) of the AlwaysOn availability groups in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="15192-165">**列名:** group_name、replica_server_name、node_name</span><span class="sxs-lookup"><span data-stu-id="15192-165">**Column names:** group_name, replica_server_name, node_name</span></span>  
  
 [<span data-ttu-id="15192-166">sys.dm_hadr_availability_replica_cluster_nodes</span><span class="sxs-lookup"><span data-stu-id="15192-166">sys.dm_hadr_availability_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 <span data-ttu-id="15192-167">Windows Server フェールオーバー クラスタリング (WSFC) クラスター内のすべての AlwaysOn 可用性グループ (レプリカの場所に関係なく) のレプリカ (結合状態に関係なく) ごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-167">Returns a row for each replica (regardless of join state) of all AlwaysOn availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="15192-168">**列名:** replica_id、replica_server_name、group_id、join_state、join_state_desc</span><span class="sxs-lookup"><span data-stu-id="15192-168">**Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span></span>  
  
 [<span data-ttu-id="15192-169">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="15192-169">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 <span data-ttu-id="15192-170">各ローカル可用性レプリカの状態を示す 1 行のデータと、同じ可用性グループに含まれるリモート可用性グループごとの 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-170">Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.</span></span>  
  
 <span data-ttu-id="15192-171">**列名:** replica_id、group_id、is_local、role、role_desc、operational_state、operational_state_desc、connected_state、connected_state_desc、recovery_health、recovery_health_desc、synchronization_health、synchronization_health_desc、last_connect_error_number、last_connect_error_description、last_connect_error_timestamp</span><span class="sxs-lookup"><span data-stu-id="15192-171">**Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp</span></span>  
  
 [<span data-ttu-id="15192-172">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="15192-172">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 <span data-ttu-id="15192-173">現在のレプリカが推奨されるバックアップ レプリカであるかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="15192-173">Determines whether the current replica is the preferred backup replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15192-174">可用性レプリカのパフォーマンス カウンター ( **SQLServer:可用性レプリカ**  パフォーマンス オブジェクト) の詳細については、「 [SQL Server、可用性レプリカ](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15192-174">For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="monitoring-availability-databases"></a><a name="AvDbs"></a><span data-ttu-id="15192-175">可用性データベースの監視</span><span class="sxs-lookup"><span data-stu-id="15192-175">Monitoring Availability Databases</span></span>  
 <span data-ttu-id="15192-176">可用性データベースを監視するには、次のビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="15192-176">To monitor availability databases, use the following views:</span></span>  
  
 [<span data-ttu-id="15192-177">可用性データベースの監視</span><span class="sxs-lookup"><span data-stu-id="15192-177">sys.availability_databases_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
 <span data-ttu-id="15192-178">クラスターのすべての AlwaysOn 可用性グループに含まれる SQL Server インスタンス上のデータベースごとに、1 行のデータを格納します。ローカル コピー データベースが可用性グループに参加しているかどうかは問いません。</span><span class="sxs-lookup"><span data-stu-id="15192-178">Contains one row for each database on the instance of SQL Server that are part of all AlwaysOn Availability Groups in the cluster, regardless of whether the local copy database has been joined to the availability group yet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15192-179">データベースを可用性グループに追加すると、プライマリ データベースは自動的にそのグループに参加します。</span><span class="sxs-lookup"><span data-stu-id="15192-179">When a database is added to an availability group, the primary database is automatically joined to the group.</span></span> <span data-ttu-id="15192-180">セカンダリ データベースを可用性グループに参加させるには、各セカンダリ レプリカでそのデータベースを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15192-180">Secondary databases must be prepared on each secondary replica before they can be joined to the availability group.</span></span>  
  
 <span data-ttu-id="15192-181">**列名:** group_id、group_database_id、database_name</span><span class="sxs-lookup"><span data-stu-id="15192-181">**Column names:** group_id, group_database_id, database_name</span></span>  
  
 [<span data-ttu-id="15192-182">sys.databases</span><span class="sxs-lookup"><span data-stu-id="15192-182">sys.databases</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
 <span data-ttu-id="15192-183">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスに、データベースごとに 1 行のデータを保持します。</span><span class="sxs-lookup"><span data-stu-id="15192-183">Contains one row per database in the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15192-184">データベースが可用性レプリカに属している場合は、そのデータベースの行に、レプリカの GUID と、その可用性グループ内のデータベースの一意識別子が表示されます。</span><span class="sxs-lookup"><span data-stu-id="15192-184">If a database belongs to an availability replica, the row for that database displays the GUID of the replica and the unique identifier of the database within its availability group.</span></span>  
  
 <span data-ttu-id="15192-185">\*\* [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 列名:\*\* replica_id、group_database_id</span><span class="sxs-lookup"><span data-stu-id="15192-185">**[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] column names:** replica_id, group_database_id</span></span>  
  
 [<span data-ttu-id="15192-186">sys.dm_hadr_auto_page_repair</span><span class="sxs-lookup"><span data-stu-id="15192-186">sys.dm_hadr_auto_page_repair</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
 <span data-ttu-id="15192-187">サーバー インスタンスで任意の可用性グループに対してホストされている可用性レプリカの可用性データベースに対するページの自動修復の試行ごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-187">Returns a row for every automatic page-repair attempt on any availability database on an availability replica that is hosted for any availability group by the server instance.</span></span> <span data-ttu-id="15192-188">このビューには、特定のプライマリまたはセカンダリ データベースに対して最近試行されたページの自動修復に対応する行が含まれます (データベースあたり最大 100 行)。</span><span class="sxs-lookup"><span data-stu-id="15192-188">This view contains rows for the latest automatic page-repair attempts on a given primary or secondary database, with a maximum of 100 rows per database.</span></span> <span data-ttu-id="15192-189">データベースあたりの最大行数に達すると、その後に試行されたページの自動修復の行によって、既存のエントリが置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="15192-189">As soon as a database reaches the maximum, the row for its next automatic page-repair attempt replaces one of the existing entries.</span></span>  
  
 <span data-ttu-id="15192-190">**列名:** database_id、file_id、page_id、error_type、page_status、modification_time</span><span class="sxs-lookup"><span data-stu-id="15192-190">**Column names:** database_id, file_id, page_id, error_type, page_status, modification_time</span></span>  
  
 [<span data-ttu-id="15192-191">sys.dm_hadr_database_replica_states</span><span class="sxs-lookup"><span data-stu-id="15192-191">sys.dm_hadr_database_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
 <span data-ttu-id="15192-192">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスが可用性レプリカをホストしている任意の可用性グループに参加しているデータベースごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-192">Returns a row for each database that is participating in any availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is hosting an availability replica.</span></span>  
  
 <span data-ttu-id="15192-193">**列名:** database_id、group_id、replica_id、group_database_id、is_local、synchronization_state、synchronization_state_desc、is_commit_participant、synchronization_health、synchronization_health_desc、database_state、database_state_desc、is_suspended、suspend_reason、suspend_reason_desc、recovery_lsn、truncation_lsn、last_sent_lsn、last_sent_time、last_received_lsn、last_received_time、last_hardened_lsn、last_hardened_time、last_redone_lsn、last_redone_time、log_send_queue_size、log_send_rate、redo_queue_size、redo_rate、filestream_send_rate、end_of_log_lsn、last_commit_lsn、last_commit_time、low_water_mark_for_ghosts</span><span class="sxs-lookup"><span data-stu-id="15192-193">**Column names:** database_id, group_id, replica_id, group_database_id, is_local, synchronization_state, synchronization_state_desc, is_commit_participant, synchronization_health, synchronization_health_desc, database_state, database_state_desc, is_suspended, suspend_reason, suspend_reason_desc, recovery_lsn, truncation_lsn, last_sent_lsn, last_sent_time, last_received_lsn, last_received_time, last_hardened_lsn, last_hardened_time, last_redone_lsn, last_redone_time, log_send_queue_size, log_send_rate, redo_queue_size, redo_rate, filestream_send_rate, end_of_log_lsn, last_commit_lsn, last_commit_time, low_water_mark_for_ghosts</span></span>  
  
 [<span data-ttu-id="15192-194">sys.availability_databases_cluster</span><span class="sxs-lookup"><span data-stu-id="15192-194">sys.dm_hadr_database_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
 <span data-ttu-id="15192-195">Windows Server フェールオーバー クラスタリング (WSFC) クラスター上の各可用性グループに含まれる可用性データベースの正常性を把握するための情報を含む行を返します。</span><span class="sxs-lookup"><span data-stu-id="15192-195">Returns a row containing information intended to provide you with insight into the health of the availability databases in each availability group on the Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="15192-196">この動的管理ビューは、フェールオーバーを計画する際やフェールオーバーに応答する際のほか、特定のプライマリ データベースでログの切り捨てを維持している可用性グループ内のセカンダリ レプリカを検出する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="15192-196">This dynamic management view is useful when planning or responding to a failover or for discovering which secondary replica in an availability group is holding up log truncation on a given primary database.</span></span>  
  
 <span data-ttu-id="15192-197">**列名:** replica_id、group_database_id、database_name、is_failover_ready、is_pending_secondary_suspend、is_database_joined、recovery_lsn、truncation_lsn</span><span class="sxs-lookup"><span data-stu-id="15192-197">**Column names:** replica_id, group_database_id, database_name, is_failover_ready, is_pending_secondary_suspend, is_database_joined, recovery_lsn, truncation_lsn</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15192-198">プライマリ レプリカの場所は、可用性グループに対して権限を持つソースです。</span><span class="sxs-lookup"><span data-stu-id="15192-198">The primary replica location is the authoritative source for an availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15192-199">可用性データベースの [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] パフォーマンス カウンター ( **SQLServer:Database Replica** パフォーマンス オブジェクト) の詳細については、「 [SQL Server、データベース レプリカ](../../../relational-databases/performance-monitor/sql-server-database-replica.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15192-199">For information about the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] performance counters for availability databases (the **SQLServer:Database Replica** performance object), see [SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md).</span></span> <span data-ttu-id="15192-200">また、可用性データベースのトランザクションログの利用状況を監視するには、 **SQLServer: databases**パフォーマンスオブジェクトの次のカウンターを使用します。これは、 **Log Flush Write Time (ms)**、 **log Flush/Sec**、 **log pool Cache ミス/sec**、Log Pool **Disk Reads**/sec、 **log pool Requests/sec**です。詳細については、「 [SQL Server、Databases オブジェクト](../../../relational-databases/performance-monitor/sql-server-databases-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15192-200">Also, to monitor transaction-log activity on availability databases, use the following counters of the **SQLServer:Databases** performance object: **Log Flush Write Time (ms)**, **Log Flushes/sec**, **Log Pool Cache Misses/sec**, **Log Pool Disk Reads/sec**, and **Log Pool Requests/sec**. For more information, see [SQL Server, Databases Object](../../../relational-databases/performance-monitor/sql-server-databases-object.md).</span></span>  
  
##  <a name="monitoring-availability-group-listeners"></a><a name="AGlisteners"></a><span data-ttu-id="15192-201">可用性グループリスナーの監視</span><span class="sxs-lookup"><span data-stu-id="15192-201">Monitoring Availability Group Listeners</span></span>  
 <span data-ttu-id="15192-202">WSFC クラスターのサブネット上の可用性グループ リスナーを監視するには、次のビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="15192-202">To monitor the availability group listeners on subnets of the WSFC cluster, use the following views:</span></span>  
  
 [<span data-ttu-id="15192-203">sys.availability_group_listener_ip_addresses</span><span class="sxs-lookup"><span data-stu-id="15192-203">sys.availability_group_listener_ip_addresses</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 <span data-ttu-id="15192-204">可用性グループ リスナーに対してオンラインになっている準拠仮想 IP アドレスごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-204">Returns a row for every conformant virtual IP address that is currently online for an availability group listener.</span></span>  
  
 <span data-ttu-id="15192-205">**列名:** listener_id、ip_address、ip_subnet_mask、is_dhcp、network_subnet_ip、network_subnet_prefix_length、network_subnet_ipv4_mask、state, state_desc</span><span class="sxs-lookup"><span data-stu-id="15192-205">**Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span></span>  
  
 [<span data-ttu-id="15192-206">sys.availability_group_listeners</span><span class="sxs-lookup"><span data-stu-id="15192-206">sys.availability_group_listeners</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 <span data-ttu-id="15192-207">特定の可用性グループについて、可用性グループにネットワーク名が関連付けられていないことを示すゼロ行を返すか、WSFC クラスター内の可用性グループ リスナーの構成ごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="15192-207">For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.</span></span>  
  
 <span data-ttu-id="15192-208">**列名** : group_id、listener_id、dns_name、port、is_conformant、ip_configuration_string_from_cluster</span><span class="sxs-lookup"><span data-stu-id="15192-208">**Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span></span>  
  
 [<span data-ttu-id="15192-209">sys.dm_tcp_listener_states</span><span class="sxs-lookup"><span data-stu-id="15192-209">sys.dm_tcp_listener_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 <span data-ttu-id="15192-210">各 TCP リスナーの動的状態情報を含む行を返します。</span><span class="sxs-lookup"><span data-stu-id="15192-210">Returns a row containing dynamic-state information for each TCP listener.</span></span>  
  
 <span data-ttu-id="15192-211">**列名** : listener_id、ip_address、is_ipv4、port、type、type_desc、state、state_desc、start_time</span><span class="sxs-lookup"><span data-stu-id="15192-211">**Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span></span>  
  
 <span data-ttu-id="15192-212">**主キー:** listener_id</span><span class="sxs-lookup"><span data-stu-id="15192-212">**Primary key:** listener_id</span></span>  
  
 <span data-ttu-id="15192-213">可用性グループ リスナーの詳細については、「[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15192-213">For information about availability group listeners, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="15192-214">関連タスク</span><span class="sxs-lookup"><span data-stu-id="15192-214">Related Tasks</span></span>  
 <span data-ttu-id="15192-215">**AlwaysOn 可用性グループの監視タスク:**</span><span class="sxs-lookup"><span data-stu-id="15192-215">**AlwaysOn Availability Groups monitoring tasks:**</span></span>  
  
-   <span data-ttu-id="15192-216">[[オブジェクト エクスプローラーの詳細] を使用した可用性グループの監視 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)</span><span class="sxs-lookup"><span data-stu-id="15192-216">[Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)</span></span>  
  
-   [<span data-ttu-id="15192-217">可用性グループのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-217">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="15192-218">可用性レプリカのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-218">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="15192-219">可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-219">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
 <span data-ttu-id="15192-220">**AlwaysOn 可用性グループの監視に関するリファレンス (Transact-SQL) :**</span><span class="sxs-lookup"><span data-stu-id="15192-220">**AlwaysOn Availability Groups monitoring reference (Transact-SQL):**</span></span>  
  
-   [<span data-ttu-id="15192-221">SERVERPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-221">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
-   [<span data-ttu-id="15192-222">sys.availability_group_listener_ip_addresses &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-222">sys.availability_group_listener_ip_addresses &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
  
-   [<span data-ttu-id="15192-223">sys.availability_group_listeners &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-223">sys.availability_group_listeners &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
  
-   [<span data-ttu-id="15192-224">sys.availability_databases_cluster &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-224">sys.availability_databases_cluster &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
  
-   [<span data-ttu-id="15192-225">sys.availability_groups &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-225">sys.availability_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
  
-   [<span data-ttu-id="15192-226">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-226">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   [<span data-ttu-id="15192-227">sys.availability_replicas &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-227">sys.availability_replicas &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
  
-   [<span data-ttu-id="15192-228">sys.dm_hadr_availability_replica_cluster_nodes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-228">sys.dm_hadr_availability_replica_cluster_nodes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
  
-   [<span data-ttu-id="15192-229">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-229">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="15192-230">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-230">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
-   [<span data-ttu-id="15192-231">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-231">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
  
-   [<span data-ttu-id="15192-232">sys.dm_hadr_availability_group_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-232">sys.dm_hadr_availability_group_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
  
-   [<span data-ttu-id="15192-233">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-233">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="15192-234">sys.dm_hadr_availability_group_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-234">sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
  
-   [<span data-ttu-id="15192-235">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-235">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [<span data-ttu-id="15192-236">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-236">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="15192-237">sys.dm_hadr_cluster &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-237">sys.dm_hadr_cluster &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
  
-   [<span data-ttu-id="15192-238">sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-238">sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
  
-   [<span data-ttu-id="15192-239">sys.dm_hadr_cluster_networks &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-239">sys.dm_hadr_cluster_networks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
  
-   [<span data-ttu-id="15192-240">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-240">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="15192-241">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-241">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [<span data-ttu-id="15192-242">sys.dm_hadr_instance_node_map &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-242">sys.dm_hadr_instance_node_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
  
-   [<span data-ttu-id="15192-243">sys.dm_hadr_name_id_map &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-243">sys.dm_hadr_name_id_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
  
-   [<span data-ttu-id="15192-244">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-244">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
-   [<span data-ttu-id="15192-245">sys.dm_tcp_listener_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-245">sys.dm_tcp_listener_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
  
-   [<span data-ttu-id="15192-246">sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-246">sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 <span data-ttu-id="15192-247">**AlwaysOn パフォーマンス カウンター:**</span><span class="sxs-lookup"><span data-stu-id="15192-247">**AlwaysOn performance counters:**</span></span>  
  
-   [<span data-ttu-id="15192-248">SQL Server、可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="15192-248">SQL Server, Availability Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)  
  
-   [<span data-ttu-id="15192-249">SQL Server、データベース レプリカ</span><span class="sxs-lookup"><span data-stu-id="15192-249">SQL Server, Database Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-database-replica.md)  
  
-   [<span data-ttu-id="15192-250">SQL Server, Databases Object</span><span class="sxs-lookup"><span data-stu-id="15192-250">SQL Server, Databases Object</span></span>](../../../relational-databases/performance-monitor/sql-server-databases-object.md)  
  
 <span data-ttu-id="15192-251">**AlwaysOn 可用性グループのポリシー ベースの管理**</span><span class="sxs-lookup"><span data-stu-id="15192-251">**Policy-based management for AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="15192-252">AlwaysOn ポリシーを使用して、可用性グループ &#40;SQL Server の正常性を表示&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-252">Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="15192-253">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-253">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="15192-254">参照</span><span class="sxs-lookup"><span data-stu-id="15192-254">See Also</span></span>  
 <span data-ttu-id="15192-255">[AlwaysOn 可用性グループ (SQL Server)](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15192-255">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="15192-256">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15192-256">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="15192-257">可用性グループの監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="15192-257">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
