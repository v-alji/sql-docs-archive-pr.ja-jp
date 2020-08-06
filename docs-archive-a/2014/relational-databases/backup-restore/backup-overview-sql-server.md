---
title: バックアップの概要 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], backing up data
- backups [SQL Server]
- database backups [SQL Server]
- backup types [SQL Server]
- data backups [SQL Server]
- backing up tables [SQL Server]
- database restores [SQL Server], backups
- backing up [SQL Server], about backing up
- restoring [SQL Server], backup types
- backups [SQL Server], about
- backups [SQL Server], table-level backups unsupported
ms.assetid: 09a6e0c2-d8fd-453f-9aac-4ff24a97dc1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60fbd0341c4e29c6f98cc4d5fe5a2cfabc9b703f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645691"
---
# <a name="backup-overview-sql-server"></a><span data-ttu-id="66ced-102">Backup Overview (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="66ced-102">Backup Overview (SQL Server)</span></span>
  <span data-ttu-id="66ced-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップ コンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="66ced-103">This topic introduces the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup component.</span></span> <span data-ttu-id="66ced-104">データを保護するためには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをバックアップすることが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="66ced-104">Backing up your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is essential for protecting your data.</span></span> <span data-ttu-id="66ced-105">ここでは、バックアップの種類およびバックアップの制限事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="66ced-105">This discussion covers backup types, and backup restrictions.</span></span> <span data-ttu-id="66ced-106">また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップ デバイスとバックアップ メディアについても取り上げます。</span><span class="sxs-lookup"><span data-stu-id="66ced-106">The topic also introduces [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices and backup media.</span></span>  
  
 <span data-ttu-id="66ced-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="66ced-107">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="66ced-108">コンポーネントおよび概念</span><span class="sxs-lookup"><span data-stu-id="66ced-108">Components and Concepts</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="66ced-109">バックアップの圧縮</span><span class="sxs-lookup"><span data-stu-id="66ced-109">Backup Compression</span></span>](#BackupCompression)  
  
-   [<span data-ttu-id="66ced-110">SQL Server でのバックアップ操作の制限事項</span><span class="sxs-lookup"><span data-stu-id="66ced-110">Restrictions on Backup Operations in SQL Server</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="66ced-111">関連タスク</span><span class="sxs-lookup"><span data-stu-id="66ced-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="66ced-112">コンポーネントおよび概念</span><span class="sxs-lookup"><span data-stu-id="66ced-112">Components and Concepts</span></span>  
 <span data-ttu-id="66ced-113">バックアップ (back up) (動詞)</span><span class="sxs-lookup"><span data-stu-id="66ced-113">back up [verb]</span></span>  
 <span data-ttu-id="66ced-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースまたはそのトランザクション ログからバックアップ デバイス (ディスクなど) にデータまたはログ レコードをコピーすることによって、データ バックアップまたはログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="66ced-114">Copies the data or log records from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.</span></span>  
  
 <span data-ttu-id="66ced-115">バックアップ (backup) (名詞)</span><span class="sxs-lookup"><span data-stu-id="66ced-115">backup [noun]</span></span>  
 <span data-ttu-id="66ced-116">障害の発生後、データの復元と復旧に使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データのコピー。</span><span class="sxs-lookup"><span data-stu-id="66ced-116">A copy of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data that can be used to restore and recover the data after a failure.</span></span> <span data-ttu-id="66ced-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データのバックアップは、データベース レベル、あるいは 1 つまたは複数のデータベース ファイル (ファイル グループ) レベルで作成されます。</span><span class="sxs-lookup"><span data-stu-id="66ced-117">A backup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data is created at the level of a database or one or more of its files or filegroups.</span></span> <span data-ttu-id="66ced-118">テーブルレベルのバックアップは作成できません。</span><span class="sxs-lookup"><span data-stu-id="66ced-118">Table-level backups cannot be created.</span></span> <span data-ttu-id="66ced-119">完全復旧モデルでは、データのバックアップに加えて、トランザクション ログのバックアップを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66ced-119">In addition to data backups, the full recovery model requires creating backups of the transaction log.</span></span>  
  
 [<span data-ttu-id="66ced-120">復旧モデル (recovery model)</span><span class="sxs-lookup"><span data-stu-id="66ced-120">recovery model</span></span>](recovery-models-sql-server.md)  
 <span data-ttu-id="66ced-121">データベースのトランザクション ログのメンテナンスを制御するデータベース プロパティ。</span><span class="sxs-lookup"><span data-stu-id="66ced-121">A database property that controls transaction log maintenance on a database.</span></span> <span data-ttu-id="66ced-122">復旧モデルの種類は、単純、完全、および一括ログの 3 種類です。</span><span class="sxs-lookup"><span data-stu-id="66ced-122">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="66ced-123">データベースのバックアップと復元の要件は、その復旧モデルによって決まります。</span><span class="sxs-lookup"><span data-stu-id="66ced-123">The recovery model of database determines its backup and restore requirements.</span></span>  
  
 [<span data-ttu-id="66ced-124">復元 (restore)</span><span class="sxs-lookup"><span data-stu-id="66ced-124">restore</span></span>](restore-and-recovery-overview-sql-server.md)  
 <span data-ttu-id="66ced-125">データを直近の状態まで戻す複数フェーズから成る処理。指定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップからすべてのデータおよびログ ページを指定されたデータベースにコピーするフェーズと、バックアップにログとして記録されているすべてのトランザクションをロールフォワード (ログに記録されている変更を適用) するフェーズとで構成されます。</span><span class="sxs-lookup"><span data-stu-id="66ced-125">A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.</span></span>  
  
 <span data-ttu-id="66ced-126">**バックアップの種類**</span><span class="sxs-lookup"><span data-stu-id="66ced-126">**Types of Backups**</span></span>  
  
 [<span data-ttu-id="66ced-127">コピーのみのバックアップ (copy-only backup)</span><span class="sxs-lookup"><span data-stu-id="66ced-127">copy-only backup</span></span>](copy-only-backups-sql-server.md)  
 <span data-ttu-id="66ced-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の通常のバックアップ シーケンスから独立した特殊な用途のバックアップ。</span><span class="sxs-lookup"><span data-stu-id="66ced-128">A special-use backup that is independent of the regular sequence of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span>  
  
 <span data-ttu-id="66ced-129">データ バックアップ (data backup)</span><span class="sxs-lookup"><span data-stu-id="66ced-129">data backup</span></span>  
 <span data-ttu-id="66ced-130">データのバックアップ。データベース全体 (データベース バックアップ)、データベースの一部 (部分バックアップ)、または一連のデータ ファイルやファイルグループ (ファイル バックアップ) の形式で存在します。</span><span class="sxs-lookup"><span data-stu-id="66ced-130">A backup of data in a complete database (a database backup), a partial database (a partial backup), or a set of data files or filegroups (a file backup).</span></span>  
  
 [<span data-ttu-id="66ced-131">データベース バックアップ (database backup)</span><span class="sxs-lookup"><span data-stu-id="66ced-131">database backup</span></span>](full-database-backups-sql-server.md)  
 <span data-ttu-id="66ced-132">データベースのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="66ced-132">A backup of a database.</span></span> <span data-ttu-id="66ced-133">データベースの完全バックアップは、バックアップが完了した時点のデータベース全体を表します。</span><span class="sxs-lookup"><span data-stu-id="66ced-133">Full database backups represent the whole database at the time the backup finished.</span></span> <span data-ttu-id="66ced-134">差分データベース バックアップには、最新の完全バックアップ以降に行われたデータベースへの変更のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="66ced-134">Differential database backups contain only changes made to the database since its most recent full database backup.</span></span>  
  
 [<span data-ttu-id="66ced-135">差分バックアップ (differential backup)</span><span class="sxs-lookup"><span data-stu-id="66ced-135">differential backup</span></span>](full-database-backups-sql-server.md)  
 <span data-ttu-id="66ced-136">データベース全体、データベースの一部、または一連のデータ ファイル (またはファイル グループ) の最新の完全バックアップ ( *差分ベース*) をベースとし、その差分ベース以後に変更されたデータ エクステントのみを含んだデータ バックアップ。</span><span class="sxs-lookup"><span data-stu-id="66ced-136">A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the *differential base*) and that contains only the data extents that have changed since the differential base.</span></span>  
  
 <span data-ttu-id="66ced-137">部分的な差分バックアップでは、ファイル グループのデータのうち、前回の部分バックアップ以降に変更されたデータだけが記録されます。この前回の部分バックアップを差分に対するベースと呼びます。</span><span class="sxs-lookup"><span data-stu-id="66ced-137">A differential partial backup records only the data extents that have changed in the filegroups since the previous partial backup, known as the base for the differential.</span></span>  
  
 <span data-ttu-id="66ced-138">完全バックアップ (full backup)</span><span class="sxs-lookup"><span data-stu-id="66ced-138">full backup</span></span>  
 <span data-ttu-id="66ced-139">特定のデータベース (または一連のファイルやファイル グループ) 内のデータがすべて含まれ、さらに、データを復旧するために必要なログも含んだデータ バックアップ。</span><span class="sxs-lookup"><span data-stu-id="66ced-139">A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.</span></span>  
  
 [<span data-ttu-id="66ced-140">ログ バックアップ (log backup)</span><span class="sxs-lookup"><span data-stu-id="66ced-140">log backup</span></span>](transaction-log-backups-sql-server.md)  
 <span data-ttu-id="66ced-141">前回のログ バックアップでバックアップされなかったすべてのログ レコードを含むトランザクション ログのバックアップ</span><span class="sxs-lookup"><span data-stu-id="66ced-141">A backup of transaction logs that includes all log records that were not backed up in a previous log backup.</span></span> <span data-ttu-id="66ced-142">(完全復旧モデル)。</span><span class="sxs-lookup"><span data-stu-id="66ced-142">(full recovery model)</span></span>  
  
 [<span data-ttu-id="66ced-143">ファイル バックアップ (file backup)</span><span class="sxs-lookup"><span data-stu-id="66ced-143">file backup</span></span>](full-file-backups-sql-server.md)  
 <span data-ttu-id="66ced-144">1 つ以上のデータベース ファイルまたはファイル グループから成るバックアップ。</span><span class="sxs-lookup"><span data-stu-id="66ced-144">A backup of one or more database files or filegroups.</span></span>  
  
 [<span data-ttu-id="66ced-145">部分バックアップ (partial backup)</span><span class="sxs-lookup"><span data-stu-id="66ced-145">partial backup</span></span>](partial-backups-sql-server.md)  
 <span data-ttu-id="66ced-146">データベースの一部のファイル グループのデータのみを格納します。プライマリ ファイル グループ、すべての読み取り/書き込みファイル グループのほか、必要に応じて指定した読み取り専用ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="66ced-146">Contains data from only some of the filegroups in a database, including the data in the primary filegroup, every read/write filegroup, and any optionally-specified read-only files.</span></span>  
  
 <span data-ttu-id="66ced-147">**バックアップメディアの用語と定義**</span><span class="sxs-lookup"><span data-stu-id="66ced-147">**Backup Media Terms and Definitions**</span></span>  
  
 [<span data-ttu-id="66ced-148">バックアップ デバイス (backup device)</span><span class="sxs-lookup"><span data-stu-id="66ced-148">backup device</span></span>](backup-devices-sql-server.md)  
 <span data-ttu-id="66ced-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップの書き込みと復元に使用されるディスクまたはテープ デバイス。</span><span class="sxs-lookup"><span data-stu-id="66ced-149">A disk or tape device to which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups are written and from which they can be restored.</span></span> <span data-ttu-id="66ced-150">SQL Server のバックアップは、Azure Blob Storage サービスに書き込むこともできます。バックアップ先とバックアップ ファイルの名前を指定するには **URL** 形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="66ced-150">SQL Server backups can also be written to an Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file..</span></span> <span data-ttu-id="66ced-151">詳細については、「 [Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66ced-151">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 [<span data-ttu-id="66ced-152">バックアップ メディア (backup media)</span><span class="sxs-lookup"><span data-stu-id="66ced-152">backup media</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="66ced-153">バックアップの書き込み先となる 1 つまたは複数のテープまたはディスク ファイル。</span><span class="sxs-lookup"><span data-stu-id="66ced-153">One or more tapes or disk files to which one or more backup have been written.</span></span>  
  
 [<span data-ttu-id="66ced-154">バックアップ セット (backup set)</span><span class="sxs-lookup"><span data-stu-id="66ced-154">backup set</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="66ced-155">正常に完了したバックアップ操作によってメディア セットに追加されるバックアップ コンテンツ。</span><span class="sxs-lookup"><span data-stu-id="66ced-155">The backup content that is added to a media set by a successful backup operation.</span></span>  
  
 [<span data-ttu-id="66ced-156">メディア ファミリ (media family)</span><span class="sxs-lookup"><span data-stu-id="66ced-156">media family</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="66ced-157">ミラー化されていない単一のデバイスまたはメディア セット内のミラー化されている一連のデバイスで作成されたバックアップ。</span><span class="sxs-lookup"><span data-stu-id="66ced-157">Backups created on a single nonmirrored device or a set of mirrored devices in a media set</span></span>  
  
 [<span data-ttu-id="66ced-158">メディア セット (media set)</span><span class="sxs-lookup"><span data-stu-id="66ced-158">media set</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="66ced-159">テープやディスク ファイルなどのバックアップ メディアに順番を付けてまとめたもの。バックアップ メディアには、1 回以上のバックアップ操作によって、固定型の複数のバックアップ デバイスを使用して書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="66ced-159">An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span>  
  
 [<span data-ttu-id="66ced-160">ミラー化メディア セット (mirrored media set)</span><span class="sxs-lookup"><span data-stu-id="66ced-160">mirrored media set</span></span>](mirrored-backup-media-sets-sql-server.md)  
 <span data-ttu-id="66ced-161">メディア セットの複数のコピー (ミラー)。</span><span class="sxs-lookup"><span data-stu-id="66ced-161">Multiple copies (mirrors) of a media set.</span></span>  
  
##  <a name="backup-compression"></a><a name="BackupCompression"></a><span data-ttu-id="66ced-162">バックアップの圧縮</span><span class="sxs-lookup"><span data-stu-id="66ced-162">Backup Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="66ced-163">以降のバージョンでは、バックアップの圧縮がサポートされ、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、圧縮されたバックアップを復元することができます。</span><span class="sxs-lookup"><span data-stu-id="66ced-163">and later versions support compressing backups, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions can restore a compressed backup.</span></span> <span data-ttu-id="66ced-164">詳細については、「[バックアップの圧縮 &#40;SQL Server&#41;](backup-compression-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66ced-164">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>  
  
##  <a name="restrictions-on-backup-operations-in-sql-server"></a><a name="Restrictions"></a><span data-ttu-id="66ced-165">SQL Server でのバックアップ操作に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="66ced-165">Restrictions on Backup Operations in SQL Server</span></span>  
 <span data-ttu-id="66ced-166">オンラインでデータベースを使用中であってもバックアップを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="66ced-166">Backup can occur while the database is online and being used.</span></span> <span data-ttu-id="66ced-167">ただし、次の制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="66ced-167">However, the following restrictions exist.</span></span>  
  
### <a name="offline-data-cannot-be-backed-up"></a><span data-ttu-id="66ced-168">オフライン データはバックアップできない</span><span class="sxs-lookup"><span data-stu-id="66ced-168">Offline Data Cannot Be Backed Up</span></span>  
 <span data-ttu-id="66ced-169">オフライン データを暗黙的または明示的に参照するバックアップ操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="66ced-169">Any backup operation that implicitly or explicitly references data that is offline fails.</span></span> <span data-ttu-id="66ced-170">よく見られる例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="66ced-170">Some typical examples include the following:</span></span>  
  
-   <span data-ttu-id="66ced-171">データベースの完全バックアップを要求したが、データベースのいずれかのファイル グループがオフラインである場合。</span><span class="sxs-lookup"><span data-stu-id="66ced-171">You request a full database backup, but one filegroup of the database is offline.</span></span> <span data-ttu-id="66ced-172">データベースの完全バックアップにはすべてのファイル グループが暗黙的に含まれるため、この操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="66ced-172">Because all filegroups are implicitly included in a full database backup, this operation fails.</span></span>  
  
     <span data-ttu-id="66ced-173">このデータベースをバックアップするには、ファイル バックアップを使用し、オンラインのファイル グループのみを指定します。</span><span class="sxs-lookup"><span data-stu-id="66ced-173">To back up this database, you can use a file backup and specify only the filegroups that are online.</span></span>  
  
-   <span data-ttu-id="66ced-174">部分バックアップを要求したが、読み取り/書き込みファイル グループがオフラインの場合。</span><span class="sxs-lookup"><span data-stu-id="66ced-174">You request a partial backup, but a read/write filegroup is offline.</span></span> <span data-ttu-id="66ced-175">部分バックアップにはすべての読み取り/書き込みファイル グループが必要なので、この操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="66ced-175">Because all read/write filegroups are required for a partial backup, the operation fails.</span></span>  
  
-   <span data-ttu-id="66ced-176">特定のファイルのファイル バックアップを要求したが、いずれかのファイルがオンラインでない場合。</span><span class="sxs-lookup"><span data-stu-id="66ced-176">You request a file backup of specific files, but one of the files is not online.</span></span> <span data-ttu-id="66ced-177">操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="66ced-177">The operation fails.</span></span> <span data-ttu-id="66ced-178">オンライン ファイルをバックアップするには、ファイル一覧からオフライン ファイルを削除し、操作を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="66ced-178">To back up the online files, you can omit the offline file from the file list and repeat the operation.</span></span>  
  
 <span data-ttu-id="66ced-179">通常、1 つ以上のデータ ファイルを使用できない状態でも、ログ バックアップは続行できます。</span><span class="sxs-lookup"><span data-stu-id="66ced-179">Typically, a log backup succeeds even if one or more data files are unavailable.</span></span> <span data-ttu-id="66ced-180">ただし、一括ログ復旧モデルで行われた一括ログ変更がいずれかのファイルに含まれている場合、バックアップを続行するにはすべてのファイルをオンラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="66ced-180">However, if any file contains bulk-logged changes made under the bulk-logged recovery model, all the files must be online for the backup to succeed.</span></span>  
  
### <a name="concurrency-restrictions-during-backup"></a><span data-ttu-id="66ced-181">バックアップ中のコンカレンシーの制限事項</span><span class="sxs-lookup"><span data-stu-id="66ced-181">Concurrency Restrictions During Backup</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="66ced-182">では、オンライン バックアップを使って、使用中のデータベースをバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="66ced-182">uses an online backup process to allow for a database backup while the database is still being used.</span></span> <span data-ttu-id="66ced-183">バックアップ中はほとんどの操作が可能です。たとえば、INSERT、UPDATE、または DELETE ステートメントはバックアップ操作中でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="66ced-183">During a backup, most operations are possible; for example, INSERT, UPDATE, or DELETE statements are allowed during a backup operation.</span></span> <span data-ttu-id="66ced-184">ただし、データベースの作成中または削除中にバックアップ操作を開始しようとすると、データベースの作成または削除操作が完了するまで、またはバックアップがタイムアウトするまで、バックアップ操作が待機します。</span><span class="sxs-lookup"><span data-stu-id="66ced-184">However, if you try to start a backup operation while a database file is being created or deleted, the backup operation waits until the create or delete operation is finished or the backup times out.</span></span>  
  
 <span data-ttu-id="66ced-185">データベース バックアップやトランザクション ログ バックアップ中に、次の操作を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="66ced-185">Operations that cannot run during a database backup or transaction log backup include the following:</span></span>  
  
-   <span data-ttu-id="66ced-186">ADD FILE または REMOVE FILE のいずれかのオプションが指定された ALTER DATABASE ステートメントなどのファイル管理操作。</span><span class="sxs-lookup"><span data-stu-id="66ced-186">File-management operations such as the ALTER DATABASE statement with either the ADD FILE or REMOVE FILE options.</span></span>  
  
-   <span data-ttu-id="66ced-187">データベースまたはファイルの圧縮操作。</span><span class="sxs-lookup"><span data-stu-id="66ced-187">Shrink database or shrink file operations.</span></span> <span data-ttu-id="66ced-188">これには自動圧縮操作も含まれます。</span><span class="sxs-lookup"><span data-stu-id="66ced-188">This includes auto-shrink operations.</span></span>  
  
-   <span data-ttu-id="66ced-189">バックアップ操作実行中にデータベース ファイルを作成または削除しようとすると、作成操作または削除操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="66ced-189">If you try to create or delete a database file while a backup operation is in progress, the create or delete operation fails.</span></span>  
  
 <span data-ttu-id="66ced-190">バックアップ操作がファイル管理操作または圧縮操作の実行と重複すると、競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="66ced-190">If a backup operation overlaps with a file-management operation or shrink operation, a conflict occurs.</span></span> <span data-ttu-id="66ced-191">競合する操作のどちらが先に開始されたかにかかわらず、1 つ目の操作によって設定されたロックのタイムアウトを 2 つ目の操作が待機します(タイムアウト期間はセッション タイムアウトの設定によって制御されます)。ロックがタイムアウト期間内に解放されると、2 番目の操作が開始されます。</span><span class="sxs-lookup"><span data-stu-id="66ced-191">Regardless of which of the conflicting operation began first, the second operation waits for the lock set by the first operation to time out. (The time-out period is controlled by a session time-out setting.) If the lock is released during the time-out period, the second operation continues.</span></span> <span data-ttu-id="66ced-192">ロックがタイムアウトになると、2 番目の操作は実行されません。</span><span class="sxs-lookup"><span data-stu-id="66ced-192">If the lock times out, the second operation fails.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="66ced-193">関連タスク</span><span class="sxs-lookup"><span data-stu-id="66ced-193">Related Tasks</span></span>  
 <span data-ttu-id="66ced-194">**バックアップ デバイスとバックアップ メディアを操作するには**</span><span class="sxs-lookup"><span data-stu-id="66ced-194">**To work with backup devices and backup media**</span></span>  
  
-   [<span data-ttu-id="66ced-195">ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-195">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="66ced-196">テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-196">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="66ced-197">バックアップ先としてディスクまたはテープを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-197">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="66ced-198">バックアップ デバイスの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-198">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="66ced-199">バックアップの有効期限の設定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-199">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="66ced-200">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-200">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="66ced-201">バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-201">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="66ced-202">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-202">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="66ced-203">デバイスからのバックアップ復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-203">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
-   [<span data-ttu-id="66ced-204">チュートリアル:Azure Blob Storage サービスへの SQL Server のバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="66ced-204">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
 <span data-ttu-id="66ced-205">**バックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="66ced-205">**To create a backup**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66ced-206">部分バックアップまたはコピーのみのバックアップでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントにそれぞれ PARTIAL オプションまたは COPY_ONLY オプションを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="66ced-206">For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL or COPY_ONLY option, respectively.</span></span>  
  
-   [<span data-ttu-id="66ced-207">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-207">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="66ced-208">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-208">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="66ced-209">ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-209">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="66ced-210">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-210">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="66ced-211">データベースが破損したときのトランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-211">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [<span data-ttu-id="66ced-212">バックアップ中または復元中にバックアップ チェックサムを有効または無効にする &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-212">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [<span data-ttu-id="66ced-213">バックアップまたは復元の操作をエラー発生後に続行するか停止するかを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-213">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
-   [<span data-ttu-id="66ced-214">リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-214">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="66ced-215">チュートリアル:Azure Blob Storage サービスへの SQL Server のバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="66ced-215">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="66ced-216">参照</span><span class="sxs-lookup"><span data-stu-id="66ced-216">See Also</span></span>  
 <span data-ttu-id="66ced-217">[SQL Server データベースのバックアップと復元](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="66ced-217">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="66ced-218">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="66ced-218">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="66ced-219">[メンテナンス プラン](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="66ced-219">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 <span data-ttu-id="66ced-220">[トランザクション ログ &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="66ced-220">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="66ced-221">復旧モデル &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66ced-221">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
