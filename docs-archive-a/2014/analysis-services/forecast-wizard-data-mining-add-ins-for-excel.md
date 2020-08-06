---
title: 予測ウィザード (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- forecasting [data mining]
- time series [data mining]
ms.assetid: c5b33f75-42d4-4598-89e7-94815c142ce6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c3fae97bf1c36154d8ae378840014f2fb997afd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633430"
---
# <a name="forecast-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="8577f-102">予測ウィザード (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="8577f-102">Forecast Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="8577f-103">![[データ マイニング] リボンの関連付けウィザード](media/dmc-forecast.gif "[データ マイニング] リボンの関連付けウィザード")</span><span class="sxs-lookup"><span data-stu-id="8577f-103">![Associate wizard in Data Mining ribbon](media/dmc-forecast.gif "Associate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="8577f-104">予測ウィザードでは、時系列の値を予測できます。</span><span class="sxs-lookup"><span data-stu-id="8577f-104">The Forecast wizard helps you predict values in a time series.</span></span> <span data-ttu-id="8577f-105">予測ウィザードでは、製品売上などの連続列を予測するための回帰アルゴリズムである [!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="8577f-105">The Forecast wizard uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm, which is a regression algorithm for use in predicting continuous columns, such as product sales.</span></span>  
  
 <span data-ttu-id="8577f-106">各予測モデルには、ケース シリーズが含まれている必要があります。ケース シリーズとは、シーケンス内のポイントを区別する列です。</span><span class="sxs-lookup"><span data-stu-id="8577f-106">Each forecasting model must contain a case series, which is the column that distinguishes between points in a sequence.</span></span> <span data-ttu-id="8577f-107">たとえば、履歴データを使用して数か月間にわたる売上を予測する場合は、一連のデータを含む列をケース シリーズとして使用します。</span><span class="sxs-lookup"><span data-stu-id="8577f-107">For example, if you are using historical data to forecast sales over a period of several months, you would use a column containing a series of dates as the case series.</span></span>  
  
 <span data-ttu-id="8577f-108">新しい入力データを提供しなくても、予測モデルから予測を作成できます。</span><span class="sxs-lookup"><span data-stu-id="8577f-108">You can create predictions from a forecasting model without providing new input data.</span></span>  
  
 <span data-ttu-id="8577f-109">[**分析**] リボンの [ [&#41;Excel 用テーブル分析ツールの予測 &#40;テーブル分析ツール](forecast-table-analysis-tools-for-excel.md)] を使用すると、予測モデルを作成することもできますが、カスタマイズはできず、Excel テーブルのデータのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8577f-109">The [Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) tool, in the **Analyze** ribbon, also lets you create forecasting models, but it is less customizable and can only use data in Excel tables.</span></span>  
  
## <a name="using-the-forecast-wizard"></a><span data-ttu-id="8577f-110">予測ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="8577f-110">Using the Forecast Wizard</span></span>  
  
1.  <span data-ttu-id="8577f-111">[**データマイニング**] リボンで、[**予測**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8577f-111">In the **Data Mining** ribbon, click **Forecast**.</span></span>  
  
2.  <span data-ttu-id="8577f-112">**[ソースデータの選択**] で、入力として使用する Excel のテーブル、範囲、または外部データソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="8577f-112">In the **Select Source Data**, choose the Excel table, range, or external data source to use as inputs.</span></span>  
  
     <span data-ttu-id="8577f-113">外部データ ソースを使用する場合、カスタム ビューまたはカスタム クエリを定義し、それを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソースとして保存できます。</span><span class="sxs-lookup"><span data-stu-id="8577f-113">If you use an external data source, you can define custom view or queries and save it as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="8577f-114">[**予測**] ページの [**タイムスタンプ**] で、ケースシリーズとして使用できる一意の数値 (日付と時刻の値を含む) を含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="8577f-114">On the **Forecasting** page, for **Time stamp**, select a column that contains unique numeric value (this includes date and time values) that can be used as the case series.</span></span> <span data-ttu-id="8577f-115">データ ソースは、この列の昇順で並べ替えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8577f-115">The data source must be sorted in ascending order by this column.</span></span>  
  
     <span data-ttu-id="8577f-116">データにこのような列がない場合は、オプションを使用でき \<no time stamp> ます。</span><span class="sxs-lookup"><span data-stu-id="8577f-116">If your data does not have such a column, you can use the option \<no time stamp>.</span></span> <span data-ttu-id="8577f-117">ウィザードによって、入力データ用に一意の順序列が追加されます。そのため、ウィザードを実行してこのオプションを選択する前に、データが希望どおりに並べ替えられることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8577f-117">The wizard will add a unique order column for the input data; therefore, you must make sure that the data is sorted the way you want before running the wizard and choosing this option.</span></span>  
  
4.  <span data-ttu-id="8577f-118">必要に応じて、[**パラメーター** ] をクリックして、マイニングモデルの動作をカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8577f-118">Optionally, you can click **Parameters** and customize the behavior of the mining model.</span></span>  
  
     <span data-ttu-id="8577f-119">予測モデルでは、いくつか異なるアルゴリズムがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8577f-119">Forecasting models support several different algorithms:</span></span>  
  
    -   <span data-ttu-id="8577f-120">ARIMA</span><span class="sxs-lookup"><span data-stu-id="8577f-120">ARIMA</span></span>  
  
    -   <span data-ttu-id="8577f-121">ARTXP (回帰モデルの一種)</span><span class="sxs-lookup"><span data-stu-id="8577f-121">ARTXP (a type of regression model)</span></span>  
  
    -   <span data-ttu-id="8577f-122">ARTXP と ARIMA の組み合わせ</span><span class="sxs-lookup"><span data-stu-id="8577f-122">ARTXP and ARIMA combined</span></span>  
  
     <span data-ttu-id="8577f-123">違いの詳細については、「 [Microsoft タイムシリーズアルゴリズムテクニカルリファレンス](data-mining/microsoft-time-series-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8577f-123">For information about the differences, see [Microsoft Time Series Algorithm Technical Reference](data-mining/microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
     <span data-ttu-id="8577f-124">また、モデルに対して周期性のヒントを追加し、スムージング オプションを指定して、回帰オプションをカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8577f-124">You can also add periodicity hints, specify smoothing options, and customize regression options for the model.</span></span>  
  
5.  <span data-ttu-id="8577f-125">[**完了**] ページで、データセットとモデルのわかりやすい名前を指定し、完成したモデルの操作方法を制御する次のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="8577f-125">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="8577f-126">**モデルを参照**します。</span><span class="sxs-lookup"><span data-stu-id="8577f-126">**Browse model**.</span></span> <span data-ttu-id="8577f-127">このオプションを選択すると、ウィザードがモデルの処理を終了するとすぐに、[**参照**] ウィンドウが開き、結果を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="8577f-127">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="8577f-128">ビューアーの内容は、構築したモデルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="8577f-128">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="8577f-129">詳細については、「[予測モデルの参照](browsing-a-forecasting-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8577f-129">For more information, see [Browsing a Forecasting Model](browsing-a-forecasting-model.md).</span></span>  
  
    -   <span data-ttu-id="8577f-130">**ドリルスルーを有効に**します。</span><span class="sxs-lookup"><span data-stu-id="8577f-130">**Enable drillthrough**.</span></span> <span data-ttu-id="8577f-131">このチェック ボックスをオンにすると、完成したモデルから基になるデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="8577f-131">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="8577f-132">このオプションは、デシジョン ツリー モデルを構築する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8577f-132">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="8577f-133">**一時的なモデルを使用**します。</span><span class="sxs-lookup"><span data-stu-id="8577f-133">**Use temporary model**.</span></span> <span data-ttu-id="8577f-134">このチェック ボックスをオンにすると、モデルがサーバーに保存されません。</span><span class="sxs-lookup"><span data-stu-id="8577f-134">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="8577f-135">一時的なモデルは、Excel の終了時に削除されます。</span><span class="sxs-lookup"><span data-stu-id="8577f-135">Temporary models are deleted when you close Excel.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="8577f-136">必要条件</span><span class="sxs-lookup"><span data-stu-id="8577f-136">Requirements</span></span>  
 <span data-ttu-id="8577f-137">データには、時系列として使用できる列が 1 列以上含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8577f-137">Your data should include at least one column that can be used as the time series.</span></span> <span data-ttu-id="8577f-138">この列の値は一意であり、連続している必要があります。つまり、ギャップは存在しません。</span><span class="sxs-lookup"><span data-stu-id="8577f-138">The values in this column should be unique and continuous - that is, there should be no gaps.</span></span> <span data-ttu-id="8577f-139">ウィザードを実行する前に、時系列の列の昇順でデータを並べ替えてください。</span><span class="sxs-lookup"><span data-stu-id="8577f-139">Before running the wizard, sort the data by the time series column in ascending order.</span></span>  
  
 <span data-ttu-id="8577f-140">データに時刻または日付の列が含まれていない場合は、任意の数値系列を割り当てるか、ウィザードで作成することができます。</span><span class="sxs-lookup"><span data-stu-id="8577f-140">If your data does not include a time or date column, you can assign an arbitrary numeric series, or let the wizard create one.</span></span> <span data-ttu-id="8577f-141">ウィザードで系列の順序の列を作成する場合は、ウィザードを開始する前に、他の列が必要な順序で並べ替えられていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8577f-141">F you let the wizard create the series order column, make sure the other columns are sorted in the worder you want them before starting the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8577f-142">参照</span><span class="sxs-lookup"><span data-stu-id="8577f-142">See Also</span></span>  
 <span data-ttu-id="8577f-143">[データマイニングモデルの作成](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="8577f-143">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="8577f-144">[Excel 用のテーブル分析ツールの予測 &#40;&#41;](forecast-table-analysis-tools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="8577f-144">[Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) </span></span>  
 [<span data-ttu-id="8577f-145">予測モデルの参照</span><span class="sxs-lookup"><span data-stu-id="8577f-145">Browsing a Forecasting Model</span></span>](browsing-a-forecasting-model.md)  
  
  
