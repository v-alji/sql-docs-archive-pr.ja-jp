---
title: 自動フェールオーバーの条件を制御する柔軟なフェールオーバーポリシーの構成 (Always On 可用性グループ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c938624a3ed39fe2d41f21a21af5231aa76a8c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740506"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a><span data-ttu-id="371dd-102">自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 (AlwaysOn 可用性グループ)</span><span class="sxs-lookup"><span data-stu-id="371dd-102">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (Always On Availability Groups)</span></span>
  <span data-ttu-id="371dd-103">このトピックでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] で [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]または PowerShell を使用して AlwaysOn 可用性グループの柔軟なフェールオーバー ポリシーを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="371dd-103">This topic describes how to configure the flexible failover policy for an AlwaysOn availability group by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="371dd-104">柔軟なフェールオーバー ポリシーを使用すると、可用性グループの自動フェールオーバーを実行する条件をきめ細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="371dd-104">A flexible failover policy provides granular control over the conditions that cause automatic failover for an availability group.</span></span> <span data-ttu-id="371dd-105">自動フェールオーバーを実行するエラー条件および正常性チェックの頻度を変更することで、自動フェールオーバーの確率値を増減して高可用性の SLA をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="371dd-105">By changing the failure conditions that trigger an automatic failover and the frequency of health checks, you can increase or decrease the likelihood of an automatic failover to support your SLA for high availability.</span></span>  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="371dd-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="371dd-106">Before You Begin</span></span>  
  
###  <a name="limitations-on-automatic-failovers"></a><a name="Limitations"></a> <span data-ttu-id="371dd-107">自動フェールオーバーの制限</span><span class="sxs-lookup"><span data-stu-id="371dd-107">Limitations on Automatic Failovers</span></span>  
  
-   <span data-ttu-id="371dd-108">自動フェールオーバーが行われるには、現在のプライマリ レプリカおよび 1 つのセカンダリ レプリカが自動フェールオーバーを使用する同期コミット可用性モード用に構成され、セカンダリ レプリカがプライマリ レプリカと同期している必要があります。</span><span class="sxs-lookup"><span data-stu-id="371dd-108">For an automatic failover to occur, the current primary replica and one secondary replica must be configured for synchronous-commit availability mode with automatic failover and the secondary replica must be synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="371dd-109">WSFC クラスターでは、可用性グループが WSFC のエラーしきい値を超えると、自動フェールオーバーはその可用性グループに対して実行されません。</span><span class="sxs-lookup"><span data-stu-id="371dd-109">If an availability group exceeds its WSFC failure threshold, the WSFC cluster will not attempt an automatic failover for the availability group.</span></span> <span data-ttu-id="371dd-110">また、クラスター管理者が失敗したリソース グループを手動でオンラインにするか、データベース管理者が可用性グループの手動フェールオーバーを実行するまで、可用性グループの WSFC リソース グループはエラー状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="371dd-110">Furthermore, the WSFC resource group of the availability group remains in a failed state until either the cluster administrator manually brings the failed resource group online or the database administrator performs a manual failover of the availability group.</span></span> <span data-ttu-id="371dd-111">*WSFC のエラーしきい値* は、特定の期間に可用性グループに対して許容されるエラーの最大数として定義されています。</span><span class="sxs-lookup"><span data-stu-id="371dd-111">The *WSFC failure threshold* is defined as the maximum number of failures supported for the availability group during a given time period.</span></span> <span data-ttu-id="371dd-112">既定の期間は 6 時間であり、この期間のエラーの最大数の既定値は *n*-1 です ( *n* は WSFC ノードの数です)。</span><span class="sxs-lookup"><span data-stu-id="371dd-112">The default time period is six hours, and the default value for the maximum number of failures during this period is *n*-1, where *n* is the number of WSFC nodes.</span></span> <span data-ttu-id="371dd-113">特定の可用性グループのエラーしきい値を変更するには、WSFC フェールオーバー マネージャー コンソールを使用します。</span><span class="sxs-lookup"><span data-stu-id="371dd-113">To change the failure-threshold values for a given availability group, use the WSFC Failover Manager Console.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="371dd-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="371dd-114">Prerequisites</span></span>  
  
-   <span data-ttu-id="371dd-115">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="371dd-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="371dd-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="371dd-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="371dd-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="371dd-117">Permissions</span></span>  
  
|<span data-ttu-id="371dd-118">タスク</span><span class="sxs-lookup"><span data-stu-id="371dd-118">Task</span></span>|<span data-ttu-id="371dd-119">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="371dd-119">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="371dd-120">新しい可用性グループの柔軟なフェールオーバー ポリシーを構成する</span><span class="sxs-lookup"><span data-stu-id="371dd-120">To configure the flexible failover policy for a new availability group</span></span>|<span data-ttu-id="371dd-121">**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="371dd-121">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="371dd-122">既存の可用性グループのポリシーを変更する</span><span class="sxs-lookup"><span data-stu-id="371dd-122">To modify the policy of an existing availability group</span></span>|<span data-ttu-id="371dd-123">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="371dd-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="371dd-124">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="371dd-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="371dd-125">**柔軟なフェールオーバー ポリシーを構成するには**</span><span class="sxs-lookup"><span data-stu-id="371dd-125">**To configure the flexible failover policy**</span></span>  
  
1.  <span data-ttu-id="371dd-126">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="371dd-126">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="371dd-127">新しい可用性グループの場合は、 [CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql)ステートメントを使用し [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="371dd-127">For a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="371dd-128">既存の可用性グループを変更する場合は、 [ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql)ステートメントを使用し [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="371dd-128">If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="371dd-129">フェールオーバーの条件レベルを設定するには、FAILURE_CONDITION_LEVEL = *n* オプションを使用します。ここで、 *n* は 1 ～ 5 の整数です。</span><span class="sxs-lookup"><span data-stu-id="371dd-129">To set the failover condition level, use the FAILURE_CONDITION_LEVEL = *n* option, where, *n* is an integer from 1 to 5.</span></span>  
  
         <span data-ttu-id="371dd-130">たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、既存の可用性グループ `AG1`のエラー条件レベルをレベル 1 に変更します。</span><span class="sxs-lookup"><span data-stu-id="371dd-130">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement changes the failure-condition level of an existing availability group, `AG1`, to level one:</span></span>  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         <span data-ttu-id="371dd-131">これらの整数値とエラー条件レベルの関係は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="371dd-131">The relationship of these integer values to the failure condition levels is as follows:</span></span>  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="371dd-132">値</span><span class="sxs-lookup"><span data-stu-id="371dd-132">Value</span></span>|<span data-ttu-id="371dd-133">Level</span><span class="sxs-lookup"><span data-stu-id="371dd-133">Level</span></span>|<span data-ttu-id="371dd-134">自動フェールオーバーが開始される条件</span><span class="sxs-lookup"><span data-stu-id="371dd-134">Automatic Is Failover Initiated When...</span></span>|  
        |------------------------------|-----------|-------------------------------------------|  
        |<span data-ttu-id="371dd-135">1</span><span class="sxs-lookup"><span data-stu-id="371dd-135">1</span></span>|<span data-ttu-id="371dd-136">1 つ</span><span class="sxs-lookup"><span data-stu-id="371dd-136">One</span></span>|<span data-ttu-id="371dd-137">サーバーの停止。</span><span class="sxs-lookup"><span data-stu-id="371dd-137">On server down.</span></span> <span data-ttu-id="371dd-138">フェールオーバーまたは再起動のため、SQL Server サービスが停止した場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-138">The SQL Server service stops because of a failover or restart.</span></span>|  
        |<span data-ttu-id="371dd-139">2</span><span class="sxs-lookup"><span data-stu-id="371dd-139">2</span></span>|<span data-ttu-id="371dd-140">2 つ</span><span class="sxs-lookup"><span data-stu-id="371dd-140">Two</span></span>|<span data-ttu-id="371dd-141">サーバーの応答停止。</span><span class="sxs-lookup"><span data-stu-id="371dd-141">On server unresponsive.</span></span> <span data-ttu-id="371dd-142">下限値の任意の条件が満たされた場合、SQL Server サービスがクラスターに接続され正常性チェックのタイムアウトしきい値を超えた場合、または現在のプライマリ レプリカがエラー状態になった場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-142">Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.</span></span>|  
        |<span data-ttu-id="371dd-143">3</span><span class="sxs-lookup"><span data-stu-id="371dd-143">3</span></span>|<span data-ttu-id="371dd-144">3</span><span class="sxs-lookup"><span data-stu-id="371dd-144">Three</span></span>|<span data-ttu-id="371dd-145">重大なサーバー エラー。</span><span class="sxs-lookup"><span data-stu-id="371dd-145">On critical server error.</span></span> <span data-ttu-id="371dd-146">下限値の任意の条件が満たされるか、重大な内部サーバー エラーが発生した場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-146">Any condition of lower value is satisfied or an internal critical server error occurs.</span></span><br /><br /> <span data-ttu-id="371dd-147">これは既定のレベルです。</span><span class="sxs-lookup"><span data-stu-id="371dd-147">This is the default level.</span></span>|  
        |<span data-ttu-id="371dd-148">4</span><span class="sxs-lookup"><span data-stu-id="371dd-148">4</span></span>|<span data-ttu-id="371dd-149">4</span><span class="sxs-lookup"><span data-stu-id="371dd-149">Four</span></span>|<span data-ttu-id="371dd-150">中程度のサーバー エラー。</span><span class="sxs-lookup"><span data-stu-id="371dd-150">On moderate server error.</span></span> <span data-ttu-id="371dd-151">下限値の任意の条件が満たされるか、中程度のサーバー エラーが発生した場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-151">Any condition of lower value is satisfied or a moderate Server error occurs.</span></span>|  
        |<span data-ttu-id="371dd-152">5</span><span class="sxs-lookup"><span data-stu-id="371dd-152">5</span></span>|<span data-ttu-id="371dd-153">5</span><span class="sxs-lookup"><span data-stu-id="371dd-153">Five</span></span>|<span data-ttu-id="371dd-154">任意の限定されたエラー条件。</span><span class="sxs-lookup"><span data-stu-id="371dd-154">On any qualified failure conditions.</span></span> <span data-ttu-id="371dd-155">下限値の任意の条件が満たされるか、限定されたエラー条件が発生した場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-155">Any condition of lower value is satisfied or a qualifying failure condition occurs.</span></span>|  
  
         <span data-ttu-id="371dd-156">詳細については、「[可用性グループの自動フェールオーバーのための柔軟なフェールオーバー ポリシー &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="371dd-156">For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).</span></span>  
  
    -   <span data-ttu-id="371dd-157">正常性チェックのタイムアウトしきい値を構成するには、HEALTH_CHECK_TIMEOUT = *n* オプションを使用します。ここで *n* は 15000 ミリ秒 (15 秒) ～ 4294967295 ミリ秒の整数です。</span><span class="sxs-lookup"><span data-stu-id="371dd-157">To configure the health check timeout threshold, use the HEALTH_CHECK_TIMEOUT = *n* option, where, *n* is an integer from 15000 milliseconds (15 seconds) to 4294967295 milliseconds.</span></span> <span data-ttu-id="371dd-158">既定値は 30000 ミリ秒 (30 秒) です。</span><span class="sxs-lookup"><span data-stu-id="371dd-158">The default value is 30000 milliseconds (30 seconds)</span></span>  
  
         <span data-ttu-id="371dd-159">たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、既存の可用性グループ `AG1`の正常性チェックのタイムアウトしきい値が  60,000 ミリ秒 (1 分) に変更されます。</span><span class="sxs-lookup"><span data-stu-id="371dd-159">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement changes the health-check timeout threshold of an existing availability group, `AG1`, to 60,000 milliseconds (one minute).</span></span>  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="371dd-160">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="371dd-160">Using PowerShell</span></span>  

### <a name="to-configure-the-flexible-failover-policy"></a><span data-ttu-id="371dd-161">柔軟なフェールオーバーポリシーを構成するには \* \*</span><span class="sxs-lookup"><span data-stu-id="371dd-161">To configure the flexible failover policy\*\*</span></span>  
  
1.  <span data-ttu-id="371dd-162">既定 (`cd`) を、プライマリ レプリカをホストするサーバー インスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="371dd-162">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="371dd-163">可用性グループに可用性レプリカを追加する場合は、`New-SqlAvailabilityGroup` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="371dd-163">When adding an availability replica to an availability group, use the `New-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="371dd-164">既存の可用性レプリカを変更する場合は、`Set-SqlAvailabilityGroup` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="371dd-164">When modifying an existing availability replica, use the `Set-SqlAvailabilityGroup` cmdlet.</span></span>  
  
    -   <span data-ttu-id="371dd-165">フェールオーバーの条件レベルを設定するには、 `FailureConditionLevel` *level*パラメーターを使用します。ここで、 *level*は次の値のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="371dd-165">To set the failover condition level, use the `FailureConditionLevel`*level* parameter, where, *level* is one of the following values:</span></span>  
  
        |<span data-ttu-id="371dd-166">値</span><span class="sxs-lookup"><span data-stu-id="371dd-166">Value</span></span>|<span data-ttu-id="371dd-167">Level</span><span class="sxs-lookup"><span data-stu-id="371dd-167">Level</span></span>|<span data-ttu-id="371dd-168">自動フェールオーバーが開始される条件</span><span class="sxs-lookup"><span data-stu-id="371dd-168">Automatic Is Failover Initiated When...</span></span>|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|<span data-ttu-id="371dd-169">1 つ</span><span class="sxs-lookup"><span data-stu-id="371dd-169">One</span></span>|<span data-ttu-id="371dd-170">サーバーの停止。</span><span class="sxs-lookup"><span data-stu-id="371dd-170">On server down.</span></span> <span data-ttu-id="371dd-171">フェールオーバーまたは再起動のため、SQL Server サービスが停止した場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-171">The SQL Server service stops because of a failover or restart.</span></span>|  
        |`OnServerUnresponsive`|<span data-ttu-id="371dd-172">2 つ</span><span class="sxs-lookup"><span data-stu-id="371dd-172">Two</span></span>|<span data-ttu-id="371dd-173">サーバーの応答停止。</span><span class="sxs-lookup"><span data-stu-id="371dd-173">On server unresponsive.</span></span> <span data-ttu-id="371dd-174">下限値の任意の条件が満たされた場合、SQL Server サービスがクラスターに接続され正常性チェックのタイムアウトしきい値を超えた場合、または現在のプライマリ レプリカがエラー状態になった場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-174">Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.</span></span>|  
        |`OnCriticalServerError`|<span data-ttu-id="371dd-175">3</span><span class="sxs-lookup"><span data-stu-id="371dd-175">Three</span></span>|<span data-ttu-id="371dd-176">重大なサーバー エラー。</span><span class="sxs-lookup"><span data-stu-id="371dd-176">On critical server error.</span></span> <span data-ttu-id="371dd-177">下限値の任意の条件が満たされるか、重大な内部サーバー エラーが発生した場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-177">Any condition of lower value is satisfied or an internal critical server error occurs.</span></span><br /><br /> <span data-ttu-id="371dd-178">これは既定のレベルです。</span><span class="sxs-lookup"><span data-stu-id="371dd-178">This is the default level.</span></span>|  
        |`OnModerateServerError`|<span data-ttu-id="371dd-179">4</span><span class="sxs-lookup"><span data-stu-id="371dd-179">Four</span></span>|<span data-ttu-id="371dd-180">中程度のサーバー エラー。</span><span class="sxs-lookup"><span data-stu-id="371dd-180">On moderate server error.</span></span> <span data-ttu-id="371dd-181">下限値の任意の条件が満たされるか、中程度のサーバー エラーが発生した場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-181">Any condition of lower value is satisfied or a moderate Server error occurs.</span></span>|  
        |`OnAnyQualifiedFailureConditions`|<span data-ttu-id="371dd-182">5</span><span class="sxs-lookup"><span data-stu-id="371dd-182">Five</span></span>|<span data-ttu-id="371dd-183">任意の限定されたエラー条件。</span><span class="sxs-lookup"><span data-stu-id="371dd-183">On any qualified failure conditions.</span></span> <span data-ttu-id="371dd-184">下限値の任意の条件が満たされるか、限定されたエラー条件が発生した場合。</span><span class="sxs-lookup"><span data-stu-id="371dd-184">Any condition of lower value is satisfied or a qualifying failure condition occurs.</span></span>|  
  
         <span data-ttu-id="371dd-185">詳細については、「[可用性グループの自動フェールオーバーのための柔軟なフェールオーバー ポリシー &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="371dd-185">For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).</span></span>  
  
         <span data-ttu-id="371dd-186">たとえば、次のコマンドでは、既存の可用性グループ `AG1`のエラー条件レベルをレベル 1 に変更します。</span><span class="sxs-lookup"><span data-stu-id="371dd-186">For example, the following command changes the failure-condition level of an existing availability group, `AG1`, to level one.</span></span>  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `
         -FailureConditionLevel OnServerDown  
        ```  
  
    -   <span data-ttu-id="371dd-187">正常性チェックのタイムアウトしきい値を設定するには、 `HealthCheckTimeout` *n*パラメーターを使用します。ここで、 *n*は15000ミリ秒 (15 秒) ~ 4294967295 ミリ秒の整数です。</span><span class="sxs-lookup"><span data-stu-id="371dd-187">To set the health check timeout threshold, use the `HealthCheckTimeout`*n* parameter, where, *n* is an integer from 15000 milliseconds (15 seconds) to 4294967295 milliseconds.</span></span> <span data-ttu-id="371dd-188">既定値は 30000 ミリ秒 (30 秒) です。</span><span class="sxs-lookup"><span data-stu-id="371dd-188">The default value is 30000 milliseconds (30 seconds).</span></span>  
  
         <span data-ttu-id="371dd-189">たとえば、次のコマンドでは、既存の可用性グループ `AG1`の正常性チェックのタイムアウトしきい値が 120,000 ミリ秒 (2 分) に変更されます。</span><span class="sxs-lookup"><span data-stu-id="371dd-189">For example, the following command changes the health-check timeout threshold of an existing availability group, `AG1`, to 120,000 milliseconds (two minutes).</span></span>  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `
         -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  <span data-ttu-id="371dd-190">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="371dd-190">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="371dd-191">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="371dd-191">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="371dd-192">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="371dd-192">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="371dd-193">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="371dd-193">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="371dd-194">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="371dd-194">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a><span data-ttu-id="371dd-195">参照</span><span class="sxs-lookup"><span data-stu-id="371dd-195">See Also</span></span>  
 <span data-ttu-id="371dd-196">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="371dd-196">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="371dd-197">[可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="371dd-197">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="371dd-198">[フェールオーバーとフェールオーバーモード &#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="371dd-198">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="371dd-199">[Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="371dd-199">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 <span data-ttu-id="371dd-200">[フェールオーバー クラスター インスタンスのフェールオーバー ポリシー](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) </span><span class="sxs-lookup"><span data-stu-id="371dd-200">[Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) </span></span>  
 [<span data-ttu-id="371dd-201">sp_server_diagnostics &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="371dd-201">sp_server_diagnostics &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
