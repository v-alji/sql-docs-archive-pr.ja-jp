---
title: VM 環境でのインメモリ OLTP の使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 27ec7eb3-3a24-41db-aa65-2f206514c6f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83cf785fbcd2df9449d61e328e3bf8e374a6656d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715686"
---
# <a name="using-in-memory-oltp-in-a-vm-environment"></a><span data-ttu-id="38503-102">VM 環境でのインメモリ OLTP の使用</span><span class="sxs-lookup"><span data-stu-id="38503-102">Using In-Memory OLTP in a VM Environment</span></span>
  <span data-ttu-id="38503-103">サーバー仮想化に伴い、各企業は IT の資本コストと運用コストを削減し、アプリケーションの準備、メンテナンス、可用性、バックアップと復旧の各プロセスを向上させることにより、IT 効率の大幅な上昇を達成しています。</span><span class="sxs-lookup"><span data-stu-id="38503-103">Server virtualization can help you lower IT capital and operational costs and attain greater IT efficiency with improved application provisioning, maintenance, availability, and backup/recovery processes.</span></span> <span data-ttu-id="38503-104">最近の技術的な進歩により、仮想化を使用して、複雑なデータベース ワークロードを従来より容易に統合することができます。</span><span class="sxs-lookup"><span data-stu-id="38503-104">With recent technological advances, complex database workloads can be more readily consolidated using virtualization.</span></span> <span data-ttu-id="38503-105">ここでは、仮想化環境内での [!INCLUDE[hek_1](../includes/hek-1-md.md)] の使用に関して推奨されるベスト プラクティスについて取り扱います。</span><span class="sxs-lookup"><span data-stu-id="38503-105">This topic covers best practices for using [!INCLUDE[hek_1](../includes/hek-1-md.md)] in a virtualized environment.</span></span>  
  
##  <a name="memory-pre-allocation"></a><a name="bkmk_memoryPreAllocation"></a><span data-ttu-id="38503-106">メモリの事前割り当て</span><span class="sxs-lookup"><span data-stu-id="38503-106">Memory pre-allocation</span></span>  
 <span data-ttu-id="38503-107">仮想化環境でのメモリに関して、パフォーマンス向上とサポート拡張は重要な考慮事項です。</span><span class="sxs-lookup"><span data-stu-id="38503-107">For memory in a virtualized environment, better performance and enhanced support are essential considerations.</span></span> <span data-ttu-id="38503-108">仮想マシンの需要 (ピーク負荷とオフピーク負荷) に応じてメモリを迅速に仮想マシンに割り当てる能力が必須であり、メモリが浪費されていないことを確認する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="38503-108">You must be able to both quickly allocate memory to virtual machines depending on their requirements (peak and off-peak loads) and ensure that the memory is not wasted.</span></span> <span data-ttu-id="38503-109">Hyper-V 動的メモリ機能により、1 台のホスト上で実行する複数の仮想マシン間でのメモリ割り当てと管理がより迅速に行われます。</span><span class="sxs-lookup"><span data-stu-id="38503-109">The Hyper-V Dynamic Memory feature increases agility in how the memory is allocated and managed between virtual machines running on a host.</span></span>  
  
 <span data-ttu-id="38503-110">メモリ最適化テーブルを含むデータベースを仮想化する場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の仮想化と管理に関するいくつかのベスト プラクティスを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38503-110">Some best practices for virtualizing and managing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] need to be modified when virtualizing a database with memory-optimized tables.</span></span> <span data-ttu-id="38503-111">メモリ最適化されたテーブルが存在しない場合、次の 2 つのベスト プラクティスがあります。</span><span class="sxs-lookup"><span data-stu-id="38503-111">Without memory-optimized tables, two of the best practices are:</span></span>  
  
-   <span data-ttu-id="38503-112">MIN_SERVER_MEMORY を使用する場合は、必要とされる量のメモリのみを割り当てる方が適切です。その結果、他のプロセス用に十分なメモリを残すことができます (その結果、ページングを回避できます)。</span><span class="sxs-lookup"><span data-stu-id="38503-112">If you use MIN_SERVER_MEMORY, it is better to assign only the amount of memory that is required so sufficient memory remains for other processes (thereby avoiding paging).</span></span>  
  
-   <span data-ttu-id="38503-113">メモリの事前割り当ての値を過度に大きく設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="38503-113">Do not set the memory pre-allocation value too high.</span></span> <span data-ttu-id="38503-114">そうしない場合は、他のプロセスがメモリを必要とする時点で十分なメモリを取得できず、メモリのページングが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38503-114">Otherwise, other processes may not get sufficient memory at the time when they require it, and this can result in memory paging.</span></span>  
  
 <span data-ttu-id="38503-115">メモリ最適化テーブルがデータベース内に含まれている場合に上記のプラクティスに従うと、データベースの復元と復旧を試みたときに、データベースを復旧するための十分なメモリが存在するにもかかわらず、データベースが "復旧の保留中" という状態にとどまる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38503-115">If you follow the above practices for a database with memory-optimized tables, an attempt to restore and recover a database could result in the database being in a "Recovery Pending" state, even if you have sufficient memory to recover the database.</span></span> <span data-ttu-id="38503-116">その理由は、動的メモリ割り当て機能がメモリをデータベースに割り当てる場合に比べて、 [!INCLUDE[hek_2](../includes/hek-2-md.md)] は起動時により積極的にデータをメモリ内に読み込むことにあります。</span><span class="sxs-lookup"><span data-stu-id="38503-116">The reason for this is that, when starting up, [!INCLUDE[hek_2](../includes/hek-2-md.md)] brings data into memory more aggressively than dynamic memory allocation allocates memory to the database.</span></span>  
  
 <span data-ttu-id="38503-117">**解決策**</span><span class="sxs-lookup"><span data-stu-id="38503-117">**Resolution**</span></span>  
  
 <span data-ttu-id="38503-118">この問題を軽減するためには、必要に応じて追加のメモリを提供する動的メモリ機能に依存して最小限のメモリを割り当てる代わりに、データベースを復旧または再起動するために十分なメモリをデータベースに事前に割り当ててください。</span><span class="sxs-lookup"><span data-stu-id="38503-118">To mitigate this, pre-allocate sufficient memory to the database to recover or restart the database, not a minimum value relying on dynamic memory to provide the additional memory when needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38503-119">参照</span><span class="sxs-lookup"><span data-stu-id="38503-119">See Also</span></span>  
 [<span data-ttu-id="38503-120">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="38503-120">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
