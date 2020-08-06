---
title: '[バックアップ デバイス] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.general.f1
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d73bdf3ce4b88214286b5f232924d811716a247e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632530"
---
# <a name="backup-device-general-page"></a><span data-ttu-id="1cc41-102">[バックアップ デバイス] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="1cc41-102">Backup Device (General Page)</span></span>
  <span data-ttu-id="1cc41-103">**[全般]** ページを使用すると、論理バックアップ デバイスの全般プロパティを指定したり、表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-103">Use the **General** page to specify or view the general properties of a logical backup device.</span></span>  
  
 <span data-ttu-id="1cc41-104">**SQL Server Management Studio を使用してバックアップ デバイスの内容を表示するには**</span><span class="sxs-lookup"><span data-stu-id="1cc41-104">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="1cc41-105">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-105">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-106">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-106">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="1cc41-107">Options</span><span class="sxs-lookup"><span data-stu-id="1cc41-107">Options</span></span>  
 <span data-ttu-id="1cc41-108">**[デバイス名]**</span><span class="sxs-lookup"><span data-stu-id="1cc41-108">**Device name**</span></span>  
 <span data-ttu-id="1cc41-109">既存の論理バックアップ デバイスの名前を表示するか、新しい論理バックアップ デバイスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1cc41-109">View the name of an existing logical backup device or specify the name of a new logical backup device.</span></span>  
  
 <span data-ttu-id="1cc41-110">**[テープ]**</span><span class="sxs-lookup"><span data-stu-id="1cc41-110">**Tape**</span></span>  
 <span data-ttu-id="1cc41-111">**[テープ]** の一覧からバックアップ先テープ デバイスを表示したり、選択したりします。</span><span class="sxs-lookup"><span data-stu-id="1cc41-111">View or select the destination tape device in the **Tape** list.</span></span> <span data-ttu-id="1cc41-112">このオプションは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスを実行しているコンピューターにテープ ドライブが接続されている場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-112">This option is available only if a tape drive is attached to the computer that is running the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1cc41-113">リモート コンピューターのテープ バックアップ デバイスは、有効なバックアップ先ではありません。</span><span class="sxs-lookup"><span data-stu-id="1cc41-113">Tape backup devices on remote computers are not valid backup destinations.</span></span>  
  
 <span data-ttu-id="1cc41-114">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="1cc41-114">**File**</span></span>  
 <span data-ttu-id="1cc41-115">既存の論理バックアップ デバイスのバックアップ先ファイルを表示するか、新しい論理バックアップ デバイスのバックアップ先ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="1cc41-115">View the destination file of an existing logical backup device, or specify a destination file for a new logical backup device.</span></span>  
  
-   <span data-ttu-id="1cc41-116">既存の論理バックアップ デバイスを使用する場合、バックアップ ファイルのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-116">For an existing logical backup device, the path of the backup file is displayed.</span></span> <span data-ttu-id="1cc41-117">**[ファイル]** フィールドは編集できません。また、参照ボタンは使用できません。</span><span class="sxs-lookup"><span data-stu-id="1cc41-117">The **File** field is not editable, and the Browse button is unavailable.</span></span>  
  
-   <span data-ttu-id="1cc41-118">新しい論理バックアップ デバイスでは、論理バックアップ デバイスを定義しているバックアップ ファイルのパスを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cc41-118">For a new logical backup device, you must supply the path of the backup file for which you are defining the logical backup device.</span></span> <span data-ttu-id="1cc41-119">このファイルは、まだ存在していなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="1cc41-119">This file does not have to exist yet.</span></span>  
  
     <span data-ttu-id="1cc41-120">ローカル バックアップ ファイルを指定するには、 **[ファイル]** ボックスの右の参照ボタンをクリックできます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-120">To specify a local backup file, you can click the Browse button to the right of the **File** text box.</span></span> <span data-ttu-id="1cc41-121">その後、 **[データベース ファイルの検索]** ダイアログ ボックスを使用して、サーバー インスタンスを実行しているコンピューターの固定ドライブの任意の場所に移動できます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-121">Then, in the **Locate Database Files** dialog box, you can navigate to any location on any of the fixed drives on the computer running the server instance.</span></span> <span data-ttu-id="1cc41-122">バックアップ ファイルが存在しない場合、ダイアログ ボックスの **[ファイル名]** に使用するファイル名を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cc41-122">If the backup file does not exist yet, you must enter the filename you want to use in the **File name** field of that dialog box.</span></span>  
  
     <span data-ttu-id="1cc41-123">**[ファイル]** を手動で編集して、既定のパス、ファイル名、および拡張子をオーバーライドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-123">Alternatively, you can edit the **File** field manually to override the default path, file name, and extension.</span></span> <span data-ttu-id="1cc41-124">バックアップ先としてリモート ファイルを指定するには、完全修飾の汎用名前付け規則 (UNC) 名を入力してください。</span><span class="sxs-lookup"><span data-stu-id="1cc41-124">To specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="1cc41-125">詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cc41-125">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1cc41-126">ネットワークを経由してデータをバックアップすると、ネットワーク エラーが発生する可能性があります。バックアップ終了後にバックアップ操作を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1cc41-126">Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes.</span></span> <span data-ttu-id="1cc41-127">詳細については、「[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1cc41-127">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cc41-128">解説</span><span class="sxs-lookup"><span data-stu-id="1cc41-128">Remarks</span></span>  
 <span data-ttu-id="1cc41-129">単一または一連のバックアップ デバイス上にあるバックアップによって、1 つのメディア セットが構成されます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-129">The backups on a set of one or more backup devices compose a single media set.</span></span> <span data-ttu-id="1cc41-130">*メディア セット* とは、テープやディスク ファイルなどのバックアップ メディアに順番を付けてまとめたものです。バックアップ メディアには、1 回以上のバックアップ操作によって、固定型の複数のバックアップ デバイスを使用して書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-130">A *media set* is an ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span> <span data-ttu-id="1cc41-131">メディア セットの詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cc41-131">For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="1cc41-132">論理バックアップ デバイスに対応している物理バックアップ デバイスは、メディア セットの最初のバックアップを論理バックアップ デバイスに書き込むときに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-132">The physical backup device corresponding to a logical backup device is initialized when the first backup in the media set is written to the logical backup device.</span></span> <span data-ttu-id="1cc41-133">物理バックアップ デバイスが、まだ存在していないファイルの場合は、この時点で作成されます。</span><span class="sxs-lookup"><span data-stu-id="1cc41-133">If the physical backup device is a file that does not exist yet, it is created at that time.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1cc41-134">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1cc41-134">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1cc41-135">ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-135">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-136">テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-136">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-137">バックアップ先としてディスクまたはテープを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-137">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-138">バックアップ デバイスの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-138">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-139">バックアップの有効期限の設定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-139">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-140">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-140">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-141">バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-141">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-142">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-142">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="1cc41-143">デバイスからのバックアップ復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-143">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="1cc41-144">参照</span><span class="sxs-lookup"><span data-stu-id="1cc41-144">See Also</span></span>  
 <span data-ttu-id="1cc41-145">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1cc41-145">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="1cc41-146">メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1cc41-146">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
