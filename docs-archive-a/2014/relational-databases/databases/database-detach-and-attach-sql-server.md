---
title: データベースのデタッチとアタッチ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [SQL Server], detaching
- detach database [SQL Server]
- databases [SQL Server], attaching
- removing databases
- transaction logs [SQL Server], detaching
- databases [SQL Server], removing
- restoring [SQL Server], attached databases
- transaction logs [SQL Server], attaching
- differential backups, after detaching
- moving databases
- attach database [SQL Server]
- detaching databases [SQL Server]
- differential base [SQL Server]
- attaching databases [SQL Server]
- databases [SQL Server], moving
ms.assetid: d0de0639-bc54-464e-98b1-6af22a27eb86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 54eeeec995e390b71ce8871b680c26138fc88783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640079"
---
# <a name="database-detach-and-attach-sql-server"></a><span data-ttu-id="eafc9-102">データベースのデタッチとアタッチ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eafc9-102">Database Detach and Attach (SQL Server)</span></span>
  <span data-ttu-id="eafc9-103">データベースのデータ ファイルおよびトランザクション ログ ファイルは、デタッチして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の同一または別のインスタンスに再度アタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-103">The data and transaction log files of a database can be detached and then reattached to the same or another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eafc9-104">同一コンピューターの別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにデータベースを変更したり、データベースを移動したりする場合、データベースをデタッチしてアタッチする操作が便利です。</span><span class="sxs-lookup"><span data-stu-id="eafc9-104">Detaching and attaching a database is useful if you want to change the database to a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer or to move the database.</span></span>  
  
 <span data-ttu-id="eafc9-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のディスク上のストレージ形式は、64 ビット環境でも 32 ビット環境でも同じです。</span><span class="sxs-lookup"><span data-stu-id="eafc9-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="eafc9-106">このため、アタッチは 32 ビット環境と 64 ビット環境の間でも機能します。</span><span class="sxs-lookup"><span data-stu-id="eafc9-106">Therefore, attach works across 32-bit and 64-bit environments.</span></span>  <span data-ttu-id="eafc9-107">一方の環境で実行中のサーバー インスタンスからデタッチしたデータベースは、他方の環境で実行中のサーバー インスタンスにアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-107">A database detached from a server instance running in one environment can be attached on a server instance that runs in another environment.</span></span>  
  
  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eafc9-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="eafc9-108">Security</span></span>  
 <span data-ttu-id="eafc9-109">ファイル アクセス許可は、データベースのデタッチやアタッチなど、さまざまなデータベース操作中に設定されます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-109">File access permissions are set during a number of database operations, including detaching or attaching a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eafc9-110">不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="eafc9-110">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="eafc9-111">こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-111">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="eafc9-112">不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-112">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="detaching-a-database"></a><a name="DetachDb"></a> <span data-ttu-id="eafc9-113">データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="eafc9-113">Detaching a Database</span></span>  
 <span data-ttu-id="eafc9-114">データベースはデタッチすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスからは削除されますが、データ ファイルおよびトランザクション ログ ファイル内ではそのまま残ります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-114">Detaching a database removes it from the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but leaves the database intact within its data files and transaction log files.</span></span> <span data-ttu-id="eafc9-115">これらのデータ ファイルとトランザクション ログ ファイルを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の任意のインスタンスにデータベースをアタッチできます。その際、そのデータベースをデタッチした元のサーバーにアタッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-115">These files can then be used to attach the database to any instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], including the server from which the database was detached.</span></span>  
  
 <span data-ttu-id="eafc9-116">次の条件に 1 つでも該当する場合、データベースをデタッチできません。</span><span class="sxs-lookup"><span data-stu-id="eafc9-116">You cannot detach a database if any of the following are true:</span></span>  
  
-   <span data-ttu-id="eafc9-117">データベースがレプリケートおよびパブリッシュされている。</span><span class="sxs-lookup"><span data-stu-id="eafc9-117">The database is replicated and published.</span></span> <span data-ttu-id="eafc9-118">レプリケートされている場合、データベースをパブリッシュしてはいけません。</span><span class="sxs-lookup"><span data-stu-id="eafc9-118">If replicated, the database must be unpublished.</span></span> <span data-ttu-id="eafc9-119">データベースをデタッチする前に、 [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)を実行してパブリッシングを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-119">Before you can detach it, you must disable publishing by running [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eafc9-120">**sp_replicationdboption**を使用できない場合、 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)を実行してレプリケーションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-120">If you cannot use **sp_replicationdboption**, you can remove replication by running [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql).</span></span>  
  
-   <span data-ttu-id="eafc9-121">データベースに、データベース スナップショットが存在する。</span><span class="sxs-lookup"><span data-stu-id="eafc9-121">A database snapshot exists on the database.</span></span>  
  
     <span data-ttu-id="eafc9-122">データベースをデタッチするには、すべてのデータベース スナップショットを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-122">Before you can detach the database, you must drop all of its snapshots.</span></span> <span data-ttu-id="eafc9-123">詳細については、「 [データベース スナップショットの削除 &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-123">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eafc9-124">データベース スナップショットのデタッチおよびアタッチは行うことができません。</span><span class="sxs-lookup"><span data-stu-id="eafc9-124">A database snapshot cannot be detached or attached.</span></span>  
  
-   <span data-ttu-id="eafc9-125">データベースがデータベース ミラーリング セッションでミラー化される。</span><span class="sxs-lookup"><span data-stu-id="eafc9-125">The database is being mirrored in a database mirroring session.</span></span>  
  
     <span data-ttu-id="eafc9-126">セッションが終了するまでは、データベースはデタッチできません。</span><span class="sxs-lookup"><span data-stu-id="eafc9-126">The database cannot be detached unless the session is terminated.</span></span> <span data-ttu-id="eafc9-127">詳細については、「 [データベース ミラーリングの削除 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-127">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="eafc9-128">データベースに問題がある。</span><span class="sxs-lookup"><span data-stu-id="eafc9-128">The database is suspect.</span></span> <span data-ttu-id="eafc9-129">問題のあるデータベースはデタッチできません。デタッチするには緊急モードにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-129">A suspect database cannot be detached; before you can detach it, you must put it into emergency mode.</span></span> <span data-ttu-id="eafc9-130">データベースを緊急モードに設定する方法の詳細については、「 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-130">For more information about how to put a database into emergency mode, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="eafc9-131">データベースがシステム データベースである。</span><span class="sxs-lookup"><span data-stu-id="eafc9-131">The database is a system database.</span></span>  
  
### <a name="backup-and-restore-and-detach"></a><span data-ttu-id="eafc9-132">バックアップと復元およびデタッチ</span><span class="sxs-lookup"><span data-stu-id="eafc9-132">Backup and Restore and Detach</span></span>  
 <span data-ttu-id="eafc9-133">読み取り専用のデータベースをデタッチすると、差分バックアップの差分ベースに関する情報が失われます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-133">Detaching a read-only database loses information about the differential bases of differential backups.</span></span> <span data-ttu-id="eafc9-134">詳細については、「 [差分バックアップ &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-134">For more information, see [Differential Backups &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).</span></span>  
  
### <a name="responding-to-detach-errors"></a><span data-ttu-id="eafc9-135">デタッチ エラーへの対応</span><span class="sxs-lookup"><span data-stu-id="eafc9-135">Responding to Detach Errors</span></span>  
 <span data-ttu-id="eafc9-136">データベースのデタッチ中にエラーが発生すると、データベースがクリーンに閉じず、トランザクション ログが再構築されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-136">Errors produced while detaching a database can prevent the database from closing cleanly and the transaction log from being rebuilt.</span></span> <span data-ttu-id="eafc9-137">エラー メッセージが表示される場合は、次の修正操作を実行してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-137">If you receive an error message, perform the following corrective actions:</span></span>  
  
1.  <span data-ttu-id="eafc9-138">プライマリ ファイルだけでなく、データベースに関連付けられているすべてのファイルを再アタッチします。</span><span class="sxs-lookup"><span data-stu-id="eafc9-138">Reattach all files associated with the database, not just the primary file.</span></span>  
  
2.  <span data-ttu-id="eafc9-139">エラー メッセージの原因となった問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="eafc9-139">Resolve the problem that caused the error message.</span></span>  
  
3.  <span data-ttu-id="eafc9-140">データベースをデタッチし直します。</span><span class="sxs-lookup"><span data-stu-id="eafc9-140">Detach the database again.</span></span>  
  
##  <a name="attaching-a-database"></a><a name="AttachDb"></a> <span data-ttu-id="eafc9-141">データベースのインポート</span><span class="sxs-lookup"><span data-stu-id="eafc9-141">Attaching a Database</span></span>  
 <span data-ttu-id="eafc9-142">コピーまたはデタッチした [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースはアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-142">You can attach a copied or detached [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="eafc9-143">サーバーインスタンスをアタッチすると [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] 、カタログファイルは、の場合と同じように、他のデータベースファイルと一緒に以前の場所からアタッチされ [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-143">When you attach a [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] server instance, the catalog files are attached from their previous location along with the other database files, the same as in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="eafc9-144">詳細については、「 [フルテキスト検索のアップグレード](../search/upgrade-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-144">For more information, see [Upgrade Full-Text Search](../search/upgrade-full-text-search.md).</span></span>  
  
 <span data-ttu-id="eafc9-145">データベースをアタッチするときは、すべてのデータ ファイル (MDF ファイルおよび NDF ファイル) を利用できる状態にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-145">When you attach a database, all data files (MDF and NDF files) must be available.</span></span> <span data-ttu-id="eafc9-146">データベースを最初に作成したときか最後にアタッチしたときとデータ ファイルのパスが異なる場合、ファイルの現在のパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-146">If any data file has a different path from when the database was first created or last attached, you must specify the current path of the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eafc9-147">アタッチ中のプライマリ データ ファイルが読み取り専用の場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ではデータベースが読み取り専用であると想定されます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-147">If the primary data file being attached is read-only, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] assumes that the database is read-only.</span></span>  
  
 <span data-ttu-id="eafc9-148">暗号化されたデータベースがのインスタンスに最初にアタッチされている場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、データベース所有者は、OPEN MASTER KEY 解読 BY PASSWORD = **' *`password`* '** というステートメントを実行して、データベースのマスターキーを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-148">When an encrypted database is first attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the database owner must open the master key of the database by executing the following statement: OPEN MASTER KEY DECRYPTION BY PASSWORD = **'*`password`*'**.</span></span> <span data-ttu-id="eafc9-149">ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY ステートメントを実行してマスター キーの自動暗号化解除を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="eafc9-149">We recommend that you enable automatic decryption of the master key by executing the following statement: ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY.</span></span> <span data-ttu-id="eafc9-150">詳細については、「[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)」と「[ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-150">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) and [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span>  
  
 <span data-ttu-id="eafc9-151">次に示すように、ログ ファイルをアタッチするための要件の一部は、データベースが読み書き可能か読み取り専用かによって異なります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-151">The requirement for attaching log files depends partly on whether the database is read-write or read-only, as follows:</span></span>  
  
-   <span data-ttu-id="eafc9-152">読み書き可能なデータベースは、通常、新しい場所にログ ファイルをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-152">For a read-write database, you can usually attach a log file in a new location.</span></span> <span data-ttu-id="eafc9-153">ただし、場合によっては、データベースの再アタッチに既存のログ ファイルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-153">However, in some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="eafc9-154">したがって、デタッチされたログ ファイルなしでデータベースが正常にアタッチされるまで、デタッチされたすべてのログ ファイルを常に保持しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="eafc9-154">Therefore, it is important to always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
     <span data-ttu-id="eafc9-155">読み書き可能なデータベースのログ ファイルが 1 つで、そのファイルの新しい場所を指定しない場合、アタッチ操作ではファイルの古い場所が検索されます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-155">If a read-write database has a single log file and you do not specify a new location for the log file, the attach operation looks in the old location for the file.</span></span> <span data-ttu-id="eafc9-156">古いログ ファイルが見つかった場合、データベースがクリーンにシャットダウンされたかどうかにかかわらず、そのファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-156">If it is found, the old log file is used, regardless of whether the database was shut down cleanly.</span></span> <span data-ttu-id="eafc9-157">しかし、古いログ ファイルが見つからなかった場合、およびデータベースがクリーンにシャットダウンされたもののアクティブなログ チェーンがない場合、アタッチ操作によってそのデータベースの新しいログ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-157">However, if the old log file is not found and if the database was shut down cleanly and has no active log chain, the attach operation attempts to build a new log file for the database.</span></span>  
  
-   <span data-ttu-id="eafc9-158">アタッチされているプライマリデータファイルが読み取り専用の場合、は [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] プライマリファイルに格納されているログの場所を更新できません。</span><span class="sxs-lookup"><span data-stu-id="eafc9-158">If the primary data file being attached is read-only, the [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] cannot update the log location stored in the primary file.</span></span>  
  
  
  
###  <a name="metadata-changes-on-attaching-a-database"></a><a name="Metadata"></a> <span data-ttu-id="eafc9-159">データベースのインポート時におけるメタデータの変更</span><span class="sxs-lookup"><span data-stu-id="eafc9-159">Metadata Changes on Attaching a Database</span></span>  
 <span data-ttu-id="eafc9-160">読み取り専用データベースをデタッチして再アタッチすると、現在の差分ベースに関するバックアップ情報が失われます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-160">When a read-only database is detached and then reattached, the backup information about the current differential base is lost.</span></span> <span data-ttu-id="eafc9-161">*差分ベース* とは、データベース内のすべてのデータ、またはデータベースのファイルやファイル グループのサブセット内のすべてのデータを対象とした最新の完全バックアップのことです。</span><span class="sxs-lookup"><span data-stu-id="eafc9-161">The *differential base* is the most recent full backup of all the data in the database or in a subset of the files or filegroups of the database.</span></span> <span data-ttu-id="eafc9-162">ベース バックアップ情報がない場合、 **master** データベースは読み取り専用データベースと同期されなくなります。そのため、それ以降に取得した差分バックアップで予期しない結果が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-162">Without the base-backup information, the **master** database becomes unsynchronized with the read-only database, so differential backups taken thereafter may provide unexpected results.</span></span> <span data-ttu-id="eafc9-163">したがって、読み取り専用データベースに対して差分バックアップを使用する場合は、データベースを再アタッチした後に、完全バックアップを行って新しい差分ベースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-163">Therefore, if you are using differential backups with a read-only database, you should establish a new differential base by taking a full backup after you reattach the database.</span></span> <span data-ttu-id="eafc9-164">差分バックアップについては、「[差分バックアップ &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-164">For information about differential backups, see [Differential Backups &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="eafc9-165">アタッチ時に、データベースが起動します。</span><span class="sxs-lookup"><span data-stu-id="eafc9-165">On attach, database startup occurs.</span></span> <span data-ttu-id="eafc9-166">通常はデータベースをアタッチすると、そのデータベースはデタッチまたはコピーされたときと同じ状態になります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-166">Generally, attaching a database places it in the same state that it was in when it was detached or copied.</span></span> <span data-ttu-id="eafc9-167">ただし、アタッチおよびデタッチ操作により、複数データベースにまたがる組み合わせ所有権が無効になります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-167">However, attach-and-detach operations both disable cross-database ownership chaining for the database.</span></span> <span data-ttu-id="eafc9-168">チェーンを有効にする方法については、「 [cross db ownership chaining サーバー構成オプション](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-168">For information about how to enable chaining, see [cross db ownership chaining Server Configuration Option](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md).</span></span> <span data-ttu-id="eafc9-169">また、データベースをアタッチするときは常に TRUSTWORTHY が OFF に設定されます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-169">Also, TRUSTWORTHY is set to OFF whenever the database is attached.</span></span> <span data-ttu-id="eafc9-170">TRUSTWORTHY を ON に設定する方法については「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-170">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
### <a name="backup-and-restore-and-attach"></a><span data-ttu-id="eafc9-171">バックアップと復元およびアタッチ</span><span class="sxs-lookup"><span data-stu-id="eafc9-171">Backup and Restore and Attach</span></span>  
 <span data-ttu-id="eafc9-172">完全または部分的にオフラインのデータベースと同様に、復元中のファイルが含まれているデータベースはアタッチできません。</span><span class="sxs-lookup"><span data-stu-id="eafc9-172">Like any database that is fully or partially offline, a database with restoring files cannot be attached.</span></span> <span data-ttu-id="eafc9-173">復元シーケンスを停止すると、データベースをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-173">If you stop the restore sequence, you can attach the database.</span></span> <span data-ttu-id="eafc9-174">データベースのインポート後、復元シーケンスを再開できます。</span><span class="sxs-lookup"><span data-stu-id="eafc9-174">Then, you can restart the restore sequence.</span></span>  
  
###  <a name="attaching-a-database-to-another-server-instance"></a><a name="OtherServerInstance"></a> <span data-ttu-id="eafc9-175">別のサーバー インスタンスへのデータベースのインポート</span><span class="sxs-lookup"><span data-stu-id="eafc9-175">Attaching a Database to Another Server Instance</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eafc9-176">新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で作成したデータベースは、それ以前のバージョンでアタッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="eafc9-176">A database created by a more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be attached in earlier versions.</span></span>  
  
 <span data-ttu-id="eafc9-177">データベースを別のサーバー インスタンスにアタッチするときは、ユーザーおよびアプリケーションに一貫した使用環境を提供するために、アタッチ先のサーバー インスタンスで、ログインやジョブなどのデータベースのメタデータの一部またはすべてを作成し直す必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="eafc9-177">When you attach a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="eafc9-178">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafc9-178">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="eafc9-179">関連タスク</span><span class="sxs-lookup"><span data-stu-id="eafc9-179">Related Tasks</span></span>  
 <span data-ttu-id="eafc9-180">**データベースをデタッチするには**</span><span class="sxs-lookup"><span data-stu-id="eafc9-180">**To detach a database**</span></span>  
  
-   [<span data-ttu-id="eafc9-181">sp_detach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eafc9-181">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [<span data-ttu-id="eafc9-182">データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="eafc9-182">Detach a Database</span></span>](detach-a-database.md)  
  
 <span data-ttu-id="eafc9-183">**データベースをアタッチするには**</span><span class="sxs-lookup"><span data-stu-id="eafc9-183">**To attach a database**</span></span>  
  
-   [<span data-ttu-id="eafc9-184">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eafc9-184">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="eafc9-185">データベースのアタッチ</span><span class="sxs-lookup"><span data-stu-id="eafc9-185">Attach a Database</span></span>](attach-a-database.md)  
  
-   [<span data-ttu-id="eafc9-186">sp_attach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eafc9-186">sp_attach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql)  
  
-   [<span data-ttu-id="eafc9-187">sp_attach_single_file_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eafc9-187">sp_attach_single_file_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql)  
  
 <span data-ttu-id="eafc9-188">**デタッチとアタッチを使用してデータベースをアップグレードするには**</span><span class="sxs-lookup"><span data-stu-id="eafc9-188">**To upgrade a database using detach and attach operations**</span></span>  
  
-   [<span data-ttu-id="eafc9-189">デタッチとアタッチを使用したデータベースのアップグレード &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eafc9-189">Upgrade a Database Using Detach and Attach &#40;Transact-SQL&#41;</span></span>](upgrade-a-database-using-detach-and-attach-transact-sql.md)  
  
 <span data-ttu-id="eafc9-190">**デタッチとアタッチを使用してデータベースを移動するには**</span><span class="sxs-lookup"><span data-stu-id="eafc9-190">**To move a database using detach and attach operations**</span></span>  
  
-   [<span data-ttu-id="eafc9-191">デタッチとアタッチを使用してデータベースを移動する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eafc9-191">Move a Database Using Detach and Attach &#40;Transact-SQL&#41;</span></span>](move-a-database-using-detach-and-attach-transact-sql.md)  
  
 <span data-ttu-id="eafc9-192">**データベース スナップショットを削除するには**</span><span class="sxs-lookup"><span data-stu-id="eafc9-192">**To delete a database snapshot**</span></span>  
  
-   [<span data-ttu-id="eafc9-193">データベース スナップショットの削除 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eafc9-193">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="eafc9-194">参照</span><span class="sxs-lookup"><span data-stu-id="eafc9-194">See Also</span></span>  
 [<span data-ttu-id="eafc9-195">データベース ファイルとファイル グループ</span><span class="sxs-lookup"><span data-stu-id="eafc9-195">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
