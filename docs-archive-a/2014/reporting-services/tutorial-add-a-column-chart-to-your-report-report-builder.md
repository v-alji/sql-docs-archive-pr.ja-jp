---
title: 'チュートリアル: レポートへの縦棒グラフの追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ef3b3f2872c2f8181296bb05337ca18975ac2f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737861"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a><span data-ttu-id="d3096-102">チュートリアル: レポートへの縦棒グラフの追加 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="d3096-102">Tutorial: Add a Column Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="d3096-103">縦棒グラフでは、カテゴリ別にグループ化された縦棒のセットとして系列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-103">A column chart displays a series as a set of vertical bars that are grouped by category.</span></span> <span data-ttu-id="d3096-104">縦棒グラフは次の場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="d3096-104">A column chart can be useful to:</span></span>  
  
-   <span data-ttu-id="d3096-105">時間の経過に伴うデータの変化を示す。</span><span class="sxs-lookup"><span data-stu-id="d3096-105">Show data changes over a period of time.</span></span>  
  
-   <span data-ttu-id="d3096-106">複数の系列の相対値を比較する。</span><span class="sxs-lookup"><span data-stu-id="d3096-106">Compare the relative value of multiple series.</span></span>  
  
-   <span data-ttu-id="d3096-107">移動平均を表示して傾向を示す。</span><span class="sxs-lookup"><span data-stu-id="d3096-107">Display a moving average to show trends.</span></span>  
  
 <span data-ttu-id="d3096-108">次の図に、これから作成する、移動平均が含まれた縦棒グラフを示します。</span><span class="sxs-lookup"><span data-stu-id="d3096-108">The following illustration shows the column chart you will create, with a moving average.</span></span>  
  
 <span data-ttu-id="d3096-109">![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")</span><span class="sxs-lookup"><span data-stu-id="d3096-109">![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="d3096-110">学習内容</span><span class="sxs-lookup"><span data-stu-id="d3096-110">What You Will Learn</span></span>  
 <span data-ttu-id="d3096-111">このチュートリアルでは、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="d3096-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="d3096-112">グラフ ウィザードからグラフ レポートを作成する</span><span class="sxs-lookup"><span data-stu-id="d3096-112">Create a Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="d3096-113">グラフの種類を選択する</span><span class="sxs-lookup"><span data-stu-id="d3096-113">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="d3096-114">横軸の形式とラベルを設定する</span><span class="sxs-lookup"><span data-stu-id="d3096-114">Format and Label the Horizontal Axis</span></span>](#Horizontal)  
  
4.  [<span data-ttu-id="d3096-115">凡例を移動する</span><span class="sxs-lookup"><span data-stu-id="d3096-115">Move the Legend</span></span>](#Legend)  
  
5.  [<span data-ttu-id="d3096-116">グラフのタイトルを設定する</span><span class="sxs-lookup"><span data-stu-id="d3096-116">Title the Chart</span></span>](#ChartTitle)  
  
6.  [<span data-ttu-id="d3096-117">縦軸の形式とラベルを設定する</span><span class="sxs-lookup"><span data-stu-id="d3096-117">Format and Label the Vertical Axis</span></span>](#Vertical)  
  
7.  [<span data-ttu-id="d3096-118">移動平均を追加する</span><span class="sxs-lookup"><span data-stu-id="d3096-118">Add a Moving Average</span></span>](#Average)  
  
8.  [<span data-ttu-id="d3096-119">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="d3096-119">Add a Report Title</span></span>](#Title)  
  
9. [<span data-ttu-id="d3096-120">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="d3096-120">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="d3096-121">このチュートリアルでは、ウィザードに関する複数の手順を 1 つにまとめて示します。</span><span class="sxs-lookup"><span data-stu-id="d3096-121">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="d3096-122">レポート サーバーの参照、データ ソースの選択、データセットの作成に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 &#40;レポート ビルダー&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3096-122">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="d3096-123">このチュートリアルの推定所要時間: 15 分</span><span class="sxs-lookup"><span data-stu-id="d3096-123">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3096-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="d3096-124">Requirements</span></span>  
 <span data-ttu-id="d3096-125">要件の詳細については、[「チュートリアルの前提条件 (レポート ビルダー)」](../reporting-services/report-builder-tutorials.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3096-125">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="d3096-126">1. グラフウィザードからグラフレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="d3096-126">1. Create a Chart Report from the Chart Wizard</span></span>  
 <span data-ttu-id="d3096-127">[**はじめに**] ダイアログボックスで、グラフウィザードを使用して埋め込みデータセットを作成し、共有データソースを選択して、縦棒グラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3096-127">From the **Getting Started** dialog box, use the Chart Wizard to create an embedded dataset, choose a shared data source, and create a column chart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3096-128">このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="d3096-128">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="d3096-129">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="d3096-129">This makes the query quite long.</span></span> <span data-ttu-id="d3096-130">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="d3096-130">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="d3096-131">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="d3096-131">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="d3096-132">新しいグラフ レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="d3096-132">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="d3096-133">**[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-133">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="d3096-134">[**はじめに**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-134">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3096-135">[**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-135">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="d3096-136">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3096-136">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="d3096-137">右ペインで、 **[グラフ ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-137">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="d3096-138">[**データセットの選択] ページ**で、[**データセットの作成**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-138">On the **Choose a dataset page**, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="d3096-139">**[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="d3096-140">ユーザー名とパスワードの入力が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3096-140">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3096-141">適切な権限を持っている限り、選択するデータ ソースは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="d3096-141">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="d3096-142">データ ソースからはデータを取得しません。</span><span class="sxs-lookup"><span data-stu-id="d3096-142">You will not be getting data from the data source.</span></span> <span data-ttu-id="d3096-143">詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3096-143">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="d3096-144">**[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-144">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="d3096-145">次のクエリをクエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d3096-145">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  <span data-ttu-id="d3096-146">(省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3096-146">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="d3096-147">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-147">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="d3096-148">2. グラフの種類を選択する</span><span class="sxs-lookup"><span data-stu-id="d3096-148">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="d3096-149">あらかじめ定義されているさまざまなグラフの種類から選択できます。</span><span class="sxs-lookup"><span data-stu-id="d3096-149">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-column-chart"></a><span data-ttu-id="d3096-150">縦棒グラフを追加するには</span><span class="sxs-lookup"><span data-stu-id="d3096-150">To add a column chart</span></span>  
  
1.  <span data-ttu-id="d3096-151">**[グラフの種類の選択]** ページでは、縦棒グラフが既定のグラフの種類です。</span><span class="sxs-lookup"><span data-stu-id="d3096-151">On the **Choose a chart type** page, the column chart is the default chart type.</span></span> <span data-ttu-id="d3096-152">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-152">Click **Next**.</span></span>  
  
2.  <span data-ttu-id="d3096-153">**[グラフのフィールドの配置]** ページで、SalesDate フィールドを **[カテゴリ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d3096-153">On the **Arrange chart fields** page, drag the SalesDate field to **Categories**.</span></span> <span data-ttu-id="d3096-154">カテゴリは横軸に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-154">Categories display on the horizontal axis.</span></span>  
  
3.  <span data-ttu-id="d3096-155">Sales フィールドを **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d3096-155">Drag the Sales field to **Values**.</span></span> <span data-ttu-id="d3096-156">販売の合計値の総計が 1 日ごとに集計されるので、 **[値]** ボックスには Sum(Sales) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-156">The **Values** box displays Sum(Sales) because the sum of the sales total value is aggregated for each date.</span></span> <span data-ttu-id="d3096-157">値は縦軸に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-157">Values display on the vertical axis.</span></span>  
  
4.  <span data-ttu-id="d3096-158">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-158">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="d3096-159">[**スタイルの選択**] ページの [スタイル] ボックスで、スタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-159">On the **Choose a Style** page, in the Styles box, select a style.</span></span>  
  
     <span data-ttu-id="d3096-160">スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3096-160">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="d3096-161">スタイルを選択すると、プレビュー ペインにそのスタイルのグラフのサンプルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-161">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
6.  <span data-ttu-id="d3096-162">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-162">Click **Finish**.</span></span>  
  
     <span data-ttu-id="d3096-163">グラフがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-163">The chart is added to the design surface.</span></span>  
  
7.  <span data-ttu-id="d3096-164">グラフをクリックして、グラフのハンドルを表示します。</span><span class="sxs-lookup"><span data-stu-id="d3096-164">Click the chart to display the chart handles.</span></span> <span data-ttu-id="d3096-165">グラフの右下隅をドラッグして、グラフのサイズを大きくします。</span><span class="sxs-lookup"><span data-stu-id="d3096-165">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span> <span data-ttu-id="d3096-166">レポート デザイン画面も、グラフ サイズに合わせて大きくなります。</span><span class="sxs-lookup"><span data-stu-id="d3096-166">Note that the report design surface increases in size to accommodate the chart size.</span></span>  
  
8.  <span data-ttu-id="d3096-167">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d3096-167">Click **Run** to preview the report.</span></span>  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a><span data-ttu-id="d3096-168">3. 横軸の書式を設定してラベルを付ける</span><span class="sxs-lookup"><span data-stu-id="d3096-168">3. Format and Label the Horizontal Axis</span></span>  
 <span data-ttu-id="d3096-169">既定では、横軸の値が一般的な形式で表示されます。この場合、グラフのサイズに合わせて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="d3096-169">By default, the horizontal axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a><span data-ttu-id="d3096-170">横軸に表示される日付の書式を変更するには</span><span class="sxs-lookup"><span data-stu-id="d3096-170">To format a date on the horizontal axis</span></span>  
  
1.  <span data-ttu-id="d3096-171">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-171">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d3096-172">横軸を右クリックし、[**横軸のプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-172">Right-click the horizontal axis, and then click **Horizontal Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="d3096-173">[**数値**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-173">Click **Number**.</span></span>  
  
4.  <span data-ttu-id="d3096-174">[**カテゴリ**] で [**日付**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-174">In **Category**, select **Date**.</span></span>  
  
5.  <span data-ttu-id="d3096-175">**[型]** ボックスで **[2000 年 1 月 31 日]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-175">In the **Type** box, select **31 Jan 2000**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="d3096-176">[ホーム] タブで **[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d3096-176">On the Home tab, click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="d3096-177">選択した日付書式で日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-177">The date displays in the date format that you selected.</span></span> <span data-ttu-id="d3096-178">グラフの横軸を見ると、すべてのカテゴリに対してラベルが表示されているわけではないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="d3096-178">Notice that the chart does not label every category on the horizontal axis.</span></span> <span data-ttu-id="d3096-179">既定では、軸の横に収まるラベルだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-179">By default, only labels that fit next to the axis are included.</span></span>  
  
 <span data-ttu-id="d3096-180">ラベルを回転して間隔を指定することによってラベル表示をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d3096-180">You can customize the label display by rotating the labels and specifying the interval.</span></span>  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a><span data-ttu-id="d3096-181">軸ラベルを回転して横軸の表示間隔を変更するには</span><span class="sxs-lookup"><span data-stu-id="d3096-181">To rotate the axis labels and change the display interval along the horizontal axis</span></span>  
  
1.  <span data-ttu-id="d3096-182">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-182">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d3096-183">横軸のタイトルを右クリックし、[軸の**タイトルの表示**] をクリックしてタイトルを削除します。</span><span class="sxs-lookup"><span data-stu-id="d3096-183">Right-click the horizontal axis title, and then click **Show Axis Title** to remove the title.</span></span> <span data-ttu-id="d3096-184">横軸には日付が表示されるので、タイトルは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d3096-184">Because the horizontal axis displays dates, the title is not needed.</span></span>  
  
3.  <span data-ttu-id="d3096-185">横軸を右クリックし、[横軸の**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-185">Right-click the horizontal axis and then click **Horizontal Axis Properties**.</span></span>  
  
4.  <span data-ttu-id="d3096-186">[軸の**範囲と間隔**] の下の [**軸のオプション**] ページで、[**間隔**] に「 **3** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d3096-186">In the **Axis Options** page under **Axis range and interval**, type **3** for **Interval**.</span></span> <span data-ttu-id="d3096-187">3 日ごとの日付がグラフに表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="d3096-187">The chart will display every third date.</span></span>  
  
5.  <span data-ttu-id="d3096-188">[**ラベル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-188">Click **Labels**.</span></span>  
  
6.  <span data-ttu-id="d3096-189">[**軸ラベルの自動調整オプションの変更**] で、[**自動調整を無効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-189">In **Change axis label auto-fit options**, select **Disable auto-fit**.</span></span>  
  
7.  <span data-ttu-id="d3096-190">**[ラベルの回転角度]** で **[-90]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-190">In **Label rotation angle**, select **-90**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="d3096-191">横軸のサンプル テキストが 90 度回転します。</span><span class="sxs-lookup"><span data-stu-id="d3096-191">The sample text for the horizontal axis rotates by 90 degrees.</span></span>  
  
9. <span data-ttu-id="d3096-192">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d3096-192">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="d3096-193">グラフでは、ラベルが回転して 3 日ごとに表示されています。</span><span class="sxs-lookup"><span data-stu-id="d3096-193">On the chart, the labels are rotated and the label for every third date is shown.</span></span>  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a><span data-ttu-id="d3096-194">4. 凡例を移動する</span><span class="sxs-lookup"><span data-stu-id="d3096-194">4. Move the Legend</span></span>  
 <span data-ttu-id="d3096-195">凡例は、カテゴリと系列データから自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-195">The legend is automatically created from category and series data.</span></span>  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a><span data-ttu-id="d3096-196">凡例を縦棒グラフのグラフ領域の下に移動するには</span><span class="sxs-lookup"><span data-stu-id="d3096-196">To move the legend below the chart area of a column chart</span></span>  
  
1.  <span data-ttu-id="d3096-197">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-197">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d3096-198">グラフの凡例を右クリックし、[**凡例のプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-198">Right-click the legend on the chart, and then click **Legend Properties**.</span></span>  
  
3.  <span data-ttu-id="d3096-199">[**レイアウトと位置**] で、別の位置を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-199">For **Layout and Position**, select a different position.</span></span> <span data-ttu-id="d3096-200">たとえば、下部中央の位置を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-200">For example, set the position to the middle bottom option.</span></span>  
  
     <span data-ttu-id="d3096-201">凡例をグラフの上または下に配置すると、凡例のレイアウトが縦方向から横方向に変更されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-201">When the legend is placed at the top or bottom of a chart, the layout of the legend changes from vertical to horizontal.</span></span> <span data-ttu-id="d3096-202">**[レイアウト]** ドロップダウン リストから、異なるレイアウトを選択できます。</span><span class="sxs-lookup"><span data-stu-id="d3096-202">You can select a different layout from the **Layout** drop-down list.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="d3096-203">(省略可) このチュートリアルではカテゴリが 1 つしかないので、凡例は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d3096-203">(Optional) Because there is only one category in this tutorial, the legend is not needed.</span></span> <span data-ttu-id="d3096-204">凡例を削除するには、凡例を右クリックし、[**凡例の削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-204">To remove the legend, right-click the legend and then click **Delete Legend**.</span></span>  
  
6.  <span data-ttu-id="d3096-205">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d3096-205">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a><span data-ttu-id="d3096-206">5. グラフのタイトルをする</span><span class="sxs-lookup"><span data-stu-id="d3096-206">5. Title the Chart</span></span>  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a><span data-ttu-id="d3096-207">グラフ領域の上に表示されるグラフのタイトルを変更するには</span><span class="sxs-lookup"><span data-stu-id="d3096-207">To change the chart title above the chart area</span></span>  
  
1.  <span data-ttu-id="d3096-208">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-208">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d3096-209">グラフの上部にある [**グラフのタイトル**] というテキストを選択し、「**店舗販売注文合計**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d3096-209">Select the words **Chart Title** at the top of the chart, and then type the following text: **Store Sales Order Totals**.</span></span>  
  
3.  <span data-ttu-id="d3096-210">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d3096-210">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a><span data-ttu-id="d3096-211">6. 縦軸の形式とラベルを設定する</span><span class="sxs-lookup"><span data-stu-id="d3096-211">6. Format and Label the Vertical Axis</span></span>  
 <span data-ttu-id="d3096-212">既定では、縦軸の値が一般的な形式で表示されます。この場合、グラフのサイズに合わせて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="d3096-212">By default, the vertical axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a><span data-ttu-id="d3096-213">縦軸に表示される数値を通貨形式に変更するには</span><span class="sxs-lookup"><span data-stu-id="d3096-213">To format as currency the numbers on the vertical axis</span></span>  
  
1.  <span data-ttu-id="d3096-214">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-214">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d3096-215">グラフの側面に沿った垂直軸のラベルをダブルクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-215">Double-click the labels on the vertical axis along the side of the chart to select them.</span></span>  
  
3.  <span data-ttu-id="d3096-216">リボンの [**ホーム**] タブの [**数値**] グループで、[**通貨**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-216">On the ribbon, on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="d3096-217">軸ラベルの表示が、通貨形式に変更されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-217">The axis labels change to show the currency format.</span></span>  
  
4.  <span data-ttu-id="d3096-218">リボンの [**ホーム**] タブの [**数値**] グループで、[**小数点表示桁下げ**] ボタンを2回クリックして、最も近いドルに丸めた数値を表示します。</span><span class="sxs-lookup"><span data-stu-id="d3096-218">On the ribbon, on the **Home** tab, in the **Number** group, click the **Decrease Decimal** button two times, to show the number rounded to the nearest dollar.</span></span>  
  
5.  <span data-ttu-id="d3096-219">縦軸を右クリックし、[**縦軸のプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-219">Right-click the vertical axis and click **Vertical Axis Properties**.</span></span>  
  
6.  <span data-ttu-id="d3096-220">[**数値**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-220">Click **Number**.</span></span> <span data-ttu-id="d3096-221">[**カテゴリ**] ボックスでは [**通貨**] が既に選択されており、[**小数点以下**桁数] は既に**0** (ゼロ) になっています。</span><span class="sxs-lookup"><span data-stu-id="d3096-221">Note that **Currency** is already selected in the **Category** box, and **Decimal places** is already **0** (zero).</span></span>  
  
7.  <span data-ttu-id="d3096-222">[**値の表示**方法] ボックスで、[**千**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-222">In the **Show Values in** box, click **Thousands**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="d3096-223">グラフの側面に沿った縦軸のタイトルを右クリックし、[**軸のタイトルのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-223">Right-click the vertical axis title along the side of the chart and click **Axis Title Properties**.</span></span>  
  
10. <span data-ttu-id="d3096-224">[**タイトルのテキスト**] フィールドのテキストを「 **Sales Total (1000 単位)**」というテキストに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-224">Replace the text in the **Title text** field with the following text: **Sales Total (in Thousands)**.</span></span> <span data-ttu-id="d3096-225">タイトルの表示形式に関連した各種オプションを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3096-225">You can also specify a variety of options related to how the title is formatted.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="d3096-226">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d3096-226">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a><span data-ttu-id="d3096-227">7. 移動平均を追加する</span><span class="sxs-lookup"><span data-stu-id="d3096-227">7. Add a Moving Average</span></span>  
  
#### <a name="to-add-a-moving-average"></a><span data-ttu-id="d3096-228">移動平均を追加するには</span><span class="sxs-lookup"><span data-stu-id="d3096-228">To add a moving average</span></span>  
  
1.  <span data-ttu-id="d3096-229">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-229">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d3096-230">グラフをダブルクリックして、 **グラフ データ** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="d3096-230">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="d3096-231">[**値**] 領域にある **[Sum (Sales)]** フィールドを右クリックし、[**計算系列の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-231">Right-click the **[Sum(Sales)]** field that is in the **Values** area, and then click **Add Calculated Series**.</span></span>  
  
4.  <span data-ttu-id="d3096-232">**[数式]** で、 **[移動平均]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3096-232">In **Formula**, verify that **Moving average** is selected.</span></span>  
  
5.  <span data-ttu-id="d3096-233">**[数式パラメーターの設定]** の **[期間]** で、 **[4]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-233">In **Set Formula Parameters**, for **Period**, select **4**.</span></span>  
  
6.  <span data-ttu-id="d3096-234">[**罫線**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-234">Click **Border**.</span></span>  
  
7.  <span data-ttu-id="d3096-235">[**線の幅**] で [ **1pt から 3pt**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3096-235">In **Line width**, select **3pt**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="d3096-236">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d3096-236">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="d3096-237">グラフに、4 日ごとに平均値を求めた日付別の売上合計の移動平均を示す線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-237">The chart displays a line that shows the moving average for total sales by date, averaged over every four dates.</span></span>  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="d3096-238">8. レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="d3096-238">8. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="d3096-239">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="d3096-239">To add a report title</span></span>  
  
1.  <span data-ttu-id="d3096-240">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-240">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d3096-241">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-241">On the design surface, click **Click to add title**.</span></span>  
  
3.  <span data-ttu-id="d3096-242">「 **Sales Chart**」と入力し、enter キーを押し、次のように**2009**入力します。</span><span class="sxs-lookup"><span data-stu-id="d3096-242">Type **Sales Chart**, press ENTER, and then type **January to December 2009**, so it looks like this:</span></span>  
  
     <span data-ttu-id="d3096-243">**Sales Chart**</span><span class="sxs-lookup"><span data-stu-id="d3096-243">**Sales Chart**</span></span>  
  
     <span data-ttu-id="d3096-244">**January to December 2009**</span><span class="sxs-lookup"><span data-stu-id="d3096-244">**January to December 2009**</span></span>  
  
4.  <span data-ttu-id="d3096-245">[ **Sales Chart**] を選択し、リボンの [**ホーム**] タブの [**フォント**] セクションで [**太字**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-245">Select **Sales Chart**, and click the **Bold** button in the **Font** section on the **Home** tab of the ribbon.</span></span>  
  
5.  <span data-ttu-id="d3096-246">**1 月から12月 2009**を選択し、[**ホーム**] タブの [**フォント**] セクションで、フォントサイズを**10**に設定します。</span><span class="sxs-lookup"><span data-stu-id="d3096-246">Select **January to December 2009**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
6.  <span data-ttu-id="d3096-247">Optional下部の端をクリックしたときに双方向矢印を下に引いて、2行のテキストに合わせて**タイトル**のテキストボックスの高さを大きくする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3096-247">(Optional) You may need to make the **Title** text box taller to accommodate the two lines of text by pulling down on the double-headed arrows when you click in the middle of the bottom edge.</span></span>  
  
     <span data-ttu-id="d3096-248">このタイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3096-248">This title will appear at the top of the report.</span></span> <span data-ttu-id="d3096-249">ページ ヘッダーが定義されていないとき、レポート本文の最上部にあるアイテムがレポート ヘッダーに相当します。</span><span class="sxs-lookup"><span data-stu-id="d3096-249">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
7.  <span data-ttu-id="d3096-250">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d3096-250">Click **Run** to preview the report.</span></span>  
  
##  <a name="9-save-the-report"></a><a name="Save"></a><span data-ttu-id="d3096-251">9. レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="d3096-251">9. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="d3096-252">レポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="d3096-252">To save the report</span></span>  
  
1.  <span data-ttu-id="d3096-253">レポート デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3096-253">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="d3096-254">レポート ビルダー のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-254">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="d3096-255">**[名前]** に「 **Sales Order Column Chart**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d3096-255">In **Name**, type **Sales Order Column Chart**.</span></span>  
  
4.  <span data-ttu-id="d3096-256">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3096-256">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d3096-257">次の手順</span><span class="sxs-lookup"><span data-stu-id="d3096-257">Next Steps</span></span>  
 <span data-ttu-id="d3096-258">これで、「レポートへの縦棒グラフの追加」チュートリアルを終了します。</span><span class="sxs-lookup"><span data-stu-id="d3096-258">You have successfully completed the Adding a Column Chart to Your Report tutorial.</span></span> <span data-ttu-id="d3096-259">グラフの詳細については、「[グラフ (レポート ビルダーおよび SSRS)](report-design/charts-report-builder-and-ssrs.md)」と「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3096-259">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3096-260">参照</span><span class="sxs-lookup"><span data-stu-id="d3096-260">See Also</span></span>  
 <span data-ttu-id="d3096-261">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="d3096-261">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="d3096-262">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="d3096-262">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
