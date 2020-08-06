---
title: トレース内のイベントをフィルター処理する (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: fef9dd6956d407011261c54f796a751a0bf94941
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739030"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a><span data-ttu-id="39f10-102">トレース内のイベントへのフィルターの適用 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="39f10-102">Filter Events in a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="39f10-103">フィルターを使用すると、トレースに出力するイベントを制限することができます。</span><span class="sxs-lookup"><span data-stu-id="39f10-103">Filters limit the events collected in a trace.</span></span> <span data-ttu-id="39f10-104">フィルターが設定されていない場合は、選択したイベント クラスのすべてのイベントがトレースに出力されます。</span><span class="sxs-lookup"><span data-stu-id="39f10-104">If a filter is not set, all events of the selected event classes are returned in the trace output.</span></span> <span data-ttu-id="39f10-105">トレースのフィルター設定は必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="39f10-105">It is not mandatory to set a filter for a trace.</span></span> <span data-ttu-id="39f10-106">ただし、フィルターを設定すると、トレース中に発生するオーバーヘッドを低減できます。</span><span class="sxs-lookup"><span data-stu-id="39f10-106">However, a filter minimizes the overhead that is incurred during tracing.</span></span>  
  
 <span data-ttu-id="39f10-107">フィルターをトレース定義に追加するには、 **[トレースのプロパティ]** ダイアログ ボックスまたは **[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="39f10-107">You add filters to trace definitions by using the **Events Selection** tab of the **Trace Properties** or **Trace Template Properties** dialog box.</span></span>  
  
### <a name="to-filter-events-in-a-trace"></a><span data-ttu-id="39f10-108">トレース内のイベントにフィルターを適用するには</span><span class="sxs-lookup"><span data-stu-id="39f10-108">To filter events in a trace</span></span>  
  
1.  <span data-ttu-id="39f10-109">**[トレースのプロパティ]** ダイアログ ボックスまたは **[トレース テンプレートのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39f10-109">In the **Trace Properties** or **Trace Template Properties** dialog box, click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="39f10-110">**[イベントの選択]** タブにはグリッド コントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="39f10-110">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="39f10-111">グリッド コントロールは、トレース可能な各イベント クラスを含んでいるテーブルです。</span><span class="sxs-lookup"><span data-stu-id="39f10-111">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="39f10-112">このテーブルには、各イベント クラスが 1 行で表示されます。</span><span class="sxs-lookup"><span data-stu-id="39f10-112">The table contains one row for each event class.</span></span> <span data-ttu-id="39f10-113">イベント クラスは、接続先のサーバーの種類やバージョンによって多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="39f10-113">The event classes may differ slightly, depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="39f10-114">イベント クラスは、グリッドの **[イベント]** 列で識別され、イベント カテゴリ別に分類されています。</span><span class="sxs-lookup"><span data-stu-id="39f10-114">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="39f10-115">残りの列には、各イベント クラスに対応するデータ列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39f10-115">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
2.  <span data-ttu-id="39f10-116">**[列フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39f10-116">Click **Column Filters.**</span></span>  
  
     <span data-ttu-id="39f10-117">**[フィルターの編集]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39f10-117">The **Edit Filter**dialog box appears.</span></span> <span data-ttu-id="39f10-118">**[フィルターの編集]** ダイアログ ボックスには、トレース内のイベントにフィルターを適用するための比較演算子が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="39f10-118">The **Edit Filter**dialog box contains a list of comparison operators that you can use to filter events in a trace.</span></span>  
  
3.  <span data-ttu-id="39f10-119">フィルターを適用するには、比較演算子をクリックして、フィルターに対して使用する値を入力します。</span><span class="sxs-lookup"><span data-stu-id="39f10-119">To apply a filter, click the comparison operator, and type a value to use for the filter.</span></span>  
  
4.  <span data-ttu-id="39f10-120">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39f10-120">Click **OK**.</span></span>  
  
 <span data-ttu-id="39f10-121">**考慮事項:**</span><span class="sxs-lookup"><span data-stu-id="39f10-121">**Considerations:**</span></span>  
  
-   <span data-ttu-id="39f10-122">[イベントの選択] タブの **[StartTime]** データ列および **[EndTime]** データ列に対してフィルター条件を設定するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="39f10-122">If you set filter conditions on the **StartTime** and **EndTime** data columns of the Events Selection tab, then make sure that:</span></span>  
  
    -   <span data-ttu-id="39f10-123">日付は `YYYY/MM/DD HH:mm:sec`の形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="39f10-123">The date you enter matches this format: `YYYY/MM/DD HH:mm:sec`.</span></span>  
  
         <span data-ttu-id="39f10-124">\- または -</span><span class="sxs-lookup"><span data-stu-id="39f10-124">-OR-</span></span>  
  
    -   <span data-ttu-id="39f10-125">**[全般オプション]** ダイアログ ボックスで、 **[日時の値の表示に地域別設定を使用する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="39f10-125">**Use regional settings to display date and time values** is checked in the **General Options** dialog box.</span></span> <span data-ttu-id="39f10-126">**[全般オプション]** ダイアログ ボックスを表示するには、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で **[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39f10-126">To view the **General Options** dialog box, on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tools** menu, click **Option**.</span></span>  
  
         <span data-ttu-id="39f10-127">および</span><span class="sxs-lookup"><span data-stu-id="39f10-127">-AND-</span></span>  
  
    -   <span data-ttu-id="39f10-128">1753 年 1 月 1 日～ 9999 年 12 月 31 日の日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="39f10-128">The date you enter is between January 1, 1753 and December 31, 9999.</span></span>  
  
-   <span data-ttu-id="39f10-129">**osql** ユーティリティまたは **sqlcmd** ユーティリティからイベントをトレースしている場合は必ず、 **%** を **TextData** データ列のフィルターに付加します。</span><span class="sxs-lookup"><span data-stu-id="39f10-129">If tracing events from the **osql** utility or from the **sqlcmd** utility, always append **%** to filters on the **TextData** data column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f10-130">参照</span><span class="sxs-lookup"><span data-stu-id="39f10-130">See Also</span></span>  
 [<span data-ttu-id="39f10-131">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="39f10-131">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
