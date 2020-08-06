---
title: MSSQL_ENG014160 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3351567a31a0a0384ab8957073ab0457ef0ea7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631813"
---
# <a name="mssql_eng014160"></a><span data-ttu-id="cf1b8-102">MSSQL_ENG014160</span><span class="sxs-lookup"><span data-stu-id="cf1b8-102">MSSQL_ENG014160</span></span>
    
## <a name="message-details"></a><span data-ttu-id="cf1b8-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="cf1b8-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf1b8-104">製品名</span><span class="sxs-lookup"><span data-stu-id="cf1b8-104">Product Name</span></span>|<span data-ttu-id="cf1b8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cf1b8-105">SQL Server</span></span>|  
|<span data-ttu-id="cf1b8-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="cf1b8-106">Event ID</span></span>|<span data-ttu-id="cf1b8-107">14160</span><span class="sxs-lookup"><span data-stu-id="cf1b8-107">14160</span></span>|  
|<span data-ttu-id="cf1b8-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="cf1b8-108">Event Source</span></span>|<span data-ttu-id="cf1b8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cf1b8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cf1b8-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="cf1b8-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="cf1b8-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="cf1b8-111">Symbolic Name</span></span>||  
|<span data-ttu-id="cf1b8-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="cf1b8-112">Message Text</span></span>|<span data-ttu-id="cf1b8-113">パブリケーション [%s] のしきい値 [%s:%s] が設定されています。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="cf1b8-114">このパブリケーションに対する 1 つ以上のサブスクリプションの有効期限が切れています。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-114">One or more subscriptions to this publication have expired.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf1b8-115">説明</span><span class="sxs-lookup"><span data-stu-id="cf1b8-115">Explanation</span></span>  
 <span data-ttu-id="cf1b8-116">レプリケーションでは、いくつかの条件に対して警告を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="cf1b8-117">こうした条件には、サブスクリプションの有効期限の残り時間などがあります。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-117">This includes imminent subscription expiration.</span></span> <span data-ttu-id="cf1b8-118">指定した *保有期間*内にサブスクリプションの同期をとらないと、サブスクリプションの有効期限が切れることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-118">Subscriptions can expire if they are not synchronized within a specified *retention period*.</span></span> <span data-ttu-id="cf1b8-119">詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-119">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="cf1b8-120">レプリケーション モニターまたは [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)を使用して警告を有効にするときは、警告を表示するタイミングを決定するしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-120">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="cf1b8-121">指定したしきい値に達するか、そのしきい値を超えた場合、警告がレプリケーション モニターに表示され、イベントが Windows イベント ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-121">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="cf1b8-122">しきい値に達した時点で、SQL Server エージェントの警告を表示させることもできます。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-122">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="cf1b8-123">詳細については、「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」および「[プログラムによるレプリケーションの監視](monitoring-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-123">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf1b8-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="cf1b8-124">User Action</span></span>  
 <span data-ttu-id="cf1b8-125">この問題の解決策は、警告が発生した原因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-125">The resolution for this issue depends on the reason the warning was raised:</span></span>  
  
-   <span data-ttu-id="cf1b8-126">しきい値を超えても、サブスクリプションの有効期限が切れていない場合は、そのサブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-126">If the threshold has been exceeded, but the subscription has not yet expired, synchronize the subscription.</span></span> <span data-ttu-id="cf1b8-127">詳細については、「 [データの同期](synchronize-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-127">For more information, see [Synchronize Data](synchronize-data.md).</span></span>  
  
-   <span data-ttu-id="cf1b8-128">エージェントが実行されていても、変更が適切にレプリケートされていない場合は、サブスクリプションの有効期限が切れる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-128">If the agent has been running, but has not been replicating changes properly, this can cause the subscription to expire.</span></span> <span data-ttu-id="cf1b8-129">トランザクション レプリケーションの場合は、ディストリビューション エージェントとログ リーダー エージェントが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-129">For transactional replication, make sure that the Distribution Agent and Log Reader Agent are running.</span></span> <span data-ttu-id="cf1b8-130">マージ レプリケーションの場合は、マージ エージェントが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-130">For merge replication, make sure the Merge Agent is running.</span></span> <span data-ttu-id="cf1b8-131">これらのエージェントの起動方法については、「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」および「[レプリケーション エージェント実行可能ファイルの概念](concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-131">For information about how to start these agents, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="cf1b8-132">サブスクリプションの有効期限が切れている場合、サブスクリプションの種類と期限切れになってからの期間によって、再初期化するか、削除して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-132">If the subscription has expired, it must either be reinitialized or dropped and re-created, depending on the type of subscription and how long it has been expired.</span></span> <span data-ttu-id="cf1b8-133">詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf1b8-133">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1b8-134">参照</span><span class="sxs-lookup"><span data-stu-id="cf1b8-134">See Also</span></span>  
 [<span data-ttu-id="cf1b8-135">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="cf1b8-135">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
