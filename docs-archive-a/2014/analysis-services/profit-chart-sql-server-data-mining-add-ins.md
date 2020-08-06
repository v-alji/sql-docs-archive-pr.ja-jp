---
title: 利益チャート (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- profit chart
- mining models, charting
- mining models, testing
ms.assetid: 5c902543-4da9-4db3-99d5-4ce04c43d7ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 030e511047b816543c12c81bdab307e599bbc5d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641260"
---
# <a name="profit-chart-sql-server-data-mining-add-ins"></a><span data-ttu-id="65d4d-102">利益チャート (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="65d4d-102">Profit Chart (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="65d4d-103">![[データ マイニング] リボンの [利益チャート] ボタン](media/dmc-profitchart.gif "[データ マイニング] リボンの [利益チャート] ボタン")</span><span class="sxs-lookup"><span data-stu-id="65d4d-103">![Profit Chart button in Data Mining ribbon](media/dmc-profitchart.gif "Profit Chart button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="65d4d-104">利益チャートでは、マイニング モデルの使用に関連して予測される利益増加分を表示することによって、ビジネス シナリオに応じてどの顧客にコンタクトするべきかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-104">A profit chart displays the estimated profit increase that is associated with using a mining model to determine which customers a company should contact in a business scenario.</span></span> <span data-ttu-id="65d4d-105">このチャートの Y 軸は利益を、X 軸はコンタクトした母集団の割合を示します。</span><span class="sxs-lookup"><span data-stu-id="65d4d-105">The Y-axis of the chart represents the profit, while the X-axis represents the percentage of the population that the company contacted.</span></span> <span data-ttu-id="65d4d-106">一般的に、利益チャートでは、ある時点まで利益の増加が見られますが、その時点以降では、コンタクトする顧客数が増加するにつれて利益は減少します。</span><span class="sxs-lookup"><span data-stu-id="65d4d-106">A typical profit chart shows an increase in profits up to a point, after which profits decrease as more of the population is contacted.</span></span>  
  
## <a name="configuring-the-profit-chart"></a><span data-ttu-id="65d4d-107">利益チャートの構成</span><span class="sxs-lookup"><span data-stu-id="65d4d-107">Configuring the Profit Chart</span></span>  
 <span data-ttu-id="65d4d-108">精度チャートでは予測が正しいか誤りであるかの確率のみが評価されますが、利益チャートには予測に応じて実行されたアクションの結果に関する実際の情報が組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-108">Whereas the accuracy chart assesses only the probability that predictions are right or wrong, the profit chart incorporates real-world knowledge about the consequences of taking action on a prediction.</span></span> <span data-ttu-id="65d4d-109">これは、ウィザードの実行中に指定する次の要因を考慮することにより実現されます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-109">This is achieved by taking into account the following factors, which you specify when you run the wizard:</span></span>  
  
-   <span data-ttu-id="65d4d-110">**作成**</span><span class="sxs-lookup"><span data-stu-id="65d4d-110">**Population**</span></span>  
  
     <span data-ttu-id="65d4d-111">リフト チャートを作成するために使用されるデータセット内のケース数。</span><span class="sxs-lookup"><span data-stu-id="65d4d-111">The number of cases in the dataset that is being used to create the lift chart.</span></span> <span data-ttu-id="65d4d-112">たとえば、潜在顧客の数などです。</span><span class="sxs-lookup"><span data-stu-id="65d4d-112">For example, the number of potential customers.</span></span>  
  
-   <span data-ttu-id="65d4d-113">**固定コスト**</span><span class="sxs-lookup"><span data-stu-id="65d4d-113">**Fixed Cost**</span></span>  
  
     <span data-ttu-id="65d4d-114">そのビジネス問題に関連する固定コスト。</span><span class="sxs-lookup"><span data-stu-id="65d4d-114">The fixed cost that is associated with the business problem.</span></span> <span data-ttu-id="65d4d-115">たとえば、対象顧客に販促メールを送付する場合は、かけた電話の回数、販促メールの送付数といった変動要因に左右されないコストが固定コストになります。</span><span class="sxs-lookup"><span data-stu-id="65d4d-115">If this were for a targeted mailing solution, the cost would not depend on variables such as the number of telephone calls made or the number of promotional mailings sent.</span></span>  
  
-   <span data-ttu-id="65d4d-116">**個別コスト**</span><span class="sxs-lookup"><span data-stu-id="65d4d-116">**Individual Cost**</span></span>  
  
     <span data-ttu-id="65d4d-117">固定コスト以外に追加されるコストで、各顧客へのコンタクトに関連するコストです。</span><span class="sxs-lookup"><span data-stu-id="65d4d-117">Costs that are in addition to the fixed cost, that can be associated with each customer contact.</span></span> <span data-ttu-id="65d4d-118">たとえば、販促用メール送付や電話などです。</span><span class="sxs-lookup"><span data-stu-id="65d4d-118">For example, promotional mailings or telephone calls.</span></span>  
  
-   <span data-ttu-id="65d4d-119">**個人ごとの収益**</span><span class="sxs-lookup"><span data-stu-id="65d4d-119">**Revenue Per Individual**</span></span>  
  
     <span data-ttu-id="65d4d-120">成功した各販売に関連する収益です。</span><span class="sxs-lookup"><span data-stu-id="65d4d-120">The amount of revenue that is associated with each successful sale.</span></span>  
  
## <a name="using-the-profit-chart-wizard"></a><span data-ttu-id="65d4d-121">利益チャート ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="65d4d-121">Using the Profit Chart Wizard</span></span>  
 <span data-ttu-id="65d4d-122">利益チャートを作成するには、既存のデータ マイニング モデルを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65d4d-122">To create a profit chart, you must reference an existing data mining model.</span></span> <span data-ttu-id="65d4d-123">[モデルの**管理**] または [**参照**] をクリックして、使用されたアルゴリズムとマイニングモデルの列の詳細を表示すると、モデルを参照して、データに一致するモデルを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-123">You can browse models to find a model that matches your data by clicking **Manage Models** or **Browse** to see details about the algorithm that was used and the columns in the mining model.</span></span>  
  
 <span data-ttu-id="65d4d-124">詳細については、「 [Excel でのモデルの参照 &#40;SQL Server データ&#41;マイニング](browsing-models-in-excel-sql-server-data-mining-add-ins.md)アドイン」を参照してください。 SQL Server[データマイニングアドイン&#41;&#40;、モデルの管理と管理](manage-models-sql-server-data-mining-add-ins.md)を行います。</span><span class="sxs-lookup"><span data-stu-id="65d4d-124">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) and [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md).</span></span>  
  
#### <a name="to-create-a-profit-chart"></a><span data-ttu-id="65d4d-125">利益チャートを作成するには</span><span class="sxs-lookup"><span data-stu-id="65d4d-125">To create a profit chart</span></span>  
  
1.  <span data-ttu-id="65d4d-126">既存のモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="65d4d-126">Select an existing model.</span></span>  
  
2.  <span data-ttu-id="65d4d-127">予測の対象となる列とターゲット値 (必要な場合) を指定します。</span><span class="sxs-lookup"><span data-stu-id="65d4d-127">Specify the column that you want to predict, and a target value, if appropriate.</span></span>  
  
3.  <span data-ttu-id="65d4d-128">ソース データ (予測を作成するためにモデルに渡すデータ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="65d4d-128">Select the source data, which means the data you will pass through the model in order to create a prediction.</span></span> <span data-ttu-id="65d4d-129">モデルの作成に使用したデータとは異なるデータを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65d4d-129">This should not be the same data that you used to create the model.</span></span>  
  
4.  <span data-ttu-id="65d4d-130">新しい (ソース) データの列と、データ マイニング モデルに使用された列とをマッピングします。</span><span class="sxs-lookup"><span data-stu-id="65d4d-130">Map the columns in the new (source) date to the columns used in the data mining model.</span></span> <span data-ttu-id="65d4d-131">列名が似ている場合、ウィザードによって自動的にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-131">If the column names are similar, the wizard will automatically map them.</span></span>  
  
5.  <span data-ttu-id="65d4d-132">ウィザードに従って、コスト情報 (固定コスト、変動コスト、母集団、および予測される収益) を入力します。</span><span class="sxs-lookup"><span data-stu-id="65d4d-132">Enter the cost information required by the wizard: the fixed cost, individual cost, the population, and the revenue expected.</span></span>  
  
6.  <span data-ttu-id="65d4d-133">必要に応じて、段階的な一連のコストを入力できます (参照ボタン ([. **..])** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65d4d-133">Optionally, you can enter a graduated series of costs (click the browse **(...)** button).</span></span> <span data-ttu-id="65d4d-134">たとえば、メール送付は送付数が増えるほどコストが安くなるため、送付数に対応する別々のコストを入力でき、ウィザードによってサンプルのサイズに合わせてコストが調整されます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-134">For example, a mailing might become cheaper as you increase the number of items that are sent, so you can enter a different cost depending on the number of items, and the wizard will automatically adjust the costs for each sample size.</span></span>  
  
7.  <span data-ttu-id="65d4d-135">ウィザードによって、モデルのコストとメリットに関する分析のチャートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-135">The wizard creates a chart that includes the cost-benefit analysis for the model.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="65d4d-136">必要条件</span><span class="sxs-lookup"><span data-stu-id="65d4d-136">Requirements</span></span>  
 <span data-ttu-id="65d4d-137">不連続な数値を予測する場合は、予測する正確なターゲット値を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65d4d-137">If you are predicting a discrete numeric value, you must select the exact target value to predict.</span></span>  
  
## <a name="understanding-the-profit-chart"></a><span data-ttu-id="65d4d-138">利益チャートについて</span><span class="sxs-lookup"><span data-stu-id="65d4d-138">Understanding the Profit Chart</span></span>  
 <span data-ttu-id="65d4d-139">利益チャートには、チャート内の任意の場所をクリックすると移動する灰色の垂直線が描かれています。</span><span class="sxs-lookup"><span data-stu-id="65d4d-139">The profit chart contains a gray vertical line, which you can move by clicking a location in the chart.</span></span> <span data-ttu-id="65d4d-140">[**マイニング凡例**] には、スコア、母集団の適正、およびグラフの灰色の線の位置に関連付けられている予測確率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-140">The **Mining Legend** displays a score, the population correct, and the predict probability that are associated with the location of the gray line on the chart.</span></span> <span data-ttu-id="65d4d-141">灰色の線を使用してチャート内の利益の最大点を選択すると、予測確率値を使用して顧客へのコンタクト用の確率しきい値を判定できます。</span><span class="sxs-lookup"><span data-stu-id="65d4d-141">If you select the maximum point of profits in the chart by using the gray line, you can use the predict probability value to determine a probability threshold for contacting a customer.</span></span>  
  
 <span data-ttu-id="65d4d-142">たとえば、利益曲線の最大点が母集団の 55% の位置にあり、関連する予測確率が 20% の場合は、最大の利益を得るために、20% 以上の応答が得られると予測される顧客数のみにコンタクトすればよいことがわかります。</span><span class="sxs-lookup"><span data-stu-id="65d4d-142">For example, if the peak of the profit curve is at 55 percent of the population and the associated predict probability is 20 percent, this indicates that to achieve maximum profits you should only contact those customers whose response is predicted with a 20 percent or greater probability.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d4d-143">参照</span><span class="sxs-lookup"><span data-stu-id="65d4d-143">See Also</span></span>  
 [<span data-ttu-id="65d4d-144">Excel 用データマイニングアドインのモデルを検証し、モデルを使用して予測 &#40;する&#41;</span><span class="sxs-lookup"><span data-stu-id="65d4d-144">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
