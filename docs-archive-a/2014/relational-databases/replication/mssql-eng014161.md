---
title: MSSQL_ENG014161 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014161 error
ms.assetid: 4b983e76-bb77-43c5-b44b-19919d3da619
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8cf85181e444385e1a3908761ba71414b68cf3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630923"
---
# <a name="mssql_eng014161"></a><span data-ttu-id="9434a-102">MSSQL_ENG014161</span><span class="sxs-lookup"><span data-stu-id="9434a-102">MSSQL_ENG014161</span></span>
    
## <a name="message-details"></a><span data-ttu-id="9434a-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="9434a-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9434a-104">製品名</span><span class="sxs-lookup"><span data-stu-id="9434a-104">Product Name</span></span>|<span data-ttu-id="9434a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9434a-105">SQL Server</span></span>|  
|<span data-ttu-id="9434a-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="9434a-106">Event ID</span></span>|<span data-ttu-id="9434a-107">14161</span><span class="sxs-lookup"><span data-stu-id="9434a-107">14161</span></span>|  
|<span data-ttu-id="9434a-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="9434a-108">Event Source</span></span>|<span data-ttu-id="9434a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9434a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9434a-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9434a-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="9434a-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="9434a-111">Symbolic Name</span></span>||  
|<span data-ttu-id="9434a-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="9434a-112">Message Text</span></span>|<span data-ttu-id="9434a-113">パブリケーション [%s] のしきい値 [%s:%s] が設定されています。</span><span class="sxs-lookup"><span data-stu-id="9434a-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="9434a-114">ログ リーダーとディストリビューション エージェントが実行されており、待機時間の要件に適合することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9434a-114">Make sure that the logreader and distribution agents are running and can match the latency requirement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9434a-115">説明</span><span class="sxs-lookup"><span data-stu-id="9434a-115">Explanation</span></span>  
 <span data-ttu-id="9434a-116">レプリケーションでは、いくつかの条件に対して警告を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="9434a-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="9434a-117">これには、トランザクション サブスクリプションに指定した待機時間の超過も含まれます。</span><span class="sxs-lookup"><span data-stu-id="9434a-117">This includes exceeding a specified latency for transactional subscriptions.</span></span> <span data-ttu-id="9434a-118">待機時間とは、パブリッシャーでデータ変更がコミットされてから、サブスクライバーで対応する変更がコミットされるまでの経過時間です。</span><span class="sxs-lookup"><span data-stu-id="9434a-118">Latency is the period of time that elapses between a data change being committed at the Publisher and the corresponding change being committed at the Subscriber.</span></span>  
  
 <span data-ttu-id="9434a-119">レプリケーション モニターまたは [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)を使用して警告を有効にするときは、警告を表示するタイミングを決定するしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="9434a-119">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="9434a-120">指定したしきい値に達するか、そのしきい値を超えた場合、警告がレプリケーション モニターに表示され、イベントが Windows イベント ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9434a-120">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="9434a-121">しきい値に達した時点で、SQL Server エージェントの警告を表示させることもできます。</span><span class="sxs-lookup"><span data-stu-id="9434a-121">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="9434a-122">詳細については、「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」および「[プログラムによるレプリケーションの監視](monitoring-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9434a-122">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9434a-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="9434a-123">User Action</span></span>  
 <span data-ttu-id="9434a-124">サブスクリプションが待機時間のしきい値を超えた場合は、システムでパフォーマンスの問題が発生しているかどうか、またはしきい値を調整する必要があるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9434a-124">If a subscription exceeds a latency threshold, you must determine whether there is a performance issue with the system or whether the threshold should be adjusted.</span></span> <span data-ttu-id="9434a-125">レプリケーションを構成したら、パフォーマンス基準を策定します。これにより、アプリケーションおよびトポロジにおける通常のワークロードに対するレプリケーションの動作方法について判断できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9434a-125">After you configure replication, develop a performance baseline that will let you determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="9434a-126">このパフォーマンス基準には待機時間を組み入れ、適切なしきい値を設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9434a-126">Include latency in this baseline so that you can set an appropriate value for the threshold.</span></span>  
  
 <span data-ttu-id="9434a-127">しきい値が適切でも、その値を超えた場合は、システム内のパフォーマンスのボトルネックになる部分を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9434a-127">If the threshold value is appropriate, but it is being exceeded, you must determine where the performance bottleneck is in the system.</span></span> <span data-ttu-id="9434a-128">レプリケーション パフォーマンスの監視とトラブルシューティングを行う方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9434a-128">For more information about how to monitor and troubleshoot replication performance, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9434a-129">待機時間を計測して Connections for Transactional Replication を検証します。</span><span class="sxs-lookup"><span data-stu-id="9434a-129">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
-   [<span data-ttu-id="9434a-130">レプリケーション モニターを使用したパフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="9434a-130">Monitor Performance with Replication Monitor</span></span>](monitor/monitor-performance-with-replication-monitor.md)  
  
## <a name="see-also"></a><span data-ttu-id="9434a-131">参照</span><span class="sxs-lookup"><span data-stu-id="9434a-131">See Also</span></span>  
 [<span data-ttu-id="9434a-132">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="9434a-132">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
