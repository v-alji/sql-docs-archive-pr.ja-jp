---
title: ファイルおよびファイル グループのバックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up filegroups [SQL Server]
- file backups [SQL Server], how-to topics
- backing up files [SQL Server]
- backups [SQL Server], creating
- filegroups [SQL Server], backing up
ms.assetid: a0d3a567-7d8b-4cfe-a505-d197b9a51f70
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7affc90b064febaa70e0a67108074f412b4bbf00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632007"
---
# <a name="back-up-files-and-filegroups-sql-server"></a><span data-ttu-id="432f1-102">ファイルおよびファイル グループのバックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="432f1-102">Back Up Files and Filegroups (SQL Server)</span></span>
  <span data-ttu-id="432f1-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または PowerShell を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でファイルとファイル グループをバックアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="432f1-103">This topic describes how to back up files and filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="432f1-104">データベースのサイズやパフォーマンスの要件によりデータベースの完全バックアップが不可能な場合は、代わりに、ファイル バックアップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="432f1-104">When the database size and performance requirements make a full database backup impractical, you can create a file backup instead.</span></span> <span data-ttu-id="432f1-105">*ファイル バックアップ* には、1 つ以上のファイル (またはファイル グループ) 内のすべてのデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="432f1-105">A *file backup* contains all the data in one or more files (or filegroups).</span></span> <span data-ttu-id="432f1-106">ファイルのバックアップの詳細については、「 [ファイルの完全バックアップ &#40;SQL Server&#41;](full-file-backups-sql-server.md) 」および「 [差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-106">For more information about file backups, see [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) and [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="432f1-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="432f1-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="432f1-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="432f1-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="432f1-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="432f1-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="432f1-110">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="432f1-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="432f1-111">Security</span><span class="sxs-lookup"><span data-stu-id="432f1-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="432f1-112">**ファイルおよびファイル グループをバックアップする方法:**</span><span class="sxs-lookup"><span data-stu-id="432f1-112">**To back up files and filegroups, using:**</span></span>  
  
     [<span data-ttu-id="432f1-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="432f1-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="432f1-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="432f1-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="432f1-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="432f1-115">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="432f1-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="432f1-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="432f1-117">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="432f1-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="432f1-118">BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="432f1-118">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="432f1-119">単純復旧モデルでは、読み取りと書き込みが可能なファイルはすべてまとめてバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="432f1-119">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="432f1-120">これにより、データベースを一貫性のある時点に復元できます。</span><span class="sxs-lookup"><span data-stu-id="432f1-120">This helps make sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="432f1-121">読み取りと書き込みが可能なファイルまたはファイル グループを個別に指定するのではなく、READ_WRITE_FILEGROUPS オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="432f1-121">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="432f1-122">このオプションにより、読み取りと書き込みが可能なすべてのファイル グループがデータベースにバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="432f1-122">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="432f1-123">READ_WRITE_FILEGROUPS を指定して作成されたバックアップは、*部分バックアップ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="432f1-123">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a *partial backup*.</span></span> <span data-ttu-id="432f1-124">詳細については、「[部分バックアップ &#40;SQL Server&#41;](partial-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-124">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="432f1-125">この機能の制限および制約の詳細については、「 [バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-125">For more information about limitations and restrictions, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="432f1-126">推奨事項</span><span class="sxs-lookup"><span data-stu-id="432f1-126">Recommendations</span></span>  
  
-   <span data-ttu-id="432f1-127">既定では、バックアップ操作が成功するたびに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにエントリが 1 つ追加されます。</span><span class="sxs-lookup"><span data-stu-id="432f1-127">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="432f1-128">ログを頻繁にバックアップすると、これらの成功メッセージがすぐに蓄積され、他のメッセージを探すのが困難になるほどエラー ログが大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="432f1-128">If you back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="432f1-129">そのような場合、これらのエントリに依存するスクリプトがなければ、トレース フラグ 3226 を使用することによってこれらのログ エントリを除外できます。</span><span class="sxs-lookup"><span data-stu-id="432f1-129">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="432f1-130">詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-130">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="432f1-131">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="432f1-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="432f1-132">Permissions</span><span class="sxs-lookup"><span data-stu-id="432f1-132">Permissions</span></span>  
 <span data-ttu-id="432f1-133">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="432f1-133">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="432f1-134">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="432f1-134">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="432f1-135">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="432f1-135">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="432f1-136">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="432f1-136">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="432f1-137">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="432f1-137">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="432f1-138">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="432f1-138">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-database-files-and-filegroups"></a><span data-ttu-id="432f1-139">データベース ファイルおよびファイル グループをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="432f1-139">To back up database files and filegroups</span></span>  
  
1.  <span data-ttu-id="432f1-140">適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスへの接続後、オブジェクト エクスプローラーでサーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="432f1-140">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="432f1-141">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="432f1-141">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="432f1-142">データベースを右クリックして **[タスク]** をポイントし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-142">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="432f1-143">**[データベースのバックアップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="432f1-143">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="432f1-144">**[データベース]** ボックスの一覧で、適切なデータベース名が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="432f1-144">In the **Database** list, verify the database name.</span></span> <span data-ttu-id="432f1-145">必要に応じて、このボックスの一覧から別のデータベースを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="432f1-145">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="432f1-146">**[バックアップの種類]** ボックスの一覧の **[完全]** または **[差分]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-146">In the **Backup type** list, select **Full** or **Differential**.</span></span>  
  
6.  <span data-ttu-id="432f1-147">**[バックアップ コンポーネント]** の **[ファイルとファイル グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-147">For the **Backup component** option, click **File and Filegroups**.</span></span>  
  
7.  <span data-ttu-id="432f1-148">**[ファイルおよびファイル グループの選択]** ダイアログ ボックスで、バックアップするファイルおよびファイル グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="432f1-148">In the **Select Files and Filegroups** dialog box, select the files and filegroups you want to back up.</span></span> <span data-ttu-id="432f1-149">個別のファイルを 1 つ以上選択できるほか、ファイル グループのチェック ボックスをオンにすると自動的にファイル グループ内のすべてのファイルが選択されます。</span><span class="sxs-lookup"><span data-stu-id="432f1-149">You can select one or more individual files or check the box for a filegroup to automatically select all the files in that filegroup.</span></span>  
  
8.  <span data-ttu-id="432f1-150">**[名前]** ボックスに表示された既定のバックアップ セット名をそのまま使用するか、または別のバックアップ セット名を入力します。</span><span class="sxs-lookup"><span data-stu-id="432f1-150">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="432f1-151">必要に応じて、 **[説明]** ボックスに、バックアップ セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="432f1-151">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
10. <span data-ttu-id="432f1-152">バックアップ セットの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="432f1-152">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="432f1-153">バックアップ セットが指定の日数後に期限切れになるようにするには、 **[期間指定]** (既定のオプション) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-153">To have the backup set expire after a specific number of days, click **After** (the default option).</span></span> <span data-ttu-id="432f1-154">次に、セットを作成してから期限切れになるまでの日数を入力します。</span><span class="sxs-lookup"><span data-stu-id="432f1-154">Then, enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="432f1-155">0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。</span><span class="sxs-lookup"><span data-stu-id="432f1-155">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="432f1-156">既定値は、 **[サーバーのプロパティ]** ダイアログ ボックス ( **[データベースの設定]** ページ) の **[バックアップ メディアの既定の保有期間 (日)]** オプションで設定されています。</span><span class="sxs-lookup"><span data-stu-id="432f1-156">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="432f1-157">このオプションを表示するには、オブジェクト エクスプローラーでサーバー名を右クリックし、[プロパティ] をクリックします。次に、 **[データベースの設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-157">To access this option, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="432f1-158">バックアップ セットが特定の日付に期限切れになるようにするには、 **[日時指定]** をクリックし、セットの有効期限が切れる日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="432f1-158">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="432f1-159">**[ディスク]** または **[テープ]** をクリックして、バックアップ先を選択します。</span><span class="sxs-lookup"><span data-stu-id="432f1-159">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="432f1-160">1 つのメディア セットを含んでいる最大 64 個のディスク ドライブまたはテープ ドライブのパスを選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-160">To select the paths of up to 64 disk or tape drives that contain a single media set, click **Add**.</span></span> <span data-ttu-id="432f1-161">選択したパスは、 **[バックアップ先]** ボックスの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="432f1-161">The selected paths are displayed in the **Backup to** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="432f1-162">バックアップ先を削除するには、バックアップ先を選択して **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-162">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="432f1-163">バックアップ先の内容を表示するには、バックアップ先を選択して **[内容]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-163">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="432f1-164">詳細設定オプションを表示または選択するには、 **[ページの選択]** ペインの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-164">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="432f1-165">次のいずれかをクリックして、 **[メディアに上書きします]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="432f1-165">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="432f1-166">**[既存のメディア セットにバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="432f1-166">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="432f1-167">このオプションでは、 **[既存のバックアップ セットに追加する]** または **[既存のすべてのバックアップ セットを上書きする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="432f1-167">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="432f1-168">既存のメディア セットへのバックアップの詳細については、「[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-168">For information about backing up to an existing media set, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="432f1-169">必要に応じて、 **[メディア セット名とバックアップ セットの有効期限を確認する]** チェック ボックスをオンにします。これにより、バックアップ操作で、メディア セットとバックアップ セットの有効期限が切れる日付と時刻の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="432f1-169">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="432f1-170">必要に応じて、 **[メディア セット名]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="432f1-170">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="432f1-171">名前を指定しなかった場合、空の名前でメディア セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="432f1-171">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="432f1-172">メディア セット名を指定した場合は、メディア (テープまたはディスク) の実際の名前がここで入力した名前と一致しているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="432f1-172">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name that you enter here.</span></span>  
  
         <span data-ttu-id="432f1-173">メディア名を指定せずに、このチェック ボックスをオンにしてこのメディアを確認するよう指定した場合は、実際のメディア名も空でないとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="432f1-173">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="432f1-174">**[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]**</span><span class="sxs-lookup"><span data-stu-id="432f1-174">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="432f1-175">このオプションでは、 **[新しいメディア セット名]** ボックスに名前を入力し、必要に応じて **[新しいメディア セットの説明]** ボックスにメディア セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="432f1-175">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span> <span data-ttu-id="432f1-176">新しいメディア セットを詳細する方法の詳細については、「[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-176">For more information about creating a new media set, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
14. <span data-ttu-id="432f1-177">[**信頼性**] セクションで、必要に応じて次のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="432f1-177">In the **Reliability** section, optionally check:</span></span>  
  
    -   <span data-ttu-id="432f1-178">**[完了時にバックアップを検証する]** 。</span><span class="sxs-lookup"><span data-stu-id="432f1-178">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="432f1-179">**[メディアに書き込む前にチェックサムを行う]** 、および、必要に応じて、 **[チェックサム エラーのまま続行する]** 。</span><span class="sxs-lookup"><span data-stu-id="432f1-179">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="432f1-180">チェックサムの詳細については、「[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-180">For more information about checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="432f1-181">**[全般]** ページの **[バックアップ先]** セクションで、テープ ドライブにバックアップするように指定した場合は、 **[バックアップ後にテープをアンロードする]** チェック ボックスがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="432f1-181">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="432f1-182">このオプションをオンにすると、 **[アンロードの前にテープを巻き戻す]** オプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="432f1-182">Clicking this option enables the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="432f1-183">**[全般]** ページの **[バックアップの種類]** で、トランザクション ログをバックアップするように指定しなかった場合、 **[トランザクション ログ]** セクションの各オプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="432f1-183">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="432f1-184">以降のバージョンでは、 [バックアップの圧縮](backup-compression-sql-server.md)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="432f1-184">and later versions support [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="432f1-185">既定では、バックアップが圧縮されるかどうかは、 **[バックアップ圧縮の既定]** サーバー構成オプションの値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="432f1-185">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="432f1-186">ただし、現在のサーバー レベルの既定の設定にかかわらず、 **[バックアップを圧縮する]** をオンにしてバックアップを圧縮することも、 **[バックアップを圧縮しない]** をオンにして圧縮しないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="432f1-186">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="432f1-187">**現在の backup compression default 値を表示するには**</span><span class="sxs-lookup"><span data-stu-id="432f1-187">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="432f1-188">backup compression default サーバー構成オプションの表示または構成</span><span class="sxs-lookup"><span data-stu-id="432f1-188">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="432f1-189">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="432f1-189">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-files-and-filegroups"></a><span data-ttu-id="432f1-190">ファイルおよびファイル グループをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="432f1-190">To back up files and filegroups</span></span>  
  
1.  <span data-ttu-id="432f1-191">ファイルまたはファイル グループのバックアップを作成するには、[BACKUP DATABASE <file_or_filegroup>](/sql/t-sql/statements/backup-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="432f1-191">To create a file or filegroup backup, use a [BACKUP DATABASE <file_or_filegroup>](/sql/t-sql/statements/backup-transact-sql) statement.</span></span> <span data-ttu-id="432f1-192">このステートメントでは、少なくとも次の項目を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="432f1-192">Minimally, this statement must specify the following:</span></span>  
  
    -   <span data-ttu-id="432f1-193">データベース名です。</span><span class="sxs-lookup"><span data-stu-id="432f1-193">The database name.</span></span>  
  
    -   <span data-ttu-id="432f1-194">ファイルまたはファイル グループごとに FILE 句または FILEGROUP 句。</span><span class="sxs-lookup"><span data-stu-id="432f1-194">A FILE or FILEGROUP clause for each file or filegroup, respectively.</span></span>  
  
    -   <span data-ttu-id="432f1-195">完全バックアップが書き込まれるバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="432f1-195">The backup device on which the full backup will be written.</span></span>  
  
     <span data-ttu-id="432f1-196">ファイル バックアップの基本的な [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="432f1-196">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for a file backup is:</span></span>  
  
     <span data-ttu-id="432f1-197">BACKUP DATABASE *database*</span><span class="sxs-lookup"><span data-stu-id="432f1-197">BACKUP DATABASE *database*</span></span>  
  
     <span data-ttu-id="432f1-198">{ FILE **=** _logical_file_name_ | FILEGROUP **=** _logical_filegroup_name_ } [ **,** ...*f* ]</span><span class="sxs-lookup"><span data-stu-id="432f1-198">{ FILE **=**_logical_file_name_ | FILEGROUP **=**_logical_filegroup_name_ } [ **,**...*f* ]</span></span>  
  
     <span data-ttu-id="432f1-199">TO *backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="432f1-199">TO *backup_device* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="432f1-200">[ WITH *with_options* [ **,** ...*o* ] ] ;</span><span class="sxs-lookup"><span data-stu-id="432f1-200">[ WITH *with_options* [ **,**...*o* ] ] ;</span></span>  
  
    |<span data-ttu-id="432f1-201">オプション</span><span class="sxs-lookup"><span data-stu-id="432f1-201">Option</span></span>|<span data-ttu-id="432f1-202">説明</span><span class="sxs-lookup"><span data-stu-id="432f1-202">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="432f1-203">*database*</span><span class="sxs-lookup"><span data-stu-id="432f1-203">*database*</span></span>|<span data-ttu-id="432f1-204">トランザクション ログ、データベースの一部、またはデータベース全体をバックアップする場合の、バックアップ元となるデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="432f1-204">Is the database from which the transaction log, partial database, or complete database is backed up.</span></span>|  
    |<span data-ttu-id="432f1-205">FILE **=** _logical_file_name_</span><span class="sxs-lookup"><span data-stu-id="432f1-205">FILE **=**_logical_file_name_</span></span>|<span data-ttu-id="432f1-206">ファイル バックアップに含めるファイルの論理名を指定します。</span><span class="sxs-lookup"><span data-stu-id="432f1-206">Specifies the logical name of a file to include in the file backup.</span></span>|  
    |<span data-ttu-id="432f1-207">FILEGROUP **=** _logical_filegroup_name_</span><span class="sxs-lookup"><span data-stu-id="432f1-207">FILEGROUP **=**_logical_filegroup_name_</span></span>|<span data-ttu-id="432f1-208">ファイル バックアップに含めるファイル グループの論理名を指定します。</span><span class="sxs-lookup"><span data-stu-id="432f1-208">Specifies the logical name of a filegroup to include in the file backup.</span></span> <span data-ttu-id="432f1-209">単純復旧モデルでは、ファイル グループのバックアップは、読み取り専用のファイル グループに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="432f1-209">Under the simple recovery model, a filegroup backup is allowed only for a read-only filegroup.</span></span>|  
    |<span data-ttu-id="432f1-210">[ **,** ...*f* ]</span><span class="sxs-lookup"><span data-stu-id="432f1-210">[ **,**...*f* ]</span></span>|<span data-ttu-id="432f1-211">複数のファイルおよびファイル グループを指定できることを示すプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="432f1-211">Is a placeholder that indicates that multiple files and filegroups may be specified.</span></span> <span data-ttu-id="432f1-212">ファイルまたはファイル グループの数は無制限です。</span><span class="sxs-lookup"><span data-stu-id="432f1-212">The number of files or filegroups is unlimited.</span></span>|  
    |<span data-ttu-id="432f1-213">*backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="432f1-213">*backup_device* [ **,**...*n* ]</span></span>|<span data-ttu-id="432f1-214">バックアップ操作に使用する 1 ～ 64 個のバックアップ デバイスの一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="432f1-214">Specifies a list of from 1 to 64 backup devices to use for the backup operation.</span></span> <span data-ttu-id="432f1-215">物理バックアップ デバイスを指定したり、対応する論理バックアップ デバイス (既に定義されている場合) を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="432f1-215">You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined.</span></span> <span data-ttu-id="432f1-216">物理バックアップ デバイスを指定するには、DISK オプションまたは TAPE オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="432f1-216">To specify a physical backup device, use the DISK or TAPE option:</span></span><br /><br /> <span data-ttu-id="432f1-217">{ DISK &#124; TAPE } **=** _physical_backup_device_name_</span><span class="sxs-lookup"><span data-stu-id="432f1-217">{ DISK &#124; TAPE } **=**_physical_backup_device_name_</span></span><br /><br /> <span data-ttu-id="432f1-218">詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-218">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>|  
    |<span data-ttu-id="432f1-219">WITH *with_options* [ **,** ...*o* ]</span><span class="sxs-lookup"><span data-stu-id="432f1-219">WITH *with_options* [ **,**...*o* ]</span></span>|<span data-ttu-id="432f1-220">必要に応じて、1 つ以上の追加オプション (DIFFERENTIAL など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="432f1-220">Optionally, specifies one or more additional options, such as DIFFERENTIAL.</span></span><br /><br /> <span data-ttu-id="432f1-221">注: ファイルの差分バックアップを行うには、差分のベースとなる完全ファイル バックアップが必要です。</span><span class="sxs-lookup"><span data-stu-id="432f1-221">Note: A differential file backup requires a full file backup as a base.</span></span> <span data-ttu-id="432f1-222">詳細については、「[データベースの差分バックアップの作成 &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-222">For more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).</span></span>|  
  
2.  <span data-ttu-id="432f1-223">完全復旧モデルでは、トランザクション ログもバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="432f1-223">Under the full recovery model, you must also back up the transaction log.</span></span> <span data-ttu-id="432f1-224">ファイルの完全バックアップの完全なセットを使用してデータベースを復元するには、最初のファイル バックアップの先頭から、すべてのファイル バックアップにわたって十分なログ バックアップが必要です。</span><span class="sxs-lookup"><span data-stu-id="432f1-224">To use a complete set of full file backups to restore a database, you must also have enough log backups to span all the file backups, from the start of the first file backup.</span></span> <span data-ttu-id="432f1-225">詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-225">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="432f1-226">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="432f1-226">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="432f1-227">次の例では、 `Sales` データベースのセカンダリ ファイル グループの 1 つ以上のファイルをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="432f1-227">The following examples back up one or more files of the secondary filegroups of the `Sales` database.</span></span> <span data-ttu-id="432f1-228">このデータベースでは、完全復旧モデルを使用し、次のセカンダリ ファイル グループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="432f1-228">This database uses the full recovery model and contains the following secondary filegroups:</span></span>  
  
-   <span data-ttu-id="432f1-229">`SalesGroup1` ファイルと `SGrp1Fi1` ファイルを含む、 `SGrp1Fi2`という名前のファイル グループ。</span><span class="sxs-lookup"><span data-stu-id="432f1-229">A filegroup named `SalesGroup1` that has the files `SGrp1Fi1` and `SGrp1Fi2`.</span></span>  
  
-   <span data-ttu-id="432f1-230">`SalesGroup2` ファイルと `SGrp2Fi1` ファイルを含む、 `SGrp2Fi2`という名前のファイル グループ。</span><span class="sxs-lookup"><span data-stu-id="432f1-230">A filegroup named `SalesGroup2` that has the files `SGrp2Fi1` and `SGrp2Fi2`.</span></span>  
  
#### <a name="a-creating-a-file-backup-of-two-files"></a><span data-ttu-id="432f1-231">A.</span><span class="sxs-lookup"><span data-stu-id="432f1-231">A.</span></span> <span data-ttu-id="432f1-232">2 つのファイルのファイル バックアップの作成</span><span class="sxs-lookup"><span data-stu-id="432f1-232">Creating a file backup of two files</span></span>  
 <span data-ttu-id="432f1-233">次の例では、 `SGrp1Fi2` ファイル グループの `SalesGroup1` ファイルと `SGrp2Fi2` ファイル グループの `SalesGroup2` ファイルのみのファイルの差分バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="432f1-233">The following example creates a differential file backup of only the `SGrp1Fi2` file of the `SalesGroup1` and the `SGrp2Fi2` file of the `SalesGroup2` filegroup.</span></span>  
  
```sql  
--Backup the files in the SalesGroup1 secondary filegroup.  
BACKUP DATABASE Sales  
   FILE = 'SGrp1Fi2',   
   FILE = 'SGrp2Fi2'   
   TO DISK = 'G:\SQL Server Backups\Sales\SalesGroup1.bck';  
GO  
```  
  
#### <a name="b-creating-a-full-file-backup-of-the-secondary-filegroups"></a><span data-ttu-id="432f1-234">B.</span><span class="sxs-lookup"><span data-stu-id="432f1-234">B.</span></span> <span data-ttu-id="432f1-235">セカンダリ ファイル グループの完全ファイル バックアップを作成する</span><span class="sxs-lookup"><span data-stu-id="432f1-235">Creating a full file backup of the secondary filegroups</span></span>  
 <span data-ttu-id="432f1-236">次の例では、両方のセカンダリ ファイル グループ内のすべてのファイルについて、完全ファイル バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="432f1-236">The following example creates a full file backup of every file in both of the secondary filegroups.</span></span>  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck';  
GO  
```  
  
#### <a name="c-creating-a-differential-file-backup-of-the-secondary-filegroups"></a><span data-ttu-id="432f1-237">C.</span><span class="sxs-lookup"><span data-stu-id="432f1-237">C.</span></span> <span data-ttu-id="432f1-238">セカンダリ ファイル グループの差分ファイル バックアップを作成する</span><span class="sxs-lookup"><span data-stu-id="432f1-238">Creating a differential file backup of the secondary filegroups</span></span>  
 <span data-ttu-id="432f1-239">次の例では、両方のセカンダリ ファイル グループ内のすべてのファイルについて、差分ファイル バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="432f1-239">The following example creates a differential file backup of every file in both of the secondary filegroups.</span></span>  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck'  
   WITH   
      DIFFERENTIAL;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="432f1-240">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="432f1-240">Using PowerShell</span></span>  
  
<span data-ttu-id="432f1-241">`Backup-SqlDatabase` コマンドレットを使用して、`Files` パラメーターの値に `-BackupAction` を指定します。</span><span class="sxs-lookup"><span data-stu-id="432f1-241">Use the `Backup-SqlDatabase` cmdlet and specify `Files` for the value of the `-BackupAction` parameter.</span></span> <span data-ttu-id="432f1-242">また、次のいずれかのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="432f1-242">Also, specify one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="432f1-243">特定のファイルをバックアップするには、 `-DatabaseFile` *文字列*パラメーターを指定します。ここで、 *string*はバックアップする1つ以上のデータベースファイルです。</span><span class="sxs-lookup"><span data-stu-id="432f1-243">To back up a specific file, specify the `-DatabaseFile`*String* parameter, where *String* is one or more database files to be backed up.</span></span>  
  
    -   <span data-ttu-id="432f1-244">特定のファイルグループ内のすべてのファイルをバックアップするには、 `-DatabaseFileGroup` *文字列*パラメーターを指定します。 *string*は、バックアップする1つ以上のデータベースファイルグループです。</span><span class="sxs-lookup"><span data-stu-id="432f1-244">To back up all the files in a given filegroup, specify the `-DatabaseFileGroup`*String* parameter, where *String* is one or more database filegroups to be backed up.</span></span>  
  
     <span data-ttu-id="432f1-245">次の例では、 `MyDB` データベースのセカンダリ ファイル グループである FileGroup1 および FileGroup2 のすべてのファイルの完全ファイル バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="432f1-245">The following example creates a full file backup of every file in the secondary filegroups 'FileGroup1' and 'FileGroup2' in the `MyDB` database.</span></span> <span data-ttu-id="432f1-246">バックアップは、サーバー インスタンス `Computer\Instance`の既定のバックアップ先に作成されます。</span><span class="sxs-lookup"><span data-stu-id="432f1-246">The backups are created on the default backup location of the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Files -DatabaseFileGroup "FileGroup1","FileGroup2"  
    ```  
  
<span data-ttu-id="432f1-247">SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432f1-247">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="432f1-248">参照</span><span class="sxs-lookup"><span data-stu-id="432f1-248">See Also</span></span>  
 <span data-ttu-id="432f1-249">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="432f1-249">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="432f1-250">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="432f1-250">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="432f1-251">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="432f1-251">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="432f1-252">[バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="432f1-252">[Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span></span>  
 <span data-ttu-id="432f1-253">[データベースのバックアップ &#40;全般ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="432f1-253">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="432f1-254">[[データベースのバックアップ] &#40;[バックアップ オプション] ページ&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="432f1-254">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="432f1-255">[ファイルの完全バックアップ &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="432f1-255">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="432f1-256">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="432f1-256">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="432f1-257">[ファイルの復元 &#40;完全復旧モデル&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="432f1-257">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="432f1-258">ファイル復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="432f1-258">File Restores &#40;Simple Recovery Model&#41;</span></span>](file-restores-simple-recovery-model.md)  
  
  
