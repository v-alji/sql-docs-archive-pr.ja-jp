---
title: WSFC クォーラム モードと投票の構成 (SQL Server) | Microsoft Docs
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
ms.assetid: ca0d59ef-25f0-4047-9130-e2282d058283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b1d5ad992c59f252f485f2d65451a72f150bef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640513"
---
# <a name="wsfc-quorum-modes-and-voting-configuration-sql-server"></a><span data-ttu-id="aac9b-102">WSFC クォーラム モードと投票の構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="aac9b-102">WSFC Quorum Modes and Voting Configuration (SQL Server)</span></span>
  <span data-ttu-id="aac9b-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] と AlwaysOn フェールオーバー クラスター インスタンス (FCI) のどちらも、Windows Server フェールオーバー クラスタリング (WSFC) をプラットフォーム テクノロジとして使用します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-103">Both [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and AlwaysOn Failover Cluster Instances (FCI) take advantage of Windows Server Failover Clustering (WSFC) as a platform technology.</span></span>  <span data-ttu-id="aac9b-104">WSFC は、クォーラム ベースのアプローチを使用してクラスターの全体的な正常性を監視し、ノード レベルのフォールト トレランスを最大限に高めます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-104">WSFC uses a quorum-based approach to monitoring overall cluster health and maximize node-level fault tolerance.</span></span> <span data-ttu-id="aac9b-105">WSFC クォーラム モードおよびノード投票構成の基本について理解することは、AlwaysOn 高可用性およびディザスター リカバリー ソリューションの設計、運用、トラブルシューティングのために非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="aac9b-105">A fundamental understanding of WSFC quorum modes and node voting configuration is very important to designing, operating, and troubleshooting your AlwaysOn high availability and disaster recovery solution.</span></span>  
  
 <span data-ttu-id="aac9b-106">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="aac9b-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="aac9b-107">クォーラムによるクラスター状態検出</span><span class="sxs-lookup"><span data-stu-id="aac9b-107">Cluster Health Detection by Quorum</span></span>](#ClusterHealthDetectionbyQuorum)  
  
-   [<span data-ttu-id="aac9b-108">クォーラムモード</span><span class="sxs-lookup"><span data-stu-id="aac9b-108">Quorum Modes</span></span>](#QuorumModes)  
  
-   [<span data-ttu-id="aac9b-109">投票と非投票ノード</span><span class="sxs-lookup"><span data-stu-id="aac9b-109">Voting and Non-Voting Nodes</span></span>](#VotingandNonVotingNodes)  
  
-   [<span data-ttu-id="aac9b-110">クォーラム投票に推奨される調整</span><span class="sxs-lookup"><span data-stu-id="aac9b-110">Recommended Adjustments to Quorum Voting</span></span>](#RecommendedAdjustmentstoQuorumVoting)  
  
-   [<span data-ttu-id="aac9b-111">関連タスク</span><span class="sxs-lookup"><span data-stu-id="aac9b-111">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="aac9b-112">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="aac9b-112">Related Content</span></span>](#RelatedContent)  
  
##  <a name="cluster-health-detection-by-quorum"></a><a name="ClusterHealthDetectionbyQuorum"></a><span data-ttu-id="aac9b-113">クォーラムによるクラスターの正常性の検出</span><span class="sxs-lookup"><span data-stu-id="aac9b-113">Cluster Health Detection by Quorum</span></span>  
 <span data-ttu-id="aac9b-114">WSFC クラスター内の各ノードは、定期的なハートビート通信に参加し、ノードの正常性状態を他のノードと共有します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-114">Each node in a WSFC cluster participates in periodic heartbeat communication to share the node's health status with the other nodes.</span></span> <span data-ttu-id="aac9b-115">応答しないノードは、エラー状態であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-115">Unresponsive nodes are considered to be in a failed state.</span></span>  
  
 <span data-ttu-id="aac9b-116">*クォーラム* ノード セットは、WSFC クラスター内の大多数の投票ノードおよび監視サーバーです。</span><span class="sxs-lookup"><span data-stu-id="aac9b-116">A *quorum* node set is a majority of the voting nodes and witnesses in the WSFC cluster.</span></span> <span data-ttu-id="aac9b-117">WSFC クラスターの全体的な正常性と状態は、定期的な *クォーラムの投票*によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-117">The overall health and status of a WSFC cluster is determined by a periodic *quorum vote*.</span></span>  <span data-ttu-id="aac9b-118">クォーラムの存在は、クラスターが正常であり、ノード レベルのフォールト トレランスを提供できることを表します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-118">The presence of a quorum means that the cluster is healthy and able to provide node-level fault tolerance.</span></span>  
  
 <span data-ttu-id="aac9b-119">クォーラムがない状態は、クラスターが正常でないことを示します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-119">The absence of a quorum indicates that the cluster is not healthy.</span></span>  <span data-ttu-id="aac9b-120">プライマリ ノードのフェールオーバー先として正常なセカンダリ ノードを使用できるようにするために、WSFC クラスターの全体的な正常性が維持される必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-120">Overall WSFC cluster health must be maintained in order to ensure that healthy secondary nodes are available for primary nodes to fail over to.</span></span>  <span data-ttu-id="aac9b-121">クォーラム投票に失敗した場合、WSFC クラスターは、予防策としてオフラインに設定されます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-121">If the quorum vote fails, the WSFC cluster will be set offline as a precautionary measure.</span></span>  <span data-ttu-id="aac9b-122">これによって、クラスターに登録されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスがすべて停止します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-122">This will also cause all [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instances registered with the cluster to be stopped.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aac9b-123">クォーラム障害のために WSFC クラスターがオフラインに設定されると、オンラインに戻すために手動介入が必要です。</span><span class="sxs-lookup"><span data-stu-id="aac9b-123">If a WSFC cluster is set offline because of quorum failure, manual intervention is required to bring it back online.</span></span>  
>   
>  <span data-ttu-id="aac9b-124">詳細については、「 [WSFC の強制クォーラムによる災害復旧 &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md)によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-124">For more information, see: [WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md).</span></span>  
  
##  <a name="quorum-modes"></a><a name="QuorumModes"></a><span data-ttu-id="aac9b-125">クォーラムモード</span><span class="sxs-lookup"><span data-stu-id="aac9b-125">Quorum Modes</span></span>  
 <span data-ttu-id="aac9b-126">*クォーラム モード* は、WSFC クラスター レベルで構成され、クォーラム投票の方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-126">A *quorum mode* is configured at the WSFC cluster level that dictates the methodology used for quorum voting.</span></span>  <span data-ttu-id="aac9b-127">フェールオーバー クラスター マネージャー ユーティリティは、クラスター内のノード数に基づいて、クォーラム モードを推奨します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-127">The Failover Cluster Manager utility will recommend a quorum mode based on the number of nodes in the cluster.</span></span>  
  
 <span data-ttu-id="aac9b-128">投票クォーラムの構成を決定するために、次のクォーラム モードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-128">The following quorum modes can be used to determine what constitutes a quorum of votes:</span></span>  
  
-   <span data-ttu-id="aac9b-129">**ノードマジョリティ。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-129">**Node Majority.**</span></span> <span data-ttu-id="aac9b-130">クラスターが正常であるためには、クラスター内の半分以上の投票ノードが肯定的に投票する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-130">More than one-half of the voting nodes in the cluster must vote affirmatively for the cluster to be healthy.</span></span>  
  
-   <span data-ttu-id="aac9b-131">**ノードおよびファイル共有マジョリティ。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-131">**Node and File Share Majority.**</span></span> <span data-ttu-id="aac9b-132">ノード マジョリティ クォーラム モードに似ていますが、リモート ファイル共有も投票監視として構成され、その共有に対する各ノードからの接続も肯定的な投票としてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-132">Similar to Node Majority quorum mode, except that a remote file share is also configured as a voting witness, and connectivity from any node to that share is also counted as an affirmative vote.</span></span>  <span data-ttu-id="aac9b-133">クラスターが正常であるためには、使用可能な投票の半分以上が肯定的である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-133">More than one-half of the possible votes must be affirmative for the cluster to be healthy.</span></span>  
  
     <span data-ttu-id="aac9b-134">推奨事項として、監視ファイル共有はクラスター内のノードに存在せず、クラスター内のすべてのノードから見える必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-134">As a best practice, the witness file share should not reside on any node in the cluster, and it should be visible to all nodes in the cluster.</span></span>  
  
-   <span data-ttu-id="aac9b-135">**ノードおよびディスクマジョリティ。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-135">**Node and Disk Majority.**</span></span> <span data-ttu-id="aac9b-136">ノード マジョリティ クォーラム モードに似ていますが、共有ディスク クラスター リソースも投票監視として使用され、その共有ディスクに対する各ノードからの接続も肯定的な投票としてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-136">Similar to Node Majority quorum mode, except that a shared disk cluster resource is also designated as a voting witness, and connectivity from any node to that shared disk is also counted as an affirmative vote.</span></span>  <span data-ttu-id="aac9b-137">クラスターが正常であるためには、使用可能な投票の半分以上が肯定的である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-137">More than one-half of the possible votes must be affirmative for the cluster to be healthy.</span></span>  
  
-   <span data-ttu-id="aac9b-138">**ディスクのみ。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-138">**Disk Only.**</span></span> <span data-ttu-id="aac9b-139">共有ディスク クラスター リソースが監視として使用され、その共有ディスクに対する各ノードからの接続も肯定的な投票としてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-139">A shared disk cluster resource is designated as a witness, and connectivity by any node to that shared disk is counted as an affirmative vote.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="aac9b-140">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の非対称的なストレージ構成を使用する際には、通常、投票ノード数が奇数の場合はノード マジョリティ クォーラム モード、投票ノード数が偶数の場合はノードおよびファイル共有マジョリティ クォーラム モードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="aac9b-140">When using an asymmetric storage configuration for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], you should generally use the Node Majority quorum mode when you have an odd number of voting nodes, or the Node and File Share Majority quorum mode when you have an even number of voting nodes.</span></span>  
  
##  <a name="voting-and-non-voting-nodes"></a><a name="VotingandNonVotingNodes"></a><span data-ttu-id="aac9b-141">投票と非投票ノード</span><span class="sxs-lookup"><span data-stu-id="aac9b-141">Voting and Non-Voting Nodes</span></span>  
 <span data-ttu-id="aac9b-142">既定では、WSFC クラスター内の各ノードがクラスター クォーラムのメンバーとして含まれます。各ノードはクラスターの全体的な正常性の決定において 1 つの投票を持ちます。また、各ノードはクォーラムの構築を試行し続けます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-142">By default, each node in the WSFC cluster is included as a member of the cluster quorum; each node has a single vote in determining the overall cluster health, and each node will continuously attempt to establish a quorum.</span></span>  <span data-ttu-id="aac9b-143">クォーラムに関するここまでの説明では、クラスター状態について投票する WSFC クラスター ノードのセットを *投票ノード*として注意深く限定してきました。</span><span class="sxs-lookup"><span data-stu-id="aac9b-143">The quorum discussion to this point has carefully qualified the set of WSFC cluster nodes that vote on cluster health as *voting nodes*.</span></span>  
  
 <span data-ttu-id="aac9b-144">WSFC クラスター内のノードは、クラスターが全体として正常であるまたは正常でないと明確に決定することはできません。</span><span class="sxs-lookup"><span data-stu-id="aac9b-144">No individual node in a WSFC cluster can definitively determine that the cluster as a whole is healthy or unhealthy.</span></span>  <span data-ttu-id="aac9b-145">特定の時点で、各ノードからは、他のノードの一部はオフラインに見えるか、フェールオーバー中であるか、またはネットワーク通信のエラーにより応答不能に見えます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-145">At any given moment, from the perspective of each node, some of the other nodes may appear to be offline, or appear to be in the process of failover, or appear unresponsive due to a network communication failure.</span></span>  <span data-ttu-id="aac9b-146">クォーラム投票の主な機能は、WSFC クラスターの各ノードの外観の状態が、本当にそれらのノードの実際の状態であるかどうかを判断することです。</span><span class="sxs-lookup"><span data-stu-id="aac9b-146">A key function of the quorum vote is to determine whether the apparent state of each of node in the WSFC cluster is indeed that actual state of those nodes.</span></span>  
  
 <span data-ttu-id="aac9b-147">"ディスクのみ" 以外のすべてのクォーラム モデルでは、クォーラム投票の有効性は、クラスター内のすべての投票ノード間の信頼できる通信によります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-147">For all of the quorum models except 'Disk Only', the effectiveness of a quorum vote depends on reliable communications between all of the voting nodes in the cluster.</span></span> <span data-ttu-id="aac9b-148">同じ物理サブネット上のノード間のネットワーク通信は信頼性が高いと見なす必要があります。クォーラム投票は、信頼される必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-148">Network communications between nodes on the same physical subnet should be considered reliable; the quorum vote should be trusted.</span></span>  
  
 <span data-ttu-id="aac9b-149">しかし、クォーラム投票で他のサブネット上のノードが応答しないように見えるが実際はオンラインで正常である場合、サブネット間のネットワーク通信のエラーが原因であることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-149">However, if a node on another subnet is seen as non-responsive in a quorum vote, but it is actually online and otherwise healthy, that is most likely due to a network communications failure between subnets.</span></span>  <span data-ttu-id="aac9b-150">クラスター トポロジ、クォーラム モード、およびフェールオーバー ポリシー構成によっては、ネットワーク通信エラーによって投票ノードのセット (またはサブセット) が実質的に複数作成されてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-150">Depending upon the cluster topology, quorum mode, and failover policy configuration, that network communications failure may effectively create more than one set (or subset) of voting nodes.</span></span>  
  
 <span data-ttu-id="aac9b-151">投票ノードの複数のサブセットが自身でクォーラムを構築できる場合、それは *スプリット ブレイン シナリオ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-151">When more than one subset of voting nodes is able to establish a quorum on its own, that is known as a *split-brain scenario*.</span></span>  <span data-ttu-id="aac9b-152">このようなシナリオでは、各クォーラム上のノードが別々の動作をし、相互に競合します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-152">In such a scenario, the nodes in the separate quorums may behave differently, and in conflict with one another.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aac9b-153">スプリット ブレイン シナリオは、システム管理者が強制クォーラム動作を手動で実行、または非常にまれですが強制フェールオーバーを実行することで、クォーラム ノード セットが明示的に細分化された場合にのみ発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-153">The split-brain scenario is only possible when a system administrator manually performs a forced quorum operation, or in very rare circumstances, a forced failover; explicitly subdividing the quorum node set.</span></span>  
  
 <span data-ttu-id="aac9b-154">クォーラム構成を単純化してアップタイムを向上させるために、ノードの投票がクォーラムに対してカウントされないように、各ノードの*Nodeweight*設定を調整することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="aac9b-154">In order to simplify your quorum configuration and increase up-time, you may want to adjust each node's *NodeWeight* setting so that the node's vote is not counted towards the quorum.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aac9b-155">NodeWeight 設定を使用するには、次の修正プログラムが WSFC クラスターのすべてのサーバーに適用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-155">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="aac9b-156">[KB2494036](https://support.microsoft.com/kb/2494036): とでクォーラム投票のないクラスターノードを構成するための修正プログラムが用意されています。 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)][!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aac9b-156">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
##  <a name="recommended-adjustments-to-quorum-voting"></a><a name="RecommendedAdjustmentstoQuorumVoting"></a><span data-ttu-id="aac9b-157">クォーラム投票に推奨される調整</span><span class="sxs-lookup"><span data-stu-id="aac9b-157">Recommended Adjustments to Quorum Voting</span></span>  
 <span data-ttu-id="aac9b-158">特定の WSFC ノードの投票を有効または無効にする場合は、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="aac9b-158">When enabling or disabling a given WSFC node's vote, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="aac9b-159">**既定では、投票は行いません。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-159">**No vote by default.**</span></span> <span data-ttu-id="aac9b-160">各ノードは明白な正当性がなければ投票しないものとします。</span><span class="sxs-lookup"><span data-stu-id="aac9b-160">Assume that each node should not vote without explicit justification.</span></span>  
  
-   <span data-ttu-id="aac9b-161">**すべてのプライマリ レプリカを含めます。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-161">**Include all primary replicas.**</span></span> <span data-ttu-id="aac9b-162">可用性グループのプライマリ レプリカをホストしているか、FCI の優先所有者である各 WSFC ノードは、投票を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-162">Each WSFC node that hosts an availability group primary replica or is the preferred owner of an FCI should have a vote.</span></span>  
  
-   <span data-ttu-id="aac9b-163">**可能性のある自動フェールオーバーの所有者を含めます。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-163">**Include possible automatic failover owners.**</span></span> <span data-ttu-id="aac9b-164">自動可用性グループ フェールオーバーまたは FCI フェールオーバーの結果として、プライマリ レプリカをホストする可能性がある各ノードは、投票を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="aac9b-164">Each node that could host a primary replica, as the result of an automatic availability group failover or FCI failover, should have a vote.</span></span> <span data-ttu-id="aac9b-165">WSFC クラスターに可用性グループが 1 つだけあり、可用性レプリカがスタンドアロン インスタンスだけによってホストされている場合、この規則には自動フェールオーバー ターゲットであるセカンダリ レプリカだけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-165">If there is only one availability group in the WSFC cluster and availability replicas are hosted only by standalone instances, this rule includes only the secondary replica that is the automatic failover target.</span></span>  
  
-   <span data-ttu-id="aac9b-166">**セカンダリ サイト ノードを除外します。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-166">**Exclude secondary site nodes.**</span></span> <span data-ttu-id="aac9b-167">通常は、セカンダリ ディザスター リカバリー サイトに存在する WSFC ノードには投票を提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="aac9b-167">In general, do not give votes to WSFC nodes that reside at a secondary disaster recovery site.</span></span>  <span data-ttu-id="aac9b-168">プライマリ サイトに問題がない場合、セカンダリ サイト内のノードがクラスターをオフラインにするという判断に影響を与えることは避けるべきです。</span><span class="sxs-lookup"><span data-stu-id="aac9b-168">You do not want nodes in the secondary site to contribute to a decision to take the cluster offline when there is nothing wrong with the primary site.</span></span>  
  
-   <span data-ttu-id="aac9b-169">**投票数を奇数にします。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-169">**Odd number of votes.**</span></span> <span data-ttu-id="aac9b-170">必要に応じて、監視ファイル共有、監視ノード、または監視ディスクをクラスターに追加し、クォーラム モードを調整してクォーラム投票内の結合を防止します。</span><span class="sxs-lookup"><span data-stu-id="aac9b-170">If necessary, add a witness file share, a witness node, or a witness disk to the cluster and adjust the quorum mode to prevent possible ties in the quorum vote.</span></span>  
  
-   <span data-ttu-id="aac9b-171">**フェールオーバー後の投票割り当てを再評価します。**</span><span class="sxs-lookup"><span data-stu-id="aac9b-171">**Re-assess vote assignments post-failover.**</span></span> <span data-ttu-id="aac9b-172">正常なクォーラムをサポートしないクラスター構成にフェールオーバーすることは避けます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-172">You do not want to fail over into a cluster configuration that does not support a healthy quorum.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aac9b-173">WSFC クォーラム投票の構成を検証するときに、以下の条件が該当する場合、AlwaysOn 可用性グループ ウィザードで警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aac9b-173">When validating WSFC quorum vote configuration, the AlwaysOn Availability Group Wizard shows a warning if any of the following conditions are true:</span></span>  
> 
>  -   <span data-ttu-id="aac9b-174">プライマリ レプリカをホストしているクラスター ノードが投票を持たない。</span><span class="sxs-lookup"><span data-stu-id="aac9b-174">The cluster node that hosts the primary replica does not have a vote</span></span>  
> -   <span data-ttu-id="aac9b-175">セカンダリ レプリカが自動フェールオーバー用に構成されており、そのクラスター ノードが投票を持たない。</span><span class="sxs-lookup"><span data-stu-id="aac9b-175">A secondary replica is configured for automatic failover and its cluster node does not have a vote.</span></span>  
> -   <span data-ttu-id="aac9b-176">可用性レプリカをホストしているすべてのクラスター ノードに[KB2494036](https://support.microsoft.com/kb/2494036) がインストールされていない。</span><span class="sxs-lookup"><span data-stu-id="aac9b-176">[KB2494036](https://support.microsoft.com/kb/2494036) is not installed on all cluster nodes that host availability replicas.</span></span> <span data-ttu-id="aac9b-177">この修正プログラムは、マルチサイト配置でのクラスター ノードに対する投票の追加または削除のために必要です。</span><span class="sxs-lookup"><span data-stu-id="aac9b-177">This patch is required to add or remove votes for cluster nodes in multi-site deployments.</span></span> <span data-ttu-id="aac9b-178">ただし、単一サイト配置では通常は不要であり、警告を無視しても安全です。</span><span class="sxs-lookup"><span data-stu-id="aac9b-178">However, in single-site deployments, it is usually not required and you may safely ignore the warning.</span></span>  
> 
> [!TIP]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="aac9b-179">WSFC クラスター構成およびノード クォーラム投票に関する設定を管理するために、いくつかのシステム動的管理ビュー (DMV) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="aac9b-179">exposes several system dynamic management views (DMVs) that can help you manage settings related WSFC cluster configuration and node quorum voting.</span></span>  
> 
>  <span data-ttu-id="aac9b-180">詳細については、  [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), [sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql), [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aac9b-180">For more information, see:  [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), [sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql), [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="aac9b-181">関連タスク</span><span class="sxs-lookup"><span data-stu-id="aac9b-181">Related Tasks</span></span>  
  
-   [<span data-ttu-id="aac9b-182">クラスター クォーラムの NodeWeight 設定を表示</span><span class="sxs-lookup"><span data-stu-id="aac9b-182">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="aac9b-183">クラスター クォーラムの NodeWeight の設定の構成</span><span class="sxs-lookup"><span data-stu-id="aac9b-183">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="aac9b-184">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="aac9b-184">Related Content</span></span>  
  
-   [<span data-ttu-id="aac9b-185">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="aac9b-185">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [<span data-ttu-id="aac9b-186">AlwaysOn 可用性グループ ウィザードでのクォーラムの投票の構成のチェック</span><span class="sxs-lookup"><span data-stu-id="aac9b-186">Quorum vote configuration check in AlwaysOn Availability Group Wizards</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/03/13/quorum-vote-configuration-check-in-alwayson-availability-group-wizards-andy-jing.aspx)  
  
-   <span data-ttu-id="aac9b-187">[Windows Server テクノロジ: フェールオーバー クラスター](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="aac9b-187">[Windows Server Technologies:  Failover Clusters](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)</span></span>  
  
-   <span data-ttu-id="aac9b-188">[フェールオーバー クラスターのステップ バイ ステップ ガイド: フェールオーバー クラスターのクォーラムの構成](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="aac9b-188">[Failover Cluster Step-by-Step Guide: Configuring the Quorum in a Failover Cluster](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac9b-189">参照</span><span class="sxs-lookup"><span data-stu-id="aac9b-189">See Also</span></span>  
 <span data-ttu-id="aac9b-190">[WSFC の強制クォーラムによるディザスターリカバリー &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aac9b-190">[WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span></span>  
 [<span data-ttu-id="aac9b-191">Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server</span><span class="sxs-lookup"><span data-stu-id="aac9b-191">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
