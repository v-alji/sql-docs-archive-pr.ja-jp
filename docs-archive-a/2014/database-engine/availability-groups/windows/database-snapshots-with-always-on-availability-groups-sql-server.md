---
title: AlwaysOn 可用性グループを使用したデータベーススナップショット (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 7432da1c-ce2f-4cd9-af41-54c97744166b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1e4307653b5b8150d71019a373ee073d15123f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736793"
---
# <a name="database-snapshots-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="88dac-102">AlwaysOn 可用性グループを含むデータベース スナップショット (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="88dac-102">Database Snapshots with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="88dac-103">データベース スナップショットは、可用性グループ内のプライマリ データベースまたはセカンダリ データベースに作成できます。</span><span class="sxs-lookup"><span data-stu-id="88dac-103">You can create a database snapshot on an primary or secondary database in an availability group.</span></span> <span data-ttu-id="88dac-104">レプリカのロールは "プライマリ" または "セカンダリ" とし、"解決中" 状態でないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="88dac-104">The replica role must be either PRIMARY or SECONDARY, not in the RESOLVING state.</span></span>  
  
 <span data-ttu-id="88dac-105">データベース スナップショットの作成は、データベースの同期状態が "同期中" または "同期済み" であるときに実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="88dac-105">We recommend that the database synchronization state be SYNCHRONIZING or SYNCHRONIZED when you create a database snapshot.</span></span> <span data-ttu-id="88dac-106">ただし、データベースの同期状態が "同期されていません" であっても、データベース スナップショットを作成することはできます。</span><span class="sxs-lookup"><span data-stu-id="88dac-106">However, database snapshots can be created when the database synchronization state is NOT SYNCHRONIZING.</span></span>  
  
 <span data-ttu-id="88dac-107">セカンダリ レプリカがプライマリ レプリカから切断された (DISCONNECTED 状態) 場合、セカンダリ レプリカ上のデータベース スナップショットは引き続き実行できます。</span><span class="sxs-lookup"><span data-stu-id="88dac-107">A database snapshot on a secondary replica should continue to work if the replica is DISCONNECTED from the primary replica.</span></span>  
  
 <span data-ttu-id="88dac-108">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の一部の条件が原因で、ソース データベースとそのデータベース スナップショットが再起動され、一時的にユーザーの接続が切断されます。</span><span class="sxs-lookup"><span data-stu-id="88dac-108">Some [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] conditions cause both the source database and its database snapshots to be restarted, temporarily disconnecting users.</span></span> <span data-ttu-id="88dac-109">このような条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="88dac-109">These conditions are as follows:</span></span>  
  
-   <span data-ttu-id="88dac-110">同じサーバー インスタンスで現在のプライマリ レプリカがオフラインになり、オンラインに戻ったため、または可用性グループのフェールオーバーが発生したため、プライマリ レプリカでロールが変更される場合</span><span class="sxs-lookup"><span data-stu-id="88dac-110">The primary replica changes roles, whether because the current primary replica goes off line and comes back online on the same server instance or because the availability group fails over.</span></span>  
  
-   <span data-ttu-id="88dac-111">データベースがセカンダリ ロールに移行する場合</span><span class="sxs-lookup"><span data-stu-id="88dac-111">The database enters the secondary role.</span></span>  
  
 <span data-ttu-id="88dac-112">データベース スナップショットをホストする可用性レプリカがフェールオーバーされると、データベース スナップショットは、そのデータベース スナップショットが作成されたサーバー インスタンス上に残ります。</span><span class="sxs-lookup"><span data-stu-id="88dac-112">If the availability replica that hosts database snapshots is failed over, the database snapshots remain on the server instance where they were created.</span></span> <span data-ttu-id="88dac-113">ユーザーは、フェールオーバーの発生後、このスナップショットを引き続き使用できます。パフォーマンスを重視する環境の場合は、手動フェールオーバー モード用に構成するセカンダリ レプリカによってホストされるセカンダリ データベース上にのみデータベース スナップショットを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="88dac-113">Users can continue to use the snapshots after the failover.If performance is a concern in your environment, we recommend that you create database snapshots only on secondary databases that are hosted by a secondary replica that is configured for manual failover mode.</span></span>  <span data-ttu-id="88dac-114">このセカンダリ レプリカに可用性グループを手動でフェールオーバーすると、データベース スナップショットの新しいセットを別のセカンダリ レプリカ上に作成し、クライアントを新しいデータベース スナップショットに再出力して、プライマリ データベースからすべてのデータベース スナップショットを削除できます。</span><span class="sxs-lookup"><span data-stu-id="88dac-114">If you ever manually fail over the availability group to this secondary replica, you can create a new set of database snapshots on another secondary replica, redirect clients to the new database snapshots, and drop all of the database snapshots from the now primary databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88dac-115">参照</span><span class="sxs-lookup"><span data-stu-id="88dac-115">See Also</span></span>  
 <span data-ttu-id="88dac-116">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="88dac-116">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="88dac-117">Database Snapshots &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="88dac-117">Database Snapshots &#40;SQL Server&#41;</span></span>](../../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
