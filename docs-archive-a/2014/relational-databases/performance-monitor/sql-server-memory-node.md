---
title: SQL Server、Memory Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5bbc3f581ea9ececeb7d55a614ef27c3c72de7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645004"
---
# <a name="sql-server-memory-node"></a><span data-ttu-id="1c6b8-102">SQL Server、Memory Node</span><span class="sxs-lookup"><span data-stu-id="1c6b8-102">SQL Server, Memory Node</span></span>
  <span data-ttu-id="1c6b8-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **Memory Node** オブジェクトには、NUMA ノードのサーバー メモリの使用状況を監視するためのカウンターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1c6b8-103">The **Memory Node** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor server memory usage on NUMA nodes.</span></span>  
  
## <a name="memory-node-counters"></a><span data-ttu-id="1c6b8-104">Memory Node カウンター</span><span class="sxs-lookup"><span data-stu-id="1c6b8-104">Memory Node Counters</span></span>  
 <span data-ttu-id="1c6b8-105">次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1c6b8-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** counters.</span></span>  
  
|<span data-ttu-id="1c6b8-106">SQL Server Memory Manager カウンター</span><span class="sxs-lookup"><span data-stu-id="1c6b8-106">SQL Server Memory Manager counters</span></span>|<span data-ttu-id="1c6b8-107">説明</span><span class="sxs-lookup"><span data-stu-id="1c6b8-107">Description</span></span>|  
|----------------------------------------|-----------------|  
|<span data-ttu-id="1c6b8-108">**Database Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="1c6b8-108">**Database Node Memory (KB)**</span></span>|<span data-ttu-id="1c6b8-109">このノードでデータベース ページに現在使用しているメモリの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c6b8-109">Specifies the amount of memory the server is currently using on this node for database pages.</span></span>|  
|<span data-ttu-id="1c6b8-110">**Free Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="1c6b8-110">**Free Node Memory (KB)**</span></span>|<span data-ttu-id="1c6b8-111">このノードの未使用のメモリの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c6b8-111">Specifies the amount of memory the server is not using on this node.</span></span>|  
|<span data-ttu-id="1c6b8-112">**Foreign Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="1c6b8-112">**Foreign Node Memory (KB)**</span></span>|<span data-ttu-id="1c6b8-113">このノードの NUMA ローカル メモリ以外のメモリの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c6b8-113">Specifies the amount of non NUMA-local memory on this node.</span></span>|  
|<span data-ttu-id="1c6b8-114">**Stolen Memory Node (KB)**</span><span class="sxs-lookup"><span data-stu-id="1c6b8-114">**Stolen Memory Node (KB)**</span></span>|<span data-ttu-id="1c6b8-115">このノードでデータベース ページ以外に使用しているメモリの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c6b8-115">Specifies the amount of memory the server is using on this node for purposes other than database pages.</span></span>|  
|<span data-ttu-id="1c6b8-116">**Target Node Memory**</span><span class="sxs-lookup"><span data-stu-id="1c6b8-116">**Target Node Memory**</span></span>|<span data-ttu-id="1c6b8-117">このノードの理想的なメモリの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c6b8-117">Specifies the ideal amount of memory for this node.</span></span>|  
|<span data-ttu-id="1c6b8-118">**Total Node Memory**</span><span class="sxs-lookup"><span data-stu-id="1c6b8-118">**Total Node Memory**</span></span>|<span data-ttu-id="1c6b8-119">サーバーがこのノードでコミットしているメモリの総容量を示します。</span><span class="sxs-lookup"><span data-stu-id="1c6b8-119">Indicates the total amount of memory the server has committed on this node.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c6b8-120">参照</span><span class="sxs-lookup"><span data-stu-id="1c6b8-120">See Also</span></span>  
 <span data-ttu-id="1c6b8-121">[リソースの利用状況の監視 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="1c6b8-121">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="1c6b8-122">[SQL Server: Buffer Manager オブジェクト](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="1c6b8-122">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="1c6b8-123">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1c6b8-123">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
