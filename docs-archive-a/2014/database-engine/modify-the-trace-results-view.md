---
title: トレース結果の表示の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 860a80dc-bac0-4ef0-bf7f-7a9b430d7aa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 050c8f179742cf3cef6473b03f062390caf195f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632646"
---
# <a name="modify-the-trace-results-view"></a><span data-ttu-id="4cf64-102">トレース結果の表示の変更</span><span class="sxs-lookup"><span data-stu-id="4cf64-102">Modify the Trace Results View</span></span>
  <span data-ttu-id="4cf64-103">このトピックでは、次のタスクを実行して [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の拡張イベント セッションのトレース結果ビューを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-103">This topic describes how to modify the trace results view of an Extended Events session in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] by performing the following tasks.</span></span>  
  
1.  [<span data-ttu-id="4cf64-104">列の追加または削除</span><span class="sxs-lookup"><span data-stu-id="4cf64-104">Add or Remove Columns</span></span>](#AddRemoveColumns)  
  
2.  [<span data-ttu-id="4cf64-105">結合列の作成、編集、および削除</span><span class="sxs-lookup"><span data-stu-id="4cf64-105">Create, Edit, or Delete Merged Columns</span></span>](#ChangeColumns)  
  
3.  [<span data-ttu-id="4cf64-106">結果の並べ替え</span><span class="sxs-lookup"><span data-stu-id="4cf64-106">Sort the Results</span></span>](#SortResults)  
  
4.  [<span data-ttu-id="4cf64-107">結果のグループ化</span><span class="sxs-lookup"><span data-stu-id="4cf64-107">Group the Results</span></span>](#GroupResults)  
  
5.  [<span data-ttu-id="4cf64-108">結果の集計</span><span class="sxs-lookup"><span data-stu-id="4cf64-108">Aggregate the Results</span></span>](#AggregateResults)  
  
6.  [<span data-ttu-id="4cf64-109">結果をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="4cf64-109">Filter the Results</span></span>](#Filter)  
  
7.  [<span data-ttu-id="4cf64-110">列のテキストの検索</span><span class="sxs-lookup"><span data-stu-id="4cf64-110">Search for Text in Columns</span></span>](#Search)  
  
8.  [<span data-ttu-id="4cf64-111">表示設定の変更</span><span class="sxs-lookup"><span data-stu-id="4cf64-111">Change the Display Settings</span></span>](#ChangeDisplay)  
  
##  <a name="add-or-remove-columns"></a><a name="AddRemoveColumns"></a><span data-ttu-id="4cf64-112">列の追加または削除</span><span class="sxs-lookup"><span data-stu-id="4cf64-112">Add or Remove Columns</span></span>  
  
1.  <span data-ttu-id="4cf64-113">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-113">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-114">セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4cf64-114">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="4cf64-115">トレース結果ウィンドウで、列見出しを右クリックして、 **[列の選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-115">In the trace results window, right-click the column header, and then select **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="4cf64-116">**[列の選択]** ダイアログ ボックスの **[使用可能な列]** で、追加する列の名前を選択し、右矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-116">In the **Choose Columns** dialog box, in the **Available columns** section, select the column names you want to add, and then click the right arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-117">既定では、列は名前順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-117">By default, the columns are arranged by name.</span></span> <span data-ttu-id="4cf64-118">列をイベント順に表示するには、 **[イベントで並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-118">To display the columns by event, click **Arrange by event**.</span></span>  
  
     <span data-ttu-id="4cf64-119">列を削除するには、 **[選択した列]** セクションで、削除する列を選択し、左矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-119">To remove columns, in the **Selected columns** section, select the columns you want to remove, and click the left arrow.</span></span>  
  
4.  <span data-ttu-id="4cf64-120">列の表示順序を変更するには、 **[選択した列]** セクションで **[上へ移動]** または **[下へ移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-120">In the **Selected columns** section, to change the column order display, click **Move Up** or **Move Down** respectively.</span></span> <span data-ttu-id="4cf64-121">複数行を移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="4cf64-121">You cannot move multiple rows.</span></span>  
  
5.  <span data-ttu-id="4cf64-122">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-122">Click **OK**.</span></span>  
  
##  <a name="create-edit-or-delete-merged-columns"></a><a name="ChangeColumns"></a><span data-ttu-id="4cf64-123">結合列の作成、編集、または削除</span><span class="sxs-lookup"><span data-stu-id="4cf64-123">Create, Edit, or Delete Merged Columns</span></span>  
  
#### <a name="to-create-merged-columns"></a><span data-ttu-id="4cf64-124">結合列を作成するには</span><span class="sxs-lookup"><span data-stu-id="4cf64-124">To create merged columns</span></span>  
  
1.  <span data-ttu-id="4cf64-125">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-125">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-126">セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4cf64-126">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="4cf64-127">トレース結果ウィンドウで、列見出しを右クリックして、 **[列の選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-127">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="4cf64-128">**[列の選択]** ダイアログ ボックスで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-128">In the **Choose Columns** dialog box, click **New**.</span></span>  
  
4.  <span data-ttu-id="4cf64-129">**[新しい結合列]** ダイアログ ボックスの **[結合列の名前]** ボックスに結合列の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-129">In the **New Merged Column** dialog box, in the **Merged column name** box, enter a name for the merged columns.</span></span>  
  
5.  <span data-ttu-id="4cf64-130">**[結合元の列]** ボックスの一覧で、結合する列を 2 つ以上選択します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-130">In the **Original columns to merge** box, select two or more columns to merge from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-131">拡張イベントは最大 5 列までの結合をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-131">Extended Events only supports merging up to five columns.</span></span>  
  
6.  <span data-ttu-id="4cf64-132">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-132">Click **OK**.</span></span>  
  
#### <a name="to-edit-merged-columns"></a><span data-ttu-id="4cf64-133">結合列を編集するには</span><span class="sxs-lookup"><span data-stu-id="4cf64-133">To edit merged columns</span></span>  
  
1.  <span data-ttu-id="4cf64-134">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-134">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-135">セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4cf64-135">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="4cf64-136">トレース結果ウィンドウで、列見出しを右クリックして、 **[列の選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-136">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="4cf64-137">**[列の選択]** ダイアログ ボックスで **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-137">In the **Choose Columns** dialog box, click **Edit**.</span></span>  
  
4.  <span data-ttu-id="4cf64-138">結合列の名前を変更するには、 **[新しい結合列]** ダイアログ ボックスの **[結合列の名前]** ボックスに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-138">To change the name of the merged column, in the **New Merged Column** dialog box, in the **Merged column name** box, enter the new name.</span></span>  
  
     <span data-ttu-id="4cf64-139">結合する列を変更するには、 **[結合元の列]** ボックスの一覧で、結合する列を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-139">To change the columns you want to merge, in the **Original columns to merge** box, select the columns you want to merge from the drop-down list, and then click **OK**.</span></span>  
  
#### <a name="to-delete-merged-columns"></a><span data-ttu-id="4cf64-140">結合列を削除するには</span><span class="sxs-lookup"><span data-stu-id="4cf64-140">To delete merged columns</span></span>  
  
1.  <span data-ttu-id="4cf64-141">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-141">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-142">セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4cf64-142">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="4cf64-143">トレース結果ウィンドウで、列見出しを右クリックして、 **[列の選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-143">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="4cf64-144">**[列の選択]** ダイアログ ボックスで、削除する結合列の名前を選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-144">In the **Choose Columns** dialog box, select the name of the merged column you want to delete, and then click **Delete**.</span></span>  
  
##  <a name="sort-the-results"></a><a name="SortResults"></a><span data-ttu-id="4cf64-145">結果の並べ替え</span><span class="sxs-lookup"><span data-stu-id="4cf64-145">Sort the Results</span></span>  
  
#### <a name="to-sort-the-results-in-ascending-or-descending-order"></a><span data-ttu-id="4cf64-146">結果を昇順または降順に並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="4cf64-146">To sort the results in ascending or descending order</span></span>  
  
-   <span data-ttu-id="4cf64-147">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-147">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-148">セッション名を右クリックし、 **[ライブ データの監視]** をクリックして、ツール バーの **[データ フィードの停止]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-148">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
-   <span data-ttu-id="4cf64-149">トレース結果ウィンドウで、並べ替える列見出しを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-149">In the trace results window, right-click the column heading you want to sort.</span></span> <span data-ttu-id="4cf64-150">**[昇順で並べ替え]** または **[降順で並べ替え]** をクリックして、列をそれぞれ昇順または降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-150">Click **Sort Ascending** or **Sort Descending** to sort the column in ascending or descending order respectively.</span></span>  
  
     <span data-ttu-id="4cf64-151">列がグループ化されている場合、データはグループ内のみで並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-151">If you have grouped columns, sorting the column will only sort data within the group.</span></span>  
  
##  <a name="group-results"></a><a name="GroupResults"></a><span data-ttu-id="4cf64-152">結果のグループ化</span><span class="sxs-lookup"><span data-stu-id="4cf64-152">Group Results</span></span>  
  
#### <a name="to-group-the-results-by-a-single-column"></a><span data-ttu-id="4cf64-153">結果を 1 つの列でグループ化するには</span><span class="sxs-lookup"><span data-stu-id="4cf64-153">To group the results by a single column</span></span>  
  
1.  <span data-ttu-id="4cf64-154">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-154">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-155">セッション名を右クリックし、 **[ライブ データの監視]** をクリックして、[拡張イベント] ツール バーの **[データ フィードの停止]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-155">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the Extended Events toolbar.</span></span>  
  
2.  <span data-ttu-id="4cf64-156">トレース結果ウィンドウで、グループ化する列ヘッダーを右クリックし、 **[この列でグループ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-156">In the trace results window, right-click the column header you want to group, and then click **Group By This Column**.</span></span>  
  
#### <a name="to-group-the-results-by-multiple-columns"></a><span data-ttu-id="4cf64-157">結果を複数の列でグループ化するには</span><span class="sxs-lookup"><span data-stu-id="4cf64-157">To group the results by multiple columns</span></span>  
  
1.  <span data-ttu-id="4cf64-158">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-158">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-159">セッション名を右クリックし、 **[ライブ データの監視]** をクリックして、ツール バーの **[データ フィードの停止]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-159">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
2.  <span data-ttu-id="4cf64-160">[拡張イベント] ツール バーの **[グループ化]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-160">Click the **Grouping** button on the Extended Events toolbar.</span></span>  
  
3.  <span data-ttu-id="4cf64-161">**[グループ化]** ダイアログ ボックスの **[使用可能な列]** で、グループ化する列を選択し、右矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-161">In the **Grouping** dialog box, in the **Available columns** box, select the columns you want to group, and then click the right arrow.</span></span>  
  
     <span data-ttu-id="4cf64-162">グループ化の順序を変更するには、 **[次の条件でグループ化される列]** セクションで上矢印または下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-162">To change the grouping order, in the **Columns grouped on** section, click the up or down arrows.</span></span>  
  
     <span data-ttu-id="4cf64-163">グループ化から列を削除するには、 **[次の条件でグループ化される列]** ボックスで、削除する列を選択し、左矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-163">To remove columns from the grouping, in the **Columns grouped on** box, select the columns you want to remove and then click the left arrow.</span></span>  
  
4.  <span data-ttu-id="4cf64-164">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-164">Click **OK**.</span></span>  
  
##  <a name="aggregate-results"></a><a name="AggregateResults"></a><span data-ttu-id="4cf64-165">結果の集計</span><span class="sxs-lookup"><span data-stu-id="4cf64-165">Aggregate Results</span></span>  
 <span data-ttu-id="4cf64-166">拡張イベントは次の 5 つの集計関数をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-166">Extended Events supports five aggregation functions:</span></span>  
  
-   <span data-ttu-id="4cf64-167">SUM</span><span class="sxs-lookup"><span data-stu-id="4cf64-167">Sum</span></span>  
  
-   <span data-ttu-id="4cf64-168">Min</span><span class="sxs-lookup"><span data-stu-id="4cf64-168">Min</span></span>  
  
-   <span data-ttu-id="4cf64-169">Max</span><span class="sxs-lookup"><span data-stu-id="4cf64-169">Max</span></span>  
  
-   <span data-ttu-id="4cf64-170">Average</span><span class="sxs-lookup"><span data-stu-id="4cf64-170">Average</span></span>  
  
-   <span data-ttu-id="4cf64-171">Count</span><span class="sxs-lookup"><span data-stu-id="4cf64-171">Count</span></span>  
  
 <span data-ttu-id="4cf64-172">Sum、Min、Max、および Average は、これらの関数を使用可能な数値列のみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-172">Sum, Min,  Max, and Average can only be used with available numeric columns.</span></span> <span data-ttu-id="4cf64-173">count は、グループ内の選択した列に存在する NULL 以外の値の数を表します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-173">Count is the number of non-null values that exist for the selected column in the group.</span></span>  
  
#### <a name="to-aggregate-results"></a><span data-ttu-id="4cf64-174">結果を集計するには</span><span class="sxs-lookup"><span data-stu-id="4cf64-174">To aggregate results</span></span>  
  
1.  <span data-ttu-id="4cf64-175">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-175">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-176">セッション名を右クリックし、 **[ライブ データの監視]** をクリックして、ツール バーの **[データ フィードの停止]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-176">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-177">集計はグループに対して実行されるため、集計を実行する前に結果をグループ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cf64-177">Aggregation is run against a group, so you must group the results before you can perform the aggregation.</span></span>  
  
2.  <span data-ttu-id="4cf64-178">[拡張イベント] ツール バーの **[集計]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-178">On the Extended Events toolbar, click the **Aggregate** button.</span></span>  
  
     <span data-ttu-id="4cf64-179">集計に使用できる列が **[集計]** ダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-179">The **Aggregation** dialog box appears displaying the columns available for aggregation.</span></span>  
  
3.  <span data-ttu-id="4cf64-180">**[集計の種類]** ボックスの一覧で、対応する列の集計方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-180">Under **Aggregation Type**, select how you want to aggregate the corresponding column from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="4cf64-181">**[集計の並べ替え]** ボックスの一覧で、並べ替えの基準となる列を選択します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-181">In the **Sort aggregation by** box, select the column you want to sort by from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="4cf64-182">集計結果を昇順に並べ替えるには、 **[昇順]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-182">Select the **In ascending order** option to sort the aggregation result in ascending order.</span></span>  
  
6.  <span data-ttu-id="4cf64-183">集計結果を降順に並べ替えるには、 **[降順]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-183">Select the **In descending order** option to sort the aggregation result in descending order.</span></span>  
  
7.  <span data-ttu-id="4cf64-184">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-184">Click **OK**.</span></span>  
  
##  <a name="filter-results"></a><a name="Filter"></a><span data-ttu-id="4cf64-185">結果のフィルター処理</span><span class="sxs-lookup"><span data-stu-id="4cf64-185">Filter Results</span></span>  
 <span data-ttu-id="4cf64-186">フィルターを適用することで、トレース ウィンドウに表示されるトレース結果を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-186">You can apply filters to narrow down the trace results that are displayed in the trace window.</span></span> <span data-ttu-id="4cf64-187">表示フィルターには、時間フィルターと高度なフィルターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4cf64-187">The display filter includes a time filter and an advanced filter.</span></span> <span data-ttu-id="4cf64-188">時間フィルターではトレース結果をイベントのタイムスタンプでフィルター処理し、高度なフィルターではイベントのフィールドとアクションを使用してフィルター条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-188">You use the time filter to filter the trace results by event timestamp, and you use the advanced filter to construct filter conditions using the event fields and actions.</span></span> <span data-ttu-id="4cf64-189">時間フィルターと高度なフィルターとの間には論理 AND 関係があります。</span><span class="sxs-lookup"><span data-stu-id="4cf64-189">There is an logical AND relationship between the Time and Advanced Filters.</span></span>  
  
#### <a name="to-create-a-filter"></a><span data-ttu-id="4cf64-190">フィルターを作成するには</span><span class="sxs-lookup"><span data-stu-id="4cf64-190">To create a filter</span></span>  
  
1.  <span data-ttu-id="4cf64-191">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-191">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-192">セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4cf64-192">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="4cf64-193">トレース結果ウィンドウでフィルターを選択し、[拡張イベント] ツール バーの **[フィルター]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-193">In the trace results window, select the results you want to filter, and then on the Extended Events toolbar, click the **Filters** button.</span></span>  
  
3.  <span data-ttu-id="4cf64-194">**[フィルター]** ダイアログ ボックスで **[時間フィルターの設定]** をクリックし、スライダー バーをドラッグしてタイムラインを設定することにより時間フィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-194">In the **Filters** dialog box, select **Set time filter** to set the time filter by dragging the slider bars to set the timeline.</span></span> <span data-ttu-id="4cf64-195">スライダー バーを移動すると、それに応じた時間値が時間ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-195">Note that when you move the slider bars, the time box displays the time value accordingly.</span></span> <span data-ttu-id="4cf64-196">時間を時間ボックスに入力するか、ドロップダウン リストから選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-196">You can also enter the time in the time boxes, or you select it from the drop-down list.</span></span> <span data-ttu-id="4cf64-197">時間を入力すると、その値に応じて左の時間スライダーが移動します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-197">Note that when you enter the time, the left time slider will move accordingly.</span></span>  
  
4.  <span data-ttu-id="4cf64-198">**[追加のフィルター]** セクションでフィルター条件を適用し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-198">In the **Additional Filters** section, apply your filter criteria, and then click **Apply**.</span></span> <span data-ttu-id="4cf64-199">フィルターの作成が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-199">When your finished created the filter, click **OK**.</span></span>  
  
 <span data-ttu-id="4cf64-200">特殊な状況として、イベント フィールドがアクションと同じ名前を持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="4cf64-200">A special situation is when an event field has the same name as an action.</span></span> <span data-ttu-id="4cf64-201">session_id がこの例に該当します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-201">An example of this would be session_id.</span></span> <span data-ttu-id="4cf64-202">session_id フィールドを含むイベントがいくつかあり、session_id アクションを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-202">There are several events that include a session_id field and you could also add the session_id action.</span></span> <span data-ttu-id="4cf64-203">両方の種類の情報が収集されますが、拡張イベント プロファイラーの表示グリッドでは次のロジックが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-203">Both pieces of information are collected, but the Extended Events profiler display grid uses the following logic.</span></span>  
  
-   <span data-ttu-id="4cf64-204">グリッド表示には、1 つの列 (この場合は session_id) だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-204">Only one copy of the column (session_id in this case) is shown in the grid display.</span></span>  
  
-   <span data-ttu-id="4cf64-205">フィールドとアクションの両方がデータに存在する場合は、フィールド値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-205">If both fields and action exist in the data, the field value is shown.</span></span>  
  
-   <span data-ttu-id="4cf64-206">フィールドとアクションの一方のみがデータに存在する場合は、フィールドまたはアクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-206">If only field or action is exists in the data, the field or action is displayed.</span></span>  
  
-   <span data-ttu-id="4cf64-207">フィールドとアクションのどちらも存在しない場合は、NULL が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-207">If neither action nor field exists, display NULL.</span></span>  
  
##  <a name="search-for-text-in-columns"></a><a name="Search"></a><span data-ttu-id="4cf64-208">列内のテキストの検索</span><span class="sxs-lookup"><span data-stu-id="4cf64-208">Search for Text in Columns</span></span>  
  
1.  <span data-ttu-id="4cf64-209">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-209">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-210">セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4cf64-210">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="4cf64-211">[拡張イベント] ツール バーの **[検索]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-211">On the Extended Events toolbar, click the **Find** button.</span></span>  
  
3.  <span data-ttu-id="4cf64-212">**[拡張イベントで検索]** ダイアログ ボックスの **[検索する文字列]** ボックスに、検索するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-212">In the **Find in Extended Events** dialog box, in the **Find what** box, enter the text you want to search for.</span></span>  
  
     <span data-ttu-id="4cf64-213">ドロップダウン リストから直前の 20 回の検索文字列の 1 つを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-213">You can select one of your last 20 search strings from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="4cf64-214">**[検索対象]** ボックスで、ドロップダウン リストから、指定したテキストを検索する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-214">In the **Look in** box, select the location in which to search for the specified text from the drop-down list.</span></span> <span data-ttu-id="4cf64-215">次の検索オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-215">Use the following options for searching:</span></span>  
  
    -   <span data-ttu-id="4cf64-216">**[テーブル列]**。</span><span class="sxs-lookup"><span data-stu-id="4cf64-216">**Table Columns**.</span></span> <span data-ttu-id="4cf64-217">トレース ウィンドウに表示されているすべての列を検索するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-217">Use this option to search all visible columns in the trace window.</span></span>  
  
    -   <span data-ttu-id="4cf64-218">**詳細**。</span><span class="sxs-lookup"><span data-stu-id="4cf64-218">**Details**.</span></span> <span data-ttu-id="4cf64-219">このオプションを使用すると、[**拡張イベントで検索**] ダイアログボックスを開く前に選択したトレースウィンドウで、昇格および昇格されていないすべての列を検索できます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-219">Use this option to search all columns (promoted and non-promoted) in the trace window that were selected before opening the **Find in Extended Events** dialog box.</span></span>  
  
    -   <span data-ttu-id="4cf64-220">**\<Event column name>**.</span><span class="sxs-lookup"><span data-stu-id="4cf64-220">**\<Event column name>**.</span></span> <span data-ttu-id="4cf64-221">ドロップダウン リストから特定のイベント列で検索するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-221">Use this option to search in a specific event column from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="4cf64-222">検索の定義方法を指定するには、次のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-222">Use the following options to specify how you want to define the search:</span></span>  
  
    1.  <span data-ttu-id="4cf64-223">**大文字と小文字を区別**します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-223">**Match case**.</span></span> <span data-ttu-id="4cf64-224">**[検索する文字列]** で入力したテキストに大文字と小文字の違いを含めて完全に一致する検索結果を表示するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-224">Use this option to display the search results for the text you entered in the **Find what** box that are matched both by content and by case.</span></span>  
  
    2.  <span data-ttu-id="4cf64-225">**単語単位で検索**します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-225">**Match whole word**.</span></span> <span data-ttu-id="4cf64-226">入力したテキストに単語単位で一致する検索結果のみを表示するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-226">Use this option to display only the search results for the text you entered that match complete words.</span></span>  
  
    3.  <span data-ttu-id="4cf64-227">**検索**します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-227">**Search up**.</span></span> <span data-ttu-id="4cf64-228">カーソル位置から先頭までを検索するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-228">Use this option to search from your cursor location to the beginning of the results.</span></span>  
  
    4.  <span data-ttu-id="4cf64-229">**を使用**します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-229">**Use**.</span></span> <span data-ttu-id="4cf64-230">このオプションを使用して、[**検索**する文字列] ボックスに入力した特殊文字および正規表現を解釈します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-230">Use this option to interpret the special characters and the regular expressions you entered in the **Find what** box.</span></span> <span data-ttu-id="4cf64-231">特殊文字には 1 文字以上を表すワイルドカード文字 (\*) および (?) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-231">Special characters include the wildcard characters (\*) and (?) to represent one or more characters.</span></span> <span data-ttu-id="4cf64-232">正規表現は、検索テキストのパターンを定義する特殊な表記です。</span><span class="sxs-lookup"><span data-stu-id="4cf64-232">Regular expressions are special notations used to define patterns of search text.</span></span>  
  
6.  <span data-ttu-id="4cf64-233">**[次を検索]** をクリックすると、 **[検索する文字列]** で入力したテキストの次の箇所が検索されます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-233">Click **Find Next** to search for the next text that you entered in the **Find what** box.</span></span>  
  
##  <a name="change-the-display-settings"></a><a name="ChangeDisplay"></a><span data-ttu-id="4cf64-234">表示設定を変更する</span><span class="sxs-lookup"><span data-stu-id="4cf64-234">Change the Display Settings</span></span>  
 <span data-ttu-id="4cf64-235">トレース結果の列情報 (列の順番、結合列、および列幅) とフィルター情報は、拡張イベント表示設定ファイル (.viewsetting ファイル) に保存することができます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-235">You can save column information (column order, merge column, and column width) and filter information of a trace result into an Extended Events display setting file (.viewsetting file).</span></span> <span data-ttu-id="4cf64-236">ファイルを保存した後、トレース結果に適用することによって、ビューを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-236">After saving the file, you can apply it to your trace results to change the view.</span></span>  
  
#### <a name="to-change-the-display-settings"></a><span data-ttu-id="4cf64-237">表示設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="4cf64-237">To change the display settings</span></span>  
  
1.  <span data-ttu-id="4cf64-238">.XEL ファイルを開いてトレース結果を表示します</span><span class="sxs-lookup"><span data-stu-id="4cf64-238">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4cf64-239">セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4cf64-239">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="4cf64-240">トレース結果ウィンドウの [拡張イベント] ツール バー (またはメニュー) で、 **[表示設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cf64-240">In the trace results window, on the Extended Events toolbar or menu, select **Display Settings**.</span></span>  
  
3.  <span data-ttu-id="4cf64-241">ドロップダウン リストから次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-241">From the drop-down list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="4cf64-242">**名前を付けて保存**します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-242">**Save as**.</span></span> <span data-ttu-id="4cf64-243">トレース結果の列情報とフィルター情報を .viewsetting ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="4cf64-243">Save the columns and filter information of a trace result to a .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="4cf64-244">を**開き**ます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-244">**Open**.</span></span> <span data-ttu-id="4cf64-245">既存の .viewsetting ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-245">Open an existing .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="4cf64-246">**[最近使用した項目を開く]**。</span><span class="sxs-lookup"><span data-stu-id="4cf64-246">**Open recent**.</span></span> <span data-ttu-id="4cf64-247">最近保存した .viewsetting ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="4cf64-247">Open a recently saved .viewsetting file.</span></span>  
  
  
