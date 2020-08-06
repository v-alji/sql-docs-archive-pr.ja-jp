---
title: 統計の削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], deleting
- deleting statistics
ms.assetid: eccce0aa-591e-4a1d-bd10-373b022f8749
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 36b74d7e1465c0742cda4fef9f34fb4b3930719c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644380"
---
# <a name="delete-statistics"></a><span data-ttu-id="aa6b2-102">統計の削除</span><span class="sxs-lookup"><span data-stu-id="aa6b2-102">Delete Statistics</span></span>
  <span data-ttu-id="aa6b2-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または  を使用してテーブルおよびビューから統計を削除できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa6b2-103">You can delete (drop) statistics from tables and views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="aa6b2-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="aa6b2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="aa6b2-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="aa6b2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="aa6b2-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="aa6b2-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="aa6b2-107">Security</span><span class="sxs-lookup"><span data-stu-id="aa6b2-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="aa6b2-108">**テーブルまたはビューから統計を削除するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="aa6b2-108">**To drop statistics from a table or view, using:**</span></span>  
  
     [<span data-ttu-id="aa6b2-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa6b2-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="aa6b2-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aa6b2-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="aa6b2-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="aa6b2-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="aa6b2-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="aa6b2-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="aa6b2-113">統計を削除するときは注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-113">Be careful when you drop statistics.</span></span> <span data-ttu-id="aa6b2-114">統計を削除すると、クエリ オプティマイザーによって選択された実行プランに影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-114">Doing so may affect the execution plan chosen by the query optimizer.</span></span>  
  
-   <span data-ttu-id="aa6b2-115">インデックスの統計を DROP STATISTICS で削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-115">Statistics on indexes cannot be dropped by using DROP STATISTICS.</span></span> <span data-ttu-id="aa6b2-116">インデックスが存在する限り、統計は維持されます。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-116">Statistics remain as long as the index exists.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="aa6b2-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="aa6b2-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="aa6b2-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="aa6b2-118">Permissions</span></span>  
 <span data-ttu-id="aa6b2-119">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-119">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="aa6b2-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="aa6b2-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a><span data-ttu-id="aa6b2-121">テーブルまたはビューから統計を削除するには</span><span class="sxs-lookup"><span data-stu-id="aa6b2-121">To drop statistics from a table or view</span></span>  
  
1.  <span data-ttu-id="aa6b2-122">**オブジェクト エクスプローラー**で、統計を削除するデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-122">In **Object Explorer**, click the plus sign to expand the database in which you want to delete a statistic.</span></span>  
  
2.  <span data-ttu-id="aa6b2-123">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-123">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="aa6b2-124">プラス記号をクリックして、統計を削除するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-124">Click the plus sign to expand the table in which you want to delete a statistic.</span></span>  
  
4.  <span data-ttu-id="aa6b2-125">プラス記号をクリックして **[統計]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-125">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="aa6b2-126">削除する統計オブジェクトを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-126">Right-click the statistics object that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="aa6b2-127">**[オブジェクトの削除]** ダイアログ ボックスで、正しい統計が選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-127">In the **Delete Object** dialog box, ensure that the correct statistic has been selected and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="aa6b2-128">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="aa6b2-128">Using Transact-SQL</span></span>  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a><span data-ttu-id="aa6b2-129">テーブルまたはビューから統計を削除するには</span><span class="sxs-lookup"><span data-stu-id="aa6b2-129">To drop statistics from a table or view</span></span>  
  
1.  <span data-ttu-id="aa6b2-130">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="aa6b2-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="aa6b2-132">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- First, create two statistics named VendorCredit and CustomerTotal  
    -- The first statistic uses a random 50% sample of information provided from the Name and CreditRating columns in the Purchasing.Vendor table.  
    CREATE STATISTICS VendorCredit  
        ON Purchasing.Vendor (Name, CreditRating)  
        WITH SAMPLE 50 PERCENT  
    -- The second statistic uses all of the information from the CustomerID and TotalDue columns in the Sales.SalesOrderHeader table  
    CREATE STATISTICS CustomerTotal  
        ON Sales.SalesOrderHeader (CustomerID, TotalDue)  
        WITH FULLSCAN;  
    GO  
    -- This next statement drops both of the statistics created above. Note that the naming convention is [table_name].[statistics_name].  
    DROP STATISTICS Purchasing.Vendor.VendorCredit, Sales.SalesOrderHeader.CustomerTotal;  
    GO  
    ```  
  
 <span data-ttu-id="aa6b2-133">詳細については、「[DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa6b2-133">For more information, see [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql).</span></span>  
  
  
