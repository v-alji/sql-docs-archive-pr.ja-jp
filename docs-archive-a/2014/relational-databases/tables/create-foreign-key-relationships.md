---
title: 外部キーのリレーションシップの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], creating
ms.assetid: 867a54b8-5be4-46e6-9702-49ae6dabf67c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ee0de3311eb6abffcdb71ab725d0650fe96b04c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646100"
---
# <a name="create-foreign-key-relationships"></a><span data-ttu-id="d6186-102">外部キーのリレーションシップの作成</span><span class="sxs-lookup"><span data-stu-id="d6186-102">Create Foreign Key Relationships</span></span>
  <span data-ttu-id="d6186-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で外部キーのリレーションシップを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6186-103">This topic describes how to create foreign key relationships in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d6186-104">あるテーブルの行と他のテーブルの行を関連付ける場合は、2 つのテーブル間にリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6186-104">You create a relationship between two tables when you want to associate rows of one table with rows of another.</span></span>  
  
 <span data-ttu-id="d6186-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d6186-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d6186-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d6186-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d6186-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d6186-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d6186-108">Security</span><span class="sxs-lookup"><span data-stu-id="d6186-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d6186-109">**以下を使用して外部キー リレーションシップを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="d6186-109">**To Create Foreign Key Relationships by using:**</span></span>  
  
     [<span data-ttu-id="d6186-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d6186-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d6186-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d6186-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d6186-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="d6186-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d6186-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d6186-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d6186-114">外部キー制約からリンクを設定できるのは、別のテーブルの主キー制約だけではありません。別のテーブルの UNIQUE 制約が定義された列を参照するように定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6186-114">A foreign key constraint does not have to be linked only to a primary key constraint in another table; it can also be defined to reference the columns of a UNIQUE constraint in another table.</span></span>  
  
-   <span data-ttu-id="d6186-115">FOREIGN KEY 制約の列に NULL 以外の値を入力するときは、その値が参照される列に存在している必要があります。存在していないと外部キー違反のエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="d6186-115">When a value other than NULL is entered into the column of a FOREIGN KEY constraint, the value must exist in the referenced column; otherwise, a foreign key violation error message is returned.</span></span> <span data-ttu-id="d6186-116">複合外部キー制約のすべての値が検証されるようにするには、参加しているすべての列に NOT NULL を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6186-116">To make sure that all values of a composite foreign key constraint are verified, specify NOT NULL on all the participating columns.</span></span>  
  
-   <span data-ttu-id="d6186-117">FOREIGN KEY 制約は、同じサーバー上の同じデータベース内のテーブルのみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="d6186-117">FOREIGN KEY constraints can reference only tables within the same database on the same server.</span></span> <span data-ttu-id="d6186-118">複数のデータベースにまたがる参照整合性は、トリガーを使って実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6186-118">Cross-database referential integrity must be implemented through triggers.</span></span> <span data-ttu-id="d6186-119">詳細については、「[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6186-119">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
-   <span data-ttu-id="d6186-120">FOREIGN KEY 制約は、同じテーブル内の他の列を参照できます。</span><span class="sxs-lookup"><span data-stu-id="d6186-120">FOREIGN KEY constraints can reference another column in the same table.</span></span> <span data-ttu-id="d6186-121">これは、自己参照と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d6186-121">This is referred to as a self-reference.</span></span>  
  
-   <span data-ttu-id="d6186-122">列レベルで指定された FOREIGN KEY 制約は、参照列を 1 つだけ表示できます。</span><span class="sxs-lookup"><span data-stu-id="d6186-122">A FOREIGN KEY constraint specified at the column level can list only one reference column.</span></span> <span data-ttu-id="d6186-123">この参照列は、制約が定義されている列と同じデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6186-123">This column must have the same data type as the column on which the constraint is defined.</span></span>  
  
-   <span data-ttu-id="d6186-124">テーブルレベルで指定された FOREIGN KEY 制約は、制約列リスト内の列の数と同じ数の参照列を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6186-124">A FOREIGN KEY constraint specified at the table level must have the same number of reference columns as the number of columns in the constraint column list.</span></span> <span data-ttu-id="d6186-125">また、各参照列のデータ型は、列リスト内の、参照列に対応する列と同じでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="d6186-125">The data type of each reference column must also be the same as the corresponding column in the column list.</span></span>  
  
-   <span data-ttu-id="d6186-126">[!INCLUDE[ssDE](../../includes/ssde-md.md)] には、他のテーブルを参照するテーブルに含めることができる FOREIGN KEY 制約の数についても、特定のテーブルを参照する他のテーブルが持つ FOREIGN KEY 制約の数についても、事前定義済みの制限はありません。</span><span class="sxs-lookup"><span data-stu-id="d6186-126">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not have a predefined limit on either the number of FOREIGN KEY constraints a table can contain that reference other tables, or the number of FOREIGN KEY constraints that are owned by other tables that reference a specific table.</span></span> <span data-ttu-id="d6186-127">ただし、使用できる FOREIGN KEY 制約の実際の数は、ハードウェア構成やデータベースおよびアプリケーションのデザインにより制限されます。</span><span class="sxs-lookup"><span data-stu-id="d6186-127">Nevertheless, the actual number of FOREIGN KEY constraints that can be used is limited by the hardware configuration and by the design of the database and application.</span></span> <span data-ttu-id="d6186-128">1 つのテーブルに含める FOREIGN KEY 制約は 253 個までとし、253 個以内の FOREIGN KEY 制約から参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d6186-128">We recommend that a table contain no more than 253 FOREIGN KEY constraints, and that it be referenced by no more than 253 FOREIGN KEY constraints.</span></span>  
  
-   <span data-ttu-id="d6186-129">FOREIGN KEY 制約は一時テーブルには設定されません。</span><span class="sxs-lookup"><span data-stu-id="d6186-129">FOREIGN KEY constraints are not enforced on temporary tables.</span></span>  
  
-   <span data-ttu-id="d6186-130">CLR ユーザー定義型の列に対して外部キーを定義する場合は、型の実装でバイナリ順がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6186-130">If a foreign key is defined on a CLR user-defined type column, the implementation of the type must support binary ordering.</span></span> <span data-ttu-id="d6186-131">詳細については、「 [CLR ユーザー定義型](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6186-131">For more information, see [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).</span></span>  
  
-   <span data-ttu-id="d6186-132">`varchar(max)` 型の列は、その列が参照する主キーも `varchar(max)` 型として定義されている場合にのみ FOREIGN KEY 制約で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6186-132">A column of type `varchar(max)` can participate in a FOREIGN KEY constraint only if the primary key it references is also defined as type `varchar(max)`.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d6186-133">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d6186-133">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d6186-134">Permissions</span><span class="sxs-lookup"><span data-stu-id="d6186-134">Permissions</span></span>  
 <span data-ttu-id="d6186-135">外部キーが設定された、新しいテーブルを作成するには、データベースの CREATE TABLE 権限と、テーブルを作成するスキーマの ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d6186-135">Creating a new table with a foreign key requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>  
  
 <span data-ttu-id="d6186-136">既存のテーブルに外部キーを作成するには、テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d6186-136">Creating a foreign key in an existing table requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d6186-137">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d6186-137">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-foreign-key-relationship-in-table-designer"></a><span data-ttu-id="d6186-138">テーブル デザイナーで外部キー リレーションシップを作成するには</span><span class="sxs-lookup"><span data-stu-id="d6186-138">To create a foreign key relationship in Table Designer</span></span>  
  
1.  <span data-ttu-id="d6186-139">オブジェクト エクスプローラーで、リレーションシップの外部キー側となるテーブルを右クリックして、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-139">In Object Explorer, right-click the table that will be on the foreign-key side of the relationship and click **Design**.</span></span>  
  
     <span data-ttu-id="d6186-140"> **[テーブル デザイナー]**  にテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6186-140">The table opens in **Table Designer**.</span></span>  
  
2.  <span data-ttu-id="d6186-141">**[テーブル デザイナー]** メニューの **[リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-141">From the **Table Designer** menu, click **Relationships**.</span></span>  
  
3.  <span data-ttu-id="d6186-142">**[外部キーのリレーションシップ]** ダイアログ ボックスで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-142">In the **Foreign-key Relationships** dialog box, click **Add**.</span></span>  
  
     <span data-ttu-id="d6186-143">リレーションシップが **[選択されたリレーションシップ]** ボックスに表示されます。このリレーションシップには、FK_\<*tablename*>_\<*tablename*> (*tablename* は外部キー テーブルの名前) という形式の名前が自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d6186-143">The relationship appears in the **Selected Relationship** list with a system-provided name in the format FK_\<*tablename*>_\<*tablename*>, where *tablename* is the name of the foreign key table.</span></span>  
  
4.  <span data-ttu-id="d6186-144">**[選択されたリレーションシップ]** ボックスの一覧で、リレーションシップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-144">Click the relationship in the **Selected Relationship** list.</span></span>  
  
5.  <span data-ttu-id="d6186-145">右側のグリッドの **[テーブルと列の指定]** をクリックし、その右側にある省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-145">Click **Tables and Columns Specification** in the grid to the right and click the ellipses (**...**) to the right of the property.</span></span>  
  
6.  <span data-ttu-id="d6186-146">**[テーブルと列]** ダイアログ ボックスの **[主キー]** ボックスの一覧で、リレーションシップの主キー側となるテーブルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-146">In the **Tables and Columns** dialog box, in the **Primary Key** drop-down list, choose the table that will be on the primary-key side of the relationship.</span></span>  
  
7.  <span data-ttu-id="d6186-147">下のグリッドで、テーブルの主キーになる列を選択します。</span><span class="sxs-lookup"><span data-stu-id="d6186-147">In the grid beneath, choose the columns contributing to the table's primary key.</span></span> <span data-ttu-id="d6186-148">各列の左横のグリッド セルで、外部キー テーブルの対応する外部キー列を選択します。</span><span class="sxs-lookup"><span data-stu-id="d6186-148">In the adjacent grid cell to the left of each column, choose the corresponding foreign-key column of the foreign-key table.</span></span>  
  
     <span data-ttu-id="d6186-149">リレーションシップの名前は、**テーブル デザイナー** によって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d6186-149">**Table Designer** suggests a name for the relationship.</span></span> <span data-ttu-id="d6186-150">この名前を変更するには、 **[リレーションシップ名]** ボックスの内容を編集します。</span><span class="sxs-lookup"><span data-stu-id="d6186-150">To change this name, edit the contents of the **Relationship Name** text box.</span></span>  
  
8.  <span data-ttu-id="d6186-151">**[OK]** をクリックしてリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6186-151">Choose **OK** to create the relationship.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d6186-152">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d6186-152">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-foreign-key-in-a-new-table"></a><span data-ttu-id="d6186-153">新しいテーブルに外部キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="d6186-153">To create a foreign key in a new table</span></span>  
  
1.  <span data-ttu-id="d6186-154">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d6186-154">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d6186-155">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-155">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d6186-156">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-156">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d6186-157">この例では、テーブルを作成し、`Sales.SalesReason` テーブル内の `SalesReasonID` 列を参照する外部キー制約を `TempID` 列に定義します。</span><span class="sxs-lookup"><span data-stu-id="d6186-157">The example creates a table and defines a foreign key constraint on the column `TempID` that references the column `SalesReasonID` in the `Sales.SalesReason` table.</span></span> <span data-ttu-id="d6186-158">ON DELETE CASCADE 句および ON UPDATE CASCADE 句を使用することによって、`Sales.SalesReason` テーブルに対する変更が自動的に `Sales.TempSalesReason` テーブルにも反映されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="d6186-158">The ON DELETE CASCADE and ON UPDATE CASCADE clauses are used to ensure that changes made to `Sales.SalesReason` table are automatically propagated to the `Sales.TempSalesReason` table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Sales.TempSalesReason (TempID int NOT NULL, Name nvarchar(50),   
    CONSTRAINT PK_TempSales PRIMARY KEY NONCLUSTERED (TempID),   
    CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    );GO  
  
    ```  
  
#### <a name="to-create-a-foreign-key-in-an-existing-table"></a><span data-ttu-id="d6186-159">既存のテーブルに外部キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="d6186-159">To create a foreign key in an existing table</span></span>  
  
1.  <span data-ttu-id="d6186-160">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d6186-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d6186-161">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d6186-162">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6186-162">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d6186-163">この例では、`TempID` 列に外部キーを作成し、`Sales.SalesReason` テーブルの `SalesReasonID` 列を参照します。</span><span class="sxs-lookup"><span data-stu-id="d6186-163">The example creates a foreign key on the column `TempID` and references the column `SalesReasonID` in the `Sales.SalesReason` table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Sales.TempSalesReason   
    ADD CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    ;  
    GO  
  
    ```  
  
     <span data-ttu-id="d6186-164">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」、「[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)」、および「[table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6186-164">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
  
