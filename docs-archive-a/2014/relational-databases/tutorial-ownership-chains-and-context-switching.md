---
title: 'チュートリアル : 所有権の継承とコンテキストの切り替え | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- context switching [SQL Server], tutorials
- ownership chains [SQL Server]
ms.assetid: db5d4cc3-5fc5-4cf5-afc1-8d4edc1d512b
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e9072a68dd3179e5900fda06d4fea58b484a37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634366"
---
# <a name="tutorial-ownership-chains-and-context-switching"></a><span data-ttu-id="d2a30-102">Tutorial: Ownership Chains and Context Switching</span><span class="sxs-lookup"><span data-stu-id="d2a30-102">Tutorial: Ownership Chains and Context Switching</span></span>
  <span data-ttu-id="d2a30-103">このチュートリアルでは、1 つのシナリオを使用して、所有権の継承とユーザー コンテキストの切り替えに関係する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のセキュリティ概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-103">This tutorial uses a scenario to illustrate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] security concepts involving ownership chains and user context switching.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2a30-104">このチュートリアルのコードを実行するには、混合モードのセキュリティが構成されていることと、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースがインストールされていることが条件となります。</span><span class="sxs-lookup"><span data-stu-id="d2a30-104">To run the code in this tutorial you must have both Mixed Mode security configured and the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database installed.</span></span> <span data-ttu-id="d2a30-105">混合モードのセキュリティの詳細については、「 [認証モードの選択](security/choose-an-authentication-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a30-105">For more information about Mixed Mode security, see [Choose an Authentication Mode](security/choose-an-authentication-mode.md).</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="d2a30-106">シナリオ</span><span class="sxs-lookup"><span data-stu-id="d2a30-106">Scenario</span></span>  
 <span data-ttu-id="d2a30-107">このシナリオでは、2 人のユーザーが、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースに格納されている購買発注データにアクセスするためのアカウントを必要としていることを想定します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-107">In this scenario, two users need accounts to access purchase order data stored in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="d2a30-108">要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d2a30-108">The requirements are as follows:</span></span>  
  
-   <span data-ttu-id="d2a30-109">最初のアカウント (TestManagerUser) では、すべての購買注文のすべての詳細を確認できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2a30-109">The first account (TestManagerUser) must be able to see all details in every purchase order.</span></span>  
  
-   <span data-ttu-id="d2a30-110">2 番目のアカウント (TestEmployeeUser) では、配送の一部が受領された場合の品目に関して、発注番号、発注日、出荷日、製品 ID 番号、発注品目数と受領品目数を、購買注文ごとに発注番号で確認できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2a30-110">The second account (TestEmployeeUser) must be able to see the purchase order number, order date, shipping date, product ID numbers, and the ordered and received items per purchase order, by purchase order number, for items where partial shipments have been received.</span></span>  
  
-   <span data-ttu-id="d2a30-111">他のすべてのアカウントでは、各自の現在の権限を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2a30-111">All other accounts must retain their current permissions.</span></span>  
  
 <span data-ttu-id="d2a30-112">このシナリオの要件を満たすため、ここでは例を次のように 4 分割して、所有権の継承とコンテキストの切り替えの各概念を示します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-112">To fulfill the requirements of this scenario, the example is broken into four parts that demonstrate the concepts of ownership chains and context switching:</span></span>  
  
1.  <span data-ttu-id="d2a30-113">環境を構成する。</span><span class="sxs-lookup"><span data-stu-id="d2a30-113">Configuring the environment.</span></span>  
  
2.  <span data-ttu-id="d2a30-114">購買注文によってデータにアクセスするストアド プロシージャを作成する。</span><span class="sxs-lookup"><span data-stu-id="d2a30-114">Creating a stored procedure to access data by purchase order.</span></span>  
  
3.  <span data-ttu-id="d2a30-115">ストアド プロシージャからデータにアクセスする。</span><span class="sxs-lookup"><span data-stu-id="d2a30-115">Accessing the data through the stored procedure.</span></span>  
  
4.  <span data-ttu-id="d2a30-116">環境をリセットする。</span><span class="sxs-lookup"><span data-stu-id="d2a30-116">Resetting the environment.</span></span>  
  
 <span data-ttu-id="d2a30-117">以下で、この例の各コード ブロックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-117">Each code block in this example is explained in line.</span></span> <span data-ttu-id="d2a30-118">完全なサンプル コードをコピーするには、このチュートリアルの最後の「 [完全なサンプル コード](#CompleteExample) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a30-118">To copy the complete example, see [Complete Example](#CompleteExample) at the end of this tutorial.</span></span>  
  
## <a name="1-configure-the-environment"></a><span data-ttu-id="d2a30-119">1.環境を構成する</span><span class="sxs-lookup"><span data-stu-id="d2a30-119">1. Configure the Environment</span></span>  
 <span data-ttu-id="d2a30-120">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]と次のコードを使用して `AdventureWorks2012` データベースを開き、ステートメントを使用し `CURRENT_USER` [!INCLUDE[tsql](../includes/tsql-md.md)] て、dbo ユーザーがコンテキストとして表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-120">Use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and the following code to open the `AdventureWorks2012` database, and use the `CURRENT_USER` [!INCLUDE[tsql](../includes/tsql-md.md)] statement to check that the dbo user is displayed as the context.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
```  
  
 <span data-ttu-id="d2a30-121">CURRENT_USER ステートメントの詳細については、「[CURRENT_USER (Transact-SQL)](/sql/t-sql/functions/current-user-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a30-121">For more information about the CURRENT_USER statement, see [CURRENT_USER &#40;Transact-SQL&#41;](/sql/t-sql/functions/current-user-transact-sql).</span></span>  
  
 <span data-ttu-id="d2a30-122">次のコードを dbo ユーザーとして実行し、サーバー上と [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース内に 2 ユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-122">Use this code as the dbo user to create two users on the server and in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
CREATE LOGIN TestManagerUser   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khx';  
GO  
CREATE USER TestManagerUser   
   FOR LOGIN TestManagerUser  
   WITH DEFAULT_SCHEMA = Purchasing;  
GO   
  
CREATE LOGIN TestEmployeeUser  
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
GO  
CREATE USER TestEmployeeUser   
   FOR LOGIN TestEmployeeUser;  
GO   
```  
  
 <span data-ttu-id="d2a30-123">CREATE_USER ステートメントの詳細については、「[CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a30-123">For more information about the CREATE USER statement, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span> <span data-ttu-id="d2a30-124">CREATE_LOGIN ステートメントの詳細については、「[CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a30-124">For more information about the CREATE LOGIN statement, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
 <span data-ttu-id="d2a30-125">次のコードを実行し、 `Purchasing` スキーマの所有権を `TestManagerUser` アカウントに変更します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-125">Use the following code to change the ownership of the `Purchasing` schema to the `TestManagerUser` account.</span></span> <span data-ttu-id="d2a30-126">所有権を与えられたアカウントでは、 `SELECT` 権限や `INSERT` 権限などすべてのデータ操作言語 (DML) のアクセス権限を、中のオブジェクトに対し使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2a30-126">This allows that account to use all Data Manipulation Language (DML) statement access (such as `SELECT` and `INSERT` permissions) on the objects it contains.</span></span> <span data-ttu-id="d2a30-127">`TestManagerUser` にもストアド プロシージャを作成する権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="d2a30-127">`TestManagerUser` is also granted the ability to create stored procedures.</span></span>  
  
```  
/* Change owner of the Purchasing Schema to TestManagerUser */  
ALTER AUTHORIZATION   
   ON SCHEMA::Purchasing   
   TO TestManagerUser;  
GO  
  
GRANT CREATE PROCEDURE   
   TO TestManagerUser   
   WITH GRANT OPTION;  
GO  
```  
  
 <span data-ttu-id="d2a30-128">GRANT ステートメントの詳細については、「[GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a30-128">For more information about the GRANT statement, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span> <span data-ttu-id="d2a30-129">ストアド プロシージャの詳細については、「[ストアド プロシージャ (データベース エンジン)](stored-procedures/stored-procedures-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a30-129">For more information about stored procedures, see [Stored Procedures &#40;Database Engine&#41;](stored-procedures/stored-procedures-database-engine.md).</span></span> <span data-ttu-id="d2a30-130">すべてのアクセス許可のポスターについ [!INCLUDE[ssDE](../includes/ssde-md.md)] ては、「」を参照してください [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf) 。</span><span class="sxs-lookup"><span data-stu-id="d2a30-130">For a poster of all [!INCLUDE[ssDE](../includes/ssde-md.md)] permissions, see [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf).</span></span>  
  
## <a name="2-create-a-stored-procedure-to-access-data"></a><span data-ttu-id="d2a30-131">2.データにアクセスするストアド プロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="d2a30-131">2. Create a Stored Procedure to Access Data</span></span>  
 <span data-ttu-id="d2a30-132">データベース内でコンテキストを切り替えるには、EXECUTE AS ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-132">To switch context within a database, use the EXECUTE AS statement.</span></span> <span data-ttu-id="d2a30-133">EXECUTE AS を使用するには IMPERSONATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d2a30-133">EXECUTE AS requires IMPERSONATE permissions.</span></span>  
  
 <span data-ttu-id="d2a30-134">次のコードでは、 `EXECUTE AS` ステートメントによりコンテキストを `TestManagerUser` に変更し、 `TestEmployeeUser`に必要とされるデータのみを表示するストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-134">Use the `EXECUTE AS` statement in the following code to change the context to `TestManagerUser` and create a stored procedure showing only the data required by `TestEmployeeUser`.</span></span> <span data-ttu-id="d2a30-135">要件を満たすには、ストアド プロシージャでは発注番号を表す変数を 1 つ受け取ります。財務情報は表示せず、WHERE 句によって結果を一部配送のみに限定します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-135">To satisfy the requirements, the stored procedure accepts one variable for the purchase order number and does not display financial information, and the WHERE clause limits the results to partial shipments.</span></span>  
  
```  
EXECUTE AS LOGIN = 'TestManagerUser'  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
  
/* Note: The user that calls the EXECUTE AS statement must have IMPERSONATE permissions on the target principal */  
CREATE PROCEDURE usp_ShowWaitingItems @ProductID int  
AS  
BEGIN   
   SELECT a.PurchaseOrderID, a.OrderDate, a.ShipDate  
      , b.ProductID, b.OrderQty, b.ReceivedQty  
   FROM Purchasing.PurchaseOrderHeader a  
      INNER JOIN Purchasing.PurchaseOrderDetail b  
         ON a.PurchaseOrderID = b.PurchaseOrderID  
   WHERE b.OrderQty > b.ReceivedQty  
      AND @ProductID = b.ProductID  
   ORDER BY b.ProductID ASC  
END  
GO  
```  
  
 <span data-ttu-id="d2a30-136">この時点では、 `TestEmployeeUser` はどのデータベース オブジェクトにもアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="d2a30-136">Currently `TestEmployeeUser` does not have access to any database objects.</span></span> <span data-ttu-id="d2a30-137">コンテキストは引き続き `TestManagerUser` です。次のコードを実行し、ストアド プロシージャを介して  ユーザー アカウントがベース テーブル情報をクエリできるようにします。</span><span class="sxs-lookup"><span data-stu-id="d2a30-137">The following code (still in the `TestManagerUser` context) grants the user account the ability to query base-table information through the stored procedure.</span></span>  
  
```  
GRANT EXECUTE  
   ON OBJECT::Purchasing.usp_ShowWaitingItems  
   TO TestEmployeeUser;  
GO  
```  
  
 <span data-ttu-id="d2a30-138">`Purchasing` は既定では `TestManagerUser` スキーマに割り当てられるため、スキーマが明示的に指定されていない場合でも、ストアド プロシージャは `Purchasing` スキーマの一部です。</span><span class="sxs-lookup"><span data-stu-id="d2a30-138">The stored procedure is part of the `Purchasing` schema, even though no schema was explicitly specified, because `TestManagerUser` is assigned by default to the `Purchasing` schema.</span></span> <span data-ttu-id="d2a30-139">次のコードに示すように、システム カタログ情報を使用してオブジェクトを特定できます。</span><span class="sxs-lookup"><span data-stu-id="d2a30-139">You can use system catalog information to locate objects, as shown in the following code.</span></span>  
  
```  
SELECT a.name AS 'Schema'  
   , b.name AS 'Object Name'  
   , b.type AS 'Object Type'  
FROM sys.schemas a  
   INNER JOIN sys.objects b  
      ON a.schema_id = b.schema_id   
WHERE b.name = 'usp_ShowWaitingItems';  
GO  
```  
  
 <span data-ttu-id="d2a30-140">例のこの部分が完了すると、コードでは `REVERT` ステートメントによってコンテキストが切り替えられ、コンテキストは dbo に戻ります。</span><span class="sxs-lookup"><span data-stu-id="d2a30-140">With this section of the example completed, the code switches context back to dbo using the `REVERT` statement.</span></span>  
  
```  
REVERT;  
GO  
```  
  
 <span data-ttu-id="d2a30-141">REVERT ステートメントの詳細については、「[REVERT (Transact-SQL)](/sql/t-sql/statements/revert-transact-sql)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a30-141">For more information about the REVERT statement, see [REVERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/revert-transact-sql).</span></span>  
  
## <a name="3-access-data-through-the-stored-procedure"></a><span data-ttu-id="d2a30-142">3.ストアド プロシージャからデータにアクセスする</span><span class="sxs-lookup"><span data-stu-id="d2a30-142">3. Access Data Through the Stored Procedure</span></span>  
 <span data-ttu-id="d2a30-143">`TestEmployeeUser` は、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースのオブジェクトに対し、ログイン権限と public データベース ロールに割り当てられた権限だけを持ちます。</span><span class="sxs-lookup"><span data-stu-id="d2a30-143">`TestEmployeeUser` has no permissions on the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database objects other than a login and the rights assigned to the public database role.</span></span> <span data-ttu-id="d2a30-144">`TestEmployeeUser` がベース テーブルにアクセスしようとすると、次のコードによりエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="d2a30-144">The following code returns an error when `TestEmployeeUser` attempts to access base tables.</span></span>  
  
```  
EXECUTE AS LOGIN = 'TestEmployeeUser'  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
/* This won't work */  
SELECT *  
FROM Purchasing.PurchaseOrderHeader;  
GO  
SELECT *  
FROM Purchasing.PurchaseOrderDetail;  
GO  
```  
  
 <span data-ttu-id="d2a30-145">前のセクションで作成したストアド プロシージャで参照されるオブジェクトは、 `TestManagerUser` スキーマの所有権により `Purchasing` の所有となります。したがって、 `TestEmployeeUser` はストアド プロシージャを介してベース テーブルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d2a30-145">Because the objects referenced by the stored procedure created in the last section are owned by `TestManagerUser` by virtue of the `Purchasing` schema ownership, `TestEmployeeUser` can access the base tables through the stored procedure.</span></span> <span data-ttu-id="d2a30-146">次のコードでは、引き続き `TestEmployeeUser` をコンテキストとし、購買注文 952 をパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-146">The following code, still using the `TestEmployeeUser` context, passes purchase order 952 as a parameter.</span></span>  
  
```  
EXEC Purchasing.usp_ShowWaitingItems 952  
GO  
```  
  
## <a name="4-reset-the-environment"></a><span data-ttu-id="d2a30-147">4.環境をリセットする</span><span class="sxs-lookup"><span data-stu-id="d2a30-147">4. Reset the Environment</span></span>  
 <span data-ttu-id="d2a30-148">次のコードでは、 `REVERT` コマンドにより現在のアカウントのコンテキストを `dbo`に戻し、環境をリセットします。</span><span class="sxs-lookup"><span data-stu-id="d2a30-148">The following code uses the `REVERT` command to return the context of the current account to `dbo`, and then resets the environment.</span></span>  
  
```  
REVERT;  
GO  
ALTER AUTHORIZATION   
ON SCHEMA::Purchasing TO dbo;  
GO  
DROP PROCEDURE Purchasing.usp_ShowWaitingItems;  
GO  
DROP USER TestEmployeeUser;  
GO  
DROP USER TestManagerUser;  
GO  
DROP LOGIN TestEmployeeUser;  
GO  
DROP LOGIN TestManagerUser;  
GO  
```  
  
##  <a name="complete-example"></a><a name="CompleteExample"></a><span data-ttu-id="d2a30-149">コード例全体</span><span class="sxs-lookup"><span data-stu-id="d2a30-149">Complete Example</span></span>  
 <span data-ttu-id="d2a30-150">次に、完全なサンプル コードを示します。</span><span class="sxs-lookup"><span data-stu-id="d2a30-150">This section displays the complete example code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2a30-151">`TestEmployeeUser` はベース テーブルから選択することができないため、2 つのエラーが発生することが予測されますが、このコードには含まれていません。</span><span class="sxs-lookup"><span data-stu-id="d2a30-151">This code does not include the two expected errors that demonstrate the inability of `TestEmployeeUser` to select from base tables.</span></span>  
  
```  
/*   
Script:       UserContextTutorial.sql  
Author:       Microsoft  
Last Updated: Books Online  
Conditions:   Execute as DBO or sysadmin in the AdventureWorks database  
Section 1:    Configure the Environment   
*/  
USE AdventureWorks2012;  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
/* Create server and database users */  
CREATE LOGIN TestManagerUser   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khx';  
  
GO  
  
CREATE USER TestManagerUser   
   FOR LOGIN TestManagerUser  
   WITH DEFAULT_SCHEMA = Purchasing;  
GO   
  
CREATE LOGIN TestEmployeeUser  
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
GO  
CREATE USER TestEmployeeUser   
   FOR LOGIN TestEmployeeUser;  
GO   
  
/* Change owner of the Purchasing Schema to TestManagerUser */  
ALTER AUTHORIZATION   
   ON SCHEMA::Purchasing   
   TO TestManagerUser;  
GO  
  
GRANT CREATE PROCEDURE   
   TO TestManagerUser   
   WITH GRANT OPTION;  
GO  
  
/*   
Section 2: Switch Context and Create Objects  
*/  
EXECUTE AS LOGIN = 'TestManagerUser';  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
  
/* Note: The user that calls the EXECUTE AS statement must have IMPERSONATE permissions on the target principal */  
CREATE PROCEDURE usp_ShowWaitingItems @ProductID int  
AS  
BEGIN   
   SELECT a.PurchaseOrderID, a.OrderDate, a.ShipDate  
      , b.ProductID, b.OrderQty, b.ReceivedQty  
   FROM Purchasing.PurchaseOrderHeader AS a  
      INNER JOIN Purchasing.PurchaseOrderDetail AS b  
         ON a.PurchaseOrderID = b.PurchaseOrderID  
   WHERE b.OrderQty > b.ReceivedQty  
      AND @ProductID = b.ProductID  
   ORDER BY b.ProductID ASC  
END;  
GO  
  
/* Give the employee the ability to run the procedure */  
GRANT EXECUTE   
   ON OBJECT::Purchasing.usp_ShowWaitingItems  
   TO TestEmployeeUser;  
GO   
  
/* Notice that the stored procedure is located in the Purchasing   
schema. This also demonstrates system catalogs */  
SELECT a.name AS 'Schema'  
   , b.name AS 'Object Name'  
   , b.type AS 'Object Type'  
FROM sys.schemas AS a  
   INNER JOIN sys.objects AS b  
      ON a.schema_id = b.schema_id   
WHERE b.name = 'usp_ShowWaitingItems';  
GO  
  
/* Go back to being the dbo user */  
REVERT;  
GO  
  
/*  
Section 3: Switch Context and Observe Security   
*/  
EXECUTE AS LOGIN = 'TestEmployeeUser';  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
EXEC Purchasing.usp_ShowWaitingItems 952;  
GO  
  
/*   
Section 4: Clean Up Example  
*/  
REVERT;  
GO  
ALTER AUTHORIZATION   
ON SCHEMA::Purchasing TO dbo;  
GO  
DROP PROCEDURE Purchasing.usp_ShowWaitingItems;  
GO  
DROP USER TestEmployeeUser;  
GO  
DROP USER TestManagerUser;  
GO  
DROP LOGIN TestEmployeeUser;  
GO  
DROP LOGIN TestManagerUser;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2a30-152">参照</span><span class="sxs-lookup"><span data-stu-id="d2a30-152">See Also</span></span>  
 [<span data-ttu-id="d2a30-153">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="d2a30-153">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
