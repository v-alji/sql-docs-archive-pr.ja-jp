---
title: ミラー化バックアップ メディア セット (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server], mirrored backups
- mirrored media sets [SQL Server]
- backup mirrors [SQL Server]
- duplicate backup copies
- interchangeable backup copies [SQL Server]
- media sets [SQL Server], mirrored backup media sets
- backup media [SQL Server], mirrored media
ms.assetid: 05a0b8d1-3585-4f77-972f-69d1c0d4aa9b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce3513c67a0087dd00021de75f360b19819b46db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645133"
---
# <a name="mirrored-backup-media-sets-sql-server"></a><span data-ttu-id="b3080-102">ミラー化バックアップ メディア セット (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b3080-102">Mirrored Backup Media Sets (SQL Server)</span></span>
    
> [!NOTE]  
>  <span data-ttu-id="b3080-103">ミラー化バックアップ メディア セットは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の Enterprise Edition のみでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b3080-103">Mirrored backup media sets are supported only in the Enterprise edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b3080-104">メディア セットをミラー化すると、バックアップ デバイスの誤動作の影響が小さくなるため、バックアップの信頼性が向上します。</span><span class="sxs-lookup"><span data-stu-id="b3080-104">Mirroring a media set increases backup reliability by reducing the impact of backup-device malfunctions.</span></span> <span data-ttu-id="b3080-105">バックアップはデータ損失に対する最後の防護策なので、このような誤動作は非常に深刻です。</span><span class="sxs-lookup"><span data-stu-id="b3080-105">These malfunctions are very serious because backups are the last line of defense against data loss.</span></span> <span data-ttu-id="b3080-106">データベースが大きくなるにつれて、バックアップ デバイスやメディアの障害によってバックアップを復元できなくなる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="b3080-106">As databases grow, the probability increases that a failure of a backup device or media will make a backup nonrestorable.</span></span> <span data-ttu-id="b3080-107">バックアップ メディアをミラー化すると、冗長性によってバックアップの信頼性が向上します。</span><span class="sxs-lookup"><span data-stu-id="b3080-107">Mirroring backup media increases the reliability of backups by providing redundancy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3080-108">メディア セットの概要については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)の Enterprise Edition のみでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b3080-108">For information about media sets in general, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="b3080-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b3080-109">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="b3080-110">ミラー化メディア セットの概要</span><span class="sxs-lookup"><span data-stu-id="b3080-110">Overview of Mirrored Media Sets</span></span>](#OverviewofMirroredMediaSets)  
  
-   [<span data-ttu-id="b3080-111">バックアップ ミラーのハードウェア要件</span><span class="sxs-lookup"><span data-stu-id="b3080-111">Hardware Requirements for Backup Mirrors</span></span>](#HardwareReqs)  
  
-   [<span data-ttu-id="b3080-112">関連タスク</span><span class="sxs-lookup"><span data-stu-id="b3080-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="overview-of-mirrored-media-sets"></a><a name="OverviewofMirroredMediaSets"></a> <span data-ttu-id="b3080-113">ミラー化メディア セットの概要</span><span class="sxs-lookup"><span data-stu-id="b3080-113">Overview of Mirrored Media Sets</span></span>  
 <span data-ttu-id="b3080-114">メディアのミラー化は、メディア セットのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="b3080-114">Media mirroring is a property of the media set.</span></span> <span data-ttu-id="b3080-115">*ミラー化メディア セット* は、メディア セットの複数のコピー (*ミラー*) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b3080-115">A *mirrored media set* consists of multiple copies (*mirrors*) of the media set.</span></span> <span data-ttu-id="b3080-116">メディア セットには、1 つ以上のメディア ファミリが含まれており、各メディア ファミリが 1 つのバックアップ デバイスに対応します。</span><span class="sxs-lookup"><span data-stu-id="b3080-116">A media set contains one or more media families, each of which corresponds to a backup device.</span></span> <span data-ttu-id="b3080-117">たとえば、BACKUP DATABASE ステートメントの TO 句に 3 つのデバイスを指定する場合、BACKUP によって 1 つのデバイスにつき 3 つのメディア ファミリにデータが分散されます。</span><span class="sxs-lookup"><span data-stu-id="b3080-117">For example, if the TO clause of a BACKUP DATABASE statement lists three devices, BACKUP spreads the data among three media families, one per device.</span></span> <span data-ttu-id="b3080-118">メディア ファミリとミラーの数は、メディア セットを作成するときに定義します (BACKUP DATABASE ステートメントで WITH FORMAT を指定します)。</span><span class="sxs-lookup"><span data-stu-id="b3080-118">The number of media families and mirrors is defined when the media set is created (by a BACKUP DATABASE statement that specifies WITH FORMAT).</span></span>  
  
 <span data-ttu-id="b3080-119">ミラー化メディア セットには、2 ～ 4 つのミラーがあります。</span><span class="sxs-lookup"><span data-stu-id="b3080-119">A mirrored media set possesses from two to four mirrors.</span></span> <span data-ttu-id="b3080-120">各ミラーには、メディア セットのすべてのメディア ファミリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b3080-120">Each mirror contains all the media families in the media set.</span></span> <span data-ttu-id="b3080-121">ミラーには、メディア ファミリ 1 つにつき、同数のデバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="b3080-121">The mirrors require the same number of devices, one per media family.</span></span> <span data-ttu-id="b3080-122">各ミラーには、メディア ファミリごとに別のバックアップ デバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="b3080-122">Each mirror requires a separate backup device for each media family.</span></span> <span data-ttu-id="b3080-123">たとえば、3 つのミラーを持つ 4 つのメディア ファミリで構成されるミラー化メディア セットには、12 台のバックアップ デバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="b3080-123">For example, a mirrored media set that consists of four media families with three mirrors requires twelve backup devices.</span></span> <span data-ttu-id="b3080-124">これらのデバイスはすべて同等であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="b3080-124">All of these devices must be equivalent.</span></span> <span data-ttu-id="b3080-125">たとえば、同じ製造元で同じモデル番号のテープ ドライブなどです。</span><span class="sxs-lookup"><span data-stu-id="b3080-125">For example, tape drives that have the same model number from the same manufacturer.</span></span>  
  
 <span data-ttu-id="b3080-126">次の図は、2 つのミラーを持つ 2 つのメディア ファミリで構成されるミラー化メディア セットの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="b3080-126">The following illustration shows an example of a mirrored media set that consists of two media families with two mirrors.</span></span> <span data-ttu-id="b3080-127">各メディア ファミリには 3 つのメディア ボリュームがあり、ミラーごとに 1 回ずつバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="b3080-127">Each media family contains three media volumes, which are backed up one time per mirror.</span></span>  
  
 <span data-ttu-id="b3080-128">![ミラー化メディア セット: 2 つのミラーから成る 2 つのファミリ](../../database-engine/media/bnr-backup-media-mirror.gif "ミラー化メディア セット: 2 つのミラーから成る 2 つのファミリ")</span><span class="sxs-lookup"><span data-stu-id="b3080-128">![Mirrored media set: two families with two mirrors](../../database-engine/media/bnr-backup-media-mirror.gif "Mirrored media set: two families with two mirrors")</span></span>  
  
 <span data-ttu-id="b3080-129">ミラーの対応するボリュームは、同じ内容です。</span><span class="sxs-lookup"><span data-stu-id="b3080-129">Corresponding volumes on the mirrors have identical contents.</span></span> <span data-ttu-id="b3080-130">これにより、復元時にボリュームを交換できます。</span><span class="sxs-lookup"><span data-stu-id="b3080-130">This makes them interchangeable at restore time.</span></span> <span data-ttu-id="b3080-131">たとえば、上の図では、テープ 2 の 3 番目のボリュームは、テープ 0 の 3 番目のボリュームと交換可能です。</span><span class="sxs-lookup"><span data-stu-id="b3080-131">For example, in the previous illustration, the third volume of tape2 is interchangeable with the third volume of tape0.</span></span>  
  
 <span data-ttu-id="b3080-132">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] では、ミラー化メディアの内容がすべて同じになるように、デバイスへの書き込みの同期をとっています。</span><span class="sxs-lookup"><span data-stu-id="b3080-132">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] guarantees that the mirrored media have identical contents by synchronizing writes to the devices.</span></span> <span data-ttu-id="b3080-133">いずれかのミラーが満杯になると、同じことが同時にすべてのミラーに起こります。</span><span class="sxs-lookup"><span data-stu-id="b3080-133">When any one of the mirrors fills, all the mirrors are spanned at one time.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b3080-134">ミラー化メディア セットは、ミラーを削除することによって暗黙的に分割できません。</span><span class="sxs-lookup"><span data-stu-id="b3080-134">A mirrored media set cannot be implicitly broken (split) by removing a mirror.</span></span> <span data-ttu-id="b3080-135">ミラー内のいずれかのテープまたはディスクが損傷を受けたり再フォーマットされたりすると、そのミラーはその後のバックアップに使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b3080-135">If any tape or disk in a mirror is damaged or reformatted, the mirror is no longer usable for additional backups.</span></span> <span data-ttu-id="b3080-136">少なくとも 1 つのミラーが完全な状態になっていれば、メディア セットを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="b3080-136">If at least one full mirror remains intact, the media set can be read.</span></span> <span data-ttu-id="b3080-137">すべてのミラーで特定のメディア ファミリが失われると、そのメディア セットは使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b3080-137">If every mirror loses a given media family, the media set is useless.</span></span>  
  
 <span data-ttu-id="b3080-138">すべてのミラーが存在する必要があるかどうかは、バックアップ操作と復元操作で異なります。</span><span class="sxs-lookup"><span data-stu-id="b3080-138">Backup and restore operations impose different requirements on whether all the mirrors must be present.</span></span> <span data-ttu-id="b3080-139">ミラー化メディア セットを書き込む (作成または拡張する) バックアップ操作では、すべてのミラーが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3080-139">For a backup operation to write (that is, to create or extend) a mirrored media set, all the mirrors must be present.</span></span> <span data-ttu-id="b3080-140">一方、ミラー化メディア セットからバックアップを復元する場合は、各メディア ファミリに対して 1 つのミラーだけを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b3080-140">In contrast, when you are restoring a backup from a mirrored media set, you can specify only a single mirror for each media family.</span></span> <span data-ttu-id="b3080-141">ファミリ数よりも少ない数のデバイスからでも復元できますが、各メディア ファミリが処理されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="b3080-141">You can restore from fewer devices than families, but each media family is processed only one time.</span></span> <span data-ttu-id="b3080-142">エラーが発生したとき、他に複数のミラーを用意しておくと復元に関する問題をすばやく解決できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3080-142">In the presence of errors, however, having the other mirrors enables some restore problems to be resolved quickly.</span></span> <span data-ttu-id="b3080-143">損傷したメディア ボリュームは、別のミラーの対応するボリュームで代替できます。</span><span class="sxs-lookup"><span data-stu-id="b3080-143">You can substitute a damaged media volume with the corresponding volume from another mirror.</span></span> <span data-ttu-id="b3080-144">これは、RESTORE および RESTORE VERIFYONLY によって、壊れたメディアと他のミラーの対応するバックアップ メディア ボリュームが置換されるためです。</span><span class="sxs-lookup"><span data-stu-id="b3080-144">This is because RESTORE and RESTORE VERIFYONLY support substitution of damaged media with the corresponding backup-media volume from another mirror.</span></span>  
  
##  <a name="hardware-requirements-for-backup-mirrors"></a><a name="HardwareReqs"></a> <span data-ttu-id="b3080-145">バックアップ ミラーのハードウェア要件</span><span class="sxs-lookup"><span data-stu-id="b3080-145">Hardware Requirements for Backup Mirrors</span></span>  
 <span data-ttu-id="b3080-146">ミラー化は、ディスクとテープの両方に適用されます (ディスクでは連続テープはサポートされていません)。</span><span class="sxs-lookup"><span data-stu-id="b3080-146">Mirroring applies both to disk and tape (disks do not support continuation tapes).</span></span> <span data-ttu-id="b3080-147">同一のバックアップ操作または復元操作に使用するバックアップ デバイスはすべて同じ種類、つまりディスクまたはテープのいずれかにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3080-147">All backup devices for a single backup or restore operation must be of the same type, disk or tape.</span></span>  
  
 <span data-ttu-id="b3080-148">これらの大まかな種類の中では、同じプロパティを持つ同等のデバイスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3080-148">Within these broader classes, you must use similar devices that have the same properties.</span></span> <span data-ttu-id="b3080-149">デバイスが同等でない場合は、エラー メッセージ (3212) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b3080-149">Insufficiently similar devices generate an error message (3212).</span></span> <span data-ttu-id="b3080-150">デバイスの不適合によって生じるリスクを回避するには、同じ製造元で同じモデル番号のドライブのみを使用するなど、同等のデバイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="b3080-150">To avoid the risk of a device mismatch, use devices that are equivalent, such as, only drives with the same model number from the same manufacturer.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b3080-151">関連タスク</span><span class="sxs-lookup"><span data-stu-id="b3080-151">Related Tasks</span></span>  
 <span data-ttu-id="b3080-152">**ミラー化バックアップ デバイスにバックアップするには**</span><span class="sxs-lookup"><span data-stu-id="b3080-152">**To back up to mirrored backup devices**</span></span>  
  
-   [<span data-ttu-id="b3080-153">ミラー化メディア セットへのバックアップ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b3080-153">Back Up to a Mirrored Media Set &#40;Transact-SQL&#41;</span></span>](back-up-to-a-mirrored-media-set-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3080-154">参照</span><span class="sxs-lookup"><span data-stu-id="b3080-154">See Also</span></span>  
 <span data-ttu-id="b3080-155">[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b3080-155">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 <span data-ttu-id="b3080-156">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b3080-156">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="b3080-157">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b3080-157">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="b3080-158">メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b3080-158">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
