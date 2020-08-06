---
title: 精度チャート (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- mining models, validating
- mining models, charting
- lift chart
- mining models, testing
- lift [data mining]
ms.assetid: 303973b4-71c0-4cfc-b7bc-92218b52509d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 45ca5b4d3944948b257b5fa063ebce5583701157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632809"
---
# <a name="accuracy-chart-sql-server-data-mining-add-ins"></a><span data-ttu-id="2a10f-102">精度チャート (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="2a10f-102">Accuracy Chart (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="2a10f-103">![[データ マイニング] リボンの [精度チャート] ボタン](media/dmc-accchart.gif "[データ マイニング] リボンの [精度チャート] ボタン")</span><span class="sxs-lookup"><span data-stu-id="2a10f-103">![Accuracy Chart button in Data Mining ribbon](media/dmc-accchart.gif "Accuracy Chart button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="2a10f-104">精度チャートでは、新しいデータ セットにモデルを適用し、そのモデルの精度を評価できます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-104">An accuracy chart enables you to apply a model to a new set of data and then evaluate how well the model performs.</span></span> <span data-ttu-id="2a10f-105">このウィザードによって作成される精度チャートは*リフトチャート*です。これは、データマイニングモデルの精度を測定するために頻繁に使用されるグラフの一種です。</span><span class="sxs-lookup"><span data-stu-id="2a10f-105">The accuracy chart created by this wizard is a *lift chart*, which is a type of chart that is frequently used to measure the accuracy of a data mining model.</span></span> <span data-ttu-id="2a10f-106">このタイプの精度チャートには、ランダムな予測と理想的な予測 (100% 正確な予測) を基準とし、それらと比べた場合に特定のデータ マイニング モデルを使用することによって、どの程度の改善を見込めるかがグラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-106">This type of accuracy chart displays a graphical representation of the improvement that you obtain from using the specified data mining model, as compared to random predictions, and to the ideal case where 100 percent of predictions are accurate.</span></span> <span data-ttu-id="2a10f-107">1 つのチャートで複数のモデルを比較できます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-107">You can compare multiple models within a single chart.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a10f-108">例</span><span class="sxs-lookup"><span data-stu-id="2a10f-108">Example</span></span>  
 <span data-ttu-id="2a10f-109">Adventure Works Cycles 社のマーケティング部門がターゲット メーリング キャンペーンの導入を検討しています。</span><span class="sxs-lookup"><span data-stu-id="2a10f-109">Consider the case in which the Marketing department at Adventure Works Cycles wants to create a targeted mailing campaign.</span></span> <span data-ttu-id="2a10f-110">これまでのキャンペーンの結果から、反応率は 10% 程度であることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="2a10f-110">From past campaigns, they know that a 10 percent response rate is typical.</span></span> <span data-ttu-id="2a10f-111">データベースのテーブルには、10,000 人の潜在顧客のリストが保存されています。</span><span class="sxs-lookup"><span data-stu-id="2a10f-111">They have a list of 10,000 potential customers stored in a table in the database.</span></span> <span data-ttu-id="2a10f-112">一般的な反応率が 10% なので、このうち 1,000 人の顧客から何らかの反応があると予測できます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-112">Based on the typical response rate, they can expect 1,000 customers to respond.</span></span>  
  
 <span data-ttu-id="2a10f-113">しかし、今回は予算の都合上、広告を郵送できる顧客が 5,000 人に限られています。そこで、同社のマーケティング部門では、マイニング モデルを使用して、最も効果が期待できる 5,000 人の顧客を抽出することにしました。</span><span class="sxs-lookup"><span data-stu-id="2a10f-113">However, because they can afford to mail an advertisement to only 5,000 customers, the Marketing department uses a mining model to target the 5,000 customers who are most likely to respond.</span></span>  
  
 <span data-ttu-id="2a10f-114">5,000 人の顧客をランダムに選択した場合は、500 件の反応しか期待できません。これは、一般にターゲットとされた顧客の 10% しか反応しないためです。</span><span class="sxs-lookup"><span data-stu-id="2a10f-114">If the company randomly selects 5,000 customers, they can expect to receive only 500 positive responses, because only 10 percent of those who are targeted typically respond.</span></span> <span data-ttu-id="2a10f-115">このシナリオは、リフト チャートのランダム線によって示されています。</span><span class="sxs-lookup"><span data-stu-id="2a10f-115">This scenario is what the random line in the lift chart represents.</span></span>  
  
 <span data-ttu-id="2a10f-116">マイニング モデルを使って対象顧客を絞り込んだ場合はどうでしょうか。このモデルの予測が 100% 正確であると仮定した場合、このモデルが提示する 1,000 人の潜在顧客に広告を郵送すれば、1,000 件の反応を得られることになります。</span><span class="sxs-lookup"><span data-stu-id="2a10f-116">However, if the Marketing department uses a mining model to target their mailing, and if the model were perfect, the company could expect to receive 1,000 responses by mailing an advertisement to the 1,000 potential customers recommended by the model.</span></span> <span data-ttu-id="2a10f-117">このシナリオは、リフト チャートの理想線によって示されています。</span><span class="sxs-lookup"><span data-stu-id="2a10f-117">This scenario is represented by the ideal line in the lift chart.</span></span>  
  
## <a name="using-the-accuracy-chart-wizard"></a><span data-ttu-id="2a10f-118">精度チャート ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="2a10f-118">Using the Accuracy Chart Wizard</span></span>  
 <span data-ttu-id="2a10f-119">精度チャートを作成するには、既存のデータ マイニング構造を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a10f-119">To create an accuracy chart, you must reference an existing data mining structure.</span></span> <span data-ttu-id="2a10f-120">モデルの予測対象が同じであれば、この構造に基づく複数のモデルの精度を測定できます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-120">You can measure the accuracy of multiple models that are based on that structure, as long as they predict the same thing.</span></span>  
  
 <span data-ttu-id="2a10f-121">使用可能な構造がわからない場合は、サーバーを参照できます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-121">If you are not sure which structures are available, you can browse the server.</span></span> <span data-ttu-id="2a10f-122">詳細については、「 [Excel でのモデルの参照 &#40;SQL Server データマイニングアドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a10f-122">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>  
  
#### <a name="to-create-an-accuracy-chart"></a><span data-ttu-id="2a10f-123">精度チャートを作成するには</span><span class="sxs-lookup"><span data-stu-id="2a10f-123">To create an accuracy chart</span></span>  
  
1.  <span data-ttu-id="2a10f-124">[**データマイニングクライアント**] リボンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a10f-124">Click the **Data Mining Client** ribbon.</span></span>  
  
2.  <span data-ttu-id="2a10f-125">[**精度と検証**] グループで、[**精度チャート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a10f-125">In the **Accuracy and Validation** group, click **Accuracy Chart**.</span></span>  
  
3.  <span data-ttu-id="2a10f-126">**[構造またはモデルの選択**] ダイアログボックスで、評価するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a10f-126">In the **Select Structure or Model** dialog box, choose the model that you want to evaluate.</span></span> <span data-ttu-id="2a10f-127">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a10f-127">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a10f-128">テスト対象のデータに最も適合するモデルを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a10f-128">You must choose a model that closely matches the data you intend to test.</span></span>  
  
4.  <span data-ttu-id="2a10f-129">[予測**する列と予測する値の指定**] ダイアログボックスで、予測する列を選択し、必要に応じて対象の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a10f-129">In the **Specify Column to Predict and Value to Predict** dialog box, choose the column that you want to predict, and a target value, if appropriate.</span></span> <span data-ttu-id="2a10f-130">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a10f-130">Click **Next**.</span></span>  
  
     <span data-ttu-id="2a10f-131">たとえば、上の例では、顧客の反応をモデル化した列を選択し、ターゲット値として "Probably Will Buy" を指定します。</span><span class="sxs-lookup"><span data-stu-id="2a10f-131">For example, in the example above, you might choose the column that models the customer response, and specify the target value as "Probably Will Buy".</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a10f-132">連続値を予測することはできません。</span><span class="sxs-lookup"><span data-stu-id="2a10f-132">You cannot predict a continuous value.</span></span> <span data-ttu-id="2a10f-133">ただし、値を不連続な範囲に分割することで、列を離散化することができます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-133">However, you can discretize the column by separating the values into discrete ranges.</span></span> <span data-ttu-id="2a10f-134">この操作はデータ マイニング モデルを作成する前に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a10f-134">You must do this before creating the data mining model.</span></span>  
  
5.  <span data-ttu-id="2a10f-135">**[ソースデータの選択**] ダイアログボックスで、予測を作成するためにモデルを通過するデータのソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a10f-135">In the **Select Source Data** dialog box, specify the source of the data that you will pass through the model in order to create a prediction.</span></span>  
  
6.  <span data-ttu-id="2a10f-136">モデルと共に格納されているテストデータではなく、データの外部ソースを使用している場合は、[**リレーションシップの指定**] ダイアログボックスで、新しいソースデータの列をデータマイニングモデルで使用されている列にマップします。</span><span class="sxs-lookup"><span data-stu-id="2a10f-136">If you are using an external source of data, and not the test data that is stored with the model, in the **Specify Relationships** dialog box, map the columns in the new source data to the columns used in the data mining model.</span></span>  
  
     <span data-ttu-id="2a10f-137">列名が似ている場合、ウィザードによって自動的にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-137">If the column names are similar, the wizard will automatically map them.</span></span> <span data-ttu-id="2a10f-138">入力データ内の列には、分析に無関係で無視できる列と、データ マイニング モデルで入力を処理するために必要な列があります。</span><span class="sxs-lookup"><span data-stu-id="2a10f-138">Although some columns in your input data may be irrelevant to analysis and can be ignored, some columns are required for the data mining model to process the input.</span></span> <span data-ttu-id="2a10f-139">このような列には、トランザクション ID、ターゲット値、または予測に使用される列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-139">Such columns might include a transaction ID, the target value, or columns used for prediction.</span></span> <span data-ttu-id="2a10f-140">必要な列を割り当てなかった場合は、ウィザードに警告メッセージが示されます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-140">If you fail to map a column that is required, the wizard will provide a warning message.</span></span>  
  
7.  <span data-ttu-id="2a10f-141">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a10f-141">Click **Finish**.</span></span>  
  
     <span data-ttu-id="2a10f-142">ウィザードにより、リフト チャートおよび基になるデータを含んだレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-142">The wizard creates a report that includes the lift chart and underlying data.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="2a10f-143">必要条件</span><span class="sxs-lookup"><span data-stu-id="2a10f-143">Requirements</span></span>  
 <span data-ttu-id="2a10f-144">不連続の値を予測する場合は、予測対象のターゲット値を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a10f-144">If you are predicting a discrete value, you must select the target value that you want to predict.</span></span> <span data-ttu-id="2a10f-145">たとえば、"Yes: Buy" という反応が 1 で、"No: Do Not Buy" という反応が 2 のようにデータが分類されている場合は、予測値として 1 または 2 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a10f-145">For example, if your data is categorized with a response "Yes: Buy" as 1 and the response "No: Do Not Buy" as 2, you must specify either 1 or 2 as the prediction values.</span></span> <span data-ttu-id="2a10f-146">これに対し、特定の範囲の値を予測する場合、一度に比較できる値は 2 つまでです。</span><span class="sxs-lookup"><span data-stu-id="2a10f-146">However, if you want to predict a range of values, you can compare only two values at a time.</span></span> <span data-ttu-id="2a10f-147">たとえば、5 以上のスコアを予測する場合は、ソース データを再定義し、結果を 5 以上と 5 未満という 2 つのグループに分類する新しいモデルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a10f-147">For example, if you want to predict a score above 5, you might have to relabel your source data and create a new model that separates the results into two sets: those greater than 5 and those less than 5.</span></span> <span data-ttu-id="2a10f-148">その上で、この 2 つのグループの精度を比較できます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-148">You can then compare the accuracy of those two groups.</span></span>  
  
## <a name="understanding-accuracy"></a><span data-ttu-id="2a10f-149">精度について</span><span class="sxs-lookup"><span data-stu-id="2a10f-149">Understanding Accuracy</span></span>  
 <span data-ttu-id="2a10f-150">作成できるチャートは 2 種類あります。1 つは予測可能な列の状態を指定するチャート、もう 1 つは状態を指定しないチャートです。</span><span class="sxs-lookup"><span data-stu-id="2a10f-150">You can create two types of charts, one in which you specify a state of the predictable column, and one in which you do not specify the state.</span></span>  
  
 <span data-ttu-id="2a10f-151">予測可能な列の状態を指定する場合、チャートの X 軸は、予測を比較するために使用されるテスト データ セットの割合を示します。</span><span class="sxs-lookup"><span data-stu-id="2a10f-151">If you specify the state of the predictable column, the x-axis of the chart represents the percentage of the test dataset that is used to compare the predictions.</span></span> <span data-ttu-id="2a10f-152">チャートの Y 軸は、指定された状態になると予測される値の割合を示します。</span><span class="sxs-lookup"><span data-stu-id="2a10f-152">The y-axis of the chart represents the percentage of values that are predicted to be the specified state.</span></span>  
  
 <span data-ttu-id="2a10f-153">予測可能な列の状態を指定しない場合は、想定されるすべての予測に対するモデルの精度がチャートに示されます。</span><span class="sxs-lookup"><span data-stu-id="2a10f-153">If you do not specify the state of the predictable column, the chart shows the accuracy of the model for all possible predictions.</span></span>  
  
 <span data-ttu-id="2a10f-154">リフト チャートの機能、およびランダム予測線と理想予測線に基づく精度の計算方法については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックの「リフト チャート」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a10f-154">For more information about how a lift chart works, and how accuracy is calculated based on the random and ideal prediction lines, see the topic "Lift Chart" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a10f-155">参照</span><span class="sxs-lookup"><span data-stu-id="2a10f-155">See Also</span></span>  
 [<span data-ttu-id="2a10f-156">Excel 用データマイニングアドインのモデルを検証し、モデルを使用して予測 &#40;する&#41;</span><span class="sxs-lookup"><span data-stu-id="2a10f-156">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
