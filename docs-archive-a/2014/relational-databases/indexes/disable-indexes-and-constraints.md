---
title: インデックスと制約の無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.disableindexes.f1
helpviewer_keywords:
- disabled indexes [SQL Server], index operations
- nonclustered indexes [SQL Server], disabling
- disabled indexes [SQL Server], guidelines
- clustered indexes, disabling
- constraints [SQL Server], disabling
- disabled indexes [SQL Server], viewing
- FOREIGN KEY constraints, disabling
- statistical information [SQL Server], indexes
- index disabling [SQL Server]
- indexed views [SQL Server], disabled indexes
ms.assetid: 2198f1af-fa44-47e9-92df-f4fde322ba18
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 40f9de4108be4defeb2353a9e7835c289641a819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740925"
---
# <a name="disable-indexes-and-constraints"></a><span data-ttu-id="c8355-102">インデックスと制約の無効化</span><span class="sxs-lookup"><span data-stu-id="c8355-102">Disable Indexes and Constraints</span></span>
  <span data-ttu-id="c8355-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、インデックスまたは制約を無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8355-103">This topic describes how to disable an index or constraints in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c8355-104">インデックスを無効にすると、ユーザーはそのインデックスにアクセスできなくなります。クラスター化インデックスの場合は、基になるテーブルのデータにもアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="c8355-104">Disabling an index prevents user access to the index, and for clustered indexes to the underlying table data.</span></span> <span data-ttu-id="c8355-105">ただし、インデックス定義はメタデータに残り、インデックス統計は非クラスター化インデックス上に保持されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-105">The index definition remains in metadata, and index statistics are kept on nonclustered indexes.</span></span> <span data-ttu-id="c8355-106">ビュー上で非クラスター化インデックスまたはクラスター化インデックスを無効にすると、インデックス データが物理的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-106">Disabling a nonclustered or clustered index on a view physically deletes the index data.</span></span> <span data-ttu-id="c8355-107">テーブルのクラスター化インデックスを無効にすると、データにアクセスできなくなります。つまり、データはテーブルに残りますが、そのインデックスを削除するか再構築するまでは、データ操作言語 (DML) 操作で使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c8355-107">Disabling a clustered index on a table prevents access to the data; the data still remains in the table, but is unavailable for data manipulation language (DML) operations until the index is dropped or rebuilt.</span></span>  
  
 <span data-ttu-id="c8355-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c8355-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c8355-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c8355-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c8355-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c8355-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c8355-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c8355-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c8355-112">**以下を使用してインデックスを無効化するには**</span><span class="sxs-lookup"><span data-stu-id="c8355-112">**To disable an index, using:**</span></span>  
  
     [<span data-ttu-id="c8355-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c8355-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c8355-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c8355-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c8355-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="c8355-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c8355-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c8355-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c8355-117">無効なインデックスは保守されません。</span><span class="sxs-lookup"><span data-stu-id="c8355-117">The index is not maintained while it is disabled.</span></span>  
  
-   <span data-ttu-id="c8355-118">クエリ オプティマイザーは、クエリの実行プランの作成時に無効なインデックスを考慮しません。</span><span class="sxs-lookup"><span data-stu-id="c8355-118">The query optimizer does not consider the disabled index when creating query execution plans.</span></span> <span data-ttu-id="c8355-119">また、無効化されたインデックスをテーブル ヒントで参照するクエリは失敗します。</span><span class="sxs-lookup"><span data-stu-id="c8355-119">Also, queries that reference the disabled index with a table hint fail.</span></span>  
  
-   <span data-ttu-id="c8355-120">無効になっている既存のインデックスと同じ名前のインデックスを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="c8355-120">You cannot create an index that uses the same name as an existing disabled index.</span></span>  
  
-   <span data-ttu-id="c8355-121">無効化されたインデックスは削除できます。</span><span class="sxs-lookup"><span data-stu-id="c8355-121">A disabled index can be dropped.</span></span>  
  
-   <span data-ttu-id="c8355-122">一意なインデックスを作成する場合、PRIMARY KEY 制約または UNIQUE 制約と、他のテーブルのインデックス付き列を参照するすべての FOREIGN KEY 制約も無効化されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-122">When disabling a unique index, the PRIMARY KEY or UNIQUE constraint and all FOREIGN KEY constraints that reference the indexed columns from other tables are also disabled.</span></span> <span data-ttu-id="c8355-123">クラスター化インデックスを無効にする場合、基になるテーブルを参照元または参照先とするすべての FOREIGN KEY 制約も無効になります。</span><span class="sxs-lookup"><span data-stu-id="c8355-123">When disabling a clustered index, all incoming and outgoing FOREIGN KEY constraints on the underlying table are also disabled.</span></span> <span data-ttu-id="c8355-124">インデックスを無効にすると、警告メッセージに制約名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-124">The constraint names are listed in a warning message when the index is disabled.</span></span> <span data-ttu-id="c8355-125">インデックスを再構築した後で、ALTER TABLE CHECK CONSTRAINT ステートメントを使用してすべての制約を手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8355-125">After rebuilding the index, all constraints must be manually enabled by using the ALTER TABLE CHECK CONSTRAINT statement.</span></span>  
  
-   <span data-ttu-id="c8355-126">非クラスター化インデックスは、関連付けられたクラスター化インデックスを無効にすると自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="c8355-126">Nonclustered indexes are automatically disabled when the associated clustered index is disabled.</span></span> <span data-ttu-id="c8355-127">非クラスター化インデックスを有効にするには、クラスター化インデックスを有効にする (テーブルまたはビューの場合) か、クラスター化インデックスを削除する (テーブルの場合) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8355-127">They cannot be enabled until either the clustered index on the table or view is enabled or the clustered index on the table is dropped.</span></span> <span data-ttu-id="c8355-128">ALTER INDEX ALL REBUILD ステートメントを使用してクラスター化インデックスを有効にした場合を除き、非クラスター化インデックスは明示的に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8355-128">Nonclustered indexes must be explicitly enabled, unless the clustered index was enabled by using the ALTER INDEX ALL REBUILD statement.</span></span>  
  
-   <span data-ttu-id="c8355-129">ALTER INDEX ALL REBUILD ステートメントを実行すると、ビューの無効化されたインデックスを除く、テーブル上の無効化されたインデックスがすべて再構築されて有効になります。</span><span class="sxs-lookup"><span data-stu-id="c8355-129">The ALTER INDEX ALL REBUILD statement rebuilds and enables all disabled indexes on the table, except for disabled indexes on views.</span></span> <span data-ttu-id="c8355-130">ビューのインデックスは、別の ALTER INDEX ALL REBUILD ステートメントで有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8355-130">Indexes on views must be enabled in a separate ALTER INDEX ALL REBUILD statement.</span></span>  
  
-   <span data-ttu-id="c8355-131">テーブルのクラスター化インデックスを無効にすると、そのテーブルを参照しているビューのクラスター化インデックスおよび非クラスター化インデックスもすべて無効になります。</span><span class="sxs-lookup"><span data-stu-id="c8355-131">Disabling a clustered index on a table also disables all clustered and nonclustered indexes on views that reference that table.</span></span> <span data-ttu-id="c8355-132">このようなインデックスは、参照先テーブルのインデックスと同時に再構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8355-132">These indexes must be rebuilt just as those on the referenced table.</span></span>  
  
-   <span data-ttu-id="c8355-133">無効化されたクラスター化インデックスのデータ行には、クラスター化インデックスを削除または再構築する場合以外はアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="c8355-133">The data rows of the disabled clustered index cannot be accessed except to drop or rebuild the clustered index.</span></span>  
  
-   <span data-ttu-id="c8355-134">無効化された非クラスター化インデックスは、無効化されたクラスター化インデックスがテーブルに存在しなければオンラインで再構築できます。</span><span class="sxs-lookup"><span data-stu-id="c8355-134">You can rebuild a disabled nonclustered index online when the table does not have a disabled clustered index.</span></span> <span data-ttu-id="c8355-135">ただし、ALTER INDEX REBUILD ステートメントまたは CREATE INDEX WITH DROP_EXISTING ステートメントのいずれかを使用している場合は常に、無効化されたクラスター化インデックスをオフラインで再構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8355-135">However, you must always rebuild a disabled clustered index offline if you use either the ALTER INDEX REBUILD or CREATE INDEX WITH DROP_EXISTING statement.</span></span> <span data-ttu-id="c8355-136">オンラインでのインデックス操作の詳細については、「 [オンラインでのインデックス操作の実行](perform-index-operations-online.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8355-136">For more information about online index operations, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
-   <span data-ttu-id="c8355-137">クラスター化インデックスが無効になっているテーブルに対して、CREATE STATISTICS ステートメントを正常に実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="c8355-137">The CREATE STATISTICS statement cannot be successfully executed on a table that has a disabled clustered index.</span></span>  
  
-   <span data-ttu-id="c8355-138">インデックスが無効であり、次の条件に一致する場合、AUTO_CREATE_STATISTICS データベース オプションを指定することで列の新しい統計が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-138">The AUTO_CREATE_STATISTICS database option creates new statistics on a column when the index is disabled and the following conditions exist:</span></span>  
  
    -   <span data-ttu-id="c8355-139">AUTO_CREATE_STATISTICS が ON に設定されている</span><span class="sxs-lookup"><span data-stu-id="c8355-139">AUTO_CREATE_STATISTICS is set to ON</span></span>  
  
    -   <span data-ttu-id="c8355-140">列の統計がまだ存在しない</span><span class="sxs-lookup"><span data-stu-id="c8355-140">There are no existing statistics for the column.</span></span>  
  
    -   <span data-ttu-id="c8355-141">クエリの最適化で統計が必要である</span><span class="sxs-lookup"><span data-stu-id="c8355-141">Statistics are required during query optimization.</span></span>  
  
-   <span data-ttu-id="c8355-142">クラスター化インデックスが無効になっている場合、 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) は基になるテーブルに関する情報を返すことができません。代わりに、クラスター化インデックスが無効であることが報告されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-142">If a clustered index is disabled, [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) cannot return information about the underlying table; instead, the statement reports that the clustered index is disabled.</span></span> <span data-ttu-id="c8355-143">[DBCC INDEXDEFRAG](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql) を使用して、無効化されたインデックスの断片化を解消することはできません。このステートメントはエラー メッセージを出力して失敗します。</span><span class="sxs-lookup"><span data-stu-id="c8355-143">[DBCC INDEXDEFRAG](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql) cannot be used to defragment a disabled index; the statement fails with an error message.</span></span> <span data-ttu-id="c8355-144">無効化されたインデックスの再構築には [DBCC DBREINDEX](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8355-144">You can use [DBCC DBREINDEX](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) to rebuild a disabled index.</span></span>  
  
-   <span data-ttu-id="c8355-145">新しいクラスター化インデックスを作成すると、以前に無効化された非クラスター化インデックスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="c8355-145">Creating a new clustered index enables previously disabled nonclustered indexes.</span></span> <span data-ttu-id="c8355-146">詳しくは、「 [Enable Indexes and Constraints](enable-indexes-and-constraints.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c8355-146">For more information, see [Enable Indexes and Constraints](enable-indexes-and-constraints.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c8355-147">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c8355-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c8355-148">Permissions</span><span class="sxs-lookup"><span data-stu-id="c8355-148">Permissions</span></span>  
 <span data-ttu-id="c8355-149">ALTER INDEX を実行するには、少なくとも、テーブルまたはビューの ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c8355-149">To execute ALTER INDEX, at a minimum, ALTER permission on the table or view is required.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c8355-150">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c8355-150">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-an-index"></a><span data-ttu-id="c8355-151">インデックスを無効にするには</span><span class="sxs-lookup"><span data-stu-id="c8355-151">To disable an index</span></span>  
  
1.  <span data-ttu-id="c8355-152">オブジェクト エクスプローラーで、インデックスを無効にするテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="c8355-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to disable an index.</span></span>  
  
2.  <span data-ttu-id="c8355-153">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c8355-153">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="c8355-154">プラス記号をクリックして、インデックスを無効にするテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="c8355-154">Click the plus sign to expand the table on which you want to disable an index.</span></span>  
  
4.  <span data-ttu-id="c8355-155">プラス記号をクリックして **[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c8355-155">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="c8355-156">無効にするインデックスを右クリックし、 **[無効化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8355-156">Right-click the index you want to disable and select **Disable**.</span></span>  
  
6.  <span data-ttu-id="c8355-157">**[インデックスの無効化]** ダイアログ ボックスで、 **[無効にするインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8355-157">In the **Disable Indexes** dialog box, verify that the correct index is in the **Indexes to disable** grid and click **OK**.</span></span>  
  
#### <a name="to-disable-all-indexes-on-a-table"></a><span data-ttu-id="c8355-158">テーブルのすべてのインデックスを無効にするには</span><span class="sxs-lookup"><span data-stu-id="c8355-158">To disable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="c8355-159">オブジェクト エクスプローラーで、インデックスを無効にするテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="c8355-159">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to disable the indexes.</span></span>  
  
2.  <span data-ttu-id="c8355-160">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c8355-160">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="c8355-161">プラス記号をクリックして、インデックスを無効にするテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="c8355-161">Click the plus sign to expand the table on which you want to disable the indexes.</span></span>  
  
4.  <span data-ttu-id="c8355-162">**[インデックス]** フォルダーを右クリックし、 **[すべて無効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8355-162">Right-click the **Indexes** folder and select **Disable All**.</span></span>  
  
5.  <span data-ttu-id="c8355-163">**[インデックスの無効化]** ダイアログ ボックスで、 **[無効にするインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8355-163">In the **Disable Indexes** dialog box, verify that the correct indexes are in the **Indexes to disable** grid and click **OK**.</span></span> <span data-ttu-id="c8355-164">**[無効にするインデックス]** グリッドからインデックスを削除するには、インデックスを選択し、Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c8355-164">To remove an index from the **Indexes to disable** grid, select the index and then press the Delete key.</span></span>  
  
 <span data-ttu-id="c8355-165">**[無効にするインデックス]** ダイアログ ボックスには、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-165">The following information is available in the **Disable Indexes** dialog box:</span></span>  
  
 <span data-ttu-id="c8355-166">**Index Name**</span><span class="sxs-lookup"><span data-stu-id="c8355-166">**Index Name**</span></span>  
 <span data-ttu-id="c8355-167">インデックスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c8355-167">Displays the name of the index.</span></span> <span data-ttu-id="c8355-168">実行中は、状態を表すアイコンもこの列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-168">During execution, this column also displays an icon representing the status.</span></span>  
  
 <span data-ttu-id="c8355-169">**テーブル名**</span><span class="sxs-lookup"><span data-stu-id="c8355-169">**Table Name**</span></span>  
 <span data-ttu-id="c8355-170">インデックスが作成されているテーブルまたはビューの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c8355-170">Displays the name of the table or view that the index was created on.</span></span>  
  
 <span data-ttu-id="c8355-171">**[インデックスの種類]**</span><span class="sxs-lookup"><span data-stu-id="c8355-171">**Index Type**</span></span>  
 <span data-ttu-id="c8355-172">インデックスの種類 ( **[クラスター化]** 、 **[非クラスター化]** 、 **[空間]** 、または **[XML]** ) を表示します。</span><span class="sxs-lookup"><span data-stu-id="c8355-172">Displays the type of the index: **Clustered**, **Nonclustered**, **Spatial**, or **XML**.</span></span>  
  
 <span data-ttu-id="c8355-173">**状態**</span><span class="sxs-lookup"><span data-stu-id="c8355-173">**Status**</span></span>  
 <span data-ttu-id="c8355-174">無効化操作の状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="c8355-174">Displays the status of the disable operation.</span></span> <span data-ttu-id="c8355-175">実行後の値は、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="c8355-175">Possible values after execution are:</span></span>  
  
-   <span data-ttu-id="c8355-176">空白</span><span class="sxs-lookup"><span data-stu-id="c8355-176">Blank</span></span>  
  
     <span data-ttu-id="c8355-177">実行前の **[状態]** は空白です。</span><span class="sxs-lookup"><span data-stu-id="c8355-177">Prior to execution **Status** is blank.</span></span>  
  
-   <span data-ttu-id="c8355-178">**[実行中]**</span><span class="sxs-lookup"><span data-stu-id="c8355-178">**In progress**</span></span>  
  
     <span data-ttu-id="c8355-179">インデックスの無効化操作が開始されましたが、まだ完了していません。</span><span class="sxs-lookup"><span data-stu-id="c8355-179">Disabling of the indexes has been started but is not complete.</span></span>  
  
-   <span data-ttu-id="c8355-180">**Success**</span><span class="sxs-lookup"><span data-stu-id="c8355-180">**Success**</span></span>  
  
     <span data-ttu-id="c8355-181">インデックスの無効化操作は正常に終了しました。</span><span class="sxs-lookup"><span data-stu-id="c8355-181">The disable operation completed successfully.</span></span>  
  
-   <span data-ttu-id="c8355-182">**Error**</span><span class="sxs-lookup"><span data-stu-id="c8355-182">**Error**</span></span>  
  
     <span data-ttu-id="c8355-183">インデックスの無効化操作の実行中にエラーが発生したため、操作が正常に終了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="c8355-183">An error was encountered during the index disable operation, and the operation did not complete successfully.</span></span>  
  
-   <span data-ttu-id="c8355-184">**停止**</span><span class="sxs-lookup"><span data-stu-id="c8355-184">**Stopped**</span></span>  
  
     <span data-ttu-id="c8355-185">インデックスの無効化操作はユーザーによって中止されたため、正常に終了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="c8355-185">The disable of the index was not completed successfully because the user stopped the operation.</span></span>  
  
 <span data-ttu-id="c8355-186">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="c8355-186">**Message**</span></span>  
 <span data-ttu-id="c8355-187">無効化操作中にエラー メッセージのテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="c8355-187">Provides the text of error messages during the disable operation.</span></span> <span data-ttu-id="c8355-188">実行中、エラーはハイパーリンクとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-188">During execution, errors appear as hyperlinks.</span></span> <span data-ttu-id="c8355-189">エラーの内容は、ハイパーリンクのテキストに示されます。</span><span class="sxs-lookup"><span data-stu-id="c8355-189">The text of the hyperlinks describes the body of the error.</span></span> <span data-ttu-id="c8355-190">多くの場合、 **[メッセージ]** 列が狭いためにメッセージ テキスト全体が表示されません。</span><span class="sxs-lookup"><span data-stu-id="c8355-190">The **Message** column is rarely wide enough to read the full message text.</span></span> <span data-ttu-id="c8355-191">テキスト全体を表示するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="c8355-191">There are two ways to get the full text:</span></span>  
  
-   <span data-ttu-id="c8355-192">マウス ポインターをメッセージ セル上に移動して、ツールヒントにエラー テキストが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="c8355-192">Move the mouse pointer over the message cell to display a ToolTip with the error text.</span></span>  
  
-   <span data-ttu-id="c8355-193">ハイパーリンクをクリックして、エラー全体を表示するダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="c8355-193">Click the hyperlink to display a dialog box displaying the full error.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c8355-194">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c8355-194">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-an-index"></a><span data-ttu-id="c8355-195">インデックスを無効にするには</span><span class="sxs-lookup"><span data-stu-id="c8355-195">To disable an index</span></span>  
  
1.  <span data-ttu-id="c8355-196">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c8355-196">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c8355-197">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8355-197">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c8355-198">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8355-198">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- disables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    DISABLE;  
    ```  
  
#### <a name="to-disable-all-indexes-on-a-table"></a><span data-ttu-id="c8355-199">テーブルのすべてのインデックスを無効にするには</span><span class="sxs-lookup"><span data-stu-id="c8355-199">To disable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="c8355-200">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c8355-200">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c8355-201">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8355-201">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c8355-202">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8355-202">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Disables all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    DISABLE;  
    ```  
  
 <span data-ttu-id="c8355-203">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8355-203">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
