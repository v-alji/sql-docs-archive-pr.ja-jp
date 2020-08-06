---
title: 高度な時系列予測 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b614ebdb-07ca-44af-a0ff-893364bd4b71
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 70ebf856ba0782cbf44969aba30602818015582a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720540"
---
# <a name="advanced-time-series-predictions-intermediate-data-mining-tutorial"></a><span data-ttu-id="9bde6-102">高度な時系列予測 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="9bde6-102">Advanced Time Series Predictions (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="9bde6-103">予測モデルの検証によって、ほとんどの地域の売上が似たパターンに合致するものの、太平洋地域の M200 モデルなど、一部の地域とモデルについては、傾向が大きく異なることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="9bde6-103">You saw from exploring the forecasting model that although sales in most of the regions follow a similar pattern, some regions and some models, such as the M200 model in the Pacific region, exhibit very different trends.</span></span> <span data-ttu-id="9bde6-104">これは驚くことではなく、地域間で違いが生じることは一般的で、その要因は販売促進の有無、レポートの不正確性、地政学的なイベントの有無など多岐にわたります。</span><span class="sxs-lookup"><span data-stu-id="9bde6-104">This does not surprise you, as you know that differences among regions are common and can be caused by many factors, including marketing promotions, inaccurate reporting, or geopolitical events.</span></span>  
  
 <span data-ttu-id="9bde6-105">しかし、ユーザーは世界中で適用できるモデルを求めています。</span><span class="sxs-lookup"><span data-stu-id="9bde6-105">However, your users are asking for a model that can be applied worldwide.</span></span> <span data-ttu-id="9bde6-106">したがって、個別の要因が予測に与える影響を最小限に抑えるため、全世界の売上の集計メジャーに基づくモデルを作成することにします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-106">Therefore, to minimize the effect of individual factors on projections, you decide to build a model that is based on aggregated measures of worldwide sales.</span></span> <span data-ttu-id="9bde6-107">その後、このモデルを使用して、個々の地域に対する予測を行います。</span><span class="sxs-lookup"><span data-stu-id="9bde6-107">You can then use this model to make predictions for each individual region.</span></span>  
  
 <span data-ttu-id="9bde6-108">このタスクでは、高度な予測タスクの実行に必要なすべてのデータ ソースを構築します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-108">In this task, you will build all the data sources that you need to perform the advanced prediction tasks.</span></span> <span data-ttu-id="9bde6-109">予測クエリへの入力として使用する 2 つのデータ ソース ビューと、新しいモデルの構築に使用する 1 つのデータ ソース ビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-109">You will create two data source views for use as inputs to the prediction query, and one data source view to use in building a new model.</span></span>  
  
 <span data-ttu-id="9bde6-110">**手順**</span><span class="sxs-lookup"><span data-stu-id="9bde6-110">**Steps**</span></span>  
  
1.  [<span data-ttu-id="9bde6-111">(予測用の) 拡張売上データを準備する</span><span class="sxs-lookup"><span data-stu-id="9bde6-111">Prepare the extended sales data (for prediction)</span></span>](#bkmk_newExtendData)  
  
2.  [<span data-ttu-id="9bde6-112">(モデルを構築するための) 集計データを準備する</span><span class="sxs-lookup"><span data-stu-id="9bde6-112">Prepare the aggregated data (for building the model)</span></span>](#bkmk_newReplaceData)  
  
3.  [<span data-ttu-id="9bde6-113">(クロス予測のための) 系列データを準備する</span><span class="sxs-lookup"><span data-stu-id="9bde6-113">Prepare the series data (for cross-prediction)</span></span>](#bkmk_CrossData2)  
  
4.  [<span data-ttu-id="9bde6-114">EXTEND を使用して予測する</span><span class="sxs-lookup"><span data-stu-id="9bde6-114">Predict using EXTEND</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
5.  [<span data-ttu-id="9bde6-115">クロス予測モデルを作成する</span><span class="sxs-lookup"><span data-stu-id="9bde6-115">Create the cross-prediction model</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
6.  [<span data-ttu-id="9bde6-116">REPLACE を使用して予測する</span><span class="sxs-lookup"><span data-stu-id="9bde6-116">Predict using REPLACE</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
7.  [<span data-ttu-id="9bde6-117">新しい予測を検討する</span><span class="sxs-lookup"><span data-stu-id="9bde6-117">Review the new predictions</span></span>](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
##  <a name="creating-the-new-extended-sales-data"></a><a name="bkmk_newExtendData"></a><span data-ttu-id="9bde6-118">新しい拡張売上データの作成</span><span class="sxs-lookup"><span data-stu-id="9bde6-118">Creating the New Extended Sales Data</span></span>  
 <span data-ttu-id="9bde6-119">売上データを更新するには、最新の売上の数値を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bde6-119">To update your sales data, you will need to get the latest sales figures.</span></span> <span data-ttu-id="9bde6-120">特に関心があるのは太平洋地域のデータです。この地域では、地域の販売促進を開始して、新しい店への関心を引きつけ、製品の認知度を高めています。</span><span class="sxs-lookup"><span data-stu-id="9bde6-120">Of particular interest are the data just in from the Pacific region, which launched a regional sales promotion to call attention to the new stores and raise awareness of their products.</span></span>  
  
 <span data-ttu-id="9bde6-121">このシナリオでは、2つのリージョンについて、3か月分の新しいデータを含む Excel ブックからデータがインポートされていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="9bde6-121">For this scenario, we'll assume that the data has been imported from an Excel workbook that contains just three months of new data for a couple of regions.</span></span> <span data-ttu-id="9bde6-122">Transact-sql スクリプトを使用してデータのテーブルを作成し、予測に使用するデータソースビューを定義します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-122">You'll create a table for the data using a Transact-SQL script, and then define a data source view to use for prediction.</span></span>  
  
#### <a name="create-the-table-with-new-sales-data"></a><span data-ttu-id="9bde6-123">新しい売上データでのテーブルの作成</span><span class="sxs-lookup"><span data-stu-id="9bde6-123">Create the table with new sales data</span></span>  
  
1.  <span data-ttu-id="9bde6-124">Transact-SQL クエリ ウィンドウで次のステートメントを実行し、AdventureWorksDW データベース (またはその他のデータベース) に売上データを追加します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-124">In a Transact-SQL query window, execute the following statement to add the sales data to the AdventureWorksDW database (or any other database).</span></span>  
  
    ```  
    USE [database name];  
    GO  
    IF OBJECT_ID ([dbo].[NewSalesData]) IS NOT NULL   
        DROP TABLE [dbo].[NewSalesData];  
    GO  
    CREATE TABLE [dbo].[NewSalesData]([Series] [nvarchar](255) NULL,  
    [NewDate] [datetime] NULL,  
    [NewQty] [float] NULL,  
    [NewAmount] [money] NULL) ON [PRIMARY]  
  
    GO  
    ```  
  
2.  <span data-ttu-id="9bde6-125">次のスクリプトを使用して、新しい値を挿入します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-125">Insert the new values using the following script.</span></span>  
  
    ```  
    INSERT INTO [NewSalesData]  
    (Series,NewDate,NewQty,NewAmount)  
    VALUES('T1000 Pacific', '7/25/08', 55, '$130,170.22'),  
    ('T1000 Pacific', '8/25/08', 50, '$114,435.36 '),  
    ('T1000 Pacific', '9/25/08', 50, '$117,296.24 '),  
    ('T1000 Europe', '7/25/08', 37, '$88,210.00 '),  
    ('T1000 Europe', '8/25/08', 41, '$97,746.00 '),  
    ('T1000 Europe', '9/25/08', 37, '$88,210.00 '),  
    ('T1000 North America', '7/25/08', 69, '$164,500.00 '),  
    ('T1000 North America', '8/25/08', 66, '$157,348.00 '),  
    ('T1000 North America', '9/25/08', 58, '$138,276.00 '),  
    ('M200 Pacific', '7/25/08', 65, '$149,824.35'),  
    ('M200 Pacific', '8/25/08', 54,  '$124,619.46'),  
    ('M200 Pacific', '9/25/08', 61, '$141,143.39'),  
    ('M200 Europe', '7/25/08', 75, '$173,026.00'),  
    ('M200 Europe', '8/25/08', 76, '$175,212.00'),  
    ('M200 Europe', '9/25/08', 84, '$193,731.00'),  
    ('M200 North America', '7/25/08', 94, '$216,916.00'),  
    ('M200 North America', '8/25/08', 94, '$216,891.00'),  
    ('M200 North America', '9/25/08', 91,'$209,943.00');  
    ```  
  
    > [!WARNING]  
    >  <span data-ttu-id="9bde6-126">通貨の値と共に引用符を使用し、コンマ区切り記号および通貨記号の問題を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="9bde6-126">The quotation marks are used with the currency values to prevent problems with the comma separator and the currency symbol.</span></span> <span data-ttu-id="9bde6-127">また、`130170.22` の形式で通貨の値を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="9bde6-127">You could also pass in the currency values in this format: `130170.22`</span></span>  
    >   
    >  <span data-ttu-id="9bde6-128">サンプル データベースで使用されている日付は、このリリース用に更新されています。</span><span class="sxs-lookup"><span data-stu-id="9bde6-128">Note that the dates used in the sample database have changed for this release.</span></span> <span data-ttu-id="9bde6-129">AdventureWorks の以前のエディションを使用している場合は、それに合わせて、挿入する日付を調整しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9bde6-129">If you are using an earlier edition of AdventureWorks, you might need to adjust the inserted dates accordingly.</span></span>  
  
###  <a name="create-a-data-source-view-using-the-new-sales-data"></a><a name="bkmk_newReplaceData"></a><span data-ttu-id="9bde6-130">新しい売上データを使用してデータソースビューを作成する</span><span class="sxs-lookup"><span data-stu-id="9bde6-130">Create a data source view using the new sales data</span></span>  
  
1.  <span data-ttu-id="9bde6-131">**ソリューションエクスプローラー**で、[**データソースビュー**] を右クリックし、[**新しいデータソースビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-131">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="9bde6-132">データ ソース ビュー ウィザードで、以下の選択を行います。</span><span class="sxs-lookup"><span data-stu-id="9bde6-132">In the Data Source View wizard, make the following selections:</span></span>  
  
     <span data-ttu-id="9bde6-133">**データソース**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bde6-133">**Data Source**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span></span>  
  
     <span data-ttu-id="9bde6-134">**[テーブルとビューの選択**]: 先ほど作成したテーブル NewSalesData を選択します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-134">**Select Tables and Views**: Select the table that you just created, NewSalesData.</span></span>  
  
3.  <span data-ttu-id="9bde6-135">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-135">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="9bde6-136">データソースビューのデザイン画面で、[NewSalesData] を右クリックし、[**データの探索**] を選択してデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-136">In the Data Source View design surface, right-click NewSalesData, and then select **Explore Data** to verify the data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9bde6-137">このデータは予測だけに使用するので、データが不完全でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="9bde6-137">You will use this data for prediction only, so it does not matter that the data is incomplete.</span></span>  
  
##  <a name="creating-the-data-for-the-cross-prediction-model"></a><a name="bkmk_CrossData2"></a><span data-ttu-id="9bde6-138">クロス予測モデルのデータの作成</span><span class="sxs-lookup"><span data-stu-id="9bde6-138">Creating the Data for the Cross-Prediction Model</span></span>  
 <span data-ttu-id="9bde6-139">元の予測モデルで使用されていたデータは既にビュー vTimeSeries によってグループ化されており、複数の自転車モデルが少数のカテゴリにまとめられ、個別の国の結果が地域に結合されていました。</span><span class="sxs-lookup"><span data-stu-id="9bde6-139">The data that was used in the original forecasting model was already grouped somewhat by the view vTimeSeries, which collapsed several bike models into a smaller number of categories, and merged results from individual countries into regions.</span></span> <span data-ttu-id="9bde6-140">世界的な予測に使用できるモデルを作成するには、データ ソース ビュー デザイナーで直接、追加の簡単な集計をいくつか作成します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-140">To create a model that can be used for world-wide projections, you will create some additional simple aggregations directly in the Data Source View Designer.</span></span> <span data-ttu-id="9bde6-141">新しいデータ ソース ビューには、すべての地域におけるすべての製品の売上の合計と平均だけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9bde6-141">The new data source view will contain just a sum and an average of the sales of all products for all regions.</span></span>  
  
 <span data-ttu-id="9bde6-142">モデルに使用するデータ ソースを作成した後、予測に使用する新しいデータ ソース ビューを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bde6-142">After you have created the data source used for the model, you must create a new data source view to use for prediction.</span></span> <span data-ttu-id="9bde6-143">たとえば、新しい全世界モデルを使用してヨーロッパの売上を予測する場合は、ヨーロッパ地域のみのデータを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bde6-143">For example, if you want to predict sales for Europe using the new worldwide model, you must feed in data for the Europe region only.</span></span> <span data-ttu-id="9bde6-144">そこで、元のデータをフィルター処理する新しいデータ ソース ビューを設定し、各予測クエリ セットごとにフィルター条件を変更します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-144">So you will set up a new data source view that filters the original data, and change the filter condition for each set of prediction queries.</span></span>  
  
#### <a name="to-create-the-model-data-using-a-custom-data-source-view"></a><span data-ttu-id="9bde6-145">カスタム データ ソース ビューを使用してモデル データを作成するには</span><span class="sxs-lookup"><span data-stu-id="9bde6-145">To create the model data using a custom data source view</span></span>  
  
1.  <span data-ttu-id="9bde6-146">**ソリューションエクスプローラー**で、[**データソースビュー**] を右クリックし、[**新しいデータソースビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-146">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="9bde6-147">ウィザードの [ようこそ] ページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-147">On the welcome page of the wizard, click **Next**.</span></span>  
  
3.  <span data-ttu-id="9bde6-148">**[データ ソースの選択]** ページで [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-148">On the **Select Data Source** page, select [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="9bde6-149">[テーブル**とビューの選択**] ページで、テーブルを追加せずに、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-149">In the page, **Select Tables and Views**, do not add any tables-just click **Next**.</span></span>  
  
5.  <span data-ttu-id="9bde6-150">[] ページで、**ウィザードを完了**し、名前を入力して、 `AllRegions` [**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-150">On the page, **Completing the Wizard**, type the name `AllRegions`, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="9bde6-151">次に、空のデータソースビューデザイン画面を右クリックし、[**新しい名前付きクエリ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-151">Next, right-click the blank data source view design surface, and then select **New Named Query**.</span></span>  
  
7.  <span data-ttu-id="9bde6-152">[名前**付きクエリの作成**] ダイアログボックスの [**名前**] に「」と入力し、[説明] に「 `AllRegions` **すべてのモデルと地域の売上の合計と平均**」と入力します。 **Description**</span><span class="sxs-lookup"><span data-stu-id="9bde6-152">In the **Create Named Query** dialog box, for **Name**, type `AllRegions`, and for **Description**, type **Sum and average of sales for all models and regions**.</span></span>  
  
8.  <span data-ttu-id="9bde6-153">SQL テキスト ペインに、以下のステートメントを入力して [OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-153">In the SQL text pane, type the following statement and then click OK:</span></span>  
  
    ```  
    SELECT ReportingDate,   
    SUM([Quantity]) as SumQty, AVG([Quantity]) as AvgQty,  
    SUM([Amount]) AS SumAmt, AVG([Amount]) AS AvgAmt,  
    'All Regions' as [Region]  
    FROM dbo.vTimeSeries   
    GROUP BY ReportingDate  
    ```  
  
9. <span data-ttu-id="9bde6-154">テーブルを右クリック `AllRegions` し、[データの**探索**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-154">Right-click the `AllRegions` table, and then select **Explore Data**.</span></span>  
  
###  <a name="to-create-the-series-data-for-cross-prediction"></a><a name="bkmk_CrossData"></a><span data-ttu-id="9bde6-155">クロス予測用の系列データを作成するには</span><span class="sxs-lookup"><span data-stu-id="9bde6-155">To create the series data for cross-prediction</span></span>  
  
1.  <span data-ttu-id="9bde6-156">**ソリューションエクスプローラー**で、[**データソースビュー**] を右クリックし、[**新しいデータソースビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-156">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="9bde6-157">データ ソース ビュー ウィザードで、以下の選択を行います。</span><span class="sxs-lookup"><span data-stu-id="9bde6-157">In the Data Source View wizard, make the following selections:</span></span>  
  
     <span data-ttu-id="9bde6-158">**データソース**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bde6-158">**Data Source**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span></span>  
  
     <span data-ttu-id="9bde6-159">**[テーブルとビューの選択]**: テーブルを選択しない</span><span class="sxs-lookup"><span data-stu-id="9bde6-159">**Select Tables and Views**: Do not select any tables</span></span>  
  
     <span data-ttu-id="9bde6-160">**名前**: `T1000 Pacific Region`</span><span class="sxs-lookup"><span data-stu-id="9bde6-160">**Name**: `T1000 Pacific Region`</span></span>  
  
3.  <span data-ttu-id="9bde6-161">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-161">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="9bde6-162">**T1000 太平洋地域の dsv**の空のデザインサーフェイスを右クリックし、[**新しい名前付きクエリ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-162">Right-click the empty design surface for **T1000 Pacific Region.dsv**, and then select **New Named Query**.</span></span>  
  
     <span data-ttu-id="9bde6-163">**[名前付きクエリの作成]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9bde6-163">The **Create Named Query** dialog box appears.</span></span> <span data-ttu-id="9bde6-164">名前を再入力し、以下の説明を追加します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-164">Retype the name, and then add the following description:</span></span>  
  
     <span data-ttu-id="9bde6-165">**名前**: `T1000 Pacific Region`</span><span class="sxs-lookup"><span data-stu-id="9bde6-165">**Name**: `T1000 Pacific Region`</span></span>  
  
     <span data-ttu-id="9bde6-166">**説明**: \*\* `vTimeSeries` 地域とモデルによるフィルター処理\*\*</span><span class="sxs-lookup"><span data-stu-id="9bde6-166">**Description**: **Filter`vTimeSeries`by region and model**</span></span>  
  
5.  <span data-ttu-id="9bde6-167">テキスト ペインに、以下のクエリを入力して [OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bde6-167">In the text pane, type the following query, and then click OK:</span></span>  
  
    ```  
    SELECT ReportingDate, ModelRegion, Quantity, Amount  
    FROM dbo.vTimeSeries  
    WHERE (ModelRegion = N'T1000 Pacific')  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="9bde6-168">各系列で個別に予測を作成する必要があるので、クエリ テキストをコピーしてテキスト ファイルに保存し、他のデータ系列で再利用できます。</span><span class="sxs-lookup"><span data-stu-id="9bde6-168">Since you will need to create predictions for each series separately, you might want to copy the query text and save it to a text file so that you can re-use it for the other data series.</span></span>  
  
6.  <span data-ttu-id="9bde6-169">データソースビューのデザイン画面で、[T1000 太平洋] を右クリックし、[**データの探索**] を選択して、データが正しくフィルター処理されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-169">In the Data Source View design surface, right-click T1000 Pacific, and then select **Explore Data** to verify that the data is filtered correctly.</span></span>  
  
     <span data-ttu-id="9bde6-170">クロス予測クエリを作成するときは、このデータをモデルへの入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="9bde6-170">You will use this data as the input to the model when creating cross-prediction queries.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9bde6-171">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="9bde6-171">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9bde6-172">更新されたデータを使用した時系列予測 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="9bde6-172">Time Series Predictions using Updated Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="9bde6-173">参照</span><span class="sxs-lookup"><span data-stu-id="9bde6-173">See Also</span></span>  
 <span data-ttu-id="9bde6-174">[Microsoft タイムシリーズアルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="9bde6-174">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 <span data-ttu-id="9bde6-175">[Microsoft タイムシリーズアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9bde6-175">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="9bde6-176">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="9bde6-176">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
