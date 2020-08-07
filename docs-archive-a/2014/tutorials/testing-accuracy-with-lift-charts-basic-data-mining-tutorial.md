---
title: リフトチャートを使用した精度のテスト (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a3dcdd1d1b78911f5ffd37a383532abdd4814c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718992"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a><span data-ttu-id="259d5-102">リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="259d5-102">Testing Accuracy with Lift Charts (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="259d5-103">データマイニングデザイナーの [**マイニング精度チャート**] タブでは、各モデルがどの程度予測されるかを計算し、各モデルの結果を他のモデルの結果と比較して直接比較することができます。</span><span class="sxs-lookup"><span data-stu-id="259d5-103">On the **Mining Accuracy Chart** tab of Data Mining Designer, you can calculate how well each of your models makes predictions, and compare the results of each model directly against the results of the other models.</span></span> <span data-ttu-id="259d5-104">この比較方法を*リフトチャート*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="259d5-104">This method of comparison is referred to as a *lift chart*.</span></span> <span data-ttu-id="259d5-105">通常、マイニング モデルの予測精度は、リフトまたは分類の精度によって測定します。</span><span class="sxs-lookup"><span data-stu-id="259d5-105">Typically, the predictive accuracy of a mining model is measured by either lift or classification accuracy.</span></span> <span data-ttu-id="259d5-106">このチュートリアルでは、リフト チャートのみを使用します。</span><span class="sxs-lookup"><span data-stu-id="259d5-106">For this tutorial we will use the lift chart only.</span></span>  
  
 <span data-ttu-id="259d5-107">このトピックでは次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="259d5-107">In this topic, you will perform the following tasks:</span></span>  
  
-   [<span data-ttu-id="259d5-108">入力データの選択</span><span class="sxs-lookup"><span data-stu-id="259d5-108">Choose the Input Data</span></span>](#BKMK_InputData)  
  
-   [<span data-ttu-id="259d5-109">精度チャートのパラメーターの構成</span><span class="sxs-lookup"><span data-stu-id="259d5-109">Configure Accuracy Chart Parameters</span></span>](#BKMK_Selecting)  
  
##  <a name="choosing-the-input-data"></a><a name="BKMK_InputData"></a><span data-ttu-id="259d5-110">入力データの選択</span><span class="sxs-lookup"><span data-stu-id="259d5-110">Choosing the Input Data</span></span>  
 <span data-ttu-id="259d5-111">マイニング モデルの精度をテストするには、まず、テストに使用するデータ ソースを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="259d5-111">The first step in testing the accuracy of your mining models is to select the data source that you will use for testing.</span></span> <span data-ttu-id="259d5-112">テスト データに対するモデルの予測精度をテストし、その後で外部データに対してモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="259d5-112">You will test how well the models perform against your testing data and then you will use them with external data.</span></span>  
  
#### <a name="to-select-the-data-set"></a><span data-ttu-id="259d5-113">データ セットを選択するには</span><span class="sxs-lookup"><span data-stu-id="259d5-113">To select the data set</span></span>  
  
1.  <span data-ttu-id="259d5-114">のデータマイニングデザイナーの [**マイニング精度チャート**] タブに切り替え [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] て、[**入力の選択**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="259d5-114">Switch to the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and select the **Input Selection** tab.</span></span>  
  
2.  <span data-ttu-id="259d5-115">[**精度チャートに使用するデータセットの選択**] グループボックスで、[**マイニング構造のテストケースを使用**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="259d5-115">In the **Select data set to be used for Accuracy Chart** group box, select **Use mining structure test cases**.</span></span> <span data-ttu-id="259d5-116">これは、マイニング構造を作成したときに確保したテスト データです。</span><span class="sxs-lookup"><span data-stu-id="259d5-116">This is the testing data that you set aside when you created the mining structure.</span></span>  
  
     <span data-ttu-id="259d5-117">その他のオプションの詳細については、「[精度チャートの種類の選択」および「グラフのオプションの設定](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="259d5-117">For more information on the other options, see [Choose an Accuracy Chart Type and Set Chart Options](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
##  <a name="setting-accuracy-chart-parameters"></a><a name="BKMK_Selecting"></a><span data-ttu-id="259d5-118">精度チャートのパラメーターの設定</span><span class="sxs-lookup"><span data-stu-id="259d5-118">Setting Accuracy Chart Parameters</span></span>  
 <span data-ttu-id="259d5-119">精度チャートを作成するには、次の 3 つの事項を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="259d5-119">To create an accuracy chart, you must define three things:</span></span>  
  
-   <span data-ttu-id="259d5-120">どのモデルを精度チャートに含めますか。</span><span class="sxs-lookup"><span data-stu-id="259d5-120">Which models should you include in the accuracy chart?</span></span>  
  
-   <span data-ttu-id="259d5-121">予測可能な、どの属性を測定しますか。</span><span class="sxs-lookup"><span data-stu-id="259d5-121">Which predictable attribute do you want to measure?</span></span> <span data-ttu-id="259d5-122">特定のモデルには複数の対象が存在しますが、各グラフで測定できるのは一度に 1 つの結果のみです。</span><span class="sxs-lookup"><span data-stu-id="259d5-122">Some models might have multiple targets, but each chart can measure only one outcome at a time.</span></span>  
  
     <span data-ttu-id="259d5-123">精度チャートで**予測可能列の名前**として列を使用するには、列の使用法の種類がまたはである必要があり `Predict` `Predict Only` ます。</span><span class="sxs-lookup"><span data-stu-id="259d5-123">To use a column as the **Predictable Column Name** in an accuracy chart, the columns must have the usage type of `Predict` or `Predict Only`.</span></span> <span data-ttu-id="259d5-124">また、対象列のコンテンツの種類は、`Discrete` と `Discretized` のどちらかであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="259d5-124">Also, the content type of the target column must be either `Discrete` or `Discretized`.</span></span> <span data-ttu-id="259d5-125">つまり、リフト チャートを使用して、連続する数値の出力に関する精度を測定することはできません。</span><span class="sxs-lookup"><span data-stu-id="259d5-125">In other words, you cannot measure accuracy against continuous numeric outputs using the lift chart.</span></span>  
  
-   <span data-ttu-id="259d5-126">モデルの一般精度、または特定の値を予測する精度 ([自転車購入者] = ' Yes ' など) を測定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="259d5-126">Do you want to measure the model's general accuracy, or its accuracy  in predicting a particular value (such as [Bike Buyer] = 'Yes')</span></span>  
  
#### <a name="to-generate-the-lift-chart"></a><span data-ttu-id="259d5-127">リフト チャートを生成するには</span><span class="sxs-lookup"><span data-stu-id="259d5-127">To generate the lift chart</span></span>  
  
1.  <span data-ttu-id="259d5-128">データマイニングデザイナーの [**入力の選択**] タブの [**リフトチャートに表示する予測可能なマイニングモデル列の選択**] で、[**予測列と値の同期**] のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="259d5-128">On the **Input Selection** tab of Data Mining Designer, under **Select predictable mining model columns to show in the lift chart**, select the checkbox for **Synchronize Prediction Columns and Values**.</span></span>  
  
2.  <span data-ttu-id="259d5-129">[**予測可能列の名前**] 列で、各モデルに対して [**自転車購入**者] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="259d5-129">In the **Predictable Column Name** column, verify that **Bike Buyer** is selected for each model.</span></span>  
  
3.  <span data-ttu-id="259d5-130">[**表示]** 列で、各モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="259d5-130">In the **Show** column, select each of the models.</span></span>  
  
     <span data-ttu-id="259d5-131">既定では、マイニング構造内のすべてのモデルが選択されます。</span><span class="sxs-lookup"><span data-stu-id="259d5-131">By default, all the models in the mining structure are selected.</span></span> <span data-ttu-id="259d5-132">モデルを除外することもできますが、このチュートリアルではすべてのモデルを選択したままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="259d5-132">You can decide not to include a model, but for this tutorial leave all the models selected.</span></span>  
  
4.  <span data-ttu-id="259d5-133">[**予測値**] 列で**1**を選択します。</span><span class="sxs-lookup"><span data-stu-id="259d5-133">In the **Predict Value** column, select **1**.</span></span> <span data-ttu-id="259d5-134">同じ予測可能列を持つモデルのそれぞれに対して、同じ値が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="259d5-134">The same value is automatically filled in for each model that has the same predictable column.</span></span>  
  
5.  <span data-ttu-id="259d5-135">[**リフトチャート**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="259d5-135">Select the **Lift Chart** tab.</span></span>  
  
     <span data-ttu-id="259d5-136">このタブをクリックすると、予測クエリが実行されてテスト データに関する予測結果が取得され、結果は既知の値と比較されます。</span><span class="sxs-lookup"><span data-stu-id="259d5-136">When you click the tab, a prediction query is executed to get predictions for the test data, and the results are compared against the known values.</span></span> <span data-ttu-id="259d5-137">結果がグラフとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="259d5-137">The results are plotted on the graph.</span></span>  
  
     <span data-ttu-id="259d5-138">[**予測値**] オプションを使用して特定のターゲットの結果を指定した場合、リフトチャートはランダムな推測の結果と理想的なモデルの結果をプロットします。</span><span class="sxs-lookup"><span data-stu-id="259d5-138">If you specified a particular target outcome using the **Predict Value** option, the lift chart plots the results of random guesses and the results of an ideal model.</span></span>  
  
    -   <span data-ttu-id="259d5-139">ランダム推定の線では、何もデータを使用せずに予測を行う場合に、モデルがどれほどの精度であるかが示されます。つまり、2 つの結果のいずれかを予測する場合は、50 対 50 の分割が行われます。</span><span class="sxs-lookup"><span data-stu-id="259d5-139">The random guess line shows how accurate the model would be without using any data to inform its predictions: that is, a 50-50 split between two outcomes.</span></span> <span data-ttu-id="259d5-140">リフト チャートを使用すると、ランダム推定と比較してモデルがどれほど改善された予測を行うかが視覚的に表現されます。</span><span class="sxs-lookup"><span data-stu-id="259d5-140">The lift chart helps you visualize how much better your model performs in comparison to a random guess.</span></span>  
  
    -   <span data-ttu-id="259d5-141">理想的なモデルの線は、精度の上限を表します。</span><span class="sxs-lookup"><span data-stu-id="259d5-141">The ideal model line represents the upper bound of accuracy.</span></span> <span data-ttu-id="259d5-142">これは、モデルが常にできるだけ高い精度で予測を行う場合に達成できる、実現可能な最大の成果を示しています。</span><span class="sxs-lookup"><span data-stu-id="259d5-142">It shows you the maximum possible benefit you could achieve if your model always predicted accurately.</span></span>  
  
     <span data-ttu-id="259d5-143">作成したマイニング モデルは通常、これら 2 つの極値の間に位置します。</span><span class="sxs-lookup"><span data-stu-id="259d5-143">The mining models you created will usually fall between these two extremes.</span></span> <span data-ttu-id="259d5-144">ランダムな推測による改善は、*リフト*と見なされます。</span><span class="sxs-lookup"><span data-stu-id="259d5-144">Any improvement from the random guess is considered to be *lift*.</span></span>  
  
6.  <span data-ttu-id="259d5-145">凡例を使用して、理想モデルとランダム推測モデルを表す色付きの線を配置します。</span><span class="sxs-lookup"><span data-stu-id="259d5-145">Use the legend to locate the colored lines representing the Ideal Model and the Random Guess Model.</span></span>  
  
     <span data-ttu-id="259d5-146">このモデルでは、 `TM_Decision_Tree` クラスタリングモデルと Naive Bayes モデルの両方を実行することで、最大のリフトが得られることがわかります。</span><span class="sxs-lookup"><span data-stu-id="259d5-146">You'll notice that the `TM_Decision_Tree` model provides the greatest lift,  outperforming both the Clustering and Naive Bayes models.</span></span>  
  
 <span data-ttu-id="259d5-147">このレッスンで作成したものと似たリフトチャートの詳細については、「[リフトチャート &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="259d5-147">For an in-depth explanation of a lift chart similar to the one created in this lesson, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="259d5-148">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="259d5-148">Next Task in Lesson</span></span>  
 [<span data-ttu-id="259d5-149">フィルター選択されたモデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="259d5-149">Testing a Filtered Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="259d5-150">参照</span><span class="sxs-lookup"><span data-stu-id="259d5-150">See Also</span></span>  
 <span data-ttu-id="259d5-151">[リフトチャート &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="259d5-151">[Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="259d5-152">[[リフトチャート] タブ &#40;マイニング精度チャートビュー&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)</span><span class="sxs-lookup"><span data-stu-id="259d5-152">[Lift Chart Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)</span></span>  
  
  
