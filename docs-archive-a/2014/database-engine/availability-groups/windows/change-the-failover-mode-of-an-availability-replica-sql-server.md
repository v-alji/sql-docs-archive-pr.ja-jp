---
title: 可用性レプリカのフェールオーバー モードの変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover modes [SQL Server]
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover modes
- Availability Groups [SQL Server], configuring
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d946440e2950192299c42652babb4082790dbd03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741318"
---
# <a name="change-the-failover-mode-of-an-availability-replica-sql-server"></a><span data-ttu-id="a7034-102">可用性レプリカのフェールオーバー モードの変更 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a7034-102">Change the Failover Mode of an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="a7034-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、または PowerShell を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]の AlwaysOn 可用性グループでの可用性レプリカのフェールオーバー モードを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7034-103">This topic describes how to change the failover mode of an availability replica in an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="a7034-104">フェールオーバー モードは、同期コミット可用性モードで実行されるレプリカのフェールオーバー モードを決定するレプリカ プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a7034-104">The failover mode is a replica property that determines the failover mode for replicas that run under synchronous-commit availability mode.</span></span> <span data-ttu-id="a7034-105">詳細については、「[フェールオーバーとフェールオーバー モード &#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md)」および「[可用性モード &#40;AlwaysOn 可用性グループ&#41;](availability-modes-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7034-105">For more information, see [Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) and [Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a7034-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="a7034-106">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="a7034-107">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="a7034-107">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="a7034-108">このタスクは、プライマリ レプリカ上でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a7034-108">This task is supported only on primary replicas.</span></span> <span data-ttu-id="a7034-109">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7034-109">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="a7034-110">SQL Server フェールオーバー クラスター インスタンス (FCI) は可用性グループによる自動フェールオーバーをサポートしないため、FCI によってホストされる可用性レプリカは手動フェールオーバー用にのみ構成できます。</span><span class="sxs-lookup"><span data-stu-id="a7034-110">SQL Server Failover Cluster Instances (FCIs) do not support automatic failover by availability groups, so any availability replica that is hosted by an FCI can only be configured for manual failover.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a7034-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a7034-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a7034-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="a7034-112">Permissions</span></span>  
 <span data-ttu-id="a7034-113">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7034-113">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a7034-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a7034-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a7034-115">**可用性レプリカのフェールオーバー モードを変更するには**</span><span class="sxs-lookup"><span data-stu-id="a7034-115">**To change the failover mode of an availability replica**</span></span>  
  
1.  <span data-ttu-id="a7034-116">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7034-116">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="a7034-117">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7034-117">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="a7034-118">変更するレプリカが含まれる可用性グループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7034-118">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="a7034-119">レプリカを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7034-119">Right-click the replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="a7034-120">**[可用性レプリカ プロパティ]** ダイアログ ボックスで **[フェールオーバー モード]** ボックスの一覧を使用して、このレプリカのフェールオーバー モードを変更します。</span><span class="sxs-lookup"><span data-stu-id="a7034-120">In the **Availability Replica Properties** dialog box, use the **Failover mode** drop list to change the failover mode of this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a7034-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a7034-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="a7034-122">**可用性レプリカのフェールオーバー モードを変更するには**</span><span class="sxs-lookup"><span data-stu-id="a7034-122">**To change the failover mode of an availability replica**</span></span>  
  
1.  <span data-ttu-id="a7034-123">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a7034-123">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="a7034-124">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="a7034-124">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="a7034-125">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span><span class="sxs-lookup"><span data-stu-id="a7034-125">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span></span>  
  
     <span data-ttu-id="a7034-126">WITH ( {</span><span class="sxs-lookup"><span data-stu-id="a7034-126">WITH ( {</span></span>  
  
     <span data-ttu-id="a7034-127">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span><span class="sxs-lookup"><span data-stu-id="a7034-127">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span></span>  
  
     <span data-ttu-id="a7034-128">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span><span class="sxs-lookup"><span data-stu-id="a7034-128">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span></span>  
  
     <span data-ttu-id="a7034-129">}  )</span><span class="sxs-lookup"><span data-stu-id="a7034-129">}  )</span></span>  
  
     <span data-ttu-id="a7034-130">where</span><span class="sxs-lookup"><span data-stu-id="a7034-130">where</span></span>  
  
    -   <span data-ttu-id="a7034-131">*group_name* は、可用性グループの名前です。</span><span class="sxs-lookup"><span data-stu-id="a7034-131">*group_name* is the name of the availability group.</span></span>  
  
    -   <span data-ttu-id="a7034-132">{ '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }</span><span class="sxs-lookup"><span data-stu-id="a7034-132">{ '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }</span></span>  
  
         <span data-ttu-id="a7034-133">変更する可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7034-133">Specifies the address of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica to be altered.</span></span> <span data-ttu-id="a7034-134">このアドレスの構成要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a7034-134">The components of this address are as follows:</span></span>  
  
         <span data-ttu-id="a7034-135">*system_name*</span><span class="sxs-lookup"><span data-stu-id="a7034-135">*system_name*</span></span>  
         <span data-ttu-id="a7034-136">スタンドアロン サーバー インスタンスが存在するコンピューター システムの NetBIOS 名です。</span><span class="sxs-lookup"><span data-stu-id="a7034-136">Is the NetBIOS name of the computer system on which a stand-alone server instance resides.</span></span>  
  
         <span data-ttu-id="a7034-137">*FCI_network_name*</span><span class="sxs-lookup"><span data-stu-id="a7034-137">*FCI_network_name*</span></span>  
         <span data-ttu-id="a7034-138">ターゲット サーバー インスタンスが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー (FCI) である [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターにアクセスするために使用されるネットワーク名です。</span><span class="sxs-lookup"><span data-stu-id="a7034-138">Is the network name that is used to access a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster in which a target server instance is a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover partner (an FCI).</span></span>  
  
         <span data-ttu-id="a7034-139">*instance_name*</span><span class="sxs-lookup"><span data-stu-id="a7034-139">*instance_name*</span></span>  
         <span data-ttu-id="a7034-140">ターゲットの可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="a7034-140">Is the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the target availability replica.</span></span> <span data-ttu-id="a7034-141">既定のサーバー インスタンスの場合、 *instance_name* は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a7034-141">For a default server instance, *instance_name* is optional.</span></span>  
  
     <span data-ttu-id="a7034-142">これらのパラメーターの詳細については、「[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7034-142">For more information about these parameters, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
     <span data-ttu-id="a7034-143">次の例は、 *MyAG* 可用性グループのプライマリ レプリカで実行すると、 *COMPUTER01*という名前のコンピューター上の既定のサーバー インスタンスにある可用性レプリカで、フェールオーバー モードが自動フェールオーバーに変更されます。</span><span class="sxs-lookup"><span data-stu-id="a7034-143">The following example, entered on the primary replica of the *MyAG* availability group, changes the failover mode to automatic failover on the availability replica that is located on the default server instance on a computer named *COMPUTER01*.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="a7034-144">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="a7034-144">Using PowerShell</span></span>  

### <a name="to-change-the-failover-mode-of-an-availability-replica"></a><span data-ttu-id="a7034-145">可用性レプリカのフェールオーバー モードを変更するには</span><span class="sxs-lookup"><span data-stu-id="a7034-145">To change the failover mode of an availability replica</span></span>
  
1.  <span data-ttu-id="a7034-146">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="a7034-146">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="a7034-147">`Set-SqlAvailabilityReplica` パラメーターを指定して `FailoverMode` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7034-147">Use the `Set-SqlAvailabilityReplica` cmdlet with the `FailoverMode` parameter.</span></span> <span data-ttu-id="a7034-148">レプリカを自動フェールオーバーに設定するときは、`AvailabilityMode` パラメーターを使用して、レプリカを同期コミット可用性モードに変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7034-148">When setting a replica to automatic failover, you might need to use the `AvailabilityMode` parameter to change the replica to synchronous-commit availability mode.</span></span>  
  
     <span data-ttu-id="a7034-149">たとえば、次のコマンドは、可用性グループ `MyReplica` のレプリカ `MyAg` を、同期コミット可用性モードを使用し、自動フェールオーバーをサポートするように変更します。</span><span class="sxs-lookup"><span data-stu-id="a7034-149">For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous-commit availability mode and to support automatic failover.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\Replicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7034-150">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7034-150">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="a7034-151">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7034-151">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="a7034-152">SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7034-152">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a7034-153">参照</span><span class="sxs-lookup"><span data-stu-id="a7034-153">See Also</span></span>  
 [<span data-ttu-id="a7034-154">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="a7034-154">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="a7034-155">[可用性モード &#40;AlwaysOn 可用性グループ&#41;](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="a7034-155">[Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="a7034-156">フェールオーバーとフェールオーバーモード &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="a7034-156">Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;</span></span>](failover-and-failover-modes-always-on-availability-groups.md) 
