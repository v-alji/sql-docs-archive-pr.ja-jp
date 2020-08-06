---
title: cost threshold for parallelism サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cost threshold for parallelism option
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 675055a753e84ace3a4fcb44b41b8c914326c5c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632701"
---
# <a name="configure-the-cost-threshold-for-parallelism-server-configuration-option"></a><span data-ttu-id="009f9-102">cost threshold for parallelism サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="009f9-102">Configure the cost threshold for parallelism Server Configuration Option</span></span>
  <span data-ttu-id="009f9-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] cost threshold for parallelism [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="009f9-103">This topic describes how to configure the **cost threshold for parallelism** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="009f9-104">**cost threshold for parallelism** オプションによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がクエリの並列プランを作成および実行するしきい値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="009f9-104">The **cost threshold for parallelism** option specifies the threshold at which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates and runs parallel plans for queries.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="009f9-105">によって、クエリの並列プランが作成および実行されるのは、同じクエリの直列プランを実行するための推定コストが **cost threshold for parallelism**に設定されている値を超える場合のみです。</span><span class="sxs-lookup"><span data-stu-id="009f9-105">creates and runs a parallel plan for a query only when the estimated cost to run a serial plan for the same query is higher than the value set in **cost threshold for parallelism**.</span></span> <span data-ttu-id="009f9-106">コストとは、特定のハードウェア構成で、直列プランを実行するための予想所要時間を秒単位で表したものです。</span><span class="sxs-lookup"><span data-stu-id="009f9-106">The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration.</span></span> <span data-ttu-id="009f9-107">**cost threshold for parallelism** オプションには、0 ～ 32,767 の範囲の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="009f9-107">The **cost threshold for parallelism** option can be set to any value from 0 through 32767.</span></span> <span data-ttu-id="009f9-108">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="009f9-108">The default value is 5.</span></span>  
  
 <span data-ttu-id="009f9-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="009f9-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="009f9-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="009f9-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="009f9-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="009f9-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="009f9-112">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="009f9-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="009f9-113">Security</span><span class="sxs-lookup"><span data-stu-id="009f9-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="009f9-114">**以下を使用して cost threshold for parallelism オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="009f9-114">**To configure the cost threshold for parallelism option, using:**</span></span>  
  
     [<span data-ttu-id="009f9-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="009f9-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="009f9-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="009f9-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="009f9-117">**補足情報:** [cost threshold for parallelism オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="009f9-117">**Follow Up:**  [After you configure the cost threshold for parallelism option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="009f9-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="009f9-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="009f9-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="009f9-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="009f9-120">コストとは、特定のハードウェア構成で、直列プランを実行するための予想所要時間を秒単位で表したものです。</span><span class="sxs-lookup"><span data-stu-id="009f9-120">The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration.</span></span> <span data-ttu-id="009f9-121">**cost threshold for parallelism** は、SMP (symmetric multiprocessor) 環境でのみ設定します。</span><span class="sxs-lookup"><span data-stu-id="009f9-121">Only set **cost threshold for parallelism** on symmetric multiprocessors.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="009f9-122">では **または** の値が無視されます。</span><span class="sxs-lookup"><span data-stu-id="009f9-122">ignores the **cost threshold for parallelism** value under the following conditions:</span></span>  
  
    -   <span data-ttu-id="009f9-123">使用しているコンピューターに論理プロセッサが 1 つしか搭載されていない場合。</span><span class="sxs-lookup"><span data-stu-id="009f9-123">Your computer has only one logical processor.</span></span>  
  
    -   <span data-ttu-id="009f9-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 関係マスク **構成オプションの設定により、** で 1 つの論理プロセッサしか使用できない場合。</span><span class="sxs-lookup"><span data-stu-id="009f9-124">Only a single logical processor is available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because of the **affinity mask** configuration option.</span></span>  
  
    -   <span data-ttu-id="009f9-125">**max degree of parallelism** オプションが 1 に設定されている場合。</span><span class="sxs-lookup"><span data-stu-id="009f9-125">The **max degree of parallelism** option is set to 1.</span></span>  
  
 <span data-ttu-id="009f9-126">論理プロセッサは、オペレーティング システムでのタスクのディスパッチまたはスレッド コンテキストの実行を可能にするプロセッサ ハードウェアの基本単位です。</span><span class="sxs-lookup"><span data-stu-id="009f9-126">A logical processor is the basic unit of processor hardware that allows the operating system to dispatch a task or execute a thread context.</span></span> <span data-ttu-id="009f9-127">各論理プロセッサは一度に 1 つのスレッド コンテキストのみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="009f9-127">Each logical processor can execute only one thread context at a time.</span></span> <span data-ttu-id="009f9-128">プロセッサのコアは、命令をデコードして実行する能力を提供する回路です。</span><span class="sxs-lookup"><span data-stu-id="009f9-128">The processor core is the circuitry that provides ability to decode and execute instructions.</span></span> <span data-ttu-id="009f9-129">プロセッサのコアには 1 つ以上の論理プロセッサが含まれます。</span><span class="sxs-lookup"><span data-stu-id="009f9-129">A processor core may contain one or more logical processors.</span></span> <span data-ttu-id="009f9-130">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリは、システムの CPU 情報の取得に使用できます。</span><span class="sxs-lookup"><span data-stu-id="009f9-130">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] query can be used for obtaining CPU information for the system.</span></span>  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="009f9-131">推奨事項</span><span class="sxs-lookup"><span data-stu-id="009f9-131">Recommendations</span></span>  
  
-   <span data-ttu-id="009f9-132">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="009f9-132">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="009f9-133">クエリのコスト プランが **cost threshold for parallelism** の現在の値より小さくても、並列プランが選択されることがあります。</span><span class="sxs-lookup"><span data-stu-id="009f9-133">In certain cases, a parallel plan may be chosen even though the query's cost plan is less than the current **cost threshold for parallelism** value.</span></span> <span data-ttu-id="009f9-134">並列プランまたは直列プランのどちらを使用するかが、完全な最適化が完了する前に算出されたコストの推定値に基づいて決定された場合に、このようなことが起こります。</span><span class="sxs-lookup"><span data-stu-id="009f9-134">This can happen because the decision to use a parallel or serial plan is based on a cost estimate provided before the full optimization is complete.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="009f9-135">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="009f9-135">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="009f9-136">Permissions</span><span class="sxs-lookup"><span data-stu-id="009f9-136">Permissions</span></span>  
 <span data-ttu-id="009f9-137">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="009f9-137">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="009f9-138">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="009f9-138">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="009f9-139">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="009f9-139">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="009f9-140">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="009f9-140">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a><span data-ttu-id="009f9-141">cost threshold for parallelism オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="009f9-141">To configure the cost threshold for parallelism option</span></span>  
  
1.  <span data-ttu-id="009f9-142">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="009f9-142">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="009f9-143">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="009f9-143">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="009f9-144">**[並列処理]** で、 **[CostThresholdForParallelism]** オプションを目的の値に変更します。</span><span class="sxs-lookup"><span data-stu-id="009f9-144">Under **Parallelism**, change the **CostThresholdForParallelism** option to the value you want.</span></span> <span data-ttu-id="009f9-145">0 ～ 32767 の値を、入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="009f9-145">Type or select a value from 0 to 32767.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="009f9-146">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="009f9-146">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a><span data-ttu-id="009f9-147">cost threshold for parallelism オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="009f9-147">To configure the cost threshold for parallelism option</span></span>  
  
1.  <span data-ttu-id="009f9-148">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="009f9-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="009f9-149">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="009f9-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="009f9-150">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="009f9-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="009f9-151">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `cost threshold for parallelism` オプションの値を `10`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="009f9-151">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `cost threshold for parallelism` option to `10`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="009f9-152">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="009f9-152">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-cost-threshold-for-parallelism-option"></a><a name="FollowUp"></a><span data-ttu-id="009f9-153">補足情報: cost threshold for parallelism オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="009f9-153">Follow Up: After you configure the cost threshold for parallelism option</span></span>  
 <span data-ttu-id="009f9-154">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="009f9-154">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009f9-155">参照</span><span class="sxs-lookup"><span data-stu-id="009f9-155">See Also</span></span>  
 <span data-ttu-id="009f9-156">[並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="009f9-156">[Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md) </span></span>  
 <span data-ttu-id="009f9-157">[クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="009f9-157">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 <span data-ttu-id="009f9-158">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="009f9-158">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="009f9-159">[affinity mask サーバー構成オプション](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="009f9-159">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="009f9-160">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="009f9-160">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="009f9-161">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="009f9-161">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="009f9-162">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="009f9-162">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
