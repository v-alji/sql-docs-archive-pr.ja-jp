---
title: メモリ最適化テーブルの統計 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e644766d-1d1c-43d7-83ff-8ccfe4f3af9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ae09d76c2642e23c56afcdd5ae4e1e468ef5883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740994"
---
# <a name="statistics-for-memory-optimized-tables"></a><span data-ttu-id="9e4ec-102">メモリ最適化テーブルの統計</span><span class="sxs-lookup"><span data-stu-id="9e4ec-102">Statistics for Memory-Optimized Tables</span></span>
  <span data-ttu-id="9e4ec-103">クエリ オプティマイザーでは、クエリのパフォーマンスを向上させるクエリ プランを作成するために列に関する統計を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-103">The query optimizer uses statistics about columns to create query plans that improve query performance.</span></span> <span data-ttu-id="9e4ec-104">統計はデータベースのテーブルから収集され、データベース メタデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-104">Statistics are collected from the tables in the database and stored in the database metadata.</span></span>  
  
 <span data-ttu-id="9e4ec-105">統計は自動的に作成されますが、手動で作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-105">Statistics are created automatically, but can also be created manually.</span></span> <span data-ttu-id="9e4ec-106">たとえば、統計は、インデックスの作成時にインデックス キー列に対して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-106">For example, statistics are created automatically for index key columns when the index is created.</span></span> <span data-ttu-id="9e4ec-107">統計の作成の詳細については、「 [Statistics](../statistics/statistics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-107">For more information about creating statistics see [Statistics](../statistics/statistics.md).</span></span>  
  
 <span data-ttu-id="9e4ec-108">テーブル データは通常、時間の経過に伴い、行が挿入、更新、または削除されて変化します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-108">Table data typically changes over time as rows are inserted, updated, and deleted.</span></span> <span data-ttu-id="9e4ec-109">これは、統計を定期的に更新する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-109">This means statistics need to be updated periodically.</span></span> <span data-ttu-id="9e4ec-110">既定では、ディスク ベース テーブルの統計は、オプティマイザーが統計が古くなったと判断したときに自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-110">By default, statistics on disk-based tables are updated automatically when the optimizer determines they might be out of date.</span></span>  
  
 <span data-ttu-id="9e4ec-111">メモリ最適化テーブルの統計は、既定では更新されません。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-111">Statistics on memory-optimized tables are not updated by default.</span></span> <span data-ttu-id="9e4ec-112">手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-112">Instead, you need to update them manually.</span></span> <span data-ttu-id="9e4ec-113">個々の列、インデックス、またはテーブルに対して、 [transact-sql&#41;&#40;UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-113">Use [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql) for individual columns, indexes, or tables.</span></span> <span data-ttu-id="9e4ec-114">[Sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)を使用して、データベース内のすべてのユーザーと内部テーブルの統計を更新します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-114">Use [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) to update statistics for all user and internal tables in the database.</span></span>  
  
 <span data-ttu-id="9e4ec-115">[CREATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)または[UPDATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/update-statistics-transact-sql)を使用する場合は、 `NORECOMPUTE` メモリ最適化テーブルの統計の自動更新を無効にするように指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-115">When using [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) or [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql), you must specify `NORECOMPUTE` to disable automatic statistics update for memory-optimized tables.</span></span> <span data-ttu-id="9e4ec-116">ディスクベーステーブルの場合、 [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)は、最後の[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)以降にテーブルが変更されている場合にのみ統計を更新します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-116">For disk based tables, [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) only updates statistics if the table has been modified since the last [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span> <span data-ttu-id="9e4ec-117">メモリ最適化テーブルの場合、 [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)は常に更新された統計を生成します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-117">For memory-optimized tables, [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) always generates updated statistics.</span></span> <span data-ttu-id="9e4ec-118">[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)は、メモリ最適化テーブルに適したオプションです。それ以外の場合は、統計を個別に更新できるように、重要な変更が加えられているテーブルを把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-118">[sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) is a good option for memory-optimized tables; otherwise you need to know which tables have significant changes so you can update statistics individually.</span></span>  
  
 <span data-ttu-id="9e4ec-119">統計は、データのサンプリングまたはフルスキャンの実行によって生成できます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-119">Statistics can either be generated by either sampling the data or performing a full scan.</span></span> <span data-ttu-id="9e4ec-120">サンプリング統計は、データ分布を推定するためにテーブル データのサンプルのみを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-120">Sampled statistics only use a sample of the table data to estimate the data distribution.</span></span> <span data-ttu-id="9e4ec-121">フルスキャン統計は、データの分布を調べるためにテーブル全体をスキャンします。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-121">Fullscan statistics scan the entire table to determine the data distribution.</span></span> <span data-ttu-id="9e4ec-122">通常、フルスキャン統計の方が正確ですが、計算にかかる時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-122">Fullscan statistics are usually more accurate but take longer to compute.</span></span> <span data-ttu-id="9e4ec-123">サンプリング統計はより速く収集できます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-123">Sampled statistics can be collected faster.</span></span>  
  
 <span data-ttu-id="9e4ec-124">ディスク ベース テーブルでは、既定ではサンプリング統計が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-124">Disk-based tables use sampled statistics by default.</span></span> <span data-ttu-id="9e4ec-125">メモリ最適化テーブルでは、フルスキャン統計のみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-125">Memory-optimized tables only support fullscan statistics.</span></span> <span data-ttu-id="9e4ec-126">[CREATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)または[UPDATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/update-statistics-transact-sql)を使用する場合は、 `FULLSCAN` メモリ最適化テーブルのオプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-126">When using [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) or [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql), you must specify the `FULLSCAN` option for memory-optimized tables.</span></span>  
  
 <span data-ttu-id="9e4ec-127">メモリ最適化テーブルの統計に関するその他の注意点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-127">Additional considerations for statistics on memory-optimized tables:</span></span>  
  
-   <span data-ttu-id="9e4ec-128">メモリ最適化テーブルのインデックスはテーブルを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-128">Indexes on memory-optimized tables are created with the table.</span></span> <span data-ttu-id="9e4ec-129">インデックス キー列の統計は、テーブルが空のときに作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-129">The statistics on the index key columns are created when the table is empty.</span></span> <span data-ttu-id="9e4ec-130">したがって、これらの統計は、データがテーブルに読み込まれた後に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-130">Therefore, these statistics need to be updated after data is loaded into the table.</span></span>  
  
-   <span data-ttu-id="9e4ec-131">ネイティブ コンパイル ストアド プロシージャの場合、プロシージャのコンパイル時にプロシージャ内のクエリの実行プランが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-131">For natively compiled stored procedures, execution plans for queries in the procedure are optimized when the procedure is compiled.</span></span> <span data-ttu-id="9e4ec-132">これは、統計が更新されたときではなく、プロシージャが作成されたときおよびサーバーが再起動されたときにのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-132">This happens only when the procedure is created and when the server restarts, not when statistics are updated.</span></span> <span data-ttu-id="9e4ec-133">したがって、テーブルには代表的なデータのセットが含まれている必要があり、統計はプロシージャが作成される前に最新の状態にする必要があります </span><span class="sxs-lookup"><span data-stu-id="9e4ec-133">Therefore, the tables need to contain a representative set of data and statistics need to be up-to-date before the procedures are created.</span></span> <span data-ttu-id="9e4ec-134">(ネイティブ コンパイル ストアド プロシージャは、データベースがオフラインになってから再度オンラインに戻った場合、またはサーバーが再起動された場合に再コンパイルされます)。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-134">(Natively compiled stored procedures are recompiled if the database is taken offline and brought back online, or if there is a server restart.)</span></span>  
  
## <a name="guidelines-for-statistics-when-deploying-memory-optimized-tables"></a><span data-ttu-id="9e4ec-135">メモリ最適化テーブルを配置するときの統計のガイドライン</span><span class="sxs-lookup"><span data-stu-id="9e4ec-135">Guidelines for Statistics When Deploying Memory-Optimized Tables</span></span>  
 <span data-ttu-id="9e4ec-136">クエリ オプティマイザーでクエリ プランを作成するときに最新の統計が使用されるように、次の 5 つの手順を使用してメモリ最適化テーブルを配置します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-136">To ensure that the query optimizer has up-to-date statistics when creating query plans, deploy memory-optimized tables using these five steps:</span></span>  
  
1.  <span data-ttu-id="9e4ec-137">テーブルとインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-137">Create tables and indexes.</span></span> <span data-ttu-id="9e4ec-138">インデックスは、`CREATE TABLE` ステートメントでインラインで指定されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-138">Indexes are specified inline in the `CREATE TABLE` statements.</span></span>  
  
2.  <span data-ttu-id="9e4ec-139">テーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-139">Load data into the tables.</span></span>  
  
3.  <span data-ttu-id="9e4ec-140">テーブル上の統計を更新します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-140">Update statistics on the tables.</span></span>  
  
4.  <span data-ttu-id="9e4ec-141">テーブルにアクセスするストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-141">Create stored procedures that access the tables.</span></span>  
  
5.  <span data-ttu-id="9e4ec-142">ワークロードを実行します。これには、ネイティブ コンパイル ストアド プロシージャ、解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] ストアド プロシージャ、およびアドホック バッチが混在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-142">Run the workload, which can contain a mix of natively compiled and interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures, as well as ad hoc batches.</span></span>  
  
 <span data-ttu-id="9e4ec-143">データを読み込んで統計を更新してからネイティブ コンパイル ストアド プロシージャを作成することにより、オプティマイザーで統計をメモリ最適化テーブル用に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-143">Creating natively compiled stored procedures after you load the data and update the statistics ensures that the optimizer has statistics available for the memory-optimized tables.</span></span> <span data-ttu-id="9e4ec-144">これによって、プロシージャをコンパイルすると効率的なクエリ プランが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-144">This will ensure efficient query plans when the procedure is compiled.</span></span>  
  
## <a name="guidelines-for-maintaining-statistics-on-memory-optimized-tables"></a><span data-ttu-id="9e4ec-145">メモリ最適化テーブルでの統計の管理のガイドライン</span><span class="sxs-lookup"><span data-stu-id="9e4ec-145">Guidelines for Maintaining Statistics on Memory-Optimized Tables</span></span>  
 <span data-ttu-id="9e4ec-146">統計を最新に保つためには、メモリ最適化テーブルの統計を定期的に更新します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-146">To keep statistics up-to-date, regularly update the statistics on memory-optimized tables.</span></span>  
  
 <span data-ttu-id="9e4ec-147">データが頻繁に変更される場合は、統計を頻繁に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-147">If data changes frequently, you should update statistics frequently.</span></span> <span data-ttu-id="9e4ec-148">たとえば、バッチ更新の後にテーブルの統計を更新します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-148">For example, update table statistics after a batch update.</span></span> <span data-ttu-id="9e4ec-149">統計を更新した後、更新された統計の利点を得られるように、ネイティブ コンパイル ストアド プロシージャを削除して再作成します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-149">After you update statistics, drop and recreate natively compiled stored procedures so they can benefit from the updated statistics.</span></span>  
  
 <span data-ttu-id="9e4ec-150">.</span><span class="sxs-lookup"><span data-stu-id="9e4ec-150">.</span></span>  
  
 <span data-ttu-id="9e4ec-151">ピーク ワークロード中に統計を更新しないでください。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-151">Do not update statistics during peak workload.</span></span>  
  
 <span data-ttu-id="9e4ec-152">統計を更新するには:</span><span class="sxs-lookup"><span data-stu-id="9e4ec-152">To update statistics:</span></span>  
  
-   <span data-ttu-id="9e4ec-153">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)][統計の更新タスク](../maintenance-plans/update-statistics-task-maintenance-plan.md)を使用して[メンテナンスプランを作成](../maintenance-plans/create-a-maintenance-plan.md)するには、を使用します</span><span class="sxs-lookup"><span data-stu-id="9e4ec-153">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to [Create a Maintenance Plan](../maintenance-plans/create-a-maintenance-plan.md) with an [Update Statistic Task](../maintenance-plans/update-statistics-task-maintenance-plan.md)</span></span>  
  
-   <span data-ttu-id="9e4ec-154">または、後で説明する [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを使用して統計を更新します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-154">Or, update statistics through a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script, as discussed below.</span></span>  
  
 <span data-ttu-id="9e4ec-155">1つのメモリ最適化テーブル (*myschema.xml*) の統計を更新するには</span><span class="sxs-lookup"><span data-stu-id="9e4ec-155">To update the statistics for a single memory-optimized table (*myschema*.</span></span> <span data-ttu-id="9e4ec-156">*Mytable*)、次のスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-156">*Mytable*), run the following script:</span></span>  
  
```  
UPDATE STATISTICS myschema.Mytable WITH FULLSCAN, NORECOMPUTE  
```  
  
 <span data-ttu-id="9e4ec-157">現在のデータベース内のすべてのメモリ最適化テーブルの統計を更新するには、次のスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-157">To update statistics for all memory-optimized tables in the current database, run the following script:</span></span>  
  
```sql  
DECLARE @sql NVARCHAR(MAX) = N''  
  
SELECT @sql += N'  
   UPDATE STATISTICS ' + quotename(schema_name(schema_id)) + N'.' + quotename(name) + N' WITH FULLSCAN, NORECOMPUTE'  
FROM sys.tables WHERE is_memory_optimized=1  
  
EXEC sp_executesql @sql  
```  
  
 <span data-ttu-id="9e4ec-158">データベース内のすべてのテーブルの統計を更新するには、 [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-158">To update statistics for all tables in the database, run [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span>  
  
 <span data-ttu-id="9e4ec-159">次のサンプルでは、メモリ最適化テーブルの最終更新日を報告します。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-159">The following sample reports when the statistics on memory-optimized tables were last updated.</span></span> <span data-ttu-id="9e4ec-160">この情報は、統計を更新する必要があるかどうかを判断するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9e4ec-160">This information can help you decide if you need to update the statistics.</span></span>  
  
```sql  
select t.object_id, t.name, sp.last_updated as 'stats_last_updated'  
from sys.tables t join sys.stats s on t.object_id=s.object_id cross apply sys.dm_db_stats_properties(t.object_id, s.stats_id) sp  
where t.is_memory_optimized=1  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e4ec-161">参照</span><span class="sxs-lookup"><span data-stu-id="9e4ec-161">See Also</span></span>  
 [<span data-ttu-id="9e4ec-162">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="9e4ec-162">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
