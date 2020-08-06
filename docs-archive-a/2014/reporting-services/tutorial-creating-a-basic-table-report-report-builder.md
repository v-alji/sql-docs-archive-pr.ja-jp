---
title: チュートリアル:基本的な表レポートの作成 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9e30521-f8ae-4c45-89c3-d40727f622f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3587e2a53e2b09dd347a2733875eafd708b8a05a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633714"
---
# <a name="tutorial-creating-a-basic-table-report-report-builder"></a><span data-ttu-id="b2a96-102">チュートリアル:基本的な表レポートの作成 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="b2a96-102">Tutorial: Creating a Basic Table Report (Report Builder)</span></span>
  <span data-ttu-id="b2a96-103">このチュートリアルでは、サンプルの売上データに基づいて基本的な表レポートを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-103">This tutorial teaches you to create a basic table report based on sample sales data.</span></span> <span data-ttu-id="b2a96-104">次の図に、ここで作成するレポートを示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-104">The following illustration shows the report you will create.</span></span>  
  
 <span data-ttu-id="b2a96-105">![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")</span><span class="sxs-lookup"><span data-stu-id="b2a96-105">![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="b2a96-106">学習内容</span><span class="sxs-lookup"><span data-stu-id="b2a96-106">What You Will Learn</span></span>  
 <span data-ttu-id="b2a96-107">このチュートリアルでは、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-107">In this tutorial, you will learn how to do the following:</span></span>  
  
1.  <span data-ttu-id="b2a96-108">[[作業の開始] を使用して新しいレポートを作成する](#CreateTable)</span><span class="sxs-lookup"><span data-stu-id="b2a96-108">[Create a New Report from Getting Started](#CreateTable)</span></span>  
  
    1.  [<span data-ttu-id="b2a96-109">テーブル ウィザードでデータ接続を指定する</span><span class="sxs-lookup"><span data-stu-id="b2a96-109">Specify a Data Connection in the Table Wizard</span></span>](#DataConnection)  
  
    2.  [<span data-ttu-id="b2a96-110">テーブル ウィザードでクエリを作成する</span><span class="sxs-lookup"><span data-stu-id="b2a96-110">Create a Query in the Table Wizard</span></span>](#Query)  
  
    3.  [<span data-ttu-id="b2a96-111">テーブル ウィザードでデータをグループにまとめる</span><span class="sxs-lookup"><span data-stu-id="b2a96-111">Organize Data into Groups in the Table Wizard</span></span>](#Groups)  
  
    4.  [<span data-ttu-id="b2a96-112">テーブル ウィザードで小計行と合計行を追加する</span><span class="sxs-lookup"><span data-stu-id="b2a96-112">Add Subtotal and Total Rows in the Table Wizard</span></span>](#Subtotals)  
  
    5.  [<span data-ttu-id="b2a96-113">テーブル ウィザードでスタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="b2a96-113">Choose a Style in the Table Wizard</span></span>](#Style)  
  
2.  [<span data-ttu-id="b2a96-114">データに通貨の書式を設定する</span><span class="sxs-lookup"><span data-stu-id="b2a96-114">Format Data as Currency</span></span>](#FormatCurrency)  
  
3.  [<span data-ttu-id="b2a96-115">データに日付の書式を設定する</span><span class="sxs-lookup"><span data-stu-id="b2a96-115">Format Data as Date</span></span>](#FormatDate)  
  
4.  [<span data-ttu-id="b2a96-116">列幅を変更する</span><span class="sxs-lookup"><span data-stu-id="b2a96-116">Change Column Widths</span></span>](#Width)  
  
5.  [<span data-ttu-id="b2a96-117">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="b2a96-117">Add a Report Title</span></span>](#Title)  
  
6.  [<span data-ttu-id="b2a96-118">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="b2a96-118">Save the Report</span></span>](#Save)  
  
7.  [<span data-ttu-id="b2a96-119">レポートをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="b2a96-119">Export the Report</span></span>](#Export)  
  
 <span data-ttu-id="b2a96-120">このチュートリアルの推定所要時間 : 20 分</span><span class="sxs-lookup"><span data-stu-id="b2a96-120">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2a96-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="b2a96-121">Requirements</span></span>  
 <span data-ttu-id="b2a96-122">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2a96-122">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-new-report-from-getting-started"></a><a name="CreateTable"></a><span data-ttu-id="b2a96-123">1. はじめにから新しいレポートを作成します</span><span class="sxs-lookup"><span data-stu-id="b2a96-123">1. Create a New Report from Getting Started</span></span>  
 <span data-ttu-id="b2a96-124">[**はじめに**] ダイアログボックスからテーブルレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-124">Create a table report from the **Getting Started** dialog box.</span></span> <span data-ttu-id="b2a96-125">レポート デザイン モードと共有データセット デザイン モードの 2 つのモードがあります。</span><span class="sxs-lookup"><span data-stu-id="b2a96-125">There are two modes: report design and shared dataset design.</span></span> <span data-ttu-id="b2a96-126">レポート デザイン モードでは、レポート データ ペインでデータを指定し、デザイン画面でレポート レイアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-126">In report design mode, you specify data in the Report Data pane and the report layout on the design surface.</span></span> <span data-ttu-id="b2a96-127">共有データセット デザイン モードでは、他のユーザーと共有するデータセット クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-127">In shared dataset design mode, you create dataset queries to share with others.</span></span> <span data-ttu-id="b2a96-128">このチュートリアルでは、レポート デザイン モードを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-128">In this tutorial, you will be using report design mode.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="b2a96-129">新しいレポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-129">To create a new report</span></span>  
  
1.  <span data-ttu-id="b2a96-130">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-130">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="b2a96-131">**[作業の開始]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-131">The **Getting Started** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2a96-132">[**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-132">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="b2a96-133">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-133">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="b2a96-134">右ペインで、 **[テーブルまたはマトリックス ウィザード]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-134">In the right pane, verify that **Table or Matrix Wizard** is selected.</span></span>  
  
##  <a name="1a-specify-a-data-connection-in-the-table-wizard"></a><a name="DataConnection"></a><span data-ttu-id="b2a96-135">sr-1.</span><span class="sxs-lookup"><span data-stu-id="b2a96-135">1a.</span></span> <span data-ttu-id="b2a96-136">テーブル ウィザードでデータ接続を指定する</span><span class="sxs-lookup"><span data-stu-id="b2a96-136">Specify a Data Connection in the Table Wizard</span></span>  
 <span data-ttu-id="b2a96-137">データ接続には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースなどの外部データ ソースに接続するときに必要な情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-137">A data connection contains the information to connect to an external data source such as a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="b2a96-138">通常、使用する接続情報と資格情報の種類はデータ ソースの所有者から提供されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-138">Usually, you get the connection information and the type of credentials to use from the data source owner.</span></span> <span data-ttu-id="b2a96-139">データ接続を指定するには、レポート サーバーの共有データ ソースを使用するか、このレポートでのみ使用する埋め込みデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-139">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in this report.</span></span>  
  
 <span data-ttu-id="b2a96-140">このチュートリアルでは、埋め込みデータ ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-140">In this tutorial, you will use an embedded data source.</span></span> <span data-ttu-id="b2a96-141">共有データ ソースの使用方法の詳細については、「[別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2a96-141">To learn more about using a shared data sources, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="b2a96-142">埋め込みデータ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-142">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="b2a96-143">**[データセットの選択]** ページで **[データセットを作成する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-143">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="b2a96-144">**[データ ソースへの接続の選択]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-144">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="b2a96-145">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-145">Click **New**.</span></span> <span data-ttu-id="b2a96-146">**[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-146">The **Data Source Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b2a96-147">[**名前**] に、データソースの名前として「 **Product Sales** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-147">In **Name**, type **Product Sales** a name for the data source.</span></span>  
  
4.  <span data-ttu-id="b2a96-148">**[接続の種類の選択]** で、 **[Microsoft SQL Server]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-148">In **Select a connection type**, verify that **Microsoft SQL Server** is selected.</span></span>  
  
5.  <span data-ttu-id="b2a96-149">[**接続文字列**] に次のテキストを入力します。ここで、 *\<servername>* はのインスタンスの名前です [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b2a96-149">In **Connection string**, type the following text, where *\<servername>* is the name of an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
    ```  
    Data Source=<servername>  
    ```  
  
     <span data-ttu-id="b2a96-150">データベースからデータを取得する代わりに、データを指定するクエリを使用するため、接続文字列にデータベース名は含まれません。</span><span class="sxs-lookup"><span data-stu-id="b2a96-150">Because you will use a query that contains the data instead of retrieving the data from a database, the connection string does not include the database name.</span></span> <span data-ttu-id="b2a96-151">詳細については、「[チュートリアルの前提条件 &#40;レポート ビルダー&#41;](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2a96-151">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
6.  <span data-ttu-id="b2a96-152">**[資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-152">Click **Credentials**.</span></span> <span data-ttu-id="b2a96-153">外部データ ソースへのアクセスに必要な資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-153">Enter the credentials that you need to access the external data source.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="b2a96-154">**[データ ソースへの接続の選択]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="b2a96-154">You are back on the **Choose a connection to a data source** page.</span></span>  
  
8.  <span data-ttu-id="b2a96-155">データ ソースに接続できることを確認するために、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-155">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="b2a96-156">"接続が正常に作成されました" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-156">The message "Connection created successfully" appears.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="b2a96-157">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-157">Click **Next**.</span></span>  
  
##  <a name="1b-create-a-query-in-the-table-wizard"></a><a name="Query"></a><span data-ttu-id="b2a96-158">ドル.</span><span class="sxs-lookup"><span data-stu-id="b2a96-158">1b.</span></span> <span data-ttu-id="b2a96-159">テーブル ウィザードでクエリを作成する</span><span class="sxs-lookup"><span data-stu-id="b2a96-159">Create a Query in the Table Wizard</span></span>  
 <span data-ttu-id="b2a96-160">レポートでは、クエリが事前に定義された共有データセットを使用するか、そのレポートでのみ使用する埋め込みデータセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-160">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="b2a96-161">このチュートリアルでは、埋め込みデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-161">In this tutorial, you will create an embedded dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2a96-162">このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="b2a96-162">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="b2a96-163">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="b2a96-163">This makes the query quite long.</span></span> <span data-ttu-id="b2a96-164">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="b2a96-164">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="b2a96-165">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="b2a96-165">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-query"></a><span data-ttu-id="b2a96-166">クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-166">To create a query</span></span>  
  
1.  <span data-ttu-id="b2a96-167">**[クエリのデザイン]** ページでは、リレーショナル クエリ デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-167">On the **Design a query** page, the relational query designer is open.</span></span> <span data-ttu-id="b2a96-168">このチュートリアルでは、テキスト ベースのクエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-168">For this tutorial, you will use the text-based query designer.</span></span>  
  
     <span data-ttu-id="b2a96-169">[**テキストとして編集] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-169">Click **Edit As Text**.</span></span> <span data-ttu-id="b2a96-170">テキスト ベースのクエリ デザイナーは、クエリ ペインと結果ペインで構成されています。</span><span class="sxs-lookup"><span data-stu-id="b2a96-170">The text-based query designer displays a query pane and a results pane.</span></span>  
  
2.  <span data-ttu-id="b2a96-171">[!INCLUDE[tsql](../includes/tsql-md.md)] [クエリ] **ボックスに、次の** クエリを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-171">Paste the following [!INCLUDE[tsql](../includes/tsql-md.md)] query into the **Query** box.</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(9924.60 AS money) AS Sales, 68 as Quantity  
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
  
3.  <span data-ttu-id="b2a96-172">クエリデザイナーのツールバーで、[**実行**] (**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-172">On the query designer toolbar, click **Run** (**!**).</span></span>  
  
     <span data-ttu-id="b2a96-173">SalesDate、Subcategory、Product、Sales、および Quantity の各フィールドを取得するクエリが実行され、結果セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-173">The query runs and displays the result set for the fields SalesDate, Subcategory, Product, Sales, and Quantity.</span></span>  
  
     <span data-ttu-id="b2a96-174">結果セットの列見出しはクエリの名前に基づきます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-174">In the result set, the column headings are based on the names in the query.</span></span> <span data-ttu-id="b2a96-175">データセットの列見出しはフィールド名になり、レポートに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-175">In the dataset, the column headings become the field names, and are saved in the report.</span></span> <span data-ttu-id="b2a96-176">ウィザードを完了した後、レポート データ ペインを使用してデータセット フィールドのコレクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-176">After you complete the wizard, you can use the Report Data pane to view the collection of dataset fields.</span></span>  
  
4.  <span data-ttu-id="b2a96-177">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-177">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups-in-the-table-wizard"></a><a name="Groups"></a><span data-ttu-id="b2a96-178">1c.</span><span class="sxs-lookup"><span data-stu-id="b2a96-178">1c.</span></span> <span data-ttu-id="b2a96-179">テーブル ウィザードでデータをグループにまとめる</span><span class="sxs-lookup"><span data-stu-id="b2a96-179">Organize Data into Groups in the Table Wizard</span></span>  
 <span data-ttu-id="b2a96-180">グループ化するフィールドを選択し、詳細データおよび集計データを表示する行と列を含むテーブルをデザインします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-180">When you select fields to group on, you design a table that has rows and columns that display detail data and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="b2a96-181">データをグループにまとめるには</span><span class="sxs-lookup"><span data-stu-id="b2a96-181">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="b2a96-182">[**フィールドの配置**] ページで、Product を [**値**] にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-182">On the **Arrange fields** page, drag Product to **Values**.</span></span>  
  
2.  <span data-ttu-id="b2a96-183">Quantity を **[値]** にドラッグして Product の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-183">Drag Quantity to **Values** and place below Product.</span></span>  
  
     <span data-ttu-id="b2a96-184">Quantity は Sum 関数 (数値フィールドの既定の集計関数) を使用して自動的に集計されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-184">Quantity is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="b2a96-185">値は [Sum(Quantity)] です。</span><span class="sxs-lookup"><span data-stu-id="b2a96-185">The value is [Sum(Quantity)].</span></span>  
  
     <span data-ttu-id="b2a96-186">ドロップダウン リストを開くと、使用可能なその他の集計関数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-186">You can open the drop-down list to view the other aggregate functions available.</span></span> <span data-ttu-id="b2a96-187">集計関数は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="b2a96-187">Do not change the aggregate function.</span></span>  
  
3.  <span data-ttu-id="b2a96-188">Sales を **[値]** にドラッグして [Sum(Quantity)] の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-188">Drag Sales to **Values** and place below [Sum(Quantity)].</span></span>  
  
     <span data-ttu-id="b2a96-189">Sales は Sum 関数を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-189">Sales is aggregated by the Sum function.</span></span> <span data-ttu-id="b2a96-190">値は [Sum(Sales)] です。</span><span class="sxs-lookup"><span data-stu-id="b2a96-190">The value is [Sum(Sales)].</span></span>  
  
     <span data-ttu-id="b2a96-191">手順 1. ～ 3. で、テーブルに表示するデータが指定されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-191">Steps 1, 2, and 3 specify the data to display in the table.</span></span>  
  
4.  <span data-ttu-id="b2a96-192">SalesDate を **[行グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-192">Drag SalesDate to **Row groups**.</span></span>  
  
5.  <span data-ttu-id="b2a96-193">Subcategory を **[行グループ]** にドラッグして SalesDate の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-193">Drag Subcategory to **Row groups** and place below SalesDate.</span></span>  
  
     <span data-ttu-id="b2a96-194">手順 4. および 5. で、フィールドの値がまず日付でまとめられ、次にその日付の製品サブカテゴリでまとめられます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-194">Steps 4 and 5 organize the values for the fields first by date, and then by product subcategory for that date.</span></span>  
  
6.  <span data-ttu-id="b2a96-195">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-195">Click **Next**.</span></span>  
  
##  <a name="1d-add-subtotal-and-total-rows-in-the-table-wizard"></a><a name="Subtotals"></a><span data-ttu-id="b2a96-196">引か.</span><span class="sxs-lookup"><span data-stu-id="b2a96-196">1d.</span></span> <span data-ttu-id="b2a96-197">テーブル ウィザードで小計行と合計行を追加する</span><span class="sxs-lookup"><span data-stu-id="b2a96-197">Add Subtotal and Total Rows in the Table Wizard</span></span>  
 <span data-ttu-id="b2a96-198">グループを作成したら、フィールドの集計値を表示する行を追加して書式を設定できます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-198">After you create groups, you can add and format rows on which to display aggregate values for the fields.</span></span> <span data-ttu-id="b2a96-199">すべてのデータを表示するか、グループ化されたデータの展開と折りたたみをユーザーが対話的に行えるようにするかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-199">You can choose whether to show all the data or to let a user expand and collapse grouped data interactively.</span></span>  
  
#### <a name="to-add-subtotals-and-totals"></a><span data-ttu-id="b2a96-200">小計と合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-200">To add subtotals and totals</span></span>  
  
1.  <span data-ttu-id="b2a96-201">[**レイアウトの選択**] ページの [**オプション**] で、[**小計と総計を表示**する] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-201">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
2.  <span data-ttu-id="b2a96-202">**[ブロック、小計は下]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-202">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
     <span data-ttu-id="b2a96-203">ウィザードのプレビュー ペインに、5 行を含むテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-203">The wizard Preview pane displays a table with five rows.</span></span> <span data-ttu-id="b2a96-204">レポートを実行すると、各行は次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-204">When you run the report, each row will display in the following way:</span></span>  
  
    1.  <span data-ttu-id="b2a96-205">1 行目はテーブルで 1 回表示され、列見出しを示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-205">The first row will repeat once for the table to show column headings.</span></span>  
  
    2.  <span data-ttu-id="b2a96-206">2 行目は販売注文の行アイテムごとに 1 回表示され、製品名、注文数量、および行の合計を示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-206">The second row will repeat once for each line item in the sales order and display the product name, order quantity, and line total.</span></span>  
  
    3.  <span data-ttu-id="b2a96-207">3 行目は販売注文ごとに 1 回表示され、注文あたりの小計を示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-207">The third row will repeat once for each sales order to display subtotals per order.</span></span>  
  
    4.  <span data-ttu-id="b2a96-208">4 行目は注文日ごとに 1 回表示され、1 日あたりの小計を示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-208">The fourth row will repeat once for each order date to display the subtotals per day.</span></span>  
  
    5.  <span data-ttu-id="b2a96-209">5 行目はテーブルで 1 回表示され、総計を示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-209">The fifth row will repeat once for the table to display the grand totals.</span></span>  
  
3.  <span data-ttu-id="b2a96-210">**[グループの展開/折りたたみ]** オプションをオフにします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-210">Clear the option **Expand/collapse groups**.</span></span> <span data-ttu-id="b2a96-211">このチュートリアルで作成するレポートでは、ユーザーが親グループ階層を展開して子グループ行および詳細行を表示できるようにするドリル ダウン機能は使用されません。</span><span class="sxs-lookup"><span data-stu-id="b2a96-211">In this tutorial, the report you create does not use the drilldown feature that lets a user expand a parent group hierarchy to display child group rows and detail rows.</span></span>  
  
4.  <span data-ttu-id="b2a96-212">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-212">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style-in-the-table-wizard"></a><a name="Style"></a><span data-ttu-id="b2a96-213">1e.</span><span class="sxs-lookup"><span data-stu-id="b2a96-213">1e.</span></span> <span data-ttu-id="b2a96-214">テーブル ウィザードでスタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="b2a96-214">Choose a Style in the Table Wizard</span></span>  
 <span data-ttu-id="b2a96-215">スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-215">A style specifies a font style, a set of colors, and a border style.</span></span>  
  
#### <a name="to-specify-a-table-style"></a><span data-ttu-id="b2a96-216">テーブルのスタイルを指定するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-216">To specify a table style</span></span>  
  
1.  <span data-ttu-id="b2a96-217">[**スタイルの選択**] ページのスタイルペインで、[海上] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-217">On the **Choose a Style** page, in the Styles pane, select Ocean.</span></span>  
  
     <span data-ttu-id="b2a96-218">プレビュー ペインにそのスタイルのテーブルのサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-218">The Preview pane displays a sample of the table with that style.</span></span>  
  
2.  <span data-ttu-id="b2a96-219">必要に応じて、他のスタイルをクリックして、そのスタイルが適用されたサンプルを表示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-219">Optionally, click the other styles to see the sample with them applied.</span></span>  
  
3.  <span data-ttu-id="b2a96-220">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-220">Click **Finish**.</span></span>  
  
 <span data-ttu-id="b2a96-221">テーブルがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-221">The table is added to the design surface.</span></span> <span data-ttu-id="b2a96-222">テーブルには 5 列および 5 行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b2a96-222">The table has 5 columns and 5 rows.</span></span> <span data-ttu-id="b2a96-223">行グループ ペインに、SalesDate、Subcategory、および Details の 3 つの行グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-223">The Row Groups pane shows three row groups: SalesDate, Subcategory, and Details.</span></span> <span data-ttu-id="b2a96-224">詳細データは、データセット クエリによって取得されるすべてのデータです。</span><span class="sxs-lookup"><span data-stu-id="b2a96-224">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
##  <a name="2-format-data-as-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="b2a96-225">2. データを通貨として書式設定する</span><span class="sxs-lookup"><span data-stu-id="b2a96-225">2. Format Data as Currency</span></span>  
 <span data-ttu-id="b2a96-226">既定では、Sales フィールドの集計データは通常の数値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-226">By default, the summary data for the Sales field displays a general number.</span></span> <span data-ttu-id="b2a96-227">このフィールドを書式設定して、数値を通貨として表示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-227">Format it to display the number as currency.</span></span> <span data-ttu-id="b2a96-228">書式設定したテキスト ボックスおよびプレースホルダー テキストのサンプル値を表示するには、 **[プレースホルダーのスタイル]** の設定を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-228">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="b2a96-229">通貨フィールドを書式設定するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-229">To format a currency field</span></span>  
  
1.  <span data-ttu-id="b2a96-230">デザインビューに切り替えるには、[**デザイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-230">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="b2a96-231">[Sales] 列の 2 行目 (列見出しの次の行) のセルをクリックして下にドラッグし、 `[Sum(Sales)]`が格納されたすべてのセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-231">Click the cell in the second row (under the column headings row) in the Sales column and drag down to select all cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="b2a96-232">**[ホーム]** タブの **[数値]** グループで、 **[通貨]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-232">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="b2a96-233">書式設定された通貨を表示するようにセルが変化します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-233">The cells change to show the formatted currency.</span></span>  
  
     <span data-ttu-id="b2a96-234">地域設定が英語 (米国) の場合、既定のサンプル テキストは [**$12,345.00**] です。</span><span class="sxs-lookup"><span data-stu-id="b2a96-234">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="b2a96-235">通貨値の例が表示されない場合は、[**数値**] グループの [**プレースホルダーのスタイル**] をクリックし、[**サンプルの値**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-235">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="b2a96-236">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-236">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="b2a96-237">Sales の集計値が通貨として表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-237">The summary values for Sales display as currency.</span></span>  
  
##  <a name="3-format-data-as-date"></a><a name="FormatDate"></a><span data-ttu-id="b2a96-238">3. データを日付として書式設定する</span><span class="sxs-lookup"><span data-stu-id="b2a96-238">3. Format Data as Date</span></span>  
 <span data-ttu-id="b2a96-239">既定では、SalesDate フィールドには日付と時刻の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-239">By default, the SalesDate field displays both date and time information.</span></span> <span data-ttu-id="b2a96-240">このフィールドを書式設定して、日付のみを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-240">You can format them to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a><span data-ttu-id="b2a96-241">日付フィールドの書式を既定の書式に設定するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-241">To format a date field as the default format</span></span>  
  
1.  <span data-ttu-id="b2a96-242">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="b2a96-242">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b2a96-243">`[SalesDate]`が格納されたセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-243">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="b2a96-244">リボンの [**ホーム**] タブの [**数値**] グループで、ドロップダウンリストから [**日付**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-244">On the Ribbon, on the **Home** tab, in the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="b2a96-245">セルに、日付の例として **[2000/1/31]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-245">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="b2a96-246">日付の例が表示されない場合は、 **[数値]** グループの **[プレースホルダーのスタイル]** をクリックし、 **[サンプルの値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-246">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="b2a96-247">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-247">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b2a96-248">SalesDate の値が、既定の日付の書式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-248">The SalesDate values display in the default date format.</span></span>  
  
#### <a name="to-change-the-date-format-to-a-custom-format"></a><span data-ttu-id="b2a96-249">日付の書式をカスタム書式に変更するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-249">To change the date format to a custom format</span></span>  
  
1.  <span data-ttu-id="b2a96-250">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="b2a96-250">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b2a96-251">`[SalesDate]`が格納されたセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-251">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="b2a96-252">[**ホーム**] タブの [**数値**] グループで、[] ダイアログボックスランチャーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-252">On the **Home** tab, in the **Number** group, click the dialog box launcher.</span></span>  
  
     <span data-ttu-id="b2a96-253">起動ツールは、そのグループの右隅にある小さな矢印です。</span><span class="sxs-lookup"><span data-stu-id="b2a96-253">The launcher is the small arrow in the right-hand corner of the group.</span></span> <span data-ttu-id="b2a96-254">**[テキスト ボックスのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-254">The **Text Box Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="b2a96-255">[カテゴリ] ペインで、 **[日付]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-255">In the Category pane, verify that **Date** is selected.</span></span>  
  
5.  <span data-ttu-id="b2a96-256">**[型]** ペインで **[2000 年 1 月 31 日]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-256">In the **Type** pane, select **January 31, 2000**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="b2a96-257">セルに、日付の例として **[2000 年 1 月 31 日]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-257">The cell displays the example date **[January 31, 2000]**.</span></span>  
  
7.  <span data-ttu-id="b2a96-258">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-258">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="b2a96-259">SalesDate の値が、月の数字ではなく月の名前で表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-259">The SalesDate value displays with the name of the month instead of the number for the month.</span></span>  
  
##  <a name="4-change-column-widths"></a><a name="Width"></a><span data-ttu-id="b2a96-260">4. 列幅を変更する</span><span class="sxs-lookup"><span data-stu-id="b2a96-260">4. Change Column Widths</span></span>  
 <span data-ttu-id="b2a96-261">テーブルの各セルには、既定でテキスト ボックスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-261">By default, each cell in a table contains a text box.</span></span> <span data-ttu-id="b2a96-262">テキスト ボックスは、ページを表示するときにテキストに合わせて垂直方向に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-262">A text box expands vertically to accommodate text when the page is rendered.</span></span> <span data-ttu-id="b2a96-263">表示されるレポートでは、各行がその行で最も高いテキスト ボックスの高さに拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-263">In the rendered report, each row expands to the height of the tallest rendered text box in the row.</span></span> <span data-ttu-id="b2a96-264">デザイン画面の行の高さは、表示されるレポートの行の高さには影響しません。</span><span class="sxs-lookup"><span data-stu-id="b2a96-264">The height of the row on the design surface has no affect on the height of the row in the rendered report.</span></span>  
  
 <span data-ttu-id="b2a96-265">各行の垂直方向の領域を小さくするには、列の幅を広げ、列で想定されるテキスト ボックスの内容が 1 行に収まるようにします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-265">To reduce the amount of vertical space each row takes, expand the column width to accommodate the expected contents of the text boxes in the column on one line.</span></span>  
  
#### <a name="to-change-the-width-of-table-columns"></a><span data-ttu-id="b2a96-266">テーブル列の幅を変更するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-266">To change the width of table columns</span></span>  
  
1.  <span data-ttu-id="b2a96-267">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="b2a96-267">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b2a96-268">テーブルをクリックし、列ハンドルおよび行ハンドルをテーブルの上部および横に表示します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-268">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="b2a96-269">テーブルの上と横のグレーのバーは、列および行ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="b2a96-269">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
3.  <span data-ttu-id="b2a96-270">列ハンドルの間の罫線をポイントします。カーソルが 2 方向の矢印の形状に変化します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-270">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="b2a96-271">列をドラッグして、目的のサイズに変更します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-271">Drag the columns to the size you want.</span></span> <span data-ttu-id="b2a96-272">たとえば、製品名が 1 行に表示されるように Product 列を広げます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-272">For example, expand the column for Product so that the product name displays on one line.</span></span>  
  
4.  <span data-ttu-id="b2a96-273">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-273">Click **Run** to preview your report.</span></span>  
  
##  <a name="5-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="b2a96-274">5. レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="b2a96-274">5. Add a Report Title</span></span>  
 <span data-ttu-id="b2a96-275">レポート タイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-275">A report title appears at the top of the report.</span></span> <span data-ttu-id="b2a96-276">レポート ヘッダーがあれば、そこにレポート タイトルを配置します。レポート ヘッダーを使用しない場合は、レポート本文の一番上のテキスト ボックスに配置します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-276">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="b2a96-277">このチュートリアルでは、自動的にレポート本文の一番上に配置されるテキスト ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-277">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="b2a96-278">テキストの語句や文字のフォントのスタイル、サイズ、および色を変更して、テキストをさらに強調することもできます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-278">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="b2a96-279">詳細については、「[テキスト ボックス内のテキストの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2a96-279">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="b2a96-280">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-280">To add a report title</span></span>  
  
1.  <span data-ttu-id="b2a96-281">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-281">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="b2a96-282">「 **Product Sales**」と入力し、テキスト ボックスの外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-282">Type **Product Sales**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="b2a96-283">**Product Sales** が含まれているテキスト ボックスを右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-283">Right-click the text box that contains **Product Sales** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="b2a96-284">**[テキスト ボックスのプロパティ]** ダイアログ ボックスで、 **[フォント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-284">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="b2a96-285">**[サイズ]** ボックスの一覧の **[18pt]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-285">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="b2a96-286">**[色]** ボックスの一覧の **[コーンフラワー ブルー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-286">In the **Color** list, select **Cornflower Blue**.</span></span>  
  
7.  <span data-ttu-id="b2a96-287">**[太字]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-287">Select **Bold**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-save-the-report"></a><a name="Save"></a><span data-ttu-id="b2a96-288">6. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="b2a96-288">6. Save the Report</span></span>  
 <span data-ttu-id="b2a96-289">レポートをレポート サーバーまたは自分のコンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-289">Save the report to a report server or your computer.</span></span> <span data-ttu-id="b2a96-290">レポート サーバーに保存しない場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のいくつかの機能 (レポート パーツ、サブレポートなど) が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b2a96-290">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="b2a96-291">レポート サーバーにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-291">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="b2a96-292">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-292">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="b2a96-293">**[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-293">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="b2a96-294">レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-294">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="b2a96-295">"レポート サーバーに接続しています" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-295">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="b2a96-296">接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-296">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="b2a96-297">**[名前]** に入力されている既定の名前を「 **Product Sales**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-297">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
5.  <span data-ttu-id="b2a96-298">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-298">Click **Save**.</span></span>  
  
 <span data-ttu-id="b2a96-299">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-299">The report is saved to the report server.</span></span> <span data-ttu-id="b2a96-300">接続しているレポート サーバーの名前がウィンドウ下部のステータス バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-300">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="b2a96-301">コンピューターにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-301">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="b2a96-302">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-302">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="b2a96-303">**[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、レポートを保存するフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-303">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="b2a96-304">**[名前]** に入力されている既定の名前を「 **Product Sales**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-304">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
4.  <span data-ttu-id="b2a96-305">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-305">Click **Save**.</span></span>  
  
##  <a name="7-export-the-report"></a><a name="Export"></a><span data-ttu-id="b2a96-306">7. レポートをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="b2a96-306">7. Export the Report</span></span>  
 <span data-ttu-id="b2a96-307">レポートは、Microsoft Excel や CSV (コンマ区切り) 形式など、別の形式にエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-307">Reports can be exported to different formats such Microsoft Excel and comma separated value (CSV).</span></span> <span data-ttu-id="b2a96-308">詳細については、「[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2a96-308">For more information, see [Exporting Reports &#40;Report Builder and SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b2a96-309">このチュートリアルでは、レポートを Excel にエクスポートします。また、レポートのプロパティを設定して、ブック見出しに独自の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-309">In this tutorial, you will export the report to Excel and set a property on the report to provide a custom name for the workbook tab.</span></span>  
  
#### <a name="to-specify-the-workbook-tab-name"></a><span data-ttu-id="b2a96-310">ブック見出しの名前を指定するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-310">To specify the workbook tab name</span></span>  
  
1.  <span data-ttu-id="b2a96-311">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="b2a96-311">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b2a96-312">レポート外の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-312">Click anywhere outside the report.</span></span>  
  
3.  <span data-ttu-id="b2a96-313">.[プロパティ] ペインで、[InitialPageName] プロパティを探し、「 **Product Sales Excel**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-313">.In the Properties pane, locate the InitialPageName property and type **Product Sales Excel**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2a96-314">プロパティペインが表示されていない場合は、リボンの [表示] タブをクリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-314">If the Properties pane is not visible, click the View tab on the ribbon, and then click **Properties**.</span></span>  
  
#### <a name="to-export-a-report-to-excel"></a><span data-ttu-id="b2a96-315">レポートを Excel にエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="b2a96-315">To export a report to Excel</span></span>  
  
1.  <span data-ttu-id="b2a96-316">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-316">Click **Run** to preview the report.</span></span>  
  
2.  <span data-ttu-id="b2a96-317">.リボンの [**エクスポート**] をクリックし、[ **Excel**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-317">.On the ribbon, click **Export**, and then click **Excel**.</span></span>  
  
     <span data-ttu-id="b2a96-318">**[名前を付けて保存]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="b2a96-318">The **Save As** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b2a96-319">**Documents**フォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-319">Browse to the **Documents** folder.</span></span>  
  
4.  <span data-ttu-id="b2a96-320">[**ファイル名**] ボックスに「 **Product Sales Excel**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-320">In the **File name** text box, type **Product Sales Excel**.</span></span>  
  
5.  <span data-ttu-id="b2a96-321">ファイルの種類が**Excel ブック**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-321">Verify that the file type is **Excel Workbook**.</span></span>  
  
6.  <span data-ttu-id="b2a96-322">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-322">Click **Save**.</span></span>  
  
#### <a name="to-view-the-report-in-excel"></a><span data-ttu-id="b2a96-323">Excel でレポートを表示するには</span><span class="sxs-lookup"><span data-stu-id="b2a96-323">To view the report in Excel</span></span>  
  
1.  <span data-ttu-id="b2a96-324">**Documents**フォルダーを開き、[ **Product Sales Excel.xlsx**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a96-324">Open the **Documents** folder and double click **Product Sales Excel.xlsx**.</span></span>  
  
2.  <span data-ttu-id="b2a96-325">ブック見出しの名前が「 **Product Sales Excel**」であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a96-325">Verify that the name of the workbook tab is **Product Sales Excel**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b2a96-326">次の手順</span><span class="sxs-lookup"><span data-stu-id="b2a96-326">Next Steps</span></span>  
 <span data-ttu-id="b2a96-327">これで、基本的なテーブル レポートを作成する方法のチュートリアルは終了です。</span><span class="sxs-lookup"><span data-stu-id="b2a96-327">This concludes the walkthrough for how to create a basic table report.</span></span> <span data-ttu-id="b2a96-328">テーブルの詳細については、「[テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2a96-328">For more information about tables, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a96-329">参照</span><span class="sxs-lookup"><span data-stu-id="b2a96-329">See Also</span></span>  
 <span data-ttu-id="b2a96-330">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="b2a96-330">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="b2a96-331">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="b2a96-331">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
