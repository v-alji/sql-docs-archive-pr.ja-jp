---
title: メモリ最適化テーブルでのインデックスの使用に関するガイドライン |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- hash indexes
ms.assetid: 16ef63a4-367a-46ac-917d-9eebc81ab29b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f00d643088634c918eb626917eae64a001ce3678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716597"
---
# <a name="guidelines-for-using-indexes-on-memory-optimized-tables"></a><span data-ttu-id="d8388-102">メモリ最適化テーブルでのインデックス使用のガイドライン</span><span class="sxs-lookup"><span data-stu-id="d8388-102">Guidelines for Using Indexes on Memory-Optimized Tables</span></span>
  <span data-ttu-id="d8388-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブルのデータに効率的にアクセスするためにインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8388-103">Indexes are used for efficiently accessing data in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="d8388-104">適切なインデックスを指定することにより、クエリのパフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="d8388-104">Specifying the right indexes can dramatically improve query performance.</span></span> <span data-ttu-id="d8388-105">たとえば、次のクエリについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="d8388-105">Consider, for example, the query:</span></span>  
  
```sql  
SELECT c1, c2 FROM t WHERE c1 = 1;  
```  
  
 <span data-ttu-id="d8388-106">列 c1 にインデックスがない場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、テーブル t 全体をスキャンして、条件 c1=1 を満たす行をフィルター処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8388-106">If there is no index on column c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will need to scan the entire table t, and then filter on the rows that satisfy the condition c1=1.</span></span> <span data-ttu-id="d8388-107">一方、列 c1 にインデックスがある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、値 1 を直接シークして行を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d8388-107">However, if t has an index on column c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can seek directly on the value 1 and retrieve the rows.</span></span>  
  
 <span data-ttu-id="d8388-108">テーブルの 1 個以上の列について、特定の値または値の範囲を持つレコードを検索する場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ではそれらの列のインデックスを使用することで、対応するレコードを迅速に検索できます。</span><span class="sxs-lookup"><span data-stu-id="d8388-108">When searching for records that have a specific value, or range of values, for one or more columns in the table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can use an index on those columns to quickly locate the corresponding records.</span></span> <span data-ttu-id="d8388-109">ディスク ベースのテーブルおよびメモリ最適化テーブルのいずれの場合でも、インデックスの利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="d8388-109">Both disk-based and memory-optimized tables benefit from indexes.</span></span> <span data-ttu-id="d8388-110">ただし、インデックス構造間には、メモリ最適化テーブルを使用する場合に考慮する必要がある一定の相違点があります </span><span class="sxs-lookup"><span data-stu-id="d8388-110">There are, however, certain differences between index structures that need to be considered when using memory-optimized tables.</span></span> <span data-ttu-id="d8388-111">(メモリ最適化テーブルのインデックスは、メモリ最適化インデックスと呼ばれます)。主な違いの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d8388-111">(Indexes on memory-optimized tables are referred to as memory-optimized indexes.) Some of the key differences are:</span></span>  
  
-   <span data-ttu-id="d8388-112">メモリ最適化インデックスは[CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql)で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8388-112">Memory-optimized indexes must be created with [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span> <span data-ttu-id="d8388-113">ディスク ベース インデックスは、`CREATE TABLE` および `CREATE INDEX` を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="d8388-113">Disk-based indexes can be created with `CREATE TABLE` and `CREATE INDEX`.</span></span>  
  
-   <span data-ttu-id="d8388-114">メモリ最適化インデックスはメモリにしか存在しません。</span><span class="sxs-lookup"><span data-stu-id="d8388-114">Memory-optimized indexes exist only in memory.</span></span> <span data-ttu-id="d8388-115">インデックス構造はディスクに保存されず、インデックス操作はトランザクション ログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="d8388-115">Index structures are not persisted to disk and index operations are not logged in the transaction log.</span></span> <span data-ttu-id="d8388-116">インデックス構造は、CREATE TABLE の実行中およびデータベースの起動中に、メモリ最適化テーブルがメモリ内に作成されるときに作成されます。</span><span class="sxs-lookup"><span data-stu-id="d8388-116">The index structure is created when the memory-optimized table is created in memory, both during CREATE TABLE and during database startup.</span></span>  
  
-   <span data-ttu-id="d8388-117">メモリ最適化インデックスは本質的にいきわたっています。</span><span class="sxs-lookup"><span data-stu-id="d8388-117">Memory-optimized indexes are inherently covering.</span></span> <span data-ttu-id="d8388-118">いきわたっているという意味は、すべての列が実質的にインデックスに含まれて、メモリ最適化テーブルにブックマーク参照は必要ないということです。</span><span class="sxs-lookup"><span data-stu-id="d8388-118">Covering means that all columns are virtually included in the index and bookmark lookups are not needed for memory-optimized tables.</span></span> <span data-ttu-id="d8388-119">主キーへの参照ではなく、メモリ最適化インデックスには、テーブル データ構造内の実際の行を指すメモリ ポインターだけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8388-119">Rather than a reference to the primary key, memory-optimized indexes simply contain a memory pointer to the actual row in the table data structure.</span></span>  
  
-   <span data-ttu-id="d8388-120">断片化と Fillfactor は、メモリ最適化インデックスには適用されません。</span><span class="sxs-lookup"><span data-stu-id="d8388-120">Fragmentation and fillfactor do not apply to memory-optimized indexes.</span></span> <span data-ttu-id="d8388-121">ディスク ベース インデックスでは、断片化は、乱れた順序でディスクに書き込まれる B ツリーのページを示します。</span><span class="sxs-lookup"><span data-stu-id="d8388-121">In disk-based indexes, fragmentation refers to pages in the B-tree being written to disk out-of-order.</span></span> <span data-ttu-id="d8388-122">メモリ最適化インデックスは、ディスクに対して書き込まれることも読み取られることもありません。</span><span class="sxs-lookup"><span data-stu-id="d8388-122">Memory-optimized indexes are not written to or read from disk.</span></span> <span data-ttu-id="d8388-123">ディスク ベースの B ツリー インデックスの Fillfactor は、物理ページ構造が実際のデータでいっぱいになる度合いを示します。</span><span class="sxs-lookup"><span data-stu-id="d8388-123">Fillfactor in disk-based B-tree indexes refers to the degree to which the physical page structures are filled with actual data.</span></span> <span data-ttu-id="d8388-124">メモリ最適化インデックス構造には、固定サイズのページはありません。</span><span class="sxs-lookup"><span data-stu-id="d8388-124">The memory-optimized index structures do not have fixed-size pages.</span></span>  
  
 <span data-ttu-id="d8388-125">メモリ最適化インデックスには、次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="d8388-125">There are two types of memory-optimized indexes:</span></span>  
  
-   <span data-ttu-id="d8388-126">ポイント参照用に作成された非クラスター化ハッシュ インデックス。</span><span class="sxs-lookup"><span data-stu-id="d8388-126">Nonclustered hash indexes, which are made for point lookups.</span></span> <span data-ttu-id="d8388-127">ハッシュインデックスの詳細については、「[ハッシュインデックス](hash-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8388-127">For more information about hash indexes, see [Hash Indexes](hash-indexes.md).</span></span>  
  
-   <span data-ttu-id="d8388-128">範囲スキャンと並べ替えられたスキャン用に作成された非クラスター化インデックス。</span><span class="sxs-lookup"><span data-stu-id="d8388-128">Nonclustered indexes, which are made for range scans and ordered scans.</span></span>  
  
 <span data-ttu-id="d8388-129">ハッシュ インデックスの場合は、インメモリ ハッシュ テーブルを通じてデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d8388-129">With a hash index, data is accessed through an in-memory hash table.</span></span> <span data-ttu-id="d8388-130">ハッシュ インデックスにはページはなく、常に固定サイズです。</span><span class="sxs-lookup"><span data-stu-id="d8388-130">Hash indexes do not have pages and are always of a fixed size.</span></span> <span data-ttu-id="d8388-131">ただし、ハッシュ インデックスは、限定的な使用されていない空間が生じることになる空のハッシュ バケットを伴うことがあります。</span><span class="sxs-lookup"><span data-stu-id="d8388-131">However, a hash index can have empty hash buckets, which result in limited wasted space.</span></span> <span data-ttu-id="d8388-132">ハッシュ インデックスを使用するクエリから返された値の並べ替えは行われません。</span><span class="sxs-lookup"><span data-stu-id="d8388-132">The values returned from a query using a hash index are not sorted.</span></span> <span data-ttu-id="d8388-133">ハッシュ インデックスは、等値述語に対するインデックス シーク用に最適化されており、フル インデックス スキャンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d8388-133">Hash indexes are optimized for index seeks on equality predicates and also support full index scans.</span></span>  
  
 <span data-ttu-id="d8388-134">(ハッシュ インデックスではない) 非クラスター化インデックスでは、ハッシュ インデックスでサポートされるすべての操作に加えて、"より大きい" や "より小さい" などの不等値述語に対するシーク操作、および並べ替え順がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d8388-134">Nonclustered indexes (not hash indexes) support everything that hash indexes supports plus seek operations on inequality predicates such as greater than or less than, as well as sort order.</span></span> <span data-ttu-id="d8388-135">行は、インデックスの作成時に指定した順序に従って取得できます。</span><span class="sxs-lookup"><span data-stu-id="d8388-135">Rows can be retrieved according to the order specified with index creation.</span></span> <span data-ttu-id="d8388-136">インデックスの並べ替え順が特定のクエリに必要な並べ替え順と一致する場合 (たとえば、インデックス キーが ORDER BY 句と一致する場合)、クエリの実行の一環として行を並べ替える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d8388-136">If the sort order of the index matches the sort order required for a particular query, for example if the index key matches the ORDER BY clause, there is no need to sort the rows as part of query execution.</span></span> <span data-ttu-id="d8388-137">メモリ最適化された非クラスター化インデックスは 1 方向です。つまり、インデックスの並べ替え順の逆となる並べ替え順で行を取得することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d8388-137">Memory-optimized nonclustered indexes are unidirectional; they do not support retrieving rows in a sort order that is the reverse of the sort order of the index.</span></span> <span data-ttu-id="d8388-138">たとえば、指定されたインデックスが (c1 ASC) の場合、逆順、つまり (c1 DESC) でインデックスをスキャンすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d8388-138">For example, for an index specified as (c1 ASC), it is not possible to scan the index in reverse order, as (c1 DESC).</span></span>  
  
 <span data-ttu-id="d8388-139">各インデックスはメモリを消費します。</span><span class="sxs-lookup"><span data-stu-id="d8388-139">Each index consumes memory.</span></span> <span data-ttu-id="d8388-140">ハッシュ インデックスは、バケット数の関数である固定量のメモリを消費します。</span><span class="sxs-lookup"><span data-stu-id="d8388-140">Hash indexes consume a fixed amount of memory, which is a function of the bucket count.</span></span> <span data-ttu-id="d8388-141">非クラスター化インデックスの場合、メモリ消費量はインデックス キー列の行数とサイズによって決まり、ワークロードによってはオーバーヘッドが増加することがあります。</span><span class="sxs-lookup"><span data-stu-id="d8388-141">For nonclustered indexes, memory consumption is a function of the row count and the size of the index key columns, with some additional overhead depending on the workload.</span></span> <span data-ttu-id="d8388-142">メモリ最適化インデックス用のメモリは、メモリ最適化テーブルに行を格納するために使用されるメモリとは別であり、これに加えて必要になります。</span><span class="sxs-lookup"><span data-stu-id="d8388-142">Memory for memory-optimized indexes is in addition to and separate from the memory used to store rows in memory-optimized tables.</span></span>  
  
 <span data-ttu-id="d8388-143">重複するキーの値によって、同じハッシュ バケットが常に共有されます。</span><span class="sxs-lookup"><span data-stu-id="d8388-143">Duplicate key values always share the same hash bucket.</span></span> <span data-ttu-id="d8388-144">重複するキーの値がハッシュ インデックスに多数含まれている場合、ハッシュ チェーンが長くなってパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="d8388-144">If a hash index contains many duplicate key values, the resulting long hash chains will harm performance.</span></span> <span data-ttu-id="d8388-145">どのハッシュ インデックスでも発生するハッシュの競合により、このシナリオではパフォーマンスはさらに低下します。</span><span class="sxs-lookup"><span data-stu-id="d8388-145">Hash collisions, which occur in any hash index, will further reduce performance in this scenario.</span></span> <span data-ttu-id="d8388-146">このため、一意のインデックスキーの数が行数より少なくとも100倍になると、バケット数を大幅に増やすことでハッシュの競合のリスクを軽減できます (詳細については、「[ハッシュインデックスの正しいバケット数の決定](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md)」を参照してください)。または、非クラスター化インデックスを使用してハッシュの競合を完全に排除</span><span class="sxs-lookup"><span data-stu-id="d8388-146">For that reason, if the number of unique index keys is at least 100 times smaller than the row count, you can reduce the risk of hash collisions by making the bucket count much larger (at least eight times the number of unique index keys; see [Determining the Correct Bucket Count for Hash Indexes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) for more information) or you can eliminate hash collisions entirely by using a nonclustered index.</span></span>  
  
## <a name="determining-which-indexes-to-use-for-a-memory-optimized-table"></a><span data-ttu-id="d8388-147">メモリ最適化テーブルに使用するインデックスの決定</span><span class="sxs-lookup"><span data-stu-id="d8388-147">Determining Which Indexes to Use for a Memory-Optimized Table</span></span>  
 <span data-ttu-id="d8388-148">それぞれのメモリ最適化テーブルには、1 つ以上のインデックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="d8388-148">Each memory-optimized table must have at least one index.</span></span> <span data-ttu-id="d8388-149">それぞれの PRIMARY KEY 制約では、暗黙的にインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8388-149">Note that each PRIMARY KEY constraint implicitly creates an index.</span></span> <span data-ttu-id="d8388-150">したがって、テーブルに主キーがある場合は、インデックスがあります。</span><span class="sxs-lookup"><span data-stu-id="d8388-150">Therefore, if a table has a primary key, it has an index.</span></span> <span data-ttu-id="d8388-151">主キーは、持続性のあるメモリ最適化テーブルに必須です。</span><span class="sxs-lookup"><span data-stu-id="d8388-151">A primary key is a requirement for a durable memory-optimized table.</span></span>  
  
 <span data-ttu-id="d8388-152">メモリ最適化テーブルを照会する際に、述語句に等値述語のみが含まれている場合は、ハッシュ インデックスのパフォーマンスが高くなります。</span><span class="sxs-lookup"><span data-stu-id="d8388-152">When querying a memory-optimized table, hash indexes perform better when the predicate clause contains only equality predicates.</span></span> <span data-ttu-id="d8388-153">述語はハッシュ インデックス キーのすべての列を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8388-153">The predicate must include all columns in the hash index key.</span></span> <span data-ttu-id="d8388-154">ハッシュ インデックスは、非等値述語が指定されているとスキャンに戻ります。</span><span class="sxs-lookup"><span data-stu-id="d8388-154">A hash index will revert to a scan given an inequality predicate.</span></span>  
  
 <span data-ttu-id="d8388-155">メモリ最適化テーブルの列は、ハッシュ インデックスと非クラスター化インデックスの両方に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d8388-155">A column in a memory-optimized table can be part of both a hash index and a nonclustered index.</span></span>  
  
 <span data-ttu-id="d8388-156">非等値述語でメモリ最適化テーブルを照会する場合は、非クラスター化ハッシュ インデックスより非クラスター化インデックスのパフォーマンスが高くなります。</span><span class="sxs-lookup"><span data-stu-id="d8388-156">When querying a memory-optimized table with inequality predicates, nonclustered indexes will perform better than nonclustered hash indexes.</span></span>  
  
 <span data-ttu-id="d8388-157">ハッシュ インデックスでは、インデックスに対してシークを実行するための (ハッシュ用の) キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="d8388-157">The hash index requires a key (to hash) to seek into the index.</span></span> <span data-ttu-id="d8388-158">インデックス キーが 2 列で構成される場合に、最初の列しか指定されないと、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でハッシュ用とするキーが不完全になります。</span><span class="sxs-lookup"><span data-stu-id="d8388-158">If an index key consists of two columns and you only provide the first column, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not have a complete key to hash.</span></span> <span data-ttu-id="d8388-159">この場合は、インデックス スキャン クエリ プランが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d8388-159">This will result in an index scan query plan.</span></span> <span data-ttu-id="d8388-160">インデックスを設定する列は、使用状況によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="d8388-160">Usage determines which columns should be indexed.</span></span>  
  
 <span data-ttu-id="d8388-161">非クラスター化インデックスの列の値が、多数の行で同じである (インデックス キー列に多数の重複値がある) 場合は、更新、挿入、および削除に関してパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="d8388-161">When a column in a nonclustered index has the same value in many rows (index key columns have a lot of duplicate values), performance can degrade for updates, inserts, and deletions.</span></span>  <span data-ttu-id="d8388-162">このような場合にパフォーマンスを改善する方法の 1 つは、非クラスター化インデックスに列を追加することです。</span><span class="sxs-lookup"><span data-stu-id="d8388-162">One way to improve performance in this situation is to add another column to the nonclustered index.</span></span>  
  
### <a name="operations-on-memory-optimized-and-disk-based-indexes"></a><span data-ttu-id="d8388-163">メモリ最適化インデックスおよびディスク ベース インデックスに対する操作</span><span class="sxs-lookup"><span data-stu-id="d8388-163">Operations on memory-optimized and disk-based indexes.</span></span>  
  
|<span data-ttu-id="d8388-164">操作</span><span class="sxs-lookup"><span data-stu-id="d8388-164">Operation</span></span>|<span data-ttu-id="d8388-165">メモリ最適化された非クラスター化ハッシュ インデックス</span><span class="sxs-lookup"><span data-stu-id="d8388-165">Memory-optimized, nonclustered hash, index</span></span>|<span data-ttu-id="d8388-166">メモリ最適化された非クラスター化インデックス</span><span class="sxs-lookup"><span data-stu-id="d8388-166">Memory-optimized nonclustered index</span></span>|<span data-ttu-id="d8388-167">ディスク ベース インデックス</span><span class="sxs-lookup"><span data-stu-id="d8388-167">Disk-based index</span></span>|  
|---------------|-------------------------------------------------|------------------------------------------|-----------------------|  
|<span data-ttu-id="d8388-168">インデックス スキャン、すべてのテーブルの行を取得する。</span><span class="sxs-lookup"><span data-stu-id="d8388-168">Index Scan, retrieve all table rows.</span></span>|<span data-ttu-id="d8388-169">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-169">Yes</span></span>|<span data-ttu-id="d8388-170">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-170">Yes</span></span>|<span data-ttu-id="d8388-171">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-171">Yes</span></span>|  
|<span data-ttu-id="d8388-172">等値述語 (=) に対するインデックス シーク。</span><span class="sxs-lookup"><span data-stu-id="d8388-172">Index seek on equality predicate(s) (=).</span></span>|<span data-ttu-id="d8388-173">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-173">Yes</span></span><br /><br /> <span data-ttu-id="d8388-174">(フル キーが必要)</span><span class="sxs-lookup"><span data-stu-id="d8388-174">(Full key required.)</span></span>|<span data-ttu-id="d8388-175">はい <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d8388-175">Yes <sup>1</sup></span></span>|<span data-ttu-id="d8388-176">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-176">Yes</span></span>|  
|<span data-ttu-id="d8388-177">非等値述語 (>、<、 \<=, > =、BETWEEN) に対するインデックスシーク。</span><span class="sxs-lookup"><span data-stu-id="d8388-177">Index seek on inequality predicates (>, <, \<=, >=, BETWEEN).</span></span>|<span data-ttu-id="d8388-178">不可 (インデックス スキャンの結果)</span><span class="sxs-lookup"><span data-stu-id="d8388-178">No (results in an index scan)</span></span>|<span data-ttu-id="d8388-179">はい <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d8388-179">Yes <sup>1</sup></span></span>|<span data-ttu-id="d8388-180">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-180">Yes</span></span>|  
|<span data-ttu-id="d8388-181">インデックス定義に一致する並べ替え順序で行を取得する。</span><span class="sxs-lookup"><span data-stu-id="d8388-181">Retrieve rows in a sort-order matching the index definition.</span></span>|<span data-ttu-id="d8388-182">いいえ</span><span class="sxs-lookup"><span data-stu-id="d8388-182">No</span></span>|<span data-ttu-id="d8388-183">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-183">Yes</span></span>|<span data-ttu-id="d8388-184">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-184">Yes</span></span>|  
|<span data-ttu-id="d8388-185">インデックス定義の逆の並べ替え順序で行を取得する。</span><span class="sxs-lookup"><span data-stu-id="d8388-185">Retrieve rows in a sort-order matching the reverse of the index definition.</span></span>|<span data-ttu-id="d8388-186">いいえ</span><span class="sxs-lookup"><span data-stu-id="d8388-186">No</span></span>|<span data-ttu-id="d8388-187">いいえ</span><span class="sxs-lookup"><span data-stu-id="d8388-187">No</span></span>|<span data-ttu-id="d8388-188">はい</span><span class="sxs-lookup"><span data-stu-id="d8388-188">Yes</span></span>|  
  
 <span data-ttu-id="d8388-189">この表で、可はインデックスによって要求を十分に満たすことができることを意味し、不可は要求を満たすためにインデックスを適切に使用できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="d8388-189">In the table, Yes means that the index can adequately service the request and No means that the index cannot be used successfully to satisfy the request.</span></span>  
  
 <span data-ttu-id="d8388-190"><sup>1</sup>非クラスター化メモリ最適化インデックスの場合、インデックスシークの実行にフルキーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d8388-190"><sup>1</sup> For a nonclustered memory-optimized index, the full key is not required to perform an index seek.</span></span> <span data-ttu-id="d8388-191">ただし、インデックスのキー列の順序が指定されている場合、列の値の前に見つからない列があると、スキャンが発生します。</span><span class="sxs-lookup"><span data-stu-id="d8388-191">Although, given the column order of the index key, a scan will occur if a value for a column comes after a missing column.</span></span>  
  
## <a name="index-count"></a><span data-ttu-id="d8388-192">インデックスの数</span><span class="sxs-lookup"><span data-stu-id="d8388-192">Index Count</span></span>  
 <span data-ttu-id="d8388-193">メモリ最適化テーブルには最大 8 個のインデックスを設定できます。これには、主キーで作成されるインデックスを含みます。</span><span class="sxs-lookup"><span data-stu-id="d8388-193">A memory-optimized table can have up to 8 indexes, including the index created with the primary key.</span></span>  
  
 <span data-ttu-id="d8388-194">メモリ最適化テーブルに作成されるインデックスの数については、次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="d8388-194">Regarding the number of indexes created on a memory-optimized table, consider the following:</span></span>  
  
-   <span data-ttu-id="d8388-195">テーブルの作成時に、必要なインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d8388-195">Specify the indexes you need when you create the table.</span></span> <span data-ttu-id="d8388-196">テーブルの作成後は、メモリ最適化テーブルのインデックスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="d8388-196">You cannot create an index for a memory-optimized table after the table is created.</span></span> <span data-ttu-id="d8388-197">メモリ最適化テーブルにインデックスを追加する場合は、そのテーブルを削除してから再作成します。</span><span class="sxs-lookup"><span data-stu-id="d8388-197">If you want to add an index to a memory-optimized table, drop and recreate that table.</span></span>  
  
-   <span data-ttu-id="d8388-198">ほとんど使用しないインデックスは作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="d8388-198">Do not create an index that you rarely use:</span></span>  
  
     <span data-ttu-id="d8388-199">ガベージ コレクションは、テーブルのすべてのインデックスを頻繁に使用する場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="d8388-199">Garbage collection works best if all indexes on the table are frequently used.</span></span> <span data-ttu-id="d8388-200">ほとんど使用しないインデックスがある場合、ガベージ コレクション システムは古い行バージョンに対して適切に機能しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d8388-200">Rarely-used indexes may cause the garbage collection system to not perform optimally for old row versions.</span></span>  
  
## <a name="creating-a-memory-optimized-index-code-samples"></a><span data-ttu-id="d8388-201">メモリ最適化インデックスの作成: コード サンプル</span><span class="sxs-lookup"><span data-stu-id="d8388-201">Creating a Memory-Optimized Index: Code Samples</span></span>  
 <span data-ttu-id="d8388-202">列レベルのハッシュ インデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-202">Column level hash index:</span></span>  
  
```sql  
CREATE TABLE t1   
   (c1 INT NOT NULL INDEX idx HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="d8388-203">テーブル レベルのハッシュ インデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-203">Table level hash index:</span></span>  
  
```sql  
CREATE TABLE t1_1   
   (c1 INT NOT NULL,   
   INDEX IDX HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="d8388-204">列レベルの主キーのハッシュ インデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-204">Column level primary key hash index:</span></span>  
  
```sql  
CREATE TABLE t2   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="d8388-205">テーブル レベルの主キーのハッシュ インデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-205">Table level primary key hash index:</span></span>  
  
```sql  
CREATE TABLE t2_2   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="d8388-206">列レベルの非クラスター化インデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-206">Column level nonclustered index:</span></span>  
  
```sql  
CREATE TABLE t3   
   (c1 INT NOT NULL INDEX ID)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="d8388-207">テーブル レベルの非クラスター化インデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-207">Table level nonclustered  index:</span></span>  
  
```sql  
CREATE TABLE t3_3   
   (c1 INT NOT NULL,   
   INDEX IDX NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="d8388-208">列レベルの主キー非クラスター化インデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-208">Column level primary key nonclustered  index:</span></span>  
  
```sql  
CREATE TABLE t4   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="d8388-209">テーブル レベルの主キー非クラスター化インデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-209">Table level primary key nonclustered index:</span></span>  
  
```sql  
CREATE TABLE t4_4   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="d8388-210">列を定義した後に定義される複数列のインデックス:</span><span class="sxs-lookup"><span data-stu-id="d8388-210">Multicolumn index defined after columns are defined:</span></span>  
  
```sql  
create table t (  
       a int not null constraint ta primary key nonclustered,  
       b int not null,  
       c int not null,  
       d int not null,  
       index idx_t_b_c_d nonclustered (b, c asc, d desc)  
) with (memory_optimized = on, durability = SCHEMA_AND_DATA)  
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8388-211">参照</span><span class="sxs-lookup"><span data-stu-id="d8388-211">See Also</span></span>  
 <span data-ttu-id="d8388-212">[メモリ最適化テーブルのインデックス](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="d8388-212">[Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="d8388-213">[ハッシュインデックスの適切なバケット数の決定](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="d8388-213">[Determining the Correct Bucket Count for Hash Indexes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) </span></span>  
 [<span data-ttu-id="d8388-214">ハッシュインデックス</span><span class="sxs-lookup"><span data-stu-id="d8388-214">Hash Indexes</span></span>](hash-indexes.md)  
  
  
