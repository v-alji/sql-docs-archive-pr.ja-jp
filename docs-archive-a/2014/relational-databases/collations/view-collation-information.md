---
title: 照合順序情報の表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 995e559cfd7ca871f5abd90751f2f79167bdf76f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645652"
---
# <a name="view-collation-information"></a><span data-ttu-id="f5669-102">照合順序情報の表示</span><span class="sxs-lookup"><span data-stu-id="f5669-102">View Collation Information</span></span>
    
##  <a name="you-can-view-the-collation-of-a-server-database-or-column-in-ssmanstudiofull-using-object-explorer-menu-options-or-by-using-tsql"></a><a name="Top"></a> <span data-ttu-id="f5669-103">サーバー、データベース、または列の照合順序は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でオブジェクト エクスプローラーのメニュー オプションを使用するか、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="f5669-103">You can view the collation of a server, database, or column in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] using Object Explorer menu options or by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
##  <a name="how-to-view-a-collation-setting"></a><a name="Procedures"></a> <span data-ttu-id="f5669-104">照合順序の設定を表示する方法</span><span class="sxs-lookup"><span data-stu-id="f5669-104">How to View a Collation Setting</span></span>  
 <span data-ttu-id="f5669-105">次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="f5669-105">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="f5669-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f5669-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="f5669-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5669-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f5669-108">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f5669-108">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f5669-109">**サーバー (SQL Server のインスタンス) の照合順序設定をオブジェクト エクスプローラーで表示するには**</span><span class="sxs-lookup"><span data-stu-id="f5669-109">**To view a collation setting for a server (instance of SQL Server) in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="f5669-110">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f5669-110">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f5669-111">インスタンスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5669-111">Right-click the instance and select **Properties**.</span></span>  
  
 <span data-ttu-id="f5669-112">**データベースの照合順序設定をオブジェクト エクスプローラーで表示するには**</span><span class="sxs-lookup"><span data-stu-id="f5669-112">**To view a collation setting for a database in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="f5669-113">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="f5669-113">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f5669-114">**[データベース]** を展開し、データベースを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5669-114">Expand **Databases**, right-click the database and select **Properties**.</span></span>  
  
 <span data-ttu-id="f5669-115">**列の照合順序設定をオブジェクト エクスプローラーで表示するには**</span><span class="sxs-lookup"><span data-stu-id="f5669-115">**To view a collation setting for a column in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="f5669-116">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="f5669-116">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f5669-117">**[データベース]** を展開し、データベースを展開して、 **[テーブル]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="f5669-117">Expand **Databases**, expand the database and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="f5669-118">目的の列を含んだテーブルを展開し、 **[列]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="f5669-118">Expand the table that contains the column and then expand **Columns**.</span></span>  
  
4.  <span data-ttu-id="f5669-119">列を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5669-119">Right-click the column and select **Properties**.</span></span> <span data-ttu-id="f5669-120">照合順序プロパティが空の場合、列が文字データ型ではありません。</span><span class="sxs-lookup"><span data-stu-id="f5669-120">If the collation property is empty, the column is not a character data type.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f5669-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f5669-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="f5669-122">**サーバーの照合順序設定を表示するには**</span><span class="sxs-lookup"><span data-stu-id="f5669-122">**To view the collation setting of a server**</span></span>  
  
1.  <span data-ttu-id="f5669-123">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5669-123">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f5669-124">クエリ ウィンドウで、SERVERPROPERTY システム関数を使用した次のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="f5669-124">In the query window, enter the following statement that uses the SERVERPROPERTY system function.</span></span>  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  <span data-ttu-id="f5669-125">また、sp_helpsort システム ストアド プロシージャを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f5669-125">Alternatively, you can use the sp_helpsort system stored procedure.</span></span>  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 <span data-ttu-id="f5669-126">**サポートされているすべての照合順序を表示するには [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="f5669-126">**To view all collations supported by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**</span></span>  
  
1.  <span data-ttu-id="f5669-127">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5669-127">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f5669-128">クエリ ウィンドウで、SERVERPROPERTY システム関数を使用した次のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="f5669-128">In the query window, enter the following statement that uses the SERVERPROPERTY system function.</span></span>  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 <span data-ttu-id="f5669-129">**データベースの照合順序設定を表示するには**</span><span class="sxs-lookup"><span data-stu-id="f5669-129">**To view the collation setting of a database**</span></span>  
  
1.  <span data-ttu-id="f5669-130">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5669-130">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f5669-131">クエリ ウィンドウで、sys.databases システム カタログ ビューを使用した次のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="f5669-131">In the query window, enter the following statement that uses the sys.databases system catalog view.</span></span>  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  <span data-ttu-id="f5669-132">また、DATABASEPROPERTYEX システム関数を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f5669-132">Alternatively, you can use the DATABASEPROPERTYEX system function.</span></span>  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 <span data-ttu-id="f5669-133">**列の照合順序設定を表示するには**</span><span class="sxs-lookup"><span data-stu-id="f5669-133">**To view the collation setting of a column**</span></span>  
  
1.  <span data-ttu-id="f5669-134">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5669-134">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f5669-135">クエリ ウィンドウで、sys.columns システム カタログ ビューを使用した次のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="f5669-135">In the query window, enter the following statement that uses the sys.columns system catalog view.</span></span>  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f5669-136">参照</span><span class="sxs-lookup"><span data-stu-id="f5669-136">See Also</span></span>  
 <span data-ttu-id="f5669-137">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5669-137">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="f5669-138">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5669-138">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span></span>  
 <span data-ttu-id="f5669-139">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5669-139">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="f5669-140">[sys.columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5669-140">[sys.columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) </span></span>  
 <span data-ttu-id="f5669-141">[照合順序の優先順位 &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5669-141">[Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span></span>  
 [<span data-ttu-id="f5669-142">sp_helpsort &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5669-142">sp_helpsort &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-helpsort-transact-sql)  
  
  
