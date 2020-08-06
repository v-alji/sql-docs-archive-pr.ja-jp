---
title: ビューの削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3e05724f7d6384d0407e915207ad60a1cdfb01b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631723"
---
# <a name="delete-views"></a><span data-ttu-id="6a144-102">ビューの削除</span><span class="sxs-lookup"><span data-stu-id="6a144-102">Delete Views</span></span>
  <span data-ttu-id="6a144-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、次のいずれかを使用してビューを削除できます: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a144-103">You can delete (drop) views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6a144-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="6a144-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6a144-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6a144-105">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6a144-106">ビューを削除すると、ビューの定義やビューに関するその他の情報がシステム カタログから削除されます。</span><span class="sxs-lookup"><span data-stu-id="6a144-106">When you drop a view, the definition of the view and other information about the view is deleted from the system catalog.</span></span> <span data-ttu-id="6a144-107">ビューに対する権限もすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="6a144-107">All permissions for the view are also deleted.</span></span>  
  
-   <span data-ttu-id="6a144-108">`DROP TABLE` を使用して削除されたテーブルのすべてのビューは、 `DROP VIEW`を使用して明示的に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a144-108">Any view on a table that is dropped by using `DROP TABLE` must be dropped explicitly by using `DROP VIEW`.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6a144-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6a144-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6a144-110">Permissions</span><span class="sxs-lookup"><span data-stu-id="6a144-110">Permissions</span></span>  
 <span data-ttu-id="6a144-111">SCHEMA に対する ALTER 権限、または OBJECT に対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6a144-111">Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6a144-112">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6a144-112">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-view-from-a-database"></a><span data-ttu-id="6a144-113">データベースからビューを削除するには</span><span class="sxs-lookup"><span data-stu-id="6a144-113">To delete a view from a database</span></span>  
  
1.  <span data-ttu-id="6a144-114">**オブジェクト エクスプローラー**で、削除するビューを含むデータベースを展開します。次に、 **[ビュー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="6a144-114">In **Object Explorer**, expand the database that contains the view you want to delete, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="6a144-115">削除するビューを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a144-115">Right-click the view you want to delete and click **Delete**.</span></span>  
  
3.  <span data-ttu-id="6a144-116">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a144-116">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6a144-117">[**オブジェクトの削除**] ダイアログボックスの [**依存関係の表示**] をクリックして、[ _view_name_の**依存関係**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="6a144-117">Click **Show Dependencies** in the **Delete Object** dialog box to open the _view_name_**Dependencies** dialog box.</span></span> <span data-ttu-id="6a144-118">ビューに依存するすべてのオブジェクトと、ビューが依存するすべてのオブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a144-118">This will show all of the objects that depend on the view and all of the objects on which the view depends.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6a144-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6a144-119">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-view-from-a-database"></a><span data-ttu-id="6a144-120">データベースからビューを削除するには</span><span class="sxs-lookup"><span data-stu-id="6a144-120">To delete a view from a database</span></span>  
  
1.  <span data-ttu-id="6a144-121">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6a144-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6a144-122">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a144-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6a144-123">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a144-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6a144-124">この例では、ビューが既に存在する場合にのみ、指定されたビューを削除します。</span><span class="sxs-lookup"><span data-stu-id="6a144-124">The example deletes the specified view only if the view already exists.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 <span data-ttu-id="6a144-125">詳細については、「[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a144-125">For more information, see [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).</span></span>  
  
  
