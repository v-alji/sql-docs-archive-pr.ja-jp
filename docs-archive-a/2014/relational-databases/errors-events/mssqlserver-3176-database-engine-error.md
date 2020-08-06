---
title: MSSQLSERVER_3176 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 64e1a836995fe8738bb5c2ff0cb4de10d84d1f29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640983"
---
# <a name="mssqlserver_3176"></a><span data-ttu-id="c478a-102">MSSQLSERVER_3176</span><span class="sxs-lookup"><span data-stu-id="c478a-102">MSSQLSERVER_3176</span></span>
    
## <a name="details"></a><span data-ttu-id="c478a-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c478a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c478a-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c478a-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="c478a-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c478a-105">Event ID</span></span>|<span data-ttu-id="c478a-106">3176</span><span class="sxs-lookup"><span data-stu-id="c478a-106">3176</span></span>|  
|<span data-ttu-id="c478a-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c478a-107">Event Source</span></span>|<span data-ttu-id="c478a-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c478a-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c478a-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c478a-109">Component</span></span>|<span data-ttu-id="c478a-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c478a-110">SQLEngine</span></span>|  
|<span data-ttu-id="c478a-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c478a-111">Symbolic Name</span></span>|<span data-ttu-id="c478a-112">LDDB_FILE_CLAIM</span><span class="sxs-lookup"><span data-stu-id="c478a-112">LDDB_FILE_CLAIM</span></span>|  
|<span data-ttu-id="c478a-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c478a-113">Message Text</span></span>|<span data-ttu-id="c478a-114">ファイル '%ls' が '%ls'(%d) と '%ls'(%d) から要求されました。</span><span class="sxs-lookup"><span data-stu-id="c478a-114">File '%ls' is claimed by '%ls'(%d) and '%ls'(%d).</span></span> <span data-ttu-id="c478a-115">WITH MOVE 句を使用して、1 つ以上のファイルを再配置できます。</span><span class="sxs-lookup"><span data-stu-id="c478a-115">The WITH MOVE clause can be used to relocate one or more files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c478a-116">説明</span><span class="sxs-lookup"><span data-stu-id="c478a-116">Explanation</span></span>  
 <span data-ttu-id="c478a-117">ファイルを複数の目的で使用しようとしています。</span><span class="sxs-lookup"><span data-stu-id="c478a-117">Attempting to use a file for more than one purpose.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="c478a-118">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="c478a-118">Possible Causes</span></span>  
 <span data-ttu-id="c478a-119">既に別のデータベースで同じファイル名が使用されています。</span><span class="sxs-lookup"><span data-stu-id="c478a-119">Another database is already using the file name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c478a-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c478a-120">User Action</span></span>  
 <span data-ttu-id="c478a-121">データベース ファイルを別の場所に復元します。</span><span class="sxs-lookup"><span data-stu-id="c478a-121">Restore the database files to a different location.</span></span> <span data-ttu-id="c478a-122">これには、RESTORE ステートメントで WITH MOVE 句を使用して、各ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="c478a-122">In a RESTORE statement, use a WITH MOVE clause to move each file.</span></span> <span data-ttu-id="c478a-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、 **[データベースの復元オプション]** ダイアログ ボックスの **[次のデータベース ファイルに復元]** グリッドでファイルの場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="c478a-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], change the file locations in the **Restore the database files as** grid of the **Restore Database Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c478a-124">参照</span><span class="sxs-lookup"><span data-stu-id="c478a-124">See Also</span></span>  
 <span data-ttu-id="c478a-125">[データベースを新しい場所に復元する &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c478a-125">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="c478a-126">[新しい場所にファイルを復元する &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c478a-126">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 [<span data-ttu-id="c478a-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c478a-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
