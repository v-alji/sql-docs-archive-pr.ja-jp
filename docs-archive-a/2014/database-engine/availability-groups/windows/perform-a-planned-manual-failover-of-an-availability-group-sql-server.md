---
title: 可用性グループの計画的な手動フェールオーバーの実行 (SQLServer) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c62942eaa8f4ab4472bca5c7123e5999eb069216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718746"
---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a><span data-ttu-id="c437f-102">可用性グループの計画的な手動フェールオーバーの実行 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c437f-102">Perform a Planned Manual Failover of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="c437f-103"> このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループ上でデータを失わずに手動フェールオーバー (*計画的な手動フェールオーバー*) を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c437f-103">This topic describes how to perform a manual failover without data loss (a *planned manual failover*) on an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c437f-104">可用性グループは、可用性レプリカのレベルでフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="c437f-104">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="c437f-105">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] フェールオーバーのような計画的な手動フェールオーバーでは、セカンダリ レプリカはプライマリ ロールに移行し、同時に、それまでのプライマリ レプリカはセカンダリ ロールに移行します。</span><span class="sxs-lookup"><span data-stu-id="c437f-105">A planned manual failover, like any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] failover, transitions a secondary replica to primary role and, concurrently, transitions the former primary replica to the secondary role.</span></span>  
  
 <span data-ttu-id="c437f-106">計画的な手動フェールオーバーは、プライマリ レプリカおよびターゲット セカンダリ レプリカが同期コミット モードで動作していて、現在同期されている場合にのみサポートされます。この場合、ターゲット セカンダリ レプリカ上の可用性グループに参加しているセカンダリ データベース内のすべてのデータが維持されます。</span><span class="sxs-lookup"><span data-stu-id="c437f-106">A planned manual failover, which is supported only when the primary replica and the target secondary replica are running in synchronous-commit mode and are currently synchronized, preserves all the data in the secondary databases that are joined to the availability group on the target secondary replica.</span></span> <span data-ttu-id="c437f-107">元のプライマリ レプリカがセカンダリ ロールに移行すると、そのデータベースはセカンダリ データベースになり、新しいプライマリ データベースとの同期が開始されます。</span><span class="sxs-lookup"><span data-stu-id="c437f-107">Once the former primary replica transitions to the secondary role, its databases become secondary databases and begin synchronizing with the new primary databases.</span></span> <span data-ttu-id="c437f-108">すべてが SYNCHRONIZED 状態に移行した後は、新しいセカンダリ レプリカが、将来の計画的な手動フェールオーバーのターゲットとして機能できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c437f-108">After they all transition into the SYNCHRONIZED state, the new secondary replica becomes eligible to serve as the target of a future planned manual failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c437f-109">セカンダリ レプリカとプライマリ レプリカの両方に対して自動フェールオーバー モードを構成し、セカンダリ レプリカを同期すると、自動フェールオーバーのターゲットとしても機能できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c437f-109">If the secondary and primary replicas are both configured for automatic failover mode, once the secondary replica is synchronized, it can also serve as the target for an automatic failover.</span></span> <span data-ttu-id="c437f-110">詳細については、「[可用性モード &#40;AlwaysOn 可用性グループ&#41;](availability-modes-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c437f-110">For more information, see [Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md).</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c437f-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="c437f-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c437f-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c437f-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c437f-113">フェールオーバー コマンドは、ターゲットのセカンダリ レプリカがコマンドを受け入れた直後に戻ります。</span><span class="sxs-lookup"><span data-stu-id="c437f-113">A failover command returns as soon as the target secondary replica has accepted the command.</span></span> <span data-ttu-id="c437f-114">ただし、データベースの復旧は、可用性グループがフェールオーバーを完了した後に非同期で行われます。</span><span class="sxs-lookup"><span data-stu-id="c437f-114">However, database recovery occurs asynchronously after the availability group has finished failing over.</span></span>  
  
-   <span data-ttu-id="c437f-115">フェールオーバー時に、可用性グループ内のデータベース間の一貫性は維持されません。</span><span class="sxs-lookup"><span data-stu-id="c437f-115">Cross-database consistency across databases within the availability group is not maintained on failover.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c437f-116">複数のデータベースにまたがるトランザクションおよび分散トランザクションは、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="c437f-116">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="c437f-117">詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c437f-117">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="c437f-118">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="c437f-118">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="c437f-119">ターゲットのセカンダリ レプリカとプライマリ レプリカは、両方とも同期コミット可用性モードで実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c437f-119">The target secondary replica and the primary replica must both be running in synchronous-commit availability mode.</span></span>  
  
-   <span data-ttu-id="c437f-120">ターゲットのセカンダリ レプリカは、現在プライマリ レプリカと同期されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c437f-120">The target secondary replica must currently be synchronized with the primary replica.</span></span> <span data-ttu-id="c437f-121">このためには、この可用性レプリカのすべてのセカンダリ データベースが可用性グループに参加している必要があり、対応するプライマリ データベースに同期されている必要があります (つまり、ローカル セカンダリ データベースは SYNCHRONIZED 状態である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="c437f-121">This requires that all the secondary databases on this secondary replica must have been joined to the availability group and be synchronized with their corresponding primary databases (that is, the local secondary databases must be SYNCHRONIZED).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="c437f-122">セカンダリ レプリカのフェールオーバーの準備状態を調べるには、[sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) 動的管理ビューで **is_failover_ready** 列をクエリするか、[AlwaysOn グループ ダッシュボード](use-the-always-on-dashboard-sql-server-management-studio.md)の **[フェールオーバーの準備]** 列を確認します。</span><span class="sxs-lookup"><span data-stu-id="c437f-122">To determine the failover readiness of an secondary replica, query the **is_failover_ready** column in the [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) dynamic management view, or look at the **Failover Readiness** column of the [AlwaysOn Group Dashboard](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="c437f-123">このタスクは、ターゲット セカンダリ レプリカ上でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c437f-123">This task is supported only on the target secondary replica.</span></span> <span data-ttu-id="c437f-124">ターゲット セカンダリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c437f-124">You must be connected to the server instance that hosts the target secondary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c437f-125">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c437f-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c437f-126">Permissions</span><span class="sxs-lookup"><span data-stu-id="c437f-126">Permissions</span></span>  
 <span data-ttu-id="c437f-127">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c437f-127">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c437f-128">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c437f-128">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c437f-129">**可用性グループを手動でフェールオーバーするには**</span><span class="sxs-lookup"><span data-stu-id="c437f-129">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="c437f-130">オブジェクト エクスプローラーで、フェールオーバーを行う可用性グループのセカンダリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c437f-130">In Object Explorer, connect to a server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="c437f-131">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="c437f-131">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="c437f-132">フェールオーバーする [可用性グループ] ノードを右クリックし、 **[フェールオーバー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c437f-132">Right-click the availability group to be failed over, and select the **Failover** command.</span></span>  
  
4.  <span data-ttu-id="c437f-133">可用性グループのフェールオーバー ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="c437f-133">This launches the Failover Availability Group Wizard.</span></span> <span data-ttu-id="c437f-134">詳細については、「[可用性グループのフェールオーバー ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c437f-134">For more information, see [Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c437f-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c437f-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="c437f-136">**可用性グループを手動でフェールオーバーするには**</span><span class="sxs-lookup"><span data-stu-id="c437f-136">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="c437f-137">ターゲット セカンダリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c437f-137">Connect to the server instance that hosts the target secondary replica.</span></span>  
  
2.  <span data-ttu-id="c437f-138">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="c437f-138">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="c437f-139">ALTER AVAILABILITY GROUP *group_name* FAILOVER</span><span class="sxs-lookup"><span data-stu-id="c437f-139">ALTER AVAILABILITY GROUP *group_name* FAILOVER</span></span>  
  
     <span data-ttu-id="c437f-140">*group_name* は可用性グループの名前です。</span><span class="sxs-lookup"><span data-stu-id="c437f-140">where *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="c437f-141">次の例では、 *Myag*可用性グループを接続されたセカンダリレプリカに手動でフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="c437f-141">The following example manually fails over the *MyAg* availability group to the connected secondary replica.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="c437f-142">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="c437f-142">Using PowerShell</span></span>  
 <span data-ttu-id="c437f-143">**可用性グループを手動でフェールオーバーするには**</span><span class="sxs-lookup"><span data-stu-id="c437f-143">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="c437f-144">ディレクトリ変更コマンド (`cd`) を使用して、ターゲット セカンダリ レプリカをホストするサーバー インスタンスに移動します。</span><span class="sxs-lookup"><span data-stu-id="c437f-144">Change directory (`cd`) to the server instance that hosts the target secondary replica.</span></span>  
  
2.  <span data-ttu-id="c437f-145">`Switch-SqlAvailabilityGroup` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="c437f-145">Use the `Switch-SqlAvailabilityGroup` cmdlet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c437f-146">コマンドレットの構文を表示するには、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="c437f-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="c437f-147">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c437f-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
     <span data-ttu-id="c437f-148">次の例では、指定されたパスのセカンダリレプリカに*Myag*可用性グループを手動でフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="c437f-148">The following example manually fails over the *MyAg* availability group to the secondary replica with the specified path.</span></span>  
  
    ```powershell
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 <span data-ttu-id="c437f-149">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="c437f-149">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="c437f-150">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c437f-150">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="c437f-151">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="c437f-151">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="follow-up-after-manually-failing-over-an-availability-group"></a><a name="FollowUp"></a> <span data-ttu-id="c437f-152">補足情報: 可用性グループの手動フェールオーバー後</span><span class="sxs-lookup"><span data-stu-id="c437f-152">Follow Up: After Manually Failing Over an Availability Group</span></span>  
 <span data-ttu-id="c437f-153">可用性グループの [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] の外側でフェールオーバーした場合、WSFC ノードのクォーラム投票を調整して新しい可用性グループの構成を反映します。</span><span class="sxs-lookup"><span data-stu-id="c437f-153">If you failed over outside of the [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] of the availability group, adjust the quorum votes of the WSFC nodes to reflect your new availability group configuration.</span></span> <span data-ttu-id="c437f-154">詳細については、「 [Windows Server フェールオーバークラスタリング &#40;WSFC&#41; SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c437f-154">For more information, see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c437f-155">参照</span><span class="sxs-lookup"><span data-stu-id="c437f-155">See Also</span></span>  
 <span data-ttu-id="c437f-156">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c437f-156">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="c437f-157">[フェールオーバーとフェールオーバーモード &#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="c437f-157">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="c437f-158">可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c437f-158">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
