---
title: '[データベースの復元] ([ファイル] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.files.f1 in the code
- sql12.swb.restoredb.files.f1
ms.assetid: 714c36ea-a9f9-43a4-99f9-a6f73d1baf8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: edffd9454b51ea80a18311f735d29407f97f6eb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643423"
---
# <a name="restore-database-files-page"></a><span data-ttu-id="c5162-102">[データベースの復元]\([ファイル] ページ)</span><span class="sxs-lookup"><span data-stu-id="c5162-102">Restore Database (Files Page)</span></span>
  <span data-ttu-id="c5162-103">**[データベースの復元]** ダイアログ ボックスの **[ファイル]** ページを使用して、データベース内で復元するように選択した特定のファイルを管理します。</span><span class="sxs-lookup"><span data-stu-id="c5162-103">Use the **Files** page of the **Restore Database** dialog box to manage the specific files you have chosen to restore within the database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c5162-104">Options</span><span class="sxs-lookup"><span data-stu-id="c5162-104">Options</span></span>  
  
### <a name="restore-database-files-as"></a><span data-ttu-id="c5162-105">[次のデータベース ファイルに復元]</span><span class="sxs-lookup"><span data-stu-id="c5162-105">Restore database files as</span></span>  
 <span data-ttu-id="c5162-106">復元されたファイルに新しいファイル パスを割り当て、管理できます。</span><span class="sxs-lookup"><span data-stu-id="c5162-106">Use to assign and manage the new file path to the restored files.</span></span>  
  
 <span data-ttu-id="c5162-107">**[すべてのファイルをフォルダーに移動]**</span><span class="sxs-lookup"><span data-stu-id="c5162-107">**Relocate all files to folder**</span></span>  
 <span data-ttu-id="c5162-108">復元されたファイルを再配置します。</span><span class="sxs-lookup"><span data-stu-id="c5162-108">Relocates restored files.</span></span>  
  
|<span data-ttu-id="c5162-109">オプション</span><span class="sxs-lookup"><span data-stu-id="c5162-109">Option</span></span>|<span data-ttu-id="c5162-110">説明</span><span class="sxs-lookup"><span data-stu-id="c5162-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c5162-111">**データ ファイル フォルダー**</span><span class="sxs-lookup"><span data-stu-id="c5162-111">**Data file folder**</span></span>|<span data-ttu-id="c5162-112">復元されたデータ ファイルが移されるデータ ファイルのフォルダー名を入力または検索します。</span><span class="sxs-lookup"><span data-stu-id="c5162-112">Enter or search for the data file folder name that the restored data file or files should be relocated to.</span></span>|  
|<span data-ttu-id="c5162-113">**ログ ファイル フォルダー**</span><span class="sxs-lookup"><span data-stu-id="c5162-113">**Log file folder**</span></span>|<span data-ttu-id="c5162-114">復元されたログ ファイルが移されるログ ファイル フォルダーを入力または検索します。</span><span class="sxs-lookup"><span data-stu-id="c5162-114">Enter or search for the log file or files folder that the restored log file should be relocated to.</span></span>|  
  
 <span data-ttu-id="c5162-115">**[論理ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="c5162-115">**Logical File Name**</span></span>  
 <span data-ttu-id="c5162-116">復元するデータベース ファイルごとに 1 つの行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5162-116">Displays one row for each database file to be restored.</span></span>  
  
 <span data-ttu-id="c5162-117">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="c5162-117">**File Type**</span></span>  
 <span data-ttu-id="c5162-118">ファイルの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="c5162-118">Displays the file type.</span></span>  
  
 <span data-ttu-id="c5162-119">**[元のファイル名]**</span><span class="sxs-lookup"><span data-stu-id="c5162-119">**Original File Name**</span></span>  
 <span data-ttu-id="c5162-120">復元されたファイルの元のファイル パスを表示します。</span><span class="sxs-lookup"><span data-stu-id="c5162-120">Displays the original file path for the restored file.</span></span>  
  
 <span data-ttu-id="c5162-121">**[復元先]**</span><span class="sxs-lookup"><span data-stu-id="c5162-121">**Restore As**</span></span>  
 <span data-ttu-id="c5162-122">復元されたファイルが保存される際のファイル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5162-122">Lists the file names that the restored files are to be saved as.</span></span> <span data-ttu-id="c5162-123">適切なファイル名を入力または検索します。</span><span class="sxs-lookup"><span data-stu-id="c5162-123">Enter or search for the appropriate file name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5162-124">参照</span><span class="sxs-lookup"><span data-stu-id="c5162-124">See Also</span></span>  
 <span data-ttu-id="c5162-125">[[データベースの復元] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="c5162-125">[Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="c5162-126">[[データベースの復元] &#40;[オプション] ページ&#41;](restore-database-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="c5162-126">[Restore Database &#40;Options Page&#41;](restore-database-options-page.md) </span></span>  
 <span data-ttu-id="c5162-127">[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5162-127">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="c5162-128">[テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c5162-128">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="c5162-129">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c5162-129">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
