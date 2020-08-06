---
title: コールセンターモデルの調査 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2aceec298ba78e29988571293f8422ab9e55aa97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719124"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="ee5cb-102">コール センター モデルの検証 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="ee5cb-102">Exploring the Call Center Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="ee5cb-103">調査モデルを構築したら、それを使用して、データについてより深く考察することができます。具体的には、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] に備わっている次のツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-103">Now that you have built the exploratory model, you can use it to learn more about your data by using the following tools provided in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="ee5cb-104">[Microsoft ニューラルネットワークビューアー](#bkmk_NNviewer) **:** このビューアーは、データマイニングデザイナーの [**マイニングモデルビューアー** ] タブで使用でき、データの相互作用をテストするのに役立つように設計されています。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-104">[Microsoft Neural Network Viewer](#bkmk_NNviewer) **:** This viewer is available in the **Mining Model Viewer** tab of Data Mining Designer, and is designed to help you experiment with interactions in the data.</span></span>  
  
-   <span data-ttu-id="ee5cb-105">[Microsoft 汎用コンテンツツリービューアー](#bkmk_genviewer) **:** この標準ビューアーは、モデルの生成時にアルゴリズムによって検出されたパターンと統計に関する詳細な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-105">[Microsoft Generic Content Tree Viewer](#bkmk_genviewer) **:** This standard viewer provides in-depth detail about the patterns and statistics discovered by the algorithm when it generated the model.</span></span>  
  
##  <a name="microsoft-neural-network-viewer"></a><a name="bkmk_NNviewer"></a><span data-ttu-id="ee5cb-106">Microsoft ニューラルネットワークビューアー</span><span class="sxs-lookup"><span data-stu-id="ee5cb-106">Microsoft Neural Network Viewer</span></span>  
 <span data-ttu-id="ee5cb-107">ビューアーには、**入力**、**出力**、および**変数**の3つのペインがあります。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-107">The viewer has three panes - **Input**, **Output**, and **Variables**.</span></span>  
  
 <span data-ttu-id="ee5cb-108">[**出力**] ペインを使用すると、予測可能な属性または依存変数に対して異なる値を選択できます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-108">By using the **Output** pane, you can select different values for the predictable attribute, or dependent variable.</span></span> <span data-ttu-id="ee5cb-109">モデルに複数の予測可能な属性が含まれている場合は、[**出力属性**] の一覧から属性を選択できます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-109">If your model contains multiple predictable attributes, you can select the attribute from the **Output Attribute** list.</span></span>  
  
 <span data-ttu-id="ee5cb-110">[**変数**] ペインでは、貢献する属性 (変数) の観点から選択した2つの結果が比較されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-110">The **Variables** pane compares the two outcomes that you chose in terms of contributing attributes, or variables.</span></span> <span data-ttu-id="ee5cb-111">色分けされたバーは、対象となる結果に対し、変数がどの程度強く影響を与えているかを視覚的に表します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-111">The colored bars visually represent how strongly the variable affects the target outcomes.</span></span> <span data-ttu-id="ee5cb-112">変数のリフト スコアを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-112">You can also view lift scores for the variables.</span></span> <span data-ttu-id="ee5cb-113">リフト スコアは、使用しているマイニング モデルの種類によって計算方法が異なりますが、一般には、予測にこの属性を使用した場合のモデルの改善状況を示します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-113">A lift score is calculated differently depending on which mining model type you are using, but generally tells you the improvement in the model when using this attribute for prediction.</span></span>  
  
 <span data-ttu-id="ee5cb-114">**入力**ペインでは、モデルに影響力を追加して、さまざまな what-if シナリオを試すことができます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-114">The **Input** pane lets you add influencers to the model to try out various what-if scenarios.</span></span>  
  
### <a name="using-the-output-pane"></a><span data-ttu-id="ee5cb-115">[出力] ペインの使用</span><span class="sxs-lookup"><span data-stu-id="ee5cb-115">Using the Output Pane</span></span>  
 <span data-ttu-id="ee5cb-116">この初期モデルでは、サービスのグレードに対して各種の要因がどのように影響を及ぼしているかを調べます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-116">In this initial model, you are interested in seeing how various factors affect the grade of service.</span></span> <span data-ttu-id="ee5cb-117">これを行うには、出力属性の一覧から [サービスグレード] を選択し、[**値 1** ] と [**値 2**] のドロップダウンリストから範囲を選択して、異なるサービスレベルを比較します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-117">To do this, you can select Service Grade from the list of output attributes, and then compare different levels of service by selecting ranges from the dropdown lists for **Value 1** and **Value 2**.</span></span>  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a><span data-ttu-id="ee5cb-118">最低と最高のサービス グレードを比較するには</span><span class="sxs-lookup"><span data-stu-id="ee5cb-118">To compare lowest and highest service grades</span></span>  
  
1.  <span data-ttu-id="ee5cb-119">[**値 1**] で、最小値を持つ範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-119">For **Value 1**, select the range with the lowest values.</span></span> <span data-ttu-id="ee5cb-120">たとえば、0 ～ 0.07 の範囲は、最低の電話放棄呼率 (つまり、最高のサービス水準) を表します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-120">For example, the range 0-0-0.7 represents the lowest abandon rates, and therefore the best level of service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee5cb-121">この範囲に含まれる厳密な値は、モデルの構成方法によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-121">The exact values in this range may vary depending on how you configured the model.</span></span>  
  
2.  <span data-ttu-id="ee5cb-122">[**値 2**] では、値が最も大きい範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-122">For **Value 2**, select the range with the highest values.</span></span> <span data-ttu-id="ee5cb-123">たとえば、>= 0.12 という値を持つ範囲は、最大の破棄率を表します。したがって、最も悪いサービスグレードです。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-123">For example, the range with the value >=0.12 represents the highest abandon rates, and therefore the worst service grade.</span></span> <span data-ttu-id="ee5cb-124">つまり、このシフト中に電話をかけてきた顧客の 12% が、担当者が応対する前に電話を切ったことになります。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-124">In other words, 12% of the customers who phoned during this shift hung up before speaking to a representative.</span></span>  
  
     <span data-ttu-id="ee5cb-125">[**変数**] ペインの内容が更新され、結果値に寄与する属性が比較されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-125">The contents of the **Variables** pane are updated to compare attributes that contribute to the outcome values.</span></span> <span data-ttu-id="ee5cb-126">左側の列は、最高グレードのサービスに関連付けられている属性を表し、右側の列は、最低グレードのサービスに関連付けられている属性を表します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-126">Therefore, the left column shows you the attributes that are associated with the best grade of service, and the right column shows you the attributes associated with the worst grade of service.</span></span>  
  
### <a name="using-the-variables-pane"></a><span data-ttu-id="ee5cb-127">[変数] ペインの使用</span><span class="sxs-lookup"><span data-stu-id="ee5cb-127">Using the Variables Pane</span></span>  
 <span data-ttu-id="ee5cb-128">このモデルでは、重要な要素として表示され `Average Time Per Issue` ます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-128">In this model, it appears that `Average Time Per Issue` is an important factor.</span></span> <span data-ttu-id="ee5cb-129">この変数は、問い合わせの種類に関係なく、問い合わせから回答までに要した平均時間を示します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-129">This variable indicates the average time that it takes for a call to be answered, regardless of call type.</span></span>  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a><span data-ttu-id="ee5cb-130">属性の確率スコアとリフト スコアを表示およびコピーするには</span><span class="sxs-lookup"><span data-stu-id="ee5cb-130">To view and copy probability and lift scores for an attribute</span></span>  
  
1.  <span data-ttu-id="ee5cb-131">[**変数**] ペインで、最初の行の色分けされたバーの上にマウスポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-131">In the **Variables** pane, pause the mouse over the colored bar in the first row.</span></span>  
  
     <span data-ttu-id="ee5cb-132">この色分けされたバーは `Average Time Per Issue` 、サービスグレードに対して非常に大きな影響を与える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-132">This colored bar shows you how strongly `Average Time Per Issue` contributes toward the service grade.</span></span> <span data-ttu-id="ee5cb-133">ツールヒントには、変数と対象となる結果の組み合わせごとに、全体的なスコア、確率、およびリフト スコアが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-133">The tooltip shows an overall score, probabilities, and lift scores for each combination of a variable and a target outcome.</span></span>  
  
2.  <span data-ttu-id="ee5cb-134">[**変数**] ペインで、色分けされたバーを右クリックし、[**コピー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-134">In the **Variables** pane, right-click any colored bar and select **Copy**.</span></span>  
  
3.  <span data-ttu-id="ee5cb-135">Excel ワークシートで、任意のセルを右クリックし、[**貼り付け**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-135">In an Excel worksheet, right-click any cell and select **Paste**.</span></span>  
  
     <span data-ttu-id="ee5cb-136">レポートが HTML テーブルとして貼り付けられ、各バーのスコアだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-136">The report is pasted as an HTML table, and shows only the scores for each bar.</span></span>  
  
4.  <span data-ttu-id="ee5cb-137">別の Excel ワークシートで、任意のセルを右クリックし、[**特殊な貼り付け**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-137">In a different Excel worksheet, right-click any cell and select **Paste Special**.</span></span>  
  
     <span data-ttu-id="ee5cb-138">レポートがテキスト形式で貼り付けられ、関連する統計 (次のセクションで説明) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-138">The report is pasted as text format, and includes the related statistics described in the next section.</span></span>  
  
### <a name="using-the-input-pane"></a><span data-ttu-id="ee5cb-139">[入力] ペインの使用</span><span class="sxs-lookup"><span data-stu-id="ee5cb-139">Using the Input Pane</span></span>  
 <span data-ttu-id="ee5cb-140">シフトやオペレーターの人数など、特定の要因の影響を調べているとします。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-140">Suppose that you are interested in looking at the effect of a particular factor, such as the shift, or number of operators.</span></span> <span data-ttu-id="ee5cb-141">[**入力**] ペインを使用して特定の変数を選択すると、[**変数**] ペインが自動的に更新され、指定した変数が指定された2つ前に選択したグループが比較されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-141">You can select a particular variable by using the **Input** pane, and the **Variables** pane is automatically updated to compare the two previously selected groups given the specified variable.</span></span>  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a><span data-ttu-id="ee5cb-142">入力属性を変更することによってサービス グレードへの影響をレビューするには</span><span class="sxs-lookup"><span data-stu-id="ee5cb-142">To review the effect on service grade by changing input attributes</span></span>  
  
1.  <span data-ttu-id="ee5cb-143">[**入力**] ペインの [**属性**] で、[Shift] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-143">In the **Input** pane, for **attribute**, select Shift.</span></span>  
  
2.  <span data-ttu-id="ee5cb-144">[**値**] で [ **AM**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-144">For **Value**, select **AM**.</span></span>  
  
     <span data-ttu-id="ee5cb-145">[**変数**] ペインが更新され、シフトが**AM**の場合のモデルへの影響が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-145">The **Variables** pane updates to show the impact on the model when the shift is **AM**.</span></span> <span data-ttu-id="ee5cb-146">それ以外のすべての選択は変わりません。サービスグレードの最低値と最高値を比較しています。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-146">All other selections remain the same - you are still comparing the lowest and highest service grades.</span></span>  
  
3.  <span data-ttu-id="ee5cb-147">[**値**] で、[ **PM1**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-147">For **Value**, select **PM1**.</span></span>  
  
     <span data-ttu-id="ee5cb-148">[**変数**] ペインが更新され、シフトが変化したときのモデルへの影響が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-148">The **Variables** pane updates to show the impact on the model when the shift changes.</span></span>  
  
4.  <span data-ttu-id="ee5cb-149">[**入力**] ペインで、[**属性**] の次の空白行をクリックし、[呼び出し] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-149">In the **Input** pane, click the next blank row under **Attribute**, and select Calls.</span></span> <span data-ttu-id="ee5cb-150">[**値**] で、呼び出しの最大数を示す範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-150">For **Value**, select the range that indicates the greatest number of calls.</span></span>  
  
     <span data-ttu-id="ee5cb-151">リストに新しい入力条件が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-151">A new input condition is added to the list.</span></span> <span data-ttu-id="ee5cb-152">[**変数**] ペインが更新され、呼び出しボリュームが最高の場合の特定のシフトのモデルへの影響が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-152">The **Variables** pane updates to show the impact on the model for a particular shift when the call volume is highest.</span></span>  
  
5.  <span data-ttu-id="ee5cb-153">[シフト] および [問い合わせ] の値を変更しながら、シフト、問い合わせ件数、およびサービス グレードの間に、何か相関関係がないか見極めます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-153">Continue to change the values for Shift and Calls to find any interesting correlations between shift, call volume, and service grade.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee5cb-154">異なる属性を使用できるように**入力**ウィンドウをクリアするには、[**ビューアーのコンテンツを最新の情報に更新**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-154">To clear the **Input** pane so that you can use different attributes, click **Refresh viewer content**.</span></span>  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a><span data-ttu-id="ee5cb-155">ビューアーに表示される統計の解釈</span><span class="sxs-lookup"><span data-stu-id="ee5cb-155">Interpreting the Statistics Provided in the Viewer</span></span>  
 <span data-ttu-id="ee5cb-156">待ち時間が長ければ、電話放棄呼率が高くなり、サービス グレードも低下します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-156">Longer waiting times are a strong predictor of a high abandon rate, meaning a poor service grade.</span></span> <span data-ttu-id="ee5cb-157">当然の結果のようにも見えますが、マイニング モデルは、その傾向を読み解くための補足的な統計データをいくつか提供します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-157">This may seem an obvious conclusion; however, the mining model provides you with some additional statistical data to help you interpret these trends.</span></span>  
  
-   <span data-ttu-id="ee5cb-158">**Score**: 結果間の識別のこの変数の全体的な重要度を示す値。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-158">**Score**: Value that indicates the overall importance of this variable for discriminating between outcomes.</span></span> <span data-ttu-id="ee5cb-159">スコアが高いほど、その変数が結果に及ぼす影響は強くなります。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-159">The higher the score, the stronger the effect the variable has on the outcome.</span></span>  
  
-   <span data-ttu-id="ee5cb-160">**値1の確率**: この結果のこの値の確率を表します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-160">**Probability of value 1**: Percentage that represents the probability of this value for this outcome.</span></span>  
  
-   <span data-ttu-id="ee5cb-161">**値2の確率**: この結果のこの値の確率を表すパーセント値。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-161">**Probability of value 2**: Percentage that represents the probability of this value for this outcome.</span></span>  
  
-   <span data-ttu-id="ee5cb-162">値**1 のリフト**と値**2 のリフト**: 値1と値2の結果を予測するためにこの特定の変数を使用した場合の影響を表すスコア。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-162">**Lift for Value 1** and **Lift for Value 2**: Scores that represents the impact of using this particular variable for predicting the Value 1 and Value 2 outcomes.</span></span> <span data-ttu-id="ee5cb-163">スコアが高いほど、その変数を使って、効果的に結果を予測することができます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-163">The higher the score, the better the variable is at predicting the outcomes.</span></span>  
  
 <span data-ttu-id="ee5cb-164">次の表に、トップ インフルエンサについて、いくつかの値の例を示します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-164">The following table contains some example values for the top influencers.</span></span> <span data-ttu-id="ee5cb-165">たとえば、**値1の確率**は60.6% で、**値2の確率**は8.30% です。つまり、各問題の平均時間が44-70 分の範囲内にあった場合は、60.6% が最も高いサービスグレード (値 1) でシフトされ、ケースの8.30% は、サービスグレードが悪くなります (値 2)。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-165">For example, the **Probability of value 1** is 60.6% and **Probability of value 2** is 8.30%, meaning that when the Average Time Per Issue was in the range of 44-70 minutes, 60.6% of cases were in the shift with the highest service grades (Value 1), and 8.30% of cases were in the shift with the worse service grades (Value 2).</span></span>  
  
 <span data-ttu-id="ee5cb-166">この情報からは、いくつかの結論を導き出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-166">From this information, you can draw some conclusions.</span></span> <span data-ttu-id="ee5cb-167">問い合わせ応対時間が短いことは (44 ～ 70 の範囲)、サービス グレードの向上に強く影響しています (0.00 ～ 0.07 の範囲)。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-167">Shorter call response time (the range of 44-70) strongly influences better service grade (the range 0.00-0.07).</span></span> <span data-ttu-id="ee5cb-168">スコア (92.35) からも、この変数が非常に重要であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-168">The score (92.35) tells you that this variable is very important.</span></span>  
  
 <span data-ttu-id="ee5cb-169">ただし、要因リストの下の方に目を向けると、影響が微弱で解釈が難しいその他の要因がいくつか確認できます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-169">However, as you look down the list of contributing factors, you see some other factors with effects that are more subtle and more difficult to interpret.</span></span> <span data-ttu-id="ee5cb-170">たとえば、シフトは一見、サービスに影響を及ぼすように見えますが、リフト スコアおよび相対的確率を見る限り、シフトはさほど大きな要因ではありません。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-170">For example, shift appears to influence service, but the lift scores and the relative probabilities indicate that shift is not a major factor.</span></span>  
  
|<span data-ttu-id="ee5cb-171">属性</span><span class="sxs-lookup"><span data-stu-id="ee5cb-171">Attribute</span></span>|<span data-ttu-id="ee5cb-172">値</span><span class="sxs-lookup"><span data-stu-id="ee5cb-172">Value</span></span>|<span data-ttu-id="ee5cb-173">0.07 を優先 \<</span><span class="sxs-lookup"><span data-stu-id="ee5cb-173">Favors \< 0.07</span></span>|<span data-ttu-id="ee5cb-174">優先 >= 0.12</span><span class="sxs-lookup"><span data-stu-id="ee5cb-174">Favors >= 0.12</span></span>|  
|---------------|-----------|--------------------|----------------------|  
|<span data-ttu-id="ee5cb-175">案件あたりの平均時間</span><span class="sxs-lookup"><span data-stu-id="ee5cb-175">Average Time Per Issue</span></span>|<span data-ttu-id="ee5cb-176">89.087 ~ 120.000</span><span class="sxs-lookup"><span data-stu-id="ee5cb-176">89.087 - 120.000</span></span>||<span data-ttu-id="ee5cb-177">スコア: 100</span><span class="sxs-lookup"><span data-stu-id="ee5cb-177">Score:  100</span></span><br /><br /> <span data-ttu-id="ee5cb-178">Value1 の確率: 4.45%</span><span class="sxs-lookup"><span data-stu-id="ee5cb-178">Probability of Value1: 4.45 %</span></span><br /><br /> <span data-ttu-id="ee5cb-179">Value2 の確率: 51.94%</span><span class="sxs-lookup"><span data-stu-id="ee5cb-179">Probability of Value2: 51.94 %</span></span><br /><br /> <span data-ttu-id="ee5cb-180">Value1 のリフト: 0.19</span><span class="sxs-lookup"><span data-stu-id="ee5cb-180">Lift for Value1: 0.19</span></span><br /><br /> <span data-ttu-id="ee5cb-181">Value2 のリフト: 1.94</span><span class="sxs-lookup"><span data-stu-id="ee5cb-181">Lift for Value2: 1.94</span></span>|  
|<span data-ttu-id="ee5cb-182">案件あたりの平均時間</span><span class="sxs-lookup"><span data-stu-id="ee5cb-182">Average Time Per Issue</span></span>|<span data-ttu-id="ee5cb-183">44.000 ~ 70.597</span><span class="sxs-lookup"><span data-stu-id="ee5cb-183">44.000 - 70.597</span></span>|<span data-ttu-id="ee5cb-184">スコア : 92.35</span><span class="sxs-lookup"><span data-stu-id="ee5cb-184">Score: 92.35</span></span><br /><br /> <span data-ttu-id="ee5cb-185">値 1 の確率 : 60.06 %</span><span class="sxs-lookup"><span data-stu-id="ee5cb-185">Probability of Value1: 60.06 %</span></span><br /><br /> <span data-ttu-id="ee5cb-186">値 2 の確率 : 8.30 %</span><span class="sxs-lookup"><span data-stu-id="ee5cb-186">Probability of Value2: 8.30 %</span></span><br /><br /> <span data-ttu-id="ee5cb-187">値 1 のリフト : 2.61</span><span class="sxs-lookup"><span data-stu-id="ee5cb-187">Lift for Value1: 2.61</span></span><br /><br /> <span data-ttu-id="ee5cb-188">値 2 のリフト : 0.31</span><span class="sxs-lookup"><span data-stu-id="ee5cb-188">Lift for Value2: 0.31</span></span>||  
  
 [<span data-ttu-id="ee5cb-189">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="ee5cb-189">Back to Top</span></span>](#bkmk_NNviewer)  
  
##  <a name="microsoft-generic-content-tree-viewer"></a><a name="bkmk_genviewer"></a><span data-ttu-id="ee5cb-190">Microsoft 汎用コンテンツツリービューアー</span><span class="sxs-lookup"><span data-stu-id="ee5cb-190">Microsoft Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="ee5cb-191">このビューアーを使用すると、モデルの処理時にアルゴリズムによって作成された、さらに詳しい情報を閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-191">This viewer can be used to view even more detailed information created by the algorithm when the model is processed.</span></span> <span data-ttu-id="ee5cb-192">**Microsoft 汎用コンテンツツリービューアー**は、マイニングモデルを一連のノードとして表します。各ノードは、トレーニングデータに関する学習済みの知識を表します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-192">The **MicrosoftGeneric Content Tree Viewer** represents the mining model as a series of nodes, wherein each node represents learned knowledge about the training data.</span></span> <span data-ttu-id="ee5cb-193">このビューアーは、あらゆるモデルで使用できますが、ノードの内容はモデルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-193">This viewer can be used with all models, but the contents of the nodes are different depending in the model type.</span></span>  
  
 <span data-ttu-id="ee5cb-194">ニューラル ネットワーク モデルまたはロジスティック回帰モデルの場合、特に重要なのは `marginal statistics node` です。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-194">For neural network models or logistic regression models, you might find the `marginal statistics node` particularly useful.</span></span> <span data-ttu-id="ee5cb-195">このノードには、データに含まれる値の分布に関して得られた統計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-195">This node contains derived statistics about the distribution of values in your data.</span></span> <span data-ttu-id="ee5cb-196">この情報は、多数の T-SQL クエリを作成せずにデータの概要を取得する必要がある場合に、役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-196">This information can be useful if you want to get a summary of the data without having to write many T-SQL queries.</span></span> <span data-ttu-id="ee5cb-197">前のトピックで、ビン分割値のグラフを取り上げましたが、このグラフは、マージナル統計ノードから導かれたものです。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-197">The chart of binning values in the previous topic was derived from the marginal statistics node.</span></span>  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a><span data-ttu-id="ee5cb-198">マイニング モデルからデータ値の概要を取得するには</span><span class="sxs-lookup"><span data-stu-id="ee5cb-198">To obtain a summary of data values from the mining model</span></span>  
  
1.  <span data-ttu-id="ee5cb-199">データマイニングデザイナーの [**マイニングモデルビューアー** ] タブで、を選択し \<mining model name> ます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-199">In Data Mining Designer, in the **Mining Model Viewer** tab, select \<mining model name>.</span></span>  
  
2.  <span data-ttu-id="ee5cb-200">[**ビューアー** ] ボックスの一覧から [ **Microsoft 汎用コンテンツツリービューアー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-200">From the **Viewer** list, select **Microsoft Generic Content Tree Viewer**.</span></span>  
  
     <span data-ttu-id="ee5cb-201">マイニング モデルのビューが更新されて、左側のペインにノード階層が、右側のペインに HTML テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-201">The view of the mining model refreshes to show a node hierarchy in the left-hand pane and an HTML table in the right-hand pane.</span></span>  
  
3.  <span data-ttu-id="ee5cb-202">[**ノードのキャプション**] ペインで、名前が10000000000000000のノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-202">In the **Node Caption** pane, click the node that has the name 10000000000000000.</span></span>  
  
     <span data-ttu-id="ee5cb-203">どのモデルにも言えることですが、最上位のノードは常に、そのモデルのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-203">The topmost node in any model is always the model root node.</span></span> <span data-ttu-id="ee5cb-204">ニューラル ネットワーク モデルまたはロジスティック回帰モデルでは、その直下のノードがマージナル統計ノードです。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-204">In a neural network or logistic regression model, the node immediately under that is the marginal statistics node.</span></span>  
  
4.  <span data-ttu-id="ee5cb-205">[**ノードの詳細**] ペインで、行が表示されるまで下にスクロールして NODE_DISTRIBUTION ます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-205">In the **Node Details** pane, scroll down until you find the row, NODE_DISTRIBUTION.</span></span>  
  
5.  <span data-ttu-id="ee5cb-206">NODE_DISTRIBUTION テーブルを下にスクロールして、ニューラル ネットワークのアルゴリズムによって計算された値の分布を表示します。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-206">Scroll down through the NODE_DISTRIBUTION table to view the distribution of values as calculated by the neural network algorithm.</span></span>  
  
 <span data-ttu-id="ee5cb-207">このデータをレポートに使用するには、特定の行の情報を選択してコピーします。または、次のデータ マイニング拡張機能 (DMX) クエリを使用して、ノードの完全な内容を抽出することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-207">To use this data in a report, you could select and then copy the information for specific rows, or you can use the following Data Mining Extensions (DMX) query to extract the complete contents of the node.</span></span>  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 <span data-ttu-id="ee5cb-208">ノード階層と、NODE_DISTRIBUTION テーブル内の詳細情報を使用して、ニューラル ネットワーク内のパスを個別にたどり、非表示になっているレイヤーの統計を閲覧することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-208">You can also use the node hierarchy and the details in the NODE_DISTRIBUTION table to traverse individual paths in the neural network and view statistics from the hidden layer.</span></span> <span data-ttu-id="ee5cb-209">詳細については、「[ニューラルネットワークモデルのクエリ例](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee5cb-209">For more information, see [Neural Network Model Query Examples](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="ee5cb-210">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="ee5cb-210">Back to Top</span></span>](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ee5cb-211">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="ee5cb-211">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ee5cb-212">呼び出しセンター構造へのロジスティック回帰モデルの追加 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="ee5cb-212">Adding a Logistic Regression Model to the Call Center Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee5cb-213">参照</span><span class="sxs-lookup"><span data-stu-id="ee5cb-213">See Also</span></span>  
 <span data-ttu-id="ee5cb-214">[ニューラルネットワークモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ee5cb-214">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="ee5cb-215">[ニューラルネットワークモデルのクエリ例](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="ee5cb-215">[Neural Network Model Query Examples](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md) </span></span>  
 <span data-ttu-id="ee5cb-216">[Microsoft ニューラルネットワークアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ee5cb-216">[Microsoft Neural Network Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="ee5cb-217">マイニング モデルでの列の分離の変更</span><span class="sxs-lookup"><span data-stu-id="ee5cb-217">Change the Discretization of a Column in a Mining Model</span></span>](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
