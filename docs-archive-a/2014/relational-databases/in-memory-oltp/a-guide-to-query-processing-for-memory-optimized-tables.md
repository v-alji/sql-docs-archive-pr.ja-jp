---
title: メモリ最適化テーブルのクエリ処理のガイド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 065296fe-6711-4837-965e-252ef6c13a0f
author: rothja
ms.author: jroth
ms.openlocfilehash: 93489e5dea295964826005e081bcffe889cb7586
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643837"
---
# <a name="a-guide-to-query-processing-for-memory-optimized-tables"></a><span data-ttu-id="6a828-102">メモリ最適化テーブルのクエリ処理のガイド</span><span class="sxs-lookup"><span data-stu-id="6a828-102">A Guide to Query Processing for Memory-Optimized Tables</span></span>
  <span data-ttu-id="6a828-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、インメモリ OLTP によってメモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャが導入されています。</span><span class="sxs-lookup"><span data-stu-id="6a828-103">In-Memory OLTP introduces memory-optimized tables and natively compiled stored procedures in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6a828-104">ここでは、メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャの両方に対するクエリ処理の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="6a828-104">This article gives an overview of query processing for both memory-optimized tables and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="6a828-105">ここでは、次の内容を含め、メモリ最適化テーブルに対するクエリがどのようにコンパイルおよび実行されるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6a828-105">The document explains how queries on memory-optimized tables are compiled and executed, including:</span></span>  
  
-   <span data-ttu-id="6a828-106">ディスク ベース テーブルに対する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のクエリ処理パイプライン。</span><span class="sxs-lookup"><span data-stu-id="6a828-106">The query processing pipeline in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for disk-based tables.</span></span>  
  
-   <span data-ttu-id="6a828-107">クエリ最適化。メモリ最適化テーブルの統計のロール、および不適切なクエリ プランのトラブルシューティングのためのガイドライン。</span><span class="sxs-lookup"><span data-stu-id="6a828-107">Query optimization; the role of statistics on memory-optimized tables as well as guidelines for troubleshooting bad query plans.</span></span>  
  
-   <span data-ttu-id="6a828-108">解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用したメモリ最適化テーブルへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="6a828-108">The use of interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] to access memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="6a828-109">メモリ最適化テーブルへのアクセスのためのクエリ最適化に関する注意点。</span><span class="sxs-lookup"><span data-stu-id="6a828-109">Considerations about query optimization for memory-optimized table access.</span></span>  
  
-   <span data-ttu-id="6a828-110">ネイティブ コンパイル ストアド プロシージャのコンパイルと処理。</span><span class="sxs-lookup"><span data-stu-id="6a828-110">Natively compiled stored procedure compilation and processing.</span></span>  
  
-   <span data-ttu-id="6a828-111">オプティマイザーがコストの推定に使用する統計。</span><span class="sxs-lookup"><span data-stu-id="6a828-111">Statistics that are used for cost estimation by the optimizer.</span></span>  
  
-   <span data-ttu-id="6a828-112">不適切なクエリ プランを修正する方法。</span><span class="sxs-lookup"><span data-stu-id="6a828-112">Ways to fix bad query plans.</span></span>  
  
## <a name="example-query"></a><span data-ttu-id="6a828-113">サンプル クエリ</span><span class="sxs-lookup"><span data-stu-id="6a828-113">Example Query</span></span>  
 <span data-ttu-id="6a828-114">次の例を使用して、この記事で説明するクエリ処理の概念を示します。</span><span class="sxs-lookup"><span data-stu-id="6a828-114">The following example will be used to illustrate the query processing concepts discussed in this article.</span></span>  
  
 <span data-ttu-id="6a828-115">ここでは、Customer と Order という 2 個のテーブルについて検討します。</span><span class="sxs-lookup"><span data-stu-id="6a828-115">We consider two tables, Customer and Order.</span></span> <span data-ttu-id="6a828-116">次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトには、2 個のテーブルおよび関連するインデックスの定義が (従来の) ディスク ベース形式で含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a828-116">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] script contains the definitions for these two tables and associated indexes, in their (traditional) disk-based form:</span></span>  
  
```sql  
CREATE TABLE dbo.[Customer] (  
  CustomerID nchar (5) NOT NULL PRIMARY KEY,  
  ContactName nvarchar (30) NOT NULL   
)  
GO  
  
CREATE TABLE dbo.[Order] (  
  OrderID int NOT NULL PRIMARY KEY,  
  CustomerID nchar (5) NOT NULL,  
  OrderDate date NOT NULL  
)  
GO  
CREATE INDEX IX_CustomerID ON dbo.[Order](CustomerID)  
GO  
CREATE INDEX IX_OrderDate ON dbo.[Order](OrderDate)  
GO  
```  
  
 <span data-ttu-id="6a828-117">ここでは、クエリ プランを構築できるように、2 個のテーブルに Northwind サンプル データベースのサンプル データが読み込まれています。このサンプル データベースは「 [SQL Server 2000 用の Northwind サンプル データベースと pubs サンプル データベース](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="6a828-117">For constructing the query plans shown in this article, the two tables were populated with sample data from the Northwind sample database, which you can download from [Northwind and pubs Sample Databases for SQL Server 2000](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>  
  
 <span data-ttu-id="6a828-118">次のクエリについて考えてみます。このクエリでは、Customer テーブルと Order テーブルを結合し、注文の ID および関連付けられた顧客情報を返します。</span><span class="sxs-lookup"><span data-stu-id="6a828-118">Consider the following query, which joins the tables Customer and Order and returns the ID of the order and the associated customer information:</span></span>  
  
```sql  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="6a828-119">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] では、次のような推定実行プランが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-119">The estimated execution plan as displayed by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] is as follows</span></span>  
  
 <span data-ttu-id="6a828-120">![ディスク ベース テーブルの結合のためのクエリ プラン。](../../database-engine/media/hekaton-query-plan-1.gif "ディスク ベース テーブルの結合のためのクエリ プラン。")</span><span class="sxs-lookup"><span data-stu-id="6a828-120">![Query plan for join of disk-based tables.](../../database-engine/media/hekaton-query-plan-1.gif "Query plan for join of disk-based tables.")</span></span>  
<span data-ttu-id="6a828-121">ディスク ベース テーブルの結合のためのクエリ プラン。</span><span class="sxs-lookup"><span data-stu-id="6a828-121">Query plan for join of disk-based tables.</span></span>  
  
 <span data-ttu-id="6a828-122">このクエリ プランについて</span><span class="sxs-lookup"><span data-stu-id="6a828-122">About this query plan:</span></span>  
  
-   <span data-ttu-id="6a828-123">Customer テーブルの行は、クラスター化インデックスから取得されます。これは、テーブル データ全体を含んでいるプライマリ データ構造になっています。</span><span class="sxs-lookup"><span data-stu-id="6a828-123">The rows from the Customer table are retrieved from the clustered index, which is the primary data structure and has the full table data.</span></span>  
  
-   <span data-ttu-id="6a828-124">Order テーブルのデータは、CustomerID 列の非クラスター化インデックスを使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-124">Data from the Order table is retrieved using the nonclustered index on the CustomerID column.</span></span> <span data-ttu-id="6a828-125">このインデックスには、結合に使用される CustomerID 列と、ユーザーに返す主キー列 OrderID の両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a828-125">This index contains both the CustomerID column, which is used for the join, and the primary key column OrderID, which is returned to the user.</span></span> <span data-ttu-id="6a828-126">Order テーブルから追加の列を返す場合は、Order テーブルのクラスター化インデックス内の参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="6a828-126">Returning additional columns from the Order table would require lookups in the clustered index for the Order table.</span></span>  
  
-   <span data-ttu-id="6a828-127">`Inner Join` 論理操作は、`Merge Join` 物理操作により実装されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-127">The logical operator `Inner Join` is implemented by the physical operator `Merge Join`.</span></span> <span data-ttu-id="6a828-128">その他の物理結合の種類は、`Nested Loops` と `Hash Join` です。</span><span class="sxs-lookup"><span data-stu-id="6a828-128">The other physical join types are `Nested Loops` and `Hash Join`.</span></span> <span data-ttu-id="6a828-129">この `Merge Join` 操作では、両方のインデックスが結合列 CustomerID を基準に並べ替えられていることを利用します。</span><span class="sxs-lookup"><span data-stu-id="6a828-129">The `Merge Join` operator takes advantage of the fact that both indexes are sorted on the join column CustomerID.</span></span>  
  
 <span data-ttu-id="6a828-130">これを少し変えたバリエーションとして、OrderID だけでなく、Order テーブルのすべての行を返すクエリを検討します。</span><span class="sxs-lookup"><span data-stu-id="6a828-130">Consider a slight variation on this query, which returns all rows from the Order table, not only OrderID:</span></span>  
  
```sql  
SELECT o.*, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="6a828-131">このクエリの推定プランは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6a828-131">The estimated plan for this query is:</span></span>  
  
 <span data-ttu-id="6a828-132">![ディスク ベース テーブルのハッシュ結合のクエリ プラン。](../../database-engine/media/hekaton-query-plan-2.gif "ディスク ベース テーブルのハッシュ結合のクエリ プラン。")</span><span class="sxs-lookup"><span data-stu-id="6a828-132">![Query plan for a hash join of disk-based tables.](../../database-engine/media/hekaton-query-plan-2.gif "Query plan for a hash join of disk-based tables.")</span></span>  
<span data-ttu-id="6a828-133">ディスク ベース テーブルのハッシュ結合のクエリ プラン。</span><span class="sxs-lookup"><span data-stu-id="6a828-133">Query plan for a hash join of disk-based tables.</span></span>  
  
 <span data-ttu-id="6a828-134">このクエリでは、Orders テーブルの行はクラスター化インデックスを使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-134">In this query, rows from the Order table are retrieved using the clustered index.</span></span> <span data-ttu-id="6a828-135">これで、`Hash Match` 物理操作は `Inner Join` に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-135">The `Hash Match` physical operator is now used for the `Inner Join`.</span></span> <span data-ttu-id="6a828-136">Order のクラスター化インデックスは CustomerID で並べ替えられません。したがって、`Merge Join` はパフォーマンスに影響を与える並べ替え操作を必要とします。</span><span class="sxs-lookup"><span data-stu-id="6a828-136">The clustered index on Order is not sorted on CustomerID, and so a `Merge Join` would require a sort operator, which would affect performance.</span></span> <span data-ttu-id="6a828-137">前の例の `Hash Match` 操作のコスト (46%) と比較して、`Merge Join` 操作 (75%) の相対コストを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-137">Note the relative cost of the `Hash Match` operator (75%) compared with the cost of the `Merge Join` operator in the previous example (46%).</span></span> <span data-ttu-id="6a828-138">オプティマイザーでは、前の例でも `Hash Match` 操作を検討したうえで、`Merge Join` 操作の方がパフォーマンスがよいと判断されています。</span><span class="sxs-lookup"><span data-stu-id="6a828-138">The optimizer would have considered the `Hash Match` operator also in the previous example, but concluded that the `Merge Join` operator gave better performance.</span></span>  
  
## <a name="ssnoversion-query-processing-for-disk-based-tables"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6a828-139">ディスク ベース テーブルに対するクエリ処理</span><span class="sxs-lookup"><span data-stu-id="6a828-139">Query Processing for Disk-Based Tables</span></span>  
 <span data-ttu-id="6a828-140">次の図は、アドホック クエリに対する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のクエリ処理フローの概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a828-140">The following diagram outlines the query processing flow in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for ad hoc queries:</span></span>  
  
 <span data-ttu-id="6a828-141">![SQL Server クエリ処理パイプライン。](../../database-engine/media/hekaton-query-plan-3.gif "SQL Server クエリ処理パイプライン。")</span><span class="sxs-lookup"><span data-stu-id="6a828-141">![SQL Server query processing pipeline.](../../database-engine/media/hekaton-query-plan-3.gif "SQL Server query processing pipeline.")</span></span>  
<span data-ttu-id="6a828-142">SQL Server クエリ処理パイプライン。</span><span class="sxs-lookup"><span data-stu-id="6a828-142">SQL Server query processing pipeline.</span></span>  
  
 <span data-ttu-id="6a828-143">このシナリオでは:</span><span class="sxs-lookup"><span data-stu-id="6a828-143">In this scenario:</span></span>  
  
1.  <span data-ttu-id="6a828-144">ユーザーがクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="6a828-144">The user issues a query.</span></span>  
  
2.  <span data-ttu-id="6a828-145">パーサーと algebrizer は、ユーザーから送信される [!INCLUDE[tsql](../../../includes/tsql-md.md)] テキストに基づき、論理操作でクエリ ツリーを構築します。</span><span class="sxs-lookup"><span data-stu-id="6a828-145">The parser and algebrizer construct a query tree with logical operators based on the [!INCLUDE[tsql](../../../includes/tsql-md.md)] text submitted by the user.</span></span>  
  
3.  <span data-ttu-id="6a828-146">オプティマイザーは物理操作 (たとえば、Nested Loops 結合) を含む最適化されたクエリ プランを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a828-146">The optimizer creates an optimized query plan containing physical operators (for example, nested-loops join).</span></span> <span data-ttu-id="6a828-147">最適化後に、そのプランはプラン キャッシュに保存される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6a828-147">After optimization, the plan may be stored in the plan cache.</span></span> <span data-ttu-id="6a828-148">プラン キャッシュにこのクエリのプランが既に含まれている場合、この手順は省略されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-148">This step is bypassed if the plan cache already contains a plan for this query.</span></span>  
  
4.  <span data-ttu-id="6a828-149">クエリ実行エンジンは、クエリ プランの解釈を処理します。</span><span class="sxs-lookup"><span data-stu-id="6a828-149">The query execution engine processes an interpretation of the query plan.</span></span>  
  
5.  <span data-ttu-id="6a828-150">各インデックスのシーク、インデックス スキャン、およびテーブル スキャン操作では、実行エンジンはそれぞれのインデックスおよびテーブルの構造からの行を Access Methods から要求します。</span><span class="sxs-lookup"><span data-stu-id="6a828-150">For each index seek, index scan, and table scan operator, the execution engine requests rows from the respective index and table structures from Access Methods.</span></span>  
  
6.  <span data-ttu-id="6a828-151">Access Methods は、バッファー プールのインデックスおよびデータ ページから行を取得し、必要に応じてバッファー プールにディスクからページを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="6a828-151">Access Methods retrieves the rows from the index and data pages in the buffer pool and loads pages from disk into the buffer pool as needed.</span></span>  
  
 <span data-ttu-id="6a828-152">クエリの最初の例の場合、実行エンジンは、Customer のクラスター化インデックスおよび Order の非クラスター化インデックスの行を Access Methods から要求します。</span><span class="sxs-lookup"><span data-stu-id="6a828-152">For the first example query, the execution engine requests rows in the clustered index on Customer and the nonclustered index on Order from Access Methods.</span></span> <span data-ttu-id="6a828-153">Access Methods は、要求された行を取得するために B ツリー インデックス構造をスキャンします。</span><span class="sxs-lookup"><span data-stu-id="6a828-153">Access Methods traverses the B-tree index structures to retrieve the requested rows.</span></span> <span data-ttu-id="6a828-154">この場合は、プランがフル インデックス スキャンを必要とするため、すべての行が取得されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-154">In this case all rows are retrieved as the plan calls for full index scans.</span></span>  
  
## <a name="interpreted-tsql-access-to-memory-optimized-tables"></a><span data-ttu-id="6a828-155">解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] によるメモリ最適化テーブルへのアクセス</span><span class="sxs-lookup"><span data-stu-id="6a828-155">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] Access to Memory-Optimized Tables</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="6a828-156">アドホック バッチおよびストアド プロシージャは、解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)]とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="6a828-156">ad hoc batches and stored procedures are also referred to as interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6a828-157">"解釈された" とは、クエリ プラン内の各演算子について、クエリ実行エンジンによってクエリ プランが解釈されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6a828-157">Interpreted refers to the fact that the query plan is interpreted by the query execution engine for each operator in the query plan.</span></span> <span data-ttu-id="6a828-158">実行エンジンは、演算子とそのパラメーターを読み取り、操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="6a828-158">The execution engine reads the operator and its parameters and performs the operation.</span></span>  
  
 <span data-ttu-id="6a828-159">解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して、メモリ最適化テーブルとディスク ベース テーブルの両方にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6a828-159">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] can be used to access both memory-optimized and disk-based tables.</span></span> <span data-ttu-id="6a828-160">次の図は、解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] によるメモリ最適化テーブルへのアクセスのクエリ処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a828-160">The following figure illustrates query processing for interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] access to memory-optimized tables:</span></span>  
  
 <span data-ttu-id="6a828-161">![解釈された tsql のクエリ処理パイプライン。](../../database-engine/media/hekaton-query-plan-4.gif "解釈された tsql のクエリ処理パイプライン。")</span><span class="sxs-lookup"><span data-stu-id="6a828-161">![Query processing pipeline for interpreted tsql.](../../database-engine/media/hekaton-query-plan-4.gif "Query processing pipeline for interpreted tsql.")</span></span>  
<span data-ttu-id="6a828-162">解釈された Transact-SQL によるメモリ最適化テーブルへのアクセスのクエリ処理パイプライン。</span><span class="sxs-lookup"><span data-stu-id="6a828-162">Query processing pipeline for interpreted Transact-SQL access to memory-optimized tables.</span></span>  
  
 <span data-ttu-id="6a828-163">図で示すように、ほとんどの場合、クエリ処理パイプラインは変更されません。</span><span class="sxs-lookup"><span data-stu-id="6a828-163">As illustrated by the figure, the query processing pipeline remains mostly unchanged:</span></span>  
  
-   <span data-ttu-id="6a828-164">パーサーと algebrizer はクエリ ツリーを構築します。</span><span class="sxs-lookup"><span data-stu-id="6a828-164">The parser and algebrizer construct the query tree.</span></span>  
  
-   <span data-ttu-id="6a828-165">オプティマイザーは実行プランを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a828-165">The optimizer creates the execution plan.</span></span>  
  
-   <span data-ttu-id="6a828-166">クエリ実行エンジンは、実行プランを解釈します。</span><span class="sxs-lookup"><span data-stu-id="6a828-166">The query execution engine interprets the execution plan.</span></span>  
  
 <span data-ttu-id="6a828-167">従来のクエリ処理パイプライン (図 2) との主な相違点は、メモリ最適化テーブルの行が Access Methods を使用してバッファー プールから取得されないことです。</span><span class="sxs-lookup"><span data-stu-id="6a828-167">The main difference with the traditional query processing pipeline (figure 2) is that rows for memory-optimized tables are not retrieved from the buffer pool using Access Methods.</span></span> <span data-ttu-id="6a828-168">代わりに、インメモリ データ構造体からインメモリ OLTP エンジンを使用して行が取得されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-168">Instead, rows are retrieved from the in-memory data structures through the In-Memory OLTP engine.</span></span> <span data-ttu-id="6a828-169">データ構造が異なるために、次の例で示すように、オプティマイザーが異なるプランを引数として取得する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6a828-169">Differences in data structures cause the optimizer to pick different plans in some cases, as illustrated by the following example.</span></span>  
  
 <span data-ttu-id="6a828-170">次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトには、ハッシュ インデックスを使用する Order テーブルと Customer テーブルのメモリ最適化バージョンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a828-170">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] script contains memory-optimized versions of the Order and Customer tables, using hash indexes:</span></span>  
  
```sql  
CREATE TABLE dbo.[Customer] (  
  CustomerID nchar (5) NOT NULL PRIMARY KEY NONCLUSTERED,  
  ContactName nvarchar (30) NOT NULL   
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE TABLE dbo.[Order] (  
  OrderID int NOT NULL PRIMARY KEY NONCLUSTERED,  
  CustomerID nchar (5) NOT NULL INDEX IX_CustomerID HASH(CustomerID) WITH (BUCKET_COUNT=100000),  
  OrderDate date NOT NULL INDEX IX_OrderDate HASH(OrderDate) WITH (BUCKET_COUNT=100000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 <span data-ttu-id="6a828-171">同じクエリをメモリ最適化テーブルで実行するとします。</span><span class="sxs-lookup"><span data-stu-id="6a828-171">Consider the same query executed on memory-optimized tables:</span></span>  
  
```sql  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="6a828-172">推定プランは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6a828-172">The estimated plan is as follows:</span></span>  
  
 <span data-ttu-id="6a828-173">![メモリ最適化テーブルの結合のためのクエリ プラン。](../../database-engine/media/hekaton-query-plan-5.gif "メモリ最適化テーブルの結合のためのクエリ プラン。")</span><span class="sxs-lookup"><span data-stu-id="6a828-173">![Query plan for join of memory optimized tables.](../../database-engine/media/hekaton-query-plan-5.gif "Query plan for join of memory optimized tables.")</span></span>  
<span data-ttu-id="6a828-174">メモリ最適化テーブルの結合のためのクエリ プラン。</span><span class="sxs-lookup"><span data-stu-id="6a828-174">Query plan for join of memory-optimized tables.</span></span>  
  
 <span data-ttu-id="6a828-175">ディスク ベース テーブルの同じクエリに対するプラン (図 1) で、次の相違点を確認します。</span><span class="sxs-lookup"><span data-stu-id="6a828-175">Observe the following differences with the plan for the same query on disk-based tables (figure 1):</span></span>  
  
-   <span data-ttu-id="6a828-176">このプランでは、Customer テーブルに対するクラスター化インデックス スキャンではなくテーブル スキャンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a828-176">This plan contains a table scan rather than a clustered index scan for the table Customer:</span></span>  
  
    -   <span data-ttu-id="6a828-177">テーブルの定義には、クラスター化インデックスが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="6a828-177">The definition of the table does not contain a clustered index.</span></span>  
  
    -   <span data-ttu-id="6a828-178">クラスター化インデックスは、メモリ最適化テーブルでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6a828-178">Clustered indexes are not supported with memory-optimized tables.</span></span> <span data-ttu-id="6a828-179">代わりに、すべてのメモリ最適化テーブルには 1 つ以上の非クラスター化インデックスが必要です。メモリ最適化テーブルのすべてのインデックスは、そのテーブル内のすべての列に効率的にアクセスできます。列をインデックスに格納したり、クラスター化されたインデックスを参照したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6a828-179">Instead, every memory-optimized table must have at least one nonclustered index and all indexes on memory-optimized tables can efficiently access all columns in the table without having to store them in the index or refer to a clustered index.</span></span>  
  
-   <span data-ttu-id="6a828-180">このプランには、`Hash Match` ではなく `Merge Join` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6a828-180">This plan contains a `Hash Match` rather than a `Merge Join`.</span></span> <span data-ttu-id="6a828-181">Order テーブルと Customer テーブルの両方のインデックスはハッシュ インデックスになるため、順序付けされません。</span><span class="sxs-lookup"><span data-stu-id="6a828-181">The indexes on both the Order and the Customer table are hash indexes, and are thus not ordered.</span></span> <span data-ttu-id="6a828-182">`Merge Join` では並べ替え操作が必要であり、それによってパフォーマンスが低下していました。</span><span class="sxs-lookup"><span data-stu-id="6a828-182">A `Merge Join` would require sort operators that would decrease performance.</span></span>  
  
## <a name="natively-compiled-stored-procedures"></a><span data-ttu-id="6a828-183">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="6a828-183">Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6a828-184">ネイティブ コンパイル ストアド プロシージャは、クエリ実行エンジンによって解釈されるのではなく、マシン語コードにコンパイルされる [!INCLUDE[tsql](../../../includes/tsql-md.md)] ストアド プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="6a828-184">Natively compiled stored procedures are [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures compiled to machine code, rather than interpreted by the query execution engine.</span></span> <span data-ttu-id="6a828-185">次のスクリプトは、(クエリの例のセクションの) クエリの例を実行する、ネイティブ コンパイル ストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a828-185">The following script creates a natively compiled stored procedure that runs the example query (from the Example Query section).</span></span>  
  
```sql  
CREATE PROCEDURE usp_SampleJoin  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = 'english')  
  
  SELECT o.OrderID, c.CustomerID, c.ContactName   
FROM dbo.[Order] o INNER JOIN dbo.[Customer] c   
  ON c.CustomerID = o.CustomerID  
  
END  
```  
  
 <span data-ttu-id="6a828-186">ネイティブ コンパイル ストアド プロシージャは作成時にコンパイルされ、解釈されたストアド プロシージャは最初の実行時にコンパイルされます</span><span class="sxs-lookup"><span data-stu-id="6a828-186">Natively compiled stored procedures are compiled at create time, whereas interpreted stored procedures are compiled at first execution time.</span></span> <span data-ttu-id="6a828-187">(コンパイルの一部、特に解析と algebrizer の処理は作成時に実行されますが、</span><span class="sxs-lookup"><span data-stu-id="6a828-187">(A portion of the compilation, particularly parsing and algebrization, take place at create.</span></span> <span data-ttu-id="6a828-188">解釈されたストアド プロシージャの場合は、最初の実行時にクエリ プランの最適化が実行されます)。再コンパイルの論理と似ています。</span><span class="sxs-lookup"><span data-stu-id="6a828-188">However, for interpreted stored procedures, optimization of the query plans takes place at first execution.) The recompilation logic is similar.</span></span> <span data-ttu-id="6a828-189">サーバーを再起動した場合、ネイティブ コンパイル ストアド プロシージャは、プロシージャの最初の実行時に再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="6a828-189">Natively compiled stored procedures are recompiled on first execution of the procedure if the server is restarted.</span></span> <span data-ttu-id="6a828-190">解釈されたストアド プロシージャは、そのプランがプラン キャッシュに存在しなくなった場合は再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="6a828-190">Interpreted stored procedures are recompiled if the plan is no longer in the plan cache.</span></span> <span data-ttu-id="6a828-191">次の表は、ネイティブ コンパイル ストアド プロシージャと解釈されたストアド プロシージャの両方について、コンパイルおよび再コンパイルのケースをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="6a828-191">The following table summarizes compilation and recompilation cases for both natively compiled and interpreted stored procedures:</span></span>  
  
||<span data-ttu-id="6a828-192">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="6a828-192">Natively compiled</span></span>|<span data-ttu-id="6a828-193">解釈された</span><span class="sxs-lookup"><span data-stu-id="6a828-193">Interpreted</span></span>|  
|-|-----------------------|-----------------|  
|<span data-ttu-id="6a828-194">最初のコンパイル</span><span class="sxs-lookup"><span data-stu-id="6a828-194">Initial compilation</span></span>|<span data-ttu-id="6a828-195">作成時。</span><span class="sxs-lookup"><span data-stu-id="6a828-195">At create time.</span></span>|<span data-ttu-id="6a828-196">最初の実行時。</span><span class="sxs-lookup"><span data-stu-id="6a828-196">At first execution.</span></span>|  
|<span data-ttu-id="6a828-197">自動再コンパイル</span><span class="sxs-lookup"><span data-stu-id="6a828-197">Automatic recompilation</span></span>|<span data-ttu-id="6a828-198">データベースまたはサーバーの再起動後、プロシージャの最初の実行時。</span><span class="sxs-lookup"><span data-stu-id="6a828-198">Upon first execution of the procedure after a database or server restart.</span></span>|<span data-ttu-id="6a828-199">サーバーの再起動時。</span><span class="sxs-lookup"><span data-stu-id="6a828-199">On server restart.</span></span> <span data-ttu-id="6a828-200">または、通常はスキーマや統計の変更またはメモリ不足に基づく、プラン キャッシュからの削除時。</span><span class="sxs-lookup"><span data-stu-id="6a828-200">Or, eviction from the plan cache, usually based on schema or stats changes, or memory pressure.</span></span>|  
|<span data-ttu-id="6a828-201">手動での再コンパイル</span><span class="sxs-lookup"><span data-stu-id="6a828-201">Manual recompilation</span></span>|<span data-ttu-id="6a828-202">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6a828-202">Not supported.</span></span> <span data-ttu-id="6a828-203">回避策は、ストアド プロシージャを削除して再作成することです。</span><span class="sxs-lookup"><span data-stu-id="6a828-203">The workaround is to drop and recreate the stored procedure.</span></span>|<span data-ttu-id="6a828-204">`sp_recompile` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-204">Use `sp_recompile`.</span></span> <span data-ttu-id="6a828-205">たとえば DBCC FREEPROCCACHE を使用して、キャッシュからプランを手動で削除できます。</span><span class="sxs-lookup"><span data-stu-id="6a828-205">You can manually evict the plan from the cache, for example through DBCC FREEPROCCACHE.</span></span> <span data-ttu-id="6a828-206">また、WITH RECOMPILE ストアド プロシージャを作成することもできます。このストアド プロシージャは、実行のたびに再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="6a828-206">You can also create the stored procedure WITH RECOMPILE and the stored procedure will be recompiled at every execution.</span></span>|  
  
### <a name="compilation-and-query-processing"></a><span data-ttu-id="6a828-207">コンパイルとクエリ処理</span><span class="sxs-lookup"><span data-stu-id="6a828-207">Compilation and Query Processing</span></span>  
 <span data-ttu-id="6a828-208">次の図は、ネイティブ コンパイル ストアド プロシージャのコンパイル処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a828-208">The following diagram illustrates the compilation process for natively compiled stored procedures:</span></span>  
  
 <span data-ttu-id="6a828-209">![ストアド プロシージャのネイティブでのコンパイル](../../database-engine/media/hekaton-query-plan-6.gif "ストアド プロシージャのネイティブでのコンパイル")</span><span class="sxs-lookup"><span data-stu-id="6a828-209">![Native compilation of stored procedures.](../../database-engine/media/hekaton-query-plan-6.gif "Native compilation of stored procedures.")</span></span>  
<span data-ttu-id="6a828-210">ストアド プロシージャのネイティブでのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6a828-210">Native compilation of stored procedures.</span></span>  
  
 <span data-ttu-id="6a828-211">この処理は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6a828-211">The process is described as,</span></span>  
  
1.  <span data-ttu-id="6a828-212">ユーザーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対して `CREATE PROCEDURE` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6a828-212">The user issues a `CREATE PROCEDURE` statement to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="6a828-213">パーサーと algebrizer は、プロシージャの処理フロー、およびストアド プロシージャ内の [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリのクエリ ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a828-213">The parser and algebrizer create the processing flow for the procedure, as well as query trees for the [!INCLUDE[tsql](../../../includes/tsql-md.md)] queries in the stored procedure.</span></span>  
  
3.  <span data-ttu-id="6a828-214">オプティマイザーは、ストアド プロシージャ内のすべてのクエリに対して最適化されたクエリ実行プランを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a828-214">The optimizer creates optimized query execution plans for all the queries in the stored procedure.</span></span>  
  
4.  <span data-ttu-id="6a828-215">インメモリ OLTP コンパイラは、埋め込みの最適化されたクエリ プランで処理フローを受け取り、ストアド プロシージャを実行するためのマシン語コードを含む DLL を生成します。</span><span class="sxs-lookup"><span data-stu-id="6a828-215">The In-Memory OLTP compiler takes the processing flow with the embedded optimized query plans and generates a DLL that contains the machine code for executing the stored procedure.</span></span>  
  
5.  <span data-ttu-id="6a828-216">生成された DLL がメモリに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6a828-216">The generated DLL is loaded into memory.</span></span>  
  
 <span data-ttu-id="6a828-217">ネイティブ コンパイル ストアド プロシージャの呼び出しは、DLL 内の関数の呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-217">Invocation of a natively compiled stored procedure translates to calling a function in the DLL.</span></span>  
  
 <span data-ttu-id="6a828-218">![ネイティブ コンパイル ストアド プロシージャの実行。](../../database-engine/media/hekaton-query-plan-7.gif "ネイティブ コンパイル ストアド プロシージャの実行。")</span><span class="sxs-lookup"><span data-stu-id="6a828-218">![Execution of natively compiled stored procedures.](../../database-engine/media/hekaton-query-plan-7.gif "Execution of natively compiled stored procedures.")</span></span>  
<span data-ttu-id="6a828-219">ネイティブ コンパイル ストアド プロシージャの実行。</span><span class="sxs-lookup"><span data-stu-id="6a828-219">Execution of natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="6a828-220">ネイティブ コンパイル ストアド プロシージャの呼び出しは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6a828-220">Invocation of a natively compiled stored procedure is described as follows:</span></span>  
  
1.  <span data-ttu-id="6a828-221">ユーザーは、 `EXEC` *usp_myproc*ステートメントを発行します。</span><span class="sxs-lookup"><span data-stu-id="6a828-221">The user issues an `EXEC`*usp_myproc* statement.</span></span>  
  
2.  <span data-ttu-id="6a828-222">パーサーは、名前とストアド プロシージャのパラメーターを抽出します。</span><span class="sxs-lookup"><span data-stu-id="6a828-222">The parser extracts the name and stored procedure parameters.</span></span>  
  
     <span data-ttu-id="6a828-223">たとえば `sp_prep_exec` を使用して、ステートメントが準備されている場合、パーサーは実行時にプロシージャ名とパラメーターを抽出する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6a828-223">If the statement was prepared, for example using `sp_prep_exec`, the parser does not need to extract the procedure name and parameters at execution time.</span></span>  
  
3.  <span data-ttu-id="6a828-224">インメモリ OLTP ランタイムがストアド プロシージャに対する DLL エントリ ポイントを特定します。</span><span class="sxs-lookup"><span data-stu-id="6a828-224">The In-Memory OLTP runtime locates the DLL entry point for the stored procedure.</span></span>  
  
4.  <span data-ttu-id="6a828-225">DLL のマシン語コードが実行され、その結果がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-225">The machine code in the DLL is executed and the results of are returned to the client.</span></span>  
  
 <span data-ttu-id="6a828-226">**パラメーターを見つけ出す**</span><span class="sxs-lookup"><span data-stu-id="6a828-226">**Parameter sniffing**</span></span>  
  
 <span data-ttu-id="6a828-227">解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] ストアド プロシージャは最初の実行時にコンパイルされますが、ネイティブ コンパイル ストアド プロシージャは作成時にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="6a828-227">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures are compiled at first execution, in contrast to natively compiled stored procedures, which are compiled at create time.</span></span> <span data-ttu-id="6a828-228">解釈されたストアド プロシージャが呼び出し時にコンパイルされる場合、この呼び出しに指定されたパラメーターの値が、実行プランの生成時にオプティマイザーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-228">When interpreted stored procedures are compiled at invocation, the values of the parameters supplied for this invocation are used by the optimizer when generating the execution plan.</span></span> <span data-ttu-id="6a828-229">コンパイル時にパラメーターをこのように使用することを、"パラメーターを見つけ出す" と表現します。</span><span class="sxs-lookup"><span data-stu-id="6a828-229">This use of parameters during compilation is called parameter sniffing.</span></span>  
  
 <span data-ttu-id="6a828-230">パラメーターを見つけ出すことは、ネイティブ コンパイル ストアド プロシージャのコンパイルには使用されません。</span><span class="sxs-lookup"><span data-stu-id="6a828-230">Parameter sniffing is not used for compiling natively compiled stored procedures.</span></span> <span data-ttu-id="6a828-231">ストアド プロシージャに対するすべてのパラメーターは、UNKNOWN 値があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="6a828-231">All parameters to the stored procedure are considered to have UNKNOWN values.</span></span> <span data-ttu-id="6a828-232">解釈されたストアド プロシージャと同様に、ネイティブ コンパイル ストアド プロシージャでも、`OPTIMIZE FOR` ヒントがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6a828-232">Like interpreted stored procedures, natively compiled stored procedures also support the `OPTIMIZE FOR` hint.</span></span> <span data-ttu-id="6a828-233">詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-233">For more information, see [Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
### <a name="retrieving-a-query-execution-plan-for-natively-compiled-stored-procedures"></a><span data-ttu-id="6a828-234">ネイティブ コンパイル ストアド プロシージャ用のクエリ実行プランの取得</span><span class="sxs-lookup"><span data-stu-id="6a828-234">Retrieving a Query Execution Plan for Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6a828-235">ネイティブ コンパイル ストアド プロシージャ用のクエリ実行プランは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の **推定実行プラン** または [!INCLUDE[tsql](../../../includes/tsql-md.md)]の SHOWPLAN_XML オプションを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="6a828-235">The query execution plan for a natively compiled stored procedure can be retrieved using **Estimated Execution Plan** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or using the SHOWPLAN_XML option in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6a828-236">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6a828-236">For example:</span></span>  
  
```sql  
SET SHOWPLAN_XML ON  
GO  
EXEC dbo.usp_myproc  
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 <span data-ttu-id="6a828-237">クエリ オプティマイザーによって生成される実行プランは、ノード上のクエリ演算子を含むツリーおよびツリーのリーフで構成されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-237">The execution plan generated by the query optimizer consists of a tree with query operators on the nodes and leaves of the tree.</span></span> <span data-ttu-id="6a828-238">ツリーの構造により、演算子間の対話 (演算子間での行のフロー) が決定されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-238">The structure of the tree determines the interaction (the flow of rows from one operator to another) between the operators.</span></span> <span data-ttu-id="6a828-239">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]のグラフィカルなビューでは、フローは右から左に流れます。</span><span class="sxs-lookup"><span data-stu-id="6a828-239">In the graphical view of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the flow is from right to left.</span></span> <span data-ttu-id="6a828-240">たとえば、図 1 のクエリ プランは、2 個のインデックス スキャン操作を含み、マージ結合操作に行を渡しています。</span><span class="sxs-lookup"><span data-stu-id="6a828-240">For example, the query plan in figure 1 contains two index scan operators, which supplies rows to a merge join operator.</span></span> <span data-ttu-id="6a828-241">マージ結合操作が選択操作に行を渡します。</span><span class="sxs-lookup"><span data-stu-id="6a828-241">The merge join operator supplies rows to a select operator.</span></span> <span data-ttu-id="6a828-242">選択操作は、最終的にはクライアントに行を返します。</span><span class="sxs-lookup"><span data-stu-id="6a828-242">The select operator, finally, returns the rows to the client.</span></span>  
  
### <a name="query-operators-in-natively-compiled-stored-procedures"></a><span data-ttu-id="6a828-243">ネイティブ コンパイル ストアド プロシージャのクエリ演算子</span><span class="sxs-lookup"><span data-stu-id="6a828-243">Query Operators in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6a828-244">次の表は、ネイティブ コンパイル ストアド プロシージャの内部でサポートされるクエリ演算子をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="6a828-244">The following table summarizes the query operators supported inside natively compiled stored procedures:</span></span>  
  
|<span data-ttu-id="6a828-245">演算子</span><span class="sxs-lookup"><span data-stu-id="6a828-245">Operator</span></span>|<span data-ttu-id="6a828-246">サンプル クエリ</span><span class="sxs-lookup"><span data-stu-id="6a828-246">Sample query</span></span>|  
|--------------|------------------|  
|<span data-ttu-id="6a828-247">SELECT</span><span class="sxs-lookup"><span data-stu-id="6a828-247">SELECT</span></span>|`SELECT OrderID FROM dbo.[Order]`|  
|<span data-ttu-id="6a828-248">INSERT</span><span class="sxs-lookup"><span data-stu-id="6a828-248">INSERT</span></span>|`INSERT dbo.Customer VALUES ('abc', 'def')`|  
|<span data-ttu-id="6a828-249">UPDATE</span><span class="sxs-lookup"><span data-stu-id="6a828-249">UPDATE</span></span>|`UPDATE dbo.Customer SET ContactName='ghi' WHERE CustomerID='abc'`|  
|<span data-ttu-id="6a828-250">DELETE</span><span class="sxs-lookup"><span data-stu-id="6a828-250">DELETE</span></span>|`DELETE dbo.Customer WHERE CustomerID='abc'`|  
|<span data-ttu-id="6a828-251">Compute Scalar</span><span class="sxs-lookup"><span data-stu-id="6a828-251">Compute Scalar</span></span>|<span data-ttu-id="6a828-252">この操作は、組み込み関数と型変換の両方で使用されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-252">This operator is used both for intrinsic functions and type conversions.</span></span> <span data-ttu-id="6a828-253">一部の関数と型変換は、ネイティブ コンパイル ストアド プロシージャの内部でサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6a828-253">Not all functions and type conversions are supported inside natively compiled stored procedures.</span></span><br /><br /> `SELECT OrderID+1 FROM dbo.[Order]`|  
|<span data-ttu-id="6a828-254">Nested Loops 結合</span><span class="sxs-lookup"><span data-stu-id="6a828-254">Nested Loops Join</span></span>|<span data-ttu-id="6a828-255">Nested Loops は、ネイティブ コンパイル ストアド プロシージャでサポートされている唯一の結合操作です。</span><span class="sxs-lookup"><span data-stu-id="6a828-255">Nested Loops is the only join operator supported in natively compiled stored procedures.</span></span> <span data-ttu-id="6a828-256">解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] として実行される同じクエリのプランにハッシュ結合またはマージ結合が含まれている場合でも、結合を含むすべてのプランは Nested Loops 操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a828-256">All plans that contain joins will use the Nested Loops operator, even if the plan for same query executed as interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] contains a hash or merge join.</span></span><br /><br /> `SELECT o.OrderID, c.CustomerID`  <br /> `FROM dbo.[Order] o INNER JOIN dbo.[Customer] c`|  
|<span data-ttu-id="6a828-257">並べ替え</span><span class="sxs-lookup"><span data-stu-id="6a828-257">Sort</span></span>|`SELECT ContactName FROM dbo.Customer`  <br /> `ORDER BY ContactName`|  
|<span data-ttu-id="6a828-258">TOP</span><span class="sxs-lookup"><span data-stu-id="6a828-258">Top</span></span>|`SELECT TOP 10 ContactName FROM dbo.Customer`|  
|<span data-ttu-id="6a828-259">Top-sort</span><span class="sxs-lookup"><span data-stu-id="6a828-259">Top-sort</span></span>|<span data-ttu-id="6a828-260">`TOP` 式 (返される行数) が 8,000 行を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="6a828-260">The `TOP` expression (the number of rows to be returned) cannot exceed 8,000 rows.</span></span> <span data-ttu-id="6a828-261">クエリに結合演算子および集計演算子がある場合、処理できる行数はこれより少なくなります。</span><span class="sxs-lookup"><span data-stu-id="6a828-261">Fewer if there are also join and aggregation operators in the query.</span></span> <span data-ttu-id="6a828-262">一般的に結合と集計を行うと、並べ替える行数は、ベース テーブルの行数より少なくなります。</span><span class="sxs-lookup"><span data-stu-id="6a828-262">Joins and aggregation do typically reduce the number of rows to be sorted, compared with the row count of the base tables.</span></span><br /><br /> `SELECT TOP 10 ContactName FROM dbo.Customer`  <br /> `ORDER BY ContactName`|  
|<span data-ttu-id="6a828-263">Stream Aggregate</span><span class="sxs-lookup"><span data-stu-id="6a828-263">Stream Aggregate</span></span>|<span data-ttu-id="6a828-264">Hash Match 操作が集計をサポートしていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-264">Note that the Hash Match operator is not supported for aggregation.</span></span> <span data-ttu-id="6a828-265">したがって、解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] 内の同じクエリに対するプランが Hash Match 操作を使用しても、ネイティブ コンパイル ストアド プロシージャ内のすべての集計は Stream Aggregate 操作を使用します</span><span class="sxs-lookup"><span data-stu-id="6a828-265">Therefore, all aggregation in natively compiled stored procedures uses the Stream Aggregate operator, even if the plan for the same query in interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] uses the Hash Match operator.</span></span><br /><br /> `SELECT count(CustomerID) FROM dbo.Customer`|  
  
## <a name="column-statistics-and-joins"></a><span data-ttu-id="6a828-266">列統計と結合</span><span class="sxs-lookup"><span data-stu-id="6a828-266">Column Statistics and Joins</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6a828-267">インデックス スキャンやインデックス シークなど特定の操作のコストを推定できるように、インデックス キー列に値の統計を保持します。</span><span class="sxs-lookup"><span data-stu-id="6a828-267">maintains statistics on values in index key columns to help estimate the cost of certain operations, such as index scan and index seeks.</span></span> <span data-ttu-id="6a828-268">([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、非インデックス キー列に対しても、明示的に作成された場合またはクエリ オプティマイザーによってクエリの述語に応じて作成された場合、統計が作成されます)。コストの推定の主要な基準は、1 個の操作によって処理される行数です。</span><span class="sxs-lookup"><span data-stu-id="6a828-268">( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also creates statistics on non-index key columns if you explicitly create them or if the query optimizer creates them in response to a query with a predicate.) The main metric in cost estimation is the number of rows processed by a single operator.</span></span> <span data-ttu-id="6a828-269">ディスク ベース テーブルの場合、コストの推定では、特定の操作でアクセスされるページ数が重要です。</span><span class="sxs-lookup"><span data-stu-id="6a828-269">Note that for disk-based tables, the number of pages accessed by a particular operator is significant in cost estimation.</span></span> <span data-ttu-id="6a828-270">ただし、メモリ最適化テーブルではページ数は重要ではないため (常にゼロ)、ここでは行数を中心に説明します。</span><span class="sxs-lookup"><span data-stu-id="6a828-270">However, as page count is not important for memory-optimized tables (it is always zero), this discussion focuses on row count.</span></span> <span data-ttu-id="6a828-271">推定は、プラン内のインデックス シークおよびスキャン操作で開始され、続いて、結合操作などの他の操作へと進みます。</span><span class="sxs-lookup"><span data-stu-id="6a828-271">The estimation starts with the index seek and scan operators in the plan, and is then extended to include the other operators, like the join operator.</span></span> <span data-ttu-id="6a828-272">結合操作によって処理される行数の推定値は、基になるインデックス、シーク、およびスキャン操作の推定値に基づきます。</span><span class="sxs-lookup"><span data-stu-id="6a828-272">The estimated number of rows to be processed by a join operator is based on the estimation for the underlying index, seek, and scan operators.</span></span> <span data-ttu-id="6a828-273">解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] によるメモリ最適化テーブルへのアクセスの場合は、実際の実行プランを調べて、プラン内の操作の推定行数と実際の行数の違いを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="6a828-273">For interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] access to memory-optimized tables, you can observe the actual execution plan to see the difference between the estimated and actual row counts for the operators in the plan.</span></span>  
  
 <span data-ttu-id="6a828-274">図 1 の例の場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6a828-274">For the example in figure 1,</span></span>  
  
-   <span data-ttu-id="6a828-275">Customer でのクラスター化インデックス スキャンは、推定値が 91、実際の値が 91。</span><span class="sxs-lookup"><span data-stu-id="6a828-275">The clustered index scan on Customer has estimated 91; actual 91.</span></span>  
  
-   <span data-ttu-id="6a828-276">CustomerID での非クラスター化インデックス スキャンは、推定値が 830、実際の値が 830。</span><span class="sxs-lookup"><span data-stu-id="6a828-276">The nonclustered index scan on CustomerID has estimated 830; actual 830.</span></span>  
  
-   <span data-ttu-id="6a828-277">マージ結合操作は、推定値が 815、実際の値が 830。</span><span class="sxs-lookup"><span data-stu-id="6a828-277">The Merge Join operator has estimated 815; actual 830.</span></span>  
  
 <span data-ttu-id="6a828-278">インデックス スキャンの推定値は正確です。</span><span class="sxs-lookup"><span data-stu-id="6a828-278">The estimates for the index scans are accurate.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6a828-279">ディスク ベース テーブルの行数を保持します。</span><span class="sxs-lookup"><span data-stu-id="6a828-279">maintains the row count for disk-based tables.</span></span> <span data-ttu-id="6a828-280">テーブル全体の推定およびインデックス スキャンは常に正確です。</span><span class="sxs-lookup"><span data-stu-id="6a828-280">Estimates for full table and index scans are always accurate.</span></span> <span data-ttu-id="6a828-281">結合の推定も非常に正確です。</span><span class="sxs-lookup"><span data-stu-id="6a828-281">The estimate for the join is fairly accurate, too.</span></span>  
  
 <span data-ttu-id="6a828-282">これらの推定が変わると、さまざまなプランの選択肢に対するコストの注意点も変わります。</span><span class="sxs-lookup"><span data-stu-id="6a828-282">If these estimates change, the cost considerations for different plan alternatives change as well.</span></span> <span data-ttu-id="6a828-283">たとえば、1 個の結合操作の推定値が 1 または少ない行数である場合、Nested Loops 結合を使用する方が低コストです。</span><span class="sxs-lookup"><span data-stu-id="6a828-283">For example, if one of the sides of the join has an estimated row count of 1 or just a few rows, using a nested loops joins is less expensive.</span></span>  
  
 <span data-ttu-id="6a828-284">次に、クエリのプランを示します。</span><span class="sxs-lookup"><span data-stu-id="6a828-284">The following is the plan for the query:</span></span>  
  
```  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="6a828-285">Customer テーブルで 1 行だけを残してすべての行を削除した後</span><span class="sxs-lookup"><span data-stu-id="6a828-285">After deleting all rows but one in the table Customer:</span></span>  
  
 <span data-ttu-id="6a828-286">![列統計と結合。](../../database-engine/media/hekaton-query-plan-9.gif "列統計と結合。")</span><span class="sxs-lookup"><span data-stu-id="6a828-286">![Column statistics and joins.](../../database-engine/media/hekaton-query-plan-9.gif "Column statistics and joins.")</span></span>  
  
 <span data-ttu-id="6a828-287">このクエリ プランについて</span><span class="sxs-lookup"><span data-stu-id="6a828-287">Regarding this query plan:</span></span>  
  
-   <span data-ttu-id="6a828-288">Hash Match は、Nested Loops 物理結合操作で置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="6a828-288">The Hash Match has been replaced with a Nested Loops physical join operator.</span></span>  
  
-   <span data-ttu-id="6a828-289">IX_CustomerID でのフル インデックス スキャンは、インデックス シークで置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="6a828-289">The full index scan on IX_CustomerID has been replaced with an index seek.</span></span> <span data-ttu-id="6a828-290">これにより、スキャンの対象は 5 行となり、フル インデックス スキャンに必要な 830 行ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="6a828-290">This resulted in scanning 5 rows, instead of the 830 rows required for the full index scan.</span></span>  
  
### <a name="statistics-and-cardinality-for-memory-optimized-tables"></a><span data-ttu-id="6a828-291">メモリ最適化テーブルの統計およびカーディナリティ</span><span class="sxs-lookup"><span data-stu-id="6a828-291">Statistics and Cardinality for Memory-Optimized Tables</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6a828-292">では、メモリ最適化テーブルの列レベルの統計が保持されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-292">maintains column-level statistics for memory-optimized tables.</span></span> <span data-ttu-id="6a828-293">また、テーブルの実際の行数も保持されます。</span><span class="sxs-lookup"><span data-stu-id="6a828-293">In addition, it maintains the actual row count of the table.</span></span> <span data-ttu-id="6a828-294">ただし、ディスク ベース テーブルとは異なり、メモリ最適化テーブルの統計は自動更新されません。</span><span class="sxs-lookup"><span data-stu-id="6a828-294">However, in contrast to disk-based tables, the statistics for memory-optimized tables are not automatically updated.</span></span> <span data-ttu-id="6a828-295">このため、テーブルに重要な変更が発生した場合は、統計を手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a828-295">Therefore, statistics need to be manually updated after significant changes in the tables.</span></span> <span data-ttu-id="6a828-296">詳細については、「 [メモリ最適化テーブルの統計](memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-296">For more information, see [Statistics for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a828-297">参照</span><span class="sxs-lookup"><span data-stu-id="6a828-297">See Also</span></span>  
 [<span data-ttu-id="6a828-298">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="6a828-298">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
