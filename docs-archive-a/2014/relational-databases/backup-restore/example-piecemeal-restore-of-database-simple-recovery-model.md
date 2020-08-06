---
title: データベースの段階的な部分復元 (単純復旧モデル) の例 | Microsoft Docs
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
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69de84fa2ff3a853eb9926549ad4859d2f1ae38e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720096"
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a><span data-ttu-id="8a669-102">例:データベースの部分復元 (単純復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="8a669-102">Example: Piecemeal Restore of Database (Simple Recovery Model)</span></span>
  <span data-ttu-id="8a669-103">段階的な部分復元シーケンスでは、プライマリ ファイル グループからすべての読み取り/書き込みセカンダリ ファイル グループの順に、ファイル グループ レベルで段階的にデータベースが復元および復旧されます。</span><span class="sxs-lookup"><span data-stu-id="8a669-103">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="8a669-104">この例では、障害発生後、データベース `adb` を新しいコンピューターに復元します。</span><span class="sxs-lookup"><span data-stu-id="8a669-104">In this example, database `adb` is restored to a new computer after a disaster.</span></span> <span data-ttu-id="8a669-105">このデータベースでは、単純復旧モデルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="8a669-105">The database is using the simple recovery model.</span></span> <span data-ttu-id="8a669-106">障害が発生する前は、すべてのファイル グループがオンラインです。</span><span class="sxs-lookup"><span data-stu-id="8a669-106">Before the disaster, all the filegroups are online.</span></span> <span data-ttu-id="8a669-107">ファイル グループ `A` とファイル グループ `C` は読み取り/書き込みが可能で、ファイル グループ `B` は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="8a669-107">Filegroups `A` and `C` are read/write, and filegroup `B` is read-only.</span></span> <span data-ttu-id="8a669-108">ファイル グループ `B` は、最新の部分バックアップを実行する前に読み取り専用になりました。この部分バックアップには、プライマリ ファイル グループと読み取りと書き込みが可能なセカンダリ ファイル グループ `A` と `C`が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8a669-108">Filegroup `B` became read-only before the most recent partial backup, which contains the primary filegroup and the read/write secondary filegroups, `A` and `C`.</span></span> <span data-ttu-id="8a669-109">ファイル グループ `B` が読み取り専用になった後、ファイル グループ `B` の別のファイル バックアップが作成されました。</span><span class="sxs-lookup"><span data-stu-id="8a669-109">After filegroup `B` became read-only, a separate file backup of filegroup `B` was taken.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="8a669-110">復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="8a669-110">Restore Sequences</span></span>  
  
1.  <span data-ttu-id="8a669-111">プライマリ ファイル グループ、ファイル グループ `A` 、およびファイル グループ `C`の部分復元を行います。</span><span class="sxs-lookup"><span data-stu-id="8a669-111">Partial restore of the primary and filegroups `A` and `C`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     <span data-ttu-id="8a669-112">この時点で、プライマリ ファイル グループ、ファイル グループ `A` 、およびファイル グループ `C` はオンラインです。</span><span class="sxs-lookup"><span data-stu-id="8a669-112">At this point, the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="8a669-113">ファイル グループ `B` のすべてのファイルは復旧待ち状態なので、このファイル グループはオフラインです。</span><span class="sxs-lookup"><span data-stu-id="8a669-113">All files in filegroup `B` are recovery pending, and the filegroup is offline.</span></span>  
  
2.  <span data-ttu-id="8a669-114">ファイル グループ `B`をオンライン復元します。</span><span class="sxs-lookup"><span data-stu-id="8a669-114">Online restore of filegroup `B`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     <span data-ttu-id="8a669-115">すべてのファイル グループがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="8a669-115">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="8a669-116">その他の例</span><span class="sxs-lookup"><span data-stu-id="8a669-116">Additional Examples</span></span>  
  
-   [<span data-ttu-id="8a669-117">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="8a669-117">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="8a669-118">例: 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="8a669-118">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="8a669-119">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="8a669-119">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="8a669-120">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="8a669-120">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="8a669-121">例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="8a669-121">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="8a669-122">例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="8a669-122">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a669-123">参照</span><span class="sxs-lookup"><span data-stu-id="8a669-123">See Also</span></span>  
 <span data-ttu-id="8a669-124">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8a669-124">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="8a669-125">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a669-125">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="8a669-126">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a669-126">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="8a669-127">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8a669-127">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
