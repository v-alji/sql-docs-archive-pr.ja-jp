---
title: ユーザー データベースの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- editions [SQL Server], moving databases between
- moving full-text catalogs
- scheduled disk maintenace [SQL Server]
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- moving user databases
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: ad9a4e92-13fb-457d-996a-66ffc2d55b79
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6c2b82c3bec13c82aa30aebd175ef78f8136ee04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640062"
---
# <a name="move-user-databases"></a><span data-ttu-id="ed52b-102">ユーザー データベースの移動</span><span class="sxs-lookup"><span data-stu-id="ed52b-102">Move User Databases</span></span>
  <span data-ttu-id="ed52b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) ステートメントの FILENAME 句で新しいファイルの場所を指定することで、ユーザー データベースのデータ ファイル、ログ ファイル、およびフルテキスト カタログ ファイルを新しい場所に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="ed52b-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can move the data, log, and full-text catalog files of a user database to a new location by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="ed52b-104">この方法は、同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス内でデータベース ファイルを移動する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed52b-104">This method applies to moving database files within the same instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ed52b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスや、別のサーバーにデータベースを移動する場合は、 [バックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md) 操作か [デタッチ操作とアタッチ操作](move-a-database-using-detach-and-attach-transact-sql.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-105">To move a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to another server, use [backup and restore](../backup-restore/back-up-and-restore-of-sql-server-databases.md) or [detach and attach operations](move-a-database-using-detach-and-attach-transact-sql.md).</span></span>  
  
## <a name="considerations"></a><span data-ttu-id="ed52b-106">考慮事項</span><span class="sxs-lookup"><span data-stu-id="ed52b-106">Considerations</span></span>  
 <span data-ttu-id="ed52b-107">データベースを別のサーバー インスタンスに移動するときは、ユーザーおよびアプリケーションに一貫した使用環境を提供するために、データベースのメタデータの一部またはすべてを作成し直す必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ed52b-107">When you move a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all the metadata for the database.</span></span> <span data-ttu-id="ed52b-108">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed52b-108">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
 <span data-ttu-id="ed52b-109">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の一部の機能は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]がデータベース ファイルに情報を格納する方法を変更します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-109">Some features of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] change the way that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores information in the database files.</span></span> <span data-ttu-id="ed52b-110">これらの機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定のエディションでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed52b-110">These features are restricted to specific editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ed52b-111">これらの機能を備えたデータベースを、それらをサポートしない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエディションに移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="ed52b-111">A database that contains these features cannot be moved to an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that does not support them.</span></span> <span data-ttu-id="ed52b-112">現在のデータベースで有効なエディション固有の機能をすべて一覧表示するには、sys.dm_db_persisted_sku_features 動的管理ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-112">Use the sys.dm_db_persisted_sku_features dynamic management view to list all edition-specific features that are enabled in the current database.</span></span>  
  
 <span data-ttu-id="ed52b-113">このトピックの手順では、データベース ファイルの論理名が必要です。</span><span class="sxs-lookup"><span data-stu-id="ed52b-113">The procedures in this topic require the logical name of the database files.</span></span> <span data-ttu-id="ed52b-114">論理名を取得するには、 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) カタログ ビューで name 列に対するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-114">To obtain the name, query the name column in the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="ed52b-115">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]以降では、フルテキスト カタログは、ファイル システムに格納されるのではなく、データベースに統合されています。</span><span class="sxs-lookup"><span data-stu-id="ed52b-115">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], full-text catalogs are integrated into the database rather than being stored in the file system.</span></span> <span data-ttu-id="ed52b-116">フルテキスト カタログは、データベースの移動時に自動的に移動されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ed52b-116">The full-text catalogs now move automatically when you move a database.</span></span>  
  
## <a name="planned-relocation-procedure"></a><span data-ttu-id="ed52b-117">計画に従った再配置の手順</span><span class="sxs-lookup"><span data-stu-id="ed52b-117">Planned Relocation Procedure</span></span>  
 <span data-ttu-id="ed52b-118">計画に従った再配置の一環としてデータ ファイルやログ ファイルを移動するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-118">To move a data or log file as part of a planned relocation, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ed52b-119">次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-119">Run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name SET OFFLINE;  
    ```  
  
2.  <span data-ttu-id="ed52b-120">ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-120">Move the file or files to the new location.</span></span>  
  
3.  <span data-ttu-id="ed52b-121">移動したそれぞれのファイルに対して、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-121">For each file moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name, FILENAME = 'new_path\os_file_name' );  
    ```  
  
4.  <span data-ttu-id="ed52b-122">次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-122">Run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name SET ONLINE;  
    ```  
  
5.  <span data-ttu-id="ed52b-123">次のクエリを実行して、ファイルが変更されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-123">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="relocation-for-scheduled-disk-maintenance"></a><span data-ttu-id="ed52b-124">スケジュールされたディスク メンテナンスでの再配置</span><span class="sxs-lookup"><span data-stu-id="ed52b-124">Relocation for Scheduled Disk Maintenance</span></span>  
 <span data-ttu-id="ed52b-125">スケジュールされたディスク メンテナンスの一環としてファイルを再配置するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-125">To relocate a file as part of a scheduled disk maintenance process, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ed52b-126">移動対象のそれぞれのファイルに対して、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-126">For each file to be moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
2.  <span data-ttu-id="ed52b-127">メンテナンスを行うため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを停止するか、システムをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="ed52b-127">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or shut down the system to perform maintenance.</span></span> <span data-ttu-id="ed52b-128">詳細については、「 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed52b-128">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="ed52b-129">ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-129">Move the file or files to the new location.</span></span>  
  
4.  <span data-ttu-id="ed52b-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスまたはサーバーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-130">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the server.</span></span> <span data-ttu-id="ed52b-131">詳細については、「 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed52b-131">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)</span></span>  
  
5.  <span data-ttu-id="ed52b-132">次のクエリを実行して、ファイルが変更されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-132">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="failure-recovery-procedure"></a><span data-ttu-id="ed52b-133">障害復旧の手順</span><span class="sxs-lookup"><span data-stu-id="ed52b-133">Failure Recovery Procedure</span></span>  
 <span data-ttu-id="ed52b-134">ハードウェア障害が原因でファイルを移動する必要がある場合、次の手順に従って別の場所にファイルを再配置します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-134">If a file must be moved because of a hardware failure, use the following steps to relocate the file to a new location.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ed52b-135">データベースを起動できないとき、つまり、データベースが問題のあるモードか復旧できない状態にある場合、ファイルを移動できるのは、sysadmin 固定ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="ed52b-135">If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.</span></span>  
  
1.  <span data-ttu-id="ed52b-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動していたら停止します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-136">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if it is started.</span></span>  
  
2.  <span data-ttu-id="ed52b-137">コマンド プロンプトで次のいずれかのコマンドを入力し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを master のみを復旧するモードで開始します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-137">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in master-only recovery mode by entering one of the following commands at the command prompt.</span></span>  
  
    -   <span data-ttu-id="ed52b-138">既定 (MSSQLSERVER) のインスタンスの場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-138">For the default (MSSQLSERVER) instance, run the following command.</span></span>  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   <span data-ttu-id="ed52b-139">名前付きインスタンスの場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-139">For a named instance, run the following command.</span></span>  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     <span data-ttu-id="ed52b-140">詳細については、「 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed52b-140">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="ed52b-141">移動対象の各ファイルに対して、 **sqlcmd** コマンドか [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-141">For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
     <span data-ttu-id="ed52b-142">**sqlcmd** ユーティリティの使用方法については、「 [sqlcmd ユーティリティの使用](../scripting/sqlcmd-use-the-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed52b-142">For more information about how to use the **sqlcmd** utility, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
4.  <span data-ttu-id="ed52b-143">**sqlcmd** ユーティリティまたは [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を終了します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-143">Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
5.  <span data-ttu-id="ed52b-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-144">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
6.  <span data-ttu-id="ed52b-145">ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-145">Move the file or files to the new location.</span></span>  
  
7.  <span data-ttu-id="ed52b-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを開始します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-146">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ed52b-147">たとえば、 `NET START MSSQLSERVER`を実行します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-147">For example, run: `NET START MSSQLSERVER`.</span></span>  
  
8.  <span data-ttu-id="ed52b-148">次のクエリを実行して、ファイルが変更されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-148">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="examples"></a><span data-ttu-id="ed52b-149">例</span><span class="sxs-lookup"><span data-stu-id="ed52b-149">Examples</span></span>  
 <span data-ttu-id="ed52b-150">次の例では、計画に従った再配置の一環として、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] のログ ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="ed52b-150">The following example moves the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] log file to a new location as part of a planned relocation.</span></span>  
  
```  
USE master;  
GO  
-- Return the logical file name.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
GO  
ALTER DATABASE AdventureWorks2012 SET OFFLINE;  
GO  
-- Physically move the file to a new location.  
-- In the following statement, modify the path specified in FILENAME to  
-- the new location of the file on your server.  
ALTER DATABASE AdventureWorks2012   
    MODIFY FILE ( NAME = AdventureWorks2012_Log,   
                  FILENAME = 'C:\NewLoc\AdventureWorks2012_Log.ldf');  
GO  
ALTER DATABASE AdventureWorks2012 SET ONLINE;  
GO  
--Verify the new location.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed52b-151">参照</span><span class="sxs-lookup"><span data-stu-id="ed52b-151">See Also</span></span>  
 <span data-ttu-id="ed52b-152">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed52b-152">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="ed52b-153">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed52b-153">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="ed52b-154">[データベースのデタッチとアタッチ &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ed52b-154">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="ed52b-155">[システム データベースの移動](system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="ed52b-155">[Move System Databases](system-databases.md) </span></span>  
 <span data-ttu-id="ed52b-156">[データベース ファイルの移動](move-database-files.md) </span><span class="sxs-lookup"><span data-stu-id="ed52b-156">[Move Database Files](move-database-files.md) </span></span>  
 <span data-ttu-id="ed52b-157">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed52b-157">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="ed52b-158">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed52b-158">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="ed52b-159">データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動</span><span class="sxs-lookup"><span data-stu-id="ed52b-159">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
