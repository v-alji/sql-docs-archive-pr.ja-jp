---
title: マークされたトランザクションを使用して、関連するデータベースを一貫して復旧する (完全復旧モデル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction marks [SQL Server]
- marked transactions [SQL Server]
- database restores [SQL Server], inserting transaction marks for
- recovery [SQL Server], related databases
- restoring databases [SQL Server], related database recovery
- database restores [SQL Server], related databases
- marked transactions [SQL Server], creating
- BEGIN TRAN...WITH MARK statement
- two-phase commit
ms.assetid: 50a73574-1a69-448e-83dd-9abcc7cb7e1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8dd368ad14f6e521fb8d504bdea774e3088c2522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736421"
---
# <a name="use-marked-transactions-to-recover-related-databases-consistently-full-recovery-model"></a><span data-ttu-id="ddde2-102">マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="ddde2-102">Use Marked Transactions to Recover Related Databases Consistently (Full Recovery Model)</span></span>
  <span data-ttu-id="ddde2-103">このトピックは、完全復旧モデルまたは一括ログ復旧モデルを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのみに関連しています。</span><span class="sxs-lookup"><span data-stu-id="ddde2-103">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="ddde2-104">関連する更新を複数のデータベース ( *関連データベース*) に対して実行する場合、トランザクション マークを使用して、それらのデータベースを論理的に一貫した状態に復旧できます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-104">When you make related updates to two or more databases, *related databases*, you can use transaction marks to recover them to a logically consistent point.</span></span> <span data-ttu-id="ddde2-105">ただし、この復旧により、復旧ポイントとして使用されていたマークより後にコミットされたトランザクションはすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-105">However, this recovery loses any transaction that is committed after the mark that was used as the recovery point.</span></span> <span data-ttu-id="ddde2-106">マークされたトランザクションの使用が適しているのは、関連データベースをテストする場合や、最近コミットされたトランザクションが失われてもよい場合のみです。</span><span class="sxs-lookup"><span data-stu-id="ddde2-106">Marking transactions is suitable only when you are testing related databases or when you are willing to lose recently committed transactions.</span></span>  
  
 <span data-ttu-id="ddde2-107">すべての関連データベースの関連トランザクションに定期的にマークを付けることにより、これらのデータベースに共通する一連の復旧ポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-107">Routinely marking related transactions in every related database establishes a series of common recovery points in the databases.</span></span> <span data-ttu-id="ddde2-108">これらのトランザクション マークはトランザクション ログに記録され、ログ バックアップに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-108">The transaction marks are recorded in the transaction log and included in log backups.</span></span> <span data-ttu-id="ddde2-109">障害が発生した場合、各データベースを同じトランザクション マークまで復元し、一貫性のある状態に復旧できます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-109">In the event of a disaster, you can restore each of the databases to the same transaction mark to recover them to a consistent point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddde2-110">データベースのログ バックアップは、各データベースで別々に作成できるため、同時に作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ddde2-110">Log backups on the different databases can be created independently of each other and do not have to be simultaneous.</span></span>  
  
 <span data-ttu-id="ddde2-111">次のシナリオで関連データベースを復旧するには、既にすべての関連データベースにマークされたトランザクションが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-111">Recovering related databases in the following scenarios requires that you have already marked transactions in every related database:</span></span>  
  
-   <span data-ttu-id="ddde2-112">1 つ以上のトランザクション ログが壊れている。</span><span class="sxs-lookup"><span data-stu-id="ddde2-112">One or more transaction logs are destroyed.</span></span> <span data-ttu-id="ddde2-113">データベースのセットを、最後のログ バックアップの時点の一貫性のある状態に復元する必要がある。</span><span class="sxs-lookup"><span data-stu-id="ddde2-113">You have to restore the set of databases to a consistent state at the time of your last log backup.</span></span>  
  
-   <span data-ttu-id="ddde2-114">データベースのセット全体を、以前の特定の時点の相互に一貫性のある状態に復元する必要がある。</span><span class="sxs-lookup"><span data-stu-id="ddde2-114">You have to restore the entire set of databases to a mutually consistent state at some earlier point in time.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ddde2-115">関連データベースを復旧できるのは、特定の時点までではなく、マークが付けられたトランザクションまでに限られます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-115">You can recover related databases only to a marked transaction, not to a specific point in time.</span></span>  
  
 <span data-ttu-id="ddde2-116">マークされたトランザクションの作成方法の詳細については、このトピックの「マーク付きトランザクションの作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddde2-116">For information about how to create marking transactions, see "Creating the Marked Transactions," later in this topic.</span></span>  
  
## <a name="typical-scenario-for-using-marked-transactions"></a><span data-ttu-id="ddde2-117">マークされたトランザクションを使用するための一般的なシナリオ</span><span class="sxs-lookup"><span data-stu-id="ddde2-117">Typical Scenario for Using Marked Transactions</span></span>  
 <span data-ttu-id="ddde2-118">マークされたトランザクションを使用するための一般的なシナリオでは、次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-118">A typical scenario for using marked transactions includes the following steps:</span></span>  
  
1.  <span data-ttu-id="ddde2-119">各関連データベースの完全バックアップまたは差分バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-119">Create a full or differential database backup of each of the related databases.</span></span>  
  
2.  <span data-ttu-id="ddde2-120">すべてのデータベースのトランザクション ブロックにマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-120">Mark a transaction block in all the databases.</span></span>  
  
3.  <span data-ttu-id="ddde2-121">すべてのデータベースのトランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="ddde2-121">Back up the transaction log for all the databases.</span></span>  
  
4.  <span data-ttu-id="ddde2-122">WITH NORECOVERY を指定してデータベース バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-122">Restore database backups WITH NORECOVERY.</span></span>  
  
5.  <span data-ttu-id="ddde2-123">WITH STOPATMARK を指定してログを復元します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-123">Restore logs WITH STOPATMARK.</span></span>  
  
## <a name="considerations-for-using-marked-transactions"></a><span data-ttu-id="ddde2-124">マークされたトランザクションの使用に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="ddde2-124">Considerations for Using Marked Transactions</span></span>  
 <span data-ttu-id="ddde2-125">名前付きマークをトランザクション ログに挿入する前に、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ddde2-125">Before inserting named marks into the transaction log, consider the following:</span></span>  
  
-   <span data-ttu-id="ddde2-126">トランザクション マークはログ領域を使用するので、データベース復旧ストラテジにおいて重要な役割を果たすトランザクションだけに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-126">Because transaction marks consume log space, use them only for transactions that play a significant role in the database recovery strategy.</span></span>  
  
-   <span data-ttu-id="ddde2-127">マークされたトランザクションのコミットが完了したら、 [msdb](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) の **logmarkhistory**テーブルに 1 行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-127">After a marked transaction commits, a row is inserted in the [logmarkhistory](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) table in **msdb**.</span></span>  
  
-   <span data-ttu-id="ddde2-128">マークされたトランザクションが同じデータベース サーバーまたは異なるサーバー上の複数のデータベースと関係している場合は、影響を受けたすべてのデータベースのログにそのマークが記録される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-128">If a marked transaction spans multiple databases on the same database server or on different servers, the marks must be recorded in the logs of all the affected databases.</span></span>  
  
## <a name="creating-the-marked-transactions"></a><span data-ttu-id="ddde2-129">マーク付きトランザクションの作成</span><span class="sxs-lookup"><span data-stu-id="ddde2-129">Creating the Marked Transactions</span></span>  
 <span data-ttu-id="ddde2-130">マーク付きトランザクションを作成するには、 [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) ステートメントと WITH MARK [*description*] 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-130">To create a marked transaction, use the [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) statement and the WITH MARK [*description*] clause.</span></span> <span data-ttu-id="ddde2-131">省略可能な *description* は、マークの説明テキストです。</span><span class="sxs-lookup"><span data-stu-id="ddde2-131">The optional *description* is a textual description of the mark.</span></span> <span data-ttu-id="ddde2-132">トランザクションのマーク名が必要です。</span><span class="sxs-lookup"><span data-stu-id="ddde2-132">A mark name for the transaction is required.</span></span> <span data-ttu-id="ddde2-133">マーク名は再利用できます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-133">A mark name can be reused.</span></span> <span data-ttu-id="ddde2-134">トランザクション ログには、マーク名、説明、データベース、ユーザー、datetime 情報、および LSN (ログ シーケンス番号) が記録されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-134">The transaction log records the mark name, description, database, user, datetime information, and the log sequence number (LSN).</span></span> <span data-ttu-id="ddde2-135">マーク名と共に datetime 情報を使用することで、マークが一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-135">The datetime information is used along with the mark name to uniquely identify the mark.</span></span>  
  
 <span data-ttu-id="ddde2-136">**データベースのセットでマーク付きトランザクションを作成するには**</span><span class="sxs-lookup"><span data-stu-id="ddde2-136">**To create marked transactions in a set of databases:**</span></span>  
  
1.  <span data-ttu-id="ddde2-137">BEGIN TRAN ステートメントでトランザクションに名前を付け、WITH MARK 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-137">Name the transaction in the BEGIN TRAN statement and use the WITH MARK clause</span></span>  
  
     <span data-ttu-id="ddde2-138">BEGIN TRAN *new_mark_name* WITH MARK ステートメントは、既存のトランザクション内で入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-138">You can nest the statement BEGIN TRAN *new_mark_name* WITH MARK within an existing transaction.</span></span> <span data-ttu-id="ddde2-139">トランザクションに名前が付いている場合でも、 *new_mark_name* の値がそのトランザクションのマーク名になります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-139">The value of *new_mark_name* is the mark name for the transaction, even if the transaction possesses a transaction name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ddde2-140">入れ子にした 2 番目の BEGIN TRAN...WITH MARK を実行すると、このステートメントはスキップされますが、警告メッセージは生成されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-140">If you issue a second nested BEGIN TRAN...WITH MARK, that statement is skipped but causes a warning message.</span></span>  
  
2.  <span data-ttu-id="ddde2-141">セット内のすべてのデータベースに対して更新を実行します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-141">Run an update against all of the databases in the set.</span></span>  
  
     <span data-ttu-id="ddde2-142">BEGIN TRAN...WITH MARK ステートメントが実行されるサーバー インスタンス上でのみ、特定のトランザクションのマークがトランザクション ログに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-142">The mark for a specific transaction is inserted into transaction logs only on the server instance where the BEGIN TRAN...WITH MARK statement is executed.</span></span> <span data-ttu-id="ddde2-143">トランザクション マークは、そのサーバー インスタンス上のマーク付きトランザクションによって更新されたすべてのデータベースのトランザクション ログに配置されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-143">The transaction mark is placed in the transaction log of every database updated by the marked transaction on that server instance.</span></span> <span data-ttu-id="ddde2-144">データベースが他のサーバー インスタンス上にある場合は、それらのサーバー インスタンスで同一のマークを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-144">If the databases reside on different server instances, identical marks must be created on each of the server instances.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ddde2-145">例</span><span class="sxs-lookup"><span data-stu-id="ddde2-145">Examples</span></span>  
 <span data-ttu-id="ddde2-146">次の例では、トランザクション ログを `ListPriceUpdate`というマーク付きトランザクションのマークまで復元します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-146">The following example restores the transaction log to the mark in the marked transaction named `ListPriceUpdate`.</span></span>  
  
```sql  
USE AdventureWorks  
GO  
BEGIN TRANSACTION ListPriceUpdate  
   WITH MARK 'UPDATE Product list prices';  
GO  
  
UPDATE Production.Product  
   SET ListPrice = ListPrice * 1.10  
   WHERE ProductNumber LIKE 'BK-%';  
GO  
  
COMMIT TRANSACTION ListPriceUpdate;  
GO  
  
-- Time passes. Regular database   
-- and log backups are taken.  
-- An error occurs in the database.  
USE master  
GO  
  
RESTORE DATABASE AdventureWorks  
FROM AdventureWorksBackups  
WITH FILE = 3, NORECOVERY;  
GO  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups   
   WITH FILE = 4,  
   RECOVERY,   
   STOPATMARK = 'ListPriceUpdate';  
```  
  
## <a name="forcing-a-mark-to-spread-to-other-servers"></a><span data-ttu-id="ddde2-147">他のサーバーへのマークの強制波及</span><span class="sxs-lookup"><span data-stu-id="ddde2-147">Forcing a Mark to Spread to Other Servers</span></span>  
 <span data-ttu-id="ddde2-148">トランザクションが別のサーバーに波及しても、トランザクション マーク名はそのサーバーに自動的には分散されません。</span><span class="sxs-lookup"><span data-stu-id="ddde2-148">A transaction mark name is not automatically distributed to another server as the transaction spreads there.</span></span> <span data-ttu-id="ddde2-149">他のサーバーにマークが広まるようにするには、BEGIN TRAN *name* WITH MARK ステートメントを含むストアド プロシージャを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-149">To force the mark to spread to the other servers, a stored procedure must be written that contains a BEGIN TRAN *name* WITH MARK statement.</span></span> <span data-ttu-id="ddde2-150">このストアド プロシージャは、元のサーバーのトランザクションの範囲内においてリモート サーバー上で実行されなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ddde2-150">That stored procedure must then be executed on the remote server under the scope of the transaction in the originating server.</span></span>  
  
 <span data-ttu-id="ddde2-151">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の複数のインスタンスに存在するパーティション データベースを考えてください。</span><span class="sxs-lookup"><span data-stu-id="ddde2-151">For example, consider a partitioned database that exists on multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ddde2-152">各インスタンスには、 `coyote`という名前のデータベースがあります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-152">On each instance is a database named `coyote`.</span></span> <span data-ttu-id="ddde2-153">まず、すべてのデータベースで `sp_SetMark`などのストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-153">First, in every database, create a stored procedure, for example, `sp_SetMark`.</span></span>  
  
```sql  
CREATE PROCEDURE sp_SetMark  
@name nvarchar (128)  
AS  
BEGIN TRANSACTION @name WITH MARK  
UPDATE coyote.dbo.Marks SET one = 1  
COMMIT TRANSACTION;  
GO  
```  
  
 <span data-ttu-id="ddde2-154">次に、すべてのデータベースにマークを挿入するトランザクションを含んでいる、 `sp_MarkAll` というストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-154">Next, create stored procedure `sp_MarkAll` containing a transaction that places a mark in every database.</span></span> <span data-ttu-id="ddde2-155">`sp_MarkAll` は、任意のインスタンスから実行できます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-155">`sp_MarkAll` can be run from any of the instances.</span></span>  
  
```sql  
CREATE PROCEDURE sp_MarkAll  
@name nvarchar (128)  
AS  
BEGIN TRANSACTION  
EXEC instance0.coyote.dbo.sp_SetMark @name  
EXEC instance1.coyote.dbo.sp_SetMark @name  
EXEC instance2.coyote.dbo.sp_SetMark @name  
COMMIT TRANSACTION;  
GO  
```  
  
### <a name="two-phase-commit"></a><span data-ttu-id="ddde2-156">2 フェーズ コミット (two-phase commit)</span><span class="sxs-lookup"><span data-stu-id="ddde2-156">Two-Phase Commit</span></span>  
 <span data-ttu-id="ddde2-157">分散トランザクションのコミットは、準備とコミットという 2 つのフェーズで発生します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-157">Committing a distributed transaction occurs in two phases: prepare and commit.</span></span> <span data-ttu-id="ddde2-158">マーク付きトランザクションがコミットされると、マーク付きトランザクション内の各データベースに関するコミット ログ レコードは、状況不明トランザクションがどのログにも含まれていない時点のログに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-158">When a marked transaction is committed, the commit log record for each database in the marked transaction is placed in the log at a point where there are no in-doubt transactions in any of the logs.</span></span> <span data-ttu-id="ddde2-159">これにより、トランザクションのコミット状態がログごとに異なるなどの問題がなくなります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-159">At this point, it is guaranteed that there are no transactions that appear as committed in one log, but not committed in another log.</span></span>  
  
 <span data-ttu-id="ddde2-160">この処理は、マーク付きトランザクションのコミット中に次の順で行われます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-160">The following steps accomplish this during the commit of a marked transaction:</span></span>  
  
1.  <span data-ttu-id="ddde2-161">マーク付きトランザクションの準備フェーズで、すべての新しい準備とコミットが停止します。</span><span class="sxs-lookup"><span data-stu-id="ddde2-161">Prepare phase of a marking transaction stalls all new prepares and commits.</span></span>  
  
2.  <span data-ttu-id="ddde2-162">既に準備が完了しているトランザクションのコミットのみが、継続を許可されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-162">Only commits of already prepared transactions are allowed to continue.</span></span>  
  
3.  <span data-ttu-id="ddde2-163">マーク付きトランザクションは、タイムアウトによってすべての準備されたトランザクションがなくなるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-163">Marking transaction then waits for all prepared transactions to drain (with time-out).</span></span>  
  
4.  <span data-ttu-id="ddde2-164">マーク付きのトランザクションが準備され、コミットされます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-164">Marked transaction is prepared and committed.</span></span>  
  
5.  <span data-ttu-id="ddde2-165">新しい準備とコミットの停止が解除されます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-165">The stall of new prepares and commits is removed.</span></span>  
  
 <span data-ttu-id="ddde2-166">複数のデータベースにまたがるマーク付きトランザクションによって引き起こされた機能停止は、サーバーのトランザクション処理パフォーマンスを低下させる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-166">The stalls generated by marked transactions that span multiple databases can reduce the transaction processing performance of the server.</span></span>  
  
 <span data-ttu-id="ddde2-167">複数のマーク付きトランザクションを同時に実行しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ddde2-167">We recommend that you do not run concurrent marked transactions.</span></span> <span data-ttu-id="ddde2-168">実際にはあまりないことですが、分散されたマーク付きトランザクションのコミットが、同時にコミットされる他のマーク付き分散トランザクションによってデッドロックに陥ることがあります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-168">It is rare but possible for the commit of a distributed marked transaction to deadlock with other distributed marked transactions that are committing at the same time.</span></span> <span data-ttu-id="ddde2-169">その場合、マーク付きトランザクションは、デッドロックの対象として選択され、ロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-169">When this happens, the marking transaction is chosen as the deadlock victim and is rolled back.</span></span> <span data-ttu-id="ddde2-170">このエラーが発生した場合、アプリケーションではマーク付きトランザクションを再試行できます。</span><span class="sxs-lookup"><span data-stu-id="ddde2-170">When this error occurs, the application can retry the marked transaction.</span></span> <span data-ttu-id="ddde2-171">複数のマーク付きトランザクションのコミットが同時に試行されると、デッドロックが生じる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="ddde2-171">When multiple marked transactions try to commit concurrently, there is a higher probability of deadlock.</span></span>  
  
## <a name="recovering-to-a-marked-transaction"></a><span data-ttu-id="ddde2-172">マークされたトランザクションへの復旧</span><span class="sxs-lookup"><span data-stu-id="ddde2-172">Recovering to a Marked Transaction</span></span>  
 <span data-ttu-id="ddde2-173">マークされたトランザクションを含むデータベースを特定のマークかその直前まで復旧する方法の詳細については、「 [マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法](recovery-of-related-databases-that-contain-marked-transaction.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddde2-173">For information about how to recover a database that contains marked transactions to or just before a particular mark, see [Recovery of Related  Databases That Contain Marked Transaction](recovery-of-related-databases-that-contain-marked-transaction.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddde2-174">参照</span><span class="sxs-lookup"><span data-stu-id="ddde2-174">See Also</span></span>  
 <span data-ttu-id="ddde2-175">[BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-distributed-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddde2-175">[BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-distributed-transaction-transact-sql) </span></span>  
 <span data-ttu-id="ddde2-176">[システム データベースのバックアップと復元 &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ddde2-176">[Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span></span>  
 <span data-ttu-id="ddde2-177">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddde2-177">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span></span>  
 <span data-ttu-id="ddde2-178">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ddde2-178">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="ddde2-179">[データベースの完全バックアップ &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ddde2-179">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="ddde2-180">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddde2-180">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="ddde2-181">マークされたトランザクションを含む関連データベースの復旧</span><span class="sxs-lookup"><span data-stu-id="ddde2-181">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
  
