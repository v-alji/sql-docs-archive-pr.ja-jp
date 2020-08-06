---
title: 'SQL Server: Broker Activation オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4048c2baecaeb4bde7a1e215a15e8c51a60a01bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715234"
---
# <a name="sql-server-broker-activation-object"></a><span data-ttu-id="30475-102">SQL Server: Broker Activation オブジェクト</span><span class="sxs-lookup"><span data-stu-id="30475-102">SQL Server, Broker Activation Object</span></span>
  <span data-ttu-id="30475-103">**SQLServer:BrokerActivation** パフォーマンス オブジェクトには、ストアド プロシージャのアクティブ化に関する情報を報告するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="30475-103">The **SQLServer:BrokerActivation** performance object contains performance counters that report information on stored procedure activation.</span></span> <span data-ttu-id="30475-104">次の表は、このオブジェクトに含まれているカウンターを示します。</span><span class="sxs-lookup"><span data-stu-id="30475-104">The table below lists the counters that this object contains.</span></span>  
  
|<span data-ttu-id="30475-105">SQL Server Broker Activation カウンター</span><span class="sxs-lookup"><span data-stu-id="30475-105">SQL Server Broker Activation counters</span></span>|<span data-ttu-id="30475-106">説明</span><span class="sxs-lookup"><span data-stu-id="30475-106">Description</span></span>|  
|-------------------------------------------|-----------------|  
|<span data-ttu-id="30475-107">**Stored Procedures Invoked/sec**</span><span class="sxs-lookup"><span data-stu-id="30475-107">**Stored Procedures Invoked/sec**</span></span>|<span data-ttu-id="30475-108">インスタンス内のすべてのキュー モニターによって 1 秒間に呼び出されたアクティブ化ストアド プロシージャの合計数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="30475-108">This counter reports the total number of activation stored procedures invoked by all queue monitors in the instance per second.</span></span>|  
|<span data-ttu-id="30475-109">**Task Limit Reached**</span><span class="sxs-lookup"><span data-stu-id="30475-109">**Task Limit Reached**</span></span>|<span data-ttu-id="30475-110">キューに登録できる最大数のタスクが既に実行されているために、キュー モニターで新しいタスクの開始に失敗した合計回数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="30475-110">This counter reports the total number of times that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.</span></span>|  
|<span data-ttu-id="30475-111">**Task Limit Reached/sec**</span><span class="sxs-lookup"><span data-stu-id="30475-111">**Task Limit Reached/sec**</span></span>|<span data-ttu-id="30475-112">キューに登録できる最大数のタスクが既に実行されているために、キュー モニターで 1 秒間に新しいタスクの開始に失敗した回数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="30475-112">This counter reports the number of times per second that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.</span></span>|  
|<span data-ttu-id="30475-113">**Tasks Aborted/sec**</span><span class="sxs-lookup"><span data-stu-id="30475-113">**Tasks Aborted/sec**</span></span>|<span data-ttu-id="30475-114">エラーが発生して終了したか、メッセージを受信できないためにキュー モニターによって中断されたアクティブ化ストアド プロシージャのタスク数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="30475-114">This counter reports the number of activation stored procedure tasks that end with an error, or are aborted by a queue monitor for failing to receive messages.</span></span>|  
|<span data-ttu-id="30475-115">**Tasks Running**</span><span class="sxs-lookup"><span data-stu-id="30475-115">**Tasks Running**</span></span>|<span data-ttu-id="30475-116">現在実行中のアクティブ化ストアド プロシージャの数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="30475-116">This counter reports the number of activation stored procedures that are currently running.</span></span>|  
|<span data-ttu-id="30475-117">**Tasks Started/sec**</span><span class="sxs-lookup"><span data-stu-id="30475-117">**Tasks Started/sec**</span></span>|<span data-ttu-id="30475-118">インスタンス内のすべてのキュー モニターによって 1 秒間に開始されたアクティブ化ストアド プロシージャの数が報告されます。</span><span class="sxs-lookup"><span data-stu-id="30475-118">This counter reports the number of activation stored procedures started per second by all queue monitors in the instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30475-119">参照</span><span class="sxs-lookup"><span data-stu-id="30475-119">See Also</span></span>  
 <span data-ttu-id="30475-120">[sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="30475-120">[sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql) </span></span>  
 <span data-ttu-id="30475-121">[sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="30475-121">[sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql) </span></span>  
 [<span data-ttu-id="30475-122">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="30475-122">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
