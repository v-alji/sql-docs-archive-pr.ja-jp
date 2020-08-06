---
title: 部分バックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- partial backups [SQL Server]
- READ_WRITE_FILEGROUPS option
- database backups [SQL Server], about backing up databases
ms.assetid: fe6b6bb1-38d0-46c4-bab8-31df14e8999c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c03cf2fb4d3af6fe87459e881e26c48cfacc232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643441"
---
# <a name="partial-backups-sql-server"></a><span data-ttu-id="aab9c-102">部分バックアップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="aab9c-102">Partial Backups (SQL Server)</span></span>
  <span data-ttu-id="aab9c-103">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 復旧モデルで部分バックアップがサポートされるため、このトピックの内容はすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="aab9c-103">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recovery models support partial backups, so this topic is relevant for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="aab9c-104">ただし、部分バックアップは、1 つ以上の読み取り専用のファイル グループを含む非常に大きなデータベースをバックアップする場合の柔軟性を向上するために、単純復旧モデルで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="aab9c-104">However, partial backups are designed for use under the simple recovery model to improve flexibility for backing up very large databases that contain one or more read-only filegroups.</span></span>  
  
 <span data-ttu-id="aab9c-105">読み取り専用のファイル グループを除外する場合は、部分バックアップが有効です。</span><span class="sxs-lookup"><span data-stu-id="aab9c-105">Partial backups are useful whenever you want to exclude read-only filegroups.</span></span> <span data-ttu-id="aab9c-106">*部分バックアップ* はデータベースの完全バックアップに似ていますが、部分バックアップには一部のファイル グループが含まれません。</span><span class="sxs-lookup"><span data-stu-id="aab9c-106">A *partial backup* resembles a full database backup, but a partial backup does not contain all the filegroups.</span></span> <span data-ttu-id="aab9c-107">部分バックアップに含まれるデータは、読み取り/書き込み可能なデータベースの場合、プライマリ ファイル グループのデータ、読み取りと書き込みが可能なすべてのファイル グループのデータ、および必要に応じて指定された読み取り専用ファイルのデータです。</span><span class="sxs-lookup"><span data-stu-id="aab9c-107">Instead, for a read-write database, a partial backup contains the data in the primary filegroup, every read-write filegroup, and, optionally, one or more read-only files.</span></span> <span data-ttu-id="aab9c-108">読み取り専用データベースの部分バックアップには、プライマリ ファイル グループのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aab9c-108">A partial backup of a read-only database contains only the primary filegroup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aab9c-109">部分バックアップの後に、読み取り専用のデータベースを読み取り/書き込み可能に変更すると、部分バックアップには含まれない、読み取り/書き込みセカンダリ ファイル グループが存在することになります。</span><span class="sxs-lookup"><span data-stu-id="aab9c-109">If a read-only database is changed to read/write after a partial backup, there might be read/write secondary filegroups that are not in the partial backup.</span></span> <span data-ttu-id="aab9c-110">この場合、部分的な差分バックアップの実行を試みると、バックアップに失敗します。</span><span class="sxs-lookup"><span data-stu-id="aab9c-110">In this case, if you try to take a differential partial backup, the backup fails.</span></span> <span data-ttu-id="aab9c-111">データベースの部分的な差分バックアップを実行する前に、別の部分バックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aab9c-111">Before you can take a differential partial backup of the database, you must take another partial backup.</span></span> <span data-ttu-id="aab9c-112">新しい部分バックアップには、すべての読み取り/書き込みセカンダリ ファイル グループが含まれるので、このバックアップを部分的な差分バックアップのベースにすることができます。</span><span class="sxs-lookup"><span data-stu-id="aab9c-112">The new partial backup contains every read/write secondary filegroup and can serve as the base for differential partial backups.</span></span>  
  
 <span data-ttu-id="aab9c-113">読み取り専用ファイル グループのファイル バックアップは、部分バックアップと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="aab9c-113">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="aab9c-114">ファイルのバックアップの詳細については、「[ファイルの完全バックアップ &#40;SQL Server&#41;](full-file-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aab9c-114">For information about file backups, see [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="aab9c-115">部分バックアップは、部分的な差分バックアップの *差分ベース* として使用できます。</span><span class="sxs-lookup"><span data-stu-id="aab9c-115">A partial backup can serve as the *differential base* for differential partial backups.</span></span> <span data-ttu-id="aab9c-116">詳細については、「 [差分バックアップ &#40;SQL Server&#41;](differential-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aab9c-116">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="aab9c-117">関連タスク</span><span class="sxs-lookup"><span data-stu-id="aab9c-117">Related Tasks</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aab9c-118">部分バックアップは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはメンテナンス プラン ウィザードではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="aab9c-118">Partial backups are not supported by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the Maintenance Plan Wizard.</span></span>  
  
 <span data-ttu-id="aab9c-119">**部分バックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="aab9c-119">**To create a partial backup**</span></span>  
  
-   <span data-ttu-id="aab9c-120">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (必要に応じて READ_WRITE_FILEGROUPS; FILEGROUP オプションを使用)</span><span class="sxs-lookup"><span data-stu-id="aab9c-120">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (READ_WRITE_FILEGROUPS; FILEGROUP option, if needed)</span></span>  
  
 <span data-ttu-id="aab9c-121">**復元シーケンスで部分バックアップを使用するには**</span><span class="sxs-lookup"><span data-stu-id="aab9c-121">**To use a partial backup in a restore sequence**</span></span>  
  
-   [<span data-ttu-id="aab9c-122">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="aab9c-122">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="aab9c-123">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="aab9c-123">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="aab9c-124">参照</span><span class="sxs-lookup"><span data-stu-id="aab9c-124">See Also</span></span>  
 <span data-ttu-id="aab9c-125">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aab9c-125">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="aab9c-126">[ファイルの復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="aab9c-126">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="aab9c-127">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="aab9c-127">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
