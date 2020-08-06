---
title: オブジェクトエクスプローラーの詳細を使用して可用性グループを監視する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.OEdetails.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: 84affc47-40e0-43d9-855e-468967068c35
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 419f1cd22e0a7aa314f6a1036793091bb7b385fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632700"
---
# <a name="use-the-object-explorer-details-to-monitor-availability-groups-sql-server-management-studio"></a><span data-ttu-id="b124f-102">[オブジェクト エクスプローラーの詳細] を使用した可用性グループの監視 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b124f-102">Use the Object Explorer Details to Monitor Availability Groups (SQL Server Management Studio)</span></span>
  <span data-ttu-id="b124f-103">このトピックでは、 **の** [オブジェクト エクスプローラーの詳細] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ペインを使用して、既存の AlwaysOn 可用性グループ、可用性レプリカ、および可用性データベースを監視および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b124f-103">This topic describes how to use the **Object Explorer Details** pane of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to monitor and manage existing AlwaysOn availability groups, availability replicas, and availability databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b124f-104">[オブジェクト エクスプローラーの詳細] ペインの使用方法の詳細については、「 [[オブジェクト エクスプローラーの詳細] ペイン](../../../ssms/object/object-explorer-details-pane.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b124f-104">For information about using the Object Explorer Details pane, see [Object Explorer Details Pane](../../../ssms/object/object-explorer-details-pane.md).</span></span>  
  
-   <span data-ttu-id="b124f-105">**作業を開始する準備:**  [前提条件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="b124f-105">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
-   <span data-ttu-id="b124f-106">**可用性グループを監視するために使用するもの:**  [SQL Server Management Studio](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="b124f-106">**To Monitor an Availability Group, using:**  [SQL Server Management Studio](#SSMSProcedure)</span></span>  
  
-   <span data-ttu-id="b124f-107">**オブジェクト エクスプローラーの詳細:**</span><span class="sxs-lookup"><span data-stu-id="b124f-107">**Object Explorer Details:**</span></span>  
  
     [<span data-ttu-id="b124f-108">可用性グループの詳細</span><span class="sxs-lookup"><span data-stu-id="b124f-108">Availability Group Details</span></span>](#AvGroupsDetails)  
  
     [<span data-ttu-id="b124f-109">可用性レプリカの詳細</span><span class="sxs-lookup"><span data-stu-id="b124f-109">Availability Replica Details</span></span>](#AvReplicaDetails)  
  
     [<span data-ttu-id="b124f-110">可用性データベースの詳細</span><span class="sxs-lookup"><span data-stu-id="b124f-110">Availability Database Details</span></span>](#AvDbDetails)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b124f-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="b124f-111">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="b124f-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="b124f-112">Prerequisites</span></span>  
 <span data-ttu-id="b124f-113">プライマリ レプリカまたはセカンダリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス (サーバー インスタンス) に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b124f-113">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b124f-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b124f-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b124f-115">**可用性グループ、可用性レプリカ、および可用性データベースを監視するには**</span><span class="sxs-lookup"><span data-stu-id="b124f-115">**To monitor availability groups, availability replicas, and availability databases**</span></span>  
  
1.  <span data-ttu-id="b124f-116">[表示] メニューの **[オブジェクト エクスプローラーの詳細]** をクリックするか、 **F7** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b124f-116">On the View menu, click **Object Explorer Details**, or press the **F7** key.</span></span>  
  
2.  <span data-ttu-id="b124f-117">オブジェクト エクスプローラーで、可用性グループを監視する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続し、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b124f-117">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to monitor an availability group, and click the server name to expand the server tree.</span></span>  
  
3.  <span data-ttu-id="b124f-118">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="b124f-118">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
4.  <span data-ttu-id="b124f-119">**[オブジェクト エクスプローラーの詳細]** ペインに、接続したサーバー インスタンスがそのレプリカをホストしている可用性グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-119">The **Object Explorer Details** pane displays every availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="b124f-120">それぞれの可用性グループについて、 **[サーバー インスタンス (プライマリ)]** 列に、プライマリ レプリカを現在ホストしているサーバー インスタンス名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-120">For each availability group, the **Server Instance (Primary)** column displays the name of the server instance that is currently hosting the primary replica.</span></span>  <span data-ttu-id="b124f-121">特定の可用性グループの詳細を表示するには、オブジェクト エクスプ ローラーでそのグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="b124f-121">To display more information about a given availability group, select it in Object Explorer.</span></span>  
  
5.  <span data-ttu-id="b124f-122">**[オブジェクト エクスプローラーの詳細]** ペインに、その可用性グループの **[可用性レプリカ]** と **[可用性データベース]** ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-122">The **Object Explorer Details** pane then displays the **Availability Replicas** and **Availability Databases** nodes for this availability group:</span></span>  
  
    -   <span data-ttu-id="b124f-123">オブジェクト エクスプローラーで **[可用性グループ]** ノードを展開し、 **[可用性レプリカ]** ノードを選択すると、 **[オブジェクト エクスプローラーの詳細]** ペインにグループ内の可用性レプリカの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-123">When you expand the **Availability Group** node in Object Explorer and select the **Availability Replicas** node, the **Object Explorer Details** pane displays information about each of the availability replicas in the group.</span></span> <span data-ttu-id="b124f-124">詳細については、このトピックの「 [可用性レプリカの詳細](#AvReplicaDetails)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b124f-124">For more information, see [Availability Replica Details](#AvReplicaDetails), later in this topic.</span></span>  
  
         <span data-ttu-id="b124f-125">複数の可用性レプリカに対する操作を行うには、それらのレプリカを選択して右クリックし、ショートカット メニューを開きます。ここには、使用できるコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-125">To perform operations on multiple availability replicas, select them, and right-click them to open up a context menu that lists the available commands.</span></span>  
  
    -   <span data-ttu-id="b124f-126">オブジェクト エクスプローラーで **[可用性グループ]** ノードを展開し、 **[可用性データベース]** ノードを選択すると、 **[オブジェクト エクスプローラーの詳細]** ペインにグループ内の可用性データベースの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-126">When you expand the **Availability Group** node in Object Explorer and select the **Availability Databases** node, the **Object Explorer Details** pane displays information about each of the availability databases in the group.</span></span> <span data-ttu-id="b124f-127">詳細については、このトピックの「 [可用性データベースの詳細](#AvDbDetails)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b124f-127">For more information, see [Availability Database Details](#AvDbDetails), later in this topic.</span></span>  
  
         <span data-ttu-id="b124f-128">複数の可用性データベースに対する操作を行うには、それらのデータベースを選択して右クリックし、ショートカット メニューを開きます。ここには、使用できるコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-128">To perform operations on multiple availability databases, select them, and right-click them to open up a context menu that lists the available commands.</span></span>  
  
##  <a name="availability-groups-details"></a><a name="AvGroupsDetails"></a> <span data-ttu-id="b124f-129">可用性グループの詳細</span><span class="sxs-lookup"><span data-stu-id="b124f-129">Availability Groups Details</span></span>  
 <span data-ttu-id="b124f-130">**[可用性グループ]** の詳細画面には、次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-130">The **Availability Groups** details screen displays the following columns:</span></span>  
  
 <span data-ttu-id="b124f-131">**名前**</span><span class="sxs-lookup"><span data-stu-id="b124f-131">**Name**</span></span>  
 <span data-ttu-id="b124f-132">選択した可用性グループの **[可用性レプリカ]** 、 **[可用性データベース]** 、および **[可用性グループ]** リスナー フォルダーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-132">Lists the **Availability Replicas**, **Availability Databases**, and **Availability Group** Listeners folders of the selected availability group.</span></span>  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> <span data-ttu-id="b124f-133">可用性レプリカの詳細</span><span class="sxs-lookup"><span data-stu-id="b124f-133">Availability Replica Details</span></span>  
 <span data-ttu-id="b124f-134">**[可用性レプリカ]** の詳細画面には、次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-134">The **Availability Replica** details screen displays the following columns:</span></span>  
  
 <span data-ttu-id="b124f-135">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="b124f-135">**Server Instance**</span></span>  
 <span data-ttu-id="b124f-136">可用性レプリカをホストするサーバー インスタンス名と、サーバー インスタンスからローカル サーバー インスタンスへの現在の接続状態を示すアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-136">Displays the name of the server instance that hosts the availability replica, along with an icon that indicates the current connection state of the server instance to the local server instance.</span></span>  
  
 <span data-ttu-id="b124f-137">**ロール**</span><span class="sxs-lookup"><span data-stu-id="b124f-137">**Role**</span></span>  
 <span data-ttu-id="b124f-138">可用性レプリカの現在のロール ( **[プライマリ]** または **[セカンダリ]** ) を示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-138">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="b124f-139">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のロールについては、「[AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b124f-139">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
 <span data-ttu-id="b124f-140">**[セカンダリ ロールの接続モード]**</span><span class="sxs-lookup"><span data-stu-id="b124f-140">**Connection Mode in Secondary Role**</span></span>  
 <span data-ttu-id="b124f-141">セカンダリ ロールを実行している (つまりセカンダリ レプリカとして機能している) 特定の可用性レプリカのデータベースがクライアントから接続を受け入れることができるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-141">Indicates whether the databases of a given availability replica that is performing the secondary role (that is, is acting as a secondary replica) can accept connections from clients.</span></span>  
  
 <span data-ttu-id="b124f-142">次のような値が考えられます。</span><span class="sxs-lookup"><span data-stu-id="b124f-142">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="b124f-143">値</span><span class="sxs-lookup"><span data-stu-id="b124f-143">Value</span></span>|<span data-ttu-id="b124f-144">説明</span><span class="sxs-lookup"><span data-stu-id="b124f-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b124f-145">**接続を禁止**</span><span class="sxs-lookup"><span data-stu-id="b124f-145">**Disallow Connections**</span></span>|<span data-ttu-id="b124f-146">この可用性レプリカがセカンダリ レプリカとして動作する場合、可用性データベースに対する直接接続は許可されません。</span><span class="sxs-lookup"><span data-stu-id="b124f-146">No direct connections are allowed to the availability databases when this availability replica is acting as a secondary replica.</span></span> <span data-ttu-id="b124f-147">セカンダリ データベースは読み取りアクセスでは利用できません。</span><span class="sxs-lookup"><span data-stu-id="b124f-147">Secondary databases are not available for read access.</span></span>|  
|<span data-ttu-id="b124f-148">**読み取りを目的とした接続のみを許可**</span><span class="sxs-lookup"><span data-stu-id="b124f-148">**Allow Only Read Intent Connections**</span></span>|<span data-ttu-id="b124f-149">このレプリカがセカンダリ レプリカとして動作する場合、直接接続は、読み取り専用でのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-149">Only direct read-only connections are allowed  when this replica acting as a secondary replica.</span></span> <span data-ttu-id="b124f-150">レプリカ内のすべてのデータベースは読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="b124f-150">All database(s) in the replica are available for read access.</span></span>|  
|<span data-ttu-id="b124f-151">**すべての接続を許可**</span><span class="sxs-lookup"><span data-stu-id="b124f-151">**Allow All Connections**</span></span>|<span data-ttu-id="b124f-152">このレプリカがセカンダリ レプリカとして動作する場合、読み取り専用でこれらのデータベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-152">All connections are allowed to these databases for read-only access when this replica acting as a secondary replica.</span></span>|  
  
 <span data-ttu-id="b124f-153">**接続状態**</span><span class="sxs-lookup"><span data-stu-id="b124f-153">**Connection State**</span></span>  
 <span data-ttu-id="b124f-154">セカンダリ レプリカが現在プライマリ レプリカに接続されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-154">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="b124f-155">次のような値が考えられます。</span><span class="sxs-lookup"><span data-stu-id="b124f-155">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="b124f-156">値</span><span class="sxs-lookup"><span data-stu-id="b124f-156">Value</span></span>|<span data-ttu-id="b124f-157">説明</span><span class="sxs-lookup"><span data-stu-id="b124f-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b124f-158">**切断**</span><span class="sxs-lookup"><span data-stu-id="b124f-158">**Disconnected**</span></span>|<span data-ttu-id="b124f-159">リモート可用性レプリカの場合、ローカル可用性レプリカから切断されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-159">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="b124f-160">接続解除状態のローカル レプリカの応答は、そのロールによって次のように異なります。</span><span class="sxs-lookup"><span data-stu-id="b124f-160">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span><br /><br /> <span data-ttu-id="b124f-161">プライマリ レプリカでは、セカンダリ レプリカが切断されている場合、プライマリ レプリカ上のセカンダリ データベースは **[同期未実行]** とマークされ、プライマリ レプリカはセカンダリが再接続するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="b124f-161">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span><br /><br /> <span data-ttu-id="b124f-162">セカンダリ レプリカでは、切断されていることを検出すると、セカンダリ レプリカはプライマリ レプリカへの再接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="b124f-162">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>|  
|<span data-ttu-id="b124f-163">**接続済み**</span><span class="sxs-lookup"><span data-stu-id="b124f-163">**Connected**</span></span>|<span data-ttu-id="b124f-164">現在ローカル レプリカに接続されているリモート可用性レプリカです。</span><span class="sxs-lookup"><span data-stu-id="b124f-164">A remote availability replica that is currently connected to the local replica.</span></span>|  
|<span data-ttu-id="b124f-165">**NULL**</span><span class="sxs-lookup"><span data-stu-id="b124f-165">**NULL**</span></span>|<span data-ttu-id="b124f-166">ローカル レプリカがセカンダリ レプリカの場合、この値は他のセカンダリ レプリカに対して NULL です。</span><span class="sxs-lookup"><span data-stu-id="b124f-166">If the local replica is a secondary replica, this value is NULL for other secondary replicas.</span></span>|  
  
 <span data-ttu-id="b124f-167">**[同期状態]**</span><span class="sxs-lookup"><span data-stu-id="b124f-167">**Synchronization State**</span></span>  
 <span data-ttu-id="b124f-168">セカンダリ レプリカが現在プライマリ レプリカと同期されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-168">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="b124f-169">次のような値が考えられます。</span><span class="sxs-lookup"><span data-stu-id="b124f-169">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="b124f-170">値</span><span class="sxs-lookup"><span data-stu-id="b124f-170">Value</span></span>|<span data-ttu-id="b124f-171">説明</span><span class="sxs-lookup"><span data-stu-id="b124f-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b124f-172">**[同期未実行]**</span><span class="sxs-lookup"><span data-stu-id="b124f-172">**Not Synchronized**</span></span>|<span data-ttu-id="b124f-173">データベースが同期されていないか、可用性グループにまだ参加していません。</span><span class="sxs-lookup"><span data-stu-id="b124f-173">The database is not synchronized or has not yet been joined to the availability group.</span></span>|  
|<span data-ttu-id="b124f-174">**同期済み**</span><span class="sxs-lookup"><span data-stu-id="b124f-174">**Synchronized**</span></span>|<span data-ttu-id="b124f-175">データベースは、現在のプライマリ レプリカ上、または最後のプライマリ レプリカ上のプライマリ データベースと同期されています。</span><span class="sxs-lookup"><span data-stu-id="b124f-175">The database is synchronized with the primary database on the current primary replica, if any, or on the last primary replica.</span></span><br /><br /> <span data-ttu-id="b124f-176">注:パフォーマンス モードでは、データベースは同期済みの状態にはなりません。</span><span class="sxs-lookup"><span data-stu-id="b124f-176">Note: In performance mode, the database is never in the Synchronized state.</span></span>|  
|<span data-ttu-id="b124f-177">**NULL**</span><span class="sxs-lookup"><span data-stu-id="b124f-177">**NULL**</span></span>|<span data-ttu-id="b124f-178">不明な状態です。</span><span class="sxs-lookup"><span data-stu-id="b124f-178">Unknown state.</span></span> <span data-ttu-id="b124f-179">この値は、ローカル サーバー インスタンスが WSFC フェールオーバー クラスターと通信できない (ローカル ノードが WSFC クォーラムの一部ではない) 場合に生じます。</span><span class="sxs-lookup"><span data-stu-id="b124f-179">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b124f-180">可用性レプリカのパフォーマンス カウンターの詳細については、「 [SQL Server、Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b124f-180">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="availability-database-details"></a><a name="AvDbDetails"></a> <span data-ttu-id="b124f-181">可用性データベースの詳細</span><span class="sxs-lookup"><span data-stu-id="b124f-181">Availability Database Details</span></span>  
 <span data-ttu-id="b124f-182">**[可用性データベース]** の詳細画面には、可用性グループ内の可用性データベースの次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b124f-182">The **Availability Database** details screen displays the following properties of the availability databases in a given availability group:</span></span>  
  
 <span data-ttu-id="b124f-183">**名前**</span><span class="sxs-lookup"><span data-stu-id="b124f-183">**Name**</span></span>  
 <span data-ttu-id="b124f-184">可用性データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="b124f-184">The name of the availability database.</span></span>  
  
 <span data-ttu-id="b124f-185">**[同期状態]**</span><span class="sxs-lookup"><span data-stu-id="b124f-185">**Synchronization State**</span></span>  
 <span data-ttu-id="b124f-186">可用性データベースが現在プライマリ レプリカと同期されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-186">Indicates whether the availability database is currently synchronized with primary replica.</span></span>  
  
 <span data-ttu-id="b124f-187">考えられる同期状態は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b124f-187">The possible synchronization states are as follows:</span></span>  
  
|<span data-ttu-id="b124f-188">値</span><span class="sxs-lookup"><span data-stu-id="b124f-188">Value</span></span>|<span data-ttu-id="b124f-189">説明</span><span class="sxs-lookup"><span data-stu-id="b124f-189">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b124f-190">[同期中]</span><span class="sxs-lookup"><span data-stu-id="b124f-190">Synchronizing</span></span>|<span data-ttu-id="b124f-191">セカンダリ データベースが、ディスクに書き込まれていないプライマリ データベースのトランザクション ログ レコードを受け取りました。</span><span class="sxs-lookup"><span data-stu-id="b124f-191">The secondary database has received the transaction log records for the primary database that are not yet written to disk (hardened).</span></span><br /><br /> <span data-ttu-id="b124f-192">注:非同期コミット モードでは、同期の状態は常に **[同期中]** です。</span><span class="sxs-lookup"><span data-stu-id="b124f-192">Note: In asynchronous-commit mode, the synchronization state is always **Synchronizing**.</span></span>|  
  
 <span data-ttu-id="b124f-193">**中断済み**</span><span class="sxs-lookup"><span data-stu-id="b124f-193">**Suspended**</span></span>  
 <span data-ttu-id="b124f-194">可用性データベースが現在オンラインであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-194">Indicates whether the availability database is currently online.</span></span> <span data-ttu-id="b124f-195">次のような値が考えられます。</span><span class="sxs-lookup"><span data-stu-id="b124f-195">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="b124f-196">値</span><span class="sxs-lookup"><span data-stu-id="b124f-196">Value</span></span>|<span data-ttu-id="b124f-197">説明</span><span class="sxs-lookup"><span data-stu-id="b124f-197">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b124f-198">**中断済み**</span><span class="sxs-lookup"><span data-stu-id="b124f-198">**Suspended**</span></span>|<span data-ttu-id="b124f-199">この状態は、データベースがローカルで中断され、手動で再開する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-199">This state indicates that the database is suspended locally and needs to be manually resumed.</span></span><br /><br /> <span data-ttu-id="b124f-200">プライマリ レプリカでは、セカンダリ データベースの値の信頼性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="b124f-200">On the primary replica, the value is unreliable for a secondary database.</span></span> <span data-ttu-id="b124f-201">セカンダリ データベースが中断されているかどうかを確実に判断するには、データベースをホストするセカンダリ レプリカでクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b124f-201">To reliably determine whether a secondary database is suspended, query it on the secondary replica that hosts the database.</span></span>|  
|<span data-ttu-id="b124f-202">**未参加**</span><span class="sxs-lookup"><span data-stu-id="b124f-202">**Not Joined**</span></span>|<span data-ttu-id="b124f-203">セカンダリ データベースが可用性グループにまだ参加していないか、グループから削除されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-203">Indicates that the secondary database either has not been joined to the availability group or has been removed from the group.</span></span>|  
|<span data-ttu-id="b124f-204">**オンライン**</span><span class="sxs-lookup"><span data-stu-id="b124f-204">**Online**</span></span>|<span data-ttu-id="b124f-205">データベースがローカル可用性レプリカで中断されておらず、データベースが接続されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-205">Indicates that the database is not suspended on the local availability replica and that the database is connected.</span></span>|  
|<span data-ttu-id="b124f-206">**未接続**</span><span class="sxs-lookup"><span data-stu-id="b124f-206">**Not Connected**</span></span>|<span data-ttu-id="b124f-207">セカンダリ レプリカが現在プライマリ レプリカに接続できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="b124f-207">Indicates that the secondary replica is currently unable to connect to the primary replica.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b124f-208">可用性データベースのパフォーマンス カウンターの詳細については、「 [SQL Server、Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b124f-208">For information about performance counters for availability databases, see [SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b124f-209">参照</span><span class="sxs-lookup"><span data-stu-id="b124f-209">See Also</span></span>  
 <span data-ttu-id="b124f-210">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b124f-210">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span></span>  
 <span data-ttu-id="b124f-211">[AlwaysOn ダッシュボード &#40;SQL Server Management Studio を使用&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b124f-211">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="b124f-212">[可用性グループのプロパティの表示 &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b124f-212">[View Availability Group Properties &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md) </span></span>  
 [<span data-ttu-id="b124f-213">可用性レプリカのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b124f-213">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
  
