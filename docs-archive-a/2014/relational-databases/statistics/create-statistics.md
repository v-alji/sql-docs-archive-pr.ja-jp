---
title: 統計の作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.statistics.propertis.f1
- sql12.swb.statistics.filter.f1
- sql12.swb.stat.properties.f1
- sql12.swb.stat.columns.f1
helpviewer_keywords:
- creating statistics
- statistics [SQL Server], creating
ms.assetid: 95a455fb-664d-4c95-851e-c6b62d7ebe04
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 230bd4d840c3d59dc1267dd6801754b68386cb32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644381"
---
# <a name="create-statistics"></a><span data-ttu-id="64ec7-102">統計の作成</span><span class="sxs-lookup"><span data-stu-id="64ec7-102">Create Statistics</span></span>
  <span data-ttu-id="64ec7-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のテーブルまたはインデックス付きビューの 1 つまたは複数の列で、クエリの最適化に関する統計 (フィルター選択された統計情報を含む) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-103">You can create query optimization statistics on one or more columns of a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="64ec7-104">ほとんどのクエリでは、高品質のクエリ プランに必要な統計がクエリ オプティマイザーによって既に生成されていますが、最適な結果を得るために追加の統計情報を作成する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="64ec7-104">For most queries, the query optimizer already generates the necessary statistics for a high-quality query plan; in a few cases, you need to create additional statistics.</span></span>  
  
 <span data-ttu-id="64ec7-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="64ec7-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="64ec7-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="64ec7-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="64ec7-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="64ec7-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="64ec7-108">Security</span><span class="sxs-lookup"><span data-stu-id="64ec7-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="64ec7-109">**統計を作成するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="64ec7-109">**To create statistics, using:**</span></span>  
  
     [<span data-ttu-id="64ec7-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="64ec7-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="64ec7-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="64ec7-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="64ec7-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="64ec7-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="64ec7-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="64ec7-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="64ec7-114">CREATE STATISTICS ステートメントで統計を作成する前に、AUTO_CREATE_STATISTICS オプションがデータベース レベルで設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-114">Before creating statistics with the CREATE STATISTICS statement, verify that the AUTO_CREATE_STATISTICS option is set at the database level.</span></span> <span data-ttu-id="64ec7-115">これにより、クエリ オプティマイザーが常にクエリ述語列について 1 列ずつの統計を作成し続けるようになります。</span><span class="sxs-lookup"><span data-stu-id="64ec7-115">This will ensure that the query optimizer continues to routinely create single-column statistics for query predicate columns.</span></span>  
  
-   <span data-ttu-id="64ec7-116">統計オブジェクトごとに最大 32 列の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-116">You can list up to 32 columns per statistics object.</span></span>  
  
-   <span data-ttu-id="64ec7-117">フィルター選択された統計情報の述語で定義されているテーブル列の定義を削除、名前変更、または変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="64ec7-117">You cannot drop, rename, or alter the definition of a table column that is defined in a filtered statistics predicate.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="64ec7-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="64ec7-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="64ec7-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="64ec7-119">Permissions</span></span>  
 <span data-ttu-id="64ec7-120">ユーザーがテーブルまたはインデックス付きビューの所有者であるか、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、または **db_ddladmin** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="64ec7-120">Requires that the user be the table or indexed view owner, or a member of one of the following roles: **sysadmin** fixed server role, **db_owner** fixed database role, or the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="64ec7-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="64ec7-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-statistics"></a><span data-ttu-id="64ec7-122">統計を作成するには</span><span class="sxs-lookup"><span data-stu-id="64ec7-122">To create statistics</span></span>  
  
1.  <span data-ttu-id="64ec7-123">**オブジェクト エクスプローラー**で、新しい統計を作成するデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-123">In **Object Explorer**, click the plus sign to expand the database in which you want to create a new statistic.</span></span>  
  
2.  <span data-ttu-id="64ec7-124">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-124">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="64ec7-125">プラス記号をクリックして、新しい統計を作成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-125">Click the plus sign to expand the table in which you want to create a new statistic.</span></span>  
  
4.  <span data-ttu-id="64ec7-126">**[統計]** フォルダーを右クリックし、 **[新しい統計]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-126">Right-click the **Statistics** folder and select **New Statistics...**.</span></span>  
  
     <span data-ttu-id="64ec7-127">[テーブル_table_name_の**新しい統計**] ダイアログボックスの [**全般**] ページには、次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-127">The following properties show on the **General** page in the **New Statistics on Table**_table_name_ dialog box.</span></span>  
  
     <span data-ttu-id="64ec7-128">**テーブル名**</span><span class="sxs-lookup"><span data-stu-id="64ec7-128">**Table Name**</span></span>  
     <span data-ttu-id="64ec7-129">統計の対象となるテーブルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-129">Displays the name of the table described by the statistics.</span></span>  
  
     <span data-ttu-id="64ec7-130">**[統計名]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-130">**Statistics Name**</span></span>  
     <span data-ttu-id="64ec7-131">統計情報が格納されるデータベース オブジェクトの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-131">Displays the name of the database object where the statistics are stored.</span></span>  
  
     <span data-ttu-id="64ec7-132">**[統計の列]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-132">**Statistics Columns**</span></span>  
     <span data-ttu-id="64ec7-133">このグリッドに、この統計の対象となる列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-133">This grid shows the columns described by this set of statistics.</span></span> <span data-ttu-id="64ec7-134">グリッド内のすべての値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="64ec7-134">All values in the grid are read-only.</span></span>  
  
     <span data-ttu-id="64ec7-135">**名前**</span><span class="sxs-lookup"><span data-stu-id="64ec7-135">**Name**</span></span>  
     <span data-ttu-id="64ec7-136">統計の対象となる列の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-136">Displays the name of the column described by the statistics.</span></span> <span data-ttu-id="64ec7-137">表示されるのは、1 つのテーブルの 1 つの列、または列の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="64ec7-137">This can be a single column or a combination of columns in a single table.</span></span>  
  
     <span data-ttu-id="64ec7-138">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-138">**Data Type**</span></span>  
     <span data-ttu-id="64ec7-139">統計の対象となる列のデータ型を表します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-139">Indicates the data type of the columns described by the statistics.</span></span>  
  
     <span data-ttu-id="64ec7-140">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-140">**Size**</span></span>  
     <span data-ttu-id="64ec7-141">各列のデータ型のサイズが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-141">Displays the size of the data type for each column.</span></span>  
  
     <span data-ttu-id="64ec7-142">**ID**</span><span class="sxs-lookup"><span data-stu-id="64ec7-142">**Identity**</span></span>  
     <span data-ttu-id="64ec7-143">オンの場合、ID 列を示します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-143">Indicates an identity column when it is checked.</span></span>  
  
     <span data-ttu-id="64ec7-144">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-144">**Allow Nulls**</span></span>  
     <span data-ttu-id="64ec7-145">列で NULL 値が許容されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-145">Indicates whether the column accepts NULL values.</span></span>  
  
     <span data-ttu-id="64ec7-146">**追加**</span><span class="sxs-lookup"><span data-stu-id="64ec7-146">**Add**</span></span>  
     <span data-ttu-id="64ec7-147">テーブルの列を統計グリッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-147">Add additional columns from the table to the statistics grid.</span></span>  
  
     <span data-ttu-id="64ec7-148">**Remove**</span><span class="sxs-lookup"><span data-stu-id="64ec7-148">**Remove**</span></span>  
     <span data-ttu-id="64ec7-149">選択されている列を統計グリッドから削除します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-149">Remove the selected column from the statistics grid.</span></span>  
  
     <span data-ttu-id="64ec7-150">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-150">**Move Up**</span></span>  
     <span data-ttu-id="64ec7-151">統計グリッド内で選択されている列を上に移動します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-151">Move the selected column to an earlier location in the statistics grid.</span></span> <span data-ttu-id="64ec7-152">グリッド内の列の位置は、統計の実用性に大きく影響します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-152">The location in the grid can substantially impact the usefulness of the statistics.</span></span>  
  
     <span data-ttu-id="64ec7-153">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-153">**Move Down**</span></span>  
     <span data-ttu-id="64ec7-154">統計グリッド内で選択されている列を下に移動します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-154">Move the selected column to a later location in the statistics grid.</span></span>  
  
     <span data-ttu-id="64ec7-155">**[これらの列に対する統計の最終更新日時]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-155">**Statistics for these columns were last updated:**</span></span>  
     <span data-ttu-id="64ec7-156">統計がどれだけ古いかを示します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-156">Indicates how old the statistics are.</span></span> <span data-ttu-id="64ec7-157">統計は、新しいほど価値があります。</span><span class="sxs-lookup"><span data-stu-id="64ec7-157">Statistics are more valuable when they are current.</span></span> <span data-ttu-id="64ec7-158">データに大きな変更が加えられた後や、通常とは異なるデータを追加した後は、統計を更新してください。</span><span class="sxs-lookup"><span data-stu-id="64ec7-158">Update statistics after large changes to the data or after adding atypical data.</span></span> <span data-ttu-id="64ec7-159">データの変更が平均しているテーブルの場合は、統計を頻繁に更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="64ec7-159">Statistics for tables that have a consistent distribution of data need to be updated less frequently.</span></span>  
  
     <span data-ttu-id="64ec7-160">**[この列の統計を更新する]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-160">**Update statistics for these columns**</span></span>  
     <span data-ttu-id="64ec7-161">オンにすると、ダイアログ ボックスを閉じたときに統計を更新します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-161">Check to update the statistics when the dialog box is closed.</span></span>  
  
     <span data-ttu-id="64ec7-162">[テーブル_table_name_の**新しい統計**] ダイアログボックスの [**フィルター** ] ページで、次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-162">The following property shows on the **Filter** page in the **New Statistics on Table**_table_name_ dialog box.</span></span>  
  
     <span data-ttu-id="64ec7-163">**[フィルター式]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-163">**Filter Expression**</span></span>  
     <span data-ttu-id="64ec7-164">フィルター処理された統計情報にどのデータ行を含めるかを定義します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-164">Defines which data rows to include in the filtered statistics.</span></span> <span data-ttu-id="64ec7-165">たとえば、`Production.ProductSubcategoryID IN ( 1,2,3 )` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-165">For example, `Production.ProductSubcategoryID IN ( 1,2,3 )`</span></span>  
  
5.  <span data-ttu-id="64ec7-166">[テーブル_table_name_の**新しい統計**] ダイアログボックスの [**全般**] ページで、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64ec7-166">In the **New Statistics on Table**_table_name_ dialog box, on the **General** page, click **Add**.</span></span>  
  
     <span data-ttu-id="64ec7-167">**[列の選択]** ダイアログ ボックスに次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-167">The following properties show in the **Select Columns** dialog box.</span></span> <span data-ttu-id="64ec7-168">この情報は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="64ec7-168">This information is read-only.</span></span>  
  
     <span data-ttu-id="64ec7-169">**名前**</span><span class="sxs-lookup"><span data-stu-id="64ec7-169">**Name**</span></span>  
     <span data-ttu-id="64ec7-170">統計の対象となる列の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-170">Displays the name of the column described by the statistics.</span></span> <span data-ttu-id="64ec7-171">表示されるのは、1 つのテーブルの 1 つの列、または列の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="64ec7-171">This can be a single column or a combination of columns in a single table.</span></span>  
  
     <span data-ttu-id="64ec7-172">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-172">**Data Type**</span></span>  
     <span data-ttu-id="64ec7-173">統計の対象となる列のデータ型を表します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-173">Indicates the data type of the columns described by the statistics.</span></span>  
  
     <span data-ttu-id="64ec7-174">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-174">**Size**</span></span>  
     <span data-ttu-id="64ec7-175">各列のデータ型のサイズが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ec7-175">Displays the size of the data type for each column.</span></span>  
  
     <span data-ttu-id="64ec7-176">**ID**</span><span class="sxs-lookup"><span data-stu-id="64ec7-176">**Identity**</span></span>  
     <span data-ttu-id="64ec7-177">オンの場合、ID 列を示します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-177">Indicates an identity column when checked.</span></span>  
  
     <span data-ttu-id="64ec7-178">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="64ec7-178">**Allow NULLs**</span></span>  
     <span data-ttu-id="64ec7-179">列で NULL 値が許容されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-179">Indicates whether the column accepts NULL values.</span></span>  
  
6.  <span data-ttu-id="64ec7-180">**[列の選択]** ダイアログ ボックスで、統計を作成する列のチェック ボックスをオンにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64ec7-180">In the **Select Columns** dialog box, select the check box or check boxes of each column for which you want to create a statistic and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="64ec7-181">[テーブル_table_name_の**新しい統計**] ダイアログボックスで、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64ec7-181">In the **New Statistics on Table**_table_name_ dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="64ec7-182">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="64ec7-182">Using Transact-SQL</span></span>  
  
#### <a name="to-create-statistics"></a><span data-ttu-id="64ec7-183">統計を作成するには</span><span class="sxs-lookup"><span data-stu-id="64ec7-183">To create statistics</span></span>  
  
1.  <span data-ttu-id="64ec7-184">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-184">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="64ec7-185">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64ec7-185">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="64ec7-186">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64ec7-186">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Create new statistic object called ContactMail1  
    -- on the BusinessEntityID and EmailPromotion columns in the Person.Person table.   
  
    CREATE STATISTICS ContactMail1  
        ON Person.Person (BusinessEntityID, EmailPromotion);   
    GO  
    ```  
  
4.  <span data-ttu-id="64ec7-187">上記で作成された統計により、次のクエリの結果が潜在的に向上します。</span><span class="sxs-lookup"><span data-stu-id="64ec7-187">The statistic created above potentially improves the results for the following query.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT LastName, FirstName  
    FROM Person.Person  
    WHERE EmailPromotion = 2  
    ORDER BY LastName, FirstName;   
    GO  
    ```  
  
 <span data-ttu-id="64ec7-188">詳細については、「[CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64ec7-188">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
  
