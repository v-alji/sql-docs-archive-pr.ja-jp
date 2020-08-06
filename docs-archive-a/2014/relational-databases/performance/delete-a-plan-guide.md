---
title: プラン ガイドの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], deleting
ms.assetid: aa4d3188-6927-43de-a3e3-90fc16eeaca7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 303ad6f59cbe24265aec66f3cb780a5b4ad4f157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714222"
---
# <a name="delete-a-plan-guide"></a><span data-ttu-id="7e4a5-102">プラン ガイドの削除</span><span class="sxs-lookup"><span data-stu-id="7e4a5-102">Delete a Plan Guide</span></span>
  <span data-ttu-id="7e4a5-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してプラン ガイドを削除できます。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-103">You can delete (drop) a plan guide in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7e4a5-104">[!INCLUDE[tsql](../../includes/tsql-md.md)]を使用すると、データベース内のすべてのプラン ガイドを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-104">Using [!INCLUDE[tsql](../../includes/tsql-md.md)], you can also delete all of the plan guides in a database.</span></span>  
  
 <span data-ttu-id="7e4a5-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="7e4a5-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7e4a5-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="7e4a5-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7e4a5-107">Security</span><span class="sxs-lookup"><span data-stu-id="7e4a5-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7e4a5-108">**プラン ガイドの削除に使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="7e4a5-108">**To delete a plan guide, using:**</span></span>  
  
     [<span data-ttu-id="7e4a5-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7e4a5-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7e4a5-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7e4a5-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7e4a5-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="7e4a5-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7e4a5-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7e4a5-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7e4a5-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="7e4a5-113">Permissions</span></span>  
 <span data-ttu-id="7e4a5-114">OBJECT プラン ガイドの削除には、プラン ガイドによって参照されるオブジェクト (関数、ストアド プロシージャなど) に対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-114">Deleting an OBJECT plan guide requires ALTER permission on the object (for example: function, stored procedure) that is referenced by the plan guide.</span></span> <span data-ttu-id="7e4a5-115">その他すべてのプラン ガイドでは、ALTER DATABASE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-115">All other plan guides require ALTER DATABASE permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7e4a5-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7e4a5-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-plan-guide"></a><span data-ttu-id="7e4a5-117">プラン ガイドを削除するには</span><span class="sxs-lookup"><span data-stu-id="7e4a5-117">To delete a plan guide</span></span>  
  
1.  <span data-ttu-id="7e4a5-118">プラス記号をクリックして、削除するプラン ガイドのあるデータベースを展開し、プラス記号をクリックして **[プログラミング]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-118">Click the plus sign to expand the database in which you want to delete a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="7e4a5-119">プラス記号をクリックして **[プラン ガイド]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-119">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="7e4a5-120">削除するプラン ガイドを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-120">Right-click the plan guide you want to delete and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="7e4a5-121">**[オブジェクトの削除]** ダイアログ ボックスで、正しいプラン ガイドが選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-121">In the **Delete Object** dialog box, ensure that the correct plan guide is selected and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7e4a5-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7e4a5-122">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-single-plan-guide"></a><span data-ttu-id="7e4a5-123">単一のプラン ガイドを削除するには</span><span class="sxs-lookup"><span data-stu-id="7e4a5-123">To delete a single plan guide</span></span>  
  
1.  <span data-ttu-id="7e4a5-124">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7e4a5-125">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7e4a5-126">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
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
    GO  
    --Drop the plan guide.  
    EXEC sp_control_plan_guide N'DROP', N'Guide3';  
    GO  
    ```  
  
#### <a name="to-delete-all-plan-guides-in-a-database"></a><span data-ttu-id="7e4a5-127">データベース内のすべてのプラン ガイドを削除するには</span><span class="sxs-lookup"><span data-stu-id="7e4a5-127">To delete all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="7e4a5-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7e4a5-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7e4a5-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_control_plan_guide N'DROP ALL';  
    GO  
    ```  
  
 <span data-ttu-id="7e4a5-131">詳細については、「[sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e4a5-131">For more information, see [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).</span></span>  
  
  
