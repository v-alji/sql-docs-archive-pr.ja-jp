---
title: '[入力の選択] タブ ([マイニング精度チャート] ビュー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.columnmapping.f1
ms.assetid: f8b1193c-5c86-4c7e-8e35-158d293184fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c5e99e5be275dff6e218d172316c612b5ba0c41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641367"
---
# <a name="input-selection-tab-mining-accuracy-chart-view"></a><span data-ttu-id="ba248-102">[入力の選択] タブ ([マイニング精度チャート] ビュー)</span><span class="sxs-lookup"><span data-stu-id="ba248-102">Input Selection Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="ba248-103">**[マイニング精度チャート]** デザイナーの **[入力の選択]** タブを使用すると、モデルのテストや精度チャートの作成に使用するデータのソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ba248-103">Use the **Input Selection** tab of the **Mining Accuracy Chart** designer to specify the source of the data that is used to test the model and build the accuracy chart.</span></span>  
  
 <span data-ttu-id="ba248-104">**詳細情報: 「** [テストおよび検証 &#40;データ マイニング&#41;](data-mining/testing-and-validation-data-mining.md)」</span><span class="sxs-lookup"><span data-stu-id="ba248-104">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="ba248-105">Options</span><span class="sxs-lookup"><span data-stu-id="ba248-105">Options</span></span>  
 <span data-ttu-id="ba248-106">**[予測列と**  **値の同期]**</span><span class="sxs-lookup"><span data-stu-id="ba248-106">**Synchronize Prediction**  **Columns and Values**</span></span>  
 <span data-ttu-id="ba248-107">グリッドの予測可能な属性を調整する場合にオンにします。属性が異なる名前を持っていても、モデル トレーニング中に同じ予測可能なマイニング構造列から属性が派生されるように調整します。</span><span class="sxs-lookup"><span data-stu-id="ba248-107">Select to coordinate the predictable attributes in the grid so that, even if they have a different name, they are derived from the same predictable mining structure column during model training.</span></span>  
  
 <span data-ttu-id="ba248-108">**注** 既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="ba248-108">**Note** This option is selected by default.</span></span> <span data-ttu-id="ba248-109">2 つのマイニング構造列の基になるリレーショナル ソースまたは多次元ソースが同じで、列の状態が同じであるかまたは不連続性が同じであることがわかっている場合にのみ、オフにしてください。</span><span class="sxs-lookup"><span data-stu-id="ba248-109">You should only clear this box for cases in which you know that two mining structure columns derive from the same underlying relational or multi-dimensional source, and that the columns contain the same states or have been discretized in the same way.</span></span>  
  
 <span data-ttu-id="ba248-110">**[リフト チャートに表示する予測可能なマイニング モデル列の選択]**</span><span class="sxs-lookup"><span data-stu-id="ba248-110">**Select predictable mining model columns to show in the lift chart**</span></span>  
 <span data-ttu-id="ba248-111">リフト チャートに含めるモデルの決定と、リフト チャートでの使用方法を制御するための列を含むグリッドです。</span><span class="sxs-lookup"><span data-stu-id="ba248-111">A grid that contains columns to control which models are included in the lift chart and how they are used in the lift chart.</span></span>  
  
|<span data-ttu-id="ba248-112">値</span><span class="sxs-lookup"><span data-stu-id="ba248-112">Value</span></span>|<span data-ttu-id="ba248-113">説明</span><span class="sxs-lookup"><span data-stu-id="ba248-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ba248-114">**表示**</span><span class="sxs-lookup"><span data-stu-id="ba248-114">**Show**</span></span>|<span data-ttu-id="ba248-115">グラフに表示するマイニング モデル内の各予測可能列の名前の横にあるボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ba248-115">Select the box next to the name of each predictable column in the mining model that you want to display in the chart.</span></span><br /><br /> <span data-ttu-id="ba248-116">グラフが複雑で見づらい場合は、1 つまたは複数の列の横にあるボックスをオフにすると、見やすくなります。</span><span class="sxs-lookup"><span data-stu-id="ba248-116">If the chart is too complex to view easily, clear the box next to one or more columns to simplify the chart.</span></span><br /><br /> <span data-ttu-id="ba248-117">注: 1 つ以上の列が選択されていないと精度チャートを作成できません。</span><span class="sxs-lookup"><span data-stu-id="ba248-117">Note: You cannot create an accuracy chart unless at least one column is selected.</span></span>|  
|<span data-ttu-id="ba248-118">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="ba248-118">**Mining Model**</span></span>|<span data-ttu-id="ba248-119">マイニング構造に含まれるマイニング モデルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ba248-119">Lists the mining models that are contained in the mining structure.</span></span>|  
|<span data-ttu-id="ba248-120">**[予測可能列名]**</span><span class="sxs-lookup"><span data-stu-id="ba248-120">**Predictable Column Name**</span></span>|<span data-ttu-id="ba248-121">リフト チャートの作成に使用される、マイニング モデル内に含まれた予測可能列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba248-121">Select a predictable column that is contained in the mining models that are used to create the lift chart.</span></span>|  
|<span data-ttu-id="ba248-122">**[予測値]**</span><span class="sxs-lookup"><span data-stu-id="ba248-122">**Predict Value**</span></span>|<span data-ttu-id="ba248-123">予測可能列の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba248-123">Select a value for the predictable column.</span></span> <span data-ttu-id="ba248-124">この値を空白にすると、リフト チャートは、予測可能列のすべての状態に対してモデルがどのように実行されるかを予測します。</span><span class="sxs-lookup"><span data-stu-id="ba248-124">If you leave this blank, the lift chart predicts how well the model performs for all states of the predictable column.</span></span>|  
  
 <span data-ttu-id="ba248-125">**[精度チャートに使用するデータセットの選択]**</span><span class="sxs-lookup"><span data-stu-id="ba248-125">**Select data set to be used for Accuracy Chart**</span></span>  
 <span data-ttu-id="ba248-126">精度テスト データを指定するための 3 つのオプションを含むオプション グループです。</span><span class="sxs-lookup"><span data-stu-id="ba248-126">An option group that contains three options for specifying accuracy test data.</span></span>  
  
|<span data-ttu-id="ba248-127">値</span><span class="sxs-lookup"><span data-stu-id="ba248-127">Value</span></span>|<span data-ttu-id="ba248-128">説明</span><span class="sxs-lookup"><span data-stu-id="ba248-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ba248-129">**[マイニング モデルのテスト ケースを使用する]**</span><span class="sxs-lookup"><span data-stu-id="ba248-129">**Use mining model test cases**</span></span>|<span data-ttu-id="ba248-130">マイニング構造をパーティション分割したときに作成されたテスト セットを使用し、モデルに定義されているフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="ba248-130">Use the testing set that was created when you partitioned the mining structure, and apply the filter that is defined on the model.</span></span> <span data-ttu-id="ba248-131">モデル フィルターについて詳しくは、「 [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="ba248-131">For information about model filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)</span></span>|  
|<span data-ttu-id="ba248-132">**[マイニング構造のテスト ケースを使用する]**</span><span class="sxs-lookup"><span data-stu-id="ba248-132">**Use mining structure test cases**</span></span>|<span data-ttu-id="ba248-133">マイニング構造をパーティション分割したときに作成されたテスト セットを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba248-133">Use the testing set that was created when you partitioned the mining structure.</span></span>|  
|<span data-ttu-id="ba248-134">**[別のデータセットを指定する]**</span><span class="sxs-lookup"><span data-stu-id="ba248-134">**Specify a different data set**</span></span>|<span data-ttu-id="ba248-135">テスト データセットとして使用するテーブルを既存のデータ ソース ビューから指定します。</span><span class="sxs-lookup"><span data-stu-id="ba248-135">Specify a table from an existing data source view to use as a test data set.</span></span>|  
  
## <a name="filtering-options"></a><span data-ttu-id="ba248-136">フィルター処理オプション</span><span class="sxs-lookup"><span data-stu-id="ba248-136">Filtering Options</span></span>  
 <span data-ttu-id="ba248-137">**[別のデータセットを指定する]** オプションを選択した場合、データ ソース ビューを定義したり、そのデータに適用するフィルターを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="ba248-137">If you select the option **Specify a different data set**, you can define a data source view and create filters to apply to that data.</span></span> <span data-ttu-id="ba248-138">フィルターを作成することは、テスト データをデータ ソース ビューから返すクエリに WHERE 句を作成することです。</span><span class="sxs-lookup"><span data-stu-id="ba248-138">When you create a filter, you are creating a WHERE clause in the query that returns the test data from the data source view.</span></span>  
  
 <span data-ttu-id="ba248-139">**メモ**[**入力の選択**] タブを使用して、マイニングモデルにフィルターを指定することはできません。モデルフィルターを作成するには、[**マイニングモデル**] タブをクリックし、モデルのプロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="ba248-139">**Note** You cannot specify a filter on the mining model by using the **Input Selection** tab. To create a model filter, click the **Mining Models** tab and edit the model properties.</span></span>  
  
 <span data-ttu-id="ba248-140">マイニング構造を作成したときにテスト用に提示されるセットを作成しなかった場合は、このオプションを選択し、元のデータ ソース ビューをテスト セットとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="ba248-140">If you did not create a holdout set for testing when you created the mining structure, you can select this option and then specify the original data source view as a test set.</span></span> <span data-ttu-id="ba248-141">この方法を使用することで、元のデータセットにフィルターを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ba248-141">By using  this workaround, you can also set filters on the original data set.</span></span>  
  
 <span data-ttu-id="ba248-142">**[列マッピングの指定]**</span><span class="sxs-lookup"><span data-stu-id="ba248-142">**Specify Column Mapping**</span></span>  
 <span data-ttu-id="ba248-143">**[列マッピングの指定]** ダイアログ ボックスを開きます。このダイアログ ボックスでは、データ ソースの選択、ケースおよび入れ子になったテーブルの指定、マイニング構造列への外部データ列のマッピングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ba248-143">Opens the **Specify Column Mapping** dialog box, where you select the data source, specify case and nested tables, and map external data columns to the mining structure columns.</span></span>  
  
 <span data-ttu-id="ba248-144">詳しくは、「[[列マッピングの指定] ダイアログ ボックス &#40;マイニング精度チャート&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ba248-144">For more information, see [Specify Column Mapping Dialog Box &#40;Mining Accuracy Chart&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md).</span></span>  
  
 <span data-ttu-id="ba248-145">**[フィルター式]**</span><span class="sxs-lookup"><span data-stu-id="ba248-145">**Filter Expression**</span></span>  
 <span data-ttu-id="ba248-146">フィルター エディターを使用して作成したフィルター条件が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba248-146">Displays the filter condition that you built by using the filter editors.</span></span>  
  
 <span data-ttu-id="ba248-147">**[フィルター エディターを開く]**</span><span class="sxs-lookup"><span data-stu-id="ba248-147">**Open Filter Editor**</span></span>  
 <span data-ttu-id="ba248-148">**[データセット フィルター]** ダイアログ ボックスを開きます。このダイアログ ボックスでは、外部テーブルの選択やケース テーブル列への条件の設定を行うことができます。さらに、 **[フィルター]** ダイアログ ボックスを使用して、選択されているテーブルの個々の列または入れ子になったテーブルの列に適用する条件を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ba248-148">Opens the **Data Set Filter** dialog box, which lets you select external tables, and set conditions on case table columns, and the **Filter** dialog box, which helps you build conditions that apply to individual columns in the selected table, or to columns in nested tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba248-149">参照</span><span class="sxs-lookup"><span data-stu-id="ba248-149">See Also</span></span>  
 <span data-ttu-id="ba248-150">[テストと検証のタスクと操作方法 &#40;データマイニング&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ba248-150">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 <span data-ttu-id="ba248-151">[マイニング精度チャートデザイナー &#40;データマイニング&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ba248-151">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="ba248-152">[マイニングモデルへのフィルターの適用](data-mining/apply-a-filter-to-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="ba248-152">[Apply a Filter to a Mining Model](data-mining/apply-a-filter-to-a-mining-model.md) </span></span>  
 [<span data-ttu-id="ba248-153">マイニング モデルのフィルター &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="ba248-153">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining/mining-models-analysis-services-data-mining.md)  
  
  
