---
title: AlwaysOn ダッシュボードを使用する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
- Availability Groups [SQL Server], dashboard
ms.assetid: c9ba2589-139e-42bc-99e1-94546717c64d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4ce0072bcd6642dcb4f3ac63e04c98786bd550e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634051"
---
# <a name="use-the-alwayson-dashboard-sql-server-management-studio"></a><span data-ttu-id="98471-102">AlwaysOn ダッシュボードの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="98471-102">Use the AlwaysOn Dashboard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="98471-103">データベース管理者は AlwaysOn ダッシュボードを使用して、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の AlwaysOn 可用性グループ、可用性レプリカ、および可用性データベースの正常性をひとめで確認できるビューを取得します。</span><span class="sxs-lookup"><span data-stu-id="98471-103">Database administrators use the AlwaysOn Dashboard to obtains an at-a-glance view the health of an AlwaysOn availability group and its availability replicas and databases in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="98471-104">AlwaysOn ダッシュボードの一般的な用途を次に示します。</span><span class="sxs-lookup"><span data-stu-id="98471-104">Some of the typical uses for the AlwaysOn Dashboard are:</span></span>  
  
-   <span data-ttu-id="98471-105">手動フェールオーバー用のレプリカの選択。</span><span class="sxs-lookup"><span data-stu-id="98471-105">Choosing a replica for a manual failover.</span></span>  
  
-   <span data-ttu-id="98471-106">フェールオーバーを強制した場合のデータ損失の推定。</span><span class="sxs-lookup"><span data-stu-id="98471-106">Estimating data loss if you force failover.</span></span>  
  
-   <span data-ttu-id="98471-107">データ同期のパフォーマンスの評価。</span><span class="sxs-lookup"><span data-stu-id="98471-107">Evaluating data-synchronization performance.</span></span>  
  
-   <span data-ttu-id="98471-108">同期コミット セカンダリ レプリカのパフォーマンスへの影響の評価。</span><span class="sxs-lookup"><span data-stu-id="98471-108">Evaluating the performance impact of a synchronous-commit secondary replica</span></span>  
  
 <span data-ttu-id="98471-109">AlwaysOn ダッシュボードは、可用性グループの主要な状態およびパフォーマンス インジケーターを提供し、以下の種類の情報を使用して高可用性操作について容易に判断できるようにします。</span><span class="sxs-lookup"><span data-stu-id="98471-109">The AlwaysOn Dashboard provides key availability group states and performance indicators allowing you to easily make high availability operational decisions using the following types of information.</span></span>  
  
-   <span data-ttu-id="98471-110">レプリカのロールアップの状態</span><span class="sxs-lookup"><span data-stu-id="98471-110">Replica roll-up state</span></span>  
  
-   <span data-ttu-id="98471-111">同期のモードと状態</span><span class="sxs-lookup"><span data-stu-id="98471-111">Synchronization mode and state</span></span>  
  
-   <span data-ttu-id="98471-112">推定データ損失</span><span class="sxs-lookup"><span data-stu-id="98471-112">Estimate Data Loss</span></span>  
  
-   <span data-ttu-id="98471-113">推定復旧時間 (再実行による遅延の解消)</span><span class="sxs-lookup"><span data-stu-id="98471-113">Estimated Recovery Time (redo catch up)</span></span>  
  
-   <span data-ttu-id="98471-114">データベース レプリカの詳細</span><span class="sxs-lookup"><span data-stu-id="98471-114">Database Replica details</span></span>  
  
-   <span data-ttu-id="98471-115">同期のモードと状態</span><span class="sxs-lookup"><span data-stu-id="98471-115">Synchronization mode and state</span></span>  
  
-   <span data-ttu-id="98471-116">ログの復元時間</span><span class="sxs-lookup"><span data-stu-id="98471-116">Time to restore log</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="98471-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="98471-117">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="98471-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="98471-118">Prerequisites</span></span>  
 <span data-ttu-id="98471-119">可能性グループのプライマリ レプリカまたはセカンダリ レプリカのどちらかをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス (サーバー インスタンス) に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="98471-119">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica of an availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="98471-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="98471-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="98471-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="98471-121">Permissions</span></span>  
 <span data-ttu-id="98471-122">CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="98471-122">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="to-start-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a><span data-ttu-id="98471-123">AlwaysOn ダッシュボードを開始するには</span><span class="sxs-lookup"><span data-stu-id="98471-123">To start the AlwaysOn Dashboard</span></span>  
  
1.  <span data-ttu-id="98471-124">オブジェクト エクスプローラーで、AlwaysOn ダッシュボードを実行する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="98471-124">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to run the AlwaysOn Dashboard.</span></span>  
  
2.  <span data-ttu-id="98471-125">**[AlwaysOn 高可用性]** ノードを展開し、**[可用性グループ]** ノードを右クリックして、**[ダッシュボードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98471-125">Expand the **AlwaysOn High Availability** node, right-click the **Availability Groups** node, and then click **Show Dashboard**.</span></span>  
  
###  <a name="to-change-alwayson-dashboard-options"></a><a name="DashboardOptions"></a><span data-ttu-id="98471-126">AlwaysOn ダッシュボードのオプションを変更するには</span><span class="sxs-lookup"><span data-stu-id="98471-126">To Change AlwaysOn Dashboard Options</span></span>  
 <span data-ttu-id="98471-127">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の **[オプション]** ダイアログ ボックスを使って、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn ダッシュボードの自動更新と自動定義 AlwaysOn ポリシーの有効化の動作を構成できます。</span><span class="sxs-lookup"><span data-stu-id="98471-127">You can use the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**Options** dialog box to configure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn Dashboard behavior for automatic refreshing and enabling an auto-defined AlwaysOn policy.</span></span>  
  
1.  <span data-ttu-id="98471-128">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98471-128">From the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="98471-129">ダッシュボードを自動的に更新するには、 **[オプション]** ダイアログ ボックスで **[自動更新を有効にする]** を選択し、更新間隔を秒単位で入力して、接続の再試行の回数を入力します。</span><span class="sxs-lookup"><span data-stu-id="98471-129">To automatically refresh the dashboard, in the **Options** dialog box, select **Turn on automatic refresh**, enter the refresh interval in seconds, and then enter the number of times you want to retry the connection.</span></span>  
  
3.  <span data-ttu-id="98471-130">ユーザー定義ポリシーを有効にするには、**[ユーザー定義の AlwaysOn ポリシーを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="98471-130">To enable a user-defined policy, select **Enable user-defined AlwaysOn policy**.</span></span>  
  
##  <a name="availability-group-summary"></a><a name="AvGroupsView"></a> <span data-ttu-id="98471-131">可用性グループの概要</span><span class="sxs-lookup"><span data-stu-id="98471-131">Availability Group Summary</span></span>  
 <span data-ttu-id="98471-132">可用性グループの画面には、接続されているサーバー インスタンスがホストしているレプリカの可用性グループごとに概要を示す行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-132">The availability group screen displays a summary line for each availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="98471-133">このペインには、次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-133">This pane displays the following columns.</span></span>  
  
 <span data-ttu-id="98471-134">**可用性グループ名**</span><span class="sxs-lookup"><span data-stu-id="98471-134">**Availability Group Name**</span></span>  
 <span data-ttu-id="98471-135">接続されているサーバー インスタンスがホストしているレプリカの可用性グループの名前。</span><span class="sxs-lookup"><span data-stu-id="98471-135">The name of an availability group for which the connected server instance hosts a replica.</span></span>  
  
 <span data-ttu-id="98471-136">**プライマリインスタンス**</span><span class="sxs-lookup"><span data-stu-id="98471-136">**Primary Instance**</span></span>  
 <span data-ttu-id="98471-137">可用性グループのプライマリ レプリカをホストしているサーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="98471-137">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="98471-138">**フェールオーバー モード**</span><span class="sxs-lookup"><span data-stu-id="98471-138">**Failover Mode**</span></span>  
 <span data-ttu-id="98471-139">レプリカの構成で指定されているフェールオーバー モードを表示します。</span><span class="sxs-lookup"><span data-stu-id="98471-139">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="98471-140">フェールオーバー モードとして有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="98471-140">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="98471-141">**[自動]** 。</span><span class="sxs-lookup"><span data-stu-id="98471-141">**Automatic**.</span></span> <span data-ttu-id="98471-142">1 つまたは複数のレプリカが自動フェールオーバー モードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-142">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="98471-143">**手動**。</span><span class="sxs-lookup"><span data-stu-id="98471-143">**Manual**.</span></span> <span data-ttu-id="98471-144">自動フェールオーバー モードのレプリカがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-144">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="98471-145">**問題**</span><span class="sxs-lookup"><span data-stu-id="98471-145">**Issues**</span></span>  
 <span data-ttu-id="98471-146">**[問題]** リンクをクリックすると、問題のトラブルシューティングのドキュメントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-146">Click the **Issues** link to open troubleshooting documentation for a given issue.</span></span> <span data-ttu-id="98471-147">AlwaysOn ポリシーのすべての問題の一覧については、「 [AlwaysOn 可用性グループでの運用上の問題の Alwayson ポリシー」 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98471-147">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="98471-148">列見出しをクリックすると、可用性グループの名前、プライマリ インスタンス、フェールオーバー モード、または問題で、可用性グループの情報を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="98471-148">Click the column headings to sort the availability group information by the name of the availability group, primary instance, failover mode, or Issue.</span></span>  
  
##  <a name="availability-group-details"></a><a name="AvGroupDetails"></a> <span data-ttu-id="98471-149">可用性グループの詳細</span><span class="sxs-lookup"><span data-stu-id="98471-149">Availability Group Details</span></span>  
 <span data-ttu-id="98471-150">概要の画面で選択した可用性グループについての以下の詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-150">The following detail information is displayed for the availability group that you select from the summary screen:</span></span>  
  
 <span data-ttu-id="98471-151">**[可用性グループの状態]**</span><span class="sxs-lookup"><span data-stu-id="98471-151">**Availability group state**</span></span>  
 <span data-ttu-id="98471-152">可用性グループの正常性の状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="98471-152">Displays the state of health for the availability group.</span></span>  
  
 <span data-ttu-id="98471-153">**Primary instance**</span><span class="sxs-lookup"><span data-stu-id="98471-153">**Primary instance**</span></span>  
 <span data-ttu-id="98471-154">可用性グループのプライマリ レプリカをホストしているサーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="98471-154">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="98471-155">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="98471-155">**Failover mode**</span></span>  
 <span data-ttu-id="98471-156">レプリカの構成で指定されているフェールオーバー モードを表示します。</span><span class="sxs-lookup"><span data-stu-id="98471-156">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="98471-157">フェールオーバー モードとして有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="98471-157">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="98471-158">**[自動]** 。</span><span class="sxs-lookup"><span data-stu-id="98471-158">**Automatic**.</span></span> <span data-ttu-id="98471-159">1 つまたは複数のレプリカが自動フェールオーバー モードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-159">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="98471-160">**手動**。</span><span class="sxs-lookup"><span data-stu-id="98471-160">**Manual**.</span></span> <span data-ttu-id="98471-161">自動フェールオーバー モードのレプリカがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-161">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="98471-162">**[クラスターの状態]**</span><span class="sxs-lookup"><span data-stu-id="98471-162">**Cluster state**</span></span>  
 <span data-ttu-id="98471-163">接続されているサーバーのインスタンスと可用性グループがメンバー ノードになっているクラスターの名前と状態。</span><span class="sxs-lookup"><span data-stu-id="98471-163">Name and state of the cluster where the instance of the connected server and the availability group is a member node.</span></span>  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> <span data-ttu-id="98471-164">可用性レプリカの詳細</span><span class="sxs-lookup"><span data-stu-id="98471-164">Availability Replica Details</span></span>  
 <span data-ttu-id="98471-165">**[可用性レプリカ]** ペインには、次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-165">The **Availability replica** pane displays the following columns:</span></span>  
  
 <span data-ttu-id="98471-166">**名前**</span><span class="sxs-lookup"><span data-stu-id="98471-166">**Name**</span></span>  
 <span data-ttu-id="98471-167">可用性レプリカをホストするサーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="98471-167">The name of the server instance that hosts the availability replica.</span></span> <span data-ttu-id="98471-168">この列は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-168">This column is shown by default.</span></span>  
  
 <span data-ttu-id="98471-169">**ロール**</span><span class="sxs-lookup"><span data-stu-id="98471-169">**Role**</span></span>  
 <span data-ttu-id="98471-170">可用性レプリカの現在のロール ( **[プライマリ]** または **[セカンダリ]** ) を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-170">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="98471-171">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のロールについては、「[AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98471-171">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span> <span data-ttu-id="98471-172">この列は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-172">This column is shown by default.</span></span>  
  
 <span data-ttu-id="98471-173">**フェールオーバー モード**</span><span class="sxs-lookup"><span data-stu-id="98471-173">**Failover Mode**</span></span>  
 <span data-ttu-id="98471-174">レプリカの構成で指定されているフェールオーバー モードを表示します。</span><span class="sxs-lookup"><span data-stu-id="98471-174">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="98471-175">フェールオーバー モードとして有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="98471-175">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="98471-176">**[自動]** 。</span><span class="sxs-lookup"><span data-stu-id="98471-176">**Automatic**.</span></span> <span data-ttu-id="98471-177">1 つまたは複数のレプリカが自動フェールオーバー モードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-177">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="98471-178">**手動**。</span><span class="sxs-lookup"><span data-stu-id="98471-178">**Manual**.</span></span> <span data-ttu-id="98471-179">自動フェールオーバー モードのレプリカがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-179">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="98471-180">**[同期状態]**</span><span class="sxs-lookup"><span data-stu-id="98471-180">**Synchronization State**</span></span>  
 <span data-ttu-id="98471-181">セカンダリ レプリカが現在プライマリ レプリカと同期されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-181">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="98471-182">この列は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-182">This column is shown by default.</span></span> <span data-ttu-id="98471-183">指定できる値は、</span><span class="sxs-lookup"><span data-stu-id="98471-183">The possible values are:</span></span>  
  
-   <span data-ttu-id="98471-184">**同期されていません**。</span><span class="sxs-lookup"><span data-stu-id="98471-184">**Not Synchronized**.</span></span> <span data-ttu-id="98471-185">レプリカ内の 1 つ以上のデータベースが同期されておらず、可用性グループにまだ参加していません。</span><span class="sxs-lookup"><span data-stu-id="98471-185">One or more databases in the replica are not synchronized or have not yet been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="98471-186">**同期**中です。</span><span class="sxs-lookup"><span data-stu-id="98471-186">**Synchronizing**.</span></span> <span data-ttu-id="98471-187">レプリカ内の 1 つ以上のデータベースは同期されています。</span><span class="sxs-lookup"><span data-stu-id="98471-187">One or more databases in the replica are being synchronized.</span></span>  
  
-   <span data-ttu-id="98471-188">**同期**済み。</span><span class="sxs-lookup"><span data-stu-id="98471-188">**Synchronized**.</span></span> <span data-ttu-id="98471-189">セカンダリ レプリカ内のすべてのデータベースは、現在のプライマリ レプリカ (ある場合) または最後のプライマリ レプリカ上の対応するプライマリ データベースと同期されています。</span><span class="sxs-lookup"><span data-stu-id="98471-189">All databases in the secondary replica are synchronized with the corresponding primary databases on the current primary replica, if any, or on the last primary replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98471-190">パフォーマンス モードでは、データベースは同期済みの状態にはなりません。</span><span class="sxs-lookup"><span data-stu-id="98471-190">In performance mode, the database is never in the synchronized state.</span></span>  
  
-   <span data-ttu-id="98471-191">**NULL**。</span><span class="sxs-lookup"><span data-stu-id="98471-191">**NULL**.</span></span> <span data-ttu-id="98471-192">不明な状態です。</span><span class="sxs-lookup"><span data-stu-id="98471-192">Unknown state.</span></span> <span data-ttu-id="98471-193">この値は、ローカル サーバー インスタンスが WSFC フェールオーバー クラスターと通信できない (ローカル ノードが WSFC クォーラムの一部ではない) 場合に生じます。</span><span class="sxs-lookup"><span data-stu-id="98471-193">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>  
  
 <span data-ttu-id="98471-194">**問題**</span><span class="sxs-lookup"><span data-stu-id="98471-194">**Issues**</span></span>  
 <span data-ttu-id="98471-195">問題の名前が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-195">Lists the issue name.</span></span> <span data-ttu-id="98471-196">この値は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-196">This value is shown by default.</span></span> <span data-ttu-id="98471-197">AlwaysOn ポリシーのすべての問題の一覧については、「 [AlwaysOn 可用性グループでの運用上の問題の Alwayson ポリシー」 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98471-197">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="98471-198">**可用性モード**</span><span class="sxs-lookup"><span data-stu-id="98471-198">**Availability Mode**</span></span>  
 <span data-ttu-id="98471-199">各可用性レプリカのために個別に設定したレプリカ プロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-199">Indicates the replica property that you set separately for each availability replica.</span></span> <span data-ttu-id="98471-200">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-200">This value is hidden by default.</span></span> <span data-ttu-id="98471-201">指定できる値は、</span><span class="sxs-lookup"><span data-stu-id="98471-201">The possible values are:</span></span>  
  
-   <span data-ttu-id="98471-202">**非同期**。</span><span class="sxs-lookup"><span data-stu-id="98471-202">**Asynchronous**.</span></span> <span data-ttu-id="98471-203">セカンダリ レプリカがプライマリ レプリカと同期されることはありません。</span><span class="sxs-lookup"><span data-stu-id="98471-203">The secondary replica never becomes synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="98471-204">**同期**。</span><span class="sxs-lookup"><span data-stu-id="98471-204">**Synchronous**.</span></span> <span data-ttu-id="98471-205">セカンダリ データベースは、プライマリ データベースからの遅れを取り戻すと、この状態になります。データベースでデータの同期が継続されている間は、この状態が続きます。</span><span class="sxs-lookup"><span data-stu-id="98471-205">When catching up to the primary database, a secondary database enters this state, and it remains caught up as long as data synchronization continues for the database.</span></span>  
  
 <span data-ttu-id="98471-206">**プライマリ接続モード**</span><span class="sxs-lookup"><span data-stu-id="98471-206">**Primary Connection Mode**</span></span>  
 <span data-ttu-id="98471-207">プライマリ レプリカへの接続に使用されるモードを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-207">Indicates the mode that is used to connect to the primary replica.</span></span>  <span data-ttu-id="98471-208">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-208">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-209">**セカンダリ接続モード**</span><span class="sxs-lookup"><span data-stu-id="98471-209">**Secondary Connection Mode**</span></span>  
 <span data-ttu-id="98471-210">セカンダリ レプリカへの接続に使用されるモードを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-210">Indicates the mode that is used to connect to the secondary replica.</span></span>  <span data-ttu-id="98471-211">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-211">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-212">**接続状態**</span><span class="sxs-lookup"><span data-stu-id="98471-212">**Connection State**</span></span>  
 <span data-ttu-id="98471-213">セカンダリ レプリカが現在プライマリ レプリカに接続されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-213">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="98471-214">この列は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-214">This column is hidden by default.</span></span> <span data-ttu-id="98471-215">指定できる値は、</span><span class="sxs-lookup"><span data-stu-id="98471-215">The possible values are:</span></span>  
  
-   <span data-ttu-id="98471-216">**切断**されました。</span><span class="sxs-lookup"><span data-stu-id="98471-216">**Disconnected**.</span></span> <span data-ttu-id="98471-217">リモート可用性レプリカの場合、ローカル可用性レプリカから切断されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-217">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="98471-218">接続解除状態のローカル レプリカの応答は、そのロールによって次のように異なります。</span><span class="sxs-lookup"><span data-stu-id="98471-218">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span>  
  
    -   <span data-ttu-id="98471-219">プライマリ レプリカでは、セカンダリ レプリカが切断されている場合、プライマリ レプリカ上のセカンダリ データベースは **[同期未実行]** とマークされ、プライマリ レプリカはセカンダリが再接続するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="98471-219">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span>  
  
    -   <span data-ttu-id="98471-220">セカンダリ レプリカでは、切断されていることを検出すると、セカンダリ レプリカはプライマリ レプリカへの再接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="98471-220">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>  
  
-   <span data-ttu-id="98471-221">**接続さ**れました。</span><span class="sxs-lookup"><span data-stu-id="98471-221">**Connected**.</span></span> <span data-ttu-id="98471-222">現在ローカル レプリカに接続されているリモート可用性レプリカです。</span><span class="sxs-lookup"><span data-stu-id="98471-222">A remote availability replica that is currently connected to the local replica.</span></span>  
  
 <span data-ttu-id="98471-223">**動作状態**</span><span class="sxs-lookup"><span data-stu-id="98471-223">**Operational State**</span></span>  
 <span data-ttu-id="98471-224">セカンダリ レプリカの現在の操作状態を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-224">Indicates the current operational state of the secondary replica.</span></span> <span data-ttu-id="98471-225">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-225">This value is hidden by default.</span></span> <span data-ttu-id="98471-226">指定できる値は、</span><span class="sxs-lookup"><span data-stu-id="98471-226">The possible values are:</span></span>  
  
 <span data-ttu-id="98471-227">**0**.フェールオーバー保留</span><span class="sxs-lookup"><span data-stu-id="98471-227">**0**. Pending failover</span></span>  
  
 <span data-ttu-id="98471-228">**1**.Pending</span><span class="sxs-lookup"><span data-stu-id="98471-228">**1**. Pending</span></span>  
  
 <span data-ttu-id="98471-229">**2**.オンライン</span><span class="sxs-lookup"><span data-stu-id="98471-229">**2**. Online</span></span>  
  
 <span data-ttu-id="98471-230">**3**.Offline</span><span class="sxs-lookup"><span data-stu-id="98471-230">**3**. Offline</span></span>  
  
 <span data-ttu-id="98471-231">**4**.失敗</span><span class="sxs-lookup"><span data-stu-id="98471-231">**4**. Failed</span></span>  
  
 <span data-ttu-id="98471-232">**5**.失敗、クォーラムなし</span><span class="sxs-lookup"><span data-stu-id="98471-232">**5**. Failed, no quorum</span></span>  
  
 <span data-ttu-id="98471-233">**NULL**。</span><span class="sxs-lookup"><span data-stu-id="98471-233">**NULL**.</span></span> <span data-ttu-id="98471-234">レプリカがローカルでない</span><span class="sxs-lookup"><span data-stu-id="98471-234">Replica is not local</span></span>  
  
 <span data-ttu-id="98471-235">**[最後の接続エラー番号]**</span><span class="sxs-lookup"><span data-stu-id="98471-235">**Last Connection Error No.**</span></span>  
 <span data-ttu-id="98471-236">最後の接続エラーの番号。</span><span class="sxs-lookup"><span data-stu-id="98471-236">Number of the last connection error.</span></span>  <span data-ttu-id="98471-237">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-237">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-238">**[最後の接続エラーの説明]**</span><span class="sxs-lookup"><span data-stu-id="98471-238">**Last Connection Error Description**</span></span>  
 <span data-ttu-id="98471-239">最後の接続エラーの説明。</span><span class="sxs-lookup"><span data-stu-id="98471-239">Description of the last connection error.</span></span>  <span data-ttu-id="98471-240">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-240">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-241">**[最後の接続エラーのタイムスタンプ]**</span><span class="sxs-lookup"><span data-stu-id="98471-241">**Last Connection Error Timestamp**</span></span>  
 <span data-ttu-id="98471-242">最後の接続エラーのタイムスタンプ。</span><span class="sxs-lookup"><span data-stu-id="98471-242">Timestamp of the last connection error.</span></span> <span data-ttu-id="98471-243">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-243">This value is hidden by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98471-244">可用性レプリカのパフォーマンス カウンターの詳細については、「 [SQL Server、Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98471-244">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="to-group-availability-group-information"></a><a name="AvDbDetails"></a> <span data-ttu-id="98471-245">可用性グループの情報をグループ化するには</span><span class="sxs-lookup"><span data-stu-id="98471-245">To Group Availability Group Information</span></span>  
 <span data-ttu-id="98471-246">情報をグループ化するには、 **[グループ化]** をクリックし、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="98471-246">To group the information, click **Group by**, and select one of the following:</span></span>  
  
-   <span data-ttu-id="98471-247">**可用性レプリカ**</span><span class="sxs-lookup"><span data-stu-id="98471-247">**Availability replicas**</span></span>  
  
-   <span data-ttu-id="98471-248">**可用性データベース**</span><span class="sxs-lookup"><span data-stu-id="98471-248">**Availability databases**</span></span>  
  
-   <span data-ttu-id="98471-249">**同期状態**</span><span class="sxs-lookup"><span data-stu-id="98471-249">**Synchronization state**</span></span>  
  
-   <span data-ttu-id="98471-250">**フェールオーバーの準備**</span><span class="sxs-lookup"><span data-stu-id="98471-250">**Failover readiness**</span></span>  
  
-   <span data-ttu-id="98471-251">**問題**</span><span class="sxs-lookup"><span data-stu-id="98471-251">**Issues**</span></span>  
  
 <span data-ttu-id="98471-252">グループ化された情報を表示するペインには、次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-252">The pane that displays the grouped information displays the following columns:</span></span>  
  
 <span data-ttu-id="98471-253">**名前**</span><span class="sxs-lookup"><span data-stu-id="98471-253">**Name**</span></span>  
 <span data-ttu-id="98471-254">可用性データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="98471-254">The name of the availability database.</span></span> <span data-ttu-id="98471-255">この値は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-255">This value is shown by default.</span></span>  
  
 <span data-ttu-id="98471-256">**[レプリカ]**</span><span class="sxs-lookup"><span data-stu-id="98471-256">**Replica**</span></span>  
 <span data-ttu-id="98471-257">可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="98471-257">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span> <span data-ttu-id="98471-258">この値は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-258">This value is shown by default.</span></span>  
  
 <span data-ttu-id="98471-259">**[同期状態]**</span><span class="sxs-lookup"><span data-stu-id="98471-259">**Synchronization State**</span></span>  
 <span data-ttu-id="98471-260">可用性データベースが現在プライマリ レプリカと同期されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-260">Indicates whether the availability database is currently synchronized with primary replica.</span></span> <span data-ttu-id="98471-261">この値は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-261">This value is shown by default.</span></span> <span data-ttu-id="98471-262">有効な同期状態は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="98471-262">The possible synchronization states are:</span></span>  
  
-   <span data-ttu-id="98471-263">**[同期されていません]**。</span><span class="sxs-lookup"><span data-stu-id="98471-263">**Not synchronizing**.</span></span>  
  
    -   <span data-ttu-id="98471-264">プライマリ ロールの場合、データベースがそのトランザクション ログを対応するセカンダリ データベースと同期する準備ができていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-264">For the primary role, indicates that the database is not ready to synchronize its transaction log with the corresponding secondary databases.</span></span>  
  
    -   <span data-ttu-id="98471-265">セカンダリ データベースの場合、データベースが接続の問題によりログの同期を開始していないか、データベースが中断されているか、起動中またはロールの切り替え中にデータベースが遷移状態になっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-265">For a secondary database, indicates that the database has not started log synchronization because of a connection issue, is being suspended, or is going through transition states during startup or a role switch.</span></span>  
  
-   <span data-ttu-id="98471-266">**同期**中です。</span><span class="sxs-lookup"><span data-stu-id="98471-266">**Synchronizing**.</span></span>  
  
     <span data-ttu-id="98471-267">プライマリ レプリカの場合:</span><span class="sxs-lookup"><span data-stu-id="98471-267">On a primary replica:</span></span>  
  
    -   <span data-ttu-id="98471-268">プライマリ データベースについては、このデータベースがセカンダリ データベースからのスキャン要求を受け入れる準備ができることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-268">For a primary database, indicates that this database is ready to accept a scan request from a secondary database.</span></span>  
  
    -   <span data-ttu-id="98471-269">セカンダリ データベースについては、そのセカンダリ データベースのアクティブなデータ移動が行われていることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-269">On a secondary replica, indicates that there is active data movement going on for that secondary database.</span></span>  
  
     <span data-ttu-id="98471-270">セカンダリ レプリカの場合、そのレプリカのアクティブなデータ移動が行われていることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-270">On a secondary replica, indicates that there is active data movement going on for that replica.</span></span>  
  
-   <span data-ttu-id="98471-271">**同期**済み。</span><span class="sxs-lookup"><span data-stu-id="98471-271">**Synchronized**.</span></span>  
  
     <span data-ttu-id="98471-272">プライマリ データベースの場合、少なくとも 1 つのセカンダリ データベースが同期されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-272">For a primary database, indicates that at least one secondary database is synchronized.</span></span>  
  
     <span data-ttu-id="98471-273">セカンダリ データベースの場合、対応するプライマリ データベースと同期されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-273">For a secondary database, indicates that the database is synchronized with the corresponding primary database.</span></span>  
  
-   <span data-ttu-id="98471-274">**[元に戻しています]** 。</span><span class="sxs-lookup"><span data-stu-id="98471-274">**Reverting**.</span></span>  
  
     <span data-ttu-id="98471-275">セカンダリ データベースがプライマリ データベースからページをアクティブに取得している場合の元に戻すプロセスのフェーズを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-275">Indicates the phase in the undo process when a secondary database is actively getting pages from the primary database.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="98471-276">データベースが REVERTING 状態の場合、セカンダリ レプリカに強制的にフェールオーバーすると、そのデータベースは起動できない状態のままになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="98471-276">When a database is in the REVERTING state, forcing failover to the secondary replica can leave that database in a state in which it cannot be started.</span></span>  
  
-   <span data-ttu-id="98471-277">**[初期化中]** 。</span><span class="sxs-lookup"><span data-stu-id="98471-277">**Initializing**.</span></span>  
  
     <span data-ttu-id="98471-278">セカンダリ データベースが元に戻す LSN からの遅れを取り戻すために必要なトランザクション ログがセカンダリ レプリカに配布され、書き込まれている場合の元に戻すフェーズを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-278">Indicates the phase of undo when the transaction log required for a secondary database to catch up to the undo LSN is being shipped and hardened on a secondary replica.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="98471-279">データベースが INITIALIZING 状態の場合、セカンダリ レプリカに強制的にフェールオーバーすると、常にそのデータベースは起動できない状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="98471-279">When a database is in the INITIALIZING state, forcing failover to the secondary replica will always leave that database in a state in which it cannot be started.</span></span>  
  
 <span data-ttu-id="98471-280">**[フェールオーバーの準備]**</span><span class="sxs-lookup"><span data-stu-id="98471-280">**Failover Readiness**</span></span>  
 <span data-ttu-id="98471-281">どの可用性レプリカがフェールオーバーできるかを、データ損失の可能性の有無と共に示します。</span><span class="sxs-lookup"><span data-stu-id="98471-281">Indicates which availability replica can be failed over with or without potential data loss.</span></span> <span data-ttu-id="98471-282">この列は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-282">This column is shown by default.</span></span> <span data-ttu-id="98471-283">指定できる値は、</span><span class="sxs-lookup"><span data-stu-id="98471-283">The possible values are:</span></span>  
  
-   <span data-ttu-id="98471-284">**[データ損失]**</span><span class="sxs-lookup"><span data-stu-id="98471-284">**Data Loss**</span></span>  
  
-   <span data-ttu-id="98471-285">**[データ損失なし]**</span><span class="sxs-lookup"><span data-stu-id="98471-285">**No Data Loss**</span></span>  
  
 <span data-ttu-id="98471-286">**問題**</span><span class="sxs-lookup"><span data-stu-id="98471-286">**Issues**</span></span>  
 <span data-ttu-id="98471-287">問題の名前が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-287">Lists the issue name.</span></span> <span data-ttu-id="98471-288">この列は既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-288">This column is shown by default.</span></span> <span data-ttu-id="98471-289">指定できる値は、</span><span class="sxs-lookup"><span data-stu-id="98471-289">The possible values are:</span></span>  
  
-   <span data-ttu-id="98471-290">**[警告]** 。</span><span class="sxs-lookup"><span data-stu-id="98471-290">**Warnings**.</span></span> <span data-ttu-id="98471-291">クリックすると、しきい値と警告の問題が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-291">Click to display the thresholds and warnings issues.</span></span>  
  
-   <span data-ttu-id="98471-292">**[重大]** 。</span><span class="sxs-lookup"><span data-stu-id="98471-292">**Critical**.</span></span> <span data-ttu-id="98471-293">クリックすると、重大な問題が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98471-293">Click to display the critical issues.</span></span>  
  
 <span data-ttu-id="98471-294">AlwaysOn ポリシーのすべての問題の一覧については、「 [AlwaysOn 可用性グループでの運用上の問題の Alwayson ポリシー」 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98471-294">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="98471-295">**中断済み**</span><span class="sxs-lookup"><span data-stu-id="98471-295">**Suspended**</span></span>  
 <span data-ttu-id="98471-296">データベースが **[中断状態]** であるか **[再開]** されたかを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-296">Indicates whether the database is **Suspended** or has been **Resumed**.</span></span> <span data-ttu-id="98471-297">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-297">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-298">**中断の理由**</span><span class="sxs-lookup"><span data-stu-id="98471-298">**Suspend Reason**</span></span>  
 <span data-ttu-id="98471-299">中断状態の理由を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-299">Indicates the reason for the suspended state.</span></span> <span data-ttu-id="98471-300">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-300">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-301">**[推定データ損失] (秒)**</span><span class="sxs-lookup"><span data-stu-id="98471-301">**Estimate Data Loss (seconds)**</span></span>  
 <span data-ttu-id="98471-302">プライマリ レプリカおよびセカンダリ レプリカ内の最後のトランザクション ログ レポートの時間の差分を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-302">Indicates the time difference of the last transaction log record in the primary replica and secondary replica.</span></span> <span data-ttu-id="98471-303">プライマリ レプリカが失敗すると、時間枠内のすべてのトランザクション ログ レコードが失われます。</span><span class="sxs-lookup"><span data-stu-id="98471-303">If the primary replica fails, all transaction log records within the time window will be lost.</span></span> <span data-ttu-id="98471-304">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-304">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-305">**[推定復旧時間] (秒)**</span><span class="sxs-lookup"><span data-stu-id="98471-305">**Estimated Recovery Time (seconds)**</span></span>  
 <span data-ttu-id="98471-306">キャッチアップ時間の再実行にかかる時間を秒単位で示します。</span><span class="sxs-lookup"><span data-stu-id="98471-306">Indicates the time in seconds it takes to redo the catch-up time.</span></span> <span data-ttu-id="98471-307">*キャッチアップ時間* は、セカンダリ レプリカがプライマリ レプリカに追いつくためにかかる時間です。</span><span class="sxs-lookup"><span data-stu-id="98471-307">The *catch-up time* is the time it will take for the secondary replica to catch up with the primary replica.</span></span> <span data-ttu-id="98471-308">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-308">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-309">**[同期のパフォーマンス] (秒)**</span><span class="sxs-lookup"><span data-stu-id="98471-309">**Synchronization Performance (seconds)**</span></span>  
 <span data-ttu-id="98471-310">プライマリ レプリカとセカンダリ レプリカ間の同期にかかる時間を秒単位で示します。</span><span class="sxs-lookup"><span data-stu-id="98471-310">Indicates the time in seconds it takes to synchronize between the primary and secondary replicas.</span></span> <span data-ttu-id="98471-311">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-311">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-312">**[ログ送信キューのサイズ] (KB)**</span><span class="sxs-lookup"><span data-stu-id="98471-312">**Log Send Queue Size (KB)**</span></span>  
 <span data-ttu-id="98471-313">まだセカンダリ レプリカに送信されていない、プライマリ データベースのログ ファイル内のログ レコードの量を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-313">Indicates the amount of log records in the log files of the primary database that have not been sent to the secondary replica.</span></span> <span data-ttu-id="98471-314">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-314">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-315">**[ログの送信速度 (KB/秒)]**</span><span class="sxs-lookup"><span data-stu-id="98471-315">**Log Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="98471-316">ログ レコードがセカンダリ レプリカに送信される比率を 1 秒あたりの KB 単位で示します。この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-316">Indicates the rate in KB per second at which log records are being sent to the secondary replica This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-317">**[再実行キューのサイズ] (KB)**</span><span class="sxs-lookup"><span data-stu-id="98471-317">**Redo Queue Size (KB)**</span></span>  
 <span data-ttu-id="98471-318">まだ再実行されていないセカンダリ レプリカのログ ファイル内のログ レコードの量を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-318">Indicates the amount of log records in the log files of the secondary replica that have not yet been redone.</span></span> <span data-ttu-id="98471-319">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-319">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-320">**[再実行率 (KB/秒)]**</span><span class="sxs-lookup"><span data-stu-id="98471-320">**Redo Rate (KB/sec)**</span></span>  
 <span data-ttu-id="98471-321">ログ レコードが再実行される速度を 1 秒あたりの KB 単位で示します。</span><span class="sxs-lookup"><span data-stu-id="98471-321">Indicates the rate in KB per second at which the log records are being redone.</span></span> <span data-ttu-id="98471-322">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-322">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-323">**[FileStream 送信比率] (KB/秒)**</span><span class="sxs-lookup"><span data-stu-id="98471-323">**FileStream Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="98471-324">トランザクションがレプリカに送信されるときの FileStream の比率を 1 秒あたりの KB 単位で示します。</span><span class="sxs-lookup"><span data-stu-id="98471-324">Indicates the rate of the FileStream in KB per second at which transactions are being sent to the replica.</span></span> <span data-ttu-id="98471-325">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-325">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-326">**[ログ LSN の最後]**</span><span class="sxs-lookup"><span data-stu-id="98471-326">**End of Log LSN**</span></span>  
 <span data-ttu-id="98471-327">プライマリ レプリカおよびセカンダリ レプリカのログ キャッシュ内の最後のログ レコードに対応する実際のログ シーケンス番号 (LSN) を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-327">Indicates the actual log sequence number (LSN) that corresponds to the last log record in the log cache on the primary and secondary replicas.</span></span> <span data-ttu-id="98471-328">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-328">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-329">**[復旧 LSN]**</span><span class="sxs-lookup"><span data-stu-id="98471-329">**Recovery LSN**</span></span>  
 <span data-ttu-id="98471-330">プライマリ レプリカでの復旧後またはフェールオーバー後、レプリカが新しいログ レコードを書き込む前のトランザクション ログの末尾を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-330">Indicates the end of the transaction log before the replica writes any new log records after recovery or failover on the primary replica.</span></span> <span data-ttu-id="98471-331">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-331">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-332">**[切り捨て LSN]**</span><span class="sxs-lookup"><span data-stu-id="98471-332">**Truncation LSN**</span></span>  
 <span data-ttu-id="98471-333">プライマリ レプリカの最小のログ切り捨て値を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-333">Indicates the minimum log truncation value for the primary replica.</span></span> <span data-ttu-id="98471-334">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-334">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-335">**[最後にコミットした LSN]**</span><span class="sxs-lookup"><span data-stu-id="98471-335">**Last Commit LSN**</span></span>  
 <span data-ttu-id="98471-336">トランザクション ログの最終コミット レコードに対応する実際の LSN を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-336">Indicates the actual LSN corresponding to the last commit record in the transaction log.</span></span> <span data-ttu-id="98471-337">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-337">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-338">**[最終コミット時間]**</span><span class="sxs-lookup"><span data-stu-id="98471-338">**Last Commit Time**</span></span>  
 <span data-ttu-id="98471-339">最終コミット レコードに対応する時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-339">Indicates the time corresponding to the last commit record.</span></span> <span data-ttu-id="98471-340">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-340">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-341">**[最後に送信した LSN]**</span><span class="sxs-lookup"><span data-stu-id="98471-341">**Last Sent LSN**</span></span>  
 <span data-ttu-id="98471-342">プライマリ レプリカによって送信されたすべてのログ ブロックの最後のポイントを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-342">Indicates the point up to which all log blocks have been sent by the primary replica.</span></span> <span data-ttu-id="98471-343">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-343">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-344">**[最終送信時間]**</span><span class="sxs-lookup"><span data-stu-id="98471-344">**Last Sent Time**</span></span>  
 <span data-ttu-id="98471-345">ログ ブロックが最後に送信された時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-345">Indicates the time when the last log block was sent.</span></span> <span data-ttu-id="98471-346">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-346">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-347">**[最後に受信した LSN]**</span><span class="sxs-lookup"><span data-stu-id="98471-347">**Last Received LSN**</span></span>  
 <span data-ttu-id="98471-348">セカンダリ データベースをホストするセカンダリ レプリカによって受信されたすべてのログ ブロックの最後のポイントを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-348">Indicates the point up to which all log blocks have been received by the secondary replica that hosts the secondary database.</span></span> <span data-ttu-id="98471-349">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-349">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-350">**[最終受信時間]**</span><span class="sxs-lookup"><span data-stu-id="98471-350">**Last Received Time**</span></span>  
 <span data-ttu-id="98471-351">最後に受信されたメッセージのログ ブロック識別子がセカンダリ レプリカで読み取られた時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-351">Indicates the time when the log block identifier in last message received was read on the secondary replica.</span></span> <span data-ttu-id="98471-352">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-352">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-353">**[最後に書き込まれた LSN]**</span><span class="sxs-lookup"><span data-stu-id="98471-353">**Last Hardened LSN**</span></span>  
 <span data-ttu-id="98471-354">セカンダリ レプリカのディスクにフラッシュされたすべてのログ レコードの最後のポイントを示します。</span><span class="sxs-lookup"><span data-stu-id="98471-354">Indicates the point up to which all log records have been flushed to disk on the secondary replica.</span></span> <span data-ttu-id="98471-355">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-355">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-356">**[最終書き込み時刻]**</span><span class="sxs-lookup"><span data-stu-id="98471-356">**Last Hardened Time**</span></span>  
 <span data-ttu-id="98471-357">セカンダリ レプリカで最後に書き込まれた LSN のためにログ ブロック ID が受信された時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-357">Indicates the time when the log-block identifier was received for the last hardened LSN on the secondary replica.</span></span> <span data-ttu-id="98471-358">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-358">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-359">**[最後に再実行された LSN]**</span><span class="sxs-lookup"><span data-stu-id="98471-359">**Last Redone LSN**</span></span>  
 <span data-ttu-id="98471-360">セカンダリ レプリカで最後に再実行されたログ レコードの実際の LSN を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-360">Indicates the actual LSN of the log record that was redone last on the secondary replica.</span></span> <span data-ttu-id="98471-361">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-361">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="98471-362">**[最終再実行時間]**</span><span class="sxs-lookup"><span data-stu-id="98471-362">**Last Redone Time**</span></span>  
 <span data-ttu-id="98471-363">セカンダリ データベースでログ レコードが最後に再実行された時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="98471-363">Indicates the time when the last log record was redone on the secondary database.</span></span> <span data-ttu-id="98471-364">この値は既定で非表示になります。</span><span class="sxs-lookup"><span data-stu-id="98471-364">This value is hidden by default.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="98471-365">関連タスク</span><span class="sxs-lookup"><span data-stu-id="98471-365">Related Tasks</span></span>  
  
-   [<span data-ttu-id="98471-366">AlwaysOn ポリシーを使用して、可用性グループ &#40;SQL Server の正常性を表示&#41;</span><span class="sxs-lookup"><span data-stu-id="98471-366">Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="98471-367">参照</span><span class="sxs-lookup"><span data-stu-id="98471-367">See Also</span></span>  
 <span data-ttu-id="98471-368">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="98471-368">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span></span>  
 [<span data-ttu-id="98471-369">可用性グループの監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="98471-369">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
