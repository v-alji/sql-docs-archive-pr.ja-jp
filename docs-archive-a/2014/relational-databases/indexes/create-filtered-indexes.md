---
title: フィルター選択されたインデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- filtered indexes [SQL Server], about filtered indexes
- designing indexes [SQL Server], filtered
- filtered indexes [SQL Server]
- nonclustered indexes [SQL Server], filtered
- indexes [SQL Server], filtered
ms.assetid: 25e1fcc5-45d7-4c53-8c79-5493dfaa1c74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77cf641ca84181496f26a995244029d0525ade63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740962"
---
# <a name="create-filtered-indexes"></a><span data-ttu-id="818a3-102">フィルター選択されたインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="818a3-102">Create Filtered Indexes</span></span>
  <span data-ttu-id="818a3-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、フィルター選択されたインデックスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="818a3-103">This topic describes how to create a filtered index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="818a3-104">フィルター選択されたインデックスは、最適化された非クラスター化インデックスであり、適切に定義されたデータのサブセットから選択するクエリに対応する際に特に適しています。</span><span class="sxs-lookup"><span data-stu-id="818a3-104">A filtered index is an optimized nonclustered index especially suited to cover queries that select from a well-defined subset of data.</span></span> <span data-ttu-id="818a3-105">フィルター選択されたインデックスは、フィルター述語を使用して、テーブル内の一部の行にインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="818a3-105">It uses a filter predicate to index a portion of rows in the table.</span></span> <span data-ttu-id="818a3-106">フィルター選択されたインデックスを適切にデザインすると、クエリのパフォーマンスが向上するだけでなく、テーブル全体のインデックスと比較してインデックスのメンテナンス コストおよびストレージ コストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="818a3-106">A well-designed filtered index can improve query performance as well as reduce index maintenance and storage costs compared with full-table indexes.</span></span>  
  
 <span data-ttu-id="818a3-107">フィルター選択されたインデックスは、テーブル全体のインデックスよりも次の点で優れています。</span><span class="sxs-lookup"><span data-stu-id="818a3-107">Filtered indexes can provide the following advantages over full-table indexes:</span></span>  
  
-   <span data-ttu-id="818a3-108">**クエリのパフォーマンスとプランの品質の向上**</span><span class="sxs-lookup"><span data-stu-id="818a3-108">**Improved query performance and plan quality**</span></span>  
  
     <span data-ttu-id="818a3-109">フィルター選択されたインデックスを適切にデザインすると、クエリのパフォーマンスと実行プランの品質が向上します。これは、このインデックスが、テーブル全体の非クラスター化インデックスよりも小さく、フィルター選択された統計情報を含むためです。</span><span class="sxs-lookup"><span data-stu-id="818a3-109">A well-designed filtered index improves query performance and execution plan quality because it is smaller than a full-table nonclustered index and has filtered statistics.</span></span> <span data-ttu-id="818a3-110">フィルター選択された統計情報は、フィルター選択されたインデックスの行のみを対象としているため、テーブル全体の統計情報よりも正確です。</span><span class="sxs-lookup"><span data-stu-id="818a3-110">The filtered statistics are more accurate than full-table statistics because they cover only the rows in the filtered index.</span></span>  
  
-   <span data-ttu-id="818a3-111">**インデックスのメンテナンス コストの削減**</span><span class="sxs-lookup"><span data-stu-id="818a3-111">**Reduced index maintenance costs**</span></span>  
  
     <span data-ttu-id="818a3-112">インデックスのメンテナンスが行われるのは、データ操作言語 (DML) ステートメントがインデックス内のデータに影響を与える場合のみです。</span><span class="sxs-lookup"><span data-stu-id="818a3-112">An index is maintained only when data manipulation language (DML) statements affect the data in the index.</span></span> <span data-ttu-id="818a3-113">フィルター選択されたインデックスにより、インデックスのメンテナンス コストは、テーブル全体の非クラスター化インデックスと比較して削減されます。これは、フィルター選択されたインデックスは小さく、インデックス内のデータが変更された場合にのみメンテナンスされるためです。</span><span class="sxs-lookup"><span data-stu-id="818a3-113">A filtered index reduces index maintenance costs compared with a full-table nonclustered index because it is smaller and is only maintained when the data in the index is changed.</span></span> <span data-ttu-id="818a3-114">特に、含まれるデータの変更頻度が引く場合は、多数のフィルター選択されたインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="818a3-114">It is possible to have a large number of filtered indexes, especially when they contain data that is changed infrequently.</span></span> <span data-ttu-id="818a3-115">同様に、フィルター選択されたインデックスに頻繁に変更されるデータのみが含まれている場合は、インデックスのサイズを小さくすると、統計情報の更新コストが削減されます。</span><span class="sxs-lookup"><span data-stu-id="818a3-115">Similarly, if a filtered index contains only the frequently modified data, the smaller size of the index reduces the cost of updating the statistics.</span></span>  
  
-   <span data-ttu-id="818a3-116">**インデックスのストレージ コストの削減**</span><span class="sxs-lookup"><span data-stu-id="818a3-116">**Reduced index storage costs**</span></span>  
  
     <span data-ttu-id="818a3-117">テーブル全体のインデックスが不要な場合は、フィルター選択されたインデックスを作成すると、非クラスター化インデックスのディスク ストレージを削減できます。</span><span class="sxs-lookup"><span data-stu-id="818a3-117">Creating a filtered index can reduce disk storage for nonclustered indexes when a full-table index is not necessary.</span></span> <span data-ttu-id="818a3-118">ストレージ要件をあまり増やすことなく、テーブル全体の非クラスター化インデックスを複数のフィルター選択されたインデックスに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="818a3-118">You can replace a full-table nonclustered index with multiple filtered indexes without significantly increasing the storage requirements.</span></span>  
  
 <span data-ttu-id="818a3-119">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="818a3-119">**In This Topic**</span></span>  
  
-   <span data-ttu-id="818a3-120">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="818a3-120">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="818a3-121">デザインに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="818a3-121">Design Considerations</span></span>](#Design)  
  
     [<span data-ttu-id="818a3-122">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="818a3-122">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="818a3-123">Security</span><span class="sxs-lookup"><span data-stu-id="818a3-123">Security</span></span>](#Security)  
  
-   <span data-ttu-id="818a3-124">**以下を使用してフィルター選択されたインデックスを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="818a3-124">**To create a filtered index, using:**</span></span>  
  
     [<span data-ttu-id="818a3-125">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="818a3-125">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="818a3-126">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="818a3-126">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="818a3-127">はじめに</span><span class="sxs-lookup"><span data-stu-id="818a3-127">Before You Begin</span></span>  
  
###  <a name="design-considerations"></a><a name="Design"></a> <span data-ttu-id="818a3-128">デザインに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="818a3-128">Design Considerations</span></span>  
  
-   <span data-ttu-id="818a3-129">クエリに関連する少数の値だけが列に含まれている場合、値のサブセットにフィルター選択されたインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="818a3-129">When a column only has a small number of relevant values for queries, you can create a filtered index on the subset of values.</span></span> <span data-ttu-id="818a3-130">たとえば、列の値がほとんど NULL の場合に、クエリで常に NULL 以外の値を選択するときは、NULL 以外のデータ行にフィルター選択されたインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="818a3-130">For example, when the values in a column are mostly NULL and the query selects only from the non-NULL values, you can create a filtered index for the non-NULL data rows.</span></span> <span data-ttu-id="818a3-131">作成したインデックスは、同じキー列に定義されているテーブル全体の非クラスター化インデックスよりも小さく、メンテナンス コストが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="818a3-131">The resulting index will be smaller and cost less to maintain than a full-table nonclustered index defined on the same key columns.</span></span>  
  
-   <span data-ttu-id="818a3-132">テーブルに異種データの行が含まれている場合、1 つ以上のカテゴリのデータに対してフィルター選択されたインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="818a3-132">When a table has heterogeneous data rows, you can create a filtered index for one or more categories of data.</span></span> <span data-ttu-id="818a3-133">これにより、クエリのフォーカスをテーブルの特定の領域に狭めて、これらのデータに対するクエリのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="818a3-133">This can improve the performance of queries on these data rows by narrowing the focus of a query to a specific area of the table.</span></span> <span data-ttu-id="818a3-134">繰り返しになりますが、作成したインデックスは、テーブル全体の非クラスター化インデックスよりも小さく、メンテナンス コストが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="818a3-134">Again, the resulting index will be smaller and cost less to maintain than a full-table nonclustered index.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="818a3-135">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="818a3-135">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="818a3-136">フィルター選択されたインデックスをビューに作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="818a3-136">You cannot create a filtered index on a view.</span></span> <span data-ttu-id="818a3-137">ただし、クエリ オプティマイザーにとって、ビューで参照されているテーブルに定義されたフィルター選択されたインデックスは役立ちます。</span><span class="sxs-lookup"><span data-stu-id="818a3-137">However, the query optimizer can benefit from a filtered index defined on a table that is referenced in a view.</span></span> <span data-ttu-id="818a3-138">クエリ オプティマイザーでは、クエリ結果が正しくなる場合、ビューから選択するクエリに対してフィルター選択されたインデックスが検討されます。</span><span class="sxs-lookup"><span data-stu-id="818a3-138">The query optimizer considers a filtered index for a query that selects from a view if the query results will be correct.</span></span>  
  
-   <span data-ttu-id="818a3-139">フィルター選択されたインデックスは、インデックス付きビューよりも次の点で優れています。</span><span class="sxs-lookup"><span data-stu-id="818a3-139">Filtered indexes have the following advantages over indexed views:</span></span>  
  
    -   <span data-ttu-id="818a3-140">インデックスのメンテナンス コストの削減。</span><span class="sxs-lookup"><span data-stu-id="818a3-140">Reduced index maintenance costs.</span></span> <span data-ttu-id="818a3-141">たとえば、インデックス付きビューを更新する場合よりもフィルター選択されたインデックスを更新する場合の方が、クエリ プロセッサで使用する CPU リソースが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="818a3-141">For example, the query processor uses fewer CPU resources to update a filtered index than an indexed view.</span></span>  
  
    -   <span data-ttu-id="818a3-142">プランの品質の向上。</span><span class="sxs-lookup"><span data-stu-id="818a3-142">Improved plan quality.</span></span> <span data-ttu-id="818a3-143">たとえば、クエリのコンパイル時、同等のインデックス付きビューよりも多くの状況でフィルター選択されたインデックスを使用することがクエリ オプティマイザーで検討されます。</span><span class="sxs-lookup"><span data-stu-id="818a3-143">For example, during query compilation, the query optimizer considers using a filtered index in more situations than the equivalent indexed view.</span></span>  
  
    -   <span data-ttu-id="818a3-144">オンラインでのインデックス再構築。</span><span class="sxs-lookup"><span data-stu-id="818a3-144">Online index rebuilds.</span></span> <span data-ttu-id="818a3-145">フィルター選択されたインデックスは、クエリで使用可能なときに再構築できます。</span><span class="sxs-lookup"><span data-stu-id="818a3-145">You can rebuild filtered indexes while they are available for queries.</span></span> <span data-ttu-id="818a3-146">オンラインでのインデックス再構築は、インデックス付きビューではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="818a3-146">Online index rebuilds are not supported for indexed views.</span></span> <span data-ttu-id="818a3-147">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」の「REBUILD オプション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a3-147">For more information, see the REBUILD option for [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
    -   <span data-ttu-id="818a3-148">一意ではないインデックス。</span><span class="sxs-lookup"><span data-stu-id="818a3-148">Non-unique indexes.</span></span> <span data-ttu-id="818a3-149">フィルター選択されたインデックスは一意ではないインデックスにすることができますが、インデックス付きビューは一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="818a3-149">Filtered indexes can be non-unique, whereas indexed views must be unique.</span></span>  
  
-   <span data-ttu-id="818a3-150">フィルター選択されたインデックスは 1 つのテーブルで定義され、単純な比較演算子のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="818a3-150">Filtered indexes are defined on one table and only support simple comparison operators.</span></span> <span data-ttu-id="818a3-151">複数のテーブルを参照するフィルター式や複雑なロジックを含むフィルター式が必要な場合は、ビューを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="818a3-151">If you need a filter expression that references multiple tables or has complex logic, you should create a view.</span></span>  
  
-   <span data-ttu-id="818a3-152">フィルター選択されたインデックスの式がクエリ述語と同じであり、フィルター選択されたインデックスの式の列がクエリ結果と共に返されない場合、その式の列を、フィルター選択されたインデックスの定義でキー列または付加列にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="818a3-152">A column in the filtered index expression does not need to be a key or included column in the filtered index definition if the filtered index expression is equivalent to the query predicate and the query does not return the column in the filtered index expression with the query results.</span></span>  
  
-   <span data-ttu-id="818a3-153">フィルター選択されたインデックスの式と異なるクエリ述語で比較に列が使用される場合は、フィルター選択されたインデックスの式の列を、フィルター選択されたインデックスの定義でキー列または付加列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="818a3-153">A column in the filtered index expression should be a key or included column in the filtered index definition if the query predicate uses the column in a comparison that is not equivalent to the filtered index expression.</span></span>  
  
-   <span data-ttu-id="818a3-154">フィルター選択されたインデックスの式の列がクエリ結果セットに含まれる場合、その列をフィルター選択されたインデックスの定義でキー列または付加列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="818a3-154">A column in the filtered index expression should be a key or included column in the filtered index definition if the column is in the query result set.</span></span>  
  
-   <span data-ttu-id="818a3-155">テーブルのクラスター化インデックス キーは、フィルター選択されたインデックスの定義でキー列または付加列にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="818a3-155">The clustered index key of the table does not need to be a key or included column in the filtered index definition.</span></span> <span data-ttu-id="818a3-156">クラスター化インデックス キーは、フィルター選択されたインデックスなど、すべての非クラスター化インデックスに自動的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="818a3-156">The clustered index key is automatically included in all nonclustered indexes, including filtered indexes.</span></span>  
  
-   <span data-ttu-id="818a3-157">フィルター選択されたインデックスでは、その式に指定された比較演算子によって暗黙的または明示的なデータ変換が行われる場合、変換が比較演算子の左辺で行われると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="818a3-157">If the comparison operator specified in the filtered index expression of the filtered index results in an implicit or explicit data conversion, an error will occur if the conversion occurs on the left side of a comparison operator.</span></span> <span data-ttu-id="818a3-158">解決方法としては、比較演算子の右辺にデータ変換演算子 (CAST または CONVERT) を含む、フィルター選択されたインデックスの式を記述します。</span><span class="sxs-lookup"><span data-stu-id="818a3-158">A solution is to write the filtered index expression with the data conversion operator (CAST or CONVERT) on the right side of the comparison operator.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="818a3-159">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="818a3-159">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="818a3-160">Permissions</span><span class="sxs-lookup"><span data-stu-id="818a3-160">Permissions</span></span>  
 <span data-ttu-id="818a3-161">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="818a3-161">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="818a3-162">実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="818a3-162">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span> <span data-ttu-id="818a3-163">フィルター選択されたインデックスの式を変更するには、CREATE INDEX WITH DROP_EXISTING を使用します。</span><span class="sxs-lookup"><span data-stu-id="818a3-163">To modify the filtered index expression, use CREATE INDEX WITH DROP_EXISTING.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="818a3-164">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="818a3-164">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-filtered-index"></a><span data-ttu-id="818a3-165">フィルター選択されたインデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="818a3-165">To create a filtered index</span></span>  
  
1.  <span data-ttu-id="818a3-166">オブジェクト エクスプローラーで、フィルター選択されたインデックスを作成するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="818a3-166">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to create a filtered index.</span></span>  
  
2.  <span data-ttu-id="818a3-167">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="818a3-167">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="818a3-168">プラス記号をクリックして、フィルター選択されたインデックスを作成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="818a3-168">Click the plus sign to expand the table on which you want to create a filtered index.</span></span>  
  
4.  <span data-ttu-id="818a3-169">**[インデックス]** フォルダーを右クリックし、 **[新しいインデックス]** をポイントし、 **[非クラスター化インデックス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="818a3-169">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="818a3-170">**[新しいインデックス]** ダイアログ ボックスの **[全般]** ページで、 **[インデックス名]** ボックスに新しいインデックスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="818a3-170">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="818a3-171">**[インデックス キー列]** で、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="818a3-171">Under **Index key columns**, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="818a3-172">[Table_name**から列を選択**_table_name_ ] ダイアログボックスで、一意のインデックスに追加するテーブル列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="818a3-172">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the unique index.</span></span>  
  
8.  <span data-ttu-id="818a3-173">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="818a3-173">Click **OK**.</span></span>  
  
9. <span data-ttu-id="818a3-174">**[フィルター]** ページで、 **[フィルター式]** に、フィルター選択されたインデックスの作成に使用する SQL 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="818a3-174">On the **Filter** page, under **Filter Expression**, enter SQL expression that you'll use to create the filtered index.</span></span>  
  
10. <span data-ttu-id="818a3-175">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="818a3-175">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="818a3-176">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="818a3-176">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-filtered-index"></a><span data-ttu-id="818a3-177">フィルター選択されたインデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="818a3-177">To create a filtered index</span></span>  
  
1.  <span data-ttu-id="818a3-178">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="818a3-178">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="818a3-179">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="818a3-179">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="818a3-180">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="818a3-180">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Looks for an existing filtered index named "FIBillOfMaterialsWithEndDate"  
    -- and deletes it from the table Production.BillOfMaterials if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
        WHERE name = N'FIBillOfMaterialsWithEndDate'  
        AND object_id = OBJECT_ID (N'Production.BillOfMaterials'))  
    DROP INDEX FIBillOfMaterialsWithEndDate  
        ON Production.BillOfMaterials  
    GO  
    -- Creates a filtered index "FIBillOfMaterialsWithEndDate"  
    -- on the table Production.BillOfMaterials   
    -- using the columms ComponentID and StartDate.  
  
    CREATE NONCLUSTERED INDEX FIBillOfMaterialsWithEndDate  
        ON Production.BillOfMaterials (ComponentID, StartDate)  
        WHERE EndDate IS NOT NULL ;  
    GO  
    ```  
  
     <span data-ttu-id="818a3-181">上記のフィルター選択されたインデックスは、次のクエリに対して有効です。</span><span class="sxs-lookup"><span data-stu-id="818a3-181">The filtered index above is valid for the following query.</span></span> <span data-ttu-id="818a3-182">クエリ実行プランを表示して、クエリ オプティマイザーでフィルター選択されたインデックスが使用されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="818a3-182">You can display the query execution plan to determine if the query optimizer used the filtered index.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT ProductAssemblyID, ComponentID, StartDate   
    FROM Production.BillOfMaterials  
    WHERE EndDate IS NOT NULL   
        AND ComponentID = 5   
        AND StartDate > '01/01/2008' ;  
    GO  
    ```  
  
#### <a name="to-ensure-that-a-filtered-index-is-used-in-a-sql-query"></a><span data-ttu-id="818a3-183">フィルター選択されたインデックスが SQL クエリで使用されるようにするには</span><span class="sxs-lookup"><span data-stu-id="818a3-183">To ensure that a filtered index is used in a SQL query</span></span>  
  
1.  <span data-ttu-id="818a3-184">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="818a3-184">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="818a3-185">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="818a3-185">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="818a3-186">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="818a3-186">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT ComponentID, StartDate FROM Production.BillOfMaterials  
        WITH ( INDEX ( FIBillOfMaterialsWithEndDate ) )   
    WHERE EndDate IN ('20000825', '20000908', '20000918');   
    GO  
    ```  
  
 <span data-ttu-id="818a3-187">詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a3-187">For more information, see  [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
