---
title: 'チュートリアル: レポートへの横棒グラフの追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6956ebd6-0217-4087-a4fa-5cc1c3804691
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01708ca548c40118daa03fac34d8a323d628b012
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634819"
---
# <a name="tutorial-add-a-bar-chart-to-your-report-report-builder"></a><span data-ttu-id="5f4ed-102">チュートリアル: レポートへの横棒グラフの追加 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="5f4ed-102">Tutorial: Add a Bar Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="5f4ed-103">横棒グラフでは、カテゴリ データが水平方向に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-103">A bar chart displays category data horizontally.</span></span> <span data-ttu-id="5f4ed-104">これは、次のようなことに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-104">This can help to:</span></span>  
  
-   <span data-ttu-id="5f4ed-105">長いカテゴリ名を読みやすくする。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-105">Improve readability of long category names.</span></span>  
  
-   <span data-ttu-id="5f4ed-106">値としてプロットされた時間をわかりやすく示す。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-106">Improve understandability of times plotted as values.</span></span>  
  
-   <span data-ttu-id="5f4ed-107">複数の系列の相対値を比較する。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-107">Compare the relative value of multiple series.</span></span>  
  
 <span data-ttu-id="5f4ed-108">次の図は、ここで作成する横棒グラフを示しています。このグラフでは、2008 年と 2009 年の上位 5 人の販売員の売上をアルファベット順に示します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-108">The following illustration shows the bar chart that you will create, with sales for 2008 and 2009 for the top five salespeople, in alphabetical order.</span></span>  
  
 <span data-ttu-id="5f4ed-109">![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")</span><span class="sxs-lookup"><span data-stu-id="5f4ed-109">![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="5f4ed-110">学習内容</span><span class="sxs-lookup"><span data-stu-id="5f4ed-110">What You Will Learn</span></span>  
 <span data-ttu-id="5f4ed-111">このチュートリアルでは、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="5f4ed-112">グラフ ウィザードからグラフ レポートを作成する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-112">Create a Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="5f4ed-113">グラフの種類を選択する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-113">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="5f4ed-114">すべてのカテゴリ値を縦軸に表示する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-114">Display all Category Values on the Vertical Axis</span></span>](#AllValues)  
  
4.  [<span data-ttu-id="5f4ed-115">縦軸の名前の表示を変更する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-115">Modify the Display of Names on the Vertical Axis</span></span>](#Sort)  
  
5.  [<span data-ttu-id="5f4ed-116">凡例を移動する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-116">Move the Legend</span></span>](#Legend)  
  
6.  [<span data-ttu-id="5f4ed-117">グラフ タイトルを移動する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-117">Move the Chart Title</span></span>](#ChartTitle)  
  
7.  [<span data-ttu-id="5f4ed-118">横軸の形式とラベルを設定する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-118">Format and Label the Horizontal Axis</span></span>](#Horizontal)  
  
8.  [<span data-ttu-id="5f4ed-119">フィルターを追加して上位 5 件の値を表示する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-119">Add a Filter to Display the Top Five Values</span></span>](#Filter)  
  
9. [<span data-ttu-id="5f4ed-120">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-120">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="5f4ed-121">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-121">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="5f4ed-122">このチュートリアルでは、ウィザードに関する複数の手順を 1 つにまとめて示します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-122">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="5f4ed-123">レポート サーバーの参照、データセットの作成、データ ソースの選択に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 (レポート ビルダー)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-123">For step-by-step instructions about how to browse to a report server, create a dataset, and choose a data source, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="5f4ed-124">このチュートリアルの推定所要時間: 15 分</span><span class="sxs-lookup"><span data-stu-id="5f4ed-124">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f4ed-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="5f4ed-125">Requirements</span></span>  
 <span data-ttu-id="5f4ed-126">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-126">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="5f4ed-127">1. グラフウィザードからグラフレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-127">1. Create a Chart Report from the Chart Wizard</span></span>  
 <span data-ttu-id="5f4ed-128">[**はじめに**] ダイアログボックスで、埋め込みデータセットを作成し、共有データソースを選択して、グラフウィザードを使用して横棒グラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-128">From the **Getting Started** dialog box, create an embedded dataset, choose a shared data source, and create a bar chart by using the Chart Wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f4ed-129">このチュートリアルでは、外部のデータ ソースが必要ないようにクエリにデータ値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-129">In this tutorial, the query contains the data values so that it does not need an external data source.</span></span> <span data-ttu-id="5f4ed-130">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-130">This makes the query quite long.</span></span> <span data-ttu-id="5f4ed-131">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-131">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="5f4ed-132">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-132">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="5f4ed-133">新しいグラフ レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-133">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="5f4ed-134">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-134">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="5f4ed-135">[**はじめに**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-135">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5f4ed-136">[**はじめに**] ダイアログボックスが表示されない場合は、[レポートビルダー] ボタンをクリックし、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-136">If the **Getting Started** dialog box does not appear, click the Report Builder button, and then click **New**.</span></span>  
  
2.  <span data-ttu-id="5f4ed-137">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-137">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="5f4ed-138">右ペインで、 **[グラフ ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-138">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="5f4ed-139">**[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-139">On the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="5f4ed-140">**[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-140">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="5f4ed-141">ユーザー名とパスワードの入力が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-141">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5f4ed-142">適切な権限を持っている限り、選択するデータ ソースは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-142">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="5f4ed-143">データ ソースからはデータを取得しません。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-143">You will not be getting data from the data source.</span></span> <span data-ttu-id="5f4ed-144">詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-144">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="5f4ed-145">**[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-145">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="5f4ed-146">次のクエリをクエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-146">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Luis' as FirstName, 'Alverca' as LastName, CAST(170000.00 AS money) AS SalesYear2009, CAST(150000. AS money) AS SalesYear2008  
    UNION SELECT 'Jeffrey' as FirstName, 'Zeng' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(190000. AS money) AS SalesYear2008  
    UNION SELECT 'Houman' as FirstName, 'Pournasseh' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Robin' as FirstName, 'Wood' as LastName, CAST(75000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'Daniela' as FirstName, 'Guaita' as LastName,  CAST(170000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'John' as FirstName, 'Yokim' as LastName, CAST(160000. AS money) AS SalesYear2009, CAST(195000. AS money) AS SalesYear2008  
    UNION SELECT 'Delphine' as FirstName, 'Ribaute' as LastName, CAST(180000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Robert' as FirstName, 'Hernady' as LastName, CAST(140000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Tanja' as FirstName, 'Plate' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(160000. AS money) AS SalesYear2008  
    UNION SELECT 'David' as FirstName, 'Bradley' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Michal' as FirstName, 'Jaworski' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(220000. AS money) AS SalesYear2008  
    UNION SELECT 'Chris' as FirstName, 'Ashton' as LastName, CAST(195000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Pongsiri' as FirstName, 'Hirunyanitiwatna' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(215000. AS money) AS SalesYear2008  
    UNION SELECT 'Brian' as FirstName, 'Burke' as LastName, CAST(187000. AS money) AS SalesYear2009, CAST(207000. AS money) AS SalesYear2008  
    ```  
  
8.  <span data-ttu-id="5f4ed-147">(省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-147">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="5f4ed-148">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-148">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="5f4ed-149">2. グラフの種類を選択する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-149">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="5f4ed-150">あらかじめ定義されているさまざまなグラフの種類から選択できます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-150">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-column-chart"></a><span data-ttu-id="5f4ed-151">縦棒グラフを追加するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-151">To add a column chart</span></span>  
  
1.  <span data-ttu-id="5f4ed-152">**[グラフの種類の選択]** ページでは、縦棒グラフが既定のグラフの種類です。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-152">On the **Choose a chart type** page, the column chart is the default chart type.</span></span>  
  
2.  <span data-ttu-id="5f4ed-153">**[横棒]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-153">Click **Bar**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="5f4ed-154">[**グラフのフィールドの配置**] ページには、**使用可能なフィールド**ウィンドウに FirstName、LastName、SalesYear2009、および SalesYear2008 の4つのフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-154">On the **Arrange chart fields** page, there are four fields in the **Available fields** pane: FirstName, LastName, SalesYear2009, and SalesYear2008.</span></span>  
  
3.  <span data-ttu-id="5f4ed-155">LastName をカテゴリ ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-155">Drag LastName to the Categories pane.</span></span>  
  
4.  <span data-ttu-id="5f4ed-156">SalesYear2009 を値ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-156">Drag SalesYear2009 to the Values pane.</span></span> <span data-ttu-id="5f4ed-157">SalesYear2009 は、2009 年の各販売員の売上高を表します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-157">SalesYear2009 represents the sales amount for each salesperson for the year 2009.</span></span> <span data-ttu-id="5f4ed-158">各製品の集計がグラフに表示されるため、値ペインには " `[Sum(SalesYear2009)]` " と表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-158">The Values pane displays `[Sum(SalesYear2009)]` because the chart displays the aggregate for each product.</span></span>  
  
5.  <span data-ttu-id="5f4ed-159">SalesYear2008 を、値ペインの SalesYear2009 の下にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-159">Drag SalesYear2008 to the Values pane under SalesYear2009.</span></span> <span data-ttu-id="5f4ed-160">SalesYear2008 は、2008 年の各販売員の売上高を表します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-160">SalesYear2008 represents the sales amount for each salesperson for the year 2008.</span></span>  
  
6.  <span data-ttu-id="5f4ed-161">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-161">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="5f4ed-162">[**スタイルの選択**] ページのスタイルペインで、スタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-162">On the **Choose a style** page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="5f4ed-163">スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-163">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="5f4ed-164">スタイルを選択すると、プレビュー ペインにそのスタイルのグラフのサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-164">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
8.  <span data-ttu-id="5f4ed-165">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-165">Click **Finish**.</span></span>  
  
     <span data-ttu-id="5f4ed-166">グラフがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-166">The chart is added to the design surface.</span></span>  
  
9. <span data-ttu-id="5f4ed-167">グラフをクリックして、グラフのハンドルを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-167">Click the chart to display the chart handles.</span></span> <span data-ttu-id="5f4ed-168">グラフの右下隅をドラッグして、グラフのサイズを大きくします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-168">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span>  
  
10. <span data-ttu-id="5f4ed-169">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-169">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="5f4ed-170">2008 年と 2009 年の各販売員の売上を示す横棒グラフがレポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-170">The report displays the bar chart for sales for each sales person for the years 2008 and 2009.</span></span> <span data-ttu-id="5f4ed-171">横棒の長さは、売上総額に対応します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-171">The length of the bar corresponds to the sales total.</span></span>  
  
##  <a name="3-modify-the-display-of-names-on-the-vertical-axis"></a><a name="AllValues"></a><span data-ttu-id="5f4ed-172">3. 縦軸の名前の表示を変更する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-172">3. Modify the Display of Names on the Vertical Axis</span></span>  
 <span data-ttu-id="5f4ed-173">既定では、縦軸の値の一部のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-173">By default, only some of the values on the vertical axis appear.</span></span> <span data-ttu-id="5f4ed-174">すべてのカテゴリを表示するようにグラフを変更できます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-174">You can change the chart to display all categories.</span></span>  
  
#### <a name="to-display-all-sales-persons-along-the-category-axis-of-a-bar-chart"></a><span data-ttu-id="5f4ed-175">横棒グラフのカテゴリ軸に沿ってすべての販売員を表示するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-175">To display all sales persons along the category axis of a bar chart</span></span>  
  
1.  <span data-ttu-id="5f4ed-176">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-176">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="5f4ed-177">縦軸を右クリックし、[**縦軸のプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-177">Right-click the vertical axis, and then click **Vertical Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="5f4ed-178">**[軸の範囲と間隔]** の **[間隔]** ボックスに「 **1**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-178">Under **Axis range and interval**, in the **Interval** box, type **1**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="5f4ed-179">縦軸の**タイトル**を右クリックし、[**軸のタイトルの表示**] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-179">Right-click the vertical **Axis Title** and clear the **Show Axis Title** check box.</span></span>  
  
6.  <span data-ttu-id="5f4ed-180">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-180">Click **Run** to preview the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f4ed-181">縦軸に表示される販売員の名前が読みにくい場合は、グラフを縦方向に大きくするか、軸ラベルの形式オプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-181">If you cannot read the salesperson names on the vertical axis, you can make your chart taller or change the formatting options for the axis labels.</span></span>  
  
###  <a name="display-last-name-and-first-name-on-vertical-axis"></a><a name="CategoryExpression"></a><span data-ttu-id="5f4ed-182">縦軸に姓と名を表示する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-182">Display Last Name and First Name on Vertical Axis</span></span>  
 <span data-ttu-id="5f4ed-183">各販売員の姓と名を含むように、カテゴリ式を変更できます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-183">You can change the category expression to include last name followed by first name of each sales person.</span></span>  
  
##### <a name="to-change-the-category-expression"></a><span data-ttu-id="5f4ed-184">カテゴリ式を変更するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-184">To change the category expression</span></span>  
  
1.  <span data-ttu-id="5f4ed-185">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-185">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="5f4ed-186">グラフをダブルクリックして、 **グラフ データ** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-186">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="5f4ed-187">**[カテゴリ グループ]** 領域で、[LastName] を右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-187">In the **Category Groups** area, right-click [LastName], and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="5f4ed-188">[ラベル] で、式 ([Fx]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-188">In Label, click the expression (Fx) button.</span></span>  
  
5.  <span data-ttu-id="5f4ed-189">次の式を入力します。 `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span><span class="sxs-lookup"><span data-stu-id="5f4ed-189">Type the following expression: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span></span>  
  
     <span data-ttu-id="5f4ed-190">この式は、姓、コンマ、および名を連結します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-190">This expression concatenates the last name, a comma, and the first name.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="5f4ed-191">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-191">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="5f4ed-192">レポートを実行したときに名が表示されない場合は、データを手動で更新します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-192">If the first names do not appear when you run the report, you can refresh the data manually.</span></span> <span data-ttu-id="5f4ed-193">プレビュー モードのまま、 **[実行]** タブの **[ナビゲーション]** グループで、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-193">While still in preview mode, on the **Run** tab in the **Navigation** group, click **Refresh**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f4ed-194">縦軸に表示される販売員の名前が読みにくい場合は、グラフを縦方向に大きくするか、軸ラベルの形式オプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-194">If you cannot read the salesperson names on the vertical axis, you can make your chart taller or change the formatting options for the axis labels.</span></span>  
  
##  <a name="4-change-the-sort-order-for-names-on-the-vertical-axis"></a><a name="Sort"></a><span data-ttu-id="5f4ed-195">4. 縦軸の名前の並べ替え順序を変更する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-195">4. Change the Sort Order for Names on the Vertical Axis</span></span>  
 <span data-ttu-id="5f4ed-196">グラフのデータを並べ替えると、カテゴリ軸の値の順序が変更されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-196">When you sort the data on a chart, you are changing the order of values on the category axis.</span></span>  
  
#### <a name="to-sort-the-names-in-alphabetical-order-on-the-bar-chart"></a><span data-ttu-id="5f4ed-197">横棒グラフで名前をアルファベット順に並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-197">To sort the names in alphabetical order on the bar chart</span></span>  
  
1.  <span data-ttu-id="5f4ed-198">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-198">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="5f4ed-199">グラフをダブルクリックして、 **グラフ データ** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-199">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="5f4ed-200">**[カテゴリ グループ]** 領域で、[LastName] を右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-200">In the **Category Groups** area, right-click [LastName], and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="5f4ed-201">**[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-201">Click **Sorting**.</span></span> <span data-ttu-id="5f4ed-202">**[並べ替えのオプションを変更します]** ページに、並べ替え式の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-202">The **Change sorting options** page displays a list of sort expressions.</span></span> <span data-ttu-id="5f4ed-203">既定では、この一覧には、元のカテゴリ グループの式と同じである 1 つの並べ替え式が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-203">By default, this list has one sort expression that is the same as the original category group expression.</span></span>  
  
5.  <span data-ttu-id="5f4ed-204">[並べ替え] で、式 ([**Fx**]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-204">In Sort by, click the expression (**Fx**) button.</span></span>  
  
6.  <span data-ttu-id="5f4ed-205">次の式を入力します。 `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span><span class="sxs-lookup"><span data-stu-id="5f4ed-205">Type the following expression: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span></span>  
  
7.  <span data-ttu-id="5f4ed-206">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-206">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="5f4ed-207">[**カテゴリグループのプロパティ**] ページに戻り、[**順序**] ボックスの一覧で [ **Z**] を選択します。名前が上から下に順番に表示されるように、アルファベットの逆順を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-207">Back on the **Category Group Properties** page, in the **Order** drop-down list, select **Z to A**. This selects reverse alphabetical order so that the names appear in order from top to bottom.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="5f4ed-208">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-208">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="5f4ed-209">横軸の名前は逆順に並べ替えられ、一番上に**Alerca**があり、一番下に**zeng**が付きます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-209">The names on the horizontal axis are sorted in reverse order, with **Alerca** at the top and **Zeng** at the bottom.</span></span>  
  
##  <a name="5-move-the-legend"></a><a name="Legend"></a><span data-ttu-id="5f4ed-210">5. 凡例を移動する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-210">5. Move the Legend</span></span>  
 <span data-ttu-id="5f4ed-211">グラフの凡例を移動することで、グラフの値を読みやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-211">To improve the readability of the chart values, you might want to move the chart legend.</span></span> <span data-ttu-id="5f4ed-212">たとえば、バーが横方向に表示される横棒グラフでは、グラフ領域の上または下に来るように凡例の位置を変更します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-212">For example, in a bar chart where bars are shown horizontally, you can change the position of the legend so that it is above or below the chart area.</span></span> <span data-ttu-id="5f4ed-213">こうすることで、バーの水平方向のスペースを広げることができます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-213">This gives more horizontal space to the bars.</span></span>  
  
#### <a name="to-display-the-legend-below-the-chart-area-of-a-bar-chart"></a><span data-ttu-id="5f4ed-214">凡例を横棒グラフのグラフ領域の下に表示するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-214">To display the legend below the chart area of a bar chart</span></span>  
  
1.  <span data-ttu-id="5f4ed-215">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-215">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="5f4ed-216">グラフの凡例を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-216">Right-click the legend on the chart.</span></span>  
  
3.  <span data-ttu-id="5f4ed-217">**[凡例のプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-217">Select **Legend Properties**.</span></span>  
  
4.  <span data-ttu-id="5f4ed-218">**[凡例の位置]** で、異なる位置を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-218">For **Legend position**, select a different position.</span></span> <span data-ttu-id="5f4ed-219">たとえば、下部中央の位置を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-219">For example, set the position to the middle bottom option.</span></span>  
  
     <span data-ttu-id="5f4ed-220">凡例をグラフの上または下に配置すると、凡例のレイアウトが縦方向から横方向に変更されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-220">When the legend is placed at the top or bottom of a chart, the layout of the legend changes from vertical to horizontal.</span></span> <span data-ttu-id="5f4ed-221">**[レイアウト]** ドロップダウン リストから、異なるレイアウトを選択できます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-221">You can select a different layout from the **Layout** drop-down list.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="5f4ed-222">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-222">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-title-the-chart"></a><a name="ChartTitle"></a><span data-ttu-id="5f4ed-223">6. グラフのタイトルをする</span><span class="sxs-lookup"><span data-stu-id="5f4ed-223">6. Title the Chart</span></span>  
  
#### <a name="to-change-the-chart-title-above-the-chart-area-of-a-bar-chart"></a><span data-ttu-id="5f4ed-224">横棒グラフのグラフ領域の上に表示されるグラフのタイトルを変更するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-224">To change the chart title above the chart area of a bar chart</span></span>  
  
1.  <span data-ttu-id="5f4ed-225">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-225">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="5f4ed-226">グラフの上部にある [**グラフのタイトル**] というテキストを選択し、「 **Sales for 2008 and 2009**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-226">Select the words **Chart Title** at the top of the chart, and then type the following text: **Sales for 2008 and 2009**.</span></span>  
  
3.  <span data-ttu-id="5f4ed-227">テキスト外の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-227">Click anywhere outside the text.</span></span>  
  
4.  <span data-ttu-id="5f4ed-228">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-228">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a><span data-ttu-id="5f4ed-229">7. 横軸の形式とラベルを設定する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-229">7. Format and Label the Horizontal Axis</span></span>  
 <span data-ttu-id="5f4ed-230">既定では、横軸の値が一般的な形式で表示されます。この場合、グラフのサイズに合わせて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-230">By default, the horizontal axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-the-numbers-on-the-horizontal-axis"></a><span data-ttu-id="5f4ed-231">横軸に表示される数値の書式を変更するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-231">To format the numbers on the horizontal axis</span></span>  
  
1.  <span data-ttu-id="5f4ed-232">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-232">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="5f4ed-233">グラフの底辺に沿った横軸をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-233">Click the horizontal axis along the bottom of the chart to select it.</span></span>  
  
     <span data-ttu-id="5f4ed-234">リボンの [**ホーム**] タブの [**数値**] グループで、[**通貨**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-234">On the ribbon, on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="5f4ed-235">横軸ラベルが通貨に変更されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-235">The horizontal axis labels change to currency.</span></span>  
  
3.  <span data-ttu-id="5f4ed-236">(省略可) 小数点以下の桁を削除します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-236">(Optional) Remove the decimal digits.</span></span> <span data-ttu-id="5f4ed-237">**[通貨]** ボタンの近くにある **[小数点表示桁下げ]** ボタンを 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-237">Near the **Currency** button, click the **Decrease Decimal** button twice.</span></span>  
  
4.  <span data-ttu-id="5f4ed-238">横軸を右クリックし、 **[横軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-238">Right-click the horizontal axis, and click **Horizontal Axis Properties**.</span></span>  
  
5.  <span data-ttu-id="5f4ed-239">[**数値**] タブで、[**値を千単位で表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-239">On the **Number** tab, select **Show values in Thousands.**</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="5f4ed-240">[軸の**タイトル**] を右クリックし、[**軸のタイトルのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-240">Right-click **Axis Title** and click **Axis Title Properties**.</span></span>  
  
8.  <span data-ttu-id="5f4ed-241">[**タイトル**] ボックスに「 **Sales in 千」** と入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-241">In the **Title text** box, type **Sales in thousands** and click **OK**.</span></span>  
  
9. <span data-ttu-id="5f4ed-242">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-242">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="5f4ed-243">レポートの横軸に売上高が千単位の通貨で表示され、小数点以下の桁が省略されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-243">The report displays the sales amount on the horizontal axis as currency in thousands, and has no decimal digits.</span></span>  
  
##  <a name="8-add-a-filter-to-display-the-top-five-values"></a><a name="Filter"></a><span data-ttu-id="5f4ed-244">8. フィルターを追加して上位5つの値を表示する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-244">8. Add a Filter to Display the Top Five Values</span></span>  
 <span data-ttu-id="5f4ed-245">グラフにフィルターを追加して、データセットのどのデータをグラフに含め、どのデータをグラフに含めないかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-245">You can add a filter to the chart to specify which data from the dataset to include or exclude in the chart.</span></span>  
  
#### <a name="to-add-a-filter-and-display-the-top-five-values"></a><span data-ttu-id="5f4ed-246">フィルターを追加して上位 5 件の値を表示するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-246">To add a filter and display the top five values</span></span>  
  
1.  <span data-ttu-id="5f4ed-247">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-247">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="5f4ed-248">グラフをダブルクリックして、 **グラフ データ** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-248">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="5f4ed-249">**[カテゴリ グループ]** 領域で、[LastName] フィールドを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-249">In the **Category Groups** area, right-click the [LastName] field, and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="5f4ed-250">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-250">Click **Filters**.</span></span> <span data-ttu-id="5f4ed-251">**[フィルターを変更します]** ページに、フィルター式の一覧を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-251">The **Change filters** page can display a list of filter expressions.</span></span> <span data-ttu-id="5f4ed-252">既定では、この一覧には何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-252">By default, this list is empty.</span></span>  
  
5.  <span data-ttu-id="5f4ed-253">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-253">Click **Add**.</span></span> <span data-ttu-id="5f4ed-254">新しい空のフィルターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-254">A new blank filter appears.</span></span>  
  
6.  <span data-ttu-id="5f4ed-255">[**式**] に「 **[Sum (SalesYear2009)]**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-255">In **Expression**, type **[Sum(SalesYear2009)]**.</span></span> <span data-ttu-id="5f4ed-256">基になる式 `=Sum(Fields!SalesYear2009.Value)`が作成され、この式は **[fx]** ボタンをクリックすると表示できます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-256">This creates the underlying expression `=Sum(Fields!SalesYear2009.Value)`, which you can see if you click the **fx** button.</span></span>  
  
7.  <span data-ttu-id="5f4ed-257">データ型が **Text**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-257">Verify that the data type is **Text**.</span></span>  
  
8.  <span data-ttu-id="5f4ed-258">**[演算子]** で、ドロップダウン リストから **[上位 N]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-258">In **Operator**, select **Top N** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="5f4ed-259">**[値]** に式「 **=5**」を入力します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-259">In **Value**, type the following expression: **=5**</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="5f4ed-260">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-260">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="5f4ed-261">レポートを実行したときに結果がフィルター選択されない場合は、データを手動で更新します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-261">If the results are not filtered when you run the report, you can refresh the data manually.</span></span> <span data-ttu-id="5f4ed-262">**[実行]** タブの **[ナビゲーション]** グループで、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-262">On the **Run** tab in the **Navigation** group, click **Refresh**.</span></span>  
  
 <span data-ttu-id="5f4ed-263">グラフに、2009 年の売上データから取得された上位 5 人の販売員の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-263">The chart shows the top five salesperson names from the 2009 sales data.</span></span>  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="5f4ed-264">9. レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-264">9. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="5f4ed-265">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-265">To add a report title</span></span>  
  
1.  <span data-ttu-id="5f4ed-266">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-266">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="5f4ed-267">「 **Sales Bar Chart**」と入力し、enter キーを押します。次に、 **2009 の上位5人の**販売者を入力します。次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-267">Type **Sales Bar Chart**, press ENTER, and then type **Top Five Sellers for 2009**, so it looks like this:</span></span>  
  
     <span data-ttu-id="5f4ed-268">**Sales Bar Chart**</span><span class="sxs-lookup"><span data-stu-id="5f4ed-268">**Sales Bar Chart**</span></span>  
  
     <span data-ttu-id="5f4ed-269">**Top Five Sellers for 2009**</span><span class="sxs-lookup"><span data-stu-id="5f4ed-269">**Top Five Sellers for 2009**</span></span>  
  
3.  <span data-ttu-id="5f4ed-270">**[Sales Bar Chart]** を選択し、 **[太字]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-270">Select **Sales Bar Chart**, and click the **Bold** button.</span></span>  
  
4.  <span data-ttu-id="5f4ed-271">**2009 の上位5人の**販売元を選択し、[**ホーム**] タブの [**フォント**] セクションで、フォントサイズを**10**に設定します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-271">Select **Top Five Sellers for 2009**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
5.  <span data-ttu-id="5f4ed-272">(省略可) 2 行のテキストに合わせて、[タイトル] テキスト ボックスの高さを高くする必要が生じる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-272">(Optional) You may need to make the Title text box taller to accommodate the two lines of text.</span></span>  
  
     <span data-ttu-id="5f4ed-273">このタイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-273">This title will appear at the top of the report.</span></span> <span data-ttu-id="5f4ed-274">ページ ヘッダーが定義されていないとき、レポート本文の最上部にあるアイテムがレポート ヘッダーに相当します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-274">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
6.  <span data-ttu-id="5f4ed-275">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-275">Click **Run** to preview the report.</span></span>  
  
##  <a name="10-save-the-report"></a><a name="Save"></a><span data-ttu-id="5f4ed-276">10. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="5f4ed-276">10. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="5f4ed-277">レポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="5f4ed-277">To save the report</span></span>  
  
1.  <span data-ttu-id="5f4ed-278">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-278">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="5f4ed-279">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-279">From the **Report Builder** button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="5f4ed-280">**[名前]** に「 **Sales Bar Chart**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-280">In **Name**, type **Sales Bar Chart**.</span></span>  
  
4.  <span data-ttu-id="5f4ed-281">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-281">Click **Save**.</span></span>  
  
 <span data-ttu-id="5f4ed-282">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-282">Your report is saved on the report server.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5f4ed-283">次の手順</span><span class="sxs-lookup"><span data-stu-id="5f4ed-283">Next Steps</span></span>  
 <span data-ttu-id="5f4ed-284">これで、「レポートへの横棒グラフの追加」チュートリアルを終了します。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-284">You have successfully completed the Adding a Bar Chart to Your Report tutorial.</span></span> <span data-ttu-id="5f4ed-285">グラフの詳細については、「[グラフ (レポート ビルダーおよび SSRS)](report-design/charts-report-builder-and-ssrs.md)」と「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4ed-285">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4ed-286">参照</span><span class="sxs-lookup"><span data-stu-id="5f4ed-286">See Also</span></span>  
 <span data-ttu-id="5f4ed-287">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="5f4ed-287">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="5f4ed-288">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="5f4ed-288">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
