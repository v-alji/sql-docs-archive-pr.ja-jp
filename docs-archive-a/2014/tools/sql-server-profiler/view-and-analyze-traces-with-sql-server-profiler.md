---
title: SQL Server Profiler を使用したトレースの表示と分析 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], viewing traces
- SQL Server Profiler, viewing traces
- traces [SQL Server], viewing
- SQL Server Profiler, troubleshooting
- troubleshooting [SQL Server], traces
- events [SQL Server], finding inside trace
- Profiler [SQL Server Profiler], troubleshooting
- traces [SQL Server], events
ms.assetid: 17e821ca-a12e-4192-acc1-96765d9ae266
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3e848fe9a07d838631eef1737c2a7679b67e649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634183"
---
# <a name="view-and-analyze-traces-with-sql-server-profiler"></a><span data-ttu-id="563a4-102">SQL Server Profiler を使用したトレースの表示と分析</span><span class="sxs-lookup"><span data-stu-id="563a4-102">View and Analyze Traces with SQL Server Profiler</span></span>
  <span data-ttu-id="563a4-103">トレースにキャプチャされたイベント データを表示するには、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="563a4-103">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to view captured event data in a trace.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="563a4-104">では、定義されたトレース プロパティに基づいてデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="563a4-104">displays data based on defined trace properties.</span></span> <span data-ttu-id="563a4-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータを分析するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] や [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーなどの別のプログラムにデータをコピーする方法があります。</span><span class="sxs-lookup"><span data-stu-id="563a4-105">One way to analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data is to copy the data to another program, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor.</span></span> [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="563a4-106">チューニング アドバイザーは、 **Text** データ列がトレースに含まれている場合、SQL バッチおよびリモート プロシージャ コール (RPC) のイベントを含んだトレース ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="563a4-106">Tuning Advisor can use a trace file that contains SQL batch and remote procedure call (RPC) events if the **Text** data column is included in the trace.</span></span> <span data-ttu-id="563a4-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーで使用する適切なイベントと列がキャプチャされるようにするには、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]に付属の定義済みチューニング テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="563a4-107">To make sure that the correct events and columns are captured for use with [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, use the predefined Tuning template that is supplied with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="563a4-108">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用してトレースを開くとき、そのトレース ファイルが [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] または SQL トレース システムのストアド プロシージャによって作成されている場合は、トレース ファイルに .trc というファイル拡張子が付いている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="563a4-108">When you open a trace by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the trace file does not need to have the .trc file extension if the file was created by either [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or SQL Trace system stored procedures.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="563a4-109">は、SQL トレース .log ファイルと汎用 SQL スクリプト ファイルも読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="563a4-109">can also read SQL Trace .log files and generic SQL script files.</span></span> <span data-ttu-id="563a4-110">ファイル拡張子 .log がない SQL トレース ファイル、たとえば trace.txt を開く場合は、ファイル形式として **SQLTrace_Log** を指定します。</span><span class="sxs-lookup"><span data-stu-id="563a4-110">When opening a SQL Trace .log file that does not have a .log file extension, such as trace.txt, specify **SQLTrace_Log** as the file format.</span></span>  
  
 <span data-ttu-id="563a4-111">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] の日付および時刻の表示形式は、トレース分析を行いやすいように設定できます。</span><span class="sxs-lookup"><span data-stu-id="563a4-111">You can configure the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] date and time display format to assist in trace analysis.</span></span>  
  
## <a name="troubleshooting-data"></a><span data-ttu-id="563a4-112">データのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="563a4-112">Troubleshooting Data</span></span>  
 <span data-ttu-id="563a4-113">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用すると、トレースまたはトレース ファイルを **Duration**、 **CPU**、 **Reads**、または **Writes** の各データ列でグループ化することにより、データをトラブルシューティングできます。</span><span class="sxs-lookup"><span data-stu-id="563a4-113">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can troubleshoot data by grouping traces or trace files by the **Duration**, **CPU**, **Reads**, or **Writes** data columns.</span></span> <span data-ttu-id="563a4-114">トラブルシューティングできるデータの例としては、実行時間のかかるクエリや、論理読み取り操作の数が例外的に多いクエリなどがあります。</span><span class="sxs-lookup"><span data-stu-id="563a4-114">Examples of data you might troubleshoot are queries that perform poorly or that have exceptionally high numbers of logical read operations.</span></span>  
  
 <span data-ttu-id="563a4-115">さらに、トレースをテーブルに保存し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してイベント データをクエリすることにより、追加の情報を検索できます。</span><span class="sxs-lookup"><span data-stu-id="563a4-115">Additional information can be found by saving traces to tables and using [!INCLUDE[tsql](../../includes/tsql-md.md)] to query the event data.</span></span> <span data-ttu-id="563a4-116">たとえば、どの **SQL:BatchCompleted** イベントの待機時間が長すぎるかを調べるには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="563a4-116">For example, to determine which **SQL:BatchCompleted** events had excessive wait time, execute the following:</span></span>  
  
```  
SELECT  TextData, Duration, CPU  
FROM    trace_table_name  
WHERE   EventClass = 12 -- SQL:BatchCompleted events  
AND     CPU < (Duration * 1000)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="563a4-117">サーバーはマイクロ秒 (100 万分の 1 (10<sup>-6</sup>) 秒) 単位でのイベント期間、およびイベントにより使用されるミリ秒 (10<sup>-3</sup>秒) 単位での CPU 時間をレポートします。</span><span class="sxs-lookup"><span data-stu-id="563a4-117">The server reports the duration of an event in microseconds (one millionth, or 10<sup>-6</sup>, of a second) and the amount of CPU time used by the event in milliseconds (one thousandth, or 10<sup>-3</sup>, of a second).</span></span> <span data-ttu-id="563a4-118">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のグラフィカル ユーザー インターフェイスに、既定ではミリ秒単位で **Duration** 列が表示されますが、トレースがファイルまたはデータベース テーブルに保存されると、 **Duration** 列の値はマイクロ秒単位で記述されます。</span><span class="sxs-lookup"><span data-stu-id="563a4-118">The [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] graphical user interface displays the **Duration** column in milliseconds by default, but when a trace is saved to either a file or a database table, the **Duration** column value is written in microseconds.</span></span>  
  
## <a name="displaying-object-names-when-viewing-traces"></a><span data-ttu-id="563a4-119">トレースを確認するときのオブジェクト名の表示</span><span class="sxs-lookup"><span data-stu-id="563a4-119">Displaying Object Names When Viewing Traces</span></span>  
 <span data-ttu-id="563a4-120">オブジェクトの識別子 (**Object ID**) でなく名前を表示するには、 **Object Name** データ列に加えて **Server Name** と **Database ID** の各データ列もキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="563a4-120">If you wish to display the name of an object rather than the object identifier (**Object ID**), you must capture the **Server Name** and **Database ID** data columns along with the **Object Name** data column.</span></span>  
  
 <span data-ttu-id="563a4-121">**Object ID** データ列でグループ化する場合は、まず **Server Name** と **Database ID** の各データ列でグループ化してから、 **Object ID** データ列でグループ化してください。</span><span class="sxs-lookup"><span data-stu-id="563a4-121">If you choose to group by the **Object ID** data column, make sure you group by the **Server Name** and **Database ID** data columns first, and then by the **Object ID** data column.</span></span> <span data-ttu-id="563a4-122">同様に、 **Index ID** データ列でグループ化する場合は、まず **Server Name**、 **Database ID**、および **Object ID** の各データ列でグループ化してから、 **Index ID** データ列でグループ化してください。</span><span class="sxs-lookup"><span data-stu-id="563a4-122">Similarly, if you choose to group by the **Index ID** data column, make sure you group by the **Server Name**, **Database ID**, and **Object ID** data columns first, and then by the **Index ID** data columns.</span></span> <span data-ttu-id="563a4-123">サーバーとデータベース (およびインデックス ID の場合はオブジェクト) の間ではオブジェクト ID とインデックス ID は一意でないので、この順序でグループ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="563a4-123">You must group in this order because object and index IDs are not unique among servers and databases (and among objects for index IDs).</span></span>  
  
## <a name="finding-specific-events-within-a-trace"></a><span data-ttu-id="563a4-124">トレース内での特定のイベントの検索</span><span class="sxs-lookup"><span data-stu-id="563a4-124">Finding Specific Events Within a Trace</span></span>  
 <span data-ttu-id="563a4-125">トレース内のイベントを検索およびグループ化するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="563a4-125">To find and group events in a trace, follow these steps:</span></span>  
  
1.  <span data-ttu-id="563a4-126">トレースを作成します。</span><span class="sxs-lookup"><span data-stu-id="563a4-126">Create your trace.</span></span>  
  
    -   <span data-ttu-id="563a4-127">トレースを定義する場合、キャプチャするその他のデータ列に加え、 **Event Class**、 **ClientProcessID**、 **Start Time** の各データ列もキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="563a4-127">When defining the trace, capture the **Event Class**, **ClientProcessID**, and **Start Time** data columns in addition to any other data columns you want to capture.</span></span> <span data-ttu-id="563a4-128">詳細については、「[トレースの作成 &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="563a4-128">For more information, see [Create a Trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="563a4-129">**Event Class**データ列でキャプチャされたデータをグループ化し、トレースをファイルまたはテーブルにキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="563a4-129">Group the captured data by the **Event Class**data column, and capture the trace to a file or table.</span></span> <span data-ttu-id="563a4-130">キャプチャされたデータをグループ化するには、[トレースのプロパティ] ダイアログ ボックスの **[イベントの選択]** タブで **[列の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563a4-130">To group the captured data, click **Organize Columns** on the **Events Selection** tab of the Trace Properties dialog box.</span></span> <span data-ttu-id="563a4-131">詳細については、「[トレースに表示される列の構成 &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="563a4-131">For more information, see [Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="563a4-132">トレースを開始して、適切な時間が経過するか、適切な数のイベントがキャプチャされたら、トレースを停止します。</span><span class="sxs-lookup"><span data-stu-id="563a4-132">Start the trace and stop it after the appropriate time has passed or number of events have been captured.</span></span>  
  
2.  <span data-ttu-id="563a4-133">対象のイベントを検索します。</span><span class="sxs-lookup"><span data-stu-id="563a4-133">Find the target events.</span></span>  
  
    -   <span data-ttu-id="563a4-134">トレース ファイルまたはテーブルを開き、必要なイベント クラスのノード、たとえば **Deadlock Chain**を展開します。</span><span class="sxs-lookup"><span data-stu-id="563a4-134">Open the trace file or table, and expand the node of the desired event class; for example, **Deadlock Chain**.</span></span> <span data-ttu-id="563a4-135">詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="563a4-135">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="563a4-136">目的のイベントが見つかるまで、トレース データ全体を検索します。 **の** [編集] **メニューの** [検索] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用すると、トレース内の値を検索するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="563a4-136">Search through the trace data until you find the events for which you are looking (use the **Find** command on the **Edit** menu of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to help you find values in the trace).</span></span> <span data-ttu-id="563a4-137">トレースするイベントの **ClientProcessID** データ列に加えて **Start Time** データ列の値を書き留めておきます。</span><span class="sxs-lookup"><span data-stu-id="563a4-137">Note the values in the **ClientProcessID** and **Start Time** data columns of the events you trace.</span></span>  
  
3.  <span data-ttu-id="563a4-138">コンテキスト内でイベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="563a4-138">Display the events in context.</span></span>  
  
    -   <span data-ttu-id="563a4-139">トレースのプロパティを表示し、 **ClientProcessID**ClientProcessID **Event Class** の各データ列もキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="563a4-139">Display the trace properties, and group by the **ClientProcessID**data column rather than by the **Event Class** data column.</span></span>  
  
    -   <span data-ttu-id="563a4-140">表示する各クライアント プロセス ID のノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="563a4-140">Expand the nodes of each client process ID you want to view.</span></span> <span data-ttu-id="563a4-141">トレース全体を手動で検索するか、または前の対象イベントの **Start Time** 値が見つかるまで **[検索]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="563a4-141">Search through the trace manually, or use **Find** until you find the previously noted **Start Time**values of the target events.</span></span> <span data-ttu-id="563a4-142">選択した各クライアント プロセス ID に属するその他のイベントと共に、イベントは発生順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="563a4-142">The events are displayed in chronological order with the other events that belong to each selected client process ID.</span></span> <span data-ttu-id="563a4-143">たとえば、トレース内にキャプチャされた **Deadlock** データ列に加えて **Deadlock Chain**イベントは、展開されたクライアント プロセス ID 内の **SQL:BatchStarting**events within the expデータ列に加えてed client process ID.</span><span class="sxs-lookup"><span data-stu-id="563a4-143">For example, the **Deadlock** and **Deadlock Chain**events, captured within the trace, appear immediately after the **SQL:BatchStarting**events within the expanded client process ID.</span></span>  
  
 <span data-ttu-id="563a4-144">これと同じ方法で、グループ化されたイベントを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="563a4-144">The same technique can be used to find any grouped events.</span></span> <span data-ttu-id="563a4-145">目的のイベントが見つかったら、 **ClientProcessID**、 **ApplicationName**、その他のイベント クラスでイベントをグループ化すると、関連する動作を発生順に表示できます。</span><span class="sxs-lookup"><span data-stu-id="563a4-145">Once you have found the events you seek, group them by **ClientProcessID**, **ApplicationName**, or another event class to view related activity in chronological order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563a4-146">参照</span><span class="sxs-lookup"><span data-stu-id="563a4-146">See Also</span></span>  
 <span data-ttu-id="563a4-147">[保存されているトレースの表示 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="563a4-147">[View a Saved Trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md) </span></span>  
 <span data-ttu-id="563a4-148">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="563a4-148">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span></span>  
 <span data-ttu-id="563a4-149">[フィルター情報の表示 &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="563a4-149">[View Filter Information &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="563a4-150">[フィルター情報の表示 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="563a4-150">[View Filter Information &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md) </span></span>  
 <span data-ttu-id="563a4-151">[トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="563a4-151">[Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="563a4-152">トレース テーブルを開く &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="563a4-152">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](open-a-trace-table-sql-server-profiler.md)  
  
  
