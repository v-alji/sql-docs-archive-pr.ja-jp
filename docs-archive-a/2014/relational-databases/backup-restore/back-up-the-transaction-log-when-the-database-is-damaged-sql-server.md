---
title: データベースが破損したときのトランザクション ログのバックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], damaged
- backing up [SQL Server]. damaged database
- transaction log backups [SQL Server], damaged databases
ms.assetid: 9b8873cc-df54-4336-ab9b-8f525132c2b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea712e6bc4e73119a4f07a7775f9f25e212f8534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631110"
---
# <a name="back-up-the-transaction-log-when-the-database-is-damaged-sql-server"></a><span data-ttu-id="d1966-102">データベースが破損したときのトランザクション ログのバックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d1966-102">Back Up the Transaction Log When the Database Is Damaged (SQL Server)</span></span>
  <span data-ttu-id="d1966-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースが損傷しているときにトランザクション ログをバックアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1966-103">This topic describes how to back up a transaction log when the database is damaged in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d1966-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d1966-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d1966-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d1966-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d1966-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d1966-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d1966-107">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="d1966-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d1966-108">Security</span><span class="sxs-lookup"><span data-stu-id="d1966-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d1966-109">**データベースが損傷したときのトランザクション ログのバックアップ方法:**</span><span class="sxs-lookup"><span data-stu-id="d1966-109">**To back up the transaction log when the database is damaged, using:**</span></span>  
  
     [<span data-ttu-id="d1966-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d1966-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d1966-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d1966-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d1966-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="d1966-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d1966-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d1966-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d1966-114">BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d1966-114">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d1966-115">推奨事項</span><span class="sxs-lookup"><span data-stu-id="d1966-115">Recommendations</span></span>  
  
-   <span data-ttu-id="d1966-116">データベースで完全復旧モデルまたは一括ログ復旧モデルを使用している場合は、通常、データベースの復元を開始する前に、ログの末尾をバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1966-116">For a database that uses either the full or bulk-logged recovery model, you generally need to back up the tail of the log before beginning to restore the database.</span></span> <span data-ttu-id="d1966-117">また、ログ配布構成をフェールオーバーする前に、プライマリ データベースのログの末尾もバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1966-117">You also should back up the tail of the log of the primary database before failing over a log shipping configuration.</span></span> <span data-ttu-id="d1966-118">データベースを復旧する前にログ末尾のバックアップを最後のログ バックアップとして復元すると、障害発生後の作業損失を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="d1966-118">Restoring the tail-log backup as the final log backup before recovering the database avoids work loss after a failure.</span></span> <span data-ttu-id="d1966-119">ログ末尾のバックアップの詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](tail-log-backups-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1966-119">For more information about tail-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d1966-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d1966-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d1966-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="d1966-121">Permissions</span></span>  
 <span data-ttu-id="d1966-122">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="d1966-122">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="d1966-123">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="d1966-123">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1966-124">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d1966-124">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="d1966-125">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="d1966-125">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="d1966-126">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d1966-126">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d1966-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d1966-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-the-tail-of-the-transaction-log"></a><span data-ttu-id="d1966-128">トランザクション ログの末尾をバックアップするには</span><span class="sxs-lookup"><span data-stu-id="d1966-128">To back up the tail of the transaction log</span></span>  
  
1.  <span data-ttu-id="d1966-129">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="d1966-129">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="d1966-130">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1966-130">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="d1966-131">データベースを右クリックして **[タスク]** をポイントし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1966-131">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="d1966-132">**[データベースのバックアップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1966-132">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="d1966-133">**[データベース]** ボックスに、適切なデータベース名が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d1966-133">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="d1966-134">必要に応じて、このボックスの一覧から別のデータベースを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1966-134">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="d1966-135">復旧モデルが **[FULL]** または **[BULK_LOGGED]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d1966-135">Verify that the recovery model is either **FULL** or **BULK_LOGGED**.</span></span>  
  
6.  <span data-ttu-id="d1966-136">**[バックアップの種類]** ボックスの一覧で、 **[トランザクション ログ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d1966-136">In the **Backup type** list box, select **Transaction Log**.</span></span>  
  
7.  <span data-ttu-id="d1966-137">**[バックアップのみコピーする]** はオフのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="d1966-137">Leave **Copy Only Backup** deselected.</span></span>  
  
8.  <span data-ttu-id="d1966-138">**[バックアップ セット]** で、表示された既定のバックアップ セット名をそのまま使用するか、または **[名前]** ボックスに別のバックアップ セット名を入力します。</span><span class="sxs-lookup"><span data-stu-id="d1966-138">In the **Backup set** area, either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="d1966-139">**[説明]** ボックスに、ログ末尾のバックアップの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="d1966-139">In the **Description** text box, enter a description for the tail-log backup.</span></span>  
  
10. <span data-ttu-id="d1966-140">バックアップ セットの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1966-140">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="d1966-141">バックアップ セットが指定の日数後に期限切れになるようにするには、 **[期間指定]** \(既定のオプション) をクリックし、セットを作成してからセットが期限切れになるまでの日数を入力します。</span><span class="sxs-lookup"><span data-stu-id="d1966-141">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="d1966-142">0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。</span><span class="sxs-lookup"><span data-stu-id="d1966-142">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="d1966-143">既定値は、 **[サーバーのプロパティ]** ダイアログ ボックス ( **[データベースの設定]** ページ) の **[バックアップ メディアの既定の保有期間 (日)]** オプションで設定されています。</span><span class="sxs-lookup"><span data-stu-id="d1966-143">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="d1966-144">このダイアログ ボックスを開くには、オブジェクト エクスプローラーでサーバー名を右クリックし、[プロパティ] をクリックして、 **[データベースの設定]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1966-144">To access this dialog box, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="d1966-145">バックアップ セットが特定の日付に期限切れになるようにするには、 **[日時指定]** をクリックし、セットの有効期限が切れる日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="d1966-145">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="d1966-146">**[ディスク]** または **[テープ]** をクリックして、バックアップ先を選択します。</span><span class="sxs-lookup"><span data-stu-id="d1966-146">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="d1966-147">1 つのメディア セットを含んでいる最大 64 個のディスク ドライブまたはテープ ドライブのパスを選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1966-147">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="d1966-148">選択したパスは、 **[バックアップ先]** ボックスの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1966-148">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="d1966-149">バックアップ先を削除するには、バックアップ先を選択して **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1966-149">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="d1966-150">バックアップ先の内容を表示するには、バックアップ先を選択して **[内容]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1966-150">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="d1966-151">**[オプション]** ページで、次のいずれかをクリックして **[メディアに上書きします]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1966-151">On the **Options** page, select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="d1966-152">**[既存のメディア セットにバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="d1966-152">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="d1966-153">このオプションでは、 **[既存のバックアップ セットに追加する]** または **[既存のすべてのバックアップ セットを上書きする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1966-153">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span>  
  
         <span data-ttu-id="d1966-154">必要に応じて、 **[メディア セット名とバックアップ セットの有効期限を確認する]** チェック ボックスをオンにします。これにより、バックアップ操作で、メディア セットとバックアップ セットの有効期限が切れる日付と時刻の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="d1966-154">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="d1966-155">必要に応じて、 **[メディア セット名]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d1966-155">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="d1966-156">名前を指定しなかった場合、空の名前でメディア セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d1966-156">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="d1966-157">メディア セット名を指定した場合は、メディア (テープまたはディスク) の実際の名前がここで入力した名前と一致しているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="d1966-157">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="d1966-158">メディア名を指定せずに、このチェック ボックスをオンにしてこのメディアを確認するよう指定した場合は、実際のメディア名も空でないとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="d1966-158">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="d1966-159">**[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]**</span><span class="sxs-lookup"><span data-stu-id="d1966-159">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="d1966-160">このオプションでは、 **[新しいメディア セット名]** ボックスに名前を入力し、必要に応じて **[新しいメディア セットの説明]** ボックスにメディア セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="d1966-160">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
     <span data-ttu-id="d1966-161">メディア セット オプションの詳細については、「[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1966-161">For more information about media set options, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
13. <span data-ttu-id="d1966-162">**[信頼性]** セクションで、必要に応じて次の項目をオンにします。</span><span class="sxs-lookup"><span data-stu-id="d1966-162">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="d1966-163">**[完了時にバックアップを検証する]** 。</span><span class="sxs-lookup"><span data-stu-id="d1966-163">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="d1966-164">**[メディアに書き込む前にチェックサムを行う]** 。</span><span class="sxs-lookup"><span data-stu-id="d1966-164">**Perform checksum before writing to media**.</span></span>  
  
    -   <span data-ttu-id="d1966-165">**[チェックサム エラーのまま続行する]**</span><span class="sxs-lookup"><span data-stu-id="d1966-165">**Continue on checksum error**</span></span>  
  
     <span data-ttu-id="d1966-166">チェックサムの詳細については、「[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1966-166">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
14. <span data-ttu-id="d1966-167">**[トランザクション ログ]** セクションで、 **[ログの末尾をバックアップし、データベースを復元中の状態にしておく]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="d1966-167">In the **Transaction log** section, check **Back up the tail of the log, and leave database in the restoring state**.</span></span>  
  
     <span data-ttu-id="d1966-168">これは、次の [BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントを指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="d1966-168">This is equivalent to specifying the following [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement:</span></span>  
  
     `BACKUP LOG <database_name> TO <backup_device> WITH NORECOVERY`  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d1966-169">復元時には、[データベースの復元] ダイアログ ボックスに、ログ末尾のバックアップの種類が **[トランザクション ログ (コピーのみ)]** として表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1966-169">At restore time, the Restore Database dialog box displays the type of a tail-log backup as **Transaction Log (Copy Only)**.</span></span>  
  
15. <span data-ttu-id="d1966-170">**[全般]** ページの **[バックアップ先]** セクションで、テープ ドライブにバックアップするように指定した場合は、 **[バックアップ後にテープをアンロードする]** チェック ボックスがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="d1966-170">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="d1966-171">このオプションをオンにすると、 **[アンロードの前にテープを巻き戻す]** オプションがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="d1966-171">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="d1966-172">以降では、 [バックアップの圧縮](backup-compression-sql-server.md)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d1966-172">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="d1966-173">既定では、バックアップが圧縮されるかどうかは、 **[バックアップ圧縮の既定]** サーバー構成オプションの値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="d1966-173">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="d1966-174">ただし、現在のサーバー レベルの既定の設定にかかわらず、 **[バックアップを圧縮する]** をオンにしてバックアップを圧縮することも、 **[バックアップを圧縮しない]** をオンにして圧縮しないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d1966-174">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="d1966-175">**現在の backup compression default 値を表示するには**</span><span class="sxs-lookup"><span data-stu-id="d1966-175">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="d1966-176">backup compression default サーバー構成オプションの表示または構成</span><span class="sxs-lookup"><span data-stu-id="d1966-176">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d1966-177">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d1966-177">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-backup-of-the-currently-active-transaction-log"></a><span data-ttu-id="d1966-178">現在アクティブなトランザクション ログのバックアップを作成するには</span><span class="sxs-lookup"><span data-stu-id="d1966-178">To create a backup of the currently active transaction log</span></span>  
  
1.  <span data-ttu-id="d1966-179">BACKUP LOG ステートメントを実行し、現在アクティブなトランザクション ログをバックアップします。このとき、次の指定を行います。</span><span class="sxs-lookup"><span data-stu-id="d1966-179">Execute the BACKUP LOG statement to back up the currently active transaction log, specifying:</span></span>  
  
    -   <span data-ttu-id="d1966-180">バックアップするトランザクション ログが属しているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="d1966-180">The name of the database to which the transaction log to back up belongs.</span></span>  
  
    -   <span data-ttu-id="d1966-181">トランザクション ログ バックアップが書き込まれるバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="d1966-181">The backup device where the transaction log backup will be written.</span></span>  
  
    -   <span data-ttu-id="d1966-182">NO_TRUNCATE 句。</span><span class="sxs-lookup"><span data-stu-id="d1966-182">The NO_TRUNCATE clause.</span></span>  
  
         <span data-ttu-id="d1966-183">この句を使用すると、データベースにアクセスできない場合でも、トランザクション ログ ファイルにアクセスでき、損傷していなければ、トランザクション ログのアクティブな部分をバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="d1966-183">This clause allows the active part of the transaction log to be backed up even if the database is inaccessible, provided that the transaction log file is accessible and undamaged.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="d1966-184">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d1966-184">Example (Transact-SQL)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1966-185">この例では、単純復旧モデルを使用する [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]を使用しています。</span><span class="sxs-lookup"><span data-stu-id="d1966-185">This example uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], which uses the simple recovery model.</span></span> <span data-ttu-id="d1966-186">ただし、ログ バックアップを可能にするために、データベースの完全バックアップを行う前に、データベースが完全復旧モデルを使用するように設定されています。</span><span class="sxs-lookup"><span data-stu-id="d1966-186">To permit log backups, before taking a full database backup, the database was set to use the full recovery model.</span></span> <span data-ttu-id="d1966-187">詳細については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1966-187">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="d1966-188">この例では、データベースが破損していてアクセスできないときでも、トランザクション ログ ファイルが破損しておらずアクセスできる場合は、現在アクティブなトランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="d1966-188">This example backs up the currently active transaction log when a database is damaged and inaccessible, if the transaction log is undamaged and accessible.</span></span>  
  
```scr  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1  
   WITH NO_TRUNCATE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1966-189">参照</span><span class="sxs-lookup"><span data-stu-id="d1966-189">See Also</span></span>  
 <span data-ttu-id="d1966-190">[トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1966-190">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="d1966-191">[SQL Server データベースを特定の時点に復元する方法 &#40;完全復旧モデル&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d1966-191">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="d1966-192">[[データベースのバックアップ] &#40;[バックアップ オプション] ページ&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="d1966-192">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="d1966-193">[データベースのバックアップ &#40;全般ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="d1966-193">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="d1966-194">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1966-194">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d1966-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d1966-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="d1966-196">[ファイルの復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d1966-196">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="d1966-197">ファイル復元 &#40; 完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="d1966-197">File Restores &#40;Full Recovery Model&#41;</span></span>](file-restores-full-recovery-model.md)  
  
  
