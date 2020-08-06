---
title: テーブルまたはインデックスの圧縮の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.compwiz.selectaction.f1
- sql12.swb.compwiz.welcome.f1
- sql12.swb.compwiz.scriptfileoption.f1
- sql12.swb.compwiz.createjob.f1
- sql12.swb.compwiz.progress.f1
- sql12.swb.compwiz.outputoptions.f1
- sql12.swb.compwiz.compressiontype.f1
- sql12.swb.compwiz.summary.f1
helpviewer_keywords:
- data compression wizard
- compression [SQL Server], enable
ms.assetid: b7442cff-e616-475a-9c5a-5a765089e5f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a51c3b5e0c4e9b5624911310ce20db5a8e060a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643965"
---
# <a name="enable-compression-on-a-table-or-index"></a><span data-ttu-id="c8535-102">テーブルまたはインデックスの圧縮の有効化</span><span class="sxs-lookup"><span data-stu-id="c8535-102">Enable Compression on a Table or Index</span></span>
  <span data-ttu-id="c8535-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、テーブルまたはインデックスで圧縮を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8535-103">This topic describes how to enable compression on a table or index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c8535-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c8535-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c8535-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c8535-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c8535-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c8535-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c8535-107">Security</span><span class="sxs-lookup"><span data-stu-id="c8535-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c8535-108">**次を使用してテーブルまたはインデックスの圧縮を有効にするには:**</span><span class="sxs-lookup"><span data-stu-id="c8535-108">**To enable compression on a table or index, using:**</span></span>  
  
     [<span data-ttu-id="c8535-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c8535-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c8535-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c8535-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c8535-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="c8535-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c8535-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c8535-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c8535-113">システム テーブルで圧縮を有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c8535-113">System tables cannot be enabled for compression.</span></span>  
  
-   <span data-ttu-id="c8535-114">テーブルがヒープの場合、ONLINE モードでは、再構築操作がシングル スレッドになります。</span><span class="sxs-lookup"><span data-stu-id="c8535-114">If the table is a heap, the rebuild operation for ONLINE mode will be single threaded.</span></span> <span data-ttu-id="c8535-115">マルチスレッドのヒープの再構築操作では、OFFLINE モードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="c8535-115">Use OFFLINE mode for a multi-threaded heap rebuild operation.</span></span> <span data-ttu-id="c8535-116">データ圧縮の詳細については、「 [データの圧縮](data-compression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8535-116">For a more information about data compression, see [Data Compression](data-compression.md).</span></span>  
  
-   <span data-ttu-id="c8535-117">固定されていないインデックスがテーブルにある場合、そのパーティションの圧縮設定を変更できません。</span><span class="sxs-lookup"><span data-stu-id="c8535-117">You cannot change the compression setting of a single partition if the table has nonaligned indexes.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c8535-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c8535-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c8535-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="c8535-119">Permissions</span></span>  
 <span data-ttu-id="c8535-120">テーブルまたはインデックスに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c8535-120">Requires ALTER permission on the table or index.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c8535-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c8535-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-compression-on-a-table-or-index"></a><span data-ttu-id="c8535-122">テーブルまたはインデックスの圧縮を有効にするには</span><span class="sxs-lookup"><span data-stu-id="c8535-122">To enable compression on a table or index</span></span>  
  
1.  <span data-ttu-id="c8535-123">オブジェクト エクスプローラーで、圧縮するテーブルを含むデータベースを展開します。次に、 **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c8535-123">In Object Explorer, expand the database that contains the table that you want to compress and then expand the **Tables** folder.</span></span>  
  
2.  <span data-ttu-id="c8535-124">インデックスを圧縮するには、圧縮するインデックスを含むテーブルを展開します。次に、 **[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c8535-124">To compress an index, expand the table that contains the index that you want to compress and then expand the **Indexes** folder.</span></span>  
  
3.  <span data-ttu-id="c8535-125">圧縮するテーブルまたはインデックスを右クリックし、 **[ストレージ]** をポイントして、 **[圧縮の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-125">Right-click the table or index to compress, point to **Storage** and select **Manage Compression...**.</span></span>  
  
4.  <span data-ttu-id="c8535-126">データ圧縮ウィザードの **[データ圧縮ウィザードへようこそ]** ページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-126">In the Data Compression Wizard, on the **Welcome to the Data Compression Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="c8535-127">**[圧縮の種類の選択]** ページで、圧縮するテーブルまたはインデックスの各パーティションに適用する圧縮の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-127">On the **Select Compression Type** page, select the compression type to apply to each partition in the table or index you want to compress.</span></span> <span data-ttu-id="c8535-128">完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-128">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="c8535-129">**[圧縮の種類の選択]** ページには次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="c8535-129">The following options are available on the **Select Compression Type** page:</span></span>  
  
     <span data-ttu-id="c8535-130">**[すべてのパーティションに同じ種類の圧縮を使用する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="c8535-130">**Use the same compression type for all partitions** check box</span></span>  
     <span data-ttu-id="c8535-131">すべてのパーティションに対して同じ圧縮設定を構成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-131">Select to configure the same compression setting for all partitions.</span></span> <span data-ttu-id="c8535-132">これにより、選択ボックスが有効になり、グリッドにある **[圧縮の種類]** 列が無効になります。</span><span class="sxs-lookup"><span data-stu-id="c8535-132">This enables the selection box and disables the **Compression Type** column in the grid.</span></span> <span data-ttu-id="c8535-133">オンにすると、隣接するリストのオプションは、 **[なし]** 、 **[行]** 、および **[ページ]** になります。</span><span class="sxs-lookup"><span data-stu-id="c8535-133">When selected, the options in the adjacent list are **None**, **Row**, and **Page**.</span></span>  
  
     <span data-ttu-id="c8535-134">**[パーティション番号]**</span><span class="sxs-lookup"><span data-stu-id="c8535-134">**Partition Number**</span></span>  
     <span data-ttu-id="c8535-135">テーブルまたはインデックスで各パーティションを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c8535-135">Lists each partition in the table or index.</span></span> <span data-ttu-id="c8535-136">この列は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c8535-136">This column is read-only.</span></span>  
  
     <span data-ttu-id="c8535-137">**[圧縮の種類]**</span><span class="sxs-lookup"><span data-stu-id="c8535-137">**Compression Type**</span></span>  
     <span data-ttu-id="c8535-138">各パーティションの圧縮オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-138">Select the compression option for each partition.</span></span> <span data-ttu-id="c8535-139">**[すべてのパーティションに対して同じ圧縮の種類を使用]** が選択されている場合は、使用できません。</span><span class="sxs-lookup"><span data-stu-id="c8535-139">Is not available when **Use the same compression type for all partitions** is selected.</span></span> <span data-ttu-id="c8535-140">リストのオプションは、 **[なし]** 、 **[行]** 、および **[ページ]** です。</span><span class="sxs-lookup"><span data-stu-id="c8535-140">List options are **None**, **Row**, and **Page**.</span></span>  
  
     <span data-ttu-id="c8535-141">**[境界]**</span><span class="sxs-lookup"><span data-stu-id="c8535-141">**Boundary**</span></span>  
     <span data-ttu-id="c8535-142">パーティションの境界が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8535-142">Displays the partition boundary.</span></span> <span data-ttu-id="c8535-143">この列は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c8535-143">This column is read-only.</span></span>  
  
     <span data-ttu-id="c8535-144">**行数**</span><span class="sxs-lookup"><span data-stu-id="c8535-144">**Row Count**</span></span>  
     <span data-ttu-id="c8535-145">このパーティションの行数を表示します。</span><span class="sxs-lookup"><span data-stu-id="c8535-145">Displays the number of rows in this partition.</span></span> <span data-ttu-id="c8535-146">この列は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c8535-146">This column is read-only.</span></span>  
  
     <span data-ttu-id="c8535-147">**[現在の領域]**</span><span class="sxs-lookup"><span data-stu-id="c8535-147">**Current Space**</span></span>  
     <span data-ttu-id="c8535-148">このパーティションが占有する現在の領域をメガバイト (MB) 単位で表示します。</span><span class="sxs-lookup"><span data-stu-id="c8535-148">Displays the current space this partition occupies in megabytes (MB).</span></span> <span data-ttu-id="c8535-149">この列は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c8535-149">This column is read-only.</span></span>  
  
     <span data-ttu-id="c8535-150">**[要求された圧縮の領域]**</span><span class="sxs-lookup"><span data-stu-id="c8535-150">**Requested Compressed Space**</span></span>  
     <span data-ttu-id="c8535-151">**[計算]** をクリックした場合に、 **[圧縮の種類]** 列で指定された設定を使用して圧縮した後の、各パーティションの推定サイズがこの列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8535-151">After you click **Calculate**, this column displays the estimated size of each partition after compression by using the setting specified in the **Compression Type** column.</span></span> <span data-ttu-id="c8535-152">この列は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c8535-152">This column is read-only.</span></span>  
  
     <span data-ttu-id="c8535-153">**[計算]**</span><span class="sxs-lookup"><span data-stu-id="c8535-153">**Calculate**</span></span>  
     <span data-ttu-id="c8535-154">**[圧縮の種類]** 列で指定された設定を使用して圧縮した後の、各パーティションのサイズを推定する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-154">Click to estimate the size of each partition after compression by using the setting specified in the **Compression Type** column.</span></span>  
  
6.  <span data-ttu-id="c8535-155">**[出力オプションの選択]** ページで、圧縮を完了する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8535-155">In the **Select an Output Option** page, specify how you want to complete your compression.</span></span> <span data-ttu-id="c8535-156">ウィザードの前のページに基づいて SQL スクリプトを作成するには、 **[スクリプトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-156">Select **Create Script** to create a SQL script based the previous pages in the wizard.</span></span> <span data-ttu-id="c8535-157">ウィザードの残りのすべてのページが完了した後に新しいパーティション テーブルを作成するには、 **[すぐに実行する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-157">Select **Run immediately** to create the new partitioned table after completing all remaining pages in the wizard.</span></span> <span data-ttu-id="c8535-158">事前に定義した時刻に新しいパーティション テーブルを作成するには、 **[スケジュール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-158">Select **Schedule** to create the new partitioned table at a predetermined time in the future.</span></span>  
  
     <span data-ttu-id="c8535-159">**[スクリプトの作成]** を選択した場合、 **[スクリプト オプション]** で次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8535-159">If you select **Create script**, the following options are available under **Script options**:</span></span>  
  
     <span data-ttu-id="c8535-160">**[スクリプトをファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="c8535-160">**Script to file**</span></span>  
     <span data-ttu-id="c8535-161">スクリプトを .sql ファイルとして生成します。</span><span class="sxs-lookup"><span data-stu-id="c8535-161">Generates the script as a .sql file.</span></span> <span data-ttu-id="c8535-162">**[ファイル名]** ボックスにファイルの名前と場所を入力するか、または **[参照]** をクリックして **[スクリプト ファイルの場所]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="c8535-162">Enter a file name and location in the **File name** box or click **Browse** to open the **Script File Location** dialog box.</span></span> <span data-ttu-id="c8535-163">**[名前を付けて保存]** で、 **[Unicode テキスト]** または **[ANSI テキスト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-163">From **Save As**, select **Unicode text** or **ANSI text**.</span></span>  
  
     <span data-ttu-id="c8535-164">**[スクリプトをクリップボードに保存]**</span><span class="sxs-lookup"><span data-stu-id="c8535-164">**Script to Clipboard**</span></span>  
     <span data-ttu-id="c8535-165">スクリプトをクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="c8535-165">Saves the script to the Clipboard.</span></span>  
  
     <span data-ttu-id="c8535-166">**[スクリプトを新しいクエリ ウィンドウに保存]**</span><span class="sxs-lookup"><span data-stu-id="c8535-166">**Script to New Query Window**</span></span>  
     <span data-ttu-id="c8535-167">新しいクエリ エディター ウィンドウにスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="c8535-167">Generates the script to a new Query Editor window.</span></span> <span data-ttu-id="c8535-168">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="c8535-168">This is the default selection.</span></span>  
  
     <span data-ttu-id="c8535-169">**[スケジュール]** を選択した場合は、 **[スケジュールの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-169">If you select **Schedule**, click **Change schedule**.</span></span>  
  
    1.  <span data-ttu-id="c8535-170">**[新しいジョブ スケジュール]** ダイアログ ボックスで、 **[名前]** ボックスに、ジョブのスケジュールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-170">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
    2.  <span data-ttu-id="c8535-171">**[スケジュールの種類]** ボックスで、スケジュールの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-171">On the **Schedule type** list, select the type of schedule:</span></span>  
  
        -   <span data-ttu-id="c8535-172">**[SQL Server エージェントの開始時に自動的に開始]**</span><span class="sxs-lookup"><span data-stu-id="c8535-172">**Start automatically when SQL Server Agent starts**</span></span>  
  
        -   <span data-ttu-id="c8535-173">**[CPU がアイドル状態になったときに開始]**</span><span class="sxs-lookup"><span data-stu-id="c8535-173">**Start whenever the CPUs become idle**</span></span>  
  
        -   <span data-ttu-id="c8535-174">**[定期的]** 。</span><span class="sxs-lookup"><span data-stu-id="c8535-174">**Recurring**.</span></span> <span data-ttu-id="c8535-175">新しいパーティション テーブルを新しい情報で定期的に更新するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-175">Select this option if your new partitioned table updates with new information on a regular basis.</span></span>  
  
        -   <span data-ttu-id="c8535-176">**[指定日時]** 。</span><span class="sxs-lookup"><span data-stu-id="c8535-176">**One time**.</span></span> <span data-ttu-id="c8535-177">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="c8535-177">This is the default selection.</span></span>  
  
    3.  <span data-ttu-id="c8535-178">**[有効]** チェック ボックスをオンまたはオフにして、スケジュールを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="c8535-178">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
    4.  <span data-ttu-id="c8535-179">**[定期的]** を選択した場合:</span><span class="sxs-lookup"><span data-stu-id="c8535-179">If you select **Recurring**:</span></span>  
  
        1.  <span data-ttu-id="c8535-180">**[頻度]** の **[実行]** ボックスの一覧で、実行の頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8535-180">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
            -   <span data-ttu-id="c8535-181">**[日単位]** を選択した場合は、 **[間隔]** ボックスに、ジョブ スケジュールを繰り返す頻度を日単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-181">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
            -   <span data-ttu-id="c8535-182">**[週単位]** を選択した場合は、 **[間隔]** ボックスに、ジョブ スケジュールを繰り返す頻度を週単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-182">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="c8535-183">ジョブ スケジュールを実行する曜日を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-183">Select the day or days of the week on which the job schedule is run.</span></span>  
  
            -   <span data-ttu-id="c8535-184">**[月単位]** を選択した場合は、 **[日]** または **[曜日]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-184">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                -   <span data-ttu-id="c8535-185">**[日]** を選択した場合は、ジョブ スケジュールを実行する日付と、ジョブ スケジュールを繰り返す頻度を月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="c8535-185">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="c8535-186">たとえば、隔月の 15 日にジョブ スケジュールを実行する場合は、 **[日]** を選択し、1 番目のボックスに「15」と入力し、2 番目のボックスに「2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-186">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="c8535-187">2 番目のボックスで使用できる最大の値は "99" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c8535-187">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                -   <span data-ttu-id="c8535-188">**[曜日]** を選択した場合は、ジョブ スケジュールを実行する曜日と、ジョブ スケジュールを繰り返す頻度を月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="c8535-188">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="c8535-189">たとえば、隔月の最後の平日にジョブ スケジュールを実行する場合は、 **[日]** を選択し、リストから **[最終]** を選択します。次に 2 番目のリストから **[平日]** を選択し、最後のボックスに「2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-189">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="c8535-190">**[第 1]** 、 **[第 2]** 、 **[第 3]** 、または **[第 4]** も、特定の平日 (たとえば、日曜日や水曜日) に加えて、最初の 2 つのリストから選択できます。</span><span class="sxs-lookup"><span data-stu-id="c8535-190">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="c8535-191">最後のボックスで使用できる最大の値は "99" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c8535-191">Please note that the largest number allowed in the last box is "99".</span></span>  
  
        2.  <span data-ttu-id="c8535-192">**[一日のうちの頻度]** で、頻度、ジョブ スケジュールを実行する当日にジョブ スケジュールを繰り返す頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8535-192">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
            -   <span data-ttu-id="c8535-193">**[1 回]** を選択した場合は、ジョブ スケジュールを実行する特定の時刻を **[1 回]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-193">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="c8535-194">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-194">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            -   <span data-ttu-id="c8535-195">**[間隔]** を選択した場合は、 **[頻度]** で選択した日にジョブ スケジュールを実行する頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8535-195">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="c8535-196">たとえば、ジョブ スケジュールを実行する当日に 2 時間おきにジョブ スケジュールを実行する場合は、 **[間隔]** を選択し、1 番目のボックスに「2」と入力してから、 **[時間]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-196">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="c8535-197">このリストでは、 **[分]** と **[秒]** を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="c8535-197">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="c8535-198">1 番目のボックスで使用できる最大の値は "100" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c8535-198">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                 <span data-ttu-id="c8535-199">**[開始]** ボックスに、ジョブ スケジュールの実行を開始する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-199">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="c8535-200">**[終了]** ボックスに、ジョブ スケジュールの実行を終了する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-200">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="c8535-201">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-201">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        3.  <span data-ttu-id="c8535-202">**[期間]** で、 **[開始日]** に、ジョブ スケジュールの実行を開始する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-202">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="c8535-203">**[終了日]** を選択します。ジョブ スケジュールの実行を停止するタイミングを指定しない場合は、 **[終了日なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8535-203">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="c8535-204">**[終了日]** を選択した場合は、ジョブ スケジュールの実行を停止する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-204">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
    5.  <span data-ttu-id="c8535-205">**[指定日時]** を選択した場合は、 **[指定日時に発生]** の **[日付]** ボックスに、ジョブ スケジュールを実行する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-205">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="c8535-206">**[時刻]** ボックスに、ジョブ スケジュールを実行する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-206">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="c8535-207">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8535-207">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
    6.  <span data-ttu-id="c8535-208">**[概要]** の **[説明]** で、すべてのジョブ スケジュール設定が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c8535-208">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
    7.  <span data-ttu-id="c8535-209">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-209">Click **OK**.</span></span>  
  
     <span data-ttu-id="c8535-210">このページを完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-210">After completing this page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="c8535-211">**[概要の確認]** ページの **[選択内容の確認]** で、使用可能なすべてのオプションを展開し、すべての圧縮設定が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c8535-211">On the **Review Summary** page, under **Review your selections**, expand all available options to verify that all compression settings are correct.</span></span> <span data-ttu-id="c8535-212">すべての設定が適切であることを確認したら、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-212">If everything is as expected, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="c8535-213">**[圧縮ウィザードの進行状況]** ページで、パーティションの作成ウィザードの操作に関する状態情報を監視します。</span><span class="sxs-lookup"><span data-stu-id="c8535-213">On the **Compression Wizard Progress** page, monitor status information about the actions of the Create Partition Wizard.</span></span> <span data-ttu-id="c8535-214">ウィザードで選択したオプションに応じて、[進行状況] ページに 1 つまたは複数のアクションが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c8535-214">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="c8535-215">上部のボックスには、ウィザードの全体的な状態と受信した状態メッセージ、エラー メッセージ、および警告メッセージの数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8535-215">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="c8535-216">**[圧縮ウィザードの進行状況]** ページでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8535-216">The following options are available on the **Compression Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="c8535-217">**詳細**</span><span class="sxs-lookup"><span data-stu-id="c8535-217">**Details**</span></span>  
     <span data-ttu-id="c8535-218">アクション、状態、およびウィザードで実行したアクションから返されたメッセージが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c8535-218">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="c8535-219">**操作**</span><span class="sxs-lookup"><span data-stu-id="c8535-219">**Action**</span></span>  
     <span data-ttu-id="c8535-220">各アクションの種類と名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8535-220">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="c8535-221">**状態**</span><span class="sxs-lookup"><span data-stu-id="c8535-221">**Status**</span></span>  
     <span data-ttu-id="c8535-222">全体としてウィザードのアクションが **[成功]** または **[失敗]** のいずれの値を返したかを示します。</span><span class="sxs-lookup"><span data-stu-id="c8535-222">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="c8535-223">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="c8535-223">**Message**</span></span>  
     <span data-ttu-id="c8535-224">プロセスから返されたすべてのエラー メッセージまたは警告メッセージを提供します。</span><span class="sxs-lookup"><span data-stu-id="c8535-224">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="c8535-225">**Report**</span><span class="sxs-lookup"><span data-stu-id="c8535-225">**Report**</span></span>  
     <span data-ttu-id="c8535-226">パーティションの作成ウィザードの結果を含むレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8535-226">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="c8535-227">**[レポートの表示]** 、 **[レポートをファイルに保存]** 、 **[レポートをクリップボードにコピー]** 、 **[レポートを電子メールとして送信]** の各オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="c8535-227">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="c8535-228">**[レポートの表示]**</span><span class="sxs-lookup"><span data-stu-id="c8535-228">**View Report**</span></span>  
     <span data-ttu-id="c8535-229">パーティションの作成ウィザードの進行状況に関するテキスト レポートを表示する **[レポートの表示]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="c8535-229">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="c8535-230">**[レポートをファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="c8535-230">**Save Report to File**</span></span>  
     <span data-ttu-id="c8535-231">**[レポートに名前を付けて保存]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="c8535-231">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="c8535-232">**[レポートをクリップボードにコピー]**</span><span class="sxs-lookup"><span data-stu-id="c8535-232">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="c8535-233">ウィザードの進行状況レポートの結果をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c8535-233">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="c8535-234">**[レポートを電子メールとして送信]**</span><span class="sxs-lookup"><span data-stu-id="c8535-234">**Send Report as Email**</span></span>  
     <span data-ttu-id="c8535-235">ウィザードの進行状況レポートの結果を電子メール メッセージにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c8535-235">Copies the results of the wizard's progress report into an email message.</span></span>  
  
     <span data-ttu-id="c8535-236">完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-236">When complete, click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c8535-237">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c8535-237">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-compression-on-a-table"></a><span data-ttu-id="c8535-238">テーブルで圧縮を有効にするには</span><span class="sxs-lookup"><span data-stu-id="c8535-238">To enable compression on a table</span></span>  
  
1.  <span data-ttu-id="c8535-239">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c8535-239">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c8535-240">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-240">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c8535-241">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-241">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c8535-242">この例では、最初にストアド プロシージャ `sp_estimate_data_compression_savings` を実行して、行の圧縮設定を使用した場合のオブジェクトの推定サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="c8535-242">The example first executes the stored procedure `sp_estimate_data_compression_savings` to return the estimated size of the object if it were to use the ROW compression setting.</span></span> <span data-ttu-id="c8535-243">次に、指定したテーブルのすべてのパーティションで行の圧縮を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c8535-243">The example then enables ROW compression on all partitions in the specified table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_estimate_data_compression_savings 'Production', 'TransactionHistory', NULL, NULL, 'ROW' ;  
  
    ALTER TABLE Production.TransactionHistory REBUILD PARTITION = ALL  
    WITH (DATA_COMPRESSION = ROW);   
    GO  
    ```  
  
#### <a name="to-enable-compression-on-an-index"></a><span data-ttu-id="c8535-244">インデックスで圧縮を有効にするには</span><span class="sxs-lookup"><span data-stu-id="c8535-244">To enable compression on an index</span></span>  
  
1.  <span data-ttu-id="c8535-245">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c8535-245">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c8535-246">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-246">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c8535-247">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8535-247">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c8535-248">この例では、最初に `sys.indexes` カタログ ビューを問い合わせて、 `index_id` テーブルの各インデックスの名前と `Production.TransactionHistory` を返します。</span><span class="sxs-lookup"><span data-stu-id="c8535-248">The example first queries the `sys.indexes` catalog view to return the name and `index_id` for each index on the `Production.TransactionHistory` table.</span></span> <span data-ttu-id="c8535-249">次に、ストアド プロシージャ `sp_estimate_data_compression_savings` を実行して、ページの圧縮設定を使用した場合の指定されたインデックス ID の推定サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="c8535-249">It then executes the stored procedure `sp_estimate_data_compression_savings` to return the estimated size of the specified index ID if it were to use the PAGE compression setting.</span></span> <span data-ttu-id="c8535-250">最後に、インデックス ID 2 (`IX_TransactionHistory_ProductID`) を再構築し、ページの圧縮を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8535-250">Finally, the example rebuilds index ID 2 (`IX_TransactionHistory_ProductID`), specifying PAGE compression.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT name, index_id  
    FROM sys.indexes  
    WHERE OBJECT_NAME (object_id) = N'TransactionHistory';  
  
    EXEC sp_estimate_data_compression_savings   
        @schema_name = 'Production',   
        @object_name = 'TransactionHistory',  
        @index_id = 2,   
        @partition_number = NULL,   
        @data_compression = 'PAGE' ;   
  
    ALTER INDEX IX_TransactionHistory_ProductID ON Production.TransactionHistory REBUILD PARTITION = ALL WITH (DATA_COMPRESSION = PAGE);  
    GO  
    ```  
  
 <span data-ttu-id="c8535-251">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」および「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8535-251">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8535-252">参照</span><span class="sxs-lookup"><span data-stu-id="c8535-252">See Also</span></span>  
 <span data-ttu-id="c8535-253">[データの圧縮](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="c8535-253">[Data Compression](data-compression.md) </span></span>  
 [<span data-ttu-id="c8535-254">sp_estimate_data_compression_savings &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c8535-254">sp_estimate_data_compression_savings &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql)  
  
  
