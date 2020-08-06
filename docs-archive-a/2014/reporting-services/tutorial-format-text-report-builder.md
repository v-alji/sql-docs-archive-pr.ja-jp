---
title: 'チュートリアル: 書式文字列 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c96b500f8aa30b77c78f75ccd1342398fd44eb2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737806"
---
# <a name="tutorial-format-text-report-builder"></a><span data-ttu-id="f0f31-102">チュートリアル: テキストの書式設定 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="f0f31-102">Tutorial: Format Text (Report Builder)</span></span>
  <span data-ttu-id="f0f31-103">このチュートリアルでは、さまざまな方法でテキストの書式を設定する方法について解説します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-103">In this tutorial, you can practice formatting text in various ways.</span></span> <span data-ttu-id="f0f31-104">空のレポートと、データ ソースおよびデータセットを設定した後、必要な手順を選んで進めることができます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-104">After you set up the blank report with the data source and dataset, you can pick and choose the steps that you want to explore.</span></span>  
  
 <span data-ttu-id="f0f31-105">次の図に、ここで作成するレポートと同様のレポートを示します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-105">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="f0f31-106">![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")</span><span class="sxs-lookup"><span data-stu-id="f0f31-106">![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")</span></span>  
  
 <span data-ttu-id="f0f31-107">途中の手順で一度わざと正しくない方法を試し、それがなぜ問題なのかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-107">In one step, you make a mistake on purpose so you can see why it is a mistake.</span></span> <span data-ttu-id="f0f31-108">その後、必要な効果が得られるように問題を修正します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-108">Then you correct the mistake to achieve the desired effect.</span></span>  
  
 <span data-ttu-id="f0f31-109">このチュートリアルで作成するレポートについては、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] レポート ビルダーのサンプル レポートに発展版が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0f31-109">An enhanced version of the report you create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="f0f31-110">このサンプルレポートおよびその他のレポートをダウンロードする方法の詳細については、「[レポートビルダーサンプルレポート](https://go.microsoft.com/fwlink/?LinkId=184851)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f31-110">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="f0f31-111">学習内容</span><span class="sxs-lookup"><span data-stu-id="f0f31-111">What You Will Learn</span></span>  
  
### <a name="set-up-the-report"></a><span data-ttu-id="f0f31-112">レポートを設定する</span><span class="sxs-lookup"><span data-stu-id="f0f31-112">Set Up the Report</span></span>  
 1. [<span data-ttu-id="f0f31-113">データソースとデータセットを含む空のレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="f0f31-113">Create a Blank Report with a Data Source and Dataset</span></span>](#CreateReport)  
  
 2. [<span data-ttu-id="f0f31-114">レポート デザイン画面にフィールドを追加する (正しくない方法と正しい方法)</span><span class="sxs-lookup"><span data-stu-id="f0f31-114">Add a Field to the Report Design Surface (Incorrectly, then Correctly)</span></span>](#AddField)  
  
 3. [<span data-ttu-id="f0f31-115">レポートにテーブルを追加デザインサーフェイス</span><span class="sxs-lookup"><span data-stu-id="f0f31-115">Add a Table to the Report Design Surface</span></span>](#AddTable)  
  
### <a name="pick-and-choose"></a><span data-ttu-id="f0f31-116">選択する</span><span class="sxs-lookup"><span data-stu-id="f0f31-116">Pick and Choose</span></span>  
 [<span data-ttu-id="f0f31-117">レポートへのハイパーリンクの追加</span><span class="sxs-lookup"><span data-stu-id="f0f31-117">Add a Hyperlink to the Report</span></span>](#AddHyperlink)  
  
 [<span data-ttu-id="f0f31-118">レポート内のテキストの回転</span><span class="sxs-lookup"><span data-stu-id="f0f31-118">Rotate Text in the Report</span></span>](#RotateText)  
  
 [<span data-ttu-id="f0f31-119">HTML 形式のテキストの表示</span><span class="sxs-lookup"><span data-stu-id="f0f31-119">Displaying Text with HTML Formatting</span></span>](#FormatHTML)  
  
 [<span data-ttu-id="f0f31-120">通貨の書式設定</span><span class="sxs-lookup"><span data-stu-id="f0f31-120">Format Currency</span></span>](#FormatCurrency)  
  
 [<span data-ttu-id="f0f31-121">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="f0f31-121">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="f0f31-122">このチュートリアルの推定所要時間 : 20 分</span><span class="sxs-lookup"><span data-stu-id="f0f31-122">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0f31-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="f0f31-123">Requirements</span></span>  
 <span data-ttu-id="f0f31-124">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f31-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="create-a-blank-report-with-a-data-source-and-dataset"></a><a name="CreateReport"></a><span data-ttu-id="f0f31-125">データソースとデータセットを含む空のレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="f0f31-125">Create a Blank Report with a Data Source and Dataset</span></span>  
  
#### <a name="to-create-a-blank-report"></a><span data-ttu-id="f0f31-126">空のレポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-126">To create a blank report</span></span>  
  
1.  <span data-ttu-id="f0f31-127">[**スタート**] をクリックし、[**プログラム**]、[レポートビルダー] の順にポイントし、[ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder\*\*\*\*レポートビルダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-127">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0f31-128">**[作業の開始]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-128">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="f0f31-129">表示されない場合は、レポート ビルダーのボタンの **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-129">If it does not, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="f0f31-130">**[作業の開始]** ダイアログ ボックスの左ペインで **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-130">In the left pane of the **Getting Started** dialog box, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="f0f31-131">右ペインで、 **[空のレポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-131">In the right pane, click **Blank Report**.</span></span>  
  
#### <a name="to-create-a-data-source"></a><span data-ttu-id="f0f31-132">データ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-132">To create a data source</span></span>  
  
1.  <span data-ttu-id="f0f31-133">レポートデータペインで、[**新規作成**] をクリックし、[**データソース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-133">In the Report Data pane, click **New**, and then click **Data Source**.</span></span>  
  
2.  <span data-ttu-id="f0f31-134">**[名前]** ボックスに「 **TextDataSource**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-134">In the **Name** box, type: **TextDataSource**</span></span>  
  
3.  <span data-ttu-id="f0f31-135">**[レポートに埋め込まれた接続を使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-135">Click **Use a connection embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="f0f31-136">接続の種類が Microsoft SQL Server であることを確認し、[**接続文字列**] ボックスに「 **Data \<servername> Source =** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-136">Verify that the connection type is Microsoft SQL Server, and then in the **Connection string** box type: **Data Source = \<servername>**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0f31-137">式 \<servername>には、たとえば Report001 など、SQL Server データベース エンジンのインスタンスがインストールされているコンピューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-137">The expression \<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="f0f31-138">このチュートリアルでは、特定のデータは必要ありません。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] データベースへの接続だけが必要です。</span><span class="sxs-lookup"><span data-stu-id="f0f31-138">This tutorial does not need specific data; it just needs a connection to a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span> <span data-ttu-id="f0f31-139">**[データ ソース接続]** の一覧に既にデータ ソース接続が表示されている場合は、データ ソース接続を選択してから次の手順「データセットを作成するには」に進みます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-139">If you already have a data source connection listed under **Data Source Connections**, you can select it and go to the next procedure, "To create a dataset."</span></span> <span data-ttu-id="f0f31-140">詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f31-140">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-create-a-dataset"></a><span data-ttu-id="f0f31-141">データセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-141">To create a dataset</span></span>  
  
1.  <span data-ttu-id="f0f31-142">レポートデータペインで、[**新規作成**] をクリックし、[**データセット**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-142">In the Report Data pane, click **New**, and then click **Dataset**.</span></span>  
  
2.  <span data-ttu-id="f0f31-143">データ ソースが **TextDataSource**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-143">Verify that the data source is **TextDataSource**.</span></span>  
  
3.  <span data-ttu-id="f0f31-144">**[名前]** ボックスに「 **TextDataset**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-144">In the **Name** box, type: **TextDataset.**</span></span>  
  
4.  <span data-ttu-id="f0f31-145">クエリの種類に **[テキスト]** が選択されていることを確認してから、 **[クエリ デザイナー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-145">Verify that the **Text** query type is selected, and then click **Query Designer**.</span></span>  
  
5.  <span data-ttu-id="f0f31-146">**[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-146">Click **Edit as Text**.</span></span>  
  
6.  <span data-ttu-id="f0f31-147">次のクエリをクエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-147">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  <span data-ttu-id="f0f31-148">[実行]\(**!**) をクリックしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-148">Click Run (**!**) to run the query.</span></span>  
  
     <span data-ttu-id="f0f31-149">クエリの結果が、レポートに表示できるデータになります。</span><span class="sxs-lookup"><span data-stu-id="f0f31-149">The query results are the data available to display in your report.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="add-a-field-to-the-report-design-surface"></a><a name="AddField"></a><span data-ttu-id="f0f31-150">レポートにフィールドを追加デザインサーフェイス</span><span class="sxs-lookup"><span data-stu-id="f0f31-150">Add a Field to the Report Design Surface</span></span>  
 <span data-ttu-id="f0f31-151">レポート内にデータセットのフィールドを表示する場合、まず、デザイン画面に直接フィールドをドラッグしたくなるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="f0f31-151">If you want a field from your dataset to appear in a report, your first impulse may be to drag it directly to the design surface.</span></span> <span data-ttu-id="f0f31-152">ここでは、その方法がうまくいかない理由と、正しい方法について学びます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-152">This exercise points out why that doesn't work and what to do instead.</span></span>  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a><span data-ttu-id="f0f31-153">レポートにフィールドを追加する (うまくいかない方法を試す) には</span><span class="sxs-lookup"><span data-stu-id="f0f31-153">To add a field to the report (and get the wrong result)</span></span>  
  
1.  <span data-ttu-id="f0f31-154">[レポート データ] ペインからデザイン画面に **FullName** フィールドをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-154">Drag the **FullName** field from the Report Data pane to the design surface.</span></span>  
  
     <span data-ttu-id="f0f31-155">レポート ビルダーによってテキスト ボックスが作成され、ボックス内に式が \<Expr>として表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-155">Report Builder creates a text box with an expression in it, represented as \<Expr>.</span></span>  
  
2.  <span data-ttu-id="f0f31-156">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-156">Click **Run**.</span></span>  
  
     <span data-ttu-id="f0f31-157">**Fernando Ross**というレコードが1つだけ存在することに注意してください。これは、クエリの最初のレコードのアルファベット順です。</span><span class="sxs-lookup"><span data-stu-id="f0f31-157">Note that there is just one record, **Fernando Ross**, which is alphabetically the first record in the query.</span></span> <span data-ttu-id="f0f31-158">フィールドの表示が繰り返されず、フィールド内の他のレコードが表示されません。</span><span class="sxs-lookup"><span data-stu-id="f0f31-158">The field does not repeat to show the other records in that field.</span></span>  
  
3.  <span data-ttu-id="f0f31-159">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f0f31-159">Click **Design** to return to design view.</span></span>  
  
4.  <span data-ttu-id="f0f31-160">テキスト ボックス内の式 \<Expr> を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-160">Select the expression \<Expr> in the text box.</span></span>  
  
5.  <span data-ttu-id="f0f31-161">プロパティ ペインの **[値]** プロパティが次のように表示されています (プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** チェック ボックスをオンにします)。</span><span class="sxs-lookup"><span data-stu-id="f0f31-161">In the Properties pane, for the **Value** property, you see the following (if you don't see the Properties pane, on the **View** tab, check **Properties**):</span></span>  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
     <span data-ttu-id="f0f31-162">`First` 関数は、フィールド内の最初の値のみを取得するように設計されているので、最初の値のみが取得されました。</span><span class="sxs-lookup"><span data-stu-id="f0f31-162">The `First` function is designed to retrieve only the first value in a field, and that is what it has done.</span></span>  
  
     <span data-ttu-id="f0f31-163">デザイン画面にフィールドを直接ドラッグすることによって、テキスト ボックスが作成されました。</span><span class="sxs-lookup"><span data-stu-id="f0f31-163">Dragging the field directly to the design surface created a text box.</span></span> <span data-ttu-id="f0f31-164">テキスト ボックス自体はデータ領域ではないので、レポート データセットのデータを表示しません。</span><span class="sxs-lookup"><span data-stu-id="f0f31-164">Text boxes by themselves are not data regions, so they do not display data from a report dataset.</span></span> <span data-ttu-id="f0f31-165">テーブル、マトリックス、一覧などのデータ領域のテキスト ボックスが、データを表示します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-165">Text boxes in data regions, such as tables, matrices, and lists, do display data.</span></span>  
  
6.  <span data-ttu-id="f0f31-166">テキスト ボックスを選択して (式を選択している場合は、&lt;localizedText&gt;Esc&lt;/localizedText&gt; キーを押してからテキスト ボックスを選択します)、&lt;localizedText&gt;Del&lt;/localizedText&gt; キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-166">Select the text box (if you have the expression selected, press ESC to select the text box), and press the DELETE key.</span></span>  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a><span data-ttu-id="f0f31-167">レポートにフィールドを追加する (正しい結果を得る) には</span><span class="sxs-lookup"><span data-stu-id="f0f31-167">To add a field to the report (and get the right result)</span></span>  
  
1.  <span data-ttu-id="f0f31-168">リボンの **[挿入]** タブの **[データ領域]** で、 **[一覧]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-168">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **List**.</span></span> <span data-ttu-id="f0f31-169">デザイン画面でマウスをドラッグして、幅約 5 センチ メートル、高さ約 3 センチ メートルのボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-169">Click the design surface, and then drag to create a box that about two inches wide and one inch tall.</span></span>  
  
2.  <span data-ttu-id="f0f31-170">作成したリスト ボックスに [レポート データ] ペインから **FullName** フィールドをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-170">Drag the **FullName** field from the Report Data pane to the list box.</span></span>  
  
     <span data-ttu-id="f0f31-171">今度は、レポート ビルダーによって、 `[FullName]` という式が表示されたテキスト ボックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-171">This time Report Builder creates a text box with the expression `[FullName]` in it.</span></span>  
  
3.  <span data-ttu-id="f0f31-172">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-172">Click **Run**.</span></span>  
  
     <span data-ttu-id="f0f31-173">今回は、ボックスの表示が繰り返され、クエリ内のすべてのレコードが表示されています。</span><span class="sxs-lookup"><span data-stu-id="f0f31-173">Note that this time the box repeats to show all the records in the query.</span></span>  
  
4.  <span data-ttu-id="f0f31-174">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f0f31-174">Click **Design** to return to design view.</span></span>  
  
5.  <span data-ttu-id="f0f31-175">テキスト ボックス内の式を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-175">Select the expression in the text box.</span></span>  
  
6.  <span data-ttu-id="f0f31-176">[プロパティ] ペインの **[値]** プロパティが次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-176">In the Properties pane, for the **Value** property, you see the following:</span></span>  
  
    ```  
    =Fields!FullName.Value  
    ```  
  
     <span data-ttu-id="f0f31-177">テキスト ボックスを一覧データ領域にドラッグすることによって、データセット内のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-177">By dragging the text box to the list data region, you display the data that is in the dataset.</span></span>  
  
7.  <span data-ttu-id="f0f31-178">リスト ボックスを選択し、<localizedText>Del</localizedText> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-178">Select the list box and press the DELETE key.</span></span>  
  
##  <a name="add-a-table-to-the-report-design-surface"></a><a name="AddTable"></a><span data-ttu-id="f0f31-179">レポートにテーブルを追加デザインサーフェイス</span><span class="sxs-lookup"><span data-stu-id="f0f31-179">Add a Table to the Report Design Surface</span></span>  
 <span data-ttu-id="f0f31-180">このテーブルを作成して、ハイパーリンクと回転したテキストを配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-180">Create this table so that you'll have a place to put hyperlinks and rotated text.</span></span>  
  
#### <a name="to-add-a-table-to-the-report"></a><span data-ttu-id="f0f31-181">テーブルをレポートに追加するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-181">To add a table to the report</span></span>  
  
1.  <span data-ttu-id="f0f31-182">[**挿入**] メニューの [**テーブル**] をクリックし、[**テーブルウィザード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-182">On the **Insert** menu, click **Table**, and then click **Table Wizard**.</span></span>  
  
2.  <span data-ttu-id="f0f31-183">テーブルまたはマトリックスの新規作成ウィザードの [**データセットの選択**] ページで、[**このレポートまたは共有データセット内の既存のデータセットを選択する**] をクリックし、[ **textdataset (このレポート)**] をクリックして、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-183">On the **Choose a dataset** page of the New Table or Matrix wizard, click **Choose an existing dataset in this report or a shared dataset**, and click **TextDataset (in this Report)**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="f0f31-184">[**フィールドの配置**] ページで、[**区域**]、[ **LinkText**]、[ **Product** ] の各フィールドを [**行グループ**] にドラッグし、 **Sales**フィールドを [**値**] にドラッグして、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-184">On the **Arrange fields** page, drag the **Territory**, **LinkText**, and **Product** fields to **Row groups**, drag the **Sales** field to **Values**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="f0f31-185">[**レイアウトの選択**] ページで、[**グループの展開/折りたたみ**] チェックボックスをオフにしてテーブル全体を表示し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-185">On the **Choose the layout** page, clear the **Expand/collapse groups** check box so you can see the whole table, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="f0f31-186">[**スタイルの選択**] ページで [**スレート**] をクリックし、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-186">On the **Choose a style** page, click **Slate**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="f0f31-187">テーブルをドラッグして、タイトルのブロックの下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-187">Drag the table so it is below the title block.</span></span>  
  
7.  <span data-ttu-id="f0f31-188">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-188">Click **Run**.</span></span>  
  
     <span data-ttu-id="f0f31-189">テーブルは問題ないように見えますが、合計行が 2 か所に含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0f31-189">The table looks OK, but it has two Total rows.</span></span> <span data-ttu-id="f0f31-190">**LinkText**フィールドには合計行は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f0f31-190">The **LinkText** field doesn't need a Total row.</span></span>  
  
8.  <span data-ttu-id="f0f31-191">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f0f31-191">Click **Design** to return to design view.</span></span>  
  
9. <span data-ttu-id="f0f31-192">が含まれているテキストボックスを右クリック `[LinkText]` し、[**セルの分割**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-192">Right-click the text box that contains `[LinkText]`, and click **Split Cells**.</span></span>  
  
10. <span data-ttu-id="f0f31-193">セルの下にある空のセルを選択 `[LinkText]` し、shift キーを押しながら右側の2つのセル ( **Product**列の**Total**セルと `[Sum(Sales)]` **Sales**列のセル) を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-193">Select the empty cell below the `[LinkText]` cell, and then hold down the SHIFT key and select the two cells to its right: the **Total** cell in the **Product** column and the `[Sum(Sales)]` cell in the **Sales** column.</span></span>  
  
11. <span data-ttu-id="f0f31-194">これら3つのセルを選択した状態で、これらのセルの1つを右クリックし、[**行の削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-194">With those three cells selected, right-click one of those cells and click **Delete Row**.</span></span>  
  
12. <span data-ttu-id="f0f31-195">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-195">Click **Run**.</span></span>  
  
##  <a name="add-a-hyperlink-to-the-report"></a><a name="AddHyperlink"></a><span data-ttu-id="f0f31-196">レポートへのハイパーリンクの追加</span><span class="sxs-lookup"><span data-stu-id="f0f31-196">Add a Hyperlink to the Report</span></span>  
 <span data-ttu-id="f0f31-197">ここでは、前のセクションで作成したテーブルのテキストに、ハイパーリンクを追加します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-197">In this section, you add a hyperlink to text in the table from the previous section.</span></span>  
  
#### <a name="to-add-a-hyperlink-to-the-report"></a><span data-ttu-id="f0f31-198">レポートにハイパーリンクを追加するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-198">To add a hyperlink to the report</span></span>  
  
1.  <span data-ttu-id="f0f31-199">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f0f31-199">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="f0f31-200">`[LinkText]`を含むセルを右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-200">Right-click in the cell containing `[LinkText]`, and click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="f0f31-201">[**テキストボックスのプロパティ**] ボックスで、[**アクション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-201">In the **Text Box Properties** box, click **Action**.</span></span>  
  
4.  <span data-ttu-id="f0f31-202">[ **URL にジャンプ] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-202">Click **Go to URL**.</span></span>  
  
5.  <span data-ttu-id="f0f31-203">[ **Url の選択**] ボックスで [ **url]** をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-203">In the **Select URL** box, click **[URL]**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="f0f31-204">テキストが、他と同じに見えることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="f0f31-204">Note that the text does not look any different.</span></span> <span data-ttu-id="f0f31-205">リンク テキストのように表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0f31-205">You need to make it look like link text.</span></span>  
  
7.  <span data-ttu-id="f0f31-206">[`[LinkText]`] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-206">Select `[LinkText]`.</span></span>  
  
8.  <span data-ttu-id="f0f31-207">[**ホーム**] タブの [**フォント**] セクションで、[**下線**] ボタンをクリックし、[**色**] ボタンの横にあるドロップダウン矢印をクリックして、[**青**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-207">In the **Font** section of the **Home** tab, click the **Underline** button, and then click the drop-down arrow next to the **Color** button, and click **Blue**.</span></span>  
  
9. <span data-ttu-id="f0f31-208">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-208">Click **Run**.</span></span>  
  
     <span data-ttu-id="f0f31-209">テキストがリンクらしく見えるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f0f31-209">The text now looks like a link.</span></span>  
  
10. <span data-ttu-id="f0f31-210">リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-210">Click a link.</span></span> <span data-ttu-id="f0f31-211">コンピューターがインターネットに接続している場合は、レポート ビルダー ヘルプのトピックが表示されたブラウザーが開きます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-211">If the computer is connected to the Internet, a browser will open to a Report Builder Help topic.</span></span>  
  
##  <a name="rotate-text-in-the-report"></a><a name="RotateText"></a><span data-ttu-id="f0f31-212">レポート内のテキストの回転</span><span class="sxs-lookup"><span data-stu-id="f0f31-212">Rotate Text in the Report</span></span>  
 <span data-ttu-id="f0f31-213">ここでは、前のセクションで使用したテーブル内のテキストの一部を回転します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-213">In this section, you rotate some of the text in the table from the previous sections.</span></span>  
  
#### <a name="to-rotate-text"></a><span data-ttu-id="f0f31-214">テキストを回転するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-214">To rotate text</span></span>  
  
1.  <span data-ttu-id="f0f31-215">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f0f31-215">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="f0f31-216">次を含むセルをクリックします。 `[Territory].`</span><span class="sxs-lookup"><span data-stu-id="f0f31-216">Click in the cell containing `[Territory].`</span></span>  
  
3.  <span data-ttu-id="f0f31-217">**[ホーム]** タブの **[フォント]** セクションで、 **[太字]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-217">On the **Home** tab in the **Font** section, click the **Bold** button.</span></span>  
  
4.  <span data-ttu-id="f0f31-218">プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-218">If the Properties pane is not open, on the **View** tab, select the **Properties** check box.</span></span>  
  
5.  <span data-ttu-id="f0f31-219">[プロパティ] ペインで、WritingMode プロパティを見つけます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-219">Locate the WritingMode property in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0f31-220">プロパティ ペインのプロパティがカテゴリごとに整理されている場合、WritingMode は、 **[ローカライズ]** カテゴリ内にあります。</span><span class="sxs-lookup"><span data-stu-id="f0f31-220">When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.</span></span> <span data-ttu-id="f0f31-221">テキストではなくセルを選択してあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-221">Be sure you have selected the cell and not the text.</span></span> <span data-ttu-id="f0f31-222">WritingMode は、テキストではなくテキスト ボックスのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="f0f31-222">WritingMode is a property of the text box, not of the text.</span></span>  
  
6.  <span data-ttu-id="f0f31-223">リストボックスで、[ **Rotate270**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-223">In the list box, click **Rotate270**.</span></span>  
  
7.  <span data-ttu-id="f0f31-224">[**ホーム**] タブの [**段落**] セクションで、**中央**揃えおよび**中央揃え**のボタンをクリックして、セルの中央にあるテキストを垂直方向および水平方向に配置します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-224">On the **Home** tab in the **Paragraph** section, click the **Middle** and **Center** buttons to locate the text in the center of the cell both vertically and horizontally.</span></span>  
  
8.  <span data-ttu-id="f0f31-225">[実行] (**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-225">Click Run (**!**).</span></span>  
  
 <span data-ttu-id="f0f31-226">`[Territory]` セル内のテキストがセルの下から上に向かって縦に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-226">Now the text in the `[Territory]` cell runs vertically from the bottom to the top of the cells.</span></span>  
  
##  <a name="displaying-text-with-html-formatting"></a><a name="FormatHTML"></a><span data-ttu-id="f0f31-227">HTML 形式のテキストの表示</span><span class="sxs-lookup"><span data-stu-id="f0f31-227">Displaying Text with HTML Formatting</span></span>  
  
#### <a name="to-display-text-formatted-as-html"></a><span data-ttu-id="f0f31-228">HTML 形式のテキストを表示するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-228">To display text formatted as HTML</span></span>  
  
1.  <span data-ttu-id="f0f31-229">デザインビューに切り替えるには、[**デザイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-229">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="f0f31-230">**[挿入]** タブで **[テキスト ボックス]** をクリックしてから、デザイン画面のテーブルの下でマウスをドラッグして、幅約 10 センチ メートル、高さ約 8 センチ メートルのボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-230">On the **Insert** tab, click **Text Box**, and then on the design surface, click and drag to create a text box under the table, about four inches wide and three inches tall.</span></span>  
  
3.  <span data-ttu-id="f0f31-231">次のテキストをコピーして、テキスト ボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-231">Copy this text and paste it into the text box:</span></span>  
  
    ```  
    <h4>Limitations of cascading style sheet attributes</h4>  
          <p>Only a basic set of <b>cascading style sheet (CSS)</b> attributes are defined:</p>  
          <ul><li>  
              text-align, text-indent  
            </li><li>  
              font-family, font-size  
            </li><li>  
              color  
            </li><li>  
              padding, padding-bottom, padding-top, padding-right, padding-left  
            </li><li>  
              font-weight  
            </li></ul>  
    ```  
  
4.  <span data-ttu-id="f0f31-232">テキスト ボックス内のすべてのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-232">Select all of the text in the text box.</span></span>  
  
     <span data-ttu-id="f0f31-233">これは、テキスト ボックスではなくテキストのプロパティなので、1 つのテキスト ボックス内にプレーンテキストと HTML タグを使用したテキストの両方のスタイルを混在させることもできます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-233">This is a property of the text, not the text box, so in one text box you could have a mixture of plain text and text that uses HTML tags as styles.</span></span>  
  
5.  <span data-ttu-id="f0f31-234">選択したテキスト全体を右クリックして、 **[テキスト プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-234">Right-click all of the selected text and click **Text Properties**.</span></span>  
  
6.  <span data-ttu-id="f0f31-235">[**全般**] ページの [**マークアップの種類**] で、[html **-html タグをスタイルとして解釈**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-235">On the **General** page, under **Markup type**, click **HTML - Interpret HTML tags as styles**.</span></span>  
  
7.  <span data-ttu-id="f0f31-236">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-236">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="f0f31-237">[実行]\(**!**) をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-237">Click Run (**!**) to preview the report.</span></span>  
  
 <span data-ttu-id="f0f31-238">テキスト ボックス内のテキストが、見出し、段落、箇条書きとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-238">The text in the text box is displayed as a heading, paragraph, and bulleted list.</span></span>  
  
##  <a name="format-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="f0f31-239">通貨の書式設定</span><span class="sxs-lookup"><span data-stu-id="f0f31-239">Format Currency</span></span>  
  
#### <a name="to-format-numbers-as-currency"></a><span data-ttu-id="f0f31-240">数値を通貨として書式設定するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-240">To format numbers as currency</span></span>  
  
1.  <span data-ttu-id="f0f31-241">デザインビューに切り替えるには、[**デザイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-241">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="f0f31-242">テーブルの一番上の `[Sum(Sales)]`が含まれているセルをクリックし、&lt;localizedText&gt;Shift&lt;/localizedText&gt; キーを押しながらテーブルの一番下の `[Sum(Sales)]`が含まれているセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-242">Click the top table cell that contains `[Sum(Sales)]`, hold down the SHIFT key, and click the bottom table cell that contains `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="f0f31-243">**[ホーム]** タブの **[数値]** グループで、 **[通貨]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-243">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>  
  
4.  <span data-ttu-id="f0f31-244">Optional[**ホーム**] タブの [**数値**] グループで、[**プレースホルダーのスタイル**] ボタンをクリックし、[**サンプルの値**] をクリックして、数値の書式設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-244">(Optional) On the **Home** tab, in the **Number** group, click the **Placeholder Styles** button and click **Sample Values** to see how the numbers will be formatted.</span></span>  
  
5.  <span data-ttu-id="f0f31-245">(省略可) **[ホーム]** タブの **[数値]** グループで、 **[小数点表示桁下げ]** ボタンを 2 回クリックして、表示されるドルの値にセントの部分が含まれないようにします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-245">(Optional) On the **Home** tab, in the **Number** group, click the **Decrease Decimals** button twice to display dollar figures with no cents.</span></span>  
  
6.  <span data-ttu-id="f0f31-246">[実行]\(**!**) をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-246">Click Run (**!**) to preview the report.</span></span>  
  
 <span data-ttu-id="f0f31-247">レポートには書式が設定されたデータが表示され、読みやすくなりました。</span><span class="sxs-lookup"><span data-stu-id="f0f31-247">The report now displays formatted data and is easier to read.</span></span>  
  
##  <a name="save-the-report"></a><a name="Save"></a><span data-ttu-id="f0f31-248">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="f0f31-248">Save the Report</span></span>  
 <span data-ttu-id="f0f31-249">レポートは、レポート サーバー、SharePoint ライブラリ、またはコンピューターに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-249">You can save reports to a report server, SharePoint library, or your computer.</span></span>  
  
 <span data-ttu-id="f0f31-250">このチュートリアルでは、レポートをレポート サーバーに保存します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-250">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="f0f31-251">レポート サーバーにアクセスできない場合は、レポートをコンピューターに保存してください。</span><span class="sxs-lookup"><span data-stu-id="f0f31-251">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="f0f31-252">レポート サーバーにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-252">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="f0f31-253">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-253">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="f0f31-254">**[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-254">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="f0f31-255">レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-255">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="f0f31-256">"レポート サーバーに接続しています" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-256">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="f0f31-257">接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-257">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="f0f31-258">**[名前]** に表示されている既定の名前を任意の名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-258">In **Name**, replace the default name with a name of your choosing.</span></span>  
  
5.  <span data-ttu-id="f0f31-259">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-259">Click **Save**.</span></span>  
  
 <span data-ttu-id="f0f31-260">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-260">The report is saved to the report server.</span></span> <span data-ttu-id="f0f31-261">接続しているレポート サーバーの名前がウィンドウ下部のステータス バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f31-261">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="f0f31-262">コンピューターにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="f0f31-262">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="f0f31-263">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-263">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="f0f31-264">**[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、レポートを保存するフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-264">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="f0f31-265">**[名前]** に表示されている既定の名前を任意の名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="f0f31-265">In **Name**, replace the default name with a name of your choosing.</span></span>  
  
4.  <span data-ttu-id="f0f31-266">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0f31-266">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f0f31-267">次の手順</span><span class="sxs-lookup"><span data-stu-id="f0f31-267">Next Steps</span></span>  
 <span data-ttu-id="f0f31-268">レポートビルダーチュートリアルでは、さまざまな方法でテキストを書式設定できます[。自由形式のレポートの作成 &#40;レポートビルダー&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md)の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0f31-268">There are many ways to format text in Report Builder [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) contains more examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f31-269">参照</span><span class="sxs-lookup"><span data-stu-id="f0f31-269">See Also</span></span>  
 <span data-ttu-id="f0f31-270">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="f0f31-270">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="f0f31-271">[レポートアイテムの書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0f31-271">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f0f31-272">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="f0f31-272">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
