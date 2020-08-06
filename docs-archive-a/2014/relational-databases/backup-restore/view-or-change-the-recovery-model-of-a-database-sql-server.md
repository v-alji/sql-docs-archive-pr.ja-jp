---
title: データベースの復旧モデルの表示または変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], recovery models
- recovery [SQL Server], recovery model
- backing up databases [SQL Server], recovery models
- recovery models [SQL Server], switching
- recovery models [SQL Server], viewing
- database restores [SQL Server], recovery models
- modifying database recovery models
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 889080301109938f0514bd6b81265c100237ab60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718308"
---
# <a name="view-or-change-the-recovery-model-of-a-database-sql-server"></a><span data-ttu-id="c454d-102">データベースの復旧モデルの表示または変更 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c454d-102">View or Change the Recovery Model of a Database (SQL Server)</span></span>
  <span data-ttu-id="c454d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]でデータベースの復旧モデルを表示または変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c454d-103">This topic describes how to view or change the recovery model of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c454d-104">*復旧モデル* は、トランザクションをログに記録する方法、トランザクション ログのバックアップを必須 (および可能) にするかどうか、利用できる復元操作の種類などを制御するデータベース プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c454d-104">A *recovery model* is a database property that controls how transactions are logged, whether the transaction log requires (and allows) backing up, and what kinds of restore operations are available.</span></span> <span data-ttu-id="c454d-105">復旧モデルの種類は、単純、完全、および一括ログの 3 種類です。</span><span class="sxs-lookup"><span data-stu-id="c454d-105">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="c454d-106">通常、データベースには完全復旧モデルまたは単純復旧モデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c454d-106">Typically, a database uses the full recovery model or simple recovery model.</span></span> <span data-ttu-id="c454d-107">データベースは、任意の時点で別の復旧モデルに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="c454d-107">A database can be switched to another recovery model at any time.</span></span> <span data-ttu-id="c454d-108">**model** データベースは、新しいデータベースの既定の復旧モデルを設定します。</span><span class="sxs-lookup"><span data-stu-id="c454d-108">The **model** database sets the default recovery model of new databases.</span></span>  
  
 <span data-ttu-id="c454d-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c454d-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c454d-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c454d-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c454d-111">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="c454d-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c454d-112">Security</span><span class="sxs-lookup"><span data-stu-id="c454d-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c454d-113">**データベースの復旧モデルを表示または変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="c454d-113">**To view or change the recovery model of a database, using:**</span></span>  
  
     [<span data-ttu-id="c454d-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c454d-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c454d-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c454d-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="c454d-116">**補足の推奨事項:**  [復旧モデルを変更した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="c454d-116">**Follow Up Recommendations:**  [After You Change the Recovery Model](#FollowUp)</span></span>  
  
-   [<span data-ttu-id="c454d-117">関連タスク</span><span class="sxs-lookup"><span data-stu-id="c454d-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c454d-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="c454d-118">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c454d-119">推奨事項</span><span class="sxs-lookup"><span data-stu-id="c454d-119">Recommendations</span></span>  
  
-   <span data-ttu-id="c454d-120">完全復旧モデルまたは一括ログ復旧モデルから切り替える前に、トランザクション ログをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="c454d-120">Before switching from the full recovery or bulk-logged recovery model, back up the transaction log.</span></span>  
  
-   <span data-ttu-id="c454d-121">一括ログ復旧モデルでは特定の時点に復旧できません。</span><span class="sxs-lookup"><span data-stu-id="c454d-121">Point-in-time recovery is not possible with bulk-logged model.</span></span> <span data-ttu-id="c454d-122">そのため、一括ログ復旧モデルでトランザクション ログの復元を必要とするトランザクションを実行すると、データが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c454d-122">Therefore, if you run transactions under the bulk-logged recovery model that might require a transaction log restore, these transactions could be exposed to data loss.</span></span> <span data-ttu-id="c454d-123">災害復旧シナリオでデータをより確実に復旧するには、次の条件下でのみ一括ログ復旧モデルに切り替えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c454d-123">To maximize data recoverability in a disaster-recovery scenario, we recommend that you switch to the bulk-logged recovery model only under the following conditions:</span></span>  
  
    -   <span data-ttu-id="c454d-124">ユーザーが現在データベースで許可されていない場合。</span><span class="sxs-lookup"><span data-stu-id="c454d-124">Users are currently not allowed in the database.</span></span>  
  
    -   <span data-ttu-id="c454d-125">一括処理中に行われたすべての変更が、ログ バックアップを行うかどうかに関係なく復旧可能な場合 (一括処理の再実行など)。</span><span class="sxs-lookup"><span data-stu-id="c454d-125">All modifications made during bulk processing are recoverable without depending on taking a log backup; for example, by re-running the bulk processes.</span></span>  
  
     <span data-ttu-id="c454d-126">この 2 つの条件を満たす場合は、一括ログ復旧モデルでバックアップされたトランザクション ログの復元中に、データが失われることはありません。</span><span class="sxs-lookup"><span data-stu-id="c454d-126">If you satisfy these two conditions, you will not be exposed to any data loss while restoring a transaction log that was backed up under the bulk-logged recovery model..</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c454d-127">一括操作中に完全復旧モデルに切り替える場合は、一括操作のログ記録が最小ログ記録から完全ログ記録に変わり、また、その逆も同様です。</span><span class="sxs-lookup"><span data-stu-id="c454d-127">If you switch to the full recovery model during a bulk operation, the logging of the bulk operation changes from minimal logging to full logging, and vice versa.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c454d-128">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c454d-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c454d-129">Permissions</span><span class="sxs-lookup"><span data-stu-id="c454d-129">Permissions</span></span>  
 <span data-ttu-id="c454d-130">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c454d-130">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c454d-131">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c454d-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-recovery-model"></a><span data-ttu-id="c454d-132">復旧モデルを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="c454d-132">To view or change the recovery model</span></span>  
  
1.  <span data-ttu-id="c454d-133">適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスへの接続後、オブジェクト エクスプローラーでサーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c454d-133">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="c454d-134">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="c454d-134">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="c454d-135">データベースを右クリックし、 **[プロパティ]** をクリックすると、 **[データベースのプロパティ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="c454d-135">Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="c454d-136">**[ページの選択]** ペインの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c454d-136">In the **Select a page** pane, click **Options**.</span></span>  
  
5.  <span data-ttu-id="c454d-137">**[復旧モデル]** ボックスの一覧に現在の復旧モデルが表示されています。</span><span class="sxs-lookup"><span data-stu-id="c454d-137">The current recovery model is displayed in the **Recovery model** list box.</span></span>  
  
6.  <span data-ttu-id="c454d-138">復旧モデルを変更する必要がある場合は、別のモデルをこの一覧で選択します。</span><span class="sxs-lookup"><span data-stu-id="c454d-138">Optionally, to change the recovery model select a different model list.</span></span> <span data-ttu-id="c454d-139">選択できるのは、 **[完全]** 、 **[一括ログ]** 、 **[単純]** のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="c454d-139">The choices are **Full**, **Bulk-logged**, or **Simple**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c454d-140">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c454d-140">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-recovery-model"></a><span data-ttu-id="c454d-141">復旧モデルを表示するには</span><span class="sxs-lookup"><span data-stu-id="c454d-141">To view the recovery model</span></span>  
  
1.  <span data-ttu-id="c454d-142">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="c454d-142">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c454d-143">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c454d-143">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c454d-144">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c454d-144">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c454d-145">この例では、 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) カタログ ビューにクエリを実行して、 **model** データベースの復旧モデルを確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c454d-145">This example shows how to query the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view to learn the recovery model of the **model** database.</span></span>  
  
```sql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### <a name="to-change-the-recovery-model"></a><span data-ttu-id="c454d-146">復旧モデルを変更するには</span><span class="sxs-lookup"><span data-stu-id="c454d-146">To change the recovery model</span></span>  
  
1.  <span data-ttu-id="c454d-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="c454d-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c454d-148">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c454d-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c454d-149">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c454d-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c454d-150">この例では、 `model` ALTER DATABASE `FULL` ステートメントの `SET RECOVERY` オプションを使用して、 [データベース内の復旧モデルを](/sql/t-sql/statements/alter-database-transact-sql-set-options) に変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c454d-150">This example shows how to change the recovery model in the `model` database to `FULL` by using the `SET RECOVERY` option of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement.</span></span>  
  
```sql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="follow-up-recommendations-after-you-change-the-recovery-model"></a><a name="FollowUp"></a><span data-ttu-id="c454d-151">フォローアップに関する推奨事項: 復旧モデルを変更した後</span><span class="sxs-lookup"><span data-stu-id="c454d-151">Follow Up Recommendations: After You Change the Recovery Model</span></span>  
  
-   <span data-ttu-id="c454d-152">**完全復旧モデルと一括ログ復旧モデルの切り替え後の処理**</span><span class="sxs-lookup"><span data-stu-id="c454d-152">**After switching between the full and bulk-logged recovery models**</span></span>  
  
    -   <span data-ttu-id="c454d-153">一括操作の完了後、すぐに完全復旧モードに戻してください。</span><span class="sxs-lookup"><span data-stu-id="c454d-153">After completing the bulk operations, immediately switch back to full recovery mode.</span></span>  
  
    -   <span data-ttu-id="c454d-154">一括ログ復旧モデルから完全復旧モデルに戻した後に、ログをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="c454d-154">After switching from the bulk-logged recovery model back to the full recovery model, back up the log.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c454d-155">バックアップ ストラテジは変更されません。つまり、データベースのバックアップ、ログ バックアップ、および差分バックアップが引き続き定期的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c454d-155">Your backup strategy remains the same: continue performing periodic database, log, and differential backups.</span></span>  
  
-   <span data-ttu-id="c454d-156">**単純復旧モデルからの切り替え後の処理**</span><span class="sxs-lookup"><span data-stu-id="c454d-156">**After switching from the simple recovery model**</span></span>  
  
    -   <span data-ttu-id="c454d-157">完全復旧モデルまたは一括ログ復旧モデルに切り替えた直後に、データベースの完全バックアップまたはデータベースの差分バックアップを作成し、ログ チェーンを開始します。</span><span class="sxs-lookup"><span data-stu-id="c454d-157">Immediately after switching to the full recovery model or bulk-logged recovery model, take a full or differential database backup to start the log chain.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c454d-158">完全復旧モデルまたは一括ログ復旧モデルへの切り替えは、最初のデータ バックアップ後に有効になります。</span><span class="sxs-lookup"><span data-stu-id="c454d-158">The switch to the full or bulk-logged recovery model takes effect only after the first data backup.</span></span>  
  
    -   <span data-ttu-id="c454d-159">定期的なログ バックアップをスケジュールし、それに応じて復元プランを更新します。</span><span class="sxs-lookup"><span data-stu-id="c454d-159">Schedule regular log backups, and update your restore plan accordingly.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="c454d-160">ログのバックアップ頻度が不十分な場合、トランザクション ログが拡大し、領域不足になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c454d-160">If you do not back up the log frequently enough, the transaction log can expand until it runs out of disk space.</span></span>  
  
-   <span data-ttu-id="c454d-161">**単純復旧モデルへの切り替え後の処理**</span><span class="sxs-lookup"><span data-stu-id="c454d-161">**After switching to the simple recovery model**</span></span>  
  
    -   <span data-ttu-id="c454d-162">トランザクション ログをバックアップするためのスケジュールが設定されたすべてのジョブを停止します。</span><span class="sxs-lookup"><span data-stu-id="c454d-162">Discontinue any scheduled jobs for backing up the transaction log.</span></span>  
  
    -   <span data-ttu-id="c454d-163">定期的なデータベースのバックアップがスケジュールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c454d-163">Ensure periodic database backups are scheduled.</span></span> <span data-ttu-id="c454d-164">データの保護と、トランザクション ログのアクティブでない部分の切り捨ての両方にとって、データベースのバックアップは重要です。</span><span class="sxs-lookup"><span data-stu-id="c454d-164">Backing up your database is essential both to protect your data and to truncate the inactive portion of the transaction log.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c454d-165">関連タスク</span><span class="sxs-lookup"><span data-stu-id="c454d-165">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c454d-166">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c454d-166">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="c454d-167">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c454d-167">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="c454d-168">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="c454d-168">Create a Job</span></span>](../../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="c454d-169">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="c454d-169">Disable or Enable a Job</span></span>](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="c454d-170">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="c454d-170">Related Content</span></span>  
  
-   <span data-ttu-id="c454d-171">[メンテナンス プラン](../maintenance-plans/maintenance-plans.md) ( [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] オンライン ブック)</span><span class="sxs-lookup"><span data-stu-id="c454d-171">[Database Maintenance Plans](../maintenance-plans/maintenance-plans.md) (in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c454d-172">参照</span><span class="sxs-lookup"><span data-stu-id="c454d-172">See Also</span></span>  
 <span data-ttu-id="c454d-173">[復旧モデル &#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c454d-173">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="c454d-174">[トランザクション ログ &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c454d-174">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="c454d-175">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c454d-175">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="c454d-176">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c454d-176">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="c454d-177">復旧モデル &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c454d-177">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
