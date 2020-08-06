---
title: メモリ最適化テーブルのテーブルと行のサイズ | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b0a248a4-4488-4cc8-89fc-46906a8c24a1
author: rothja
ms.author: jroth
ms.openlocfilehash: 74cc40b7d1f2d0132d79d1e9ae15c2321ac9b74a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742049"
---
# <a name="table-and-row-size-in-memory-optimized-tables"></a><span data-ttu-id="c5868-102">メモリ最適化テーブルのテーブルと行のサイズ</span><span class="sxs-lookup"><span data-stu-id="c5868-102">Table and Row Size in Memory-Optimized Tables</span></span>
  <span data-ttu-id="c5868-103">メモリ最適化テーブルは、行のコレクションと、行へのポインターを格納するインデックスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c5868-103">A memory-optimized table consists of a collection of rows and indexes that contain pointers to rows.</span></span> <span data-ttu-id="c5868-104">メモリ最適化テーブルでは、行を 8,060 バイトより長くすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c5868-104">In a memory-optimized table, rows cannot be longer than 8,060 bytes.</span></span> <span data-ttu-id="c5868-105">メモリ最適化テーブルのサイズを知ることで、コンピューターに十分なメモリがあるかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="c5868-105">Understanding the size of a memory-optimized table will help you understand if your computer has enough memory.</span></span>  
  
 <span data-ttu-id="c5868-106">テーブルと行のサイズを計算する理由は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="c5868-106">There are two reasons for computing table and row size:</span></span>  
  
-   <span data-ttu-id="c5868-107">テーブルが使用するメモリの量</span><span class="sxs-lookup"><span data-stu-id="c5868-107">How much memory does a table use?</span></span>  
  
    -   <span data-ttu-id="c5868-108">テーブルで使用されるメモリの量は、正確に計算することはできません。</span><span class="sxs-lookup"><span data-stu-id="c5868-108">The amount of memory used by the table cannot be calculated exactly.</span></span> <span data-ttu-id="c5868-109">使用されるメモリの量には、多くの要因が影響します。</span><span class="sxs-lookup"><span data-stu-id="c5868-109">Many factors affect the amount of memory used.</span></span> <span data-ttu-id="c5868-110">たとえば、ページ単位のメモリ割り当て、局所性、キャッシュ、余白などの要因です。</span><span class="sxs-lookup"><span data-stu-id="c5868-110">Factors such as page-based memory allocation, locality, caching, and padding.</span></span> <span data-ttu-id="c5868-111">また、アクティブなトランザクションが関連付けられている行や、ガベージ コレクションを待機している行には複数のバージョンが存在します。</span><span class="sxs-lookup"><span data-stu-id="c5868-111">Also, multiple versions of rows that either have active transactions associated or that are waiting for garbage collection.</span></span>  
  
    -   <span data-ttu-id="c5868-112">テーブル内のデータとインデックスに必要な最小サイズは、後で説明する [テーブル サイズ] (table size) の計算によって得られます。</span><span class="sxs-lookup"><span data-stu-id="c5868-112">The minimum size required for the data and indexes in the table is given by the calculation for [table size], discussed below.</span></span>  
  
    -   <span data-ttu-id="c5868-113">メモリ使用量の計算で得られる値は、最善でも近似値です。配置プランにキャパシティ プランニングを含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c5868-113">Calculating memory use is at best an approximation and you are advised to include capacity planning in your deployment plans.</span></span>  
  
-   <span data-ttu-id="c5868-114">行のデータ サイズと、そのデータ サイズが行サイズの上限である 8,060 バイト以下であるかどうか。</span><span class="sxs-lookup"><span data-stu-id="c5868-114">The data size of a row, and does it fit in the 8,060 byte row size limitation?</span></span> <span data-ttu-id="c5868-115">これを調べるには、以降に説明する行本文サイズ (row body size) の計算を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5868-115">To answer these questions, use the computation for [row body size], discussed below.</span></span>  
  
 <span data-ttu-id="c5868-116">次の図は、インデックスと行を含むテーブルを示しています。行には行ヘッダーと行本文が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5868-116">The following figure illustrates a table with indexes and rows, which in turn have row headers and bodies:</span></span>  
  
 <span data-ttu-id="c5868-117">![メモリ最適化テーブル。](../../database-engine/media/hekaton-guide-1.gif "メモリ最適化テーブル")</span><span class="sxs-lookup"><span data-stu-id="c5868-117">![Memory optimized table.](../../database-engine/media/hekaton-guide-1.gif "Memory optimized table.")</span></span>  
<span data-ttu-id="c5868-118">インデックスと行で構成されたメモリ最適化テーブル。</span><span class="sxs-lookup"><span data-stu-id="c5868-118">Memory-optimized table, consisting of indexes and rows.</span></span>  
  
 <span data-ttu-id="c5868-119">テーブルのメモリ内サイズ (バイト単位) は、次のように計算されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-119">The in-memory size of a table, in bytes, is computed as follows:</span></span>  
  
```  
[table size] = [size of index 1] + ... + [size of index n] + ([row size] * [row count])  
```  
  
 <span data-ttu-id="c5868-120">ハッシュ インデックスのサイズはテーブルの作成時に固定され、実際のバケット数によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c5868-120">The size of a hash index is fixed at table creation time and depends on the actual bucket count.</span></span> <span data-ttu-id="c5868-121">インデックスの仕様で指定された bucket_count は、[実際のバケット数] (actual bucket count) を取得するために、最も近い 2 のべき乗の値に切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="c5868-121">The bucket_count specified with the index specification is rounded up to the nearest power of 2 to obtain the [actual bucket count].</span></span> <span data-ttu-id="c5868-122">たとえば、指定された bucket_count が 100,000 の場合、インデックスの [実際のバケット数] (actual bucket count) は 131,072 になります。</span><span class="sxs-lookup"><span data-stu-id="c5868-122">For example, if the specified bucket_count is 100000, the [actual bucket count] for the index is 131072.</span></span>  
  
```  
[hash index size] = 8 * [actual bucket count]  
```  
  
 <span data-ttu-id="c5868-123">行サイズは、ヘッダーと本文のサイズを合計して算出されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-123">The row size is computed by adding the header and the body:</span></span>  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices]  
```  
  
 <span data-ttu-id="c5868-124">**行本文サイズ**</span><span class="sxs-lookup"><span data-stu-id="c5868-124">**Row body size**</span></span>  
  
 <span data-ttu-id="c5868-125">行本文サイズ (row body size) の計算について、次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="c5868-125">The calculation of [row body size] is discussed in the following table.</span></span>  
  
 <span data-ttu-id="c5868-126">行本文サイズには、計算されたサイズと実際のサイズという 2 種類の計算があります。</span><span class="sxs-lookup"><span data-stu-id="c5868-126">There are two different computations for row body size: computed size and the actual size:</span></span>  
  
-   <span data-ttu-id="c5868-127">[計算された行本文サイズ] (computed row body size) で示される計算されたサイズは、8,060 バイトという行サイズの上限値を超えるかどうかを判断するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-127">The computed size, denoted with [computed row body size], is used to determine if the row size limitation of 8,060 bytes is exceeded.</span></span>  
  
-   <span data-ttu-id="c5868-128">[実際の行本文サイズ] (actual row body size) で示される実際のサイズは、メモリ内およびチェックポイント ファイル内の行本文の実際の格納サイズです。</span><span class="sxs-lookup"><span data-stu-id="c5868-128">The actual size, denoted with [actual row body size], is the actual storage size of the row body in memory and in the checkpoint files.</span></span>  
  
 <span data-ttu-id="c5868-129">[計算された行本文サイズ] (computed row body size) と [実際の行本文サイズ] (actual row body size) はほぼ同じ方法で計算されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-129">Both [computed row body size] and [actual row body size] are calculated similarly.</span></span> <span data-ttu-id="c5868-130">次の表の最後に説明されているとおり、唯一の違いは、(n)varchar(i) 列と varbinary(i) 列のサイズの計算です。</span><span class="sxs-lookup"><span data-stu-id="c5868-130">The only difference is the calculation of the size of (n)varchar(i) and varbinary(i) columns, as reflected at the bottom of the following table.</span></span> <span data-ttu-id="c5868-131">計算された行本体サイズでは、宣言されたサイズ *i* を列のサイズとして使用しますが、実際の行本体サイズではデータの実際のサイズを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5868-131">The computed row body size uses the declared size *i* as the size of the column, while the actual row body size uses the actual size of the data.</span></span>  
  
 <span data-ttu-id="c5868-132">[実際の行本文サイズ] = SUM([シャロー型のサイズ]) + 2 + 2 \* [ディープ型の列の数] として指定した場合、行本文サイズの計算について、次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="c5868-132">The following table describes the calculation of the row body size, given as [actual row body size] = SUM([size of shallow types]) + 2 + 2 \* [number of deep type columns].</span></span>  
  
|<span data-ttu-id="c5868-133">Section</span><span class="sxs-lookup"><span data-stu-id="c5868-133">Section</span></span>|<span data-ttu-id="c5868-134">サイズ</span><span class="sxs-lookup"><span data-stu-id="c5868-134">Size</span></span>|<span data-ttu-id="c5868-135">説明</span><span class="sxs-lookup"><span data-stu-id="c5868-135">Comments</span></span>|  
|-------------|----------|--------------|  
|<span data-ttu-id="c5868-136">シャロー型の列</span><span class="sxs-lookup"><span data-stu-id="c5868-136">Shallow type columns</span></span>|<span data-ttu-id="c5868-137">SUM([シャロー型のサイズ] (size of shallow types))</span><span class="sxs-lookup"><span data-stu-id="c5868-137">SUM([size of shallow types])</span></span><br /><br /> <span data-ttu-id="c5868-138">**個々の型のサイズは次のとおりです。**</span><span class="sxs-lookup"><span data-stu-id="c5868-138">**Size of the individual types is as follows:**</span></span><br /><br /> <span data-ttu-id="c5868-139">Bit &#124; 1</span><span class="sxs-lookup"><span data-stu-id="c5868-139">Bit &#124; 1</span></span><br /><br /> <span data-ttu-id="c5868-140">Tinyint &#124; 1</span><span class="sxs-lookup"><span data-stu-id="c5868-140">Tinyint &#124; 1</span></span><br /><br /> <span data-ttu-id="c5868-141">Smallint &#124; 2</span><span class="sxs-lookup"><span data-stu-id="c5868-141">Smallint &#124; 2</span></span><br /><br /> <span data-ttu-id="c5868-142">Int &#124; 4</span><span class="sxs-lookup"><span data-stu-id="c5868-142">Int &#124; 4</span></span><br /><br /> <span data-ttu-id="c5868-143">Real &#124; 4</span><span class="sxs-lookup"><span data-stu-id="c5868-143">Real &#124; 4</span></span><br /><br /> <span data-ttu-id="c5868-144">Smalldatetime &#124; 4</span><span class="sxs-lookup"><span data-stu-id="c5868-144">Smalldatetime &#124; 4</span></span><br /><br /> <span data-ttu-id="c5868-145">Smallmoney &#124; 4</span><span class="sxs-lookup"><span data-stu-id="c5868-145">Smallmoney &#124; 4</span></span><br /><br /> <span data-ttu-id="c5868-146">Bigint &#124; 8</span><span class="sxs-lookup"><span data-stu-id="c5868-146">Bigint &#124; 8</span></span><br /><br /> <span data-ttu-id="c5868-147">Datetime &#124; 8</span><span class="sxs-lookup"><span data-stu-id="c5868-147">Datetime &#124; 8</span></span><br /><br /> <span data-ttu-id="c5868-148">Datetime2 &#124; 8</span><span class="sxs-lookup"><span data-stu-id="c5868-148">Datetime2 &#124; 8</span></span><br /><br /> <span data-ttu-id="c5868-149">Float 8</span><span class="sxs-lookup"><span data-stu-id="c5868-149">Float 8</span></span><br /><br /> <span data-ttu-id="c5868-150">Money 8</span><span class="sxs-lookup"><span data-stu-id="c5868-150">Money 8</span></span><br /><br /> <span data-ttu-id="c5868-151">Numeric (precision <= 18) &#124; 8</span><span class="sxs-lookup"><span data-stu-id="c5868-151">Numeric (precision <=18) &#124; 8</span></span><br /><br /> <span data-ttu-id="c5868-152">Time &#124; 8</span><span class="sxs-lookup"><span data-stu-id="c5868-152">Time &#124; 8</span></span><br /><br /> <span data-ttu-id="c5868-153">数値 (有効桁数>18) &#124; 16</span><span class="sxs-lookup"><span data-stu-id="c5868-153">Numeric(precision>18) &#124; 16</span></span><br /><br /> <span data-ttu-id="c5868-154">Uniqueidentifier &#124; 16</span><span class="sxs-lookup"><span data-stu-id="c5868-154">Uniqueidentifier &#124; 16</span></span>||  
|<span data-ttu-id="c5868-155">シャロー列の余白</span><span class="sxs-lookup"><span data-stu-id="c5868-155">Shallow column padding</span></span>|<span data-ttu-id="c5868-156">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="c5868-156">Possible values are:</span></span><br /><br /> <span data-ttu-id="c5868-157">ディープ型の列が存在し、シャロー列の合計データ サイズが奇数になる場合は 1。</span><span class="sxs-lookup"><span data-stu-id="c5868-157">1 if there are deep type columns and the total data size of the shallow columns is as odd number.</span></span><br /><br /> <span data-ttu-id="c5868-158">それ以外の場合は、0。</span><span class="sxs-lookup"><span data-stu-id="c5868-158">0 otherwise</span></span>|<span data-ttu-id="c5868-159">ディープ型は、(var)binary 型と (n)(var)char 型です。</span><span class="sxs-lookup"><span data-stu-id="c5868-159">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="c5868-160">ディープ型の列のオフセット配列</span><span class="sxs-lookup"><span data-stu-id="c5868-160">Offset array for deep type columns</span></span>|<span data-ttu-id="c5868-161">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="c5868-161">Possible values are:</span></span><br /><br /> <span data-ttu-id="c5868-162">ディープ型の列がない場合は 0</span><span class="sxs-lookup"><span data-stu-id="c5868-162">0 if there are no deep type columns</span></span><br /><br /> <span data-ttu-id="c5868-163">それ以外の場合は 2 + 2 \* [ディープ型の列の数] (number of deep type columns)</span><span class="sxs-lookup"><span data-stu-id="c5868-163">2 + 2 \* [number of deep type columns] otherwise</span></span>|<span data-ttu-id="c5868-164">ディープ型は、(var)binary 型と (n)(var)char 型です。</span><span class="sxs-lookup"><span data-stu-id="c5868-164">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="c5868-165">NULL 配列</span><span class="sxs-lookup"><span data-stu-id="c5868-165">NULL array</span></span>|<span data-ttu-id="c5868-166">[NULL 値を許容する列の数] / 8 (完全なバイト数になるように切り上げ)。</span><span class="sxs-lookup"><span data-stu-id="c5868-166">[number of nullable columns] / 8, rounded up to full bytes.</span></span>|<span data-ttu-id="c5868-167">配列は、NULL 値を許容する列ごとに 1 ビットを保持します。</span><span class="sxs-lookup"><span data-stu-id="c5868-167">The array has one bit per nullable column.</span></span> <span data-ttu-id="c5868-168">これは、完全なバイト数になるように切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="c5868-168">This is rounded up to full bytes.</span></span>|  
|<span data-ttu-id="c5868-169">NULL 配列の余白</span><span class="sxs-lookup"><span data-stu-id="c5868-169">NULL array padding</span></span>|<span data-ttu-id="c5868-170">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="c5868-170">Possible values are:</span></span><br /><br /> <span data-ttu-id="c5868-171">ディープ型の列が存在し、NULL 配列のサイズのバイト数が奇数である場合は 1。</span><span class="sxs-lookup"><span data-stu-id="c5868-171">1 if there are deep type columns and the size of the NULL array is an odd number of bytes.</span></span><br /><br /> <span data-ttu-id="c5868-172">それ以外の場合は、0。</span><span class="sxs-lookup"><span data-stu-id="c5868-172">0 otherwise</span></span>|<span data-ttu-id="c5868-173">ディープ型は、(var)binary 型と (n)(var)char 型です。</span><span class="sxs-lookup"><span data-stu-id="c5868-173">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="c5868-174">パディング</span><span class="sxs-lookup"><span data-stu-id="c5868-174">Padding</span></span>|<span data-ttu-id="c5868-175">ディープ型の列がない場合は: 0</span><span class="sxs-lookup"><span data-stu-id="c5868-175">If there are no deep type columns: 0</span></span><br /><br /> <span data-ttu-id="c5868-176">ディープ型の列がある場合、シャロー列に必要な最大の配置に基づいて、余白の 0 ～ 7 バイトが追加されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-176">If there are deep type columns, 0-7 bytes of padding is added, based on the largest alignment required by a shallow column.</span></span> <span data-ttu-id="c5868-177">前に説明したように、各シャロー列の配置は、列のサイズと等しい値にする必要があります。ただし、例外として、GUID 列の配置は 1 バイト (16 ではない) とし、数値列の配置は常に 8 バイト (16 ではない) とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5868-177">Each shallow column requires alignment equal to its size as documented above, except that GUID columns need alignment of 1 byte (not 16) and numeric columns always need alignment of 8 bytes (never 16).</span></span> <span data-ttu-id="c5868-178">すべてのシャロー列間で必要となる配置の値の中で、最も大きな値が使用されます。それまでの合計サイズ (ディープ型の列を含まない) が必要な配置の倍数になるように、余白として 0 ～ 7 バイトが追加されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-178">The largest alignment requirement among all shallow columns is used, and 0-7 bytes of padding is added in such a way that the total size so far (without the deep type columns) is a multiple of the required alignment.</span></span>|<span data-ttu-id="c5868-179">ディープ型は、(var)binary 型と (n)(var)char 型です。</span><span class="sxs-lookup"><span data-stu-id="c5868-179">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="c5868-180">固定長のディープ型の列</span><span class="sxs-lookup"><span data-stu-id="c5868-180">Fixed-length deep type columns</span></span>|<span data-ttu-id="c5868-181">SUM([固定長のディープ型の列のサイズ])</span><span class="sxs-lookup"><span data-stu-id="c5868-181">SUM([size of fixed length deep type columns])</span></span><br /><br /> <span data-ttu-id="c5868-182">個々の列のサイズは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c5868-182">The size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="c5868-183">char(i) および binary(i) の場合は i。</span><span class="sxs-lookup"><span data-stu-id="c5868-183">i for char(i) and binary(i).</span></span><br /><br /> <span data-ttu-id="c5868-184">nchar(i) の場合は 2 \* i。</span><span class="sxs-lookup"><span data-stu-id="c5868-184">2 \* i for nchar(i)</span></span>|<span data-ttu-id="c5868-185">固定長のディープ型の列では、列の型が char(i)、nchar(i)、または binary(i) です。</span><span class="sxs-lookup"><span data-stu-id="c5868-185">Fixed-length deep type columns are columns of type char(i), nchar(i), or binary(i).</span></span>|  
|<span data-ttu-id="c5868-186">可変長のディープ型の列の [計算されたサイズ]</span><span class="sxs-lookup"><span data-stu-id="c5868-186">Variable length deep type columns [computed size]</span></span>|<span data-ttu-id="c5868-187">SUM([可変長のディープ型の列の計算されたサイズ])</span><span class="sxs-lookup"><span data-stu-id="c5868-187">SUM([computed size of variable length deep type columns])</span></span><br /><br /> <span data-ttu-id="c5868-188">個々の列の計算されたサイズは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c5868-188">The computed size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="c5868-189">varchar(i) および varbinary(i) の場合は i。</span><span class="sxs-lookup"><span data-stu-id="c5868-189">i for varchar(i) and varbinary(i)</span></span><br /><br /> <span data-ttu-id="c5868-190">nvarchar(i) の場合は 2 \* i。</span><span class="sxs-lookup"><span data-stu-id="c5868-190">2 \* i for nvarchar(i)</span></span>|<span data-ttu-id="c5868-191">この行は、[計算された行本文サイズ] (computed row body size) にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-191">This row only applied to [computed row body size].</span></span><br /><br /> <span data-ttu-id="c5868-192">可変長のディープ型の列では、列の型が varchar(i)、nvarchar(i)、または varbinary(i) です。</span><span class="sxs-lookup"><span data-stu-id="c5868-192">Variable-length deep type columns are columns of type varchar(i), nvarchar(i), or varbinary(i).</span></span> <span data-ttu-id="c5868-193">計算されたサイズは、列の最大長 (i) で決まります。</span><span class="sxs-lookup"><span data-stu-id="c5868-193">The computed size is determined by the max length (i) of the column.</span></span>|  
|<span data-ttu-id="c5868-194">可変長のディープ型の列の [実際のサイズ]</span><span class="sxs-lookup"><span data-stu-id="c5868-194">Variable length deep type columns [actual size]</span></span>|<span data-ttu-id="c5868-195">SUM([可変長のディープ型の列の実際のサイズ])</span><span class="sxs-lookup"><span data-stu-id="c5868-195">SUM([actual size of variable length deep type columns])</span></span><br /><br /> <span data-ttu-id="c5868-196">個々の列の実際のサイズは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c5868-196">The actual size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="c5868-197">varchar(i) の場合は n (ここで n は列に格納されている文字数)。</span><span class="sxs-lookup"><span data-stu-id="c5868-197">n, where n is the number of characters stored in the column, for varchar(i).</span></span><br /><br /> <span data-ttu-id="c5868-198">nvarchar(i) の場合は 2 \* n (ここで n は列に格納されている文字数)。</span><span class="sxs-lookup"><span data-stu-id="c5868-198">2 \* n, where n is the number of characters stored in the column, for nvarchar(i).</span></span><br /><br /> <span data-ttu-id="c5868-199">varbinary(i) の場合は n (ここで n は列に格納されているバイト数)。</span><span class="sxs-lookup"><span data-stu-id="c5868-199">n, where n is the number of bytes stored in the column, for varbinary(i).</span></span>|<span data-ttu-id="c5868-200">この行は、[実際の行本文サイズ] (actual row body size) にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-200">This row only applied to [actual row body size].</span></span><br /><br /> <span data-ttu-id="c5868-201">実際のサイズは、行の列内に格納されているデータで決まります。</span><span class="sxs-lookup"><span data-stu-id="c5868-201">The actual size is determined by the data stored in the columns in the row.</span></span>|  
  
##  <a name="row-structure"></a><a name="bkmk_RowStructure"></a> <span data-ttu-id="c5868-202">行構造</span><span class="sxs-lookup"><span data-stu-id="c5868-202">Row Structure</span></span>  
 <span data-ttu-id="c5868-203">メモリ最適化テーブルの行は、次のコンポーネントを備えています。</span><span class="sxs-lookup"><span data-stu-id="c5868-203">The rows in a memory-optimized table have the following components:</span></span>  
  
-   <span data-ttu-id="c5868-204">行ヘッダーは、行のバージョン管理を実装するために必要なタイムスタンプを格納したものです。</span><span class="sxs-lookup"><span data-stu-id="c5868-204">The row header contains the timestamp necessary to implement row versioning.</span></span> <span data-ttu-id="c5868-205">行ヘッダーにはほかにも、(上で説明した) ハッシュ バケットの行のチェーン関係を実装するためのインデックス ポインターが格納されています。</span><span class="sxs-lookup"><span data-stu-id="c5868-205">The row header also contains the index pointer to implement the row chaining in the hash buckets (described above).</span></span>  
  
-   <span data-ttu-id="c5868-206">行の本文は、実際の列データを格納する部分であり、NULL 値を許容する列の null 配列や可変長データ型のオフセット配列など、補助的な情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5868-206">The row body contains the actual column data, which includes some auxiliary information like the null array for nullable columns and the offset array for variable-length data types.</span></span>  
  
 <span data-ttu-id="c5868-207">次の図は、2 種類のインデックスを備えたテーブルの行構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="c5868-207">The following figure illustrates the row structure for a table that has two indexes:</span></span>  
  
 <span data-ttu-id="c5868-208">![2 つのインデックスがあるテーブルの行構造](../../database-engine/media/hekaton-tables-4.gif "2 つのインデックスがあるテーブルの行構造")</span><span class="sxs-lookup"><span data-stu-id="c5868-208">![Row structure for a table that has two indexes.](../../database-engine/media/hekaton-tables-4.gif "Row structure for a table that has two indexes.")</span></span>  
  
 <span data-ttu-id="c5868-209">開始タイムスタンプおよび終了タイムスタンプは、特定の行バージョンが有効である期間を示します。</span><span class="sxs-lookup"><span data-stu-id="c5868-209">The begin and end timestamps indicate the period in which a particular row version is valid.</span></span> <span data-ttu-id="c5868-210">この間隔で開始されるトランザクションで、この行バージョンが使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="c5868-210">Transactions that start in this interval can see this row version.</span></span> <span data-ttu-id="c5868-211">詳細については、「[メモリ最適化テーブルを使用するトランザクション](memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5868-211">For more details see [Transactions in Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="c5868-212">インデックス ポインターは、ハッシュ バケットに属しているチェーン内の次の行を参照します。</span><span class="sxs-lookup"><span data-stu-id="c5868-212">The index pointers point to the next row in the chain belonging to the hash bucket.</span></span> <span data-ttu-id="c5868-213">次の図は、(名前と都市の) 2 列があり、名前の列用と都市の列用にそれぞれ 1 つのインデックスを備えたテーブルの構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="c5868-213">The following figure illustrates the structure of a table with two columns (name, city), and with two indexes, one on the column name, and one on the column city.</span></span>  
  
 <span data-ttu-id="c5868-214">![2 つの列とインデックスを持つテーブルの構造](../../database-engine/media/hekaton-tables-5.gif "2 つの列とインデックスを持つテーブルの構造")</span><span class="sxs-lookup"><span data-stu-id="c5868-214">![Structure of a table with two columns and indexes.](../../database-engine/media/hekaton-tables-5.gif "Structure of a table with two columns and indexes.")</span></span>  
  
 <span data-ttu-id="c5868-215">この図では、John と Jane の名前がハッシュされ、最初のバケットに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-215">In this figure, the names John and Jane are hashed to the first bucket.</span></span> <span data-ttu-id="c5868-216">Susan は、ハッシュされて 2 番目のバケットに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-216">Susan is hashed to the second bucket.</span></span> <span data-ttu-id="c5868-217">Beijing と Bogota の各都市は、ハッシュされて最初のバケットに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-217">The cities Beijing and Bogota are hashed to the first bucket.</span></span> <span data-ttu-id="c5868-218">Paris と Prague は、ハッシュされて 2 番目のバケットに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-218">Paris and Prague are hashed to the second bucket.</span></span>  
  
 <span data-ttu-id="c5868-219">以上のことから、名前のハッシュ インデックスのチェーンは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c5868-219">Thus, the chains for the hash index on name are as follows:</span></span>  
  
-   <span data-ttu-id="c5868-220">最初のバケット: (John, Beijing); (John, Paris); (Jane, Prague)</span><span class="sxs-lookup"><span data-stu-id="c5868-220">First bucket: (John, Beijing); (John, Paris); (Jane, Prague)</span></span>  
  
-   <span data-ttu-id="c5868-221">2 番目のバケット: (Susan, Bogota)</span><span class="sxs-lookup"><span data-stu-id="c5868-221">Second bucket: (Susan, Bogota)</span></span>  
  
 <span data-ttu-id="c5868-222">都市のインデックスのチェーンは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c5868-222">The chains for the index on city are as follows:</span></span>  
  
-   <span data-ttu-id="c5868-223">最初のバケット: (John, Beijing), (Susan, Bogota)</span><span class="sxs-lookup"><span data-stu-id="c5868-223">First bucket: (John, Beijing), (Susan, Bogota)</span></span>  
  
-   <span data-ttu-id="c5868-224">2 番目のバケット: (John, Paris), (Jane, Prague)</span><span class="sxs-lookup"><span data-stu-id="c5868-224">Second bucket: (John, Paris), (Jane, Prague)</span></span>  
  
 <span data-ttu-id="c5868-225">終了タイムスタンプ &#x221e; (無限大) は、これが行の現在有効なバージョンであることを示します。</span><span class="sxs-lookup"><span data-stu-id="c5868-225">An end timestamp &#x221e; (infinity) indicates that this is the currently valid version of the row.</span></span> <span data-ttu-id="c5868-226">この行は、この行バージョンが書き込まれてから更新および削除されていません。</span><span class="sxs-lookup"><span data-stu-id="c5868-226">The row has not been updated or deleted since this row version was written.</span></span>  
  
 <span data-ttu-id="c5868-227">時間が 200 より大きくなると、テーブルには次の行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5868-227">For a time greater than 200, the table contains the following rows:</span></span>  
  
|<span data-ttu-id="c5868-228">名前</span><span class="sxs-lookup"><span data-stu-id="c5868-228">Name</span></span>|<span data-ttu-id="c5868-229">City</span><span class="sxs-lookup"><span data-stu-id="c5868-229">City</span></span>|  
|----------|----------|  
|<span data-ttu-id="c5868-230">John</span><span class="sxs-lookup"><span data-stu-id="c5868-230">John</span></span>|<span data-ttu-id="c5868-231">北京</span><span class="sxs-lookup"><span data-stu-id="c5868-231">Beijing</span></span>|  
|<span data-ttu-id="c5868-232">Jane</span><span class="sxs-lookup"><span data-stu-id="c5868-232">Jane</span></span>|<span data-ttu-id="c5868-233">Prague</span><span class="sxs-lookup"><span data-stu-id="c5868-233">Prague</span></span>|  
  
 <span data-ttu-id="c5868-234">ただし、開始時刻が 100 のアクティブなトランザクションでは、以下のバージョンのテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5868-234">However, any active transaction with begin time 100 will see the following version of the table:</span></span>  
  
|<span data-ttu-id="c5868-235">名前</span><span class="sxs-lookup"><span data-stu-id="c5868-235">Name</span></span>|<span data-ttu-id="c5868-236">City</span><span class="sxs-lookup"><span data-stu-id="c5868-236">City</span></span>|  
|----------|----------|  
|<span data-ttu-id="c5868-237">John</span><span class="sxs-lookup"><span data-stu-id="c5868-237">John</span></span>|<span data-ttu-id="c5868-238">Paris</span><span class="sxs-lookup"><span data-stu-id="c5868-238">Paris</span></span>|  
|<span data-ttu-id="c5868-239">Jane</span><span class="sxs-lookup"><span data-stu-id="c5868-239">Jane</span></span>|<span data-ttu-id="c5868-240">Prague</span><span class="sxs-lookup"><span data-stu-id="c5868-240">Prague</span></span>|  
|<span data-ttu-id="c5868-241">Susan</span><span class="sxs-lookup"><span data-stu-id="c5868-241">Susan</span></span>|<span data-ttu-id="c5868-242">Bogata</span><span class="sxs-lookup"><span data-stu-id="c5868-242">Bogata</span></span>|  
  
##  <a name="example-table-and-row-size-computation"></a><a name="bkmk_ExampleComputation"></a> <span data-ttu-id="c5868-243">例: テーブルと行のサイズの計算</span><span class="sxs-lookup"><span data-stu-id="c5868-243">Example: Table and Row Size Computation</span></span>  
 <span data-ttu-id="c5868-244">ハッシュ インデックスの場合、実際のバケット数は最も近い 2 のべき乗に切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="c5868-244">For hash indexes, the actual bucket count is rounded up to the nearest power of 2.</span></span> <span data-ttu-id="c5868-245">たとえば、指定された bucket_count が 100,000 の場合、インデックスの実際のバケット数は 131,072 です。</span><span class="sxs-lookup"><span data-stu-id="c5868-245">For example, if the specified bucket_count is 100000, the actual bucket count for the index is 131072.</span></span>  
  
 <span data-ttu-id="c5868-246">次の定義を含む Orders テーブルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="c5868-246">Consider an Orders table with the following definition:</span></span>  
  
```sql  
CREATE TABLE dbo.Orders (  
     OrderID int NOT NULL   
           PRIMARY KEY NONCLUSTERED,  
     CustomerID int NOT NULL   
           INDEX IX_CustomerID HASH WITH (BUCKET_COUNT=10000),  
     OrderDate datetime NOT NULL,  
     OrderDescription nvarchar(1000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 <span data-ttu-id="c5868-247">このテーブルには 1 つのハッシュ インデックスと 1 つの非クラスター化インデックス (主キー) が含まれていることを注意してください。</span><span class="sxs-lookup"><span data-stu-id="c5868-247">Notice that this table has one hash index and a nonclustered index (the primary key).</span></span> <span data-ttu-id="c5868-248">さらに、3 個の固定長列および 1 個の可変長列があり、そのうちの 1 個の列は NULL 値を許容します (OrderDescription)。</span><span class="sxs-lookup"><span data-stu-id="c5868-248">It also has three fixed-length columns and one variable-length column, with one of the columns being NULLable (OrderDescription).</span></span> <span data-ttu-id="c5868-249">Orders テーブルに8379行あり、OrderDescription 列の値の平均の長さが78文字であるとします。</span><span class="sxs-lookup"><span data-stu-id="c5868-249">Let's assume the Orders table has 8379 rows, and the average length of the values in the OrderDescription column is 78 characters.</span></span>  
  
 <span data-ttu-id="c5868-250">このテーブルのサイズを判断するには、最初にインデックスのサイズを調べます。</span><span class="sxs-lookup"><span data-stu-id="c5868-250">To determine the table size, first determine the size of the indexes.</span></span> <span data-ttu-id="c5868-251">両方のインデックスの bucket_count は 10,000 と指定されています。</span><span class="sxs-lookup"><span data-stu-id="c5868-251">The bucket_count for both indexes is specified as 10000.</span></span> <span data-ttu-id="c5868-252">これは、最も近い 2 のべき乗に切り上げられて次のようになります: 16384</span><span class="sxs-lookup"><span data-stu-id="c5868-252">This is rounded up to the nearest power of 2: 16384.</span></span> <span data-ttu-id="c5868-253">したがって、Orders テーブルのインデックスの合計サイズは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c5868-253">Therefore, the total size of the indexes for the Orders table is:</span></span>  
  
```  
8 * 16384 = 131072 bytes  
```  
  
 <span data-ttu-id="c5868-254">テーブルのデータ サイズは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c5868-254">What remains is the table data size, which is,</span></span>  
  
```  
[row size] * [row count] = [row size] * 8379  
```  
  
 <span data-ttu-id="c5868-255">(このテーブルには 8,379 行あります。)次の計算式を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5868-255">(The example table has 8379 rows.) Now, we have:</span></span>  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices] = 24 + 8 * 1 = 32 bytes  
```  
  
 <span data-ttu-id="c5868-256">ここで、[実際の行本文サイズ]を計算します。</span><span class="sxs-lookup"><span data-stu-id="c5868-256">Next, let's calculate [actual row body size]:</span></span>  
  
-   <span data-ttu-id="c5868-257">シャロー型の列:</span><span class="sxs-lookup"><span data-stu-id="c5868-257">Shallow type columns:</span></span>  
  
    ```  
    SUM([size of shallow types]) = 4 [int] + 4 [int] + 8 [datetime] = 16  
    ```  
  
-   <span data-ttu-id="c5868-258">シャロー列のサイズが偶数であるため、シャロー列の余白は 0 です。</span><span class="sxs-lookup"><span data-stu-id="c5868-258">Shallow column padding is 0, as the total shallow column size is even.</span></span>  
  
-   <span data-ttu-id="c5868-259">ディープ型の列のオフセット配列:</span><span class="sxs-lookup"><span data-stu-id="c5868-259">Offset array for deep type columns:</span></span>  
  
    ```  
    2 + 2 * [number of deep type columns] = 2 + 2 * 1 = 4  
    ```  
  
-   <span data-ttu-id="c5868-260">NULL 配列は 1 です。</span><span class="sxs-lookup"><span data-stu-id="c5868-260">NULL array = 1</span></span>  
  
-   <span data-ttu-id="c5868-261">NULL 配列のサイズが奇数であり、ディープ型の列が存在するため、null 配列の余白は 1 です。</span><span class="sxs-lookup"><span data-stu-id="c5868-261">NULL array padding = 1, as the NULL array size is odd and there is a deep type column.</span></span>  
  
-   <span data-ttu-id="c5868-262">パディング</span><span class="sxs-lookup"><span data-stu-id="c5868-262">Padding</span></span>  
  
    -   <span data-ttu-id="c5868-263">必要な配置のうち、最も大きな値は 8 です。</span><span class="sxs-lookup"><span data-stu-id="c5868-263">8 is the largest alignment requirement.</span></span>  
  
    -   <span data-ttu-id="c5868-264">これまでのサイズは、16+ 0 + 4 + 1 + 1 = 22 です。</span><span class="sxs-lookup"><span data-stu-id="c5868-264">Size so far is 16 + 0 + 4 + 1 + 1 = 22.</span></span>  
  
    -   <span data-ttu-id="c5868-265">最も近い 8 の倍数は 24 です。</span><span class="sxs-lookup"><span data-stu-id="c5868-265">Nearest multiple of 8 is 24.</span></span>  
  
    -   <span data-ttu-id="c5868-266">合計余白は 24 - 22 = 2 バイトです。</span><span class="sxs-lookup"><span data-stu-id="c5868-266">Total padding is 24 - 22 = 2 bytes.</span></span>  
  
-   <span data-ttu-id="c5868-267">固定長のディープ型の列はありません (固定長のディープ型の列は 0)。</span><span class="sxs-lookup"><span data-stu-id="c5868-267">There are no fixed-length deep type columns (Fixed-length deep type columns: 0.).</span></span>  
  
-   <span data-ttu-id="c5868-268">ディープ型の列の実際のサイズは 2 \* 78 = 156 です。</span><span class="sxs-lookup"><span data-stu-id="c5868-268">The actual size of deep type column is 2 \* 78 = 156.</span></span> <span data-ttu-id="c5868-269">単一のディープ型の列である OrderDescription は nvarchar 型です。</span><span class="sxs-lookup"><span data-stu-id="c5868-269">The single deep type column OrderDescription has type nvarchar.</span></span>  
  
```  
[actual row body size] = 24 + 156 = 180 bytes  
```  
  
 <span data-ttu-id="c5868-270">次のように計算を完了します。</span><span class="sxs-lookup"><span data-stu-id="c5868-270">To complete the calculation:</span></span>  
  
```  
[row size] = 32 + 180 = 212 bytes  
[table size] = 8 * 16384 + 212 * 8379 = 131072 + 1776348 = 1907420  
```  
  
 <span data-ttu-id="c5868-271">メモリ内のテーブルの合計サイズは、約 2 MB です。</span><span class="sxs-lookup"><span data-stu-id="c5868-271">Total table size in memory is thus approximately 2 megabytes.</span></span> <span data-ttu-id="c5868-272">ただし、メモリ割り当てによって発生する潜在的なオーバーヘッドや、このテーブルにアクセスするトランザクションに必要な行のバージョン管理は考慮されていません。</span><span class="sxs-lookup"><span data-stu-id="c5868-272">This does not account for potential overhead incurred by memory allocation as well as any row versioning required for the transactions accessing this table.</span></span>  
  
 <span data-ttu-id="c5868-273">実際にこのテーブルおよびインデックスに割り当てられ、使用されるメモリは、次のクエリを使用して取得することができます。</span><span class="sxs-lookup"><span data-stu-id="c5868-273">The actual memory allocated for and used by this table and its indexes can be obtained through the following query:</span></span>  
  
```sql  
select * from sys.dm_db_xtp_table_memory_stats  
where object_id = object_id('dbo.Orders')  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5868-274">参照</span><span class="sxs-lookup"><span data-stu-id="c5868-274">See Also</span></span>  
 [<span data-ttu-id="c5868-275">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="c5868-275">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
