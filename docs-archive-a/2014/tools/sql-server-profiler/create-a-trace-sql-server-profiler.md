---
title: トレースの作成 (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], creating
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d73333bbf0ba985ed4952e03584b4e4c130ab6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711277"
---
# <a name="create-a-trace-sql-server-profiler"></a><span data-ttu-id="23467-102">トレースの作成 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="23467-102">Create a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="23467-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してトレースを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="23467-103">This topic describes how to use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create a trace.</span></span>  
  
### <a name="to-create-a-trace"></a><span data-ttu-id="23467-104">トレースを作成するには</span><span class="sxs-lookup"><span data-stu-id="23467-104">To create a trace</span></span>  
  
1.  <span data-ttu-id="23467-105">**[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="23467-105">On the **File** menu, click **New Trace**, and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="23467-106">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="23467-106">The **Trace Properties** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23467-107">**[接続の確立直後にトレースを開始する]** を選択している場合は、**[トレースのプロパティ]** ダイアログ ボックスは表示されずに、トレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="23467-107">The **Trace Properties** dialog box fails to appear, and the trace begins instead, if **Start tracing immediately after making connection** is selected.</span></span> <span data-ttu-id="23467-108">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="23467-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="23467-109">**[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="23467-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="23467-110">**[使用するテンプレート]** ボックスの一覧で、トレースの基本として使用するトレース テンプレートを選択します。テンプレートを使用しない場合は、 **[空白]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="23467-110">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="23467-111">トレース結果を保存するには、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="23467-111">To save the trace results, do one of the following:</span></span>  
  
    -   <span data-ttu-id="23467-112">**[ファイルに保存する]** をクリックし、トレースをファイルにキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="23467-112">Click **Save to file**to capture the trace to a file.</span></span> <span data-ttu-id="23467-113">**[最大ファイル サイズの設定]** ボックスに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="23467-113">Specify a value for **Set maximum file size**.</span></span> <span data-ttu-id="23467-114">既定値は 5 MB です。</span><span class="sxs-lookup"><span data-stu-id="23467-114">The default value is 5 megabytes (MB).</span></span>  
  
         <span data-ttu-id="23467-115">ファイル サイズが最大に達したとき新しいファイルを自動的に作成する場合は、 **[ファイル ロールオーバーを有効にする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="23467-115">Optionally, select **Enable file rollover** to automatically create new files when the maximum file size is reached.</span></span> <span data-ttu-id="23467-116">または、 **[サーバーがトレース データを処理する]** を選択することもできます。これを選択すると、トレースを実行しているサービスが、クライアント アプリケーションに代わってトレース データを処理します。</span><span class="sxs-lookup"><span data-stu-id="23467-116">You can also optionally select **Server processes trace data**, which causes the service that is running the trace to process trace data instead of the client application.</span></span> <span data-ttu-id="23467-117">サーバーがトレース データを処理する場合、ストレス条件下でもイベントはスキップされません。ただし、サーバー パフォーマンスは低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="23467-117">When the server processes trace data, no events are skipped even under stress conditions, but server performance may be affected.</span></span>  
  
    -   <span data-ttu-id="23467-118">トレースをデータベース テーブルに記録する場合は、 **[テーブルに保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23467-118">Click **Save to table** to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="23467-119">必要に応じて、 **[最大行数の設定 (1000 行単位)]** チェック ボックスをオンにし、値を指定します。</span><span class="sxs-lookup"><span data-stu-id="23467-119">Optionally, click **Set maximum rows**, and specify a value.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="23467-120">トレース結果をファイルにもテーブルにも保存しない場合は、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を開いているときにトレースを表示できます。</span><span class="sxs-lookup"><span data-stu-id="23467-120">When you do not save the trace results to a file or table, you can view the trace while [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is open.</span></span> <span data-ttu-id="23467-121">ただし、トレースを停止して [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を終了した場合、トレース結果は失われます。</span><span class="sxs-lookup"><span data-stu-id="23467-121">However, you lose the trace results after you stop the trace and close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="23467-122">このようにトレース結果が失われないようにするには、 **[ファイル]** メニューの **[保存]** をクリックして、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を終了する前にトレース結果を保存します。</span><span class="sxs-lookup"><span data-stu-id="23467-122">To avoid losing the trace results in this way, click **Save** on the **File** menu to save the results before you close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
5.  <span data-ttu-id="23467-123">必要に応じて、 **[トレース停止時刻を有効にする]** チェック ボックスをオンにして、停止日時を指定します。</span><span class="sxs-lookup"><span data-stu-id="23467-123">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="23467-124">イベント、データ列、フィルターを追加または削除するには、**[イベントの選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="23467-124">To add or remove events, data columns or filters, click the **Events Selection**tab.</span></span> <span data-ttu-id="23467-125">詳細については、「[トレース ファイルに含めるイベントとデータ列の指定 &#40;SQL Server Profiler&#41;](sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23467-125">For more information, see: [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](sql-server-profiler.md)</span></span>  
  
7.  <span data-ttu-id="23467-126">**[実行]** をクリックしてトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="23467-126">Click **Run** to start the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23467-127">参照</span><span class="sxs-lookup"><span data-stu-id="23467-127">See Also</span></span>  
 <span data-ttu-id="23467-128">[SQL Server Profiler の実行に必要な権限](permissions-required-to-run-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="23467-128">[Permissions Required to Run SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="23467-129">[SQL Server プロファイラーのテンプレートと権限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="23467-129">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 <span data-ttu-id="23467-130">[[SQL Server Profiler]](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="23467-130">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="23467-131">トレースと Windows パフォーマンス ログ データの関連付け &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="23467-131">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
