---
title: max worker threads サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- worker threads [SQL Server]
- max worker threads option
ms.assetid: abeadfa4-a14d-469a-bacf-75812e48fac1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4881cefee350d34d93b539c56be6f43866d3ddfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642306"
---
# <a name="configure-the-max-worker-threads-server-configuration-option"></a><span data-ttu-id="87ac7-102">max worker threads サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="87ac7-102">Configure the max worker threads Server Configuration Option</span></span>
  <span data-ttu-id="87ac7-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] max worker threads [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-103">This topic describes how to configure the **max worker threads** server configuration option in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="87ac7-104">**max worker threads** オプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスで利用できるワーカー スレッド数を構成します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-104">The **max worker threads** option configures the number of worker threads that are available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="87ac7-105">では、オペレーティング システムのネイティブ スレッド サービスを使用しているため、1 つ以上のスレッドが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で同時にサポートされている各ネットワークをサポートし、他のスレッドがデータベース チェックポイントを処理し、スレッド プールがすべてのユーザーを処理します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-105">uses the native thread services of the operating systems so that one or more threads support each network that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports simultaneously, another thread handles database checkpoints, and a pool of threads handles all users.</span></span> <span data-ttu-id="87ac7-106">**max worker threads** の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="87ac7-106">The default value for **max worker threads** is 0.</span></span> <span data-ttu-id="87ac7-107">この場合、ワーカー スレッドの数が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって起動時に自動で構成されます。</span><span class="sxs-lookup"><span data-stu-id="87ac7-107">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to automatically configure the number of worker threads at startup.</span></span> <span data-ttu-id="87ac7-108">既定の設定は、ほとんどのシステムで最適な設定です。</span><span class="sxs-lookup"><span data-stu-id="87ac7-108">The default setting is best for most systems.</span></span> <span data-ttu-id="87ac7-109">ただし、システム構成によっては、 **max worker threads** を特定の値に設定するとパフォーマンスが向上することがあります。</span><span class="sxs-lookup"><span data-stu-id="87ac7-109">However, depending on your system configuration, setting **max worker threads** to a specific value sometimes improves performance.</span></span>  
  
 <span data-ttu-id="87ac7-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="87ac7-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="87ac7-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="87ac7-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="87ac7-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="87ac7-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="87ac7-113">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="87ac7-113">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="87ac7-114">Security</span><span class="sxs-lookup"><span data-stu-id="87ac7-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="87ac7-115">**以下を使用して max worker threads オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="87ac7-115">**To configure the max worker threads option, using:**</span></span>  
  
     [<span data-ttu-id="87ac7-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="87ac7-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="87ac7-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87ac7-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="87ac7-118">**補足情報:** [max worker threads オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="87ac7-118">**Follow Up:**  [After you configure the max worker threads option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="87ac7-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="87ac7-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="87ac7-120">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="87ac7-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="87ac7-121">実際のクエリ要求数が **max worker threads**に設定した値を下回る場合、1 つのスレッドで 1 つのクエリ要求が処理されます。</span><span class="sxs-lookup"><span data-stu-id="87ac7-121">When the actual number of query requests is less than the amount set in **max worker threads**, one thread handles each query request.</span></span> <span data-ttu-id="87ac7-122">ただし、実際のクエリ要求数が**max worker threads**で設定されている量を超えた場合、はワーカースレッドをプールして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 次に使用可能なワーカースレッドが要求を処理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="87ac7-122">However, if the actual number of query request exceeds the amount set in **max worker threads**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pools the worker threads so that the next available worker thread can handle the request.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="87ac7-123">推奨事項</span><span class="sxs-lookup"><span data-stu-id="87ac7-123">Recommendations</span></span>  
  
-   <span data-ttu-id="87ac7-124">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="87ac7-124">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="87ac7-125">スレッド プールは、多数のクライアントがサーバーに接続されている場合のパフォーマンスの最適化に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="87ac7-125">Thread pooling helps optimize performance when large numbers of clients are connected to the server.</span></span> <span data-ttu-id="87ac7-126">通常、クエリ要求ごとに個別のオペレーティング システム スレッドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="87ac7-126">Usually, a separate operating system thread is created for each query request.</span></span> <span data-ttu-id="87ac7-127">ただし、サーバーへの接続が数百にもなる場合、クエリ要求ごとに 1 つのスレッドを使用すると大量のシステム リソースが消費されることがあります。</span><span class="sxs-lookup"><span data-stu-id="87ac7-127">However, with hundreds of connections to the server, using one thread per query request can consume large amounts of system resources.</span></span> <span data-ttu-id="87ac7-128">**max worker threads** オプションを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってワーカー スレッド プールが作成され多数のクエリ要求を処理できるようになります。その結果、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-128">The **max worker threads** option enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create a pool of worker threads to service a larger number of query requests, which improves performance.</span></span>  
  
-   <span data-ttu-id="87ac7-129">次の表に、CPU および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各バージョンのさまざまな組み合わせに対して、自動的に構成されるワーカー スレッドの最大数を示します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-129">The following table shows the automatically configured number of max worker threads for various combinations of CPUs and versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    |<span data-ttu-id="87ac7-130">CPU の数</span><span class="sxs-lookup"><span data-stu-id="87ac7-130">Number of CPUs</span></span>|<span data-ttu-id="87ac7-131">32 ビット コンピューター</span><span class="sxs-lookup"><span data-stu-id="87ac7-131">32-bit computer</span></span>|<span data-ttu-id="87ac7-132">64 ビット コンピューター</span><span class="sxs-lookup"><span data-stu-id="87ac7-132">64-bit computer</span></span>|  
    |--------------------|----------------------|----------------------|  
    |<span data-ttu-id="87ac7-133">\<= 4 個のプロセッサ</span><span class="sxs-lookup"><span data-stu-id="87ac7-133">\<= 4 processors</span></span>|<span data-ttu-id="87ac7-134">256</span><span class="sxs-lookup"><span data-stu-id="87ac7-134">256</span></span>|<span data-ttu-id="87ac7-135">512</span><span class="sxs-lookup"><span data-stu-id="87ac7-135">512</span></span>|  
    |<span data-ttu-id="87ac7-136">8 個のプロセッサ</span><span class="sxs-lookup"><span data-stu-id="87ac7-136">8 processors</span></span>|<span data-ttu-id="87ac7-137">288</span><span class="sxs-lookup"><span data-stu-id="87ac7-137">288</span></span>|<span data-ttu-id="87ac7-138">576</span><span class="sxs-lookup"><span data-stu-id="87ac7-138">576</span></span>|  
    |<span data-ttu-id="87ac7-139">16 個のプロセッサ</span><span class="sxs-lookup"><span data-stu-id="87ac7-139">16 processors</span></span>|<span data-ttu-id="87ac7-140">352</span><span class="sxs-lookup"><span data-stu-id="87ac7-140">352</span></span>|<span data-ttu-id="87ac7-141">704</span><span class="sxs-lookup"><span data-stu-id="87ac7-141">704</span></span>|  
    |<span data-ttu-id="87ac7-142">32 個のプロセッサ</span><span class="sxs-lookup"><span data-stu-id="87ac7-142">32 processors</span></span>|<span data-ttu-id="87ac7-143">480</span><span class="sxs-lookup"><span data-stu-id="87ac7-143">480</span></span>|<span data-ttu-id="87ac7-144">960</span><span class="sxs-lookup"><span data-stu-id="87ac7-144">960</span></span>|  
    |<span data-ttu-id="87ac7-145">64 個のプロセッサ</span><span class="sxs-lookup"><span data-stu-id="87ac7-145">64 processors</span></span>|<span data-ttu-id="87ac7-146">736</span><span class="sxs-lookup"><span data-stu-id="87ac7-146">736</span></span>|<span data-ttu-id="87ac7-147">1472</span><span class="sxs-lookup"><span data-stu-id="87ac7-147">1472</span></span>|  
    |<span data-ttu-id="87ac7-148">128 個のプロセッサ</span><span class="sxs-lookup"><span data-stu-id="87ac7-148">128 processors</span></span>|<span data-ttu-id="87ac7-149">4224</span><span class="sxs-lookup"><span data-stu-id="87ac7-149">4224</span></span>|<span data-ttu-id="87ac7-150">4480</span><span class="sxs-lookup"><span data-stu-id="87ac7-150">4480</span></span>|  
    |<span data-ttu-id="87ac7-151">256 個のプロセッサ</span><span class="sxs-lookup"><span data-stu-id="87ac7-151">256 processors</span></span>|<span data-ttu-id="87ac7-152">8320</span><span class="sxs-lookup"><span data-stu-id="87ac7-152">8320</span></span>|<span data-ttu-id="87ac7-153">8576</span><span class="sxs-lookup"><span data-stu-id="87ac7-153">8576</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="87ac7-154">64 個を超える CPU を使用する場合の推奨事項については、「 [64 個を超える CPU を搭載したコンピューター上で SQL Server を実行する場合のベスト プラクティス](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ac7-154">For recommendations on using more than 64 CPUs, refer to [Best Practices for Running SQL Server on Computers That Have More Than 64 CPUs](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="87ac7-155">32 ビット コンピューター上で動作する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの場合、ワーカー スレッドの最大数として 1024 をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="87ac7-155">We recommend 1024 as the maximum number of worker threads for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on a 32-bit computer.</span></span>  
  
-   <span data-ttu-id="87ac7-156">クエリの実行が長時間にわたり、すべてのスレッドがアクティブになっている場合、いずれかのワーカー スレッドが処理を完了し使用できるようになるまで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が応答していないように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="87ac7-156">When all worker threads are active with long running queries, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might appear unresponsive until a worker thread completes and becomes available.</span></span> <span data-ttu-id="87ac7-157">これは欠陥ではありませんが、望ましくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="87ac7-157">Although this is not a defect, it can sometimes be undesirable.</span></span> <span data-ttu-id="87ac7-158">プロセスが応答せず新しいクエリを処理できない場合は、専用管理者接続 (DAC) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-158">If a process appears to be unresponsive and no new queries can be processed, then connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the dedicated administrator connection (DAC), and kill the process.</span></span> <span data-ttu-id="87ac7-159">このような状態を回避するには、ワーカー スレッド数を増やします。</span><span class="sxs-lookup"><span data-stu-id="87ac7-159">To prevent this, increase the number of max worker threads.</span></span>  
  
 <span data-ttu-id="87ac7-160">**max worker threads** サーバー構成オプションでは、可用性グループ、Service Broker、ロック マネージャーなど、すべてのシステム タスクに必要なスレッドは考慮されません。</span><span class="sxs-lookup"><span data-stu-id="87ac7-160">The **max worker threads** server configuration option does not take into account threads that are required for all the system tasks such as Availibility Groups, Service Broker, Lock Manager, and others.</span></span>  <span data-ttu-id="87ac7-161">構成されたスレッドの数を超えている場合は、次のクエリによって、追加のスレッドを生成したシステム タスクに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="87ac7-161">If the number of threads configured are being exceeded, the following query will provide information about the system tasks that have spawned the additional threads.</span></span>  
  
```  
SELECT  
s.session_id,  
r.command,  
r.status,  
r.wait_type,  
r.scheduler_id,  
w.worker_address,  
w.is_preemptive,  
w.state,  
t.task_state,  
t.session_id,  
t.exec_context_id,  
t.request_id  
FROM sys.dm_exec_sessions AS s  
INNERJOIN sys.dm_exec_requests AS r  
    ON s.session_id = r.session_id  
INNER JOIN sys.dm_os_tasks AS t  
    ON r.task_address = t.task_address  
INNER JOIN sys.dm_os_workers AS w  
    ON t.worker_address = w.worker_address  
WHERE s.is_user_process = 0;  
  
```  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="87ac7-162">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="87ac7-162">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="87ac7-163">Permissions</span><span class="sxs-lookup"><span data-stu-id="87ac7-163">Permissions</span></span>  
 <span data-ttu-id="87ac7-164">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="87ac7-164">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="87ac7-165">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="87ac7-165">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="87ac7-166">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="87ac7-166">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="87ac7-167">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="87ac7-167">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-worker-threads-option"></a><span data-ttu-id="87ac7-168">max worker threads オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="87ac7-168">To configure the max worker threads option</span></span>  
  
1.  <span data-ttu-id="87ac7-169">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87ac7-169">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="87ac7-170">**[プロセッサ]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="87ac7-170">Click the **Processors** node.</span></span>  
  
3.  <span data-ttu-id="87ac7-171">[**ワーカースレッドの最大数**] ボックスで、128 ~ 32767 の値を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-171">In the **Max worker threads** box, type or select a value from 128 through 32767.</span></span>  
  
     <span data-ttu-id="87ac7-172">**[ワーカー スレッド最大数]** オプションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスで利用できるワーカー スレッド数を設定できます。</span><span class="sxs-lookup"><span data-stu-id="87ac7-172">Use the **max worker threads** option to configure the number of worker threads available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes.</span></span> <span data-ttu-id="87ac7-173">ほとんどのシステムの場合、 **[ワーカー スレッド最大数]** の既定値を使用するのが最適です。</span><span class="sxs-lookup"><span data-stu-id="87ac7-173">The default setting for **max worker threads** is best for most systems.</span></span> <span data-ttu-id="87ac7-174">ただし、システム構成によっては、 **max worker threads** の値を小さくするとパフォーマンスが向上することがあります。</span><span class="sxs-lookup"><span data-stu-id="87ac7-174">However, depending on your system configuration, setting **max worker threads** to a smaller value sometimes improves performance.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="87ac7-175">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="87ac7-175">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-worker-threads-option"></a><span data-ttu-id="87ac7-176">max worker threads オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="87ac7-176">To configure the max worker threads option</span></span>  
  
1.  <span data-ttu-id="87ac7-177">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-177">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="87ac7-178">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87ac7-178">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="87ac7-179">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87ac7-179">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="87ac7-180">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `max worker threads` オプションを `900`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="87ac7-180">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max worker threads` option to `900`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'max worker threads', 900 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="87ac7-181">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ac7-181">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-worker-threads-option"></a><a name="FollowUp"></a><span data-ttu-id="87ac7-182">補足情報: max worker threads オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="87ac7-182">Follow Up: After you configure the max worker threads option</span></span>  
 <span data-ttu-id="87ac7-183">[!INCLUDE[ssDE](../../includes/ssde-md.md)] を再起動しなくても、変更は直ちに有効になります。</span><span class="sxs-lookup"><span data-stu-id="87ac7-183">The change will take effect immediately without requiring the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ac7-184">参照</span><span class="sxs-lookup"><span data-stu-id="87ac7-184">See Also</span></span>  
 <span data-ttu-id="87ac7-185">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87ac7-185">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="87ac7-186">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="87ac7-186">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="87ac7-187">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87ac7-187">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="87ac7-188">データベース管理者用の診断接続</span><span class="sxs-lookup"><span data-stu-id="87ac7-188">Diagnostic Connection for Database Administrators</span></span>](diagnostic-connection-for-database-administrators.md)  
  
  
