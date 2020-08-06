---
title: エラー (SQL Server) を検出した後で、バックアップまたは復元操作を続行するか停止するかを指定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], backups
- backing up databases [SQL Server], errors
- backups [SQL Server], errors
- database backups [SQL Server], errors
ms.assetid: 042be17a-b9b0-4629-b6bb-b87a8bc6c316
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 87cccec6f7eea18f2750d3b0be81b577b0eb170a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644482"
---
# <a name="specify-whether-a-backup-or-restore-operation-continues-or-stops-after-encountering-an-error-sql-server"></a><span data-ttu-id="01605-102">バックアップまたは復元の操作をエラー発生後に続行するか停止するかを指定する (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="01605-102">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error (SQL Server)</span></span>
  <span data-ttu-id="01605-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、エラーが発生したときにバックアップ操作または復元操作を中止するか続行するかを指定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="01605-103">This topic describes how to specify whether a backup or restore operation continues or stops after encountering an error in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="01605-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="01605-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="01605-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="01605-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="01605-106">Security</span><span class="sxs-lookup"><span data-stu-id="01605-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="01605-107">**エラーが発生したときにバックアップ操作または復元操作を続行するかどうかを指定する方法:**</span><span class="sxs-lookup"><span data-stu-id="01605-107">**To specify whether a backup or restore operation continues after encountering an error, using:**</span></span>  
  
     [<span data-ttu-id="01605-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="01605-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="01605-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="01605-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="01605-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="01605-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="01605-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01605-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="01605-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="01605-112">Permissions</span></span>  
 <span data-ttu-id="01605-113">BACKUP</span><span class="sxs-lookup"><span data-stu-id="01605-113">BACKUP</span></span>  
 <span data-ttu-id="01605-114">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="01605-114">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="01605-115">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="01605-115">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="01605-116">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="01605-116">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="01605-117">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="01605-117">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="01605-118">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01605-118">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
 <span data-ttu-id="01605-119">RESTORE</span><span class="sxs-lookup"><span data-stu-id="01605-119">RESTORE</span></span>  
 <span data-ttu-id="01605-120">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01605-120">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="01605-121">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="01605-121">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="01605-122">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="01605-122">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="01605-123">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="01605-123">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="01605-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="01605-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-whether-backup-continues-or-stops-after-an-error-is-encountered"></a><span data-ttu-id="01605-125">エラーが発生したときにバックアップ操作を続行するか停止するかを指定するには</span><span class="sxs-lookup"><span data-stu-id="01605-125">To specify whether backup continues or stops after an error is encountered</span></span>  
  
1.  <span data-ttu-id="01605-126">「 [データベースのバックアップを作成する](create-a-full-database-backup-sql-server.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="01605-126">Follow the steps to [create a database backup](create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="01605-127">**[オプション]** ページの **[信頼性]** セクションで、 **[メディアに書き込む前にチェックサムを行う]** と **[エラーのまま続行する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01605-127">On the **Options** page, in the **Reliability** section, click **Perform checksum before writing to media** and **Continue on error**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="01605-128">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="01605-128">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-whether-a-backup-operation-continues-or-stops-after-encountering-an-error"></a><span data-ttu-id="01605-129">エラーが発生したときにバックアップ操作を続行するか停止するかを指定するには</span><span class="sxs-lookup"><span data-stu-id="01605-129">To specify whether a backup operation continues or stops after encountering an error</span></span>  
  
1.  <span data-ttu-id="01605-130">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="01605-130">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="01605-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01605-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="01605-132">[BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントに、続行する場合は CONTINUE_AFTER ERROR オプションを、停止する場合は STOP_ON_ERROR オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="01605-132">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the CONTINUE_AFTER ERROR option to continue or the STOP_ON_ERROR option to stop.</span></span> <span data-ttu-id="01605-133">既定の動作は、エラーが発生した場合は停止することです。</span><span class="sxs-lookup"><span data-stu-id="01605-133">The default behavior is to stop after encountering an error.</span></span> <span data-ttu-id="01605-134">次の例では、エラーが発生してもバックアップ操作を続行するように命令します。</span><span class="sxs-lookup"><span data-stu-id="01605-134">This example instructs the backup operation to continue despite encountering an error.</span></span>  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
#### <a name="to-specify-whether-a-restore-operation-continues-or-stops-after-encountering-an-error"></a><span data-ttu-id="01605-135">エラーが発生したときに復元操作を続行するか停止するかを指定するには</span><span class="sxs-lookup"><span data-stu-id="01605-135">To specify whether a restore operation continues or stops after encountering an error</span></span>  
  
1.  <span data-ttu-id="01605-136">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="01605-136">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="01605-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01605-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="01605-138">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントに、続行する場合は CONTINUE_AFTER ERROR オプションを、停止する場合は STOP_ON_ERROR オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="01605-138">In the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify the CONTINUE_AFTER ERROR option to continue or the STOP_ON_ERROR option to stop.</span></span> <span data-ttu-id="01605-139">既定の動作は、エラーが発生した場合は停止することです。</span><span class="sxs-lookup"><span data-stu-id="01605-139">The default behavior is to stop after encountering an error.</span></span> <span data-ttu-id="01605-140">次の例では、エラーが発生しても復元操作を続行するように命令します。</span><span class="sxs-lookup"><span data-stu-id="01605-140">This example instructs the restore operation to continue despite encountering an error.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'   
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="01605-141">参照</span><span class="sxs-lookup"><span data-stu-id="01605-141">See Also</span></span>  
 <span data-ttu-id="01605-142">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01605-142">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="01605-143">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01605-143">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="01605-144">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01605-144">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="01605-145">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01605-145">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="01605-146">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01605-146">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="01605-147">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01605-147">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="01605-148">[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01605-148">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="01605-149">[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="01605-149">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="01605-150">バックアップ中または復元中にバックアップ チェックサムを有効または無効にする &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="01605-150">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
  
