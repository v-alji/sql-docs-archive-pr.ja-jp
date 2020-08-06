---
title: SQL Server:Locks オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Locks object
- SQLServer:Locks
ms.assetid: ace04f0d-3993-4444-8317-ca39d7087e49
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f13d4ea1172d6b32b90c045a45445c5c87f48a94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633088"
---
# <a name="sql-server-locks-object"></a><span data-ttu-id="4006f-102">SQL Server:Locks オブジェクト</span><span class="sxs-lookup"><span data-stu-id="4006f-102">SQL Server, Locks Object</span></span>
  <span data-ttu-id="4006f-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **SQLServer:Locks** オブジェクトでは、各リソースの種類の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロックに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4006f-103">The **SQLServer:Locks** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locks on individual resource types.</span></span> <span data-ttu-id="4006f-104">ロックは、複数のトランザクションで同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースが同時に使用されるのを防ぐために、トランザクション中に読み取られたり変更されたりする行などにかけられます。</span><span class="sxs-lookup"><span data-stu-id="4006f-104">Locks are held on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources, such as rows read or modified during a transaction, to prevent concurrent use of resources by different transactions.</span></span> <span data-ttu-id="4006f-105">たとえば、あるトランザクションによってテーブルの行に排他 (X) ロックがかけられると、他のトランザクションはロックが解除されるまでその行を変更できません。</span><span class="sxs-lookup"><span data-stu-id="4006f-105">For example, if an exclusive (X) lock is held on a row within a table by a transaction, no other transaction can modify that row until the lock is released.</span></span> <span data-ttu-id="4006f-106">ロックを最小限にとどめるとコンカレンシーが向上し、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="4006f-106">Minimizing locks increases concurrency, which can improve performance.</span></span> <span data-ttu-id="4006f-107">異なる種類のリソースのロックを表す複数の **Locks** オブジェクトのインスタンスを同時に監視することができます。</span><span class="sxs-lookup"><span data-stu-id="4006f-107">Multiple instances of the **Locks** object can be monitored at the same time, with each instance representing a lock on a resource type.</span></span>  
  
 <span data-ttu-id="4006f-108">次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4006f-108">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** counters.</span></span>  
  
|<span data-ttu-id="4006f-109">SQL Server:Locks カウンター</span><span class="sxs-lookup"><span data-stu-id="4006f-109">SQL Server Locks counters</span></span>|<span data-ttu-id="4006f-110">説明</span><span class="sxs-lookup"><span data-stu-id="4006f-110">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="4006f-111">**Average Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="4006f-111">**Average Wait Time (ms)**</span></span>|<span data-ttu-id="4006f-112">待つ必要がある各ロック要求の平均待ち時間 (ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="4006f-112">Average amount of wait time (in milliseconds) for each lock request that resulted in a wait.</span></span>|  
|<span data-ttu-id="4006f-113">**Lock Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="4006f-113">**Lock Requests/sec**</span></span>|<span data-ttu-id="4006f-114">ロック マネージャーから 1 秒あたりに要求された新しいロックと、ロック変換の数。</span><span class="sxs-lookup"><span data-stu-id="4006f-114">Number of new locks and lock conversions per second requested from the lock manager.</span></span>|  
|<span data-ttu-id="4006f-115">**Lock Timeouts (timeout > 0)/sec**</span><span class="sxs-lookup"><span data-stu-id="4006f-115">**Lock Timeouts (timeout > 0)/sec**</span></span>|<span data-ttu-id="4006f-116">NOWAIT ロックの要求を除く、1 秒あたりにタイムアウトしたロック要求の数。</span><span class="sxs-lookup"><span data-stu-id="4006f-116">Number of lock requests per second that timed out, but excluding requests for NOWAIT locks.</span></span>|  
|<span data-ttu-id="4006f-117">**Lock Timeouts/sec**</span><span class="sxs-lookup"><span data-stu-id="4006f-117">**Lock Timeouts/sec**</span></span>|<span data-ttu-id="4006f-118">NOWAIT ロックの要求を含めた、1 秒あたりにタイムアウトしたロック要求の数。</span><span class="sxs-lookup"><span data-stu-id="4006f-118">Number of lock requests per second that timed out, including requests for NOWAIT locks.</span></span>|  
|<span data-ttu-id="4006f-119">**Lock Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="4006f-119">**Lock Wait Time (ms)**</span></span>|<span data-ttu-id="4006f-120">最後の 1 秒間のロックの総待機時間 (ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="4006f-120">Total wait time (in milliseconds) for locks in the last second.</span></span>|  
|<span data-ttu-id="4006f-121">**Lock Waits/sec**</span><span class="sxs-lookup"><span data-stu-id="4006f-121">**Lock Waits/sec**</span></span>|<span data-ttu-id="4006f-122">呼び出し元が待つ必要のあった 1 秒あたりのロック要求の数。</span><span class="sxs-lookup"><span data-stu-id="4006f-122">Number of lock requests per second that required the caller to wait.</span></span>|  
|<span data-ttu-id="4006f-123">**Number of Deadlocks/sec**</span><span class="sxs-lookup"><span data-stu-id="4006f-123">**Number of Deadlocks/sec**</span></span>|<span data-ttu-id="4006f-124">デッドロックが発生した 1 秒あたりのロック要求の数。</span><span class="sxs-lookup"><span data-stu-id="4006f-124">Number of lock requests per second that resulted in a deadlock.</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4006f-125">では、以下のリソースをロックできます。</span><span class="sxs-lookup"><span data-stu-id="4006f-125">can lock these resources.</span></span>  
  
|<span data-ttu-id="4006f-126">項目</span><span class="sxs-lookup"><span data-stu-id="4006f-126">Item</span></span>|<span data-ttu-id="4006f-127">説明</span><span class="sxs-lookup"><span data-stu-id="4006f-127">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="4006f-128">**_Total**</span><span class="sxs-lookup"><span data-stu-id="4006f-128">**_Total**</span></span>|<span data-ttu-id="4006f-129">すべてのロックに関する情報。</span><span class="sxs-lookup"><span data-stu-id="4006f-129">Information for all locks.</span></span>|  
|<span data-ttu-id="4006f-130">**AllocUnit**</span><span class="sxs-lookup"><span data-stu-id="4006f-130">**AllocUnit**</span></span>|<span data-ttu-id="4006f-131">アロケーション ユニットのロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-131">A lock on an allocation unit.</span></span>|  
|<span data-ttu-id="4006f-132">**Application**</span><span class="sxs-lookup"><span data-stu-id="4006f-132">**Application**</span></span>|<span data-ttu-id="4006f-133">アプリケーションで指定されているリソースのロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-133">A lock on an application-specified resource.</span></span>|  
|<span data-ttu-id="4006f-134">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="4006f-134">**Database**</span></span>|<span data-ttu-id="4006f-135">データベース内のすべてのオブジェクトを含むデータベースのロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-135">A lock on a database, including all objects in the database.</span></span>|  
|<span data-ttu-id="4006f-136">**Extent**</span><span class="sxs-lookup"><span data-stu-id="4006f-136">**Extent**</span></span>|<span data-ttu-id="4006f-137">連続した 8 ページのグループのロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-137">A lock on a contiguous group of 8 pages.</span></span>|  
|<span data-ttu-id="4006f-138">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="4006f-138">**File**</span></span>|<span data-ttu-id="4006f-139">データベース ファイルのロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-139">A lock on a database file.</span></span>|  
|<span data-ttu-id="4006f-140">**Heap/BTree**</span><span class="sxs-lookup"><span data-stu-id="4006f-140">**Heap/BTree**</span></span>|<span data-ttu-id="4006f-141">ヒープまたは BTree (HOBT)。</span><span class="sxs-lookup"><span data-stu-id="4006f-141">Heap or BTree (HOBT).</span></span> <span data-ttu-id="4006f-142">データ ページのヒープまたはインデックスの BTree 構造のロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-142">A lock on a heap of data pages, or on the BTree structure of an index.</span></span>|  
|<span data-ttu-id="4006f-143">**キー**</span><span class="sxs-lookup"><span data-stu-id="4006f-143">**Key**</span></span>|<span data-ttu-id="4006f-144">インデックスの行のロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-144">A lock on a row in an index.</span></span>|  
|<span data-ttu-id="4006f-145">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="4006f-145">**Metadata**</span></span>|<span data-ttu-id="4006f-146">カタログ情報 (メタデータ) のロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-146">A lock on a piece of catalog information, also called metadata.</span></span>|  
|<span data-ttu-id="4006f-147">**Object**</span><span class="sxs-lookup"><span data-stu-id="4006f-147">**Object**</span></span>|<span data-ttu-id="4006f-148">すべてのデータとインデックスを含む、テーブル、ストアド プロシージャ、ビューなどのロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-148">A lock on table, stored procedure, view, etc, including all data and indexes.</span></span> <span data-ttu-id="4006f-149">このオブジェクトには、 **sys.all_objects**内のエントリを持つ任意のアイテムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4006f-149">The object can be anything that has an entry in **sys.all_objects**.</span></span>|  
|<span data-ttu-id="4006f-150">**ページ**</span><span class="sxs-lookup"><span data-stu-id="4006f-150">**Page**</span></span>|<span data-ttu-id="4006f-151">データベース内の 8 KB のページのロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-151">A lock on an 8-kilobyte (KB) page in a database.</span></span>|  
|<span data-ttu-id="4006f-152">**RID**</span><span class="sxs-lookup"><span data-stu-id="4006f-152">**RID**</span></span>|<span data-ttu-id="4006f-153">行 ID。</span><span class="sxs-lookup"><span data-stu-id="4006f-153">Row ID.</span></span> <span data-ttu-id="4006f-154">ヒープ内の単一行のロック。</span><span class="sxs-lookup"><span data-stu-id="4006f-154">A lock on a single row in a heap.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4006f-155">参照</span><span class="sxs-lookup"><span data-stu-id="4006f-155">See Also</span></span>  
 [<span data-ttu-id="4006f-156">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="4006f-156">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
