---
title: '[バックアップ デバイス] ([メディアの内容] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.contents.f1
ms.assetid: 5fc7bd22-b6d8-4af1-8a58-2e7d0b994d08
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 07204b5e05ce9fc17e6ea23450066f9f58b7cf87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641697"
---
# <a name="backup-device-media-contents-page"></a><span data-ttu-id="ff6f5-102">[バックアップ デバイス] ([メディアの内容] ページ)</span><span class="sxs-lookup"><span data-stu-id="ff6f5-102">Backup Device (Media Contents Page)</span></span>
  <span data-ttu-id="ff6f5-103">**[バックアップ デバイス]** ダイアログ ボックスを使用すると、バックアップの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-103">Use the **Backup Device** dialog box to view the backup information.</span></span> <span data-ttu-id="ff6f5-104">ここでは、デバイス、メディア、メディア セット、バックアップ セットの情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-104">This information describes the device, the media, the media set, and the backup set or sets.</span></span>  
  
 <span data-ttu-id="ff6f5-105">**SQL Server Management Studio を使用してバックアップ デバイスの内容を表示するには**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-105">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="ff6f5-106">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-106">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-107">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-107">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="ff6f5-108">Options</span><span class="sxs-lookup"><span data-stu-id="ff6f5-108">Options</span></span>  
 <span data-ttu-id="ff6f5-109">個々のメディア、メディア セット、バックアップ セットに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-109">View information about the individual media, media set, and backup sets.</span></span>  
  
 <span data-ttu-id="ff6f5-110">**メディア**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-110">**Media**</span></span>  
 <span data-ttu-id="ff6f5-111">バックアップ情報が保存されるディスク、またはテープのセットです。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-111">A disk or set of tapes on which backup information is stored.</span></span>  
  
 <span data-ttu-id="ff6f5-112">**[メディア シーケンス]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-112">**Media sequence**</span></span>  
 <span data-ttu-id="ff6f5-113">メディア シーケンス番号、ファミリ シーケンス番号、ミラー識別子を一覧表示します (それぞれ存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-113">Lists the media sequence number, the family sequence number, and the mirror identifier, if any.</span></span> <span data-ttu-id="ff6f5-114">物理的なバックアップ メディアには、メディアが使用された順序を示すメディア シーケンス番号がそれぞれに付けられます。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-114">The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used.</span></span> <span data-ttu-id="ff6f5-115">最初のバックアップ メディアには 1 が割り当てられ、2 番目のメディア (つまり最初の後続テープ) には 2 が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-115">The initial backup media is tagged with 1, the second (the first continuation tape) is tagged with 2, and so forth.</span></span> <span data-ttu-id="ff6f5-116">バックアップ セットを復元する際に、このシーケンス番号を使用することで、適切なメディアを適切な順序でマウントできます。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-116">When the backup set is restored, the media sequence numbers ensure that the operator restoring the backup mounts the correct media in the correct order.</span></span>  
  
 <span data-ttu-id="ff6f5-117">**[作成日]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-117">**Created on**</span></span>  
 <span data-ttu-id="ff6f5-118">メディア セットが作成された日付と時刻を表示します。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-118">Displays the creation date and time of the media set.</span></span>  
  
 <span data-ttu-id="ff6f5-119">**[メディア セット]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-119">**Media Set**</span></span>  
 <span data-ttu-id="ff6f5-120">メディア セットとは、一定の数のバックアップ デバイスを使用し、1 回以上のバックアップ操作で書き込まれたバックアップ メディアを番号順に並べた集合体です。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-120">A media set is an ordered collection of backup media to which one or more backup operations have written by using a constant number of backup devices.</span></span>  
  
 <span data-ttu-id="ff6f5-121">**名前**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-121">**Name**</span></span>  
 <span data-ttu-id="ff6f5-122">メディア セットの名前を表示します (メディア セットが存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-122">Displays the name of the media set, if any.</span></span>  
  
 <span data-ttu-id="ff6f5-123">**説明**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-123">**Description**</span></span>  
 <span data-ttu-id="ff6f5-124">メディア セットの説明を表示します (メディア セットが存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-124">Displays the description of the media set, if any.</span></span>  
  
 <span data-ttu-id="ff6f5-125">**[メディア ファミリ数]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-125">**Media family count**</span></span>  
 <span data-ttu-id="ff6f5-126">メディア セット内のファミリの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-126">Displays the number of families in the media set.</span></span> <span data-ttu-id="ff6f5-127">各メディア セットは、1 つ以上のメディア ファミリの集合体です。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-127">Each media set is a collection of one or more media families.</span></span> <span data-ttu-id="ff6f5-128">特定の 1 つのバックアップ デバイス (またはミラーリングされるバックアップ デバイスのグループ) に対するすべての出力が、1 つのメディア ファミリを形成します。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-128">All the output to a given single backup device (or group of mirrored backup devices) forms a single media family.</span></span> <span data-ttu-id="ff6f5-129">各メディア セットには、単独のデバイス (またはミラーリングされるデバイスのグループ) ごとに 1 つのメディア ファミリが含まれます。たとえば、メディア セットでミラーリングされないバックアップ デバイスが 2 つ使用されている場合、このメディア セットには 2 つのメディア ファミリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-129">Each media set contains one media family per separate device (or group of mirrored devices); for instance, if a media set uses two non-mirrored backup devices, the media set contains two media families.</span></span>  
  
 <span data-ttu-id="ff6f5-130">**[バックアップ セット]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-130">**Backup sets**</span></span>  
 <span data-ttu-id="ff6f5-131">メディアに収められているバックアップ セットに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-131">Displays information about the backup set or sets contained on the media.</span></span> <span data-ttu-id="ff6f5-132">バックアップ セットとは、正常に完了したバックアップ操作の結果です。バックアップ セットの内容は、一連のバックアップ デバイスのメディアに分散されます。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-132">A backup set is the result of a successful backup operation, whose content is distributed among the media on the set of backup devices.</span></span>  
  
|<span data-ttu-id="ff6f5-133">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="ff6f5-133">Header</span></span>|<span data-ttu-id="ff6f5-134">値</span><span class="sxs-lookup"><span data-stu-id="ff6f5-134">Values</span></span>|  
|------------|------------|  
|<span data-ttu-id="ff6f5-135">**名前**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-135">**Name**</span></span>|<span data-ttu-id="ff6f5-136">バックアップ セットの名前です。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-136">The name of the backup set.</span></span>|  
|<span data-ttu-id="ff6f5-137">**Type**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-137">**Type**</span></span>|<span data-ttu-id="ff6f5-138">バックアップされるオブジェクト: [データベース]、[ファイル]、または *\<blank>* (トランザクション ログ用)。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-138">The backed-up object: Database, File, or *\<blank>* (for transaction logs).</span></span>|  
|<span data-ttu-id="ff6f5-139">**コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-139">**Component**</span></span>|<span data-ttu-id="ff6f5-140">実行するバックアップの種類: [完全]、[差分]、[トランザクション ログ]。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-140">The type of backup performed: Full, Differential or Transaction Log.</span></span>|  
|<span data-ttu-id="ff6f5-141">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-141">**Server**</span></span>|<span data-ttu-id="ff6f5-142">バックアップ操作を実行した [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-142">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that performed the backup operation.</span></span>|  
|<span data-ttu-id="ff6f5-143">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-143">**Database**</span></span>|<span data-ttu-id="ff6f5-144">バックアップされたデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-144">The name of the database that was backed up.</span></span>|  
|<span data-ttu-id="ff6f5-145">**Position**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-145">**Position**</span></span>|<span data-ttu-id="ff6f5-146">ボリューム内でのバックアップ セットの位置。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-146">The position of the backup set in the volume.</span></span>|  
|<span data-ttu-id="ff6f5-147">**Date**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-147">**Date**</span></span>|<span data-ttu-id="ff6f5-148">バックアップ操作が完了したときの日付と時刻。クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-148">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
|<span data-ttu-id="ff6f5-149">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-149">**Size**</span></span>|<span data-ttu-id="ff6f5-150">バックアップ セットのサイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-150">The size of the backup set in bytes.</span></span>|  
|<span data-ttu-id="ff6f5-151">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-151">**User Name**</span></span>|<span data-ttu-id="ff6f5-152">バックアップ操作を実行したユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-152">The name of the user who performed the backup operation.</span></span>|  
|<span data-ttu-id="ff6f5-153">**[有効期限]**</span><span class="sxs-lookup"><span data-stu-id="ff6f5-153">**Expiration**</span></span>|<span data-ttu-id="ff6f5-154">バックアップ セットの期限が切れる日付と時刻。</span><span class="sxs-lookup"><span data-stu-id="ff6f5-154">The date and time the backup set expires.</span></span>|  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ff6f5-155">関連タスク</span><span class="sxs-lookup"><span data-stu-id="ff6f5-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ff6f5-156">ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-156">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-157">テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-157">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-158">バックアップ先としてディスクまたはテープを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-158">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-159">バックアップ デバイスの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-159">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-160">バックアップの有効期限の設定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-160">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-161">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-161">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-162">バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-162">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-163">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-163">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="ff6f5-164">デバイスからのバックアップ復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-164">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ff6f5-165">参照</span><span class="sxs-lookup"><span data-stu-id="ff6f5-165">See Also</span></span>  
 <span data-ttu-id="ff6f5-166">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ff6f5-166">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="ff6f5-167">メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ff6f5-167">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
