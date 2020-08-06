---
title: ヒープ サイズの見積もり | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- estimating heap size
- size [SQL Server], heap
- space [SQL Server], indexes
- heaps
ms.assetid: 81fd5ec9-ce0f-4c2c-8ba0-6c483cea6c75
author: stevestein
ms.author: sstein
ms.openlocfilehash: f32432d07a9731d849ceb793daf209cfc505b0ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645628"
---
# <a name="estimate-the-size-of-a-heap"></a><span data-ttu-id="f3730-102">ヒープ サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="f3730-102">Estimate the Size of a Heap</span></span>
  <span data-ttu-id="f3730-103">ヒープにデータを格納するために必要な領域は、次の手順で見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="f3730-103">You can use the following steps to estimate the amount of space that is required to store data in a heap:</span></span>  
  
1.  <span data-ttu-id="f3730-104">次のように、テーブル内の行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3730-104">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="f3730-105">***Num_Rows***  = テーブル内の行数</span><span class="sxs-lookup"><span data-stu-id="f3730-105">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="f3730-106">次のように、固定長列と可変長列の数を指定し、それらの列を格納するために必要な領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="f3730-106">Specify the number of fixed-length and variable-length columns and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="f3730-107">固定長列のグループと可変長列のグループがデータ行内で使用する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="f3730-107">Calculate the space that each of these groups of columns occupies within the data row.</span></span> <span data-ttu-id="f3730-108">列のサイズは、データ型と長さの指定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f3730-108">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="f3730-109">***Num_Cols***  = 列 (固定長および可変長) の総数</span><span class="sxs-lookup"><span data-stu-id="f3730-109">***Num_Cols***  = total number of columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="f3730-110">***Fixed_Data_Size***  = すべての固定長列の合計バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="f3730-110">***Fixed_Data_Size***  = total byte size of all fixed-length columns</span></span>  
  
     <span data-ttu-id="f3730-111">***Num_Variable_Cols***  = 可変長列の数</span><span class="sxs-lookup"><span data-stu-id="f3730-111">***Num_Variable_Cols***  = number of variable-length columns</span></span>  
  
     <span data-ttu-id="f3730-112">***Max_Var_Size*** = すべての可変長列の最大合計バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="f3730-112">***Max_Var_Size***  = maximum total byte size of all variable-length columns</span></span>  
  
3.  <span data-ttu-id="f3730-113">NULL ビットマップと呼ばれる行の部分は、列の NULL 値の許容を管理するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="f3730-113">Part of the row, known as the null bitmap, is reserved to manage column nullability.</span></span> <span data-ttu-id="f3730-114">このサイズは次のように計算します。</span><span class="sxs-lookup"><span data-stu-id="f3730-114">Calculate its size:</span></span>  
  
     <span data-ttu-id="f3730-115">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="f3730-115">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="f3730-116">この式の計算結果は、整数部分だけを使用します。</span><span class="sxs-lookup"><span data-stu-id="f3730-116">Only the integer part of this expression should be used.</span></span> <span data-ttu-id="f3730-117">小数部分は無視してください。</span><span class="sxs-lookup"><span data-stu-id="f3730-117">Discard any remainder.</span></span>  
  
4.  <span data-ttu-id="f3730-118">次の式で、可変長のデータ サイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="f3730-118">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="f3730-119">テーブル内に可変長列が存在する場合、次の式を使用して、行内でそれらの列を格納するために使用する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="f3730-119">If there are variable-length columns in the table, determine how much space is used to store the columns within the row:</span></span>  
  
     <span data-ttu-id="f3730-120">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span><span class="sxs-lookup"><span data-stu-id="f3730-120">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span></span>  
  
     <span data-ttu-id="f3730-121">***Max_Var_Size*** に追加されたバイトは、それぞれの可変長列を追跡するためのものです。</span><span class="sxs-lookup"><span data-stu-id="f3730-121">The bytes added to ***Max_Var_Size*** are for tracking each variable-length column.</span></span> <span data-ttu-id="f3730-122">この式は、すべての可変長列がいっぱいになることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f3730-122">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="f3730-123">可変長列の格納領域の使用率が 100% 以下になることが予想される場合、その使用率に基づいて ***Max_Var_Size*** の値を調整し、テーブルの全体サイズをより正確に見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="f3730-123">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3730-124">定義済みのテーブルの合計サイズが 8,060 バイトを超える `varchar`、`nvarchar`、`varbinary`、または `sql_variant` 列の連結が可能です。</span><span class="sxs-lookup"><span data-stu-id="f3730-124">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="f3730-125">これらの各列の長さは `varchar` 、、、または列の8000バイトの制限内に収まる必要があり `nvarchar,``varbinary` `sql_variant` ます。</span><span class="sxs-lookup"><span data-stu-id="f3730-125">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `nvarchar,``varbinary`, or `sql_variant` column.</span></span> <span data-ttu-id="f3730-126">ただし、これらの列を連結したサイズは、テーブルの制限である 8,060 バイトを超過してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f3730-126">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span>  
  
     <span data-ttu-id="f3730-127">可変長列が存在しない場合は、 ***Variable_Data_Size*** に 0 を設定します。</span><span class="sxs-lookup"><span data-stu-id="f3730-127">If there are no variable-length columns, set ***Variable_Data_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="f3730-128">次の式で行サイズの合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="f3730-128">Calculate the total row size:</span></span>  
  
     <span data-ttu-id="f3730-129">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span><span class="sxs-lookup"><span data-stu-id="f3730-129">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span></span>  
  
     <span data-ttu-id="f3730-130">上記の式の 4 という値は、データ行の行ヘッダー オーバーヘッドです。</span><span class="sxs-lookup"><span data-stu-id="f3730-130">The value 4 in the formula is the row header overhead of the data row.</span></span>  
  
6.  <span data-ttu-id="f3730-131">次の式で、1 ページあたりの行数を計算します (1 ページあたりの空きバイト数は 8,096 です)。</span><span class="sxs-lookup"><span data-stu-id="f3730-131">Calculate the number of rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="f3730-132">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="f3730-132">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="f3730-133">行は複数のページにまたがらないので、計算結果の端数は切り捨ててください。</span><span class="sxs-lookup"><span data-stu-id="f3730-133">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="f3730-134">上記の式の 2 という値は、ページのスロット配列内の行のエントリのためのものです。</span><span class="sxs-lookup"><span data-stu-id="f3730-134">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
7.  <span data-ttu-id="f3730-135">次の式で、すべての行を格納するために必要なページ数を計算します。</span><span class="sxs-lookup"><span data-stu-id="f3730-135">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="f3730-136">***Num_Pages***  = ***Num_Rows*** / ***Rows_Per_Page***</span><span class="sxs-lookup"><span data-stu-id="f3730-136">***Num_Pages***  = ***Num_Rows*** / ***Rows_Per_Page***</span></span>  
  
     <span data-ttu-id="f3730-137">算出したページ数の端数は切り上げてください。</span><span class="sxs-lookup"><span data-stu-id="f3730-137">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
8.  <span data-ttu-id="f3730-138">次の式で、ヒープにデータを格納するために必要な領域を計算します (1 ページあたりの総バイト数は 8,192 です)。</span><span class="sxs-lookup"><span data-stu-id="f3730-138">Calculate the amount of space that is required to store the data in the heap (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="f3730-139">ヒープのサイズ (バイト) = 8192 x ***Num_Pages***</span><span class="sxs-lookup"><span data-stu-id="f3730-139">Heap size (bytes) = 8192 x ***Num_Pages***</span></span>  
  
 <span data-ttu-id="f3730-140">この計算では、次のことは考慮されていません。</span><span class="sxs-lookup"><span data-stu-id="f3730-140">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="f3730-141">パーティション分割</span><span class="sxs-lookup"><span data-stu-id="f3730-141">Partitioning</span></span>  
  
     <span data-ttu-id="f3730-142">パーティション分割による領域のオーバーヘッドはわずかですが、計算が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="f3730-142">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="f3730-143">これは、計算に含めるほど重要なことではありません。</span><span class="sxs-lookup"><span data-stu-id="f3730-143">It is not important to include.</span></span>  
  
-   <span data-ttu-id="f3730-144">アロケーション ページ</span><span class="sxs-lookup"><span data-stu-id="f3730-144">Allocation pages</span></span>  
  
     <span data-ttu-id="f3730-145">ヒープに割り当てられたページの追跡に使用する IAM ページが少なくとも 1 ページありますが、使用される IAM ページ数を正確に計算できるアルゴリズムはなく、領域のオーバーヘッドはわずかです。</span><span class="sxs-lookup"><span data-stu-id="f3730-145">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="f3730-146">ラージ オブジェクト (LOB) の値</span><span class="sxs-lookup"><span data-stu-id="f3730-146">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="f3730-147">LOB データ型、、、 `varchar(max)` `varbinary(max)` `nvarchar(max)` `text` 、 **ntextxml**、および値の格納に使用される領域を正確に特定するためのアルゴリズム `image` は複雑です。</span><span class="sxs-lookup"><span data-stu-id="f3730-147">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, **ntextxml**, and `image` values is complex.</span></span> <span data-ttu-id="f3730-148">LOB データ型の値で使用される領域の計算は、予想される LOB 値の平均サイズを合計し、ヒープの合計サイズに加算するだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="f3730-148">It is sufficient to just add the average size of the LOB values that are expected and add that to the total heap size.</span></span>  
  
-   <span data-ttu-id="f3730-149">圧縮</span><span class="sxs-lookup"><span data-stu-id="f3730-149">Compression</span></span>  
  
     <span data-ttu-id="f3730-150">圧縮されたヒープのサイズを事前に計算することはできません。</span><span class="sxs-lookup"><span data-stu-id="f3730-150">You cannot pre-calculate the size of a compressed heap.</span></span>  
  
-   <span data-ttu-id="f3730-151">スパース列</span><span class="sxs-lookup"><span data-stu-id="f3730-151">Sparse columns</span></span>  
  
     <span data-ttu-id="f3730-152">スパース列の領域要件については、「 [スパース列の使用](../tables/use-sparse-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3730-152">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3730-153">参照</span><span class="sxs-lookup"><span data-stu-id="f3730-153">See Also</span></span>  
 <span data-ttu-id="f3730-154">[ヒープ &#40;クラスター化インデックスなしのテーブル&#41;](../indexes/heaps-tables-without-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="f3730-154">[Heaps &#40;Tables without Clustered Indexes&#41;](../indexes/heaps-tables-without-clustered-indexes.md) </span></span>  
 <span data-ttu-id="f3730-155">[クラスター化インデックスと非クラスター化インデックスの概念](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="f3730-155">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="f3730-156">[クラスター化インデックスの作成](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="f3730-156">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="f3730-157">[非クラスター化インデックスの作成](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="f3730-157">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="f3730-158">[テーブル サイズの見積もり](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="f3730-158">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="f3730-159">[クラスター化インデックスのサイズの見積もり](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="f3730-159">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 <span data-ttu-id="f3730-160">[非クラスター化インデックスのサイズの算出](estimate-the-size-of-a-nonclustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="f3730-160">[Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md) </span></span>  
 [<span data-ttu-id="f3730-161">データベース サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="f3730-161">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
