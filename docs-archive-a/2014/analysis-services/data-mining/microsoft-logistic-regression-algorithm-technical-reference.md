---
title: Microsoft ロジスティック回帰アルゴリズムテクニカルリファレンス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- MAXIMUM_INPUT_ATTRIBUTES parameter
- HOLDOUT_PERCENTAGE parameter
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
- SAMPLE_SIZE parameter
- regression algorithms [Analysis Services]
- HOLDOUT_SEED parameter
ms.assetid: cf32f1f3-153e-476f-91a4-bb834ec7c88d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72597453c9a52b890c822dd7c46aff46bc3ba44e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645262"
---
# <a name="microsoft-logistic-regression-algorithm-technical-reference"></a><span data-ttu-id="4b887-102">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4b887-102">Microsoft Logistic Regression Algorithm Technical Reference</span></span>
  <span data-ttu-id="4b887-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ロジスティック回帰アルゴリズムは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムを変形したものです。このアルゴリズムでは、 *HIDDEN_NODE_RATIO* パラメーターは 0 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="4b887-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm is a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm, where the *HIDDEN_NODE_RATIO* parameter is set to 0.</span></span> <span data-ttu-id="4b887-104">この設定により、非表示の層を含んでいない、ロジスティック回帰に相当するニューラル ネットワーク モデルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-104">This setting will create a neural network model that does not contain a hidden layer, and that therefore is equivalent to logistic regression.</span></span>

## <a name="implementation-of-the-microsoft-logistic-regression-algorithm"></a><span data-ttu-id="4b887-105">Microsoft ロジスティック回帰アルゴリズムの実装</span><span class="sxs-lookup"><span data-stu-id="4b887-105">Implementation of the Microsoft Logistic Regression Algorithm</span></span>
 <span data-ttu-id="4b887-106">予測可能列に状態が 2 つしか含まれていない場合に、予測可能列に特定の状態が含められる確率と入力列を関連付けて、回帰分析を実行する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="4b887-106">Suppose the predictable column contains only two states, yet you still want to perform a regression analysis, relating input columns to the probability that the predictable column will contain a specific state.</span></span> <span data-ttu-id="4b887-107">次の図は、予測可能列の状態に 1 と 0 を割り当て、この列に特定の状態が含められる確率を計算し、入力変数に対する線形回帰を実行した場合に得られる結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="4b887-107">The following diagram illustrates the results you will obtain if you assign 1 and 0 to the states of the predictable column, calculate the probability that the column will contain a specific state, and perform a linear regression against an input variable.</span></span>

 <span data-ttu-id="4b887-108">![線形回帰を使用して不十分にモデル化されたデータ](../media/logistic-linear-regression.gif "線形回帰を使用して不十分にモデル化されたデータ")</span><span class="sxs-lookup"><span data-stu-id="4b887-108">![Poorly modeled data using linear regression](../media/logistic-linear-regression.gif "Poorly modeled data using linear regression")</span></span>

 <span data-ttu-id="4b887-109">x 軸には入力列の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-109">The x-axis contains values of an input column.</span></span> <span data-ttu-id="4b887-110">y 軸には、予測可能列が特定の状態またはもう一方の状態になる確率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-110">The y-axis contains the probabilities that the predictable column will be one state or the other.</span></span> <span data-ttu-id="4b887-111">この場合の問題は、列の最大値と最小値が 0 と 1 であっても、線形回帰によって列が 0 と 1 の間に制限されないことです。</span><span class="sxs-lookup"><span data-stu-id="4b887-111">The problem with this is that the linear regression does not constrain the column to be between 0 and 1, even though those are the maximum and minimum values of the column.</span></span> <span data-ttu-id="4b887-112">この問題を解決するには、ロジスティック回帰を実行します。</span><span class="sxs-lookup"><span data-stu-id="4b887-112">A way to solve this problem is to perform logistic regression.</span></span> <span data-ttu-id="4b887-113">ロジスティック回帰分析では、直線を作成するのではなく、制約の最大値と最小値を含んでいる "S" 字型曲線が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-113">Instead of creating a straight line, logistic regression analysis creates an "S" shaped curve that contains maximum and minimum constraints.</span></span> <span data-ttu-id="4b887-114">たとえば、次の図は、前の例で使用したのと同じデータに対してロジスティック回帰を実行した場合に得られる結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="4b887-114">For example, the following diagram illustrates the results you will achieve if you perform a logistic regression against the same data as used for the previous example.</span></span>

 <span data-ttu-id="4b887-115">![ロジスティック回帰を使用してモデル化されたデータ](../media/logistic-regression.gif "ロジスティック回帰を使用してモデル化されたデータ")</span><span class="sxs-lookup"><span data-stu-id="4b887-115">![Data modeled by using logistic regression](../media/logistic-regression.gif "Data modeled by using logistic regression")</span></span>

 <span data-ttu-id="4b887-116">曲線が 0 ～ 1 の範囲を超えていないことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="4b887-116">Notice how the curve never goes above 1 or below 0.</span></span> <span data-ttu-id="4b887-117">ロジスティック回帰を使用して、予測可能列の状態の決定に重要な役割を果たす入力列を特定できます。</span><span class="sxs-lookup"><span data-stu-id="4b887-117">You can use logistic regression to describe which input columns are important in determining the state of the predictable column.</span></span>

### <a name="feature-selection"></a><span data-ttu-id="4b887-118">特徴選択</span><span class="sxs-lookup"><span data-stu-id="4b887-118">Feature Selection</span></span>
 <span data-ttu-id="4b887-119">機能の選択は、分析の向上と処理負荷の削減のためにすべての Analysis Services データ マイニング アルゴリズムで自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-119">Feature selection is used automatically by all Analysis Services data mining algorithms to improve analysis and reduce processing load.</span></span> <span data-ttu-id="4b887-120">ロジスティック回帰モデルの機能の選択に使用される方法は、属性のデータ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="4b887-120">The method used for feature selection in a logistic regression model depends on the data type of the attribute.</span></span> <span data-ttu-id="4b887-121">ロジスティック回帰は、Microsoft ニューラル ネットワーク アルゴリズムに基づいているため、ニューラル ネットワークに適用される機能の選択方法のサブセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b887-121">Because logistic regression is based on the Microsoft Neural Network algorithm, it uses a subset of the feature selection methods that apply to neural networks.</span></span> <span data-ttu-id="4b887-122">詳細については、「[機能の選択 &#40;データ マイニング&#41;](feature-selection-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b887-122">For more information, see [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>

### <a name="scoring-inputs"></a><span data-ttu-id="4b887-123">入力のスコアリング</span><span class="sxs-lookup"><span data-stu-id="4b887-123">Scoring Inputs</span></span>
 <span data-ttu-id="4b887-124">ニューラル ネットワーク モデルまたはロジスティック回帰モデルのコンテキストにおける "*スコアリング* " とは、データに存在する値を同じ尺度を使用する値のセットに変換して相互に比較できるようにするプロセスを意味します。</span><span class="sxs-lookup"><span data-stu-id="4b887-124">*Scoring* in the context of a neural network model or logistic regression model means the process of converting the values that are present in the data into a set of values that use the same scale and therefore can be compared to each other.</span></span> <span data-ttu-id="4b887-125">たとえば、Income に対する入力の範囲が 0 ～ 100,000 であるのに対し、[Number of Children] に対する入力の範囲は 0 ～ 5 であるとします。</span><span class="sxs-lookup"><span data-stu-id="4b887-125">For example, suppose the inputs for Income range from 0 to 100,000 whereas the inputs for [Number of Children] range from 0 to 5.</span></span> <span data-ttu-id="4b887-126">この変換プロセスでは、値の違いに関係なく、各入力の重要度を*スコア*付けしたり、比較したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="4b887-126">This conversion process allows you to *score*, or compare, the importance of each input regardless of the difference in values.</span></span>

 <span data-ttu-id="4b887-127">トレーニング セットに表示されている状態ごとに、モデルは 1 つの入力を生成します。</span><span class="sxs-lookup"><span data-stu-id="4b887-127">For each state that appears in the training set, the model generates an input.</span></span> <span data-ttu-id="4b887-128">不連続な入力または分離された入力の場合、Missing 状態がトレーニング セットに 1 回以上表示されると、Missing 状態を表す追加の入力が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-128">For discrete or discretized inputs, an additional input is created to represent the Missing state, if the missing state appears at least once in the training set.</span></span> <span data-ttu-id="4b887-129">連続する入力では、最大 2 つの入力ノードが作成されます。1 つはトレーニング データに存在する場合の Missing 値用の入力ノードで、もう 1 つはすべての既存の値 (Null 以外の値) 用の入力ノードです。</span><span class="sxs-lookup"><span data-stu-id="4b887-129">For continuous inputs, at most two input nodes are created: one for Missing values, if present in the training data, and one input for all existing, or non-null, values.</span></span> <span data-ttu-id="4b887-130">各入力は、z スコア正規化方式 (x μ)/StdDev. を使用して数値形式にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="4b887-130">Each input is scaled to a numeric format using the z-score normalization method, (x - μ)/StdDev.</span></span>

 <span data-ttu-id="4b887-131">z スコア正規化中に、トレーニング セット全体の平均 (μ) と標準偏差が取得されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-131">During z-score normalization, the mean (μ) and standard deviation are obtained over the complete training set.</span></span>

 <span data-ttu-id="4b887-132">**連続値**</span><span class="sxs-lookup"><span data-stu-id="4b887-132">**Continuous values**</span></span>

 <span data-ttu-id="4b887-133">値が存在します: (X μ)/σ//X は、エンコードされている実際の値です。</span><span class="sxs-lookup"><span data-stu-id="4b887-133">Value is present:   (X - μ)/σ // X is the actual value being encoded)</span></span>

 <span data-ttu-id="4b887-134">値が存在しません:-μ/σ//負の mu をシグマで除算してください)</span><span class="sxs-lookup"><span data-stu-id="4b887-134">Value is absent:    -   μ/σ  // negative mu divided by sigma)</span></span>

 <span data-ttu-id="4b887-135">**不連続値**</span><span class="sxs-lookup"><span data-stu-id="4b887-135">**Discrete values**</span></span>

 <span data-ttu-id="4b887-136">μ = p-(状態の前の確率)</span><span class="sxs-lookup"><span data-stu-id="4b887-136">μ = p - (the prior probability of a state)</span></span>

 <span data-ttu-id="4b887-137">StdDev  = sqrt(p(1-p))</span><span class="sxs-lookup"><span data-stu-id="4b887-137">StdDev  = sqrt(p(1-p))</span></span>

 <span data-ttu-id="4b887-138">値が存在します: (1 μ)/σ//(1 ~ mu) をシグマで除算)</span><span class="sxs-lookup"><span data-stu-id="4b887-138">Value is present:     (1 - μ)/σ// (One minus mu) divided by sigma)</span></span>

 <span data-ttu-id="4b887-139">値が存在しません: (-μ)/σ//負の mu をシグマで割った値</span><span class="sxs-lookup"><span data-stu-id="4b887-139">Value is absent:     (- μ)/σ// negative mu divided by sigma)</span></span>

### <a name="understanding-logistic-regression-coefficients"></a><span data-ttu-id="4b887-140">ロジスティック回帰係数について</span><span class="sxs-lookup"><span data-stu-id="4b887-140">Understanding Logistic Regression Coefficients</span></span>
 <span data-ttu-id="4b887-141">統計学の文献にはロジスティック回帰を実行するためのさまざまな方法が記されていますが、どの方法でも重要なのはモデルの適合性を評価する部分です。</span><span class="sxs-lookup"><span data-stu-id="4b887-141">There are various methods in the statistical literature for performing logistic regression, but an important part of all methods is assessing the fit of the model.</span></span> <span data-ttu-id="4b887-142">適合度統計の中でも、オッズ比と共変量パターンを扱うものについて、さまざまな提案がなされています。</span><span class="sxs-lookup"><span data-stu-id="4b887-142">A variety of goodness-to-fit statistics have been proposed, among them odds ratios and covariate patterns.</span></span> <span data-ttu-id="4b887-143">モデルの適合性を測定する方法についてはこのトピックでは扱いませんが、モデルの係数の値を取得し、それらの係数を使用して独自に適合性の測定方法を設計できます。</span><span class="sxs-lookup"><span data-stu-id="4b887-143">A discussion of how to measure the fit of a model is beyond the scope of this topic; however, you can retrieve the value of the coefficients in the model and use them to design your own measures of fit.</span></span>

> [!NOTE]
>  <span data-ttu-id="4b887-144">ロジスティック回帰モデルの一部として作成される係数はオッズ比を表しているわけではなく、またそのように解釈すべきではありません。</span><span class="sxs-lookup"><span data-stu-id="4b887-144">The coefficients that are created as part of a logistic regression model do not represent odds ratios and should not be interpreted as such.</span></span>

 <span data-ttu-id="4b887-145">モデル グラフ内の各ノードの係数は、そのノードへの入力の加重和を表します。</span><span class="sxs-lookup"><span data-stu-id="4b887-145">The coefficients for each node in the model graph represent a weighted sum of the inputs to that node.</span></span> <span data-ttu-id="4b887-146">ロジスティック回帰モデルでは、非表示層が空であるため、出力ノードに 1 セットの係数だけが格納されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-146">In a logistic regression model, the hidden layer is empty; therefore, there is only one set of coefficients, which is stored in the output nodes.</span></span> <span data-ttu-id="4b887-147">次のクエリを使用すると、係数の値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="4b887-147">You can retrieve the values of the coefficients by using the following query:</span></span>

```
SELECT FLATTENED [NODE_UNIQUE NAME],
(SELECT ATTRIBUTE_NAME< ATTRIBUTE_VALUE
FROM NODE_DISTRIBUTION) AS t
FROM <model name>.CONTENT
WHERE NODE_TYPE = 23
```

 <span data-ttu-id="4b887-148">このクエリは、出力値ごとに、係数と、関連の入力ノードを指す ID を返します。</span><span class="sxs-lookup"><span data-stu-id="4b887-148">For each output value, this query returns the coefficients and an ID that points back to the related input node.</span></span> <span data-ttu-id="4b887-149">また、出力と切片の値を含む行も返します。</span><span class="sxs-lookup"><span data-stu-id="4b887-149">It also returns a row that contains the value of the output and the intercept.</span></span> <span data-ttu-id="4b887-150">各入力 X には独自の係数 (Ci) がありますが、入れ子になったテーブルには、次の式に従って計算される "free" 係数 (Co) も含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b887-150">Each input X has its own coefficient (Ci), but the nested table also contains a "free" coefficient (Co), calculated according to the following formula:</span></span>

 <span data-ttu-id="4b887-151">F (X) = X1 \* C1 + X2 \* C2 +... + Xn \* Cn + X0</span><span class="sxs-lookup"><span data-stu-id="4b887-151">F(X) = X1\*C1 + X2\*C2 + ... +Xn\*Cn + X0</span></span>

 <span data-ttu-id="4b887-152">アクティブ化: exp(F(X)) / (1 + exp(F(X)) )</span><span class="sxs-lookup"><span data-stu-id="4b887-152">Activation: exp(F(X)) / (1 + exp(F(X)) )</span></span>

 <span data-ttu-id="4b887-153">詳細については、「 [ロジスティック回帰モデルのクエリ例](logistic-regression-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b887-153">For more information, see [Logistic Regression Model Query Examples](logistic-regression-model-query-examples.md).</span></span>

## <a name="customizing-the-logistic-regression-algorithm"></a><span data-ttu-id="4b887-154">ロジスティック回帰アルゴリズムのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="4b887-154">Customizing the Logistic Regression Algorithm</span></span>
 <span data-ttu-id="4b887-155">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ロジスティック回帰アルゴリズムでは、結果として得られるマイニング モデルの動作、パフォーマンス、および精度に影響を与えるいくつかのパラメーターがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4b887-155">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] logistic regression algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="4b887-156">また、入力として使用する列にモデリング フラグを設定して、モデルの動作を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b887-156">You can also modify the behavior of the model by setting modeling flags on the columns used as input.</span></span>

### <a name="setting-algorithm-parameters"></a><span data-ttu-id="4b887-157">アルゴリズム パラメーターの設定</span><span class="sxs-lookup"><span data-stu-id="4b887-157">Setting Algorithm Parameters</span></span>
 <span data-ttu-id="4b887-158">次の表は、Microsoft ロジスティック回帰アルゴリズムで使用できるパラメーターを示しています。</span><span class="sxs-lookup"><span data-stu-id="4b887-158">The following table describes the parameters that can be used with the Microsoft Logistic Regression algorithm.</span></span>

 <span data-ttu-id="4b887-159">提示されたエラーの計算に使用するトレーニングデータ内のケースの割合を HOLDOUT_PERCENTAGE 指定します。</span><span class="sxs-lookup"><span data-stu-id="4b887-159">HOLDOUT_PERCENTAGE Specifies the percentage of cases within the training data used to calculate the holdout error.</span></span> <span data-ttu-id="4b887-160">HOLDOUT_PERCENTAGE は、マイニング モデルのトレーニング中に停止条件の一部として使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-160">HOLDOUT_PERCENTAGE is used as part of the stopping criteria while training the mining model.</span></span>

 <span data-ttu-id="4b887-161">既定値は 30 です。</span><span class="sxs-lookup"><span data-stu-id="4b887-161">The default is 30.</span></span>

 <span data-ttu-id="4b887-162">予約データをランダムに決定するときに擬似乱数ジェネレーターをシード処理するために使用する数値を指定 HOLDOUT_SEED します。</span><span class="sxs-lookup"><span data-stu-id="4b887-162">HOLDOUT_SEED Specifies a number to use to seed the pseudo-random generator when randomly determining the holdout data.</span></span> <span data-ttu-id="4b887-163">HOLDOUT_SEED を 0 に設定すると、アルゴリズムによってマイニング モデルの名前に基づいたシードが生成され、再処理中にモデルのコンテンツが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="4b887-163">If HOLDOUT_SEED is set to 0, the algorithm generates the seed based on the name of the mining model, to guarantee that the model content remains the same during reprocessing.</span></span>

 <span data-ttu-id="4b887-164">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="4b887-164">The default is 0.</span></span>

 <span data-ttu-id="4b887-165">MAXIMUM_INPUT_ATTRIBUTES は、機能の選択を呼び出す前にアルゴリズムが処理できる入力属性の数を定義します。</span><span class="sxs-lookup"><span data-stu-id="4b887-165">MAXIMUM_INPUT_ATTRIBUTES Defines the number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="4b887-166">この値を 0 に設定すると、機能の選択がオフになります。</span><span class="sxs-lookup"><span data-stu-id="4b887-166">Set this value to 0 to turn off feature selection.</span></span>

 <span data-ttu-id="4b887-167">既定値は 255 です。</span><span class="sxs-lookup"><span data-stu-id="4b887-167">The default is 255.</span></span>

 <span data-ttu-id="4b887-168">MAXIMUM_OUTPUT_ATTRIBUTES は、機能の選択を呼び出す前にアルゴリズムが処理できる出力属性の数を定義します。</span><span class="sxs-lookup"><span data-stu-id="4b887-168">MAXIMUM_OUTPUT_ATTRIBUTES Defines the number of output attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="4b887-169">この値を 0 に設定すると、機能の選択がオフになります。</span><span class="sxs-lookup"><span data-stu-id="4b887-169">Set this value to 0 to turn off feature selection.</span></span>

 <span data-ttu-id="4b887-170">既定値は 255 です。</span><span class="sxs-lookup"><span data-stu-id="4b887-170">The default is 255.</span></span>

 <span data-ttu-id="4b887-171">MAXIMUM_STATES アルゴリズムがサポートする属性の状態の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b887-171">MAXIMUM_STATES Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="4b887-172">属性の状態の数が状態の最大数よりも大きい場合、アルゴリズムでは属性の最も一般的な状態が使用され、残りの状態は無視されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-172">If the number of states that an attribute has is larger than the maximum number of states, the algorithm uses the most popular states of the attribute and ignores the remaining states.</span></span>

 <span data-ttu-id="4b887-173">既定値は、100 です。</span><span class="sxs-lookup"><span data-stu-id="4b887-173">The default is 100.</span></span>

 <span data-ttu-id="4b887-174">SAMPLE_SIZE は、モデルのトレーニングに使用するケースの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b887-174">SAMPLE_SIZE Specifies the number of cases to be used to train the model.</span></span> <span data-ttu-id="4b887-175">アルゴリズム プロバイダーでは、この数と、HOLDOUT_PERCENTAGE パラメーターで指定された割合に含まれないケースの総数の割合のうち、いずれか小さい方が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-175">The algorithm provider uses either this number or the percentage of total of cases that are not included in the holdout percentage as specified by the HOLDOUT_PERCENTAGE parameter, whichever value is smaller.</span></span>

 <span data-ttu-id="4b887-176">たとえば、HOLDOUT_PERCENTAGE が 30 に設定されている場合、アルゴリズムでは、このパラメーターの値と、ケースの総数の 70% に相当する値のうち、いずれか小さい方が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-176">In other words, if HOLDOUT_PERCENTAGE is set to 30, the algorithm will use either the value of this parameter, or a value that is equal to 70 percent of the total number of cases, whichever is smaller.</span></span>

 <span data-ttu-id="4b887-177">既定値は 10000 です。</span><span class="sxs-lookup"><span data-stu-id="4b887-177">The default is 10000.</span></span>

### <a name="modeling-flags"></a><span data-ttu-id="4b887-178">ModelingFlags</span><span class="sxs-lookup"><span data-stu-id="4b887-178">Modeling Flags</span></span>
 <span data-ttu-id="4b887-179">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ロジスティック回帰アルゴリズムでは、次のモデリング フラグを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4b887-179">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>

 <span data-ttu-id="4b887-180">NOT NULL は、列に null を含めることができないことを示します。</span><span class="sxs-lookup"><span data-stu-id="4b887-180">NOT NULL Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="4b887-181">モデルのトレーニング中に NULL が検出された場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4b887-181">An error will result if Analysis Services encounters a null during model training.</span></span>

 <span data-ttu-id="4b887-182">マイニング構造列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-182">Applies to mining structure columns.</span></span>

 <span data-ttu-id="4b887-183">MODEL_EXISTENCE_ONLY は、列が、およびの2つの可能な状態を持つ列として扱われることを意味し `Missing` `Existing` ます。</span><span class="sxs-lookup"><span data-stu-id="4b887-183">MODEL_EXISTENCE_ONLY Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="4b887-184">NULL は Missing 値になります。</span><span class="sxs-lookup"><span data-stu-id="4b887-184">A null is a missing value.</span></span>

 <span data-ttu-id="4b887-185">マイニング モデル列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4b887-185">Applies to mining model column.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b887-186">必要条件</span><span class="sxs-lookup"><span data-stu-id="4b887-186">Requirements</span></span>
 <span data-ttu-id="4b887-187">ロジスティック回帰モデルには、キー列、入力列、および少なくとも 1 つの予測可能列が必要です。</span><span class="sxs-lookup"><span data-stu-id="4b887-187">A logistic regression model must contain a key column, input columns, and at least one predictable column.</span></span>

### <a name="input-and-predictable-columns"></a><span data-ttu-id="4b887-188">入力列と予測可能列</span><span class="sxs-lookup"><span data-stu-id="4b887-188">Input and Predictable Columns</span></span>
 <span data-ttu-id="4b887-189">次の表のように、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ロジスティック回帰アルゴリズムでは、特定の入力列のコンテンツの種類、予測可能列のコンテンツの種類、およびモデリング フラグがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4b887-189">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm supports the specific input column content types, predictable column content types, and modeling flags that are listed in the following table.</span></span> <span data-ttu-id="4b887-190">マイニング モデルにおけるコンテンツの種類の意味については、「[コンテンツの種類 &#40;データ マイニング&#41;](content-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b887-190">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>

|<span data-ttu-id="4b887-191">列</span><span class="sxs-lookup"><span data-stu-id="4b887-191">Column</span></span>|<span data-ttu-id="4b887-192">コンテンツの種類</span><span class="sxs-lookup"><span data-stu-id="4b887-192">Content types</span></span>|
|------------|-------------------|
|<span data-ttu-id="4b887-193">入力属性</span><span class="sxs-lookup"><span data-stu-id="4b887-193">Input attribute</span></span>|<span data-ttu-id="4b887-194">Continuous、Discrete、Discretized、Key、Table</span><span class="sxs-lookup"><span data-stu-id="4b887-194">Continuous, Discrete, Discretized, Key, Table</span></span>|
|<span data-ttu-id="4b887-195">予測可能な属性</span><span class="sxs-lookup"><span data-stu-id="4b887-195">Predictable attribute</span></span>|<span data-ttu-id="4b887-196">Continuous、Discrete、Discretized</span><span class="sxs-lookup"><span data-stu-id="4b887-196">Continuous, Discrete, Discretized</span></span>|

## <a name="see-also"></a><span data-ttu-id="4b887-197">参照</span><span class="sxs-lookup"><span data-stu-id="4b887-197">See Also</span></span>
 <span data-ttu-id="4b887-198">[Microsoft ロジスティック回帰アルゴリズム](microsoft-logistic-regression-algorithm.md)[線形回帰モデルのクエリ例](linear-regression-model-query-examples.md)[ロジスティック回帰モデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](mining-model-content-for-logistic-regression-models.md) [Microsoft ニューラルネットワークアルゴリズム](microsoft-neural-network-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="4b887-198">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) [Linear Regression Model Query Examples](linear-regression-model-query-examples.md) [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)</span></span>


