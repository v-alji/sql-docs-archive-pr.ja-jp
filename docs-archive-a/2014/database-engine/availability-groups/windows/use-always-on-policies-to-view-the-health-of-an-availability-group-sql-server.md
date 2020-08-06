---
title: AlwaysOn ポリシーを使用して可用性グループの正常性を表示する (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c4444afc2348b2407dc19c1c12761ef0251631e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741262"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a><span data-ttu-id="eb616-102">AlwaysOn ポリシーを使用した可用性グループの正常性の確認 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eb616-102">Use AlwaysOn Policies to View the Health of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="eb616-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の AlwaysOn ポリシーまたは [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の PowerShell を使用して、AlwaysOn 可用性グループの運用状態の正常性を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb616-103">This topic describes how to determine the operational health of an AlwaysOn availability group by using an AlwaysOn policy in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="eb616-104">AlwaysOn ポリシーベースの管理の詳細については、「 [AlwaysOn 可用性グループでの運用上の問題の Alwayson ポリシー」 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb616-104">For information about AlwaysOn Policy Based Management, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eb616-105">AlwaysOn ポリシーでは、カテゴリの名前が ID として使用されます。</span><span class="sxs-lookup"><span data-stu-id="eb616-105">For AlwaysOn policies, the category names are used as IDs.</span></span> <span data-ttu-id="eb616-106">AlwaysOn カテゴリの名前を変更すると、正常性評価の機能を使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="eb616-106">Changing the name of an AlwaysOn category would break its health-evaluation functionality.</span></span> <span data-ttu-id="eb616-107">このため、AlwaysOn カテゴリの名前は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="eb616-107">Therefore, the names of AlwaysOn category should never be modified.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb616-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="eb616-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb616-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="eb616-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eb616-110">Permissions</span><span class="sxs-lookup"><span data-stu-id="eb616-110">Permissions</span></span>  
 <span data-ttu-id="eb616-111">CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eb616-111">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="using-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a><span data-ttu-id="eb616-112">AlwaysOn ダッシュボードの使用</span><span class="sxs-lookup"><span data-stu-id="eb616-112">Using the AlwaysOn Dashboard</span></span>  
 <span data-ttu-id="eb616-113">**AlwaysOn ダッシュボードを開くには**</span><span class="sxs-lookup"><span data-stu-id="eb616-113">**To open the AlwaysOn Dashboard**</span></span>  
  
1.  <span data-ttu-id="eb616-114">オブジェクト エクスプローラーで、可用性レプリカの 1 つをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="eb616-114">In Object Explorer, connect to the server instance that hosts one of the availability replicas.</span></span> <span data-ttu-id="eb616-115">可用性グループ内のすべての可用性レプリカについての情報を表示するには、プライマリ レプリカをホストするサーバー インスタンスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="eb616-115">To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="eb616-116">サーバー名をクリックし、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="eb616-116">Click the server name to expand the server tree.</span></span>  
  
3.  <span data-ttu-id="eb616-117">**[AlwaysOn 高可用性]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="eb616-117">Expand the **AlwaysOn High Availability** node.</span></span>  
  
     <span data-ttu-id="eb616-118">**[可用性グループ]** ノードを右クリックするか、このノードを展開し、特定の可用性グループを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="eb616-118">Either right-click the **Availability Groups** node or expand this node and right-click a specific availability group.</span></span>  
  
4.  <span data-ttu-id="eb616-119">**[ダッシュボードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb616-119">Select the **Show Dashboard** command.</span></span>  
  
 <span data-ttu-id="eb616-120">AlwaysOn ダッシュボードの使用方法の詳細については、「[AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb616-120">For information about how to use the AlwaysOn Dashboard, see [Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="eb616-121">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="eb616-121">Using PowerShell</span></span>  
 <span data-ttu-id="eb616-122">**AlwaysOn ポリシーを使用して可用性グループの正常性を表示する**</span><span class="sxs-lookup"><span data-stu-id="eb616-122">**Use AlwaysOn policies to view the health of an availability group**</span></span>  
  
1.  <span data-ttu-id="eb616-123">可用性レプリカの 1 つをホストするサーバー インスタンスを既定の操作対象に設定 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="eb616-123">Set default (`cd`) to a server instance that hosts one of the availability replicas.</span></span> <span data-ttu-id="eb616-124">可用性グループ内のすべての可用性レプリカについての情報を表示するには、プライマリ レプリカをホストするサーバー インスタンスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="eb616-124">To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="eb616-125">次のコマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb616-125">Use the following cmdlets:</span></span>  
  
     `Test-SqlAvailabilityGroup`  
     <span data-ttu-id="eb616-126">SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性グループの正常性を査定します。</span><span class="sxs-lookup"><span data-stu-id="eb616-126">Assesses the health of an availability group by evaluating SQL Server policy based management (PBM) policies.</span></span> <span data-ttu-id="eb616-127">このコマンドレットを実行するには、CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eb616-127">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.</span></span>  
  
     <span data-ttu-id="eb616-128">たとえば、次のコマンドでは、サーバー インスタンス `Computer\Instance`上で正常性状態が "Error" の可用性グループすべてを表示します。</span><span class="sxs-lookup"><span data-stu-id="eb616-128">For example, the following command shows all availability groups with a health state of "Error" on the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups |
        Test-SqlAvailabilityGroup |
        Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     <span data-ttu-id="eb616-129">SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性レプリカの正常性を査定します。</span><span class="sxs-lookup"><span data-stu-id="eb616-129">Assesses the health of availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span> <span data-ttu-id="eb616-130">このコマンドレットを実行するには、CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eb616-130">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.</span></span>  
  
     <span data-ttu-id="eb616-131">たとえば、次のコマンドは、可用性グループ `MyReplica` 内の `MyAg` という名前の可用性レプリカの正常性を評価し、概要を出力します。</span><span class="sxs-lookup"><span data-stu-id="eb616-131">For example, the following command evaluates the health of the availability replica named `MyReplica` in the availability group `MyAg` and outputs a brief summary.</span></span>  
  
    ```powershell
    Test-SqlAvailabilityReplica -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     <span data-ttu-id="eb616-132">SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、参加しているすべての可用性レプリカ上の可用性データベースの正常性を査定します。</span><span class="sxs-lookup"><span data-stu-id="eb616-132">Assesses the health of an availability database on all joined availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span>  
  
     <span data-ttu-id="eb616-133">たとえば、次のコマンドは、可用性グループ `MyAg` 内のすべての可用性データベースの正常性を評価し、各データベースの概要を出力します。</span><span class="sxs-lookup"><span data-stu-id="eb616-133">For example, the following command evaluates the health of all availability databases in the availability group `MyAg` and outputs a brief summary for each database.</span></span>  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates |
        Test-SqlDatabaseReplicaState  
    ```  
  
     <span data-ttu-id="eb616-134">これらのコマンドレットでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb616-134">These cmdlets accept the following options:</span></span>  
  
    |<span data-ttu-id="eb616-135">オプション</span><span class="sxs-lookup"><span data-stu-id="eb616-135">Option</span></span>|<span data-ttu-id="eb616-136">[説明]</span><span class="sxs-lookup"><span data-stu-id="eb616-136">Description</span></span>|  
    |------------|-----------------|  
    |`AllowUserPolicies`|<span data-ttu-id="eb616-137">AlwaysOn ポリシーのカテゴリにあるユーザー ポリシーを実行します。</span><span class="sxs-lookup"><span data-stu-id="eb616-137">Runs user policies found in the AlwaysOn policy categories.</span></span>|  
    |`InputObject`|<span data-ttu-id="eb616-138">可用性グループ、可用性レプリカ、または可用性データベースの状態 (使用するコマンドレットに応じて異なります) を表すオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="eb616-138">A collection of objects that, represent availability groups, availability replicas, or availability database states (depending on which cmdlet you are using).</span></span> <span data-ttu-id="eb616-139">コマンドレットを実行すると、指定されたオブジェクトの正常性が計算されます。</span><span class="sxs-lookup"><span data-stu-id="eb616-139">The cmdlet will compute the health of the specified objects.</span></span>|  
    |`NoRefresh`|<span data-ttu-id="eb616-140">このパラメーターを設定すると、コマンドレットの実行時に、`-Path` または `-InputObject` パラメーターで指定されたオブジェクトが手動で最新の情報に更新されません。</span><span class="sxs-lookup"><span data-stu-id="eb616-140">When this parameter is set, the cmdlet will not manually refresh the objects specified by the `-Path` or `-InputObject` parameter.</span></span>|  
    |`Path`|<span data-ttu-id="eb616-141">可用性グループ、1 つ以上の可用性レプリカ、または可用性データベースのデータベース レプリカ クラスターの状態へのパス (使用するコマンドレットに応じて異なります) です。</span><span class="sxs-lookup"><span data-stu-id="eb616-141">The path to the availability group, one or more availability replicas, or database replica cluster state of the availability database (depending on which cmdlet you are using).</span></span> <span data-ttu-id="eb616-142">これは省略可能なパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="eb616-142">This is an optional parameter.</span></span> <span data-ttu-id="eb616-143">このパラメーターの値を指定しない場合、既定では、現在の場所に設定されます。</span><span class="sxs-lookup"><span data-stu-id="eb616-143">If not specified, the value of this parameter defaults to the current working location.</span></span>|  
    |`ShowPolicyDetails`|<span data-ttu-id="eb616-144">このコマンドレットで実行された各ポリシー評価の結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="eb616-144">Shows the result of each policy evaluation performed by this cmdlet.</span></span> <span data-ttu-id="eb616-145">コマンドレットを実行すると、ポリシー評価ごとに 1 つのオブジェクトが出力されます。このオブジェクトには評価の結果を表すフィールド (ポリシーが渡されるかどうかに関係なく、ポリシー名、カテゴリなど) があります。</span><span class="sxs-lookup"><span data-stu-id="eb616-145">The cmdlet outputs one object per policy evaluation, and this object has fields describing the results of evaluation (whether the policy passed or not, the policy name and category, and so forth).</span></span>|  
  
     <span data-ttu-id="eb616-146">たとえば、次の `Test-SqlAvailabilityGroup` コマンドは、`-ShowPolicyDetails` パラメーターを指定して、可用性グループ `MyAg` 上で実行されたポリシー ベースの管理 (PBM) のポリシーごとに、このコマンドレットによって実行されたそれぞれのポリシー評価の結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="eb616-146">For example, the following `Test-SqlAvailabilityGroup` command specifies the `-ShowPolicyDetails` parameter to show the result of each policy evaluation performed by this cmdlet for each policy-based management (PBM) policy that was executed on the availability group named `MyAg`.</span></span>  
  
    ```powershell
    Test-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName -ShowPolicyDetails  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb616-147">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb616-147">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="eb616-148">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb616-148">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="eb616-149">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="eb616-149">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="eb616-150">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="eb616-150">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="eb616-151">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb616-151">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="eb616-152">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="eb616-152">Related Content</span></span>  
 <span data-ttu-id="eb616-153">**AlwaysOn チームのブログの SQL Server: PowerShell を使用した AlwaysOn 正常性状態の監視:**</span><span class="sxs-lookup"><span data-stu-id="eb616-153">**SQL Server AlwaysOn Team Blogs-Monitoring AlwaysOn Health with PowerShell:**</span></span>  
  
-   [<span data-ttu-id="eb616-154">パート 1: 基本的なコマンドレットの概要</span><span class="sxs-lookup"><span data-stu-id="eb616-154">Part 1: Basic Cmdlet Overview</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
-   [<span data-ttu-id="eb616-155">パート 2: 高度なコマンドレットの使用方法</span><span class="sxs-lookup"><span data-stu-id="eb616-155">Part 2: Advanced Cmdlet Usage</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
-   [<span data-ttu-id="eb616-156">パート 3: 単純な監視アプリケーション</span><span class="sxs-lookup"><span data-stu-id="eb616-156">Part 3: A Simple Monitoring Application</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-3-a-simple-monitoring-application)  
  
-   [<span data-ttu-id="eb616-157">パート 4: SQL Server エージェントの統合</span><span class="sxs-lookup"><span data-stu-id="eb616-157">Part 4: Integration with SQL Server Agent</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-4-integration-with-sql-server-agent)  
  
## <a name="see-also"></a><span data-ttu-id="eb616-158">参照</span><span class="sxs-lookup"><span data-stu-id="eb616-158">See Also</span></span>  
 <span data-ttu-id="eb616-159">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eb616-159">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="eb616-160">[可用性グループ &#40;SQL Server の管理&#41;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eb616-160">[Administration of an Availability Group &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="eb616-161">[可用性グループの監視 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eb616-161">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="eb616-162">AlwaysOn 可用性グループでの運用上の問題のポリシー ベースの管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eb616-162">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-policies-for-operational-issues-always-on-availability.md) 
