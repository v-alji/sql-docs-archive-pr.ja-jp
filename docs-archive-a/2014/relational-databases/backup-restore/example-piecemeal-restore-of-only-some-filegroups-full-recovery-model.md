---
title: 一部のファイル グループのみを復元する段階的な部分復元 (完全復旧モデル) の例 | Microsoft Docs
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
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b3cb1a5ea33a5016c99fdf1f5a7f4e892c045b59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742318"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-full-recovery-model"></a><span data-ttu-id="dc0cf-102">例:一部のファイル グループのみを復元する段階的な部分復元 (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="dc0cf-102">Example: Piecemeal Restore of Only Some Filegroups (Full Recovery Model)</span></span>
  <span data-ttu-id="dc0cf-103">このトピックは、複数のファイルやファイル グループを含む、完全復旧モデルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに関連しています。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="dc0cf-104">段階的な部分復元シーケンスでは、プライマリ ファイル グループからすべての読み取り/書き込みセカンダリ ファイル グループの順に、ファイル グループ レベルで段階的にデータベースが復元および復旧されます。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-104">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="dc0cf-105">この例では、完全復旧モデルを使用する `adb`というデータベースに 3 つのファイル グループが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-105">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="dc0cf-106">ファイル グループ `A` は読み取り/書き込みが可能で、ファイル グループ `B` とファイル グループ `C` は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-106">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="dc0cf-107">最初は、すべてのファイル グループがオンラインです。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-107">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="dc0cf-108">データベース `B` のプライマリ ファイル グループとファイル グループ `adb` が破損しているようです。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-108">The primary and filegroup `B` of database `adb` appear to be damaged.</span></span> <span data-ttu-id="dc0cf-109">プライマリ ファイル グループは比較的サイズが小さいので、すぐに復元できます。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-109">The primary filegroup is fairly small and can be restored quickly.</span></span> <span data-ttu-id="dc0cf-110">データベース管理者は、段階的な部分復元シーケンスを使用して、これらのファイル グループを復元することにしました。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-110">The database administrator decides to restore them by using a piecemeal restore sequence.</span></span> <span data-ttu-id="dc0cf-111">まず、プライマリ ファイル グループと後続のトランザクション ログを復元し、データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-111">First, the primary filegroup and the subsequent transaction logs are restored the database is recovered.</span></span>  
  
 <span data-ttu-id="dc0cf-112">変更されていないファイル グループ `A` と `C` には重要なデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-112">The intact filegroups `A` and `C` contain critical data.</span></span> <span data-ttu-id="dc0cf-113">そのため、次にこれらのファイル グループをできるだけ早く復元して、オンラインにします。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-113">Therefore, they will be recovered next to bring them online as quickly as possible.</span></span> <span data-ttu-id="dc0cf-114">最後に、破損したセカンダリ ファイル グループ `B`を復元および復旧します。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-114">Finally, the damaged secondary filegroup, `B`, is restored and recovered.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="dc0cf-115">復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="dc0cf-115">Restore Sequences:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc0cf-116">オンライン復元シーケンスでは、オフライン復元シーケンスと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-116">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="dc0cf-117">データベース `adb`のログ末尾のバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-117">Create a tail log backup of database `adb`.</span></span> <span data-ttu-id="dc0cf-118">データベースの復旧ポイントに対して、破損していないファイル グループ `A` および `C` を最新の状態にするには、この手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-118">This step is essential to make the intact filegroups `A` and `C` current with the recovery point of the database.</span></span>  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  <span data-ttu-id="dc0cf-119">プライマリ ファイル グループの部分復元を行います。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-119">Partial restore of the primary filegroup.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="dc0cf-120">この時点では、プライマリ ファイル グループはオンラインです。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-120">At this point the primary is online.</span></span> <span data-ttu-id="dc0cf-121">ファイル グループ `A`、 `B`、および `C` はオフラインで、これらのファイル グループのファイルは復旧待ち状態です。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-121">Files in filegroups `A`, `B`, and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
3.  <span data-ttu-id="dc0cf-122">ファイル グループ `A` と `C`をオンライン復元します。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-122">Online restore of filegroups `A` and `C`.</span></span>  
  
     <span data-ttu-id="dc0cf-123">これらのファイル グループのデータは破損していないため、バックアップから復元する必要はありません。ただし、これらのファイル グループをオンラインにするために、復旧する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-123">Because their data is undamaged, these filegroups do not have to be restored from a backup, but they do have to be recovered to bring them online.</span></span>  
  
     <span data-ttu-id="dc0cf-124">データベース管理者は、すぐにファイル グループ `A` と `C` を復旧します。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-124">The database administrator recovers `A` and `C` immediately.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     <span data-ttu-id="dc0cf-125">この時点で、プライマリ ファイル グループ、ファイル グループ `A` 、およびファイル グループ `C` はオンラインです。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-125">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="dc0cf-126">ファイル グループ `B` はオフラインで、このファイル グループのファイルは復旧待ち状態のままです。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-126">Files in filegroup `B` remain recovery pending, with the filegroup offline.</span></span>  
  
4.  <span data-ttu-id="dc0cf-127">ファイル グループ `B`をオンライン復元します。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-127">Online restore of filegroup `B`.</span></span>  
  
     <span data-ttu-id="dc0cf-128">ファイル グループ `B` のファイルは、これ以降の任意の時点で復元します。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-128">Files in filegroup `B` are restored any time thereafter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc0cf-129">ファイル グループ `B` のバックアップは、ファイルをロールフォワードする必要がないように、ファイル グループ B が読み取り専用になってから行います。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-129">The backup of filegroup `B` was taken after the filegroup became read-only; therefore, these files do not have to be rolled forward.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="dc0cf-130">すべてのファイル グループがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="dc0cf-130">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="dc0cf-131">その他の例</span><span class="sxs-lookup"><span data-stu-id="dc0cf-131">Additional Examples</span></span>  
  
-   [<span data-ttu-id="dc0cf-132">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="dc0cf-132">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="dc0cf-133">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="dc0cf-133">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="dc0cf-134">例: 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="dc0cf-134">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="dc0cf-135">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="dc0cf-135">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="dc0cf-136">例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="dc0cf-136">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="dc0cf-137">例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="dc0cf-137">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="dc0cf-138">参照</span><span class="sxs-lookup"><span data-stu-id="dc0cf-138">See Also</span></span>  
 <span data-ttu-id="dc0cf-139">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc0cf-139">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="dc0cf-140">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dc0cf-140">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="dc0cf-141">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dc0cf-141">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="dc0cf-142">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc0cf-142">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="dc0cf-143">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dc0cf-143">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
