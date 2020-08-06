---
title: ストアド プロシージャの定義の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4da455d38f984b08ee1f396f26cd4cc85411be92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640841"
---
# <a name="view-the-definition-of-a-stored-procedure"></a><span data-ttu-id="c8246-102">ストアド プロシージャの定義の表示</span><span class="sxs-lookup"><span data-stu-id="c8246-102">View the Definition of a Stored Procedure</span></span>
    
##  <a name="you-can-view-the-definition-of-a-stored-procedure-in-ssmanstudiofull-using-object-explorer-menu-options-or-in-the-query-editor-using-tsql-this-topic-describes-how-to-view-the-definition-of-procedure-in-object-explorer-and-by-using-a-system-stored-procedure-system-function-and-object-catalog-view-in-the-query-editor"></a><a name="Top"></a> <span data-ttu-id="c8246-103">ストアド プロシージャの定義は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でオブジェクト エクスプローラーのメニュー オプションを使用するか、クエリ エディターで [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="c8246-103">You can view the definition of a stored procedure in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] using Object Explorer menu options or in the Query Editor using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c8246-104">このトピックでは、オブジェクト エクスプローラーでプロシージャの定義を表示する方法について説明します。さらに、クエリ エディターでのシステム プロシージャ、システム関数、およびオブジェクト カタログ ビューを使用した表示方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8246-104">This topic describes how to view the definition of procedure in Object Explorer and by using a system stored procedure, system function, and object catalog view in the Query Editor.</span></span>  
  
-   <span data-ttu-id="c8246-105">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="c8246-105">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="c8246-106">**プロシージャの定義を表示するには、次を使用:** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="c8246-106">**To view the definition of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c8246-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="c8246-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c8246-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c8246-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c8246-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="c8246-109">Permissions</span></span>  
 <span data-ttu-id="c8246-110">システム ストアド プロシージャ: `sp_helptext`</span><span class="sxs-lookup"><span data-stu-id="c8246-110">System Stored Procedure: `sp_helptext`</span></span>  
 <span data-ttu-id="c8246-111">ロール **public** のメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="c8246-111">Requires membership in the **public** role.</span></span> <span data-ttu-id="c8246-112">システム オブジェクトの定義は、公開されます。</span><span class="sxs-lookup"><span data-stu-id="c8246-112">System object definitions are publicly visible.</span></span> <span data-ttu-id="c8246-113">ユーザー オブジェクトの定義は、オブジェクトの所有者、または次のいずれかの権限を許可された人が表示できます。ALTER、CONTROL、TAKE OWNERSHIP、VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="c8246-113">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span>  
  
 <span data-ttu-id="c8246-114">システム関数: `OBJECT_DEFINITION`</span><span class="sxs-lookup"><span data-stu-id="c8246-114">System Function: `OBJECT_DEFINITION`</span></span>  
 <span data-ttu-id="c8246-115">システム オブジェクトの定義は、公開されます。</span><span class="sxs-lookup"><span data-stu-id="c8246-115">System object definitions are publicly visible.</span></span> <span data-ttu-id="c8246-116">ユーザー オブジェクトの定義は、オブジェクトの所有者、または次のいずれかの権限を許可された人が表示できます。ALTER、CONTROL、TAKE OWNERSHIP、VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="c8246-116">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span> <span data-ttu-id="c8246-117">これらの権限は **db_owner**、 **db_ddladmin**、および **db_securityadmin** 固定データベース ロールのメンバーが暗黙的に保有します。</span><span class="sxs-lookup"><span data-stu-id="c8246-117">These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.</span></span>  
  
 <span data-ttu-id="c8246-118">オブジェクト カタログ ビュー: `sys.sql_modules`</span><span class="sxs-lookup"><span data-stu-id="c8246-118">Object Catalog View: `sys.sql_modules`</span></span>  
 <span data-ttu-id="c8246-119">カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。</span><span class="sxs-lookup"><span data-stu-id="c8246-119">The visibility of the metadata in catalog views is limited to securables that a user either owns or on which the user has been granted some permission.</span></span> <span data-ttu-id="c8246-120">詳細については、「 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8246-120">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
##  <a name="how-to-view-the-definition-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="c8246-121">ストアド プロシージャの定義の表示方法</span><span class="sxs-lookup"><span data-stu-id="c8246-121">How to View the Definition of a Stored Procedure</span></span>  
 <span data-ttu-id="c8246-122">次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8246-122">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="c8246-123">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c8246-123">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="c8246-124">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c8246-124">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c8246-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c8246-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c8246-126">**オブジェクト エクスプローラーでプロシージャの定義を表示するには**</span><span class="sxs-lookup"><span data-stu-id="c8246-126">**To view the definition a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="c8246-127">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="c8246-127">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c8246-128">**[データベース]** を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="c8246-128">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="c8246-129">**[ストアド プロシージャ]** を展開し、プロシージャを右クリックしてから **[ストアド プロシージャをスクリプト化]** をクリックします。その後、次のいずれかをクリックします: **[新規作成]** 、 **[構造変更]** 、 **[削除および作成]** 。</span><span class="sxs-lookup"><span data-stu-id="c8246-129">Expand **Stored Procedures**, right-click the procedure and then click **Script Stored Procedure as**, and then click one of the following: **Create To**, **Alter To**, or **Drop and Create To**.</span></span>  
  
4.  <span data-ttu-id="c8246-130">**新しいクエリ エディター ウィンドウ**を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8246-130">Select **New Query Editor Window**.</span></span> <span data-ttu-id="c8246-131">プロシージャの定義が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8246-131">This will display the procedure definition.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c8246-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c8246-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="c8246-133">**クエリ エディターでプロシージャの定義を表示するには**</span><span class="sxs-lookup"><span data-stu-id="c8246-133">**To view the definition of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="c8246-134">システム ストアド プロシージャ: `sp_helptext`</span><span class="sxs-lookup"><span data-stu-id="c8246-134">System Stored Procedure: `sp_helptext`</span></span>  
 1.  <span data-ttu-id="c8246-135">オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c8246-135">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c8246-136">ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8246-136">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c8246-137">クエリ ウィンドウで、`sp_helptext` システム ストアド プロシージャを使用した次のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8246-137">In the query window, enter the following statement that uses the `sp_helptext` system stored procedure.</span></span> <span data-ttu-id="c8246-138">データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。</span><span class="sxs-lookup"><span data-stu-id="c8246-138">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 <span data-ttu-id="c8246-139">システム関数: `OBJECT_DEFINITION`</span><span class="sxs-lookup"><span data-stu-id="c8246-139">System Function: `OBJECT_DEFINITION`</span></span>  
 1.  <span data-ttu-id="c8246-140">オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c8246-140">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c8246-141">ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8246-141">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c8246-142">クエリ ウィンドウで、`OBJECT_DEFINITION` システム関数を使用した次のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8246-142">In the query window, enter the following statements that use the `OBJECT_DEFINITION` system function.</span></span> <span data-ttu-id="c8246-143">データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。</span><span class="sxs-lookup"><span data-stu-id="c8246-143">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 <span data-ttu-id="c8246-144">オブジェクト カタログ ビュー: `sys.sql_modules`</span><span class="sxs-lookup"><span data-stu-id="c8246-144">Object Catalog View: `sys.sql_modules`</span></span>  
 1.  <span data-ttu-id="c8246-145">オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c8246-145">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c8246-146">ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8246-146">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c8246-147">クエリ ウィンドウで、`sys.sql_modules` カタログ ビューを使用した次のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="c8246-147">In the query window, enter the following statements that use the `sys.sql_modules` catalog view.</span></span> <span data-ttu-id="c8246-148">データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。</span><span class="sxs-lookup"><span data-stu-id="c8246-148">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c8246-149">参照</span><span class="sxs-lookup"><span data-stu-id="c8246-149">See Also</span></span>  
 <span data-ttu-id="c8246-150">[ストアド プロシージャの作成](create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c8246-150">[Create a Stored Procedure](create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="c8246-151">[ストアド プロシージャの変更](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c8246-151">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="c8246-152">[ストアド プロシージャの削除](delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c8246-152">[Delete a Stored Procedure](delete-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="c8246-153">[ストアド プロシージャの名前の変更](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c8246-153">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="c8246-154">[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8246-154">[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) </span></span>  
 <span data-ttu-id="c8246-155">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8246-155">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="c8246-156">[sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8246-156">[sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql) </span></span>  
 [<span data-ttu-id="c8246-157">OBJECT_ID &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c8246-157">OBJECT_ID &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-id-transact-sql)  
  
  
