---
title: 'チュートリアル: マトリックス レポートの作成 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9ee19c2e-2a8c-4bb0-9274-04a5812c2e96
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3df32098d9e6400931ba2a88b2ffd22d6e015a62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737819"
---
# <a name="tutorial-creating-a-matrix-report-report-builder"></a><span data-ttu-id="a83ab-102">チュートリアル: マトリックス レポートの作成 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="a83ab-102">Tutorial: Creating a Matrix Report (Report Builder)</span></span>
  <span data-ttu-id="a83ab-103">このチュートリアルでは、サンプルの売上データに基づいて基本的なマトリックス レポートを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-103">This tutorial teaches you how to create a basic matrix report based on sample sales data.</span></span> <span data-ttu-id="a83ab-104">このマトリックスは、入れ子になった行グループと列グループ、および隣接する列グループで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-104">The matrix has nested row and column groups and an adjacent column group.</span></span> <span data-ttu-id="a83ab-105">また、列を書式設定し、テキストを回転させる方法についても学習します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-105">You will also learn how to format columns and rotate text.</span></span> <span data-ttu-id="a83ab-106">次の図に、ここで作成するレポートと同様のレポートを示します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-106">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="a83ab-107">![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")</span><span class="sxs-lookup"><span data-stu-id="a83ab-107">![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")</span></span>  
  
 <span data-ttu-id="a83ab-108">このチュートリアルで作成するレポートの拡張バージョンは、サンプルレポートビルダーレポートとして入手でき [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-108">An enhanced version of the report you will create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="a83ab-109">このサンプルレポートおよびその他のレポートをダウンロードする方法の詳細については、「[レポートビルダーサンプルレポート](https://go.microsoft.com/fwlink/?LinkId=184851)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a83ab-109">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="a83ab-110">学習内容</span><span class="sxs-lookup"><span data-stu-id="a83ab-110">What You Will Learn</span></span>  
 <span data-ttu-id="a83ab-111">このチュートリアルでは、次の内容を学習します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-111">In this tutorial, you will learn how to:</span></span>  
  
1.  [<span data-ttu-id="a83ab-112">テーブルまたはマトリックスの新規作成ウィザードを使用してマトリックス レポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="a83ab-112">Create a Matrix Report and Dataset from the New Table or Matrix Wizard</span></span>](#CreateMatrix)  
  
2.  [<span data-ttu-id="a83ab-113">テーブルまたはマトリックスの新規作成ウィザードを使用してデータを整理し、レイアウトとスタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="a83ab-113">Organize Data and Choose Layout and Style from the New Table or Matrix Wizard</span></span>](#Groups)  
  
3.  [<span data-ttu-id="a83ab-114">データの書式設定</span><span class="sxs-lookup"><span data-stu-id="a83ab-114">Format Data</span></span>](#FormatData)  
  
4.  [<span data-ttu-id="a83ab-115">隣接する列グループを追加する</span><span class="sxs-lookup"><span data-stu-id="a83ab-115">Add Adjacent Column Group</span></span>](#AdjacentGroup)  
  
5.  [<span data-ttu-id="a83ab-116">列幅を変更する</span><span class="sxs-lookup"><span data-stu-id="a83ab-116">Change Column Widths</span></span>](#Width)  
  
6.  [<span data-ttu-id="a83ab-117">マトリックス セルを結合する</span><span class="sxs-lookup"><span data-stu-id="a83ab-117">Merge Matrix Cells</span></span>](#MergeCells)  
  
7.  [<span data-ttu-id="a83ab-118">レポート ヘッダーおよびレポート タイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="a83ab-118">Add a Report Header and Report Title</span></span>](#HeaderTitle)  
  
8.  [<span data-ttu-id="a83ab-119">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="a83ab-119">Save the Report</span></span>](#Save)  
  
### <a name="other-optional-step"></a><span data-ttu-id="a83ab-120">その他の省略可能な手順</span><span class="sxs-lookup"><span data-stu-id="a83ab-120">Other Optional Step</span></span>  
  
1.  [<span data-ttu-id="a83ab-121">テキスト ボックスを 270 度回転させる</span><span class="sxs-lookup"><span data-stu-id="a83ab-121">Rotate Text Box 270 Degrees</span></span>](#RotateTextBox)  
  
 <span data-ttu-id="a83ab-122">このチュートリアルの推定所要時間 : 20 分</span><span class="sxs-lookup"><span data-stu-id="a83ab-122">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a83ab-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="a83ab-123">Requirements</span></span>  
 <span data-ttu-id="a83ab-124">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a83ab-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-new-table-or-matrix-wizard"></a><a name="CreateMatrix"></a><span data-ttu-id="a83ab-125">1. テーブルまたはマトリックスの新規作成ウィザードからマトリックスレポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="a83ab-125">1. Create a Matrix Report and Dataset from the New Table or Matrix Wizard</span></span>  
 <span data-ttu-id="a83ab-126">レポートビルダーの [**はじめに**] ダイアログボックスで、共有データソースを選択し、埋め込みデータセットを作成して、マトリックスにデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-126">From the **Getting Started** dialog box in Report Builder, choose a shared data source, create an embedded dataset, and then display the data in a matrix.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a83ab-127">このチュートリアルのクエリには既にデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="a83ab-127">In this tutorial, the query already contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="a83ab-128">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="a83ab-128">This makes the query quite long.</span></span> <span data-ttu-id="a83ab-129">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="a83ab-129">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="a83ab-130">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="a83ab-130">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-matrix"></a><span data-ttu-id="a83ab-131">新しいマトリックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-131">To create a new matrix</span></span>  
  
1.  <span data-ttu-id="a83ab-132">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a83ab-133">**[作業の開始]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-133">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="a83ab-134">そうでない場合は、[レポートビルダー] ボタンの [**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-134">If it doesn't, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="a83ab-135">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-135">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="a83ab-136">右ペインで、 **[テーブルまたはマトリックス ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-136">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="a83ab-137">**[データセットの選択]** ページで、 **[データセットを作成する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-137">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="a83ab-138">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="a83ab-139">[**データソースへの接続の選択**] ページで、既存のデータソースを選択するか、レポートサーバーを参照してからデータソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server, and then select a data source.</span></span> <span data-ttu-id="a83ab-140">使用できるデータ ソースがなく、レポート サーバーにもアクセスできない場合は、代わりに埋め込みデータ ソースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-140">If no data source is available or you do not have access to a report server, you can use an embedded data source instead.</span></span> <span data-ttu-id="a83ab-141">埋め込みデータソースの作成の詳細については、「[チュートリアル: 基本的なテーブルレポートの作成 &#40;レポートビルダー&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a83ab-141">For more information about creating an embedded data source, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
7.  <span data-ttu-id="a83ab-142">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="a83ab-143">**[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-143">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="a83ab-144">次のクエリをコピーし、クエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-144">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
10. <span data-ttu-id="a83ab-145">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-145">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-and-choose-layout-and-style-from-the-new-table-or-matrix-wizard"></a><a name="Groups"></a><span data-ttu-id="a83ab-146">2. テーブルまたはマトリックスの新規作成ウィザードでデータを整理し、レイアウトとスタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="a83ab-146">2. Organize Data and Choose Layout and Style from the New Table or Matrix Wizard</span></span>  
 <span data-ttu-id="a83ab-147">ウィザードを使用して、データを表示する最初のデザインを作成します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-147">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="a83ab-148">ウィザードのプレビュー ペインでは、マトリックスのデザインを完了する前にデータのグループ化の結果を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-148">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups-and-choose-a-layout-and-style"></a><span data-ttu-id="a83ab-149">データをグループにまとめてレイアウトとスタイルを選択するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-149">To organize data into groups and choose a layout and style</span></span>  
  
1.  <span data-ttu-id="a83ab-150">**[フィールドの配置]** ページで、 **[使用できるフィールド]** から Territory を **[行グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-150">On the **Arrange fields** page, drag Territory from **Available fields** to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="a83ab-151">SalesDate を **[行グループ]** にドラッグして Territory の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-151">Drag SalesDate to **Row groups** and place it below Territory.</span></span>  
  
     <span data-ttu-id="a83ab-152">**[行グループ]** 内でフィールドが表示される順序によって、グループの階層が決まります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-152">The order in which fields are listed in **Row groups** defines the group hierarchy.</span></span> <span data-ttu-id="a83ab-153">手順 1. および 2. で、フィールドの値がまず販売区域でまとめられ、次に販売日でまとめられます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-153">Steps 1 and 2 organize the values of the fields first by territory, and then by sales date.</span></span>  
  
3.  <span data-ttu-id="a83ab-154">Subcategory を **[列グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-154">Drag Subcategory to **Column groups**.</span></span>  
  
4.  <span data-ttu-id="a83ab-155">Product を [**列グループ]** にドラッグし、[サブカテゴリ] の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-155">Drag Product to **Column groups,** and then place below Subcategory.</span></span>  
  
     <span data-ttu-id="a83ab-156">[**列グループ**] に表示されるフィールドの順序によって、グループの階層が定義されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-156">The order in which fields are listed in **Column groups** defines the group hierarchy.</span></span>  
  
     <span data-ttu-id="a83ab-157">手順 3. および 4. で、フィールドの値がまずサブカテゴリでまとめられ、次に製品でまとめられます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-157">Steps 3 and 4 organize the values for the fields first by subcategory, and then by product.</span></span>  
  
5.  <span data-ttu-id="a83ab-158">Sales を **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-158">Drag Sales to **Values**.</span></span>  
  
     <span data-ttu-id="a83ab-159">Sales は Sum 関数 (数値フィールドを集計するための既定の関数) を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-159">Sales is summarized with the Sum function, the default function to summarize numeric fields.</span></span>  
  
6.  <span data-ttu-id="a83ab-160">Quantity を **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-160">Drag Quantity to **Values**.</span></span>  
  
     <span data-ttu-id="a83ab-161">Quantity は Sum 関数を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-161">Quantity is summarized with the Sum function.</span></span>  
  
     <span data-ttu-id="a83ab-162">手順 5. および 6. で、マトリックスのデータ セルに表示するデータが指定されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-162">Steps 5 and 6 specify the data to display in the matrix data cells.</span></span>  
  
7.  <span data-ttu-id="a83ab-163">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-163">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="a83ab-164">[レイアウトの選択] ページの **[オプション]** で、 **[小計と総計を表示]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-164">On the Choose the Layout page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
9. <span data-ttu-id="a83ab-165">**[ブロック、小計は下]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-165">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
10. <span data-ttu-id="a83ab-166">**[グループの展開/折りたたみ]** チェック ボックスがオンであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-166">Verify the option **Expand/collapse groups** is selected.</span></span>  
  
11. <span data-ttu-id="a83ab-167">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-167">Click **Next**.</span></span>  
  
12. <span data-ttu-id="a83ab-168">[スタイルの選択] ページの スタイル ペインで、 **[スレート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-168">On the Choose a Style page, in the Styles pane, select **Slate**.</span></span>  
  
13. <span data-ttu-id="a83ab-169">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-169">Click **Finish**.</span></span>  
  
     <span data-ttu-id="a83ab-170">マトリックスがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-170">The matrix is added to the design surface.</span></span> <span data-ttu-id="a83ab-171">行グループ ペインには、Territory と SalesDate の 2 つの行グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-171">The Row Groups pane shows two row groups: Territory and SalesDate.</span></span> <span data-ttu-id="a83ab-172">列グループ ペインには、Subcategory と Product の 2 つの行グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-172">The Column Groups pane shows two column groups: Subcategory and Product.</span></span> <span data-ttu-id="a83ab-173">詳細データは、データセット クエリによって取得されるすべてのデータです。</span><span class="sxs-lookup"><span data-stu-id="a83ab-173">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
14. <span data-ttu-id="a83ab-174">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-174">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="a83ab-175">マトリックスには、特定の日付に販売された製品ごとに、製品のサブカテゴリと販売区域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-175">For each product that is sold on a specific date, the matrix shows the subcategory to which the product belongs and the territory of the sales.</span></span>  
  
##  <a name="3-format-data"></a><a name="FormatData"></a><span data-ttu-id="a83ab-176">3. データの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="a83ab-176">3. Format Data</span></span>  
 <span data-ttu-id="a83ab-177">既定では Sales フィールドの概要データでは通常の数値が、SalesDate フィールドには日付と時刻の両方の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-177">By default, the summary data for the Sales field displays a general number and the SalesDate field displays both date and time information.</span></span> <span data-ttu-id="a83ab-178">書式を設定して Sales フィールドでは数値が通貨として表示されるようにし、SalesDate フィールドでは日付のみが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-178">Format the Sales field to display the number as currency and the SalesDate field to display only the date.</span></span> <span data-ttu-id="a83ab-179">書式設定したテキスト ボックスおよびプレースホルダー テキストのサンプル値を表示するには、 **[プレースホルダーのスタイル]** の設定を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-179">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-fields"></a><span data-ttu-id="a83ab-180">フィールドの書式を設定するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-180">To format fields</span></span>  
  
1.  <span data-ttu-id="a83ab-181">デザインビューに切り替えるには、[**デザイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-181">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="a83ab-182">Ctrl&lt;/localizedText&gt; キーを押しながら、 `[Sum(Sales)]`が格納されている 9 つのセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-182">Press the Ctrl key, and then select the nine cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="a83ab-183">**[ホーム]** タブの **[数値]** グループで、 **[通貨]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-183">On the **Home** tab, in the **Number** group, click **Currency**.</span></span> <span data-ttu-id="a83ab-184">セルの表示が、通貨の書式に変更されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-184">The cells changeto show the formatted currency.</span></span>  
  
     <span data-ttu-id="a83ab-185">地域設定が英語 (米国) の場合、既定のサンプル テキストは [**$12,345.00**] です。</span><span class="sxs-lookup"><span data-stu-id="a83ab-185">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="a83ab-186">通貨値の例が表示されない場合は、[**数値**] グループの [**プレースホルダーのスタイル**] をクリックし、[**サンプルの値**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-186">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="a83ab-187">`[SalesDate]`が格納されたセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-187">Click the cell that contains `[SalesDate]`.</span></span>  
  
5.  <span data-ttu-id="a83ab-188">[**数値**] グループで、ドロップダウンリストから [**日付**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-188">In the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="a83ab-189">セルに、日付の例として **[2000/1/31]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-189">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="a83ab-190">日付の例が表示されない場合は、 **[数値]** グループの **[プレースホルダーのスタイル]** をクリックし、 **[サンプルの値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-190">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
6.  <span data-ttu-id="a83ab-191">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-191">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="a83ab-192">日付値には日付のみが表示され、売上の値は通貨として表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-192">The date values display only dates and the sales values display as currency.</span></span>  
  
##  <a name="4-add-adjacent-column-group"></a><a name="AdjacentGroup"></a><span data-ttu-id="a83ab-193">4. 隣接する列グループを追加する</span><span class="sxs-lookup"><span data-stu-id="a83ab-193">4. Add Adjacent Column Group</span></span>  
 <span data-ttu-id="a83ab-194">行グループと列グループは親子リレーションシップを使用して入れ子にしたり、兄弟リレーションシップを使用して隣接させたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-194">You can nest row and column groups in parent child relationships or adjacent in sibling relationships.</span></span>  
  
 <span data-ttu-id="a83ab-195">Subcategory 列グループに隣接する列グループを追加し、セルをコピーして新しい列グループに値を設定し、式を使用して列グループ ヘッダーの値を作成します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-195">Add a column group that is adjacent to the Subcategory column group, copy cells to populate the new column group, and then use an expression to create the value of the column group header.</span></span>  
  
#### <a name="to-add-an-adjacent-column-group"></a><span data-ttu-id="a83ab-196">隣接する列グループを追加するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-196">To add an adjacent column group</span></span>  
  
1.  <span data-ttu-id="a83ab-197">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-197">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a83ab-198">`[Subcategory]`を格納しているセルを右クリックし、 **[グループの追加]** をポイントして **[右に隣接]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-198">Right-click the cell that contains `[Subcategory]`, point to **Add Group**, and then click **Adjacent Right**.</span></span>  
  
     <span data-ttu-id="a83ab-199">**[Tablix のグループ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-199">The **Tablix Group** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="a83ab-200">**[グループ化]** ボックスの一覧で [SalesDate] を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-200">In the **Group By** list, select SalesDate, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a83ab-201">Subcategory 列グループの左側に新しい列グループが追加されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-201">A new column group is added to the left of the Subcategory column group.</span></span>  
  
4.  <span data-ttu-id="a83ab-202">新しい列グループで `[SalesDate],` を格納しているセルを右クリックして、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-202">Right-click the cell in the new column group that contains `[SalesDate],` and then click **Expression**.</span></span>  
  
5.  <span data-ttu-id="a83ab-203">[式] ボックスに次の式をコピーします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-203">Copy the following expression to expression box.</span></span>  
  
    ```  
    =WeekdayName(DatePart("w",Fields!SalesDate.Value))  
    ```  
  
     <span data-ttu-id="a83ab-204">この式により、販売日から曜日が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-204">This expression extracts the weekday name from the sales date.</span></span> <span data-ttu-id="a83ab-205">詳細については、「[式 (レポート ビルダーおよび SSRS)](report-design/expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a83ab-205">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="a83ab-206">Subcategory 列グループで Total を格納しているセルを右クリックして、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-206">Right-click the cell in the Subcategory column group that contains Total, and then click **Copy**.</span></span>  
  
7.  <span data-ttu-id="a83ab-207">手順 5. で作成した式が格納されているセルの直下のセルを右クリックして、 **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-207">Right-click the cell immediately below the cell that contains the expression you created in step 5 and click **Paste**.</span></span>  
  
8.  <span data-ttu-id="a83ab-208">Ctrl&lt;/localizedText&gt; キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-208">Press the Ctrl key.</span></span>  
  
9. <span data-ttu-id="a83ab-209">Subcategory グループで Sales 列ヘッダーとその下の 3 つのセルをクリックして右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-209">In the Subcategory group, click the Sales column header and the three cells below it, right-click, and then click **Copy**.</span></span>  
  
10. <span data-ttu-id="a83ab-210">この 4 つのセルを新しい列グループの 4 つの空のセルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-210">Paste the four cells into the four empty cells in the new column group.</span></span>  
  
11. <span data-ttu-id="a83ab-211">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-211">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="a83ab-212">レポートには、月曜日と火曜日という名前の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-212">The report includes columns named Monday and Tuesday.</span></span> <span data-ttu-id="a83ab-213">データセットには、この 2 つの曜日のデータのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a83ab-213">The dataset contains only data for these two days.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a83ab-214">他の曜日のデータが含まれている場合は、レポートにそれらの曜日の列も表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-214">If the data included other days, the report would include columns for them as well.</span></span> <span data-ttu-id="a83ab-215">各列には、列ヘッダー、 `Sales` 、および区域ごとの売上合計が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a83ab-215">Each column has the column header, `Sales`, and sales totals by territory.</span></span>  
  
##  <a name="5-change-column-widths"></a><a name="Width"></a><span data-ttu-id="a83ab-216">5. 列幅を変更する</span><span class="sxs-lookup"><span data-stu-id="a83ab-216">5. Change Column Widths</span></span>  
 <span data-ttu-id="a83ab-217">通常、マトリックスを含むレポートは、実行すると、水平方向と垂直方向に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-217">A report that includes a matrix typically expands horizontally as well as vertically when it runs.</span></span> <span data-ttu-id="a83ab-218">水平方向の拡張の制御は、印刷レポートに使用される Microsoft Word や Adobe PDF などの形式にレポートをエクスポートする場合、特に重要です。</span><span class="sxs-lookup"><span data-stu-id="a83ab-218">Controlling horizontal expansion is particularly important if you plan to export the report to formats such as Microsoft Word or Adobe PDF that are used for printed reports.</span></span> <span data-ttu-id="a83ab-219">レポートが複数のページにまたがって水平方向に拡張される場合、印刷レポートは理解しにくくなります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-219">If the report expands horizontally across multiple pages, the printed report is difficult to understand.</span></span> <span data-ttu-id="a83ab-220">水平方向の拡張を最小限に抑えるには、列のサイズを変更して、折り返しをしないでデータを表示できるだけの幅にします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-220">To minimize horizontal expansion, you can resize columns to be only the width necessary to display the data without wrapping.</span></span> <span data-ttu-id="a83ab-221">また、列の名前を変更して、タイトルがデータの表示に必要な幅に収まるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-221">You can also rename columns so that their titles fit the width needed to display the data.</span></span>  
  
#### <a name="to-rename-and-resize-the-columns"></a><span data-ttu-id="a83ab-222">列の名前とサイズを変更するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-222">To rename and resize the columns</span></span>  
  
1.  <span data-ttu-id="a83ab-223">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-223">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a83ab-224">一番左にある Quantity 列のテキストを選択して、「 **QTY**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-224">Select the text in the furthest Quantity column to the left, and then type **QTY**.</span></span>  
  
     <span data-ttu-id="a83ab-225">列のタイトルが、QTY になります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-225">The column title is now QTY.</span></span>  
  
3.  <span data-ttu-id="a83ab-226">その他の Quantity 列についても、手順 2. を実行します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-226">Repeat step 2 for the other columns named Quantity.</span></span> <span data-ttu-id="a83ab-227">このような列は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-227">There are two of them.</span></span>  
  
4.  <span data-ttu-id="a83ab-228">マトリックスをクリックし、列ハンドルおよび行ハンドルをマトリックスの上部および横に表示します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-228">Click the matrix so that column and row handles appear above and next to the matrix.</span></span>  
  
     <span data-ttu-id="a83ab-229">テーブルの上と横のグレーのバーは、列および行ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="a83ab-229">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
5.  <span data-ttu-id="a83ab-230">一番左にある QTY 列のサイズを変更するには、列ハンドルの間の罫線をポイントします。カーソルが 2 方向の矢印の形状に変化します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-230">To resize the furthest QTY column to the left, point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="a83ab-231">列を左にドラッグして、幅を 1/2 インチにします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-231">Drag the column towards the left until it is 1/2 inch wide.</span></span>  
  
     <span data-ttu-id="a83ab-232">幅が 1/2 インチの列であれば、数量を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-232">A column width of 1/2 inch is adequate to display the quantity.</span></span>  
  
6.  <span data-ttu-id="a83ab-233">その他の QTY 列についても、手順 5. を実行します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-233">Repeat step 5 for the other columns named QTY.</span></span>  
  
7.  <span data-ttu-id="a83ab-234">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-234">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="a83ab-235">数量を表示するレポート内の列は、名前が QTY になり、幅が狭くなりました。</span><span class="sxs-lookup"><span data-stu-id="a83ab-235">The columns in the report that contains quantities are now named QTY and the columns are narrower.</span></span>  
  
##  <a name="6-merge-matrix-cells"></a><a name="MergeCells"></a><span data-ttu-id="a83ab-236">6. マトリックスセルを結合する</span><span class="sxs-lookup"><span data-stu-id="a83ab-236">6. Merge Matrix Cells</span></span>  
 <span data-ttu-id="a83ab-237">コーナー領域は、マトリックスの左上隅にあります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-237">The corner area is in the upper left corner of the matrix.</span></span> <span data-ttu-id="a83ab-238">マトリックス内の行グループと列グループの数に応じて、コーナー領域にセル数は変わります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-238">Depending on the number of row and column groups in the matrix, the number of cells in the corner area varies.</span></span> <span data-ttu-id="a83ab-239">このチュートリアルで作成するマトリックスには、コーナー領域に 4 つのセルがあります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-239">The matrix, built in this tutorial, has four cells in its corner area.</span></span> <span data-ttu-id="a83ab-240">これらのセルは、行グループと列グループの階層の深さに対応して、2 行 2 列で表示されています。</span><span class="sxs-lookup"><span data-stu-id="a83ab-240">The cells are arranged in two rows and two columns, reflecting the depth of row and column group hierarchies.</span></span> <span data-ttu-id="a83ab-241">これらの 4 つのセルはこのレポートでは使用されないので、結合して 1 つのセルにします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-241">The four cells are not used in this report and you will merge them into one.</span></span>  
  
#### <a name="to-merge-matrix-cells"></a><span data-ttu-id="a83ab-242">マトリックス セルを結合するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-242">To merge matrix cells</span></span>  
  
1.  <span data-ttu-id="a83ab-243">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-243">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a83ab-244">マトリックスをクリックし、列ハンドルおよび行ハンドルをマトリックスの上部および横に表示します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-244">Click the matrix so that column and row handles appear above and next to the matrix.</span></span>  
  
3.  <span data-ttu-id="a83ab-245">Ctrl&lt;/localizedText&gt; キーを押しながら、4 つのコーナー セルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-245">Press the Ctrl key, and then select the four corner cells.</span></span>  
  
4.  <span data-ttu-id="a83ab-246">セルを右クリックし、[**セルの結合**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-246">Right-click the cells and then click **Merge Cells**.</span></span>  
  
5.  <span data-ttu-id="a83ab-247">コーナーセルを右クリックし、[**テキストボックスのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-247">Right-click the corner cell, and then click **Text Box Properties**.</span></span>  
  
6.  <span data-ttu-id="a83ab-248">**[塗りつぶし]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-248">Click the **Fill** tab.</span></span>  
  
7.  <span data-ttu-id="a83ab-249">**塗りつぶしの色**として [(***fx***)] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-249">Click the (***fx***) button for **Fill color**.</span></span>  
  
8.  <span data-ttu-id="a83ab-250">次の式をコピーして、[式] ボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-250">Copy and paste the following expression in the expression box.</span></span>  
  
    ```  
    #96a4b2  
    ```  
  
     <span data-ttu-id="a83ab-251">これは、"スレート" スタイルで使用される青灰色を表す RGB の 16 進数値です。</span><span class="sxs-lookup"><span data-stu-id="a83ab-251">This is the RGB hex value for a gray blue color used in the Slate style.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="a83ab-252">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-252">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="a83ab-253">上隅のマトリックスは単一のセルになり、行グループおよび列グループのセルと同じ色が適用されています。</span><span class="sxs-lookup"><span data-stu-id="a83ab-253">The upper corner matrix is a single cell and has the same color as the row group and column group cells.</span></span>  
  
##  <a name="7-add-a-report-header-and-report-title"></a><a name="HeaderTitle"></a><span data-ttu-id="a83ab-254">7. レポートヘッダーとレポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="a83ab-254">7. Add a Report Header and Report Title</span></span>  
 <span data-ttu-id="a83ab-255">レポート タイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-255">A report title appears at the top of the report.</span></span> <span data-ttu-id="a83ab-256">レポート ヘッダーがあれば、そこにレポート タイトルを配置します。レポート ヘッダーを使用しない場合は、レポート本文の一番上のテキスト ボックスに配置します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-256">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="a83ab-257">このチュートリアルでは、レポートの一番上に配置されているテキスト ボックスを削除し、ヘッダーにタイトルを追加します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-257">In this tutorial, you will remove the text box at the top of the report and add a title to the header.</span></span>  
  
#### <a name="to-add-a-report-header-and-report-title"></a><span data-ttu-id="a83ab-258">レポート ヘッダーおよびレポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-258">To add a report header and report title</span></span>  
  
1.  <span data-ttu-id="a83ab-259">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-259">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a83ab-260">**[タイトルの追加] を**含むレポート本文の上部にあるテキストボックスをクリックし、del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-260">Click the text box at the top of the report body that contains **Click to add title**, and then press the Delete key.</span></span>  
  
3.  <span data-ttu-id="a83ab-261">リボンの [**挿入**] タブで、[**ヘッダー** ] をクリックし、[**ヘッダーの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-261">On the **Insert** tab of the ribbon, click **Header** and then click **Add Header**.</span></span>  
  
     <span data-ttu-id="a83ab-262">ヘッダーがレポート本文の先頭に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-262">A header is added to the top of the report body.</span></span>  
  
4.  <span data-ttu-id="a83ab-263">**[挿入]** タブの **[テキスト ボックス]** をクリックし、テキスト ボックスをレポート ヘッダーの内側にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-263">On the **Insert** tab, click **Text Box**, and then drag a text box inside the report header.</span></span> <span data-ttu-id="a83ab-264">テキスト ボックスのサイズをおおよそ横 6 インチ、縦 3/4 インチにして、レポート ヘッダーの左側に配置します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-264">Make the text box about 6 inches long and 3/4 inch tall and place it on the left side of the report header.</span></span>  
  
5.  <span data-ttu-id="a83ab-265">テキスト ボックスに「 **Territory、Subcategory、および Day ごとの売上**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-265">In the text box, type **Sales by Territory, Subcategory, and Day**.</span></span>  
  
6.  <span data-ttu-id="a83ab-266">入力したテキストを選択して右クリックし、[**テキストのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-266">Select the text you typed, right-click, and then click **Text Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a83ab-267">複数の文字の書式を同時に設定するには、文字が連続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-267">To format characters at the same time, they must be contiguous.</span></span>  
  
7.  <span data-ttu-id="a83ab-268">[**テキストのプロパティ**] ダイアログボックスで、[**フォント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-268">In the **Text Properties** dialog box, click **Font**.</span></span>  
  
8.  <span data-ttu-id="a83ab-269">[**フォント**] ボックスの一覧で、[ **Times New Roman**] を選択します。[**サイズ**] で [ **24 pt**] を選択し、[**色**] で [**茶色**] を選択し、[**スタイル**] で [**斜体**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-269">In the **Font** list, select **Times New Roman**; in **Size** select **24 pt**, in **Color** select **Maroon**, and in **Style** select **Italic**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="a83ab-270">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-270">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="a83ab-271">レポートのレポート ヘッダーにレポート タイトルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-271">The report includes a report title in the report header.</span></span>  
  
##  <a name="8-save-the-report"></a><a name="Save"></a><span data-ttu-id="a83ab-272">8. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="a83ab-272">8. Save the Report</span></span>  
 <span data-ttu-id="a83ab-273">レポートは、レポート サーバー、SharePoint ライブラリ、またはコンピューターに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-273">You can save reports to a report server, SharePoint library, or your computer.</span></span>  
  
 <span data-ttu-id="a83ab-274">このチュートリアルでは、レポートをレポート サーバーに保存します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-274">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="a83ab-275">レポート サーバーにアクセスできない場合は、レポートをコンピューターに保存してください。</span><span class="sxs-lookup"><span data-stu-id="a83ab-275">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="a83ab-276">レポート サーバーにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-276">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="a83ab-277">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-277">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="a83ab-278">**[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-278">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="a83ab-279">レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-279">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="a83ab-280">"レポート サーバーに接続しています" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-280">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="a83ab-281">接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-281">When the connection is complete, you will see the contents of the report folder that the report server administrator specified as the default report location.</span></span>  
  
4.  <span data-ttu-id="a83ab-282">**[名前]** に表示されている既定の名前を「 **SalesByTerritorySubcategory**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-282">In **Name**, replace the default name with **SalesByTerritorySubcategory**.</span></span>  
  
5.  <span data-ttu-id="a83ab-283">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-283">Click **Save**.</span></span>  
  
 <span data-ttu-id="a83ab-284">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-284">The report is saved to the report server.</span></span> <span data-ttu-id="a83ab-285">接続しているレポート サーバーの名前がウィンドウ下部のステータス バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-285">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="a83ab-286">コンピューターにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="a83ab-286">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="a83ab-287">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-287">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="a83ab-288">**[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、レポートを保存するフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-288">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="a83ab-289">**[名前]** に表示されている既定の名前を「 **SalesByTerritorySubcategory**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-289">In **Name**, replace the default name with **SalesByTerritorySubcategory**.</span></span>  
  
4.  <span data-ttu-id="a83ab-290">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-290">Click **Save**.</span></span>  
  
##  <a name="9-optional-rotate-text-box-270-degrees"></a><a name="RotateTextBox"></a><span data-ttu-id="a83ab-291">9. (省略可能) テキストボックスを270度回転させる</span><span class="sxs-lookup"><span data-stu-id="a83ab-291">9. (Optional) Rotate Text Box 270 Degrees</span></span>  
 <span data-ttu-id="a83ab-292">マトリックスを含むレポートは、実行すると、水平方向と垂直方向に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-292">A report with matrices can expand horizontally and vertically when it runs.</span></span> <span data-ttu-id="a83ab-293">テキストボックスを垂直方向に、つまり 270 度回転させると、水平方向のスペースを節約できます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-293">By rotating text boxes vertically, or 270 degrees, you can save horizontal space.</span></span> <span data-ttu-id="a83ab-294">表示レポートの幅は狭くなり、Microsoft Word などの形式にエクスポートした場合は、印刷ページ内に収まる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-294">The rendered report is then narrower and if exported to a format such as Microsoft Word, will be more likely to fit on a printed page.</span></span>  
  
 <span data-ttu-id="a83ab-295">テキスト ボックスでも、テキストを水平方向または垂直方向 (上から下) に表示できます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-295">A text box can also display text as horizontal, vertical (top to bottom).</span></span> <span data-ttu-id="a83ab-296">詳細については、「[テキスト ボックス (レポート ビルダーおよび SSRS)](report-design/text-boxes-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a83ab-296">For more information, see [Text Boxes &#40;Report Builder and SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-rotate-text-box-270-degrees"></a><span data-ttu-id="a83ab-297">テキスト ボックスを 270 度回転させるには</span><span class="sxs-lookup"><span data-stu-id="a83ab-297">To rotate text box 270 degrees</span></span>  
  
1.  <span data-ttu-id="a83ab-298">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-298">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a83ab-299">`[Territory].` が格納されたセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-299">Click the cell that contains `[Territory].`</span></span>  
  
3.  <span data-ttu-id="a83ab-300">[プロパティ] ペインで、[WritingMode] プロパティを探し、ドロップダウンリストから [ **Rotate270**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-300">In the Properties pane, locate the WritingMode property and in its drop-down list, select **Rotate270**.</span></span>  
  
     <span data-ttu-id="a83ab-301">[プロパティ] ペインが表示されていない場合は、リボンの **[表示]** タブの **[プロパティ]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-301">If the Properties pane is not open, click the **View** tab of the ribbon, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="a83ab-302">CanGrow プロパティがに設定されていることを確認し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-302">Verify that the CanGrow property is set to `True`.</span></span>  
  
5.  <span data-ttu-id="a83ab-303">Territory 列の幅を 1/2 インチに変更して、列タイトルを削除します。</span><span class="sxs-lookup"><span data-stu-id="a83ab-303">Resize the Territory column to be 1/2 inch wide and delete the column title.</span></span>  
  
6.  <span data-ttu-id="a83ab-304">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a83ab-304">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="a83ab-305">販売区域名が垂直方向 (上から下) に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a83ab-305">The territory name is written vertically, bottom to top.</span></span> <span data-ttu-id="a83ab-306">Territory 行グループの高さは、販売区域名の長さによって変わります。</span><span class="sxs-lookup"><span data-stu-id="a83ab-306">The height of the Territory row group varies by the length of the territory name.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a83ab-307">次の手順</span><span class="sxs-lookup"><span data-stu-id="a83ab-307">Next Steps</span></span>  
 <span data-ttu-id="a83ab-308">これで、マトリックス レポートを作成する方法のチュートリアルは終了です。</span><span class="sxs-lookup"><span data-stu-id="a83ab-308">This concludes the tutorial for how to create a matrix report.</span></span> <span data-ttu-id="a83ab-309">マトリックスの詳細については、「[テーブル、マトリックス、および一覧 &#40;レポートビルダーと ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)、[マトリックス &#40;レポートビルダーと ssrs&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md)、 [tablix データ領域の領域 &#40;レポートビルダーと Ssrs&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md)、 [tablix データ領域のセル、行、および列](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)&#40;レポートビルダー&#41; と ssrs」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a83ab-309">For more information about matrices, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Matrices &#40;Report Builder and SSRS&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md), [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a83ab-310">参照</span><span class="sxs-lookup"><span data-stu-id="a83ab-310">See Also</span></span>  
 <span data-ttu-id="a83ab-311">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="a83ab-311">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="a83ab-312">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="a83ab-312">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
