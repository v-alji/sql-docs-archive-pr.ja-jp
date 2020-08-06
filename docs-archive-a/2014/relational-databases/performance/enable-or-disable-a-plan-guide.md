---
title: プラン ガイドの有効化または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], disabling
- enabling plan guides
- plan guides [SQL Server], enabling
- disabling plan guides
ms.assetid: b00ab550-5308-4cb8-8330-483cd1d25654
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2611697e479d318245d8306b28c826e744ae85ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736276"
---
# <a name="enable-or-disable-a-plan-guide"></a><span data-ttu-id="2d89f-102">プラン ガイドの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="2d89f-102">Enable or Disable a Plan Guide</span></span>
  <span data-ttu-id="2d89f-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、プラン ガイドを無効化および有効化できます。</span><span class="sxs-lookup"><span data-stu-id="2d89f-103">You can disable and enable plan guides in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2d89f-104">データベース内の 1 つのプラン ガイドまたはすべてのプラン ガイドを有効化または無効化できます。</span><span class="sxs-lookup"><span data-stu-id="2d89f-104">Either a single plan guides or all plan guides in a database can be enabled or disabled.</span></span>  
  
 <span data-ttu-id="2d89f-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2d89f-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2d89f-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2d89f-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2d89f-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2d89f-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2d89f-108">Security</span><span class="sxs-lookup"><span data-stu-id="2d89f-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2d89f-109">**プラン ガイドの無効化または有効化に使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="2d89f-109">**To disable and enable plan guides, using:**</span></span>  
  
     [<span data-ttu-id="2d89f-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2d89f-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2d89f-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2d89f-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2d89f-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="2d89f-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2d89f-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2d89f-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2d89f-114">有効、無効にする場合のどちらでも、そのプラン ガイドで参照されている関数、ストアド プロシージャ、または DML トリガーを削除または変更しようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2d89f-114">Trying to drop or modify a function, stored procedure, or DML trigger that is referenced by a plan guide, either enabled or disabled, causes an error.</span></span> <span data-ttu-id="2d89f-115">上記のいずれかのオブジェクトの削除または変更の前に、常に依存関係を確認してください。</span><span class="sxs-lookup"><span data-stu-id="2d89f-115">Always check for dependencies before dropping or modifying any of the objects listed above.</span></span>  
  
-   <span data-ttu-id="2d89f-116">無効なプラン ガイドを無効にする場合や、有効なプラン ガイドを有効にする場合は影響は生じず、エラーなしで実行できます。</span><span class="sxs-lookup"><span data-stu-id="2d89f-116">Disabling a disabled plan guide or enabling an enabled plan guide has no effect and runs without error.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2d89f-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2d89f-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2d89f-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="2d89f-118">Permissions</span></span>  
 <span data-ttu-id="2d89f-119">OBJECT プラン ガイドの無効化または有効化には、プラン ガイドによって参照されるオブジェクト (関数、ストアド プロシージャなど) に対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2d89f-119">Disabling or enabling an OBJECT plan guide requires ALTER permission on the object (for example: function, stored procedure) that is referenced by the plan guide.</span></span> <span data-ttu-id="2d89f-120">その他すべてのプラン ガイドでは、ALTER DATABASE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2d89f-120">All other plan guides require ALTER DATABASE permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2d89f-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2d89f-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-enable-a-plan-guide"></a><span data-ttu-id="2d89f-122">プラン ガイドを無効化または有効化するには</span><span class="sxs-lookup"><span data-stu-id="2d89f-122">To disable or enable a plan guide</span></span>  
  
1.  <span data-ttu-id="2d89f-123">プラス記号をクリックして、無効化または有効化するプラン ガイドのあるデータベースを展開し、プラス記号をクリックして **[プログラミング]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2d89f-123">Click the plus sign to expand the database in which you want to disable or enable a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="2d89f-124">プラス記号をクリックして **[プラン ガイド]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2d89f-124">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="2d89f-125">無効化または有効化するプラン ガイドを右クリックし、 **[無効化]** または **[有効化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d89f-125">Right-click the plan guide you want to disable or enable and select either **Disable** or **Enable**.</span></span>  
  
4.  <span data-ttu-id="2d89f-126">**[プラン ガイドの無効化]** または **[プラン ガイドの有効化]** ダイアログ ボックスで、選択した動作が成功したことを確認し、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d89f-126">In either the **Disable Plan Guide** or **Enable Plan Guide** dialog box, verify that the chosen action was successful and then click **Close**.</span></span>  
  
#### <a name="to-disable-or-enable-all-plan-guides-in-a-database"></a><span data-ttu-id="2d89f-127">データベース内のすべてのプラン ガイドを無効化または有効化するには</span><span class="sxs-lookup"><span data-stu-id="2d89f-127">To disable or enable all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="2d89f-128">プラス記号をクリックして、無効化または有効化するプラン ガイドのあるデータベースを展開し、プラス記号をクリックして **[プログラミング]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2d89f-128">Click the plus sign to expand the database in which you want to disable or enable a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="2d89f-129">**[プラン ガイド]** フォルダーを右クリックし、 **[すべて有効化]** または **[すべて無効化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d89f-129">Right-click the **Plan Guides** folder and then select either **Enable All** or **Disable All**.</span></span>  
  
3.  <span data-ttu-id="2d89f-130">**[すべてのプラン ガイドを無効化]** または **[すべてのプラン ガイドを有効化]** ダイアログ ボックスで、選択した動作が成功したことを確認し、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d89f-130">In either the **Disable all Plan Guides** or **Enable all Plan Guides** dialog box, verify that the chosen action was successful and then click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2d89f-131">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2d89f-131">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-enable-a-plan-guide"></a><span data-ttu-id="2d89f-132">プラン ガイドを無効化または有効化するには</span><span class="sxs-lookup"><span data-stu-id="2d89f-132">To disable or enable a plan guide</span></span>  
  
1.  <span data-ttu-id="2d89f-133">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2d89f-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2d89f-134">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d89f-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2d89f-135">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d89f-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Create a procedure on which to define the plan guide.  
    IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetSalesOrderByCountry;  
    GO  
    CREATE PROCEDURE Sales.GetSalesOrderByCountry   
        (@Country nvarchar(60))  
    AS  
    BEGIN  
        SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country;  
    END  
    GO  
    --Create the plan guide.  
    EXEC sp_create_plan_guide N'Guide3',  
        N'SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country',  
        N'OBJECT',  
        N'Sales.GetSalesOrderByCountry',  
        NULL,  
        N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
    --Disable the plan guide.  
    EXEC sp_control_plan_guide N'DISABLE', N'Guide3';  
    GO  
    --Enable the plan guide.  
    EXEC sp_control_plan_guide N'ENABLE', N'Guide3';  
    GO  
  
    ```  
  
#### <a name="to-disable-or-enable-all-plan-guides-in-a-database"></a><span data-ttu-id="2d89f-136">データベース内のすべてのプラン ガイドを無効化または有効化するには</span><span class="sxs-lookup"><span data-stu-id="2d89f-136">To disable or enable all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="2d89f-137">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2d89f-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2d89f-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d89f-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2d89f-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d89f-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Disable all plan guides in the database.  
    EXEC sp_control_plan_guide N'DISABLE ALL';  
    GO  
    --Enable all plan guides in the database.  
    EXEC sp_control_plan_guide N'ENABLE ALL';  
    GO  
  
    ```  
  
 <span data-ttu-id="2d89f-140">詳細については、「[sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d89f-140">For more information, see [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).</span></span>  
  
  
