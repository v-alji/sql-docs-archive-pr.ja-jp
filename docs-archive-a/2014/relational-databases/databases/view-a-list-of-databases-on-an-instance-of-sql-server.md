---
title: SQL Server インスタンス上のデータベースの一覧表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- current databases
- databases currently on server [SQL Server]
- database list [SQL Server]
- viewing database list
- displaying database list
- databases [SQL Server], viewing
- servers [SQL Server], databases listed on
- listing databases
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 47283fa9065a0b9d6238dab804094d9a65d17897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741073"
---
# <a name="view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="a8662-102">SQL Server インスタンス上のデータベースの一覧表示</span><span class="sxs-lookup"><span data-stu-id="a8662-102">View a List of Databases on an Instance of SQL Server</span></span>
  <span data-ttu-id="a8662-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]インスタンス上のデータベースの一覧を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8662-103">This topic describes how to view a list of databases on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a8662-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a8662-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a8662-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a8662-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a8662-106">Security</span><span class="sxs-lookup"><span data-stu-id="a8662-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a8662-107">**以下を使用して SQL Server インスタンス上のデータベースの一覧を表示するには:**</span><span class="sxs-lookup"><span data-stu-id="a8662-107">**To view a list of databases on an instance of SQL Server, using:**</span></span>  
  
     [<span data-ttu-id="a8662-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a8662-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a8662-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a8662-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a8662-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="a8662-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a8662-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a8662-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a8662-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="a8662-112">Permissions</span></span>  
 <span data-ttu-id="a8662-113">**sys.databases** の呼び出し元がデータベースの所有者ではなく、データベースが **master** でも **tempdb**でもない場合、対応する行を表示するには、少なくとも **master** データベースで、ALTER ANY DATABASE または VIEW ANY DATABASE のサーバーレベルの権限、あるいは、CREATE DATABASE の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a8662-113">If the caller of **sys.databases** is not the owner of the database and the database is not **master** or **tempdb**, the minimum permissions required to see the corresponding row are ALTER ANY DATABASE or VIEW ANY DATABASE server-level permission, or CREATE DATABASE permission in the **master** database.</span></span> <span data-ttu-id="a8662-114">呼び出し元が接続しているデータベースは常に **sys.databases**で確認できます。</span><span class="sxs-lookup"><span data-stu-id="a8662-114">The database to which the caller is connected can always be viewed in **sys.databases**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a8662-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a8662-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="a8662-116">SQL Server インスタンス上のデータベースの一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="a8662-116">To view a list of databases on an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="a8662-117">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a8662-117">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a8662-118">インスタンス上のすべてのデータベースの一覧を表示するには、 **[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a8662-118">To see a list of all databases on the instance, expand **Databases**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a8662-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a8662-119">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="a8662-120">SQL Server インスタンス上のデータベースの一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="a8662-120">To view a list of databases on an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="a8662-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="a8662-121">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a8662-122">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8662-122">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a8662-123">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8662-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a8662-124">この例は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに存在するデータベースの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="a8662-124">This example returns a list of databases on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a8662-125">この一覧には、データベースの名前、ID、および作成日が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a8662-125">The list includes the names of the databases, their database IDs, and the dates when the databases were created.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8662-126">参照</span><span class="sxs-lookup"><span data-stu-id="a8662-126">See Also</span></span>  
 <span data-ttu-id="a8662-127">[データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a8662-127">[Databases and Files Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql) </span></span>  
 [<span data-ttu-id="a8662-128">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a8662-128">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
