---
title: SQL Server オブジェクトの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- server performance [SQL Server], objects for monitoring
- database monitoring [SQL Server], objects for monitoring
- charts [SQL Server]
- System Monitor [SQL Server], counters
- counters [SQL Server], listed
- objects [SQL Server], performance monitoring
- objects [SQL Server], Windows System Monitor
- performance counters [SQL Server], about performance counters
- System Monitor [SQL Server], objects
- performance counters [SQL Server]
- counters [SQL Server], about performance counters
- tuning databases [SQL Server], objects for monitoring
- database performance [SQL Server], objects for monitoring
- SQL Server, objects
- monitoring performance [SQL Server], objects for monitoring
- Windows System Monitor [SQL Server], objects
- Windows System Monitor [SQL Server], counters
- counters [SQL Server]
- performance counters [SQL Server], listed
ms.assetid: bcd731b1-3c4e-4086-b58a-af7a3af904ad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c073b0f438ec022e1b05f481652d6f08ef34cc53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714233"
---
# <a name="use-sql-server-objects"></a><span data-ttu-id="5d3e5-102">SQL Server オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="5d3e5-102">Use SQL Server Objects</span></span>
  <span data-ttu-id="5d3e5-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、システム モニターで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを実行しているコンピューターの利用状況を監視できるオブジェクトとカウンターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides objects and counters that can be used by System Monitor to monitor activity in computers running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5d3e5-104">オブジェクトとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロックや Windows プロセスなど任意の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースです。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-104">An object is any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lock or Windows process.</span></span> <span data-ttu-id="5d3e5-105">各オブジェクトには、監視するオブジェクトのさまざまな特性を示す 1 つ以上のカウンターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-105">Each object contains one or more counters that determine various aspects of the objects to monitor.</span></span> <span data-ttu-id="5d3e5-106">たとえば、 **SQL Server Locks** オブジェクトには、 **Number of Deadlocks/sec** や **Lock Timeouts/sec**という名前のカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-106">For example, the **SQL Server Locks** object contains counters called **Number of Deadlocks/sec** and **Lock Timeouts/sec**.</span></span>  
  
 <span data-ttu-id="5d3e5-107">同じ種類の複数のリソースがコンピューター上に存在する場合、オブジェクトによっては複数のインスタンスがある場合があります。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-107">Some objects have several instances if multiple resources of a given type exist on the computer.</span></span> <span data-ttu-id="5d3e5-108">たとえば、システムに複数のプロセッサが搭載されている場合、オブジェクトの種類 **Processor** には複数のインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-108">For example, the **Processor** object type will have multiple instances if a system has multiple processors.</span></span> <span data-ttu-id="5d3e5-109">オブジェクトの種類 **Databases** には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータベースごとに 1 つのインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-109">The **Databases** object type has one instance for each database on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5d3e5-110">**Memory Manager** オブジェクトなど一部のオブジェクトの種類には、1 しかインスタンスのないものもあります。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-110">Some object types (for example, the **Memory Manager** object) have only one instance.</span></span> <span data-ttu-id="5d3e5-111">あるオブジェクトの種類に複数のインスタンスがある場合には、インスタンスごとに、または多くの場合は一度にすべてのインスタンスに、統計を追跡するためのカウンターを追加できます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-111">If an object type has multiple instances, you can add counters to track statistics for each instance, or in many cases, all instances at once.</span></span> <span data-ttu-id="5d3e5-112">既定のインスタンスのカウンターは、**SQLServer:** _\<object name>_ の形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-112">Counters for the default instance appear in the format **SQLServer:**_\<object name>_.</span></span> <span data-ttu-id="5d3e5-113">名前付きインスタンスのカウンターは、**MSSQL$** _\<instance name>_ **:** _\<counter name>_ または **SQLAgent$** _\<instance name>_ **:** _\<counter name>_ の形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-113">Counters for named instances appear in the format **MSSQL$**_\<instance name>_**:**_\<counter name>_ or **SQLAgent$**_\<instance name>_**:**_\<counter name>_.</span></span>  
  
 <span data-ttu-id="5d3e5-114">グラフでカウンターを追加または削除し、グラフ設定を保存して、システム モニターを起動したときに監視する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトとカウンターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-114">By adding or removing counters to the chart and saving the chart settings, you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects and counters that are monitored when System Monitor is started.</span></span>  
  
 <span data-ttu-id="5d3e5-115">システム モニターは、任意の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カウンターの統計を表示するように構成することができます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-115">You can configure System Monitor to display statistics from any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counter.</span></span> <span data-ttu-id="5d3e5-116">また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カウンターにしきい値を設定して、カウンターがしきい値を超えたときに警告を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-116">In addition, you can set a threshold value for any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counter and then generate an alert when a counter exceeds a threshold.</span></span> <span data-ttu-id="5d3e5-117">警告を構成する方法の詳細については、「 [SQL Server データベース警告の作成](create-a-sql-server-database-alert.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-117">For more information about setting an alert, see [Create a SQL Server Database Alert](create-a-sql-server-database-alert.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5d3e5-118">の統計情報は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがインストールされているときにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-118">statistics are displayed only when an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="5d3e5-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを停止して再起動すると、SQL Server の統計情報の表示も中断され、自動的に再開されます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-119">If you stop and restart an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the display of statistics is interrupted and resumes automatically.</span></span> <span data-ttu-id="5d3e5-120">システム モニター スナップインでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されていないときでも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のカウンターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-120">Also note that you will see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counters in the System Monitor snap-in even if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running.</span></span> <span data-ttu-id="5d3e5-121">クラスター化されたインスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されているノードでのみ、パフォーマンス カウンターが機能します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-121">On a clustered instance, performance counters only function on the node where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
 <span data-ttu-id="5d3e5-122">このトピックには、次のセクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-122">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="5d3e5-123">SQL Server エージェント パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-123">SQL Server Agent Performance Objects</span></span>](#SQLServerAgentPOs)  
  
-   [<span data-ttu-id="5d3e5-124">Service Broker のパフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-124">Service Broker Performance Objects</span></span>](#ServiceBrokerPOs)  
  
-   [<span data-ttu-id="5d3e5-125">SQL Server パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-125">SQL Server Performance Objects</span></span>](#SQLServerPOs)  
  
-   [<span data-ttu-id="5d3e5-126">SQL Server レプリケーション パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-126">SQL Server Replication Performance Objects</span></span>](#SQLServerReplicationPOs)  
  
-   [<span data-ttu-id="5d3e5-127">SSIS Pipeline カウンター</span><span class="sxs-lookup"><span data-stu-id="5d3e5-127">SSIS Pipeline Counters</span></span>](#SsisPipelineCounters)  
  
-   [<span data-ttu-id="5d3e5-128">必要なアクセス許可</span><span class="sxs-lookup"><span data-stu-id="5d3e5-128">Required Permissions</span></span>](#RequiredPermissions)  
  
##  <a name="sql-server-agent-performance-objects"></a><a name="SQLServerAgentPOs"></a> <span data-ttu-id="5d3e5-129">SQL Server エージェント パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-129">SQL Server Agent Performance Objects</span></span>  
 <span data-ttu-id="5d3e5-130">次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント用のパフォーマンス オブジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-130">The following table lists the performance objects provided for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent:</span></span>  
  
|<span data-ttu-id="5d3e5-131">パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-131">Performance object</span></span>|<span data-ttu-id="5d3e5-132">説明</span><span class="sxs-lookup"><span data-stu-id="5d3e5-132">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="5d3e5-133">SQLAgent:Alerts</span><span class="sxs-lookup"><span data-stu-id="5d3e5-133">SQLAgent:Alerts</span></span>](sql-server-agent-alerts-object.md)|<span data-ttu-id="5d3e5-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント警告についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-134">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>|  
|[<span data-ttu-id="5d3e5-135">SQLAgent:Jobs</span><span class="sxs-lookup"><span data-stu-id="5d3e5-135">SQLAgent:Jobs</span></span>](sql-server-agent-jobs-object.md)|<span data-ttu-id="5d3e5-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-136">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
|[<span data-ttu-id="5d3e5-137">SQLAgent:JobSteps</span><span class="sxs-lookup"><span data-stu-id="5d3e5-137">SQLAgent:JobSteps</span></span>](sql-server-agent-jobsteps-object.md)|<span data-ttu-id="5d3e5-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-138">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps.</span></span>|  
|[<span data-ttu-id="5d3e5-139">SQLAgent:Statistics</span><span class="sxs-lookup"><span data-stu-id="5d3e5-139">SQLAgent:Statistics</span></span>](sql-server-agent-statistics-object.md)|<span data-ttu-id="5d3e5-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントについての一般的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-140">Provides general information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>|  
  
##  <a name="service-broker-performance-objects"></a><a name="ServiceBrokerPOs"></a> <span data-ttu-id="5d3e5-141">Service Broker のパフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-141">Service Broker Performance Objects</span></span>  
 <span data-ttu-id="5d3e5-142">次の表は、 [!INCLUDE[ssSB](../../includes/sssb-md.md)]用のパフォーマンス オブジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-142">The following table lists the performance objects provided for [!INCLUDE[ssSB](../../includes/sssb-md.md)].</span></span>  
  
|<span data-ttu-id="5d3e5-143">パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-143">Performance object</span></span>|<span data-ttu-id="5d3e5-144">説明</span><span class="sxs-lookup"><span data-stu-id="5d3e5-144">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="5d3e5-145">SQLServer:Broker Activation</span><span class="sxs-lookup"><span data-stu-id="5d3e5-145">SQLServer:Broker Activation</span></span>](sql-server-broker-activation-object.md)|<span data-ttu-id="5d3e5-146">[!INCLUDE[ssSB](../../includes/sssb-md.md)]のアクティブなタスクについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-146">Provides information about [!INCLUDE[ssSB](../../includes/sssb-md.md)]-activated tasks.</span></span>|  
|[<span data-ttu-id="5d3e5-147">SQLServer:Broker Statistics</span><span class="sxs-lookup"><span data-stu-id="5d3e5-147">SQLServer:Broker Statistics</span></span>](sql-server-broker-statistics-object.md)|<span data-ttu-id="5d3e5-148">[!INCLUDE[ssSB](../../includes/sssb-md.md)] についての一般的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-148">Provides general [!INCLUDE[ssSB](../../includes/sssb-md.md)] information.</span></span>|  
|[<span data-ttu-id="5d3e5-149">SQLServer:Broker Transport</span><span class="sxs-lookup"><span data-stu-id="5d3e5-149">SQLServer:Broker Transport</span></span>](sql-server-broker-dbm-transport-object.md)|<span data-ttu-id="5d3e5-150">[!INCLUDE[ssSB](../../includes/sssb-md.md)] のネットワークについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-150">Provides information on [!INCLUDE[ssSB](../../includes/sssb-md.md)] networking.</span></span>|  
  
##  <a name="sql-server-performance-objects"></a><a name="SQLServerPOs"></a> <span data-ttu-id="5d3e5-151">SQL Server パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-151">SQL Server Performance Objects</span></span>  
 <span data-ttu-id="5d3e5-152">次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-152">The following table describes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span>  
  
|<span data-ttu-id="5d3e5-153">パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-153">Performance object</span></span>|<span data-ttu-id="5d3e5-154">説明</span><span class="sxs-lookup"><span data-stu-id="5d3e5-154">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="5d3e5-155">SQLServer:Access Methods</span><span class="sxs-lookup"><span data-stu-id="5d3e5-155">SQLServer:Access Methods</span></span>](sql-server-access-methods-object.md)|<span data-ttu-id="5d3e5-156">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース オブジェクトの割り当てを検索して計測します。たとえば、インデックスとデータに割り当てられているインデックス検索の数またはページ数を計測します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-156">Searches through and measures allocation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects (for example, the number of index searches or number of pages that are allocated to indexes and data).</span></span>|  
|[<span data-ttu-id="5d3e5-157">SQLServer:Backup Device</span><span class="sxs-lookup"><span data-stu-id="5d3e5-157">SQLServer:Backup Device</span></span>](sql-server-backup-device-object.md)|<span data-ttu-id="5d3e5-158">バックアップ デバイスのスループットなど、バックアップ操作と復元操作で使用するバックアップ デバイスについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-158">Provides information about backup devices used by backup and restore operations, such as the throughput of the backup device.</span></span>|  
|[<span data-ttu-id="5d3e5-159">SQLServer: Buffer Manager</span><span class="sxs-lookup"><span data-stu-id="5d3e5-159">SQLServer:Buffer Manager</span></span>](sql-server-buffer-manager-object.md)|<span data-ttu-id="5d3e5-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]freememory **や** buffer cache hit ratio **など、** で使用するメモリ バッファーについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-160">Provides information about the memory buffers used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as **freememory** and **buffer cache hit ratio**.</span></span>|  
|[<span data-ttu-id="5d3e5-161">SQL Server: Buffer Node</span><span class="sxs-lookup"><span data-stu-id="5d3e5-161">SQL Server:Buffer Node</span></span>](sql-server-buffer-node.md)|<span data-ttu-id="5d3e5-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によるフリー ページの要求頻度とアクセスの頻度についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-162">Provides information about how frequently [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requests and accesses free pages.</span></span>|  
|[<span data-ttu-id="5d3e5-163">SQLServer:CLR</span><span class="sxs-lookup"><span data-stu-id="5d3e5-163">SQLServer:CLR</span></span>](sql-server-clr-object.md)|<span data-ttu-id="5d3e5-164">共通言語ランタイム (CLR: Common Language Runtime) に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-164">Provides information about the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="5d3e5-165">SQLServer:Cursor Manager by Type</span><span class="sxs-lookup"><span data-stu-id="5d3e5-165">SQLServer:Cursor Manager by Type</span></span>](sql-server-cursor-manager-by-type-object.md)|<span data-ttu-id="5d3e5-166">カーソルについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-166">Provides information about cursors.</span></span>|  
|[<span data-ttu-id="5d3e5-167">SQLServer:Cursor Manager Total</span><span class="sxs-lookup"><span data-stu-id="5d3e5-167">SQLServer:Cursor Manager Total</span></span>](sql-server-cursor-manager-total-object.md)|<span data-ttu-id="5d3e5-168">カーソルについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-168">Provides information about cursors.</span></span>|  
|[<span data-ttu-id="5d3e5-169">SQLServer:Database Mirroring</span><span class="sxs-lookup"><span data-stu-id="5d3e5-169">SQLServer:Database Mirroring</span></span>](sql-server-database-mirroring-object.md)|<span data-ttu-id="5d3e5-170">データベース ミラーリングについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-170">Provides information about database mirroring.</span></span>|  
|[<span data-ttu-id="5d3e5-171">SQLServer:Databases</span><span class="sxs-lookup"><span data-stu-id="5d3e5-171">SQLServer:Databases</span></span>](sql-server-databases-object.md)|<span data-ttu-id="5d3e5-172">使用できるログ用空きディスク領域やデータベース内のアクティブなトランザクションの数など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-172">Provides information about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, such as the amount of free log space available or the number of active transactions in the database.</span></span> <span data-ttu-id="5d3e5-173">このオブジェクトには、複数のインスタンスが存在することがあります。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-173">There can be multiple instances of this object.</span></span>|  
|[<span data-ttu-id="5d3e5-174">SQL Server:Deprecated Features</span><span class="sxs-lookup"><span data-stu-id="5d3e5-174">SQL Server:Deprecated Features</span></span>](sql-server-deprecated-features-object.md)|<span data-ttu-id="5d3e5-175">非推奨機能が使用された回数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-175">Counts the number of times that deprecated features are used.</span></span>|  
|[<span data-ttu-id="5d3e5-176">SQLServer:Exec Statistics</span><span class="sxs-lookup"><span data-stu-id="5d3e5-176">SQLServer:Exec Statistics</span></span>](sql-server-execstatistics-object.md)|<span data-ttu-id="5d3e5-177">実行統計についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-177">Provides information about execution statistics.</span></span>|  
|[<span data-ttu-id="5d3e5-178">SQLServer:General Statistics</span><span class="sxs-lookup"><span data-stu-id="5d3e5-178">SQLServer:General Statistics</span></span>](sql-server-general-statistics-object.md)|<span data-ttu-id="5d3e5-179">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続しているユーザーの数など、一般的なサーバー全体の利用状況についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-179">Provides information about general server-wide activity, such as the number of users who are connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="5d3e5-180">SQL Server:HADR Availability Replica</span><span class="sxs-lookup"><span data-stu-id="5d3e5-180">SQL Server:HADR Availability Replica</span></span>](sql-server-availability-replica.md)|<span data-ttu-id="5d3e5-181">現在割り当てられているロック構造の総数など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 可用性レプリカについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-181">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] availability replicas.</span></span>|  
|[<span data-ttu-id="5d3e5-182">SQL Server:HADR Database Replica</span><span class="sxs-lookup"><span data-stu-id="5d3e5-182">SQL Server:HADR Database Replica</span></span>](sql-server-database-replica.md)|<span data-ttu-id="5d3e5-183">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] データベース レプリカについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-183">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] database replicas.</span></span>|  
|[<span data-ttu-id="5d3e5-184">SQLServer:Latches</span><span class="sxs-lookup"><span data-stu-id="5d3e5-184">SQLServer:Latches</span></span>](sql-server-latches-object.md)|<span data-ttu-id="5d3e5-185">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用されるデータベース ページなど、内部リソースのラッチについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-185">Provides information about the latches on internal resources, such as database pages, that are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="5d3e5-186">SQLServer:Locks</span><span class="sxs-lookup"><span data-stu-id="5d3e5-186">SQLServer:Locks</span></span>](sql-server-locks-object.md)|<span data-ttu-id="5d3e5-187">ロック タイムアウトやデッドロックなど、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]による各ロック要求についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-187">Provides information about the individual lock requests made by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as lock time-outs and deadlocks.</span></span> <span data-ttu-id="5d3e5-188">このオブジェクトには、複数のインスタンスが存在することがあります。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-188">There can be multiple instances of this object.</span></span>|  
|[<span data-ttu-id="5d3e5-189">SQLServer:Memory Manager</span><span class="sxs-lookup"><span data-stu-id="5d3e5-189">SQLServer:Memory Manager</span></span>](sql-server-memory-manager-object.md)|<span data-ttu-id="5d3e5-190">現在割り当てられているロック構造の総数など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリの利用状況についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-190">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory usage, such as the total number of lock structures currently allocated.</span></span>|  
|[<span data-ttu-id="5d3e5-191">SQLServer:Plan Cache</span><span class="sxs-lookup"><span data-stu-id="5d3e5-191">SQLServer:Plan Cache</span></span>](sql-server-plan-cache-object.md)|<span data-ttu-id="5d3e5-192">ストアド プロシージャ、トリガー、クエリ プランなど、オブジェクトを保存するために使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] キャッシュについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-192">Provides information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cache used to store objects such as stored procedures, triggers, and query plans.</span></span>|  
|[<span data-ttu-id="5d3e5-193">SQLServer:Resource Pool Stats</span><span class="sxs-lookup"><span data-stu-id="5d3e5-193">SQLServer: Resource Pool Stats</span></span>](sql-server-resource-pool-stats-object.md)|<span data-ttu-id="5d3e5-194">リソース ガバナーのリソース プール統計に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-194">Provides information about Resource Governor resource pool statistics.</span></span>|  
|[<span data-ttu-id="5d3e5-195">SQLServer:SQL Errors</span><span class="sxs-lookup"><span data-stu-id="5d3e5-195">SQLServer:SQL Errors</span></span>](sql-server-sql-errors-object.md)|<span data-ttu-id="5d3e5-196">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-196">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errors.</span></span>|  
|[<span data-ttu-id="5d3e5-197">SQLServer:SQL Statistics</span><span class="sxs-lookup"><span data-stu-id="5d3e5-197">SQLServer:SQL Statistics</span></span>](sql-server-sql-statistics-object.md)|<span data-ttu-id="5d3e5-198">[!INCLUDE[tsql](../../includes/tsql-md.md)] で受信する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのバッチ数など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリの側面についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-198">Provides information about aspects of [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, such as the number of batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements received by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="5d3e5-199">SQLServer:Transactions</span><span class="sxs-lookup"><span data-stu-id="5d3e5-199">SQLServer:Transactions</span></span>](sql-server-transactions-object.md)|<span data-ttu-id="5d3e5-200">トランザクションの総数やスナップショット トランザクションの数など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアクティブなトランザクションについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-200">Provides information about the active transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as the overall number of transactions and the number of snapshot transactions.</span></span>|  
|[<span data-ttu-id="5d3e5-201">SQLServer:User Settable</span><span class="sxs-lookup"><span data-stu-id="5d3e5-201">SQLServer:User Settable</span></span>](sql-server-user-settable-object.md)|<span data-ttu-id="5d3e5-202">カスタム監視を実行します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-202">Performs custom monitoring.</span></span> <span data-ttu-id="5d3e5-203">各カウンターは、監視する値を返すカスタム ストアド プロシージャまたは任意の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-203">Each counter can be a custom stored procedure or any [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that returns a value to be monitored.</span></span>|  
|[<span data-ttu-id="5d3e5-204">SQLServer:Wait Statistics</span><span class="sxs-lookup"><span data-stu-id="5d3e5-204">SQLServer: Wait Statistics</span></span>](sql-server-wait-statistics-object.md)|<span data-ttu-id="5d3e5-205">待機についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-205">Provides information about waits.</span></span>|  
|[<span data-ttu-id="5d3e5-206">SQLServer:Workload Group Stats</span><span class="sxs-lookup"><span data-stu-id="5d3e5-206">SQLServer: Workload Group Stats</span></span>](sql-server-workload-group-stats-object.md)|<span data-ttu-id="5d3e5-207">リソース ガバナーのワークロード グループ統計に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-207">Provides information about Resource Governor workload group statistics.</span></span>|  
  
##  <a name="sql-server-replication-performance-objects"></a><a name="SQLServerReplicationPOs"></a> <span data-ttu-id="5d3e5-208">SQL Server レプリケーション パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-208">SQL Server Replication Performance Objects</span></span>  
 <span data-ttu-id="5d3e5-209">次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション用のパフォーマンス オブジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-209">The following table lists the performance objects provided for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication:</span></span>  
  
|<span data-ttu-id="5d3e5-210">パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d3e5-210">Performance object</span></span>|<span data-ttu-id="5d3e5-211">説明</span><span class="sxs-lookup"><span data-stu-id="5d3e5-211">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="5d3e5-212">**SQLServer:Replication Agents**</span><span class="sxs-lookup"><span data-stu-id="5d3e5-212">**SQLServer:Replication Agents**</span></span><br /><br /> <span data-ttu-id="5d3e5-213">**SQLServer:Replication Snapshot**</span><span class="sxs-lookup"><span data-stu-id="5d3e5-213">**SQLServer:Replication Snapshot**</span></span><br /><br /> <span data-ttu-id="5d3e5-214">**SQLServer:Replication Logreader**</span><span class="sxs-lookup"><span data-stu-id="5d3e5-214">**SQLServer:Replication Logreader**</span></span><br /><br /> <span data-ttu-id="5d3e5-215">**SQLServer:Replication Dist.**</span><span class="sxs-lookup"><span data-stu-id="5d3e5-215">**SQLServer:Replication Dist.**</span></span><br /><br /> <span data-ttu-id="5d3e5-216">**SQLServer:Replication Merge**</span><span class="sxs-lookup"><span data-stu-id="5d3e5-216">**SQLServer:Replication Merge**</span></span><br /><br /> <span data-ttu-id="5d3e5-217">詳細については、「 [Monitoring Replication with System Monitor](../replication/monitor/monitoring-replication-with-system-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-217">For more information, see [Monitoring Replication with System Monitor](../replication/monitor/monitoring-replication-with-system-monitor.md).</span></span>|<span data-ttu-id="5d3e5-218">レプリケーション エージェントの利用状況についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-218">Provides information about replication agent activity.</span></span>|  
  
##  <a name="ssis-pipeline-counters"></a><a name="SsisPipelineCounters"></a> <span data-ttu-id="5d3e5-219">SSIS Pipeline カウンター</span><span class="sxs-lookup"><span data-stu-id="5d3e5-219">SSIS Pipeline Counters</span></span>  
 <span data-ttu-id="5d3e5-220">**SSIS Pipeline** カウンターの詳細については、「 [パフォーマンス カウンター](../../integration-services/performance/performance-counters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-220">For the **SSIS Pipeline** counter, see [Performance Counters](../../integration-services/performance/performance-counters.md).</span></span>  
  
##  <a name="required-permissions"></a><a name="RequiredPermissions"></a> <span data-ttu-id="5d3e5-221">必要な権限</span><span class="sxs-lookup"><span data-stu-id="5d3e5-221">Required Permissions</span></span>  
 <span data-ttu-id="5d3e5-222">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLAgent:Alerts **以外の**オブジェクトを使用する際の権限は Windows のアクセス許可に依存しています。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-222">Use of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects depends on Windows permissions, except **SQLAgent:Alerts**.</span></span> <span data-ttu-id="5d3e5-223">**SQLAgent:Alerts** を使用するには、ユーザーは **sysadmin**固定サーバー ロールのメンバーでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-223">Users must be a member of the **sysadmin** fixed server role to use **SQLAgent:Alerts**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3e5-224">参照</span><span class="sxs-lookup"><span data-stu-id="5d3e5-224">See Also</span></span>  
 <span data-ttu-id="5d3e5-225">[パフォーマンス オブジェクトの使用](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="5d3e5-225">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="5d3e5-226">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5d3e5-226">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  