---
title: クォーラムを使用せずに WSFC クラスターを強制的に起動する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: 4a121375-7424-4444-b876-baefa8fe9015
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6f2110b706de015d0c7b19475b335908c118267
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640522"
---
# <a name="force-a-wsfc-cluster-to-start-without-a-quorum"></a><span data-ttu-id="cc7fd-102">クォーラムを使用せずに WSFC クラスターを強制的に起動する</span><span class="sxs-lookup"><span data-stu-id="cc7fd-102">Force a WSFC Cluster to Start Without a Quorum</span></span>
  <span data-ttu-id="cc7fd-103">このトピックでは、クォーラムを使用せずに Windows Server フェールオーバー クラスタリング (WSFC) クラスター ノードを強制的に起動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-103">This topic describes how to force a Windows Server Failover Clustering (WSFC) cluster node to start without a quorum.</span></span>  <span data-ttu-id="cc7fd-104">この処理が必要になるのは、ディザスター リカバリーとマルチサブネットのシナリオにおいて、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスのデータを復旧し、高可用性を完全に再確立する場合です。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-104">This may be required in disaster recovery and multi-subnet scenarios to recover data and fully re-establish high-availability for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="cc7fd-105">**開始前の準備:**  [推奨事項](#Recommendations)、 [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="cc7fd-105">**Before you start:**  [Recommendations](#Recommendations), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="cc7fd-106">**クォーラムを使用せずにクラスターを強制的に起動する方法:**  [フェールオーバー クラスター マネージャーの使用](#FailoverClusterManagerProcedure)、 [PowerShell の使用](#PowerShellProcedure)、 [net.exe の使用](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="cc7fd-106">**To force a cluster to start without a quorum using:**  [Using Failover Cluster Manager](#FailoverClusterManagerProcedure), [Using Powershell](#PowerShellProcedure), [Using Net.exe](#CommandPromptProcedure)</span></span>  
  
-   <span data-ttu-id="cc7fd-107">**補足情報:**  [補足情報: クォーラムを使用せずにクラスターを強制的に起動した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="cc7fd-107">**Follow up:**  [Follow Up: After Forcing Cluster to Start without a Quorum](#FollowUp)</span></span>  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cc7fd-108">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="cc7fd-108">Before You Start</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="cc7fd-109">推奨事項</span><span class="sxs-lookup"><span data-stu-id="cc7fd-109">Recommendations</span></span>  
 <span data-ttu-id="cc7fd-110">明示的に指定されている場合を除き、このトピックの手順は、WSFC クラスター内のノードから実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-110">Except where explicitly directed, the procedures in this topic should work if you execute them from any node in the WSFC cluster.</span></span>  <span data-ttu-id="cc7fd-111">ただし、クォーラムを使用せずに強制的に起動する対象となるノードからこれらの手順を実行することにより、適切な結果が得られ、ネットワークの問題の発生を回避できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-111">However, you may obtain better results, and avoid networking issues, by executing these steps from the node that you intend to force to start without a quorum.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cc7fd-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cc7fd-112">Security</span></span>  
 <span data-ttu-id="cc7fd-113">ユーザーは、WSFC クラスターの各ノードのローカル Administrators グループのメンバーであるドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-113">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-failover-cluster-manager"></a><a name="FailoverClusterManagerProcedure"></a> <span data-ttu-id="cc7fd-114">フェールオーバー クラスター マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="cc7fd-114">Using Failover Cluster Manager</span></span>  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="cc7fd-115">クォーラムを使用せずにクラスターを強制的に起動するには</span><span class="sxs-lookup"><span data-stu-id="cc7fd-115">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="cc7fd-116">フェールオーバー クラスター マネージャーを開き、強制的にオンラインにする目的のクラスター ノードに接続します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-116">Open a Failover Cluster Manager and connect to the desired cluster node to force online.</span></span>  
  
2.  <span data-ttu-id="cc7fd-117">[**操作**] ウィンドウで、[**クラスターの強制起動**] をクリックし、[は**い-クラスターを強制的に起動する**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-117">In the **Actions** pane, click **Force Cluster Start**, and then click **Yes - Force my cluster to start**.</span></span>  
  
3.  <span data-ttu-id="cc7fd-118">左ペインにある **[フェールオーバー クラスター マネージャー]** ツリーで、クラスター名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-118">In the left pane, in the **Failover Cluster Manager** tree, click the cluster name.</span></span>  
  
4.  <span data-ttu-id="cc7fd-119">概要ペインで、 **[クォーラムの構成]** の現在の値が  **[警告: クラスターは ForceQuorum 状態で実行中です]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-119">In the summary pane, confirm that the current **Quorum Configuration** value is:  **Warning: Cluster is running in ForceQuorum state**.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="cc7fd-120">Powershell の使用</span><span class="sxs-lookup"><span data-stu-id="cc7fd-120">Using Powershell</span></span>  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="cc7fd-121">クォーラムを使用せずにクラスターを強制的に起動するには</span><span class="sxs-lookup"><span data-stu-id="cc7fd-121">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="cc7fd-122">**[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-122">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="cc7fd-123">`FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-123">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="cc7fd-124">`Stop-ClusterNode` を使用して、クラスター サービスが停止していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-124">Use `Stop-ClusterNode` to make sure that the cluster service is stopped.</span></span>  
  
4.  <span data-ttu-id="cc7fd-125">`Start-ClusterNode` を指定した `-FixQuorum` を使用して、クラスター サービスを強制的に起動します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-125">Use `Start-ClusterNode` with `-FixQuorum` to force the cluster service to start.</span></span>  
  
5.  <span data-ttu-id="cc7fd-126">`Get-ClusterNode` を指定した `-Propery NodeWieght = 1` を使用して、ノードがクォーラムの投票メンバーであることを保証する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-126">Use `Get-ClusterNode` with `-Propery NodeWieght = 1` to set the value the guarantees that the node is a voting member of the quorum.</span></span>  
  
6.  <span data-ttu-id="cc7fd-127">クラスター ノードのプロパティを判読可能な形式で出力します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-127">Output the cluster node properties in a readable format.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="cc7fd-128">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="cc7fd-128">Example (Powershell)</span></span>  
 <span data-ttu-id="cc7fd-129">次の例では、クォーラムを使用せずに AlwaysOnSrv02 ノードのクラスター サービスを強制的に起動します。また、 `NodeWeight = 1`を設定し、新しく強制的に起動されたノードからクラスター ノードの状態を列挙します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-129">The following example forces the AlwaysOnSrv02 node cluster service to start without a quorum, sets the `NodeWeight = 1`, and then enumerates cluster node status from the newly forced node.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv02"  
Stop-ClusterNode -Name $node  
Start-ClusterNode -Name $node -FixQuorum  
  
(Get-ClusterNode $node).NodeWeight = 1  
  
$nodes = Get-ClusterNode -Cluster $node  
$nodes | Format-Table -property NodeName, State, NodeWeight
```  
  
##  <a name="using-netexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="cc7fd-130">net.exe の使用</span><span class="sxs-lookup"><span data-stu-id="cc7fd-130">Using Net.exe</span></span>  
  
### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="cc7fd-131">クォーラムを使用せずにクラスターを強制的に起動するには</span><span class="sxs-lookup"><span data-stu-id="cc7fd-131">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="cc7fd-132">リモート デスクトップを使用して、強制的にオンラインにする目的のクラスター ノードに接続します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-132">Use Remote Desktop to connect to the desired cluster node to force online.</span></span>  
  
2.  <span data-ttu-id="cc7fd-133">**[実行管理者として実行]** から高度な権限でコマンド プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-133">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
3.  <span data-ttu-id="cc7fd-134">**net.exe** を使用して、ローカルのクラスター サービスが停止していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-134">Use **net.exe** to make sure that the local cluster service is stopped.</span></span>  
  
4.  <span data-ttu-id="cc7fd-135">**を指定した** net.exe `/forcequorum` を使用して、ローカルのクラスター サービスを強制的に起動します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-135">Use **net.exe** with `/forcequorum` to force the local cluster service to start.</span></span>  
  
### <a name="example-netexe"></a><span data-ttu-id="cc7fd-136">例 (net.exe)</span><span class="sxs-lookup"><span data-stu-id="cc7fd-136">Example (Net.exe)</span></span>  
 <span data-ttu-id="cc7fd-137">次の例では、クォーラムを使用せずにノードのクラスター サービスを強制的に起動します。また、 `NodeWeight = 1`を設定し、新しく強制的に起動されたノードからクラスター ノードの状態を列挙します。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-137">The following example forces a node cluster service to start without a quorum, sets the `NodeWeight = 1`, and then enumerates cluster node status from the newly forced node.</span></span>  
  
```cmd
net.exe stop clussvc  
net.exe start clussvc /forcequorum  
```  
  
##  <a name="follow-up-after-forcing-cluster-to-start-without-a-quorum"></a><a name="FollowUp"></a><span data-ttu-id="cc7fd-138">補足情報: クォーラムを使用せずにクラスターを強制的に起動した後</span><span class="sxs-lookup"><span data-stu-id="cc7fd-138">Follow Up: After Forcing Cluster to Start without a Quorum</span></span>  
  
-   <span data-ttu-id="cc7fd-139">他のノードをオンラインに戻す前に、NodeWeight の値を再評価および再構成して、新しいクォーラムを正しく構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-139">You must re-evaluate and reconfigure NodeWeight values to correctly construct a new quorum before bringing other nodes back online.</span></span> <span data-ttu-id="cc7fd-140">この処理を行わないと、クラスターが再びオフラインに戻る場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-140">Otherwise, the cluster may go back offline again.</span></span>  
  
     <span data-ttu-id="cc7fd-141">詳細については、「[WSFC クォーラム モードと投票の構成 &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-141">For more information, see [WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md).</span></span>  
  
-   <span data-ttu-id="cc7fd-142">このトピックの手順は、クォーラムに予定外の障害が発生した場合に、WSFC クラスターをオンラインに戻すことのできる唯一の手順です。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-142">The procedures in this topic are only one step in bringing the WSFC cluster back online if an un-planned quorum failure were to occur.</span></span>  <span data-ttu-id="cc7fd-143">他の WSFC クラスター ノードが新しいクォーラム構成に影響を与えないようにするために、追加の手順の実行が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-143">You may also want to take additional steps to prevent other WSFC cluster nodes from interfering with the new quorum configuration.</span></span>  
  
-   <span data-ttu-id="cc7fd-144">また、データを復旧し、高可用性を完全に再確立するために、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のその他の機能 ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]、データベース ミラーリング、ログ配布など) にも追加の操作が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc7fd-144">Other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features such as [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], database mirroring, and log shipping may also require subsequent actions to recover data and to fully re-establish high-availability.</span></span>  
  
     <span data-ttu-id="cc7fd-145">**詳細情報:**</span><span class="sxs-lookup"><span data-stu-id="cc7fd-145">**For more information:**</span></span>  
  
     [<span data-ttu-id="cc7fd-146">可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cc7fd-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
     [<span data-ttu-id="cc7fd-147">データベース ミラーリング セッションでのサービスを強制する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc7fd-147">Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](../../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
  
     [<span data-ttu-id="cc7fd-148">ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cc7fd-148">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="cc7fd-149">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="cc7fd-149">Related Content</span></span>  
  
-   <span data-ttu-id="cc7fd-150">[フェールオーバー クラスターのイベントおよびログを表示する](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="cc7fd-150">[View Events and Logs for a Failover Cluster](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))</span></span>  
  
-   [<span data-ttu-id="cc7fd-151">Get-ClusterLog フェールオーバー クラスター コマンドレット</span><span class="sxs-lookup"><span data-stu-id="cc7fd-151">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="cc7fd-152">参照</span><span class="sxs-lookup"><span data-stu-id="cc7fd-152">See Also</span></span>  
 <span data-ttu-id="cc7fd-153">[WSFC の強制クォーラムによるディザスターリカバリー &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc7fd-153">[WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span></span>  
 <span data-ttu-id="cc7fd-154">[クラスタークォーラムの NodeWeight 設定の構成](configure-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="cc7fd-154">[Configure Cluster Quorum NodeWeight Settings](configure-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="cc7fd-155">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus (タスク フォーカスによって一覧表示される Windows PowerShell でのフェールオーバー クラスター コマンドレット)](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="cc7fd-155">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
