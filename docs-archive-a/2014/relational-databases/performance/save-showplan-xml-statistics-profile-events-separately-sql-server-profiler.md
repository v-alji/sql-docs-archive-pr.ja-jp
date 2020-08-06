---
title: Showplan XML Statistics Profile イベントを個別に保存 (SQL Server Profiler) | Microsoft Docs
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
ms.assetid: df393f13-d538-4d94-8155-9c2fdf5f755d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be0c02f8396df81af803c365b9ede42610353ed3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716286"
---
# <a name="save-showplan-xml-statistics-profile-events-separately-sql-server-profiler"></a><span data-ttu-id="eaa08-102">Showplan XML Statistics Profile イベントを個別に保存 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="eaa08-102">Save Showplan XML Statistics Profile Events Separately (SQL Server Profiler)</span></span>
  <span data-ttu-id="eaa08-103">このトピックでは、トレースでキャプチャされる **Showplan XML Statistics Profile** イベントを、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して個別の SQLPlan ファイルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-103">This topic describes how to save **Showplan XML Statistics Profile** events that are captured in traces into separate .SQLPlan files by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="eaa08-104">**Showplan XML Statistics Profile** イベント ファイルは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で開くことができ、イベントごとの実行プランをグラフィカルに表示できます。</span><span class="sxs-lookup"><span data-stu-id="eaa08-104">You can open the **Showplan XML Statistics Profile** event files in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], which enables you to view the graphical execution plan for each event.</span></span>  
  
### <a name="to-save-showplan-xml-statistics-events-separately"></a><span data-ttu-id="eaa08-105">Showplan XML Statistics Profile イベントを個別に保存するには</span><span class="sxs-lookup"><span data-stu-id="eaa08-105">To save Showplan XML statistics events separately</span></span>  
  
1.  <span data-ttu-id="eaa08-106">**[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-106">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="eaa08-107">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eaa08-107">The **Trace Properties** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eaa08-108">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="eaa08-108">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box does not appear and the trace begins instead.</span></span> <span data-ttu-id="eaa08-109">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="eaa08-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="eaa08-110">**[トレースのプロパティ]** ダイアログ ボックスの **[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-110">In the **Trace Properties** dialog box, type a name for the trace in the **Trace name** box.</span></span>  
  
3.  <span data-ttu-id="eaa08-111">**[使用するテンプレート]** ボックスの一覧で、トレースのベースとなるトレース テンプレートを選択します。テンプレートを使用しない場合は、 **[空白]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-111">In the **Use the template** list, select a trace template to base the trace on, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="eaa08-112">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="eaa08-113">トレースをファイルに記録する場合は、**[ファイルに保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eaa08-113">Click**Save to file**to capture the trace to a file.</span></span> <span data-ttu-id="eaa08-114">**[最大ファイル サイズの設定]** ボックスに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-114">Specify a value for **Set maximum file size**.</span></span>  
  
         <span data-ttu-id="eaa08-115">必要に応じて、[**ファイルロールオーバーを有効にする**] と [**サーバープロセストレースデータ**] を選択します</span><span class="sxs-lookup"><span data-stu-id="eaa08-115">Optionally select **Enable file rollover** and **Server processes trace data**.</span></span>  
  
    -   <span data-ttu-id="eaa08-116">トレースをデータベース テーブルに記録する場合は、**[テーブルに保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eaa08-116">Click**Save to table** to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="eaa08-117">必要に応じて、[**最大行数の設定**] をクリックし、値を指定します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-117">Optionally click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="eaa08-118">必要に応じて、[**トレース停止時刻を有効にする**] チェックボックスをオンにして、停止日時を指定します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-118">Optionally select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="eaa08-119">**[イベントの選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eaa08-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="eaa08-120">**Events**データ列で、 **Performance**イベント カテゴリを展開し、 **[Showplan XML Statistics Profile]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eaa08-120">In the **Events**data column, expand the **Performance**event category, and then select the **Showplan XML Statistics Profile**check box.</span></span> <span data-ttu-id="eaa08-121">**Performance** イベント カテゴリが表示されない場合は、 **[すべてのイベントを表示する]** チェック ボックスをオンにしてください。</span><span class="sxs-lookup"><span data-stu-id="eaa08-121">If the **Performance** event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="eaa08-122">**[トレースのプロパティ]** ダイアログ ボックスに **[イベント抽出の設定]** タブが追加されます。</span><span class="sxs-lookup"><span data-stu-id="eaa08-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog.</span></span>  
  
8.  <span data-ttu-id="eaa08-123">**[イベント抽出の設定]** タブで、 **[XML プラン表示イベントを個別に保存する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eaa08-123">On the **Events Extraction Settings**tab, click **Save XML Showplan events separately**.</span></span>  
  
9. <span data-ttu-id="eaa08-124">**[名前を付けて保存]** ダイアログ ボックスで、 **Showplan XML Statistics Profile** イベントを格納するファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-124">In the **Save As** dialog box, enter the file name to store the **Showplan XML Statistics Profile** events.</span></span>  
  
10. <span data-ttu-id="eaa08-125">**[1 つのファイルにすべての XML プラン表示バッチを保存する]** をクリックし、1 つの XML ファイルにすべての **Showplan XML Statistics Profile** イベントを保存します。または、 **[個別のファイルに各 XML プラン表示バッチを保存する]** をクリックし、 **Showplan XML Statistics Profile** イベントごとに新しい XML ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="eaa08-125">Click **All batches in a single file** to save all **Showplan XML Statistics Profile** events in a single XML file, or click **Each XML Showplan batch in a distinct file**to create a new XML file for each **Showplan XML Statistics Profile** event.</span></span>  
  
11. <span data-ttu-id="eaa08-126">SQL Server Management Studio で **Showplan XML Statistics Profile** イベント ファイルを表示するには、 **[ファイル]** メニューで **[開く]** をポイントし、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eaa08-126">To view the **Showplan XML Statistics Profile** event file in SQL Server Management Studio, on the **File** menu, point to **Open**, and click **File**.</span></span> <span data-ttu-id="eaa08-127">**Showplan XML Statistics Profile** イベント ファイルを保存したディレクトリに移動し、ファイルを選択して開きます。</span><span class="sxs-lookup"><span data-stu-id="eaa08-127">Navigate to the directory where you saved the **Showplan XML Statistics Profile** event file or files to select one and open it.</span></span> <span data-ttu-id="eaa08-128">**Showplan XML Statistics Profile** イベント ファイルの拡張子は .SQLPlan です。</span><span class="sxs-lookup"><span data-stu-id="eaa08-128">**Showplan XML Statistics Profile** event files have a .SQLPlan file extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa08-129">参照</span><span class="sxs-lookup"><span data-stu-id="eaa08-129">See Also</span></span>  
 [<span data-ttu-id="eaa08-130">SQL Server Profiler での Showplan 結果を使用したクエリの分析</span><span class="sxs-lookup"><span data-stu-id="eaa08-130">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
