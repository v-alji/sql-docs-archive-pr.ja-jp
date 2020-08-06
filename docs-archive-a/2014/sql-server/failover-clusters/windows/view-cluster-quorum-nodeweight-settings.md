---
title: クラスター クォーラムの NodeWeight 設定を表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: b845e73a-bb01-4de2-aac2-8ac12abebc95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef2176d4916e8affbb9ef89c9b26499289c520ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640519"
---
# <a name="view-cluster-quorum-nodeweight-settings"></a><span data-ttu-id="7269f-102">クラスター クォーラムの NodeWeight 設定を表示</span><span class="sxs-lookup"><span data-stu-id="7269f-102">View Cluster Quorum NodeWeight Settings</span></span>
  <span data-ttu-id="7269f-103">このトピックでは、Windows Server フェールオーバー クラスタリング (WSFC) クラスター内の各メンバー ノードの NodeWeight 設定を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7269f-103">This topic describes how to view NodeWeight settings for each member node in a Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="7269f-104">NodeWeight 設定は、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスのディザスター リカバリーとマルチサブネットのシナリオをサポートするためのクォーラムの投票時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7269f-104">NodeWeight settings are used during quorum voting to support disaster recovery and multi-subnet scenarios for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="7269f-105">**開始前の準備:** [前提条件](#Prerequisites)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="7269f-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="7269f-106">**クォーラムの NodeWeight 設定を表示する方法:** [Transact-SQL の使用](#TsqlProcedure)、[PowerShell の使用](#PowerShellProcedure)、[Cluster.exe の使用](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="7269f-106">**To view quorum NodeWeight settings using:** [Using Transact-SQL](#TsqlProcedure), [Using Powershell](#PowerShellProcedure), [Using Cluster.exe](#CommandPromptProcedure)</span></span>  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7269f-107">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="7269f-107">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="7269f-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="7269f-108">Prerequisites</span></span>  
 <span data-ttu-id="7269f-109">この機能は [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 以降のバージョンでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7269f-109">This feature is supported only in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] or later versions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7269f-110">NodeWeight 設定を使用するには、次の修正プログラムが WSFC クラスターのすべてのサーバーに適用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7269f-110">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="7269f-111">[KB2494036](https://support.microsoft.com/kb/2494036):この修正プログラムを使用すると、[!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] および [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] でクォーラムの投票のないクラスター ノードを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="7269f-111">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="7269f-112">この修正プログラムがインストールされていない場合、このトピックの例では、NodeWeight に対して空の値または NULL 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="7269f-112">If this hotfix is not installed, the examples in this topic will return empty or NULL values for NodeWeight.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7269f-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7269f-113">Security</span></span>  
 <span data-ttu-id="7269f-114">ユーザーは、WSFC クラスターの各ノードのローカル Administrators グループのメンバーであるドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7269f-114">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7269f-115">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7269f-115">Using Transact-SQL</span></span>  
  
##### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="7269f-116">NodeWeight 設定を表示するには</span><span class="sxs-lookup"><span data-stu-id="7269f-116">To view NodeWeight settings</span></span>  
  
1.  <span data-ttu-id="7269f-117">クラスター内の任意の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7269f-117">Connect to any [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the cluster.</span></span>  
  
2.  <span data-ttu-id="7269f-118">[sys].[dm_hadr_cluster_members] ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="7269f-118">Query the [sys].[dm_hadr_cluster_members] view.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="7269f-119">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7269f-119">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="7269f-120">次の例では、システム ビューに対するクエリを実行して、そのインスタンスのクラスター内のすべてのノードの値を返します。</span><span class="sxs-lookup"><span data-stu-id="7269f-120">The following example queries a system view to return values for all of the nodes in that instance's cluster.</span></span>  
  
```sql  
SELECT  member_name, member_state_desc, number_of_quorum_votes  
 FROM   sys.dm_hadr_cluster_members;  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="7269f-121">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="7269f-121">Using Powershell</span></span>  
  
### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="7269f-122">NodeWeight 設定を表示するには</span><span class="sxs-lookup"><span data-stu-id="7269f-122">To view NodeWeight settings</span></span>
  
1.  <span data-ttu-id="7269f-123">**[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。</span><span class="sxs-lookup"><span data-stu-id="7269f-123">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="7269f-124">`FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7269f-124">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="7269f-125">`Get-ClusterNode` オブジェクトを使用して、クラスター ノード オブジェクトのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="7269f-125">Use the `Get-ClusterNode` object to return a collection of cluster node objects.</span></span>  
  
4.  <span data-ttu-id="7269f-126">クラスター ノードのプロパティを判読可能な形式で出力します。</span><span class="sxs-lookup"><span data-stu-id="7269f-126">Output the cluster node properties in a readable format.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="7269f-127">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="7269f-127">Example (Powershell)</span></span>  
 <span data-ttu-id="7269f-128">次の例では、"Cluster001" というクラスターについて、ノードの一部のプロパティを出力します。</span><span class="sxs-lookup"><span data-stu-id="7269f-128">The following example output some of the node properties for the cluster called "Cluster001".</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$cluster = "Cluster001"  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -Property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="7269f-129">cluster.exe の使用</span><span class="sxs-lookup"><span data-stu-id="7269f-129">Using Cluster.exe</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7269f-130">cluster.exe ユーティリティは [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] リリースでは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="7269f-130">The cluster.exe utility is deprecated in the [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] release.</span></span>  <span data-ttu-id="7269f-131">今後は PowerShell とフェールオーバー クラスタリングを使用してください。</span><span class="sxs-lookup"><span data-stu-id="7269f-131">Please use PowerShell with Failover Clustering for future development.</span></span>  <span data-ttu-id="7269f-132">cluster.exe ユーティリティは、Windows Server の次のリリースで削除されます。</span><span class="sxs-lookup"><span data-stu-id="7269f-132">The cluster.exe utility will be removed in the next release of Windows Server.</span></span> <span data-ttu-id="7269f-133">詳細については、「 [フェールオーバー クラスターの Windows PowerShell コマンドレットへの Cluster.exe コマンドのマッピング](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7269f-133">For more information, see [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).</span></span>  
  
##### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="7269f-134">NodeWeight 設定を表示するには</span><span class="sxs-lookup"><span data-stu-id="7269f-134">To view NodeWeight settings</span></span>  
  
1.  <span data-ttu-id="7269f-135">**[実行管理者として実行]** から高度な権限でコマンド プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="7269f-135">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="7269f-136">**cluster.exe** を使用して、ノードの状態と NodeWeight の値を返します。</span><span class="sxs-lookup"><span data-stu-id="7269f-136">Use **cluster.exe** to return node status and NodeWeight values</span></span>  
  
### <a name="example-clusterexe"></a><span data-ttu-id="7269f-137">例 (Cluster.exe)</span><span class="sxs-lookup"><span data-stu-id="7269f-137">Example (Cluster.exe)</span></span>  
 <span data-ttu-id="7269f-138">次の例では、"Cluster001" というクラスターについて、ノードの一部のプロパティを出力します。</span><span class="sxs-lookup"><span data-stu-id="7269f-138">The following example outputs some of the node properties for the cluster called "Cluster001".</span></span>  
  
```cmd
cluster.exe Cluster001 node /status /properties  
```  
  
## <a name="see-also"></a><span data-ttu-id="7269f-139">参照</span><span class="sxs-lookup"><span data-stu-id="7269f-139">See Also</span></span>  
 <span data-ttu-id="7269f-140">[WSFC クォーラム モードと投票の構成 &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7269f-140">[WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="7269f-141">[クラスター クォーラムの NodeWeight の設定の構成](configure-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7269f-141">[Configure Cluster Quorum NodeWeight Settings](configure-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="7269f-142">[sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7269f-142">[sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql) </span></span>  
 <span data-ttu-id="7269f-143">[タスク フォーカスによって一覧表示される Windows PowerShell でのフェールオーバー クラスター コマンドレット](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7269f-143">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
