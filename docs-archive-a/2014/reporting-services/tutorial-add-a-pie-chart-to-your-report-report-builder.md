---
title: 'チュートリアル: レポートへの円グラフの追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eaadf7bf-c312-428a-b214-0a1fbf959c3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 318370b185dcd75a8c3c54be49c47756bad5f3c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720961"
---
# <a name="tutorial-add-a-pie-chart-to-your-report-report-builder"></a><span data-ttu-id="4811c-102">チュートリアル: レポートへの円グラフの追加 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="4811c-102">Tutorial: Add a Pie Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="4811c-103">円グラフおよびドーナツ グラフは、データを全体に対する比率として表示します。</span><span class="sxs-lookup"><span data-stu-id="4811c-103">Pie charts and doughnut charts display data as a proportion of the whole.</span></span> <span data-ttu-id="4811c-104">円グラフは、主に、グループ間の比較を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-104">Pie charts are most commonly used to make comparisons between groups.</span></span> <span data-ttu-id="4811c-105">円グラフとドーナツグラフは、ピラミッドグラフおよびじょうごグラフと共に、図形グラフと呼ばれるグラフのグループを構成します。</span><span class="sxs-lookup"><span data-stu-id="4811c-105">Pie and doughnut charts, along with pyramid and funnel charts, constitute a group of charts known as shape charts.</span></span> <span data-ttu-id="4811c-106">図形グラフには軸がありません。</span><span class="sxs-lookup"><span data-stu-id="4811c-106">Shape charts have no axes.</span></span> <span data-ttu-id="4811c-107">図形グラフに数値フィールドをドロップすると、それぞれの値の全体に占める比率が計算されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-107">When a numeric field is dropped on a shape chart, the chart calculates the percentage of each value to the total.</span></span>  
  
 <span data-ttu-id="4811c-108">円グラフのデータ ポイントが多すぎると、データ ポイント ラベルが過密状態になって見づらくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4811c-108">If there are too many data points on a pie chart, your data point labels might be too crowded to read.</span></span> <span data-ttu-id="4811c-109">その場合は、折れ線グラフの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="4811c-109">In that case, consider using a line chart.</span></span> <span data-ttu-id="4811c-110">円グラフは、データを少数のデータ ポイントに集計したうえで使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="4811c-110">Consider using pie charts only after you have aggregated your data into a few data points.</span></span>  
  
 <span data-ttu-id="4811c-111">次の図に、ここで作成する円グラフを示します。</span><span class="sxs-lookup"><span data-stu-id="4811c-111">The following illustration shows the pie chart you will create.</span></span>  
  
 <span data-ttu-id="4811c-112">![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")</span><span class="sxs-lookup"><span data-stu-id="4811c-112">![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="4811c-113">学習内容</span><span class="sxs-lookup"><span data-stu-id="4811c-113">What You Will Learn</span></span>  
 <span data-ttu-id="4811c-114">このチュートリアルでは、次の内容を学習します。</span><span class="sxs-lookup"><span data-stu-id="4811c-114">In this tutorial, you will learn how to:</span></span>  
  
1.  [<span data-ttu-id="4811c-115">グラフ ウィザードから円グラフを作成する</span><span class="sxs-lookup"><span data-stu-id="4811c-115">Create a Pie Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="4811c-116">グラフの種類を選択する</span><span class="sxs-lookup"><span data-stu-id="4811c-116">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="4811c-117">各スライスにパーセンテージを表示する</span><span class="sxs-lookup"><span data-stu-id="4811c-117">Display Percentages in Each Slice</span></span>](#Percentages)  
  
4.  [<span data-ttu-id="4811c-118">小さな複数のスライスを 1 つのスライスにまとめる</span><span class="sxs-lookup"><span data-stu-id="4811c-118">Combine Small Slices into One Slice</span></span>](#CombineSlices)  
  
5.  [<span data-ttu-id="4811c-119">描画効果をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="4811c-119">Customize the Drawing Effect</span></span>](#DrawingEffect)  
  
6.  [<span data-ttu-id="4811c-120">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="4811c-120">Add a Report Title</span></span>](#Title)  
  
7.  [<span data-ttu-id="4811c-121">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="4811c-121">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="4811c-122">このチュートリアルでは、ウィザードに関する手順を 2 つにまとめて示します。</span><span class="sxs-lookup"><span data-stu-id="4811c-122">In this tutorial, the steps for the wizard are consolidated into two procedures.</span></span> <span data-ttu-id="4811c-123">レポート サーバーの参照、データ ソースの選択、データセットの作成に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 (レポート ビルダー)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4811c-123">For step-by-step instructions about how to browse to a report server, add a data source, and add a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="4811c-124">このチュートリアルの推定所要時間: 10 分</span><span class="sxs-lookup"><span data-stu-id="4811c-124">Estimated time to complete this tutorial: 10 minutes</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4811c-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="4811c-125">Requirements</span></span>  
 <span data-ttu-id="4811c-126">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4811c-126">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-pie-chart-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="4811c-127">1. グラフウィザードから円グラフを作成する</span><span class="sxs-lookup"><span data-stu-id="4811c-127">1. Create a Pie Chart from the Chart Wizard</span></span>  
 <span data-ttu-id="4811c-128">[作業の開始] ダイアログ ボックスで、グラフ ウィザードを使用して埋め込みデータセットを作成し、共有データ ソースを選択して、円グラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="4811c-128">From the Getting Started dialog box, use the Chart Wizard to create an embedded dataset, choose a shared data source, and create a pie chart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4811c-129">このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="4811c-129">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="4811c-130">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="4811c-130">This makes the query quite long.</span></span> <span data-ttu-id="4811c-131">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="4811c-131">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="4811c-132">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="4811c-132">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="4811c-133">新しいグラフ レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="4811c-133">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="4811c-134">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-134">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="4811c-135">[作業の開始] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-135">The Getting Started dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4811c-136">[はじめに] ダイアログボックスが表示されない場合は、[レポートビルダー] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-136">If the Getting Started dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="4811c-137">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4811c-137">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="4811c-138">右ペインで、 **[グラフ ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-138">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="4811c-139">**[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-139">On the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="4811c-140">**[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-140">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="4811c-141">ユーザー名とパスワードの入力が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="4811c-141">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4811c-142">適切な権限を持っている限り、選択するデータ ソースは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="4811c-142">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="4811c-143">データ ソースからはデータを取得しません。</span><span class="sxs-lookup"><span data-stu-id="4811c-143">You will not be getting data from the data source.</span></span> <span data-ttu-id="4811c-144">詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4811c-144">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="4811c-145">[**クエリのデザイン**] ページで、[**テキストとして編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-145">On the **Design a Query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="4811c-146">次のクエリをクエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4811c-146">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Advanced Digital Camera' AS Product, CAST(254995.21 AS money) AS Sales  
    UNION SELECT 'Slim Digital Camera' AS Product, CAST(164499.04 AS money) AS Sales  
    UNION SELECT 'SLR Digital Camera' AS Product, CAST(782176.79 AS money) AS Sales  
    UNION SELECT 'Lens Adapter' AS Product, CAST(36333.08 AS money) AS Sales  
    UNION SELECT 'Macro Zoom Lens' AS Product, CAST(40199.3 AS money) AS Sales  
    UNION SELECT 'USB Cable' AS Product, CAST(53245.5 AS money) AS Sales  
    UNION SELECT 'Independent Filmmaker Camcorder' AS Product, CAST(452288.0 AS money) AS Sales  
    UNION SELECT 'Full Frame Digital Camera' AS Product, CAST(247250.85 AS money) AS Sales  
    ```  
  
8.  <span data-ttu-id="4811c-147">(省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="4811c-147">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="4811c-148">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-148">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="4811c-149">2. グラフの種類を選択する</span><span class="sxs-lookup"><span data-stu-id="4811c-149">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="4811c-150">あらかじめ定義されているさまざまなグラフの種類から選択できます。</span><span class="sxs-lookup"><span data-stu-id="4811c-150">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-pie-chart"></a><span data-ttu-id="4811c-151">円グラフを追加するには</span><span class="sxs-lookup"><span data-stu-id="4811c-151">To add a pie chart</span></span>  
  
1.  <span data-ttu-id="4811c-152">[**グラフの種類の選択**] ページで、[**円**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-152">On the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span> <span data-ttu-id="4811c-153">**[グラフのフィールドの配置]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="4811c-153">The **Arrange chart fields** page opens.</span></span>  
  
     <span data-ttu-id="4811c-154">**[グラフのフィールドの配置]** ページで、Product フィールドを **[カテゴリ]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4811c-154">On the **Arrange chart fields** page, drag the Product field to the **Categories** pane.</span></span> <span data-ttu-id="4811c-155">カテゴリは円グラフのスライスの数を定義します。</span><span class="sxs-lookup"><span data-stu-id="4811c-155">Categories define the number of slices in the pie chart.</span></span> <span data-ttu-id="4811c-156">この例では、各製品に 1 つずつ、合計 8 個のスライスになります。</span><span class="sxs-lookup"><span data-stu-id="4811c-156">In this example, there will be eight slices, one for each product.</span></span>  
  
2.  <span data-ttu-id="4811c-157">Sales フィールドを **[値]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4811c-157">Drag the Sales field to the **Values** pane.</span></span> <span data-ttu-id="4811c-158">Sales は、サブカテゴリの売上高を表します。</span><span class="sxs-lookup"><span data-stu-id="4811c-158">Sales represents the sales amount for the subcategory.</span></span> <span data-ttu-id="4811c-159">各製品の集計がグラフに表示されるので、[**値**] ペインが表示され `[Sum(Sales)]` ます。</span><span class="sxs-lookup"><span data-stu-id="4811c-159">The **Values** pane displays `[Sum(Sales)]` because the chart displays the aggregate for each product.</span></span>  
  
3.  <span data-ttu-id="4811c-160">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-160">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="4811c-161">[**スタイルの選択**] ページのスタイルペインで、スタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4811c-161">On the **Choose a style** page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="4811c-162">スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="4811c-162">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="4811c-163">スタイルを選択すると、プレビュー ペインにそのスタイルのグラフのサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-163">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
5.  <span data-ttu-id="4811c-164">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-164">Click **Finish**.</span></span>  
  
     <span data-ttu-id="4811c-165">グラフがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-165">The chart is added to the design surface.</span></span>  
  
6.  <span data-ttu-id="4811c-166">グラフをクリックして、グラフのハンドルを表示します。</span><span class="sxs-lookup"><span data-stu-id="4811c-166">Click the chart to display the chart handles.</span></span> <span data-ttu-id="4811c-167">グラフの右下隅をドラッグして、グラフのサイズを大きくします。</span><span class="sxs-lookup"><span data-stu-id="4811c-167">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span> <span data-ttu-id="4811c-168">レポート デザイン画面も、グラフ サイズに合わせて大きくなります。</span><span class="sxs-lookup"><span data-stu-id="4811c-168">Note that the report design surface increases in size to accommodate the chart size.</span></span>  
  
7.  <span data-ttu-id="4811c-169">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="4811c-169">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4811c-170">各製品に 1 つずつ、合計 8 個のスライスを含む円グラフがレポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-170">The report displays the pie chart with eight slices, one for each product.</span></span> <span data-ttu-id="4811c-171">各スライスのサイズはその製品の売上を表します。</span><span class="sxs-lookup"><span data-stu-id="4811c-171">The size of each slice represents the sales for that product.</span></span> <span data-ttu-id="4811c-172">これらのスライスのうち 3 つは、非常に小さくなります。</span><span class="sxs-lookup"><span data-stu-id="4811c-172">Three of the slices are quite thin.</span></span>  
  
##  <a name="3-display-percentages-in-each-slice"></a><a name="Percentages"></a><span data-ttu-id="4811c-173">3. 各スライスにパーセンテージを表示する</span><span class="sxs-lookup"><span data-stu-id="4811c-173">3. Display Percentages in Each Slice</span></span>  
 <span data-ttu-id="4811c-174">円グラフの各スライスには、そのスライスの全体に占めるパーセンテージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="4811c-174">On each slice of the pie, you can display a percentage for this slice compared to the whole pie.</span></span>  
  
#### <a name="to-display-percentages-in-each-slice-of-the-pie-chart"></a><span data-ttu-id="4811c-175">円グラフの各スライスにパーセンテージを表示するには</span><span class="sxs-lookup"><span data-stu-id="4811c-175">To display percentages in each slice of the pie chart</span></span>  
  
1.  <span data-ttu-id="4811c-176">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4811c-176">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4811c-177">円グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-177">Right-click the pie chart and click **Show Data Labels**.</span></span> <span data-ttu-id="4811c-178">グラフにデータ ラベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-178">The data labels appear on the chart.</span></span>  
  
3.  <span data-ttu-id="4811c-179">ラベルを右クリックし、[**系列ラベルのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-179">Right-click a label, and then click **Series Label Properties**.</span></span>  
  
4.  <span data-ttu-id="4811c-180">[ラベルデータ] のドロップダウンボックスから、[ **#PERCENT**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4811c-180">In Label data, from the drop-down box, select **#PERCENT**.</span></span>  
  
     <span data-ttu-id="4811c-181">値をパーセンテージとして表示するには、UseValueAsLabel プロパティを false に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4811c-181">To display values as percentages, the UseValueAsLabel property must be false.</span></span> <span data-ttu-id="4811c-182">**[アクションの確認]** ダイアログでこの値の設定を求めるメッセージが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-182">If you are prompted to set this value in the **Confirm Action** dialog, click **Yes**.</span></span>  
  
5.  <span data-ttu-id="4811c-183">Optionalラベルに表示する小数点以下桁数を指定するには、「」と入力し `#PERCENT{Pn}` ます。ここで、 *n*は、表示する小数点以下の桁数です。</span><span class="sxs-lookup"><span data-stu-id="4811c-183">(Optional) To specify how many decimal places the label shows, type `#PERCENT{Pn}` where *n* is the number of decimal places to display.</span></span> <span data-ttu-id="4811c-184">たとえば、小数点以下の桁数を表示しない場合は、「」と入力 `#PERCENT{P0}` します。</span><span class="sxs-lookup"><span data-stu-id="4811c-184">For example, to display no decimal places, type `#PERCENT{P0}`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4811c-185">**[系列ラベルのプロパティ]** ダイアログ ボックスの **[数値書式]** は、パーセンテージの表示形式には影響しません。</span><span class="sxs-lookup"><span data-stu-id="4811c-185">**Number Format** in the **Series Label Properties** dialog box has no effect when you format percentages.</span></span> <span data-ttu-id="4811c-186">この場合、ラベルの表示形式がパーセンテージに設定されるだけで、円グラフに対する各スライスのパーセンテージが計算されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="4811c-186">This formats the labels as percentages, but does not calculate the percentage of the pie that each slice represents.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="4811c-187">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="4811c-187">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4811c-188">円グラフの各スライスがそれぞれ全体の何パーセントを占めているかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-188">The report displays the percentage of the whole for each pie slice.</span></span>  
  
##  <a name="4-combine-small-slices-into-one-slice"></a><a name="CombineSlices"></a><span data-ttu-id="4811c-189">4. 小さいスライスを1つのスライスにまとめる</span><span class="sxs-lookup"><span data-stu-id="4811c-189">4. Combine Small Slices into One Slice</span></span>  
 <span data-ttu-id="4811c-190">円グラフ内の 3 つのスライスは、非常に小さくなります。</span><span class="sxs-lookup"><span data-stu-id="4811c-190">Three of the slices in the pie are quite small.</span></span> <span data-ttu-id="4811c-191">複数の小さなスライスをまとめて 1 つの大きなスライスで表すことができます。</span><span class="sxs-lookup"><span data-stu-id="4811c-191">You can combine multiple small slices into one larger slice that represents all of them.</span></span>  
  
#### <a name="to-combine-any-slices-on-the-pie-chart-smaller-than-5-percent-into-one-slice"></a><span data-ttu-id="4811c-192">円グラフの 5% 未満のスライスを 1 つのスライスにまとめるには</span><span class="sxs-lookup"><span data-stu-id="4811c-192">To combine any slices on the pie chart smaller than 5 percent into one slice</span></span>  
  
1.  <span data-ttu-id="4811c-193">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4811c-193">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4811c-194">[**表示**] タブの [**表示/非**表示] グループで、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4811c-194">On the **View** tab, in the **Show/Hide** group, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="4811c-195">デザイン画面で、円グラフの任意のスライスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-195">On the design surface, click on any slice of the pie chart.</span></span> <span data-ttu-id="4811c-196">系列のプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-196">The properties for the series are displayed in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="4811c-197">**[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="4811c-197">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
5.  <span data-ttu-id="4811c-198">**[CollectedStyle]** プロパティを **[SingleSlice]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="4811c-198">Set the **CollectedStyle** property to **SingleSlice**.</span></span>  
  
6.  <span data-ttu-id="4811c-199">**[CollectedThreshold]** プロパティが 5 に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4811c-199">Verify that the **CollectedThreshold** property is set to 5.</span></span>  
  
7.  <span data-ttu-id="4811c-200">**[CollectedThresholdUsePercent]** プロパティが **True**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4811c-200">Verify that the **CollectedThresholdUsePercent** property is set to **True**.</span></span>  
  
8.  <span data-ttu-id="4811c-201">リボンの [**ホーム**] タブで、[**実行**] をクリックしてレポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="4811c-201">On the Ribbon, on the **Home** tab, click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4811c-202">凡例に "その他" というカテゴリが追加されています。</span><span class="sxs-lookup"><span data-stu-id="4811c-202">In the legend, the category "Other" now exists.</span></span> <span data-ttu-id="4811c-203">この新しいスライスでは、5% 未満のすべてのスライスが 1 つにまとめられて、円グラフ全体の 6% を占めるスライスが作成されています。</span><span class="sxs-lookup"><span data-stu-id="4811c-203">The new pie slice combines all the slices that were under 5% into one slice that is 6% of the whole pie.</span></span>  
  
##  <a name="5-customize-the-drawing-effect"></a><a name="DrawingEffect"></a><span data-ttu-id="4811c-204">5. 描画効果をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="4811c-204">5. Customize the Drawing Effect</span></span>  
 <span data-ttu-id="4811c-205">グラフ ウィザードの場合、円グラフの既定のスタイルは、凹型の描画効果が特徴的な [オーシャン] です。</span><span class="sxs-lookup"><span data-stu-id="4811c-205">In the Chart Wizard, the default style for a pie chart is Ocean, which features a Concave drawing effect.</span></span> <span data-ttu-id="4811c-206">スタイルは、ウィザードの実行後にも変更できます。</span><span class="sxs-lookup"><span data-stu-id="4811c-206">You can change that after you run the wizard.</span></span>  
  
#### <a name="to-add-a-drawing-effect-to-the-pie-chart"></a><span data-ttu-id="4811c-207">円グラフに描画効果を追加するには</span><span class="sxs-lookup"><span data-stu-id="4811c-207">To add a drawing effect to the pie chart</span></span>  
  
1.  <span data-ttu-id="4811c-208">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4811c-208">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4811c-209">プロパティペインがまだ開いていない場合は、[**表示**] タブで [**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4811c-209">If the Properties pane is not already opened, on the **View** tab, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="4811c-210">円グラフ自体をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-210">Double-click the pie chart itself.</span></span> <span data-ttu-id="4811c-211">プロパティ ペインに、円グラフの系列のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-211">The series properties for the pie chart are shown in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="4811c-212">プロパティ ペインで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="4811c-212">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
5.  <span data-ttu-id="4811c-213">**PieDrawingStyle**を**SoftEdge**に設定します。</span><span class="sxs-lookup"><span data-stu-id="4811c-213">Set the **PieDrawingStyle** to **SoftEdge**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4811c-214">描画効果と 3 次元効果を同時に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="4811c-214">Drawing effects and three-dimensional effects are exclusive options.</span></span> <span data-ttu-id="4811c-215">グラフに3次元効果が適用されている場合、[プロパティ] ペインで**PieDrawingStyle**を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="4811c-215">If a chart has three-dimensional effects applied, **PieDrawingStyle** is not available on the Properties pane.</span></span>  
  
6.  <span data-ttu-id="4811c-216">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="4811c-216">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4811c-217">次の図に、ぼかし効果が適用された円グラフを示します。</span><span class="sxs-lookup"><span data-stu-id="4811c-217">The following illustration shows the pie chart with the soft edge effect.</span></span>  
  
 <span data-ttu-id="4811c-218">![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")</span><span class="sxs-lookup"><span data-stu-id="4811c-218">![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")</span></span>  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="4811c-219">6. レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="4811c-219">6. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="4811c-220">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="4811c-220">To add a report title</span></span>  
  
1.  <span data-ttu-id="4811c-221">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-221">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="4811c-222">「 **Camera and Camcorder Sales**」と入力して Enter キーを押し、さらに「 **As a Percentage of Total Sales**」と入力します。次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-222">Type **Camera and Camcorder Sales**, press ENTER, and then type **As a Percentage of Total Sales**, so it looks like this:</span></span>  
  
     <span data-ttu-id="4811c-223">**Camera and Camcorder Sales**</span><span class="sxs-lookup"><span data-stu-id="4811c-223">**Camera and Camcorder Sales**</span></span>  
  
     <span data-ttu-id="4811c-224">**As a Percentage of Total Sales**</span><span class="sxs-lookup"><span data-stu-id="4811c-224">**As a Percentage of Total Sales**</span></span>  
  
3.  <span data-ttu-id="4811c-225">[**カメラとカムコーダーの売上**] を選択し、リボンの [**ホーム**] タブの [**フォント**] セクションで [**太字**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-225">Select **Camera and Camcorder Sales**, and click the **Bold** button from the **Font** section of the **Home** tab of the ribbon.</span></span>  
  
4.  <span data-ttu-id="4811c-226">**全体の売上に対する比率**としてを選択し、[**ホーム**] タブの [**フォント**] セクションで、フォントサイズを**10**に設定します。</span><span class="sxs-lookup"><span data-stu-id="4811c-226">Select **As a Percentage of Total Sales**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
5.  <span data-ttu-id="4811c-227">(省略可) 2 行のテキストに合わせて、[タイトル] テキスト ボックスの高さを高くする必要が生じる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4811c-227">(Optional) You may need to make the Title text box taller to accommodate the two lines of text.</span></span>  
  
     <span data-ttu-id="4811c-228">このタイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-228">This title will appear at the top of the report.</span></span> <span data-ttu-id="4811c-229">ページ ヘッダーが定義されていないとき、レポート本文の最上部にあるアイテムがレポート ヘッダーに相当します。</span><span class="sxs-lookup"><span data-stu-id="4811c-229">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
6.  <span data-ttu-id="4811c-230">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="4811c-230">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="4811c-231">7. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="4811c-231">7. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="4811c-232">レポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="4811c-232">To save the report</span></span>  
  
1.  <span data-ttu-id="4811c-233">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4811c-233">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4811c-234">レポート ビルダー のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-234">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="4811c-235">**[名前]** に「 **Sales Pie Chart**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="4811c-235">In **Name**, type **Sales Pie Chart**.</span></span>  
  
4.  <span data-ttu-id="4811c-236">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4811c-236">Click **Save**.</span></span>  
  
 <span data-ttu-id="4811c-237">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="4811c-237">Your report is saved on the report server.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4811c-238">次の手順</span><span class="sxs-lookup"><span data-stu-id="4811c-238">Next Steps</span></span>  
 <span data-ttu-id="4811c-239">これで、「レポートへの円グラフの追加」チュートリアルを終了します。</span><span class="sxs-lookup"><span data-stu-id="4811c-239">You have successfully completed the Adding a Pie Chart to Your Report tutorial.</span></span> <span data-ttu-id="4811c-240">グラフの詳細については、「[グラフ (レポート ビルダーおよび SSRS)](report-design/charts-report-builder-and-ssrs.md)」と「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4811c-240">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4811c-241">参照</span><span class="sxs-lookup"><span data-stu-id="4811c-241">See Also</span></span>  
 <span data-ttu-id="4811c-242">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="4811c-242">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="4811c-243">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="4811c-243">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
