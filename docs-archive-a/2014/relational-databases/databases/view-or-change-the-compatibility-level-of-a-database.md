---
title: データベースの互換性レベルの表示または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- compatibility levels [SQL Server], viewing
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], changing
ms.assetid: 579867ec-57cb-4cb8-af35-9688c1e9e15d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35cf7af50eba333440c42a1bac428df1fff156b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741081"
---
# <a name="view-or-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="1a31d-102">データベースの互換性レベルの表示または変更</span><span class="sxs-lookup"><span data-stu-id="1a31d-102">View or Change the Compatibility Level of a Database</span></span>
  <span data-ttu-id="1a31d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースの互換性レベルを表示または変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a31d-103">This topic describes how to view or change the compatibility level of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1a31d-104">データベースの互換性レベルを変更する前に、この変更がアプリケーションに及ぼす影響について理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a31d-104">Before you change the compatibility level of a database, you should understand the impact of the change on your applications.</span></span> <span data-ttu-id="1a31d-105">詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a31d-105">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
 <span data-ttu-id="1a31d-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1a31d-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1a31d-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1a31d-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1a31d-108">Security</span><span class="sxs-lookup"><span data-stu-id="1a31d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1a31d-109">**以下を使用してデータベースの互換性レベルを表示または変更するには:**</span><span class="sxs-lookup"><span data-stu-id="1a31d-109">**To view or change the compatibility level of a database, using:**</span></span>  
  
     [<span data-ttu-id="1a31d-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1a31d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1a31d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1a31d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1a31d-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="1a31d-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1a31d-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1a31d-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1a31d-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="1a31d-114">Permissions</span></span>  
 <span data-ttu-id="1a31d-115">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="1a31d-115">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1a31d-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1a31d-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="1a31d-117">データベースの互換性レベルを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="1a31d-117">To view or change the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="1a31d-118">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の適切なインスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a31d-118">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name.</span></span>  
  
2.  <span data-ttu-id="1a31d-119">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="1a31d-119">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="1a31d-120">データベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a31d-120">Right-click the database, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="1a31d-121">**[データベースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a31d-121">The **Database Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="1a31d-122">**[ページの選択]** ペインの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a31d-122">In the **Select a page** pane, click **Options**.</span></span>  
  
     <span data-ttu-id="1a31d-123">**[互換性レベル]** ボックスの一覧に現在の互換性レベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a31d-123">The current compatibility level is displayed in the **Compatibility level** list box.</span></span>  
  
5.  <span data-ttu-id="1a31d-124">互換性レベルを変更するには、一覧から別のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="1a31d-124">To change the compatibility level, select a different option from the list.</span></span> <span data-ttu-id="1a31d-125">選択できるのは、 **[SQL Server 2008 (100)]**、 **[SQL Server 2012 (110)]**、 **[SQL Server 2014 (120)]** のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="1a31d-125">The choices are **SQL Server 2008 (100)**, **SQL Server 2012 (110)**, or **SQL Server 2014 (120)**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1a31d-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1a31d-126">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-compatibility-level-of-a-database"></a><span data-ttu-id="1a31d-127">データベースの互換性レベルを表示するには</span><span class="sxs-lookup"><span data-stu-id="1a31d-127">To view the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="1a31d-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="1a31d-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1a31d-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a31d-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1a31d-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a31d-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1a31d-131">この例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの互換性レベルを返します。</span><span class="sxs-lookup"><span data-stu-id="1a31d-131">This example returns the compatibility level of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="1a31d-132">データベースの互換性レベルを変更するには</span><span class="sxs-lookup"><span data-stu-id="1a31d-132">To change the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="1a31d-133">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="1a31d-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1a31d-134">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a31d-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1a31d-135">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a31d-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1a31d-136">この例では、の互換性レベルを変更 [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="1a31d-136">This example changes the compatibility level of the [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)].</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
  
