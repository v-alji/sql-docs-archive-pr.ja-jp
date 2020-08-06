---
title: ログ シーケンス番号への復旧 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4df55c3468fc009d86cffd58a837d6935f5ce14b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643435"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a><span data-ttu-id="688e8-102">ログ シーケンス番号への復旧 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="688e8-102">Recover to a Log Sequence Number (SQL Server)</span></span>
  <span data-ttu-id="688e8-103">このトピックは、完全復旧モデルまたは一括ログ復旧モデルを使用するデータベースのみに関連しています。</span><span class="sxs-lookup"><span data-stu-id="688e8-103">This topic is relevant only for databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="688e8-104">ログ シーケンス番号 (LSN) を使用して、復元操作の復旧ポイントを定義できます。</span><span class="sxs-lookup"><span data-stu-id="688e8-104">You can use a log sequence number (LSN) to define the recovery point for a restore operation.</span></span> <span data-ttu-id="688e8-105">ただし、この機能はツール ベンダーを対象としたものであり、一般的には、あまり有益ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="688e8-105">However, this is a specialized feature that is intended for tools vendors and is unlikely to be generally useful.</span></span>  
  
##  <a name="overview-of-log-sequence-numbers"></a><a name="LSNs"></a> <span data-ttu-id="688e8-106">ログ シーケンス番号の概要</span><span class="sxs-lookup"><span data-stu-id="688e8-106">Overview of Log Sequence Numbers</span></span>  
 <span data-ttu-id="688e8-107">LSN は、RESTORE シーケンス中に、データを復元する時点を追跡するために内部で使用されます。</span><span class="sxs-lookup"><span data-stu-id="688e8-107">LSNs are used internally during a RESTORE sequence to track the point in time to which data has been restored.</span></span> <span data-ttu-id="688e8-108">バックアップを復元するときに、データはバックアップが実行された時点に対応する LSN まで復元されます。</span><span class="sxs-lookup"><span data-stu-id="688e8-108">When a backup is restored, the data is restored to the LSN corresponding to the point in time at which the backup was taken.</span></span> <span data-ttu-id="688e8-109">差分バックアップとログ バックアップの場合、復元されるデータベースは LSN が大きい方、つまり、より後の時点に向かって進められます。</span><span class="sxs-lookup"><span data-stu-id="688e8-109">Differential and log backups advance the restored database to a later time, which corresponds to a higher LSN.</span></span>  
  
 <span data-ttu-id="688e8-110">トランザクション ログのすべてのレコードは、ログ シーケンス番号 (LSN) によって一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="688e8-110">Every record in the transaction log is uniquely identified by a log sequence number (LSN).</span></span> <span data-ttu-id="688e8-111">LSN の順序は、LSN2 が LSN1 より大きい場合、LSN2 によって参照されるログ レコードで示される変更が、ログ レコード LSN1 で示される変更の後に行われたようになっています。</span><span class="sxs-lookup"><span data-stu-id="688e8-111">LSNs are ordered such that if LSN2 is greater than LSN1, the change described by the log record referred to by LSN2 occurred after the change described by the log record LSN.</span></span>  
  
 <span data-ttu-id="688e8-112">重要なイベントが発生した時点のログ レコードの LSN を、正しい復元シーケンスの構築に役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="688e8-112">The LSN of a log record at which a significant event occurred can be useful for constructing correct restore sequences.</span></span> <span data-ttu-id="688e8-113">Lsn は順序付けられているため、等しいかどうかを比較できます (つまり、、、 **\<**, **>** **=** **\<=**, **>=** )。</span><span class="sxs-lookup"><span data-stu-id="688e8-113">Because LSNs are ordered, they can be compared for equality and inequality (that is, **\<**, **>**, **=**, **\<=**, **>=**).</span></span> <span data-ttu-id="688e8-114">このような比較は、復元シーケンスを構築するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="688e8-114">Such comparisons are useful when constructing restore sequences.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="688e8-115">LSN は、データ型 `numeric`(25,0) の値です。</span><span class="sxs-lookup"><span data-stu-id="688e8-115">LSNs are values of data type `numeric`(25,0).</span></span> <span data-ttu-id="688e8-116">算術演算 (加算や減算など) は、意味が無いので LSN では行わないでください。</span><span class="sxs-lookup"><span data-stu-id="688e8-116">Arithmetic operations (for example, addition or subtraction) are not meaningful and must not be used with LSNs.</span></span>  
  

  
## <a name="viewing-lsns-used-by-backup-and-restore"></a><span data-ttu-id="688e8-117">バックアップと復元で使用される LSN の表示</span><span class="sxs-lookup"><span data-stu-id="688e8-117">Viewing LSNs Used by Backup and Restore</span></span>  
 <span data-ttu-id="688e8-118">特定のバックアップと復元イベントが発生したログ レコードの LSN は、次の 1 つ以上の方法を使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="688e8-118">The LSN of a log record at which a given backup and restore event occurred is viewable using one or more of the following:</span></span>  
  
-   [<span data-ttu-id="688e8-119">backupset</span><span class="sxs-lookup"><span data-stu-id="688e8-119">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
-   [<span data-ttu-id="688e8-120">backupfile</span><span class="sxs-lookup"><span data-stu-id="688e8-120">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)  
  
-   <span data-ttu-id="688e8-121">[sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)、 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="688e8-121">[sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql); [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)</span></span>  
  
-   [<span data-ttu-id="688e8-122">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="688e8-122">RESTORE HEADERONLY</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="688e8-123">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="688e8-123">RESTORE FILELISTONLY</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="688e8-124">LSN は、一部のメッセージ テキストにも表示されます。</span><span class="sxs-lookup"><span data-stu-id="688e8-124">LSNs also appear in some message texts.</span></span>  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a><span data-ttu-id="688e8-125">LSN に復元するための Transact-SQL 構文</span><span class="sxs-lookup"><span data-stu-id="688e8-125">Transact-SQL Syntax for Restoring to an LSN</span></span>  
 <span data-ttu-id="688e8-126">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントを使用して、次のように LSN または LSN の直前まで復元できます。</span><span class="sxs-lookup"><span data-stu-id="688e8-126">By using a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, you can stop at or immediately before the LSN, as follows:</span></span>  
  
-   <span data-ttu-id="688e8-127">WITH STOPATMARK **='** lsn: _<lsn_number>_ **'** 句を使用します。ここで、lsn: *\<lsnNumber>* は、指定された LSN が含まれるログ レコードが復旧ポイントであることを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="688e8-127">Use the WITH STOPATMARK **='** lsn:_<lsn_number>_**'** clause, where lsn:*\<lsnNumber>* is a string that specifies that the log record that contains the specified LSN is the recovery point.</span></span>  
  
     <span data-ttu-id="688e8-128">STOPATMARK によって LSN までロールフォワードされ、そのログ レコードがロールフォワードに含められます。</span><span class="sxs-lookup"><span data-stu-id="688e8-128">STOPATMARK roll forwards to the LSN and includes that log record in the roll forward.</span></span>  
  
-   <span data-ttu-id="688e8-129">WITH STOPBEFOREMARK **='** lsn: _<lsn_number>_ **'** 句を使用します。ここで、lsn: *\<lsnNumber>* は、指定した LSN 番号が含まれるログ レコードの直前のログ レコードが復旧ポイントであることを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="688e8-129">Use the WITH STOPBEFOREMARK **='** lsn:_<lsn_number>_**'** clause, where lsn:*\<lsnNumber>* is a string that specifies that the log record immediately before the log record that contains the specified LSN number is the recovery point.</span></span>  
  
     <span data-ttu-id="688e8-130">STOPBEFOREMARK では、LSN までロールフォワードされますが、指定されたログ レコードはロールフォワードから除外されます。</span><span class="sxs-lookup"><span data-stu-id="688e8-130">STOPBEFOREMARK rolls forward to the LSN and excludes that log record from the roll forward.</span></span>  
  
 <span data-ttu-id="688e8-131">通常は、包含または除外する特定のトランザクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="688e8-131">Typically, a specific transaction is selected to be included or excluded.</span></span> <span data-ttu-id="688e8-132">実際には必要ありませんが、指定するログ レコードはトランザクション コミット レコードです。</span><span class="sxs-lookup"><span data-stu-id="688e8-132">Although not required, in practice, the specified log record is a transaction-commit record.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="688e8-133">例</span><span class="sxs-lookup"><span data-stu-id="688e8-133">Examples</span></span>  
 <span data-ttu-id="688e8-134">次の例では、完全復旧モデルを使用するように `AdventureWorks` データベースが変更されていることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="688e8-134">The following example assumes that the `AdventureWorks` database has been changed to use the full recovery model.</span></span>  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="688e8-135">関連タスク</span><span class="sxs-lookup"><span data-stu-id="688e8-135">Related Tasks</span></span>  
  
-   [<span data-ttu-id="688e8-136">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="688e8-136">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="688e8-137">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="688e8-137">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="688e8-138">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="688e8-138">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="688e8-139">完全復旧モデルで障害発生時点までデータベースを復元する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="688e8-139">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="688e8-140">マークされたトランザクションへのデータベースの復元 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="688e8-140">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="688e8-141">SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="688e8-141">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="688e8-142">参照</span><span class="sxs-lookup"><span data-stu-id="688e8-142">See Also</span></span>  
 <span data-ttu-id="688e8-143">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="688e8-143">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="688e8-144">[トランザクション ログ &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="688e8-144">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="688e8-145">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="688e8-145">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
