---
title: HealthCheckTimeout プロパティ設定の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a38cd6e9e4718a2f1c136e5412cde340e92f14c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640533"
---
# <a name="configure-healthchecktimeout-property-settings"></a><span data-ttu-id="d7ae5-102">HealthCheckTimeout プロパティ設定の構成</span><span class="sxs-lookup"><span data-stu-id="d7ae5-102">Configure HealthCheckTimeout Property Settings</span></span>
  <span data-ttu-id="d7ae5-103">HealthCheckTimeout 設定は、SQL Server リソース DLL が[sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)ストアドプロシージャから返された情報を待機する時間 (ミリ秒単位) を指定するために使用されます。この時間を経過すると、AlwaysOn フェールオーバークラスターインスタンス (fci) は応答不能として報告されます。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-103">The HealthCheckTimeout setting is used to specify the length of time, in milliseconds, that the SQL Server resource DLL should wait for information returned by the [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) stored procedure before reporting the AlwaysOn Failover Cluster Instance (FCI) as unresponsive.</span></span> <span data-ttu-id="d7ae5-104">タイムアウトの設定に加えられた変更は直ちに有効になり、SQL Server リソースを再起動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-104">Changes that are made to the timeout settings are effective immediately and do not require a restart of the SQL Server resource.</span></span>  
  
-   <span data-ttu-id="d7ae5-105">**作業を開始する準備:** [制限事項と制約事項](#Limits)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="d7ae5-105">**Before you begin:**  [Limitations and Restrictions](#Limits), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="d7ae5-106">**HeathCheckTimeout 設定を構成する方法:**  [PowerShell](#PowerShellProcedure)、 [フェールオーバー クラスター マネージャー](#WSFC)、 [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="d7ae5-106">**To Configure the HeathCheckTimeout setting, using:**  [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d7ae5-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="d7ae5-107">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> <span data-ttu-id="d7ae5-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d7ae5-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="d7ae5-109">このプロパティの既定値は 60,000 ミリ秒 (60 秒) です。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-109">The default value for this property is 60,000 milliseconds (60 seconds).</span></span> <span data-ttu-id="d7ae5-110">最小値は 15,000 ミリ秒 (15 秒) です。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-110">The minimum value is 15,000 milliseconds (15 seconds).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d7ae5-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d7ae5-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d7ae5-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="d7ae5-112">Permissions</span></span>  
 <span data-ttu-id="d7ae5-113">ALTER SETTINGS 権限および VIEW SERVER STATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-113">Requires ALTER SETTINGS and VIEW SERVER STATE permissions.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="d7ae5-114">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="d7ae5-114">Using PowerShell</span></span>  
  
### <a name="to-configure-healthchecktimeout-settings"></a><span data-ttu-id="d7ae5-115">HealthCheckTimeout 設定を構成するには</span><span class="sxs-lookup"><span data-stu-id="d7ae5-115">To configure HealthCheckTimeout settings</span></span>  
  
1.  <span data-ttu-id="d7ae5-116">**[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-116">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="d7ae5-117">`FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-117">Import the `FailoverClusters` module to enable cluster cmdlets.</span></span>  
  
3.  <span data-ttu-id="d7ae5-118">コマンドレットを使用して `Get-ClusterResource` リソースを検索 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] し、次にコマンドレットを使用して、 `Set-ClusterParameter` フェールオーバークラスターインスタンスの**HealthCheckTimeout**プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-118">Use the `Get-ClusterResource` cmdlet to find the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource, then use `Set-ClusterParameter` cmdlet to set the **HealthCheckTimeout** property for the failover cluster instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="d7ae5-119">新しい PowerShell ウィンドウを開くたびに、`FailoverClusters` モジュールをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-119">Every time you open a new PowerShell window, you need to import the `FailoverClusters` module.</span></span>  

 <span data-ttu-id="d7ae5-120">次の例では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソース "`SQL Server (INST1)`" の HealthCheckTimeout 設定が 60000 ミリ秒に変更されます。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-120">The following example changes the HealthCheckTimeout setting on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource "`SQL Server (INST1)`" to 60000 milliseconds.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a><span data-ttu-id="d7ae5-121">関連コンテンツ (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="d7ae5-121">Related Content (PowerShell)</span></span>  
  
-   <span data-ttu-id="d7ae5-122">[クラスターと高可用性](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (フェールオーバー クラスタリングとネットワーク負荷分散のチームのブログ)</span><span class="sxs-lookup"><span data-stu-id="d7ae5-122">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Failover Clustering and Network Load Balancing Team Blog)</span></span>  
  
-   <span data-ttu-id="d7ae5-123">[フェールオーバー クラスターの Windows PowerShell の概要](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="d7ae5-123">[Getting Started with Windows PowerShell on a Failover Cluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="d7ae5-124">クラスター リソースのコマンドと同等の Windows PowerShell コマンドレット</span><span class="sxs-lookup"><span data-stu-id="d7ae5-124">Cluster resource commands and equivalent Windows PowerShell cmdlets</span></span>](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="d7ae5-125">フェールオーバー クラスター マネージャー スナップインの使用</span><span class="sxs-lookup"><span data-stu-id="d7ae5-125">Using the Failover Cluster Manager Snap-in</span></span>  
 <span data-ttu-id="d7ae5-126">**HealthCheckTimeout 設定を構成するには**</span><span class="sxs-lookup"><span data-stu-id="d7ae5-126">**To configure HealthCheckTimeout setting**</span></span>  
  
1.  <span data-ttu-id="d7ae5-127">フェールオーバー クラスター マネージャー スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-127">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="d7ae5-128">**[サービスとアプリケーション]** を展開し、FCI を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-128">Expand **Services and Applications** and select the FCI.</span></span>  
  
3.  <span data-ttu-id="d7ae5-129">**[その他のリソース]** の下の **[SQL Server リソース]** を右クリックし、表示されるメニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-129">Right-click the **SQL Server resource** under **Other Resources** and select **Properties** from the right-click menu.</span></span> <span data-ttu-id="d7ae5-130">SQL Server リソースの **[プロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-130">The SQL Server resource **Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="d7ae5-131">**[プロパティ]** タブをクリックし、 **[HealthCheckTimeout]** プロパティに適切な値を入力し、 **[OK]** をクリックして変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-131">Select the **Properties** tab, enter the desired value for the **HealthCheckTimeout** property, and then click **OK** to apply the change.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d7ae5-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d7ae5-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="d7ae5-133">[ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)ステートメントを使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] HealthCheckTimeOut プロパティ値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-133">Using the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, you can specify the HealthCheckTimeOut property value.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="d7ae5-134">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d7ae5-134">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="d7ae5-135">次の例では、HealthCheckTimeout オプションを 15,000 ミリ秒 (15 秒) に設定します。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-135">The following example sets the HealthCheckTimeout option to 15,000 milliseconds (15 seconds).</span></span>  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7ae5-136">参照</span><span class="sxs-lookup"><span data-stu-id="d7ae5-136">See Also</span></span>  
 [<span data-ttu-id="d7ae5-137">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="d7ae5-137">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
