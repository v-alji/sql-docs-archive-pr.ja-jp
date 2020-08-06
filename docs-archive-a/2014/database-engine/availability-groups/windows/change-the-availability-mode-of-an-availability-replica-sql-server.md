---
title: 可用性レプリカの可用性モードの変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1636f3ea86e083e47276423b120dbc8d3744d387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741329"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a><span data-ttu-id="89a3c-102">可用性レプリカの可用性モードの変更 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="89a3c-102">Change the Availability Mode of an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="89a3c-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、または PowerShell を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]の AlwaysOn 可用性グループでの可用性レプリカの可用性モードを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-103">This topic describes how to change the availability mode of an availability replica in an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="89a3c-104">可用性モードは、レプリカによるコミットが非同期か同期かを制御するレプリカ プロパティです。</span><span class="sxs-lookup"><span data-stu-id="89a3c-104">The availability mode is a replica property that controls the whether the replica commits asynchronously or synchronously.</span></span> <span data-ttu-id="89a3c-105">*非同期コミット モード* は、高可用性を犠牲にしてパフォーマンスを最大限に高めるものであり、 *強制フェールオーバー*と通常呼ばれる強制手動フェールオーバー (データ損失の可能性あり) のみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="89a3c-105">*Asynchronous-commit mode* maximizes performance at the expense of high availability and supports only forced manual failover (with possible data loss), typically called *forced failover*.</span></span> <span data-ttu-id="89a3c-106">*同期コミット モード* は、パフォーマンスよりも高可用性を重視し、セカンダリ レプリカの同期後は手動でのフェールオーバーをサポートします (必要に応じて、自動フェールオーバーもサポートします)。</span><span class="sxs-lookup"><span data-stu-id="89a3c-106">*Synchronous-commit mode* emphasizes high availability over performance and, once the secondary replica is synchronized, supports manual failover and, optionally, automatic failover.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="89a3c-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="89a3c-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="89a3c-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="89a3c-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="89a3c-109">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="89a3c-109">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="89a3c-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="89a3c-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="89a3c-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="89a3c-111">Permissions</span></span>  
 <span data-ttu-id="89a3c-112">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="89a3c-112">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="89a3c-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="89a3c-113">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="89a3c-114">**可用性グループの可用性モードを変更するには**</span><span class="sxs-lookup"><span data-stu-id="89a3c-114">**To change the availability mode of an availability group**</span></span>  
  
1.  <span data-ttu-id="89a3c-115">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-115">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="89a3c-116">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-116">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="89a3c-117">変更するレプリカが含まれる可用性グループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="89a3c-117">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="89a3c-118">レプリカを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89a3c-118">Right-click the replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="89a3c-119">**[可用性レプリカ プロパティ]** ダイアログ ボックスで **[可用性モード]** ボックスの一覧を使用して、このレプリカの可用性モードを変更します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-119">In the **Availability Replica Properties** dialog box, use the **Availability mode** drop list to change the availability mode of this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="89a3c-120">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="89a3c-120">Using Transact-SQL</span></span>  
 <span data-ttu-id="89a3c-121">**可用性グループの可用性モードを変更するには**</span><span class="sxs-lookup"><span data-stu-id="89a3c-121">**To change the availability mode of an availability group**</span></span>  
  
1.  <span data-ttu-id="89a3c-122">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-122">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="89a3c-123">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-123">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="89a3c-124">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span><span class="sxs-lookup"><span data-stu-id="89a3c-124">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span></span>  
  
     <span data-ttu-id="89a3c-125">WITH ( {</span><span class="sxs-lookup"><span data-stu-id="89a3c-125">WITH ( {</span></span>  
  
     <span data-ttu-id="89a3c-126">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span><span class="sxs-lookup"><span data-stu-id="89a3c-126">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span></span>  
  
     <span data-ttu-id="89a3c-127">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span><span class="sxs-lookup"><span data-stu-id="89a3c-127">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span></span>  
  
     <span data-ttu-id="89a3c-128">} )</span><span class="sxs-lookup"><span data-stu-id="89a3c-128">} )</span></span>  
  
     <span data-ttu-id="89a3c-129">ここで*group_name*は可用性グループの名前、 *server_name*は変更するレプリカをホストするサーバーインスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="89a3c-129">where *group_name* is the name of the availability group and *server_name* is the name of the server instance that hosts the replica to be modified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89a3c-130">FAILOVER_MODE = AUTOMATIC は、AVAILABILITY_MODE = SYNCHRONOUS_COMMIT も指定した場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="89a3c-130">FAILOVER_MODE = AUTOMATIC is supported only if you also specify AVAILABILITY_MODE = SYNCHRONOUS_COMMIT.</span></span>  
  
     <span data-ttu-id="89a3c-131">次の例は、 `AccountsAG` 可用性グループのプライマリ レプリカに入力すると、 `INSTANCE09` サーバー インスタンスでホストされるレプリカの可用性モードを同期コミット、フェールオーバー モードを自動フェールオーバーに変更します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-131">The following example, entered on the primary replica of the `AccountsAG` availability group, changes the availability and failover modes to synchronous commit and automatic failover, respectively, for the replica hosted by the `INSTANCE09` server instance.</span></span>  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="89a3c-132">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="89a3c-132">Using PowerShell</span></span>

### <a name="to-change-the-availability-mode-of-an-availability-group"></a><span data-ttu-id="89a3c-133">可用性グループの可用性モードを変更するには</span><span class="sxs-lookup"><span data-stu-id="89a3c-133">To change the availability mode of an availability group</span></span>
  
1.  <span data-ttu-id="89a3c-134">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-134">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="89a3c-135">`Set-SqlAvailabilityReplica` コマンドレットを `AvailabilityMode` パラメーターと共に使用し、必要に応じて `FailoverMode` パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-135">Use the `Set-SqlAvailabilityReplica` cmdlet with the `AvailabilityMode` parameter and, optionally, the `FailoverMode` parameter.</span></span>  
  
     <span data-ttu-id="89a3c-136">たとえば、次のコマンドは、可用性グループ `MyReplica` のレプリカ `MyAg` を、同期コミット可用性モードを使用し、自動フェールオーバーをサポートするように変更します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-136">For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous-commit availability mode and to support automatic failover.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="89a3c-137">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="89a3c-137">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="89a3c-138">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89a3c-138">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="89a3c-139">SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89a3c-139">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89a3c-140">参照</span><span class="sxs-lookup"><span data-stu-id="89a3c-140">See Also</span></span>  
 <span data-ttu-id="89a3c-141">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="89a3c-141">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="89a3c-142">[可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="89a3c-142">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="89a3c-143">フェールオーバーとフェールオーバーモード &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="89a3c-143">Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;</span></span>](failover-and-failover-modes-always-on-availability-groups.md)  
