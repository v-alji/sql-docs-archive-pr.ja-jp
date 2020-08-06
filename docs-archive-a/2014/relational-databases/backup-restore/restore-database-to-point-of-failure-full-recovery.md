---
title: 完全復旧モデルで障害発生時点までデータベースを復元する方法 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- point of failure [SQL Server]
- restoring databases [SQL Server], point of failure
- database restores [SQL Server], point of failure
ms.assetid: 04106e18-bbf7-4a5e-a2e1-3d65319814d5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95b73660ebb44f4daffe6eaefd873699cfbbd8ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640087"
---
# <a name="restore-a-database-to-the-point-of-failure-under-the-full-recovery-model-transact-sql"></a><span data-ttu-id="0a859-102">完全復旧モデルで障害発生時点までデータベースを復元する方法 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0a859-102">Restore a Database to the Point of Failure Under the Full Recovery Model (Transact-SQL)</span></span>
  <span data-ttu-id="0a859-103">このトピックでは、障害が発生する直前の状態まで復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a859-103">This topic explains how to restore to the point of failure.</span></span> <span data-ttu-id="0a859-104">このトピックは、完全復旧モデルまたは一括ログ復旧モデルを使用しているデータベースのみを対象としています。</span><span class="sxs-lookup"><span data-stu-id="0a859-104">The topic is relevant only for databases that are using the full or bulk-logged recovery models.</span></span>  
  
### <a name="to-restore-to-the-point-of-failure"></a><span data-ttu-id="0a859-105">障害発生時点まで復元するには</span><span class="sxs-lookup"><span data-stu-id="0a859-105">To restore to the point of failure</span></span>  
  
1.  <span data-ttu-id="0a859-106">次の基本的な [BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントを実行して、ログの末尾をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="0a859-106">Back up the tail of the log by running the following basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement:</span></span>  
  
    ```  
    BACKUP LOG <database_name> TO <backup_device>   
       WITH NORECOVERY, NO_TRUNCATE;  
    ```  
  
2.  <span data-ttu-id="0a859-107">次の基本的な [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントを実行して、データベースの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="0a859-107">Restore a full database backup by running the following basic [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
3.  <span data-ttu-id="0a859-108">必要に応じて、次の基本的な RESTORE DATABASE ステートメントを実行して、データベースの差分バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="0a859-108">Optionally, restore a differential database backup by running the following basic RESTORE DATABASE statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
4.  <span data-ttu-id="0a859-109">RESTORE LOG ステートメントで WITH NORECOVERY を指定して、手順 1. で作成したログ末尾のバックアップを含む各トランザクション ログ バックアップを適用します。</span><span class="sxs-lookup"><span data-stu-id="0a859-109">Apply each transaction log, including the tail-log backup you created in step 1, by specifying WITH NORECOVERY in the RESTORE LOG statement:</span></span>  
  
    ```  
    RESTORE LOG <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
5.  <span data-ttu-id="0a859-110">次の RESTORE DATABASE ステートメントを実行して、データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="0a859-110">Recover the database by running the following RESTORE DATABASE statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name>   
       WITH RECOVERY;  
    ```  
  
## <a name="example"></a><span data-ttu-id="0a859-111">例</span><span class="sxs-lookup"><span data-stu-id="0a859-111">Example</span></span>  
 <span data-ttu-id="0a859-112">この例を実行する前に、次の準備作業を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a859-112">Before you can run the example, you must complete the following preparations:</span></span>  
  
1.  <span data-ttu-id="0a859-113">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの既定の復旧モデルは、単純復旧モデルです。</span><span class="sxs-lookup"><span data-stu-id="0a859-113">The default recovery model of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is the simple recovery model.</span></span> <span data-ttu-id="0a859-114">この復旧モデルでは障害発生時点までの復旧がサポートされていないため、次の [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ALTER DATABASE [ステートメントを実行して、完全復旧モデルが使用されるように](/sql/t-sql/statements/alter-database-transact-sql) を設定します。</span><span class="sxs-lookup"><span data-stu-id="0a859-114">Because this recovery model does not support restoring to the point of a failure, set [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] to use the full recovery model by running the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
    ```  
  
2.  <span data-ttu-id="0a859-115">次の BACKUP ステートメントを使用して、このデータベースの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a859-115">Create a full database back of the database by using the following BACKUP statement:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Data.bck';  
    ```  
  
3.  <span data-ttu-id="0a859-116">次のように、定期的なログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a859-116">Create a routine log backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Log.bck';  
    ```  
  
 <span data-ttu-id="0a859-117">次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースのログ末尾のバックアップを作成した後に、以前作成したバックアップを復元します</span><span class="sxs-lookup"><span data-stu-id="0a859-117">The following example restores the backups that are created previously, after creating a tail-log backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="0a859-118">(この手順は、ログ ディスクにアクセスできることを前提としています)。</span><span class="sxs-lookup"><span data-stu-id="0a859-118">(This step assumes that the log disk can be accessed.)</span></span>  
  
 <span data-ttu-id="0a859-119">まず、データベースのログ末尾のバックアップを作成して、アクティブなログをキャプチャし、データベースを復元中の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="0a859-119">First, the example creates a tail-log backup of the database that captures the active log and leaves the database in the Restoring state.</span></span> <span data-ttu-id="0a859-120">次に、データベースのバックアップを復元し、以前作成した定期的なログ バックアップを適用し、ログ末尾のバックアップを適用します。</span><span class="sxs-lookup"><span data-stu-id="0a859-120">Then, the example restores the database backup, applies the routine log backup created previously, and applies the tail-log backup.</span></span> <span data-ttu-id="0a859-121">最後に、別の手順でデータベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="0a859-121">Finally, the example recovers the database in a separate step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a859-122">既定の動作では、最終的なバックアップを復元するステートメントに、データベースの復旧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a859-122">The default behavior is to recover a database as part of the statement that restores the final backup.</span></span>  
  
```  
/* Example of restoring a to the point of failure */  
-- Step 1: Create a tail-log backup by using WITH NORECOVERY.  
BACKUP LOG AdventureWorks2012  
   TO DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 2: Restore the full database backup.  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Data.bck'  
   WITH NORECOVERY;  
GO  
-- Step 3: Restore the first transaction log backup.  
RESTORE LOG AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 4: Restore the tail-log backup.  
RESTORE LOG AdventureWorks2012  
   FROM  DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 5: Recover the database.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a859-123">参照</span><span class="sxs-lookup"><span data-stu-id="0a859-123">See Also</span></span>  
 <span data-ttu-id="0a859-124">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a859-124">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="0a859-125">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0a859-125">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
