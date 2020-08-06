---
title: テーブル間での列のコピー (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying columns
- columns [SQL Server], copying
ms.assetid: 5f5e70dc-69f9-44b8-bc48-b5d51ac20d77
author: stevestein
ms.author: sstein
ms.openlocfilehash: 37b98bf0910cbbb4c2a1d7fe01f11d52703ec88c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646108"
---
# <a name="copy-columns-from-one-table-to-another-database-engine"></a><span data-ttu-id="2fa00-102">テーブル間での列のコピー (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="2fa00-102">Copy Columns from One Table to Another (Database Engine)</span></span>
  <span data-ttu-id="2fa00-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で列の定義のみ、または定義とデータの両方をコピーすることで、あるテーブルから別のテーブルに列をコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2fa00-103">This topic describes how to copy columns from one table to another, copying either just the column definition, or the definition and data in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2fa00-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2fa00-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2fa00-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2fa00-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2fa00-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2fa00-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2fa00-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2fa00-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2fa00-108">**列をコピーする方法:**</span><span class="sxs-lookup"><span data-stu-id="2fa00-108">**To coy columns, using:**</span></span>  
  
     [<span data-ttu-id="2fa00-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2fa00-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2fa00-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2fa00-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2fa00-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="2fa00-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2fa00-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2fa00-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="2fa00-113">別名データ型の列をデータベース間でコピーする場合、コピー先のデータベースで同じ別名データ型を使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2fa00-113">When you copy a column that has an alias data type from one database to another, the alias data type may not be available in the destination database.</span></span> <span data-ttu-id="2fa00-114">その場合、コピー先データベースで使用できる基本データ型の中で最も近いデータ型がその列に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="2fa00-114">In such a case, the column will be assigned the nearest matching base data type available in that database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2fa00-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2fa00-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2fa00-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="2fa00-116">Permissions</span></span>  
 <span data-ttu-id="2fa00-117">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2fa00-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2fa00-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2fa00-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a><span data-ttu-id="2fa00-119">テーブル間で列の定義をコピーするには</span><span class="sxs-lookup"><span data-stu-id="2fa00-119">To copy column definitions from one table to another</span></span>  
  
1.  <span data-ttu-id="2fa00-120">コピーする列を含むテーブルおよびコピー先のテーブルを右クリックして **[デザイン]** をクリックし、それらのテーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2fa00-120">Open the table with columns you want to copy and the one you want to copy into by right-clicking the tables, and then clicking **Design**.</span></span>  
  
2.  <span data-ttu-id="2fa00-121">コピーする列を含むテーブルのタブをクリックして、コピーする列を選択します。</span><span class="sxs-lookup"><span data-stu-id="2fa00-121">Click the tab for the table with the columns you want to copy and select those columns.</span></span>  
  
3.  <span data-ttu-id="2fa00-122">**[編集]** メニューの **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-122">From the **Edit** menu, click **Copy**.</span></span>  
  
4.  <span data-ttu-id="2fa00-123">列をコピーする先のテーブルのタブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-123">Click the tab for the table into which you want to copy the columns.</span></span>  
  
5.  <span data-ttu-id="2fa00-124">コピーした列を挿入する列を選択し、 **[編集]** メニューの **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-124">Select the column you want to follow the inserted columns and, from the **Edit** menu, click **Paste**.</span></span>  
  
#### <a name="to-copy-data-from-one-table-to-another"></a><span data-ttu-id="2fa00-125">テーブル間でデータをコピーするには</span><span class="sxs-lookup"><span data-stu-id="2fa00-125">To copy data from one table to another</span></span>  
  
1.  <span data-ttu-id="2fa00-126">前述の列定義のコピーの指示に従います。</span><span class="sxs-lookup"><span data-stu-id="2fa00-126">Follow the directions for copying column definitions above.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2fa00-127">テーブル間でデータのコピーを始める前に、コピー先の列のデータ型が、コピー元の列のデータ型と互換性があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2fa00-127">Before you begin to copy data from one table to another, make sure that the data types in the destination columns are compatible with the data types of the source columns</span></span>  
  
2.  <span data-ttu-id="2fa00-128">オブジェクト エクスプローラーで、**[ビュー]** ノードを右クリックし、**[新しいビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-128">In Object Explorer, right-click the **Views** node, and then click **New View**.</span></span>  
  
3.  <span data-ttu-id="2fa00-129">**[クエリ デザイナー]** メニューの **[クエリ タイプの変更]** をポイントし、 **[結果の挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-129">From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.</span></span>  
  
4.  <span data-ttu-id="2fa00-130">**[挿入先のテーブル選択]** ダイアログ ボックスで、データのコピー先のテーブルを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-130">In the **Choose Target Table for Insert Results** dialog box, select the table into which you want to copy the data, and then click **OK**.</span></span>  
  
     <span data-ttu-id="2fa00-131">同じテーブル内で行をコピーする場合は、コピー先テーブルと同じコピー元テーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="2fa00-131">If you are copying rows within a table, you can add the source table as a destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2fa00-132">**[クエリ デザイナー]** は、更新できるテーブルおよびビューを事前に判別できません。</span><span class="sxs-lookup"><span data-stu-id="2fa00-132">**Query Designer** cannot determine in advance which tables and views you can update.</span></span> <span data-ttu-id="2fa00-133">そのため、 **[挿入先のテーブル選択]** ダイアログ ボックスのテーブルのボックスには、クエリを実行するデータ接続で使用できるテーブルおよびビューがすべて表示されます。行をコピーできないテーブルおよびビューも表示されます。</span><span class="sxs-lookup"><span data-stu-id="2fa00-133">Therefore, the list of tables in the **Choose Target Table for Insert Results** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.</span></span>  
  
5.  <span data-ttu-id="2fa00-134">ダイアグラム ペインの本体を右クリックし、ショートカット メニューの **[テーブルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-134">Right-click in the body of the diagram pane and, from the shortcut menu, click **Add Table to Diagram**.</span></span>  
  
6.  <span data-ttu-id="2fa00-135">**[テーブルの追加]** ダイアログ ボックスで、データのコピー元の各テーブルを選択し、 **[追加]** をクリックし、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-135">In the **Add Table** dialog box, select each table from which you want to copy data, click **Add**, and then click **Close**.</span></span>  
  
     <span data-ttu-id="2fa00-136">テーブルが省略形でダイアグラム ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2fa00-136">The tables, in an abbreviated form, appear in the diagram pane.</span></span>  
  
7.  <span data-ttu-id="2fa00-137">省略形のテーブルで、データのコピー元の列のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-137">In the abbreviated tables, check the boxes for any columns from which you want to copy data.</span></span>  
  
8.  <span data-ttu-id="2fa00-138">抽出条件ペインの **[追加]** 列で、各コピー先の列に対してデータのコピー元の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="2fa00-138">In the criteria pane, in the **Append** column, for each target column choose a column from which you want to copy data.</span></span>  
  
9. <span data-ttu-id="2fa00-139">抽出条件ペインに検索条件を入力して、コピーする行を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fa00-139">Specify the rows to copy by entering search conditions in the criteria pane.</span></span> <span data-ttu-id="2fa00-140">詳細については、「[検索条件の指定 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa00-140">For details, see [Specify Search Conditions &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="2fa00-141">検索条件を指定しなかった場合は、コピー元テーブルのすべての行がコピー先テーブルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="2fa00-141">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
10. <span data-ttu-id="2fa00-142">概要情報をコピーする場合は、[**グループ化**] オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="2fa00-142">If you want to copy summary information, specify **Group By** options.</span></span> <span data-ttu-id="2fa00-143">詳細については、「[テーブルにあるすべての行の値の要約または集計 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa00-143">For details, see [Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md).</span></span>  
  
11. <span data-ttu-id="2fa00-144">**[SQL の実行]** ボタンをクリックしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="2fa00-144">Click the **Execute SQL button** to run the query.</span></span>  
  
     <span data-ttu-id="2fa00-145">結果の挿入クエリを実行しても、 [結果ペイン](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)に結果は表示されません。</span><span class="sxs-lookup"><span data-stu-id="2fa00-145">When you execute an insert results query, no results are reported in the [Results Pane](../../ssms/visual-db-tools/results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="2fa00-146">代わりに、コピーされた行数を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2fa00-146">Instead, a message appears indicating how many rows were copied.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2fa00-147">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2fa00-147">Using Transact-SQL</span></span>  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a><span data-ttu-id="2fa00-148">テーブル間で列の定義をコピーするには</span><span class="sxs-lookup"><span data-stu-id="2fa00-148">To copy column definitions from one table to another</span></span>  
  
1.  <span data-ttu-id="2fa00-149">Transact-SQL ステートメントを使用して、個々の列をあるテーブルから別の既存のテーブルにコピーすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2fa00-149">You cannot copy individual columns from one table to another existing table by using Transact-SQL statements.</span></span> <span data-ttu-id="2fa00-150">ただし、SELECT INTO を使用して、既定のファイル グループに新しいテーブルを作成し、クエリの結果得られた行をそのテーブルに挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="2fa00-150">However, you can create a new table in the default filegroup and inserts the resulting rows from the query into it by using SELECT INTO.</span></span> <span data-ttu-id="2fa00-151">詳細については、「[INTO 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-into-clause-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa00-151">For more information, see [INTO Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-into-clause-transact-sql).</span></span>  
  
#### <a name="to-copy-data-from-one-table-to-another"></a><span data-ttu-id="2fa00-152">テーブル間でデータをコピーするには</span><span class="sxs-lookup"><span data-stu-id="2fa00-152">To copy data from one table to another</span></span>  
  
1.  <span data-ttu-id="2fa00-153">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2fa00-153">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2fa00-154">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-154">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2fa00-155">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fa00-155">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.EmployeeSales  
    ( BusinessEntityID   varchar(11) NOT NULL,  
      SalesYTD money NOT NULL  
    );  
    GO  
    INSERT INTO dbo.EmployeeSales  
        SELECT BusinessEntityID, SalesYTD   
        FROM Sales.SalesPerson;  
    GO  
    ```  
  
  
