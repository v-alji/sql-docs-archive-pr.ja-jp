---
title: ストアド プロシージャの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- new stored procedures
- stored procedures [SQL Server], creating
- creating stored procedures
ms.assetid: 76e8a6ba-1381-4620-b356-4311e1331ca7
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6781840e6a6c84773f40a6cd0557ccb79b676eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644362"
---
# <a name="create-a-stored-procedure"></a><span data-ttu-id="96fcc-102">ストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="96fcc-102">Create a Stored Procedure</span></span>
  <span data-ttu-id="96fcc-103">このトピックでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の CREATE PROCEDURE ステートメントを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-103">This topic describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE PROCEDURE statement.</span></span>  
  
##  <a name="Top"></a>   
-   <span data-ttu-id="96fcc-104">**作業を開始する準備:** [アクセス許可](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="96fcc-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="96fcc-105">**プロシージャを作成するには次を使用します:** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="96fcc-105">**To create a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="96fcc-106">Permissions</span><span class="sxs-lookup"><span data-stu-id="96fcc-106">Permissions</span></span>  
 <span data-ttu-id="96fcc-107">データベースの CREATE PROCEDURE 権限と、プロシージャを作成するスキーマに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="96fcc-107">Requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
##  <a name="how-to-create-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="96fcc-108">ストアド プロシージャを作成する方法</span><span class="sxs-lookup"><span data-stu-id="96fcc-108">How to Create a Stored Procedure</span></span>  
 <span data-ttu-id="96fcc-109">次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-109">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="96fcc-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="96fcc-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="96fcc-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="96fcc-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="96fcc-112">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="96fcc-112">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="96fcc-113">**オブジェクト エクスプローラーでプロシージャを作成するには**</span><span class="sxs-lookup"><span data-stu-id="96fcc-113">**To create a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="96fcc-114">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-114">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="96fcc-115">**[データベース]** を展開し、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを展開して、 **[プログラミング]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-115">Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="96fcc-116">**[ストアド プロシージャ]** を右クリックし、 **[新しいストアド プロシージャ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96fcc-116">Right-click **Stored Procedures**, and then click **New Stored Procedure**.</span></span>  
  
4.  <span data-ttu-id="96fcc-117">**[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96fcc-117">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
5.  <span data-ttu-id="96fcc-118">**[テンプレート パラメーターの値の指定]** ダイアログ ボックスで、各パラメーターに次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-118">In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.</span></span>  
  
    |<span data-ttu-id="96fcc-119">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96fcc-119">Parameter</span></span>|<span data-ttu-id="96fcc-120">値</span><span class="sxs-lookup"><span data-stu-id="96fcc-120">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="96fcc-121">Author</span><span class="sxs-lookup"><span data-stu-id="96fcc-121">Author</span></span>|<span data-ttu-id="96fcc-122">*名前*</span><span class="sxs-lookup"><span data-stu-id="96fcc-122">*Your name*</span></span>|  
    |<span data-ttu-id="96fcc-123">Create Date</span><span class="sxs-lookup"><span data-stu-id="96fcc-123">Create Date</span></span>|<span data-ttu-id="96fcc-124">*今日の日付*</span><span class="sxs-lookup"><span data-stu-id="96fcc-124">*Today's date*</span></span>|  
    |<span data-ttu-id="96fcc-125">説明</span><span class="sxs-lookup"><span data-stu-id="96fcc-125">Description</span></span>|<span data-ttu-id="96fcc-126">従業員のデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="96fcc-126">Returns employee data.</span></span>|  
    |<span data-ttu-id="96fcc-127">[Procedure_name]</span><span class="sxs-lookup"><span data-stu-id="96fcc-127">Procedure_name</span></span>|<span data-ttu-id="96fcc-128">HumanResources.uspGetEmployeesTest</span><span class="sxs-lookup"><span data-stu-id="96fcc-128">HumanResources.uspGetEmployeesTest</span></span>|  
    |@Param1|@LastName|  
    |@Datatype_For_Param1|<span data-ttu-id="96fcc-129">`nvarchar`(50)</span><span class="sxs-lookup"><span data-stu-id="96fcc-129">`nvarchar`(50)</span></span>|  
    |<span data-ttu-id="96fcc-130">[Default_Value_For_Param1]</span><span class="sxs-lookup"><span data-stu-id="96fcc-130">Default_Value_For_Param1</span></span>|<span data-ttu-id="96fcc-131">NULL</span><span class="sxs-lookup"><span data-stu-id="96fcc-131">NULL</span></span>|  
    |@Param2|@FirstName|  
    |@Datatype_For_Param2|<span data-ttu-id="96fcc-132">`nvarchar`(50)</span><span class="sxs-lookup"><span data-stu-id="96fcc-132">`nvarchar`(50)</span></span>|  
    |<span data-ttu-id="96fcc-133">[Default_Value_For_Param2]</span><span class="sxs-lookup"><span data-stu-id="96fcc-133">Default_Value_For_Param2</span></span>|<span data-ttu-id="96fcc-134">NULL</span><span class="sxs-lookup"><span data-stu-id="96fcc-134">NULL</span></span>|  
  
6.  <span data-ttu-id="96fcc-135">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96fcc-135">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="96fcc-136">**クエリ エディター**で、SELECT ステートメントを次のステートメントに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="96fcc-136">In the **Query Editor**, replace the SELECT statement with the following statement:</span></span>  
  
    ```sql  
    SELECT FirstName, LastName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory  
    WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    ```  
  
8.  <span data-ttu-id="96fcc-137">構文をテストするには、 **[クエリ]** メニューの **[解析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96fcc-137">To test the syntax, on the **Query** menu, click **Parse**.</span></span> <span data-ttu-id="96fcc-138">エラー メッセージが返された場合は、ステートメントと上記の情報を比較し、必要に応じて修正します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-138">If an error message is returned, compare the statements with the information above and correct as needed.</span></span>  
  
9. <span data-ttu-id="96fcc-139">ストアド プロシージャを作成するには、 **[クエリ]** メニューの **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96fcc-139">To create the procedure, from  the **Query** menu, click **Execute**.</span></span> <span data-ttu-id="96fcc-140">プロシージャがデータベース内のオブジェクトとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="96fcc-140">The procedure is created as an object in the database.</span></span>  
  
10. <span data-ttu-id="96fcc-141">オブジェクト エクスプローラーにリストされたプロシージャを確認するには、 **[ストアド プロシージャ]** を右クリックして **[更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-141">To see the procedure listed in Object Explorer, right-click **Stored Procedures** and select **Refresh**.</span></span>  
  
11. <span data-ttu-id="96fcc-142">プロシージャを実行するには、オブジェクト エクスプローラーでストアド プロシージャ名 **HumanResources.uspGetEmployeesTest** を右クリックし、 **[ストアド プロシージャの実行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-142">To run the procedure, in Object Explorer, right-click the stored procedure name **HumanResources.uspGetEmployeesTest** and select **Execute Stored Procedure**.</span></span>  
  
12. <span data-ttu-id="96fcc-143">**[プロシージャの実行]** ウィンドウでパラメーター @LastName の値に「Margheim」を、パラメーター @FirstName の値に「Diane」を入力します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-143">In the **Execute Procedure** window, enter Margheim as the value for the parameter @LastName and enter the value Diane as the value for the parameter @FirstName.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="96fcc-144">すべてのユーザー入力を検証します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-144">Validate all user input.</span></span> <span data-ttu-id="96fcc-145">ユーザー入力は検証するまで連結しないでください。</span><span class="sxs-lookup"><span data-stu-id="96fcc-145">Do not concatenate user input before you validate it.</span></span> <span data-ttu-id="96fcc-146">検証していないユーザー入力から作成されたコマンドは、絶対に実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="96fcc-146">Never execute a command constructed from unvalidated user input.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="96fcc-147">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="96fcc-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="96fcc-148">**クエリ エディターでプロシージャを作成するには**</span><span class="sxs-lookup"><span data-stu-id="96fcc-148">**To create a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="96fcc-149">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-149">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="96fcc-150">**[ファイル]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96fcc-150">From the **File** menu, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="96fcc-151">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96fcc-151">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="96fcc-152">この例では、上と同じストアド プロシージャを別のプロシージャ名で作成します。</span><span class="sxs-lookup"><span data-stu-id="96fcc-152">This example creates the same stored procedure as above using a different procedure name.</span></span>  
  
    ```sql
    USE AdventureWorks2012;  
    GO  
    CREATE PROCEDURE HumanResources.uspGetEmployeesTest2   
        @LastName nvarchar(50),   
        @FirstName nvarchar(50)   
    AS
  
        SET NOCOUNT ON;  
        SELECT FirstName, LastName, Department  
        FROM HumanResources.vEmployeeDepartmentHistory  
        WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    GO
    ```  
  
4.  <span data-ttu-id="96fcc-153">プロシージャを実行するには、次の例をコピーして新しいクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96fcc-153">To run the procedure, copy and paste the following example into a new query window and click **Execute**.</span></span> <span data-ttu-id="96fcc-154">パラメーター値を指定するときに別の方法が表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="96fcc-154">Notice that different methods of specifying the parameter values are shown.</span></span>  
  
    ```sql
    EXECUTE HumanResources.uspGetEmployeesTest2 N'Ackerman', N'Pilar';  
    -- Or  
    EXEC HumanResources.uspGetEmployeesTest2 @LastName = N'Ackerman', @FirstName = N'Pilar';  
    GO  
    -- Or  
    EXECUTE HumanResources.uspGetEmployeesTest2 @FirstName = N'Pilar', @LastName = N'Ackerman';  
    GO
    ```  
  
## <a name="see-also"></a><span data-ttu-id="96fcc-155">参照</span><span class="sxs-lookup"><span data-stu-id="96fcc-155">See Also</span></span>  
 [<span data-ttu-id="96fcc-156">CREATE PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="96fcc-156">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  