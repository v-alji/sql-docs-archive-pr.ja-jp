---
title: 読み取り専用ファイルのオンライン復元の例 (完全復旧モデル) | Microsoft Docs
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
ms.assetid: 7ea2d2af-086f-48dc-9636-38dc194c7090
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f493c88d64e6ed22e44f33f1442ae581daa8ed4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742326"
---
# <a name="example-online-restore-of-a-read-only-file-full-recovery-model"></a><span data-ttu-id="0d9f0-102">例:読み取り専用ファイルのオンライン復元 (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="0d9f0-102">Example: Online Restore of a Read-Only File (Full Recovery Model)</span></span>
  <span data-ttu-id="0d9f0-103">このトピックは、複数のファイルやファイル グループを含む、完全復旧モデルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに関連しています。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="0d9f0-104">この例では、完全復旧モデルを使用する `adb`というデータベースに 3 つのファイル グループが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-104">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="0d9f0-105">ファイル グループ `A` は読み取り/書き込みが可能で、ファイル グループ `B` とファイル グループ `C` は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-105">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="0d9f0-106">最初は、すべてのファイル グループがオンラインです。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-106">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="0d9f0-107">データベース `b1`のファイル グループ `B` に含まれている読み取り専用ファイル `adb` を復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-107">A read-only file, `b1`, in filegroup `B` of database `adb` has to be restored.</span></span> <span data-ttu-id="0d9f0-108">ファイルが読み取り専用になってからバックアップを行ったので、ログ バックアップは不要です。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-108">A backup was taken since the file became read-only; therefore, log backups are not required.</span></span> <span data-ttu-id="0d9f0-109">復元の間、ファイル グループ `B` はオフラインになりますが、データベースの残りの部分はオンライン状態で維持されます。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-109">Filegroup `B` is offline for the duration of the restore, but the remainder of the database remains online.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="0d9f0-110">復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="0d9f0-110">Restore Sequence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d9f0-111">オンライン復元シーケンスでは、オフライン復元シーケンスと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-111">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
 <span data-ttu-id="0d9f0-112">ファイルを復元するには、データベース管理者が次の復元シーケンスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-112">To restore the file, the database administrator uses the following restore sequence:</span></span>  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup  
WITH RECOVERY   
```  
  
 <span data-ttu-id="0d9f0-113">ファイル B がオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="0d9f0-113">Filegroup B is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="0d9f0-114">その他の例</span><span class="sxs-lookup"><span data-stu-id="0d9f0-114">Additional Examples</span></span>  
  
-   [<span data-ttu-id="0d9f0-115">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="0d9f0-115">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="0d9f0-116">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="0d9f0-116">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="0d9f0-117">例: 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="0d9f0-117">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="0d9f0-118">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="0d9f0-118">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="0d9f0-119">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="0d9f0-119">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="0d9f0-120">例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="0d9f0-120">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="0d9f0-121">参照</span><span class="sxs-lookup"><span data-stu-id="0d9f0-121">See Also</span></span>  
 <span data-ttu-id="0d9f0-122">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0d9f0-122">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="0d9f0-123">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0d9f0-123">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="0d9f0-124">[ファイルの復元 &#40;完全復旧モデル&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="0d9f0-124">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="0d9f0-125">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0d9f0-125">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
