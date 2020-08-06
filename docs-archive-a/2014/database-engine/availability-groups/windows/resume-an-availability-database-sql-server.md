---
title: 可用性データベースの再開 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.resumedatamove.f1
helpviewer_keywords:
- Availability Groups [SQL Server], resuming a database
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], databases
ms.assetid: 20e9147b-e985-4caa-910e-fc4b38dbf9a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a2279940c2502a310e9dac4448bd6029b6e13dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740482"
---
# <a name="resume-an-availability-database-sql-server"></a><span data-ttu-id="83ae0-102">可用性データベースの再開 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="83ae0-102">Resume an Availability Database (SQL Server)</span></span>
  <span data-ttu-id="83ae0-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用して、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の中断された可用性データベースを再開できます。</span><span class="sxs-lookup"><span data-stu-id="83ae0-103">You can resume a suspended availability database in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="83ae0-104">中断されたデータベースを再開すると、データベースが SYNCHRONIZING 状態になります。</span><span class="sxs-lookup"><span data-stu-id="83ae0-104">Resuming a suspended database puts the database into the SYNCHRONIZING state.</span></span> <span data-ttu-id="83ae0-105">プライマリ データベースを再開することにより、プライマリ データベースの中断の結果として中断されたセカンダリ データベースもすべて再開されます。</span><span class="sxs-lookup"><span data-stu-id="83ae0-105">Resuming the primary database also resumes any of its secondary databases that were suspended as the result of suspending the primary database.</span></span> <span data-ttu-id="83ae0-106">セカンダリ データベースが、セカンダリ レプリカをホストするサーバー インスタンスからローカルで中断された場合、そのセカンダリ データベースはローカルで再開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83ae0-106">If any secondary database was suspended locally, from the server instance that hosts the secondary replica, that secondary database must be resumed locally.</span></span> <span data-ttu-id="83ae0-107">特定のセカンダリ データベースおよび対応するプライマリ データベースが SYNCHRONIZING 状態になると、セカンダリ データベースでデータ同期が再開されます。</span><span class="sxs-lookup"><span data-stu-id="83ae0-107">Once a given secondary database and the corresponding primary database are in the SYNCHRONIZING state, data synchronization resumes on the secondary database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83ae0-108">AlwaysOn セカンダリ データベースの中断と再開が、プライマリ データベースの可用性に直接影響することはありません。</span><span class="sxs-lookup"><span data-stu-id="83ae0-108">Suspending and resuming an AlwaysOn secondary database does not directly affect the availability of the primary database.</span></span> <span data-ttu-id="83ae0-109">ただし、中断されたセカンダリ データベースが再開されるまで、セカンダリ データベースの中断はプライマリ データベースの冗長性とフェールオーバー機能に影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="83ae0-109">However, suspending a secondary database can impact redundancy and failover capabilities for the primary database, until the suspended secondary database is resumed.</span></span> <span data-ttu-id="83ae0-110">ミラーリングの場合はこれと異なり、ミラーリングが再開されるまで、ミラーリングの状態はミラー データベースでもプリンシパル データベースでも中断になります。</span><span class="sxs-lookup"><span data-stu-id="83ae0-110">This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database until mirroring is resumed.</span></span> <span data-ttu-id="83ae0-111">AlwaysOn プライマリ データベースを中断すると、対応するすべてのセカンダリ データベースでデータ移動が中断され、そのデータベースの冗長性とフェールオーバー機能はプライマリ データベースが再開されるまで停止されます。</span><span class="sxs-lookup"><span data-stu-id="83ae0-111">Suspending an AlwaysOn primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.</span></span>  
  
-   <span data-ttu-id="83ae0-112">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="83ae0-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="83ae0-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="83ae0-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="83ae0-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="83ae0-114">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="83ae0-115">Security</span><span class="sxs-lookup"><span data-stu-id="83ae0-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="83ae0-116">**次のものを使用してセカンダリ データベースを再開するには:**</span><span class="sxs-lookup"><span data-stu-id="83ae0-116">**To resume a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="83ae0-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="83ae0-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="83ae0-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="83ae0-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="83ae0-119">PowerShell</span><span class="sxs-lookup"><span data-stu-id="83ae0-119">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="83ae0-120">関連タスク</span><span class="sxs-lookup"><span data-stu-id="83ae0-120">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="83ae0-121">はじめに</span><span class="sxs-lookup"><span data-stu-id="83ae0-121">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="83ae0-122">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="83ae0-122">Limitations and Restrictions</span></span>  
 <span data-ttu-id="83ae0-123">RESUME コマンドは、対象のデータベースをホストするレプリカによって受け付けられるとすぐに戻りますが、実際にはデータベースの再開が非同期に行われます。</span><span class="sxs-lookup"><span data-stu-id="83ae0-123">A RESUME command returns as soon as it has been accepted by the replica that hosts the target database, but actually resuming the database occurs asynchronously.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="83ae0-124">前提条件</span><span class="sxs-lookup"><span data-stu-id="83ae0-124">Prerequisites</span></span>  
  
-   <span data-ttu-id="83ae0-125">再開するデータベースをホストするサーバー インスタンスに接続している。</span><span class="sxs-lookup"><span data-stu-id="83ae0-125">You must be connected to the server instance that hosts the database to be resumed.</span></span>  
  
-   <span data-ttu-id="83ae0-126">可用性グループがオンラインになっている。</span><span class="sxs-lookup"><span data-stu-id="83ae0-126">The availability group must be online.</span></span>  
  
-   <span data-ttu-id="83ae0-127">プライマリ データベースがオンラインであり、使用できる状態である。</span><span class="sxs-lookup"><span data-stu-id="83ae0-127">The primary database must be online and available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="83ae0-128">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="83ae0-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="83ae0-129">Permissions</span><span class="sxs-lookup"><span data-stu-id="83ae0-129">Permissions</span></span>  
 <span data-ttu-id="83ae0-130">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="83ae0-130">Requires ALTER permission on the database.</span></span>  
  
 <span data-ttu-id="83ae0-131">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="83ae0-131">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="83ae0-132">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="83ae0-132">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="83ae0-133">**セカンダリ データベースを再開するには**</span><span class="sxs-lookup"><span data-stu-id="83ae0-133">**To resume a secondary database**</span></span>  
  
1.  <span data-ttu-id="83ae0-134">オブジェクト エクスプローラーで、データベースを再開する可用性レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-134">In Object Explorer, connect to the server instance that hosts the availability replica on which you want to resume a database, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="83ae0-135">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-135">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="83ae0-136">可用性グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-136">Expand the availability group.</span></span>  
  
4.  <span data-ttu-id="83ae0-137">**[可用性データベース]** ノードを展開し、データベースを右クリックして、 **[データ移動の再開]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83ae0-137">Expand the **Availability Databases** node, right-click the database, and click **Resume Data Movement**.</span></span>  
  
5.  <span data-ttu-id="83ae0-138">**[データ移動の再開]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83ae0-138">In the **Resume Data Movement** dialog box, click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83ae0-139">このレプリカの場所で他のデータベースを再開するには、データベースごとに手順 4. と手順 5. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-139">To resume additional databases on this replica location, repeat steps 4 and 5 for each database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="83ae0-140">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="83ae0-140">Using Transact-SQL</span></span>  
 <span data-ttu-id="83ae0-141">**ローカルで中断されたセカンダリ データベースを再開するには**</span><span class="sxs-lookup"><span data-stu-id="83ae0-141">**To resume a secondary database that was suspended locally**</span></span>  
  
1.  <span data-ttu-id="83ae0-142">再開するデータベースが含まれるセカンダリ レプリカがホストされているサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-142">Connect to the server instance that hosts the secondary replica whose database you want to resume.</span></span>  
  
2.  <span data-ttu-id="83ae0-143">次の [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)ステートメントを使用して、セカンダリ データベースを再開します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-143">Resume the secondary database by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)statement:</span></span>  
  
     <span data-ttu-id="83ae0-144">ALTER DATABASE *database_name* SET HADR RESUME</span><span class="sxs-lookup"><span data-stu-id="83ae0-144">ALTER DATABASE *database_name* SET HADR RESUME</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="83ae0-145">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="83ae0-145">Using PowerShell</span></span>  

### <a name="to-resume-a-secondary-database"></a><span data-ttu-id="83ae0-146">セカンダリ データベースを再開するには</span><span class="sxs-lookup"><span data-stu-id="83ae0-146">To resume a secondary database</span></span>
  
1.  <span data-ttu-id="83ae0-147">再開するデータベースが含まれるレプリカがホストされているサーバー インスタンスに、ディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-147">Change directory (`cd`) to the server instance that hosts the replica whose database you want to resume.</span></span> <span data-ttu-id="83ae0-148">詳細については、このトピックの「 [前提条件](#Prerequisites)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="83ae0-148">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="83ae0-149">**Resume-SqlAvailabilityDatabase** コマンドレットを使用して可用性グループを再開します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-149">Use the **Resume-SqlAvailabilityDatabase** cmdlet to resume the availability group.</span></span>  
  
     <span data-ttu-id="83ae0-150">たとえば、次のコマンドでは、可用性グループ `MyDb3` に含まれている可用性データベース `MyAg`のデータの同期を再開します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-150">For example, the following command resumes data synchronization for the availability database `MyDb3` in the availability group `MyAg`.</span></span>  
  
    ```powershell
    Resume-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="83ae0-151">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="83ae0-151">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="83ae0-152">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83ae0-152">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="83ae0-153">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="83ae0-153">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="83ae0-154">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="83ae0-154">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="83ae0-155">関連タスク</span><span class="sxs-lookup"><span data-stu-id="83ae0-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="83ae0-156">可用性データベースの中断 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83ae0-156">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="83ae0-157">参照</span><span class="sxs-lookup"><span data-stu-id="83ae0-157">See Also</span></span>  
 [<span data-ttu-id="83ae0-158">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="83ae0-158">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
