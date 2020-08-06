---
title: クラスター化列ストアインデックスの使用 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5af6b91c-724f-45ac-aff1-7555014914f4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: afc7da4e28ef7f32ca4a2b4ea762e5a5af442471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632048"
---
# <a name="using-clustered-columnstore-indexes"></a><span data-ttu-id="8e10e-102">クラスター化列ストア インデックスの使用</span><span class="sxs-lookup"><span data-stu-id="8e10e-102">Using Clustered Columnstore Indexes</span></span>
  <span data-ttu-id="8e10e-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクラスター化 columnstore インデックスを使用するタスクです。</span><span class="sxs-lookup"><span data-stu-id="8e10e-103">Tasks for using clustered columnstore indexes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="8e10e-104">列ストアインデックスの概要については、「[列ストアインデックス](../relational-databases/indexes/columnstore-indexes-described.md)の概要」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e10e-104">For an overview of columnstore indexes, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>

 <span data-ttu-id="8e10e-105">クラスター化列ストアインデックスの詳細については、「[クラスター化列ストアインデックスの使用](../relational-databases/indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e10e-105">For information about clustered columnstore indexes, see [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).</span></span>

## <a name="contents"></a><span data-ttu-id="8e10e-106">内容</span><span class="sxs-lookup"><span data-stu-id="8e10e-106">Contents</span></span>

-   [<span data-ttu-id="8e10e-107">クラスター化列ストア インデックスを作成する</span><span class="sxs-lookup"><span data-stu-id="8e10e-107">Create a Clustered Columnstore Index</span></span>](#create)

-   [<span data-ttu-id="8e10e-108">クラスター化 Columnstore インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="8e10e-108">Drop a Clustered Columnstore Index</span></span>](#drop)

-   [<span data-ttu-id="8e10e-109">クラスター化 Columnstore インデックスへのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="8e10e-109">Load Data into a Clustered Columnstore Index</span></span>](#load)

-   [<span data-ttu-id="8e10e-110">クラスター化 Columnstore インデックス内のデータの変更</span><span class="sxs-lookup"><span data-stu-id="8e10e-110">Change Data in a Clustered Columnstore Index</span></span>](#change)

-   [<span data-ttu-id="8e10e-111">クラスター化列ストアインデックスを再構築する</span><span class="sxs-lookup"><span data-stu-id="8e10e-111">Rebuild a Clustered Columnstore Index</span></span>](#rebuild)

-   [<span data-ttu-id="8e10e-112">クラスター化列ストアインデックスの再編成</span><span class="sxs-lookup"><span data-stu-id="8e10e-112">Reorganize a Clustered Columnstore Index</span></span>](#reorganize)

##  <a name="create-a-clustered-columnstore-index"></a><a name="create"></a><span data-ttu-id="8e10e-113">クラスター化列ストアインデックスを作成する</span><span class="sxs-lookup"><span data-stu-id="8e10e-113">Create a Clustered Columnstore Index</span></span>
 <span data-ttu-id="8e10e-114">クラスター化列ストアインデックスを作成するには、まずヒープまたはクラスター化インデックスとして行ストアテーブルを作成し、次に[CREATE CLUSTERED 列ストアインデックス &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)ステートメントを使用して、テーブルをクラスター化列ストアインデックスに変換します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-114">To create a clustered columnstore index, first create a rowstore table as a heap or clustered index, and then use the [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) statement to convert the table to a clustered columnstore index.</span></span> <span data-ttu-id="8e10e-115">クラスター化 columnstore インデックスにクラスター化インデックスと同じ名前を付ける場合は、DROP_EXISTING オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-115">If you want the clustered columnstore index to have the same name as the clustered index, use the DROP_EXISTING option.</span></span>

 <span data-ttu-id="8e10e-116">この例では、テーブルをヒープとして作成してから、cci_Simple という名前のクラスター化 columnstore インデックスに変換します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-116">This example creates a table as a heap and then converts it to a clustered columnstore index named cci_Simple.</span></span> <span data-ttu-id="8e10e-117">こうすることで、テーブル全体のストレージが行ストアから列ストアに変更されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-117">This changes the storage for the entire table from rowstore to columnstore.</span></span>

```
CREATE TABLE T1(
    ProductKey [int] NOT NULL, 
    OrderDateKey [int] NOT NULL, 
    DueDateKey [int] NOT NULL, 
    ShipDateKey [int] NOT NULL);
GO
CREATE CLUSTERED COLUMNSTORE INDEX cci_T1 ON T1;
GO
```

 <span data-ttu-id="8e10e-118">詳細については、「 [CREATE CLUSTERED INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)」の「例」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e10e-118">For more examples, see the Examples section in [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>

##  <a name="drop-a-clustered-columnstore-index"></a><a name="drop"></a><span data-ttu-id="8e10e-119">クラスター化列ストアインデックスを削除する</span><span class="sxs-lookup"><span data-stu-id="8e10e-119">Drop a Clustered Columnstore Index</span></span>
 <span data-ttu-id="8e10e-120">[DROP INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/drop-index-transact-sql)ステートメントを使用して、クラスター化列ストアインデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-120">Use the [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql) statement to drop a clustered columnstore index.</span></span> <span data-ttu-id="8e10e-121">この操作は、インデックスを削除し、列ストア テーブルを行ストア ヒープに変換します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-121">This operation will drop the index and convert the columnstore table to a rowstore heap.</span></span>

##  <a name="load-data-into-a-clustered-columnstore-index"></a><a name="load"></a><span data-ttu-id="8e10e-122">クラスター化列ストアインデックスへのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="8e10e-122">Load Data into a Clustered Columnstore Index</span></span>
 <span data-ttu-id="8e10e-123">標準的な読み込み方法を使用して既存のクラスター化列ストア インデックスにデータを追加できます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-123">You can add data to an existing clustered columnstore index by using any of the standard loading methods.</span></span>  <span data-ttu-id="8e10e-124">たとえば、bcp 一括読み込みツール、Integration Services、挿入...[すべてのデータをクラスター化列ストアインデックスに読み込むことができる] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-124">For example, the bcp bulk loading tool, Integration Services, and INSERT ... SELECT can all load data into a clustered columnstore index.</span></span>

 <span data-ttu-id="8e10e-125">クラスター化 columnstore インデックスでは、columnstore の列セグメントの断片化を防ぐためにデルタストアを活用します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-125">Clustered columnstore indexes leverage the deltastore in order to prevent fragmentation of column segments in the columnstore.</span></span>

### <a name="loading-into-a-partitioned-table"></a><span data-ttu-id="8e10e-126">パーティションテーブルへの読み込み</span><span class="sxs-lookup"><span data-stu-id="8e10e-126">Loading into a partitioned table</span></span>
 <span data-ttu-id="8e10e-127">パーティション分割されたデータの場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] はまずパーティションに各行を割り当て、次にパーティション内のデータの columnstore 処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-127">For partitioned data, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] first assigns each row to a partition, and then performs columnstore operations on the data within the partition.</span></span> <span data-ttu-id="8e10e-128">各パーティションには、独自の行グループと少なくとも 1 つのデルタストアがあります。</span><span class="sxs-lookup"><span data-stu-id="8e10e-128">Each partition has its own rowgroups and at least one deltastore.</span></span>

### <a name="deltastore-loading-scenarios"></a><span data-ttu-id="8e10e-129">デルタストアの読み込みのシナリオ</span><span class="sxs-lookup"><span data-stu-id="8e10e-129">Deltastore loading scenarios</span></span>
 <span data-ttu-id="8e10e-130">デルタストアの行は、行グループに許容されている最大行数になるまで蓄積されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-130">Rows accumulate in the deltastore until the number of rows is the maximum number of rows allowed for a rowgroup.</span></span> <span data-ttu-id="8e10e-131">デルタストアに行グループあたりの最大行数が含まれている場合は、行グループを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] "CLOSED" としてマークします。</span><span class="sxs-lookup"><span data-stu-id="8e10e-131">When the deltastore contains the maximum number of rows per rowgroup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the rowgroup as "CLOSED".</span></span> <span data-ttu-id="8e10e-132">"組ムーバー" と呼ばれるバックグラウンドプロセスは、閉じられた行グループを検索し、列ストアに移動します。ここでは、行グループが列セグメントに圧縮され、列セグメントが列ストアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-132">A background process, called the "tuple-mover", finds the CLOSED rowgroup and moves into the columnstore, where the rowgroup is compressed into column segments and the column segments are stored in the columnstore.</span></span>

 <span data-ttu-id="8e10e-133">各クラスター化 columnstore インデックスに対して複数のデルタストアが許容されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-133">For each clustered columnstore index there can be multiple deltastores.</span></span>

-   <span data-ttu-id="8e10e-134">デルタストアがロックされている場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は別のデルタストアのロックを獲得しようとします。</span><span class="sxs-lookup"><span data-stu-id="8e10e-134">If a deltastore is locked, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will try to obtain a lock on a different deltastore.</span></span> <span data-ttu-id="8e10e-135">使用できるデルタストアがない場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は新しいデルタストアを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-135">If there are no deltastores available, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will create a new deltastore.</span></span>

-   <span data-ttu-id="8e10e-136">パーティション テーブルでは、各パーティションに 1 つ以上のデルタストアが許容されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-136">For a partitioned table, there can be one or more deltastores for each partition.</span></span>

 <span data-ttu-id="8e10e-137">クラスター化 columnstore インデックスのみについて、次のシナリオは、読み込まれた行が columnstore に直接移動するときと、デルタストアに移動するときについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-137">For clustered columnstore indexes only, the following scenarios describe when loaded rows go directly to the columnstore or when they go to the deltastore.</span></span>

 <span data-ttu-id="8e10e-138">この例では、行グループはそれぞれ 102,400 ～ 1,048,576 個の行を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-138">In the example, each rowgroup can have 102,400-1,048,576 rows per rowgroup.</span></span>

|<span data-ttu-id="8e10e-139">一括読み込みを行う行</span><span class="sxs-lookup"><span data-stu-id="8e10e-139">Rows to Bulk Load</span></span>|<span data-ttu-id="8e10e-140">列ストアに追加される行</span><span class="sxs-lookup"><span data-stu-id="8e10e-140">Rows Added to the Columnstore</span></span>|<span data-ttu-id="8e10e-141">デルタストアに追加される行</span><span class="sxs-lookup"><span data-stu-id="8e10e-141">Rows Added to the Deltastore</span></span>|
|-----------------------|-----------------------------------|----------------------------------|
|<span data-ttu-id="8e10e-142">102,000</span><span class="sxs-lookup"><span data-stu-id="8e10e-142">102,000</span></span>|<span data-ttu-id="8e10e-143">0</span><span class="sxs-lookup"><span data-stu-id="8e10e-143">0</span></span>|<span data-ttu-id="8e10e-144">102,000</span><span class="sxs-lookup"><span data-stu-id="8e10e-144">102,000</span></span>|
|<span data-ttu-id="8e10e-145">145,000</span><span class="sxs-lookup"><span data-stu-id="8e10e-145">145,000</span></span>|<span data-ttu-id="8e10e-146">145,000</span><span class="sxs-lookup"><span data-stu-id="8e10e-146">145,000</span></span><br /><br /> <span data-ttu-id="8e10e-147">行グループのサイズ:145,000</span><span class="sxs-lookup"><span data-stu-id="8e10e-147">Rowgroup size: 145,000</span></span>|<span data-ttu-id="8e10e-148">0</span><span class="sxs-lookup"><span data-stu-id="8e10e-148">0</span></span>|
|<span data-ttu-id="8e10e-149">1,048,577</span><span class="sxs-lookup"><span data-stu-id="8e10e-149">1,048,577</span></span>|<span data-ttu-id="8e10e-150">1,048,576</span><span class="sxs-lookup"><span data-stu-id="8e10e-150">1,048,576</span></span><br /><br /> <span data-ttu-id="8e10e-151">行グループのサイズ:1,048,576</span><span class="sxs-lookup"><span data-stu-id="8e10e-151">Rowgroup size: 1,048,576.</span></span>|<span data-ttu-id="8e10e-152">1</span><span class="sxs-lookup"><span data-stu-id="8e10e-152">1</span></span>|
|<span data-ttu-id="8e10e-153">2,252,152</span><span class="sxs-lookup"><span data-stu-id="8e10e-153">2,252,152</span></span>|<span data-ttu-id="8e10e-154">2,252,152</span><span class="sxs-lookup"><span data-stu-id="8e10e-154">2,252,152</span></span><br /><br /> <span data-ttu-id="8e10e-155">行グループのサイズ:1,048,576、1,048,576、155,000</span><span class="sxs-lookup"><span data-stu-id="8e10e-155">Rowgroup sizes: 1,048,576, 1,048,576, 155,000.</span></span>|<span data-ttu-id="8e10e-156">0</span><span class="sxs-lookup"><span data-stu-id="8e10e-156">0</span></span>|

 <span data-ttu-id="8e10e-157">次の例は、1,048,577 個の行をパーティションに読み込んだ結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e10e-157">The following example shows the results of loading 1,048,577 rows into a partition.</span></span> <span data-ttu-id="8e10e-158">この結果では、列ストアに 1 つの圧縮された行グループ (圧縮された列セグメントとして)、およびデルタストアに 1 行があります。</span><span class="sxs-lookup"><span data-stu-id="8e10e-158">The results show that one COMPRESSED rowgroup in the columnstore (as compressed column segments), and 1 row in the deltastore.</span></span>

```sql
SELECT * FROM sys.column_store_row_groups;
```

 <span data-ttu-id="8e10e-159">![バッチ読み込みの行グループとデルタストア](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "バッチ読み込みの行グループとデルタストア")</span><span class="sxs-lookup"><span data-stu-id="8e10e-159">![Rowgroup and deltastore for a batch load](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "Rowgroup and deltastore for a batch load")</span></span>



##  <a name="change-data-in-a-clustered-columnstore-index"></a><a name="change"></a><span data-ttu-id="8e10e-160">クラスター化列ストアインデックスのデータの変更</span><span class="sxs-lookup"><span data-stu-id="8e10e-160">Change Data in a Clustered Columnstore Index</span></span>
 <span data-ttu-id="8e10e-161">クラスター化 columnstore インデックスでは挿入、更新、および DML 削除操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-161">Clustered columnstore indexes support insert, update, and delete DML operations.</span></span>

 <span data-ttu-id="8e10e-162">[Insert &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql)を使用して行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-162">Use [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) to insert a row.</span></span> <span data-ttu-id="8e10e-163">行はデルタストアに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-163">The row will be added to the deltastore.</span></span>

 <span data-ttu-id="8e10e-164">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) を使用して行を削除します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-164">Use [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) to delete a row.</span></span>

-   <span data-ttu-id="8e10e-165">行が列ストアにある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は行を論理的に削除されたとしてマークしますが、インデックスが再構築されるまで行の物理ストレージを再確保することはありません。</span><span class="sxs-lookup"><span data-stu-id="8e10e-165">If the row is in the columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the row as logically deleted but does not reclaim the physical storage for the row until the index is rebuilt.</span></span>

-   <span data-ttu-id="8e10e-166">行がデルタストアにある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は論理的および物理的に行を削除します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-166">If the row is in the deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logically and physically deletes the row.</span></span>

 <span data-ttu-id="8e10e-167">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) を使用して行を更新します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-167">Use [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) to update a row.</span></span>

-   <span data-ttu-id="8e10e-168">行が列ストアにある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は行を論理的に削除されたとしてマークし、更新された行をデルタストアに挿入します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-168">If the row is in the columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the row as logically deleted, and then inserts the updated row into the deltastore.</span></span>

-   <span data-ttu-id="8e10e-169">行がデルタストアにある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、デルタストアの行を更新します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-169">If the row is in the deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] updates the row in the deltastore.</span></span>

##  <a name="rebuild-a-clustered-columnstore-index"></a><a name="rebuild"></a><span data-ttu-id="8e10e-170">クラスター化列ストアインデックスを再構築する</span><span class="sxs-lookup"><span data-stu-id="8e10e-170">Rebuild a Clustered Columnstore Index</span></span>
 <span data-ttu-id="8e10e-171">[CREATE CLUSTERED 列ストアインデックス &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)または[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)を使用して、既存のクラスター化列ストアインデックスの完全な再構築を実行します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-171">Use [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) to perform a full rebuild of an existing clustered columnstore index.</span></span> <span data-ttu-id="8e10e-172">また、ALTER INDEX...再構築して特定のパーティションを再構築します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-172">Additionally, you can use ALTER INDEX ... REBUILD to rebuild a specific partition.</span></span>

### <a name="rebuild-process"></a><span data-ttu-id="8e10e-173">再構築プロセス</span><span class="sxs-lookup"><span data-stu-id="8e10e-173">Rebuild Process</span></span>
 <span data-ttu-id="8e10e-174">クラスター化列ストア インデックスを再構築する際、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は以下のように動作します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-174">To rebuild a clustered columnstore index, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>

-   <span data-ttu-id="8e10e-175">再構築が行われている間、テーブルまたはパーティションを排他的にロックします。</span><span class="sxs-lookup"><span data-stu-id="8e10e-175">Acquires an exclusive lock on the table or partition while the rebuild occurs.</span></span>  <span data-ttu-id="8e10e-176">再構築の間、データは "オフライン" になって使用できません。</span><span class="sxs-lookup"><span data-stu-id="8e10e-176">The data is "offline" and unavailable during the rebuild.</span></span>

-   <span data-ttu-id="8e10e-177">テーブルから論理的に削除された行を物理的に削除することで、列ストアをデフラグします。削除されたバイトは物理メディアで再利用されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-177">Defragments the columnstore by physically deleting rows that have been logically deleted from the table; the deleted bytes are reclaimed on the physical media.</span></span>

-   <span data-ttu-id="8e10e-178">インデックスを再構築する前に、デルタストアの行ストア データを columnstore のデータとマージします。</span><span class="sxs-lookup"><span data-stu-id="8e10e-178">Merges the rowstore data in the deltastore with the data in the columnstore before it rebuilds the index.</span></span> <span data-ttu-id="8e10e-179">再構築が終了すると、すべてのデータが columnstore 形式で格納され、デルタストアが空になります。</span><span class="sxs-lookup"><span data-stu-id="8e10e-179">When the rebuild is finished, all data is stored in columnstore format, and the deltastore is empty.</span></span>

-   <span data-ttu-id="8e10e-180">すべてのデータを列ストアに再圧縮します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-180">Re-compresses all data into the columnstore.</span></span> <span data-ttu-id="8e10e-181">再構築が行われている間、列ストア インデックスのコピーが 2 つ存在します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-181">Two copies of the columnstore index exist while the rebuild is taking place.</span></span> <span data-ttu-id="8e10e-182">再構築が完了したら、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] により、元の列ストア インデックスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-182">When the rebuild is finished, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] deletes the original columnstore index.</span></span>

### <a name="recommendations-for-rebuilding-a-clustered-columnstore-index"></a><span data-ttu-id="8e10e-183">クラスター化 Columnstore インデックスの再構築の推奨設定</span><span class="sxs-lookup"><span data-stu-id="8e10e-183">Recommendations for Rebuilding a Clustered Columnstore Index</span></span>
 <span data-ttu-id="8e10e-184">クラスター化 columnstore インデックスを再構築すると、断片化の解消およびすべての行を columnstore に移動する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="8e10e-184">Rebuilding a clustered columnstore index is useful for removing fragmentation, and for moving all rows into the columnstore.</span></span> <span data-ttu-id="8e10e-185">次の推奨事項が用意されています。</span><span class="sxs-lookup"><span data-stu-id="8e10e-185">We have the following recommendations:</span></span>

-   <span data-ttu-id="8e10e-186">テーブル全体ではなくパーティションを再構築します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-186">Rebuild a partition instead of the entire table.</span></span>

    1.  <span data-ttu-id="8e10e-187">インデックスが大きいとテーブル全体の再構築には時間がかかり、再構築中にインデックスの追加コピーを格納するために十分なディスク領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="8e10e-187">Rebuilding the entire table takes a long time if the index is large, and it requires enough disk space to store an additional copy of the index during the rebuild.</span></span> <span data-ttu-id="8e10e-188">通常は、最近使用されたパーティションを再構築するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-188">Usually it is only necessary to rebuild the most recently used partition.</span></span>

    2.  <span data-ttu-id="8e10e-189">パーティション テーブルでは、columnstore インデックス全体を再構築する必要はありません。断片化は最近変更されたパーティションのみで起きる可能性が高いためです。</span><span class="sxs-lookup"><span data-stu-id="8e10e-189">For partitioned tables, you do not need to rebuild the entire columnstore index because fragmentation is likely to occur in only the partitions that have been modified recently.</span></span> <span data-ttu-id="8e10e-190">ファクト テーブルや大きなディメンション テーブルは通常、テーブルのチャンク上でバックアップおよび管理を行うためにパーティション分割されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-190">Fact tables and large dimension tables are usually partitioned in order to perform backup and management operations on chunks of the table.</span></span>

-   <span data-ttu-id="8e10e-191">負荷の高い DML 操作後にパーティションを再構築します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-191">Rebuild a partition after heavy DML operations.</span></span>

     <span data-ttu-id="8e10e-192">パーティションを再構築すると、パーティションの断片化を解消し、ディスク ストレージが減少します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-192">Rebuilding a partition will defragment the partition and reduce disk storage.</span></span> <span data-ttu-id="8e10e-193">再構築すると、削除のマークが付けられた columnstore からすべての行が削除され、すべての行がデルタストアから columnstore に移動されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-193">Rebuilding will delete all rows from the columnstore that are marked for deletion, and it will move all rows from the deltastore into the columnstore.</span></span>

-   <span data-ttu-id="8e10e-194">データを読み込んだ後に、パーティションを再構築します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-194">Rebuild a partition after loading data.</span></span>

     <span data-ttu-id="8e10e-195">これにより、すべてデータが columnstore に格納されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-195">This ensures all data is stored in the columnstore.</span></span> <span data-ttu-id="8e10e-196">複数の負荷が同時に発生した場合は、各パーティションは複数のデルタストアを持つ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e10e-196">If multiple loads occur at the same time, each partition could end up having multiple deltastores.</span></span> <span data-ttu-id="8e10e-197">再構築すると、すべてのデルタストア行が columnstore に移動されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-197">Rebuilding will move all deltastore rows into the columnstore.</span></span>

##  <a name="reorganize-a-clustered-columnstore-index"></a><a name="reorganize"></a><span data-ttu-id="8e10e-198">クラスター化列ストアインデックスの再編成</span><span class="sxs-lookup"><span data-stu-id="8e10e-198">Reorganize a Clustered Columnstore Index</span></span>
 <span data-ttu-id="8e10e-199">クラスター化 columnstore インデックスを再構成すると、すべての CLOSED 行グループが columnstore に移動されます。</span><span class="sxs-lookup"><span data-stu-id="8e10e-199">Reorganizing a clustered columnstore index moves all CLOSED rowgroups into the columnstore.</span></span> <span data-ttu-id="8e10e-200">再編成を実行するには、 [ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)を再構成オプションと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-200">To perform a reorganize, use [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)with the REORGANIZE option.</span></span>

 <span data-ttu-id="8e10e-201">再構成は、CLOSED 行グループを columnstore に移動するためには必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8e10e-201">Reorganizing is not required in order to move CLOSED rowgroups into the columnstore.</span></span> <span data-ttu-id="8e10e-202">組ムーバープロセスは、最終的にすべての閉じた行グループを検索して移動します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-202">The tuple-mover process will eventually find all CLOSED rowgroups and move them.</span></span> <span data-ttu-id="8e10e-203">ただし、組ムーバーはシングルスレッドであり、ワークロードに対して十分な速度で行グループを移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="8e10e-203">However, the tuple-mover is single-threaded and might not move rowgroups fast enough for your workload.</span></span>

### <a name="recommendations-for-reorganizing"></a><span data-ttu-id="8e10e-204">再構成に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="8e10e-204">Recommendations for Reorganizing</span></span>
 <span data-ttu-id="8e10e-205">クラスター化列ストア インデックスを再構成するとき:</span><span class="sxs-lookup"><span data-stu-id="8e10e-205">When to reorganize a clustered columnstore index:</span></span>

-   <span data-ttu-id="8e10e-206">クエリのパフォーマンスの利点をできるだけ早く得るために、1 つ以上のデータが読み込まれた後にクラスター化列ストア インデックスを再編成します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-206">Reorganize a clustered columnstore index after one or more data loads to achieve query performance benefits as quickly as possible.</span></span> <span data-ttu-id="8e10e-207">再構成ではデータを圧縮するために最初に追加の CPU リソースが必要とされ、システムの全体的なパフォーマンスが遅くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8e10e-207">Reorganizing will initially require additional CPU resources to compress the data, which could slow overall system performance.</span></span> <span data-ttu-id="8e10e-208">しかし、データが圧縮されるとすぐにクエリ パフォーマンスが改善します。</span><span class="sxs-lookup"><span data-stu-id="8e10e-208">However, as soon as the data is compressed, query performance can improve.</span></span>


