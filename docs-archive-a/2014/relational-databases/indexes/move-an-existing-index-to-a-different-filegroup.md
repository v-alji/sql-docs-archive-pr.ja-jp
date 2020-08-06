---
title: 既存のインデックスの別のファイル グループへの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- moving tables
- switching filegroups for index
- moving indexes
- indexes [SQL Server], moving
- filegroups [SQL Server], switching
ms.assetid: 167ebe77-487d-4ca8-9452-4b2c7d5cb96e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c99847dcb8d4d65272dd3660c7fd60d3efb8d951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645055"
---
# <a name="move-an-existing-index-to-a-different-filegroup"></a><span data-ttu-id="0d2fc-102">既存のインデックスの別のファイル グループへの移動</span><span class="sxs-lookup"><span data-stu-id="0d2fc-102">Move an Existing Index to a Different Filegroup</span></span>
  <span data-ttu-id="0d2fc-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、既存のインデックスを現在のファイル グループから別のファイル グループに移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-103">This topic describes how to move an existing index from its current filegroup to a different filegroup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0d2fc-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0d2fc-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0d2fc-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0d2fc-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0d2fc-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0d2fc-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0d2fc-108">**既存のインデックスを別のファイル グループに移動するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-108">**To move an existing index to a different filegroup, using:**</span></span>  
  
     [<span data-ttu-id="0d2fc-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d2fc-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0d2fc-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d2fc-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0d2fc-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="0d2fc-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0d2fc-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0d2fc-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0d2fc-113">テーブルにクラスター化インデックスがある場合、クラスター化インデックスを新しいファイル グループに移動すると、テーブルはそのファイル グループに移動します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-113">If a table has a clustered index, moving the clustered index to a new filegroup moves the table to that filegroup.</span></span>  
  
-   <span data-ttu-id="0d2fc-114">UNIQUE 制約または PRIMARY KEY 制約を使用して作成されたインデックスは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を使用して移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-114">You cannot move indexes created using a UNIQUE or PRIMARY KEY constraint using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="0d2fc-115">これらのインデックスを移動するには、 [で](/sql/t-sql/statements/create-index-transact-sql) CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを (DROP_EXISTING=ON) オプションと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-115">To move these indexes use the [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) statement with the (DROP_EXISTING=ON) option in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0d2fc-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0d2fc-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0d2fc-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="0d2fc-117">Permissions</span></span>  
 <span data-ttu-id="0d2fc-118">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-118">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="0d2fc-119">実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-119">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0d2fc-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="0d2fc-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup-using-table-designer"></a><span data-ttu-id="0d2fc-121">テーブル デザイナーを使用して既存のインデックスを別のファイル グループに移動するには</span><span class="sxs-lookup"><span data-stu-id="0d2fc-121">To move an existing index to a different filegroup using Table Designer</span></span>  
  
1.  <span data-ttu-id="0d2fc-122">オブジェクト エクスプローラーで、移動するインデックスがあるテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-122">In Object Explorer, click the plus sign to expand the database that contains the table containing the index that you want to move.</span></span>  
  
2.  <span data-ttu-id="0d2fc-123">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-123">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="0d2fc-124">移動するインデックスがあるテーブルを右クリックし、 **[デザイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-124">Right-click the table containing the index that you want to move and select **Design**.</span></span>  
  
4.  <span data-ttu-id="0d2fc-125">**[テーブル デザイナー]** メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-125">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="0d2fc-126">移動するインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-126">Select the index that you want to move.</span></span>  
  
6.  <span data-ttu-id="0d2fc-127">メイン グリッドで、 **[データ領域の指定]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-127">In the main grid, expand **Data Space Specification**.</span></span>  
  
7.  <span data-ttu-id="0d2fc-128">**[ファイル グループまたはパーティション構成名]** を選択し、インデックスの移動先のファイル グループまたはパーティション構成を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-128">Select **Filegroup or Partition Scheme Name** and select from the list the filegroup or partition scheme to where you want to move the index.</span></span>  
  
8.  <span data-ttu-id="0d2fc-129">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-129">Click **Close**.</span></span>  
  
9. <span data-ttu-id="0d2fc-130">**ファイル** メニューの **table_name**_を保存_を選びます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-130">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup-in-object-explorer"></a><span data-ttu-id="0d2fc-131">オブジェクト エクスプローラーで既存のインデックスを別のファイル グループに移動するには</span><span class="sxs-lookup"><span data-stu-id="0d2fc-131">To move an existing index to a different filegroup in Object Explorer</span></span>  
  
1.  <span data-ttu-id="0d2fc-132">オブジェクト エクスプローラーで、移動するインデックスがあるテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-132">In Object Explorer, click the plus sign to expand the database that contains the table containing the index that you want to move.</span></span>  
  
2.  <span data-ttu-id="0d2fc-133">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-133">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="0d2fc-134">プラス記号をクリックして、移動するインデックスのあるテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-134">Click the plus sign to expand the table containing the index that you want to move.</span></span>  
  
4.  <span data-ttu-id="0d2fc-135">プラス記号をクリックして **[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-135">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="0d2fc-136">移動するインデックスを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-136">Right-click the index that you want to move and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="0d2fc-137">**[ページの選択]** の **[ストレージ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-137">Under **Select a page**, select **Storage**.</span></span>  
  
7.  <span data-ttu-id="0d2fc-138">インデックスの移動先のファイル グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-138">Select the filegroup in which to move the index.</span></span>  
  
     <span data-ttu-id="0d2fc-139">テーブルまたはインデックスがパーティション分割されている場合は、インデックスの移動先のパーティション構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-139">If the table or index is partitioned, select the partition scheme in which to move the index.</span></span> <span data-ttu-id="0d2fc-140">パーティション インデックスの詳細については、「 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-140">For more information about partitioned indexes, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
     <span data-ttu-id="0d2fc-141">クラスター化インデックスを移動する場合は、オンライン処理を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-141">If you are moving a clustered index, you can use online processing.</span></span> <span data-ttu-id="0d2fc-142">オンライン処理を使用すると、インデックス操作中、基になるデータや非クラスター化インデックスへの同時ユーザー アクセスが可能になります。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-142">Online processing allows concurrent user access to the underlying data and to nonclustered indexes during the index operation.</span></span> <span data-ttu-id="0d2fc-143">詳しくは、「 [Perform Index Operations Online](perform-index-operations-online.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-143">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
     <span data-ttu-id="0d2fc-144">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を使用するマルチプロセッサ コンピューターでは、並列処理の最大許容値を設定することで、インデックス ステートメントの実行に使用するプロセッサの数を構成できます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-144">On multiprocessor computers using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can configure the number of processors used to execute the index statement by specifying a maximum degree of parallelism value.</span></span> <span data-ttu-id="0d2fc-145">並列インデックス操作機能は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-145">The Parallel indexed operations feature is not available in every edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0d2fc-146">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-146">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="0d2fc-147">並列インデックス操作の詳細については、「 [並列インデックス操作の構成](configure-parallel-index-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-147">For more information about Parallel indexed operations, see [Configure Parallel Index Operations](configure-parallel-index-operations.md).</span></span>  
  
8.  <span data-ttu-id="0d2fc-148">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-148">Click **OK**.</span></span>  
  
 <span data-ttu-id="0d2fc-149">**[インデックスのプロパティ -** index_name **]** ダイアログ ボックスの _[ストレージ]_ ページでは、次の情報を利用できます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-149">The following information is available on the **Storage** page of the **Index Properties -** _index_name_ dialog box:</span></span>  
  
 <span data-ttu-id="0d2fc-150">**[ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-150">**Filegroup**</span></span>  
 <span data-ttu-id="0d2fc-151">指定したファイル グループのインデックスを格納します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-151">Stores the index in the specified filegroup.</span></span> <span data-ttu-id="0d2fc-152">一覧には、標準 (ROW) ファイル グループのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-152">The list only displays standard (row) filegroups.</span></span> <span data-ttu-id="0d2fc-153">既定で選択されているのは、データベースのプライマリ ファイル グループです。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-153">The default list selection is the PRIMARY filegroup of the database.</span></span>  
  
 <span data-ttu-id="0d2fc-154">**[Filestream ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-154">**Filestream filegroup**</span></span>  
 <span data-ttu-id="0d2fc-155">FILESTREAM データのファイル グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-155">Specifies the filegroup for FILESTREAM data.</span></span> <span data-ttu-id="0d2fc-156">この一覧には FILESTREAM ファイル グループのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-156">This list displays only FILESTREAM filegroups.</span></span> <span data-ttu-id="0d2fc-157">既定で選択されているのは、PRIMARY FILESTREAM ファイル グループです。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-157">The default list selection is the PRIMARY FILESTREAM filegroup.</span></span>  
  
 <span data-ttu-id="0d2fc-158">**[パーティション構成]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-158">**Partition scheme**</span></span>  
 <span data-ttu-id="0d2fc-159">パーティション構成のインデックスを格納します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-159">Stores the index in a partition scheme.</span></span> <span data-ttu-id="0d2fc-160">**[パーティション構成]** をクリックすると、下のグリッドが有効になります。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-160">Clicking **Partition Scheme** enables the grid below.</span></span> <span data-ttu-id="0d2fc-161">既定で選択されているのは、テーブルのデータを格納するために使用されるパーティション構成です。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-161">The default list selection is the partition scheme that is used for storing the table data.</span></span> <span data-ttu-id="0d2fc-162">一覧にある他のパーティション構成を選択すると、グリッドに表示される情報が更新されます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-162">When you select a different partition scheme in the list, the information in the grid is updated.</span></span>  
  
 <span data-ttu-id="0d2fc-163">この [パーティション構成] オプションは、データベースにパーティション構成がなければ使用できません。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-163">The partition scheme option is unavailable if there are no partition schemes in the database.</span></span>  
  
 <span data-ttu-id="0d2fc-164">**[FileStream パーティション構成]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-164">**Filestream partition scheme**</span></span>  
 <span data-ttu-id="0d2fc-165">FILESTREAM データのパーティション構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-165">Specifies the partition scheme for FILESTREAM data.</span></span> <span data-ttu-id="0d2fc-166">パーティション構成は、 **[パーティション構成]** オプションで指定した構成と対称である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-166">The partition scheme must be symmetric with the scheme that is specified in the **Partition scheme** option.</span></span>  
  
 <span data-ttu-id="0d2fc-167">テーブルがパーティション分割されていない場合、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-167">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="0d2fc-168">**[パーティション構成パラメーター]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-168">**Partition Scheme Parameter**</span></span>  
 <span data-ttu-id="0d2fc-169">パーティション構成に使用される列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-169">Displays the name of the column that participates in the partition scheme.</span></span>  
  
 <span data-ttu-id="0d2fc-170">**[テーブル列]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-170">**Table Column**</span></span>  
 <span data-ttu-id="0d2fc-171">パーティション構成にマップされるテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-171">Select the table or view to map to the partition scheme.</span></span>  
  
 <span data-ttu-id="0d2fc-172">**[列データ型]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-172">**Column Data Type**</span></span>  
 <span data-ttu-id="0d2fc-173">列のデータ型情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-173">Displays data type information about the column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d2fc-174">テーブルの列が計算列の場合、 **[列データ型]** には "計算列" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-174">If the table column is a computed column, **Column Data Type** displays "computed column."</span></span>  
  
 <span data-ttu-id="0d2fc-175">**[インデックスの移動中に DML ステートメントのオンライン処理を許可する]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-175">**Allow online processing of DML statements while moving the index**</span></span>  
 <span data-ttu-id="0d2fc-176">インデックス操作中に、基本となるテーブルやクラスター化インデックス データ、および関連する非クラスター化インデックスにユーザーがアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-176">Allows users to access the underlying table or clustered index data and any associated nonclustered indexes during the index operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d2fc-177">XML インデックスの場合、またはインデックスが無効なクラスター化インデックスの場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-177">This option is not available for XML indexes, or if the index is a disabled clustered index.</span></span>  
  
 <span data-ttu-id="0d2fc-178">**[並列処理の最大限度の設定]**</span><span class="sxs-lookup"><span data-stu-id="0d2fc-178">**Set maximum degree of parallelism**</span></span>  
 <span data-ttu-id="0d2fc-179">並列実行プランの実行中に使用されるプロセッサ数を制限します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-179">Limits the number of processors to use during parallel plan execution.</span></span> <span data-ttu-id="0d2fc-180">既定値は 0 です。0 の場合、実際に使用可能な CPU 数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-180">The default value, 0, uses the actual number of available CPUs.</span></span> <span data-ttu-id="0d2fc-181">値を 1 に設定すると、並列実行プランが生成されなくなります。値を 1 よりも大きな数値に設定すると、1 つのクエリ実行で使用されるプロセッサの最大数が限定されます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-181">Setting the value to 1 suppresses parallel plan generation; setting the value to a number greater than 1 restricts the maximum number of processors used by a single query execution.</span></span> <span data-ttu-id="0d2fc-182">このオプションは、ダイアログ ボックスが **再構築** または **再作成** 状態のときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-182">This option only becomes available if the dialog box is in the **Rebuild** or **Recreate** state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d2fc-183">使用可能な CPU 数よりも多い値を指定すると、実際に使用可能な CPU 数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-183">If a value greater than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0d2fc-184">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="0d2fc-184">Using Transact-SQL</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup"></a><span data-ttu-id="0d2fc-185">既存のインデックスを別のファイル グループに移動するには</span><span class="sxs-lookup"><span data-stu-id="0d2fc-185">To move an existing index to a different filegroup</span></span>  
  
1.  <span data-ttu-id="0d2fc-186">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-186">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d2fc-187">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-187">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0d2fc-188">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-188">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the TransactionsFG1 filegroup on the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP TransactionsFG1;  
    GO  
    /* Adds the TransactionsFG1dat3 file to the TransactionsFG1 filegroup. Please note that you will have to change the filename parameter in this statement to execute it without errors.  
    */  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = TransactionsFG1dat3,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\TransactionsFG1dat3.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP TransactionsFG1;  
    GO  
    /*Creates the IX_Employee_OrganizationLevel_OrganizationNode index  
      on the TransactionsPS1 filegroup and drops the original IX_Employee_OrganizationLevel_OrganizationNode index.  
    */  
    CREATE NONCLUSTERED INDEX IX_Employee_OrganizationLevel_OrganizationNode  
        ON HumanResources.Employee (OrganizationLevel, OrganizationNode)  
        WITH (DROP_EXISTING = ON)  
        ON TransactionsFG1;  
    GO  
    ```  
  
 <span data-ttu-id="0d2fc-189">詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d2fc-189">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
