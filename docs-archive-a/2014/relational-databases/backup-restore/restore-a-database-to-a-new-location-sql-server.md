---
title: データベースを新しい場所に復元する (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], moving
- database restores [SQL Server], creating new databases
- restoring [SQL Server], with move
- restoring databases [SQL Server], creating new databases
- database backups [SQL Server], creating new database from
- backing up databases [SQL Server], creating new database from
- restoring databases [SQL Server], renaming
- database creation [SQL Server], restoring with move
ms.assetid: 4da76d61-5e11-4bee-84f5-b305240d9f42
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 89b42f439b5622074327506b9f2ca2b2358cd12f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643429"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a><span data-ttu-id="5579c-102">データベースを新しい場所に復元する (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5579c-102">Restore a Database to a New Location (SQL Server)</span></span>
  <span data-ttu-id="5579c-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)]データベースを新しい場所に復元し、必要に応じてデータベースの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5579c-103">This topic describes how to restore a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a new location, and optionally rename the database, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5579c-104">新しいディレクトリ パスにデータベースを移動できるほか、同じサーバー インスタンスまたは別のサーバー インスタンスにデータベースのコピーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5579c-104">You can move a database to a new directory path or create a copy of a database on either the same server instance or a different server instance.</span></span>  
  
 <span data-ttu-id="5579c-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="5579c-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5579c-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="5579c-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5579c-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5579c-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5579c-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="5579c-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="5579c-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="5579c-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="5579c-110">Security</span><span class="sxs-lookup"><span data-stu-id="5579c-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5579c-111">**新しい場所にデータベースを復元し、必要に応じて名前を変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="5579c-111">**To restore a database to a new location, and optionally rename the database, using:**</span></span>  
  
     [<span data-ttu-id="5579c-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5579c-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5579c-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5579c-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="5579c-114">関連タスク</span><span class="sxs-lookup"><span data-stu-id="5579c-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5579c-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="5579c-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5579c-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5579c-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5579c-117">データベースの完全バックアップの復元中は、復元作業を実行するシステム管理者以外は、復元中のデータベースを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5579c-117">The system administrator restoring a full database backup must be the only person currently using the database to be restored.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="5579c-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="5579c-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="5579c-119">完全復旧モデルまたは一括ログ復旧モデルを使用する場合は、データベースを復元する前に、アクティブ トランザクション ログをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5579c-119">Under the full or bulk-logged recovery model, before you can restore a database, you must back up the active transaction log.</span></span> <span data-ttu-id="5579c-120">詳細については、「[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-120">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="5579c-121">推奨事項</span><span class="sxs-lookup"><span data-stu-id="5579c-121">Recommendations</span></span>  
  
-   <span data-ttu-id="5579c-122">暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。</span><span class="sxs-lookup"><span data-stu-id="5579c-122">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="5579c-123">証明書または非対称キーがないと、データベースは復元できません。</span><span class="sxs-lookup"><span data-stu-id="5579c-123">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="5579c-124">このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="5579c-124">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="5579c-125">詳細については、「 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5579c-125">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
-   <span data-ttu-id="5579c-126">データベースの移行に関するその他の考慮事項については、「[バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-126">For information about additional considerations for moving a database, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
-   <span data-ttu-id="5579c-127">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のデータベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]に復元すると、データベースが自動的にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="5579c-127">If you restore a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or higher  database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is automatically upgraded.</span></span> <span data-ttu-id="5579c-128">通常、データベースは直ちに使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="5579c-128">Typically, the database becomes available immediately.</span></span> <span data-ttu-id="5579c-129">ただし、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、  **upgrade_option** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。</span><span class="sxs-lookup"><span data-stu-id="5579c-129">However, if a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade_option** server property.</span></span> <span data-ttu-id="5579c-130">アップグレード オプションがインポート (**upgrade_option** = 2) または再構築 (**upgrade_option** = 0) に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5579c-130">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="5579c-131">インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="5579c-131">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="5579c-132">また、アップグレード オプションがインポートに設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="5579c-132">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="5579c-133">**upgrade_option** サーバー プロパティの設定を変更するには、 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="5579c-133">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5579c-134">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5579c-134">Security</span></span>  
 <span data-ttu-id="5579c-135">セキュリティを確保するため、不明なソースや信頼されていないソースからのデータベースは、アタッチまたは復元しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5579c-135">For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="5579c-136">こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5579c-136">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="5579c-137">不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。</span><span class="sxs-lookup"><span data-stu-id="5579c-137">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5579c-138">Permissions</span><span class="sxs-lookup"><span data-stu-id="5579c-138">Permissions</span></span>  
 <span data-ttu-id="5579c-139">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5579c-139">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="5579c-140">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています。</span><span class="sxs-lookup"><span data-stu-id="5579c-140">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database.</span></span>  
  
 <span data-ttu-id="5579c-141">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="5579c-141">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="5579c-142">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="5579c-142">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5579c-143">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="5579c-143">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a><span data-ttu-id="5579c-144">新しい場所にデータベースを復元し、必要に応じて名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="5579c-144">To restore a database to a new location, and optionally rename the database</span></span>  
  
1.  <span data-ttu-id="5579c-145">適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5579c-145">Connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="5579c-146">**[データベース]** を右クリックし、 **[データベースの復元]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5579c-146">Right-click **Databases**, and then click **Restore Database**.</span></span> <span data-ttu-id="5579c-147">**[データベースの復元]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5579c-147">The **Restore Database** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="5579c-148">**[全般]** ページの **復元元**のセクションを使用して、復元するバックアップ セットの復元元ファイルと場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-148">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="5579c-149">以下のオプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="5579c-149">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="5579c-150">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="5579c-150">**Database**</span></span>  
  
         <span data-ttu-id="5579c-151">復元するデータベースをドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="5579c-151">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="5579c-152">このリストには、 **msdb** バックアップ履歴に従ってバックアップされたデータベースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5579c-152">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5579c-153">別のサーバーで作成されたバックアップの場合、復元先のサーバーには指定されたデータベースのバックアップ履歴情報が存在しません。</span><span class="sxs-lookup"><span data-stu-id="5579c-153">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="5579c-154">この場合、 **[デバイス]** をクリックして、復元するファイルまたはデバイスを手動で指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-154">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    1.  <span data-ttu-id="5579c-155">**[デバイス]**</span><span class="sxs-lookup"><span data-stu-id="5579c-155">**Device**</span></span>  
  
         <span data-ttu-id="5579c-156">参照ボタン ( **[...]** ) をクリックし、 **[バックアップ デバイスの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="5579c-156">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="5579c-157">**[バックアップ メディアの種類]** ボックスから、デバイスの種類を 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="5579c-157">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="5579c-158">**[バックアップ メディア]** ボックスにデバイスを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5579c-158">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="5579c-159">**[バックアップ メディア]** ボックスに目的のデバイスを追加したら、 **[OK]** をクリックして、 **[全般]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="5579c-159">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="5579c-160">**[ソース: デバイス:データベース]** リスト ボックスで、復元するデータベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="5579c-160">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="5579c-161">**メモ** この一覧は **[デバイス]** をクリックした場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5579c-161">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="5579c-162">選択されたデバイスにバックアップを持つデータベースのみが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5579c-162">Only databases that have backups on the selected device will be available.</span></span>  
  
4.  <span data-ttu-id="5579c-163">**復元先のセクション**の **[データベース]** ボックスに、復元するデータベースの名前が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5579c-163">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="5579c-164">データベースの名前を変更するには、 **[データベース]** ボックスに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="5579c-164">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
5.  <span data-ttu-id="5579c-165">**[復元先]** ボックスで、既定値の **[最後に作成されたバックアップ]** のままにするか、 **[タイムライン]** をクリックして、 **[バックアップのタイムライン]** ダイアログ ボックスにアクセスし、具体的にどの時点で復旧アクションを停止するかを手動で選択します。</span><span class="sxs-lookup"><span data-stu-id="5579c-165">In the **Restore to** box, leave the default as **To the last backup taken** or click on **Timeline** to access the **Backup Timeline** dialog box to manually select a point in time to stop the recovery action.</span></span> <span data-ttu-id="5579c-166">特定の時点を指定する方法の詳細については、「 [Backup Timeline](backup-timeline.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-166">See [Backup Timeline](backup-timeline.md) for more information on designating a specific point in time.</span></span>  
  
6.  <span data-ttu-id="5579c-167">**[復元するバックアップ セット]** グリッドで、復元するバックアップを選択します。</span><span class="sxs-lookup"><span data-stu-id="5579c-167">In the **Backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="5579c-168">このグリッドには、指定された場所に対して使用可能なバックアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5579c-168">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="5579c-169">既定では、復旧計画が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="5579c-169">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="5579c-170">推奨された復元計画を変更するには、グリッドの選択を変更します。</span><span class="sxs-lookup"><span data-stu-id="5579c-170">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="5579c-171">以前のバックアップの選択を解除すると、以前のバックアップの復元に依存するバックアップは自動的に選択が解除されます。</span><span class="sxs-lookup"><span data-stu-id="5579c-171">Backups that depend on the restoration of an earlier backup are automatically deselected when the earlier backup is deselected.</span></span>  
  
     <span data-ttu-id="5579c-172">**[復元するバックアップ セット]** グリッドの列の詳細については、「[データベースの復元 &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-172">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
7.  <span data-ttu-id="5579c-173">データベース ファイルの新しい場所を指定するには、 **[ファイル]** ページを選択し、 **[すべてのファイルをフォルダーに移動する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5579c-173">To specify the new location of the database files, select the **Files** page, and then click **Relocate all files to folder**.</span></span> <span data-ttu-id="5579c-174">**[データ ファイルのフォルダー]** および **[ログ ファイルのフォルダー]** の新しい場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-174">Provide a new location for the **Data file folder** and **Log file folder**.</span></span> <span data-ttu-id="5579c-175">このグリッドの詳細については、「[データベースの復元 &#40;[ファイル] ページ&#41;](restore-database-files-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-175">For more information about this grid, see [Restore Database &#40;Files Page&#41;](restore-database-files-page.md).</span></span>  
  
8.  <span data-ttu-id="5579c-176">**[オプション]** ページで必要に応じてオプションを調整します。</span><span class="sxs-lookup"><span data-stu-id="5579c-176">On the **Options** page, adjust the options if you want.</span></span> <span data-ttu-id="5579c-177">これらのオプションの詳細については、「[データベースの復元 &#40;[オプション] ページ&#41;](restore-database-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-177">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5579c-178">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="5579c-178">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a><span data-ttu-id="5579c-179">新しい場所にデータベースを復元し、必要に応じて名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="5579c-179">To restore a database to a new location, and optionally rename the database</span></span>  
  
1.  <span data-ttu-id="5579c-180">必要に応じて、復元するデータベースの完全バックアップを含んでいるバックアップ セット内のファイルの論理名と物理名を判断します。</span><span class="sxs-lookup"><span data-stu-id="5579c-180">Optionally, determine the logical and physical names of the files in the backup set that contains the full database backup that you want to restore.</span></span> <span data-ttu-id="5579c-181">このステートメントは、バックアップ セットに保存されているデータベースとログ ファイルのリストを返します。</span><span class="sxs-lookup"><span data-stu-id="5579c-181">This statement returns a list of the database and log files contained in the backup set.</span></span> <span data-ttu-id="5579c-182">基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5579c-182">The basic syntax is as follows:</span></span>  
  
     <span data-ttu-id="5579c-183">RESTORE FILELISTONLY FROM *<backup_device>* WITH FILE = *backup_set_file_number*</span><span class="sxs-lookup"><span data-stu-id="5579c-183">RESTORE FILELISTONLY FROM *<backup_device>* WITH FILE = *backup_set_file_number*</span></span>  
  
     <span data-ttu-id="5579c-184">この *backup_set_file_number* は、メディア セット内のバックアップの位置を示します。</span><span class="sxs-lookup"><span data-stu-id="5579c-184">Here, *backup_set_file_number* indicates the position of the backup in the media set.</span></span> <span data-ttu-id="5579c-185">バックアップ セットの位置は、 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) ステートメントを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="5579c-185">You can obtain the position of a backup set by using the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span> <span data-ttu-id="5579c-186">詳細については、「[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)」の「バックアップ セットの指定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-186">For more information, see "Specifying a Backup Set" in [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
     <span data-ttu-id="5579c-187">このステートメントは、多くの WITH オプションもサポートします。</span><span class="sxs-lookup"><span data-stu-id="5579c-187">This statement also supports a number of WITH options.</span></span> <span data-ttu-id="5579c-188">詳細については、[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-188">For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>  
  
2.  <span data-ttu-id="5579c-189">[RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントを使用し、データベースの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="5579c-189">Use the [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) statement to restore the full database backup.</span></span> <span data-ttu-id="5579c-190">既定で、データとログ ファイルが元の場所に復元されます。</span><span class="sxs-lookup"><span data-stu-id="5579c-190">By default, data and log files are restored to their original locations.</span></span> <span data-ttu-id="5579c-191">データベースを再配置するには、MOVE オプションを使用して、各データベース ファイルを再配置し、既存ファイルとの衝突が発生するのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="5579c-191">To relocate a database, use the MOVE option to relocate each of the database files and to avoid collisions with existing files.</span></span>  
  
     <span data-ttu-id="5579c-192">データベースを新しい場所と新しい名前に復元するための基本的な [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5579c-192">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for restoring the database to a new location and a new name is:</span></span>  
  
     <span data-ttu-id="5579c-193">RESTORE DATABASE *new_database_name*</span><span class="sxs-lookup"><span data-stu-id="5579c-193">RESTORE DATABASE *new_database_name*</span></span>  
  
     <span data-ttu-id="5579c-194">FROM *backup_device* [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="5579c-194">FROM *backup_device* [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="5579c-195">[ WITH</span><span class="sxs-lookup"><span data-stu-id="5579c-195">[ WITH</span></span>  
  
     <span data-ttu-id="5579c-196">{</span><span class="sxs-lookup"><span data-stu-id="5579c-196">{</span></span>  
  
     <span data-ttu-id="5579c-197">[ **RECOVERY** |NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="5579c-197">[ **RECOVERY** | NORECOVERY ]</span></span>  
  
     <span data-ttu-id="5579c-198">[ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]</span><span class="sxs-lookup"><span data-stu-id="5579c-198">[ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]</span></span>  
  
     <span data-ttu-id="5579c-199">[ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="5579c-199">[ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="5579c-200">}</span><span class="sxs-lookup"><span data-stu-id="5579c-200">}</span></span>  
  
     <span data-ttu-id="5579c-201">;</span><span class="sxs-lookup"><span data-stu-id="5579c-201">;</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5579c-202">データベースを別のディスクに再配置する準備をする場合は、容量が十分あるかどうか、および既存のファイルと衝突する可能性がないかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-202">When preparing to relocate a database on a different disk, you should verify that sufficient space is available and identify any potential collisions with existing files.</span></span> <span data-ttu-id="5579c-203">この作業は、 [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) ステートメントを使用して、RESTORE DATABASE ステートメントで使用するのと同じ MOVE パラメーターを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5579c-203">This involves using a [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) statement that specifies the same MOVE parameters that you plan to use in your RESTORE DATABASE statement.</span></span>  
  
     <span data-ttu-id="5579c-204">次の表で、データベースを新しい場所に復元するという点で、この RESTORE ステートメントの引数を説明します。</span><span class="sxs-lookup"><span data-stu-id="5579c-204">The following table describes arguments of this RESTORE statement in terms of restoring a database to a new location.</span></span> <span data-ttu-id="5579c-205">これらの引数の詳細については、「 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)データベースを新しい場所に復元し、必要に応じてデータベースの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5579c-205">For more information about these arguments, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
     <span data-ttu-id="5579c-206">*new_database_name*</span><span class="sxs-lookup"><span data-stu-id="5579c-206">*new_database_name*</span></span>  
     <span data-ttu-id="5579c-207">データベースの新しい名前。</span><span class="sxs-lookup"><span data-stu-id="5579c-207">The new name for the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5579c-208">異なるサーバー インスタンスにデータベースを復元している場合は、新しい名前ではなく元のデータベース名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5579c-208">If you are restoring the database to a different server instance, you can use the original database name instead of a new name.</span></span>  
  
     <span data-ttu-id="5579c-209">*backup_device* [ `,` ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="5579c-209">*backup_device* [ `,`...*n* ]</span></span>  
     <span data-ttu-id="5579c-210">データベース バックアップを復元する 1 ～ 64 個のバックアップ デバイスのコンマ区切りリストを指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-210">Specifies a comma-separated list of from 1 to 64 backup devices from which the database backup is to be restored.</span></span> <span data-ttu-id="5579c-211">物理バックアップ デバイスを指定したり、対応する論理バックアップ デバイス (定義されている場合) を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="5579c-211">You can specify a physical backup device, or you can specify a corresponding logical backup device, if defined.</span></span> <span data-ttu-id="5579c-212">物理バックアップ デバイスを指定するには、DISK オプションまたは TAPE オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="5579c-212">To specify a physical backup device, use the DISK or TAPE option:</span></span>  
  
     <span data-ttu-id="5579c-213">{ DISK | TAPE } `=` *physical_backup_device_name*</span><span class="sxs-lookup"><span data-stu-id="5579c-213">{ DISK | TAPE } `=`*physical_backup_device_name*</span></span>  
  
     <span data-ttu-id="5579c-214">詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-214">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
     <span data-ttu-id="5579c-215">{ **RECOVERY** | NORECOVERY }</span><span class="sxs-lookup"><span data-stu-id="5579c-215">{ **RECOVERY** | NORECOVERY }</span></span>  
     <span data-ttu-id="5579c-216">データベースで完全復旧モデルを使用している場合は、データベースの復元後にトランザクション ログ バックアップを適用しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5579c-216">If the database uses the full recovery model, you might need to apply transaction log backups after you restore the database.</span></span> <span data-ttu-id="5579c-217">この場合は、NORECOVERY オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-217">In this case, specify the NORECOVERY option.</span></span>  
  
     <span data-ttu-id="5579c-218">そうでない場合は、既定の RECOVERY オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="5579c-218">Otherwise, use the RECOVERY option, which is the default.</span></span>  
  
     <span data-ttu-id="5579c-219">FILE = { *backup_set_file_number* | @*backup_set_file_number* }</span><span class="sxs-lookup"><span data-stu-id="5579c-219">FILE = { *backup_set_file_number* | @*backup_set_file_number* }</span></span>  
     <span data-ttu-id="5579c-220">復元するバックアップ セットを特定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-220">Identifies the backup set to be restored.</span></span> <span data-ttu-id="5579c-221">たとえば、 *1* の **backup_set_file_number** は、バックアップ 目での最初のバックアップ セットを示し、2 の *backup_set_file_number* は **2** 番目のバックアップ セットを示します。</span><span class="sxs-lookup"><span data-stu-id="5579c-221">For example, a *backup_set_file_number* of **1** indicates the first backup set on the backup medium and a *backup_set_file_number* of **2** indicates the second backup set.</span></span> <span data-ttu-id="5579c-222">バックアップ セットの *backup_set_file_number* を取得するには、 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5579c-222">You can obtain the *backup_set_file_number* of a backup set by using the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="5579c-223">このオプションを指定しない場合、既定ではバックアップ デバイスの 1 番目のバックアップ セットを使用します。</span><span class="sxs-lookup"><span data-stu-id="5579c-223">When this option is not specified, the default is to use the first backup set on the backup device.</span></span>  
  
     <span data-ttu-id="5579c-224">詳細については、「[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)」の「バックアップ セットの指定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-224">For more information, see "Specifying a Backup Set," in [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
     <span data-ttu-id="5579c-225">' \*\* *`logical_file_name_in_backup`* '\*\* を **' *`operating_system_file_name`* '** に移動 `,` します。*n* ]</span><span class="sxs-lookup"><span data-stu-id="5579c-225">MOVE **'*`logical_file_name_in_backup`*'** TO **'*`operating_system_file_name`*'** [ `,`...*n* ]</span></span>  
     <span data-ttu-id="5579c-226">*logical_file_name_in_backup* で指定されるデータまたはログ ファイルが、 *operating_system_file_name*で指定される位置に復元されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-226">Specifies that the data or log file specified by *logical_file_name_in_backup* is to be restored to the location specified by *operating_system_file_name*.</span></span> <span data-ttu-id="5579c-227">バックアップ セットから新しい位置に復元する論理ファイルごとに、MOVE ステートメントを指定してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-227">Specify a MOVE statement for every logical file you want to restore from the backup set to a new location.</span></span>  
  
    |<span data-ttu-id="5579c-228">オプション</span><span class="sxs-lookup"><span data-stu-id="5579c-228">Option</span></span>|<span data-ttu-id="5579c-229">説明</span><span class="sxs-lookup"><span data-stu-id="5579c-229">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="5579c-230">*logical_file_name_in_backup*</span><span class="sxs-lookup"><span data-stu-id="5579c-230">*logical_file_name_in_backup*</span></span>|<span data-ttu-id="5579c-231">バックアップ セット内のデータまたはログ ファイルの論理名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-231">Specifies the logical name of a data or log file in the backup set.</span></span> <span data-ttu-id="5579c-232">バックアップ セット内のデータ ファイルまたはログ ファイルの論理ファイル名は、バックアップ セットが作成されたときのデータベース内における論理名と同じです。</span><span class="sxs-lookup"><span data-stu-id="5579c-232">The logical file name of a data or log file in a backup set matches its logical name in the database when the backup set was created.</span></span><br /><br /> <span data-ttu-id="5579c-233">注:バックアップ セットに含まれる論理ファイルの一覧を取得するには、[RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="5579c-233">Note: To obtain a list of the logical files from the backup set, use [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>|  
    |<span data-ttu-id="5579c-234">*operating_system_file_name*</span><span class="sxs-lookup"><span data-stu-id="5579c-234">*operating_system_file_name*</span></span>|<span data-ttu-id="5579c-235">*logical_file_name_in_backup*で指定したファイルの新しい場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-235">Specifies a new location for the file specified by *logical_file_name_in_backup*.</span></span> <span data-ttu-id="5579c-236">ファイルはこの場所に復元されます。</span><span class="sxs-lookup"><span data-stu-id="5579c-236">The file will be restored to this location.</span></span><br /><br /> <span data-ttu-id="5579c-237">必要に応じて、 *operating_system_file_name* に復元するファイルの新しいファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5579c-237">Optionally, *operating_system_file_name* specifies a new file name for the restored file.</span></span> <span data-ttu-id="5579c-238">これは、同じサーバー インスタンスで既存のデータベースのコピーを作成する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="5579c-238">This is necessary if you are creating a copy of an existing database on the same server instance.</span></span>|  
    |<span data-ttu-id="5579c-239">*n*</span><span class="sxs-lookup"><span data-stu-id="5579c-239">*n*</span></span>|<span data-ttu-id="5579c-240">追加の MOVE ステートメントを指定できることを示すプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="5579c-240">Is a placeholder indicating that you can specify additional MOVE statements.</span></span>|  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="5579c-241">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5579c-241">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="5579c-242">この例では、 `MyAdvWorks` サンプル データベースのバックアップを復元して、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] という名前の新しいデータベースを作成します。このデータベースには、2 つのファイル、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data と [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5579c-242">This example creates a new database named `MyAdvWorks` by restoring a backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database, which includes two files: [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log.</span></span> <span data-ttu-id="5579c-243">このデータベースは、単純復旧モデルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="5579c-243">This database uses the simple recovery model.</span></span> <span data-ttu-id="5579c-244">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースはサーバー インスタンスに既に存在するため、バックアップ内のファイルを新しい場所に復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5579c-244">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database already exists on the server instance, so the files in the backup must be restored to a new location.</span></span> <span data-ttu-id="5579c-245">RESTORE FILELISTONLY ステートメントは、復元するデータベース内のファイル数と名前を判断するために使用します。</span><span class="sxs-lookup"><span data-stu-id="5579c-245">The RESTORE FILELISTONLY statement is used to determine the number and names of the files in the database being restored.</span></span> <span data-ttu-id="5579c-246">データベース バックアップは、バックアップ デバイスの 1 番目のバックアップ セットです。</span><span class="sxs-lookup"><span data-stu-id="5579c-246">The database backup is the first backup set on the backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5579c-247">特定日時への復元を含む、トランザクション ログのバックアップと復元の例では、次の `MyAdvWorks_FullRM` の例と同様、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] から作成した `MyAdvWorks` データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="5579c-247">The examples of backing up and restoring the transaction log, including point-in-time restores, use the `MyAdvWorks_FullRM` database that is created from [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] just like the following `MyAdvWorks` example.</span></span> <span data-ttu-id="5579c-248">ただし、作成された `MyAdvWorks_FullRM` データベースは、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使って、完全復旧モデルを使用するように変更する必要があります:ALTER DATABASE <データベース名> SET RECOVERY FULL。</span><span class="sxs-lookup"><span data-stu-id="5579c-248">However, the resulting `MyAdvWorks_FullRM` database must be changed to use the full recovery model by using the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement: ALTER DATABASE <database_name> SET RECOVERY FULL.</span></span>  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
-- AdventureWorks2012_Backup is the name of the backup device.  
RESTORE FILELISTONLY  
   FROM AdventureWorks2012_Backup;  
-- Restore the files for MyAdvWorks.  
RESTORE DATABASE MyAdvWorks  
   FROM AdventureWorks2012_Backup  
   WITH RECOVERY,  
   MOVE 'AdventureWorks2012_Data' TO 'D:\MyData\MyAdvWorks_Data.mdf',   
   MOVE 'AdventureWorks2012_Log' TO 'F:\MyLog\MyAdvWorks_Log.ldf';  
GO  
  
```  
  
 <span data-ttu-id="5579c-249">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの完全データベース バックアップを作成する方法の例については、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5579c-249">For an example of how to create a full database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5579c-250">関連タスク</span><span class="sxs-lookup"><span data-stu-id="5579c-250">Related Tasks</span></span>  
  
-   [<span data-ttu-id="5579c-251">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5579c-251">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="5579c-252">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5579c-252">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="5579c-253">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5579c-253">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="5579c-254">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5579c-254">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="5579c-255">参照</span><span class="sxs-lookup"><span data-stu-id="5579c-255">See Also</span></span>  
 <span data-ttu-id="5579c-256">[データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="5579c-256">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 <span data-ttu-id="5579c-257">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5579c-257">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="5579c-258">バックアップと復元によるデータベースのコピー</span><span class="sxs-lookup"><span data-stu-id="5579c-258">Copy Databases with Backup and Restore</span></span>](../databases/copy-databases-with-backup-and-restore.md)  
  
  
