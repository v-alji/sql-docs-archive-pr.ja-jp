---
title: 列ストアインデックスの説明 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: 80a29b8e8cc5b53c09369156a5cf5f717e9447a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740961"
---
# <a name="columnstore-indexes-described"></a><span data-ttu-id="d5fb1-102">Columnstore Indexes Described</span><span class="sxs-lookup"><span data-stu-id="d5fb1-102">Columnstore Indexes Described</span></span>
  <span data-ttu-id="d5fb1-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]*インメモリ列ストアインデックス*は、列ベースのデータストレージと列ベースのクエリ処理を使用して、データを格納および管理します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *in-memory columnstore index* stores and manages data by using column-based data storage and column-based query processing.</span></span> <span data-ttu-id="d5fb1-104">列ストア インデックスは、主に一括読み込みと読み取り専用のクエリを実行するデータ ウェアハウスのワークロードで適切に動作します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-104">Columnstore indexes work well for data warehousing workloads that primarily perform bulk loads and read-only queries.</span></span> <span data-ttu-id="d5fb1-105">従来の行指向ストレージの最大 **10 倍のクエリ パフォーマンス** と、非圧縮データ サイズの最大 **7 倍のデータ圧縮** を達成するために列ストア インデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-105">Use the columnstore index to achieve up to **10x query performance** gains over traditional row-oriented storage, and up to **7x data compression** over the uncompressed data size.</span></span>

> [!NOTE]
>  <span data-ttu-id="d5fb1-106">大規模なデータ ウェアハウス ファクト テーブルを格納するために、クラスター化列ストア インデックスが標準とされており、ほとんどのデータ ウェアハウス シナリオで使用されることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-106">We view the clustered columnstore index as the standard for storing large data warehousing fact tables, and expect it will be used in most data warehousing scenarios.</span></span> <span data-ttu-id="d5fb1-107">クラスター化列ストア インデックスは更新可能であるため、ワークロードで多数の挿入、更新、および削除操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-107">Since the clustered columnstore index is updateable, your workload can perform a large number of insert, update, and delete operations.</span></span>

## <a name="contents"></a><span data-ttu-id="d5fb1-108">内容</span><span class="sxs-lookup"><span data-stu-id="d5fb1-108">Contents</span></span>

-   [<span data-ttu-id="d5fb1-109">基本操作</span><span class="sxs-lookup"><span data-stu-id="d5fb1-109">Basics</span></span>](#basics)

-   [<span data-ttu-id="d5fb1-110">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="d5fb1-110">Loading Data</span></span>](#dataload)

-   [<span data-ttu-id="d5fb1-111">パフォーマンスに関するヒント</span><span class="sxs-lookup"><span data-stu-id="d5fb1-111">Performance Tips</span></span>](#performance)

-   [<span data-ttu-id="d5fb1-112">関連タスクおよびトピック</span><span class="sxs-lookup"><span data-stu-id="d5fb1-112">Related Tasks and Topics</span></span>](#related)

##  <a name="basics"></a><a name="basics"></a><span data-ttu-id="d5fb1-113">方</span><span class="sxs-lookup"><span data-stu-id="d5fb1-113">Basics</span></span>
 <span data-ttu-id="d5fb1-114">*columnstore index* は、列ストアと呼ばれる列指向データ形式を使用してデータを格納、取得、および管理するためのテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-114">A *columnstore index* is a technology for storing, retrieving and managing data by using a columnar data format, called a columnstore.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="d5fb1-115">では、クラスター化列ストア インデックスと非クラスター化列ストア インデックスの両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-115">supports both clustered and nonclustered columnstore indexes.</span></span> <span data-ttu-id="d5fb1-116">どちらでも同じインメモリ列ストア テクノロジが使用されますが、目的とサポートされる機能に違いがあります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-116">Both use the same in-memory columnstore technology, but they do have differences in purpose and in features they support.</span></span>

###  <a name="benefits"></a><a name="benefits"></a> <span data-ttu-id="d5fb1-117">利点</span><span class="sxs-lookup"><span data-stu-id="d5fb1-117">Benefits</span></span>
 <span data-ttu-id="d5fb1-118">列ストア インデックスは、主に大きいデータ セットに対して分析を実行する読み取り専用のクエリで効果的に動作します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-118">Columnstore indexes work well for mostly read-only queries that perform analysis on large data sets.</span></span> <span data-ttu-id="d5fb1-119">多くの場合、これらはデータ ウェアハウスのワークロードのクエリです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-119">Often, these are queries for data warehousing workloads.</span></span> <span data-ttu-id="d5fb1-120">列ストア インデックスは、フル テーブル スキャンを使用するクエリで高いパフォーマンスを発揮しますが、データをシークして特定の値を検索するクエリには適していません。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-120">Columnstore indexes give high performance gains for queries that use full table scans, and are not well-suited for queries that seek into the data, searching for a particular value.</span></span>

 <span data-ttu-id="d5fb1-121">列ストア インデックスの利点:</span><span class="sxs-lookup"><span data-stu-id="d5fb1-121">Columnstore Index benefits:</span></span>

-   <span data-ttu-id="d5fb1-122">列には類似したデータがよくあり、圧縮比率が高くなります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-122">Columns often have similar data, which results in high compression rates.</span></span>

-   <span data-ttu-id="d5fb1-123">高い圧縮比率により、メモリ使用量が削減され、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-123">High compression rates improve query performance by using a smaller in-memory footprint.</span></span> <span data-ttu-id="d5fb1-124">さらに、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がより多くのクエリやデータ操作をインメモリで実行できるため、クエリのパフォーマンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-124">In turn, query performance can improve because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can perform more query and data operations in-memory.</span></span>

-   <span data-ttu-id="d5fb1-125">SQL Server に追加されたバッチ モード実行と呼ばれる新しいクエリ実行メカニズムにより、CPU 使用率が大きく軽減されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-125">A new query execution mechanism called batch-mode execution has been added to SQL Server that reduces CPU usage by a large amount.</span></span> <span data-ttu-id="d5fb1-126">バッチ モード実行は、列ストア ストレージ形式と緊密に統合され、このストレージ形式に合わせて最適化されています。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-126">Batch-mode execution is closely integrated with, and optimized around, the columnstore storage format.</span></span> <span data-ttu-id="d5fb1-127">バッチ モード実行は、ベクター ベースの実行またはベクター化された実行と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-127">Batch-mode execution is sometimes known as vector-based or vectorized execution.</span></span>

-   <span data-ttu-id="d5fb1-128">クエリはテーブルから少数の列のみを選択することが多く、物理メディアからの合計 I/O を低減します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-128">Queries often select only a few columns from a table, which reduces total I/O from the physical media.</span></span>

### <a name="columnstore-versions"></a><span data-ttu-id="d5fb1-129">列ストアのバージョン</span><span class="sxs-lookup"><span data-stu-id="d5fb1-129">Columnstore Versions</span></span>
 <span data-ttu-id="d5fb1-130">SQL Server 2012、SQL Server 2012 並列データ ウェアハウス、および SQL Server 2014 では、いずれも列ストア インデックスを使用して、一般的な列データ ウェアハウスのクエリが高速化されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-130">SQL Server 2012, SQL Server 2012 Parallel Data Warehouse, and SQL Server 2014 all use columnstore indexes to accelerate common data warehouse queries.</span></span> <span data-ttu-id="d5fb1-131">SQL Server 2012 では 2 つの新機能が導入されました。1 つは非クラスター化列ストア インデックスで、もう 1 つは、データを "バッチ" という単位で処理するベクター ベースのクエリ実行機能です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-131">SQL Server 2012 introduced two new features: a nonclustered columnstore index and a vector-based query execution capability that processes data in units called "batches."</span></span> <span data-ttu-id="d5fb1-132">SQL Server 2014 では、SQL Server 2012 の機能に加えて、更新可能なクラスター化列ストア インデックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-132">SQL Server 2014 has the features of SQL Server 2012 plus updateable clustered columnstore indexes.</span></span>

### <a name="key-characteristics"></a><span data-ttu-id="d5fb1-133">主な特性</span><span class="sxs-lookup"><span data-stu-id="d5fb1-133">Key Characteristics</span></span>

||
|-|
|<span data-ttu-id="d5fb1-134">**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5fb1-134">**Applies to**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] through [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>|

 <span data-ttu-id="d5fb1-135">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]でのクラスター化列ストア インデックス:</span><span class="sxs-lookup"><span data-stu-id="d5fb1-135">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a clustered columnstore index:</span></span>

-   <span data-ttu-id="d5fb1-136">Enterprise Edition、Developer Edition、および Evaluatio Edition で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-136">Is available in Enterprise, Developer, and Evaluation editions.</span></span>

-   <span data-ttu-id="d5fb1-137">更新可能です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-137">Is updateable.</span></span>

-   <span data-ttu-id="d5fb1-138">テーブル全体における主要な格納方法です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-138">Is the primary storage method for the entire table.</span></span>

-   <span data-ttu-id="d5fb1-139">キー列はありません。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-139">Has no key columns.</span></span> <span data-ttu-id="d5fb1-140">すべての列は付加列です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-140">All columns are included columns.</span></span>

-   <span data-ttu-id="d5fb1-141">テーブルの唯一のインデックスです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-141">Is the only index on the table.</span></span> <span data-ttu-id="d5fb1-142">他のどのインデックスとも組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-142">It cannot be combined with any other indexes.</span></span>

-   <span data-ttu-id="d5fb1-143">列ストアまたは列ストアの保存用圧縮を使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-143">Can be configured to use columnstore or columnstore archival compression.</span></span>

-   <span data-ttu-id="d5fb1-144">列を並べ替えられた順に物理的に格納するのではありません。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-144">Does not physically store columns in a sorted order.</span></span> <span data-ttu-id="d5fb1-145">代わりに、データを格納して圧縮とパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-145">Instead, it stores data to improve compression and performance.</span></span>

||
|-|
|<span data-ttu-id="d5fb1-146">**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5fb1-146">**Applies to**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] through [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>|

 <span data-ttu-id="d5fb1-147">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]での非クラスター化列ストア インデックス:</span><span class="sxs-lookup"><span data-stu-id="d5fb1-147">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a nonclustered columnstore index:</span></span>

-   <span data-ttu-id="d5fb1-148">クラスター化インデックスまたはヒープ内の列のサブセットにインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-148">Can index a subset of columns in the clustered index or heap.</span></span> <span data-ttu-id="d5fb1-149">たとえば、頻繁に使用される列にインデックスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-149">For example, it can index the frequently used columns.</span></span>

-   <span data-ttu-id="d5fb1-150">インデックス内の列のコピーを格納する追加ストレージが必要です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-150">Requires extra storage to store a copy of the columns in the index.</span></span>

-   <span data-ttu-id="d5fb1-151">は、インデックスの再構築またはパーティションの切り替えによって更新されます。挿入、更新、削除などの DML 操作を使用して更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-151">Is updated by rebuilding the index or switching partitions in and out. It is not updateable by using the DML operations such as insert, update, and delete.</span></span>

-   <span data-ttu-id="d5fb1-152">テーブルの他のインデックスと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-152">Can be combined with other indexes on the table.</span></span>

-   <span data-ttu-id="d5fb1-153">列ストアまたは列ストアの保存用圧縮を使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-153">Can be configured to use columnstore or columnstore archival compression.</span></span>

-   <span data-ttu-id="d5fb1-154">列を並べ替えられた順に物理的に格納するのではありません。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-154">Does not physically store columns in a sorted order.</span></span> <span data-ttu-id="d5fb1-155">代わりに、データを格納して圧縮とパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-155">Instead, it stores data to improve compression and performance.</span></span> <span data-ttu-id="d5fb1-156">列ストア インデックスの作成前にデータを並べ替える必要はありませんが、あらかじめ並べ替えておくと、列ストア圧縮が向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-156">Pre-sorting the data before creating the columnstore index is not required, but can improve columnstore compression.</span></span>

###  <a name="key-concepts-and-terms"></a><a name="Concepts"></a><span data-ttu-id="d5fb1-157">主要な概念と用語</span><span class="sxs-lookup"><span data-stu-id="d5fb1-157">Key Concepts and Terms</span></span>
 <span data-ttu-id="d5fb1-158">ここでは、列ストア インデックスに関連する主な用語と概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-158">The following key terms and concepts are associated with columnstore indexes.</span></span>

 <span data-ttu-id="d5fb1-159">列ストアインデックス列ストア*インデックス*は、列ストアと呼ばれる列形式のデータ形式を使用してデータを格納、取得、および管理するためのテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-159">columnstore index A *columnstore index* is a technology for storing, retrieving and managing data by using a columnar data format, called a columnstore.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="d5fb1-160">では、クラスター化列ストア インデックスと非クラスター化列ストア インデックスの両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-160">supports both clustered and nonclustered columnstore indexes.</span></span> <span data-ttu-id="d5fb1-161">どちらでも同じインメモリ列ストア テクノロジが使用されますが、目的とサポートされる機能に違いがあります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-161">Both use the same in-memory columnstore technology, but they do have differences in purpose and in features they support.</span></span>

 <span data-ttu-id="d5fb1-162">列ストア*は、* 行と列を含むテーブルとして論理的に編成され、列方向のデータ形式で物理的に格納されるデータです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-162">columnstore A *columnstore* is data that is logically organized as a table with rows and columns, and physically stored in a column-wise data format.</span></span>

 <span data-ttu-id="d5fb1-163">行ストア行*ストア*は、行と列を含むテーブルとして論理的に編成され、行方向のデータ形式で物理的に格納されるデータです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-163">rowstore A *rowstore* is data that is logically organized as a table with rows and columns, and then physically stored in a row-wise data format.</span></span> <span data-ttu-id="d5fb1-164">これは、リレーショナル テーブル データを格納する従来の方法です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-164">This has been the traditional way to store relational table data.</span></span>

 <span data-ttu-id="d5fb1-165">行グループと列セグメントは、高いパフォーマンスと高い圧縮率を目的としています。列ストアインデックスは、テーブルを行グループと呼ばれる行のグループにスライスし、各行グループを列方向に圧縮します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-165">rowgroups and column segments For high performance and high compression rates, the columnstore index slices the table into groups of rows, called row groups, and then compresses each row group in a column-wise manner.</span></span> <span data-ttu-id="d5fb1-166">行グループ内の行数は、圧縮率を向上させるのに十分な大きさで、インメモリ操作の利点を十分に小さくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-166">The number of rows in the row group must be large enough to improve compression rates, and small enough to benefit from in-memory operations.</span></span>

 <span data-ttu-id="d5fb1-167">行*グループ a 行グループは、同時*に列ストア形式に圧縮される行のグループです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-167">row group A *rowgroup* is a group of rows that are compressed into columnstore format at the same time.</span></span>

 <span data-ttu-id="d5fb1-168">列セグメント列*セグメント*は、行グループ内のデータの列です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-168">column segment A *column segment* is a column of data from within the rowgroup.</span></span>

-   <span data-ttu-id="d5fb1-169">通常、1 つの行グループには、行グループあたりの最大行数である 1,048,576 行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-169">A rowgroup usually contains the maximum number of rows per rowgroup which is 1,048,576 rows.</span></span>

-   <span data-ttu-id="d5fb1-170">それぞれの行グループには、テーブルの 1 つの列につき 1 つの列セグメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-170">Each rowgroup contains one column segment for every column in the table.</span></span>

-   <span data-ttu-id="d5fb1-171">それぞれの列セグメントは一緒に圧縮され、物理メディアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-171">Each column segment is compressed together and stored on physical media.</span></span>

 <span data-ttu-id="d5fb1-172">![列セグメント](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "列セグメント")</span><span class="sxs-lookup"><span data-stu-id="d5fb1-172">![Column segment](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")</span></span>

 <span data-ttu-id="d5fb1-173">非クラスター化列ストアインデックスは、既存のクラスター化インデックスまたはヒープテーブルに作成された読み取り専用の*インデックスです。*</span><span class="sxs-lookup"><span data-stu-id="d5fb1-173">nonclustered columnstore index A *nonclustered columnstore index* is a read-only index created on an existing clustered index or heap table.</span></span> <span data-ttu-id="d5fb1-174">このインデックスには、テーブル内のすべての列について、列のサブセットのコピーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-174">It contains a copy of a subset of columns, up to and including all of the columns in the table..</span></span> <span data-ttu-id="d5fb1-175">非クラスター化列ストアインデックスが含まれているテーブルは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-175">The table is read-only while it contains a nonclustered columnstore index.</span></span>

 <span data-ttu-id="d5fb1-176">非クラスター化列ストア インデックスは、分析クエリを実行しながら、同時に元のテーブルに対して読み取り専用操作を実行できる列ストア インデックスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-176">A nonclustered columnstore index provides a way to have a columnstore index for running analysis queries while at the same time performing read-only operations on the original table.</span></span>

 <span data-ttu-id="d5fb1-177">![非クラスター化列ストア インデックス](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "非クラスター化列ストア インデックス")</span><span class="sxs-lookup"><span data-stu-id="d5fb1-177">![Nonclustered columnstore index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "Nonclustered columnstore index")</span></span>

 <span data-ttu-id="d5fb1-178">クラスター化列ストア*インデックスは、* テーブル全体の物理ストレージであり、テーブルの唯一のインデックスです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-178">clustered columnstore index A *clustered columnstore index* is the physical storage for the entire table and is the only index for the table.</span></span> <span data-ttu-id="d5fb1-179">クラスター化インデックスは更新可能です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-179">The clustered index is updateable.</span></span> <span data-ttu-id="d5fb1-180">インデックスに対して挿入、削除、および更新操作を実行したり、インデックスへのデータの一括読み込みを行ったりできます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-180">You can perform insert, delete, and update operations on the index and you can bulk load data into the index.</span></span>

 <span data-ttu-id="d5fb1-181">![クラスター化列ストア インデックス](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "クラスター化列ストア インデックス")</span><span class="sxs-lookup"><span data-stu-id="d5fb1-181">![Clustered Columnstore Index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")</span></span>

 <span data-ttu-id="d5fb1-182">列セグメントの断片化を低減し、パフォーマンスを高めるために、列ストア インデックスでは、一部のデータおよび削除された行に対応する ID の B-Tree を一時的に行ストア テーブルに格納することがあります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-182">To reduce fragmentation of the column segments and improve performance, the columnstore index might store some data temporarily into a rowstore table, called a deltastore, plus a B-Tree of IDs for deleted rows.</span></span> <span data-ttu-id="d5fb1-183">デルタストア操作は内部で処理されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-183">The deltastore operations are handled behind the scenes.</span></span> <span data-ttu-id="d5fb1-184">列ストア インデックスは、正しいクエリ結果を返すために、列ストアとデルタストアの両方からのクエリ結果を結合します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-184">To return the correct query results, the clustered columnstore index combines query results from both the columnstore and the deltastore.</span></span>

 <span data-ttu-id="d5fb1-185">デルタストアは、クラスター化列ストアインデックスでのみ使用されます。デルタ*ストア*は、行の数が列ストアに移動するのに十分な大きさになるまで行を格納する行ストアテーブルです。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-185">deltastore Used with clustered columnstore indexes only, a *deltastore* is a rowstore table that stores rows until the number of rows is large enough to be moved into the columnstore.</span></span> <span data-ttu-id="d5fb1-186">デルタストアは、読み込みやその他の DML 操作のパフォーマンスを高めるために、クラスター化列ストア インデックスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-186">A deltastore is used with clustered columnstore indexes to improve performance for loading and other DML operations.</span></span>

 <span data-ttu-id="d5fb1-187">大規模な一括読み込みでは、行のほとんどがデルタストアを通らずに列ストアに直接移動します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-187">During a large bulk load, most of the rows go directly to the columnstore without passing through the deltastore.</span></span> <span data-ttu-id="d5fb1-188">一括読み込みの最後に位置する行の数は、行グループの最小サイズである 102,400 行を満たすには足りないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-188">Some rows at the end of the bulk load might be too few in number to meet the minimum size of a rowgroup which is 102,400 rows.</span></span> <span data-ttu-id="d5fb1-189">この場合、それらの行は列ストアではなくデルタストアに移動します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-189">When this happens, the final rows go to the deltastore instead of the columnstore.</span></span> <span data-ttu-id="d5fb1-190">102,400 行未満の小規模な一括読み込みでは、すべての行がデルタストアに直接移動します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-190">For small bulk loads with less than 102,400 rows, all of the rows go directly to the deltastore.</span></span>

 <span data-ttu-id="d5fb1-191">デルタストアは、最大行数に達すると閉じられます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-191">When the deltastore reaches the maximum number of rows, it becomes closed.</span></span> <span data-ttu-id="d5fb1-192">タプル移動プロセスは、終了した行グループを確認します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-192">A tuple-move process checks for closed row groups.</span></span> <span data-ttu-id="d5fb1-193">閉じている行グループが見つかると、その行グループが圧縮され、列ストアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-193">When it finds the closed rowgroup, it compresses it and stores it into the columnstore.</span></span>

##  <a name="loading-data"></a><a name="dataload"></a><span data-ttu-id="d5fb1-194">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="d5fb1-194">Loading Data</span></span>

###  <a name="loading-data-into-a-nonclustered-columnstore-index"></a><a name="dataload_nci"></a><span data-ttu-id="d5fb1-195">非クラスター化列ストアインデックスへのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="d5fb1-195">Loading Data into a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="d5fb1-196">データを非クラスター化列ストアインデックスに読み込むには、まず、ヒープまたはクラスター化インデックスとして格納されている従来の行ストアテーブルにデータを読み込み、次に[transact-sql&#41;&#40;CREATE 列ストアインデックス](/sql/t-sql/statements/create-columnstore-index-transact-sql)を使用して非クラスター化列ストアインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-196">To load data into a nonclustered columnstore index, first load data into a traditional rowstore table stored as a heap or clustered index, and then create the nonclustered columnstore index with [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>

 <span data-ttu-id="d5fb1-197">![列ストア インデックスへのデータの読み込み](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "列ストア インデックスへのデータの読み込み")</span><span class="sxs-lookup"><span data-stu-id="d5fb1-197">![Loading data into a columnstore index](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Loading data into a columnstore index")</span></span>

 <span data-ttu-id="d5fb1-198">非クラスター化列ストア インデックスを持つテーブルは、インデックスが削除または無効化されるまで読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-198">A table with a nonclustered columnstore index is read-only until the index is dropped or disabled.</span></span> <span data-ttu-id="d5fb1-199">テーブルと非クラスター化列ストアインデックスを更新するには、パーティションを切り替えることができます。また、インデックスを無効にし、テーブルを更新してから、インデックスを再構築することもできます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-199">To update the table and the nonclustered columnstore index you can switch partitions in and out. You can also disable the index, update the table, and then rebuild the index.</span></span>

 <span data-ttu-id="d5fb1-200">詳細については、「 [Using Nonclustered Columnstore Indexes](indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-200">For more information see [Using Nonclustered Columnstore Indexes](indexes.md)</span></span>

###  <a name="loading-data-into-a-clustered-columnstore-index"></a><a name="dataload_cci"></a><span data-ttu-id="d5fb1-201">クラスター化列ストアインデックスへのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="d5fb1-201">Loading Data into a Clustered Columnstore Index</span></span>
 <span data-ttu-id="d5fb1-202">![クラスター化列ストア インデックスへの読み込み](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "クラスター化列ストア インデックスへの読み込み")</span><span class="sxs-lookup"><span data-stu-id="d5fb1-202">![Loading into a clustered columnstore index](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "Loading into a clustered columnstore index")</span></span>

 <span data-ttu-id="d5fb1-203">図が示すように、クラスター化列ストア インデックスにデータを読み込むには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]は次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-203">As the diagram suggests, to load data into a clustered columnstore index, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>

1.  <span data-ttu-id="d5fb1-204">最大サイズの行グループを列ストアに直接挿入します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-204">Inserts maximum-size rowgroups directly into the columnstore.</span></span> <span data-ttu-id="d5fb1-205">データが読み込まれると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は開いている行グループに先着順でデータ行を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-205">As the data is loaded, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assigns the data rows in a first-come first-serve order into an open rowgroup.</span></span>

2.  <span data-ttu-id="d5fb1-206">それぞれの行グループが最大サイズに到達すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]は次の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-206">For each rowgroup, after it reaches the maximum size, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>

    1.  <span data-ttu-id="d5fb1-207">行グループを CLOSED としてマークします。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-207">Marks the rowgroup as CLOSED.</span></span>

    2.  <span data-ttu-id="d5fb1-208">デルタストアをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-208">Bypasses the deltastore.</span></span>

    3.  <span data-ttu-id="d5fb1-209">列ストア圧縮を使用する行グループで、それぞれの列セグメントを圧縮します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-209">Compresses each column segment with the rowgroup with columnstore compression.</span></span>

    4.  <span data-ttu-id="d5fb1-210">圧縮された列セグメントを列ストアに物理的に格納します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-210">Physically stores each compressed column segment into the columnstore.</span></span>

3.  <span data-ttu-id="d5fb1-211">次のように、列ストアまたはデルタストアに残りの行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-211">Inserts the remaining rows into the columnstore or the deltastore as follows:</span></span>

    1.  <span data-ttu-id="d5fb1-212">行数が行グループの最小限の行数の要件を満たしている場合は、行が列ストアに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-212">If the number of rows meets the minimum rows per rowgroup requirement, the rows are added to the columnstore.</span></span>

    2.  <span data-ttu-id="d5fb1-213">行数が行グループの最小限の行数の要件を満たしていない場合は、行がデルタストアに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-213">If the number of rows is less than the minimum rows per rowgroup, the rows are added to the deltastore.</span></span>

 <span data-ttu-id="d5fb1-214">デルタストアのタスクとプロセスの詳細については、「 [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-214">For more information about deltastore tasks and processes, see [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)</span></span>

##  <a name="performance-tips"></a><a name="performance"></a><span data-ttu-id="d5fb1-215">パフォーマンスに関するヒント</span><span class="sxs-lookup"><span data-stu-id="d5fb1-215">Performance Tips</span></span>

### <a name="plan-for-enough-memory-to-create-columnstore-indexes-in-parallel"></a><span data-ttu-id="d5fb1-216">列ストア インデックスを並列で作成するための十分なメモリの計画</span><span class="sxs-lookup"><span data-stu-id="d5fb1-216">Plan for enough memory to create columnstore indexes in parallel</span></span>
 <span data-ttu-id="d5fb1-217">列ストア インデックスの作成は、メモリに制限がない限り既定で並列操作になります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-217">Creating a columnstore index is by default a parallel operation unless memory is constrained.</span></span> <span data-ttu-id="d5fb1-218">インデックスを並列で作成するには、インデックスを順次作成する場合よりも多くのメモリが必要です。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-218">Creating the index in parallel requires more memory than creating the index serially.</span></span> <span data-ttu-id="d5fb1-219">十分なメモリがある場合、列ストア インデックスの作成には、同じ列で B-Tree を構築する場合の約 1.5 倍の時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-219">When there is ample memory, creating a columnstore index takes on the order of 1.5 times as long as building a B-tree on the same columns.</span></span>

 <span data-ttu-id="d5fb1-220">列ストア インデックスを作成するために必要なメモリは、列数、文字列型の列数、並列処理の最大限度 (DOP)、およびデータの特性によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-220">The memory required for creating a columnstore index depends on the number of columns, the number of string columns, the degree of parallelism (DOP), and the characteristics of the data.</span></span> <span data-ttu-id="d5fb1-221">たとえば、テーブル内の行数が 100 万未満の場合、SQL Server はスレッドを 1 つだけ使用して列ストア インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-221">For example, if your table has fewer than one million rows, SQL Server will use only one thread to create the columnstore index.</span></span>

 <span data-ttu-id="d5fb1-222">テーブルに 100 万を超える行があり、SQL Server で MAXDOP を使用してインデックスを作成するための十分なメモリ許可を取得できない場合、SQL Server は必要に応じて自動的に MAXDOP を減らし、使用できるメモリ許可に合うように調整します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-222">If your table has more than one million rows, but SQL Server cannot get a large enough memory grant to create the index using MAXDOP, SQL Server will automatically decrease MAXDOP as needed to fit into the available memory grant.</span></span>  <span data-ttu-id="d5fb1-223">場合によっては、メモリが制限された状況でインデックスを構築できるように、DOP を 1 まで小さくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-223">In some cases, DOP must be decreased to one in order to build the index under constrained memory.</span></span>

##  <a name="related-tasks-and-topics"></a><a name="related"></a><span data-ttu-id="d5fb1-224">関連するタスクとトピック</span><span class="sxs-lookup"><span data-stu-id="d5fb1-224">Related Tasks and Topics</span></span>

### <a name="nonclustered-columnstore-indexes"></a><span data-ttu-id="d5fb1-225">非クラスター化列ストア インデックス</span><span class="sxs-lookup"><span data-stu-id="d5fb1-225">Nonclustered Columnstore Indexes</span></span>
 <span data-ttu-id="d5fb1-226">一般的なタスクについては、「 [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-226">For common tasks, see [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md).</span></span>

-   [<span data-ttu-id="d5fb1-227">CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-227">CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-columnstore-index-transact-sql)

-   <span data-ttu-id="d5fb1-228">[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)を再構築します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-228">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD.</span></span>

-   [<span data-ttu-id="d5fb1-229">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-229">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)

### <a name="clustered-columnstore-indexes"></a><span data-ttu-id="d5fb1-230">クラスター化列ストア インデックス</span><span class="sxs-lookup"><span data-stu-id="d5fb1-230">Clustered Columnstore Indexes</span></span>
 <span data-ttu-id="d5fb1-231">一般的なタスクについては、「 [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-231">For common tasks, see [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md).</span></span>

-   [<span data-ttu-id="d5fb1-232">Transact-sql&#41;&#40;のクラスター化列ストアインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="d5fb1-232">CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-columnstore-index-transact-sql)

-   <span data-ttu-id="d5fb1-233">[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)を再構築または再構成します。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-233">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD or REORGANIZE.</span></span>

-   [<span data-ttu-id="d5fb1-234">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-234">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)

-   [<span data-ttu-id="d5fb1-235">INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-235">INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/insert-transact-sql)

-   [<span data-ttu-id="d5fb1-236">UPDATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-236">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)

-   [<span data-ttu-id="d5fb1-237">DELETE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-237">DELETE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/delete-transact-sql)

### <a name="metadata"></a><span data-ttu-id="d5fb1-238">Metadata</span><span class="sxs-lookup"><span data-stu-id="d5fb1-238">Metadata</span></span>
 <span data-ttu-id="d5fb1-239">列ストア インデックス内のすべての列は、付加列としてメタデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-239">All of the columns in a columnstore index are stored in the metadata as included columns.</span></span> <span data-ttu-id="d5fb1-240">列ストア インデックスにキー列はありません。</span><span class="sxs-lookup"><span data-stu-id="d5fb1-240">The columnstore index does not have key columns.</span></span>

-   [<span data-ttu-id="d5fb1-241">sys.indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-241">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)

-   [<span data-ttu-id="d5fb1-242">sys.index_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-242">sys.index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)

-   [<span data-ttu-id="d5fb1-243">sys.partitions &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-243">sys.partitions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql)

-   [<span data-ttu-id="d5fb1-244">sys.column_store_segments &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-244">sys.column_store_segments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-segments-transact-sql)

-   [<span data-ttu-id="d5fb1-245">sys.column_store_dictionaries &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-245">sys.column_store_dictionaries &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql)

-   [<span data-ttu-id="d5fb1-246">sys.column_store_row_groups &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5fb1-246">sys.column_store_row_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)


