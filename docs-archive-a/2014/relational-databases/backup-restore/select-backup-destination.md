---
title: '[バックアップ先の選択] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdest.f1
ms.assetid: f79e824b-1525-45de-8ede-513563af41b6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ffd1d2529dd13e42689bcf168c972d757fb5499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643413"
---
# <a name="select-backup-destination"></a><span data-ttu-id="fb39c-102">[バックアップ先の選択]</span><span class="sxs-lookup"><span data-stu-id="fb39c-102">Select Backup Destination</span></span>
  <span data-ttu-id="fb39c-103">**[バックアップ先の選択]** ダイアログ ボックスを使用すると、バックアップ先としてデバイスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="fb39c-103">Use the **Select Backup Destination** dialog box to select a device as your backup destination.</span></span> <span data-ttu-id="fb39c-104">バックアップ先として、ディスクまたは論理バックアップ デバイスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fb39c-104">A backup destination can be either a disk or a logical backup device.</span></span>  
  
 <span data-ttu-id="fb39c-105">**SQL Server Management Studio を使用してデータベースをバックアップするには**</span><span class="sxs-lookup"><span data-stu-id="fb39c-105">**To use SQL Server Management Studio to back up a database**</span></span>  
  
-   [<span data-ttu-id="fb39c-106">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb39c-106">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="fb39c-107">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb39c-107">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="fb39c-108">ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb39c-108">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="fb39c-109">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb39c-109">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="fb39c-110">Options</span><span class="sxs-lookup"><span data-stu-id="fb39c-110">Options</span></span>  
 <span data-ttu-id="fb39c-111">このダイアログ ボックスのオプションは、ディスクまたはテープのどちらをバックアップ先として選択しているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="fb39c-111">The options of this dialog box depend on whether you are selecting a destination on disk or on tape.</span></span>  
  
 <span data-ttu-id="fb39c-112">**[ディスクのバックアップ先]**</span><span class="sxs-lookup"><span data-stu-id="fb39c-112">**Destination on disk**</span></span>  
 <span data-ttu-id="fb39c-113">バックアップ先を指定するには、次のオプションのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="fb39c-113">To specify a backup destination, choose one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fb39c-114">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="fb39c-114">**File name**</span></span>|<span data-ttu-id="fb39c-115">ローカル ファイルまたはリモート ファイルをバックアップ先としてテキスト ボックスに入力するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fb39c-115">Choose this option to enter a local or remote file as the backup destination in the text box.</span></span><br /><br /> <span data-ttu-id="fb39c-116">ローカルファイルを指定するには、テキストボックスの右側にある参照ボタンをクリックし、サーバーを実行しているコンピューターの固定ドライブ上のファイルに移動するか、完全なパスとファイル名を直接入力します。たとえば、のように `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak` なります。</span><span class="sxs-lookup"><span data-stu-id="fb39c-116">To specify a local file, click the browse button to the right of the text box and navigate to a file on the fixed drives of the computer running the server, or enter the full path and file name directly; for example, `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`.</span></span><br /><br /> <span data-ttu-id="fb39c-117">バックアップ先としてリモート ファイルを指定するには、完全修飾の汎用名前付け規則 (UNC) 名を入力してください。</span><span class="sxs-lookup"><span data-stu-id="fb39c-117">To specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="fb39c-118">詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb39c-118">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span><br /><br /> <span data-ttu-id="fb39c-119">**\*\* 重要 \*\*** ネットワークを経由してデータをバックアップすると、ネットワーク エラーが発生する可能性があります。バックアップ終了後にバックアップ操作を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fb39c-119">**\*\* Important \*\*** Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes.</span></span> <span data-ttu-id="fb39c-120">詳細については、「[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb39c-120">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>|  
|<span data-ttu-id="fb39c-121">**バックアップ デバイス**</span><span class="sxs-lookup"><span data-stu-id="fb39c-121">**Backup device**</span></span>|<span data-ttu-id="fb39c-122">論理バックアップ デバイスを選択するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fb39c-122">Choose this option to select a logical backup device.</span></span><br /><br /> <span data-ttu-id="fb39c-123">注:ディスク バックアップ デバイスを作成する方法の詳細については、「[ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb39c-123">Note: For information about how to create a disk backup device, see [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md).</span></span>|  
  
 <span data-ttu-id="fb39c-124">**[テープのバックアップ先]**</span><span class="sxs-lookup"><span data-stu-id="fb39c-124">**Destination on tape**</span></span>  
 <span data-ttu-id="fb39c-125">サーバー (つまり、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンス) を実行しているコンピューターに、物理的に接続されているテープ ドライブ上のバックアップ先を指定します。</span><span class="sxs-lookup"><span data-stu-id="fb39c-125">Specify a backup destination on a tape drive physically connected to the computer running the server (that is, the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]).</span></span> <span data-ttu-id="fb39c-126">次のオプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="fb39c-126">Choose one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fb39c-127">**[テープ ドライブ]**</span><span class="sxs-lookup"><span data-stu-id="fb39c-127">**Tape drive**</span></span>|<span data-ttu-id="fb39c-128">サーバー インスタンスを実行しているコンピューターに物理的に接続されているテープ ドライブの一覧から、バックアップ先としてテープ ドライブを選択するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fb39c-128">Choose this option to select a tape drive as the backup destination from the list of tape drives that are physically connected to the computer that is running the server instance.</span></span><br /><br /> <span data-ttu-id="fb39c-129">注:リモート コンピューターのテープ バックアップ デバイスは、有効なバックアップ先ではありません。</span><span class="sxs-lookup"><span data-stu-id="fb39c-129">Note: Tape backup devices on remote computers are not valid backup destinations.</span></span>|  
|<span data-ttu-id="fb39c-130">**バックアップ デバイス**</span><span class="sxs-lookup"><span data-stu-id="fb39c-130">**Backup device**</span></span>|<span data-ttu-id="fb39c-131">既存の論理バックアップ デバイスを選択するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fb39c-131">Choose this option to select an existing logical backup device.</span></span> <span data-ttu-id="fb39c-132">これらの論理バックアップ デバイスは、サーバー インスタンスを実行しているコンピューターに物理的に接続されているテープ ドライブに対応しています。</span><span class="sxs-lookup"><span data-stu-id="fb39c-132">These logical backup devices correspond to tape drives that are physically connected to the computer that is running the server instance.</span></span><br /><br /> <span data-ttu-id="fb39c-133">注:テープバックアップ デバイスを作成する方法の詳細については、「[テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb39c-133">Note: For information about how to create a tape backup device, see [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb39c-134">参照</span><span class="sxs-lookup"><span data-stu-id="fb39c-134">See Also</span></span>  
 <span data-ttu-id="fb39c-135">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb39c-135">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="fb39c-136">メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb39c-136">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
