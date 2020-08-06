---
title: XTP ガベージコレクション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 341a45c1c103f154672bb01a0648339562ee9750
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714261"
---
# <a name="xtp-garbage-collection"></a><span data-ttu-id="e1957-102">XTP Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="e1957-102">XTP Garbage Collection</span></span>
  <span data-ttu-id="e1957-103">XTP Garbage Collection パフォーマンス オブジェクトには、XTP エンジンのガベージ コレクターに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1957-103">The XTP Garbage Collection performance object contains counters related to the XTP engine's garbage collector.</span></span>  
  
 <span data-ttu-id="e1957-104">次の表では、 **XTP ガベージコレクション**カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e1957-104">This table describes the **XTP garbage Collection** counters.</span></span>  
  
|<span data-ttu-id="e1957-105">カウンター</span><span class="sxs-lookup"><span data-stu-id="e1957-105">Counter</span></span>|<span data-ttu-id="e1957-106">説明</span><span class="sxs-lookup"><span data-stu-id="e1957-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1957-107">**Dusty corner scan retries/sec (GC-issued)**</span><span class="sxs-lookup"><span data-stu-id="e1957-107">**Dusty corner scan retries/sec (GC-issued)**</span></span>|<span data-ttu-id="e1957-108">ガベージ コレクターによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-108">The number of scan retries due to write conflicts during dusty corner sweeps issued by the garbage collector (on average), per second.</span></span> <span data-ttu-id="e1957-109">これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。</span><span class="sxs-lookup"><span data-stu-id="e1957-109">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="e1957-110">**Main GC work items/sec**</span><span class="sxs-lookup"><span data-stu-id="e1957-110">**Main GC work items/sec**</span></span>|<span data-ttu-id="e1957-111">メイン GC スレッドで処理された作業項目の数です。</span><span class="sxs-lookup"><span data-stu-id="e1957-111">The number of work items processed by the main GC thread.</span></span>|  
|<span data-ttu-id="e1957-112">**Parallel GC work item/sec**</span><span class="sxs-lookup"><span data-stu-id="e1957-112">**Parallel GC work item/sec**</span></span>|<span data-ttu-id="e1957-113">並列スレッドが GC 作業項目を実行した回数です。</span><span class="sxs-lookup"><span data-stu-id="e1957-113">The number of times a parallel thread has executed a GC work item.</span></span>|  
|<span data-ttu-id="e1957-114">**Rows processed/sec**</span><span class="sxs-lookup"><span data-stu-id="e1957-114">**Rows processed/sec**</span></span>|<span data-ttu-id="e1957-115">ガベージ コレクターにより 1 秒間に処理された (平均) 行数です。</span><span class="sxs-lookup"><span data-stu-id="e1957-115">The number of rows processed by the garbage collector (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-116">**Rows processed/sec (first in bucket and removed)**</span><span class="sxs-lookup"><span data-stu-id="e1957-116">**Rows processed/sec (first in bucket and removed)**</span></span>|<span data-ttu-id="e1957-117">ガベージ コレクターによって処理され、最初は対応するハッシュ バケット内に存在し、直ちに削除することができた行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-117">The number of rows processed by the garbage collector that were first in the corresponding hash bucket, and were able to be removed immediately (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-118">**Rows processed/sec (first in bucket)**</span><span class="sxs-lookup"><span data-stu-id="e1957-118">**Rows processed/sec (first in bucket)**</span></span>|<span data-ttu-id="e1957-119">ガベージ コレクターによって処理され、最初は対応するハッシュ バケット内に存在していた行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-119">The number of rows processed by the garbage collector that were first in the corresponding hash bucket (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-120">**Rows processed/sec (marked for unlink)**</span><span class="sxs-lookup"><span data-stu-id="e1957-120">**Rows processed/sec (marked for unlink)**</span></span>|<span data-ttu-id="e1957-121">ガベージ コレクターによって処理され、既にリンク解除のマークが付いていた行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-121">The number of rows processed by the garbage collector that were already marked for unlink (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-122">**Rows processed/sec (no sweep needed)**</span><span class="sxs-lookup"><span data-stu-id="e1957-122">**Rows processed/sec (no sweep needed)**</span></span>|<span data-ttu-id="e1957-123">ガベージ コレクターによって処理され、ダスティ コーナー スウィープ (詳細なクリーンアップ) を必要としない行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-123">The number of rows processed by the garbage collector that will not require a dusty corner sweep (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-124">**Sweep expired rows removed/sec**</span><span class="sxs-lookup"><span data-stu-id="e1957-124">**Sweep expired rows removed/sec**</span></span>|<span data-ttu-id="e1957-125">ダスティ コーナー スウィープの実行中に削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-125">The number of expired rows removed during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-126">**Sweep expired rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="e1957-126">**Sweep expired rows touched/sec**</span></span>|<span data-ttu-id="e1957-127">ダスティ コーナー スウィープの実行中に操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-127">The number of expired rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-128">**Sweep expiring rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="e1957-128">**Sweep expiring rows touched/sec**</span></span>|<span data-ttu-id="e1957-129">ダスティ コーナー スウィープの実行中に操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-129">The number of expiring rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-130">**Sweep rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="e1957-130">**Sweep rows touched/sec**</span></span>|<span data-ttu-id="e1957-131">ダスティ コーナー スウィープの実行中に操作された行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="e1957-131">The number of rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="e1957-132">**Sweep scans started/sec**</span><span class="sxs-lookup"><span data-stu-id="e1957-132">**Sweep scans started/sec**</span></span>|<span data-ttu-id="e1957-133">ダスティ コーナー スウィープ スキャンが開始された回数に関する 1 秒あたりの平均。</span><span class="sxs-lookup"><span data-stu-id="e1957-133">The number of dusty corner sweep scans started (on average), per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1957-134">参照</span><span class="sxs-lookup"><span data-stu-id="e1957-134">See Also</span></span>  
 [<span data-ttu-id="e1957-135">XTP &#40;インメモリ OLTP&#41; パフォーマンスカウンター</span><span class="sxs-lookup"><span data-stu-id="e1957-135">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
