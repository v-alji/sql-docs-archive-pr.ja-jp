---
title: ハッシュインデックスの適切なバケット数の決定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6d1ac280-87db-4bd8-ad43-54353647d8b5
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0579a98e3302b6944f68ca449d3e7cda0ecc01d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634011"
---
# <a name="determining-the-correct-bucket-count-for-hash-indexes"></a><span data-ttu-id="78f63-102">ハッシュ インデックスの適切なバケット数の決定</span><span class="sxs-lookup"><span data-stu-id="78f63-102">Determining the Correct Bucket Count for Hash Indexes</span></span>
  <span data-ttu-id="78f63-103">メモリ最適化テーブルを作成するときに `BUCKET_COUNT` パラメーターの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-103">You must specify a value for the `BUCKET_COUNT` parameter when you create the memory-optimized table.</span></span> <span data-ttu-id="78f63-104">このトピックでは、`BUCKET_COUNT` パラメーターの適切な値を判断する際の推奨事項を示します。</span><span class="sxs-lookup"><span data-stu-id="78f63-104">This topic makes recommendations for determining the appropriate value for the `BUCKET_COUNT` parameter.</span></span> <span data-ttu-id="78f63-105">適切なバケット数を決定できない場合は、代わりに非クラスター化インデックスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="78f63-105">If you cannot determine the correct bucket count, use a nonclustered index instead.</span></span>  <span data-ttu-id="78f63-106">`BUCKET_COUNT` の値が不適切な場合 (特に小さすぎる場合)、ワークロードのパフォーマンス、およびデータベースの復旧時間に大きな影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-106">An incorrect `BUCKET_COUNT` value, especially one that is too low, can significantly impact workload performance, as well as recovery time of the database.</span></span> <span data-ttu-id="78f63-107">バケット数は大きめに設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78f63-107">It is better to overestimate the bucket count.</span></span>  
  
 <span data-ttu-id="78f63-108">重複したインデックス キーは、複数のキーが同じバケットにハッシュされることが原因でバケットのチェーンの増加を引き起こし、ハッシュ インデックスのパフォーマンス低下につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-108">Duplicate index keys can decrease performance with a hash index because the keys are hashed to the same bucket, causing that bucket's chain to increase.</span></span>  
  
 <span data-ttu-id="78f63-109">非クラスター化ハッシュ インデックスの詳細については、「 [Hash Indexes](hash-indexes.md) 」と「 [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78f63-109">For more information about nonclustered hash indexes, see [Hash Indexes](hash-indexes.md) and [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="78f63-110">メモリ最適化テーブルの各ハッシュ インデックスに対して 1 個のハッシュ テーブルが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="78f63-110">One hash table is allocated for each hash index on a memory-optimized table.</span></span> <span data-ttu-id="78f63-111">インデックスに割り当てられるハッシュテーブルのサイズは、 `BUCKET_COUNT` [CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql)のパラメーター、または[TRANSACT-SQL&#41;&#40;CREATE TYPE](/sql/t-sql/statements/create-type-transact-sql)によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="78f63-111">The size of the hash table allocated for an index is specified by the `BUCKET_COUNT` parameter in [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) or [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span> <span data-ttu-id="78f63-112">バケット数は内部的に、最も近い 2 のべき乗に切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="78f63-112">The bucket count will internally be rounded up to the next power of two.</span></span> <span data-ttu-id="78f63-113">たとえば、バケット数に 300,000 を指定すると、実際のバケット数は 524,288 になります。</span><span class="sxs-lookup"><span data-stu-id="78f63-113">For example, specifying a bucket count of 300,000 will result in an actual bucket count of 524,288.</span></span>  
  
 <span data-ttu-id="78f63-114">バケット数に関する記事とビデオへのリンクについては、「 [ハッシュ インデックス (インメモリ OLTP) に正しいバケット数を指定する方法](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78f63-114">For links to an article and video on bucket count, see [How to determine the right bucket count for hash indexes (In-Memory OLTP)](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/).</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="78f63-115">Recommendations</span><span class="sxs-lookup"><span data-stu-id="78f63-115">Recommendations</span></span>  
 <span data-ttu-id="78f63-116">ほとんどの場合、バケット数はインデックス キーにおける別個の値の数の 1 倍から 2 倍の範囲に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-116">In most cases the bucket count should be between 1 and 2 times the number of distinct values in the index key.</span></span> <span data-ttu-id="78f63-117">インデックス キーに重複する値が多数含まれている場合 (平均して各インデックス キー値に対して 10 を超える行がある場合) は、代わりに非クラスター化インデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="78f63-117">If the index key contains a lot of duplicate values, on average there are more than 10 rows for each index key value, use a nonclustered index instead</span></span>  
  
 <span data-ttu-id="78f63-118">特定のインデックス キーに値がどれぐらいあるかは、予測できないこともあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-118">You may not always be able to predict how many values a particular index key may have or will have.</span></span> <span data-ttu-id="78f63-119">`BUCKET_COUNT` 値が実際のキー値の数の 5 倍以内である場合、パフォーマンスは許容できます。</span><span class="sxs-lookup"><span data-stu-id="78f63-119">Performance should be acceptable if the `BUCKET_COUNT` value is within 5 times of the actual number of key values.</span></span>  
  
 <span data-ttu-id="78f63-120">既存のデータの一意なインデックス キーの数を判断するには、次の例のようなクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="78f63-120">To determine the number of unique index keys in existing data, use queries similar to the following examples:</span></span>  
  
### <a name="primary-key-and-unique-indexes"></a><span data-ttu-id="78f63-121">主キーと一意インデックス</span><span class="sxs-lookup"><span data-stu-id="78f63-121">Primary Key and Unique Indexes</span></span>  
 <span data-ttu-id="78f63-122">主キー インデックスは一意であるため、そのキーでの別個の値の数はテーブル内の行の数に相当します。</span><span class="sxs-lookup"><span data-stu-id="78f63-122">Because the primary key index is unique, the number of distinct values in the key corresponds to the number of rows in the table.</span></span> <span data-ttu-id="78f63-123">AdventureWorks データベースの Sales.SalesOrderDetail テーブル内の (SalesOrderID, SalesOrderDetailID) の主キーの例の場合は、次のクエリを発行して、テーブル内の行数に相当する別個の主キーの値の数を計算します。</span><span class="sxs-lookup"><span data-stu-id="78f63-123">For an example primary key on (SalesOrderID, SalesOrderDetailID) in the table Sales.SalesOrderDetail in the AdventureWorks database, issue the following query to calculate the number of distinct primary key values, which corresponds to the number of rows in the table:</span></span>  
  
```sql  
SELECT COUNT(*) AS [row count]   
FROM Sales.SalesOrderDetail  
```  
  
 <span data-ttu-id="78f63-124">このクエリは行数 121,317 を示します。</span><span class="sxs-lookup"><span data-stu-id="78f63-124">This query shows a row count of 121,317.</span></span> <span data-ttu-id="78f63-125">行数が大幅に変化しない場合は、240,000 というバケット数を使用します。</span><span class="sxs-lookup"><span data-stu-id="78f63-125">Use a bucket count of 240,000 if the row count will not change significantly.</span></span> <span data-ttu-id="78f63-126">テーブル内にある販売注文の数が 4 倍になると予想されている場合は、480,000 というバケット数を使用します。</span><span class="sxs-lookup"><span data-stu-id="78f63-126">Use a bucket count of 480,000 if the number of sales orders in the table is expected to quadruple.</span></span>  
  
### <a name="non-unique-indexes"></a><span data-ttu-id="78f63-127">一意ではないインデックス</span><span class="sxs-lookup"><span data-stu-id="78f63-127">Non-Unique Indexes</span></span>  
 <span data-ttu-id="78f63-128">(SpecialOfferID, ProductID) の複数列のインデックスなど、その他のインデックスの場合は、次のクエリを発行して一意なインデックス キーの値の数を決定します。</span><span class="sxs-lookup"><span data-stu-id="78f63-128">For other indexes, for example a multi-column index on (SpecialOfferID, ProductID), issue the following query to determine the number of unique index key values:</span></span>  
  
```sql  
SELECT COUNT(*) AS [SpecialOfferID_ProductID index key count]  
FROM   
   (SELECT DISTINCT SpecialOfferID, ProductID   
    FROM Sales.SalesOrderDetail) t  
```  
  
 <span data-ttu-id="78f63-129">このクエリは (SpecialOfferID, ProductID) に対応するインデックス キー数として 484 を返し、非クラスター化ハッシュ インデックスの代わりに、非クラスター化インデックスを使用する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="78f63-129">This query returns an index key count for (SpecialOfferID, ProductID) of 484, indicating a that a nonclustered index should be used instead of a nonclustered hash index.</span></span>  
  
### <a name="determining-the-number-of-duplicates"></a><span data-ttu-id="78f63-130">重複数の決定</span><span class="sxs-lookup"><span data-stu-id="78f63-130">Determining the Number of Duplicates</span></span>  
 <span data-ttu-id="78f63-131">インデックス キー値の重複する値の平均数を決定するには、合計行数を一意のインデックス キーの数で割ります。</span><span class="sxs-lookup"><span data-stu-id="78f63-131">To determine the average number of duplicate values for an index key value, divide the total number of rows by the number of unique index keys.</span></span>  
  
 <span data-ttu-id="78f63-132">(SpecialOfferID, ProductID) のインデックスの例の場合は、121317 / 484 = 251 になります。</span><span class="sxs-lookup"><span data-stu-id="78f63-132">For the example index on (SpecialOfferID, ProductID), this leads to 121317 / 484 = 251.</span></span> <span data-ttu-id="78f63-133">この結果から、インデックス キーの値が平均して 251 あるため、非クラスター化インデックスを使用する必要があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="78f63-133">This means index key values have an average of 251, and thus this should be a nonclustered index.</span></span>  
  
## <a name="troubleshooting-the-bucket-count"></a><span data-ttu-id="78f63-134">バケット数のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="78f63-134">Troubleshooting the Bucket Count</span></span>  
 <span data-ttu-id="78f63-135">メモリ最適化テーブルでのバケット数の問題のトラブルシューティングを行うには、dm_db_xtp_hash_index_stats を使用して[transact-sql&#41;&#40;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql)します。これにより、空のバケットと行チェーンの長さに関する統計情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="78f63-135">To troubleshoot bucket count issues in memory-optimized tables, use [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql) to obtain statistics about the empty buckets and the length of row chains.</span></span> <span data-ttu-id="78f63-136">次のクエリを使用して、現在のデータベースのすべてのハッシュ インデックスに関する統計情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="78f63-136">The following query can be used to obtain statistics about all the hash indexes in the current database.</span></span> <span data-ttu-id="78f63-137">データベースに大きなテーブルがある場合、このクエリの実行には数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-137">The query can take several minutes to run if there are large tables in the database.</span></span>  
  
```sql  
SELECT   
   object_name(hs.object_id) AS 'object name',   
   i.name as 'index name',   
   hs.total_bucket_count,  
   hs.empty_bucket_count,  
   floor((cast(empty_bucket_count as float)/total_bucket_count) * 100) AS 'empty_bucket_percent',  
   hs.avg_chain_length,   
   hs.max_chain_length  
FROM sys.dm_db_xtp_hash_index_stats AS hs   
   JOIN sys.indexes AS i   
   ON hs.object_id=i.object_id AND hs.index_id=i.index_id  
```  
  
 <span data-ttu-id="78f63-138">ハッシュ インデックスの状態を示す主要インジケーターとして、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-138">The two key indicators of hash index health are:</span></span>  
  
 <span data-ttu-id="78f63-139">*empty_bucket_percent*</span><span class="sxs-lookup"><span data-stu-id="78f63-139">*empty_bucket_percent*</span></span>  
 <span data-ttu-id="78f63-140">*empty_bucket_percent* は、ハッシュ インデックス内の空のバケットの数を示します。</span><span class="sxs-lookup"><span data-stu-id="78f63-140">*empty_bucket_percent* indicates the number of empty buckets in the hash index.</span></span>  
  
 <span data-ttu-id="78f63-141">*empty_bucket_percent* が 10 未満の場合は、バケット数が少なすぎると考えられます。</span><span class="sxs-lookup"><span data-stu-id="78f63-141">If *empty_bucket_percent* is less than 10 percent, the bucket count is likely to be too low.</span></span> <span data-ttu-id="78f63-142">*empty_bucket_percent* は 33% 以上であるのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="78f63-142">Ideally, the *empty_bucket_percent* should be 33 percent or greater.</span></span> <span data-ttu-id="78f63-143">バケット数がインデックス キー値の数と一致する場合、ハッシュ分散のためにバケットの約 1/3 が空です。</span><span class="sxs-lookup"><span data-stu-id="78f63-143">If the bucket count matches the number of index key values, about 1/3 of the buckets is empty, due to hash distribution.</span></span>  
  
 <span data-ttu-id="78f63-144">*avg_chain_length*</span><span class="sxs-lookup"><span data-stu-id="78f63-144">*avg_chain_length*</span></span>  
 <span data-ttu-id="78f63-145">*avg_chain_length* は、ハッシュ バケット内の行チェーンの平均の長さを示します。</span><span class="sxs-lookup"><span data-stu-id="78f63-145">*avg_chain_length* indicates the average length of the row chains in the hash buckets.</span></span>  
  
 <span data-ttu-id="78f63-146">*avg_chain_length* が 10 より大きくて、 *empty_bucket_percent* が 10% より大きい場合は、重複するインデックス キー値が多いと考えられるため、非クラスター化インデックスの方が適切です。</span><span class="sxs-lookup"><span data-stu-id="78f63-146">If *avg_chain_length* is greater than 10 and *empty_bucket_percent* is greater than 10 percent, there likely are many duplicate index key values and a nonclustered index would be more appropriate.</span></span> <span data-ttu-id="78f63-147">平均チェーン長さが 1 であれば理想的です。</span><span class="sxs-lookup"><span data-stu-id="78f63-147">An average chain length of 1 is ideal.</span></span>  
  
 <span data-ttu-id="78f63-148">チェーン長さに影響を与える要素には、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-148">There are two factors that impact the chain length:</span></span>  
  
1.  <span data-ttu-id="78f63-149">重複: すべての重複行は、ハッシュ インデックスの同じチェーンに含まれます。</span><span class="sxs-lookup"><span data-stu-id="78f63-149">Duplicates; all duplicate rows are part of the same chain in the hash index.</span></span>  
  
2.  <span data-ttu-id="78f63-150">複数のキー値が同じバケットにマップされます。</span><span class="sxs-lookup"><span data-stu-id="78f63-150">Multiple key values map to the same bucket.</span></span> <span data-ttu-id="78f63-151">バケット数が少ない場合は、複数の値のマップ先となるバケットが多くなります。</span><span class="sxs-lookup"><span data-stu-id="78f63-151">The lower the bucket count, the more buckets that will have multiple values mapped to them.</span></span>  
  
 <span data-ttu-id="78f63-152">例として、次のテーブルとテーブルのサンプル行を挿入するスクリプトを考えます。</span><span class="sxs-lookup"><span data-stu-id="78f63-152">As an example, consider the following table and script to insert sample rows in the table:</span></span>  
  
```sql  
CREATE TABLE [Sales].[SalesOrderHeader_test]  
(  
   [SalesOrderID] [uniqueidentifier] NOT NULL DEFAULT (newid()),  
   [OrderSequence] int NOT NULL,  
   [OrderDate] [datetime2](7) NOT NULL,  
   [Status] [tinyint] NOT NULL,  
  
PRIMARY KEY NONCLUSTERED HASH ([SalesOrderID]) WITH ( BUCKET_COUNT = 262144 ),  
INDEX IX_OrderSequence HASH (OrderSequence) WITH ( BUCKET_COUNT = 20000),  
INDEX IX_Status HASH ([Status]) WITH ( BUCKET_COUNT = 8),  
INDEX IX_OrderDate NONCLUSTERED ([OrderDate] ASC),  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
DECLARE @i int = 0  
BEGIN TRAN  
WHILE @i < 262144  
BEGIN  
   INSERT Sales.SalesOrderHeader_test (OrderSequence, OrderDate, [Status]) VALUES (@i, sysdatetime(), @i % 8)  
   SET @i += 1  
END  
COMMIT  
GO  
```  
  
 <span data-ttu-id="78f63-153">スクリプトは、テーブルに 262,144 個の行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="78f63-153">The script inserts 262,144 rows in the table.</span></span> <span data-ttu-id="78f63-154">これは、主キー インデックスと IX_OrderSequence に一意な値を挿入し、</span><span class="sxs-lookup"><span data-stu-id="78f63-154">It inserts unique values in the primary key index and in IX_OrderSequence.</span></span> <span data-ttu-id="78f63-155">重複する値をインデックス IX_Status に挿入します。別個の値は 8 つだけ生成されます。</span><span class="sxs-lookup"><span data-stu-id="78f63-155">It inserts a lot of duplicate values in the index IX_Status: the script only generates 8 distinct values.</span></span>  
  
 <span data-ttu-id="78f63-156">BUCKET_COUNT トラブルシューティング クエリの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="78f63-156">The output of the BUCKET_COUNT troubleshooting query is as follows:</span></span>  
  
|<span data-ttu-id="78f63-157">インデックス名</span><span class="sxs-lookup"><span data-stu-id="78f63-157">index name</span></span>|<span data-ttu-id="78f63-158">total_bucket_count</span><span class="sxs-lookup"><span data-stu-id="78f63-158">total_bucket_count</span></span>|<span data-ttu-id="78f63-159">empty_bucket_count</span><span class="sxs-lookup"><span data-stu-id="78f63-159">empty_bucket_count</span></span>|<span data-ttu-id="78f63-160">empty_bucket_percent</span><span class="sxs-lookup"><span data-stu-id="78f63-160">empty_bucket_percent</span></span>|<span data-ttu-id="78f63-161">avg_chain_length</span><span class="sxs-lookup"><span data-stu-id="78f63-161">avg_chain_length</span></span>|<span data-ttu-id="78f63-162">max_chain_length</span><span class="sxs-lookup"><span data-stu-id="78f63-162">max_chain_length</span></span>|  
|----------------|--------------------------|--------------------------|----------------------------|------------------------|------------------------|  
|<span data-ttu-id="78f63-163">IX_Status</span><span class="sxs-lookup"><span data-stu-id="78f63-163">IX_Status</span></span>|<span data-ttu-id="78f63-164">8</span><span class="sxs-lookup"><span data-stu-id="78f63-164">8</span></span>|<span data-ttu-id="78f63-165">4</span><span class="sxs-lookup"><span data-stu-id="78f63-165">4</span></span>|<span data-ttu-id="78f63-166">50</span><span class="sxs-lookup"><span data-stu-id="78f63-166">50</span></span>|<span data-ttu-id="78f63-167">65536</span><span class="sxs-lookup"><span data-stu-id="78f63-167">65536</span></span>|<span data-ttu-id="78f63-168">65536</span><span class="sxs-lookup"><span data-stu-id="78f63-168">65536</span></span>|  
|<span data-ttu-id="78f63-169">IX_OrderSequence</span><span class="sxs-lookup"><span data-stu-id="78f63-169">IX_OrderSequence</span></span>|<span data-ttu-id="78f63-170">32768</span><span class="sxs-lookup"><span data-stu-id="78f63-170">32768</span></span>|<span data-ttu-id="78f63-171">13</span><span class="sxs-lookup"><span data-stu-id="78f63-171">13</span></span>|<span data-ttu-id="78f63-172">0</span><span class="sxs-lookup"><span data-stu-id="78f63-172">0</span></span>|<span data-ttu-id="78f63-173">8</span><span class="sxs-lookup"><span data-stu-id="78f63-173">8</span></span>|<span data-ttu-id="78f63-174">26</span><span class="sxs-lookup"><span data-stu-id="78f63-174">26</span></span>|  
|<span data-ttu-id="78f63-175">PK_SalesOrd_B14003C3F8FB3364</span><span class="sxs-lookup"><span data-stu-id="78f63-175">PK_SalesOrd_B14003C3F8FB3364</span></span>|<span data-ttu-id="78f63-176">262144</span><span class="sxs-lookup"><span data-stu-id="78f63-176">262144</span></span>|<span data-ttu-id="78f63-177">96319</span><span class="sxs-lookup"><span data-stu-id="78f63-177">96319</span></span>|<span data-ttu-id="78f63-178">36</span><span class="sxs-lookup"><span data-stu-id="78f63-178">36</span></span>|<span data-ttu-id="78f63-179">1</span><span class="sxs-lookup"><span data-stu-id="78f63-179">1</span></span>|<span data-ttu-id="78f63-180">8</span><span class="sxs-lookup"><span data-stu-id="78f63-180">8</span></span>|  
  
 <span data-ttu-id="78f63-181">このテーブルの 3 つのハッシュ インデックスについて考えます。</span><span class="sxs-lookup"><span data-stu-id="78f63-181">Consider the three hash indexes on this table:</span></span>  
  
-   <span data-ttu-id="78f63-182">IX_Status: バケットの 50% が空で、適切です。</span><span class="sxs-lookup"><span data-stu-id="78f63-182">IX_Status: 50 percent of the buckets are empty, which is good.</span></span> <span data-ttu-id="78f63-183">しかし、平均チェーン長さは非常に高くなっています (65,536)。</span><span class="sxs-lookup"><span data-stu-id="78f63-183">However, the average chain length is very high (65,536).</span></span> <span data-ttu-id="78f63-184">これは、重複する値が多いことを示しています。</span><span class="sxs-lookup"><span data-stu-id="78f63-184">This indicates a large number of duplicate values.</span></span> <span data-ttu-id="78f63-185">したがって、この場合は非クラスター化ハッシュ インデックスの使用は適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="78f63-185">Therefore, using a nonclustered hash index is not appropriate in this case.</span></span> <span data-ttu-id="78f63-186">代わりに、非クラスター化インデックスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-186">A nonclustered index should be used instead.</span></span>  
  
-   <span data-ttu-id="78f63-187">IX_OrderSequence: バケットの 0% が空で、値が低すぎます。</span><span class="sxs-lookup"><span data-stu-id="78f63-187">IX_OrderSequence: 0 percent of the buckets are empty, which is too low.</span></span> <span data-ttu-id="78f63-188">また、平均チェーン長さは 8 です。</span><span class="sxs-lookup"><span data-stu-id="78f63-188">In addition, the average chain length is 8.</span></span> <span data-ttu-id="78f63-189">このインデックスの値は一意であるため、これは平均 8 個の値が各バケットにマップされていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="78f63-189">As the values in this index are unique, this means on average 8 values are mapped to each bucket.</span></span> <span data-ttu-id="78f63-190">バケット数を増やす必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-190">The bucket count should be increased.</span></span> <span data-ttu-id="78f63-191">インデックス キーには 262,144 個の一意な値があるため、バケット数は少なくとも 262,144 個必要です。</span><span class="sxs-lookup"><span data-stu-id="78f63-191">As the index key has 262,144 unique values, the bucket count should be at least 262,144.</span></span> <span data-ttu-id="78f63-192">今後さらに大きくなることが予測される場合、さらに数を多くする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-192">If future growth is expected, the number should be higher.</span></span>  
  
-   <span data-ttu-id="78f63-193">主キーインデックス (PK__SalesOrder...): バケットの36% が空で、適切です。</span><span class="sxs-lookup"><span data-stu-id="78f63-193">Primary key index (PK__SalesOrder...): 36 percent of the buckets are empty, which is good.</span></span> <span data-ttu-id="78f63-194">また、平均チェーン長さも 1 で、適切です。</span><span class="sxs-lookup"><span data-stu-id="78f63-194">In addition the average chain length is 1, which is also good.</span></span> <span data-ttu-id="78f63-195">変更は不要です。</span><span class="sxs-lookup"><span data-stu-id="78f63-195">No change needed.</span></span>  
  
 <span data-ttu-id="78f63-196">メモリ最適化ハッシュ インデックスの問題のトラブルシューティングの詳細については、「 [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78f63-196">For more information on troubleshooting issues with your memory-optimized hash indexes, see [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md).</span></span>  
  
## <a name="detailed-considerations-for-further-optimization"></a><span data-ttu-id="78f63-197">さらに最適化するための詳細な検討</span><span class="sxs-lookup"><span data-stu-id="78f63-197">Detailed Considerations for Further Optimization</span></span>  
 <span data-ttu-id="78f63-198">このセクションでは、バケット数を最適化するための考慮事項について概説します。</span><span class="sxs-lookup"><span data-stu-id="78f63-198">This section outlines further considerations for optimizing the bucket count.</span></span>  
  
 <span data-ttu-id="78f63-199">ハッシュ インデックスで最高のパフォーマンスを発揮するには、ハッシュ テーブルに割り当てるメモリの量と主キーでの別個の値の数とのバランスを取ります。</span><span class="sxs-lookup"><span data-stu-id="78f63-199">To achieve the best performance for hash indexes, balance the amount of memory allocated to the hash table and the number of distinct values in the index key.</span></span> <span data-ttu-id="78f63-200">ポイント参照とテーブル スキャンの間のバランスもあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-200">There is also a balance between the performance of point lookups and table scans:</span></span>  
  
-   <span data-ttu-id="78f63-201">バケット数が大きくなると、インデックス内の空のバケットの数が増えることになります。</span><span class="sxs-lookup"><span data-stu-id="78f63-201">The higher the bucket count value, the more empty buckets there will be in the index.</span></span> <span data-ttu-id="78f63-202">このことは、各バケットをテーブル スキャンの一部としてスキャンするときに、メモリ使用量 (バケットごとに 8 バイト) とテーブル スキャンのパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="78f63-202">This has an impact on memory usage (8 bytes per bucket) and the performance of table scans, as each bucket is scanned as part of a table scan.</span></span>  
  
-   <span data-ttu-id="78f63-203">バケット数が小さくなると、単一のバケットにより多くの値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="78f63-203">The lower the bucket count, the more values are assigned to a single bucket.</span></span> <span data-ttu-id="78f63-204">この場合、検索述語で指定された値を検索するには [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が単一のバケットで複数の値をスキャンすることが必要になる可能性があるため、ポイント参照や挿入のパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="78f63-204">This decreases performance for point lookups and inserts, because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] may need to traverse several values in a single bucket to find the value specified by the search predicate.</span></span>  
  
 <span data-ttu-id="78f63-205">バケット数が一意のインデックス キーの数を大幅に下回る場合、多くの値が各バケットにマップされます。</span><span class="sxs-lookup"><span data-stu-id="78f63-205">If the bucket count is significantly lower than the number of unique index keys, many values will map to each bucket.</span></span> <span data-ttu-id="78f63-206">これによって、ポイント参照 (個々のインデックス キーの参照) や挿入操作などほとんどの DML 操作でパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="78f63-206">This degrades performance of most DML operations, particularly point lookups (lookups of individual index keys) and insert operations.</span></span> <span data-ttu-id="78f63-207">たとえば、WHERE 句でインデックス キー列を照合するための等値述語が含まれた SELECT クエリ、UPDATE 操作、および DELETE 操作で、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-207">For example, you may see poor performance of SELECT queries and, UPDATE and DELETE operations with equality predicates matching the index key columns in the WHERE clause.</span></span> <span data-ttu-id="78f63-208">データベースの起動時にインデックスが再作成されるため、バケット数が少ないと、データベースの復旧時間にも影響があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-208">A low bucket count will also affect the recovery time of the database, as the indexes are recreated on database startup.</span></span>  
  
### <a name="duplicate-index-key-values"></a><span data-ttu-id="78f63-209">重複するインデックス キー値</span><span class="sxs-lookup"><span data-stu-id="78f63-209">Duplicate Index Key Values</span></span>  
 <span data-ttu-id="78f63-210">重複する値によって、ハッシュの競合のパフォーマンスに与える影響が大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-210">Duplicate values can increase the performance impact of hash collisions.</span></span> <span data-ttu-id="78f63-211">各インデックス キーの重複数が少ない場合、これは通常は問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="78f63-211">This is usually not a problem if each index key has a low number of duplicates.</span></span> <span data-ttu-id="78f63-212">ただし、一意のインデックス キーの数とテーブル内の行の数の差が非常に大きくなると、問題になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-212">But this can be a problem if the discrepancy between the number of unique index keys and the number of rows in the tables becomes very large.</span></span>  
  
 <span data-ttu-id="78f63-213">インデックス キーの値が同じである行はすべて同じ重複チェーンに入ります。</span><span class="sxs-lookup"><span data-stu-id="78f63-213">All rows with the same index key will go into the same duplicate chain.</span></span> <span data-ttu-id="78f63-214">ハッシュの競合により複数のインデックス キーが同じバケットにある場合、インデックスのスキャナーは常に、2 つ目の値に対応する最初の行の検索前に最初の値の完全な重複チェーンをスキャンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-214">If multiple index keys are in the same bucket due to a hash collision, index scanners always need to scan the full duplicate chain for the first value before they can locate the first row corresponding to the second value.</span></span> <span data-ttu-id="78f63-215">重複するキーによって、ガベージ コレクションで行を探すことが困難にもなります。</span><span class="sxs-lookup"><span data-stu-id="78f63-215">Duplicate keys also make it more difficult for garbage collection to locate the row.</span></span> <span data-ttu-id="78f63-216">たとえば、任意のキーの重複が 1,000 個あり、その行の 1 つが削除された場合、ガベージ コレクターは、一連の 1,000 個の重複をスキャンし、インデックスから行のリンクを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-216">For example, if there are 1,000 duplicates for any key and one of the rows is deleted, the garbage collector needs to scan the chain of 1,000 duplicates to unlink the row from the index.</span></span> <span data-ttu-id="78f63-217">これは、削除対象を検索したクエリでより効率的なインデックス (主キー インデックス) を使用して行を指定する場合にも当てはまります。ガベージ コレクターは各インデックスからリンクを解除する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="78f63-217">This is true even if the query that found the delete used a more efficient index (a primary key index) to locate the row, because the garbage collector needs to unlink from every index</span></span>  
  
 <span data-ttu-id="78f63-218">ハッシュ インデックスの場合、インデックス キー値の重複が原因で生じる作業量を減らす方法は 2 とおりあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-218">For hash indexes, there are two ways to reduce the work caused by duplicate index key values:</span></span>  
  
-   <span data-ttu-id="78f63-219">代わりに、非クラスター化インデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="78f63-219">Use a nonclustered index instead.</span></span> <span data-ttu-id="78f63-220">インデックス キーに列を追加して、重複数を減らすことができます。その際、アプリケーションを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="78f63-220">You can decrease the duplicates by adding columns to the index key without requiring any changes to the application.</span></span>  
  
-   <span data-ttu-id="78f63-221">インデックスに非常に多いバケット数を指定します。</span><span class="sxs-lookup"><span data-stu-id="78f63-221">Specify a very high bucket count for the index.</span></span> <span data-ttu-id="78f63-222">たとえば、一意のインデックス キーの数の 20 ～ 100 倍を指定します。</span><span class="sxs-lookup"><span data-stu-id="78f63-222">For example, 20-to-100 times the number of unique index keys.</span></span> <span data-ttu-id="78f63-223">これで、ハッシュの競合が減少します。</span><span class="sxs-lookup"><span data-stu-id="78f63-223">This will reduce hash collisions.</span></span>  
  
### <a name="small-tables"></a><span data-ttu-id="78f63-224">小さいテーブル</span><span class="sxs-lookup"><span data-stu-id="78f63-224">Small Tables</span></span>  
 <span data-ttu-id="78f63-225">小さいテーブルの場合は、データベース全体のサイズと比較してインデックスのサイズが小さいため、メモリ使用量は通常は問題になりません。</span><span class="sxs-lookup"><span data-stu-id="78f63-225">For smaller tables, memory utilization is usually not a concern, as the size of the index will be small compared to the overall size of the database.</span></span>  
  
 <span data-ttu-id="78f63-226">ここでは、必要なパフォーマンスの種類に基づいて選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-226">You must now make a choice based on the kind of performance you want:</span></span>  
  
-   <span data-ttu-id="78f63-227">インデックスに関するパフォーマンス クリティカルな操作が主にポイント参照や挿入操作の場合は、バケット数を大きくするとハッシュ競合の可能性が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="78f63-227">If the performance-critical operations on the index are predominantly point lookups and/or insert operations, a higher bucket count would be appropriate to reduce the likelihood of hash collisions.</span></span> <span data-ttu-id="78f63-228">行の数の 3 倍以上に設定するのが最適です。</span><span class="sxs-lookup"><span data-stu-id="78f63-228">Three times the number of rows or even more would be the best option.</span></span>  
  
-   <span data-ttu-id="78f63-229">パフォーマンス クリティカルな操作がフル インデックス スキャンである場合は、実際のインデックス キー値の数に近いバケット数を使用します。</span><span class="sxs-lookup"><span data-stu-id="78f63-229">If full index scans are the predominant performance-critical operations, use a bucket count that is close to the actual number of index key values.</span></span>  
  
### <a name="big-tables"></a><span data-ttu-id="78f63-230">大きいテーブル</span><span class="sxs-lookup"><span data-stu-id="78f63-230">Big Tables</span></span>  
 <span data-ttu-id="78f63-231">大きいテーブルの場合は、メモリ使用量が問題になることがあります。</span><span class="sxs-lookup"><span data-stu-id="78f63-231">For large tables, memory utilization could become a concern.</span></span> <span data-ttu-id="78f63-232">たとえば、2億5000万行のテーブルに4つのハッシュインデックスがあり、それぞれのバケット数が10億である場合、ハッシュテーブルのオーバーヘッドは4インデックス \* 10億バケット \* 8 バイト = 32 gb のメモリ使用率になります。</span><span class="sxs-lookup"><span data-stu-id="78f63-232">For example, with a 250 million row table that has 4 hash indexes, each with a bucket count of one billion, the overhead for the hash tables is 4 indexes \* 1 billion buckets \* 8 bytes = 32 gigabytes of memory utilization.</span></span> <span data-ttu-id="78f63-233">インデックスごとのバケット数に 2 億 5 千万個を選択すると、ハッシュ テーブルの合計オーバーヘッドは 8 GB です。</span><span class="sxs-lookup"><span data-stu-id="78f63-233">When choosing a bucket count of 250 million for each of the indexes, the total overhead for the hash tables will be 8 gigabytes.</span></span> <span data-ttu-id="78f63-234">これは、各インデックスが個々の行に追加するメモリ使用量の8バイトに加えて、このシナリオでは 8 gb です (4 インデックス \* 8 バイト \* 2億5000万行)。</span><span class="sxs-lookup"><span data-stu-id="78f63-234">Note that this is in addition to the 8 bytes of memory usage each index adds to each individual row, which is 8 gigabytes in this scenario (4 indexes \* 8 bytes \* 250 million rows).</span></span>  
  
 <span data-ttu-id="78f63-235">OLTP ワークロードのパフォーマンス クリティカル パスでは、フル テーブル スキャンは一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="78f63-235">Full table scans are not usually in the performance-critical path for OLTP workloads.</span></span> <span data-ttu-id="78f63-236">そのため、メモリ使用量とポイント参照および挿入操作のパフォーマンスの間での選択になります。</span><span class="sxs-lookup"><span data-stu-id="78f63-236">Therefore, the choice is between memory utilization versus performance of point lookup and insert operations:</span></span>  
  
-   <span data-ttu-id="78f63-237">メモリ使用量を重視する場合は、インデックス キー値の数に近いバケット数を選択します。</span><span class="sxs-lookup"><span data-stu-id="78f63-237">If memory utilization is a concern, choose a bucket count close to the number of index key values.</span></span> <span data-ttu-id="78f63-238">バケット数は、インデックス キー値の数より大幅に小さくならないようにする必要があります。大幅に小さい場合、ほとんどの DML 操作や、サーバーの再起動後のデータベースの復旧に要する時間にも影響があります。</span><span class="sxs-lookup"><span data-stu-id="78f63-238">The bucket count should not be significantly lower than the number of index key values, as this impacts most DML operations as well the time it takes to recover the database after server restart.</span></span>  
  
-   <span data-ttu-id="78f63-239">ポイント参照のパフォーマンスを最適化する際は、一意のインデックス値の数の 2 ～ 3 倍のバケット数が適しています。</span><span class="sxs-lookup"><span data-stu-id="78f63-239">When optimizing the performance for point lookups, a higher bucket count of two or even three times the number of unique index values would be appropriate.</span></span> <span data-ttu-id="78f63-240">バケット数を大きくすると、メモリ使用量が増え、フル インデックス スキャンに必要な時間が増えます。</span><span class="sxs-lookup"><span data-stu-id="78f63-240">A higher bucket count would mean an increased memory utilization and an increase in the time required for a full index scan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f63-241">参照</span><span class="sxs-lookup"><span data-stu-id="78f63-241">See Also</span></span>  
 [<span data-ttu-id="78f63-242">メモリ最適化テーブルのインデックス</span><span class="sxs-lookup"><span data-stu-id="78f63-242">Indexes on Memory-Optimized Tables</span></span>](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
