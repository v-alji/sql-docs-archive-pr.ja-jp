---
title: 列の変更 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: a73c25d91b742f1cc1f7edcc8a95cdf226b2683c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641993"
---
# <a name="modify-columns-database-engine"></a><span data-ttu-id="3f311-102">列の変更 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="3f311-102">Modify Columns (Database Engine)</span></span>
  <span data-ttu-id="3f311-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して列のデータ型を変更できます。</span><span class="sxs-lookup"><span data-stu-id="3f311-103">You can modify the data type of a column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="3f311-104">既にデータが格納されている列のデータ型を変更すると、既存のデータが新しい型に変換される時点で、それらのデータは完全に失われます。</span><span class="sxs-lookup"><span data-stu-id="3f311-104">Modifying the data type of a column that already contains data can result in the permanent loss of data when the existing data is converted to the new type.</span></span> <span data-ttu-id="3f311-105">さらに、変更した列に依存しているコードやアプリケーションも正常に動作しなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f311-105">In addition, code and applications that depend on the modified column may fail.</span></span> <span data-ttu-id="3f311-106">これには、クエリ、ビュー、ストアド プロシージャ、ユーザー定義関数、およびクライアント アプリケーションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3f311-106">These include queries, views, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="3f311-107">このようなエラーは連鎖するので注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="3f311-107">Note that these failures will cascade.</span></span> <span data-ttu-id="3f311-108">たとえば、変更した列に依存しているユーザー定義関数を呼び出すストアド プロシージャは、正常に動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f311-108">For example, a stored procedure that calls a user-defined function that depends on the modified column may fail.</span></span> <span data-ttu-id="3f311-109">列に対して変更を行う場合は、よく考えてから行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f311-109">Carefully consider any changes you want to make to a column before making it.</span></span>  
  
 <span data-ttu-id="3f311-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="3f311-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3f311-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3f311-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3f311-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3f311-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3f311-113">**列のデータ型を変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="3f311-113">**To modify the data type of a column, using:**</span></span>  
  
     [<span data-ttu-id="3f311-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3f311-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3f311-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3f311-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3f311-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="3f311-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3f311-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3f311-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3f311-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="3f311-118">Permissions</span></span>  
 <span data-ttu-id="3f311-119">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3f311-119">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3f311-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3f311-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-data-type-of-a-column"></a><span data-ttu-id="3f311-121">列のデータ型を変更するには</span><span class="sxs-lookup"><span data-stu-id="3f311-121">To modify the data type of a column</span></span>  
  
1.  <span data-ttu-id="3f311-122">**オブジェクト エクスプローラー**で、有効桁数を変更する列が含まれているテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f311-122">In **Object Explorer**, right-click the table with columns for which you want to change the scale and click **Design**.</span></span>  
  
2.  <span data-ttu-id="3f311-123">データ型を変更する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f311-123">Select the column for which you want to modify the data type.</span></span>  
  
3.  <span data-ttu-id="3f311-124">**[列のプロパティ]** タブで、 **[データ型]** プロパティのグリッド セルをクリックし、ドロップダウン リストから新しいデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f311-124">In the **Column Properties** tab, click the grid cell for the **Data Type** property and choose a new data type from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="3f311-125">**[ファイル]** メニューの **[ _<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f311-125">On the **File** menu, click **Save**_table name_.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f311-126">列のデータ型を変更すると、テーブル デザイナーでは選択したデータ型の既定の長さが適用されます。これは既に別の長さを選択していた場合でも同じです。</span><span class="sxs-lookup"><span data-stu-id="3f311-126">When you modify the data type of a column, Table Designer applies the default length of the data type you selected, even if you have already specified another.</span></span> <span data-ttu-id="3f311-127">データ型の指定後、必要な値を格納できるようにするために、データ型に適切な長さを設定してください。</span><span class="sxs-lookup"><span data-stu-id="3f311-127">Always set the data type length for to the desired value after specifying the data type.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="3f311-128">別のテーブルに関連付けられている列のデータ型を変更しようとすると、別のテーブルの列にも変更が行われることを確認するメッセージがテーブル デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f311-128">If you attempt to modify the data type of a column that relates to other tables, Table Designer asks you to confirm that the change should be made to the columns in the other tables as well.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3f311-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3f311-129">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-the-data-type-of-a-column"></a><span data-ttu-id="3f311-130">列のデータ型を変更するには</span><span class="sxs-lookup"><span data-stu-id="3f311-130">To modify the data type of a column</span></span>  
  
1.  <span data-ttu-id="3f311-131">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3f311-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3f311-132">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f311-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3f311-133">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f311-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 <span data-ttu-id="3f311-134">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f311-134">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span></span>  
  
  
