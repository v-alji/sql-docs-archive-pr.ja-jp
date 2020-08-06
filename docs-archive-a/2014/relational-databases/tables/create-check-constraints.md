---
title: CHECK 制約の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table constraints [SQL Server]
- attaching check constraints
- columns [SQL Server], constraints
- constraints [SQL Server], check
- CHECK constraints, attaching
ms.assetid: b8756304-9454-4d39-996a-64516831b7df
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7795ee6eca85a22bdd4e84c90ce49a9449ddff28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646104"
---
# <a name="create-check-constraints"></a><span data-ttu-id="671b2-102">CHECK 制約の作成</span><span class="sxs-lookup"><span data-stu-id="671b2-102">Create Check Constraints</span></span>
  <span data-ttu-id="671b2-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してテーブルで CHECK 制約を作成して、1 つ以上の列に入力できるデータ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="671b2-103">You can create a check constraint in a table to specify the data values that are acceptable in one or more columns in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="671b2-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="671b2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="671b2-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="671b2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="671b2-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="671b2-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="671b2-107">**新しい CHECK 制約を作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="671b2-107">**To create a new check constraint using:**</span></span>  
  
     [<span data-ttu-id="671b2-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="671b2-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="671b2-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="671b2-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="671b2-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="671b2-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="671b2-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="671b2-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="671b2-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="671b2-112">Permissions</span></span>  
 <span data-ttu-id="671b2-113">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="671b2-113">Requires ALTER permissions on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="671b2-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="671b2-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-new-check-constraint"></a><span data-ttu-id="671b2-115">新しい CHECK 制約を作成するには</span><span class="sxs-lookup"><span data-stu-id="671b2-115">To create a new check constraint</span></span>  
  
1.  <span data-ttu-id="671b2-116">**オブジェクト エクスプローラー**で、CHECK 制約を追加するテーブルを展開し、 **[制約]** を右クリックして、 **[新しい制約]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="671b2-116">In **Object Explorer**, expand the table to which you want to add a check constraint, right-click **Constraints** and click **New Constraint**.</span></span>  
  
2.  <span data-ttu-id="671b2-117">**[CHECK 制約]** ダイアログ ボックスで、 **[式]** フィールドをクリックして、省略記号 **[...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="671b2-117">In the **Check Constraints** dialog box, click in the **Expression** field and then click the ellipses **(...)**.</span></span>  
  
3.  <span data-ttu-id="671b2-118">**[CHECK 制約式]** ダイアログ ボックスで、CHECK 制約の SQL 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="671b2-118">In the **Check Constraint Expression** dialog box, type the SQL expressions for the check constraint.</span></span> <span data-ttu-id="671b2-119">たとえば、 `SellEndDate` テーブルの `Product` 列への入力を `SellStartDate` 列の日付と同じか、それよりも後の日付の値または NULL 値に限定するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="671b2-119">For example, to limit the entries in the `SellEndDate` column of the `Product` table to a value that is either greater than or equal to the date in the `SellStartDate` column or is a NULL value, type:</span></span>  
  
    ```  
    SellEndDate >= SellStartDate OR SellEndDate IS NULL  
    ```  
  
     <span data-ttu-id="671b2-120">また、 `zip` 列への入力を 5 桁の数値に限定するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="671b2-120">Or, to require entries in the `zip` column to be 5 digits, type:</span></span>  
  
    ```  
    zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="671b2-121">数値以外の制約値は、必ず単一引用符 (') で囲んでください。</span><span class="sxs-lookup"><span data-stu-id="671b2-121">Make sure to enclose any non-numeric constraint values in single quotation marks (').</span></span>  
  
4.  <span data-ttu-id="671b2-122">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="671b2-122">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="671b2-123">**[ID]** カテゴリでは、CHECK 制約の名前を変更し、制約の説明 (拡張プロパティ) を追加できます。</span><span class="sxs-lookup"><span data-stu-id="671b2-123">In the **Identity** category, you can change the name of the check constraint and add a description (extended property) for the constraint.</span></span>  
  
6.  <span data-ttu-id="671b2-124">**テーブル デザイナー** のカテゴリでは、制約が適用されるタイミングを設定できます。</span><span class="sxs-lookup"><span data-stu-id="671b2-124">In the **Table Designer** category, you can set when the constraint is enforced.</span></span>  
  
    |<span data-ttu-id="671b2-125">**To:**</span><span class="sxs-lookup"><span data-stu-id="671b2-125">**To:**</span></span>|<span data-ttu-id="671b2-126">**[はい] を選択するフィールド:**</span><span class="sxs-lookup"><span data-stu-id="671b2-126">**Select Yes in the Following Fields:**</span></span>|  
    |-------------|---------------------------------------------|  
    |<span data-ttu-id="671b2-127">制約を作成する前に既に存在していたデータで制約をテストする</span><span class="sxs-lookup"><span data-stu-id="671b2-127">Test the constraint on data that existed before you created the constraint</span></span>|<span data-ttu-id="671b2-128">**[作成または有効化するときに既存データを確認]**</span><span class="sxs-lookup"><span data-stu-id="671b2-128">**Check Existing Data On Creation Or Enabling**</span></span>|  
    |<span data-ttu-id="671b2-129">このテーブルでレプリケーション操作が発生するたびに制約を適用する</span><span class="sxs-lookup"><span data-stu-id="671b2-129">Enforce the constraint whenever a replication operation occurs on this table</span></span>|<span data-ttu-id="671b2-130">**[レプリケーションに対して適用]**</span><span class="sxs-lookup"><span data-stu-id="671b2-130">**Enforce For Replication**</span></span>|  
    |<span data-ttu-id="671b2-131">このテーブルの行を挿入または更新するたびに制約を適用する</span><span class="sxs-lookup"><span data-stu-id="671b2-131">Enforce the constraint whenever a row of this table is inserted or updated</span></span>|<span data-ttu-id="671b2-132">**[INSERT および UPDATE に適用]**</span><span class="sxs-lookup"><span data-stu-id="671b2-132">**Enforce For INSERTs And UPDATEs**</span></span>|  
  
7.  <span data-ttu-id="671b2-133">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="671b2-133">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="671b2-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="671b2-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-new-check-constraint"></a><span data-ttu-id="671b2-135">新しい CHECK 制約を作成するには</span><span class="sxs-lookup"><span data-stu-id="671b2-135">To create a new check constraint</span></span>  
  
1.  <span data-ttu-id="671b2-136">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="671b2-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="671b2-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="671b2-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="671b2-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="671b2-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER TABLE dbo.DocExc   
       ADD ColumnD int NULL   
       CONSTRAINT CHK_ColumnD_DocExc   
       CHECK (ColumnD > 10 AND ColumnD < 50);  
    GO  
    -- Adding values that will pass the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (49);  
    GO  
    -- Adding values that will fail the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (55);  
    GO  
  
    ```  
  
 <span data-ttu-id="671b2-139">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="671b2-139">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
