---
title: Deadlock Graph の保存 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], saving deadlock graphs
- graphs [SQL Server]
- saving deadlock graphs
ms.assetid: bf1fc906-abd6-4a89-842e-da0d66b2defe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cdd0bd808ba4b934e5b2d91c9079909acf6e3997
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642737"
---
# <a name="save-deadlock-graphs-sql-server-profiler"></a><span data-ttu-id="1102b-102">Deadlock Graph の保存 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="1102b-102">Save Deadlock Graphs (SQL Server Profiler)</span></span>
  <span data-ttu-id="1102b-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して Deadlock Graph を保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1102b-103">This topic describes how to save a deadlock graph by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="1102b-104">Deadlock Graph は XML ファイルとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="1102b-104">Deadlock graphs are saved as XML files.</span></span>  
  
### <a name="to-save-deadlock-graph-events-separately"></a><span data-ttu-id="1102b-105">Deadlock Graph のイベントを個別に保存するには</span><span class="sxs-lookup"><span data-stu-id="1102b-105">To save deadlock graph events separately</span></span>  
  
1.  <span data-ttu-id="1102b-106">**[ファイル]** メニューの **[新しいトレース]** をクリックし、SQL Server のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1102b-106">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="1102b-107">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1102b-107">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1102b-108">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1102b-108">If **Start tracing immediately after making connection** is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="1102b-109">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="1102b-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="1102b-110">[トレースのプロパティ] ダイアログ ボックスの **[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="1102b-110">In the Trace Properties dialog box, type a name for the trace in the**Trace name** box.</span></span>  
  
3.  <span data-ttu-id="1102b-111">**[使用するテンプレート]** ボックスの一覧で、トレースの基本として使用するトレース テンプレートを選択します。テンプレートを使用しない場合は、 **[空白]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1102b-111">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="1102b-112">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="1102b-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="1102b-113">トレースをファイルにキャプチャするには、**[ファイルに保存]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1102b-113">Select the**Save to file** check box to capture the trace to a file.</span></span> <span data-ttu-id="1102b-114">**[最大ファイル サイズの設定]** ボックスに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="1102b-114">Specify a value for **Set maximum file size**.</span></span>  
  
         <span data-ttu-id="1102b-115">必要に応じて、 **[ファイル ロールオーバーを有効にする]** チェック ボックスと **[サーバーがトレース データを処理する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1102b-115">Optionally, select **Enable file rollover** and **Server processes trace data**.</span></span>  
  
    -   <span data-ttu-id="1102b-116">トレースをデータベース テーブルにキャプチャするには、 **[テーブルに保存する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1102b-116">Select the **Save to table** check box to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="1102b-117">必要に応じて、 **[最大行数の設定 (1000 行単位)]** チェック ボックスをオンにし、値を指定します。</span><span class="sxs-lookup"><span data-stu-id="1102b-117">Optionally, click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="1102b-118">必要に応じて、 **[トレース停止時刻を有効にする]** チェック ボックスをオンにして、停止日時を指定します。</span><span class="sxs-lookup"><span data-stu-id="1102b-118">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="1102b-119">**[イベントの選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1102b-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="1102b-120">**[Events]** データ列で、 **[Locks]** イベント カテゴリを展開し、 **[Deadlock graph]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1102b-120">In the **Events**data column, expand the **Locks**event category, and then select the **Deadlock graph**check box.</span></span> <span data-ttu-id="1102b-121">Locks イベント カテゴリが表示されない場合は、 **[すべてのイベントを表示する]** チェック ボックスをオンにして表示します。</span><span class="sxs-lookup"><span data-stu-id="1102b-121">If the Locks event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="1102b-122">**[トレースのプロパティ]** ダイアログ ボックスに **[イベント抽出の設定]** タブが追加されます。</span><span class="sxs-lookup"><span data-stu-id="1102b-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog box.</span></span>  
  
8.  <span data-ttu-id="1102b-123">**[イベント抽出の設定]** タブで、 **[デッドロック XML イベントを個別に保存する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1102b-123">On the **Events Extraction Settings**tab, click **Save Deadlock XML Events Separately**.</span></span>  
  
9. <span data-ttu-id="1102b-124">**[名前を付けて保存]** ダイアログ ボックスで、Deadlock Graph のイベントを格納するファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="1102b-124">In the **Save As** dialog box, enter the name of the file in which to store the deadlock graph events.</span></span>  
  
10. <span data-ttu-id="1102b-125">1 つの XML ファイルに Deadlock Graph のすべてのイベントを保存するには、 **[1 つのファイルにすべてのデッドロック XML バッチを保存する]** をクリックします。また、Deadlock Graph ごとに新しい XML ファイルを作成するには、 **[個別のファイルに各デッドロック XML バッチを保存する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1102b-125">Click **All Deadlock XML batches in a single file** to save all deadlock graph events in a single XML file, or click **Each Deadlock XML batch in a distinct file**to create a new XML file for each deadlock graph.</span></span>  
  
 <span data-ttu-id="1102b-126">デッドロック ファイルを保存した後は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="1102b-126">After you have saved the deadlock file, you can open the file in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1102b-127">詳細については、「[デッドロックファイルを開く、表示、および印刷する &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1102b-127">For more information, see [Open, View, and Print a Deadlock File &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1102b-128">参照</span><span class="sxs-lookup"><span data-stu-id="1102b-128">See Also</span></span>  
 [<span data-ttu-id="1102b-129">SQL Server Profiler を使用したデッドロックの分析</span><span class="sxs-lookup"><span data-stu-id="1102b-129">Analyze Deadlocks with SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)  
  
  
