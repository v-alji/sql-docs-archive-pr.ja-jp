---
title: '[バックアップ デバイスの選択] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a848f9188eec0ebb09931bca460b0389b9570ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736420"
---
# <a name="select-backup-device"></a><span data-ttu-id="7958f-102">[バックアップ デバイスの選択]</span><span class="sxs-lookup"><span data-stu-id="7958f-102">Select Backup Device</span></span>
  <span data-ttu-id="7958f-103">**[バックアップ デバイスの選択]** ダイアログ ボックスを使用すると、復元操作で使用する論理バックアップ デバイスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7958f-103">Use the **Select Backup Device** dialog box to select a logical backup device for the restore operation.</span></span>  
  
 <span data-ttu-id="7958f-104">論理バックアップ デバイスは、オペレーティング システムによって提供される物理デバイス (テープ ドライブまたはディスク ドライブ) に対応するユーザー定義の論理デバイスです。</span><span class="sxs-lookup"><span data-stu-id="7958f-104">A logical backup device is a user-defined logical device that corresponds to a physical device, either a tape drive or a disk drive, that is provided by the operating system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7958f-105">バックアップで複数のバックアップ デバイスを使用する場合、すべてのバックアップ デバイスが 1 つの種類のデバイスに対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7958f-105">If a backup uses multiple backup devices, they all must correspond to a single type of device.</span></span>  
  
 <span data-ttu-id="7958f-106">**SQL Server Management Studio を使用してバックアップ デバイスの内容を表示するには**</span><span class="sxs-lookup"><span data-stu-id="7958f-106">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="7958f-107">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7958f-107">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="7958f-108">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7958f-108">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="7958f-109">Options</span><span class="sxs-lookup"><span data-stu-id="7958f-109">Options</span></span>  
 <span data-ttu-id="7958f-110">**バックアップ デバイス**</span><span class="sxs-lookup"><span data-stu-id="7958f-110">**Backup device**</span></span>  
 <span data-ttu-id="7958f-111">復元操作で使用する論理バックアップ デバイスの名前を、このリスト ボックスから選択します。</span><span class="sxs-lookup"><span data-stu-id="7958f-111">In the list box, select the name of a logical backup device from which you want to restore.</span></span>  
  
 <span data-ttu-id="7958f-112">バックアップデバイスのコンテンツの表示方法の詳細については、「 [論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7958f-112">For information about how to view the contents of a backup device, see [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7958f-113">解説</span><span class="sxs-lookup"><span data-stu-id="7958f-113">Remarks</span></span>  
 <span data-ttu-id="7958f-114">探していたバックアップを含む論理バックアップ デバイスが一覧に表示されない場合、バックアップが 1 つ以上のファイルまたはテープ ドライブに直接書き込まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7958f-114">If you do not see a logical backup device that contains the backup you are seeking on the list, the backup might have been written directly to one or more files or tape drives.</span></span> <span data-ttu-id="7958f-115">この場合、 **[バックアップ デバイスの選択]** ダイアログ ボックスを取り消し、 **[バックアップの指定]** ダイアログ ボックスの **[バックアップ メディア]** ボックスで **[ファイル]** または **[テープ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7958f-115">If this is the case, cancel the **Select Backup Device** dialog box; and in the **Specify Backup** dialog box, select **File** or **Tape** in the **Backup media** list box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7958f-116">参照</span><span class="sxs-lookup"><span data-stu-id="7958f-116">See Also</span></span>  
 [<span data-ttu-id="7958f-117">バックアップ デバイス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7958f-117">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
