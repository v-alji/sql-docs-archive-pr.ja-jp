---
title: インメモリ OLTP のメモリの管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90f9b638697d59a0a573a9a31c0a5faade23e870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738688"
---
# <a name="managing-memory-for-in-memory-oltp"></a><span data-ttu-id="00e84-102">インメモリ OLTP のメモリ管理</span><span class="sxs-lookup"><span data-stu-id="00e84-102">Managing Memory for In-Memory OLTP</span></span>
  <span data-ttu-id="00e84-103">メモリ最適化テーブルでは、すべての行とインデックスをメモリ内に保持するために十分なメモリが必要です。</span><span class="sxs-lookup"><span data-stu-id="00e84-103">Memory-optimized tables require that sufficient memory exist to keep all of the rows and indexes in memory.</span></span> <span data-ttu-id="00e84-104">メモリは有限のリソースであるため、システム上のメモリ使用量を把握して管理することが重要です。</span><span class="sxs-lookup"><span data-stu-id="00e84-104">Because memory is a finite resource, it is important that you understand and manage memory usage on your system.</span></span> <span data-ttu-id="00e84-105">このセクションのトピックでは、一般的なメモリの使用量と管理シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="00e84-105">The topics in this section cover common memory use and management scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00e84-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="00e84-106">In this section</span></span>  
  
|<span data-ttu-id="00e84-107">セクション</span><span class="sxs-lookup"><span data-stu-id="00e84-107">Section</span></span>|<span data-ttu-id="00e84-108">説明</span><span class="sxs-lookup"><span data-stu-id="00e84-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00e84-109">メモリ最適化テーブルのメモリ必要量の推定</span><span class="sxs-lookup"><span data-stu-id="00e84-109">Estimate Memory Requirements for Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|<span data-ttu-id="00e84-110">テーブルのメモリの必要量を推定します。</span><span class="sxs-lookup"><span data-stu-id="00e84-110">Estimate a table's memory needs.</span></span>|  
|[<span data-ttu-id="00e84-111">データベースを作成してリソース プールにバインドする方法については、「</span><span class="sxs-lookup"><span data-stu-id="00e84-111">Bind a Database with Memory-Optimized Tables to a Resource Pool</span></span>](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|<span data-ttu-id="00e84-112">データベースをリソース プールにバインドする手順を示すチュートリアル。</span><span class="sxs-lookup"><span data-stu-id="00e84-112">Step by step walkthrough to bind a database with a resource pool.</span></span>|  
|[<span data-ttu-id="00e84-113">メモリ使用量の監視とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="00e84-113">Monitor and Troubleshoot Memory Usage</span></span>](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|<span data-ttu-id="00e84-114">メモリ使用量を監視するために使用できるツール。</span><span class="sxs-lookup"><span data-stu-id="00e84-114">Tools you can use to monitor your memory usage.</span></span> <span data-ttu-id="00e84-115">メモリ使用量が多くなりすぎた場合のトラブルシューティングについても説明します。</span><span class="sxs-lookup"><span data-stu-id="00e84-115">Also covers troubleshooting if memory usage gets too high.</span></span>|  
|[<span data-ttu-id="00e84-116">メモリ不足の問題の解決</span><span class="sxs-lookup"><span data-stu-id="00e84-116">Resolve Out Of Memory Issues</span></span>](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|<span data-ttu-id="00e84-117">OOM (メモリ不足) 状態から回復する手順。</span><span class="sxs-lookup"><span data-stu-id="00e84-117">Steps to recover from an OOM (Out of Memory) situation.</span></span>|  
|[<span data-ttu-id="00e84-118">データベースの復元とリソース プールへのバインド</span><span class="sxs-lookup"><span data-stu-id="00e84-118">Restore a Database and Bind it to a Resource Pool</span></span>](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|<span data-ttu-id="00e84-119">[!INCLUDE[hek_2](../includes/hek-2-md.md)] データベースを復元して名前付きリソース プールにバインドする手順。</span><span class="sxs-lookup"><span data-stu-id="00e84-119">Steps to restore an [!INCLUDE[hek_2](../includes/hek-2-md.md)] database and bind it to a named resource pool.</span></span>|  
|[<span data-ttu-id="00e84-120">インメモリ OLTP ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="00e84-120">In-Memory OLTP Garbage Collection</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|<span data-ttu-id="00e84-121">削除された行でのガベージ コレクションの動作に関する理解を深めることができます。</span><span class="sxs-lookup"><span data-stu-id="00e84-121">Understand how garbage collection operates on deleted rows.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00e84-122">参照</span><span class="sxs-lookup"><span data-stu-id="00e84-122">See Also</span></span>  
 [<span data-ttu-id="00e84-123">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="00e84-123">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
