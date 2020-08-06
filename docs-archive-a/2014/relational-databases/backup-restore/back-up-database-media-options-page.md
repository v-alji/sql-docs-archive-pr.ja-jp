---
title: '[データベースのバックアップ] ([メディア オプション] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- swb.backupdatabase.mediaoptions.f1
- sql12.swb.backupdatabase.mediaoptions.f1
ms.assetid: eff36228-710c-4ed5-9af5-95859575dc0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd09eb091a7f488f891bc2e69d19ad039b65e065
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720108"
---
# <a name="back-up-database-media-options-page"></a><span data-ttu-id="af88b-102">[データベースのバックアップ] ([メディア オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="af88b-102">Back Up Database (Media Options Page)</span></span>
  <span data-ttu-id="af88b-103">**[データベースのバックアップ]** ダイアログ ボックスの **[メディア オプション]** ページを使用すると、データベースのメディアのオプションを表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="af88b-103">Use the  **Media Options** page of the **Back Up Database** dialog box to view or modify database media options.</span></span>  
  
 <span data-ttu-id="af88b-104">**SQL Server Management Studio を使用してバックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="af88b-104">**To create a backup by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="af88b-105">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af88b-105">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="af88b-106">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af88b-106">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="af88b-107">データベース メンテナンス プランを定義して、データベース バックアップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="af88b-107">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="af88b-108">詳細については、「 [メンテナンス プラン](../maintenance-plans/maintenance-plans.md) 」および「 [メンテナンス プラン ウィザードの使用](../maintenance-plans/use-the-maintenance-plan-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af88b-108">For more information, see [Maintenance Plans](../maintenance-plans/maintenance-plans.md) and [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af88b-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してバックアップ タスクを指定する場合、 [!INCLUDE[tsql](../../includes/tsql-md.md)][[スクリプト]](/sql/t-sql/statements/backup-transact-sql) ボタンをクリックしてスクリプトの保存先を選択することにより、対応する **BACKUP** スクリプトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="af88b-109">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
## <a name="options"></a><span data-ttu-id="af88b-110">Options</span><span class="sxs-lookup"><span data-stu-id="af88b-110">Options</span></span>  
  
### <a name="overwrite-media"></a><span data-ttu-id="af88b-111">[メディアに上書きします]</span><span class="sxs-lookup"><span data-stu-id="af88b-111">Overwrite media</span></span>  
 <span data-ttu-id="af88b-112">**[メディアに上書きします]** パネルのオプションでは、バックアップをメディアに書き込む方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="af88b-112">The options of the **Overwrite media** panel control how the backup is written to the media.</span></span> <span data-ttu-id="af88b-113">[データベースのバックアップ] ダイアログ ボックスの [全般] ページでバックアップ先として [URL] (Azure Storage) を選択した場合、[メディアに上書きします] セクションのオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="af88b-113">IF you selected URL (Azure Storage) as the backup destination on the General page of the Back Up Database dialog box, the options under the Overwrite media section are disabled.</span></span> <span data-ttu-id="af88b-114">Transact-SQL の `BACKUP TO URL.. WITH FORMAT` ステートメントを使用してバックアップを上書きすることもできます。</span><span class="sxs-lookup"><span data-stu-id="af88b-114">You can overwrite a backup using the `BACKUP TO URL.. WITH FORMAT` Transact-SQL statement.</span></span> <span data-ttu-id="af88b-115">詳細については、「 [SQL Server Backup to URL](sql-server-backup-to-url.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af88b-115">For more information, see [SQL Server Backup to URL](sql-server-backup-to-url.md).</span></span>  
  
 <span data-ttu-id="af88b-116">暗号化オプションとの併用がサポートされているのは、 **[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]** オプションのみです。</span><span class="sxs-lookup"><span data-stu-id="af88b-116">Only the option, **Backup to a new media, and erase all existing backup sets** is supported with encryption options.</span></span> <span data-ttu-id="af88b-117">**[既存のメディア セットにバックアップする]** セクションのオプションを選択すると、 **[バックアップ オプション]** ページの暗号化オプションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="af88b-117">If you select the options under the **Back up to existing media** section, the encryptions options on the **Backup Options** page will be disabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af88b-118">メディア セットの詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af88b-118">For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="af88b-119">**[既存のメディア セットにバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="af88b-119">**Back up to the existing media set**</span></span>  
 <span data-ttu-id="af88b-120">データベースを既存のメディア セットにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="af88b-120">Back up a database to an existing media set.</span></span> <span data-ttu-id="af88b-121">このオプション ボタンをクリックすると、3 つのオプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="af88b-121">Selecting this option button activates three options.</span></span>  
  
 <span data-ttu-id="af88b-122">次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="af88b-122">Choose one of the following options:</span></span>  
  
 <span data-ttu-id="af88b-123">**既存のバックアップセットに追加する**</span><span class="sxs-lookup"><span data-stu-id="af88b-123">**Append to the existing backup set**</span></span>  
 <span data-ttu-id="af88b-124">バックアップ セットを既存のメディア セットに追加し、以前のバックアップをすべて保持します。</span><span class="sxs-lookup"><span data-stu-id="af88b-124">Append the backup set to the existing media set, preserving any prior backups.</span></span>  
  
 <span data-ttu-id="af88b-125">**[既存のすべてのバックアップ セットを上書きする]**</span><span class="sxs-lookup"><span data-stu-id="af88b-125">**Overwrite all existing backup sets**</span></span>  
 <span data-ttu-id="af88b-126">既存のメディア セット上にある以前のバックアップをすべて現在のバックアップに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="af88b-126">Replace any prior backups on the existing media set with the current backup.</span></span>  
  
 <span data-ttu-id="af88b-127">**[メディア セット名とバックアップ セットの有効期限を確認する]**</span><span class="sxs-lookup"><span data-stu-id="af88b-127">**Check media set name and backup set expiration**</span></span>  
 <span data-ttu-id="af88b-128">既存のメディア セットをバックアップする場合は、必要に応じて、バックアップ操作でバックアップ セットの名前と有効期限を確認することを指定します。</span><span class="sxs-lookup"><span data-stu-id="af88b-128">Optionally, if backing up to an existing media set, require the backup operation to verify the name and the expiration date of the backup sets.</span></span>  
  
 <span data-ttu-id="af88b-129">**[メディア セット名]**</span><span class="sxs-lookup"><span data-stu-id="af88b-129">**Media set name**</span></span>  
 <span data-ttu-id="af88b-130">**[メディア セット名とバックアップ セットの有効期限を確認する]** チェック ボックスがオンの場合、必要に応じて、このバックアップ操作で使用するメディア セットの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="af88b-130">If **Check media set name and backup set expiration** is selected, optionally, specify the name of the media set to be used for this backup operation.</span></span>  
  
 <span data-ttu-id="af88b-131">**[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]**</span><span class="sxs-lookup"><span data-stu-id="af88b-131">**Back up to a new media set, and erase all existing backup sets**</span></span>  
 <span data-ttu-id="af88b-132">新しいメディア セットを使用して、以前のバックアップ セットを消去します。</span><span class="sxs-lookup"><span data-stu-id="af88b-132">Use a new media set, erasing the previous backup sets.</span></span>  
  
 <span data-ttu-id="af88b-133">このオプションをクリックすると、次のオプションを指定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="af88b-133">Clicking this option activates the following options:</span></span>  
  
 <span data-ttu-id="af88b-134">**[新しいメディア セット名]**</span><span class="sxs-lookup"><span data-stu-id="af88b-134">**New media set name**</span></span>  
 <span data-ttu-id="af88b-135">必要に応じて、メディア セットの新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="af88b-135">Optionally, enter a new name for the media set.</span></span>  
  
 <span data-ttu-id="af88b-136">**[新しいメディア セットの説明]**</span><span class="sxs-lookup"><span data-stu-id="af88b-136">**New media set description**</span></span>  
 <span data-ttu-id="af88b-137">必要に応じて、新しいメディア セットのわかりやすい説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="af88b-137">Optionally, enter a meaningful description of the new media set.</span></span> <span data-ttu-id="af88b-138">この説明は、内容について正確に伝えられるだけの具体性が必要です。</span><span class="sxs-lookup"><span data-stu-id="af88b-138">This description should be specific enough to communicate the contents accurately.</span></span>  
  
### <a name="reliability"></a><span data-ttu-id="af88b-139">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="af88b-139">Reliability</span></span>  
 <span data-ttu-id="af88b-140">**[トランザクション ログ]** パネルのオプションでは、バックアップ操作によるエラー管理を制御します。</span><span class="sxs-lookup"><span data-stu-id="af88b-140">The options of the **Transaction log** panel control error management by the backup operation.</span></span>  
  
 <span data-ttu-id="af88b-141">**完了時にバックアップを検証する**</span><span class="sxs-lookup"><span data-stu-id="af88b-141">**Verify backup when finished**</span></span>  
 <span data-ttu-id="af88b-142">バックアップ セットが完全で、すべてのボリュームが読み取り可能であることを検証します。</span><span class="sxs-lookup"><span data-stu-id="af88b-142">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
 <span data-ttu-id="af88b-143">**メディアに書き込む前にチェックサムを実行する**</span><span class="sxs-lookup"><span data-stu-id="af88b-143">**Perform checksum before writing to media**</span></span>  
 <span data-ttu-id="af88b-144">バックアップ メディアに書き込む前にチェックサムを検証します。</span><span class="sxs-lookup"><span data-stu-id="af88b-144">Verify the checksums before writing to the backup media.</span></span> <span data-ttu-id="af88b-145">このチェック ボックスをオンにすることは、 [!INCLUDE[tsql](../../includes/tsql-md.md)]の BACKUP ステートメントで CHECKSUM オプションを指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="af88b-145">Selecting this option is equivalent to specifying the CHECKSUM option in the BACKUP statement of [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="af88b-146">このオプションをオンにするとワークロードが増加し、バックアップ操作のバックアップ スループットが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af88b-146">Selecting this option may increase the workload, and decrease the backup throughput of the backup operation.</span></span> <span data-ttu-id="af88b-147">バックアップ チェックサムの詳細については、「[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af88b-147">For information about backup checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
 <span data-ttu-id="af88b-148">**エラー時に続行する**</span><span class="sxs-lookup"><span data-stu-id="af88b-148">**Continue on error**</span></span>  
 <span data-ttu-id="af88b-149">エラーが 1 回以上発生しても、バックアップ操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="af88b-149">The backup operation is to continue even after encountering one or more errors.</span></span>  
  
### <a name="transaction-log"></a><span data-ttu-id="af88b-150">[トランザクション ログ]</span><span class="sxs-lookup"><span data-stu-id="af88b-150">Transaction log</span></span>  
 <span data-ttu-id="af88b-151">**[トランザクション ログ]** パネルのオプションでは、トランザクション ログ バックアップの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="af88b-151">The options of the **Transaction log** panel control the behavior of a transaction log backup.</span></span> <span data-ttu-id="af88b-152">これらのオプションは、完全復旧モデルと一括ログ復旧モデルにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="af88b-152">These options are relevant only under the full recovery model or bulk-logged recovery model.</span></span> <span data-ttu-id="af88b-153">これらのオプションは、 **[データベースのバックアップ]** ダイアログ ボックスの [[全般]](../../integration-services/general-page-of-integration-services-designers-options.md) ページにある **[バックアップの種類]** フィールドで **[トランザクション ログ]** を選択した場合のみアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="af88b-153">They are activated only if **Transaction log** has been selected in the **Backup type** field on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Back Up Database** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af88b-154">トランザクション ログのバックアップの詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af88b-154">For information about transaction log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="af88b-155">**[トランザクション ログを切り捨てる]**</span><span class="sxs-lookup"><span data-stu-id="af88b-155">**Truncate the transaction log**</span></span>  
 <span data-ttu-id="af88b-156">トランザクション ログをバックアップし、それを切り捨てることでログの領域を解放します。</span><span class="sxs-lookup"><span data-stu-id="af88b-156">Back up the transaction log and truncate it to free log space.</span></span> <span data-ttu-id="af88b-157">データベースはオンラインを維持します。</span><span class="sxs-lookup"><span data-stu-id="af88b-157">The database remains online.</span></span> <span data-ttu-id="af88b-158">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="af88b-158">This is the default option.</span></span>  
  
 <span data-ttu-id="af88b-159">**[ログの末尾をバックアップし、データベースを復元中の状態にしておく]**</span><span class="sxs-lookup"><span data-stu-id="af88b-159">**Back up the tail of the log, and leave the database in the restoring state**</span></span>  
 <span data-ttu-id="af88b-160">ログの末尾をバックアップし、データベースを復元中の状態にします。</span><span class="sxs-lookup"><span data-stu-id="af88b-160">Back up the tail of the log and leave the database in a restoring state.</span></span> <span data-ttu-id="af88b-161">このオプションでは、 *ログ末尾のバックアップ*を作成します。このバックアップでは、データベースの復元に備えて、通常、まだバックアップされていないログ (アクティブなログ) をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="af88b-161">This option creates a *tail-log backup*, which backs up logs that have not yet been backed up (the active log), typically, in preparation for restoring a database.</span></span> <span data-ttu-id="af88b-162">復元が完了するまで、ユーザーはデータベースを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="af88b-162">The database will be unavailable to users until it is completely restored.</span></span>  
  
 <span data-ttu-id="af88b-163">このオプションを選択することは、[BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメント ([!INCLUDE[tsql](../../includes/tsql-md.md)]) で WITH NO_TRUNCATE および NORECOVERY を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="af88b-163">Selecting this option is equivalent to specifying WITH NO_TRUNCATE, NORECOVERY in a [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span> <span data-ttu-id="af88b-164">詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](tail-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af88b-164">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
### <a name="tape-drive"></a><span data-ttu-id="af88b-165">[テープ ドライブ]</span><span class="sxs-lookup"><span data-stu-id="af88b-165">Tape drive</span></span>  
 <span data-ttu-id="af88b-166">**[テープ ドライブ]** パネルのオプションでは、バックアップ操作時のテープ管理を制御します。</span><span class="sxs-lookup"><span data-stu-id="af88b-166">The options of the **Tape drive** panel control tape management during the backup operation.</span></span> <span data-ttu-id="af88b-167">これらのオプションは、 **[データベースのバックアップ]** ダイアログ ボックスの [[全般]](../../integration-services/general-page-of-integration-services-designers-options.md) ページにある **[バックアップ先]** パネルで **[テープ]** を選択した場合のみアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="af88b-167">These options are activated only if **Tape** has been selected in the **Destination** panel on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Back Up Database** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af88b-168">テープ デバイスの使用方法については、「[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af88b-168">For information about how to use tape devices, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="af88b-169">**[バックアップ後にテープをアンロードする]**</span><span class="sxs-lookup"><span data-stu-id="af88b-169">**Unload the tape after backup**</span></span>  
 <span data-ttu-id="af88b-170">バックアップの完了後、テープをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="af88b-170">After the backup is complete, unload the tape.</span></span>  
  
 <span data-ttu-id="af88b-171">**[アンロードの前にテープを巻き戻す]**</span><span class="sxs-lookup"><span data-stu-id="af88b-171">**Rewind the tape before unloading**</span></span>  
 <span data-ttu-id="af88b-172">テープをアンロードする前にテープを解放し、巻き戻します。</span><span class="sxs-lookup"><span data-stu-id="af88b-172">Before unloading the tape, release and rewind it.</span></span> <span data-ttu-id="af88b-173">このオプションは、 **[バックアップ後にテープをアンロードする]** チェック ボックスをオンにした場合のみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="af88b-173">This is enabled only if **Unload the tape after backup** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af88b-174">参照</span><span class="sxs-lookup"><span data-stu-id="af88b-174">See Also</span></span>  
 <span data-ttu-id="af88b-175">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af88b-175">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="af88b-176">[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af88b-176">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="af88b-177">[ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af88b-177">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="af88b-178">データベースが破損したときのトランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af88b-178">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
