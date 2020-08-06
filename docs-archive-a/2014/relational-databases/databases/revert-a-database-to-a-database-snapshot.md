---
title: データベースをデータベース スナップショットに戻す | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], reverting to
- reverting databases
ms.assetid: 8f74dd31-c9ca-4537-8760-0c7648f0787d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c78da3d7c559309c0563760e7062f01cf784648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640055"
---
# <a name="revert-a-database-to-a-database-snapshot"></a><span data-ttu-id="5963a-102">データベースをデータベース スナップショットに戻す</span><span class="sxs-lookup"><span data-stu-id="5963a-102">Revert a Database to a Database Snapshot</span></span>
  <span data-ttu-id="5963a-103">オンライン データベースのデータが破損した場合、特定のケースでは、データベースをバックアップから復元する代わりに、データベースをデータが破損した日付より前のデータベース スナップショットに復帰させる方が適切であることがあります。</span><span class="sxs-lookup"><span data-stu-id="5963a-103">If data in an online database becomes damaged, in some cases, reverting the database to a database snapshot that predates the damage might be an appropriate alternative to restoring the database from a backup.</span></span> <span data-ttu-id="5963a-104">たとえば、テーブルの削除など、最近の重大なユーザー エラーを元に戻すには、データベースの復帰が役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="5963a-104">For example, reverting a database might be useful for reverse a recent serious user error, such as a dropped table.</span></span> <span data-ttu-id="5963a-105">ただし、スナップショットの作成後に行った変更はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="5963a-105">However, all changes made after the snapshot was created are lost.</span></span>  
  
-   <span data-ttu-id="5963a-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="5963a-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5963a-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5963a-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5963a-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="5963a-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="5963a-109">Security</span><span class="sxs-lookup"><span data-stu-id="5963a-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5963a-110">**以下を使用して、データベースをデータベース スナップショットに戻す方法:** [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="5963a-110">**To Revert a Database to a Database Snapshot, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5963a-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="5963a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5963a-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5963a-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="5963a-113">元に戻す操作は、次の状況ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="5963a-113">Reverting is unsupported under the following conditions:</span></span>  
  
-   <span data-ttu-id="5963a-114">現在、データベースに、復帰する対象としてデータベース スナップショットが 1 つしかない。</span><span class="sxs-lookup"><span data-stu-id="5963a-114">The database must currently have only one database snapshot, to which you plan to revert.</span></span>  
  
-   <span data-ttu-id="5963a-115">読み取り専用のファイル グループまたは圧縮されたファイル グループがデータベースにある。</span><span class="sxs-lookup"><span data-stu-id="5963a-115">Any read-only or compressed filegroups exist in the database.</span></span>  
  
-   <span data-ttu-id="5963a-116">ファイルは現在オフラインだが、スナップショットの作成時はオンラインだった。</span><span class="sxs-lookup"><span data-stu-id="5963a-116">Any files are now offline but were online when the snapshot was created.</span></span>  
  
 <span data-ttu-id="5963a-117">データベースを復帰する前に、次の制限について検討してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-117">Before reverting a database, consider the following limitations:</span></span>  
  
-   <span data-ttu-id="5963a-118">復帰は、メディアの復旧を目的としたものではありません。</span><span class="sxs-lookup"><span data-stu-id="5963a-118">Reverting is not intended for media recovery.</span></span> <span data-ttu-id="5963a-119">.</span><span class="sxs-lookup"><span data-stu-id="5963a-119">.</span></span> <span data-ttu-id="5963a-120">データベース スナップショットはデータベース ファイルの不完全なコピーであるため、データベースまたはデータベース スナップショットが壊れた場合、スナップショットから復帰することはほぼ不可能です。</span><span class="sxs-lookup"><span data-stu-id="5963a-120">A database snapshot is an incomplete copy of the database files, so if either the database or the database snapshot is corrupted, reverting from a snapshot is likely to be impossible.</span></span> <span data-ttu-id="5963a-121">復帰が可能であっても、データベースまたはデータベース スナップショットが壊れている場合は、問題が解決しない可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="5963a-121">Furthermore, even when it is possible, reverting in the event of corruption is unlikely to correct the problem.</span></span> <span data-ttu-id="5963a-122">このため、データベースの保護には、定期的なバックアップと復元プランのテストが必要です。</span><span class="sxs-lookup"><span data-stu-id="5963a-122">Therefore, taking regular backups and testing your restore plan are essential to protect a database.</span></span> <span data-ttu-id="5963a-123">詳しくは、「[SQL Server データベースのバックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5963a-123">For more information, see [Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5963a-124">データベース スナップショットの作成時点の状態にソース データベースを復元できるようにする必要がある場合は、完全復旧モデルを使用し、そのためのバックアップ ポリシーを実装してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-124">If you need to be able to restore the source database to the point in time at which you created a database snapshot, use the full recovery model and implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="5963a-125">元のソース データベースは、復帰されたデータベースで上書きされるため、スナップショットの作成後にデータベースに行った更新内容はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="5963a-125">The original source database is overwritten by the reverted database, so any updates to the database since the snapshot's creation are lost.</span></span>  
  
-   <span data-ttu-id="5963a-126">また、復帰操作によって古いログ ファイルが上書きされ、ログが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="5963a-126">The revert operation also overwrites the old log file and rebuilds the log.</span></span> <span data-ttu-id="5963a-127">そのため、復帰したデータベースをユーザー エラーの時点までロール フォワードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5963a-127">Consequently, you cannot roll the reverted database forward to the point of user error.</span></span> <span data-ttu-id="5963a-128">したがって、データベースを復帰させる前に、ログをバックアップすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5963a-128">Therefore, we recommend that you back up the log before reverting a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5963a-129">元のログを復元してデータベースをロール フォワードすることはできませんが、元のログ ファイルの情報は失われたデータを再構築する際に役に立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="5963a-129">Although you cannot restore the original log to roll forward the database, the information in the original log file can be useful for reconstructing lost data.</span></span>  
  
-   <span data-ttu-id="5963a-130">復帰によってログ バックアップ チェーンが中断されます。</span><span class="sxs-lookup"><span data-stu-id="5963a-130">Reverting breaks the log backup chain.</span></span> <span data-ttu-id="5963a-131">したがって、復帰したデータベースのログ バックアップを行う前に、最初にデータベース全体のバックアップまたはファイルのバックアップを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5963a-131">Therefore, before you can take log backups of the reverted database, you must first take a full database backup or file backup.</span></span> <span data-ttu-id="5963a-132">データベースの完全バックアップをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5963a-132">We recommend a full database backup.</span></span>  
  
-   <span data-ttu-id="5963a-133">復帰操作中、スナップショットとソース データベースは両方とも使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5963a-133">During a revert operation, both the snapshot and the source database are unavailable.</span></span> <span data-ttu-id="5963a-134">ソース データベースとスナップショットには両方とも "復元中" のマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="5963a-134">The source database and snapshot are both marked "In restore."</span></span> <span data-ttu-id="5963a-135">復帰操作中にエラーが発生した場合は、データベースを再起動すると、復帰操作の終了が試行されます。</span><span class="sxs-lookup"><span data-stu-id="5963a-135">If an error occurs during the revert operation, when the database starts up again, the revert operation will try to finish reverting.</span></span>  
  
-   <span data-ttu-id="5963a-136">復帰したデータベースのメタデータは、スナップショット時のメタデータと同じです。</span><span class="sxs-lookup"><span data-stu-id="5963a-136">The metadata of a reverted database is the same as the metadata at the time of the snapshot.</span></span>  
  
-   <span data-ttu-id="5963a-137">復帰を行うと、すべてのフルテキスト カタログが削除されます。</span><span class="sxs-lookup"><span data-stu-id="5963a-137">Reverting drops all the full-text catalogs.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="5963a-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="5963a-138">Prerequisites</span></span>  
 <span data-ttu-id="5963a-139">ソース データベースとデータベースの スナップショットが次の前提条件を満たすことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-139">Ensure that the source database and database snapshot meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="5963a-140">データベースが破損していないことを確認する。</span><span class="sxs-lookup"><span data-stu-id="5963a-140">Verify that the database has not become corrupted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5963a-141">データベースが破損している場合は、バックアップから復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5963a-141">If the database has been corrupted, you will need to restore it from backups.</span></span> <span data-ttu-id="5963a-142">詳細については、「[データベースの全体復元 &#40;単純復旧モデル&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md)」または「[データベースの全体復元 &#40;完全復旧モデル&#41;](../backup-restore/complete-database-restores-full-recovery-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-142">For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) or [Complete Database Restores &#40;Full Recovery Model&#41;](../backup-restore/complete-database-restores-full-recovery-model.md).</span></span>  
  
-   <span data-ttu-id="5963a-143">エラーの前に作成された最近のスナップショットを特定する。</span><span class="sxs-lookup"><span data-stu-id="5963a-143">Identify a recent snapshot that was created before the error.</span></span> <span data-ttu-id="5963a-144">詳細については、「 [データベース スナップショットの表示 &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)で参照できます。</span><span class="sxs-lookup"><span data-stu-id="5963a-144">For more information, see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span></span>  
  
-   <span data-ttu-id="5963a-145">データベース上に現在存在するその他のスナップショットをすべて削除する。</span><span class="sxs-lookup"><span data-stu-id="5963a-145">Drop any other snapshots that currently exist on the database.</span></span> <span data-ttu-id="5963a-146">詳細については、「 [データベース スナップショットの削除 &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-146">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5963a-147">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5963a-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5963a-148">Permissions</span><span class="sxs-lookup"><span data-stu-id="5963a-148">Permissions</span></span>  
 <span data-ttu-id="5963a-149">ソース データベースで RESTORE DATABASE 権限を持つユーザーは、データベース スナップショットが作成されたときの状態に復帰させることができます。</span><span class="sxs-lookup"><span data-stu-id="5963a-149">Any user who has RESTORE DATABASE permissions on the source database can revert it to its state when a database snapshot was created.</span></span>  
  
##  <a name="how-to-revert-a-database-to-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5963a-150">データベースをデータベース スナップショットに戻す方法 (Transact-SQL の使用)</span><span class="sxs-lookup"><span data-stu-id="5963a-150">How to Revert a Database to a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="5963a-151">**データベースをデータベース スナップショットに戻すには**</span><span class="sxs-lookup"><span data-stu-id="5963a-151">**To revert a database to a database snapshot**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5963a-152">この手順の例については、このセクションの後半の「 [例 (Transact-SQL)](#TsqlExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-152">For an example of this procedure, see [Examples (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="5963a-153">データベースを戻す対象になるデータベース スナップショットを特定します。</span><span class="sxs-lookup"><span data-stu-id="5963a-153">Identify the database snapshot to which you want to revert the database.</span></span> <span data-ttu-id="5963a-154">データベース内のスナップショットは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で参照できます (詳細については、「 [データベース スナップショットの表示 &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5963a-154">You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)).</span></span> <span data-ttu-id="5963a-155">また、 **sys.databases &amp;#40;Transact-SQL&amp;#41;** カタログ ビューの [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 列から、ビューのソース データベースを特定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5963a-155">Also, you can identify the source database of a view from the **source_database_id** column of the [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
2.  <span data-ttu-id="5963a-156">他のデータベース スナップショットを削除します。</span><span class="sxs-lookup"><span data-stu-id="5963a-156">Drop any other database snapshots.</span></span>  
  
     <span data-ttu-id="5963a-157">スナップショットの削除の詳細については、「 [データベース スナップショットの削除 &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-157">For information on dropping snapshots, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span> <span data-ttu-id="5963a-158">データベースで完全復旧モデルを使用している場合は、データベースを戻す前にログをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5963a-158">If the database uses the full recovery model, before reverting, you should back up the log.</span></span> <span data-ttu-id="5963a-159">詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md)」または「[データベースが破損したときのトランザクション ログのバックアップ &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-159">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) or [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="5963a-160">データベースを戻す操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5963a-160">Perform the revert operation.</span></span>  
  
     <span data-ttu-id="5963a-161">データベースを戻す操作には、ソース データベースに対して RESTORE DATABASE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="5963a-161">A revert operation requires RESTORE DATABASE permissions on the source database.</span></span> <span data-ttu-id="5963a-162">データベースを戻すには、次の Transact-SQL ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5963a-162">To revert the database, use the following Transact-SQL statement:</span></span>  
  
     <span data-ttu-id="5963a-163">RESTORE DATABASE *database_name* FROM DATABASE_SNAPSHOT **=** _database_snapshot_name_</span><span class="sxs-lookup"><span data-stu-id="5963a-163">RESTORE DATABASE *database_name* FROM DATABASE_SNAPSHOT **=**_database_snapshot_name_</span></span>  
  
     <span data-ttu-id="5963a-164">*database_name* はソース データベースで、 *database_snapshot_name* はデータベースを戻す対象になるスナップショットの名前です。</span><span class="sxs-lookup"><span data-stu-id="5963a-164">Where *database_name* is the source database and *database_snapshot_name* is the name of the snapshot to which you want to revert the database.</span></span> <span data-ttu-id="5963a-165">このステートメントでは、バックアップ デバイスではなく、スナップショット名を指定する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-165">Notice that in this statement, you must specify a snapshot name rather than a backup device.</span></span>  
  
     <span data-ttu-id="5963a-166">詳細については、「 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)で復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="5963a-166">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5963a-167">データベースを戻す操作中、スナップショットとソース データベースはどちらも使用できません。</span><span class="sxs-lookup"><span data-stu-id="5963a-167">During the revert operation, both the snapshot and the source database are unavailable.</span></span> <span data-ttu-id="5963a-168">ソース データベースとスナップショットは、どちらも "復元中" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5963a-168">The source database and snapshot are both marked as "In restore."</span></span> <span data-ttu-id="5963a-169">データベースを戻す操作中にエラーが発生した場合は、データベースを再び起動したときに、データベースを戻す操作の完了を試行します。</span><span class="sxs-lookup"><span data-stu-id="5963a-169">If an error occurs during the revert operation, it will try to finish reverting when the database starts up again.</span></span>  
  
4.  <span data-ttu-id="5963a-170">データベース スナップショットの作成後にデータベース所有者を変更した場合、戻したデータベースのデータベース所有者を更新できます。</span><span class="sxs-lookup"><span data-stu-id="5963a-170">If the database owner changed since creation of the database snapshot, you may want to update the database owner of the reverted database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5963a-171">戻したデータベースでは、データベース スナップショットの権限と構成 (データベース所有者や復旧モデルなど) が保持されます。</span><span class="sxs-lookup"><span data-stu-id="5963a-171">The reverted database retains the permissions and configuration (such as database owner and recovery model) of the database snapshot.</span></span>  
  
5.  <span data-ttu-id="5963a-172">データベースを起動します。</span><span class="sxs-lookup"><span data-stu-id="5963a-172">Start the database.</span></span>  
  
6.  <span data-ttu-id="5963a-173">必要に応じて (特に、完全 (または一括ログ) 復旧モデルを使用している場合)、戻したデータベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="5963a-173">Optionally, back up the reverted database, especially if it uses the full (or bulk-logged) recovery model.</span></span> <span data-ttu-id="5963a-174">データベースをバックアップするには、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-174">To back up a database, see [Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="5963a-175">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5963a-175">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="5963a-176">ここでは、データベースをデータベース スナップショットに戻す、次の例を示します。</span><span class="sxs-lookup"><span data-stu-id="5963a-176">This section contains the following examples of reverting a database to a database snapshot:</span></span>  
  
-   <span data-ttu-id="5963a-177">A.</span><span class="sxs-lookup"><span data-stu-id="5963a-177">A.</span></span> [<span data-ttu-id="5963a-178">AdventureWorks データベースのスナップショットを戻す</span><span class="sxs-lookup"><span data-stu-id="5963a-178">Reverting a snapshot on the AdventureWorks database</span></span>](#Reverting_AW)  
  
-   <span data-ttu-id="5963a-179">B.</span><span class="sxs-lookup"><span data-stu-id="5963a-179">B.</span></span> [<span data-ttu-id="5963a-180">Sales データベースのスナップショットを戻す</span><span class="sxs-lookup"><span data-stu-id="5963a-180">Reverting a snapshot on the Sales database</span></span>](#Reverting_Sales)  
  
####  <a name="a-reverting-a-snapshot-on-the-adventureworks-database"></a><a name="Reverting_AW"></a> <span data-ttu-id="5963a-181">A.</span><span class="sxs-lookup"><span data-stu-id="5963a-181">A.</span></span> <span data-ttu-id="5963a-182">AdventureWorks データベースのスナップショットを戻す</span><span class="sxs-lookup"><span data-stu-id="5963a-182">Reverting a snapshot on the AdventureWorks database</span></span>  
 <span data-ttu-id="5963a-183">この例では、現在、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに 1 つだけスナップショットが存在することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="5963a-183">This example assumes that only one snapshot currently exists on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="5963a-184">データベースを戻す対象になるスナップショットを作成する例については、「 [データベース スナップショットの作成 &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-184">For the example that creates the snapshot to which the database is reverted here, see [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span></span>  
  
```  
USE master;  
-- Reverting AdventureWorks to AdventureWorks_dbss1800  
RESTORE DATABASE AdventureWorks from   
DATABASE_SNAPSHOT = 'AdventureWorks_dbss1800';  
GO  
```  
  
####  <a name="b-reverting-a-snapshot-on-the-sales-database"></a><a name="Reverting_Sales"></a> <span data-ttu-id="5963a-185">B.</span><span class="sxs-lookup"><span data-stu-id="5963a-185">B.</span></span> <span data-ttu-id="5963a-186">Sales データベースのスナップショットを戻す</span><span class="sxs-lookup"><span data-stu-id="5963a-186">Reverting a snapshot on the Sales database</span></span>  
 <span data-ttu-id="5963a-187">この例では、現在、 **Sales** データベースに 2 つのスナップショット ( **sales_snapshot0600** および **sales_snapshot1200**) が存在することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="5963a-187">This example assumes that two snapshots currently exist on the **Sales** database: **sales_snapshot0600** and **sales_snapshot1200**.</span></span> <span data-ttu-id="5963a-188">古いスナップショットを削除し、新しいスナップショットにデータベースを戻します。</span><span class="sxs-lookup"><span data-stu-id="5963a-188">The example deletes the older of the snapshots and reverts the database to the more recent snapshot.</span></span>  
  
 <span data-ttu-id="5963a-189">この例で使用するサンプル データベースおよびスナップショットを作成するためのコードについては、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-189">For the code for creating the sample database and snapshots on which this example depends, see:</span></span>  
  
-   <span data-ttu-id="5963a-190">**Sales** データベースと **sales_snapshot0600** スナップショットについては、「[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」の「ファイル グループのあるデータベースを作成する」および「データベース スナップショットを作成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-190">For the **Sales** database and the **sales_snapshot0600** snapshot, see "Creating a database with filegroups" and "Creating a database snapshot" in [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
-   <span data-ttu-id="5963a-191">**sales_snapshot1200** スナップショットについては、「[データベース スナップショットの作成 &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md)」の「Sales データベースのスナップショットを作成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5963a-191">For the **sales_snapshot1200** snapshot, see "Creating a snapshot on the Sales database" in [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span></span>  
  
```  
--Test to see if sales_snapshot0600 exists and if it   
-- does, delete it.  
IF EXISTS (SELECT dbid FROM sys.databases  
    WHERE NAME='sales_snapshot0600')  
    DROP DATABASE SalesSnapshot0600;  
GO  
-- Reverting Sales to sales_snapshot1200  
USE master;  
RESTORE DATABASE Sales FROM DATABASE_SNAPSHOT = 'sales_snapshot1200';  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5963a-192">関連タスク</span><span class="sxs-lookup"><span data-stu-id="5963a-192">Related Tasks</span></span>  
  
-   [<span data-ttu-id="5963a-193">データベース スナップショットの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5963a-193">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="5963a-194">データベース スナップショットの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5963a-194">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="5963a-195">データベース スナップショットの削除 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5963a-195">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="5963a-196">参照</span><span class="sxs-lookup"><span data-stu-id="5963a-196">See Also</span></span>  
 <span data-ttu-id="5963a-197">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5963a-197">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span></span>  
 <span data-ttu-id="5963a-198">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5963a-198">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="5963a-199">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5963a-199">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="5963a-200">データベース ミラーリングとデータベース スナップショット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5963a-200">Database Mirroring and Database Snapshots &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-and-database-snapshots-sql-server.md)  
  
  
