---
title: 統計の更新 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- updating statistics
- statistics [SQL Server], updating
ms.assetid: 4b97c0b4-03ff-4cfb-9c3f-3b33290b7a2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 28491dda23c2ba9402e91dc051249f5bdcdf28d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644369"
---
# <a name="update-statistics"></a><span data-ttu-id="5697d-102">統計の更新</span><span class="sxs-lookup"><span data-stu-id="5697d-102">Update Statistics</span></span>
  <span data-ttu-id="5697d-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のテーブルまたはインデックス付きビューについての、クエリの最適化に関する統計を更新します。</span><span class="sxs-lookup"><span data-stu-id="5697d-103">You can update query optimization statistics on a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5697d-104">既定では、統計はクエリ プランを改善するためにクエリ オプティマイザーによって必要に応じて更新されますが、UPDATE STATISTICS またはストアド プロシージャ `sp_updatestats` を使用して既定の更新より頻繁に統計を更新することでクエリのパフォーマンスを向上させることができる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5697d-104">By default, the query optimizer already updates statistics as necessary to improve the query plan; in some cases you can improve query performance by using UPDATE STATISTICS or the stored procedure `sp_updatestats` to update statistics more frequently than the default updates.</span></span>  
  
 <span data-ttu-id="5697d-105">統計を更新すると、クエリが最新の統計を使用してコンパイルされるようになります。</span><span class="sxs-lookup"><span data-stu-id="5697d-105">Updating statistics ensures that queries compile with up-to-date statistics.</span></span> <span data-ttu-id="5697d-106">ただし、統計の更新によりクエリが再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="5697d-106">However, updating statistics causes queries to recompile.</span></span> <span data-ttu-id="5697d-107">パフォーマンスの向上を目的とする場合、クエリ プランの改善とクエリの再コンパイルに要する時間の間にはトレードオフの関係があるため、あまり頻繁に統計を更新しないようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5697d-107">We recommend not updating statistics too frequently because there is a performance tradeoff between improving query plans and the time it takes to recompile queries.</span></span> <span data-ttu-id="5697d-108">実際のトレードオフはアプリケーションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="5697d-108">The specific tradeoffs depend on your application.</span></span> <span data-ttu-id="5697d-109">統計の更新では、tempdb を使用して、統計を作成するための行のサンプルを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="5697d-109">UPDATE STATISTICS can use tempdb to sort the sample of rows for building statistics.</span></span>  
  
 <span data-ttu-id="5697d-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="5697d-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5697d-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="5697d-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5697d-112">Security</span><span class="sxs-lookup"><span data-stu-id="5697d-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5697d-113">**統計オブジェクトを更新するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="5697d-113">**To update a statistics object, using:**</span></span>  
  
     [<span data-ttu-id="5697d-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5697d-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5697d-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5697d-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5697d-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="5697d-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5697d-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5697d-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5697d-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="5697d-118">Permissions</span></span>  
 <span data-ttu-id="5697d-119">UPDATE STATISTICS を使用するか、または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で変更する場合は、テーブルまたはビューに対する ALTER 権限が必要です</span><span class="sxs-lookup"><span data-stu-id="5697d-119">If using UPDATE STATISTICS or making changes through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], requires ALTER permission on the table or view.</span></span> <span data-ttu-id="5697d-120">`sp_updatestats`を使用する場合は、 **sysadmin** 固定サーバー ロールのメンバーシップまたはデータベース (**dbo**) の所有権が必要です。</span><span class="sxs-lookup"><span data-stu-id="5697d-120">If using `sp_updatestats`, requires membership in the **sysadmin** fixed server role, or ownership of the database (**dbo**).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5697d-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="5697d-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-update-a-statistics-object"></a><span data-ttu-id="5697d-122">統計オブジェクトを更新するには</span><span class="sxs-lookup"><span data-stu-id="5697d-122">To update a statistics object</span></span>  
  
1.  <span data-ttu-id="5697d-123">**オブジェクト エクスプローラー**で、統計を更新するデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="5697d-123">In **Object Explorer**, click the plus sign to expand the database in which you want to update the statistic.</span></span>  
  
2.  <span data-ttu-id="5697d-124">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5697d-124">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="5697d-125">プラス記号をクリックして、統計を更新するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="5697d-125">Click the plus sign to expand the table in which you want to update the statistic.</span></span>  
  
4.  <span data-ttu-id="5697d-126">プラス記号をクリックして **[統計]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5697d-126">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="5697d-127">更新する統計オブジェクトを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5697d-127">Right-click the statistics object you wish to update and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="5697d-128">[**統計のプロパティ-**_statistics_name_ ] ダイアログボックスで、[**これらの列の統計を更新**する] チェックボックスをオンにし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5697d-128">In the **Statistics Properties -**_statistics_name_ dialog box, select the **Update statistics for these columns** check box and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5697d-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="5697d-129">Using Transact-SQL</span></span>  
  
#### <a name="to-update-a-specific-statistics-object"></a><span data-ttu-id="5697d-130">特定の統計オブジェクトを更新するには</span><span class="sxs-lookup"><span data-stu-id="5697d-130">To update a specific statistics object</span></span>  
  
1.  <span data-ttu-id="5697d-131">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5697d-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5697d-132">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5697d-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5697d-133">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5697d-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example updates the statistics for the AK_SalesOrderDetail_rowguid index of the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;   
    GO  
    ```  
  
#### <a name="to-update-all-statistics-in-a-table"></a><span data-ttu-id="5697d-134">テーブルのすべての統計を更新するには</span><span class="sxs-lookup"><span data-stu-id="5697d-134">To update all statistics in a table</span></span>  
  
1.  <span data-ttu-id="5697d-135">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5697d-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5697d-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5697d-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5697d-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5697d-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all indexes on the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail;   
    GO  
    ```  
  
 <span data-ttu-id="5697d-138">詳細については、「 [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)で作成されたデータベース メンテナンス プランを実行します。</span><span class="sxs-lookup"><span data-stu-id="5697d-138">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
#### <a name="to-update-all-statistics-in-a-database"></a><span data-ttu-id="5697d-139">データベースのすべての統計を更新するには</span><span class="sxs-lookup"><span data-stu-id="5697d-139">To update all statistics in a database</span></span>  
  
1.  <span data-ttu-id="5697d-140">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5697d-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5697d-141">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5697d-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5697d-142">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5697d-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all tables in the database.   
    EXEC sp_updatestats;  
    ```  
  
 <span data-ttu-id="5697d-143">詳細については、「[sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5697d-143">For more information, see [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span>  
  
  
