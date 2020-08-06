---
title: SQL Server プロファイラー-列の構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.organize.columns.f1
ms.assetid: bf5674f4-da5e-43f9-aeb2-76ca37993790
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b63c2f7d882bac05fc6baf10614170ec23125c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736720"
---
# <a name="sql-server-profiler---organize-columns"></a><span data-ttu-id="846ba-102">[SQL Server Profiler] - [列の構成]</span><span class="sxs-lookup"><span data-stu-id="846ba-102">SQL Server Profiler - Organize Columns</span></span>
  <span data-ttu-id="846ba-103">大きなトレース ファイルまたはトレース テーブルの表示や分析を簡単に行えるように、トレースに表示されるイベントをグループ化または集計する場合は、 **[列の構成]** ダイアログ ボックスを使用してデータ列を選択します。</span><span class="sxs-lookup"><span data-stu-id="846ba-103">Use the **Organize Columns** dialog box to select data columns for grouping or aggregating events that are displayed in a trace, which makes large trace files or tables easier to view and analyze.</span></span>  
  
 <span data-ttu-id="846ba-104">集計を実行すると、トレース内のすべてのイベントはそれぞれのイベント クラスの種類の下に移動され、折りたたまれます。</span><span class="sxs-lookup"><span data-stu-id="846ba-104">Aggregating moves and collapses all events in the trace under its respective event class type.</span></span> <span data-ttu-id="846ba-105">**+** イベントクラス名の左側にプラス記号 () が表示されます。</span><span class="sxs-lookup"><span data-stu-id="846ba-105">A plus sign (**+**) appears to the left of the event class name.</span></span> <span data-ttu-id="846ba-106">プラス記号をクリックしてイベント クラスを展開すると、その種類のイベントがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="846ba-106">Clicking the plus sign expands the event class so you can view all events of that type.</span></span>  
  
 <span data-ttu-id="846ba-107">グループ化を実行すると、特定の種類のすべてのイベント クラスがトレース ウィンドウ表示にまとめて構成されます。</span><span class="sxs-lookup"><span data-stu-id="846ba-107">Grouping organizes all event classes of a specific type together in the trace window display.</span></span> <span data-ttu-id="846ba-108">ただし、イベントはイベント クラスの種類の下に折りたたまれません。</span><span class="sxs-lookup"><span data-stu-id="846ba-108">However, the events are not collapsed under the event class type.</span></span>  
  
 <span data-ttu-id="846ba-109">トレース ウィンドウ表示内でイベントのグループ化または集計を行うときに、選択されている列は表示ウィンドウ内で固定された状態のままですが、左右にスクロールして他のデータ列をすべて見ることができます。</span><span class="sxs-lookup"><span data-stu-id="846ba-109">When you group or aggregate events in a trace window display, the columns selected for grouping or aggregating remain fixed in the display window, but you can scroll to the right or left to view all other data columns.</span></span>  
  
 <span data-ttu-id="846ba-110">このダイアログ ボックスを表示するには、既存のトレース ファイルまたはトレース テーブルを開き、 **の** [ファイル] [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="846ba-110">To access this dialog box, open an existing trace file or table, and click **Properties** on the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **File** menu.</span></span> <span data-ttu-id="846ba-111">**[トレースのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックし、次に **[列の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="846ba-111">In the **Trace Properties** dialog box, click the **Events Selection** tab, and then click **Organize Columns**.</span></span> <span data-ttu-id="846ba-112">新しいトレースを作成する場合も、 **[イベントの選択]** タブの **[列の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="846ba-112">You can also click **Organize Columns** on the **Events Selection** tab when you are creating a new trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="846ba-113">Options</span><span class="sxs-lookup"><span data-stu-id="846ba-113">Options</span></span>  
 <span data-ttu-id="846ba-114">**グループ**</span><span class="sxs-lookup"><span data-stu-id="846ba-114">**Groups**</span></span>  
 <span data-ttu-id="846ba-115">**[グループ]** でデータ列名を移動することにより、トレース ウィンドウでイベント クラスのグループ化または集計を実行できます。</span><span class="sxs-lookup"><span data-stu-id="846ba-115">Move data column names under **Groups** to group or aggregate event classes in the trace window.</span></span>  
  
 <span data-ttu-id="846ba-116">イベントを集計するには、1 つのデータ列を **[グループ]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="846ba-116">To aggregate events, move one data column into **Groups**.</span></span> <span data-ttu-id="846ba-117">これにより、特定の種類のすべてのイベントが、トレース ウィンドウ表示のイベント クラスの種類名の下に折りたたまれます。</span><span class="sxs-lookup"><span data-stu-id="846ba-117">This causes all events of a specific type to be collapsed under event class type name in the trace window display.</span></span> <span data-ttu-id="846ba-118">**+** イベントクラス名の左側にプラス記号 () が表示されます。</span><span class="sxs-lookup"><span data-stu-id="846ba-118">A plus sign (**+**) appears to the left of the event class name.</span></span> <span data-ttu-id="846ba-119">このプラス記号をクリックすると、イベント クラスの種類が展開され、すべてのイベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="846ba-119">Click the plus sign to expand the event class type and view all events.</span></span> <span data-ttu-id="846ba-120">集計とグループ化のオンとオフを設定するには、 **[表示]** メニューの **[集計ビュー]** または **[グループ化ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="846ba-120">You can set aggregation and grouping on and off by clicking **Aggregated View** or **Grouped View** on the **View** menu.</span></span>  
  
 <span data-ttu-id="846ba-121">イベントをグループ化するには、複数のデータ列を **[グループ]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="846ba-121">To group events, move more than one data column into **Groups**.</span></span> <span data-ttu-id="846ba-122">これにより、トレース ウィンドウ表示で特定の種類のすべてのイベントがグループ化されますが、イベントは各イベント クラスの種類名の下には折りたたまれません。</span><span class="sxs-lookup"><span data-stu-id="846ba-122">This causes all events of a specific type to be grouped together in the trace window display, but does not collapse the events under each event class type name.</span></span> <span data-ttu-id="846ba-123">グループ化ビューとグループ化されていないビューを切り替えるには、[表示] メニューの **[グループ化ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="846ba-123">You can switch back and forth between a grouped view and an ungrouped view by clicking **Grouped View** on the View menu.</span></span> <span data-ttu-id="846ba-124">複数のデータ列を **[グループ]** に移動した場合、 **[集計ビュー]** に切り替えることはできません。</span><span class="sxs-lookup"><span data-stu-id="846ba-124">When more than one data column is moved into **Groups**, the option to switch to **Aggregated View** is not available.</span></span>  
  
 <span data-ttu-id="846ba-125">**[列]**</span><span class="sxs-lookup"><span data-stu-id="846ba-125">**Columns**</span></span>  
 <span data-ttu-id="846ba-126">**[グループ]** への移動に使用できるデータ列の一覧です。</span><span class="sxs-lookup"><span data-stu-id="846ba-126">List of data columns available to move into **Groups**.</span></span> <span data-ttu-id="846ba-127">[列] の左にあるプラス記号 () をクリックして **+** 、一覧を展開します**Columns** 。</span><span class="sxs-lookup"><span data-stu-id="846ba-127">Click the plus sign (**+**) to the left of **Columns** to expand the list.</span></span>  
  
 <span data-ttu-id="846ba-128">**設定**</span><span class="sxs-lookup"><span data-stu-id="846ba-128">**Up**</span></span>  
 <span data-ttu-id="846ba-129">データ列を選択した後で、 **[上へ]** をクリックすると、データ列を上に移動して **[グループ]** に入れることができます。</span><span class="sxs-lookup"><span data-stu-id="846ba-129">After selecting a data column, click **Up** to move data columns up into **Groups**.</span></span> <span data-ttu-id="846ba-130">また、 **[上へ]** をクリックして、トレース ウィンドウ表示内の列の表示を再構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="846ba-130">You can also click **Up** to rearrange the display of columns in the trace window display.</span></span>  
  
 <span data-ttu-id="846ba-131">**[下へ]**</span><span class="sxs-lookup"><span data-stu-id="846ba-131">**Down**</span></span>  
 <span data-ttu-id="846ba-132">データ列を選択した後で、 **[下へ]** をクリックすると、データ列を下に移動して **[グループ]** から除外することができます。</span><span class="sxs-lookup"><span data-stu-id="846ba-132">After selecting a data column, click **Down** to move data columns out of **Groups**.</span></span> <span data-ttu-id="846ba-133">また、 **[下へ]** をクリックして、トレース ウィンドウ表示内の列の表示を再構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="846ba-133">You can also click **Down** to rearrange the display of columns in the trace window display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846ba-134">参照</span><span class="sxs-lookup"><span data-stu-id="846ba-134">See Also</span></span>  
 <span data-ttu-id="846ba-135">[トレース &#40;SQL Server プロファイラーに表示される列の構成&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="846ba-135">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="846ba-136">[トレース &#40;SQL Server プロファイラーの作成&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="846ba-136">[Create a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="846ba-137">[トレース テンプレートの作成 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="846ba-137">[Create a Trace Template &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="846ba-138">[トレースファイル &#40;SQL Server プロファイラーを開き&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="846ba-138">[Open a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="846ba-139">トレース テーブルを開く &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="846ba-139">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
  
