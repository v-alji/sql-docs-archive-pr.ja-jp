---
title: データベースのプロパティの表示または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6aee7503ca02d47575be4e8103641f61d9696d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741062"
---
# <a name="view-or-change-the-properties-of-a-database"></a><span data-ttu-id="e217f-102">データベースのプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="e217f-102">View or Change the Properties of a Database</span></span>
  <span data-ttu-id="e217f-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベースのプロパティを表示または変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e217f-103">This topic describes how to view or change the properties of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e217f-104">データベースのプロパティを変更すると、変更は直ちに有効になります。</span><span class="sxs-lookup"><span data-stu-id="e217f-104">After you change a database property, the modification takes effect immediately.</span></span>  
  
 <span data-ttu-id="e217f-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e217f-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e217f-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e217f-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e217f-107">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="e217f-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="e217f-108">Security</span><span class="sxs-lookup"><span data-stu-id="e217f-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e217f-109">**以下を使用してデータベースのプロパティを表示または変更するには:**</span><span class="sxs-lookup"><span data-stu-id="e217f-109">**To view or change the properties of a database, using:**</span></span>  
  
     [<span data-ttu-id="e217f-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e217f-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e217f-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e217f-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e217f-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="e217f-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e217f-113">推奨事項</span><span class="sxs-lookup"><span data-stu-id="e217f-113">Recommendations</span></span>  
  
-   <span data-ttu-id="e217f-114">AUTO_CLOSE が ON の場合、データベースからデータを取得できないため、 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) カタログ ビューの一部の列、および DATABASEPROPERTYEX 関数は、NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="e217f-114">When AUTO_CLOSE is ON, some columns in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view and DATABASEPROPERTYEX function will return NULL because the database is unavailable to retrieve the data.</span></span> <span data-ttu-id="e217f-115">これを解決するには、USE ステートメントを実行してデータベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="e217f-115">To resolve this, execute a USE statement to open the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e217f-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e217f-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e217f-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="e217f-117">Permissions</span></span>  
 <span data-ttu-id="e217f-118">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e217f-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e217f-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e217f-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a><span data-ttu-id="e217f-120">データベースのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="e217f-120">To view or change the properties of a database</span></span>  
  
1.  <span data-ttu-id="e217f-121">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="e217f-121">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e217f-122">**[データベース]** を展開し、表示するデータベースを右クリックします。次に **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-122">Expand **Databases**, right-click the database to view, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e217f-123">**[データベースのプロパティ]** ダイアログ ボックスで、任意のページを選択して、対応する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="e217f-123">In the **Database Properties** dialog box, select a page to view the corresponding information.</span></span> <span data-ttu-id="e217f-124">たとえば、データおよびログ ファイルの情報を表示するには、 **[ファイル]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-124">For example, select the **Files** page to view data and log file information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e217f-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e217f-125">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-property-of-a-database-by-using-databasepropertyex"></a><span data-ttu-id="e217f-126">DATABASEPROPERTYEX を使用してデータベースのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="e217f-126">To view a property of a database by using DATABASEPROPERTYEX</span></span>  
  
1.  <span data-ttu-id="e217f-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="e217f-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e217f-128">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e217f-129">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e217f-130">この例では、 [データベースの AUTO_SHRINK データベース オプションのステータスを、](/sql/t-sql/functions/databasepropertyex-transact-sql) DATABASEPROPERTYEX [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] システム関数を使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="e217f-130">This example uses the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) system function to return the status of the AUTO_SHRINK database option in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="e217f-131">戻り値が 1 の場合はオプションがオンに、戻り値が 0 の場合はオフに設定されていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e217f-131">A return value of 1 means that the option is set to ON, and a return value of 0 means that the option is set to OFF.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
GO  
  
```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a><span data-ttu-id="e217f-132">sys.databases をクエリすることによってデータベースのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="e217f-132">To view the properties of a database by querying sys.databases</span></span>  
  
1.  <span data-ttu-id="e217f-133">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="e217f-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e217f-134">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e217f-135">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e217f-136">この例では、 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) カタログ ビューをクエリして、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースのいくつかのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="e217f-136">This example queries the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view to view several properties of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="e217f-137">この例では、データベースの ID 番号 (`database_id`)、データベースが読み取り専用か読み取り/書き込み可能かの情報 (`is_read_only`)、データベースの照合順序 (`collation_name`)、データベースの互換性レベル (`compatibility_level`) を取得します。</span><span class="sxs-lookup"><span data-stu-id="e217f-137">This example returns the database ID number (`database_id`), whether the database is read-only or read-write (`is_read_only`), the collation for the database (`collation_name`), and the database compatibility level (`compatibility_level`).</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT database_id, is_read_only, collation_name, compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-properties-of-a-database"></a><span data-ttu-id="e217f-138">データベースのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="e217f-138">To change the properties of a database</span></span>  
  
1.  <span data-ttu-id="e217f-139">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="e217f-139">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e217f-140">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-140">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e217f-141">次の例をコピーし、クエリ ウィンドウに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e217f-141">Copy and paste the following example into the query window.</span></span> <span data-ttu-id="e217f-142">この例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース上のスナップショット分離の状態を確認し、プロパティの状態を変更した後、変更内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="e217f-142">The example determines the state of snapshot isolation on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, changes the state of the property, and then verifies the change.</span></span>  
  
     <span data-ttu-id="e217f-143">スナップショット分離の状態を確認するには、まず `SELECT` ステートメントを選択し、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-143">To determine the state of snapshot isolation, select the first `SELECT` statement and click **Execute**.</span></span>  
  
     <span data-ttu-id="e217f-144">スナップショット分離の状態を変更するには、 `ALTER DATABASE` ステートメントを選択し、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-144">To change the state of snapshot isolation, select the `ALTER DATABASE` statement and click **Execute**.</span></span>  
  
     <span data-ttu-id="e217f-145">変更内容を確認するには、2 つ目の `SELECT` ステートメントを選択し、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e217f-145">To verify the change, select the second `SELECT` statement, and click **Execute**.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase9](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase9)]  
  
## <a name="see-also"></a><span data-ttu-id="e217f-146">参照</span><span class="sxs-lookup"><span data-stu-id="e217f-146">See Also</span></span>  
 <span data-ttu-id="e217f-147">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e217f-147">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="e217f-148">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span><span class="sxs-lookup"><span data-stu-id="e217f-148">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span></span>  
 <span data-ttu-id="e217f-149">[ALTER DATABASE SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="e217f-149">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="e217f-150">[ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="e217f-150">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="e217f-151">[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span><span class="sxs-lookup"><span data-stu-id="e217f-151">[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span></span>  
 [<span data-ttu-id="e217f-152">ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e217f-152">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
  
