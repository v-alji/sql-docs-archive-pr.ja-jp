---
title: UNIQUE 制約の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- UNIQUE constraints [SQL Server], deleting
- constraints [SQL Server], deleting
- deleting constraints
- constraints [SQL Server], unique
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2fe2264aed4eb2f292a6bd1e4e565cebe2a833f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642663"
---
# <a name="delete-unique-constraints"></a><span data-ttu-id="85136-102">UNIQUE 制約の削除</span><span class="sxs-lookup"><span data-stu-id="85136-102">Delete Unique Constraints</span></span>
  <span data-ttu-id="85136-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して UNIQUE 制約を削除できます。</span><span class="sxs-lookup"><span data-stu-id="85136-103">You can delete a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="85136-104">UNIQUE 制約を削除すると、制約式に含まれる 1 つ以上の列に入力される値に対する一意性の条件が取り除かれ、対応する一意なインデックスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="85136-104">Deleting a unique constraint removes the requirement for uniqueness for values entered in the column or combination of columns included in the constraint expression and deletes the corresponding unique index.</span></span>  
  
 <span data-ttu-id="85136-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="85136-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="85136-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="85136-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="85136-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="85136-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="85136-108">**UNIQUE 制約を削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="85136-108">**To delete a unique constraint, using:**</span></span>  
  
     [<span data-ttu-id="85136-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="85136-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="85136-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="85136-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="85136-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="85136-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="85136-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="85136-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="85136-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="85136-113">Permissions</span></span>  
 <span data-ttu-id="85136-114">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="85136-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="85136-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="85136-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-unique-constraint-using-object-explorer"></a><span data-ttu-id="85136-116">オブジェクト エクスプローラーを使用して UNIQUE 制約を削除するには</span><span class="sxs-lookup"><span data-stu-id="85136-116">To delete a unique constraint using Object Explorer</span></span>  
  
1.  <span data-ttu-id="85136-117">オブジェクト エクスプローラーで、UNIQUE 制約を含むテーブルを展開し、 **[制約]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="85136-117">In Object Explorer, expand the table that contains the unique constraint and then expand **Constraints**.</span></span>  
  
2.  <span data-ttu-id="85136-118">キーを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-118">Right-click the key and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="85136-119">**[オブジェクトの削除]** ダイアログ ボックスで正しいキーが指定されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-119">In the **Delete Object** dialog box, verify the correct key is specified and click **OK**.</span></span>  
  
#### <a name="to-delete-a-unique-constraint-using-table-designer"></a><span data-ttu-id="85136-120">テーブル デザイナーを使用して UNIQUE 制約を削除するには</span><span class="sxs-lookup"><span data-stu-id="85136-120">To delete a unique constraint using Table Designer</span></span>  
  
1.  <span data-ttu-id="85136-121">**オブジェクト エクスプローラー**で、UNIQUE 制約が設定されたテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-121">In **Object Explorer**, right-click the table with the unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="85136-122">**[テーブル デザイナー]** メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-122">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
3.  <span data-ttu-id="85136-123">**[インデックス/キー]** ダイアログ ボックスの **[Selected Primary/Unique Key and Index (選択された主/一意キーまたはインデックス)]** ボックスの一意キーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-123">In the **Indexes/Keys** dialog box, select the unique key in the **Selected Primary/Unique Key and Index** list.</span></span>  
  
4.  <span data-ttu-id="85136-124">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-124">Click **Delete**.</span></span>  
  
5.  <span data-ttu-id="85136-125">**[ファイル]** メニューの **[** <テーブル名> _を保存]_ をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-125">On the **File** menu, click **Save** _table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="85136-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="85136-126">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-unique-constraint"></a><span data-ttu-id="85136-127">UNIQUE 制約を削除するには</span><span class="sxs-lookup"><span data-stu-id="85136-127">To delete a unique constraint</span></span>  
  
1.  <span data-ttu-id="85136-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="85136-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="85136-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="85136-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85136-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 <span data-ttu-id="85136-131">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」および「[sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85136-131">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
