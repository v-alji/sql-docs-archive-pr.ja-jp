---
title: 予測モデルの予測の比較 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ead8a1fe-60d8-4017-8fb8-6fe32168e46d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 63cf9c001298b0d2bfd2cf35ed42485a16817fd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720504"
---
# <a name="comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="141f7-102">予測モデルの予測の比較 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="141f7-102">Comparing Predictions for Forecasting Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="141f7-103">このチュートリアルのこれまでの手順では、複数の時系列モデルを作成しました。</span><span class="sxs-lookup"><span data-stu-id="141f7-103">In the previous steps of this tutorial, you created multiple time series models:</span></span>  
  
-   <span data-ttu-id="141f7-104">個々のモデルと地域のデータのみに基づく地域とモデルの組み合わせごとの予測</span><span class="sxs-lookup"><span data-stu-id="141f7-104">Predictions for each combination of region and model, based only on data for the individual model and region.</span></span>  
  
-   <span data-ttu-id="141f7-105">更新したデータに基づく地域ごとの予測</span><span class="sxs-lookup"><span data-stu-id="141f7-105">Predictions for each region, based on updated data.</span></span>  
  
-   <span data-ttu-id="141f7-106">集計データに基づく全世界におけるすべてのモデルの予測</span><span class="sxs-lookup"><span data-stu-id="141f7-106">Predictions for all models on a worldwide basis, based on aggregated data.</span></span>  
  
-   <span data-ttu-id="141f7-107">集計モデルに基づく北米地域の M200 モデルの予測</span><span class="sxs-lookup"><span data-stu-id="141f7-107">Predictions for the M200 model in the North America region, based on the aggregated model.</span></span>  
  
 <span data-ttu-id="141f7-108">時系列予測の機能をまとめるため、変更を検討し、データを拡張または置換するオプションの使用が予測結果に与えた影響を確認します。</span><span class="sxs-lookup"><span data-stu-id="141f7-108">To summarize the features for time series predictions, you will review the changes to see how the use of the options to extend or replace data affected forecasting results.</span></span>  
  
 [<span data-ttu-id="141f7-109">EXTEND_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="141f7-109">EXTEND_MODEL_CASES</span></span>](#bkmk_EXTEND)  
  
 [<span data-ttu-id="141f7-110">REPLACE_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="141f7-110">REPLACE_MODEL_CASES</span></span>](#bkmk_REPLACE)  
  
##  <a name="comparing-the-original-results-with-results-after-adding-data"></a><a name="bkmk_EXTEND"></a><span data-ttu-id="141f7-111">データを追加した後の結果と元の結果の比較</span><span class="sxs-lookup"><span data-stu-id="141f7-111">Comparing the Original Results with Results after Adding Data</span></span>  
 <span data-ttu-id="141f7-112">太平洋地域の M200 製品ラインのデータだけを見て、新しいデータでモデルを更新することによって結果にどのような影響があるかを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="141f7-112">Let's look at the data for just the M200 product line in the Pacific region, to see how updating the model with new data affects the results.</span></span> <span data-ttu-id="141f7-113">元のデータ系列は 2004 年 6 月に終了し、7 月、8 月、9 月の新しいデータを取得したことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="141f7-113">Remember that the original data series ended in June 2004, and we obtained new data for July, August, and September.</span></span>  
  
-   <span data-ttu-id="141f7-114">最初の列は、追加された新しいデータを示します。</span><span class="sxs-lookup"><span data-stu-id="141f7-114">The first column shows the new data that was added.</span></span>  
  
-   <span data-ttu-id="141f7-115">2 番目の列は、元のデータ系列に基づく 7 月以降の予測を示しています。</span><span class="sxs-lookup"><span data-stu-id="141f7-115">The second column shows the forecast for July and later based on the original data series.</span></span>  
  
-   <span data-ttu-id="141f7-116">3 番目の列は、拡張したデータに基づく予測を示しています。</span><span class="sxs-lookup"><span data-stu-id="141f7-116">The third column shows the forecast based on the extended data.</span></span>  
  
|<span data-ttu-id="141f7-117">**M200 太平洋**</span><span class="sxs-lookup"><span data-stu-id="141f7-117">**M200 Pacific**</span></span>|<span data-ttu-id="141f7-118">更新された実売上データ</span><span class="sxs-lookup"><span data-stu-id="141f7-118">Updated real sales data</span></span>|<span data-ttu-id="141f7-119">データを追加する前の予測</span><span class="sxs-lookup"><span data-stu-id="141f7-119">Forecast before data was added</span></span>|<span data-ttu-id="141f7-120">拡張された予測</span><span class="sxs-lookup"><span data-stu-id="141f7-120">Extended prediction</span></span>|  
|----------------------|-----------------------------|------------------------------------|-------------------------|  
|<span data-ttu-id="141f7-121">7-25-2008</span><span class="sxs-lookup"><span data-stu-id="141f7-121">7-25-2008</span></span>|<span data-ttu-id="141f7-122">**65**</span><span class="sxs-lookup"><span data-stu-id="141f7-122">**65**</span></span>|<span data-ttu-id="141f7-123">32</span><span class="sxs-lookup"><span data-stu-id="141f7-123">32</span></span>|<span data-ttu-id="141f7-124">**65**</span><span class="sxs-lookup"><span data-stu-id="141f7-124">**65**</span></span>|  
|<span data-ttu-id="141f7-125">8-25-2008</span><span class="sxs-lookup"><span data-stu-id="141f7-125">8-25-2008</span></span>|<span data-ttu-id="141f7-126">**54**</span><span class="sxs-lookup"><span data-stu-id="141f7-126">**54**</span></span>|<span data-ttu-id="141f7-127">37</span><span class="sxs-lookup"><span data-stu-id="141f7-127">37</span></span>|<span data-ttu-id="141f7-128">**54**</span><span class="sxs-lookup"><span data-stu-id="141f7-128">**54**</span></span>|  
|<span data-ttu-id="141f7-129">9-25-2008</span><span class="sxs-lookup"><span data-stu-id="141f7-129">9-25-2008</span></span>|<span data-ttu-id="141f7-130">**61**</span><span class="sxs-lookup"><span data-stu-id="141f7-130">**61**</span></span>|<span data-ttu-id="141f7-131">32</span><span class="sxs-lookup"><span data-stu-id="141f7-131">32</span></span>|<span data-ttu-id="141f7-132">**61**</span><span class="sxs-lookup"><span data-stu-id="141f7-132">**61**</span></span>|  
|<span data-ttu-id="141f7-133">10-25-2008</span><span class="sxs-lookup"><span data-stu-id="141f7-133">10-25-2008</span></span>|<span data-ttu-id="141f7-134">データなし</span><span class="sxs-lookup"><span data-stu-id="141f7-134">No data</span></span>|<span data-ttu-id="141f7-135">36</span><span class="sxs-lookup"><span data-stu-id="141f7-135">36</span></span>|<span data-ttu-id="141f7-136">32</span><span class="sxs-lookup"><span data-stu-id="141f7-136">32</span></span>|  
|<span data-ttu-id="141f7-137">11-25-2008</span><span class="sxs-lookup"><span data-stu-id="141f7-137">11-25-2008</span></span>|<span data-ttu-id="141f7-138">データなし</span><span class="sxs-lookup"><span data-stu-id="141f7-138">No data</span></span>|<span data-ttu-id="141f7-139">31</span><span class="sxs-lookup"><span data-stu-id="141f7-139">31</span></span>|<span data-ttu-id="141f7-140">41</span><span class="sxs-lookup"><span data-stu-id="141f7-140">41</span></span>|  
|<span data-ttu-id="141f7-141">12-25-2008</span><span class="sxs-lookup"><span data-stu-id="141f7-141">12-25-2008</span></span>|<span data-ttu-id="141f7-142">データなし</span><span class="sxs-lookup"><span data-stu-id="141f7-142">No data</span></span>|<span data-ttu-id="141f7-143">34</span><span class="sxs-lookup"><span data-stu-id="141f7-143">34</span></span>|<span data-ttu-id="141f7-144">32</span><span class="sxs-lookup"><span data-stu-id="141f7-144">32</span></span>|  
  
 <span data-ttu-id="141f7-145">拡張データを使用した予測 (ここでは太字で表示) が実際のデータ ポイントを正確に繰り返していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="141f7-145">You will note that the forecasts using the extended data (shown here in bold) repeat the real data points exactly.</span></span> <span data-ttu-id="141f7-146">この繰り返しは、意図的なものです。</span><span class="sxs-lookup"><span data-stu-id="141f7-146">The repetition is by design.</span></span> <span data-ttu-id="141f7-147">予測クエリは、使用する実データ ポイントがある限りは実際の値を返し、新しい実際のデータ ポイントをすべて使用した後でのみ新しい予測値を出力します。</span><span class="sxs-lookup"><span data-stu-id="141f7-147">As long as there are real data points to use, the prediction query will return the actual values, and output new prediction values only after the new actual data points have been used up.</span></span>  
  
 <span data-ttu-id="141f7-148">一般に、アルゴリズムでは、モデル データの開始からのデータより、新しいデータでの変更に、より大きい重みを設定します。</span><span class="sxs-lookup"><span data-stu-id="141f7-148">In general, the algorithm weights the changes in the new data more strongly than data from the beginning of the model data.</span></span> <span data-ttu-id="141f7-149">しかし、このケースでは、新しい売上の値は前の期間に対して 20 ～ 30% だけの増加を示しているので、予測される売上にはわずかな上昇しかなく、その後の売上予測は再度下降して、新しいデータの前の数か月の傾向と同じようになっています。</span><span class="sxs-lookup"><span data-stu-id="141f7-149">However, in this case, the new sales figures represent an increase of only 20-30 percent over the previous period, so there only was a slight uptick in projected sales, after which the sales projections drop again, more in line with the trend in the months before the new data.</span></span>  
  
##  <a name="comparing-the-original-and-cross-prediction-results"></a><a name="bkmk_REPLACE"></a><span data-ttu-id="141f7-150">元の結果とクロス予測の結果を比較する</span><span class="sxs-lookup"><span data-stu-id="141f7-150">Comparing the Original and Cross-Prediction Results</span></span>  
 <span data-ttu-id="141f7-151">元のマイニング モデルでは、地域と製品ラインの間に大きな差が見られました。</span><span class="sxs-lookup"><span data-stu-id="141f7-151">Remember that the original mining model revealed big differences between regions and between product lines.</span></span> <span data-ttu-id="141f7-152">たとえば、M200 モデルの売上は非常に強い一方で、T1000 モデルの売上はすべての地域でかなり低くなっています。</span><span class="sxs-lookup"><span data-stu-id="141f7-152">For example, sales for the M200 model were very strong, while sales for the T1000 model were fairly low across all regions.</span></span> <span data-ttu-id="141f7-153">さらに、一部の系列には多くのデータがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="141f7-153">Moreover, some series didn't have much data.</span></span> <span data-ttu-id="141f7-154">系列は不規則で、開始点が同じではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="141f7-154">Series were ragged, meaning they didn't have the same starting point.</span></span>  
  
 <span data-ttu-id="141f7-155">![M200 および T1000 の数量を予測するシリーズ](../../2014/tutorials/media/6series-defaultforecasting.gif "M200 および T1000 の数量を予測するシリーズ")</span><span class="sxs-lookup"><span data-stu-id="141f7-155">![Series predicting M200 and T1000 quantity](../../2014/tutorials/media/6series-defaultforecasting.gif "Series predicting M200 and T1000 quantity")</span></span>  
  
 <span data-ttu-id="141f7-156">元のデータ セットではなく世界的な売上に基づく汎用モデルに基づく予測を行うと、どのように変化したでしょうか。</span><span class="sxs-lookup"><span data-stu-id="141f7-156">So how did the predictions change when you made your projections based on the general model, which was based on world-wide sales, rather than the original data sets?</span></span> <span data-ttu-id="141f7-157">情報が失われたり予測が偏ったりしていないことを確認するには、結果をテーブルに保存し、予測のテーブルを履歴データのテーブルに結合して、履歴データと予測の 2 セットをグラフ化します。</span><span class="sxs-lookup"><span data-stu-id="141f7-157">To assure yourself that you have not lost any information or skewed the predictions, you can save the results to a table, join the table of predictions to the table of historical data, and then graph the two sets of historical data and predictions.</span></span>  
  
 <span data-ttu-id="141f7-158">次の図は、ただ 1 つの製品ライン M200 に基づいています。</span><span class="sxs-lookup"><span data-stu-id="141f7-158">The following diagram is based on just one product line, the M200.</span></span> <span data-ttu-id="141f7-159">グラフでは、初期のマイニング モデルによる予測と、集計されたマイニング モデルによる予測が比較されます。</span><span class="sxs-lookup"><span data-stu-id="141f7-159">The graph compares the predictions from the initial mining model against the predictions using the aggregated mining model.</span></span>  
  
 <span data-ttu-id="141f7-160">![予測を比較する Excel グラフ](../../2014/tutorials/media/m200-predictions-compared.gif "予測を比較する Excel グラフ")</span><span class="sxs-lookup"><span data-stu-id="141f7-160">![Excel chart comparing predictions](../../2014/tutorials/media/m200-predictions-compared.gif "Excel chart comparing predictions")</span></span>  
  
 <span data-ttu-id="141f7-161">この図からは、個々のデータ系列の変動を最小限に抑えると同時に、集計マイニング モデルによって値の全体的な範囲と傾向が保持されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="141f7-161">From this diagram, you can see that the aggregated mining model preserves the overall range and trends in values while minimizing the fluctuations in the individual data series.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="141f7-162">まとめ</span><span class="sxs-lookup"><span data-stu-id="141f7-162">Conclusion</span></span>  
 <span data-ttu-id="141f7-163">予測に使用できる時系列モデルを作成してカスタマイズする方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="141f7-163">You have learned how to create and to customize a time series model that can be used for forecasting.</span></span>  
  
 <span data-ttu-id="141f7-164">新しいデータを追加し、パラメーター EXTEND_MODEL_CASES を使用して予測を作成することによって、時系列モデルを再処理することなく更新する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="141f7-164">You have learned to update your time series models without having to reprocess them, by adding new data and creating predictions using the parameter, EXTEND_MODEL_CASES.</span></span>  
  
 <span data-ttu-id="141f7-165">REPLACE_MODEL_CASES パラメーターを使用し、異なるデータ系列にモデルを適用することによって、クロス予測に使用できるモデルを作成する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="141f7-165">You have learned to create models that can be used for cross-prediction, by using the REPLACE_MODEL_CASES parameter and applying the model to a different data series.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="141f7-166">参照</span><span class="sxs-lookup"><span data-stu-id="141f7-166">See Also</span></span>  
 <span data-ttu-id="141f7-167">[中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="141f7-167">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="141f7-168">Time Series Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="141f7-168">Time Series Model Query Examples</span></span>](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
