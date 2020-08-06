---
title: イベントセッションデータの表示 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac742a01-2a95-42c7-b65e-ad565020dc49
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eaeb5fd22b95b8f1056b8dce9e3c7d683b52602f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741205"
---
# <a name="view-event-session-data"></a><span data-ttu-id="6b308-102">イベント セッション データの表示</span><span class="sxs-lookup"><span data-stu-id="6b308-102">View Event Session Data</span></span>
  <span data-ttu-id="6b308-103">このトピックでは、表示のユーザー インターフェイスを使用して、拡張イベント データを表示および分析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b308-103">This topic describes using the display user interface to see and analyze extended event data:</span></span>  
  
-   <span data-ttu-id="6b308-104">[ターゲット データの表示]</span><span class="sxs-lookup"><span data-stu-id="6b308-104">View Target Data</span></span>  
  
-   <span data-ttu-id="6b308-105">データの処理</span><span class="sxs-lookup"><span data-stu-id="6b308-105">Working With Data</span></span>  
  
## <a name="view-target-data"></a><span data-ttu-id="6b308-106">[ターゲット データの表示]</span><span class="sxs-lookup"><span data-stu-id="6b308-106">View Target Data</span></span>  
 <span data-ttu-id="6b308-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]内で指定したターゲットに収集されたデータを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-107">You can display the data collected into the specified target within [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="view-target-data"></a><span data-ttu-id="6b308-108">[ターゲット データの表示]</span><span class="sxs-lookup"><span data-stu-id="6b308-108">View Target Data</span></span>  
 <span data-ttu-id="6b308-109">ターゲット データを表示するには:</span><span class="sxs-lookup"><span data-stu-id="6b308-109">To view target data:</span></span>  
  
1.  <span data-ttu-id="6b308-110">オブジェクト エクスプローラーで、 **[管理]**、 **[拡張イベント]**、 **[セッション]** の順に展開し、セッションを展開します。</span><span class="sxs-lookup"><span data-stu-id="6b308-110">In Object Explorer, expand **Management**, **Extended Events**, **Sessions**, and then a session.</span></span>  
  
2.  <span data-ttu-id="6b308-111">ターゲット名を右クリックし、 **[ターゲット データの表示]** をクリックしてターゲット データを表示します。</span><span class="sxs-lookup"><span data-stu-id="6b308-111">Right-click the target name, and then click **View Target Data** to display the target data.</span></span>  
  
     <span data-ttu-id="6b308-112">既定のビューにターゲット データ ウィンドウが表示され、ターゲット データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-112">The target data window appears in default view and displays the target data.</span></span>  
  
 <span data-ttu-id="6b308-113">ターゲット データを表示する際の注意事項:</span><span class="sxs-lookup"><span data-stu-id="6b308-113">Notes on viewing target data:</span></span>  
  
-   <span data-ttu-id="6b308-114">ETW ターゲットに対しては、ターゲット データを利用できません。</span><span class="sxs-lookup"><span data-stu-id="6b308-114">Target data is not available for the ETW target.</span></span>  
  
-   <span data-ttu-id="6b308-115">ring_buffer データを XML 形式で表示するには、ターゲット データ ウィンドウで **[ring_buffer ターゲット データ]** リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-115">To view the ring_buffer data in xml format, in the target data window click the **ring_buffer target data** link.</span></span> <span data-ttu-id="6b308-116">XML エディターに ring_buffer.xml ファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-116">The ring_buffer.xml file appears in the xml editor.</span></span>  
  
-   <span data-ttu-id="6b308-117">event_file ターゲットの場合、ファイル ターゲット データ (.XEL ファイル) を表示するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-117">For an event_file target, view the file target data (.XEL file) using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6b308-118">ファイル > を使用してで開き [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6b308-118">Use File -> Open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>
    
    -   <span data-ttu-id="6b308-119">ファイルをにドラッグアンドドロップし [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6b308-119">Drag and drop the file into [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> 
    
    -   <span data-ttu-id="6b308-120">.XEL ファイルをダブルクリックする。</span><span class="sxs-lookup"><span data-stu-id="6b308-120">Double click the .XEL file.</span></span>  
    
    -   <span data-ttu-id="6b308-121">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、実行中の拡張イベント セッションを右クリックし、[ターゲット データの表示] をクリックする。</span><span class="sxs-lookup"><span data-stu-id="6b308-121">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right click on a running Extended Events session and select View Target Data.</span></span> 
    
    -   <span data-ttu-id="6b308-122">[fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6b308-122">[fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>
    
    -   <span data-ttu-id="6b308-123">[SQLServer. XEvent モジュール](https://www.powershellgallery.com/packages/SqlServer.XEvent)で Powershell Read sqlxevent を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-123">Use Powershell Read-SQLXevent in [SQLServer.XEvent module](https://www.powershellgallery.com/packages/SqlServer.XEvent).</span></span>
    
    -   <span data-ttu-id="6b308-124">[Xelite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite)を使用してプログラムで xevent を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-124">Programmatically consume XEvents by using the [XELite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite).</span></span>
    
    -   <span data-ttu-id="6b308-125">複数のを表示できます。XEL ファイルを開くには、[ファイル] メニューの [**拡張イベントファイルのマージ**] を選択し > します。</span><span class="sxs-lookup"><span data-stu-id="6b308-125">You can view more than one .XEL file by selecting **Merge Extended Event Files** from the File -> Open menu.</span></span>

### <a name="watching-live-data"></a><span data-ttu-id="6b308-126">ライブ データの監視</span><span class="sxs-lookup"><span data-stu-id="6b308-126">Watching Live Data</span></span>  
 <span data-ttu-id="6b308-127">キャプチャされているライブ データを監視することができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-127">You can watch live data as it is being captured.</span></span>  
  
-   <span data-ttu-id="6b308-128">オブジェクトエクスプローラーで、[**管理**]、[**拡張イベント**]、[**セッション**] ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6b308-128">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  

-   <span data-ttu-id="6b308-129">セッション名を右クリックし、 **[ライブ データの監視]** をクリックしてトレース データを表示します。</span><span class="sxs-lookup"><span data-stu-id="6b308-129">Right-click the session name and then click **Watch Live Data** to start displaying the tracing data.</span></span>  
  
     <span data-ttu-id="6b308-130">既定の表示列は、 **Event Name** と **TimeStamp**です。</span><span class="sxs-lookup"><span data-stu-id="6b308-130">The default display columns are **Event Name** and **TimeStamp**.</span></span>  
  
     <span data-ttu-id="6b308-131">トレース ウィンドウに列を追加するには、[拡張イベント] ツール バーで **[列の選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-131">To add additional columns to the trace window, click the **Choose Columns** button on the Extended Events toolbar.</span></span> <span data-ttu-id="6b308-132">**[詳細]** タブに選択したイベントのすべてのイベント情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-132">The **Details** tab shows all of the event details for the selected event.</span></span>  
  
     <span data-ttu-id="6b308-133">イベントは通常、約 30 秒間表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-133">Events are usually displayed in approximately 30 seconds.</span></span> <span data-ttu-id="6b308-134">待機時間を変更するには、 **[新しいセッション]** ダイアログの **[詳細設定]** ページで **[ディスパッチの最大待機時間]** を変更します。</span><span class="sxs-lookup"><span data-stu-id="6b308-134">If you want to change the latency period, you can change the **Maximum dispatch latency** on the **Advanced** page of the of the **New Session** dialog.</span></span>  
     
-    <span data-ttu-id="6b308-135">ライブデータは、 [SqlServer. XEvent PowerShell モジュール](https://www.powershellgallery.com/packages/SqlServer.XEvent)でストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="6b308-135">Live data can be streamed by the [SqlServer.XEvent PowerShell module](https://www.powershellgallery.com/packages/SqlServer.XEvent).</span></span>
     
### <a name="to-refresh-target-data"></a><span data-ttu-id="6b308-136">ターゲット データを更新するには</span><span class="sxs-lookup"><span data-stu-id="6b308-136">To Refresh Target Data</span></span>  
 <span data-ttu-id="6b308-137">event_files ターゲットでは、ターゲット データの更新はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6b308-137">Refreshing target data is not supported for event_files targets:</span></span>  
  
1.  <span data-ttu-id="6b308-138">ターゲット データが自動的に更新されるようにするには、ターゲット データを右クリックして **[更新間隔]** をクリックし、更新間隔の一覧から更新間隔を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b308-138">To refresh the target data automatically, right click the target data, select **Refresh Interval**, and then select the refresh interval from the interval list.</span></span>  
  
2.  <span data-ttu-id="6b308-139">自動更新を一時停止または再開するには、ターゲット データを右クリックし、 **[一時停止]** または **[再開]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-139">To pause and resume the automatic refresh, right-click the target data and then select **Pause** or **Resume**.</span></span>  
  
3.  <span data-ttu-id="6b308-140">ターゲット データを手動で更新するには、ターゲット データを右クリックし、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-140">To refresh the target data manually, right click the target data, and then select **Refresh**.</span></span>  
  
## <a name="working-with-data"></a><span data-ttu-id="6b308-141">データの処理</span><span class="sxs-lookup"><span data-stu-id="6b308-141">Working With Data</span></span>  
 <span data-ttu-id="6b308-142">拡張イベント ユーザー インターフェイスの分析機能を使用すると、問題を特定することができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-142">You can use the analysis capabilities of the Extended Events user interface to identify problems.</span></span>  
  
### <a name="details-pane"></a><span data-ttu-id="6b308-143">[詳細] ペイン</span><span class="sxs-lookup"><span data-stu-id="6b308-143">Details Pane</span></span>  
 <span data-ttu-id="6b308-144">**[詳細]** ペインには、フィールドとアクションを含め、選択したイベントのすべての列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-144">The **Details** pane shows all the columns for the selected event, including fields and actions.</span></span> <span data-ttu-id="6b308-145">ターゲット データ テーブルに列を追加するには、 **[詳細]** ペインで行を右クリックし、 **[テーブルの列を表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-145">You can add a column to the target data table by right-clicking a row in the **Details** pane and selecting **Show Column in Table**.</span></span>  
  
### <a name="create-modify-or-delete-merged-columns"></a><span data-ttu-id="6b308-146">結合列の作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="6b308-146">Create, Modify, or Delete Merged Columns</span></span>  
 <span data-ttu-id="6b308-147">結合列を使用すると、一連のフィールドを結合して、1 つの列に表示することができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-147">A merged column allows you to combine a set of fields to be displayed in a single column.</span></span> <span data-ttu-id="6b308-148">結合列には、NULL 以外の最初のフィールドのデータが、フィールド リストに追加されたときの順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-148">The merged column will show the data from the first non-NULL field based on the order they are added to the field list.</span></span> <span data-ttu-id="6b308-149">これは、イベントに応じて異なるデータが特定の列に表示される [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler の表示に似ています (これの最も一般的な例は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler の TextData フィールドです)。</span><span class="sxs-lookup"><span data-stu-id="6b308-149">This is similar to what you see in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler, where a specific column may show different data depending on the event (the most common example of this is the TextData field in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler).</span></span> <span data-ttu-id="6b308-150">たとえば、sql_statement_completed イベントのステートメントと sql_batch_completed イベントの batch_text フィールドを myStatement という名前のフィールドに結合できます。</span><span class="sxs-lookup"><span data-stu-id="6b308-150">For an example, you could merge the statement and batch_text fields from the sql_statement_completed and sql_batch_completed events, respectively, into a field named myStatement.</span></span> <span data-ttu-id="6b308-151">テーブルに myStatement 列を表示すると、関連付けられているイベントの適切なデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-151">When you display the myStatement column in the table it will show the appropriate data for the associated event.</span></span>  
  
 <span data-ttu-id="6b308-152">結合列を作成、変更、または削除するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6b308-152">You can create, modify, or delete merged columns:</span></span>  
  
1.  <span data-ttu-id="6b308-153">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="6b308-153">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6b308-154">(セッション名を右クリックし、[**ライブデータの監視**] をクリックすることもできます)。</span><span class="sxs-lookup"><span data-stu-id="6b308-154">(You can also right click the session name, and then select **Watch Live Data**.)</span></span>  
  
2.  <span data-ttu-id="6b308-155">トレース結果ウィンドウで、列見出しを右クリックして、 **[列の選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-155">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
 <span data-ttu-id="6b308-156">結合列を作成するには、 **[列の選択]** ダイアログ ボックスで、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-156">To create a merged column, click **New** in the **Choose Columns** dialog box.</span></span>  <span data-ttu-id="6b308-157">**[新しい結合列]** ダイアログで、結合列の名前を付け、結合列に含める元の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b308-157">In the **New Merged Column** dialog, name the merged column and select the original columns to be included in the merged column.</span></span>  
  
 <span data-ttu-id="6b308-158">結合列を編集するには、 **[列の選択]** ダイアログで、結合列を選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-158">To edit a merged column, select a merged column in the **Choose Columns** dialog and click **Edit**.</span></span> <span data-ttu-id="6b308-159">**[結合列の編集]** ダイアログで、結合列の名前や結合列に含める元の列を変更します。</span><span class="sxs-lookup"><span data-stu-id="6b308-159">In the **Edit Merged Column** dialog, rename the merged column or modify the original columns to be included in the merged column.</span></span>  
  
 <span data-ttu-id="6b308-160">結合列を削除するには、 **[列の選択]** ダイアログで、結合列を選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-160">To delete a merged column, select a merged column in the **Choose Columns** dialog and click **Delete**.</span></span>  
  
### <a name="filter-results"></a><span data-ttu-id="6b308-161">結果へのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="6b308-161">Filter Results</span></span>  
 <span data-ttu-id="6b308-162">トレース結果を表示します。フィルターを適用することで、トレース ウィンドウに表示されるトレース結果を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-162">You can view trace results, and then apply filters to narrow down the trace results that are displayed in the trace window.</span></span> <span data-ttu-id="6b308-163">表示フィルターには、時間フィルターと高度なフィルターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b308-163">The display filter includes a time filter and an advanced filter.</span></span> <span data-ttu-id="6b308-164">時間フィルターではトレース結果をイベントのタイムスタンプでフィルター処理し、高度なフィルターではイベントのフィールドとアクションを使用してフィルター条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="6b308-164">You use the time filter to filter the trace results by event timestamp, and you use the advanced filter to construct filter conditions using the event fields and actions.</span></span> <span data-ttu-id="6b308-165">時間フィルターと高度なフィルターとの間には "and" 関係があります。</span><span class="sxs-lookup"><span data-stu-id="6b308-165">There is an "and" relationship between the time and advanced filters.</span></span>  
  
 <span data-ttu-id="6b308-166">フィルターを作成する手順は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6b308-166">To create a filter:</span></span>  
  
1.  <span data-ttu-id="6b308-167">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="6b308-167">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6b308-168">(セッション名を右クリックし、[**ライブデータの監視**] をクリックすることもできます)。</span><span class="sxs-lookup"><span data-stu-id="6b308-168">(You can also right click the session name, and then select **Watch Live Data**.)</span></span>  
  
2.  <span data-ttu-id="6b308-169">トレース結果ウィンドウでフィルターを選択し、 **[拡張イベント]** ツール バーの **[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-169">In the trace results window, select the results you want to filter, and then on the **Extended Events** toolbar, click **Filters**.</span></span>  
  
3.  <span data-ttu-id="6b308-170">**[フィルター]** ダイアログ ボックスで **[時間フィルターの設定]** をクリックし、スライダー バーをドラッグするか、編集ボックスの時間を変更することにより時間フィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="6b308-170">In the **Filters** dialog box, select **Set time filter** to set the time filter by dragging the slider bars or modifying the time in the edit box.</span></span>  
  
4.  <span data-ttu-id="6b308-171">[**追加のフィルター** ] セクションで、フィルター条件を適用し、[**適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-171">In the **Additional filters** section, apply your filter criteria, and then click **Apply**.</span></span>  
  
### <a name="sort-results"></a><span data-ttu-id="6b308-172">結果の並べ替え</span><span class="sxs-lookup"><span data-stu-id="6b308-172">Sort Results</span></span>  
 <span data-ttu-id="6b308-173">結果を昇順または降順に並べ替えるには:</span><span class="sxs-lookup"><span data-stu-id="6b308-173">To sort results either in ascending or descending order:</span></span>  
  
1.  <span data-ttu-id="6b308-174">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="6b308-174">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6b308-175">(セッション名を右クリックし、[**ライブデータの監視**] を選択して、ツールバーの [**データフィードの停止**] ボタンをクリックすることもできます)。</span><span class="sxs-lookup"><span data-stu-id="6b308-175">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
2.  <span data-ttu-id="6b308-176">トレース結果ウィンドウで、並べ替える列の見出しを右クリックし、 **[昇順で並べ替え]** または **[降順で並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-176">In the trace results window, right-click the column heading you want to sort and click **Sort Ascending** or **Sort Descending**.</span></span>  
  
 <span data-ttu-id="6b308-177">また、列見出しをクリックして並べ替え順を切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="6b308-177">You can also click the column header to reverse the sort order.</span></span>  
  
 <span data-ttu-id="6b308-178">列がグループ化されている場合、データはグループ内のみで並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="6b308-178">If you have grouped columns, sorting the column will only sort data within the group.</span></span>  
  
### <a name="group-results"></a><span data-ttu-id="6b308-179">結果のグループ化</span><span class="sxs-lookup"><span data-stu-id="6b308-179">Group Results</span></span>  
 <span data-ttu-id="6b308-180">結果のグループ化は、[!INCLUDE[tsql](../includes/tsql-md.md)] の `GROUP BY` 句と同等の機能です。</span><span class="sxs-lookup"><span data-stu-id="6b308-180">Grouped results are equivalent to the functionality of the `GROUP BY` clause in [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span> <span data-ttu-id="6b308-181">ターゲット データ テーブルにはグループ化されたデータが表示され、データの展開と折りたたみを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-181">The target data table will show the data grouped together, allowing you to expand and collapse the data.</span></span>  
  
 <span data-ttu-id="6b308-182">データは、集計する前にグループ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b308-182">You must group data before you can aggregate it.</span></span> <span data-ttu-id="6b308-183">たとえば、query_hash 値でグループ化し、実行時間を基準に降順に並べ替え、各グループの平均実行時間を取得した後、集計を基準に降順に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-183">For example, you can group on the query_hash value, sort descending by duration, get the average duration for each group, and then sort descending on the aggregation.</span></span>  <span data-ttu-id="6b308-184">これにより生成された一覧には、平均実行時間が長い方から順に並べ替えられた一意のステートメントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-184">This will produce a list that shows the list of unique statements from longest to shortest average duration.</span></span> <span data-ttu-id="6b308-185">一番上のグループを展開すると、そのクエリの個々の実行時間が長い方から順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-185">When you expand the top group you will see the individual executions of that specific query sorted from longest to shortest.</span></span>  
  
 <span data-ttu-id="6b308-186">1 つの列または複数の列で結果をグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="6b308-186">You can group results by a single column or by multiple columns.</span></span>  
  
 <span data-ttu-id="6b308-187">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="6b308-187">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6b308-188">(セッション名を右クリックし、[**ライブデータの監視**] を選択して、ツールバーの [**データフィードの停止**] ボタンをクリックすることもできます)。</span><span class="sxs-lookup"><span data-stu-id="6b308-188">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
 <span data-ttu-id="6b308-189">1 つの列で結果をグループ化するには、トレース結果ウィンドウで、列見出しを右クリックし、 **[この列でグループ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-189">To group results by a single column, right-click the column heading in the trace results window, and click **Group by this Column**.</span></span> <span data-ttu-id="6b308-190">グループ化を解除するには、行の 1 つを選択し、 **[すべてのグループを削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-190">To undo the grouping, select one of the rows and click **Remove All Groupings**.</span></span>  
  
 <span data-ttu-id="6b308-191">複数の列で結果をグループ化するには、 **[拡張イベント]** ツール バーの **[グループ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-191">To group results by a multiple columns, click the **Grouping** button on the **Extended Events** toolbar.</span></span> <span data-ttu-id="6b308-192">**[グループ化]** ダイアログの **[使用可能な列]** ボックスでグループ化する列を選択し、選択した列を **[次の条件でグループ化される列]** ボックスに移動します。</span><span class="sxs-lookup"><span data-stu-id="6b308-192">In the **Available columns** box of the **Grouping** dialog, select the columns you want to group, and move them into the **Columns grouped on** box.</span></span> <span data-ttu-id="6b308-193">順序を変更するには、 **[次の条件でグループ化される列]** ボックスで上矢印または下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-193">To change the order in the **Columns grouped on** box, click the up or down arrows.</span></span>  
  
### <a name="aggregate-results"></a><span data-ttu-id="6b308-194">結果の集計</span><span class="sxs-lookup"><span data-stu-id="6b308-194">Aggregate Results</span></span>  
 <span data-ttu-id="6b308-195">トレース結果を表示できます。また、結果の列を集計することにより、イベント データをさらに詳細に分析できます。</span><span class="sxs-lookup"><span data-stu-id="6b308-195">You can view the trace results, and then further analyze your event data by aggregating columns in your results.</span></span> <span data-ttu-id="6b308-196">拡張イベントは次の 5 つの集計関数をサポートします。</span><span class="sxs-lookup"><span data-stu-id="6b308-196">Extended Events supports five aggregation functions:</span></span>  
  
-   <span data-ttu-id="6b308-197">Sum</span><span class="sxs-lookup"><span data-stu-id="6b308-197">sum</span></span>  
  
-   <span data-ttu-id="6b308-198">min</span><span class="sxs-lookup"><span data-stu-id="6b308-198">min</span></span>  
  
-   <span data-ttu-id="6b308-199">max</span><span class="sxs-lookup"><span data-stu-id="6b308-199">max</span></span>  
  
-   <span data-ttu-id="6b308-200">average</span><span class="sxs-lookup"><span data-stu-id="6b308-200">average</span></span>  
  
-   <span data-ttu-id="6b308-201">count</span><span class="sxs-lookup"><span data-stu-id="6b308-201">count</span></span>  
  
 <span data-ttu-id="6b308-202">sum、min、max、および average は、数値列のみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b308-202">Sum, min, max, and average can only be used with numeric columns.</span></span> <span data-ttu-id="6b308-203">count は、グループ内の選択した列に存在する NULL 以外の値の数を表します。</span><span class="sxs-lookup"><span data-stu-id="6b308-203">Count is the number of non-null values that exist for the selected column in the group.</span></span>  
  
 <span data-ttu-id="6b308-204">集計はグループに対して実行されるため、集計を実行する前に結果をグループ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b308-204">Aggregation is performed on a group, so you must group the results before you can perform the aggregation.</span></span> <span data-ttu-id="6b308-205">結果を集計するには:</span><span class="sxs-lookup"><span data-stu-id="6b308-205">To aggregate results:</span></span>  
  
1.  <span data-ttu-id="6b308-206">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="6b308-206">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6b308-207">(セッション名を右クリックし、[**ライブデータの監視**] を選択して、ツールバーの [**データフィードの停止**] ボタンをクリックすることもできます)。</span><span class="sxs-lookup"><span data-stu-id="6b308-207">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
2.  <span data-ttu-id="6b308-208">**[拡張イベント]** ツール バーの **[集計]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-208">On the **Extended Events** toolbar, click the **Aggregation** button.</span></span> <span data-ttu-id="6b308-209">集計に使用できる列が [集計] ダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-209">The Aggregation dialog box will display the columns available for aggregation.</span></span>  
  
3.  <span data-ttu-id="6b308-210">**[集計の種類]** 列で、集計の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b308-210">In the **Aggregation Type** column, select the aggregation type.</span></span>  
  
4.  <span data-ttu-id="6b308-211">**[集計の並べ替え]** ボックスで、並べ替え列を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b308-211">In the **Sort aggregation by** box, select the sort column.</span></span> <span data-ttu-id="6b308-212">次に、昇順または降順を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b308-212">Then select ascending or descending order.</span></span>  
  
### <a name="search-for-text-in-columns"></a><span data-ttu-id="6b308-213">列のテキストの検索</span><span class="sxs-lookup"><span data-stu-id="6b308-213">Search for Text in Columns</span></span>  
 <span data-ttu-id="6b308-214">列のテキストを検索するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6b308-214">You can search for text in columns:</span></span>  
  
1.  <span data-ttu-id="6b308-215">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="6b308-215">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6b308-216">(セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません)。</span><span class="sxs-lookup"><span data-stu-id="6b308-216">(You can also right click the session name, select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="6b308-217">**[拡張イベント]** ツール バーの **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-217">Click **Find** on the **Extended Events** toolbar.</span></span>  
  
3.  <span data-ttu-id="6b308-218">**[拡張イベントで検索]** ダイアログ ボックスの **[検索する文字列]** ボックスに、検索テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="6b308-218">In the **Find what** box of the **Find in Extended Events** dialog box, enter the search text.</span></span> <span data-ttu-id="6b308-219">ドロップダウン リストから直前の 20 回の検索文字列の 1 つを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-219">You can select one of your last 20 search strings from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="6b308-220">**[検索対象]** ボックスで、指定したテキストを検索する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b308-220">In the **Look in** box, select the location to search for the specified text.</span></span> <span data-ttu-id="6b308-221">次の検索オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b308-221">Use the following options for searching:</span></span>  
  
    -   <span data-ttu-id="6b308-222">[テーブル列]。</span><span class="sxs-lookup"><span data-stu-id="6b308-222">Table Columns.</span></span> <span data-ttu-id="6b308-223">トレース ウィンドウに表示されているすべての列を検索するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-223">Use this option to search all visible columns in the trace window.</span></span>  
  
    -   <span data-ttu-id="6b308-224">[詳細]。</span><span class="sxs-lookup"><span data-stu-id="6b308-224">Details.</span></span> <span data-ttu-id="6b308-225">このオプションを使用すると、[**拡張イベントで検索**] ダイアログボックスを開く前に選択したトレースウィンドウで、昇格および昇格されていないすべての列を検索できます。</span><span class="sxs-lookup"><span data-stu-id="6b308-225">Use this option to search all columns (promoted and non-promoted) in the trace window that were selected before opening the **Find in Extended Events** dialog box.</span></span>  
  
    -   <span data-ttu-id="6b308-226">*Event_column_name*。</span><span class="sxs-lookup"><span data-stu-id="6b308-226">*Event_column_name*.</span></span> <span data-ttu-id="6b308-227">ドロップダウン リストから特定のイベント列で検索するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-227">Use this option to search in a specific event column from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="6b308-228">検索の定義方法を指定するには、次のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-228">Use the following options to specify how you want to define the search:</span></span>  
  
    -   <span data-ttu-id="6b308-229">[大文字と小文字を区別する]。</span><span class="sxs-lookup"><span data-stu-id="6b308-229">Match case.</span></span> <span data-ttu-id="6b308-230">[検索する文字列] で入力したテキストに大文字と小文字の違いを含めて完全に一致する検索結果を表示するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-230">Use this option to display the search results for the text you entered in the Find what box that are matched both by content and by case.</span></span>  
  
    -   <span data-ttu-id="6b308-231">[単語単位]。</span><span class="sxs-lookup"><span data-stu-id="6b308-231">Match whole word.</span></span> <span data-ttu-id="6b308-232">入力したテキストに単語単位で一致する検索結果のみを表示するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-232">Use this option to display only the search results for the text you entered that match complete words.</span></span>  
  
    -   <span data-ttu-id="6b308-233">[上へ検索]。</span><span class="sxs-lookup"><span data-stu-id="6b308-233">Search up.</span></span> <span data-ttu-id="6b308-234">カーソル位置から先頭までを検索するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-234">Use this option to search from your cursor location to the beginning of the results.</span></span>  
  
    -   <span data-ttu-id="6b308-235">[使用]。</span><span class="sxs-lookup"><span data-stu-id="6b308-235">Use.</span></span> <span data-ttu-id="6b308-236">[検索する文字列] ボックスに入力された特殊文字および正規表現を解釈するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-236">Use this option to interpret the special characters and the regular expressions you entered in the Find what box.</span></span> <span data-ttu-id="6b308-237">特殊文字には 1 文字以上を表すワイルドカード文字 (\*) および (?) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6b308-237">Special characters include the wildcard characters (\*) and (?) to represent one or more characters.</span></span> <span data-ttu-id="6b308-238">正規表現は、検索テキストのパターンを定義する特殊な表記です。</span><span class="sxs-lookup"><span data-stu-id="6b308-238">Regular expressions are special notations used to define patterns of search text.</span></span>  
  
    -   <span data-ttu-id="6b308-239">**[次を検索]** をクリックすると、 **[検索する文字列]** で入力したテキストの次の箇所が検索されます。</span><span class="sxs-lookup"><span data-stu-id="6b308-239">Click **Find Next** to search for the next text that you entered in the **Find what** box.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="6b308-240">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="6b308-240">Bookmarks</span></span>  
 <span data-ttu-id="6b308-241">行に簡単に戻ることができるようにするには、ターゲット データの 1 つまたは複数の行にブックマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="6b308-241">To make it easier to return to a row, you can bookmark one or more row(s) in the target data.</span></span> <span data-ttu-id="6b308-242">ブックマークを変更するには、行を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-242">Right click on a row to change the bookmark.</span></span> <span data-ttu-id="6b308-243">ブックマークが付いている行に移動するには、 **[拡張イベント]** ツール バーの [戻る] および [次へ] を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b308-243">Use the previous and next buttons on the **Extended Events** toolbar to navigate to bookmarked rows.</span></span>  
  
### <a name="change-display-settings"></a><span data-ttu-id="6b308-244">表示設定の変更</span><span class="sxs-lookup"><span data-stu-id="6b308-244">Change Display Settings</span></span>  
 <span data-ttu-id="6b308-245">トレース結果の列情報 (列の順番、結合列、および列幅) とフィルター情報は、拡張イベント表示設定ファイル (.viewsetting ファイル) に保存することができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-245">You can save column information (column order, merge column, and column width) and filter information of a trace result into an Extended Events display setting file (.viewsetting file).</span></span> <span data-ttu-id="6b308-246">ファイルを保存した後、トレース結果に適用することによって、ビューを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-246">After saving the file, you can apply it to your trace results to change the view.</span></span>  
  
 <span data-ttu-id="6b308-247">表示設定を変更するには:</span><span class="sxs-lookup"><span data-stu-id="6b308-247">To change the display settings:</span></span>  
  
1.  <span data-ttu-id="6b308-248">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="6b308-248">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6b308-249">(セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません)。</span><span class="sxs-lookup"><span data-stu-id="6b308-249">(You can also right click the session name, select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="6b308-250">**[拡張イベント]** ツール バーで、 **[表示設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-250">On the **Extended Events** toolbar, select **Display Settings**.</span></span> <span data-ttu-id="6b308-251">ドロップダウン リストから次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6b308-251">From the drop-down list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="6b308-252">[名前を付けて保存]。</span><span class="sxs-lookup"><span data-stu-id="6b308-252">Save as.</span></span> <span data-ttu-id="6b308-253">トレース結果の列情報とフィルター情報を .viewsetting ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="6b308-253">Save the columns and filter information of a trace result to a .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="6b308-254">開く。</span><span class="sxs-lookup"><span data-stu-id="6b308-254">Open.</span></span> <span data-ttu-id="6b308-255">既存の .viewsetting ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6b308-255">Open an existing .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="6b308-256">[最近使用した項目を開く]。</span><span class="sxs-lookup"><span data-stu-id="6b308-256">Open recent.</span></span> <span data-ttu-id="6b308-257">最近保存した .viewsetting ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6b308-257">Open a recently saved .viewsetting file.</span></span>  
  
### <a name="copy-or-export-trace-results"></a><span data-ttu-id="6b308-258">トレース結果のコピーまたはエクスポート</span><span class="sxs-lookup"><span data-stu-id="6b308-258">Copy or Export Trace Results</span></span>  
 <span data-ttu-id="6b308-259">トレース結果から選択した行にセル、行、および詳細をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="6b308-259">You can copy cells, rows, and details to selected rows from your trace results.</span></span> <span data-ttu-id="6b308-260">トレース結果を次のものにエクスポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6b308-260">You can also export your trace results to the following:</span></span>  
  
-   <span data-ttu-id="6b308-261">.XEL ファイル</span><span class="sxs-lookup"><span data-stu-id="6b308-261">.XEL file</span></span>  
  
-   <span data-ttu-id="6b308-262">table</span><span class="sxs-lookup"><span data-stu-id="6b308-262">table</span></span>  
  
-   <span data-ttu-id="6b308-263">.CSV ファイル</span><span class="sxs-lookup"><span data-stu-id="6b308-263">.CSV file</span></span>  
  
 <span data-ttu-id="6b308-264">トレース結果をコピーするには、セルまたは行 (行は複数可) を選択し、右クリックして、 **[コピー]** をクリックし、 **[セル]**、 **[行]**、または **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-264">To copy trace results, select a cell, row, or rows, right click, select **Copy** and then **Cell**, **Row**, or **Details**.</span></span> <span data-ttu-id="6b308-265">拡張イベントは、最大 1000 行のコピーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6b308-265">Extended Events supports copying up to a maximum of 1000 rows.</span></span>  
  
 <span data-ttu-id="6b308-266">トレース結果を .XEL ファイル、テーブル、または .CSV ファイルにエクスポートするには、 **で** [拡張イベント] **メニュー オプションの** [エクスポート先] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-266">You can export trace results to a .XEL file, table, or .CSV file by selecting **Export to** from the **Extended Events** menu option in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="view-a-deadlock-graph-and-query-plans"></a><span data-ttu-id="6b308-267">Deadlock Graph とクエリ プランの表示</span><span class="sxs-lookup"><span data-stu-id="6b308-267">View a Deadlock Graph and Query Plans</span></span>  
 <span data-ttu-id="6b308-268">[詳細] ペインで **xml_deadlock_report** のデッドロック グラフを表示して、デッドロックのトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6b308-268">You can view the deadlock graph for **xml_deadlock_report** in the Details pane to help you troubleshoot deadlocks.</span></span> <span data-ttu-id="6b308-269">次のイベントのクエリ プラン グラフを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="6b308-269">You can also view query plan graphs for the following events:</span></span>  
  
-   <span data-ttu-id="6b308-270">query_post_compilation_showplan</span><span class="sxs-lookup"><span data-stu-id="6b308-270">query_post_compilation_showplan</span></span>  
  
-   <span data-ttu-id="6b308-271">query_pre_execution_showplan</span><span class="sxs-lookup"><span data-stu-id="6b308-271">query_pre_execution_showplan</span></span>  
  
-   <span data-ttu-id="6b308-272">query_post_execution_showplan</span><span class="sxs-lookup"><span data-stu-id="6b308-272">query_post_execution_showplan</span></span>  
  
 <span data-ttu-id="6b308-273">デッドロック グラフを表示するには:</span><span class="sxs-lookup"><span data-stu-id="6b308-273">To view the deadlock graph:</span></span>  
  
-   <span data-ttu-id="6b308-274">オブジェクトエクスプローラーで、[**管理**]、[**拡張イベント**]、[**セッション**] ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6b308-274">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
-   <span data-ttu-id="6b308-275">表示する構成されたデッドロック イベントが含まれているセッションを右クリックして、 **[ライブ データの監視]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-275">Right-click the session that contains the configured deadlock event that you want to view, and select **Watch Live Data**.</span></span>  
  
-   <span data-ttu-id="6b308-276">デッドロック イベントを選択して、[詳細] ペインの **[デッドロック]** タブでグラフを表示します。</span><span class="sxs-lookup"><span data-stu-id="6b308-276">Select the deadlock event and view the graph on the **Deadlock** tab in the Details pane.</span></span>  
  
 <span data-ttu-id="6b308-277">クエリ プラン グラフを表示するには:</span><span class="sxs-lookup"><span data-stu-id="6b308-277">To view query plan graphs:</span></span>  
  
1.  <span data-ttu-id="6b308-278">オブジェクトエクスプローラーで、[**管理**]、[**拡張イベント**]、[**セッション**] ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6b308-278">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="6b308-279">表示する構成されたクエリ プラン グラフ (query_post_compilation_showplan など) が含まれているセッションを右クリックして、 **[ライブ データの監視]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b308-279">Right-click the session that contains the query plan graph that you want to view (for example, query_post_compilation_showplan), and then select **Watch Live Data**.</span></span>  
  
3.  <span data-ttu-id="6b308-280">クエリ プラン グラフ イベント (query_post_compilation_showplan など) を選択して、[詳細] ペインの **[クエリ プラン]** タブでグラフを表示します。</span><span class="sxs-lookup"><span data-stu-id="6b308-280">Select the query plan graph event (for example, query_post_compilation_showplan) and view the graph on the **Query plan** tab in the Details pane.</span></span>  
  
  
