---
title: クラスター化インデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index creation [SQL Server], clustered indexes
- clustered indexes, creating
- clustered indexes, PRIMARY KEY constraint
- clustered indexes, UNIQUE constraint
- indexes [SQL Server], clustered
ms.assetid: 47148383-c2c7-4f08-a9e4-7016bf2d1d13
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 567ff9a01bd93323149168b9e3aa0f34d78aee39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639960"
---
# <a name="create-clustered-indexes"></a><span data-ttu-id="94bbd-102">クラスター化インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="94bbd-102">Create Clustered Indexes</span></span>
  <span data-ttu-id="94bbd-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、テーブルにクラスター化インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-103">You can create clustered indexes on tables in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="94bbd-104">クラスター化インデックスは、いくつかの例外を除くすべてのテーブルに必要です。</span><span class="sxs-lookup"><span data-stu-id="94bbd-104">With few exceptions, every table should have a clustered index.</span></span> <span data-ttu-id="94bbd-105">クラスター化インデックスは、クエリ パフォーマンスを向上するだけではなく、必要に応じて再構築または再構成してテーブルの断片化を制御することができます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-105">Besides improving query performance, a clustered index can be rebuilt or reorganized on demand to control table fragmentation.</span></span> <span data-ttu-id="94bbd-106">また、クラスター化インデックスをビューに作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-106">A clustered index can also be created on a view.</span></span> <span data-ttu-id="94bbd-107">(クラスター化インデックスの定義は「 [クラスター化インデックスと非クラスター化インデックスの概念](clustered-and-nonclustered-indexes-described.md)」にあります。)</span><span class="sxs-lookup"><span data-stu-id="94bbd-107">(Clustered indexes are defined in the topic [Clustered and Nonclustered Indexes Described](clustered-and-nonclustered-indexes-described.md).)</span></span>  
  
 <span data-ttu-id="94bbd-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="94bbd-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="94bbd-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="94bbd-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="94bbd-110">一般的な実装</span><span class="sxs-lookup"><span data-stu-id="94bbd-110">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="94bbd-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="94bbd-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="94bbd-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="94bbd-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="94bbd-113">**テーブルにクラスター化インデックスを作成するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="94bbd-113">**To create a clustered index on a table, using:**</span></span>  
  
     [<span data-ttu-id="94bbd-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="94bbd-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="94bbd-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="94bbd-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="94bbd-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="94bbd-116">Before You Begin</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="94bbd-117">一般的な実装</span><span class="sxs-lookup"><span data-stu-id="94bbd-117">Typical Implementations</span></span>  
 <span data-ttu-id="94bbd-118">クラスター化インデックスは、次のように実装されます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-118">Clustered indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="94bbd-119">**PRIMARY KEY 制約と UNIQUE 制約**</span><span class="sxs-lookup"><span data-stu-id="94bbd-119">**PRIMARY KEY and UNIQUE constraints**</span></span>  
  
     <span data-ttu-id="94bbd-120">PRIMARY KEY 制約を作成すると、テーブルにクラスター化インデックスが存在せず、一意の非クラスター化インデックスを指定しなかった場合、列に一意のクラスター化インデックスが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-120">When you create a PRIMARY KEY constraint, a unique clustered index on the column or columns is automatically created if a clustered index on the table does not already exist and you do not specify a unique nonclustered index.</span></span> <span data-ttu-id="94bbd-121">主キー列には NULL 値を指定できません。</span><span class="sxs-lookup"><span data-stu-id="94bbd-121">The primary key column cannot allow NULL values.</span></span>  
  
     <span data-ttu-id="94bbd-122">UNIQUE 制約を作成すると、既定では、一意な非クラスター化インデックスが作成され、UNIQUE 制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-122">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="94bbd-123">テーブルにクラスター化インデックスが存在しない場合は、一意なクラスター化インデックスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-123">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span>  
  
     <span data-ttu-id="94bbd-124">制約の一部として作成されたインデックスには、自動的に制約名と同じ名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-124">An index created as part of the constraint is automatically given the same name as the constraint name.</span></span> <span data-ttu-id="94bbd-125">詳細については、「 [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) 」および「 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94bbd-125">For more information, see [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) and [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
-   <span data-ttu-id="94bbd-126">**制約に依存しないインデックス**</span><span class="sxs-lookup"><span data-stu-id="94bbd-126">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="94bbd-127">非クラスター化主キー制約が指定された場合、主キー列以外の列にクラスター化インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-127">You can create a clustered index on a column other than primary key column if a nonclustered primary key constraint was specified.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="94bbd-128">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="94bbd-128">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="94bbd-129">クラスター化インデックスの構造を作成する場合、古い (作成元の) 構造と新しい (作成先の) 構造の両方を格納するディスク領域が、それぞれのファイルとファイル グループで必要になります。</span><span class="sxs-lookup"><span data-stu-id="94bbd-129">When a clustered index structure is created, disk space for both the old (source) and new (target) structures is required in their respective files and filegroups.</span></span> <span data-ttu-id="94bbd-130">古い構造の割り当ては、トランザクション全体がコミットされるまで解除されません。</span><span class="sxs-lookup"><span data-stu-id="94bbd-130">The old structure is not deallocated until the complete transaction commits.</span></span> <span data-ttu-id="94bbd-131">並べ替え操作用に、余分な一時ディスク領域が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="94bbd-131">Additional temporary disk space for sorting may also be required.</span></span> <span data-ttu-id="94bbd-132">詳細については、「 [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="94bbd-132">For more information, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
-   <span data-ttu-id="94bbd-133">複数の非クラスター化インデックスが存在するヒープにクラスター化インデックスを作成する場合、すべての非クラスター化インデックスを再構築して、行識別子 (RID) の代わりにクラスター化キー値が含まれるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="94bbd-133">If a clustered index is created on a heap with several existing nonclustered indexes, all the nonclustered indexes must be rebuilt so that they contain the clustering key value instead of the row identifier (RID).</span></span> <span data-ttu-id="94bbd-134">同様に、複数の非クラスター化インデックスを持つテーブルのクラスター化インデックスを削除すると、DROP 操作の一部として非クラスター化インデックスがすべて再構築されます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-134">Similarly, if a clustered index is dropped on a table that has several nonclustered indexes, the nonclustered indexes are all rebuilt as part of the DROP operation.</span></span> <span data-ttu-id="94bbd-135">大きなテーブルでは、この操作に相当な時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="94bbd-135">This may take significant time on large tables.</span></span>  
  
     <span data-ttu-id="94bbd-136">大きなテーブルにインデックスを構築する場合、最初にクラスター化インデックスを構築してから、非クラスター化インデックスを構築することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-136">The preferred way to build indexes on large tables is to start with the clustered index and then build any nonclustered indexes.</span></span> <span data-ttu-id="94bbd-137">既存のテーブルにインデックスを作成するときは、ONLINE オプションを ON に設定することを検討します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-137">Consider setting the ONLINE option to ON when you create indexes on existing tables.</span></span> <span data-ttu-id="94bbd-138">ON に設定すると、テーブル ロックは長時間保持されません。</span><span class="sxs-lookup"><span data-stu-id="94bbd-138">When set to ON, long-term table locks are not held.</span></span> <span data-ttu-id="94bbd-139">これにより、基になるテーブルに対するクエリまたは更新を続行できます。</span><span class="sxs-lookup"><span data-stu-id="94bbd-139">This enables queries or updates to the underlying table to continue.</span></span> <span data-ttu-id="94bbd-140">詳しくは、「 [Perform Index Operations Online](perform-index-operations-online.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="94bbd-140">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
-   <span data-ttu-id="94bbd-141">クラスター化インデックスのインデックス キーには、ROW_OVERFLOW_DATA アロケーション ユニットに既存のデータを持つ `varchar` 列を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="94bbd-141">The index key of a clustered index cannot contain `varchar` columns that have existing data in the ROW_OVERFLOW_DATA allocation unit.</span></span> <span data-ttu-id="94bbd-142">クラスター化インデックスが `varchar` 列に作成され、その列の既存データが IN_ROW_DATA アロケーション ユニットにある場合、それ以後、既存データを行外に押し出すことになるような挿入や更新操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-142">If a clustered index is created on a `varchar` column and the existing data is in the IN_ROW_DATA allocation unit, subsequent insert or update actions on the column that would push the data off-row will fail.</span></span> <span data-ttu-id="94bbd-143">行オーバーフロー データを含んでいる可能性のあるテーブルまたはインデックスに関する情報を取得するには、[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) 動的管理関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-143">To obtain information about tables that might contain row-overflow data, use the [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) dynamic management function.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="94bbd-144">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="94bbd-144">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="94bbd-145">Permissions</span><span class="sxs-lookup"><span data-stu-id="94bbd-145">Permissions</span></span>  
 <span data-ttu-id="94bbd-146">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="94bbd-146">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="94bbd-147">実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="94bbd-147">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="94bbd-148">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="94bbd-148">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-clustered-index-by-using-object-explorer"></a><span data-ttu-id="94bbd-149">オブジェクト エクスプ ローラーを使用してクラスター化インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="94bbd-149">To create a clustered index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="94bbd-150">オブジェクト エクスプローラーで、クラスター化インデックスを作成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-150">In Object Explorer, expand the table on which you want to create a clustered index.</span></span>  
  
2.  <span data-ttu-id="94bbd-151">**[インデックス]** フォルダーを右クリックし、 **[新しいインデックス]** をポイントして、 **[クラスター化インデックス...]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-151">Right-click the **Indexes** folder, point to **New Index**, and select **Clustered Index...**.</span></span>  
  
3.  <span data-ttu-id="94bbd-152">**[新しいインデックス]** ダイアログ ボックスの **[全般]** ページで、 **[インデックス名]** ボックスに新しいインデックスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-152">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
4.  <span data-ttu-id="94bbd-153">**[インデックス キー列]** で、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-153">Under **Index key columns**, click **Add...**.</span></span>  
  
5.  <span data-ttu-id="94bbd-154">[Table_name**から列を選択**_table_name_ ] ダイアログボックスで、クラスター化インデックスに追加するテーブル列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-154">In the **Select Columns from**_table_name_ dialog box, select the check box of the table column to be added to the clustered index.</span></span>  
  
6.  <span data-ttu-id="94bbd-155">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-155">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="94bbd-156">**[新しいインデックス]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-156">In the **New Index** dialog box, click **OK**.</span></span>  
  
#### <a name="to-create-a-clustered-index-by-using-the-table-designer"></a><span data-ttu-id="94bbd-157">テーブル デザイナーを使用してクラスター化インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="94bbd-157">To create a clustered index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="94bbd-158">オブジェクト エクスプローラーで、クラスター化インデックスを含むテーブルを作成するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-158">In Object Explorer, expand the database on which you want to create a table with a clustered index.</span></span>  
  
2.  <span data-ttu-id="94bbd-159">**[テーブル]** フォルダーを右クリックし、 **[新しいテーブル...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-159">Right-click the **Tables** folder and click **New Table...**.</span></span>  
  
3.  <span data-ttu-id="94bbd-160">通常どおりに新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-160">Create a new table as you normally would.</span></span> <span data-ttu-id="94bbd-161">詳しくは、「[テーブルの作成 &#40;データベース エンジン&#41;](../tables/create-tables-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94bbd-161">For more information, see [Create Tables &#40;Database Engine&#41;](../tables/create-tables-database-engine.md).</span></span>  
  
4.  <span data-ttu-id="94bbd-162">上の手順で作成した新しいテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-162">Right-click the new table created above and click **Design**.</span></span>  
  
5.  <span data-ttu-id="94bbd-163">**[テーブル デザイナー]** メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-163">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
6.  <span data-ttu-id="94bbd-164">**[インデックス/キー]** ダイアログ ボックスで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-164">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
7.  <span data-ttu-id="94bbd-165">**[Selected Primary/Unique Key or Index (選択された主/一意キーまたはインデックス)]** ボックスで、新しいインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-165">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
8.  <span data-ttu-id="94bbd-166">グリッドで、 **[CLUSTERED として作成]** を選択し、プロパティ右のドロップダウン リストの **[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-166">In the grid, select **Create as Clustered**, and choose **Yes** from the drop-down list to the right of the property.</span></span>  
  
9. <span data-ttu-id="94bbd-167">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-167">Click **Close**.</span></span>  
  
10. <span data-ttu-id="94bbd-168">**[ファイル]** メニューの **テーブル名**_の保存]_ をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-168">On the **File** menu, click **Save**_table_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="94bbd-169">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="94bbd-169">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-clustered-index"></a><span data-ttu-id="94bbd-170">クラスター化インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="94bbd-170">To create a clustered index</span></span>  
  
1.  <span data-ttu-id="94bbd-171">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="94bbd-171">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="94bbd-172">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-172">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="94bbd-173">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94bbd-173">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Create a new table with three columns.  
    CREATE TABLE dbo.TestTable  
        (TestCol1 int NOT NULL,  
         TestCol2 nchar(10) NULL,  
         TestCol3 nvarchar(50) NULL);  
    GO  
    -- Create a clustered index called IX_TestTable_TestCol1  
    -- on the dbo.TestTable table using the TestCol1 column.  
    CREATE CLUSTERED INDEX IX_TestTable_TestCol1   
        ON dbo.TestTable (TestCol1);   
    GO  
    ```  
  
 <span data-ttu-id="94bbd-174">詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94bbd-174">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bbd-175">参照</span><span class="sxs-lookup"><span data-stu-id="94bbd-175">See Also</span></span>  
 <span data-ttu-id="94bbd-176">[主キーの作成](../tables/create-primary-keys.md) </span><span class="sxs-lookup"><span data-stu-id="94bbd-176">[Create Primary Keys](../tables/create-primary-keys.md) </span></span>  
 [<span data-ttu-id="94bbd-177">UNIQUE 制約の作成</span><span class="sxs-lookup"><span data-stu-id="94bbd-177">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)  
  
  
