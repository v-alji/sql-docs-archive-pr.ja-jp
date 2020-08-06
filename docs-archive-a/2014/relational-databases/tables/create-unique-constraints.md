---
title: UNIQUE 制約の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], creating
- constraints [SQL Server], unique
ms.assetid: a86f9d6f-f242-43be-b65d-b3435b71b62a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 252de63f965f98734a6d62d94bfff9dc5774cab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738167"
---
# <a name="create-unique-constraints"></a><span data-ttu-id="e6e45-102">UNIQUE 制約の作成</span><span class="sxs-lookup"><span data-stu-id="e6e45-102">Create Unique Constraints</span></span>
  <span data-ttu-id="e6e45-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して UNIQUE 制約を作成し、主キー以外の特定の列に重複した値が入力されないようにします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-103">You can create a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] to ensure no duplicate values are entered in specific columns that do not participate in a primary key.</span></span> <span data-ttu-id="e6e45-104">UNIQUE 制約を作成すると、対応する一意なインデックスが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6e45-104">Creating a unique constraint automatically creates a corresponding unique index.</span></span>  
  
 <span data-ttu-id="e6e45-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e6e45-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e6e45-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e6e45-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e6e45-107">Security</span><span class="sxs-lookup"><span data-stu-id="e6e45-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e6e45-108">**UNIQUE 制約を作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="e6e45-108">**To create a unique constraint, using:**</span></span>  
  
     [<span data-ttu-id="e6e45-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e6e45-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e6e45-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6e45-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e6e45-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="e6e45-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e6e45-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e6e45-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e6e45-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="e6e45-113">Permissions</span></span>  
 <span data-ttu-id="e6e45-114">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e6e45-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e6e45-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e6e45-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-unique-constraint"></a><span data-ttu-id="e6e45-116">UNIQUE 制約を作成するには</span><span class="sxs-lookup"><span data-stu-id="e6e45-116">To create a unique constraint</span></span>  
  
1.  <span data-ttu-id="e6e45-117">**オブジェクト エクスプローラー**で、UNIQUE 制約を追加するテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-117">In **Object Explorer**, right-click the table to which you want to add a unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="e6e45-118">[**テーブルデザイナー** ] メニューの [**インデックス/キー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-118">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
3.  <span data-ttu-id="e6e45-119">**[インデックス/キー]** ダイアログ ボックスで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-119">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="e6e45-120">**[全般]** の下のグリッドで、 **[型]** をクリックし、プロパティの右にあるドロップダウン リスト ボックスの **[一意キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-120">In the grid under **General**, click **Type** and choose **Unique Key** from the drop-down list box to the right of the property.</span></span>  
  
5.  <span data-ttu-id="e6e45-121">**[ファイル]** メニューの **[_<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-121">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e6e45-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e6e45-122">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-unique-constraint"></a><span data-ttu-id="e6e45-123">UNIQUE 制約を作成するには</span><span class="sxs-lookup"><span data-stu-id="e6e45-123">To create a unique constraint</span></span>  
  
1.  <span data-ttu-id="e6e45-124">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6e45-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6e45-125">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e6e45-126">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-126">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e6e45-127">次の例では、 `TransactionHistoryArchive4` テーブルを作成して `TransactionID`列に UNIQUE 制約を作成します。</span><span class="sxs-lookup"><span data-stu-id="e6e45-127">The example creates the table `TransactionHistoryArchive4` and creates a unique constraint on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive4  
     (  
       TransactionID int NOT NULL,   
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)   
    );   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-on-an-existing-table"></a><span data-ttu-id="e6e45-128">既存のテーブルに UNIQUE 制約を作成するには</span><span class="sxs-lookup"><span data-stu-id="e6e45-128">To create a unique constraint on an existing table</span></span>  
  
1.  <span data-ttu-id="e6e45-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6e45-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6e45-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e6e45-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-131">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e6e45-132">次の例では、`Person.Password` テーブルの `PasswordHash` および `PasswordSalt` 列に UNIQUE 制約を作成します。</span><span class="sxs-lookup"><span data-stu-id="e6e45-132">The example creates a unique constraint on the columns `PasswordHash` and `PasswordSalt` in the table `Person.Password`.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    ALTER TABLE Person.Password   
    ADD CONSTRAINT AK_Password UNIQUE (PasswordHash, PasswordSalt);   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-in-an-new-table"></a><span data-ttu-id="e6e45-133">新しいテーブルに UNIQUE 制約を作成するには</span><span class="sxs-lookup"><span data-stu-id="e6e45-133">To create a unique constraint in an new table</span></span>  
  
1.  <span data-ttu-id="e6e45-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6e45-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6e45-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e6e45-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6e45-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e6e45-137">次の例では、テーブルを作成して `TransactionID`列に UNIQUE 制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="e6e45-137">The example creates a table and defines a unique constraint on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive2  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)  
    );  
    GO  
  
    ```  
  
     <span data-ttu-id="e6e45-138">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」、「[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)」、および「[table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6e45-138">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
