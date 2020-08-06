---
title: パーティション テーブルとパーティション インデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.createpartition.partitionscheme.f1
- sql12.swb.createpartition.selectoutput.f1
- sql12.swb.createpartition.finish.f1
- sql12.swb.createpartition.summary.f1
- sql12.swb.createpartition.mappartition.f1
- sql12.swb.createpartition.partitioncolumn.f1
- sql12.swb.createpartition.progress.f1
- sql12.swb.createpartition.createjob.f1
- sql12.swb.createpartition.getstart.f1
- sql12.swb.createpartition.partitionfunction.f1
helpviewer_keywords:
- partitioned indexes [SQL Server], creating
- partition schemes [SQL Server], creating
- partition functions [SQL Server], creating
- partitioned tables [SQL Server], creating
- partition functions [SQL Server]
- partition schemes [SQL Server]
ms.assetid: 7641df10-1921-42a7-ba6e-4cb03b3ba9c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 76ccd8b784902f8542f06f3823e5f8dcb78e9201
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639470"
---
# <a name="create-partitioned-tables-and-indexes"></a><span data-ttu-id="cb813-102">パーティション テーブルとパーティション インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="cb813-102">Create Partitioned Tables and Indexes</span></span>
  <span data-ttu-id="cb813-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、パーティション テーブルまたはパーティション インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb813-103">You can create a partitioned table or index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cb813-104">パーティション テーブルとパーティション インデックスのデータは、データベース内の複数のファイル グループに分散できるように、行方向に複数の単位に分割されています。</span><span class="sxs-lookup"><span data-stu-id="cb813-104">The data in partitioned tables and indexes is horizontally divided into units that can be spread across more than one filegroup in a database.</span></span> <span data-ttu-id="cb813-105">パーティション分割により、大規模なテーブルとインデックスの管理の可能性と拡張性が向上します。</span><span class="sxs-lookup"><span data-stu-id="cb813-105">Partitioning can make large tables and indexes more manageable and scalable.</span></span>  
  
 <span data-ttu-id="cb813-106">一般に、パーティション テーブルまたはパーティション インデックスの作成は、次の 4 つの操作で構成されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-106">Creating a partitioned table or index typically happens in four parts:</span></span>  
  
1.  <span data-ttu-id="cb813-107">ファイル グループと、パーティション構成で指定されたパーティションを保持する対応するファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-107">Create a filegroup or filegroups and corresponding files that will hold the partitions specified by the partition scheme.</span></span>  
  
2.  <span data-ttu-id="cb813-108">テーブルまたはインデックスの行を指定された列の値に基づいてパーティションにマップするパーティション関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-108">Create a partition function that maps the rows of a table or index into partitions based on the values of a specified column.</span></span>  
  
3.  <span data-ttu-id="cb813-109">パーティション テーブルまたはパーティション インデックスのパーティションを新しいファイル グループにマップするパーティション構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-109">Create a partition scheme that maps the partitions of a partitioned table or index to the new filegroups.</span></span>  
  
4.  <span data-ttu-id="cb813-110">テーブルまたはインデックスを作成または変更し、格納場所としてそのパーティション構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-110">Create or modify a table or index and specify the partition scheme as the storage location.</span></span>  
  
 <span data-ttu-id="cb813-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="cb813-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cb813-112">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="cb813-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cb813-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="cb813-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cb813-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cb813-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cb813-115">**以下を使用してパーティション テーブルまたはパーティション インデックスを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="cb813-115">**To create a partitioned table or index, using:**</span></span>  
  
     [<span data-ttu-id="cb813-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cb813-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cb813-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cb813-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cb813-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="cb813-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cb813-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="cb813-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cb813-120">パーティション関数および構成のスコープは、それが作成されたデータベースに制限されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-120">The scope of a partition function and scheme is limited to the database in which they have been created.</span></span> <span data-ttu-id="cb813-121">データベース内では、パーティション関数は他の関数とは別の名前空間に配置されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-121">Within the database, partition functions reside in a separate namespace from other functions.</span></span>  
  
-   <span data-ttu-id="cb813-122">パーティション関数内のいずれかの行に null 値を持つパーティション分割列がある場合、これらの行は左端のパーティションに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cb813-122">If any rows within a partition function have partitioning columns with null values, these rows are allocated to the left-most partition.</span></span> <span data-ttu-id="cb813-123">ただし、NULL が境界値として指定され、RIGHT が指定されている場合、NULL 値は左端のパーティションを空にしたまま 2 番目のパーティションに配置されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-123">However, if NULL is specified as a boundary value and RIGHT is indicated, the left-most partition remains empty and NULL values are placed in the second partition.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cb813-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cb813-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cb813-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="cb813-125">Permissions</span></span>  
 <span data-ttu-id="cb813-126">パーティション テーブルを作成するには、データベースでの CREATE TABLE 権限と、テーブルを作成する構成に対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cb813-126">Creating a partitioned table requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span> <span data-ttu-id="cb813-127">パーティション インデックスを作成するには、インデックスを作成するテーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cb813-127">Creating a partitioned index requires ALTER permission on the table or view where the index is being created.</span></span> <span data-ttu-id="cb813-128">パーティション テーブルまたはパーティション インデックスを作成するには、次の追加の権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="cb813-128">Creating either a partitioned table or index requires any one of the following additional permissions:</span></span>  
  
-   <span data-ttu-id="cb813-129">ALTER ANY DATASPACE 権限。</span><span class="sxs-lookup"><span data-stu-id="cb813-129">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="cb813-130">この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="cb813-130">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="cb813-131">パーティション関数およびパーティション構成を作成するデータベースに対する CONTROL 権限または ALTER 権限。</span><span class="sxs-lookup"><span data-stu-id="cb813-131">CONTROL or ALTER permission on the database in which the partition function and partition scheme are being created.</span></span>  
  
-   <span data-ttu-id="cb813-132">パーティション関数およびパーティション構成を作成するデータベースのサーバーに対する CONTROL SERVER 権限または ALTER ANY DATABASE 権限。</span><span class="sxs-lookup"><span data-stu-id="cb813-132">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition function and partition scheme are being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cb813-133">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="cb813-133">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cb813-134">次の手順を実行して、1 つまたは複数のファイル グループ、対応するファイルと、およびテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-134">Follow the steps in this procedure to create one or more filegroups, corresponding files, and a table.</span></span> <span data-ttu-id="cb813-135">これらのオブジェクトは、次の手順でパーティション テーブルを作成するときに参照します。</span><span class="sxs-lookup"><span data-stu-id="cb813-135">You will reference these objects in the next procedure when you create the partitioned table.</span></span>  
  
#### <a name="to-create-new-filegroups-for-a-partitioned-table"></a><span data-ttu-id="cb813-136">パーティション テーブルの新しいファイル グループを作成するには</span><span class="sxs-lookup"><span data-stu-id="cb813-136">To create new filegroups for a partitioned table</span></span>  
  
1.  <span data-ttu-id="cb813-137">オブジェクト エクスプローラーで、パーティション テーブルを作成するデータベースを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-137">In Object Explorer, right-click the database in which you want to create a partitioned table and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="cb813-138">[**データベースのプロパティ -** *database_name*] ダイアログ ボックスの **[ページの選択]** で、 **[ファイル グループ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-138">In the **Database Properties -** *database_name* dialog box, under **Select a page**, select **Filegroups**.</span></span>  
  
3.  <span data-ttu-id="cb813-139">**[行]** で、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-139">Under **Rows**, click **Add**.</span></span> <span data-ttu-id="cb813-140">新しい行に、ファイル グループ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-140">In the new row, enter the filegroup name.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="cb813-141">パーティションを作成するときは常に、境界値に指定されたファイル グループの数より 1 つ多い数のファイル グループが必要です。</span><span class="sxs-lookup"><span data-stu-id="cb813-141">You must always have one extra filegroup in addition to the number of filegroups specified for the boundary values when you are creating partitions.</span></span>  
  
4.  <span data-ttu-id="cb813-142">行の追加を繰り返して、パーティション テーブルのすべてのファイル グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-142">Continue adding rows until you have created all of the filegroups for the partitioned table.</span></span>  
  
5.  <span data-ttu-id="cb813-143">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-143">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="cb813-144">**[ページの選択]** で、 **[ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-144">Under **Select a page**, select **Files**.</span></span>  
  
7.  <span data-ttu-id="cb813-145">**[行]** で、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-145">Under **Rows**, click **Add**.</span></span> <span data-ttu-id="cb813-146">新しい行にファイル名を入力し、ファイル グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-146">In the new row, enter a filename and select a filegroup.</span></span>  
  
8.  <span data-ttu-id="cb813-147">行の追加を繰り返して、各ファイル グループに少なくとも 1 つのファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-147">Continue adding rows until you have created at least one file for each filegroup.</span></span>  
  
9. <span data-ttu-id="cb813-148">**[テーブル]** フォルダーを展開し、通常と同じようにテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-148">Expand the **Tables** folder and create a table as you normally would.</span></span> <span data-ttu-id="cb813-149">詳しくは、「[テーブルの作成 &#40;データベース エンジン&#41;](../tables/create-tables-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb813-149">For more information, see [Create Tables &#40;Database Engine&#41;](../tables/create-tables-database-engine.md).</span></span> <span data-ttu-id="cb813-150">または、次の手順で既存のテーブルを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb813-150">Alternatively, you can specify an existing table in the next procedure.</span></span>  
  
#### <a name="to-create-a-partitioned-table"></a><span data-ttu-id="cb813-151">パーティション テーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="cb813-151">To create a partitioned table</span></span>  
  
1.  <span data-ttu-id="cb813-152">パーティション分割するテーブルを右クリックし、 **[ストレージ]** をポイントします。次に、 **[パーティションの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-152">Right-click the table that you wish to partition, point to **Storage**, and then click **Create Partition...**.</span></span>  
  
2.  <span data-ttu-id="cb813-153">**パーティションの作成ウィザード**の **[パーティションの作成ウィザードへようこそ]** ページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-153">In the **Create Partition Wizard**, on the **Welcome to the Create Partition Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="cb813-154">**[パーティション分割列の選択]** ページの **[使用可能なパーティション分割列]** グリッドで、テーブルのパーティション分割に使用する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-154">On the **Select a Partitioning Column** page, in the **Available partitioning columns** grid, select the column on which you want to partition your table.</span></span> <span data-ttu-id="cb813-155">**[使用可能なパーティション分割列]** グリッドには、データのパーティション分割に使用できるデータ型の列だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-155">Only columns with data types that can be used to partition data will be displayed in the **Available partitioning columns** grid.</span></span> <span data-ttu-id="cb813-156">計算列をパーティション分割列として選択する場合は、列を PERSISTED として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb813-156">If you select a computed column as the partitioning column, the column must be designated as a persisted column.</span></span>  
  
     <span data-ttu-id="cb813-157">パーティション分割列とその値の範囲の選択肢は、主に、データをどの程度論理的にグループ化できるかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="cb813-157">The choices you have for the partitioning column and the values range are determined primarily by the extent to which your data can be grouped in a logical way.</span></span> <span data-ttu-id="cb813-158">たとえば、月や四半期に基づいてデータを論理グループに分割することができます。</span><span class="sxs-lookup"><span data-stu-id="cb813-158">For example, you may choose to divide your data into logical groupings by months or quarters of a year.</span></span> <span data-ttu-id="cb813-159">この論理グループがテーブル パーティションの管理に適しているかどうかは、データに対してどのようなクエリを実行する予定かによって決まります。</span><span class="sxs-lookup"><span data-stu-id="cb813-159">The queries you plan to make against your data will determine whether this logical grouping is adequate for managing your table partitions.</span></span> <span data-ttu-id="cb813-160">すべてのデータ型は、、、、、、、、、 `text` `ntext` `image` `xml` `timestamp` `varchar(max)` `nvarchar(max)` `varbinary(max)` 別名データ型、または CLR ユーザー定義データ型を除く、パーティション分割列として使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb813-160">All data types are valid for use as partitioning columns, except `text`, `ntext`, `image`, `xml`, `timestamp`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, alias data types, or CLR user-defined data types.</span></span>  
  
     <span data-ttu-id="cb813-161">このページで使用できる他のオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb813-161">The following additional options are available on this page:</span></span>  
  
     <span data-ttu-id="cb813-162">**[このテーブルを選択したパーティション テーブルに併置する]**</span><span class="sxs-lookup"><span data-stu-id="cb813-162">**Collocate this table to the selected partitioned table**</span></span>  
     <span data-ttu-id="cb813-163">パーティション分割列でこのテーブルと連結する関連データが含まれている、パーティション テーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="cb813-163">Allows you to select a partitioned table that contains related data to join with this table on the partitioning column.</span></span> <span data-ttu-id="cb813-164">通常、テーブルのパーティションをパーティション分割列で連結すると、クエリの効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="cb813-164">Tables with partitions joined on the partitioning columns are typically queried more efficiently.</span></span>  
  
     <span data-ttu-id="cb813-165">**[一意でないインデックスと一意のインデックスをインデックス付きパーティション列にストレージ固定]**</span><span class="sxs-lookup"><span data-stu-id="cb813-165">**Storage-align non-unique indexes and unique indexes with an indexed partition column**</span></span>  
     <span data-ttu-id="cb813-166">同じパーティション構成でパーティション分割されたテーブルのすべてのインデックスを固定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-166">Aligns all indexes of the table that are partitioned with the same partition scheme.</span></span> <span data-ttu-id="cb813-167">テーブルとインデックスを固定すると、データが同じアルゴリズムでパーティション分割されるため、パーティションをパーティション テーブル内外に効果的に移動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb813-167">When a table and its indexes are aligned, you can move partitions in and out of partitioned tables more effectively, because your data is partitioned with the same algorithm.</span></span>  
  
     <span data-ttu-id="cb813-168">パーティション分割列とその他のオプションを選択したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-168">After selecting the partitioning column and any other options, click **Next**.</span></span>  
  
4.  <span data-ttu-id="cb813-169">**[パーティション関数の選択]** ページの **[パーティション関数の選択**] で、 **[新しいパーティション関数]** または **[既存のパーティション関数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-169">On the **Select a Partition Function** page, under **Select partition function**, click either **New partition function** or **Existing partition function**.</span></span> <span data-ttu-id="cb813-170">**[新しいパーティション関数]** を選択した場合は、関数の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-170">If you choose **New partition function**, enter the name of the function.</span></span> <span data-ttu-id="cb813-171">**[既存のパーティション関数]** を選択した場合は、使用する関数の名前を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-171">If you choose **Existing partition function**, select the name of the function you'd like to use from the list.</span></span> <span data-ttu-id="cb813-172">データベースに他のパーティション関数がない場合、 **[既存のパーティション関数]** オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="cb813-172">The **Existing partition function** option will not be available if there are no other partition functions on the database.</span></span>  
  
     <span data-ttu-id="cb813-173">このページを完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-173">After completing this page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="cb813-174">**[パーティション構成の選択]** ページの **[パーティション構成の選択]** で、 **[新しいパーティション構成]** または **[既存のパーティション構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-174">On the **Select a Partition Scheme** page, under **Select partition scheme**, click either **New partition scheme** or **Existing partition scheme**.</span></span> <span data-ttu-id="cb813-175">**[新しいパーティション構成]** を選択した場合は、構成の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-175">If you choose **New partition scheme**, enter the name of the scheme.</span></span> <span data-ttu-id="cb813-176">**[既存のパーティション構成]** を選択した場合は、使用する構成の名前を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-176">If you choose **Existing partition scheme**, select the name of the scheme you'd like to use from the list.</span></span> <span data-ttu-id="cb813-177">データベースに他のパーティション構成がない場合、 **[既存のパーティション構成]** オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="cb813-177">The **Existing partition scheme** option will not be available if there are no other partition schemes on the database.</span></span>  
  
     <span data-ttu-id="cb813-178">このページを完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-178">After completing this page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="cb813-179">**[パーティションのマップ]** ページの **[範囲]** で、 **[左側の境界]** または **[右側の境界]** を選択して、作成する各ファイル グループ内に最大または最小の境界値を含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-179">On the **Map Partitions** page, under **Range**, select either **Left boundary** or **Right boundary** to specify whether to include the highest or lowest bounding value within each filegroup you create.</span></span> <span data-ttu-id="cb813-180">パーティションを作成するときは常に、境界値に指定されたファイル グループの数に 1 つ余分なファイル グループを足した数を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb813-180">You must always enter one extra filegroup in addition to the number of filegroups specified for the boundary values when you are creating partitions.</span></span>  
  
     <span data-ttu-id="cb813-181">**[ファイル グループを選択して境界値を指定します]** グリッドの **[ファイル グループ]** で、データをパーティション分割するファイル グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-181">In the **Select filegroups and specify boundary values** grid, under **Filegroup**, select the filegroup into which you want to partition your data.</span></span> <span data-ttu-id="cb813-182">**[境界]** で、各ファイル グループの境界値を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-182">Under **Boundary**, enter the boundary value for each filegroup.</span></span> <span data-ttu-id="cb813-183">境界値を空にした場合、パーティション関数は、パーティション関数名を使用して、テーブルまたはインデックス全体を単一のパーティションにマップします。</span><span class="sxs-lookup"><span data-stu-id="cb813-183">If boundary value is left empty, the partition function maps the whole table or index into a single partition using the partition function name.</span></span>  
  
     <span data-ttu-id="cb813-184">このページで使用できる他のオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb813-184">The following additional options are available on this page:</span></span>  
  
     <span data-ttu-id="cb813-185">**[境界の設定]**</span><span class="sxs-lookup"><span data-stu-id="cb813-185">**Set Boundaries...**</span></span>  
     <span data-ttu-id="cb813-186">**[境界値の設定]** ダイアログ ボックスを開き、パーティションの境界値と日付範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-186">Opens the **Set Boundary Values** dialog box to select the boundary values and date ranges you want for your partitions.</span></span> <span data-ttu-id="cb813-187">このオプションは `date` 、、、 `datetime` `smalldatetime` 、 `datetime2` 、または `datetimeoffset` のいずれかのデータ型を含むパーティション分割列を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb813-187">This option is only available when you have selected a partitioning column that contains one of the following data types: `date`, `datetime`, `smalldatetime`, `datetime2`, or `datetimeoffset`.</span></span>  
  
     <span data-ttu-id="cb813-188">**[ストレージの推定]**</span><span class="sxs-lookup"><span data-stu-id="cb813-188">**Estimate storage**</span></span>  
     <span data-ttu-id="cb813-189">パーティションに指定された各ファイル グループのストレージの行数、必要な領域、および使用できる領域を推定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-189">Estimates rowcount, required space, and available space for storage for each filegroup specified for the partitions.</span></span> <span data-ttu-id="cb813-190">これらの値は、読み取り専用の値としてグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-190">These values are displayed in the grid as read-only values.</span></span>  
  
     <span data-ttu-id="cb813-191">**[境界値の設定]** ダイアログ ボックスでは、次の追加オプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="cb813-191">The **Set Boundary Values** dialog box allows for the following additional options:</span></span>  
  
     <span data-ttu-id="cb813-192">**開始日**</span><span class="sxs-lookup"><span data-stu-id="cb813-192">**Start date**</span></span>  
     <span data-ttu-id="cb813-193">パーティションの範囲値の開始日を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-193">Selects the starting date for the range values of your partitions.</span></span>  
  
     <span data-ttu-id="cb813-194">**終了日**</span><span class="sxs-lookup"><span data-stu-id="cb813-194">**End date**</span></span>  
     <span data-ttu-id="cb813-195">パーティションの範囲値の終了日を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-195">Selects the ending date for the range values of your partitions.</span></span> <span data-ttu-id="cb813-196">**[パーティションのマップ]** ページで **[左側の境界]** を選択した場合、この日付は、各ファイル グループまたはパーティションの最後の値になります。</span><span class="sxs-lookup"><span data-stu-id="cb813-196">If you selected **Left boundary** on the **Map Partitions** page, this date will be the last value for each filegroup/partition.</span></span> <span data-ttu-id="cb813-197">**[パーティションのマップ]** ページで **[右側の境界]** を選択した場合、この日付は、最後から 2 番目のファイル グループの最初の値になります。</span><span class="sxs-lookup"><span data-stu-id="cb813-197">If you selected **Right boundary** on the **Map Partitions** page, this date will be the first value in the next-to-last filegroup.</span></span>  
  
     <span data-ttu-id="cb813-198">**日付範囲**</span><span class="sxs-lookup"><span data-stu-id="cb813-198">**Date range**</span></span>  
     <span data-ttu-id="cb813-199">各パーティションの日付粒度または範囲値の増分を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-199">Selects the date granularity or range value increment you want for each partition.</span></span>  
  
     <span data-ttu-id="cb813-200">このページを完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-200">After completing this page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="cb813-201">**[出力オプションの選択]** ページで、パーティション テーブルを完了する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-201">In the **Select an Output Option** page, specify how you want to complete your partitioned table.</span></span> <span data-ttu-id="cb813-202">ウィザードの前のページに基づいて SQL スクリプトを作成するには、 **[スクリプトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-202">Select **Create Script** to create a SQL script based the previous pages in the wizard.</span></span> <span data-ttu-id="cb813-203">ウィザードの残りのすべてのページが完了した後に新しいパーティション テーブルを作成するには、 **[すぐに実行する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-203">Select **Run immediately** to create the new partitioned table after completing all remaining pages in the wizard.</span></span> <span data-ttu-id="cb813-204">事前に定義した時刻に新しいパーティション テーブルを作成するには、 **[スケジュール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-204">Select **Schedule** to create the new partitioned table at a predetermined time in the future.</span></span>  
  
     <span data-ttu-id="cb813-205">**[スクリプトの作成]** を選択した場合、 **[スクリプト オプション]** で次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb813-205">If you select **Create script**, the following options are available under **Script options**:</span></span>  
  
     <span data-ttu-id="cb813-206">**[スクリプトをファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="cb813-206">**Script to file**</span></span>  
     <span data-ttu-id="cb813-207">スクリプトを .sql ファイルとして生成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-207">Generates the script as a .sql file.</span></span> <span data-ttu-id="cb813-208">**[ファイル名]** ボックスにファイルの名前と場所を入力するか、または **[参照]** をクリックして **[スクリプト ファイルの場所]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb813-208">Enter a file name and location in the **File name** box or click **Browse** to open the **Script File Location** dialog box.</span></span> <span data-ttu-id="cb813-209">**[名前を付けて保存]** で、 **[Unicode テキスト]** または **[ANSI テキスト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-209">From **Save As**, select **Unicode text** or **ANSI text**.</span></span>  
  
     <span data-ttu-id="cb813-210">**[スクリプトをクリップボードに保存]**</span><span class="sxs-lookup"><span data-stu-id="cb813-210">**Script to Clipboard**</span></span>  
     <span data-ttu-id="cb813-211">スクリプトをクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="cb813-211">Saves the script to the Clipboard.</span></span>  
  
     <span data-ttu-id="cb813-212">**[スクリプトを新しいクエリ ウィンドウに保存]**</span><span class="sxs-lookup"><span data-stu-id="cb813-212">**Script to New Query Window**</span></span>  
     <span data-ttu-id="cb813-213">新しいクエリ エディター ウィンドウにスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-213">Generates the script to a new Query Editor window.</span></span> <span data-ttu-id="cb813-214">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="cb813-214">This is the default selection.</span></span>  
  
     <span data-ttu-id="cb813-215">**[スケジュール]** を選択した場合は、 **[スケジュールの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-215">If you select **Schedule**, click **Change schedule**.</span></span>  
  
    1.  <span data-ttu-id="cb813-216">**[新しいジョブ スケジュール]** ダイアログ ボックスで、 **[名前]** ボックスに、ジョブのスケジュールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-216">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
    2.  <span data-ttu-id="cb813-217">**[スケジュールの種類]** ボックスで、スケジュールの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-217">On the **Schedule type** list, select the type of schedule:</span></span>  
  
        -   <span data-ttu-id="cb813-218">**[SQL Server エージェントの開始時に自動的に開始]**</span><span class="sxs-lookup"><span data-stu-id="cb813-218">**Start automatically when SQL Server Agent starts**</span></span>  
  
        -   <span data-ttu-id="cb813-219">**[CPU がアイドル状態になったときに開始]**</span><span class="sxs-lookup"><span data-stu-id="cb813-219">**Start whenever the CPUs become idle**</span></span>  
  
        -   <span data-ttu-id="cb813-220">**[定期的]** 。</span><span class="sxs-lookup"><span data-stu-id="cb813-220">**Recurring**.</span></span> <span data-ttu-id="cb813-221">新しいパーティション テーブルを新しい情報で定期的に更新するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-221">Select this option if your new partitioned table updates with new information on a regular basis.</span></span>  
  
        -   <span data-ttu-id="cb813-222">**[指定日時]** 。</span><span class="sxs-lookup"><span data-stu-id="cb813-222">**One time**.</span></span> <span data-ttu-id="cb813-223">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="cb813-223">This is the default selection.</span></span>  
  
    3.  <span data-ttu-id="cb813-224">**[有効]** チェック ボックスをオンまたはオフにして、スケジュールを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="cb813-224">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
    4.  <span data-ttu-id="cb813-225">**[定期的]** を選択した場合:</span><span class="sxs-lookup"><span data-stu-id="cb813-225">If you select **Recurring**:</span></span>  
  
        1.  <span data-ttu-id="cb813-226">**[頻度]** の **[実行]** ボックスの一覧で、実行の頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-226">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
            -   <span data-ttu-id="cb813-227">**[日単位]** を選択した場合は、 **[間隔]** ボックスに、ジョブ スケジュールを繰り返す頻度を日単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-227">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
            -   <span data-ttu-id="cb813-228">**[週単位]** を選択した場合は、 **[間隔]** ボックスに、ジョブ スケジュールを繰り返す頻度を週単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-228">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="cb813-229">ジョブ スケジュールを実行する曜日を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-229">Select the day or days of the week on which the job schedule is run.</span></span>  
  
            -   <span data-ttu-id="cb813-230">**[月単位]** を選択した場合は、 **[日]** または **[曜日]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-230">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                -   <span data-ttu-id="cb813-231">**[日]** を選択した場合は、ジョブ スケジュールを実行する日付と、ジョブ スケジュールを繰り返す頻度を月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-231">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="cb813-232">たとえば、隔月の 15 日にジョブ スケジュールを実行する場合は、 **[日]** を選択し、1 番目のボックスに「15」と入力し、2 番目のボックスに「2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-232">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="cb813-233">2 番目のボックスで使用できる最大の値は "99" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb813-233">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                -   <span data-ttu-id="cb813-234">**[曜日]** を選択した場合は、ジョブ スケジュールを実行する曜日と、ジョブ スケジュールを繰り返す頻度を月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-234">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="cb813-235">たとえば、隔月の最後の平日にジョブ スケジュールを実行する場合は、 **[日]** を選択し、リストから **[最終]** を選択します。次に 2 番目のリストから **[平日]** を選択し、最後のボックスに「2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-235">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="cb813-236">最初の 2 つのリストでは、特定の平日 (たとえば、日曜日や水曜日) に加えて、 **[第 1]** 、 **[第 2]** 、 **[第 3]** 、または **[第 4]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="cb813-236">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="cb813-237">最後のボックスで使用できる最大の値は "99" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb813-237">Please note that the largest number allowed in the last box is "99".</span></span>  
  
        2.  <span data-ttu-id="cb813-238">**[一日のうちの頻度]** で、頻度、ジョブ スケジュールを実行する当日にジョブ スケジュールを繰り返す頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-238">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
            -   <span data-ttu-id="cb813-239">**[1 回]** を選択した場合は、ジョブ スケジュールを実行する特定の時刻を **[1 回]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-239">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="cb813-240">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-240">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            -   <span data-ttu-id="cb813-241">**[間隔]** を選択した場合は、 **[頻度]** で選択した日にジョブ スケジュールを実行する頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-241">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="cb813-242">たとえば、ジョブ スケジュールを実行する当日に 2 時間おきにジョブ スケジュールを実行する場合は、 **[間隔]** を選択し、1 番目のボックスに「2」と入力してから、 **[時間]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-242">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="cb813-243">このリストでは、 **[分]** と **[秒]** を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb813-243">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="cb813-244">1 番目のボックスで使用できる最大の値は "100" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb813-244">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                 <span data-ttu-id="cb813-245">**[開始]** ボックスに、ジョブ スケジュールの実行を開始する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-245">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="cb813-246">**[終了]** ボックスに、ジョブ スケジュールの実行を終了する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-246">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="cb813-247">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-247">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        3.  <span data-ttu-id="cb813-248">**[期間]** で、 **[開始日]** に、ジョブ スケジュールの実行を開始する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-248">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="cb813-249">**[終了日]** を選択します。ジョブ スケジュールの実行を停止するタイミングを指定しない場合は、 **[終了日なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb813-249">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="cb813-250">**[終了日]** を選択した場合は、ジョブ スケジュールの実行を停止する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-250">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
    5.  <span data-ttu-id="cb813-251">**[指定日時]** を選択した場合は、 **[指定日時に発生]** の **[日付]** ボックスに、ジョブ スケジュールを実行する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-251">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="cb813-252">**[時刻]** ボックスに、ジョブ スケジュールを実行する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-252">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="cb813-253">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="cb813-253">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
    6.  <span data-ttu-id="cb813-254">**[概要]** の **[説明]** で、すべてのジョブ スケジュール設定が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb813-254">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
    7.  <span data-ttu-id="cb813-255">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-255">Click **OK**.</span></span>  
  
     <span data-ttu-id="cb813-256">このページを完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-256">After completing this page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="cb813-257">**[概要の確認]** ページの **[選択内容の確認]** で、使用可能なすべてのオプションを展開し、すべてのパーティション設定が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb813-257">On the **Review Summary** page, under **Review your selections**, expand all available options to verify that all partition settings are correct.</span></span> <span data-ttu-id="cb813-258">すべての設定が適切であることを確認したら、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-258">If everything is as expected, click **Finish**.</span></span>  
  
9. <span data-ttu-id="cb813-259">**[パーティションの作成ウィザードの進行状況]** ページで、パーティションの作成ウィザードの操作に関する状態情報を監視します。</span><span class="sxs-lookup"><span data-stu-id="cb813-259">On the **Create Partition Wizard Progress** page, monitor status information about the actions of the Create Partition Wizard.</span></span> <span data-ttu-id="cb813-260">ウィザードで選択したオプションに応じて、[進行状況] ページに 1 つまたは複数のアクションが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cb813-260">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="cb813-261">上部のボックスには、ウィザードの全体的な状態と受信した状態メッセージ、エラー メッセージ、および警告メッセージの数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-261">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="cb813-262">**[パーティションの作成ウィザードの進行状況]** ページでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb813-262">The following options are available on the **Create Partition Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="cb813-263">**詳細**</span><span class="sxs-lookup"><span data-stu-id="cb813-263">**Details**</span></span>  
     <span data-ttu-id="cb813-264">アクション、状態、およびウィザードで実行したアクションから返されたメッセージが提供されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-264">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="cb813-265">**操作**</span><span class="sxs-lookup"><span data-stu-id="cb813-265">**Action**</span></span>  
     <span data-ttu-id="cb813-266">各アクションの種類と名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb813-266">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="cb813-267">**状態**</span><span class="sxs-lookup"><span data-stu-id="cb813-267">**Status**</span></span>  
     <span data-ttu-id="cb813-268">全体としてウィザードのアクションが **[成功]** または **[失敗]** のいずれの値を返したかを示します。</span><span class="sxs-lookup"><span data-stu-id="cb813-268">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="cb813-269">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="cb813-269">**Message**</span></span>  
     <span data-ttu-id="cb813-270">プロセスから返されたすべてのエラー メッセージまたは警告メッセージを提供します。</span><span class="sxs-lookup"><span data-stu-id="cb813-270">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="cb813-271">**Report**</span><span class="sxs-lookup"><span data-stu-id="cb813-271">**Report**</span></span>  
     <span data-ttu-id="cb813-272">パーティションの作成ウィザードの結果を含むレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-272">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="cb813-273">**[レポートの表示]** 、 **[レポートをファイルに保存]** 、 **[レポートをクリップボードにコピー]** 、 **[レポートを電子メールとして送信]** の各オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="cb813-273">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="cb813-274">**[レポートの表示]**</span><span class="sxs-lookup"><span data-stu-id="cb813-274">**View Report**</span></span>  
     <span data-ttu-id="cb813-275">パーティションの作成ウィザードの進行状況に関するテキスト レポートを表示する **[レポートの表示]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb813-275">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="cb813-276">**[レポートをファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="cb813-276">**Save Report to File**</span></span>  
     <span data-ttu-id="cb813-277">**[レポートに名前を付けて保存]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb813-277">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="cb813-278">**[レポートをクリップボードにコピー]**</span><span class="sxs-lookup"><span data-stu-id="cb813-278">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="cb813-279">ウィザードの進行状況レポートの結果をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="cb813-279">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="cb813-280">**[レポートを電子メールとして送信]**</span><span class="sxs-lookup"><span data-stu-id="cb813-280">**Send Report as Email**</span></span>  
     <span data-ttu-id="cb813-281">ウィザードの進行状況レポートの結果を電子メール メッセージにコピーします。</span><span class="sxs-lookup"><span data-stu-id="cb813-281">Copies the results of the wizard's progress report into an email message.</span></span>  
  
     <span data-ttu-id="cb813-282">完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-282">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="cb813-283">パーティションの作成ウィザードによってパーティション関数とパーティション構成が作成され、指定したテーブルにパーティション分割が適用されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-283">The Create Partition Wizard creates the partition function and scheme and then applies the partitioning to the specified table.</span></span> <span data-ttu-id="cb813-284">テーブル パーティション分割を検証するには、オブジェクト エクスプローラーでテーブルを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-284">To verify the table partitioning, in Object Explorer, right-click the table and select **Properties**.</span></span> <span data-ttu-id="cb813-285">**[ストレージ]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-285">Click the **Storage** page.</span></span> <span data-ttu-id="cb813-286">このページには、パーティション関数の名前および構成やパーティションの数などの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-286">The page displays information such as the name of the partition function and scheme and the number of partitions.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cb813-287">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="cb813-287">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-partitioned-table"></a><span data-ttu-id="cb813-288">パーティション テーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="cb813-288">To create a partitioned table</span></span>  
  
1.  <span data-ttu-id="cb813-289">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="cb813-289">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cb813-290">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-290">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cb813-291">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb813-291">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cb813-292">この例では、新しいファイル グループ、パーティション関数とパーティション構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="cb813-292">The example creates new filegroups, a partition function, and a partition scheme.</span></span> <span data-ttu-id="cb813-293">パーティション構成を格納場所として指定した新しいテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-293">A new table is created with the partition scheme specified as the storage location.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Adds four new filegroups to the AdventureWorks2012 database  
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
  
    -- Adds one file for each filegroup.  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test1dat1,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t1dat1.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test1fg;  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test2dat2,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t2dat2.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test3dat3,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t3dat3.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test4dat4,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t4dat4.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test4fg;  
    GO  
    -- Creates a partition function called myRangePF1 that will partition a table into four partitions  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
        AS RANGE LEFT FOR VALUES (1, 100, 1000) ;  
    GO  
    -- Creates a partition scheme called myRangePS1 that applies myRangePF1 to the four filegroups created above  
    CREATE PARTITION SCHEME myRangePS1  
        AS PARTITION myRangePF1  
        TO (test1fg, test2fg, test3fg, test4fg) ;  
    GO  
    -- Creates a partitioned table called PartitionTable that uses myRangePS1 to partition col1  
    CREATE TABLE PartitionTable (col1 int PRIMARY KEY, col2 char(10))  
        ON myRangePS1 (col1) ;  
    GO  
    ```  
  
#### <a name="to-determine-if-a-table-is-partitioned"></a><span data-ttu-id="cb813-294">テーブルがパーティション分割されているかどうかを調べるには</span><span class="sxs-lookup"><span data-stu-id="cb813-294">To determine if a table is partitioned</span></span>  
  
1.  <span data-ttu-id="cb813-295">次のクエリでは、テーブル `PartitionTable` がパーティション分割されている場合、1 つ以上の行が返されます。</span><span class="sxs-lookup"><span data-stu-id="cb813-295">The following query returns one or more rows if the table `PartitionTable` is partitioned.</span></span> <span data-ttu-id="cb813-296">テーブルがパーティション分割されていない場合は、行が返されません。</span><span class="sxs-lookup"><span data-stu-id="cb813-296">If the table is not partitioned, no rows are returned.</span></span>  
  
    ```  
    SELECT *   
    FROM sys.tables AS t   
    JOIN sys.indexes AS i   
        ON t.[object_id] = i.[object_id]   
        AND i.[type] IN (0,1)   
    JOIN sys.partition_schemes ps   
        ON i.data_space_id = ps.data_space_id   
    WHERE t.name = 'PartitionTable';   
    GO  
    ```  
  
#### <a name="to-determine-the-boundary-values-for-a-partitioned-table"></a><span data-ttu-id="cb813-297">パーティション テーブルの境界値を調べるには</span><span class="sxs-lookup"><span data-stu-id="cb813-297">To determine the boundary values for a partitioned table</span></span>  
  
1.  <span data-ttu-id="cb813-298">次のクエリでは、 `PartitionTable` テーブルの各パーティションの境界値を返します。</span><span class="sxs-lookup"><span data-stu-id="cb813-298">The following query returns the boundary values for each partition in the `PartitionTable` table.</span></span>  
  
    ```  
    SELECT t.name AS TableName, i.name AS IndexName, p.partition_number, p.partition_id, i.data_space_id, f.function_id, f.type_desc, r.boundary_id, r.value AS BoundaryValue   
    FROM sys.tables AS t  
    JOIN sys.indexes AS i  
        ON t.object_id = i.object_id  
    JOIN sys.partitions AS p  
        ON i.object_id = p.object_id AND i.index_id = p.index_id   
    JOIN  sys.partition_schemes AS s   
        ON i.data_space_id = s.data_space_id  
    JOIN sys.partition_functions AS f   
        ON s.function_id = f.function_id  
    LEFT JOIN sys.partition_range_values AS r   
        ON f.function_id = r.function_id and r.boundary_id = p.partition_number  
    WHERE t.name = 'PartitionTable' AND i.type <= 1  
    ORDER BY p.partition_number;  
    ```  
  
#### <a name="to-determine-the-partition-column-for-a-partitioned-table"></a><span data-ttu-id="cb813-299">パーティション テーブルのパーティション列を調べるには</span><span class="sxs-lookup"><span data-stu-id="cb813-299">To determine the partition column for a partitioned table</span></span>  
  
1.  <span data-ttu-id="cb813-300">次のクエリでは、テーブルのパーティション分割列の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="cb813-300">The following query returns the name of the partitioning column for table.</span></span> <span data-ttu-id="cb813-301">[https://login.microsoftonline.com/consumers/](`PartitionTable`)</span><span class="sxs-lookup"><span data-stu-id="cb813-301">`PartitionTable`.</span></span>  
  
    ```  
    SELECT   
        t.[object_id] AS ObjectID   
        , t.name AS TableName   
        , ic.column_id AS PartitioningColumnID   
        , c.name AS PartitioningColumnName   
    FROM sys.tables AS t   
    JOIN sys.indexes AS i   
        ON t.[object_id] = i.[object_id]   
        AND i.[type] <= 1 -- clustered index or a heap   
    JOIN sys.partition_schemes AS ps   
        ON ps.data_space_id = i.data_space_id   
    JOIN sys.index_columns AS ic   
        ON ic.[object_id] = i.[object_id]   
        AND ic.index_id = i.index_id   
        AND ic.partition_ordinal >= 1 -- because 0 = non-partitioning column   
    JOIN sys.columns AS c   
        ON t.[object_id] = c.[object_id]   
        AND ic.column_id = c.column_id   
    WHERE t.name = 'PartitionTable' ;   
    GO  
    ```  
  
 <span data-ttu-id="cb813-302">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb813-302">For more information, see:</span></span>  
  
-   [<span data-ttu-id="cb813-303">ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cb813-303">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
-   [<span data-ttu-id="cb813-304">CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cb813-304">CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-partition-function-transact-sql)  
  
-   [<span data-ttu-id="cb813-305">CREATE PARTITION SCHEME &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cb813-305">CREATE PARTITION SCHEME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-partition-scheme-transact-sql)  
  
-   [<span data-ttu-id="cb813-306">CREATE TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cb813-306">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
  
