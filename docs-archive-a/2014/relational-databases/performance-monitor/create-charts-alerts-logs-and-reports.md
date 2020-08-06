---
title: グラフ、警告、ログ、およびレポートの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], charts and reports
- charts [SQL Server]
- reports [SQL Server]
- reports [SQL Server], creating
- Windows System Monitor [SQL Server], charts and reports
- logs [SQL Server], System Monitor
- System Monitor [SQL Server], logs
- Windows System Monitor [SQL Server], logs
ms.assetid: c9162b37-e5dc-43d1-a3aa-1e9ebc69fecc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a0c95c3f483a8af3e3e68d9c5c7d3caf44350d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739751"
---
# <a name="create-charts-alerts-logs-and-reports"></a><span data-ttu-id="a0271-102">グラフ、警告、ログ、およびレポートの作成</span><span class="sxs-lookup"><span data-stu-id="a0271-102">Create Charts, Alerts, Logs, and Reports</span></span>
  <span data-ttu-id="a0271-103">システム モニターを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを監視するためのグラフ、警告、ログ、およびレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-103">System Monitor lets you create charts, alerts, logs, and reports to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="charts"></a><span data-ttu-id="a0271-104">グラフ</span><span class="sxs-lookup"><span data-stu-id="a0271-104">Charts</span></span>  
 <span data-ttu-id="a0271-105">グラフを使用すると、CPU 使用率やディスク I/O など、選択したオブジェクトとカウンターの現在のパフォーマンスを監視できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-105">Charts can monitor the current performance of selected objects and counters; for example, the CPU usage or disk I/O.</span></span> <span data-ttu-id="a0271-106">システム モニターのオブジェクトやカウンターのさまざまな組み合わせをグラフに追加できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-106">You can add to a chart various combinations of System Monitor objects and counters.</span></span> <span data-ttu-id="a0271-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のオブジェクトやカウンターをグラフに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0271-107">You also can add [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows objects and counters to a chart.</span></span>  
  
 <span data-ttu-id="a0271-108">各グラフは、監視する情報のサブセットを示します。</span><span class="sxs-lookup"><span data-stu-id="a0271-108">Each chart represents a subset of information you want to monitor.</span></span> <span data-ttu-id="a0271-109">たとえば、1 つのグラフでメモリ使用率の統計を追跡して、もう 1 つのグラフでディスク I/O 統計を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-109">For example, one chart can track memory usage statistics and a second chart can track disk I/O statistics.</span></span>  
  
 <span data-ttu-id="a0271-110">グラフを使用すると、次の作業に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a0271-110">Using a chart can be useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="a0271-111">コンピューターまたはアプリケーションが遅い原因または非効率な原因を調査します。</span><span class="sxs-lookup"><span data-stu-id="a0271-111">Investigating why a computer or application is slow or inefficient.</span></span>  
  
-   <span data-ttu-id="a0271-112">システムを継続的に監視して、断続的なパフォーマンスの問題を検出します。</span><span class="sxs-lookup"><span data-stu-id="a0271-112">Continually monitoring systems to find intermittent performance problems.</span></span>  
  
-   <span data-ttu-id="a0271-113">処理容量を増加させる必要があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="a0271-113">Discovering why you need to increase capacity.</span></span>  
  
-   <span data-ttu-id="a0271-114">線グラフで傾向を表示します。</span><span class="sxs-lookup"><span data-stu-id="a0271-114">Displaying a trend as a line chart.</span></span>  
  
-   <span data-ttu-id="a0271-115">ヒストグラムで比較します。</span><span class="sxs-lookup"><span data-stu-id="a0271-115">Displaying a comparison as a histogram chart.</span></span>  
  
 <span data-ttu-id="a0271-116">現在発生しているイベントを監視する場合など、ローカル コンピューターまたはリモート コンピューターを短い時間、リアルタイムで監視するのにグラフは便利です。</span><span class="sxs-lookup"><span data-stu-id="a0271-116">Charts are useful for short-term, real-time monitoring of a local or remote computer (for example, when you want to monitor an event as it occurs).</span></span>  
  
## <a name="alerts"></a><span data-ttu-id="a0271-117">警告</span><span class="sxs-lookup"><span data-stu-id="a0271-117">Alerts</span></span>  
 <span data-ttu-id="a0271-118">システム モニターで警告を使用すると、特定のイベントを追跡して、要求に応じてそのイベントを通知できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-118">Using alerts, System Monitor tracks specific events and notifies you of these events as requested.</span></span> <span data-ttu-id="a0271-119">警告ログは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のオブジェクトに対して選択したカウンターとインスタンスについて現在のパフォーマンスを監視できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-119">An alert log can monitor the current performance of selected counters and instances for objects in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a0271-120">カウンターが指定した値を超えたときに、ログはそのイベントの日付と時刻を記録します。</span><span class="sxs-lookup"><span data-stu-id="a0271-120">When a counter exceeds a given value, the log records the date and time of the event.</span></span> <span data-ttu-id="a0271-121">イベントはネットワーク警告を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0271-121">An event can also generate a network alert.</span></span> <span data-ttu-id="a0271-122">また、イベントが初めて発生したとき、またはイベントが発生するたびに、特定のプログラムを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-122">You can have a specified program run the first time or every time an event occurs.</span></span> <span data-ttu-id="a0271-123">たとえば、警告はすべてのシステム管理者に対して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのディスク容量が不足していることを示すネットワーク メッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-123">For example, an alert can send a network message to all system administrators that the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is getting low on disk space.</span></span>  
  
## <a name="logs"></a><span data-ttu-id="a0271-124">ログ</span><span class="sxs-lookup"><span data-stu-id="a0271-124">Logs</span></span>  
 <span data-ttu-id="a0271-125">ログを使用すると、選択したオブジェクトとコンピューターの現在の利用状況について情報を記録し、後にその情報を表示および分析することができます。</span><span class="sxs-lookup"><span data-stu-id="a0271-125">Logs allow you to record information on the current activity of selected objects and computers for later viewing and analysis.</span></span> <span data-ttu-id="a0271-126">複数のシステムからデータを収集して、1 つのログ ファイルに記録することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0271-126">You can collect data from multiple systems into a single log file.</span></span> <span data-ttu-id="a0271-127">たとえば、さまざまなコンピューターで選択したオブジェクトのパフォーマンスについて情報を蓄積するために、さまざまなログを作成して、後に分析のために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-127">For example, you can create different logs to accumulate information about the performance of selected objects on various computers for future analysis.</span></span> <span data-ttu-id="a0271-128">ファイル名を付けて選択した設定を保存すれば、比較のために同様の情報についてもう 1 つのログを作成するときに再使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-128">You can save these selections under a file name and reuse them when you want to create another log of similar information for comparison.</span></span>  
  
 <span data-ttu-id="a0271-129">ログ ファイルには、トラブルシューティングやプランニングに役立つ豊富な情報が記録されています。</span><span class="sxs-lookup"><span data-stu-id="a0271-129">Log files provide a wealth of information for troubleshooting or planning.</span></span> <span data-ttu-id="a0271-130">現在の利用状況に関するグラフ、警告、およびレポートが即時のフィードバックを与えるのに対して、ログ ファイルは、長期間にわたってカウンターを追跡できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-130">Whereas charts, alerts, and reports on current activity provide instant feedback, log files enable you to track counters over a long period of time.</span></span> <span data-ttu-id="a0271-131">このため、情報をより徹底的に検査し、システムのパフォーマンスを文書化することができます。</span><span class="sxs-lookup"><span data-stu-id="a0271-131">Thus, you can examine information more thoroughly and document system performance.</span></span>  
  
## <a name="reports"></a><span data-ttu-id="a0271-132">Reports</span><span class="sxs-lookup"><span data-stu-id="a0271-132">Reports</span></span>  
 <span data-ttu-id="a0271-133">レポートを使用すると、選択したオブジェクトに対して、絶えず変化し続けるカウンター値とインスタンス値を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a0271-133">Reports allow you to display constantly changing counter and instance values for selected objects.</span></span> <span data-ttu-id="a0271-134">値は、各インスタンスの列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a0271-134">Values appear in columns for each instance.</span></span> <span data-ttu-id="a0271-135">レポート間隔を調整したり、スナップショットを印刷したり、データをエクスポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a0271-135">You can adjust report intervals, print snapshots, and export data.</span></span> <span data-ttu-id="a0271-136">raw 番号を表示する必要がある場合には、レポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0271-136">Use reports when you need to display the raw numbers.</span></span>  
  
 <span data-ttu-id="a0271-137">グラフ、警告、ログ、およびレポートの作成、または Windows オブジェクトとカウンターの詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0271-137">For more information about creating charts, alerts, logs, and reports, or about Windows objects and counters, see the Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0271-138">参照</span><span class="sxs-lookup"><span data-stu-id="a0271-138">See Also</span></span>  
 [<span data-ttu-id="a0271-139">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="a0271-139">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
