---
title: インデックスの FILL FACTOR の指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- fill factor [SQL Server]
- page splits [SQL Server]
ms.assetid: 237a577e-b42b-4adb-90cf-aa7fb174f3ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ac54f2b22de55ed74c4635ec0f86d008c7624a42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739918"
---
# <a name="specify-fill-factor-for-an-index"></a><span data-ttu-id="4db57-102">インデックスの FILL FACTOR の指定</span><span class="sxs-lookup"><span data-stu-id="4db57-102">Specify Fill Factor for an Index</span></span>
  <span data-ttu-id="4db57-103">このトピックでは、FILL FACTOR について説明すると共に、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]のインデックスの FILL FACTOR 値を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4db57-103">This topic describes what fill factor is and how to specify a fill factor value on an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4db57-104">FILL FACTOR オプションは、インデックス データ ストレージとパフォーマンスの微調整を行うために用意されています。</span><span class="sxs-lookup"><span data-stu-id="4db57-104">The fill-factor option is provided for fine-tuning index data storage and performance.</span></span> <span data-ttu-id="4db57-105">インデックスの作成または再構築を行うとき、各リーフ レベルのページのデータを格納する領域の割合が FILL FACTOR 値によって決まり、今後インデックスのサイズが大きくなる場合に備えて指定した各ページ上の残りの空き領域が予約されます。</span><span class="sxs-lookup"><span data-stu-id="4db57-105">When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the remainder on each page as free space for future growth.</span></span> <span data-ttu-id="4db57-106">たとえば、FILL FACTOR 値を 80 に指定すると、基になるテーブルにデータを追加したときにインデックスのサイズを拡張するための領域として、各リーフ レベルのページの 20% が空き領域として確保されます。</span><span class="sxs-lookup"><span data-stu-id="4db57-106">For example, specifying a fill-factor value of 80 means that 20 percent of each leaf-level page will be left empty, providing space for index expansion as data is added to the underlying table.</span></span> <span data-ttu-id="4db57-107">空き領域は、インデックスの最後ではなく、インデックス行の間に確保されます。</span><span class="sxs-lookup"><span data-stu-id="4db57-107">The empty space is reserved between the index rows rather than at the end of the index.</span></span>  
  
 <span data-ttu-id="4db57-108">有効な FILL FACTOR 値は 1 ～ 100 (パーセント) です。サーバー全体の既定値は 0 で、これはリーフ レベルのページの全容量が使用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="4db57-108">The fill-factor value is a percentage from 1 to 100, and the server-wide default is 0 which means that the leaf-level pages are filled to capacity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4db57-109">FILL FACTOR 値 0 と 100 の機能は、まったく同じです。</span><span class="sxs-lookup"><span data-stu-id="4db57-109">Fill-factor values 0 and 100 are the same in all respects.</span></span>  
  
 <span data-ttu-id="4db57-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4db57-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4db57-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4db57-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4db57-112">パフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="4db57-112">Performance Considerations</span></span>](#Performance)  
  
     [<span data-ttu-id="4db57-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4db57-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4db57-114">**以下を使用してインデックスの FILL FACTOR を指定するには:**</span><span class="sxs-lookup"><span data-stu-id="4db57-114">**To specify a fill factor in an index, using:**</span></span>  
  
     [<span data-ttu-id="4db57-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4db57-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4db57-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4db57-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4db57-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="4db57-117">Before You Begin</span></span>  
  
###  <a name="performance-considerations"></a><a name="Performance"></a> <span data-ttu-id="4db57-118">パフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="4db57-118">Performance Considerations</span></span>  
  
#### <a name="page-splits"></a><span data-ttu-id="4db57-119">ページ分割</span><span class="sxs-lookup"><span data-stu-id="4db57-119">Page Splits</span></span>  
 <span data-ttu-id="4db57-120">適切な FILL FACTOR 値を選択すると、基になるテーブルにデータが追加されたときにインデックスのサイズを拡張するのに十分な領域が確保され、ページ分割が実行される可能性が低くなります。フル インデックス ページに新しい行を追加すると、新しい行を挿入する領域を確保するために、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] により行の約半分が新しいページに移動されます。</span><span class="sxs-lookup"><span data-stu-id="4db57-120">A correctly chosen fill-factor value can reduce potential page splits by providing enough space for index expansion as data is added to the underlying table.When a new row is added to a full index page, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] moves approximately half the rows to a new page to make room for the new row.</span></span> <span data-ttu-id="4db57-121">この再構成をページ分割といいます。</span><span class="sxs-lookup"><span data-stu-id="4db57-121">This reorganization is known as a page split.</span></span> <span data-ttu-id="4db57-122">ページ分割により新しいレコード用の領域が確保されますが、この操作の実行には時間がかかることがあります。また、ページ分割はリソースを集中的に消費する操作です。</span><span class="sxs-lookup"><span data-stu-id="4db57-122">A page split makes room for new records, but can take time to perform and is a resource intensive operation.</span></span> <span data-ttu-id="4db57-123">さらに、I/O 操作を増加させる断片化の原因となることもあります。</span><span class="sxs-lookup"><span data-stu-id="4db57-123">Also, it can cause fragmentation that causes increased I/O operations.</span></span> <span data-ttu-id="4db57-124">ページ分割が頻繁に行われる場合は、新規または既存の FILL FACTOR 値を使用してデータを再配布して、インデックスを再構築できます。</span><span class="sxs-lookup"><span data-stu-id="4db57-124">When frequent page splits occur, the index can be rebuilt by using a new or existing fill-factor value to redistribute the data.</span></span> <span data-ttu-id="4db57-125">詳細については、「 [インデックスの再編成と再構築](reorganize-and-rebuild-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4db57-125">For more information, see [Reorganize and Rebuild Indexes](reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="4db57-126">FILL FACTOR 値を 0 以外の小さな値に設定すると、インデックスのサイズが大きくなったときにページを分割する必要性を減少させることができますが、さらに多くの保存領域が必要になり、読み取りのパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="4db57-126">Although a low, nonzero fill-factor value may reduce the requirement to split pages as the index grows, the index will require more storage space and can decrease read performance.</span></span> <span data-ttu-id="4db57-127">挿入や更新が頻繁に実行されるアプリケーションでも、データベース読み取り回数はデータベース書き込み回数よりも 5 ～ 10 倍多くなるのが普通です。</span><span class="sxs-lookup"><span data-stu-id="4db57-127">Even for an application oriented for many insert and update operations, the number of database reads typically outnumber database writes by a factor of 5 to 10.</span></span> <span data-ttu-id="4db57-128">したがって、既定値以外の FILL FACTOR 値を指定すると、FILL FACTOR の設定に反比例してデータベース読み取りのパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4db57-128">Therefore, specifying a fill factor other than the default can decrease database read performance by an amount inversely proportional to the fill-factor setting.</span></span> <span data-ttu-id="4db57-129">たとえば、FILL FACTOR 値を 50 に指定すると、データベース読み取りのパフォーマンスが 1/2 に低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="4db57-129">For example, a fill-factor value of 50 can cause database read performance to decrease by two times.</span></span> <span data-ttu-id="4db57-130">インデックスに多くのページが含まれていて、データを取得するには、ディスク I/O 操作を増加させる必要があるため、読み取りのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="4db57-130">Read performance is decreased because the index contains more pages, therefore increasing the disk IO operations required to retrieve the data.</span></span>  
  
#### <a name="adding-data-to-the-end-of-the-table"></a><span data-ttu-id="4db57-131">テーブルの最後へのデータの追加</span><span class="sxs-lookup"><span data-stu-id="4db57-131">Adding Data to the End of the Table</span></span>  
 <span data-ttu-id="4db57-132">新しいデータがテーブル全体に均等に分散される場合は、0 および 100 以外の FILL FACTOR を指定するとパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4db57-132">A nonzero fill factor other than 0 or 100 can be good for performance if the new data is evenly distributed throughout the table.</span></span> <span data-ttu-id="4db57-133">ただし、すべてのデータがテーブルの最後に追加されると、インデックス ページ内の空き領域は埋められません。</span><span class="sxs-lookup"><span data-stu-id="4db57-133">However, if all the data is added to the end of the table, the empty space in the index pages will not be filled.</span></span> <span data-ttu-id="4db57-134">たとえば、インデックス キー列が IDENTITY 列であると、新しい行のキーが常に増加し、インデックス行はインデックスの最後に論理的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="4db57-134">For example, if the index key column is an IDENTITY column, the key for new rows is always increasing and the index rows are logically added to the end of the index.</span></span> <span data-ttu-id="4db57-135">行のサイズを大きくするデータで既存の行が更新される場合は、FILL FACTOR 値を 100 未満にしてください。</span><span class="sxs-lookup"><span data-stu-id="4db57-135">If existing rows will be updated with data that lengthens the size of the rows, use a fill factor of less than 100.</span></span> <span data-ttu-id="4db57-136">各ページ上の追加のバイトにより、行の追加の長さによって発生するページ分割を最小限にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4db57-136">The extra bytes on each page will help to minimize page splits caused by extra length in the rows.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4db57-137">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4db57-137">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4db57-138">Permissions</span><span class="sxs-lookup"><span data-stu-id="4db57-138">Permissions</span></span>  
 <span data-ttu-id="4db57-139">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4db57-139">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="4db57-140">実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="4db57-140">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4db57-141">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4db57-141">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-fill-factor-by-using-table-designer"></a><span data-ttu-id="4db57-142">テーブル デザイナーを使用して FILL FACTOR を指定するには</span><span class="sxs-lookup"><span data-stu-id="4db57-142">To specify a fill factor by using Table Designer</span></span>  
  
1.  <span data-ttu-id="4db57-143">オブジェクト エクスプローラーで、インデックスの FILL FACTOR を指定するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4db57-143">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to specify an index's fill factor.</span></span>  
  
2.  <span data-ttu-id="4db57-144">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4db57-144">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="4db57-145">インデックスの FILL FACTOR を指定するテーブルを右クリックし、 **[デザイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4db57-145">Right-click the table on which you want to specify an index's fill factor and select **Design**.</span></span>  
  
4.  <span data-ttu-id="4db57-146">**[テーブル デザイナー]** メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db57-146">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="4db57-147">FILL FACTOR を指定するインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="4db57-147">Select the index with the fill factor that you want to specify.</span></span>  
  
6.  <span data-ttu-id="4db57-148">**[FILL の指定]** を展開し、 **[FILL FACTOR]** 行を選択し、目的の FILL FACTOR を行に入力します。</span><span class="sxs-lookup"><span data-stu-id="4db57-148">Expand **Fill Specification**, select the **Fill Factor** row and enter the fill factor you want in the row.</span></span>  
  
7.  <span data-ttu-id="4db57-149">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db57-149">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="4db57-150">**ファイル** メニューの **table_name**_を保存_を選びます。</span><span class="sxs-lookup"><span data-stu-id="4db57-150">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-specify-a-fill-factor-in-an-index-by-using-object-explorer"></a><span data-ttu-id="4db57-151">オブジェクト エクスプローラーを使用してインデックスの FILL FACTOR を指定するには</span><span class="sxs-lookup"><span data-stu-id="4db57-151">To specify a fill factor in an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="4db57-152">オブジェクト エクスプローラーで、インデックスの FILL FACTOR を指定するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4db57-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to specify an index's fill factor.</span></span>  
  
2.  <span data-ttu-id="4db57-153">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4db57-153">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="4db57-154">プラス記号をクリックして、インデックスの FILL FACTOR を指定するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="4db57-154">Click the plus sign to expand the table on which you want to specify an index's fill factor.</span></span>  
  
4.  <span data-ttu-id="4db57-155">プラス記号をクリックして **[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4db57-155">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="4db57-156">FILL FACTOR を指定するインデックスを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4db57-156">Right-click the index with the fill factor that you want to specify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="4db57-157">**[ページの選択]** の **[オプション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4db57-157">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="4db57-158">**[FILL FACTOR]** 行に、目的の FILL FACTOR を入力します。</span><span class="sxs-lookup"><span data-stu-id="4db57-158">In the **Fill factor** row, enter the fill factor that you want.</span></span>  
  
8.  <span data-ttu-id="4db57-159">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db57-159">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4db57-160">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4db57-160">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-fill-factor-in-an-existing-index"></a><span data-ttu-id="4db57-161">既存のインデックスの FILL FACTOR を指定するには</span><span class="sxs-lookup"><span data-stu-id="4db57-161">To specify a fill factor in an existing index</span></span>  
  
1.  <span data-ttu-id="4db57-162">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="4db57-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4db57-163">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db57-163">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4db57-164">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db57-164">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4db57-165">この例では、既存のインデックスを再構築し、再構築処理中に指定された FILL FACTOR を適用します。</span><span class="sxs-lookup"><span data-stu-id="4db57-165">The example rebuilds an existing index and applies the specified fill factor during the rebuild operation.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Rebuilds the IX_Employee_OrganizationLevel_OrganizationNode index   
    -- with a fill factor of 80 on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD WITH (FILLFACTOR = 80);   
    GO  
    ```  
  
#### <a name="another-way-to-specify-a-fill-factor-in-an-index"></a><span data-ttu-id="4db57-166">別の方法でインデックスの FILL FACTOR を指定する</span><span class="sxs-lookup"><span data-stu-id="4db57-166">Another way to specify a fill factor in an index</span></span>  
  
1.  <span data-ttu-id="4db57-167">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="4db57-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4db57-168">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db57-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4db57-169">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db57-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    /* Drops and re-creates the IX_Employee_OrganizationLevel_OrganizationNode index on the HumanResources.Employee table with a fill factor of 80.  
    */  
  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)   
    WITH (DROP_EXISTING = ON, FILLFACTOR = 80);   
    GO  
    ```  
  
 <span data-ttu-id="4db57-170">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4db57-170">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
