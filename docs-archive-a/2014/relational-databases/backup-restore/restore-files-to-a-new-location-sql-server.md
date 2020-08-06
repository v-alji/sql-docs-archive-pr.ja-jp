---
title: 新しい場所へのファイルの復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring files [SQL Server], how-to topics
- restoring databases [SQL Server], moving
- restoring files [SQL Server], steps
- file restores [SQL Server], how-to topics
- filegroups [SQL Server], restoring
- restoring filegroups [SQL Server]
ms.assetid: b4f4791d-646e-4632-9980-baae9cb1aade
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a8336e5d186fb72df4e0a17fdd9affccab4ee57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715418"
---
# <a name="restore-files-to-a-new-location-sql-server"></a><span data-ttu-id="4acfc-102">新しい場所へのファイルの復元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4acfc-102">Restore Files to a New Location (SQL Server)</span></span>
  <span data-ttu-id="4acfc-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で新しい場所にファイルを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-103">This topic describes how to restore files to a new location in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4acfc-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4acfc-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4acfc-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4acfc-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4acfc-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4acfc-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4acfc-107">Security</span><span class="sxs-lookup"><span data-stu-id="4acfc-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4acfc-108">**ファイルを新しい場所に復元する方法:**</span><span class="sxs-lookup"><span data-stu-id="4acfc-108">**To restore files to a new location, using:**</span></span>  
  
     [<span data-ttu-id="4acfc-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4acfc-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4acfc-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4acfc-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4acfc-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="4acfc-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4acfc-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4acfc-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4acfc-113">ファイルの復元中は、復元作業を実行するシステム管理者以外は、復元されるデータベースを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4acfc-113">The system administrator restoring the files must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="4acfc-114">RESTORE は、明示的または暗黙的なトランザクションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="4acfc-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="4acfc-115">完全復旧モデルまたは一括ログ復旧モデルを使用する場合は、ファイルを復元する前に、ログの末尾と呼ばれるアクティブ トランザクション ログをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4acfc-115">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="4acfc-116">詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4acfc-116">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="4acfc-117">暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。</span><span class="sxs-lookup"><span data-stu-id="4acfc-117">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="4acfc-118">証明書または非対称キーがないと、データベースは復元できません。</span><span class="sxs-lookup"><span data-stu-id="4acfc-118">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="4acfc-119">このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4acfc-119">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="4acfc-120">詳細については、「 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4acfc-120">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4acfc-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4acfc-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4acfc-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="4acfc-122">Permissions</span></span>  
 <span data-ttu-id="4acfc-123">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4acfc-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="4acfc-124">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="4acfc-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="4acfc-125">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="4acfc-126">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="4acfc-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4acfc-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4acfc-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-to-a-new-location"></a><span data-ttu-id="4acfc-128">ファイルを新しい場所に復元するには</span><span class="sxs-lookup"><span data-stu-id="4acfc-128">To restore files to a new location</span></span>  
  
1.  <span data-ttu-id="4acfc-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続して、そのインスタンスを展開します。次に、 **[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-129">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="4acfc-130">目的のデータベースを右クリックし、 **[タスク]** 、 **[復元]** の順にポイントし、 **[ファイルおよびファイル グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4acfc-130">Right-click the database that you want, point to **Tasks**, point to **Restore**, and then click **Files and Filegroups**.</span></span>  
  
3.  <span data-ttu-id="4acfc-131">**[全般]** ページの **[復元先データベース]** ボックスに、復元するデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-131">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="4acfc-132">新しいデータベースを入力するか、ドロップダウン リストから既存のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-132">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="4acfc-133">このリストには、システム データベース **master** および **tempdb**を除いた、サーバー上のすべてのデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-133">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
4.  <span data-ttu-id="4acfc-134">復元するバックアップ セットの復元元ファイルと場所を指定するには、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4acfc-134">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="4acfc-135">**[復元元データベース]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-135">**From database**</span></span>  
  
         <span data-ttu-id="4acfc-136">ボックスにデータベース名を入力します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-136">Enter a database name in the list box.</span></span> <span data-ttu-id="4acfc-137">このリストには、 **msdb** バックアップ履歴に従ってバックアップされたデータベースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-137">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="4acfc-138">**[復元元デバイス]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-138">**From device**</span></span>  
  
         <span data-ttu-id="4acfc-139">参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4acfc-139">Click the browse button.</span></span> <span data-ttu-id="4acfc-140">**[バックアップ デバイスの指定]** ダイアログ ボックスで、 **[バックアップ メディアの種類]** ボックスの一覧からいずれかのデバイスの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-140">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="4acfc-141">**[バックアップ メディア]** ボックスに 1 つまたは複数のデバイスを選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4acfc-141">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="4acfc-142">**[バックアップ メディア]** ボックスに目的のデバイスを追加したら、 **[OK]** をクリックして、 **[全般]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4acfc-142">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
5.  <span data-ttu-id="4acfc-143">**[復元するバックアップ セットの選択]** グリッドで、復元するバックアップを選択します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-143">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="4acfc-144">このグリッドには、指定された場所に対して使用可能なバックアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-144">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="4acfc-145">既定では、復旧計画が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="4acfc-145">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="4acfc-146">推奨された復元計画を変更するには、グリッドの選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-146">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="4acfc-147">バックアップの選択を解除すると、それに依存するその他のバックアップも自動的に選択が解除されます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-147">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="4acfc-148">列見出し</span><span class="sxs-lookup"><span data-stu-id="4acfc-148">Column head</span></span>|<span data-ttu-id="4acfc-149">値</span><span class="sxs-lookup"><span data-stu-id="4acfc-149">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="4acfc-150">**復元**</span><span class="sxs-lookup"><span data-stu-id="4acfc-150">**Restore**</span></span>|<span data-ttu-id="4acfc-151">このチェック ボックスをオンにすると、バックアップ セットが復元されます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-151">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="4acfc-152">**名前**</span><span class="sxs-lookup"><span data-stu-id="4acfc-152">**Name**</span></span>|<span data-ttu-id="4acfc-153">バックアップ セットの名前です。</span><span class="sxs-lookup"><span data-stu-id="4acfc-153">The name of the backup set.</span></span>|  
    |<span data-ttu-id="4acfc-154">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-154">**File Type**</span></span>|<span data-ttu-id="4acfc-155">バックアップのデータの種類を指定します。**データ**、**ログ**、または **Filestream データ**です。</span><span class="sxs-lookup"><span data-stu-id="4acfc-155">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="4acfc-156">テーブルに含まれるデータの種類は、 **データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-156">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="4acfc-157">トランザクション ログ データの種類は、 **ログ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-157">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="4acfc-158">ファイル システムに格納されたバイナリ ラージ オブジェクト (BLOB) データの種類は、 **FILESTREAM データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-158">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="4acfc-159">**Type**</span><span class="sxs-lookup"><span data-stu-id="4acfc-159">**Type**</span></span>|<span data-ttu-id="4acfc-160">実行するバックアップの種類: **[完全]** 、 **[差分]** 、 **[トランザクション ログ]** 。</span><span class="sxs-lookup"><span data-stu-id="4acfc-160">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="4acfc-161">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-161">**Server**</span></span>|<span data-ttu-id="4acfc-162">バックアップ操作を実行するデータベース エンジン インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="4acfc-162">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="4acfc-163">**[ファイルの論理名]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-163">**File Logical Name**</span></span>|<span data-ttu-id="4acfc-164">ファイルの論理名です。</span><span class="sxs-lookup"><span data-stu-id="4acfc-164">The logical name of the file.</span></span>|  
    |<span data-ttu-id="4acfc-165">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-165">**Database**</span></span>|<span data-ttu-id="4acfc-166">バックアップ操作に呼び出されるデータベース名です。</span><span class="sxs-lookup"><span data-stu-id="4acfc-166">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="4acfc-167">**[開始日]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-167">**Start Date**</span></span>|<span data-ttu-id="4acfc-168">バックアップ操作が開始した日時で、クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-168">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="4acfc-169">**完了日**</span><span class="sxs-lookup"><span data-stu-id="4acfc-169">**Finish Date**</span></span>|<span data-ttu-id="4acfc-170">バックアップ操作が完了したときの日付と時刻。クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-170">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="4acfc-171">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-171">**Size**</span></span>|<span data-ttu-id="4acfc-172">バックアップ セットのサイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="4acfc-172">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="4acfc-173">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="4acfc-173">**User Name**</span></span>|<span data-ttu-id="4acfc-174">バックアップ操作を実行したユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="4acfc-174">The name of the user who performed the backup operation.</span></span>|  
  
6.  <span data-ttu-id="4acfc-175">**[ページの選択]** ペインの **[オプション]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4acfc-175">In the **Select a page** pane, click the **Options** page.</span></span>  
  
7.  <span data-ttu-id="4acfc-176">**[次のデータベース ファイルに復元]** グリッドに、移動するファイルの新しい場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-176">In the **Restore database files as** grid, specify a new location for the file or files that you want to move.</span></span>  
  
    |<span data-ttu-id="4acfc-177">列見出し</span><span class="sxs-lookup"><span data-stu-id="4acfc-177">Column head</span></span>|<span data-ttu-id="4acfc-178">値</span><span class="sxs-lookup"><span data-stu-id="4acfc-178">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="4acfc-179">**[元のファイル名]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-179">**Original File Name**</span></span>|<span data-ttu-id="4acfc-180">ソース バックアップ ファイルの完全なパスです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-180">The full path of a source backup file.</span></span>|  
    |<span data-ttu-id="4acfc-181">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-181">**File Type**</span></span>|<span data-ttu-id="4acfc-182">バックアップのデータの種類を指定します。**データ**、**ログ**、または **Filestream データ**です。</span><span class="sxs-lookup"><span data-stu-id="4acfc-182">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="4acfc-183">テーブルに含まれるデータの種類は、 **データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-183">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="4acfc-184">トランザクション ログ データの種類は、 **ログ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-184">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="4acfc-185">ファイル システムに格納されたバイナリ ラージ オブジェクト (BLOB) データの種類は、 **FILESTREAM データ** ファイルです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-185">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="4acfc-186">**[復元先]**</span><span class="sxs-lookup"><span data-stu-id="4acfc-186">**Restore As**</span></span>|<span data-ttu-id="4acfc-187">復元されるデータベース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-187">The full path of the database file to be restored.</span></span> <span data-ttu-id="4acfc-188">新しい復元ファイルを指定するには、テキスト ボックスをクリックして、指定されているパスおよびファイル名を編集します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-188">To specify a new restore file, click the text box and edit the suggested path and file name.</span></span> <span data-ttu-id="4acfc-189">**[復元先]** 列でパスまたはファイル名を変更することは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE ステートメントで MOVE オプションを使用することと同じです。</span><span class="sxs-lookup"><span data-stu-id="4acfc-189">Changing the path or file name in the **Restore As** column is equivalent to using the MOVE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>|  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4acfc-190">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4acfc-190">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-to-a-new-location"></a><span data-ttu-id="4acfc-191">ファイルを新しい場所に復元するには</span><span class="sxs-lookup"><span data-stu-id="4acfc-191">To restore files to a new location</span></span>  
  
1.  <span data-ttu-id="4acfc-192">必要に応じて、RESTORE FILELISTONLY ステートメントを実行し、データベースの完全バックアップ内のファイル数とファイル名を特定します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-192">Optionally, execute the RESTORE FILELISTONLY statement to determine the number and names of the files in the full database backup.</span></span>  
  
2.  <span data-ttu-id="4acfc-193">次の項目を指定した RESTORE DATABASE ステートメントを実行し、データベースの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-193">Execute the RESTORE DATABASE statement to restore the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="4acfc-194">復元するデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="4acfc-194">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="4acfc-195">復元するデータベースの完全バックアップが格納されているバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="4acfc-195">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="4acfc-196">新しい場所に復元するファイルごとの MOVE 句。</span><span class="sxs-lookup"><span data-stu-id="4acfc-196">The MOVE clause for each file to restore to a new location.</span></span>  
  
    -   <span data-ttu-id="4acfc-197">NORECOVERY 句。</span><span class="sxs-lookup"><span data-stu-id="4acfc-197">The NORECOVERY clause.</span></span>  
  
3.  <span data-ttu-id="4acfc-198">ファイル バックアップの作成後にファイルが変更された場合は、RESTORE LOG ステートメントを実行して、トランザクション ログ バックアップを適用します。そのとき、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-198">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="4acfc-199">トランザクション ログが適用されるデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="4acfc-199">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="4acfc-200">復元するトランザクション ログのバックアップが格納されているバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="4acfc-200">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="4acfc-201">NORECOVERY 句。現在のトランザクション ログ バックアップを適用した後、別のバックアップがある場合に指定します。それ以外の場合は RECOVERY 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-201">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="4acfc-202">トランザクション ログ バックアップを適用する場合、そのバックアップには、ファイルとファイル グループのバックアップが作成された時刻の情報が格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4acfc-202">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4acfc-203">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4acfc-203">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4acfc-204">この例では、元は C ドライブに配置されていた `MyNwind` データベースの 2 つのファイルを D ドライブ上の新しい場所に復元します。データベースを現在の時刻に復元するために、2 つのトランザクション ログも適用されます。</span><span class="sxs-lookup"><span data-stu-id="4acfc-204">This example restores two of the files for the `MyNwind` database that were originally located on Drive C to new locations on Drive D. Two transaction logs will also be applied to restore the database to the current time.</span></span> <span data-ttu-id="4acfc-205">`RESTORE FILELISTONLY` ステートメントは、復元するデータベース内のファイルの数、論理名、および物理名をするために使用します。</span><span class="sxs-lookup"><span data-stu-id="4acfc-205">The `RESTORE FILELISTONLY` statement is used to determine the number and logical and physical names of the files in the database being restored.</span></span>  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
RESTORE FILELISTONLY  
   FROM MyNwind_1;  
-- Restore the files for MyNwind.  
RESTORE DATABASE MyNwind  
   FROM MyNwind_1  
   WITH NORECOVERY,  
   MOVE 'MyNwind_data_1' TO 'D:\MyData\MyNwind_data_1.mdf',   
   MOVE 'MyNwind_data_2' TO 'D:\MyData\MyNwind_data_2.ndf';  
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
  
## <a name="see-also"></a><span data-ttu-id="4acfc-206">参照</span><span class="sxs-lookup"><span data-stu-id="4acfc-206">See Also</span></span>  
 <span data-ttu-id="4acfc-207">[データベースバックアップを復元する &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="4acfc-207">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="4acfc-208">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4acfc-208">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="4acfc-209">[バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="4acfc-209">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="4acfc-210">ファイルおよびファイル グループの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4acfc-210">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
  
