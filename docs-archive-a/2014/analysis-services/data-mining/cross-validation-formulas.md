---
title: クロス検証数式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fd1ea582-29a1-4154-8de2-47bab3539b4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 878d88f695b2cdbf3c999c54568304accc54e3d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639809"
---
# <a name="cross-validation-formulas"></a><span data-ttu-id="14d0d-102">クロス検証の式</span><span class="sxs-lookup"><span data-stu-id="14d0d-102">Cross-Validation Formulas</span></span>
  <span data-ttu-id="14d0d-103">生成したクロス検証レポートには、マイニング モデルの種類 (つまり、モデルの作成に使用したアルゴリズム)、予測可能な属性のデータ型、および予測可能な属性の値に応じて、モデルごとの精度のメジャーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-103">When you generate a cross-validation report, it contains accuracy measures for each model, depending on the type of mining model (that is, the algorithm that was used to create the model), the data type of the predictable attribute, and the predictable attribute value, if any.</span></span>  
  
 <span data-ttu-id="14d0d-104">このセクションでは、クロス検証レポートで使用されるメジャーを示し、計算の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="14d0d-104">This section lists the measures used in the cross-validation report and describes the method of calculation.</span></span>  
  
 <span data-ttu-id="14d0d-105">モデルの種類ごとの精度のメジャーについて詳しくは、「 [相互検証レポートのメジャー](measures-in-the-cross-validation-report.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="14d0d-105">For a breakdown of the accuracy measures by model type, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
## <a name="formulas-used-for-cross-validation-measures"></a><span data-ttu-id="14d0d-106">クロス検証のメジャーで使用される数式</span><span class="sxs-lookup"><span data-stu-id="14d0d-106">Formulas used for Cross-Validation Measures</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14d0d-107">**重要:** これらの精度のメジャーは、対象の属性ごとに計算されます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-107">**Important:** These measures of accuracy are computed for each target attribute.</span></span> <span data-ttu-id="14d0d-108">属性ごとに対象の値を指定または省略できます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-108">For each attribute you can specify or omit a target value.</span></span> <span data-ttu-id="14d0d-109">データ セット内のケースに対象の属性の値が含まれない場合、そのケースは、" *不足値*" と呼ばれる特殊な値が含まれるものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-109">If a case in the data set does not have any value for the target attribute, the case is treated as having a special value called the *missing value*.</span></span> <span data-ttu-id="14d0d-110">不足値のある行は、特定の対象の属性に対する精度のメジャーを計算するときにカウントされません。</span><span class="sxs-lookup"><span data-stu-id="14d0d-110">Rows that have missing values are not counted when computing the accuracy measure for a particular target attribute.</span></span> <span data-ttu-id="14d0d-111">スコアは属性ごとに個別に計算されるので、対象の属性に値があって他の属性に値がなくても、対象の属性のスコアには影響しません。</span><span class="sxs-lookup"><span data-stu-id="14d0d-111">Note that because the scores are computed for each attribute individually, if values are present for the target attribute but missing for other attributes, it does not affect the score for the target attribute.</span></span>  
  
|<span data-ttu-id="14d0d-112">Measure</span><span class="sxs-lookup"><span data-stu-id="14d0d-112">Measure</span></span>|<span data-ttu-id="14d0d-113">適用対象</span><span class="sxs-lookup"><span data-stu-id="14d0d-113">Applies To</span></span>|<span data-ttu-id="14d0d-114">実装</span><span class="sxs-lookup"><span data-stu-id="14d0d-114">Implementation</span></span>|  
|-------------|----------------|--------------------|  
|<span data-ttu-id="14d0d-115">**真陽性**</span><span class="sxs-lookup"><span data-stu-id="14d0d-115">**True positive**</span></span>|<span data-ttu-id="14d0d-116">不連続属性、値を指定</span><span class="sxs-lookup"><span data-stu-id="14d0d-116">Discrete attribute, value is specified</span></span>|<span data-ttu-id="14d0d-117">以下の条件を満たしているケースの数です。</span><span class="sxs-lookup"><span data-stu-id="14d0d-117">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="14d0d-118">対象の値がケースに含まれている。</span><span class="sxs-lookup"><span data-stu-id="14d0d-118">Case contains the target value.</span></span><br /><br /> <span data-ttu-id="14d0d-119">対象の値がケースに含まれていることがモデルで予測された。</span><span class="sxs-lookup"><span data-stu-id="14d0d-119">Model predicted that case contains the target value.</span></span>|  
|<span data-ttu-id="14d0d-120">**真陰性**</span><span class="sxs-lookup"><span data-stu-id="14d0d-120">**True Negative**</span></span>|<span data-ttu-id="14d0d-121">不連続属性、値を指定</span><span class="sxs-lookup"><span data-stu-id="14d0d-121">Discrete attribute, value is specified</span></span>|<span data-ttu-id="14d0d-122">以下の条件を満たしているケースの数です。</span><span class="sxs-lookup"><span data-stu-id="14d0d-122">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="14d0d-123">対象の値がケースに含まれていない。</span><span class="sxs-lookup"><span data-stu-id="14d0d-123">Case does not contain the target value.</span></span><br /><br /> <span data-ttu-id="14d0d-124">対象の値がケースに含まれていないことがモデルで予測された。</span><span class="sxs-lookup"><span data-stu-id="14d0d-124">Model predicted that case does not contain the target value.</span></span>|  
|<span data-ttu-id="14d0d-125">**偽陽性**</span><span class="sxs-lookup"><span data-stu-id="14d0d-125">**False positive**</span></span>|<span data-ttu-id="14d0d-126">不連続属性、値を指定</span><span class="sxs-lookup"><span data-stu-id="14d0d-126">Discrete attribute, value is specified</span></span>|<span data-ttu-id="14d0d-127">以下の条件を満たしているケースの数です。</span><span class="sxs-lookup"><span data-stu-id="14d0d-127">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="14d0d-128">実際の値が対象の値と等しい。</span><span class="sxs-lookup"><span data-stu-id="14d0d-128">Actual value is equal to target value.</span></span><br /><br /> <span data-ttu-id="14d0d-129">対象の値がケースに含まれていることがモデルで予測された。</span><span class="sxs-lookup"><span data-stu-id="14d0d-129">Model predicted that case contains the target value.</span></span>|  
|<span data-ttu-id="14d0d-130">**偽陰性**</span><span class="sxs-lookup"><span data-stu-id="14d0d-130">**False Negative**</span></span>|<span data-ttu-id="14d0d-131">不連続属性、値を指定</span><span class="sxs-lookup"><span data-stu-id="14d0d-131">Discrete attribute, value is specified</span></span>|<span data-ttu-id="14d0d-132">以下の条件を満たしているケースの数です。</span><span class="sxs-lookup"><span data-stu-id="14d0d-132">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="14d0d-133">実際の値が対象の値と等しくない。</span><span class="sxs-lookup"><span data-stu-id="14d0d-133">Actual value not equal to target value.</span></span><br /><br /> <span data-ttu-id="14d0d-134">対象の値がケースに含まれていないことがモデルで予測された。</span><span class="sxs-lookup"><span data-stu-id="14d0d-134">Model predicted that case does not contain the target value.</span></span>|  
|<span data-ttu-id="14d0d-135">**成功/失敗**</span><span class="sxs-lookup"><span data-stu-id="14d0d-135">**Pass/fail**</span></span>|<span data-ttu-id="14d0d-136">不連続属性、対象の指定なし</span><span class="sxs-lookup"><span data-stu-id="14d0d-136">Discrete attribute, no specified target</span></span>|<span data-ttu-id="14d0d-137">以下の条件を満たしているケースの数です。</span><span class="sxs-lookup"><span data-stu-id="14d0d-137">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="14d0d-138">最も高い確率を持つ予測された状態が入力状態と同じであり、確率が **[状態のしきい値]** の値を超える場合は合格。</span><span class="sxs-lookup"><span data-stu-id="14d0d-138">Pass if the predicted state with the highest probability is the same as the input state and probability is greater than the value of **State Threshold**.</span></span><br /><br /> <span data-ttu-id="14d0d-139">それ以外の場合は不合格。</span><span class="sxs-lookup"><span data-stu-id="14d0d-139">Otherwise, fail.</span></span>|  
|<span data-ttu-id="14d0d-140">**生み**</span><span class="sxs-lookup"><span data-stu-id="14d0d-140">**Lift**</span></span>|<span data-ttu-id="14d0d-141">不連続属性。</span><span class="sxs-lookup"><span data-stu-id="14d0d-141">Discrete attribute.</span></span> <span data-ttu-id="14d0d-142">対象の値を指定できますが、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="14d0d-142">Target value can be specified but is not required.</span></span>|<span data-ttu-id="14d0d-143">対象の属性の値が含まれるすべての行の平均対数確率値。ここで、各ケースの対数確率値は Log(ActualProbability/MarginalProbability) として計算されます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-143">The mean log likelihood for all rows with values for the target attribute, where log likelihood for each case is calculated as Log(ActualProbability/MarginalProbability).</span></span> <span data-ttu-id="14d0d-144">平均を計算するため、対数尤度の合計が入力データセットの行数で割られます。対象の属性の不足値がある行は除外されます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-144">To compute the mean, the sum of the log likelihood values is divided by the number of rows in the input dataset, excluding rows with missing values for the target attribute.</span></span><br /><br /> <span data-ttu-id="14d0d-145">Lift には正または負の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-145">Lift can be either a negative or positive value.</span></span> <span data-ttu-id="14d0d-146">正の値は、ランダムな推測を上回る効果的なモデルであることを示します。</span><span class="sxs-lookup"><span data-stu-id="14d0d-146">A positive value means an effective model that outperforms the random guess.</span></span>|  
|<span data-ttu-id="14d0d-147">**ログスコア**</span><span class="sxs-lookup"><span data-stu-id="14d0d-147">**Log score**</span></span>|<span data-ttu-id="14d0d-148">不連続属性。</span><span class="sxs-lookup"><span data-stu-id="14d0d-148">Discrete attribute.</span></span> <span data-ttu-id="14d0d-149">対象の値を指定できますが、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="14d0d-149">Target value can be specified but is not required.</span></span>|<span data-ttu-id="14d0d-150">合計後に入力データセットの行数で割った、各ケースの実際の確率の対数。対象の属性の不足値がある行は除外されます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-150">Log of the actual probability for each case, summed, and then divided by the number of rows in the input dataset, excluding rows with missing values for the target attribute.</span></span><br /><br /> <span data-ttu-id="14d0d-151">確率は小数で表されるので、ログ スコアは常に負の数値になります。</span><span class="sxs-lookup"><span data-stu-id="14d0d-151">Because probability is represented as a decimal fraction, log scores are always negative numbers.</span></span> <span data-ttu-id="14d0d-152">0 に近いほど、良いスコアになります。</span><span class="sxs-lookup"><span data-stu-id="14d0d-152">A score that is closer to 0 is a better score.</span></span>|  
|<span data-ttu-id="14d0d-153">**ケースの確率**</span><span class="sxs-lookup"><span data-stu-id="14d0d-153">**Case likelihood**</span></span>|<span data-ttu-id="14d0d-154">クラスター</span><span class="sxs-lookup"><span data-stu-id="14d0d-154">Cluster</span></span>|<span data-ttu-id="14d0d-155">パーティション内のケースの数で割った、すべてのケースのクラスター可能性スコアの合計。対象の属性の不足値がある行は除外されます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-155">Sum of the cluster likelihood scores for all cases, divided by the number of cases in the partition, excluding rows with missing values for the target attribute.</span></span>|  
|<span data-ttu-id="14d0d-156">**平均絶対誤差**</span><span class="sxs-lookup"><span data-stu-id="14d0d-156">**Mean absolute error**</span></span>|<span data-ttu-id="14d0d-157">連続属性</span><span class="sxs-lookup"><span data-stu-id="14d0d-157">Continuous attribute</span></span>|<span data-ttu-id="14d0d-158">パーティション内のケースの数で割った、パーティションのすべてのケースの絶対誤差の合計。</span><span class="sxs-lookup"><span data-stu-id="14d0d-158">Sum of the absolute error for all cases in the partition, divided by the number of cases in the partition.</span></span>|  
|<span data-ttu-id="14d0d-159">**平方根平均二乗誤差**</span><span class="sxs-lookup"><span data-stu-id="14d0d-159">**Root mean square error**</span></span>|<span data-ttu-id="14d0d-160">連続属性</span><span class="sxs-lookup"><span data-stu-id="14d0d-160">Continuous attribute</span></span>|<span data-ttu-id="14d0d-161">パーティションの平均 2 乗誤差の平方根。</span><span class="sxs-lookup"><span data-stu-id="14d0d-161">Square root of the mean squared error for the partition.</span></span>|  
|<span data-ttu-id="14d0d-162">**二乗平均平方根誤差**</span><span class="sxs-lookup"><span data-stu-id="14d0d-162">**Root mean squared error**</span></span>|<span data-ttu-id="14d0d-163">不連続属性。</span><span class="sxs-lookup"><span data-stu-id="14d0d-163">Discrete attribute.</span></span> <span data-ttu-id="14d0d-164">対象の値を指定できますが、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="14d0d-164">Target value can be specified but is not required.</span></span>|<span data-ttu-id="14d0d-165">パーティション内のケースの数で割った、確率スコアの補数の 2 乗の平均の平方根。対象の属性の不足値がある行は除外されます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-165">Square root of the mean of the squares of complement of the probability score, divided by the number of cases in the partition, excluding rows with missing values for the target attribute.</span></span>|  
|<span data-ttu-id="14d0d-166">**二乗平均平方根誤差**</span><span class="sxs-lookup"><span data-stu-id="14d0d-166">**Root mean squared error**</span></span>|<span data-ttu-id="14d0d-167">不連続属性、対象の指定なし。</span><span class="sxs-lookup"><span data-stu-id="14d0d-167">Discrete attribute, no specified target.</span></span>|<span data-ttu-id="14d0d-168">パーティション内のケースの数で割った、確率スコアの補数の 2 乗の平均の平方根。対象の属性の不足値があるケースは除外されます。</span><span class="sxs-lookup"><span data-stu-id="14d0d-168">Square root of the mean of the squares of complement of the probability score, divided by the number of cases in the partition, excluding cases with missing values for the target attribute.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14d0d-169">参照</span><span class="sxs-lookup"><span data-stu-id="14d0d-169">See Also</span></span>  
 <span data-ttu-id="14d0d-170">[データマイニング&#41;のテストと検証 &#40;](testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="14d0d-170">[Testing and Validation &#40;Data Mining&#41;](testing-and-validation-data-mining.md) </span></span>  
 [<span data-ttu-id="14d0d-171">相互検証 &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="14d0d-171">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)  
  
  