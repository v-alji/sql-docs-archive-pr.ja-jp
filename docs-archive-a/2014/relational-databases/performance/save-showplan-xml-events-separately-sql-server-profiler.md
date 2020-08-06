---
title: Showplan XML イベントを個別に保存する方法 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 240fb408bb3ed8585ecc915ba4829ac21285d241
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645000"
---
# <a name="save-showplan-xml-events-separately-sql-server-profiler"></a><span data-ttu-id="6266a-102">Showplan XML イベントを個別に保存する方法 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="6266a-102">Save Showplan XML Events Separately (SQL Server Profiler)</span></span>
  <span data-ttu-id="6266a-103">このトピックでは、トレースにキャプチャされた **Showplan XML** イベントを [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]で個別の .SQLPlan ファイルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6266a-103">This topic describes how to save **Showplan XML** events that are captured in traces into separate .SQLPlan files by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="6266a-104">**で** Showplan XML [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]イベント ファイルを開くことができ、これによって各イベントのグラフィカル実行プランを表示できます。</span><span class="sxs-lookup"><span data-stu-id="6266a-104">You can open the **Showplan XML** event files in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], which enables you to view the graphical execution plan for each event.</span></span>  
  
### <a name="to-save-showplan-xml-events-separately"></a><span data-ttu-id="6266a-105">Showplan XML イベントを個別に保存するには</span><span class="sxs-lookup"><span data-stu-id="6266a-105">To save Showplan XML events separately</span></span>  
  
1.  <span data-ttu-id="6266a-106">**[ファイル]** メニューの **[新しいトレース]** をクリックし、SQL Server のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6266a-106">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="6266a-107">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6266a-107">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6266a-108">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="6266a-108">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="6266a-109">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="6266a-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="6266a-110">**[トレースのプロパティ]** ダイアログ ボックスの **[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6266a-110">In the **Trace Properties** dialog box, type a name for the trace in the **Trace name** box.</span></span>  
  
3.  <span data-ttu-id="6266a-111">**[使用するテンプレート]** ボックスの一覧で、トレースの基本として使用するトレース テンプレートを選択します。テンプレートを使用しない場合は、 **[空白]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6266a-111">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="6266a-112">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="6266a-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="6266a-113">トレースをファイルにキャプチャするには、**[ファイルに保存]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6266a-113">Select the**Save to file** check box to capture the trace to a file.</span></span> <span data-ttu-id="6266a-114">**[最大ファイル サイズの設定]** ボックスに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6266a-114">Specify a value for **Set maximum file size**.</span></span> <span data-ttu-id="6266a-115">必要に応じて、 **[ファイル ロールオーバーを有効にする]** および **[サーバーがトレース データを処理する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6266a-115">Optionally, select the **Enable file rollover** and **Server processes trace data** check boxes.</span></span>  
  
    -   <span data-ttu-id="6266a-116">トレースをデータベース テーブルにキャプチャするには、**[テーブルに保存する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6266a-116">Select the**Save to table** check box to capture the trace to a database table.</span></span> <span data-ttu-id="6266a-117">必要に応じて、[**最大行数の設定**] をクリックし、値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6266a-117">Optionally click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="6266a-118">必要に応じて、 **[トレース停止時刻を有効にする]** チェック ボックスをオンにして、停止日時を指定します。</span><span class="sxs-lookup"><span data-stu-id="6266a-118">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="6266a-119">**[イベントの選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6266a-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="6266a-120">**[Events]** データ列で **[Performance]** イベント カテゴリを展開し、 **[Showplan XML]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6266a-120">In the **Events**data column, expand the **Performance**event category, and then select the **Showplan XML**check box.</span></span> <span data-ttu-id="6266a-121">**Performance** イベント カテゴリが表示されない場合は、 **[すべてのイベントを表示する]** チェック ボックスをオンにしてください。</span><span class="sxs-lookup"><span data-stu-id="6266a-121">If the **Performance** event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="6266a-122">**[トレースのプロパティ]** ダイアログ ボックスに **[イベント抽出の設定]** タブが追加されます。</span><span class="sxs-lookup"><span data-stu-id="6266a-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog box.</span></span>  
  
8.  <span data-ttu-id="6266a-123">**[イベント抽出の設定]** タブで、 **[XML プラン表示イベントを個別に保存する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6266a-123">On the **Events Extraction Settings**tab, click **Save XML Showplan events separately**.</span></span>  
  
9. <span data-ttu-id="6266a-124">**[名前を付けて保存]** ダイアログ ボックスで、 **Showplan XML** イベントを保存するファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="6266a-124">In the **Save As** dialog box, enter the name of the file in which to store the **Showplan XML** events.</span></span>  
  
10. <span data-ttu-id="6266a-125">**[1 つのファイルにすべての XML プラン表示バッチを保存する]** をクリックして、すべての **Showplan XML** イベントを 1 つの XML ファイルに保存します。または、 **[個別のファイルに各 XML プラン表示バッチを保存する]** をクリックして、 **Showplan XML** イベントごとに新しい XML ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6266a-125">Click **All XML Showplan batches in a single file** to save all **Showplan XML** events in a single XML file, or click **Each XML Showplan batch in a distinct file**to create a new XML file for each **Showplan XML** event.</span></span>  
  
11. <span data-ttu-id="6266a-126">SQL Server Management Studio で **Showplan XML** イベント ファイルを表示するには、 **[ファイル]** メニューの **[開く]** をポイントして、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6266a-126">To view the **Showplan XML** event file in SQL Server Management Studio, on the **File** menu, point to **Open**, and click **File**.</span></span> <span data-ttu-id="6266a-127">**Showplan XML** イベント ファイルを保存したディレクトリに移動し、イベント ファイルを選択して開きます。</span><span class="sxs-lookup"><span data-stu-id="6266a-127">Navigate to the directory where you saved the **Showplan XML** event file or files to select one and open it.</span></span> <span data-ttu-id="6266a-128">**Showplan XML** イベント ファイルには .SQLPlan ファイル拡張子が付いています。</span><span class="sxs-lookup"><span data-stu-id="6266a-128">**Showplan XML** event files have a .SQLPlan file extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6266a-129">参照</span><span class="sxs-lookup"><span data-stu-id="6266a-129">See Also</span></span>  
 [<span data-ttu-id="6266a-130">SQL Server Profiler での Showplan 結果を使用したクエリの分析</span><span class="sxs-lookup"><span data-stu-id="6266a-130">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
