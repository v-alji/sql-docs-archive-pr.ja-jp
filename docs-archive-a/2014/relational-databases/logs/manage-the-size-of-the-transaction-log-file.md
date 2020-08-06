---
title: トランザクション ログ ファイルのサイズの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], size management
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 219ba0605d60bab0b13675f7f9f7ff01cace5755
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639498"
---
# <a name="manage-the-size-of-the-transaction-log-file"></a><span data-ttu-id="1739f-102">トランザクション ログ ファイルのサイズの管理</span><span class="sxs-lookup"><span data-stu-id="1739f-102">Manage the Size of the Transaction Log File</span></span>
  <span data-ttu-id="1739f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのトランザクション ログは、必要に応じて、その物理ログ ファイルを物理的に圧縮または展開することができます。</span><span class="sxs-lookup"><span data-stu-id="1739f-103">In some cases, it can be useful to physically shrink or expand the physical log file of the transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="1739f-104">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のトランザクション ログ サイズの監視、トランザクション ログの圧縮、トランザクション ログ ファイルの追加と拡大、 **tempdb** トランザクション ログ増加率の最適化、トランザクション ログ ファイルのサイズ拡大の管理の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1739f-104">This topic contains information about how to monitor the size of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction log, shrink the transaction log, add or enlarge a transaction log file, optimize the **tempdb** transaction log growth rate, and control the growth of a transaction log file.</span></span>  
  
  
##  <a name="monitor-log-space-use"></a><a name="MonitorSpaceUse"></a><span data-ttu-id="1739f-105">ログ領域の使用量の監視</span><span class="sxs-lookup"><span data-stu-id="1739f-105">Monitor Log Space Use</span></span>  
 <span data-ttu-id="1739f-106">ログ領域の使用量は、DBCC SQLPERF (LOGSPACE) を使用して監視することができます。</span><span class="sxs-lookup"><span data-stu-id="1739f-106">You can monitor log space use by using DBCC SQLPERF (LOGSPACE).</span></span> <span data-ttu-id="1739f-107">このコマンドは、現在使用されているログ領域の量に関する情報を返し、いつトランザクション ログを切り捨てる必要があるかを示します。</span><span class="sxs-lookup"><span data-stu-id="1739f-107">This command returns information about the amount of log space currently used and indicates when the transaction log is in need of truncation.</span></span> <span data-ttu-id="1739f-108">詳細については、「 [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1739f-108">For more information, see [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql).</span></span> <span data-ttu-id="1739f-109">ログ ファイルの現在のサイズ、最大サイズ、およびファイルの自動拡張オプションについては、**sys.database_files** にある、そのログ ファイルに関する **size**、**max_size**、**growth** の各列も使用できます。</span><span class="sxs-lookup"><span data-stu-id="1739f-109">For information about the current size of a log file, its maximum size, and the autogrow option for the file, you can also use the **size**, **max_size**, and **growth** columns for that log file in **sys.database_files**.</span></span> <span data-ttu-id="1739f-110">詳細については、「[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1739f-110">For more information, see [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1739f-111">ログ ディスクが過負荷にならないようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1739f-111">We recommend that you avoid overloading the log disk.</span></span>  
  
  
##  <a name="shrink-the-size-of-the-log-file"></a><a name="ShrinkSize"></a><span data-ttu-id="1739f-112">ログファイルのサイズを縮小する</span><span class="sxs-lookup"><span data-stu-id="1739f-112">Shrink the Size of the Log File</span></span>  
 <span data-ttu-id="1739f-113">物理ログ ファイルの物理サイズを削減するには、ログ ファイルを圧縮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1739f-113">To reduce the physical size of a physical log file, you must shrink the log file.</span></span> <span data-ttu-id="1739f-114">トランザクション ログ ファイルに不要な未使用領域が含まれていることがわかっている場合にはこの方法が有効です。</span><span class="sxs-lookup"><span data-stu-id="1739f-114">This is useful if you know that a transaction log file contains unused space that you will not be needing.</span></span> <span data-ttu-id="1739f-115">ログ ファイルの圧縮を実行できるのは、データベースがオンラインで、1 つ以上の仮想ログ ファイルが解放されている間だけです。</span><span class="sxs-lookup"><span data-stu-id="1739f-115">Shrinking a log file can occur only while the database is online and, also, at least one virtual log file is free.</span></span> <span data-ttu-id="1739f-116">場合によっては、次のログの切り捨てまでログを圧縮できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="1739f-116">In some cases, shrinking the log may not be possible until after the next log truncation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1739f-117">実行時間の長いトランザクションなど、長期間にわたって仮想ログ ファイルがアクティブなままになる要因があると、ログの圧縮が制限されたり、ログがまったく圧縮できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="1739f-117">Factors, such as a long-running transaction, that keep virtual log files active for an extended period can restrict log shrinkage or even prevent the log from shrinking at all.</span></span> <span data-ttu-id="1739f-118">ログの切り捨てが遅れる要因については、「[トランザクション ログ &#40;SQL Server&#41;](the-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1739f-118">For information about factors that can delay log truncation, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="1739f-119">ログ ファイルを圧縮すると、論理ログのどの部分も保持しない 1 つまたは複数の仮想ログ ファイル (つまり、 *非アクティブな仮想ログ ファイル*) が削除されます。</span><span class="sxs-lookup"><span data-stu-id="1739f-119">Shrinking a log file removes one or more virtual log files that do not hold any part of the logical log (that is, *inactive virtual log files*).</span></span> <span data-ttu-id="1739f-120">トランザクション ログ ファイルを圧縮すると、ログ ファイルが目的のサイズにできるだけ近いサイズに縮小されるように、非アクティブな仮想ログ ファイルがログ ファイルの末尾から削除されます。</span><span class="sxs-lookup"><span data-stu-id="1739f-120">When a transaction log file is shrunk, enough inactive virtual log files are removed from the end of the log file to reduce the log to approximately the target size.</span></span>  
  
 <span data-ttu-id="1739f-121">**データベース ファイルを圧縮せずにログ ファイルを圧縮するには**</span><span class="sxs-lookup"><span data-stu-id="1739f-121">**To shrink a log file (without shrinking database files)**</span></span>  
  
-   [<span data-ttu-id="1739f-122">DBCC SHRINKFILE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1739f-122">DBCC SHRINKFILE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql)  
  
-   [<span data-ttu-id="1739f-123">ファイルの圧縮</span><span class="sxs-lookup"><span data-stu-id="1739f-123">Shrink a File</span></span>](../databases/shrink-a-file.md)  
  
 <span data-ttu-id="1739f-124">**ログ ファイルの圧縮イベントを監視するには**</span><span class="sxs-lookup"><span data-stu-id="1739f-124">**To monitor log-file shrink events**</span></span>  
  
-   <span data-ttu-id="1739f-125">[Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="1739f-125">[Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md).</span></span>  
  
 `To monitor log space`  
  
-   [<span data-ttu-id="1739f-126">DBCC SQLPERF &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1739f-126">DBCC SQLPERF &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)  
  
-   <span data-ttu-id="1739f-127">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) (ログ ファイルまたはファイルの **size**、**max_size**、**growth** 列を参照してください。)</span><span class="sxs-lookup"><span data-stu-id="1739f-127">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) (See the **size**, **max_size**, and **growth** columns for the log file or files.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1739f-128">データベースおよびログ ファイルの圧縮は、自動的に行われるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="1739f-128">Shrinking database and log files can be set to occur automatically.</span></span> <span data-ttu-id="1739f-129">ただし、自動圧縮は推奨されず、`autoshrink` データベース プロパティは既定で FALSE に設定されています。</span><span class="sxs-lookup"><span data-stu-id="1739f-129">However, we recommend against automatic shrinking, and the `autoshrink` database property is set to FALSE by default.</span></span> <span data-ttu-id="1739f-130">`autoshrink` を TRUE に設定すると、ファイル領域の 25% を超える領域が未使用の場合にのみ、自動圧縮によってファイルのサイズが縮小されます。</span><span class="sxs-lookup"><span data-stu-id="1739f-130">If `autoshrink` is set to TRUE, automatic shrinking reduces the size of a file only when more than 25 percent of its space is unused.</span></span> <span data-ttu-id="1739f-131">ファイルは、ファイル領域の 25% のみが未使用領域になるサイズ、またはファイルの元のサイズの、どちらか大きい方のサイズまで圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="1739f-131">The file is shrunk either to the size at which only 25 percent of the file is unused space or to the original size of the file, whichever is larger.</span></span> <span data-ttu-id="1739f-132">プロパティの設定を変更する方法の詳細については `autoshrink` 、「[データベースのプロパティを表示または変更](../databases/view-or-change-the-properties-of-a-database.md)する」を参照してください。または、[**オプション**] ページで**自動圧縮**プロパティを使用するか、 [transact-sql&#41;&#40;ALTER Database SET オプション](/sql/t-sql/statements/alter-database-transact-sql-set-options)を使用して AUTO_SHRINK オプションを使用してください。</span><span class="sxs-lookup"><span data-stu-id="1739f-132">For information about changing the setting of the `autoshrink` property, see [View or Change the Properties of a Database](../databases/view-or-change-the-properties-of-a-database.md)-use the **Auto Shrink** property on the **Options** page-or [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-use the AUTO_SHRINK option.</span></span>  
  
  
##  <a name="add-or-enlarge-a-log-file"></a><a name="AddOrEnlarge"></a><span data-ttu-id="1739f-133">ログファイルを追加または拡大する</span><span class="sxs-lookup"><span data-stu-id="1739f-133">Add or Enlarge a Log File</span></span>  
 <span data-ttu-id="1739f-134">既存のログ ファイルを拡大するか (ディスク領域が十分にある場合)、別のディスク上にあるデータベースにログ ファイルを追加することによって、領域を確保することもできます。</span><span class="sxs-lookup"><span data-stu-id="1739f-134">Alternatively, you can gain space by enlarging the existing log file (if disk space permits) or by adding a log file to the database, typically on a different disk.</span></span>  
  
-   <span data-ttu-id="1739f-135">データベースにログ ファイルを追加するには、ALTER DATABASE ステートメントの ADD LOG FILE 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="1739f-135">To add a log file to the database, use the ADD LOG FILE clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="1739f-136">ログ ファイルを追加すると、ログを大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="1739f-136">Adding a log file allows the log to grow.</span></span>  
  
-   <span data-ttu-id="1739f-137">ログ ファイルを拡大するには、ALTER DATABASE ステートメントの MODIFY FILE 句を使用し、SIZE および MAXSIZE 構文を指定します。</span><span class="sxs-lookup"><span data-stu-id="1739f-137">To enlarge the log file, use the MODIFY FILE clause of the ALTER DATABASE statement, specifying the SIZE and MAXSIZE syntax.</span></span> <span data-ttu-id="1739f-138">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1739f-138">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
  
##  <a name="optimize-the-size-of-the-tempdb-transaction-log"></a><a name="tempdbOptimize"></a><span data-ttu-id="1739f-139">Tempdb トランザクションログのサイズを最適化する</span><span class="sxs-lookup"><span data-stu-id="1739f-139">Optimize the Size of the tempdb Transaction Log</span></span>  
 <span data-ttu-id="1739f-140">サーバー インスタンスを再起動すると、 **tempdb** データベースのトランザクション ログのサイズが、元の自動拡張前のサイズに変更されます。</span><span class="sxs-lookup"><span data-stu-id="1739f-140">Restarting a server instance resizes the transaction log of the **tempdb** database to its original, pre-autogrow size.</span></span> <span data-ttu-id="1739f-141">これにより、 **tempdb** のトランザクション ログのパフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="1739f-141">This can reduce the performance of the **tempdb** transaction log.</span></span> <span data-ttu-id="1739f-142">このオーバーヘッドは、サーバー インスタンスを起動または再起動した後、 **tempdb** のトランザクション ログのサイズを増やすことで回避できます。</span><span class="sxs-lookup"><span data-stu-id="1739f-142">You can avoid this overhead by increasing the size of the **tempdb** transaction log after starting or restarting the server instance.</span></span> <span data-ttu-id="1739f-143">詳細については、「 [tempdb Database](../databases/tempdb-database.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1739f-143">For more information, see [tempdb Database](../databases/tempdb-database.md).</span></span>  
  
  
##  <a name="control-the-growth-of-a-transaction-log-file"></a><a name="ControlGrowth"></a><span data-ttu-id="1739f-144">トランザクションログファイルの拡張を制御する</span><span class="sxs-lookup"><span data-stu-id="1739f-144">Control the Growth of a Transaction Log File</span></span>  
 <span data-ttu-id="1739f-145">トランザクション ログ ファイルのサイズの拡張を管理するには、[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1739f-145">You can use the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement to manage the growth of a transaction log file.</span></span> <span data-ttu-id="1739f-146">次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="1739f-146">Note the following:</span></span>  
  
-   <span data-ttu-id="1739f-147">現在のサイズを KB、MB、GB、および TB 単位で変更する場合は、SIZE オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="1739f-147">To change the current file size in KB, MB, GB, and TB units, use the SIZE option.</span></span>  
  
-   <span data-ttu-id="1739f-148">拡張増分値で変更するには、FILEGROWTH オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="1739f-148">To change the growth increment, use the FILEGROWTH option.</span></span> <span data-ttu-id="1739f-149">0 は、自動拡張がオフで、領域を追加できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1739f-149">A value of 0 indicates that automatic growth is set to off and no additional space is permitted.</span></span> <span data-ttu-id="1739f-150">ログ ファイルの自動拡張の増分値が小さい場合も、パフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="1739f-150">A small autogrowth increment on a log file can reduce performance.</span></span> <span data-ttu-id="1739f-151">ログ ファイルの拡張増分値は、拡張を頻繁に行わなくても済むように十分な大きさにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1739f-151">The file growth increment on a log file should be sufficiently large to avoid frequent expansion.</span></span> <span data-ttu-id="1739f-152">通常は、既定の拡張増分値 (10%) が適しています。</span><span class="sxs-lookup"><span data-stu-id="1739f-152">The default growth increment of 10 percent is generally suitable.</span></span>  
  
     <span data-ttu-id="1739f-153">ログファイルのファイル拡張プロパティを変更する方法の詳細については、「 [ALTER DATABASE &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1739f-153">For information on changing the file-growth property on a log file, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="1739f-154">ログ ファイルの最大サイズを KB、MB、GB、および TB 単位で制御するか、拡張値を UNLIMITED に設定するには、MAXSIZE オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="1739f-154">To control the maximum the size of a log file in KB, MB, GB, and TB units or to set growth to UNLIMITED, use the MAXSIZE option.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="1739f-155">参照</span><span class="sxs-lookup"><span data-stu-id="1739f-155">See Also</span></span>  
 <span data-ttu-id="1739f-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1739f-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="1739f-157">満杯になったトランザクション ログのトラブルシューティング &#40;SQL Server エラー 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="1739f-157">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  
