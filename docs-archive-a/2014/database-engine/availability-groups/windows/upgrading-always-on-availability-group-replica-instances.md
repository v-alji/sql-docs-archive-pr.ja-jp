---
title: ダウンタイムとデータ損失を最小限に抑えた可用性グループサーバーのアップグレードと更新 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: f670af56-dbcc-4309-9119-f919dcad8a65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bac882b93016a430fbcace2d590e6cc087123d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741273"
---
# <a name="upgrade-and-update-of-availability-group-servers-with-minimal-downtime-and-data-loss"></a><span data-ttu-id="ddf12-102">ダウンタイムとデータ損失を最小限に抑えた可用性グループ サーバーのアップグレードおよび更新</span><span class="sxs-lookup"><span data-stu-id="ddf12-102">Upgrade and Update of Availability Group Servers with Minimal Downtime and Data Loss</span></span>
  <span data-ttu-id="ddf12-103">SQL Server 2012 のサーバー インスタンスをサービス パックで更新するとき、または新しいバージョンにアップグレードするときに、順次更新または順次アップグレードを実行することにより、可用性グループのダウンタイムを手動フェールオーバー 1 回分のみに抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="ddf12-103">When updating or upgrading server instances from SQL Server 2012 to a service pack or a newer version, you can reduce downtime for an availability group to only a single manual failover by performing a sequential update or upgrade.</span></span> <span data-ttu-id="ddf12-104">SQL Server のバージョンをアップグレードする場合、この操作をローリング アップグレードと呼びます。現在のバージョンの SQL Server に修正プログラムまたはサービス パックを適用して更新する場合、この操作をローリング アップデートと呼びます。</span><span class="sxs-lookup"><span data-stu-id="ddf12-104">For upgrading SQL Server versions, it is known as rolling upgrade; for updating the current SQL Server version with hotfixes or service packs, it is known as rolling update.</span></span>  
  
 <span data-ttu-id="ddf12-105">ここでは、SQL Server のアップグレードまたは更新についてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="ddf12-105">This topic limits the discussion to SQL Server upgrades/updates only.</span></span> <span data-ttu-id="ddf12-106">高可用性 SQL Server インスタンスが実行されているオペレーティングシステムに関連したアップグレードまたは更新については、「[オペレーティングシステムのアップグレードにおける AlwaysOn 可用性グループのクラスター間での移行](https://msdn.microsoft.com/library/jj873730.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddf12-106">For operating system-related upgrades/updates that the highly-available SQL Server instances are running on, see [Cross-cluster Migration of AlwaysOn Availability Groups for Operating System Upgrades](https://msdn.microsoft.com/library/jj873730.aspx)</span></span>  
  
## <a name="rolling-upgradeupdate-best-practices-for-alwayson-availability-groups"></a><span data-ttu-id="ddf12-107">AlwaysOn 可用性グループのローリング アップグレードおよびローリング アップデートのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="ddf12-107">Rolling Upgrade/Update Best Practices for AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="ddf12-108">サーバーのアップグレードまたは更新の際に可用性グループのダウンタイムとデータ損失を最小限に抑えるには、次のベスト プラクティスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="ddf12-108">The following best practices should be observed when performing server upgrades/updates in order to minimize downtime and data loss for your availability groups:</span></span>  
  
-   <span data-ttu-id="ddf12-109">ローリング アップグレードまたはローリング アップデートを開始する前に、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ddf12-109">Before starting the rolling upgrade/update,</span></span>  
  
    -   <span data-ttu-id="ddf12-110">少なくとも 1 つの同期コミット レプリカで試験的に手動フェールオーバーを実行する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-110">Perform a practice manual failover on at least one of your synchronous-commit replicas</span></span>  
  
    -   <span data-ttu-id="ddf12-111">すべての可用性データベースを対象にデータベースの完全バックアップを実行し、データを保護する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-111">Protect your data by performing a full database backup on every availability database</span></span>  
  
    -   <span data-ttu-id="ddf12-112">すべての可用性データベースに対して DBCC CHECKDB コマンドを実行する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-112">Run DBCC CHECKDB on every availability database</span></span>  
  
-   <span data-ttu-id="ddf12-113">常に、最初はリモートのセカンダリ レプリカ ノード、次にローカルのセカンダリ レプリカ ノード、最後にプライマリ レプリカ ノードという順序でアップグレードまたは更新してください。</span><span class="sxs-lookup"><span data-stu-id="ddf12-113">Always upgrade/update the remote secondary replica nodes first, then local secondary replica nodes next, and the primary replica node last.</span></span>  
  
-   <span data-ttu-id="ddf12-114">アップグレード中のデータベースでバックアップを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="ddf12-114">Backups cannot occur on a database that is in the process of being upgraded.</span></span>  <span data-ttu-id="ddf12-115">セカンダリ レプリカをアップグレードする前に、プライマリ レプリカでのみバックアップを実行するように自動バックアップ設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="ddf12-115">Prior to upgrading the secondary replicas, configure the automated backup preference to run backups only on the primary replica.</span></span>  <span data-ttu-id="ddf12-116">プライマリ レプリカをアップグレードする前に、この設定を変更してセカンダリ レプリカでのみバックアップを実行するようにします。</span><span class="sxs-lookup"><span data-stu-id="ddf12-116">Prior to upgrading the primary replica, modify this setting to run backups only on the secondary replicas.</span></span>  
  
-   <span data-ttu-id="ddf12-117">アップグレード プロセスまたは更新プロセスの間に可用性グループが誤ってフェールオーバーされることを防ぐために、作業開始前にすべての同期コミット レプリカから可用性フェールオーバーを削除してください。</span><span class="sxs-lookup"><span data-stu-id="ddf12-117">To prevent the availability group from unintended failovers during the upgrade/update process, remove availability failover from all synchronous-commit replicas before you begin.</span></span>  
  
-   <span data-ttu-id="ddf12-118">最初にセカンダリ レプリカを使用して可用性グループをアップグレード済みノードにフェールオーバーした後で、プライマリ レプリカ ノードをアップグレードするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ddf12-118">Do not upgrade the primary replica node before failing over the availability group to an upgraded node with a secondary replica first.</span></span> <span data-ttu-id="ddf12-119">このベスト プラクティスに従わなかった場合、プライマリ レプリカでのアップグレードまたは更新の際にクライアント アプリケーションで長時間のダウンタイムが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-119">Otherwise, client applications may suffer extended downtime during the upgrade/update on the primary replica.</span></span>  
  
-   <span data-ttu-id="ddf12-120">可用性グループは常に同期コミット セカンダリ レプリカ ノードにフェールオーバーしてください。</span><span class="sxs-lookup"><span data-stu-id="ddf12-120">Always fail over the availability group to a synchronous-commit secondary replica node.</span></span> <span data-ttu-id="ddf12-121">非同期コミット セカンダリ レプリカにフェールオーバーした場合、データベースでデータ損失が発生し、データ移動が自動的に中断されます。データ移動を再開するには、手動で操作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-121">If you fail over to an asynchronous-commit secondary replica, the databases will suffer data loss, and data movement is automatically suspended until you manually resume data movement.</span></span>  
  
-   <span data-ttu-id="ddf12-122">他のセカンダリ レプリカ ノードをアップグレードまたは更新する前に、プライマリ レプリカ ノードをアップグレードまたは更新しないでください。</span><span class="sxs-lookup"><span data-stu-id="ddf12-122">Do not upgrade/update the primary replica node before upgrading/updating any other secondary replica nodes.</span></span> <span data-ttu-id="ddf12-123">アップグレードされたプライマリ レプリカから、同じバージョンにまだアップグレードされていないセカンダリ レプリカにログを送信できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-123">An upgraded primary replica can no longer ship logs to any secondary replica that has not yet been upgraded to the same version.</span></span> <span data-ttu-id="ddf12-124">セカンダリ レプリカへのデータ移動が中断されているときには、そのレプリカに対する自動フェールオーバーは実行されず、可用性データベースでデータ損失が発生する危険性が高まります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-124">When data movement to a secondary replica is suspended, no automatic failover can occur for that replica, and your availability databases are vulnerable to data loss.</span></span>  
  
-   <span data-ttu-id="ddf12-125">可用性グループをフェールオーバーする前に、フェールオーバー ターゲットの同期状態が SYNCHRONIZED であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ddf12-125">Before failing over an availability group, verify that the synchronization state of the failover target is SYNCHRONIZED.</span></span>  
  
## <a name="rolling-upgradeupdate-process"></a><span data-ttu-id="ddf12-126">ローリング アップグレードおよびローリング アップデートのプロセス</span><span class="sxs-lookup"><span data-stu-id="ddf12-126">Rolling Upgrade/Update Process</span></span>  
 <span data-ttu-id="ddf12-127">実際のプロセスは、可用性グループの配置トポロジや各レプリカのコミット モードなどの要因によって変わります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-127">In practice, the exact process will depend on factors such as the deployment topology of your availability groups and the commit mode of each replica.</span></span> <span data-ttu-id="ddf12-128">ただし、最も単純なシナリオにおけるローリング アップグレードおよびローリング アップデートは、次の手順で構成される単純な複数段階のプロセスになります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-128">But in the simplest scenario, a rolling upgrade/update is a multi-stage process that in its simplest form involves the following steps:</span></span>  
  
 <span data-ttu-id="ddf12-129">![HADR シナリオの可用性グループのアップグレード](../../media/alwaysonupgrade-ag-hadr.gif "HADR シナリオの可用性グループのアップグレード")</span><span class="sxs-lookup"><span data-stu-id="ddf12-129">![Availability Group Upgrade in HADR Scenario](../../media/alwaysonupgrade-ag-hadr.gif "Availability Group Upgrade in HADR Scenario")</span></span>  
  
1.  <span data-ttu-id="ddf12-130">すべての同期コミット レプリカの自動フェールオーバーを削除する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-130">Remove automatic failover on all synchronous-commit replicas</span></span>  
  
2.  <span data-ttu-id="ddf12-131">非同期コミット セカンダリ レプリカを実行しているリモート サーバー インスタンスをすべてアップグレードまたは更新する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-131">Upgrade/update all remote server instances running asynchronous-commit secondary replicas</span></span>  
  
3.  <span data-ttu-id="ddf12-132">プライマリ レプリカを現在実行していないローカル サーバー インスタンスをすべてアップグレードまたは更新する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-132">Upgrade/update the all local server instances that are not currently running the primary replica</span></span>  
  
4.  <span data-ttu-id="ddf12-133">可用性グループを手動で同期コミット セカンダリ レプリカにフェールオーバーする。</span><span class="sxs-lookup"><span data-stu-id="ddf12-133">Manually fail over the availability group to a synchronous-commit secondary replica</span></span>  
  
5.  <span data-ttu-id="ddf12-134">それまでプライマリ レプリカをホストしていたサーバー インスタンスをアップグレードまたは更新する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-134">Upgrade/update the server instance that formerly hosted the primary replica</span></span>  
  
6.  <span data-ttu-id="ddf12-135">必要に応じて自動フェールオーバー パートナーを構成する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-135">Configure automatic failover partners as desired</span></span>  
  
 <span data-ttu-id="ddf12-136">必要であれば、さらに手動でフェールオーバーを実行して、可用性グループを元の構成に戻すこともできます。</span><span class="sxs-lookup"><span data-stu-id="ddf12-136">If necessary, you can perform an extra manual failover to return the availability group to its original configuration.</span></span>  
  
## <a name="availability-group-with-one-remote-secondary-replica"></a><span data-ttu-id="ddf12-137">1 つのリモート セカンダリ レプリカを含む可用性グループ</span><span class="sxs-lookup"><span data-stu-id="ddf12-137">Availability Group with One Remote Secondary Replica</span></span>  
 <span data-ttu-id="ddf12-138">災害復旧のみを目的として可用性グループを配置していた場合、可用性グループを非同期コミット セカンダリ レプリカにフェールオーバーする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-138">If you have deployed an availability group only for disaster recovery, you may need to fail over the availability group to an asynchronous-commit secondary replica.</span></span> <span data-ttu-id="ddf12-139">次の図に、そのような構成の例を示します。</span><span class="sxs-lookup"><span data-stu-id="ddf12-139">Such configuration is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="ddf12-140">![DR シナリオの可用性グループのアップグレード](../../media/agupgrade-ag-dr.gif "DR シナリオの可用性グループのアップグレード")</span><span class="sxs-lookup"><span data-stu-id="ddf12-140">![Availability Group Upgrade in DR Scenario](../../media/agupgrade-ag-dr.gif "Availability Group Upgrade in DR Scenario")</span></span>  
  
 <span data-ttu-id="ddf12-141">この場合には、ローリング アップグレードまたはローリング アップデートの際に可用性グループを非同期コミット セカンダリ レプリカにフェールオーバーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-141">In this situation, you must fail over the availability group to the asynchronous-commit secondary replica during the rolling upgrade/update.</span></span> <span data-ttu-id="ddf12-142">データ損失を防ぐために、コミット モードを同期コミットに変更し、セカンダリ レプリカが同期されるまで待ってから、可用性グループをフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="ddf12-142">To prevent data loss, change the commit mode to synchronous commit and wait for the secondary replica to be synchronized before you fail over the availability group.</span></span> <span data-ttu-id="ddf12-143">そのため、ローリング アップグレードまたはローリング アップデートのプロセスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-143">Therefore, the rolling upgrade/update process may look as follows:</span></span>  
  
1.  <span data-ttu-id="ddf12-144">リモート サーバーをアップグレードまたは更新する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-144">Upgrade/update the remote server</span></span>  
  
2.  <span data-ttu-id="ddf12-145">コミット モードを同期コミットに変更する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-145">Change the commit mode to synchronous commit</span></span>  
  
3.  <span data-ttu-id="ddf12-146">同期状態が SYNCHRONIZED になるまで待機する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-146">Wait until synchronization state is SYNCHRONIZED</span></span>  
  
4.  <span data-ttu-id="ddf12-147">可用性グループをリモート サイトにフェールオーバーする。</span><span class="sxs-lookup"><span data-stu-id="ddf12-147">Fail over the availability group to the remote site</span></span>  
  
5.  <span data-ttu-id="ddf12-148">ローカル (プライマリ サイト) サーバーをアップグレードまたは更新する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-148">Upgrade/update the local (primary site) server</span></span>  
  
6.  <span data-ttu-id="ddf12-149">可用性グループをプライマリ サイトにフェールオーバーする。</span><span class="sxs-lookup"><span data-stu-id="ddf12-149">Fail over the availability group to the primary site</span></span>  
  
7.  <span data-ttu-id="ddf12-150">コミット モードを非同期コミットに変更する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-150">Change the commit mode to asynchronous commit</span></span>  
  
 <span data-ttu-id="ddf12-151">同期コミット モードはリモート サイトとのデータ同期には推奨されない設定であるため、設定の変更後、クライアント アプリケーションでデータベース待機時間が急増する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-151">Since the synchronous-commit mode is not a recommended setting for data synchronization to a remote site, client applications may notice an immediate increase in database latency after the setting change.</span></span> <span data-ttu-id="ddf12-152">さらに、フェールオーバーを実行すると未確認のログ メッセージがすべて破棄されます。</span><span class="sxs-lookup"><span data-stu-id="ddf12-152">Moreover, performing a failover will cause all unacknowledged log messages to be discarded.</span></span> <span data-ttu-id="ddf12-153">2 つのサイト間のネットワーク待機時間が長い場合、破棄されるログ メッセージの数が膨大になり、クライアントで大量のトランザクション エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-153">The amount of discarded log messages can be quite large due to the high network latency between the two sites, causing clients to experience a high volume of transactional failure.</span></span> <span data-ttu-id="ddf12-154">クライアント アプリケーションへの影響を最小限に抑えるには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ddf12-154">You can minimize impact to client applications by doing the following:</span></span>  
  
-   <span data-ttu-id="ddf12-155">クライアント トラフィックが少ない時間帯にメンテナンス予定を設定する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-155">Carefully select a maintenance window during low client traffic</span></span>  
  
-   <span data-ttu-id="ddf12-156">プライマリ サイトの SQL Server をアップグレードまたは更新する際に可用性モードを非同期コミットに戻し、プライマリ サイトへの再フェールオーバーの準備が完了したときに、同期コミットに戻す。</span><span class="sxs-lookup"><span data-stu-id="ddf12-156">While upgrading/updating SQL Server on the primary site, change the availability mode back to asynchronous commit, then revert to synchronous commit when you are ready to fail over to the primary site again</span></span>  
  
## <a name="availability-group-with-failover-cluster-instance-nodes"></a><span data-ttu-id="ddf12-157">フェールオーバー クラスター インスタンス ノードを含む可用性グループ</span><span class="sxs-lookup"><span data-stu-id="ddf12-157">Availability Group with Failover Cluster Instance Nodes</span></span>  
 <span data-ttu-id="ddf12-158">可用性グループにフェールオーバー クラスター インスタンス (FCI) ノードが含まれている場合、非アクティブなノードをアップグレードまたは更新した後で、アクティブなノードをアップグレードまたは更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-158">If an availability group contains failover cluster instance (FCI) nodes, you should upgrade/update the inactive nodes before you upgrade/update the active nodes.</span></span> <span data-ttu-id="ddf12-159">次の図では、ローカルでの可用性を高めるために FCI を使用し、リモートのディザスター リカバリーのために FCI 間の非同期コミットを使用する、一般的な可用性グループのシナリオを示します。さらに、アップグレード手順も示しています。</span><span class="sxs-lookup"><span data-stu-id="ddf12-159">The figure below illustrates a common availability group scenario with FCIs for local high availability and asynchronous commit between the FCIs for remote disaster recovery, and the upgrade sequence.</span></span>  
  
 <span data-ttu-id="ddf12-160">![FCI による可用性グループのアップグレード:](../../media/agupgrade-ag-fci-dr.gif "FCI による可用性グループのアップグレード:")</span><span class="sxs-lookup"><span data-stu-id="ddf12-160">![Availability Group Upgrade with FCIs](../../media/agupgrade-ag-fci-dr.gif "Availability Group Upgrade with FCIs")</span></span>  
  
1.  <span data-ttu-id="ddf12-161">REMOTE2 のアップグレード/更新</span><span class="sxs-lookup"><span data-stu-id="ddf12-161">Upgrade/update REMOTE2</span></span>  
  
2.  <span data-ttu-id="ddf12-162">FCI2 を REMOTE2 にフェールオーバーする。</span><span class="sxs-lookup"><span data-stu-id="ddf12-162">Fail over FCI2 to REMOTE2</span></span>  
  
3.  <span data-ttu-id="ddf12-163">REMOTE1 のアップグレード/更新</span><span class="sxs-lookup"><span data-stu-id="ddf12-163">Upgrade/update REMOTE1</span></span>  
  
4.  <span data-ttu-id="ddf12-164">PRIMARY2 のアップグレード/更新</span><span class="sxs-lookup"><span data-stu-id="ddf12-164">Upgrade/update PRIMARY2</span></span>  
  
5.  <span data-ttu-id="ddf12-165">FCI1 を PRIMARY2 にフェールオーバーする。</span><span class="sxs-lookup"><span data-stu-id="ddf12-165">Fail over FCI1 to PRIMARY2</span></span>  
  
6.  <span data-ttu-id="ddf12-166">PRIMARY1 のアップグレード/更新</span><span class="sxs-lookup"><span data-stu-id="ddf12-166">Upgrade/update PRIMARY1</span></span>  
  
## <a name="upgradeupdate-sql-server-instances-with-multiple-availability-groups"></a><span data-ttu-id="ddf12-167">複数の可用性グループを含む SQL Server インスタンスのアップグレードまたは更新</span><span class="sxs-lookup"><span data-stu-id="ddf12-167">Upgrade/Update SQL Server Instances with Multiple Availability Groups</span></span>  
 <span data-ttu-id="ddf12-168">プライマリ レプリカが別々のサーバー ノードに存在する (アクティブ/アクティブ構成) 可用性グループが複数実行されている場合、アップグレードまたは更新の際には高可用性を維持するためのフェールオーバー手順を追加で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-168">If you are running multiple availability groups with primary replicas on separate server nodes (an Active/Active configuration), the upgrade/update path involves more failover steps to preserve high availability in the process.</span></span> <span data-ttu-id="ddf12-169">次の表に示すように、3 つのサーバー ノードで 3 つの可用性グループが実行され、すべてのセカンダリ レプリカが同期コミット モードで実行されているとします。</span><span class="sxs-lookup"><span data-stu-id="ddf12-169">Suppose you are running three availability groups on three server nodes as shown in the following table, and all secondary replicas are running in synchronous-commit mode.</span></span>  
  
|<span data-ttu-id="ddf12-170">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="ddf12-170">Availability Group</span></span>|<span data-ttu-id="ddf12-171">Node1</span><span class="sxs-lookup"><span data-stu-id="ddf12-171">Node1</span></span>|<span data-ttu-id="ddf12-172">Node2</span><span class="sxs-lookup"><span data-stu-id="ddf12-172">Node2</span></span>|<span data-ttu-id="ddf12-173">Node3</span><span class="sxs-lookup"><span data-stu-id="ddf12-173">Node3</span></span>|  
|------------------------|-----------|-----------|-----------|  
|<span data-ttu-id="ddf12-174">AG1</span><span class="sxs-lookup"><span data-stu-id="ddf12-174">AG1</span></span>|<span data-ttu-id="ddf12-175">プライマリ</span><span class="sxs-lookup"><span data-stu-id="ddf12-175">Primary</span></span>|||  
|<span data-ttu-id="ddf12-176">AG2</span><span class="sxs-lookup"><span data-stu-id="ddf12-176">AG2</span></span>||<span data-ttu-id="ddf12-177">プライマリ</span><span class="sxs-lookup"><span data-stu-id="ddf12-177">Primary</span></span>||  
|<span data-ttu-id="ddf12-178">AG3</span><span class="sxs-lookup"><span data-stu-id="ddf12-178">AG3</span></span>|||<span data-ttu-id="ddf12-179">プライマリ</span><span class="sxs-lookup"><span data-stu-id="ddf12-179">Primary</span></span>|  
  
 <span data-ttu-id="ddf12-180">この状況では、次の順序で負荷分散ローリング アップグレードまたはローリング アップデートを実行することが適切であると考えられます。</span><span class="sxs-lookup"><span data-stu-id="ddf12-180">It may be appropriate in your situation to perform a load-balanced rolling upgrade/update in the following sequence:</span></span>  
  
1.  <span data-ttu-id="ddf12-181">AG2 を Node3 にフェールオーバーする (Node2 を解放)。</span><span class="sxs-lookup"><span data-stu-id="ddf12-181">Fail over AG2 to Node3 (to free up Node2)</span></span>  
  
2.  <span data-ttu-id="ddf12-182">Node2 をアップグレードまたは更新する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-182">Upgrade/update Node2</span></span>  
  
3.  <span data-ttu-id="ddf12-183">AG1 を Node2 にフェールオーバーする (Node1 を解放)。</span><span class="sxs-lookup"><span data-stu-id="ddf12-183">Fail over AG1 to Node2 (to free up Node1)</span></span>  
  
4.  <span data-ttu-id="ddf12-184">Node1 をアップグレードまたは更新する。</span><span class="sxs-lookup"><span data-stu-id="ddf12-184">Upgrade/update Node1</span></span>  
  
5.  <span data-ttu-id="ddf12-185">AG2 および AG3 を Node1 にフェールオーバーする (Node3 を解放)。</span><span class="sxs-lookup"><span data-stu-id="ddf12-185">Fail over both AG2 and AG3 to Node1 (to free up Node3)</span></span>  
  
6.  <span data-ttu-id="ddf12-186">Node3 のアップグレード/更新</span><span class="sxs-lookup"><span data-stu-id="ddf12-186">Upgrade/update Node3</span></span>  
  
7.  <span data-ttu-id="ddf12-187">AG3 を Node3 にフェールオーバーする。</span><span class="sxs-lookup"><span data-stu-id="ddf12-187">Fail over AG3 to Node3</span></span>  
  
 <span data-ttu-id="ddf12-188">この順序でアップグレードまたは更新を実行した場合、1 つの可用性グループに対して 2 回のフェールオーバーを実行するよりも平均ダウンタイムが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-188">This upgrade/update sequence has an average downtime of less than two failovers per availability group.</span></span> <span data-ttu-id="ddf12-189">実行後の構成は、次の表のようになります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-189">The resulting configuration is shown in the table below.</span></span>  
  
|<span data-ttu-id="ddf12-190">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="ddf12-190">Availability Group</span></span>|<span data-ttu-id="ddf12-191">Node1</span><span class="sxs-lookup"><span data-stu-id="ddf12-191">Node1</span></span>|<span data-ttu-id="ddf12-192">Node2</span><span class="sxs-lookup"><span data-stu-id="ddf12-192">Node2</span></span>|<span data-ttu-id="ddf12-193">Node3</span><span class="sxs-lookup"><span data-stu-id="ddf12-193">Node3</span></span>|  
|------------------------|-----------|-----------|-----------|  
|<span data-ttu-id="ddf12-194">AG1</span><span class="sxs-lookup"><span data-stu-id="ddf12-194">AG1</span></span>||<span data-ttu-id="ddf12-195">プライマリ</span><span class="sxs-lookup"><span data-stu-id="ddf12-195">Primary</span></span>||  
|<span data-ttu-id="ddf12-196">AG2</span><span class="sxs-lookup"><span data-stu-id="ddf12-196">AG2</span></span>|<span data-ttu-id="ddf12-197">プライマリ</span><span class="sxs-lookup"><span data-stu-id="ddf12-197">Primary</span></span>|||  
|<span data-ttu-id="ddf12-198">AG3</span><span class="sxs-lookup"><span data-stu-id="ddf12-198">AG3</span></span>|||<span data-ttu-id="ddf12-199">プライマリ</span><span class="sxs-lookup"><span data-stu-id="ddf12-199">Primary</span></span>|  
  
 <span data-ttu-id="ddf12-200">実際の実装方法に応じて、アップグレードまたは更新の手順が変わる可能性があります。また、クライアント アプリケーションで発生するダウンタイムも変わります。</span><span class="sxs-lookup"><span data-stu-id="ddf12-200">Based on your specific implementation, your upgrade/update path may vary, and the downtime that client applications experience may vary as well.</span></span>  
  
  
