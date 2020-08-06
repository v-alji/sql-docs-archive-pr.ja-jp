---
title: 可用性グループ リスナーのプロパティの表示 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistenerproperties.general.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
ms.assetid: aca0d016-3228-40b8-bdc3-285ed6d9b280
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef7fe316394a030350ceb12a0d1b8e2d48ee1d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632113"
---
# <a name="view-availability-group-listener-properties-sql-server"></a><span data-ttu-id="76ca3-102">可用性グループ リスナーのプロパティの表示 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="76ca3-102">View Availability Group Listener Properties (SQL Server)</span></span>
  <span data-ttu-id="76ca3-103">このトピックでは、 *で* または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して、AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] 可用性グループ リスナー [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のプロパティを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-103">This topic describes how to view the properties of an AlwaysOn *availability group listener* by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="76ca3-104">**リスナーのプロパティを表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="76ca3-104">**To view listener properties, using:**</span></span>  
  
     [<span data-ttu-id="76ca3-105">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="76ca3-105">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="76ca3-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="76ca3-106">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="76ca3-107">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="76ca3-107">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="76ca3-108">**リスナーのプロパティを表示するには**</span><span class="sxs-lookup"><span data-stu-id="76ca3-108">**To view listener properties**</span></span>  
  
1.  <span data-ttu-id="76ca3-109">オブジェクト エクスプローラーで、リスナーを表示する可用性グループの任意の可用性レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-109">In Object Explorer, connect to a server instance that hosts any availability replica of the availability group whose listener you want to view.</span></span> <span data-ttu-id="76ca3-110">サーバー名をクリックし、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-110">Click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="76ca3-111">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-111">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="76ca3-112">可用性グループのノード、 **[可用性グループ リスナー]** ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-112">Expand the node of the availability group, and expand the **Availability Groups Listeners** node.</span></span>  
  
4.  <span data-ttu-id="76ca3-113">表示するリスナーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ca3-113">Right-click the listener that you want to view, and select the **Properties** command.</span></span>  
  
5.  <span data-ttu-id="76ca3-114">これにより、 **[可用性グループ リスナーのプロパティ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="76ca3-114">This opens the **Availability Group Listener Properties** dialog box.</span></span> <span data-ttu-id="76ca3-115">詳細については、このトピックの「 [[可用性グループ リスナーのプロパティ] (ダイアログ ボックス)](#AgListenerPropertiesDialog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76ca3-115">For more information, see [Availability Group Listener Properties (Dialog Box)](#AgListenerPropertiesDialog), later in this topic.</span></span>  
  
###  <a name="availability-group-listener-properties-dialog-box"></a><a name="AgListenerPropertiesDialog"></a> <span data-ttu-id="76ca3-116">[可用性グループ リスナーのプロパティ] (ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="76ca3-116">Availability Group Listener Properties (Dialog Box)</span></span>  
 <span data-ttu-id="76ca3-117">**[リスナーの DNS 名]**</span><span class="sxs-lookup"><span data-stu-id="76ca3-117">**Listener DNS Name**</span></span>  
 <span data-ttu-id="76ca3-118">可用性グループ リスナーのネットワーク名。</span><span class="sxs-lookup"><span data-stu-id="76ca3-118">The network name of the availability group listener.</span></span>  
  
 <span data-ttu-id="76ca3-119">**[ポート]**</span><span class="sxs-lookup"><span data-stu-id="76ca3-119">**Port**</span></span>  
 <span data-ttu-id="76ca3-120">このリスナーで使用される TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="76ca3-120">The TCP port used by this listener.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76ca3-121">プライマリ レプリカに接続している場合は、このフィールドを使用してリスナーのポート番号を変更できます。</span><span class="sxs-lookup"><span data-stu-id="76ca3-121">If you are connected the primary replica, you can use this field to modify the port number of the listener.</span></span> <span data-ttu-id="76ca3-122">それには、可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="76ca3-122">This requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="76ca3-123">**[ネットワーク モード]**</span><span class="sxs-lookup"><span data-stu-id="76ca3-123">**Network Mode**</span></span>  
 <span data-ttu-id="76ca3-124">リスナーで使用される TCP プロトコルを指定します。次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="76ca3-124">Indicates the TCP protocol used by the listener, one of:</span></span>  
  
 <span data-ttu-id="76ca3-125">**[DHCP]**</span><span class="sxs-lookup"><span data-stu-id="76ca3-125">**DHCP**</span></span>  
 <span data-ttu-id="76ca3-126">リスナーは、動的ホスト構成プロトコル (DHCP) を実行しているサーバーによって割り当てられる動的 IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-126">The listener uses an dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).</span></span>  
  
 <span data-ttu-id="76ca3-127">**[静的 IP]**</span><span class="sxs-lookup"><span data-stu-id="76ca3-127">**Static IP**</span></span>  
 <span data-ttu-id="76ca3-128">リスナーは、1 つまたは複数の静的 IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-128">The listener uses one or more Static IP addresses.</span></span> <span data-ttu-id="76ca3-129">別のサブネットにアクセスするには、可用性グループ リスナーは静的 IP アドレスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76ca3-129">To access the different subnets, an availability group listener must use static IP addresses.</span></span>  
  
 <span data-ttu-id="76ca3-130">グリッドには、リスナーがリッスンする各サブネットと、そのサブネットに関連付けられた IP アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="76ca3-130">The grid displays each of the subnets on which the listener listens and the IP address associated with that subnet.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="76ca3-131">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="76ca3-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="76ca3-132">**リスナーのプロパティを表示するには**</span><span class="sxs-lookup"><span data-stu-id="76ca3-132">**To view listener properties**</span></span>  
  
 <span data-ttu-id="76ca3-133">可用性グループ リスナーを監視するには、次のビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-133">To monitor the availability group listeners, use the following views:</span></span>  
  
 [<span data-ttu-id="76ca3-134">sys.availability_group_listener_ip_addresses</span><span class="sxs-lookup"><span data-stu-id="76ca3-134">sys.availability_group_listener_ip_addresses</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 <span data-ttu-id="76ca3-135">可用性グループ リスナーに対してオンラインになっている準拠仮想 IP アドレスごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-135">Returns a row for every conformant virtual IP address that is currently online for an availability group listener.</span></span>  
  
 <span data-ttu-id="76ca3-136">**列名:** listener_id、ip_address、ip_subnet_mask、is_dhcp、network_subnet_ip、network_subnet_prefix_length、network_subnet_ipv4_mask、state, state_desc</span><span class="sxs-lookup"><span data-stu-id="76ca3-136">**Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span></span>  
  
 [<span data-ttu-id="76ca3-137">sys.availability_group_listeners</span><span class="sxs-lookup"><span data-stu-id="76ca3-137">sys.availability_group_listeners</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 <span data-ttu-id="76ca3-138">特定の可用性グループについて、可用性グループにネットワーク名が関連付けられていないことを示すゼロ行を返すか、WSFC クラスター内の可用性グループ リスナーの構成ごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-138">For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.</span></span>  
  
 <span data-ttu-id="76ca3-139">**列名** : group_id、listener_id、dns_name、port、is_conformant、ip_configuration_string_from_cluster</span><span class="sxs-lookup"><span data-stu-id="76ca3-139">**Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span></span>  
  
 [<span data-ttu-id="76ca3-140">sys.dm_tcp_listener_states</span><span class="sxs-lookup"><span data-stu-id="76ca3-140">sys.dm_tcp_listener_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 <span data-ttu-id="76ca3-141">各 TCP リスナーの動的状態情報を含む行を返します。</span><span class="sxs-lookup"><span data-stu-id="76ca3-141">Returns a row containing dynamic-state information for each TCP listener.</span></span>  
  
 <span data-ttu-id="76ca3-142">**列名** : listener_id、ip_address、is_ipv4、port、type、type_desc、state、state_desc、start_time</span><span class="sxs-lookup"><span data-stu-id="76ca3-142">**Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76ca3-143">[!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用した [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 環境の監視の詳細については、「[可用性グループの監視 &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76ca3-143">For more information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] to monitor your [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] environment, see [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="76ca3-144">関連タスク</span><span class="sxs-lookup"><span data-stu-id="76ca3-144">Related Tasks</span></span>  
  
-   [<span data-ttu-id="76ca3-145">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="76ca3-145">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="76ca3-146">可用性グループ リスナーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="76ca3-146">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="76ca3-147">参照</span><span class="sxs-lookup"><span data-stu-id="76ca3-147">See Also</span></span>  
 <span data-ttu-id="76ca3-148">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="76ca3-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="76ca3-149">[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="76ca3-149">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="76ca3-150">可用性グループの監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="76ca3-150">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
  
