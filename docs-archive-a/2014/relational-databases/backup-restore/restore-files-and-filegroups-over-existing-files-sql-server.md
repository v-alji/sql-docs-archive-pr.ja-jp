---
title: 既存のファイルにファイルとファイル グループを復元する (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring files [SQL Server], how-to topics
- restoring files [SQL Server], steps
- file restores [SQL Server], how-to topics
- filegroups [SQL Server], restoring
- restoring filegroups [SQL Server]
- overwriting filegroups
- overwriting files
ms.assetid: 517e07eb-9685-4b06-90af-b1cc496700b7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc72ae3ae2472fe579755fa624e9af6953c7aed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640086"
---
# <a name="restore-files-and-filegroups-over-existing-files-sql-server"></a><span data-ttu-id="f3e80-102">既存のファイルにファイルとファイル グループを復元する (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f3e80-102">Restore Files and Filegroups over Existing Files (SQL Server)</span></span>
  <span data-ttu-id="f3e80-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でファイルとファイル グループを既存のファイルに復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-103">This topic describes how to restore files and filegroups over existing files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f3e80-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f3e80-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f3e80-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f3e80-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f3e80-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f3e80-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f3e80-107">Security</span><span class="sxs-lookup"><span data-stu-id="f3e80-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f3e80-108">**ファイルとファイル グループを既存のファイルに復元する方法:**</span><span class="sxs-lookup"><span data-stu-id="f3e80-108">**To restore files and filegroups over existing files, using:**</span></span>  
  
     [<span data-ttu-id="f3e80-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f3e80-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f3e80-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f3e80-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f3e80-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="f3e80-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f3e80-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f3e80-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f3e80-113">復元するデータベースは、ファイルとファイル グループの復元作業を行うシステム管理者以外のユーザーによって使用されていない状態にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3e80-113">The system administrator who is restoring the files and filegroups must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="f3e80-114">RESTORE は、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="f3e80-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="f3e80-115">完全復旧モデルまたは一括ログ復旧モデルを使用する場合は、ファイルを復元する前に、ログの末尾と呼ばれるアクティブ トランザクション ログをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3e80-115">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="f3e80-116">詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3e80-116">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f3e80-117">暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。</span><span class="sxs-lookup"><span data-stu-id="f3e80-117">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="f3e80-118">証明書または非対称キーがないと、データベースは復元できません。</span><span class="sxs-lookup"><span data-stu-id="f3e80-118">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="f3e80-119">このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3e80-119">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="f3e80-120">詳細については、「 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f3e80-120">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f3e80-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f3e80-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f3e80-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="f3e80-122">Permissions</span></span>  
 <span data-ttu-id="f3e80-123">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3e80-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="f3e80-124">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="f3e80-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="f3e80-125">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="f3e80-126">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="f3e80-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f3e80-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f3e80-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-and-filegroups-over-existing-files"></a><span data-ttu-id="f3e80-128">ファイルとファイル グループを既存のファイルに復元するには</span><span class="sxs-lookup"><span data-stu-id="f3e80-128">To restore files and filegroups over existing files</span></span>  
  
1.  <span data-ttu-id="f3e80-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続して、そのインスタンスを展開します。次に、 **[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-129">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="f3e80-130">目的のデータベースを右クリックし、 **[タスク]** 、 **[復元]** の順にポイントし、 **[ファイルおよびファイル グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e80-130">Right-click the database that you want, point to **Tasks**, point to **Restore**, and then click **Files and Filegroups**.</span></span>  
  
3.  <span data-ttu-id="f3e80-131">**[全般]** ページの **[復元先データベース]** ボックスに、復元するデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-131">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="f3e80-132">新しいデータベースを入力するか、ドロップダウン リストから既存のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-132">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="f3e80-133">このリストには、システム データベース **master** および **tempdb**を除いた、サーバー上のすべてのデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-133">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
4.  <span data-ttu-id="f3e80-134">復元するバックアップ セットの復元元ファイルと場所を指定するには、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e80-134">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="f3e80-135">**[復元元データベース]**</span><span class="sxs-lookup"><span data-stu-id="f3e80-135">**From database**</span></span>  
  
         <span data-ttu-id="f3e80-136">ボックスにデータベース名を入力します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-136">Enter a database name in the list box.</span></span> <span data-ttu-id="f3e80-137">このリストには、 **msdb** バックアップ履歴に従ってバックアップされたデータベースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-137">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="f3e80-138">**[復元元デバイス]**</span><span class="sxs-lookup"><span data-stu-id="f3e80-138">**From device**</span></span>  
  
         <span data-ttu-id="f3e80-139">参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e80-139">Click the browse button.</span></span> <span data-ttu-id="f3e80-140">**[バックアップ デバイスの指定]** ダイアログ ボックスで、 **[バックアップ メディアの種類]** ボックスの一覧からいずれかのデバイスの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-140">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="f3e80-141">**[バックアップ メディア]** ボックスに 1 つまたは複数のデバイスを選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e80-141">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="f3e80-142">**[バックアップ メディア]** ボックスに目的のデバイスを追加したら、 **[OK]** をクリックして、 **[全般]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f3e80-142">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
5.  <span data-ttu-id="f3e80-143">**[復元するバックアップ セットの選択]** グリッドで、復元するバックアップを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-143">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="f3e80-144">このグリッドには、指定された場所に対して使用可能なバックアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-144">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="f3e80-145">既定では、復旧計画が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="f3e80-145">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="f3e80-146">推奨された復元計画を変更するには、グリッドの選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-146">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="f3e80-147">バックアップの選択を解除すると、それに依存するその他のバックアップも自動的に選択が解除されます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-147">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="f3e80-148">列見出し</span><span class="sxs-lookup"><span data-stu-id="f3e80-148">Column head</span></span>|<span data-ttu-id="f3e80-149">値</span><span class="sxs-lookup"><span data-stu-id="f3e80-149">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="f3e80-150">**復元**</span><span class="sxs-lookup"><span data-stu-id="f3e80-150">**Restore**</span></span>|<span data-ttu-id="f3e80-151">このチェック ボックスをオンにすると、バックアップ セットが復元されます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-151">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="f3e80-152">**名前**</span><span class="sxs-lookup"><span data-stu-id="f3e80-152">**Name**</span></span>|<span data-ttu-id="f3e80-153">バックアップ セットの名前です。</span><span class="sxs-lookup"><span data-stu-id="f3e80-153">The name of the backup set.</span></span>|  
    |<span data-ttu-id="f3e80-154">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="f3e80-154">**File Type**</span></span>|<span data-ttu-id="f3e80-155">バックアップのデータの種類を指定します。**データ**、**ログ**、または **Filestream データ**です。</span><span class="sxs-lookup"><span data-stu-id="f3e80-155">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="f3e80-156">テーブルに含まれるデータの種類は、 **データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f3e80-156">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="f3e80-157">トランザクション ログ データの種類は、 **ログ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f3e80-157">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="f3e80-158">ファイル システムに格納されたバイナリ ラージ オブジェクト (BLOB) データの種類は、 **FILESTREAM データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f3e80-158">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="f3e80-159">**Type**</span><span class="sxs-lookup"><span data-stu-id="f3e80-159">**Type**</span></span>|<span data-ttu-id="f3e80-160">実行するバックアップの種類: **[完全]** 、 **[差分]** 、 **[トランザクション ログ]** 。</span><span class="sxs-lookup"><span data-stu-id="f3e80-160">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="f3e80-161">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="f3e80-161">**Server**</span></span>|<span data-ttu-id="f3e80-162">バックアップ操作を実行するデータベース エンジン インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="f3e80-162">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="f3e80-163">**[ファイルの論理名]**</span><span class="sxs-lookup"><span data-stu-id="f3e80-163">**File Logical Name**</span></span>|<span data-ttu-id="f3e80-164">ファイルの論理名です。</span><span class="sxs-lookup"><span data-stu-id="f3e80-164">The logical name of the file.</span></span>|  
    |<span data-ttu-id="f3e80-165">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="f3e80-165">**Database**</span></span>|<span data-ttu-id="f3e80-166">バックアップ操作に呼び出されるデータベース名です。</span><span class="sxs-lookup"><span data-stu-id="f3e80-166">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="f3e80-167">**[開始日]**</span><span class="sxs-lookup"><span data-stu-id="f3e80-167">**Start Date**</span></span>|<span data-ttu-id="f3e80-168">バックアップ操作が開始した日時で、クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-168">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="f3e80-169">**完了日**</span><span class="sxs-lookup"><span data-stu-id="f3e80-169">**Finish Date**</span></span>|<span data-ttu-id="f3e80-170">バックアップ操作が完了したときの日付と時刻。クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-170">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="f3e80-171">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="f3e80-171">**Size**</span></span>|<span data-ttu-id="f3e80-172">バックアップ セットのサイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="f3e80-172">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="f3e80-173">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="f3e80-173">**User Name**</span></span>|<span data-ttu-id="f3e80-174">バックアップ操作を実行したユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="f3e80-174">The name of the user who performed the backup operation.</span></span>|  
  
6.  <span data-ttu-id="f3e80-175">**[ページの選択]** ペインの **[オプション]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e80-175">In the **Select a page** pane, click the **Options** page.</span></span>  
  
7.  <span data-ttu-id="f3e80-176">**[復元オプション]** パネルで、 **[既存のデータベースを上書きする (WITH REPLACE)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e80-176">In the **Restore options** panel, select **Overwrite the existing database (WITH REPLACE)**.</span></span> <span data-ttu-id="f3e80-177">同じ名前を持つ別のデータベースまたはファイルが既に存在している場合でも、復元操作は、既存のデータベースおよび関連ファイルを上書きします。</span><span class="sxs-lookup"><span data-stu-id="f3e80-177">The restore operation overwrites any existing databases and their related files, even if another database or file already exists with the same name.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f3e80-178">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f3e80-178">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-and-filegroups-over-existing-files"></a><span data-ttu-id="f3e80-179">ファイルとファイル グループを既存のファイルに復元するには</span><span class="sxs-lookup"><span data-stu-id="f3e80-179">To restore files and filegroups over existing files</span></span>  
  
1.  <span data-ttu-id="f3e80-180">RESTORE DATABASE ステートメントを実行して、ファイルとファイル グループのバックアップを復元します。そのとき、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-180">Execute the RESTORE DATABASE statement to restore the file and filegroup backup, specifying:</span></span>  
  
    -   <span data-ttu-id="f3e80-181">復元するデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="f3e80-181">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="f3e80-182">復元するデータベースの完全バックアップが格納されているバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="f3e80-182">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="f3e80-183">復元する各ファイルに対応する FILE 句。</span><span class="sxs-lookup"><span data-stu-id="f3e80-183">The FILE clause for each file to restore.</span></span>  
  
    -   <span data-ttu-id="f3e80-184">復元する各ファイル グループに対応する FILEGROUP 句。</span><span class="sxs-lookup"><span data-stu-id="f3e80-184">The FILEGROUP clause for each filegroup to restore.</span></span>  
  
    -   <span data-ttu-id="f3e80-185">REPLACE オプション。各ファイルを、同じ名前および同じ場所の既存のファイルに復元できるよう指定します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-185">The REPLACE option to specify that each file can be restored over existing files of the same name and location.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="f3e80-186">REPLACE オプションは慎重に使用してください。</span><span class="sxs-lookup"><span data-stu-id="f3e80-186">Use the REPLACE option cautiously.</span></span> <span data-ttu-id="f3e80-187">詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3e80-187">For more information, see .</span></span>  
  
    -   <span data-ttu-id="f3e80-188">NORECOVERY オプション。</span><span class="sxs-lookup"><span data-stu-id="f3e80-188">The NORECOVERY option.</span></span> <span data-ttu-id="f3e80-189">バックアップ作成後にファイルが変更されていない場合は、RECOVERY 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-189">If the files have not been modified after the backup was created, specify the RECOVERY clause.</span></span>  
  
2.  <span data-ttu-id="f3e80-190">ファイル バックアップの作成後にファイルが変更された場合は、RESTORE LOG ステートメントを実行して、トランザクション ログ バックアップを適用します。そのとき、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-190">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="f3e80-191">トランザクション ログが適用されるデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="f3e80-191">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="f3e80-192">復元するトランザクション ログのバックアップが格納されているバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="f3e80-192">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="f3e80-193">NORECOVERY 句。現在のトランザクション ログ バックアップを適用した後、別のバックアップがある場合に指定します。それ以外の場合は RECOVERY 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3e80-193">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="f3e80-194">トランザクション ログ バックアップを適用する場合、そのバックアップには、ファイルとファイル グループのバックアップが作成された時刻の情報が格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3e80-194">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f3e80-195">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f3e80-195">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f3e80-196">次の例では、 `MyNwind` データベースのファイルとファイル グループを復元し、同じ名前の既存のファイルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-196">The following example restores the files and filegroups for the `MyNwind` database, and replaces any existing files of the same name.</span></span> <span data-ttu-id="f3e80-197">データベースを現在の時刻に復元するために、2 つのトランザクション ログも適用されます。</span><span class="sxs-lookup"><span data-stu-id="f3e80-197">Two transaction logs will also be applied to restore the database to the current time.</span></span>  
  
```sql  
USE master;  
GO  
-- Restore the files and filesgroups for MyNwind.  
RESTORE DATABASE MyNwind  
   FILE = 'MyNwind_data_1',  
   FILEGROUP = 'new_customers',  
   FILE = 'MyNwind_data_2',  
   FILEGROUP = 'first_qtr_sales'  
   FROM MyNwind_1  
   WITH NORECOVERY,  
   REPLACE;  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3e80-198">参照</span><span class="sxs-lookup"><span data-stu-id="f3e80-198">See Also</span></span>  
 <span data-ttu-id="f3e80-199">[データベースバックアップを復元する &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="f3e80-199">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="f3e80-200">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f3e80-200">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="f3e80-201">[ファイルおよびファイル グループの復元 &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f3e80-201">[Restore Files and Filegroups &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="f3e80-202">バックアップと復元によるデータベースのコピー</span><span class="sxs-lookup"><span data-stu-id="f3e80-202">Copy Databases with Backup and Restore</span></span>](../databases/copy-databases-with-backup-and-restore.md)  
  
  
