---
title: SQL Server の ExecStatistics オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d1a50c97add4708a58b9edc45fd49982b97a51ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633093"
---
# <a name="sql-server-execstatistics-object"></a><span data-ttu-id="015a3-102">SQL Server の ExecStatistics オブジェクト</span><span class="sxs-lookup"><span data-stu-id="015a3-102">SQL Server, ExecStatistics Object</span></span>
  <span data-ttu-id="015a3-103">Microsoft SQL Server の **SQLServer:ExecStatistics** オブジェクトには、さまざまな実行を監視するためのカウンターがあります。</span><span class="sxs-lookup"><span data-stu-id="015a3-103">The **SQLServer:ExecStatistics** object in Microsoft SQL Server provides counters to monitor various executions.</span></span>  
  
 <span data-ttu-id="015a3-104">次の表では、SQL Server の **Exec Statistics** カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="015a3-104">This table describes the SQL Server **Exec Statistics** counters.</span></span>  
  
|<span data-ttu-id="015a3-105">SQL Server Exec Statistics のカウンター</span><span class="sxs-lookup"><span data-stu-id="015a3-105">SQL Server Exec Statistics counters</span></span>|<span data-ttu-id="015a3-106">説明</span><span class="sxs-lookup"><span data-stu-id="015a3-106">Description</span></span>|  
|-----------------------------------------|-----------------|  
|<span data-ttu-id="015a3-107">**Distributed Query**</span><span class="sxs-lookup"><span data-stu-id="015a3-107">**Distributed Query**</span></span>|<span data-ttu-id="015a3-108">分散クエリの実行に関連する統計データ。</span><span class="sxs-lookup"><span data-stu-id="015a3-108">Statistics relevant to execution of distributed queries.</span></span>|  
|<span data-ttu-id="015a3-109">**DTC calls**</span><span class="sxs-lookup"><span data-stu-id="015a3-109">**DTC calls**</span></span>|<span data-ttu-id="015a3-110">DTC 呼び出しの実行に関連する統計データ。</span><span class="sxs-lookup"><span data-stu-id="015a3-110">Statistics relevant to execution of DTC calls.</span></span>|  
|<span data-ttu-id="015a3-111">**Extended Procedures**</span><span class="sxs-lookup"><span data-stu-id="015a3-111">**Extended Procedures**</span></span>|<span data-ttu-id="015a3-112">拡張プロシージャの実行に関連する統計データ。</span><span class="sxs-lookup"><span data-stu-id="015a3-112">Statistics relevant to execution of extended procedures.</span></span>|  
|<span data-ttu-id="015a3-113">**OLEDB calls**</span><span class="sxs-lookup"><span data-stu-id="015a3-113">**OLEDB calls**</span></span>|<span data-ttu-id="015a3-114">OLEDB 呼び出しの実行に関連する統計データ。</span><span class="sxs-lookup"><span data-stu-id="015a3-114">Statistics relevant to execution of OLEDB calls.</span></span>|  
  
 <span data-ttu-id="015a3-115">オブジェクトの各カウンターには、次のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="015a3-115">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="015a3-116">Item</span><span class="sxs-lookup"><span data-stu-id="015a3-116">Item</span></span>|<span data-ttu-id="015a3-117">説明</span><span class="sxs-lookup"><span data-stu-id="015a3-117">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="015a3-118">**Average execution time (ms)**</span><span class="sxs-lookup"><span data-stu-id="015a3-118">**Average execution time (ms)**</span></span>|<span data-ttu-id="015a3-119">選択した種類の実行の平均実行時間。</span><span class="sxs-lookup"><span data-stu-id="015a3-119">Average execution time of the selected type of execution.</span></span>|  
|<span data-ttu-id="015a3-120">**Cumulative execution time (ms) per second**</span><span class="sxs-lookup"><span data-stu-id="015a3-120">**Cumulative execution time (ms) per second**</span></span>|<span data-ttu-id="015a3-121">選択した種類の実行の 1 秒あたりの累積実行時間。</span><span class="sxs-lookup"><span data-stu-id="015a3-121">Aggregated execution time per second, of the selected type of execution.</span></span>|  
|<span data-ttu-id="015a3-122">**Execs in progress**</span><span class="sxs-lookup"><span data-stu-id="015a3-122">**Execs in progress**</span></span>|<span data-ttu-id="015a3-123">選択した種類の実行のうち現在進行中の数。</span><span class="sxs-lookup"><span data-stu-id="015a3-123">Number of execs in progress of the selected type of execution.</span></span>|  
|<span data-ttu-id="015a3-124">**Exec started per second**</span><span class="sxs-lookup"><span data-stu-id="015a3-124">**Exec started per second**</span></span>|<span data-ttu-id="015a3-125">選択した種類の実行が 1 秒あたりに開始される数。</span><span class="sxs-lookup"><span data-stu-id="015a3-125">Number of exes started per second of the selected type of execution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="015a3-126">参照</span><span class="sxs-lookup"><span data-stu-id="015a3-126">See Also</span></span>  
 [<span data-ttu-id="015a3-127">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="015a3-127">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
