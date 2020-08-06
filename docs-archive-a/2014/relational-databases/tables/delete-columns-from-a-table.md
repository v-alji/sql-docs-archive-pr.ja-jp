---
title: テーブルからの列の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 62f9bca8ee53ae97bb1ac7f37e597b7814a0c370
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641995"
---
# <a name="delete-columns-from-a-table"></a><span data-ttu-id="17c09-102">テーブルからの列の削除</span><span class="sxs-lookup"><span data-stu-id="17c09-102">Delete Columns from a Table</span></span>
  <span data-ttu-id="17c09-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してテーブル列を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="17c09-103">This topic describes how to delete table columns in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="17c09-104">テーブルから列を削除すると、列および列に含まれているすべてのデータがデータベースから削除されます。</span><span class="sxs-lookup"><span data-stu-id="17c09-104">When you delete a column from a table, it and all the data it contains are deleted from the database.</span></span> <span data-ttu-id="17c09-105">この削除操作は元に戻すことができません。</span><span class="sxs-lookup"><span data-stu-id="17c09-105">This action cannot be undone.</span></span>  
  
 <span data-ttu-id="17c09-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="17c09-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="17c09-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="17c09-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="17c09-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="17c09-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="17c09-109">Security</span><span class="sxs-lookup"><span data-stu-id="17c09-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="17c09-110">**テーブルから列を削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="17c09-110">**To delete a column from a table, using:**</span></span>  
  
     [<span data-ttu-id="17c09-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="17c09-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="17c09-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="17c09-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="17c09-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="17c09-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="17c09-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="17c09-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="17c09-115">CHECK 制約がある列を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="17c09-115">You cannot delete a column that has a CHECK constraint.</span></span> <span data-ttu-id="17c09-116">最初に制約を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17c09-116">You must first delete the constraint.</span></span>  
  
 <span data-ttu-id="17c09-117">テーブル デザイナーを使用する場合を除き、PRIMARY KEY 制約、FOREIGN KEY 制約、またはその他の依存関係がある列を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="17c09-117">You cannot delete a column that has PRIMARY KEY or FOREIGN KEY constraints or other dependencies except when using the Table Designer.</span></span> <span data-ttu-id="17c09-118">オブジェクト エクスプローラーまたは [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用する場合、最初に列のすべての依存関係を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17c09-118">When using Object Explorer or [!INCLUDE[tsql](../../includes/tsql-md.md)], you must first remove all dependencies on the column.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="17c09-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="17c09-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="17c09-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="17c09-120">Permissions</span></span>  
 <span data-ttu-id="17c09-121">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="17c09-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="17c09-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="17c09-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a><span data-ttu-id="17c09-123">オブジェクト エクスプローラーを使用して列を削除するには</span><span class="sxs-lookup"><span data-stu-id="17c09-123">To delete columns by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="17c09-124">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="17c09-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="17c09-125">**オブジェクト エクスプローラー**で、列を削除するテーブルを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17c09-125">In **Object Explorer**, right-click the table from which you want to delete columns and choose **Delete**.</span></span>  
  
3.  <span data-ttu-id="17c09-126">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17c09-126">In **Delete Object** dialog box, click **OK**.</span></span>  
  
 <span data-ttu-id="17c09-127">列に制約またはその他の依存関係が含まれている場合は、 **[オブジェクトの削除]** ダイアログ ボックスにエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17c09-127">If the column contains constraints or other dependencies, an error message will display in the **Delete Object** dialog box.</span></span> <span data-ttu-id="17c09-128">参照制約を削除することによって、エラーを解決します。</span><span class="sxs-lookup"><span data-stu-id="17c09-128">Resolve the error by deleting the referenced constraints.</span></span>  
  
#### <a name="to-delete-columns-by-using-table-designer"></a><span data-ttu-id="17c09-129">テーブル デザイナーを使用して列を削除するには</span><span class="sxs-lookup"><span data-stu-id="17c09-129">To delete columns by using Table Designer</span></span>  
  
1.  <span data-ttu-id="17c09-130">**オブジェクト エクスプローラー**で、列を削除するテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17c09-130">In **Object Explorer**, right-click the table from which you want to delete columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="17c09-131">削除する列を右クリックし、ショートカット メニューの **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17c09-131">Right-click the column you want to delete and choose **Delete Column** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="17c09-132">列にリレーションシップ (FOREIGN KEY または PRIMARY KEY) が適用されている場合は、選択した列および列のリレーションシップの削除を確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17c09-132">If the column participates in a relationship (FOREIGN KEY or PRIMARY KEY), a message prompts you to confirm the deletion of the selected columns and their relationships.</span></span> <span data-ttu-id="17c09-133">**[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17c09-133">Choose **Yes**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="17c09-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="17c09-134">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-columns"></a><span data-ttu-id="17c09-135">列を削除するには</span><span class="sxs-lookup"><span data-stu-id="17c09-135">To delete columns</span></span>  
  
1.  <span data-ttu-id="17c09-136">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="17c09-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="17c09-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17c09-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="17c09-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17c09-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 <span data-ttu-id="17c09-139">列に制約またはその他の依存関係が含まれている場合は、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="17c09-139">If the column contains constraints or other dependencies, an error message will be returned.</span></span> <span data-ttu-id="17c09-140">参照制約を削除することによって、エラーを解決します。</span><span class="sxs-lookup"><span data-stu-id="17c09-140">Resolve the error by deleting the referenced constraints.</span></span>  
  
 <span data-ttu-id="17c09-141">例については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17c09-141">For additional examples, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
##  <a name="FollowUp"></a>  
