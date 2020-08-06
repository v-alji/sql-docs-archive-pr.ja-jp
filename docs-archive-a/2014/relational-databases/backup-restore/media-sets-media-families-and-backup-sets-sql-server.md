---
title: メディア セット、メディア ファミリ、およびバックアップ セット (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media sets [SQL Server], about media sets
- backup media [SQL Server], about backup media
- backups [SQL Server], media sets
- media sets [SQL Server]
- media headers [SQL Server]
- backup sets [SQL Server], about backup sets
- backup media [SQL Server], media sets
- backups [SQL Server], media families
- backup media [SQL Server], media families
- media families [SQL Server]
- backups [SQL Server], backup sets
- backup sets [SQL Server]
ms.assetid: 2b8f19a2-ee9d-4120-b194-fbcd2076a489
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 853451ea5a7c43cd073fdf75703b3c4651b442d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643447"
---
# <a name="media-sets-media-families-and-backup-sets-sql-server"></a><span data-ttu-id="fb31c-102">メディア セット、メディア ファミリ、およびバックアップ セット (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fb31c-102">Media Sets, Media Families, and Backup Sets (SQL Server)</span></span>
  <span data-ttu-id="fb31c-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を初めて使用するユーザーを対象とし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のバックアップと復元で使用する基本的なバックアップ メディア用語を紹介します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-103">This topic introduces the basic backup-media terminology of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore and is intended for readers who are new to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fb31c-104">ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でバックアップ メディアに使用する形式、バックアップ メディアとバックアップ デバイス間の対応付け、バックアップ メディアでのバックアップの構成、メディア セットとメディア ファミリに関するいくつかの注意点について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-104">This topic describes the format that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses for backup media, the correspondence between backup media and backup devices, the organization of backups on backup media, and several considerations for media sets and media families.</span></span> <span data-ttu-id="fb31c-105">古いメディア セットを新しいメディア セットと交換する前に行うバックアップ メディアの初期化およびフォーマット処理の手順、メディア セット内の古いバックアップ セットを上書きする方法、新しいバックアップ セットをメディア セットに追加する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-105">The topic also describes the steps initializing or formatting backup media before you use it for the first time or replace an old media set with a new media set, how to overwrite old backup sets in a media set, and how to append new backup sets to a media set.</span></span>

> [!NOTE]
>  <span data-ttu-id="fb31c-106">Azure Blob ストレージサービスへの SQL Server バックアップの詳細については、「 [Azure Blob Storage サービスを使用したバックアップと復元 SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-106">For more information on SQL Server backup to the Azure Blob storage service,, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>


##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="fb31c-107">用語と定義</span><span class="sxs-lookup"><span data-stu-id="fb31c-107">Terms and Definitions</span></span>
 <span data-ttu-id="fb31c-108">メディア セット (メディア セット (media set)) テープやディスク ファイルなどのバックアップ メディアに順番を付けてまとめたもの。バックアップ メディアには、1 回以上のバックアップ操作によって、固定型の複数のバックアップ デバイスを使用して書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-108">media set An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span>

 <span data-ttu-id="fb31c-109">メディア ファミリ (メディア ファミリ (media family)) ミラー化されていない単一のデバイスまたはメディア セット内のミラー化されている一連のデバイスで作成されたバックアップ。</span><span class="sxs-lookup"><span data-stu-id="fb31c-109">media family Backups created on a single nonmirrored device or a set of mirrored devices in a media set</span></span>

 <span data-ttu-id="fb31c-110">バックアップ セット (バックアップ セット (backup set)) 正常に完了したバックアップ操作によってメディア セットに追加されるバックアップ コンテンツ。</span><span class="sxs-lookup"><span data-stu-id="fb31c-110">backup set The backup content that is added to a media set by a successful backup operation.</span></span>


##  <a name="overview-of-media-sets-media-families-and-backup-sets"></a><a name="OvMediaSetsFamiliesBackupSets"></a><span data-ttu-id="fb31c-111">メディアセット、メディアファミリ、およびバックアップセットの概要</span><span class="sxs-lookup"><span data-stu-id="fb31c-111">Overview of Media Sets, Media Families, and Backup Sets</span></span>
 <span data-ttu-id="fb31c-112">1 つまたは複数の一連のバックアップ メディアにあるバックアップによって、1 つのメディア セットが構成されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-112">The backups on a set of one or more backup media compose a single media set.</span></span> <span data-ttu-id="fb31c-113">*"メディア セット"* とは、テープやディスク ファイル、Azure BLOB などの *"バックアップ メディア"* の順序付きコレクションのことです。バックアップ メディアは、1 つまたは複数のバックアップ操作によって、固定型の多数のバックアップ デバイスを使用して書き込まれています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-113">A *media set* is an ordered collection of *backup media*, tapes or disk files, or Azure Blobs, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span> <span data-ttu-id="fb31c-114">1 つのメディア セットでは、テープ ドライブ、ディスク ドライブ、または Azure BLOB を使用しますが、これらの複数を組み合わせることはありません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-114">A given media set uses tape drives, or disk drives or Azure blobs, but not a combination of two or more.</span></span> <span data-ttu-id="fb31c-115">たとえば、あるメディア セットに関連付けられているバックアップ デバイスが、 `\\.\TAPE0`、 `\\.\TAPE1`、 `\\.\TAPE2`という 3 台のテープ ドライブである場合を想定します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-115">For example, the backup devices associated with a media set might be three tape drives named `\\.\TAPE0`, `\\.\TAPE1`, and `\\.\TAPE2`.</span></span> <span data-ttu-id="fb31c-116">このメディア セットにはテープのみが含まれます。テープの数は最低 3 本です (デバイスごとに 1 本)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-116">That media set contains only tapes, starting with a minimum of three tapes (one per drive).</span></span> <span data-ttu-id="fb31c-117">バックアップ デバイスの種類と台数はメディア セットの作成時に決定され、変更できません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-117">The type and number of backup devices are established when a media set is created, and they cannot be changed.</span></span> <span data-ttu-id="fb31c-118">ただし、必要に応じて、バックアップ操作と復元操作の間に特定のデバイスを同じ種類のデバイスと交換できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-118">However, if necessary, between backup and restore operations a given device can be replaced with a device of the same type.</span></span>

 <span data-ttu-id="fb31c-119">メディア セットは、バックアップ メディアをフォーマットすることによって、バックアップ操作中にバックアップ メディア上に作成されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-119">A media set is created on the backup media during a backup operation by formatting the backup media.</span></span> <span data-ttu-id="fb31c-120">詳細については、このトピックの「 [新しいメディア セットの作成](#CreatingMediaSet)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-120">For more information, see [Creating a New Media Set](#CreatingMediaSet), later in this topic.</span></span> <span data-ttu-id="fb31c-121">フォーマットが終了すると、各ファイルまたはテープにメディア セット用のメディア ヘッダーが書き込まれ、バックアップ コンテンツの受け入れ準備が整います。</span><span class="sxs-lookup"><span data-stu-id="fb31c-121">After formatting, each file or tape contains a media header for the media set and is ready to receive backup content.</span></span> <span data-ttu-id="fb31c-122">ヘッダーが書き込まれると、バックアップ操作用に指定されているすべてのバックアップ デバイス上のバックアップ メディアに指定のデータをバックアップする作業に進みます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-122">With the header in place, the backup operation proceeds to back up the specified data to the backup media on all of the backup devices specified for the operation.</span></span>

> [!NOTE]
>  <span data-ttu-id="fb31c-123">メディア セットは、メディア ボリューム (テープまたはディスク ファイル) の破損に備えてミラー化できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-123">Media sets can be mirrored to protect against a damaged media volume (a tape or disk file).</span></span> <span data-ttu-id="fb31c-124">詳細については、「 [ミラー化バックアップ メディア セット &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-124">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>

 [!INCLUDE[ssEnterpriseEd10](../../includes/sskatmai-md.md)]<span data-ttu-id="fb31c-125">以降では、圧縮されたバックアップを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-125">or later can read compressed backups.</span></span> <span data-ttu-id="fb31c-126">詳細については、「[バックアップの圧縮 &#40;SQL Server&#41;](backup-compression-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-126">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>


### <a name="media-families"></a><span data-ttu-id="fb31c-127">メディア ファミリ</span><span class="sxs-lookup"><span data-stu-id="fb31c-127">Media Families</span></span>
 <span data-ttu-id="fb31c-128">*メディア ファミリ*とは、ミラー化されていない単一のデバイスまたはメディア セット内のミラー化されている一連のデバイスで作成されたバックアップの集合です。</span><span class="sxs-lookup"><span data-stu-id="fb31c-128">Backups created on a single nonmirrored device or a set of mirrored devices in a media set constitute a *media family*.</span></span> <span data-ttu-id="fb31c-129">メディア セット用に使用されているバックアップ デバイスの数によって、メディア セット内のメディア ファミリの数が決まります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-129">The number of backup devices used for the media set determines the number of media families in a media set.</span></span> <span data-ttu-id="fb31c-130">たとえば、ミラー化されていない 2 つのバックアップ デバイスを使用しているメディア セットには、2 つのメディア ファミリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-130">For example, if a media set uses two nonmirrored backup devices, the media set contains two media families.</span></span>

> [!NOTE]
>  <span data-ttu-id="fb31c-131">ミラー化メディア セットでは、各メディア ファミリがミラー化されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-131">In a mirrored media set, each media family is mirrored.</span></span> <span data-ttu-id="fb31c-132">たとえば、6 つのバックアップ デバイスを使用して 1 つのメディア セットをフォーマットし、そのメディア セットで 2 つのミラーが使用されている場合は、3 つのメディア ファミリがあります。各ファミリには、2 つの同等のバックアップ データ コピーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-132">For example, if six backup devices are used to format a media set, where two mirrors are used, there are three media families, each containing two equivalent copies of backup data.</span></span> <span data-ttu-id="fb31c-133">ミラー化メディア セットの詳細については、[ミラー化バックアップ メディア セット &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-133">For more information about mirrored media sets, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>

 <span data-ttu-id="fb31c-134">メディア ファミリ内の各テープまたはディスクには、 *メディア シーケンス番号*が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-134">Each tape or disk in a media family is assigned a *media sequence number*.</span></span> <span data-ttu-id="fb31c-135">ディスクのメディア シーケンス番号は常に 1 です。</span><span class="sxs-lookup"><span data-stu-id="fb31c-135">The media sequence number of a disk is always 1.</span></span> <span data-ttu-id="fb31c-136">テープ メディア ファミリでは、先頭テープのシーケンス番号が 1、2 番目のテープのシーケンス番号が 2 のように割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-136">In a tape media family, the sequence number of the initial tape is 1, the sequence number of the second tape is 2, and so forth.</span></span> <span data-ttu-id="fb31c-137">詳細については、「 [メディア セットとメディア ファミリの使用](#ConsiderationsForMediaSetFamilies)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-137">For more information, see [Using Media Sets and Families](#ConsiderationsForMediaSetFamilies).</span></span>

#### <a name="the-media-header"></a><span data-ttu-id="fb31c-138">メディア ヘッダー</span><span class="sxs-lookup"><span data-stu-id="fb31c-138">The Media Header</span></span>
 <span data-ttu-id="fb31c-139">バックアップ メディアの各ボリューム (ディスク ファイルまたはテープ) には、メディア ヘッダーが含まれています。メディア ヘッダーは、そのテープ (またはディスク) を使用する最初のバックアップ操作によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-139">Every volume of backup media (disk file or tape) contains a media header that is created when by the first backup operation that uses the tape (or disk).</span></span> <span data-ttu-id="fb31c-140">このヘッダーは、メディアが再フォーマットされるまでそのままの状態で維持されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-140">That header remains intact until the media is reformatted.</span></span>

 <span data-ttu-id="fb31c-141">メディア ヘッダーには、メディア (ディスク ファイルまたはテープ) を識別するために必要な情報と、そのメディアが属するメディア ファミリ内での位置を識別するために必要な情報がすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-141">The media header contains all of the information required to identify the media (disk file or tape) and its place within the media family to which it belongs.</span></span> <span data-ttu-id="fb31c-142">次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-142">This information includes:</span></span>

-   <span data-ttu-id="fb31c-143">メディア名。</span><span class="sxs-lookup"><span data-stu-id="fb31c-143">The name of the media.</span></span>

     <span data-ttu-id="fb31c-144">メディア名は省略可能ですが、メディアを明確に識別するためにメディア名を常に使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fb31c-144">The media name is optionally, but we recommend consistently using media names that clearly identify your media.</span></span> <span data-ttu-id="fb31c-145">メディア名は、そのメディアをフォーマットしたユーザーが指定します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-145">A media name is assigned by whoever formats the media.</span></span>

-   <span data-ttu-id="fb31c-146">メディア セットの一意の識別番号。</span><span class="sxs-lookup"><span data-stu-id="fb31c-146">The unique identification number of the media set.</span></span>

-   <span data-ttu-id="fb31c-147">メディア セット内のメディア ファミリの数。</span><span class="sxs-lookup"><span data-stu-id="fb31c-147">The number of media families in the media set.</span></span>

-   <span data-ttu-id="fb31c-148">このメディアを含んでいるメディア ファミリのシーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="fb31c-148">The sequence number of the media family containing this media.</span></span>

-   <span data-ttu-id="fb31c-149">メディア ファミリの一意の識別番号。</span><span class="sxs-lookup"><span data-stu-id="fb31c-149">The unique identification number for the media family.</span></span>

-   <span data-ttu-id="fb31c-150">メディア ファミリ内でのこのメディアのシーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="fb31c-150">The sequence number of this media in the media family.</span></span> <span data-ttu-id="fb31c-151">ディスク ファイルの場合、この値は常に 1 になります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-151">For a disk file, this value is always 1.</span></span>

-   <span data-ttu-id="fb31c-152">メディアの説明に MTF メディア ラベルまたはメディアの説明が含まれているかどうか。</span><span class="sxs-lookup"><span data-stu-id="fb31c-152">Whether the media description contains an MTF media label or a media description.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="fb31c-153">バックアップまたは復元操作に使用されるすべてのメディアは、という標準バックアップ形式を使用し [!INCLUDE[msCoName](../../includes/ssnoversion-md.md)] ます。これは、別のアプリケーションによって書き込まれた mtf メディアラベルを保持しますが、mtf メディアラベルを作成しません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-153">All media that is used for a backup or restore operation use a standard backup format called [!INCLUDE[msCoName](../../includes/ssnoversion-md.md)] preserves any MTF media label written by another application but does not write MTF media labels.</span></span>

-   <span data-ttu-id="fb31c-154">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Tape Format メディア ラベルまたはメディアの説明 (自由な形式のテキスト)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-154">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Tape Format media label or the media description (in free-form text).</span></span>

-   <span data-ttu-id="fb31c-155">ラベルを作成したバックアップ ソフトウェアの名前。</span><span class="sxs-lookup"><span data-stu-id="fb31c-155">The name of the backup software that wrote the label.</span></span>

-   <span data-ttu-id="fb31c-156">メディアをフォーマットしたソフトウェア ベンダーの一意のベンダー識別番号。</span><span class="sxs-lookup"><span data-stu-id="fb31c-156">The unique vendor identification number of the software vendor that formatted the media.</span></span>

-   <span data-ttu-id="fb31c-157">ラベルが作成された日時。</span><span class="sxs-lookup"><span data-stu-id="fb31c-157">The date and time the label was written.</span></span>

-   <span data-ttu-id="fb31c-158">セット内のミラーの数 (1 ～ 4)。1 はミラー化されていないデバイスを示します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-158">The number of mirrors in the set (1-4); 1 indicates an unmirrored device.</span></span>

 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="fb31c-159">では、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でフォーマットされたメディアを処理できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-159">can process media formatted by earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

### <a name="backup-sets"></a><span data-ttu-id="fb31c-160">バックアップ セット</span><span class="sxs-lookup"><span data-stu-id="fb31c-160">Backup Sets</span></span>
 <span data-ttu-id="fb31c-161">バックアップ操作が正常に行われると、メディア セットに 1 つの *バックアップ セット* が追加されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-161">A successful backup operation adds a single *backup set* to the media set.</span></span> <span data-ttu-id="fb31c-162">バックアップ セットは、バックアップが属するメディア セットの観点から表現されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-162">The backup set is described in terms of the media set to which the backup belongs.</span></span> <span data-ttu-id="fb31c-163">バックアップ メディアにメディア ファミリが 1 つしかない場合は、そのファミリにバックアップ セット全体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-163">If the backup media consists of only one media family, that family contains the entire backup set.</span></span> <span data-ttu-id="fb31c-164">バックアップ メディアが複数のメディア ファミリで構成されている場合、バックアップ セットはこれらのファミリ間で分散されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-164">If the backup media consists of multiple media families, the backup set is distributed among them.</span></span> <span data-ttu-id="fb31c-165">各メディアのバックアップ セットには、そのバックアップ セットを説明するヘッダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-165">On each medium, the backup set contains a header that describes the backup set.</span></span>

 <span data-ttu-id="fb31c-166">次の例は、バックアップ デバイスとして 3 つのテープ ドライブを使用し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] データベース用に `MyAdvWorks_MediaSet_1` というメディア セットを作成する [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-166">The following example shows a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that creates a media set called `MyAdvWorks_MediaSet_1` for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database using three tape drives as backup devices:</span></span>

```
BACKUP DATABASE AdventureWorks2012
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
WITH 
   FORMAT,
   MEDIANAME = 'MyAdvWorks_MediaSet_1'
```

 <span data-ttu-id="fb31c-167">このバックアップ操作が正常に実行されると、新しいメディア ヘッダーを含む 1 つの新しいメディア セットと、3 つのテープに分散されている 1 つのバックアップ セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-167">If successful, this backup operation results in a new media set containing a new media header and one backup set spread across three tapes.</span></span> <span data-ttu-id="fb31c-168">次の図は、この結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-168">The following figure illustrates these results:</span></span>

 <span data-ttu-id="fb31c-169">![メディア ヘッダーと最初のバックアップ セットを 3 つのテープに記録](../../database-engine/media/bnr-mediaset-new.gif "メディア ヘッダーと最初のバックアップ セットを 3 つのテープに記録")</span><span class="sxs-lookup"><span data-stu-id="fb31c-169">![Media header and first backup set on 3 tapes](../../database-engine/media/bnr-mediaset-new.gif "Media header and first backup set on 3 tapes")</span></span>

 <span data-ttu-id="fb31c-170">通常、メディア セットが作成されると、その後のバックアップ操作では、そのメディア セットにバックアップ セットが 1 つずつ追加されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-170">Typically, after a media set is created, subsequent backup operations, one after another, append their backup sets to the media set.</span></span> <span data-ttu-id="fb31c-171">関連するメディアまたはバックアップ デバイスの数にかかわらず、バックアップ セットで使用されるすべてのメディアによってメディア セットが構成されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-171">All of the media used by a backup set make up the media set, regardless of the number of media or backup devices involved.</span></span> <span data-ttu-id="fb31c-172">バックアップ セットは、メディア セット内での位置に従ってシーケンス番号が付けられています。この番号により、どのバックアップ セットを復元するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-172">Backup sets are sequentially numbered by their position in the media set, allowing you to specify which backup set to restore.</span></span>

 <span data-ttu-id="fb31c-173">メディア セットに対するすべてのバックアップ操作で、同じ数および種類のバックアップ デバイスに書き込みを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-173">Every backup operation to a media set must write to the same number and type of backup devices.</span></span> <span data-ttu-id="fb31c-174">複数のデバイスがある場合は、最初のバックアップ セットと同様に、後続のすべてのバックアップ セットの内容が、すべてのデバイス上のバックアップ メディアに分散されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-174">With multiple devices, as with the first backup set, the content of every subsequent backup set is distributed among the backup media on all of the devices.</span></span> <span data-ttu-id="fb31c-175">上記の例を続行するには、2 番目のバックアップ操作 (差分バックアップ) で同じメディア セットに情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-175">To continue the above example, a second backup operation (a differential backup) appends information to the same media set:</span></span>

```
BACKUP DATABASE AdventureWorks2012
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
WITH 
   NOINIT,
   MEDIANAME = 'AdventureWorksMediaSet1',
   DIFFERENTIAL
```

> [!NOTE]
>  <span data-ttu-id="fb31c-176">NOINIT オプションは既定ですが、わかりやすくするために含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-176">The NOINIT option is the default, but is included for clarity.</span></span>

 <span data-ttu-id="fb31c-177">2 番目のバックアップ操作が正常に終了すると、次のようにバックアップ内容を分散して、2 番目のバックアップ セットがメディア セットに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-177">If the second backup operation succeeds, it writes a second backup set to the media set, with the following distribution of backup content:</span></span>

 <span data-ttu-id="fb31c-178">![2 つ目のバックアップ セットを 3 つのメディア セット テープにまたがって記録](../../database-engine/media/bnr-mediaset-appendedto.gif "2 つ目のバックアップ セットを 3 つのメディア セット テープにまたがって記録")</span><span class="sxs-lookup"><span data-stu-id="fb31c-178">![Second backup set spread across 3 media-set tapes](../../database-engine/media/bnr-mediaset-appendedto.gif "Second backup set spread across 3 media-set tapes")</span></span>

 <span data-ttu-id="fb31c-179">バックアップを復元するとき、使用するバックアップを FILE オプションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-179">When you are restoring backups, you can use you the FILE option to specify which backups you want to use.</span></span> <span data-ttu-id="fb31c-180">次の例は、 **=** _データベースの完全バックアップを復元した後、同じメディア セットで差分バックアップを行う場合の FILE_ backup_set_file_number [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 句の使用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-180">The following example shows the use of FILE **=**_backup_set_file_number_ clauses when restoring a full database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database followed by a differential database backup on the same media set.</span></span> <span data-ttu-id="fb31c-181">メディア セットでは 3 つのバックアップ テープが使用されます。テープが装着されているテープ ドライブは `\\.\tape0`、 `tape1`、および `tape2`です。</span><span class="sxs-lookup"><span data-stu-id="fb31c-181">The media set uses three backup tapes, which are on tape drives `\\.\tape0`, `tape1`, and `tape2`.</span></span>

```
RESTORE DATABASE AdventureWorks2012 FROM TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
   WITH 
   MEDIANAME = 'AdventureWorksMediaSet1',
   FILE=1, 
   NORECOVERY;
RESTORE DATABASE AdventureWorks2012 FROM TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2' 
   WITH 
   MEDIANAME = 'AdventureWorksMediaSet1',
   FILE=2, 
   RECOVERY;
GO
```

 <span data-ttu-id="fb31c-182">メディア セット、メディア ファミリ、およびバックアップ セットに関する情報が保存される履歴テーブルの詳細については、[バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-182">For information about the history tables that store information about media sets and their media families and backup sets, see [Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md).</span></span>

 <span data-ttu-id="fb31c-183">メディア セット内のバックアップ メディアの数は、次のような要因によって決まります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-183">The number of backup media in a media set depends on several factors:</span></span>

-   <span data-ttu-id="fb31c-184">バックアップ デバイスの数</span><span class="sxs-lookup"><span data-stu-id="fb31c-184">Number of backup devices</span></span>

-   <span data-ttu-id="fb31c-185">バックアップ デバイスの種類</span><span class="sxs-lookup"><span data-stu-id="fb31c-185">Type of backup devices</span></span>

-   <span data-ttu-id="fb31c-186">バックアップ セットの数</span><span class="sxs-lookup"><span data-stu-id="fb31c-186">Number of backup sets</span></span>

##  <a name="using-media-sets-and-families"></a><a name="ConsiderationsForMediaSetFamilies"></a><span data-ttu-id="fb31c-187">メディアセットとファミリの使用</span><span class="sxs-lookup"><span data-stu-id="fb31c-187">Using Media Sets and Families</span></span>
 <span data-ttu-id="fb31c-188">このセクションでは、メディア セットとメディア ファミリの使用上の注意点について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-188">This section discusses several considerations for using media sets and media families.</span></span>



###  <a name="creating-a-new-media-set"></a><a name="CreatingMediaSet"></a><span data-ttu-id="fb31c-189">新しいメディアセットの作成</span><span class="sxs-lookup"><span data-stu-id="fb31c-189">Creating a New Media Set</span></span>
 <span data-ttu-id="fb31c-190">新しいメディア セットを作成するには、バックアップ メディア (テープまたはディスク ファイル) をフォーマットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-190">To create a new media set, you must format the backup media (one or more tapes or disk files).</span></span> <span data-ttu-id="fb31c-191">フォーマットを実行すると、バックアップ メディアが次のように変化します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-191">The formatting process changes the backup media as follows:</span></span>

1.  <span data-ttu-id="fb31c-192">古いヘッダー (存在する場合) が削除され、その結果バックアップ メディアの以前の内容が削除されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-192">Deletes the old header (if any), effectively deleting the previous contents of the backup media.</span></span>

     <span data-ttu-id="fb31c-193">テープ デバイスをフォーマットすると、現在マウントされているテープの以前の内容がすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-193">Formatting a tape device deletes all previous contents of the currently mounted tape.</span></span> <span data-ttu-id="fb31c-194">ディスクをフォーマットするときは、バックアップ操作に指定したファイルのみが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-194">Formatting a disk affects only the file that you specify for the backup operation</span></span>

2.  <span data-ttu-id="fb31c-195">各バックアップ デバイスのバックアップ メディア (テープまたはディスク ファイル) に新しいメディア ヘッダーが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-195">Writes a new media header on the backup media (tape or disk file) on each of the backup devices.</span></span>


###  <a name="backing-up-to-an-existing-media-set"></a><a name="UseExistingMediaSet"></a><span data-ttu-id="fb31c-196">既存のメディアセットへのバックアップ</span><span class="sxs-lookup"><span data-stu-id="fb31c-196">Backing Up to an Existing Media Set</span></span>
 <span data-ttu-id="fb31c-197">既存のメディア セットにバックアップする場合、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-197">When you are backing up to an existing media set, you have the following two options:</span></span>

-   <span data-ttu-id="fb31c-198">既存のバックアップ セットに追加します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-198">Append to the existing backup set.</span></span>

     <span data-ttu-id="fb31c-199">使用可能な領域を最大限に使用するには、一般に、新しいバックアップ セットを既存のメディア セットに追加します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-199">To make the best possible use of the available space, new backup sets typically are appended to existing media set.</span></span> <span data-ttu-id="fb31c-200">新しいバックアップ セットを追加した場合も、以前のバックアップはすべて保持されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-200">Appending to the backup preserves any prior backups.</span></span> <span data-ttu-id="fb31c-201">詳細については、このセクションの「 [既存のバックアップ セットへの追加](#Appending)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-201">For more information, see [Appending to Existing Backup Sets](#Appending), later in this section.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="fb31c-202">追加は BACKUP ステートメントの既定の動作ですが、NOINIT オプションを使用して明示的に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-202">Appending, which is the default behavior of the BACKUP, can be explicitly specified by using the NOINIT option.</span></span>

-   <span data-ttu-id="fb31c-203">既存のすべてのバックアップ セットを現在のバックアップで上書きします。現在のメディア ヘッダーはそのまま残します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-203">Overwrite all existing backup sets with the current backup, leaving the current media header in place.</span></span>

     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fb31c-204">のバックアップには、メディアを間違って上書きしないための保護手段が備えられています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-204">backup has safeguards to prevent you from accidentally overwriting media.</span></span> <span data-ttu-id="fb31c-205">ただし、あらかじめ定義した有効期限に達したバックアップ セットは、バックアップ操作により自動的に上書きできます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-205">However, backup can automatically overwrite backup sets that have reached a predefined expiration date.</span></span>

     <span data-ttu-id="fb31c-206">テープ ヘッダーの場合は、ヘッダーをそのまま残すことに意味があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-206">For tape headers, leaving the header in place can make sense.</span></span> <span data-ttu-id="fb31c-207">詳細については、このセクションの「 [バックアップ セットの上書き](#Overwriting)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-207">For more information, see [Overwriting Backup Sets](#Overwriting), later in this section.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="fb31c-208">既存のバックアップ セットの上書きは、BACKUP ステートメントの INIT オプションを使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-208">Overwriting existing backup sets is specified by using the INIT option of the BACKUP statement.</span></span>

####  <a name="appending-to-existing-backup-sets"></a><a name="Appending"></a><span data-ttu-id="fb31c-209">既存のバックアップセットへの追加</span><span class="sxs-lookup"><span data-stu-id="fb31c-209">Appending to Existing Backup Sets</span></span>
 <span data-ttu-id="fb31c-210">異なる時間に作成されたバックアップは、同じデータベースでも異なるデータベースでも同じメディアに記憶できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-210">Backups performed at different times from the same or different databases can be stored on the same media.</span></span> <span data-ttu-id="fb31c-211">他のバックアップ セットを既存のメディアに追加すると、メディアの既存のコンテンツはそのまま保持され、メディア上の最後のバックアップの後に新しいバックアップが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-211">By appending another backup set to existing media, the previous contents of the media remain intact, and the new backup is written after the end of the last backup on the media.</span></span>

 <span data-ttu-id="fb31c-212">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により常に新しいバックアップがメディアに追加されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-212">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] always appends new backups to media.</span></span> <span data-ttu-id="fb31c-213">追加は、必ずメディアの最後に行われます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-213">Appending can occur only at the end of the media.</span></span> <span data-ttu-id="fb31c-214">たとえば、メディア ボリュームに 5 個のバックアップ セットが含まれている場合、最初の 3 個のバックアップ セットをスキップして、4 番目のバックアップ セットに新しいバックアップ セットを上書きすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-214">For example, if a media volume contains five backup sets, it is not possible to skip the first three backup sets to overwrite the fourth backup set with a new backup set.</span></span>

 <span data-ttu-id="fb31c-215">テープ バックアップに BACKUP WITH NOREWIND を使用すると、操作の最後にテープは開いたままになります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-215">If you use BACKUP WITH NOREWIND for a tape backup, the tape will be left open at the end of the operation.</span></span> <span data-ttu-id="fb31c-216">その結果、テープを巻き戻し、再び前方向にスキャンして最後のバックアップ セットを見つける必要なく、テープにバックアップをさらに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-216">This allows you to append further backups to the tape without rewinding the tape and then scanning forward again to find the last backup set.</span></span> <span data-ttu-id="fb31c-217">**sys.dm_io_backup_tapes** 動的管理ビューで、開いているテープ ドライブの一覧を検索できます。詳細については、[sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-217">You can find the list of open tape drives in the **sys.dm_io_backup_tapes** dynamic management view; for more information, see [sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql).</span></span>

 <span data-ttu-id="fb31c-218">Microsoft Windows バックアップと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップでは同じメディアを共有できますが、同時には使用できません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-218">Microsoft Windows backups and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups can share the same media, but they are not interoperable.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fb31c-219">バックアップは、Windows データをバックアップできません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-219">backup cannot back up Windows data.</span></span>

> [!IMPORTANT]
>  [!INCLUDE[ssEnterpriseEd10](../../includes/sskatmai-md.md)]<span data-ttu-id="fb31c-220">以降のバージョンでは、圧縮されたバックアップを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-220">or later versions can read compressed backups.</span></span> <span data-ttu-id="fb31c-221">詳細については、「[バックアップの圧縮 &#40;SQL Server&#41;](backup-compression-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-221">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>


####  <a name="overwriting-backup-sets"></a><a name="Overwriting"></a><span data-ttu-id="fb31c-222">バックアップセットの上書き</span><span class="sxs-lookup"><span data-stu-id="fb31c-222">Overwriting Backup Sets</span></span>
 <span data-ttu-id="fb31c-223">既存のバックアップ セットの上書きは、BACKUP ステートメントの INIT オプションを使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-223">Overwriting of existing backup sets is specified by using the INIT option of the BACKUP statement.</span></span> <span data-ttu-id="fb31c-224">このオプションでは、メディア上のすべてのバックアップ セットが上書きされ、メディア ヘッダーがある場合は保持されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-224">This option overwrites all the backup sets on the media and preserve the media header, if any.</span></span> <span data-ttu-id="fb31c-225">メディア ヘッダーが存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-225">If no media header exists, one is created.</span></span>

 <span data-ttu-id="fb31c-226">テープ ヘッダーの場合は、ヘッダーをそのまま残すことに意味があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-226">For tape headers, leaving the header in place can make sense.</span></span> <span data-ttu-id="fb31c-227">ディスク バックアップ メディアの場合、バックアップ操作で指定されたバックアップ デバイスが使用したファイルだけが上書きされます。ディスク上のそれ以外のファイルは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-227">For disk backup media, only the files used by the backup devices specified in the backup operation are overwritten; other files on the disk are unaffected.</span></span> <span data-ttu-id="fb31c-228">バックアップを上書きする場合、既存のメディア ヘッダーを保持し、新しいバックアップをバックアップ デバイスの初めてのバックアップとして作成できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-228">When overwriting backups, any existing media header is preserved, and the new backup is created as the first backup on the backup device.</span></span> <span data-ttu-id="fb31c-229">既存のメディア ヘッダーがない場合、関連付けられたメディア名とメディアの説明が入った有効なメディア ヘッダーが自動的に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-229">If there is no existing media header, a valid media header with an associated media name and media description is written automatically.</span></span> <span data-ttu-id="fb31c-230">既存のメディア ヘッダーが無効な場合、バックアップ操作は終了します。</span><span class="sxs-lookup"><span data-stu-id="fb31c-230">If the existing media header is invalid, the backup operation terminates.</span></span> <span data-ttu-id="fb31c-231">メディアが空の場合、MEDIANAME、MEDIAPASSWORD、および MEDIADESCRIPTION が指定されていれば、それらを使用して新しいメディア ヘッダーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-231">If the media is empty, the new media header is generated with the given MEDIANAME, MEDIAPASSWORD, and MEDIADESCRIPTION, if any.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="fb31c-232">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降では、バックアップの作成での MEDIAPASSWORD オプションが廃止されました。</span><span class="sxs-lookup"><span data-stu-id="fb31c-232">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the MEDIAPASSWORD option is discontinued for creating backups.</span></span> <span data-ttu-id="fb31c-233">ただし、パスワード付きで作成されたバックアップを復元することは、引き続き可能です。</span><span class="sxs-lookup"><span data-stu-id="fb31c-233">However, you can still restore backups created with passwords.</span></span>

 <span data-ttu-id="fb31c-234">次のいずれかの条件が存在する場合、バックアップ メディアは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-234">Backup media is not overwritten if either of the following conditions exists:</span></span>

-   <span data-ttu-id="fb31c-235">メディア上の既存のバックアップ セットが失効していない</span><span class="sxs-lookup"><span data-stu-id="fb31c-235">The existing backups on the media have not expired.</span></span> <span data-ttu-id="fb31c-236">(SKIP が指定されている場合、有効期限はチェックされません)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-236">(If SKIP is specified, expiration is not checked.)</span></span>

     <span data-ttu-id="fb31c-237">有効期限は、バックアップの有効期間の完了日を指定しており、期限を過ぎると別のバックアップで上書きできるようになります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-237">The expiration date specifies the date that the backup expires and can be overwritten by another backup.</span></span> <span data-ttu-id="fb31c-238">有効期限はバックアップの作成時に指定できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-238">You can specify the expiration date when a backup is created.</span></span> <span data-ttu-id="fb31c-239">既定では、有効期限は **sp_configure** で設定された **media retention**オプションによって決まります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-239">By default, the expiration date is determined by the **media retention** option set with **sp_configure**.</span></span> <span data-ttu-id="fb31c-240">詳細については、「 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-240">For more information, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>

-   <span data-ttu-id="fb31c-241">メディア名が指定されても、バックアップ メディア上の名前とは一致していない。</span><span class="sxs-lookup"><span data-stu-id="fb31c-241">The media name, if provided, does not match the name on the backup media.</span></span>

     <span data-ttu-id="fb31c-242">メディア名は、メディアを識別しやすくするためのわかりやすい名前です。</span><span class="sxs-lookup"><span data-stu-id="fb31c-242">The media name is a descriptive name used for easy identification of the media.</span></span>

 <span data-ttu-id="fb31c-243">ただし、テープ上のバックアップが不要になったことがわかっているなど、既存のメディアに上書きできることが確かな場合は、このチェックを明示的にスキップできます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-243">If you are sure you want to overwrite the existing media (for example, if you know that the backups on the tape are no longer needed), you can explicitly skip these checks.</span></span>

 <span data-ttu-id="fb31c-244">バックアップ メディアが Microsoft Windows によってパスワードで保護されている場合、Microsoft SQL Server からメディアに書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="fb31c-244">If the backup media is password protected by Microsoft Windows, Microsoft SQL Server does not write to the media.</span></span> <span data-ttu-id="fb31c-245">パスワードで保護されたメディアに上書きするには、メディアを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-245">To overwrite media that is password protected, you must reinitialize the media.</span></span>


###  <a name="sequence-numbers"></a><a name="SequenceNumbers"></a><span data-ttu-id="fb31c-246">シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="fb31c-246">Sequence Numbers</span></span>
 <span data-ttu-id="fb31c-247">メディア セット内の複数のメディア ファミリ、またはメディア ファミリ内の複数のバックアップ メディアは、正しい順序で配置することが重要です。</span><span class="sxs-lookup"><span data-stu-id="fb31c-247">The correct order is important for multiple media families within a media set or multiple backup media within a media family.</span></span> <span data-ttu-id="fb31c-248">このため、バックアップ時に次のようにシーケンス番号が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-248">Therefore, backup assigns sequence numbers in the following ways:</span></span>

-   <span data-ttu-id="fb31c-249">メディア セット内のシーケンシャル メディア ファミリ</span><span class="sxs-lookup"><span data-stu-id="fb31c-249">Sequential media families within a media set</span></span>

     <span data-ttu-id="fb31c-250">メディア セット内のメディア ファミリには、メディア セット内の位置に応じて連番が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-250">Within a media set, the media families are numbered sequentially according to their position in the media set.</span></span> <span data-ttu-id="fb31c-251">メディア ファミリ番号は、 **backupmediafamily** テーブルの **family_sequence_number** 列に記録されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-251">The media-family number is recorded in the **family_sequence_number** column of the **backupmediafamily** table.</span></span>

-   <span data-ttu-id="fb31c-252">メディア ファミリ内の物理メディア</span><span class="sxs-lookup"><span data-stu-id="fb31c-252">Physical media within a media family</span></span>

     <span data-ttu-id="fb31c-253">メディア シーケンス番号は、メディア ファミリ内の物理メディアの順序を示しています。</span><span class="sxs-lookup"><span data-stu-id="fb31c-253">A media sequence number indicates the order of the physical media within a media family.</span></span> <span data-ttu-id="fb31c-254">先頭のバックアップ メディアのシーケンス番号は 1 なので、</span><span class="sxs-lookup"><span data-stu-id="fb31c-254">The sequence number is 1 for the initial backup media.</span></span> <span data-ttu-id="fb31c-255">1 が割り当てられます。2 番目のメディア、つまり最初の後続テープには 2 が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-255">This is tagged with 1; the second (the first continuation tape) is tagged with 2; and so on.</span></span> <span data-ttu-id="fb31c-256">バックアップ セットを復元するとき、このメディア シーケンス番号によって、オペレーターは適切なメディアを正しい順序でマウントできます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-256">When the backup set is restored, the media sequence numbers make sure that the operator restoring the backup mounts the correct media in the correct order.</span></span>

###  <a name="multiple-devices"></a><a name="MultipleDevices"></a> <span data-ttu-id="fb31c-257">複数のデバイス</span><span class="sxs-lookup"><span data-stu-id="fb31c-257">Multiple Devices</span></span>
 <span data-ttu-id="fb31c-258">複数のテープ ドライブまたはディスク ファイルを使用する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="fb31c-258">When you use multiple tape drives or disk files, the following considerations apply:</span></span>

-   <span data-ttu-id="fb31c-259">バックアップの場合</span><span class="sxs-lookup"><span data-stu-id="fb31c-259">For backup:</span></span>

     <span data-ttu-id="fb31c-260">後続のバックアップ操作では、最初のバックアップ操作で作成したメディア セット全体を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-260">The complete media set that is created by a backup operation must be used by all subsequent backup operations.</span></span> <span data-ttu-id="fb31c-261">たとえば、2 つのテープ バックアップ デバイスを使用して 1 つのメディア セットを作成した場合、同じメディア セットに関連した後続のすべてのバックアップ操作でも 2 つのバックアップ デバイスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-261">For example, if a media set was created by using two tape backup devices, all subsequent backup operations that involve the same media set must use two backup devices.</span></span>

-   <span data-ttu-id="fb31c-262">復元の場合</span><span class="sxs-lookup"><span data-stu-id="fb31c-262">For restore:</span></span>

     <span data-ttu-id="fb31c-263">ディスク バックアップからの復元とオンライン復元の場合、すべてのメディア ファミリを同時にマウントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-263">For any restore from disk backups and for any online restore, all the all media families must be concurrently mounted.</span></span> <span data-ttu-id="fb31c-264">テープ バックアップからのオフライン復元の場合は、ディスクの場合よりも少数のバックアップ デバイスを使用してメディア ファミリを処理できます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-264">For an offline restore from tape backups, you can process the media families from fewer backup devices.</span></span> <span data-ttu-id="fb31c-265">1 つのメディア ファミリの処理が完了してから、別のメディア ファミリを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb31c-265">Each media family must be processed completely before starting to process another media family.</span></span> <span data-ttu-id="fb31c-266">1 台のデバイスで復元する場合を除き、メディア ファミリは常に並列処理されます。</span><span class="sxs-lookup"><span data-stu-id="fb31c-266">Media families are always processed in parallel, unless they are being restored with a single device.</span></span>

##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fb31c-267">関連タスク</span><span class="sxs-lookup"><span data-stu-id="fb31c-267">Related Tasks</span></span>
 <span data-ttu-id="fb31c-268">**新しいメディア セットを作成するには**</span><span class="sxs-lookup"><span data-stu-id="fb31c-268">**To create a new media set**</span></span>

-   <span data-ttu-id="fb31c-269">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) ( **[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]** オプション)</span><span class="sxs-lookup"><span data-stu-id="fb31c-269">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Back up to a new media set, and erase all existing backup sets** option)</span></span>

-   <span data-ttu-id="fb31c-270">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (FORMAT オプション)</span><span class="sxs-lookup"><span data-stu-id="fb31c-270">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (FORMAT option)</span></span>

-   <xref:Microsoft.SqlServer.Management.Smo.Backup.FormatMedia%2A>

 <span data-ttu-id="fb31c-271">**新しいバックアップを既存のメディアに追加するには**</span><span class="sxs-lookup"><span data-stu-id="fb31c-271">**To append a new backup to existing media**</span></span>

-   <span data-ttu-id="fb31c-272">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) ( **[既存のバックアップ セットに追加する]** オプション)</span><span class="sxs-lookup"><span data-stu-id="fb31c-272">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Append to the existing backup set** option)</span></span>

-   <span data-ttu-id="fb31c-273">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (NOINIT オプション)</span><span class="sxs-lookup"><span data-stu-id="fb31c-273">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (NOINIT option)</span></span>

 <span data-ttu-id="fb31c-274">**既存のバックアップ セットを上書きするには**</span><span class="sxs-lookup"><span data-stu-id="fb31c-274">**To overwrite existing backup sets**</span></span>

-   <span data-ttu-id="fb31c-275">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) ( **[既存のすべてのバックアップ セットを上書きする]** オプション)</span><span class="sxs-lookup"><span data-stu-id="fb31c-275">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Overwrite all existing backup sets** option)</span></span>

-   <span data-ttu-id="fb31c-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (INIT オプション)</span><span class="sxs-lookup"><span data-stu-id="fb31c-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (INIT option)</span></span>

 <span data-ttu-id="fb31c-277">**有効期限を設定するには**</span><span class="sxs-lookup"><span data-stu-id="fb31c-277">**To set the expiration date**</span></span>

-   [<span data-ttu-id="fb31c-278">バックアップの有効期限の設定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb31c-278">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)

 <span data-ttu-id="fb31c-279">**メディア シーケンス番号およびファミリ シーケンス番号を表示するには**</span><span class="sxs-lookup"><span data-stu-id="fb31c-279">**To view the media sequence and family sequence numbers**</span></span>

-   [<span data-ttu-id="fb31c-280">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb31c-280">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)

-   <span data-ttu-id="fb31c-281">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) (**family_sequence_number** 列)</span><span class="sxs-lookup"><span data-stu-id="fb31c-281">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) (**family_sequence_number** column)</span></span>

 <span data-ttu-id="fb31c-282">**特定のバックアップ デバイス上のバックアップ セットを表示するには**</span><span class="sxs-lookup"><span data-stu-id="fb31c-282">**To view the backup sets on a particular backup device**</span></span>

-   [<span data-ttu-id="fb31c-283">バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb31c-283">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)

-   [<span data-ttu-id="fb31c-284">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb31c-284">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)

-   [<span data-ttu-id="fb31c-285">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb31c-285">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)

 <span data-ttu-id="fb31c-286">**バックアップ デバイス上のメディアのメディア ヘッダーを読み取るには**</span><span class="sxs-lookup"><span data-stu-id="fb31c-286">**To read the media header of the media on a backup device**</span></span>

-   [<span data-ttu-id="fb31c-287">RESTORE LABELONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb31c-287">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)


## <a name="see-also"></a><span data-ttu-id="fb31c-288">参照</span><span class="sxs-lookup"><span data-stu-id="fb31c-288">See Also</span></span>
 <span data-ttu-id="fb31c-289">[SQL Server データベースのバックアップと復元](back-up-and-restore-of-sql-server-databases.md) [&#40;バックアップと復元の実行中に発生する可能性のあるメディアエラー SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) [バックアップの履歴とヘッダーの情報](backup-history-and-header-information-sql-server.md)&#40;SQL Server&#41;ミラー化された[バックアップメディアセット](mirrored-backup-media-sets-sql-server.md)&#40;SQL Server&#41;[バックアップ &#40;](/sql/t-sql/statements/backup-transact-sql) transact-sql&#41;[復元](/sql/t-sql/statements/restore-statements-transact-sql)&#40;transact-sql [&#41;&#40;&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql) [sp_configure transact-sql &#40;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="fb31c-289">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) [Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql) [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)</span></span>


