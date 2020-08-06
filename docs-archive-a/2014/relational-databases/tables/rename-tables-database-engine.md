---
title: テーブル名の変更 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e73bbb92d8fd3fdcaa7756ce1dcb74d8cd598b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643720"
---
# <a name="rename-tables-database-engine"></a><span data-ttu-id="4d0c2-102">テーブル名の変更 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="4d0c2-102">Rename Tables (Database Engine)</span></span>
  <span data-ttu-id="4d0c2-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してテーブルの名前を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-103">You can rename a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="4d0c2-104">テーブル名の変更については、十分に検討してください。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-104">Think carefully before you rename a table.</span></span> <span data-ttu-id="4d0c2-105">そのテーブルを参照するクエリ、ビュー、ユーザー定義関数、ストアド プロシージャ、またはプログラムが存在する場合、テーブル名を変更すると、各オブジェクトが無効になります。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-105">If existing queries, views, user-defined functions, stored procedures, or programs refer to that table, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="4d0c2-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4d0c2-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4d0c2-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4d0c2-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4d0c2-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4d0c2-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4d0c2-109">Security</span><span class="sxs-lookup"><span data-stu-id="4d0c2-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4d0c2-110">**テーブル名を変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="4d0c2-110">**To rename a table, using:**</span></span>  
  
     [<span data-ttu-id="4d0c2-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d0c2-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4d0c2-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d0c2-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4d0c2-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="4d0c2-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4d0c2-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4d0c2-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="4d0c2-115">テーブル名を変更しても、そのテーブルに対する参照の名前は自動的には変更されません。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-115">Renaming a table will not automatically rename references to that table.</span></span> <span data-ttu-id="4d0c2-116">名前を変更したテーブルを参照しているオブジェクトに対しては、手動で変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-116">You must manually modify any objects that reference the renamed table.</span></span> <span data-ttu-id="4d0c2-117">たとえば、テーブルの名前を変更するとき、そのテーブルがトリガーで参照されている場合は、新しいテーブル名が反映されるようにトリガーに変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-117">For example, if you rename a table and that table is referenced in a trigger, you must modify the trigger to reflect the new table name.</span></span> <span data-ttu-id="4d0c2-118">オブジェクトの名前を変更する前には、 [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) を使ってテーブルの従属関係を一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-118">Use [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) to list dependencies on the table before renaming it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4d0c2-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4d0c2-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4d0c2-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="4d0c2-120">Permissions</span></span>  
 <span data-ttu-id="4d0c2-121">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4d0c2-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4d0c2-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-table"></a><span data-ttu-id="4d0c2-123">テーブル名を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d0c2-123">To rename a table</span></span>  
  
1.  <span data-ttu-id="4d0c2-124">オブジェクト エクスプローラーで、名前を変更するテーブルを右クリックし、ショートカット メニューの **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-124">In Object Explorer, right-click the table you want to rename and choose **Design** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="4d0c2-125">**[表示]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-125">From the **View** menu, choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="4d0c2-126">**[プロパティ]** ウィンドウの **[オブジェクト名]** ボックスに、テーブルの新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-126">In the field for the **Name** value in the **Properties** window, type a new name for the table.</span></span>  
  
4.  <span data-ttu-id="4d0c2-127">この操作を取り消すには、このフィールド外に移動する前に Esc キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-127">To cancel this action, press the ESC key before leaving this field.</span></span>  
  
5.  <span data-ttu-id="4d0c2-128">[**ファイル**] メニューの [_テーブル名_の**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-128">From the **File** menu choose **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4d0c2-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4d0c2-129">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-table"></a><span data-ttu-id="4d0c2-130">テーブル名を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d0c2-130">To rename a table</span></span>  
  
1.  <span data-ttu-id="4d0c2-131">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4d0c2-132">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4d0c2-133">次の例では、`Sales` スキーマの `SalesTerritory` テーブルの名前を `SalesTerr` に変更します。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-133">The following example renames the `SalesTerritory` table to `SalesTerr` in the `Sales` schema.</span></span> <span data-ttu-id="4d0c2-134">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 <span data-ttu-id="4d0c2-135">その他の例については、「[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d0c2-135">For additional examples, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
