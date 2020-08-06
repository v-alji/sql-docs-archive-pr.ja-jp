---
title: テーブルの削除 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e361456534f565f854d348bbef5751c7d66c0f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738160"
---
# <a name="delete-tables-database-engine"></a><span data-ttu-id="b18f0-102">テーブルの削除 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="b18f0-102">Delete Tables (Database Engine)</span></span>
  <span data-ttu-id="b18f0-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してデータベースからテーブルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="b18f0-103">You can delete (drop) a table from your database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b18f0-104">テーブルの削除については、十分に検討してください。</span><span class="sxs-lookup"><span data-stu-id="b18f0-104">Think carefully before you delete a table.</span></span> <span data-ttu-id="b18f0-105">テーブルを参照するクエリ、ビュー、ユーザー定義関数、ストアド プロシージャ、またはプログラムがある場合は、テーブルを削除すると、各オブジェクトが無効になります。</span><span class="sxs-lookup"><span data-stu-id="b18f0-105">If existing queries, views, user-defined functions, stored procedures, or programs refer to that table, the deletion will make these objects invalid.</span></span>  
  
 <span data-ttu-id="b18f0-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b18f0-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b18f0-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b18f0-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b18f0-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b18f0-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b18f0-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b18f0-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b18f0-110">**テーブルを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="b18f0-110">**To Delete a Table, using:**</span></span>  
  
     [<span data-ttu-id="b18f0-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b18f0-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b18f0-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b18f0-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b18f0-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="b18f0-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b18f0-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b18f0-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b18f0-115">FOREIGN KEY 制約によって参照されているテーブルを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="b18f0-115">You cannot drop a table that is referenced by a FOREIGN KEY constraint.</span></span> <span data-ttu-id="b18f0-116">まず、参照している FOREIGN KEY 制約または参照テーブルを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b18f0-116">The referencing FOREIGN KEY constraint or the referencing table must first be dropped.</span></span> <span data-ttu-id="b18f0-117">参照しているテーブルと、主キーを格納しているテーブルの両方を同じ DROP TABLE ステートメントで削除する場合には、参照しているテーブルを先に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b18f0-117">If both the referencing table and the table that holds the primary key are being dropped in the same DROP TABLE statement, the referencing table must be listed first.</span></span>  
  
-   <span data-ttu-id="b18f0-118">テーブルを削除すると、そのテーブルのルールや既定値はバインドを失い、そのテーブルに関係付けられている制約やトリガーも自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="b18f0-118">When a table is dropped, rules or defaults on the table lose their binding, and any constraints or triggers associated with the table are automatically dropped.</span></span> <span data-ttu-id="b18f0-119">テーブルを再作成する場合は、適切なルールや既定値を再バインドし、トリガーを再作成し、必要なすべての制約を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b18f0-119">If you re-create a table, you must rebind the appropriate rules and defaults, re-create any triggers, and add all required constraints.</span></span>  
  
-   <span data-ttu-id="b18f0-120">FILESTREAM 属性が指定されている `varbinary (max)` 列を含むテーブルを削除しても、ファイル システムに保存されているデータは削除されません。</span><span class="sxs-lookup"><span data-stu-id="b18f0-120">If you drop a table that contains a `varbinary (max)` column with the FILESTREAM attribute, any data stored in the file system will not be removed.</span></span>  
  
-   <span data-ttu-id="b18f0-121">DROP TABLE と CREATE TABLE を同じバッチ内の同じテーブルに対して実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="b18f0-121">DROP TABLE and CREATE TABLE should not be executed on the same table in the same batch.</span></span> <span data-ttu-id="b18f0-122">実行した場合、予期しないエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b18f0-122">Otherwise an unexpected error may occur.</span></span>  
  
-   <span data-ttu-id="b18f0-123">削除されたテーブルを参照しているすべてのビューとストアド プロシージャを、明示的に削除するか、変更してテーブルへの参照を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b18f0-123">Any view or stored procedure that references the dropped table must be explicitly deleted or modified to remove the reference to the table.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b18f0-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b18f0-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b18f0-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="b18f0-125">Permissions</span></span>  
 <span data-ttu-id="b18f0-126">テーブルが属するスキーマに対する ALTER 権限、テーブルに対する CONTROL 権限、または **db_ddladmin** 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="b18f0-126">Requires ALTER permission on the schema to which the table belongs, CONTROL permission on the table, or membership in the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b18f0-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b18f0-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-table-from-the-database"></a><span data-ttu-id="b18f0-128">データベースからテーブルを削除するには</span><span class="sxs-lookup"><span data-stu-id="b18f0-128">To delete a table from the database</span></span>  
  
1.  <span data-ttu-id="b18f0-129">オブジェクト エクスプローラーで、削除するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b18f0-129">In Object Explorer, select the table you want to delete.</span></span>  
  
2.  <span data-ttu-id="b18f0-130">テーブルを右クリックし、ショートカット メニューの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b18f0-130">Right-click the table and choose **Delete** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="b18f0-131">削除の確認を要求するメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b18f0-131">A message box prompts you to confirm the deletion.</span></span> <span data-ttu-id="b18f0-132">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b18f0-132">Click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b18f0-133">テーブルを削除すると、テーブルへのリレーションシップが自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="b18f0-133">Deleting a table automatically removes any relationships to it.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b18f0-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b18f0-134">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-table-in-query-editor"></a><span data-ttu-id="b18f0-135">クエリ エディターでテーブルを削除するには</span><span class="sxs-lookup"><span data-stu-id="b18f0-135">To delete a table in Query Editor</span></span>  
  
1.  <span data-ttu-id="b18f0-136">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="b18f0-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b18f0-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b18f0-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b18f0-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b18f0-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 <span data-ttu-id="b18f0-139">詳細については、「[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b18f0-139">For more information, see [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)</span></span>  
  
  
