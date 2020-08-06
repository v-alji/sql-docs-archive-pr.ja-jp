---
title: 非クラスター化インデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index creation [SQL Server], nonclustered indexes
- nonclustered indexes [SQL Server], creating
- nonclustered indexes [SQL Server], UNIQUE constraint
- indexes [SQL Server], nonclustered
- nonclustered indexes [SQL Server], PRIMARY KEY constraint
ms.assetid: 9402029a-1227-46c4-93aa-c2122eb1b943
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fae0c06b1f562dc3fc518a319df1787b3384c0cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740937"
---
# <a name="create-nonclustered-indexes"></a><span data-ttu-id="d2352-102">非クラスター化インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="d2352-102">Create Nonclustered Indexes</span></span>
  <span data-ttu-id="d2352-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して非クラスター化インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d2352-103">You can create nonclustered indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d2352-104">非クラスター化インデックスは、テーブルに格納されているデータとは別個の、選択された 1 つまたは複数の列を並べ替えるインデックス構造です。</span><span class="sxs-lookup"><span data-stu-id="d2352-104">A nonclustered index is an index structure separate from the data stored in a table that reorders one or more selected columns.</span></span> <span data-ttu-id="d2352-105">非クラスター化インデックスを使用すると、基になるテーブルを検索するよりも迅速にデータを検索できるようになります。クエリの結果が非クラスター化インデックスのデータのみによって得られたり、非クラスター化インデックスによって基になるテーブル内の行を [!INCLUDE[ssDE](../../includes/ssde-md.md)] に対して指定できたりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="d2352-105">Nonclustered indexes can often help you find data more quickly than searching the underlying table; queries can sometimes be answered entirely by the data in the nonclustered index, or the nonclustered index can point the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to the rows in the underlying table.</span></span> <span data-ttu-id="d2352-106">一般に、非クラスター化インデックスは、クラスター化インデックスで対応できない、頻繁に使用されるクエリのパフォーマンスを向上させたり、クラスター化インデックスのないテーブル (ヒープと呼ばれます) 内の行を探すために作成します。</span><span class="sxs-lookup"><span data-stu-id="d2352-106">Generally, nonclustered indexes are created to improve the performance of frequently used queries not covered by the clustered index or to locate rows in a table without a clustered index (called a heap).</span></span> <span data-ttu-id="d2352-107">1 つのテーブルまたはインデックス付きビューに複数の非クラスター化インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d2352-107">You can create multiple nonclustered indexes on a table or indexed view.</span></span>  
  
 <span data-ttu-id="d2352-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d2352-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d2352-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d2352-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d2352-110">一般的な実装</span><span class="sxs-lookup"><span data-stu-id="d2352-110">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="d2352-111">Security</span><span class="sxs-lookup"><span data-stu-id="d2352-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d2352-112">**非クラスター化インデックスを作成するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="d2352-112">**To create a nonclustered index, using:**</span></span>  
  
     [<span data-ttu-id="d2352-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d2352-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d2352-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d2352-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d2352-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="d2352-115">Before You Begin</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a><span data-ttu-id="d2352-116">一般的な実装</span><span class="sxs-lookup"><span data-stu-id="d2352-116">Typical Implementations</span></span>  
 <span data-ttu-id="d2352-117">非クラスター化インデックスは、次のように実装されます。</span><span class="sxs-lookup"><span data-stu-id="d2352-117">Nonclustered indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="d2352-118">**UNIQUE 制約**</span><span class="sxs-lookup"><span data-stu-id="d2352-118">**UNIQUE constraints**</span></span>  
  
     <span data-ttu-id="d2352-119">UNIQUE 制約を作成すると、既定では、一意な非クラスター化インデックスが作成され、UNIQUE 制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d2352-119">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="d2352-120">テーブルにクラスター化インデックスが存在しない場合は、一意なクラスター化インデックスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d2352-120">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span> <span data-ttu-id="d2352-121">詳細については、「 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2352-121">For more information, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
-   <span data-ttu-id="d2352-122">**制約に依存しないインデックス**</span><span class="sxs-lookup"><span data-stu-id="d2352-122">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="d2352-123">既定では、クラスター化オプションが指定されていない場合に、非クラスター化インデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d2352-123">By default, a nonclustered index is created if clustered is not specified.</span></span> <span data-ttu-id="d2352-124">非クラスター化インデックスは、1 つのテーブルに 999 個まで作成できます。</span><span class="sxs-lookup"><span data-stu-id="d2352-124">The maximum number of nonclustered indexes that can be created per table is 999.</span></span> <span data-ttu-id="d2352-125">これには、PRIMARY KEY 制約または UNIQUE 制約によって作成されたインデックスを含みますが、XML インデックスは含みせん。</span><span class="sxs-lookup"><span data-stu-id="d2352-125">This includes any indexes created by PRIMARY KEY or UNIQUE constraints, but does not include XML indexes.</span></span>  
  
-   <span data-ttu-id="d2352-126">**インデックス付きビューの非クラスター化インデックス**</span><span class="sxs-lookup"><span data-stu-id="d2352-126">**Nonclustered index on an indexed view**</span></span>  
  
     <span data-ttu-id="d2352-127">非クラスター化インデックスは、ビューで一意なクラスター化インデックスが作成されるまで作成できません。</span><span class="sxs-lookup"><span data-stu-id="d2352-127">After a unique clustered index has been created on a view, nonclustered indexes can be created.</span></span> <span data-ttu-id="d2352-128">詳細については、「 [インデックス付きビューの作成](../views/views.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2352-128">For more information, see [Create Indexed Views](../views/views.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d2352-129">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d2352-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d2352-130">Permissions</span><span class="sxs-lookup"><span data-stu-id="d2352-130">Permissions</span></span>  
 <span data-ttu-id="d2352-131">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d2352-131">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="d2352-132">実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2352-132">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d2352-133">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d2352-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-nonclustered-index-by-using-the-table-designer"></a><span data-ttu-id="d2352-134">テーブル デザイナーを使用して非クラスター化インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="d2352-134">To create a nonclustered index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="d2352-135">オブジェクト エクスプローラーで、非クラスター化インデックスを作成するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="d2352-135">In Object Explorer, expand the database that contains the table on which you want to create a nonclustered index.</span></span>  
  
2.  <span data-ttu-id="d2352-136">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="d2352-136">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="d2352-137">非クラスター化インデックスを作成するテーブルを右クリックし、 **[デザイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d2352-137">Right-click the table on which you want to create a nonclustered index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="d2352-138">[**テーブルデザイナー** ] メニューの [**インデックス/キー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-138">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="d2352-139">**[インデックス/キー]** ダイアログ ボックスで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-139">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="d2352-140">**[Selected Primary/Unique Key or Index (選択された主/一意キーまたはインデックス)]** ボックスで、新しいインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="d2352-140">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
7.  <span data-ttu-id="d2352-141">グリッドで、 **[CLUSTERED として作成]** を選択し、プロパティ右のドロップダウン リストの **[いいえ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d2352-141">In the grid, select **Create as Clustered**, and choose **No** from the drop-down list to the right of the property.</span></span>  
  
8.  <span data-ttu-id="d2352-142">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-142">Click **Close**.</span></span>  
  
9. <span data-ttu-id="d2352-143">**[ファイル]** メニューの **テーブル名**_の保存]_ をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-143">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="to-create-a-nonclustered-index-by-using-object-explorer"></a><span data-ttu-id="d2352-144">オブジェクト エクスプ ローラーを使用して非クラスター化インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="d2352-144">To create a nonclustered index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="d2352-145">オブジェクト エクスプローラーで、非クラスター化インデックスを作成するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="d2352-145">In Object Explorer, expand the database that contains the table on which you want to create a nonclustered index.</span></span>  
  
2.  <span data-ttu-id="d2352-146">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="d2352-146">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="d2352-147">非クラスター化インデックスを作成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="d2352-147">Expand the table on which you want to create a nonclustered index.</span></span>  
  
4.  <span data-ttu-id="d2352-148">**[インデックス]** フォルダーを右クリックし、 **[新しいインデックス]** をポイントし、 **[非クラスター化インデックス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d2352-148">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="d2352-149">**[新しいインデックス]** ダイアログ ボックスの **[全般]** ページで、 **[インデックス名]** ボックスに新しいインデックスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2352-149">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="d2352-150">**[インデックス キー列]** で、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-150">Under **Index key columns**, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="d2352-151">**テーブル名**_から列を選択]_ ダイアログ ボックスで、非クラスター化インデックスに追加する 1 つまたは複数のテーブル列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d2352-151">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the nonclustered index.</span></span>  
  
8.  <span data-ttu-id="d2352-152">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-152">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d2352-153">**[新しいインデックス]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-153">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d2352-154">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d2352-154">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-nonclustered-index-on-a-table"></a><span data-ttu-id="d2352-155">テーブルに非クラスター化インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="d2352-155">To create a nonclustered index on a table</span></span>  
  
1.  <span data-ttu-id="d2352-156">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d2352-156">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d2352-157">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-157">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d2352-158">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2352-158">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named IX_ProductVendor_VendorID and delete it if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
                WHERE name = N'IX_ProductVendor_VendorID')   
        DROP INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor;   
    GO  
    -- Create a nonclustered index called IX_ProductVendor_VendorID   
    -- on the Purchasing.ProductVendor table using the BusinessEntityID column.   
    CREATE NONCLUSTERED INDEX IX_ProductVendor_VendorID   
        ON Purchasing.ProductVendor (BusinessEntityID);   
    GO  
    ```  
  
 <span data-ttu-id="d2352-159">詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2352-159">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
