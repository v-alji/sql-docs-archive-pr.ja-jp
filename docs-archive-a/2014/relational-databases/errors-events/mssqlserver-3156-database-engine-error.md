---
title: MSSQLSERVER_3156 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 25b5a037012a6d6b47b91e763a49cfb67b89f43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640987"
---
# <a name="mssqlserver_3156"></a><span data-ttu-id="71aa6-102">MSSQLSERVER_3156</span><span class="sxs-lookup"><span data-stu-id="71aa6-102">MSSQLSERVER_3156</span></span>
    
## <a name="details"></a><span data-ttu-id="71aa6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="71aa6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71aa6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="71aa6-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="71aa6-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="71aa6-105">Event ID</span></span>|<span data-ttu-id="71aa6-106">3156</span><span class="sxs-lookup"><span data-stu-id="71aa6-106">3156</span></span>|  
|<span data-ttu-id="71aa6-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="71aa6-107">Event Source</span></span>|<span data-ttu-id="71aa6-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="71aa6-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="71aa6-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="71aa6-109">Component</span></span>|<span data-ttu-id="71aa6-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="71aa6-110">SQLEngine</span></span>|  
|<span data-ttu-id="71aa6-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="71aa6-111">Symbolic Name</span></span>|<span data-ttu-id="71aa6-112">LDDB_CANT_WRITE</span><span class="sxs-lookup"><span data-stu-id="71aa6-112">LDDB_CANT_WRITE</span></span>|  
|<span data-ttu-id="71aa6-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="71aa6-113">Message Text</span></span>|<span data-ttu-id="71aa6-114">ファイル '%ls' を '%ls' に復元できません。</span><span class="sxs-lookup"><span data-stu-id="71aa6-114">File '%ls' cannot be restored to '%ls'.</span></span> <span data-ttu-id="71aa6-115">WITH MOVE を使用して、そのファイルにとって有効な場所を特定してください。</span><span class="sxs-lookup"><span data-stu-id="71aa6-115">Use WITH MOVE to identify a valid location for the file.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="71aa6-116">説明</span><span class="sxs-lookup"><span data-stu-id="71aa6-116">Explanation</span></span>  
 <span data-ttu-id="71aa6-117">この一般的なメッセージは、指定の場所に問題があり、ファイルを復元できなかった場合の論理ファイル名または物理ファイル名を示すものです。</span><span class="sxs-lookup"><span data-stu-id="71aa6-117">This general message identifies the logical or physical file names of files that could not be restored because of a problem with the specified location.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="71aa6-118">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="71aa6-118">Possible Causes</span></span>  
 <span data-ttu-id="71aa6-119">以下のような原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="71aa6-119">The possible causes include the following:</span></span>  
  
-   <span data-ttu-id="71aa6-120">指定の Windows ディレクトリへのアクセス権が必要。</span><span class="sxs-lookup"><span data-stu-id="71aa6-120">You might need access to the specified Windows directory.</span></span>  
  
-   <span data-ttu-id="71aa6-121">パスの入力ミス、または存在しないパスを指定した。</span><span class="sxs-lookup"><span data-stu-id="71aa6-121">You might have mistyped the path or specified a path that does not exist.</span></span>  
  
-   <span data-ttu-id="71aa6-122">ファイル名が別のファイルで使用されており、上書きできない。</span><span class="sxs-lookup"><span data-stu-id="71aa6-122">The file name might be being used by a file that cannot be overwritten.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="71aa6-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="71aa6-123">User Action</span></span>  
 <span data-ttu-id="71aa6-124">エラー ログで、他のメッセージに詳細がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="71aa6-124">Look at the error logs for other messages that provide more details.</span></span>  
  
 <span data-ttu-id="71aa6-125">アクセス権を付与するなどして指定場所の問題を修正するか、RESTORE ステートメントで WITH MOVE オプションを使用してファイルを再配置します。</span><span class="sxs-lookup"><span data-stu-id="71aa6-125">Correct the problem with the specified location, for example, by granting access, or use the WITH MOVE option in your RESTORE statement to relocate the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71aa6-126">参照</span><span class="sxs-lookup"><span data-stu-id="71aa6-126">See Also</span></span>  
 <span data-ttu-id="71aa6-127">[データベースを新しい場所に復元する &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="71aa6-127">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="71aa6-128">[新しい場所にファイルを復元する &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="71aa6-128">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 [<span data-ttu-id="71aa6-129">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="71aa6-129">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
