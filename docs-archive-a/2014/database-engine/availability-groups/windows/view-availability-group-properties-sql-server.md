---
title: 可用性グループのプロパティの表示 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server]
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7d1f57a9bd29b6c65160ec9a163bc77dfca48b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634639"
---
# <a name="view-availability-group-properties-sql-server"></a><span data-ttu-id="853ef-102">可用性グループのプロパティの表示 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="853ef-102">View Availability Group Properties (SQL Server)</span></span>
  <span data-ttu-id="853ef-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)] または [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して、AlwaysOn 可用性グループの可用性グループのプロパティを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="853ef-103">This topic describes how to view the properties of an availability group for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="853ef-104">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="853ef-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="853ef-105">**可用性グループのプロパティを表示および変更するには**</span><span class="sxs-lookup"><span data-stu-id="853ef-105">**To view and change the properties an availability group**</span></span>  
  
1.  <span data-ttu-id="853ef-106">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="853ef-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="853ef-107">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="853ef-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="853ef-108">表示するプロパティを持つ可用性グループを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="853ef-108">Right-click the availability group whose properties you want to view, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="853ef-109">**[可用性グループのプロパティ]** ダイアログ ボックスで、**[全般]** および **[バックアップの設定]** ページを使用して、選択された可用性グループのプロパティを表示し、必要に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="853ef-109">In the **Availability Group Properties** dialog box, use the **General** and **Backup Preferences** pages to view and, in some cases, change properties of the selected availability group.</span></span> <span data-ttu-id="853ef-110">詳細については、「[[可用性グループのプロパティ]: [新しい可用性グループ] &#40;[全般] ページ&#41;](availability-group-properties-new-availability-group-general-page.md)」、「[[可用性グループのプロパティ]: [新しい可用性グループ] &#40;[バックアップの設定] ページ&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="853ef-110">For more information, see [Availability Group Properties and New Availability Group &#40;General Page&#41;](availability-group-properties-new-availability-group-general-page.md) and [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
     <span data-ttu-id="853ef-111">**[権限]** ページを使用して、可用性グループに関連付けられている現在のログイン、ロール、および明示的な権限を表示できます。</span><span class="sxs-lookup"><span data-stu-id="853ef-111">Use the **Permissions** page to view the current logins, roles, and explicit permissions associated with the availability group.</span></span> <span data-ttu-id="853ef-112">詳細については、「 [[権限] ページまたは [セキュリティ保護可能なリソース] ページ](../../../relational-databases/security/permissions-or-securables-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="853ef-112">For more information, see [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md).</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="853ef-113">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="853ef-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="853ef-114">**可用性グループのプロパティおよび状態を表示するには**</span><span class="sxs-lookup"><span data-stu-id="853ef-114">**To view the properties and state of an availability group**</span></span>  
  
 <span data-ttu-id="853ef-115">サーバー インスタンスが可用性レプリカをホストしている可用性グループのプロパティおよび状態を確認するには、次のビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="853ef-115">To query the properties and states of the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="853ef-116">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="853ef-116">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="853ef-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスが可用性レプリカをホストしている各可用性グループの行を返します。</span><span class="sxs-lookup"><span data-stu-id="853ef-117">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="853ef-118">各行には、可用性グループ メタデータのキャッシュされたコピーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="853ef-118">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="853ef-119">**列名:** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="853ef-119">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="853ef-120">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="853ef-120">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="853ef-121">WSFC クラスター内の可用性グループごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="853ef-121">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="853ef-122">各行には、Windows Server フェールオーバー クラスタリング (WSFC) クラスターからの可用性グループ メタデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="853ef-122">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="853ef-123">**列名:** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="853ef-123">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="853ef-124">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="853ef-124">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="853ef-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のローカル インスタンスで可用性レプリカを保持する可用性グループごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="853ef-125">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="853ef-126">各行には、特定の可用性グループの正常性を定義する状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="853ef-126">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="853ef-127">**列名:** group_id、primary_replica、primary_recovery_health、primary_recovery_health_desc、secondary_recovery_health、secondary_recovery_health_desc、synchronization_health、synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="853ef-127">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="853ef-128">関連タスク</span><span class="sxs-lookup"><span data-stu-id="853ef-128">Related Tasks</span></span>  
 <span data-ttu-id="853ef-129">**可用性グループに関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="853ef-129">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="853ef-130">可用性レプリカのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-130">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="853ef-131">可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-131">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="853ef-132">AlwaysOn 可用性グループ &#40;SQL Server での運用上の問題のための AlwaysOn ポリシー&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-132">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="853ef-133">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-133">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="853ef-134">可用性グループの監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-134">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="853ef-135">**既存の可用性グループを構成するには**</span><span class="sxs-lookup"><span data-stu-id="853ef-135">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="853ef-136">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-136">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="853ef-137">可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-137">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="853ef-138">可用性グループへのデータベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-138">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="853ef-139">可用性グループからのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-139">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="853ef-140">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-140">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="853ef-141">可用性グループ リスナーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-141">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="853ef-142">可用性グループからのプライマリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-142">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="853ef-143">可用性グループの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-143">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="853ef-144">**可用性グループを手動でフェールオーバーするには**</span><span class="sxs-lookup"><span data-stu-id="853ef-144">**To manually fail over an availability group**</span></span>  
  
-   [<span data-ttu-id="853ef-145">可用性グループの計画的な手動フェールオーバーの実行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-145">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="853ef-146">可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="853ef-147">参照</span><span class="sxs-lookup"><span data-stu-id="853ef-147">See Also</span></span>  
 <span data-ttu-id="853ef-148">&#40;&#41;AlwaysOn 可用性グループ[での運用上の問題に対する transact-sql &#40;AlwaysOn ポリシー](always-on-policies-for-operational-issues-always-on-availability.md) SQL Server&#41;SQL Server[可用性グループを監視](monitor-availability-groups-transact-sql.md)する[AlwaysOn 可用性グループ &#40;の概要](overview-of-always-on-availability-groups-sql-server.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="853ef-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)</span></span> 
  
  
