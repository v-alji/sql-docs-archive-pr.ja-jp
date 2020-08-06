---
title: データベースの完全バックアップの作成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f406464680a1669133dc87bdfb231c644d33fbdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741097"
---
# <a name="create-a-full-database-backup-sql-server"></a><span data-ttu-id="83850-102">データベースの完全バックアップの作成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="83850-102">Create a Full Database Backup (SQL Server)</span></span>
  <span data-ttu-id="83850-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、または PowerShell を使用して、データベースの完全バックアップを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="83850-103">This topic describes how to create a full database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83850-104">Azure Blob ストレージサービスへの SQL Server のバックアップの詳細については、「」 SQL Server、「 [Azure Blob Storage サービスを使用したバックアップと復元](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-104">For information on SQL Server backup to the Azure Blob storage service, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="83850-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="83850-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="83850-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="83850-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="83850-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="83850-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="83850-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="83850-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="83850-109">Security</span><span class="sxs-lookup"><span data-stu-id="83850-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="83850-110">**データベースの完全バックアップを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="83850-110">**To create a full database backup, using:**</span></span>  
  
     [<span data-ttu-id="83850-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="83850-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="83850-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="83850-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="83850-113">PowerShell</span><span class="sxs-lookup"><span data-stu-id="83850-113">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="83850-114">関連タスク</span><span class="sxs-lookup"><span data-stu-id="83850-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="83850-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="83850-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="83850-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="83850-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="83850-117">BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="83850-117">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="83850-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって作成されたバックアップは、それより前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では復元できません。</span><span class="sxs-lookup"><span data-stu-id="83850-118">Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="83850-119">詳細については、「 [バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-119">For more information, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="83850-120">推奨事項</span><span class="sxs-lookup"><span data-stu-id="83850-120">Recommendations</span></span>  
  
-   <span data-ttu-id="83850-121">データベース サイズが大きくなると、データベースの完全バックアップにかかる時間は長くなり、必要な記憶領域も増加します。</span><span class="sxs-lookup"><span data-stu-id="83850-121">As a database increases in size full database backups take more time to finish and require more storage space.</span></span> <span data-ttu-id="83850-122">このため、大きなデータベースの場合は、データベースの完全バックアップを一連の *差分データベース バックアップ*で補完することができます。</span><span class="sxs-lookup"><span data-stu-id="83850-122">Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*.</span></span> <span data-ttu-id="83850-123">詳細については、「 [差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-123">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="83850-124">データベースの完全バックアップのサイズは、 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) システム ストアド プロシージャを使用して推計することができます。</span><span class="sxs-lookup"><span data-stu-id="83850-124">You can estimate the size of a full database backup by using the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) system stored procedure.</span></span>  
  
-   <span data-ttu-id="83850-125">既定では、バックアップ操作が成功するたびに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにエントリが 1 つ追加されます。</span><span class="sxs-lookup"><span data-stu-id="83850-125">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="83850-126">ログを頻繁にバックアップすると、これらの成功メッセージがすぐに蓄積され、他のメッセージを探すのが困難になるほどエラー ログが大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="83850-126">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="83850-127">そのような場合、これらのエントリに依存するスクリプトがなければ、トレース フラグ 3226 を使用することによってこれらのログ エントリを除外できます。</span><span class="sxs-lookup"><span data-stu-id="83850-127">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="83850-128">詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-128">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="83850-129">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="83850-129">Security</span></span>  
 <span data-ttu-id="83850-130">データベースをバックアップすると、TRUSTWORTHY は OFF に設定されます。</span><span class="sxs-lookup"><span data-stu-id="83850-130">TRUSTWORTHY is set to OFF on a database backup.</span></span> <span data-ttu-id="83850-131">TRUSTWORTHY を ON に設定する方法については「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-131">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="83850-132">以降では [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、 `PASSWORD` バックアップを `MEDIAPASSWORD` 作成するためのオプションとオプションが廃止されました。</span><span class="sxs-lookup"><span data-stu-id="83850-132">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] the `PASSWORD` and `MEDIAPASSWORD` options are discontinued for creating backups.</span></span> <span data-ttu-id="83850-133">パスワード付きで作成されたバックアップを復元することは、引き続き可能です。</span><span class="sxs-lookup"><span data-stu-id="83850-133">You can still restore backups created with passwords.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="83850-134">Permissions</span><span class="sxs-lookup"><span data-stu-id="83850-134">Permissions</span></span>  
 <span data-ttu-id="83850-135">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="83850-135">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="83850-136">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="83850-136">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="83850-137">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="83850-137">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="83850-138">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="83850-138">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="83850-139">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="83850-139">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="83850-140">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="83850-140">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83850-141">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してバックアップ タスクを指定する場合、**[スクリプト]** ボタンをクリックしてスクリプトの保存先を選択することにより、対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) スクリプトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="83850-141">When you specify a back up task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and selecting a script destination.</span></span>  
  
#### <a name="to-back-up-a-database"></a><span data-ttu-id="83850-142">データベースをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="83850-142">To back up a database</span></span>  
  
1.  <span data-ttu-id="83850-143">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]で適切な オブジェクト エクスプローラーのインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="83850-143">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="83850-144">**[データベース]** を展開し、目的のデータベースに応じて、任意のユーザー データベースを選択するか、または **[システム データベース]** を展開して任意のシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="83850-144">Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="83850-145">データベースを右クリックして **[タスク]** をポイントし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83850-145">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="83850-146">**[データベースのバックアップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83850-146">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="83850-147">`Database`リストボックスで、データベース名を確認します。</span><span class="sxs-lookup"><span data-stu-id="83850-147">In the `Database` list box, verify the database name.</span></span> <span data-ttu-id="83850-148">必要に応じて、このボックスの一覧から別のデータベースを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="83850-148">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="83850-149">どの復旧モデル (**[FULL]**、 **[BULK_LOGGED]**、 **[SIMPLE]**) でも、データベースのバックアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="83850-149">You can perform a database backup for any recovery model (**FULL**, **BULK_LOGGED**, or **SIMPLE**).</span></span>  
  
6.  <span data-ttu-id="83850-150">**[バックアップの種類]** ボックスの一覧の **[完全]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83850-150">In the **Backup type** list box, select **Full**.</span></span>  
  
     <span data-ttu-id="83850-151">データベースの完全バックアップを作成すると、データベースの差分バックアップを作成できるようになります。詳細については、「 [データベースの差分バックアップの作成 &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-151">Note that after creating a full database backup, you can create a differential database backup; for more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).</span></span>  
  
7.  <span data-ttu-id="83850-152">必要に応じて、 **[コピーのみのバックアップ]** を選択して、コピーのみのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="83850-152">Optionally, you can select **Copy Only Backup** to create a copy-only backup.</span></span> <span data-ttu-id="83850-153">*コピーのみのバックアップ*は、従来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップのシーケンスから独立した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップです。</span><span class="sxs-lookup"><span data-stu-id="83850-153">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="83850-154">詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](copy-only-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-154">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="83850-155">**[差分]** オプションが選択されている場合、コピーのみのバックアップは作成できません。</span><span class="sxs-lookup"><span data-stu-id="83850-155">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
8.  <span data-ttu-id="83850-156">[**バックアップコンポーネント**] で、[] をクリックし `Database` ます。</span><span class="sxs-lookup"><span data-stu-id="83850-156">For **Backup component**, click `Database`.</span></span>  
  
9. <span data-ttu-id="83850-157">**[名前]** ボックスに表示された既定のバックアップ セット名をそのまま使用するか、または別のバックアップ セット名を入力します。</span><span class="sxs-lookup"><span data-stu-id="83850-157">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
10. <span data-ttu-id="83850-158">必要に応じて、 **[説明]** ボックスに、バックアップ セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="83850-158">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
11. <span data-ttu-id="83850-159">**[ディスク]**、 **[テープ]** 、または **[URL]** をクリックして、バックアップ先を選択します。</span><span class="sxs-lookup"><span data-stu-id="83850-159">Choose the type of backup destination by clicking **Disk**, **Tape** or **URL**.</span></span> <span data-ttu-id="83850-160">1 つのメディア セットを含んでいる最大 64 個のディスク ドライブまたはテープ ドライブのパスを選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83850-160">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="83850-161">選択したパスは、 **[バックアップ先]** ボックスの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="83850-161">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="83850-162">バックアップ先を削除するには、バックアップ先を選択して **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83850-162">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="83850-163">バックアップ先の内容を表示するには、バックアップ先を選択して **[内容]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83850-163">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="83850-164">メディア オプションを表示または選択するには、 **[ページの選択]** ペインの **[メディア オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83850-164">To view or select the media options, click **Media Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="83850-165">次のいずれかをクリックして、 **[メディアに上書きします]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="83850-165">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="83850-166">**[既存のメディア セットにバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="83850-166">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="83850-167">このオプションでは、 **[既存のバックアップ セットに追加する]** または **[既存のすべてのバックアップ セットを上書きする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83850-167">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="83850-168">詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-168">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="83850-169">必要に応じて、 **[メディア セット名とバックアップ セットの有効期限を確認する]** チェック ボックスをオンにします。これにより、バックアップ操作で、メディア セットとバックアップ セットの有効期限が切れる日付と時刻の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="83850-169">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="83850-170">必要に応じて、 **[メディア セット名]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="83850-170">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="83850-171">名前を指定しなかった場合、空の名前でメディア セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="83850-171">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="83850-172">メディア セット名を指定した場合は、メディア (テープまたはディスク) の実際の名前がここで入力した名前と一致しているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="83850-172">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="83850-173">**[全般]** ページでバックアップ先として **[URL]** を選択した場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="83850-173">This option is disabled if you selected **URL** as the backup destination in the **General** page.</span></span> <span data-ttu-id="83850-174">詳細については、「[[データベースのバックアップ] &#40;[メディア オプション] ページ&#41;](back-up-database-media-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-174">For more information, see [Back Up Database &#40;Media Options Page&#41;](back-up-database-media-options-page.md)</span></span>  
        >   
        >  <span data-ttu-id="83850-175">暗号化を使用する場合は、このオプションを選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="83850-175">If you plan to use encryption, do not select this option.</span></span> <span data-ttu-id="83850-176">このオプションを選択すると、 **[バックアップ オプション]** ページの暗号化オプションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="83850-176">If you select this option, the encryption options in the **Backup Options** page will be disabled.</span></span> <span data-ttu-id="83850-177">既存のバックアップ セットに追加するときには、暗号化はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="83850-177">Encryption is not supported when appending to the existing backup set.</span></span>  
  
    -   <span data-ttu-id="83850-178">**[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]**</span><span class="sxs-lookup"><span data-stu-id="83850-178">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="83850-179">このオプションでは、 **[新しいメディア セット名]** ボックスに名前を入力し、必要に応じて **[新しいメディア セットの説明]** ボックスにメディア セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="83850-179">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="83850-180">**[全般]** ページで **[URL]** を選択した場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="83850-180">This option is disabled if you selected **URL** in the **General** page.</span></span> <span data-ttu-id="83850-181">これらのアクションは、Azure storage へのバックアップ時にはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="83850-181">These actions are not supported when backing up to Azure storage.</span></span>  
  
14. <span data-ttu-id="83850-182">[**信頼性**] セクションで、必要に応じて次のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="83850-182">In the **Reliability** section, optionally check:</span></span>  
  
    -   <span data-ttu-id="83850-183">**[完了時にバックアップを検証する]** 。</span><span class="sxs-lookup"><span data-stu-id="83850-183">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="83850-184">**[メディアに書き込む前にチェックサムを行う]** 、および、必要に応じて、 **[チェックサム エラーのまま続行する]** 。</span><span class="sxs-lookup"><span data-stu-id="83850-184">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="83850-185">チェックサムの詳細については、「[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-185">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="83850-186">**[全般]** ページの **[バックアップ先]** セクションで、テープ ドライブにバックアップするように指定した場合は、 **[バックアップ後にテープをアンロードする]** チェック ボックスがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="83850-186">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="83850-187">このオプションをオンにすると、 **[アンロードの前にテープを巻き戻す]** オプションがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="83850-187">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="83850-188">**[全般]** ページの **[バックアップの種類]** で、トランザクション ログをバックアップするように指定しなかった場合、 **[トランザクション ログ]** セクションの各オプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="83850-188">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
16. <span data-ttu-id="83850-189">バックアップ オプションを表示または選択するには、 **[ページの選択]** ペインの **[バックアップ オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83850-189">To view or select the backup options, click **Backup Options** in the **Select a page** pane.</span></span>  
  
17. <span data-ttu-id="83850-190">バックアップ セットの有効期限と、有効期限が過ぎたデータを明示的に確認せずに上書きできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-190">Specify when the backup set will expire and can be overwritten without explicitly skipping verification of the expiration data:</span></span>  
  
    -   <span data-ttu-id="83850-191">バックアップ セットが指定の日数後に期限切れになるようにするには、 **[期間指定]** \(既定のオプション) をクリックし、セットを作成してからセットが期限切れになるまでの日数を入力します。</span><span class="sxs-lookup"><span data-stu-id="83850-191">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="83850-192">0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。</span><span class="sxs-lookup"><span data-stu-id="83850-192">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="83850-193">既定値は、**[サーバーのプロパティ]** ダイアログ ボックス ([データベースの設定] ページ) の **[バックアップ メディアの既定の保有期間 (日)]** オプションで設定します。</span><span class="sxs-lookup"><span data-stu-id="83850-193">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (Database Settings Page).</span></span> <span data-ttu-id="83850-194">このオプションを表示するには、オブジェクト エクスプローラーでサーバー名を右クリックし、プロパティを選択してから **[データベースの設定]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="83850-194">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="83850-195">バックアップ セットが特定の日付に期限切れになるようにするには、 **[日時指定]** をクリックし、セットの有効期限が切れる日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="83850-195">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
         <span data-ttu-id="83850-196">バックアップの有効期限の詳細については、「 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-196">For more information about backup expiration dates, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
18. [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="83850-197">以降では、 [バックアップの圧縮](backup-compression-sql-server.md)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="83850-197">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="83850-198">既定では、バックアップが圧縮されるかどうかは、 **[バックアップ圧縮の既定]** サーバー構成オプションの値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="83850-198">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="83850-199">ただし、現在のサーバー レベルの既定の設定にかかわらず、 **[バックアップを圧縮する]** をオンにしてバックアップを圧縮することも、 **[バックアップを圧縮しない]** をオンにして圧縮しないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="83850-199">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="83850-200">**現在の backup compression default 値を表示または変更するには**</span><span class="sxs-lookup"><span data-stu-id="83850-200">**To view or change the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="83850-201">backup compression default サーバー構成オプションの表示または構成</span><span class="sxs-lookup"><span data-stu-id="83850-201">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
19. <span data-ttu-id="83850-202">バックアップに暗号化を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-202">Specify whether to use encryption for the backup.</span></span> <span data-ttu-id="83850-203">暗号化手順に使用する暗号化アルゴリズムを選択し、既存の証明書または非対称キーの一覧から証明書または非対称キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-203">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="83850-204">暗号化は SQL Server 2014 以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="83850-204">Encryption is supported in SQL Server 2014 or later.</span></span> <span data-ttu-id="83850-205">暗号化オプションの詳細については、「 [データベースのバックアップ &#40;バックアップ オプション ページ&#41;](back-up-database-backup-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-205">For more details on the Encryption options, see [Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83850-206">メンテナンス プラン ウィザードを使用して、データベースのバックアップを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="83850-206">Alternatively, you can use the Maintenance Plan Wizard to create database backups.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="83850-207">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="83850-207">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-full-database-backup"></a><span data-ttu-id="83850-208">データベースの完全バックアップを作成するには</span><span class="sxs-lookup"><span data-stu-id="83850-208">To create a full database backup</span></span>  
  
1.  <span data-ttu-id="83850-209">次の項目を指定した BACKUP DATABASE ステートメントを実行し、データベースの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="83850-209">Execute the BACKUP DATABASE statement to create the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="83850-210">バックアップするデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="83850-210">The name of the database to back up.</span></span>  
  
    -   <span data-ttu-id="83850-211">データベースの完全バックアップを書き込むバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="83850-211">The backup device where the full database backup is written.</span></span>  
  
     <span data-ttu-id="83850-212">データベースの完全バックアップのための [!INCLUDE[tsql](../../includes/tsql-md.md)] の基本構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="83850-212">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for a full database backup is:</span></span>  
  
     <span data-ttu-id="83850-213">BACKUP DATABASE *database*</span><span class="sxs-lookup"><span data-stu-id="83850-213">BACKUP DATABASE *database*</span></span>  
  
     <span data-ttu-id="83850-214">TO *backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="83850-214">TO *backup_device* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="83850-215">[ WITH *with_options* [ **,** ...*o* ] ] ;</span><span class="sxs-lookup"><span data-stu-id="83850-215">[ WITH *with_options* [ **,**...*o* ] ] ;</span></span>  
  
    |<span data-ttu-id="83850-216">オプション</span><span class="sxs-lookup"><span data-stu-id="83850-216">Option</span></span>|<span data-ttu-id="83850-217">説明</span><span class="sxs-lookup"><span data-stu-id="83850-217">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="83850-218">*database*</span><span class="sxs-lookup"><span data-stu-id="83850-218">*database*</span></span>|<span data-ttu-id="83850-219">バックアップするデータベースです。</span><span class="sxs-lookup"><span data-stu-id="83850-219">Is the database that is to be backed up.</span></span>|  
    |<span data-ttu-id="83850-220">*backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="83850-220">*backup_device* [ **,**...*n* ]</span></span>|<span data-ttu-id="83850-221">バックアップ操作に使用する 1 ～ 64 個のバックアップ デバイスの一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-221">Specifies a list of from 1 to 64 backup devices to use for the backup operation.</span></span> <span data-ttu-id="83850-222">物理バックアップ デバイスを指定したり、対応する論理バックアップ デバイス (既に定義されている場合) を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="83850-222">You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined.</span></span> <span data-ttu-id="83850-223">物理バックアップ デバイスを指定するには、DISK オプションまたは TAPE オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="83850-223">To specify a physical backup device, use the DISK or TAPE option:</span></span><br /><br /> <span data-ttu-id="83850-224">{ DISK &#124; TAPE } **=** _physical_backup_device_name_</span><span class="sxs-lookup"><span data-stu-id="83850-224">{ DISK &#124; TAPE } **=**_physical_backup_device_name_</span></span><br /><br /> <span data-ttu-id="83850-225">詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-225">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>|  
    |<span data-ttu-id="83850-226">WITH *with_options* [ **,** ...*o* ]</span><span class="sxs-lookup"><span data-stu-id="83850-226">WITH *with_options* [ **,**...*o* ]</span></span>|<span data-ttu-id="83850-227">必要に応じて、1 つ以上の追加オプション ( *o*) を指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-227">Optionally, specifies one or more additional options, *o*.</span></span> <span data-ttu-id="83850-228">基本的な with オプションについては、手順 2. を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-228">For information about some of the basic with options, see step 2.</span></span>|  
  
2.  <span data-ttu-id="83850-229">必要に応じて、1 つ以上の WITH オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-229">Optionally, specify one or more WITH options.</span></span> <span data-ttu-id="83850-230">ここでは、一部の基本的な WITH オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="83850-230">A few basic WITH options are described here.</span></span> <span data-ttu-id="83850-231">すべての WITH オプションについては、「[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-231">For information about all the WITH options, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
    -   <span data-ttu-id="83850-232">基本的なバックアップ セット WITH オプション</span><span class="sxs-lookup"><span data-stu-id="83850-232">Basic backup set WITH options:</span></span>  
  
         <span data-ttu-id="83850-233">{ COMPRESSION | NO_COMPRESSION }</span><span class="sxs-lookup"><span data-stu-id="83850-233">{ COMPRESSION | NO_COMPRESSION }</span></span>  
         <span data-ttu-id="83850-234">[!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] 以降でのみ、このバックアップで [バックアップの圧縮](backup-compression-sql-server.md) を実行するかどうかを指定し、サーバー レベルの既定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="83850-234">In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] and later only, specifies whether [backup compression](backup-compression-sql-server.md) is performed on this backup, overriding the server-level default.</span></span>  
  
         <span data-ttu-id="83850-235">ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)</span><span class="sxs-lookup"><span data-stu-id="83850-235">ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)</span></span>  
         <span data-ttu-id="83850-236">SQL Server 2014 以降でのみ、使用する暗号化アルゴリズムと暗号化の保護に使用する証明書または非対称キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-236">In SQL Server 2014 or later only, specify the encryption algorithm to use, and the Certificate or Asymmetric key to use to secure the encryption.</span></span>  
  
         <span data-ttu-id="83850-237">説明 **=** { **' *`text`* '**  |  **@** _text_variable_ }</span><span class="sxs-lookup"><span data-stu-id="83850-237">DESCRIPTION **=** { **'*`text`*'** | **@**_text_variable_ }</span></span>  
         <span data-ttu-id="83850-238">バックアップ セットを記述したテキストを自由な形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-238">Specifies the free-form text that describes the backup set.</span></span> <span data-ttu-id="83850-239">文字列の長さは最大 255 文字です。</span><span class="sxs-lookup"><span data-stu-id="83850-239">The string can have a maximum of 255 characters.</span></span>  
  
         <span data-ttu-id="83850-240">名前 **=** { *backup_set_name*  |  **@** _backup_set_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="83850-240">NAME **=** { *backup_set_name* | **@**_backup_set_name_var_ }</span></span>  
         <span data-ttu-id="83850-241">バックアップ セットの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-241">Specifies the name of the backup set.</span></span> <span data-ttu-id="83850-242">名前の長さは最大 128 文字です。</span><span class="sxs-lookup"><span data-stu-id="83850-242">Names can have a maximum of 128 characters.</span></span> <span data-ttu-id="83850-243">NAME を指定しないと、名前は空白になります。</span><span class="sxs-lookup"><span data-stu-id="83850-243">If NAME is not specified, it is blank.</span></span>  
  
    -   <span data-ttu-id="83850-244">基本的なバックアップ セット WITH オプション</span><span class="sxs-lookup"><span data-stu-id="83850-244">Basic backup set WITH options:</span></span>  
  
         <span data-ttu-id="83850-245">既定では、BACKUP はバックアップを既存のメディア セットに追加し、既存のバックアップ セットを保持します。</span><span class="sxs-lookup"><span data-stu-id="83850-245">By default, BACKUP appends the backup to an existing media set, preserving existing backup sets.</span></span> <span data-ttu-id="83850-246">これを明示的に指定するには、NOINIT オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="83850-246">To explicitly specify this, use the NOINIT option.</span></span> <span data-ttu-id="83850-247">既存のバックアップ セットへの追加については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83850-247">For information about appending to existing backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="83850-248">また、FORMAT オプションを使用して、バックアップ メディアをフォーマットすることもできます。</span><span class="sxs-lookup"><span data-stu-id="83850-248">Alternatively, to format the backup media, use the FORMAT option:</span></span>  
  
         <span data-ttu-id="83850-249">FORMAT [ **,** MEDIANAME **=** { *media_name*  |  **@** _media_name_variable_ }] [ **,** MEDIADESCRIPTION **=** { *text*  |  **@** _text_variable_ }]</span><span class="sxs-lookup"><span data-stu-id="83850-249">FORMAT [ **,** MEDIANAME**=** { *media_name* | **@**_media_name_variable_ } ] [ **,** MEDIADESCRIPTION **=** { *text* | **@**_text_variable_ } ]</span></span>  
         <span data-ttu-id="83850-250">FORMAT 句は、バックアップ メディアを初めて使用する場合や既存のデータをすべて上書きする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="83850-250">Use the FORMAT clause when you are using media for the first time or you want to overwrite all existing data.</span></span> <span data-ttu-id="83850-251">必要に応じて、新しいメディアにメディア名と説明を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="83850-251">Optionally, assign the new media a media name and description.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="83850-252">BACKUP ステートメントで FORMAT 句を使用すると、バックアップ メディアに格納されているバックアップが破棄されるので、十分注意して使用してください。</span><span class="sxs-lookup"><span data-stu-id="83850-252">Use extreme caution when you are using the FORMAT clause of the BACKUP statement because this destroys any backups that were previously stored on the backup media.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="83850-253">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="83850-253">Examples (Transact-SQL)</span></span>  
  
#### <a name="a-backing-up-to-a-disk-device"></a><span data-ttu-id="83850-254">A.</span><span class="sxs-lookup"><span data-stu-id="83850-254">A.</span></span> <span data-ttu-id="83850-255">ディスク デバイスへのバックアップ</span><span class="sxs-lookup"><span data-stu-id="83850-255">Backing up to a disk device</span></span>  
 <span data-ttu-id="83850-256">次の例では、新しいメディア セットを作成する [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] を使用して、 `FORMAT` データベース全体をディスクにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="83850-256">The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to disk, by using `FORMAT` to create a new media set.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="b-backing-up-to-a-tape-device"></a><span data-ttu-id="83850-257">B.</span><span class="sxs-lookup"><span data-stu-id="83850-257">B.</span></span> <span data-ttu-id="83850-258">テープ デバイスへのバックアップ</span><span class="sxs-lookup"><span data-stu-id="83850-258">Backing up to a tape device</span></span>  
 <span data-ttu-id="83850-259">次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース全体をテープにバックアップし、以前のバックアップに追加します。</span><span class="sxs-lookup"><span data-stu-id="83850-259">The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]database to tape, appending the backup to the previous backups.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="c-backing-up-to-a-logical-tape-device"></a><span data-ttu-id="83850-260">C.</span><span class="sxs-lookup"><span data-stu-id="83850-260">C.</span></span> <span data-ttu-id="83850-261">論理テープ デバイスへのバックアップ</span><span class="sxs-lookup"><span data-stu-id="83850-261">Backing up to a logical tape device</span></span>  
 <span data-ttu-id="83850-262">次の例では、テープ ドライブ用の論理バックアップ デバイスを作成した後、</span><span class="sxs-lookup"><span data-stu-id="83850-262">The following example creates a logical backup device for a tape drive.</span></span> <span data-ttu-id="83850-263">作成したデバイスに [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース全体をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="83850-263">The example then backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to that device.</span></span>  
  
```sql  
-- Create a logical backup device,   
-- AdventureWorks2012_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'AdventureWorks2012_Bak_Tape', '\\.\tape0'; USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO AdventureWorks2012_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'AdventureWorks2012_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="83850-264">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="83850-264">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="83850-265">`Backup-SqlDatabase` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="83850-265">Use the `Backup-SqlDatabase` cmdlet.</span></span> <span data-ttu-id="83850-266">データベースの完全バックアップであることを明示するには、 **-backupaction**パラメーターに既定値を指定し `Database` ます。</span><span class="sxs-lookup"><span data-stu-id="83850-266">To explicitly indicate that this is a full database backup, specify the **-BackupAction**  parameter with its default value, `Database`.</span></span> <span data-ttu-id="83850-267">このパラメーターは、データベースの完全バックアップでは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="83850-267">This parameter is optional for full database backups.</span></span>  
  
     <span data-ttu-id="83850-268">次の例では、 `MyDB` データベースの完全なバックアップを、サーバー インスタンス `Computer\Instance`の既定のバックアップ場所に作成します。</span><span class="sxs-lookup"><span data-stu-id="83850-268">The following example creates a full database backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`.</span></span> <span data-ttu-id="83850-269">オプションで、`-BackupAction Database` を指定します。</span><span class="sxs-lookup"><span data-stu-id="83850-269">Optionally, this example specifies `-BackupAction Database`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
    ```  
  
 <span data-ttu-id="83850-270">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="83850-270">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="83850-271">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="83850-271">SQL Server PowerShell Provider</span></span>](../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="83850-272">関連タスク</span><span class="sxs-lookup"><span data-stu-id="83850-272">Related Tasks</span></span>  
  
-   [<span data-ttu-id="83850-273">データベースのバックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="83850-273">Back Up a Database (SQL Server)</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="83850-274">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83850-274">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="83850-275">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="83850-275">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="83850-276">単純復旧モデルでのデータベース バックアップの復元 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83850-276">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="83850-277">完全復旧モデルで障害発生時点までデータベースを復元する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83850-277">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="83850-278">データベースを新しい場所に復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83850-278">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="83850-279">メンテナンス プラン ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="83850-279">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="83850-280">参照</span><span class="sxs-lookup"><span data-stu-id="83850-280">See Also</span></span>  
 <span data-ttu-id="83850-281">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="83850-281">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="83850-282">[トランザクション ログのバックアップ &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="83850-282">[Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="83850-283">[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="83850-283">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="83850-284">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="83850-284">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="83850-285">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="83850-285">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="83850-286">[データベースのバックアップ &#40;全般ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="83850-286">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="83850-287">[[データベースのバックアップ] &#40;[バックアップ オプション] ページ&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="83850-287">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="83850-288">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="83850-288">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="83850-289">データベースの完全バックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83850-289">Full Database Backups &#40;SQL Server&#41;</span></span>](full-database-backups-sql-server.md)  
