---
title: '[トレーステンプレートのプロパティ] ([イベントの選択] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetemplateproperties.eventsselection.f1
helpviewer_keywords:
- Trace Template Properties dialog box
ms.assetid: 5b202457-ab42-4902-8012-7f3f40aa09f5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: da497db6e9373c63836753dc2be96deb3ce90244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740290"
---
# <a name="trace-template-properties-events-selection-tab"></a><span data-ttu-id="853dc-102">[トレース テンプレートのプロパティ] ([イベントの選択] タブ)</span><span class="sxs-lookup"><span data-stu-id="853dc-102">Trace Template Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="853dc-103">**[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用すると、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] トレース テンプレートに含めるイベント クラスとデータ列の表示、編集、指定ができます。</span><span class="sxs-lookup"><span data-stu-id="853dc-103">Use the **Events Selection** tab of the **Trace Template Properties** dialog box to view, edit, or specify event classes and data columns to include in a [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace template.</span></span>  
  
## <a name="options"></a><span data-ttu-id="853dc-104">Options</span><span class="sxs-lookup"><span data-stu-id="853dc-104">Options</span></span>  
 <span data-ttu-id="853dc-105">**[イベント]** 列</span><span class="sxs-lookup"><span data-stu-id="853dc-105">**Events** column</span></span>  
 <span data-ttu-id="853dc-106">イベント列のチェック ボックスをオンまたはオフにして、トレースするイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="853dc-106">Specify events that should be traced by selecting or clearing the check box in the event column.</span></span> <span data-ttu-id="853dc-107">イベントは、イベント カテゴリ別に分類されます。</span><span class="sxs-lookup"><span data-stu-id="853dc-107">Events are organized by event category.</span></span>  
  
 <span data-ttu-id="853dc-108">**[全般]** タブの **[既存のテンプレートを基に新しいテンプレートを作成する]** を選択した場合、指定したテンプレートに応じてイベントが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="853dc-108">If you selected **Base new template on existing one** on the **General** tab, events are automatically selected according to the specified template.</span></span> <span data-ttu-id="853dc-109">イベント クラスの詳細については、「 [SQL Server イベント クラスの参照](../relational-databases/event-classes/sql-server-event-class-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="853dc-109">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="853dc-110">データ列</span><span class="sxs-lookup"><span data-stu-id="853dc-110">Data columns</span></span>  
 <span data-ttu-id="853dc-111">トレースするデータ列を指定するには、必要なイベント列とデータ列に対応するチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="853dc-111">Specify data columns that should be traced by checking the box that corresponds with the event and the data column you need.</span></span> <span data-ttu-id="853dc-112">トレースに含まれる各イベントに対応するチェック ボックスがオンになっている場合、そのイベントのイベント列は既定ですべてオンになります。</span><span class="sxs-lookup"><span data-stu-id="853dc-112">All relevant event columns are checked by default for each event included in the trace, if the checkbox corresponding to the event is checked.</span></span> <span data-ttu-id="853dc-113">**[全般]** タブの **[既存のテンプレートを基に新しいテンプレートを作成する]** をオンにした場合、指定したテンプレートに応じてデータ列とフィルターが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="853dc-113">If you checked **Base new template on existing one** on the **General** tab, data columns and filters are automatically selected according to the specified template.</span></span>  
  
 <span data-ttu-id="853dc-114">フィルターを指定するには、データ列のヘッダーをクリックし、フィルター基準を入力します。</span><span class="sxs-lookup"><span data-stu-id="853dc-114">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="853dc-115">フィルター選択されるデータ列については、 **[フィルターの編集]** ダイアログ ボックスの列ラベルの左側にフィルターのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="853dc-115">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="853dc-116">**[すべてのイベントを表示する]**</span><span class="sxs-lookup"><span data-stu-id="853dc-116">**Show all events**</span></span>  
 <span data-ttu-id="853dc-117">表示できるイベントをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="853dc-117">Show all available events.</span></span> <span data-ttu-id="853dc-118">既存のテンプレートを基にしていない新しいテンプレートを作成する場合、このオプションは既定でオンになります。</span><span class="sxs-lookup"><span data-stu-id="853dc-118">This option is checked by default if you are creating a new template that is not based on an existing template.</span></span> <span data-ttu-id="853dc-119">オフにすると、 **[イベントの選択]** グリッドで選択されていないイベントがすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="853dc-119">Uncheck to hide all unselected events in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="853dc-120">**[すべての列を表示]**</span><span class="sxs-lookup"><span data-stu-id="853dc-120">**Show all columns**</span></span>  
 <span data-ttu-id="853dc-121">表示できるデータ列をすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="853dc-121">Show all available data columns.</span></span> <span data-ttu-id="853dc-122">既存のテンプレートを基にしていない新しいテンプレートを作成する場合、このオプションは既定でオンになります。</span><span class="sxs-lookup"><span data-stu-id="853dc-122">This option is checked by default if you are creating a new template that is not based on an existing template.</span></span> <span data-ttu-id="853dc-123">オフにすると、 **[イベントの選択]** グリッドで選択されていないデータ列がすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="853dc-123">Uncheck to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="853dc-124">**列フィルター**</span><span class="sxs-lookup"><span data-stu-id="853dc-124">**Column Filters**</span></span>  
 <span data-ttu-id="853dc-125">**[フィルターの編集]** ダイアログ ボックスを開きます。ここでは、データ列のラベルの左側にフィルターのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="853dc-125">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the data column label.</span></span> <span data-ttu-id="853dc-126">**[フィルターの編集]** ダイアログ ボックスを使用して、データ列のフィルターを編集します。</span><span class="sxs-lookup"><span data-stu-id="853dc-126">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="853dc-127">**[列の構成]**</span><span class="sxs-lookup"><span data-stu-id="853dc-127">**Organize Columns**</span></span>  
 <span data-ttu-id="853dc-128">トレースとグループ化の結果で、1 つ以上の列を使用して列の順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="853dc-128">Changes the order of columns in the trace and groups results by one or more columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853dc-129">参照</span><span class="sxs-lookup"><span data-stu-id="853dc-129">See Also</span></span>  
 <span data-ttu-id="853dc-130">[トレースファイルのイベントとデータ列を指定する &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="853dc-130">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="853dc-131">[トレース &#40;SQL Server プロファイラーに表示される列の構成&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="853dc-131">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="853dc-132">[トレース &#40;SQL Server プロファイラーのイベントをフィルター処理し&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="853dc-132">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="853dc-133">[フィルター情報の表示 &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="853dc-133">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="853dc-134">[フィルター &#40;SQL Server プロファイラーの変更&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="853dc-134">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="853dc-135">[SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="853dc-135">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="853dc-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="853dc-136">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
