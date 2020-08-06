---
title: 'チュートリアル: レポートへのスパークラインの追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 18c90a36-48bf-4805-a960-2d1e8f00c2dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1bf83810b6c743b977e399864ce2edd514f572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720955"
---
# <a name="tutorial-add-a-sparkline-to-your-report-report-builder"></a><span data-ttu-id="bb615-102">チュートリアル: レポートへのスパークラインの追加 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="bb615-102">Tutorial: Add a Sparkline to Your Report (Report Builder)</span></span>
  <span data-ttu-id="bb615-103">このチュートリアルでは、サンプルの売上データに基づいて基本的なテーブル レポートを作成してから、テーブルのセルにスパークライン グラフを追加します。</span><span class="sxs-lookup"><span data-stu-id="bb615-103">In this tutorial, you create a basic table report based on sample sales data, and then add a sparkline chart to a cell in the table.</span></span>  
  
 <span data-ttu-id="bb615-104">このチュートリアルで作成するレポートについては、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] レポート ビルダーのサンプル レポートに発展版が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb615-104">An enhanced version of the report you create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="bb615-105">このサンプルレポートおよびその他のレポートをダウンロードする方法の詳細については、「[レポートビルダーサンプルレポート](https://go.microsoft.com/fwlink/?LinkId=184851)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb615-105">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span> <span data-ttu-id="bb615-106">次の図に、ここで作成するレポートと同様のサンプル レポートを示します。</span><span class="sxs-lookup"><span data-stu-id="bb615-106">The following illustration shows the sample report similar to the one that you will create.</span></span>  
  
 <span data-ttu-id="bb615-107">![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")</span><span class="sxs-lookup"><span data-stu-id="bb615-107">![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")</span></span>  
  
 <span data-ttu-id="bb615-108">ビデオ「[方法: テーブルにスパークラインを作成する (レポートビルダービデオ)」](https://technet.microsoft.com/bi/ff871942.aspx)では、スパークラインを使用して同様のレポートを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb615-108">The video [How to: Create a Sparkline in a Table (Report Builder Video)](https://technet.microsoft.com/bi/ff871942.aspx) illustrates how to create a similar report with sparklines.</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="bb615-109">学習内容</span><span class="sxs-lookup"><span data-stu-id="bb615-109">What You Will Learn</span></span>  
 <span data-ttu-id="bb615-110">このチュートリアルでは、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="bb615-110">In this tutorial, you will learn how to do the following:</span></span>  
  
 1. [<span data-ttu-id="bb615-111">テーブルを使用したレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="bb615-111">Create a Report with a Table</span></span>](#CreateTable)  
  
 2. [<span data-ttu-id="bb615-112">テーブルまたはマトリックス ウィザードでクエリを作成する</span><span class="sxs-lookup"><span data-stu-id="bb615-112">Create a Query in the Table or Matrix Wizard</span></span>](#Query)  
  
 3. [<span data-ttu-id="bb615-113">スパークラインをテーブルに追加する</span><span class="sxs-lookup"><span data-stu-id="bb615-113">Add a Sparkline to the Table</span></span>](#Sparkline)  
  
 4. [<span data-ttu-id="bb615-114">スパークラインを垂直方向および水平方向に揃える</span><span class="sxs-lookup"><span data-stu-id="bb615-114">Align the Sparklines Vertically and Horizontally</span></span>](#AlignSparklines)  
  
### <a name="other-optional-steps"></a><span data-ttu-id="bb615-115">その他のオプションの手順</span><span class="sxs-lookup"><span data-stu-id="bb615-115">Other Optional Steps</span></span>  
 5. [<span data-ttu-id="bb615-116">データに通貨の書式を設定する</span><span class="sxs-lookup"><span data-stu-id="bb615-116">Format Data as Currency</span></span>](#FormatCurrency)  
  
 6. [<span data-ttu-id="bb615-117">データに日付の書式を設定する</span><span class="sxs-lookup"><span data-stu-id="bb615-117">Format Data as Dates</span></span>](#FormatDates)  
  
 7. [<span data-ttu-id="bb615-118">列幅を変更する</span><span class="sxs-lookup"><span data-stu-id="bb615-118">Change Column Widths</span></span>](#Width)  
  
 8. [<span data-ttu-id="bb615-119">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="bb615-119">Add a Report Title</span></span>](#Title)  
  
 9. [<span data-ttu-id="bb615-120">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="bb615-120">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="bb615-121">このチュートリアルの推定所要時間: 30 分。</span><span class="sxs-lookup"><span data-stu-id="bb615-121">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb615-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="bb615-122">Requirements</span></span>  
 <span data-ttu-id="bb615-123">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb615-123">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-report-with-a-table"></a><a name="CreateTable"></a><span data-ttu-id="bb615-124">1. テーブルを含むレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="bb615-124">1. Create a Report with a Table</span></span>  
  
#### <a name="to-create-a-report"></a><span data-ttu-id="bb615-125">レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="bb615-125">To create a report</span></span>  
  
1.  <span data-ttu-id="bb615-126">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-126">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="bb615-127">**[作業の開始]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="bb615-127">The **Getting Started** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bb615-128">[**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-128">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="bb615-129">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb615-129">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="bb615-130">右ペインで、 **[テーブルまたはマトリックス ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-130">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="bb615-131">**[データセットの選択]** ページで **[データセットを作成する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-131">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="bb615-132">**[データ ソースへの接続の選択]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="bb615-132">The **Choose a connection to a data source** page opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bb615-133">このチュートリアルでは、特定のデータは必要ありません。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] データベースへの接続だけが必要です。</span><span class="sxs-lookup"><span data-stu-id="bb615-133">This tutorial does not need specific data; it just needs a connection to a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span> <span data-ttu-id="bb615-134">**[データ ソース接続]** の一覧に既にデータ ソース接続が表示されている場合は、データ ソース接続を選択して手順 10 に進みます。</span><span class="sxs-lookup"><span data-stu-id="bb615-134">If you already have a data source connection listed under **Data Source Connections**, you can select it and go to step 10.</span></span> <span data-ttu-id="bb615-135">詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb615-135">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
5.  <span data-ttu-id="bb615-136">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-136">Click **New**.</span></span> <span data-ttu-id="bb615-137">**[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-137">The **Data Source Properties** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="bb615-138">**[名前]** に、データ ソースの名前として「 **Product Sales**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="bb615-138">In **Name**, type **Product Sales**, a name for the data source.</span></span>  
  
7.  <span data-ttu-id="bb615-139">**[接続の種類の選択]** で、 **[Microsoft SQL Server]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb615-139">In **Select a connection type**, verify that **Microsoft SQL Server** is selected.</span></span>  
  
8.  <span data-ttu-id="bb615-140">**[接続文字列]** に次のテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="bb615-140">In **Connection string**, type the following text:</span></span>  
  
     <span data-ttu-id="bb615-141">**データソース =\<servername>**</span><span class="sxs-lookup"><span data-stu-id="bb615-141">**Data Source=\<servername>**</span></span>  
  
     <span data-ttu-id="bb615-142">式 \<servername>には、たとえば Report001 など、SQL Server データベース エンジンのインスタンスがインストールされているコンピューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb615-142">The expression \<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="bb615-143">レポート データは SQL Server のデータベースから抽出されるのではないので、データベース名を含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bb615-143">Because the report data is not extracted from a SQL Server database, you need not include the name of a database.</span></span> <span data-ttu-id="bb615-144">指定したサーバー上の既定のデータベースを使用して、クエリが解析されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-144">The default database on the specified server is used to parse the query.</span></span>  
  
9. <span data-ttu-id="bb615-145">**[資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-145">Click **Credentials**.</span></span> <span data-ttu-id="bb615-146">外部データ ソースへのアクセスに必要な資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb615-146">Enter the credentials that you need to access the external data source.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="bb615-147">**[データ ソースへの接続の選択]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="bb615-147">You are back on the **Choose a connection to a data source** page.</span></span>  
  
11. <span data-ttu-id="bb615-148">データ ソースに接続できることを確認するために、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-148">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="bb615-149">"接続が正常に作成されました" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-149">The message "Connection created successfully" appears.</span></span>  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. <span data-ttu-id="bb615-150">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-150">Click **Next**.</span></span>  
  
##  <a name="2-create-a-query-in-the-table-wizard"></a><a name="Query"></a><span data-ttu-id="bb615-151">2. テーブルウィザードでクエリを作成する</span><span class="sxs-lookup"><span data-stu-id="bb615-151">2. Create a Query in the Table Wizard</span></span>  
 <span data-ttu-id="bb615-152">レポートでは、クエリが事前に定義された共有データセットを使用するか、そのレポートでのみ使用する埋め込みデータセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bb615-152">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="bb615-153">このチュートリアルでは、埋め込みデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb615-153">In this tutorial, you will create an embedded dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb615-154">このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="bb615-154">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="bb615-155">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="bb615-155">This makes the query quite long.</span></span> <span data-ttu-id="bb615-156">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="bb615-156">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="bb615-157">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="bb615-157">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-query"></a><span data-ttu-id="bb615-158">クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="bb615-158">To create a query</span></span>  
  
1.  <span data-ttu-id="bb615-159">**[クエリのデザイン]** ページでは、リレーショナル クエリ デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="bb615-159">On the **Design a query** page, the relational query designer is open.</span></span> <span data-ttu-id="bb615-160">このチュートリアルでは、テキスト ベースのクエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb615-160">For this tutorial, you will use the text-based query designer.</span></span>  
  
2.  <span data-ttu-id="bb615-161">[**テキストとして編集] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-161">Click **Edit As Text**.</span></span> <span data-ttu-id="bb615-162">テキスト ベースのクエリ デザイナーは、クエリ ペインと結果ペインで構成されています。</span><span class="sxs-lookup"><span data-stu-id="bb615-162">The text-based query designer displays a query pane and a results pane.</span></span>  
  
3.  <span data-ttu-id="bb615-163">[!INCLUDE[tsql](../includes/tsql-md.md)] [クエリ] **ボックスに、次の** クエリを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="bb615-163">Paste the following [!INCLUDE[tsql](../includes/tsql-md.md)] query into the **Query** box.</span></span>  
  
    ```  
    SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Budget Movie-Maker' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Slim Digital' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,'Accessories' as Subcategory,    
       'Budget Movie-Maker' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2010-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Carrying Case' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
4.  <span data-ttu-id="bb615-164">クエリ デザイナーのツール バーで、[実行]\(**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-164">On the query designer toolbar, click Run  (**!**).</span></span>  
  
     <span data-ttu-id="bb615-165">**SalesDate**、 **Subcategory**、 **Product**、 **Sales**、および **Quantity**の各フィールドを取得するクエリが実行され、結果セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-165">The query runs and displays the result set for the fields **SalesDate**, **Subcategory**, **Product**, **Sales**, and **Quantity**.</span></span>  
  
5.  <span data-ttu-id="bb615-166">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-166">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="bb615-167">**[フィールドの配置]** ページで、 **Sales** を **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bb615-167">On the **Arrange fields** page, drag **Sales** to **Values**.</span></span>  
  
     <span data-ttu-id="bb615-168">**Sales** は Sum 関数を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-168">**Sales** is aggregated by the Sum function.</span></span> <span data-ttu-id="bb615-169">値は [Sum(Sales)] です。</span><span class="sxs-lookup"><span data-stu-id="bb615-169">The value is [Sum(Sales)].</span></span>  
  
7.  <span data-ttu-id="bb615-170">**Product** を **[行グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bb615-170">Drag **Product** to **Row groups**.</span></span>  
  
8.  <span data-ttu-id="bb615-171">**SalesDate** を **[列グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bb615-171">Drag **SalesDate** to **Column groups**.</span></span>  
  
9. <span data-ttu-id="bb615-172">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-172">Click **Next**.</span></span>  
  
10. <span data-ttu-id="bb615-173">[**レイアウトの選択**] ページの [**オプション**] で、[**小計と総計を表示**する] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb615-173">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="bb615-174">ウィザードのプレビュー ペインに、3 行を含むテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-174">The wizard Preview pane displays a table with three rows.</span></span> <span data-ttu-id="bb615-175">レポートを実行すると、各行は次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-175">When you run the report, each row will display in the following way:</span></span>  
  
    1.  <span data-ttu-id="bb615-176">1 行目はテーブルで 1 回表示され、列見出しを示します。</span><span class="sxs-lookup"><span data-stu-id="bb615-176">The first row will appear once for the table to show column headings.</span></span>  
  
    2.  <span data-ttu-id="bb615-177">2 行目は製品ごとに 1 回表示され、製品名、1 日あたりの合計、および行の合計を示します。</span><span class="sxs-lookup"><span data-stu-id="bb615-177">The second row will repeat once for each product and display the product name, total per day, and line total.</span></span>  
  
    3.  <span data-ttu-id="bb615-178">3 行目はテーブルで 1 回表示され、総計を示します。</span><span class="sxs-lookup"><span data-stu-id="bb615-178">The third row will appear once for the table to display the grand totals.</span></span>  
  
11. <span data-ttu-id="bb615-179">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-179">Click **Next**.</span></span>  
  
12. <span data-ttu-id="bb615-180">**[スタイルの選択]** ページの **スタイル** ペインで、 **[スレート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb615-180">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>  
  
     <span data-ttu-id="bb615-181">プレビュー ペインにそのスタイルのテーブルのサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-181">The Preview pane displays a sample of the table with that style.</span></span>  
  
13. <span data-ttu-id="bb615-182">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-182">Click **Finish**.</span></span>  
  
14. <span data-ttu-id="bb615-183">テーブルがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-183">The table is added to the design surface.</span></span> <span data-ttu-id="bb615-184">テーブルには 3 列および 5 行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb615-184">The table has three columns and three rows.</span></span>  
  
     <span data-ttu-id="bb615-185">グループ化ペインを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb615-185">Look in the Grouping pane.</span></span> <span data-ttu-id="bb615-186">グループ化ペインが表示されない場合、 **[表示]** メニューの **[グループ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-186">If you can't see the Grouping pane, on the **View** menu, click **Grouping**.</span></span> <span data-ttu-id="bb615-187">行グループ ペインに行グループ **Product**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-187">The Row Groups pane shows one row group: **Product**.</span></span> <span data-ttu-id="bb615-188">列グループ ペインに列グループ **SalesDate**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-188">The Column Groups pane shows one column group: **SalesDate**.</span></span> <span data-ttu-id="bb615-189">詳細データは、データセット クエリによって取得されるすべてのデータです。</span><span class="sxs-lookup"><span data-stu-id="bb615-189">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
15. <span data-ttu-id="bb615-190">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="bb615-190">Click **Run** to preview the report.</span></span>  
  
##  <a name="3-add-a-sparkline"></a><a name="Sparkline"></a><span data-ttu-id="bb615-191">3. スパークラインを追加する</span><span class="sxs-lookup"><span data-stu-id="bb615-191">3. Add a Sparkline</span></span>  
  
#### <a name="to-add-a-sparkline-chart-to-a-table"></a><span data-ttu-id="bb615-192">テーブルにスパークライン グラフを追加するには</span><span class="sxs-lookup"><span data-stu-id="bb615-192">To add a sparkline chart to a table</span></span>  
  
1.  <span data-ttu-id="bb615-193">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="bb615-193">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="bb615-194">テーブルの合計列を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb615-194">Select the Total column in your table.</span></span>  
  
3.  <span data-ttu-id="bb615-195">右クリックして表示される **[列の挿入]** を選択してから、 **[左]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-195">Right-click, point to **Insert Column**, and then click **Left**.</span></span>  
  
4.  <span data-ttu-id="bb615-196">新しい列で [Product] 行を右クリックし、[**挿入**] リボンタブをポイントして、[**スパークライン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-196">In the new column, right-click in the [Product] row, point to the **Insert** ribbon tab, and then click **Sparkline**.</span></span>  
  
5.  <span data-ttu-id="bb615-197">**列**の行の最初のスパークラインが選択されていることを確認し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-197">Make sure the first sparkline in the **Column** row is selected and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="bb615-198">スパークラインをクリックして、グラフ データ ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="bb615-198">Click the sparkline to show the Chart Data pane.</span></span>  
  
7.  <span data-ttu-id="bb615-199">[値] ボックスのプラス記号 (+) をクリックし、[ **Sales**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-199">Click the plus (+) sign in the Values box, and then click **Sales**.</span></span>  
  
     <span data-ttu-id="bb615-200">**Sales** フィールドの値がスパークラインの値になります。</span><span class="sxs-lookup"><span data-stu-id="bb615-200">The values in the **Sales** field are now the values for the sparkline.</span></span>  
  
8.  <span data-ttu-id="bb615-201">[カテゴリグループ] ボックスのプラス記号 (+) をクリックし、[ **Salesdate**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-201">Click the plus (+) sign in the Category Groups box, and then click **SalesDate**.</span></span>  
  
9. <span data-ttu-id="bb615-202">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="bb615-202">Click **Run** to preview your report.</span></span>  
  
     <span data-ttu-id="bb615-203">テーブルの各行にスパークライン グラフがありますが、正しくないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bb615-203">Note that there are sparkline charts in each row of the table, but they're not correct.</span></span> <span data-ttu-id="bb615-204">グラフ内のバーが揃っていません。</span><span class="sxs-lookup"><span data-stu-id="bb615-204">The bars in the charts don't line up with each other.</span></span> <span data-ttu-id="bb615-205">データの 2 行目のバーは 4 本しかないので、バーが 6 本ある最初の行のバーよりも太くなっています。</span><span class="sxs-lookup"><span data-stu-id="bb615-205">There are only four bars in the second row of data, so the bars are wider than the bars in the first row, which has six.</span></span> <span data-ttu-id="bb615-206">1 日あたりの各製品の値を比較できません。</span><span class="sxs-lookup"><span data-stu-id="bb615-206">You can't compare values for each product per day.</span></span> <span data-ttu-id="bb615-207">グラフ内のバーは揃っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb615-207">They need to line up with each other.</span></span>  
  
     <span data-ttu-id="bb615-208">また、どの行も、最も高いバーの高さがその行の高さに合わせられています。</span><span class="sxs-lookup"><span data-stu-id="bb615-208">Also note that for each row, the tallest bar for that row is the height of the row.</span></span> <span data-ttu-id="bb615-209">これは、各行の最大値が等しくないため、誤解を招くこともあります。予算ムービーメーカーの最大値は $10400 ですが、スリムデジタルの最大値は $26576-2 倍以上のサイズです。</span><span class="sxs-lookup"><span data-stu-id="bb615-209">This is misleading, too, because the largest values for each row are not equal: the largest value for Budget Movie-Maker is $10,400, but the largest value for Slim Digital is $26,576-more than twice as large.</span></span> <span data-ttu-id="bb615-210">ところが、これらの 2 つの行の最も高いバーはほぼ同じ高さになっています。</span><span class="sxs-lookup"><span data-stu-id="bb615-210">And yet the largest bars in those two rows are about the same height.</span></span> <span data-ttu-id="bb615-211">こちらも他のスパークラインに合わせて修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb615-211">That also needs to be made to scale with the other sparklines.</span></span>  
  
     <span data-ttu-id="bb615-212">![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")</span><span class="sxs-lookup"><span data-stu-id="bb615-212">![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")</span></span>  
  
##  <a name="4-align-the-sparklines-vertically-and-horizontally"></a><a name="AlignSparklines"></a><span data-ttu-id="bb615-213">4. スパークラインを垂直方向および水平方向に揃える</span><span class="sxs-lookup"><span data-stu-id="bb615-213">4. Align the Sparklines Vertically and Horizontally</span></span>  
 <span data-ttu-id="bb615-214">スパークラインは、すべて同じ測定値を使用しないと、読み取るのは困難です。</span><span class="sxs-lookup"><span data-stu-id="bb615-214">The sparklines are hard to read when they don't all use the same measurements.</span></span> <span data-ttu-id="bb615-215">各スパークラインの縦軸と横軸は、残りのスパークラインと一致させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb615-215">Both the horizontal and vertical axes for each need to match the rest.</span></span>  
  
#### <a name="to-set-alignment-for-the-sparklines-in-the-table"></a><span data-ttu-id="bb615-216">テーブル内のスパークラインの配置を設定するには</span><span class="sxs-lookup"><span data-stu-id="bb615-216">To set alignment for the sparklines in the table</span></span>  
  
1.  <span data-ttu-id="bb615-217">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="bb615-217">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="bb615-218">スパークラインを右クリックし、 **[縦軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-218">Right-click the sparkline and click **Vertical Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="bb615-219">**[軸を整列する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="bb615-219">Check the **Align axes in** check box.</span></span>  
  
     <span data-ttu-id="bb615-220">一覧に Tablix1 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-220">Tablix1 is showing in the list.</span></span> <span data-ttu-id="bb615-221">これが唯一のオプションです。</span><span class="sxs-lookup"><span data-stu-id="bb615-221">That is the only option.</span></span> <span data-ttu-id="bb615-222">このオプションによって、各スパークラインのバーの高さが相対的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-222">This sets the height of the bars in each sparkline relative to the others.</span></span>  
  
4.  <span data-ttu-id="bb615-223">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-223">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="bb615-224">スパークラインを右クリックし、 **[横軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-224">Right-click the sparkline and click **Horizontal Axis Properties**.</span></span>  
  
6.  <span data-ttu-id="bb615-225">**[軸を整列する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="bb615-225">Check the **Align axes in** check box.</span></span>  
  
     <span data-ttu-id="bb615-226">一覧に Tablix1 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-226">Tablix1 is showing in the list.</span></span> <span data-ttu-id="bb615-227">これが唯一のオプションです。</span><span class="sxs-lookup"><span data-stu-id="bb615-227">That is the only option.</span></span> <span data-ttu-id="bb615-228">このオプションによって、各スパークラインのバーの幅が相対的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-228">This sets the width of the bars in each sparkline relative to the others.</span></span> <span data-ttu-id="bb615-229">あるスパークラインで他のスパークラインよりバーの数が少ない場合は、そのスパークラインのデータがない位置は空白のスペースになります。</span><span class="sxs-lookup"><span data-stu-id="bb615-229">If some sparklines have fewer bars than others, then those sparklines will have blank spaces for the missing data.</span></span>  
  
7.  <span data-ttu-id="bb615-230">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-230">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="bb615-231">**[実行]** をクリックして、レポートをもう一度プレビューします。</span><span class="sxs-lookup"><span data-stu-id="bb615-231">Click **Run** to preview your report again.</span></span>  
  
 <span data-ttu-id="bb615-232">今度は、すべてのバーが他の行のバーと揃っています。</span><span class="sxs-lookup"><span data-stu-id="bb615-232">Note that all the bars are now aligned with the bars in the other rows.</span></span>  
  
##  <a name="5-optional-format-data-as-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="bb615-233">5. (省略可能) データを通貨として書式設定する</span><span class="sxs-lookup"><span data-stu-id="bb615-233">5. (Optional) Format Data as Currency</span></span>  
 <span data-ttu-id="bb615-234">既定では、 **Sales**フィールドの集計データには一般的な数値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-234">By default, the summary data for the **Sales** field displays a general number.</span></span> <span data-ttu-id="bb615-235">このフィールドを書式設定して、数値を通貨として表示します。</span><span class="sxs-lookup"><span data-stu-id="bb615-235">Format it to display the number as currency.</span></span> <span data-ttu-id="bb615-236">書式設定したテキスト ボックスおよびプレースホルダー テキストのサンプル値を表示するには、 **[プレースホルダーのスタイル]** の設定を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="bb615-236">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="bb615-237">通貨フィールドを書式設定するには</span><span class="sxs-lookup"><span data-stu-id="bb615-237">To format a currency field</span></span>  
  
1.  <span data-ttu-id="bb615-238">デザインビューに切り替えるには、[**デザイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-238">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="bb615-239">**Salesdate**列の2番目の行 (列見出しの行) のセルをクリックし、をドラッグして、を含むすべてのセルを選択し `[Sum(Sales)]` ます。</span><span class="sxs-lookup"><span data-stu-id="bb615-239">Click the cell in the second row (under the column headings row) in the **SalesDate** column and drag to select all cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="bb615-240">**[ホーム]** タブの **[数値]** グループで、 **[通貨]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-240">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="bb615-241">書式設定された通貨を表示するようにセルが変化します。</span><span class="sxs-lookup"><span data-stu-id="bb615-241">The cells change to show the formatted currency.</span></span>  
  
     <span data-ttu-id="bb615-242">地域設定が英語 (米国) の場合、既定のサンプル テキストは [**$12,345.00**] です。</span><span class="sxs-lookup"><span data-stu-id="bb615-242">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="bb615-243">通貨値の例が表示されない場合は、[**数値**] グループの [**プレースホルダーのスタイル**] をクリックし、[**サンプルの値**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-243">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="bb615-244">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="bb615-244">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="bb615-245">**Sales**の集計値は通貨として表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-245">The summary values for **Sales** display as currency.</span></span>  
  
##  <a name="6-optional-format-data-as-dates"></a><a name="FormatDates"></a><span data-ttu-id="bb615-246">6. (省略可能) データを日付として書式設定する</span><span class="sxs-lookup"><span data-stu-id="bb615-246">6. (Optional) Format Data as Dates</span></span>  
 <span data-ttu-id="bb615-247">既定では、 **salesdate**フィールドには日付と時刻の両方の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-247">By default, the **SalesDate** field displays both date and time information.</span></span> <span data-ttu-id="bb615-248">このフィールドを書式設定して、日付のみを表示できます。</span><span class="sxs-lookup"><span data-stu-id="bb615-248">You can format them to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a><span data-ttu-id="bb615-249">日付フィールドの書式を既定の書式に設定するには</span><span class="sxs-lookup"><span data-stu-id="bb615-249">To format a date field as the default format</span></span>  
  
1.  <span data-ttu-id="bb615-250">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="bb615-250">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="bb615-251">`[SalesDate]`が格納されたセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-251">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="bb615-252">リボンの [**ホーム**] タブの [**数値**] グループで、ドロップダウンリストから [**日付**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb615-252">On the Ribbon, on the **Home** tab, in the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="bb615-253">セルに、日付の例として **[2000/1/31]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-253">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="bb615-254">日付の例が表示されない場合は、 **[数値]** グループの **[プレースホルダーのスタイル]** をクリックし、 **[サンプルの値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-254">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="bb615-255">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="bb615-255">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="bb615-256">**Salesdate**の値は、既定の日付形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-256">The **SalesDate** values display in the default date format.</span></span>  
  
##  <a name="7-optional-change-column-widths"></a><a name="Width"></a><span data-ttu-id="bb615-257">7. (省略可能) 列の幅を変更する</span><span class="sxs-lookup"><span data-stu-id="bb615-257">7. (Optional) Change Column Widths</span></span>  
 <span data-ttu-id="bb615-258">テーブルの各セルには、既定でテキスト ボックスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb615-258">By default, each cell in a table contains a text box.</span></span> <span data-ttu-id="bb615-259">テキスト ボックスは、ページを表示するときにテキストに合わせて垂直方向に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-259">A text box expands vertically to accommodate text when the page is rendered.</span></span> <span data-ttu-id="bb615-260">表示されるレポートでは、各行がその行で最も高いテキスト ボックスの高さに拡張されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-260">In the rendered report, each row expands to the height of the tallest rendered text box in the row.</span></span> <span data-ttu-id="bb615-261">デザイン画面の行の高さは、表示されるレポートの行の高さには影響しません。</span><span class="sxs-lookup"><span data-stu-id="bb615-261">The height of the row on the design surface has no affect on the height of the row in the rendered report.</span></span>  
  
 <span data-ttu-id="bb615-262">各行の垂直方向の領域を小さくするには、列の幅を広げ、列で想定されるテキスト ボックスの内容が 1 行に収まるようにします。</span><span class="sxs-lookup"><span data-stu-id="bb615-262">To reduce the amount of vertical space each row takes, expand the column width to accommodate the expected contents of the text boxes in the column on one line.</span></span>  
  
#### <a name="to-change-the-width-of-columns"></a><span data-ttu-id="bb615-263">列の幅を変更するには</span><span class="sxs-lookup"><span data-stu-id="bb615-263">To change the width of columns</span></span>  
  
1.  <span data-ttu-id="bb615-264">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="bb615-264">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="bb615-265">テーブルをクリックし、列ハンドルおよび行ハンドルをテーブルの上部および横に表示します。</span><span class="sxs-lookup"><span data-stu-id="bb615-265">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="bb615-266">テーブルの上と横のグレーのバーは、列および行ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="bb615-266">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
3.  <span data-ttu-id="bb615-267">列ハンドルの間の罫線をポイントします。カーソルが 2 方向の矢印の形状に変化します。</span><span class="sxs-lookup"><span data-stu-id="bb615-267">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="bb615-268">列をドラッグして、目的のサイズに変更します。</span><span class="sxs-lookup"><span data-stu-id="bb615-268">Drag the columns to the size you want.</span></span> <span data-ttu-id="bb615-269">たとえば、製品名が1行に表示されるように**product**の列を展開します。</span><span class="sxs-lookup"><span data-stu-id="bb615-269">For example, expand the column for **Product** so that the product name displays on one line.</span></span>  
  
4.  <span data-ttu-id="bb615-270">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="bb615-270">Click **Run** to preview your report.</span></span>  
  
##  <a name="8-optional-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="bb615-271">8. (省略可能) レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="bb615-271">8. (Optional) Add a Report Title</span></span>  
 <span data-ttu-id="bb615-272">レポート タイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-272">A report title appears at the top of the report.</span></span> <span data-ttu-id="bb615-273">レポート ヘッダーがあれば、そこにレポート タイトルを配置します。レポート ヘッダーを使用しない場合は、レポート本文の一番上のテキスト ボックスに配置します。</span><span class="sxs-lookup"><span data-stu-id="bb615-273">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="bb615-274">このチュートリアルでは、自動的にレポート本文の一番上に配置されるテキスト ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb615-274">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="bb615-275">テキストの語句や文字のフォントのスタイル、サイズ、および色を変更して、テキストをさらに強調することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb615-275">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="bb615-276">詳細については、「[テキスト ボックス内のテキストの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb615-276">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="bb615-277">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="bb615-277">To add a report title</span></span>  
  
1.  <span data-ttu-id="bb615-278">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-278">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="bb615-279">「 **Product Sales**」と入力し、テキスト ボックスの外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-279">Type **Product Sales**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="bb615-280">**Product Sales** が含まれているテキスト ボックスを右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-280">Right-click the text box that contains **Product Sales** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="bb615-281">**[テキスト ボックスのプロパティ]** ダイアログ ボックスで、 **[フォント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-281">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="bb615-282">**[サイズ]** ボックスの一覧の **[18pt]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb615-282">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="bb615-283">[**色**] ボックスの一覧で [**茶色**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb615-283">In the **Color** list, select **Maroon**.</span></span>  
  
7.  <span data-ttu-id="bb615-284">**[太字]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb615-284">Select **Bold**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="9-save-the-report"></a><a name="Save"></a><span data-ttu-id="bb615-285">9. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="bb615-285">9. Save the Report</span></span>  
 <span data-ttu-id="bb615-286">レポートをレポート サーバーまたは自分のコンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="bb615-286">Save the report to a report server or your computer.</span></span> <span data-ttu-id="bb615-287">レポート サーバーに保存しない場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のいくつかの機能 (レポート パーツ、サブレポートなど) が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bb615-287">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="bb615-288">レポート サーバーにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="bb615-288">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="bb615-289">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-289">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="bb615-290">**[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-290">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="bb615-291">レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="bb615-291">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="bb615-292">"レポート サーバーに接続しています" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-292">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="bb615-293">接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-293">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="bb615-294">**[名前]** に入力されている既定の名前を「 **Product Sales**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bb615-294">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
5.  <span data-ttu-id="bb615-295">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-295">Click **Save**.</span></span>  
  
 <span data-ttu-id="bb615-296">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-296">The report is saved to the report server.</span></span> <span data-ttu-id="bb615-297">接続しているレポート サーバーの名前がウィンドウ下部のステータス バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb615-297">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="bb615-298">コンピューターにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="bb615-298">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="bb615-299">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-299">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="bb615-300">**[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、レポートを保存するフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="bb615-300">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="bb615-301">**[名前]** に入力されている既定の名前を「 **Product Sales**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bb615-301">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
4.  <span data-ttu-id="bb615-302">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb615-302">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="bb615-303">次の手順</span><span class="sxs-lookup"><span data-stu-id="bb615-303">Next Steps</span></span>  
 <span data-ttu-id="bb615-304">これで、スパークライン グラフを使ったテーブル レポートを作成するチュートリアルを終了します。</span><span class="sxs-lookup"><span data-stu-id="bb615-304">This concludes the tutorial for creating a table report with sparkline charts.</span></span> <span data-ttu-id="bb615-305">スパークラインの詳細については、[「スパークラインとデータ バー (レポート ビルダーおよび SSRS)」](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb615-305">For more information about sparklines, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb615-306">参照</span><span class="sxs-lookup"><span data-stu-id="bb615-306">See Also</span></span>  
 <span data-ttu-id="bb615-307">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="bb615-307">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="bb615-308">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="bb615-308">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
