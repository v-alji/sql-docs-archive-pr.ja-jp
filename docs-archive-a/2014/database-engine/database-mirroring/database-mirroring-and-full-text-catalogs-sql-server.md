---
title: データベース ミラーリングとフルテキスト カタログ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- full-text catalogs [SQL Server], database mirroring
- catalogs [SQL Server], database mirroring
ms.assetid: e34072ae-fe8a-462d-bb03-02fa0987f793
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 39929f4bed6edbd1e8ec5c1b72dbe8f7aefeec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634029"
---
# <a name="database-mirroring-and-full-text-catalogs-sql-server"></a><span data-ttu-id="61518-102">データベース ミラーリングとフルテキスト カタログ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="61518-102">Database Mirroring and Full-Text Catalogs (SQL Server)</span></span>
  <span data-ttu-id="61518-103">フルテキスト カタログが格納されたデータベースをミラー化するには、通常どおりにバックアップを使用してプリンシパル データベースの完全バックアップを作成した後、そのバックアップを復元してデータベースをミラー サーバーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="61518-103">To mirror a database that has a full-text catalog, use backup as usual to create a full database backup of the principal database, and then restore the backup to copy the database to the mirror server.</span></span> <span data-ttu-id="61518-104">詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="61518-104">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
## <a name="full-text-catalog-and-indexes-before-failover"></a><span data-ttu-id="61518-105">フェールオーバー前のフルテキスト カタログとフルテキスト インデックス</span><span class="sxs-lookup"><span data-stu-id="61518-105">Full-Text Catalog and Indexes Before Failover</span></span>  
 <span data-ttu-id="61518-106">新しく作成されたミラー データベースのフルテキスト カタログは、データベースがバックアップされた時点と同じものです。</span><span class="sxs-lookup"><span data-stu-id="61518-106">In a newly created mirror database, the full-text catalog is the same as when the database was backed up.</span></span> <span data-ttu-id="61518-107">データベース ミラーリングの開始後、DDL ステートメント (CREATE FULLTEXT CATALOG、ALTER FULLTEXT CATALOG、および DROP FULLTEXT CATALOG) によって加えられたカタログレベルの変更は、ミラー データベース上で再生するためにログ記録されミラー サーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="61518-107">After database mirroring starts, any catalog-level changes that were made by DDL statements (CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG) are logged and sent to the mirror server to be replayed on the mirror database.</span></span> <span data-ttu-id="61518-108">ただし、インデックスレベルの変更は、プリンシパル サーバーにログ記録されないため、ミラー データベース上では再現されません。</span><span class="sxs-lookup"><span data-stu-id="61518-108">However, index-level changes are not reproduced on the mirror database because it is not logged on to the principal server.</span></span> <span data-ttu-id="61518-109">このため、プリンシパル データベース上でフルテキスト カタログの内容が変更されると、ミラー データベース上のフルテキスト カタログの内容と同期されていない状態になります。</span><span class="sxs-lookup"><span data-stu-id="61518-109">Therefore, as the contents of the full-text catalog change on the principal database, the contents of the full-text catalog on the mirror database are unsynchronized.</span></span>  
  
## <a name="full-text-indexes-after-failover"></a><span data-ttu-id="61518-110">フェールオーバー後のフルテキスト インデックス</span><span class="sxs-lookup"><span data-stu-id="61518-110">Full-Text Indexes After Failover</span></span>  
 <span data-ttu-id="61518-111">フェールオーバー後、次のような状況では、新しいプリンシパル サーバー上でフルテキスト インデックスのフル クロールを実行することが必要になる場合や役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="61518-111">After a failover, a full crawl of a full-text index on the new principal server might be required or useful in the following situations:</span></span>  
  
-   <span data-ttu-id="61518-112">フルテキスト インデックスでの変更の追跡が無効になっている場合は、次のステートメントを使用し、そのインデックスでフル クロールを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61518-112">If change-tracking is turned OFF on a full text index, you must start a full crawl on that index by using the following statement:</span></span>  
  
     <span data-ttu-id="61518-113">ALTER FULLTEXT INDEX ON *table_name* START FULL POPULATION</span><span class="sxs-lookup"><span data-stu-id="61518-113">ALTER FULLTEXT INDEX ON *table_name* START FULL POPULATION</span></span>  
  
-   <span data-ttu-id="61518-114">変更の追跡を自動的に実行するようにフルテキスト インデックスが構成されている場合、そのフルテキスト インデックスは自動的に同期されます。</span><span class="sxs-lookup"><span data-stu-id="61518-114">If a full-text index is configured for automatic change tracking, the full-text index is automatically synchronized.</span></span> <span data-ttu-id="61518-115">ただし、同期によってフルテキスト操作のパフォーマンスは若干低下します。</span><span class="sxs-lookup"><span data-stu-id="61518-115">However, synchronization slows full-text performance somewhat.</span></span> <span data-ttu-id="61518-116">パフォーマンスが極端に低下する場合は、変更の追跡を無効にしてから、自動的に実行されるように再設定することにより、フル クロールを開始できます。</span><span class="sxs-lookup"><span data-stu-id="61518-116">If performance is too slow, you can cause a full crawl by setting change tracking off and then resetting it to automatic:</span></span>  
  
    -   <span data-ttu-id="61518-117">変更の追跡を無効にするには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="61518-117">To set change tracking off:</span></span>  
  
         <span data-ttu-id="61518-118">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="61518-118">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING OFF</span></span>  
  
    -   <span data-ttu-id="61518-119">変更の追跡が自動的に実行されるように設定するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="61518-119">To set on automatic change tracking to automatic:</span></span>  
  
         <span data-ttu-id="61518-120">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="61518-120">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING AUTO</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="61518-121">変更の自動追跡が有効かどうかを確認するには、 [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) 関数を使用して、テーブルの **TableFullTextBackgroundUpdateIndexOn** プロパティをクエリできます。</span><span class="sxs-lookup"><span data-stu-id="61518-121">To see whether auto change tracking is on, you can use the [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) function to query the **TableFullTextBackgroundUpdateIndexOn** property of the table.</span></span>  
  
 <span data-ttu-id="61518-122">詳細については、「 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61518-122">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="61518-123">フェールオーバー後にクロールを開始することは、復元後にクロールを開始することと同じです。</span><span class="sxs-lookup"><span data-stu-id="61518-123">Starting a crawl after failover works the same as starting a crawl after a restore.</span></span>  
  
## <a name="after-forcing-service"></a><span data-ttu-id="61518-124">サービスの強制後</span><span class="sxs-lookup"><span data-stu-id="61518-124">After Forcing Service</span></span>  
 <span data-ttu-id="61518-125">サービスをミラー サーバーに強制 (データ損失が伴う場合もあります) した後、フル クロールを開始します。</span><span class="sxs-lookup"><span data-stu-id="61518-125">After service is forced to the mirror server (with possible data loss), start a full crawl.</span></span> <span data-ttu-id="61518-126">フル クロールの開始方法は、フルテキスト インデックスの変更が追跡されるかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="61518-126">The method to use for starting a full crawl depends on whether the full-text index is change tracked.</span></span> <span data-ttu-id="61518-127">詳細については、このトピックの「フェールオーバー後のフルテキスト インデックス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61518-127">For more information, see "Full-Text Indexes After Failover," earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61518-128">参照</span><span class="sxs-lookup"><span data-stu-id="61518-128">See Also</span></span>  
 <span data-ttu-id="61518-129">[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="61518-129">[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="61518-130">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="61518-130">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="61518-131">[DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="61518-131">[DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="61518-132">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="61518-132">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="61518-133">フルテキスト カタログとフルテキスト インデックスのバックアップおよび復元</span><span class="sxs-lookup"><span data-stu-id="61518-133">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](../../relational-databases/indexes/indexes.md)  
  
  
