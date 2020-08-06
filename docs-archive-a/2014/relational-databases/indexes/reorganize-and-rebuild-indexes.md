---
title: インデックスの再構成と再構築 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.indexproperties.fragmentation.f1
- sql12.swb.index.reorg.f1
- sql12.swb.index.rebuild.f1
helpviewer_keywords:
- large object defragmenting
- indexes [SQL Server], reorganizing
- index reorganization [SQL Server]
- reorganizing indexes
- defragmenting large object data types
- index fragmentation [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- indexes [SQL Server], rebuilding
- defragmenting indexes
- nonclustered indexes [SQL Server], defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
- LOB data [SQL Server], defragmenting
- clustered indexes, defragmenting
ms.assetid: a28c684a-c4e9-4b24-a7ae-e248808b31e9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c00f2128bb4c54064511ffff9e8929c9faf4d59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739966"
---
# <a name="reorganize-and-rebuild-indexes"></a><span data-ttu-id="16337-102">インデックスの再構成と再構築</span><span class="sxs-lookup"><span data-stu-id="16337-102">Reorganize and Rebuild Indexes</span></span>
  <span data-ttu-id="16337-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、断片化したインデックスを再構成または再構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="16337-103">This topic describes how to reorganize or rebuild a fragmented index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="16337-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] では、基になるデータに対して挿入、更新、または削除の各操作が行われるたびに、インデックスが自動的にメンテナンスされます。</span><span class="sxs-lookup"><span data-stu-id="16337-104">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatically maintains indexes whenever insert, update, or delete operations are made to the underlying data.</span></span> <span data-ttu-id="16337-105">このような変更が長期にわたると、インデックス内の情報がデータベース内に散在 (断片化) することになります。</span><span class="sxs-lookup"><span data-stu-id="16337-105">Over time these modifications can cause the information in the index to become scattered in the database (fragmented).</span></span> <span data-ttu-id="16337-106">インデックスに、キー値に基づく論理順序とデータ ファイル内の物理順序が一致しないページが存在すると、断片化が発生します。</span><span class="sxs-lookup"><span data-stu-id="16337-106">Fragmentation exists when indexes have pages in which the logical ordering, based on the key value, does not match the physical ordering inside the data file.</span></span> <span data-ttu-id="16337-107">インデックスが大量に断片化されると、クエリのパフォーマンスが低下し、アプリケーションの応答が遅くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="16337-107">Heavily fragmented indexes can degrade query performance and cause your application to respond slowly.</span></span>  
  
 <span data-ttu-id="16337-108">インデックスを再構成するか、インデックスを再構築することにより、インデックスの断片化を解消できます。</span><span class="sxs-lookup"><span data-stu-id="16337-108">You can remedy index fragmentation by reorganizing or rebuilding an index.</span></span> <span data-ttu-id="16337-109">パーティション構成に基づいて構築されたパーティション インデックスでは、完全なインデックスまたはインデックスの 1 つのパーティションで、再構成または再構築のいずれかを実行できます。</span><span class="sxs-lookup"><span data-stu-id="16337-109">For partitioned indexes built on a partition scheme, you can use either of these methods on a complete index or a single partition of an index.</span></span> <span data-ttu-id="16337-110">インデックスの再構築では、インデックスを削除し再作成します。</span><span class="sxs-lookup"><span data-stu-id="16337-110">Rebuilding an index drops and re-creates the index.</span></span> <span data-ttu-id="16337-111">この操作では、断片化をなくし、指定されているか既に存在する FILL FACTOR 設定に基づいてページを圧縮することによりディスク領域を取り戻した後、連続するページにインデックス行を再び並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="16337-111">This removes fragmentation, reclaims disk space by compacting the pages based on the specified or existing fill factor setting, and reorders the index rows in contiguous pages.</span></span> <span data-ttu-id="16337-112">ALL を指定した場合、テーブル上のすべてのインデックスが、1 回のトランザクションで削除され再構築されます。</span><span class="sxs-lookup"><span data-stu-id="16337-112">When ALL is specified, all indexes on the table are dropped and rebuilt in a single transaction.</span></span> <span data-ttu-id="16337-113">インデックスの再構成では、最小のシステム リソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="16337-113">Reorganizing an index uses minimal system resources.</span></span> <span data-ttu-id="16337-114">この操作では、リーフ レベル ページをリーフ ノードの論理順序 (左から右) に合わせて物理的に並べ替えることにより、テーブルやビュー上にあるクラスター化および非クラスター化インデックスのリーフ レベルをデフラグします。</span><span class="sxs-lookup"><span data-stu-id="16337-114">It defragments the leaf level of clustered and nonclustered indexes on tables and views by physically reordering the leaf-level pages to match the logical, left to right, order of the leaf nodes.</span></span> <span data-ttu-id="16337-115">再構成でも、インデックス ページは圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="16337-115">Reorganizing also compacts the index pages.</span></span> <span data-ttu-id="16337-116">圧縮は既存の FILL FACTOR 値に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="16337-116">Compaction is based on the existing fill factor value.</span></span>  
  
 <span data-ttu-id="16337-117">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="16337-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="16337-118">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="16337-118">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="16337-119">断片化の検出</span><span class="sxs-lookup"><span data-stu-id="16337-119">Detecting Fragmentation</span></span>](#Fragmentation)  
  
     [<span data-ttu-id="16337-120">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="16337-120">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="16337-121">Security</span><span class="sxs-lookup"><span data-stu-id="16337-121">Security</span></span>](#Security)  
  
-   <span data-ttu-id="16337-122">**インデックスの断片化を確認するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="16337-122">**To check the fragmentation of an index, using:**</span></span>  
  
     [<span data-ttu-id="16337-123">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="16337-123">SQL Server Management Studio</span></span>](#SSMSProcedureFrag)  
  
     [<span data-ttu-id="16337-124">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="16337-124">Transact-SQL</span></span>](#TsqlProcedureFrag)  
  
-   <span data-ttu-id="16337-125">**インデックスを再構成または再構築するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="16337-125">**To reorganize or rebuild an index, using:**</span></span>  
  
     [<span data-ttu-id="16337-126">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="16337-126">SQL Server Management Studio</span></span>](#SSMSProcedureReorg)  
  
     [<span data-ttu-id="16337-127">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="16337-127">Transact-SQL</span></span>](#TsqlProcedureReorg)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="16337-128">はじめに</span><span class="sxs-lookup"><span data-stu-id="16337-128">Before You Begin</span></span>  
  
###  <a name="detecting-fragmentation"></a><a name="Fragmentation"></a> <span data-ttu-id="16337-129">断片化の検出</span><span class="sxs-lookup"><span data-stu-id="16337-129">Detecting Fragmentation</span></span>  
 <span data-ttu-id="16337-130">断片化を解消する方法を決める最初の手順は、断片化の程度を判断するためにインデックスを分析することです。</span><span class="sxs-lookup"><span data-stu-id="16337-130">The first step in deciding which defragmentation method to use is to analyze the index to determine the degree of fragmentation.</span></span> <span data-ttu-id="16337-131">システム関数 [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)を使用して、特定のインデックス、テーブルやインデックス付きビュー上のすべてのインデックス、データベース内のすべてのインデックス、またはすべてのデータベース内のすべてのインデックスの断片化を検出できます。</span><span class="sxs-lookup"><span data-stu-id="16337-131">By using the system function [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql), you can detect fragmentation in a specific index, all indexes on a table or indexed view, all indexes in a database, or all indexes in all databases.</span></span> <span data-ttu-id="16337-132">パーティション インデックスの場合は、 **sys.dm_db_index_physical_stats** でもパーティションごとの断片化情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="16337-132">For partitioned indexes, **sys.dm_db_index_physical_stats** also provides fragmentation information for each partition.</span></span>  
  
 <span data-ttu-id="16337-133">**sys.dm_db_index_physical_stats** 関数から返される結果セットに含まれる列を次に示します。</span><span class="sxs-lookup"><span data-stu-id="16337-133">The result set returned by the **sys.dm_db_index_physical_stats** function includes the following columns.</span></span>  
  
|<span data-ttu-id="16337-134">列</span><span class="sxs-lookup"><span data-stu-id="16337-134">Column</span></span>|<span data-ttu-id="16337-135">説明</span><span class="sxs-lookup"><span data-stu-id="16337-135">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="16337-136">**avg_fragmentation_in_percent**</span><span class="sxs-lookup"><span data-stu-id="16337-136">**avg_fragmentation_in_percent**</span></span>|<span data-ttu-id="16337-137">論理的な断片化 (インデックス内で順序が乱れたページ) の割合。</span><span class="sxs-lookup"><span data-stu-id="16337-137">The percent of logical fragmentation (out-of-order pages in the index).</span></span>|  
|<span data-ttu-id="16337-138">**fragment_count**</span><span class="sxs-lookup"><span data-stu-id="16337-138">**fragment_count**</span></span>|<span data-ttu-id="16337-139">インデックス内の断片化 (物理的に連続したリーフ ページ) の数。</span><span class="sxs-lookup"><span data-stu-id="16337-139">The number of fragments (physically consecutive leaf pages) in the index.</span></span>|  
|<span data-ttu-id="16337-140">**avg_fragment_size_in_pages**</span><span class="sxs-lookup"><span data-stu-id="16337-140">**avg_fragment_size_in_pages**</span></span>|<span data-ttu-id="16337-141">インデックス内の 1 つの断片化内の平均ページ数。</span><span class="sxs-lookup"><span data-stu-id="16337-141">Average number of pages in one fragment in an index.</span></span>|  
  
 <span data-ttu-id="16337-142">断片化の程度がわかったら、次の表を使用して、断片化を解消するための最適な方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="16337-142">After the degree of fragmentation is known, use the following table to determine the best method to correct the fragmentation.</span></span>  
  
|<span data-ttu-id="16337-143">**avg_fragmentation_in_percent** 値</span><span class="sxs-lookup"><span data-stu-id="16337-143">**avg_fragmentation_in_percent** value</span></span>|<span data-ttu-id="16337-144">断片化解消ステートメント</span><span class="sxs-lookup"><span data-stu-id="16337-144">Corrective statement</span></span>|  
|-----------------------------------------------|--------------------------|  
|<span data-ttu-id="16337-145">> 5% および \< = 30%</span><span class="sxs-lookup"><span data-stu-id="16337-145">> 5% and \< = 30%</span></span>|<span data-ttu-id="16337-146">ALTER INDEX REORGANIZE</span><span class="sxs-lookup"><span data-stu-id="16337-146">ALTER INDEX REORGANIZE</span></span>|  
|<span data-ttu-id="16337-147">> 30%</span><span class="sxs-lookup"><span data-stu-id="16337-147">> 30%</span></span>|<span data-ttu-id="16337-148">ALTER INDEX REBUILD WITH (ONLINE = ON) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16337-148">ALTER INDEX REBUILD WITH (ONLINE = ON) <sup>1</sup></span></span>|

<span data-ttu-id="16337-149"><sup>1</sup> インデックスの再構築はオンラインでもオフラインでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="16337-149"><sup>1</sup> Rebuilding an index can be executed online or offline.</span></span> <span data-ttu-id="16337-150">インデックスの再構成は、常にオンラインで実行されます。</span><span class="sxs-lookup"><span data-stu-id="16337-150">Reorganizing an index is always executed online.</span></span> <span data-ttu-id="16337-151">再構成オプションと同様の可用性を実現するには、インデックスをオンラインで再構築してください。</span><span class="sxs-lookup"><span data-stu-id="16337-151">To achieve availability similar to the reorganize option, you should rebuild indexes online.</span></span>  
  
> [!TIP]
> <span data-ttu-id="16337-152">これらの値は、`ALTER INDEX REORGANIZE` と `ALTER INDEX REBUILD` の使い分けの大まかな目安となります。</span><span class="sxs-lookup"><span data-stu-id="16337-152">These values provide a rough guideline for determining the point at which you should switch between `ALTER INDEX REORGANIZE` and `ALTER INDEX REBUILD`.</span></span> <span data-ttu-id="16337-153">ただし、実際の値は状況によって変わります。</span><span class="sxs-lookup"><span data-stu-id="16337-153">However, the actual values may vary from case to case.</span></span> <span data-ttu-id="16337-154">それぞれの環境で実際に試して最適なしきい値を特定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="16337-154">It is important that you experiment to determine the best threshold for your environment.</span></span> <span data-ttu-id="16337-155">たとえば、特定のインデックスが主にスキャン操作に使用されている場合、断片化を解消すると、これらの操作のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="16337-155">For example, if a given index is used mainly for scan operations, removing fragmentation can improve performance of these operations.</span></span> <span data-ttu-id="16337-156">主にシーク操作に使用されるインデックスについては、パフォーマンス上の利点は小さくなります。</span><span class="sxs-lookup"><span data-stu-id="16337-156">The performance benefit is less noticeable for indexes that are used primarily for seek operations.</span></span> <span data-ttu-id="16337-157">同様に、ヒープ (クラスター化インデックスのないテーブル) 内の断片化の解消は、非クラスター化インデックスのスキャン操作では特に便利ですが、参照操作にはほとんど影響しません。</span><span class="sxs-lookup"><span data-stu-id="16337-157">Similarly, removing fragmentation in a heap (a table with no clustered index) is especially useful for nonclustered index scan operations, but has little effect in lookup operations.</span></span>

<span data-ttu-id="16337-158">断片化のレベルが非常に低い場合 (5% 未満) は、通常、これらのコマンドのいずれも使用しないでください。インデックスの再構成や再構築には、ほとんどの場合、そのようなわずかな断片化を解消するには見合わないコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="16337-158">Very low levels of fragmentation (less than 5 percent) should typically not be addressed by either of these commands, because the benefit from removing such a small amount of fragmentation is almost always vastly outweighed by the cost of reorganizing or rebuilding the index.</span></span> 

> [!NOTE]
> <span data-ttu-id="16337-159">小さなインデックスを再構築または再構成しても、多くの場合、断片化が解消することはありません。</span><span class="sxs-lookup"><span data-stu-id="16337-159">Rebuilding or reorganizing small indexes often does not reduce fragmentation.</span></span> <span data-ttu-id="16337-160">小さなインデックスのページは、混合エクステントに格納される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="16337-160">The pages of small indexes are sometimes stored on mixed extents.</span></span> <span data-ttu-id="16337-161">混合エクステントは最大 8 つのオブジェクトで共有されるため、小さなインデックスを再構成または再構築しても、その断片化は解消されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="16337-161">Mixed extents are shared by up to eight objects, so the fragmentation in a small index might not be reduced after reorganizing or rebuilding it.</span></span>

### <a name="index-defragmentation-considerations"></a><span data-ttu-id="16337-162">インデックスの最適化に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="16337-162">Index defragmentation considerations</span></span>
<span data-ttu-id="16337-163">特定の条件下では、非クラスター化インデックス レコードに含まれる物理識別子または論理識別子を変更する必要がある場合に、クラスター化インデックスを再構築すると、クラスター化キーを参照する非クラスター化インデックスが自動的に再構築されます。</span><span class="sxs-lookup"><span data-stu-id="16337-163">Under certain conditions, rebuilding a clustered index will automatically rebuild any nonclustered index that reference the clustering key, if the physical or logical identifiers contained in the nonclustered index records needs to change.</span></span>

<span data-ttu-id="16337-164">すべての非クラスター化インデックスを強制的にテーブル上に自動再構築するシナリオ:</span><span class="sxs-lookup"><span data-stu-id="16337-164">Scenarios that force all nonclustered indexes to be automatically rebuilt on a table:</span></span>

-  <span data-ttu-id="16337-165">テーブルに対するクラスター化インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="16337-165">Creating a clustered index on a table</span></span>
-  <span data-ttu-id="16337-166">テーブルがヒープとして格納される原因となる、クラスター化インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="16337-166">Removing a clustered index, causing the table to be stored as a heap</span></span>
-  <span data-ttu-id="16337-167">クラスター化キーの変更による列の挿入または除外</span><span class="sxs-lookup"><span data-stu-id="16337-167">Changing the clustering key to include or exclude columns</span></span>

<span data-ttu-id="16337-168">すべての非クラスター化インデックスをテーブル上で自動的に再構築する必要がないシナリオ:</span><span class="sxs-lookup"><span data-stu-id="16337-168">Scenarios that do not require all nonclustered indexes to be automatically rebuilt on a table:</span></span>

-  <span data-ttu-id="16337-169">一意のクラスター化インデックスの再構築</span><span class="sxs-lookup"><span data-stu-id="16337-169">Rebuilding a unique clustered index</span></span>
-  <span data-ttu-id="16337-170">一意でないクラスター化インデックスの再構築</span><span class="sxs-lookup"><span data-stu-id="16337-170">Rebuilding a non-unique clustered index</span></span>
-  <span data-ttu-id="16337-171">クラスター化インデックスへのパーティション構成の適用、クラスター化インデックスの別のファイルグループへの移動など、インデックス スキーマの変更</span><span class="sxs-lookup"><span data-stu-id="16337-171">Changing the index schema, such as applying a partitioning scheme to a clustered index or moving the clustered index to a different filegroup</span></span>
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="16337-172">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="16337-172">Limitations and Restrictions</span></span>  
  
<span data-ttu-id="16337-173">128 エクステントを超えるインデックスは、論理フェーズと物理フェーズの 2 つの独立したフェーズで再構築されます。</span><span class="sxs-lookup"><span data-stu-id="16337-173">Indexes with more than 128 extents are rebuilt in two separate phases: logical and physical.</span></span> <span data-ttu-id="16337-174">論理フェーズでは、インデックスによって使用されている既存のアロケーション ユニットが、割り当て解除に設定されます。その後、データ行がコピーされ、並べ替えられてから、再構築されたインデックスを格納するために作成された新しいアロケーション ユニットに移動されます。</span><span class="sxs-lookup"><span data-stu-id="16337-174">In the logical phase, the existing allocation units used by the index are marked for deallocation, the data rows are copied and sorted, then moved to new allocation units created to store the rebuilt index.</span></span> <span data-ttu-id="16337-175">物理フェーズでは、バックグラウンドで行われる短いトランザクションで、以前に割り当て解除に設定されたアロケーション ユニットが物理的に削除され、ロックの必要はあまり多くありません。</span><span class="sxs-lookup"><span data-stu-id="16337-175">In the physical phase, the allocation units previously marked for deallocation are physically dropped in short transactions that happen in the background, and do not require many locks.</span></span> <span data-ttu-id="16337-176">エクステントの詳細については、「[ページとエクステントのアーキテクチャ ガイド](https://docs.microsoft.com/sql/relational-databases/pages-and-extents-architecture-guide)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16337-176">For more information about extents, refer to the [Pages and Extents Architecture Guide](https://docs.microsoft.com/sql/relational-databases/pages-and-extents-architecture-guide).</span></span>

<span data-ttu-id="16337-177">この操作では、ファイル グループ内の他のファイルではなく、同じファイル上に一時的な作業ページを割り当てなければならないため、 `ALTER INDEX REORGANIZE` ステートメントには、使用可能な領域があるインデックスを含むデータ ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="16337-177">The `ALTER INDEX REORGANIZE` statement requires the data file containing the index to have space available, because the operation can only allocate temporary work pages on the same file, not another file within the filegroup.</span></span> <span data-ttu-id="16337-178">そのため、ファイル グループに空き容量があるとしても、エラー 1105 が発生することがあります。`Could not allocate space for object '###' in database '###' because the '###' filegroup is full. Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.`</span><span class="sxs-lookup"><span data-stu-id="16337-178">So although the filegroup might have free pages available, the user can still encounter error 1105: `Could not allocate space for object '###' in database '###' because the '###' filegroup is full. Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.`</span></span>

<span data-ttu-id="16337-179">固定されていないインデックスをパーティションが 1, 000 個以上あるテーブルに作成または再構築することは可能ですが、推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="16337-179">Creating and rebuilding non-aligned indexes on a table with more than 1,000 partitions is possible, but is not recommended.</span></span> <span data-ttu-id="16337-180">このような操作を行うと、操作中にパフォーマンスが低下したりメモリが過度に消費される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16337-180">Doing so may cause degraded performance or excessive memory consumption during these operations.</span></span>

<span data-ttu-id="16337-181">インデックスのあるファイル グループがオフラインであるか、または読み取り専用に設定されている場合、インデックスを再構成または再構築することはできません。</span><span class="sxs-lookup"><span data-stu-id="16337-181">An index cannot be reorganized or rebuilt if the filegroup in which it is located is offline or set to read-only.</span></span> <span data-ttu-id="16337-182">キーワード `ALL` を指定した場合で、1 つ以上のインデックスがオフラインまたは読み取り専用のファイル グループにある場合、ステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="16337-182">When the keyword `ALL` is specified and one or more indexes are in an offline or read-only filegroup, the statement fails.</span></span>
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="16337-183">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="16337-183">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="16337-184">Permissions</span><span class="sxs-lookup"><span data-stu-id="16337-184">Permissions</span></span>  
 <span data-ttu-id="16337-185">テーブルまたはビューに対する `ALTER` 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="16337-185">Requires `ALTER` permission on the table or view.</span></span> <span data-ttu-id="16337-186">実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="16337-186">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedureFrag"></a> <span data-ttu-id="16337-187">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="16337-187">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-check-the-fragmentation-of-an-index"></a><span data-ttu-id="16337-188">インデックスの断片化を確認するには</span><span class="sxs-lookup"><span data-stu-id="16337-188">To check the fragmentation of an index</span></span>  
  
1.  <span data-ttu-id="16337-189">オブジェクト エクスプローラーで、インデックスの断片化を確認するテーブルが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-189">In Object Explorer, Expand the database that contains the table on which you want to check an index's fragmentation.</span></span>  
  
2.  <span data-ttu-id="16337-190">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-190">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="16337-191">インデックスの断片化を確認するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-191">Expand the table on which you want to check an index's fragmentation.</span></span>  
  
4.  <span data-ttu-id="16337-192">**[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-192">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="16337-193">断片化を確認するインデックスを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="16337-193">Right-click the index of which you want to check the fragmentation and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="16337-194">**[ページの選択]** の **[断片化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="16337-194">Under **Select a page**, select **Fragmentation**.</span></span>  
  
     <span data-ttu-id="16337-195">**[断片化]** ページでは、次の情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="16337-195">The following information is available on the **Fragmentation** page:</span></span>  
  
     <span data-ttu-id="16337-196">**[ページのゆとり]**</span><span class="sxs-lookup"><span data-stu-id="16337-196">**Page fullness**</span></span>  
     <span data-ttu-id="16337-197">インデックス ページのゆとりの平均をパーセントで示します。</span><span class="sxs-lookup"><span data-stu-id="16337-197">Indicates average fullness of the index pages, as a percentage.</span></span> <span data-ttu-id="16337-198">100% は、インデックス ページが完全にいっぱいであることを示します。</span><span class="sxs-lookup"><span data-stu-id="16337-198">100% means the index pages are completely full.</span></span> <span data-ttu-id="16337-199">50% は、平均して各インデックス ページが半分埋まっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="16337-199">50% means that, on average, each index page is half full.</span></span>  
  
     <span data-ttu-id="16337-200">**[全体の断片化]**</span><span class="sxs-lookup"><span data-stu-id="16337-200">**Total fragmentation**</span></span>  
     <span data-ttu-id="16337-201">論理的な断片化の割合です。</span><span class="sxs-lookup"><span data-stu-id="16337-201">The logical fragmentation percentage.</span></span> <span data-ttu-id="16337-202">この値は、順番に格納されないインデックス内のページ数を示します。</span><span class="sxs-lookup"><span data-stu-id="16337-202">This indicates the number of pages in an index that are not stored in order.</span></span>  
  
     <span data-ttu-id="16337-203">**[行の平均サイズ]**</span><span class="sxs-lookup"><span data-stu-id="16337-203">**Average row size**</span></span>  
     <span data-ttu-id="16337-204">リーフ レベルの行の平均サイズです。</span><span class="sxs-lookup"><span data-stu-id="16337-204">The average size of a leaf level row.</span></span>  
  
     <span data-ttu-id="16337-205">**[奥行]**</span><span class="sxs-lookup"><span data-stu-id="16337-205">**Depth**</span></span>  
     <span data-ttu-id="16337-206">インデックス内のレベルの数 (リーフ レベルを含む) です。</span><span class="sxs-lookup"><span data-stu-id="16337-206">The number of levels in the index, including the leaf level.</span></span>  
  
     <span data-ttu-id="16337-207">**[転送されたレコード]**</span><span class="sxs-lookup"><span data-stu-id="16337-207">**Forwarded records**</span></span>  
     <span data-ttu-id="16337-208">別のデータの場所への転送ポインターを持つ、ヒープ内の転送されたレコード数です</span><span class="sxs-lookup"><span data-stu-id="16337-208">The number of records in a heap that have forward pointers to another data location.</span></span> <span data-ttu-id="16337-209">(この状態は、更新中に、新しい行を格納できる十分なスペースが元の場所にない場合に発生します)。</span><span class="sxs-lookup"><span data-stu-id="16337-209">(This state occurs during an update, when there is not enough room to store the new row in the original location.)</span></span>  
  
     <span data-ttu-id="16337-210">**[非実体行]**</span><span class="sxs-lookup"><span data-stu-id="16337-210">**Ghost rows**</span></span>  
     <span data-ttu-id="16337-211">削除のマークが付けられている行の中で、まだ削除されていない行の数です。</span><span class="sxs-lookup"><span data-stu-id="16337-211">The number of rows that are marked as deleted but not yet removed.</span></span> <span data-ttu-id="16337-212">これらの行は、サーバーが使用中でないときにクリーンアップ スレッドによって削除されます。</span><span class="sxs-lookup"><span data-stu-id="16337-212">These rows will be removed by a clean-up thread, when the server is not busy.</span></span> <span data-ttu-id="16337-213">この値には、スナップショット分離トランザクションが未完了であるために保持される行は含まれません。</span><span class="sxs-lookup"><span data-stu-id="16337-213">This value does not include rows that are being retained due to an outstanding snapshot isolation transaction.</span></span>  
  
     <span data-ttu-id="16337-214">**[インデックスの種類]**</span><span class="sxs-lookup"><span data-stu-id="16337-214">**Index type**</span></span>  
     <span data-ttu-id="16337-215">インデックスの種類です。</span><span class="sxs-lookup"><span data-stu-id="16337-215">The type of index.</span></span> <span data-ttu-id="16337-216">指定できる値は、 **[クラスター化]** 、 **[非クラスター化]** 、および **[プライマリ XML]** です。</span><span class="sxs-lookup"><span data-stu-id="16337-216">Possible values are **Clustered index**, **Nonclustered index**, and **Primary XML**.</span></span> <span data-ttu-id="16337-217">テーブルは、ヒープ (インデックスなし) としても格納できますが、その場合は、この [インデックスのプロパティ] ページは開きません。</span><span class="sxs-lookup"><span data-stu-id="16337-217">Tables can also be stored as a heap (without indexes), but then this Index Properties page cannot be opened.</span></span>  
  
     <span data-ttu-id="16337-218">**[リーフレベルの行]**</span><span class="sxs-lookup"><span data-stu-id="16337-218">**Leaf-level rows**</span></span>  
     <span data-ttu-id="16337-219">リール レベルの行の数です。</span><span class="sxs-lookup"><span data-stu-id="16337-219">The number of leaf level rows.</span></span>  
  
     <span data-ttu-id="16337-220">**[行の最大サイズ]**</span><span class="sxs-lookup"><span data-stu-id="16337-220">**Maximum row size**</span></span>  
     <span data-ttu-id="16337-221">リーフ レベルの最大行サイズです。</span><span class="sxs-lookup"><span data-stu-id="16337-221">The maximum leaf-level row size.</span></span>  
  
     <span data-ttu-id="16337-222">**[行の最小サイズ]**</span><span class="sxs-lookup"><span data-stu-id="16337-222">**Minimum row size**</span></span>  
     <span data-ttu-id="16337-223">リーフ レベルの最小行サイズです。</span><span class="sxs-lookup"><span data-stu-id="16337-223">The minimum leaf-level row size.</span></span>  
  
     <span data-ttu-id="16337-224">**ページ**</span><span class="sxs-lookup"><span data-stu-id="16337-224">**Pages**</span></span>  
     <span data-ttu-id="16337-225">データ ページ数の合計です。</span><span class="sxs-lookup"><span data-stu-id="16337-225">The total number of data pages.</span></span>  
  
     <span data-ttu-id="16337-226">**パーティション ID**</span><span class="sxs-lookup"><span data-stu-id="16337-226">**Partition ID**</span></span>  
     <span data-ttu-id="16337-227">インデックスを含む B ツリーのパーティション ID です。</span><span class="sxs-lookup"><span data-stu-id="16337-227">The partition ID of the b-tree containing the index.</span></span>  
  
     <span data-ttu-id="16337-228">**[バージョンの非実体行]**</span><span class="sxs-lookup"><span data-stu-id="16337-228">**Version ghost rows**</span></span>  
     <span data-ttu-id="16337-229">未処理のスナップショット分離トランザクションが原因で保持されているゴースト レコードの数。</span><span class="sxs-lookup"><span data-stu-id="16337-229">The number of ghost records that are being retained due to an outstanding snapshot isolation transaction.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedureFrag"></a> <span data-ttu-id="16337-230">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="16337-230">Using Transact-SQL</span></span>  
  
#### <a name="to-check-the-fragmentation-of-an-index"></a><span data-ttu-id="16337-231">インデックスの断片化を確認するには</span><span class="sxs-lookup"><span data-stu-id="16337-231">To check the fragmentation of an index</span></span>  
  
1.  <span data-ttu-id="16337-232">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="16337-232">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="16337-233">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-233">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="16337-234">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-234">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find the average fragmentation percentage of all indexes  
    -- in the HumanResources.Employee table.   
    SELECT a.index_id, name, avg_fragmentation_in_percent  
    FROM sys.dm_db_index_physical_stats (DB_ID(N'AdventureWorks2012'), OBJECT_ID(N'HumanResources.Employee'), NULL, NULL, NULL) AS a  
        JOIN sys.indexes AS b ON a.object_id = b.object_id AND a.index_id = b.index_id;   
    GO  
    ```  
  
     <span data-ttu-id="16337-235">上のステートメントでは、次のような結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="16337-235">The statement above might return a result set similar to the following.</span></span>  
  
    ```  
    index_id    name                                                  avg_fragmentation_in_percent  
    ----------- ----------------------------------------------------- ----------------------------  
    1           PK_Employee_BusinessEntityID                          0  
    2           IX_Employee_OrganizationalNode                        0  
    3           IX_Employee_OrganizationalLevel_OrganizationalNode    0  
    5           AK_Employee_LoginID                                   66.6666666666667  
    6           AK_Employee_NationalIDNumber                          50  
    7           AK_Employee_rowguid                                   0  
  
    (6 row(s) affected)  
    ```  
  
 <span data-ttu-id="16337-236">詳細については、「 [sys. dm_db_index_physical_stats &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16337-236">For more information, see  [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedureReorg"></a> <span data-ttu-id="16337-237">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="16337-237">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-reorganize-or-rebuild-an-index"></a><span data-ttu-id="16337-238">インデックスを再構成または再構築するには</span><span class="sxs-lookup"><span data-stu-id="16337-238">To reorganize or rebuild an index</span></span>  
  
1.  <span data-ttu-id="16337-239">オブジェクト エクスプローラーで、インデックスを再構成するテーブルが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-239">In Object Explorer, Expand the database that contains the table on which you want to reorganize an index.</span></span>  
  
2.  <span data-ttu-id="16337-240">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-240">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="16337-241">インデックスを再構成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-241">Expand the table on which you want to reorganize an index.</span></span>  
  
4.  <span data-ttu-id="16337-242">**[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-242">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="16337-243">再構成するインデックスを右クリックし、 **[再構成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="16337-243">Right-click the index you want to reorganize and select **Reorganize**.</span></span>  
  
6.  <span data-ttu-id="16337-244">**[インデックスの再構成]** ダイアログ ボックスで、 **[再構成するインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-244">In the **Reorganize Indexes** dialog box, verify that the correct index is in the **Indexes to be reorganized** grid and click **OK**.</span></span>  
  
7.  <span data-ttu-id="16337-245">**[ラージ オブジェクトの列データを圧縮する]** チェック ボックスをオンにして、ラージ オブジェクト (LOB) データを含むページもすべて圧縮することを指定します。</span><span class="sxs-lookup"><span data-stu-id="16337-245">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
8.  <span data-ttu-id="16337-246">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-246">Click **OK.**</span></span>  
  
#### <a name="to-reorganize-all-indexes-in-a-table"></a><span data-ttu-id="16337-247">テーブルのすべてのインデックスを再構成するには</span><span class="sxs-lookup"><span data-stu-id="16337-247">To reorganize all indexes in a table</span></span>  
  
1.  <span data-ttu-id="16337-248">オブジェクト エクスプローラーで、インデックスを再構成するテーブルが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-248">In Object Explorer, Expand the database that contains the table on which you want to reorganize the indexes.</span></span>  
  
2.  <span data-ttu-id="16337-249">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-249">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="16337-250">インデックスを再構成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-250">Expand the table on which you want to reorganize the indexes.</span></span>  
  
4.  <span data-ttu-id="16337-251">**[インデックス]** フォルダーを右クリックし、 **[すべて再構成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="16337-251">Right-click the **Indexes** folder and select **Reorganize All**.</span></span>  
  
5.  <span data-ttu-id="16337-252">**[インデックスの再構成]** ダイアログ ボックスで、 **[再構成するインデックス]** に目的のインデックスが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="16337-252">In the **Reorganize Indexes** dialog box, verify that the correct indexes are in the **Indexes to be reorganized**.</span></span> <span data-ttu-id="16337-253">**[再構成するインデックス]** グリッドからインデックスを削除するには、インデックスを選択し、Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="16337-253">To remove an index from the **Indexes to be reorganized** grid, select the index and then press the Delete key.</span></span>  
  
6.  <span data-ttu-id="16337-254">**[ラージ オブジェクトの列データを圧縮する]** チェック ボックスをオンにして、ラージ オブジェクト (LOB) データを含むページもすべて圧縮することを指定します。</span><span class="sxs-lookup"><span data-stu-id="16337-254">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
7.  <span data-ttu-id="16337-255">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-255">Click **OK.**</span></span>  
  
#### <a name="to-rebuild-an-index"></a><span data-ttu-id="16337-256">インデックスを再構築するには</span><span class="sxs-lookup"><span data-stu-id="16337-256">To rebuild an index</span></span>  
  
1.  <span data-ttu-id="16337-257">オブジェクト エクスプローラーで、インデックスを再構成するテーブルが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-257">In Object Explorer, Expand the database that contains the table on which you want to reorganize an index.</span></span>  
  
2.  <span data-ttu-id="16337-258">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-258">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="16337-259">インデックスを再構成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-259">Expand the table on which you want to reorganize an index.</span></span>  
  
4.  <span data-ttu-id="16337-260">**[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="16337-260">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="16337-261">再構成するインデックスを右クリックし、 **[再構成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="16337-261">Right-click the index you want to reorganize and select **Reorganize**.</span></span>  
  
6.  <span data-ttu-id="16337-262">**[インデックスの再構築]** ダイアログ ボックスで、 **[再構築するインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-262">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to be rebuilt** grid and click **OK**.</span></span>  
  
7.  <span data-ttu-id="16337-263">**[ラージ オブジェクトの列データを圧縮する]** チェック ボックスをオンにして、ラージ オブジェクト (LOB) データを含むページもすべて圧縮することを指定します。</span><span class="sxs-lookup"><span data-stu-id="16337-263">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
8.  <span data-ttu-id="16337-264">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-264">Click **OK.**</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedureReorg"></a> <span data-ttu-id="16337-265">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="16337-265">Using Transact-SQL</span></span>  
  
#### <a name="to-reorganize-a-defragmented-index"></a><span data-ttu-id="16337-266">デフラグされたインデックスを再構成するには</span><span class="sxs-lookup"><span data-stu-id="16337-266">To reorganize a defragmented index</span></span>  
  
1.  <span data-ttu-id="16337-267">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="16337-267">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="16337-268">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-268">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="16337-269">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-269">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize the IX_Employee_OrganizationalLevel_OrganizationalNode index on the HumanResources.Employee table.   
  
    ALTER INDEX IX_Employee_OrganizationalLevel_OrganizationalNode ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### <a name="to-reorganize-all-indexes-in-a-table"></a><span data-ttu-id="16337-270">テーブルのすべてのインデックスを再構成するには</span><span class="sxs-lookup"><span data-stu-id="16337-270">To reorganize all indexes in a table</span></span>  
  
1.  <span data-ttu-id="16337-271">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="16337-271">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="16337-272">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-272">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="16337-273">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-273">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### <a name="to-rebuild-a-defragmented-index"></a><span data-ttu-id="16337-274">デフラグされたインデックスを再構築するには</span><span class="sxs-lookup"><span data-stu-id="16337-274">To rebuild a defragmented index</span></span>  
  
1.  <span data-ttu-id="16337-275">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="16337-275">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="16337-276">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-276">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="16337-277">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-277">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="16337-278">次の例では、 `Employee` テーブルで単一のインデックスを再構築します。</span><span class="sxs-lookup"><span data-stu-id="16337-278">The example rebuilds a single index on the `Employee` table.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex1](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex1)]  
  
#### <a name="to-rebuild-all-indexes-in-a-table"></a><span data-ttu-id="16337-279">テーブルのすべてのインデックスを再構築するには</span><span class="sxs-lookup"><span data-stu-id="16337-279">To rebuild all indexes in a table</span></span>  
  
1.  <span data-ttu-id="16337-280">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="16337-280">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="16337-281">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16337-281">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="16337-282">次の例をコピーしてクエリ ウィンドウに貼り付けます。この例では、キーワード `ALL`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="16337-282">Copy and paste the following example into the query The example specifies the keyword `ALL`.</span></span> <span data-ttu-id="16337-283">この場合、テーブルに関連付けられているすべてのインデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="16337-283">This rebuilds all indexes associated with the table.</span></span> <span data-ttu-id="16337-284">3 つのオプションが指定されます。</span><span class="sxs-lookup"><span data-stu-id="16337-284">Three options are specified.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 <span data-ttu-id="16337-285">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16337-285">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16337-286">参照</span><span class="sxs-lookup"><span data-stu-id="16337-286">See Also</span></span>  
 [<span data-ttu-id="16337-287">SQL Server 2000 インデックスの最適化に関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="16337-287">Microsoft SQL Server 2000 Index Defragmentation Best Practices</span></span>](https://technet.microsoft.com/library/cc966523.aspx)  
  
  
