---
title: 主キーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
author: stevestein
ms.author: sstein
ms.openlocfilehash: c515ef8f978b41225ff45e87646b0aa7a9706a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646101"
---
# <a name="create-primary-keys"></a><span data-ttu-id="da3f0-102">主キーの作成</span><span class="sxs-lookup"><span data-stu-id="da3f0-102">Create Primary Keys</span></span>
  <span data-ttu-id="da3f0-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して主キーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="da3f0-103">You can define a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="da3f0-104">主キーを作成すると、対応する一意なクラスター化または非クラスター化インデックスが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="da3f0-104">Creating a primary key automatically creates a corresponding unique, clustered or nonclustered index.</span></span>  
  
 <span data-ttu-id="da3f0-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="da3f0-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="da3f0-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="da3f0-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="da3f0-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="da3f0-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="da3f0-108">Security</span><span class="sxs-lookup"><span data-stu-id="da3f0-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="da3f0-109">**主キーを変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="da3f0-109">**To create a primary key, using:**</span></span>  
  
     [<span data-ttu-id="da3f0-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="da3f0-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="da3f0-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="da3f0-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="da3f0-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="da3f0-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="da3f0-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="da3f0-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="da3f0-114">テーブルに含めることができる PRIMARY KEY 制約は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="da3f0-114">A table can contain only one PRIMARY KEY constraint.</span></span>  
  
-   <span data-ttu-id="da3f0-115">PRIMARY KEY 制約中で定義する列はすべて、NOT NULL として定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da3f0-115">All columns defined within a PRIMARY KEY constraint must be defined as NOT NULL.</span></span> <span data-ttu-id="da3f0-116">NULL 値を許容するかどうかを指定しない場合、PRIMARY KEY 制約の影響を受けるすべての列は NOT NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="da3f0-116">If nullability is not specified, all columns participating in a PRIMARY KEY constraint have their nullability set to NOT NULL.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="da3f0-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="da3f0-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="da3f0-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="da3f0-118">Permissions</span></span>  
 <span data-ttu-id="da3f0-119">主キーが設定された、新しいテーブルを作成するには、データベースの CREATE TABLE 権限と、テーブルを作成するスキーマの ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="da3f0-119">Creating a new table with a primary key requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>  
  
 <span data-ttu-id="da3f0-120">既存のテーブルに主キーを作成するには、テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="da3f0-120">Creating a primary key in an existing table requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="da3f0-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="da3f0-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-primary-key"></a><span data-ttu-id="da3f0-122">主キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="da3f0-122">To create a primary key</span></span>  
  
1.  <span data-ttu-id="da3f0-123">オブジェクトエクスプローラーで、unique 制約を追加するテーブルを右クリックし、[**デザイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da3f0-123">In Object Explorer, right-click the table to which you want to add a unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="da3f0-124">**テーブル デザイナー**で、主キーとして定義するデータベース列の行セレクターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="da3f0-124">In **Table Designer**, click the row selector for the database column you want to define as the primary key.</span></span> <span data-ttu-id="da3f0-125">複数列を選択する場合は、Ctrl キーを押しながら、他の列の行セレクターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="da3f0-125">If you want to select multiple columns, hold down the CTRL key while you click the row selectors for the other columns.</span></span>  
  
3.  <span data-ttu-id="da3f0-126">列の行セレクターを右クリックし、 **[主キーの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da3f0-126">Right-click the row selector for the column and select **Set Primary Key**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="da3f0-127">主キーを再定義する場合は、新しい主キーを作成する前に、既存の主キーに対するリレーションシップをすべて削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da3f0-127">If you want to redefine the primary key, any relationships to the existing primary key must be deleted before the new primary key can be created.</span></span> <span data-ttu-id="da3f0-128">再定義中に、既存のリレーションシップが自動的に削除されることを警告するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da3f0-128">A message will warn you that existing relationships will be automatically deleted as part of this process.</span></span>  
  
 <span data-ttu-id="da3f0-129">主キー列は、行セレクターに主キーの記号で示されます。</span><span class="sxs-lookup"><span data-stu-id="da3f0-129">A primary key column is identified by a primary key symbol in its row selector.</span></span>  
  
 <span data-ttu-id="da3f0-130">主キーが複数の列で構成される場合、1 つの列では重複した値が許可されますが、主キーのすべての列の値の組み合わせは一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="da3f0-130">If a primary key consists of more than one column, duplicate values are allowed in one column, but each combination of values from all the columns in the primary key must be unique.</span></span>  
  
 <span data-ttu-id="da3f0-131">複合キーを定義する場合は、主キーの列の順序が、テーブルに表示される列の順序と同じになります。</span><span class="sxs-lookup"><span data-stu-id="da3f0-131">If you define a compound key, the order of columns in the primary key matches the order of columns as shown in the table.</span></span> <span data-ttu-id="da3f0-132">ただし、主キー作成後に列の順序を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="da3f0-132">However, you can change the order of columns after the primary key is created.</span></span> <span data-ttu-id="da3f0-133">詳細については、「 [主キーの変更](modify-primary-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da3f0-133">For more information, see [Modify Primary Keys](modify-primary-keys.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="da3f0-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="da3f0-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-primary-key-in-an-existing-table"></a><span data-ttu-id="da3f0-135">既存のテーブルに主キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="da3f0-135">To create a primary key in an existing table</span></span>  
  
1.  <span data-ttu-id="da3f0-136">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="da3f0-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="da3f0-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da3f0-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="da3f0-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da3f0-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="da3f0-139">この例では、 `TransactionID`列で主キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="da3f0-139">The example creates a primary key on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
  
    ```  
  
#### <a name="to-create-a-primary-key-in-a-new-table"></a><span data-ttu-id="da3f0-140">新しいテーブルに主キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="da3f0-140">To create a primary key in a new table</span></span>  
  
1.  <span data-ttu-id="da3f0-141">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="da3f0-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="da3f0-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da3f0-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="da3f0-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da3f0-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="da3f0-144">次の例では、テーブルを作成して `TransactionID`列に主キーを定義します。</span><span class="sxs-lookup"><span data-stu-id="da3f0-144">The example creates a table and defines a primary key on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
  
    ```  
  
     <span data-ttu-id="da3f0-145">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」、「[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)」、および「[table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da3f0-145">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
