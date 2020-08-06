---
title: データベースの差分バックアップの作成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- database backups [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
- backups [SQL Server], creating
ms.assetid: 70f49794-b217-4519-9f2a-76ed61fa9f99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c3fb53d90ce633498bc518282d1ff03ce0b926e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645673"
---
# <a name="create-a-differential-database-backup-sql-server"></a><span data-ttu-id="edfc8-102">データベースの差分バックアップの作成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="edfc8-102">Create a Differential Database Backup (SQL Server)</span></span>
  <span data-ttu-id="edfc8-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースの差分バックアップを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-103">This topic describes how to create a differential database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="edfc8-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="edfc8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="edfc8-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="edfc8-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="edfc8-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="edfc8-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="edfc8-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="edfc8-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="edfc8-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="edfc8-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="edfc8-109">Security</span><span class="sxs-lookup"><span data-stu-id="edfc8-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="edfc8-110">**データベースの差分バックアップを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="edfc8-110">**To create a differential database backup, using:**</span></span>  
  
     [<span data-ttu-id="edfc8-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="edfc8-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="edfc8-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="edfc8-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="edfc8-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="edfc8-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="edfc8-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="edfc8-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="edfc8-115">BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="edfc8-115">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="edfc8-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="edfc8-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="edfc8-117">データベースの差分バックアップを作成するには、データベースの以前の完全バックアップが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-117">Creating a differential database backup requires that a previous full database backup exist.</span></span> <span data-ttu-id="edfc8-118">選択したデータベースをバックアップしたことがない場合は、差分バックアップを作成する前にデータベースの完全バックアップを実行してください。</span><span class="sxs-lookup"><span data-stu-id="edfc8-118">If the selected database has never been backed up, run a full database backup before creating any differential backups.</span></span> <span data-ttu-id="edfc8-119">詳細については、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edfc8-119">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="edfc8-120">推奨事項</span><span class="sxs-lookup"><span data-stu-id="edfc8-120">Recommendations</span></span>  
  
-   <span data-ttu-id="edfc8-121">差分バックアップのサイズが大きくなると、データベースを復元するときに、差分バックアップの復元に要する時間がかなり長くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-121">As the differential backups increase in size, restoring a differential backup can significantly increase the time that is required to restore a database.</span></span> <span data-ttu-id="edfc8-122">このため、定期的に新しい完全バックアップを実行することにより、データの新しい差分ベースを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="edfc8-122">Therefore, we recommend that you take a new full backup at set intervals to establish a new differential base for the data.</span></span> <span data-ttu-id="edfc8-123">たとえば、データベース全体のバックアップ (つまり、データベースの完全バックアップ) を週に 1 回実行し、次の週の完全バックアップまでの間、一連のデータベースの差分バックアップを定期的に実行します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-123">For example, you might take a weekly full backup of the whole database (that is, a full database backup) followed by a regular series of differential database backups during the week.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="edfc8-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="edfc8-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="edfc8-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="edfc8-125">Permissions</span></span>  
 <span data-ttu-id="edfc8-126">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="edfc8-126">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="edfc8-127">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-127">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="edfc8-128">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="edfc8-128">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="edfc8-129">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="edfc8-129">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="edfc8-130">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-130">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="edfc8-131">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="edfc8-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-differential-database-backup"></a><span data-ttu-id="edfc8-132">データベースの差分バックアップを作成するには</span><span class="sxs-lookup"><span data-stu-id="edfc8-132">To create a differential database backup</span></span>  
  
1.  <span data-ttu-id="edfc8-133">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]で適切な オブジェクト エクスプローラーのインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-133">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="edfc8-134">**[データベース]** を展開し、目的のデータベースに応じて、任意のユーザー データベースを選択するか、または **[システム データベース]** を展開して任意のシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-134">Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="edfc8-135">データベースを右クリックして **[タスク]** をポイントし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edfc8-135">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="edfc8-136">**[データベースのバックアップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-136">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="edfc8-137">**[データベース]** ボックスに、適切なデータベース名が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-137">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="edfc8-138">必要に応じて、このボックスの一覧から別のデータベースを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-138">You can optionally select a different database from the list.</span></span>  
  
     <span data-ttu-id="edfc8-139">差分バックアップは、すべての復旧モデル (完全復旧モデル、一括ログ復旧モデル、または単純復旧モデル) に対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-139">You can perform a differential backup for any recovery model (full, bulk-logged, or simple).</span></span>  
  
5.  <span data-ttu-id="edfc8-140">**[バックアップの種類]** ボックスの一覧の **[差分]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-140">In the **Backup type** list box, select **Differential**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="edfc8-141">**[差分]** を選択する場合は、 **[バックアップのみコピーする]** チェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-141">When **Differential** is selected, verify that the **Copy Only Backup** check box is cleared.</span></span>  
  
6.  <span data-ttu-id="edfc8-142">**[バックアップ コンポーネント]** で、 **[データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edfc8-142">For **Backup component**, click **Database**.</span></span>  
  
7.  <span data-ttu-id="edfc8-143">**[名前]** ボックスに表示された既定のバックアップ セット名をそのまま使用するか、または別のバックアップ セット名を入力します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-143">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
8.  <span data-ttu-id="edfc8-144">必要に応じて、 **[説明]** ボックスに、バックアップ セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-144">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
9. <span data-ttu-id="edfc8-145">バックアップ セットの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-145">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="edfc8-146">バックアップ セットが指定の日数後に期限切れになるようにするには、 **[期間指定]** \(既定のオプション) をクリックし、セットを作成してからセットが期限切れになるまでの日数を入力します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-146">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="edfc8-147">0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-147">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="edfc8-148">既定値は、 **[サーバーのプロパティ]** ダイアログ ボックス ( **[データベースの設定]** ページ) の **[バックアップ メディアの既定の保有期間 (日)]** オプションで設定されています。</span><span class="sxs-lookup"><span data-stu-id="edfc8-148">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="edfc8-149">このオプションを表示するには、オブジェクト エクスプローラーでサーバー名を右クリックし、プロパティを選択してから **[データベースの設定]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-149">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="edfc8-150">バックアップ セットが特定の日付に期限切れになるようにするには、 **[日時指定]** をクリックし、セットの有効期限が切れる日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-150">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
10. <span data-ttu-id="edfc8-151">**[ディスク]** または **[テープ]** をクリックして、バックアップ先を選択します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-151">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="edfc8-152">**[追加]** をクリックすると、1 つのメディア セットを含んでいる、最高で 64 個のディスク ドライブまたはテープ ドライブのパスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-152">To select the path of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="edfc8-153">選択したパスは、 **[バックアップ先]** ボックスの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-153">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="edfc8-154">バックアップ先を削除するには、バックアップ先を選択して **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edfc8-154">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="edfc8-155">バックアップ先の内容を表示するには、バックアップ先を選択して **[内容]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edfc8-155">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
11. <span data-ttu-id="edfc8-156">詳細設定オプションを表示または選択するには、 **[ページの選択]** ペインの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edfc8-156">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
12. <span data-ttu-id="edfc8-157">次のいずれかをクリックして、 **[メディアに上書きします]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-157">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="edfc8-158">**[既存のメディア セットにバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="edfc8-158">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="edfc8-159">このオプションでは、 **[既存のバックアップ セットに追加する]** または **[既存のすべてのバックアップ セットを上書きする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edfc8-159">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="edfc8-160">必要に応じて、 **[メディア セット名とバックアップ セットの有効期限を確認する]** チェック ボックスをオンにします。また、必要に応じて、 **[メディア セット名]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-160">Optionally, check the **Check media set name and backup set expiration** check box and, optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="edfc8-161">名前を指定しなかった場合、空の名前でメディア セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-161">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="edfc8-162">メディア セット名を指定した場合は、メディア (テープまたはディスク) を調べて、実際の名前とここで入力した名前が一致するかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-162">If you specify a media set name, the media (tape or disk) is checked to see if the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="edfc8-163">メディア名を指定せずに、このチェック ボックスをオンにしてこのメディアを確認するよう指定した場合は、実際のメディア名も空でないとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-163">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="edfc8-164">**[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]**</span><span class="sxs-lookup"><span data-stu-id="edfc8-164">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="edfc8-165">このオプションでは、 **[新しいメディア セット名]** ボックスに名前を入力し、必要に応じて **[新しいメディア セットの説明]** ボックスにメディア セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-165">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
13. <span data-ttu-id="edfc8-166">**[信頼性]** セクションで、必要に応じて次の項目をオンにします。</span><span class="sxs-lookup"><span data-stu-id="edfc8-166">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="edfc8-167">**[完了時にバックアップを検証する]** 。</span><span class="sxs-lookup"><span data-stu-id="edfc8-167">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="edfc8-168">**[メディアに書き込む前にチェックサムを行う]** 、および、必要に応じて、 **[チェックサム エラーのまま続行する]** 。</span><span class="sxs-lookup"><span data-stu-id="edfc8-168">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="edfc8-169">詳細については、「[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edfc8-169">For information about checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
14. <span data-ttu-id="edfc8-170">**[全般]** ページの **[バックアップ先]** セクションで、テープ ドライブにバックアップするように指定した場合は、 **[バックアップ後にテープをアンロードする]** チェック ボックスがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-170">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="edfc8-171">このオプションをオンにすると、 **[アンロードの前にテープを巻き戻す]** オプションがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-171">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="edfc8-172">**[全般]** ページの **[バックアップの種類]** で、トランザクション ログをバックアップするように指定しなかった場合、 **[トランザクション ログ]** セクションの各オプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="edfc8-172">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
15. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="edfc8-173">以降では、 [バックアップの圧縮](backup-compression-sql-server.md)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="edfc8-173">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="edfc8-174">既定では、バックアップが圧縮されるかどうかは、 **[バックアップ圧縮の既定]** サーバー構成オプションの値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="edfc8-174">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="edfc8-175">ただし、現在のサーバー レベルの既定の設定にかかわらず、 **[バックアップを圧縮する]** をオンにしてバックアップを圧縮することも、 **[バックアップを圧縮しない]** をオンにして圧縮しないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-175">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="edfc8-176">**現在の backup compression default 値を表示するには**</span><span class="sxs-lookup"><span data-stu-id="edfc8-176">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="edfc8-177">backup compression default サーバー構成オプションの表示または構成</span><span class="sxs-lookup"><span data-stu-id="edfc8-177">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
    > [!NOTE]  
    >  <span data-ttu-id="edfc8-178">メンテナンス プラン ウィザードを使用して、データベースの差分バックアップを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="edfc8-178">Alternatively, you can use the Maintenance Plan Wizard to create differential database backups.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="edfc8-179">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="edfc8-179">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-differential-database-backup"></a><span data-ttu-id="edfc8-180">データベースの差分バックアップを作成するには</span><span class="sxs-lookup"><span data-stu-id="edfc8-180">To create a differential database backup</span></span>  
  
1.  <span data-ttu-id="edfc8-181">次の項目を指定した BACKUP DATABASE ステートメントを実行し、データベースの差分バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-181">Execute the BACKUP DATABASE statement to create the differential database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="edfc8-182">バックアップするデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="edfc8-182">The name of the database to back up.</span></span>  
  
    -   <span data-ttu-id="edfc8-183">データベースの完全バックアップを書き込むバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="edfc8-183">The backup device where the full database backup is written.</span></span>  
  
    -   <span data-ttu-id="edfc8-184">DIFFERENTIAL 句。この句は、データベースの前回の完全バックアップの作成後に変更されたデータベースの部分だけをバックアップするときに指定します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-184">The DIFFERENTIAL clause, to specify that only the parts of the database that have changed after the last full database backup was created are backed up.</span></span>  
  
     <span data-ttu-id="edfc8-185">必須の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="edfc8-185">The required syntax is:</span></span>  
  
     <span data-ttu-id="edfc8-186">BACKUP DATABASE *database_name* TO <backup_device> WITH DIFFERENTIAL</span><span class="sxs-lookup"><span data-stu-id="edfc8-186">BACKUP DATABASE *database_name* TO <backup_device> WITH DIFFERENTIAL</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="edfc8-187">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="edfc8-187">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="edfc8-188">この例では、 `MyAdvWorks` データベースの完全バックアップおよび差分バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="edfc8-188">This example creates a full and a differential database backup for the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Create a full database backup first.  
BACKUP DATABASE MyAdvWorks   
   TO MyAdvWorks_1   
   WITH INIT;  
GO  
-- Time elapses.  
-- Create a differential database backup, appending the backup  
-- to the backup device containing the full database backup.  
BACKUP DATABASE MyAdvWorks  
   TO MyAdvWorks_1  
   WITH DIFFERENTIAL;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="edfc8-189">参照</span><span class="sxs-lookup"><span data-stu-id="edfc8-189">See Also</span></span>  
 <span data-ttu-id="edfc8-190">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="edfc8-190">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="edfc8-191">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="edfc8-191">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="edfc8-192">[ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="edfc8-192">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="edfc8-193">[データベースの差分バックアップの復元 &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="edfc8-193">[Restore a Differential Database Backup &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="edfc8-194">[トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="edfc8-194">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="edfc8-195">[メンテナンス プラン](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="edfc8-195">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 [<span data-ttu-id="edfc8-196">ファイルの完全バックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="edfc8-196">Full File Backups &#40;SQL Server&#41;</span></span>](full-file-backups-sql-server.md)  
  
  
