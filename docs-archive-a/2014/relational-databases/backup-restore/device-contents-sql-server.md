---
title: デバイス コンテンツ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.bnrdevicecontents.f1
ms.assetid: 95e1902e-8c7a-4830-bdf9-1a6aca414a24
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c904718eca671b1965a95d0d400f3f6fa075b500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640097"
---
# <a name="device-contents-sql-server"></a><span data-ttu-id="ec9fc-102">デバイス コンテンツ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ec9fc-102">Device Contents (SQL Server)</span></span>
  <span data-ttu-id="ec9fc-103">このダイアログ ボックスは、バックアップ情報の表示に使用します。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-103">Use this dialog box to view the backup information.</span></span> <span data-ttu-id="ec9fc-104">ここでは、デバイス、メディア、メディア セット、バックアップ セットの情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-104">This information describes the device, the media, the media set, and the backup set or sets.</span></span>  
  
 <span data-ttu-id="ec9fc-105">**SQL Server Management Studio を使用してバックアップ デバイスの内容を表示するには**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-105">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="ec9fc-106">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ec9fc-106">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="ec9fc-107">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ec9fc-107">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="ec9fc-108">Options</span><span class="sxs-lookup"><span data-stu-id="ec9fc-108">Options</span></span>  
 <span data-ttu-id="ec9fc-109">**メディア**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-109">**Media**</span></span>  
 <span data-ttu-id="ec9fc-110">バックアップ情報が保存されるディスク、またはテープのセットです。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-110">A disk or set of tapes on which backup information is stored.</span></span>  
  
 <span data-ttu-id="ec9fc-111">**[メディア シーケンス]**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-111">**Media sequence**</span></span>  
 <span data-ttu-id="ec9fc-112">メディア シーケンス番号、ファミリ シーケンス番号、ミラー識別子を一覧表示します (それぞれ存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-112">Lists the media sequence number, the family sequence number, and the mirror identifier, if any.</span></span> <span data-ttu-id="ec9fc-113">物理的なバックアップ メディアには、メディアが使用された順序を示すメディア シーケンス番号がそれぞれに付けられます。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-113">The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used.</span></span> <span data-ttu-id="ec9fc-114">最初のバックアップ メディアには 1 が割り当てられ、2 番目のメディア (つまり最初の後続テープ) には 2 が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-114">The initial backup medium is tagged with 1, the second (the first continuation tape) is tagged with 2, and so forth.</span></span> <span data-ttu-id="ec9fc-115">バックアップ セットを復元する際に、このシーケンス番号を使用することで、適切なメディアを適切な順序でマウントできます。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-115">When the backup set is restored, the media sequence numbers ensure that the operator that restores the backup mounts the correct media in the correct order.</span></span>  
  
 <span data-ttu-id="ec9fc-116">**[作成日]**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-116">**Created on**</span></span>  
 <span data-ttu-id="ec9fc-117">メディアの日付を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-117">Displays the media date.</span></span>  
  
 <span data-ttu-id="ec9fc-118">**[メディア セット]**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-118">**Media Set**</span></span>  
 <span data-ttu-id="ec9fc-119">メディア セットとは、一定の数のバックアップ デバイスを使用し、1 回以上のバックアップ操作で書き込まれたバックアップ メディアを番号順に並べた集合体です。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-119">A media set is an ordered collection of backup media to which one or more backup operations have written using a constant number of backup devices.</span></span>  
  
 <span data-ttu-id="ec9fc-120">**名前**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-120">**Name**</span></span>  
 <span data-ttu-id="ec9fc-121">メディア セットの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-121">Displays the name of the media set.</span></span>  
  
 <span data-ttu-id="ec9fc-122">**説明**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-122">**Description**</span></span>  
 <span data-ttu-id="ec9fc-123">メディア セットの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-123">Displays the description media set.</span></span>  
  
 <span data-ttu-id="ec9fc-124">**[メディア ファミリ数]**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-124">**Media family count**</span></span>  
 <span data-ttu-id="ec9fc-125">メディア ファミリ数を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-125">Displays the media family count.</span></span> <span data-ttu-id="ec9fc-126">各メディア セットは、1 つ以上のメディア ファミリの集合体です。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-126">Each media set is a collection of one or more media families.</span></span> <span data-ttu-id="ec9fc-127">特定の 1 つのバックアップ デバイス (またはミラーリングされるバックアップ デバイスのグループ) に対するすべての出力が、1 つのメディア ファミリを形成します。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-127">All the output to a given single backup device (or group of mirrored backup devices) forms a single media family.</span></span> <span data-ttu-id="ec9fc-128">各メディア セットには、単独のデバイス (またはミラーリングされるデバイスのグループ) ごとに 1 つのメディア ファミリが含まれます。たとえば、メディア セットでミラーリングされないバックアップ デバイスが 2 つ使用されている場合、このメディア セットには 2 つのメディア ファミリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-128">Each media set contains one media family per separate device (or group of mirrored devices); for example, if a media set uses two nonmirrored backup devices, the media set contains two media families.</span></span>  
  
 <span data-ttu-id="ec9fc-129">**[バックアップ セット]**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-129">**Backup sets**</span></span>  
 <span data-ttu-id="ec9fc-130">メディアに収められているバックアップ セットに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-130">Displays information about the backup set or sets contained on the media.</span></span> <span data-ttu-id="ec9fc-131">バックアップ セットとは、正常に完了したバックアップ操作の結果です。バックアップ セットの内容は、一連のバックアップ デバイスのメディアに分散されます。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-131">A backup set is the result of a successful backup operation whose content is distributed among the media on the set of backup devices.</span></span>  
  
|<span data-ttu-id="ec9fc-132">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="ec9fc-132">Header</span></span>|<span data-ttu-id="ec9fc-133">値</span><span class="sxs-lookup"><span data-stu-id="ec9fc-133">Values</span></span>|  
|------------|------------|  
|<span data-ttu-id="ec9fc-134">**名前**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-134">**Name**</span></span>|<span data-ttu-id="ec9fc-135">バックアップ セットの名前です。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-135">The name of the backup set.</span></span>|  
|<span data-ttu-id="ec9fc-136">**Type**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-136">**Type**</span></span>|<span data-ttu-id="ec9fc-137">実行するバックアップの種類: [完全]、[差分]、[トランザクション ログ]。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-137">The type of backup performed: Full, Differential or Transaction Log.</span></span>|  
|<span data-ttu-id="ec9fc-138">**コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-138">**Component**</span></span>|<span data-ttu-id="ec9fc-139">バックアップされるコンポーネント:[データベース]、[ファイル]、または *\<blank>* (トランザクション ログ用)。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-139">The backed-up component: Database, File, or *\<blank>* (for transaction logs).</span></span>|  
|<span data-ttu-id="ec9fc-140">**サーバー**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-140">**Server**</span></span>|<span data-ttu-id="ec9fc-141">バックアップ操作を実行した [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-141">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that performed the backup operation.</span></span>|  
|<span data-ttu-id="ec9fc-142">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-142">**Database**</span></span>|<span data-ttu-id="ec9fc-143">バックアップされたデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-143">The name of the database that was backed up.</span></span>|  
|<span data-ttu-id="ec9fc-144">**Position**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-144">**Position**</span></span>|<span data-ttu-id="ec9fc-145">ボリューム内でのバックアップ セットの位置。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-145">The position of the backup set in the volume.</span></span>|  
|<span data-ttu-id="ec9fc-146">**Date**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-146">**Date**</span></span>|<span data-ttu-id="ec9fc-147">バックアップ操作が完了したときの日付と時刻。クライアントの地域設定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-147">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
|<span data-ttu-id="ec9fc-148">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-148">**Size**</span></span>|<span data-ttu-id="ec9fc-149">バックアップ セットのサイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-149">The size of the backup set in bytes.</span></span>|  
|<span data-ttu-id="ec9fc-150">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-150">**User Name**</span></span>|<span data-ttu-id="ec9fc-151">バックアップ操作を実行したユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-151">The name of the user who performed the backup operation.</span></span>|  
|<span data-ttu-id="ec9fc-152">**[有効期限]**</span><span class="sxs-lookup"><span data-stu-id="ec9fc-152">**Expiration**</span></span>|<span data-ttu-id="ec9fc-153">バックアップ セットの期限が切れる日付と時刻。</span><span class="sxs-lookup"><span data-stu-id="ec9fc-153">The date and time the backup set expires.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec9fc-154">参照</span><span class="sxs-lookup"><span data-stu-id="ec9fc-154">See Also</span></span>  
 [<span data-ttu-id="ec9fc-155">メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ec9fc-155">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
