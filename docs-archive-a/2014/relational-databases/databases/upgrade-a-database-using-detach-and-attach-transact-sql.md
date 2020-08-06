---
title: デタッチとアタッチを使用したデータベースのアップグレード (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database attaching [SQL Server]
- upgrading databases
- database upgrades [SQL Server]
- database detaching [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 99f66ed9-3a75-4e38-ad7d-6c27cc3529a9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d430825fd862ff49b867790f366200a524df3c1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634556"
---
# <a name="upgrade-a-database-using-detach-and-attach-transact-sql"></a><span data-ttu-id="260aa-102">デタッチとアタッチを使用したデータベースのアップグレード (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="260aa-102">Upgrade a Database Using Detach and Attach (Transact-SQL)</span></span>
  <span data-ttu-id="260aa-103">このトピックでは、デタッチ操作とアタッチ操作を使用し、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のデータベースをアップグレードする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="260aa-103">This topic describes how to use detach and attach operations to upgrade a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="260aa-104">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアタッチした後は、データベースが直ちに使用可能となり、自動的にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="260aa-104">After being attached to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is available immediately and is automatically upgraded.</span></span>  
  
 <span data-ttu-id="260aa-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="260aa-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="260aa-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="260aa-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="260aa-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="260aa-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="260aa-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="260aa-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="260aa-109">**SQL Server データベースをアップグレードするには:**</span><span class="sxs-lookup"><span data-stu-id="260aa-109">**To Upgrade a SQL Server Database:**</span></span>  
  
     [<span data-ttu-id="260aa-110">デタッチ操作とアタッチ操作の使用</span><span class="sxs-lookup"><span data-stu-id="260aa-110">Using detach and attach operations</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="260aa-111">**補足情報:**  [SQL Server データベースのアップグレード後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="260aa-111">**Follow Up:**  [After Upgrading a SQL Server Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="260aa-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="260aa-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="260aa-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="260aa-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="260aa-114">システム データベースをアタッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="260aa-114">The system databases cannot be attached.</span></span>  
  
-   <span data-ttu-id="260aa-115">アタッチとデタッチを行うと、 **cross db ownership chaining** オプションが 0 に設定され、複数データベースの組み合わせ所有権が無効になります。</span><span class="sxs-lookup"><span data-stu-id="260aa-115">Attach and detach disable cross-database ownership chaining for the database by setting its **cross db ownership chaining** option to 0.</span></span> <span data-ttu-id="260aa-116">チェーンを有効にする方法については、「 [cross db ownership chaining サーバー構成オプション](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-116">For information about enabling chaining, see [cross db ownership chaining Server Configuration Option](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md).</span></span>  
  
-   <span data-ttu-id="260aa-117">レプリケートされたデータベースをアタッチする際に、そのデータベースがデタッチではなくコピーされたものである場合は、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-117">When attaching a replicated database that was copied instead of detached:</span></span>  
  
    -   <span data-ttu-id="260aa-118">同じサーバー インスタンスのアップグレードされたバージョンにデータベースをアタッチする場合は、アタッチ操作が完了した後、 **sp_vupgrade_replication** を実行してレプリケーションをアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="260aa-118">If you attach the database to an upgraded version of the same server instance, you must execute **sp_vupgrade_replication** to upgrade replication after the attach operation finishes.</span></span> <span data-ttu-id="260aa-119">詳細については、「[sp_vupgrade_replication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-119">For more information, see [sp_vupgrade_replication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="260aa-120">バージョンに関係なく別のサーバー インスタンスにデータベースをアタッチする場合は、アタッチ操作が完了した後、 **sp_removedbreplication** を実行してレプリケーションを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="260aa-120">If you attach the database to a different server instance (regardless of version), you must execute **sp_removedbreplication** to remove replication after the attach operation finishes.</span></span> <span data-ttu-id="260aa-121">詳細については、「[sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-121">For more information, see [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="260aa-122">推奨事項</span><span class="sxs-lookup"><span data-stu-id="260aa-122">Recommendations</span></span>  
 <span data-ttu-id="260aa-123">不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="260aa-123">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="260aa-124">こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="260aa-124">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="260aa-125">不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。</span><span class="sxs-lookup"><span data-stu-id="260aa-125">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="to-upgrade-a-database-by-using-detach-and-attach"></a><a name="SSMSProcedure"></a> <span data-ttu-id="260aa-126">デタッチとアタッチを使用してデータベースをアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="260aa-126">To Upgrade a Database by Using Detach and Attach</span></span>  
  
1.  <span data-ttu-id="260aa-127">データベースをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="260aa-127">Detach the database.</span></span> <span data-ttu-id="260aa-128">詳細については、「 [データベースのデタッチ](detach-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-128">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
2.  <span data-ttu-id="260aa-129">必要に応じて、デタッチされたデータベース ファイルとログ ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="260aa-129">Optionally, move the detached database file or files and the log file or files.</span></span>  
  
     <span data-ttu-id="260aa-130">新しいログ ファイルを作成する場合であっても、ログ ファイルをデータ ファイルと一緒に移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="260aa-130">You should move the log files along with the data files, even if you intend to create new log files.</span></span> <span data-ttu-id="260aa-131">場合によっては、データベースの再アタッチに既存のログ ファイルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="260aa-131">In some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="260aa-132">したがって、デタッチしたログ ファイルを使わずにデータベースを正常にアタッチできるまで、デタッチしたログ ファイルは必ずすべて保管しておいてください。</span><span class="sxs-lookup"><span data-stu-id="260aa-132">Therefore, always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="260aa-133">ログ ファイルを指定せずにデータベースのインポートを試みると、アタッチ操作は元の場所でログ ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="260aa-133">If you try to attach the database without specifying the log file, the attach operation will look for the log file in its original location.</span></span> <span data-ttu-id="260aa-134">元の場所にログの元のコピーが依然として存在する場合は、そのコピーがアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="260aa-134">If the original copy of the log still exists in that location, that copy is attached.</span></span> <span data-ttu-id="260aa-135">元のログ ファイルが使用されないようにするには、新しいログ ファイルのパスを指定するか、ログ ファイルの元のコピーを (新しい場所にコピーした後で) 削除します。</span><span class="sxs-lookup"><span data-stu-id="260aa-135">To avoid using the original log file, either specify the path of the new log file or remove the original copy of the log file (after copying it to the new location).</span></span>  
  
3.  <span data-ttu-id="260aa-136">コピーしたファイルを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="260aa-136">Attach the copied files to the instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="260aa-137">詳細については、「 [Attach a Database](attach-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-137">For more information, see [Attach a Database](attach-a-database.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="260aa-138">例</span><span class="sxs-lookup"><span data-stu-id="260aa-138">Example</span></span>  
 <span data-ttu-id="260aa-139">次の例では、データベースのコピーを以前のバージョンの SQL Server からアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="260aa-139">The following example upgrades a copy of a database from an earlier version of SQL Server.</span></span> <span data-ttu-id="260aa-140">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、アタッチするサーバー インスタンスに接続されたクエリ エディター ウィンドウで実行しています。</span><span class="sxs-lookup"><span data-stu-id="260aa-140">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are executed in a Query Editor window that is connected to the server instance to which is attached.</span></span>  
  
1.  <span data-ttu-id="260aa-141">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行してデータベースをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="260aa-141">Detach the database by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'MyDatabase';  
    GO  
    ```  
  
2.  <span data-ttu-id="260aa-142">任意の方法で、データ ファイルとログ ファイルを新しい場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="260aa-142">Using the method of your choice, copy the data and log files to the new location.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="260aa-143">実稼動データベースの場合は、データベースとトランザクション ログを別のディスクに配置します。</span><span class="sxs-lookup"><span data-stu-id="260aa-143">For a production database, place the database and transaction log on separate disks.</span></span>  
  
     <span data-ttu-id="260aa-144">ファイルをネットワーク経由でリモート コンピューターのディスクにコピーするには、そのリモート コンピューターの UNC (Universal Naming Convention) 名を使用します。</span><span class="sxs-lookup"><span data-stu-id="260aa-144">To copy files over the network to a disk on a remote computer, use the universal naming convention (UNC) name of the remote location.</span></span> <span data-ttu-id="260aa-145">UNC 名の形式は、 **\\\\** _Servername_ **\\** _Sharename_ **\\** _Path_ **\\** _Filename_です。</span><span class="sxs-lookup"><span data-stu-id="260aa-145">A UNC name takes the form **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="260aa-146">ローカル ハード ディスクにファイルを書き込む場合と同様、リモート ディスクでのファイルの読み取りや書き込みに必要な適切な権限が、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスで使用するユーザー アカウントに許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="260aa-146">As with writing files to the local hard disk, the appropriate permissions that are required to read or write to a file on the remote disk must be granted to the user account used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="260aa-147">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して、移動したデータベースとログをアタッチします (ログのアタッチは省略できます)。</span><span class="sxs-lookup"><span data-stu-id="260aa-147">Attach the moved database and, optionally, its log by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyDatabase   
        ON (FILENAME = 'C:\MySQLServer\MyDatabase.mdf'),  
        (FILENAME = 'C:\MySQLServer\Database.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     <span data-ttu-id="260aa-148">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、新しくアタッチされたデータベースはオブジェクト エクスプローラーにすぐに表示されません。</span><span class="sxs-lookup"><span data-stu-id="260aa-148">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], a newly attached database is not immediately visible in Object Explorer.</span></span> <span data-ttu-id="260aa-149">このデータベースを表示するには、オブジェクト エクスプローラーで、 **[表示]** をクリックし、 **[最新の情報に更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="260aa-149">To view the database, in Object Explorer, click **View,** and then **Refresh**.</span></span> <span data-ttu-id="260aa-150">オブジェクト エクスプローラーの **[データベース]** ノードを展開すると、データベースの一覧に新しくアタッチされたデータベースが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="260aa-150">When the **Databases** node is expanded in Object Explorer, the newly attached database now appears in the list of databases.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a><span data-ttu-id="260aa-151">補足情報: SQL Server データベースのアップグレード後</span><span class="sxs-lookup"><span data-stu-id="260aa-151">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="260aa-152">データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、 **upgrade_option** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。</span><span class="sxs-lookup"><span data-stu-id="260aa-152">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **upgrade_option** server property.</span></span> <span data-ttu-id="260aa-153">アップグレード オプションがインポート (**upgrade_option** = 2) または再構築 (**upgrade_option** = 0) に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="260aa-153">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="260aa-154">インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="260aa-154">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="260aa-155">また、アップグレード オプションがインポートに設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="260aa-155">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="260aa-156">**upgrade_option** サーバー プロパティの設定を変更するには、 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="260aa-156">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
### <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="260aa-157">アップグレード後のデータベース互換性レベル</span><span class="sxs-lookup"><span data-stu-id="260aa-157">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="260aa-158">アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。</span><span class="sxs-lookup"><span data-stu-id="260aa-158">If the compatibility level of a user database is 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="260aa-159">アップグレードされたデータベースの互換性レベルが 90 の場合、互換性レベルは 100 に設定されます。これは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でサポートされている下限の互換性レベルです。</span><span class="sxs-lookup"><span data-stu-id="260aa-159">If the compatibility level is 90 before upgrade in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="260aa-160">詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-160">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
### <a name="managing-metadata-on-the-upgraded-server-instance"></a><span data-ttu-id="260aa-161">アップグレードされたサーバー インスタンスでのメタデータの管理</span><span class="sxs-lookup"><span data-stu-id="260aa-161">Managing Metadata on the Upgraded Server Instance</span></span>  
 <span data-ttu-id="260aa-162">データベースを別のサーバー インスタンスにアタッチするときは、ユーザーおよびアプリケーションに一貫した使用環境を提供するために、アタッチ先のサーバー インスタンスで、ログイン、ジョブ、権限などのデータベースのメタデータの一部またはすべてを作成し直す必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="260aa-162">When you attach a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins, jobs, and permissions, on the other server instance.</span></span> <span data-ttu-id="260aa-163">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-163">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
### <a name="service-master-key-and-database-master-key-encryption-changes-from-3des-to-aes"></a><span data-ttu-id="260aa-164">3DES から AES へのサービス マスター キーとデータベース マスター キーの暗号化の変更</span><span class="sxs-lookup"><span data-stu-id="260aa-164">Service Master Key and Database Master Key Encryption changes from 3DES to AES</span></span>  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="260aa-165">以降のバージョンは、AES 暗号化アルゴリズムを使用してサービス マスター キー (SMK) とデータベース マスター キー (DMK) を保護します。</span><span class="sxs-lookup"><span data-stu-id="260aa-165">and higher versions uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK).</span></span> <span data-ttu-id="260aa-166">AES は、以前のバージョンで使用されていた 3DES よりも新しい暗号化アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="260aa-166">AES is a newer encryption algorithm than 3DES used in earlier versions.</span></span> <span data-ttu-id="260aa-167">データベースが最初に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の新しいインスタンスにアタッチまたは復元されるとき、データベース マスター キー (サービス マスター キーにより暗号化されたもの) のコピーはまだサーバーに格納されていません。</span><span class="sxs-lookup"><span data-stu-id="260aa-167">When a database is first attached or restored to a new instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a copy of the database master key (encrypted by the service master key) is not yet stored in the server.</span></span> <span data-ttu-id="260aa-168">使用する必要があります、 `OPEN MASTER KEY` ステートメントをデータベース マスター_キー (DMK) の暗号化を解除します。</span><span class="sxs-lookup"><span data-stu-id="260aa-168">You must use the `OPEN MASTER KEY` statement to decrypt the database master key (DMK).</span></span> <span data-ttu-id="260aa-169">DMK の暗号化が解除されると、`ALTER MASTER KEY REGENERATE` ステートメントを使用して、サービス マスター キー (SMK) で暗号化された DMK のコピーをサーバーに提供することにより、将来、自動的に暗号化解除することも可能となります。</span><span class="sxs-lookup"><span data-stu-id="260aa-169">Once the DMK has been decrypted, you have the option of enabling automatic decryption in the future by using the `ALTER MASTER KEY REGENERATE` statement to provision the server with a copy of the DMK, encrypted with the service master key (SMK).</span></span> <span data-ttu-id="260aa-170">データベースを以前のバージョンからアップグレードした場合、新しい AES アルゴリズムを使用するように DMK を再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="260aa-170">When a database has been upgraded from an earlier version, the DMK should be regenerated to use the newer AES algorithm.</span></span> <span data-ttu-id="260aa-171">DMK を再作成する方法については、「[ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260aa-171">For more information about regenerating the DMK, see [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span> <span data-ttu-id="260aa-172">DMK キーを再作成して AES にアップグレードするのに必要な時間は、DMK によって保護されているオブジェクトの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="260aa-172">The time required to regenerate the DMK key to upgrade to AES depends upon the number of objects protected by the DMK.</span></span> <span data-ttu-id="260aa-173">DMK キーを再作成して AES にアップグレードする作業は、1 回限りで済み、今後のキー ローテーション方法には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="260aa-173">Regenerating the DMK key to upgrade to AES is only necessary once, and has no impact on future regenerations as part of a key rotation strategy.</span></span>  
  
  
