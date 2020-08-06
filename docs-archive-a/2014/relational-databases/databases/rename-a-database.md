---
title: データベースの名前変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd25a78e3d3b9be2e7191ce6ed3d6bdcbb0f9606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640058"
---
# <a name="rename-a-database"></a><span data-ttu-id="746cd-102">データベースの名前変更</span><span class="sxs-lookup"><span data-stu-id="746cd-102">Rename a Database</span></span>
  <span data-ttu-id="746cd-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ユーザー定義のデータベースの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="746cd-103">This topic describes how to rename a user-defined database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="746cd-104">識別子の規則に従っていれば、データベースの名前にはいずれの文字も使用できます。</span><span class="sxs-lookup"><span data-stu-id="746cd-104">The name of the database can include any characters that follow the rules for identifiers.</span></span>  
  
 <span data-ttu-id="746cd-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="746cd-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="746cd-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="746cd-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="746cd-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="746cd-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="746cd-108">Security</span><span class="sxs-lookup"><span data-stu-id="746cd-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="746cd-109">**以下を使用してデータベースの名前を変更するには:**</span><span class="sxs-lookup"><span data-stu-id="746cd-109">**To rename a database, using:**</span></span>  
  
     [<span data-ttu-id="746cd-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="746cd-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="746cd-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="746cd-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="746cd-112">**補足情報:** [データベースの名前を変更した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="746cd-112">**Follow Up:**  [After renaming a database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="746cd-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="746cd-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="746cd-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="746cd-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="746cd-115">システム データベースの名前は変更できません。</span><span class="sxs-lookup"><span data-stu-id="746cd-115">System databases cannot be renamed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="746cd-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="746cd-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="746cd-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="746cd-117">Permissions</span></span>  
 <span data-ttu-id="746cd-118">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="746cd-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="746cd-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="746cd-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-database"></a><span data-ttu-id="746cd-120">データベースの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="746cd-120">To rename a database</span></span>  
  
1.  <span data-ttu-id="746cd-121">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="746cd-121">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="746cd-122">データベースを使用している人がいないことを確認し、 [データベースをシングル ユーザー モードに設定します](set-a-database-to-single-user-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="746cd-122">Make sure that no one is using the database, and then [set the database to single-user mode](set-a-database-to-single-user-mode.md).</span></span>  
  
3.  <span data-ttu-id="746cd-123">**[データベース]** を展開し、名前を変更するデータベースを右クリックして、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="746cd-123">Expand **Databases**, right-click the database to rename, and then click **Rename**.</span></span>  
  
4.  <span data-ttu-id="746cd-124">新しいデータベース名を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="746cd-124">Enter the new database name, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="746cd-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="746cd-125">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-database"></a><span data-ttu-id="746cd-126">データベースの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="746cd-126">To rename a database</span></span>  
  
1.  <span data-ttu-id="746cd-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="746cd-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="746cd-128">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="746cd-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="746cd-129">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="746cd-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="746cd-130">この例では、 `AdventureWorks2012` データベースの名前を `Northwind`に変更します。</span><span class="sxs-lookup"><span data-stu-id="746cd-130">This example changes the name of the `AdventureWorks2012` database to `Northwind`.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
###  <a name="TsqlExample"></a>   
##  <a name="follow-up-after-renaming-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="746cd-131">補足情報: データベースの名前を変更した後</span><span class="sxs-lookup"><span data-stu-id="746cd-131">Follow Up: After renaming a database</span></span>  
 <span data-ttu-id="746cd-132">データベースの名前を変更した後は、 **master** データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="746cd-132">Back up the **master** database after you rename any database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="746cd-133">参照</span><span class="sxs-lookup"><span data-stu-id="746cd-133">See Also</span></span>  
 <span data-ttu-id="746cd-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="746cd-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="746cd-135">データベース識別子</span><span class="sxs-lookup"><span data-stu-id="746cd-135">Database Identifiers</span></span>](database-identifiers.md)  
  
  
