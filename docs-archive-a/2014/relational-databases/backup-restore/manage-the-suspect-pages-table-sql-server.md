---
title: suspect_pages テーブルの管理 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
- restoring pages [SQL Server]
- pages [SQL Server], suspect
- pages [SQL Server], restoring
- suspect_pages system table
- suspect pages [SQL Server]
- restoring [SQL Server], pages
ms.assetid: f394d4bc-1518-4e61-97fc-bf184d972e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dd7aea63ae85a16e23ff532c7e18ace3c376a707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645672"
---
# <a name="manage-the-suspect_pages-table-sql-server"></a><span data-ttu-id="3d2fe-102">suspect_pages テーブルの管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3d2fe-102">Manage the suspect_pages Table (SQL Server)</span></span>
  <span data-ttu-id="3d2fe-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] suspect_pages [!INCLUDE[tsql](../../includes/tsql-md.md)]テーブルを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-103">This topic describes how to manage the **suspect_pages** table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3d2fe-104">**suspect_pages** テーブルは、問題があると考えられるページに関する情報を保持するためのテーブルであり、復元が必要かどうかを判断する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-104">The **suspect_pages** table is used for maintaining information about suspect pages, and is relevant in helping to decide whether a restore is necessary.</span></span> <span data-ttu-id="3d2fe-105">[suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) テーブルは、 [msdb データベース](../databases/msdb-database.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-105">The [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table resides in the [msdb database](../databases/msdb-database.md).</span></span>  
  
 <span data-ttu-id="3d2fe-106">[!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] がデータ ページの読み取りを試みたときに次のエラーのいずれかを検出すると、ページは "問題あり" と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-106">A page is considered "suspect" when the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] encounters one of the following errors when it tries to read a data page:</span></span>  
  
-   <span data-ttu-id="3d2fe-107">ディスクエラー (特定のハードウェアエラー) など、オペレーティングシステムによって発行された巡回冗長検査 (CRC) によって発生した[823 エラー](../errors-events/mssqlserver-823-database-engine-error.md)</span><span class="sxs-lookup"><span data-stu-id="3d2fe-107">An [823 error](../errors-events/mssqlserver-823-database-engine-error.md) that was caused by a cyclic redundancy check (CRC) issued by the operating system, such as a disk error (certain hardware errors)</span></span>  
  
-   <span data-ttu-id="3d2fe-108">[824 エラー](../errors-events/mssqlserver-824-database-engine-error.md)(破損ページ (すべての論理エラー) など)</span><span class="sxs-lookup"><span data-stu-id="3d2fe-108">An [824 error](../errors-events/mssqlserver-824-database-engine-error.md), such as a torn page (any logical error)</span></span>  
  
 <span data-ttu-id="3d2fe-109">問題があると考えられるすべてのページのページ ID が **suspect_pages** テーブルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-109">The page ID of every suspect page is recorded in the **suspect_pages** table.</span></span> <span data-ttu-id="3d2fe-110">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、次のような通常の処理中に検出された問題のあるページを記録します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-110">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] records any suspect pages encountered during regular processing, such as the following:</span></span>  
  
-   <span data-ttu-id="3d2fe-111">クエリがページを読み取る必要があるとき</span><span class="sxs-lookup"><span data-stu-id="3d2fe-111">A query has to read a page.</span></span>  
  
-   <span data-ttu-id="3d2fe-112">DBCC CHECKDB 操作の実行中</span><span class="sxs-lookup"><span data-stu-id="3d2fe-112">During a DBCC CHECKDB operation.</span></span>  
  
-   <span data-ttu-id="3d2fe-113">バックアップ操作の実行中</span><span class="sxs-lookup"><span data-stu-id="3d2fe-113">During a backup operation.</span></span>  
  
 <span data-ttu-id="3d2fe-114">**suspect_pages** テーブルは、復元操作、DBCC 修復操作、データベースの削除操作などの実行中にも必要に応じて更新されます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-114">The **suspect_pages** table is also updated as necessary during a restore operation, a DBCC repair operation, or a drop database operation.</span></span>  
  
 <span data-ttu-id="3d2fe-115">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="3d2fe-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3d2fe-116">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3d2fe-116">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3d2fe-117">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="3d2fe-117">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="3d2fe-118">Security</span><span class="sxs-lookup"><span data-stu-id="3d2fe-118">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3d2fe-119">**suspect_pages テーブルを管理する方法:**</span><span class="sxs-lookup"><span data-stu-id="3d2fe-119">**To manage the suspect_pages table, using:**</span></span>  
  
     [<span data-ttu-id="3d2fe-120">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3d2fe-120">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3d2fe-121">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3d2fe-121">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3d2fe-122">はじめに</span><span class="sxs-lookup"><span data-stu-id="3d2fe-122">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="3d2fe-123">推奨事項</span><span class="sxs-lookup"><span data-stu-id="3d2fe-123">Recommendations</span></span>  
  
-   <span data-ttu-id="3d2fe-124">**suspect_pages テーブルに記録されるエラー**</span><span class="sxs-lookup"><span data-stu-id="3d2fe-124">**Errors Recorded in suspect_pages Table**</span></span>  
  
     <span data-ttu-id="3d2fe-125">**suspect_pages** テーブルには、824 エラーにより失敗したページごとに 1 行ずつ、上限を 1,000 行として格納されます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-125">The **suspect_pages** table contains one row per page that failed with an 824 error, up to a limit of 1,000 rows.</span></span> <span data-ttu-id="3d2fe-126">次の表に、 **suspect_pages** テーブルの **event_type** 列にログ記録されるエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-126">The following table shows errors logged in the **event_type** column of the **suspect_pages** table.</span></span>  
  
    |<span data-ttu-id="3d2fe-127">エラーの説明</span><span class="sxs-lookup"><span data-stu-id="3d2fe-127">Error description</span></span>|<span data-ttu-id="3d2fe-128">**event_type** 値</span><span class="sxs-lookup"><span data-stu-id="3d2fe-128">**event_type** value</span></span>|  
    |-----------------------|---------------------------|  
    |<span data-ttu-id="3d2fe-129">オペレーティング システムの CRC エラーによって発生した 823 エラー、または、不適切なチェックサムまたは破損ページ (不適切なページ ID) 以外の 824 エラー</span><span class="sxs-lookup"><span data-stu-id="3d2fe-129">823 error caused by an operating system CRC error  or 824 error other than a bad checksum or a torn page (for example, a bad page ID)</span></span>|<span data-ttu-id="3d2fe-130">1</span><span class="sxs-lookup"><span data-stu-id="3d2fe-130">1</span></span>|  
    |<span data-ttu-id="3d2fe-131">不適切なチェックサム</span><span class="sxs-lookup"><span data-stu-id="3d2fe-131">Bad checksum</span></span>|<span data-ttu-id="3d2fe-132">2</span><span class="sxs-lookup"><span data-stu-id="3d2fe-132">2</span></span>|  
    |<span data-ttu-id="3d2fe-133">正しくないページ</span><span class="sxs-lookup"><span data-stu-id="3d2fe-133">Torn page</span></span>|<span data-ttu-id="3d2fe-134">3</span><span class="sxs-lookup"><span data-stu-id="3d2fe-134">3</span></span>|  
    |<span data-ttu-id="3d2fe-135">復元済み (ページは不適切と見なされた後で復元されました)</span><span class="sxs-lookup"><span data-stu-id="3d2fe-135">Restored (The page was restored after it was marked bad)</span></span>|<span data-ttu-id="3d2fe-136">4</span><span class="sxs-lookup"><span data-stu-id="3d2fe-136">4</span></span>|  
    |<span data-ttu-id="3d2fe-137">修復済み (DBCC、AlwaysOn、またはミラーリングで修復されたページ)</span><span class="sxs-lookup"><span data-stu-id="3d2fe-137">Repaired (DBCC, AlwaysOn, or mirroring repaired the page)</span></span>|<span data-ttu-id="3d2fe-138">5</span><span class="sxs-lookup"><span data-stu-id="3d2fe-138">5</span></span>|  
    |<span data-ttu-id="3d2fe-139">DBCC による割り当て解除</span><span class="sxs-lookup"><span data-stu-id="3d2fe-139">Deallocated by DBCC</span></span>|<span data-ttu-id="3d2fe-140">7</span><span class="sxs-lookup"><span data-stu-id="3d2fe-140">7</span></span>|  
  
     <span data-ttu-id="3d2fe-141">**suspect_pages** テーブルには、一時的なエラーも記録されます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-141">The **suspect_pages** table also records transient errors.</span></span> <span data-ttu-id="3d2fe-142">一時的なエラーの原因としては、I/O エラー (たとえば、ケーブルが取りはずされた場合) や、反復的なチェックサム テストで一時的にエラーになったページなどがあります。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-142">Sources of transient errors include an I/O error (for example, a cable was disconnected) or a page that temporarily fails a repeated checksum test.</span></span>  
  
-   <span data-ttu-id="3d2fe-143">**データベース エンジンによる suspect_pages テーブルの更新方法**</span><span class="sxs-lookup"><span data-stu-id="3d2fe-143">**How the Database Engine Updates the suspect_pages Table**</span></span>  
  
     <span data-ttu-id="3d2fe-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、 **suspect_pages** テーブルに対して次のアクションを行います。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-144">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] takes the following actions on the **suspect_pages** table:</span></span>  
  
    -   <span data-ttu-id="3d2fe-145">テーブルに空き容量がある場合は、エラーの発生を示す 824 エラーをすべて記録し、エラー カウンターの値を増やします。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-145">If the table is not full, it is updated for every 824 error, to indicate that an error has occurred, and the error counter is incremented.</span></span> <span data-ttu-id="3d2fe-146">修復、復元、または割り当て解除による修正の後に、ページにエラーがある場合は、 **number_of_errors** カウントの値を増やし、 **last_update** 列を更新します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-146">If a page has an error after it is fixed by being repaired, restored, or deallocated, its **number_of_errors** count is incremented and its **last_update** column is updated</span></span>  
  
    -   <span data-ttu-id="3d2fe-147">リストされているページが復元や修復操作によって修正された場合は、そのページが修復 ( **event_type** = 5) または復元 (**event_type** = 4) されたことを示すために**suspect_pages** の行を更新します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-147">After a listed page is fixed by a restore or a repair operation, the operation updates the **suspect_pages** row to indicate that the page is repaired (**event_type** = 5) or restored (**event_type** = 4).</span></span>  
  
    -   <span data-ttu-id="3d2fe-148">DBCC チェックを実行すると、エラーのないページは修復済み (**event_type** = 5) または割り当て解除済み (**event_type** = 7) としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-148">If a DBCC check is run, the check marks any error-free pages as repaired (**event_type** = 5) or deallocated (**event_type** = 7).</span></span>  
  
-   <span data-ttu-id="3d2fe-149">**suspect_pages テーブルに対する自動更新**</span><span class="sxs-lookup"><span data-stu-id="3d2fe-149">**Automatic Updates to the suspect_pages Table**</span></span>  
  
     <span data-ttu-id="3d2fe-150">次のいずれかの理由によりデータ ファイルのページの読み取りに失敗すると、データベース ミラーリング パートナーまたは AlwaysOn 可用性レプリカは **suspect_pages** テーブルを更新します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-150">A database mirroring partner or AlwaysOn availability replica updates the **suspect_pages** table after an attempt to read a page from a data file fails for one of the following reasons.</span></span>  
  
    -   <span data-ttu-id="3d2fe-151">オペレーティング システムの CRC エラーによって発生した 823 エラー</span><span class="sxs-lookup"><span data-stu-id="3d2fe-151">An 823 error that is caused by an operating system CRC error.</span></span>  
  
    -   <span data-ttu-id="3d2fe-152">824 エラー (破損ページなどの論理破損)</span><span class="sxs-lookup"><span data-stu-id="3d2fe-152">An 824 error (logical corruption such as a torn page).</span></span>  
  
     <span data-ttu-id="3d2fe-153">次に示す操作を行うと、 **suspect_pages** テーブルの行も自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-153">The following actions also automatically update rows in the **suspect_pages** table.</span></span>  
  
    -   <span data-ttu-id="3d2fe-154">DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS を実行すると、割り当て解除または修復を行った各ページを示すために、 **suspect_pages** テーブルが更新されます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-154">DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS updates the **suspect_pages** table to indicate each page that it has deallocated or repaired.</span></span>  
  
    -   <span data-ttu-id="3d2fe-155">完全復元、ファイル復元、またはページ復元を行うと、復元されたページのエントリが復元済みとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-155">A full, file, or page RESTORE marks the page entries as restored.</span></span>  
  
     <span data-ttu-id="3d2fe-156">次に示す操作を行うと、 **suspect_pages** テーブルの行が自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-156">The following actions automatically delete rows from the **suspect_pages** table.</span></span>  
  
    -   <span data-ttu-id="3d2fe-157">ALTER DATABASE REMOVE FILE。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-157">ALTER DATABASE REMOVE FILE</span></span>  
  
    -   <span data-ttu-id="3d2fe-158">DROP DATABASE</span><span class="sxs-lookup"><span data-stu-id="3d2fe-158">DROP DATABASE</span></span>  
  
-   <span data-ttu-id="3d2fe-159">**データベース管理者が担う管理の役割**</span><span class="sxs-lookup"><span data-stu-id="3d2fe-159">**Maintenance Role of the Database Administrator**</span></span>  
  
     <span data-ttu-id="3d2fe-160">suspect_pages テーブルの管理は、主に古い行を削除することで、データベース管理者が行います。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-160">Database administrators are responsible for managing the table, primarily by deleting old rows.</span></span> <span data-ttu-id="3d2fe-161">**suspect_pages** テーブルのサイズには制限があり、このテーブルに空き領域がなくなると新しいエラーはログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-161">The **suspect_pages** table is limited in size, and if it fills, new errors are not logged.</span></span> <span data-ttu-id="3d2fe-162">このテーブルがいっぱいになるのを防ぐには、データベース管理者またはシステム管理者が、手動でこのテーブルから行を削除することによって古いエントリを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-162">To prevent this table from filling up, the database administrator or system administrator must manually clear out old entries from this table by deleting rows.</span></span> <span data-ttu-id="3d2fe-163">そのため、復元済みまたは修復済みの **event_type** を含む行や、古い **last_update** 値を含む行を、定期的に削除またはアーカイブすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-163">Therefore, we recommend that you periodically delete or archive rows that have an **event_type** of restored or repaired, or rows that have an old **last_update** value.</span></span>  
  
     <span data-ttu-id="3d2fe-164">suspect_pages テーブルの処理を監視するには、 [Database Suspect Data Page イベント クラス](../event-classes/database-suspect-data-page-event-class.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-164">To monitor the activity on the suspect_pages table, you can use the [Database Suspect Data Page Event Class](../event-classes/database-suspect-data-page-event-class.md).</span></span> <span data-ttu-id="3d2fe-165">一時的なエラーが原因で、 **suspect_pages** テーブルに行が追加されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-165">Rows are sometimes added to the **suspect_pages** table because of transient errors.</span></span> <span data-ttu-id="3d2fe-166">このテーブルに多数の行が追加されている場合、I/O サブシステムに問題がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-166">If many rows are being added to the table, however, a problem probably exists with the I/O subsystem.</span></span> <span data-ttu-id="3d2fe-167">テーブルに追加されている行数が急激に増加している場合は、I/O サブシステムの考えられる問題を調査することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-167">If you notice a sudden increase in the number of rows being added to the table, we recommend that you investigate possible problems in your I/O subsystem.</span></span>  
  
     <span data-ttu-id="3d2fe-168">データベース管理者は、レコードの挿入や更新も行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-168">A database administrator can also insert or update records.</span></span> <span data-ttu-id="3d2fe-169">たとえば、問題のあるページが実際には一貫性の取れている状態であることが確かであっても、しばらくレコードを残しておきたい場合に、行を更新できると便利です。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-169">For example, updating a row might useful when the database administrator knows that a particular suspect page is actually intact, but wants to preserve the record for a while.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3d2fe-170">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3d2fe-170">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3d2fe-171">Permissions</span><span class="sxs-lookup"><span data-stu-id="3d2fe-171">Permissions</span></span>  
 <span data-ttu-id="3d2fe-172">**msdb** に対するアクセスを持つユーザー は、 **suspect_pages** テーブルのデータを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-172">Anyone with access to **msdb** can read the data in the **suspect_pages** table.</span></span> <span data-ttu-id="3d2fe-173">suspect_pages テーブルに対する UPDATE 権限を持つすべてのユーザーは、そのレコードを更新できます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-173">Anyone with UPDATE permission on the suspect_pages table can update its records.</span></span> <span data-ttu-id="3d2fe-174">**msdb** の **db_owner** 固定データベース ロールのメンバーまたは **sysadmin** 固定サーバー ロールのメンバーは、レコードの挿入、更新、および削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-174">Members the **db_owner** fixed database role on **msdb** or the **sysadmin** fixed server role can insert, update, and delete records.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3d2fe-175">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3d2fe-175">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-manage-the-suspect_pages-table"></a><span data-ttu-id="3d2fe-176">suspect_pages テーブルを管理するには</span><span class="sxs-lookup"><span data-stu-id="3d2fe-176">To manage the suspect_pages table</span></span>  
  
1.  <span data-ttu-id="3d2fe-177">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]のインスタンスに接続して、そのインスタンスを展開します。次に、 **[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-177">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="3d2fe-178">**[システム データベース]** 、 **[msdb]** 、 **[テーブル]** 、 **[システム テーブル]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-178">Expand **System Databases**, expand **msdb**, expand **Tables**, and then expand **System Tables**.</span></span>  
  
3.  <span data-ttu-id="3d2fe-179">**[dbo.suspect_pages]** を展開し、 **[上位 200 行の編集]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-179">Expand **dbo.suspect_pages** and right-click **Edit Top 200 Rows**.</span></span>  
  
4.  <span data-ttu-id="3d2fe-180">クエリ ウィンドウで、目的の行を編集、更新、または削除します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-180">In the query window, edit, update, or delete the rows that you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3d2fe-181">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3d2fe-181">Using Transact-SQL</span></span>  
  
#### <a name="to-manage-the-suspect_pages-table"></a><span data-ttu-id="3d2fe-182">suspect_pages テーブルを管理するには</span><span class="sxs-lookup"><span data-stu-id="3d2fe-182">To manage the suspect_pages table</span></span>  
  
1.  <span data-ttu-id="3d2fe-183">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-183">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3d2fe-184">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-184">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3d2fe-185">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-185">Copy and paste the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="3d2fe-186">次の例は、 `suspect_pages` テーブルからいくつかの行を削除します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-186">This example deletes some of the rows from the `suspect_pages` table.</span></span>  
  
```  
-- Delete restored, repaired, or deallocated pages.  
DELETE FROM msdb..suspect_pages  
   WHERE (event_type = 4 OR event_type = 5 OR event_type = 7);  
GO  
  
```  
  
 <span data-ttu-id="3d2fe-187">次の例は、 `suspect_pages` テーブル内の不適切なページを返します。</span><span class="sxs-lookup"><span data-stu-id="3d2fe-187">This example returns the bad pages in the `suspect_pages` table.</span></span>  
  
```  
-- Select nonspecific 824, bad checksum, and torn page errors.  
SELECT * FROM msdb..suspect_pages  
   WHERE (event_type = 1 OR event_type = 2 OR event_type = 3);  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d2fe-188">参照</span><span class="sxs-lookup"><span data-stu-id="3d2fe-188">See Also</span></span>  
 <span data-ttu-id="3d2fe-189">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3d2fe-189">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span></span>  
 <span data-ttu-id="3d2fe-190">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3d2fe-190">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="3d2fe-191">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3d2fe-191">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="3d2fe-192">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3d2fe-192">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span></span>  
 <span data-ttu-id="3d2fe-193">[ページ復元 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3d2fe-193">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="3d2fe-194">[suspect_pages &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3d2fe-194">[suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql) </span></span>  
 <span data-ttu-id="3d2fe-195">[MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="3d2fe-195">[MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md) </span></span>  
 [<span data-ttu-id="3d2fe-196">MSSQLSERVER_824</span><span class="sxs-lookup"><span data-stu-id="3d2fe-196">MSSQLSERVER_824</span></span>](../errors-events/mssqlserver-824-database-engine-error.md)  
  
  
