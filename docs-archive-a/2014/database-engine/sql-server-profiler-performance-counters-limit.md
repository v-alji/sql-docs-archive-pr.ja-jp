---
title: SQL Server プロファイラー-パフォーマンスカウンターの制限 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27bda135abaf9d91b078e36a69a87098a734acbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736697"
---
# <a name="sql-server-profiler---performance-counters-limit"></a><span data-ttu-id="893fc-102">[SQL Server Profiler] - [パフォーマンス カウンター制限ダイアログ]</span><span class="sxs-lookup"><span data-stu-id="893fc-102">SQL Server Profiler - Performance Counters Limit</span></span>
  <span data-ttu-id="893fc-103">[パフォーマンス カウンター制限ダイアログ] ダイアログ ボックスを使用すると、システム モニターのパフォーマンス ログ ファイルと [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] トレースを相関させるときに、ファイルからの情報を制限できます。</span><span class="sxs-lookup"><span data-stu-id="893fc-103">Use the Performance Counters Limit dialog box to limit the information from a System Monitor performance log file when correlating it with a [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace.</span></span> <span data-ttu-id="893fc-104">このダイアログ ボックスで、相関のために表示して使用するカウンターを選択できます。</span><span class="sxs-lookup"><span data-stu-id="893fc-104">You can use this dialog box to select counters that should be displayed and used for correlation.</span></span>  
  
 <span data-ttu-id="893fc-105">**[パフォーマンス カウンター制限ダイアログ ボックス]** ダイアログ ボックスには、パフォーマンス ログ ファイルに含まれているパフォーマンス オブジェクトおよびカウンターによって値が入力されます。</span><span class="sxs-lookup"><span data-stu-id="893fc-105">The **Performance Counters Limit** dialog box is populated with the performance objects and counters that the performance log file contains.</span></span>  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a><span data-ttu-id="893fc-106">トレースと相関させるパフォーマンス オブジェクトおよびカウンターを選択するには</span><span class="sxs-lookup"><span data-stu-id="893fc-106">To select performance objects and counters to correlate with a trace</span></span>  
  
1.  <span data-ttu-id="893fc-107">パフォーマンス オブジェクトを展開して、パフォーマンス ログ ファイルに含まれているカウンターを確認します。</span><span class="sxs-lookup"><span data-stu-id="893fc-107">Expand a performance object to see which counters are included in the performance log file.</span></span>  
  
2.  <span data-ttu-id="893fc-108">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] トレース ファイルと相関させる対象カウンターをオンにします。</span><span class="sxs-lookup"><span data-stu-id="893fc-108">Check the counters that you want to correlate with the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace file.</span></span>  
  
     <span data-ttu-id="893fc-109">パフォーマンス オブジェクトに対してすべてのカウンターを選択する場合は、パフォーマンス オブジェクトの横にあるボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="893fc-109">If you want to select all counters for a performance object, check the box that is adjacent to the performance object.</span></span> <span data-ttu-id="893fc-110">コンピューターを示している最上位ノードをオンにすると、パフォーマンス ログ ファイル内のすべてのパフォーマンス オブジェクトおよびカウンターが選択されます。</span><span class="sxs-lookup"><span data-stu-id="893fc-110">Checking the topmost node, which indicates the computer, selects all performance objects and counters contained in the performance log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893fc-111">参照</span><span class="sxs-lookup"><span data-stu-id="893fc-111">See Also</span></span>  
 [<span data-ttu-id="893fc-112">トレースと Windows パフォーマンス ログ データの関連付け &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="893fc-112">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  
