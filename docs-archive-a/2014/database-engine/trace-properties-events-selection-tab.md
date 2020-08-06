---
title: '[トレースのプロパティ] ([イベントの選択] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11f4725865d39c21e36f5fd09eaf2afd4cde3017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718633"
---
# <a name="trace-properties-events-selection-tab"></a><span data-ttu-id="42121-102">[トレースのプロパティ] ([イベントの選択] タブ)</span><span class="sxs-lookup"><span data-stu-id="42121-102">Trace Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="42121-103">**[トレースのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用すると、トレースの対象となるイベントとデータ列を表示および指定できます。</span><span class="sxs-lookup"><span data-stu-id="42121-103">Use the **Events Selection** tab of the **Trace Properties** dialog box to view or specify traced events and data columns.</span></span>  
  
## <a name="options"></a><span data-ttu-id="42121-104">Options</span><span class="sxs-lookup"><span data-stu-id="42121-104">Options</span></span>  
 <span data-ttu-id="42121-105">**[イベント]** 列</span><span class="sxs-lookup"><span data-stu-id="42121-105">**Events** column</span></span>  
 <span data-ttu-id="42121-106">イベント列のチェック ボックスをオンまたはオフにして、トレースするイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="42121-106">Specify traced events by selecting or clearing the check box in the event column.</span></span> <span data-ttu-id="42121-107">**[イベント]** 列は、イベント カテゴリ別に分類されています。</span><span class="sxs-lookup"><span data-stu-id="42121-107">**Events** are organized by event category.</span></span> <span data-ttu-id="42121-108">テンプレートで指定されているイベント クラスが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="42121-108">Event classes specified in the template are automatically selected.</span></span> <span data-ttu-id="42121-109">詳しくは、「 [SQL Server イベント クラスの参照](../relational-databases/event-classes/sql-server-event-class-reference.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="42121-109">For more information, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="42121-110">データ列</span><span class="sxs-lookup"><span data-stu-id="42121-110">Data columns</span></span>  
 <span data-ttu-id="42121-111">必要なイベント列とデータ列に対応するチェック ボックスをオンにして、トレースするデータ列を指定します。</span><span class="sxs-lookup"><span data-stu-id="42121-111">Specify traced data columns by checking the box that corresponds with the event and the data column you need.</span></span> <span data-ttu-id="42121-112">トレースの対象になる各イベントに対応するイベント列は、既定ですべてオンになっています。</span><span class="sxs-lookup"><span data-stu-id="42121-112">All relevant event columns are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="42121-113">フィルターを指定するには、データ列のヘッダーをクリックし、フィルター基準を入力します。</span><span class="sxs-lookup"><span data-stu-id="42121-113">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="42121-114">フィルター選択されるデータ列については、 **[フィルターの編集]** ダイアログ ボックスの列ラベルの左側にフィルターのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="42121-114">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="42121-115">詳細については、「 [SQL Server Profiler - [フィルターの編集]](../../2014/database-engine/sql-server-profiler-edit-filter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42121-115">For more information, see [SQL Server Profiler - Edit Filter](../../2014/database-engine/sql-server-profiler-edit-filter.md).</span></span>  
  
 <span data-ttu-id="42121-116">**[すべてのイベントを表示する]**</span><span class="sxs-lookup"><span data-stu-id="42121-116">**Show all events**</span></span>  
 <span data-ttu-id="42121-117">表示できるイベントをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="42121-117">Show all available events.</span></span> <span data-ttu-id="42121-118">既定では、 **[イベントの選択]** グリッドで選択されている行だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="42121-118">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="42121-119">このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないイベントがすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="42121-119">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="42121-120">**[すべての列を表示]**</span><span class="sxs-lookup"><span data-stu-id="42121-120">**Show all columns**</span></span>  
 <span data-ttu-id="42121-121">表示できるデータ列をすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="42121-121">Show all available data columns.</span></span> <span data-ttu-id="42121-122">既定では、選択されているデータ列だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="42121-122">By default, only data columns that are selected display.</span></span> <span data-ttu-id="42121-123">このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないデータ列がすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="42121-123">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="42121-124">**列フィルター**</span><span class="sxs-lookup"><span data-stu-id="42121-124">**Column Filters**</span></span>  
 <span data-ttu-id="42121-125">**[フィルターの編集]** ダイアログ ボックスを起動します。</span><span class="sxs-lookup"><span data-stu-id="42121-125">Launches the **Edit Filter** dialog box.</span></span> <span data-ttu-id="42121-126">このダイアログ ボックスを使用して、データ列のフィルターを編集できます。</span><span class="sxs-lookup"><span data-stu-id="42121-126">You can use this dialog to edit data column filters.</span></span>  
  
 <span data-ttu-id="42121-127">**[列の構成]**</span><span class="sxs-lookup"><span data-stu-id="42121-127">**Organize Columns**</span></span>  
 <span data-ttu-id="42121-128">トレースとグループ化の結果で、1 つ以上の列を使用して列の順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="42121-128">Changes the order of columns in the trace and groups results by one or more columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42121-129">参照</span><span class="sxs-lookup"><span data-stu-id="42121-129">See Also</span></span>  
 <span data-ttu-id="42121-130">[トレースファイルのイベントとデータ列を指定する &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="42121-130">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="42121-131">[トレース &#40;SQL Server プロファイラーに表示される列の構成&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="42121-131">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="42121-132">[トレース &#40;SQL Server プロファイラーのイベントをフィルター処理し&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="42121-132">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="42121-133">[フィルター情報の表示 &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="42121-133">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="42121-134">[フィルター &#40;SQL Server プロファイラーの変更&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="42121-134">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="42121-135">[SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="42121-135">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="42121-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="42121-136">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
