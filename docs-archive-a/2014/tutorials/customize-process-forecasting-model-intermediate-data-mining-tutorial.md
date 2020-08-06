---
title: 予測モデルのカスタマイズと処理 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4bd25e15-9d9e-4528-b7bc-ccb856643aec
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 03dc67907b22750eb1b8539feaddec58f61f702f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643048"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="0f995-102">予測モデルのカスタマイズと処理 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="0f995-102">Customizing and Processing the Forecasting Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="0f995-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムには、モデルの作成方法と時間データの分析方法に影響するいくつかのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="0f995-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm provides parameters that affect how a model is created, and how time data is analyzed.</span></span> <span data-ttu-id="0f995-104">これらのプロパティを変更すると、マイニング モデルでの予測の作成方法に大きく影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f995-104">Changing these properties can significantly affect how the mining model makes predictions.</span></span>  
  
 <span data-ttu-id="0f995-105">このチュートリアルでは、次の作業を行ってモデルを変更します。</span><span class="sxs-lookup"><span data-stu-id="0f995-105">For this task in the tutorial, you will perform the following tasks to modify the model:</span></span>  
  
1.  <span data-ttu-id="0f995-106">*PERIODICITY_HINT*パラメーターに新しい値を追加することで、モデルが期間を処理する方法をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="0f995-106">You will customize the way your model handles time periods by adding a new value for the *PERIODICITY_HINT* parameter.</span></span>  
  
2.  <span data-ttu-id="0f995-107">Microsoft Time Series アルゴリズムの重要な 2 つのパラメーターについて理解します。FORECAST_METHOD では、予測に使用される方法を制御できます。PREDICTION_SMOOTHING では、長期予測と短期予測の組み合わせをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="0f995-107">You will learn about two other important parameters for the Microsoft Time Series algorithm: FORECAST_METHOD, which lets you control the method used for forecasting, and PREDICTION_SMOOTHING, which lets you customize the blend of long-term and short-term predictions.</span></span>  
  
3.  <span data-ttu-id="0f995-108">必要に応じて、不足値を帰属させる方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f995-108">Optionally, you will tell the algorithm how you want missing values to be imputed.</span></span>  
  
4.  <span data-ttu-id="0f995-109">すべての変更が完了したら、モデルを配置して処理します。</span><span class="sxs-lookup"><span data-stu-id="0f995-109">After all the changes have been made, you will deploy and process the model.</span></span>  
  
## <a name="setting-time-series-parameters"></a><span data-ttu-id="0f995-110">時系列のパラメーターの設定</span><span class="sxs-lookup"><span data-stu-id="0f995-110">Setting Time Series Parameters</span></span>  
 <span data-ttu-id="0f995-111">**周期性のヒント**</span><span class="sxs-lookup"><span data-stu-id="0f995-111">**Periodicity Hints**</span></span>  
  
 <span data-ttu-id="0f995-112">*PERIODICITY_HINT*パラメーターは、データに表示されると予想される追加の期間に関する情報をアルゴリズムに提供します。</span><span class="sxs-lookup"><span data-stu-id="0f995-112">The *PERIODICITY_HINT* parameter provides the algorithm with information about additional time periods that you expect to see in the data.</span></span> <span data-ttu-id="0f995-113">時系列モデルでは、既定でデータのパターンの検出が自動的に試行されますが、</span><span class="sxs-lookup"><span data-stu-id="0f995-113">By default, time series models will try to automatically detect a pattern in the data.</span></span> <span data-ttu-id="0f995-114">予想される周期が既にわかっている場合は、周期性のヒントを指定することでモデルの精度を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="0f995-114">However, if you already know the expected time cycle, providing a periodicity hint can potentially improve the accuracy of the model.</span></span> <span data-ttu-id="0f995-115">ただし、適切でない周期性のヒントを指定すると精度が低下することがあるため、どの値を使用すればよいか確信がない場合は、既定値を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0f995-115">However, if you provide the wrong periodicity hint, it can decrease accuracy; therefore, if you are not sure what value should be used, it is best to use the default.</span></span>  
  
 <span data-ttu-id="0f995-116">たとえば、このモデルで使用されるビューでは、1 か月ごとに [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] から売上データが集計されます。</span><span class="sxs-lookup"><span data-stu-id="0f995-116">For example, the view used for this model aggregates sales data from [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] on a monthly basis.</span></span> <span data-ttu-id="0f995-117">したがって、このモデルで使用される各タイム スライスは 1 か月を表し、予測もすべて月単位で行われます。</span><span class="sxs-lookup"><span data-stu-id="0f995-117">Therefore each time slice used by the model represents one month, and all predictions will also be in terms of months.</span></span> <span data-ttu-id="0f995-118">1年に12か月があり、売上パターンが毎年繰り返されることが予想されるため、 *PERIODICITY_HINT*パラメーターをに設定して `12` 、12個のタイムスライス (月) が1つの完全な販売サイクルを構成することを示します。</span><span class="sxs-lookup"><span data-stu-id="0f995-118">Since there are 12 months in a year and you expect that sales patterns more or less repeat on a yearly basis, you will set the *PERIODICITY_HINT* parameter to `12`, to indicate that 12 time slices (months) constitute one complete sales cycle.</span></span>  
  
 <span data-ttu-id="0f995-119">**予測方法**</span><span class="sxs-lookup"><span data-stu-id="0f995-119">**Forecasting Method**</span></span>  
  
 <span data-ttu-id="0f995-120">*FORECAST_METHOD*パラメーターは、タイムシリーズアルゴリズムを短期または長期の予測用に最適化するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="0f995-120">The *FORECAST_METHOD* parameter controls whether the time series algorithm is optimized for short-term or long-term predictions.</span></span> <span data-ttu-id="0f995-121">既定では、 *FORECAST_METHOD*パラメーターは MIXED に設定されています。つまり、2つの異なるアルゴリズムがブレンドされ、短期予測と長期予測の両方に適した結果が得られるようになります。</span><span class="sxs-lookup"><span data-stu-id="0f995-121">By default, the *FORECAST_METHOD* parameter is set to MIXED, which means that two different algorithms are blended and balanced to provide good results for both short-term and long-term prediction.</span></span>  
  
 <span data-ttu-id="0f995-122">ただし、使用するアルゴリズムが決まっている場合は、ARIMA または ARTXP に値を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="0f995-122">However, if you know that you want to use a particular algorithm, you can change the value to either ARIMA or ARTXP.</span></span>  
  
 <span data-ttu-id="0f995-123">**長期的な予測と短期的な予測の重み付け**</span><span class="sxs-lookup"><span data-stu-id="0f995-123">**Weighting Long-Term vs. Short-Term Predictions**</span></span>  
  
 <span data-ttu-id="0f995-124">PREDICTION_SMOOTHING パラメーターを使用して、長期予測と短期予測の組み合わせ方法をカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0f995-124">You can also customize the way that long-term and short-term predictions are combined by using the PREDICTION_SMOOTHING parameter.</span></span> <span data-ttu-id="0f995-125">既定では、このパラメーターは 0.5 に設定されます。一般には、これが全体的な精度を確保するための最適なバランスです。</span><span class="sxs-lookup"><span data-stu-id="0f995-125">By default, this parameter is set to 0.5, which generally provides the best balance for overall accuracy.</span></span>  
  
#### <a name="to-change-the-algorithm-parameters"></a><span data-ttu-id="0f995-126">アルゴリズム パラメーターを変更するには</span><span class="sxs-lookup"><span data-stu-id="0f995-126">To change the algorithm parameters</span></span>  
  
1.  <span data-ttu-id="0f995-127">[**マイニングモデル**] タブで、[**予測**] を右クリックし、[**アルゴリズムパラメーターの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f995-127">On the **Mining Models** tab, right-click **Forecasting**, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="0f995-128">[ `PERIODICITY_HINT` **アルゴリズムパラメーター** ] ダイアログボックスの行で、[**値**] 列をクリックし、「 `{12}` 」と入力します (中かっこを含む)。</span><span class="sxs-lookup"><span data-stu-id="0f995-128">In the `PERIODICITY_HINT` row of the **Algorithm Parameters** dialog box, click the **Value** column, then type `{12}`, including the braces.</span></span>  
  
     <span data-ttu-id="0f995-129">既定で、値 {1} も追加されます。</span><span class="sxs-lookup"><span data-stu-id="0f995-129">By default, the algorithm will also add the value {1}.</span></span>  
  
3.  <span data-ttu-id="0f995-130">行で、 `FORECAST_METHOD` [**値**] テキストボックスが空白であるか、に設定されていることを確認し `MIXED` ます。</span><span class="sxs-lookup"><span data-stu-id="0f995-130">In the `FORECAST_METHOD` row, verify that the **Value** text box is either blank or set to `MIXED`.</span></span> <span data-ttu-id="0f995-131">別の値が入力されている場合は、「」と入力して `MIXED` パラメーターを既定値に戻します。</span><span class="sxs-lookup"><span data-stu-id="0f995-131">If a different value has been entered, type `MIXED` to change the parameter back to the default value.</span></span>  
  
4.  <span data-ttu-id="0f995-132">**PREDICTION_SMOOTHING**の行で、[**値**] テキストボックスが空白であるか、または0.5 に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0f995-132">In the **PREDICTION_SMOOTHING** row, verify that the **Value** text box is either blank or set to 0.5.</span></span> <span data-ttu-id="0f995-133">別の値を入力した場合は、[**値**] をクリックして、 `0.5` パラメーターを既定値に戻します。</span><span class="sxs-lookup"><span data-stu-id="0f995-133">If a different value has been entered, click **Value** and type `0.5` to change the parameter back to the default value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0f995-134">PREDICTION_SMOOTHING パラメーターは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f995-134">The PREDICTION_SMOOTHING parameter is available only in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="0f995-135">したがって、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard Edition では PREDICTION_SMOOTHING パラメーターの値を表示または変更できません。</span><span class="sxs-lookup"><span data-stu-id="0f995-135">Therefore, you cannot view or change the value of the PREDICTION_SMOOTHING parameter in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard.</span></span> <span data-ttu-id="0f995-136">ただし、既定の動作では両方のアルゴリズムが使用され、同等の重み付けが行われます。</span><span class="sxs-lookup"><span data-stu-id="0f995-136">However, the default behavior is to use both algorithms and weight them equally.</span></span>  
  
5.  <span data-ttu-id="0f995-137">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f995-137">Click **OK**.</span></span>  
  
## <a name="handling-missing-data-optional"></a><span data-ttu-id="0f995-138">不足データの処理 (オプション)</span><span class="sxs-lookup"><span data-stu-id="0f995-138">Handling Missing Data (Optional)</span></span>  
 <span data-ttu-id="0f995-139">売上データに NULL で埋められたギャップ (途切れ) が含まれていたり、店舗からのレポートが期限に間に合わなかったために系列の終了時点で空のセルが残されたりすることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="0f995-139">In many cases, your sales data might have gaps that are filled with nulls, or a store might have failed to meet the reporting deadline, leaving an empty cell at the end of the series.</span></span> <span data-ttu-id="0f995-140">このような場合は、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] から次のエラーが表示されてモデルが処理されません。</span><span class="sxs-lookup"><span data-stu-id="0f995-140">In such scenarios, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] raises the following error and will not process the model.</span></span>  
  
 <span data-ttu-id="0f995-141">"エラー (データマイニング): マイニングモデルの系列で始まるタイムスタンプが同期されていません \<series name> \<model name> 。</span><span class="sxs-lookup"><span data-stu-id="0f995-141">"Error (Data mining): Time stamps not synchronized starting with series \<series name>, of the mining model, \<model name>.</span></span> <span data-ttu-id="0f995-142">すべての時系列は同一の時点で終了する必要があります。また、データ消失点をそれぞれが任意に持つこともできません。</span><span class="sxs-lookup"><span data-stu-id="0f995-142">All time series must end at the same time mark and cannot have arbitrarily missing data points.</span></span> <span data-ttu-id="0f995-143">MISSING_VALUE_SUBSTITUTION パラメーターを Previous または数値定数に設定すると、可能な場所にデータ消失点が自動的に設定されます。"</span><span class="sxs-lookup"><span data-stu-id="0f995-143">Setting the MISSING_VALUE_SUBSTITUTION parameter to Previous or to a numeric constant will automatically patch missing data points where possible."</span></span>  
  
 <span data-ttu-id="0f995-144">このエラーを回避するには、次のいずれかの方法で、ギャップを埋めるための新しい値が [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] から自動的に提供されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="0f995-144">To avoid this error, you can specify that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatically provide new values to fill in the gaps by using any one of the following methods:</span></span>  
  
-   <span data-ttu-id="0f995-145">平均値を使用する。</span><span class="sxs-lookup"><span data-stu-id="0f995-145">Using an average value.</span></span> <span data-ttu-id="0f995-146">平均は、同じデータ系列のすべての有効値を使用して計算されます。</span><span class="sxs-lookup"><span data-stu-id="0f995-146">The mean is calculated by using all valid values in the same data series.</span></span>  
  
-   <span data-ttu-id="0f995-147">前の値を使用する。</span><span class="sxs-lookup"><span data-stu-id="0f995-147">Using the previous value.</span></span> <span data-ttu-id="0f995-148">複数の不足セルに前の値を割り当てることは可能ですが、開始値を埋めることはできません。</span><span class="sxs-lookup"><span data-stu-id="0f995-148">You can substitute previous values for multiple missing cells, but you cannot fill starting values.</span></span>  
  
-   <span data-ttu-id="0f995-149">指定した定数値を使用する。</span><span class="sxs-lookup"><span data-stu-id="0f995-149">Using a constant value that you supply.</span></span>  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a><span data-ttu-id="0f995-150">値の平均を計算してギャップを埋めるように指定するには</span><span class="sxs-lookup"><span data-stu-id="0f995-150">To specify that gaps be filled by averaging values</span></span>  
  
1.  <span data-ttu-id="0f995-151">[**マイニングモデル**] タブで、[**予測**] 列を右クリックし、[**アルゴリズムパラメーターの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f995-151">On the **Mining Models** tab, right-click the **Forecasting** column, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="0f995-152">[**アルゴリズムパラメーター** ] ダイアログボックスの [ **MISSING_VALUE_SUBSTITUTION** ] 行で、[**値**] 列をクリックし、「」と入力し `Mean` ます。</span><span class="sxs-lookup"><span data-stu-id="0f995-152">In the **Algorithm Parameters** dialog box, in the **MISSING_VALUE_SUBSTITUTION** row, click the **Value** column, and type `Mean`.</span></span>  
  
## <a name="build-the-model"></a><span data-ttu-id="0f995-153">モデルを構築する</span><span class="sxs-lookup"><span data-stu-id="0f995-153">Build the Model</span></span>  
 <span data-ttu-id="0f995-154">モデルを使用するには、サーバーにモデルを配置し、アルゴリズムを使用してトレーニング データを実行することでそのモデルを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f995-154">To use the model, you must deploy it to a server, and process the model by running the training data through the algorithm.</span></span>  
  
#### <a name="to-process-the-forecasting-model"></a><span data-ttu-id="0f995-155">予測モデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="0f995-155">To process the forecasting model</span></span>  
  
1.  <span data-ttu-id="0f995-156">の [**マイニングモデル**] メニューで、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] [**マイニング構造とすべてのモデルの処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0f995-156">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], select **Process Mining Structure and All Models**.</span></span>  
  
2.  <span data-ttu-id="0f995-157">プロジェクトをビルドして配置するかどうかを確認する警告が表示されたら、[**はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f995-157">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="0f995-158">[**マイニング構造の処理-予測**] ダイアログボックスで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f995-158">In the **Process Mining Structure - Forecasting** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="0f995-159">[**処理の進行状況**] ダイアログボックスが開き、モデルの処理に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f995-159">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="0f995-160">モデルの処理には、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="0f995-160">Model processing may take some time.</span></span>  
  
4.  <span data-ttu-id="0f995-161">処理が完了したら、[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0f995-161">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="0f995-162">もう一度 [**閉じる**] をクリックして、[**マイニング構造の処理-予測**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0f995-162">Click **Close** again to exit the **Process Mining Structure - Forecasting** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="0f995-163">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="0f995-163">Next Task in Lesson</span></span>  
 [<span data-ttu-id="0f995-164">予測モデル &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="0f995-164">Exploring the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="0f995-165">参照</span><span class="sxs-lookup"><span data-stu-id="0f995-165">See Also</span></span>  
 <span data-ttu-id="0f995-166">[Microsoft タイムシリーズアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0f995-166">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="0f995-167">[Microsoft タイムシリーズアルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="0f995-167">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 [<span data-ttu-id="0f995-168">処理の要件および注意事項 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="0f995-168">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
