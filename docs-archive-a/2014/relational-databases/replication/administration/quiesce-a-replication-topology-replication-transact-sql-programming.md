---
title: レプリケーション トポロジの停止 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- administering replication, quiescing
- quiesce [SQL Server replication]
- transactional replication, backup and restore
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12f0fb8ee3a6118e03799d17836573fb5c733df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736247"
---
# <a name="quiesce-a-replication-topology-replication-transact-sql-programming"></a><span data-ttu-id="7de62-102">レプリケーション トポロジの停止 (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="7de62-102">Quiesce a Replication Topology (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="7de62-103"> システムの*停止*を実行するには、すべてのノードのパブリッシュされたテーブルで処理を停止し、他のすべてのノードからのすべての変更を各ノードが受信しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7de62-103">*Quiescing* a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes.</span></span> <span data-ttu-id="7de62-104">このトピックでは、いくつかの管理タスクで必要とされる、レプリケーション トポロジの停止方法や、他のノードからのすべての変更をノードが受け取ったことを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7de62-104">This topic explains how to quiesce a replication topology, which is required for a number of administrative tasks, and how to ensure that a node has received all changes from other nodes.</span></span>  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-read-only-subscriptions"></a><span data-ttu-id="7de62-105">読み取り専用サブスクライバーを含むトランザクション レプリケーション トポロジを停止するには</span><span class="sxs-lookup"><span data-stu-id="7de62-105">To quiesce a transactional replication topology with read-only subscriptions</span></span>  
  
1.  <span data-ttu-id="7de62-106">パブリッシャーで、すべてのパブリッシュされたテーブルの処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="7de62-106">Stop activity on all published tables at the Publisher.</span></span>  
  
2.  <span data-ttu-id="7de62-107">パブリッシャー側のパブリケーション データベースに対して、[sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-107">At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).</span></span>  
  
3.  <span data-ttu-id="7de62-108">パブリッシャー側のパブリケーション データベースに対して、 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-108">At the Publisher on the publication database, execute [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).</span></span>  
  
4.  <span data-ttu-id="7de62-109">各サブスクライバーがトレーサー トークンを受け取ったことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7de62-109">Ensure that each Subscriber has received the tracer token.</span></span>  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-updatable-subscriptions"></a><span data-ttu-id="7de62-110">更新可能サブスクリプションを含むトランザクション レプリケーション トポロジを停止するには</span><span class="sxs-lookup"><span data-stu-id="7de62-110">To quiesce a transactional replication topology with updatable subscriptions</span></span>  
  
1.  <span data-ttu-id="7de62-111">パブリッシャーおよびすべてのサブスクライバーで、すべてのパブリッシュされたテーブルの処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="7de62-111">Stop activity on all published tables at the Publisher and all Subscribers.</span></span>  
  
2.  <span data-ttu-id="7de62-112">キュー更新サブスクリプションを使用するサブスクライバーがある場合</span><span class="sxs-lookup"><span data-stu-id="7de62-112">If any Subscribers use queued updating subscriptions:</span></span>  
  
    1.  <span data-ttu-id="7de62-113">キュー リーダー エージェントが連続モードで実行されていない場合は、エージェントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-113">If the Queue Reader Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="7de62-114">エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7de62-114">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
    2.  <span data-ttu-id="7de62-115">キューが空であることを確認するには、各サブスクライバーで [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-115">To verify that the queue is empty, execute [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) at each Subscriber.</span></span>  
  
3.  <span data-ttu-id="7de62-116">パブリッシャー側のパブリケーション データベースに対して、 [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-116">At the Publisher on the publication database, execute [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).</span></span>  
  
4.  <span data-ttu-id="7de62-117">パブリッシャー側のパブリケーション データベースに対して、 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-117">At the Publisher on the publication database, execute [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).</span></span>  
  
5.  <span data-ttu-id="7de62-118">各サブスクライバーがトレーサー トークンを受け取ったことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7de62-118">Ensure that each Subscriber has received the tracer token.</span></span>  
  
### <a name="to-quiesce-a-peer-to-peer-transactional-replication-topology"></a><span data-ttu-id="7de62-119">ピア ツー ピアのトランザクション レプリケーション トポロジを停止するには</span><span class="sxs-lookup"><span data-stu-id="7de62-119">To quiesce a peer-to-peer transactional replication topology</span></span>  
  
1.  <span data-ttu-id="7de62-120">すべてのノードで、すべてのパブリッシュされたテーブルの処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="7de62-120">Stop activity on all published tables at all nodes.</span></span>  
  
2.  <span data-ttu-id="7de62-121">トポロジ内の各パブリケーション データベースで [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-121">Execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) on each publication database in the topology.</span></span>  
  
3.  <span data-ttu-id="7de62-122">ログ リーダー エージェントまたはディストリビューション エージェントが連続モードで実行されていない場合は、エージェントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-122">If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="7de62-123">ログ リーダー エージェントは、ディストリビューション エージェントの前に開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7de62-123">The Log Reader Agent must be started before the Distribution Agent.</span></span> <span data-ttu-id="7de62-124">エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7de62-124">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
4.  <span data-ttu-id="7de62-125">トポロジ内の各パブリケーション データベースで [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-125">Execute [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) on each publication database in the topology.</span></span> <span data-ttu-id="7de62-126">結果セットに他のノードからの応答が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7de62-126">Ensure that the result set contains responses from each of the other nodes.</span></span>  
  
### <a name="to-ensure-a-peer-to-peer-node-has-received-all-prior-changes"></a><span data-ttu-id="7de62-127">ピア ツー ピア ノードが前の変更をすべて受け取ったことを確認するには</span><span class="sxs-lookup"><span data-stu-id="7de62-127">To ensure a peer-to-peer node has received all prior changes</span></span>  
  
1.  <span data-ttu-id="7de62-128">チェックする対象のノードのパブリケーション データベースで [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-128">Execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) on the publication database at the node you are checking.</span></span>  
  
2.  <span data-ttu-id="7de62-129">ログ リーダー エージェントまたはディストリビューション エージェントが連続モードで実行されていない場合は、エージェントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-129">If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="7de62-130">ログ リーダー エージェントは、ディストリビューション エージェントの前に開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7de62-130">The Log Reader Agent must be started before the Distribution Agent.</span></span> <span data-ttu-id="7de62-131">エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7de62-131">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
3.  <span data-ttu-id="7de62-132">チェックする対象のノードのパブリケーション データベースで [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7de62-132">Execute [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) on the publication database at the node you are checking.</span></span> <span data-ttu-id="7de62-133">結果セットに他のノードからの応答が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7de62-133">Ensure that the result set contains responses from each of the other nodes.</span></span>  
  
### <a name="to-quiesce-a-merge-replication-topology"></a><span data-ttu-id="7de62-134">マージ レプリケーション トポロジを停止するには</span><span class="sxs-lookup"><span data-stu-id="7de62-134">To quiesce a merge replication topology</span></span>  
  
1.  <span data-ttu-id="7de62-135">パブリッシャーおよびすべてのサブスクライバーで、すべてのパブリッシュされたテーブルの処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="7de62-135">Stop activity on all published tables at the Publisher and at all Subscribers.</span></span>  
  
2.  <span data-ttu-id="7de62-136">各サブスクリプションに対して、マージ エージェントを 2 回実行します。すべてのサブスクリプションを 1 回同期させてから、各サブスクリプションをもう 1 回同期させます。</span><span class="sxs-lookup"><span data-stu-id="7de62-136">Run the Merge Agent for each subscription two times: synchronize all subscriptions once and then synchronize each subscription a second time.</span></span> <span data-ttu-id="7de62-137">これにより、すべての変更がすべてのノードに確実にレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="7de62-137">This ensures that all changes are replicated to all nodes.</span></span> <span data-ttu-id="7de62-138">エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7de62-138">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7de62-139">同期中に競合が発生した場合は、マージ エージェントを 2 回実行した後でも、競合の解決に必要な変更が全ノードに反映されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7de62-139">If conflicts occur during synchronization, it is possible that changes required by conflict resolution will not be propagated to all nodes after running the Merge Agent two times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de62-140">参照</span><span class="sxs-lookup"><span data-stu-id="7de62-140">See Also</span></span>  
 <span data-ttu-id="7de62-141">[ピア ツー ピア トポロジの管理 &#40;レプリケーション Transact-SQL プログラミング&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="7de62-141">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="7de62-142">待機時間を計測して Connections for Transactional Replication を検証します。</span><span class="sxs-lookup"><span data-stu-id="7de62-142">Measure Latency and Validate Connections for Transactional Replication</span></span>](../monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
