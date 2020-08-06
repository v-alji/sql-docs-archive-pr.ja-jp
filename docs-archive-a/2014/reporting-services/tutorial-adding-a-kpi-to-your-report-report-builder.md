---
title: 'チュートリアル: レポートへの KPI の追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1bf77859-0b33-4f40-abaf-ebeeb6ebb1f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 405978721068583597adf5c4257978a222121078
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720942"
---
# <a name="tutorial-adding-a-kpi-to-your-report-report-builder"></a><span data-ttu-id="ee511-102">チュートリアル: レポートへの KPI の追加 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="ee511-102">Tutorial: Adding a KPI to Your Report (Report Builder)</span></span>
  <span data-ttu-id="ee511-103">主要業績評価指標 (KPI) は、ビジネス上重要な測定可能値です。</span><span class="sxs-lookup"><span data-stu-id="ee511-103">A key performance indicator (KPI) is a measurable value that has business significance.</span></span> <span data-ttu-id="ee511-104">このチュートリアルでは、レポートに KPI を追加する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="ee511-104">This tutorial teaches you how to include a (KPI) in a report.</span></span> <span data-ttu-id="ee511-105">このシナリオの KPI は、製品サブカテゴリ別の販売集計です。</span><span class="sxs-lookup"><span data-stu-id="ee511-105">In this scenario, the sales summary by product subcategories is the KPI.</span></span> <span data-ttu-id="ee511-106">この KPI の現在の状態を、色、ゲージ、およびインジケーターを使用して表示します。</span><span class="sxs-lookup"><span data-stu-id="ee511-106">The current state of the KPI is shown by using colors, gauges, and indicators.</span></span>  
  
 <span data-ttu-id="ee511-107">次の図に、ここで作成するレポートを示します。</span><span class="sxs-lookup"><span data-stu-id="ee511-107">The following illustration shows the report that you will create.</span></span>  
  
 <span data-ttu-id="ee511-108">![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")</span><span class="sxs-lookup"><span data-stu-id="ee511-108">![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="ee511-109">学習内容</span><span class="sxs-lookup"><span data-stu-id="ee511-109">What You Will Learn</span></span>  
 <span data-ttu-id="ee511-110">このチュートリアルでは、テーブルのセルの背景色をセルの値に基づいて設定することによって KPI を追加する方法、ゲージおよびインジケーターを追加して構成する方法、</span><span class="sxs-lookup"><span data-stu-id="ee511-110">In this tutorial, you will learn to add a KPI by setting the background color of table cells based on cell value and add and configure a gauge and an indicator.</span></span> <span data-ttu-id="ee511-111">およびテーブルのセルの背景色を設定する式を作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="ee511-111">You also learn to write the expression that sets the background color of the table cells.</span></span>  
  
 <span data-ttu-id="ee511-112">このチュートリアルでは以下の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee511-112">This tutorial contains the following procedures:</span></span>  
  
1.  [<span data-ttu-id="ee511-113">テーブルまたはマトリックス ウィザードを使用して表レポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="ee511-113">Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>](#Table)  
  
2.  [<span data-ttu-id="ee511-114">テーブルまたはマトリックス ウィザードでデータを整理し、レイアウトとスタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="ee511-114">Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>](#CompleteWizard)  
  
3.  [<span data-ttu-id="ee511-115">背景色を使用して KPI を表示する</span><span class="sxs-lookup"><span data-stu-id="ee511-115">Use Background Colors to Display a KPI</span></span>](#BackgroundColors)  
  
4.  [<span data-ttu-id="ee511-116">ゲージを使用して KPI を表示する</span><span class="sxs-lookup"><span data-stu-id="ee511-116">Display a KPI by Using a Gauge</span></span>](#Gauge)  
  
5.  [<span data-ttu-id="ee511-117">インジケーターを使用して KPI を表示する</span><span class="sxs-lookup"><span data-stu-id="ee511-117">Display a KPI by Using an Indicator</span></span>](#Indicator)  
  
6.  [<span data-ttu-id="ee511-118">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="ee511-118">Add a Report Title</span></span>](#Title)  
  
7.  [<span data-ttu-id="ee511-119">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="ee511-119">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="ee511-120">このチュートリアルでは、ウィザードに関する複数の手順を、データセットの作成とテーブルの作成の 2 つの手順にまとめて示します。</span><span class="sxs-lookup"><span data-stu-id="ee511-120">In this tutorial, the steps for the wizard are consolidated into two procedures: one to create the dataset and one to create a table.</span></span> <span data-ttu-id="ee511-121">レポート サーバーの参照、データ ソースの選択、データセットの作成、およびウィザードの実行に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 &#40;レポート ビルダー&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee511-121">For step-by-step instructions about how to browse to a report server, choose a data source, create a dataset, and run the wizard, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="ee511-122">このチュートリアルの推定所要時間: 15 分</span><span class="sxs-lookup"><span data-stu-id="ee511-122">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee511-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="ee511-123">Requirements</span></span>  
 <span data-ttu-id="ee511-124">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee511-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Table"></a><span data-ttu-id="ee511-125">1. テーブルまたはマトリックスウィザードからテーブルレポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="ee511-125">1. Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="ee511-126">[**はじめに**] ダイアログボックスで、共有データソースを選択し、埋め込みデータセットを作成して、データをテーブルに表示します。</span><span class="sxs-lookup"><span data-stu-id="ee511-126">From the **Getting Started** dialog box, choose a shared data source, create an embedded dataset, and display the data in a table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee511-127">このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="ee511-127">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="ee511-128">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="ee511-128">This makes the query quite long.</span></span> <span data-ttu-id="ee511-129">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="ee511-129">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="ee511-130">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="ee511-130">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-table"></a><span data-ttu-id="ee511-131">新しいテーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="ee511-131">To create a new table</span></span>  
  
1.  <span data-ttu-id="ee511-132">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="ee511-133">[**はじめに**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-133">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee511-134">[**はじめに**] ダイアログボックスが表示されない場合は、[レポートビルダー] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-134">If the **Getting Started** dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="ee511-135">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee511-135">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="ee511-136">右ペインで、 **[テーブルまたはマトリックス ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-136">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="ee511-137">[データセットの選択] ページで、 **[データセットを作成する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-137">On the Choose a dataset page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="ee511-138">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="ee511-139">[**データソースへの接続の選択**] ページで、既存のデータソースを選択するか、レポートサーバーを参照してデータソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="ee511-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source.</span></span> <span data-ttu-id="ee511-140">使用できるデータ ソースがなく、レポート サーバーにもアクセスできない場合は、代わりに埋め込みデータ ソースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee511-140">If there no data source is available or you do not have access to a report server, you can use an embedded data source instead.</span></span> <span data-ttu-id="ee511-141">詳細については、「[チュートリアル: 基本的な表レポートの作成 (レポート ビルダー)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee511-141">For more information, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
7.  <span data-ttu-id="ee511-142">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="ee511-143">**[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-143">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="ee511-144">次のクエリをコピーし、クエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="ee511-144">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Mini Battery Charger' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Telephoto Conversion Lens' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,'Accessories' as Subcategory,    
       'USB Cable' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Business Videographer' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-10' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Social Videographer' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Advanced Digital' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Compact Digital' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Consumer Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera 35mm' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
10. <span data-ttu-id="ee511-145">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-145">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-choose-layout-and-style-from-the-table-or-matrix-wizard"></a><a name="CompleteWizard"></a><span data-ttu-id="ee511-146">2. テーブルまたはマトリックスウィザードでデータを整理し、レイアウトとスタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="ee511-146">2. Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="ee511-147">ウィザードを使用して、データを表示する最初のデザインを作成します。</span><span class="sxs-lookup"><span data-stu-id="ee511-147">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="ee511-148">ウィザードのプレビュー ペインでは、テーブルやマトリックスのデザインを完了する前にデータのグループ化の結果を表示できます。</span><span class="sxs-lookup"><span data-stu-id="ee511-148">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the table or matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups-choose-a-layout-and-a-style"></a><span data-ttu-id="ee511-149">データをグループにまとめるには、レイアウトとスタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="ee511-149">To organize data into groups, choose a layout and a style</span></span>  
  
1.  <span data-ttu-id="ee511-150">[フィールドの配置] ページで、Product を **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ee511-150">On the Arrange fields page, drag Product to **Values**.</span></span>  
  
2.  <span data-ttu-id="ee511-151">Quantity を **[値]** にドラッグして Product の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="ee511-151">Drag Quantity to **Values** and place below Product.</span></span>  
  
     <span data-ttu-id="ee511-152">Quantity は Sum 関数 (数値フィールドを集計するための既定の関数) を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-152">Quantity is summarized with the Sum function, the default function to summarize numeric fields.</span></span>  
  
3.  <span data-ttu-id="ee511-153">Sales を **[値]** にドラッグして Quantity の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="ee511-153">Drag Sales to **Values** and place below Quantity.</span></span>  
  
     <span data-ttu-id="ee511-154">手順 1. ～ 3. で、テーブルに表示するデータが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-154">Steps 1, 2, and 3 specify the data to display in the table.</span></span>  
  
4.  <span data-ttu-id="ee511-155">SalesDate を **[行グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ee511-155">Drag SalesDate to **Row groups**.</span></span>  
  
5.  <span data-ttu-id="ee511-156">Subcategory を **[行グループ]** にドラッグして SalesDate の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="ee511-156">Drag Subcategory to **Row groups** and place below SalesDate.</span></span>  
  
     <span data-ttu-id="ee511-157">手順 4. および 5. で、フィールドの値がまず日付でまとめられ、次にその日付のすべての売上でまとめられます。</span><span class="sxs-lookup"><span data-stu-id="ee511-157">Steps 4 and 5 organize the values for the fields first by date, and then by all sales for that date.</span></span>  
  
6.  <span data-ttu-id="ee511-158">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-158">Click **Next**.</span></span>  
  
     <span data-ttu-id="ee511-159">レポートを実行すると、テーブルに各日付、日付ごとのすべての注文、および注文ごとのすべての製品、数量、および売上の合計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-159">When you run the report, the table displays each date, all orders for each date, and all products, quantities, and sales totals for each order.</span></span>  
  
7.  <span data-ttu-id="ee511-160">[レイアウトの選択] ページの **[オプション]** で、 **[小計と総計を表示]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee511-160">On the Choose the Layout page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
8.  <span data-ttu-id="ee511-161">**[ブロック、小計は下]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee511-161">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
9. <span data-ttu-id="ee511-162">**[グループの展開/折りたたみ]** オプションをオフにします。</span><span class="sxs-lookup"><span data-stu-id="ee511-162">Clear the option **Expand/collapse groups**.</span></span>  
  
     <span data-ttu-id="ee511-163">このチュートリアルで作成するレポートでは、ユーザーが親グループ階層を展開して子グループ行および詳細行を表示できるようにするドリル ダウン機能は使用されません。</span><span class="sxs-lookup"><span data-stu-id="ee511-163">In this tutorial, the report you create does not use the drilldown feature that lets a user expand a parent group hierarchy to display child group rows and detail rows.</span></span>  
  
10. <span data-ttu-id="ee511-164">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-164">Click **Next**.</span></span>  
  
11. <span data-ttu-id="ee511-165">[スタイルの選択] ページのスタイル ペインで、スタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="ee511-165">On the Choose a Style page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="ee511-166">先ほどの図の完成したレポートでは、[オーシャン] スタイルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="ee511-166">The illustration of the completed report shows the report using the Ocean style.</span></span>  
  
12. <span data-ttu-id="ee511-167">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-167">Click **Finish**.</span></span>  
  
     <span data-ttu-id="ee511-168">テーブルがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-168">The table is added to the design surface.</span></span> <span data-ttu-id="ee511-169">テーブルには 5 列 5 行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee511-169">The table has five columns and five rows.</span></span> <span data-ttu-id="ee511-170">行グループ ペインに、SalesDate、Subcategory、および Details の 3 つの行グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-170">The Row Groups pane shows three row groups: SalesDate, Subcategory, and Details.</span></span> <span data-ttu-id="ee511-171">詳細データは、データセット クエリによって取得されるすべてのデータです。</span><span class="sxs-lookup"><span data-stu-id="ee511-171">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
13. <span data-ttu-id="ee511-172">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="ee511-172">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="ee511-173">テーブルには、特定の日付に販売された製品ごとに製品名、販売数量、および売上合計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-173">For each product that is sold on a specific date, the table displays the product name, the quantity sold, and the sales total.</span></span> <span data-ttu-id="ee511-174">このデータがまず販売日でまとめられ、次にサブカテゴリでまとめられます。</span><span class="sxs-lookup"><span data-stu-id="ee511-174">The data is organized first by sales date and then by subcategory.</span></span>  
  
##  <a name="3-use-background-colors-to-display-a-kpi"></a><a name="BackgroundColors"></a><span data-ttu-id="ee511-175">3. 背景色を使用して KPI を表示する</span><span class="sxs-lookup"><span data-stu-id="ee511-175">3. Use Background Colors to Display a KPI</span></span>  
 <span data-ttu-id="ee511-176">背景色を、レポートの実行時に評価される式に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="ee511-176">Background colors can be set to an expression that is evaluated when you run the report.</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-by-using-background-colors"></a><span data-ttu-id="ee511-177">背景色を使用して KPI の現在の状態を表示するには</span><span class="sxs-lookup"><span data-stu-id="ee511-177">To display the present state of a KPI by using background colors</span></span>  
  
1.  <span data-ttu-id="ee511-178">テーブルで、 `[Sum(Sales)]` セル (サブカテゴリの売上を表示する小計行) の下の2つのセルを右クリックし、[**テキストボックスのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-178">In the table, right-click two cells down from the `[Sum(Sales)]` cell (the subtotal row that displays the sales for a subcategory), and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="ee511-179">[**塗りつぶし**] で、[**塗りつぶしの色**] オプションの横にある [ **fx** ] ボタンをクリックし、[**式の設定: BackgroundColor** ] フィールドに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="ee511-179">In **Fill**, click the **fx** button next to the **Fill color** option and enter the following expression in the **Set expression for: BackgroundColor** field:</span></span>  
  
 `=IIF(Sum(Fields!Sales.Value) >= 5000 ,"Lime", IIF(Sum(Fields!Sales.Value) < 2500, "Red","Yellow"))`  
  
 <span data-ttu-id="ee511-180">これにより、`[Sum(Sales)]` の集計値が 5000 以上になる各セルの背景色が、"ライム" という緑の網掛けを使用した緑色に変わります。</span><span class="sxs-lookup"><span data-stu-id="ee511-180">This changes the background color to green, using the shade of green named "Lime", for each cell that contains an aggregated sum for `[Sum(Sales)]` that is greater than or equal to 5000.</span></span> <span data-ttu-id="ee511-181">2500 ～ 5000 の `[Sum(Sales)]` の値は、黄色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-181">Values of `[Sum(Sales)]` between 2500 and 5000 are colored yellow.</span></span> <span data-ttu-id="ee511-182">2500 未満の値は赤色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-182">Values less than 2500 are colored red.</span></span>  
  
1.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
2.  <span data-ttu-id="ee511-183">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="ee511-183">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="ee511-184">サブカテゴリの売上を表示する小計行のセルの背景色が、合計売上の値に応じて赤、黄、または緑になります。</span><span class="sxs-lookup"><span data-stu-id="ee511-184">In the subtotal row that displays the sales for a subcategory, the background color of the cell is red, yellow, or green depending on value of the sales sum.</span></span>  
  
##  <a name="4-display-a-kpi-by-using-a-gauge"></a><a name="Gauge"></a><span data-ttu-id="ee511-185">4. ゲージを使用して KPI を表示する</span><span class="sxs-lookup"><span data-stu-id="ee511-185">4. Display a KPI by Using a Gauge</span></span>  
 <span data-ttu-id="ee511-186">ゲージは、データセットの単一の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="ee511-186">A gauge depicts a single value in a dataset.</span></span> <span data-ttu-id="ee511-187">このチュートリアルでは、水平方向の線形ゲージを使用します。このゲージは、その形と単純さにより、テーブルのセルで使用してサイズが小さくなっても読み取りやすいからです。</span><span class="sxs-lookup"><span data-stu-id="ee511-187">This tutorial uses a horizontal linear gauge because its shape and simplicity makes it easy to read, even in when it is a small size and used within a table cell.</span></span> <span data-ttu-id="ee511-188">詳しくは、「 [ゲージ &#40;レポート ビルダーおよび SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee511-188">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-a-gauge"></a><span data-ttu-id="ee511-189">ゲージを使用して KPI の現在の状態を表示するには</span><span class="sxs-lookup"><span data-stu-id="ee511-189">To display the present state of a KPI using a gauge</span></span>  
  
1.  <span data-ttu-id="ee511-190">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ee511-190">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="ee511-191">テーブルで、前の手順で変更したセルの列ハンドラーを右クリックし、[**列の挿入**] をポイントして、[**右**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-191">In the table, right-click the column handler for the cell that you changed in the previous procedure, point to **Insert Column**, and then click **Right**.</span></span> <span data-ttu-id="ee511-192">テーブルに新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-192">A new column is added to the table.</span></span>  
  
3.  <span data-ttu-id="ee511-193">列見出しに「 **KPI** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ee511-193">Type **KPI** in the column heading.</span></span>  
  
4.  <span data-ttu-id="ee511-194">[**挿入**] タブの [**データ領域**] グループで、[**ゲージ**] をクリックし、テーブルの外側にあるデザイン画面をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-194">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then click the design surface outside the table.</span></span> <span data-ttu-id="ee511-195">**[ゲージの種類の選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-195">The **Select Gauge Type** dialog box appears.</span></span>  
  
5.  <span data-ttu-id="ee511-196">[**線形**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-196">Click **Linear**.</span></span> <span data-ttu-id="ee511-197">最初の線形ゲージの種類 (**水平**) が選択されています。</span><span class="sxs-lookup"><span data-stu-id="ee511-197">The first linear gauge type, **Horizontal**, is selected.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="ee511-198">デザイン画面にゲージが追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-198">A gauge is added to the design surface.</span></span>  
  
7.  <span data-ttu-id="ee511-199">レポート データ ペインからゲージに Sales をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ee511-199">From the Report Data pane, drag Sales to the gauge.</span></span> <span data-ttu-id="ee511-200">Sales をゲージにドラッグすると、ゲージ データ ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="ee511-200">When you drag Sales across the gauge, the Gauge Data pane opens.</span></span>  
  
8.  <span data-ttu-id="ee511-201">[**値**] ボックスの一覧の [Sales] を削除します。</span><span class="sxs-lookup"><span data-stu-id="ee511-201">Drop Sales in the **Values** list.</span></span>  
  
     <span data-ttu-id="ee511-202">フィールドをゲージにドロップすると、組み込み Sum 関数を使用してフィールドが集計されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-202">When you drop the field onto the gauge, the field is aggregated by using the built-in Sum function.</span></span>  
  
9. <span data-ttu-id="ee511-203">ゲージ内のポインターを右クリックし、[**ポインターのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-203">Right-click the pointer in the gauge and click **Pointer Properties**.</span></span>  
  
10. <span data-ttu-id="ee511-204">[**ポインターの種類**] で、[**バー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee511-204">In **Pointer Type**, select **Bar**.</span></span> <span data-ttu-id="ee511-205">これにより、ポインターがマーカーからバーに変更され、テーブルにゲージを追加したときに見やすくなります。</span><span class="sxs-lookup"><span data-stu-id="ee511-205">This changes the pointer from a marker to a bar that will be more visible when the gauge is added to the table.</span></span>  
  
11. <span data-ttu-id="ee511-206">[**ポインターの塗りつぶし**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-206">Click **Pointer Fill**.</span></span> <span data-ttu-id="ee511-207">[ **2 番目の色] で、[黄] を**選択します。 **Yellow**</span><span class="sxs-lookup"><span data-stu-id="ee511-207">In **Secondary Color,** pick **Yellow**.</span></span> <span data-ttu-id="ee511-208">グラデーションの塗りつぶしパターンが白から黄色に変更されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-208">The gradient fill pattern will change from white to yellow.</span></span>  
  
12. <span data-ttu-id="ee511-209">ゲージのスケールを右クリックし、 **[スケールのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-209">Right-click the scale in the gauge and click **Scale Properties**.</span></span>  
  
13. <span data-ttu-id="ee511-210">[**最大**] オプションを25000に設定します。</span><span class="sxs-lookup"><span data-stu-id="ee511-210">Set the **Maximum** option to 25000.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee511-211">25000 などの定数の代わりに、 **[最大]** オプションの値を動的に計算する式を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee511-211">Instead of a constant such as 25000, you can use an expression to dynamically calculate the value of the **Maximum** option.</span></span> <span data-ttu-id="ee511-212">その式では、入れ子になった集計の機能を使用します (例: `=Max(Sum(Fields!Sales.value), "Tablix1")`)。</span><span class="sxs-lookup"><span data-stu-id="ee511-212">The expression would use the aggregate of aggregate feature and look similar to the expression `=Max(Sum(Fields!Sales.value), "Tablix1")`.</span></span>  
  
14. <span data-ttu-id="ee511-213">ゲージを、テーブル内の挿入した列の、サブカテゴリの売上を表示する小計行の 3 番目のセルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ee511-213">Drag the gauge inside the table into the third cell in the subtotal row that displays the sales for a subcategory of the column that you inserted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee511-214">水平方向の線形ゲージがセルに収まるように、列のサイズを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee511-214">You might have to resize the column so that the horizontal linear gauge fits into the cell.</span></span> <span data-ttu-id="ee511-215">列のサイズを変更するには、列ヘッダーをクリックし、ハンドルを使用してセルの横方向と縦方向のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="ee511-215">To resize the column, click a column header and use the handles to resize the cells horizontally and vertically.</span></span>  
  
15. <span data-ttu-id="ee511-216">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="ee511-216">Click **Run** to preview the report.</span></span>  
  
     <span data-ttu-id="ee511-217">ゲージ内のバーの幅が、KPI の値によって変わります。</span><span class="sxs-lookup"><span data-stu-id="ee511-217">The horizontal length of the bar in the gauge changes depending on the value of the KPI.</span></span>  
  
16. <span data-ttu-id="ee511-218">(省略可) オーバーフローを処理する最大ピンを追加して、スケールの最大値を超える任意の値が常に最大ピンを参照できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ee511-218">(Optional) Add a maximum pin to handle overflow so that any value over the scale maximum always points to the maximum pin:</span></span>  
  
    1.  <span data-ttu-id="ee511-219">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="ee511-219">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="ee511-220">[スケール] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-220">Click the scale.</span></span> <span data-ttu-id="ee511-221">線形スケールのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-221">The properties for the linear scale are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="ee511-222">[**スケールピン**] カテゴリで、[ **maximumpin** ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="ee511-222">In the **Scale Pins** category, expand the **MaximumPin** node.</span></span>  
  
    4.  <span data-ttu-id="ee511-223">**Enable**プロパティをに設定し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="ee511-223">Set the **Enable** property to `True`.</span></span> <span data-ttu-id="ee511-224">スケールの最大値の後にピンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-224">A pin appears after the maximum value on the scale.</span></span>  
  
    5.  <span data-ttu-id="ee511-225">**BorderColor**をに設定 `Lime` します。</span><span class="sxs-lookup"><span data-stu-id="ee511-225">Set **BorderColor** to `Lime`.</span></span>  
  
17. <span data-ttu-id="ee511-226">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="ee511-226">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-display-a-kpi-by-using-an-indicator"></a><a name="Indicator"></a><span data-ttu-id="ee511-227">5. インジケーターを使用して KPI を表示する</span><span class="sxs-lookup"><span data-stu-id="ee511-227">5. Display a KPI by Using an Indicator</span></span>  
 <span data-ttu-id="ee511-228">インジケーターは、データ値をひとめでわかるようにするための単純で小さなゲージです。</span><span class="sxs-lookup"><span data-stu-id="ee511-228">Indicators are small simple gauges that communicate data values at a glance.</span></span> <span data-ttu-id="ee511-229">そのサイズと単純さのために、テーブルやマトリックスでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-229">Because of their size and simplicity, indicators are often used in tables and matrices.</span></span> <span data-ttu-id="ee511-230">詳細については、「[インジケーター (レポート ビルダーおよび SSRS)](report-design/indicators-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee511-230">For more information, see [Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-an-indicator"></a><span data-ttu-id="ee511-231">インジケーターを使用して KPI の現在の状態を表示するには</span><span class="sxs-lookup"><span data-stu-id="ee511-231">To display the present state of a KPI using an indicator</span></span>  
  
1.  <span data-ttu-id="ee511-232">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ee511-232">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="ee511-233">テーブルで、前の手順で変更したセルの列ハンドラーを右クリックし、[**列の挿入**] をポイントして、[**右**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-233">In the table, right-click the column handler for the cell that you changed in the previous procedure, point to **Insert Column**, and then click **Right**.</span></span> <span data-ttu-id="ee511-234">テーブルに新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-234">A new column is added to the table.</span></span>  
  
3.  <span data-ttu-id="ee511-235">列見出しに「 **KPI** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ee511-235">Type **KPI** in the column heading.</span></span>  
  
4.  <span data-ttu-id="ee511-236">サブカテゴリの小計のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-236">Click the cell for the subcategory subtotal.</span></span>  
  
5.  <span data-ttu-id="ee511-237">[**挿入**] タブの [**データ領域**] グループで、[インジケーター] をダブルクリックし**ます。**</span><span class="sxs-lookup"><span data-stu-id="ee511-237">On the **Insert** tab, in the **Data Regions** group, double-click **Indicator.**</span></span>  
  
     <span data-ttu-id="ee511-238">**[インジケーターの種類の選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-238">The **Select Indicator Type** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="ee511-239">[**図形**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-239">Click **Shapes**.</span></span> <span data-ttu-id="ee511-240">最初の図形の種類である3つの信号 **(枠なし)** が選択されています。</span><span class="sxs-lookup"><span data-stu-id="ee511-240">The first shape type, **3 Traffic Lights (Unrimmed),** is selected.</span></span>  
  
     <span data-ttu-id="ee511-241">このチュートリアルではこのインジケーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee511-241">You will use this indicator in the tutorial.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="ee511-242">インジケーターがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-242">The indicator is added to the design surface.</span></span>  
  
8.  <span data-ttu-id="ee511-243">インジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-243">Right-click the indicator and click **Indicator Properties**.</span></span>  
  
9. <span data-ttu-id="ee511-244">[**値と状態] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-244">Click **Values and States**.</span></span>  
  
10. <span data-ttu-id="ee511-245">[値] ドロップダウンリストで **[Sum (Sales)]** を選択しますが、その他のオプションは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="ee511-245">In the Value drop-down list, select **[Sum(Sales)]**, but do not change any other options.</span></span>  
  
     <span data-ttu-id="ee511-246">既定では、データ領域のデータが同期され、 **Tablix1**という値 (レポートのテーブル データ領域の名前) が **[同期スコープ]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-246">By default, data synchronization occurs across the data region and you see the value **Tablix1**, the name of the table data region in the report, in the **Synchronization scope** box.</span></span>  
  
     <span data-ttu-id="ee511-247">このレポートでは、サブカテゴリの小計のセルに配置したインジケーターのスコープを変更して、SalesDate フィールドのデータが同期されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ee511-247">In this report, you can also change the scope of an indicator placed in the cell of the subcategory subtotal to synchronize across the SalesDate field.</span></span>  
  
11. <span data-ttu-id="ee511-248">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="ee511-248">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="ee511-249">6. レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="ee511-249">6. Add a Report Title</span></span>  
 <span data-ttu-id="ee511-250">レポート タイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-250">A report title appears at the top of the report.</span></span> <span data-ttu-id="ee511-251">レポート ヘッダーがあれば、そこにレポート タイトルを配置します。レポート ヘッダーを使用しない場合は、レポート本文の一番上のテキスト ボックスに配置します。</span><span class="sxs-lookup"><span data-stu-id="ee511-251">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="ee511-252">その場合は、自動的にレポート本文の一番上に配置されるテキスト ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee511-252">You will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="ee511-253">テキストの語句や文字のフォントのスタイル、サイズ、および色を変更して、テキストをさらに強調することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee511-253">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="ee511-254">詳細については、「[テキスト ボックス内のテキストの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee511-254">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="ee511-255">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="ee511-255">To add a report title</span></span>  
  
1.  <span data-ttu-id="ee511-256">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-256">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="ee511-257">「 **Product SALES KPI**」と入力し、テキストボックスの外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-257">Type **Product Sales KPI**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="ee511-258">必要に応じて、 **Product SALES KPI**が含まれているテキストボックスを右クリックし、[**テキストボックスのプロパティ**] をクリックします。次に、[フォント] タブで、異なるフォントスタイル、サイズ、および色を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee511-258">Optionally, right-click the text box that contains **Product Sales KPI**, click **Text Box Properties**, and then on the Font tab select the different font styles, sizes and colors.</span></span>  
  
4.  <span data-ttu-id="ee511-259">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="ee511-259">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="ee511-260">7. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="ee511-260">7. Save the Report</span></span>  
 <span data-ttu-id="ee511-261">レポートをレポート サーバーまたは自分のコンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="ee511-261">Save the report to a report server or your computer.</span></span> <span data-ttu-id="ee511-262">レポート サーバーに保存しない場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のいくつかの機能 (レポート パーツ、サブレポートなど) が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ee511-262">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="ee511-263">レポート サーバーにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="ee511-263">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="ee511-264">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-264">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="ee511-265">**[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-265">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="ee511-266">レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="ee511-266">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="ee511-267">"レポート サーバーに接続しています" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-267">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="ee511-268">接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-268">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="ee511-269">**[名前]** に入力されている既定の名前を「 **Product Sales KPI**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ee511-269">In **Name**, replace the default name with **Product Sales KPI**.</span></span>  
  
5.  <span data-ttu-id="ee511-270">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-270">Click **Save**.</span></span>  
  
 <span data-ttu-id="ee511-271">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-271">The report is saved to the report server.</span></span> <span data-ttu-id="ee511-272">接続しているレポート サーバーの名前がウィンドウ下部のステータス バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee511-272">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="ee511-273">コンピューターにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="ee511-273">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="ee511-274">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-274">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="ee511-275">**[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、レポートを保存するフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="ee511-275">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee511-276">レポート サーバーにアクセスできない場合は、 **[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、コンピューターにレポートを保存してください。</span><span class="sxs-lookup"><span data-stu-id="ee511-276">If you do not have access to a report server, click **Desktop**, **My Documents**, or **My computer** and save the report to your computer.</span></span>  
  
1.  <span data-ttu-id="ee511-277">**[名前]** に入力されている既定の名前を「 **Product Sales KPI**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ee511-277">In **Name**, replace the default name with **Product Sales KPI**.</span></span>  
  
2.  <span data-ttu-id="ee511-278">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee511-278">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ee511-279">次の手順</span><span class="sxs-lookup"><span data-stu-id="ee511-279">Next Steps</span></span>  
 <span data-ttu-id="ee511-280">これで、「レポートへの KPI の追加」チュートリアルを終了します。</span><span class="sxs-lookup"><span data-stu-id="ee511-280">You have successfully completed the Adding a KPI to Your Report tutorial.</span></span> <span data-ttu-id="ee511-281">詳細については、「ゲージ (レポートビルダー)[インジケーター &#40;レポートビルダーと SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee511-281">For more information, see Gauges (Report Builder) [Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee511-282">参照</span><span class="sxs-lookup"><span data-stu-id="ee511-282">See Also</span></span>  
 <span data-ttu-id="ee511-283">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="ee511-283">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="ee511-284">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="ee511-284">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
