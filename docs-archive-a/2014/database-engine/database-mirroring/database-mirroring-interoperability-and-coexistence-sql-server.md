---
title: 'データベース ミラーリング: 相互運用性と共存 (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 057392842974c3342fc57d0ec113f8b1bb58b9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639651"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a><span data-ttu-id="d76cb-102">データベース ミラーリング: 相互運用性と共存 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d76cb-102">Database Mirroring: Interoperability and Coexistence (SQL Server)</span></span>
  <span data-ttu-id="d76cb-103">データベース ミラーリングは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の次の機能またはコンポーネントと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="d76cb-103">Database mirroring can be used with the following features or components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="d76cb-104">AlwaysOn フェールオーバー クラスター インスタンス (SQL Server フェールオーバー クラスタリング)</span><span class="sxs-lookup"><span data-stu-id="d76cb-104">AlwaysOn Failover Cluster Instances (SQL Server Failover Clustering)</span></span>](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [<span data-ttu-id="d76cb-105">変更データ キャプチャと変更の追跡</span><span class="sxs-lookup"><span data-stu-id="d76cb-105">Change data capture (and change tracking)</span></span>](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [<span data-ttu-id="d76cb-106">データベース スナップショット</span><span class="sxs-lookup"><span data-stu-id="d76cb-106">Database snapshots</span></span>](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [<span data-ttu-id="d76cb-107">フルテキスト カタログ</span><span class="sxs-lookup"><span data-stu-id="d76cb-107">Full-text catalogs</span></span>](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [<span data-ttu-id="d76cb-108">ログ配布</span><span class="sxs-lookup"><span data-stu-id="d76cb-108">Log shipping</span></span>](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="d76cb-109">レプリケーション</span><span class="sxs-lookup"><span data-stu-id="d76cb-109">Replication</span></span>](database-mirroring-and-replication-sql-server.md)  
  
 <span data-ttu-id="d76cb-110">データベース ミラーリングは、次の機能との相互運用はできません。</span><span class="sxs-lookup"><span data-stu-id="d76cb-110">Database mirroring does not interoperate with the following:</span></span>  
  
-   <span data-ttu-id="d76cb-111">複数データベースにまたがるトランザクション/分散トランザクション</span><span class="sxs-lookup"><span data-stu-id="d76cb-111">Cross-database transactions/distributed transactions</span></span>  
  
     <span data-ttu-id="d76cb-112">このようなトランザクションがサポートされない理由の詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d76cb-112">For information about why such transactions are not supported, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d76cb-113">参照</span><span class="sxs-lookup"><span data-stu-id="d76cb-113">See Also</span></span>  
 [<span data-ttu-id="d76cb-114">データベース ミラーリング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d76cb-114">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
