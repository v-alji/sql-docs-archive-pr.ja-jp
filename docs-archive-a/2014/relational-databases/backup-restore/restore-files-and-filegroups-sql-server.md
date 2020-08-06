---
title: ファイルとファイル グループの復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restorefilesandfilegrps.general.f1
- sql12.swb.restorefilesandfilegrps.options.f1
- sql12.swb.bselectfilegrpsfiles.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], restoring files and filegroups
- restoring [SQL Server], files
ms.assetid: 72603b21-3065-4b56-8b01-11b707911b05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2576f1326cb50fa197b1623aaa1326d70137823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715422"
---
# <a name="restore-files-and-filegroups-sql-server"></a><span data-ttu-id="56777-102">ファイルとファイル グループの復元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="56777-102">Restore Files and Filegroups (SQL Server)</span></span>
  <span data-ttu-id="56777-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でファイルとファイル グループを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="56777-103">This topic describes how to restore files and filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="56777-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="56777-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="56777-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="56777-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="56777-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="56777-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="56777-107">Security</span><span class="sxs-lookup"><span data-stu-id="56777-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="56777-108">**ファイルおよびファイル グループを復元する方法:**</span><span class="sxs-lookup"><span data-stu-id="56777-108">**To restore files and filegroups, using:**</span></span>  
  
     [<span data-ttu-id="56777-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="56777-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="56777-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="56777-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="56777-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="56777-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="56777-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="56777-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="56777-113">ファイルとファイル グループの復元中は、復元作業を実行するシステム管理者以外は、復元されるデータベースを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="56777-113">The system administrator restoring the files and filegroups must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="56777-114">RESTORE は、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="56777-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="56777-115">単純復旧モデルでは、ファイルは読み取り専用のファイル グループに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="56777-115">Under the simple recovery model, the file must belong to a read-only filegroup.</span></span>  
  
-   <span data-ttu-id="56777-116">完全復旧モデルまたは一括ログ復旧モデルを使用する場合は、ファイルを復元する前に、ログの末尾と呼ばれるアクティブ トランザクション ログをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56777-116">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="56777-117">詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56777-117">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="56777-118">暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。</span><span class="sxs-lookup"><span data-stu-id="56777-118">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="56777-119">証明書または非対称キーがないと、データベースは復元できません。</span><span class="sxs-lookup"><span data-stu-id="56777-119">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="56777-120">このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="56777-120">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="56777-121">詳細については、「 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56777-121">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="56777-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="56777-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="56777-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="56777-123">Permissions</span></span>  
 <span data-ttu-id="56777-124">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56777-124">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="56777-125">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="56777-125">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="56777-126">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="56777-126">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="56777-127">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="56777-127">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="56777-128">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="56777-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-and-filegroups"></a><span data-ttu-id="56777-129">ファイルおよびファイル グループを復元するには</span><span class="sxs-lookup"><span data-stu-id="56777-129">To restore files and filegroups</span></span>  
  
1.  <span data-ttu-id="56777-130">オブジェクト エクスプローラーで適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="56777-130">After you connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="56777-131">**[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="56777-131">Expand **Databases**.</span></span> <span data-ttu-id="56777-132">復元するデータベースに応じて、ユーザー データベースを選択するか、 **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="56777-132">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="56777-133">データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56777-133">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="56777-134">**[ファイルおよびファイル グループ]** をクリックして **[ファイルおよびファイル グループの復元]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="56777-134">Click **Files and Filegroups**, which opens the **Restore Files and Filegroups** dialog box.</span></span>  
  
5.  <span data-ttu-id="56777-135">**[全般]** ページの **[復元先データベース]** ボックスに、復元するデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="56777-135">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="56777-136">新しいデータベースを入力するか、ドロップダウン リストから既存のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="56777-136">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="56777-137">このリストには、システム データベース **master** および **tempdb**を除いた、サーバー上のすべてのデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56777-137">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
6.  <span data-ttu-id="56777-138">復元するバックアップ セットの復元元ファイルと場所を指定するには、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="56777-138">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="56777-139">**[復元元データベース]**</span><span class="sxs-lookup"><span data-stu-id="56777-139">**From database**</span></span>  
  
         <span data-ttu-id="56777-140">ボックスにデータベース名を入力します。</span><span class="sxs-lookup"><span data-stu-id="56777-140">Enter a database name in the list box.</span></span> <span data-ttu-id="56777-141">このリストには、 **msdb** バックアップ履歴に従ってバックアップされたデータベースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="56777-141">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="56777-142">**[復元元デバイス]**</span><span class="sxs-lookup"><span data-stu-id="56777-142">**From device**</span></span>  
  
         <span data-ttu-id="56777-143">参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="56777-143">Click the browse button.</span></span> <span data-ttu-id="56777-144">**[バックアップ デバイスの指定]** ダイアログ ボックスで、 **[バックアップ メディアの種類]** ボックスの一覧からいずれかのデバイスの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="56777-144">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="56777-145">**[バックアップ メディア]** ボックスに 1 つまたは複数のデバイスを選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56777-145">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="56777-146">**[バックアップ メディア]** ボックスに目的のデバイスを追加したら、 **[OK]** をクリックして、 **[全般]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="56777-146">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
7.  <span data-ttu-id="56777-147">**[復元するバックアップ セットの選択]** グリッドで、復元するバックアップを選択します。</span><span class="sxs-lookup"><span data-stu-id="56777-147">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="56777-148">このグリッドには、指定された場所に対して使用可能なバックアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56777-148">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="56777-149">既定では、復旧計画が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="56777-149">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="56777-150">推奨された復元計画を変更するには、グリッドの選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="56777-150">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="56777-151">バックアップの選択を解除すると、それに依存するその他のバックアップも自動的に選択が解除されます。</span><span class="sxs-lookup"><span data-stu-id="56777-151">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="56777-152">列見出し</span><span class="sxs-lookup"><span data-stu-id="56777-152">Column head</span></span>|<span data-ttu-id="56777-153">値</span><span class="sxs-lookup"><span data-stu-id="56777-153">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="56777-154">**復元**</span><span class="sxs-lookup"><span data-stu-id="56777-154">**Restore**</span></span>|<span data-ttu-id="56777-155">このチェック ボックスをオンにすると、バックアップ セットが復元されます。</span><span class="sxs-lookup"><span data-stu-id="56777-155">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="56777-156">**名前**</span><span class="sxs-lookup"><span data-stu-id="56777-156">**Name**</span></span>|<span data-ttu-id="56777-157">バックアップ セットの名前です。</span><span class="sxs-lookup"><span data-stu-id="56777-157">The name of the backup set.</span></span>|  
    |<span data-ttu-id="56777-158">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="56777-158">**File Type**</span></span>|<span data-ttu-id="56777-159">バックアップのデータの種類を指定します。**データ**、**ログ**、または **Filestream データ**です。</span><span class="sxs-lookup"><span data-stu-id="56777-159">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="56777-160">テーブルに含まれるデータの種類は、 **データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="56777-160">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="56777-161">トランザクション ログ データの種類は、 **ログ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="56777-161">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="56777-162">ファイル システムに格納されたバイナリ ラージ オブジェクト (BLOB) データの種類は、 **FILESTREAM データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="56777-162">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="56777-163">**Type**</span><span class="sxs-lookup"><span data-stu-id="56777-163">**Type**</span></span>|<span data-ttu-id="56777-164">実行するバックアップの種類: **[完全]** 、 **[差分]** 、 **[トランザクション ログ]** 。</span><span class="sxs-lookup"><span data-stu-id="56777-164">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="56777-165">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="56777-165">**Server**</span></span>|<span data-ttu-id="56777-166">バックアップ操作を実行するデータベース エンジン インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="56777-166">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="56777-167">**[ファイルの論理名]**</span><span class="sxs-lookup"><span data-stu-id="56777-167">**File Logical Name**</span></span>|<span data-ttu-id="56777-168">ファイルの論理名です。</span><span class="sxs-lookup"><span data-stu-id="56777-168">The logical name of the file.</span></span>|  
    |<span data-ttu-id="56777-169">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="56777-169">**Database**</span></span>|<span data-ttu-id="56777-170">バックアップ操作に呼び出されるデータベース名です。</span><span class="sxs-lookup"><span data-stu-id="56777-170">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="56777-171">**[開始日]**</span><span class="sxs-lookup"><span data-stu-id="56777-171">**Start Date**</span></span>|<span data-ttu-id="56777-172">バックアップ操作が開始した日時で、クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="56777-172">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="56777-173">**完了日**</span><span class="sxs-lookup"><span data-stu-id="56777-173">**Finish Date**</span></span>|<span data-ttu-id="56777-174">バックアップ操作が完了したときの日付と時刻。クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="56777-174">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="56777-175">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="56777-175">**Size**</span></span>|<span data-ttu-id="56777-176">バックアップ セットのサイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="56777-176">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="56777-177">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="56777-177">**User Name**</span></span>|<span data-ttu-id="56777-178">バックアップ操作を実行したユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="56777-178">The name of the user who performed the backup operation.</span></span>|  
  
8.  <span data-ttu-id="56777-179">詳細設定オプションの表示または選択を行うには、 **[ページの選択]** ペインの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56777-179">To view or select the advanced options, click **Options** in the **Select a page pane**.</span></span>  
  
9. <span data-ttu-id="56777-180">状況が適切であれば、 **[復元オプション]** パネルでは、次の任意のオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="56777-180">In the **Restore options** panel, you can choose any of the following options, if appropriate for your situation.</span></span>  
  
     <span data-ttu-id="56777-181">**[ファイル グループとして復元する]**</span><span class="sxs-lookup"><span data-stu-id="56777-181">**Restore as filegroup**</span></span>  
     <span data-ttu-id="56777-182">ファイル グループ全体が復元されることを示します。</span><span class="sxs-lookup"><span data-stu-id="56777-182">Indicates that an entire filegroup is being restored.</span></span>  
  
     <span data-ttu-id="56777-183">**[既存のデータベースを上書きする]**</span><span class="sxs-lookup"><span data-stu-id="56777-183">**Overwrite the existing database**</span></span>  
     <span data-ttu-id="56777-184">同じ名前を持つ別のデータベースまたはファイルが既に存在していても、復元操作で既存のデータベースおよび関連ファイルを上書きするように指定します。</span><span class="sxs-lookup"><span data-stu-id="56777-184">Specifies that the restore operation should overwrite any existing databases and their related files, even if another database or file already exists with the same name.</span></span>  
  
     <span data-ttu-id="56777-185">このオプションを選択することは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE ステートメントで REPLACE オプションを使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="56777-185">Selecting this option is equivalent to using the REPLACE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="56777-186">**[各バックアップを復元する前に確認する]**</span><span class="sxs-lookup"><span data-stu-id="56777-186">**Prompt before restoring each backup**</span></span>  
     <span data-ttu-id="56777-187">各バックアップ セットを復元する前にユーザーに確認します。</span><span class="sxs-lookup"><span data-stu-id="56777-187">Asks you for confirmation before restoring each backup set.</span></span>  
  
     <span data-ttu-id="56777-188">このオプションは、サーバーのテープ デバイスが 1 台であるために、メディア セットごとにテープを入れ替える必要がある場合などに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="56777-188">This option is particularly useful where you must swap tapes for different media sets, such as when the server has one tape device.</span></span>  
  
     <span data-ttu-id="56777-189">**[復元するデータベースへのアクセスを制限する]**</span><span class="sxs-lookup"><span data-stu-id="56777-189">**Restrict access to the restored database**</span></span>  
     <span data-ttu-id="56777-190">復元するデータベースの使用を、 **db_owner**、 **dbcreator**、または **sysadmin**のメンバーだけに制限します。</span><span class="sxs-lookup"><span data-stu-id="56777-190">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
     <span data-ttu-id="56777-191">このオプションを選択することは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE ステートメントで RESTRICTED_USER オプションを使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="56777-191">Selecting this option is synonymous to using the RESTRICTED_USER option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
10. <span data-ttu-id="56777-192">新しい場所にデータベースを復元する場合、必要に応じて、 **[次のデータベース ファイルに復元]** グリッドで各ファイルの新しい復元先を指定できます。</span><span class="sxs-lookup"><span data-stu-id="56777-192">Optionally, you can restore the database to a new location by specifying a new restore destination for each file in the **Restore database files as** grid.</span></span>  
  
    |<span data-ttu-id="56777-193">列見出し</span><span class="sxs-lookup"><span data-stu-id="56777-193">Column head</span></span>|<span data-ttu-id="56777-194">値</span><span class="sxs-lookup"><span data-stu-id="56777-194">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="56777-195">**[元のファイル名]**</span><span class="sxs-lookup"><span data-stu-id="56777-195">**Original File Name**</span></span>|<span data-ttu-id="56777-196">ソース バックアップ ファイルの完全なパスです。</span><span class="sxs-lookup"><span data-stu-id="56777-196">The full path of a source backup file.</span></span>|  
    |<span data-ttu-id="56777-197">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="56777-197">**File Type**</span></span>|<span data-ttu-id="56777-198">バックアップのデータの種類を指定します。**データ**、**ログ**、または **Filestream データ**です。</span><span class="sxs-lookup"><span data-stu-id="56777-198">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="56777-199">テーブルに含まれるデータの種類は、 **データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="56777-199">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="56777-200">トランザクション ログ データの種類は、 **ログ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="56777-200">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="56777-201">ファイル システムに格納されたバイナリ ラージ オブジェクト (BLOB) データの種類は、 **FILESTREAM データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="56777-201">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="56777-202">**[復元先]**</span><span class="sxs-lookup"><span data-stu-id="56777-202">**Restore As**</span></span>|<span data-ttu-id="56777-203">復元されるデータベース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="56777-203">The full path of the database file to be restored.</span></span> <span data-ttu-id="56777-204">新しい復元ファイルを指定するには、テキスト ボックスをクリックして、指定されているパスおよびファイル名を編集します。</span><span class="sxs-lookup"><span data-stu-id="56777-204">To specify a new restore file, click the text box and edit the suggested path and file name.</span></span> <span data-ttu-id="56777-205">**[復元先]** 列でパスまたはファイル名を変更することは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE ステートメントで MOVE オプションを使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="56777-205">Changing the path or file name in the **Restore As** column is equivalent to using the MOVE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>|  
  
11. <span data-ttu-id="56777-206">**[復旧状態]** パネルの選択内容により、復元操作後のデータベースの状態が決まります。</span><span class="sxs-lookup"><span data-stu-id="56777-206">The **Recovery state** panel determines the state of the database after the restore operation.</span></span>  
  
     <span data-ttu-id="56777-207">**[コミットされていないトランザクションをロールバックして、データベースを使用可能な状態にする。別のトランザクション ログは復元できません。(RESTORE WITH RECOVERY)]**</span><span class="sxs-lookup"><span data-stu-id="56777-207">**Leave the database ready for use by rolling back the uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**</span></span>  
     <span data-ttu-id="56777-208">データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="56777-208">Recovers the database.</span></span> <span data-ttu-id="56777-209">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="56777-209">This is the default behavior.</span></span> <span data-ttu-id="56777-210">このオプションは、必要なすべてのバックアップをすべて復元する場合のみ選択します。</span><span class="sxs-lookup"><span data-stu-id="56777-210">Choose this option only if you are restoring all of the necessary backups now.</span></span> <span data-ttu-id="56777-211">このオプションを選択することは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE ステートメントで WITH RECOVERY を使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="56777-211">This option is equivalent to specifying WITH RECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="56777-212">**データベースは操作不可状態のままで、コミットされていないトランザクションはロールバックしない。別のトランザクション ログは復元できます(RESTORE WITH NORECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="56777-212">**Leave the database non-operational, and don't roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**</span></span>  
     <span data-ttu-id="56777-213">データベースを復元状態のままにします。</span><span class="sxs-lookup"><span data-stu-id="56777-213">Leaves the database in the restoring state.</span></span> <span data-ttu-id="56777-214">データベースを復旧するには、RESTORE WITH RECOVERY オプションを使用して (上記を参照) 別の復元を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56777-214">To recover the database, you will need to perform another restore using the preceding RESTORE WITH RECOVERY option (see above).</span></span> <span data-ttu-id="56777-215">このオプションを選択することは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE ステートメントで WITH NORECOVERY を使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="56777-215">This option is equivalent to specifying WITH NORECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="56777-216">このオプションを選択すると、 **[レプリケーションの設定を保存する]** オプションを選択できなくなります。</span><span class="sxs-lookup"><span data-stu-id="56777-216">If you select this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
     <span data-ttu-id="56777-217">**[データベースを読み取り専用モードにする。コミットされていないトランザクションはロールバックされますが、復旧結果を元に戻せるようにロールバック操作をファイルに保存します。(RESTORE WITH STANDBY)]**</span><span class="sxs-lookup"><span data-stu-id="56777-217">**Leave the database in read-only mode. Roll back the uncommitted transactions, but save the rollback operation in a file so the recovery effects can be undone. (RESTORE WITH STANDBY)**</span></span>  
     <span data-ttu-id="56777-218">データベースをスタンバイ状態のままにします。</span><span class="sxs-lookup"><span data-stu-id="56777-218">Leaves the database in a standby state.</span></span> <span data-ttu-id="56777-219">このオプションを選択することは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE ステートメントで WITH STANDBY を使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="56777-219">This option is equivalent to specifying WITH STANDBY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="56777-220">このオプションを選択した場合は、スタンバイ ファイルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56777-220">Choosing this option requires that you specify a standby file.</span></span>  
  
     <span data-ttu-id="56777-221">**[ロールバック UNDO ファイル]**</span><span class="sxs-lookup"><span data-stu-id="56777-221">**Rollback undo file**</span></span>  
     <span data-ttu-id="56777-222">**[ロールバック UNDO ファイル]** テキスト ボックスで、スタンバイ ファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="56777-222">Specify a standby file name in the **Rollback undo file** text box.</span></span> <span data-ttu-id="56777-223">データベースを読み取り専用モード (RECOVERY WITH STANDBY) にする場合は、このオプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="56777-223">This option is required if you leave the database in read-only mode (RESTORE WITH STANDBY).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="56777-224">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="56777-224">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-and-filegroups"></a><span data-ttu-id="56777-225">ファイルおよびファイル グループを復元するには</span><span class="sxs-lookup"><span data-stu-id="56777-225">To restore files and filegroups</span></span>  
  
1.  <span data-ttu-id="56777-226">RESTORE DATABASE ステートメントを実行して、ファイルとファイル グループのバックアップを復元します。そのとき、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="56777-226">Execute the RESTORE DATABASE statement to restore the file and filegroup backup, specifying:</span></span>  
  
    -   <span data-ttu-id="56777-227">復元するデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="56777-227">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="56777-228">復元するデータベースの完全バックアップが格納されているバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="56777-228">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="56777-229">復元する各ファイルに対応する FILE 句。</span><span class="sxs-lookup"><span data-stu-id="56777-229">The FILE clause for each file to restore.</span></span>  
  
    -   <span data-ttu-id="56777-230">復元する各ファイル グループに対応する FILEGROUP 句。</span><span class="sxs-lookup"><span data-stu-id="56777-230">The FILEGROUP clause for each filegroup to restore.</span></span>  
  
    -   <span data-ttu-id="56777-231">NORECOVERY 句。</span><span class="sxs-lookup"><span data-stu-id="56777-231">The NORECOVERY clause.</span></span> <span data-ttu-id="56777-232">バックアップ作成後にファイルが変更されていない場合は、RECOVERY 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="56777-232">If the files have not been modified after the backup was created, specify the RECOVERY clause.</span></span>  
  
2.  <span data-ttu-id="56777-233">ファイル バックアップの作成後にファイルが変更された場合は、RESTORE LOG ステートメントを実行して、トランザクション ログ バックアップを適用します。そのとき、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="56777-233">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="56777-234">トランザクション ログが適用されるデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="56777-234">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="56777-235">復元するトランザクション ログのバックアップが格納されているバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="56777-235">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="56777-236">NORECOVERY 句。現在のトランザクション ログ バックアップを適用した後、別のバックアップがある場合に指定します。それ以外の場合は RECOVERY 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="56777-236">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="56777-237">トランザクション ログ バックアップを適用する場合、そのバックアップには、ファイルとファイル グループのバックアップが作成された時刻の情報が格納されている必要があります (すべてのデータベース ファイルを復元する場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="56777-237">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up until the end of log (unless ALL database files are restored).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="56777-238">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="56777-238">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="56777-239">この例では、 `MyDatabase` データベースのファイルとファイル グループを復元します。</span><span class="sxs-lookup"><span data-stu-id="56777-239">This example restores the files and filegroups for the `MyDatabase` database.</span></span> <span data-ttu-id="56777-240">データベースを現在の時刻に復元するために、2 つのトランザクション ログが適用されます。</span><span class="sxs-lookup"><span data-stu-id="56777-240">To restore the database to the current time, two transaction logs are applied.</span></span>  
  
```sql  
USE master;  
GO  
-- Restore the files and filesgroups for MyDatabase.  
RESTORE DATABASE MyDatabase  
   FILE = 'MyDatabase_data_1',  
   FILEGROUP = 'new_customers',  
   FILE = 'MyDatabase_data_2',  
   FILEGROUP = 'first_qtr_sales'  
   FROM MyDatabase_1  
   WITH NORECOVERY;  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="56777-241">参照</span><span class="sxs-lookup"><span data-stu-id="56777-241">See Also</span></span>  
 <span data-ttu-id="56777-242">[データベースバックアップを復元する &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="56777-242">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="56777-243">[ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56777-243">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="56777-244">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56777-244">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="56777-245">[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56777-245">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="56777-246">[トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56777-246">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="56777-247">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56777-247">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
