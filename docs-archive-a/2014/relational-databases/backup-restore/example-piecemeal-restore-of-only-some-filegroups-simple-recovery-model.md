---
title: 一部のファイル グループのみを復元する段階的な部分復元 (単純復旧モデル) の例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: d7ad026c-5355-4308-9560-0dc843940d4f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8254ac96a269b6fb433759e5a649bf9df1b7feac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742317"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model"></a><span data-ttu-id="43ea6-102">例:一部のファイル グループのみを復元する段階的な部分復元 (単純復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="43ea6-102">Example: Piecemeal Restore of Only Some Filegroups (Simple Recovery Model)</span></span>
  <span data-ttu-id="43ea6-103">このトピックは、読み取り専用のファイル グループを含む、単純復旧モデルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに関連しています。</span><span class="sxs-lookup"><span data-stu-id="43ea6-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the simple recovery model that contain a read-only filegroup.</span></span>  
  
 <span data-ttu-id="43ea6-104">段階的な部分復元シーケンスでは、プライマリ ファイル グループからすべての読み取り/書き込みセカンダリ ファイル グループの順に、ファイル グループレベルで段階的にデータベースが復元および復旧されます。</span><span class="sxs-lookup"><span data-stu-id="43ea6-104">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="43ea6-105">この例では、単純復旧モデルを使用する `adb`というデータベースに 3 つのファイル グループが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="43ea6-105">In this example, a database named `adb`, which uses the simple recovery model, contains three filegroups.</span></span> <span data-ttu-id="43ea6-106">ファイル グループ `A` は読み取り/書き込みが可能で、ファイル グループ `B` とファイル グループ `C` は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="43ea6-106">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="43ea6-107">最初は、すべてのファイル グループがオンラインです。</span><span class="sxs-lookup"><span data-stu-id="43ea6-107">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="43ea6-108">データベース `B` のプライマリ ファイル グループとファイル グループ `adb` が破損しているようなので、データベース管理者は段階的な部分復元シーケンスを使用して、これらを復元することにしました。</span><span class="sxs-lookup"><span data-stu-id="43ea6-108">The primary and filegroup `B` of database `adb` appear to be damaged; therefore, the database administrator decides to restore them by using a piecemeal restore sequence.</span></span> <span data-ttu-id="43ea6-109">単純復旧モデルでは、すべての読み取り/書き込みファイル グループは、同じ部分バックアップから復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43ea6-109">Under the simple recovery model, all read/write filegroups must be restored from the same partial backup.</span></span> <span data-ttu-id="43ea6-110">ファイル グループ `A` は破損していませんが、プライマリ ファイル グループと共に復元して一貫性を維持する必要があります (データベースは前回の部分バックアップの末尾で定義されている時点まで復元されます)。</span><span class="sxs-lookup"><span data-stu-id="43ea6-110">Although filegroup `A` is intact, it must be restored with the primary filegroup to make sure that they are consistent (the database will be restored to the point in time defined by the end of the last partial backup).</span></span> <span data-ttu-id="43ea6-111">ファイル グループ `C` も破損していませんが、復旧してオンラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43ea6-111">Filegroup `C` is intact, but it must be recovered to bring it online.</span></span> <span data-ttu-id="43ea6-112">ファイル グループ `B`は破損していますが、ファイル グループ `C`に比べて重要なデータが少ないため、最後に `B` を復元します。</span><span class="sxs-lookup"><span data-stu-id="43ea6-112">Filegroup `B`, although damaged, contains less critical data than Filegroup `C`; therefore, `B` will be restored last.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="43ea6-113">復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="43ea6-113">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="43ea6-114">オンライン復元シーケンスでは、オフライン復元シーケンスと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="43ea6-114">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="43ea6-115">部分バックアップからプライマリ ファイル グループとファイル グループ `A` を部分復元します。</span><span class="sxs-lookup"><span data-stu-id="43ea6-115">Partial restore of the primary and filegroup `A` from a partial backup.</span></span>  
  
    ```  
    RESTORE DATABASE adb READ_WRITE_FILEGROUPS FROM partial_backup   
    WITH PARTIAL, RECOVERY  
    ```  
  
     <span data-ttu-id="43ea6-116">この時点では、プライマリ ファイル グループとファイル グループ `A` がオンラインです。</span><span class="sxs-lookup"><span data-stu-id="43ea6-116">At this point the primary filegroup and filegroup `A` are online.</span></span> <span data-ttu-id="43ea6-117">ファイル グループ `B` と `C` のファイルは、復旧待ち状態なので、オフラインです。</span><span class="sxs-lookup"><span data-stu-id="43ea6-117">Files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
2.  <span data-ttu-id="43ea6-118">ファイル グループ `C`をオンライン復旧します。</span><span class="sxs-lookup"><span data-stu-id="43ea6-118">Online recovery of filegroup `C`.</span></span>  
  
     <span data-ttu-id="43ea6-119">上記で復元された部分バックアップはファイル グループ `C` が読み取り専用になった後で作成されているため、復元によりデータベースがある時点の状態に戻されていても、ファイル グループ `C` の一貫性は維持されます。</span><span class="sxs-lookup"><span data-stu-id="43ea6-119">Filegroup `C` is consistent because the partial backup that was restored above was taken after filegroup `C` became read-only, although the database was taken back in time by the restore.</span></span> <span data-ttu-id="43ea6-120">データベース管理者は、ファイル グループ `C`を復元せずにそのままオンラインに復旧します。</span><span class="sxs-lookup"><span data-stu-id="43ea6-120">The database administrator recovers the filegroup `C`, without restoring it, to bring it online.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' WITH RECOVERY  
    ```  
  
     <span data-ttu-id="43ea6-121">この時点で、プライマリ ファイル グループ、ファイル グループ `A` 、およびファイル グループ `C` はオンラインです。</span><span class="sxs-lookup"><span data-stu-id="43ea6-121">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="43ea6-122">ファイル グループ B のファイルは復旧が保留になったままで、ファイル グループはオフラインになっています。</span><span class="sxs-lookup"><span data-stu-id="43ea6-122">Files in filegroupB remain recovery pending, with the filegroup offline.</span></span>  
  
3.  <span data-ttu-id="43ea6-123">ファイル グループ  をオンライン復元します。 `B.`</span><span class="sxs-lookup"><span data-stu-id="43ea6-123">Online restore of filegroup `B.`</span></span>  
  
     <span data-ttu-id="43ea6-124">ファイル グループ `B` のファイルは、復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43ea6-124">Files in filegroup `B` must be restored.</span></span> <span data-ttu-id="43ea6-125">データベース管理者は、ファイル グループ `B` が読み取り専用になってから部分バックアップが作成されるまでの間に作成されたファイル グループ `B` のバックアップから、復元を行います。</span><span class="sxs-lookup"><span data-stu-id="43ea6-125">The database administrator restores the backup of filegroup `B` taken after filegroup `B` became read-only and before the partial backup.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup   
    WITH RECOVERY  
    ```  
  
     <span data-ttu-id="43ea6-126">すべてのファイル グループがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="43ea6-126">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="43ea6-127">その他の例</span><span class="sxs-lookup"><span data-stu-id="43ea6-127">Additional Examples</span></span>  
  
-   [<span data-ttu-id="43ea6-128">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="43ea6-128">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="43ea6-129">例: 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="43ea6-129">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="43ea6-130">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="43ea6-130">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="43ea6-131">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="43ea6-131">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="43ea6-132">例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="43ea6-132">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="43ea6-133">例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="43ea6-133">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="43ea6-134">参照</span><span class="sxs-lookup"><span data-stu-id="43ea6-134">See Also</span></span>  
 <span data-ttu-id="43ea6-135">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="43ea6-135">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="43ea6-136">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43ea6-136">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="43ea6-137">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43ea6-137">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="43ea6-138">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="43ea6-138">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
