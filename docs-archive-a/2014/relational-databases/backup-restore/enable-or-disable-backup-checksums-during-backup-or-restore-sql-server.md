---
title: バックアップ中または復元中にバックアップ チェックサムを有効または無効にする (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup checksums [SQL Server]
- disabling checksums
- checksums [SQL Server]
ms.assetid: 6786bd1e-ad97-430a-8dfb-d4ba952d6c4d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a239dcdfca689be8555117104264d66a2ac037f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742333"
---
# <a name="enable-or-disable-backup-checksums-during-backup-or-restore-sql-server"></a><span data-ttu-id="a65c6-102">バックアップ中または復元中にバックアップ チェックサムを有効または無効にする (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a65c6-102">Enable or Disable Backup Checksums During Backup or Restore (SQL Server)</span></span>
  <span data-ttu-id="a65c6-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でデータベースをバックアップまたは復元するときにバックアップ チェックサムを有効または無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-103">This topic describes how to enable or disable backup checksums when you are backing up or restoring a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a65c6-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a65c6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a65c6-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a65c6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a65c6-106">Security</span><span class="sxs-lookup"><span data-stu-id="a65c6-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a65c6-107">**バックアップ チェックサムを有効または無効にする方法:**</span><span class="sxs-lookup"><span data-stu-id="a65c6-107">**To enable or disable backup checksums, using:**</span></span>  
  
     [<span data-ttu-id="a65c6-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a65c6-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a65c6-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a65c6-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a65c6-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="a65c6-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a65c6-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a65c6-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a65c6-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="a65c6-112">Permissions</span></span>  
 <span data-ttu-id="a65c6-113">BACKUP</span><span class="sxs-lookup"><span data-stu-id="a65c6-113">BACKUP</span></span>  
 <span data-ttu-id="a65c6-114">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="a65c6-114">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="a65c6-115">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="a65c6-115">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a65c6-116">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a65c6-116">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="a65c6-117">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="a65c6-117">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="a65c6-118">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a65c6-118">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
 <span data-ttu-id="a65c6-119">RESTORE</span><span class="sxs-lookup"><span data-stu-id="a65c6-119">RESTORE</span></span>  
 <span data-ttu-id="a65c6-120">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a65c6-120">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="a65c6-121">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="a65c6-121">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="a65c6-122">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="a65c6-122">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="a65c6-123">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="a65c6-123">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a65c6-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a65c6-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-or-disable-checksums-during-a-backup-operation"></a><span data-ttu-id="a65c6-125">バックアップ操作中にバックアップ チェックサムを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="a65c6-125">To enable or disable checksums during a backup operation</span></span>  
  
1.  <span data-ttu-id="a65c6-126">「 [データベースのバックアップを作成する](create-a-full-database-backup-sql-server.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a65c6-126">Follow the steps to [create a database backup](create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="a65c6-127">**[オプション]** ページの **[信頼性]** セクションで、 **[メディアに書き込む前にチェックサムを行う]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a65c6-127">On the **Options** page, in the **Reliability** section, click **Perform checksum before writing to media**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a65c6-128">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a65c6-128">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-backup-operation"></a><span data-ttu-id="a65c6-129">バックアップ操作のバックアップ チェックサムを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="a65c6-129">To enable or disable backup checksum for a backup operation</span></span>  
  
1.  <span data-ttu-id="a65c6-130">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-130">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a65c6-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a65c6-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a65c6-132">[BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントでバックアップ チェックサムを有効にするのには、WITH CHECKSUM オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-132">To enable backup checksums in a [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the WITH CHECKSUM option.</span></span> <span data-ttu-id="a65c6-133">バックアップ チェックサムを無効にするには、WITH NO_CHECKSUM オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-133">To disable backup checksums, specify the WITH NO_CHECKSUM option.</span></span> <span data-ttu-id="a65c6-134">これは圧縮されたバックアップ以外の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="a65c6-134">This is the default behavior, except for a compressed backup.</span></span> <span data-ttu-id="a65c6-135">次の例では、チェックサムを実行するように指定します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-135">The following example specifies that checksums be performed.</span></span>  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-restore-operation"></a><span data-ttu-id="a65c6-136">復元操作のバックアップ チェックサムを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="a65c6-136">To enable or disable backup checksum for a restore operation</span></span>  
  
1.  <span data-ttu-id="a65c6-137">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a65c6-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a65c6-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a65c6-139">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントでバックアップ チェックサムを有効にするのには、WITH CHECKSUM オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-139">To enable backup checksums in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify the WITH CHECKSUM option.</span></span> <span data-ttu-id="a65c6-140">これは圧縮されたバックアップの既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="a65c6-140">This is the default behavior for a compressed backup.</span></span> <span data-ttu-id="a65c6-141">バックアップ チェックサムを無効にするには、WITH NO_CHECKSUM オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-141">To disable backup checksums, specify the WITH NO_CHECKSUM option.</span></span> <span data-ttu-id="a65c6-142">これは圧縮されたバックアップ以外の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="a65c6-142">This is the default behavior, except for a compressed backup.</span></span> <span data-ttu-id="a65c6-143">次の例では、バックアップ チェックサムを実行するように指定します。</span><span class="sxs-lookup"><span data-stu-id="a65c6-143">The following example specifies that backup checksums be performed.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
> [!WARNING]  
>  <span data-ttu-id="a65c6-144">復元操作に対し CHECKSUM を明示的に要求した場合、およびバックアップにバックアップ チェックサムが含まれている場合、バックアップ チェックサムおよびページ チェックサムの両方が検証されます (既定の動作です)。</span><span class="sxs-lookup"><span data-stu-id="a65c6-144">If you explicitly request CHECKSUM for a restore operation and if the backup contains backup checksums, backup checksums and page checksums are both verified, as in the default case.</span></span> <span data-ttu-id="a65c6-145">ただし、バックアップ セットにバックアップ チェックサムがない場合、復元操作は失敗し、チェックサムがないことを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a65c6-145">However, if the backup set lacks backup checksums, the restore operation fails with a message indicating that checksums are not present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65c6-146">参照</span><span class="sxs-lookup"><span data-stu-id="a65c6-146">See Also</span></span>  
 <span data-ttu-id="a65c6-147">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a65c6-147">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="a65c6-148">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a65c6-148">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="a65c6-149">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a65c6-149">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="a65c6-150">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a65c6-150">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="a65c6-151">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a65c6-151">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="a65c6-152">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a65c6-152">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="a65c6-153">[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a65c6-153">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="a65c6-154">[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a65c6-154">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="a65c6-155">バックアップまたは復元の操作をエラー発生後に続行するか停止するかを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a65c6-155">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
  
