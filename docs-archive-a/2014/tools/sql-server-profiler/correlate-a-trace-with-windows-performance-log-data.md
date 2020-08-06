---
title: トレースと Windows パフォーマンス ログ データの関連付け | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 879441c948f0ad04b971159a37ec0dcec90e3ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711281"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a><span data-ttu-id="671dc-102">トレースと Windows パフォーマンス ログ データの関連付け</span><span class="sxs-lookup"><span data-stu-id="671dc-102">Correlate a Trace with Windows Performance Log Data</span></span>
  <span data-ttu-id="671dc-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用すると、Microsoft Windows パフォーマンス ログを開き、トレースと関連付けるカウンターを選択し、選択したパフォーマンス カウンターをトレースと共に [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のグラフィカル ユーザー インターフェイスに表示できます。</span><span class="sxs-lookup"><span data-stu-id="671dc-103">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can open a Microsoft Windows performance log, choose the counters you want to correlate with a trace, and display the selected performance counters alongside the trace in the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] graphical user interface.</span></span> <span data-ttu-id="671dc-104">トレース ウィンドウでイベントを選択すると、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] の [システム モニター] データ ウィンドウ画面の赤い縦棒で、選択したトレース イベントに関連付けられているパフォーマンス ログ データが示されます。</span><span class="sxs-lookup"><span data-stu-id="671dc-104">When you select an event in the trace window, a vertical red bar in the System Monitor data window pane of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indicates the performance log data that correlates with the selected trace event.</span></span>  
  
 <span data-ttu-id="671dc-105">トレースをパフォーマンス カウンターに関連付けるには、**StartTime** および **EndTime** データ列を含んでいるトレース ファイルまたはテーブルを開き、**の**[ファイル][!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] メニューで **[パフォーマンス データのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="671dc-105">To correlate a trace with performance counters, open a trace file or table that contains the **StartTime** and **EndTime** data columns, and then click **Import Performance Data** on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File** menu.</span></span> <span data-ttu-id="671dc-106">パフォーマンス ログを開き、トレースに関連付けるシステム モニター オブジェクトおよびカウンターを選択します。</span><span class="sxs-lookup"><span data-stu-id="671dc-106">You can then open a performance log, and select the System Monitor objects and counters that you want to correlate with the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671dc-107">参照</span><span class="sxs-lookup"><span data-stu-id="671dc-107">See Also</span></span>  
 [<span data-ttu-id="671dc-108">トレースと Windows パフォーマンス ログ データの関連付け &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="671dc-108">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
