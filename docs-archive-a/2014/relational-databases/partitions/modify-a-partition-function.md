---
title: パーティション関数の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae5bfc09-f27a-4ea9-9518-485278b11674
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bf14e633e62839b1abca7f38f833efab933c18f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713101"
---
# <a name="modify-a-partition-function"></a><span data-ttu-id="f23a5-102">パーティション関数の変更</span><span class="sxs-lookup"><span data-stu-id="f23a5-102">Modify a Partition Function</span></span>
  <span data-ttu-id="f23a5-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用してパーティション テーブルまたはパーティション インデックスのパーティション関数で、指定するパーティションの数を 1 つずつ増減させることにより、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でのテーブルまたはインデックスのパーティション分割方法を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f23a5-103">You can change the way a table or index is partitioned in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by adding or subtracting the number of partitions specified, in increments of 1, in the partition function of the partitioned table or index by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f23a5-104">パーティションを追加するには、既存のパーティションを 2 つのパーティションに分割し、新しいパーティションの境界を再定義します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-104">When you add a partition, you do so by "splitting" an existing partition into two partitions and redefining the boundaries of the new partitions.</span></span> <span data-ttu-id="f23a5-105">パーティションを削除するには、2 つのパーティションの境界を 1 つのパーティションにマージします。</span><span class="sxs-lookup"><span data-stu-id="f23a5-105">When you drop a partition, you do so by "merging" the boundaries of two partitions into one.</span></span> <span data-ttu-id="f23a5-106">この最後の操作により、1 つのパーティションが再作成され、もう 1 つのパーティションは未割り当てのままになります。</span><span class="sxs-lookup"><span data-stu-id="f23a5-106">This last action repopulates one partition and leaves the other partition unassigned.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f23a5-107">複数のテーブルやインデックスで同じパーティション関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f23a5-107">More than one table or index can use the same partition function.</span></span> <span data-ttu-id="f23a5-108">パーティション関数を変更すると、1 回のトランザクションでそれらのテーブルやインデックスすべてに影響します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-108">When you modify a partition function, you affect all of them in a single transaction.</span></span> <span data-ttu-id="f23a5-109">パーティション関数を変更する場合は、事前にその依存関係を確認してください。</span><span class="sxs-lookup"><span data-stu-id="f23a5-109">Check the partition function's dependencies before modifying it.</span></span>  
  
 <span data-ttu-id="f23a5-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f23a5-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f23a5-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f23a5-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f23a5-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f23a5-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f23a5-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f23a5-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f23a5-114">**次を使用してパーティション関数を変更するには:**</span><span class="sxs-lookup"><span data-stu-id="f23a5-114">**To modify a partition function, using:**</span></span>  
  
     [<span data-ttu-id="f23a5-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f23a5-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f23a5-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f23a5-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f23a5-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="f23a5-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f23a5-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f23a5-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f23a5-119">ALTER PARTITION FUNCTION は、1 つのパーティションを 2 つに分割するか、または 2 つのパーティションを 1 つにマージする目的にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f23a5-119">ALTER PARTITION FUNCTION can only be used for splitting one partition into two, or for merging two partitions into one.</span></span> <span data-ttu-id="f23a5-120">テーブルまたはインデックスのパーティション分割方法を変更する (たとえば 10 個のパーティションから 5 個のパーティションに変更する) には、次のいずれかの方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f23a5-120">To change the way a table or index is partitioned (from 10 partitions to 5, for example), you can use any one of the following options:</span></span>  
  
    -   <span data-ttu-id="f23a5-121">適切なパーティション関数でパーティション テーブルを新規作成し、INSERT INTO ...SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたは **の** パーティションの管理ウィザード [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で古いテーブルから新しいテーブルにデータを挿入します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-121">Create a new partitioned table with the desired partition function, and then insert the data from the old table into the new table by using either an INSERT INTO ... SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or the **Manage Partition Wizard** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
    -   <span data-ttu-id="f23a5-122">パーティション分割されたクラスター化インデックスを、ヒープ上に作成します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-122">Create a partitioned clustered index on a heap.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f23a5-123">パーティション分割されたクラスター化インデックスを削除すると、パーティション分割されたヒープが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f23a5-123">Dropping a partitioned clustered index results in a partitioned heap.</span></span>  
  
    -   <span data-ttu-id="f23a5-124">[!INCLUDE[tsql](../../includes/tsql-md.md)] の CREATE INDEX ステートメントと DROP EXISTING = ON 句を使用して、既存のパーティション インデックスを削除および再構築します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-124">Drop and rebuild an existing partitioned index by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX statement with the DROP EXISTING = ON clause.</span></span>  
  
    -   <span data-ttu-id="f23a5-125">一連の ALTER PARTITION FUNCTION ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-125">Perform a sequence of ALTER PARTITION FUNCTION statements.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f23a5-126">では、パーティション関数の変更に関するレプリケーションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f23a5-126">does not provide replication support for modifying a partition function.</span></span> <span data-ttu-id="f23a5-127">パブリケーション データベースのパーティション関数に変更を加える場合は、サブスクリプション データベースでこの操作を手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f23a5-127">If you want to make changes to a partition function in the publication database, you must do this manually in the subscription database.</span></span>  
  
-   <span data-ttu-id="f23a5-128">ALTER PARTITION FUNCTION の影響を受けるすべてのファイル グループは、オンラインである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f23a5-128">All filegroups that are affected by ALTER PARTITION FUNCTION must be online.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f23a5-129">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f23a5-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f23a5-130">Permissions</span><span class="sxs-lookup"><span data-stu-id="f23a5-130">Permissions</span></span>  
 <span data-ttu-id="f23a5-131">次の権限のいずれかを使用すると、ALTER PARTITION FUNCTION を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f23a5-131">Any one of the following permissions can be used to execute ALTER PARTITION FUNCTION:</span></span>  
  
-   <span data-ttu-id="f23a5-132">ALTER ANY DATASPACE 権限。</span><span class="sxs-lookup"><span data-stu-id="f23a5-132">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="f23a5-133">この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="f23a5-133">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="f23a5-134">パーティション関数が作成されたデータベースでの CONTROL または ALTER 権限。</span><span class="sxs-lookup"><span data-stu-id="f23a5-134">CONTROL or ALTER permission on the database in which the partition function was created.</span></span>  
  
-   <span data-ttu-id="f23a5-135">パーティション関数が作成されたデータベースのサーバーでの CONTROL SERVER または ALTER ANY DATABASE 権限。</span><span class="sxs-lookup"><span data-stu-id="f23a5-135">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition function was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f23a5-136">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f23a5-136">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f23a5-137">**パーティション関数を変更するには:**</span><span class="sxs-lookup"><span data-stu-id="f23a5-137">**To modify a partition function:**</span></span>  
  
 <span data-ttu-id="f23a5-138">この操作は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では実行できません。</span><span class="sxs-lookup"><span data-stu-id="f23a5-138">This specific action cannot be performed using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f23a5-139">パーティション関数を変更するには、最初にパーティション関数を削除し、パーティションの作成ウィザードを使用して必要なプロパティを持つ新しいパーティション関数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f23a5-139">In order to modify a partition function, you must first delete the function and then create a new one with the desired properties using the Create Partition Wizard.</span></span> <span data-ttu-id="f23a5-140">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="f23a5-140">For more information, see</span></span>  
  
#### <a name="to-delete-a-partition-function"></a><span data-ttu-id="f23a5-141">パーティション関数を削除するには</span><span class="sxs-lookup"><span data-stu-id="f23a5-141">To delete a partition function</span></span>  
  
1.  <span data-ttu-id="f23a5-142">パーティション関数を削除するデータベースを展開し、 **ストレージ** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-142">Expand the database where you want to delete the partition function and then expand the **Storage** folder.</span></span>  
  
2.  <span data-ttu-id="f23a5-143">**パーティション関数** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-143">Expand the **Partition Functions** folder.</span></span>  
  
3.  <span data-ttu-id="f23a5-144">削除するパーティション関数を右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23a5-144">Right-click the partition function you want to delete and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="f23a5-145">**[オブジェクトの削除]** ダイアログ ボックスで、正しいパーティション関数が選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23a5-145">In the **Delete Object** dialog box, ensure that the correct partition function is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f23a5-146">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f23a5-146">Using Transact-SQL</span></span>  
  
#### <a name="to-split-a-single-partition-into-two-partitions"></a><span data-ttu-id="f23a5-147">1 つのパーティションを 2 つのパーティションに分割するには</span><span class="sxs-lookup"><span data-stu-id="f23a5-147">To split a single partition into two partitions</span></span>  
  
1.  <span data-ttu-id="f23a5-148">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-148">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f23a5-149">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23a5-149">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f23a5-150">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23a5-150">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Look for a previous version of the partition function "myRangePF1" and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called "myRangePF1" that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Split the partition between boundary_values 100 and 1000  
    --to create two partitions between boundary_values 100 and 500  
    --and between boundary_values 500 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    SPLIT RANGE (500);  
    ```  
  
#### <a name="to-merge-two-partitions-into-one-partition"></a><span data-ttu-id="f23a5-151">2 つのパーティションを 1 つのパーティションにマージするには</span><span class="sxs-lookup"><span data-stu-id="f23a5-151">To merge two partitions into one partition</span></span>  
  
1.  <span data-ttu-id="f23a5-152">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f23a5-152">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f23a5-153">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23a5-153">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f23a5-154">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23a5-154">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Look for a previous version of the partition function "myRangePF1" and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called "myRangePF1" that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Merge the partitions between boundary_values 1 and 100  
    --and between boundary_values 100 and 1000 to create one partition  
    --between boundary_values 1 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    MERGE RANGE (100);  
    ```  
  
 <span data-ttu-id="f23a5-155">詳細については、「[ALTER PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-function-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f23a5-155">For more information, see [ALTER PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-function-transact-sql).</span></span>  
  
  
