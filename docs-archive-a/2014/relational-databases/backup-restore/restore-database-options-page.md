---
title: データベースの復元 ([オプション] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.options.f1
ms.assetid: 9a75d48b-c25f-40f3-8ea1-32cfa8211754
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d60474b5d72ab9745500325dfd523f83f155343c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640094"
---
# <a name="restore-database-options-page"></a><span data-ttu-id="af382-102">データベースの復元 ([オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="af382-102">Restore Database (Options Page)</span></span>
  <span data-ttu-id="af382-103">**[データベースの復元]** ダイアログ ボックスの **[オプション]** ページを使用して、復元操作の動作と結果を変更します。</span><span class="sxs-lookup"><span data-stu-id="af382-103">Use the **Options** page of the **Restore Database** dialog box to modify the behavior and outcome of the restore operation.</span></span>  
  
 <span data-ttu-id="af382-104">**SQL Server Management Studio を使用してデータベース バックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="af382-104">**To use SQL Server Management Studio to restore a database backup**</span></span>  
  
-   [<span data-ttu-id="af382-105">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af382-105">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [<span data-ttu-id="af382-106">テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af382-106">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="af382-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して復元タスクを指定するときに、この復元操作の RESTORE ステートメントを含む、対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="af382-107">When you specify a restore task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate a corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] script containing the RESTORE statements for this restore operation.</span></span> <span data-ttu-id="af382-108">このスクリプトを生成するには、 **[スクリプト]** をクリックし、スクリプトの保存先を選択します。</span><span class="sxs-lookup"><span data-stu-id="af382-108">To generate the script, click **Script** and then select a destination for the script.</span></span> <span data-ttu-id="af382-109">RESTORE 構文については、「 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af382-109">For information about the RESTORE syntax, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="af382-110">Options</span><span class="sxs-lookup"><span data-stu-id="af382-110">Options</span></span>  
  
### <a name="restore-options"></a><span data-ttu-id="af382-111">復元オプション</span><span class="sxs-lookup"><span data-stu-id="af382-111">Restore options</span></span>  
 <span data-ttu-id="af382-112">復元操作の動作の特徴を変更するには、 **[復元オプション]** パネルのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="af382-112">To modify aspects of the behavior of the restore operation, use the options of the **Restore options** panel.</span></span>  
  
 <span data-ttu-id="af382-113">**[既存のデータベースを上書きする [WITH REPLACE]]**</span><span class="sxs-lookup"><span data-stu-id="af382-113">**Overwrite the existing database [WITH REPLACE]**</span></span>  
 <span data-ttu-id="af382-114">データベースの名前が、 **[データベースの復元]** ダイアログ ボックスの [[全般]](../../integration-services/general-page-of-integration-services-designers-options.md) ページにある **[復元先]** フィールドで指定した名前と同じ場合は、そのデータベースのファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="af382-114">The restore operation will overwrite the files of any database that is currently using the database name that you are specifying in the **Restore to**field on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Restore Database** dialog box.</span></span> <span data-ttu-id="af382-115">別のデータベースのバックアップを既存のデータベース名に復元する場合でも、既存のデータベースのファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="af382-115">The files of the existing database will be overwritten even if you are restoring backups from a different database to the existing database name.</span></span> <span data-ttu-id="af382-116">このオプションを選択することは、 [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) ステートメント ([!INCLUDE[tsql](../../includes/tsql-md.md)]) で REPLACE オプションを使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="af382-116">Selecting this option is equivalent to using the REPLACE option in a [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="af382-117">このオプションは、十分な検討を行った場合に限り使用してください。</span><span class="sxs-lookup"><span data-stu-id="af382-117">Use this option only after careful consideration.</span></span> <span data-ttu-id="af382-118">詳細については、「[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af382-118">For more information, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
 <span data-ttu-id="af382-119">**[レプリケーションの設定を保存する [WITH KEEP_REPLICATION]]**</span><span class="sxs-lookup"><span data-stu-id="af382-119">**Preserve the replication settings [WITH KEEP_REPLICATION]**</span></span>  
 <span data-ttu-id="af382-120">パブリッシュされたデータベースを、そのデータベースが作成されたサーバー以外のサーバーに復元するときに、レプリケーションの設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="af382-120">Preserves the replication settings when restoring a published database to a server other than the server where the database was created.</span></span> <span data-ttu-id="af382-121">このオプションは、バックアップ作成時にデータベースがレプリケートされた場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="af382-121">This option is relevant only if the database was replicated when the backup was created.</span></span>  
  
 <span data-ttu-id="af382-122">このオプションは、この表で後に説明する **[コミットされていないトランザクションをロールバックして、データベースを使用可能な状態にする。別のトランザクション ログは復元できません。]** オプションをクリックした場合だけ使用できます。これは、RECOVERY オプションを指定してバックアップを復元するのと同じです。</span><span class="sxs-lookup"><span data-stu-id="af382-122">This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions** option (described later in this table), which is equivalent to restoring a backup with the RECOVERY option.</span></span>  
  
 <span data-ttu-id="af382-123">このオプションを選択することは、 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントで KEEP_REPLICATION オプションを使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="af382-123">Selecting this option is equivalent to using the KEEP_REPLICATION option in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="af382-124">詳細については、「 [レプリケートされたデータベースのバックアップと復元](../replication/administration/back-up-and-restore-replicated-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af382-124">For more information, see [Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
 <span data-ttu-id="af382-125">**[復元するデータベースへのアクセスを制限する [WITH RESTRICTED_USER]]**</span><span class="sxs-lookup"><span data-stu-id="af382-125">**Restrict access to the restored database [WITH RESTRICTED_USER]**</span></span>  
 <span data-ttu-id="af382-126">復元するデータベースの使用を、 **db_owner**、 **dbcreator**、または **sysadmin**のメンバーだけに制限します。</span><span class="sxs-lookup"><span data-stu-id="af382-126">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
 <span data-ttu-id="af382-127">このオプションを選択することは、RESTORE ステートメントで RESTRICTED_USER オプションを使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="af382-127">Selecting this option is synonymous to using the RESTRICTED_USER option in a RESTORE statement.</span></span>  
  
### <a name="recovery-state"></a><span data-ttu-id="af382-128">[復旧状態]</span><span class="sxs-lookup"><span data-stu-id="af382-128">Recovery state</span></span>  
 <span data-ttu-id="af382-129">復元操作後にデータベースの状態を確認するには、 **[復旧状態]** パネルのいずれかのオプションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af382-129">To determine the state of the database after the store operation, you must select one of the options of the **Recovery state** panel.</span></span>  
  
 <span data-ttu-id="af382-130">**RESTORE WITH RECOVERY**</span><span class="sxs-lookup"><span data-stu-id="af382-130">**RESTORE WITH RECOVERY**</span></span>  
 <span data-ttu-id="af382-131">**[全般]** ページの [[復元するバックアップ セット]](../../integration-services/general-page-of-integration-services-designers-options.md)グリッドでチェック ボックスがオンになっている最後のバックアップを復元した後に、データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="af382-131">Recovers the database after restoring the final backup checked in the **Backup sets to restore**grid on the [General page](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span> <span data-ttu-id="af382-132">これは既定のオプションで、 [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) ステートメント ([!INCLUDE[tsql](../../includes/tsql-md.md)]) で WITH RECOVERY を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="af382-132">This is the default option and is equivalent to specifying WITH RECOVERY in a [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af382-133">完全復旧モデルまたは一括ログ復旧モデルでは、すべてのログ ファイルを復元する場合にのみこのオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="af382-133">Under the full recovery model or bulk-logged recovery model, choose this option only if you are restoring all the log files now.</span></span>  
  
 <span data-ttu-id="af382-134">**RESTORE WITH NORECOVERY**</span><span class="sxs-lookup"><span data-stu-id="af382-134">**RESTORE WITH NORECOVERY**</span></span>  
 <span data-ttu-id="af382-135">データベースを復元状態のままにします。</span><span class="sxs-lookup"><span data-stu-id="af382-135">Leaves the database in the restoring state.</span></span> <span data-ttu-id="af382-136">これにより、現在の復旧パスで他のバックアップを復元できます。</span><span class="sxs-lookup"><span data-stu-id="af382-136">This allows you to restore additional backups in the current recovery path.</span></span> <span data-ttu-id="af382-137">データベースを復旧するには、RESTORE WITH RECOVERY オプションを使用して復元操作を実行する必要があります (上記のオプションを参照)。</span><span class="sxs-lookup"><span data-stu-id="af382-137">To recover the database, you will have to perform a restore operation by using the RESTORE WITH RECOVERY option (see the preceding option).</span></span>  
  
 <span data-ttu-id="af382-138">このオプションを選択することは、RESTORE ステートメントで WITH NORECOVERY を使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="af382-138">This option is equivalent to specifying WITH NORECOVERY in a RESTORE statement.</span></span>  
  
 <span data-ttu-id="af382-139">このオプションを選択すると、 **[レプリケーションの設定を保存する]** オプションを選択できなくなります。</span><span class="sxs-lookup"><span data-stu-id="af382-139">If you select this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
 <span data-ttu-id="af382-140">**RESTORE WITH STANDBY**</span><span class="sxs-lookup"><span data-stu-id="af382-140">**RESTORE WITH STANDBY**</span></span>  
 <span data-ttu-id="af382-141">データベースをスタンバイ状態のままにします。この状態では、データベースは、制限付きの読み取り専用アクセスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="af382-141">Leaves the database in a standby state, in which the database is available for limited read-only access.</span></span> <span data-ttu-id="af382-142">このオプションを選択することは、RESTORE ステートメントで WITH STANDBY を使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="af382-142">This option is equivalent to specifying WITH STANDBY in a RESTORE statement.</span></span>  
  
 <span data-ttu-id="af382-143">このオプションを選択するには、 **[スタンバイ ファイル]** ボックスにスタンバイ ファイルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af382-143">Choosing this option requires that you specify a standby file in the **Standby file** text box.</span></span> <span data-ttu-id="af382-144">スタンバイ ファイルを使用すると、復旧結果を元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="af382-144">The standby file allows the recovery effects to be undone.</span></span>  
  
 <span data-ttu-id="af382-145">**[スタンバイ ファイル]**</span><span class="sxs-lookup"><span data-stu-id="af382-145">**Standby file**</span></span>  
 <span data-ttu-id="af382-146">スタンバイ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="af382-146">Specifies a standby file.</span></span> <span data-ttu-id="af382-147">スタンバイ ファイルは、参照して指定するか、テキスト ボックスにパス名を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="af382-147">You can browse for the standby file or enter its pathname directly in the text box.</span></span>  
  
### <a name="tail-log-backup"></a><span data-ttu-id="af382-148">[ログ末尾のバックアップ]</span><span class="sxs-lookup"><span data-stu-id="af382-148">Tail-Log backup</span></span>  
 <span data-ttu-id="af382-149">データベースの復元と共にログ末尾のバックアップを実行するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="af382-149">Allows you to designate that a tail-log backup be performed along with the database restore.</span></span>  
  
 <span data-ttu-id="af382-150">**[復元の前にログ末尾のバックアップを行う]**</span><span class="sxs-lookup"><span data-stu-id="af382-150">**Take tail-Log backup before restoring**</span></span>  
 <span data-ttu-id="af382-151">ログ末尾のバックアップを行うように指定するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="af382-151">Check this box to designate that a tail-log backup should be performed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af382-152">[[バックアップのタイムライン]](backup-timeline.md) ダイアログ ボックスで選択した特定の時点がログ末尾のバックアップを必要としている場合は、このチェック ボックスがオンになり、それを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="af382-152">If the point-in-time you have selected in the [Backup Timeline](backup-timeline.md) dialog box requires a tail-log backup, this box will be selected and you will not be able to edit it.</span></span>  
  
 <span data-ttu-id="af382-153">**[バックアップ ファイル]**</span><span class="sxs-lookup"><span data-stu-id="af382-153">**Backup file**</span></span>  
 <span data-ttu-id="af382-154">ログ末尾のバックアップ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="af382-154">Specifies a backup file for the tail of the log.</span></span> <span data-ttu-id="af382-155">バックアップ ファイルは、参照して指定するか、テキスト ボックスに名前を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="af382-155">You can browse for the backup file or enter its name directly in the text box.</span></span>  
  
### <a name="server-connections"></a><span data-ttu-id="af382-156">サーバー接続</span><span class="sxs-lookup"><span data-stu-id="af382-156">Server connections</span></span>  
 <span data-ttu-id="af382-157">既存のデータベース接続を閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="af382-157">Allows you to close existing database connections.</span></span>  
  
 <span data-ttu-id="af382-158">**[既存の接続を閉じる]**</span><span class="sxs-lookup"><span data-stu-id="af382-158">**Close existing connections**</span></span>  
 <span data-ttu-id="af382-159">データベースへのアクティブな接続がある場合、復元操作は失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af382-159">Restore operations may fail if there are active connections to the database.</span></span> <span data-ttu-id="af382-160">**とデータベース間のすべてのアクティブな接続を閉じるには、** [既存の接続を閉じる] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] オプションをオンにします。</span><span class="sxs-lookup"><span data-stu-id="af382-160">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span> <span data-ttu-id="af382-161">このチェック ボックスをオンにすると、データベースは復元操作の実行前にシングル ユーザー モードに設定され、復元操作の完了後にマルチユーザー モードに設定されます。</span><span class="sxs-lookup"><span data-stu-id="af382-161">This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.</span></span>  
  
### <a name="prompt"></a><span data-ttu-id="af382-162">Prompt</span><span class="sxs-lookup"><span data-stu-id="af382-162">Prompt</span></span>  
 <span data-ttu-id="af382-163">**[各バックアップを復元する前に確認する]**</span><span class="sxs-lookup"><span data-stu-id="af382-163">**Prompt before restoring each backup**</span></span>  
 <span data-ttu-id="af382-164">各バックアップが復元された後、復元シーケンスを続行するかどうかを確認する **[復元の続行]** ダイアログ ボックスを表示することを指定します。</span><span class="sxs-lookup"><span data-stu-id="af382-164">Specifies that after each backup is restored, the **Continue with Restore** dialog box will be displayed to inquire whether you want to continue the restore sequence.</span></span> <span data-ttu-id="af382-165">このダイアログ ボックスには、次のメディア セットの名前 (既知の場合) および次のバックアップ セットの名前と説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="af382-165">This dialog box displays the name of the next media set (if known) and the name and description of the next backup set.</span></span>  
  
 <span data-ttu-id="af382-166">このオプションを使用すると、バックアップの復元後に復元シーケンスを一時停止できます。</span><span class="sxs-lookup"><span data-stu-id="af382-166">This option allows you to pause a restore sequence after restoring any of the backups.</span></span> <span data-ttu-id="af382-167">メディア セットごとにテープを交換する必要がある場合 (サーバーにテープ デバイスが 1 台しかない場合など) に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="af382-167">This option is particularly useful when you must swap tapes for different media sets; for example, when your server has only one tape device.</span></span> <span data-ttu-id="af382-168">続行する準備ができたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af382-168">When you are ready to proceed, click **OK**.</span></span>  
  
 <span data-ttu-id="af382-169">**[いいえ]** をクリックすると、復元シーケンスを中断できます。</span><span class="sxs-lookup"><span data-stu-id="af382-169">You can interrupt a restore sequence by clicking **No**.</span></span> <span data-ttu-id="af382-170">これにより、データベースが復元状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="af382-170">This leaves the database is in the restoring state.</span></span> <span data-ttu-id="af382-171">その後、都合のよいときに、 **[復元の続行]** ダイアログ ボックスに表示されている次のバックアップから再開することで、復元シーケンスを続行できます。</span><span class="sxs-lookup"><span data-stu-id="af382-171">At your convenience, you can later continue the restore sequence by resuming with the next backup described in the **Continue with Restore** dialog box.</span></span> <span data-ttu-id="af382-172">次のバックアップを復元する方法は、そのバックアップに含まれているのがデータかトランザクション ログかによって、次のように異なります。</span><span class="sxs-lookup"><span data-stu-id="af382-172">The procedure restoring the next backup depends on whether it contains data or transaction log, as follows:</span></span>  
  
-   <span data-ttu-id="af382-173">次のバックアップが完全バックアップまたは差分バックアップの場合は、 **[データベースの復元]** タスクを再度使用します。</span><span class="sxs-lookup"><span data-stu-id="af382-173">If the next backup is a full or differential backup, use the **Restore Database** task again.</span></span>  
  
-   <span data-ttu-id="af382-174">次のバックアップがファイル バックアップの場合は、 **[ファイルおよびファイル グループの復元]** タスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="af382-174">If the next backup is a file backup, use the **Restore Files and Filegroup**s task.</span></span> <span data-ttu-id="af382-175">詳細については、「[ファイルとファイル グループの復元 &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af382-175">For more information, see [Restore Files and Filegroups &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="af382-176">次のバックアップがログ バックアップの場合は、 **[トランザクション ログの復元]** タスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="af382-176">If the next backup is a log backup, use the **Restore Transaction Log** task.</span></span> <span data-ttu-id="af382-177">トランザクション ログの復元による復元シーケンスの再開については、「 [トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af382-177">For information about resuming a restore sequence by restoring a transaction log, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af382-178">参照</span><span class="sxs-lookup"><span data-stu-id="af382-178">See Also</span></span>  
 <span data-ttu-id="af382-179">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af382-179">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="af382-180">[デバイスからのバックアップ復元 &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af382-180">[Restore a Backup from a Device &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md) </span></span>  
 <span data-ttu-id="af382-181">[トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af382-181">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="af382-182">[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af382-182">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="af382-183">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af382-183">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="af382-184">[[データベースの復元] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="af382-184">[Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
  
