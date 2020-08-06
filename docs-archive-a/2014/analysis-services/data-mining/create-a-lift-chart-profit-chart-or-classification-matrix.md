---
title: リフトチャート、利益チャート、または分類マトリックスを作成します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], mining structures
ms.assetid: aa3d052f-58a9-4417-8e7a-5e6feb562af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 932138b37b36269bed86df42786bd5d684f75ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712653"
---
# <a name="create-a-lift-chart-profit-chart-or-classification-matrix"></a><span data-ttu-id="87ca0-102">リフト チャート、利益チャート、または分類マトリックスの作成</span><span class="sxs-lookup"><span data-stu-id="87ca0-102">Create a Lift Chart, Profit Chart, or Classification Matrix</span></span>
  <span data-ttu-id="87ca0-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ マイニング モデルの精度チャートを作成するには、次の 5 つの基本手順に従います。</span><span class="sxs-lookup"><span data-stu-id="87ca0-103">You can create an accuracy chart for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data mining model in five basic steps:</span></span>  
  
-   <span data-ttu-id="87ca0-104">比較するマイニング モデルが含まれているマイニング構造を選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-104">Select the mining structure that contains the mining models that you want to compare.</span></span>  
  
-   <span data-ttu-id="87ca0-105">グラフに追加するマイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-105">Select the mining models to add to the chart.</span></span>  
  
-   <span data-ttu-id="87ca0-106">グラフの生成に使用するテスト データのソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-106">Specify a source of testing data to use in generating the chart.</span></span>  
  
-   <span data-ttu-id="87ca0-107">グラフの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-107">Choose the chart type.</span></span>  
  
-   <span data-ttu-id="87ca0-108">グラフのオプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-108">Configure the chart options.</span></span>  
  
 <span data-ttu-id="87ca0-109">これらの基本手順は、リフト チャート、利益チャート、および分類マトリックスと同じです。</span><span class="sxs-lookup"><span data-stu-id="87ca0-109">These basic steps are the same for the lift chart, profit chart, and classification matrix.</span></span> <span data-ttu-id="87ca0-110">これらのグラフの種類の基本的なグラフ オプションを構成する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-110">The following procedures outline the steps to configure the basic chart options for these chart types.</span></span> <span data-ttu-id="87ca0-111">相互検証レポートの作成方法については、「 [相互検証レポートのメジャー](measures-in-the-cross-validation-report.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ca0-111">For information about how to create a cross-validation report, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
### <a name="open-the-mining-structure-in-the-accuracy-chart-designer"></a><span data-ttu-id="87ca0-112">マイニング構造を精度チャート デザイナーで開く</span><span class="sxs-lookup"><span data-stu-id="87ca0-112">Open the mining structure in the Accuracy Chart Designer</span></span>  
  
1.  <span data-ttu-id="87ca0-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でデータ マイニング デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-113">Open the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="87ca0-114">ソリューション エクスプローラーで、マイニング モデルを含む構造をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="87ca0-114">In Solution Explorer, double-click the structure that contains the mining model or models.</span></span>  
  
3.  <span data-ttu-id="87ca0-115">**[マイニング精度チャート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="87ca0-115">Click the **Mining Accuracy Chart** tab.</span></span>  
  
### <a name="select-mining-models-for-inclusion-in-the-chart"></a><span data-ttu-id="87ca0-116">グラフに含めるマイニング モデルの選択</span><span class="sxs-lookup"><span data-stu-id="87ca0-116">Select mining models for inclusion in the chart</span></span>  
  
1.  <span data-ttu-id="87ca0-117">**のデータ マイニング デザイナーの** [マイニング精度チャート] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、 **[入力の選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="87ca0-117">On the **Mining Accuracy Chart** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Input Selection** tab.</span></span>  
  
     <span data-ttu-id="87ca0-118">現在の構造内にある、予測可能な属性が同じであるモデルがすべて、一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-118">The list displays all models in the current structure that have the same predictable attribute.</span></span>  
  
2.  <span data-ttu-id="87ca0-119">グラフに含めるモデルごとに **[ボックスを表示する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="87ca0-119">Select the **Show box** for each model that you want to include in the chart.</span></span>  
  
3.  <span data-ttu-id="87ca0-120">**[予測可能列名]** ボックスをクリックし、一覧から予測可能列の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-120">Click the **Predictable Column Name** text box, and select the name of a predictable column from the list.</span></span> <span data-ttu-id="87ca0-121">1 つのグラフに含めるすべてのモデルで、同一の予測可能列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87ca0-121">All models that you put in one chart must have the same predictable column.</span></span>  
  
4.  <span data-ttu-id="87ca0-122">2 つのモデルを比較する場合に、予測可能列の値またはデータ型が異なるときは、 **[予測列と値の同期]** チェック ボックスをオフにすると、強制的に比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-122">If you compare two models and the predictable columns have different values or different data types, clear the **Synchonize prediction columns and values** box to force a comparison.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="87ca0-123">**[予測列と値の同期]** チェック ボックスをオンにした場合、モデルの予測可能列のデータとテスト データが Analysis Services によって分析され、最も合うものが検索されます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-123">If the **Synchonize prediction columns and values** box is selected, Analysis Services analyzes the data in the predictable columns of the model and the test data, and attempts to find the best match.</span></span> <span data-ttu-id="87ca0-124">したがって、強制的な列の比較がどうしても必要な場合にのみ、このチェック ボックスをオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="87ca0-124">Therefore, do not clear the box unless absolutely necessary to force a comparison of the columns.</span></span>  
  
5.  <span data-ttu-id="87ca0-125">**[予測値]** ボックスをクリックし、一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-125">Click the **Predict Value** text box, and select a value from the list.</span></span> <span data-ttu-id="87ca0-126">予測可能列のデータ型が連続値の場合は、このボックスに値を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87ca0-126">If the predictable column is a continuous data type, you must type a value in the text box.</span></span>  
  
     <span data-ttu-id="87ca0-127">詳細については、「 [マイニング モデルのテストに使用する列の選択](choose-the-column-to-use-for-testing-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ca0-127">For more information, see [Choose the Column to Use for Testing a Mining Model](choose-the-column-to-use-for-testing-a-mining-model.md).</span></span>  
  
### <a name="select-testing-data"></a><span data-ttu-id="87ca0-128">テスト データの選択</span><span class="sxs-lookup"><span data-stu-id="87ca0-128">Select testing data</span></span>  
  
1.  <span data-ttu-id="87ca0-129">**[マイニング精度チャート]** タブにある **[入力の選択]** タブで、 **[精度チャートに使用するデータセットの選択]** のいずれかのオプションを選択することによって、グラフの生成に使用するデータのソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-129">On the **Input Selection** tab of the **Mining Accuracy Chart** tab, specify the source of the data that you will use to generate the chart by selecting one of the options in the group, **Select data set to be used for accuracy chart**.</span></span>  
  
    -   <span data-ttu-id="87ca0-130">マイニング構造のテスト ケースとモデルの作成時に適用されたフィルターの積集合で定義されているケースのサブセットを使用する場合は、 **[マイニング モデルのテスト ケースを使用する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-130">Select the option, **Use Mining Model test cases**, if you want to use the subset of cases that is defined by the intersection of the mining structure test cases and any filters that may have been applied during model creation.</span></span>  
  
    -   <span data-ttu-id="87ca0-131">マイニング構造の予約データ セットの一部として定義されたテスト ケースの完全なセットを使用するには、 **[マイニング モデルのテスト ケースを使用する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-131">Select the option, **Use mining structure test cases**, to use the full set of testing cases that were defined as part of the mining structures holdout data set.</span></span>  
  
    -   <span data-ttu-id="87ca0-132">外部データを使用する場合は、 **[別のデータセットを指定する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-132">Select the option, **Specify a different data set**, if you want to use external data.</span></span>  <span data-ttu-id="87ca0-133">データ セットは、データ ソース ビューとして使用可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="87ca0-133">The data set must be available as a data source view.</span></span>   <span data-ttu-id="87ca0-134">参照ボタン ([.**..**]) をクリックして、精度チャートに使用するデータテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-134">Click the browse (**...**) button to choose the data tables to use for the accuracy chart.</span></span> <span data-ttu-id="87ca0-135">詳細については、「 [モデルのテスト データの選択およびマップ](choose-and-map-model-testing-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ca0-135">For more information, see [Choose and Map Model Testing Data](choose-and-map-model-testing-data.md).</span></span>  
  
         <span data-ttu-id="87ca0-136">外部データセットを使用する場合、必要に応じて入力データセットをフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-136">If you are using an external data set, you can optionally filter the input data set.</span></span> <span data-ttu-id="87ca0-137">詳細については、「 [モデルのテスト データへのフィルターの適用](apply-filters-to-model-testing-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ca0-137">For more information, see [Apply Filters to Model Testing Data](apply-filters-to-model-testing-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87ca0-138">[**入力の選択**] タブでは、モデルのテストケースまたはマイニング構造のテストケースに対してフィルターを作成することはできません。マイニングモデルにフィルターを作成するには、モデルの Filter プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-138">You cannot create a filter on the model test cases or the mining structure test cases on the **Input Selection** tab. To create a filter on the mining model, modify the Filter property of the model.</span></span> <span data-ttu-id="87ca0-139">詳細については、「 [マイニング モデルへのフィルターの適用](apply-a-filter-to-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ca0-139">For more information, see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
### <a name="configure-chart-settings-and-generate-the-chart"></a><span data-ttu-id="87ca0-140">グラフ設定の構成とグラフの生成</span><span class="sxs-lookup"><span data-stu-id="87ca0-140">Configure chart settings and generate the chart</span></span>  
  
1.  <span data-ttu-id="87ca0-141">**[マイニング精度チャート]** タブで、作成するグラフのタブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="87ca0-141">In the **Mining Accuracy Chart** tab, click the tab for the chart you want to create.</span></span>  
  
2.  <span data-ttu-id="87ca0-142">**リフトチャート**の場合は、[**リフトチャート**] タブをクリックします。グラフは、選択したモデル、予測可能な属性、および入力データに基づいて自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-142">For a **lift chart**, click the **Lift Chart** tab. The chart is automatically generated based on the model, predictable attributes, and input data that you just selected.</span></span>  
  
3.  <span data-ttu-id="87ca0-143">**分類マトリックス**の場合は、[**分類マトリックス**] タブをクリックします。これ以上の設定は必要ありません。選択した入力データおよびモデルに基づいて、グラフが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-143">For a **classification matrix**, click the **Classification Matrix** tab. No further settings are needed; the chart is automatically generated based on the input data and model that you selected.</span></span>  
  
4.  <span data-ttu-id="87ca0-144">**利益チャート**の場合は、最初に [**リフトチャート**] タブをクリックします。次に、[**グラフの種類**] ドロップダウンリストから [**利益チャート**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-144">For a **profit chart**, first click the **Lift Chart** tab. Then, from the **Chart type** drop-down list, select **Profit chart**.</span></span>  
  
     <span data-ttu-id="87ca0-145">**[利益チャートの設定]** ダイアログ ボックスで次の設定を入力します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-145">Enter the following settings in the **Profit Chart Settings** dialog box.</span></span>  
  
     <span data-ttu-id="87ca0-146">**作成**</span><span class="sxs-lookup"><span data-stu-id="87ca0-146">**Population**</span></span>  
     <span data-ttu-id="87ca0-147">リフト チャートを作成するときに使用するデータセット内のケースの数。</span><span class="sxs-lookup"><span data-stu-id="87ca0-147">The number of cases from the data set that you want to use when creating the lift chart.</span></span>  
  
     <span data-ttu-id="87ca0-148">モデルは常に確率が高い順にケースを選択します。したがって、潜在顧客を評価する際に顧客データベースのレコード数の半分に相当する数を選択すると、そのモデルに最適なケースのサブセットで精度が測定されます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-148">The model always chooses the cases in order of decreasing probability; that is, if you are assessing potential customers and you choose a number that represents only half the records in your customer database, the model will measure accuracy on the subset of cases that best fit your model.</span></span>  
  
     <span data-ttu-id="87ca0-149">これは、そのモデルを使用してダイレクトメールを生成したりキャンペーンを作成したりする際には、各ケースに関連付けられている予測確率を使用して、前向きな反応を示す確率が最も高い顧客のみに対象を絞り込むからです。</span><span class="sxs-lookup"><span data-stu-id="87ca0-149">This is because when you use the model to generate a mailing or create a campaign, you will use the prediction probability associated with each case to target only the customers who have the highest probability of making a positive response.</span></span>  
  
     <span data-ttu-id="87ca0-150">**固定コスト**</span><span class="sxs-lookup"><span data-stu-id="87ca0-150">**Fixed Cost**</span></span>  
     <span data-ttu-id="87ca0-151">そのビジネス問題に関連する固定コスト。</span><span class="sxs-lookup"><span data-stu-id="87ca0-151">The fixed cost that is associated with the business problem.</span></span>  
  
     <span data-ttu-id="87ca0-152">ターゲット メーリング ソリューションの例では、ダイレクトメールの準備の初期コストをカバーする印刷業者の設定料などを表します。</span><span class="sxs-lookup"><span data-stu-id="87ca0-152">If this were for a targeted mailing solution, the fixed cost might represent a printer setup fee that covers the initial cost of preparing the promotional mailing.</span></span>  
  
     <span data-ttu-id="87ca0-153">このコストは、対象になる母集団全体に 1 回だけ適用されます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-153">This cost applies one time to the entire target population.</span></span>  
  
     <span data-ttu-id="87ca0-154">**個別コスト**</span><span class="sxs-lookup"><span data-stu-id="87ca0-154">**Individual Cost**</span></span>  
     <span data-ttu-id="87ca0-155">固定コスト以外に追加されるコストで、各顧客へのコンタクトに関連するコストです。</span><span class="sxs-lookup"><span data-stu-id="87ca0-155">Costs that are in addition to the fixed cost, that can be associated with each customer contact.</span></span> <span data-ttu-id="87ca0-156">たとえば、ダイレクトメールの郵送料や電話料金などを入力できます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-156">For example, you might enter the postage cost for a promotional mailing or the cost of making telephone calls.</span></span>  
  
     <span data-ttu-id="87ca0-157">このコストは、対象になる母集団全体で同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="87ca0-157">This cost must be the same for the entire target population.</span></span> <span data-ttu-id="87ca0-158">それぞれの値に、対象になるケースの数を掛けた値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="87ca0-158">Each value is multiplied by the number of cases that are targeted.</span></span>  
  
     <span data-ttu-id="87ca0-159">**個人ごとの収益**</span><span class="sxs-lookup"><span data-stu-id="87ca0-159">**Revenue Per Individual**</span></span>  
     <span data-ttu-id="87ca0-160">成功した各販売に関連する収益です。</span><span class="sxs-lookup"><span data-stu-id="87ca0-160">The amount of revenue that is associated with each successful sale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ca0-161">参照</span><span class="sxs-lookup"><span data-stu-id="87ca0-161">See Also</span></span>  
 <span data-ttu-id="87ca0-162">[リフトチャート &#40;Analysis Services-データマイニング&#41;](lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="87ca0-162">[Lift Chart &#40;Analysis Services - Data Mining&#41;](lift-chart-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="87ca0-163">分類マトリックス &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="87ca0-163">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)  
  
  
