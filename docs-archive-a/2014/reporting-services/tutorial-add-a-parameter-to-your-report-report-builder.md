---
title: チュートリアル:レポートへのパラメーターの追加 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eab34ec4-b3ad-4a76-95cc-07b2f75ee6d7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dff41066a2d505ab53b17a10fb3da9b6cb17130f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720966"
---
# <a name="tutorial-add-a-parameter-to-your-report-report-builder"></a><span data-ttu-id="b0cb3-102">チュートリアル:レポートへのパラメーターの追加 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="b0cb3-102">Tutorial: Add a Parameter to Your Report (Report Builder)</span></span>
  <span data-ttu-id="b0cb3-103">レポートにパラメーターを追加して、ユーザーがデータソースまたはレポート内のレポートデータをフィルター処理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-103">Add a parameter to your report to let users filter report data from the data source or in the report.</span></span> <span data-ttu-id="b0cb3-104">レポート パラメーターは、データセット クエリに追加したクエリ パラメーターごとに自動で作成されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-104">Report parameters are created automatically for each query parameter that you include in a dataset query.</span></span> <span data-ttu-id="b0cb3-105">パラメーターのデータ型により、パラメーターがレポート ビューアー ツール バーに表示される方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-105">The parameter data type determines how it appears on the report view toolbar.</span></span>  
  
 <span data-ttu-id="b0cb3-106">![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")</span><span class="sxs-lookup"><span data-stu-id="b0cb3-106">![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="b0cb3-107">学習内容</span><span class="sxs-lookup"><span data-stu-id="b0cb3-107">What You Will Learn</span></span>  
 <span data-ttu-id="b0cb3-108">このチュートリアルでは、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-108">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="b0cb3-109">テーブルまたはマトリックス ウィザードを使用してマトリックス レポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-109">Create a Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#Setup)  
  
2.  [<span data-ttu-id="b0cb3-110">テーブルまたはマトリックス ウィザードでデータを整理し、レイアウトとスタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-110">Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>](#CompleteWizard)  
  
3.  [<span data-ttu-id="b0cb3-111">クエリ パラメーターを追加してレポート パラメーターを作成する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-111">Add a Query Parameter to Create a Report Parameter</span></span>](#Query)  
  
4.  [<span data-ttu-id="b0cb3-112">レポート パラメーターの既定のデータ型とその他のプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-112">Change Default Data Type and Other Properties for a Report Parameter</span></span>](#ChangeDefaultProperties)  
  
    1.  [<span data-ttu-id="b0cb3-113">使用可能な値と表示名を提供するデータセットを追加する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-113">Add a Dataset to Provide Available Values and Display Names</span></span>](#AddDataset)  
  
    2.  [<span data-ttu-id="b0cb3-114">使用可能な値を指定して値のドロップダウン リストを作成する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-114">Specify Available Values to Create a Drop-List of Values</span></span>](#AvailableValues)  
  
    3.  [<span data-ttu-id="b0cb3-115">既定値を指定してレポートが自動的に実行されるようにする</span><span class="sxs-lookup"><span data-stu-id="b0cb3-115">Specify Default Values so the Report Runs Automatically</span></span>](#DefaultValues)  
  
    4.  [<span data-ttu-id="b0cb3-116">名前と値のペアを持つデータセットから値を参照する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-116">Look up a Value from a Dataset that has Name/Value Pairs</span></span>](#NameValue)  
  
5.  [<span data-ttu-id="b0cb3-117">選択されたパラメーターの値をレポートに表示する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-117">Display the Selected Parameter Value in the Report</span></span>](#Expression)  
  
6.  [<span data-ttu-id="b0cb3-118">フィルターにレポート パラメーターを使用する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-118">Use the Report Parameter in a Filter</span></span>](#Filter)  
  
7.  [<span data-ttu-id="b0cb3-119">レポート パラメーターを複数値をとるように変更する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-119">Change the Report Parameter to Accept Multiple Values</span></span>](#Multivalued)  
  
8.  [<span data-ttu-id="b0cb3-120">条件付き表示のためにブール型パラメーターを追加する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-120">Add a Boolean Parameter for Conditional Visibility</span></span>](#Boolean)  
  
9. [<span data-ttu-id="b0cb3-121">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-121">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="b0cb3-122">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-122">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="b0cb3-123">このチュートリアルでは、ウィザードに関する複数の手順を 1 つにまとめて示します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-123">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="b0cb3-124">レポート サーバーの参照、データ ソースの選択、データセットの作成に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 &#40;レポート ビルダー&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-124">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="b0cb3-125">このチュートリアルの推定所要時間 : 25 分</span><span class="sxs-lookup"><span data-stu-id="b0cb3-125">Estimated time to complete this tutorial: 25 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0cb3-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="b0cb3-126">Requirements</span></span>  
 <span data-ttu-id="b0cb3-127">要件の詳細については、[「チュートリアルの前提条件 (レポート ビルダー)」](../reporting-services/report-builder-tutorials.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-127">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a><span data-ttu-id="b0cb3-128">1. テーブルまたはマトリックスウィザードでマトリックスレポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-128">1. Create a Matrix Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="b0cb3-129">マトリックス レポート、データ ソース、およびデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-129">Create a matrix report, a data source, and a dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0cb3-130">このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-130">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="b0cb3-131">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-131">This makes the query quite long.</span></span> <span data-ttu-id="b0cb3-132">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-132">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="b0cb3-133">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-133">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-matrix-report"></a><span data-ttu-id="b0cb3-134">新しいマトリックス レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-134">To create a new matrix report</span></span>  
  
1.  <span data-ttu-id="b0cb3-135">[**スタート**] をクリックし、[**プログラム**]、[レポートビルダー] の順にポイントし、[ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder\*\*\*\*レポートビルダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-135">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="b0cb3-136">[**はじめに**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-136">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b0cb3-137">[**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-137">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="b0cb3-138">左側のウィンドウで、[**レポート**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-138">In the left pane, verify that **Report** is selected.</span></span>  
  
3.  <span data-ttu-id="b0cb3-139">右ペインで、 **[テーブルまたはマトリックス ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-139">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="b0cb3-140">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-140">Click **Create**.</span></span>  
  
5.  <span data-ttu-id="b0cb3-141">**[データセットの選択]** ページで、 **[データセットを作成する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-141">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
6.  <span data-ttu-id="b0cb3-142">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-142">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="b0cb3-143">**[データ ソースへの接続の選択]** ページで、種類が **[SQL Server]** のデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-143">On the **Choose a connection to a data source** page, select a data source that is type **SQL Server**.</span></span> <span data-ttu-id="b0cb3-144">一覧からデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-144">Select a data source from the list or browse to the report server to select one.</span></span>  
  
8.  <span data-ttu-id="b0cb3-145">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-145">Click **Next**.</span></span>  
  
9. <span data-ttu-id="b0cb3-146">**[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-146">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
10. <span data-ttu-id="b0cb3-147">次のクエリをクエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-147">Paste the following query into the query pane:</span></span>  
  
    ```  
    ;WITH CTE (StoreID, Subcategory, Quantity)   
    AS (  
    SELECT 200 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 2002 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Camcorders' AS Subcategory, 1954 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Accessories' AS Subcategory, 1895 AS Quantity  
    UNION SELECT  199 AS StoreID, 'Digital Cameras' AS Subcategory, 1849 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1579 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Camcorders' AS Subcategory, 1561 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital Cameras' AS Subcategory, 1553 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Accessories' AS Subcategory, 1534 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Accessories' AS Subcategory, 1755 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Camcorders' AS Subcategory, 1631 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1772 AS Quantity)  
    SELECT StoreID, Subcategory, Quantity  
    FROM CTE  
    ```  
  
     <span data-ttu-id="b0cb3-148">Contoso サンプル データベースから抜粋した単純化されたデータを使って値を指定する関係上、このクエリでは、複数の [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT ステートメントの結果が共通テーブル式の中で結合されています。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-148">This query combines the results of several [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT statements inside a common table expression to specify values that are based on simplified data from the Contoso sample database.</span></span> <span data-ttu-id="b0cb3-149">Contoso 売上データは、消費者向け商品の各国の売上データを表します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-149">The Contoso sales data represents international sales data for consumer goods.</span></span> <span data-ttu-id="b0cb3-150">このチュートリアルでは、カメラの売上データを使用します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-150">This tutorial uses sales data for cameras.</span></span> <span data-ttu-id="b0cb3-151">サブカテゴリは、デジタル カメラ、デジタル一眼レフ (SLR) カメラ、ビデオ カメラ、およびアクセサリを表します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-151">The subcategories represent digital cameras, digital single lens reflex (SLR) cameras, camcorders, and accessories.</span></span>  
  
     <span data-ttu-id="b0cb3-152">クエリには、3 つの店舗の販売注文に関して、店舗 ID (StoreID)、商品のサブカテゴリ (Subcategory)、および注文数 (Quantity) を格納している列の名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-152">The query specifies column names that include a store identifier, a sales item subcategory, and the quantity ordered for sales orders from three stores.</span></span> <span data-ttu-id="b0cb3-153">このクエリでは、店舗名は結果セットに含まれません。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-153">In this query, the store name is not part of the result set.</span></span> <span data-ttu-id="b0cb3-154">このチュートリアルで後ほど、店舗 ID に対応する店舗の名前を別のデータセットから参照します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-154">Later in this tutorial, you will look up the name of the store that corresponds to the store identifier from a separate dataset.</span></span>  
  
     <span data-ttu-id="b0cb3-155">クエリ パラメーターは存在しません。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-155">This query does not contain query parameters.</span></span> <span data-ttu-id="b0cb3-156">以降、このチュートリアルの中でクエリ パラメーターを追加していきます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-156">You will add query parameters later in this tutorial.</span></span>  
  
11. <span data-ttu-id="b0cb3-157">クエリデザイナーのツールバーで、[**実行**] (**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-157">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="b0cb3-158">結果セットは StoreID 列、Subcategory 列、Quantity 列で構成され、4 店舗のサブカテゴリごとの販売済み商品数量を示す 11 行のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-158">The result set displays 11 rows of data that show the quantity of items sold for each subcategory for four stores, and includes the following columns: StoreID, Subcategory, Quantity.</span></span>  
  
12. <span data-ttu-id="b0cb3-159">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-159">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-choose-layout-and-style-from-the-table-or-matrix-wizard"></a><a name="CompleteWizard"></a><span data-ttu-id="b0cb3-160">2. テーブルまたはマトリックスウィザードでデータを整理し、レイアウトとスタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-160">2. Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="b0cb3-161">ウィザードを使用して、データを表示する最初のデザインを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-161">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="b0cb3-162">ウィザードのプレビュー ペインでは、テーブルやマトリックスのデザインを完了する前にデータのグループ化の結果を表示できます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-162">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the table or matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="b0cb3-163">データをグループにまとめるには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-163">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="b0cb3-164">**[フィールドの配置]** ページで、Subcategory を **[行グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-164">On the **Arrange fields** page, drag Subcategory to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="b0cb3-165">StoreID を **[列グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-165">Drag StoreID to **Column groups**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-166">Quantity を **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-166">Drag Quantity to **Values**.</span></span>  
  
     <span data-ttu-id="b0cb3-167">販売数量の値をサブカテゴリごとにグループ化された行に整理しました。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-167">You have organized the quantity sold values in rows grouped by subcategory.</span></span> <span data-ttu-id="b0cb3-168">店舗ごとに 1 列のデータが存在します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-168">There will be one column for each store.</span></span>  
  
4.  <span data-ttu-id="b0cb3-169">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-169">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="b0cb3-170">[**レイアウトの選択**] ページの [**オプション**] で、[**小計と総計を表示**する] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-170">On the **Choose a Layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="b0cb3-171">レポートを実行すると、最後の列にはすべての店舗のサブカテゴリごとの合計数量が表示され、最後の行には店舗ごとのすべてのサブカテゴリの合計数量が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-171">When you run the report, the last column will show the total quantity of each subcategory for all stores, and the last row will show the total quantity for all subcategories for each store.</span></span>  
  
6.  <span data-ttu-id="b0cb3-172">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-172">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="b0cb3-173">[**スタイルの選択**] ページのスタイルペインで、スタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-173">On the **Choose a Style** page, in the Styles pane, select a style.</span></span>  
  
8.  <span data-ttu-id="b0cb3-174">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-174">Click **Finish**.</span></span>  
  
     <span data-ttu-id="b0cb3-175">マトリックスがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-175">The matrix is added to the design surface.</span></span> <span data-ttu-id="b0cb3-176">マトリックスは 3 行× 3 列で表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-176">The matrix displays three columns and three rows.</span></span> <span data-ttu-id="b0cb3-177">先頭行のセルの内容は、Subcategory、[StoreID]、および Total です。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-177">The contents of the cells in the first row are Subcategory, [StoreID], and Total.</span></span> <span data-ttu-id="b0cb3-178">2 番目の行のセルの内容は、サブカテゴリ、店舗ごとの販売品目の数量、および、すべての店舗のサブカテゴリごとの合計数量を表す式です。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-178">The contents of the cells in the second row contain expressions that represent the subcategory, the quantity of items sold for each store, and the total quantity for each subcategory for all stores.</span></span> <span data-ttu-id="b0cb3-179">最後の行のセルには、店舗ごとの総計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-179">The cells in the final row display the grand total for each store.</span></span>  
  
9. <span data-ttu-id="b0cb3-180">マトリックス内をクリックし、最初の列の端にカーソルを合わせてハンドルをドラッグして、列の幅を拡張します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-180">Click in the matrix, hover over the edge of the first column, grab the handle, and expand the column width.</span></span>  
  
10. <span data-ttu-id="b0cb3-181">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-181">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b0cb3-182">レポート サーバーでレポートが実行され、タイトルとレポートの処理時刻がレポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-182">The report runs on the report server and displays the title and the time the report processing occurred.</span></span>  
  
 <span data-ttu-id="b0cb3-183">このシナリオでは、列見出しに店舗 ID は表示されますが店舗名は表示されません。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-183">In this scenario, the column headings display the store identifier but not the store name.</span></span> <span data-ttu-id="b0cb3-184">後ほど、店舗 ID と店舗名のペアが格納されているデータセットで店舗名を参照する式を追加します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-184">Later, you will add an expression to look up the store name in a dataset that contains store identifier/store name pairs.</span></span>  
  
##  <a name="3-add-a-query-parameter-to-create-a-report-parameter"></a><a name="Query"></a><span data-ttu-id="b0cb3-185">3. クエリパラメーターを追加してレポートパラメーターを作成する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-185">3. Add a Query Parameter to Create a Report Parameter</span></span>  
 <span data-ttu-id="b0cb3-186">クエリ パラメーターをクエリに対して追加すると、名前、プロンプト、およびデータ型に既定のプロパティを持つ単一値のレポート パラメーターがレポート ビルダーによって自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-186">When you add a query parameter to a query, Report Builder automatically creates a single-valued report parameter with default properties for name, prompt, and data type.</span></span>  
  
#### <a name="to-add-a-query-parameter"></a><span data-ttu-id="b0cb3-187">クエリ パラメーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-187">To add a query parameter</span></span>  
  
1.  <span data-ttu-id="b0cb3-188">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-188">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="b0cb3-189">レポート データ ペインで、 **[データセット]** フォルダーを展開して **DataSet1**を右クリックし、 **[クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-189">In the Report Data pane, expand the **Datasets** folder, right-click **DataSet1**, and then click **Query**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-190">次の [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` 句をクエリの最後の行として追加します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-190">Add the following [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause as the last line in the query:</span></span>  
  
    ```  
    WHERE StoreID = (@StoreID)  
    ```  
  
     <span data-ttu-id="b0cb3-191">句は、取得したデータを、 `WHERE` クエリパラメーターで指定されたストア id に限定し *@StoreID* ます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-191">The `WHERE` clause limits the retrieved data to the store identifier that is specified by the query parameter *@StoreID*.</span></span>  
  
4.  <span data-ttu-id="b0cb3-192">クエリデザイナーのツールバーで、[**実行**] (**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-192">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="b0cb3-193">この **[クエリ パラメーターの定義]** ダイアログ ボックスが開き、クエリ パラメーター *@StoreID*」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-193">The **Define Query Parameters** dialog box opens and prompts for a value for the query parameter *@StoreID*.</span></span>  
  
5.  <span data-ttu-id="b0cb3-194">**[パラメーター値]** に「 **200**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-194">In **Parameter Value**, type **200**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="b0cb3-195">結果セットには、店舗 ID **200**について、Accessories、Camcorders、および Digital SLR Cameras の販売数量が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-195">The result set displays the quantities sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="b0cb3-196">レポート データ ペインで **[パラメーター]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-196">In the Report Data pane, expand the **Parameters** folder.</span></span>  
  
 <span data-ttu-id="b0cb3-197">という名前のレポートパラメーターが存在することに注意 *@StoreID* してください。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-197">Notice that there is now a report parameter named *@StoreID*.</span></span> <span data-ttu-id="b0cb3-198">既定では、パラメーターのデータ型は**Text**です。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-198">By default, the parameter has data type **Text**.</span></span> <span data-ttu-id="b0cb3-199">店舗 ID は整数なので、次の手順でデータ型を [整数] に変更します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-199">Because the store identifier is an integer, you will change the data type to Integer in the next procedure.</span></span>  
  
##  <a name="4-change-default-data-type-and-other-properties-for-a-report-parameter"></a><a name="ChangeDefaultProperties"></a><span data-ttu-id="b0cb3-200">4. レポートパラメーターの既定のデータ型およびその他のプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-200">4. Change Default Data Type and Other Properties for a Report Parameter</span></span>  
 <span data-ttu-id="b0cb3-201">プロパティの既定値は、レポート パラメーターの作成後に調整することができます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-201">After a report parameter is created, you can adjust the default values for properties.</span></span>  
  
#### <a name="to-change-the-default-data-type-for-a-report-parameter"></a><span data-ttu-id="b0cb3-202">レポート パラメーターの既定のデータ型を変更するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-202">To change the default data type for a report parameter</span></span>  
  
1.  <span data-ttu-id="b0cb3-203">レポートデータペインの [**パラメーター** ] ノードで、を右クリック *@StoreID* し、[**パラメーターのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-203">In the Report Data pane under the **Parameters** node, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="b0cb3-204">[プロンプト] に「 **Store identifier?** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-204">In Prompt, type **Store identifier?**</span></span> <span data-ttu-id="b0cb3-205">レポートを実行すると、レポート ビューアーのツール バーにこのテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-205">This text appears on the report viewer toolbar when you run the report.</span></span>  
  
3.  <span data-ttu-id="b0cb3-206">**[データ型]** のドロップダウン リストから **[整数]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-206">In **Data type**, from the drop-down list, select **Integer**.</span></span>  
  
4.  <span data-ttu-id="b0cb3-207">このダイアログ ボックスのそれ以外の設定は、既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-207">Accept the remaining default values in the dialog box.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="b0cb3-208">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-208">Preview the report.</span></span> <span data-ttu-id="b0cb3-209">レポートビューアーに、のプロンプトが表示され *@StoreID* ます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-209">The report viewer displays the prompt for *@StoreID*.</span></span>  
  
7.  <span data-ttu-id="b0cb3-210">レポート ビューアー ツール バーで、店舗 ID の横に「 **200**」と入力し、 **[レポートの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-210">On the report viewer toolbar, next to Store ID, type **200**, and then click **View Report**.</span></span>  
  
##  <a name="4a-add-a-dataset-to-provide-available-values-and-display-names"></a><a name="AddDataset"></a><span data-ttu-id="b0cb3-211">4a.</span><span class="sxs-lookup"><span data-stu-id="b0cb3-211">4a.</span></span> <span data-ttu-id="b0cb3-212">使用可能な値と表示名を提供するデータセットを追加する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-212">Add a Dataset to Provide Available Values and Display Names</span></span>  
 <span data-ttu-id="b0cb3-213">ユーザーがパラメーターの有効な値しか入力できないようにするには、選択可能な値のドロップダウン リストを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-213">To ensure a user can type only valid values for a parameter, you can create a drop-down list of values to choose from.</span></span> <span data-ttu-id="b0cb3-214">値は、データセットまたは指定した一覧から取得できます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-214">The values can come from a dataset or from a list that you specify.</span></span> <span data-ttu-id="b0cb3-215">使用可能な値は、パラメーターへの参照を含まないクエリが格納されているデータセットから指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-215">Available values must be supplied from a dataset that has a query that does not contain a reference to the parameter.</span></span>  
  
#### <a name="to-create-a-dataset-for-valid-values-for-a-parameter"></a><span data-ttu-id="b0cb3-216">パラメーターの有効な値のデータセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-216">To create a dataset for valid values for a parameter</span></span>  
  
1.  <span data-ttu-id="b0cb3-217">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-217">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="b0cb3-218">レポート データ ペインで、 **[データセット]** フォルダーを右クリックし、 **[データセットの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-218">In the Report Data pane, right-click the **Datasets** folder, and then click **Add Dataset**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-219">**[名前]** に、「 **Stores**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-219">In **Name**, type **Stores**.</span></span>  
  
4.  <span data-ttu-id="b0cb3-220">[**レポートに埋め込まれたデータセットを使用する**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-220">Select the **Use a dataset embedded in my report** option.</span></span>  
  
5.  <span data-ttu-id="b0cb3-221">[**データソース**] のドロップダウンリストから、最初の手順で作成したデータソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-221">In **Data source**, from the drop-down list, choose the data source you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="b0cb3-222">**[クエリの種類]** で **[テキスト]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-222">In **Query type**, verify that **Text** is selected.</span></span>  
  
7.  <span data-ttu-id="b0cb3-223">**[クエリ]** に、次のテキストを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-223">In **Query**, paste the following text:</span></span>  
  
    ```  
    SELECT 200 AS StoreID, 'Contoso Catalog Store' as StoreName  
    UNION SELECT 199 AS StoreID, 'Contoso North America Online Store' as StoreName  
    UNION SELECT 307 AS StoreID, 'Contoso Asia Online Store' as StoreName  
    UNION SELECT 306 AS StoreID, 'Contoso Europe Online Store' as StoreName  
    ```  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="b0cb3-224">レポート データ ペインの **Stores** データセット ノードに、StoreID フィールドと StoreName フィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-224">The Report Data pane displays the fields StoreID and StoreName under the **Stores** dataset node.</span></span>  
  
##  <a name="4b-specify-available-values-to-create-a-drop-down-list-of-values"></a><a name="AvailableValues"></a><span data-ttu-id="b0cb3-225">4b.</span><span class="sxs-lookup"><span data-stu-id="b0cb3-225">4b.</span></span> <span data-ttu-id="b0cb3-226">使用可能な値を指定して、値のドロップダウンリストを作成します</span><span class="sxs-lookup"><span data-stu-id="b0cb3-226">Specify Available Values to Create a Drop-down List of Values</span></span>  
 <span data-ttu-id="b0cb3-227">使用できる値のソースとなるデータセットを作成したら、レポートのプロパティで、レポート ビューアー ツール バーの有効な値のドロップダウン リストに値を設定するために使用するデータセットとフィールドを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-227">After you create a dataset to provide available values, you must change the report properties to specify which dataset and which field to use to populate the drop-down list of valid values on the reportviewer toolbar.</span></span>  
  
#### <a name="to-provide-available-values-for-a-parameter-from-a-dataset"></a><span data-ttu-id="b0cb3-228">パラメーターに使用できる値をデータセットから提供するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-228">To provide available values for a parameter from a dataset</span></span>  
  
1.  <span data-ttu-id="b0cb3-229">レポートデータペインでパラメーターを右クリック *@StoreID* し、[**パラメーターのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-229">In the Report Data pane, right-click the parameter *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="b0cb3-230">**[使用できる値]** をクリックし、 **[クエリから値を取得]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-230">Click **Available Values**, and then click **Get values from a query**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-231">**[データセット]** ドロップダウン リストで **[Stores]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-231">In **Dataset**, from the drop-down list, click **Stores**.</span></span>  
  
4.  <span data-ttu-id="b0cb3-232">**[値フィールド]** ドロップダウン リストで [StoreID] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-232">In **Value field**, from the drop-down list, click StoreID.</span></span>  
  
5.  <span data-ttu-id="b0cb3-233">**[ラベル フィールド]** ドロップダウン リストで [StoreName] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-233">In **Label field**, from the drop-down list, click StoreName.</span></span> <span data-ttu-id="b0cb3-234">ラベル フィールドによって値の表示名が指定されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-234">The label field specifies the display name for the value.</span></span>  
  
6.  <span data-ttu-id="b0cb3-235">**[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-235">Click **General**.</span></span>  
  
7.  <span data-ttu-id="b0cb3-236">[プロンプト] に「 **Store name?** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-236">In Prompt, type **Store name?**</span></span>  
  
     <span data-ttu-id="b0cb3-237">これで、店舗 ID ではなく、店舗名の一覧からの選択ができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-237">The user will now select from a list of store names instead of store identifiers.</span></span> <span data-ttu-id="b0cb3-238">ただし、パラメーターは店舗名ではなく店舗 ID に基づいているので、パラメーターのデータ型は **[整数]** のままです。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-238">Note that the parameter data type remains **Integer** because the parameter is based on the store identifier, not the store name.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="b0cb3-239">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-239">Preview the report.</span></span>  
  
     <span data-ttu-id="b0cb3-240">レポートビューアーツールバーのパラメーターテキストボックスが、表示されるドロップダウンリストになりました **\<Select a Value>** 。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-240">In the report viewer toolbar, the parameter text box is now a drop-down list that displays **\<Select a Value>**.</span></span>  
  
10. <span data-ttu-id="b0cb3-241">ドロップダウンリストから [Contoso Catalog Store] を選択し、[**レポートの表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-241">From the drop-down list, select Contoso Catalog Store, and then click **View Report**.</span></span>  
  
 <span data-ttu-id="b0cb3-242">レポートには、店舗 ID **200**について、Accessories、Camcorders、および Digital SLR Cameras の販売数量が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-242">The report displays the quantity sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
##  <a name="4c-specify-default-values-so-the-report-runs-automatically"></a><a name="DefaultValues"></a><span data-ttu-id="b0cb3-243">4c.</span><span class="sxs-lookup"><span data-stu-id="b0cb3-243">4c.</span></span> <span data-ttu-id="b0cb3-244">既定値を指定してレポートが自動的に実行されるようにする</span><span class="sxs-lookup"><span data-stu-id="b0cb3-244">Specify Default Values so the Report Runs Automatically</span></span>  
 <span data-ttu-id="b0cb3-245">各パラメーターの既定値を指定して、レポートが自動的に実行されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-245">You can specify a default value for each parameter so the report runs automatically.</span></span>  
  
#### <a name="to-specify-a-default-value-from-a-dataset"></a><span data-ttu-id="b0cb3-246">データセットから既定値を指定するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-246">To specify a default value from a dataset</span></span>  
  
1.  <span data-ttu-id="b0cb3-247">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-247">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="b0cb3-248">レポートデータペインでを右クリックし、[ *@StoreID* **パラメーターのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-248">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-249">[**既定値**] をクリックし、[**クエリから値を取得**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-249">Click **Default Values**, and then click **Get values from a query**.</span></span>  
  
4.  <span data-ttu-id="b0cb3-250">**[データセット]** ドロップダウン リストで **[Stores]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-250">In **Dataset**, from the drop-down list, click **Stores**.</span></span>  
  
5.  <span data-ttu-id="b0cb3-251">**[値フィールド]** ドロップダウン リストで [StoreID] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-251">In **Value field**, from the drop-down list, click StoreID.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="b0cb3-252">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-252">Preview the report.</span></span>  
  
 <span data-ttu-id="b0cb3-253">*@StoreID*では、レポートビューアーに "Contoso 北米 Online Store" という値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-253">For *@StoreID*, the report viewer displays the value "Contoso North America Online Store".</span></span> <span data-ttu-id="b0cb3-254">これは、データセット**ストア**の結果セットの最初の値です。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-254">This is the first value from the result set for the dataset **Stores**.</span></span> <span data-ttu-id="b0cb3-255">レポートには、店舗 ID **199**について、Digital Cameras の販売数量が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-255">The report displays the quantity sold for Digital Cameras for store identifier **199**.</span></span>  
  
#### <a name="to-specify-a-custom-default-value"></a><span data-ttu-id="b0cb3-256">カスタムの既定値を指定するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-256">To specify a custom default value</span></span>  
  
1.  <span data-ttu-id="b0cb3-257">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-257">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="b0cb3-258">レポートデータペインでを右クリックし、[ *@StoreID* **パラメーターのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-258">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-259">[**既定値**] をクリックし、[**値の指定**] をクリックして、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-259">Click **Default Values**, and click **Specify values**, and then click **Add**.</span></span> <span data-ttu-id="b0cb3-260">新しい値の行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-260">A new value row is added.</span></span>  
  
4.  <span data-ttu-id="b0cb3-261">**[値]** に「 **200**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-261">In **Value**, type **200**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="b0cb3-262">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-262">Preview the report.</span></span>  
  
 <span data-ttu-id="b0cb3-263">*@StoreID*では、レポートビューアーに "Contoso Catalog Store" という値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-263">For *@StoreID*, the report viewer displays the value "Contoso Catalog Store".</span></span> <span data-ttu-id="b0cb3-264">これは、ストア id **200**の表示名です。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-264">This is the display name for store identifier **200**.</span></span> <span data-ttu-id="b0cb3-265">レポートには、店舗 ID **200**について、Accessories、Camcorders、および Digital SLR Cameras の販売数量が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-265">The report displays the quantity sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
##  <a name="4d-look-up-a-value-from-a-dataset-that-has-namevalue-pairs"></a><a name="NameValue"></a><span data-ttu-id="b0cb3-266">4d.</span><span class="sxs-lookup"><span data-stu-id="b0cb3-266">4d.</span></span> <span data-ttu-id="b0cb3-267">名前と値のペアを持つデータセットから値を参照する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-267">Look up a Value from a Dataset that has Name/Value Pairs</span></span>  
 <span data-ttu-id="b0cb3-268">データセットには、ID と対応する名前フィールドの両方が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-268">A dataset might contain both the identifier and the corresponding name field.</span></span> <span data-ttu-id="b0cb3-269">ID しかない場合は、名前と値のペアが格納されている作成済みのデータセットで対応する名前を参照できます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-269">When you only have an identifier, you can look up the corresponding name in a dataset that you created that includes name/value pairs.</span></span>  
  
#### <a name="to-look-up-a-value-from-a-dataset"></a><span data-ttu-id="b0cb3-270">データセットから値を参照するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-270">To look up a value from a dataset</span></span>  
  
1.  <span data-ttu-id="b0cb3-271">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-271">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="b0cb3-272">デザイン画面のマトリックスの先頭行の列見出しで、 `[StoreID]` を右クリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-272">On the design surface, in the matrix, in the first row column header, right-click `[StoreID]` and then click **Expression**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-273">式ペインで、先頭の `equals` (=) を除くすべてのテキストを削除します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-273">In the expression pane, delete all text except the beginning `equals` (=).</span></span>  
  
4.  <span data-ttu-id="b0cb3-274">**[カテゴリ]** で、 **[共通の関数]** を展開して **[その他]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-274">In **Category**, expand **Common Functions**, and click **Miscellaneous**.</span></span> <span data-ttu-id="b0cb3-275">アイテム ペインに関数セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-275">The Item pane displays a set of functions.</span></span>  
  
5.  <span data-ttu-id="b0cb3-276">[アイテム] で、 **[参照]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-276">In Item, double-click **Lookup**.</span></span> <span data-ttu-id="b0cb3-277">式ペインに " `=Lookup(`" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-277">The expression pane displays `=Lookup(`.</span></span> <span data-ttu-id="b0cb3-278">サンプル ペインに Lookup 構文の例が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-278">The Example pane displays an example of Lookup syntax.</span></span>  
  
6.  <span data-ttu-id="b0cb3-279">次の式を入力します。 `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`</span><span class="sxs-lookup"><span data-stu-id="b0cb3-279">Type the following expression: `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`</span></span>  
  
     <span data-ttu-id="b0cb3-280">Lookup 関数は、StoreID の値を受け取って Stores データセットを検索して、StoreName の値を返します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-280">The Lookup function takes the value for StoreID, looks it up in the "Stores" dataset, and returns the StoreName value.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="b0cb3-281">ストア列ヘッダーには、複合式の表示テキストが含まれてい **<\<Expr>>** ます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-281">The store column header contains the display text for a complex expression: **<\<Expr>>**.</span></span>  
  
8.  <span data-ttu-id="b0cb3-282">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-282">Preview the report.</span></span>  
  
 <span data-ttu-id="b0cb3-283">各ページの上部にあるテキスト ボックスに、店舗 ID ではなく店舗名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-283">The text box at the top of each page displays the store name instead of the store identifier.</span></span>  
  
##  <a name="5-display-the-selected-parameter-value-in-the-report"></a><a name="Expression"></a><span data-ttu-id="b0cb3-284">5. 選択したパラメーター値をレポートに表示する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-284">5. Display the Selected Parameter Value in the Report</span></span>  
 <span data-ttu-id="b0cb3-285">ユーザーがレポートの詳細を確認する場合に、選択したパラメーターの値がわかるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-285">When a user has questions about a report, it helps to know which parameter values they chose.</span></span> <span data-ttu-id="b0cb3-286">レポートのパラメーターごとにユーザーが選択した値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-286">You can preserve user-selected values for each parameter in the report.</span></span> <span data-ttu-id="b0cb3-287">そのための方法の 1 つとして、ページ フッターのテキスト ボックスにパラメーターを表示する方法があります。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-287">One way is to display the parameters in a text box in the page footer.</span></span>  
  
#### <a name="to-display-the-selected-parameter-value-and-label-on-a-page-footer"></a><span data-ttu-id="b0cb3-288">選択されたパラメーターの値とラベルをページ フッターに表示するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-288">To display the selected parameter value and label on a page footer</span></span>  
  
1.  <span data-ttu-id="b0cb3-289">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-289">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="b0cb3-290">ページフッターを右クリックし、[**挿入**] をポイントして、[**テキストボックス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-290">Right-click the page footer, point to **Insert**, and then click **Text Box**.</span></span> <span data-ttu-id="b0cb3-291">タイムスタンプを示すテキスト ボックスの横にテキスト ボックスをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-291">Drag the text box next to the text box with the time stamp.</span></span> <span data-ttu-id="b0cb3-292">テキスト ボックスの側面にあるハンドルをクリックしてドラッグすることにより、幅を拡張します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-292">Grab the side handle of the text box and expand the width.</span></span>  
  
3.  <span data-ttu-id="b0cb3-293">レポートデータペインからテキストボックスにパラメーターをドラッグし *@StoreID* ます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-293">From the Report Data pane, drag the parameter *@StoreID* to the text box.</span></span> <span data-ttu-id="b0cb3-294">テキスト ボックスに " `[@StoreID]`" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-294">The text box displays `[@StoreID]`.</span></span>  
  
4.  <span data-ttu-id="b0cb3-295">パラメーターのラベルを表示するには、既存の式の後ろに挿入カーソルが表示されるまでテキスト ボックスをクリックし、空白を入力した後、レポート データ ペインからテキスト ボックスにもう一度パラメーターをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-295">To display the parameter label, click in the text box until the insert cursor appears after the existing expression, type a space, and then drag another copy of the parameter from the Report Data pane to the text box.</span></span> <span data-ttu-id="b0cb3-296">テキスト ボックスに " `[@StoreID] [@StoreID]`" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-296">The text box displays `[@StoreID] [@StoreID]`.</span></span>  
  
5.  <span data-ttu-id="b0cb3-297">最初の式を右クリックし、[**式**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-297">Right-click the first expression and click **Expression**.</span></span> <span data-ttu-id="b0cb3-298">**[式]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-298">The **Expression** dialog box opens.</span></span> <span data-ttu-id="b0cb3-299">「`Value`」を「`Label`」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-299">Replace the text `Value` by `Label`.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="b0cb3-300">テキスト ボックスに " `[@StoreID.Label] [@StoreID]`" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-300">The text displays: `[@StoreID.Label] [@StoreID]`.</span></span>  
  
7.  <span data-ttu-id="b0cb3-301">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-301">Preview the report.</span></span>  
  
##  <a name="6-use-the-report-parameter-in-a-filter"></a><a name="Filter"></a><span data-ttu-id="b0cb3-302">6. フィルターでレポートパラメーターを使用する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-302">6. Use the Report Parameter in a Filter</span></span>  
 <span data-ttu-id="b0cb3-303">フィルターを使用すると、外部データ ソースから取得されたデータのうちどのデータをレポートで使用するかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-303">Filters help control which data to use in a report after it is retrieved from an external data source.</span></span> <span data-ttu-id="b0cb3-304">表示するデータをユーザーが制御できるようにするには、マトリックスのフィルターにレポート パラメーターを含めます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-304">To let a user help control the data they want to see, you can include the report parameter in a filter for the matrix.</span></span>  
  
#### <a name="to-specify-a-parameter-in-a-matrix-filter"></a><span data-ttu-id="b0cb3-305">マトリックス フィルターにパラメーターを指定するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-305">To specify a parameter in a matrix filter</span></span>  
  
1.  <span data-ttu-id="b0cb3-306">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-306">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="b0cb3-307">マトリックス上の行ヘッダーまたは列ヘッダーのハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-307">Right-click a row or column header handle on the matrix, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-308">**[フィルター]** をクリックして、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-308">Click **Filters**, and then click **Add**.</span></span> <span data-ttu-id="b0cb3-309">新しいフィルター行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-309">A new filter row appears.</span></span>  
  
4.  <span data-ttu-id="b0cb3-310">**[式]** ドロップダウン リストからデータセット フィールドの StoreID を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-310">In **Expression**, from the drop-down list, select the dataset field StoreID.</span></span> <span data-ttu-id="b0cb3-311">データ型に **[整数]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-311">The data type displays **Integer**.</span></span> <span data-ttu-id="b0cb3-312">式の値がデータセット フィールドの場合、データ型は自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-312">When the expression value is a dataset field, the data type is set automatically.</span></span>  
  
5.  <span data-ttu-id="b0cb3-313">[**演算子**] で、 `equals` (=) が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-313">In **Operator**, verify that `equals` (=) is selected.</span></span>  
  
6.  <span data-ttu-id="b0cb3-314">**[値]** に「`[@StoreID]`」を入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-314">In **Value**, type `[@StoreID]`.</span></span> <span data-ttu-id="b0cb3-315">`[@StoreID]` は、 `=Parameters!StoreID.Value`を表す単純な式の構文です。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-315">`[@StoreID]` is the simple expression syntax that represents `=Parameters!StoreID.Value`.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="b0cb3-316">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-316">Preview the report.</span></span>  
  
     <span data-ttu-id="b0cb3-317">マトリックスに、"Contoso Catalog Store" のデータのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-317">The matrix displays data only for "Contoso Catalog Store".</span></span>  
  
9. <span data-ttu-id="b0cb3-318">レポート ビューアー ツール バーで、" **Store name?**" に対して **Contoso Asia Online Store**を選択し、 **[レポートの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-318">On the report viewer toolbar, for **Store name?**, select **Contoso Asia Online Store**, and then click **View Report**.</span></span>  
  
 <span data-ttu-id="b0cb3-319">マトリックスに、選択した店舗に対応するデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-319">The matrix displays data that corresponds to the store that you selected.</span></span>  
  
##  <a name="7-change-the-report-parameter-to-accept-multiple-values"></a><a name="Multivalued"></a><span data-ttu-id="b0cb3-320">7. レポートパラメーターを複数の値を受け入れるように変更する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-320">7. Change the Report Parameter to Accept Multiple Values</span></span>  
 <span data-ttu-id="b0cb3-321">パラメーターを単一値ではなく複数値をとるように変更するには、クエリと、フィルターなどのパラメーターへの参照を含むすべての式を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-321">To change a parameter from single to multivalued, you must change the query, and all expressions that contain a reference to the parameter, including filters.</span></span> <span data-ttu-id="b0cb3-322">複数値パラメーターは値の配列です。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-322">A multivalued parameter is an array of values.</span></span> <span data-ttu-id="b0cb3-323">データセット クエリでは、クエリ構文で 1 つの値が一連の値に含まれているかどうかをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-323">In a dataset query, query syntax must test for inclusion of one value in a set of values.</span></span> <span data-ttu-id="b0cb3-324">レポート式では、式の構文が個々の値ではなく値の配列にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-324">In a report expression, expression syntax must access an array of values instead of an individual value.</span></span>  
  
#### <a name="to-change-a-parameter-from-single-to-multivalued"></a><span data-ttu-id="b0cb3-325">パラメーターを単一値ではなく複数値をとるように変更するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-325">To change a parameter from single to multivalued</span></span>  
  
1.  <span data-ttu-id="b0cb3-326">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-326">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="b0cb3-327">レポートデータペインでを右クリックし、[ *@StoreID* **パラメーターのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-327">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-328">**[複数の値を許可]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-328">Select **Allow multiple values**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="b0cb3-329">レポート データ ペインで、 **[データセット]** フォルダーを展開して **DataSet1**を右クリックし、 **[クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-329">In the Report Data pane, expand the **Datasets** folder, right-click **DataSet1**, and then click **Query**.</span></span>  
  
6.  <span data-ttu-id="b0cb3-330">`equals`クエリの最後の行の句で、(=) をに変更し `IN` [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` ます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-330">Change `equals` (=) to `IN` in the [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause in the last line in the query:</span></span>  
  
    ```  
    WHERE StoreID IN (@StoreID)  
    ```  
  
     <span data-ttu-id="b0cb3-331">`IN` 演算子によって、値が一連の値に含まれているかどうかがテストされます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-331">The `IN` operator tests a value for inclusion in a set of values.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="b0cb3-332">マトリックス上の行ヘッダーまたは列ヘッダーのハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-332">Right-click a row or column header handle on the matrix, and then click **Tablix Properties**.</span></span>  
  
9. <span data-ttu-id="b0cb3-333">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-333">Click **Filters**.</span></span>  
  
10. <span data-ttu-id="b0cb3-334">**[演算子]** で **[次に含まれる]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-334">In **Operator**, select **In**.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="b0cb3-335">ページ フッターのパラメーターを表示するテキスト ボックスで、すべてのテキストを削除します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-335">In the text box that displays the parameter in the page footer, delete all text.</span></span>  
  
13. <span data-ttu-id="b0cb3-336">テキスト ボックスを右クリックして、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-336">Right-click the text box, and then click **Expression**.</span></span> <span data-ttu-id="b0cb3-337">次の式を入力します。 `=Join(Parameters!StoreID.Label, ", ")`</span><span class="sxs-lookup"><span data-stu-id="b0cb3-337">Type the following expression: `=Join(Parameters!StoreID.Label, ", ")`</span></span>  
  
     <span data-ttu-id="b0cb3-338">この式は、ユーザーが選択したすべての店舗名を連結します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-338">This expression concatenates all store names that the user selected.</span></span>  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. <span data-ttu-id="b0cb3-339">作成した式の前にあるテキスト ボックス内をクリックして、「Parameter Values Selected:」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-339">Click in the text box in front of the expression that you just created, and then type the following: Parameter Values Selected:.</span></span>  
  
16. <span data-ttu-id="b0cb3-340">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-340">Preview the report.</span></span>  
  
17. <span data-ttu-id="b0cb3-341">"Store Name?" の横にあるドロップダウン リストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-341">Click the drop-down list next to Store Name?</span></span>  
  
     <span data-ttu-id="b0cb3-342">有効な各値がチェック ボックスの横に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-342">Each valid value appears next to a check box.</span></span>  
  
18. <span data-ttu-id="b0cb3-343">**[すべて選択]** をクリックして、 **[レポートの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-343">Click **Select All**, and then click **View Report**.</span></span>  
  
     <span data-ttu-id="b0cb3-344">レポートに、全店舗のすべてのサブカテゴリの販売数量が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-344">The report displays the quantity sold for all subcategories for all stores.</span></span>  
  
19. <span data-ttu-id="b0cb3-345">ドロップダウン リストで **[すべて選択]** をクリックして一覧を消去し、"Contoso Catalog Store" と "Contoso Asia Online Store" をクリックして **[レポートの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-345">From the drop-down list, click **Select All** to clear the list, click "Contoso Catalog Store" and "Contoso Asia Online Store", and then click **View Report**.</span></span>  
  
##  <a name="8-add-a-boolean-parameter-for-conditional-visibility"></a><a name="Boolean"></a><span data-ttu-id="b0cb3-346">8. 条件付き表示のためのブール型パラメーターを追加する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-346">8. Add a Boolean Parameter for Conditional Visibility</span></span>  
  
#### <a name="to-add-a-boolean-parameter"></a><span data-ttu-id="b0cb3-347">ブール型パラメーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-347">To add a boolean parameter</span></span>  
  
1.  <span data-ttu-id="b0cb3-348">デザイン画面のレポート データ ペインで **[パラメーター]** を右クリックし、 **[パラメーターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-348">On the design surface, in the Report Data pane, right-click **Parameters**, and click **Add Parameter**.</span></span>  
  
2.  <span data-ttu-id="b0cb3-349">**[名前]** に「ShowSelections」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-349">In **Name**, type ShowSelections.</span></span>  
  
3.  <span data-ttu-id="b0cb3-350">**[プロンプト]** に「Show selections?」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-350">In **Prompt**, type Show selections?</span></span>  
  
4.  <span data-ttu-id="b0cb3-351">[**データ型**] のドロップダウンリストで、[**ブール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-351">In **Data type**, from the drop-down list, click **Boolean**.</span></span>  
  
5.  <span data-ttu-id="b0cb3-352">**[既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-352">Click **Default Values**.</span></span>  
  
6.  <span data-ttu-id="b0cb3-353">**[値の指定]** をクリックして、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-353">Click **Specify value**, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="b0cb3-354">**[値]** に「 **False**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-354">In **Value**, type **False**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-set-visibility-based-on-a-boolean-parameter"></a><span data-ttu-id="b0cb3-355">ブール型パラメーターに基づいて表示を設定するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-355">To set visibility based on a boolean parameter</span></span>  
  
1.  <span data-ttu-id="b0cb3-356">デザイン画面で、ページ フッターのパラメーター値を表示するテキスト ボックスを右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-356">On the design surface, right-click the text box in the page footer that displays the parameter values, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="b0cb3-357">**[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-357">Click **Visibility**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-358">**[式を基に表示/非表示を切り替える]** オプションを選択し、式ボタン ( **[Fx]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-358">Select the option **Show or hide based on an expression**, and then click the expression button **Fx**.</span></span>  
  
4.  <span data-ttu-id="b0cb3-359">次の式を入力します。 `=Not Parameters!ShowSelections.Value`</span><span class="sxs-lookup"><span data-stu-id="b0cb3-359">Type the following expression: `=Not Parameters!ShowSelections.Value`</span></span>  
  
     <span data-ttu-id="b0cb3-360">テキスト ボックスの [表示] オプションは、[非表示] プロパティによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-360">The text box Visibility option is controlled by the property Hidden.</span></span> <span data-ttu-id="b0cb3-361">`Not` 演算子を適用すると、パラメーターが選択されたときに、[非表示] プロパティが false になり、テキスト ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-361">Apply the `Not` operator so that when the parameter is selected, the Hidden property is false, and the text box will be displayed.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="b0cb3-362">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-362">Preview the report.</span></span>  
  
     <span data-ttu-id="b0cb3-363">パラメーターの選択肢を表示するテキスト ボックスが表示されません。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-363">The text box that displays the parameter choices does not appear.</span></span>  
  
8.  <span data-ttu-id="b0cb3-364">レポートビューアーツールバーで、[**選択内容の表示**] の横にあるをクリックし `True` ます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-364">In the report viewer toolbar, next to **Show selections**, click `True`.</span></span>  
  
9. <span data-ttu-id="b0cb3-365">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-365">Preview the report.</span></span>  
  
 <span data-ttu-id="b0cb3-366">ページ フッターのテキスト ボックスに、選択したすべての店舗名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-366">The text box in the page footer displays all the store names that you selected.</span></span>  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="b0cb3-367">9. レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-367">9. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="b0cb3-368">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-368">To add a report title</span></span>  
  
1.  <span data-ttu-id="b0cb3-369">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-369">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="b0cb3-370">「Parameterized Product Sales」と入力し、テキスト ボックスの外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-370">Type Parameterized Product Sales, and then click outside the text box.</span></span>  
  
##  <a name="10-save-the-report"></a><a name="Save"></a><span data-ttu-id="b0cb3-371">10. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="b0cb3-371">10. Save the Report</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="b0cb3-372">レポート サーバーにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="b0cb3-372">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="b0cb3-373">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-373">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="b0cb3-374">**[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-374">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="b0cb3-375">レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-375">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="b0cb3-376">" **レポート サーバーに接続しています**" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-376">The message **Connecting to report server appears**.</span></span> <span data-ttu-id="b0cb3-377">接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-377">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="b0cb3-378">**[名前]** に表示されている既定の名前を Parameterized Sales Report に変更します。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-378">In **Name**, replace the default name with Parameterized Sales Report.</span></span>  
  
5.  <span data-ttu-id="b0cb3-379">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-379">Click **Save**.</span></span>  
  
 <span data-ttu-id="b0cb3-380">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-380">The report is saved to the report server.</span></span> <span data-ttu-id="b0cb3-381">接続しているレポート サーバーがウィンドウ下部のステータス バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-381">The report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b0cb3-382">次の手順</span><span class="sxs-lookup"><span data-stu-id="b0cb3-382">Next Steps</span></span>  
 <span data-ttu-id="b0cb3-383">これで、レポートにパラメーターを追加する方法のチュートリアルは終了です。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-383">This concludes the walkthrough for how to add a parameter to your report.</span></span> <span data-ttu-id="b0cb3-384">パラメーターの詳細については、「[レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](report-design/report-parameters-report-builder-and-report-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0cb3-384">To learn more about parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0cb3-385">参照</span><span class="sxs-lookup"><span data-stu-id="b0cb3-385">See Also</span></span>  
 <span data-ttu-id="b0cb3-386">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="b0cb3-386">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="b0cb3-387">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="b0cb3-387">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
