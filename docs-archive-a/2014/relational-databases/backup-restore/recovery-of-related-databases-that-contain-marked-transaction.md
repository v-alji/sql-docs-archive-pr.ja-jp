---
title: マークされたトランザクションを含む関連データベースの復旧 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], marks
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- transactions [SQL Server], recovering to a mark
- database recovery [SQL Server]
- marked transactions [SQL Server], restoring
- database restores [SQL Server], point in time
ms.assetid: 77a0d9c0-978a-4891-8b0d-a4256c81c3f8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b968322f92c7a135adb5fd0733b5774e7562bc39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736438"
---
# <a name="recovery-of-related--databases-that-contain-marked-transaction"></a><span data-ttu-id="46fec-102">マークされたトランザクションを含む関連データベースの復旧</span><span class="sxs-lookup"><span data-stu-id="46fec-102">Recovery of Related  Databases That Contain Marked Transaction</span></span>
  <span data-ttu-id="46fec-103">このトピックは、マークされたトランザクションが含まれており、完全復旧モデルまたは一括ログ復旧モデルを使用するデータベースのみに関連しています。</span><span class="sxs-lookup"><span data-stu-id="46fec-103">This topic is relevant only for databases that contain marked transactions and that use the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="46fec-104">特定の復旧ポイントまでの復元するための要件については、「 [SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46fec-104">For information about the requirements for restoring to a specific recovery point, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="46fec-105">トランザクション ログに名前付きマークを挿入することによって、その特定のマークの時点に復旧できます。</span><span class="sxs-lookup"><span data-stu-id="46fec-105">supports inserting named marks into the transaction log to allow recovery to that specific mark.</span></span> <span data-ttu-id="46fec-106">ログ マークはトランザクションに固有で、関連するトランザクションがコミットされる場合のみ挿入されます。</span><span class="sxs-lookup"><span data-stu-id="46fec-106">Log marks are transaction specific and are inserted only if their associated transaction commits.</span></span> <span data-ttu-id="46fec-107">このため、マークを特定の操作に結び付けることが可能で、この操作を含む時点または含まない時点に復旧できます。</span><span class="sxs-lookup"><span data-stu-id="46fec-107">As a result, marks can be tied to specific work, and you can recover to a point that includes or excludes this work.</span></span>  
  
 <span data-ttu-id="46fec-108">名前付きマークをトランザクション ログに挿入する前に、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="46fec-108">Before you insert named marks into the transaction log, consider the following:</span></span>  
  
-   <span data-ttu-id="46fec-109">トランザクション マークはログ領域を使用するので、データベース復旧ストラテジにおいて重要な役割を果たすトランザクションだけに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46fec-109">Because transaction marks consume log space, use them only for transactions that play a significant role in the database recovery strategy.</span></span>  
  
-   <span data-ttu-id="46fec-110">マークされたトランザクションのコミットが完了したら、 [msdb](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) の **logmarkhistory**テーブルに 1 行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="46fec-110">After a marked transaction commits, a row is inserted in the [logmarkhistory](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) table in **msdb**.</span></span>  
  
-   <span data-ttu-id="46fec-111">マークされたトランザクションが同じデータベース サーバーまたは異なるサーバー上の複数のデータベースと関係している場合は、影響を受けたすべてのデータベースのログにそのマークが記録される必要があります。</span><span class="sxs-lookup"><span data-stu-id="46fec-111">If a marked transaction spans multiple databases on the same database server or on different servers, the marks must be recorded in the logs of all the affected databases.</span></span> <span data-ttu-id="46fec-112">詳細については、「 [マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46fec-112">For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46fec-113">トランザクションをマークする方法の詳細については、「 [マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46fec-113">For information about how to mark transactions, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
## <a name="transact-sql-syntax-for-inserting-named-marks-into-a-transaction-log"></a><span data-ttu-id="46fec-114">名前付きマークをトランザクション ログに挿入するための Transact-SQL 構文</span><span class="sxs-lookup"><span data-stu-id="46fec-114">Transact-SQL Syntax for Inserting Named Marks into a Transaction Log</span></span>  
 <span data-ttu-id="46fec-115">トランザクション ログにマークを挿入するには、 [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) ステートメントと WITH MARK [*description*] 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="46fec-115">To insert marks into the transaction logs, use the [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) statement and the WITH MARK [*description*] clause.</span></span> <span data-ttu-id="46fec-116">マークの名前はトランザクションの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="46fec-116">The mark is named the same as the transaction.</span></span> <span data-ttu-id="46fec-117">省略可能な *description* は、マークの名前ではなく、マークの説明テキストです。</span><span class="sxs-lookup"><span data-stu-id="46fec-117">The optional *description* is a textual description of the mark, not the mark name.</span></span> <span data-ttu-id="46fec-118">たとえば、次の `BEGIN TRANSACTION` ステートメントで作成されるトランザクションとマークは、いずれも名前が `Tx1`になります。</span><span class="sxs-lookup"><span data-stu-id="46fec-118">For example, the name of both the transaction and the mark that is created in the following `BEGIN TRANSACTION` statement is `Tx1`:</span></span>  
  
```wmimof  
BEGIN TRANSACTION Tx1 WITH MARK 'not the mark name, just a description'    
```  
  
 <span data-ttu-id="46fec-119">トランザクション ログには、マーク名 (トランザクション名)、説明、データベース、ユーザー、`datetime` 情報、および LSN (ログ シーケンス番号) が記録されます。</span><span class="sxs-lookup"><span data-stu-id="46fec-119">The transaction log records the mark name (transaction name), description, database, user, `datetime` information, and the log sequence number (LSN).</span></span> <span data-ttu-id="46fec-120">マーク名と共に `datetime` 情報を使用することで、マークが一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="46fec-120">The `datetime` information is used with the mark name to uniquely identify the mark.</span></span>  
  
 <span data-ttu-id="46fec-121">複数のデータベースに関係するトランザクションにマークを挿入する方法については、「 [マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46fec-121">For information about how to insert a mark into a transaction that spans multiple databases, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
## <a name="transact-sql-syntax-for-recovering-to-a-mark"></a><span data-ttu-id="46fec-122">特定のマークの時点へ復旧するための Transact-SQL 構文</span><span class="sxs-lookup"><span data-stu-id="46fec-122">Transact-SQL Syntax for Recovering to a Mark</span></span>  
 <span data-ttu-id="46fec-123">マークされたトランザクションを[RESTORE LOG](/sql/t-sql/statements/restore-statements-transact-sql)ステートメントで指定する場合、次のいずれかの句を使用して、マークに到達した時点またはマークの直前まで復旧できます。</span><span class="sxs-lookup"><span data-stu-id="46fec-123">When you target a marked transaction by using a[RESTORE LOG](/sql/t-sql/statements/restore-statements-transact-sql)statement, you can use one the following clauses to stop at or immediately before the mark:</span></span>  
  
-   <span data-ttu-id="46fec-124">WITH stopatmark = **' *`<mark_name>`* '** 句を使用して、マークされたトランザクションが復旧ポイントであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="46fec-124">Use the WITH STOPATMARK = **'*`<mark_name>`*'** clause to specify that the marked transaction is the recovery point.</span></span>  
  
     <span data-ttu-id="46fec-125">STOPATMARK では、マークまでロールフォワードされます。ロールフォワードには、マークされたトランザクションも含まれます。</span><span class="sxs-lookup"><span data-stu-id="46fec-125">STOPATMARK rolls forward to the mark and includes the marked transaction in the roll forward.</span></span>  
  
-   <span data-ttu-id="46fec-126">WITH STOPBEFOREMARK = **' *`<mark_name>`* '** 句を使用して、マークの直前にあるログレコードが復旧ポイントであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="46fec-126">Use the WITH STOPBEFOREMARK = **'*`<mark_name>`*'** clause to specify that the log record that is immediately before the mark is the recovery point.</span></span>  
  
     <span data-ttu-id="46fec-127">STOPBEFOREMARK では、マークまでロールフォワードされますが、マークされたトランザクションは含まれません。</span><span class="sxs-lookup"><span data-stu-id="46fec-127">STOPBEFOREMARK rolls forward to the mark and excludes marked the transaction from the roll forward.</span></span>  
  
 <span data-ttu-id="46fec-128">STOPATMARK オプションと STOPBEFOREMARK オプションは両方とも、省略可能な AFTER *datetime* 句をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="46fec-128">The STOPATMARK and STOPBEFOREMARK options both support an optional AFTER *datetime* clause.</span></span> <span data-ttu-id="46fec-129">*datetime* を使用する場合、マーク名を一意にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="46fec-129">When *datetime* is used, mark names do not have to be unique.</span></span>  
  
 <span data-ttu-id="46fec-130">AFTER *datetime* の指定を省略すると、指定した名前を持つ最初のマークでロールフォワードが停止します。</span><span class="sxs-lookup"><span data-stu-id="46fec-130">If AFTER *datetime* is omitted, roll forward stops at the first mark that has the specified name.</span></span> <span data-ttu-id="46fec-131">AFTER *datetime* を指定すると、 *datetime*以降の指定した名前を持つ最初のマークでロールフォワードが停止します。</span><span class="sxs-lookup"><span data-stu-id="46fec-131">If AFTER *datetime* is specified, roll forward stops at the first mark that has the specified name, exactly at or after *datetime*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46fec-132">時間を指定したすべての復元操作と同様に、一括ログ記録の対象となる操作がデータベースで実行されている場合は、マーク時点に復旧できません。</span><span class="sxs-lookup"><span data-stu-id="46fec-132">As in all point-in-time restore operations, recovering to a mark is disallowed when the database is undergoing operations that are bulk-logged.</span></span>  
  
 <span data-ttu-id="46fec-133">**マークされたトランザクションまで復旧するには**</span><span class="sxs-lookup"><span data-stu-id="46fec-133">**To restore to a marked transaction**</span></span>  
  
 [<span data-ttu-id="46fec-134">マークされたトランザクションへのデータベースの復元 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="46fec-134">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
 [<span data-ttu-id="46fec-135">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="46fec-135">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
### <a name="preparing-the-log-backups"></a><span data-ttu-id="46fec-136">ログ バックアップの準備</span><span class="sxs-lookup"><span data-stu-id="46fec-136">Preparing the Log Backups</span></span>  
 <span data-ttu-id="46fec-137">この例の場合、関連データベースに適切なバックアップ方法は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="46fec-137">For this example, an appropriate backup strategy for these related databases would be the following:</span></span>  
  
1.  <span data-ttu-id="46fec-138">両方のデータベースで完全復旧モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="46fec-138">Use the full recovery model for both databases.</span></span>  
  
2.  <span data-ttu-id="46fec-139">各データベースの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="46fec-139">Create a full backup of each database.</span></span>  
  
     <span data-ttu-id="46fec-140">データベースは順次と同時の両方でバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="46fec-140">The databases can be backed up sequentially or simultaneously.</span></span>  
  
3.  <span data-ttu-id="46fec-141">トランザクション ログをバックアップする前に、すべてのデータベースで実行されるトランザクションにマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="46fec-141">Before backing up the transaction log, mark a transaction that executes in all databases.</span></span> <span data-ttu-id="46fec-142">マークされたトランザクションを作成する方法の詳細については、「 [マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46fec-142">For information about how to create the marked transactions, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
4.  <span data-ttu-id="46fec-143">各データベースでトランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="46fec-143">Back up the transaction log on each database.</span></span>  
  
### <a name="recovering-the-database-to-a-marked-transaction"></a><span data-ttu-id="46fec-144">マークされたトランザクションへのデータベースの復旧</span><span class="sxs-lookup"><span data-stu-id="46fec-144">Recovering the Database to a Marked Transaction</span></span>  
 <span data-ttu-id="46fec-145">**バックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="46fec-145">**To restore the backup**</span></span>  
  
1.  <span data-ttu-id="46fec-146">可能であれば、壊れていないデータベースの [ログ末尾のバックアップ](tail-log-backups-sql-server.md) を作成します。</span><span class="sxs-lookup"><span data-stu-id="46fec-146">Create [tail-log backups](tail-log-backups-sql-server.md) of the undamaged databases, if possible.</span></span>  
  
2.  <span data-ttu-id="46fec-147">各データベースの最新の完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="46fec-147">Restore the most recent full database backup of each database.</span></span>  
  
3.  <span data-ttu-id="46fec-148">すべてのトランザクション ログ バックアップで使用できるマークされた最新のトランザクションを識別します。</span><span class="sxs-lookup"><span data-stu-id="46fec-148">Identify the most recent marked transaction that is available in all of the transaction log backups.</span></span> <span data-ttu-id="46fec-149">この情報は、各サーバー上の **msdb** データベースの **logmarkhistory** テーブルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="46fec-149">This information is stored in the **logmarkhistory** table in the **msdb** database on each server.</span></span>  
  
4.  <span data-ttu-id="46fec-150">そのマークが格納されているすべての関連データベースのログ バックアップを識別します。</span><span class="sxs-lookup"><span data-stu-id="46fec-150">Identify the log backups for all related databases that contain this mark.</span></span>  
  
5.  <span data-ttu-id="46fec-151">それぞれのログ バックアップを復元し、マーク付きトランザクションで停止します。</span><span class="sxs-lookup"><span data-stu-id="46fec-151">Restore each log backup, stopping at the marked transaction.</span></span>  
  
6.  <span data-ttu-id="46fec-152">各データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="46fec-152">Recover each database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46fec-153">参照</span><span class="sxs-lookup"><span data-stu-id="46fec-153">See Also</span></span>  
 <span data-ttu-id="46fec-154">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="46fec-154">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span></span>  
 <span data-ttu-id="46fec-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="46fec-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="46fec-156">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="46fec-156">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="46fec-157">[マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) </span><span class="sxs-lookup"><span data-stu-id="46fec-157">[Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) </span></span>  
 <span data-ttu-id="46fec-158">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="46fec-158">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="46fec-159">[SQL Server データベースを特定の時点に復元する方法 &#40;完全復旧モデル&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="46fec-159">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="46fec-160">復元シーケンスの計画と実行 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="46fec-160">Plan and Perform Restore Sequences &#40;Full Recovery Model&#41;</span></span>](plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
