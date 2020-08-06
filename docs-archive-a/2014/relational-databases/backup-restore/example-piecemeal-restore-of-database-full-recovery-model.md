---
title: '例 : データベースの部分復元 (完全復旧モデル) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- piecemeal restores [SQL Server], full recovery model
- restore sequences [SQL Server], piecemeal
ms.assetid: 0a84892d-2f7a-4e77-b2d0-d68b95595210
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5cfccccdbdc0c4fb3b189ee0a9fa3aeaf426578b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720097"
---
# <a name="example-piecemeal-restore-of-database-full-recovery-model"></a><span data-ttu-id="c4968-102">例:データベースの部分復元 (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="c4968-102">Example: Piecemeal Restore of Database (Full Recovery Model)</span></span>
  <span data-ttu-id="c4968-103">段階的な部分復元シーケンスでは、プライマリ ファイル グループとすべての読み書き可能なセカンダリ ファイル グループから順に、ファイル グループ レベルで段階的にデータベースが復元され、復旧されます。</span><span class="sxs-lookup"><span data-stu-id="c4968-103">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read-write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="c4968-104">この例では、障害発生後、データベース `adb` を新しいコンピューターに復元します。</span><span class="sxs-lookup"><span data-stu-id="c4968-104">In this example, database `adb` is restored to a new computer after a disaster.</span></span> <span data-ttu-id="c4968-105">データベースでは完全復旧モデルを使用しているため、復元を開始する前に、データベースのログ末尾のバックアップを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4968-105">The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database.</span></span> <span data-ttu-id="c4968-106">障害が発生する前は、すべてのファイル グループがオンラインです。</span><span class="sxs-lookup"><span data-stu-id="c4968-106">Before the disaster, all the filegroups are online.</span></span> <span data-ttu-id="c4968-107">ファイル グループ `B` は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="c4968-107">Filegroup `B` is read-only.</span></span> <span data-ttu-id="c4968-108">すべてのセカンダリ ファイル グループを復元する必要があります。ただし、これらのファイル グループは、重要度に従って `A` 、 `C`、 `B`の順に復元します (重要度が最も高いのは A です)。</span><span class="sxs-lookup"><span data-stu-id="c4968-108">All of the secondary filegroups must be restored, but they are restored in order of importance: `A` (highest), `C`, and lastly `B`.</span></span> <span data-ttu-id="c4968-109">この例では、ログ末尾のバックアップを含めて、4 つのログ バックアップがあるとします。</span><span class="sxs-lookup"><span data-stu-id="c4968-109">In this example, there are four log backups, including the tail-log backup.</span></span>  
  
## <a name="tail-log-backup"></a><span data-ttu-id="c4968-110">ログ末尾のバックアップ</span><span class="sxs-lookup"><span data-stu-id="c4968-110">Tail-Log Backup</span></span>  
 <span data-ttu-id="c4968-111">データベースの管理者は、データベースを復元する前に、ログの末尾をバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4968-111">Before restoring the database, the database administrator must back up the tail of the log.</span></span> <span data-ttu-id="c4968-112">データベースが破損しているため、ログ末尾のバックアップを作成するには、NO_TRUNCATE オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4968-112">Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:</span></span>  
  
```  
BACKUP LOG adb TO tailLogBackup WITH NORECOVERY, NO_TRUNCATE  
```  
  
 <span data-ttu-id="c4968-113">ログ末尾のバックアップは、次の復元シーケンスの最後に適用されます。</span><span class="sxs-lookup"><span data-stu-id="c4968-113">The tail-log backup is the last backup that is applied in the following restore sequences.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="c4968-114">復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="c4968-114">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4968-115">オンライン復元シーケンスでは、オフライン復元シーケンスと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4968-115">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="c4968-116">プライマリおよびセカンダリ ファイル グループ `A`の部分復元を行います。</span><span class="sxs-lookup"><span data-stu-id="c4968-116">Partial restore of the primary and secondary filegroup `A`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
       WITH PARTIAL, NORECOVERY  
    RESTORE DATABASE adb FILEGROUP='A' FROM backup2   
       WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
2.  <span data-ttu-id="c4968-117">ファイル グループ `C`をオンライン復元します。</span><span class="sxs-lookup"><span data-stu-id="c4968-117">Online restore of filegroup `C`.</span></span>  
  
     <span data-ttu-id="c4968-118">この時点で、プライマリ ファイル グループとセカンダリ ファイル グループ `A` はオンラインです。</span><span class="sxs-lookup"><span data-stu-id="c4968-118">At this point, the primary filegroup and secondary filegroup `A` are online.</span></span> <span data-ttu-id="c4968-119">ファイル グループ `B` とファイル グループ `C` のすべてのファイルは復旧が保留されており、ファイル グループはオフラインです。</span><span class="sxs-lookup"><span data-stu-id="c4968-119">All the files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
     <span data-ttu-id="c4968-120">最後の `RESTORE LOG` ステートメント (手順 1.) からのメッセージでは、ファイル グループ `C` が使用できないため、このファイル グループを含むトランザクションのロールバックに遅延が生じたことが示されています。</span><span class="sxs-lookup"><span data-stu-id="c4968-120">Messages from the last `RESTORE LOG` statement in step 1 indicate that rollback of transactions that involve filegroup `C` was deferred, because this filegroup is not available.</span></span> <span data-ttu-id="c4968-121">通常の操作は続行できますが、これらのトランザクションによってロックが保持され、ロールバックが完了するまで、ログの切り捨てが行われません。</span><span class="sxs-lookup"><span data-stu-id="c4968-121">Regular operations can continue, but locks are held by these transactions and log truncation will not occur until the rollback can complete.</span></span>  
  
     <span data-ttu-id="c4968-122">2 番目の復元シーケンスでは、データベース管理者がファイル グループ `C`を復元します。</span><span class="sxs-lookup"><span data-stu-id="c4968-122">In the second restore sequence, the database administrator restores filegroup `C`:</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' FROM backup2a WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="c4968-123">この時点で、プライマリ ファイル グループ、ファイル グループ `A` 、およびファイル グループ `C` はオンラインです。</span><span class="sxs-lookup"><span data-stu-id="c4968-123">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="c4968-124">ファイル グループ `B` はオフラインで、このファイル グループのファイルは復旧待ち状態のままです。</span><span class="sxs-lookup"><span data-stu-id="c4968-124">Files in filegroup `B` remain recovery pending, with the filegroup offline.</span></span> <span data-ttu-id="c4968-125">遅延トランザクションは解決され、ログの切り捨てが行われます。</span><span class="sxs-lookup"><span data-stu-id="c4968-125">Deferred transactions have been resolved, and log truncation occurs.</span></span>  
  
3.  <span data-ttu-id="c4968-126">ファイル グループ `B`をオンライン復元します。</span><span class="sxs-lookup"><span data-stu-id="c4968-126">Online restore of filegroup `B`.</span></span>  
  
     <span data-ttu-id="c4968-127">3 番目の復元シーケンスでは、データベース管理者がファイル グループ `B`を復元します。</span><span class="sxs-lookup"><span data-stu-id="c4968-127">In the third restore sequence, the database administrator restores filegroup `B`.</span></span> <span data-ttu-id="c4968-128">ファイル グループ `B` のバックアップは、ファイル グループ B が読み取り専用になってから行います。このため、復旧中にこのファイル グループをロールフォワードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c4968-128">The backup of filegroup `B` was taken after the filegroup became read-only; therefore, it does not have to be rolled forward during recovery.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup2b WITH RECOVERY  
    ```  
  
     <span data-ttu-id="c4968-129">すべてのファイル グループがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="c4968-129">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="c4968-130">その他の例</span><span class="sxs-lookup"><span data-stu-id="c4968-130">Additional Examples</span></span>  
  
-   [<span data-ttu-id="c4968-131">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="c4968-131">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="c4968-132">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="c4968-132">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="c4968-133">例: 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="c4968-133">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="c4968-134">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="c4968-134">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="c4968-135">例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="c4968-135">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="c4968-136">例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="c4968-136">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4968-137">参照</span><span class="sxs-lookup"><span data-stu-id="c4968-137">See Also</span></span>  
 <span data-ttu-id="c4968-138">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4968-138">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="c4968-139">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c4968-139">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="c4968-140">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c4968-140">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="c4968-141">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4968-141">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="c4968-142">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c4968-142">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
