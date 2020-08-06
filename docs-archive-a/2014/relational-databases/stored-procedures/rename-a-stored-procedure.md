---
title: ストアド プロシージャの名前の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], renaming
- renaming stored procedures
ms.assetid: 5d2e4c68-7e0b-4405-8919-f5b203e46770
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02e1acb528a32ef242e160e0ce5dd0267237c876
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646116"
---
# <a name="rename-a-stored-procedure"></a><span data-ttu-id="e5919-102">ストアド プロシージャの名前の変更</span><span class="sxs-lookup"><span data-stu-id="e5919-102">Rename a Stored Procedure</span></span>
  <span data-ttu-id="e5919-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でストアド プロシージャの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5919-103">This topic describes how to rename a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e5919-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e5919-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e5919-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e5919-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e5919-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e5919-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e5919-107">Security</span><span class="sxs-lookup"><span data-stu-id="e5919-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e5919-108">**ストアド プロシージャの名前を変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="e5919-108">**To rename a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="e5919-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e5919-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e5919-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e5919-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e5919-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="e5919-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e5919-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e5919-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e5919-113">プロシージャ名は、 [識別子](../databases/database-identifiers.md)のルールに従っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5919-113">Procedure names must comply with the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="e5919-114">ストアド プロシージャの名前を変更しても、 **sys.sql_modules** カタログ ビューの定義列にある、対応するオブジェクトの名前は変更されません。</span><span class="sxs-lookup"><span data-stu-id="e5919-114">Renaming a stored procedure will not change the name of the corresponding object name in the definition column of the **sys.sql_modules** catalog view.</span></span> <span data-ttu-id="e5919-115">したがって、このオブジェクトの種類の名前を変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5919-115">Therefore, we recommend that you do not rename this object type.</span></span> <span data-ttu-id="e5919-116">代わりに、ストアド プロシージャを削除して新しい名前で再作成してください。</span><span class="sxs-lookup"><span data-stu-id="e5919-116">Instead, drop and re-create the stored procedure with its new name.</span></span>  
  
-   <span data-ttu-id="e5919-117">プロシージャの名前または定義を変更すると、依存オブジェクトを更新してプロシージャに加えられた変更を反映しなければ、その依存オブジェクトが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5919-117">Changing the name or definition of a procedure can cause dependent objects to fail when the objects are not updated to reflect the changes that have been made to the procedure.</span></span> <span data-ttu-id="e5919-118">詳細については、「 [ストアド プロシージャの依存関係の表示](view-the-dependencies-of-a-stored-procedure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5919-118">For more information, see [View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e5919-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e5919-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e5919-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="e5919-120">Permissions</span></span>  
 <span data-ttu-id="e5919-121">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="e5919-121">CREATE PROCEDURE</span></span>  
 <span data-ttu-id="e5919-122">データベースの CREATE PROCEDURE 権限およびプロシージャの作成先となるスキーマの ALTER 権限、または、**db_ddladmin** 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="e5919-122">Requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created, or requires membership in the **db_ddladmin** fixed database role.</span></span>  
  
 <span data-ttu-id="e5919-123">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="e5919-123">ALTER PROCEDURE</span></span>  
 <span data-ttu-id="e5919-124">プロシージャの ALTER 権限、または **db_ddladmin** 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="e5919-124">Requires ALTER permission on the procedure or requires membership in the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e5919-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e5919-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-stored-procedure"></a><span data-ttu-id="e5919-126">ストアド プロシージャの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="e5919-126">To rename a stored procedure</span></span>  
  
1.  <span data-ttu-id="e5919-127">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="e5919-127">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e5919-128">**[データベース]** を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="e5919-128">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="e5919-129">[ストアド プロシージャの依存関係を確認します](view-the-dependencies-of-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="e5919-129">[Determine the dependencies of the stored procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
4.  <span data-ttu-id="e5919-130">**[ストアド プロシージャ]** を展開し、名前を変更するプロシージャを右クリックして、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5919-130">Expand **Stored Procedures**, right-click the procedure to rename, and then click **Rename**.</span></span>  
  
5.  <span data-ttu-id="e5919-131">プロシージャ名を変更します。</span><span class="sxs-lookup"><span data-stu-id="e5919-131">Modify the procedure name.</span></span>  
  
6.  <span data-ttu-id="e5919-132">依存オブジェクトまたはスクリプトで参照しているプロシージャ名を変更します。</span><span class="sxs-lookup"><span data-stu-id="e5919-132">Modify the procedure name referenced in any dependent objects or scripts.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e5919-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e5919-133">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-stored-procedure"></a><span data-ttu-id="e5919-134">ストアド プロシージャの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="e5919-134">To rename a stored procedure</span></span>  
  
1.  <span data-ttu-id="e5919-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="e5919-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e5919-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5919-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e5919-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5919-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e5919-138">この例では、プロシージャを削除した後、新しい名前でプロシージャを再作成することによってプロシージャの名前を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e5919-138">This example shows how to rename a procedure by dropping the procedure and re-creating the procedure with a new name.</span></span> <span data-ttu-id="e5919-139">最初の例では、 `'HumanResources.uspGetAllEmployeesTest`という名前のストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5919-139">The first example creates the stored procedure `'HumanResources.uspGetAllEmployeesTest`.</span></span> <span data-ttu-id="e5919-140">2 番目の例では、ストアド プロシージャの名前を `HumanResources.uspEveryEmployeeTest`に変更します。</span><span class="sxs-lookup"><span data-stu-id="e5919-140">The second example renames the stored procedure to `HumanResources.uspEveryEmployeeTest`.</span></span>  
  
```sql  
--Create the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspGetAllEmployeesTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
  
--Rename the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspEveryEmployeeTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5919-141">参照</span><span class="sxs-lookup"><span data-stu-id="e5919-141">See Also</span></span>  
 <span data-ttu-id="e5919-142">[ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e5919-142">[ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql) </span></span>  
 <span data-ttu-id="e5919-143">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e5919-143">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 <span data-ttu-id="e5919-144">[ストアド プロシージャの作成](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e5919-144">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="e5919-145">[ストアド プロシージャの変更](../stored-procedures/modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e5919-145">[Modify a Stored Procedure](../stored-procedures/modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="e5919-146">[ストアド プロシージャの削除](../stored-procedures/delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e5919-146">[Delete a Stored Procedure](../stored-procedures/delete-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="e5919-147">[ストアド プロシージャの定義の表示](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e5919-147">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="e5919-148">ストアド プロシージャの依存関係の表示</span><span class="sxs-lookup"><span data-stu-id="e5919-148">View the Dependencies of a Stored Procedure</span></span>](view-the-dependencies-of-a-stored-procedure.md)  
  
  
