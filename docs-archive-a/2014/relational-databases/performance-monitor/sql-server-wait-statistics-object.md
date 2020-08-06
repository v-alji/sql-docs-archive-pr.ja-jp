---
title: 'SQL Server: Wait Statistics オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5cfd2f1309cb118896ff7951b7f82feb38de60e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713069"
---
# <a name="sql-server-wait-statistics-object"></a><span data-ttu-id="1e9fd-102">SQL Server: Wait Statistics オブジェクト</span><span class="sxs-lookup"><span data-stu-id="1e9fd-102">SQL Server, Wait Statistics Object</span></span>
  <span data-ttu-id="1e9fd-103">**SQLServer:Wait Statistics** パフォーマンス オブジェクトには、待機状態に関する情報を報告するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-103">The **SQLServer:Wait Statistics** performance object contains performance counters that report information about wait status.</span></span>  
  
 <span data-ttu-id="1e9fd-104">Wait Statistics オブジェクトに含まれるカウンターを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-104">The table below lists the counters that the Wait Statistics object contains.</span></span>  
  
|<span data-ttu-id="1e9fd-105">SQL Server Wait Statistics カウンター</span><span class="sxs-lookup"><span data-stu-id="1e9fd-105">SQL Server Wait Statistics counters</span></span>|<span data-ttu-id="1e9fd-106">説明</span><span class="sxs-lookup"><span data-stu-id="1e9fd-106">Description</span></span>|  
|-----------------------------------------|-----------------|  
|<span data-ttu-id="1e9fd-107">**Lock waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-107">**Lock waits**</span></span>|<span data-ttu-id="1e9fd-108">ロックを待機しているプロセスの統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-108">Statistics for processes waiting on a lock.</span></span>|  
|<span data-ttu-id="1e9fd-109">**Log buffer waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-109">**Log buffer waits**</span></span>|<span data-ttu-id="1e9fd-110">ログ バッファーが使用可能になるのを待機しているプロセスの統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-110">Statistics for processes waiting for log buffer to be available.</span></span>|  
|<span data-ttu-id="1e9fd-111">**Log write waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-111">**Log write waits**</span></span>|<span data-ttu-id="1e9fd-112">ログ バッファーへの書き込みを待機しているプロセスの統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-112">Statistics for processes waiting for log buffer to be written.</span></span>|  
|<span data-ttu-id="1e9fd-113">**Memory grant queue waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-113">**Memory grant queue waits**</span></span>|<span data-ttu-id="1e9fd-114">メモリ許可が使用可能になるのを待機しているプロセスの統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-114">Statistics for processes waiting for memory grant to become available.</span></span>|  
|<span data-ttu-id="1e9fd-115">**Network IO waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-115">**Network IO waits**</span></span>|<span data-ttu-id="1e9fd-116">ネットワーク I/O の待機に関する統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-116">Statistics relevant to wait on network I/O.</span></span>|  
|<span data-ttu-id="1e9fd-117">**Non-Page latch waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-117">**Non-Page latch waits**</span></span>|<span data-ttu-id="1e9fd-118">ページ以外のラッチに関する統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-118">Statistics relevant to non-page latches.</span></span>|  
|<span data-ttu-id="1e9fd-119">**Page IO latch waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-119">**Page IO latch waits**</span></span>|<span data-ttu-id="1e9fd-120">ページ I/O ラッチに関する統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-120">Statistics relevant to page I/O latches.</span></span>|  
|<span data-ttu-id="1e9fd-121">**Page latch waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-121">**Page latch waits**</span></span>|<span data-ttu-id="1e9fd-122">ページ ラッチに関する統計。I/O ラッチは含みません。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-122">Statistics relevant to page latches, not including I/O latches.</span></span>|  
|<span data-ttu-id="1e9fd-123">**Thread-safe memory objects waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-123">**Thread-safe memory objects waits**</span></span>|<span data-ttu-id="1e9fd-124">スレッドセーフなメモリ割り当てを待機しているプロセスの統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-124">Statistics for processes waiting on thread-safe memory allocators.</span></span>|  
|<span data-ttu-id="1e9fd-125">**Transaction ownership waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-125">**Transaction ownership waits**</span></span>|<span data-ttu-id="1e9fd-126">トランザクションへのアクセスを同期するプロセスに関する統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-126">Statistics relevant to processes synchronizing access to transaction.</span></span>|  
|<span data-ttu-id="1e9fd-127">**Wait for the worker**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-127">**Wait for the worker**</span></span>|<span data-ttu-id="1e9fd-128">ワーカーが使用可能になるのを待機しているプロセスに関する統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-128">Statistics relevant to processes waiting for worker to become available.</span></span>|  
|<span data-ttu-id="1e9fd-129">**Workspace synchronization waits**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-129">**Workspace synchronization waits**</span></span>|<span data-ttu-id="1e9fd-130">ワークスペースへのアクセスを同期するプロセスに関する統計。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-130">Statistics relevant to processes synchronizing access to workspace.</span></span>|  
  
 <span data-ttu-id="1e9fd-131">オブジェクトの各カウンターには、次のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-131">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="1e9fd-132">Item</span><span class="sxs-lookup"><span data-stu-id="1e9fd-132">Item</span></span>|<span data-ttu-id="1e9fd-133">説明</span><span class="sxs-lookup"><span data-stu-id="1e9fd-133">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1e9fd-134">**平均待機時間 (ミリ秒)**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-134">**Average wait time (ms)**</span></span>|<span data-ttu-id="1e9fd-135">選択した待機の種類の平均時間。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-135">Average time for the selected type of wait.</span></span>|  
|<span data-ttu-id="1e9fd-136">**1 秒あたりの累積待機時間 (ミリ秒)**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-136">**Cumulative wait time (ms) per second**</span></span>|<span data-ttu-id="1e9fd-137">選択した待機の種類の 1 秒あたりに集計された待機時間。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-137">Aggregated wait time per second, for the selected type of wait.</span></span>|  
|<span data-ttu-id="1e9fd-138">**待機中**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-138">**Waits in progress**</span></span>|<span data-ttu-id="1e9fd-139">次の種類で現在待機しているプロセスの数。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-139">Number of processes currently waiting on the following type.</span></span>|  
|<span data-ttu-id="1e9fd-140">**1 秒あたりに開始された待機回数**</span><span class="sxs-lookup"><span data-stu-id="1e9fd-140">**Waits started per second**</span></span>|<span data-ttu-id="1e9fd-141">選択した待機の種類の 1 秒あたりに開始された待機の回数。</span><span class="sxs-lookup"><span data-stu-id="1e9fd-141">Number of waits started per second of the selected type of wait.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e9fd-142">参照</span><span class="sxs-lookup"><span data-stu-id="1e9fd-142">See Also</span></span>  
 [<span data-ttu-id="1e9fd-143">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="1e9fd-143">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
