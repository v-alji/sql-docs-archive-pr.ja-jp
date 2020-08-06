---
title: モデルテストデータを選択してマップする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining accuracy charts
- Mining Accuracy Chart [Analysis Services], column mappings
- input column mapping [Analysis Services]
- mapping input columns [Analysis Services]
ms.assetid: be0d9f20-40c3-4dac-81da-281cfe724126
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f1d01c40070069d610bb028ab003223c5afbcd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639808"
---
# <a name="choose-and-map-model-testing-data"></a><span data-ttu-id="29586-102">モデルのテスト データの選択およびマップ</span><span class="sxs-lookup"><span data-stu-id="29586-102">Choose and Map Model Testing Data</span></span>
  <span data-ttu-id="29586-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で精度チャートを作成するには、モデルのテストに使用されるデータを選択し、データをモデルにマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="29586-103">To create an accuracy chart in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must choose the data that will be used to test the model, and map the data to the model.</span></span>  
  
 <span data-ttu-id="29586-104">既定では、予約データ セットをマイニング構造の構築時に作成した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではマイニング モデルのテスト データが使用されます。</span><span class="sxs-lookup"><span data-stu-id="29586-104">By default, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will use the mining model testing data, provided that you created a holdout data set when you built the mining structure.</span></span> <span data-ttu-id="29586-105">予約テスト セットを作成すると、列名とデータ型は常にモデルと一致し、データの分布が類似することを合理的に想定できるため、同じマイニング構造に基づくモデルを最も簡単にテストできます。</span><span class="sxs-lookup"><span data-stu-id="29586-105">Creating a holdout test set is the easiest way to test models that are based on the same mining structure, because the column names and data types will always match the model, and you can be reasonably assured that the distribution of the data is similar.</span></span> <span data-ttu-id="29586-106">また、デザイナーでは入力列とモデル列間のリレーションシップが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="29586-106">Also, the designer will automatically create the relationships between the input and model columns.</span></span>  
  
 <span data-ttu-id="29586-107">または、データの外部ソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="29586-107">Alternatively, you can specify an external source of data.</span></span> <span data-ttu-id="29586-108">外部データについては、いくつかの追加要件があります。</span><span class="sxs-lookup"><span data-stu-id="29586-108">For external data, there are some additional requirements:</span></span>  
  
-   <span data-ttu-id="29586-109">外部データ セットは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスでデータ ソース ビューとして定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="29586-109">The external data set must be defined as a data source view in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="29586-110">外部データ セットには、マイニング モデルの予測可能列にマッピングできる列が 1 つ以上含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="29586-110">The external data set must at least contain one column that can be mapped to the predictable column in the mining model.</span></span> <span data-ttu-id="29586-111">いくつかの列を無視することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="29586-111">You can choose to ignore some columns.</span></span>  
  
-   <span data-ttu-id="29586-112">新しい列を追加したり、別のデータ ソース ビューの列をマップしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="29586-112">You cannot add new columns or map columns in a different data source view.</span></span> <span data-ttu-id="29586-113">選択したデータ ソース ビューには、予測クエリに必要なすべての列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="29586-113">The data source view that you select must contain all the columns that you need for the prediction query.</span></span>  
  
-   <span data-ttu-id="29586-114">外部列名がモデルの列名と正確に一致する場合は、デザイナーによってマップされます。</span><span class="sxs-lookup"><span data-stu-id="29586-114">If the external column names exactly match those in the model, the designer will map them for you.</span></span> <span data-ttu-id="29586-115">マッピングが正しくない場合は、マッピングを変更するか、削除して既存の列に新しいマッピングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="29586-115">If the mappings are wrong, you can change them, or delete and create new mappings for existing columns.</span></span>  
  
-   <span data-ttu-id="29586-116">外部データ ソースを使用する場合は、フィルターを適用して、テスト データを関連するケースのサブセットに制限できます。</span><span class="sxs-lookup"><span data-stu-id="29586-116">If you use an external data source, you can apply filters to restrict the testing data to a relevant subset of cases.</span></span>  
  
-   <span data-ttu-id="29586-117">予約テスト セットを使用する場合でも、フィルターが原因でマイニング構造に関連付けられているテスト データとマイニング モデルのテスト ケースとが異なる可能性があることに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29586-117">Even when you use the holdout test set, you should be aware that filters can cause differences between the testing data associated with a mining structure and the mining model test cases.</span></span>  
  
 <span data-ttu-id="29586-118">このトピックでは、テスト データを選択およびマップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="29586-118">This topic describes how to choose and map the testing data:</span></span>  
  
 [<span data-ttu-id="29586-119">マイニング モデルの精度をテストするための入力テーブルの選択</span><span class="sxs-lookup"><span data-stu-id="29586-119">Select input tables to test the accuracy of a mining model</span></span>](#bkmk_SelectInputs)  
  
 [<span data-ttu-id="29586-120">モデル列からテスト データの列へのマップ</span><span class="sxs-lookup"><span data-stu-id="29586-120">Map model columns to the columns in the testing data</span></span>](#bkmk_MapColumns)  
  
 [<span data-ttu-id="29586-121">テスト データの列がモデルにマップされる方法の変更</span><span class="sxs-lookup"><span data-stu-id="29586-121">Change the way that columns in the testing data are mapped to the model</span></span>](#bkmk_ChangeMappings)  
  
##  <a name="to-select-input-tables-to-test-the-accuracy-of-a-mining-model"></a><a name="bkmk_SelectInputs"></a> <span data-ttu-id="29586-122">マイニング モデルの精度をテストするための入力テーブルを選択するには</span><span class="sxs-lookup"><span data-stu-id="29586-122">To select input tables to test the accuracy of a mining model</span></span>  
  
1.  <span data-ttu-id="29586-123">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーで、チャートを作成するモデルを含むマイニング構造をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="29586-123">In Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the mining structure that contains the models you want to chart.</span></span>  
  
2.  <span data-ttu-id="29586-124">**[マイニング精度チャート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="29586-124">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="29586-125">**[マイニング精度チャート]** ビューの **[入力の選択]** タブで、次のオプションのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-125">On the **Input Selection Tab** of the **Mining Accuracy Chart** view, select one of the following options:</span></span>  
  
     <span data-ttu-id="29586-126">**[マイニング モデルのテスト ケースを使用する]**</span><span class="sxs-lookup"><span data-stu-id="29586-126">**Use mining model test cases**</span></span>  
  
     <span data-ttu-id="29586-127">**[マイニング構造のテスト ケースを使用する]**</span><span class="sxs-lookup"><span data-stu-id="29586-127">**Use mining structure test cases**</span></span>  
  
     <span data-ttu-id="29586-128">**[別のデータセットを指定する]**</span><span class="sxs-lookup"><span data-stu-id="29586-128">**Specify a different data set**</span></span>  
  
4.  <span data-ttu-id="29586-129">**[別のデータセットを指定する]** を選択した場合は、必要に応じて **[フィルター エディターを開く]** をクリックし、入力データセットのフィルター条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="29586-129">If you selected **Specify a different data set**, optionally click **Open Filter Editor** to create filter conditions on the input data set.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="29586-130">**[リフト チャート]** タブまたは **[分類マトリックス]** タブをクリックすると、指定したテスト データを使用して自動的にチャートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="29586-130">Click the **Lift Chart** tab or the **Classification Matrix** tab to automatically build the chart by using the testing data you specified.</span></span>  
  
##  <a name="to-map-model-columns-to-the-columns-in-the-testing-data"></a><a name="bkmk_MapColumns"></a> <span data-ttu-id="29586-131">モデル列をテスト データの列にマップするには</span><span class="sxs-lookup"><span data-stu-id="29586-131">To map model columns to the columns in the testing data</span></span>  
  
1.  <span data-ttu-id="29586-132">チャートを作成するモデルを含むマイニング構造をダブルクリックし、データ マイニング デザイナーで構造とモデルを開きます。</span><span class="sxs-lookup"><span data-stu-id="29586-132">Double-click the mining structure that contains the models you want to chart, to open the structure and models in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="29586-133">**[マイニング精度チャート]** タブを選択し、次に **[入力の選択]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-133">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="29586-134">**[入力の選択]** タブの **[精度チャートに使用するデータセットの選択]** で、 **[別のデータセットを指定する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-134">In the **Input Selection** tab, under **Select data set to be used for Accuracy Chart**, select **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="29586-135">参照ボタン ([. **..])** をクリックしてダイアログボックスを開き、外部データセットの定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="29586-135">Click the browse button **(...)** to open a dialog box and build the definition of the external data set.</span></span>  
  
5.  <span data-ttu-id="29586-136">**[マイニング構造の選択]** ダイアログ ボックスで、操作するモデルを含んでいるマイニング構造を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="29586-136">In the **Select Mining Structure** dialog box, select the mining structure that contains the models you want to work with, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="29586-137">**[マイニング精度チャート]** タブにある **[入力テーブルの選択]** テーブルで、 **[ケース テーブルの選択]** をクリックして、 **[テーブルの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="29586-137">On the **Select Input Table(s)** table of the **Mining Accuracy Chart** tab, click **Select Case Table** to open the **Select Table** dialog box.</span></span>  
  
7.  <span data-ttu-id="29586-138">**[テーブルの選択]** ダイアログ ボックスで、データ ソースを **[データ ソース]** 一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-138">In the **Select Table** dialog box, select a data source from the **Data Source** list.</span></span> <span data-ttu-id="29586-139">モデルの精度を測定するために予測クエリで使用するデータが含まれているテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-139">Choose a table that contains the data that you want to use in the prediction queries to determine the accuracy of the models.</span></span>  
  
8.  <span data-ttu-id="29586-140">**[テーブル名またはビュー名]** ボックスで、モデルのテストに使用するデータが含まれているテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-140">In the **Table/View Name** box, select the table that contains the data that you want to use to test the models.</span></span>  
  
9. <span data-ttu-id="29586-141">必要に応じてマッピングを編集します。</span><span class="sxs-lookup"><span data-stu-id="29586-141">Edit the mappings, if necessary.</span></span> <span data-ttu-id="29586-142">マイニング構造の列が入力テーブルの同じ名前の列に自動的にマップされます。</span><span class="sxs-lookup"><span data-stu-id="29586-142">Columns in the mining structure are automatically mapped to the columns with the same name in the input table.</span></span> <span data-ttu-id="29586-143">**[入力テーブルの選択]** テーブルの列をクリックし、 **[マイニング構造]** テーブルの対応する列にドラッグして、マッピングを手動で作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="29586-143">To manually create mappings, click a column in the **Select Input Table(s)** table and drag it onto the corresponding column in the **Mining Structure** table.</span></span> <span data-ttu-id="29586-144">マッピングを削除するには、 **[マイニング構造]** テーブルの列が **[入力テーブルの選択]** テーブル内のマップ先の列にリンクしている線をクリックし、&lt;localizedText&gt;Del&lt;/localizedText&gt; キーを押します。</span><span class="sxs-lookup"><span data-stu-id="29586-144">To delete a mapping, click the line that links the column in the **Mining Structure** table to the mapped column in the **Select Input Table(s)** table, and then press DELETE.</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="to-modify-the-way-input-data-is-mapped-to-the-model"></a><a name="bkmk_ChangeMappings"></a><span data-ttu-id="29586-145">入力データをモデルにマップする方法を変更するには</span><span class="sxs-lookup"><span data-stu-id="29586-145">To modify the way input data is mapped to the model</span></span>  
  
1.  <span data-ttu-id="29586-146">データ マイニング デザイナーで、チャートを作成するモデルを含んだ構造をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="29586-146">In Data Mining Designer, double-click the structure that contains the models you want to chart.</span></span>  
  
2.  <span data-ttu-id="29586-147">**[マイニング精度チャート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="29586-147">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="29586-148">**[入力の選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="29586-148">Click the **Input Selection** tab.</span></span>  
  
4.  <span data-ttu-id="29586-149">**[精度チャートに使用するデータセットの選択**] で、[**別のデータセットを指定**する] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-149">In **Select data set to be used for Accuracy Chart**, select the option **Specify a different data set**.</span></span>  
  
5.  <span data-ttu-id="29586-150">参照ボタン ([. **..])** をクリックしてダイアログボックスを開き、外部データソースの定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="29586-150">Click the browse button **(...)** to open a dialog box and build the definition of the external data source.</span></span>  
  
6.  <span data-ttu-id="29586-151">**[列マッピングの指定]** ダイアログ ボックスで、 **[ケース テーブルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="29586-151">In the **Specify Column Mapping** dialog box, click **Select Case Table**.</span></span>  
  
7.  <span data-ttu-id="29586-152">[テーブルの選択] ダイアログ ボックスで、一覧からデータ ソース ビューを選択し、ケース データが含まれているテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-152">In the Select Table dialog box, Select a data source view from the list, and select the table that contains the case data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="29586-153">必要なテーブルがない場合は、ダイアログ ボックスを閉じ、対象のテーブルを含む新しいデータ ソース ビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="29586-153">If the tables you need are not available, close the dialog box and create a new data source view that contains the table.</span></span> <span data-ttu-id="29586-154">データソースビューの作成方法については、「[データ ソース ビューの定義 &#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29586-154">For information about how to create a data source view, see [Defining a Data Source View &#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md).</span></span>  
  
9. <span data-ttu-id="29586-155">マイニング モデルに入れ子になったテーブルが含まれている場合は、 **[入れ子になったテーブルの選択]** をクリックし、データ ソース ビューのテーブルの一覧から入れ子になったテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-155">If the mining model contains a nested table, click **Select Nested Table**, and select the nested table from the list of tables in the data source view.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="29586-156">変更するマッピングの結合線を選択し、 **[接続の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="29586-156">Select the join line of the mapping you want to modify, and select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="29586-157">**[マッピングの変更]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="29586-157">The **Modify Mapping** dialog box opens.</span></span> <span data-ttu-id="29586-158">このダイアログ ボックスのテーブルの **[マイニング構造列]** には、選択されたマイニング構造に含まれている各列が一覧表示され、 **[テーブル列]** には、マイニング構造内の列にマップされている入力テーブルの列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="29586-158">In the table in this dialog box, **Mining Structure Column** lists each column that the selected mining structure contains, and **Table Column** lists the columns from input tables that are mapped to columns in the mining structure.</span></span>  
  
11. <span data-ttu-id="29586-159">**[テーブル列]** で、リレーションシップを変更する **[マイニング構造列]** の下の行に対応する行を選択します。</span><span class="sxs-lookup"><span data-stu-id="29586-159">Under **Table Column**, select the row that corresponds to the row under **Mining Structure Column** for which you want to modify a relationship.</span></span> <span data-ttu-id="29586-160">一覧から新しい列を選択するか、一覧から空白エントリを選択して列を削除します。</span><span class="sxs-lookup"><span data-stu-id="29586-160">Select a new column from the list, or select the blank entry from the list to delete the column.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="29586-161">**[列マッピングの指定]** ダイアログ ボックスに、新しい列マッピングが表示されます。</span><span class="sxs-lookup"><span data-stu-id="29586-161">The new column mappings are displayed in the **Specify Column Mapping** dialog box.</span></span> <span data-ttu-id="29586-162">2 つの列を結ぶ線を選択して &lt;localizedText&gt;Del&lt;/localizedText&gt; キーを押すと、マッピングを削除できます。</span><span class="sxs-lookup"><span data-stu-id="29586-162">You can remove a mapping by selecting the line between the columns and pressing the DELETE key.</span></span> <span data-ttu-id="29586-163">**[マイニング構造]** テーブルで列を選択し、 **[入力テーブルの選択]** テーブルの対応する列にドラッグすると、新しい接続を作成できます。</span><span class="sxs-lookup"><span data-stu-id="29586-163">You can create a new connection by selecting a column in the **Mining Structure** table and dragging it to the corresponding column in the **SelectInput Table(s)** table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29586-164">参照</span><span class="sxs-lookup"><span data-stu-id="29586-164">See Also</span></span>  
 [<span data-ttu-id="29586-165">テストおよび検証タスク、および操作方法 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="29586-165">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
