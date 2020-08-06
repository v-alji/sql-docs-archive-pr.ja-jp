---
title: パーティション構成の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 515de63f-dfc5-434d-9adb-f3b5992f745a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d57984228e23143d2061df6bf447f978f9bd3c46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642753"
---
# <a name="modify-a-partition-scheme"></a><span data-ttu-id="974b9-102">パーティション構成の変更</span><span class="sxs-lookup"><span data-stu-id="974b9-102">Modify a Partition Scheme</span></span>
  <span data-ttu-id="974b9-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、パーティション テーブルに追加される次のパーティションを保持するファイル グループを指定することにより、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でパーティション構成を変更できます。</span><span class="sxs-lookup"><span data-stu-id="974b9-103">You can modify a partition scheme in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by designating a filegroup to hold the next partition that is added to a partitioned table using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="974b9-104">この操作は、NEXT USED プロパティをファイル グループに割り当てることで実行できます。</span><span class="sxs-lookup"><span data-stu-id="974b9-104">You do this by assigning the NEXT USED property to a filegroup.</span></span> <span data-ttu-id="974b9-105">NEXT USED プロパティは、空のファイル グループか、またはパーティションを既に保持しているファイル グループに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="974b9-105">You can assign the NEXT USED property to an empty filegroup or to one that already holds a partition.</span></span> <span data-ttu-id="974b9-106">つまり、ファイル グループでは、複数のパーティションを保持することができます。</span><span class="sxs-lookup"><span data-stu-id="974b9-106">In other words, a filegroup can hold more than one partition.</span></span>  
  
 <span data-ttu-id="974b9-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="974b9-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="974b9-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="974b9-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="974b9-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="974b9-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="974b9-110">Security</span><span class="sxs-lookup"><span data-stu-id="974b9-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="974b9-111">**以下を使用してパーティション テーブルまたはパーティション インデックスを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="974b9-111">**To create a partitioned table or index, using:**</span></span>  
  
     [<span data-ttu-id="974b9-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="974b9-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="974b9-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="974b9-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="974b9-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="974b9-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="974b9-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="974b9-115">Limitations and Restrictions</span></span>  
 <span data-ttu-id="974b9-116">ALTER PARTITION SCHEME の対象となるファイル グループは、オンラインになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="974b9-116">Any filegroup affected by ALTER PARTITION SCHEME must be online.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="974b9-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="974b9-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="974b9-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="974b9-118">Permissions</span></span>  
 <span data-ttu-id="974b9-119">次の権限を使って ALTER PARTITION SCHEME を実行できます。</span><span class="sxs-lookup"><span data-stu-id="974b9-119">The following permissions can be used to execute ALTER PARTITION SCHEME:</span></span>  
  
-   <span data-ttu-id="974b9-120">ALTER ANY DATASPACE 権限。</span><span class="sxs-lookup"><span data-stu-id="974b9-120">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="974b9-121">この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="974b9-121">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="974b9-122">パーティション構成が作成されたデータベースに対する CONTROL または ALTER 権限。</span><span class="sxs-lookup"><span data-stu-id="974b9-122">CONTROL or ALTER permission on the database in which the partition scheme was created.</span></span>  
  
-   <span data-ttu-id="974b9-123">パーティション構成が作成されたデータベースのサーバーに対する CONTROL SERVER または ALTER ANY DATABASE 権限。</span><span class="sxs-lookup"><span data-stu-id="974b9-123">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition scheme was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="974b9-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="974b9-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="974b9-125">**パーティション構成を変更するには:**</span><span class="sxs-lookup"><span data-stu-id="974b9-125">**To modify a partition scheme:**</span></span>  
  
 <span data-ttu-id="974b9-126">この操作は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では実行できません。</span><span class="sxs-lookup"><span data-stu-id="974b9-126">This specific action cannot be performed using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="974b9-127">パーティション構成を変更するには、最初にパーティション構成を削除し、パーティションの作成ウィザードを使用して必要なプロパティを持つ新しいパーティション構成を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="974b9-127">In order to modify a partition scheme, you must first delete the scheme and then create a new one with the desired properties using the Create Partition Wizard.</span></span> <span data-ttu-id="974b9-128">詳細については、「**パーティションテーブルとパーティションインデックスの作成**」の「 [SQL Server Management Studio を使用したパーティションテーブルとパーティションインデックスの作成](create-partitioned-tables-and-indexes.md#SSMSProcedure)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974b9-128">For more information, see [Create Partitioned Tables and Indexes Using SQL Server Management Studio](create-partitioned-tables-and-indexes.md#SSMSProcedure) under **Create Partitioned Tables and Indexes**.</span></span>  
  
#### <a name="to-delete-a-partition-scheme"></a><span data-ttu-id="974b9-129">パーティション構成を削除するには</span><span class="sxs-lookup"><span data-stu-id="974b9-129">To delete a partition scheme</span></span>  
  
1.  <span data-ttu-id="974b9-130">プラス記号をクリックして、パーティション構成を削除するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="974b9-130">Click the plus sign to expand the database where you want to delete the partition scheme.</span></span>  
  
2.  <span data-ttu-id="974b9-131">プラス記号をクリックして **[ストレージ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="974b9-131">Click the plus sign to expand the **Storage** folder.</span></span>  
  
3.  <span data-ttu-id="974b9-132">プラス記号をクリックして **[パーティション構成]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="974b9-132">Click the plus sign to expand the **Partition Schemes** folder.</span></span>  
  
4.  <span data-ttu-id="974b9-133">削除するパーティション構成を右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="974b9-133">Right-click the partition scheme you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="974b9-134">**[オブジェクトの削除]** ダイアログ ボックスで、正しいパーティション構成が選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="974b9-134">In the **Delete Object** dialog box, ensure that the correct partition scheme is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="974b9-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="974b9-135">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-partition-scheme"></a><span data-ttu-id="974b9-136">パーティション構成を変更するには</span><span class="sxs-lookup"><span data-stu-id="974b9-136">To modify a partition scheme</span></span>  
  
1.  <span data-ttu-id="974b9-137">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="974b9-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="974b9-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="974b9-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="974b9-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="974b9-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- add five new filegroups to the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test1fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test4fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test5fg;  
    GO  
    -- if the "myRangePF1" partition function and the "myRangePS1" partition scheme exist,  
    -- drop them from the AdventureWorks2012 database  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
    DROP PARTITION FUNCTION myRangePF1;  
    GO  
    IF EXISTS (SELECT * FROM sys.partition_schemes  
        WHERE name = 'myRangePS1')  
    DROP PARTITION SCHEME myRangePS1;  
    GO  
    -- create the new partition function "myRangePF1" with four partition groups  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    -- create the new partition scheme "myRangePS1"that will use   
    -- the "myRangePF1" partition function with five file groups.  
    -- The last filegroup, "test5fg," will be kept empty but marked  
    -- as the next used filegroup in the partition scheme.  
    CREATE PARTITION SCHEME myRangePS1  
    AS PARTITION myRangePF1  
    TO (test1fg, test2fg, test3fg, test4fg, test5fg);  
    GO  
    --Split "myRangePS1" between boundary_values 100 and 1000  
    --to create two partitions between boundary_values 100 and 500  
    --and between boundary_values 500 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    SPLIT RANGE (500);  
    GO  
    -- Allow the "myRangePS1" partition scheme to use the filegroup "test5fg"  
    -- for the partition with boundary_values of 100 and 500  
    ALTER PARTITION SCHEME myRangePS1  
    NEXT USED test5fg;  
    GO  
    ```  
  
 <span data-ttu-id="974b9-140">詳細については、「[ALTER PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-scheme-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974b9-140">For more information, see [ALTER PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-scheme-transact-sql).</span></span>  
  
  
