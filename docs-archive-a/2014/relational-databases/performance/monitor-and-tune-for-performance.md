---
title: パフォーマンスの監視とチューニング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- instances of SQL Server, monitoring performance
- monitoring server performance [SQL Server]
- Database Engine [SQL Server], performance
- monitoring performance [SQL Server], about performance
- server performance [SQL Server]
- monitoring performance [SQL Server]
- database performance [SQL Server], about performance
- tuning databases [SQL Server], about performance
- status information [SQL Server], performance monitoring
- database monitoring [SQL Server], about performance
- monitoring [SQL Server], queries performance
- server performance [SQL Server], about performance
- tuning databases [SQL Server]
- database performance [SQL Server]
- monitoring [SQL Server], server performance
- database monitoring [SQL Server]
- monitoring server performance [SQL Server], about monitoring server performance
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe07bdf01df6c4b61a64c6ee78de313a21d62f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634478"
---
# <a name="monitor-and-tune-for-performance"></a><span data-ttu-id="96e69-102">パフォーマンスの監視とチューニング</span><span class="sxs-lookup"><span data-stu-id="96e69-102">Monitor and Tune for Performance</span></span>
  <span data-ttu-id="96e69-103">データベースを監視する目的は、サーバーのパフォーマンスを評価することです。</span><span class="sxs-lookup"><span data-stu-id="96e69-103">The goal of monitoring databases is to assess how a server is performing.</span></span> <span data-ttu-id="96e69-104">適切な監視には、現在のパフォーマンスのスナップショットを定期的にキャプチャして問題の原因となっているプロセスを特定したり、長期にわたって継続的にデータを採取してパフォーマンスの傾向を追跡する作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="96e69-104">Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.</span></span>  
  
 <span data-ttu-id="96e69-105">データベース パフォーマンスの継続的な評価は、応答時間を最小限にし、スループットを最大限にして、最適なパフォーマンスを実現するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="96e69-105">Ongoing evaluation of the database performance helps you minimize response times and maximize throughput, yielding optimal performance.</span></span> <span data-ttu-id="96e69-106">パフォーマンスを最大限に高めるには、効率的なネットワーク トラフィック、ディスク I/O、および CPU 使用が重要です。</span><span class="sxs-lookup"><span data-stu-id="96e69-106">Efficient network traffic, disk I/O, and CPU usage are key to peak performance.</span></span> <span data-ttu-id="96e69-107">アプリケーションの要件を十分に分析し、データの論理構造と物理構造を理解し、データベースの使用状況を評価し、競合する処理 (オンライン トランザクション処理 (OLTP) と意思決定支援など) の関係を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96e69-107">You need to thoroughly analyze the application requirements, understand the logical and physical structure of the data, assess database usage, and negotiate tradeoffs between conflicting uses such as online transaction processing (OLTP) versus decision support.</span></span>  
  
## <a name="benefits-of-monitoring-and-tuning-databases-for-performance"></a><span data-ttu-id="96e69-108">パフォーマンスのためのデータベースの監視とチューニングの利点</span><span class="sxs-lookup"><span data-stu-id="96e69-108">Benefits of Monitoring and Tuning Databases for Performance</span></span>  
 <span data-ttu-id="96e69-109">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および Microsoft Windows オペレーティング システムでは、データベースの現在の状態を参照したり、状態の変化に伴うパフォーマンスを追跡するためのユーティリティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="96e69-109">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the Microsoft Windows operating system provide utilities that allow you to view the current condition of the database and to track performance as conditions change.</span></span> <span data-ttu-id="96e69-110">の監視に使用できるさまざまなツールと手法があり [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="96e69-110">There are a variety of tools and techniques that can be used to monitor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="96e69-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を監視する方法を理解しておくと、次の作業に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="96e69-111">Understanding how to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can help you:</span></span>  
  
-   <span data-ttu-id="96e69-112">パフォーマンスを向上できるかどうかの判断。</span><span class="sxs-lookup"><span data-stu-id="96e69-112">Determine whether you can improve performance.</span></span> <span data-ttu-id="96e69-113">たとえば、頻繁に使用するクエリの応答時間を監視することで、テーブルに対するクエリまたはインデックスの変更が必要かどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="96e69-113">For example, by monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables are required.</span></span>  
  
-   <span data-ttu-id="96e69-114">ユーザーの利用状況の評価。</span><span class="sxs-lookup"><span data-stu-id="96e69-114">Evaluate user activity.</span></span> <span data-ttu-id="96e69-115">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続しようとするユーザーを監視することで、セキュリティが適切に設定されているかどうかを判断し、アプリケーションや開発システムをテストできます。</span><span class="sxs-lookup"><span data-stu-id="96e69-115">For example, by monitoring users trying to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can determine whether security is set up adequately and test applications or development systems.</span></span> <span data-ttu-id="96e69-116">また、実行時に SQL クエリを監視することで、クエリが正しく作成され、期待どおりの結果が得られているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="96e69-116">For example, by monitoring SQL queries as they are executed, you can determine whether they are written correctly and producing the expected results.</span></span>  
  
-   <span data-ttu-id="96e69-117">問題のトラブルシューティングや、ストアド プロシージャなどのアプリケーション コンポーネントのデバッグ。</span><span class="sxs-lookup"><span data-stu-id="96e69-117">Troubleshoot any problems or debug application components, such as stored procedures.</span></span>  
  
### <a name="monitoring-in-a-dynamic-environment"></a><span data-ttu-id="96e69-118">動的な環境での監視</span><span class="sxs-lookup"><span data-stu-id="96e69-118">Monitoring in a Dynamic Environment</span></span>  
 <span data-ttu-id="96e69-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では動的な環境でサービスを提供しているため、監視することは重要です。</span><span class="sxs-lookup"><span data-stu-id="96e69-119">Monitoring is important because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a service in a dynamic environment.</span></span> <span data-ttu-id="96e69-120">条件を変更すると、パフォーマンスが変化します。</span><span class="sxs-lookup"><span data-stu-id="96e69-120">Changing conditions result in changing performance.</span></span> <span data-ttu-id="96e69-121">評価では、ユーザー数の増加によるパフォーマンスの変化、ユーザーのアクセス方法と接続方法の変化、データベース コンテンツの増加、クライアント アプリケーションの変化、アプリケーション内のデータの変化、クエリの複雑化、およびネットワーク トラフィックの増加を確認できます。</span><span class="sxs-lookup"><span data-stu-id="96e69-121">In your evaluations, you can see performance changes as the number of users increases, user access and connection methods change, database contents grow, client applications change, data in the applications changes, queries become more complex, and network traffic rises.</span></span> <span data-ttu-id="96e69-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ツールを使用してパフォーマンスを監視することにより、パフォーマンスの変化を、変化する条件と複雑なクエリに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="96e69-122">By using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools to monitor performance, you can associate some changes in performance with changing conditions and complex queries.</span></span> <span data-ttu-id="96e69-123">次のシナリオで例を示します。</span><span class="sxs-lookup"><span data-stu-id="96e69-123">The following scenarios provide examples:</span></span>  
  
-   <span data-ttu-id="96e69-124">頻繁に使用されるクエリの応答時間を監視することによって、クエリを実行するテーブルに対するクエリまたはインデックスの変更が必要かどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="96e69-124">By monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables where the queries execute are required.</span></span>  
  
-   <span data-ttu-id="96e69-125">実行時に [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを監視することによって、クエリが正しく作成され、期待どおりの結果が得られているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="96e69-125">By monitoring [!INCLUDE[tsql](../../includes/tsql-md.md)] queries as they are executed, you can determine whether the queries are written correctly and producing the expected results.</span></span>  
  
-   <span data-ttu-id="96e69-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続しようとするユーザーを監視することによって、セキュリティが適切に設定されているかどうかを判断でき、アプリケーションまたは開発システムをテストできます。</span><span class="sxs-lookup"><span data-stu-id="96e69-126">By monitoring users that try to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can determine whether security is set up adequately and test applications or development systems.</span></span>  
  
 <span data-ttu-id="96e69-127">応答時間は、クエリが処理されていることを視覚的に確認できる形式で、結果セットの先頭行をユーザーに返すのに必要な時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="96e69-127">Response time is the length of time required for the first row of the result set to be returned to the user in the form of visual confirmation that a query is being processed.</span></span> <span data-ttu-id="96e69-128">スループットは、指定した時間内にサーバーで処理されたクエリの合計数です。</span><span class="sxs-lookup"><span data-stu-id="96e69-128">Throughput is the total number of queries handled by the server during a specified period of time.</span></span>  
  
 <span data-ttu-id="96e69-129">ユーザーの数が増えるにつれて、サーバーのリソースの競合も増えます。その結果、応答時間が長くなり、全般的なスループットが減少します。</span><span class="sxs-lookup"><span data-stu-id="96e69-129">As the number of users increases, so does the competition for a server's resources, which in turn increases response time and decreases overall throughput.</span></span>  
  
## <a name="monitoring-and-tuning-performance-tasks"></a><span data-ttu-id="96e69-130">パフォーマンスの監視とチューニングのタスク</span><span class="sxs-lookup"><span data-stu-id="96e69-130">Monitoring and Tuning Performance Tasks</span></span>  
  
|<span data-ttu-id="96e69-131">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="96e69-131">Task Description</span></span>|<span data-ttu-id="96e69-132">トピック</span><span class="sxs-lookup"><span data-stu-id="96e69-132">Topic</span></span>|  
|----------------------|-----------|  
|[<span data-ttu-id="96e69-133">SQL Server コンポーネントの監視</span><span class="sxs-lookup"><span data-stu-id="96e69-133">Monitor SQL Server Components</span></span>](monitor-sql-server-components.md)|<span data-ttu-id="96e69-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のコンポーネントを効果的に監視するために必要な手順を提供します。</span><span class="sxs-lookup"><span data-stu-id="96e69-134">Provides the necessary steps required to effectively monitor any component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="96e69-135">パフォーマンス監視およびチューニング ツール</span><span class="sxs-lookup"><span data-stu-id="96e69-135">Performance Monitoring and Tuning Tools</span></span>](performance-monitoring-and-tuning-tools.md)|<span data-ttu-id="96e69-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の監視およびチューニング用のツールの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="96e69-136">Lists the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitoring and tuning tools.</span></span>|  
|[<span data-ttu-id="96e69-137">パフォーマンスのベースラインの設定</span><span class="sxs-lookup"><span data-stu-id="96e69-137">Establish a Performance Baseline</span></span>](establish-a-performance-baseline.md)|<span data-ttu-id="96e69-138">パフォーマンス ベースラインを設定する方法についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="96e69-138">Provides information about how to establish a performance baseline.</span></span>|  
|[<span data-ttu-id="96e69-139">パフォーマンスの問題の特定</span><span class="sxs-lookup"><span data-stu-id="96e69-139">Isolate Performance Problems</span></span>](isolate-performance-problems.md)|<span data-ttu-id="96e69-140">データベースのパフォーマンスの問題を特定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="96e69-140">Describes how to isolate database performance problems.</span></span>|  
|[<span data-ttu-id="96e69-141">ボトルネックの特定</span><span class="sxs-lookup"><span data-stu-id="96e69-141">Identify Bottlenecks</span></span>](identify-bottlenecks.md)|<span data-ttu-id="96e69-142">ボトルネックを特定するために、サーバーのパフォーマンスを監視および追跡する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="96e69-142">Describes how to monitor and track server performance to identify bottlenecks.</span></span>|  
|[<span data-ttu-id="96e69-143">サーバーのパフォーマンスと利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="96e69-143">Server Performance and Activity Monitoring</span></span>](server-performance-and-activity-monitoring.md)|<span data-ttu-id="96e69-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と、Windows のパフォーマンスと利用状況の監視ツールを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="96e69-144">Describes how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows performance and activity monitoring tools.</span></span>|  
|[<span data-ttu-id="96e69-145">実行プランの表示と保存</span><span class="sxs-lookup"><span data-stu-id="96e69-145">Display and Save Execution Plans</span></span>](display-and-save-execution-plans.md)|<span data-ttu-id="96e69-146">実行プランの表示方法と、XML 形式でファイルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="96e69-146">Describes how to display and save execution plans to a file in XML format.</span></span>|  
|[<span data-ttu-id="96e69-147">クエリのストアを使用した、パフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="96e69-147">Monitoring Performance By Using the Query Store</span></span>](monitoring-performance-by-using-the-query-store.md)|<span data-ttu-id="96e69-148">クエリ ストアは、自動的にクエリ、プラン、および実行時統計の履歴をキャプチャし、確認用に保持します。</span><span class="sxs-lookup"><span data-stu-id="96e69-148">The Query Store automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96e69-149">参照</span><span class="sxs-lookup"><span data-stu-id="96e69-149">See Also</span></span>  
 <span data-ttu-id="96e69-150">[エンタープライズ全体の管理の自動化](../../ssms/agent/automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="96e69-150">[Automated Administration Across an Enterprise](../../ssms/agent/automated-administration-across-an-enterprise.md) </span></span>  
 <span data-ttu-id="96e69-151">[データベース エンジン チューニング アドバイザー](database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="96e69-151">[Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="96e69-152">[リソースの利用状況の監視 &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="96e69-152">[Monitor Resource Usage &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 [<span data-ttu-id="96e69-153">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="96e69-153">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
