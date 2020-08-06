---
title: テーブルの計算列の指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, define
ms.assetid: 731a4576-09c1-47f0-a8f6-edd0b55679f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22e4df8d67b61e50383ffd8e33f982990ff3f2ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643718"
---
# <a name="specify-computed-columns-in-a-table"></a><span data-ttu-id="946d9-102">テーブルの計算列の指定</span><span class="sxs-lookup"><span data-stu-id="946d9-102">Specify Computed Columns in a Table</span></span>
  <span data-ttu-id="946d9-103">計算列は、PERSISTED とマークされていない限り、テーブルに物理的に保存されない仮想列です。</span><span class="sxs-lookup"><span data-stu-id="946d9-103">A computed column is a virtual column that is not physically stored in the table, unless the column is marked PERSISTED.</span></span> <span data-ttu-id="946d9-104">計算列の式は、他の列のデータを使用して値を計算し、それを自身の列に格納します。</span><span class="sxs-lookup"><span data-stu-id="946d9-104">A computed column expression can use data from other columns to calculate a value for the column to which it belongs.</span></span> <span data-ttu-id="946d9-105">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 上では、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して計算列に式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="946d9-105">You can specify an expression for a computed column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="946d9-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="946d9-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="946d9-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="946d9-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="946d9-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="946d9-108">Limitations and Restrictions</span></span>](#Limitations)  
  
     [<span data-ttu-id="946d9-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="946d9-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="946d9-110">**計算列を指定する方法:**</span><span class="sxs-lookup"><span data-stu-id="946d9-110">**To specify a computed column, using:**</span></span>  
  
     [<span data-ttu-id="946d9-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="946d9-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="946d9-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="946d9-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="946d9-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="946d9-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limitations"></a> <span data-ttu-id="946d9-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="946d9-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="946d9-115">計算列は、DEFAULT 制約定義または FOREIGN KEY 制約定義として使用したり、NOT NULL 制約定義と共に使用したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="946d9-115">A computed column cannot be used as a DEFAULT or FOREIGN KEY constraint definition or with a NOT NULL constraint definition.</span></span> <span data-ttu-id="946d9-116">ただし、計算列の値が決定的な式によって定義され、その結果のデータ型がインデックス列で可能な場合、計算列は、インデックスのキー列として、または任意の PRIMARY KEY 制約または UNIQUE 制約の一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="946d9-116">However, if the computed column value is defined by a deterministic expression and the data type of the result is allowed in index columns, a computed column can be used as a key column in an index or as part of any PRIMARY KEY or UNIQUE constraint.</span></span> <span data-ttu-id="946d9-117">たとえば、テーブルに整数型の列 a と b がある場合、計算列 a + b にはインデックスを作成できますが、計算列 a+DATEPART(dd, GETDATE()) にインデックスを作成することはできません。これは、この計算列の値が次以降の呼び出しで変更される可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="946d9-117">For example, if the table has integer columns a and b, the computed column a + b may be indexed, but computed column a + DATEPART(dd, GETDATE()) cannot be indexed, because the value might change in subsequent invocations.</span></span>  
  
-   <span data-ttu-id="946d9-118">計算列を INSERT ステートメントまたは UPDATE ステートメントの対象にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="946d9-118">A computed column cannot be the target of an INSERT or UPDATE statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="946d9-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="946d9-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="946d9-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="946d9-120">Permissions</span></span>  
 <span data-ttu-id="946d9-121">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="946d9-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="946d9-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="946d9-122">Using SQL Server Management Studio</span></span>  
  
###  <a name="to-add-a-new-computed-column"></a><a name="NewColumn"></a> <span data-ttu-id="946d9-123">新しい計算列を追加するには</span><span class="sxs-lookup"><span data-stu-id="946d9-123">To add a new computed column</span></span>  
  
1.  <span data-ttu-id="946d9-124">**オブジェクト エクスプローラー**で、新しい計算列を追加するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="946d9-124">In **Object Explorer**, expand the table for which you want to add the new computed column.</span></span> <span data-ttu-id="946d9-125">**[列]** を右クリックして **[新しい列]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-125">Right-click **Columns** and select **New Column**.</span></span>  
  
2.  <span data-ttu-id="946d9-126">列名を入力し、既定のデータ型 (`nchar`(10)) をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="946d9-126">Enter the column name and accept the default data type (`nchar`(10)).</span></span> <span data-ttu-id="946d9-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)] により、計算列のデータ型は、数式で指定された式のデータ型のうち優先順位が高い方になります。</span><span class="sxs-lookup"><span data-stu-id="946d9-127">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] determines the data type of the computed column by applying the rules of data type precedence to the expressions specified in the formula.</span></span> <span data-ttu-id="946d9-128">たとえば、式で `money` 型の列と `int` 型の列を参照する場合、`money` 型の方が優先順位が高いため、計算列はそのデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="946d9-128">For example, if the formula references a column of type `money` and a column of type `int`, the computed column will be of type `money` because that data type has the higher precedence.</span></span> <span data-ttu-id="946d9-129">詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-type-precedence-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="946d9-129">For more information, see [Data Type Precedence &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-type-precedence-transact-sql).</span></span>  
  
3.  <span data-ttu-id="946d9-130">**[列のプロパティ]** タブの **[計算列の指定]** プロパティを展開します。</span><span class="sxs-lookup"><span data-stu-id="946d9-130">In the **Column Properties** tab, expand the **Computed Column Specification** property.</span></span>  
  
4.  <span data-ttu-id="946d9-131">**[(数式)]** 子プロパティで、列の式を右側のグリッド セルに入力します。</span><span class="sxs-lookup"><span data-stu-id="946d9-131">In the **(Formula)** child property, enter the expression for this column in the grid cell to the right.</span></span> <span data-ttu-id="946d9-132">たとえば、 `SalesTotal` 列に `SubTotal+TaxAmt+Freight`という数式を入力した場合、テーブル内の各行のこれらの列の値が加算されます。</span><span class="sxs-lookup"><span data-stu-id="946d9-132">For example, in a `SalesTotal` column, the formula you enter might be `SubTotal+TaxAmt+Freight`, which adds the value in these columns for each row in the table.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="946d9-133">数式でデータ型が異なる 2 つの式を結合すると、データ型の優先順位の規則によって、優先順位の低いデータ型を優先順位の高いデータ型に変換することが指定されます。</span><span class="sxs-lookup"><span data-stu-id="946d9-133">When a formula combines two expressions of different data types, the rules for data type precedence specify that the data type with the lower precedence is converted to the data type with the higher precedence.</span></span> <span data-ttu-id="946d9-134">暗黙的な変換がサポートされていない場合は、「`Error validating the formula for column column_name.`」というエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="946d9-134">If the conversion is not a supported implicit conversion, the error "`Error validating the formula for column column_name.`" is returned.</span></span> <span data-ttu-id="946d9-135">データ型の競合を解決するには、CAST 関数または CONVERT 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="946d9-135">Use the CAST or CONVERT function to resolve the data type conflict.</span></span> <span data-ttu-id="946d9-136">たとえば、`nvarchar` 型の列を `int` 型の列と結合する場合は、この数式 `('Prod'+CONVERT(nvarchar(23),ProductID))` のように、整数型を `nvarchar` に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="946d9-136">For example, if a column of type `nvarchar` is combined with a column of type `int`, the integer type must be converted to `nvarchar` as shown in this formula `('Prod'+CONVERT(nvarchar(23),ProductID))`.</span></span> <span data-ttu-id="946d9-137">詳細については、「[CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="946d9-137">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
5.  <span data-ttu-id="946d9-138">**[Is Persisted]** 子プロパティのドロップダウンの **[はい]** または **[いいえ]** をクリックし、データを永続化するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="946d9-138">Indicate whether the data is persisted by choosing **Yes** or **No** from the drop-down for the **Is Persisted** child property.</span></span>  
  
6.  <span data-ttu-id="946d9-139">**[ファイル]** メニューの **[_<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-139">On the **File** menu, click **Save**_table name_.</span></span>  
  
#### <a name="to-add-a-computed-column-definition-to-an-existing-column"></a><span data-ttu-id="946d9-140">既存の列に計算列の定義を追加するには</span><span class="sxs-lookup"><span data-stu-id="946d9-140">To add a computed column definition to an existing column</span></span>  
  
1.  <span data-ttu-id="946d9-141">**オブジェクト エクスプローラー**で、変更する列が含まれているテーブルを右クリックし、 **[列]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="946d9-141">In **Object Explorer**, right-click the table with the column for which you want to change and expand the **Columns** folder.</span></span>  
  
2.  <span data-ttu-id="946d9-142">計算列の数式を指定する列を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-142">Right-click the column for which you want to specify a computed column formula and click **Delete**.</span></span> <span data-ttu-id="946d9-143">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-143">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="946d9-144">前の手順に従って、新しい列を追加し、計算列の数式を指定して、新しい計算列を追加します。</span><span class="sxs-lookup"><span data-stu-id="946d9-144">Add a new column and specify the computed column formula by following the previous procedure to add a new computed column.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="946d9-145">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="946d9-145">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-computed-column-when-creating-a-table"></a><span data-ttu-id="946d9-146">テーブルの作成時に計算列を追加するには</span><span class="sxs-lookup"><span data-stu-id="946d9-146">To add a computed column when creating a table</span></span>  
  
1.  <span data-ttu-id="946d9-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="946d9-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="946d9-148">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="946d9-149">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-149">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="946d9-150">この例では、 `QtyAvailable` 列の値と `UnitPrice` 列の値を乗算する計算列を含むテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="946d9-150">The example creates a table with a computed column that multiplies the value in the `QtyAvailable` column times the value in the `UnitPrice` column.</span></span>  
  
    ```  
    CREATE TABLE dbo.Products   
    (  
        ProductID int IDENTITY (1,1) NOT NULL  
      , QtyAvailable smallint  
      , UnitPrice money  
      , InventoryValue AS QtyAvailable * UnitPrice  
    );  
  
    -- Insert values into the table.  
    INSERT INTO dbo.Products (QtyAvailable, UnitPrice)  
    VALUES (25, 2.00), (10, 1.5);  
  
    -- Display the rows in the table.  
    SELECT ProductID, QtyAvailable, UnitPrice, InventoryValue  
    FROM dbo.Products;  
  
    ```  
  
#### <a name="to-add-a-new-computed-column-to-an-existing-table"></a><span data-ttu-id="946d9-151">既存のテーブルに新しい計算列を追加するには</span><span class="sxs-lookup"><span data-stu-id="946d9-151">To add a new computed column to an existing table</span></span>  
  
1.  <span data-ttu-id="946d9-152">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="946d9-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="946d9-153">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="946d9-154">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-154">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="946d9-155">次の例では、前の例で作成したテーブルに新しい列を追加します。</span><span class="sxs-lookup"><span data-stu-id="946d9-155">The following example adds a new column to the table created in the previous example.</span></span>  
  
    ```  
    ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.35);  
  
    ```  
  
#### <a name="to-change-an-existing-column-to-a-computed-column"></a><span data-ttu-id="946d9-156">既存の列を計算列に変更するには</span><span class="sxs-lookup"><span data-stu-id="946d9-156">To change an existing column to a computed column</span></span>  
  
1.  <span data-ttu-id="946d9-157">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="946d9-157">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="946d9-158">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-158">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="946d9-159">既存の列を計算列に変更するには、計算列を削除してから再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="946d9-159">To change an existing column to a computed column you must drop and re-create the computed column.</span></span> <span data-ttu-id="946d9-160">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="946d9-160">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="946d9-161">次の例では、前の例で追加した列を変更します。</span><span class="sxs-lookup"><span data-stu-id="946d9-161">The following example modifies the column added in the previous example.</span></span>  
  
    ```  
    ALTER TABLE dbo.Products DROP COLUMN RetailValue;  
    GO  
    ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.5);  
  
    ```  
  
     <span data-ttu-id="946d9-162">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="946d9-162">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
