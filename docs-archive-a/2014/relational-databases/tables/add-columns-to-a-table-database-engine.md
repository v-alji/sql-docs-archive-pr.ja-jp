---
title: テーブルへの列の追加 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7e9294de10be0df9ef470c75d0934e9f8787b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640843"
---
# <a name="add-columns-to-a-table-database-engine"></a><span data-ttu-id="ae5d1-102">テーブルへの列の追加 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="ae5d1-102">Add Columns to a Table (Database Engine)</span></span>
  <span data-ttu-id="ae5d1-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してテーブルに新しい列を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-103">This topic describes how to add new columns to a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ae5d1-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ae5d1-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ae5d1-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ae5d1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ae5d1-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ae5d1-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ae5d1-107">Security</span><span class="sxs-lookup"><span data-stu-id="ae5d1-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ae5d1-108">**列を挿入する方法:**</span><span class="sxs-lookup"><span data-stu-id="ae5d1-108">**To insert columns, using:**</span></span>  
  
     [<span data-ttu-id="ae5d1-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ae5d1-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ae5d1-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ae5d1-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ae5d1-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="ae5d1-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ae5d1-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ae5d1-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ae5d1-113">ALTER TABLE ステートメントを使用してテーブルに列を追加すると、これらの列は自動的にテーブルの最後に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-113">Using the ALTER TABLE statement to add columns to a table automatically adds those columns to the end of the table.</span></span> <span data-ttu-id="ae5d1-114">テーブル内の列を特定の順序で表示する場合は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-114">If you want the columns in a specific order in the table, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ae5d1-115">ただし、これはデータベース デザインのベスト プラクティスではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-115">However, note that this is not a database design best practice.</span></span> <span data-ttu-id="ae5d1-116">列が返される順序をアプリケーションおよびクエリ レベルで指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-116">Best practice is to specify the order in which the columns are returned at the application and query level.</span></span> <span data-ttu-id="ae5d1-117">テーブルで定義されている順序に基づいて、すべての列が予想される順序で返されるようにするために、SELECT \* の使用に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-117">You should not rely on the use of SELECT \* to return all columns in an expected order based on the order in which they are defined in the table.</span></span> <span data-ttu-id="ae5d1-118">クエリまたはアプリケーションでは必ず、表示される順序で列の名前を指定してください。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-118">Always specify the columns by name in your queries and applications in the order in which you would like them to appear.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ae5d1-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ae5d1-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ae5d1-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="ae5d1-120">Permissions</span></span>  
 <span data-ttu-id="ae5d1-121">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ae5d1-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ae5d1-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-insert-columns-into-a-table-with-table-designer"></a><span data-ttu-id="ae5d1-123">テーブル デザイナーでテーブルに列を挿入するには</span><span class="sxs-lookup"><span data-stu-id="ae5d1-123">To insert columns into a table with Table Designer</span></span>  
  
1.  <span data-ttu-id="ae5d1-124">**オブジェクト エクスプローラー**で、列を追加するテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-124">In **Object Explorer**, right-click the table to which you want to add columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="ae5d1-125">**[列名]** 列内の最初の空白セルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-125">Click in the first blank cell in the **Column Name** column.</span></span>  
  
3.  <span data-ttu-id="ae5d1-126">セルに列名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-126">Type the column name in the cell.</span></span> <span data-ttu-id="ae5d1-127">[列名] には値が必要です。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-127">The column name is a required value.</span></span>  
  
4.  <span data-ttu-id="ae5d1-128">Tab キーを押して **[データ型]** セルに移動し、ドロップダウンからデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-128">Press the TAB key to go to the **Data Type** cell and select a data type from the dropdown.</span></span> <span data-ttu-id="ae5d1-129">データ型も必須の値です。選択しない場合は既定の値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-129">This too is a required value, and will be assigned the default value if you don't choose one.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae5d1-130"> この既定の値は、 **[データベース ツール]** の下の **[オプション]** ダイアログ ボックスで変更できます。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-130">You can change the default value in the **Options** dialog box under **Database Tools**.</span></span>  
  
5.  <span data-ttu-id="ae5d1-131">次に **[列のプロパティ]** タブで他の列のプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-131">Continue to define any other column properties in the **Column Properties** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae5d1-132">新しい列の作成時には、列プロパティの既定の値が追加されますが、 **[列のプロパティ]** タブで値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-132">The default values for your column properties are added when you create a new column, but you can change them in the **Column Properties** tab.</span></span>  
  
6.  <span data-ttu-id="ae5d1-133">列の追加が完了したら、**[ファイル]** メニューで [_<テーブル名>_**を保存**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-133">When you are finished adding columns, from the **File** menu, choose **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ae5d1-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ae5d1-134">Using Transact-SQL</span></span>  
  
#### <a name="to-insert-columns-into-a-table"></a><span data-ttu-id="ae5d1-135">テーブルに列を挿入するには</span><span class="sxs-lookup"><span data-stu-id="ae5d1-135">To insert columns into a table</span></span>  
  
1.  <span data-ttu-id="ae5d1-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ae5d1-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ae5d1-138">次の例では、 `dbo.doc_exa`テーブルに列を 2 つ追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-138">The following example adds two columns to the table `dbo.doc_exa`.</span></span> <span data-ttu-id="ae5d1-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-139">Copy and paste the following example into the query window and click **Execute**</span></span>  
  
```  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;  
```  
  
##  <a name="for-more-information-see-alter-table-40transact-sql41"></a><a name="FollowUp"></a><span data-ttu-id="ae5d1-140">詳細については、「 [ALTER TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/alter-table-transact-sql) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae5d1-140">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span></span>  
  
  
