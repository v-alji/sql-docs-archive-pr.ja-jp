---
title: 段階的な部分復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- partial updates [SQL Server]
- staged restores [SQL Server]
- piecemeal restores [SQL Server]
- restoring [SQL Server], piecemeal restore scenario
ms.assetid: 208f55e0-0762-4cfb-85c4-d36a76ea0f5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ebc4ea11780908f847946a01338571211b57678a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715430"
---
# <a name="piecemeal-restores-sql-server"></a><span data-ttu-id="cfc39-102">段階的な部分復元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cfc39-102">Piecemeal Restores (SQL Server)</span></span>
  <span data-ttu-id="cfc39-103">このトピックの内容は、複数のファイルまたはファイル グループ (単純復旧モデルでは、読み取り専用ファイル グループのみ) を含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Enterprise エディションのデータベースだけに関するものです。</span><span class="sxs-lookup"><span data-stu-id="cfc39-103">This topic is relevant only for databases in the Enterprise edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.</span></span>  
  
 <span data-ttu-id="cfc39-104">段階的な部分復元とメモリ最適化テーブルの詳細については、「 [メモリ最適化テーブルを持つデータベースの段階的な部分復元](../in-memory-oltp/memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfc39-104">For information about piecemeal restore and memory-optimized tables, see [Piecemeal Restore of Databases With Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="cfc39-105">*段階的な部分復元* 機能では、複数のファイル グループを含むデータベースを段階的に復元および復旧できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-105">*Piecemeal restore* allows databases that contain multiple filegroups to be restored and recovered in stages.</span></span> <span data-ttu-id="cfc39-106">段階的な部分復元には、プライマリ ファイル グループから始まり、場合によっては 1 つ以上のセカンダリ ファイル グループを復元するための、一連の復元シーケンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cfc39-106">Piecemeal restore involves a series of restore sequences, starting with the primary filegroup and, in some cases, one or more secondary filegroups.</span></span> <span data-ttu-id="cfc39-107">段階的な部分復元では、データベースの一貫性を最終的に確保するために、継続的にチェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-107">Piecemeal restore maintains checks to ensure that the database will be consistent in the end.</span></span> <span data-ttu-id="cfc39-108">復元シーケンスの完了後、復元されたファイルは (これらのファイルが有効で、データベースとの一貫性があれば) 直接オンラインにできます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-108">After the restore sequence is completed, recovered files, if they are valid and consistent with the database, can be brought online directly.</span></span>  
  
 <span data-ttu-id="cfc39-109">段階的な部分復元は、すべての復旧モデルで使用できますが、単純復旧モデルよりも完全復旧モデルと一括ログ復旧モデルの方がより柔軟に実行できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-109">Piecemeal restore works with all recovery models, but is more flexible for the full and bulk-logged models than for the simple model.</span></span>  
  
 <span data-ttu-id="cfc39-110">すべての段階的な部分復元は、 *部分復元シーケンス*と呼ばれる初期復元シーケンスから始まります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-110">Every piecemeal restore starts with an initial restore sequence called the *partial-restore sequence*.</span></span> <span data-ttu-id="cfc39-111">最小限の部分復元シーケンスでは、プライマリ ファイル グループが復元および復旧されます。単純な復旧モデルでは、すべての読み取り/書き込みファイル グループが復元および復旧されます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-111">Minimally, the partial-restore sequence restores and recovers the primary filegroup and, under the simple recovery model, all read/write filegroups.</span></span> <span data-ttu-id="cfc39-112">段階的な部分復元シーケンスの間は、データベース全体をオフラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-112">During the piecemeal-restore sequence, the whole database must go offline.</span></span> <span data-ttu-id="cfc39-113">その後、データベースをオンラインにすると、復元されたファイル グループが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-113">Thereafter, the database is online and restored filegroups are available.</span></span> <span data-ttu-id="cfc39-114">ただし、復元されないファイル グループはオフラインのままで、アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="cfc39-114">However, any unrestored filegroups remain offline and are not accessible.</span></span> <span data-ttu-id="cfc39-115">オフラインのファイル グループを復元してオンラインにするには、後でファイル復元を行います。</span><span class="sxs-lookup"><span data-stu-id="cfc39-115">Any offline filegroups, however, can be restored and brought online later by a file restore.</span></span>  
  
 <span data-ttu-id="cfc39-116">データベースに使用されている復旧モデルにかかわらず、部分復元シーケンスは、完全バックアップを復元する RESTORE DATABASE ステートメントと PARTIAL オプションから始まります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-116">Regardless of the recovery model that is used by the database, the partial-restore sequence starts with a RESTORE DATABASE statement that restores a full backup and specifies the PARTIAL option.</span></span> <span data-ttu-id="cfc39-117">PARTIAL オプションを指定すると、常に新しい段階的な部分復元が開始されます。このため、PARTIAL オプションは部分復元シーケンスの最初のステートメントに 1 回だけ指定します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-117">The PARTIAL option always starts a new piecemeal restore; therefore, you must specify PARTIAL only one time in the initial statement of the partial-restore sequence.</span></span> <span data-ttu-id="cfc39-118">この部分復元シーケンスが完了し、データベースがオンラインになると、残りのファイルの状態が "復旧待ち" になります。これは、残りのファイルの復旧が延期されているためです。</span><span class="sxs-lookup"><span data-stu-id="cfc39-118">When the partial restore sequence finishes and the database is brought online, the state of the remaining files becomes "recovery pending" because their recovery has been postponed.</span></span>  
  
 <span data-ttu-id="cfc39-119">段階的な部分復元のこの後の部分には、通常、 *ファイル グループ復元シーケンス*と呼ばれる 1 つ以上の復元シーケンスがあります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-119">Subsequently, a piecemeal restore typically includes one or more restore sequences, which are called *filegroup-restore sequences*.</span></span> <span data-ttu-id="cfc39-120">特定のファイル グループ復元シーケンスは、必要な時間待機させることができます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-120">You can wait to perform a specific filegroup-restore sequence for as long as you want.</span></span> <span data-ttu-id="cfc39-121">各ファイル グループ復元シーケンスでは、1 つ以上のオフラインのファイル グループを、データベースの一貫性がある時点に復元および復旧します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-121">Each filegroup-restore sequence restores and recovers one or more offline filegroups to a point consistent with the database.</span></span> <span data-ttu-id="cfc39-122">ファイル グループ復元シーケンスのタイミングと数は、復旧の目的、つまり復旧するオフライン ファイル グループの数、および 1 回のファイル グループ復元シーケンスで復元するファイル グループの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-122">The timing and number of filegroup-restore sequences depends on your recovery goal, the number of offline filegroups you want to restore, and on how many of them you restore per filegroup-restore sequence.</span></span>  
  
 <span data-ttu-id="cfc39-123">実行する段階的な部分復元の正確な要件は、データベースの復旧モデルによって異なります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-123">The exact requirements for performing a piecemeal restore depend on the recovery model of the database.</span></span> <span data-ttu-id="cfc39-124">詳細については、後の「単純復旧モデルでの段階的な部分復元」および「完全復旧モデルでの段階的な部分復元」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfc39-124">For more information, see "Piecemeal Restore Under the Simple Recovery Model" and "Piecemeal Restore Under the Full Recovery Model," later in this topic.</span></span>  
  
## <a name="piecemeal-restore-scenarios"></a><span data-ttu-id="cfc39-125">段階的な部分復元のシナリオ</span><span class="sxs-lookup"><span data-stu-id="cfc39-125">Piecemeal Restore Scenarios</span></span>  
 <span data-ttu-id="cfc39-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではすべてのエディションで、オフラインの段階的な部分復元がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-126">All editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support offline piecemeal restores.</span></span> <span data-ttu-id="cfc39-127">Enterprise エディションでは、段階的な部分復元をオンラインでもオフラインでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-127">In the Enterprise edition, a piecemeal restore can be either online or offline.</span></span> <span data-ttu-id="cfc39-128">オフラインとオンラインの段階的な部分復元の影響を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-128">The implications of offline and online piecemeal restores are as follows:</span></span>  
  
-   <span data-ttu-id="cfc39-129">オフラインの段階的な部分復元のシナリオ</span><span class="sxs-lookup"><span data-stu-id="cfc39-129">Offline piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="cfc39-130">オフラインの段階的な部分復元では、部分復元シーケンスの実行後にデータベースがオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-130">In an offline piecemeal restore, the database is online after the partial-restore sequence.</span></span> <span data-ttu-id="cfc39-131">復元されていないファイル グループはオフラインのままになりますが、データベースをオフラインにすれば、必要に応じて復元できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-131">Filegroups that have not yet been restored remain offline, but they can be restored as you need them after taking the database offline.</span></span>  
  
-   <span data-ttu-id="cfc39-132">オンラインの段階的な部分復元のシナリオ</span><span class="sxs-lookup"><span data-stu-id="cfc39-132">Online piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="cfc39-133">オンラインの段階的な部分復元シナリオでは、部分復元シーケンスの実行後にデータベースがオンラインになり、プライマリ ファイル グループと復旧されたすべてのセカンダリ ファイル グループが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-133">In an online piecemeal restore, after the partial-restore sequence, the database is online, and the primary filegroup and any recovered secondary filegroups are available.</span></span> <span data-ttu-id="cfc39-134">復元されていないファイル グループはオフラインのままになりますが、データベースがオンラインの状態であれば、その間に必要に応じて復元できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-134">Filegroups that have not yet been restored remain offline, but they can be restored as needed while the database remains online.</span></span>  
  
     <span data-ttu-id="cfc39-135">オンラインの段階的な部分復元では遅延トランザクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-135">Online piecemeal restores can involve deferred transactions.</span></span> <span data-ttu-id="cfc39-136">ファイル グループのサブセットだけが復元された場合、データベース内のトランザンションの中でオンライン ファイル グループに依存するものは遅延される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-136">When only a subset of filegroups has been restored, transactions in the database that depend on online filegroups might become deferred.</span></span> <span data-ttu-id="cfc39-137">これは、データベース全体の一貫性を保つための一般的な動作です。</span><span class="sxs-lookup"><span data-stu-id="cfc39-137">This is typical, because the whole database must be consistent.</span></span> <span data-ttu-id="cfc39-138">詳細については、「 [遅延トランザクション &#40;SQL Server&#41;](deferred-transactions-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfc39-138">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
-   [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="cfc39-139">段階的な部分復元のシナリオ</span><span class="sxs-lookup"><span data-stu-id="cfc39-139">piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="cfc39-140">インメモリ OLTP データベースの段階的な部分復元の詳細については、「 [メモリ最適化テーブルを持つデータベースの段階的なバックアップと部分復元](../in-memory-oltp/memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfc39-140">For information on Piecemeal Restores of In-Memory OLTP databases see [Piecemeal Backup and Restore of Databases With Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="cfc39-141">制限</span><span class="sxs-lookup"><span data-stu-id="cfc39-141">Restrictions</span></span>  
 <span data-ttu-id="cfc39-142">部分復元シーケンスで [FILESTREAM](../blob/filestream-sql-server.md) ファイル グループを除外した場合、特定の時点への復元はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="cfc39-142">If a partial restore sequence excludes any [FILESTREAM](../blob/filestream-sql-server.md) filegroup, point-in-time restore is not supported.</span></span> <span data-ttu-id="cfc39-143">復元シーケンスを強制的に実行して続行することもできます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-143">You can force the restore sequence to continue.</span></span> <span data-ttu-id="cfc39-144">ただし、RESTORE ステートメントから除外された FILESTREAM ファイル グループは復元できません。</span><span class="sxs-lookup"><span data-stu-id="cfc39-144">However the FILESTREAM filegroups that are omitted from your RESTORE statement can never be restored.</span></span> <span data-ttu-id="cfc39-145">特定の時点への復元を強制的に実行するには、STOPAT、STOPATMARK、または STOPBEFOREMARK オプションに CONTINUE_AFTER_ERROR オプションを組み合わせて指定します。これらのオプションは、後続の RESTORE LOG ステートメントでも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-145">To force a point-in-time restore, specify the CONTINUE_AFTER_ERROR option together with the STOPAT, STOPATMARK, or STOPBEFOREMARK option, which you must also specify in your subsequent RESTORE LOG statements.</span></span> <span data-ttu-id="cfc39-146">CONTINUE_AFTER_ERROR を指定した場合、部分復元シーケンスは正常に実行されますが、FILESTREAM ファイル グループは復元できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-146">If you specify CONTINUE_AFTER_ERROR, the partial restore sequence succeeds and the FILESTREAM filegroup becomes unrecoverable.</span></span>  
  
## <a name="piecemeal-restore-under-the-simple-recovery-model"></a><span data-ttu-id="cfc39-147">単純復旧モデルでの段階的な部分復元</span><span class="sxs-lookup"><span data-stu-id="cfc39-147">Piecemeal Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="cfc39-148">単純復旧モデルでは、データベースの完全バックアップまたは差分バックアップから段階的な部分復元シーケンスを始める必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-148">Under the simple recovery model, the piecemeal restore sequence must start with a full database or partial backup.</span></span> <span data-ttu-id="cfc39-149">その後、復元されたバックアップが差分ベースであれば、最新の差分バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-149">Then, if the restored backup is a differential base, restore the latest differential backup next.</span></span>  
  
 <span data-ttu-id="cfc39-150">最初の部分復元シーケンスの間に読み取り/書き込みファイル グループのサブセットだけを復元した場合、部分的に復元されたデータベースを復旧すると、復元されていないファイル グループはすべて機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-150">During the first partial restore sequence, if you restore only a subset of read/write filegroups, any unrestored filegroups become defunct when you recover the partially restored database.</span></span> <span data-ttu-id="cfc39-151">部分復元シーケンスから読み取り/書き込みファイル グループを除くことが適切なのは、次の場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-151">Omitting a read/write filegroup from the partial-restore sequence is appropriate only in the following cases:</span></span>  
  
-   <span data-ttu-id="cfc39-152">復元されないファイル グループを意図的に機能しないようにする場合。</span><span class="sxs-lookup"><span data-stu-id="cfc39-152">You intend for the unrestored filegroups to become defunct.</span></span>  
  
-   <span data-ttu-id="cfc39-153">部分復元シーケンスの前の復元中に、復元されていない各ファイル グループが、読み取り専用、削除済み、または機能しない状態になっている復旧ポイントに復元シーケンスが到達する場合。</span><span class="sxs-lookup"><span data-stu-id="cfc39-153">The restore sequence will arrive at a recovery point at which each unrestored filegroup has become read-only, dropped, or defunct (during a previous restore in the partial-restore sequence).</span></span>  
  
-   <span data-ttu-id="cfc39-154">データベースに対して単純復旧モデルを使用している期間中に完全バックアップを行ったが、完全復旧モデルを使用している時点に復旧ポイントがある場合。</span><span class="sxs-lookup"><span data-stu-id="cfc39-154">The full backup was taken while the database was using the simple recovery model, but the recovery point is at a time when the database is using the full recovery model.</span></span> <span data-ttu-id="cfc39-155">詳細については、後の「復旧モデルを単純から完全に切り替えたデータベースの段階的な部分復元の実行」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfc39-155">For more information, see "Performing a Piecemeal Restore of a Database Whose Recovery Model Has Been Switched from Simple to Full," later in this topic.</span></span>  
  
### <a name="requirements-for-piecemeal-restore-under-the-simple-recovery-model"></a><span data-ttu-id="cfc39-156">単純復旧モデルでの段階的な部分復元の要件</span><span class="sxs-lookup"><span data-stu-id="cfc39-156">Requirements for Piecemeal Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="cfc39-157">単純復旧モデルでは、初期段階でプライマリ ファイル グループと、すべての読み取り/書き込みセカンダリ ファイル グループが復元および復旧されます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-157">Under the simple recovery model, the initial stage restores and recovers the primary filegroup and all read/write secondary filegroups.</span></span> <span data-ttu-id="cfc39-158">初期段階の完了後、復元されたファイルは (これらのファイルが有効で、データベースとの一貫性があれば) 直接オンラインにできます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-158">After the initial stage is completed, recovered files, if they are valid and consistent with the database, can be brought online directly.</span></span>  
  
 <span data-ttu-id="cfc39-159">その後、読み取り専用のファイル グループが 1 回以上の追加段階で復元されます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-159">Thereafter, read-only filegroups can be restored in one or more additional stages.</span></span>  
  
 <span data-ttu-id="cfc39-160">読み取り専用のセカンダリ ファイル グループの段階的な部分復元は、次の条件が満たされた場合に限り可能になります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-160">Piecemeal restore is available for a read-only secondary filegroup only if the following are true:</span></span>  
  
-   <span data-ttu-id="cfc39-161">バックアップ時に読み取り専用だったこと。</span><span class="sxs-lookup"><span data-stu-id="cfc39-161">Was read-only when backed up.</span></span>  
  
-   <span data-ttu-id="cfc39-162">読み取り専用のままであること (プライマリ ファイル グループと論理的に一貫性があること)。</span><span class="sxs-lookup"><span data-stu-id="cfc39-162">Has remained read-only (keeping it logically consistent with the primary filegroup).</span></span>  
  
 <span data-ttu-id="cfc39-163">段階的な部分復元を実行する場合、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="cfc39-163">To perform a piecemeal restore, the following guidelines must be followed:</span></span>  
  
-   <span data-ttu-id="cfc39-164">単純復旧モデルのデータベースに対する段階的な部分復元では、完全なバックアップ セットに次のバックアップが必要です。</span><span class="sxs-lookup"><span data-stu-id="cfc39-164">A complete set of backups for the piecemeal restore of a simple recovery model database must contain the following:</span></span>  
  
    -   <span data-ttu-id="cfc39-165">プライマリ ファイル グループと、バックアップ時に読み取りと書き込みが可能だったすべてのファイル グループを含んでいる、データベースの部分バックアップまたは完全バックアップ。</span><span class="sxs-lookup"><span data-stu-id="cfc39-165">A partial or full database backup that contains the primary filegroup and all filegroups that were read/write at the time of the backup.</span></span>  
  
    -   <span data-ttu-id="cfc39-166">各読み取り専用ファイルのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="cfc39-166">A backup of each read-only file.</span></span>  
  
-   <span data-ttu-id="cfc39-167">読み取り専用ファイルのバックアップとプライマリ ファイル グループに一貫性がある場合、セカンダリ ファイル グループがバックアップされ、プライマリ ファイル グループを含んでいるバックアップが完了するまでの間、そのセカンダリ ファイル グループは読み取り専用である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-167">For the backup of a read-only file to be consistent with the primary filegroup, the secondary filegroup must have been read-only from when it was backed up until the backup that contains the primary filegroup was completed.</span></span> <span data-ttu-id="cfc39-168">セカンダリ ファイル グループが読み取り専用になった後でバックアップを作成した場合は、ファイルの差分バックアップを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-168">You can use differential file backups, if they were taken after the filegroup became read-only.</span></span>  
  
### <a name="piecemeal-restore-stages-simple-recovery-model"></a><span data-ttu-id="cfc39-169">段階的な部分復元の各段階 (単純復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="cfc39-169">Piecemeal Restore Stages (Simple Recovery Model)</span></span>  
 <span data-ttu-id="cfc39-170">段階的な部分復元シナリオには、次の段階があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-170">The piecemeal restore scenario involves the following stages:</span></span>  
  
-   <span data-ttu-id="cfc39-171">初期段階 (プライマリ ファイル グループとすべての読み取り/書き込みファイル グループを復元および復旧します)。</span><span class="sxs-lookup"><span data-stu-id="cfc39-171">Initial stage (restore and recover the primary filegroup and all read/write filegroups)</span></span>  
  
     <span data-ttu-id="cfc39-172">初期段階では部分復元が実行されます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-172">The initial stage performs a partial restore.</span></span> <span data-ttu-id="cfc39-173">この部分復元シーケンスでは、プライマリ ファイル グループとすべての読み取り/書き込みセカンダリ ファイル グループ、および必要に応じて、一部の読み取り専用ファイル グループが復元されます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-173">The partial restore sequence restores the primary filegroup, all read/write secondary filegroups, and (optionally) some of the read-only filegroups.</span></span> <span data-ttu-id="cfc39-174">初期段階では、データベース全体をオフライン状態にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-174">During the initial stage, the whole database must go offline.</span></span> <span data-ttu-id="cfc39-175">初期段階後は、データベースがオンラインになり、復元されたファイル グループが利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-175">After the initial stage, the database is online, and restored filegroups are available.</span></span> <span data-ttu-id="cfc39-176">ただし、復元されていない読み取り専用ファイル グループは、オフラインのままです。</span><span class="sxs-lookup"><span data-stu-id="cfc39-176">However, any read-only filegroups that have not yet been restored, remain offline.</span></span>  
  
     <span data-ttu-id="cfc39-177">初期段階の最初の RESTORE ステートメントでは、以下の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-177">The first RESTORE statement in the initial stage must do the following:</span></span>  
  
    -   <span data-ttu-id="cfc39-178">プライマリ ファイル グループとバックアップ時点で読み取りと書き込みが可能だったすべてのファイル グループを含む、データベースの部分バックアップまたはデータベースの完全バックアップを使用します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-178">Use a partial or full database backup that contains the primary filegroup and all filegroups that were read/write at the time of the backup.</span></span> <span data-ttu-id="cfc39-179">通常は、部分バックアップを復元することで、部分復元シーケンスを開始します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-179">It is common to start a partial restore sequence by restoring a partial backup.</span></span>  
  
    -   <span data-ttu-id="cfc39-180">段階的な部分復元の開始を指定する PARTIAL オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-180">Specify the PARTIAL option, which indicates the start of a piecemeal restore.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cfc39-181">復元後のデータベースが運用データベースとして適切な状態になるように、安全性チェックが PARTIAL オプションによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-181">The PARTIAL option performs safety checks that ensure that the resulting database is suited for use as a production database.</span></span>  
  
    -   <span data-ttu-id="cfc39-182">バックアップがデータベースの完全バックアップである場合は、READ_WRITE_FILEGROUPS オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-182">Specify the READ_WRITE_FILEGROUPS option if the backup is a full database backup.</span></span>  
  
-   <span data-ttu-id="cfc39-183">データベースがオンラインの間、1 つ以上のオンライン ファイルの復元を使用して、バックアップ時点で読み取り専用であったオフラインの読み取り専用ファイルを復元および復旧できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-183">While the database is online, you can use one or more online file restores to restore and recover offline read-only files that were read-only at the time of backup.</span></span> <span data-ttu-id="cfc39-184">オンライン ファイルの復元のタイミングは、データをオンラインにするタイミングによって異なります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-184">The timing of the online file restores depends on when you want to have the data online.</span></span>  
  
     <span data-ttu-id="cfc39-185">データをファイルに復元する必要があるかどうかは次の要因によって決まります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-185">Whether you must restore data to a file depends on the following:</span></span>  
  
    -   <span data-ttu-id="cfc39-186">データベースとの一貫性がある有効な読み取り専用ファイルは、データの復元は一切行わずに、ファイルを復旧することで直接オンラインにできます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-186">Valid read-only files that are consistent with the database can be brought online directly by recovering them without restoring any data.</span></span>  
  
    -   <span data-ttu-id="cfc39-187">損傷しているファイルや、データベースと一貫性のないファイルは、復旧する前に復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-187">Files that are damaged or inconsistent with the database must be restored before they are recovered.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cfc39-188">例</span><span class="sxs-lookup"><span data-stu-id="cfc39-188">Examples</span></span>  
  
-   [<span data-ttu-id="cfc39-189">例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="cfc39-189">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="cfc39-190">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="cfc39-190">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="piecemeal-restore-under-the-full-recovery-model"></a><span data-ttu-id="cfc39-191">完全復旧モデルでの段階的な部分復元</span><span class="sxs-lookup"><span data-stu-id="cfc39-191">Piecemeal Restore Under the Full Recovery Model</span></span>  
 <span data-ttu-id="cfc39-192">完全復旧モデルまたは一括ログ復旧モデルでは、複数のファイル グループを含むすべてのデータベースで段階的な部分復元を実行でき、データベースを任意の時点に復元できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-192">Under the full recovery model or bulk-logged recovery model, piecemeal restore is available for any database that contains multiple filegroups and you can restore a database to any point in time.</span></span> <span data-ttu-id="cfc39-193">段階的な部分復元の復元シーケンスは、次のように行われます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-193">The restore sequences of a piecemeal restore behave as follows:</span></span>  
  
-   <span data-ttu-id="cfc39-194">部分復元シーケンス</span><span class="sxs-lookup"><span data-stu-id="cfc39-194">Partial-restore sequence</span></span>  
  
     <span data-ttu-id="cfc39-195">この部分復元シーケンスでは、プライマリ ファイル グループと、必要に応じて、一部のセカンダリ ファイル グループが復元されます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-195">The partial restore sequence restores the primary filegroup and, optionally, some of the secondary filegroups.</span></span>  
  
     <span data-ttu-id="cfc39-196">最初の RESTORE DATABASE ステートメントでは次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-196">The first RESTORE DATABASE statement must do the following:</span></span>  
  
    -   <span data-ttu-id="cfc39-197">PARTIAL オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-197">Specify the PARTIAL option.</span></span> <span data-ttu-id="cfc39-198">これは段階的な部分復元を開始することを示します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-198">This indicates the start of a piecemeal restore.</span></span>  
  
    -   <span data-ttu-id="cfc39-199">プライマリ ファイル グループを含むデータベースの完全バックアップを使用します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-199">Use any full database backup that contains the primary filegroup.</span></span> <span data-ttu-id="cfc39-200">通常は、部分バックアップを復元することで、部分復元シーケンスを開始します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-200">The common practice is to start a partial restore sequence by restoring a partial backup.</span></span>  
  
    -   <span data-ttu-id="cfc39-201">特定の時点に復元するには、部分復元シーケンスで時刻を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-201">To restore to a specific point in time, you must specify the time in the partial restore sequence.</span></span> <span data-ttu-id="cfc39-202">復元シーケンスのその後のすべてのステップで、同じ時点を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-202">Every successive step of the restore sequence must specify the same point in time.</span></span>  
  
-   <span data-ttu-id="cfc39-203">ファイル グループ復元シーケンスではその他のファイル グループをデータベースと一貫性がある時点でオンラインにします。</span><span class="sxs-lookup"><span data-stu-id="cfc39-203">Filegroup-restore sequences bring additional filegroups online to a point consistent with the database.</span></span>  
  
     <span data-ttu-id="cfc39-204">Enterprise エディションでは、データベースをオンラインにしたまま、オフラインのセカンダリ ファイル グループを復元および復旧できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-204">In the Enterprise edition, any offline secondary filegroup can be restored and recovered while the database remains online.</span></span> <span data-ttu-id="cfc39-205">特定の読み取り専用ファイルに損傷がなく、データベースと一貫性があれば、そのファイルを復元する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cfc39-205">If a specific read-only file is undamaged and consistent with the database, the file does not have to be restored.</span></span> <span data-ttu-id="cfc39-206">詳細については、「[データを復元しないデータベースの復旧 &#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfc39-206">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
### <a name="applying-log-backups"></a><span data-ttu-id="cfc39-207">ログ バックアップの適用</span><span class="sxs-lookup"><span data-stu-id="cfc39-207">Applying Log Backups</span></span>  
 <span data-ttu-id="cfc39-208">読み取り専用ファイル グループがバックアップの作成前から読み取り専用だった場合は、ログ バックアップをファイル グループに適用する必要はないので、ファイルの復元の際にスキップされます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-208">If a read-only filegroup has been read-only since before the file backup was created, applying log backups to the filegroup is unnecessary and is skipped by file restore.</span></span> <span data-ttu-id="cfc39-209">読み取り/書き込みファイル グループの場合は、最新の完全復元または差分復元にチェーンが途切れていないログ バックアップを適用し、ファイル グループに現在のログ ファイルの状態を反映する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfc39-209">If the filegroup is read/write, an unbroken chain of log backups must be applied to the last full or differential restore to bring the filegroup forward to the current log file.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cfc39-210">例</span><span class="sxs-lookup"><span data-stu-id="cfc39-210">Examples</span></span>  
  
-   [<span data-ttu-id="cfc39-211">例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="cfc39-211">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="cfc39-212">例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="cfc39-212">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
## <a name="performing-a-piecemeal-restore-of-a-database-whose-recovery-model-has-been-switched-from-simple-to-full"></a><span data-ttu-id="cfc39-213">復旧モデルを単純から完全に切り替えたデータベースの段階的な部分復元の実行</span><span class="sxs-lookup"><span data-stu-id="cfc39-213">Performing a Piecemeal Restore of a Database Whose Recovery Model Has Been Switched from Simple to Full</span></span>  
 <span data-ttu-id="cfc39-214">データベースの完全バックアップまたは部分バックアップ以降に単純復旧モデルから完全復旧モデルに切り替えたデータベースは、段階的な部分復元を実行できます。</span><span class="sxs-lookup"><span data-stu-id="cfc39-214">You can perform a piecemeal restore of a database that has been switched from the simple recovery model to the full recovery model since the full partial or database backup.</span></span> <span data-ttu-id="cfc39-215">たとえば、データベースで次の手順を実行した場合を検討します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-215">For example, consider a database for which you take the following steps:</span></span>  
  
1.  <span data-ttu-id="cfc39-216">単純モデルのデータベースの部分バックアップ (backup_1) を作成します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-216">Create a partial backup (backup_1) of a simple-model database.</span></span>  
  
2.  <span data-ttu-id="cfc39-217">その後、復旧モデルを "完全" に変更します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-217">After some time, change the recovery model to full.</span></span>  
  
3.  <span data-ttu-id="cfc39-218">差分バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-218">Create a differential backup.</span></span>  
  
4.  <span data-ttu-id="cfc39-219">ログ バックアップを開始します。</span><span class="sxs-lookup"><span data-stu-id="cfc39-219">Start taking log backups.</span></span>  
  
 <span data-ttu-id="cfc39-220">これ以降、次のシーケンスが有効です。</span><span class="sxs-lookup"><span data-stu-id="cfc39-220">Thereafter, the following sequence is valid:</span></span>  
  
1.  <span data-ttu-id="cfc39-221">部分復元で一部のセカンダリ ファイル グループを省略する。</span><span class="sxs-lookup"><span data-stu-id="cfc39-221">A partial restore that omits some secondary filegroups.</span></span>  
  
2.  <span data-ttu-id="cfc39-222">差分復元の後、その他の必要な復元を行う。</span><span class="sxs-lookup"><span data-stu-id="cfc39-222">A differential restore followed by any other needed restores.</span></span>  
  
3.  <span data-ttu-id="cfc39-223">後で、WITH NORECOVERY を指定して backup_1 部分バックアップから読み取り/書き込みセカンダリ ファイル グループを復元する。</span><span class="sxs-lookup"><span data-stu-id="cfc39-223">Later, a file restore of a read/write secondary filegroup WITH NORECOVERY from the backup_1 partial backup</span></span>  
  
4.  <span data-ttu-id="cfc39-224">差分バックアップの後、元の段階的な部分復元でその他の復元を実行して、元の復旧ポイントまでデータを復元する。</span><span class="sxs-lookup"><span data-stu-id="cfc39-224">The differential backup followed by any other backups that were restored in the original piecemeal restore sequence to restore the data up to the original recovery point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc39-225">参照</span><span class="sxs-lookup"><span data-stu-id="cfc39-225">See Also</span></span>  
 <span data-ttu-id="cfc39-226">[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cfc39-226">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="cfc39-227">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cfc39-227">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="cfc39-228">[SQL Server データベースを特定の時点に復元する方法 &#40;完全復旧モデル&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="cfc39-228">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="cfc39-229">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cfc39-229">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="cfc39-230">復元シーケンスの計画と実行 &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="cfc39-230">Plan and Perform Restore Sequences &#40;Full Recovery Model&#41;</span></span>](plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
