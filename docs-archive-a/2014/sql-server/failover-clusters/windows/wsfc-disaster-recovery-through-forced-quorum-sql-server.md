---
title: WSFC の強制クォーラムによる災害復旧 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: 6cefdc18-899e-410c-9ae4-d6080f724046
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2c9399472c6e67c9e2121a008f9283ba05943da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640514"
---
# <a name="wsfc-disaster-recovery-through-forced-quorum-sql-server"></a><span data-ttu-id="dc584-102">WSFC の強制クォーラムによる災害復旧 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dc584-102">WSFC Disaster Recovery through Forced Quorum (SQL Server)</span></span>
  <span data-ttu-id="dc584-103">クォーラム障害は、通常、システム障害、永続的な通信障害、または WSFC クラスター内の複数のノードにおける不適切な構成が原因で発生します。</span><span class="sxs-lookup"><span data-stu-id="dc584-103">Quorum failure is usually caused by a systemic disaster, or a persistent communications failure, or a misconfiguration involving several nodes in the WSFC cluster.</span></span>  <span data-ttu-id="dc584-104">クォーラム障害からの復旧には、手動による介入が必要になります。</span><span class="sxs-lookup"><span data-stu-id="dc584-104">Manual intervention is required to recovery from a quorum failure.</span></span>  
  
-   <span data-ttu-id="dc584-105">**開始前の準備:**  [前提条件](#Prerequisites)、 [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="dc584-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="dc584-106">**強制クォーラムの手順による WSFC のディザスター リカバリー** [強制クォーラムの手順による WSFC のディザスター リカバリー](#Main)</span><span class="sxs-lookup"><span data-stu-id="dc584-106">**WSFC Disaster Recovery through the Forced Quorum Procedure** [WSFC Disaster Recovery through the Forced Quorum Procedure](#Main)</span></span>  
  
-   [<span data-ttu-id="dc584-107">関連タスク</span><span class="sxs-lookup"><span data-stu-id="dc584-107">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="dc584-108">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="dc584-108">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dc584-109">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="dc584-109">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="dc584-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="dc584-110">Prerequisites</span></span>  
 <span data-ttu-id="dc584-111">強制クォーラムの手順では、クォーラム障害の発生前に、正常なクォーラムが存在していたことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="dc584-111">The Forced Quorum Procedure assumes that a healthy quorum existed before the quorum failure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="dc584-112">ユーザーは、Windows Server フェールオーバー クラスタリング、WSFC クォーラム モデル、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、および環境に固有の配置構成の概念および操作に関する十分な知識を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc584-112">The user should be well-informed on the concepts and interactions of Windows Server Failover Clustering, WSFC Quorum Models, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the environment's specific deployment configuration.</span></span>  
>   
>  <span data-ttu-id="dc584-113">詳細については、「  [Windows Server フェールオーバー クラスタリング (WSFC) と SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC クォーラム モードと投票の構成 (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc584-113">For more information, see:  [Windows Server Failover Clustering (WSFC) with SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC Quorum Modes and Voting Configuration (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dc584-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="dc584-114">Security</span></span>  
 <span data-ttu-id="dc584-115">ユーザーは、WSFC クラスターの各ノードのローカル Administrators グループのメンバーであるドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc584-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="wsfc-disaster-recovery-through-the-forced-quorum-procedure"></a><a name="Main"></a> <span data-ttu-id="dc584-116">WSFC の強制クォーラムの手順による災害復旧</span><span class="sxs-lookup"><span data-stu-id="dc584-116">WSFC Disaster Recovery through the Forced Quorum Procedure</span></span>  
 <span data-ttu-id="dc584-117">クォーラム障害が発生すると、クラスターの構成どおりにノード レベルのフォールト トレランスを確保できなくなるため、WSFC クラスター内のクラスター化されているサービス、SQL Server インスタンス、および [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]がすべてオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="dc584-117">Remember that quorum failure will cause all clustered services, SQL Server instances, and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], in the WSFC cluster to be set offline, because the cluster, as configured, cannot ensure node-level fault tolerance.</span></span>  <span data-ttu-id="dc584-118">クォーラム障害は、WSFC クラスター内の正常な投票ノードがクォーラム モデルを満たさなくなったことを意味します。</span><span class="sxs-lookup"><span data-stu-id="dc584-118">A quorum failure means that healthy voting nodes in the WSFC cluster no longer satisfy the quorum model.</span></span> <span data-ttu-id="dc584-119">ノードによって、まったく機能しなくなるものもあれば、WSFC サービスがシャットダウンしただけで、クォーラムと通信できなくなったことを除けば正常なものもあります。</span><span class="sxs-lookup"><span data-stu-id="dc584-119">Some nodes may have failed completely, and some may have just shut down the WSFC service and are otherwise healthy, except for the loss of the ability to communicate with a quorum.</span></span>  
  
 <span data-ttu-id="dc584-120">WSFC クラスターをオンラインに戻すには、既存の構成でクォーラム障害の根本的な原因を解決し、影響を受けたデータベースを必要に応じて復元する必要があります。また、稼働しているクラスター トポロジを反映させるために、WSFC クラスター内の残りのノードの再構成が必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="dc584-120">To bring the WSFC cluster back online, you must correct the root cause of the quorum failure under the existing configuration, recover the affected databases as needed, and you may want to reconfigure the remaining nodes in the WSFC cluster to reflect the surviving cluster topology.</span></span>  
  
 <span data-ttu-id="dc584-121">WSFC クラスター ノードで *強制クォーラム* の手順を使用して、クラスターをオフラインにした安全管理をオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="dc584-121">You can use the *forced quorum* procedure on a WSFC cluster node to override the safety controls that took the cluster offline.</span></span>  <span data-ttu-id="dc584-122">これにより、クラスターでのクォーラム投票のチェックが実質的に中断され、クラスター内の任意のノードで WSFC クラスター リソースと SQL Server をオンラインに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="dc584-122">This effectively tells the cluster to suspend the quorum voting checks, and lets you bring the WSFC cluster resources and SQL Server back online on any of the nodes in the cluster.</span></span>  
  
 <span data-ttu-id="dc584-123">この種のディザスター リカバリー プロセスの手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dc584-123">This type of disaster recovery process should include the following steps:</span></span>  
  
#### <a name="to-recover-from-quorum-failure"></a><span data-ttu-id="dc584-124">クォーラム障害から復旧するには:</span><span class="sxs-lookup"><span data-stu-id="dc584-124">To Recover from Quorum Failure:</span></span>  
  
1.  <span data-ttu-id="dc584-125">**障害の範囲を特定します。**</span><span class="sxs-lookup"><span data-stu-id="dc584-125">**Determine the scope of the failure.**</span></span> <span data-ttu-id="dc584-126">応答しない可用性グループや SQL Server インスタンス、災害後に使用できるオンラインのクラスター ノードをそれぞれ特定し、Windows イベント ログと SQL Server システム ログを確認します。</span><span class="sxs-lookup"><span data-stu-id="dc584-126">Identify which availability groups or SQL Server instances are non-responsive, which cluster nodes are online and available for post-disaster use, and examine the Windows event logs and the SQL Server system logs.</span></span>  <span data-ttu-id="dc584-127">必要に応じて、後で分析できるように解析データやシステム ログを保存しておきます。</span><span class="sxs-lookup"><span data-stu-id="dc584-127">Where practical, you should preserve forensic data and system logs for later analysis.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="dc584-128">応答している [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]インスタンスで、 [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) 動的管理ビュー (DMV) クエリを実行して、ローカル サーバー インスタンスに可用性レプリカを保持している可用性グループの正常性に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="dc584-128">On a responsive instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can obtain information about the health of availability groups that possess an availability replica on the local server instance by querying the [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) dynamic management view (DMV).</span></span>  
  
2.  <span data-ttu-id="dc584-129">**1 つのノードで強制クォーラムを使用して WSFC クラスターを起動します。**</span><span class="sxs-lookup"><span data-stu-id="dc584-129">**Start the WSFC cluster by using forced quorum on a single node.**</span></span> <span data-ttu-id="dc584-130">WSFC クラスター サービスがシャットダウンしたもの以外で、コンポーネントの障害が最も少ないノードを特定し、</span><span class="sxs-lookup"><span data-stu-id="dc584-130">Identify a node with a minimal number of component failures, other than that the WSFC cluster service was shut down.</span></span>  <span data-ttu-id="dc584-131">そのノードが他の大半のノードと通信できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dc584-131">Verify that this node can communicate with a majority of the other nodes.</span></span>  
  
     <span data-ttu-id="dc584-132">このノードで、強制クォーラムの手順に従って、クラスターを手動で強制的にオンラインにします。</span><span class="sxs-lookup"><span data-stu-id="dc584-132">On this node, manually force the cluster to come online using the forced quorum procedure.</span></span>  <span data-ttu-id="dc584-133">データ損失の可能性を最小限に抑えるには、可用性グループのプライマリ レプリカを最後にホストしていたノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc584-133">To minimize potential data loss, select a node that was last hosting an availability group primary replica.</span></span>  
  
     <span data-ttu-id="dc584-134">詳細については、「  [クォーラムを使用せずに WSFC クラスターを強制的に起動する](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc584-134">For more information, see:  [Force a WSFC Cluster to Start Without a Quorum](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc584-135">強制クォーラムの設定はクラスター全体に影響します。論理的 WSFC クラスターの投票が過半数に達し、通常のクォーラム モードの動作に自動的に切り替わるまで、クラスター全体のクォーラムのチェックがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="dc584-135">The forced quorum setting has a cluster-wide affect to block quorum checks until the logical WSFC cluster achieves a majority of votes and automatically transitions to a regular quorum mode of operation.</span></span>  
  
3.  <span data-ttu-id="dc584-136">**他の正常な各ノードで、一度に 1 つずつ、通常の方法で WSFC サービスを起動します。**</span><span class="sxs-lookup"><span data-stu-id="dc584-136">**Start the WSFC service normally on each otherwise healthy node, one at a time.**</span></span> <span data-ttu-id="dc584-137">他のノードでクラスター サービスを起動するときは、強制クォーラム オプションを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dc584-137">You do not have to specify the forced quorum option when you start the cluster service on the other nodes.</span></span>  
  
     <span data-ttu-id="dc584-138">各ノードの WSFC サービスがオンラインに戻ると、他の正常なノードとの間でネゴシエーションが行われ、新しいクラスター構成の状態が同期されます。</span><span class="sxs-lookup"><span data-stu-id="dc584-138">As the WSFC service on each node comes back online, it negotiates with the other healthy nodes to synchronize the new cluster configuration state.</span></span>  <span data-ttu-id="dc584-139">この手順は、クラスターの最新の状態を解決するときに競合状態が発生するのを回避するために、必ず一度に 1 つのノードで行うようにしてください。</span><span class="sxs-lookup"><span data-stu-id="dc584-139">Remember to do this one node at a time to prevent potential race conditions in resolving the last known state of the cluster.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="dc584-140">起動した各ノードが新たにオンラインにした他のノードと通信できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dc584-140">Ensure that each node that you start can communicate with the other newly online nodes.</span></span>  <span data-ttu-id="dc584-141">他のノードでは WSFC サービスを無効にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="dc584-141">Consider disabling the WSFC service on the other nodes.</span></span>  <span data-ttu-id="dc584-142">そうしないと、クォーラム ノード セットが複数作成される可能性があります。これをスプリット ブレイン シナリオと呼びます。</span><span class="sxs-lookup"><span data-stu-id="dc584-142">Otherwise,  you run the risk of creating more than one quorum node set; that is a split-brain scenario.</span></span> <span data-ttu-id="dc584-143">手順 1. の結果に問題がなければ、この現象は発生しません。</span><span class="sxs-lookup"><span data-stu-id="dc584-143">If your findings in step 1 were accurate, this should not occur.</span></span>  
  
4.  <span data-ttu-id="dc584-144">**新しいクォーラム モードとノードの投票の構成を適用します。**</span><span class="sxs-lookup"><span data-stu-id="dc584-144">**Apply new quorum mode and node vote configuration.**</span></span> <span data-ttu-id="dc584-145">クォーラムを強制することによってクラスターのすべてのノードが正常に再起動し、クォーラムのエラーの根本原因が修正された場合、元のクォーラム モードとノードの投票の構成に対する変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="dc584-145">If forcing quorum successfully restarted all the nodes in the cluster and the root cause of the quorum failure has been corrected, changes to the original quorum mode and node vote configuration are unnecessary.</span></span>  
  
     <span data-ttu-id="dc584-146">それ以外の場合は、新たに復元されたクラスター ノードと可用性レプリカ トポロジを評価し、必要に応じて各ノードのクォーラム モードと投票割り当てを変更します。</span><span class="sxs-lookup"><span data-stu-id="dc584-146">Otherwise, you should evaluate the newly recovered cluster node and availability replica topology, and change the quorum mode and vote assignments for each node as appropriate.</span></span> <span data-ttu-id="dc584-147">復元されていないノードについては、オフラインにするか、ノードの投票を 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc584-147">Un-recovered nodes should be set offline or have their node votes set to zero.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="dc584-148">この時点で、クラスター内のノードと SQL Server インスタンスが通常の動作に戻っているように見えることがありますが、</span><span class="sxs-lookup"><span data-stu-id="dc584-148">At this point, the nodes and SQL Server instances in the cluster may appear to be restored back to regular operation.</span></span>  <span data-ttu-id="dc584-149">正常なクォーラムはまだ存在しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc584-149">However, a healthy quorum may still not exist.</span></span>  <span data-ttu-id="dc584-150">フェールオーバー クラスター マネージャー、SQL Server Management Studio の AlwaysOn ダッシュボード、または適切な DMV を使用して、クォーラムが復元されたことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="dc584-150">Using the Failover Cluster Manager, or the AlwaysOn Dashboard within SQL Server Management Studio, or the appropriate DMVs, verify that a quorum has been restored.</span></span>  
  
5.  <span data-ttu-id="dc584-151">**必要に応じて、可用性グループのデータベース レプリカを復旧します。**</span><span class="sxs-lookup"><span data-stu-id="dc584-151">**Recover availability group database replicas as needed.**</span></span> <span data-ttu-id="dc584-152">可用性グループ以外のデータベースは、SQL Server の通常の起動処理の一環として個別に復旧されてオンラインに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc584-152">Non-availability group databases should recover and come back online on their own as part of the regular SQL Server startup process.</span></span>  
  
     <span data-ttu-id="dc584-153">データ損失の可能性や可用性グループ レプリカの復旧時間を最小限に抑えるには、プライマリ レプリカ、同期セカンダリ レプリカ、非同期セカンダリ レプリカの順にオンラインに戻します。</span><span class="sxs-lookup"><span data-stu-id="dc584-153">You can minimize potential data loss and recovery time for the availability group replicas by bringing them back online in this sequence:  primary replica, synchronous secondary replicas, asynchronous secondary replicas.</span></span>  
  
6.  <span data-ttu-id="dc584-154">**障害が発生したコンポーネントを修復するか交換し、クラスターを再検証します。**</span><span class="sxs-lookup"><span data-stu-id="dc584-154">**Repair or replace failed components and re-validate cluster.**</span></span> <span data-ttu-id="dc584-155">最初の災害およびクォーラム障害から復旧したので、障害が発生したノードを修復するか交換し、WSFC と AlwaysOn の関連する構成を適切に調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc584-155">Now that you have recovered from the initial disaster and quorum failure, you should repair or replace the failed nodes and adjust related WSFC and AlwaysOn configurations accordingly.</span></span>  <span data-ttu-id="dc584-156">これには、可用性グループ レプリカの削除、クラスターからのノードの削除、ノードへのソフトウェアの再インストールなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc584-156">This can include dropping availability group replicas, evicting nodes from the cluster, or flattening and re-installing software on a node.</span></span>  
  
     <span data-ttu-id="dc584-157">停止したすべての可用性レプリカを修復または削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc584-157">You must repair or remove all failed availability replicas.</span></span>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="dc584-158">では、可用性レプリカよりもはるかに前の認識されている最後の時点からトランザクション ログが切り捨てられません。</span><span class="sxs-lookup"><span data-stu-id="dc584-158">will not truncate the transaction log past the last known point of the farthest behind availability replica.</span></span>   <span data-ttu-id="dc584-159">可用性グループから停止したレプリカを修復または削除しないと、トランザクション ログが大きくなり、他のレプリカのトランザクション ログの領域が不足する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc584-159">If a failed replica is not repaired or removed from the availability group, the transaction logs will grow and you will run the risk of running out of transaction log space on the other replicas.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc584-160">WSFC クラスターに可用性グループ リスナーが存在するときに、WSFC の構成の検証ウィザードを実行すると、次のような誤った警告メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="dc584-160">If you run the WSFC Validate a Configuration Wizard when an availability group listener exists on the WSFC cluster, the wizard generates the following incorrect warning message:</span></span>  
    >   
    >  <span data-ttu-id="dc584-161">"ネットワーク名 'Name:<network_name>' の RegisterAllProviderIP プロパティは 1 に設定されています。現在のクラスター構成の場合、この値は 0 に設定する必要があります。"</span><span class="sxs-lookup"><span data-stu-id="dc584-161">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="dc584-162">このメッセージは無視してください。</span><span class="sxs-lookup"><span data-stu-id="dc584-162">Please ignore this message.</span></span>  
  
7.  <span data-ttu-id="dc584-163">**必要に応じて手順 4. を繰り返します。**</span><span class="sxs-lookup"><span data-stu-id="dc584-163">**Repeat step 4 as needed.**</span></span> <span data-ttu-id="dc584-164">この目的は、正常な動作に対する適切なレベルのフォールト トレランスと高可用性を再確立することです。</span><span class="sxs-lookup"><span data-stu-id="dc584-164">The goal is to re-establish the appropriate level of fault tolerance and high availability for healthy operations.</span></span>  
  
8.  <span data-ttu-id="dc584-165">**RPO/RTO 分析を実行します。**</span><span class="sxs-lookup"><span data-stu-id="dc584-165">**Conduct RPO/RTO analysis.**</span></span> <span data-ttu-id="dc584-166">SQL Server システム ログ、データベースのタイムスタンプ、および Windows イベント ログを分析して、障害の根本的な原因を特定し、実際の復旧ポイントと復旧時間を文書化します。</span><span class="sxs-lookup"><span data-stu-id="dc584-166">You should analyze SQL Server system logs, database timestamps, and Windows event logs to determine root cause of the failure, and to document actual recovery point and recovery time experiences.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="dc584-167">関連タスク</span><span class="sxs-lookup"><span data-stu-id="dc584-167">Related Tasks</span></span>  
  
-   [<span data-ttu-id="dc584-168">クォーラムを使用せずに WSFC クラスターを強制的に起動する</span><span class="sxs-lookup"><span data-stu-id="dc584-168">Force a WSFC Cluster to Start Without a Quorum</span></span>](force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [<span data-ttu-id="dc584-169">可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dc584-169">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="dc584-170">クラスター クォーラムの NodeWeight 設定を表示</span><span class="sxs-lookup"><span data-stu-id="dc584-170">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="dc584-171">クラスター クォーラムの NodeWeight の設定の構成</span><span class="sxs-lookup"><span data-stu-id="dc584-171">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="dc584-172">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="dc584-172">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md) 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="dc584-173">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="dc584-173">Related Content</span></span>  
  
-   <span data-ttu-id="dc584-174">[フェールオーバー クラスターのイベントおよびログを表示する](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="dc584-174">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="dc584-175">Get-ClusterLog フェールオーバー クラスター コマンドレット</span><span class="sxs-lookup"><span data-stu-id="dc584-175">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="dc584-176">参照</span><span class="sxs-lookup"><span data-stu-id="dc584-176">See Also</span></span>  
 [<span data-ttu-id="dc584-177">Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server</span><span class="sxs-lookup"><span data-stu-id="dc584-177">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
