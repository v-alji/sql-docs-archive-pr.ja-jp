---
title: XTP カーソル |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 217a1196717492cb92adb24eaf7c06c8867abc2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719857"
---
# <a name="xtp-cursors"></a><span data-ttu-id="1d0b0-102">XTP Cursors</span><span class="sxs-lookup"><span data-stu-id="1d0b0-102">XTP Cursors</span></span>
  <span data-ttu-id="1d0b0-103">XTP Cursors パフォーマンス オブジェクトには、XTP エンジンの内部カーソルに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-103">The XTP Cursors performance object contains counters related to internal XTP engine cursors.</span></span> <span data-ttu-id="1d0b0-104">カーソルとは、XTP エンジンが [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを処理するために使用する、低レベルの構成要素です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-104">Cursors are the low-level building blocks the XTP engine uses to process [!INCLUDE[tsql](../../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="1d0b0-105">このため、通常はユーザー側でカーソルを直接管理することはありません。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-105">As such, you do not typically have direct control over them.</span></span>  
  
 <span data-ttu-id="1d0b0-106">次の表では、 **XTP カーソル**カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-106">This table describes the **XTP Cursors** counters.</span></span>  
  
|<span data-ttu-id="1d0b0-107">カウンター</span><span class="sxs-lookup"><span data-stu-id="1d0b0-107">Counter</span></span>|<span data-ttu-id="1d0b0-108">説明</span><span class="sxs-lookup"><span data-stu-id="1d0b0-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d0b0-109">**Cursor deletes/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-109">**Cursor deletes/sec**</span></span>|<span data-ttu-id="1d0b0-110">カーソルの削除回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-110">The number of cursor deletes (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-111">**Cursor inserts/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-111">**Cursor inserts/sec**</span></span>|<span data-ttu-id="1d0b0-112">カーソルの挿入回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-112">The number of cursor inserts (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-113">**Cursor scans started /sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-113">**Cursor scans started /sec**</span></span>|<span data-ttu-id="1d0b0-114">カーソル スキャンが開始された回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-114">The number of cursor scans started (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-115">**Cursor unique violations/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-115">**Cursor unique violations/sec**</span></span>|<span data-ttu-id="1d0b0-116">UNIQUE 制約の違反に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-116">The number of unique-constraint violations (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-117">**Cursor updates/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-117">**Cursor updates/sec**</span></span>|<span data-ttu-id="1d0b0-118">カーソルの更新回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-118">The number of cursor updates (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-119">**Cursor write conflicts/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-119">**Cursor write   conflicts/sec**</span></span>|<span data-ttu-id="1d0b0-120">同じ行バージョンに対する書き込み - 書き込みの競合回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-120">The number of write-write conflicts to the same row version (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-121">**Dusty corner scan retries/sec (user-issued)**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-121">**Dusty corner scan retries/sec (user-issued)**</span></span>|<span data-ttu-id="1d0b0-122">ユーザーのフル テーブル スキャンによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-122">The number of scan retries due to write conflicts during dusty corner sweeps issued by a user's full-table scan (on average), per second.</span></span> <span data-ttu-id="1d0b0-123">これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-123">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="1d0b0-124">**Expired rows removed/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-124">**Expired rows removed/sec**</span></span>|<span data-ttu-id="1d0b0-125">カーソルによって削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-125">The number of expired rows removed by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-126">**Expired rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-126">**Expired rows touched/sec**</span></span>|<span data-ttu-id="1d0b0-127">カーソルによって操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-127">The number of expired rows touched by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-128">**Rows returned/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-128">**Rows returned/sec**</span></span>|<span data-ttu-id="1d0b0-129">カーソルによって返された、有効期限切れの行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-129">The number of rows returned by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-130">**Rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-130">**Rows touched/sec**</span></span>|<span data-ttu-id="1d0b0-131">カーソルによって操作された行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-131">The number of rows touched by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="1d0b0-132">**Tentatively-deleted rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="1d0b0-132">**Tentatively-deleted rows touched/sec**</span></span>|<span data-ttu-id="1d0b0-133">カーソルによって操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-133">The number of expiring rows touched by cursors (on average), per second.</span></span> <span data-ttu-id="1d0b0-134">行が間もなく期限切れになるのは、その行を削除したトランザクションが依然としてアクティブな場合 (つまり、コミットや中止がまだ行われていない場合) です。</span><span class="sxs-lookup"><span data-stu-id="1d0b0-134">A row is expiring if the transaction that deleted it is still active (i.e. has not yet committed or aborted.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d0b0-135">参照</span><span class="sxs-lookup"><span data-stu-id="1d0b0-135">See Also</span></span>  
 [<span data-ttu-id="1d0b0-136">XTP &#40;インメモリ OLTP&#41; パフォーマンスカウンター</span><span class="sxs-lookup"><span data-stu-id="1d0b0-136">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
