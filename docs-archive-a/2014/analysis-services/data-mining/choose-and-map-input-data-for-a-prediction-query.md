---
title: 予測クエリの入力データの選択およびマップ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tables [Analysis Services], prediction queries
- Mining Model Prediction [Analysis Services], input tables
ms.assetid: 00d330a0-879d-4da0-9f29-53c288116f4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54e11752d6278e01e50a379bf7bb57521ff9bb29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639812"
---
# <a name="choose-and-map-input-data-for-a-prediction-query"></a><span data-ttu-id="8ce51-102">予測クエリの入力データの選択およびマップ</span><span class="sxs-lookup"><span data-stu-id="8ce51-102">Choose and Map Input Data for a Prediction Query</span></span>
  <span data-ttu-id="8ce51-103">マイニング モデルから予測を作成する場合は、一般に新しいデータをモデルに供給することでこの操作を行います</span><span class="sxs-lookup"><span data-stu-id="8ce51-103">When you create predictions from a mining model, you generally do this by feeding new data into the model.</span></span> <span data-ttu-id="8ce51-104">(例外はタイム シリーズ モデルで、履歴データのみに基づいて予測を行うことができます)。モデルに新しいデータを提供するには、データがデータ ソース ビューの一部として使用可能であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-104">(The exception is time series models, which can make predictions based on historical data only.) To provide the model with new data, you must make sure that the data is available as part of a data source view.</span></span> <span data-ttu-id="8ce51-105">予測に使用するデータがあらかじめわかっている場合は、モデルの作成に使用するデータ ソース ビューにそのデータを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-105">If you know in advance which data you will use for prediction, you can include it in the data source view that you used to create the model.</span></span> <span data-ttu-id="8ce51-106">それ以外の場合は、新しいデータ ソース ビューを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-106">Otherwise, you might have to create a new data source view.</span></span> <span data-ttu-id="8ce51-107">詳細については、 [「多次元モデルのデータ ソース ビュー」](../multidimensional-models/data-source-views-in-multidimensional-models.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ce51-107">For more information, see [Data Source Views in Multidimensional Models](../multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="8ce51-108">必要なデータが一対多の結合で複数の表に含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-108">Sometimes the data that you need might be contained within more than one table in a one-to-many join.</span></span> <span data-ttu-id="8ce51-109">これはデータがアソシエーション モデルまたはシーケンス クラスター モデルに使用されるケースであり、製品またはトランザクションの詳細を含む入れ子になったテーブルにリンクしているケース テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-109">This is the case with data used for association models or sequence clustering models, which use a case table linked to a nested table that contains product or transaction details.</span></span> <span data-ttu-id="8ce51-110">モデルでケースが入れ子になったテーブル構造を使用する場合は、予測に使用するデータにもケースが入れ子になったテーブル構造が必要です。</span><span class="sxs-lookup"><span data-stu-id="8ce51-110">If your model uses a case-nested table structure, the data that you use for prediction must also have a case-nested table structure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8ce51-111">新しい列を追加したり、別のデータ ソース ビュー内にある列をマップしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8ce51-111">You cannot add new columns or map columns that are in a different data source view.</span></span> <span data-ttu-id="8ce51-112">選択したデータ ソース ビューには、予測クエリに必要なすべての列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-112">The data source view that you select must contain all the columns that you need for the prediction query.</span></span>  
  
 <span data-ttu-id="8ce51-113">予測に使用するデータが格納されているテーブルを識別した後で、外部データの列をマイニング モデルの列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-113">After you have identified the tables that contain the data you will use for predictions, you must map the columns in the external data to the columns in the mining model.</span></span> <span data-ttu-id="8ce51-114">たとえば、モデルで人口統計とアンケートの回答に基づいて顧客の購入行動を予測する場合、入力データには、モデル内に何があるかに通常対応する情報が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-114">For example, if your model predicts customer purchasing behavior based on demographics and survey responses, your input data should contains information that generally corresponds to what is in the model.</span></span> <span data-ttu-id="8ce51-115">すべての単一列に対応データが必要なわけではありませんが、対応する列が多い方が適しています。</span><span class="sxs-lookup"><span data-stu-id="8ce51-115">You do not need to have matching data for every single column, but the more columns you can match, the better.</span></span> <span data-ttu-id="8ce51-116">異なるデータ型の列をマップしようとすると、エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-116">If you try to map columns that have different data types, you might get an error.</span></span> <span data-ttu-id="8ce51-117">その場合は、データ ソース ビューで名前付きの計算を定義して、新しい列データをモデルに必要なデータ型にキャストまたは変換できます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-117">In that case, you could define a named calculation in the data source view to cast or convert the new column data to the data type required by the model.</span></span> <span data-ttu-id="8ce51-118">詳細については、「[データソースビューでの名前付き計算の定義 &#40;Analysis Services&#41;](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ce51-118">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md).</span></span>  
  
 <span data-ttu-id="8ce51-119">予測に使用するデータを選択すると、選択したデータ ソース内の一部の列は、名前の類似性および一致するデータ型に基づいてマイニング モデルの列に自動的にマップされることがあります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-119">When you choose the data to use for prediction, some columns in the selected data source might be automatically mapped to the mining model columns, based on name similarity and matching data type.</span></span> <span data-ttu-id="8ce51-120">**[マイニング モデル予測]** の **[マッピングの変更]** ダイアログ ボックスを使用して、マップされる列の変更、不適切なマッピングの削除、または既存の列の新規マッピングの作成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-120">You can use the **Modify Mapping** dialog box in the **Mining Model Prediction** to change the columns that are mapped, delete inappropriate mappings, or create new mappings for existing columns.</span></span> <span data-ttu-id="8ce51-121">**[マイニング モデル予測]** デザイン画面では、接続のドラッグ アンド ドロップ編集もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-121">The **Mining Model Prediction** design surface also supports drag-and-drop editing of connections.</span></span>  
  
-   <span data-ttu-id="8ce51-122">新しい接続を作成するには、 **[マイニング モデル]** テーブルで単に列を選択し、 **[入力テーブルの選択]** テーブルの対応する列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-122">To create a new connection, just select a column in the **Mining Model** table and drag it to the corresponding column in the **SelectInput Table(s)** table.</span></span>  
  
-   <span data-ttu-id="8ce51-123">接続を削除するには、接続線を選択して Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-123">To remove a connection, select the connection line and press the DELETE key.</span></span>  
  
 <span data-ttu-id="8ce51-124">次の手順では、 **[入れ子になった結合の指定]** ダイアログ ボックスを使用して、予測クエリへの入力として使用するためにケース テーブルと入れ子になったテーブルの間に作成された結合を変更する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-124">The following procedure describes how you can modify the joins that have been created between the case table and a nested table used as inputs to a prediction query, using the **Specify Nested Join** dialog box.</span></span>  
  
### <a name="select-an-input-table"></a><span data-ttu-id="8ce51-125">入力テーブルの選択</span><span class="sxs-lookup"><span data-stu-id="8ce51-125">Select an input table</span></span>  
  
1.  <span data-ttu-id="8ce51-126">**のデータ マイニング デザイナーの** [マイニング精度チャート] **タブにある** [入力テーブルの選択] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]テーブルで、 **[ケース テーブルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-126">On the **Select Input Table(s)** table of the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Select Case Table**.</span></span>  
  
     <span data-ttu-id="8ce51-127">**[テーブルの選択]** ダイアログ ボックスが表示され、クエリの基になるデータが含まれているテーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-127">The **Select Table** dialog box opens, in which you can select the table that contains the data on which to base your queries.</span></span>  
  
2.  <span data-ttu-id="8ce51-128">**[テーブルの選択]** ダイアログ ボックスで、データ ソースを **[データ ソース]** 一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-128">In the **Select Table** dialog box, select a data source from the **Data Source** list.</span></span>  
  
3.  <span data-ttu-id="8ce51-129">**[テーブル名またはビュー名]** で、モデルのテストに使用するデータが含まれているテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-129">Under **Table/View Name**, select the table that contains the data you want to use to test the models.</span></span>  
  
4.  <span data-ttu-id="8ce51-130">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-130">Click **OK**.</span></span>  
  
     <span data-ttu-id="8ce51-131">マイニング構造の列が、入力テーブル内の同じ名前を持つ列に自動的にマップされます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-131">The columns in the mining structure are automatically mapped to the columns that have the same name in the input table.</span></span>  
  
### <a name="change-the-way-that-input-data-is-mapped-to-the-model"></a><span data-ttu-id="8ce51-132">入力データがモデルにマップされる方法の変更</span><span class="sxs-lookup"><span data-stu-id="8ce51-132">Change the way that input data is mapped to the model</span></span>  
  
1.  <span data-ttu-id="8ce51-133">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーで、 **[マイニング モデル予測]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-133">In Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="8ce51-134">**[マイニング モデル]** メニューで **[接続の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-134">On the **Mining Model** menu, select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="8ce51-135">**[マッピングの変更]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-135">The **Modify Mapping** dialog box opens.</span></span> <span data-ttu-id="8ce51-136">このダイアログ ボックスの **[マイニング モデル列]** に、選択したマイニング構造の列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-136">In this dialog box, the column **Mining Model Column** lists the columns in the selected mining structure.</span></span> <span data-ttu-id="8ce51-137">**[テーブル列]** に、 **[入力テーブルの選択]** ダイアログ ボックスで選択した外部データ ソースの列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-137">The column **Table Column** lists the columns in the external data source that you chose in the **SelectInput Table(s)** dialog box.</span></span> <span data-ttu-id="8ce51-138">外部データ ソースの列はマイニング モデル内の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-138">The columns in the external data source are mapped to columns in the mining model.</span></span>  
  
3.  <span data-ttu-id="8ce51-139">**[テーブル列]** で、マップ先のマイニング モデル列に対応する行を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-139">Under **Table Column**, select the row that corresponds to the mining model column that you want to map to.</span></span>  
  
4.  <span data-ttu-id="8ce51-140">外部データ ソースで使用可能な列の一覧から新しい列を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-140">Select a new column from the list of available columns in the external data source.</span></span> <span data-ttu-id="8ce51-141">列マッピングを削除するには、一覧内の空白の項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-141">Select the blank item in the list to delete the column mapping.</span></span>  
  
5.  <span data-ttu-id="8ce51-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="8ce51-143">新しい列マッピングがデザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-143">The new column mappings are displayed in the designer.</span></span>  
  
### <a name="remove-a-relationship-between-input-tables"></a><span data-ttu-id="8ce51-144">入力テーブル間のリレーションシップの削除</span><span class="sxs-lookup"><span data-stu-id="8ce51-144">Remove a relationship between input tables</span></span>  
  
1.  <span data-ttu-id="8ce51-145">**のデータ マイニング デザイナーの** [マイニング モデル予測] **タブにある** [入力テーブルの選択] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]テーブルで、 **[結合の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-145">On the **Select Input Table(s)** table of the **Mining Model Prediction** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Modify Join**.</span></span>  
  
     <span data-ttu-id="8ce51-146">**[入れ子になった結合の指定]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-146">The **Specify Nested Join** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8ce51-147">リレーションシップを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-147">Select a relationship.</span></span>  
  
3.  <span data-ttu-id="8ce51-148">**[リレーションシップの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-148">Click **Remove Relationship**.</span></span>  
  
4.  <span data-ttu-id="8ce51-149">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-149">Click **OK**.</span></span>  
  
     <span data-ttu-id="8ce51-150">ケース テーブルと入れ子になったテーブルの間のリレーションシップが削除されます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-150">The relationship between the case table and the nested table has been removed.</span></span>  
  
### <a name="create-a-new-relationship-between-input-tables"></a><span data-ttu-id="8ce51-151">入力テーブル間の新しいリレーションシップの作成</span><span class="sxs-lookup"><span data-stu-id="8ce51-151">Create a new relationship between input tables</span></span>  
  
1.  <span data-ttu-id="8ce51-152">データ マイニング デザイナーの **[マイニング モデル予測]** タブにある **[入力テーブルの選択]** テーブルで、 **[結合の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-152">On the **Select Input Table(s)** table of the **Mining Model Prediction** tab in Data Mining Designer, click **Modify Join**.</span></span>  
  
     <span data-ttu-id="8ce51-153">**[入れ子になった結合の指定]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-153">The **Specify Nested Join** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8ce51-154">**[リレーションシップの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-154">Click **Add Relationship**.</span></span>  
  
     <span data-ttu-id="8ce51-155">**[リレーションシップの作成]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-155">The **Create Relationship** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="8ce51-156">入れ子になったテーブルのキーを **[基になる列]** で選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-156">Select the key of the nested table in **Source Columns**.</span></span>  
  
4.  <span data-ttu-id="8ce51-157">ケース テーブルのキーを **[対象になる列]** で選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-157">Select the key of the case table in **Destination Columns**.</span></span>  
  
5.  <span data-ttu-id="8ce51-158">**[リレーションシップの作成]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-158">Click **OK** in the **Create Relationship** dialog box.</span></span>  
  
6.  <span data-ttu-id="8ce51-159">**[入れ子になった結合の指定]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce51-159">Click **OK** in the **Specify Nested Join** dialog box.</span></span>  
  
     <span data-ttu-id="8ce51-160">ケース テーブルと入れ子になったテーブルの間に新しいリレーションシップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-160">A new relationship has been created between the case table and the nested table.</span></span>  
  
### <a name="add-a-nested-table-to-the-input-tables-of-a-prediction-query"></a><span data-ttu-id="8ce51-161">入れ子になったテーブルの予測クエリの入力テーブルへの追加</span><span class="sxs-lookup"><span data-stu-id="8ce51-161">Add a nested table to the input tables of a prediction query</span></span>  
  
1.  <span data-ttu-id="8ce51-162">データ マイニング デザイナーの **[マイニング モデル予測]** タブで、 **[ケース テーブルの選択]** をクリックして **[テーブルの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-162">On the **Mining Model Prediction** tab in Data Mining Designer, click **Select Case Table** to open the **Select Table** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ce51-163">入れ子になったテーブルはケース テーブルを指定しないと入力に追加できません。</span><span class="sxs-lookup"><span data-stu-id="8ce51-163">You cannot add a nested table to the inputs unless you have specified a case table.</span></span> <span data-ttu-id="8ce51-164">入れ子になったテーブルを使用するには、予測に使用するマイニング モデルでも入れ子になったテーブルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce51-164">Use of a nested table requires that the mining model you are using for prediction also uses a nested table.</span></span>  
  
2.  <span data-ttu-id="8ce51-165">**[テーブルの選択]** ダイアログ ボックスで、 **[データ ソース]** ボックスの一覧からデータ ソースを選択し、データ ソース ビュー内でケース データが含まれているテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-165">In the **Select Table** dialog box, select a data source from the **Data Source** list, and select the table in the data source view that contains the case data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="8ce51-166">**[入れ子になったテーブルの選択]** をクリックして **[テーブルの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-166">Click **Select Nested Table** to open the **Select Table** dialog box.</span></span>  
  
4.  <span data-ttu-id="8ce51-167">**[テーブルの選択]** ダイアログ ボックスで、 **[データ ソース]** ボックスの一覧からデータ ソースを選択し、データ ソース ビュー内で入れ子になったデータが含まれているテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce51-167">In the **Select Table** dialog box, select a data source from the **Data Source** list, and select the table in the data source view that contains the nested data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="8ce51-168">リレーションシップが既に存在する場合は、マイニング モデルの列が、入力テーブル内の同じ名前の列に自動的にマップされます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-168">If a relationship already exists, the columns in the mining model are automatically mapped to the columns that have the same name in the input table.</span></span> <span data-ttu-id="8ce51-169">入れ子になったテーブルとケース テーブル間のリレーションシップは、 **[結合の変更]** をクリックし、 **[リレーションシップの作成]** ダイアログ ボックスを開いて変更できます。</span><span class="sxs-lookup"><span data-stu-id="8ce51-169">You can modify the relationship between the nested table and the case table by clicking **Modify Join**, which opens the **Create Relationship** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce51-170">参照</span><span class="sxs-lookup"><span data-stu-id="8ce51-170">See Also</span></span>  
 [<span data-ttu-id="8ce51-171">予測クエリ &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="8ce51-171">Prediction Queries &#40;Data Mining&#41;</span></span>](prediction-queries-data-mining.md)  
  
  
