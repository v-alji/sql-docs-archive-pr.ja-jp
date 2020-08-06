---
title: Analysis Services インスタンスを監視する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- monitoring [Analysis Services - multidimensional data]
- multidimensional data [Analysis Services], monitoring
- monitoring performance [SQL Server], SQL Server Profiler
- performance [SQL Server], monitoring tools
ms.assetid: 2f0ab717-05f3-427e-b8cd-a8bdca374add
author: minewiskan
ms.author: owend
ms.openlocfilehash: b98037ea9f26c339cdf7aba22c37e2cfb3dfbb97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643001"
---
# <a name="monitor-an-analysis-services-instance"></a><span data-ttu-id="a6038-102">Analysis Services インスタンスの監視</span><span class="sxs-lookup"><span data-stu-id="a6038-102">Monitor an Analysis Services Instance</span></span>
  <span data-ttu-id="a6038-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] またはパフォーマンス モニター ( [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] PerfMon **とも呼ばれるアプリケーション) を使用して、** のパフォーマンスを監視できます。</span><span class="sxs-lookup"><span data-stu-id="a6038-103">You can monitor the performance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor, an application sometimes referred to as **PerfMon**.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="a6038-104">レースを作成および管理し、トレースの結果を分析および再生できます。</span><span class="sxs-lookup"><span data-stu-id="a6038-104">lets you create and manage traces and analyze and replay trace results.</span></span> <span data-ttu-id="a6038-105">パフォーマンス モニターでは、特定のカウンターでインデックスを付けたサーバーの状態が報告されます。これについては、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="a6038-105">Performance Monitor reports on server status, as indexed through certain counters, which are discussed in the next section.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6038-106">操作の監視の詳細については、「 [SQL Server 2008 R2 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6038-106">For more information about monitoring, see the [SQL Server 2008 R2 Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6038-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a6038-107">In This Section</span></span>  
 <span data-ttu-id="a6038-108">監視の詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6038-108">Follow these links to learn more about monitoring.</span></span>  
  
 [<span data-ttu-id="a6038-109">Analysis Services トレース イベント</span><span class="sxs-lookup"><span data-stu-id="a6038-109">Analysis Services Trace Events</span></span>](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)  
  
 [<span data-ttu-id="a6038-110">SQL Server Profiler を使用した Analysis Services の監視</span><span class="sxs-lookup"><span data-stu-id="a6038-110">Use SQL Server Profiler to Monitor Analysis Services</span></span>](use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 [<span data-ttu-id="a6038-111">SQL Server 拡張イベント &#40;Xevent&#41; を使用して監視 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="a6038-111">Use SQL Server Extended Events &#40;XEvents&#41; to Monitor Analysis Services</span></span>](../instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
 [<span data-ttu-id="a6038-112">動的管理ビュー (DMV) を使用した Analysis Services の監視</span><span class="sxs-lookup"><span data-stu-id="a6038-112">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
 [<span data-ttu-id="a6038-113">パフォーマンス カウンター (SSAS)</span><span class="sxs-lookup"><span data-stu-id="a6038-113">Performance Counters &#40;SSAS&#41;</span></span>](performance-counters-ssas.md)  
  
  
