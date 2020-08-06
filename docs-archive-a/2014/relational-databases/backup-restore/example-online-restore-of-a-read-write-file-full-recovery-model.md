---
title: '例 : 読み取り/書き込みファイルのオンライン復元 (完全復旧モデル) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 0dbeda81-1464-44ba-9011-914900096368
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5b99a3d97644c2a5f104173457f30fc5b3fd7188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632529"
---
# <a name="example-online-restore-of-a-read-write-file-full-recovery-model"></a><span data-ttu-id="99ecb-102">例:読み取り/書き込みファイルのオンライン復元 (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="99ecb-102">Example: Online Restore of a Read-Write File (Full Recovery Model)</span></span>
  <span data-ttu-id="99ecb-103">このトピックは、複数のファイルやファイル グループを含む、完全復旧モデルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに関連しています。</span><span class="sxs-lookup"><span data-stu-id="99ecb-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="99ecb-104">この例では、完全復旧モデルを使用する `adb`というデータベースに 3 つのファイル グループが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="99ecb-104">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="99ecb-105">ファイル グループ `A` は読み取り/書き込みが可能で、ファイル グループ `B` とファイル グループ `C` は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="99ecb-105">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="99ecb-106">最初は、すべてのファイル グループがオンラインです。</span><span class="sxs-lookup"><span data-stu-id="99ecb-106">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="99ecb-107">ファイル グループ `a1` のファイル `A` が損傷していると思われるので、データベース管理者は、データベースをオンライン状態のままで復元することにします。</span><span class="sxs-lookup"><span data-stu-id="99ecb-107">File `a1` in filegroup `A` appears to be damaged, and the database administrator decides to restore it while the database remains online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99ecb-108">単純復旧モデルでは、読み取り/書き込みデータをオンライン復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="99ecb-108">Under the simple recovery model, online restore of read/write data is not allowed.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="99ecb-109">復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="99ecb-109">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99ecb-110">オンライン復元シーケンスでは、オフライン復元シーケンスと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="99ecb-110">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="99ecb-111">ファイル `a1`をオンライン復元します。</span><span class="sxs-lookup"><span data-stu-id="99ecb-111">Online restore of file `a1`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILE='a1' FROM backup   
    WITH NORECOVERY;  
    ```  
  
     <span data-ttu-id="99ecb-112">この時点で、ファイル a1 は復元状態になり、ファイル グループ A はオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="99ecb-112">At this point, file a1 is in the RESTORING state, and filegroup A is offline.</span></span>  
  
2.  <span data-ttu-id="99ecb-113">ファイルの復元後、データベース管理者は新しいログ バックアップを行い、ファイルをオフラインにしたポイントがわかるようにしておきます。</span><span class="sxs-lookup"><span data-stu-id="99ecb-113">After restoring the file, the database administrator takes a new log backup to make sure that the point at which the file went offline is captured.</span></span>  
  
    ```  
    BACKUP LOG adb TO log_backup3;   
    ```  
  
3.  <span data-ttu-id="99ecb-114">ログ バックアップをオンライン復元します。</span><span class="sxs-lookup"><span data-stu-id="99ecb-114">Online restore of log backups.</span></span>  
  
     <span data-ttu-id="99ecb-115">復元したファイル バックアップ以降、最新のログ バックアップ (手順 2. で作成した*log_backup3*) までのすべてのログ バックアップを、管理者が復元します。</span><span class="sxs-lookup"><span data-stu-id="99ecb-115">The administrator restores all the log backups taken since the restored file backup, ending with the latest log backup (*log_backup3*, taken in step 2).</span></span> <span data-ttu-id="99ecb-116">最後のバックアップを復元した後、データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="99ecb-116">After the last backup is restored, the database is recovered.</span></span>  
  
    ```  
    RESTORE LOG adb FROM log_backup1 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup2 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup3 WITH NORECOVERY;  
    RESTORE LOG adb WITH RECOVERY;  
    ```  
  
     <span data-ttu-id="99ecb-117">ファイル `a1` がオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="99ecb-117">File `a1` is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="99ecb-118">その他の例</span><span class="sxs-lookup"><span data-stu-id="99ecb-118">Additional Examples</span></span>  
  
-   [<span data-ttu-id="99ecb-119">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="99ecb-119">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="99ecb-120">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="99ecb-120">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="99ecb-121">例: 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="99ecb-121">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="99ecb-122">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="99ecb-122">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="99ecb-123">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="99ecb-123">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="99ecb-124">例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="99ecb-124">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="99ecb-125">参照</span><span class="sxs-lookup"><span data-stu-id="99ecb-125">See Also</span></span>  
 <span data-ttu-id="99ecb-126">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99ecb-126">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="99ecb-127">[段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99ecb-127">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="99ecb-128">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="99ecb-128">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="99ecb-129">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99ecb-129">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="99ecb-130">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99ecb-130">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="99ecb-131">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="99ecb-131">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
