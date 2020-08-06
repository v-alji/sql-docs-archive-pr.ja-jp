---
title: ビューの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- views [SQL Server], modifying
- modifying views
- renaming views
ms.assetid: 2d3c14dc-43e5-4324-b8fb-f2692d330b16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10cf9ecc860d8f9b46a06ac679b0f1a8241000bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640821"
---
# <a name="modify-views"></a><span data-ttu-id="2233c-102">ビューの変更</span><span class="sxs-lookup"><span data-stu-id="2233c-102">Modify Views</span></span>
  <span data-ttu-id="2233c-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、ビューの定義後にビューの削除や再作成を行わずに、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ビューの名前または定義を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2233c-103">After you define a view, you can modify its definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] without dropping and re-creating the view by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2233c-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2233c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2233c-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2233c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2233c-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2233c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2233c-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2233c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2233c-108">**以下を使用してビューを変更するには:**</span><span class="sxs-lookup"><span data-stu-id="2233c-108">**To modify a view, using:**</span></span>  
  
     [<span data-ttu-id="2233c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2233c-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2233c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2233c-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2233c-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="2233c-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2233c-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2233c-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2233c-113">依存オブジェクトが無効になるような変更を行わない限り、ビューを変更しても、ストアド プロシージャやトリガーなどの依存オブジェクトには影響しません。</span><span class="sxs-lookup"><span data-stu-id="2233c-113">Modifying a view does not affect any dependent objects, such as stored procedures or triggers, unless the definition of the view changes in such a way that the dependent object is no longer valid.</span></span>  
  
-   <span data-ttu-id="2233c-114">現在使用されているビューを ALTER VIEW を使用して変更する場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はビューに対して排他スキーマ ロックを設定します。</span><span class="sxs-lookup"><span data-stu-id="2233c-114">If a view currently used is modified by using ALTER VIEW, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] takes an exclusive schema lock on the view.</span></span> <span data-ttu-id="2233c-115">ロックが許可され、ビューのアクティブ ユーザーがいなくなると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はプロシージャ キャッシュからビューのすべてのコピーを削除します。</span><span class="sxs-lookup"><span data-stu-id="2233c-115">When the lock is granted, and there are no active users of the view, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] deletes all copies of the view from the procedure cache.</span></span> <span data-ttu-id="2233c-116">ビューを参照している既存のプランはキャッシュに残りますが、呼び出されると再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="2233c-116">Existing plans referencing the view remain in the cache but are recompiled when invoked.</span></span>  
  
-   <span data-ttu-id="2233c-117">ALTER VIEW は、インデックス付きビューに適用できますが、そのビューのすべてのインデックスを無条件で削除します。</span><span class="sxs-lookup"><span data-stu-id="2233c-117">ALTER VIEW can be applied to indexed views; however, ALTER VIEW unconditionally drops all indexes on the view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2233c-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2233c-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2233c-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="2233c-119">Permissions</span></span>  
 <span data-ttu-id="2233c-120">ALTER VIEW を実行するには、少なくとも OBJECT に対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2233c-120">To execute ALTER VIEW, at a minimum, ALTER permission on OBJECT is required.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2233c-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2233c-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-view"></a><span data-ttu-id="2233c-122">ビューを変更するには</span><span class="sxs-lookup"><span data-stu-id="2233c-122">To modify a view</span></span>  
  
1.  <span data-ttu-id="2233c-123">**オブジェクト エクスプローラー**で、ビューがあるデータベースの横にあるプラス記号をクリックし、 **[ビュー]** フォルダーの横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2233c-123">In **Object Explorer**, click the plus sign next to the database where your view is located and then click the plus sign next to the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="2233c-124">変更するビューを右クリックし、 **[デザイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2233c-124">Right-click on the view you wish to modify and select **Design**.</span></span>  
  
3.  <span data-ttu-id="2233c-125">クエリ デザイナーのダイアグラム ペインで、次の方法を使用してビューを変更します。</span><span class="sxs-lookup"><span data-stu-id="2233c-125">In the diagram pane of the query designer, make changes to the view in one or more of the following ways:</span></span>  
  
    1.  <span data-ttu-id="2233c-126">追加または削除する要素のチェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="2233c-126">Select or clear the check boxes of any elements you wish to add or remove.</span></span>  
  
    2.  <span data-ttu-id="2233c-127">ダイアグラム ペイン内で右クリックし、 **[テーブルの追加]** を選択します。次に、 **[テーブルの追加]** ダイアログ ボックスで、ビューに追加する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="2233c-127">Right-click within the diagram pane, select **Add Table...**, and then select the additional columns you want to add to the view from the **Add Table** dialog box.</span></span>  
  
    3.  <span data-ttu-id="2233c-128">削除するテーブルのタイトル バーを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2233c-128">Right-click the title bar of the table you wish to remove and select **Remove**.</span></span>  
  
4.  <span data-ttu-id="2233c-129">**ファイル** メニューの **view name**_の保存_をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2233c-129">On the **File** menu, click **Save**_view name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2233c-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2233c-130">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-view"></a><span data-ttu-id="2233c-131">ビューを変更するには</span><span class="sxs-lookup"><span data-stu-id="2233c-131">To modify a view</span></span>  
  
1.  <span data-ttu-id="2233c-132">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2233c-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2233c-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2233c-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2233c-134">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2233c-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2233c-135">この例では、ビューを作成した後、ALTER VIEW を使用してビューを変更します。</span><span class="sxs-lookup"><span data-stu-id="2233c-135">The example first creates a view and then modifies the view by using ALTER VIEW.</span></span> <span data-ttu-id="2233c-136">ビュー定義に WHERE 句が追加されています。</span><span class="sxs-lookup"><span data-stu-id="2233c-136">A WHERE clause is added to the view definition.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    -- Create a view.  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
  
    -- Modify the view by adding a WHERE clause to limit the rows returned.  
    ALTER VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID  
    WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;   
    GO  
    ```  
  
 <span data-ttu-id="2233c-137">詳細については、「[ALTER VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-view-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2233c-137">For more information, see [ALTER VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-view-transact-sql).</span></span>  
  
  
