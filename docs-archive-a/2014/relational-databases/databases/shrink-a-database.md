---
title: データベースの圧縮 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkdatabase.f1
helpviewer_keywords:
- shrinking databases
- databases [SQL Server], shrinking
- decreasing database size
- database shrinking [SQL Server]
- reducing database size
ms.assetid: 83afbf74-fd50-4c39-831c-b1f473a50620
author: stevestein
ms.author: sstein
ms.openlocfilehash: 246036bfea6dc8431f878165330f7f0571949897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712010"
---
# <a name="shrink-a-database"></a><span data-ttu-id="6ba9f-102">データベースの圧縮</span><span class="sxs-lookup"><span data-stu-id="6ba9f-102">Shrink a Database</span></span>
  <span data-ttu-id="6ba9f-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] から [!INCLUDE[tsql](../../includes/tsql-md.md)]のオブジェクトを使用して、データベースを圧縮する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-103">This topic describes how to shrink a database by using Object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6ba9f-104">ファイルの末尾にあるデータのページを、ファイルの先頭に近い占有されていない領域に移動することにより、データ ファイルが圧縮され、領域が回復されます。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-104">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="6ba9f-105">ファイル末尾に十分な空き領域が作成された場合は、ファイル末尾のデータ ページの割り当てを解除して、ファイル システムに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-105">When enough free space is created at the end of the file, data pages at end of the file can be deallocated and returned to the file system.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6ba9f-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="6ba9f-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6ba9f-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6ba9f-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6ba9f-108">データベースは、そのデータベースの最小サイズより小さくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-108">The database cannot be made smaller than the minimum size of the database.</span></span> <span data-ttu-id="6ba9f-109">最小サイズは、データベースが最初に作成されたときに指定されたサイズか、DBCC SHRINKFILE などのファイル サイズ変更操作によって最後に明示的に設定されたサイズのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-109">The minimum size is the size specified when the database was originally created, or the last explicit size set by using a file-size-changing operation, such as DBCC SHRINKFILE.</span></span> <span data-ttu-id="6ba9f-110">たとえば、作成時にサイズを 10 MB に指定したデータベースが 100 MB まで拡張した場合、データベース内のすべてのデータを削除したとしても、縮小できる限界は 10 MB までです。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-110">For example, if a database was originally created with a size of 10 MB and grew to 100 MB, the smallest size the database could be reduced to is 10 MB, even if all the data in the database has been deleted.</span></span>  
  
-   <span data-ttu-id="6ba9f-111">データベースのバックアップ中、データベースを圧縮することはできません。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-111">You cannot shrink a database while the database is being backed up.</span></span> <span data-ttu-id="6ba9f-112">逆に、データベースの圧縮操作の進行中、データベースをバックアップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-112">Conversely, you cannot backup a database while a shrink operation on the database is in process.</span></span>  
  
-   <span data-ttu-id="6ba9f-113">DBCC SHRINKDATABASE は、xVelocity メモリ最適化列ストア インデックスを検出すると失敗します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-113">DBCC SHRINKDATABASE will fail when it encounters an xVelocity memory optimized columnstore index.</span></span> <span data-ttu-id="6ba9f-114">列ストア インデックスを検出する前に完了した処理は成功するので、データベースが小さくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-114">Work completed before encountering the columnstore index will succeed so the database might be smaller.</span></span> <span data-ttu-id="6ba9f-115">DBCC SHRINKDATABASE を完了するには、DBCC SHRINKDATABASE を実行する前にすべての列ストア インデックスを無効にし、後で列ストア インデックスを再構築します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-115">To complete DBCC SHRINKDATABASE, disable all columnstore indexes before executing DBCC SHRINKDATABASE, and then rebuild the columnstore indexes.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6ba9f-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="6ba9f-116">Recommendations</span></span>  
  
-   <span data-ttu-id="6ba9f-117">データベース内にある現在の空き (未割り当て) 領域の大きさを確認します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-117">To view the current amount of free (unallocated) space in the database.</span></span> <span data-ttu-id="6ba9f-118">詳細については、「 [データベースのデータ領域とログ領域情報の表示](display-data-and-log-space-information-for-a-database.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-118">For more information, see [Display Data and Log Space Information for a Database](display-data-and-log-space-information-for-a-database.md)</span></span>  
  
-   <span data-ttu-id="6ba9f-119">データベースを圧縮する場合は次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-119">Consider the following information when you plan to shrink a database:</span></span>  
  
    -   <span data-ttu-id="6ba9f-120">圧縮操作は、テーブルの切り捨てやテーブルの削除操作など、大きな未使用領域を生成する操作の後に実行すると最も効果的です。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-120">A shrink operation is most effective after an operation that creates lots of unused space, such as a truncate table or a drop table operation.</span></span>  
  
    -   <span data-ttu-id="6ba9f-121">ほとんどのデータベースでは、毎日の定期的操作で使用するための空き領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-121">Most databases require some free space to be available for regular day-to-day operations.</span></span> <span data-ttu-id="6ba9f-122">データベースを何度圧縮しても、データベースのサイズが大きくなってしまう場合は、通常の操作にそれだけの領域が必要であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-122">If you shrink a database repeatedly and notice that the database size grows again, this indicates that the space that was shrunk is required for regular operations.</span></span> <span data-ttu-id="6ba9f-123">このような場合、繰り返しデータベースを圧縮することは無意味です。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-123">In these cases, repeatedly shrinking the database is a wasted operation.</span></span>  
  
    -   <span data-ttu-id="6ba9f-124">圧縮操作では、データベース内のインデックスの断片化状態は保持されず、一般に、断片化の程度が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-124">A shrink operation does not preserve the fragmentation state of indexes in the database, and generally increases fragmentation to a degree.</span></span> <span data-ttu-id="6ba9f-125">この理由からも、データベースを繰り返し圧縮することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-125">This is another reason not to repeatedly shrink the database.</span></span>  
  
    -   <span data-ttu-id="6ba9f-126">特別な要件がない限り、AUTO_SHRINK データベース オプションを ON に設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-126">Unless you have a specific requirement, do not set the AUTO_SHRINK database option to ON.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6ba9f-127">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6ba9f-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6ba9f-128">Permissions</span><span class="sxs-lookup"><span data-stu-id="6ba9f-128">Permissions</span></span>  
 <span data-ttu-id="6ba9f-129">**sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-129">Requires membership in the **sysadmin** fixed server role or the **db_owner** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6ba9f-130">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6ba9f-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-shrink-a-database"></a><span data-ttu-id="6ba9f-131">データベースを圧縮するには</span><span class="sxs-lookup"><span data-stu-id="6ba9f-131">To shrink a database</span></span>  
  
1.  <span data-ttu-id="6ba9f-132">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-132">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="6ba9f-133">**[データベース]** を展開し、圧縮するデータベースを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-133">Expand **Databases**, and then right-click the database that you want to shrink.</span></span>  
  
3.  <span data-ttu-id="6ba9f-134">**[タスク]** 、 **[圧縮]** の順にポイントし、 **[データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-134">Point to **Tasks**, point to **Shrink**, and then click **Database**.</span></span>  
  
     <span data-ttu-id="6ba9f-135">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="6ba9f-135">**Database**</span></span>  
     <span data-ttu-id="6ba9f-136">選択しているデータベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-136">Displays the name of the selected database.</span></span>  
  
     <span data-ttu-id="6ba9f-137">**[現在割り当てられている領域]**</span><span class="sxs-lookup"><span data-stu-id="6ba9f-137">**Current allocated space**</span></span>  
     <span data-ttu-id="6ba9f-138">選択されているデータベースの使用済み領域と未使用領域の合計を表示します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-138">Displays the total used and unused space for the selected database.</span></span>  
  
     <span data-ttu-id="6ba9f-139">**[使用可能な空き領域]**</span><span class="sxs-lookup"><span data-stu-id="6ba9f-139">**Available free space**</span></span>  
     <span data-ttu-id="6ba9f-140">選択されているデータベースのログ ファイルおよびデータ ファイル内の空き領域の合計を表示します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-140">Displays the sum of free space in the log and data files of the selected database.</span></span>  
  
     <span data-ttu-id="6ba9f-141">**[未使用領域の解放前にファイルを再構成する]**</span><span class="sxs-lookup"><span data-stu-id="6ba9f-141">**Reorganize files before releasing unused space**</span></span>  
     <span data-ttu-id="6ba9f-142">このオプションをオンにすることは、目的のパーセント オプションを指定して DBCC SHRINKDATABASE を実行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-142">Selecting this option is equivalent to executing DBCC SHRINKDATABASE specifying a target percent option.</span></span> <span data-ttu-id="6ba9f-143">このオプションをオフにすると、TRUNCATEONLY オプションを使用して DBCC SHRINKDATABASE を実行するのと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-143">Clearing this option is equivalent to executing DBCC SHRINKDATABASE with TRUNCATEONLY option.</span></span> <span data-ttu-id="6ba9f-144">既定では、ダイアログが開いたときに、このオプションはオフに設定されます。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-144">By default, this option is not selected when the dialog is opened.</span></span> <span data-ttu-id="6ba9f-145">このオプションをオンにした場合、ユーザーは目的のパーセント オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-145">If this option is selected, the user must specify a target percent option.</span></span>  
  
     <span data-ttu-id="6ba9f-146">**[圧縮後のファイルの最大空き領域]**</span><span class="sxs-lookup"><span data-stu-id="6ba9f-146">**Maximum free space in files after shrinking**</span></span>  
     <span data-ttu-id="6ba9f-147">データベースを圧縮した後に、データベース ファイル内に残す空き領域の最大パーセンテージを入力します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-147">Enter the maximum percentage of free space to be left in the database files after the database has been shrunk.</span></span> <span data-ttu-id="6ba9f-148">0 ～ 99 の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-148">Permissible values are between 0 and 99.</span></span>  
  
4.  <span data-ttu-id="6ba9f-149">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-149">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6ba9f-150">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6ba9f-150">Using Transact-SQL</span></span>  
  
#### <a name="to-shrink-a-database"></a><span data-ttu-id="6ba9f-151">データベースを圧縮するには</span><span class="sxs-lookup"><span data-stu-id="6ba9f-151">To shrink a database</span></span>  
  
1.  <span data-ttu-id="6ba9f-152">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6ba9f-153">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6ba9f-154">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-154">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6ba9f-155">この例では、 [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) を使用して、 `UserDB` データベース内のデータ ファイルとログ ファイルのサイズを圧縮し、データベースの空き領域が `10` % になるようにします。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-155">This example uses [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) to decreases the size of the data and log files in the `UserDB` database and to allow for `10` percent free space in the database.</span></span>  
  
 [!code-sql[DBCC#DBCC_SHRINKDB1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkdb1)]  
  
##  <a name="follow-up-after-you-shrink-a-database"></a><a name="FollowUp"></a><span data-ttu-id="6ba9f-156">補足情報: データベースを圧縮した後</span><span class="sxs-lookup"><span data-stu-id="6ba9f-156">Follow Up: After you shrink a database</span></span>  
 <span data-ttu-id="6ba9f-157">ファイルを圧縮するために移動されたデータは、ファイル内のあらゆる使用可能な場所に分散される場合があります。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-157">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="6ba9f-158">これにより、インデックスの断片化が発生し、広範なインデックスを検索するクエリのパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-158">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="6ba9f-159">断片化を解消するには、圧縮後にファイルのインデックスを再構築することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="6ba9f-159">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba9f-160">参照</span><span class="sxs-lookup"><span data-stu-id="6ba9f-160">See Also</span></span>  
 <span data-ttu-id="6ba9f-161">[ファイルの圧縮](shrink-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="6ba9f-161">[Shrink a File](shrink-a-file.md) </span></span>  
 <span data-ttu-id="6ba9f-162">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6ba9f-162">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="6ba9f-163">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6ba9f-163">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="6ba9f-164">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6ba9f-164">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span></span>  
 <span data-ttu-id="6ba9f-165">[DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6ba9f-165">[DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) </span></span>  
 [<span data-ttu-id="6ba9f-166">データベース ファイルとファイル グループ</span><span class="sxs-lookup"><span data-stu-id="6ba9f-166">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
