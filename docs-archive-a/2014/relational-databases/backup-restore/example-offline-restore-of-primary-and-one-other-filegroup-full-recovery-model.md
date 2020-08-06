---
title: '例: プライマリファイルグループと他のファイルグループを1つオフラインで復元する (完全復旧モデル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- offline restores [SQL Server]
- restore sequences [SQL Server], offline
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f845927fdd74fba476139fccbf9a5fa112d434e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644483"
---
# <a name="example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model"></a><span data-ttu-id="ad6f7-102">例:プライマリ ファイル グループと他のファイル グループを 1 つオフラインで復元する (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="ad6f7-102">Example: Offline Restore of Primary and One Other Filegroup (Full Recovery Model)</span></span>
  <span data-ttu-id="ad6f7-103">このトピックは、複数のファイル グループを含む、完全復旧モデルのデータベースだけに関連しています。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-103">This topic is relevant only for databases under the full recovery model that contain multiple filegroups.</span></span>  
  
 <span data-ttu-id="ad6f7-104">この例では、 `adb` というデータベースに 3 つのファイル グループが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-104">In this example, a database named `adb` contains three filegroups.</span></span> <span data-ttu-id="ad6f7-105">ファイル グループ `A` とファイル グループ `C` は読み取り/書き込みが可能で、ファイル グループ `B` は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-105">Filegroups `A` and `C` are read/write, and filegroup `B` is read-only.</span></span> <span data-ttu-id="ad6f7-106">プライマリ ファイル グループとファイル グループ `B` は破損していますが、ファイル グループ `A` とファイル グループ `C` は破損していません。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-106">The primary filegroup and filegroup `B` are damaged, but filegroups `A` and `C` are intact.</span></span> <span data-ttu-id="ad6f7-107">障害が発生する前は、すべてのファイル グループがオンラインになっていました。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-107">Before the disaster, all the filegroups were online.</span></span>  
  
 <span data-ttu-id="ad6f7-108">データベース管理者は、プライマリ ファイル グループとファイル グループ `B`を復元および復旧することにしました。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-108">The database administrator decides to restore and recover the primary filegroup and filegroup `B`.</span></span> <span data-ttu-id="ad6f7-109">データベースでは完全復旧モデルを使用しているため、復元を開始する前に、データベースのログ末尾のバックアップを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-109">The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database.</span></span> <span data-ttu-id="ad6f7-110">データベースがオンラインになると、ファイル グループ `A` とファイル グループ `C` は自動的にオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-110">When the database comes on line, Filegroups `A` and `C` are automatically brought online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad6f7-111">オフライン復元シーケンスは、読み取り専用ファイルのオンライン復元の場合に比べ、少ない手順で済みます。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-111">The offline restore sequence has fewer steps than an online restore of a read-only file.</span></span> <span data-ttu-id="ad6f7-112">例については、「[読み取り専用ファイルのオンライン復元の例 &#40;完全復旧モデル&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-112">For an example, see [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md).</span></span> <span data-ttu-id="ad6f7-113">ただし、オフライン復元中は、データベース全体がオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-113">However, the whole database is offline for the duration of the sequence.</span></span>  
  
## <a name="tail-log-backup"></a><span data-ttu-id="ad6f7-114">ログ末尾のバックアップ</span><span class="sxs-lookup"><span data-stu-id="ad6f7-114">Tail-Log Backup</span></span>  
 <span data-ttu-id="ad6f7-115">データベースの管理者は、データベースを復元する前に、ログの末尾をバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-115">Before restoring the database, the database administrator must back up the tail of the log.</span></span> <span data-ttu-id="ad6f7-116">データベースが破損しているため、ログ末尾のバックアップを作成するには、NO_TRUNCATE オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-116">Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:</span></span>  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 <span data-ttu-id="ad6f7-117">ログ末尾のバックアップは、次の復元シーケンスの最後に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-117">The tail-log backup is the last backup that is applied in the following restore sequences.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="ad6f7-118">復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="ad6f7-118">Restore Sequence</span></span>  
 <span data-ttu-id="ad6f7-119">プライマリ ファイル グループとファイル グループ `B`を復元するために、データベース管理者は、次に示すように、PARTIAL オプションを使用せずに復元シーケンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-119">To restore the primary filegroup and filegroup `B`, the database administrator uses a restore sequence without the PARTIAL option, as follows:</span></span>  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 <span data-ttu-id="ad6f7-120">復元しないファイルは、自動的にオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-120">The files that are not restored are automatically brought online.</span></span> <span data-ttu-id="ad6f7-121">これで、すべてのファイル グループがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="ad6f7-121">All the filegroups are now online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6f7-122">参照</span><span class="sxs-lookup"><span data-stu-id="ad6f7-122">See Also</span></span>  
 <span data-ttu-id="ad6f7-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad6f7-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="ad6f7-124">[段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad6f7-124">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="ad6f7-125">[ファイルの復元 &#40;完全復旧モデル&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="ad6f7-125">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="ad6f7-126">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad6f7-126">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="ad6f7-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ad6f7-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
