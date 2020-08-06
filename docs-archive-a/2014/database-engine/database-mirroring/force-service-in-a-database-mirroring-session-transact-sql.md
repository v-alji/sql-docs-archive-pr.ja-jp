---
title: データベース ミラーリング セッションでのサービスの強制 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b909f3602a78f3244ab3cf4479b8745956a7bd62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742569"
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="fba59-102">データベース ミラーリング セッションでのサービスの強制 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fba59-102">Force Service in a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="fba59-103">高パフォーマンス モードおよび自動フェールオーバーを伴わない高い安全性モードでは、ミラー サーバーが使用可能であるときにプリンシパル サーバーで障害が発生した場合、データベース所有者はサービスを強制的にミラー データベースにフェールオーバーして、データベースを直ちに使用可能な状態にできます (ただし、データが損失する場合があります)。</span><span class="sxs-lookup"><span data-stu-id="fba59-103">In high-performance mode and high-safety mode without automatic failover, if the principal server fails while the mirror server is available, the database owner can make the database available by forcing service to fail over (with possible data loss) to the mirror database.</span></span> <span data-ttu-id="fba59-104">この方法は、次のすべての条件に一致する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="fba59-104">This option is available only under all the following conditions:</span></span>  
  
-   <span data-ttu-id="fba59-105">プリンシパル サーバーが停止している。</span><span class="sxs-lookup"><span data-stu-id="fba59-105">The principal server is down.</span></span>  
  
-   <span data-ttu-id="fba59-106">WITNESS が OFF に設定されているか、またはミラーリング監視サーバーがミラー サーバーに接続されている。</span><span class="sxs-lookup"><span data-stu-id="fba59-106">WITNESS is set to OFF or is connected to the mirror server.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="fba59-107">サービスの強制は、厳密にはディザスター リカバリーの方法です。</span><span class="sxs-lookup"><span data-stu-id="fba59-107">Forced service is strictly a disaster recovery method.</span></span> <span data-ttu-id="fba59-108">サービスを強制すると、一部のデータが損失する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fba59-108">Forcing service may involve some data loss.</span></span> <span data-ttu-id="fba59-109">このため、サービスを強制するのは、データベースに対するサービスを直ちに復元するためにデータの損失を許容できる場合のみに限定します。</span><span class="sxs-lookup"><span data-stu-id="fba59-109">Therefore, force service only if you are willing to risk losing some data in order to restore service to the database immediately.</span></span> <span data-ttu-id="fba59-110">サービスの強制によって重要なデータを失うリスクがある場合は、ミラーリングを停止してデータベースを手動で再同期することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fba59-110">If forcing service risks losing significant data, we recommend that you stop mirroring and manually resynchronize the databases.</span></span> <span data-ttu-id="fba59-111">サービスの強制によるリスクの詳細については、「 [データベース ミラーリングの動作モード](database-mirroring-operating-modes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fba59-111">For more information about the risks of forcing service, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="fba59-112">サービスを強制すると、セッションが中断して新しい復旧分岐が始まります。</span><span class="sxs-lookup"><span data-stu-id="fba59-112">Forcing service suspends the session and starts a new recovery fork.</span></span> <span data-ttu-id="fba59-113">サービスの強制による効果は、ミラーリングを削除して以前のプリンシパル データベースを復旧する効果に似ています。</span><span class="sxs-lookup"><span data-stu-id="fba59-113">The effect of forcing service is similar to removing mirroring and recovering the former principal database.</span></span> <span data-ttu-id="fba59-114">ただし、サービスを強制した場合は、ミラーリング再開時のデータベースの再同期が容易になります (データが損失する可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="fba59-114">However, forcing service facilitates resynchronizing the databases (with possible data loss) when mirroring resumes.</span></span>  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a><span data-ttu-id="fba59-115">データベース ミラーリング セッションでサービスを強制するには</span><span class="sxs-lookup"><span data-stu-id="fba59-115">To force service in a database mirroring session</span></span>  
  
1.  <span data-ttu-id="fba59-116">ミラー サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="fba59-116">Connect to the mirror server.</span></span>  
  
2.  <span data-ttu-id="fba59-117">次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="fba59-117">Issue the following statement:</span></span>  
  
     <span data-ttu-id="fba59-118">ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS</span><span class="sxs-lookup"><span data-stu-id="fba59-118">ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS</span></span>  
  
     <span data-ttu-id="fba59-119">ここで、 *<database_name>* はミラー化されたデータベースです。</span><span class="sxs-lookup"><span data-stu-id="fba59-119">where *<database_name>* is the mirrored database.</span></span>  
  
     <span data-ttu-id="fba59-120">ミラー サーバーは、直ちにプリンシパル サーバーに切り替わり、ミラーリングが中断されます。</span><span class="sxs-lookup"><span data-stu-id="fba59-120">The mirror server immediately transitions to principal server, and mirroring is suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba59-121">参照</span><span class="sxs-lookup"><span data-stu-id="fba59-121">See Also</span></span>  
 <span data-ttu-id="fba59-122">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fba59-122">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="fba59-123">Database Mirroring Operating Modes</span><span class="sxs-lookup"><span data-stu-id="fba59-123">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
