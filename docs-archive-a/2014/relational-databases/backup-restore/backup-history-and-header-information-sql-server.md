---
title: バックアップの履歴とヘッダーの情報 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup headers [SQL Server]
- history tables [SQL Server]
- file restores [SQL Server], status information
- backup sets [SQL Server], status information
- listing backed up databases
- status information [SQL Server], backups
- backing up [SQL Server], viewing backup sets
- restoring [SQL Server], history tables
- restoring databases [SQL Server], status information
- backups [SQL Server], status information
- headers [SQL Server]
- media headers [SQL Server]
- backup history tables [SQL Server]
- viewing backup information
- restoring files [SQL Server], viewing backup information
- restoring databases [SQL Server], history tables
- displaying backup information
- restoring files [SQL Server], status information
- historical information [SQL Server], backups
- database restores [SQL Server], history tables
- restore history tables [SQL Server]
- listing backed up files
ms.assetid: 799b9934-0ec2-4f43-960b-5c9653f18374
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ff1e75cc88e51de75af32bcd9d48860be52d5861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743322"
---
# <a name="backup-history-and-header-information-sql-server"></a><span data-ttu-id="8dcc5-102">バックアップの履歴とヘッダーの情報 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8dcc5-102">Backup History and Header Information (SQL Server)</span></span>
  <span data-ttu-id="8dcc5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースには、サーバー インスタンスで行われた** のすべてのバックアップ操作および復元操作の完全な履歴が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-103">A complete history of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore operations on a server instance is stored in the **msdb** database.</span></span> <span data-ttu-id="8dcc5-104">このトピックでは、バックアップと復元の履歴テーブルに加え、バックアップ履歴へのアクセスに使用する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントについても説明します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-104">This topic introduces the backup and restore history tables and also the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are used to access backup history.</span></span> <span data-ttu-id="8dcc5-105">また、データベース ファイルとトランザクション ログ ファイルの一覧表示が役立つ状況について説明し、メディア ヘッダー情報を使用する状況とバックアップ ヘッダー情報を使用する状況の比較についても説明します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-105">The topic also discusses when listing database and transaction log files is useful and when to use media-header information compared to when to use backup-header information.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8dcc5-106">バックアップと復元の履歴に対する最新の変更情報の損失リスクを管理するために、頻繁に **msdb** をバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-106">To manage the risk of losing recent changes to your backup and restore history, back up **msdb** frequently.</span></span> <span data-ttu-id="8dcc5-107">バックアップする必要があるシステム データベースの詳細については、「[システム データベースのバックアップと復元 &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-107">For information about which of the system databases you must back up, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
 <span data-ttu-id="8dcc5-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-108">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="8dcc5-109">バックアップと復元の履歴テーブル</span><span class="sxs-lookup"><span data-stu-id="8dcc5-109">Backup and Restore History Tables</span></span>](#BnRHistoryTables)  
  
-   [<span data-ttu-id="8dcc5-110">バックアップ履歴にアクセスするための Transact-SQL ステートメント</span><span class="sxs-lookup"><span data-stu-id="8dcc5-110">Transact-SQL Statements for Accessing Backup History</span></span>](#TsqlStatementsForBackupHistory)  
  
-   [<span data-ttu-id="8dcc5-111">データベース ファイルとトランザクション ログ ファイル</span><span class="sxs-lookup"><span data-stu-id="8dcc5-111">Database and Transaction Log Files</span></span>](#ListDbTlogFiles)  
  
-   [<span data-ttu-id="8dcc5-112">メディア ヘッダー情報</span><span class="sxs-lookup"><span data-stu-id="8dcc5-112">Media-Header Information</span></span>](#MediaHeader)  
  
-   [<span data-ttu-id="8dcc5-113">バックアップ ヘッダー情報</span><span class="sxs-lookup"><span data-stu-id="8dcc5-113">Backup-Header Information</span></span>](#BackupHeader)  
  
-   [<span data-ttu-id="8dcc5-114">メディア ヘッダーとバックアップ ヘッダーの情報の比較</span><span class="sxs-lookup"><span data-stu-id="8dcc5-114">Comparison of Media-Header and Backup-Header Information</span></span>](#CompareMediaHeaderBackupHeader)  
  
-   [<span data-ttu-id="8dcc5-115">バックアップの検証</span><span class="sxs-lookup"><span data-stu-id="8dcc5-115">Backup Verification</span></span>](#Verification)  
  
-   [<span data-ttu-id="8dcc5-116">関連タスク</span><span class="sxs-lookup"><span data-stu-id="8dcc5-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="backup-and-restore-history-tables"></a><a name="BnRHistoryTables"></a> <span data-ttu-id="8dcc5-117">バックアップと復元の履歴テーブル</span><span class="sxs-lookup"><span data-stu-id="8dcc5-117">Backup and Restore History Tables</span></span>  
 <span data-ttu-id="8dcc5-118">ここでは、 **msdb** システム データベース内のバックアップ メタデータおよび復元メタデータが保存される履歴テーブルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-118">This section introduces the history tables that store backup and restore metadata in the **msdb** system database.</span></span>  
  
|<span data-ttu-id="8dcc5-119">履歴テーブル</span><span class="sxs-lookup"><span data-stu-id="8dcc5-119">History table</span></span>|<span data-ttu-id="8dcc5-120">説明</span><span class="sxs-lookup"><span data-stu-id="8dcc5-120">Description</span></span>|  
|-------------------|-----------------|  
|[<span data-ttu-id="8dcc5-121">backupfile</span><span class="sxs-lookup"><span data-stu-id="8dcc5-121">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)|<span data-ttu-id="8dcc5-122">バックアップされるデータ ファイルまたはログ ファイルごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-122">Contains one row for each data or log file that is backed up.</span></span>|  
|[<span data-ttu-id="8dcc5-123">backupfilegroup</span><span class="sxs-lookup"><span data-stu-id="8dcc5-123">backupfilegroup</span></span>](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)|<span data-ttu-id="8dcc5-124">バックアップ セットのファイル グループごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-124">Contains a row for each filegroup in a backup set.</span></span>|  
|[<span data-ttu-id="8dcc5-125">backupmediafamily</span><span class="sxs-lookup"><span data-stu-id="8dcc5-125">backupmediafamily</span></span>](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)|<span data-ttu-id="8dcc5-126">メディア ファミリごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-126">Contains one row for each media family.</span></span> <span data-ttu-id="8dcc5-127">メディア ファミリがミラー化されたメディア セット内にある場合は、メディア セット内のミラーごとに個別の行が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-127">If a media family resides in a mirrored media set, the family has a separate row for each mirror in the media set.</span></span>|  
|[<span data-ttu-id="8dcc5-128">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="8dcc5-128">backupmediaset</span></span>](/sql/relational-databases/system-tables/backupmediaset-transact-sql)|<span data-ttu-id="8dcc5-129">バックアップ メディア セットごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-129">Contains one row for each backup media set.</span></span>|  
|[<span data-ttu-id="8dcc5-130">backupset</span><span class="sxs-lookup"><span data-stu-id="8dcc5-130">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)|<span data-ttu-id="8dcc5-131">バックアップ セットごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-131">Contains a row for each backup set.</span></span>|  
|[<span data-ttu-id="8dcc5-132">restorefile</span><span class="sxs-lookup"><span data-stu-id="8dcc5-132">restorefile</span></span>](/sql/relational-databases/system-tables/restorefile-transact-sql)|<span data-ttu-id="8dcc5-133">復元されたファイルごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-133">Contains one row for each restored file.</span></span> <span data-ttu-id="8dcc5-134">これには、ファイル グループ名から間接的に復元されたファイルも含まれます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-134">This includes files restored indirectly by filegroup name.</span></span>|  
|[<span data-ttu-id="8dcc5-135">restorefilegroup</span><span class="sxs-lookup"><span data-stu-id="8dcc5-135">restorefilegroup</span></span>](/sql/relational-databases/system-tables/restorefilegroup-transact-sql)|<span data-ttu-id="8dcc5-136">復元されたファイル グループごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-136">Contains one row for each restored filegroup.</span></span>|  
|[<span data-ttu-id="8dcc5-137">restorehistory</span><span class="sxs-lookup"><span data-stu-id="8dcc5-137">restorehistory</span></span>](/sql/relational-databases/system-tables/restorehistory-transact-sql)|<span data-ttu-id="8dcc5-138">復元操作ごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-138">Contains one row for each restore operation.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="8dcc5-139">復元を実行すると、バックアップ履歴テーブルと復元履歴テーブルが変更されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-139">When a restore is performed, backup history tables and restore history tables are modified.</span></span>  
  
##  <a name="transact-sql-statements-for-accessing-backup-history"></a><a name="TsqlStatementsForBackupHistory"></a> <span data-ttu-id="8dcc5-140">バックアップ履歴にアクセスするための Transact-SQL ステートメント</span><span class="sxs-lookup"><span data-stu-id="8dcc5-140">Transact-SQL Statements for Accessing Backup History</span></span>  
 <span data-ttu-id="8dcc5-141">復元情報ステートメントは、特定のバックアップ履歴テーブルに格納されている情報に対応しています。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-141">The restore information statements correspond with information stored in certain backup history tables.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8dcc5-142">RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY、および RESTORE VERIFYONLY の各 Transact-SQL ステートメントを実行するために CREATE DATABASE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-142">The RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, and RESTORE VERIFYONLY Transact-SQL statements require CREATE DATABASE permission.</span></span> <span data-ttu-id="8dcc5-143">この要件により、以前のバージョンよりも、バックアップ ファイルの安全性が高くなり、バックアップ情報が十分保護されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-143">This requirement secures your backup files and protects your backup information more fully than in previous versions.</span></span> <span data-ttu-id="8dcc5-144">このアクセス許可の詳細については、「[データベースの権限の許可&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-144">For information about this permission, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
|<span data-ttu-id="8dcc5-145">情報ステートメント</span><span class="sxs-lookup"><span data-stu-id="8dcc5-145">Information statement</span></span>|<span data-ttu-id="8dcc5-146">バックアップ履歴テーブル</span><span class="sxs-lookup"><span data-stu-id="8dcc5-146">Backup history table</span></span>|<span data-ttu-id="8dcc5-147">説明</span><span class="sxs-lookup"><span data-stu-id="8dcc5-147">Description</span></span>|  
|---------------------------|--------------------------|-----------------|  
|[<span data-ttu-id="8dcc5-148">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="8dcc5-148">RESTORE FILELISTONLY</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)|[<span data-ttu-id="8dcc5-149">backupfile</span><span class="sxs-lookup"><span data-stu-id="8dcc5-149">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)|<span data-ttu-id="8dcc5-150">指定したバックアップ セットに含まれるデータベース ファイルとログ ファイルの一覧を含む結果セットを返します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-150">Returns a result set that has a list of the database and log files that are contained in the specified backup set.</span></span><br /><br /> <span data-ttu-id="8dcc5-151">詳細については、このトピックの「データベース ファイルとトランザクション ログ ファイルの一覧表示」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-151">For more information, see "Listing Database and Transaction Log Files," later in this topic.</span></span>|  
|[<span data-ttu-id="8dcc5-152">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="8dcc5-152">RESTORE HEADERONLY</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)|[<span data-ttu-id="8dcc5-153">backupset</span><span class="sxs-lookup"><span data-stu-id="8dcc5-153">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)|<span data-ttu-id="8dcc5-154">特定のバックアップ デバイス上のすべてのバックアップ セットについて、バックアップ ヘッダーに関するすべての情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-154">Retrieves all the backup header information for all backup sets on a particular backup device.</span></span> <span data-ttu-id="8dcc5-155">RESTORE HEADERONLY を実行して得られる結果は、結果セットです。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-155">The result from executing RESTORE HEADERONLY is a result set.</span></span><br /><br /> <span data-ttu-id="8dcc5-156">詳細については、このトピックの「バックアップ ヘッダー情報の表示」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-156">For more information, see "Viewing the Backup-Header Information," later in this topic.</span></span>|  
|[<span data-ttu-id="8dcc5-157">RESTORE LABELONLY</span><span class="sxs-lookup"><span data-stu-id="8dcc5-157">RESTORE LABELONLY</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)|[<span data-ttu-id="8dcc5-158">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="8dcc5-158">backupmediaset</span></span>](/sql/relational-databases/system-tables/backupmediaset-transact-sql)|<span data-ttu-id="8dcc5-159">指定したバックアップ デバイス上のバックアップ メディアに関する情報を含む結果セットを返します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-159">Returns a result set that contains information about the backup media on a specified backup device.</span></span><br /><br /> <span data-ttu-id="8dcc5-160">詳細については、このトピックの「メディア ヘッダー情報の表示」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-160">For more information, see "Viewing the Media-Header Information," later in this topic.</span></span>|  
  
##  <a name="database-and-transaction-log-files"></a><a name="ListDbTlogFiles"></a> <span data-ttu-id="8dcc5-161">データベース ファイルとトランザクション ログ ファイル</span><span class="sxs-lookup"><span data-stu-id="8dcc5-161">Database and Transaction Log Files</span></span>  
 <span data-ttu-id="8dcc5-162">バックアップ内のデータベース ファイルおよびトランザクション ログ ファイルの一覧を表示すると、論理名、物理名、ファイルの種類 (データベースまたはログ)、ファイル グループのメンバーシップ、ファイルのサイズ (バイト単位)、ファイルの最大許容サイズ、および定義済みのファイル拡張サイズ (バイト単位) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-162">Information that is displayed when the database and transaction log files are listed in a backup includes the logical name, physical name, file type (database or log), filegroup membership, file size (in bytes), the maximum allowed file size, and the predefined file growth size (in bytes).</span></span> <span data-ttu-id="8dcc5-163">この情報は、次のような場合に、データベース バックアップを復元する前にそのバックアップ内のファイルの名前を調べる際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-163">This information is useful, in the following situations, to determine the names of the files in a database backup before you restore the database backup:</span></span>  
  
-   <span data-ttu-id="8dcc5-164">データベースの 1 つ以上のファイルが格納されているディスク ドライブに障害が発生した場合。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-164">You have lost a disk drive that contains one or more of the files for a database.</span></span>  
  
     <span data-ttu-id="8dcc5-165">データベース バックアップ内のファイルを一覧表示して、影響を受けたファイルを調べ、そのファイルはデータベース全体の復元時に別のドライブに復元することができます。影響を受けたファイルだけを復元して、データベースのバックアップ後に作成されたすべてのトランザクション ログのバックアップを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-165">You can list the files in the database backup to determine which files were affected, and then restore those files onto a different drive when you restore the whole database; or restore just those files and apply any transaction log backups created since the database was backed up.</span></span>  
  
-   <span data-ttu-id="8dcc5-166">ディレクトリ構造やネットワーク ドライブが割り当てられていない別のサーバーにデータベースを復元する場合。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-166">You are restoring a database from one server onto another server, but the directory structure and drive mapping does not exist on the server.</span></span>  
  
     <span data-ttu-id="8dcc5-167">バックアップ内のファイルを一覧表示すると、影響を受けるファイルを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-167">Listing the files in the backup let you determine which files are affected.</span></span> <span data-ttu-id="8dcc5-168">たとえば、ドライブ E に復元する必要があるファイルがバックアップに含まれているのに、復元先サーバーにドライブ E が存在しない場合があります。この場合、ファイルの復元時に、ドライブ Z など、別の場所にファイルを配置し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-168">For example, the backup contains a file that it has to restore to drive E, but the destination server does not have a drive E. The file must be relocated to another location, such as drive Z, when the file is restored.</span></span>  
  
##  <a name="media-header-information"></a><a name="MediaHeader"></a> <span data-ttu-id="8dcc5-169">メディア ヘッダー情報</span><span class="sxs-lookup"><span data-stu-id="8dcc5-169">Media-Header Information</span></span>  
 <span data-ttu-id="8dcc5-170">メディア ヘッダーを表示すると、メディア上のバックアップではなくメディアそのものに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-170">Viewing the media header displays information about the media itself, instead of about the backups on the media.</span></span> <span data-ttu-id="8dcc5-171">メディア ヘッダー情報として、メディア名、説明、メディア ヘッダーを作成したソフトウェアの名前、およびメディア ヘッダーが書き込まれた日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-171">Media header information that is displayed includes the media name, description, name of the software that created the media header, and the date the media header was written.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8dcc5-172">メディア ヘッダーの表示にはごくわずかな時間しかかかりません。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-172">Viewing the media header is quick.</span></span>  
  
 <span data-ttu-id="8dcc5-173">詳細については、このトピックの後の方の「 [メディア ヘッダーとバックアップ ヘッダーの情報の比較](#CompareMediaHeaderBackupHeader)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-173">For more information, see [Comparison of Media-Header and Backup-Header Information](#CompareMediaHeaderBackupHeader), later in this topic.</span></span>  
  
##  <a name="backup-header-information"></a><a name="BackupHeader"></a> <span data-ttu-id="8dcc5-174">バックアップ ヘッダー情報</span><span class="sxs-lookup"><span data-stu-id="8dcc5-174">Backup-Header Information</span></span>  
 <span data-ttu-id="8dcc5-175">バックアップ ヘッダーを表示すると、メディア上のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ セットおよび[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のバックアップ セットに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-175">Viewing the backup header displays information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup sets on the media.</span></span> <span data-ttu-id="8dcc5-176">表示される情報には、使用しているバックアップ デバイスの種類、バックアップの種類 (データベース、トランザクション、ファイル、差分データベースなど)、およびバックアップの開始と終了の日時が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-176">Information that is displayed includes the types of backup devices that are used, the types of backup (for example, database, transaction, file, or differential database), and backup start and stop date/time information.</span></span> <span data-ttu-id="8dcc5-177">この情報は、テープ上のどのバックアップ セットを復元するかを判断したり、メディアに書き込まれているバックアップを調べる場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-177">This information is useful when you have to determine which backup set on the tape to restore, or the backups that are contained on the media.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8dcc5-178">メディア上の各バックアップに関する情報を表示するにはメディア全体をスキャンする必要があるため、大容量のテープの場合はバックアップ ヘッダー情報を表示するのに時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-178">Viewing backup header information can take a long time for high-capacity tapes, because the whole media must be scanned to display information about each backup on the media.</span></span>  
  
 <span data-ttu-id="8dcc5-179">詳細については、このトピックの後の方の「 [メディア ヘッダーとバックアップ ヘッダーの情報の比較](#CompareMediaHeaderBackupHeader)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-179">For more information, see [Comparison of Media-Header and Backup-Header Information](#CompareMediaHeaderBackupHeader), later in this topic.</span></span>  
  
### <a name="which-backup-set-to-restore"></a><span data-ttu-id="8dcc5-180">復元するバックアップ セットの特定</span><span class="sxs-lookup"><span data-stu-id="8dcc5-180">Which Backup Set to Restore</span></span>  
 <span data-ttu-id="8dcc5-181">バックアップ ヘッダーの情報を使用して、復元するバックアップ セットを識別できます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-181">You can use information in the backup header to identify which backup set to restore.</span></span> <span data-ttu-id="8dcc5-182">バックアップ メディアの各バックアップ セットには、データベース エンジンによって番号が付けられます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-182">The Database Engine numbers each backup set on the backup media.</span></span> <span data-ttu-id="8dcc5-183">この番号を使用すると、復元するバックアップ セットをメディア内での位置によって識別できます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-183">This lets you identify the backup set you want to restore by using its position on the media.</span></span> <span data-ttu-id="8dcc5-184">たとえば、次のメディアには 3 つのバックアップ セットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-184">For example, the following media contains three backup sets.</span></span>  
  
 <span data-ttu-id="8dcc5-185">![SQL Server バックアップ セットを含むバックアップ メディア](../../database-engine/media/bnr-media-backup-sets.gif "SQL Server バックアップ セットを含むバックアップ メディア")</span><span class="sxs-lookup"><span data-stu-id="8dcc5-185">![Backup media containing SQL Server backup sets](../../database-engine/media/bnr-media-backup-sets.gif "Backup media containing SQL Server backup sets")</span></span>  
  
 <span data-ttu-id="8dcc5-186">特定のバックアップ セットを復元するには、復元対象のバックアップ セットの位置番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-186">To restore a specific backup set, specify the position number of the backup set you want to restore.</span></span> <span data-ttu-id="8dcc5-187">たとえば、2 番目のバックアップ セットを復元するには、復元するバックアップ セットとして「2」を指定します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-187">For example, to restore the second backup set, specify 2 as the backup set to restore.</span></span>  
  
##  <a name="comparison-of-media-header-and-backup-header-information"></a><a name="CompareMediaHeaderBackupHeader"></a> <span data-ttu-id="8dcc5-188">メディア ヘッダーとバックアップ ヘッダーの情報の比較</span><span class="sxs-lookup"><span data-stu-id="8dcc5-188">Comparison of Media-Header and Backup-Header Information</span></span>  
 <span data-ttu-id="8dcc5-189">次の図で、バックアップ ヘッダー情報とメディア ヘッダー情報の表示の違いを例示します。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-189">The following illustration provides an example of the differences between viewing backup-header and media-header information.</span></span> <span data-ttu-id="8dcc5-190">メディア ヘッダーを取得するには、テープの先頭にある情報のみを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-190">Obtaining the media header requires retrieving information from only the start of the tape.</span></span> <span data-ttu-id="8dcc5-191">バックアップ ヘッダーを取得するには、テープ全体をスキャンして各バックアップ セットのヘッダーを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-191">Obtaining the backup header requires scanning the whole tape to look at the header of every backup set.</span></span>  
  
 <span data-ttu-id="8dcc5-192">![3 つの SQL Server バックアップ セットを含むメディア セット](../../database-engine/media/bnr-media-label.gif "3 つの SQL Server バックアップ セットを含むメディア セット")</span><span class="sxs-lookup"><span data-stu-id="8dcc5-192">![Media set containing three SQL Server backup sets](../../database-engine/media/bnr-media-label.gif "Media set containing three SQL Server backup sets")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8dcc5-193">複数のメディア ファミリを持ったメディア セットを使用すると、メディア ヘッダーおよびバックアップ セットがすべてのメディア ファミリに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-193">When you use media sets that have multiple media families, the media header and backup set are written to all media families.</span></span> <span data-ttu-id="8dcc5-194">したがって、このような報告操作には、メディア ファミリを 1 つ提供するだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-194">Therefore, you only have to provide a single media family for these reporting operations.</span></span>  
  
 <span data-ttu-id="8dcc5-195">メディア ヘッダーの表示方法については、このトピックの「メディア ヘッダー情報の表示」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-195">For information about how to view the media-header, see "Viewing the Media-Header Information," earlier in this topic.</span></span>  
  
 <span data-ttu-id="8dcc5-196">バックアップ デバイス上のすべてのバックアップ セットに関するバックアップ ヘッダー情報の表示方法については、このトピックの「バックアップ ヘッダー情報の表示」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-196">For information about how to view the backup header information for all backup sets on a backup device, see "Viewing the Backup-Header Information," earlier in this topic.</span></span>  
  
##  <a name="backup-verification"></a><a name="Verification"></a> <span data-ttu-id="8dcc5-197">バックアップの検証</span><span class="sxs-lookup"><span data-stu-id="8dcc5-197">Backup Verification</span></span>  
 <span data-ttu-id="8dcc5-198">必須ではありませんが、バックアップの確認は役に立つ作業です。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-198">Although not required, verifying a backup is a useful practice.</span></span> <span data-ttu-id="8dcc5-199">バックアップを確認することで、バックアップが物理的に損傷していないことが確認されます。これにより、バックアップのすべてのファイルの読み取りと復元が可能であること、必要なときにそのバックアップを復元できることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-199">Verifying a backup checks that the backup is intact physically, to ensure that all the files in the backup are readable and can be restored, and that you can restore your backup in the event you need to use it.</span></span> <span data-ttu-id="8dcc5-200">バックアップの確認では、バックアップのデータの構造は確認されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-200">It is important to understand that verifying a backup does not verify the structure of the data on the backup.</span></span> <span data-ttu-id="8dcc5-201">ただし、WITH CHECKSUMS を使用してバックアップが作成された場合、WITH CHECKSUMS を使用してバックアップを確認すると、バックアップのデータの信頼性がわかります。</span><span class="sxs-lookup"><span data-stu-id="8dcc5-201">However, if the backup was created using WITH CHECKSUMS, verifying the backup using WITH CHECKSUMS can provide a good indication of the reliability of the data on the backup.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8dcc5-202">関連タスク</span><span class="sxs-lookup"><span data-stu-id="8dcc5-202">Related Tasks</span></span>  
 <span data-ttu-id="8dcc5-203">**バックアップ履歴テーブルと復元履歴テーブルから古い行を削除するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-203">**To delete old rows from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="8dcc5-204">sp_delete_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-204">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
 <span data-ttu-id="8dcc5-205">**バックアップ履歴テーブルと復元履歴テーブルから特定のデータベースのすべての行を削除するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-205">**To delete all rows for a specific database from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="8dcc5-206">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-206">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql)  
  
 <span data-ttu-id="8dcc5-207">**バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-207">**To view the data and log files in a backup set**</span></span>  
  
-   [<span data-ttu-id="8dcc5-208">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-208">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
-   <span data-ttu-id="8dcc5-209"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="8dcc5-209"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A> (SMO)</span></span>  
  
 <span data-ttu-id="8dcc5-210">**メディア ヘッダー情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-210">**To view media header information**</span></span>  
  
-   [<span data-ttu-id="8dcc5-211">RESTORE LABELONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-211">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)  
  
-   [<span data-ttu-id="8dcc5-212">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-212">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="8dcc5-213">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-213">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   <span data-ttu-id="8dcc5-214"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="8dcc5-214"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="8dcc5-215">**バックアップ ヘッダー情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-215">**To view backup header information**</span></span>  
  
-   [<span data-ttu-id="8dcc5-216">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-216">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="8dcc5-217">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-217">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="8dcc5-218">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-218">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   <span data-ttu-id="8dcc5-219"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="8dcc5-219"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="8dcc5-220">**バックアップ履歴テーブルと復元履歴テーブルから古い行を削除するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-220">**To delete old rows from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="8dcc5-221">sp_delete_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-221">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
 <span data-ttu-id="8dcc5-222">**バックアップ履歴テーブルと復元履歴テーブルから特定のデータベースのすべての行を削除するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-222">**To delete all rows for a specific database from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="8dcc5-223">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-223">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql)  
  
 <span data-ttu-id="8dcc5-224">**メディア ヘッダー情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-224">**To view media header information**</span></span>  
  
-   [<span data-ttu-id="8dcc5-225">RESTORE LABELONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-225">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)  
  
-   [<span data-ttu-id="8dcc5-226">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-226">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="8dcc5-227">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-227">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   <span data-ttu-id="8dcc5-228"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="8dcc5-228"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="8dcc5-229">**バックアップ ヘッダー情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-229">**To view backup header information**</span></span>  
  
-   [<span data-ttu-id="8dcc5-230">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-230">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="8dcc5-231">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-231">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="8dcc5-232">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-232">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   <span data-ttu-id="8dcc5-233"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="8dcc5-233"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="8dcc5-234">**バックアップ セットに含まれているファイルを表示するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-234">**To view the files in a backup set**</span></span>  
  
-   [<span data-ttu-id="8dcc5-235">バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-235">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="8dcc5-236">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-236">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
 <span data-ttu-id="8dcc5-237">**バックアップを検証するには**</span><span class="sxs-lookup"><span data-stu-id="8dcc5-237">**To verify a backup**</span></span>  
  
-   [<span data-ttu-id="8dcc5-238">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-238">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
-   <span data-ttu-id="8dcc5-239"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="8dcc5-239"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dcc5-240">参照</span><span class="sxs-lookup"><span data-stu-id="8dcc5-240">See Also</span></span>  
 <span data-ttu-id="8dcc5-241">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8dcc5-241">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="8dcc5-242">[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8dcc5-242">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="8dcc5-243">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8dcc5-243">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="8dcc5-244">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8dcc5-244">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 [<span data-ttu-id="8dcc5-245">バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8dcc5-245">Possible Media Errors During Backup and Restore &#40;SQL Server&#41;</span></span>](possible-media-errors-during-backup-and-restore-sql-server.md)  
  
  
