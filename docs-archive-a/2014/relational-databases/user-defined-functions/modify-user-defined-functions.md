---
title: ユーザー定義関数の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 891c37b3-cb72-411f-9937-ee87e6d95f34
author: rothja
ms.author: jroth
ms.openlocfilehash: 1cf25fef91834e237f5cbaac26350220840830bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644861"
---
# <a name="modify-user-defined-functions"></a><span data-ttu-id="2b8bb-102">ユーザー定義関数の変更</span><span class="sxs-lookup"><span data-stu-id="2b8bb-102">Modify User-defined Functions</span></span>
  <span data-ttu-id="2b8bb-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してユーザー定義関数を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-103">You can modify user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2b8bb-104">以下に示す方法でユーザー定義関数を変更しても、関数の権限は変更されません。また、従属する関数、ストアド プロシージャ、またはトリガーにも影響はありません。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-104">Modifying user-defined functions as described below will not change the functions' permissions, nor will it affect any dependent functions, stored procedures, or triggers.</span></span>  
  
 <span data-ttu-id="2b8bb-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2b8bb-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2b8bb-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2b8bb-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2b8bb-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2b8bb-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2b8bb-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2b8bb-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2b8bb-109">**ユーザー定義関数を変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="2b8bb-109">**To modify a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="2b8bb-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2b8bb-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2b8bb-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2b8bb-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2b8bb-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="2b8bb-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2b8bb-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2b8bb-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="2b8bb-114">ALTER FUNCTION を使用して次の操作を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-114">ALTER FUNCTION cannot be used to perform any of the following actions:</span></span>  
  
-   <span data-ttu-id="2b8bb-115">スカラー値関数をテーブル値関数に変更したり、その逆の変更を行ったりする</span><span class="sxs-lookup"><span data-stu-id="2b8bb-115">Change a scalar-valued function to a table-valued function, or vice versa.</span></span>  
  
-   <span data-ttu-id="2b8bb-116">インライン関数を複数ステートメント関数に変更したり、その逆の変更を行ったりする</span><span class="sxs-lookup"><span data-stu-id="2b8bb-116">Change an inline function to a multistatement function, or vice versa.</span></span>  
  
-   <span data-ttu-id="2b8bb-117">Transact-SQL 関数を CLR 関数に変更したり、その逆の変更を行ったりする</span><span class="sxs-lookup"><span data-stu-id="2b8bb-117">Change a Transact-SQL function to a CLR function, or vice-versa.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2b8bb-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2b8bb-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2b8bb-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="2b8bb-119">Permissions</span></span>  
 <span data-ttu-id="2b8bb-120">関数またはスキーマに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-120">Requires ALTER permission on the function or on the schema.</span></span> <span data-ttu-id="2b8bb-121">関数でユーザー定義型が指定されている場合は、その型に対する EXECUTE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-121">If the function specifies a user-defined type, requires EXECUTE permission on the type.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2b8bb-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2b8bb-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-user-defined-function"></a><span data-ttu-id="2b8bb-123">ユーザー定義関数を変更するには</span><span class="sxs-lookup"><span data-stu-id="2b8bb-123">To modify a user-defined function</span></span>  
  
1.  <span data-ttu-id="2b8bb-124">変更する関数を含むデータベースの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-124">Click on the plus sign next to the database that contains the function you wish to modify.</span></span>  
  
2.  <span data-ttu-id="2b8bb-125">**Programmability** フォルダーの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-125">Click on the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="2b8bb-126">変更する次の関数を含むフォルダーの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-126">Click the plus sign next to the folder that contains the function you wish to modify:</span></span>  
  
    -   <span data-ttu-id="2b8bb-127">Table-valued Function</span><span class="sxs-lookup"><span data-stu-id="2b8bb-127">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="2b8bb-128">スカラー値関数</span><span class="sxs-lookup"><span data-stu-id="2b8bb-128">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="2b8bb-129">集計関数</span><span class="sxs-lookup"><span data-stu-id="2b8bb-129">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="2b8bb-130">変更する関数を右クリックし、 **[変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-130">Right-click the function you want to modify and select **Modify**.</span></span>  
  
5.  <span data-ttu-id="2b8bb-131">クエリ ウィンドウで、ALTER FUNCTION ステートメントに必要な変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-131">In the Query Window, make the necessary changes to the ALTER FUNCTION statement.</span></span>  
  
6.  <span data-ttu-id="2b8bb-132">**ファイル** メニューの **function_name**_の保存_をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-132">On the **File** menu, click **Save**_function_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2b8bb-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2b8bb-133">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-user-defined-function"></a><span data-ttu-id="2b8bb-134">ユーザー定義関数を変更するには</span><span class="sxs-lookup"><span data-stu-id="2b8bb-134">To modify a user-defined function</span></span>  
  
1.  <span data-ttu-id="2b8bb-135">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2b8bb-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2b8bb-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Scalar-Valued Function  
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetAccountingEndDate]()  
    RETURNS [datetime]   
    AS   
    BEGIN  
        RETURN DATEADD(millisecond, -2, CONVERT(datetime, '20040701', 112));  
    END;  
    ```  
  
    ```  
    -- Table-Valued Function   
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetContactInformation](@PersonID int)  
    RETURNS @retContactInformation TABLE   
    (  
        -- Columns returned by the function  
        [PersonID] int NOT NULL,   
        [FirstName] [nvarchar](50) NULL,   
        [LastName] [nvarchar](50) NULL,   
        [JobTitle] [nvarchar](50) NULL,  
        [BusinessEntityType] [nvarchar](50) NULL  
    )  
    AS   
    -- Returns the first name, last name, job title and business entity type for the specified contact.  
    -- Since a contact can serve multiple roles, more than one row may be returned.  
    BEGIN  
    IF @PersonID IS NOT NULL   
    BEGIN  
         IF EXISTS(SELECT * FROM [HumanResources].[Employee] e   
         WHERE e.[BusinessEntityID] = @PersonID)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, e.[JobTitle], 'Employee'  
              FROM [HumanResources].[Employee] AS e  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = e.[BusinessEntityID]  
              WHERE e.[BusinessEntityID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Purchasing].[Vendor] AS v  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Vendor Contact'   
              FROM [Purchasing].[Vendor] AS v  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Sales].[Store] AS s  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Store Contact'   
              FROM [Sales].[Store] AS s  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Person].[Person] AS p  
         INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
         WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, NULL, 'Consumer'   
              FROM [Person].[Person] AS p  
              INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
              WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL;   
         END  
    RETURN;  
    END;  
    ```  
  
 <span data-ttu-id="2b8bb-138">詳細については、「[ALTER FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-function-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b8bb-138">For more information, see [ALTER FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-function-transact-sql).</span></span>  
  
  
