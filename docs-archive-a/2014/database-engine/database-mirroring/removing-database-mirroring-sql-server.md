---
title: データベース ミラーリングの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- stopping database mirroring [SQL Server]
- removing database mirroring [SQL Server]
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8044fcef9d9f9bfc1fb41c1faa17b76c827da5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716750"
---
# <a name="removing-database-mirroring-sql-server"></a><span data-ttu-id="d14db-102">データベース ミラーリングの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d14db-102">Removing Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="d14db-103">データベース所有者は、いずれのパートナーでもデータベース ミラーリング セッションをいつでも手動で停止できます。</span><span class="sxs-lookup"><span data-stu-id="d14db-103">The database owner can manually stop a database mirroring session at any time, at either partner.</span></span>  
  
## <a name="impact-of-removing-mirroring"></a><span data-ttu-id="d14db-104">ミラーリングの削除による影響</span><span class="sxs-lookup"><span data-stu-id="d14db-104">Impact of Removing Mirroring</span></span>  
 <span data-ttu-id="d14db-105">ミラーリングが削除されると、次のような動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="d14db-105">When mirroring is removed, the following occurs:</span></span>  
  
-   <span data-ttu-id="d14db-106">パートナー間および各パートナーとミラーリング監視サーバー間にリレーションシップがある場合、それらのリレーションシップが完全に解除されます。</span><span class="sxs-lookup"><span data-stu-id="d14db-106">The relationship between the partners and between each partner and the witness breaks permanently, if any relationship exists.</span></span>  
  
     <span data-ttu-id="d14db-107">セッションが停止した時点でパートナーどうしが通信している場合、そのリレーションシップは両方のコンピューターですぐに解除されます。</span><span class="sxs-lookup"><span data-stu-id="d14db-107">If the partners are communicating with each other when the session is stopped, their relationship is immediately broken on both computers.</span></span> <span data-ttu-id="d14db-108">パートナーどうしが通信していない場合、つまり停止時点でデータベースが DISCONNECTED 状態である場合は、ミラーリング停止処理を実行した側のパートナーではリレーションシップがすぐに解除されます。もう一方のパートナーは、再接続を試行したときに、データベース ミラーリング セッションが停止していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="d14db-108">If the partners are not communicating (the database is in a DISCONNECTED state at the time of stopping), the relationship is broken immediately on the partner from which mirroring is stopped; when the other partner tries to reconnect, it discovers that the database mirroring session has ended.</span></span>  
  
-   <span data-ttu-id="d14db-109">セッションの一時停止の場合と異なり、ミラーリング セッションについての情報は削除されます。</span><span class="sxs-lookup"><span data-stu-id="d14db-109">Information about the mirroring session is dropped, unlike when pausing a session.</span></span> <span data-ttu-id="d14db-110">ミラーリングは、プリンシパル データベースとミラー データベースの両方から削除されます。</span><span class="sxs-lookup"><span data-stu-id="d14db-110">Mirroring is removed on both the principal database and the mirror database.</span></span> <span data-ttu-id="d14db-111">**sys.databases** では、**mirroring_state** 列およびその他すべてのミラー化に関する列が NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d14db-111">In **sys.databases**, the **mirroring_state** column and all other mirroring columns are set to NULL.</span></span> <span data-ttu-id="d14db-112">詳細については、「[sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d14db-112">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
-   <span data-ttu-id="d14db-113">各パートナー サーバー インスタンスには、データベースの個別のコピーが保持されます。</span><span class="sxs-lookup"><span data-stu-id="d14db-113">Each partner server instance is left with a separate copy of the database.</span></span>  
  
-   <span data-ttu-id="d14db-114">ミラー データベースは復元中の状態になります ( **sys.databases** の **state**列を参照)。これは、ミラー データベースが RESTORE WITH NORECOVERY を使用して作成されているためです。</span><span class="sxs-lookup"><span data-stu-id="d14db-114">The mirror database is left in the RESTORING state (see the **state** column of **sys.databases**), because the mirror database was created by using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="d14db-115">この時点で、古いミラー データベースを削除するか、WITH RECOVERY を使用して復元できます。</span><span class="sxs-lookup"><span data-stu-id="d14db-115">At this point, you can drop the former mirror database or restore it using WITH RECOVERY.</span></span> <span data-ttu-id="d14db-116">データベースを復元すると、古いプリンシパル データベースから分岐が行われます。これは、復旧によって新しい復旧分岐が開始されるためです。</span><span class="sxs-lookup"><span data-stu-id="d14db-116">When you recover the database, it will have diverged from the former principal database because the recovery starts a new recovery fork.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d14db-117">セッション停止後もミラー化を続行するには、新しいデータベース ミラーリング セッションを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d14db-117">To continue mirroring after stopping a session, you must establish a new database mirroring session.</span></span> <span data-ttu-id="d14db-118">ミラー化の停止後にログ バックアップを作成する場合は、ミラー化を再開する前にミラー データベースにそのログ バックアップを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d14db-118">If you create a log backup after stopping mirroring, you must apply it to the mirror database before restarting mirroring.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d14db-119">関連タスク</span><span class="sxs-lookup"><span data-stu-id="d14db-119">Related Tasks</span></span>  
 <span data-ttu-id="d14db-120">**データベース ミラーリングを削除するには**</span><span class="sxs-lookup"><span data-stu-id="d14db-120">**To remove database mirroring**</span></span>  
  
-   [<span data-ttu-id="d14db-121">データベース ミラーリングを削除する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d14db-121">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
 <span data-ttu-id="d14db-122">**データベース ミラーリングを開始するには**</span><span class="sxs-lookup"><span data-stu-id="d14db-122">**To start database mirroring**</span></span>  
  
-   [<span data-ttu-id="d14db-123">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d14db-123">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="d14db-124">Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d14db-124">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="d14db-125">参照</span><span class="sxs-lookup"><span data-stu-id="d14db-125">See Also</span></span>  
 <span data-ttu-id="d14db-126">[ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="d14db-126">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="d14db-127">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d14db-127">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="d14db-128">[データベース ミラーリングの一時停止と再開 &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d14db-128">[Pausing and Resuming Database Mirroring &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="d14db-129">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d14db-129">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
