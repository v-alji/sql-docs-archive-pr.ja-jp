---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c926d05be9613ff559f119484fa5e238d71d861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631820"
---
# <a name="mssql_eng014150"></a><span data-ttu-id="4c842-102">MSSQL_ENG014150</span><span class="sxs-lookup"><span data-stu-id="4c842-102">MSSQL_ENG014150</span></span>
    
## <a name="message-details"></a><span data-ttu-id="4c842-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="4c842-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c842-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4c842-104">Product Name</span></span>|<span data-ttu-id="4c842-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4c842-105">SQL Server</span></span>|  
|<span data-ttu-id="4c842-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4c842-106">Event ID</span></span>|<span data-ttu-id="4c842-107">14150</span><span class="sxs-lookup"><span data-stu-id="4c842-107">14150</span></span>|  
|<span data-ttu-id="4c842-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4c842-108">Event Source</span></span>|<span data-ttu-id="4c842-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4c842-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4c842-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4c842-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="4c842-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4c842-111">Symbolic Name</span></span>||  
|<span data-ttu-id="4c842-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4c842-112">Message Text</span></span>|<span data-ttu-id="4c842-113">レプリケーション-%s: エージェント %s が成功しました。</span><span class="sxs-lookup"><span data-stu-id="4c842-113">Replication-%s: agent %s succeeded.</span></span> <span data-ttu-id="4c842-114">%s</span><span class="sxs-lookup"><span data-stu-id="4c842-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4c842-115">説明</span><span class="sxs-lookup"><span data-stu-id="4c842-115">Explanation</span></span>  
 <span data-ttu-id="4c842-116">このメッセージは、レプリケーション エージェントの実行が正常に完了したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="4c842-116">This message indicates that a replication agent has successfully finished running.</span></span> <span data-ttu-id="4c842-117">レプリケーションでは、次のエージェントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c842-117">Replication uses the following agents:</span></span>  
  
-   <span data-ttu-id="4c842-118">スナップショット エージェント。</span><span class="sxs-lookup"><span data-stu-id="4c842-118">The Snapshot Agent.</span></span> <span data-ttu-id="4c842-119">すべてのパブリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c842-119">This agent is used by all publications.</span></span>  
  
-   <span data-ttu-id="4c842-120">ログ リーダー エージェント。</span><span class="sxs-lookup"><span data-stu-id="4c842-120">The Log Reader Agent.</span></span> <span data-ttu-id="4c842-121">すべてのトランザクション パブリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c842-121">This agent is used by all transactional publications.</span></span>  
  
-   <span data-ttu-id="4c842-122">キュー リーダー エージェント。</span><span class="sxs-lookup"><span data-stu-id="4c842-122">The Queue Reader Agent.</span></span> <span data-ttu-id="4c842-123">キュー更新サブスクリプションに有効なトランザクション パブリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c842-123">This agent is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="4c842-124">ディストリビューション エージェント。</span><span class="sxs-lookup"><span data-stu-id="4c842-124">The Distribution Agent.</span></span> <span data-ttu-id="4c842-125">サブスクリプションをトランザクション パブリケーションおよびスナップショット パブリケーションと同期します。</span><span class="sxs-lookup"><span data-stu-id="4c842-125">This agent synchronizes subscriptions to transactional and snapshot publications.</span></span>  
  
-   <span data-ttu-id="4c842-126">マージ エージェント。</span><span class="sxs-lookup"><span data-stu-id="4c842-126">The Merge Agent.</span></span> <span data-ttu-id="4c842-127">サブスクリプションをマージ パブリケーションと同期します。</span><span class="sxs-lookup"><span data-stu-id="4c842-127">This agent synchronizes subscriptions to merge publications.</span></span>  
  
-   <span data-ttu-id="4c842-128">レプリケーション メンテナンス ジョブ。</span><span class="sxs-lookup"><span data-stu-id="4c842-128">Replication maintenance jobs.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4c842-129">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4c842-129">User Action</span></span>  
 <span data-ttu-id="4c842-130">通常、ログ リーダー エージェント、キュー リーダー エージェント、およびディストリビューション エージェントは連続実行しますが、他のエージェントは、要求時に実行するかスケジュールに合わせて実行します。</span><span class="sxs-lookup"><span data-stu-id="4c842-130">The Log Reader Agent, Queue Reader Agent, and Distribution Agent typically run continuously, whereas the other agents typically run on demand or on a schedule.</span></span> <span data-ttu-id="4c842-131">エージェントが実行を完了したかどうかわからない場合は、エージェントの状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="4c842-131">If you do not expect an agent to have completed a run, check the status of the agent.</span></span> <span data-ttu-id="4c842-132">詳細については、「 [Monitor Replication Agents](agents/replication-agents-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c842-132">For more information, see [Monitor Replication Agents](agents/replication-agents-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c842-133">参照</span><span class="sxs-lookup"><span data-stu-id="4c842-133">See Also</span></span>  
 <span data-ttu-id="4c842-134">[レプリケーション エージェントの管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="4c842-134">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="4c842-135">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="4c842-135">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="4c842-136">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="4c842-136">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="4c842-137">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="4c842-137">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="4c842-138">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="4c842-138">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="4c842-139">[レプリケーション キュー リーダー エージェント](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="4c842-139">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="4c842-140">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="4c842-140">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
