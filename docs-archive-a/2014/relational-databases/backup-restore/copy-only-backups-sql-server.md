---
title: コピーのみのバックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- copy-only backups [SQL Server]
- COPY_ONLY option [BACKUP statement]
- backups [SQL Server], copy-only backups
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc74d7b1bba2a0163ac9edefb5d465c54ef6296c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645674"
---
# <a name="copy-only-backups-sql-server"></a><span data-ttu-id="55594-102">コピーのみのバックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="55594-102">Copy-Only Backups (SQL Server)</span></span>
  <span data-ttu-id="55594-103">*コピーのみのバックアップ*は、従来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップのシーケンスから独立した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップです。</span><span class="sxs-lookup"><span data-stu-id="55594-103">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="55594-104">通常、バックアップを行うとデータベースが変更され、その後のバックアップの復元方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="55594-104">Usually, taking a backup changes the database and affects how later backups are restored.</span></span> <span data-ttu-id="55594-105">ただし、データベース全体のバックアップや復元の手順に影響を与えない、特殊な目的にバックアップを行うと役に立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="55594-105">However, occasionally, it is useful to take a backup for a special purpose without affecting the overall backup and restore procedures for the database.</span></span> <span data-ttu-id="55594-106">このため、コピーのみのバックアップが導入されました。</span><span class="sxs-lookup"><span data-stu-id="55594-106">Copy-only backups serve this purpose.</span></span>  
  
 <span data-ttu-id="55594-107">コピーのみのバックアップには、次の種類があります。</span><span class="sxs-lookup"><span data-stu-id="55594-107">The types of copy-only backups are as follows:</span></span>  
  
-   <span data-ttu-id="55594-108">コピーのみの完全バックアップ (すべての復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="55594-108">Copy-only full backups (all recovery models)</span></span>  
  
     <span data-ttu-id="55594-109">コピーのみのバックアップは、差分ベースまたは差分バックアップとして使用できません。また、差分ベースに影響しません。</span><span class="sxs-lookup"><span data-stu-id="55594-109">A copy-only backup cannot serve as a differential base or differential backup and does not affect the differential base.</span></span>  
  
     <span data-ttu-id="55594-110">コピーのみの完全バックアップも、他の完全バックアップと同じ方法で復元できます。</span><span class="sxs-lookup"><span data-stu-id="55594-110">Restoring a copy-only full backup is the same as restoring any other full backup.</span></span>  
  
-   <span data-ttu-id="55594-111">コピーのみのログ バックアップ (完全復旧モデルおよび一括ログ復旧モデルのみ)</span><span class="sxs-lookup"><span data-stu-id="55594-111">Copy-only log backups (full recovery model and bulk-logged recovery model only)</span></span>  
  
     <span data-ttu-id="55594-112">コピーのみのログ バックアップは、既存のログ アーカイブ ポイントを保持するため、定期的なログ バックアップの一連の作業に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="55594-112">A copy-only log backup preserves the existing log archive point and, therefore, does not affect the sequencing of regular log backups.</span></span> <span data-ttu-id="55594-113">通常、コピーのみのログ バックアップは不要です。</span><span class="sxs-lookup"><span data-stu-id="55594-113">Copy-only log backups are typically unnecessary.</span></span> <span data-ttu-id="55594-114">新しい定期的なログ バックアップを (WITH NORECOVERY を使用して) 作成してから、そのバックアップを、復元シーケンスに必要なすべての以前のログ バックアップと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="55594-114">Instead, you can create a new routine log backup (using WITH NORECOVERY) and use that backup together with any previous log backups that are required for the restore sequence.</span></span> <span data-ttu-id="55594-115">ただし、コピーのみのログ バックアップは、オンライン復元を実行する際に役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="55594-115">However, a copy-only log backup can sometimes be useful for performing an online restore.</span></span> <span data-ttu-id="55594-116">この例については、「[例:読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55594-116">For an example of this, see [Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md).</span></span>  
  
     <span data-ttu-id="55594-117">コピーのみのバックアップの後、トランザクション ログは切り捨てられません。</span><span class="sxs-lookup"><span data-stu-id="55594-117">The transaction log is never truncated after a copy-only backup.</span></span>  
  
 <span data-ttu-id="55594-118">コピーのみのバックアップは、 **backupset** テーブルの [is_copy_only](/sql/relational-databases/system-tables/backupset-transact-sql) 列に記録されます。</span><span class="sxs-lookup"><span data-stu-id="55594-118">Copy-only backups are recorded in the **is_copy_only** column of the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) table.</span></span>  
  
## <a name="to-create-a-copy-only-backup"></a><span data-ttu-id="55594-119">コピーのみのバックアップを作成するには</span><span class="sxs-lookup"><span data-stu-id="55594-119">To Create a Copy-Only Backup</span></span>  
 <span data-ttu-id="55594-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用してコピーのみのバックアップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="55594-120">You can create a copy-only backup by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="55594-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="55594-121">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="55594-122">**[データベースのバックアップ]** ダイアログ ボックスの **[全般]** ページで、**[バックアップのみコピーする]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="55594-122">On the **General** page of the **Back Up Database** dialog box, select the **Copy Only Backup** option.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="55594-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="55594-123">Using Transact-SQL</span></span>  
 <span data-ttu-id="55594-124">必須の [!INCLUDE[tsql](../../../includes/tsql-md.md)] 構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55594-124">The essential [!INCLUDE[tsql](../../../includes/tsql-md.md)] syntax is as follows:</span></span>  
  
-   <span data-ttu-id="55594-125">コピーのみの完全バックアップの場合:</span><span class="sxs-lookup"><span data-stu-id="55594-125">For a copy-only full backup:</span></span>  
  
     <span data-ttu-id="55594-126">データベース*database_name*を \<backup_device*> \*...COPY_ONLY...</span><span class="sxs-lookup"><span data-stu-id="55594-126">BACKUP DATABASE *database_name* TO \<backup_device*>\* ... WITH COPY_ONLY ...</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="55594-127">COPY_ONLY は、DIFFERENTIAL オプションと共に指定した場合には機能しません。</span><span class="sxs-lookup"><span data-stu-id="55594-127">COPY_ONLY has no effect when specified with the DIFFERENTIAL option.</span></span>  
  
-   <span data-ttu-id="55594-128">コピーのみのログ バックアップの場合:</span><span class="sxs-lookup"><span data-stu-id="55594-128">For a copy-only log backup:</span></span>  
  
     <span data-ttu-id="55594-129">バックアップログ*database_name* .. *\<*backup_device*>* .COPY_ONLY...</span><span class="sxs-lookup"><span data-stu-id="55594-129">BACKUP LOG *database_name* TO *\<*backup_device*>* ... WITH COPY_ONLY ...</span></span>  
  
###  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="55594-130">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="55594-130">Using PowerShell</span></span>  
  
<span data-ttu-id="55594-131">`Backup-SqlDatabase` パラメーターを指定して `-CopyOnly` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="55594-131">Use the `Backup-SqlDatabase` cmdlet with the `-CopyOnly` parameter.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="55594-132">関連タスク</span><span class="sxs-lookup"><span data-stu-id="55594-132">Related Tasks</span></span>  

### <a name="to-create-a-full-or-log-backup"></a><span data-ttu-id="55594-133">完全バックアップまたはログ バックアップを作成するには</span><span class="sxs-lookup"><span data-stu-id="55594-133">To create a full or log backup</span></span>
  
-   [<span data-ttu-id="55594-134">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="55594-134">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="55594-135">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="55594-135">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
### <a name="to-view-copy-only-backups"></a><span data-ttu-id="55594-136">コピーのみのバックアップを表示するには</span><span class="sxs-lookup"><span data-stu-id="55594-136">To view copy-only backups</span></span>
  
-   [<span data-ttu-id="55594-137">backupset &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="55594-137">backupset &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
### <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><span data-ttu-id="55594-138">SQL Server PowerShell プロバイダーを設定して使用するには</span><span class="sxs-lookup"><span data-stu-id="55594-138">To set up and use the SQL Server PowerShell provider</span></span>
  
-   [<span data-ttu-id="55594-139">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="55594-139">SQL Server PowerShell Provider</span></span>](../../powershell/sql-server-powershell-provider.md)  

## <a name="see-also"></a><span data-ttu-id="55594-140">参照</span><span class="sxs-lookup"><span data-stu-id="55594-140">See Also</span></span>  
 <span data-ttu-id="55594-141">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="55594-141">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="55594-142">[復旧モデル &#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="55594-142">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="55594-143">[バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="55594-143">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="55594-144">復元と復旧の概要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="55594-144">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
