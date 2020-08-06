---
title: ハッシュインデックス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f4bdc9c1-7922-4fac-8183-d11ec58fec4e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8d1e3a5d92078cc2ec3fe7cd5b6d3fb5b47c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741229"
---
# <a name="hash-indexes"></a><span data-ttu-id="ad397-102">ハッシュ インデックス</span><span class="sxs-lookup"><span data-stu-id="ad397-102">Hash Indexes</span></span>
  <span data-ttu-id="ad397-103">インデックスは、メモリ最適化テーブルのエントリ ポイントとして使用します。</span><span class="sxs-lookup"><span data-stu-id="ad397-103">Indexes are used as entry points for memory-optimized tables.</span></span> <span data-ttu-id="ad397-104">テーブルから行を読み取るときには、データがメモリ上のどの場所にあるかを特定するためのインデックスが必要になります。</span><span class="sxs-lookup"><span data-stu-id="ad397-104">Reading rows from a table requires an index to locate the data in memory.</span></span>  
  
 <span data-ttu-id="ad397-105">ハッシュ インデックスは、配列の形に整理されたバケットのコレクションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="ad397-105">A hash index consists of a collection of buckets organized in an array.</span></span> <span data-ttu-id="ad397-106">ハッシュ関数は、ハッシュ インデックスの対応するバケットにインデックス キーをマッピングします。</span><span class="sxs-lookup"><span data-stu-id="ad397-106">A hash function maps index keys to corresponding buckets in the hash index.</span></span> <span data-ttu-id="ad397-107">次の図は、3 つのインデックス キーがそれぞれ、ハッシュ インデックスの異なる 3 つのバケットにマッピングされているようすを示したものです。</span><span class="sxs-lookup"><span data-stu-id="ad397-107">The following figure shows three index keys that are mapped to three different buckets in the hash index.</span></span> <span data-ttu-id="ad397-108">この図では、ハッシュ関数の名前を f(X) としています。</span><span class="sxs-lookup"><span data-stu-id="ad397-108">For illustration purposes the hash function name is f(x).</span></span>  
  
 <span data-ttu-id="ad397-109">![異なるバケットにマップされるインデックス キー。](../../2014/database-engine/media/hekaton-tables-2.gif "異なるバケットにマップされるインデックス キー。")</span><span class="sxs-lookup"><span data-stu-id="ad397-109">![Index keys mapped to different buckets.](../../2014/database-engine/media/hekaton-tables-2.gif "Index keys mapped to different buckets.")</span></span>  
  
 <span data-ttu-id="ad397-110">ハッシュ インデックスに使用するハッシュ関数には、以下の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="ad397-110">The hashing function used for hash indexes has the following characteristics:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ad397-111">には、あらゆるハッシュ インデックスに使用するハッシュ関数が 1 つ用意されています。</span><span class="sxs-lookup"><span data-stu-id="ad397-111">has one hash function that is used for all hash indexes.</span></span>  
  
-   <span data-ttu-id="ad397-112">ハッシュ関数は決定的です。</span><span class="sxs-lookup"><span data-stu-id="ad397-112">The hash function is deterministic.</span></span> <span data-ttu-id="ad397-113">インデックス キーが同じであれば、常にハッシュ インデックスの同じバケットにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="ad397-113">The same index key is always mapped to the same bucket in the hash index.</span></span>  
  
-   <span data-ttu-id="ad397-114">インデックス キーが違っても、同じハッシュ バケットにマッピングされることがあります。</span><span class="sxs-lookup"><span data-stu-id="ad397-114">Multiple index keys may be mapped to the same hash bucket.</span></span>  
  
-   <span data-ttu-id="ad397-115">ハッシュ関数はバランスが取られます。つまり、通常、ハッシュ バケット上のインデックス キー値の分布はポアソン分布に従います。</span><span class="sxs-lookup"><span data-stu-id="ad397-115">The hash function is balanced, meaning that the distribution of index key values over hash buckets typically follows a Poisson distribution.</span></span>  
  
     <span data-ttu-id="ad397-116">ポアソン分布は均等な分布ではありません。</span><span class="sxs-lookup"><span data-stu-id="ad397-116">Poisson distribution is not an even distribution.</span></span> <span data-ttu-id="ad397-117">インデックス キーの値は、ハッシュ バケットで均等に分散されません。</span><span class="sxs-lookup"><span data-stu-id="ad397-117">Index key values are not evenly distributed in the hash buckets.</span></span> <span data-ttu-id="ad397-118">たとえば *、n 個のハッシュバケット*に対する*n*個の一意のインデックスキーのポワソン分布では、3つ目の空のバケットが約1つ、1番目のバケットにはインデックスキーが1つ、残りの3番目に2つのインデックスキーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ad397-118">For example, a Poisson distribution of *n* distinct index keys over *n* hash buckets results in approximately one third empty buckets, one third of the buckets containing one index key, and the other third containing two index keys.</span></span> <span data-ttu-id="ad397-119">少数のバケットに、2 つ以上のキーが格納されます。</span><span class="sxs-lookup"><span data-stu-id="ad397-119">A small number of buckets will contain more than two keys.</span></span>  
  
 <span data-ttu-id="ad397-120">2 つのインデックス キーが同じハッシュ バケットにマッピングされた場合には、ハッシュの競合となります。</span><span class="sxs-lookup"><span data-stu-id="ad397-120">If two index keys are mapped to the same hash bucket, there is a hash collision.</span></span> <span data-ttu-id="ad397-121">ハッシュの競合が大量に発生した場合には、読み取り操作のパフォーマンスに影響を及ぼすおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="ad397-121">A large number of hash collisions can have a performance impact on read operations.</span></span>  
  
 <span data-ttu-id="ad397-122">インメモリ ハッシュ インデックス構造は、メモリ ポインターの配列で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ad397-122">The in-memory hash index structure consists of an array of memory pointers.</span></span> <span data-ttu-id="ad397-123">各バケットが、この配列のオフセットにマッピングされています。</span><span class="sxs-lookup"><span data-stu-id="ad397-123">Each bucket maps to an offset in this array.</span></span> <span data-ttu-id="ad397-124">配列のバケットはそれぞれ、そのハッシュ バケットの最初の行を参照しています。</span><span class="sxs-lookup"><span data-stu-id="ad397-124">Each bucket in the array points to the first row in that hash bucket.</span></span> <span data-ttu-id="ad397-125">バケットの行はそれぞれ次の行を参照しています。このため、次の図に示すように、各ハッシュ バケットの行が連なった構造になります。</span><span class="sxs-lookup"><span data-stu-id="ad397-125">Each row in the bucket points to the next row, thus resulting in a chain of rows for each hash bucket, as illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="ad397-126">![インメモリ ハッシュ インデックス構造体。](../../2014/database-engine/media/hekaton-tables-3.gif "インメモリ ハッシュ インデックス構造体。")</span><span class="sxs-lookup"><span data-stu-id="ad397-126">![The in-memory hash index structure.](../../2014/database-engine/media/hekaton-tables-3.gif "The in-memory hash index structure.")</span></span>  
  
 <span data-ttu-id="ad397-127">図では、行を備えたバケットが 3 つ示されています。</span><span class="sxs-lookup"><span data-stu-id="ad397-127">The figure has three buckets with rows.</span></span> <span data-ttu-id="ad397-128">上から 2 番目のバケットには、赤い行が 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="ad397-128">The second bucket from the top contains the three red rows.</span></span> <span data-ttu-id="ad397-129">4 番目のバケットには、青色の行が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="ad397-129">The fourth bucket contains the single blue row.</span></span> <span data-ttu-id="ad397-130">一番下のバケットには、緑色の行が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="ad397-130">The bottom bucket contains the two green rows.</span></span> <span data-ttu-id="ad397-131">ここに挙げた行はいずれも、同じ行が別のバージョンになったものである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ad397-131">These could be different versions of the same row.</span></span>  
  
 <span data-ttu-id="ad397-132">メモリ最適化テーブルのインデックスの詳細については、「[メモリ最適化テーブルでのインデックスの使用に関するガイドライン](../relational-databases/in-memory-oltp/memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad397-132">For more information about indexes for memory-optimized tables, see [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad397-133">参照</span><span class="sxs-lookup"><span data-stu-id="ad397-133">See Also</span></span>  
 [<span data-ttu-id="ad397-134">メモリ最適化テーブルのインデックス</span><span class="sxs-lookup"><span data-stu-id="ad397-134">Indexes on Memory-Optimized Tables</span></span>](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
