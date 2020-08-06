---
title: インデックスの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- dropping indexes
- indexes [SQL Server], dropping
- index deletions [SQL Server]
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4552ba701782e5790f95f54c0c1c66f82573f1e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740933"
---
# <a name="delete-an-index"></a><span data-ttu-id="8a123-102">インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="8a123-102">Delete an Index</span></span>
  <span data-ttu-id="8a123-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、インデックスを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a123-103">This topic describes how to delete (drop) an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8a123-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="8a123-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8a123-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="8a123-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8a123-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="8a123-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8a123-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8a123-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8a123-108">**以下を使用してインデックスを削除するには:**</span><span class="sxs-lookup"><span data-stu-id="8a123-108">**To delete an index, using:**</span></span>  
  
     [<span data-ttu-id="8a123-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8a123-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8a123-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8a123-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8a123-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="8a123-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8a123-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="8a123-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8a123-113">PRIMARY KEY 制約または UNIQUE 制約の結果として作成されたインデックスは、この方法を使用して削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="8a123-113">Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be deleted by using this method.</span></span> <span data-ttu-id="8a123-114">このような場合には、制約を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a123-114">Instead, the constraint must be deleted.</span></span> <span data-ttu-id="8a123-115">制約および対応するインデックスを削除するには、 [から、](/sql/t-sql/statements/alter-table-transact-sql) ALTER TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)]を DROP CONSTRAINT 句と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="8a123-115">To remove the constraint and corresponding index, use [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) with the DROP CONSTRAINT clause in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8a123-116">詳細については、「 [Delete Primary Keys](../tables/delete-primary-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a123-116">For more information, see [Delete Primary Keys](../tables/delete-primary-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8a123-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8a123-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8a123-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="8a123-118">Permissions</span></span>  
 <span data-ttu-id="8a123-119">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8a123-119">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="8a123-120">この権限は、固定サーバー ロール **sysadmin** と、固定データベース ロール **db_ddladmin** および **db_owner** に既定で許可されています。</span><span class="sxs-lookup"><span data-stu-id="8a123-120">This permission is granted by default to the **sysadmin** fixed server role and the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8a123-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="8a123-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-index-by-using-object-explorer"></a><span data-ttu-id="8a123-122">オブジェクト エクスプローラーを使用してインデックスを削除するには</span><span class="sxs-lookup"><span data-stu-id="8a123-122">To delete an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="8a123-123">オブジェクト エクスプローラーで、インデックスを削除するテーブルが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="8a123-123">In Object Explorer, expand the database that contains the table on which you want to delete an index.</span></span>  
  
2.  <span data-ttu-id="8a123-124">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8a123-124">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="8a123-125">削除するインデックスを含むテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="8a123-125">Expand the table that contains the index you want to delete.</span></span>  
  
4.  <span data-ttu-id="8a123-126">**[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8a123-126">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="8a123-127">削除するインデックスを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a123-127">Right-click the index you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="8a123-128">**[オブジェクトの削除]** ダイアログ ボックスで、 **[削除されるオブジェクト]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a123-128">In the **Delete Object** dialog box, verify that the correct index is in the **Object to be deleted** grid and click **OK**.</span></span>  
  
#### <a name="to-delete-an-index-using-table-designer"></a><span data-ttu-id="8a123-129">テーブル デザイナーを使用してインデックスを削除するには</span><span class="sxs-lookup"><span data-stu-id="8a123-129">To delete an index using Table Designer</span></span>  
  
1.  <span data-ttu-id="8a123-130">オブジェクト エクスプローラーで、インデックスを削除するテーブルが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="8a123-130">In Object Explorer, expand the database that contains the table on which you want to delete an index.</span></span>  
  
2.  <span data-ttu-id="8a123-131">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8a123-131">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="8a123-132">削除するインデックスのあるテーブルを右クリックし、[デザイン] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a123-132">Right-click the table that contains the index you want to delete and click Design.</span></span>  
  
4.  <span data-ttu-id="8a123-133">**[テーブル デザイナー]** メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a123-133">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="8a123-134">**[インデックス/キー]** ダイアログ ボックスで、削除するインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a123-134">In the **Indexes/Keys** dialog box, select the index you want to delete.</span></span>  
  
6.  <span data-ttu-id="8a123-135">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a123-135">Click **Delete**.</span></span>  
  
7.  <span data-ttu-id="8a123-136">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a123-136">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="8a123-137">**ファイル** メニューの **table_name**_を保存_を選びます。</span><span class="sxs-lookup"><span data-stu-id="8a123-137">On the **File** menu, select **Save**_table_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8a123-138">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="8a123-138">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-index"></a><span data-ttu-id="8a123-139">インデックスを削除するには</span><span class="sxs-lookup"><span data-stu-id="8a123-139">To delete an index</span></span>  
  
1.  <span data-ttu-id="8a123-140">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8a123-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8a123-141">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a123-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8a123-142">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a123-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 <span data-ttu-id="8a123-143">詳細については、「[DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a123-143">For more information, see [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql).</span></span>  
  
  
