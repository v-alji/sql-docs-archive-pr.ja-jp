---
title: MSSQLSERVER_1457 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c30ee6149c95d93bdaf1d2877f5fe1871a575ec1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643920"
---
# <a name="mssqlserver_1457"></a><span data-ttu-id="9f409-102">MSSQLSERVER_1457</span><span class="sxs-lookup"><span data-stu-id="9f409-102">MSSQLSERVER_1457</span></span>
    
## <a name="details"></a><span data-ttu-id="9f409-103">詳細</span><span class="sxs-lookup"><span data-stu-id="9f409-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f409-104">製品名</span><span class="sxs-lookup"><span data-stu-id="9f409-104">Product Name</span></span>|<span data-ttu-id="9f409-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9f409-105">SQL Server</span></span>|  
|<span data-ttu-id="9f409-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="9f409-106">Event ID</span></span>|<span data-ttu-id="9f409-107">1457</span><span class="sxs-lookup"><span data-stu-id="9f409-107">1457</span></span>|  
|<span data-ttu-id="9f409-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="9f409-108">Event Source</span></span>|<span data-ttu-id="9f409-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9f409-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9f409-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9f409-110">Component</span></span>|<span data-ttu-id="9f409-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9f409-111">SQLEngine</span></span>|  
|<span data-ttu-id="9f409-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="9f409-112">Symbolic Name</span></span>|<span data-ttu-id="9f409-113">DBM_PAGE_UNDO_PENDING</span><span class="sxs-lookup"><span data-stu-id="9f409-113">DBM_PAGE_UNDO_PENDING</span></span>|  
|<span data-ttu-id="9f409-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="9f409-114">Message Text</span></span>|<span data-ttu-id="9f409-115">ミラー データベース '%.\*ls' の同期が中断されました。データベースの一貫性は損なわれた状態のままです。</span><span class="sxs-lookup"><span data-stu-id="9f409-115">Synchronization of the mirror database, '%.\*ls', was interrupted, leaving the database in an inconsistent state.</span></span> <span data-ttu-id="9f409-116">ALTER DATABASE コマンドが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f409-116">The ALTER DATABASE command failed.</span></span> <span data-ttu-id="9f409-117">ミラー データベースがバックアップされ、オンラインであることを確認してから、ミラー サーバー インスタンスに再接続し、ミラー データベースで同期を終了できるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9f409-117">Ensure that the mirror database is back up and online, and then reconnect the mirror server instance and allow the mirror database to finish synchronizing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9f409-118">説明</span><span class="sxs-lookup"><span data-stu-id="9f409-118">Explanation</span></span>  
 <span data-ttu-id="9f409-119">このメッセージは、ALTER DATABASE *database_name* SET PARTNER OFF ステートメントが失敗したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="9f409-119">This messages indicates that the ALTER DATABASE *database_name* SET PARTNER OFF statement has failed.</span></span> <span data-ttu-id="9f409-120">データベース ミラーリングの削除に失敗し、削除を試みたことによってミラー データベースの同期が中断されました。</span><span class="sxs-lookup"><span data-stu-id="9f409-120">The failed attempt to remove database mirroring interrupted synchronization of the mirror database.</span></span> <span data-ttu-id="9f409-121">ミラー データベースは一貫性がない状態になっています。</span><span class="sxs-lookup"><span data-stu-id="9f409-121">The database is in an inconsistent state.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9f409-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="9f409-122">User Action</span></span>  
 <span data-ttu-id="9f409-123">このエラーを解決するには、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="9f409-123">To resolve this error, you can take either of the following actions:</span></span>  
  
-   <span data-ttu-id="9f409-124">ミラー サーバーとプリンシパル サーバーとの間の接続を再度確立し、ミラー データベースの同期を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9f409-124">Restore contact between the mirror server and the principal server to allow for the mirror database to synchronize.</span></span>  
  
-   <span data-ttu-id="9f409-125">ミラー データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="9f409-125">Drop the mirror database.</span></span>  
  
     <span data-ttu-id="9f409-126">ミラー データベースを削除した後、バックアップから新しいミラー データベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9f409-126">After you drop the mirror database, you can create a new mirror database from backups.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9f409-127">SET PARTNER OFF ステートメントが失敗した後でもミラーリングが有効な場合のみ、ミラー データベースを削除できます。</span><span class="sxs-lookup"><span data-stu-id="9f409-127">You can drop the mirror database when mirroring is still enabled only after a failed SET PARTNER OFF statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f409-128">参照</span><span class="sxs-lookup"><span data-stu-id="9f409-128">See Also</span></span>  
 <span data-ttu-id="9f409-129">[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9f409-129">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="9f409-130">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f409-130">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="9f409-131">[データベース ミラーリングの設定 &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9f409-131">[Setting Up Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="9f409-132">[データベース ミラーリングの削除 &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9f409-132">[Removing Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="9f409-133">ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9f409-133">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
  
