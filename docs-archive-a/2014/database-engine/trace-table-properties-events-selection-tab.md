---
title: '[トレーステーブルのプロパティ] ([イベントの選択] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetableproperties.eventsselection.f1
helpviewer_keywords:
- Trace Table Properties dialog box
ms.assetid: fa21df6a-b6b5-4b15-9104-957385821594
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2e72f299c9d83762876ce250f750924430ba2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741210"
---
# <a name="trace-table-properties-events-selection-tab"></a><span data-ttu-id="5c9a8-102">[トレース テーブルのプロパティ] ([イベントの選択] タブ)</span><span class="sxs-lookup"><span data-stu-id="5c9a8-102">Trace Table Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="5c9a8-103">**[トレース テーブルのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用すると、トレースのイベントやデータ列プロパティを表示したり、トレースからイベントまたは列を削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-103">Use the **Events Selection** tab of the **Trace Table Properties** dialog box to view the events and data column properties of the trace or to remove events or columns from the trace.</span></span>  
  
 <span data-ttu-id="5c9a8-104">このウィンドウを表示するには、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を使用してトレース テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace table.</span></span> <span data-ttu-id="5c9a8-105">次に、[**ファイル**] メニューの [**プロパティ**] をクリックし、[**イベントの選択**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-105">Then on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5c9a8-106">Options</span><span class="sxs-lookup"><span data-stu-id="5c9a8-106">Options</span></span>  
 <span data-ttu-id="5c9a8-107">**[イベント]** 列</span><span class="sxs-lookup"><span data-stu-id="5c9a8-107">**Events** column</span></span>  
 <span data-ttu-id="5c9a8-108">イベント カテゴリにより分類された、ビューによりトレースされるイベントです。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="5c9a8-109">イベントのチェック ボックスをオンにするか、データ列をオンにすることでイベントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-109">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="5c9a8-110">イベントのチェック ボックスをオンにすると、そのイベントで使用できるデータ列がすべて選択されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-110">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="5c9a8-111">イベントのデータ列をオンにすると、イベントが選択されるだけでなく、そのほかに必要な列がすべて自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-111">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="5c9a8-112">トレース ファイルまたはトレース テーブルを表示した場合、イベントのチェック ボックスやデータ列をオフにすることで、トレース ウィンドウに表示されるデータ量が減り、分析が容易になります。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-112">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="5c9a8-113">列のフィルターを変更して、トレース ウィンドウに表示されるデータ量を減らすこともできます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-113">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="5c9a8-114">イベント クラスの詳細については、「 [SQL Server イベント クラスの参照](../relational-databases/event-classes/sql-server-event-class-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-114">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="5c9a8-115">その他のデータ列</span><span class="sxs-lookup"><span data-stu-id="5c9a8-115">Other data columns</span></span>  
 <span data-ttu-id="5c9a8-116">トレースされるデータ列を表示します。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-116">View traced data columns.</span></span> <span data-ttu-id="5c9a8-117">トレースに含まれる各イベントでは、トレースの関連するデータ列は既定ですべてオンになっています。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-117">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="5c9a8-118">フィルターを指定するには、データ列のヘッダーをクリックし、フィルター基準を入力します。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-118">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="5c9a8-119">フィルター選択されるデータ列については、 **[フィルターの編集]** ダイアログ ボックスの列ラベルの左側にフィルターのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-119">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="5c9a8-120">**[すべてのイベントを表示する]**</span><span class="sxs-lookup"><span data-stu-id="5c9a8-120">**Show all events**</span></span>  
 <span data-ttu-id="5c9a8-121">表示できるイベントをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-121">Show all available events.</span></span> <span data-ttu-id="5c9a8-122">既定では、 **[イベントの選択]** グリッドで選択されている行だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-122">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="5c9a8-123">このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないイベントがすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-123">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="5c9a8-124">**[すべてのイベントを表示する]** がオンで、トレース ファイルまたはトレース テーブルを表示している場合、トレースに記録されたすべてのイベントがトレース ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-124">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="5c9a8-125">**[すべての列を表示]**</span><span class="sxs-lookup"><span data-stu-id="5c9a8-125">**Show all columns**</span></span>  
 <span data-ttu-id="5c9a8-126">表示できるデータ列をすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-126">Show all available data columns.</span></span> <span data-ttu-id="5c9a8-127">既定では、選択されているデータ列だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-127">By default, only data columns that are selected display.</span></span> <span data-ttu-id="5c9a8-128">このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないデータ列がすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-128">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="5c9a8-129">**列フィルター**</span><span class="sxs-lookup"><span data-stu-id="5c9a8-129">**Column Filters**</span></span>  
 <span data-ttu-id="5c9a8-130">**[フィルターの編集]** ダイアログ ボックスを起動します。ここでは、データ列のラベルの左側にフィルターのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-130">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label.</span></span> <span data-ttu-id="5c9a8-131">このダイアログ ボックスを使用して、データ列のフィルターを編集できます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-131">You can use this dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="5c9a8-132">**[列の構成]**</span><span class="sxs-lookup"><span data-stu-id="5c9a8-132">**Organize Columns**</span></span>  
 <span data-ttu-id="5c9a8-133">**[イベント]** およびトレースするデータ列を選択した後、 **[列の構成]** をクリックすると、トレース結果のウィンドウの列が並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="5c9a8-133">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9a8-134">参照</span><span class="sxs-lookup"><span data-stu-id="5c9a8-134">See Also</span></span>  
 <span data-ttu-id="5c9a8-135">[トレーステーブル &#40;SQL Server プロファイラーを開き&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5c9a8-135">[Open a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5c9a8-136">[SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="5c9a8-136">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="5c9a8-137">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="5c9a8-137">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
