---
title: 可用性レプリカのセッション タイムアウト期間の変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], session timeout
- session timeout [SQL Server]
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 302ba4a2b0b72a70b05e563eb4085913074469eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741313"
---
# <a name="change-the-session-timeout-period-for-an-availability-replica-sql-server"></a><span data-ttu-id="225e2-102">可用性レプリカのセッション タイムアウト期間の変更 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="225e2-102">Change the Session-Timeout Period for an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="225e2-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性レプリカのセッション タイムアウト期間を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="225e2-103">This topic describes how to configure the session-timeout period of an AlwaysOn availability replica by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="225e2-104">セッション タイムアウト期間は、接続されたレプリカからの ping 応答を可用性レプリカが何秒待機するかを制御するレプリカ プロパティです。この期間を過ぎると、接続に失敗したと見なされます。</span><span class="sxs-lookup"><span data-stu-id="225e2-104">The session-timeout period is a replica property that controls how many seconds (in seconds) that an availability replica waits for a ping response from a connected replica before considering the connection to have failed.</span></span> <span data-ttu-id="225e2-105">既定では、レプリカは ping 応答を 10 秒間待機します。</span><span class="sxs-lookup"><span data-stu-id="225e2-105">By default, a replica waits 10 seconds for a ping response.</span></span> <span data-ttu-id="225e2-106">このレプリカ プロパティは、可用性グループ内の指定したセカンダリ レプリカとプライマリ レプリカ間の接続のみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="225e2-106">This replica property applies only the connection between a given secondary replica and the primary replica of the availability group.</span></span> <span data-ttu-id="225e2-107">セッション タイムアウト期間の詳細については、「[Always On 可用性グループの概要 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="225e2-107">For more information about the session-timeout period, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="225e2-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="225e2-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="225e2-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="225e2-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="225e2-110">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="225e2-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="225e2-111">Security</span><span class="sxs-lookup"><span data-stu-id="225e2-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="225e2-112">**セッションのタイムアウト期間を変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="225e2-112">**To change the session-timeout period, using:**</span></span>  
  
     [<span data-ttu-id="225e2-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="225e2-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="225e2-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="225e2-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="225e2-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="225e2-115">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="225e2-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="225e2-116">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="225e2-117">前提条件</span><span class="sxs-lookup"><span data-stu-id="225e2-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="225e2-118">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="225e2-118">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="225e2-119">推奨事項</span><span class="sxs-lookup"><span data-stu-id="225e2-119">Recommendations</span></span>  
 <span data-ttu-id="225e2-120">タイムアウト期間を 10 秒以上にしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="225e2-120">We recommend that you keep the time-out period at 10 seconds or greater.</span></span> <span data-ttu-id="225e2-121">値を 10 秒未満に設定すると、負荷の高いシステムでは PING を受信できず、誤認エラーが示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="225e2-121">Setting the value to less than 10 seconds creates the possibility of a heavily loaded system missing PINGs and declaring a false failure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="225e2-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="225e2-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="225e2-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="225e2-123">Permissions</span></span>  
 <span data-ttu-id="225e2-124">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="225e2-124">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="225e2-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="225e2-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="225e2-126">**可用性レプリカのセッション タイムアウト期間を変更するには**</span><span class="sxs-lookup"><span data-stu-id="225e2-126">**To change the session-timeout period for an availability replica**</span></span>  
  
1.  <span data-ttu-id="225e2-127">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="225e2-127">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="225e2-128">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="225e2-128">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="225e2-129">構成する可用性レプリカが含まれる可用性グループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="225e2-129">Click the availability group whose availability replica you want to configure.</span></span>  
  
4.  <span data-ttu-id="225e2-130">構成するレプリカを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="225e2-130">Right-click the replica to be configured, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="225e2-131">**[可用性レプリカ プロパティ]** ダイアログ ボックスで **[セッションのタイムアウト (秒)]** フィールドを使用して、このレプリカでのセッション タイムアウト期間の秒数を変更します。</span><span class="sxs-lookup"><span data-stu-id="225e2-131">In the **Availability Replica Properties** dialog box, use the **Session timeout (seconds)** field to change the number of seconds for the session-timeout period on this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="225e2-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="225e2-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="225e2-133">**可用性レプリカのセッション タイムアウト期間を変更するには**</span><span class="sxs-lookup"><span data-stu-id="225e2-133">**To change the session-timeout period for an availability replica**</span></span>  
  
1.  <span data-ttu-id="225e2-134">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="225e2-134">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="225e2-135">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="225e2-135">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="225e2-136">ALTER AVAILABILITY GROUP *group_name*</span><span class="sxs-lookup"><span data-stu-id="225e2-136">ALTER AVAILABILITY GROUP *group_name*</span></span>  
  
     <span data-ttu-id="225e2-137">MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )</span><span class="sxs-lookup"><span data-stu-id="225e2-137">MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )</span></span>  
  
     <span data-ttu-id="225e2-138">*group_name* の部分には、可用性グループの名前を指定します。 *instance_name* の部分には、変更する可用性レプリカをホストするサーバー インスタンスの名前を指定します。 *seconds* には、レプリカがセカンダリ レプリカとして機能している場合に、データベースにログを適用する前に待機する必要がある最小秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="225e2-138">where *group_name* is the name of the availability group, *instance_name* is the name of the server instance that hosts the availability replica to be modified, and *seconds* specifies the minimum number of seconds that the replica must wait before applying log to databases when acting as a secondary replica.</span></span> <span data-ttu-id="225e2-139">既定値は 0 秒です。つまり、適用の遅延はありません。</span><span class="sxs-lookup"><span data-stu-id="225e2-139">The default is 0 seconds, which indicates that there is no apply delay.</span></span>  
  
     <span data-ttu-id="225e2-140">次の例は、 `AccountsAG` 可用性グループのプライマリ レプリカに入力すると、 `15` サーバー インスタンスにあるレプリカのセッション タイムアウト値を `INSTANCE09` 秒に変更します。</span><span class="sxs-lookup"><span data-stu-id="225e2-140">The following example, entered on the primary replica of the `AccountsAG` availability group, changes the session-timeout value to `15` seconds for the replica located on the `INSTANCE09` server instance.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="225e2-141">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="225e2-141">Using PowerShell</span></span>  

### <a name="to-change-the-session-timeout-period-for-an-availability-replica"></a><span data-ttu-id="225e2-142">可用性レプリカのセッション タイムアウト期間を変更するには</span><span class="sxs-lookup"><span data-stu-id="225e2-142">To change the session-timeout period for an availability replica</span></span>
  
1.  <span data-ttu-id="225e2-143">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="225e2-143">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="225e2-144">`Set-SqlAvailabilityReplica` コマンドレットを `SessionTimeout` パラメーターを指定して使用し、指定された可用性レプリカのセッション タイムアウト期間の秒数を変更します。</span><span class="sxs-lookup"><span data-stu-id="225e2-144">Use the `Set-SqlAvailabilityReplica` cmdlet with the `SessionTimeout` parameter to change the number of seconds for the session-timeout period on a specified availability replica.</span></span>  
  
     <span data-ttu-id="225e2-145">たとえば、次のコマンドは、セッションのタイムアウト期間を 15 秒に設定します。</span><span class="sxs-lookup"><span data-stu-id="225e2-145">For example, the following command sets the session-timeout period to 15 seconds.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -SessionTimeout 15 -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="225e2-146">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="225e2-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="225e2-147">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="225e2-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="225e2-148">SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="225e2-148">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="225e2-149">参照</span><span class="sxs-lookup"><span data-stu-id="225e2-149">See Also</span></span>  
 [<span data-ttu-id="225e2-150">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="225e2-150">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
