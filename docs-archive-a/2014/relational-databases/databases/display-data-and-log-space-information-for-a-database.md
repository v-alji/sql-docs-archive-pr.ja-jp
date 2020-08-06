---
title: データベースのデータ領域とログ領域情報の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], space
- status information [SQL Server], space
- displaying space information
- disk space [SQL Server], displaying
- databases [SQL Server], space used
- viewing space information
- space allocation [SQL Server], displaying
- data space [SQL Server]
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1beb8cdedbc2b72eadeeb350ee1c3b6d16218205
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742194"
---
# <a name="display-data-and-log-space-information-for-a-database"></a><span data-ttu-id="ca8a3-102">データベースのデータ領域とログ領域情報の表示</span><span class="sxs-lookup"><span data-stu-id="ca8a3-102">Display Data and Log Space Information for a Database</span></span>
  <span data-ttu-id="ca8a3-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベースのデータ領域およびログ領域情報を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-103">This topic describes how to display the data and log space information for a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ca8a3-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ca8a3-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ca8a3-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ca8a3-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ca8a3-106">Security</span><span class="sxs-lookup"><span data-stu-id="ca8a3-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ca8a3-107">**以下を使用してデータベースのデータ領域とログ領域情報を表示するには:**</span><span class="sxs-lookup"><span data-stu-id="ca8a3-107">**To display data and log space information for a database, using:**</span></span>  
  
     [<span data-ttu-id="ca8a3-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ca8a3-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ca8a3-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ca8a3-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ca8a3-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="ca8a3-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ca8a3-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ca8a3-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ca8a3-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="ca8a3-112">Permissions</span></span>  
 <span data-ttu-id="ca8a3-113">**sp_spaceused** の実行権限は、 **public** ロールに与えられています。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-113">Permission to execute **sp_spaceused** is granted to the **public** role.</span></span> <span data-ttu-id="ca8a3-114">**@updateusage** パラメーターを指定できるのは、**db_owner** 固定データベース ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-114">Only members of the **db_owner** fixed database role can specify the **@updateusage** parameter.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ca8a3-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ca8a3-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-display-data-and-log-space-information-for-a-database"></a><span data-ttu-id="ca8a3-116">データベースのデータ領域とログ領域情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="ca8a3-116">To display data and log space information for a database</span></span>  
  
1.  <span data-ttu-id="ca8a3-117">オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-117">In Object Explorer, connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ca8a3-118">**[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-118">Expand **Databases**.</span></span>  
  
3.  <span data-ttu-id="ca8a3-119">データベースを右クリックし、 **[レポート]** 、 **[標準レポート]** の順にポイントして、 **[ディスク使用量]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-119">Right-click a database, point to **Reports**, point to **Standard Reports,**, and then click **Disk Usage**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ca8a3-120">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ca8a3-120">Using Transact-SQL</span></span>  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-using-sp_spaceused"></a><span data-ttu-id="ca8a3-121">sp_spaceused を使用してデータベースのデータ領域とログ領域情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="ca8a3-121">To display data and log space information for a database by using sp_spaceused</span></span>  
  
1.  <span data-ttu-id="ca8a3-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-122">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ca8a3-123">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ca8a3-124">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-124">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ca8a3-125">この例では、 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) システム ストアド プロシージャを使用して、 `Vendor` テーブルとそのインデックスに対するディスク領域情報を報告します。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-125">This example uses the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) system stored procedure to report disk space information for the `Vendor` table and its indexes.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-querying-sysdatabase_files"></a><span data-ttu-id="ca8a3-126">querying sys.database_files をクエリすることによってデータベースのデータ領域とログ領域情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="ca8a3-126">To display data and log space information for a database by querying sys.database_files</span></span>  
  
1.  <span data-ttu-id="ca8a3-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ca8a3-128">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ca8a3-129">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ca8a3-130">この例では、 [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) カタログ ビューに対してクエリを実行し、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内のデータ ファイルとログ ファイルに関する特定の情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-130">This example queries the [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) catalog view to return specific information about the data and log files in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca8a3-131">参照</span><span class="sxs-lookup"><span data-stu-id="ca8a3-131">See Also</span></span>  
 <span data-ttu-id="ca8a3-132">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca8a3-132">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="ca8a3-133">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca8a3-133">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="ca8a3-134">[sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca8a3-134">[sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) </span></span>  
 <span data-ttu-id="ca8a3-135">[データベースに対するデータ ファイルまたはログ ファイルの追加](add-data-or-log-files-to-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="ca8a3-135">[Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md) </span></span>  
 [<span data-ttu-id="ca8a3-136">データまたはログ ファイルのデータベースからの削除</span><span class="sxs-lookup"><span data-stu-id="ca8a3-136">Delete Data or Log Files from a Database</span></span>](delete-data-or-log-files-from-a-database.md)  
  
  
