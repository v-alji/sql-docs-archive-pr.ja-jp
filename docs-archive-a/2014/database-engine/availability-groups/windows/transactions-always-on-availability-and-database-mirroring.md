---
title: データベースミラーリングまたは AlwaysOn 可用性グループ (SQL Server) では、複数データベースにまたがるトランザクションはサポートされていません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- cross-database transactions [SQL Server]
- transactions [database mirroring]
- Availability Groups [SQL Server], interoperability
- troubleshooting [SQL Server], cross-database transactions
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a0e23e073375c8f00317003635df8ec0b69883cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741282"
---
# <a name="cross-database-transactions-not-supported-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a><span data-ttu-id="3d6fd-102">データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3d6fd-102">Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="3d6fd-103">複数のデータベースにまたがるトランザクションおよび分散トランザクションは、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]やデータベース ミラーリングではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-103">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] or by database mirroring.</span></span> <span data-ttu-id="3d6fd-104">これは、次の理由により、トランザクションの原子性と整合性を保証できないためです。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-104">This is because transaction atomicity/integrity cannot be guaranteed for the following reasons:</span></span>  
  
-   <span data-ttu-id="3d6fd-105">複数データベースにまたがるトランザクション: それぞれのデータベースが別々にコミットします。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-105">For cross-database transactions: Each database commits independently.</span></span> <span data-ttu-id="3d6fd-106">そのため、複数のデータベースが 1 つの可用性グループに属している場合でも、一方のデータベースがトランザクションをコミットした後、もう一方のデータベースがコミットする前に、フェールオーバーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-106">Therefore, even for databases in a single availability group, a failover could occur after one database commits a transaction but before the other database does.</span></span> <span data-ttu-id="3d6fd-107">データベース ミラーリングの場合、この問題はさらに複雑です。フェールオーバーの後、ミラー化されたデータベースは、もう一方のデータベースとは異なるサーバー インスタンスに存在することが多いためです。両方のデータベースが同じ 2 つのパートナー間でミラーリングされていても、両方のデータベースが同時にフェールオーバーされる保証はありません。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-107">For database mirroring this issue is compounded because after a failover, the mirrored database is typically on a different server instance from the other database, and  even if both databases are mirrored between the same two partners, there is no guarantee that both databases will fail over at the same time.</span></span>  
  
-   <span data-ttu-id="3d6fd-108">分散トランザクションの場合: フェールオーバー後、新しいプリンシパル サーバー/プライマリ レプリカは、以前のプリンシパル サーバー/プライマリ レプリカの分散トランザクション コーディネーターに接続できません。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-108">For distributed transactions: After a failover, the new principal server/primary replica is unable to connect to the distributed transaction coordinator on the previous principal server/primary replica.</span></span> <span data-ttu-id="3d6fd-109">このため、新しいプリンシパル サーバー/プライマリ レプリカはトランザクションの状態を取得できません。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-109">Therefore, the new principal server/primary replica cannot obtain the transaction status.</span></span>  
  
 <span data-ttu-id="3d6fd-110">次に示すデータベース ミラーリングの例では、論理的な不一致が発生するしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-110">The following database mirroring example illustrates how a logical inconsistency could occur.</span></span> <span data-ttu-id="3d6fd-111">この例では、アプリケーションは複数データベースにまたがるトランザクションを使用して 2 行のデータを挿入します。一方の行は、ミラー化されたデータベース A 内のテーブルに挿入され、もう一方の行は、別のデータベース B 内のテーブルに挿入されます。データベース A は、自動フェールオーバーを伴う高い安全性モードでミラー化されています。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-111">In this example, an application uses a cross-database transaction to insert two rows of data: one row is inserted into a table in a mirrored database, A, and the other row is inserted into a table in another database, B. Database A is being mirrored in high-safety mode with automatic failover.</span></span> <span data-ttu-id="3d6fd-112">トランザクションがコミットされている間、データベース A は使用できなくなり、ミラーリング セッションはデータベース A のミラーに自動的にフェールオーバーされます。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-112">While the transaction is being committed, database A becomes unavailable, and the mirroring session automatically fails over to the mirror of database A.</span></span>  
  
 <span data-ttu-id="3d6fd-113">フェールオーバー後、複数データベースにまたがるトランザクションは、データベース B では正常にコミットされますが、フェールオーバーされたデータベースではコミットされない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-113">After the failover, the cross-database transaction might be successfully committed on database B but not on the failed-over database.</span></span> <span data-ttu-id="3d6fd-114">これは、障害発生前に、複数データベースにまたがるトランザクションのログがデータベース A の元のプリンシパル サーバーからミラー サーバーに送信されなかった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-114">This would occur if the original principal server for database A had not sent the log for the cross-database transaction to the mirror server before the failure.</span></span> <span data-ttu-id="3d6fd-115">フェールオーバー後、そのトランザクションは新しいプリンシパル サーバーに存在しなくなります。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-115">After the failover, that transaction would not exist on the new principal server.</span></span> <span data-ttu-id="3d6fd-116">データベース B に挿入されたデータはそのまま保たれますが、データベース A に挿入されたデータは失われているため、データベース A と B は一致しなくなります。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-116">Databases A and B would become inconsistent, because the data inserted in database B remains intact, but the data inserted in database A has been lost.</span></span>  
  
 <span data-ttu-id="3d6fd-117">同様の状況は、MS DTC トランザクションを使用する際に発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-117">A similar scenario can occur while using a MS DTC transaction.</span></span> <span data-ttu-id="3d6fd-118">たとえば、フェールオーバー後、新しいプリンシパルが MS DTC にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-118">For example, after failover, the new principal contacts MS DTC.</span></span> <span data-ttu-id="3d6fd-119">ただし、MS DTC は、新しいプリンシパル サーバーを認識せず、"コミットの準備が整った" トランザクションを終了します。これらのトランザクションは、他のデータベースでコミットされていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-119">But MS DTC has no knowledge of the new principal server, and it terminates any transactions that are "preparing to commit," which are considered committed in other databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3d6fd-120">DTC と共にデータベース ミラーリングまたは可用性グループを使用しても、サポートされていない SQL Server がインストールされる結果にはなりません。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-120">Using Database Mirroring or Availability Groups together with DTC does not result in an unsupported SQL Server installation.</span></span> <span data-ttu-id="3d6fd-121">ただし、データベースがデータベース ミラーリング セッションの一部、または可用性グループの一部であり、そのデータベース内で DTC を使用している場合は、Microsoft による調査の対象になるサポート関連の問題は、データベース ミラーリングまたは可用性グループを DTC と組み合わせて使用していない状況のみを想定したものになります。</span><span class="sxs-lookup"><span data-stu-id="3d6fd-121">If, however, a database is part of a Database Mirroring session or an Availability Group and DTC is also used in the database, support issues will be investigated by Microsoft only if unrelated to the combined use of Database Mirroring or Availability Groups with DTC.</span></span>  
  
  
