---
title: 利益チャート (Analysis Services-データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy, charting
- revenue, estimating
- benefits, estimating
- charts [Analysis Services]
- profit charts [Analysis Services]
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
author: minewiskan
ms.author: owend
ms.openlocfilehash: a38a1d5062f53de4be9129c2305d8d3c84593f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718932"
---
# <a name="profit-chart-analysis-services---data-mining"></a><span data-ttu-id="ea49b-102">利益チャート (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="ea49b-102">Profit Chart (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="ea49b-103">利益チャートには、マイニング モデルの使用に関連して推定される収益性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-103">A profit chart displays the estimated profitability associated with using a mining model.</span></span> <span data-ttu-id="ea49b-104">たとえば、ビジネスシナリオにおいて会社がどの顧客に連絡する必要があるかをモデルが予測しているとします。</span><span class="sxs-lookup"><span data-stu-id="ea49b-104">For example, let's assume your model predicts which customers a company should contact in a business scenario.</span></span> <span data-ttu-id="ea49b-105">この場合、利益チャートに対して、ターゲット メーリング キャンペーンの実施コストに関する情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-105">In that case, you would add to the profit chart information about the cost of conducting the targeted mailing campaign.</span></span> <span data-ttu-id="ea49b-106">その後、完成したチャートで、ランダムに顧客に連絡を取った場合と比較して、顧客を正しくターゲット指定した場合に推定される利益を表示できます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-106">Then, in the completed chart, you can see the estimated profit if customers are correctly targeted, as compared to randomly contacting customers.</span></span>  
  
## <a name="build-a-profit-chart"></a><span data-ttu-id="ea49b-107">利益チャートの作成</span><span class="sxs-lookup"><span data-stu-id="ea49b-107">Build a Profit Chart</span></span>  
 <span data-ttu-id="ea49b-108">利益チャートは、リフト チャートに似ています。</span><span class="sxs-lookup"><span data-stu-id="ea49b-108">A profit chart is similar to a lift chart.</span></span> <span data-ttu-id="ea49b-109">最初にリフト チャートを作成し、その後にコスト情報と利益情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-109">You start by creating a lift chart, and then add in the cost and profit information.</span></span>  
  
 <span data-ttu-id="ea49b-110">利益チャートを作成するには、既存のモデルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea49b-110">To build a profit chart, you must have an existing model.</span></span>  
  
 <span data-ttu-id="ea49b-111">この例では、絞り込みメールのデシジョン ツリー モデルを使用しました。</span><span class="sxs-lookup"><span data-stu-id="ea49b-111">For this example, we used the Targeted Mailing decision tree model.</span></span> <span data-ttu-id="ea49b-112">このモデルでは、自転車を購入する可能性がある顧客を識別します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-112">The model identifies customers who are likely to buy a bike.</span></span> <span data-ttu-id="ea49b-113">**[利益チャート]** を適用して、利益を最大化するためにターゲット指定する顧客の数を判断することができます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-113">You can apply the **Profit Chart** to determine how many of your customers to target to maximize your profit.</span></span>  
  
 <span data-ttu-id="ea49b-114">サンプルモデルを持っていない場合は、「[基本的なデータマイニングチュートリアル](../../tutorials/basic-data-mining-tutorial.md)」を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-114">If you don't have the sample model, you can create it using the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
1.  <span data-ttu-id="ea49b-115">マイニング精度チャート ビルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-115">Open the mining accuracy chart builder.</span></span>  
  
    -   <span data-ttu-id="ea49b-116">SQL Server Management Studio でモデルを右クリックし、 **[リフト チャートの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea49b-116">In SQL Server Management Studio, right-click the model, and select **View Lift Chart**.</span></span>  
  
    -   <span data-ttu-id="ea49b-117">SQL Server Data Tools で、モデルを作成したときに使用したプロジェクトを開き、 **[マイニング精度チャート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea49b-117">In SQL Server Data Tools, open the project in which you created the model, and click the **Mining Accuracy Chart** tab.</span></span>  
  
2.  <span data-ttu-id="ea49b-118">**[入力の選択]** タブでモデルを選択し、予測可能な属性値を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-118">In **the Input Selection** tab, select the model and choose the predictable attribute value.</span></span>  
  
     <span data-ttu-id="ea49b-119">この特定のシナリオでは、[Bike Buyer] =1 という 1 つの値のみを正確に予測した状況の収益性のみに関心があります。</span><span class="sxs-lookup"><span data-stu-id="ea49b-119">For this particular scenario, you are interested only in the profitability of accurately predicting one value: [Bike Buyer] =1.</span></span>  
  
     <span data-ttu-id="ea49b-120">ただし、他のシナリオでは、false 値を正しく予測した状況にも同様の関心を持つことがあります。</span><span class="sxs-lookup"><span data-stu-id="ea49b-120">However, there are other scenarios in which you are equally interested in predicting false values correctly.</span></span> <span data-ttu-id="ea49b-121">たとえば、医療検診で偽陰性 (実際は兆候があるものを見逃す) のコストに比較して、偽陽性 (実際は兆候がないものを誤って有意と判定する) のコストが非常に高く、予測の収益性の一部として考慮する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="ea49b-121">For example, the cost of a false positive on a medical diagnostic test can be significant and needs to be factored into the profitability of the prediction, as does the cost of false negatives.</span></span> <span data-ttu-id="ea49b-122">このようなシナリオでは、すべての結果を測定することになります。</span><span class="sxs-lookup"><span data-stu-id="ea49b-122">In such scenarios, you would measure all outcomes.</span></span>  
  
3.  <span data-ttu-id="ea49b-123">テストに使用するデータ セットを選択します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-123">Select a data set for testing.</span></span> <span data-ttu-id="ea49b-124">この例では、テスト用のデータ セットを選択します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-124">For this example, select the testing data set.</span></span>  
  
4.  <span data-ttu-id="ea49b-125">次に、 **[リフト チャート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea49b-125">Now click the **Lift Chart** tab.</span></span>  
  
     <span data-ttu-id="ea49b-126">リフト チャートが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-126">A lift chart is automatically generated.</span></span>  
  
5.  <span data-ttu-id="ea49b-127">このチャートを利益チャートに変換するには、 **[グラフの種類]** の一覧から **[利益チャート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-127">To change this to a profit chart, select **Profit Chart** from the **Chart type** list.</span></span>  
  
6.  <span data-ttu-id="ea49b-128">グラフの種類として利益チャートを選択するとすぐに、 **[利益チャートの設定]** ダイアログ ボックスが自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-128">As soon as you choose profit chart as the chart type, the **Profit Chart Setting** dialog box automatically opens.</span></span>  
  
     <span data-ttu-id="ea49b-129">このダイアログ ボックスは、ターゲット メーリング キャンペーンに関連付けられているコストと利益を指定するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-129">This dialog box helps you specify the costs and benefits associated with a targeted mailing campaign.</span></span> <span data-ttu-id="ea49b-130">これらの例のグラフでは、次の値を使用しました。</span><span class="sxs-lookup"><span data-stu-id="ea49b-130">For the chart shown in these examples, we used the following values:</span></span>  
  
    |<span data-ttu-id="ea49b-131">設定</span><span class="sxs-lookup"><span data-stu-id="ea49b-131">Setting</span></span>|<span data-ttu-id="ea49b-132">値</span><span class="sxs-lookup"><span data-stu-id="ea49b-132">Value</span></span>|<span data-ttu-id="ea49b-133">説明</span><span class="sxs-lookup"><span data-stu-id="ea49b-133">Comments</span></span>|  
    |-------------|-----------|--------------|  
    |<span data-ttu-id="ea49b-134">**作成**</span><span class="sxs-lookup"><span data-stu-id="ea49b-134">**Population**</span></span>|<span data-ttu-id="ea49b-135">20,000</span><span class="sxs-lookup"><span data-stu-id="ea49b-135">20,000</span></span>|<span data-ttu-id="ea49b-136">対象になる母集団の合計に対する値の設定</span><span class="sxs-lookup"><span data-stu-id="ea49b-136">Set the value for the total target population</span></span><br /><br /> <span data-ttu-id="ea49b-137">データベースに多くの顧客が含まれている可能性もありますが、郵送料を抑えるために、最も反応がありそうな上位 20,000 人の顧客のみをターゲットにすると想定します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-137">Your database might contain many customers, but to save on mailing expenses you might choose to target only the 20,000 customers who are most likely to respond.</span></span> <span data-ttu-id="ea49b-138">予測クエリを実行し、予測モデルによって出力された確率で並べ替えると、この一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-138">You can get this list by running a prediction query and sorting by the probability output by the predictive model.</span></span>|  
    |<span data-ttu-id="ea49b-139">**[固定コスト]**</span><span class="sxs-lookup"><span data-stu-id="ea49b-139">**Fixed cost**</span></span>|<span data-ttu-id="ea49b-140">500</span><span class="sxs-lookup"><span data-stu-id="ea49b-140">500</span></span>|<span data-ttu-id="ea49b-141">20,000 人の顧客に対するターゲット メーリング キャンペーンの準備にかかる 1 回限りのコストを入力します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-141">Enter the one-time cost of setting up a targeted mailing campaign for 20,000 people.</span></span> <span data-ttu-id="ea49b-142">このコストには、印刷コスト、または電子メール キャンペーンの準備コストが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea49b-142">This might include printing, or the cost of setting up an e-mail campaign.</span></span>|  
    |<span data-ttu-id="ea49b-143">**変動コスト**</span><span class="sxs-lookup"><span data-stu-id="ea49b-143">**Individual cost**</span></span>|<span data-ttu-id="ea49b-144">3</span><span class="sxs-lookup"><span data-stu-id="ea49b-144">3</span></span>|<span data-ttu-id="ea49b-145">ターゲット メーリング キャンペーンの単位あたりのコストの入力</span><span class="sxs-lookup"><span data-stu-id="ea49b-145">Enter the per-unit cost for the targeted mailing campaign.</span></span><br /><br /> <span data-ttu-id="ea49b-146">この金額に 20,000 以下の数 (実際の数は、モデルで適切な見込み客として予測された顧客の数によって決まります) を掛けた値を計算します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-146">This amount will be multiplied by a number equal to or less than 20000, depending on how many customers the model predicts are good prospects.</span></span>|  
    |<span data-ttu-id="ea49b-147">**[個人ごとの収益]**</span><span class="sxs-lookup"><span data-stu-id="ea49b-147">**Revenue per individual**</span></span>|<span data-ttu-id="ea49b-148">400</span><span class="sxs-lookup"><span data-stu-id="ea49b-148">400</span></span>|<span data-ttu-id="ea49b-149">成功した場合に期待できる利益または収入の金額を表す値の入力</span><span class="sxs-lookup"><span data-stu-id="ea49b-149">Enter a value that represents the amount of profit or income that can be expected from a successful result.</span></span> <span data-ttu-id="ea49b-150">この例では、カタログを郵送すると、付属品または自転車の平均 $400 が購入されると想定します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-150">In this case, we'll assume that mailing a catalog results in purchase of accessories or bikes averaging $400.</span></span><br /><br /> <span data-ttu-id="ea49b-151">この金額を使用して、可能性が高いケースに関連する利益総額が算出されます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-151">This amount will be used to project the total profit associated with high probability cases.</span></span>|  
  
7.  <span data-ttu-id="ea49b-152">これらの必要なパラメーターを設定した後、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea49b-152">After you have set the required parameters, click **OK**.</span></span>  
  
8.  <span data-ttu-id="ea49b-153">チャートが更新され、利益曲線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-153">The chart updates to show the profit curve.</span></span>  
  
## <a name="understanding-the-profit-chart"></a><span data-ttu-id="ea49b-154">利益チャートについて</span><span class="sxs-lookup"><span data-stu-id="ea49b-154">Understanding the Profit Chart</span></span>  
 <span data-ttu-id="ea49b-155">次の図は、これらのパラメーターに基づくグラフを示しています。</span><span class="sxs-lookup"><span data-stu-id="ea49b-155">The following diagram shows the chart that was based on these parameters.</span></span> <span data-ttu-id="ea49b-156">このチャートの Y 軸は利益を、X 軸はターゲット メーリング キャンペーンによってコンタクトした顧客が、顧客リスト全体に占める割合を示します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-156">The Y-axis of the chart represents the profit, while the X-axis represents the percentage of the customers who were contacted by the targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="ea49b-157">ここで示したように、複数のモデルが同じ不連続属性を予測する場合は、1 つの利益チャートを使用してそれらを比較することができます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-157">As shown here, you can use a profit chart to compare multiple models, as long as they all predict the same discrete attribute.</span></span>  
  
 <span data-ttu-id="ea49b-158">![3 つのモデルを比較する利益チャート](../media/dm14-profitchartupdated.gif "3 つのモデルを比較する利益チャート")</span><span class="sxs-lookup"><span data-stu-id="ea49b-158">![a profit chart comparing three models](../media/dm14-profitchartupdated.gif "a profit chart comparing three models")</span></span>  
  
 <span data-ttu-id="ea49b-159">チャート内にある灰色の垂直線に注意してください。</span><span class="sxs-lookup"><span data-stu-id="ea49b-159">Notice the gray vertical line in the chart.</span></span> <span data-ttu-id="ea49b-160">この線をクリックしてドラッグすると、現在のポイントで、対象になる母集団の何パーセントが曲線の下に含まれているかを示すツールヒントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-160">As you click and drag the line, the ToolTip display the percentage of the target population that is included under the curve at that point.</span></span>  
  
 <span data-ttu-id="ea49b-161">線をドラッグすると **[マイニング凡例]** も更新されて、割合の値、利益のスコア、および灰色の垂直線が示す母集団の割合に関連付けられている予測確率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-161">The **Mining Legend** is also updated as you drag the line, to display the percentage value, a profit score, and the predict probability that is associated with the population percentage at the vertical gray line.</span></span>  
  
 <span data-ttu-id="ea49b-162">たとえば、このモデルを使用してプロモーション資料の送付先を決定する場合は、予測確率に基づいて母集団全体のうち 25% をターゲットにする方針を決定する可能性があります。一方、チャートの利益曲線より下側にある面積は 40 ～ 70% の間で最大になっており、より多くの顧客に資料を送付すると、全体の反応率が低下するとはいえ、利益を最大化できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="ea49b-162">For example, if you were using this model to decide who to send your promotional material to, you might decide to target 25% of the population, based on the predict probabilities, However, the area under the profit curve of the chart is greatest between 40 and 70 percent, indicating that by mailing to more people, you can maximize your return, even if a smaller overall percentage responds.</span></span>  
  
## <a name="saving-charts"></a><span data-ttu-id="ea49b-163">チャートの保存</span><span class="sxs-lookup"><span data-stu-id="ea49b-163">Saving Charts</span></span>  
 <span data-ttu-id="ea49b-164">精度チャートまたは利益チャートを作成する場合、サーバー上では何もオブジェクトが作成されません。</span><span class="sxs-lookup"><span data-stu-id="ea49b-164">When you create an accuracy chart or profit chart, no objects are created on the server.</span></span> <span data-ttu-id="ea49b-165">代わりに、既存のモデルに対してクエリが実行され、結果がビューアー内で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea49b-165">Instead, queries are executed against an existing model and the results are rendered in the viewer.</span></span> <span data-ttu-id="ea49b-166">結果を保存する必要がある場合は、チャートまたは結果を Excel または別のファイルにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea49b-166">If you need to save the results, you must copy either the chart or the results to Excel or another file.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="ea49b-167">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ea49b-167">Related Content</span></span>  
 <span data-ttu-id="ea49b-168">次のトピックには、精度チャートの構築方法と使用方法に関する詳細な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ea49b-168">The following topics contain more information about how you can build and use accuracy charts.</span></span>  
  
|<span data-ttu-id="ea49b-169">トピック</span><span class="sxs-lookup"><span data-stu-id="ea49b-169">Topics</span></span>|<span data-ttu-id="ea49b-170">リンク</span><span class="sxs-lookup"><span data-stu-id="ea49b-170">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="ea49b-171">Targeted Mailing モデルのリフト チャートの作成方法に関するチュートリアルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ea49b-171">Provides a walkthrough of how to create a lift chart for the Targeted Mailing model.</span></span>|[<span data-ttu-id="ea49b-172">基本的なデータ マイニング チュートリアル</span><span class="sxs-lookup"><span data-stu-id="ea49b-172">Basic Data Mining Tutorial</span></span>](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [<span data-ttu-id="ea49b-173">リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="ea49b-173">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|  
|<span data-ttu-id="ea49b-174">関連するグラフの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-174">Explains related chart types.</span></span>|[<span data-ttu-id="ea49b-175">リフト チャート &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="ea49b-175">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="ea49b-176">分類マトリックス &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="ea49b-176">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="ea49b-177">散布図 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="ea49b-177">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="ea49b-178">マイニング モデルとマイニング構造の相互検証について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-178">Describes cross-validation for mining models and mining structures.</span></span>|[<span data-ttu-id="ea49b-179">相互検証 &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="ea49b-179">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="ea49b-180">リフト チャートおよびその他の精度チャートを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea49b-180">Describes steps for creating lift charts and other accuracy charts.</span></span>|[<span data-ttu-id="ea49b-181">テストおよび検証タスク、および操作方法 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="ea49b-181">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ea49b-182">参照</span><span class="sxs-lookup"><span data-stu-id="ea49b-182">See Also</span></span>  
 <span data-ttu-id="ea49b-183">[データマイニング&#41;のテストと検証 &#40;](testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ea49b-183">[Testing and Validation &#40;Data Mining&#41;](testing-and-validation-data-mining.md) </span></span>  
 [<span data-ttu-id="ea49b-184">リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="ea49b-184">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
  
