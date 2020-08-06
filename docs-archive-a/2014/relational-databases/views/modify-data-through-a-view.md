---
title: ビューを使用したデータ変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- data modifications [SQL Server], views
- views [SQL Server], modifying data through
- modifying data [SQL Server], views
ms.assetid: 410e2812-4ebe-48b2-b95f-c7784f1c4336
author: stevestein
ms.author: sstein
ms.openlocfilehash: df1eb4a33d1d10e63363e52760dad805b20c0a8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631715"
---
# <a name="modify-data-through-a-view"></a><span data-ttu-id="e6923-102">ビューを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="e6923-102">Modify Data Through a View</span></span>
  <span data-ttu-id="e6923-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、基になるデータベース テーブルのデータを変更できます。</span><span class="sxs-lookup"><span data-stu-id="e6923-103">You can modify the data of an underlying base table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e6923-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e6923-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e6923-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e6923-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e6923-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e6923-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e6923-107">Security</span><span class="sxs-lookup"><span data-stu-id="e6923-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e6923-108">**以下を使用してビューを介してテーブル データを変更するには:**</span><span class="sxs-lookup"><span data-stu-id="e6923-108">**To modify table data through a view, using:**</span></span>  
  
     [<span data-ttu-id="e6923-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e6923-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e6923-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6923-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e6923-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="e6923-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e6923-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e6923-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e6923-113">「[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)」の '更新可能なビュー' セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6923-113">See the section 'Updatable Views' in [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e6923-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e6923-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e6923-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="e6923-115">Permissions</span></span>  
 <span data-ttu-id="e6923-116">実行する操作に応じて、対象のテーブルに対する UPDATE 権限、INSERT 権限、または DELETE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e6923-116">Requires UPDATE, INSERT, or DELETE permissions on the target table, depending on the action being performed.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e6923-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e6923-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-table-data-through-a-view"></a><span data-ttu-id="e6923-118">ビューを介してテーブル データを変更するには</span><span class="sxs-lookup"><span data-stu-id="e6923-118">To modify table data through a view</span></span>  
  
1.  <span data-ttu-id="e6923-119">**オブジェクト エクスプローラー**で、ビューを含むデータベースを展開し、 **[ビュー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="e6923-119">In **Object Explorer**, expand the database that contains the view and then expand **Views**.</span></span>  
  
2.  <span data-ttu-id="e6923-120">ビューを右クリックし、 **[上位 200 行の編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6923-120">Right-click the view and select **Edit Top 200 Rows**.</span></span>  
  
3.  <span data-ttu-id="e6923-121">場合により、変更対象の行を取得するために **SQL** ペインの SELECT ステートメントを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6923-121">You may need to modify the SELECT statement in the **SQL** pane to return the rows to be modified.</span></span>  
  
4.  <span data-ttu-id="e6923-122">**結果** ペインで、変更または削除する行を見つけます。</span><span class="sxs-lookup"><span data-stu-id="e6923-122">In the **Results** pane, locate the row to be changed or deleted.</span></span> <span data-ttu-id="e6923-123">行を削除するには、行を右クリックし、 **[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e6923-123">To delete the row, right-click the row and select **Delete**.</span></span> <span data-ttu-id="e6923-124">1 つ以上の列のデータを変更するには、目的の列のデータを変更します。</span><span class="sxs-lookup"><span data-stu-id="e6923-124">To change data in one or more columns, modify the data in the column.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e6923-125">ビューが複数のベース テーブルを参照している場合は、行を削除できません。</span><span class="sxs-lookup"><span data-stu-id="e6923-125">You cannot delete a row if the view references more than one base table.</span></span> <span data-ttu-id="e6923-126">1 つのベース テーブルに属している列のみを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="e6923-126">You can only update columns that belong to a single base table.</span></span>  
  
5.  <span data-ttu-id="e6923-127">行を挿入するには、行の最後までスクロールし、新しい値を挿入します。</span><span class="sxs-lookup"><span data-stu-id="e6923-127">To insert a row, scroll down to the end of the rows and insert the new values.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e6923-128">ビューが複数のベース テーブルを参照している場合は、行を挿入できません。</span><span class="sxs-lookup"><span data-stu-id="e6923-128">You cannot insert a row if the view references more than one base table.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e6923-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e6923-129">Using Transact-SQL</span></span>  
  
#### <a name="to-update-table-data-through-a-view"></a><span data-ttu-id="e6923-130">ビューを介してテーブル データを更新するには</span><span class="sxs-lookup"><span data-stu-id="e6923-130">To update table data through a view</span></span>  
  
1.  <span data-ttu-id="e6923-131">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6923-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6923-132">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6923-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e6923-133">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6923-133">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e6923-134">この例では、ビュー `StartDate` の列を参照することによって特定の従業員の `EndDate` 列および `HumanResources.vEmployeeDepartmentHistory`列の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="e6923-134">This example changes the value in the `StartDate` and `EndDate` columns for a specific employee by referencing columns in the view `HumanResources.vEmployeeDepartmentHistory`.</span></span> <span data-ttu-id="e6923-135">このビューは、2 つのテーブルの値を返します。</span><span class="sxs-lookup"><span data-stu-id="e6923-135">This view returns values from two tables.</span></span> <span data-ttu-id="e6923-136">変更対象の列の所属先は 1 つのベース テーブルであるため、このステートメントは成功します。</span><span class="sxs-lookup"><span data-stu-id="e6923-136">This statement succeeds because the columns being modified are from only one of the base tables.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    UPDATE HumanResources.vEmployeeDepartmentHistory  
    SET StartDate = '20110203', EndDate = GETDATE()   
    WHERE LastName = N'Smith' AND FirstName = 'Samantha';   
    GO  
    ```  
  
 <span data-ttu-id="e6923-137">詳細については、「[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6923-137">For more information, see [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql).</span></span>  
  
#### <a name="to-insert-table-data-through-a-view"></a><span data-ttu-id="e6923-138">ビューを介してテーブル データを挿入するには</span><span class="sxs-lookup"><span data-stu-id="e6923-138">To insert table data through a view</span></span>  
  
1.  <span data-ttu-id="e6923-139">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6923-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6923-140">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6923-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e6923-141">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6923-141">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e6923-142">この例では、ビュー `HumanResouces.Department` の該当する列を指定することによって、新しい行をベース テーブル `HumanResources.vEmployeeDepartmentHistory`に挿入します。</span><span class="sxs-lookup"><span data-stu-id="e6923-142">The example inserts a new row into the base table `HumanResouces.Department` by specifying the relevant columns from the view `HumanResources.vEmployeeDepartmentHistory`.</span></span> <span data-ttu-id="e6923-143">1 つのベース テーブルの列のみが指定され、ベース テーブルの他の列は既定値を持つため、このステートメントは成功します。</span><span class="sxs-lookup"><span data-stu-id="e6923-143">The statement succeeds because only columns from a single base table are specified and the other columns in the base table have default values.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    INSERT INTO HumanResources.vEmployeeDepartmentHistory (Department, GroupName)   
    VALUES ('MyDepartment', 'MyGroup');   
    GO  
    ```  
  
 <span data-ttu-id="e6923-144">詳細については、「[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6923-144">For more information, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).</span></span>  
  
  
