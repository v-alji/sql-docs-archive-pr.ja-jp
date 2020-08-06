---
title: MSSQLSERVER_3181 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f18509d9a18ba8be1f4e40c93bff5abfcae3d69c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640982"
---
# <a name="mssqlserver_3181"></a><span data-ttu-id="65016-102">MSSQLSERVER_3181</span><span class="sxs-lookup"><span data-stu-id="65016-102">MSSQLSERVER_3181</span></span>
    
## <a name="details"></a><span data-ttu-id="65016-103">詳細</span><span class="sxs-lookup"><span data-stu-id="65016-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65016-104">製品名</span><span class="sxs-lookup"><span data-stu-id="65016-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="65016-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="65016-105">Event ID</span></span>|<span data-ttu-id="65016-106">3181</span><span class="sxs-lookup"><span data-stu-id="65016-106">3181</span></span>|  
|<span data-ttu-id="65016-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="65016-107">Event Source</span></span>|<span data-ttu-id="65016-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="65016-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="65016-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="65016-109">Component</span></span>|<span data-ttu-id="65016-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="65016-110">SQLEngine</span></span>|  
|<span data-ttu-id="65016-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="65016-111">Symbolic Name</span></span>|<span data-ttu-id="65016-112">LDDB_STORAGE_VERIFY</span><span class="sxs-lookup"><span data-stu-id="65016-112">LDDB_STORAGE_VERIFY</span></span>|  
|<span data-ttu-id="65016-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="65016-113">Message Text</span></span>|<span data-ttu-id="65016-114">このバックアップの復元を試みるとストレージ領域に問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65016-114">Attempting to restore this backup may encounter storage space problems.</span></span> <span data-ttu-id="65016-115">詳細については、この後のメッセージを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65016-115">Subsequent messages will provide details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="65016-116">説明</span><span class="sxs-lookup"><span data-stu-id="65016-116">Explanation</span></span>  
 <span data-ttu-id="65016-117">RESTORE VERIFYONLY ステートメントでは、データベースの復元先ディスクの利用可能なストレージ領域がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="65016-117">The RESTORE VERIFYONLY statement checks the available storage space on the disk to which the database is to be restored.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="65016-118">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="65016-118">Possible Causes</span></span>  
 <span data-ttu-id="65016-119">使用可能なディスク領域が不十分なため、確認中のバックアップを復元できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65016-119">The available disk space may be insufficient to restore the backup being verified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="65016-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="65016-120">User Action</span></span>  
 <span data-ttu-id="65016-121">十分なディスク領域があるドライブにバックアップを復元するか、ディスク領域を増やします。</span><span class="sxs-lookup"><span data-stu-id="65016-121">Restore the backup to a location with sufficient disk space, or provide more space on the disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65016-122">参照</span><span class="sxs-lookup"><span data-stu-id="65016-122">See Also</span></span>  
 <span data-ttu-id="65016-123">[データベースを新しい場所に復元する &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="65016-123">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="65016-124">[新しい場所にファイルを復元する &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="65016-124">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="65016-125">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="65016-125">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="65016-126">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="65016-126">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
