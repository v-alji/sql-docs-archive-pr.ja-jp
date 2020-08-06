---
title: データベース ミラーリングとデータベース スナップショット (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- snapshots [SQL Server database snapshots], database mirroring
- database snapshots [SQL Server], database mirroring
ms.assetid: 0bf1be90-7ce4-484c-aaa7-f8a782f57c5f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9df0b74270280bf2315c6a35a80d4b009b75a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634031"
---
# <a name="database-mirroring-and-database-snapshots-sql-server"></a><span data-ttu-id="facdc-102">データベース ミラーリングとデータベース スナップショット (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="facdc-102">Database Mirroring and Database Snapshots (SQL Server)</span></span>
  <span data-ttu-id="facdc-103">可用性を維持するために運用しているミラー データベースを利用して、レポート作成の負荷を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="facdc-103">You can take advantage of a mirror database that you are maintaining for availability purposes to offload reporting.</span></span> <span data-ttu-id="facdc-104">ミラー データベースをレポート作成に利用するには、ミラー データベースでデータベース スナップショットを作成し、クライアント接続要求を最新のスナップショットに出力します。</span><span class="sxs-lookup"><span data-stu-id="facdc-104">To use a mirror database for reporting, you can create a database snapshot on the mirror database and direct client connection requests to the most recent snapshot.</span></span> <span data-ttu-id="facdc-105">データベース スナップショットは、その作成時に存在していたソース データベースの静的な読み取り専用スナップショットであり、トランザクションに一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="facdc-105">A database snapshot is a static, read-only, transaction-consistent snapshot of its source database as it existed at the moment of the snapshot's creation.</span></span> <span data-ttu-id="facdc-106">ミラー データベースにデータベース スナップショットを作成するには、データベースは同期済みのミラーリング状態になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="facdc-106">To create a database snapshot on a mirror database, the database must be in the synchronized mirroring state.</span></span>  
  
 <span data-ttu-id="facdc-107">ミラー データベース自体とは異なり、データベース スナップショットはクライアントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="facdc-107">Unlike the mirror database itself, a database snapshot is accessible to clients.</span></span> <span data-ttu-id="facdc-108">ミラー サーバーがプリンシパル サーバーと通信している間は、レポート作成用クライアントに対してスナップショットに接続するように指示できます。</span><span class="sxs-lookup"><span data-stu-id="facdc-108">As long as the mirror server is communicating with the principal server, you can direct reporting clients to connect to a snapshot.</span></span> <span data-ttu-id="facdc-109">データベース スナップショットは静的なので、新しいデータは使用できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="facdc-109">Note that because a database snapshot is static, new data is not available.</span></span> <span data-ttu-id="facdc-110">ユーザーが比較的新しいデータを使用できるようにするには、定期的に新しいデータベース スナップショットを作成し、アプリケーションが着信クライアント接続を最新のスナップショットに出力することが必要です。</span><span class="sxs-lookup"><span data-stu-id="facdc-110">To make relatively recent data available to your users, you must create a new database snapshot periodically and have applications direct incoming client connections to the newest snapshot.</span></span>  
  
 <span data-ttu-id="facdc-111">新しいデータベース スナップショットはほとんど空ですが、時間が経過し、初めて更新されるデータベース ページが増えるにつれて拡張されます。</span><span class="sxs-lookup"><span data-stu-id="facdc-111">A new database snapshot is almost empty, but it grows over time as more and more database pages are updated for the first time.</span></span> <span data-ttu-id="facdc-112">データベース上の各スナップショットはこのように段階的に拡張されるため、各データベース スナップショットは、通常のデータベースと同じ量のリソースを消費します。</span><span class="sxs-lookup"><span data-stu-id="facdc-112">Because every snapshot on a database grows incrementally in this way, each database snapshot consumes as much resources as a normal database.</span></span> <span data-ttu-id="facdc-113">ミラー サーバーおよびプリンシパル サーバーの構成によって異なりますが、1 つのミラー データベースに過度に多くのデータベース スナップショットを配置すると、プリンシパル データベース上のパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="facdc-113">Depending on the configurations of the mirror server and principal server, having an excessive number of database snapshots on a mirror database might decrease performance on the principal database.</span></span> <span data-ttu-id="facdc-114">そのため、ミラー データベースには少数の比較的新しいスナップショットのみを保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="facdc-114">Therefore, we recommend that you keep only a few relatively recent snapshots on your mirror databases.</span></span> <span data-ttu-id="facdc-115">通常、置き換えるスナップショットを作成した後に、着信クエリを新しいスナップショットに再出力し、現在のクエリが完了した後に以前のスナップショットを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="facdc-115">Typically, after you create a replacement snapshot, you should redirect incoming queries to the new snapshot and drop the earlier snapshot after any current queries complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="facdc-116">データベース スナップショットの詳細については、「 [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="facdc-116">For more information about database snapshots, see [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).</span></span>  
  
 <span data-ttu-id="facdc-117">役割の交代が発生した場合、データベースとそのスナップショットは、一時的にユーザーの接続を切断して、再起動されます。</span><span class="sxs-lookup"><span data-stu-id="facdc-117">If role switching occurs, the database and its snapshots are restarted, temporarily disconnecting users.</span></span> <span data-ttu-id="facdc-118">その後、データベース スナップショットは、そのデータベース スナップショットが作成されたサーバー インスタンス上に残り、それが新しいプリンシパル データベースになります。</span><span class="sxs-lookup"><span data-stu-id="facdc-118">Afterwards, the database snapshots remain on the server instance where they were created, which has become the new principal database.</span></span> <span data-ttu-id="facdc-119">ユーザーは、フェールオーバーの発生後、このスナップショットを引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="facdc-119">Users can continue to use the snapshots after the failover.</span></span> <span data-ttu-id="facdc-120">ただし、これによって、新しいプリンシパル サーバーにさらに負荷がかかります。</span><span class="sxs-lookup"><span data-stu-id="facdc-120">However, this places an additional load on the new principal server.</span></span> <span data-ttu-id="facdc-121">パフォーマンスを重視する環境の場合は、新しいミラー データベースが使用できるようになったらその新しいミラー データベース上にスナップショットを作成し、クライアントを新しいスナップショットに再出力し、以前のミラー データベースからすべてのデータベース スナップショットを削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="facdc-121">If performance is a concern in your environment, we recommend that you create a snapshot on the new mirror database when it becomes available, redirect clients to the new snapshot, and drop all of the database snapshots from the former mirror database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="facdc-122">頻繁にスケールアウトされる、レポート ソリューション専用サーバーの場合は、レプリケーションを検討してください。</span><span class="sxs-lookup"><span data-stu-id="facdc-122">For a dedicated reporting solution that scales out well, consider replication.</span></span> <span data-ttu-id="facdc-123">詳細については、「 [SQL Server Replication](../install-windows/install-sql-server-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="facdc-123">For more information, see [SQL Server Replication](../install-windows/install-sql-server-replication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="facdc-124">例</span><span class="sxs-lookup"><span data-stu-id="facdc-124">Example</span></span>  
 <span data-ttu-id="facdc-125">この例では、ミラー データベースでスナップショットを作成します。</span><span class="sxs-lookup"><span data-stu-id="facdc-125">This example creates snapshots on a mirrored database.</span></span>  
  
 <span data-ttu-id="facdc-126">データベース ミラーリング セッションのデータベースが [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]であるとします。</span><span class="sxs-lookup"><span data-stu-id="facdc-126">Assume that the database of a database mirroring session is [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="facdc-127">この例では、 `AdventureWorks` ドライブにある `F` データベースのミラー コピーでデータベース スナップショットを 3 つ作成します。</span><span class="sxs-lookup"><span data-stu-id="facdc-127">This example creates three database snapshots on the mirror copy of the `AdventureWorks` database, which resides on the `F` drive.</span></span> <span data-ttu-id="facdc-128">これらのスナップショットには、おおよその作成時間を識別するために `AdventureWorks_0600`、 `AdventureWorks_1200`、および `AdventureWorks_1800` という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="facdc-128">The snapshots are named `AdventureWorks_0600`, `AdventureWorks_1200`, and `AdventureWorks_1800` to identify their approximate creation times.</span></span>  
  
1.  <span data-ttu-id="facdc-129">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]のミラーで最初のデータベース スナップショットを作成します。</span><span class="sxs-lookup"><span data-stu-id="facdc-129">Create the first database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_0600  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_0600.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
2.  <span data-ttu-id="facdc-130">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]のミラーで 2 番目のデータベース スナップショットを作成します。</span><span class="sxs-lookup"><span data-stu-id="facdc-130">Create the second database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="facdc-131">まだ `AdventureWorks_0600` を使用している場合は、このスナップショットを引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="facdc-131">Users who are still using `AdventureWorks_0600` can continue to use it.</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_1200  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1200.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     <span data-ttu-id="facdc-132">この時点で、新しいクライアント接続をプログラムによって最新のスナップショットに出力できます。</span><span class="sxs-lookup"><span data-stu-id="facdc-132">At this point, new client connections can be programmatically directed to the latest snapshot.</span></span>  
  
3.  <span data-ttu-id="facdc-133">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]のミラーで 3 番目のスナップショットを作成します。</span><span class="sxs-lookup"><span data-stu-id="facdc-133">Create the third snapshot on the mirror [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="facdc-134">まだ `AdventureWorks_0600` または `AdventureWorks_1200` を使用している場合は、このスナップショットを引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="facdc-134">Users who are still using `AdventureWorks_0600` or `AdventureWorks_1200` can continue to use them.</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_1800  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1800.SNP')  
        AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     <span data-ttu-id="facdc-135">この時点で、新しいクライアント接続をプログラムによって最新のスナップショットに出力できます。</span><span class="sxs-lookup"><span data-stu-id="facdc-135">At this point, new client connections can be programmatically directed to the latest snapshot.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="facdc-136">関連タスク</span><span class="sxs-lookup"><span data-stu-id="facdc-136">Related Tasks</span></span>  
  
-   [<span data-ttu-id="facdc-137">データベース スナップショットの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="facdc-137">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="facdc-138">データベース スナップショットの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="facdc-138">View a Database Snapshot &#40;SQL Server&#41;</span></span>](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="facdc-139">データベース スナップショットの削除 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="facdc-139">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  

  
## <a name="see-also"></a><span data-ttu-id="facdc-140">参照</span><span class="sxs-lookup"><span data-stu-id="facdc-140">See Also</span></span>  
 <span data-ttu-id="facdc-141">[Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="facdc-141">[Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md) </span></span>  
 [<span data-ttu-id="facdc-142">データベース ミラーリング セッションへのクライアントの接続 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="facdc-142">Connect Clients to a Database Mirroring Session &#40;SQL Server&#41;</span></span>](connect-clients-to-a-database-mirroring-session-sql-server.md)  
  
  
