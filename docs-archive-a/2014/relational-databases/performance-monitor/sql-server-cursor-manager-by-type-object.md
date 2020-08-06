---
title: 'SQL Server: Cursor Manager by Type オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7bee15aa2917f7b8890e6c1d3f26cc0e210208a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633103"
---
# <a name="sql-server-cursor-manager-by-type-object"></a><span data-ttu-id="f6c1e-102">SQL Server: Cursor Manager by Type オブジェクト</span><span class="sxs-lookup"><span data-stu-id="f6c1e-102">SQL Server, Cursor Manager by Type Object</span></span>
  <span data-ttu-id="f6c1e-103">**SQLServer:Cursor Manager by Type** オブジェクトには、種類別にグループ化されたカーソルを監視するカウンターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-103">The **SQLServer:Cursor Manager by Type** object provides counters to monitor cursors, grouped by type.</span></span>  
  
 <span data-ttu-id="f6c1e-104">次の表で、SQL Server **Cursor Manager by Type** カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-104">This table describes the SQL Server **Cursor Manager by Type** counters.</span></span>  
  
|<span data-ttu-id="f6c1e-105">Cursor Manager by Type カウンター</span><span class="sxs-lookup"><span data-stu-id="f6c1e-105">Cursor Manager by Type counters</span></span>|<span data-ttu-id="f6c1e-106">説明</span><span class="sxs-lookup"><span data-stu-id="f6c1e-106">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="f6c1e-107">**Active cursors**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-107">**Active cursors**</span></span>|<span data-ttu-id="f6c1e-108">アクティブなカーソルの数。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-108">Number of active cursors.</span></span>|  
|<span data-ttu-id="f6c1e-109">**Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-109">**Cache Hit Ratio**</span></span>|<span data-ttu-id="f6c1e-110">キャッシュ ヒットとキャッシュ参照の比率。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-110">Ratio between cache hits and lookups.</span></span>|  
|<span data-ttu-id="f6c1e-111">**Cached Cursor Counts**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-111">**Cached Cursor Counts**</span></span>|<span data-ttu-id="f6c1e-112">キャッシュ内の特定種類のカーソルの数。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-112">Number of cursors of a given type in the cache.</span></span>|  
|<span data-ttu-id="f6c1e-113">**Cursor Cache Use Count/sec**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-113">**Cursor Cache Use Count/sec**</span></span>|<span data-ttu-id="f6c1e-114">キャッシュされている各種のカーソルが使用された時間。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-114">Times each type of cached cursor has been used.</span></span>|  
|<span data-ttu-id="f6c1e-115">**Cursor memory usage**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-115">**Cursor memory usage**</span></span>|<span data-ttu-id="f6c1e-116">カーソルによって消費されたメモリ量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-116">Amount of memory consumed by cursors in kilobytes (KB).</span></span>|  
|<span data-ttu-id="f6c1e-117">**Cursor Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-117">**Cursor Requests/sec**</span></span>|<span data-ttu-id="f6c1e-118">サーバーが受け取った SQL カーソル要求の数。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-118">Number of SQL cursor requests received by server.</span></span>|  
|<span data-ttu-id="f6c1e-119">**Cursor worktable usage**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-119">**Cursor worktable usage**</span></span>|<span data-ttu-id="f6c1e-120">カーソルによって使用された作業テーブルの数。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-120">Number of worktables used by cursors.</span></span>|  
|<span data-ttu-id="f6c1e-121">**Number of active cursor plans**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-121">**Number of active cursor plans**</span></span>|<span data-ttu-id="f6c1e-122">カーソル プランの数。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-122">Number of cursor plans.</span></span>|  
  
 <span data-ttu-id="f6c1e-123">オブジェクトの各カウンターには、次のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-123">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="f6c1e-124">Cursor Manager のインスタンス</span><span class="sxs-lookup"><span data-stu-id="f6c1e-124">Cursor Manager instance</span></span>|<span data-ttu-id="f6c1e-125">説明</span><span class="sxs-lookup"><span data-stu-id="f6c1e-125">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="f6c1e-126">**_Total**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-126">**_Total**</span></span>|<span data-ttu-id="f6c1e-127">すべてのカーソルに関する情報。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-127">Information for all cursors.</span></span>|  
|<span data-ttu-id="f6c1e-128">**API Cursor**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-128">**API Cursor**</span></span>|<span data-ttu-id="f6c1e-129">API カーソルのみに関する情報。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-129">Only the API cursor information.</span></span>|  
|<span data-ttu-id="f6c1e-130">**TSQL Global Cursor**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-130">**TSQL Global Cursor**</span></span>|<span data-ttu-id="f6c1e-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] グローバル カーソルのみに関する情報。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-131">Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] global cursor information.</span></span>|  
|<span data-ttu-id="f6c1e-132">**TSQL Local Cursor**</span><span class="sxs-lookup"><span data-stu-id="f6c1e-132">**TSQL Local Cursor**</span></span>|<span data-ttu-id="f6c1e-133">[!INCLUDE[tsql](../../includes/tsql-md.md)] ローカル カーソルのみに関する情報。</span><span class="sxs-lookup"><span data-stu-id="f6c1e-133">Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] local cursor information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6c1e-134">参照</span><span class="sxs-lookup"><span data-stu-id="f6c1e-134">See Also</span></span>  
 [<span data-ttu-id="f6c1e-135">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="f6c1e-135">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
