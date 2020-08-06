---
title: データベースの差分バックアップの復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- restoring databases [SQL Server], full differential backups
- database backups [SQL Server], full differential backups
- database restores [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
ms.assetid: 0dd971a4-ee38-4dd3-9f30-ef77fc58dd11
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8eab18d84efc1a990715e0d5488085252f93a7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643427"
---
# <a name="restore-a-differential-database-backup-sql-server"></a><span data-ttu-id="62d81-102">データベースの差分バックアップの復元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="62d81-102">Restore a Differential Database Backup (SQL Server)</span></span>
  <span data-ttu-id="62d81-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースの差分バックアップを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="62d81-103">This topic describes how to restore a differential database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="62d81-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="62d81-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="62d81-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="62d81-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="62d81-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="62d81-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="62d81-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="62d81-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="62d81-108">Security</span><span class="sxs-lookup"><span data-stu-id="62d81-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="62d81-109">**データベースの差分バックアップを復元する方法:**</span><span class="sxs-lookup"><span data-stu-id="62d81-109">**To restore a differential database backup, using:**</span></span>  
  
     [<span data-ttu-id="62d81-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="62d81-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="62d81-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="62d81-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="62d81-112">関連タスク</span><span class="sxs-lookup"><span data-stu-id="62d81-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="62d81-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="62d81-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="62d81-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="62d81-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="62d81-115">RESTORE は、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="62d81-115">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="62d81-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって作成されたバックアップは、それより前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では復元できません。</span><span class="sxs-lookup"><span data-stu-id="62d81-116">Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="62d81-117">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンを使用して作成したデータベース バックアップからユーザー データベースを復元できます。</span><span class="sxs-lookup"><span data-stu-id="62d81-117">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can restore a user database from a database backup that was created by using [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="62d81-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="62d81-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="62d81-119">完全復旧モデルまたは一括ログ復旧モデルを使用する場合は、データベースを復旧する前に、ログの末尾と呼ばれるアクティブ トランザクション ログをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="62d81-119">Under the full or bulk-logged recovery model, before you can restore a database, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="62d81-120">詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d81-120">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="62d81-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="62d81-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="62d81-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="62d81-122">Permissions</span></span>  
 <span data-ttu-id="62d81-123">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62d81-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="62d81-124">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="62d81-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="62d81-125">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="62d81-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="62d81-126">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="62d81-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="62d81-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="62d81-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-differential-database-backup"></a><span data-ttu-id="62d81-128">データベースの差分バックアップを復元するには</span><span class="sxs-lookup"><span data-stu-id="62d81-128">To restore a differential database backup</span></span>  
  
1.  <span data-ttu-id="62d81-129">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の適切なインスタンスに接続後、オブジェクト エクスプローラーでサーバー名をクリックして、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="62d81-129">After you connect to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="62d81-130">**[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="62d81-130">Expand **Databases**.</span></span> <span data-ttu-id="62d81-131">復元するデータベースに応じて、ユーザー データベースを選択するか、 **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="62d81-131">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="62d81-132">データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をポイントして、 **[データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62d81-132">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Database**.</span></span>  
  
4.  <span data-ttu-id="62d81-133">**[全般]** ページの **復元元**のセクションを使用して、復元するバックアップ セットの復元元ファイルと場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="62d81-133">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="62d81-134">以下のオプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="62d81-134">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="62d81-135">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="62d81-135">**Database**</span></span>  
  
         <span data-ttu-id="62d81-136">復元するデータベースをドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="62d81-136">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="62d81-137">このリストには、 **msdb** バックアップ履歴に従ってバックアップされたデータベースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="62d81-137">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62d81-138">別のサーバーで作成されたバックアップの場合、復元先のサーバーには指定されたデータベースのバックアップ履歴情報が存在しません。</span><span class="sxs-lookup"><span data-stu-id="62d81-138">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="62d81-139">この場合、 **[デバイス]** をクリックして、復元するファイルまたはデバイスを手動で指定します。</span><span class="sxs-lookup"><span data-stu-id="62d81-139">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    -   <span data-ttu-id="62d81-140">**[デバイス]**</span><span class="sxs-lookup"><span data-stu-id="62d81-140">**Device**</span></span>  
  
         <span data-ttu-id="62d81-141">参照ボタン ( **[...]** ) をクリックし、 **[バックアップ デバイスの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="62d81-141">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="62d81-142">**[バックアップ メディアの種類]** ボックスから、デバイスの種類を 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="62d81-142">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="62d81-143">**[バックアップ メディア]** ボックスにデバイスを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62d81-143">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="62d81-144">**[バックアップ メディア]** ボックスに目的のデバイスを追加したら、 **[OK]** をクリックして、 **[全般]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="62d81-144">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="62d81-145">**[ソース: デバイス:データベース]** リスト ボックスで、復元するデータベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="62d81-145">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="62d81-146">**メモ** この一覧は **[デバイス]** をクリックした場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="62d81-146">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="62d81-147">選択されたデバイスにバックアップを持つデータベースのみが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="62d81-147">Only databases that have backups on the selected device will be available.</span></span>  
  
5.  <span data-ttu-id="62d81-148">**復元先のセクション**の **[データベース]** ボックスに、復元するデータベースの名前が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="62d81-148">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="62d81-149">データベースの名前を変更するには、 **[データベース]** ボックスに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="62d81-149">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62d81-150">特定の時点で復元を停止するには、 **[タイムライン]** をクリックして、 **[バックアップのタイムライン]** ダイアログ ボックスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="62d81-150">To stop the restore at a specific point in time, click **Timeline** to access the **Backup Timeline** dialog box.</span></span> <span data-ttu-id="62d81-151">特定の時点でデータベースの復元を停止する方法については、「[SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d81-151">For help with stopping a database restore at a specific point in time, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
6.  <span data-ttu-id="62d81-152">**[復元するバックアップ セット]** グリッドで、差分バックアップを通じて復元するバックアップを選択します。</span><span class="sxs-lookup"><span data-stu-id="62d81-152">In the **Backup sets to restore** grid, select the backups through the differential backup that you wish to restore.</span></span>  
  
     <span data-ttu-id="62d81-153">**[復元するバックアップ セット]** グリッドの列の詳細については、「[データベースの復元 &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d81-153">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
7.  <span data-ttu-id="62d81-154">**[オプション]** ページの **[復元オプション]** パネルでは、状況に応じて、次の任意のオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="62d81-154">On the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:</span></span>  
  
    -   <span data-ttu-id="62d81-155">**[既存のデータベースを上書きする (WITH REPLACE)]**</span><span class="sxs-lookup"><span data-stu-id="62d81-155">**Overwrite the existing database (WITH REPLACE)**</span></span>  
  
    -   <span data-ttu-id="62d81-156">**[レプリケーションの設定を保存する (WITH KEEP_REPLICATION)]**</span><span class="sxs-lookup"><span data-stu-id="62d81-156">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
    -   <span data-ttu-id="62d81-157">**[各バックアップを復元する前に確認する]**</span><span class="sxs-lookup"><span data-stu-id="62d81-157">**Prompt before restoring each backup**</span></span>  
  
    -   <span data-ttu-id="62d81-158">**[復元するデータベースへのアクセスを制限する (WITH RESTRICTED_USER)]**</span><span class="sxs-lookup"><span data-stu-id="62d81-158">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
     <span data-ttu-id="62d81-159">これらのオプションの詳細については、「[データベースの復元 &#40;[オプション] ページ&#41;](restore-database-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d81-159">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
8.  <span data-ttu-id="62d81-160">**[復旧状態]** ボックスのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="62d81-160">Select an option for the **Recovery state** box.</span></span> <span data-ttu-id="62d81-161">このボックスの選択内容により、復元操作後のデータベースの状態が決まります。</span><span class="sxs-lookup"><span data-stu-id="62d81-161">This box determines the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="62d81-162">**[RESTORE WITH RECOVERY]** : コミットされていないトランザクションをロールバックして、データベースを使用可能な状態にします。これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="62d81-162">**RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions.</span></span> <span data-ttu-id="62d81-163">別のトランザクション ログは復元できません。</span><span class="sxs-lookup"><span data-stu-id="62d81-163">Additional transaction logs cannot be restored.</span></span> <span data-ttu-id="62d81-164">このオプションは、必要なバックアップをすべて復元する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="62d81-164">Select this option if you are restoring all of the necessary backups now.</span></span>  
  
    -   <span data-ttu-id="62d81-165">**[RESTORE WITH NORECOVERY]** : データベースは操作不可状態のままとなり、コミットされていないトランザクションはロールバックされません。</span><span class="sxs-lookup"><span data-stu-id="62d81-165">**RESTORE WITH NORECOVERY** which leaves the database non-operational, and does not roll back the uncommitted transactions.</span></span> <span data-ttu-id="62d81-166">別のトランザクション ログは復元できます</span><span class="sxs-lookup"><span data-stu-id="62d81-166">Additional transaction logs can be restored.</span></span> <span data-ttu-id="62d81-167">データベースは、復旧されるまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="62d81-167">The database cannot be used until it is recovered.</span></span>  
  
    -   <span data-ttu-id="62d81-168">**[RESTORE WITH STANDBY]** : データベースを読み取り専用モードにします。</span><span class="sxs-lookup"><span data-stu-id="62d81-168">**RESTORE WITH STANDBY** which leaves the database in read-only mode.</span></span> <span data-ttu-id="62d81-169">コミットされていないトランザクションは元に戻されますが、復旧結果を元に戻せるように元に戻す操作をスタンバイ ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="62d81-169">It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.</span></span>  
  
     <span data-ttu-id="62d81-170">オプションの詳細については、「[データベースの復元 &#40;[オプション] ページ&#41;](restore-database-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d81-170">For descriptions of the options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
9. <span data-ttu-id="62d81-171">データベースへのアクティブな接続がある場合、復元操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="62d81-171">Restore operations will fail if there are active connections to the database.</span></span> <span data-ttu-id="62d81-172">**とデータベース間のすべてのアクティブな接続を閉じるには、** [既存の接続を閉じる] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] オプションをオンにします。</span><span class="sxs-lookup"><span data-stu-id="62d81-172">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span>  
  
10. <span data-ttu-id="62d81-173">復元操作と復元操作の間に、その都度、確認のメッセージを表示するには、 **[各バックアップを復元する前に確認する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="62d81-173">Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation.</span></span> <span data-ttu-id="62d81-174">通常は、その必要はありません。データベースが大きく、復元操作のステータスを監視する必要がある場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="62d81-174">This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.</span></span>  
  
11. <span data-ttu-id="62d81-175">(省略可) データベースを新しい場所に復元するには、 **[ファイル]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="62d81-175">Optionally, use the **Files** page to restore the database to a new location.</span></span> <span data-ttu-id="62d81-176">データベースの移動に関する詳細については、「[データベースを新しい場所に復元する &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d81-176">For help with moving a database, see [Restore a Database to a New Location &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md).</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="62d81-177">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="62d81-177">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-differential-database-backup"></a><span data-ttu-id="62d81-178">データベースの差分バックアップを復元するには</span><span class="sxs-lookup"><span data-stu-id="62d81-178">To restore a differential database backup</span></span>  
  
1.  <span data-ttu-id="62d81-179">NORECOVERY 句を指定して RESTORE DATABASE ステートメントを実行し、データベースの差分バックアップの前に、データベースの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="62d81-179">Execute the RESTORE DATABASE statement, specifying the NORECOVERY clause, to restore the full database backup that comes before the differential database backup.</span></span> <span data-ttu-id="62d81-180">詳細については、「[完全バックアップの復元](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d81-180">For more information, see [How to: Restore a Full Backup](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="62d81-181">RESTORE DATABASE ステートメントを実行して、データベースの差分バックアップを復元します。そのとき、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="62d81-181">Execute the RESTORE DATABASE statement to restore the differential database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="62d81-182">データベースの差分バックアップを適用するデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="62d81-182">The name of the database to which the differential database backup is applied.</span></span>  
  
    -   <span data-ttu-id="62d81-183">データベースの差分バックアップの復元元であるバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="62d81-183">The backup device where the differential database backup is restored from.</span></span>  
  
    -   <span data-ttu-id="62d81-184">NORECOVERY 句。データベースの差分バックアップを復元した後、適用するトランザクション ログ バックアップがある場合に指定します。</span><span class="sxs-lookup"><span data-stu-id="62d81-184">The NORECOVERY clause if you have transaction log backups to apply after the differential database backup is restored.</span></span> <span data-ttu-id="62d81-185">それ以外の場合は、RECOVERY 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="62d81-185">Otherwise, specify the RECOVERY clause.</span></span>  
  
3.  <span data-ttu-id="62d81-186">完全復旧モデルでも、一括ログ復旧モデルでも、データベースの差分バックアップの復元では、データベースの差分バックアップが完了した時点にデータベースが復元されます。</span><span class="sxs-lookup"><span data-stu-id="62d81-186">With the full or bulk-logged recovery model, restoring a differential database backup restores the database to the point at which the differential database backup was completed.</span></span> <span data-ttu-id="62d81-187">障害の時点にさかのぼってデータベースを復旧するには、直前のデータベースの差分バックアップを作成した後に生成されたすべてのトランザクション ログ バックアップを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62d81-187">To recover to the point of failure, you must apply all transaction log backups created after the last differential database backup was created.</span></span> <span data-ttu-id="62d81-188">詳細については、「[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d81-188">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="62d81-189">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="62d81-189">Examples (Transact-SQL)</span></span>  
  
#### <a name="a-restoring-a-differential-database-backup"></a><span data-ttu-id="62d81-190">A.</span><span class="sxs-lookup"><span data-stu-id="62d81-190">A.</span></span> <span data-ttu-id="62d81-191">データベースの差分バックアップの復元</span><span class="sxs-lookup"><span data-stu-id="62d81-191">Restoring a differential database backup</span></span>  
 <span data-ttu-id="62d81-192">この例では、 `MyAdvWorks` データベースのデータベース バックアップおよびデータベースの差分バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="62d81-192">This example restores a database and differential database backup of the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Assume the database is lost, and restore full database,   
-- specifying the original full database backup and NORECOVERY,   
-- which allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   RECOVERY;  
GO  
```  
  
#### <a name="b-restoring-a-database-differential-database-and-transaction-log-backup"></a><span data-ttu-id="62d81-193">B.</span><span class="sxs-lookup"><span data-stu-id="62d81-193">B.</span></span> <span data-ttu-id="62d81-194">データベース バックアップ、データベースの差分バックアップ、およびトランザクション ログ バックアップの復元</span><span class="sxs-lookup"><span data-stu-id="62d81-194">Restoring a database, differential database, and transaction log backup</span></span>  
 <span data-ttu-id="62d81-195">この例では、 `MyAdvWorks` データベースのデータベース バックアップ、データベースの差分バックアップ、およびトランザクション ログ バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="62d81-195">This example restores a database, differential database, and transaction log backup of the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Assume the database is lost at this point. Now restore the full   
-- database. Specify the original full database backup and NORECOVERY.  
-- NORECOVERY allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   NORECOVERY;  
GO  
-- Now restore each transaction log backup created after  
-- the differential database backup.  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log1  
   WITH NORECOVERY;  
GO  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log2  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="62d81-196">関連タスク</span><span class="sxs-lookup"><span data-stu-id="62d81-196">Related Tasks</span></span>  
  
-   [<span data-ttu-id="62d81-197">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="62d81-197">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="62d81-198">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="62d81-198">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="62d81-199">参照</span><span class="sxs-lookup"><span data-stu-id="62d81-199">See Also</span></span>  
 <span data-ttu-id="62d81-200">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="62d81-200">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="62d81-201">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="62d81-201">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
