---
title: 予測用のデータソースビューの追加 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9424988efa6a9856f4ef0d558992fc90ac303861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720546"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a><span data-ttu-id="de899-102">予測用のデータ ソース ビューの追加 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="de899-102">Adding a Data Source View for Forecasting (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="de899-103">この作業では、予測シナリオに使用するデータ ソース ビューを追加します。</span><span class="sxs-lookup"><span data-stu-id="de899-103">In this task, you add a data source view that will be used for the forecasting scenario.</span></span> <span data-ttu-id="de899-104">予測モデルでは、時系列内のステップを識別するための列がデータに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="de899-104">A forecasting model requires that the data contains a column that can be used to identify steps in a time series.</span></span> <span data-ttu-id="de899-105">複数の系列のデータを分析する場合は、すべての系列が終了する日付または時間ステップが同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="de899-105">If you plan to analyze multiple series of data, all series must end on the same date or time step.</span></span>  
  
### <a name="to-add-a-data-source-view"></a><span data-ttu-id="de899-106">データ ソース ビューを追加するには</span><span class="sxs-lookup"><span data-stu-id="de899-106">To add a data source view</span></span>  
  
1.  <span data-ttu-id="de899-107">ソリューションエクスプローラーで、[**データソースビュー**] を右クリックし、[**新しいデータソースビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de899-107">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="de899-108">**[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de899-108">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="de899-109">[**データソースの選択**] ページの [**リレーショナルデータソース**] で、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="de899-109">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source.</span></span> <span data-ttu-id="de899-110">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de899-110">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="de899-111">このデータソースがない場合は、「[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)」で、データソースを作成する手順を確認できます。</span><span class="sxs-lookup"><span data-stu-id="de899-111">If you do not have this data source, you can find the steps to create the data source in the [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span>  
  
4.  <span data-ttu-id="de899-112">[**テーブルとビューの選択**] ページで、[vTimeSeries (dbo)] テーブルを選択し、右矢印をクリックしてデータソースビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="de899-112">On the **Select Tables and Views** page, select the table, vTimeSeries (dbo), and then click the right arrow to add it to the data source view.</span></span>  
  
5.  <span data-ttu-id="de899-113">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de899-113">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="de899-114">既定では、[**ウィザードの完了**] ページにはという名前のデータソースビューが [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] あります。</span><span class="sxs-lookup"><span data-stu-id="de899-114">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="de899-115">名前を**Salesbyregion**に変更し、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de899-115">Change the name to **SalesByRegion**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="de899-116">データソースビューデザイナーが開き、 **Salesbyregion**データソースビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="de899-116">Data Source View Designer opens and the **SalesByRegion** data source view appears.</span></span>  
  
## <a name="working-with-the-data-source-view"></a><span data-ttu-id="de899-117">データ ソース ビューの使用</span><span class="sxs-lookup"><span data-stu-id="de899-117">Working with the Data Source View</span></span>  
 <span data-ttu-id="de899-118">データ ソース ビューを作成したら、次の方法でデータを検証できます。</span><span class="sxs-lookup"><span data-stu-id="de899-118">After you have created the data source view, you can explore the data in the following ways:</span></span>  
  
-   <span data-ttu-id="de899-119">デザイナーで vTimeSeries テーブルを右クリックし、[データの**探索**] を選択して、選択したテーブルをグリッドで開きます。</span><span class="sxs-lookup"><span data-stu-id="de899-119">Right-click the table vTimeSeries in the designer, and select **Explore Data** to open the selected table in a grid.</span></span>  
  
-   <span data-ttu-id="de899-120">[**サンプリングオプション**] をクリックし、[**データ探索オプション**] ダイアログボックスを使用してサンプリング方法を変更します。</span><span class="sxs-lookup"><span data-stu-id="de899-120">Click **Sampling options** and then use the **Data Exploration Options** dialog box to change the sampling method.</span></span> <span data-ttu-id="de899-121">[**最新**の情報に更新] をクリックして、新しいオプション設定を使用してテーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="de899-121">Click **Refresh** to load data in the table using the new option settings.</span></span> <span data-ttu-id="de899-122">たとえば、サンプルに出力する行の数を指定したり、上位 n 行を選択したりできます。</span><span class="sxs-lookup"><span data-stu-id="de899-122">For example, you could specify the number of rows to output in the sample, or choose the top n rows.</span></span>  
  
-   <span data-ttu-id="de899-123">テーブル vTimeSeries を右クリックし、[**プロパティ**] を選択してテーブルに新しい名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="de899-123">Right-click the table vTimeSeries and select **Properties** to assign a new name to the table.</span></span> <span data-ttu-id="de899-124">データ ソース ビューから個々の列を選択して、列のプロパティを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="de899-124">You can also select individual columns from the data source view, and the modify the column properties.</span></span>  
  
-   <span data-ttu-id="de899-125">データ ソース ビューのデザイン領域の任意の場所をクリックして、新しいクエリの作成と名前の割り当て、テーブル間のリレーションシップの作成、デザイン領域のレイアウトの変更を行います。</span><span class="sxs-lookup"><span data-stu-id="de899-125">Click anywhere in the data source view design area to create a new query and assign a name to it, to create relationships between tables, or to change the layout of the design area.</span></span>  
  
-   <span data-ttu-id="de899-126">テーブルを右クリックし、[**新しい名前付き計算**] を選択して、集計を含む派生列を作成します。</span><span class="sxs-lookup"><span data-stu-id="de899-126">Right-click a table and select **New Named Calculation** to create derived columns, including aggregations.</span></span> <span data-ttu-id="de899-127">また、このビューではデータ ソースから新しいテーブルやビューを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="de899-127">You can also add new tables and views from the data source in this view.</span></span>  
  
 <span data-ttu-id="de899-128">次の作業では、時系列データについて学習し、時系列識別子として使用するのに最適な列を決定します。</span><span class="sxs-lookup"><span data-stu-id="de899-128">In the next task, you will explore the time series data and determine the best column to use as the time series identifier.</span></span> <span data-ttu-id="de899-129">時系列データのギャップを処理する方法についても学習します。</span><span class="sxs-lookup"><span data-stu-id="de899-129">You will also learn how to handle gaps in time series data.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="de899-130">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="de899-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="de899-131">タイムシリーズモデルの要件について &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="de899-131">Understanding the Requirements for a Time Series Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="de899-132">参照</span><span class="sxs-lookup"><span data-stu-id="de899-132">See Also</span></span>  
 [<span data-ttu-id="de899-133">Microsoft Time Series アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="de899-133">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
