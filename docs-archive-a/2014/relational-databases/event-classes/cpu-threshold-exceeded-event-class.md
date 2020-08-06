---
title: CPU Threshold Exceeded イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07b51e1a6f08f48c601b00d2dcb67bc6d09006f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632510"
---
# <a name="cpu-threshold-exceeded-event-class"></a><span data-ttu-id="d8537-102">CPU Threshold Exceeded イベント クラス</span><span class="sxs-lookup"><span data-stu-id="d8537-102">CPU Threshold Exceeded Event Class</span></span>
  <span data-ttu-id="d8537-103">CPU Threshold Exceeded イベント クラスは、REQUEST_MAX_CPU_TIME_SEC に指定されている CPU しきい値を超えるクエリがリソース ガバナーによって検出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="d8537-103">The CPU Threshold Exceeded event class indicates that Resource Governor detects a query that exceeds the CPU threshold specified for REQUEST_MAX_CPU_TIME_SEC.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8537-104">このイベントの検出間隔は 5 秒です。</span><span class="sxs-lookup"><span data-stu-id="d8537-104">The detection interval for this event is five seconds.</span></span> <span data-ttu-id="d8537-105">クエリが指定の制限を超えた時間が 5 秒以上の場合は、このイベントの生成が保証されます。</span><span class="sxs-lookup"><span data-stu-id="d8537-105">It is guaranteed that an event will be generated if a query exceeds the specified limit by at least five seconds.</span></span> <span data-ttu-id="d8537-106">クエリが指定のしきい値を超えた時間が 5 秒未満の場合、クエリのタイミングと前回の検出スイープの時間によっては検出されない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d8537-106">However, if a query exceeds the specified threshold by less than five seconds, its detection might be missed depending on the timing of the query and the time of last detection sweep.</span></span>  
  
## <a name="cpu-threshold-exceeded-data-columns"></a><span data-ttu-id="d8537-107">CPU Threshold Exceeded のデータ列</span><span class="sxs-lookup"><span data-stu-id="d8537-107">CPU Threshold Exceeded Data Columns</span></span>  
  
|<span data-ttu-id="d8537-108">データ列名</span><span class="sxs-lookup"><span data-stu-id="d8537-108">Data column name</span></span>|<span data-ttu-id="d8537-109">データ型</span><span class="sxs-lookup"><span data-stu-id="d8537-109">Data type</span></span>|<span data-ttu-id="d8537-110">説明</span><span class="sxs-lookup"><span data-stu-id="d8537-110">Description</span></span>|<span data-ttu-id="d8537-111">列 ID</span><span class="sxs-lookup"><span data-stu-id="d8537-111">Column ID</span></span>|<span data-ttu-id="d8537-112">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="d8537-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="d8537-113">CPU</span><span class="sxs-lookup"><span data-stu-id="d8537-113">CPU</span></span>|`int`|<span data-ttu-id="d8537-114">CPU 使用率 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="d8537-114">CPU usage in milliseconds.</span></span>|<span data-ttu-id="d8537-115">18</span><span class="sxs-lookup"><span data-stu-id="d8537-115">18</span></span>|<span data-ttu-id="d8537-116">はい</span><span class="sxs-lookup"><span data-stu-id="d8537-116">Yes</span></span>|  
|<span data-ttu-id="d8537-117">EventClass</span><span class="sxs-lookup"><span data-stu-id="d8537-117">EventClass</span></span>|`int`|<span data-ttu-id="d8537-118">214</span><span class="sxs-lookup"><span data-stu-id="d8537-118">214</span></span>|<span data-ttu-id="d8537-119">27</span><span class="sxs-lookup"><span data-stu-id="d8537-119">27</span></span>|<span data-ttu-id="d8537-120">いいえ</span><span class="sxs-lookup"><span data-stu-id="d8537-120">No</span></span>|  
|<span data-ttu-id="d8537-121">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="d8537-121">EventSubClass</span></span>|`int`|<span data-ttu-id="d8537-122">CPU 制限違反。</span><span class="sxs-lookup"><span data-stu-id="d8537-122">CPU limit violation.</span></span>|<span data-ttu-id="d8537-123">21</span><span class="sxs-lookup"><span data-stu-id="d8537-123">21</span></span>|<span data-ttu-id="d8537-124">はい</span><span class="sxs-lookup"><span data-stu-id="d8537-124">Yes</span></span>|  
|<span data-ttu-id="d8537-125">GroupID</span><span class="sxs-lookup"><span data-stu-id="d8537-125">GroupID</span></span>|`int`|<span data-ttu-id="d8537-126">違反が発生したグループ ID。</span><span class="sxs-lookup"><span data-stu-id="d8537-126">Group ID where the violation occurred.</span></span>|<span data-ttu-id="d8537-127">66</span><span class="sxs-lookup"><span data-stu-id="d8537-127">66</span></span>|<span data-ttu-id="d8537-128">はい</span><span class="sxs-lookup"><span data-stu-id="d8537-128">Yes</span></span>|  
|<span data-ttu-id="d8537-129">OwnerID</span><span class="sxs-lookup"><span data-stu-id="d8537-129">OwnerID</span></span>|`int`|<span data-ttu-id="d8537-130">違反の原因となったプロセスの SPID。</span><span class="sxs-lookup"><span data-stu-id="d8537-130">SPID of the process that caused the violation.</span></span>|<span data-ttu-id="d8537-131">58</span><span class="sxs-lookup"><span data-stu-id="d8537-131">58</span></span>|<span data-ttu-id="d8537-132">はい</span><span class="sxs-lookup"><span data-stu-id="d8537-132">Yes</span></span>|  
|<span data-ttu-id="d8537-133">SPID</span><span class="sxs-lookup"><span data-stu-id="d8537-133">SPID</span></span>|`int`|<span data-ttu-id="d8537-134">このイベントを発生させたサーバー プロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="d8537-134">ID of the server process that fires this event.</span></span><br /><br /> <span data-ttu-id="d8537-135">注: システム スレッドが CPU 使用率をバックグラウンド タスクとして検証する場合は、この ID が実際のユーザー SPID と異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="d8537-135">Note: This can differ from the actual user SPID if a system thread validates CPU usage as a background task.</span></span>|<span data-ttu-id="d8537-136">12</span><span class="sxs-lookup"><span data-stu-id="d8537-136">12</span></span>|<span data-ttu-id="d8537-137">はい</span><span class="sxs-lookup"><span data-stu-id="d8537-137">Yes</span></span>|  
|<span data-ttu-id="d8537-138">StartTime</span><span class="sxs-lookup"><span data-stu-id="d8537-138">StartTime</span></span>|`datetime`|<span data-ttu-id="d8537-139">このイベントが発生した時刻。</span><span class="sxs-lookup"><span data-stu-id="d8537-139">The time when this event fired.</span></span>|<span data-ttu-id="d8537-140">14</span><span class="sxs-lookup"><span data-stu-id="d8537-140">14</span></span>|<span data-ttu-id="d8537-141">はい</span><span class="sxs-lookup"><span data-stu-id="d8537-141">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8537-142">参照</span><span class="sxs-lookup"><span data-stu-id="d8537-142">See Also</span></span>  
 [<span data-ttu-id="d8537-143">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d8537-143">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
