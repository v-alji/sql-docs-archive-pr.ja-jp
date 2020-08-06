---
title: SQL Server プロファイラーを使用して Analysis Services を監視する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e144c1d858670f8a46b164ffc9885e6e082c4b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633419"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a><span data-ttu-id="eb4ec-102">SQL Server Profiler を使用した Analysis Services の監視</span><span class="sxs-lookup"><span data-stu-id="eb4ec-102">Use SQL Server Profiler to Monitor Analysis Services</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="eb4ec-103">では、バッチまたはトランザクションの開始などのエンジン プロセス イベントが追跡され、そのようなイベントに関するデータがキャプチャされて、サーバーおよびデータベースの利用状況 (ユーザー クエリ、ログインの利用状況など) を監視できます。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-103">tracks engine process events, such as the start of a batch or a transaction, and it captures data about those events, thus enabling you to monitor server and database activity (for example, user queries or login activity).</span></span> <span data-ttu-id="eb4ec-104">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはファイルにキャプチャして、後で分析できます。また、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の同じインスタンスまたは別のインスタンスでキャプチャしたイベントを再生して、何が起こったかを正確に確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-104">You can capture [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] data to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or a file for later analysis, and you can also replay the events captured on the same or another [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to see exactly what happened.</span></span> <span data-ttu-id="eb4ec-105">イベントはリアルタイムまたはステップごとに再生できます。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-105">You can replay events in real time or on a step-by-step basis.</span></span> <span data-ttu-id="eb4ec-106">また、同じコンピューター上のパフォーマンス カウンターと共にトレース イベントを実行すると非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-106">It is also very useful to run the trace events along with the Performance counters on the same machine.</span></span> <span data-ttu-id="eb4ec-107">このプロファイラーでは、これらの 2 つを時間に基づいて関連付けることができます。また、1 つの時間軸で同時に表示できます。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-107">The profiler can correlate these two based on time and display them together along a single timeline.</span></span> <span data-ttu-id="eb4ec-108">パフォーマンス カウンターは集計を表示しますが、トレース イベントではより詳細なデータが得られます。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-108">Trace events will give you more details while Performance counters give you an aggregate view.</span></span> <span data-ttu-id="eb4ec-109">トレースを作成および実行する方法については、「 [再生用のプロファイラー トレースの作成 &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-109">For information about how to create and run traces, see [Create Profiler Traces for Replay &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md).</span></span>  
  
 <span data-ttu-id="eb4ec-110">このトピックでは、次の内容について紹介します。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-110">The following table describes the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb4ec-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="eb4ec-111">In This Section</span></span>  
  
|<span data-ttu-id="eb4ec-112">トピック</span><span class="sxs-lookup"><span data-stu-id="eb4ec-112">Topic</span></span>|<span data-ttu-id="eb4ec-113">説明</span><span class="sxs-lookup"><span data-stu-id="eb4ec-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="eb4ec-114">SQL Server Profiler による Analysis Services の監視の概要</span><span class="sxs-lookup"><span data-stu-id="eb4ec-114">Introduction to Monitoring Analysis Services with SQL Server Profiler</span></span>](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|<span data-ttu-id="eb4ec-115">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを監視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-115">Describes how to use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to monitor an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>|  
|[<span data-ttu-id="eb4ec-116">再生用のプロファイラー トレースの作成 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eb4ec-116">Create Profiler Traces for Replay &#40;Analysis Services&#41;</span></span>](create-profiler-traces-for-replay-analysis-services.md)|<span data-ttu-id="eb4ec-117">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して再生用トレースを作成するための要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-117">Describes the requirements for creating a trace for replay by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="eb4ec-118">Analysis Services トレース イベント</span><span class="sxs-lookup"><span data-stu-id="eb4ec-118">Analysis Services Trace Events</span></span>](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|<span data-ttu-id="eb4ec-119">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のイベント クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-119">Describes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] event classes.</span></span> <span data-ttu-id="eb4ec-120">これらのイベント クラスは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって生成されるアクションにマップされ、トレースの再生に使用されます。</span><span class="sxs-lookup"><span data-stu-id="eb4ec-120">These event classes map to actions generated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and are used for trace replays.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb4ec-121">参照</span><span class="sxs-lookup"><span data-stu-id="eb4ec-121">See Also</span></span>  
 [<span data-ttu-id="eb4ec-122">Analysis Services インスタンスの監視</span><span class="sxs-lookup"><span data-stu-id="eb4ec-122">Monitor an Analysis Services Instance</span></span>](monitor-an-analysis-services-instance.md)  
  
  
