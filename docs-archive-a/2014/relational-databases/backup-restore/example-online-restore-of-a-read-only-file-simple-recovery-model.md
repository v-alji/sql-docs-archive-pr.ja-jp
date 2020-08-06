---
title: '例 : 読み取り専用ファイルのオンライン復元 (単純復旧モデル) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restore sequences [SQL Server], online
- online restores [SQL Server], simple recovery model
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d84c920a2cb40866ba106b4d30d8e24c4caea611
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742325"
---
# <a name="example-online-restore-of-a-read-only-file-simple-recovery-model"></a><span data-ttu-id="9ce08-102">例:読み取り専用ファイルのオンライン復元 (単純復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="9ce08-102">Example: Online Restore of a Read-Only File (Simple Recovery Model)</span></span>
  <span data-ttu-id="9ce08-103">このトピックは、読み取り専用のファイル グループを含む、単純復旧モデルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに関連しています。</span><span class="sxs-lookup"><span data-stu-id="9ce08-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the simple recovery model that contain a read-only filegroup.</span></span> <span data-ttu-id="9ce08-104">単純復旧モデルでは、ファイルが最後に読み取り専用になってから作成されたファイル バックアップが存在する場合、読み取り専用ファイルをオンラインに復元できます。</span><span class="sxs-lookup"><span data-stu-id="9ce08-104">Under the simple recovery model, a read-only file can be restored online if a file backup exists that was taken since the file became read-only for the last time.</span></span>  
  
 <span data-ttu-id="9ce08-105">この例では、 `adb` というデータベースに 3 つのファイル グループが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="9ce08-105">In this example, a database named `adb` contains three filegroups.</span></span> <span data-ttu-id="9ce08-106">ファイル グループ `A` は読み取り/書き込みが可能で、ファイル グループ `B` とファイル グループ `C` は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="9ce08-106">Filegroup `A` is read/write, and filegroups `B` and `C` are read-only.</span></span> <span data-ttu-id="9ce08-107">最初は、すべてのファイル グループがオンラインです。</span><span class="sxs-lookup"><span data-stu-id="9ce08-107">Initially, all of the filegroups are online.</span></span> <span data-ttu-id="9ce08-108">ファイル グループ `B`の読み取り専用ファイル `b1`を復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce08-108">A read-only file in filegroup `B`, `b1`, has to be restored.</span></span> <span data-ttu-id="9ce08-109">データベース管理者は、ファイルが読み取り専用になった後で作成されたバックアップを使用して、このファイルを復元できます。</span><span class="sxs-lookup"><span data-stu-id="9ce08-109">The database administrator can restore it by using a backup that was taken after the file became read-only.</span></span> <span data-ttu-id="9ce08-110">復元の間、ファイル グループ `B` はオフラインになりますが、データベースの残りのファイル グループはオンライン状態で維持されます。</span><span class="sxs-lookup"><span data-stu-id="9ce08-110">For the duration of the restore, filegroup `B` will be offline, but the remainder of the database will remain online.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="9ce08-111">復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="9ce08-111">Restore Sequence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ce08-112">オンライン復元シーケンスでは、オフライン復元シーケンスと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce08-112">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
 <span data-ttu-id="9ce08-113">ファイルを復元するには、データベース管理者が次の復元シーケンスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce08-113">To restore the file, the database administrator uses the following restore sequence:</span></span>  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 <span data-ttu-id="9ce08-114">ファイルがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="9ce08-114">The file is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="9ce08-115">その他の例</span><span class="sxs-lookup"><span data-stu-id="9ce08-115">Additional Examples</span></span>  
  
-   [<span data-ttu-id="9ce08-116">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce08-116">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="9ce08-117">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce08-117">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="9ce08-118">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce08-118">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="9ce08-119">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce08-119">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="9ce08-120">例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce08-120">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="9ce08-121">例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce08-121">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ce08-122">参照</span><span class="sxs-lookup"><span data-stu-id="9ce08-122">See Also</span></span>  
 <span data-ttu-id="9ce08-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9ce08-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="9ce08-124">[段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9ce08-124">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="9ce08-125">[ファイルの復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="9ce08-125">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="9ce08-126">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9ce08-126">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="9ce08-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce08-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
