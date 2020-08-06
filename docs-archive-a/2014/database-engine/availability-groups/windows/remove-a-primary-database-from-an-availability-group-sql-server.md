---
title: 可用性グループからのプライマリ データベースの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeprimarydb.f1
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 6d4ca31e-ddf0-44bf-be5e-a5da060bf096
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b6fafaf6464431d68f8cfdf9dc9d8fa844a42a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634063"
---
# <a name="remove-a-primary-database-from-an-availability-group-sql-server"></a><span data-ttu-id="cc34c-102">可用性グループからのプライマリ データベースの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc34c-102">Remove a Primary Database from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="cc34c-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の [!INCLUDE[tsql](../../../includes/tsql-md.md)]、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループからプライマリ データベースおよび対応するセカンダリ データベースの両方を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-103">This topic describes how to remove both the primary database and the corresponding secondary database(s) from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="cc34c-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="cc34c-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cc34c-105">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="cc34c-105">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="cc34c-106">Security</span><span class="sxs-lookup"><span data-stu-id="cc34c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cc34c-107">**可用性データベースを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="cc34c-107">**To remove an availability database, using:**</span></span>  
  
     [<span data-ttu-id="cc34c-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cc34c-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cc34c-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc34c-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="cc34c-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc34c-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="cc34c-111">**補足情報**  [可用性グループから可用性データベースを削除した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="cc34c-111">**Follow Up:**  [After Removing an Availability Database from an Availability Group](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cc34c-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="cc34c-112">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="cc34c-113">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="cc34c-113">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="cc34c-114">このタスクは、プライマリ レプリカ上でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="cc34c-114">This task is supported only on primary replicas.</span></span> <span data-ttu-id="cc34c-115">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc34c-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cc34c-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cc34c-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cc34c-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="cc34c-117">Permissions</span></span>  
 <span data-ttu-id="cc34c-118">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cc34c-118">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cc34c-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="cc34c-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cc34c-120">**可用性データベースを削除するには**</span><span class="sxs-lookup"><span data-stu-id="cc34c-120">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="cc34c-121">オブジェクト エクスプローラーで、削除するデータベースのプライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-121">In Object Explorer, connect to the server instance that hosts the primary replica of the database or databases to be removed, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="cc34c-122">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="cc34c-123">可用性グループを選択し、 **[可用性データベース]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-123">Select the availability group, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="cc34c-124">削除するデータベースが複数であるか 1 つのみであるかによって、次のように実行する手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="cc34c-124">This step depends on whether you want to remove multiple databases groups or only one database, as follows:</span></span>  
  
    -   <span data-ttu-id="cc34c-125">複数のデータベースを削除するには、 **[オブジェクト エクスプローラーの詳細]** ペインを使用して削除するデータベースを表示し、すべてを選択します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-125">To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove.</span></span> <span data-ttu-id="cc34c-126">詳細については、「[[オブジェクト エクスプローラーの詳細] を使用した可用性グループの監視 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc34c-126">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="cc34c-127">1 つのデータベースを削除するには、 **[オブジェクト エクスプローラー]** ペインまたは **[オブジェクト エクスプローラーの詳細]** ペインでそれを選択します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-127">To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="cc34c-128">選択したデータベースを右クリックし、コマンド メニューの **[可用性グループからデータベースを削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-128">Right-click the selected database or databases, and select **Remove Database from Availability Group** in the command menu.</span></span>  
  
6.  <span data-ttu-id="cc34c-129">**[可用性グループからデータベースを削除]** ダイアログ ボックスで、表示されたすべてのデータベースを削除するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc34c-129">In the **Remove Databases from Availability Group** dialog box, to remove all the listed databases, click **OK**.</span></span> <span data-ttu-id="cc34c-130">すべて削除しない場合は、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc34c-130">If you do not want to remove all them, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cc34c-131">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="cc34c-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="cc34c-132">**可用性データベースを削除するには**</span><span class="sxs-lookup"><span data-stu-id="cc34c-132">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="cc34c-133">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-133">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="cc34c-134">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-134">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="cc34c-135">ALTER AVAILABILITY GROUP *group_name* REMOVE DATABASE *availability_database_name*</span><span class="sxs-lookup"><span data-stu-id="cc34c-135">ALTER AVAILABILITY GROUP *group_name* REMOVE DATABASE *availability_database_name*</span></span>  
  
     <span data-ttu-id="cc34c-136">ここで、 *group_name* は可用性グループの名前、 *database_name* は削除するデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="cc34c-136">where *group_name* is the name of the availability group and *database_name* is the name of the database to be removed.</span></span>  
  
     <span data-ttu-id="cc34c-137">次の例では、 `Db6` というデータベースを `MyAG` 可用性グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-137">The following example removes a databases named `Db6` from the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE DATABASE Db6;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="cc34c-138">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="cc34c-138">Using PowerShell</span></span>  
 <span data-ttu-id="cc34c-139">**可用性データベースを削除するには**</span><span class="sxs-lookup"><span data-stu-id="cc34c-139">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="cc34c-140">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-140">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="cc34c-141">可用性グループから削除する可用性データベース名を指定して、`Remove-SqlAvailabilityDatabase` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-141">Use the `Remove-SqlAvailabilityDatabase` cmdlet, specifying the name of the availability database to be removed from the availability group.</span></span> <span data-ttu-id="cc34c-142">プライマリ レプリカをホストするサーバー インスタンスに接続している場合は、プライマリ データベースおよび対応するセカンダリ データベースがすべて可用性グループから削除されます。</span><span class="sxs-lookup"><span data-stu-id="cc34c-142">When you are connected to the server instance that hosts the primary replica, the primary database and its corresponding secondary databases are all removed from the availability group.</span></span>  
  
     <span data-ttu-id="cc34c-143">たとえば、次のコマンドは、可用性データベース `MyDb9` を `MyAg`という名前の可用性グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-143">For example, the following command removes the availability database `MyDb9` from the availability group named `MyAg`.</span></span> <span data-ttu-id="cc34c-144">このコマンドはプライマリ レプリカをホストするサーバー インスタンスで実行されるため、プライマリ データベースおよび対応するすべてのセカンダリ データベースが可用性グループから削除されます。</span><span class="sxs-lookup"><span data-stu-id="cc34c-144">Because the command is executed on the server instance that hosts the primary replica, the primary database and all its corresponding secondary databases are removed from the availability group.</span></span> <span data-ttu-id="cc34c-145">どのセカンダリ レプリカでも、このデータベースに対してデータ同期は行われなくなります。</span><span class="sxs-lookup"><span data-stu-id="cc34c-145">Data synchronization will no longer occur for this database on any secondary replica.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\PrimaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb9  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc34c-146">コマンドレットの構文を表示するには、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="cc34c-147">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc34c-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="cc34c-148">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="cc34c-148">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="cc34c-149">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="cc34c-149">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-an-availability-database-from-an-availability-group"></a><a name="FollowUp"></a> <span data-ttu-id="cc34c-150">補足情報: 可用性グループから可用性データベースを削除した後</span><span class="sxs-lookup"><span data-stu-id="cc34c-150">Follow Up: After Removing an Availability Database from an Availability Group</span></span>  
 <span data-ttu-id="cc34c-151">可用性グループから可用性データベースを削除すると、以前のプライマリ データベースおよび対応するセカンダリ データベース間のデータの同期が終了します。</span><span class="sxs-lookup"><span data-stu-id="cc34c-151">Removing an availability database from its availability group ends data synchronization between the former primary database and the corresponding secondary databases.</span></span> <span data-ttu-id="cc34c-152">以前のプライマリ データベースはオンラインのまま残ります。</span><span class="sxs-lookup"><span data-stu-id="cc34c-152">The former primary database remains online.</span></span> <span data-ttu-id="cc34c-153">すべての対応するセカンダリ データベースは RESTORING 状態になります。</span><span class="sxs-lookup"><span data-stu-id="cc34c-153">Every corresponding secondary database is placed in the RESTORING state.</span></span>  
  
 <span data-ttu-id="cc34c-154">この時点で、削除されたセカンダリ データベースを処理する別の方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cc34c-154">At this point there are alternative ways of dealing with a removed secondary database:</span></span>  
  
-   <span data-ttu-id="cc34c-155">特定のセカンダリ データベースが不要の場合は、削除できます。</span><span class="sxs-lookup"><span data-stu-id="cc34c-155">If you no longer need a given secondary database, you can drop it.</span></span>  
  
     <span data-ttu-id="cc34c-156">詳細については、「 [データベースの削除](../../../relational-databases/databases/delete-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc34c-156">For more information, see [Delete a Database](../../../relational-databases/databases/delete-a-database.md).</span></span>  
  
-   <span data-ttu-id="cc34c-157">可用性グループから削除された後に、削除されたセカンダリ データベースにアクセスする必要がある場合は、データベースを復元できます。</span><span class="sxs-lookup"><span data-stu-id="cc34c-157">If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database.</span></span> <span data-ttu-id="cc34c-158">ただし、削除されたセカンダリ データベースを復元すると、異なる 2 つのデータベースが同じ名前でオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="cc34c-158">However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online.</span></span> <span data-ttu-id="cc34c-159">クライアントからはどちらか一方のデータベース (通常は最新のプライマリ データベース) にしかアクセスできないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc34c-159">You must make sure that clients can access only one of them, typically the most recent primary database.</span></span>  
  
     <span data-ttu-id="cc34c-160">詳細については、「[データを復元しないデータベースの復旧 &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc34c-160">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc34c-161">参照</span><span class="sxs-lookup"><span data-stu-id="cc34c-161">See Also</span></span>  
 <span data-ttu-id="cc34c-162">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc34c-162">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="cc34c-163">可用性グループからのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cc34c-163">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
