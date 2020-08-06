---
title: インデックス DDL 操作に必要なディスク領域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- temporary disk space [SQL Server]
ms.assetid: 35930826-c870-44c1-a966-a6a4638f62ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4ac25fc1555d6b6cfd8ee97b50d261cf5788f587
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645070"
---
# <a name="disk-space-requirements-for-index-ddl-operations"></a><span data-ttu-id="08240-102">インデックス DDL 操作に必要なディスク領域</span><span class="sxs-lookup"><span data-stu-id="08240-102">Disk Space Requirements for Index DDL Operations</span></span>
  <span data-ttu-id="08240-103">ディスク領域は、インデックスを作成、再構築、または削除するときの重要な検討事項です。</span><span class="sxs-lookup"><span data-stu-id="08240-103">Disk space is an important consideration when you create, rebuild, or drop indexes.</span></span> <span data-ttu-id="08240-104">ディスク領域が不足すると、パフォーマンスが低下したり、インデックス操作が失敗したりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="08240-104">Inadequate disk space can degrade performance or even cause the index operation to fail.</span></span> <span data-ttu-id="08240-105">このトピックでは、インデックス DDL (データ定義言語) 操作に必要なディスク領域を判断するのに役立つ一般的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="08240-105">This topic provides general information that can help you determine the amount of disk space required for index data definition language (DDL) operations.</span></span>  
  
## <a name="index-operations-that-require-no-additional-disk-space"></a><span data-ttu-id="08240-106">追加のディスク領域を必要としないインデックス操作</span><span class="sxs-lookup"><span data-stu-id="08240-106">Index Operations That Require No Additional Disk Space</span></span>  
 <span data-ttu-id="08240-107">次のインデックス操作では、追加のディスク領域は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="08240-107">The following index operations require no additional disk space:</span></span>  
  
-   <span data-ttu-id="08240-108">ALTER INDEX REORGANIZE (ただし、ログ領域は必要です)</span><span class="sxs-lookup"><span data-stu-id="08240-108">ALTER INDEX REORGANIZE; however, log space is required.</span></span>  
  
-   <span data-ttu-id="08240-109">DROP INDEX (非クラスター化インデックスを削除している場合)</span><span class="sxs-lookup"><span data-stu-id="08240-109">DROP INDEX when you are dropping a nonclustered index.</span></span>  
  
-   <span data-ttu-id="08240-110">DROP INDEX (MOVE TO 句を指定せずにオフラインでクラスター化インデックスを削除していて、非クラスター化インデックスが存在しない場合)</span><span class="sxs-lookup"><span data-stu-id="08240-110">DROP INDEX when you are dropping a clustered index offline without specifying the MOVE TO clause and nonclustered indexes do not exist.</span></span>  
  
-   <span data-ttu-id="08240-111">CREATE TABLE (PRIMARY KEY 制約または UNIQUE 制約)</span><span class="sxs-lookup"><span data-stu-id="08240-111">CREATE TABLE (PRIMARY KEY or UNIQUE constraints)</span></span>  
  
## <a name="index-operations-that-require-additional-disk-space"></a><span data-ttu-id="08240-112">追加のディスク領域が必要なインデックス操作</span><span class="sxs-lookup"><span data-stu-id="08240-112">Index Operations That Require Additional Disk Space</span></span>  
 <span data-ttu-id="08240-113">他のすべてのインデックス DDL 操作では、操作中に使用する一時ディスク領域と、新しいインデックス構造を格納する永続的なディスク領域が追加で必要になります。</span><span class="sxs-lookup"><span data-stu-id="08240-113">All other index DDL operations require additional temporary disk space to use during the operation, and permanent disk space to store the new index structure or structures.</span></span>  
  
 <span data-ttu-id="08240-114">新しいインデックス構造を作成する場合、古い (作成元の) 構造と新しい (作成先の) 構造の両方を格納するディスク領域が、それぞれ適切なファイルおよびファイル グループで必要になります。</span><span class="sxs-lookup"><span data-stu-id="08240-114">When a new index structure is created, disk space for both the old (source) and new (target) structures is required in their appropriate files and filegroups.</span></span> <span data-ttu-id="08240-115">古い構造の割り当ては、インデックス作成トランザクションがコミットされるまで解除されません。</span><span class="sxs-lookup"><span data-stu-id="08240-115">The old structure is not deallocated until the index creation transaction commits.</span></span>  
  
 <span data-ttu-id="08240-116">次のインデックス DDL 操作では、新しいインデックス構造が作成され、追加のディスク領域が必要になります。</span><span class="sxs-lookup"><span data-stu-id="08240-116">The following index DDL operations create new index structures and require additional disk space:</span></span>  
  
-   <span data-ttu-id="08240-117">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="08240-117">CREATE INDEX</span></span>  
  
-   <span data-ttu-id="08240-118">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="08240-118">CREATE INDEX WITH DROP_EXISTING</span></span>  
  
-   <span data-ttu-id="08240-119">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="08240-119">ALTER INDEX REBUILD</span></span>  
  
-   <span data-ttu-id="08240-120">ALTER TABLE ADD CONSTRAINT (PRIMARY KEY または UNIQUE)</span><span class="sxs-lookup"><span data-stu-id="08240-120">ALTER TABLE ADD CONSTRAINT (PRIMARY KEY or UNIQUE)</span></span>  
  
-   <span data-ttu-id="08240-121">ALTER TABLE DROP CONSTRAINT (PRIMARY KEY または UNIQUE) (制約がクラスター化インデックスに基づいている場合)</span><span class="sxs-lookup"><span data-stu-id="08240-121">ALTER TABLE DROP CONSTRAINT (PRIMARY KEY or UNIQUE) when the constraint is based on a clustered index</span></span>  
  
-   <span data-ttu-id="08240-122">DROP INDEX MOVE TO (クラスター化インデックスのみ該当)</span><span class="sxs-lookup"><span data-stu-id="08240-122">DROP INDEX MOVE TO (Applies only to clustered indexes.)</span></span>  
  
## <a name="temporary-disk-space-for-sorting"></a><span data-ttu-id="08240-123">並べ替え用の一時ディスク領域</span><span class="sxs-lookup"><span data-stu-id="08240-123">Temporary Disk Space for Sorting</span></span>  
 <span data-ttu-id="08240-124">作成元の構造と作成先の構造を格納するために必要なディスク領域以外に、並べ替えに使用する一時ディスク領域も必要になります。ただし、クエリ オプティマイザーにより、並べ替えを必要としない実行プランが検出された場合は除きます。</span><span class="sxs-lookup"><span data-stu-id="08240-124">Besides the disk space required for the source and target structures, temporary disk space is required for sorting, unless the query optimizer finds an execution plan that does not require sorting.</span></span>  
  
 <span data-ttu-id="08240-125">並べ替えが必要な場合、一度に 1 つの新しいインデックスに対して並べ替えが実行されます。</span><span class="sxs-lookup"><span data-stu-id="08240-125">If sorting is required, sorting occurs one new index at a time.</span></span> <span data-ttu-id="08240-126">たとえば、1 つのステートメント内でクラスター化インデックスと関連する非クラスター化インデックスを再構築すると、インデックスは順番に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="08240-126">For example, when you rebuild a clustered index and associated nonclustered indexes within a single statement, the indexes are sorted one after the other.</span></span> <span data-ttu-id="08240-127">したがって、並べ替えに必要な追加の一時ディスク領域のサイズは、並べ替えるインデックスの中で最も大きなインデックスのサイズと同じサイズになります。</span><span class="sxs-lookup"><span data-stu-id="08240-127">Therefore, the additional temporary disk space that is required for sorting only has to be as large as the largest index in the operation.</span></span> <span data-ttu-id="08240-128">通常は、クラスター化インデックスのサイズが最も大きくなります。</span><span class="sxs-lookup"><span data-stu-id="08240-128">This is almost always the clustered index.</span></span>  
  
 <span data-ttu-id="08240-129">SORT_IN_TEMPDB オプションを ON に設定した場合は、最も大きいインデックスのサイズが **tempdb**のサイズを超えないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="08240-129">If the SORT_IN_TEMPDB option is set to ON, the largest index must fit into **tempdb**.</span></span> <span data-ttu-id="08240-130">このオプションを使用すると、インデックスの作成に使用する一時ディスク領域は増えますが、 **tempdb** がユーザー データベースとは異なるディスク セットにある場合、インデックスの作成に必要な時間を短縮できることがあります。</span><span class="sxs-lookup"><span data-stu-id="08240-130">Although this option increases the amount of temporary disk space that is used to create an index, it may reduce the time that is required to create an index when **tempdb** is on a set of disks different from the user database.</span></span>  
  
 <span data-ttu-id="08240-131">SORT_IN_TEMPDB を OFF (既定) に設定した場合、パーティション インデックスを含む各インデックスは、作成先のディスク領域で並べ替えられます。この場合、必要になるのは新しいインデックス構造のディスク領域のみです。</span><span class="sxs-lookup"><span data-stu-id="08240-131">If SORT_IN_TEMPDB is set to OFF (the default) each index, including partitioned indexes, is sorted in its destination disk space; and only the disk space for the new index structures is required.</span></span>  
  
 <span data-ttu-id="08240-132">ディスク領域の計算例については、「 [インデックスのディスク領域の例](index-disk-space-example.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08240-132">For an example of calculating disk space, see [Index Disk Space Example](index-disk-space-example.md).</span></span>  
  
## <a name="temporary-disk-space-for-online-index-operations"></a><span data-ttu-id="08240-133">オンライン インデックス操作用の一時ディスク領域</span><span class="sxs-lookup"><span data-stu-id="08240-133">Temporary Disk Space for Online Index Operations</span></span>  
 <span data-ttu-id="08240-134">インデックス操作をオンラインで実行する場合、追加の一時ディスク領域が必要になります。</span><span class="sxs-lookup"><span data-stu-id="08240-134">When you perform index operations online, additional temporary disk space is required.</span></span>  
  
 <span data-ttu-id="08240-135">クラスター化インデックスをオンラインで作成、再構築、または削除すると、古いブックマークを新しいブックマークにマップする非クラスター化インデックスが一時的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="08240-135">If a clustered index is created, rebuilt, or dropped online, a temporary nonclustered index is created to map old bookmarks to new bookmarks.</span></span> <span data-ttu-id="08240-136">SORT_IN_TEMPDB オプションを ON に設定した場合、この一時インデックスは **tempdb**に作成されます。</span><span class="sxs-lookup"><span data-stu-id="08240-136">If the SORT_IN_TEMPDB option is set to ON, this temporary index is created in **tempdb**.</span></span> <span data-ttu-id="08240-137">SORT_IN_TEMPDB を OFF に設定した場合は、新しいインデックスと同じファイル グループまたはパーティション構成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="08240-137">If SORT_IN_TEMPDB is set to OFF, the same filegroup or partition scheme as the target index is used.</span></span> <span data-ttu-id="08240-138">一時マッピング インデックスには、テーブルの行ごとに 1 つのレコードが格納されます。レコードの内容は、古いブックマーク列と新しいブックマーク列を組み合わせたもので、uniqueifier とレコード識別子が含まれます。両方のブックマークで使用されている列のコピーは 1 つしか含まれません。</span><span class="sxs-lookup"><span data-stu-id="08240-138">The temporary mapping index contains one record for each row in the table, and its contents is the union of the old and new bookmark columns, including uniqueifiers and record identifiers and including only a single copy of any column used in both bookmarks.</span></span> <span data-ttu-id="08240-139">オンラインでのインデックス操作の詳細については、「 [オンラインでのインデックス操作の実行](perform-index-operations-online.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08240-139">For more information about online index operations, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08240-140">SORT_IN_TEMPDB オプションは、DROP INDEX ステートメントには設定できません。</span><span class="sxs-lookup"><span data-stu-id="08240-140">The SORT_IN_TEMPDB option cannot be set for DROP INDEX statements.</span></span> <span data-ttu-id="08240-141">一時マッピング インデックスは、常に新しいインデックスと同じファイル グループまたはパーティション構成に作成されます。</span><span class="sxs-lookup"><span data-stu-id="08240-141">The temporary mapping index is always created in the same filegroup or partition scheme as the target index.</span></span>  
  
 <span data-ttu-id="08240-142">オンライン インデックス操作では、行のバージョン管理を使用して、他のトランザクションによる変更がインデックス操作に影響を与えないようにしています。</span><span class="sxs-lookup"><span data-stu-id="08240-142">Online index operations use row versioning to isolate the index operation from the effects of modifications made by other transactions.</span></span> <span data-ttu-id="08240-143">そのため、読み取った行の共有ロックを要求する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="08240-143">This avoids the need for requesting share locks on rows that have been read.</span></span> <span data-ttu-id="08240-144">オンライン インデックス操作と同時にユーザーの更新操作と削除操作を実行するには、 **tempdb**にバージョン レコード用の領域が必要になります。</span><span class="sxs-lookup"><span data-stu-id="08240-144">Concurrent user update and delete operations during online index operations require space for version records in **tempdb**.</span></span> <span data-ttu-id="08240-145">詳細については、「 [オンラインでのインデックス操作の実行](perform-index-operations-online.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08240-145">For more information, see [Perform Index Operations Online](perform-index-operations-online.md) .</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="08240-146">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="08240-146">Related Tasks</span></span>  
 [<span data-ttu-id="08240-147">インデックスのディスク領域の例</span><span class="sxs-lookup"><span data-stu-id="08240-147">Index Disk Space Example</span></span>](index-disk-space-example.md)  
  
 [<span data-ttu-id="08240-148">インデックス操作用のトランザクション ログのディスク領域</span><span class="sxs-lookup"><span data-stu-id="08240-148">Transaction Log Disk Space for Index Operations</span></span>](transaction-log-disk-space-for-index-operations.md)  
  
 [<span data-ttu-id="08240-149">テーブル サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="08240-149">Estimate the Size of a Table</span></span>](../databases/estimate-the-size-of-a-table.md)  
  
 [<span data-ttu-id="08240-150">クラスター化インデックスのサイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="08240-150">Estimate the Size of a Clustered Index</span></span>](../databases/estimate-the-size-of-a-clustered-index.md)  
  
 [<span data-ttu-id="08240-151">非クラスター化インデックスのサイズの算出</span><span class="sxs-lookup"><span data-stu-id="08240-151">Estimate the Size of a Nonclustered Index</span></span>](../databases/estimate-the-size-of-a-nonclustered-index.md)  
  
 [<span data-ttu-id="08240-152">ヒープ サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="08240-152">Estimate the Size of a Heap</span></span>](../databases/estimate-the-size-of-a-heap.md)  
  
## <a name="related-content"></a><span data-ttu-id="08240-153">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="08240-153">Related Content</span></span>  
 [<span data-ttu-id="08240-154">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08240-154">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
 [<span data-ttu-id="08240-155">ALTER INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08240-155">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
 [<span data-ttu-id="08240-156">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08240-156">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [<span data-ttu-id="08240-157">インデックスの FILL FACTOR の指定</span><span class="sxs-lookup"><span data-stu-id="08240-157">Specify Fill Factor for an Index</span></span>](specify-fill-factor-for-an-index.md)  
  
 [<span data-ttu-id="08240-158">インデックスの再編成と再構築</span><span class="sxs-lookup"><span data-stu-id="08240-158">Reorganize and Rebuild Indexes</span></span>](indexes.md)  
  
  
