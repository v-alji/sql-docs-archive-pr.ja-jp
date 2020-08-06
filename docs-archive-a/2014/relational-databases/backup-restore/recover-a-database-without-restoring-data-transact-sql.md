---
title: データを復元しないデータベースの復旧 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], recovery-only
- recovery-only scenario [SQL Server]
- restoring databases [SQL Server], recovery-only
- recovery [SQL Server], recovery-only
- database recovery [SQL Server]
- database restores [SQL Server], recovery-only
- recovery [SQL Server], without restoring data
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 04e4f78e51adb803bb65530c0b3b903aa7f76419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643439"
---
# <a name="recover-a-database-without-restoring-data-transact-sql"></a><span data-ttu-id="37c08-102">データを復元しないデータベースの復旧 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="37c08-102">Recover a Database Without Restoring Data (Transact-SQL)</span></span>
  <span data-ttu-id="37c08-103">通常、データベースを復旧する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのすべてのデータを復元します。</span><span class="sxs-lookup"><span data-stu-id="37c08-103">Usually, all of the data in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is restored before the database is recovered.</span></span> <span data-ttu-id="37c08-104">ただし、実際にバックアップを復元しなくても、復元操作でデータベースを復旧することは可能です。たとえば、データベースと一貫性のある読み取り専用ファイルを復旧する場合などです。</span><span class="sxs-lookup"><span data-stu-id="37c08-104">However, a restore operation can recover a database without actually restoring a backup; for example, when recovering a read-only file that is consistent with the database.</span></span> <span data-ttu-id="37c08-105">これは、 *復旧のみの復元*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="37c08-105">This is referred to as a *recovery-only restore*.</span></span> <span data-ttu-id="37c08-106">オフライン データが既にデータベースと一貫性があり、データを使用可能にするだけでよい場合、復旧のみの復元を実行することで、データベースの復旧が完了し、データがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="37c08-106">When offline data is already consistent with the database and needs only to be made available, a recovery-only restore operation completes the recovery of the database and bring the data online.</span></span>  
  
 <span data-ttu-id="37c08-107">復旧のみの復元は、データベース全体、1 つまたは複数のファイル、およびファイル グループに対して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="37c08-107">A recovery-only restore can occur for a whole database or for one or more a files or filegroups.</span></span>  
  
## <a name="recovery-only-database-restore"></a><span data-ttu-id="37c08-108">復旧のみのデータベース復元</span><span class="sxs-lookup"><span data-stu-id="37c08-108">Recovery-Only Database Restore</span></span>  
 <span data-ttu-id="37c08-109">復旧のみのデータベース復元は、次の場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="37c08-109">A recovery-only database restore can be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="37c08-110">復元シーケンスで前回のバックアップを復元したときはデータベースを復旧しなかったが、現在そのデータベースを復旧してオンラインにする必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="37c08-110">You did not recover the database when restoring the last backup in a restore sequence, and you now want to recover the database to bring it online.</span></span>  
  
-   <span data-ttu-id="37c08-111">データベースがスタンバイ モードであり、別のログ バックアップを適用せずにそのデータベースを更新可能にする場合。</span><span class="sxs-lookup"><span data-stu-id="37c08-111">The database is in standby mode, and you want to make the database updatable without applying another log backup.</span></span>  
  
 <span data-ttu-id="37c08-112">復旧のみのデータベース復元の [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37c08-112">The [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for a recovery-only database restore is as follows:</span></span>  
  
 <span data-ttu-id="37c08-113">RESTORE DATABASE *database_name* WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="37c08-113">RESTORE DATABASE *database_name* WITH RECOVERY</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="37c08-114">復旧のみの復元にはバックアップは必要ないので、FROM **=** \<*backup_device>\* 句は使用しません。</span><span class="sxs-lookup"><span data-stu-id="37c08-114">The FROM **=** \<*backup_device>\* clause is not used for recovery-only restores because no backup is necessary.</span></span>  
  
 <span data-ttu-id="37c08-115">**例**</span><span class="sxs-lookup"><span data-stu-id="37c08-115">**Example**</span></span>  
  
 <span data-ttu-id="37c08-116">次の例では、データを復元しない復元操作で [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="37c08-116">The following example recovers the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database in a restore operation without restoring data.</span></span>  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## <a name="recovery-only-file-restore"></a><span data-ttu-id="37c08-117">復旧のみのファイル復元</span><span class="sxs-lookup"><span data-stu-id="37c08-117">Recovery-Only File Restore</span></span>  
 <span data-ttu-id="37c08-118">復旧のみのファイル復元は、次の場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="37c08-118">A recovery-only file restore can be useful in the following situation:</span></span>  
  
 <span data-ttu-id="37c08-119">データベースを段階的に部分復元する場合。</span><span class="sxs-lookup"><span data-stu-id="37c08-119">A database is restored piecemeal.</span></span> <span data-ttu-id="37c08-120">プライマリ ファイル グループの復元が完了した後、復元されていないのに、新しいデータベースの状態と一貫性があるファイルが 1 つ以上ある場合。これはおそらく、しばらくの間読み取り専用であったことが原因です。</span><span class="sxs-lookup"><span data-stu-id="37c08-120">After restore of the primary filegroup is complete, one or more of the unrestored files are consistent with the new database state, perhaps because it has been read-only for some time.</span></span> <span data-ttu-id="37c08-121">このようなファイルに対して必要な作業は、復旧のみです。データをコピーする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="37c08-121">These files only have to be recovered; data copying is unnecessary.</span></span>  
  
 <span data-ttu-id="37c08-122">復旧のみの復元操作では、オフラインのファイル グループ内のデータをオンラインにします。データのコピー フェーズ、再実行フェーズ、および元に戻すフェーズはありません。</span><span class="sxs-lookup"><span data-stu-id="37c08-122">A recovery-only restore operation brings the data in the offline filegroup online; no data-copy, redo, or undo phase occurs.</span></span> <span data-ttu-id="37c08-123">復元の各フェーズに関する詳細については、「[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37c08-123">For information about the phases of restore, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
 <span data-ttu-id="37c08-124">復旧のみのファイル復元の [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37c08-124">The [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for a recovery-only file restore is:</span></span>  
  
 <span data-ttu-id="37c08-125">RESTORE DATABASE *database_name* {FILE **=** _logical_file_name_ |ファイルグループ **=** _logical_filegroup_name_ } [ **,**...*n* ] 回復</span><span class="sxs-lookup"><span data-stu-id="37c08-125">RESTORE DATABASE *database_name* { FILE **=**_logical_file_name_ | FILEGROUP **=**_logical_filegroup_name_ }[ **,**...*n* ] WITH RECOVERY</span></span>  
  
 <span data-ttu-id="37c08-126">**例**</span><span class="sxs-lookup"><span data-stu-id="37c08-126">**Example**</span></span>  
  
 <span data-ttu-id="37c08-127">次の例は、 `SalesGroup2`データベースのセカンダリ ファイル グループ `Sales` に含まれているファイルの復旧のみのファイル復元を示しています。</span><span class="sxs-lookup"><span data-stu-id="37c08-127">The following example illustrates a recovery-only file restore of the files in a secondary filegroup, `SalesGroup2`, in the `Sales` database.</span></span> <span data-ttu-id="37c08-128">プライマリ ファイル グループは段階的な部分復元の最初の手順で既に復元されており、 `SalesGroup2` は復元されたプライマリ ファイル グループと一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="37c08-128">The primary filegroup has already been restored as the initial step of a piecemeal restore, and `SalesGroup2` is consistent with the restored primary filegroup.</span></span> <span data-ttu-id="37c08-129">このファイル グループを復旧してオンラインにするために必要なのは、次に示す 1 つのステートメントだけです。</span><span class="sxs-lookup"><span data-stu-id="37c08-129">Recovering this filegroup and bringing it online requires only a single statement.</span></span>  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## <a name="examples-of-completing-a-piecemeal-restore-scenario-with-a-recovery-only-restore"></a><span data-ttu-id="37c08-130">復旧のみの復元を使用した段階的な部分復元シナリオの完了の例</span><span class="sxs-lookup"><span data-stu-id="37c08-130">Examples of Completing a Piecemeal Restore Scenario with a Recovery-Only Restore</span></span>  
 <span data-ttu-id="37c08-131">**単純復旧モデル**</span><span class="sxs-lookup"><span data-stu-id="37c08-131">**Simple recovery model**</span></span>  
  
-   [<span data-ttu-id="37c08-132">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="37c08-132">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="37c08-133">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="37c08-133">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 <span data-ttu-id="37c08-134">**完全復旧モデル**</span><span class="sxs-lookup"><span data-stu-id="37c08-134">**Full recovery model**</span></span>  
  
-   [<span data-ttu-id="37c08-135">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="37c08-135">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="37c08-136">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="37c08-136">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## <a name="see-also"></a><span data-ttu-id="37c08-137">参照</span><span class="sxs-lookup"><span data-stu-id="37c08-137">See Also</span></span>  
 <span data-ttu-id="37c08-138">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="37c08-138">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="37c08-139">[段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="37c08-139">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="37c08-140">[ファイルの復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="37c08-140">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="37c08-141">[ファイルの復元 &#40;完全復旧モデル&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="37c08-141">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="37c08-142">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="37c08-142">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
