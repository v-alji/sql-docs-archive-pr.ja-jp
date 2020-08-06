---
title: 非クラスター化インデックスのサイズの算出 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: c183b0e4-ef4c-4bfc-8575-5ac219c25b0a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 097c0e5568ba17b12f83d09e347eb3bf8b0bd7da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736378"
---
# <a name="estimate-the-size-of-a-nonclustered-index"></a><span data-ttu-id="eed01-102">非クラスター化インデックスのサイズの算出</span><span class="sxs-lookup"><span data-stu-id="eed01-102">Estimate the Size of a Nonclustered Index</span></span>
  <span data-ttu-id="eed01-103">非クラスター化インデックスを格納するために必要な領域を算出するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="eed01-103">Follow these steps to estimate the amount of space that is required to store a nonclustered index:</span></span>  
  
1.  <span data-ttu-id="eed01-104">手順 2. および 3. で使用する変数を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-104">Calculate variables for use in steps 2 and 3.</span></span>  
  
2.  <span data-ttu-id="eed01-105">非クラスター化インデックスのリーフ レベルのインデックス情報の格納に使用する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-105">Calculate the space used to store index information in the leaf level of the nonclustered index.</span></span>  
  
3.  <span data-ttu-id="eed01-106">非クラスター化インデックスの非リーフ レベルのインデックス情報の格納に使用する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-106">Calculate the space used to store index information in the non-leaf levels of the nonclustered index.</span></span>  
  
4.  <span data-ttu-id="eed01-107">計算した値を合計します。</span><span class="sxs-lookup"><span data-stu-id="eed01-107">Total the calculated values.</span></span>  
  
## <a name="step-1-calculate-variables-for-use-in-steps-2-and-3"></a><span data-ttu-id="eed01-108">手順 1.</span><span class="sxs-lookup"><span data-stu-id="eed01-108">Step 1.</span></span> <span data-ttu-id="eed01-109">手順 2. および 3. で使用する変数を計算する</span><span class="sxs-lookup"><span data-stu-id="eed01-109">Calculate Variables for Use in Steps 2 and 3</span></span>  
 <span data-ttu-id="eed01-110">上位レベルのインデックスの格納に必要な領域を算出するために使用する変数は、次の手順で算出することができます。</span><span class="sxs-lookup"><span data-stu-id="eed01-110">You can use the following steps to calculate variables that are used to estimate the amount of space that is required to store the upper levels of the index.</span></span>  
  
1.  <span data-ttu-id="eed01-111">次のように、テーブル内の行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="eed01-111">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="eed01-112">***Num_Rows***  = テーブル内の行数</span><span class="sxs-lookup"><span data-stu-id="eed01-112">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="eed01-113">次のように、インデックス キーの固定長列と可変長列の数を指定し、それらの列の格納に必要な領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-113">Specify the number of fixed-length and variable-length columns in the index key and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="eed01-114">インデックスのキー列には、固定長列と可変長列を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="eed01-114">The key columns of an index can include fixed-length and variable-length columns.</span></span> <span data-ttu-id="eed01-115">内部レベルのインデックス行サイズを見積もるには、これらの各列グループによってインデックス行内で占有される領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-115">To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row.</span></span> <span data-ttu-id="eed01-116">列のサイズは、データ型と長さの指定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eed01-116">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="eed01-117">***Num_Key_Cols***  = キー列 (固定長および可変長) の総数</span><span class="sxs-lookup"><span data-stu-id="eed01-117">***Num_Key_Cols***  = total number of key columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="eed01-118">***Fixed_Key_Size***  = すべての固定長キー列の合計バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="eed01-118">***Fixed_Key_Size***  = total byte size of all fixed-length key columns</span></span>  
  
     <span data-ttu-id="eed01-119">***Num_Variable_Key_Cols***  = 可変長キー列の数</span><span class="sxs-lookup"><span data-stu-id="eed01-119">***Num_Variable_Key_Cols***  = number of variable-length key columns</span></span>  
  
     <span data-ttu-id="eed01-120">***Max_Var_Key_Size***  = すべての可変長キー列の最大バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="eed01-120">***Max_Var_Key_Size***  = maximum byte size of all variable-length key columns</span></span>  
  
3.  <span data-ttu-id="eed01-121">インデックスが一意ではない場合に必要なデータ行ロケーターの領域を、次のように計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-121">Account for the data row locator that is required if the index is nonunique:</span></span>  
  
     <span data-ttu-id="eed01-122">非クラスター化インデックスが一意ではない場合、データ行ロケーターと非クラスター化インデックス キーを組み合わせて、各行に一意のキー値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="eed01-122">If the nonclustered index is nonunique, the data row locator is combined with the nonclustered index key to produce a unique key value for every row.</span></span>  
  
     <span data-ttu-id="eed01-123">非クラスター化インデックスがヒープ上にある場合は、データ行ロケーターはヒープ RID になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-123">If the nonclustered index is over a heap, the data row locator is the heap RID.</span></span> <span data-ttu-id="eed01-124">このサイズは 8 バイトです。</span><span class="sxs-lookup"><span data-stu-id="eed01-124">This is a size of 8 bytes.</span></span>  
  
     <span data-ttu-id="eed01-125">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="eed01-125">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="eed01-126">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="eed01-126">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="eed01-127">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 8</span><span class="sxs-lookup"><span data-stu-id="eed01-127">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 8</span></span>  
  
     <span data-ttu-id="eed01-128">非クラスター化インデックスがクラスター化インデックス上にある場合は、データ行ロケーターはクラスター化キーになります。</span><span class="sxs-lookup"><span data-stu-id="eed01-128">If the nonclustered index is over a clustered index, the data row locator is the clustering key.</span></span> <span data-ttu-id="eed01-129">非クラスター化インデックス キーと組み合わせる必要がある列は、非クラスター化インデックスのキー列のセットに含まれていないクラスター化キーの列です。</span><span class="sxs-lookup"><span data-stu-id="eed01-129">The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.</span></span>  
  
     <span data-ttu-id="eed01-130">***Num_Key_Cols***  = ***Num_Key_Cols*** + 非クラスター化インデックスのキー列のセットに含まれていないクラスター化キー列数 (クラスター化インデックスが一意でない場合は + 1)</span><span class="sxs-lookup"><span data-stu-id="eed01-130">***Num_Key_Cols***  = ***Num_Key_Cols*** + number of clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="eed01-131">***Fixed_Key_Size***  = ***Fixed_Key_Size*** + 非クラスター化インデックスのキー列のセットに含まれていない固定長クラスター化キー列の合計バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="eed01-131">***Fixed_Key_Size***  = ***Fixed_Key_Size*** + total byte size of fixed-length clustering key columns not in the set of nonclustered index key columns</span></span>  
  
     <span data-ttu-id="eed01-132">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 非クラスター化インデックスのキー列のセットに含まれていない可変長クラスター化キー列数 (クラスター化インデックスが一意でない場合は + 1)</span><span class="sxs-lookup"><span data-stu-id="eed01-132">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + number of variable-length clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="eed01-133">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 非クラスター化インデックスのキー列のセットに含まれていない可変長クラスター化キー列の最大バイト サイズ (クラスター化インデックスが一意でない場合は + 4)</span><span class="sxs-lookup"><span data-stu-id="eed01-133">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + maximum byte size of variable-length clustering key columns not in the set of nonclustered index key columns (+ 4 if the clustered index is nonunique)</span></span>  
  
4.  <span data-ttu-id="eed01-134">NULL ビットマップと呼ばれる行の一部が、列に NULL 値を許容するかどうかを管理するために予約されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="eed01-134">Part of the row, known as the null bitmap, may be reserved to manage column nullability.</span></span> <span data-ttu-id="eed01-135">このサイズは次のように計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-135">Calculate its size:</span></span>  
  
     <span data-ttu-id="eed01-136">手順 1.3. で説明している必要なクラスター化キー列を含め、インデックス キーに NULL 値を許容する列が存在する場合には、インデックス行の一部が NULL ビットマップ用に予約されます。</span><span class="sxs-lookup"><span data-stu-id="eed01-136">If there are nullable columns in the index key, including any necessary clustering key columns as described in Step 1.3, part of the index row is reserved for the null bitmap.</span></span>  
  
     <span data-ttu-id="eed01-137">***Index_Null_Bitmap***  = 2 + ((インデックス行の列数 + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="eed01-137">***Index_Null_Bitmap***  = 2 + ((number of columns in the index row + 7) / 8)</span></span>  
  
     <span data-ttu-id="eed01-138">上記の式の計算結果は、整数部分だけを使用します。</span><span class="sxs-lookup"><span data-stu-id="eed01-138">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="eed01-139">小数部分は無視してください。</span><span class="sxs-lookup"><span data-stu-id="eed01-139">Discard any remainder.</span></span>  
  
     <span data-ttu-id="eed01-140">NULL 値を許容するキー列が存在しない場合は、 ***Index_Null_Bitmap*** を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="eed01-140">If there are no nullable key columns, set ***Index_Null_Bitmap*** to 0.</span></span>  
  
5.  <span data-ttu-id="eed01-141">可変長データ サイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-141">Calculate the variable length data size:</span></span>  
  
     <span data-ttu-id="eed01-142">必要なクラスター化インデックスのキー列を含め、インデックス キーに可変長列が存在する場合は、インデックス行内に可変長列を格納するのに使用する領域を次の式で計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-142">If there are variable-length columns in the index key, including any necessary clustered index key columns, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="eed01-143">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="eed01-143">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="eed01-144">***Max_Var_Key_Size*** に追加されたバイトは、それぞれの可変長列を追跡するためのものです。この式は、すべての可変長列がいっぱいになることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="eed01-144">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable column.This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="eed01-145">可変長列の格納領域の使用率が 100% 以下になることが予想される場合、その使用率に基づいて ***Max_Var_Key_Size*** の値を調整し、テーブルの全体サイズをより正確に見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="eed01-145">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Key_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="eed01-146">可変長列が存在しない場合は、 ***Variable_Key_Size*** に 0 を設定します。</span><span class="sxs-lookup"><span data-stu-id="eed01-146">If there are no variable-length columns, set ***Variable_Key_Size*** to 0.</span></span>  
  
6.  <span data-ttu-id="eed01-147">次の式でインデックス行のサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-147">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="eed01-148">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (インデックス行の行ヘッダー オーバーヘッド) + 6 (子ページ ID のポインター)</span><span class="sxs-lookup"><span data-stu-id="eed01-148">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
7.  <span data-ttu-id="eed01-149">次の式で、1 ページあたりのインデックス行数を計算します (1 ページあたりの空きバイト数は 8,096 です)。</span><span class="sxs-lookup"><span data-stu-id="eed01-149">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="eed01-150">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="eed01-150">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="eed01-151">インデックス行は複数のページにまたがらないため、計算結果の端数は切り捨ててください。</span><span class="sxs-lookup"><span data-stu-id="eed01-151">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="eed01-152">上の式の 2 という値は、ページのスロット配列内にある行の入力用です。</span><span class="sxs-lookup"><span data-stu-id="eed01-152">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information-in-the-leaf-level"></a><span data-ttu-id="eed01-153">手順 2.</span><span class="sxs-lookup"><span data-stu-id="eed01-153">Step 2.</span></span> <span data-ttu-id="eed01-154">リーフ レベルのインデックス情報の格納に使用する領域を計算する</span><span class="sxs-lookup"><span data-stu-id="eed01-154">Calculate the Space Used to Store Index Information in the Leaf Level</span></span>  
 <span data-ttu-id="eed01-155">インデックスのリーフ レベルを格納するために必要な領域は、次の手順で算出することができます。</span><span class="sxs-lookup"><span data-stu-id="eed01-155">You can use the following steps to estimate the amount of space that is required to store the leaf level of the index.</span></span> <span data-ttu-id="eed01-156">この手順を完了するには、手順 1. で控えた値が必要になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-156">You will need the values preserved from Step 1 to complete this step.</span></span>  
  
1.  <span data-ttu-id="eed01-157">次のように、リーフ レベルの固定長列と可変長列の数を指定し、それらの列の格納に必要な領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-157">Specify the number of fixed-length and variable-length columns at the leaf level and calculate the space that is required for their storage:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eed01-158">インデックス キー列の他に非キー列を含めることにより、非クラスター化インデックスを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="eed01-158">You can extend a nonclustered index by including nonkey columns in addition to the index key columns.</span></span> <span data-ttu-id="eed01-159">このように追加された列は、非クラスター化インデックスのリーフ レベルにしか格納されません。</span><span class="sxs-lookup"><span data-stu-id="eed01-159">These additional columns are only stored at the leaf level of the nonclustered index.</span></span> <span data-ttu-id="eed01-160">詳細については、「 [付加列インデックスの作成](../indexes/create-indexes-with-included-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed01-160">For more information, see [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eed01-161">定義済みのテーブルの合計サイズが 8,060 バイトを超える `varchar`、`nvarchar`、`varbinary`、または `sql_variant` 列の連結が可能です。</span><span class="sxs-lookup"><span data-stu-id="eed01-161">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="eed01-162">この場合も、`varchar`、`varbinary`、または `sql_variant` 列の場合は 8,000 バイト、`nvarchar` 列の場合は 4,000 バイトの制限内に、各列のサイズを収める必要があります。</span><span class="sxs-lookup"><span data-stu-id="eed01-162">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `varbinary`, or `sql_variant` column, and 4,000 bytes for `nvarchar` columns.</span></span> <span data-ttu-id="eed01-163">ただし、これらの列を連結したサイズは、テーブルの制限である 8,060 バイトを超過してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="eed01-163">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span> <span data-ttu-id="eed01-164">これは、既に付加列を含んでいる非クラスター化インデックスのリーフ行にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="eed01-164">This also applies to nonclustered index leaf rows that have included columns.</span></span>  
  
     <span data-ttu-id="eed01-165">非クラスター化インデックスに付加列が含まれていない場合は、手順 1.3. での変更を含め、手順 1. の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="eed01-165">If the nonclustered index does not have any included columns, use the values from Step 1, including any modifications determined in Step 1.3:</span></span>  
  
     <span data-ttu-id="eed01-166">***Num_Leaf_Cols***  = ***Num_Key_Cols***</span><span class="sxs-lookup"><span data-stu-id="eed01-166">***Num_Leaf_Cols***  = ***Num_Key_Cols***</span></span>  
  
     <span data-ttu-id="eed01-167">***Fixed_Leaf_Size***  = ***Fixed_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="eed01-167">***Fixed_Leaf_Size***  = ***Fixed_Key_Size***</span></span>  
  
     <span data-ttu-id="eed01-168">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols***</span><span class="sxs-lookup"><span data-stu-id="eed01-168">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols***</span></span>  
  
     <span data-ttu-id="eed01-169">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="eed01-169">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="eed01-170">非クラスター化インデックスに付加列が含まれている場合は、手順 1.3. での変更を含め、手順 1. の値に適切な値を加えます。</span><span class="sxs-lookup"><span data-stu-id="eed01-170">If the nonclustered index does have included columns, add the appropriate values to the values from Step 1, including any modifications in Step 1.3.</span></span> <span data-ttu-id="eed01-171">列のサイズは、データ型と長さの指定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eed01-171">The size of a column depends on the data type and length specification.</span></span> <span data-ttu-id="eed01-172">詳細については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed01-172">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
     <span data-ttu-id="eed01-173">***Num_Leaf_Cols***  = ***Num_Key_Cols*** + 付加列の数</span><span class="sxs-lookup"><span data-stu-id="eed01-173">***Num_Leaf_Cols***  = ***Num_Key_Cols*** + number of included columns</span></span>  
  
     <span data-ttu-id="eed01-174">***Fixed_Leaf_Size***  = ***Fixed_Key_Size*** + 固定長付加列の合計バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="eed01-174">***Fixed_Leaf_Size***  = ***Fixed_Key_Size*** + total byte size of fixed-length included columns</span></span>  
  
     <span data-ttu-id="eed01-175">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols*** + 可変長付加列の数</span><span class="sxs-lookup"><span data-stu-id="eed01-175">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols*** + number of variable-length included columns</span></span>  
  
     <span data-ttu-id="eed01-176">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size*** + 可変長付加列の最大バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="eed01-176">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size*** + maximum byte size of variable-length included columns</span></span>  
  
2.  <span data-ttu-id="eed01-177">データ行ロケーターに必要な領域を次のように計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-177">Account for the data row locator:</span></span>  
  
     <span data-ttu-id="eed01-178">非クラスター化インデックスが一意でない場合は、既に手順 1.3. でデータ行ロケーターのオーバーヘッドが考慮されているので、他の変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="eed01-178">If the nonclustered index is nonunique, the overhead for the data row locator has already been considered in Step 1.3 and no additional modifications are required.</span></span> <span data-ttu-id="eed01-179">次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="eed01-179">Go to the next step.</span></span>  
  
     <span data-ttu-id="eed01-180">非クラスター化インデックスが一意の場合は、リーフ レベルのすべての行のデータ行ロケーターに必要な領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-180">If the nonclustered index is unique, the data row locator must be accounted for in all rows at the leaf level.</span></span>  
  
     <span data-ttu-id="eed01-181">非クラスター化インデックスがヒープ上にある場合は、データ行ロケーターはヒープ RID (8 バイト) になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-181">If the nonclustered index is over a heap, the data row locator is the heap RID (size 8 bytes).</span></span>  
  
     <span data-ttu-id="eed01-182">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="eed01-182">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 1</span></span>  
  
     <span data-ttu-id="eed01-183">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="eed01-183">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 1</span></span>  
  
     <span data-ttu-id="eed01-184">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 8</span><span class="sxs-lookup"><span data-stu-id="eed01-184">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 8</span></span>  
  
     <span data-ttu-id="eed01-185">非クラスター化インデックスがクラスター化インデックス上にある場合は、データ行ロケーターはクラスター化キーになります。</span><span class="sxs-lookup"><span data-stu-id="eed01-185">If the nonclustered index is over a clustered index, the data row locator is the clustering key.</span></span> <span data-ttu-id="eed01-186">非クラスター化インデックス キーと組み合わせる必要がある列は、非クラスター化インデックスのキー列のセットに含まれていないクラスター化キーの列です。</span><span class="sxs-lookup"><span data-stu-id="eed01-186">The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.</span></span>  
  
     <span data-ttu-id="eed01-187">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 非クラスター化インデックスのキー列のセットに含まれていないクラスター化キー列数 (クラスター化インデックスが一意でない場合は + 1)</span><span class="sxs-lookup"><span data-stu-id="eed01-187">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + number of clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="eed01-188">***Fixed_Leaf_Size***  = ***Fixed_Leaf_Size*** + 非クラスター化インデックスのキー列のセットに含まれていない固定長クラスター化キー列数</span><span class="sxs-lookup"><span data-stu-id="eed01-188">***Fixed_Leaf_Size***  = ***Fixed_Leaf_Size*** + number of fixed-length clustering key columns not in the set of nonclustered index key columns</span></span>  
  
     <span data-ttu-id="eed01-189">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 非クラスター化インデックスのキー列のセットに含まれていない可変長クラスター化キー列数 (クラスター化インデックスが一意でない場合は + 1)</span><span class="sxs-lookup"><span data-stu-id="eed01-189">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + number of variable-length clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="eed01-190">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 非クラスター化インデックスのキー列のセットに含まれていない可変長クラスター化キー列のバイト サイズ (クラスター化インデックスが一意でない場合は + 4)</span><span class="sxs-lookup"><span data-stu-id="eed01-190">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + size in bytes of the variable-length clustering key columns not in the set of nonclustered index key columns (+ 4 if the clustered index is nonunique)</span></span>  
  
3.  <span data-ttu-id="eed01-191">次のように、NULL ビットマップのサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-191">Calculate the null bitmap size:</span></span>  
  
     <span data-ttu-id="eed01-192">***Leaf_Null_Bitmap***  = 2 + ((***Num_Leaf_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="eed01-192">***Leaf_Null_Bitmap***  = 2 + ((***Num_Leaf_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="eed01-193">上記の式の計算結果は、整数部分だけを使用します。</span><span class="sxs-lookup"><span data-stu-id="eed01-193">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="eed01-194">小数部分は無視してください。</span><span class="sxs-lookup"><span data-stu-id="eed01-194">Discard any remainder.</span></span>  
  
4.  <span data-ttu-id="eed01-195">可変長データ サイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-195">Calculate the variable length data size:</span></span>  
  
     <span data-ttu-id="eed01-196">上記の手順 2.2. で説明した必要なクラスター化キー列を含め、インデックス キーに可変長列が存在する場合は、インデックス行内の可変長列を格納するのに使用する領域を次の式で計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-196">If there are variable-length columns in the index key, including any necessary clustering key columns as described previously in Step 2.2, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="eed01-197">***Variable_Leaf_Size***  = 2 + (***Num_Variable_Leaf_Cols*** x 2) + ***Max_Var_Leaf_Size***</span><span class="sxs-lookup"><span data-stu-id="eed01-197">***Variable_Leaf_Size***  = 2 + (***Num_Variable_Leaf_Cols*** x 2) + ***Max_Var_Leaf_Size***</span></span>  
  
     <span data-ttu-id="eed01-198">***Max_Var_Key_Size*** に追加されたバイトは、それぞれの可変長列を追跡するためのものです。この式は、すべての可変長列がいっぱいになることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="eed01-198">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable column.This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="eed01-199">可変長列の格納領域の使用率が少ないことが予想される場合、その使用率に基づいて ***Max_Var_Leaf_Size*** の値を調整し、テーブルの全体サイズをより正確に見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="eed01-199">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Leaf_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="eed01-200">可変長列が存在しない場合は、 ***Variable_Leaf_Size*** に 0 を設定します。</span><span class="sxs-lookup"><span data-stu-id="eed01-200">If there are no variable-length columns, set ***Variable_Leaf_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="eed01-201">次の式でインデックス行のサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-201">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="eed01-202">***Leaf_Row_Size***   = ***Fixed_Leaf_Size***  + ***Variable_Leaf_Size***  + ***Leaf_Null_Bitmap*** + 1 (インデックス行の行ヘッダーオーバーヘッド) + 6 (子ページ ID のポインター)</span><span class="sxs-lookup"><span data-stu-id="eed01-202">***Leaf_Row_Size***  = ***Fixed_Leaf_Size*** + ***Variable_Leaf_Size*** + ***Leaf_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
6.  <span data-ttu-id="eed01-203">次の式で、1 ページあたりのインデックス行数を計算します (1 ページあたりの空きバイト数は 8,096 です)。</span><span class="sxs-lookup"><span data-stu-id="eed01-203">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="eed01-204">***Leaf_Rows_Per_Page***  = 8096 / (***Leaf_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="eed01-204">***Leaf_Rows_Per_Page***  = 8096 / (***Leaf_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="eed01-205">インデックス行は複数のページにまたがらないため、計算結果の端数は切り捨ててください。</span><span class="sxs-lookup"><span data-stu-id="eed01-205">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="eed01-206">上の式の 2 という値は、ページのスロット配列内にある行の入力用です。</span><span class="sxs-lookup"><span data-stu-id="eed01-206">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
7.  <span data-ttu-id="eed01-207">指定した [FILL FACTOR](../indexes/specify-fill-factor-for-an-index.md) に基づいて、1 ページあたりの予約済みの空き行数を次の式で計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-207">Calculate the number of reserved free rows per page, based on the [fill factor](../indexes/specify-fill-factor-for-an-index.md) specified:</span></span>  
  
     <span data-ttu-id="eed01-208">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Leaf_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="eed01-208">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Leaf_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="eed01-209">計算で使用する FILL FACTOR は、パーセンテージではなく整数値です。</span><span class="sxs-lookup"><span data-stu-id="eed01-209">The fill factor used in the calculation is an integer value instead of a percentage.</span></span> <span data-ttu-id="eed01-210">行は複数のページにまたがらないので、計算結果の端数は切り捨ててください。</span><span class="sxs-lookup"><span data-stu-id="eed01-210">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="eed01-211">FILL FACTOR の値が大きくなるほど、各ページに格納できるデータの量が多くなり、ページ数は少なくなります。</span><span class="sxs-lookup"><span data-stu-id="eed01-211">As the fill factor grows, more data will be stored on each page and there will be fewer pages.</span></span> <span data-ttu-id="eed01-212">上の式の 2 という値は、ページのスロット配列内にある行の入力用です。</span><span class="sxs-lookup"><span data-stu-id="eed01-212">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
8.  <span data-ttu-id="eed01-213">次の式で、すべての行を格納するために必要なページ数を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-213">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="eed01-214">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Leaf_Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="eed01-214">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Leaf_Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="eed01-215">算出したページ数の端数は切り上げてください。</span><span class="sxs-lookup"><span data-stu-id="eed01-215">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
9. <span data-ttu-id="eed01-216">次の式で、インデックスのサイズを計算します (1 ページあたりの総バイト数は 8,192 です)。</span><span class="sxs-lookup"><span data-stu-id="eed01-216">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="eed01-217">***Leaf_Space_Used***  = 8192 x ***Num_Leaf_Pages***</span><span class="sxs-lookup"><span data-stu-id="eed01-217">***Leaf_Space_Used***  = 8192 x ***Num_Leaf_Pages***</span></span>  
  
## <a name="step-3-calculate-the-space-used-to-store-index-information-in-the-non-leaf-levels"></a><span data-ttu-id="eed01-218">手順 3.</span><span class="sxs-lookup"><span data-stu-id="eed01-218">Step 3.</span></span> <span data-ttu-id="eed01-219">非リーフ レベルのインデックス情報の格納に使用する領域を計算する</span><span class="sxs-lookup"><span data-stu-id="eed01-219">Calculate the Space Used to Store Index Information in the Non-leaf Levels</span></span>  
 <span data-ttu-id="eed01-220">インデックスの中間レベルおよびルート レベルを格納するために必要な領域を算出するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="eed01-220">Follow these steps to estimate the amount of space that is required to store the intermediate and root levels of the index.</span></span> <span data-ttu-id="eed01-221">この手順を完了するには、手順 2. および 3. で控えた値が必要になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-221">You will need the values preserved from steps 2 and 3 to complete this step.</span></span>  
  
1.  <span data-ttu-id="eed01-222">次の式で、インデックス内の非レベル数を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-222">Calculate the number of non-leaf levels in the index:</span></span>  
  
     <span data-ttu-id="eed01-223">***非リーフレベル***= 1 + ログ Index_Rows_Per_Page (***Num_Leaf_Pages***  /  ***Index_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="eed01-223">***Non-leaf Levels***  = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages*** / ***Index_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="eed01-224">この値を最も近い整数に切り上げます。</span><span class="sxs-lookup"><span data-stu-id="eed01-224">Round this value up to the nearest whole number.</span></span> <span data-ttu-id="eed01-225">この値には、非クラスター化インデックスのリーフ レベルは含まれません。</span><span class="sxs-lookup"><span data-stu-id="eed01-225">This value does not include the leaf level of the nonclustered index.</span></span>  
  
2.  <span data-ttu-id="eed01-226">次の式で、インデックス内の非リーフ ページ数を計算します。</span><span class="sxs-lookup"><span data-stu-id="eed01-226">Calculate the number of non-leaf pages in the index:</span></span>  
  
     <span data-ttu-id="eed01-227">***Num_Index_Pages*** = ∑ level (***Num_Leaf_Pages/Index_Rows_Per_Page***<sup>レベル</sup>)、1 <***= レベル <= レベル***</span><span class="sxs-lookup"><span data-stu-id="eed01-227">***Num_Index_Pages***  = ∑Level (***Num_Leaf_Pages/Index_Rows_Per_Page***<sup>Level</sup>)where 1 <= Level <= ***Levels***</span></span>  
  
     <span data-ttu-id="eed01-228">それぞれの値を最も近い整数に切り上げます。</span><span class="sxs-lookup"><span data-stu-id="eed01-228">Round each summand up to the nearest whole number.</span></span> <span data-ttu-id="eed01-229">簡単な例として、 ***Num_Leaf_Pages*** = 1000、 ***Index_Rows_Per_Page*** = 25 のインデックスを例に取ります。</span><span class="sxs-lookup"><span data-stu-id="eed01-229">As a simple example, consider an index where ***Num_Leaf_Pages*** = 1000 and ***Index_Rows_Per_Page*** = 25.</span></span> <span data-ttu-id="eed01-230">リーフ レベルより上位の最初のインデックス レベルでは、1000 行のインデックス行が格納されます。リーフ ページあたり 1 行のインデックス行で、1 ページあたり 25 行のインデックス行を納めることができます。</span><span class="sxs-lookup"><span data-stu-id="eed01-230">The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page.</span></span> <span data-ttu-id="eed01-231">つまり、1,000 行のインデックス行を格納するために 40 ページが必要になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-231">This means that 40 pages are required to store those 1000 index rows.</span></span> <span data-ttu-id="eed01-232">次のレベルのインデックスでは、40 行のインデックス行を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eed01-232">The next level of the index has to store 40 rows.</span></span> <span data-ttu-id="eed01-233">つまり、2 ページが必要になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-233">This means that it requires 2 pages.</span></span> <span data-ttu-id="eed01-234">最上位レベルのインデックスでは、2 行のインデックス行を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eed01-234">The final level of the index has to store 2 rows.</span></span> <span data-ttu-id="eed01-235">つまり、1 ページが必要になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-235">This means that it requires 1 page.</span></span> <span data-ttu-id="eed01-236">その結果、非リーフ インデックス ページは 43 ページとなります。</span><span class="sxs-lookup"><span data-stu-id="eed01-236">This yields 43 non-leaf index pages.</span></span> <span data-ttu-id="eed01-237">このような数値を前の式で使用すると、次のような結果になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-237">When these numbers are used in the previous formulas, the result is as follows:</span></span>  
  
     <span data-ttu-id="eed01-238">***非 leaf_Levels*** = 1 + log25 (1000/25) = 3</span><span class="sxs-lookup"><span data-stu-id="eed01-238">***Non-leaf_Levels***  = 1 + log25 (1000 / 25) = 3</span></span>  
  
     <span data-ttu-id="eed01-239">***Num_Index_Pages*** = 1000/(25<sup>3</sup>) + 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43 (例で説明したページ数)。</span><span class="sxs-lookup"><span data-stu-id="eed01-239">***Num_Index_Pages*** = 1000/(25<sup>3</sup>)+ 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43, which is the number of pages described in the example.</span></span>  
  
3.  <span data-ttu-id="eed01-240">次の式で、インデックスのサイズを計算します (1 ページあたりの総バイト数は 8,192 です)。</span><span class="sxs-lookup"><span data-stu-id="eed01-240">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="eed01-241">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span><span class="sxs-lookup"><span data-stu-id="eed01-241">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span></span>  
  
## <a name="step-4-total-the-calculated-values"></a><span data-ttu-id="eed01-242">手順 4.</span><span class="sxs-lookup"><span data-stu-id="eed01-242">Step 4.</span></span> <span data-ttu-id="eed01-243">計算した値を合計します。</span><span class="sxs-lookup"><span data-stu-id="eed01-243">Total the Calculated Values</span></span>  
 <span data-ttu-id="eed01-244">次の式で、上記の 2 つの手順から取得した値を合計します。</span><span class="sxs-lookup"><span data-stu-id="eed01-244">Total the values obtained from the previous two steps:</span></span>  
  
 <span data-ttu-id="eed01-245">非クラスター化インデックス サイズ (バイト) = ***Leaf_Space_Used*** + ***Index_Space_used***</span><span class="sxs-lookup"><span data-stu-id="eed01-245">Nonclustered index size (bytes) = ***Leaf_Space_Used*** + ***Index_Space_used***</span></span>  
  
 <span data-ttu-id="eed01-246">この計算では、次のことは考慮されていません。</span><span class="sxs-lookup"><span data-stu-id="eed01-246">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="eed01-247">パーティション分割</span><span class="sxs-lookup"><span data-stu-id="eed01-247">Partitioning</span></span>  
  
     <span data-ttu-id="eed01-248">パーティション分割による領域のオーバーヘッドはわずかですが、計算が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="eed01-248">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="eed01-249">これは、計算に含めるほど重要なことではありません。</span><span class="sxs-lookup"><span data-stu-id="eed01-249">It is not important to include.</span></span>  
  
-   <span data-ttu-id="eed01-250">アロケーション ページ</span><span class="sxs-lookup"><span data-stu-id="eed01-250">Allocation pages</span></span>  
  
     <span data-ttu-id="eed01-251">ヒープに割り当てられたページの追跡に使用する IAM ページが少なくとも 1 ページありますが、使用される IAM ページ数を正確に計算できるアルゴリズムはなく、領域のオーバーヘッドはわずかです。</span><span class="sxs-lookup"><span data-stu-id="eed01-251">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="eed01-252">ラージ オブジェクト (LOB) の値</span><span class="sxs-lookup"><span data-stu-id="eed01-252">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="eed01-253">LOB データ型の `varchar(max)`、`varbinary(max)`、`nvarchar(max)`、`text`、`ntext`、`xml`、および `image` の値を格納するために使用される領域を正確に特定するのアルゴリズムは複雑です。</span><span class="sxs-lookup"><span data-stu-id="eed01-253">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml`, and `image` values is complex.</span></span> <span data-ttu-id="eed01-254">LOB データ型の値で使用される領域の計算は、想定される LOB 値の平均サイズを合計し、 ***Num_Rows***で乗算し、非クラスター化インデックスの合計サイズに加算するだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="eed01-254">It is sufficient to just add the average size of the LOB values expected, multiply by ***Num_Rows***, and add that to the total nonclustered index size.</span></span>  
  
-   <span data-ttu-id="eed01-255">圧縮</span><span class="sxs-lookup"><span data-stu-id="eed01-255">Compression</span></span>  
  
     <span data-ttu-id="eed01-256">圧縮されたインデックスのサイズを事前に計算することはできません。</span><span class="sxs-lookup"><span data-stu-id="eed01-256">You cannot pre-calculate the size of a compressed index.</span></span>  
  
-   <span data-ttu-id="eed01-257">スパース列</span><span class="sxs-lookup"><span data-stu-id="eed01-257">Sparse columns</span></span>  
  
     <span data-ttu-id="eed01-258">スパース列の領域要件については、「 [スパース列の使用](../tables/use-sparse-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed01-258">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed01-259">参照</span><span class="sxs-lookup"><span data-stu-id="eed01-259">See Also</span></span>  
 <span data-ttu-id="eed01-260">[クラスター化インデックスと非クラスター化インデックスの概念](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="eed01-260">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="eed01-261">[非クラスター化インデックスの作成](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="eed01-261">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="eed01-262">[クラスター化インデックスの作成](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="eed01-262">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="eed01-263">[テーブル サイズの見積もり](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="eed01-263">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="eed01-264">[クラスター化インデックスのサイズの見積もり](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="eed01-264">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 <span data-ttu-id="eed01-265">[ヒープ サイズの見積もり](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="eed01-265">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 [<span data-ttu-id="eed01-266">データベース サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="eed01-266">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
