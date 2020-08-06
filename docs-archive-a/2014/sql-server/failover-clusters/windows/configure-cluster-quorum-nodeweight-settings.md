---
title: クラスター クォーラムの NodeWeight の設定の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: cb3fd9a6-39a2-4e9c-9157-619bf3db9951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e469d5fc0fc030304a7cf2f1bdd894eb578aa056
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640534"
---
# <a name="configure-cluster-quorum-nodeweight-settings"></a><span data-ttu-id="8c57f-102">クラスター クォーラムの NodeWeight の設定の構成</span><span class="sxs-lookup"><span data-stu-id="8c57f-102">Configure Cluster Quorum NodeWeight Settings</span></span>
  <span data-ttu-id="8c57f-103">このトピックでは、Windows Server フェールオーバー クラスタリング (WSFC) クラスター内のメンバー ノードに NodeWeight 設定を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c57f-103">This topic describes how to configure NodeWeight settings for a member node in a Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="8c57f-104">NodeWeight 設定は、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスのディザスター リカバリーとマルチサブネットのシナリオをサポートするためのクォーラムの投票時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c57f-104">NodeWeight settings are used during quorum voting to support disaster recovery and multi-subnet scenarios for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="8c57f-105">**開始前の準備:** [前提条件](#Prerequisites)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="8c57f-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="8c57f-106">**クォーラムの NodeWeight 設定を表示する方法:** [Powershell の使用](#PowerShellProcedure)、[Cluster.exe の使用](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="8c57f-106">**To view quorum NodeWeight settings using:** [Using Powershell](#PowerShellProcedure), [Using Cluster.exe](#CommandPromptProcedure)</span></span>  
  
-   [<span data-ttu-id="8c57f-107">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="8c57f-107">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8c57f-108">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="8c57f-108">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="8c57f-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="8c57f-109">Prerequisites</span></span>  
 <span data-ttu-id="8c57f-110">この機能は [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 以降のバージョンでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8c57f-110">This feature is supported only in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] or later versions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8c57f-111">NodeWeight 設定を使用するには、次の修正プログラムが WSFC クラスターのすべてのサーバーに適用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c57f-111">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="8c57f-112">[KB2494036](https://support.microsoft.com/kb/2494036):この修正プログラムを使用すると、[!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] および [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] でクォーラムの投票のないクラスター ノードを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="8c57f-112">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="8c57f-113">この修正プログラムがインストールされていない場合、このトピックの例では、NodeWeight に対して空の値または NULL 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="8c57f-113">If this hotfix is not installed, the examples in this topic will return empty or NULL values for NodeWeight.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8c57f-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8c57f-114">Security</span></span>  
 <span data-ttu-id="8c57f-115">ユーザーは、WSFC クラスターの各ノードのローカル Administrators グループのメンバーであるドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c57f-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="8c57f-116">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="8c57f-116">Using Powershell</span></span>  
  
### <a name="to-configure-nodeweight-settings"></a><span data-ttu-id="8c57f-117">NodeWeight 設定を構成するには</span><span class="sxs-lookup"><span data-stu-id="8c57f-117">To configure NodeWeight settings</span></span>
  
1.  <span data-ttu-id="8c57f-118">**[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。</span><span class="sxs-lookup"><span data-stu-id="8c57f-118">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="8c57f-119">`FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8c57f-119">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="8c57f-120">`Get-ClusterNode` オブジェクトを使用して、クラスター内の各ノードに `NodeWeight` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8c57f-120">Use the `Get-ClusterNode` object to set the `NodeWeight` property for each node in the cluster.</span></span>  
  
4.  <span data-ttu-id="8c57f-121">クラスター ノードのプロパティを判読可能な形式で出力します。</span><span class="sxs-lookup"><span data-stu-id="8c57f-121">Output the cluster node properties in a readable format.</span></span>  
  
 <span data-ttu-id="8c57f-122">次の例では、NodeWeight 設定を "AlwaysOnSrv1" ノードのクォーラムの投票を削除するように変更して、クラスター内のすべてのノードに設定を出力します。</span><span class="sxs-lookup"><span data-stu-id="8c57f-122">The following example changes the NodeWeight setting to remove the quorum vote for the "AlwaysOnSrv1" node, and then outputs the settings for all nodes in the cluster.</span></span>
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv1"  
(Get-ClusterNode $node).NodeWeight = 0  
  
$cluster = (Get-ClusterNode $node).Cluster  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="8c57f-123">cluster.exe の使用</span><span class="sxs-lookup"><span data-stu-id="8c57f-123">Using Cluster.exe</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c57f-124">cluster.exe ユーティリティは [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] リリースでは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="8c57f-124">The cluster.exe utility is deprecated in the [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] release.</span></span>  <span data-ttu-id="8c57f-125">今後は PowerShell とフェールオーバー クラスタリングを使用してください。</span><span class="sxs-lookup"><span data-stu-id="8c57f-125">Please use PowerShell with Failover Clustering for future development.</span></span>  <span data-ttu-id="8c57f-126">cluster.exe ユーティリティは、Windows Server の次のリリースで削除されます。</span><span class="sxs-lookup"><span data-stu-id="8c57f-126">The cluster.exe utility will be removed in the next release of Windows Server.</span></span> <span data-ttu-id="8c57f-127">詳細については、「 [フェールオーバー クラスターの Windows PowerShell コマンドレットへの Cluster.exe コマンドのマッピング](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c57f-127">For more information, see [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).</span></span>  
  
### <a name="to-configure-nodeweight-settings"></a><span data-ttu-id="8c57f-128">NodeWeight 設定を構成するには</span><span class="sxs-lookup"><span data-stu-id="8c57f-128">To configure NodeWeight settings</span></span>
  
1.  <span data-ttu-id="8c57f-129">**[実行管理者として実行]** から高度な権限でコマンド プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="8c57f-129">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="8c57f-130">**cluster.exe** を使用して、 `NodeWeight` 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="8c57f-130">Use **cluster.exe** to set `NodeWeight` values.</span></span>  

 <span data-ttu-id="8c57f-131">次の例では、NodeWeight の値を "Cluster001" クラスターで "AlwaysOnSrv1" ノードのクォーラムの投票を削除するように変更します。</span><span class="sxs-lookup"><span data-stu-id="8c57f-131">The following example changes the NodeWeight value to remove the quorum vote of the "AlwaysOnSrv1" node in the "Cluster001" cluster.</span></span>  
  
```cmd
cluster.exe Cluster001 node AlwaysOnSrv1 /prop NodeWeight=0  
```  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="8c57f-132">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="8c57f-132">Related Content</span></span>  
  
-   <span data-ttu-id="8c57f-133">[フェールオーバー クラスターのイベントおよびログを表示する](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8c57f-133">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="8c57f-134">Get-ClusterLog フェールオーバー クラスター コマンドレット</span><span class="sxs-lookup"><span data-stu-id="8c57f-134">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="8c57f-135">参照</span><span class="sxs-lookup"><span data-stu-id="8c57f-135">See Also</span></span>  
 <span data-ttu-id="8c57f-136">[WSFC クォーラムモードと投票の構成 &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8c57f-136">[WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="8c57f-137">[クラスタークォーラムの NodeWeight の設定を表示する](view-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="8c57f-137">[View Cluster Quorum NodeWeight Settings](view-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="8c57f-138">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus (タスク フォーカスによって一覧表示される Windows PowerShell でのフェールオーバー クラスター コマンドレット)](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8c57f-138">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
