---
title: 主キーの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing primary keys
- deleting primary keys
- primary keys [SQL Server], deleting
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 44fa1271143f813364bfd2109f8147f1d04294a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646092"
---
# <a name="delete-primary-keys"></a><span data-ttu-id="1f152-102">主キーの削除</span><span class="sxs-lookup"><span data-stu-id="1f152-102">Delete Primary Keys</span></span>
  <span data-ttu-id="1f152-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して主キーを削除できます。</span><span class="sxs-lookup"><span data-stu-id="1f152-103">You can delete (drop) a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1f152-104">主キーを削除すると、対応するインデックスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1f152-104">When the primary key is deleted, the corresponding index is deleted.</span></span>  
  
 <span data-ttu-id="1f152-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1f152-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1f152-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1f152-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1f152-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1f152-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1f152-108">**主キー制約を削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="1f152-108">**To delete a primary key using:**</span></span>  
  
     [<span data-ttu-id="1f152-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1f152-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1f152-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f152-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1f152-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="1f152-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1f152-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1f152-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1f152-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="1f152-113">Permissions</span></span>  
 <span data-ttu-id="1f152-114">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="1f152-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1f152-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1f152-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint-using-object-explorer"></a><span data-ttu-id="1f152-116">オブジェクト エクスプローラーを使用して主キーを削除するには</span><span class="sxs-lookup"><span data-stu-id="1f152-116">To delete a primary key constraint using Object Explorer</span></span>  
  
1.  <span data-ttu-id="1f152-117">オブジェクト エクスプローラーで、主キーを含むテーブルを展開し、 **[キー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="1f152-117">In Object Explorer, expand the table that contains the primary key and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="1f152-118">キーを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f152-118">Right-click the key and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="1f152-119">**[オブジェクトの削除]** ダイアログ ボックスで正しいキーが指定されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f152-119">In the **Delete Object** dialog box, verify the correct key is specified and click **OK**.</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint-using-table-designer"></a><span data-ttu-id="1f152-120">テーブル デザイナーを使用して主キーを削除するには</span><span class="sxs-lookup"><span data-stu-id="1f152-120">To delete a primary key constraint using Table Designer</span></span>  
  
1.  <span data-ttu-id="1f152-121">オブジェクト エクスプローラーで、主キーが設定されたテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f152-121">In Object Explorer, right-click the table with the primary key, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="1f152-122">テーブル グリッドで、主キーを持つ行を右クリックし、 **[主キーの削除]** をクリックして、設定をオンからオフに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1f152-122">In the table grid, right-click the row with the primary key and choose **Remove Primary Key** to toggle the setting from on to off.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f152-123">この操作を元に戻すには、変更を保存せずにテーブルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1f152-123">To undo this action, close the table without saving the changes.</span></span> <span data-ttu-id="1f152-124">主キーの削除を元に戻すと、テーブルに対するその他の変更はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="1f152-124">Deleting a primary key cannot be undone without losing all other changes made to the table.</span></span>  
  
3.  <span data-ttu-id="1f152-125">**[ファイル]** メニューの **[ _<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f152-125">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1f152-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1f152-126">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint"></a><span data-ttu-id="1f152-127">主キー制約を削除するには</span><span class="sxs-lookup"><span data-stu-id="1f152-127">To delete a primary key constraint</span></span>  
  
1.  <span data-ttu-id="1f152-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1f152-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1f152-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f152-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1f152-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f152-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1f152-131">次の例では、まず主キー制約の名前を指定してから制約を削除します。</span><span class="sxs-lookup"><span data-stu-id="1f152-131">The example first identifies the name of the primary key constraint and then deletes the constraint.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 <span data-ttu-id="1f152-132">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」および「[sys.key_constraints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f152-132">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [sys.key_constraints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)</span></span>  
  
###  <a name="TsqlExample"></a>  
