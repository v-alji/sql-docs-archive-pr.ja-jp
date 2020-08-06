---
title: メモリ最適化テーブルのメモリ必要量の推定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c5218a96d3650cbae22501ab2794b1b553996b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738394"
---
# <a name="estimate-memory-requirements-for-memory-optimized-tables"></a><span data-ttu-id="974ae-102">メモリ最適化テーブルのメモリ必要量の推定</span><span class="sxs-lookup"><span data-stu-id="974ae-102">Estimate Memory Requirements for Memory-Optimized Tables</span></span>
  <span data-ttu-id="974ae-103">新しいメモリ最適化テーブルを作成するか、 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 既存のディスクベーステーブルをメモリ最適化テーブルに移行するかにかかわらず、十分なメモリを使用してサーバーをプロビジョニングできるように、各テーブルのメモリニーズの妥当な推定値を確保することが重要です。</span><span class="sxs-lookup"><span data-stu-id="974ae-103">Whether you are creating a new [!INCLUDE[hek_2](../../includes/hek-2-md.md)] memory-optimized table or migrating an existing disk-based table to a memory-optimized table, it is important to have a reasonable estimate of each table's memory needs so you can provision the server with sufficient memory.</span></span> <span data-ttu-id="974ae-104">ここでは、メモリ最適化テーブルのデータを保持するために必要とされるメモリの量を推定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="974ae-104">This section describes how to estimate the amount of memory that you need to hold data for a memory-optimized table.</span></span>  
  
 <span data-ttu-id="974ae-105">ディスク ベース テーブルをメモリ最適化テーブルに移行することを検討している場合は、このトピックを読み進める前に、どのテーブルを移行するのが最善であるかを示す「 [テーブルまたはストアド プロシージャをインメモリ OLTP に移植する必要があるかどうかの確認](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) 」というトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="974ae-105">If you are contemplating migrating from disk-based tables to memory-optimized tables, before you proceed in this topic, see the topic [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) for guidance on which tables are best to migrate.</span></span> <span data-ttu-id="974ae-106">「 [インメモリ OLTP への移行](migrating-to-in-memory-oltp.md) 」に掲載されているすべてのトピックには、ディスク ベース テーブルからメモリ最適化テーブルへの移行に関するガイダンスが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="974ae-106">All the topics under [Migrating to In-Memory OLTP](migrating-to-in-memory-oltp.md) provide guidance on migrating from disk-based to memory-optimized tables.</span></span>  
  
## <a name="sections-in-this-topic"></a><span data-ttu-id="974ae-107">このトピックのセクション</span><span class="sxs-lookup"><span data-stu-id="974ae-107">Sections in this topic</span></span>  
  
-   [<span data-ttu-id="974ae-108">サンプルのメモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="974ae-108">Example memory-optimized table</span></span>](#bkmk_ExampleTable)  
  
-   [<span data-ttu-id="974ae-109">テーブルに対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-109">Memory for the table</span></span>](#bkmk_MemoryForTable)  
  
-   [<span data-ttu-id="974ae-110">インデックスに対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-110">Memory for indexes</span></span>](#bkmk_IndexMeemory)  
  
-   [<span data-ttu-id="974ae-111">行のバージョン管理に対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-111">Memory for row versioning</span></span>](#bkmk_MemoryForRowVersions)  
  
-   [<span data-ttu-id="974ae-112">テーブル変数に対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-112">Memory for table variables</span></span>](#bkmk_TableVariables)  
  
-   [<span data-ttu-id="974ae-113">成長に対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-113">Memory for growth</span></span>](#bkmk_MemoryForGrowth)  
  
##  <a name="example-memory-optimized-table"></a><a name="bkmk_ExampleTable"></a> <span data-ttu-id="974ae-114">サンプルのメモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="974ae-114">Example memory-optimized table</span></span>  
 <span data-ttu-id="974ae-115">次のメモリ最適化テーブルのスキーマを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="974ae-115">Consider the following memory-optimized table schema:</span></span>  
  
```sql  
  
CREATE TABLE t_hk (  
col1 int NOT NULL PRIMARY KEY NONCLUSTERED,  
col2 int NOT NULL INDEX t1c2_index   
     HASH WITH (bucket_count = 5000000),  
col3 int NOT NULL INDEX t1c3_index   
     HASH WITH (bucket_count = 5000000),  
col4 int NOT NULL INDEX t1c4_index   
     HASH WITH (bucket_count = 5000000),  
col5 int NOT NULL INDEX t1c5_index NONCLUSTERED,  
col6 char (50) NOT NULL,  
col7 char (50) NOT NULL,   
col8 char (30) NOT NULL,   
col9 char (50) NOT NULL  
     WITH (memory_optimized = on)  
GO  
  
```  
  
 <span data-ttu-id="974ae-116">このスキーマを使用して、このメモリ最適化テーブルで必要とされる最小メモリを決定します。</span><span class="sxs-lookup"><span data-stu-id="974ae-116">Using this schema we will determine the minimum memory needed for this memory-optimized table.</span></span>  
  
##  <a name="memory-for-the-table"></a><a name="bkmk_MemoryForTable"></a> <span data-ttu-id="974ae-117">テーブルに対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-117">Memory for the table</span></span>  
 <span data-ttu-id="974ae-118">メモリ最適化テーブルの行は、次の 3 つの部分から形成されています。</span><span class="sxs-lookup"><span data-stu-id="974ae-118">A memory-optimized table row is comprised of three parts:</span></span>  
  
-   <span data-ttu-id="974ae-119">**タイムスタンプ** </span><span class="sxs-lookup"><span data-stu-id="974ae-119">**Timestamps** </span></span>  
    <span data-ttu-id="974ae-120">行のヘッダー/タイムスタンプ = 24 バイトです。</span><span class="sxs-lookup"><span data-stu-id="974ae-120">Row header/timestamps = 24 bytes.</span></span>  
  
-   <span data-ttu-id="974ae-121">**インデックス ポインター** </span><span class="sxs-lookup"><span data-stu-id="974ae-121">**Index pointers** </span></span>  
    <span data-ttu-id="974ae-122">テーブル内の各ハッシュ インデックスにある各行には、インデックス内の次の行を指す 8 バイトのアドレス ポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="974ae-122">For each hash index in the table, each row has an 8-byte address pointer to the next row in the index.</span></span>  <span data-ttu-id="974ae-123">ここでは 4 つのインデックスが存在しているため、各行はインデックス ポインターに 32 バイト (インデックスごとに 8 バイトのポインター) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="974ae-123">Since there are 4 indexes, each row will allocate 32 bytes for index pointers (an 8 byte pointer for each index).</span></span>  
  
-   <span data-ttu-id="974ae-124">**データ** </span><span class="sxs-lookup"><span data-stu-id="974ae-124">**Data** </span></span>  
    <span data-ttu-id="974ae-125">行のデータ部分のサイズは、各データ列に対応する型サイズの合計によって決まります。</span><span class="sxs-lookup"><span data-stu-id="974ae-125">The size of the data portion of the row is determined by summing the type size for each data column.</span></span>  <span data-ttu-id="974ae-126">このテーブルには、4 バイトの整数が 5 個、50 バイトの文字列型の列が 3 個、30 バイトの文字列型の列が 1 個あります。</span><span class="sxs-lookup"><span data-stu-id="974ae-126">In our table we have five 4-byte integers, three 50-byte character columns, and one 30-byte character column.</span></span>  <span data-ttu-id="974ae-127">したがって、各行のデータ部分は、4 + 4 + 4 + 4 + 4 + 50 + 50 + 50 + 30、つまり 200 バイトです。</span><span class="sxs-lookup"><span data-stu-id="974ae-127">Therefore the data portion of each row is 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 or 200 bytes.</span></span>  
  
 <span data-ttu-id="974ae-128">以下は、メモリ最適化テーブル内に存在する 5,000,000 (500 万) 行のサイズの計算です。</span><span class="sxs-lookup"><span data-stu-id="974ae-128">The following is a size computation for 5,000,000 (5 million) rows in a memory-optimized table.</span></span> <span data-ttu-id="974ae-129">データ行で使用される合計メモリは、次のように推定されます。</span><span class="sxs-lookup"><span data-stu-id="974ae-129">The total memory used by data rows is estimated as follows:</span></span>  
  
 <span data-ttu-id="974ae-130">**テーブルの行に対応するメモリ**</span><span class="sxs-lookup"><span data-stu-id="974ae-130">**Memory for the table's rows**</span></span>  
  
 <span data-ttu-id="974ae-131">上記の計算結果から、メモリ最適化テーブル内にある各行のサイズは 24 + 32 + 200、つまり 256 バイトです。</span><span class="sxs-lookup"><span data-stu-id="974ae-131">From the above calculations, the size of each row in the memory-optimized table is 24 + 32 + 200, or 256 bytes.</span></span>  <span data-ttu-id="974ae-132">500 万の行があるため、テーブルは 5,000,000 \* 256 バイト、つまり 1,280,000,000 バイト、約 1.28 GB を使用します。</span><span class="sxs-lookup"><span data-stu-id="974ae-132">Since we have 5 million rows, the table will consume 5,000,000 \* 256 bytes, or 1,280,000,000 bytes - approximately 1.28 GB.</span></span>  
  
##  <a name="memory-for-indexes"></a><a name="bkmk_IndexMeemory"></a> <span data-ttu-id="974ae-133">インデックスに対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-133">Memory for indexes</span></span>  
 <span data-ttu-id="974ae-134">**各ハッシュ インデックスに対応するメモリ**</span><span class="sxs-lookup"><span data-stu-id="974ae-134">**Memory for each hash index**</span></span>  
  
 <span data-ttu-id="974ae-135">各ハッシュ インデックスは、8 バイトのアドレス ポインターから成るハッシュの配列です。</span><span class="sxs-lookup"><span data-stu-id="974ae-135">Each hash index is a hash array of 8-byte address pointers.</span></span>  <span data-ttu-id="974ae-136">配列のサイズは、そのインデックスの一意のインデックス値の数に基づいて適切に決定できます。たとえば、一意の Col2 の値の数を、t1c2_index の配列サイズを求めるための適切な出発点として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="974ae-136">The size of the array is best determined by the number of unique index values for that index - e.g., the number of unique Col2 values is a good starting point for the array size for the t1c2_index.</span></span> <span data-ttu-id="974ae-137">大きすぎるハッシュ配列は、メモリを浪費します。</span><span class="sxs-lookup"><span data-stu-id="974ae-137">A hash array that is too big wastes memory.</span></span>  <span data-ttu-id="974ae-138">小さすぎるハッシュ配列を使用する場合は、パフォーマンスが低下します。同じインデックスへとハッシュされるインデックス値が多くなり、非常に多くの競合が発生するためです。</span><span class="sxs-lookup"><span data-stu-id="974ae-138">A hash array that is too small slows performance since there will be too many collisions by index values that hash to the same index.</span></span>  
  
 <span data-ttu-id="974ae-139">ハッシュ インデックスは、次のように等値参照を実行する場合は非常に高速です。</span><span class="sxs-lookup"><span data-stu-id="974ae-139">Hash indexes achieve very fast equality lookups such as:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE Col2 = 3  
  
```  
  
 <span data-ttu-id="974ae-140">非クラスター化インデックスは、次のように範囲参照を実行する場合はより高速になります。</span><span class="sxs-lookup"><span data-stu-id="974ae-140">Nonclustered indexes are faster for range lookups such as:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE Col2 >= 3  
  
```  
  
 <span data-ttu-id="974ae-141">ディスク ベース テーブルを移行する場合は、t1c2_index インデックスに対応する一意の値の数を決定するために、次を使用できます。</span><span class="sxs-lookup"><span data-stu-id="974ae-141">If you are migrating a disk-based table you can use the following to determine the number of unique values for the index t1c2_index.</span></span>  
  
```sql  
  
SELECT COUNT(DISTINCT [Col2])  
  FROM t_hk  
  
```  
  
 <span data-ttu-id="974ae-142">新しいテーブルを作成する場合は、配列のサイズを推測するか、配置を実行する前にテストからデータを収集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-142">If you are creating a new table, you'll need to estimate the array size or gather data from your testing prior to deployment.</span></span>  
  
 <span data-ttu-id="974ae-143">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] メモリ最適化テーブル内でのハッシュ インデックスの動作方法の詳細については、「 [Hash Indexes](../../database-engine/hash-indexes.md)」(ハッシュ インデックス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974ae-143">For information on how hash indexes work in [!INCLUDE[hek_2](../../includes/hek-2-md.md)] memory-optimized tables, see [Hash Indexes](../../database-engine/hash-indexes.md).</span></span>  
  
 <span data-ttu-id="974ae-144">**注:** ハッシュインデックスの配列サイズを即座に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="974ae-144">**Note:** You cannot change the hash index array size on the fly.</span></span> <span data-ttu-id="974ae-145">ハッシュ インデックスの配列サイズを変更するには、テーブルを削除して bucket_count の値を変更し、そのテーブルを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-145">To change the hash index array size you must drop the table, change the bucket_count value and recreate the table.</span></span>  
  
 <span data-ttu-id="974ae-146">**ハッシュ インデックスの配列サイズの設定**</span><span class="sxs-lookup"><span data-stu-id="974ae-146">**Setting the hash index array size**</span></span>  
  
 <span data-ttu-id="974ae-147">ハッシュの配列サイズは `(bucket_count= <value>)` によって設定されます。ここで、 \<value> は、0 より大きい整数値です。</span><span class="sxs-lookup"><span data-stu-id="974ae-147">The hash array size is set by `(bucket_count= <value>)` where \<value> is an integer value greater than zero.</span></span> <span data-ttu-id="974ae-148">\<value> が 2 のべき乗でない場合は、実際の bucket_count は、最も近い 2 のべき乗になるように切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="974ae-148">If \<value> is not a power of 2, the actual bucket_count is rounded up to the next closest power of 2.</span></span>  <span data-ttu-id="974ae-149">この例のテーブル (bucket_count = 500万) では、500万は2のべき乗ではないため、実際のバケット数は 8388608 (2<sup>23</sup>) に切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="974ae-149">In our example table, (bucket_count = 5000000), since 5,000,000 is not a power of 2, the actual bucket count rounds up to 8,388,608 (2<sup>23</sup>).</span></span>  <span data-ttu-id="974ae-150">ハッシュ配列が必要とするメモリを計算するときは、5,000,000 ではなく、この数値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-150">You must use this number, not 5,000,000 when calculating memory needed by the hash array.</span></span>  
  
 <span data-ttu-id="974ae-151">したがって、この例の各ハッシュ配列で必要とされるメモリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="974ae-151">Thus, in our example, the memory needed for each hash array is:</span></span>  
  
 <span data-ttu-id="974ae-152">8388608 \* 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67108864 または約 64 MB。</span><span class="sxs-lookup"><span data-stu-id="974ae-152">8,388,608 \* 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67,108,864 or approximately 64 MB.</span></span>  
  
 <span data-ttu-id="974ae-153">3 つのハッシュ インデックスが存在するため、ハッシュ インデックスで必要とされるメモリは 3 \* 64MB = 192MB です。</span><span class="sxs-lookup"><span data-stu-id="974ae-153">Since we have three hash indexes, the memory needed for the hash indexes is 3 \* 64MB = 192MB.</span></span>  
  
 <span data-ttu-id="974ae-154">**非クラスター化インデックスに対応するメモリ**</span><span class="sxs-lookup"><span data-stu-id="974ae-154">**Memory for nonclustered indexes**</span></span>  
  
 <span data-ttu-id="974ae-155">非クラスター化インデックスは BTree として実装されており、内部ノードはインデックス値と、後続のノードを指すポインターを保持しています。</span><span class="sxs-lookup"><span data-stu-id="974ae-155">Nonclustered indexes are implemented as BTrees with the inner nodes containing the index value and pointers to subsequent nodes.</span></span>  <span data-ttu-id="974ae-156">リーフ ノードは、インデックス値と、メモリ内にあるテーブルの行を指すポインターを保持しています。</span><span class="sxs-lookup"><span data-stu-id="974ae-156">Leaf nodes contain the index value and a pointer to the table row in memory.</span></span>  
  
 <span data-ttu-id="974ae-157">ハッシュ インデックスとは異なり、非クラスター化インデックスには、固定的なバケット サイズがありません。</span><span class="sxs-lookup"><span data-stu-id="974ae-157">Unlike hash indexes, nonclustered indexes do not have a fixed bucket size.</span></span> <span data-ttu-id="974ae-158">インデックスは、データと共に動的に拡張または圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="974ae-158">The index grows and shrinks dynamically with the data.</span></span>  
  
 <span data-ttu-id="974ae-159">非クラスター化インデックスのメモリ必要量は、次のように計算することができます。</span><span class="sxs-lookup"><span data-stu-id="974ae-159">Memory needed by nonclustered indexes can be computed as follows:</span></span>  
  
-   <span data-ttu-id="974ae-160">**非リーフ ノードに割り当てられるメモリ** </span><span class="sxs-lookup"><span data-stu-id="974ae-160">**Memory allocated to non-leaf nodes** </span></span>  
    <span data-ttu-id="974ae-161">標準的な構成では、非リーフ ノードに割り当てられるメモリが、インデックスによって取得されるメモリ全体に占める割合は非常に小さいものです。</span><span class="sxs-lookup"><span data-stu-id="974ae-161">For a typical configuration, the memory allocated to non-leaf nodes is a small percentage of the overall memory taken by the index.</span></span> <span data-ttu-id="974ae-162">これは非常に小さい割合であり、無視しても安全です。</span><span class="sxs-lookup"><span data-stu-id="974ae-162">This is so small it can safely be ignored.</span></span>  
  
-   <span data-ttu-id="974ae-163">**リーフ ノードに割り当てられるメモリ** </span><span class="sxs-lookup"><span data-stu-id="974ae-163">**Memory for leaf nodes** </span></span>  
    <span data-ttu-id="974ae-164">リーフ ノードにはテーブル内に存在する一意のキーごとに 1 行のデータがあり、リーフ ノードは、その一意のキーを持つデータ行を指します。</span><span class="sxs-lookup"><span data-stu-id="974ae-164">The leaf nodes have one row for each unique key in the table that points to the data rows with that unique key.</span></span>  <span data-ttu-id="974ae-165">同じキーを持つ複数の行が存在する (つまり、一意ではない非クラスター化インデックスを使用している) 場合は、インデックスのリーフ ノード内にはただ 1 つの行があり、リーフ ノードは 1 つの行を指しており、各行は互いにリンクされています。</span><span class="sxs-lookup"><span data-stu-id="974ae-165">If you have multiple rows with the same key (i.e., you have a non-unique nonclustered index), there is only one row in the index leaf node that points to one of the rows with the other rows linked to each other.</span></span>  <span data-ttu-id="974ae-166">したがって、必要とされるメモリ全体は、次のように近似できます。</span><span class="sxs-lookup"><span data-stu-id="974ae-166">Thus, the total memory required can be approximated by:</span></span>   
    <span data-ttu-id="974ae-167">memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) \* rowsWithUniqueKeys</span><span class="sxs-lookup"><span data-stu-id="974ae-167">memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) \* rowsWithUniqueKeys</span></span>  
  
 <span data-ttu-id="974ae-168">非クラスター化インデックスは、次のクエリで例示する範囲参照の場合に使用するのが最適です。</span><span class="sxs-lookup"><span data-stu-id="974ae-168">Nonclustered indexes are best when used for range lookups, as exemplified by the following query:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE c2 > 5  
```  
  
##  <a name="memory-for-row-versioning"></a><a name="bkmk_MemoryForRowVersions"></a> <span data-ttu-id="974ae-169">行のバージョン管理に対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-169">Memory for row versioning</span></span>  
 <span data-ttu-id="974ae-170">ロックを回避するために、インメモリ OLTP は行を更新または削除するときに、オプティミスティック コンカレンシーを使用します。</span><span class="sxs-lookup"><span data-stu-id="974ae-170">To avoid locks, In-Memory OLTP uses optimistic concurrency when updating or deleting rows.</span></span> <span data-ttu-id="974ae-171">これは、行を更新するときに、行の追加バージョンが作成されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="974ae-171">This means that when a row is updated, an additional version of the row is created.</span></span> <span data-ttu-id="974ae-172">以前のバージョンを使用する可能性のあるすべてのトランザクションが実行を完了するまでは、システムは以前のバージョンを使用可能な状態に保ちます。</span><span class="sxs-lookup"><span data-stu-id="974ae-172">The system keeps the previous versions available until all transactions that could possibly use the version have finished execution.</span></span> <span data-ttu-id="974ae-173">行を削除する場合も、システムは更新の場合に似た方法で動作し、以前のバージョンが不要になるまでは、以前のバージョンを使用可能な状態に保ちます。</span><span class="sxs-lookup"><span data-stu-id="974ae-173">When a row is deleted, the system acts in a similar way to an update, keeping the version available until it is no longer necessary.</span></span> <span data-ttu-id="974ae-174">読み取りと挿入を実行する場合は、行の追加バージョンは作成されません。</span><span class="sxs-lookup"><span data-stu-id="974ae-174">Reads and inserts do not create additional row versions.</span></span>  
  
 <span data-ttu-id="974ae-175">メモリ内にはいつでも多数の追加行が存在している可能性があり、それらの行は自らのメモリを解放するガベージ コレクション サイクルを待機しているため、これらの追加の行を収容するために十分なメモリを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-175">Because there may be a number of additional rows in memory at any time waiting for the garbage collection cycle to release their memory, you must have sufficient memory to accommodate these additional rows.</span></span>  
  
 <span data-ttu-id="974ae-176">追加の行の数を推定するには、1 秒あたりの行の更新と削除に関するピークの数値を求め、その値に、最も長いトランザクションが要する秒数 (最小値は 1) を掛けます。</span><span class="sxs-lookup"><span data-stu-id="974ae-176">The number of additional rows can be estimated by computing the peak number of row updates and deletions per second, then multiplying that by the number of seconds the longest transaction takes (minimum of 1).</span></span>  
  
 <span data-ttu-id="974ae-177">この積に、行サイズを掛けると、行のバージョン管理に必要とされるバイト数を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="974ae-177">That value is then multiplied by the row size to get the number of bytes you need for row versioning.</span></span>  
  
 `rowVersions = durationOfLongestTransactionInSeconds * peakNumberOfRowUpdatesOrDeletesPerSecond`  
  
 <span data-ttu-id="974ae-178">古い行のメモリ必要量を推定するには、古い行の数に、メモリ最適化テーブルの行のサイズを掛けます (上記[の表の「メモリ](#bkmk_MemoryForTable)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="974ae-178">Memory needs for stale rows is then estimated by multiplying the number of stale rows by the size of a memory-optimized table row (see [Memory for the table](#bkmk_MemoryForTable) above).</span></span>  
  
 `memoryForRowVersions = rowVersions * rowSize`  
  
##  <a name="memory-for-table-variables"></a><a name="bkmk_TableVariables"></a> <span data-ttu-id="974ae-179">テーブル変数に対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-179">Memory for table variables</span></span>  
 <span data-ttu-id="974ae-180">テーブル変数に対応するメモリは、テーブル変数がスコープ外になる場合にのみ解放されます。</span><span class="sxs-lookup"><span data-stu-id="974ae-180">Memory used for a table variable is released only when the table variable goes out of scope.</span></span> <span data-ttu-id="974ae-181">テーブル変数から削除された行 (更新の一部として削除された行を含む) には、ガベージ コレクションは適用されません。</span><span class="sxs-lookup"><span data-stu-id="974ae-181">Deleted rows, including rows deleted as part of an update, from a table variable are not subject to garbage collection.</span></span> <span data-ttu-id="974ae-182">テーブル変数がスコープを終了するまでメモリは解放されません。</span><span class="sxs-lookup"><span data-stu-id="974ae-182">No memory is released until the table variable exits scope.</span></span>  
  
 <span data-ttu-id="974ae-183">プロシージャ スコープとは対照的に、多くのトランザクションで使用される大きな SQL バッチで定義されるテーブル変数は、多くのメモリを消費することがあります。</span><span class="sxs-lookup"><span data-stu-id="974ae-183">Table variables defined in a large SQL batch, as opposed to a procedure scope, which are used in many transactions, can consume a lot of memory.</span></span> <span data-ttu-id="974ae-184">ガベージ コレクションの対象ではないため、テーブル変数内にある削除された行は多くのメモリを使用し、パフォーマンスが低下することがあります。読み取り操作では、削除されたこれらの行をスキャンで通過させる必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="974ae-184">Because they are not garbage collected, deleted rows in a table variable can consume a lot memory and degrade performance since read operations need to scan past the deleted rows.</span></span>  
  
##  <a name="memory-for-growth"></a><a name="bkmk_MemoryForGrowth"></a> <span data-ttu-id="974ae-185">成長に対応するメモリ</span><span class="sxs-lookup"><span data-stu-id="974ae-185">Memory for growth</span></span>  
 <span data-ttu-id="974ae-186">上記の各計算では、現在存在しているテーブルに対応するメモリ必要量を推定しています。</span><span class="sxs-lookup"><span data-stu-id="974ae-186">The above calculations estimate your memory needs for the table as it currently exists.</span></span> <span data-ttu-id="974ae-187">このメモリに加えて、テーブルが成長することを推定し、その成長を収容するために十分なメモリを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-187">In addition to this memory, you need to estimate the growth of the table and provide sufficient memory to accommodate that growth.</span></span>  <span data-ttu-id="974ae-188">たとえば、10% の成長を予測している場合は、上記の結果に 1.1 を掛けて、テーブルで必要とされる合計メモリを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="974ae-188">For example, if you anticipate 10% growth then you need to multiple the results from above by 1.1 to get the total memory needed for your table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974ae-189">参照</span><span class="sxs-lookup"><span data-stu-id="974ae-189">See Also</span></span>  
 [<span data-ttu-id="974ae-190">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="974ae-190">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
