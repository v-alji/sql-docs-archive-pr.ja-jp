---
title: データベース ミラーリング セッションを手動でフェールオーバーする方法 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c04ea4908ccbc4cfe4f6bb3606347dd444ef416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632652"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="a4672-102">データベース ミラーリング セッションを手動でフェールオーバーする方法 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a4672-102">Manually Fail Over a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="a4672-103">ミラー化されたデータベースが同期されている場合 (つまり、データベースが SYNCHRONIZED 状態である場合)、データベース所有者はミラー サーバーに対して手動フェールオーバーを開始できます。</span><span class="sxs-lookup"><span data-stu-id="a4672-103">When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server.</span></span> <span data-ttu-id="a4672-104">手動フェールオーバーは、プリンシパル サーバーのみから開始できます。</span><span class="sxs-lookup"><span data-stu-id="a4672-104">Manual failover can be initiated only from the principal server.</span></span>  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a><span data-ttu-id="a4672-105">データベース ミラーリング セッションを手動でフェールオーバーするには</span><span class="sxs-lookup"><span data-stu-id="a4672-105">To manually fail over a database mirroring session</span></span>  
  
1.  <span data-ttu-id="a4672-106">プリンシパル サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="a4672-106">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="a4672-107">次のように、データベース コンテキストを **master** データベースに設定します。</span><span class="sxs-lookup"><span data-stu-id="a4672-107">Set the database context to the **master** database:</span></span>  
  
     `USE master;`  
  
3.  <span data-ttu-id="a4672-108">プリンシパル サーバーで次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a4672-108">Issue the following statement on the principal server:</span></span>  
  
     <span data-ttu-id="a4672-109">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET PARTNER FAILOVER (*database_name* はミラー化されたデータベースです)。</span><span class="sxs-lookup"><span data-stu-id="a4672-109">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET PARTNER FAILOVER, where *database_name* is the mirrored database.</span></span>  
  
     <span data-ttu-id="a4672-110">これにより、プリンシパル ロールへのミラー サーバーの移行がすぐに開始されます。</span><span class="sxs-lookup"><span data-stu-id="a4672-110">This initiates an immediate transition of the mirror server to the principal role.</span></span>  
  
 <span data-ttu-id="a4672-111">前のプリンシパルでは、クライアントはデータベースとの接続が切断され、インフライト トランザクションがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="a4672-111">On the former principal, clients are disconnected from the database and in-flight transactions are rolled back.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4672-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーターを使用して準備したトランザクションのうち、フェールオーバーの発生時点でコミットされなかったトランザクションは、データベースのフェールオーバー後に中断したと見なされます。</span><span class="sxs-lookup"><span data-stu-id="a4672-112">Transactions that have been prepared by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator but are still not committed when a failover occurs are considered aborted after the database has failed over.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4672-113">参照</span><span class="sxs-lookup"><span data-stu-id="a4672-113">See Also</span></span>  
 <span data-ttu-id="a4672-114">[ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="a4672-114">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="a4672-115">[データベースミラーリングセッションを手動でフェールオーバーする &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a4672-115">[Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="a4672-116">データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4672-116">Role Switching During a Database Mirroring Session &#40;SQL Server&#41;</span></span>](role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
