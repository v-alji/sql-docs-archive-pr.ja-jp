---
title: トランザクション ログのバックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction log backups [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- backing up transaction logs [SQL Server], SQL Server Management Studio
ms.assetid: 3426b5eb-6327-4c7f-88aa-37030be69fbf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b57ca40b08718cda5095249991e0d424e6593a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640106"
---
# <a name="back-up-a-transaction-log-sql-server"></a><span data-ttu-id="3dac5-102">トランザクション ログのバックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3dac5-102">Back Up a Transaction Log (SQL Server)</span></span>
  <span data-ttu-id="3dac5-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、または PowerShell を使用して、トランザクション ログをバックアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-103">This topic describes how to back up a transaction log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
 <span data-ttu-id="3dac5-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="3dac5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3dac5-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3dac5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3dac5-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="3dac5-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3dac5-107">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="3dac5-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="3dac5-108">Security</span><span class="sxs-lookup"><span data-stu-id="3dac5-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3dac5-109">**トランザクション ログをバックアップする方法:**</span><span class="sxs-lookup"><span data-stu-id="3dac5-109">**To back up a transaction log, using:**</span></span>  
  
     [<span data-ttu-id="3dac5-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3dac5-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3dac5-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3dac5-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="3dac5-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3dac5-112">PowerShell</span></span>](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  <span data-ttu-id="3dac5-113">または、[メンテナンス プラン ウィザード](../maintenance-plans/use-the-maintenance-plan-wizard.md)を使用して、バックアップを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-113">Alternatively, you can use the[Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)to create backups.</span></span>  
  
-   [<span data-ttu-id="3dac5-114">関連タスク</span><span class="sxs-lookup"><span data-stu-id="3dac5-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3dac5-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="3dac5-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3dac5-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="3dac5-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3dac5-117">BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="3dac5-117">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="3dac5-118">推奨事項</span><span class="sxs-lookup"><span data-stu-id="3dac5-118">Recommendations</span></span>  
  
-   <span data-ttu-id="3dac5-119">データベースで完全復旧モデルまたは一括ログ復旧モデルのいずれかを使用している場合は、データを保護し、トランザクション ログがいっぱいになるのを防止するために、十分な頻度で定期的にトランザクション ログをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-119">If a database uses either the full or bulk-logged recovery model, you must back up the transaction log regularly enough to protect your data and to keep the transaction log from filling.</span></span> <span data-ttu-id="3dac5-120">これによってログが切り捨てられ、特定の時点へのデータベースの復元がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-120">This truncates the log and supports restoring the database to a specific point in time.</span></span>  
  
-   <span data-ttu-id="3dac5-121">既定では、バックアップ操作が成功するたびに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにエントリが 1 つ追加されます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-121">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="3dac5-122">ログを頻繁にバックアップすると、これらの成功メッセージがすぐに蓄積され、他のメッセージを探すのが困難になるほどエラー ログが大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-122">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="3dac5-123">そのような場合、これらのエントリに依存するスクリプトがなければ、トレース フラグ 3226 を使用することによってこれらのログ エントリを除外できます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-123">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="3dac5-124">詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dac5-124">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3dac5-125">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3dac5-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3dac5-126">Permissions</span><span class="sxs-lookup"><span data-stu-id="3dac5-126">Permissions</span></span>  
 <span data-ttu-id="3dac5-127">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="3dac5-127">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="3dac5-128">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-128">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3dac5-129">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3dac5-129">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="3dac5-130">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="3dac5-130">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="3dac5-131">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-131">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3dac5-132">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3dac5-132">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-a-transaction-log"></a><span data-ttu-id="3dac5-133">トランザクション ログをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="3dac5-133">To back up a transaction log</span></span>  
  
1.  <span data-ttu-id="3dac5-134">適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスへの接続後、オブジェクト エクスプローラーでサーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-134">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="3dac5-135">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-135">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="3dac5-136">データベースを右クリックして **[タスク]** をポイントし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-136">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="3dac5-137">**[データベースのバックアップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-137">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="3dac5-138">**[データベース]** ボックスに、適切なデータベース名が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-138">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="3dac5-139">必要に応じて、このボックスの一覧から別のデータベースを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-139">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="3dac5-140">復旧モデルが **[FULL]** または **[BULK_LOGGED]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-140">Verify that the recovery model is either **FULL** or **BULK_LOGGED**.</span></span>  
  
6.  <span data-ttu-id="3dac5-141">**[バックアップの種類]** ボックスの一覧で、 **[トランザクション ログ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-141">In the **Backup type** list box, select **Transaction Log**.</span></span>  
  
7.  <span data-ttu-id="3dac5-142">必要に応じて、 **[コピーのみのバックアップ]** を選択して、コピーのみのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-142">Optionally, you can select **Copy Only Backup** to create a copy-only backup.</span></span> <span data-ttu-id="3dac5-143">*コピーのみのバックアップ*は、従来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップのシーケンスから独立した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップです。</span><span class="sxs-lookup"><span data-stu-id="3dac5-143">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="3dac5-144">詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](copy-only-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dac5-144">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3dac5-145">**[差分]** オプションが選択されている場合、コピーのみのバックアップは作成できません。</span><span class="sxs-lookup"><span data-stu-id="3dac5-145">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
8.  <span data-ttu-id="3dac5-146">**[名前]** ボックスに表示された既定のバックアップ セット名をそのまま使用するか、または別のバックアップ セット名を入力します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-146">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="3dac5-147">必要に応じて、 **[説明]** ボックスに、バックアップ セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-147">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
10. <span data-ttu-id="3dac5-148">バックアップ セットの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-148">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="3dac5-149">バックアップ セットが指定の日数後に期限切れになるようにするには、 **[期間指定]** \(既定のオプション) をクリックし、セットを作成してからセットが期限切れになるまでの日数を入力します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-149">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="3dac5-150">0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-150">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="3dac5-151">既定値は、 **[サーバーのプロパティ]** ダイアログ ボックス ( **[データベースの設定]** ページ) の **[バックアップ メディアの既定の保有期間 (日)]** オプションで設定されています。</span><span class="sxs-lookup"><span data-stu-id="3dac5-151">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="3dac5-152">このダイアログ ボックスを開くには、オブジェクト エクスプローラーでサーバー名を右クリックし、[プロパティ] をクリックして、 **[データベースの設定]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-152">To access this dialog box, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="3dac5-153">バックアップ セットが特定の日付に期限切れになるようにするには、 **[日時指定]** をクリックし、セットの有効期限が切れる日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-153">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="3dac5-154">**[ディスク]** 、 **[URL]** 、または **[テープ]** をクリックして、バックアップ先を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-154">Choose the type of backup destination by clicking **Disk**, **URL** or **Tape**.</span></span> <span data-ttu-id="3dac5-155">1 つのメディア セットを含んでいる最大 64 個のディスク ドライブまたはテープ ドライブのパスを選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-155">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="3dac5-156">選択したパスは、 **[バックアップ先]** ボックスの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-156">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="3dac5-157">バックアップ先を削除するには、バックアップ先を選択して **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-157">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="3dac5-158">バックアップ先の内容を表示するには、バックアップ先を選択して **[内容]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-158">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="3dac5-159">詳細設定オプションを表示または選択するには、 **[ページの選択]** ペインの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-159">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="3dac5-160">次のいずれかをクリックして、 **[メディアに上書きします]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-160">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="3dac5-161">**[既存のメディア セットにバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="3dac5-161">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="3dac5-162">このオプションでは、 **[既存のバックアップ セットに追加する]** または **[既存のすべてのバックアップ セットを上書きする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-162">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="3dac5-163">詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dac5-163">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="3dac5-164">必要に応じて、 **[メディア セット名とバックアップ セットの有効期限を確認する]** チェック ボックスをオンにします。これにより、バックアップ操作で、メディア セットとバックアップ セットの有効期限が切れる日付と時刻の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-164">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="3dac5-165">必要に応じて、 **[メディア セット名]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-165">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="3dac5-166">名前を指定しなかった場合、空の名前でメディア セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-166">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="3dac5-167">メディア セット名を指定した場合は、メディア (テープまたはディスク) の実際の名前がここで入力した名前と一致しているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-167">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="3dac5-168">メディア名を指定せずに、このチェック ボックスをオンにしてこのメディアを確認するよう指定した場合は、実際のメディア名も空でないとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-168">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="3dac5-169">**[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]**</span><span class="sxs-lookup"><span data-stu-id="3dac5-169">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="3dac5-170">このオプションでは、 **[新しいメディア セット名]** ボックスに名前を入力し、必要に応じて **[新しいメディア セットの説明]** ボックスにメディア セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-170">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span> <span data-ttu-id="3dac5-171">詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dac5-171">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
14. <span data-ttu-id="3dac5-172">**[信頼性]** セクションで、必要に応じて次の項目をオンにします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-172">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="3dac5-173">**[完了時にバックアップを検証する]** 。</span><span class="sxs-lookup"><span data-stu-id="3dac5-173">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="3dac5-174">**[メディアに書き込む前にチェックサムを行う]** 、および、必要に応じて、 **[チェックサム エラーのまま続行する]** 。</span><span class="sxs-lookup"><span data-stu-id="3dac5-174">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="3dac5-175">チェックサムの詳細については、「[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dac5-175">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="3dac5-176">**[トランザクション ログ]** セクションで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-176">In the **Transaction log** section:</span></span>  
  
    -   <span data-ttu-id="3dac5-177">定期的なログ バックアップの場合は、既定の選択肢の **[アクティブでないエントリを削除してトランザクション ログを切り捨てる]** のままにします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-177">For routine log backups, keep the default selection, **Truncate the transaction log by removing inactive entries**.</span></span>  
  
    -   <span data-ttu-id="3dac5-178">ログ末尾 (アクティブなログ) をバックアップするには、 **[ログの末尾をバックアップし、データベースを復元中の状態にしておく]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-178">To back up the tail of the log (that is, the active log), check **Back up the tail of the log, and leave database in the restoring state**.</span></span>  
  
         <span data-ttu-id="3dac5-179">ログ末尾のバックアップは、作業内容が消失しないようにログの末尾をバックアップするために、エラー後に実行されます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-179">A tail-log backup is taken after a failure to back up the tail of the log in order to prevent work loss.</span></span> <span data-ttu-id="3dac5-180">アクティブなログのバックアップ (ログ末尾のバックアップ) は、エラーの後とデータベースの復元開始前の両方か、またはセカンダリ データベースへのフェールオーバー時に行われます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-180">Back up the active log (a tail-log backup) both after a failure, before beginning to restore the database, or when failing over to a secondary database.</span></span> <span data-ttu-id="3dac5-181">このオプションを選択すると、Transact-SQL の BACKUP LOG ステートメントで NORECOVERY オプションを指定した場合と同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-181">Selecting this option is equivalent to specifying the NORECOVERY option in the BACKUP LOG statement of Transact-SQL.</span></span> <span data-ttu-id="3dac5-182">ログ末尾のバックアップの詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](tail-log-backups-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3dac5-182">For more information about tail-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
16. <span data-ttu-id="3dac5-183">**[全般]** ページの **[バックアップ先]** セクションで、テープ ドライブにバックアップするように指定した場合は、 **[バックアップ後にテープをアンロードする]** チェック ボックスがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-183">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="3dac5-184">このオプションをオンにすると、 **[アンロードの前にテープを巻き戻す]** オプションがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-184">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
17. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="3dac5-185">以降では、 [バックアップの圧縮](backup-compression-sql-server.md)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3dac5-185">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="3dac5-186">既定では、バックアップが圧縮されるかどうかは、 **[バックアップ圧縮の既定]** サーバー構成オプションの値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="3dac5-186">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="3dac5-187">ただし、現在のサーバー レベルの既定の設定にかかわらず、 **[バックアップを圧縮する]** をオンにしてバックアップを圧縮することも、 **[バックアップを圧縮しない]** をオンにして圧縮しないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3dac5-187">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="3dac5-188">**現在の backup compression default 値を表示するには**</span><span class="sxs-lookup"><span data-stu-id="3dac5-188">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="3dac5-189">backup compression default サーバー構成オプションの表示または構成</span><span class="sxs-lookup"><span data-stu-id="3dac5-189">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
 <span data-ttu-id="3dac5-190">**暗号化**</span><span class="sxs-lookup"><span data-stu-id="3dac5-190">**Encryption**</span></span>  
  
 <span data-ttu-id="3dac5-191">バックアップ ファイルを暗号化するには、 **[バックアップ ファイルを暗号化する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3dac5-191">To encrypt the backup file check the **Encrypt backup** check box.</span></span> <span data-ttu-id="3dac5-192">バックアップ ファイルの暗号化に使用する暗号化アルゴリズムを選択し、証明書または非対称キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-192">Select an encryption algorithm to use for encrypting the backup file and provide a Certificate or Asymmetric key.</span></span> <span data-ttu-id="3dac5-193">暗号化に使用できるアルゴリズムは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3dac5-193">The available algorithms for encryption are:</span></span>  
  
-   <span data-ttu-id="3dac5-194">AES 128</span><span class="sxs-lookup"><span data-stu-id="3dac5-194">AES 128</span></span>  
  
-   <span data-ttu-id="3dac5-195">AES 192</span><span class="sxs-lookup"><span data-stu-id="3dac5-195">AES 192</span></span>  
  
-   <span data-ttu-id="3dac5-196">AES 256</span><span class="sxs-lookup"><span data-stu-id="3dac5-196">AES 256</span></span>  
  
-   <span data-ttu-id="3dac5-197">Triple DES</span><span class="sxs-lookup"><span data-stu-id="3dac5-197">Triple DES</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3dac5-198">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3dac5-198">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-a-transaction-log"></a><span data-ttu-id="3dac5-199">トランザクション ログをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="3dac5-199">To back up a transaction log</span></span>  
  
1.  <span data-ttu-id="3dac5-200">BACKUP LOG ステートメントを実行して、トランザクション ログをバックアップします。ここでは、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-200">Execute the BACKUP LOG statement to back up the transaction log, specifying the following:</span></span>  
  
    -   <span data-ttu-id="3dac5-201">バックアップするトランザクション ログが属しているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="3dac5-201">The name of the database to which the transaction log that you want to back up belongs.</span></span>  
  
    -   <span data-ttu-id="3dac5-202">トランザクション ログのバックアップが書き込まれるバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="3dac5-202">The backup device where the transaction log backup is written.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="3dac5-203">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3dac5-203">Example (Transact-SQL)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3dac5-204">この例では、単純復旧モデルを使用する [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] データベースを使用しています。</span><span class="sxs-lookup"><span data-stu-id="3dac5-204">This example uses the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database, which uses the simple recovery model.</span></span> <span data-ttu-id="3dac5-205">ただし、ログ バックアップを可能にするために、データベースの完全バックアップを行う前に、データベースが完全復旧モデルを使用するように設定されています。</span><span class="sxs-lookup"><span data-stu-id="3dac5-205">To permit log backups, before taking a full database backup, the database was set to use the full recovery model.</span></span> <span data-ttu-id="3dac5-206">詳細については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dac5-206">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="3dac5-207">この例では、 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] データベースのトランザクション ログ バックアップを、以前作成した名前付きバックアップ デバイスである `MyAdvWorks_FullRM_log1`に作成します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-207">This example creates a transaction log backup for the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to the previously created named backup device, `MyAdvWorks_FullRM_log1`.</span></span>  
  
```sql  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="3dac5-208">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="3dac5-208">Using PowerShell</span></span>  
  
<span data-ttu-id="3dac5-209">`Backup-SqlDatabase` コマンドレットを使用して、`Log` パラメーターの値に `-BackupAction` を指定します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-209">Use the `Backup-SqlDatabase` cmdlet and specify `Log` for the value of the `-BackupAction` parameter.</span></span>  
  
<span data-ttu-id="3dac5-210">次の例では、 `MyDB` データベースのログのバックアップを、サーバー インスタンス `Computer\Instance`の既定のバックアップ場所に作成します。</span><span class="sxs-lookup"><span data-stu-id="3dac5-210">The following example creates a log backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Log  
    ```  
  
<span data-ttu-id="3dac5-211">SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dac5-211">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).</span></span>
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3dac5-212">関連タスク</span><span class="sxs-lookup"><span data-stu-id="3dac5-212">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3dac5-213">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3dac5-213">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="3dac5-214">SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="3dac5-214">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="3dac5-215">満杯になったトランザクション ログのトラブルシューティング &#40;SQL Server エラー 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="3dac5-215">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a><span data-ttu-id="3dac5-216">参照</span><span class="sxs-lookup"><span data-stu-id="3dac5-216">See Also</span></span>  
 <span data-ttu-id="3dac5-217">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3dac5-217">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="3dac5-218">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3dac5-218">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="3dac5-219">[メンテナンス プラン](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="3dac5-219">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 [<span data-ttu-id="3dac5-220">ファイルの完全バックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3dac5-220">Full File Backups &#40;SQL Server&#41;</span></span>](full-file-backups-sql-server.md)  
