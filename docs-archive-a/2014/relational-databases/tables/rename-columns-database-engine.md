---
title: 列名の変更 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6871ab82eaa17aa5e392e6b2bb3f5c60058f9af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643723"
---
# <a name="rename-columns-database-engine"></a><span data-ttu-id="0e1f8-102">列名の変更 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="0e1f8-102">Rename Columns (Database Engine)</span></span>
  <span data-ttu-id="0e1f8-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してテーブル列の名前を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-103">You can rename a table column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0e1f8-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="0e1f8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0e1f8-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="0e1f8-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0e1f8-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0e1f8-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0e1f8-107">Security</span><span class="sxs-lookup"><span data-stu-id="0e1f8-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0e1f8-108">**列名を変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="0e1f8-108">**To rename columns, using:**</span></span>  
  
     [<span data-ttu-id="0e1f8-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0e1f8-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0e1f8-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0e1f8-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0e1f8-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="0e1f8-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0e1f8-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0e1f8-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0e1f8-113">列名を変更しても、その列に対する参照の名前は自動的には変更されません。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-113">Renaming a column will not automatically rename references to that column.</span></span> <span data-ttu-id="0e1f8-114">名前を変更した列を参照しているオブジェクトに対しては、手動で変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-114">You must modify any objects that reference the renamed column manually.</span></span> <span data-ttu-id="0e1f8-115">たとえば、テーブルの列の名前を変更するとき、その列がトリガーで参照されている場合は、新しい列名が反映されるようにトリガーに変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-115">For example, if you rename a table column and that column is referenced in a trigger, you must modify the trigger to reflect the new column name.</span></span> <span data-ttu-id="0e1f8-116">オブジェクトの名前を変更する前には、 [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) を使ってオブジェクトの従属関係を一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-116">Use [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) to list dependencies on the object before renaming it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0e1f8-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0e1f8-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0e1f8-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="0e1f8-118">Permissions</span></span>  
 <span data-ttu-id="0e1f8-119">オブジェクトに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-119">Requires ALTER permission on the object.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0e1f8-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="0e1f8-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-column-using-object-explorer"></a><span data-ttu-id="0e1f8-121">オブジェクト エクスプ ローラーを使用して列の名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="0e1f8-121">To rename a column using Object Explorer</span></span>  
  
1.  <span data-ttu-id="0e1f8-122">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-122">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0e1f8-123">**オブジェクト エクスプローラー**で、列の名前を変更するテーブルを右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-123">In **Object Explorer**, right-click the table in which you want to rename columns and choose **Rename**.</span></span>  
  
3.  <span data-ttu-id="0e1f8-124">新しい列の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-124">Type a new column name.</span></span>  
  
#### <a name="to-rename-a-column-using-table-designer"></a><span data-ttu-id="0e1f8-125">テーブル デザイナーを使用して列の名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="0e1f8-125">To rename a column using Table Designer</span></span>  
  
1.  <span data-ttu-id="0e1f8-126">**オブジェクト エクスプローラー**で、列の名前を変更するテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-126">In **Object Explorer**, right-click the table to which you want to rename columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="0e1f8-127">**[列名]** の下の変更する名前を選択して、新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-127">Under **Column Name**, select the name you want to change and type a new one.</span></span>  
  
3.  <span data-ttu-id="0e1f8-128">**[ファイル]** メニューの **[_<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-128">On the **File** menu, click **Save**_table name_.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e1f8-129">**[列のプロパティ]** タブで列の名前を変更することもできます。名前を変更する列を選択して、 **[名前]** に新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-129">You can also change the name of a column in the **Column Properties** tab. Select the column whose name you want to change and type a new value for **Name**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0e1f8-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="0e1f8-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="0e1f8-131">**列名を変更するには**</span><span class="sxs-lookup"><span data-stu-id="0e1f8-131">**To rename a column**</span></span>  
  
#### <a name="to-rename-a-column"></a><span data-ttu-id="0e1f8-132">列名を変更するには</span><span class="sxs-lookup"><span data-stu-id="0e1f8-132">To rename a column</span></span>  
  
1.  <span data-ttu-id="0e1f8-133">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0e1f8-134">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0e1f8-135">3. 次の例では、`Sales.SalesTerritory` テーブル内の `TerritoryID` 列の名前を `TerrID` に変更します。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-135">The following example renames the column `TerritoryID` in the table `Sales.SalesTerritory` to `TerrID`.</span></span> <span data-ttu-id="0e1f8-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
    GO  
    ```  
  
 <span data-ttu-id="0e1f8-137">詳細については、「[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e1f8-137">For more information, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
