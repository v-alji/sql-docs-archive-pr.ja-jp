---
title: 可用性グループの作成 (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3af9bf896b954e6849c0d491f9ed267655369ccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743458"
---
# <a name="create-an-availability-group-sql-server-powershell"></a><span data-ttu-id="570fc-102">可用性グループの作成 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="570fc-102">Create an Availability Group (SQL Server PowerShell)</span></span>
  <span data-ttu-id="570fc-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の AlwaysOn 可用性グループを PowerShell コマンドレットで作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="570fc-103">This topic describes how to use PowerShell cmdlets to create and configure an AlwaysOn availability group by using PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="570fc-104">*可用性グループ* は、1 つのまとまりとしてフェールオーバーする一連のユーザー データベースと、フェールオーバーをサポートする一連のフェールオーバー パートナー ( *可用性レプリカ*) を定義します。</span><span class="sxs-lookup"><span data-stu-id="570fc-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, which support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="570fc-105">可用性グループの概要については、「[AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="570fc-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  

> [!NOTE]  
>  <span data-ttu-id="570fc-106">PowerShell のコマンドレットの代わりに、可用性グループの作成ウィザードや [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="570fc-106">As an alternative to using PowerShell cmdlets, you can use the Create Availability Group wizard or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="570fc-107">詳細については、「 [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 」または「 [可用性グループの作成 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)の Always On 可用性グループを PowerShell コマンドレットで作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="570fc-107">For more information, see [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) or [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="570fc-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="570fc-108">Before You Begin</span></span>  
 <span data-ttu-id="570fc-109">可用性グループを初めて作成する場合は、あらかじめこのセクションに目を通しておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="570fc-109">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="570fc-110">前提条件、制限事項、および推奨事項</span><span class="sxs-lookup"><span data-stu-id="570fc-110">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="570fc-111">可用性グループを作成する前に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の各ホスト インスタンスが、同じ Windows Server Failover Clustering (WSFC) フェールオーバー クラスタリングのそれぞれ異なる WSFC ノードに存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="570fc-111">Before creating an availability group, verify that the host instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] each resides on a different Windows Server Failover Clustering (WSFC) node of a single WSFC failover cluster.</span></span> <span data-ttu-id="570fc-112">また、使用するサーバー インスタンスが、他のサーバー インスタンスの前提条件を満たしていることと、他の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の要件がすべて満たされていること、さらに、自分自身も推奨事項を認識していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="570fc-112">Also, verify that your server instances met the other server-instance prerequisites and that all of the other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] requirements are meet and that you are aware of the recommendations.</span></span> <span data-ttu-id="570fc-113">詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」をお読みいただくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="570fc-113">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="570fc-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="570fc-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="570fc-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="570fc-115">Permissions</span></span>  
 <span data-ttu-id="570fc-116">**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="570fc-116">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
###  <a name="summary-of-tasks-and-corresponding-powershell-cmdlets"></a><a name="SummaryPSStatements"></a><span data-ttu-id="570fc-117">タスクとそれに対応する PowerShell コマンドレットの概要</span><span class="sxs-lookup"><span data-stu-id="570fc-117">Summary of Tasks and Corresponding PowerShell Cmdlets</span></span>  
 <span data-ttu-id="570fc-118">次の表は、可用性グループの構成に伴う基本的な作業の一覧です。一覧には PowerShell コマンドレットによってサポートされる作業が示されています。</span><span class="sxs-lookup"><span data-stu-id="570fc-118">The following table lists the basic tasks involved in configuring an availability group and indicates those that are supported by PowerShell cmdlets.</span></span> <span data-ttu-id="570fc-119">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に関連したこれらの作業は、この表に示されている順に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="570fc-119">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks must be performed in the sequence in which they are presented in the table.</span></span>  
  
|<span data-ttu-id="570fc-120">タスク</span><span class="sxs-lookup"><span data-stu-id="570fc-120">Task</span></span>|<span data-ttu-id="570fc-121">PowerShell コマンドレット (利用可能な場合) または Transact SQL ステートメント</span><span class="sxs-lookup"><span data-stu-id="570fc-121">PowerShell Cmdlets (if Available) or Transact-SQL Statement</span></span>|<span data-ttu-id="570fc-122">タスクを実行する場所**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="570fc-122">Where to Perform Task**<sup>\*</sup>**</span></span>|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|<span data-ttu-id="570fc-123">データベース ミラーリング エンドポイントを作成する ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスごとに 1 回)</span><span class="sxs-lookup"><span data-stu-id="570fc-123">Create database mirroring endpoint (once per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance)</span></span>|`New-SqlHadrEndPoint`|<span data-ttu-id="570fc-124">データベース ミラーリング エンドポイントが欠落している各サーバー インスタンスで実行します。</span><span class="sxs-lookup"><span data-stu-id="570fc-124">Execute on each server instance that lacks database mirroring endpoint.</span></span><br /><br /> <span data-ttu-id="570fc-125">注: 既存のデータベース ミラーリング エンドポイントに変更を加えるには、`Set-SqlHadrEndpoint` を使用します。</span><span class="sxs-lookup"><span data-stu-id="570fc-125">Note: To alter an existing database mirroring endpoint, use `Set-SqlHadrEndpoint`.</span></span>|  
|<span data-ttu-id="570fc-126">可用性グループを作成する</span><span class="sxs-lookup"><span data-stu-id="570fc-126">Create availability group</span></span>|<span data-ttu-id="570fc-127">まず、`New-SqlAvailabilityReplica` コマンドレットに `-AsTemplate` パラメーターを指定し、可用性グループに追加する予定の 2 つの可用性レプリカのそれぞれについて、インメモリの可用性レプリカ オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-127">First, use the `New-SqlAvailabilityReplica` cmdlet with the `-AsTemplate` parameter to create an in-memory availability-replica object for each of the two availability replicas that you plan to include in the availability group.</span></span><br /><br /> <span data-ttu-id="570fc-128">次に、`New-SqlAvailabilityGroup` コマンドレットを使用し、可用性レプリカ オブジェクトを参照して、可用性グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-128">Then, create the availability group by using the `New-SqlAvailabilityGroup` cmdlet and referencing your availability-replica objects.</span></span>|<span data-ttu-id="570fc-129">初期プライマリ レプリカをホストするサーバー インスタンスで実行します。</span><span class="sxs-lookup"><span data-stu-id="570fc-129">Execute on the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="570fc-130">セカンダリ レプリカを可用性グループに参加させる</span><span class="sxs-lookup"><span data-stu-id="570fc-130">Join secondary replica to availability group</span></span>|`Join-SqlAvailabilityGroup`|<span data-ttu-id="570fc-131">セカンダリ レプリカをホストする各サーバー インスタンスで実行します。</span><span class="sxs-lookup"><span data-stu-id="570fc-131">Execute on each server instance that is hosts a secondary replica.</span></span>|  
|<span data-ttu-id="570fc-132">セカンダリ データベースを準備する</span><span class="sxs-lookup"><span data-stu-id="570fc-132">Prepare the secondary database</span></span>|<span data-ttu-id="570fc-133">`Backup-SqlDatabase` および `Restore-SqlDatabase`</span><span class="sxs-lookup"><span data-stu-id="570fc-133">`Backup-SqlDatabase` and `Restore-SqlDatabase`</span></span>|<span data-ttu-id="570fc-134">プライマリ レプリカをホストするサーバー インスタンスでバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-134">Create backups on the server instance that hosts the primary replica.</span></span><br /><br /> <span data-ttu-id="570fc-135">セカンダリ レプリカをホストする各サーバー インスタンス上で、`NoRecovery` 復元パラメーターを使用してバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="570fc-135">Restore backups on each server instance that hosts a secondary replica, using the `NoRecovery` restore parameter.</span></span> <span data-ttu-id="570fc-136">プライマリ レプリカをホストするコンピューターとターゲット セカンダリ レプリカをホストするコンピューターとでファイル パスが異なる場合は、`RelocateFile` 復元パラメーターも使用します。</span><span class="sxs-lookup"><span data-stu-id="570fc-136">If the file paths differ between the computers that host the primary replica and the target secondary replica, also use the `RelocateFile` restore parameter.</span></span>|  
|<span data-ttu-id="570fc-137">各セカンダリ データベースを可用性グループに参加させてデータ同期を開始する</span><span class="sxs-lookup"><span data-stu-id="570fc-137">Start data synchronization by joining each secondary database to availability group</span></span>|`Add-SqlAvailabilityDatabase`|<span data-ttu-id="570fc-138">セカンダリ レプリカをホストする各サーバー インスタンスで実行します。</span><span class="sxs-lookup"><span data-stu-id="570fc-138">Execute on each server instance that hosts a secondary replica.</span></span>|  
  
 <span data-ttu-id="570fc-139">**<sup>\*</sup>** 特定のタスクを実行するには、指定された `cd` サーバーインスタンスにディレクトリ () を変更します。</span><span class="sxs-lookup"><span data-stu-id="570fc-139">**<sup>\*</sup>**  To perform a given task, change directory (`cd`) to the indicated server instance or instances.</span></span>  
  
###  <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><a name="PsProviderLinks"></a><span data-ttu-id="570fc-140">SQL Server PowerShell プロバイダーを設定して使用するには</span><span class="sxs-lookup"><span data-stu-id="570fc-140">To Set Up and Use the SQL Server PowerShell Provider</span></span>  
  
-   [<span data-ttu-id="570fc-141">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="570fc-141">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="570fc-142">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="570fc-142">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="using-powershell-to-create-and-configure-an-availability-group"></a><a name="PowerShellProcedure"></a><span data-ttu-id="570fc-143">PowerShell を使用した可用性グループの作成と構成</span><span class="sxs-lookup"><span data-stu-id="570fc-143">Using PowerShell to Create and Configure an Availability Group</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="570fc-144">特定のコマンドレットの構文や例を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="570fc-144">To view the syntax and an example of a given cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="570fc-145">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="570fc-145">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
1.  <span data-ttu-id="570fc-146">`cd`プライマリレプリカをホストするサーバーインスタンスにディレクトリを変更 () します。</span><span class="sxs-lookup"><span data-stu-id="570fc-146">Change directory (`cd`) to the server instance that is to host the primary replica.</span></span>  
  
2.  <span data-ttu-id="570fc-147">プライマリ レプリカのインメモリの可用性レプリカ オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-147">Create an in-memory availability-replica object for the primary replica.</span></span>  
  
3.  <span data-ttu-id="570fc-148">セカンダリ レプリカごとにインメモリの可用性レプリカ オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-148">Create an in-memory availability-replica object for each of the secondary replicas.</span></span>  
  
4.  <span data-ttu-id="570fc-149">可用性グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-149">Create the availability group.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="570fc-150">可用性グループ名の最大文字数は 128 文字です。</span><span class="sxs-lookup"><span data-stu-id="570fc-150">The maximum length for an availability group name is 128 characters.</span></span>  
  
5.  <span data-ttu-id="570fc-151">新しいセカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="570fc-151">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="570fc-152">詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="570fc-152">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
6.  <span data-ttu-id="570fc-153">可用性グループ内の各データベースについて、セカンダリ データベースを作成します。これは、プライマリ データベースの最新のバックアップを、RESTORE WITH NORECOVERY で復元することによって行います。</span><span class="sxs-lookup"><span data-stu-id="570fc-153">For each database in the availability group, create a secondary database by restoring recent backups of the primary database, using RESTORE WITH NORECOVERY.</span></span>  
  
7.  <span data-ttu-id="570fc-154">新しいセカンダリ データベースをすべて可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="570fc-154">Join every new secondary database to the availability group.</span></span> <span data-ttu-id="570fc-155">詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="570fc-155">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="570fc-156">必要に応じて、Windows の `dir` コマンドを使用し、新しい可用性グループの内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="570fc-156">Optionally, use the Windows `dir` command to verify the contents of the new availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="570fc-157">複数のサーバー インスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントが、それぞれ異なるドメイン ユーザー アカウントで実行されている場合、それぞれのサーバー インスタンス上に、もう一方のサーバー インスタンス用のログインを作成し、そのログインにローカルのデータベース ミラーリング エンドポイントへの CONNECT 権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="570fc-157">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service accounts of the server instances run under different domain user accounts, on each server instance, create a login for the other server instance and grant this login CONNECT permission to the local database mirroring endpoint.</span></span>  
  
##  <a name="example-using-powershell-to-create-an-availability-group"></a><a name="ExampleConfigureGroup"></a><span data-ttu-id="570fc-158">例: PowerShell を使用した可用性グループの作成</span><span class="sxs-lookup"><span data-stu-id="570fc-158">Example: Using PowerShell to Create an Availability Group</span></span>  
 <span data-ttu-id="570fc-159">以下の PowerShell スクリプトは、2 つの可用性レプリカと 1 つの可用性データベースから成る `MyAG` という名前の単純な可用性グループを作成、構成する例です。</span><span class="sxs-lookup"><span data-stu-id="570fc-159">The following PowerShell example creates and configures a simple availability group named `MyAG` with two availability replicas and one availability database.</span></span> <span data-ttu-id="570fc-160">この例では、次の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="570fc-160">The example:</span></span>  
  
1.  <span data-ttu-id="570fc-161">`MyDatabase` とそのトランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="570fc-161">Backs up `MyDatabase` and its transaction log.</span></span>  
  
2.  <span data-ttu-id="570fc-162">`MyDatabase` とそのトランザクション ログを `-NoRecovery` オプションを使用して復元します。</span><span class="sxs-lookup"><span data-stu-id="570fc-162">Restores `MyDatabase` and its transaction log, using the `-NoRecovery` option.</span></span>  
  
3.  <span data-ttu-id="570fc-163">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンス (名前は `PrimaryComputer\Instance`) によってホストされるプライマリ レプリカのメモリ内表現を作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-163">Creates an in-memory representation of the primary replica, which will be hosted by the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (named `PrimaryComputer\Instance`).</span></span>  
  
4.  <span data-ttu-id="570fc-164">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス (名前は `SecondaryComputer\Instance`) によってホストされるセカンダリ レプリカのメモリ内表現を作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-164">Creates an in-memory representation of the secondary replica, which will be hosted by an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (named `SecondaryComputer\Instance`).</span></span>  
  
5.  <span data-ttu-id="570fc-165">`MyAG`という名前の可用性グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="570fc-165">Creates an availability group named `MyAG`.</span></span>  
  
6.  <span data-ttu-id="570fc-166">セカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="570fc-166">Joins the secondary replica to the availability group.</span></span>  
  
7.  <span data-ttu-id="570fc-167">セカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="570fc-167">Joins the secondary database to the availability group.</span></span>  
  
```powershell
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="570fc-168">関連タスク</span><span class="sxs-lookup"><span data-stu-id="570fc-168">Related Tasks</span></span>  
 <span data-ttu-id="570fc-169">**AlwaysOn 可用性グループのサーバー インスタンスを構成するには**</span><span class="sxs-lookup"><span data-stu-id="570fc-169">**To configure a server instance for AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="570fc-170">AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-170">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="570fc-171">AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-171">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
 <span data-ttu-id="570fc-172">**可用性グループおよびレプリカのプロパティを構成するには**</span><span class="sxs-lookup"><span data-stu-id="570fc-172">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="570fc-173">可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-173">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="570fc-174">可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-174">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="570fc-175">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-175">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="570fc-176">自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 (AlwaysOn 可用性グループ)</span><span class="sxs-lookup"><span data-stu-id="570fc-176">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="570fc-177">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-177">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="570fc-178">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-178">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="570fc-179">可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-179">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="570fc-180">可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-180">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="570fc-181">可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-181">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="570fc-182">**可用性グループの構成を完了するには**</span><span class="sxs-lookup"><span data-stu-id="570fc-182">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="570fc-183">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-183">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="570fc-184">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-184">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="570fc-185">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-185">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="570fc-186">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-186">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="570fc-187">**別の方法で可用性グループを作成する**</span><span class="sxs-lookup"><span data-stu-id="570fc-187">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="570fc-188">可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-188">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   <span data-ttu-id="570fc-189">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="570fc-189">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="570fc-190">可用性グループの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-190">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
 <span data-ttu-id="570fc-191">**AlwaysOn 可用性グループの構成のトラブルシューティング方法**</span><span class="sxs-lookup"><span data-stu-id="570fc-191">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="570fc-192">AlwaysOn 可用性グループ構成 (SQL Server) の削除に関するトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="570fc-192">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="570fc-193">失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-193">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="570fc-194">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="570fc-194">Related Content</span></span>  
  
-   <span data-ttu-id="570fc-195">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="570fc-195">**Blogs:**</span></span>  
  
     [<span data-ttu-id="570fc-196">AlwaysON - HADRON 学習シリーズ:HADRON 対応データベースでのワーカー プールの使用</span><span class="sxs-lookup"><span data-stu-id="570fc-196">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="570fc-197">Configuring AlwaysOn with SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="570fc-197">Configuring AlwaysOn with SQL Server PowerShell</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [<span data-ttu-id="570fc-198">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="570fc-198">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="570fc-199">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="570fc-199">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="570fc-200">**ビデオ:**</span><span class="sxs-lookup"><span data-stu-id="570fc-200">**Videos:**</span></span>  
  
     [<span data-ttu-id="570fc-201">Microsoft SQL Server コード ネーム "Denali" AlwaysOn シリーズ パート 1: 次世代の高可用性ソリューションの概要</span><span class="sxs-lookup"><span data-stu-id="570fc-201">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="570fc-202">Microsoft SQL Server コードネーム "Denali" AlwaysOn シリーズ パート 2: AlwaysOn を使用したミッション クリティカルな高可用性ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="570fc-202">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="570fc-203">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="570fc-203">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="570fc-204">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="570fc-204">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="570fc-205">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="570fc-205">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="570fc-206">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="570fc-206">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="570fc-207">参照</span><span class="sxs-lookup"><span data-stu-id="570fc-207">See Also</span></span>  
 [<span data-ttu-id="570fc-208">データベース ミラーリング エンドポイント &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="570fc-208">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
