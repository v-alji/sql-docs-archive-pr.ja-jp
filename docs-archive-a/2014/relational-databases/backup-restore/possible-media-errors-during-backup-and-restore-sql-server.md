---
title: バックアップ中および復元中に発生する可能性があるメディア エラー (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media errors [SQL Server]
- CONTINUE_AFTER_ERROR option
- errors [SQL Server], backups
- backups [SQL Server], errors
- RESTORE VERIFYONLY statement
- backup media [SQL Server], error management
- page checksums [SQL Server]
- backup checksums [SQL Server]
- backing up [SQL Server], media errors
- RESTORE statement, media errors
- NO_CHECKSUM option
- checksums [SQL Server]
ms.assetid: 83a27b29-1191-4f8d-9648-6e6be73a9b7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15691c513aad6027be1063ef566ebdf245ebcc8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736444"
---
# <a name="possible-media-errors-during-backup-and-restore-sql-server"></a><span data-ttu-id="91e48-102">バックアップ中および復元中に発生する可能性があるメディア エラー (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91e48-102">Possible Media Errors During Backup and Restore (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="91e48-103">では、エラーが検出されてもデータベースを復旧するオプションを選択できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="91e48-103">gives you the option of recovering a database despite detected errors.</span></span> <span data-ttu-id="91e48-104">エラー検出の重要なメカニズムとして、バックアップ チェックサムを任意で作成できるようになりました。バックアップ チェックサムは、バックアップ操作で生成して、復元操作で検証できます。</span><span class="sxs-lookup"><span data-stu-id="91e48-104">An important new error-detection mechanism is the optional creation of a backup checksum that can be created by a backup operation and validated by a restore operation.</span></span> <span data-ttu-id="91e48-105">操作中にエラーを検出するかどうかと、エラー発生時に操作を停止するか続行するかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="91e48-105">You can control whether an operation checks for errors and whether the operation stops or continues on encountering an error.</span></span> <span data-ttu-id="91e48-106">バックアップにバックアップ チェックサムが含まれている場合、RESTORE ステートメントおよび RESTORE VERIFYONLY ステートメントでエラーを検査できます。</span><span class="sxs-lookup"><span data-stu-id="91e48-106">If a backup contains a backup checksum, RESTORE and RESTORE VERIFYONLY statements can check for errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91e48-107">ミラー化バックアップでは、メディア セットのコピー (ミラー) が最大で 4 つ作成され、メディアの破損によるエラーから復旧するために使用する代替コピーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-107">Mirrored backups provide up to four copies (mirrors) of a media set, providing alternative copies for recovering from errors caused by damaged media.</span></span> <span data-ttu-id="91e48-108">詳細については、「 [ミラー化バックアップ メディア セット &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91e48-108">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
  
  
##  <a name="backup-checksums"></a><a name="BckChecksums"></a> <span data-ttu-id="91e48-109">バックアップ チェックサム</span><span class="sxs-lookup"><span data-stu-id="91e48-109">Backup Checksums</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="91e48-110">でサポートされているチェックサムは、ページ チェックサム、ログ ブロック チェックサム、およびバックアップ チェックサムの 3 種類です。</span><span class="sxs-lookup"><span data-stu-id="91e48-110">supports three types of checksums: a checksum on pages, a checksum in log blocks, and a backup checksum.</span></span> <span data-ttu-id="91e48-111">バックアップ チェックサムの生成時には、データベースから読み取ったデータについて、データベース内に存在するチェックサムや破損ページ情報との整合性が BACKUP によって検証されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-111">When generating a backup checksum, BACKUP verifies that the data read from the database is consistent with any checksum or torn-page indication that is present in the database.</span></span>  
  
 <span data-ttu-id="91e48-112">BACKUP ステートメントではオプションで、バックアップ ストリームのバックアップ チェックサムを計算できます。特定のページにページ チェックサムまたは破損ページ情報がある場合、ページのバックアップ時に、そのページのチェックサムおよび破損ページの状態とページ ID も検証されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-112">The BACKUP statement optionally computes a backup checksum on the backup stream; if page-checksum or torn-page information is present on a given page, when backing up the page, BACKUP also verifies the checksum and torn-page status and the page ID, of the page.</span></span> <span data-ttu-id="91e48-113">バックアップ操作でバックアップ チェックサムを作成する際に、チェックサムがページに追加されることはありません。</span><span class="sxs-lookup"><span data-stu-id="91e48-113">When creating a backup checksum, a backup operation does not add any checksums to pages.</span></span> <span data-ttu-id="91e48-114">ページはデータベースに存在するままの状態でバックアップされます。バックアップでページは変更されません。</span><span class="sxs-lookup"><span data-stu-id="91e48-114">Pages are backed up as they exist in the database, and the pages are unmodified by backup.</span></span>  
  
 <span data-ttu-id="91e48-115">バックアップ チェックサムを使用すると、検証および生成の際のオーバーヘッドによって、パフォーマンスに影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="91e48-115">Due to the overhead verifying and generating backup checksums, using backup checksums poses a potential performance impact.</span></span> <span data-ttu-id="91e48-116">影響はワークロードおよびバックアップ スループットの両方に及ぶ場合があります。</span><span class="sxs-lookup"><span data-stu-id="91e48-116">Both the workload and the backup throughput may be affected.</span></span> <span data-ttu-id="91e48-117">このため、バックアップ チェックサムの使用は任意です。</span><span class="sxs-lookup"><span data-stu-id="91e48-117">Therefore, using backup checksums is optional.</span></span> <span data-ttu-id="91e48-118">バックアップ時にチェックサムを生成する場合は、システムで進行中のワークロードへの影響だけでなく、発生する CPU オーバーヘッドも注意深く監視してください。</span><span class="sxs-lookup"><span data-stu-id="91e48-118">When deciding to generate checksums during a backup, carefully monitor the CPU overhead incurred as well as the impact on any concurrent workload on the system.</span></span>  
  
 <span data-ttu-id="91e48-119">BACKUP を実行してもディスク上の元のページおよびページの内容は変更されません。</span><span class="sxs-lookup"><span data-stu-id="91e48-119">BACKUP never modifies the source page on disk nor the contents of a page.</span></span>  
  
 <span data-ttu-id="91e48-120">バックアップ チェックサムを有効にすると、バックアップ操作では、次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-120">When backup checksums are enabled, a backup operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="91e48-121">ページをバックアップ メディアに書き込む前に、ページ レベルの情報が検証されます (ページ チェックサムまたは破損ページ検出のいずれかが存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="91e48-121">Before writing a page to the backup media, the backup operation verifies the page-level information (page checksum or torn page detection), if either exists.</span></span> <span data-ttu-id="91e48-122">いずれの情報も存在しない場合は、ページを検証できません。</span><span class="sxs-lookup"><span data-stu-id="91e48-122">If neither exists, backup cannot verify the page.</span></span> <span data-ttu-id="91e48-123">未検証のページはそのまま書き込まれ、内容が全体のバックアップ チェックサムに追加されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-123">Unverified the pages are included as is, and their contents are added to the overall backup checksum.</span></span>  
  
     <span data-ttu-id="91e48-124">検証中にページ エラーが検出された場合、バックアップは失敗します。</span><span class="sxs-lookup"><span data-stu-id="91e48-124">If the backup operation encounters a page error during verification, the backup fails.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91e48-125">ページ チェックサムおよび破損ページ検出の詳細については、ALTER DATABASE ステートメントの PAGE_VERIFY オプションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="91e48-125">For more information about page checksums and torn page detection, see the PAGE_VERIFY option of the ALTER DATABASE statement.</span></span> <span data-ttu-id="91e48-126">詳細については、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91e48-126">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
2.  <span data-ttu-id="91e48-127">ページ チェックサムが存在するかどうかに関係なく、BACKUP によってバックアップ ストリームに個別のバックアップ チェックサムが生成されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-127">Regardless of whether page checksums are present, BACKUP generates a separate backup checksum for the backup streams.</span></span> <span data-ttu-id="91e48-128">復元操作でバックアップ チェックサムを使用し、バックアップが破損していないかどうかを検証することもできます。</span><span class="sxs-lookup"><span data-stu-id="91e48-128">Restore operations can optionally use the backup checksum to validate that the backup is not corrupted.</span></span> <span data-ttu-id="91e48-129">バックアップ チェックサムは、データベース ページにではなくバックアップ メディアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-129">The backup checksum is stored on the backup media, not on the database pages.</span></span> <span data-ttu-id="91e48-130">バックアップ チェックサムは、復元時に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="91e48-130">The backup checksum can optionally be used at restore time.</span></span>  
  
3.  <span data-ttu-id="91e48-131">バックアップ セットは ( **msdb..backupset** の **has_backup_checksums**列に) バックアップ チェックサムがあるものとしてフラグが付けられます。</span><span class="sxs-lookup"><span data-stu-id="91e48-131">The backup set is flagged as containing backup checksums (in the **has_backup_checksums** column of **msdb..backupset)**.</span></span> <span data-ttu-id="91e48-132">詳細については、「 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91e48-132">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
 <span data-ttu-id="91e48-133">復元操作中、バックアップ メディアにバックアップ チェックサムがある場合、既定では RESTORE ステートメントと RESTORE VERIFYONLY ステートメントの両方でバックアップ チェックサムとページ チェックサムが検証されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-133">During a restore operation, if backup checksums are present on the backup media, by default, both the RESTORE and RESTORE VERIFYONLY statements verify the backup checksums and page checksums.</span></span> <span data-ttu-id="91e48-134">バックアップ チェックサムがない場合、いずれの復元操作も検証が行われずに続行されます。これは、バックアップ チェックサムがないと、ページ チェックサムの検証を確実に実行できないためです。</span><span class="sxs-lookup"><span data-stu-id="91e48-134">If there is no backup checksum, either restore operation proceeds without any verification; this is because without a backup checksum, restore cannot reliably verify page checksums.</span></span>  
  
## <a name="response-to-page-checksum-errors-during-a-backup-or-restore-operation"></a><span data-ttu-id="91e48-135">バックアップまたは復元操作中のページ チェックサム エラーへの応答</span><span class="sxs-lookup"><span data-stu-id="91e48-135">Response to Page Checksum Errors During a Backup or Restore Operation</span></span>  
 <span data-ttu-id="91e48-136">既定では、ページ チェックサム エラーが発生した後、BACKUP 操作または RESTORE 操作は失敗し、RESTORE VERIFYONLY 操作が続行されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-136">By default, after encountering a page checksum error, a BACKUP or RESTORE operation fails and a RESTORE VERIFYONLY operation continues.</span></span> <span data-ttu-id="91e48-137">ただし、エラー発生時に特定の操作を失敗させるか、できる限り続行させるかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="91e48-137">However, you can control whether a given operation fails on encountering an error or continues as best it can.</span></span>  
  
 <span data-ttu-id="91e48-138">エラー発生後に BACKUP 操作を続行する場合は、次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="91e48-138">If a BACKUP operation continues after encountering errors, the operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="91e48-139">バックアップ メディア上のバックアップ セットに対し、エラーが存在するというフラグを設定し、 **msdb** データベースの **suspect_pages** テーブルでそのページを追跡します。</span><span class="sxs-lookup"><span data-stu-id="91e48-139">Flags the backup set on the backup media as containing errors and tracks the page in the **suspect_pages** table in the **msdb** database.</span></span> <span data-ttu-id="91e48-140">詳細については、「[suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91e48-140">For more information, see [suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql).</span></span>  
  
2.  <span data-ttu-id="91e48-141">SQL Server エラー ログにエラーを記録します。</span><span class="sxs-lookup"><span data-stu-id="91e48-141">Logs the error in the SQL Server error log.</span></span>  
  
3.  <span data-ttu-id="91e48-142">バックアップ セットに対し、この種類のエラーが存在するというマークを ( **msdb.backupset** の **is_damaged**列に) 付けます。</span><span class="sxs-lookup"><span data-stu-id="91e48-142">Marks the backup set as containing this type of error (in the **is_damaged** column of **msdb.backupset)**.</span></span> <span data-ttu-id="91e48-143">詳細については、「 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91e48-143">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
4.  <span data-ttu-id="91e48-144">正常にバックアップが生成されたがページ エラーが含まれていることを示すメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="91e48-144">Issues a message that the backup was successfully generated, but contains page errors.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="91e48-145">関連タスク</span><span class="sxs-lookup"><span data-stu-id="91e48-145">Related Tasks</span></span>  
 <span data-ttu-id="91e48-146">**バックアップ チェックサムを有効または無効にするには**</span><span class="sxs-lookup"><span data-stu-id="91e48-146">**To enable or disable backup checksums**</span></span>  
  
-   [<span data-ttu-id="91e48-147">バックアップ中または復元中にバックアップ チェックサムを有効または無効にする &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="91e48-147">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
 <span data-ttu-id="91e48-148">**バックアップ操作中のエラーへの応答を制御するには**</span><span class="sxs-lookup"><span data-stu-id="91e48-148">**To control the response to a error during a backup operation**</span></span>  
  
-   [<span data-ttu-id="91e48-149">バックアップまたは復元の操作をエラー発生後に続行するか停止するかを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="91e48-149">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
## <a name="see-also"></a><span data-ttu-id="91e48-150">参照</span><span class="sxs-lookup"><span data-stu-id="91e48-150">See Also</span></span>  
 <span data-ttu-id="91e48-151">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91e48-151">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="91e48-152">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91e48-152">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="91e48-153">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91e48-153">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="91e48-154">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91e48-154">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 <span data-ttu-id="91e48-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91e48-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="91e48-156">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91e48-156">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
