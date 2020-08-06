---
title: 可用性グループへのデータベースの追加 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 2a54eef8-9e8e-4e04-909c-6970112d55cc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0907cf711cac65ad77a8948841d92705fdc1eac9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632137"
---
# <a name="add-a-database-to-an-availability-group-sql-server"></a><span data-ttu-id="63acf-102">可用性グループへのデータベースの追加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63acf-102">Add a Database to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="63acf-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループにデータベースを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="63acf-103">This topic describes how to add a database to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="63acf-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="63acf-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="63acf-105">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="63acf-105">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="63acf-106">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="63acf-106">Permissions</span></span>](#Permissions)  
  
-   <span data-ttu-id="63acf-107">**可用性グループにデータベースを追加する方法:**</span><span class="sxs-lookup"><span data-stu-id="63acf-107">**To add a database to an availability group, using:**</span></span>  
  
     [<span data-ttu-id="63acf-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63acf-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="63acf-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63acf-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="63acf-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="63acf-110">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="63acf-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="63acf-111">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="63acf-112">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="63acf-112">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="63acf-113">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="63acf-113">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="63acf-114">プライマリ レプリカがホストされるサーバー インスタンスにデータベースが存在し、データベースが可用性データベースの前提条件と制限に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="63acf-114">The database must reside on the server instance that hosts the primary replica and comply with the prerequisites and restrictions for availability databases.</span></span> <span data-ttu-id="63acf-115">詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63acf-115">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="63acf-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="63acf-116">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="63acf-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="63acf-117">Permissions</span></span>  
 <span data-ttu-id="63acf-118">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="63acf-118">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="63acf-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="63acf-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="63acf-120">**可用性グループにデータベースを追加するには**</span><span class="sxs-lookup"><span data-stu-id="63acf-120">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="63acf-121">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="63acf-121">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="63acf-122">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="63acf-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="63acf-123">可用性グループを右クリックし、次のコマンドのどちらかを選択します。</span><span class="sxs-lookup"><span data-stu-id="63acf-123">Right-click the availability group, and select one of the following commands:</span></span>  
  
    -   <span data-ttu-id="63acf-124">可用性グループへのデータベース追加ウィザードを起動するには、 **[データベースの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63acf-124">To launch the Add Database to Availability Group Wizard, select the **Add Database** command.</span></span> <span data-ttu-id="63acf-125">詳細については、[可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63acf-125">For more information, see [Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md).</span></span>  
  
    -   <span data-ttu-id="63acf-126">1 つまたは複数のデータベースを追加するには、 **[可用性グループのプロパティ]** ダイアログ ボックスでそれらを指定し、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63acf-126">To add one or more databases by specifying them in the **Availability Group Properties** dialog box, select the **Properties** command.</span></span> <span data-ttu-id="63acf-127">データベースを追加する手順は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="63acf-127">The steps for adding a database are as follows:</span></span>  
  
        1.  <span data-ttu-id="63acf-128">**[可用性データベース]** ペインで、 **[追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="63acf-128">In the **Availability Databases** pane, click the **Add** button.</span></span> <span data-ttu-id="63acf-129">これにより、空のデータベース フィールドが作成され、選択されます。</span><span class="sxs-lookup"><span data-stu-id="63acf-129">This creates and selects a blank database field.</span></span>  
  
        2.  <span data-ttu-id="63acf-130">可用性データベースの前提条件を満たしているデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="63acf-130">Enter the name of a database that meets the availability-databases prerequisites.</span></span>  
  
         <span data-ttu-id="63acf-131">別のデータベースを追加するには、上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="63acf-131">To add another database, repeat the preceding steps.</span></span> <span data-ttu-id="63acf-132">データベースの指定を完了したら、 **[OK]** をクリックして操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="63acf-132">When you are done specifying databases, click **OK** to complete the operation.</span></span>  
  
         <span data-ttu-id="63acf-133">**[可用性グループのプロパティ]** ダイアログ ボックスを使用して可用性グループにデータベースを追加した後、セカンダリ レプリカをホストする各サーバー インスタンスで、対応するセカンダリ データベースを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63acf-133">After you use the **Availability Group Properties** dialog box to add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="63acf-134">詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63acf-134">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="63acf-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="63acf-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="63acf-136">**可用性グループにデータベースを追加するには**</span><span class="sxs-lookup"><span data-stu-id="63acf-136">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="63acf-137">プライマリ レプリカをホストするサーバー インスタンスをホストするセカンダリ インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="63acf-137">Connect to the server instance that hosts the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="63acf-138">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="63acf-138">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="63acf-139">ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]</span><span class="sxs-lookup"><span data-stu-id="63acf-139">ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]</span></span>  
  
     <span data-ttu-id="63acf-140">ここで、 *group_name* は可用性グループの名前、 *database_name* はグループに追加するデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="63acf-140">where *group_name* is the name of the availability group and *database_name* is the name of a database to be added to the group.</span></span>  
  
     <span data-ttu-id="63acf-141">次の例では、 *MyDb3* データベースを *MyAG* 可用性グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="63acf-141">The following example adds the *MyDb3* database to the *MyAG* availability group.</span></span>  
  
    ```  
    -- Connect to the server instance that hosts the primary replica.  
    -- Add an existing database to the availability group.  
    ALTER AVAILABILITY GROUP MyAG ADD DATABASE MyDb3;  
    GO  
    ```  
  
3.  <span data-ttu-id="63acf-142">可用性グループにデータベースを追加した後、セカンダリ データベースをホストする各サーバー インスタンスで、対応するセカンダリ データベースを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63acf-142">After you add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="63acf-143">詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63acf-143">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="63acf-144">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="63acf-144">Using PowerShell</span></span>  
 <span data-ttu-id="63acf-145">**可用性グループにデータベースを追加するには**</span><span class="sxs-lookup"><span data-stu-id="63acf-145">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="63acf-146">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="63acf-146">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="63acf-147">`Add-SqlAvailabilityDatabase` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="63acf-147">Use the `Add-SqlAvailabilityDatabase` cmdlet.</span></span>  
  
     <span data-ttu-id="63acf-148">たとえば、次のコマンドは、そのプライマリ レプリカが `MyDd` によってホストされるセカンダリ データベース `MyAG` を `PrimaryServer\InstanceName`可用性グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="63acf-148">For example, the following command adds the secondary database `MyDd` to the `MyAG` availability group, whose primary replica is hosted by `PrimaryServer\InstanceName`.</span></span>  
  
    ```powershell
    Add-SqlAvailabilityDatabase `   
     -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
     -Database "MyDb"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="63acf-149">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="63acf-149">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="63acf-150">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63acf-150">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
3.  <span data-ttu-id="63acf-151">可用性グループにデータベースを追加した後、セカンダリ データベースをホストする各サーバー インスタンスで、対応するセカンダリ データベースを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63acf-151">After you add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="63acf-152">詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63acf-152">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="63acf-153">SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63acf-153">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>

 <span data-ttu-id="63acf-154">次の例では、可用性グループのプライマリ レプリカをホストするサーバー インスタンス上のデータベースからセカンダリ データベースを準備し、そのデータベースを (プライマリ データベースとして) 可用性グループに追加した後、セカンダリ データベースを可用性グループに参加させるすべての処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="63acf-154">The following example shows the full process for preparing a secondary database from a database on the server instance that hosts the primary replica of an availability group, adding the database to an availability group (as a primary database), and then joining the secondary database to the availability group.</span></span> <span data-ttu-id="63acf-155">最初に、データベースとトランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="63acf-155">First, the example backs up the database and its transaction log.</span></span> <span data-ttu-id="63acf-156">次に、セカンダリ レプリカをホストするサーバー インスタンスにデータベースとログのバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="63acf-156">Then the example restores the database and log backups to the server instances that host a secondary replica.</span></span>  
  
 <span data-ttu-id="63acf-157">この例では、`Add-SqlAvailabilityDatabase` を 2 回呼び出します。1 回目はデータベースを可用性グループに追加するためにプライマリ レプリカで呼び出し、2 回目はセカンダリ レプリカ上のセカンダリ データベースを可用性グループに参加させるためにセカンダリ レプリカで呼び出します。</span><span class="sxs-lookup"><span data-stu-id="63acf-157">The example calls `Add-SqlAvailabilityDatabase` twice: first on the primary replica to add the database to the availability group, and then on the secondary replica to join the secondary database on that replica to the availability group.</span></span> <span data-ttu-id="63acf-158">セカンダリ レプリカが複数ある場合は、それぞれのセカンダリ データベースを復元して参加させます。</span><span class="sxs-lookup"><span data-stu-id="63acf-158">If you have more than one secondary replica, restore and join the secondary database on each of them.</span></span>  
  
```powershell
$DatabaseBackupFile = "\\share\backups\MyDatabase.bak"  
$LogBackupFile = "\\share\backups\MyDatabase.trn"  
$MyAgPrimaryPath = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
$MyAgSecondaryPath = "SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAg"  
  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "PrimaryServer\InstanceName"  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "PrimaryServer\InstanceName" -BackupAction 'Log'  
  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "SecondaryServer\InstanceName" -NoRecovery  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "SecondaryServer\InstanceName" -RestoreAction 'Log' -NoRecovery  
  
Add-SqlAvailabilityDatabase -Path $MyAgPrimaryPath -Database "MyDatabase"  
Add-SqlAvailabilityDatabase -Path $MyAgSecondaryPath -Database "MyDatabase"
```  
  
## <a name="see-also"></a><span data-ttu-id="63acf-159">参照</span><span class="sxs-lookup"><span data-stu-id="63acf-159">See Also</span></span>  
 <span data-ttu-id="63acf-160">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63acf-160">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="63acf-161">[可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63acf-161">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="63acf-162">[AlwaysOn ダッシュボード &#40;SQL Server Management Studio を使用&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="63acf-162">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="63acf-163">可用性グループの監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63acf-163">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
