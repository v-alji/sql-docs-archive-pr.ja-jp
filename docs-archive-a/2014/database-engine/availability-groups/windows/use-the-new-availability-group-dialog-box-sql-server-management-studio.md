---
title: '[新しい可用性グループ] ダイアログ ボックスの使用 (SQL Server Management Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 1b0a6421-fbd4-4bb4-87ca-657f4782c433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 811710051089dfeb402e59bf1b7f45d05c84d925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634641"
---
# <a name="use-the-new-availability-group-dialog-box-sql-server-management-studio"></a><span data-ttu-id="69480-102">[新しい可用性グループ] ダイアログ ボックスの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="69480-102">Use the New Availability Group Dialog Box (SQL Server Management Studio)</span></span>
  <span data-ttu-id="69480-103">このトピックでは、 **の** [新しい可用性グループ] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用して、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] が有効な [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69480-103">This topic contains information about how to use the **New Availability Group** dialog box of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to create an AlwaysOn availability group on instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that are enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="69480-104">*可用性グループ* は、1 つのまとまりとしてフェールオーバーする一連のユーザー データベースと、フェールオーバーをサポートする一連のフェールオーバー パートナー ( *可用性レプリカ*) を定義します。</span><span class="sxs-lookup"><span data-stu-id="69480-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69480-105">可用性グループの概要については、「[AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69480-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  

> [!NOTE]  
>  <span data-ttu-id="69480-106">可用性グループを作成する別の方法については、このトピックの後の「 [関連タスク](#RelatedTasks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69480-106">For information about alternative ways to create an availability group, see [Related Tasks](#RelatedTasks), later in this topic.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="69480-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="69480-107">Before You Begin</span></span>  
 <span data-ttu-id="69480-108">可用性グループを初めて作成する場合は、あらかじめこのセクションに目を通しておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="69480-108">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="69480-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="69480-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="69480-110">可用性グループを作成する前に、可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが同じ Windows Server フェールオーバー クラスタリング (WSFC) フェールオーバー クラスター内の別の WSFC ノードに存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="69480-110">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="69480-111">さらに、各サーバー インスタンスで [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] が有効であり、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に関するその他の前提条件がすべて満たされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="69480-111">Also, verify that each of the server instance is enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="69480-112">詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」をお読みいただくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="69480-112">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="69480-113">可用性グループを作成する前に、可用性レプリカをホストするすべてのサーバー インスタンスでデータベース ミラーリング エンドポイントが完全に機能することを確認します。</span><span class="sxs-lookup"><span data-stu-id="69480-113">Before you create an availability group, ensure that every server instance that will host an availability replica has a fully functioning database mirroring endpoint.</span></span> <span data-ttu-id="69480-114">詳細については、「 [データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69480-114">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
-   <span data-ttu-id="69480-115">**[新しい可用性グループ]** ダイアログ ボックスを使用するには、可用性レプリカをホストするサーバー インスタンスの名前がわかっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69480-115">To use the **New Availability Group** dialog box, you need to know the names of the server instances that will host availability replicas.</span></span> <span data-ttu-id="69480-116">さらに、新しい可用性グループに追加するすべてのデータベースの名前がわかっている必要があるほか、これらのデータベースが「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」に記載されている可用性データベースの前提条件および制限を満たすことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69480-116">Also, you need know the names of any databases that you intend to add to your new availability group, and you need to ensure that these databases meet the availability database prerequisites and restrictions described in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span> <span data-ttu-id="69480-117">無効な値を入力した場合、新しい可用性グループは機能しません。</span><span class="sxs-lookup"><span data-stu-id="69480-117">If you enter invalid values, the new availability group will not work.</span></span>  
  
###  <a name="limitations"></a><a name="Limitations"></a> <span data-ttu-id="69480-118">制限事項</span><span class="sxs-lookup"><span data-stu-id="69480-118">Limitations</span></span>  
 <span data-ttu-id="69480-119">**[新しい可用性グループ]** ダイアログ ボックスでは、次の操作を実行できません。</span><span class="sxs-lookup"><span data-stu-id="69480-119">The **New Availability Group** dialog box does not:</span></span>  
  
-   <span data-ttu-id="69480-120">[可用性グループ リスナーの作成]</span><span class="sxs-lookup"><span data-stu-id="69480-120">Create an availability group listener.</span></span>  
  
-   <span data-ttu-id="69480-121">セカンダリ レプリカの可用性グループへの参加</span><span class="sxs-lookup"><span data-stu-id="69480-121">Join secondary replicas to the availability group.</span></span>  
  
-   <span data-ttu-id="69480-122">最初のデータの同期の実行</span><span class="sxs-lookup"><span data-stu-id="69480-122">Perform initial data synchronization.</span></span>  
  
 <span data-ttu-id="69480-123">これらの構成タスクの詳細については、[補足情報: 可用性グループを作成した後](#FollowUp)に関する情報 (このトピックで後述) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69480-123">For information about these configuration tasks, see [Follow Up: After Creating an Availability Group](#FollowUp), later in this topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="69480-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="69480-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="69480-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="69480-125">Permissions</span></span>  
 <span data-ttu-id="69480-126">**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="69480-126">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-the-new-availability-group-dialog-box-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="69480-127">[新しい可用性グループ] ダイアログ ボックスの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="69480-127">Using the New Availability Group Dialog Box (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="69480-128">**可用性グループを作成するには**</span><span class="sxs-lookup"><span data-stu-id="69480-128">**To create an availability group**</span></span>  
  
1.  <span data-ttu-id="69480-129">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69480-129">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name.</span></span>  
  
2.  <span data-ttu-id="69480-130">**[AlwaysOn 高可用性]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="69480-130">Expand the **AlwaysOn High Availability** node.</span></span>  
  
3.  <span data-ttu-id="69480-131">**[可用性グループ]** ノードを右クリックし、 **[新しい可用性グループ]** コマンドを選択します。</span><span class="sxs-lookup"><span data-stu-id="69480-131">Right-click the **Availability Groups** node, and select the **New Availability Group** command.</span></span>  
  
4.  <span data-ttu-id="69480-132">**[新しい可用性グループ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="69480-132">This command opens up the **New Availability Group** dialog box.</span></span>  
  
5.  <span data-ttu-id="69480-133">**[全般]** ページで、 **[可用性グループ名]** ボックスに新しい可用性グループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="69480-133">On the **General** page, use the **Availability group name** field to enter a name for the new availability group.</span></span> <span data-ttu-id="69480-134">この名前は、WSFC クラスター内のすべての可用性グループ間で一意の有効な SQL Server 識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="69480-134">This name must be a valid SQL Server identifier that is unique across all availability groups in the WSFC cluster.</span></span> <span data-ttu-id="69480-135">可用性グループ名の最大文字数は 128 文字です。</span><span class="sxs-lookup"><span data-stu-id="69480-135">The maximum length for an availability group name is 128 characters.</span></span>  
  
6.  <span data-ttu-id="69480-136">**[可用性データベース]** グリッドで、 **[追加]** をクリックし、この可用性グループの所属先のローカル テータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="69480-136">In the **Availability Databases** grid, click **Add** and enter the name of a local database that you want to belong to this availability group.</span></span> <span data-ttu-id="69480-137">追加するすべてのデータベースに対してこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="69480-137">Repeat this for every database to be added.</span></span> <span data-ttu-id="69480-138">**[OK]** をクリックすると、指定したデータベースを可用性グループに参加させるための前提条件が満たされているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="69480-138">When you click **OK**, the dialog will verify whether your specified database meet the prerequisites for belonging to an availability group.</span></span> <span data-ttu-id="69480-139">これらの前提条件については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69480-139">For information about these prerequisites, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
7.  <span data-ttu-id="69480-140">**[可用性データベース]** グリッドで、 **[追加]** をクリックし、セカンダリ レプリカをホストするサーバー インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="69480-140">In the **Availability Databases** grid, click **Add** and enter the name of a server instance to host a secondary replica.</span></span> <span data-ttu-id="69480-141">これらのインスタンスへの接続は試行されません。</span><span class="sxs-lookup"><span data-stu-id="69480-141">The dialog will not attempt to connect to these instances.</span></span> <span data-ttu-id="69480-142">無効なサーバー名を指定した場合、セカンダリ レプリカは追加されますが、このレプリカに接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="69480-142">If you specify an incorrect server name, a secondary replica will be added but you will be unable to connect to that replica.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="69480-143">レプリカを追加した後ホスト サーバー インスタンスに接続できない場合は、このレプリカを削除し、新しいレプリカを追加できます。</span><span class="sxs-lookup"><span data-stu-id="69480-143">If you have added a replica and cannot connect to the host server instance, you can remove the replica and add a new one.</span></span> <span data-ttu-id="69480-144">詳細については、「[可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)」および「[可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69480-144">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) and [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="69480-145">ダイアログ ボックスの **[ページの選択]** ペインで、 **[バックアップの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69480-145">On the **Select a page** pane of the dialog box, click **Backup Preferences**.</span></span> <span data-ttu-id="69480-146">次に、 **[バックアップの設定]** ページで、レプリカのロールに基づいてどこでバックアップを実行するかを指定し、この可用性グループの可用性レプリカをホストするそれぞれのサーバー インスタンスにバックアップの優先順位を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="69480-146">Then, on the **Backup Preferences** page, specify where backups should occur based on replica role and assign backup priorities to each server instances that will host an availability replica for this availability group.</span></span> <span data-ttu-id="69480-147">詳細については、「[可用性グループのプロパティ: 新しい可用性グループ &#40;[バックアップの設定] ページ&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69480-147">For more information, see [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
9. <span data-ttu-id="69480-148">可用性グループを作成するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69480-148">To create the availability group, click **OK**.</span></span> <span data-ttu-id="69480-149">これにより、指定したデータベースが前提条件を満たしているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="69480-149">This causes the dialog to verify whether that specified databases meet the prerequisites.</span></span>  
  
     <span data-ttu-id="69480-150">可用性グループを作成しないでダイアログ ボックスを終了するには、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69480-150">To exit the dialog box without creating the availability group, click **Cancel**.</span></span>  
  
##  <a name="follow-up-after-using-the-new-availability-group-dialog-box-to-create-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="69480-151">補足情報: [新しい可用性グループ] ダイアログ ボックスを使用して可用性グループを作成した後</span><span class="sxs-lookup"><span data-stu-id="69480-151">Follow Up: After Using the New Availability Group Dialog Box to Create an Availability Group</span></span>  
  
-   <span data-ttu-id="69480-152">可用性グループのセカンダリ レプリカをホストするそれぞれのサーバー インスタンスに接続し、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69480-152">You will need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:</span></span>  
  
    1.  <span data-ttu-id="69480-153">セカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="69480-153">Join the secondary replica to the availability group.</span></span> <span data-ttu-id="69480-154">詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69480-154">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
    2.  <span data-ttu-id="69480-155">各プライマリ データベースとそのトランザクション ログの最新のバックアップを復元します (RESTORE WITH NORECOVERY を使用)。</span><span class="sxs-lookup"><span data-stu-id="69480-155">Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY).</span></span> <span data-ttu-id="69480-156">詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69480-156">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
    3.  <span data-ttu-id="69480-157">新しく準備された各セカンダリ データベースを可用性グループにすぐに参加させます。</span><span class="sxs-lookup"><span data-stu-id="69480-157">Immediately join each newly prepared secondary database to the availability group.</span></span> <span data-ttu-id="69480-158">詳細については、「 [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69480-158">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
-   <span data-ttu-id="69480-159">新しい可用性グループに対して可用性グループ リスナーを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="69480-159">We recommend that you create an availability group listener for the new availability group.</span></span> <span data-ttu-id="69480-160">そのためには、現在のプライマリ レプリカをホストするサーバー インスタンスに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69480-160">This requires that you be connected to the server instance that hosts the current primary replica.</span></span> <span data-ttu-id="69480-161">詳細については、「 [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69480-161">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="69480-162">関連タスク</span><span class="sxs-lookup"><span data-stu-id="69480-162">Related Tasks</span></span>  
 <span data-ttu-id="69480-163">**可用性グループおよびレプリカのプロパティを構成するには**</span><span class="sxs-lookup"><span data-stu-id="69480-163">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="69480-164">可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-164">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="69480-165">可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-165">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="69480-166">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-166">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="69480-167">自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 (AlwaysOn 可用性グループ)</span><span class="sxs-lookup"><span data-stu-id="69480-167">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="69480-168">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-168">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="69480-169">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-169">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="69480-170">可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-170">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="69480-171">可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-171">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="69480-172">可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-172">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="69480-173">**可用性グループの構成を完了するには**</span><span class="sxs-lookup"><span data-stu-id="69480-173">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="69480-174">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-174">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="69480-175">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-175">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="69480-176">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-176">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="69480-177">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-177">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="69480-178">**別の方法で可用性グループを作成する**</span><span class="sxs-lookup"><span data-stu-id="69480-178">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="69480-179">可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-179">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="69480-180">可用性グループの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-180">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="69480-181">可用性グループの作成 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-181">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="69480-182">**AlwaysOn 可用性グループを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="69480-182">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="69480-183">AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-183">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="69480-184">**データベース ミラーリング エンドポイントを構成するには**</span><span class="sxs-lookup"><span data-stu-id="69480-184">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="69480-185">AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-185">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="69480-186">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-186">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="69480-187">データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-187">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="69480-188">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-188">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="69480-189">**AlwaysOn 可用性グループの構成のトラブルシューティング方法**</span><span class="sxs-lookup"><span data-stu-id="69480-189">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="69480-190">AlwaysOn 可用性グループ構成 (SQL Server) の削除に関するトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="69480-190">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="69480-191">失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-191">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="69480-192">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="69480-192">Related Content</span></span>  
  
-   [<span data-ttu-id="69480-193">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="69480-193">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a><span data-ttu-id="69480-194">参照</span><span class="sxs-lookup"><span data-stu-id="69480-194">See Also</span></span>  
 <span data-ttu-id="69480-195">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="69480-195">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="69480-196">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="69480-196">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="69480-197">[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="69480-197">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="69480-198">AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;</span><span class="sxs-lookup"><span data-stu-id="69480-198">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
