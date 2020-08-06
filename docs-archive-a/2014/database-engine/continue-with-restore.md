---
title: Restore | を続行するMicrosoft Docs
description: SQL Server で、[復元の続行] ダイアログボックスを使用して、次のバックアップセットを復元するかどうかを指定します。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.continuerestore.f1
ms.assetid: 987ac05f-57c0-49a9-9903-9889717aae4f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c7a438ac7b8696d2f57bdf93ff86030cf607e682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740314"
---
# <a name="continue-with-restore"></a><span data-ttu-id="aad45-103">[復元の続行]</span><span class="sxs-lookup"><span data-stu-id="aad45-103">Continue with Restore</span></span>
  <span data-ttu-id="aad45-104">**[復元の続行]** ダイアログ ボックスを使用すると、次のバックアップ セットを復元するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="aad45-104">Use the **Continue with Restore** dialog box to indicate whether you want to restore the next backup set.</span></span> <span data-ttu-id="aad45-105">テープを交換する場合など、復元操作を遅らせるには、続行する準備ができてから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aad45-105">To delay the restore operation, for example, to swap tapes, wait until you are ready to proceed before you click **OK**.</span></span>  
  
 <span data-ttu-id="aad45-106">**[いいえ]** をクリックすると、復元シーケンスが終了し、対象データベースは復元中の状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="aad45-106">Clicking **No** terminates the restore sequence, leaving the database in the restoring state.</span></span> <span data-ttu-id="aad45-107">後で復元を続行するには、必要に応じて、 **[データベースの復元]** タスクまたは **[トランザクション ログの復元]** タスクのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="aad45-107">To continue with the restore later, use either the **Restore Database** or **Restore Transaction Log** task, as appropriate.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aad45-108">Options</span><span class="sxs-lookup"><span data-stu-id="aad45-108">Options</span></span>  
 <span data-ttu-id="aad45-109">**[メディア セット]**</span><span class="sxs-lookup"><span data-stu-id="aad45-109">**Media set**</span></span>  
 <span data-ttu-id="aad45-110">次のメディア セット名 (利用可能な場合) を表示します。</span><span class="sxs-lookup"><span data-stu-id="aad45-110">Displays the next media set name (if available).</span></span>  
  
 <span data-ttu-id="aad45-111">**バックアップセット**</span><span class="sxs-lookup"><span data-stu-id="aad45-111">**Backup set**</span></span>  
 <span data-ttu-id="aad45-112">バックアップ セット名を表示します。</span><span class="sxs-lookup"><span data-stu-id="aad45-112">Displays the backup set name.</span></span>  
  
 <span data-ttu-id="aad45-113">**バックアップセットの説明**</span><span class="sxs-lookup"><span data-stu-id="aad45-113">**Backup set description**</span></span>  
 <span data-ttu-id="aad45-114">バックアップ セットの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="aad45-114">Displays the backup set description.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad45-115">参照</span><span class="sxs-lookup"><span data-stu-id="aad45-115">See Also</span></span>  
 <span data-ttu-id="aad45-116">[バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aad45-116">[View the Contents of a Backup Tape or File &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md) </span></span>  
 <span data-ttu-id="aad45-117">[論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aad45-117">[View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span></span>  
 <span data-ttu-id="aad45-118">[データベースバックアップを復元する &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="aad45-118">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md) </span></span>  
 [<span data-ttu-id="aad45-119">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="aad45-119">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
  
