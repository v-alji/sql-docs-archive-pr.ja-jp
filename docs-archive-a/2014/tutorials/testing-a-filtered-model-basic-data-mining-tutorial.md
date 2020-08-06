---
title: フィルター選択されたモデルのテスト (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a97b5ca3523d1fc73405baba52b179a9bef04767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631386"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a><span data-ttu-id="da579-102">フィルター選択されたモデルのテスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="da579-102">Testing a Filtered Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="da579-103">モデルが最も正確であると判断したので `TM_Decision_Tree` 、絞り込みメール配信キャンペーンのニーズに合わせてモデルをカスタマイズし [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="da579-103">Now that you have determined that the `TM_Decision_Tree` model is the most accurate, you will customize the model to better suit the needs of the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] targeted mailing campaign.</span></span> <span data-ttu-id="da579-104">具体的には、マーケティング部門では男性顧客と女性顧客に違いがあるかどうかを知りたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="da579-104">Specifically, the Marketing department would like to know if there are any differences between male and female customers.</span></span> <span data-ttu-id="da579-105">この情報は、広告媒体として使用する雑誌やダイレクト メールで特集する製品を決定する際に役立つ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="da579-105">The information could help them decide which magazines to use for advertising and which products to feature in their mailings.</span></span>  
  
## <a name="using-filters"></a><span data-ttu-id="da579-106">フィルターの使用</span><span class="sxs-lookup"><span data-stu-id="da579-106">Using Filters</span></span>  
 <span data-ttu-id="da579-107">フィルター選択を行うと、データのサブセットに基づくモデルを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="da579-107">Filtering enables you to easily create models built on subsets of your data.</span></span> <span data-ttu-id="da579-108">フィルターはモデルにのみ適用され、基になるデータ ソースは変更しません。</span><span class="sxs-lookup"><span data-stu-id="da579-108">The filter is applied only to the model and does not change the underlying data source.</span></span>  
  
 <span data-ttu-id="da579-109">このレッスンでは、性別に基づいてフィルター処理を実行するモデルを作成し、男性と女性それぞれの購買行動に最も大きな影響を及ぼす特性を予測します。</span><span class="sxs-lookup"><span data-stu-id="da579-109">In this lesson, you will create a model that is filtered on gender, to predict the characteristics that most influence buying behavior in males and female.</span></span>  
  
 <span data-ttu-id="da579-110">まず、モデルのコピーを作成し `TM_Decision_Tree` ます。</span><span class="sxs-lookup"><span data-stu-id="da579-110">First you will make a copy of the `TM_Decision_Tree` model.</span></span>  
  
#### <a name="to-copy-the-decision-tree-model"></a><span data-ttu-id="da579-111">デシジョン ツリー モデルをコピーするには</span><span class="sxs-lookup"><span data-stu-id="da579-111">To copy the Decision Tree Model</span></span>  
  
1.  <span data-ttu-id="da579-112">の [ [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ソリューションエクスプローラーで、[ **BasicDataMining**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, select **BasicDataMining**.</span></span>  
  
2.  <span data-ttu-id="da579-113">**[マイニング モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="da579-113">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="da579-114">`TM_Decision_Tree`モデルを右クリックし、[**新しいマイニングモデル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da579-114">Right click the `TM_Decision_Tree` model, and select **New Mining Model.**</span></span>  
  
4.  <span data-ttu-id="da579-115">[**モデル名**] フィールドに「」と入力 `TM_Decision_Tree_Male` します。</span><span class="sxs-lookup"><span data-stu-id="da579-115">In the **Model name** field, type `TM_Decision_Tree_Male`.</span></span>  
  
5.  <span data-ttu-id="da579-116">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da579-116">Click **OK**.</span></span>  
  
 <span data-ttu-id="da579-117">次に、性別に基づいてモデルの顧客を選択するフィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="da579-117">Next, create a filter to select customers for the model based on their gender.</span></span>  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a><span data-ttu-id="da579-118">マイニング モデルに対してケース フィルターを作成するには</span><span class="sxs-lookup"><span data-stu-id="da579-118">To create a case filter on a mining model</span></span>  
  
1.  <span data-ttu-id="da579-119">マイニングモデルを右クリックし `TM_Decision_Tree_Male` て、ショートカットメニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="da579-119">Right-click the `TM_Decision_Tree_Male` mining model to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="da579-120">-- または --</span><span class="sxs-lookup"><span data-stu-id="da579-120">-- or --</span></span>  
  
     <span data-ttu-id="da579-121">モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-121">Select the model.</span></span> <span data-ttu-id="da579-122">**[マイニング モデル]** メニューの **[モデル フィルターの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da579-122">On the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
2.  <span data-ttu-id="da579-123">**[モデル フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** ボックスのグリッドの先頭行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da579-123">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
     <span data-ttu-id="da579-124">ドロップダウン リストに、そのテーブルの列の名前のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da579-124">The drop-down list displays only the names of the columns in that table.</span></span>  
  
3.  <span data-ttu-id="da579-125">[マイニング構造列] ボックスで、[**性別**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-125">In the Mining Structure Column text box, select **Gender**.</span></span>  
  
     <span data-ttu-id="da579-126">テキスト ボックスの左側のアイコンが変化して、選択されたアイテムがテーブルであるか列であるかが示されます。</span><span class="sxs-lookup"><span data-stu-id="da579-126">The icon at the left side of the text box changes to indicate that the selected item is a table or a column.</span></span>  
  
4.  <span data-ttu-id="da579-127">[**演算子**] ボックスをクリックし、一覧から等号 (=) 演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-127">Click the **Operator** text box and select the equal (=) operator from the list.</span></span>  
  
5.  <span data-ttu-id="da579-128">[**値**] テキストボックスをクリックし、「 **M**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="da579-128">Click the **Value** text box, and type **M**.</span></span>  
  
6.  <span data-ttu-id="da579-129">グリッドの次の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da579-129">Click the next row in the grid.</span></span>  
  
7.  <span data-ttu-id="da579-130">[ **OK]** をクリックして [**モデルフィルター** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="da579-130">Click **OK** to close the **Model Filter** dialog box.</span></span>  
  
     <span data-ttu-id="da579-131">フィルターが [**プロパティ**] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="da579-131">The filter displays in the **Properties** window.</span></span> <span data-ttu-id="da579-132">または、[**プロパティ**] ウィンドウから [**モデルフィルター** ] ダイアログを起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="da579-132">Alternately, you can launch the **Model Filter** dialog from the **Properties** window.</span></span>  
  
8.  <span data-ttu-id="da579-133">上記の手順を繰り返しますが、今度はモデルの名前 `TM_Decision_Tree_Female` を指定し、[**値**] テキストボックスに「 **F** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="da579-133">Repeat the above steps, but this time name the model `TM_Decision_Tree_Female` and type **F** in the **Value** text box.</span></span>  
  
## <a name="process-the-filtered-models"></a><span data-ttu-id="da579-134">フィルター選択されたモデルの処理</span><span class="sxs-lookup"><span data-stu-id="da579-134">Process the Filtered Models</span></span>  
 <span data-ttu-id="da579-135">モデルを使用するには、事前にそのモデルを配置して処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da579-135">Models cannot be used until they have been deployed and processed.</span></span> <span data-ttu-id="da579-136">モデルの処理の詳細については、「 [&#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da579-136">For more information on processing models, see [Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md).</span></span>  
  
#### <a name="to-process-the-filtered-model"></a><span data-ttu-id="da579-137">フィルター選択されたモデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="da579-137">To process the filtered model</span></span>  
  
1.  <span data-ttu-id="da579-138">モデルを右クリックし、 `TM_Decision_Tree_Male` [**マイニング構造の処理] と [すべてのモデル**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-138">Right-click the `TM_Decision_Tree_Male` model and select **Process Mining Structure and all Model**s</span></span>  
  
2.  <span data-ttu-id="da579-139">[**実行**] をクリックして、新しいモデルを処理します。</span><span class="sxs-lookup"><span data-stu-id="da579-139">Click **Run** to process the new models.</span></span>  
  
3.  <span data-ttu-id="da579-140">処理が完了したら、両方の処理ウィンドウで [**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da579-140">After processing is complete, click **Close** on both processing windows.</span></span>  
  
     <span data-ttu-id="da579-141">[**マイニングモデル**] タブに2つの新しいモデルが表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="da579-141">You now have two new models displayed in the **Mining Models** tab.</span></span>  
  
## <a name="evaluate-the-results"></a><span data-ttu-id="da579-142">結果の評価</span><span class="sxs-lookup"><span data-stu-id="da579-142">Evaluate the Results</span></span>  
 <span data-ttu-id="da579-143">結果を表示してフィルター選択されたモデルの精度を評価する方法は、前の 3 つのモデルの場合とほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="da579-143">View the results and assess the accuracy of the filtered models in much the same way as you did for the previous three models.</span></span> <span data-ttu-id="da579-144">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da579-144">For more information, see:</span></span>  
  
 [<span data-ttu-id="da579-145">デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="da579-145">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="da579-146">リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="da579-146">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a><span data-ttu-id="da579-147">フィルター選択されたモデルを調査するには</span><span class="sxs-lookup"><span data-stu-id="da579-147">To explore the filtered models</span></span>  
  
1.  <span data-ttu-id="da579-148">**データマイニングデザイナー**で [**マイニングモデルビューアー** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-148">Select the **Mining Model Viewer** tab in **Data Mining Designer**.</span></span>  
  
2.  <span data-ttu-id="da579-149">[マイニングモデル] ボックスで、を選択し `TM_Decision_Tree_Male` ます。</span><span class="sxs-lookup"><span data-stu-id="da579-149">In the Mining Model box, select `TM_Decision_Tree_Male`.</span></span>  
  
3.  <span data-ttu-id="da579-150">スライド**ショーレベル**をにスライド `3` します。</span><span class="sxs-lookup"><span data-stu-id="da579-150">Slide **Show Level** to `3`.</span></span>  
  
4.  <span data-ttu-id="da579-151">[**背景**値をに変更 `1` します。</span><span class="sxs-lookup"><span data-stu-id="da579-151">Change the **Background** value to `1`.</span></span>  
  
5.  <span data-ttu-id="da579-152">"**すべて**" というラベルが付いたノードの上にカーソルを置き、自転車購入者と非自転車購入者の数を確認します。</span><span class="sxs-lookup"><span data-stu-id="da579-152">Place your cursor over the node labeled **All** to see the number of bike buyers versus non-bike buyers.</span></span>  
  
6.  <span data-ttu-id="da579-153">に対して手順 1-5 を繰り返し `TM_Decision_Tree_Female` ます。</span><span class="sxs-lookup"><span data-stu-id="da579-153">Repeat steps 1 - 5 for `TM_Decision_Tree_Female`.</span></span>  
  
7.  <span data-ttu-id="da579-154">および性別に対してフィルター処理されたモデルの結果を調べ `TM_Decision_Tree` ます。</span><span class="sxs-lookup"><span data-stu-id="da579-154">Explore the results for the `TM_Decision_Tree` and the models filtered for gender.</span></span> <span data-ttu-id="da579-155">すべての自転車購入者と比較すると、男性の自転車購入者および女性の自転車購入者には、フィルター選択されていない自転車購入者と同じ特性もいくつかありますが、この 3 者には興味深い相違点もあります。</span><span class="sxs-lookup"><span data-stu-id="da579-155">Compared to all bike buyers, male and female bike buyers share some of the same characteristics as the unfiltered bike buyers but all three have interesting differences as well.</span></span> <span data-ttu-id="da579-156">これは、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] マーケティングキャンペーンの開発に使用できる有用な情報です。</span><span class="sxs-lookup"><span data-stu-id="da579-156">This is useful information that [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] can use to develop their marketing campaign.</span></span>  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a><span data-ttu-id="da579-157">フィルター選択されたモデルのリフトをテストするには</span><span class="sxs-lookup"><span data-stu-id="da579-157">To test the lift of the filtered models</span></span>  
  
1.  <span data-ttu-id="da579-158">のデータマイニングデザイナーの [**マイニング精度チャート**] タブに切り替え [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] て、[**入力の選択**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-158">Switch to the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and select the **Input Selection** tab.</span></span>  
  
2.  <span data-ttu-id="da579-159">[**精度チャートに使用するデータセットの選択**] グループボックスで、[**マイニング構造のテストケースを使用**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-159">In the **Select data set to be used for Accuracy Chart** group box, select **Use mining structure test cases**.</span></span>  
  
3.  <span data-ttu-id="da579-160">データマイニングデザイナーの [**入力の選択**] タブの [**リフトチャートに表示する予測可能なマイニングモデル列の選択**] で、[**予測列と値の同期**] のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="da579-160">On the **Input Selection** tab of Data Mining Designer, under **Select predictable mining model columns to show in the lift chart**, select the checkbox for **Synchronize Prediction Columns and Values**.</span></span>  
  
4.  <span data-ttu-id="da579-161">[**予測可能列の名前**] 列で、各モデルに対して [**自転車購入**者] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="da579-161">In the **Predictable Column Name** column, verify that **Bike Buyer** is selected for each model.</span></span>  
  
5.  <span data-ttu-id="da579-162">[**表示]** 列で、各モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="da579-162">In the **Show** column, select each of the models.</span></span>  
  
6.  <span data-ttu-id="da579-163">[**予測値**] 列でを選択し `1` ます。</span><span class="sxs-lookup"><span data-stu-id="da579-163">In the **Predict Value** column, select `1`.</span></span>  
  
7.  <span data-ttu-id="da579-164">[**リフトチャート**] タブを選択すると、リフトチャートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da579-164">Select the **Lift Chart** tab to display the lift chart.</span></span>  
  
     <span data-ttu-id="da579-165">3 つすべてのデシジョン ツリー モデルでランダム推測モデルよりも大幅なリフトが見られ、クラスター モデルや Naive Bayes モデルより高精度であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="da579-165">You will now notice that all three Decision Tree models provide significant lift compared to the random guess model, and also outperform the Clustering and Naive-Bayes models.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="da579-166">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="da579-166">Related Tasks</span></span>  
 <span data-ttu-id="da579-167">フィルターの詳細については、「 [Analysis Services データマイニング&#41;&#40;マイニングモデルのフィルター ](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da579-167">For more information on filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="da579-168">入れ子になったテーブルにフィルターを適用する方法の例については、「中級者向け[データマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da579-168">For an example of how to apply filters to nested tables, see [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="da579-169">このレッスンの前の作業</span><span class="sxs-lookup"><span data-stu-id="da579-169">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="da579-170">リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="da579-170">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="da579-171">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="da579-171">Next Lesson</span></span>  
 [<span data-ttu-id="da579-172">レッスン 6: 予測の作成と操作 &#40;基本的なデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="da579-172">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="da579-173">参照</span><span class="sxs-lookup"><span data-stu-id="da579-173">See Also</span></span>  
 <span data-ttu-id="da579-174">[中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="da579-174">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="da579-175">[マイニングモデルタスクと操作方法](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="da579-175">[Mining Model Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="da579-176">[マイニングモデルからのフィルターの削除](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="da579-176">[Delete a Filter from a Mining Model](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md) </span></span>  
 [<span data-ttu-id="da579-177">マイニング モデルのフィルター &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="da579-177">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
