---
title: 可用性グループへのセカンダリ レプリカの参加 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joinreplica.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
ms.assetid: e5bd2489-097a-490e-8ea1-34fe48378ad1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c38c2d59a46b15fc9a1dca77ae6a67e8e59e1b80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640230"
---
# <a name="join-a-secondary-replica-to-an-availability-group-sql-server"></a><span data-ttu-id="99cdc-102">可用性グループへのセカンダリ レプリカの参加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99cdc-102">Join a Secondary Replica to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="99cdc-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ レプリカを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-103">This topic describes how to join a secondary replica to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="99cdc-104">AlwaysOn 可用性グループにセカンダリ レプリカを追加したら、セカンダリ レプリカを可用性グループに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-104">After a secondary replica is added to an AlwaysOn availability group, the secondary replica must be joined to the availability group.</span></span> <span data-ttu-id="99cdc-105">レプリカの参加操作は、セカンダリ レプリカをホストしている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス上で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-105">The join-replica operation must be performed on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting the secondary replica.</span></span>  
  
-   <span data-ttu-id="99cdc-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="99cdc-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="99cdc-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="99cdc-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="99cdc-108">Security</span><span class="sxs-lookup"><span data-stu-id="99cdc-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="99cdc-109">**以下を使用してセカンダリ データベースを準備するには:**</span><span class="sxs-lookup"><span data-stu-id="99cdc-109">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="99cdc-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99cdc-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="99cdc-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99cdc-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="99cdc-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="99cdc-112">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="99cdc-113">**補足情報:** [セカンダリ データベースの構成](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="99cdc-113">**Follow Up:** [Configure Secondary Databases](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="99cdc-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="99cdc-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="99cdc-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="99cdc-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="99cdc-116">可用性グループのプライマリ レプリカが現在オンラインになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-116">The primary replica of the availability group must currently be online.</span></span>  
  
-   <span data-ttu-id="99cdc-117">可用性グループへの参加が済んでいないセカンダリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-117">You must be connected to the server instance that hosts a secondary replica that has not yet have been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="99cdc-118">プライマリ レプリカをホストしているサーバー インスタンスのデータベース ミラーリング エンドポイントに対してローカル サーバー インスタンスが接続できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-118">The local server instance must be able to connect to the database mirroring endpoint of the server instance that is hosting the primary replica.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="99cdc-119">いずれかの前提条件が満たされていない場合、参加操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-119">If any prerequisite is not met, the join operation fails.</span></span> <span data-ttu-id="99cdc-120">参加操作が失敗した場合は、プライマリ レプリカをホストしているサーバー インスタンスに接続し、セカンダリ レプリカを削除して再度追加した後で、可用性グループに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-120">After a failed join attempt, you might need to connect to the server instance that hosts the primary replica to remove and re-add the secondary replica before you can join it to the availability group.</span></span> <span data-ttu-id="99cdc-121">詳細については、「[可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)」および「[可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99cdc-121">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) and [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="99cdc-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="99cdc-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="99cdc-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="99cdc-123">Permissions</span></span>  
 <span data-ttu-id="99cdc-124">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="99cdc-124">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="99cdc-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="99cdc-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="99cdc-126">**可用性グループに可用性レプリカを参加させるには**</span><span class="sxs-lookup"><span data-stu-id="99cdc-126">**To join an availability replica to an availability group**</span></span>  
  
1.  <span data-ttu-id="99cdc-127">オブジェクト エクスプローラーで、セカンダリ レプリカをホストするサーバー インスタンスに接続し、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-127">In Object Explorer, connect to the server instance that hosts the secondary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="99cdc-128">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-128">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="99cdc-129">接続先のセカンダリ レプリカの可用性グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-129">Select the availability group of the secondary replica to which you are connected.</span></span>  
  
4.  <span data-ttu-id="99cdc-130">セカンダリ レプリカを右クリックし、 **[可用性グループへの参加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99cdc-130">Right-click the secondary replica, and click **Join to Availability Group**.</span></span>  
  
5.  <span data-ttu-id="99cdc-131">これにより、 **[可用性グループへのレプリカの追加]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="99cdc-131">This opens the **Join Replica to Availability Group** dialog box.</span></span>  
  
6.  <span data-ttu-id="99cdc-132">セカンダリ レプリカを可用性グループに参加させるには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99cdc-132">To join the secondary replica to the availability group, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="99cdc-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="99cdc-133">Using Transact-SQL</span></span>  
 <span data-ttu-id="99cdc-134">**可用性グループに可用性レプリカを参加させるには**</span><span class="sxs-lookup"><span data-stu-id="99cdc-134">**To join an availability replica to an availability group**</span></span>  
  
1.  <span data-ttu-id="99cdc-135">セカンダリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-135">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="99cdc-136">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-136">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="99cdc-137">ALTER AVAILABILITY GROUP *group_name* JOIN</span><span class="sxs-lookup"><span data-stu-id="99cdc-137">ALTER AVAILABILITY GROUP *group_name* JOIN</span></span>  
  
     <span data-ttu-id="99cdc-138">*group_name* は可用性グループの名前です。</span><span class="sxs-lookup"><span data-stu-id="99cdc-138">where *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="99cdc-139">次の例では、セカンダリ レプリカを `MyAG` 可用性グループに参加させています。</span><span class="sxs-lookup"><span data-stu-id="99cdc-139">The following example, joins the secondary replica to the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="99cdc-140">コンテキストで使用するこの [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを確認するには、「[可用性グループの作成 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99cdc-140">To see this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="99cdc-141">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="99cdc-141">Using PowerShell</span></span>  
 <span data-ttu-id="99cdc-142">**可用性グループに可用性レプリカを参加させるには**</span><span class="sxs-lookup"><span data-stu-id="99cdc-142">**To join an availability replica to an availability group**</span></span>  
  
 <span data-ttu-id="99cdc-143">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell プロバイダーで次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="99cdc-143">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell provider:</span></span>  
  
1.  <span data-ttu-id="99cdc-144">ディレクトリ変更コマンド (`cd`) を使用して、セカンダリ レプリカをホストするサーバー インスタンスに移動します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-144">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="99cdc-145">**Join-SqlAvailabilityGroup** コマンドレットに可用性グループの名前を指定して実行し、セカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="99cdc-145">Join the secondary replica to the availability group by executing the **Join-SqlAvailabilityGroup** cmdlet with the name of the availability group.</span></span>  
  
     <span data-ttu-id="99cdc-146">たとえば、次のコマンドは、指定されたパスにあるサーバー インスタンスによってホストされるセカンダリ レプリカを `MyAg`という名前の可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="99cdc-146">For example, the following command joins a secondary replica hosted by the server instance located at the specified path to the availability group named `MyAg`.</span></span>  <span data-ttu-id="99cdc-147">このサーバー インスタンスは、この可用性グループ内のセカンダリ レプリカをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-147">This server instance must host a secondary replica in this availability group.</span></span>  
  
    ```powershell
    Join-SqlAvailabilityGroup -Path SQLSERVER:\SQL\SecondaryServer\InstanceName -Name 'MyAg'  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="99cdc-148">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-148">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="99cdc-149">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99cdc-149">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="99cdc-150">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="99cdc-150">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="99cdc-151">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="99cdc-151">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-configure-secondary-databases"></a><a name="FollowUp"></a><span data-ttu-id="99cdc-152">補足情報: セカンダリデータベースを構成する</span><span class="sxs-lookup"><span data-stu-id="99cdc-152">Follow Up: Configure Secondary Databases</span></span>  
 <span data-ttu-id="99cdc-153">可用性グループ内のすべてのデータベースには、それぞれ対応するセカンダリ データベースが、セカンダリ レプリカをホストしているサーバー インスタンス上に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-153">For every database in the availability group, you need a secondary database on the server instance that is hosting the secondary replica.</span></span> <span data-ttu-id="99cdc-154">セカンダリ データベースの構成は、セカンダリ レプリカを可用性グループに参加させる前に行うことも、参加させた後に行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="99cdc-154">You can configure secondary databases either before or after you join a secondary replica to an availability group, as follows:</span></span>  
  
1.  <span data-ttu-id="99cdc-155">各プライマリ データベースの最新のデータベースとログ バックアップを、セカンダリ レプリカをホストするサーバー インスタンスに復元します。すべての復元操作は RESTORE WITH NORECOVERY で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="99cdc-155">Restore recent database and log backups of each primary database onto the server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY for every restore operation.</span></span> <span data-ttu-id="99cdc-156">詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-156">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="99cdc-157">各セカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="99cdc-157">Join each secondary database to the availability group.</span></span> <span data-ttu-id="99cdc-158">詳細については、「 [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99cdc-158">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cdc-159">参照</span><span class="sxs-lookup"><span data-stu-id="99cdc-159">See Also</span></span>  
 <span data-ttu-id="99cdc-160">[可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99cdc-160">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="99cdc-161">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99cdc-161">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="99cdc-162">SQL Server&#41;削除された AlwaysOn 可用性グループ構成 &#40;のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="99cdc-162">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
