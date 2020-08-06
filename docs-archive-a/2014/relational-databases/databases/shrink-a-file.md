---
title: ファイルの圧縮 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkfile.f1
helpviewer_keywords:
- shrinking files
- decreasing file size
- databases [SQL Server], shrinking
- reducing file size
- size [SQL Server], files
- file size [SQL Server]
ms.assetid: ce5c8798-c039-4ab2-81e7-90a8d688b893
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac69e4bd2db3ef7fe0815d235dd1de7d3396b302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712009"
---
# <a name="shrink-a-file"></a><span data-ttu-id="b2db9-102">ファイルの圧縮</span><span class="sxs-lookup"><span data-stu-id="b2db9-102">Shrink a File</span></span>
  <span data-ttu-id="b2db9-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータ ファイルまたはログ ファイルを圧縮する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-103">This topic describes how to shrink a data or log file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b2db9-104">ファイルの末尾にあるデータのページを、ファイルの先頭に近い占有されていない領域に移動することにより、データ ファイルが圧縮され、領域が回復されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-104">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="b2db9-105">ファイル末尾に十分な空き領域が作成された場合は、ファイル末尾のデータ ページの割り当てを解除して、ファイル システムに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-105">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
 <span data-ttu-id="b2db9-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b2db9-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b2db9-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b2db9-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b2db9-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b2db9-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b2db9-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="b2db9-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="b2db9-110">Security</span><span class="sxs-lookup"><span data-stu-id="b2db9-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b2db9-111">**以下を使用してデータ ファイルまたはログ ファイルを圧縮するには:**</span><span class="sxs-lookup"><span data-stu-id="b2db9-111">**To shrink a data or log file, using:**</span></span>  
  
     [<span data-ttu-id="b2db9-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b2db9-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b2db9-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b2db9-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b2db9-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="b2db9-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b2db9-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b2db9-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b2db9-116">プライマリ データ ファイルは、model データベースのプライマリ ファイルのサイズより小さくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b2db9-116">The primary data file cannot be made smaller than the size of the primary file in the model database.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b2db9-117">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b2db9-117">Recommendations</span></span>  
  
-   <span data-ttu-id="b2db9-118">ファイルを圧縮するために移動されたデータは、ファイル内のあらゆる使用可能な場所に分散される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b2db9-118">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="b2db9-119">これにより、インデックスの断片化が発生し、広範なインデックスを検索するクエリのパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b2db9-119">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="b2db9-120">断片化を解消するには、圧縮後にファイルのインデックスを再構築することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b2db9-120">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b2db9-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b2db9-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b2db9-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="b2db9-122">Permissions</span></span>  
 <span data-ttu-id="b2db9-123">**sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="b2db9-123">Requires membership in the **sysadmin** fixed server role or the **db_owner** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b2db9-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b2db9-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-shrink-a-data-or-log-file"></a><span data-ttu-id="b2db9-125">データ ファイルまたはログ ファイルを圧縮するには</span><span class="sxs-lookup"><span data-stu-id="b2db9-125">To shrink a data or log file</span></span>  
  
1.  <span data-ttu-id="b2db9-126">オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-126">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b2db9-127">**[データベース]** を展開し、圧縮するデータベースを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-127">Expand **Databases** and then right-click the database that you want to shrink.</span></span>  
  
3.  <span data-ttu-id="b2db9-128">**[タスク]** 、 **[圧縮]** の順にポイントし、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-128">Point to **Tasks**, point to **Shrink**, and then click **Files**.</span></span>  
  
     <span data-ttu-id="b2db9-129">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-129">**Database**</span></span>  
     <span data-ttu-id="b2db9-130">選択しているデータベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-130">Displays the name of the selected database.</span></span>  
  
     <span data-ttu-id="b2db9-131">**ファイルの種類**</span><span class="sxs-lookup"><span data-stu-id="b2db9-131">**File type**</span></span>  
     <span data-ttu-id="b2db9-132">ファイルの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-132">Select the file type for the file.</span></span> <span data-ttu-id="b2db9-133">選択できるファイルの種類は **[データ]** および **[ログ]** です。</span><span class="sxs-lookup"><span data-stu-id="b2db9-133">The available choices are **Data** and **Log** files.</span></span> <span data-ttu-id="b2db9-134">既定の選択は **[データ]** です。</span><span class="sxs-lookup"><span data-stu-id="b2db9-134">The default selection is **Data**.</span></span> <span data-ttu-id="b2db9-135">別のファイル グループの種類を選択すると、その選択に応じて他のフィールドの選択が変更されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-135">Selecting a different filegroup type changes the selections in the other fields accordingly.</span></span>  
  
     <span data-ttu-id="b2db9-136">**[ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-136">**Filegroup**</span></span>  
     <span data-ttu-id="b2db9-137">上記で選択した **[ファイルの種類]** に関連付けられたファイル グループの一覧から、ファイル グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-137">Select a filegroup from the list of Filegroups associated with the selected **File type** above.</span></span> <span data-ttu-id="b2db9-138">別のファイル グループを選択すると、その選択に応じて他のフィールドの選択が変更されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-138">Selecting a different filegroup changes the selections in the other fields accordingly.</span></span>  
  
     <span data-ttu-id="b2db9-139">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-139">**File name**</span></span>  
     <span data-ttu-id="b2db9-140">選択したファイル グループおよびファイルの種類で利用可能なファイルの一覧からファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-140">Select a file from the list of available files of the selected filegroup and file type.</span></span>  
  
     <span data-ttu-id="b2db9-141">**場所**</span><span class="sxs-lookup"><span data-stu-id="b2db9-141">**Location**</span></span>  
     <span data-ttu-id="b2db9-142">現在選択されているファイルへの完全なパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-142">Displays the full path to the currently selected file.</span></span> <span data-ttu-id="b2db9-143">このパスは編集できませんが、クリップボードにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-143">The path is not editable, but it can be copied to the clipboard.</span></span>  
  
     <span data-ttu-id="b2db9-144">**[現在割り当てられている領域]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-144">**Currently allocated space**</span></span>  
     <span data-ttu-id="b2db9-145">データ ファイルの場合は、現在割り当てられている領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-145">For data files, displays the current allocated space.</span></span> <span data-ttu-id="b2db9-146">ログ ファイルの場合は、DBCC SQLPERF(LOGSPACE) の出力から計算された、現在割り当てられている領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-146">For log files, displays the current allocated space computed from the output of DBCC SQLPERF(LOGSPACE).</span></span>  
  
     <span data-ttu-id="b2db9-147">**[使用可能な空き領域]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-147">**Available free space**</span></span>  
     <span data-ttu-id="b2db9-148">データ ファイルの場合は、DBCC SHOWFILESTATS(fileid) の出力から計算された、現在使用できる空き領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-148">For data files, displays the current available free space computed from the output of DBCC SHOWFILESTATS(fileid).</span></span> <span data-ttu-id="b2db9-149">ログ ファイルの場合は、DBCC SQLPERF(LOGSPACE) の出力から計算された、現在使用できるスペースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-149">For log files, displays the current available free space computed from the output of DBCC SQLPERF(LOGSPACE).</span></span>  
  
     <span data-ttu-id="b2db9-150">**[未使用領域を解放する]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-150">**Release unused space**</span></span>  
     <span data-ttu-id="b2db9-151">ファイル内のすべての未使用領域をオペレーティング システムに渡し、ファイルを最後に割り当てられたエクステントにまで圧縮して、データをまったく移動せずにファイル サイズを小さくします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-151">Cause any unused space in the files to be released to the operating system and shrink the file to the last allocated extent, reducing the file size without moving any data.</span></span> <span data-ttu-id="b2db9-152">割り当てられていないページへの行の再割り当て処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="b2db9-152">No attempt is made to relocate rows to unallocated pages.</span></span>  
  
     <span data-ttu-id="b2db9-153">**[未使用領域の解放前にページを再構成する]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-153">**Reorganize pages before releasing unused space**</span></span>  
     <span data-ttu-id="b2db9-154">対象ファイルのサイズを指定して DBCC SHRINKFILE を実行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="b2db9-154">Equivalent to executing DBCC SHRINKFILE specifying the target file size.</span></span> <span data-ttu-id="b2db9-155">このオプションがオンになっている場合は、 **[圧縮先のファイル]** ボックスで対象ファイルのサイズを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2db9-155">When this option is selected, the user must specify a target file size in the **Shrink file to** box.</span></span>  
  
     <span data-ttu-id="b2db9-156">**[圧縮先のファイル]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-156">**Shrink file to**</span></span>  
     <span data-ttu-id="b2db9-157">圧縮操作の対象ファイルのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-157">Specifies the target file size for the shrink operation.</span></span> <span data-ttu-id="b2db9-158">サイズは、現在割り当てられている領域より大きく、ファイルに割り当てられた合計エクステントよりも小さくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2db9-158">The size cannot be less than the current allocated space or more than the total extents allocated to the file.</span></span> <span data-ttu-id="b2db9-159">最小値または最大値の範囲外の値を入力した場合、フォーカスを変更したり、ツール バーのボタンをクリックしたりしたときに、入力した値が最小値または最大値に戻ります。</span><span class="sxs-lookup"><span data-stu-id="b2db9-159">Entering a value beyond the minimum or the maximum will revert to the min or the max once the focus is changed or when any of the buttons on the toolbar are clicked.</span></span>  
  
     <span data-ttu-id="b2db9-160">**[データを同じファイル グループの他のファイルに移行してファイルを空にする]**</span><span class="sxs-lookup"><span data-stu-id="b2db9-160">**Empty file by migrating the data to other files in the same filegroup**</span></span>  
     <span data-ttu-id="b2db9-161">指定したファイルからすべてのデータを移行します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-161">Migrate all data from the specified file.</span></span> <span data-ttu-id="b2db9-162">このオプションを使用すると、ALTER DATABASE ステートメントを使用してファイルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-162">This option allows the file to be dropped using the ALTER DATABASE statement.</span></span> <span data-ttu-id="b2db9-163">このオプションは、EMPTYFILE オプションを指定して DBCC SHRINKFILE を実行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="b2db9-163">This option is equivalent to executing DBCC SHRINKFILE with the EMPTYFILE option.</span></span>  
  
4.  <span data-ttu-id="b2db9-164">ファイルの種類とファイル名を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-164">Select the file type and file name.</span></span>  
  
5.  <span data-ttu-id="b2db9-165">必要に応じて、 **[未使用領域を解放する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-165">Optionally, select the **Release unused space** check box.</span></span>  
  
     <span data-ttu-id="b2db9-166">このオプションをオンにすると、ファイル内の未使用領域がオペレーティング システムに解放され、最後に割り当てられたエクステントにファイルが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-166">Selecting this option causes any unused space in the file to be released to the operating system and shrinks the file to the last allocated extent.</span></span> <span data-ttu-id="b2db9-167">これにより、データを移動しなくてもファイル サイズが減少します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-167">This reduces the file size without moving any data.</span></span>  
  
6.  <span data-ttu-id="b2db9-168">必要に応じて、 **[未使用領域の解放前にファイルを再構成する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-168">Optionally, select the **Reorganize files before releasing unused space** check box.</span></span> <span data-ttu-id="b2db9-169">このオプションをオンにする場合は、 **[圧縮先のファイル]** の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2db9-169">If this is selected, the **Shrink file to** value must be specified.</span></span> <span data-ttu-id="b2db9-170">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="b2db9-170">By default, the option is cleared.</span></span>  
  
     <span data-ttu-id="b2db9-171">このオプションをオンにすると、ファイル内の未使用領域がオペレーティング システムに解放され、未割り当てページに行の再割り当てを試みます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-171">Selecting this option causes any unused space in the file to be released to the operating system and tries to relocate rows to unallocated pages.</span></span>  
  
7.  <span data-ttu-id="b2db9-172">必要に応じて、データベースを圧縮した後に、データベース ファイル内に残す空き領域の最大のパーセンテージを入力します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-172">Optionally, enter the maximum percentage of free space to be left in the database file after the database has been shrunk.</span></span> <span data-ttu-id="b2db9-173">0 ～ 99 の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-173">Permissible values are between 0 and 99.</span></span> <span data-ttu-id="b2db9-174">このオプションは、 **[未使用領域の解放前にファイルを再構成する]** がオンになっている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-174">This option is only available when **Reorganize files before releasing unused space** is enabled.</span></span>  
  
8.  <span data-ttu-id="b2db9-175">必要に応じて、 **[データを同じファイル グループの他のファイルに移行してファイルを空にする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-175">Optionally, select the **Empty file by migrating the data to other files in the same filegroup** check box.</span></span>  
  
     <span data-ttu-id="b2db9-176">このオプションをオンにすると、指定したファイルのすべてのデータが同じファイル グループの他のファイルに移動されます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-176">Selecting this option moves all data from the specified file to other files in the filegroup.</span></span> <span data-ttu-id="b2db9-177">その後、空になったファイルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="b2db9-177">The empty file can then be deleted.</span></span> <span data-ttu-id="b2db9-178">このオプションは、EMPTYFILE オプションを指定して DBCC SHRINKFILE を実行するのと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="b2db9-178">This option is the same as executing DBCC SHRINKFILE with the EMPTYFILE option.</span></span>  
  
9. <span data-ttu-id="b2db9-179">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-179">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b2db9-180">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b2db9-180">Using Transact-SQL</span></span>  
  
#### <a name="to-shrink-a-data-or-log-file"></a><span data-ttu-id="b2db9-181">データ ファイルまたはログ ファイルを圧縮するには</span><span class="sxs-lookup"><span data-stu-id="b2db9-181">To shrink a data or log file</span></span>  
  
1.  <span data-ttu-id="b2db9-182">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-182">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2db9-183">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-183">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b2db9-184">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2db9-184">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b2db9-185">この例では、 [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) を使用して、 `UserDB` データベースに存在する `DataFile1` という名前のデータ ファイルのサイズを 7 MB に圧縮します。</span><span class="sxs-lookup"><span data-stu-id="b2db9-185">This example uses [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) to shrink the size of a data file named `DataFile1` in the `UserDB` database to 7 MB.</span></span>  
  
 [!code-sql[DBCC#DBCC_SHRINKFILE1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkfile1)]  
  
## <a name="see-also"></a><span data-ttu-id="b2db9-186">参照</span><span class="sxs-lookup"><span data-stu-id="b2db9-186">See Also</span></span>  
 <span data-ttu-id="b2db9-187">[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b2db9-187">[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) </span></span>  
 <span data-ttu-id="b2db9-188">[データベースの圧縮](shrink-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="b2db9-188">[Shrink a Database](shrink-a-database.md) </span></span>  
 <span data-ttu-id="b2db9-189">[データまたはログ ファイルのデータベースからの削除](delete-data-or-log-files-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="b2db9-189">[Delete Data or Log Files from a Database](delete-data-or-log-files-from-a-database.md) </span></span>  
 <span data-ttu-id="b2db9-190">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b2db9-190">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="b2db9-191">sys.database_files &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b2db9-191">sys.database_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)  
  
  
