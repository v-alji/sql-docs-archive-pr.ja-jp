---
title: 可用性グループの作成 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 8b0a6301-8b79-4415-b608-b40876f30066
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57a494af168a8f5572bafe93f8fb47b22a954a19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743453"
---
# <a name="create-an-availability-group-transact-sql"></a><span data-ttu-id="73666-102">可用性グループの作成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="73666-102">Create an Availability Group (Transact-SQL)</span></span>
  <span data-ttu-id="73666-103">このトピックでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 機能を有効にする [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンス上で可用性グループを作成および構成するために [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73666-103">This topic describes how to use [!INCLUDE[tsql](../../../includes/tsql-md.md)] to create and configure an availability group on instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] on which the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature is enabled.</span></span> <span data-ttu-id="73666-104">*可用性グループ* は、1 つのまとまりとしてフェールオーバーする一連のユーザー データベースと、フェールオーバーをサポートする一連のフェールオーバー パートナー ( *可用性レプリカ*) を定義します。</span><span class="sxs-lookup"><span data-stu-id="73666-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73666-105">可用性グループの概要については、「[AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73666-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  

> [!NOTE]  
>  <span data-ttu-id="73666-106">[!INCLUDE[tsql](../../../includes/tsql-md.md)]の代わりに、可用性グループの作成ウィザードまたは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell コマンドレットを使用する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="73666-106">As an alternative to using [!INCLUDE[tsql](../../../includes/tsql-md.md)], you can use the Create Availability Group wizard or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlets.</span></span> <span data-ttu-id="73666-107">詳細については、「 [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)」、「 [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)」、または「 [可用性グループの作成 &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73666-107">For more information, see [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md), [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md), or [Create an Availability Group &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="73666-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="73666-108">Before You Begin</span></span>  
 <span data-ttu-id="73666-109">可用性グループを初めて作成する場合は、あらかじめこのセクションに目を通しておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="73666-109">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a><span data-ttu-id="73666-110">前提条件、制限事項、および推奨事項</span><span class="sxs-lookup"><span data-stu-id="73666-110">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="73666-111">可用性グループを作成する前に、可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが同じ Windows Server フェールオーバー クラスタリング (WSFC) フェールオーバー クラスター内の別の WSFC ノードに存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="73666-111">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="73666-112">また、各サーバー インスタンスが [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の他のすべての前提条件を満たしていることも確認します。</span><span class="sxs-lookup"><span data-stu-id="73666-112">Also, verify that each of the server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="73666-113">詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」をお読みいただくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="73666-113">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="73666-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="73666-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="73666-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="73666-115">Permissions</span></span>  
 <span data-ttu-id="73666-116">**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="73666-116">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
###  <a name="summary-of-tasks-and-corresponding-transact-sql-statements"></a><a name="SummaryTsqlStatements"></a><span data-ttu-id="73666-117">タスクとそれに対応する Transact-sql ステートメントの概要</span><span class="sxs-lookup"><span data-stu-id="73666-117">Summary of Tasks and Corresponding Transact-SQL Statements</span></span>  
 <span data-ttu-id="73666-118">次の表は、可用性グループの作成と構成に伴う基本的な作業と、これらの作業に使用する [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントの一覧です。</span><span class="sxs-lookup"><span data-stu-id="73666-118">The following table lists the basic tasks involved in creating and configuring an availability group and indicates which [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements to use for these tasks.</span></span> <span data-ttu-id="73666-119">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に関連したこれらの作業は、この表に示されている順に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73666-119">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks must be performed in the sequence in which they are presented in the table.</span></span>  
  
|<span data-ttu-id="73666-120">タスク</span><span class="sxs-lookup"><span data-stu-id="73666-120">Task</span></span>|<span data-ttu-id="73666-121">Transact-SQL ステートメント</span><span class="sxs-lookup"><span data-stu-id="73666-121">Transact-SQL Statement(s)</span></span>|<span data-ttu-id="73666-122">タスクを実行する場所**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="73666-122">Where to Perform Task**<sup>\*</sup>**</span></span>|  
|----------|----------------------------------|-------------------------------------------|  
|<span data-ttu-id="73666-123">データベース ミラーリング エンドポイントを作成する ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスごとに 1 回)</span><span class="sxs-lookup"><span data-stu-id="73666-123">Create database mirroring endpoint (once per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance)</span></span>|<span data-ttu-id="73666-124">[エンドポイント](/sql/t-sql/statements/create-endpoint-transact-sql) *endpointName*の作成...DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="73666-124">[CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql) *endpointName* ... FOR DATABASE_MIRRORING</span></span>|<span data-ttu-id="73666-125">データベース ミラーリング エンドポイントが欠落している各サーバー インスタンスで実行します。</span><span class="sxs-lookup"><span data-stu-id="73666-125">Execute on each server instance that lacks database mirroring endpoint.</span></span>|  
|<span data-ttu-id="73666-126">可用性グループを作成する</span><span class="sxs-lookup"><span data-stu-id="73666-126">Create availability group</span></span>|[<span data-ttu-id="73666-127">CREATE AVAILABILITY GROUP</span><span class="sxs-lookup"><span data-stu-id="73666-127">CREATE AVAILABILITY GROUP</span></span>](/sql/t-sql/statements/create-availability-group-transact-sql)|<span data-ttu-id="73666-128">初期プライマリ レプリカをホストするサーバー インスタンスで実行します。</span><span class="sxs-lookup"><span data-stu-id="73666-128">Execute on the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="73666-129">セカンダリ レプリカを可用性グループに参加させる</span><span class="sxs-lookup"><span data-stu-id="73666-129">Join secondary replica to availability group</span></span>|<span data-ttu-id="73666-130">[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *group_name* JOIN</span><span class="sxs-lookup"><span data-stu-id="73666-130">[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *group_name* JOIN</span></span>|<span data-ttu-id="73666-131">セカンダリ レプリカをホストする各サーバー インスタンスで実行します。</span><span class="sxs-lookup"><span data-stu-id="73666-131">Execute on each server instance that hosts a secondary replica.</span></span>|  
|<span data-ttu-id="73666-132">セカンダリ データベースを準備する</span><span class="sxs-lookup"><span data-stu-id="73666-132">Prepare the secondary database</span></span>|<span data-ttu-id="73666-133">[バックアップ](/sql/t-sql/statements/backup-transact-sql)と[復元](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="73666-133">[BACKUP](/sql/t-sql/statements/backup-transact-sql) and [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>|<span data-ttu-id="73666-134">プライマリ レプリカをホストするサーバー インスタンスでバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-134">Create backups on the server instance that hosts the primary replica.</span></span><br /><br /> <span data-ttu-id="73666-135">セカンダリ レプリカをホストする各サーバー インスタンス上で、RESTORE WITH NORECOVERY を使用してバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="73666-135">Restore backups on each server instance that hosts a secondary replica, using RESTORE WITH NORECOVERY.</span></span>|  
|<span data-ttu-id="73666-136">各セカンダリ データベースを可用性グループに参加させてデータ同期を開始する</span><span class="sxs-lookup"><span data-stu-id="73666-136">Start data synchronization by joining each secondary database to availability group</span></span>|<span data-ttu-id="73666-137">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span><span class="sxs-lookup"><span data-stu-id="73666-137">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span></span>|<span data-ttu-id="73666-138">セカンダリ レプリカをホストする各サーバー インスタンスで実行します。</span><span class="sxs-lookup"><span data-stu-id="73666-138">Execute on each server instance that hosts a secondary replica.</span></span>|  
  
 <span data-ttu-id="73666-139">**<sup>\*</sup>** 特定のタスクを実行するには、指定されたサーバーインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73666-139">**<sup>\*</sup>**  To perform a given task, connect to the indicated server instance or instances.</span></span>  
  
##  <a name="using-transact-sql-to-create-and-configure-an-availability-group"></a><a name="TsqlProcedure"></a> <span data-ttu-id="73666-140">Transact-SQL を使用した可用性グループの作成と構成</span><span class="sxs-lookup"><span data-stu-id="73666-140">Using Transact-SQL to Create and Configure an Availability Group</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73666-141"> 「 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 例: Windows 認証を使用した可用性グループの構成 [」では、以上に示した各](#ExampleConfigAGWinAuth)ステートメントのコード例を交えながらサンプル構成プロシージャを紹介しています。</span><span class="sxs-lookup"><span data-stu-id="73666-141">For a sample configuration procedure containing code examples of each these [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements, see [Example: Configuring an Availability Group that Uses Windows Authentication](#ExampleConfigAGWinAuth).</span></span>  
  
1.  <span data-ttu-id="73666-142">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73666-142">Connect to the server instance that is to host the primary replica.</span></span>  
  
2.  <span data-ttu-id="73666-143">[CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql)ステートメントを使用して可用性グループを作成し [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="73666-143">Create the availability group by using the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
3.  <span data-ttu-id="73666-144">新しいセカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="73666-144">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="73666-145">詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73666-145">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="73666-146">可用性グループ内の各データベースについて、セカンダリ データベースを作成します。これは、プライマリ データベースの最新のバックアップを、RESTORE WITH NORECOVERY で復元することによって行います。</span><span class="sxs-lookup"><span data-stu-id="73666-146">For each database in the availability group, create a secondary database by restoring recent backups of the primary database, using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="73666-147">詳細については、「 [例: Windows 認証を使用した可用性グループの構成 (Transact-SQL)](create-an-availability-group-transact-sql.md)」で、データベース バックアップの復元手順をまず参照してください。</span><span class="sxs-lookup"><span data-stu-id="73666-147">For more information, see [Example: Setting Up an Availability Group Using Windows Authentication (Transact-SQL)](create-an-availability-group-transact-sql.md), starting with the step that restores the database backup.</span></span>  
  
5.  <span data-ttu-id="73666-148">新しいセカンダリ データベースをすべて可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="73666-148">Join every new secondary database to the availability group.</span></span> <span data-ttu-id="73666-149">詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73666-149">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="example-configuring-an-availability-group-that-uses-windows-authentication"></a><a name="ExampleConfigAGWinAuth"></a><span data-ttu-id="73666-150">例: Windows 認証を使用する可用性グループの構成</span><span class="sxs-lookup"><span data-stu-id="73666-150">Example: Configuring an Availability Group that Uses Windows Authentication</span></span>  
 <span data-ttu-id="73666-151">この例では、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 構成プロシージャのサンプルを作成します。サンプルでは、Windows 認証を使用するデータベース ミラーリング エンドポイントのセットアップ、さらには、可用性グループとそのセカンダリ データベースの作成と構成を [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="73666-151">This example creates a sample [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] configuration procedure that uses [!INCLUDE[tsql](../../../includes/tsql-md.md)] to set up database mirroring endpoints that use Windows Authentication and to create and configure an availability group and its secondary databases.</span></span>  
  
 <span data-ttu-id="73666-152">この例の内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="73666-152">This example contains the following sections:</span></span>  
  
-   [<span data-ttu-id="73666-153">サンプル構成プロシージャを使用するうえでの前提条件</span><span class="sxs-lookup"><span data-stu-id="73666-153">Prerequisites for Using the Sample Configuration Procedure</span></span>](#PrerequisitesForExample)  
  
-   [<span data-ttu-id="73666-154">サンプル構成プロシージャ</span><span class="sxs-lookup"><span data-stu-id="73666-154">Sample Configuration Procedure</span></span>](#SampleProcedure)  
  
-   [<span data-ttu-id="73666-155">サンプル構成プロシージャの完全なコード例</span><span class="sxs-lookup"><span data-stu-id="73666-155">Complete Code Example for Sample Configuration Procedure</span></span>](#CompleteCodeExample)  
  
###  <a name="prerequisites-for-using-the-sample-configuration-procedure"></a><a name="PrerequisitesForExample"></a><span data-ttu-id="73666-156">サンプル構成プロシージャを使用するための前提条件</span><span class="sxs-lookup"><span data-stu-id="73666-156">Prerequisites for Using the Sample Configuration Procedure</span></span>  
 <span data-ttu-id="73666-157">このサンプル プロシージャには、次の要件があります。</span><span class="sxs-lookup"><span data-stu-id="73666-157">This sample procedure has the following requirements:</span></span>  
  
-   <span data-ttu-id="73666-158">サーバー インスタンスは [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="73666-158">The server instances must support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="73666-159">詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73666-159">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="73666-160">2 つのサンプル データベース ( *MyDb1* および *MyDb2*) が、プライマリ レプリカをホストするサーバー インスタンス上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73666-160">Two sample databases, *MyDb1* and *MyDb2*, must exist on the server instance that will host the primary replica.</span></span> <span data-ttu-id="73666-161">次のコード例では、これらの 2 つのデータベースを作成、構成し、それぞれの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-161">The following code examples create and configure these two databases and create a full backup of each.</span></span> <span data-ttu-id="73666-162">これらのコード例は、サンプルの可用性グループの作成先となるサーバー インスタンス上で実行します。</span><span class="sxs-lookup"><span data-stu-id="73666-162">Execute these code examples on the server instance on which you intend to create the sample availability group.</span></span> <span data-ttu-id="73666-163">サンプル可用性グループの初期プライマリ レプリカは、このサーバー インスタンスでホストされます。</span><span class="sxs-lookup"><span data-stu-id="73666-163">This server instance will host the initial primary replica of the sample availability group.</span></span>  
  
    1.  <span data-ttu-id="73666-164">次の例の [!INCLUDE[tsql](../../../includes/tsql-md.md)] では、これらのデータベースを作成し、完全復旧モデルを使用するように変更を加えています。</span><span class="sxs-lookup"><span data-stu-id="73666-164">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] example creates these databases and alters them to use the full recovery model:</span></span>  
  
        ```sql
        -- Create sample databases:  
        CREATE DATABASE MyDb1;  
        GO  
        ALTER DATABASE MyDb1 SET RECOVERY FULL;  
        GO  
  
        CREATE DATABASE MyDb2;  
        GO  
        ALTER DATABASE MyDb2 SET RECOVERY FULL;  
        GO  
        ```  
  
    2.  <span data-ttu-id="73666-165">次のコード例では、 *MyDb1* および *MyDb2*データベースの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-165">The following code example creates a full database backup of *MyDb1* and *MyDb2*.</span></span> <span data-ttu-id="73666-166">このコード例では、架空のバックアップ共有である、ディレクトリ1を使用 \\ \\ *FILESERVER* \\ *SQLbackups*します。</span><span class="sxs-lookup"><span data-stu-id="73666-166">This code example uses a fictional backup share, \\\\*FILESERVER*\\*SQLbackups*.</span></span>  
  
        ```sql
        -- Backup sample databases:  
        BACKUP DATABASE MyDb1   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
            WITH FORMAT  
        GO  
  
        BACKUP DATABASE MyDb2   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
            WITH FORMAT  
        GO
        ```  
  
###  <a name="sample-configuration-procedure"></a><a name="SampleProcedure"></a> <span data-ttu-id="73666-167">サンプル構成プロシージャ</span><span class="sxs-lookup"><span data-stu-id="73666-167">Sample Configuration Procedure</span></span>  
 <span data-ttu-id="73666-168">このサンプル構成では、信頼関係のある異なるドメイン (`DOMAIN1` と `DOMAIN2`) の下でサービス アカウントが実行される 2 つのスタンドアロン サーバー インスタンスに可用性レプリカを作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-168">In this sample configuration, the availability replica will be created on two stand-alone server instances whose service accounts run under different, but trusted, domains (`DOMAIN1` and `DOMAIN2`).</span></span>  
  
 <span data-ttu-id="73666-169">次の表は、このサンプル構成で使用する値をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="73666-169">The following table summarizes the values used in this sample configuration.</span></span>  
  
|<span data-ttu-id="73666-170">初期ロール</span><span class="sxs-lookup"><span data-stu-id="73666-170">Initial role</span></span>|<span data-ttu-id="73666-171">システム</span><span class="sxs-lookup"><span data-stu-id="73666-171">System</span></span>|<span data-ttu-id="73666-172">ホスト [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス</span><span class="sxs-lookup"><span data-stu-id="73666-172">Host [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance</span></span>|  
|------------------|------------|---------------------------------------------|  
|<span data-ttu-id="73666-173">プライマリ</span><span class="sxs-lookup"><span data-stu-id="73666-173">Primary</span></span>|`COMPUTER01`|`AgHostInstance`|  
|<span data-ttu-id="73666-174">セカンダリ</span><span class="sxs-lookup"><span data-stu-id="73666-174">Secondary</span></span>|`COMPUTER02`|<span data-ttu-id="73666-175">既定のインスタンス</span><span class="sxs-lookup"><span data-stu-id="73666-175">Default instance.</span></span>|  
  
1.  <span data-ttu-id="73666-176">可用性グループの作成先となるサーバー インスタンス ( *上の* という名前のインスタンス) 上に、 `AgHostInstance` dbm_endpoint `COMPUTER01`という名前のデータベース ミラーリング エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-176">Create a database mirroring endpoint named *dbm_endpoint* on the server instance on which you plan to create the availability group (this is an instance named `AgHostInstance` on `COMPUTER01`).</span></span> <span data-ttu-id="73666-177">このエンドポイントはポート 7022 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73666-177">This endpoint uses port 7022.</span></span> <span data-ttu-id="73666-178">可用性グループの作成先となるサーバー インスタンスには、プライマリ レプリカがホストされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="73666-178">Note that the server instance on which you create the availability group will host the primary replica.</span></span>  
  
    ```sql
    -- Create endpoint on server instance that hosts the primary replica:  
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
2.  <span data-ttu-id="73666-179">セカンダリ レプリカをホストするサーバー インスタンス ( *上の既定のサーバー インスタンス) 上にエンドポイント* dbm_endpoint `COMPUTER02`を作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-179">Create an endpoint *dbm_endpoint* on the server instance that will host the secondary replica (this is the default server instance on `COMPUTER02`).</span></span> <span data-ttu-id="73666-180">このエンドポイントはポート 5022 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73666-180">This endpoint uses port 5022.</span></span>  
  
    ```sql
    -- Create endpoint on server instance that hosts the secondary replica:   
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=5022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
3.  > [!NOTE]  
    >  <span data-ttu-id="73666-181">可用性レプリカをホストするサーバー インスタンスのサービス アカウントが同じドメイン アカウントで実行されている場合、この手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="73666-181">If the service accounts of the server instances that are to host your availability replicas run under the same domain account this step is unnecessary.</span></span> <span data-ttu-id="73666-182">省略して次の手順に進んでください。</span><span class="sxs-lookup"><span data-stu-id="73666-182">Skip it and go directly to the next step.</span></span>  
  
     <span data-ttu-id="73666-183">2 つのサーバー インスタンスのサービス アカウントが、互いに異なるドメイン ユーザーで実行されている場合、それぞれのサーバー インスタンス上に、相手のサーバー インスタンス用のログインを作成し、このログイン権限に、ローカルのデータベース ミラーリング エンドポイントのアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="73666-183">If the service accounts of the server instances run under different domain users, on each server instance, create a login for the other server instance and grant this login permission to access the local database mirroring endpoint.</span></span>  
  
     <span data-ttu-id="73666-184">ログインを作成し、エンドポイントの権限を付与するための [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="73666-184">The following code example shows the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements for creating a login and granting it permission on an endpoint.</span></span> <span data-ttu-id="73666-185">ここでは、リモート サーバー インスタンスのドメイン アカウントを *domain_name*\\*user_name*としています。</span><span class="sxs-lookup"><span data-stu-id="73666-185">The domain account of the remote server instance is represented here as *domain_name*\\*user_name*.</span></span>  
  
    ```sql
    -- If necessary, create a login for the service account, domain_name\user_name  
    -- of the server instance that will host the other replica:  
    USE master;  
    GO  
    CREATE LOGIN [domain_name\user_name] FROM WINDOWS;  
    GO  
    -- And Grant this login connect permissions on the endpoint:  
    GRANT CONNECT ON ENDPOINT::dbm_endpoint   
       TO [domain_name\user_name];  
    GO  
    ```  
  
4.  <span data-ttu-id="73666-186">ユーザー データベースが存在するサーバー インスタンス上に、可用性グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-186">On the server instance where the user databases reside, create the availability group.</span></span>  
  
     <span data-ttu-id="73666-187">次のコード例では、サンプル データベースの *MyDb1* と *MyDb2* を作成したサーバー インスタンス上に、 *MyAG*という名前の可用性グループを作成しています。</span><span class="sxs-lookup"><span data-stu-id="73666-187">The following code example creates an availability group named *MyAG* on the server instance on which the sample databases, *MyDb1* and *MyDb2*, were created.</span></span> <span data-ttu-id="73666-188">最初に、 `AgHostInstance`COMPUTER01 *上のローカル サーバー インスタンス (* ) が指定されています。</span><span class="sxs-lookup"><span data-stu-id="73666-188">The local server instance, `AgHostInstance`, on *COMPUTER01* is specified first.</span></span> <span data-ttu-id="73666-189">初期プライマリ レプリカは、このインスタンスによってホストされます。</span><span class="sxs-lookup"><span data-stu-id="73666-189">This instance will host the initial primary replica.</span></span> <span data-ttu-id="73666-190">リモート サーバー インスタンス ( *COMPUTER02*上の既定のサーバー インスタンス) は、セカンダリ レプリカをホストするように指定されています。</span><span class="sxs-lookup"><span data-stu-id="73666-190">A remote server instance, the default server instance on *COMPUTER02*, is specified to host a secondary replica.</span></span> <span data-ttu-id="73666-191">どちらの可用性レプリカも、非同期コミット モードと手動フェールオーバーを使用するように構成します (非同期コミットのレプリカでは、手動フェールオーバーは、データ損失の可能性を伴う強制フェールオーバーを意味します)。</span><span class="sxs-lookup"><span data-stu-id="73666-191">Both availability replica are configured to use asynchronous-commit mode with manual failover (for asynchronous-commit replicas manual failover means  forced failover with possible data loss).</span></span>  
  
    ```sql
    -- Create the availability group, MyAG:   
    CREATE AVAILABILITY GROUP MyAG   
       FOR   
          DATABASE MyDB1, MyDB2   
       REPLICA ON   
          'COMPUTER01\AgHostInstance' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',   
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             ),  
          'COMPUTER02' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );   
    GO  
    ```  
  
     <span data-ttu-id="73666-192">可用性グループを作成するための他の [!INCLUDE[tsql](../../../includes/tsql-md.md)] コード例については、「[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73666-192">For additional [!INCLUDE[tsql](../../../includes/tsql-md.md)] code examples of creating an availability group, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).</span></span>  
  
5.  <span data-ttu-id="73666-193">セカンダリ レプリカをホストするサーバー インスタンス上で、セカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="73666-193">On the server instance that hosts the secondary replica, join the secondary replica to the availability group.</span></span>  
  
     <span data-ttu-id="73666-194">次のコード例では、 `COMPUTER02` 上のセカンダリ レプリカを `MyAG` 可用性グループに参加させています。</span><span class="sxs-lookup"><span data-stu-id="73666-194">The following code example joins the secondary replica on `COMPUTER02` to the `MyAG` availability group.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join the secondary replica to the availability group:  
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    GO  
    ```  
  
6.  <span data-ttu-id="73666-195">セカンダリ レプリカをホストするサーバー インスタンス上でセカンダリ データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-195">On the server instance that hosts the secondary replica, create the secondary databases.</span></span>  
  
     <span data-ttu-id="73666-196">次のコード例では、RESTORE WITH NORECOVERY でデータベース バックアップを復元することによって、 *MyDb1* と *MyDb2* のセカンダリ データベースを作成しています。</span><span class="sxs-lookup"><span data-stu-id="73666-196">The following code example creates the *MyDb1* and *MyDb2* secondary databases by restoring database backups using RESTORE WITH NORECOVERY.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- Restore database backups using the WITH NORECOVERY option:  
    RESTORE DATABASE MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NORECOVERY  
    GO  
  
    RESTORE DATABASE MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH NORECOVERY  
    GO
    ```  
  
7.  <span data-ttu-id="73666-197">プライマリ レプリカをホストするサーバー インスタンス上で、各プライマリ データベースのトランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="73666-197">On the server instance that hosts the primary replica, back up the transaction log on each of the primary databases.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="73666-198">実際に可用性グループを構成する際は、このログのバックアップを作成する前に、まず対応するセカンダリ データベースを可用性グループに参加させ、それが済んでからプライマリ データベースのログ バックアップ作業を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="73666-198">When you are configuring a real availability group, we recommend that, before taking this log backup, you suspend log backup tasks for your primary databases until you have joined the corresponding secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="73666-199">次のコード例では、MyDb1 および MyDb2 のトランザクション ログのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="73666-199">The following code example creates a transaction log backup on MyDb1 and on MyDb2.</span></span>  
  
    ```sql
    -- On the server instance that hosts the primary replica,   
    -- Backup the transaction log on each primary database:  
    BACKUP LOG MyDb1   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NOFORMAT  
    GO  
  
    BACKUP LOG MyDb2   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITHNOFORMAT  
    GO
    ```  
  
    > [!TIP]  
    >  <span data-ttu-id="73666-200">通常、ログ バックアップは各プライマリ データベースで作成した後、対応するセカンダリ データベースで (WITH NORECOVERY を使用して) 復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73666-200">Typically, a log backup must be taken on each primary database and then restored on the corresponding secondary database (using WITH NORECOVERY).</span></span> <span data-ttu-id="73666-201">ただし、データベースを作成したばかりでこのログ バックアップがまだ作成されていない場合や、復旧モデルを SIMPLE から FULL に変更したばかりの場合など、ログ バックアップが不要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="73666-201">However, this log backup might be unnecessary if the database has just been created and no log backup has been taken yet or the recovery model has just been changed from SIMPLE to FULL.</span></span>  
  
8.  <span data-ttu-id="73666-202">セカンダリ レプリカをホストするサーバー インスタンス上で、セカンダリ データベースにログ バックアップを適用します。</span><span class="sxs-lookup"><span data-stu-id="73666-202">On the server instance that hosts the secondary replica, apply log backups to the secondary databases.</span></span>  
  
     <span data-ttu-id="73666-203">次のコード例では、RESTORE WITH NORECOVERY でデータベース バックアップを復元することによって、 *MyDb1* と *MyDb2* のセカンダリ データベースにバックアップを適用しています。</span><span class="sxs-lookup"><span data-stu-id="73666-203">The following code example applies backups to *MyDb1* and *MyDb2* secondary databases by restoring database backups using RESTORE WITH NORECOVERY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="73666-204">実際のセカンダリ データベースを準備する際は、セカンダリ データベースの作成元となったデータベース バックアップの後に作成されたすべてのログ バックアップを適用する必要があります。その際には古いものから順に適用し、毎回 WITH NORECOVERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="73666-204">When you are preparing a real secondary database, you need to apply every log backup taken since the database backup from which you created the secondary database, starting with the earliest and always using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="73666-205">当然、完全と差分の両方のデータベース バックアップを復元する場合は、差分バックアップ以降に作成されたログ バックアップを適用するだけでかまいません。</span><span class="sxs-lookup"><span data-stu-id="73666-205">Of course, if you restore both full and differential database backups, you would only need to apply the log backups taken after the differential backup.</span></span>  
  
    ```sql
    -- Restore the transaction log on each secondary database,  
    -- using the WITH NORECOVERY option:  
    RESTORE LOG MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    RESTORE LOG MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
9. <span data-ttu-id="73666-206">セカンダリ レプリカをホストするサーバー インスタンス上で、新しいセカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="73666-206">On the server instance that hosts the secondary replica, join the new secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="73666-207">次のコード例では、 *MyDb1* のセカンダリ データベースと *MyDb2* のセカンダリ データベースを順に *MyAG* 可用性グループに参加させています。</span><span class="sxs-lookup"><span data-stu-id="73666-207">The following code example, joins the *MyDb1* secondary database and then the *MyDb2* secondary databases to the *MyAG* availability group.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join each secondary database to the availability group:  
    ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
    GO  
  
    ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
    GO
    ```  
  
###  <a name="complete-code-example-for-sample-configuration-procedure"></a><a name="CompleteCodeExample"></a> <span data-ttu-id="73666-208">サンプル構成プロシージャの完全なコード例</span><span class="sxs-lookup"><span data-stu-id="73666-208">Complete Code Example for Sample Configuration Procedure</span></span>  
 <span data-ttu-id="73666-209">以下のコードは、すべての手順のコード例を総合したサンプル構成プロシージャの全体像です。</span><span class="sxs-lookup"><span data-stu-id="73666-209">The following example merges the code examples from all the steps of the sample configuration procedure.</span></span> <span data-ttu-id="73666-210">このコード例で使用されているプレースホルダーの値については次の表にまとめました。</span><span class="sxs-lookup"><span data-stu-id="73666-210">The following table summarized the placeholder values used in this code example.</span></span> <span data-ttu-id="73666-211">このコード例の手順の詳細については、このトピックの「 [サンプル構成プロシージャを使用するうえでの前提条件](#PrerequisitesForExample) 」および「 [サンプル構成プロシージャ](#SampleProcedure)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73666-211">For more information about the steps in this code example, see [Prerequisites for Using the Sample Configuration Procedure](#PrerequisitesForExample) and [Sample Configuration Procedure](#SampleProcedure), earlier in this topic.</span></span>  
  
|<span data-ttu-id="73666-212">プレースホルダー</span><span class="sxs-lookup"><span data-stu-id="73666-212">Placeholder</span></span>|<span data-ttu-id="73666-213">説明</span><span class="sxs-lookup"><span data-stu-id="73666-213">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="73666-214">\\\\*FILESERVER*\\*SQLbackups*</span><span class="sxs-lookup"><span data-stu-id="73666-214">\\\\*FILESERVER*\\*SQLbackups*</span></span>|<span data-ttu-id="73666-215">架空のバックアップ共有。</span><span class="sxs-lookup"><span data-stu-id="73666-215">Fictional backup share.</span></span>|  
|<span data-ttu-id="73666-216">\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*</span><span class="sxs-lookup"><span data-stu-id="73666-216">\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*</span></span>|<span data-ttu-id="73666-217">MyDb1 のバックアップ ファイル。</span><span class="sxs-lookup"><span data-stu-id="73666-217">Backup file for MyDb1.</span></span>|  
|<span data-ttu-id="73666-218">\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*</span><span class="sxs-lookup"><span data-stu-id="73666-218">\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*</span></span>|<span data-ttu-id="73666-219">MyDb2 のバックアップ ファイル。</span><span class="sxs-lookup"><span data-stu-id="73666-219">Backup file for MyDb2.</span></span>|  
|<span data-ttu-id="73666-220">*7022*</span><span class="sxs-lookup"><span data-stu-id="73666-220">*7022*</span></span>|<span data-ttu-id="73666-221">各データベース ミラーリング エンドポイントに割り当てられたポート番号。</span><span class="sxs-lookup"><span data-stu-id="73666-221">Port number assigned to each database mirroring endpoint.</span></span>|  
|<span data-ttu-id="73666-222">*COMPUTER01\AgHostInstance*</span><span class="sxs-lookup"><span data-stu-id="73666-222">*COMPUTER01\AgHostInstance*</span></span>|<span data-ttu-id="73666-223">初期プライマリ レプリカをホストするサーバー インスタンス。</span><span class="sxs-lookup"><span data-stu-id="73666-223">Server instance that hosts the initial primary replica.</span></span>|  
|<span data-ttu-id="73666-224">*COMPUTER02*</span><span class="sxs-lookup"><span data-stu-id="73666-224">*COMPUTER02*</span></span>|<span data-ttu-id="73666-225">初期セカンダリ レプリカをホストするサーバー インスタンス。</span><span class="sxs-lookup"><span data-stu-id="73666-225">Server instance that hosts the initial secondary replica.</span></span> <span data-ttu-id="73666-226">これは、 `COMPUTER02`上の既定のサーバー インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="73666-226">This is the default server instance on `COMPUTER02`.</span></span>|  
|<span data-ttu-id="73666-227">*上の*</span><span class="sxs-lookup"><span data-stu-id="73666-227">*dbm_endpoint*</span></span>|<span data-ttu-id="73666-228">各データベース ミラーリング エンドポイントに指定した名前。</span><span class="sxs-lookup"><span data-stu-id="73666-228">Name specified for each database mirroring endpoint.</span></span>|  
|<span data-ttu-id="73666-229">*MyDb1*</span><span class="sxs-lookup"><span data-stu-id="73666-229">*MyAG*</span></span>|<span data-ttu-id="73666-230">サンプルの可用性グループの名前。</span><span class="sxs-lookup"><span data-stu-id="73666-230">Name of sample availability group.</span></span>|  
|<span data-ttu-id="73666-231">*MyDb1*</span><span class="sxs-lookup"><span data-stu-id="73666-231">*MyDb1*</span></span>|<span data-ttu-id="73666-232">1 つ目のサンプル データベースの名前。</span><span class="sxs-lookup"><span data-stu-id="73666-232">Name of first sample database.</span></span>|  
|<span data-ttu-id="73666-233">*MyDb2*</span><span class="sxs-lookup"><span data-stu-id="73666-233">*MyDb2*</span></span>|<span data-ttu-id="73666-234">2 つ目のサンプル データベースの名前。</span><span class="sxs-lookup"><span data-stu-id="73666-234">Name of second sample database.</span></span>|  
|<span data-ttu-id="73666-235">*DOMAIN1\user1*</span><span class="sxs-lookup"><span data-stu-id="73666-235">*DOMAIN1\user1*</span></span>|<span data-ttu-id="73666-236">初期プライマリ レプリカをホストするサーバー インスタンスのサービス アカウント。</span><span class="sxs-lookup"><span data-stu-id="73666-236">Service account of the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="73666-237">*DOMAIN2\user2*</span><span class="sxs-lookup"><span data-stu-id="73666-237">*DOMAIN2\user2*</span></span>|<span data-ttu-id="73666-238">初期セカンダリ レプリカをホストするサーバー インスタンスのサービス アカウント。</span><span class="sxs-lookup"><span data-stu-id="73666-238">Service account of the server instance that is to host the initial secondary replica.</span></span>|  
|<span data-ttu-id="73666-239">TCP://*COMPUTER01.Adventure-Works.com*:*7022*</span><span class="sxs-lookup"><span data-stu-id="73666-239">TCP://*COMPUTER01.Adventure-Works.com*:*7022*</span></span>|<span data-ttu-id="73666-240">COMPUTER01 上の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の AgHostInstance インスタンスのエンドポイント URL。</span><span class="sxs-lookup"><span data-stu-id="73666-240">Endpoint URL of the AgHostInstance instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on COMPUTER01.</span></span>|  
|<span data-ttu-id="73666-241">TCP://*COMPUTER02.Adventure-Works.com*:*5022*</span><span class="sxs-lookup"><span data-stu-id="73666-241">TCP://*COMPUTER02.Adventure-Works.com*:*5022*</span></span>|<span data-ttu-id="73666-242">COMPUTER02 上の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスのエンドポイント URL。</span><span class="sxs-lookup"><span data-stu-id="73666-242">Endpoint URL of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on COMPUTER02.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="73666-243">可用性グループを作成するための他の [!INCLUDE[tsql](../../../includes/tsql-md.md)] コード例については、「[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73666-243">For additional [!INCLUDE[tsql](../../../includes/tsql-md.md)] code examples of creating an availability group, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).</span></span>  
  
```sql
-- on the server instance that will host the primary replica,   
-- create sample databases:  
CREATE DATABASE MyDb1;  
GO  
ALTER DATABASE MyDb1 SET RECOVERY FULL;  
GO  
  
CREATE DATABASE MyDb2;  
GO  
ALTER DATABASE MyDb2 SET RECOVERY FULL;  
GO  
  
-- Backup sample databases:  
BACKUP DATABASE MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FORMAT  
GO  
  
BACKUP DATABASE MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FORMAT  
GO  
  
-- Create the endpoint on the server instance that will host the primary replica:  
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- Create the endpoint on the server instance that will host the secondary replica:   
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the primary replica,   
-- create a login for the service account   
-- of the server instance that will host the secondary replica, DOMAIN2\user2,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
CREATE LOGIN [DOMAIN2\user2] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN2\user2];  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the secondary replica,  
-- create a login for the service account   
-- of the server instance that will host the primary replica, DOMAIN1\user1,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
  
CREATE LOGIN [DOMAIN1\user1] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN1\user1];  
GO  
  
-- On the server instance that will host the primary replica,   
-- create the availability group, MyAG:  
CREATE AVAILABILITY GROUP MyAG   
   FOR   
      DATABASE MyDB1, MyDB2   
   REPLICA ON   
      'COMPUTER01\AgHostInstance' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         ),  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         );   
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join the secondary replica to the availability group:  
ALTER AVAILABILITY GROUP MyAG JOIN;  
GO  
  
-- Restore database backups onto this server instance, using RESTORE WITH NORECOVERY:  
RESTORE DATABASE MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NORECOVERY  
GO  
  
RESTORE DATABASE MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH NORECOVERY  
GO  
  
-- Back up the transaction log on each primary database:  
BACKUP LOG MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NOFORMAT  
GO  
  
BACKUP LOG MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITHNOFORMAT  
GO  
  
-- Restore the transaction log on each secondary database,  
-- using the WITH NORECOVERY option:  
RESTORE LOG MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FILE=1, NORECOVERY  
GO  
RESTORE LOG MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FILE=1, NORECOVERY  
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join each secondary database to the availability group:  
ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
GO  
  
ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
GO
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="73666-244">関連タスク</span><span class="sxs-lookup"><span data-stu-id="73666-244">Related Tasks</span></span>  
 <span data-ttu-id="73666-245">**可用性グループおよびレプリカのプロパティを構成するには**</span><span class="sxs-lookup"><span data-stu-id="73666-245">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="73666-246">可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-246">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="73666-247">可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-247">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="73666-248">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-248">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="73666-249">自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 (AlwaysOn 可用性グループ)</span><span class="sxs-lookup"><span data-stu-id="73666-249">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="73666-250">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-250">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="73666-251">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-251">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="73666-252">可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-252">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="73666-253">可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-253">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="73666-254">可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-254">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="73666-255">**可用性グループの構成を完了するには**</span><span class="sxs-lookup"><span data-stu-id="73666-255">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="73666-256">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-256">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="73666-257">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-257">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="73666-258">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-258">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="73666-259">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-259">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="73666-260">**別の方法で可用性グループを作成する**</span><span class="sxs-lookup"><span data-stu-id="73666-260">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="73666-261">可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-261">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   <span data-ttu-id="73666-262">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="73666-262">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="73666-263">可用性グループの作成 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-263">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="73666-264">**AlwaysOn 可用性グループを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="73666-264">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="73666-265">AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-265">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="73666-266">**データベース ミラーリング エンドポイントを構成するには**</span><span class="sxs-lookup"><span data-stu-id="73666-266">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="73666-267">AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-267">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="73666-268">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-268">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="73666-269">データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-269">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="73666-270">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-270">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="73666-271">**AlwaysOn 可用性グループの構成のトラブルシューティング方法**</span><span class="sxs-lookup"><span data-stu-id="73666-271">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="73666-272">AlwaysOn 可用性グループ構成 (SQL Server) の削除に関するトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="73666-272">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="73666-273">失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-273">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="73666-274">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="73666-274">Related Content</span></span>  
  
-   <span data-ttu-id="73666-275">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="73666-275">**Blogs:**</span></span>  
  
     [<span data-ttu-id="73666-276">AlwaysON - HADRON 学習シリーズ:HADRON 対応データベースでのワーカー プールの使用</span><span class="sxs-lookup"><span data-stu-id="73666-276">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="73666-277">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="73666-277">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="73666-278">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="73666-278">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="73666-279">**ビデオ:**</span><span class="sxs-lookup"><span data-stu-id="73666-279">**Videos:**</span></span>  
  
     [<span data-ttu-id="73666-280">Microsoft SQL Server コード ネーム "Denali" AlwaysOn シリーズ パート 1: 次世代の高可用性ソリューションの概要</span><span class="sxs-lookup"><span data-stu-id="73666-280">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="73666-281">Microsoft SQL Server コードネーム "Denali" AlwaysOn シリーズ パート 2: AlwaysOn を使用したミッション クリティカルな高可用性ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="73666-281">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="73666-282">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="73666-282">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="73666-283">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="73666-283">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="73666-284">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="73666-284">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="73666-285">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="73666-285">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="73666-286">参照</span><span class="sxs-lookup"><span data-stu-id="73666-286">See Also</span></span>  
 <span data-ttu-id="73666-287">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="73666-287">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="73666-288">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="73666-288">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="73666-289">可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="73666-289">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)   
