---
title: '[クロス検証] タブ ([マイニング精度チャート] ビュー)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.crossvalidation.f1
ms.assetid: bd215a68-1ad7-4046-9c44-ec8e2be13a64
author: minewiskan
ms.author: owend
ms.openlocfilehash: 867bd6d1abffb29ec3eb2a8a78e562e5cbcc5b29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639821"
---
# <a name="cross-validation-tab-mining-accuracy-chart-view"></a><span data-ttu-id="68035-102">[相互検証] タブ ([マイニング精度チャート] ビュー)</span><span class="sxs-lookup"><span data-stu-id="68035-102">Cross-Validation Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="68035-103">相互検証では、マイニング構造をセクションにパーティション分割し、それぞれのセクションに対してモデルのトレーニングとテストを反復的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="68035-103">Cross-validation lets you partition a mining structure into cross-sections and iteratively train and test models against each cross-section.</span></span> <span data-ttu-id="68035-104">データの分割先のフォールドをいくつか指定します。それぞれのフォールドは、順にテスト データとして使用されます。一方、残りのデータは、新しいモデルのトレーニングに使用されます。</span><span class="sxs-lookup"><span data-stu-id="68035-104">You specify a number of folds to divide the data into, and each fold is used in turn as the test data, whereas the remaining data is used to train a new model.</span></span> <span data-ttu-id="68035-105">その後、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] により、それぞれのモデルに対して標準的な精度の基準のセットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="68035-105">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] then generates a set of standard accuracy metrics for each model.</span></span> <span data-ttu-id="68035-106">それぞれのセクションに対して生成されるモデルの基準を比較することで、データセット全体に対するマイニング モデルの信頼性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="68035-106">By comparing the metrics for the models generated for each cross-section, you can get a good idea of how reliable the mining model is for the whole data set.</span></span>  
  
 <span data-ttu-id="68035-107">詳細については、「[相互検証 (Analysis Services - データ マイニング)](data-mining/cross-validation-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68035-107">For more information, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](data-mining/cross-validation-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68035-108">相互検証は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムや [!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して作成されたモデルには使用できません。</span><span class="sxs-lookup"><span data-stu-id="68035-108">Cross-validation cannot be used with models that were built by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span> <span data-ttu-id="68035-109">これらの種類のモデルを含むマイニング構造に対してレポートを実行した場合、これらのモデルはレポートに含められません。</span><span class="sxs-lookup"><span data-stu-id="68035-109">If you run the report on a mining structure that contains these types of models, the models will not be included in the report.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="68035-110">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="68035-110">Task List</span></span>  
  
-   <span data-ttu-id="68035-111">フォールドの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="68035-111">Specify the number of folds.</span></span>  
  
-   <span data-ttu-id="68035-112">相互検証に使用するケースの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="68035-112">Specify the maximum number of cases to use for cross-validation.</span></span>  
  
-   <span data-ttu-id="68035-113">予測可能列を指定します。</span><span class="sxs-lookup"><span data-stu-id="68035-113">Specify the predictable column.</span></span>  
  
-   <span data-ttu-id="68035-114">必要に応じて、予測可能な状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="68035-114">Optionally, specify a predictable state.</span></span>  
  
-   <span data-ttu-id="68035-115">必要に応じて、予測の精度の評価方法を制御するパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="68035-115">Optionally, set parameters that control how the accuracy of prediction is assessed.</span></span>  
  
-   <span data-ttu-id="68035-116">**[結果の取得]** をクリックして相互検証の結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="68035-116">Click **Get Results** to display the results of cross-validation.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="68035-117">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="68035-117">UI element list</span></span>  
 <span data-ttu-id="68035-118">**フォールドカウント**</span><span class="sxs-lookup"><span data-stu-id="68035-118">**Fold Count**</span></span>  
 <span data-ttu-id="68035-119">作成するフォールド (パーティション) の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="68035-119">Specify the number of folds, or partitions, to create.</span></span> <span data-ttu-id="68035-120">最小値は 2 です。この値は、データセットの半分をテスト用に、もう半分をトレーニング用に使用することを表します。</span><span class="sxs-lookup"><span data-stu-id="68035-120">The minimum value is 2, meaning that half the data set is used for testing and half for training.</span></span>  
  
 <span data-ttu-id="68035-121">セッション マイニング構造の最大値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="68035-121">The maximum value is 10 for session mining structures.</span></span>  
  
 <span data-ttu-id="68035-122">マイニング構造が [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに格納されている場合の最大値は 256 です。</span><span class="sxs-lookup"><span data-stu-id="68035-122">The maximum value is 256 if the mining structure is stored in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68035-123">フォールドの数を増やすほど、クロス検証の実行に必要な時間もその分だけ長くなります。</span><span class="sxs-lookup"><span data-stu-id="68035-123">As you increase the number of folds, the time that is required to perform cross-validation similarly increases by n.</span></span> <span data-ttu-id="68035-124">ケースの数が多く、 **[フォールド カウント]** の値も大きい場合は、パフォーマンス上の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68035-124">You might experience performance issues if the number of cases is large and the value of **Fold Count** is also large.</span></span>  
  
 <span data-ttu-id="68035-125">**[ケースの最大数]**</span><span class="sxs-lookup"><span data-stu-id="68035-125">**Max Cases**</span></span>  
 <span data-ttu-id="68035-126">相互検証に使用するケースの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="68035-126">Specify the maximum number of cases to use for cross-validation.</span></span> <span data-ttu-id="68035-127">特定のフォールド内のケースの数は、 **[ケースの最大数]** の値を **[フォールド カウント]** の値で除算した結果と等しくなります。</span><span class="sxs-lookup"><span data-stu-id="68035-127">The number of cases in any particular fold is equal to the **Max Cases** value divided by the **Fold Count** value.</span></span>  
  
 <span data-ttu-id="68035-128">**0**を指定した場合、ソース データ内のすべてのケースが相互検証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="68035-128">If you use **0**, all cases in the source data are used for cross-validation.</span></span>  
  
 <span data-ttu-id="68035-129">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="68035-129">There is no default value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68035-130">ケースの数を増やすほど、処理時間も長くなります。</span><span class="sxs-lookup"><span data-stu-id="68035-130">As you increase the number of cases, processing time also increases.</span></span>  
  
 <span data-ttu-id="68035-131">**ターゲット属性**</span><span class="sxs-lookup"><span data-stu-id="68035-131">**Target Attribute**</span></span>  
 <span data-ttu-id="68035-132">すべてのモデル内で検出された予測可能列の一覧から列を選択します。</span><span class="sxs-lookup"><span data-stu-id="68035-132">Select a column from the list of predictable columns found in all models.</span></span> <span data-ttu-id="68035-133">相互検証を実行するごとに選択できる予測可能列は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="68035-133">You can only select one predictable column every time that you perform cross-validation.</span></span>  
  
 <span data-ttu-id="68035-134">クラスター モデルのみをテストするには、 **[クラスター]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68035-134">To test only clustering models, select **Cluster**.</span></span>  
  
 <span data-ttu-id="68035-135">**ターゲットの状態**</span><span class="sxs-lookup"><span data-stu-id="68035-135">**Target State**</span></span>  
 <span data-ttu-id="68035-136">値を入力するか、または値のドロップダウン リストから対象の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="68035-136">Type a value, or select a target value from a drop-down list of values.</span></span>  
  
 <span data-ttu-id="68035-137">既定値は `null` で、すべての状態をテストすることを示します。</span><span class="sxs-lookup"><span data-stu-id="68035-137">The default value is `null`, indicating that all states are to be tested.</span></span>  
  
 <span data-ttu-id="68035-138">クラスター モデルの場合は無効になります。</span><span class="sxs-lookup"><span data-stu-id="68035-138">Disabled for clustering models.</span></span>  
  
 <span data-ttu-id="68035-139">**対象**の**しきい値**  </span><span class="sxs-lookup"><span data-stu-id="68035-139">**Target**  **Threshold**</span></span>  
 <span data-ttu-id="68035-140">予測確率を表す 0 ～ 1 の範囲の値を指定します。確率がこの値を超える場合、予測された状態は正しいと見なされます。</span><span class="sxs-lookup"><span data-stu-id="68035-140">Specify a value between 0 and 1 that indicates the prediction probability above which a predicted state is considered to be correct.</span></span> <span data-ttu-id="68035-141">値は 0.1 単位で設定できます。</span><span class="sxs-lookup"><span data-stu-id="68035-141">The value can be set in 0.1 increments.</span></span>  
  
 <span data-ttu-id="68035-142">既定値は `null` です。この場合、最も確率の高い予測が正しいと見なされます。</span><span class="sxs-lookup"><span data-stu-id="68035-142">The default is `null`, indicating that the most probable prediction is counted as correct.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68035-143">この値を 0.0 に設定することはできますが、その場合、処理時間が長くなるだけでなく、有意な結果も生成されません。</span><span class="sxs-lookup"><span data-stu-id="68035-143">Although you can set the value to 0.0, using this value will increase processing time and not yield meaningful results.</span></span>  
  
 <span data-ttu-id="68035-144">**[結果の取得]**</span><span class="sxs-lookup"><span data-stu-id="68035-144">**Get Results**</span></span>  
 <span data-ttu-id="68035-145">クリックすると、指定したパラメーターを使用して、モデルの相互検証が開始されます。</span><span class="sxs-lookup"><span data-stu-id="68035-145">Click to begin cross-validation of the model using the specified parameters.</span></span>  
  
 <span data-ttu-id="68035-146">モデルは指定した数のフォールドにパーティション分割され、フォールドごとに別個のモデルがテストされます。</span><span class="sxs-lookup"><span data-stu-id="68035-146">The model is partitioned into the specified number of folds and a separate model is tested for each fold.</span></span> <span data-ttu-id="68035-147">したがって、相互検証の結果が返されるまでに時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="68035-147">Therefore, it might take some time for cross-validation to return the results.</span></span>  
  
 <span data-ttu-id="68035-148">相互検証レポートに表示された結果の解釈方法の詳細については、「 [相互検証レポートのメジャー](data-mining/measures-in-the-cross-validation-report.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68035-148">For more information about how to interpret the results of the cross-validation report, see [Measures in the Cross-Validation Report](data-mining/measures-in-the-cross-validation-report.md).</span></span>  
  
## <a name="setting-the-accuracy-threshold"></a><span data-ttu-id="68035-149">精度のしきい値の設定</span><span class="sxs-lookup"><span data-stu-id="68035-149">Setting the Accuracy Threshold</span></span>  
 <span data-ttu-id="68035-150">**[対象の** **しきい値]** の値を設定することで、予測精度を測定する場合の基準を制御できます。</span><span class="sxs-lookup"><span data-stu-id="68035-150">You can control the standard for measuring prediction accuracy by setting a value for **Target** **Threshold**.</span></span> <span data-ttu-id="68035-151">しきい値は、精度バーの種類を表します。</span><span class="sxs-lookup"><span data-stu-id="68035-151">A threshold represents a kind of accuracy bar.</span></span> <span data-ttu-id="68035-152">それぞれの予測に対して、予測される値が正しいと見なされる確率が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="68035-152">Each prediction is assigned a probability that the predicted value is correct.</span></span> <span data-ttu-id="68035-153">したがって、**[対象の** **しきい値]** に 1 に近い値を設定した場合、確率が非常に高い特定の予測を良い予測として数えるように指定していることになります。</span><span class="sxs-lookup"><span data-stu-id="68035-153">Therefore, if you set the **Target** **Threshold** value closer to 1, you are requiring that the probability for any particular prediction to be fairly high to be counted as a good prediction.</span></span> <span data-ttu-id="68035-154">逆に、**[対象の** **しきい値]** に 0 に近い値を設定した場合、確率が低い予測であっても "良い" 予測として数えられます。</span><span class="sxs-lookup"><span data-stu-id="68035-154">Conversely, if you set **Target** **Threshold** closer to 0, even predictions with lower probability values are counted as "good" predictions.</span></span>  
  
 <span data-ttu-id="68035-155">予測の確率はデータの量や予測の種類に依存するので、推奨されるしきい値はありません。</span><span class="sxs-lookup"><span data-stu-id="68035-155">There is no recommended threshold value because the probability of any prediction depends on the amount of data and the type of prediction you are making.</span></span> <span data-ttu-id="68035-156">異なる確率レベルの予測を調査したうえで、データに適した精度バーを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68035-156">You should review some predictions at different probability levels to determine an appropriate accuracy bar for your data.</span></span> <span data-ttu-id="68035-157">この作業は重要です。なぜなら、**[対象の** **しきい値]** に設定する値は、測定されるモデルの精度に影響を与えるからです。</span><span class="sxs-lookup"><span data-stu-id="68035-157">It is important that you do this, because the value that you set for **Target** **Threshold** affects the measured accuracy of the model.</span></span>  
  
 <span data-ttu-id="68035-158">たとえば、特定の対象の状態に対して 3 つの予測を作成し、それぞれの予測の確率が 0.05、0.15、および 0.8 であるとします。</span><span class="sxs-lookup"><span data-stu-id="68035-158">For example, suppose three predictions are made for a particular target state, and the probabilities of each prediction are 0.05, 0.15, and 0.8.</span></span> <span data-ttu-id="68035-159">ここで、しきい値を 0.5 に設定した場合、1 つの予測だけが正しい予測であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="68035-159">If you set the threshold to 0.5, only one prediction is counted as being correct.</span></span> <span data-ttu-id="68035-160">また、**[対象の** **しきい値]** を 0.10 に設定した場合は、2 つの予測が正しい予測であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="68035-160">If you set **Target** **Threshold** to 0.10, two predictions are counted as being correct.</span></span>  
  
 <span data-ttu-id="68035-161">[**対象**の**しきい**値] を (既定値) に設定すると、 `null` 各ケースに対して最も可能性の高い予測が正しいものとしてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="68035-161">When **Target** **Threshold** is set to `null`, which is the default value, the most probable prediction for each case is counted as correct.</span></span> <span data-ttu-id="68035-162">前の例では、0.05、0.15、および 0.8 が、3 つの異なるケースの予測の確率です。</span><span class="sxs-lookup"><span data-stu-id="68035-162">In the example just cited, 0.05, 0.15, and 0.8 are the probabilities for predictions in three different cases.</span></span> <span data-ttu-id="68035-163">これらの値は大きく異なりますが、それぞれの予測はすべて正しいものと見なされます。なぜなら、それぞれのケースで生成された予測はそれぞれ 1 つであり、これらの予測はそのケースで最善の予測であるからです。</span><span class="sxs-lookup"><span data-stu-id="68035-163">Although the probabilities are very different, each prediction would be counted as correct, because each case generates only one prediction and these are the best predictions for these cases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68035-164">参照</span><span class="sxs-lookup"><span data-stu-id="68035-164">See Also</span></span>  
 <span data-ttu-id="68035-165">[データマイニング&#41;のテストと検証 &#40;](data-mining/testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="68035-165">[Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md) </span></span>  
 <span data-ttu-id="68035-166">[クロス検証 &#40;Analysis Services-データマイニング&#41;](data-mining/cross-validation-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="68035-166">[Cross-Validation &#40;Analysis Services - Data Mining&#41;](data-mining/cross-validation-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="68035-167">[相互検証レポートのメジャー](data-mining/measures-in-the-cross-validation-report.md) </span><span class="sxs-lookup"><span data-stu-id="68035-167">[Measures in the Cross-Validation Report](data-mining/measures-in-the-cross-validation-report.md) </span></span>  
 [<span data-ttu-id="68035-168">データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="68035-168">Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;</span></span>](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
