---
title: Microsoft アソシエーションアルゴリズムテクニカルリファレンス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_ITEMSET_SIZE parameter
- MAXIMUM_SUPPORT parameter
- association algorithms [Analysis Services]
- MINIMUM_SUPPORT parameter
- OPTIMIZED_PREDICTION_COUNT parameter
- associations [Analysis Services]
- MAXIMUM_ITEMSET_COUNT parameter
- MAXIMUM_ITEMSET_SIZE parameter
- MINIMUM_PROBABILITY parameter
ms.assetid: 50a22202-e936-4995-ae1d-4ff974002e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: eac813711aafc714edef6acc98cda612dd879549
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634124"
---
# <a name="microsoft-association-algorithm-technical-reference"></a><span data-ttu-id="a7413-102">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="a7413-102">Microsoft Association Algorithm Technical Reference</span></span>
  <span data-ttu-id="a7413-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムは、よく知られている Apriori アルゴリズムの直接的な実装です。</span><span class="sxs-lookup"><span data-stu-id="a7413-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm is a straightforward implementation of the well-known Apriori algorithm.</span></span>  
  
 <span data-ttu-id="a7413-104">アソシエーションの分析には、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムと [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムの両方を使用できますが、それぞれのアルゴリズムで異なるルールが検出される場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7413-104">Both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm can be used to analyze associations, but the rules that are found by each algorithm can differ.</span></span> <span data-ttu-id="a7413-105">デシジョン ツリー モデルでは、情報利得に基づく分割によってルールが導き出されるのに対し、アソシエーション モデルでは、ルールは完全に信頼度に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a7413-105">In a decision trees model, the splits that lead to specific rules are based on information gain, whereas in an association model, rules are based completely on confidence.</span></span> <span data-ttu-id="a7413-106">したがって、アソシエーション モデルの場合、強力なルール (信頼度が高いルール) は新しい情報を提供するわけではないため、興味深いものになるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="a7413-106">Therefore, in an association model, a strong rule, or one that has high confidence, might not necessarily be interesting because it does not provide new information.</span></span>  
  
## <a name="implementation-of-the-microsoft-association-algorithm"></a><span data-ttu-id="a7413-107">Microsoft アソシエーション アルゴリズムの実装</span><span class="sxs-lookup"><span data-stu-id="a7413-107">Implementation of the Microsoft Association Algorithm</span></span>  
 <span data-ttu-id="a7413-108">Apriori アルゴリズムは、パターンを分析するのではなく、 *候補アイテムセット*を生成およびカウントします。</span><span class="sxs-lookup"><span data-stu-id="a7413-108">The Apriori algorithm does not analyze patterns, but rather generates and then counts *candidate itemsets*.</span></span> <span data-ttu-id="a7413-109">アイテムは、分析するデータの種類に応じて、イベント、製品、または属性の値を表します。</span><span class="sxs-lookup"><span data-stu-id="a7413-109">An item can represent an event, a product, or the value of an attribute, depending on the type of data that is being analyzed.</span></span>  
  
 <span data-ttu-id="a7413-110">アソシエーション モデルの最も一般的な種類のうち、Yes/No または Missing/Existing の値を表すブール変数は、製品名やイベント名のようなそれぞれの属性に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a7413-110">In the most common type of association model Boolean variables, representing a Yes/No or Missing/Existing value, are assigned to each attribute, such as a product or event name.</span></span> <span data-ttu-id="a7413-111">マーケット バスケット分析は、ブール変数を使用して顧客の買い物かごに特定の製品が入っているかどうかを表すアソシエーション ルール モデルの 1 つの例です。</span><span class="sxs-lookup"><span data-stu-id="a7413-111">A market basket analysis is an example of an association rules model that uses Boolean variables to represent the presence or absence of particular products in a customer's shopping basket.</span></span>  
  
 <span data-ttu-id="a7413-112">このアルゴリズムでは、各アイテムセットに対して、サポートと信頼度を表すスコアが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-112">For each itemset, the algorithm then creates scores that represent support and confidence.</span></span> <span data-ttu-id="a7413-113">これらのスコアを使用して、アイテムセットに順位を付けたり、アイテムセットから興味深いルールを引き出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a7413-113">These scores can be used to rank and derive interesting rules from the itemsets.</span></span>  
  
 <span data-ttu-id="a7413-114">アソシエーション モデルは、数値属性に対しても作成できます。</span><span class="sxs-lookup"><span data-stu-id="a7413-114">Association models can also be created for numerical attributes.</span></span> <span data-ttu-id="a7413-115">属性が連続的である場合は、数値をバケットに *分離* またはグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="a7413-115">If the attributes are continuous, the numbers can be *discretized, or* grouped in buckets.</span></span> <span data-ttu-id="a7413-116">その分離された値がブール値または属性と値のペアとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-116">The discretized values can then be handled either as Booleans or as attribute-value pairs.</span></span>  
  
### <a name="support-probability-and-importance"></a><span data-ttu-id="a7413-117">サポート、確率、および重要度</span><span class="sxs-lookup"><span data-stu-id="a7413-117">Support, Probability, and Importance</span></span>  
 <span data-ttu-id="a7413-118">*サポート*( *頻度*とも呼ばれます) は、対象となるアイテムまたはアイテムの組み合わせを含むケースの数を表します。</span><span class="sxs-lookup"><span data-stu-id="a7413-118">*Support*, which issometimes referred to as *frequency*, means the number of cases that contain the targeted item or combination of items.</span></span> <span data-ttu-id="a7413-119">指定した以上のサポートを持つアイテムのみがモデルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="a7413-119">Only items that have at least the specified amount of support can be included in the model.</span></span>  
  
 <span data-ttu-id="a7413-120">アイテムの組み合わせのサポートも、MINIMUM_SUPPORT パラメーターで定義されているしきい値を超えている場合、そのアイテムの集合を、 *よく使用されるアイテムセット* と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a7413-120">A *frequent itemset* refers to a collection of items where the combination of items also has support above the threshold defined by the MINIMUM_SUPPORT parameter.</span></span> <span data-ttu-id="a7413-121">たとえば、アイテムセットが {A,B,C} で MINIMUM_SUPPORT の値が 10 の場合、A、B、および C の各アイテムがそれぞれ 10 個以上のケースで検出されないとそれらのアイテムはモデルに含まれませんが、さらにそのアイテムの組み合わせ {A,B,C} も 10 個以上のケースで検出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7413-121">For example, if the itemset is {A,B,C} and the MINIMUM_SUPPORT value is 10, each individual item A, B, and C must be found in at least 10 cases to be included in the model, and the combination of items {A,B,C} must also be found in at least 10 cases.</span></span>  
  
 <span data-ttu-id="a7413-122">**注** アイテムセットの最大長 (長さはアイテムの数を表します) を指定することによってマイニング モデルのアイテムセットの数を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7413-122">**Note** You can also control the number of itemsets in a mining model by specifying the maximum length of an itemset, where length means the number of items.</span></span>  
  
 <span data-ttu-id="a7413-123">特定のアイテムまたはアイテムセットのサポートは、既定ではそのアイテムまたはアイテムセットを含むケースの数を表しますが、</span><span class="sxs-lookup"><span data-stu-id="a7413-123">By default, the support for any particular item or itemset represents a count of the cases that contain that item or items.</span></span> <span data-ttu-id="a7413-124">データセット内の全ケースの割合として MINIMUM_SUPPORT を表現することもできます。その場合は、数を 1 未満の 10 進値として入力します。</span><span class="sxs-lookup"><span data-stu-id="a7413-124">However, you can also express MINIMUM_SUPPORT as a percentage of the total cases in the data set, by typing the number as a decimal value less than 1.</span></span> <span data-ttu-id="a7413-125">たとえば 0.03 という MINIMUM_SUPPORT 値を指定した場合、そのアイテムまたはアイテムセットは、データセット内の全ケースの 3% 以上に含まれていないとモデルに含まれません。</span><span class="sxs-lookup"><span data-stu-id="a7413-125">For example, if you specify a MINIMUM_SUPPORT value of 0.03, it means that at least 3% of the total cases in the data set must contain this item or itemset for inclusion in the model.</span></span> <span data-ttu-id="a7413-126">数と割合のどちらを使用するのがよいかは、実際にモデルで試して判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7413-126">You should experiment with your model to determine whether using a count or percentage makes more sense.</span></span>  
  
 <span data-ttu-id="a7413-127">一方、ルールのしきい値は、数や割合としてではなく確率 ( *信頼度*とも呼ばれます) として表現されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-127">In contrast, the threshold for rules is expressed not as a count or percentage, but as a probability, sometimes referred to as *confidence*.</span></span> <span data-ttu-id="a7413-128">たとえば、アイテムセット {A,B,C} が 50 個のケースで発生し、アイテムセット {A,B,D} も 50 個のケースで、さらにアイテムセット {A,B} も別の 50 個のケースで発生する場合、{A,B} が {C} の強力な予測子にならないことは明らかです。</span><span class="sxs-lookup"><span data-stu-id="a7413-128">For example, if the itemset {A,B,C} occurs in 50 cases, but the itemset {A,B,D} also occurs in 50 cases, and the itemset {A,B} in another 50 cases, it is obvious that {A,B} is not a strong predictor of {C}.</span></span> <span data-ttu-id="a7413-129">このため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、すべての既知の結果に対して特定の結果に加重するために、アイテムセット {A,B,C} のサポートをすべての関連するアイテムセットのサポートで割って個々のルール (If {A,B} Then {C} など) の確率が計算されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-129">Therefore, to weight a particular outcomes against all known outcomes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calculates the probability of the individual rule (such as If {A,B} Then {C}) by dividing the support for the itemset {A,B,C} by the support for all related itemsets.</span></span>  
  
 <span data-ttu-id="a7413-130">MINIMUM_PROBABILITY の値を設定すると、モデルで生成されるルールの数を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="a7413-130">You can restrict the number of rules that a model produces by setting a value for MINIMUM_PROBABILITY.</span></span>  
  
 <span data-ttu-id="a7413-131">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、作成される各ルールについて、その *重要度*( *リフト*とも呼ばれます) を示すスコアが出力されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-131">For each rule that is created, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] outputs a score that indicates its *importance*, which is alsoreferred to as *lift*.</span></span> <span data-ttu-id="a7413-132">重要度 (リフト) の計算方法はアイテムセットとルールで異なります。</span><span class="sxs-lookup"><span data-stu-id="a7413-132">Lift Importance is calculated differently for itemsets and rules.</span></span>  
  
 <span data-ttu-id="a7413-133">アイテムセットの重要度は、アイテムセットの確率をアイテムセット内の個々のアイテムの合成確率で割って計算されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-133">The importance of an itemset is calculated as the probability of the itemset divided by the compound probability of the individual items in the itemset.</span></span> <span data-ttu-id="a7413-134">たとえばアイテムセットに {A,B} が含まれている場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、この A と B の組み合わせを含むすべてのケースをカウントし、それをケースの合計数で割って確率を計算した後、その確率を正規化します。</span><span class="sxs-lookup"><span data-stu-id="a7413-134">For example, if an itemset contains {A,B}, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] first counts all the cases that contain this combination A and B, and divides that by the total number of cases, and then normalizes the probability.</span></span>  
  
 <span data-ttu-id="a7413-135">ルールの重要度は、与えられたルールの左辺に対するルールの右辺の対数尤度で計算されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-135">The importance of a rule is calculated by the log likelihood of the right-hand side of the rule, given the left-hand side of the rule.</span></span> <span data-ttu-id="a7413-136">たとえばルール `If {A} Then {B}`の場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、A と B を含むケースを B を含み A を含まないケースで割って比率を計算し、その比率を対数スケールを使用して正規化します。</span><span class="sxs-lookup"><span data-stu-id="a7413-136">For example, in the rule `If {A} Then {B}`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calculates the ratio of cases with A and B over cases with B but without A, and then normalizes that ratio by using a logarithmic scale.</span></span>  
  
### <a name="feature-selection"></a><span data-ttu-id="a7413-137">特徴選択</span><span class="sxs-lookup"><span data-stu-id="a7413-137">Feature Selection</span></span>  
 <span data-ttu-id="a7413-138">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムでは、自動的な機能の選択は一切行われません。</span><span class="sxs-lookup"><span data-stu-id="a7413-138">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm does not perform any kind of automatic feature selection.</span></span> <span data-ttu-id="a7413-139">代わりに、アルゴリズムで使用されるデータを制御するパラメーターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a7413-139">Instead, the algorithm provides parameters that control the data that is used by the algorithm.</span></span> <span data-ttu-id="a7413-140">たとえば、各アイテムセットのサイズを制限することも、アイテムセットがモデルに追加されるために必要な最大サポートおよび最小サポートを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7413-140">This might include limits on the size of each itemset, or setting the maximum and minimum support required to add an itemset to the model.</span></span>  
  
-   <span data-ttu-id="a7413-141">一般的すぎて興味深いものではないアイテムやイベントを除外するには、MAXIMUM_SUPPORT の値を小さくして頻度の高いアイテムセットをモデルから削除します。</span><span class="sxs-lookup"><span data-stu-id="a7413-141">To filter out items and events that are too common and therefore uninteresting, decrease the value of MAXIMUM_SUPPORT to remove very frequent itemsets from the model.</span></span>  
  
-   <span data-ttu-id="a7413-142">頻度の低いアイテムやアイテムセットを除外するには、MINIMUM_SUPPORT の値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="a7413-142">To filter out items and itemsets that are rare, increase the value of MINIMUM_SUPPORT.</span></span>  
  
-   <span data-ttu-id="a7413-143">ルールを除外するには、MINIMUM_PROBABILITY の値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="a7413-143">To filter out rules, increase the value of MINIMUM_PROBABILITY.</span></span>  
  
## <a name="customizing-the-microsoft-association-rules-algorithm"></a><span data-ttu-id="a7413-144">Microsoft アソシエーション ルール アルゴリズムのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="a7413-144">Customizing the Microsoft Association Rules Algorithm</span></span>  
 <span data-ttu-id="a7413-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムでは、結果として得られるマイニング モデルの動作、パフォーマンス、および精度に影響を与えるいくつかのパラメーターがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a7413-145">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="a7413-146">アルゴリズム パラメーターの設定</span><span class="sxs-lookup"><span data-stu-id="a7413-146">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="a7413-147">マイニング モデルのパラメーターは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーを使用していつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="a7413-147">You can change the parameters for a mining model at any time by using the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a7413-148"><xref:Microsoft.AnalysisServices.MiningModel.AlgorithmParameters%2A>AMO のコレクションを使用するか、XMLA の[MiningModels 要素 &#40;assl&#41;](https://docs.microsoft.com/bi-reference/assl/collections/miningmodels-element-assl)を使用することによって、プログラムでパラメーターを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7413-148">You can also change parameters programmatically by using the <xref:Microsoft.AnalysisServices.MiningModel.AlgorithmParameters%2A> collection in AMO, or by using the [MiningModels Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/collections/miningmodels-element-assl) in XMLA.</span></span> <span data-ttu-id="a7413-149">次の表では、各パラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a7413-149">The following table describes each parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7413-150">DMX ステートメントを使用して、既存のモデルのパラメーターを変更することはできません。DMX CREATE MODEL または ALTER STRUCTURE でパラメーターを指定する必要があります...モデルを作成するときにモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="a7413-150">You cannot change the parameters in an existing model by using a DMX statement; you must specify the parameters in the DMX CREATE MODEL or ALTER STRUCTURE... ADD MODEL when you create the model.</span></span>  
  
 <span data-ttu-id="a7413-151">*MAXIMUM_ITEMSET_COUNT*</span><span class="sxs-lookup"><span data-stu-id="a7413-151">*MAXIMUM_ITEMSET_COUNT*</span></span>  
 <span data-ttu-id="a7413-152">生成されるアイテムセットの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7413-152">Specifies the maximum number of itemsets to produce.</span></span> <span data-ttu-id="a7413-153">数が指定されていない場合は、既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-153">If no number is specified, the default value is used.</span></span>  
  
 <span data-ttu-id="a7413-154">既定値は 200000 です。</span><span class="sxs-lookup"><span data-stu-id="a7413-154">The default is 200000.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7413-155">アイテムセットはサポートで順位付けされます。</span><span class="sxs-lookup"><span data-stu-id="a7413-155">Itemsets are ranked by support.</span></span> <span data-ttu-id="a7413-156">サポートの値が同じアイテムセット間の順序は任意です。</span><span class="sxs-lookup"><span data-stu-id="a7413-156">Among itemsets that have the same support, ordering is arbitrary.</span></span>  
  
 <span data-ttu-id="a7413-157">*MAXIMUM_ITEMSET_SIZE*</span><span class="sxs-lookup"><span data-stu-id="a7413-157">*MAXIMUM_ITEMSET_SIZE*</span></span>  
 <span data-ttu-id="a7413-158">アイテムセットで使用できるアイテムの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7413-158">Specifies the maximum number of items that are allowed in an itemset.</span></span> <span data-ttu-id="a7413-159">この値を 0 に設定すると、アイテムセットのサイズに制限がなくなります。</span><span class="sxs-lookup"><span data-stu-id="a7413-159">Setting this value to 0 specifies that there is no limit to the size of the itemset.</span></span>  
  
 <span data-ttu-id="a7413-160">既定値は 3 です。</span><span class="sxs-lookup"><span data-stu-id="a7413-160">The default is 3.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7413-161">この制限に達するとモデルの処理が中止されるため、この値を小さくすることによってモデルの作成に要する時間を短縮できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a7413-161">Decreasing this value can potentially reduce the time that is required for creating the model, because processing of the model stops when the limit is reached.</span></span>  
  
 <span data-ttu-id="a7413-162">*MAXIMUM_SUPPORT*</span><span class="sxs-lookup"><span data-stu-id="a7413-162">*MAXIMUM_SUPPORT*</span></span>  
 <span data-ttu-id="a7413-163">アイテムセットをサポートするケースの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7413-163">Specifies the maximum number of cases that an itemset has for support.</span></span> <span data-ttu-id="a7413-164">このパラメーターを使用すると、頻繁に出現するためにあまり意味がないと考えられるアイテムを除外できます。</span><span class="sxs-lookup"><span data-stu-id="a7413-164">This parameter can be used to eliminate items that appear frequently and therefore potentially have little meaning.</span></span>  
  
 <span data-ttu-id="a7413-165">この値が 1 より小さい場合、値はケースの総数の割合を表します。</span><span class="sxs-lookup"><span data-stu-id="a7413-165">If this value is less than 1, the value represents a percentage of the total cases.</span></span> <span data-ttu-id="a7413-166">1 より大きい値は、アイテムセットを含むことができるケースの絶対数を表します。</span><span class="sxs-lookup"><span data-stu-id="a7413-166">Values greater than 1 represent the absolute number of cases that can contain the itemset.</span></span>  
  
 <span data-ttu-id="a7413-167">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="a7413-167">The default is 1.</span></span>  
  
 <span data-ttu-id="a7413-168">*MINIMUM_ITEMSET_SIZE*</span><span class="sxs-lookup"><span data-stu-id="a7413-168">*MINIMUM_ITEMSET_SIZE*</span></span>  
 <span data-ttu-id="a7413-169">アイテムセットで使用できるアイテムの最小数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7413-169">Specifies the minimum number of items that are allowed in an itemset.</span></span> <span data-ttu-id="a7413-170">この数を大きくすると、モデルに含まれるアイテムセットが少なくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a7413-170">If you increase this number, the model might contain fewer itemsets.</span></span> <span data-ttu-id="a7413-171">たとえば、1 つのアイテムから成るアイテムセットを無視する場合などに便利です。</span><span class="sxs-lookup"><span data-stu-id="a7413-171">This can be useful if you want to ignore single-item itemsets, for example.</span></span>  
  
 <span data-ttu-id="a7413-172">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="a7413-172">The default is 1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7413-173">この最小値を大きくしても、モデルの処理時間を短縮することはできません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、いずれにしても単一のアイテムの確率を処理の一環として計算しなければならないからです。</span><span class="sxs-lookup"><span data-stu-id="a7413-173">You cannot reduce model processing time by increasing the minimum value, because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] must calculate probabilities for single items anyway as part of processing.</span></span> <span data-ttu-id="a7413-174">ただし、この値を大きく設定すると、小さいアイテムセットを除外できます。</span><span class="sxs-lookup"><span data-stu-id="a7413-174">However, by setting this value higher you can filter out smaller itemsets.</span></span>  
  
 <span data-ttu-id="a7413-175">*MINIMUM_PROBABILITY*</span><span class="sxs-lookup"><span data-stu-id="a7413-175">*MINIMUM_PROBABILITY*</span></span>  
 <span data-ttu-id="a7413-176">ルールが true である最小確率を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7413-176">Specifies the minimum probability that a rule is true.</span></span>  
  
 <span data-ttu-id="a7413-177">たとえば、この値を 0.5 に設定すると、確率が 50% より低いルールは生成されなくなります。</span><span class="sxs-lookup"><span data-stu-id="a7413-177">For example, if you set this value to 0.5, it means that no rule with less than fifty percent probability can be generated.</span></span>  
  
 <span data-ttu-id="a7413-178">既定値は 0.4 です。</span><span class="sxs-lookup"><span data-stu-id="a7413-178">The default is 0.4.</span></span>  
  
 <span data-ttu-id="a7413-179">*MINIMUM_SUPPORT*</span><span class="sxs-lookup"><span data-stu-id="a7413-179">*MINIMUM_SUPPORT*</span></span>  
 <span data-ttu-id="a7413-180">アルゴリズムによってルールが生成される前に、アイテムセットを含む必要があるケースの最小数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7413-180">Specifies the minimum number of cases that must contain the itemset before the algorithm generates a rule.</span></span>  
  
 <span data-ttu-id="a7413-181">この値を 1 より小さい値に設定すると、ケースの最小数がケースの総数の割合として計算されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-181">If you set this value to less than 1, the minimum number of cases is calculated as a percentage of the total cases.</span></span>  
  
 <span data-ttu-id="a7413-182">この値を 1 より大きい整数に設定すると、ケースの最小数が、アイテムセットを含む必要のあるケースの数として計算されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-182">If you set this value to a whole number greater than 1, specifies the minimum number of cases is calculated as a count of cases that must contain the itemset.</span></span> <span data-ttu-id="a7413-183">メモリに制限がある場合は、アルゴリズムによってこのパラメーターの値が自動的に増加されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a7413-183">The algorithm might automatically increase the value of this parameter if memory is limited.</span></span>  
  
 <span data-ttu-id="a7413-184">既定値は 0.03 です。</span><span class="sxs-lookup"><span data-stu-id="a7413-184">The default is 0.03.</span></span> <span data-ttu-id="a7413-185">この場合、アイテムセットがモデルに含まれるためには少なくとも 3% のケースで検出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7413-185">This means that to be included in the model, an itemset must be found in at least 3% of cases.</span></span>  
  
 <span data-ttu-id="a7413-186">*OPTIMIZED_PREDICTION_COUNT*</span><span class="sxs-lookup"><span data-stu-id="a7413-186">*OPTIMIZED_PREDICTION_COUNT*</span></span>  
 <span data-ttu-id="a7413-187">予測を最適化するためにキャッシュされるアイテムの数を定義します。</span><span class="sxs-lookup"><span data-stu-id="a7413-187">Defines the number of items to be cached for optimizing prediction.</span></span>  
  
 <span data-ttu-id="a7413-188">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="a7413-188">The default value is 0.</span></span> <span data-ttu-id="a7413-189">既定値を使用した場合、クエリで要求された数だけ予測が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-189">When the default is used, the algorithm will produce as many predictions as requested in the query.</span></span>  
  
 <span data-ttu-id="a7413-190">*OPTIMIZED_PREDICTION_COUNT* に対して 0 以外の値を指定した場合は、追加の予測を要求したとしても、返される予測の数は多くても指定したアイテム数になります。</span><span class="sxs-lookup"><span data-stu-id="a7413-190">If you specify a nonzero value for *OPTIMIZED_PREDICTION_COUNT,* prediction queries can return at most the specified number of items, even if you request additional predictions.</span></span> <span data-ttu-id="a7413-191">ただし、値を設定することで予測のパフォーマンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7413-191">However, setting a value can improve prediction performance.</span></span>  
  
 <span data-ttu-id="a7413-192">たとえば、この値を 3 に設定すると、3 つのアイテムだけが予測用にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a7413-192">For example, if the value is set to 3, the algorithm caches only 3 items for prediction.</span></span> <span data-ttu-id="a7413-193">返される 3 つの項目と同程度の可能性を持つ他の予測を見ることはできません。</span><span class="sxs-lookup"><span data-stu-id="a7413-193">You cannot see additional predictions that might be equally probable to the 3 items that are returned.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="a7413-194">ModelingFlags</span><span class="sxs-lookup"><span data-stu-id="a7413-194">Modeling Flags</span></span>  
 <span data-ttu-id="a7413-195">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムでは、次のモデリング フラグを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7413-195">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span>  
  
 <span data-ttu-id="a7413-196">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="a7413-196">NOT NULL</span></span>  
 <span data-ttu-id="a7413-197">列に NULL を含めることはできないことを示します。</span><span class="sxs-lookup"><span data-stu-id="a7413-197">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="a7413-198">モデルのトレーニング中に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] NULL が検出された場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a7413-198">An error will result if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a null during model training.</span></span>  
  
 <span data-ttu-id="a7413-199">マイニング構造列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-199">Applies to the mining structure column.</span></span>  
  
 <span data-ttu-id="a7413-200">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="a7413-200">MODEL_EXISTENCE_ONLY</span></span>  
 <span data-ttu-id="a7413-201">列が、`Missing` および `Existing` の 2 つの可能な状態を持つ列として扱われることを示します。</span><span class="sxs-lookup"><span data-stu-id="a7413-201">Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="a7413-202">NULL は Missing 値になります。</span><span class="sxs-lookup"><span data-stu-id="a7413-202">A null is a missing value.</span></span>  
  
 <span data-ttu-id="a7413-203">マイニング モデル列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a7413-203">Applies to the mining model column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7413-204">必要条件</span><span class="sxs-lookup"><span data-stu-id="a7413-204">Requirements</span></span>  
 <span data-ttu-id="a7413-205">アソシエーション モデルには、キー列、入力列、および 1 つの予測可能列が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7413-205">An association model must contain a key column, input columns, and a single predictable column.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="a7413-206">入力列と予測可能列</span><span class="sxs-lookup"><span data-stu-id="a7413-206">Input and Predictable Columns</span></span>  
 <span data-ttu-id="a7413-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムでは、次の表に示す特定の入力列と予測可能列がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a7413-207">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="a7413-208">マイニング モデルにおけるコンテンツの種類の意味については、「[コンテンツの種類 (データ マイニング)](content-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7413-208">For more information about the meaning of content types in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="a7413-209">列</span><span class="sxs-lookup"><span data-stu-id="a7413-209">Column</span></span>|<span data-ttu-id="a7413-210">コンテンツの種類</span><span class="sxs-lookup"><span data-stu-id="a7413-210">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="a7413-211">入力属性</span><span class="sxs-lookup"><span data-stu-id="a7413-211">Input attribute</span></span>|<span data-ttu-id="a7413-212">Cyclical、Discrete、Discretized、Key、Table、Ordered</span><span class="sxs-lookup"><span data-stu-id="a7413-212">Cyclical, Discrete, Discretized, Key, Table, Ordered</span></span>|  
|<span data-ttu-id="a7413-213">予測可能な属性</span><span class="sxs-lookup"><span data-stu-id="a7413-213">Predictable attribute</span></span>|<span data-ttu-id="a7413-214">Cyclical、Discrete、Discretized、Table、Ordered</span><span class="sxs-lookup"><span data-stu-id="a7413-214">Cyclical, Discrete, Discretized, Table, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a7413-215">コンテンツの種類 Cyclical および Ordered はサポートされますが、アルゴリズムはこれらを不連続の値として扱い、特別な処理は行いません。</span><span class="sxs-lookup"><span data-stu-id="a7413-215">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7413-216">参照</span><span class="sxs-lookup"><span data-stu-id="a7413-216">See Also</span></span>  
 <span data-ttu-id="a7413-217">[Microsoft アソシエーションアルゴリズム](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a7413-217">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="a7413-218">[アソシエーションモデルのクエリ例](association-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="a7413-218">[Association Model Query Examples](association-model-query-examples.md) </span></span>  
 [<span data-ttu-id="a7413-219">アソシエーション モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="a7413-219">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
