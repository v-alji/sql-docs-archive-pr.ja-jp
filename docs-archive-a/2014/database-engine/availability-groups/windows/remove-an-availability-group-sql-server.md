---
title: 可用性グループの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.deleteag.f1
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], dropping
ms.assetid: 4b7f7f62-43a3-49db-a72e-22d4d7c2ddbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c17b7d5b362d8b4030d66ebf7ba0e425495410e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634056"
---
# <a name="remove-an-availability-group-sql-server"></a><span data-ttu-id="3a4fe-102">可用性グループの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3a4fe-102">Remove an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="3a4fe-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)]、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-103">This topic describes how to delete (drop) an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3a4fe-104">可用性グループを削除する際、可用性レプリカの 1 つをホストするサーバー インスタンスがオフラインだった場合は、再度オンラインになった時点でローカルの可用性レプリカが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-104">If a server instance that hosts one of the availability replicas is offline when you delete an availability group, after coming online, the server instance will drop the local availability replica.</span></span> <span data-ttu-id="3a4fe-105">可用性グループを削除すると、関連付けられている可用性グループ リスナーもすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-105">Dropping an availability group deletes any associated availability group listener.</span></span>  
  
 <span data-ttu-id="3a4fe-106">必要であれば、可用性グループの削除は、その可用性グループに対する適切なセキュリティ資格情報が存在する任意の Windows Server フェールオーバー クラスタリング (WSFC) ノードから行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-106">Note that, if necessary, you can drop an availability group from any Windows Server Failover Clustering (WSFC) node that possesses the correct security credentials for the availability group.</span></span> <span data-ttu-id="3a4fe-107">そのため、可用性レプリカがまったく残っていなくても可用性グループを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-107">This enables you to delete an availability group when none of its availability replicas remain.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3a4fe-108">可能であれば、プライマリ レプリカをホストするサーバー インスタンスに接続しているときにのみ可用性グループを削除してください。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-108">If possible, remove the availability group only while connected to the server instance that hosts the primary replica.</span></span> <span data-ttu-id="3a4fe-109">可用性グループをプライマリ レプリカから削除すると、元のプライマリ データベースで変更が許可されます (高可用性の保護なし)。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-109">When the availability group is dropped from the primary replica, changes are allowed in the former primary databases (without high availability protection).</span></span> <span data-ttu-id="3a4fe-110">セカンダリ レプリカから可用性グループを削除すると、プライマリ レプリカは RESTORING 状態になり、変更はデータベースで許可されません。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-110">Deleting an availability group from a secondary replica leaves the primary replica in the RESTORING state, and changes are not allowed on the databases.</span></span>  
  
-   <span data-ttu-id="3a4fe-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3a4fe-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3a4fe-112">制限事項と推奨事項</span><span class="sxs-lookup"><span data-stu-id="3a4fe-112">Limitations and Recommendations</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3a4fe-113">Security</span><span class="sxs-lookup"><span data-stu-id="3a4fe-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3a4fe-114">**以下を使用して可用性グループを削除するには:**</span><span class="sxs-lookup"><span data-stu-id="3a4fe-114">**To delete an availability group, using:**</span></span>  
  
     [<span data-ttu-id="3a4fe-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3a4fe-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3a4fe-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3a4fe-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="3a4fe-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a4fe-117">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="3a4fe-118">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="3a4fe-118">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3a4fe-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="3a4fe-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-recommendations"></a><a name="Restrictions"></a><span data-ttu-id="3a4fe-120">制限事項と推奨事項</span><span class="sxs-lookup"><span data-stu-id="3a4fe-120">Limitations and Recommendations</span></span>  
  
-   <span data-ttu-id="3a4fe-121">オンライン状態の可用性グループをセカンダリ レプリカから削除すると、プライマリ レプリカは RESTORING 状態になります。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-121">When the availability group is online, deleting it from a secondary replica causes the primary replica to transition to the RESTORING state.</span></span> <span data-ttu-id="3a4fe-122">したがって、可能であれば、プライマリ レプリカをホストするサーバー インスタンスから可用性グループのみを削除してください。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-122">Therefore, if possible, remove the availability group only from the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="3a4fe-123">WSFC フェールオーバー クラスターから削除されたコンピューターで可用性グループを削除した場合、可用性グループはローカルからのみ削除されます。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-123">If you delete an availability group from a computer that has been removed or evicted from the WSFC failover cluster, the availability group is only deleted locally.</span></span>  
  
-   <span data-ttu-id="3a4fe-124">Windows Server フェールオーバー クラスタリング (WSFC) クラスターにクォーラムがない場合は、可用性グループを削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-124">Avoid dropping an availability group when the Windows Server Failover Clustering (WSFC) cluster has no quorum.</span></span> <span data-ttu-id="3a4fe-125">クラスターのクォーラムがないときに可用性グループを削除すると、クラスターに格納されているメタデータ可用性グループは削除されません。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-125">If you must drop an availability group while the cluster lacks quorum, the metadata availability group that is stored in the cluster is not removed.</span></span> <span data-ttu-id="3a4fe-126">クラスターのクォーラムが再取得された後、WSFC クラスターから削除するために、可用性グループをもう一度削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-126">After the cluster regains quorum, you will need to drop the availability group again to remove it from the WSFC cluster.</span></span>  
  
-   <span data-ttu-id="3a4fe-127">セカンダリ レプリカについては、DROP AVAILABILITY GROUP は緊急の目的だけに使用してください。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-127">On a secondary replica, DROP AVAILABILITY GROUP should only be used only for emergency purposes.</span></span> <span data-ttu-id="3a4fe-128">理由は、可用性グループを削除すると可用性グループがオフラインになるためです。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-128">This is because dropping an availability group takes the availability group offline.</span></span> <span data-ttu-id="3a4fe-129">セカンダリ レプリカから可用性グループを削除した場合、プライマリ レプリカは、OFFLINE 状態がクォーラム損失、強制フェールオーバー、または DROP AVAILABILITY GROUP コマンドのどの原因で発生したのかを特定できません。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-129">If you drop the availability group from a secondary replica, the primary replica cannot determine whether the OFFLINE state occurred because of quorum loss, a forced failover, or a DROP AVAILABILITY GROUP command.</span></span> <span data-ttu-id="3a4fe-130">スプリット ブレイン状況の発生を防ぐために、プライマリ レプリカは RESTORING 状態に遷移します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-130">The primary replica transitions to the RESTORING state to prevent a possible split-brain situation.</span></span> <span data-ttu-id="3a4fe-131">詳細については、「 [動作方法: DROP AVAILABILITY GROUP の動作](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) 」(CSS SQL Server エンジニアのブログ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-131">For more information, see [How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server Engineers blog).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3a4fe-132">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3a4fe-132">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3a4fe-133">Permissions</span><span class="sxs-lookup"><span data-stu-id="3a4fe-133">Permissions</span></span>  
 <span data-ttu-id="3a4fe-134">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-134">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span> <span data-ttu-id="3a4fe-135">ローカル サーバー インスタンスによってホストされていない可用性グループを削除するには、その可用性グループ上の CONTROL SERVER 権限または CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-135">To drop an availability group that is not hosted by the local server instance you need CONTROL SERVER permission or CONTROL permission on that Availability Group.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3a4fe-136">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3a4fe-136">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3a4fe-137">**可用性グループを削除するには**</span><span class="sxs-lookup"><span data-stu-id="3a4fe-137">**To delete an availability group**</span></span>  
  
1.  <span data-ttu-id="3a4fe-138">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続するか (可能な場合)、可用性グループの適切なセキュリティ資格情報を持つ WSFC ノード上の AlwaysOn 可用性グループに対して有効な別のサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-138">In Object Explorer, connect to the server instance that hosts primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span> <span data-ttu-id="3a4fe-139">サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-139">Expand the server tree.</span></span>  
  
2.  <span data-ttu-id="3a4fe-140">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-140">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="3a4fe-141">削除する可用性グループが複数であるか単独であるかによって、次のように実行する手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-141">This step depends on whether you want to delete multiple availability groups or only one availability group, as follows:</span></span>  
  
    -   <span data-ttu-id="3a4fe-142">(プライマリ レプリカが接続先のサーバー インスタンスにある) 複数の可用性グループを削除するには、**[オブジェクト エクスプローラーの詳細]** ペインを使用して、削除するすべての可用性グループを表示し、選択します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-142">To delete multiple availability groups (whose primary replicas are on the connected server instance), use the **Object Explorer Details** pane to view and select all the availability groups that you want to delete.</span></span> <span data-ttu-id="3a4fe-143">詳細については、「[[オブジェクト エクスプローラーの詳細] を使用した可用性グループの監視 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-143">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="3a4fe-144">単独の可用性グループを削除するには、 **[オブジェクト エクスプローラー]** ペインまたは **[オブジェクト エクスプローラーの詳細]** ペインで目的の可用性グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-144">To delete a single availability group, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
4.  <span data-ttu-id="3a4fe-145">選択した 1 つまたは複数の可用性グループを右クリックし、 **[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-145">Right-click the selected availability group or groups, and select the **Delete** command.</span></span>  
  
5.  <span data-ttu-id="3a4fe-146">**[可用性グループの削除]** ダイアログ ボックスで、表示された可用性グループを削除するために、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-146">In the **Remove Availability Group** dialog box, to delete all the listed availability groups, click **OK**.</span></span> <span data-ttu-id="3a4fe-147">表示された可用性グループをすべて削除しない場合は、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-147">If you do not want to remove all the listed availability groups, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3a4fe-148">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3a4fe-148">Using Transact-SQL</span></span>  
 <span data-ttu-id="3a4fe-149">**可用性グループを削除するには**</span><span class="sxs-lookup"><span data-stu-id="3a4fe-149">**To delete an availability group**</span></span>  
  
1.  <span data-ttu-id="3a4fe-150">プライマリ レプリカをホストするサーバー インスタンスに接続するか (可能な場合)、可用性グループの適切なセキュリティ資格情報を持つ WSFC ノード上の AlwaysOn 可用性グループに対して有効な別のサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-150">Connect to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span>  
  
2.  <span data-ttu-id="3a4fe-151">[DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-151">Use the [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) statement, as follows</span></span>  
  
     <span data-ttu-id="3a4fe-152">DROP AVAILABILITY GROUP *group_name*</span><span class="sxs-lookup"><span data-stu-id="3a4fe-152">DROP AVAILABILITY GROUP *group_name*</span></span>  
  
     <span data-ttu-id="3a4fe-153">*group_name* には、削除する可用性グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-153">where *group_name* is the name of the availability group to be dropped.</span></span>  
  
     <span data-ttu-id="3a4fe-154">次の例では、 `MyAG` 可用性グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-154">The following example deletes the `MyAG` availability group.</span></span>  
  
    ```sql
    DROP AVAILABILITY GROUP MyAG;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="3a4fe-155">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="3a4fe-155">Using PowerShell</span></span>  
 <span data-ttu-id="3a4fe-156">**可用性グループを削除するには**</span><span class="sxs-lookup"><span data-stu-id="3a4fe-156">**To delete an availability group**</span></span>  
  
 <span data-ttu-id="3a4fe-157">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell プロバイダーで次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-157">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell provider:</span></span>  
  
1.  <span data-ttu-id="3a4fe-158">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) するか (可能な場合)、可用性グループの適切なセキュリティ資格情報を持つ WSFC ノード上の AlwaysOn 可用性グループに対して有効な別のサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-158">Change directory (`cd`) to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span>  
  
2.  <span data-ttu-id="3a4fe-159">**Remove-SqlAvailabilityGroup** コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-159">Use the **Remove-SqlAvailabilityGroup** cmdlet.</span></span>  
  
     <span data-ttu-id="3a4fe-160">たとえば、次のコマンドでは、 `MyAg`という名前の可用性グループが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-160">For example, the following command removes the availability group named `MyAg`.</span></span> <span data-ttu-id="3a4fe-161">このコマンドは、可用性グループの可用性レプリカをホストするサーバー インスタンスで実行できます。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-161">This command can be executed on any server instance that hosts an availability replica for the availability group.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="3a4fe-162">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-162">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="3a4fe-163">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a4fe-163">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="3a4fe-164">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="3a4fe-164">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="3a4fe-165">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="3a4fe-165">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="3a4fe-166">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="3a4fe-166">Related Content</span></span>  
  
-   <span data-ttu-id="3a4fe-167">[動作方法: DROP AVAILABILITY GROUP の動作](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server エンジニアのブログ)</span><span class="sxs-lookup"><span data-stu-id="3a4fe-167">[How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server Engineers blog)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a4fe-168">参照</span><span class="sxs-lookup"><span data-stu-id="3a4fe-168">See Also</span></span>  
 <span data-ttu-id="3a4fe-169">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3a4fe-169">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="3a4fe-170">可用性グループの作成と構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3a4fe-170">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
