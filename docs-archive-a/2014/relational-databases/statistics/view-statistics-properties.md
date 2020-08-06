---
title: 統計のプロパティの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.statistics.details.f1
helpviewer_keywords:
- viewing statistics properties
- statistics [SQL Server], viewing properties
ms.assetid: 0eaa2101-006e-4015-9979-3468b50e0aaa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63cabc5d8844982604993acac6a791317ee36925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644367"
---
# <a name="view-statistics-properties"></a><span data-ttu-id="e8064-102">統計のプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="e8064-102">View Statistics Properties</span></span>
  <span data-ttu-id="e8064-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のテーブルまたはインデックス付きビューについての、現在のクエリの最適化に関する統計を表示します。</span><span class="sxs-lookup"><span data-stu-id="e8064-103">You can display current query optimization statistics for a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e8064-104">統計オブジェクトには、統計に関するメタデータが含まれるヘッダー、統計オブジェクトの最初のキー列の値の分布が含まれるヒストグラム、および列間の相関関係を測定する密度ベクトルが格納されています。</span><span class="sxs-lookup"><span data-stu-id="e8064-104">Statistics objects include a header with metadata about the statistics, a histogram with the distribution of values in the first key column of the statistics object, and a density vector to measure cross-column correlation.</span></span> <span data-ttu-id="e8064-105">ヒストグラムと密度ベクトルの詳細については、「[DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8064-105">For more information about histograms and density vectors, see [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)</span></span>  
  
 <span data-ttu-id="e8064-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e8064-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e8064-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e8064-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e8064-108">Security</span><span class="sxs-lookup"><span data-stu-id="e8064-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e8064-109">**統計のプロパティを表示するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="e8064-109">**To view statistics properties, using:**</span></span>  
  
     [<span data-ttu-id="e8064-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e8064-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e8064-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e8064-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e8064-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="e8064-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e8064-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e8064-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e8064-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="e8064-114">Permissions</span></span>  
 <span data-ttu-id="e8064-115">統計オブジェクトを表示するには、テーブルを所有しているか、固定サーバー ロール `sysadmin`、固定データベース ロール `db_owner`、または固定データベース ロール `db_ddladmin` のメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8064-115">In order to view the statistics object, the user must own the table or the user must be a member of the `sysadmin` fixed server role, the `db_owner` fixed database role, or the `db_ddladmin` fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e8064-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e8064-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-statistics-properties"></a><span data-ttu-id="e8064-117">統計のプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="e8064-117">To view statistics properties</span></span>  
  
1.  <span data-ttu-id="e8064-118">**オブジェクト エクスプローラー**で、新しい統計を作成するデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="e8064-118">In **Object Explorer**, click the plus sign to expand the database in which you want to create a new statistic.</span></span>  
  
2.  <span data-ttu-id="e8064-119">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e8064-119">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="e8064-120">統計のプロパティを表示するテーブルのプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="e8064-120">Click the plus sign to expand the table in which you want to view the statistic's properties.</span></span>  
  
4.  <span data-ttu-id="e8064-121">プラス記号をクリックして **[統計]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e8064-121">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="e8064-122">プロパティを表示する統計オブジェクトを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8064-122">Right-click the Statistics object of which you want to view the properties and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="e8064-123">**[統計のプロパティ - _statistics_name_]** ダイアログ ボックスの **[ページの選択]** ウィンドウで **[詳細]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8064-123">In the **Statistics Properties -** _statistics_name_ dialog box, in the **Select a page** pane, select **Details**.</span></span>  
  
     <span data-ttu-id="e8064-124">**[統計のプロパティ - _statistics_name_]** ダイアログ ボックスの **[詳細]** ページで次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-124">The following properties show on the **Details** page in the **Statistics Properties -** _statistics_name_ dialog box.</span></span>  
  
     <span data-ttu-id="e8064-125">**テーブル名**</span><span class="sxs-lookup"><span data-stu-id="e8064-125">**Table Name**</span></span>  
     <span data-ttu-id="e8064-126">統計の対象となるテーブルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-126">Displays the name of the table described by the statistics.</span></span>  
  
     <span data-ttu-id="e8064-127">**[統計名]**</span><span class="sxs-lookup"><span data-stu-id="e8064-127">**Statistics Name**</span></span>  
     <span data-ttu-id="e8064-128">統計情報が格納されるデータベース オブジェクトの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-128">Displays the name of the database object where the statistics are stored.</span></span>  
  
     <span data-ttu-id="e8064-129">**[INDEX の統計 statistics_name]**</span><span class="sxs-lookup"><span data-stu-id="e8064-129">**Statistics for INDEXstatistics_name**</span></span>  
     <span data-ttu-id="e8064-130">このテキスト ボックスは、統計オブジェクトから返されるプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="e8064-130">This text box shows the properties returned from the statistics object.</span></span> <span data-ttu-id="e8064-131">このプロパティは、次の 3 つのセクションに分かれています:統計ヘッダー、密度ベクトル、ヒストグラム。</span><span class="sxs-lookup"><span data-stu-id="e8064-131">This properties are divided into three sections: Stats Header, Density Vector, and Histogram.</span></span>  
  
     <span data-ttu-id="e8064-132">以下に、統計ヘッダーを指定した場合に結果セットに返される列を示します。</span><span class="sxs-lookup"><span data-stu-id="e8064-132">The following information describes the columns returned in the result set for the Stats Header.</span></span>  
  
     <span data-ttu-id="e8064-133">**名前**</span><span class="sxs-lookup"><span data-stu-id="e8064-133">**Name**</span></span>  
     <span data-ttu-id="e8064-134">統計オブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="e8064-134">Name of the statistics object.</span></span>  
  
     <span data-ttu-id="e8064-135">**更新**</span><span class="sxs-lookup"><span data-stu-id="e8064-135">**Updated**</span></span>  
     <span data-ttu-id="e8064-136">統計情報が最後に更新された日付と時刻。</span><span class="sxs-lookup"><span data-stu-id="e8064-136">Date and time the statistics were last updated.</span></span>  
  
     <span data-ttu-id="e8064-137">**行数**</span><span class="sxs-lookup"><span data-stu-id="e8064-137">**Rows**</span></span>  
     <span data-ttu-id="e8064-138">統計情報が最後に更新された時点のテーブルまたはインデックス付きビューの行の総数。</span><span class="sxs-lookup"><span data-stu-id="e8064-138">Total number of rows in the table or indexed view when the statistics were last updated.</span></span> <span data-ttu-id="e8064-139">統計がフィルター選択されている場合、またはフィルター選択されたインデックスに対応している場合は、行数がテーブルの行数よりも少なくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="e8064-139">If the statistics are filtered or correspond to a filtered index, the number of rows might be less than the number of rows in the table.</span></span>  
  
     <span data-ttu-id="e8064-140">**[サンプリングされた行数]**</span><span class="sxs-lookup"><span data-stu-id="e8064-140">**Rows Sampled**</span></span>  
     <span data-ttu-id="e8064-141">統計の計算時にサンプリングされた行の合計数。</span><span class="sxs-lookup"><span data-stu-id="e8064-141">Total number of rows sampled for statistics calculations.</span></span> <span data-ttu-id="e8064-142">Rows Sampled < Rows の場合、表示されるヒストグラムおよび密度の結果は、サンプリングされた行に基づいて推定されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-142">If Rows Sampled < Rows, the displayed histogram and density results are estimates based on the sampled rows.</span></span>  
  
     <span data-ttu-id="e8064-143">**手順**</span><span class="sxs-lookup"><span data-stu-id="e8064-143">**Steps**</span></span>  
     <span data-ttu-id="e8064-144">ヒストグラムの区間の数。</span><span class="sxs-lookup"><span data-stu-id="e8064-144">Number of steps in the histogram.</span></span> <span data-ttu-id="e8064-145">各区間の範囲には、上限の列値までの列値の範囲が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e8064-145">Each step spans a range of column values followed by an upper bound column value.</span></span> <span data-ttu-id="e8064-146">ヒストグラムの区間は、統計の最初のキー列に基づいて定義されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-146">The histogram steps are defined on the first key column in the statistics.</span></span> <span data-ttu-id="e8064-147">区間の最大数は 200 です。</span><span class="sxs-lookup"><span data-stu-id="e8064-147">The maximum number of steps is 200.</span></span>  
  
     <span data-ttu-id="e8064-148">**[密度]**</span><span class="sxs-lookup"><span data-stu-id="e8064-148">**Density**</span></span>  
     <span data-ttu-id="e8064-149">ヒストグラムの境界値を除く、統計オブジェクトの最初のキー列のすべての値について、"1 / *distinct values* " として計算されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-149">Calculated as 1 / *distinct values* for all values in the first key column of the statistics object, excluding the histogram boundary values.</span></span> <span data-ttu-id="e8064-150">この密度の値はクエリ オプティマイザーでは使用されません。SQL Server 2008 より前のバージョンとの互換性を維持するために表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-150">This Density value is not used by the query optimizer and is displayed for backward compatibility with versions before SQL Server 2008.</span></span>  
  
     <span data-ttu-id="e8064-151">**[キーの平均の長さ]**</span><span class="sxs-lookup"><span data-stu-id="e8064-151">**Average Key Length**</span></span>  
     <span data-ttu-id="e8064-152">統計オブジェクトのすべてのキー列の、値ごとの平均バイト数。</span><span class="sxs-lookup"><span data-stu-id="e8064-152">Average number of bytes per value for all of the key columns in the statistics object.</span></span>  
  
     <span data-ttu-id="e8064-153">**String Index**</span><span class="sxs-lookup"><span data-stu-id="e8064-153">**String Index**</span></span>  
     <span data-ttu-id="e8064-154">Yes の場合は、統計オブジェクトに文字列の統計概要が含まれています。これにより、LIKE 演算子を使用するクエリ述語 (`WHERE ProductName LIKE '%Bike'` など) に対するカーディナリティの推定が向上します。</span><span class="sxs-lookup"><span data-stu-id="e8064-154">Yes indicates the statistics object contains string summary statistics to improve the cardinality estimates for query predicates that use the LIKE operator; for example, `WHERE ProductName LIKE '%Bike'`.</span></span> <span data-ttu-id="e8064-155">文字列の統計概要は、ヒストグラムとは別に格納されます。この統計は、統計オブジェクトの最初のキー列について、その型が **char**、 **varchar**、 **nchar**、 **nvarchar**、 **varchar(max)** 、 **nvarchar(max)** 、 **text**、 **ntext**である場合に作成されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-155">String summary statistics are stored separately from the histogram and are created on the first key column of the statistics object when it is of type **char**, **varchar**, **nchar**, **nvarchar**, **varchar(max)**, **nvarchar(max)**, **text**, or **ntext**.</span></span>  
  
     <span data-ttu-id="e8064-156">**[フィルター式]**</span><span class="sxs-lookup"><span data-stu-id="e8064-156">**Filter Expression**</span></span>  
     <span data-ttu-id="e8064-157">統計オブジェクトに含まれるテーブル行のサブセットの述語。</span><span class="sxs-lookup"><span data-stu-id="e8064-157">Predicate for the subset of table rows included in the statistics object.</span></span> <span data-ttu-id="e8064-158">NULL = フィルター選択されていない統計情報です。</span><span class="sxs-lookup"><span data-stu-id="e8064-158">NULL = non-filtered statistics.</span></span>  
  
     <span data-ttu-id="e8064-159">**[フィルター処理なしの行数]**</span><span class="sxs-lookup"><span data-stu-id="e8064-159">**Unfiltered Rows**</span></span>  
     <span data-ttu-id="e8064-160">フィルター式を適用する前のテーブル内の行の合計数。</span><span class="sxs-lookup"><span data-stu-id="e8064-160">Total number of rows in the table before applying the filter expression.</span></span> <span data-ttu-id="e8064-161">[フィルター式] が NULL の場合、[フィルター処理なしの行数] は [行数] と同じになります。</span><span class="sxs-lookup"><span data-stu-id="e8064-161">If Filter Expression is NULL, Unfiltered Rows is equal to Rows.</span></span>  
  
     <span data-ttu-id="e8064-162">以下に、密度ベクトルを指定した場合に結果セットに返される列を示します。</span><span class="sxs-lookup"><span data-stu-id="e8064-162">The following information describes the columns returned in the result set for the Density Vector.</span></span>  
  
     <span data-ttu-id="e8064-163">**[すべての密度]**</span><span class="sxs-lookup"><span data-stu-id="e8064-163">**All Density**</span></span>  
     <span data-ttu-id="e8064-164">密度は "1 / *distinct values*" です。</span><span class="sxs-lookup"><span data-stu-id="e8064-164">Density is 1 / *distinct values*.</span></span> <span data-ttu-id="e8064-165">結果には、統計オブジェクトの列の各プレフィックスに対する密度が、密度ごとに 1 行表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-165">Results display density for each prefix of columns in the statistics object, one row per density.</span></span> <span data-ttu-id="e8064-166">個別の値は、行および列プレフィックスごとの列値の個別のリストです。</span><span class="sxs-lookup"><span data-stu-id="e8064-166">A distinct value is a distinct list of the column values per row and per columns prefix.</span></span> <span data-ttu-id="e8064-167">たとえば、統計オブジェクトにキー列 (A, B, C) が含まれる場合、結果では列プレフィックス (A)、(A, B)、(A, B, C) ごとに個別の値リストの密度が報告されます。</span><span class="sxs-lookup"><span data-stu-id="e8064-167">For example, if the statistics object contains key columns (A, B, C), the results report the density of the distinct lists of values in each of these column prefixes: (A), (A,B), and (A, B, C).</span></span> <span data-ttu-id="e8064-168">プレフィックス (A、B、C) を使用すると、これらの各リストは次の個別の値リストになります。(3, 5, 6)、(4, 4, 6)、(4, 5, 6)、(4, 5, 7)。</span><span class="sxs-lookup"><span data-stu-id="e8064-168">Using the prefix (A, B, C), each of these lists is a distinct value list: (3, 5, 6), (4, 4, 6), (4, 5, 6), (4, 5, 7).</span></span> <span data-ttu-id="e8064-169">プレフィックス (A、B) を使用すると、同じ列値に次の個別の値リストが含まれます。(3, 5)、(4, 4)、(4, 5)。</span><span class="sxs-lookup"><span data-stu-id="e8064-169">Using the prefix (A, B) the same column values have these distinct value lists: (3, 5), (4, 4), and (4, 5).</span></span>  
  
     <span data-ttu-id="e8064-170">**[平均の長さ]**</span><span class="sxs-lookup"><span data-stu-id="e8064-170">**Average Length**</span></span>  
     <span data-ttu-id="e8064-171">列プレフィックスの列値のリストを格納する平均の長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="e8064-171">Average length, in bytes, to store a list of the column values for the column prefix.</span></span> <span data-ttu-id="e8064-172">たとえば、リスト (3, 5, 6) の値ごとに 4 バイト必要な場合は、長さは 12 バイトになります。</span><span class="sxs-lookup"><span data-stu-id="e8064-172">For example, if the values in the list (3, 5, 6) each require 4 bytes the length is 12 bytes.</span></span>  
  
     <span data-ttu-id="e8064-173">**[列]**</span><span class="sxs-lookup"><span data-stu-id="e8064-173">**Columns**</span></span>  
     <span data-ttu-id="e8064-174">[すべての密度] および [平均の長さ] を表示するプレフィックスの列の名前。</span><span class="sxs-lookup"><span data-stu-id="e8064-174">Names of columns in the prefix for which All density and Average length are displayed.</span></span>  
  
     <span data-ttu-id="e8064-175">以下に、ヒストグラムを指定した場合に結果セットに返される列を示します。</span><span class="sxs-lookup"><span data-stu-id="e8064-175">The following information describes the columns returned in the result set for the Histogram.</span></span>  
  
     <span data-ttu-id="e8064-176">**[RANGE_HI_KEY]**</span><span class="sxs-lookup"><span data-stu-id="e8064-176">**RANGE_HI_KEY**</span></span>  
     <span data-ttu-id="e8064-177">ヒストグラム区間の上限の列値。</span><span class="sxs-lookup"><span data-stu-id="e8064-177">Upper bound column value for a histogram step.</span></span> <span data-ttu-id="e8064-178">この列値はキー値とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e8064-178">The column value is also called a key value.</span></span>  
  
     <span data-ttu-id="e8064-179">**RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="e8064-179">**RANGE_ROWS**</span></span>  
     <span data-ttu-id="e8064-180">ヒストグラム区間内 (上限は除く) に列値がある行の予測数。</span><span class="sxs-lookup"><span data-stu-id="e8064-180">Estimated number of rows whose column value falls within a histogram step, excluding the upper bound.</span></span>  
  
     <span data-ttu-id="e8064-181">**EQ_ROWS**</span><span class="sxs-lookup"><span data-stu-id="e8064-181">**EQ_ROWS**</span></span>  
     <span data-ttu-id="e8064-182">ヒストグラム区間の上限と列値が等しい行の予測数。</span><span class="sxs-lookup"><span data-stu-id="e8064-182">Estimated number of rows whose column value equals the upper bound of the histogram step.</span></span>  
  
     <span data-ttu-id="e8064-183">**DISTINCT_RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="e8064-183">**DISTINCT_RANGE_ROWS**</span></span>  
     <span data-ttu-id="e8064-184">ヒストグラム区間内 (上限は除く) にある個別の列値を持つ行の予測数。</span><span class="sxs-lookup"><span data-stu-id="e8064-184">Estimated number of rows with a distinct column value within a histogram step, excluding the upper bound.</span></span>  
  
     <span data-ttu-id="e8064-185">**AVG_RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="e8064-185">**AVG_RANGE_ROWS**</span></span>  
     <span data-ttu-id="e8064-186">ヒストグラム区間内 (上限は除く) にある重複する列値を持つ行の平均数 (DISTINCT_RANGE_ROWS > 0 の場合 RANGE_ROWS / DISTINCT_RANGE_ROWS)</span><span class="sxs-lookup"><span data-stu-id="e8064-186">Average number of rows with duplicate column values within a histogram step, excluding the upper bound (RANGE_ROWS / DISTINCT_RANGE_ROWS for DISTINCT_RANGE_ROWS > 0).</span></span>  
  
7.  <span data-ttu-id="e8064-187">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e8064-187">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e8064-188">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e8064-188">Using Transact-SQL</span></span>  
  
#### <a name="to-view-statistics-properties"></a><span data-ttu-id="e8064-189">統計のプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="e8064-189">To view statistics properties</span></span>  
  
1.  <span data-ttu-id="e8064-190">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e8064-190">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e8064-191">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e8064-191">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e8064-192">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e8064-192">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example displays all statistics information for the AK_Address_rowguid index of the Person.Address table.   
    DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);   
    GO  
    ```  
  
 <span data-ttu-id="e8064-193">詳細については、「[DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8064-193">For more information, see [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql).</span></span>  
  
#### <a name="to-find-all-of-the-statistics-on-a-table-or-view"></a><span data-ttu-id="e8064-194">テーブルまたはビューのすべての統計を見つけるには</span><span class="sxs-lookup"><span data-stu-id="e8064-194">To find all of the statistics on a table or view</span></span>  
  
1.  <span data-ttu-id="e8064-195">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e8064-195">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e8064-196">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e8064-196">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e8064-197">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e8064-197">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Gets the following information: name and ID of the statistics, whether the statistics were created automatically or by the user, whether the statistics were created with the NORECOMPUTE option, and whether the statistics have a filter and, if so, what that filter is.  
    */  
    SELECT name AS statistics_name  
        ,stats_id  
        ,auto_created  
        ,user_created  
        ,no_recompute  
        ,has_filter  
        ,filter_definition  
    -- using the sys.stats catalog view  
    FROM sys.stats  
    -- for the Sales.SpecialOffer table  
    WHERE object_id = OBJECT_ID('Sales.SpecialOffer');  
    GO  
    ```  
  
 <span data-ttu-id="e8064-198">詳細については、「[sys.stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-stats-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8064-198">For more information, see [sys.stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-stats-transact-sql).</span></span>  
  
  
