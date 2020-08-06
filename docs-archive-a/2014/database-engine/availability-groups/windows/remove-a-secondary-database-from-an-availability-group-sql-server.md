---
title: 可用性グループからのセカンダリ データベースの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.unjoindb.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], databases
ms.assetid: 4e51a570-58d7-4f01-9390-4198f3602576
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1c3de0afd73b46ae5594d26d1763f5bd78483efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634061"
---
# <a name="remove-a-secondary-database-from-an-availability-group-sql-server"></a><span data-ttu-id="151f8-102">可用性グループからのセカンダリ データベースの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="151f8-102">Remove a Secondary Database from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="151f8-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループからセカンダリ データベースを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="151f8-103">This topic describes how to remove a secondary database from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="151f8-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="151f8-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="151f8-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="151f8-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="151f8-106">Security</span><span class="sxs-lookup"><span data-stu-id="151f8-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="151f8-107">**セカンダリ データベースを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="151f8-107">**To remove a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="151f8-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="151f8-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="151f8-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="151f8-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="151f8-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="151f8-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="151f8-111">**補足情報:**  [セカンダリ データベースを可用性グループから削除した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="151f8-111">**Follow Up:**  [After Removing a Secondary Database from an Availability Group](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="151f8-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="151f8-112">Before You Begin</span></span>  
  
###  <a name="Restrictions"></a>   
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="151f8-113">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="151f8-113">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="151f8-114">このタスクは、セカンダリ レプリカ上でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="151f8-114">This task is supported only on secondary replicas.</span></span> <span data-ttu-id="151f8-115">データベースを削除するセカンダリ レプリカをホストするサーバー インスタンスに接続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="151f8-115">You must be connected to the server instance that hosts the secondary replica from which the database is to be removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="151f8-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="151f8-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="151f8-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="151f8-117">Permissions</span></span>  
 <span data-ttu-id="151f8-118">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="151f8-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="151f8-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="151f8-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="151f8-120">**セカンダリ データベースを可用性グループから削除するには**</span><span class="sxs-lookup"><span data-stu-id="151f8-120">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="151f8-121">オブジェクト エクスプローラーで、1 つ以上のセカンダリ データベースを削除するセカンダリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="151f8-121">In Object Explorer, connect to the server instance that hosts the secondary replica from which you want to remove one or more secondary databases, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="151f8-122">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="151f8-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="151f8-123">可用性グループを選択し、 **[可用性データベース]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="151f8-123">Select the availability group, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="151f8-124">削除するデータベースが複数であるか 1 つのみであるかによって、次のように実行する手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="151f8-124">This step depends on whether you want to remove multiple databases groups or only one database, as follows:</span></span>  
  
    -   <span data-ttu-id="151f8-125">複数のデータベースを削除するには、 **[オブジェクト エクスプローラーの詳細]** ペインを使用して削除するデータベースを表示し、すべてを選択します。</span><span class="sxs-lookup"><span data-stu-id="151f8-125">To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove.</span></span> <span data-ttu-id="151f8-126">詳細については、「[[オブジェクト エクスプローラーの詳細] を使用した可用性グループの監視 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="151f8-126">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="151f8-127">1 つのデータベースを削除するには、 **[オブジェクト エクスプローラー]** ペインまたは **[オブジェクト エクスプローラーの詳細]** ペインでそれを選択します。</span><span class="sxs-lookup"><span data-stu-id="151f8-127">To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="151f8-128">選択したデータベースを右クリックし、コマンド メニューの **[セカンダリ データベースの削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="151f8-128">Right-click the selected database or databases, and select **Remove Secondary Database** in the command menu.</span></span>  
  
6.  <span data-ttu-id="151f8-129">**[可用性グループからのデータベースの削除]** ダイアログ ボックスで、表示されたすべてのデータベースを削除するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="151f8-129">In the **Remove Database from Availability Group** dialog box, to remove all the listed databases, click **OK**.</span></span> <span data-ttu-id="151f8-130">表示されたデータベースをすべて削除しない場合は、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="151f8-130">If you do not want to remove all the listed databases, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="151f8-131">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="151f8-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="151f8-132">**セカンダリ データベースを可用性グループから削除するには**</span><span class="sxs-lookup"><span data-stu-id="151f8-132">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="151f8-133">セカンダリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="151f8-133">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="151f8-134">[ALTER DATABASE ステートメントの SET HADR 句](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) を使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="151f8-134">Use the [SET HADR clause of the ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) statement, as follows:</span></span>  
  
     <span data-ttu-id="151f8-135">ALTER DATABASE *database_name* SET HADR OFF</span><span class="sxs-lookup"><span data-stu-id="151f8-135">ALTER DATABASE *database_name* SET HADR OFF</span></span>  
  
     <span data-ttu-id="151f8-136">*database_name* の部分には、可用性グループから削除するセカンダリ データベース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="151f8-136">where *database_name* is the name of a secondary database to be removed from the availability group to which it belongs.</span></span>  
  
     <span data-ttu-id="151f8-137">次の例では、ローカル セカンダリ データベース *MyDb2* を、可用性グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="151f8-137">The following example removes the local secondary database *MyDb2* from its availability group.</span></span>  
  
    ```sql
    ALTER DATABASE MyDb2 SET HADR OFF;  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="151f8-138">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="151f8-138">Using PowerShell</span></span>  
 <span data-ttu-id="151f8-139">**セカンダリ データベースを可用性グループから削除するには**</span><span class="sxs-lookup"><span data-stu-id="151f8-139">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="151f8-140">ディレクトリ変更コマンド (`cd`) を使用して、セカンダリ レプリカをホストするサーバー インスタンスに移動します。</span><span class="sxs-lookup"><span data-stu-id="151f8-140">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="151f8-141">可用性グループから削除する可用性データベース名を指定して、 **Remove-SqlAvailabilityDatabase** コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="151f8-141">Use the **Remove-SqlAvailabilityDatabase** cmdlet, specifying the name of the availability database to be removed from the availability group.</span></span> <span data-ttu-id="151f8-142">セカンダリ レプリカをホストするサーバー インスタンスに接続している場合は、ローカル セカンダリ データベースのみが可用性グループから削除されます。</span><span class="sxs-lookup"><span data-stu-id="151f8-142">When you are connected to a server instance that hosts a secondary replica, only the local secondary database is removed from the availability group.</span></span>  
  
     <span data-ttu-id="151f8-143">たとえば、次のコマンドは、 `MyDb8` という名前のサーバー インスタンスにホストされたセカンダリ レプリカから、セカンダリ データベース `SecondaryComputer\Instance`を削除します。</span><span class="sxs-lookup"><span data-stu-id="151f8-143">For example, the following command removes the secondary database `MyDb8` from the secondary replica hosted by the server instance named `SecondaryComputer\Instance`.</span></span> <span data-ttu-id="151f8-144">削除されたセカンダリ データベースへのデータ同期は行われなくなります。</span><span class="sxs-lookup"><span data-stu-id="151f8-144">Data synchronization to the removed secondary databases ceases.</span></span> <span data-ttu-id="151f8-145">このコマンドは、プライマリ データベースまたはその他のセカンダリ データベースには影響しません。</span><span class="sxs-lookup"><span data-stu-id="151f8-145">This command does not affect the primary database or any other secondary databases.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\SecondaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb8  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="151f8-146">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="151f8-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="151f8-147">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="151f8-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="151f8-148">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="151f8-148">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="151f8-149">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="151f8-149">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-database-from-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="151f8-150">補足情報: セカンダリデータベースを可用性グループから削除した後</span><span class="sxs-lookup"><span data-stu-id="151f8-150">Follow Up: After Removing a Secondary Database from an Availability Group</span></span>  
 <span data-ttu-id="151f8-151">セカンダリ データベースを削除すると、可用性グループに参加しなくなり、削除されたセカンダリ データベースに関するすべての情報が可用性グループによって破棄されます。</span><span class="sxs-lookup"><span data-stu-id="151f8-151">When a secondary database is removed, it is no longer joined to the availability group and all information about the removed secondary database is discarded by the availability group.</span></span> <span data-ttu-id="151f8-152">削除されたセカンダリ データベースは RESTORING 状態になります。</span><span class="sxs-lookup"><span data-stu-id="151f8-152">The removed secondary database is placed in the RESTORING state.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="151f8-153">セカンダリ データベースを削除してしばらくの間は、そのデータベースを可用性グループに再度参加させて、データベース上で AlwaysOn データ同期を再開できることがあります。</span><span class="sxs-lookup"><span data-stu-id="151f8-153">For a short time after removing a secondary database, you might be able to restart AlwaysOn data synchronization on the database by re-joining it to the availability group.</span></span> <span data-ttu-id="151f8-154">詳細については、「 [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="151f8-154">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="151f8-155">この時点で、削除されたセカンダリ データベースを処理する別の方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="151f8-155">At this point there are alternative ways of dealing with a removed secondary database:</span></span>  
  
-   <span data-ttu-id="151f8-156">セカンダリ データベースが不要の場合は、削除できます。</span><span class="sxs-lookup"><span data-stu-id="151f8-156">If you no longer need the secondary database, you can drop it.</span></span>  
  
     <span data-ttu-id="151f8-157">詳細については、「[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)」または「[データベースの削除](../../../relational-databases/databases/delete-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="151f8-157">For more information, see [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) or [Delete a Database](../../../relational-databases/databases/delete-a-database.md).</span></span>  
  
-   <span data-ttu-id="151f8-158">可用性グループから削除された後に、削除されたセカンダリ データベースにアクセスする必要がある場合は、データベースを復元できます。</span><span class="sxs-lookup"><span data-stu-id="151f8-158">If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database.</span></span> <span data-ttu-id="151f8-159">ただし、削除されたセカンダリ データベースを復元すると、異なる 2 つのデータベースが同じ名前でオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="151f8-159">However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online.</span></span> <span data-ttu-id="151f8-160">クライアントが現在のプライマリ データベースのみにアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="151f8-160">You must make sure that clients can access only the current primary database.</span></span>  
  
     <span data-ttu-id="151f8-161">詳細については、「[データを復元しないデータベースの復旧 &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="151f8-161">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151f8-162">参照</span><span class="sxs-lookup"><span data-stu-id="151f8-162">See Also</span></span>  
 <span data-ttu-id="151f8-163">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="151f8-163">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="151f8-164">可用性グループからのプライマリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="151f8-164">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
