---
title: テーブルの依存関係の表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20f54b913124cdaa8a7dfeebac01ba070cc37d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646086"
---
# <a name="view-the-dependencies-of-a-table"></a><span data-ttu-id="3fa35-102">テーブルの依存関係の表示</span><span class="sxs-lookup"><span data-stu-id="3fa35-102">View the Dependencies of a Table</span></span>
  <span data-ttu-id="3fa35-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してテーブルの依存関係を表示できます。</span><span class="sxs-lookup"><span data-stu-id="3fa35-103">You can view a table's dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="3fa35-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="3fa35-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3fa35-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3fa35-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3fa35-106">Security</span><span class="sxs-lookup"><span data-stu-id="3fa35-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3fa35-107">**テーブルの依存関係を表示するには、次を使用します:**</span><span class="sxs-lookup"><span data-stu-id="3fa35-107">**To view a table's dependencies, using:**</span></span>  
  
     [<span data-ttu-id="3fa35-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3fa35-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3fa35-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3fa35-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3fa35-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="3fa35-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3fa35-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3fa35-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3fa35-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="3fa35-112">Permissions</span></span>  
 <span data-ttu-id="3fa35-113">データベースに対する VIEW DEFINITION 権限およびデータベースの sys.sql_expression_dependencies に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3fa35-113">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="3fa35-114">既定では、SELECT 権限は db_owner 固定データベース ロールのメンバーだけに与えられます。</span><span class="sxs-lookup"><span data-stu-id="3fa35-114">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="3fa35-115">SELECT 権限と VIEW DEFINITION 権限が別のユーザーに与えられている場合、権限が許可されているユーザーはデータベース内のすべての依存関係を表示できます。</span><span class="sxs-lookup"><span data-stu-id="3fa35-115">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3fa35-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3fa35-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-dependencies-of-a-table"></a><span data-ttu-id="3fa35-117">テーブルの依存関係を表示するには</span><span class="sxs-lookup"><span data-stu-id="3fa35-117">To view the dependencies of a table</span></span>  
  
1.  <span data-ttu-id="3fa35-118">**オブジェクト エクスプローラー**で、 **[データベース]** を展開し、データベース、 **[テーブル]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="3fa35-118">In **Object Explorer**, expand **Databases**, expand a database, and then expand **Tables**.</span></span>  
  
2.  <span data-ttu-id="3fa35-119">テーブルを右クリックし、 **[依存関係の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fa35-119">Right-click a table, and then click **View Dependencies**.</span></span>  
  
3.  <span data-ttu-id="3fa35-120">**[オブジェクトの依存関係** _\<object name>]_ ダイアログ ボックスで、 **[** _\<object name> に依存するオブジェクト]_ または **[** _\<object name>_ **が依存するオブジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3fa35-120">In the **Object Dependencies**_\<object name>_ dialog box, select either **Objects that depend on** _\<object name>_, or **Objects on which**_\<object name>_**depends**.</span></span>  
  
4.  <span data-ttu-id="3fa35-121">**[依存関係]** グリッドでオブジェクトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fa35-121">Select an object in the **Dependencies** grid.</span></span> <span data-ttu-id="3fa35-122">オブジェクトの種類 ("トリガー" や "ストアド プロシージャ" など) が、 **[種類]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fa35-122">The type of object (such as "Trigger" or "Stored Procedure"), appears in the **Type** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3fa35-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3fa35-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a><span data-ttu-id="3fa35-124">テーブルに依存しているオブジェクトを表示するには</span><span class="sxs-lookup"><span data-stu-id="3fa35-124">To view the objects that depend on a table</span></span>  
  
1.  <span data-ttu-id="3fa35-125">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3fa35-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3fa35-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fa35-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3fa35-127">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fa35-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a><span data-ttu-id="3fa35-128">テーブルが依存しているオブジェクトを表示するには</span><span class="sxs-lookup"><span data-stu-id="3fa35-128">To view the objects on which a table depends</span></span>  
  
1.  <span data-ttu-id="3fa35-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3fa35-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3fa35-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fa35-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3fa35-131">次の例では、 `Production.Product`テーブルに依存するオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="3fa35-131">The following example returns the objects that depend on the table `Production.Product`.</span></span> <span data-ttu-id="3fa35-132">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fa35-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 <span data-ttu-id="3fa35-133">詳細については、「[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fa35-133">For additional information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)</span></span>  
  
  
