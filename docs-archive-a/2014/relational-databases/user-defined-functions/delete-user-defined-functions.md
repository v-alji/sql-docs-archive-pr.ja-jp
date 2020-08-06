---
title: ユーザー定義関数の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: db1d668a-23b7-4757-a9c5-1bd848ba7f6d
author: rothja
ms.author: jroth
ms.openlocfilehash: e5f6b2b306c4fe8db08b088d9607cfb19ab0f25e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644864"
---
# <a name="delete-user-defined-functions"></a><span data-ttu-id="565f6-102">ユーザー定義関数の削除</span><span class="sxs-lookup"><span data-stu-id="565f6-102">Delete User-defined Functions</span></span>
  <span data-ttu-id="565f6-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または  を使用してユーザー定義関数を削除できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="565f6-103">You can delete (drop) user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="565f6-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="565f6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="565f6-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="565f6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="565f6-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="565f6-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="565f6-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="565f6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="565f6-108">**ユーザー定義関数を削除するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="565f6-108">**To delete a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="565f6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="565f6-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="565f6-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="565f6-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="565f6-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="565f6-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="565f6-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="565f6-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="565f6-113">データベース内に、この関数を参照し SCHEMABINDING を使って作成された Transact-SQL 関数またはビューがある場合、または、この関数を参照する計算列、CHECK 制約、DEFAULT 制約がある場合、関数は削除できません。</span><span class="sxs-lookup"><span data-stu-id="565f6-113">You will not be able to delete the function if there are Transact-SQL functions or views in the database that reference this function and were created by using SCHEMABINDING, or if there are computed columns, CHECK constraints, or DEFAULT constraints that reference the function.</span></span>  
  
-   <span data-ttu-id="565f6-114">この関数を参照し、インデックスが作成された計算列がある場合、関数の削除はできません。</span><span class="sxs-lookup"><span data-stu-id="565f6-114">You will not be able to delete the function if there are computed columns that reference this function and have been indexed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="565f6-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="565f6-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="565f6-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="565f6-116">Permissions</span></span>  
 <span data-ttu-id="565f6-117">関数が属しているスキーマに対する ALTER 権限、または関数に対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="565f6-117">Requires ALTER permission on the schema to which the function belongs, or CONTROL permission on the function.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="565f6-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="565f6-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-user-defined-function"></a><span data-ttu-id="565f6-119">ユーザー定義関数を削除するには</span><span class="sxs-lookup"><span data-stu-id="565f6-119">To delete a user-defined function</span></span>  
  
1.  <span data-ttu-id="565f6-120">変更する関数を含むデータベースの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="565f6-120">Click on the plus sign next to the database that contains the function you wish to modify.</span></span>  
  
2.  <span data-ttu-id="565f6-121">**Programmability** フォルダーの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="565f6-121">Click on the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="565f6-122">変更する次の関数を含むフォルダーの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="565f6-122">Click the plus sign next to the folder that contains the function you wish to modify:</span></span>  
  
    -   <span data-ttu-id="565f6-123">Table-valued Function</span><span class="sxs-lookup"><span data-stu-id="565f6-123">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="565f6-124">スカラー値関数</span><span class="sxs-lookup"><span data-stu-id="565f6-124">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="565f6-125">集計関数</span><span class="sxs-lookup"><span data-stu-id="565f6-125">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="565f6-126">削除する関数を右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="565f6-126">Right-click the function you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="565f6-127">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="565f6-127">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="565f6-128">[**オブジェクトの削除**] ダイアログボックスの [**依存関係の表示**] をクリックして、[ _function_name_の**依存関係**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="565f6-128">Click **Show Dependencies** in the **Delete Object** dialog box to open the _function_name_**Dependencies** dialog box.</span></span> <span data-ttu-id="565f6-129">関数に依存するすべてのオブジェクトと、関数が依存するすべてのオブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="565f6-129">This will show all of the objects that depend on the function and all of the objects on which the function depends.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="565f6-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="565f6-130">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-user-defined-function"></a><span data-ttu-id="565f6-131">ユーザー定義関数を削除するには</span><span class="sxs-lookup"><span data-stu-id="565f6-131">To delete a user-defined function</span></span>  
  
1.  <span data-ttu-id="565f6-132">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="565f6-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="565f6-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="565f6-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="565f6-134">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="565f6-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates function called "Sales.ufn_SalesByStore"  
    USE AdventureWorks2012;  
    GO  
    CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
    RETURNS TABLE  
    AS  
    RETURN   
    (  
        SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
        FROM Production.Product AS P   
        JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
        JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
        JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
        WHERE C.StoreID = @storeid  
        GROUP BY P.ProductID, P.Name  
    );  
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- determines if function exists in database  
    IF OBJECT_ID (N'Sales.fn_SalesByStore', N'IF') IS NOT NULL  
    -- deletes function  
        DROP FUNCTION Sales.fn_SalesByStore;  
    GO  
    ```  
  
 <span data-ttu-id="565f6-135">詳細については、「[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="565f6-135">For more information, see [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).</span></span>  
  
  
