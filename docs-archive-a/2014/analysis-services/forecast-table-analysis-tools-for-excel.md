---
title: 予測 (Excel 用のテーブル分析ツール) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- forecasting
- mining model, time series
- time series [data mining]
ms.assetid: 22bb0b5e-78f5-484e-883d-2b5985a12749
author: minewiskan
ms.author: owend
ms.openlocfilehash: abca22dbcb9ae6426e839f92e391a658f5029e31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633434"
---
# <a name="forecast-table-analysis-tools-for-excel"></a><span data-ttu-id="e27e4-102">予測 (Excel 用のテーブル分析ツール)</span><span class="sxs-lookup"><span data-stu-id="e27e4-102">Forecast (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="e27e4-103">![[テーブル分析ツール] リボンの [予測] ボタン](media/tat-forecast.gif "[テーブル分析ツール] リボンの [予測] ボタン")</span><span class="sxs-lookup"><span data-stu-id="e27e4-103">![Forecast button in Table Analysis tools ribbon](media/tat-forecast.gif "Forecast button in Table Analysis tools ribbon")</span></span>  
  
 <span data-ttu-id="e27e4-104">**予測**ツールを使用すると、Excel データテーブルまたはその他のデータソースのデータに基づいて予測を行うことができ、予測される各値に関連する確率を必要に応じて表示できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-104">The **Forecast** tool helps you make predictions based on data in an Excel data table or other data source, and optionally view the probabilities associated with each predicted value.</span></span> <span data-ttu-id="e27e4-105">たとえば、日付の列と各日の売上合計の列がデータにある場合、将来の各日の売上を予測できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-105">For example, if your data contains a date column and a column that shows total sales for each day of the month, you could predict the sales for future days.</span></span> <span data-ttu-id="e27e4-106">また、取得する予測の数も指定できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-106">You can also specify the number of predictions to make.</span></span> <span data-ttu-id="e27e4-107">たとえば、5 日間または 30 日間の予測を行えます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-107">For example, you can predict five days, or thirty.</span></span>  
  
 <span data-ttu-id="e27e4-108">ツールを完了すると、ソース データ テーブルの末尾に新たに予測が追加され、新しい値が反転表示されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-108">When the tool completes, it appends the new predictions to the end of the source data table, and highlights the new values.</span></span> <span data-ttu-id="e27e4-109">新しい時系列値は追加されないため、最初に予測を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-109">New time series values are not appended; this allows you to review the predictions first.</span></span>  
  
 <span data-ttu-id="e27e4-110">このツールでは、**予測レポート**という名前の新しいワークシートも作成されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-110">The tool also creates a new worksheet named **Forecasting Report**.</span></span> <span data-ttu-id="e27e4-111">このワークシートでは、ウィザードで予測が正常に作成されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-111">This worksheet reports whether the wizard successfully created a prediction.</span></span> <span data-ttu-id="e27e4-112">新しいワークシートには、過去の傾向が表示された折れ線グラフもあります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-112">The new worksheet also contains a line graph that shows the historical trends.</span></span>  
  
 <span data-ttu-id="e27e4-113">時系列を新しい予測まで伸ばすと、折れ線グラフに予測値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-113">When you extend the time series to include the new predictions, the predicted values are added to the line graph.</span></span> <span data-ttu-id="e27e4-114">過去の値は実線で表示され、予測は点線で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-114">The historical values are shown as a solid line and the predictions are shown as a dotted line.</span></span>  
  
## <a name="using-the-forecast-tool"></a><span data-ttu-id="e27e4-115">予測ツールの使用</span><span class="sxs-lookup"><span data-stu-id="e27e4-115">Using the Forecast Tool</span></span>  
  
1.  <span data-ttu-id="e27e4-116">予測可能な数値データが保存されている Excel テーブルを開きます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-116">Open an Excel table that contains predictable numeric data.</span></span>  
  
2.  <span data-ttu-id="e27e4-117">[**分析**] タブの [**予測**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e27e4-117">Click **Forecast** on the **Analyze** tab.</span></span>  
  
3.  <span data-ttu-id="e27e4-118">予測する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-118">Specify the columns to forecast.</span></span> <span data-ttu-id="e27e4-119">このツールでは、予測可能なデータ型 (つまり、連続する数値データ) を持つデータの列が自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-119">The tool automatically selects columns in the data that have a predictable data type-that is, continuous numeric data.</span></span> <span data-ttu-id="e27e4-120">列に多数の NULL 値または 0 値が含まれる場合は、データが不足して結果に影響を及ぼす可能性があるため、連続数値データの列でも選択されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-120">The tool might not select some columns that have continuous numeric data if the columns contain many null or zero values, because the missing data might affect the results.</span></span> <span data-ttu-id="e27e4-121">この問題が発生した場合は、[ラベルの[&#40;SQL Server データマイニングアドイン&#41;](relabel-sql-server-data-mining-add-ins.md) ] ツールを使用してデータを修正できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-121">If this happens, you can fix the data by using the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool.</span></span>  
  
4.  <span data-ttu-id="e27e4-122">日付、時刻、またはその他の系列の識別子を含んでいる列を指定します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-122">Specify the column that contains the date, time, or other series identifier.</span></span> <span data-ttu-id="e27e4-123">このオプションを選択すると、 **\<no time stamp>** ソースデータ内の行のシーケンスに基づいて系列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-123">If you select the option **\<no time stamp>** the tool will create a series based on the sequence of rows in the source data.</span></span>  
  
5.  <span data-ttu-id="e27e4-124">取得する予測の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-124">Specify the number of predictions to make.</span></span>  
  
6.  <span data-ttu-id="e27e4-125">必要に応じて、データの繰り返し間隔 (週単位や月単位など) に関するヒントをアルゴリズムに提供します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-125">Optionally, provide a hint to the algorithm about whether you expect your data to repeat weekly, monthly, or in other periods.</span></span> <span data-ttu-id="e27e4-126">データが特定のパターンに合わない場合、またはパターンがわからない場合は、を選択して、 **\<detect automatically>** 繰り返し期間を検索するようにツールを設定します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-126">If your data does not fit any of the given patterns, or if you are unaware of any patterns, select **\<detect automatically>** to have the tool find the repeating time periods.</span></span>  
  
7.  <span data-ttu-id="e27e4-127">ソース テーブルに予測が追加され、新しいワークシートに予測レポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-127">The wizard adds the predictions to the source table, and creates a forecasting report in a new worksheet.</span></span>  
  
8.  <span data-ttu-id="e27e4-128">予測グラフに新しい値を追加するには、予測値を含むように時系列を伸ばします。</span><span class="sxs-lookup"><span data-stu-id="e27e4-128">To add the new values to the prediction graph, extend the time series to include the forecasted values.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="e27e4-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="e27e4-129">Requirements</span></span>  
 <span data-ttu-id="e27e4-130">予測を実行する列には、通貨やその他の数値のような連続する数値データが格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-130">The columns that you predict must contain continuous numeric data, such as currency or other numbers.</span></span>  
  
 <span data-ttu-id="e27e4-131">可能な場合は、時刻や日付のような時系列もデータに含まれているとよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="e27e4-131">If possible, your data should also include a column that contains a series of times or dates.</span></span> <span data-ttu-id="e27e4-132">日付と時刻のデータではなく、数値系列 (1、2、3...) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-132">You can use a numeric series (1,2,3....) instead of date and time data.</span></span> <span data-ttu-id="e27e4-133">ただし、系列の列の値は一意でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="e27e4-133">However, values in the series column must be unique.</span></span> <span data-ttu-id="e27e4-134">**予測**ツールで系列列の重複する値が検出されると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-134">An error occurs if the **Forecast** tool finds duplicate values in the series column.</span></span>  
  
 <span data-ttu-id="e27e4-135">**予測**ツールを使用して日付を予測することはできません。</span><span class="sxs-lookup"><span data-stu-id="e27e4-135">You cannot predict a date by using the **Forecast** tool.</span></span> <span data-ttu-id="e27e4-136">エラーが発生することはありませんが、このアルゴリズムは予測値として日付を使用するように設計されていません。</span><span class="sxs-lookup"><span data-stu-id="e27e4-136">Although an error might not occur, this algorithm is not designed to use dates as predictable values.</span></span>  
  
### <a name="understanding-time-stamps"></a><span data-ttu-id="e27e4-137">タイムスタンプについて</span><span class="sxs-lookup"><span data-stu-id="e27e4-137">Understanding Time Stamps</span></span>  
 <span data-ttu-id="e27e4-138">*タイムスタンプ*として使用する列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-138">You must identify a column to use as a *time stamp*.</span></span> <span data-ttu-id="e27e4-139">タイムスタンプには 2 つの目的があります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-139">The time stamp serves two purposes.</span></span> <span data-ttu-id="e27e4-140">1 つは、時系列で値を一意に識別することです。</span><span class="sxs-lookup"><span data-stu-id="e27e4-140">First, it uniquely identifies a value in a time series.</span></span> <span data-ttu-id="e27e4-141">たとえば、売上を日次ベースで追跡している場合は、1 日に 1 つの売上値のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="e27e4-141">For example, if you are tracking sales on a daily basis, you should have only one sales value for each day.</span></span> <span data-ttu-id="e27e4-142">カレンダー日付をタイムスタンプとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-142">The calendar date can be used as the time stamp.</span></span> <span data-ttu-id="e27e4-143">2 番目の目的は、タイムスタンプ列で予測を作成する単位を示すことです。</span><span class="sxs-lookup"><span data-stu-id="e27e4-143">Second, the time stamp column indicates the unit for making predictions.</span></span> <span data-ttu-id="e27e4-144">日次売上を追跡している場合は、予測の単位も日になります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-144">If you are tracking daily sales, your predictions will also be in units of days.</span></span>  
  
 <span data-ttu-id="e27e4-145">データに日付や時刻の列が含まれない場合は、_RowIndex という一時系列キーが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-145">If your data does not include a date or time column, the tool will automatically create a temporary series key, named _RowIndex.</span></span> <span data-ttu-id="e27e4-146">このキーは、データ セット内の行の順番に基づきます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-146">The key will be based on the order of the rows in the data set.</span></span>  
  
 <span data-ttu-id="e27e4-147">予測数を指定する場合は、ステップ数を示す整数を入力します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-147">When you specify the number of predictions, you enter a whole number that indicates the number of steps.</span></span> <span data-ttu-id="e27e4-148">これらのステップの単位は、データの時刻および日付系列で使用されている単位に依存します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-148">The units for these steps depend on the units used in the time and date series in your data.</span></span> <span data-ttu-id="e27e4-149">データが月別の販売実績の一覧である場合、予測は月単位になります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-149">If your data lists sales results by the month, the prediction will be for a series of months.</span></span> <span data-ttu-id="e27e4-150">ソース データを変更しない限り、時間の単位は変更できません。</span><span class="sxs-lookup"><span data-stu-id="e27e4-150">You cannot change the units of time unless you change the source data.</span></span>  
  
### <a name="understanding-periodicity"></a><span data-ttu-id="e27e4-151">周期性について</span><span class="sxs-lookup"><span data-stu-id="e27e4-151">Understanding Periodicity</span></span>  
 <span data-ttu-id="e27e4-152">予測は、ある期間にわたって繰り返されるパターンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="e27e4-152">A forecast is based on repeating patterns over a period of time.</span></span> <span data-ttu-id="e27e4-153">このため、Microsoft Time Series アルゴリズムでは、最も有力なパターンが発生する期間を特定するための計算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-153">Therefore, the Microsoft Time Series algorithm performs calculations to determine the time periods that have the strongest patterns.</span></span> <span data-ttu-id="e27e4-154">*周期*性とは、これらの期間を指します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-154">*Periodicity* refers to these time periods.</span></span>  
  
 <span data-ttu-id="e27e4-155">時系列には、数多くの潜在的なパターンが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-155">A time series can contain many potential patterns.</span></span> <span data-ttu-id="e27e4-156">データに一定のパターンがあることが確実であれば、アルゴリズムにヒントを与えることで予測の精度を高められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-156">If you are certain that your data contains a certain pattern, you may be able to improve the quality of prediction by providing a hint to the algorithm.</span></span>  
  
 <span data-ttu-id="e27e4-157">たとえば、データが週単位で繰り返されることが予想される場合は、[週単位] を選択して、アルゴリズムに週単位のパターンを検出するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-157">For example, if you expect that your data repeats on a weekly basis, you can select Weekly to indicate that the algorithm should look for weekly patterns.</span></span> <span data-ttu-id="e27e4-158">ただし、有力な週単位のパターンが見つからなければ、そのヒントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-158">However, if no strong weekly patterns are found, the algorithm will ignore the hint.</span></span>  
  
## <a name="understanding-the-forecasting-report"></a><span data-ttu-id="e27e4-159">予測レポートについて</span><span class="sxs-lookup"><span data-stu-id="e27e4-159">Understanding the Forecasting Report</span></span>  
 <span data-ttu-id="e27e4-160">このグラフでは、データ テーブルの過去の値が暗い線で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-160">In this graph, the historical values from your data table appear as a dark line.</span></span> <span data-ttu-id="e27e4-161">予測値は点線で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-161">The predicted values appear as dotted lines.</span></span> <span data-ttu-id="e27e4-162">線上の点をクリックすると、予測値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-162">You can click a point on the line to see the forecasted value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e27e4-163">グラフ内の予測値の時間軸にラベルが表示されない場合は、予測値を含むワークシートを開き、Excel の**Fill、Series**関数を使用して、予測値を含むようにタイムスタンプ列を拡張します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-163">If you do not see labels on the time axis for the predicted values in the graph, open the worksheet that contains the predicted values, and use the **Fill, Series** function in Excel to extend the time stamp column to include the predicted values.</span></span>  
  
 <span data-ttu-id="e27e4-164">予測のタイム スライス数が、要求した数より少ない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-164">In some cases, the forecast may not have as many time slices as requested.</span></span> <span data-ttu-id="e27e4-165">これは、将来のその時点までの予測をアルゴリズムで行うためには、データが不十分であったことを意味します。</span><span class="sxs-lookup"><span data-stu-id="e27e4-165">This usually means that data was insufficient to allow the algorithm to forecast that far into the future.</span></span> <span data-ttu-id="e27e4-166">**予測**ツールは、最小確率しきい値を満たす予測のみを行います。</span><span class="sxs-lookup"><span data-stu-id="e27e4-166">The **Forecast** tool will only make predictions that meet a minimum probability threshold.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="e27e4-167">関連ツール</span><span class="sxs-lookup"><span data-stu-id="e27e4-167">Related Tools</span></span>  
 <span data-ttu-id="e27e4-168">Excel 用のデータ マイニング クライアントは、より高度なデータ マイニング機能を備えた独立したアドインであり、予測のためのウィザードも用意されています。</span><span class="sxs-lookup"><span data-stu-id="e27e4-168">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, also contains a wizard for forecasting.</span></span>  
  
 <span data-ttu-id="e27e4-169">**予測**ツール (excel 用のテーブル分析ツール) と**予測**ウィザード (Excel 用のデータマイニングクライアント) の両方で、タイムシリーズアルゴリズムが使用さ [!INCLUDE[msCoName](../includes/msconame-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="e27e4-169">Both the **Forecast** tool (in the Table Analysis Tools for Excel) and the **Forecast** wizard (in the Data Mining Client for Excel) use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
-   <span data-ttu-id="e27e4-170">**予測**ツールを使用すると、データに最適な設定を使用するようにアルゴリズムが自動的に構成されるため、使用が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="e27e4-170">The **Forecast** tool is easier to use because it automatically configures the algorithm to use the settings that are best for your data.</span></span>  
  
-   <span data-ttu-id="e27e4-171">Excel 用のデータマイニングクライアントの**予測**ウィザードには、パラメーターをカスタマイズする機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e27e4-171">The **Forecast** wizard in the Data Mining Client for Excel provides you with the ability to customize the parameters.</span></span>  
  
 <span data-ttu-id="e27e4-172">**予測**ウィザードの詳細については、「[予測ウィザード &#40;&#41;Excel 用データマイニングアドイン](forecast-wizard-data-mining-add-ins-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e27e4-172">For more information about the **Forecast** wizard, see [Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md).</span></span> <span data-ttu-id="e27e4-173">予測に使用されるアルゴリズムの詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックの「Microsoft Time Series アルゴリズム」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e27e4-173">For more information about the algorithm used for forecasting, see the topic "Microsoft Time Series Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27e4-174">参照</span><span class="sxs-lookup"><span data-stu-id="e27e4-174">See Also</span></span>  
 [<span data-ttu-id="e27e4-175">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="e27e4-175">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
