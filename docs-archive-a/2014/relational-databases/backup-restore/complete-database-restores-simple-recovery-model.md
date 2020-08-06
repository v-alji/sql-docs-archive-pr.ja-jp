---
title: データベースの全体復元 (単純復旧モデル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- simple recovery model [SQL Server]
- restoring [SQL Server], database
ms.assetid: 49828927-1727-4d1d-9ef5-3de43f68c026
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67eee8d7d6f44c9ff83795bf2a8bd612309bf0a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645684"
---
# <a name="complete-database-restores-simple-recovery-model"></a><span data-ttu-id="f1263-102">データベースの全体復元 (単純復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="f1263-102">Complete Database Restores (Simple Recovery Model)</span></span>
  <span data-ttu-id="f1263-103">データベースの全体復元の目的は、データベース全体を復元することです。</span><span class="sxs-lookup"><span data-stu-id="f1263-103">In a complete database restore, the goal is to restore the whole database.</span></span> <span data-ttu-id="f1263-104">復元の実行中は、データベース全体がオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="f1263-104">The whole database is offline for the duration of the restore.</span></span> <span data-ttu-id="f1263-105">データベースの各部がオンラインになる前に、すべてのデータが一貫性のある状態に復旧されます。一貫性のある状態とは、データベースのすべての部分が同じ時点にあり、コミットされていないトランザクションが存在しない状態を示します。</span><span class="sxs-lookup"><span data-stu-id="f1263-105">Before any part of the database can come online, all data is recovered to a consistent point in which all parts of the database are at the same point in time and no uncommitted transactions exist.</span></span>  
  
 <span data-ttu-id="f1263-106">単純復旧モデルでは、特定のバックアップ内にある特定の時点にデータベースを復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="f1263-106">Under the simple recovery model, the database cannot be restored to a specific point in time within a specific backup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f1263-107">不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f1263-107">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="f1263-108">そのようなデータベースには、意図しない [!INCLUDE[tsql](../../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更することによりエラーを発生させる悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1263-108">These databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="f1263-109">不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。</span><span class="sxs-lookup"><span data-stu-id="f1263-109">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  

  
> [!NOTE]  
>  <span data-ttu-id="f1263-110">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からのバックアップに対するサポートの情報については、「 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)」の「互換性サポート」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1263-110">For information about support for backups from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the "Compatibility Support" section of [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="overview-of-database-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> <span data-ttu-id="f1263-111">単純復旧モデルでのデータベース復元の概要</span><span class="sxs-lookup"><span data-stu-id="f1263-111">Overview of Database Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="f1263-112">単純復旧モデルでのデータベース全体の復元は、データベースの差分バックアップを復元する必要があるかどうかに応じて 1 つまたは 2 つの [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントで行われます。</span><span class="sxs-lookup"><span data-stu-id="f1263-112">A full database restore under the simple recovery model involves one or two [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statements, depending on whether you want to restore a differential database backup.</span></span> <span data-ttu-id="f1263-113">次の図に示すように、データベースの完全バックアップのみを使用する場合は、最新のバックアップを復元するだけで完了します。</span><span class="sxs-lookup"><span data-stu-id="f1263-113">If you are using only a full database backup, just restore the most recent backup, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="f1263-114">![データベースの完全バックアップのみの復元](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "データベースの完全バックアップのみの復元")</span><span class="sxs-lookup"><span data-stu-id="f1263-114">![Restoring only a full database backup](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "Restoring only a full database backup")</span></span>  
  
 <span data-ttu-id="f1263-115">データベースの差分バックアップも使用する場合は、データベースを復旧しないで最新の完全バックアップを復元してから、最新の差分バックアップを復元してデータベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="f1263-115">If you are also using a differential database backup, restore the most recent full database backup without recovering the database, and then restore the most recent differential database backup and recover the database.</span></span> <span data-ttu-id="f1263-116">次の図に、このプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="f1263-116">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="f1263-117">![データベースの完全および差分バックアップを復元する](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "データベースの完全および差分バックアップの復元")</span><span class="sxs-lookup"><span data-stu-id="f1263-117">![Restoring full and differential database backups](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "Restoring full and differential database backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1263-118">データベースのバックアップを別のサーバー インスタンスに復元する予定の場合は、「 [バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1263-118">If you plan to restore a database backup onto a different server instance, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> <span data-ttu-id="f1263-119">基本的な Transact-SQL RESTORE 構文</span><span class="sxs-lookup"><span data-stu-id="f1263-119">Basic Transact-SQL RESTORE Syntax</span></span>  
 <span data-ttu-id="f1263-120">データベースの完全バックアップを復元する際に使用する、 [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) の基本構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f1263-120">The basic [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for restoring a full database backup is:</span></span>  
  
 <span data-ttu-id="f1263-121">RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]</span><span class="sxs-lookup"><span data-stu-id="f1263-121">RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1263-122">データベースの差分バックアップも復元する場合は、WITH NORECOVERY を指定してください。</span><span class="sxs-lookup"><span data-stu-id="f1263-122">Use WITH NORECOVERY if you plan to also restore a differential database backup.</span></span>  
  
 <span data-ttu-id="f1263-123">データベース バックアップを復元する際に使用する、 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) の基本構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f1263-123">The basic [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for restoring a database backup is:</span></span>  
  
 <span data-ttu-id="f1263-124">RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="f1263-124">RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY</span></span>  
  
###  <a name="example-transact-sql"></a><a name="Example"></a> <span data-ttu-id="f1263-125">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1263-125">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f1263-126">次の例では、まず [BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントを使用して、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの完全バックアップと差分バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1263-126">The following example first shows how to use the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement to create a full database backup and a differential database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="f1263-127">その後、これらのバックアップを順に復元します。</span><span class="sxs-lookup"><span data-stu-id="f1263-127">The example then restores these backups in sequence.</span></span> <span data-ttu-id="f1263-128">データベースは、差分データベース バックアップ完了時の状態に復元されます。</span><span class="sxs-lookup"><span data-stu-id="f1263-128">The database is restored to its state as of the time that the differential database backup finished.</span></span>  
  
 <span data-ttu-id="f1263-129">この例は、データベースの全体復元シナリオの復元シーケンスで重要なオプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="f1263-129">The example shows the critical options in a restore sequence for the complete database restore scenario.</span></span> <span data-ttu-id="f1263-130">*復元シーケンス* は、1 つ以上の復元フェーズによってデータを移動する、1 つ以上の復元操作で構成されます。</span><span class="sxs-lookup"><span data-stu-id="f1263-130">A *restore sequence* consists of one or more restore operations that move data through one or more of the phases of restore.</span></span> <span data-ttu-id="f1263-131">説明の目的に関係しない構文や詳細は、省略しています。</span><span class="sxs-lookup"><span data-stu-id="f1263-131">Syntax and details that are not relevant to this purpose are omitted.</span></span> <span data-ttu-id="f1263-132">データベースを復旧する際は、RECOVERY オプションを明示的に指定することをお勧めします。このオプションは既定値ですが、指定しておくと判別がつきやすくなります。</span><span class="sxs-lookup"><span data-stu-id="f1263-132">When you recover a database, we recommend explicitly specifying the RECOVERY option for clarity, even though it is the default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1263-133">この例の先頭では、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) ステートメントを使用して復旧モデルを `SIMPLE`に設定しています。</span><span class="sxs-lookup"><span data-stu-id="f1263-133">The example starts with an [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement that sets the recovery model to `SIMPLE`.</span></span>  
  
```  
USE master;  
--Make sure the database is using the simple recovery model.  
ALTER DATABASE AdventureWorks2012 SET RECOVERY SIMPLE;  
GO  
-- Back up the full AdventureWorks2012 database.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
  WITH FORMAT;  
GO  
--Create a differential database backup.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH DIFFERENTIAL;  
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=1, NORECOVERY;  
--Restore the differential backup (from backup set 2).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=2, RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f1263-134">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f1263-134">Related Tasks</span></span>  
 <span data-ttu-id="f1263-135">**データベースの完全バックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="f1263-135">**To restore a full database backup**</span></span>  
  
-   [<span data-ttu-id="f1263-136">単純復旧モデルでのデータベース バックアップの復元 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1263-136">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="f1263-137">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f1263-137">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="f1263-138">データベースを新しい場所に復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f1263-138">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
 <span data-ttu-id="f1263-139">**データベースの差分バックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="f1263-139">**To restore a differential database backup**</span></span>  
  
-   [<span data-ttu-id="f1263-140">データベースの差分バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f1263-140">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="f1263-141">**SQL Server 管理オブジェクト (SMO) を使用してバックアップを復元するには**</span><span class="sxs-lookup"><span data-stu-id="f1263-141">**To restore a backup by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  

  
## <a name="see-also"></a><span data-ttu-id="f1263-142">参照</span><span class="sxs-lookup"><span data-stu-id="f1263-142">See Also</span></span>  
 <span data-ttu-id="f1263-143">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1263-143">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="f1263-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1263-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="f1263-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1263-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="f1263-146">[データベースの完全バックアップ &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f1263-146">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="f1263-147">[差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f1263-147">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="f1263-148">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f1263-148">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="f1263-149">復元と復旧の概要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f1263-149">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
