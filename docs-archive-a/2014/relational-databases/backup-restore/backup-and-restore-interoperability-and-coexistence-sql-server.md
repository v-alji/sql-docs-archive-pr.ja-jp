---
title: 'バックアップと復元: 相互運用性と共存 (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server], related features
- restoring [SQL Server], files
- restoring files [SQL Server], related features
- backups [SQL Server], files or filegroups
- file backups [SQL Server], related features
ms.assetid: 69f212b8-edcd-4c5d-8a8a-679ced33c128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd78e5f1e85510ec7a14548280a616a9b32aec55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631111"
---
# <a name="backup-and-restore-interoperability-and-coexistence-sql-server"></a><span data-ttu-id="93366-102">バックアップと復元: 相互運用性と共存 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="93366-102">Backup and Restore: Interoperability and Coexistence (SQL Server)</span></span>
  <span data-ttu-id="93366-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のいくつかの機能のバックアップと復元に関する考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="93366-103">This topic describes backup-and-restore considerations for several features in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="93366-104">このような機能には、ファイル復元とデータベースの起動、オンライン復元と無効化されたインデックス、データベース ミラーリング、段階的な部分復元、およびフルテキスト インデックスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="93366-104">These features include: file restore and database startup, online restore and disabled indexes, database mirroring, and piecemeal restore and full-text indexes.</span></span>  
  
 <span data-ttu-id="93366-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="93366-105">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="93366-106">ファイル復元とデータベースの起動</span><span class="sxs-lookup"><span data-stu-id="93366-106">File Restore and Database Startup</span></span>](#FileRestoreAndDbStartup)  
  
-   [<span data-ttu-id="93366-107">オンライン復元と無効化されたインデックス</span><span class="sxs-lookup"><span data-stu-id="93366-107">Online Restore and Disabled Indexes</span></span>](#OnlineRestoreAndDisabledIndexes)  
  
-   [<span data-ttu-id="93366-108">データベース ミラーリングおよびバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="93366-108">Database Mirroring and Backup and Restore</span></span>](#DbMandBnR)  
  
-   [<span data-ttu-id="93366-109">段階的な部分復元とフルテキスト インデックス</span><span class="sxs-lookup"><span data-stu-id="93366-109">Piecemeal Restore and Full-Text Indexes</span></span>](#PiecemealAndFTIndexes)  
  
-   [<span data-ttu-id="93366-110">ファイル バックアップと復元と圧縮</span><span class="sxs-lookup"><span data-stu-id="93366-110">File Backup and Restore and Compression</span></span>](#FileBnRandCompression)  
  
-   [<span data-ttu-id="93366-111">関連タスク</span><span class="sxs-lookup"><span data-stu-id="93366-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="file-restore-and-database-startup"></a><a name="FileRestoreAndDbStartup"></a> <span data-ttu-id="93366-112">ファイル復元とデータベースの起動</span><span class="sxs-lookup"><span data-stu-id="93366-112">File Restore and Database Startup</span></span>  
 <span data-ttu-id="93366-113">ここで説明する内容は、複数のファイル グループを含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="93366-113">This section is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that have multiple filegroups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93366-114">データベースが起動されると、そのデータベースの終了時にファイルがオンラインだったファイル グループのみが復旧され、オンラインになります。</span><span class="sxs-lookup"><span data-stu-id="93366-114">When a database is started, only filegroups whose files were online when the database was closed are recovered and brought online.</span></span>  
  
 <span data-ttu-id="93366-115">データベースの起動中に問題が発生した場合、復旧は失敗し、データベースは SUSPECT に設定されます。</span><span class="sxs-lookup"><span data-stu-id="93366-115">If a problem is encountered during database startup, recovery fails, and the database is marked as SUSPECT.</span></span> <span data-ttu-id="93366-116">問題のファイルを特定できる場合、データベース管理者は、それらのファイルをオフラインにし、データベースの再起動を試行できます。</span><span class="sxs-lookup"><span data-stu-id="93366-116">If the problem can be isolated to a file or files, the database administrator can take the files offline and try to restart the database.</span></span> <span data-ttu-id="93366-117">ファイルをオフラインにするには、次の [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="93366-117">To take a file offline, you can use the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
 <span data-ttu-id="93366-118">ALTER database *database_name* MODIFY FILE (name **= ' *`filename`* '**、OFFLINE)</span><span class="sxs-lookup"><span data-stu-id="93366-118">ALTER DATABASE *database_name* MODIFY FILE (NAME **='*`filename`*'**, OFFLINE)</span></span>  
  
 <span data-ttu-id="93366-119">起動に成功した場合、オフライン ファイルが含まれるファイル グループはすべてオフライン状態で維持されます。</span><span class="sxs-lookup"><span data-stu-id="93366-119">If startup succeeds, any filegroup that contains an offline file remains offline.</span></span>  
  
##  <a name="online-restore-and-disabled-indexes"></a><a name="OnlineRestoreAndDisabledIndexes"></a> <span data-ttu-id="93366-120">オンライン復元と無効化されたインデックス</span><span class="sxs-lookup"><span data-stu-id="93366-120">Online Restore and Disabled Indexes</span></span>  
 <span data-ttu-id="93366-121">ここで説明する内容は、複数のファイル グループを含むデータベースと、単純復旧モデルの場合の 1 つ以上の読み取り専用ファイル グループに適用されます。</span><span class="sxs-lookup"><span data-stu-id="93366-121">This section is relevant only for databases that have multiple filegroups and, for the simple recovery model, at least one read-only filegroup.</span></span>  
  
 <span data-ttu-id="93366-122">これらのケースにおいて、データベースがオンラインの場合、インデックスの作成、削除、有効化や無効化を行うことができるのは、インデックスのいずれかの部分を保持しているファイル グループがすべてオンラインのときだけです。</span><span class="sxs-lookup"><span data-stu-id="93366-122">In these cases, when a database is online, the index can be created, dropped, enabled or disabled only if all filegroups holding any part of the index are online.</span></span>  
  
 <span data-ttu-id="93366-123">オフラインのファイル グループを復元する方法については、「[オンライン復元 &#40;SQL Server&#41;](online-restore-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93366-123">For information about restoring offline filegroups, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
##  <a name="database-mirroring-and-backup-and-restore"></a><a name="DbMandBnR"></a> <span data-ttu-id="93366-124">データベース ミラーリングおよびバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="93366-124">Database Mirroring and Backup and Restore</span></span>  
 <span data-ttu-id="93366-125">ここで説明する内容は、複数のファイル グループを含む完全復旧モデルのデータベースだけに関連しています。</span><span class="sxs-lookup"><span data-stu-id="93366-125">This section is relevant only for full-model databases that have multiple filegroups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93366-126">データベース ミラーリング機能は、将来のバージョンの Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="93366-126">The database mirroring feature will be removed in a future version of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="93366-127">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="93366-127">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="93366-128">代わりに [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] を使用してください</span><span class="sxs-lookup"><span data-stu-id="93366-128">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="93366-129">データベース ミラーリングは、データベースの可用性を高めるためのソリューションです。</span><span class="sxs-lookup"><span data-stu-id="93366-129">Database mirroring is a solution for increasing database availability.</span></span> <span data-ttu-id="93366-130">ミラーリングはデータベースごとに実装され、完全復旧モデルを使用するデータベースでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="93366-130">Mirroring is implemented on a per-database basis and works only with databases that use the full recovery model.</span></span> <span data-ttu-id="93366-131">詳細については、「[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93366-131">For more information, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93366-132">データベースのファイル グループのサブセットのコピーを配布するには、レプリケーションを使用します。ファイル グループ内のオブジェクトのうち、他のサーバーにコピーしたいものだけをレプリケートします。</span><span class="sxs-lookup"><span data-stu-id="93366-132">To distribute copies of a subset of the filegroups in a database, use replication: replicate only those objects in the filegroups you want to copy to other servers.</span></span> <span data-ttu-id="93366-133">レプリケーションの詳細については、「 [SQL Server のレプリケーション](../../relational-databases/replication/sql-server-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93366-133">For more information about replication, see [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md).</span></span>  
  
### <a name="creating-the-mirror-database"></a><span data-ttu-id="93366-134">ミラー データベースの作成</span><span class="sxs-lookup"><span data-stu-id="93366-134">Creating the Mirror Database</span></span>  
 <span data-ttu-id="93366-135">WITH NORECOVERY を指定してプリンシパル データベースのバックアップをミラー サーバーに復元すると、ミラー データベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="93366-135">The mirror database is created by restoring, WITH NORECOVERY, backups of the principal database on the mirror server.</span></span> <span data-ttu-id="93366-136">この復元したデータベースの名前は、元のデータベースと同じ名前のままにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="93366-136">The restore must keep the same database name.</span></span> <span data-ttu-id="93366-137">詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93366-137">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="93366-138">段階的な部分復元シーケンスの使用がサポートされている場合は、これを使用してミラー データベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="93366-138">You can create the mirror database by using use a piecemeal restore sequence, where supported.</span></span> <span data-ttu-id="93366-139">ただし、ミラーリングを開始できるのは、すべてのファイル グループを復元し、通常はログ バックアップを復元して、ミラー データベースの状態をプリンシパル データベースの状態に十分近づけてからです。</span><span class="sxs-lookup"><span data-stu-id="93366-139">However, you cannot start mirroring until you have restored all the filegroups and, typically, restored log backups to get the mirror database close enough in time with the principal database.</span></span> <span data-ttu-id="93366-140">詳細については、「[段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93366-140">For more information, see [Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md).</span></span>  
  
### <a name="restrictions-on-backup-and-restore-during-mirroring"></a><span data-ttu-id="93366-141">ミラーリング中のバックアップおよび復元の制限</span><span class="sxs-lookup"><span data-stu-id="93366-141">Restrictions on Backup and Restore During Mirroring</span></span>  
 <span data-ttu-id="93366-142">データベース ミラーリング セッションがアクティブの場合は、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="93366-142">While a database mirroring session is active, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="93366-143">ミラー データベースのバックアップおよび復元は実行できません。</span><span class="sxs-lookup"><span data-stu-id="93366-143">Backup and restore of the mirror database are not allowed.</span></span>  
  
-   <span data-ttu-id="93366-144">プリンシパル データベースのバックアップは可能ですが、BACKUP LOG WITH NORECOVERY オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="93366-144">Backup of the principal database is allowed, but BACKUP LOG WITH NORECOVERY is not allowed.</span></span>  
  
-   <span data-ttu-id="93366-145">プリンシパル データベースの復元は実行できません。</span><span class="sxs-lookup"><span data-stu-id="93366-145">Restoring the principal database is not allowed.</span></span>  
  
##  <a name="piecemeal-restore-and-full-text-indexes"></a><a name="PiecemealAndFTIndexes"></a> <span data-ttu-id="93366-146">段階的な部分復元とフルテキスト インデックス</span><span class="sxs-lookup"><span data-stu-id="93366-146">Piecemeal Restore and Full-Text Indexes</span></span>  
 <span data-ttu-id="93366-147">ここで説明する内容は、複数のファイル グループを含むデータベースのみ (単純復旧モデルのデータベースでは、読み取り専用ファイル グループのみ) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="93366-147">This section is relevant only for databases that contain multiple filegroups and, for the simple-model databases, only for read-only filegroups.</span></span>  
  
 <span data-ttu-id="93366-148">フルテキスト インデックスは、データベース ファイル グループに格納され、段階的な部分復元による影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="93366-148">Full-text indexes are stored in database filegroups and can be affected by a piecemeal restore.</span></span> <span data-ttu-id="93366-149">関連するテーブル データのいずれかと同じファイル グループにフルテキスト インデックスが格納されている場合、段階的な部分復元は想定どおりに機能します。</span><span class="sxs-lookup"><span data-stu-id="93366-149">If the full-text index resides in the same filegroup as any of the associated table data, piecemeal restore works as expected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93366-150">フルテキスト インデックスが格納されているファイル グループのファイル グループ ID を表示するには、 [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)の data_space_id 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="93366-150">To view the filegroup ID of the filegroup that contains a full-text index, select the data_space_id column of [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql).</span></span>  
  
### <a name="full-text-indexes-and-tables-in-separate-filegroups"></a><span data-ttu-id="93366-151">ファイル グループが異なるフルテキスト インデックスとテーブル</span><span class="sxs-lookup"><span data-stu-id="93366-151">Full-Text Indexes and Tables in Separate Filegroups</span></span>  
 <span data-ttu-id="93366-152">フルテキスト インデックスが、関連するテーブル データのいずれとも異なるファイル グループに格納されている場合、先にどちらのファイル グループを復元しオンラインにするかによって段階的な部分復元の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="93366-152">If a full-text index resides in a separate filegroup from all of the associated table data, the behavior of piecemeal restore depends on which of the filegroups is restored and brought online first:</span></span>  
  
-   <span data-ttu-id="93366-153">関連するテーブル データを含むファイル グループより先に、フルテキスト インデックスを含むファイル グループが復元され、オンラインになる場合は、フルテキスト インデックスがオンラインになるとすぐ、フルテキスト検索が想定どおりに機能します。</span><span class="sxs-lookup"><span data-stu-id="93366-153">If the filegroup that contains the full-text index is restored and brought online before the filegroups that contain the associated table data, full-text search works as expected as soon as the full-text index is online.</span></span>  
  
-   <span data-ttu-id="93366-154">フルテキスト インデックスを含むファイル グループより先に、テーブル データを含むファイル グループが復元され、オンラインになる場合は、フルテキストの動作に影響があります。</span><span class="sxs-lookup"><span data-stu-id="93366-154">If the filegroup that contains the table data is restored and brought online before the filegroup that contains the full-text index, full-text behavior might be affected.</span></span> <span data-ttu-id="93366-155">インデックスがオンラインになっていないと、カタログの作成、カタログの再構築、またはカタログの再編成を起動する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが失敗するためです。</span><span class="sxs-lookup"><span data-stu-id="93366-155">This is because [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that trigger a population, rebuild the catalog, or reorganize the catalog fail until the index is brought online.</span></span> <span data-ttu-id="93366-156">このようなステートメントには、CREATE FULLTEXT INDEX、ALTER FULLTEXT INDEX、DROP FULLTEXT INDEX、および ALTER FULLTEXT CATALOG があります。</span><span class="sxs-lookup"><span data-stu-id="93366-156">These statements include CREATE FULLTEXT INDEX, ALTER FULLTEXT INDEX, DROP FULLTEXT INDEX, and ALTER FULLTEXT CATALOG.</span></span>  
  
     <span data-ttu-id="93366-157">この場合、次の要因が重要です。</span><span class="sxs-lookup"><span data-stu-id="93366-157">In this case, the following factors are significant:</span></span>  
  
    -   <span data-ttu-id="93366-158">フルテキスト インデックスに変更の追跡がある場合、インデックスのファイル グループがオンラインなっていないと、ユーザー DML が失敗します。</span><span class="sxs-lookup"><span data-stu-id="93366-158">If the full-text index has change tracking, user DML will fail until the index filegroup is brought online.</span></span> <span data-ttu-id="93366-159">インデックスのファイル グループがオンラインになっていないと、削除操作も失敗します。</span><span class="sxs-lookup"><span data-stu-id="93366-159">Delete operation will also fail until the index filegroup is online.</span></span>  
  
    -   <span data-ttu-id="93366-160">変更の追跡の状態にかかわらず、インデックスが使用できないので、フルテキスト クエリは失敗します。</span><span class="sxs-lookup"><span data-stu-id="93366-160">Regardless of change tracking, full-text queries fail because the index is not available.</span></span> <span data-ttu-id="93366-161">フルテキスト クエリの実行時に、フルテキスト インデックスを含むファイル グループがオフラインだった場合、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="93366-161">If a full-text query is tried when the filegroup that contains the full-text index is offline, an error is returned.</span></span>  
  
    -   <span data-ttu-id="93366-162">状態関数 (FULLTEXTCATALOGPROPERTY など) は、フルテキスト インデックスにアクセスする必要がない場合にのみ成功します。</span><span class="sxs-lookup"><span data-stu-id="93366-162">Status functions (such as FULLTEXTCATALOGPROPERTY) succeed only when they do not have to access full-text index.</span></span> <span data-ttu-id="93366-163">たとえば、オンラインのフルテキスト メタデータへのアクセスは成功しますが、 **uniquekeycount、itemcount** は失敗します。</span><span class="sxs-lookup"><span data-stu-id="93366-163">For example, access to any online full-text metadata would succeed, but **uniquekeycount, itemcount** would fail.</span></span>  
  
     <span data-ttu-id="93366-164">フルテキスト インデックスのファイル グループが復元され、オンラインになった後は、インデックス データとテーブル データの整合性が保たれています。</span><span class="sxs-lookup"><span data-stu-id="93366-164">After the full-text index filegroup is restored and brought online, the index data and table data are consistent.</span></span>  
  
 <span data-ttu-id="93366-165">ベース テーブルのファイル グループとフルテキスト インデックスのファイル グループの両方がオンラインになるとすぐに、一時停止中のフルテキスト作成がすべて再開されます。</span><span class="sxs-lookup"><span data-stu-id="93366-165">As soon as both the base table filegroup and the full-text index filegroup are online, any paused full-text population is resumed.</span></span>  
  
##  <a name="file-backup-and-restore-and-compression"></a><a name="FileBnRandCompression"></a> <span data-ttu-id="93366-166">ファイル バックアップと復元と圧縮</span><span class="sxs-lookup"><span data-stu-id="93366-166">File Backup and Restore and Compression</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="93366-167">では、読み取り専用ファイル グループや読み取り専用データベースの NTFS ファイル システム データ圧縮がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="93366-167">supports NTFS file system data compression of read-only filegroups and read-only databases.</span></span>  
  
 <span data-ttu-id="93366-168">圧縮された NTFS ファイルでは、読み取り専用ファイル グループのファイルの復元がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="93366-168">Restoring files in a read-only filegroup is supported on compressed NTFS files.</span></span> <span data-ttu-id="93366-169">このようなファイル グループのバックアップや復元は、基本的には読み取り専用ファイル グループと同様に機能しますが、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="93366-169">Backup and restore of these filegroups works essentially as it would for any read-only filegroup, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="93366-170">圧縮されたボリュームに読み書き可能なファイル (読み書き可能なデータベースのプライマリ ファイルやログ ファイルなど) を復元すると、失敗してエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="93366-170">Restoring a read-write file (including the primary or log files of a read-write database) to a compressed volume fails and displays an error.</span></span>  
  
-   <span data-ttu-id="93366-171">圧縮されたボリュームに読み取り専用データベースを復元することは可能です。</span><span class="sxs-lookup"><span data-stu-id="93366-171">Restoring a read-only database to a compressed volume is allowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93366-172">読み取りと書き込みが可能なデータベースのログ ファイルは、圧縮されたファイル システムには配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="93366-172">Log files of read/write databases should never be placed on compressed file systems.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="93366-173">関連タスク</span><span class="sxs-lookup"><span data-stu-id="93366-173">Related Tasks</span></span>  
  
-   [<span data-ttu-id="93366-174">ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="93366-174">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="93366-175">フルテキスト カタログとフルテキスト インデックスのバックアップおよび復元</span><span class="sxs-lookup"><span data-stu-id="93366-175">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](../search/back-up-and-restore-full-text-catalogs-and-indexes.md)  
  
## <a name="see-also"></a><span data-ttu-id="93366-176">参照</span><span class="sxs-lookup"><span data-stu-id="93366-176">See Also</span></span>  
 <span data-ttu-id="93366-177">[SQL Server データベースのバックアップと復元](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="93366-177">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="93366-178">[レプリケートされたデータベースのバックアップと復元](../replication/administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="93366-178">[Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md) </span></span>  
 [<span data-ttu-id="93366-179">アクティブなセカンダリ: セカンダリレプリカでのバックアップ &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="93366-179">Active Secondaries: Backup on Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
  
  
