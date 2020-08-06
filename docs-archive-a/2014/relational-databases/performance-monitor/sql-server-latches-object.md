---
title: SQL Server の Latches オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f49ac00114065e971c0893f9217ab883eb2d7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633090"
---
# <a name="sql-server-latches-object"></a><span data-ttu-id="35450-102">SQL Server の Latches オブジェクト</span><span class="sxs-lookup"><span data-stu-id="35450-102">SQL Server, Latches Object</span></span>
  <span data-ttu-id="35450-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **SQLServer:Latches** オブジェクトには、ラッチという内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソース ロックを監視するためのカウンターがあります。</span><span class="sxs-lookup"><span data-stu-id="35450-103">The **SQLServer:Latches** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor internal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource locks called latches.</span></span> <span data-ttu-id="35450-104">ユーザーの利用状況とリソース使用率を調べるために行うラッチの監視は、パフォーマンスのボトルネックを特定するために役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="35450-104">Monitoring the latches to determine user activity and resource usage can help you to identify performance bottlenecks.</span></span>  
  
 <span data-ttu-id="35450-105">次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="35450-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** counters.</span></span>  
  
|<span data-ttu-id="35450-106">SQL Server Latches カウンター</span><span class="sxs-lookup"><span data-stu-id="35450-106">SQL Server Latches counters</span></span>|<span data-ttu-id="35450-107">説明</span><span class="sxs-lookup"><span data-stu-id="35450-107">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="35450-108">**Average Latch Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="35450-108">**Average Latch Wait Time (ms)**</span></span>|<span data-ttu-id="35450-109">待機しなければならなかったラッチ要求の平均ラッチ待ち時間 (ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="35450-109">Average latch wait time (in milliseconds) for latch requests that had to wait.</span></span>|  
|<span data-ttu-id="35450-110">**Latch Waits/sec**</span><span class="sxs-lookup"><span data-stu-id="35450-110">**Latch Waits/sec**</span></span>|<span data-ttu-id="35450-111">直ちに許可できなかったラッチ要求の数。</span><span class="sxs-lookup"><span data-stu-id="35450-111">Number of latch requests that could not be granted immediately.</span></span>|  
|<span data-ttu-id="35450-112">**Number of SuperLatches**</span><span class="sxs-lookup"><span data-stu-id="35450-112">**Number of SuperLatches**</span></span>|<span data-ttu-id="35450-113">現在の SuperLatch であるラッチの数。</span><span class="sxs-lookup"><span data-stu-id="35450-113">Number of latches that are currently SuperLatches.</span></span>|  
|<span data-ttu-id="35450-114">**SuperLatch Demotions/sec**</span><span class="sxs-lookup"><span data-stu-id="35450-114">**SuperLatch Demotions/sec**</span></span>|<span data-ttu-id="35450-115">最後の 1 秒間に通常のラッチに降格された SuperLatch の数。</span><span class="sxs-lookup"><span data-stu-id="35450-115">Number of SuperLatches that have been demoted to regular latches in the last second.</span></span>|  
|<span data-ttu-id="35450-116">**SuperLatch Demotions/sec**</span><span class="sxs-lookup"><span data-stu-id="35450-116">**SuperLatch Promotions/sec**</span></span>|<span data-ttu-id="35450-117">最後の 1 秒間に SuperLatch に昇格されたラッチの数。</span><span class="sxs-lookup"><span data-stu-id="35450-117">Number of latches that have been promoted to SuperLatches in the last second.</span></span>|  
|<span data-ttu-id="35450-118">**Total Latch Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="35450-118">**Total Latch Wait Time (ms)**</span></span>|<span data-ttu-id="35450-119">直前のラッチ要求の合計ラッチ待ち時間 (ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="35450-119">Total latch wait time (in milliseconds) for latch requests in the last second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35450-120">参照</span><span class="sxs-lookup"><span data-stu-id="35450-120">See Also</span></span>  
 [<span data-ttu-id="35450-121">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="35450-121">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
