---
title: スパース列の使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- sparse columns, described
- null columns
- sparse columns
ms.assetid: ea7ddb87-f50b-46b6-9f5a-acab222a2ede
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3068ac7a3094605bb809ac84c63766b64fda486
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640826"
---
# <a name="use-sparse-columns"></a><span data-ttu-id="bd8c7-102">スパース列の使用</span><span class="sxs-lookup"><span data-stu-id="bd8c7-102">Use Sparse Columns</span></span>
  <span data-ttu-id="bd8c7-103">スパース列は、NULL 値用にストレージが最適化されている通常の列です。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-103">Sparse columns are ordinary columns that have an optimized storage for null values.</span></span> <span data-ttu-id="bd8c7-104">スパース列によって、NULL 以外の値を取得するためのオーバーヘッドは増大しますが、NULL 値に必要となる領域は削減されます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-104">Sparse columns reduce the space requirements for null values at the cost of more overhead to retrieve nonnull values.</span></span> <span data-ttu-id="bd8c7-105">少なくとも 20 ～ 40% の領域を削減できる場合は、スパース列の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-105">Consider using sparse columns when the space saved is at least 20 percent to 40 percent.</span></span> <span data-ttu-id="bd8c7-106">スパース列および列セットを定義するには、 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) または [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-106">Sparse columns and column sets are defined by using the [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) or [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) statements.</span></span>  
  
 <span data-ttu-id="bd8c7-107">スパース列は、列セットおよびフィルター選択されたインデックスと併用できます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-107">Sparse columns can be used with column sets and filtered indexes:</span></span>  
  
-   <span data-ttu-id="bd8c7-108">列セット</span><span class="sxs-lookup"><span data-stu-id="bd8c7-108">Column sets</span></span>  
  
     <span data-ttu-id="bd8c7-109">INSERT、UPDATE、DELETE の各ステートメントは、スパース列を名前で参照できます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-109">INSERT, UPDATE, and DELETE statements can reference the sparse columns by name.</span></span> <span data-ttu-id="bd8c7-110">ただし、テーブルのすべてのスパース列を 1 つの XML 列に結合して表示および操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-110">However, you can also view and work with all the sparse columns of a table that are combined into a single XML column.</span></span> <span data-ttu-id="bd8c7-111">この列を列セットと呼びます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-111">This column is called a column set.</span></span> <span data-ttu-id="bd8c7-112">列セットの詳細については、「 [列セットの使用](../tables/use-column-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-112">For more information about column sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
-   <span data-ttu-id="bd8c7-113">フィルター選択されたインデックス</span><span class="sxs-lookup"><span data-stu-id="bd8c7-113">Filtered indexes</span></span>  
  
     <span data-ttu-id="bd8c7-114">スパース列は、NULL 値の行が多数あるため、フィルター選択されたインデックスに特に適しています。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-114">Because sparse columns have many null-valued rows, they are especially appropriate for filtered indexes.</span></span> <span data-ttu-id="bd8c7-115">スパース列でフィルター選択されたインデックスを使用すると、値が設定された行にのみインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-115">A filtered index on a sparse column can index only the rows that have populated values.</span></span> <span data-ttu-id="bd8c7-116">これにより、より小さく効率的なインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-116">This creates a smaller and more efficient index.</span></span> <span data-ttu-id="bd8c7-117">詳細については、「 [Create Filtered Indexes](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-117">For more information, see [Create Filtered Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="bd8c7-118">スパース列とフィルター選択されたインデックスを併用することで、 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]などのアプリケーションでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を使用して多数のユーザー定義プロパティを効率よく格納およびアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-118">Sparse columns and filtered indexes enable applications, such as [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], to efficiently store and access a large number of user-defined properties by using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="properties-of-sparse-columns"></a><span data-ttu-id="bd8c7-119">スパース列のプロパティ</span><span class="sxs-lookup"><span data-stu-id="bd8c7-119">Properties of Sparse Columns</span></span>  
 <span data-ttu-id="bd8c7-120">スパース列には次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-120">Sparse columns have the following characteristics:</span></span>  
  
-   <span data-ttu-id="bd8c7-121">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] は、列定義で SPARSE キーワードを使用して、その列での値のストレージを最適化します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-121">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses the SPARSE keyword in a column definition to optimize the storage of values in that column.</span></span> <span data-ttu-id="bd8c7-122">このため、列値が NULL である行がテーブルに含まれている場合、その値はストレージを必要としません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-122">Therefore, when the column value is NULL for any row in the table, the values require no storage.</span></span>  
  
-   <span data-ttu-id="bd8c7-123">スパース列を含んでいるテーブルのカタログ ビューは、一般的なテーブルのものと同じです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-123">Catalog views for a table that has sparse columns are the same as for a typical table.</span></span> <span data-ttu-id="bd8c7-124">sys.columns カタログ ビューは、テーブル内の各列の行で構成され、列セットが定義されていればそれを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-124">The sys.columns catalog view contains a row for each column in the table and includes a column set if one is defined.</span></span>  
  
-   <span data-ttu-id="bd8c7-125">スパース列は、論理テーブルではなく、ストレージ層のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-125">Sparse columns are a property of the storage layer, rather than the logical table.</span></span> <span data-ttu-id="bd8c7-126">したがって、SELECT...INTO ステートメントは、スパース列のプロパティを新しいテーブルにコピーしません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-126">Therefore a SELECT...INTO statement does not copy over the sparse column property into a new table.</span></span>  
  
-   <span data-ttu-id="bd8c7-127">COLUMNS_UPDATED 関数は、DML アクションで更新されたすべての列を示す `varbinary` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-127">The COLUMNS_UPDATED function returns a `varbinary` value to indicate all the columns that were updated during a DML action.</span></span> <span data-ttu-id="bd8c7-128">COLUMNS_UPDATED 関数から返されるビットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-128">The bits that are returned by the COLUMNS_UPDATED function are as follows:</span></span>  
  
    -   <span data-ttu-id="bd8c7-129">スパース列が明示的に更新された場合は、そのスパース列の対応するビットが 1 に設定され、列セットのビットが 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-129">When a sparse column is explicitly updated, the corresponding bit for that sparse column is set to 1, and the bit for the column set is set to 1.</span></span>  
  
    -   <span data-ttu-id="bd8c7-130">列セットが明示的に更新された場合は、列セットのビットが 1 に設定され、そのテーブル内のすべてのスパース列のビットが 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-130">When a column set is explicitly updated, the bit for the column set is set to 1, and the bits for all the sparse columns in that table are set to 1.</span></span>  
  
    -   <span data-ttu-id="bd8c7-131">挿入操作では、すべてのビットが 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-131">For insert operations, all bits are set to 1.</span></span>  
  
     <span data-ttu-id="bd8c7-132">列セットの詳細については、「 [列セットの使用](../tables/use-column-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-132">For more information about columns sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
 <span data-ttu-id="bd8c7-133">次のデータ型は SPARSE と指定できません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-133">The following data types cannot be specified as SPARSE:</span></span>  
  
|||  
|-|-|  
|`geography`|`text`|  
|`geometry`|`timestamp`|  
|`image`|`user-defined data types`|  
|`ntext`||  
  
## <a name="estimated-space-savings-by-data-type"></a><span data-ttu-id="bd8c7-134">領域を節約するためのデータ型別推定値</span><span class="sxs-lookup"><span data-stu-id="bd8c7-134">Estimated Space Savings by Data Type</span></span>  
 <span data-ttu-id="bd8c7-135">スパース列は、同一データが SPARSE とマークされていない場合に比べて、NULL 以外の値により多くのストレージ領域を必要とします。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-135">Sparse columns require more storage space for nonnull values than the space required for identical data that is not marked SPARSE.</span></span> <span data-ttu-id="bd8c7-136">次の表は、各データ型の使用領域を示したものです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-136">The following tables show the space usage for each data type.</span></span> <span data-ttu-id="bd8c7-137">**NULL の比率** 列は、正味 40% の領域を節約するために必要な NULL データの割合を示します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-137">The **NULL Percentage** column indicates what percent of the data must be NULL for a net space savings of 40 percent.</span></span>  
  
 <span data-ttu-id="bd8c7-138">**固定長データ型**</span><span class="sxs-lookup"><span data-stu-id="bd8c7-138">**Fixed-Length Data Types**</span></span>  
  
|<span data-ttu-id="bd8c7-139">データ型</span><span class="sxs-lookup"><span data-stu-id="bd8c7-139">Data type</span></span>|<span data-ttu-id="bd8c7-140">非スパース バイト数</span><span class="sxs-lookup"><span data-stu-id="bd8c7-140">Nonsparse bytes</span></span>|<span data-ttu-id="bd8c7-141">スパース バイト数</span><span class="sxs-lookup"><span data-stu-id="bd8c7-141">Sparse bytes</span></span>|<span data-ttu-id="bd8c7-142">NULL の比率</span><span class="sxs-lookup"><span data-stu-id="bd8c7-142">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`bit`|<span data-ttu-id="bd8c7-143">0.125</span><span class="sxs-lookup"><span data-stu-id="bd8c7-143">0.125</span></span>|<span data-ttu-id="bd8c7-144">5</span><span class="sxs-lookup"><span data-stu-id="bd8c7-144">5</span></span>|<span data-ttu-id="bd8c7-145">98%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-145">98%</span></span>|  
|`tinyint`|<span data-ttu-id="bd8c7-146">1</span><span class="sxs-lookup"><span data-stu-id="bd8c7-146">1</span></span>|<span data-ttu-id="bd8c7-147">5</span><span class="sxs-lookup"><span data-stu-id="bd8c7-147">5</span></span>|<span data-ttu-id="bd8c7-148">86%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-148">86%</span></span>|  
|`smallint`|<span data-ttu-id="bd8c7-149">2</span><span class="sxs-lookup"><span data-stu-id="bd8c7-149">2</span></span>|<span data-ttu-id="bd8c7-150">6</span><span class="sxs-lookup"><span data-stu-id="bd8c7-150">6</span></span>|<span data-ttu-id="bd8c7-151">76%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-151">76%</span></span>|  
|`int`|<span data-ttu-id="bd8c7-152">4</span><span class="sxs-lookup"><span data-stu-id="bd8c7-152">4</span></span>|<span data-ttu-id="bd8c7-153">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-153">8</span></span>|<span data-ttu-id="bd8c7-154">64%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-154">64%</span></span>|  
|`bigint`|<span data-ttu-id="bd8c7-155">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-155">8</span></span>|<span data-ttu-id="bd8c7-156">12</span><span class="sxs-lookup"><span data-stu-id="bd8c7-156">12</span></span>|<span data-ttu-id="bd8c7-157">52%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-157">52%</span></span>|  
|`real`|<span data-ttu-id="bd8c7-158">4</span><span class="sxs-lookup"><span data-stu-id="bd8c7-158">4</span></span>|<span data-ttu-id="bd8c7-159">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-159">8</span></span>|<span data-ttu-id="bd8c7-160">64%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-160">64%</span></span>|  
|`float`|<span data-ttu-id="bd8c7-161">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-161">8</span></span>|<span data-ttu-id="bd8c7-162">12</span><span class="sxs-lookup"><span data-stu-id="bd8c7-162">12</span></span>|<span data-ttu-id="bd8c7-163">52%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-163">52%</span></span>|  
|`smallmoney`|<span data-ttu-id="bd8c7-164">4</span><span class="sxs-lookup"><span data-stu-id="bd8c7-164">4</span></span>|<span data-ttu-id="bd8c7-165">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-165">8</span></span>|<span data-ttu-id="bd8c7-166">64%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-166">64%</span></span>|  
|`money`|<span data-ttu-id="bd8c7-167">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-167">8</span></span>|<span data-ttu-id="bd8c7-168">12</span><span class="sxs-lookup"><span data-stu-id="bd8c7-168">12</span></span>|<span data-ttu-id="bd8c7-169">52%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-169">52%</span></span>|  
|`smalldatetime`|<span data-ttu-id="bd8c7-170">4</span><span class="sxs-lookup"><span data-stu-id="bd8c7-170">4</span></span>|<span data-ttu-id="bd8c7-171">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-171">8</span></span>|<span data-ttu-id="bd8c7-172">64%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-172">64%</span></span>|  
|`datetime`|<span data-ttu-id="bd8c7-173">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-173">8</span></span>|<span data-ttu-id="bd8c7-174">12</span><span class="sxs-lookup"><span data-stu-id="bd8c7-174">12</span></span>|<span data-ttu-id="bd8c7-175">52%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-175">52%</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="bd8c7-176">16</span><span class="sxs-lookup"><span data-stu-id="bd8c7-176">16</span></span>|<span data-ttu-id="bd8c7-177">20</span><span class="sxs-lookup"><span data-stu-id="bd8c7-177">20</span></span>|<span data-ttu-id="bd8c7-178">43%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-178">43%</span></span>|  
|`date`|<span data-ttu-id="bd8c7-179">3</span><span class="sxs-lookup"><span data-stu-id="bd8c7-179">3</span></span>|<span data-ttu-id="bd8c7-180">7</span><span class="sxs-lookup"><span data-stu-id="bd8c7-180">7</span></span>|<span data-ttu-id="bd8c7-181">69%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-181">69%</span></span>|  
  
 <span data-ttu-id="bd8c7-182">**有効桁数に依存する長さのデータ型**</span><span class="sxs-lookup"><span data-stu-id="bd8c7-182">**Precision-Dependent-Length Data Types**</span></span>  
  
|<span data-ttu-id="bd8c7-183">データ型</span><span class="sxs-lookup"><span data-stu-id="bd8c7-183">Data type</span></span>|<span data-ttu-id="bd8c7-184">非スパース バイト数</span><span class="sxs-lookup"><span data-stu-id="bd8c7-184">Nonsparse bytes</span></span>|<span data-ttu-id="bd8c7-185">スパース バイト数</span><span class="sxs-lookup"><span data-stu-id="bd8c7-185">Sparse bytes</span></span>|<span data-ttu-id="bd8c7-186">NULL の比率</span><span class="sxs-lookup"><span data-stu-id="bd8c7-186">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`datetime2(0)`|<span data-ttu-id="bd8c7-187">6</span><span class="sxs-lookup"><span data-stu-id="bd8c7-187">6</span></span>|<span data-ttu-id="bd8c7-188">10</span><span class="sxs-lookup"><span data-stu-id="bd8c7-188">10</span></span>|<span data-ttu-id="bd8c7-189">57%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-189">57%</span></span>|  
|`datetime2(7)`|<span data-ttu-id="bd8c7-190">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-190">8</span></span>|<span data-ttu-id="bd8c7-191">12</span><span class="sxs-lookup"><span data-stu-id="bd8c7-191">12</span></span>|<span data-ttu-id="bd8c7-192">52%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-192">52%</span></span>|  
|`time(0)`|<span data-ttu-id="bd8c7-193">3</span><span class="sxs-lookup"><span data-stu-id="bd8c7-193">3</span></span>|<span data-ttu-id="bd8c7-194">7</span><span class="sxs-lookup"><span data-stu-id="bd8c7-194">7</span></span>|<span data-ttu-id="bd8c7-195">69%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-195">69%</span></span>|  
|`time(7)`|<span data-ttu-id="bd8c7-196">5</span><span class="sxs-lookup"><span data-stu-id="bd8c7-196">5</span></span>|<span data-ttu-id="bd8c7-197">9</span><span class="sxs-lookup"><span data-stu-id="bd8c7-197">9</span></span>|<span data-ttu-id="bd8c7-198">60%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-198">60%</span></span>|  
|`datetimetoffset(0)`|<span data-ttu-id="bd8c7-199">8</span><span class="sxs-lookup"><span data-stu-id="bd8c7-199">8</span></span>|<span data-ttu-id="bd8c7-200">12</span><span class="sxs-lookup"><span data-stu-id="bd8c7-200">12</span></span>|<span data-ttu-id="bd8c7-201">52%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-201">52%</span></span>|  
|`datetimetoffset (7)`|<span data-ttu-id="bd8c7-202">10</span><span class="sxs-lookup"><span data-stu-id="bd8c7-202">10</span></span>|<span data-ttu-id="bd8c7-203">14</span><span class="sxs-lookup"><span data-stu-id="bd8c7-203">14</span></span>|<span data-ttu-id="bd8c7-204">49%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-204">49%</span></span>|  
|`decimal/numeric(1,s)`|<span data-ttu-id="bd8c7-205">5</span><span class="sxs-lookup"><span data-stu-id="bd8c7-205">5</span></span>|<span data-ttu-id="bd8c7-206">9</span><span class="sxs-lookup"><span data-stu-id="bd8c7-206">9</span></span>|<span data-ttu-id="bd8c7-207">60%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-207">60%</span></span>|  
|`decimal/numeric(38,s)`|<span data-ttu-id="bd8c7-208">17</span><span class="sxs-lookup"><span data-stu-id="bd8c7-208">17</span></span>|<span data-ttu-id="bd8c7-209">21</span><span class="sxs-lookup"><span data-stu-id="bd8c7-209">21</span></span>|<span data-ttu-id="bd8c7-210">42%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-210">42%</span></span>|  
|`vardecimal(p,s)`|<span data-ttu-id="bd8c7-211">控えめな推定値として `decimal` 型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-211">Use the `decimal` type as a conservative estimate.</span></span>|||  
  
 <span data-ttu-id="bd8c7-212">**データに依存する長さのデータ型**</span><span class="sxs-lookup"><span data-stu-id="bd8c7-212">**Data-Dependent-Length Data Types**</span></span>  
  
|<span data-ttu-id="bd8c7-213">データ型</span><span class="sxs-lookup"><span data-stu-id="bd8c7-213">Data type</span></span>|<span data-ttu-id="bd8c7-214">非スパース バイト数</span><span class="sxs-lookup"><span data-stu-id="bd8c7-214">Nonsparse bytes</span></span>|<span data-ttu-id="bd8c7-215">スパース バイト数</span><span class="sxs-lookup"><span data-stu-id="bd8c7-215">Sparse bytes</span></span>|<span data-ttu-id="bd8c7-216">NULL の比率</span><span class="sxs-lookup"><span data-stu-id="bd8c7-216">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`sql_variant`|<span data-ttu-id="bd8c7-217">基になるデータ型で異なります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-217">Varies with the underlying data type</span></span>|||  
|<span data-ttu-id="bd8c7-218">`varchar` または `char`</span><span class="sxs-lookup"><span data-stu-id="bd8c7-218">`varchar` or `char`</span></span>|<span data-ttu-id="bd8c7-219">2\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-219">2\*</span></span>|<span data-ttu-id="bd8c7-220">4\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-220">4\*</span></span>|<span data-ttu-id="bd8c7-221">60%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-221">60%</span></span>|  
|<span data-ttu-id="bd8c7-222">`nvarchar` または `nchar`</span><span class="sxs-lookup"><span data-stu-id="bd8c7-222">`nvarchar` or `nchar`</span></span>|<span data-ttu-id="bd8c7-223">2\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-223">2\*</span></span>|<span data-ttu-id="bd8c7-224">4\*+</span><span class="sxs-lookup"><span data-stu-id="bd8c7-224">4\*+</span></span>|<span data-ttu-id="bd8c7-225">60%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-225">60%</span></span>|  
|<span data-ttu-id="bd8c7-226">`varbinary` または `binary`</span><span class="sxs-lookup"><span data-stu-id="bd8c7-226">`varbinary` or `binary`</span></span>|<span data-ttu-id="bd8c7-227">2\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-227">2\*</span></span>|<span data-ttu-id="bd8c7-228">4\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-228">4\*</span></span>|<span data-ttu-id="bd8c7-229">60%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-229">60%</span></span>|  
|`xml`|<span data-ttu-id="bd8c7-230">2\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-230">2\*</span></span>|<span data-ttu-id="bd8c7-231">4\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-231">4\*</span></span>|<span data-ttu-id="bd8c7-232">60%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-232">60%</span></span>|  
|`hierarchyid`|<span data-ttu-id="bd8c7-233">2\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-233">2\*</span></span>|<span data-ttu-id="bd8c7-234">4\*</span><span class="sxs-lookup"><span data-stu-id="bd8c7-234">4\*</span></span>|<span data-ttu-id="bd8c7-235">60%</span><span class="sxs-lookup"><span data-stu-id="bd8c7-235">60%</span></span>|  
  
 <span data-ttu-id="bd8c7-236">\* 長さは、型に含まれているデータの平均に 2 バイトまたは 4 バイトを加えた長さに等しくなります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-236">\*The length is equal to the average of the data that is contained in the type, plus 2 or 4 bytes.</span></span>  
  
## <a name="in-memory-overhead-required-for-updates-to-sparse-columns"></a><span data-ttu-id="bd8c7-237">スパース列の更新に必要なインメモリ オーバーヘッド</span><span class="sxs-lookup"><span data-stu-id="bd8c7-237">In-Memory Overhead Required for Updates to Sparse Columns</span></span>  
 <span data-ttu-id="bd8c7-238">スパース列を含むテーブルをデザインする場合は、行を更新するときにテーブル内の NULL 以外のスパース列ごとに追加の 2 バイトが必要になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-238">When designing tables with sparse columns, keep in mind that an additional 2 bytes of overhead are required for each non-null sparse column in the table when a row is being updated.</span></span> <span data-ttu-id="bd8c7-239">この追加のメモリ要件により、(このメモリ オーバーヘッドを含む) 合計行サイズが 8019 を超え、列を行外に出すことができないと、更新がエラー 576 で予期せずに失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-239">As a result of this additional memory requirement, updates can fail unexpectedly with error 576 when the total row size, including this memory overhead, exceeds 8019, and no columns can be pushed off the row.</span></span>  
  
 <span data-ttu-id="bd8c7-240">たとえば、bigint 型の 600 個のスパース列を持つテーブルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-240">Consider the example of a table that has 600 sparse columns of type bigint.</span></span> <span data-ttu-id="bd8c7-241">571 個の NULL 以外の列がある場合、ディスク上の合計サイズは 571 \* 12 = 6852 バイトです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-241">If there are 571 non-null columns, then the total size on disk is 571 \* 12 = 6852 bytes.</span></span> <span data-ttu-id="bd8c7-242">追加の行のオーバーヘッドとスパース列ヘッダーを含めた場合、サイズは約 6895 バイトになります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-242">After including additional row overhead and the sparse column header, this increases to around 6895 bytes.</span></span> <span data-ttu-id="bd8c7-243">このページは、ディスク上で約 1124 バイトをまだ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-243">The page still has around 1124 bytes available on disk.</span></span> <span data-ttu-id="bd8c7-244">これ場合、追加の列を正常に更新できるように思われます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-244">This can give the impression that additional columns can be updated successfully.</span></span> <span data-ttu-id="bd8c7-245">しかし、更新時は、"2\*(NULL 以外のスパース列の数)" で求められる追加のオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-245">However, during the update, there is additional overhead in memory which is 2\*(number of non-null sparse columns).</span></span> <span data-ttu-id="bd8c7-246">この例で追加のオーバーヘッド (2 \* 571 = 1142 バイト) を含めると、ディスク上の行サイズは約 8037 バイトに増えます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-246">In this example, including the additional overhead - 2 \* 571 = 1142 bytes - increases the row size on disk to around 8037 bytes.</span></span> <span data-ttu-id="bd8c7-247">このサイズは、最大許容サイズの 8019 バイトを超えています。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-247">This size exceeds the maximum allowed size of 8019 bytes.</span></span> <span data-ttu-id="bd8c7-248">すべての列は固定長データ型であるため、行外に出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-248">Since all the columns are fixed-length data types, they cannot be pushed off the row.</span></span> <span data-ttu-id="bd8c7-249">その結果、更新は 576 エラーで失敗します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-249">As a result, the update fails with the 576 error.</span></span>  
  
## <a name="restrictions-for-using-sparse-columns"></a><span data-ttu-id="bd8c7-250">スパース列の使用に関する制限</span><span class="sxs-lookup"><span data-stu-id="bd8c7-250">Restrictions for Using Sparse Columns</span></span>  
 <span data-ttu-id="bd8c7-251">スパース列は、任意の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型にすることができ、他の列と同じように動作しますが、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-251">Sparse columns can be of any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type and behave like any other column with the following restrictions:</span></span>  
  
-   <span data-ttu-id="bd8c7-252">スパース列は、NULL 値を許容する必要があり、ROWGUIDCOL または IDENTITY プロパティを持つことができません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-252">A sparse column must be nullable and cannot have the ROWGUIDCOL or IDENTITY properties.</span></span> <span data-ttu-id="bd8c7-253">スパース列のデータ型を `text`、`ntext`、`image`、`timestamp`、ユーザー定義データ型、`geometry`、または `geography` にすることはできません。また、スパース列には FILESTREAM 属性を指定できません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-253">A sparse column cannot be of the following data types: `text`, `ntext`, `image`, `timestamp`, user-defined data type, `geometry`, or `geography`; or have the FILESTREAM attribute.</span></span>  
  
-   <span data-ttu-id="bd8c7-254">スパース列には既定値を設定できません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-254">A sparse column cannot have a default value.</span></span>  
  
-   <span data-ttu-id="bd8c7-255">スパース列はルールにバインドできません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-255">A sparse column cannot be bound to a rule.</span></span>  
  
-   <span data-ttu-id="bd8c7-256">計算列にスパース列を含めることはできますが、計算列を SPARSE とマークすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-256">Although a computed column can contain a sparse column, a computed column cannot be marked as SPARSE.</span></span>  
  
-   <span data-ttu-id="bd8c7-257">スパース列をクラスター化インデックスまたは一意の主キー インデックスに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-257">A sparse column cannot be part of a clustered index or a unique primary key index.</span></span> <span data-ttu-id="bd8c7-258">ただし、スパース列に定義された保存される計算列と保存されない計算列は、クラスター化キーに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-258">However, both persisted and nonpersisted computed columns that are defined on sparse columns can be part of a clustered key.</span></span>  
  
-   <span data-ttu-id="bd8c7-259">スパース列は、クラスター化インデックスまたはヒープのパーティション キーとして使用できません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-259">A sparse column cannot be used as a partition key of a clustered index or heap.</span></span> <span data-ttu-id="bd8c7-260">ただし、スパース列を非クラスター化インデックスのパーティション キーとして使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-260">However, a sparse column can be used as the partition key of a nonclustered index.</span></span>  
  
-   <span data-ttu-id="bd8c7-261">テーブル変数およびテーブル値パラメーターで使用されるユーザー定義テーブル型に、スパース列を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-261">A sparse column cannot be part of a user-defined table type, which are used in table variables and table-valued parameters.</span></span>  
  
-   <span data-ttu-id="bd8c7-262">スパース列は、データ圧縮と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-262">Sparse columns are incompatible with data compression.</span></span> <span data-ttu-id="bd8c7-263">したがって、圧縮されたテーブルにスパース列を追加したり、スパース列を含むテーブルを圧縮したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-263">Therefore sparse columns cannot be added to compressed tables, nor can any tables containing sparse columns be compressed.</span></span>  
  
-   <span data-ttu-id="bd8c7-264">スパースから非スパース、または非スパースからスパースに列を変更するには、列のストレージ形式を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-264">Changing a column from sparse to nonsparse or nonsparse to sparse requires changing the storage format of the column.</span></span> <span data-ttu-id="bd8c7-265">SQL Server データベース エンジンでは、次の手順を使用してこの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-265">The SQL Server Database Engine uses the following procedure to accomplish this change:</span></span>  
  
    1.  <span data-ttu-id="bd8c7-266">新しいストレージ サイズおよびストレージ形式でテーブルに新しい列を追加します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-266">Adds a new column to the table in the new storage size and format.</span></span>  
  
    2.  <span data-ttu-id="bd8c7-267">テーブル内の行ごとに、古い列に格納されている値を更新して新しい列にコピーします。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-267">For each row in the table, updates and copies the value stored in the old column to the new column.</span></span>  
  
    3.  <span data-ttu-id="bd8c7-268">古い列をテーブル スキーマから削除します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-268">Removes the old column from the table schema.</span></span>  
  
    4.  <span data-ttu-id="bd8c7-269">古い列で使用されていた領域を再利用するために、テーブルを再構築するか (クラスター化インデックスが存在しない場合)、クラスター化インデックスを再構築します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-269">Rebuilds the table (if there is no clustered index) or rebuilds the clustered index to reclaim space used by the old column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd8c7-270">許容されている最大行サイズを行内のデータのサイズが超える場合、手順 2. が失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-270">Step 2 can fail when the size of the data in the row exceeds the maximum allowable row size.</span></span> <span data-ttu-id="bd8c7-271">このサイズには、古い列に格納されているデータのサイズと、新しい列に格納されている更新されたデータのサイズが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-271">This size includes the size of the data stored in the old column and the updated data stored in the new column.</span></span> <span data-ttu-id="bd8c7-272">この制限値は、スパース列を含まないテーブルの場合は 8,060 バイト、スパース列を含むテーブルの場合は 8,018 バイトです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-272">This limit is 8060 bytes for tables that do not contain any sparse columns or 8018 bytes for tables that contain sparse columns.</span></span> <span data-ttu-id="bd8c7-273">このエラーは、条件を満たすすべての列が行外にプッシュされている場合でも発生します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-273">This error can occur even if all eligible columns have been pushed off-row.</span></span>  
  
-   <span data-ttu-id="bd8c7-274">非スパース列をスパース列に変更すると、その列で NULL 以外の値に使用される領域が増えます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-274">When you change a non-sparse column to a sparse column, the sparse column will consume more space for non-null values.</span></span> <span data-ttu-id="bd8c7-275">行のサイズがその上限に近い場合は、操作が失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-275">When a row is close to the maximum row size limit, the operation can fail.</span></span>  
  
## <a name="sql-server-technologies-that-support-sparse-columns"></a><span data-ttu-id="bd8c7-276">スパース列をサポートする SQL Server のテクノロジ</span><span class="sxs-lookup"><span data-stu-id="bd8c7-276">SQL Server Technologies That Support Sparse Columns</span></span>  
 <span data-ttu-id="bd8c7-277">ここでは、次に示す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテクノロジでスパース列がどのようにサポートされるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-277">This section describes how sparse columns are supported in the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies:</span></span>  
  
-   <span data-ttu-id="bd8c7-278">トランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="bd8c7-278">Transactional replication</span></span>  
  
     <span data-ttu-id="bd8c7-279">トランザクション レプリケーションでは、スパース列はサポートされますが、スパース列と併用できる列セットはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-279">Transactional replication supports sparse columns, but it does not support column sets, which can be used with sparse columns.</span></span> <span data-ttu-id="bd8c7-280">列セットの詳細については、「 [列セットの使用](../tables/use-column-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-280">For more information about column sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
     <span data-ttu-id="bd8c7-281">SPARSE 属性のレプリケーションは、 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) または **の** [アーティクルのプロパティ] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスで指定されるスキーマ オプションによって決まります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-281">The replication of the SPARSE attribute is determined by a schema option that is specified by using [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) or by using the **Article Properties** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="bd8c7-282">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、スパース列がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-282">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do not support sparse columns.</span></span> <span data-ttu-id="bd8c7-283">以前のバージョンにデータをレプリケートする必要がある場合は、SPARSE 属性をレプリケートしないように指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-283">If you must replicate data to an earlier version, specify that the SPARSE attribute should not be replicated.</span></span>  
  
     <span data-ttu-id="bd8c7-284">テーブルがパブリッシュされる場合は、テーブルに新しいスパース列を追加したり、既存の列のスパース プロパティを変更したりできません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-284">For tables that are published, you cannot add any new sparse columns to a table or change the sparse property of an existing column.</span></span> <span data-ttu-id="bd8c7-285">このような操作が必要な場合は、パブリケーションを削除して再作成します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-285">If such an operation is required, drop and re-create the publication.</span></span>  
  
-   <span data-ttu-id="bd8c7-286">マージ レプリケーション</span><span class="sxs-lookup"><span data-stu-id="bd8c7-286">Merge replication</span></span>  
  
     <span data-ttu-id="bd8c7-287">マージ レプリケーションでは、スパース列または列セットがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-287">Merge replication does not support sparse columns or column sets.</span></span>  
  
-   <span data-ttu-id="bd8c7-288">Change tracking</span><span class="sxs-lookup"><span data-stu-id="bd8c7-288">Change tracking</span></span>  
  
     <span data-ttu-id="bd8c7-289">変更の追跡では、スパース列と列セットがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-289">Change tracking supports sparse columns and column sets.</span></span> <span data-ttu-id="bd8c7-290">テーブルで列セットが更新されると、変更の追跡でその操作が行全体の更新として処理されます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-290">When a column set is updated in a table, change tracking treats this as an update to the whole row.</span></span> <span data-ttu-id="bd8c7-291">列セットの更新操作で更新された一連のスパース列を正確に特定するための詳細な変更追跡は行われません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-291">No detailed change tracking is provided to obtain the exact set of sparse columns that are updated through the column set update operation.</span></span> <span data-ttu-id="bd8c7-292">スパース列が DML ステートメントを通じて明示的に更新された場合は、その列に対する変更の追跡が通常どおりに機能し、変更された一連の列を正確に特定できます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-292">If the sparse columns are updated explicitly through a DML statement, change tracking on them will work ordinarily and can identify the exact set of changed columns.</span></span>  
  
-   <span data-ttu-id="bd8c7-293">変更データ キャプチャ</span><span class="sxs-lookup"><span data-stu-id="bd8c7-293">Change data capture</span></span>  
  
     <span data-ttu-id="bd8c7-294">変更データ キャプチャでは、スパース列はサポートされますが、列セットはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-294">Change data capture supports sparse columns, but it does not support column sets.</span></span>  
  
-   <span data-ttu-id="bd8c7-295">テーブルをコピーするとき、列のスパース プロパティは保持されません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-295">The sparse property of a column is not preserved when the table is copied.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bd8c7-296">例</span><span class="sxs-lookup"><span data-stu-id="bd8c7-296">Examples</span></span>  
 <span data-ttu-id="bd8c7-297">次の例では、ドキュメント テーブルに `DocID` 列と `Title`列のセットが共通で含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-297">In this example, a document table contains a common set that has the columns `DocID` and `Title`.</span></span> <span data-ttu-id="bd8c7-298">製造グループは、すべての製造ドキュメントに `ProductionSpecification` 列と `ProductionLocation` 列を必要とします。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-298">The Production group wants a `ProductionSpecification` and `ProductionLocation` column for all production documents.</span></span> <span data-ttu-id="bd8c7-299">マーケティング グループは、マーケティング ドキュメントに `MarketingSurveyGroup` 列を必要とします。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-299">The Marketing group wants a `MarketingSurveyGroup` column for marketing documents.</span></span> <span data-ttu-id="bd8c7-300">この例のコードでは、スパース列を使用するテーブルを作成し、そのテーブルに 2 つの行を挿入し、そのテーブルからデータを選択します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-300">The code in this example creates a table that uses sparse columns, inserts two rows into the table, and then selects data from the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd8c7-301">このテーブルは、簡単に表示して確認できるように、5 つの列のみで構成されています。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-301">This table has only five columns to make it easier to display and read.</span></span> <span data-ttu-id="bd8c7-302">ANSI_NULL_DFLT_ON オプションが設定されている場合は、NULL 値を許容するようにスパース列を宣言しなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-302">Declaring the sparse columns to be nullable is optional if the ANSI_NULL_DFLT_ON option is set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE DocumentStore  
    (DocID int PRIMARY KEY,  
     Title varchar(200) NOT NULL,  
     ProductionSpecification varchar(20) SPARSE NULL,  
     ProductionLocation smallint SPARSE NULL,  
     MarketingSurveyGroup varchar(20) SPARSE NULL ) ;  
GO  
  
INSERT DocumentStore(DocID, Title, ProductionSpecification, ProductionLocation)  
VALUES (1, 'Tire Spec 1', 'AXZZ217', 27);  
GO  
  
INSERT DocumentStore(DocID, Title, MarketingSurveyGroup)  
VALUES (2, 'Survey 2142', 'Men 25 - 35');  
GO  
```  
  
 <span data-ttu-id="bd8c7-303">テーブルからすべての列を選択すると、通常の結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-303">To select all the columns from the table returns an ordinary result set.</span></span>  
  
```  
SELECT * FROM DocumentStore ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID  Title        ProductionSpecification  ProductionLocation  MarketingSurveyGroup`  
  
 `1      Tire Spec 1  AXZZ217                  27                  NULL`  
  
 `2      Survey 2142  NULL                     NULL                Men 25-35`  
  
 <span data-ttu-id="bd8c7-304">製造部門にマーケティング データは必要ないため、次のクエリに示すように、必要な列のみを返す列セットを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-304">Because the Production department is not interested in the marketing data, they want to use a column list that returns only columns of interest, as shown in the following query.</span></span>  
  
```  
SELECT DocID, Title, ProductionSpecification, ProductionLocation   
FROM DocumentStore   
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID  Title        ProductionSpecification  ProductionLocation`  
  
 `1      Tire Spec 1  AXZZ217                  27`  
  
## <a name="see-also"></a><span data-ttu-id="bd8c7-305">参照</span><span class="sxs-lookup"><span data-stu-id="bd8c7-305">See Also</span></span>  
 <span data-ttu-id="bd8c7-306">[列セットの使用](../tables/use-column-sets.md) </span><span class="sxs-lookup"><span data-stu-id="bd8c7-306">[Use Column Sets](../tables/use-column-sets.md) </span></span>  
 <span data-ttu-id="bd8c7-307">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd8c7-307">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="bd8c7-308">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd8c7-308">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="bd8c7-309">sys.columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bd8c7-309">sys.columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)  
  
  
