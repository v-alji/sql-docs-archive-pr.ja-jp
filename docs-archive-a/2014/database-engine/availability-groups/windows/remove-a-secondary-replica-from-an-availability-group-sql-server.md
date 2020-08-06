---
title: 可用性グループからのセカンダリ レプリカの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removesecondaryar.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3f2b35ec9cf27f2f7b23714a41665f2709837a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634058"
---
# <a name="remove-a-secondary-replica-from-an-availability-group-sql-server"></a><span data-ttu-id="2f4af-102">可用性グループからのセカンダリ レプリカの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2f4af-102">Remove a Secondary Replica from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="2f4af-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループからセカンダリ レプリカを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-103">This topic describes how to remove a secondary replica from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="2f4af-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2f4af-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2f4af-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2f4af-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2f4af-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="2f4af-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="2f4af-107">Security</span><span class="sxs-lookup"><span data-stu-id="2f4af-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2f4af-108">**セカンダリ レプリカを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="2f4af-108">**To remove a secondary replica, using:**</span></span>  
  
     [<span data-ttu-id="2f4af-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2f4af-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2f4af-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2f4af-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="2f4af-111">PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f4af-111">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="2f4af-112">**補足情報:**  [セカンダリ レプリカの削除後](#PostBestPractices)</span><span class="sxs-lookup"><span data-stu-id="2f4af-112">**Follow Up:**  [After Removing a Secondary Replica](#PostBestPractices)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2f4af-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="2f4af-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2f4af-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2f4af-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2f4af-115">このタスクは、プライマリ レプリカ上でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2f4af-115">This task is supported only on the primary replica.</span></span>  
  
-   <span data-ttu-id="2f4af-116">セカンダリ レプリカのみを可用性グループから削除できます。</span><span class="sxs-lookup"><span data-stu-id="2f4af-116">Only a secondary replica can be removed from an availability group.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="2f4af-117">前提条件</span><span class="sxs-lookup"><span data-stu-id="2f4af-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="2f4af-118">可用性グループのプライマリ レプリカをホストするサーバー インスタンスに接続している。</span><span class="sxs-lookup"><span data-stu-id="2f4af-118">You must be connected to the server instance that hosts the primary replica of the availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2f4af-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2f4af-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2f4af-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="2f4af-120">Permissions</span></span>  
 <span data-ttu-id="2f4af-121">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f4af-121">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2f4af-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2f4af-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2f4af-123">**セカンダリ レプリカを削除するには**</span><span class="sxs-lookup"><span data-stu-id="2f4af-123">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="2f4af-124">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-124">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="2f4af-125">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-125">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="2f4af-126">可用性グループを選択し、 **[可用性レプリカ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-126">Select the availability group, and expand the **Availability Replicas** node.</span></span>  
  
4.  <span data-ttu-id="2f4af-127">削除するレプリカが複数であるか単独であるかによって、次のように実行する手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="2f4af-127">This step depends on whether you want to remove multiple replicas or only one replica, as follows:</span></span>  
  
    -   <span data-ttu-id="2f4af-128">複数のレプリカを削除するには、 **[オブジェクト エクスプローラーの詳細]** ペインを使用して、削除するレプリカを表示してすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-128">To remove multiple replicas, use the **Object Explorer Details** pane to view and select all the replicas that you want to remove.</span></span> <span data-ttu-id="2f4af-129">詳細については、「[[オブジェクト エクスプローラーの詳細] を使用した可用性グループの監視 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f4af-129">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="2f4af-130">単独のレプリカを削除するには、 **[オブジェクト エクスプローラー]** ペインまたは **[オブジェクト エクスプローラーの詳細]** ペインで選択します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-130">To remove a single replica, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="2f4af-131">選択したセカンダリ レプリカを右クリックし、コマンド メニューの **[可用性グループからの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f4af-131">Right-click the selected secondary replica or replicas, and select **Remove from Availability Group** in the command menu.</span></span>  
  
6.  <span data-ttu-id="2f4af-132">**[可用性グループからのセカンダリ レプリカの削除]** ダイアログ ボックスで、表示されたすべてのデータベースを削除するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f4af-132">In the **Remove Secondary Replicas from Availability Group** dialog box, to remove all the listed secondary replicas, click **OK**.</span></span> <span data-ttu-id="2f4af-133">表示されたレプリカをすべて削除しない場合は、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f4af-133">If you do not want to remove all the listed replicas, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2f4af-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2f4af-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="2f4af-135">**セカンダリ レプリカを削除するには**</span><span class="sxs-lookup"><span data-stu-id="2f4af-135">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="2f4af-136">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-136">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="2f4af-137">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-137">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="2f4af-138">ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]</span><span class="sxs-lookup"><span data-stu-id="2f4af-138">ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]</span></span>  
  
     <span data-ttu-id="2f4af-139">*group_name* は可用性グループの名前、 *instance_name* はセカンダリ レプリカがあるサーバー インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="2f4af-139">where *group_name* is the name of the availability group and *instance_name* is the server instance where the secondary replica is located.</span></span>  
  
     <span data-ttu-id="2f4af-140">次の例では、セカンダリ レプリカを *MyAG* 可用性グループから削除しています。</span><span class="sxs-lookup"><span data-stu-id="2f4af-140">The following example removes a secondary replica from the *MyAG* availability group.</span></span> <span data-ttu-id="2f4af-141">対象のセカンダリ レプリカは、 *COMPUTER02* という名前のコンピューターの *HADR_INSTANCE*という名前のサーバー インスタンスにあります。</span><span class="sxs-lookup"><span data-stu-id="2f4af-141">The target secondary replica is located on a server instance named *HADR_INSTANCE* on a computer named *COMPUTER02*.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="2f4af-142">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="2f4af-142">Using PowerShell</span></span>  
 <span data-ttu-id="2f4af-143">**セカンダリ レプリカを削除するには**</span><span class="sxs-lookup"><span data-stu-id="2f4af-143">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="2f4af-144">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-144">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="2f4af-145">**Remove-SqlAvailabilityReplica** コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-145">Use the **Remove-SqlAvailabilityReplica** cmdlet.</span></span>  
  
     <span data-ttu-id="2f4af-146">たとえば、次のコマンドは、サーバー `MyReplica` 上の可用性レプリカを、 `MyAg`という名前の可用性グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-146">For example, the following command removes the availability replica on the server `MyReplica` from the availability group named `MyAg`.</span></span>  <span data-ttu-id="2f4af-147">このコマンドは、可用性グループのプライマリ レプリカをホストするサーバー インスタンスで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f4af-147">This command must be run on the server instance that hosts the primary replica of the availability group.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityReplica -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f4af-148">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-148">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="2f4af-149">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f4af-149">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="2f4af-150">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="2f4af-150">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="2f4af-151">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="2f4af-151">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-replica"></a><a name="PostBestPractices"></a><span data-ttu-id="2f4af-152">補足情報: セカンダリレプリカを削除した後</span><span class="sxs-lookup"><span data-stu-id="2f4af-152">Follow Up: After Removing a Secondary Replica</span></span>  
 <span data-ttu-id="2f4af-153">現在使用できないレプリカを指定した場合、そのレプリカがオンラインに戻ったとき、可用性グループに属していないことが検出されます。</span><span class="sxs-lookup"><span data-stu-id="2f4af-153">If you specify a replica that is currently unavailable, when the replica comes online, it will discover that it has been removed.</span></span>  
  
 <span data-ttu-id="2f4af-154">レプリカの削除により、データの受信が停止します。</span><span class="sxs-lookup"><span data-stu-id="2f4af-154">Removing a replica causes it to stop receiving data.</span></span> <span data-ttu-id="2f4af-155">セカンダリ レプリカがグローバル ストアから削除されたことが確認されると、RECOVERING 状態でローカル サーバー インスタンスに残っている可用性グループ設定がデータベースから削除されます。</span><span class="sxs-lookup"><span data-stu-id="2f4af-155">After a secondary replica confirms that it has been removed from the global store, the replica removes the availability group settings from its databases, which remain on the local server instance in the RECOVERING state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4af-156">参照</span><span class="sxs-lookup"><span data-stu-id="2f4af-156">See Also</span></span>  
 <span data-ttu-id="2f4af-157">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2f4af-157">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="2f4af-158">[セカンダリレプリカを可用性グループ &#40;SQL Server に追加&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2f4af-158">[Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md) </span></span>  
 [<span data-ttu-id="2f4af-159">可用性グループの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2f4af-159">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
