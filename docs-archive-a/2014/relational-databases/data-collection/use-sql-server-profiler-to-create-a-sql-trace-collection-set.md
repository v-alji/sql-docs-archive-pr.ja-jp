---
title: SQL Server プロファイラーを使用して SQL トレースコレクションセットを作成する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace collector set
ms.assetid: b6941dc0-50f5-475d-82eb-ce7c68117489
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e9c9514fef8069cef615d1480aad1e0acd1582cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643975"
---
# <a name="use-sql-server-profiler-to-create-a-sql-trace-collection-set-sql-server-management-studio"></a><span data-ttu-id="19f16-102">SQL Server Profiler を使用して SQL トレース コレクション セットを作成する (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="19f16-102">Use SQL Server Profiler to Create a SQL Trace Collection Set (SQL Server Management Studio)</span></span>
  <span data-ttu-id="19f16-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のサーバー側のトレース機能を利用して、ジェネリック SQL トレース コレクター型を使用するコレクション セットを作成するためのトレース定義をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="19f16-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] you can exploit the server-side trace capabilities of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to export a trace definition that you can use to create a collection set that uses the Generic SQL Trace collector type.</span></span> <span data-ttu-id="19f16-104">このプロセスは 2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="19f16-104">There are two parts to this process:</span></span>  
  
1.  <span data-ttu-id="19f16-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] トレースの作成とエクスポート</span><span class="sxs-lookup"><span data-stu-id="19f16-105">Create and export a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace.</span></span>  
  
2.  <span data-ttu-id="19f16-106">エクスポートされたトレースに基づく新しいコレクション セットのスクリプト化</span><span class="sxs-lookup"><span data-stu-id="19f16-106">Script a new collection set based on an exported trace.</span></span>  
  
 <span data-ttu-id="19f16-107">次の手順のシナリオでは、完了に 80 ミリ秒以上かかるストアド プロシージャに関するデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="19f16-107">The scenario for the following procedures involves collecting data about any stored procedure that requires 80 milliseconds or longer to complete.</span></span> <span data-ttu-id="19f16-108">この手順を完了するには、次の操作を実行できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="19f16-108">In order to complete these procedures you should be able to:</span></span>  
  
-   <span data-ttu-id="19f16-109">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用したトレースの作成および構成</span><span class="sxs-lookup"><span data-stu-id="19f16-109">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create and configure a trace.</span></span>  
  
-   <span data-ttu-id="19f16-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用したクエリの表示、編集、および実行</span><span class="sxs-lookup"><span data-stu-id="19f16-110">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open, edit, and execute a query.</span></span>  
  
### <a name="create-and-export-a-sql-server-profiler-trace"></a><span data-ttu-id="19f16-111">SQL Server Profiler トレースの作成とエクスポート</span><span class="sxs-lookup"><span data-stu-id="19f16-111">Create and export a SQL Server Profiler trace</span></span>  
  
1.  <span data-ttu-id="19f16-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を開きます</span><span class="sxs-lookup"><span data-stu-id="19f16-112">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="19f16-113">( **[ツール]** メニューの **[SQL Server Profiler]** をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="19f16-113">(On the **Tools** menu, click **SQL Server Profiler**.)</span></span>  
  
2.  <span data-ttu-id="19f16-114">**[サーバーへの接続]** ダイアログ ボックスで、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-114">In the **Connect to Server** dialog box, click **Cancel**.</span></span>  
  
3.  <span data-ttu-id="19f16-115">このシナリオでは、実行時間の値が既定でミリ秒で表示されるように設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="19f16-115">For this scenario, ensure that duration values are configured to display in milliseconds (the default).</span></span> <span data-ttu-id="19f16-116">そのためには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="19f16-116">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="19f16-117">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-117">On the **Tools** menu, click **Options**.</span></span>  
  
    2.  <span data-ttu-id="19f16-118">**[表示オプション]** 領域で、[実行時間列の値をマイクロ秒で表示する] チェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="19f16-118">In the **Display Options** area, ensure that the Show values in Duration column in microseconds check box is cleared.</span></span>  
  
    3.  <span data-ttu-id="19f16-119">**[OK]** をクリックして **[全般オプション]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="19f16-119">Click **OK** to close the **General Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="19f16-120">**[ファイル]** メニューの **[新しいトレース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-120">On the **File** menu, click **New Trace**.</span></span>  
  
5.  <span data-ttu-id="19f16-121">**[サーバーへの接続]** ダイアログ ボックスで、接続するサーバーを選択して **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-121">In the **Connect to Server** dialog box, select the server that you want to connect to, and then click **Connect**.</span></span>  
  
     <span data-ttu-id="19f16-122">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="19f16-122">The **Trace Properties** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="19f16-123">**[全般]** タブで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="19f16-123">On the **General** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="19f16-124">**[トレース名]** ボックスに、トレースに使用する名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="19f16-124">In the **Trace name** box, type the name that you want to use for the trace.</span></span> <span data-ttu-id="19f16-125">この例では、トレース名は「`SPgt80`」です。</span><span class="sxs-lookup"><span data-stu-id="19f16-125">For this example, the trace name is `SPgt80`.</span></span>  
  
    2.  <span data-ttu-id="19f16-126">**[使用するテンプレート]** ボックスの一覧でトレースに使用するテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="19f16-126">In the **Use the template list**, select the template to use for the trace.</span></span> <span data-ttu-id="19f16-127">この例では、 **[TSQL_SPs]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-127">For this example, click **TSQL_SPs**.</span></span>  
  
7.  <span data-ttu-id="19f16-128">**[イベントの選択]** タブで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="19f16-128">On the **Events Selection** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="19f16-129">トレースに使用するイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="19f16-129">Identify the events to use for the trace.</span></span> <span data-ttu-id="19f16-130">この例では、 **[ExistingConnection]** と **[SP:Completed]** を除く **[イベント]** 列のすべてのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="19f16-130">For this example, clear all check boxes in the **Events** column, except for **ExistingConnection** and **SP:Completed**.</span></span>  
  
    2.  <span data-ttu-id="19f16-131">右上隅の **[すべての列を表示する]** チェック ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="19f16-131">In the lower-right corner, select the **Show all columns** check box.</span></span>  
  
    3.  <span data-ttu-id="19f16-132">**[SP:Completed]** 行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-132">Click the **SP:Completed** row.</span></span>  
  
    4.  <span data-ttu-id="19f16-133">行をスクロールして **[実行時間]** 列を表示し、 **[実行時間]** チェック ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="19f16-133">Scroll across the row to the **Duration** column, and then select the **Duration** check box.</span></span>  
  
8.  <span data-ttu-id="19f16-134">右下隅の **[列フィルター]** をクリックし、 **[フィルターの編集]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="19f16-134">In the lower-right corner, click **Column Filters** to open the **Edit Filter** dialog box.</span></span> <span data-ttu-id="19f16-135">**[フィルターの編集]** ダイアログ ボックスで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="19f16-135">In the **Edit Filter** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="19f16-136">フィルター一覧で、 **[実行時間]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-136">In the filter list, click **Duration**.</span></span>  
  
    2.  <span data-ttu-id="19f16-137">ブール演算子ウィンドウで、[次の値**以上] ノードを**展開し、 `80` 値として「」と入力して、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-137">In the Boolean operator window, expand the **Greater than or equal** node, type `80` as the value, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="19f16-138">**[実行]** をクリックしてトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="19f16-138">Click **Run** to start the trace.</span></span>  
  
10. <span data-ttu-id="19f16-139">ツール バーの **[選択されたトレースの停止]** または **[選択されたトレースの一時停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-139">On the toolbar, click **Stop Selected Trace** or **Pause Selected Trace**.</span></span>  
  
11. <span data-ttu-id="19f16-140">**[ファイル]** メニューで **[エクスポート]** 、 **[トレース定義のスクリプト]** の順にポイントし、 **[SQL トレース コレクション セット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-140">On the **File** menu, point to **Export**, point to **Script Trace Definition**, and then click **For SQL Trace Collection Set**.</span></span>  
  
12. <span data-ttu-id="19f16-141">**[名前を付けてファイルを保存]** ダイアログ ボックスの **[ファイル名]** ボックスに、トレース定義に使用する名前を入力し、目的の場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="19f16-141">In the **Save As** dialog box, type the name that you want to use for the trace definition in the **File name** box, and then save it in the location that you want.</span></span> <span data-ttu-id="19f16-142">この例では、ファイル名はトレース名 (SPgt80) と同じです。</span><span class="sxs-lookup"><span data-stu-id="19f16-142">For this example, the file name is the same as the trace name (SPgt80).</span></span>  
  
13. <span data-ttu-id="19f16-143">ファイルが正常に保存されたことを通知するメッセージを受信したら **[OK]** をクリックし、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を閉じます。</span><span class="sxs-lookup"><span data-stu-id="19f16-143">Click **OK** when you receive a message that the file was successfully saved, and then close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="script-a-new-collection-set-from-a-sql-server-profiler-trace"></a><span data-ttu-id="19f16-144">SQL Server Profiler トレースに基づく新しいコレクション セットのスクリプト化</span><span class="sxs-lookup"><span data-stu-id="19f16-144">Script a new collection set from a SQL Server Profiler trace</span></span>  
  
1.  <span data-ttu-id="19f16-145">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-145">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **File** menu, point to **Open,** and then click **File**.</span></span>  
  
2.  <span data-ttu-id="19f16-146">**[ファイルを開く]** ダイアログ ボックスで、前の手順で作成したファイル (SPgt80) を探して開きます。</span><span class="sxs-lookup"><span data-stu-id="19f16-146">In the **Open File** dialog box, locate and then open the file that you created in the previous procedure (SPgt80).</span></span>  
  
     <span data-ttu-id="19f16-147">保存したトレース情報がクエリ ウィンドウで開かれ、新しいコレクション セットを作成するために実行できるスクリプトにマージされます。</span><span class="sxs-lookup"><span data-stu-id="19f16-147">The trace information that you saved is opened in a Query window and merged into a script that you can run to create the new collection set.</span></span>  
  
3.  <span data-ttu-id="19f16-148">スクリプトをスクロールし、スクリプトのコメント テキストに示されている次の置換を行います。</span><span class="sxs-lookup"><span data-stu-id="19f16-148">Scroll through the script and make the following replacements, which are noted in the script comment text:</span></span>  
  
    -   <span data-ttu-id="19f16-149">**SQLTrace Collection Set Name Here** をコレクション セットに使用する名前に置換します。</span><span class="sxs-lookup"><span data-stu-id="19f16-149">Replace **SQLTrace Collection Set Name Here** with the name that you want to use for the collection set.</span></span> <span data-ttu-id="19f16-150">この例では、コレクション セット名は "`SPROC_CollectionSet`" です。</span><span class="sxs-lookup"><span data-stu-id="19f16-150">For this example, name the collection set `SPROC_CollectionSet`.</span></span>  
  
    -   <span data-ttu-id="19f16-151">**SQLTrace Collection Item Name Here** をコレクション アイテムに使用する名前に置換します。</span><span class="sxs-lookup"><span data-stu-id="19f16-151">Replace **SQLTrace Collection Item Name Here** with the name that you want to use for the collection item.</span></span> <span data-ttu-id="19f16-152">この例では、コレクション アイテム名は "`SPROC_Collection_Item`" です。</span><span class="sxs-lookup"><span data-stu-id="19f16-152">For this example, name the collection item `SPROC_Collection_Item`.</span></span>  
  
4.  <span data-ttu-id="19f16-153">**[実行]** をクリックして、クエリを実行してコレクション セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="19f16-153">Click **Execute** to run the query and to create the collection set.</span></span>  
  
5.  <span data-ttu-id="19f16-154">[オブジェクト エクスプローラー] で、コレクション セットが作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="19f16-154">In Object Explorer, verify that the collection set was created.</span></span> <span data-ttu-id="19f16-155">そのためには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="19f16-155">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="19f16-156">**[管理]** を右クリックし、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19f16-156">Right-click **Management**, and then click **Refresh**.</span></span>  
  
    2.  <span data-ttu-id="19f16-157">**[管理]** 、 **[データ コレクション]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="19f16-157">Expand **Management**, and then expand **Data Collection**.</span></span>  
  
     <span data-ttu-id="19f16-158">`SPROC_CollectionSet`コレクションセットは、[**システムデータコレクションセット**ノードと同じレベルで表示されます。</span><span class="sxs-lookup"><span data-stu-id="19f16-158">The `SPROC_CollectionSet` collection set appears at the same level as the **System Data Collection Sets** node.</span></span> <span data-ttu-id="19f16-159">既定では、このコレクション セットは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="19f16-159">By default, the collection set is disabled.</span></span>  
  
6.  <span data-ttu-id="19f16-160">オブジェクト エクスプローラーを使用して、コレクション モードやアップロード スケジュールなどの SPROC_CollectionSet のプロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="19f16-160">Use Object Explorer to edit the properties of SPROC_CollectionSet, such as the collection mode and upload schedule.</span></span> <span data-ttu-id="19f16-161">編集方法は、データ コレクターで用意されているシステム データ コレクション セットの場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="19f16-161">Follow the same procedures that you would for the System Data collection sets that are provided with the data collector.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19f16-162">例</span><span class="sxs-lookup"><span data-stu-id="19f16-162">Example</span></span>  
 <span data-ttu-id="19f16-163">次のコード例は、前述の手順を実行することによって得られる最終的なスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="19f16-163">The following code sample is the final script resulting from the steps documented in the preceding procedures.</span></span>  
  
```  
/*************************************************************/  
-- SQL Trace collection set generated from SQL Server Profiler  
-- Date: 11/19/2007  12:55:31 AM  
/*************************************************************/  
  
USE msdb  
GO  
  
BEGIN TRANSACTION  
BEGIN TRY  
  
-- Define collection set  
-- ***  
-- *** Replace 'SqlTrace Collection Set Name Here' in the   
-- *** following script with the name you want  
-- *** to use for the collection set.  
-- ***  
DECLARE @collection_set_id int;  
EXEC [dbo].[sp_syscollector_create_collection_set]  
    @name = N'SPROC_CollectionSet',  
    @schedule_name = N'CollectorSchedule_Every_15min',  
    @collection_mode = 0, -- cached mode needed for Trace collections  
    @logging_level = 0, -- minimum logging  
    @days_until_expiration = 5,  
    @description = N'Collection set generated by SQL Server Profiler',  
    @collection_set_id = @collection_set_id output;  
SELECT @collection_set_id;  
  
-- Define input and output variables for the collection item.  
DECLARE @trace_definition xml;  
DECLARE @collection_item_id int;  
  
-- Define the trace parameters as an XML variable  
SELECT @trace_definition = convert(xml,   
N'<ns:SqlTraceCollector xmlns:ns"DataCollectorType" use_default="0">  
<Events>  
  <EventType name="Sessions">  
    <Event id="17" name="ExistingConnection" columnslist="1,2,14,26,3,35,12" />  
  </EventType>  
  <EventType name="Stored Procedures">  
    <Event id="43" name="SP:Completed" columnslist="1,2,26,34,3,35,12,13,14,22" />  
  </EventType>  
</Events>  
<Filters>  
  <Filter columnid="13" columnname="Duration" logical_operator="AND" comparison_operator="GE" value="80000L" />  
</Filters>  
</ns:SqlTraceCollector>  
');  
  
-- Retrieve the collector type GUID for the trace collector type.  
DECLARE @collector_type_GUID uniqueidentifier;  
SELECT @collector_type_GUID = collector_type_uid FROM [dbo].[syscollector_collector_types] WHERE name = N'Generic SQL Trace Collector Type';  
  
-- Create the trace collection item.  
-- ***  
-- *** Replace 'SqlTrace Collection Item Name Here' in   
-- *** the following script with the name you want to  
-- *** use for the collection item.  
-- ***  
EXEC [dbo].[sp_syscollector_create_collection_item]  
   @collection_set_id = @collection_set_id,  
   @collector_type_uid = @collector_type_GUID,  
   @name = N'SPROC_Collection_Item',  
   @frequency = 900, -- specified the frequency for checking to see if trace is still running  
   @parameters = @trace_definition,  
   @collection_item_id = @collection_item_id output;  
SELECT @collection_item_id;  
  
COMMIT TRANSACTION;  
END TRY  
  
BEGIN CATCH  
ROLLBACK TRANSACTION;  
DECLARE @ErrorMessage nvarchar(4000);  
DECLARE @ErrorSeverity int;  
DECLARE @ErrorState int;  
DECLARE @ErrorNumber int;  
DECLARE @ErrorLine int;  
DECLARE @ErrorProcedure nvarchar(200);  
SELECT @ErrorLine = ERROR_LINE(),  
       @ErrorSeverity = ERROR_SEVERITY(),  
       @ErrorState = ERROR_STATE(),  
       @ErrorNumber = ERROR_NUMBER(),  
       @ErrorMessage = ERROR_MESSAGE(),  
       @ErrorProcedure = ISNULL(ERROR_PROCEDURE(), '-');  
RAISERROR (14684, @ErrorSeverity, 1 , @ErrorNumber, @ErrorSeverity, @ErrorState, @ErrorProcedure, @ErrorLine, @ErrorMessage);  
END CATCH;  
GO  
```  
  
  
