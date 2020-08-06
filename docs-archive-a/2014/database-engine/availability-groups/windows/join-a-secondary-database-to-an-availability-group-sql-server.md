---
title: 可用性グループへのセカンダリ データベースの参加 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0d79325bcde33d13688003de079a42a9601cc41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640231"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a><span data-ttu-id="ec335-102">可用性グループへのセカンダリ データベースの参加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ec335-102">Join a Secondary Database to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="ec335-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec335-103">This topic explains how to join a secondary database to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="ec335-104">セカンダリ レプリカのセカンダリ データベースを準備したら、できるだけ早くそのデータベースを可用性グループに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec335-104">After you prepare a secondary database for a secondary replica, you need to join the database to the availability group as soon as possible.</span></span> <span data-ttu-id="ec335-105">これによって、対応するプライマリ データベースからセカンダリ データベースへのデータの移動が開始されます。</span><span class="sxs-lookup"><span data-stu-id="ec335-105">This will start data movement from the corresponding primary database to the secondary database.</span></span>  
  
-   <span data-ttu-id="ec335-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ec335-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ec335-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="ec335-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ec335-108">Security</span><span class="sxs-lookup"><span data-stu-id="ec335-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ec335-109">**以下を使用してセカンダリ データベースを準備するには:**</span><span class="sxs-lookup"><span data-stu-id="ec335-109">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="ec335-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ec335-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ec335-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ec335-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="ec335-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec335-112">PowerShell</span></span>](#PowerShellProcedure)  
  
> [!NOTE]  
>  <span data-ttu-id="ec335-113">セカンダリデータベースがグループに参加した後の動作については、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の概要](overview-of-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec335-113">For information about what happens after a secondary database joins the group, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ec335-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="ec335-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ec335-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="ec335-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="ec335-116">セカンダリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec335-116">You must be connected to the server instance that hosts the secondary replica.</span></span>  
  
-   <span data-ttu-id="ec335-117">セカンダリ レプリカがあらかじめ可用性グループに参加している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec335-117">The secondary replica must already be joined to the availability group.</span></span> <span data-ttu-id="ec335-118">詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec335-118">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ec335-119">セカンダリ データベースが最近準備されたものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec335-119">The secondary database must have been prepared recently.</span></span> <span data-ttu-id="ec335-120">詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec335-120">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ec335-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ec335-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ec335-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="ec335-122">Permissions</span></span>  
 <span data-ttu-id="ec335-123">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ec335-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ec335-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ec335-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ec335-125">**セカンダリ データベースを可用性グループに参加させるには**</span><span class="sxs-lookup"><span data-stu-id="ec335-125">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="ec335-126">オブジェクト エクスプローラーで、セカンダリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ec335-126">In Object Explorer, connect to the server instance that hosts the secondary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ec335-127">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="ec335-127">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="ec335-128">変更する可用性グループを展開し、 **[可用性データベース]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="ec335-128">Expand the availability group that you want to change, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="ec335-129">データベースを右クリックし、 **[可用性グループへの参加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec335-129">Right-click the database, and click **Join to Availability Group**.</span></span>  
  
5.  <span data-ttu-id="ec335-130">これにより、 **[可用性グループへのデータベースの参加]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="ec335-130">This opens the **Join Databases to Availability Group** dialog box.</span></span> <span data-ttu-id="ec335-131">タイトル バーに表示される可用性グループ名と、グリッドに表示されるデータベースの名前を確認し、 **[OK]** をクリックするか、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec335-131">Verify the availability group name, which is displayed on the title bar, and database name or names displayed in the grid, and click **OK**, or click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ec335-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ec335-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="ec335-133">**セカンダリ データベースを可用性グループに参加させるには**</span><span class="sxs-lookup"><span data-stu-id="ec335-133">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="ec335-134">セカンダリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ec335-134">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="ec335-135">[ALTER DATABASE ステートメントの SET HADR 句](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) を使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="ec335-135">Use the [SET HADR clause of the ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) statement, as follows:</span></span>  
  
     <span data-ttu-id="ec335-136">ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span><span class="sxs-lookup"><span data-stu-id="ec335-136">ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span></span>  
  
     <span data-ttu-id="ec335-137">ここで、 *database_name* は参加させるデータベースの名前で、 *group_name* は可用性グループの名前です。</span><span class="sxs-lookup"><span data-stu-id="ec335-137">where *database_name* is the name of a database to be joined and *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="ec335-138">次の例では、セカンダリ データベース `Db1` を、`MyAG` 可用性グループのローカル セカンダリ レプリカに参加させます。</span><span class="sxs-lookup"><span data-stu-id="ec335-138">The following example joins the secondary database, `Db1`, to the local secondary replica of the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec335-139">コンテキストで使用するこの [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを確認するには、「[可用性グループの作成 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec335-139">To see this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="ec335-140">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="ec335-140">Using PowerShell</span></span>  
 <span data-ttu-id="ec335-141">**セカンダリ データベースを可用性グループに参加させるには**</span><span class="sxs-lookup"><span data-stu-id="ec335-141">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="ec335-142">ディレクトリ変更コマンド (`cd`) を使用して、セカンダリ レプリカをホストするサーバー インスタンスに移動します。</span><span class="sxs-lookup"><span data-stu-id="ec335-142">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="ec335-143">`Add-SqlAvailabilityDatabase` コマンドレットを使用して、セカンダリ データベース (複数可) を可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="ec335-143">Use the `Add-SqlAvailabilityDatabase` cmdlet to join one or more secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="ec335-144">たとえば、次のコマンドでは、セカンダリ レプリカをホストするいずれかのサーバー インスタンスで可用性グループ `Db1`にセカンダリ データベース `MyAG` を参加させます。</span><span class="sxs-lookup"><span data-stu-id="ec335-144">For example, the following command joins a secondary database, `Db1`, to the availability group `MyAG` on one of the server instances that hosts a secondary replica.</span></span>  
  
    ```powershell
    Add-SqlAvailabilityDatabase -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec335-145">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec335-145">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="ec335-146">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec335-146">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="ec335-147">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="ec335-147">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="ec335-148">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="ec335-148">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ec335-149">関連タスク</span><span class="sxs-lookup"><span data-stu-id="ec335-149">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ec335-150">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ec335-150">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ec335-151">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ec335-151">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec335-152">参照</span><span class="sxs-lookup"><span data-stu-id="ec335-152">See Also</span></span>  
 <span data-ttu-id="ec335-153">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ec335-153">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span></span>  
 <span data-ttu-id="ec335-154">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ec335-154">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="ec335-155">SQL Server&#41;削除された AlwaysOn 可用性グループ構成 &#40;のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ec335-155">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
