---
title: '[トレースファイルのプロパティ] ([イベントの選択] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracefileproperties.eventsselection.f1
helpviewer_keywords:
- Trace File Properties dialog box
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abfadc2b1df4cda039d7e413e5ba0c7777e7c04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718638"
---
# <a name="trace-file-properties-events-selection-tab"></a><span data-ttu-id="6cb0e-102">[トレース ファイルのプロパティ] ([イベントの選択] タブ)</span><span class="sxs-lookup"><span data-stu-id="6cb0e-102">Trace File Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="6cb0e-103">**[トレース ファイルのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用すると、トレースの列プロパティを表示したり、トレースからデータ列を削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-103">Use the **Events Selection** tab of the **Trace File Template Properties** dialog box to view the column properties of the trace or remove data columns from the trace.</span></span>  
  
 <span data-ttu-id="6cb0e-104">このウィンドウを表示するには、トレース ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-104">To view this window, open a trace file.</span></span> <span data-ttu-id="6cb0e-105">次に、 **[ファイル]** メニューの **[プロパティ]** をクリックした後、 **[イベントの選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-105">Then, on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6cb0e-106">Options</span><span class="sxs-lookup"><span data-stu-id="6cb0e-106">Options</span></span>  
 <span data-ttu-id="6cb0e-107">**[イベント]** 列</span><span class="sxs-lookup"><span data-stu-id="6cb0e-107">**Events** column</span></span>  
 <span data-ttu-id="6cb0e-108">イベント カテゴリにより分類された、ビューによりトレースされるイベントです。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="6cb0e-109">最初は、トレースのイベントがすべて選択されています。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-109">Initially, all events in the trace are selected.</span></span> <span data-ttu-id="6cb0e-110">イベントのチェック ボックスをオンにするか、データ列をオンにすることでイベントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-110">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="6cb0e-111">イベントのチェック ボックスをオンにすると、そのイベントで使用できるデータ列がすべて選択されます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-111">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="6cb0e-112">イベントのデータ列をオンにすると、イベントが選択されるだけでなく、そのほかに必要な列がすべて自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-112">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="6cb0e-113">トレース ファイルまたはトレース テーブルを表示した場合、イベントのチェック ボックスやデータ列をオフにすることで、トレース ウィンドウに表示されるデータ量が減り、分析が容易になります。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-113">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="6cb0e-114">列のフィルターを変更して、トレース ウィンドウに表示されるデータ量を減らすこともできます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-114">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="6cb0e-115">イベント クラスの詳細については、「 [SQL Server イベント クラスの参照](../relational-databases/event-classes/sql-server-event-class-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-115">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="6cb0e-116">データ列</span><span class="sxs-lookup"><span data-stu-id="6cb0e-116">Data Columns</span></span>  
 <span data-ttu-id="6cb0e-117">トレースされるデータ列を表示します。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-117">View traced data columns.</span></span> <span data-ttu-id="6cb0e-118">トレースに含まれる各イベントでは、トレースの関連するデータ列は既定ですべてオンになっています。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-118">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="6cb0e-119">フィルターを指定するには、データ列のヘッダーをクリックし、フィルター基準を入力します。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-119">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="6cb0e-120">フィルター選択されるデータ列については、 **[フィルターの編集]** ダイアログ ボックスの列ラベルの左側にフィルターのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-120">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="6cb0e-121">**[すべてのイベントを表示する]**</span><span class="sxs-lookup"><span data-stu-id="6cb0e-121">**Show all events**</span></span>  
 <span data-ttu-id="6cb0e-122">表示できるイベントをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-122">Show all available events.</span></span> <span data-ttu-id="6cb0e-123">既定では、 **[イベントの選択]** グリッドで選択されている行だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-123">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="6cb0e-124">このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないイベントがすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-124">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="6cb0e-125">**[すべてのイベントを表示する]** がオンで、トレース ファイルまたはトレース テーブルを表示している場合、トレースに記録されたすべてのイベントがトレース ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-125">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="6cb0e-126">**[すべての列を表示]**</span><span class="sxs-lookup"><span data-stu-id="6cb0e-126">**Show all columns**</span></span>  
 <span data-ttu-id="6cb0e-127">表示できるデータ列をすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-127">Show all available data columns.</span></span> <span data-ttu-id="6cb0e-128">既定では、選択されているデータ列だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-128">By default, only data columns that are selected display.</span></span> <span data-ttu-id="6cb0e-129">このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないデータ列がすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-129">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="6cb0e-130">**列フィルター**</span><span class="sxs-lookup"><span data-stu-id="6cb0e-130">**Column Filters**</span></span>  
 <span data-ttu-id="6cb0e-131">[ **フィルターの編集** ] ダイアログ ボックスを起動します。フィルター選択されるデータ列の列ラベルの左側には、フィルターのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-131">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label for filtered data columns.</span></span> <span data-ttu-id="6cb0e-132">**[フィルターの編集]** ダイアログ ボックスを使用して、データ列のフィルターを編集します。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-132">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="6cb0e-133">**[列の構成]**</span><span class="sxs-lookup"><span data-stu-id="6cb0e-133">**Organize Columns**</span></span>  
 <span data-ttu-id="6cb0e-134">**[イベント]** およびトレースするデータ列を選択した後、 **[列の構成]** をクリックすると、トレース結果のウィンドウの列が並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="6cb0e-134">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb0e-135">参照</span><span class="sxs-lookup"><span data-stu-id="6cb0e-135">See Also</span></span>  
 <span data-ttu-id="6cb0e-136">[トレースファイルのイベントとデータ列を指定する &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6cb0e-136">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="6cb0e-137">[トレース &#40;SQL Server プロファイラーのイベントをフィルター処理し&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6cb0e-137">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="6cb0e-138">[フィルター情報の表示 &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6cb0e-138">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="6cb0e-139">[フィルター &#40;SQL Server プロファイラーの変更&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6cb0e-139">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="6cb0e-140">[SQL Server プロファイラー](../tools/sql-server-profiler/sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6cb0e-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="6cb0e-141">SQL Server プロファイラーのテンプレートとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="6cb0e-141">SQL Server Profiler Templates and Permissions</span></span>](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
  
  
