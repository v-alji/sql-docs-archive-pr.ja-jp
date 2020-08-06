---
title: チュートリアル:自由形式のレポートの作成 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 515b0d2566efa4e11216a28648338c7ec43f3950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737837"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a><span data-ttu-id="863d9-102">チュートリアル:自由形式のレポートの作成 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="863d9-102">Tutorial: Creating a Free Form Report (Report Builder)</span></span>
  <span data-ttu-id="863d9-103">このチュートリアルでは、フォーム レターのような SSRS 自由形式レポートを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="863d9-103">This tutorial teaches you how to create an SSRS free form report that resembles a forms letter.</span></span> <span data-ttu-id="863d9-104">レポート アイテムを配置して、テキスト ボックス、画像、その他のデータ領域が含まれるフォームを作成できます。</span><span class="sxs-lookup"><span data-stu-id="863d9-104">You can arrange report items to create a form with text boxes, images and other data regions.</span></span>

 <span data-ttu-id="863d9-105">このチュートリアルで作成するレポートは、このチュートリアルに含まれているサンプルの売上データに基づいています。</span><span class="sxs-lookup"><span data-stu-id="863d9-105">The report you create in this tutorial is based on sample sales data that is included in the tutorial.</span></span> <span data-ttu-id="863d9-106">このレポートでは、販売区域ごとに情報をまとめて、各区域の販売責任者の名前と売上情報の概要を表示します。</span><span class="sxs-lookup"><span data-stu-id="863d9-106">The report groups information by territory and displays the name of the sales manager for the territory as well as detailed and summary sales information.</span></span> <span data-ttu-id="863d9-107">自由形式レポートでは、一覧データ領域を基盤として使用し、画像を使用した装飾用のパネル、データが挿入された静的テキスト、詳細情報を表示するテーブル、および必要に応じて概要情報を表示する円グラフと縦棒グラフを追加します。</span><span class="sxs-lookup"><span data-stu-id="863d9-107">You will use the list data region as the foundation for the free form report, and then add a decorative panel with an image, static text with data inserted, a table to show detailed information, and optionally, pie and column charts to display summary information.</span></span>

##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="863d9-108">学習内容</span><span class="sxs-lookup"><span data-stu-id="863d9-108">What You Will Learn</span></span>
 <span data-ttu-id="863d9-109">このチュートリアルでは、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="863d9-109">In this tutorial, you will learn how to do the following:</span></span>

-   [<span data-ttu-id="863d9-110">空のレポート、データ ソース、およびデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="863d9-110">Create a Blank Report, Data Source, and Dataset</span></span>](#BlankReport)

-   [<span data-ttu-id="863d9-111">一覧を追加および構成する</span><span class="sxs-lookup"><span data-stu-id="863d9-111">Add and Configure a List</span></span>](#List)

-   [<span data-ttu-id="863d9-112">グラフィックスを追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-112">Add Graphics</span></span>](#Graphics)

-   [<span data-ttu-id="863d9-113">自由形式テキストを追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-113">Add Free Form Text</span></span>](#Text)

-   [<span data-ttu-id="863d9-114">詳細情報を表示するテーブルを追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-114">Add a Table to Show Details</span></span>](#Table)

-   [<span data-ttu-id="863d9-115">データの書式設定</span><span class="sxs-lookup"><span data-stu-id="863d9-115">Format Data</span></span>](#Format)

-   [<span data-ttu-id="863d9-116">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="863d9-116">Save the Report</span></span>](#Save)

### <a name="other-optional-steps"></a><span data-ttu-id="863d9-117">その他のオプションの手順</span><span class="sxs-lookup"><span data-stu-id="863d9-117">Other Optional Steps</span></span>

-   [<span data-ttu-id="863d9-118">レポートの領域を区切る罫線を追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-118">Add a Line to Separate Areas of Report</span></span>](#Line)

-   [<span data-ttu-id="863d9-119">概要データのビジュアル表現を追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-119">Add Summary Data Visualization</span></span>](#Visualization)

 <span data-ttu-id="863d9-120">このチュートリアルの推定所要時間 : 20 分</span><span class="sxs-lookup"><span data-stu-id="863d9-120">Estimated time to complete this tutorial: 20 minutes.</span></span>

## <a name="requirements"></a><span data-ttu-id="863d9-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="863d9-121">Requirements</span></span>
 <span data-ttu-id="863d9-122">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="863d9-122">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>

##  <a name="1-create-a-blank-report-data-source-and-dataset"></a><a name="BlankReport"></a><span data-ttu-id="863d9-123">1. 空のレポート、データソース、およびデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="863d9-123">1. Create a Blank Report, Data Source, and Dataset</span></span>

> [!NOTE]
>  <span data-ttu-id="863d9-124">このチュートリアルでは、レポートが外部のデータ ソースを必要としないように、クエリにデータ値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="863d9-124">In this tutorial, the query contains the data values so that the report does not need an external data source.</span></span> <span data-ttu-id="863d9-125">この種の内部データは学習に使用する目的に役立ちますが、そのためクエリが長くなっています。</span><span class="sxs-lookup"><span data-stu-id="863d9-125">The use of this type of internal data is great for learning purposes, but the approach makes the query long.</span></span> <span data-ttu-id="863d9-126">.</span><span class="sxs-lookup"><span data-stu-id="863d9-126">.</span></span>

#### <a name="to-create-a-blank-report"></a><span data-ttu-id="863d9-127">空のレポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="863d9-127">To create a blank report</span></span>

1.  <span data-ttu-id="863d9-128">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-128">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="863d9-129">**[作業の開始]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-129">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="863d9-130">表示されない場合は、レポート ビルダーのボタンの **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-130">If it does not, from the Report Builder button, click **New**.</span></span>

2.  <span data-ttu-id="863d9-131">**[作業の開始]** ダイアログ ボックスの左ペインで **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="863d9-131">In the left pane of the **Getting Started** dialog box, verify that **New Report** is selected.</span></span>

3.  <span data-ttu-id="863d9-132">右ペインで、 **[空のレポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-132">In the right pane, click **Blank Report**.</span></span>

#### <a name="to-create-a-new-data-source"></a><span data-ttu-id="863d9-133">新しいデータ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="863d9-133">To create a new data source</span></span>

1.  <span data-ttu-id="863d9-134">レポートデータペインで、[**新規作成**] をクリックし、[**データソース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-134">In the Report Data pane, click **New**, and then click **Data Source**.</span></span>

2.  <span data-ttu-id="863d9-135">ボックスに「 `Name` **listdatasource** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-135">In the `Name` box, type: **ListDataSource**</span></span>

3.  <span data-ttu-id="863d9-136">**[レポートに埋め込まれた接続を使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-136">Click **Use a connection embedded in my report**.</span></span>

4.  <span data-ttu-id="863d9-137">接続の種類が Microsoft SQL Server であることを確認し、[**接続文字列**] ボックスに「 **Data \<servername> Source =** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-137">Verify that the connection type is Microsoft SQL Server, and then in the **Connection string** box type: **Data Source = \<servername>**</span></span>

     <span data-ttu-id="863d9-138">\<servername>たとえば、Report001 などは、SQL Server データベースエンジンのインスタンスがインストールされているコンピューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="863d9-138">\<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="863d9-139">レポート データは SQL Server のデータベースから抽出されるのではないので、データベース名を含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="863d9-139">Because the report data is not extracted from a SQL Server database, you need not include the name of a database.</span></span> <span data-ttu-id="863d9-140">指定したサーバー上の既定のデータベースを使用して、クエリが解析されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-140">The default database on the specified server is used to parse the query.</span></span>

5.  <span data-ttu-id="863d9-141">**[資格情報]** をクリックし、SQL Server データベース エンジンのインスタンスとの接続に必要な資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-141">Click **Credentials**, and enter the credentials needed to connect to the instance of the SQL Server Database Engine.</span></span>

6.  <span data-ttu-id="863d9-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-142">Click **OK**.</span></span>

#### <a name="to-create-a-new-dataset"></a><span data-ttu-id="863d9-143">新しいデータセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="863d9-143">To create a new dataset</span></span>

1.  <span data-ttu-id="863d9-144">レポートデータペインで、[**新規作成**] をクリックし、[**データセット**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-144">In the Report Data pane, click **New**, and then click **Dataset**.</span></span>

2.  <span data-ttu-id="863d9-145">ボックスに「 `Name` Listdataset」と入力し**ます。**</span><span class="sxs-lookup"><span data-stu-id="863d9-145">In the `Name` box, type: **ListDataset.**</span></span>

3.  <span data-ttu-id="863d9-146">**[レポートに埋め込まれたデータセットを使用します]** をクリックし、データ ソースが **ListDataSource**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="863d9-146">Click **Use a dataset embedded in my report**, and verify that the data source is **ListDataSource**.</span></span>

4.  <span data-ttu-id="863d9-147">クエリの種類に **[テキスト]** が選択されていることを確認してから、 **[クエリ デザイナー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-147">Verify that the **Text** query type is selected, and then click **Query Designer**.</span></span>

5.  <span data-ttu-id="863d9-148">**[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-148">Click **Edit as Text**.</span></span>

6.  <span data-ttu-id="863d9-149">次のクエリをコピーし、クエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="863d9-149">Copy and paste the following query into the query pane:</span></span>

    ```
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity
    ```

7.  <span data-ttu-id="863d9-150">[実行] アイコンをクリックしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="863d9-150">Click Run icon to run the query.</span></span>

     <span data-ttu-id="863d9-151">クエリの結果が、レポートに表示できるデータになります。</span><span class="sxs-lookup"><span data-stu-id="863d9-151">The query results are the data available to display in your report.</span></span>

     <span data-ttu-id="863d9-152">![クエリ デザイナー](../../2014/tutorials/media/tutorial-querydesigner.png "クエリ デザイナー")</span><span class="sxs-lookup"><span data-stu-id="863d9-152">![Query Designer](../../2014/tutorials/media/tutorial-querydesigner.png "Query Designer")</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

##  <a name="2-add-and-configure-a-list"></a><a name="List"></a><span data-ttu-id="863d9-153">2. 一覧を追加および構成する</span><span class="sxs-lookup"><span data-stu-id="863d9-153">2. Add and Configure a List</span></span>
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="863d9-154">には、テーブル、マトリックス、リストという 3 つのデータ領域テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="863d9-154">provides three data region templates: table, matrix, and list.</span></span> <span data-ttu-id="863d9-155">これらのテンプレートはすべて、tablix データ領域に基づいています。</span><span class="sxs-lookup"><span data-stu-id="863d9-155">These templates are all based on a tablix data region.</span></span>

 <span data-ttu-id="863d9-156">このチュートリアルでは、リストを使用して、ニュースレターのようなレポートに、販売区域の販売情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="863d9-156">In this tutorial, you will use a list to display the sales information for sales territories in a report that resembles a newsletter.</span></span> <span data-ttu-id="863d9-157">情報は、区域ごとにグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-157">The information is grouped by territory.</span></span> <span data-ttu-id="863d9-158">区域ごとのデータをグループ化する新しい行グループを追加し、組み込みの詳細行グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="863d9-158">You will add a new row group that groups data by territory, and then delete the built-in Details row group.</span></span> <span data-ttu-id="863d9-159">リスト テンプレートは、自由形式レポートを作成するのに最適です。</span><span class="sxs-lookup"><span data-stu-id="863d9-159">The list template is ideal for creating free form reports.</span></span> <span data-ttu-id="863d9-160">詳細については、「 [&#40;レポートビルダーと SSRS&#41;の一覧](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="863d9-160">For more information, see [Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="863d9-161">このレポートでは、用紙サイズを Letter (8.5 X11) にし、余白を 1 インチとします。</span><span class="sxs-lookup"><span data-stu-id="863d9-161">This report uses the paper size Letter (8.5 X11) and 1 inch margins.</span></span> <span data-ttu-id="863d9-162">縦が 9 インチまたは横が 6 1/2 インチよりも大きいレポート ページでは、空のページが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="863d9-162">A report page taller than 9 inches or wider than 6 1/2 inches might generate blank pages.</span></span>

#### <a name="to-add-a-list"></a><span data-ttu-id="863d9-163">一覧を追加するには</span><span class="sxs-lookup"><span data-stu-id="863d9-163">To add a list</span></span>

1.  <span data-ttu-id="863d9-164">リボンの **[挿入]** タブの **[データ領域]** で **[一覧]** をクリックし、レポート本文内に一覧をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-164">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **List** and then drag the list inside the report body.</span></span> <span data-ttu-id="863d9-165">リストの高さを 7 インチ、幅を 6.25 インチにします。</span><span class="sxs-lookup"><span data-stu-id="863d9-165">Make the list 7 inches tall and 6.25 inches wide.</span></span>

2.  <span data-ttu-id="863d9-166">一覧内をクリックし、一覧の先頭を右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-166">Click inside the list, right-click the top of the list, and then click **Tablix Properties**.</span></span>

     <span data-ttu-id="863d9-167">![一覧の追加](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "一覧の追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-167">![Adding list](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "Adding list")</span></span>

3.  <span data-ttu-id="863d9-168">**[データセット名]** ドロップダウン リストの **[ListDataset]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-168">In the **Dataset name** drop-down list, select **ListDataset**.</span></span>

4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

5.  <span data-ttu-id="863d9-169">一覧内を右クリックし、 **[四角形のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-169">Right-click inside the list, and then click **Rectangle Properties**.</span></span>

     <span data-ttu-id="863d9-170">![四角形のプロパティのコマンド](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "四角形のプロパティのコマンド")</span><span class="sxs-lookup"><span data-stu-id="863d9-170">![Rectangle Properties command](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "Rectangle Properties command")</span></span>

6.  <span data-ttu-id="863d9-171">**[全般]** タブで **[後に改ページを追加する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="863d9-171">On the **General** tab, select the **Add a page break after** checkbox.</span></span>

7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

#### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a><span data-ttu-id="863d9-172">新しい行グループを追加し、詳細グループを削除するには</span><span class="sxs-lookup"><span data-stu-id="863d9-172">To add a new row group and to delete the Details group</span></span>

1.  <span data-ttu-id="863d9-173">行グループ ペインで、詳細グループを右クリックし、 **[グループの追加]** をポイントして **[親グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-173">In the Row Groups pane, right-click the Details group, point to **Add Group**, and then click **Parent Group**.</span></span>

     <span data-ttu-id="863d9-174">![親グループ コマンド](../../2014/tutorials/media/tutorial-parentgroupcommand.png "親グループ コマンド")</span><span class="sxs-lookup"><span data-stu-id="863d9-174">![Parent Group command](../../2014/tutorials/media/tutorial-parentgroupcommand.png "Parent Group command")</span></span>

2.  <span data-ttu-id="863d9-175">ドロップダウン リストの `[Territory].` を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-175">In the drop-down list, select `[Territory].`</span></span>

3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="863d9-176">一覧に列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-176">A column is added to the list.</span></span> <span data-ttu-id="863d9-177">この列には、`[Territory].` セルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-177">The column contains the cell `[Territory].`</span></span>

4.  <span data-ttu-id="863d9-178">一覧の Territory 列を右クリックし、 **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-178">Right-click the Territory column in the list, and then click **Delete Columns**.</span></span>

     <span data-ttu-id="863d9-179">![列の削除](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "[列の削除]")</span><span class="sxs-lookup"><span data-stu-id="863d9-179">![Delete columns](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "Delete columns")</span></span>

5.  <span data-ttu-id="863d9-180">**[列のみの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-180">Click **Delete Columns only**.</span></span>

     <span data-ttu-id="863d9-181">![[列の削除] ダイアログボックス](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "[列の削除] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="863d9-181">![Delete Columns dialog box](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "Delete Columns dialog box")</span></span>

6.  <span data-ttu-id="863d9-182">行グループ ペインで、 **[詳細]** グループを右クリックし、 **[グループの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-182">In the Row Groups pane, right-click the **Details** group, and then click **Delete Group**.</span></span>

     <span data-ttu-id="863d9-183">![詳細グループの削除](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "詳細グループの削除")</span><span class="sxs-lookup"><span data-stu-id="863d9-183">![Delete Details Group](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "Delete Details Group")</span></span>

7.  <span data-ttu-id="863d9-184">**[グループのみを削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-184">Click **Delete Group only**.</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

##  <a name="3-add-graphics"></a><a name="Graphics"></a><span data-ttu-id="863d9-185">3. グラフィックスを追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-185">3. Add Graphics</span></span>
 <span data-ttu-id="863d9-186">一覧データ領域を使用する利点の 1 つは、表形式のレイアウトに制限されずに、四角形やテキスト ボックスなどのレポート アイテムをどこにでも追加できることです。</span><span class="sxs-lookup"><span data-stu-id="863d9-186">One of the advantages of using a list data region is that you can add report items such as rectangles and text boxes anywhere, instead of being limited to a tabular layout.</span></span> <span data-ttu-id="863d9-187">ここでは、グラフィック (任意の色で塗りつぶされた四角形) を追加して、レポートの体裁を整えます。</span><span class="sxs-lookup"><span data-stu-id="863d9-187">You will enhance the appearance of the report by adding a graphic (a rectangle filled with a color).</span></span>

#### <a name="to-add-graphic-elements-to-the-report"></a><span data-ttu-id="863d9-188">レポートにグラフィック要素を追加するには</span><span class="sxs-lookup"><span data-stu-id="863d9-188">To add graphic elements to the report</span></span>

1.  <span data-ttu-id="863d9-189">リボンの [**挿入**] タブで、[**四角形**] をクリックし、一覧の左上隅に四角形をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-189">On the **Insert** tab of the ribbon, click **Rectangle**,and then drag a rectangle to the upper left corner of the list.</span></span> <span data-ttu-id="863d9-190">四角形のサイズを縦 7 インチ、横 1 インチにします。</span><span class="sxs-lookup"><span data-stu-id="863d9-190">Make the rectangle 7 inches tall and 1 inch wide.</span></span>

2.  <span data-ttu-id="863d9-191">四角形を右クリックし、 **[四角形のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-191">Right-click the rectangle, and then click **Rectangle Properties**.</span></span>

3.  <span data-ttu-id="863d9-192">**[塗りつぶし]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-192">Click the **Fill** tab.</span></span>

4.  <span data-ttu-id="863d9-193">**[塗りつぶしの色]** ドロップ ダウン リストの **[その他の色]** をクリックし、 **[濃い灰色]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-193">In the **Fill color** drop-down list, click **More Colors**, and then select the **DarkGray** color.</span></span>

     <span data-ttu-id="863d9-194">![塗りつぶしの色の選択](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "塗りつぶしの色の選択")</span><span class="sxs-lookup"><span data-stu-id="863d9-194">![Select fill color](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "Select fill color")</span></span>

5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

6.  <span data-ttu-id="863d9-195">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="863d9-195">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="863d9-196">レポートの左側に、ダーク グレー色の四角形からなる縦長のグラフィックが追加されています。</span><span class="sxs-lookup"><span data-stu-id="863d9-196">The left side of the report now has vertical graphic that consists of a dark gray rectangle.</span></span>

##  <a name="4-add-free-form-text"></a><a name="Text"></a><span data-ttu-id="863d9-197">4. 自由形式のテキストを追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-197">4. Add Free Form Text</span></span>
 <span data-ttu-id="863d9-198">テキスト ボックスには、各レポート ページに繰り返し表示される静的テキストとデータ フィールドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="863d9-198">A text box contains static text that is repeated on each report page as well as data fields.</span></span>

#### <a name="to-add-text-to-the-report"></a><span data-ttu-id="863d9-199">テキストをレポートに追加するには</span><span class="sxs-lookup"><span data-stu-id="863d9-199">To add text to the report</span></span>

1.  <span data-ttu-id="863d9-200">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="863d9-200">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="863d9-201">リボンの **[挿入]** タブにある **[テキスト ボックス]** をクリックし、一覧の左上隅、以前追加した四角形の内部にテキスト ボックスをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-201">On the **Insert** tab of the ribbon, click **Text Box**, and then drag a text box to the upper left corner of the list, but inside of the rectangle you added previously.</span></span> <span data-ttu-id="863d9-202">テキスト ボックスのサイズを縦 3 インチ、横 5 インチにします。</span><span class="sxs-lookup"><span data-stu-id="863d9-202">Make the text box about 3 inches tall and 5 inches wide.</span></span>

3.  <span data-ttu-id="863d9-203">テキスト ボックスの上部にカーソルを置き、「 **ニュースレター:** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-203">Place the cursor in the upper part of the text box, and then type: **Newsletter for** .</span></span>

     <span data-ttu-id="863d9-204">![ニュースレターの見出しテキストの追加](../../2014/tutorials/media/tutorial-newsletterfor.png "ニュースレターの見出しテキストの追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-204">![Add newsletter heading text](../../2014/tutorials/media/tutorial-newsletterfor.png "Add newsletter heading text")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="863d9-205">for の後に必ずスペースを入れてください。</span><span class="sxs-lookup"><span data-stu-id="863d9-205">Be sure to include the extra space after the word "for".</span></span> <span data-ttu-id="863d9-206">このスペースによって、入力したテキストと次の手順で追加するフィールドが分けられます。</span><span class="sxs-lookup"><span data-stu-id="863d9-206">The space separates the text and the field that you will add in the next step.</span></span>

4.  <span data-ttu-id="863d9-207">Territory フィールドをテキスト ボックスにドラッグし、手順 3. で入力したテキストの後に配置します。</span><span class="sxs-lookup"><span data-stu-id="863d9-207">Drag the Territory field to the text box and place it after the text you typed in step 3.</span></span>

     <span data-ttu-id="863d9-208">![Territorial フィールドの追加](../../2014/tutorials/media/tutorial-addterritorialfield.png "Territorial フィールドの追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-208">![Add Territorial field](../../2014/tutorials/media/tutorial-addterritorialfield.png "Add Territorial field")</span></span>

5.  <span data-ttu-id="863d9-209">すべてのテキストを選択して右クリックし、 **[テキストのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-209">Select all text, right-click, and then click **Text Properties**.</span></span>

6.  <span data-ttu-id="863d9-210">**[フォント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-210">Click the **Font** tab.</span></span>

7.  <span data-ttu-id="863d9-211">**[フォント]** ボックスの一覧の **[Times New Roman]**、 **[サイズ]** ボックスの一覧の **[20 pt]**、および **[色]** ボックスの一覧の **[赤]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-211">In the **Font** list, select **Times New Roman**; in **Size** select **20 pt**, in **Color** select **Red**.</span></span>

     <span data-ttu-id="863d9-212">![テキストのプロパティ](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "[テキストのプロパティ]")</span><span class="sxs-lookup"><span data-stu-id="863d9-212">![Text Properties](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "Text Properties")</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

9. <span data-ttu-id="863d9-213">手順 3. で入力したテキストの下にカーソルを置き、「 **Hello** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-213">Place the cursor below the text you typed in step 3 and type: **Hello** .</span></span>

    > [!NOTE]
    >  <span data-ttu-id="863d9-214">「Hello」の後に必ずスペースを入れてください。</span><span class="sxs-lookup"><span data-stu-id="863d9-214">Be sure to include the extra space after the word "Hello".</span></span> <span data-ttu-id="863d9-215">このスペースによって、入力したテキストと次の手順で追加するフィールドが分けられます。</span><span class="sxs-lookup"><span data-stu-id="863d9-215">The space separates the text and the field that you will add in the next step.</span></span>

10. <span data-ttu-id="863d9-216">FullName フィールドをテキスト ボックスにドラッグして、手順 9. で入力したテキストの後に配置し、コンマ (,) を入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-216">Drag the FullName field to the text box and place it after the text you typed in step 9, and then type a comma (,).</span></span>

     <span data-ttu-id="863d9-217">![氏名フィールドの追加](../../2014/tutorials/media/tutorial-addfullnamefield.png "氏名フィールドの追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-217">![Add Full Name field](../../2014/tutorials/media/tutorial-addfullnamefield.png "Add Full Name field")</span></span>

11. <span data-ttu-id="863d9-218">手順 9. および 10. で追加したテキストを選択して右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-218">Select the text you added in steps 9 and 10, right-click, and then click **Text Properties**.</span></span>

12. <span data-ttu-id="863d9-219">**[フォント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-219">Click the **Font** tab.</span></span>

13. <span data-ttu-id="863d9-220">**[フォント]** ボックスの一覧の **[Times New Roman]**、 **[サイズ]** ボックスの一覧の **[16 pt]**、および **[色]** ボックスの一覧の **[黒]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-220">In the **Font** list, select **Times New Roman**; in **Size** select **16 pt**, in **Color** select **Black** color.</span></span>

14. [!INCLUDE[clickOK](../includes/clickok-md.md)]

15. <span data-ttu-id="863d9-221">手順 9. ～ 13. で追加したテキストの下にカーソルを置き、次の "意味不明" のテキストをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="863d9-221">Place the cursor below the text you added in steps 9 through 13, and then copy and paste the following "greeked" text:</span></span>

    ```
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque. 
    Nulla facilisi. Proin ligula enim, porta ut tincidunt id, adipiscing sit amet eros. Ut purus sem, bibendum et vulputate sit amet, facilisis eget magna. Sed aliquam erat non erat eleifend hendrerit. Ut a ligula est, sit amet eleifend enim. Ut et nisl enim, sit amet adipiscing augue. Vivamus eu arcu ac libero posuere elementum. Integer condimentum bibendum venenatis. Integer odio tellus, feugiat in pellentesque semper, interdum nec sem. Sed cursus euismod sem, ut elementum sapien placerat vel. 
    ```

16. <span data-ttu-id="863d9-222">手順 15. で追加したテキストを選択して右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-222">Select the text you added in steps 15, right-click, and then click **Text Properties**.</span></span>

17. <span data-ttu-id="863d9-223">**[フォント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-223">Click the **Font** tab.</span></span>

18. <span data-ttu-id="863d9-224">**[フォント]** ボックスの一覧の **[Arial]**、 **[サイズ]** ボックスの一覧の **[10 pt]**、および **[色]** ボックスの一覧の **[黒]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-224">In the **Font** list, select **Arial**; in **Size** select **10 pt**, in **Color** select **Black**.</span></span>

19. [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="863d9-225">![ニュースレター テキストの追加](../../2014/tutorials/media/tutorial-newslettertext.png "ニュースレター テキストの追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-225">![Add newsletter text](../../2014/tutorials/media/tutorial-newslettertext.png "Add newsletter text")</span></span>

20. <span data-ttu-id="863d9-226">手順 15. で貼り付けたテキストの下にカーソルを置き、「 **売上合計:** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-226">Place the cursor below the text you pasted in step 15, and then type: **Congratulations on your total sales of** .</span></span>

    > [!NOTE]
    >  <span data-ttu-id="863d9-227">of の後に必ずスペースを入れてください。</span><span class="sxs-lookup"><span data-stu-id="863d9-227">Be sure to include the extra space after the word "of".</span></span> <span data-ttu-id="863d9-228">このスペースによって、入力したテキストと次の手順で追加するフィールドが分けられます。</span><span class="sxs-lookup"><span data-stu-id="863d9-228">The space separates the text and the field that you will add in the next step.</span></span>

21. <span data-ttu-id="863d9-229">Sales フィールドをテキスト ボックスにドラッグして、手順 20. で入力したテキストの後に配置し、感嘆符 (!) を入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-229">Drag the Sales field to the text box, place it after the text you typed in step 20, and then type an exclamation mark (!).</span></span>

22. <span data-ttu-id="863d9-230">Sales フィールドを強調表示し、フィールドを右クリックして、[**式**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-230">Highlight the Sales field, right-click the field, and then click **Expression**.</span></span>

23. <span data-ttu-id="863d9-231">[式] ボックスの式を変更して、次のように Sum 関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="863d9-231">In the expression box, change the expression to include the Sum function as follows:</span></span>

    ```
    =Sum(Fields!Sales.value)
    ```

24. [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="863d9-232">![Sales フィールドへの式の追加](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "Sales フィールドへの式の追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-232">![Add an expression to sales field](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "Add an expression to sales field")</span></span>

25. <span data-ttu-id="863d9-233">手順 20. ～ 23. で追加したテキストを選択して右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-233">Select the text you added in steps 20 through 23, right-click, and then click **Text Properties**.</span></span>

26. <span data-ttu-id="863d9-234">**[フォント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-234">Click the **Font** tab.</span></span>

27. <span data-ttu-id="863d9-235">**[フォント]** ボックスの一覧の **[Times New Roman]**、 **[サイズ]** ボックスの一覧の **[16 pt]**、および **[色]** ボックスの一覧の **[赤]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-235">In the **Font** list, select **Times New Roman**; in **Size** select **16 pt**, in **Color** select **Red**.</span></span>

28. [!INCLUDE[clickOK](../includes/clickok-md.md)]

29. <span data-ttu-id="863d9-236">`[Sum(Sales)]` を選択し、 **[ホーム]** タブの **[数値]** グループで、 **[通貨]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-236">Select `[Sum(Sales)]` and on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>

     <span data-ttu-id="863d9-237">![通貨記号の追加](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "通貨記号の追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-237">![Add currency symbol](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "Add currency symbol")</span></span>

30. <span data-ttu-id="863d9-238">"クリックしてタイトルを追加" というテキストが含まれているテキスト ボックスを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-238">Right-click the text box with the "Click to add title" text, and then click **Delete**.</span></span>

31. <span data-ttu-id="863d9-239">リスト ボックスを選択し、方向キーを使用して、リスト ボックスをページの先頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="863d9-239">Select the list box and using the arrow keys, move it to the top of the page.</span></span>

32. <span data-ttu-id="863d9-240">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="863d9-240">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="863d9-241">レポートに静的テキストが表示され、各レポート ページには特定の販売区域についてのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="863d9-241">The report displays static text and each report page includes data that pertains to a territory.</span></span> <span data-ttu-id="863d9-242">売上には通貨の書式が適用されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-242">Sales are formatted as currency.</span></span>

 <span data-ttu-id="863d9-243">![ニュースレターのプレビュー](../../2014/tutorials/media/tutorial-newsletters.png "ニュースレターのプレビュー")</span><span class="sxs-lookup"><span data-stu-id="863d9-243">![Preview of Newsletter](../../2014/tutorials/media/tutorial-newsletters.png "Preview of Newsletter")</span></span>

##  <a name="5-add-a-table-to-show-sales-details"></a><a name="Table"></a><span data-ttu-id="863d9-244">5. 売上の詳細を表示するテーブルを追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-244">5. Add a Table to Show Sales Details</span></span>
 <span data-ttu-id="863d9-245">テーブルまたはマトリックスの新規作成ウィザードを使用して、自由形式レポートにテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="863d9-245">Use the New Table and Matrix Wizard to add a table to the free form report.</span></span> <span data-ttu-id="863d9-246">ウィザードの完了後、合計を表示する行を手動で追加します。</span><span class="sxs-lookup"><span data-stu-id="863d9-246">After you complete the wizard, you will manually add a row for totals.</span></span>

#### <a name="to-add-a-table"></a><span data-ttu-id="863d9-247">テーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="863d9-247">To add a table</span></span>

1.  <span data-ttu-id="863d9-248">リボンの **[挿入]** タブの **[データ領域]** で **[テーブル]** をクリックし、 **[テーブル ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-248">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **Table**, and then click **Table Wizard**.</span></span>

2.  <span data-ttu-id="863d9-249">[データセットの選択] ページで、 **[ListDataset]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-249">On the Choose a dataset page, click **ListDataset**.</span></span>

3.  <span data-ttu-id="863d9-250">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-250">Click **Next**.</span></span>

4.  <span data-ttu-id="863d9-251">**[フィールドの配置]** ページで、 **[使用できるフィールド]** から Product フィールドを **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-251">On the **Arrange fields** page, drag the Product field from **Available fields** to **Values.**</span></span>

5.  <span data-ttu-id="863d9-252">SalesDate、Quantity、および Sales についても、手順 4. を実行します。</span><span class="sxs-lookup"><span data-stu-id="863d9-252">Repeat step 4, for SalesDate, Quantity, and Sales.</span></span> <span data-ttu-id="863d9-253">Product の下に SalesDate を、SalesDate の下に Quantity を、SalesDate の下に Sales を配置します。</span><span class="sxs-lookup"><span data-stu-id="863d9-253">Place SalesDate below Product, Quantity below SalesDate, and Sales below SalesDate.</span></span>

6.  <span data-ttu-id="863d9-254">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-254">Click **Next**.</span></span>

7.  <span data-ttu-id="863d9-255">**[レイアウトの選択]** ページで、テーブルのレイアウトを確認します。</span><span class="sxs-lookup"><span data-stu-id="863d9-255">On the **Choose the layout** page, view the layout of the table.</span></span>

     <span data-ttu-id="863d9-256">テーブルはごく単純です。</span><span class="sxs-lookup"><span data-stu-id="863d9-256">The table is very simple.</span></span> <span data-ttu-id="863d9-257">5 つの列から成り、行グループや列グループは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="863d9-257">It consists of five columns and has no row or column groups.</span></span> <span data-ttu-id="863d9-258">グループがないため、グループに関連するレイアウト オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="863d9-258">Because it has no groups, the layout options related to groups, are not available.</span></span> <span data-ttu-id="863d9-259">このチュートリアルでは後ほど、テーブルを手動で更新して合計が表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="863d9-259">You will manually update the table to include a total later in the tutorial.</span></span>

8.  <span data-ttu-id="863d9-260">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-260">Click **Next**.</span></span>

9. <span data-ttu-id="863d9-261">**[スタイルの選択]** ページの **スタイル** ペインで、 **[スレート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-261">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

10. <span data-ttu-id="863d9-262">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-262">Click **Finish**.</span></span>

11. <span data-ttu-id="863d9-263">テーブルをレッスン 4 で追加したテキスト ボックスの下にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-263">Drag the table to below the text box that you added in lesson 4.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="863d9-264">テーブルが一覧内に配置されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="863d9-264">Make sure the table is inside the list.</span></span>

12. <span data-ttu-id="863d9-265">テーブルが選択されていることを確認してから、行グループ ペインで詳細を右クリックし、 **[合計の追加]** をポイントして **[後]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-265">Confirmed that the table is selected, then in the Row Group pane right-click Details, point to **Add Total**, and then click **After**.</span></span>

     <span data-ttu-id="863d9-266">![レポート合計の追加](../../2014/tutorials/media/tutorial-addtotal.png "レポート合計の追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-266">![Add report total](../../2014/tutorials/media/tutorial-addtotal.png "Add report total")</span></span>

13. <span data-ttu-id="863d9-267">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="863d9-267">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="863d9-268">レポートに、売上の詳細情報と合計が入力されたテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-268">The report displays a table with sales details and totals.</span></span>

 <span data-ttu-id="863d9-269">![レポート内の売上合計](../../2014/tutorials/media/tutorial-reportsalestotals.png "レポート内の売上合計")</span><span class="sxs-lookup"><span data-stu-id="863d9-269">![Sales totals in report](../../2014/tutorials/media/tutorial-reportsalestotals.png "Sales totals in report")</span></span>

##  <a name="6-format-data"></a><a name="Format"></a><span data-ttu-id="863d9-270">6. データの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="863d9-270">6. Format Data</span></span>
 <span data-ttu-id="863d9-271">数値データの書式を通貨にし、日付の書式を日付と時刻のみに設定します。</span><span class="sxs-lookup"><span data-stu-id="863d9-271">Format numeric data as currency and dates as day and time only.</span></span>

#### <a name="to-format-fields-table"></a><span data-ttu-id="863d9-272">フィールド テーブルの書式を設定するには</span><span class="sxs-lookup"><span data-stu-id="863d9-272">To format fields table</span></span>

1.  <span data-ttu-id="863d9-273">デザインビューに切り替えるには、[**デザイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-273">Click **Design** to switch to design view.</span></span>

2.  <span data-ttu-id="863d9-274">`[Sum(SalesSales)]` が格納されているテーブルのセルをクリックし、 **[ホーム]** タブの **[数値]** グループで、 **[通貨]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-274">Click the table cells that contain `[Sum(SalesSales)]` and on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>

     <span data-ttu-id="863d9-275">![通貨記号を追加して売上を合計する](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "通貨記号を追加して売上を合計する")</span><span class="sxs-lookup"><span data-stu-id="863d9-275">![Add currency symbol to sum sales](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "Add currency symbol to sum sales")</span></span>

3.  <span data-ttu-id="863d9-276">`[SalesDate]` が格納されているセルをクリックし、 **[数値]** グループで、ドロップダウン リストから **[日付]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-276">Click the cell that contains `[SalesDate]` and in the **Number** group, from the drop-down list, select **Date**.</span></span>

4.  <span data-ttu-id="863d9-277">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="863d9-277">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="863d9-278">レポートには書式が設定されたデータが表示され、読みやすくなりました。</span><span class="sxs-lookup"><span data-stu-id="863d9-278">The report now displays formatted data and is easier to read.</span></span>

 <span data-ttu-id="863d9-279">![レポートでの売上合計の書式設定](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "レポートでの売上合計の書式設定")</span><span class="sxs-lookup"><span data-stu-id="863d9-279">![Format sales totals in report](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "Format sales totals in report")</span></span>

##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="863d9-280">7. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="863d9-280">7. Save the Report</span></span>
 <span data-ttu-id="863d9-281">レポートは、レポート サーバー、SharePoint ライブラリ、またはコンピューターに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="863d9-281">You can save reports to a report server, SharePoint library, or your computer.</span></span> <span data-ttu-id="863d9-282">また、レポートは Word や PDF など各種形式にエクスポートできます。そのためには、レポートを実行し、[ **エクスポート** ] メニューから形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-282">You can also export the report to a variety of formats such as Word and PDF, by running the report and selecting the format from the **Export** menu.</span></span>

 <span data-ttu-id="863d9-283">このチュートリアルでは、レポートをレポート サーバーに保存します。</span><span class="sxs-lookup"><span data-stu-id="863d9-283">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="863d9-284">レポート サーバーにアクセスできない場合は、レポートをコンピューターに保存してください。</span><span class="sxs-lookup"><span data-stu-id="863d9-284">If you do not have access to a report server, save the report to your computer.</span></span>

#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="863d9-285">レポート サーバーにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="863d9-285">To save the report on a report server</span></span>

1.  <span data-ttu-id="863d9-286">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-286">From the **Report Builder** button, click **Save As**.</span></span>

2.  <span data-ttu-id="863d9-287">**[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-287">Click **Recent Sites and Servers**.</span></span>

3.  <span data-ttu-id="863d9-288">レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-288">Select or type the name of the report server where you have permission to save reports.</span></span>

     <span data-ttu-id="863d9-289">"レポート サーバーに接続しています" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-289">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="863d9-290">接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-290">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>

4.  <span data-ttu-id="863d9-291">で `Name` 、既定の名前を「 **Salesinformationbyterritory**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="863d9-291">In `Name`, replace the default name with **SalesInformationByTerritory**.</span></span>

5.  <span data-ttu-id="863d9-292">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-292">Click **Save**.</span></span>

 <span data-ttu-id="863d9-293">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-293">The report is saved to the report server.</span></span> <span data-ttu-id="863d9-294">接続しているレポート サーバーの名前がウィンドウ下部のステータス バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-294">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>

#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="863d9-295">コンピューターにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="863d9-295">To save the report on your computer</span></span>

1.  <span data-ttu-id="863d9-296">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-296">From the **Report Builder** button, click **Save As**.</span></span>

2.  <span data-ttu-id="863d9-297">**[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、レポートを保存するフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="863d9-297">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>

3.  <span data-ttu-id="863d9-298">で `Name` 、既定の名前を「 **Salesinformationbyterritory**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="863d9-298">In `Name`, replace the default name with **SalesInformationByTerritory**.</span></span>

4.  <span data-ttu-id="863d9-299">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-299">Click **Save**.</span></span>

##  <a name="8-optional-add-a-line-to-separate-areas-of-the-report"></a><a name="Line"></a><span data-ttu-id="863d9-300">8. (省略可能) レポートの領域を区切る線を追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-300">8. (Optional) Add a Line to Separate Areas of the Report</span></span>
 <span data-ttu-id="863d9-301">レポートの編集領域と詳細領域を区切る線を追加します。</span><span class="sxs-lookup"><span data-stu-id="863d9-301">Add a line to separate the editorial and details areas of the report.</span></span>

#### <a name="to-add-a-line"></a><span data-ttu-id="863d9-302">罫線を追加するには</span><span class="sxs-lookup"><span data-stu-id="863d9-302">To add a line</span></span>

1.  <span data-ttu-id="863d9-303">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="863d9-303">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="863d9-304">リボンの **[挿入]** タブの **[レポート アイテム]** で、 **[線]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-304">On the **Insert** tab of the ribbon, in the **Report Items** area, click **Line.**</span></span>

3.  <span data-ttu-id="863d9-305">レッスン 4 で追加した自由形式のテキスト ボックスの下に線を引きます。</span><span class="sxs-lookup"><span data-stu-id="863d9-305">Draw a line below the free form text box you added in lesson 4.</span></span>

4.  <span data-ttu-id="863d9-306">線をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-306">Click the line.</span></span>

5.  <span data-ttu-id="863d9-307">**[ホーム]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-307">Click the **Home** tab.</span></span>

6.  <span data-ttu-id="863d9-308">**[罫線]** の領域で幅を **[4 1/2]** pt に、色を **[赤]** に指定します。</span><span class="sxs-lookup"><span data-stu-id="863d9-308">In the **Border** area, for width select **4 1/2** pt and for color, for color select **Red**.</span></span>

     <span data-ttu-id="863d9-309">![レポートに罫線を追加](../../2014/tutorials/media/tutorial-reportwithline.png "レポートに罫線を追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-309">![Add line to report](../../2014/tutorials/media/tutorial-reportwithline.png "Add line to report")</span></span>

##  <a name="9-optional-add-summary-data-visualization"></a><a name="Visualization"></a><span data-ttu-id="863d9-310">9. (省略可能) 概要データの視覚化を追加する</span><span class="sxs-lookup"><span data-stu-id="863d9-310">9. (Optional) Add Summary Data Visualization</span></span>
 <span data-ttu-id="863d9-311">四角形を利用して、レポートの表示方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="863d9-311">Rectangles help you control how the report renders.</span></span> <span data-ttu-id="863d9-312">四角形の内側に円グラフや縦棒グラフを配置することで、レポートを思いどおりに表示できます。</span><span class="sxs-lookup"><span data-stu-id="863d9-312">Place a pie and column chart inside a rectangle to ensure that the report renders the way you want.</span></span>

#### <a name="to-add-a-rectangle"></a><span data-ttu-id="863d9-313">四角形を追加するには</span><span class="sxs-lookup"><span data-stu-id="863d9-313">To add a rectangle</span></span>

1.  <span data-ttu-id="863d9-314">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="863d9-314">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="863d9-315">リボンの **[挿入]** タブの **[レポート アイテム]** で **[四角形]** をクリックし、一覧内でテーブルの右側に四角形をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-315">On the **Insert** tab of the ribbon, in the **Report Items** area click **Rectangle**, and then drag the rectangle inside the list, to the right of the table.</span></span> <span data-ttu-id="863d9-316">四角形のサイズを横 2 インチ、縦 4 インチにします。</span><span class="sxs-lookup"><span data-stu-id="863d9-316">Make the rectangle 2 inches wide and 4 inches tall.</span></span>

3.  <span data-ttu-id="863d9-317">四角形とテーブルの上部を揃えます。</span><span class="sxs-lookup"><span data-stu-id="863d9-317">Align the tops of the rectangle and the table.</span></span>

#### <a name="to-add-a-pie-chart"></a><span data-ttu-id="863d9-318">円グラフを追加するには</span><span class="sxs-lookup"><span data-stu-id="863d9-318">To add a pie chart</span></span>

1.  <span data-ttu-id="863d9-319">リボンの **[挿入]** タブの **[データの視覚エフェクト]** で **[グラフ]** をクリックし、 **[グラフ ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-319">On the **Insert** tab of the ribbon, in the **Data Visualizations** area, click **Chart,** and then click **Chart Wizard**.</span></span>

2.  <span data-ttu-id="863d9-320">[データセットの選択] ページで、 **[ListDataset]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-320">On the Choose a dataset page, click **ListDataset**, and then click **Next**.</span></span>

3.  <span data-ttu-id="863d9-321">**[円]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-321">Click **Pie**, and then click **Next**.</span></span>

4.  <span data-ttu-id="863d9-322">[グラフのフィールドの配置] ページで、Product を **[カテゴリ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-322">On the arrange chart fields page, drag Product to **Categories**.</span></span>

5.  <span data-ttu-id="863d9-323">Quantity を [**値**] にドラッグし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-323">Drag Quantity to **Values**, and then click **Next**.</span></span>

6.  <span data-ttu-id="863d9-324">**[スタイルの選択]** ページの **スタイル** ペインで、 **[スレート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-324">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

7.  <span data-ttu-id="863d9-325">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-325">Click **Finish**.</span></span>

8.  <span data-ttu-id="863d9-326">レポートの左上隅に表示されているグラフのサイズを変更し、縦 1 1/2 インチ、横 2 インチにします。</span><span class="sxs-lookup"><span data-stu-id="863d9-326">Resize the chart that appears in the upper left corner of the report, to be 1 1/2 inches tall and 2 inches wide.</span></span>

9. <span data-ttu-id="863d9-327">四角形の内側にグラフをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-327">Drag the chart inside the rectangle.</span></span>

     <span data-ttu-id="863d9-328">![円グラフの追加](../../2014/tutorials/media/tutorial-addpiechart.png "円グラフの追加")</span><span class="sxs-lookup"><span data-stu-id="863d9-328">![Add pie chart](../../2014/tutorials/media/tutorial-addpiechart.png "Add pie chart")</span></span>

10. <span data-ttu-id="863d9-329">グラフのタイトルを右クリックし、 **[タイトルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-329">Right-click the chart title, and then click **Title Properties**.</span></span>

11. <span data-ttu-id="863d9-330">**[グラフのタイトルのプロパティ]** ダイアログ ボックスの [タイトル] ボックスに、「 **製品の売上数量**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-330">In the **Chart Title Properties** dialog box, in Title text, type: **Product Quantities Sold**.</span></span>

12. <span data-ttu-id="863d9-331">**[フォント]** タブで、 **[サイズ]** ボックスの一覧の **[10 pt]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-331">Click the **Font** tab, and in the **Size** list, click **10pt**.</span></span>

13. [!INCLUDE[clickOK](../includes/clickok-md.md)]

#### <a name="to-add-a-column-chart"></a><span data-ttu-id="863d9-332">縦棒グラフを追加するには</span><span class="sxs-lookup"><span data-stu-id="863d9-332">To add a column chart</span></span>

1.  <span data-ttu-id="863d9-333">リボンの **[挿入]** タブの **[データの視覚エフェクト]** で **[グラフ]** をクリックし、 **[グラフ ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-333">On the **Insert** tab of the ribbon, in the **Data Visualizations** area, click **Chart,** and then click **Chart Wizard**.</span></span>

2.  <span data-ttu-id="863d9-334">**[データセットの選択]** ページで、 **[ListDataset]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-334">On the **Choose a dataset** page, click **ListDataset**, and then click **Next**.</span></span>

3.  <span data-ttu-id="863d9-335">**[列]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-335">Click **Column**, and then click **Next**.</span></span>

4.  <span data-ttu-id="863d9-336">[グラフのフィールドの配置] ページで、Product フィールドを [**カテゴリ**] にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-336">On the arrange chart fields page, drag the Product field to **Categories**.</span></span>

5.  <span data-ttu-id="863d9-337">Sales を **[値]** にドラッグして、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-337">Drag Sales to **Values,** and then click **Next**.</span></span>

     <span data-ttu-id="863d9-338">値は縦軸に表示されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-338">Values display on the vertical axis.</span></span>

6.  <span data-ttu-id="863d9-339">**[スタイルの選択]** ページの **スタイル** ペインで、 **[スレート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="863d9-339">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

7.  <span data-ttu-id="863d9-340">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-340">Click **Finish**.</span></span>

     <span data-ttu-id="863d9-341">縦棒グラフがレポートの左上隅に追加されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-341">A column chart is added to the upper left corner of the report.</span></span>

8.  <span data-ttu-id="863d9-342">グラフのサイズを横 2 インチ、縦 2 インチに変更します。</span><span class="sxs-lookup"><span data-stu-id="863d9-342">Resize the chart to be 2 inches wide and 2 inches tall.</span></span>

9. <span data-ttu-id="863d9-343">四角形の内側で円グラフの下にグラフをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="863d9-343">Drag the chart inside the rectangle, below the pie chart.</span></span>

     <span data-ttu-id="863d9-344">![縦棒グラフを追加する](../../2014/tutorials/media/tutorial-addcolumnchart.png "縦棒グラフを追加する")</span><span class="sxs-lookup"><span data-stu-id="863d9-344">![Add column chart](../../2014/tutorials/media/tutorial-addcolumnchart.png "Add column chart")</span></span>

10. <span data-ttu-id="863d9-345">グラフのタイトルを右クリックし、[**タイトルのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-345">Right-click the chart title and then click **Title Properties**.</span></span>

11. <span data-ttu-id="863d9-346">**[グラフのタイトルのプロパティ]** ダイアログ ボックスの [タイトル] ボックスに、「 **Product Sales**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="863d9-346">In the **Chart Title Properties** dialog box, in Title text, type: **Product Sales**.</span></span>

12. <span data-ttu-id="863d9-347">**[フォント]** タブで、 **[サイズ]** ボックスの一覧の **[10pt]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-347">Click the **Font** tab, and in the **Size** list click **10pt**, and then click **OK**.</span></span>

13. <span data-ttu-id="863d9-348">縦棒グラフで、縦軸を右クリックし、 **[軸のタイトルの表示]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="863d9-348">In the column chart, right click the vertical axis, and then deselect **Show Axis Title**.</span></span>

14. <span data-ttu-id="863d9-349">横軸についても、手順 13. 繰り返します。</span><span class="sxs-lookup"><span data-stu-id="863d9-349">Repeat step 13 for the horizontal axis.</span></span>

15. <span data-ttu-id="863d9-350">凡例を右クリックして **[凡例の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-350">Right click the legend, and then click **Delete Legend**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="863d9-351">軸のタイトルと凡例を削除すると、グラフのサイズが小さい場合に、グラフが見やすくなります。</span><span class="sxs-lookup"><span data-stu-id="863d9-351">Removing axis titles and the legend makes the chart more readable when it is a small size.</span></span>

 <span data-ttu-id="863d9-352">![グラフのタイトルを変更し、軸のタイトルを削除する](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "グラフのタイトルを変更し、軸のタイトルを削除する")</span><span class="sxs-lookup"><span data-stu-id="863d9-352">![Change chart titles and remove axis title](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "Change chart titles and remove axis title")</span></span>

#### <a name="to-verify-the-charts-are-inside-the-rectangle"></a><span data-ttu-id="863d9-353">四角形の内側にグラフが配置されていることを確認するには</span><span class="sxs-lookup"><span data-stu-id="863d9-353">To verify the charts are inside the rectangle</span></span>

1.  <span data-ttu-id="863d9-354">このレッスンの前の手順で追加した四角形をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-354">Click the rectangle you added earlier in this lesson.</span></span>

     <span data-ttu-id="863d9-355">プロパティ ペインで `Name` プロパティに四角形の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-355">In the Properties pane, the `Name` property displays the name of the rectangle.</span></span>

     <span data-ttu-id="863d9-356">![四角形の名前](../../2014/tutorials/media/tutorial-rectanglename.png "四角形の名前")</span><span class="sxs-lookup"><span data-stu-id="863d9-356">![Name of rectangle](../../2014/tutorials/media/tutorial-rectanglename.png "Name of rectangle")</span></span>

2.  <span data-ttu-id="863d9-357">円グラフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-357">Click the pie chart.</span></span>

3.  <span data-ttu-id="863d9-358">**プロパティ**ペインで、 `Parent` プロパティに四角形の名前が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="863d9-358">In the **Properties** pane, verify that the `Parent` property contains the name of the rectangle.</span></span>

     <span data-ttu-id="863d9-359">![円グラフの親プロパティ](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "円グラフの親プロパティ")</span><span class="sxs-lookup"><span data-stu-id="863d9-359">![Parent property for pie chart](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "Parent property for pie chart")</span></span>

4.  <span data-ttu-id="863d9-360">縦棒グラフをクリックし、手順 2. および 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="863d9-360">Click the column chart and repeat steps 2 and 3.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="863d9-361">グラフが四角形の内側にない場合、表示レポートでグラフはいっしょに表示されません。</span><span class="sxs-lookup"><span data-stu-id="863d9-361">If the charts are not inside the rectangle, the rendered report does not display the charts together.</span></span>

#### <a name="to-make-the-charts-the-same-size"></a><span data-ttu-id="863d9-362">グラフのサイズを揃えるには</span><span class="sxs-lookup"><span data-stu-id="863d9-362">To make the charts the same size</span></span>

1.  <span data-ttu-id="863d9-363">円グラフをクリックし、Ctrl キーを押しながら縦棒グラフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-363">Click the pie chart, press the Ctrl key, and then click the column chart.</span></span>

2.  <span data-ttu-id="863d9-364">両方のグラフが選択されている状態で **[レイアウト]** をポイントし **[同じ幅に揃える]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="863d9-364">With both charts selected, right-click, point to **Layout**, and then click **Make Same Width**.</span></span>

     <span data-ttu-id="863d9-365">![グラフの幅を揃える](../../2014/tutorials/media/tutorial-makechartssamewidth.png "グラフの幅を揃える")</span><span class="sxs-lookup"><span data-stu-id="863d9-365">![Make chart widths the same](../../2014/tutorials/media/tutorial-makechartssamewidth.png "Make chart widths the same")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="863d9-366">最初にクリックしたアイテムの幅が、選択されたすべてのアイテムの幅になります。</span><span class="sxs-lookup"><span data-stu-id="863d9-366">The item you click first determines the width of all the selected items.</span></span>

3.  <span data-ttu-id="863d9-367">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="863d9-367">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="863d9-368">レポートに、円グラフと縦棒グラフで概要データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="863d9-368">The report now displays summary sales data in pie and column charts.</span></span>

 <span data-ttu-id="863d9-369">![SSRS チュートリアル、自由形式レポート](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS チュートリアル、自由形式レポート")</span><span class="sxs-lookup"><span data-stu-id="863d9-369">![SSRS tutorial, free form report](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS tutorial, free form report")</span></span>

## <a name="more-information"></a><span data-ttu-id="863d9-370">説明</span><span class="sxs-lookup"><span data-stu-id="863d9-370">More Information</span></span>
 <span data-ttu-id="863d9-371">リストの詳細については、「[テーブル、マトリックス、および一覧 &#40;レポートビルダーと ssrs&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)」、「 [&#40;レポートビルダーと ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」、「 [tablix データ領域の領域 &#40;レポートビルダーと ssrs&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md)」、および「 [tablix データ領域のセル、行、および列](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)&#40;レポートビルダー&#41; と ssrs」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="863d9-371">For more information about lists, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), [Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="863d9-372">クエリ デザイナーの詳細については、「[クエリ デザイナー (レポート ビルダー)](../../2014/reporting-services/query-designers-report-builder.md)」と「[テキストベースのクエリ デザイナーのユーザー インターフェイス (レポート ビルダー)](report-data/text-based-query-designer-user-interface-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="863d9-372">For more information about query designers, see [Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](report-data/text-based-query-designer-user-interface-report-builder.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="863d9-373">参照</span><span class="sxs-lookup"><span data-stu-id="863d9-373">See Also</span></span>
 <span data-ttu-id="863d9-374">[チュートリアル &#40;](report-builder-tutorials.md) [SQL Server 2014 でのレポートビルダー](report-builder/report-builder-in-sql-server-2016.md)&#41;レポートビルダー</span><span class="sxs-lookup"><span data-stu-id="863d9-374">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) [Report Builder in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)</span></span>


