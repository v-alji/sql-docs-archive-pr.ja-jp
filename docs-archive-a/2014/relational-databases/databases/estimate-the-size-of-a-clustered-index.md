---
title: クラスター化インデックスのサイズの見積もり | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- disk space [SQL Server], indexes
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- space [SQL Server], indexes
- clustered indexes, table size
- nonclustered indexes [SQL Server], table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: 2b5137f8-98ad-46b5-9aae-4c980259bf8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d224c5ae55cc5ec7690ca0962cbc2130bac22e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742190"
---
# <a name="estimate-the-size-of-a-clustered-index"></a><span data-ttu-id="912ac-102">クラスター化インデックスのサイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="912ac-102">Estimate the Size of a Clustered Index</span></span>
  <span data-ttu-id="912ac-103">クラスター化インデックスにデータを格納するために必要な領域を見積もるには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="912ac-103">You can use the following steps to estimate the amount of space that is required to store data in a clustered index:</span></span>  
  
1.  <span data-ttu-id="912ac-104">クラスター化インデックスのリーフ レベルにデータを格納するために使用する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-104">Calculate the space used to store data in the leaf level of the clustered index.</span></span>  
  
2.  <span data-ttu-id="912ac-105">クラスター化インデックスのインデックス情報を格納するために使用する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-105">Calculate the space used to store index information for the clustered index.</span></span>  
  
3.  <span data-ttu-id="912ac-106">計算した値を合計します。</span><span class="sxs-lookup"><span data-stu-id="912ac-106">Total the calculated values.</span></span>  
  
## <a name="step-1-calculate-the-space-used-to-store-data-in-the-leaf-level"></a><span data-ttu-id="912ac-107">手順 1.</span><span class="sxs-lookup"><span data-stu-id="912ac-107">Step 1.</span></span> <span data-ttu-id="912ac-108">リーフ レベルにデータを格納するために使用する領域を計算する</span><span class="sxs-lookup"><span data-stu-id="912ac-108">Calculate the Space Used to Store Data in the Leaf Level</span></span>  
  
1.  <span data-ttu-id="912ac-109">次のように、テーブル内の行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="912ac-109">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="912ac-110">***Num_Rows***  = テーブル内の行数</span><span class="sxs-lookup"><span data-stu-id="912ac-110">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="912ac-111">次のように、固定長列と可変長列の数を指定し、それらの列を格納するために必要な領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-111">Specify the number of fixed-length and variable-length columns and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="912ac-112">固定長列のグループと可変長列のグループがデータ行内で使用する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-112">Calculate the space that each of these groups of columns occupies within the data row.</span></span> <span data-ttu-id="912ac-113">列のサイズは、データ型と長さの指定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="912ac-113">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="912ac-114">***Num_Cols***  = 列 (固定長および可変長) の総数</span><span class="sxs-lookup"><span data-stu-id="912ac-114">***Num_Cols***  = total number of columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="912ac-115">***Fixed_Data_Size***  = すべての固定長列の合計バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="912ac-115">***Fixed_Data_Size***  = total byte size of all fixed-length columns</span></span>  
  
     <span data-ttu-id="912ac-116">***Num_Variable_Cols***  = 可変長列の数</span><span class="sxs-lookup"><span data-stu-id="912ac-116">***Num_Variable_Cols***  = number of variable-length columns</span></span>  
  
     <span data-ttu-id="912ac-117">***Max_Var_Size***  = すべての可変長列の最大バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="912ac-117">***Max_Var_Size***  = maximum byte size of all variable-length columns</span></span>  
  
3.  <span data-ttu-id="912ac-118">クラスター化インデックスが一意でない場合、次のように *uniqueifier* 列を計上します。</span><span class="sxs-lookup"><span data-stu-id="912ac-118">If the clustered index is nonunique, account for the *uniqueifier* column:</span></span>  
  
     <span data-ttu-id="912ac-119">uniqueifier とは、NULL 値が許容された可変長列です。</span><span class="sxs-lookup"><span data-stu-id="912ac-119">The uniqueifier is a nullable, variable-length column.</span></span> <span data-ttu-id="912ac-120">一意でないキー値を含む行では、uniqueifier は NULL 値を許容しない 4 バイトの列になります。</span><span class="sxs-lookup"><span data-stu-id="912ac-120">It will be nonnull and 4 bytes in size in rows that have nonunique key values.</span></span> <span data-ttu-id="912ac-121">この値はインデックス キーの一部で、すべての行に一意のキー値が含まれるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="912ac-121">This value is part of the index key and is required to make sure that every row has a unique key value.</span></span>  
  
     <span data-ttu-id="912ac-122">***Num_Cols***  = ***Num_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="912ac-122">***Num_Cols***  = ***Num_Cols*** + 1</span></span>  
  
     <span data-ttu-id="912ac-123">***Num_Variable_Cols***  = ***Num_Variable_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="912ac-123">***Num_Variable_Cols***  = ***Num_Variable_Cols*** + 1</span></span>  
  
     <span data-ttu-id="912ac-124">***Max_Var_Size***  = ***Max_Var_Size*** + 4</span><span class="sxs-lookup"><span data-stu-id="912ac-124">***Max_Var_Size***  = ***Max_Var_Size*** + 4</span></span>  
  
     <span data-ttu-id="912ac-125">このような変更は、すべての値が一意でなくなることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="912ac-125">These modifications assume that all values will be nonunique.</span></span>  
  
4.  <span data-ttu-id="912ac-126">NULL ビットマップと呼ばれる行の部分は、列の NULL 値の許容を管理するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="912ac-126">Part of the row, known as the null bitmap, is reserved to manage column nullability.</span></span> <span data-ttu-id="912ac-127">このサイズは次のように計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-127">Calculate its size:</span></span>  
  
     <span data-ttu-id="912ac-128">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="912ac-128">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="912ac-129">上記の式の計算結果の整数部分だけを使用し、小数部分は無視してください。</span><span class="sxs-lookup"><span data-stu-id="912ac-129">Only the integer part of the previous expression should be used; discard any remainder.</span></span>  
  
5.  <span data-ttu-id="912ac-130">次の式で、可変長のデータ サイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-130">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="912ac-131">テーブル内に可変長列が存在する場合、次の式を使用して、行内でそれらの列を格納するために使用する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-131">If there are variable-length columns in the table, determine how much space is used to store the columns within the row:</span></span>  
  
     <span data-ttu-id="912ac-132">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span><span class="sxs-lookup"><span data-stu-id="912ac-132">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span></span>  
  
     <span data-ttu-id="912ac-133">***Max_Var_Size*** に追加されたバイトは、それぞれの可変長列を追跡するためのものです。</span><span class="sxs-lookup"><span data-stu-id="912ac-133">The bytes added to ***Max_Var_Size*** are for tracking each variable column.</span></span> <span data-ttu-id="912ac-134">この式は、すべての可変長列がいっぱいになることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="912ac-134">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="912ac-135">可変長列の格納領域の使用率が 100% 以下になることが予想される場合、その使用率に基づいて ***Max_Var_Size*** の値を調整し、テーブルの全体サイズをより正確に見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="912ac-135">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="912ac-136">定義済みのテーブルの合計サイズが 8,060 バイトを超える `varchar`、`nvarchar`、`varbinary`、または `sql_variant` 列の連結が可能です。</span><span class="sxs-lookup"><span data-stu-id="912ac-136">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="912ac-137">この場合も、`varchar`、`varbinary`、または `sql_variant` 列の場合は 8,000 バイト、`nvarchar` 列の場合は 4,000 バイトの制限内に、各列のサイズを収める必要があります。</span><span class="sxs-lookup"><span data-stu-id="912ac-137">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `varbinary`, or `sql_variant` column, and 4,000 bytes for `nvarchar` columns.</span></span> <span data-ttu-id="912ac-138">ただし、これらの列を連結したサイズは、テーブルの制限である 8,060 バイトを超過してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="912ac-138">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span>  
  
     <span data-ttu-id="912ac-139">可変長列が存在しない場合は、 ***Variable_Data_Size*** に 0 を設定します。</span><span class="sxs-lookup"><span data-stu-id="912ac-139">If there are no variable-length columns, set ***Variable_Data_Size*** to 0.</span></span>  
  
6.  <span data-ttu-id="912ac-140">次の式で行サイズの合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-140">Calculate the total row size:</span></span>  
  
     <span data-ttu-id="912ac-141">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span><span class="sxs-lookup"><span data-stu-id="912ac-141">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span></span>  
  
     <span data-ttu-id="912ac-142">4 という値は、データ行の行ヘッダー オーバーヘッドです。</span><span class="sxs-lookup"><span data-stu-id="912ac-142">The value 4 is the row header overhead of a data row.</span></span>  
  
7.  <span data-ttu-id="912ac-143">次の式で、1 ページあたりの行数を計算します (1 ページあたりの空きバイト数は 8,096 です)。</span><span class="sxs-lookup"><span data-stu-id="912ac-143">Calculate the number of rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="912ac-144">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="912ac-144">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="912ac-145">行は複数のページにまたがらないので、計算結果の端数は切り捨ててください。</span><span class="sxs-lookup"><span data-stu-id="912ac-145">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="912ac-146">上記の式の 2 という値は、ページのスロット配列内の行のエントリのためのものです。</span><span class="sxs-lookup"><span data-stu-id="912ac-146">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
8.  <span data-ttu-id="912ac-147">指定した [FILL FACTOR](../indexes/specify-fill-factor-for-an-index.md) に基づいて、1 ページあたりの予約済みの空き行数を次の式で計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-147">Calculate the number of reserved free rows per page, based on the [fill factor](../indexes/specify-fill-factor-for-an-index.md) specified:</span></span>  
  
     <span data-ttu-id="912ac-148">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="912ac-148">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="912ac-149">計算で使用する FILL FACTOR は、パーセンテージではなく整数値です。</span><span class="sxs-lookup"><span data-stu-id="912ac-149">The fill factor used in the calculation is an integer value instead of a percentage.</span></span> <span data-ttu-id="912ac-150">行は複数のページにまたがらないので、計算結果の端数は切り捨ててください。</span><span class="sxs-lookup"><span data-stu-id="912ac-150">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="912ac-151">FILL FACTOR の値が大きくなるほど、各ページに格納できるデータの量が多くなり、ページ数は少なくなります。</span><span class="sxs-lookup"><span data-stu-id="912ac-151">As the fill factor grows, more data will be stored on each page and there will be fewer pages.</span></span> <span data-ttu-id="912ac-152">上記の式の 2 という値は、ページのスロット配列内の行のエントリのためのものです。</span><span class="sxs-lookup"><span data-stu-id="912ac-152">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
9. <span data-ttu-id="912ac-153">次の式で、すべての行を格納するために必要なページ数を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-153">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="912ac-154">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="912ac-154">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="912ac-155">算出したページ数の端数は切り上げてください。</span><span class="sxs-lookup"><span data-stu-id="912ac-155">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
10. <span data-ttu-id="912ac-156">次の式で、リーフ レベルにデータを格納するために必要な領域を計算します (1 ページあたりの総バイト数は 8,192 です)。</span><span class="sxs-lookup"><span data-stu-id="912ac-156">Calculate the amount of space that is required to store the data in the leaf level (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="912ac-157">***Leaf_space_used***  = 8192 x ***Num_Leaf_Pages***</span><span class="sxs-lookup"><span data-stu-id="912ac-157">***Leaf_space_used***  = 8192 x ***Num_Leaf_Pages***</span></span>  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information"></a><span data-ttu-id="912ac-158">手順 2.</span><span class="sxs-lookup"><span data-stu-id="912ac-158">Step 2.</span></span> <span data-ttu-id="912ac-159">インデックス情報を格納するために使用する領域を計算する</span><span class="sxs-lookup"><span data-stu-id="912ac-159">Calculate the Space Used to Store Index Information</span></span>  
 <span data-ttu-id="912ac-160">次の手順を実行して、上位レベルのインデックスを格納するために必要な領域を見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="912ac-160">You can use the following steps to estimate the amount of space that is required to store the upper levels of the index:</span></span>  
  
1.  <span data-ttu-id="912ac-161">次のように、インデックス キーの固定長列と可変長列の数を指定し、それらの列の格納に必要な領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-161">Specify the number of fixed-length and variable-length columns in the index key and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="912ac-162">インデックスのキー列には、固定長列と可変長列を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="912ac-162">The key columns of an index can include fixed-length and variable-length columns.</span></span> <span data-ttu-id="912ac-163">内部レベルのインデックス行サイズを見積もるには、これらの各列グループによってインデックス行内で占有される領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-163">To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row.</span></span> <span data-ttu-id="912ac-164">列のサイズは、データ型と長さの指定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="912ac-164">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="912ac-165">***Num_Key_Cols***  = キー列 (固定長および可変長) の総数</span><span class="sxs-lookup"><span data-stu-id="912ac-165">***Num_Key_Cols***  = total number of key columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="912ac-166">***Fixed_Key_Size***  = すべての固定長キー列の合計バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="912ac-166">***Fixed_Key_Size***  = total byte size of all fixed-length key columns</span></span>  
  
     <span data-ttu-id="912ac-167">***Num_Variable_Key_Cols***  = 可変長キー列の数</span><span class="sxs-lookup"><span data-stu-id="912ac-167">***Num_Variable_Key_Cols***  = number of variable-length key columns</span></span>  
  
     <span data-ttu-id="912ac-168">***Max_Var_Key_Size***  = すべての可変長キー列の最大バイト サイズ</span><span class="sxs-lookup"><span data-stu-id="912ac-168">***Max_Var_Key_Size***  = maximum byte size of all variable-length key columns</span></span>  
  
2.  <span data-ttu-id="912ac-169">インデックスが一意でない場合は、次のように uniqueifier をすべて計上します。</span><span class="sxs-lookup"><span data-stu-id="912ac-169">Account for any uniqueifier needed if the index is nonunique:</span></span>  
  
     <span data-ttu-id="912ac-170">uniqueifier とは、NULL 値が許容された可変長列です。</span><span class="sxs-lookup"><span data-stu-id="912ac-170">The uniqueifier is a nullable, variable-length column.</span></span> <span data-ttu-id="912ac-171">一意でないインデックス キー値を含む行では、uniqueifier は NULL 値を許容しない 4 バイトの列になります。</span><span class="sxs-lookup"><span data-stu-id="912ac-171">It will be nonnull and 4 bytes in size in rows that have nonunique index key values.</span></span> <span data-ttu-id="912ac-172">この値はインデックス キーの一部で、すべての行に一意のキー値が含まれるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="912ac-172">This value is part of the index key and is required to make sure that every row has a unique key value.</span></span>  
  
     <span data-ttu-id="912ac-173">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="912ac-173">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="912ac-174">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="912ac-174">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="912ac-175">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 4</span><span class="sxs-lookup"><span data-stu-id="912ac-175">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 4</span></span>  
  
     <span data-ttu-id="912ac-176">このような変更は、すべての値が一意でなくなることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="912ac-176">These modifications assume that all values will be nonunique.</span></span>  
  
3.  <span data-ttu-id="912ac-177">次のように、NULL ビットマップのサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-177">Calculate the null bitmap size:</span></span>  
  
     <span data-ttu-id="912ac-178">インデックス キー内に NULL 値を許容する列が存在する場合、インデックス行の部分は NULL ビットマップ用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="912ac-178">If there are nullable columns in the index key, part of the index row is reserved for the null bitmap.</span></span> <span data-ttu-id="912ac-179">このサイズは次のように計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-179">Calculate its size:</span></span>  
  
     <span data-ttu-id="912ac-180">***Index_Null_Bitmap***  = 2 + ((インデックス行の列数 + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="912ac-180">***Index_Null_Bitmap***  = 2 + ((number of columns in the index row + 7) / 8)</span></span>  
  
     <span data-ttu-id="912ac-181">上記の式の計算結果は、整数部分だけを使用します。</span><span class="sxs-lookup"><span data-stu-id="912ac-181">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="912ac-182">小数部分は無視してください。</span><span class="sxs-lookup"><span data-stu-id="912ac-182">Discard any remainder.</span></span>  
  
     <span data-ttu-id="912ac-183">NULL 値を許容するキー列が存在しない場合は、 ***Index_Null_Bitmap*** を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="912ac-183">If there are no nullable key columns, set ***Index_Null_Bitmap*** to 0.</span></span>  
  
4.  <span data-ttu-id="912ac-184">次の式で、可変長のデータ サイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-184">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="912ac-185">インデックス内に可変長列が存在する場合は、インデックス行内にそれらの列を格納するために使用する領域を次の式で計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-185">If there are variable-length columns in the index, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="912ac-186">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="912ac-186">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="912ac-187">***Max_Var_Key_Size*** に追加されたバイトは、それぞれの可変長列を追跡するためのものです。</span><span class="sxs-lookup"><span data-stu-id="912ac-187">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable-length column.</span></span> <span data-ttu-id="912ac-188">この式は、すべての可変長列がいっぱいになることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="912ac-188">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="912ac-189">可変長列の格納領域の使用率が 100% 以下になることが予想される場合、その使用率に基づいて ***Max_Var_Key_Size*** の値を調整し、テーブルの全体サイズをより正確に見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="912ac-189">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Key_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="912ac-190">可変長列が存在しない場合は、 ***Variable_Key_Size*** に 0 を設定します。</span><span class="sxs-lookup"><span data-stu-id="912ac-190">If there are no variable-length columns, set ***Variable_Key_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="912ac-191">次の式でインデックス行のサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-191">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="912ac-192">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (インデックス行の行ヘッダー オーバーヘッド) + 6 (子ページ ID のポインター)</span><span class="sxs-lookup"><span data-stu-id="912ac-192">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
6.  <span data-ttu-id="912ac-193">次の式で、1 ページあたりのインデックス行数を計算します (1 ページあたりの空きバイト数は 8,096 です)。</span><span class="sxs-lookup"><span data-stu-id="912ac-193">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="912ac-194">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="912ac-194">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="912ac-195">インデックス行は複数のページにまたがらないため、計算結果の端数は切り捨ててください。</span><span class="sxs-lookup"><span data-stu-id="912ac-195">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="912ac-196">上の式の 2 という値は、ページのスロット配列内にある行の入力用です。</span><span class="sxs-lookup"><span data-stu-id="912ac-196">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
7.  <span data-ttu-id="912ac-197">次の式で、インデックス内のレベル数を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-197">Calculate the number of levels in the index:</span></span>  
  
     <span data-ttu-id="912ac-198">***非 leaf_Levels*** = 1 + ログ Index_Rows_Per_Page (***Num_Leaf_Pages***  /  ***Index_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="912ac-198">***Non-leaf_Levels***  = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages*** / ***Index_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="912ac-199">この値を最も近い整数に切り上げます。</span><span class="sxs-lookup"><span data-stu-id="912ac-199">Round this value up to the nearest whole number.</span></span> <span data-ttu-id="912ac-200">この値には、クラスター化インデックスのリーフ レベルは含まれません。</span><span class="sxs-lookup"><span data-stu-id="912ac-200">This value does not include the leaf level of the clustered index.</span></span>  
  
8.  <span data-ttu-id="912ac-201">次の式で、インデックス内の非リーフ ページ数を計算します。</span><span class="sxs-lookup"><span data-stu-id="912ac-201">Calculate the number of non-leaf pages in the index:</span></span>  
  
     <span data-ttu-id="912ac-202">***Num_Index_Pages =*** ∑ level ***(Num_Leaf_Pages/(Index_Rows_Per_Page***<sup>レベル</sup>***))***</span><span class="sxs-lookup"><span data-stu-id="912ac-202">***Num_Index_Pages =*** ∑Level ***(Num_Leaf_Pages / (Index_Rows_Per_Page***<sup>Level</sup>***))***</span></span>  
  
     <span data-ttu-id="912ac-203">ここで、1 <= Level <= ***Non-leaf_Levels***</span><span class="sxs-lookup"><span data-stu-id="912ac-203">where 1 <= Level <= ***Non-leaf_Levels***</span></span>  
  
     <span data-ttu-id="912ac-204">それぞれの値を最も近い整数に切り上げます。</span><span class="sxs-lookup"><span data-stu-id="912ac-204">Round each summand up to the nearest whole number.</span></span> <span data-ttu-id="912ac-205">簡単な例として、 ***Num_Leaf_Pages*** = 1000、 ***Index_Rows_Per_Page*** = 25 のインデックスを例に取ります。</span><span class="sxs-lookup"><span data-stu-id="912ac-205">As a simple example, consider an index where ***Num_Leaf_Pages*** = 1000 and ***Index_Rows_Per_Page*** = 25.</span></span> <span data-ttu-id="912ac-206">リーフ レベルより上位の最初のインデックス レベルでは、1000 行のインデックス行が格納されます。リーフ ページあたり 1 行のインデックス行で、1 ページあたり 25 行のインデックス行を納めることができます。</span><span class="sxs-lookup"><span data-stu-id="912ac-206">The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page.</span></span> <span data-ttu-id="912ac-207">つまり、1,000 行のインデックス行を格納するために 40 ページが必要になります。</span><span class="sxs-lookup"><span data-stu-id="912ac-207">This means that 40 pages are required to store those 1000 index rows.</span></span> <span data-ttu-id="912ac-208">次のレベルのインデックスでは、40 行のインデックス行を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="912ac-208">The next level of the index has to store 40 rows.</span></span> <span data-ttu-id="912ac-209">つまり、2 ページが必要になります。</span><span class="sxs-lookup"><span data-stu-id="912ac-209">This means it requires 2 pages.</span></span> <span data-ttu-id="912ac-210">最上位レベルのインデックスでは、2 行のインデックス行を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="912ac-210">The final level of the index has to store 2 rows.</span></span> <span data-ttu-id="912ac-211">つまり、1 ページが必要になります。</span><span class="sxs-lookup"><span data-stu-id="912ac-211">This means it requires 1 page.</span></span> <span data-ttu-id="912ac-212">その結果、非リーフ インデックス ページは 43 ページとなります。</span><span class="sxs-lookup"><span data-stu-id="912ac-212">This gives 43 non-leaf index pages.</span></span> <span data-ttu-id="912ac-213">このような数値を前の式で使用すると、次のような結果になります。</span><span class="sxs-lookup"><span data-stu-id="912ac-213">When these numbers are used in the previous formulas, the outcome is as follows:</span></span>  
  
     <span data-ttu-id="912ac-214">***非 leaf_Levels*** = 1 + log25 (1000/25) = 3</span><span class="sxs-lookup"><span data-stu-id="912ac-214">***Non-leaf_Levels***  = 1 + log25 (1000 / 25) = 3</span></span>  
  
     <span data-ttu-id="912ac-215">***Num_Index_Pages*** = 1000/(25<sup>3</sup>) + 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43 (例で説明したページ数)。</span><span class="sxs-lookup"><span data-stu-id="912ac-215">***Num_Index_Pages*** = 1000/(25<sup>3</sup>)+ 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43, which is the number of pages described in the example.</span></span>  
  
9. <span data-ttu-id="912ac-216">次の式で、インデックスのサイズを計算します (1 ページあたりの総バイト数は 8,192 です)。</span><span class="sxs-lookup"><span data-stu-id="912ac-216">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="912ac-217">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span><span class="sxs-lookup"><span data-stu-id="912ac-217">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span></span>  
  
## <a name="step-3-total-the-calculated-values"></a><span data-ttu-id="912ac-218">手順 3.</span><span class="sxs-lookup"><span data-stu-id="912ac-218">Step 3.</span></span> <span data-ttu-id="912ac-219">計算した値を合計します。</span><span class="sxs-lookup"><span data-stu-id="912ac-219">Total the Calculated Values</span></span>  
 <span data-ttu-id="912ac-220">次の式で、上記の 2 つの手順から取得した値を合計します。</span><span class="sxs-lookup"><span data-stu-id="912ac-220">Total the values obtained from the previous two steps:</span></span>  
  
 <span data-ttu-id="912ac-221">クラスター化インデックス サイズ (バイト) = ***Leaf_Space_Used*** + ***Index_Space_used***</span><span class="sxs-lookup"><span data-stu-id="912ac-221">Clustered index size (bytes) = ***Leaf_Space_Used*** + ***Index_Space_used***</span></span>  
  
 <span data-ttu-id="912ac-222">この計算では、次のことは考慮されていません。</span><span class="sxs-lookup"><span data-stu-id="912ac-222">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="912ac-223">パーティション分割</span><span class="sxs-lookup"><span data-stu-id="912ac-223">Partitioning</span></span>  
  
     <span data-ttu-id="912ac-224">パーティション分割による領域のオーバーヘッドはわずかですが、計算が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="912ac-224">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="912ac-225">これは、計算に含めるほど重要なことではありません。</span><span class="sxs-lookup"><span data-stu-id="912ac-225">It is not important to include.</span></span>  
  
-   <span data-ttu-id="912ac-226">アロケーション ページ</span><span class="sxs-lookup"><span data-stu-id="912ac-226">Allocation pages</span></span>  
  
     <span data-ttu-id="912ac-227">ヒープに割り当てられたページの追跡に使用する IAM ページが少なくとも 1 ページありますが、使用される IAM ページ数を正確に計算できるアルゴリズムはなく、領域のオーバーヘッドはわずかです。</span><span class="sxs-lookup"><span data-stu-id="912ac-227">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="912ac-228">ラージ オブジェクト (LOB) の値</span><span class="sxs-lookup"><span data-stu-id="912ac-228">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="912ac-229">LOB データ型の `varchar(max)`、`varbinary(max)`、`nvarchar(max)`、`text`、`ntext`、`xml`、および `image` の値を格納するために使用される領域を正確に特定するのアルゴリズムは複雑です。</span><span class="sxs-lookup"><span data-stu-id="912ac-229">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml`, and `image` values is complex.</span></span> <span data-ttu-id="912ac-230">LOB データ型の値で使用される領域の計算は、必要な LOB 値の平均サイズを合計し、 ***Num_Rows***で乗算し、クラスター化インデックスの合計サイズに加算するだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="912ac-230">It is sufficient to just add the average size of the LOB values that are expected, multiply by ***Num_Rows***, and add that to the total clustered index size.</span></span>  
  
-   <span data-ttu-id="912ac-231">圧縮</span><span class="sxs-lookup"><span data-stu-id="912ac-231">Compression</span></span>  
  
     <span data-ttu-id="912ac-232">圧縮されたインデックスのサイズを事前に計算することはできません。</span><span class="sxs-lookup"><span data-stu-id="912ac-232">You cannot pre-calculate the size of a compressed index.</span></span>  
  
-   <span data-ttu-id="912ac-233">スパース列</span><span class="sxs-lookup"><span data-stu-id="912ac-233">Sparse columns</span></span>  
  
     <span data-ttu-id="912ac-234">スパース列の領域要件については、「 [スパース列の使用](../tables/use-sparse-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="912ac-234">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912ac-235">参照</span><span class="sxs-lookup"><span data-stu-id="912ac-235">See Also</span></span>  
 <span data-ttu-id="912ac-236">[クラスター化インデックスと非クラスター化インデックスの概念](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="912ac-236">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="912ac-237">[テーブル サイズの見積もり](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="912ac-237">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="912ac-238">[クラスター化インデックスの作成](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="912ac-238">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="912ac-239">[非クラスター化インデックスの作成](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="912ac-239">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="912ac-240">[非クラスター化インデックスのサイズの算出](estimate-the-size-of-a-nonclustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="912ac-240">[Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md) </span></span>  
 <span data-ttu-id="912ac-241">[ヒープ サイズの見積もり](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="912ac-241">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 [<span data-ttu-id="912ac-242">データベース サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="912ac-242">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
