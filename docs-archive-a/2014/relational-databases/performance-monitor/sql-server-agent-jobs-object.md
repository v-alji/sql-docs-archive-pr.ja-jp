---
title: SQL Server エージェントの Jobs オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 82ee57eba20d44c08eadc125e9dfd69e73c35751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633799"
---
# <a name="sql-server-agent-jobs-object"></a><span data-ttu-id="d36f7-102">SQL Server エージェントの Jobs オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d36f7-102">SQL Server Agent, Jobs Object</span></span>
  <span data-ttu-id="d36f7-103">SQL Server エージェントの **Jobs** パフォーマンス オブジェクトには、SQL Server エージェントのジョブについての情報を報告するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d36f7-103">The SQL Server Agent **Jobs** performance object contains performance counters that report information about SQL Server Agent jobs.</span></span> <span data-ttu-id="d36f7-104">次の表は、このオブジェクトに含まれているカウンターを示します。</span><span class="sxs-lookup"><span data-stu-id="d36f7-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="d36f7-105">次の表には **SQLAgent:Jobs** カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d36f7-105">The table below contains the **SQLAgent:Jobs** counters.</span></span>  
  
|<span data-ttu-id="d36f7-106">名前</span><span class="sxs-lookup"><span data-stu-id="d36f7-106">Name</span></span>|<span data-ttu-id="d36f7-107">説明</span><span class="sxs-lookup"><span data-stu-id="d36f7-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="d36f7-108">**Active Jobs**</span><span class="sxs-lookup"><span data-stu-id="d36f7-108">**Active Jobs**</span></span>|<span data-ttu-id="d36f7-109">このカウンターは、現在実行中のジョブの数を報告します。</span><span class="sxs-lookup"><span data-stu-id="d36f7-109">This counter reports the number of jobs currently running.</span></span>|  
|<span data-ttu-id="d36f7-110">**Failed jobs**</span><span class="sxs-lookup"><span data-stu-id="d36f7-110">**Failed jobs**</span></span>|<span data-ttu-id="d36f7-111">このカウンターは、失敗して終了したジョブの数を報告します。</span><span class="sxs-lookup"><span data-stu-id="d36f7-111">This counter reports the number of jobs that exited with failure.</span></span>|  
|<span data-ttu-id="d36f7-112">**Job success rate**</span><span class="sxs-lookup"><span data-stu-id="d36f7-112">**Job success rate**</span></span>|<span data-ttu-id="d36f7-113">このカウンターは、実行済みジョブのうち問題なく完了したジョブの割合を報告します。</span><span class="sxs-lookup"><span data-stu-id="d36f7-113">This counter reports the percentage of executed jobs that completed successfully.</span></span>|  
|<span data-ttu-id="d36f7-114">**Jobs activated/minute**</span><span class="sxs-lookup"><span data-stu-id="d36f7-114">**Jobs activated/minute**</span></span>|<span data-ttu-id="d36f7-115">このカウンターは、最後の 1 分間に起動されたジョブの数を報告します。</span><span class="sxs-lookup"><span data-stu-id="d36f7-115">This counter reports the number of jobs launched within the last minute.</span></span>|  
|<span data-ttu-id="d36f7-116">**Queued jobs**</span><span class="sxs-lookup"><span data-stu-id="d36f7-116">**Queued jobs**</span></span>|<span data-ttu-id="d36f7-117">このカウンターは、SQL Server エージェントで実行する準備が整っているジョブで、まだ実行が開始されていないジョブの数を報告します。</span><span class="sxs-lookup"><span data-stu-id="d36f7-117">This counter reports the number of jobs that are ready for SQL Server Agent to run, but which have not yet started running.</span></span>|  
|<span data-ttu-id="d36f7-118">**Successful jobs**</span><span class="sxs-lookup"><span data-stu-id="d36f7-118">**Successful jobs**</span></span>|<span data-ttu-id="d36f7-119">このカウンターは、問題なく終了したジョブの数を報告します。</span><span class="sxs-lookup"><span data-stu-id="d36f7-119">This counter reports the number of jobs that exited with success.</span></span>|  
  
 <span data-ttu-id="d36f7-120">オブジェクトの各カウンターには、次のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d36f7-120">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="d36f7-121">インスタンス</span><span class="sxs-lookup"><span data-stu-id="d36f7-121">Instance</span></span>|<span data-ttu-id="d36f7-122">説明</span><span class="sxs-lookup"><span data-stu-id="d36f7-122">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d36f7-123">**_Total**</span><span class="sxs-lookup"><span data-stu-id="d36f7-123">**_Total**</span></span>|<span data-ttu-id="d36f7-124">すべてのジョブの情報です。</span><span class="sxs-lookup"><span data-stu-id="d36f7-124">Information for all jobs.</span></span>|  
|<span data-ttu-id="d36f7-125">**警告**</span><span class="sxs-lookup"><span data-stu-id="d36f7-125">**Alerts**</span></span>|<span data-ttu-id="d36f7-126">警告によって開始されたジョブの情報です。</span><span class="sxs-lookup"><span data-stu-id="d36f7-126">Information for jobs started by alerts.</span></span>|  
|<span data-ttu-id="d36f7-127">**Others**</span><span class="sxs-lookup"><span data-stu-id="d36f7-127">**Others**</span></span>|<span data-ttu-id="d36f7-128">警告またはスケジュールによって開始されたジョブの情報です。</span><span class="sxs-lookup"><span data-stu-id="d36f7-128">Information for jobs that were not started by alerts or schedules.</span></span> <span data-ttu-id="d36f7-129">通常、これらのジョブは **sp_start_job**を使用して手動で開始されます。</span><span class="sxs-lookup"><span data-stu-id="d36f7-129">Typically these are jobs started manually using **sp_start_job**.</span></span>|  
|<span data-ttu-id="d36f7-130">**スケジュール**</span><span class="sxs-lookup"><span data-stu-id="d36f7-130">**Schedules**</span></span>|<span data-ttu-id="d36f7-131">スケジュールによって開始されたジョブの情報です。</span><span class="sxs-lookup"><span data-stu-id="d36f7-131">Information for jobs started by schedules.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d36f7-132">参照</span><span class="sxs-lookup"><span data-stu-id="d36f7-132">See Also</span></span>  
 <span data-ttu-id="d36f7-133">[ジョブの実装](../../ssms/agent/implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="d36f7-133">[Implement Jobs](../../ssms/agent/implement-jobs.md) </span></span>  
 <span data-ttu-id="d36f7-134">[パフォーマンス オブジェクトの使用](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="d36f7-134">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="d36f7-135">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="d36f7-135">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
