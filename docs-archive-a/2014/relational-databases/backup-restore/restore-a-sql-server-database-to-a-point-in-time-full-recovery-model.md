---
title: SQL Server データベースを特定の時点に復元する方法 (完全復旧モデル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- STOPAT clause [RESTORE LOG statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
ms.assetid: 3a5daefd-08a8-4565-b54f-28ad01a47d32
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c71ff6e75cbbf27042c1eac70b1f97076290865
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643426"
---
# <a name="restore-a-sql-server-database-to-a-point-in-time-full-recovery-model"></a><span data-ttu-id="f9e2c-102">SQL Server データベースを特定の時点に復元する方法 (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="f9e2c-102">Restore a SQL Server Database to a Point in Time (Full Recovery Model)</span></span>
  <span data-ttu-id="f9e2c-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベースを特定の時点まで復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-103">This topic describes how to restore a database to a point in time in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f9e2c-104">このトピックは、完全復旧モデルまたは一括ログ復旧モデルを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにのみ関連しています。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-104">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that use the full or bulk-logged recovery models.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f9e2c-105">一括ログ復旧モデルでは、ログ バックアップに一括ログ記録された変更内容が含まれていると、そのバックアップ内の特定の時点への復旧を行うことができません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-105">Under the bulk-logged recovery model, if a log backup contains bulk-logged changes, point-in-time recovery is not possible to a point within that backup.</span></span> <span data-ttu-id="f9e2c-106">データベースは、トランザクション ログ バックアップの終了時点へ復旧する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-106">The database must be recovered to the end of the transaction log backup.</span></span>  
  
-   <span data-ttu-id="f9e2c-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f9e2c-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="f9e2c-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f9e2c-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f9e2c-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f9e2c-110">**SQL Server データベースを特定の時点まで復元する場合に使用するツール:**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-110">**To restore a SQL Server database to a point in time, using:**</span></span>  
  
     [<span data-ttu-id="f9e2c-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f9e2c-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f9e2c-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f9e2c-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f9e2c-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="f9e2c-113">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f9e2c-114">推奨事項</span><span class="sxs-lookup"><span data-stu-id="f9e2c-114">Recommendations</span></span>  
  
-   <span data-ttu-id="f9e2c-115">特定の復元時点が不明な場合の STANDBY を使用した検索</span><span class="sxs-lookup"><span data-stu-id="f9e2c-115">Use STANDBY to find unknown point in time.</span></span>  
  
-   <span data-ttu-id="f9e2c-116">復元シーケンスの早い段階での特定時点の指定</span><span class="sxs-lookup"><span data-stu-id="f9e2c-116">Specify the point in time early in a restore sequence</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f9e2c-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f9e2c-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f9e2c-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="f9e2c-118">Permissions</span></span>  
 <span data-ttu-id="f9e2c-119">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-119">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="f9e2c-120">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-120">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="f9e2c-121">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-121">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="f9e2c-122">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-122">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f9e2c-123">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f9e2c-123">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f9e2c-124">**特定の時点にデータベースを復元するには**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-124">**To restore a database to a point in time**</span></span>  
  
1.  <span data-ttu-id="f9e2c-125">オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の適切なインスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-125">In Object Explorer, connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f9e2c-126">**[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-126">Expand **Databases**.</span></span> <span data-ttu-id="f9e2c-127">復元するデータベースに応じて、ユーザー データベースを選択するか、 **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-127">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="f9e2c-128">データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をポイントして、 **[データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-128">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Database**.</span></span>  
  
4.  <span data-ttu-id="f9e2c-129">**[全般]** ページの **復元元**のセクションを使用して、復元するバックアップ セットの復元元ファイルと場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-129">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="f9e2c-130">以下のオプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-130">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="f9e2c-131">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-131">**Database**</span></span>  
  
         <span data-ttu-id="f9e2c-132">復元するデータベースをドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-132">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="f9e2c-133">このリストには、 **msdb** バックアップ履歴に従ってバックアップされたデータベースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-133">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9e2c-134">別のサーバーで作成されたバックアップの場合、復元先のサーバーには指定されたデータベースのバックアップ履歴情報が存在しません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-134">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="f9e2c-135">この場合、 **[デバイス]** をクリックして、復元するファイルまたはデバイスを手動で指定します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-135">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    -   <span data-ttu-id="f9e2c-136">**[デバイス]**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-136">**Device**</span></span>  
  
         <span data-ttu-id="f9e2c-137">参照ボタン ( **[...]** ) をクリックし、 **[バックアップ デバイスの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-137">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="f9e2c-138">**[バックアップ メディアの種類]** ボックスから、デバイスの種類を 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-138">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="f9e2c-139">**[バックアップ メディア]** ボックスにデバイスを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-139">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="f9e2c-140">**[バックアップ メディア]** ボックスに目的のデバイスを追加したら、 **[OK]** をクリックして、 **[全般]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-140">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="f9e2c-141">**[ソース: デバイス: データベース]** ボックスの一覧で、復元するデータベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-141">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="f9e2c-142">**メモ** この一覧は **[デバイス]** をクリックした場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-142">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="f9e2c-143">選択されたデバイスにバックアップを持つデータベースのみが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-143">Only databases that have backups on the selected device will be available.</span></span>  
  
5.  <span data-ttu-id="f9e2c-144">**復元先のセクション**の **[データベース]** ボックスに、復元するデータベースの名前が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-144">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="f9e2c-145">データベースの名前を変更するには、 **[データベース]** ボックスに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-145">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
6.  <span data-ttu-id="f9e2c-146">**[タイムライン]** をクリックして、 **[バックアップのタイムライン]** ダイアログ ボックスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-146">Click **Timeline** to access the **Backup Timeline** dialog box.</span></span>  
  
7.  <span data-ttu-id="f9e2c-147">**[復元先]** セクションで、 **[特定の日付と時刻]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-147">In the **Restore to** section, click **Specific date and time**.</span></span>  
  
8.  <span data-ttu-id="f9e2c-148">**[日付]** と **[時刻]** ボックスを使用するか、スライダー バーを使用して、復元を止める特定の日付と時刻を指定します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-148">Use either the **Date** and **Time** boxes or the slider bar to specify a specific date and time to where the restore should stop.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9e2c-149">**[タイムラインの間隔]** ボックスを使用して、タイムラインに表示される時間を変更します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-149">Use the **Timeline Interval** box to change the amount of time displayed on the timeline.</span></span>  
  
9. <span data-ttu-id="f9e2c-150">特定の時点を指定すると、データベース復旧アドバイザーによって、その特定の時点に復元するために必要なバックアップだけが **[復元するバックアップ セット]** グリッドの **[復元]** 列で選択されます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-150">After you have specified a specific point in time, the Database Recovery Advisor ensures that only backups that are required for restoring to that point in time are selected in the **Restore** column of the **Backup sets to restore** grid.</span></span> <span data-ttu-id="f9e2c-151">これらの選択されたバックアップは、特定の時点への復元用として推奨される復元プランを示しています。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-151">These selected backups make up the recommended restore plan for your point-in-time restore.</span></span> <span data-ttu-id="f9e2c-152">特定の時点への復元操作には選択されているバックアップのみを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-152">You should use only the selected backups for your point-in-time restore operation.</span></span>  
  
     <span data-ttu-id="f9e2c-153">**[復元するバックアップ セット]** グリッドの列の詳細については、「[データベースの復元 &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-153">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span> <span data-ttu-id="f9e2c-154">データベースの復旧アドバイザーの詳細については、「[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-154">For information about the Database Recovery Advisor, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
10. <span data-ttu-id="f9e2c-155">**[オプション]** ページの **[復元オプション]** パネルでは、状況に応じて、次の任意のオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-155">On the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:</span></span>  
  
    -   <span data-ttu-id="f9e2c-156">**[既存のデータベースを上書きする (WITH REPLACE)]**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-156">**Overwrite the existing database (WITH REPLACE)**</span></span>  
  
    -   <span data-ttu-id="f9e2c-157">**[レプリケーションの設定を保存する (WITH KEEP_REPLICATION)]**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-157">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
    -   <span data-ttu-id="f9e2c-158">**[復元するデータベースへのアクセスを制限する (WITH RESTRICTED_USER)]**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-158">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
     <span data-ttu-id="f9e2c-159">これらのオプションの詳細については、「[データベースの復元 &#40;[オプション] ページ&#41;](restore-database-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-159">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
11. <span data-ttu-id="f9e2c-160">**[復旧状態]** ボックスのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-160">Select an option for the **Recovery state** box.</span></span> <span data-ttu-id="f9e2c-161">このボックスの選択内容により、復元操作後のデータベースの状態が決まります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-161">This box determines the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="f9e2c-162">**[RESTORE WITH RECOVERY]** : コミットされていないトランザクションをロールバックして、データベースを使用可能な状態にします。これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-162">**RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions.</span></span> <span data-ttu-id="f9e2c-163">別のトランザクション ログは復元できません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-163">Additional transaction logs cannot be restored.</span></span> <span data-ttu-id="f9e2c-164">このオプションは、必要なバックアップをすべて復元する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-164">Select this option if you are restoring all of the necessary backups now.</span></span>  
  
    -   <span data-ttu-id="f9e2c-165">**[RESTORE WITH NORECOVERY]** : データベースは操作不可状態のままとなり、コミットされていないトランザクションはロールバックされません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-165">**RESTORE WITH NORECOVERY** which leaves the database non-operational, and does not roll back the uncommitted transactions.</span></span> <span data-ttu-id="f9e2c-166">別のトランザクション ログは復元できます</span><span class="sxs-lookup"><span data-stu-id="f9e2c-166">Additional transaction logs can be restored.</span></span> <span data-ttu-id="f9e2c-167">データベースは、復旧されるまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-167">The database cannot be used until it is recovered.</span></span>  
  
    -   <span data-ttu-id="f9e2c-168">**[RESTORE WITH STANDBY]** : データベースを読み取り専用モードにします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-168">**RESTORE WITH STANDBY** which leaves the database in read-only mode.</span></span> <span data-ttu-id="f9e2c-169">コミットされていないトランザクションは元に戻されますが、復旧結果を元に戻せるように元に戻す操作をスタンバイ ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-169">It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.</span></span>  
  
     <span data-ttu-id="f9e2c-170">オプションの詳細については、「[データベースの復元 &#40;[オプション] ページ&#41;](restore-database-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-170">For descriptions of the options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
12. <span data-ttu-id="f9e2c-171">選択した時点まで復元するために必要であれば、 **[復元の前にログ末尾のバックアップを実行する]** が選択されます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-171">**Take tail-log backup before restore** will be selected if it is necessary for the point in time that you have selected.</span></span> <span data-ttu-id="f9e2c-172">この設定を変更する必要はありません。ログの末尾をバックアップする必要がない場合でも、そのように選択してかまいません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-172">You do not need to modify this setting, but you can choose to backup the tail of the log even if it is not required.</span></span>  
  
13. <span data-ttu-id="f9e2c-173">データベースへのアクティブな接続がある場合、復元操作は失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-173">Restore operations may fail if there are active connections to the database.</span></span> <span data-ttu-id="f9e2c-174">**とデータベース間のすべてのアクティブな接続を閉じるには、** [既存の接続を閉じる] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] オプションをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-174">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span> <span data-ttu-id="f9e2c-175">このチェック ボックスをオンにすると、データベースは復元操作の実行前にシングル ユーザー モードに設定され、復元操作の完了後にマルチユーザー モードに設定されます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-175">This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.</span></span>  
  
14. <span data-ttu-id="f9e2c-176">復元操作と復元操作の間に、その都度、確認のメッセージを表示するには、 **[各バックアップを復元する前に確認する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-176">Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation.</span></span> <span data-ttu-id="f9e2c-177">通常は、その必要はありません。データベースが大きく、復元操作のステータスを監視する必要がある場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-177">This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f9e2c-178">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f9e2c-178">Using Transact-SQL</span></span>  
 <span data-ttu-id="f9e2c-179">**Before you begin**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-179">**Before you begin**</span></span>  
  
 <span data-ttu-id="f9e2c-180">指定した時点への復元は、常にログ バックアップから行われます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-180">A specified time is always restored from a log backup.</span></span> <span data-ttu-id="f9e2c-181">復元シーケンスのすべての RESTORE ステートメントで、同一の STOPAT 句で目的の時点またはトランザクションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-181">In every RESTORE LOG statement of the restore sequence, you must specify your target time or transaction in an identical STOPAT clause.</span></span> <span data-ttu-id="f9e2c-182">特定の時点への復元の前提条件として、最初にエンド ポイントが目的の復元時点よりも前になっているデータベースの完全バックアップを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-182">As a prerequisite to a point-in-time restore, you must first restore a full database backup whose end point is earlier than your target restore time.</span></span> <span data-ttu-id="f9e2c-183">このデータベースの完全バックアップは、データベースの最新の完全バックアップより古くてもかまいません。ただし、これは、データベースの完全バックアップを復元した後で、目的の時点を含むログ バックアップまで後続のログ バックアップをすべて復元する場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-183">That full database backup can be older than the most recent full database backup as long as you then restore every subsequent log backup, up to and including the log backup that contains your target point in time.</span></span>  
  
 <span data-ttu-id="f9e2c-184">復元するデータベース バックアップを識別しやすくするには、RESTORE DATABASE ステートメントで WITH STOPAT 句をオプションで指定し、指定した目的の時点に対してデータのバックアップが近すぎる場合はエラーが発生するようにします。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-184">To help you identify which database backup to restore, you can optionally specify your WITH STOPAT clause in your RESTORE DATABASE statement to raise an error if a data backup is too recent for the specified target time.</span></span> <span data-ttu-id="f9e2c-185">データ バックアップに目的の時点が含まれている場合でも、常にデータ バックアップ全体が復元されます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-185">The complete data backup is always restored, even if it contains the target time.</span></span>  
  
 <span data-ttu-id="f9e2c-186">**[!INCLUDE[tsql](../../includes/tsql-md.md)] の基本構文**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-186">**Basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax**</span></span>  
  
 <span data-ttu-id="f9e2c-187">STOPAT \*\* = *`time`* 、\*\* RECOVERY... を使用して <backup_device> からログ*database_name*を復元します...</span><span class="sxs-lookup"><span data-stu-id="f9e2c-187">RESTORE LOG *database_name* FROM <backup_device> WITH STOPAT **=*`time`*,** RECOVERY...</span></span>  
  
 <span data-ttu-id="f9e2c-188">復旧ポイントは、 `datetime` *time*によって指定された値以前に発生した最新のトランザクションコミットです。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-188">The recovery point is the latest transaction commit that occurred at or before the `datetime` value that is specified by *time*.</span></span>  
  
 <span data-ttu-id="f9e2c-189">特定の時点より前に行われた変更のみを復元するには、復元するバックアップごとに WITH STOPAT **=** *time* を指定します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-189">To restore only the modifications that were made before a specific point in time, specify WITH STOPAT **=** *time* for each backup you restore.</span></span> <span data-ttu-id="f9e2c-190">これにより、目的の時点を過ぎる危険性を回避できます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-190">This makes sure that you do not go past the target time.</span></span>  
  
 <span data-ttu-id="f9e2c-191">**特定の時点にデータベースを復元するには**</span><span class="sxs-lookup"><span data-stu-id="f9e2c-191">**To restore a database to a point in time**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9e2c-192">この手順の例については、このセクションの後半の「 [例 (Transact-SQL)](#TsqlExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-192">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="f9e2c-193">データベースを復元するサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-193">Connect to server instance on which you want to restore the database.</span></span>  
  
2.  <span data-ttu-id="f9e2c-194">NORECOVERY オプションを指定した RESTORE DATABASE ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-194">Execute the RESTORE DATABASE statement using the NORECOVERY option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9e2c-195">部分復元シーケンスで [FILESTREAM](../blob/filestream-sql-server.md) ファイル グループを除外した場合、特定の時点への復元はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-195">If a partial restore sequence excludes any [FILESTREAM](../blob/filestream-sql-server.md) filegroup, point-in-time restore is not supported.</span></span> <span data-ttu-id="f9e2c-196">復元シーケンスを強制的に実行して続行することもできます。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-196">You can force the restore sequence to continue.</span></span> <span data-ttu-id="f9e2c-197">ただし、RESTORE ステートメントから除外された FILESTREAM ファイル グループは復元できません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-197">However the FILESTREAM filegroups that are omitted from your RESTORE statement can never be restored.</span></span> <span data-ttu-id="f9e2c-198">特定の時点への復元を強制的に実行するには、STOPAT、STOPATMARK、または STOPBEFOREMARK オプションに CONTINUE_AFTER_ERROR オプションを組み合わせて指定します。これらのオプションは、後続の RESTORE LOG ステートメントでも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-198">To force a point-in-time restore, specify the CONTINUE_AFTER_ERROR option together with the STOPAT, STOPATMARK, or STOPBEFOREMARK option, which you must also specify in your subsequent RESTORE LOG statements.</span></span> <span data-ttu-id="f9e2c-199">CONTINUE_AFTER_ERROR を指定した場合、部分復元シーケンスは正常に実行されますが、FILESTREAM ファイル グループは復元できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-199">If you specify CONTINUE_AFTER_ERROR, the partial restore sequence succeeds and the FILESTREAM filegroup becomes unrecoverable.</span></span>  
  
3.  <span data-ttu-id="f9e2c-200">差分バックアップが存在する場合、データベースを復旧せずに最新のデータベースの差分バックアップを復元します (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-200">Restore the last differential database backup, if any,  without recovering the database (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span></span>  
  
4.  <span data-ttu-id="f9e2c-201">各トランザクションログバックアップを作成時と同じ順序で適用し、ログの復元を停止する時点を指定します (<backup_device> から STOPAT\*\* = *`time`* 、\*\* RECOVERY を使用してデータベース*database_name*を復元します)。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-201">Apply each transaction log backup in the same sequence in which they were created, specifying the time at which you intend to stop restoring log (RESTORE DATABASE *database_name* FROM <backup_device> WITH STOPAT**=*`time`*,** RECOVERY).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9e2c-202">RECOVERY オプションと STOPAT オプション。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-202">The RECOVERY and STOPAT options.</span></span> <span data-ttu-id="f9e2c-203">トランザクション ログ バックアップに、要求した時点の情報が格納されていない場合、たとえば、指定した日時がトランザクション ログに記録されている時点より後の場合などに、警告が生成されます。この場合、データベースは復旧されません。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-203">If the transaction log backup does not contain the requested time (for example, if the time specified is beyond the end of the time covered by the transaction log), a warning is generated and the database remains unrecovered.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f9e2c-204">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f9e2c-204">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f9e2c-205">次の例では、データベースを `12:00 AM``April 15, 2020` の状態に復元し、複数のログ バックアップが関連する復元操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-205">The following example restores a database to its state as of `12:00 AM` on `April 15, 2020` and shows a restore operation that involves multiple log backups.</span></span> <span data-ttu-id="f9e2c-206">バックアップ デバイス `AdventureWorksBackups`において、復元するデータベース全体のバックアップはデバイス上の 3 番目のバックアップ セット (`FILE = 3`)、最初のログ バックアップは 4 番目のバックアップ セット (`FILE = 4`)、2 番目のログ バックアップは 5 番目のバックアップ セット (`FILE = 5`) です。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-206">On the backup device, `AdventureWorksBackups`, the full database backup to be restored is the third backup set on the device (`FILE = 3`), the first log backup is the fourth backup set (`FILE = 4`), and the second log backup is the fifth backup set (`FILE = 5`).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f9e2c-207">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースは、単純復旧モデルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-207">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database uses the simple recovery model.</span></span> <span data-ttu-id="f9e2c-208">ただし、ログ バックアップを可能にするために、データベースの完全バックアップを行う前に、 `ALTER DATABASE AdventureWorks SET RECOVERY FULL`を使用して、データベースが完全復旧モデルを使用するように設定されています。</span><span class="sxs-lookup"><span data-stu-id="f9e2c-208">To permit log backups, before taking a full database backup, the database was set to use the full recovery model, using `ALTER DATABASE AdventureWorks SET RECOVERY FULL`.</span></span>  
  
```  
RESTORE DATABASE AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=3, NORECOVERY;  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=4, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=5, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
RESTORE DATABASE AdventureWorks WITH RECOVERY;   
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f9e2c-209">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f9e2c-209">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f9e2c-210">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f9e2c-210">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="f9e2c-211">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9e2c-211">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="f9e2c-212">完全復旧モデルで障害発生時点までデータベースを復元する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f9e2c-212">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="f9e2c-213">マークされたトランザクションへのデータベースの復元 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f9e2c-213">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f9e2c-214">ログ シーケンス番号への復旧 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9e2c-214">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="f9e2c-215">参照</span><span class="sxs-lookup"><span data-stu-id="f9e2c-215">See Also</span></span>  
 <span data-ttu-id="f9e2c-216">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f9e2c-216">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="f9e2c-217">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f9e2c-217">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="f9e2c-218">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f9e2c-218">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
  
