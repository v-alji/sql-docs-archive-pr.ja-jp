---
title: 可用性グループへのセカンダリ レプリカの追加 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 6669dcce-85f9-495f-aadf-7f62cff4a9da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 498103a781641c72e166c6b11663f5248ae5ccfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632718"
---
# <a name="add-a-secondary-replica-to-an-availability-group-sql-server"></a><span data-ttu-id="73915-102">可用性グループへのセカンダリ レプリカの追加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="73915-102">Add a Secondary Replica to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="73915-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73915-103">This topic describes how to add a secondary replica to an existing AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="73915-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="73915-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="73915-105">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="73915-105">Prerequisites and Restrictions</span></span>](#PrerequisitesRestrictions)  
  
     [<span data-ttu-id="73915-106">Security</span><span class="sxs-lookup"><span data-stu-id="73915-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="73915-107">**レプリカを追加するには (次を使用):**</span><span class="sxs-lookup"><span data-stu-id="73915-107">**To add a replica, using:**</span></span>  
  
     [<span data-ttu-id="73915-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="73915-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="73915-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="73915-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="73915-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="73915-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="73915-111">**補足情報:**  [セカンダリ レプリカを追加した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="73915-111">**Follow Up:**  [After Adding a Secondary Replica](#FollowUp)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="73915-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="73915-112">Before You Begin</span></span>  
 <span data-ttu-id="73915-113">可用性グループを初めて作成する場合は、あらかじめこのセクションに目を通しておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="73915-113">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
##  <a name="prerequisites-and-restrictions"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="73915-114">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="73915-114">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="73915-115">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="73915-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
 <span data-ttu-id="73915-116">詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73915-116">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="73915-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="73915-117">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="73915-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="73915-118">Permissions</span></span>  
 <span data-ttu-id="73915-119">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="73915-119">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="73915-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="73915-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="73915-121">**レプリカを追加するには**</span><span class="sxs-lookup"><span data-stu-id="73915-121">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="73915-122">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="73915-122">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="73915-123">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="73915-123">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="73915-124">可用性グループを右クリックし、次のコマンドのどちらかを選択します。</span><span class="sxs-lookup"><span data-stu-id="73915-124">Right-click the availability group, and select one of the following commands:</span></span>  
  
    -   <span data-ttu-id="73915-125">可用性グループへのレプリカ追加ウィザードを起動するには、 **[レプリカの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73915-125">Select the **Add Replica** command to launch the Add Replica to Availability Group Wizard.</span></span> <span data-ttu-id="73915-126">詳細については、「[可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73915-126">For more information, see [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
    -   <span data-ttu-id="73915-127">または、 **[可用性グループのプロパティ]** ダイアログ ボックスで、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73915-127">Alternatively, select the **Properties** command to open the **Availability Group Properties** dialog box.</span></span> <span data-ttu-id="73915-128">このダイアログ ボックスでレプリカを追加する手順は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="73915-128">The steps for adding a replica in this dialog box are as follows:</span></span>  
  
        1.  <span data-ttu-id="73915-129">ダイアログ ボックスの **[可用性レプリカ]** ペインで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73915-129">In the **Availability Replicas** pane of the dialog box, click the **Add** button.</span></span> <span data-ttu-id="73915-130">これにより、レプリカのエントリが作成され、空白の [サーバー インスタンス] フィールドが選択された状態になります。</span><span class="sxs-lookup"><span data-stu-id="73915-130">This creates and selects a replica entry in which the blank Server Instance field is selected.</span></span>  
  
        2.  <span data-ttu-id="73915-131">可用性レプリカをホストするための前提条件を満たしているサーバー インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="73915-131">Enter the name of a server instance that meets the prerequisites for hosting an availability replica.</span></span>  
  
         <span data-ttu-id="73915-132">さらにレプリカを追加するには、上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="73915-132">To add an additional replicas, repeat the preceding steps.</span></span> <span data-ttu-id="73915-133">レプリカの指定を完了したら、 **[OK]** をクリックして操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="73915-133">When you are done specifying replicas, click **OK** to complete the operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="73915-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="73915-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="73915-135">**レプリカを追加するには**</span><span class="sxs-lookup"><span data-stu-id="73915-135">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="73915-136">プライマリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73915-136">Connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="73915-137">ALTER AVAILABILITY GROUP ステートメントの ADD REPLICA ON 句を使用して、可用性グループに新しいセカンダリ レプリカを追加します。</span><span class="sxs-lookup"><span data-stu-id="73915-137">Add the new secondary replica to the availability group by using the ADD REPLICA ON clause of the ALTER AVAILABILITY GROUP statement.</span></span> <span data-ttu-id="73915-138">ADD REPLICA ON 句には、ENDPOINT_URL、AVAILABILITY_MODE、および FAILOVER_MODE オプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="73915-138">The ENDPOINT_URL, AVAILABILITY_MODE, and FAILOVER_MODE options are required in an ADD REPLICA ON clause.</span></span> <span data-ttu-id="73915-139">他のレプリカ オプション (BACKUP_PRIORITY、SECONDARY_ROLE、PRIMARY_ROLE、SESSION_TIMEOUT) は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="73915-139">The other replica options- BACKUP_PRIORITY, SECONDARY_ROLE, PRIMARY_ROLE, and SESSION_TIMEOUT-are optional.</span></span> <span data-ttu-id="73915-140">詳細については、「 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73915-140">For more information, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
     <span data-ttu-id="73915-141">たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、 `MyAG` によってホストされるデフォルト サーバー インスタンス (エンドポイント URL が `COMPUTER04`) の `TCP://COMPUTER04.Adventure-Works.com:5022'`という名前の可用性グループに新しいレプリカを作成します。</span><span class="sxs-lookup"><span data-stu-id="73915-141">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement creates a new replica to an availability group named `MyAG` on the default server instance hosted by `COMPUTER04`, whose endpoint URL is `TCP://COMPUTER04.Adventure-Works.com:5022'`.</span></span> <span data-ttu-id="73915-142">このレプリカは、手動フェールオーバーと非同期コミット可用性モードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="73915-142">This replica supports manual failover and asynchronous-commit availability mode.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG ADD REPLICA ON 'COMPUTER04'   
       WITH (  
             ENDPOINT_URL = 'TCP://COMPUTER04.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="73915-143">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="73915-143">Using PowerShell</span></span>  
 <span data-ttu-id="73915-144">**レプリカを追加するには**</span><span class="sxs-lookup"><span data-stu-id="73915-144">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="73915-145">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="73915-145">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="73915-146">**New-SqlAvailabilityReplica** コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="73915-146">Use the **New-SqlAvailabilityReplica** cmdlet.</span></span>  
  
     <span data-ttu-id="73915-147">たとえば、次のコマンドは、可用性レプリカを `MyAg`という名前の可用性グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="73915-147">For example, the following command adds an availability replica to an existing availability group named `MyAg`.</span></span> <span data-ttu-id="73915-148">このレプリカは、手動フェールオーバーと非同期コミット可用性モードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="73915-148">This replica supports manual failover and asynchronous-commit availability mode.</span></span> <span data-ttu-id="73915-149">セカンダリ ロールでは、このレプリカは読み取りアクセス接続をサポートして、読み取り専用の処理をこのレプリカにオフロードできるようにします。</span><span class="sxs-lookup"><span data-stu-id="73915-149">In the secondary role, this replica will support read access connections, allowing you to offload read-only processing to this replica.</span></span>  
  
    ```powershell
    $agPath = "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
    $endpointURL = "TCP://PrimaryServerName.domain.com:5022"  
    $failoverMode = "Manual"  
    $availabilityMode = "AsynchronousCommit"  
    $secondaryReadMode = "AllowAllConnections"  
  
    New-SqlAvailabilityReplica -Name SecondaryServer\Instance `   
    -EndpointUrl $endpointURL `   
    -FailoverMode $failoverMode `   
    -AvailabilityMode $availabilityMode `   
    -ConnectionModeInSecondaryRole $secondaryReadMode `   
    -Path $agPath  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="73915-150">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="73915-150">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="73915-151">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73915-151">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="73915-152">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="73915-152">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="73915-153">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="73915-153">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-adding-a-secondary-replica"></a><a name="FollowUp"></a> <span data-ttu-id="73915-154">補足情報: セカンダリ レプリカを追加した後</span><span class="sxs-lookup"><span data-stu-id="73915-154">Follow Up: After Adding a Secondary Replica</span></span>  
 <span data-ttu-id="73915-155">既存の可用性グループのレプリカを追加するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73915-155">To add a replica for an existing availability group, you must perform the following steps:</span></span>  
  
1.  <span data-ttu-id="73915-156">新しいセカンダリ レプリカをホストする予定のサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73915-156">Connect to the server instance that is going to host the new secondary replica.</span></span>  
  
2.  <span data-ttu-id="73915-157">新しいセカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="73915-157">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="73915-158">詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73915-158">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="73915-159">可用性グループ内の各データベースについて、セカンダリ レプリカをホストしているサーバー インスタンス上でセカンダリ データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="73915-159">For each database in the availability group, create a secondary database on the server instance that is hosting the secondary replica.</span></span> <span data-ttu-id="73915-160">詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73915-160">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="73915-161">新しいセカンダリ データベースのそれぞれを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="73915-161">Join each of the new secondary databases to the availability group.</span></span> <span data-ttu-id="73915-162">詳細については、「 [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73915-162">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="73915-163">関連タスク</span><span class="sxs-lookup"><span data-stu-id="73915-163">Related Tasks</span></span>  
 <span data-ttu-id="73915-164">**可用性レプリカを管理するには**</span><span class="sxs-lookup"><span data-stu-id="73915-164">**To manage an availability replica**</span></span>  
  
-   [<span data-ttu-id="73915-165">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73915-165">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="73915-166">可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73915-166">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="73915-167">可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73915-167">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="73915-168">可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73915-168">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="73915-169">可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73915-169">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="73915-170">可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73915-170">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="73915-171">可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73915-171">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="73915-172">参照</span><span class="sxs-lookup"><span data-stu-id="73915-172">See Also</span></span>  
 <span data-ttu-id="73915-173">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73915-173">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span></span>  
 <span data-ttu-id="73915-174">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="73915-174">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="73915-175">[可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="73915-175">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="73915-176">[AlwaysOn ダッシュボード &#40;SQL Server Management Studio を使用&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="73915-176">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="73915-177">可用性グループの監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73915-177">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
  
