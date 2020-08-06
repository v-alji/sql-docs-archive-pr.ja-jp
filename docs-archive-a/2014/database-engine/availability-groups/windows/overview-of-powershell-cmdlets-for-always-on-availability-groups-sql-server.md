---
title: AlwaysOn 可用性グループ用の PowerShell コマンドレットの概要 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], PowerShell cmdlets
- Availability Groups [SQL Server], about
- PowerShell [SQL Server], cmdlets
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6861abb3358df5e8c223d387b82e22de0f2a9d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633295"
---
# <a name="overview-of-powershell-cmdlets-for-alwayson-availability-groups-sql-server"></a><span data-ttu-id="070c1-102">AlwaysOn 可用性グループの PowerShell コマンドレットの概要 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="070c1-102">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups (SQL Server)</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="070c1-103">PowerShell は、特にシステム管理用に設計されている、タスク ベースのコマンド ライン シェルとスクリプト言語です。</span><span class="sxs-lookup"><span data-stu-id="070c1-103">PowerShell is a task-based command-line shell and scripting language designed especially for system administration.</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="070c1-104">は、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で一連の PowerShell コマンドレットを提供しており、それらを使用すると可用性グループ、可用性レプリカ、および可用性データベースの配置、管理、および監視ができます。</span><span class="sxs-lookup"><span data-stu-id="070c1-104">provides a set of PowerShell cmdlets in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that enable you to deploy, manage, and monitor availability groups, availability replicas, and availability databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="070c1-105">PowerShell コマンドレットは、アクションを正常に開始した時点で完了できます。</span><span class="sxs-lookup"><span data-stu-id="070c1-105">A PowerShell cmdlet can complete by successfully initiating an action.</span></span> <span data-ttu-id="070c1-106">つまり、目的の操作 (可用性グループのフェールオーバーなど) の完了を示すわけではありません。</span><span class="sxs-lookup"><span data-stu-id="070c1-106">This does not indicate that the intended work, such as the fail over of an availability group, has completed.</span></span> <span data-ttu-id="070c1-107">一連の操作をスクリプト化している場合は、アクションの状態を確認し、完了するまで待機しなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="070c1-107">When scripting a sequence of actions, you might have to check the status of actions, and wait for them to complete.</span></span>  
  
 <span data-ttu-id="070c1-108">このトピックでは、以下の一連のタスクのためのコマンドレットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="070c1-108">This topic introduces the cmdlets for the following sets of tasks:</span></span>  
  
-   [<span data-ttu-id="070c1-109">AlwaysOn 可用性グループ用のサーバーインスタンスの構成</span><span class="sxs-lookup"><span data-stu-id="070c1-109">Configuring a server instance for AlwaysOn Availability Groups</span></span>](#ConfiguringServerInstance)  
  
-   [<span data-ttu-id="070c1-110">データベースとトランザクションログのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="070c1-110">Backing up and restoring databases and transaction logs</span></span>](#BnRcmdlets)  
  
-   [<span data-ttu-id="070c1-111">可用性グループの作成と管理</span><span class="sxs-lookup"><span data-stu-id="070c1-111">Creating and managing an availability group</span></span>](#DeployManageAGs)  
  
-   [<span data-ttu-id="070c1-112">可用性グループ リスナーの作成と管理</span><span class="sxs-lookup"><span data-stu-id="070c1-112">Creating and managing an availability group listener</span></span>](#AGlisteners)  
  
-   [<span data-ttu-id="070c1-113">可用性レプリカの作成と管理</span><span class="sxs-lookup"><span data-stu-id="070c1-113">Creating and managing an availability replica</span></span>](#DeployManageARs)  
  
-   [<span data-ttu-id="070c1-114">可用性データベースの追加と管理</span><span class="sxs-lookup"><span data-stu-id="070c1-114">Adding and managing an availability database</span></span>](#DeployManageDbs)  
  
-   [<span data-ttu-id="070c1-115">可用性グループの正常性の監視</span><span class="sxs-lookup"><span data-stu-id="070c1-115">Monitoring availability group health</span></span>](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  <span data-ttu-id="070c1-116">コマンドレットを使用してタスクを実行する方法について説明しているオンラインブックのトピックの一覧につい [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ては、「 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] [AlwaysOn 可用性グループ &#40;SQL Server&#41;の概要](overview-of-always-on-availability-groups-sql-server.md)」の「関連タスク」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="070c1-116">For a list of topics in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Books Online that describe how to use cmdlets to perform [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks, see the "Related Tasks" section of [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="configuring-a-server-instance-for-alwayson-availability-groups"></a><a name="ConfiguringServerInstance"></a><span data-ttu-id="070c1-117">AlwaysOn 可用性グループ用のサーバーインスタンスの構成</span><span class="sxs-lookup"><span data-stu-id="070c1-117">Configuring a Server Instance for AlwaysOn Availability Groups</span></span>  
  
|<span data-ttu-id="070c1-118">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="070c1-118">Cmdlets</span></span>|<span data-ttu-id="070c1-119">説明</span><span class="sxs-lookup"><span data-stu-id="070c1-119">Description</span></span>|<span data-ttu-id="070c1-120">サポート対象</span><span class="sxs-lookup"><span data-stu-id="070c1-120">Supported on</span></span>|  
|-------------|-----------------|------------------|  
|`Disable-SqlAlwaysOn`|<span data-ttu-id="070c1-121">サーバー インスタンス上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="070c1-121">Disables the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on a server instance.</span></span>|<span data-ttu-id="070c1-122">`Path`、`InputObject`、または `Name` パラメーターによって指定されるサーバー インスタンス </span><span class="sxs-lookup"><span data-stu-id="070c1-122">The server instance that is specified by the `Path`, `InputObject`, or `Name` parameter.</span></span> <span data-ttu-id="070c1-123">( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をサポートしている [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のエディションである必要があります)。</span><span class="sxs-lookup"><span data-stu-id="070c1-123">(Must be an edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that supports [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].)</span></span>|  
|`Enable-SqlAlwaysOn`|<span data-ttu-id="070c1-124">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能をサポートしている [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンス上で [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を有効化します。</span><span class="sxs-lookup"><span data-stu-id="070c1-124">Enables [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] on an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that supports the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature.</span></span> <span data-ttu-id="070c1-125">のサポートの詳細について [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] は、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、および推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="070c1-125">For information about support for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>|<span data-ttu-id="070c1-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をサポートしている [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の任意のエディション。</span><span class="sxs-lookup"><span data-stu-id="070c1-126">Any edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that supports [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span>|  
|`New-SqlHadrEndPoint`|<span data-ttu-id="070c1-127">サーバー インスタンス上に新しいデータベース ミラーリング エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="070c1-127">Creates a new database mirroring endpoint on a server instance.</span></span> <span data-ttu-id="070c1-128">このエンドポイントは、プライマリ データベースとセカンダリ データベース間のデータ移動のために必要です。</span><span class="sxs-lookup"><span data-stu-id="070c1-128">This endpoint is required for data movement between primary and secondary databases.</span></span>|<span data-ttu-id="070c1-129">の任意のインスタンス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="070c1-129">Any instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|  
|`Set-SqlHadrEndpoint`|<span data-ttu-id="070c1-130">既存のデータベース ミラーリング エンドポイントの名前、状態、認証などのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="070c1-130">Changes the properties of an existing database mirroring endpoint, such as the name, state, or authentication properties.</span></span>|<span data-ttu-id="070c1-131">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] をサポートしていて、データベース ミラーリング エンドポイントが存在しないサーバー インスタンス。</span><span class="sxs-lookup"><span data-stu-id="070c1-131">A server instance that supports [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and lacks a database mirroring endpoint</span></span>|  
  
##  <a name="backing-up-and-restoring-databases-and-transaction-logs"></a><a name="BnRcmdlets"></a><span data-ttu-id="070c1-132">データベースとトランザクションログのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="070c1-132">Backing Up and Restoring Databases and Transaction Logs</span></span>  
  
|<span data-ttu-id="070c1-133">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="070c1-133">Cmdlets</span></span>|<span data-ttu-id="070c1-134">説明</span><span class="sxs-lookup"><span data-stu-id="070c1-134">Description</span></span>|<span data-ttu-id="070c1-135">サポート対象</span><span class="sxs-lookup"><span data-stu-id="070c1-135">Supported on</span></span>|  
|-------------|-----------------|------------------|  
|`Backup-SqlDatabase`|<span data-ttu-id="070c1-136">データまたはログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="070c1-136">Creates a data or log backup.</span></span>|<span data-ttu-id="070c1-137">任意のオンライン データベース ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の場合、プライマリ レプリカをホストしているサーバー インスタンス上のデータベース)</span><span class="sxs-lookup"><span data-stu-id="070c1-137">Any online database (for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], a database on the server instance that hosts the primary replica)</span></span>|  
|`Restore-SqlDatabase`|<span data-ttu-id="070c1-138">バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="070c1-138">Restores a backup.</span></span>|<span data-ttu-id="070c1-139">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の任意のインスタンス ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の場合、セカンダリ レプリカをホストしているサーバー インスタンス)</span><span class="sxs-lookup"><span data-stu-id="070c1-139">Any instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], a server instance that hosts a secondary replica)</span></span><br /><br /> <span data-ttu-id="070c1-140">**&#42;&#42; の重要な &#42;&#42;** セカンダリデータベースを準備するときは、 `-NoRecovery` すべてのコマンドでパラメーターを使用する必要があり `Restore-SqlDatabase` ます。</span><span class="sxs-lookup"><span data-stu-id="070c1-140">**&#42;&#42; Important &#42;&#42;** When preparing a secondary database, you must use the `-NoRecovery` parameter in every `Restore-SqlDatabase` command.</span></span>|  
  
 <span data-ttu-id="070c1-141">これらのコマンドレッドを使用してセカンダリ データベースを準備する方法の詳細については、「[可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="070c1-141">For information about using these cmdlets to prepare a secondary database, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="creating-and-managing-an-availability-group"></a><a name="DeployManageAGs"></a><span data-ttu-id="070c1-142">可用性グループの作成と管理</span><span class="sxs-lookup"><span data-stu-id="070c1-142">Creating and Managing an Availability Group</span></span>  
  
|<span data-ttu-id="070c1-143">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="070c1-143">Cmdlets</span></span>|<span data-ttu-id="070c1-144">説明</span><span class="sxs-lookup"><span data-stu-id="070c1-144">Description</span></span>|<span data-ttu-id="070c1-145">サポート対象</span><span class="sxs-lookup"><span data-stu-id="070c1-145">Supported on</span></span>|  
|-------------|-----------------|------------------|  
|`New-SqlAvailabilityGroup`|<span data-ttu-id="070c1-146">新しい可用性グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="070c1-146">Creates a new availability group.</span></span>|<span data-ttu-id="070c1-147">プライマリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-147">Server instance to host primary replica</span></span>|  
|`Remove-SqlAvailabilityGroup`|<span data-ttu-id="070c1-148">可用性グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="070c1-148">Deletes availability group.</span></span>|<span data-ttu-id="070c1-149">HADR 対応のサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-149">HADR-enabled server instance</span></span>|  
|`Set-SqlAvailabilityGroup`|<span data-ttu-id="070c1-150">可用性グループのプロパティを設定します。可用性グループをオンライン/オフラインにします。</span><span class="sxs-lookup"><span data-stu-id="070c1-150">Sets the properties of an availability group; take an availability group online/offline</span></span>|<span data-ttu-id="070c1-151">プライマリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-151">Server instance that hosts primary replica</span></span>|  
|`Switch-SqlAvailabilityGroup`|<span data-ttu-id="070c1-152">以下のいずれかの形式のフェールオーバーを開始します。</span><span class="sxs-lookup"><span data-stu-id="070c1-152">Initiates one of the following forms of failover:</span></span><br /><br /> <span data-ttu-id="070c1-153">可用性グループの強制フェールオーバー (データ損失の可能性あり)。</span><span class="sxs-lookup"><span data-stu-id="070c1-153">A forced failover of an availability group (with possible data loss).</span></span><br /><br /> <span data-ttu-id="070c1-154">可用性グループの手動フェールオーバー。</span><span class="sxs-lookup"><span data-stu-id="070c1-154">A manual failover of an availability group.</span></span>|<span data-ttu-id="070c1-155">対象のセカンダリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-155">Server instance that hosts target secondary replica</span></span>|  
  
##  <a name="creating-and-managing-an-availability-group-listener"></a><a name="AGlisteners"></a><span data-ttu-id="070c1-156">可用性グループリスナーの作成と管理</span><span class="sxs-lookup"><span data-stu-id="070c1-156">Creating and Managing an Availability Group Listener</span></span>  
  
|<span data-ttu-id="070c1-157">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="070c1-157">Cmdlet</span></span>|<span data-ttu-id="070c1-158">説明</span><span class="sxs-lookup"><span data-stu-id="070c1-158">Description</span></span>|<span data-ttu-id="070c1-159">サポート対象</span><span class="sxs-lookup"><span data-stu-id="070c1-159">Supported on</span></span>|  
|------------|-----------------|------------------|  
|`New-SqlAvailabilityGroupListener`|<span data-ttu-id="070c1-160">新しい可用性グループ リスナーを作成して、既存の可用性グループにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="070c1-160">Creates a new availability group listener and attaches it to an existing availability group.</span></span>|<span data-ttu-id="070c1-161">プライマリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-161">Server instance that hosts primary replica</span></span>|  
|`Set-SqlAvailabilityGroupListener`|<span data-ttu-id="070c1-162">既存の可用性グループ リスナーのポート設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="070c1-162">Modifies the port setting on an existing availability group listener.</span></span>|<span data-ttu-id="070c1-163">プライマリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-163">Server instance that hosts primary replica</span></span>|  
|`Add-SqlAvailabilityGroupListenerStaticIp`|<span data-ttu-id="070c1-164">既存の可用性グループ リスナー構成に静的 IP アドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="070c1-164">Adds a static IP address to an existing availability group listener configuration.</span></span> <span data-ttu-id="070c1-165">IP アドレスには、サブネットを含む IPv4 アドレス、または IPv6 アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="070c1-165">The IP address can be an IPv4 address with subnet, or an IPv6 address.</span></span>|<span data-ttu-id="070c1-166">プライマリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-166">Server instance that hosts primary replica</span></span>|  
  
##  <a name="creating-and-managing-an-availability-replica"></a><a name="DeployManageARs"></a><span data-ttu-id="070c1-167">可用性レプリカの作成と管理</span><span class="sxs-lookup"><span data-stu-id="070c1-167">Creating and Managing an Availability Replica</span></span>  
  
|<span data-ttu-id="070c1-168">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="070c1-168">Cmdlets</span></span>|<span data-ttu-id="070c1-169">説明</span><span class="sxs-lookup"><span data-stu-id="070c1-169">Description</span></span>|<span data-ttu-id="070c1-170">サポート対象</span><span class="sxs-lookup"><span data-stu-id="070c1-170">Supported on</span></span>|  
|-------------|-----------------|------------------|  
|<span data-ttu-id="070c1-171">**New-SqlAvailabilityReplica**</span><span class="sxs-lookup"><span data-stu-id="070c1-171">**New-SqlAvailabilityReplica**</span></span>|<span data-ttu-id="070c1-172">新しい可用性レプリカを作成します。</span><span class="sxs-lookup"><span data-stu-id="070c1-172">Creates a new availability replica.</span></span> <span data-ttu-id="070c1-173">`-AsTemplate` パラメーターを使用すると、新しい可用性レプリカごとにインメモリの可用性レプリカ オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="070c1-173">You can Use the `-AsTemplate` parameter to create an in-memory availability-replica object for each new availability replica.</span></span>|<span data-ttu-id="070c1-174">プライマリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-174">Server instance that hosts primary replica</span></span>|  
|`Join-SqlAvailabilityGroup`|<span data-ttu-id="070c1-175">セカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="070c1-175">Joins a secondary replica to the availability group.</span></span>|<span data-ttu-id="070c1-176">セカンダリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-176">Server instance that hosts secondary replica</span></span>|  
|<span data-ttu-id="070c1-177">**Remove-SqlAvailabilityReplica**</span><span class="sxs-lookup"><span data-stu-id="070c1-177">**Remove-SqlAvailabilityReplica**</span></span>|<span data-ttu-id="070c1-178">可用性レプリカを削除します。</span><span class="sxs-lookup"><span data-stu-id="070c1-178">Deletes an availability replica.</span></span>|<span data-ttu-id="070c1-179">プライマリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-179">Server instance that hosts primary replica</span></span>|  
|`Set-SqlAvailabilityReplica`|<span data-ttu-id="070c1-180">可用性レプリカのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="070c1-180">Sets the properties of an availability replica.</span></span>|<span data-ttu-id="070c1-181">プライマリ レプリカをホストするサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-181">Server instance that hosts primary replica</span></span>|  
  
##  <a name="adding-and-managing-an-availability-database"></a><a name="DeployManageDbs"></a><span data-ttu-id="070c1-182">可用性データベースの追加と管理</span><span class="sxs-lookup"><span data-stu-id="070c1-182">Adding and Managing an Availability Database</span></span>  
  
|<span data-ttu-id="070c1-183">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="070c1-183">Cmdlets</span></span>|<span data-ttu-id="070c1-184">説明</span><span class="sxs-lookup"><span data-stu-id="070c1-184">Description</span></span>|<span data-ttu-id="070c1-185">サポート対象</span><span class="sxs-lookup"><span data-stu-id="070c1-185">Supported on</span></span>|  
|-------------|-----------------|------------------|  
|<span data-ttu-id="070c1-186">**Add-SqlAvailabilityDatabase**</span><span class="sxs-lookup"><span data-stu-id="070c1-186">**Add-SqlAvailabilityDatabase**</span></span>|<span data-ttu-id="070c1-187">プライマリ レプリカ上で、データベースを可用性グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="070c1-187">On the primary replica, adds a database to an availability group.</span></span><br /><br /> <span data-ttu-id="070c1-188">セカンダリ レプリカ上で、セカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="070c1-188">On a secondary replica, joins a secondary database to an availability group.</span></span>|<span data-ttu-id="070c1-189">可用性レプリカをホストする任意のサーバー インスタンス (レプリカがプライマリかセカンダリかで動作が異なります)</span><span class="sxs-lookup"><span data-stu-id="070c1-189">Any server instance that hosts an availability replica (behavior differs for primary and secondary replicas)</span></span>|  
|<span data-ttu-id="070c1-190">**Remove-SqlAvailabilityDatabase**</span><span class="sxs-lookup"><span data-stu-id="070c1-190">**Remove-SqlAvailabilityDatabase**</span></span>|<span data-ttu-id="070c1-191">プライマリ レプリカ上で、可用性グループからデータベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="070c1-191">On the primary replica, removes the database from the availability group.</span></span><br /><br /> <span data-ttu-id="070c1-192">セカンダリ レプリカ上で、ローカル セカンダリ データベースをローカル セカンダリ レプリカから削除します。</span><span class="sxs-lookup"><span data-stu-id="070c1-192">On a secondary replica, removes the local secondary database from the local secondary replica.</span></span>|<span data-ttu-id="070c1-193">可用性レプリカをホストする任意のサーバー インスタンス (レプリカがプライマリかセカンダリかで動作が異なります)</span><span class="sxs-lookup"><span data-stu-id="070c1-193">Any server instance that hosts an availability replica (behavior differs for primary and secondary replicas)</span></span>|  
|`Resume-SqlAvailabilityDatabase`|<span data-ttu-id="070c1-194">中断されている可用性データベースのデータ移動を再開します。</span><span class="sxs-lookup"><span data-stu-id="070c1-194">Resumes the data movement for a suspended availability database.</span></span>|<span data-ttu-id="070c1-195">データベースが中断されたサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-195">The server instance on which the database was suspended.</span></span>|  
|`Suspend-SqlAvailabilityDatabase`|<span data-ttu-id="070c1-196">可用性データベースのデータ移動を中断します。</span><span class="sxs-lookup"><span data-stu-id="070c1-196">Suspends the data movement for an availability database.</span></span>|<span data-ttu-id="070c1-197">可用性レプリカをホストする任意のサーバー インスタンス</span><span class="sxs-lookup"><span data-stu-id="070c1-197">Any server instance that hosts an availability replica.</span></span>|  
  
##  <a name="monitoring-availability-group-health"></a><a name="MonitorTblshtAGs"></a><span data-ttu-id="070c1-198">監視可用性グループヘルス</span><span class="sxs-lookup"><span data-stu-id="070c1-198">Monitoring Availability Group Health</span></span>  
 <span data-ttu-id="070c1-199">以下の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コマンドレットを使用すると、可用性グループとそのレプリカおよびデータベースの正常性を監視できます。</span><span class="sxs-lookup"><span data-stu-id="070c1-199">The following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlets enable you to monitor the health of an availability group and its replicas and databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="070c1-200">これらのコマンドレットを実行するには、CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="070c1-200">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute these cmdlets.</span></span>  
  
|<span data-ttu-id="070c1-201">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="070c1-201">Cmdlet</span></span>|<span data-ttu-id="070c1-202">説明</span><span class="sxs-lookup"><span data-stu-id="070c1-202">Description</span></span>|<span data-ttu-id="070c1-203">サポート対象</span><span class="sxs-lookup"><span data-stu-id="070c1-203">Supported on</span></span>|  
|------------|-----------------|------------------|  
|`Test-SqlAvailabilityGroup`|<span data-ttu-id="070c1-204">SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性グループの正常性を査定します。</span><span class="sxs-lookup"><span data-stu-id="070c1-204">Assesses the health of an availability group by evaluating SQL Server policy based management (PBM) policies.</span></span>|<span data-ttu-id="070c1-205">可用性レプリカをホストする任意のサーバー インスタンス。\*</span><span class="sxs-lookup"><span data-stu-id="070c1-205">Any server instance that hosts an availability replica.\*</span></span>|  
|`Test-SqlAvailabilityReplica`|<span data-ttu-id="070c1-206">SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性レプリカの正常性を査定します。</span><span class="sxs-lookup"><span data-stu-id="070c1-206">Assesses the health of availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span>|<span data-ttu-id="070c1-207">可用性レプリカをホストする任意のサーバー インスタンス。\*</span><span class="sxs-lookup"><span data-stu-id="070c1-207">Any server instance that hosts an availability replica.\*</span></span>|  
|`Test-SqlDatabaseReplicaState`|<span data-ttu-id="070c1-208">SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、参加しているすべての可用性レプリカ上の可用性データベースの正常性を査定します。</span><span class="sxs-lookup"><span data-stu-id="070c1-208">Assesses the health of an availability database on all joined availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span>|<span data-ttu-id="070c1-209">可用性レプリカをホストする任意のサーバー インスタンス。\*</span><span class="sxs-lookup"><span data-stu-id="070c1-209">Any server instance that hosts an availability replica.\*</span></span>|  
  
 <span data-ttu-id="070c1-210">\* 可用性グループ内のすべての可用性レプリカについての情報を表示するには、プライマリ レプリカをホストするサーバー インスタンスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="070c1-210">\*To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
 <span data-ttu-id="070c1-211">詳細については、「 [AlwaysOn ポリシーを使用して可用性グループの正常性を表示する」 &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="070c1-211">For more information, see [Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070c1-212">参照</span><span class="sxs-lookup"><span data-stu-id="070c1-212">See Also</span></span>  
 <span data-ttu-id="070c1-213">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="070c1-213">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="070c1-214">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="070c1-214">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
  