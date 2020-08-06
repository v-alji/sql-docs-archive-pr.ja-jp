---
title: モデルテストデータへのフィルターの適用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input row filtering [SQL Server]
- filtering input rows [Analysis Services]
- Mining Accuracy Chart [Analysis Services], filtering input rows
ms.assetid: 9ccc9a23-5597-4b35-a05f-2fc8eb885147
author: minewiskan
ms.author: owend
ms.openlocfilehash: d1fd2b643ae4f7d831cab980ca45b7d43d8b58f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632189"
---
# <a name="apply-filters-to-model-testing-data"></a><span data-ttu-id="d4d30-102">モデルのテスト データへのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="d4d30-102">Apply Filters to Model Testing Data</span></span>
  <span data-ttu-id="d4d30-103">モデルのテストに使用する外部データ ソースを指定する場合に、入力データを制限するフィルターを必要に応じて適用できます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-103">When you specify an external data source to use in testing a model, you can optionally apply a filter to restrict the input data.</span></span> <span data-ttu-id="d4d30-104">たとえば、特定の所得範囲の顧客に関する予測についてのみモデルをテストできます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-104">For example, you might want to test the model specifically for predictions on customers in a certain income range.</span></span>  
  
 <span data-ttu-id="d4d30-105">たとえば、AdventureWorks の絞り込みメール配信シナリオでは、ProspectiveBuyer で次のようなフィルター式を作成できます。これは、テストデータを含むテーブルで、収入範囲に基づいてテストケースを制限します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-105">For example, in the AdventureWorks targeted mailing scenario, you can create a filter expression like the following one on ProspectiveBuyer, which is the table that contains the testing data, and restrict testing cases by income range:</span></span>  
  
 `[YearlyIncome] = '50000'`  
  
 <span data-ttu-id="d4d30-106">フィルターの動作は、モデル トレーニング データとテスト データ セットのどちらをフィルター選択するかによって若干異なります。</span><span class="sxs-lookup"><span data-stu-id="d4d30-106">The behavior of filters is slightly different, depending on whether you are filtering model training data or a testing data set:</span></span>  
  
-   <span data-ttu-id="d4d30-107">テスト データ セットに対するフィルターを定義する場合は、入力されるデータに対する WHERE 句を作成します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-107">When you define a filter on a testing data set, you create a WHERE clause on the incoming data.</span></span> <span data-ttu-id="d4d30-108">モデルの評価に使用する入力データ セットに対するフィルター処理では、グラフの作成時にフィルター式が Transact-SQL ステートメントに変換され、入力テーブルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-108">If you are filtering an input data set used for evaluating a model, the filter expression is translated to a Transact-SQL statement and applied to the input table when the chart is created.</span></span> <span data-ttu-id="d4d30-109">その結果として、テスト ケースの数を大幅に少なくすることができます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-109">As a result, the number of test cases can be greatly reduced.</span></span>  
  
-   <span data-ttu-id="d4d30-110">マイニング モデルに対してフィルターを適用する場合、作成したフィルター式はデータ マイニング拡張機能 (DMX) ステートメントに変換された後、個々のモデルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-110">When you apply a filter to a mining model, the filter expression that you create is translated to a Data Mining Extensions (DMX) statement, and applied to the individual model.</span></span> <span data-ttu-id="d4d30-111">したがって、フィルターをモデルに適用すると、モデルをトレーニングするのに元のデータのサブセットのみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-111">Therefore, when you apply a filter to a model, only a subset of the original data is used to train the model.</span></span> <span data-ttu-id="d4d30-112">このオプションは、モデルが特定のデータ セットに対して調整されるようにトレーニング モデルを 1 つの条件セットでフィルター選択して、さらに別の条件セットでモデルをテストする場合に問題を引き起こすことがあります。</span><span class="sxs-lookup"><span data-stu-id="d4d30-112">This can cause problems if you filter the training model with one set of criteria, so that the model is tuned to a certain set of data, and then test the model with another set of criteria.</span></span>  
  
-   <span data-ttu-id="d4d30-113">構造を作成するときにテスト データ セットを定義した場合、トレーニングに使用されるモデル ケースには、マイニング構造のトレーニング セット内にあり、 **かつ** フィルターの条件を満たすケースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-113">If you defined a testing data set when you created the structure, the model cases used for training include only those cases that are in the mining structure training set **and** which meet the conditions of the filter.</span></span> <span data-ttu-id="d4d30-114">このため、モデルをテストするときに **[マイニング モデルのテスト ケースを使用する]** オプションを選択した場合、テスト用ケースには、マイニング構造のテスト セット内にあり、かつフィルターの条件を満たすケースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-114">Thus, when you are testing a model and select the option **Use mining model test cases**, the testing cases will include only the cases that are in the mining structure test set and which meet the conditions of the filter.</span></span> <span data-ttu-id="d4d30-115">ただし、予約データセットを定義しなかった場合、テスト用のモデル ケースには、フィルター条件を満たすデータ セット内のすべてのケースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-115">However, if you did not define a holdout data set, the model cases used for testing include all the cases in the data set that meet the filter conditions</span></span>  
  
-   <span data-ttu-id="d4d30-116">モデルに適用するフィルター条件は、モデル ケースに対するドリルスルー クエリにも影響します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-116">Filter conditions that you apply on a model also affect drillthrough queries on the model cases.</span></span>  
  
 <span data-ttu-id="d4d30-117">要するに、複数のモデルをテストする場合は、すべてのモデルが同じマイニング構造に基づく場合でも、モデルがトレーニングとテストにデータの異なるサブセットを使用する可能性があることに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4d30-117">In summary, when you test multiple models, even if all the models are based on the same mining structure, you must be aware that the models potentially use different subsets of data for training and testing.</span></span> <span data-ttu-id="d4d30-118">これは、精度チャートに対して次の影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="d4d30-118">This can have the following effects on accuracy charts:</span></span>  
  
-   <span data-ttu-id="d4d30-119">テスト セット内のケースの総数が、テストされるモデル間で異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d4d30-119">The total number of cases in the testing sets can vary among the models being tested.</span></span>  
  
-   <span data-ttu-id="d4d30-120">モデルでトレーニング データまたはテスト データの異なるサブセットが使用される場合、チャート内で各モデルの割合が揃わないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d4d30-120">The percentages for each model may not align in the chart, if the models use different subsets of training data or testing data.</span></span>  
  
 <span data-ttu-id="d4d30-121">結果に影響する可能性のある定義済みのフィルターがモデルに含まれるかどうかを確認するには、 **[プロパティ]** ペインで **Filter** プロパティを探すか、データ マイニング スキーマ行セットを使用してモデルをクエリします。</span><span class="sxs-lookup"><span data-stu-id="d4d30-121">To determine whether a model contains a predefined filter that might affect results, you can look for the **Filter** property in the **Property** pane, or you can query the model by using the data mining schema rowsets.</span></span> <span data-ttu-id="d4d30-122">たとえば、次のクエリは指定したモデルのフィルター テキストを返します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-122">For example, the following query returns the filter text for the specified model:</span></span>  
  
 `SELECT [FILTER] FROM $system.DMSCHEMA_MINING_MODELS WHERE MODEL_NAME = 'name of model'`  
  
> [!WARNING]  
>  <span data-ttu-id="d4d30-123">既存のマイニング モデルからフィルターを削除する場合や、フィルター条件を変更する場合は、マイニング モデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4d30-123">If you want to remove the filter from an existing mining model, or change the filter conditions, you must reprocess the mining model.</span></span>  
  
 <span data-ttu-id="d4d30-124">適用できるフィルターの種類の詳細や、フィルター式がどのように評価されるかについては、「[モデル フィルターの構文と例 &#40;Analysis Services - データ マイニング&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4d30-124">For more information about the kinds of filters you can apply, and how filter expressions are evaluated, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
### <a name="create-a-filter-on-external-testing-data"></a><span data-ttu-id="d4d30-125">外部テスト データに対するフィルターの作成</span><span class="sxs-lookup"><span data-stu-id="d4d30-125">Create a filter on external testing data</span></span>  
  
1.  <span data-ttu-id="d4d30-126">テストするモデルを含むマイニング構造をダブルクリックして、データ マイニング デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-126">Double-click the mining structure that contains the model you want to test, to open Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="d4d30-127">**[マイニング精度チャート]** タブを選択し、次に **[入力の選択]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-127">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="d4d30-128">**[入力の選択]** タブの **[精度チャートに使用するデータセットの選択]** で、 **[別のデータセットを指定する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-128">On the **Input Selection** tab, under **Select data set to be used for Accuracy Chart**, select the option **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="d4d30-129">参照ボタン ([. **..])** をクリックしてダイアログボックスを開き、外部データセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-129">Click the browse button **(...)** to open a dialog box and choose the external data set.</span></span>  
  
5.  <span data-ttu-id="d4d30-130">ケース テーブルを選択し、入れ子になったテーブルを必要に応じて追加します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-130">Choose the case table, and add a nested table if necessary.</span></span> <span data-ttu-id="d4d30-131">必要に応じてモデルの列を外部データ セットの列にマップします。</span><span class="sxs-lookup"><span data-stu-id="d4d30-131">Map columns in the model to columns in the external data set as necessary.</span></span> <span data-ttu-id="d4d30-132">**[列マッピングの指定]** ダイアログ ボックスを閉じてソース テーブルの定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-132">Close the **Specify Column Mapping** dialog box to save the source table definition.</span></span>  
  
6.  <span data-ttu-id="d4d30-133">データセットのフィルターを定義するには、 **[フィルター エディターを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4d30-133">Click **Open Filter Editor** to define a filter for the data set.</span></span>  
  
     <span data-ttu-id="d4d30-134">**[データセット フィルター]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-134">The **Data Set Filter** dialog box opens.</span></span> <span data-ttu-id="d4d30-135">入れ子になったテーブルが構造に含まれている場合は、2 つの部分から成るフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-135">If the structure contains a nested table, you can create a filter in two parts.</span></span> <span data-ttu-id="d4d30-136">まず、ケース テーブルの条件を **[データセット フィルター]** ダイアログ ボックスで設定し、次に、入れ子になった行の条件を **[フィルター]** ダイアログ ボックスで設定します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-136">First, set conditions on the case table by using the **Data Set Filter** dialog box, and then set conditions on the nested rows by using the **Filter** dialog box.</span></span>  
  
7.  <span data-ttu-id="d4d30-137">**[データセット フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** の下のグリッドの先頭行をクリックし、一覧からテーブルまたは列を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-137">In the **Data Set Filter** dialog box, click the top row in the grid, under **Mining Structure Column**, and select a table or column from the list.</span></span>  
  
     <span data-ttu-id="d4d30-138">データ ソース ビューに複数のテーブルが含まれているか、入れ子になったテーブルが含まれている場合は、テーブル名を先に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4d30-138">If the data source view contains multiple tables, or a nested table, you must first select the table name.</span></span> <span data-ttu-id="d4d30-139">それ以外の場合は、ケース テーブルから列を直接選択できます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-139">Otherwise, you can select columns from the case table directly.</span></span>  
  
     <span data-ttu-id="d4d30-140">フィルター選択する各列に新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-140">Add a new row for each column that you want to filter.</span></span>  
  
8.  <span data-ttu-id="d4d30-141">**[演算子]** 列と **[値]** 列を使用して、列をフィルター選択する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-141">Use **Operator**, and **Value** columns to define how the column is filtered.</span></span>  
  
     <span data-ttu-id="d4d30-142">**注** 値は、引用符を使用せずに入力してください。</span><span class="sxs-lookup"><span data-stu-id="d4d30-142">**Note** Type values without using quotation marks.</span></span>  
  
9. <span data-ttu-id="d4d30-143">**[ルールの適用条件]** ボックスをクリックして論理演算子を選択し、複数の条件を結合する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-143">Click the **And/Or** text box and select a logical operator to define how multiple conditions are combine.</span></span>  
  
10. <span data-ttu-id="d4d30-144">必要に応じて、[**値**] テキストボックスの右側にある参照ボタン ([. **..])** をクリックして [**フィルター** ] ダイアログボックスを開き、入れ子になったテーブルまたは個々のケーステーブルの列に対して条件を設定します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-144">Optionally, click the browse button **(...)** at the right of the **Value** text box to open the **Filter** dialog box and set conditions on the nested table or on the individual case table columns.</span></span>  
  
11. <span data-ttu-id="d4d30-145">**[式]** ペインに表示されるテキストで、完成したフィルター条件が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4d30-145">Verify that the completed filter conditions are correct by viewing the text in the **Expression** pane.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="d4d30-146">フィルター条件は、精度チャートの作成時にデータ ソースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d4d30-146">The filter condition is applied to the data source when you create the accuracy chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d30-147">参照</span><span class="sxs-lookup"><span data-stu-id="d4d30-147">See Also</span></span>  
 <span data-ttu-id="d4d30-148">[モデルテストデータを選択してマップする](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="d4d30-148">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 <span data-ttu-id="d4d30-149">[入れ子になったテーブルデータを精度チャートの入力として使用する](using-nested-table-data-as-an-input-for-an-accuracy-chart.md) </span><span class="sxs-lookup"><span data-stu-id="d4d30-149">[Using Nested Table Data as an Input for an Accuracy Chart](using-nested-table-data-as-an-input-for-an-accuracy-chart.md) </span></span>  
 [<span data-ttu-id="d4d30-150">精度チャートの種類の選択とグラフのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="d4d30-150">Choose an Accuracy Chart Type and Set Chart Options</span></span>](choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
