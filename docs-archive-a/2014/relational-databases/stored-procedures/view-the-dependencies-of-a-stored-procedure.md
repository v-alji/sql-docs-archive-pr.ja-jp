---
title: ストアド プロシージャの依存関係の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 790684035d2db3b697fb8b718c96182eda8f1186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646111"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a><span data-ttu-id="a7639-102">ストアド プロシージャの依存関係の表示</span><span class="sxs-lookup"><span data-stu-id="a7639-102">View the Dependencies of a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-view-stored-procedure-dependencies-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="a7639-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でストアド プロシージャの依存関係を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7639-103">This topic describes how to view stored procedure dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="a7639-104">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="a7639-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="a7639-105">**プロシージャの依存関係の表示に使用するもの:** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="a7639-105">**To view the dependencies of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a7639-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="a7639-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a7639-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a7639-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a7639-108">Permissions</span><span class="sxs-lookup"><span data-stu-id="a7639-108">Permissions</span></span>  
 <span data-ttu-id="a7639-109">システム関数: `sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="a7639-109">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="a7639-110">参照先エンティティに対する CONTROL 権限および sys.dm_sql_referencing_entities に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7639-110">Requires CONTROL permission on the referenced entity and SELECT permission on sys.dm_sql_referencing_entities.</span></span> <span data-ttu-id="a7639-111">参照先エンティティがパーティション関数である場合、データベースに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7639-111">When the referenced entity is a partition function, CONTROL permission on the database is required.</span></span> <span data-ttu-id="a7639-112">既定では、SELECT 権限が public に与えられます。</span><span class="sxs-lookup"><span data-stu-id="a7639-112">By default, SELECT permission is granted to public.</span></span>  
  
 <span data-ttu-id="a7639-113">システム関数: `sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="a7639-113">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="a7639-114">sys.dm_sql_referenced_entities に対する SELECT 権限および参照元エンティティに対する VIEW DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7639-114">Requires SELECT permission on sys.dm_sql_referenced_entities and VIEW DEFINITION permission on the referencing entity.</span></span> <span data-ttu-id="a7639-115">既定では、SELECT 権限が public に与えられます。</span><span class="sxs-lookup"><span data-stu-id="a7639-115">By default, SELECT permission is granted to public.</span></span> <span data-ttu-id="a7639-116">参照元エンティティがデータベース レベルの DDL トリガーである場合は、データベースに対する VIEW DEFINITION 権限またはデータベースに対する ALTER DATABASE DDL TRIGGER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7639-116">Requires VIEW DEFINITION permission on the database or ALTER DATABASE DDL TRIGGER permission on the database when the referencing entity is a database-level DDL trigger.</span></span> <span data-ttu-id="a7639-117">参照元エンティティがサーバー レベルの DDL トリガーである場合は、サーバーに対する VIEW ANY DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7639-117">Requires VIEW ANY DEFINITION permission on the server when the referencing entity is a server-level DDL trigger.</span></span>  
  
 <span data-ttu-id="a7639-118">オブジェクト カタログ ビュー: `sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="a7639-118">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="a7639-119">データベースに対する VIEW DEFINITION 権限およびデータベースの sys.sql_expression_dependencies に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7639-119">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="a7639-120">既定では、SELECT 権限は db_owner 固定データベース ロールのメンバーだけに与えられます。</span><span class="sxs-lookup"><span data-stu-id="a7639-120">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="a7639-121">SELECT 権限と VIEW DEFINITION 権限が別のユーザーに与えられている場合、権限が許可されているユーザーはデータベース内のすべての依存関係を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a7639-121">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="how-to-view-the-dependencies-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="a7639-122">ストアド プロシージャの依存関係を表示する方法</span><span class="sxs-lookup"><span data-stu-id="a7639-122">How to View the Dependencies of a Stored Procedure</span></span>  
 <span data-ttu-id="a7639-123">次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7639-123">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="a7639-124">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a7639-124">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="a7639-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a7639-125">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a7639-126">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a7639-126">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a7639-127">**オブジェクト エクスプローラーでプロシージャの依存関係を表示するには**</span><span class="sxs-lookup"><span data-stu-id="a7639-127">**To view the dependencies of a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="a7639-128">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-128">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a7639-129">**[データベース]** を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-129">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="a7639-130">**[ストアド プロシージャ]** を展開し、プロシージャを右クリックして、 **[依存関係の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7639-130">Expand **Stored Procedures**, right-click the procedure and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="a7639-131">プロシージャに依存しているオブジェクトの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="a7639-131">View the list of objects that depend on the procedure.</span></span>  
  
5.  <span data-ttu-id="a7639-132">プロシージャが依存しているオブジェクトの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="a7639-132">View the list of objects on which the procedure depends.</span></span>  
  
6.  <span data-ttu-id="a7639-133">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7639-133">Click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a7639-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a7639-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="a7639-135">**クエリ エディターでプロシージャの依存関係を表示するには**</span><span class="sxs-lookup"><span data-stu-id="a7639-135">**To view the dependencies of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="a7639-136">システム関数: `sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="a7639-136">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="a7639-137">この関数は、プロシージャに依存しているオブジェクトを表示するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a7639-137">This function is used to display the objects that depend on a procedure.</span></span>  
  
1.  <span data-ttu-id="a7639-138">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a7639-139">**[データベース]** を展開し、プロシージャが属するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-139">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="a7639-140">**[ファイル]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7639-140">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="a7639-141">次の例をコピーし、クエリ エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a7639-141">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="a7639-142">最初の例では、 `uspVendorAllInfo` データベース内のすべてのベンダーの名前と、そのベンダーの提供製品、信用格付け、およびベンダーが現時点で製品を提供できるかどうかを返す [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] プロシージャが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7639-142">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="a7639-143">このプロシージャの作成後、2 番目の例では、sys.dm_sql_referencing_entities 関数を使用して、プロシージャに依存しているオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="a7639-143">After the procedure is created, the second example uses the sys.dm_sql_referencing_entities function to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 <span data-ttu-id="a7639-144">システム関数: `sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="a7639-144">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="a7639-145">この関数は、プロシージャが依存しているオブジェクトを表示するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a7639-145">This function is used to display the objects a procedure depends on.</span></span>  
  
1.  <span data-ttu-id="a7639-146">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-146">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a7639-147">**[データベース]** を展開し、プロシージャが属するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-147">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="a7639-148">**[ファイル]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7639-148">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="a7639-149">次の例をコピーし、クエリ エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a7639-149">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="a7639-150">最初の例では、 `uspVendorAllInfo` データベース内のすべてのベンダーの名前と、そのベンダーの提供製品、信用格付け、およびベンダーが現時点で製品を提供できるかどうかを返す [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] プロシージャが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7639-150">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="a7639-151">このプロシージャの作成後、2 番目の例では、sys.dm_sql_referenced_entities 関数を使用して、プロシージャが依存しているオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="a7639-151">After the procedure is created, the second example uses the sys.dm_sql_referenced_entities function to display the objects that the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 <span data-ttu-id="a7639-152">オブジェクト カタログ ビュー: `sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="a7639-152">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="a7639-153">このビューを使用すると、プロシージャが依存しているオブジェクトまたはプロシージャに依存しているオブジェクトを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a7639-153">This view can be used to display objects that a procedure depends on or that depend on a procedure.</span></span>  
  
 <span data-ttu-id="a7639-154">プロシージャに依存しているオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="a7639-154">Displaying the objects that depend on a procedure.</span></span>  
 1.  <span data-ttu-id="a7639-155">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a7639-156">**[データベース]** を展開し、プロシージャが属するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-156">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="a7639-157">**[ファイル]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7639-157">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="a7639-158">次の例をコピーし、クエリ エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a7639-158">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="a7639-159">最初の例では、 `uspVendorAllInfo` データベース内のすべてのベンダーの名前と、そのベンダーの提供製品、信用格付け、およびベンダーが現時点で製品を提供できるかどうかを返す [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] プロシージャが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7639-159">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="a7639-160">このプロシージャの作成後、2 番目の例では、sys.sql_expression_dependencies ビューを使用して、プロシージャに依存しているオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="a7639-160">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 <span data-ttu-id="a7639-161">プロシージャが依存しているオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="a7639-161">Displaying the objects a procedure depends on.</span></span>  
 1.  <span data-ttu-id="a7639-162">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a7639-163">**[データベース]** を展開し、プロシージャが属するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a7639-163">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="a7639-164">**[ファイル]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7639-164">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="a7639-165">次の例をコピーし、クエリ エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a7639-165">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="a7639-166">最初の例では、 `uspVendorAllInfo` データベース内のすべてのベンダーの名前と、そのベンダーの提供製品、信用格付け、およびベンダーが現時点で製品を提供できるかどうかを返す [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] プロシージャが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7639-166">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="a7639-167">このプロシージャの作成後、2 番目の例では、sys.sql_expression_dependencies ビューを使用して、プロシージャが依存しているオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="a7639-167">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a7639-168">参照</span><span class="sxs-lookup"><span data-stu-id="a7639-168">See Also</span></span>  
 <span data-ttu-id="a7639-169">[ストアド プロシージャの名前の変更](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a7639-169">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="a7639-170">[sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7639-170">[sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span></span>  
 <span data-ttu-id="a7639-171">[sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7639-171">[sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span></span>  
 [<span data-ttu-id="a7639-172">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a7639-172">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
