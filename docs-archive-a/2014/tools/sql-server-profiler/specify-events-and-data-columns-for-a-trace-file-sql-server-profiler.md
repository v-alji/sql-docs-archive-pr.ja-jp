---
title: トレース ファイルに含めるイベントとデータ列の指定 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- adding events
- traces [SQL Server], data columns
- deleting events
- removing events
- traces [SQL Server], events
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
author: stevestein
ms.author: sstein
ms.openlocfilehash: ffb8639a187f1e7e091e382031886659bd47d7d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630724"
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a><span data-ttu-id="d0f9c-102">トレース ファイルに含めるイベントとデータ列の指定 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="d0f9c-102">Specify Events and Data Columns for a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="d0f9c-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用してトレースに含めるイベント クラスとデータ列を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-103">This topic describes how to specify event classes and data columns for traces by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a><span data-ttu-id="d0f9c-104">トレースに含めるイベントとデータ列を指定するには</span><span class="sxs-lookup"><span data-stu-id="d0f9c-104">To specify events and data columns for a trace</span></span>  
  
1.  <span data-ttu-id="d0f9c-105">**[トレースのプロパティ]** または **[トレース テンプレートのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-105">On the **Trace Properties** or **Trace Template Properties** dialog box, click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="d0f9c-106">**[イベントの選択]** タブにはグリッド コントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-106">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="d0f9c-107">グリッド コントロールは、トレース可能な各イベント クラスを含んでいるテーブルです。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-107">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="d0f9c-108">このテーブルには、各イベント クラスが 1 行で表示されます。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-108">The table contains one row for each event class.</span></span> <span data-ttu-id="d0f9c-109">表示されるイベント クラスは、接続しているサーバーの種類とバージョンによって多少異なります。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-109">The event classes can differ slightly depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="d0f9c-110">イベント クラスは、グリッドの **[イベント]** 列で識別され、イベント カテゴリ別に分類されています。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-110">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="d0f9c-111">残りの列には、各イベント クラスに対応するデータ列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-111">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
2.  <span data-ttu-id="d0f9c-112">**[イベントの選択]** タブで、グリッド コントロールを使用して、トレース ファイルに対するイベントとデータ列の追加または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-112">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file.</span></span>  
  
3.  <span data-ttu-id="d0f9c-113">トレースからイベントを削除するには、各イベント クラスの **[Events]** 列のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-113">To remove events from the trace, clear the check box in the **Events** column for each event class.</span></span>  
  
4.  <span data-ttu-id="d0f9c-114">トレースにイベントを含めるには、各イベント クラスの **[Events]** 列のチェック ボックスをオンにするか、イベントに対応するデータ列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-114">To include events in a trace, check the box in the **Events** column for each event class, or check a data column that corresponds to an event.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d0f9c-115">このトレースをシステム モニターやパフォーマンス モニターのデータと関連付ける場合は、 **Start Time** データ列と **End Time** データ列の両方をトレースに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-115">If the trace is going be correlated with System Monitor or Performance Monitor data, both **Start Time** and **End Time** data columns must be included in the trace.</span></span>  
  
 <span data-ttu-id="d0f9c-116">イベント クラスを含める場合、イベントに対応するイベント クラスのチェック ボックスをオンにしていると、関連するデータ列もすべてトレースに含まれます。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-116">When you include an event class, every associated data column is also included to the trace, if you have checked the box corresponding to an event.</span></span> <span data-ttu-id="d0f9c-117">特定の列のチェック ボックスをオンにしている場合は、その列だけがトレースに含まれます。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-117">If you checked the box for a particular column, only that column is included in the trace.</span></span>  
  
1.  <span data-ttu-id="d0f9c-118">イベント クラスからデータ列を削除するには、イベント クラス行のデータ列のチェック ボックスをオフにするか、列ヘッダーを右クリックして、 **[列の選択解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-118">To remove data columns from an event class, clear the check boxes from the data column in the event class row, or right-click on the column header and select the **Deselect column** option.</span></span>  
  
2.  <span data-ttu-id="d0f9c-119">必要に応じて、トレースにフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-119">Optionally, apply filters to the trace.</span></span> <span data-ttu-id="d0f9c-120">詳細については、「[トレース内のイベントへのフィルターの適用 &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0f9c-120">For more information, see [Filter Events in a Trace &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f9c-121">参照</span><span class="sxs-lookup"><span data-stu-id="d0f9c-121">See Also</span></span>  
 [<span data-ttu-id="d0f9c-122">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d0f9c-122">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
