---
title: SQL Server:Buffer Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Buffer Node
- Buffer Node object
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14659e4c1191e2260bccdbcd612f510770913629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643778"
---
# <a name="sql-serverbuffer-node"></a><span data-ttu-id="41e83-102">SQL Server: Buffer Node</span><span class="sxs-lookup"><span data-stu-id="41e83-102">SQL Server:Buffer Node</span></span>
  <span data-ttu-id="41e83-103">**Buffer Node** オブジェクトは、 **Buffer Manager** オブジェクトで提供されるカウンターを補完するカウンターを提供します。</span><span class="sxs-lookup"><span data-stu-id="41e83-103">The **Buffer Node** object provides counters that complement counters provided by the **Buffer Manager** object.</span></span> <span data-ttu-id="41e83-104">このオブジェクトを使用すると、各 NUMA (non-uniform memory access) ノードに対する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバッファー プール ページの配分を監視することができます。</span><span class="sxs-lookup"><span data-stu-id="41e83-104">It allows you to monitor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool page distribution for each non-uniform memory access (NUMA) node.</span></span> <span data-ttu-id="41e83-105">使用中の NUMA ノードごとに **Buffer Node** オブジェクトのインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="41e83-105">There is an instance of the **Buffer Node** object for each NUMA node in use.</span></span> <span data-ttu-id="41e83-106">非 NUMA アーキテクチャでは、 **Buffer Node** オブジェクトのインスタンスが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="41e83-106">On non-NUMA architecture, there will be a single instance of the **Buffer Node** object.</span></span>  
  
## <a name="buffer-node-performance-objects"></a><span data-ttu-id="41e83-107">Buffer Node パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="41e83-107">Buffer Node Performance Objects</span></span>  
 <span data-ttu-id="41e83-108">次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Buffer Node** パフォーマンス オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="41e83-108">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Buffer Node** performance objects.</span></span>  
  
|<span data-ttu-id="41e83-109">SQL Server の Buffer Node カウンター</span><span class="sxs-lookup"><span data-stu-id="41e83-109">SQL Server Buffer Node counters</span></span>|<span data-ttu-id="41e83-110">説明</span><span class="sxs-lookup"><span data-stu-id="41e83-110">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="41e83-111">**Database pages**</span><span class="sxs-lookup"><span data-stu-id="41e83-111">**Database pages**</span></span>|<span data-ttu-id="41e83-112">データベースの内容が含まれたこのノード上のバッファー プール内のページ数を示します。</span><span class="sxs-lookup"><span data-stu-id="41e83-112">Indicates the number of pages in the buffer pool on this node with database content.</span></span>|  
|<span data-ttu-id="41e83-113">**Page life expectancy**</span><span class="sxs-lookup"><span data-stu-id="41e83-113">**Page life expectancy**</span></span>|<span data-ttu-id="41e83-114">ページが参照されないままこのノードのバッファー プールに存在する最小秒数を示します。</span><span class="sxs-lookup"><span data-stu-id="41e83-114">Indicates the minimum number of seconds a page will stay in the buffer pool on this node without references.</span></span>|  
|<span data-ttu-id="41e83-115">**Local Node page lookups/sec**</span><span class="sxs-lookup"><span data-stu-id="41e83-115">**Local Node page lookups/sec**</span></span>|<span data-ttu-id="41e83-116">このノードによって満たされた、このノードからの参照要求の数を示します。</span><span class="sxs-lookup"><span data-stu-id="41e83-116">Indicates the number of lookup requests from this node which were satisfied from this node.</span></span>|  
|<span data-ttu-id="41e83-117">**Remote Note page lookups/sec**</span><span class="sxs-lookup"><span data-stu-id="41e83-117">**Remote Note page lookups/sec**</span></span>|<span data-ttu-id="41e83-118">他のノードによって満たされた、このノードからの参照要求の数を示します。</span><span class="sxs-lookup"><span data-stu-id="41e83-118">Indicates the number of lookup requests from this node which were satisfied from other nodes.</span></span>|  
  
 <span data-ttu-id="41e83-119">SQL Server が非 NUMA ハードウェアで動作している場合は、 **Buffer Node** オブジェクトのカウンターと **Buffer Manager** オブジェクトのカウンターが一致します。</span><span class="sxs-lookup"><span data-stu-id="41e83-119">If SQL Server is running on non-NUMA hardware, the counters of **Buffer Node** and **Buffer Manager** objects should match.</span></span>  
  
 <span data-ttu-id="41e83-120">NUMA ハードウェアでは、すべての **Buffer Nodes** の各カウンターの合計は、対応する **Buffer Manager**のカウンターに一致します。</span><span class="sxs-lookup"><span data-stu-id="41e83-120">On NUMA hardware, sums of respective counters of all **Buffer Nodes** should match their counterparts of **Buffer Manager**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41e83-121">カウンター値と合計が正確に一致しない場合があります。これは、カウンターが動的な性質を持っているためと、サンプリング精度によるものです。</span><span class="sxs-lookup"><span data-stu-id="41e83-121">The counter values and sums may not match precisely due to the dynamic nature of the counters and the sampling accuracy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e83-122">参照</span><span class="sxs-lookup"><span data-stu-id="41e83-122">See Also</span></span>  
 <span data-ttu-id="41e83-123">[SQL Server: Buffer Manager オブジェクト](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="41e83-123">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 <span data-ttu-id="41e83-124">[サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="41e83-124">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="41e83-125">[リソースの利用状況の監視 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="41e83-125">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 [<span data-ttu-id="41e83-126">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="41e83-126">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
