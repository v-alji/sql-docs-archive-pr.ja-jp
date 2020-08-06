---
title: FailureConditionLevel プロパティ設定の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8924b864d7cc8be078b370e3182713114f54ff6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640535"
---
# <a name="configure-failureconditionlevel-property-settings"></a><span data-ttu-id="30566-102">FailureConditionLevel プロパティ設定の構成</span><span class="sxs-lookup"><span data-stu-id="30566-102">Configure FailureConditionLevel Property Settings</span></span>
  <span data-ttu-id="30566-103">FailureConditionLevel プロパティを使用して、AlwaysOn フェールオーバー クラスター インスタンス (FCI) がフェールオーバーまたは再起動するための状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="30566-103">Use the FailureConditionLevel property to set the conditions for the AlwaysOn Failover Cluster Instance (FCI) to fail over or restart.</span></span> <span data-ttu-id="30566-104">このプロパティへの変更はすぐに適用され、Windows Server フェールオーバー クラスター サービス (WSFC) または FCI リソースの再起動を必要としません。</span><span class="sxs-lookup"><span data-stu-id="30566-104">Changes to this property are applied immediately without requiring a restart of the Windows Server Failover Cluster (WSFC) service or the FCI resource.</span></span>  
  
-   <span data-ttu-id="30566-105">**作業を開始する準備:** [FailureConditionLevel プロパティの設定](#Restrictions)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="30566-105">**Before you begin:**  [FailureConditionLevel Property Settings](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="30566-106">**FailureConditionLevel プロパティ設定の構成に使用する機能:** [PowerShell](#PowerShellProcedure)、[フェールオーバー クラスター マネージャー](#WSFC)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="30566-106">**To configure the FailureConditionLevel property settings using,** [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="30566-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="30566-107">Before You Begin</span></span>  
  
###  <a name="failureconditionlevel-property-settings"></a><a name="Restrictions"></a> <span data-ttu-id="30566-108">FailureConditionLevel プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="30566-108">FailureConditionLevel Property Settings</span></span>  
 <span data-ttu-id="30566-109">エラー状態にはレベルが設定されています。</span><span class="sxs-lookup"><span data-stu-id="30566-109">The failure conditions are set on an increasing scale.</span></span> <span data-ttu-id="30566-110">レベル 1 ～ 5 の各レベルには、前のレベルのすべての状態に加えて独自の状態が含まれています。</span><span class="sxs-lookup"><span data-stu-id="30566-110">For levels 1-5, each level includes all the conditions from the previous levels in addition to its own conditions.</span></span> <span data-ttu-id="30566-111">これは、それぞれのレベルで、フェールオーバーまたは再起動の可能性が増加することを意味します。</span><span class="sxs-lookup"><span data-stu-id="30566-111">This means that with each level, there is an increased probability of a failover or restart.</span></span>  <span data-ttu-id="30566-112">詳細については、この「 [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) 」の「フェールオーバーの特定」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="30566-112">For more information, see the "Determining Failures" section of the [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="30566-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="30566-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="30566-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="30566-114">Permissions</span></span>  
 <span data-ttu-id="30566-115">ALTER SETTINGS 権限および VIEW SERVER STATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="30566-115">Requires ALTER SETTINGS and VIEW SERVER STATE permissions.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="30566-116">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="30566-116">Using PowerShell</span></span>  
  
### <a name="to-configure-failureconditionlevel-settings"></a><span data-ttu-id="30566-117">FailureConditionLevel 設定を構成するには</span><span class="sxs-lookup"><span data-stu-id="30566-117">To configure FailureConditionLevel settings</span></span>  
  
1.  <span data-ttu-id="30566-118">**[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。</span><span class="sxs-lookup"><span data-stu-id="30566-118">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="30566-119">`FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。</span><span class="sxs-lookup"><span data-stu-id="30566-119">Import the `FailoverClusters` module to enable cluster cmdlets.</span></span>  
  
3.  <span data-ttu-id="30566-120">コマンドレットを使用して `Get-ClusterResource` リソースを検索 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] し、次にコマンドレットを使用して、 `Set-ClusterParameter` フェールオーバークラスターインスタンスの**failureconditionlevel**プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="30566-120">Use the `Get-ClusterResource` cmdlet to find the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource, then use `Set-ClusterParameter` cmdlet to set the **FailureConditionLevel** property for a Failover Cluster Instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="30566-121">新しい PowerShell ウィンドウを開くたびに、`FailoverClusters` モジュールをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="30566-121">Every time you open a new PowerShell window, you need to import the `FailoverClusters` module.</span></span>  

 <span data-ttu-id="30566-122">次の例では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソース "`SQL Server (INST1)`" の FailureConditionLevel 設定が、重大なサーバー エラー発生時のフェールオーバーまたは再起動に変更されます。</span><span class="sxs-lookup"><span data-stu-id="30566-122">The following example changes the FailureConditionLevel setting on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource "`SQL Server (INST1)`" to fail over or restart on critical server errors.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3
```  
  
### <a name="related-content-powershell"></a><span data-ttu-id="30566-123">関連コンテンツ (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="30566-123">Related Content (PowerShell)</span></span>  
  
-   <span data-ttu-id="30566-124">[クラスターと高可用性](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (フェールオーバー クラスタリングとネットワーク負荷分散のチームのブログ)</span><span class="sxs-lookup"><span data-stu-id="30566-124">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Failover Clustering and Network Load Balancing Team Blog)</span></span>  
  
-   <span data-ttu-id="30566-125">[フェールオーバー クラスターの Windows PowerShell の概要](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="30566-125">[Getting Started with Windows PowerShell on a Failover Cluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="30566-126">クラスター リソースのコマンドと同等の Windows PowerShell コマンドレット</span><span class="sxs-lookup"><span data-stu-id="30566-126">Cluster resource commands and equivalent Windows PowerShell cmdlets</span></span>](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="30566-127">フェールオーバー クラスター マネージャー スナップインの使用</span><span class="sxs-lookup"><span data-stu-id="30566-127">Using the Failover Cluster Manager Snap-in</span></span>  

### <a name="to-configure-failureconditionlevel-property-settings"></a><span data-ttu-id="30566-128">FailureConditionLevel プロパティの設定を構成するには</span><span class="sxs-lookup"><span data-stu-id="30566-128">To configure FailureConditionLevel property settings</span></span>
  
1.  <span data-ttu-id="30566-129">フェールオーバー クラスター マネージャー スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="30566-129">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="30566-130">**[サービスとアプリケーション]** を展開し、FCI を選択します。</span><span class="sxs-lookup"><span data-stu-id="30566-130">Expand the **Services and Applications** and select the FCI.</span></span>  
  
3.  <span data-ttu-id="30566-131">**[その他のリソース]** の下の **[SQL Server リソース]** を右クリックし、表示されるメニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30566-131">Right-click the **SQL Server resource** under **Other Resources**, and then select **Properties** from the menu.</span></span> <span data-ttu-id="30566-132">SQL Server リソースの **[プロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30566-132">The SQL Server resource **Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="30566-133">**[プロパティ]** タブをクリックし、 **[FaliureConditionLevel]** プロパティに値を入力し、 **[OK]** をクリックして変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="30566-133">Select the **Properties** tab, enter the desired value for the **FaliureConditionLevel** property, and then click **OK** to apply the change.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="30566-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="30566-134">Using Transact-SQL</span></span>  

### <a name="to-configure-failureconditionlevel-property-settings"></a><span data-ttu-id="30566-135">FailureConditionLevel プロパティの設定を構成するには</span><span class="sxs-lookup"><span data-stu-id="30566-135">To configure FailureConditionLevel property settings</span></span>
  
 <span data-ttu-id="30566-136">[ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用すると、FailureConditionLevel プロパティ値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="30566-136">Using the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, you can specify the FailureConditionLevel property value.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="30566-137">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="30566-137">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="30566-138">次の例では、FailureConditionLevel プロパティを 0 に設定します。この場合、どのようなエラー状態でも、フェールオーバーまたは再起動が自動的に行われないように指定されます。</span><span class="sxs-lookup"><span data-stu-id="30566-138">The following example sets the FailureConditionLevel property to 0, indicating that failover or restart will not be triggered automatically on any failure conditions.</span></span>  
  
```sql
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a><span data-ttu-id="30566-139">参照</span><span class="sxs-lookup"><span data-stu-id="30566-139">See Also</span></span>  
 <span data-ttu-id="30566-140">[sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="30566-140">[sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) </span></span>  
 [<span data-ttu-id="30566-141">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="30566-141">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
