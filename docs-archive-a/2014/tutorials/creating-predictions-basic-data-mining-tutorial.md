---
title: 予測の作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 456aec6c6b9d0d1a5d0ee1d9949507a37577130c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711205"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a><span data-ttu-id="45715-102">予測の作成 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="45715-102">Creating Predictions (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="45715-103">マイニングモデルの精度をテストし、結果に満足したと判断したら、データマイニングデザイナーの [**マイニングモデル予測**] タブにある予測クエリビルダーを使用して予測を生成できます。</span><span class="sxs-lookup"><span data-stu-id="45715-103">After you have tested the accuracy of your mining models and decided that you are satisfied with the results, you can then generate predictions by using the Prediction Query Builder on the **Mining Model Prediction** tab in the Data Mining Designer.</span></span>  
  
 <span data-ttu-id="45715-104">予測クエリ ビルダーには 3 つのビューがあります。</span><span class="sxs-lookup"><span data-stu-id="45715-104">The Prediction Query Builder has three views.</span></span> <span data-ttu-id="45715-105">**デザイン**ビューと**クエリ**ビューでは、クエリをビルドして確認できます。</span><span class="sxs-lookup"><span data-stu-id="45715-105">With the **Design** and **Query** views, you can build and examine your query.</span></span> <span data-ttu-id="45715-106">その後、クエリを実行し、**結果ビューで**結果を表示できます。</span><span class="sxs-lookup"><span data-stu-id="45715-106">You can then run the query and view the results in the **Result** view.</span></span>  
  
 <span data-ttu-id="45715-107">すべての予測クエリは、DMX を使用します。DMX とは、データ マイニング拡張機能 (Data Mining Extensions、DMX) 言語の略称です。</span><span class="sxs-lookup"><span data-stu-id="45715-107">All prediction queries use DMX, which is short for the Data Mining Extensions (DMX) language.</span></span> <span data-ttu-id="45715-108">DMX の構文は T-SQL と似ていますが、データ マイニング オブジェクトに対するクエリに使用されます。</span><span class="sxs-lookup"><span data-stu-id="45715-108">DMX has syntax like that of T-SQL but is used for queries against data mining objects.</span></span> <span data-ttu-id="45715-109">DMX 構文は複雑ではありませんが、このようなクエリビルダーを使用する場合や、 [Office 用の SQL Server データマイニングアドイン](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md)を使用する場合は、入力と式を簡単に選択できるようになるため、基本を理解することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="45715-109">Although DMX syntax is not complicated, using a query builder like this one, or the one in the [SQL Server Data Mining Add-Ins for Office](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md), makes it much easier to select inputs and build expressions, so we highly recommend that you learn the basics.</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="45715-110">クエリの作成</span><span class="sxs-lookup"><span data-stu-id="45715-110">Creating the Query</span></span>  
 <span data-ttu-id="45715-111">予測クエリを作成するには、まず、マイニング モデルと入力テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-111">The first step in creating a prediction query is to select a mining model and input table.</span></span>  
  
#### <a name="to-select-a-model-and-input-table"></a><span data-ttu-id="45715-112">モデルと入力テーブルを選択するには</span><span class="sxs-lookup"><span data-stu-id="45715-112">To select a model and input table</span></span>  
  
1.  <span data-ttu-id="45715-113">データマイニングデザイナーの [**マイニングモデル予測**] タブで、[**マイニングモデル**] ボックスの [**モデルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45715-113">On the **Mining Model Prediction** tab of Data Mining Designer, in the **Mining Model** box, click **Select Model**.</span></span>  
  
2.  <span data-ttu-id="45715-114">**[マイニングモデルの選択**] ダイアログボックスで、ツリー内を移動先の**メーリング**構造に移動し、構造を展開して、を選択し、[OK] を `TM_Decision_Tree` クリックします。 **OK**</span><span class="sxs-lookup"><span data-stu-id="45715-114">In the **Select Mining Model** dialog box, navigate through the tree to the **Targeted Mailing** structure, expand the structure, select `TM_Decision_Tree`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="45715-115">[**入力テーブルの選択**] ボックスで、[**ケーステーブルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45715-115">In the **Select Input Table(s)** box, click **Select Case Table**.</span></span>  
  
4.  <span data-ttu-id="45715-116">**[テーブルの選択**] ダイアログボックスの [**データソース**] ボックスの一覧で、データソースビューを選択し [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="45715-116">In the **Select Table** dialog box, in the **Data Source** list, select the data source view [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span>  
  
5.  <span data-ttu-id="45715-117">[**テーブル名またはビュー名**] で、[ **ProspectiveBuyer (dbo)** ] テーブルを選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45715-117">In **Table/View Name**, select the **ProspectiveBuyer (dbo)** table, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45715-118">テーブルは、 `ProspectiveBuyer` **Vtargetmail**のケーステーブルによく似ています。</span><span class="sxs-lookup"><span data-stu-id="45715-118">The `ProspectiveBuyer` table most closely resembles the **vTargetMail** case table.</span></span>  
  
## <a name="mapping-the-columns"></a><span data-ttu-id="45715-119">列のマッピング</span><span class="sxs-lookup"><span data-stu-id="45715-119">Mapping the Columns</span></span>  
 <span data-ttu-id="45715-120">入力テーブルを選択すると、列名に基づいてマイニング モデルと入力テーブルの間に既定のマッピングが作成されます。</span><span class="sxs-lookup"><span data-stu-id="45715-120">After you select the input table, Prediction Query Builder creates a default mapping between the mining model and the input table, based on the names of the columns.</span></span> <span data-ttu-id="45715-121">構造の列と外部データの列は 1 つ以上一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45715-121">At least one column from the structure must match a column in the external data.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="45715-122">モデルの精度を判断するために使用するデータには、予測可能列にマッピングできる列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="45715-122">The data that you use to determine the accuracy of the models must contain a column that can be mapped to the predictable column.</span></span> <span data-ttu-id="45715-123">そのような列が存在しない場合は、空の値で列を作成できますが、データ型が予測可能列と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="45715-123">If such a column does not exist, you can create one with empty values, but it must have the same data type as the predictable column.</span></span>  
  
#### <a name="to-map-the-inputs-to-the-model"></a><span data-ttu-id="45715-124">入力をモデルにマップするには</span><span class="sxs-lookup"><span data-stu-id="45715-124">To map the inputs to the model</span></span>  
  
1.  <span data-ttu-id="45715-125">[**マイニングモデル**] ウィンドウに接続している行を右クリックし、[**入力テーブルの選択**] ウィンドウで [**接続の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-125">Right-click the lines connecting the **Mining Model** window to the **Select Input Table** window, and select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="45715-126">すべての列をマップするわけではありません。</span><span class="sxs-lookup"><span data-stu-id="45715-126">Notice that not every column is mapped.</span></span> <span data-ttu-id="45715-127">複数の**テーブル列**のマッピングを追加します。</span><span class="sxs-lookup"><span data-stu-id="45715-127">We will add mappings for several **Table Columns**.</span></span> <span data-ttu-id="45715-128">一致する列を増やすため、現在の日付の列に基づいて新しい生年月日の列も生成します。</span><span class="sxs-lookup"><span data-stu-id="45715-128">We will also generate a new birth date column based on the current date column, so that the columns match better.</span></span>  
  
2.  <span data-ttu-id="45715-129">[**テーブル列**] で、 `Bike Buyer` セルをクリックし、ドロップダウンから [ProspectiveBuyer] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-129">Under **Table Column**, click the `Bike Buyer` cell and select ProspectiveBuyer.Unknown from the dropdown.</span></span>  
  
     <span data-ttu-id="45715-130">これにより、予測可能列 [Bike Buyer] が入力テーブルの列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="45715-130">This maps the predictable column, [Bike Buyer], to an input table column.</span></span>  
  
3.  <span data-ttu-id="45715-131">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45715-131">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="45715-132">**ソリューションエクスプローラー**で、**対象メーリング**データソースビューを右クリックし、[**ビューデザイナー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-132">In **Solution Explorer**, right-click the **Targeted Mailing** data source view and select **View Designer**.</span></span>  
  
5.  <span data-ttu-id="45715-133">ProspectiveBuyer テーブルを右クリックし、[**新しい名前付き計算**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-133">Right-click the table, ProspectiveBuyer, and select **New Named Calculation**.</span></span>  
  
6.  <span data-ttu-id="45715-134">[**名前付き計算の作成**] ダイアログボックスの [**列名**] に「」と入力 `calcAge` します。</span><span class="sxs-lookup"><span data-stu-id="45715-134">In the **Create Named Calculation** dialog box, for **Column name**, type `calcAge`.</span></span>  
  
7.  <span data-ttu-id="45715-135">[**説明**] に、「**誕生日に基づいて年齢を計算**する」と入力します。</span><span class="sxs-lookup"><span data-stu-id="45715-135">For **Description**, type **Calculate age based on birthdate**.</span></span>  
  
8.  <span data-ttu-id="45715-136">[**式**] ボックスに「 `DATEDIFF(YYYY,[BirthDate],getdate())` 」と入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45715-136">In the **Expression** box, type `DATEDIFF(YYYY,[BirthDate],getdate())` and then click **OK**.</span></span>  
  
     <span data-ttu-id="45715-137">入力テーブルには、モデル内の列に対応する**age**列がないため、この式を使用して、入力テーブルの [誕生日] 列から顧客の年齢を計算できます。</span><span class="sxs-lookup"><span data-stu-id="45715-137">Because the input table has no **Age** column corresponding to the one in the model, you can use this expression to calculate customer age from the BirthDate column in the input table.</span></span> <span data-ttu-id="45715-138">**Age**は、自転車の購入を予測するために最も影響力の高い列として識別されたため、モデルと入力テーブルの両方に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45715-138">Since **Age** was identified as the most influential column for predicting bike buying, it must exist in both the model and in the input table.</span></span>  
  
9. <span data-ttu-id="45715-139">データマイニングデザイナーで、[**マイニングモデル予測**] タブを選択し、[**接続の変更**] ウィンドウを再び開きます。</span><span class="sxs-lookup"><span data-stu-id="45715-139">In Data Mining Designer, select the **Mining Model Prediction** tab and re-open the **Modify Connections** window.</span></span>  
  
10. <span data-ttu-id="45715-140">[**テーブル列**] の下の [ **Age** ] セルをクリックし、ドロップダウンリストから [ProspectiveBuyer] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-140">Under **Table Column**, click the **Age** cell and select ProspectiveBuyer.calcAge from the dropdown.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="45715-141">一覧に列が表示されない場合は、場合によって、デザイナーに読み込まれたデータ ソース ビューの定義を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45715-141">If you do not see the column in the list, you might have to refresh the definition of the data source view that is loaded in the designer.</span></span> <span data-ttu-id="45715-142">これを行うには、[**ファイル**] メニューの [**すべてを保存**] をクリックし、デザイナーでプロジェクトを閉じてから開き直します。</span><span class="sxs-lookup"><span data-stu-id="45715-142">To do this, from the **File** menu, select **Save all**, and then close and re-open the project in the designer.</span></span>  
  
11. <span data-ttu-id="45715-143">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45715-143">Click **OK**.</span></span>  
  
## <a name="designing-the-prediction-query"></a><span data-ttu-id="45715-144">予測クエリのデザイン</span><span class="sxs-lookup"><span data-stu-id="45715-144">Designing the Prediction Query</span></span>  
  
1.  <span data-ttu-id="45715-145">[**マイニングモデル予測**] タブのツールバーにある最初のボタンは、[**デザインビューに切り替え]/[結果ビューに切り替え]/[クエリビューに切り替え**] ボタンです。</span><span class="sxs-lookup"><span data-stu-id="45715-145">The first button on the toolbar of the **Mining Model Prediction** tab is the **Switch to design view / Switch to result view / Switch to query view** button.</span></span> <span data-ttu-id="45715-146">このボタンの下矢印をクリックし、[**デザイン**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-146">Click the down arrow on this button, and select **Design**.</span></span>  
  
2.  <span data-ttu-id="45715-147">[**マイニングモデル予測**] タブのグリッドで、[**基**になる列] の最初の空白行のセルをクリックし、[**予測関数**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-147">In the grid on the **Mining Model Prediction** tab, click the cell in the first empty row in the **Source** column, and then select **Prediction Function**.</span></span>  
  
3.  <span data-ttu-id="45715-148">**予測関数**の行の [**フィールド]** 列で、を選択し `PredictProbability` ます。</span><span class="sxs-lookup"><span data-stu-id="45715-148">In the **Prediction Function** row, in the **Field** column, select `PredictProbability`.</span></span>  
  
     <span data-ttu-id="45715-149">同じ行の [**別名**] 列に「 **result of Probability**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="45715-149">In the **Alias** column of the same row, type **Probability of result**.</span></span>  
  
4.  <span data-ttu-id="45715-150">上の [**マイニングモデル**] ウィンドウで、[自転車購入者] を選択し、[**条件と引数**] セルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45715-150">From the **Mining Model** window above, select and drag [Bike Buyer] into the **Criteria/Argument** cell.</span></span>  
  
     <span data-ttu-id="45715-151">使用する場合は、[TM_Decision_Tree] を参照してください。[自転車購入者] が [**条件と引数**] セルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="45715-151">When you let go, [TM_Decision_Tree].[Bike Buyer] appears in the **Criteria/Argument** cell.</span></span>  
  
     <span data-ttu-id="45715-152">これにより、`PredictProbability` 関数の対象列を指定します。</span><span class="sxs-lookup"><span data-stu-id="45715-152">This specifies the target column for the `PredictProbability` function.</span></span> <span data-ttu-id="45715-153">関数の詳細については、「[データマイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45715-153">For more information about functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
5.  <span data-ttu-id="45715-154">[**ソース**] 列の次の空白行をクリックし、[マイニングモデルの**TM_Decision_Tree** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-154">Click the next empty row in the **Source** column, and then select **TM_Decision_Tree** mining model.</span></span>  
  
6.  <span data-ttu-id="45715-155">行の `TM_Decision_Tree` [**フィールド**] 列で、を選択し `Bike Buyer` ます。</span><span class="sxs-lookup"><span data-stu-id="45715-155">In the `TM_Decision_Tree` row, in the **Field** column, select `Bike Buyer`.</span></span>  
  
7.  <span data-ttu-id="45715-156">行の [ `TM_Decision_Tree` **条件と引数**] 列に「」と入力 `=1` します。</span><span class="sxs-lookup"><span data-stu-id="45715-156">In the `TM_Decision_Tree` row, in the **Criteria/Argument** column, type `=1`.</span></span>  
  
8.  <span data-ttu-id="45715-157">[**ソース**] 列の次の空白行をクリックし、[ **ProspectiveBuyer table**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-157">Click the next empty row in the **Source** column, and then select **ProspectiveBuyer table**.</span></span>  
  
9. <span data-ttu-id="45715-158">行の [ `ProspectiveBuyer` **フィールド**] 列で、[ **ProspectiveBuyerKey**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-158">In the `ProspectiveBuyer` row, in the **Field** column, select **ProspectiveBuyerKey**.</span></span>  
  
     <span data-ttu-id="45715-159">予測クエリに一意識別子が追加され、自転車を購入する可能性が高い顧客とそうでない顧客を特定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="45715-159">This adds the unique identifier to the prediction query so that you can identify who is and who is not likely to buy a bicycle.</span></span>  
  
10. <span data-ttu-id="45715-160">グリッドに 5 つの行を追加します。</span><span class="sxs-lookup"><span data-stu-id="45715-160">Add five more rows to the grid.</span></span> <span data-ttu-id="45715-161">行ごとに、**ソース**として [ **ProspectiveBuyer table** ] を選択し、[**フィールド]** セルに次の列を追加します。</span><span class="sxs-lookup"><span data-stu-id="45715-161">For each row, select **ProspectiveBuyer table** as the **Source** and then add the following columns in the **Field** cells:</span></span>  
  
    -   <span data-ttu-id="45715-162">calcAge</span><span class="sxs-lookup"><span data-stu-id="45715-162">calcAge</span></span>  
  
    -   <span data-ttu-id="45715-163">LastName</span><span class="sxs-lookup"><span data-stu-id="45715-163">LastName</span></span>  
  
    -   <span data-ttu-id="45715-164">FirstName</span><span class="sxs-lookup"><span data-stu-id="45715-164">FirstName</span></span>  
  
    -   <span data-ttu-id="45715-165">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="45715-165">AddressLine1</span></span>  
  
    -   <span data-ttu-id="45715-166">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="45715-166">AddressLine2</span></span>  
  
 <span data-ttu-id="45715-167">最後に、クエリを実行して結果を参照します。</span><span class="sxs-lookup"><span data-stu-id="45715-167">Finally, run the query and browse the results.</span></span>  
  
 <span data-ttu-id="45715-168">**予測クエリビルダー**には、次のコントロールも含まれます。</span><span class="sxs-lookup"><span data-stu-id="45715-168">The **Prediction Query Builder** also includes these controls:</span></span>  
  
-   <span data-ttu-id="45715-169">チェックボックス**を表示する**</span><span class="sxs-lookup"><span data-stu-id="45715-169">**Show** check box</span></span>  
  
     <span data-ttu-id="45715-170">句をデザイナーから削除せずに、句をクエリから削除することができます。</span><span class="sxs-lookup"><span data-stu-id="45715-170">Lets you remove clauses from the query without having to delete them from the designer.</span></span> <span data-ttu-id="45715-171">複雑なクエリを使用しているときに、DMX 構文のコピーとウィンドウへの貼り付けを行わずに構文を保持しようとする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="45715-171">This can be useful when you are working with complex queries and want to preserve syntax without having to copy and paste DMX into the window.</span></span>  
  
-   <span data-ttu-id="45715-172">**グループ**</span><span class="sxs-lookup"><span data-stu-id="45715-172">**Group**</span></span>  
  
     <span data-ttu-id="45715-173">選択した行の先頭に開く (左) かっこを挿入するか、現在の行の末尾に閉じる (右) かっこを挿入します。</span><span class="sxs-lookup"><span data-stu-id="45715-173">Inserts an opening (left) parentheses at the beginning of the selected line, or inserts a closing (right) parenthesis at the end of the current line.</span></span>  
  
-   <span data-ttu-id="45715-174">**AND/OR**</span><span class="sxs-lookup"><span data-stu-id="45715-174">**AND/OR**</span></span>  
  
     <span data-ttu-id="45715-175">現在の関数または現在の列の直後に、`AND` 演算子または `OR` 演算子を挿入します。</span><span class="sxs-lookup"><span data-stu-id="45715-175">Inserts the  `AND` operator or the `OR` operator immediately after the current function or column.</span></span>  
  
#### <a name="to-run-the-query-and-view-results"></a><span data-ttu-id="45715-176">クエリを実行して結果を表示するには</span><span class="sxs-lookup"><span data-stu-id="45715-176">To run the query and view results</span></span>  
  
1.  <span data-ttu-id="45715-177">[**マイニングモデル予測**] タブで、[**結果**] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="45715-177">In the **Mining Model Prediction** tab, select the **Result** button.</span></span>  
  
2.  <span data-ttu-id="45715-178">クエリを実行して結果が表示されたら、その結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="45715-178">After the query runs and the results are displayed, you can review the results.</span></span>  
  
     <span data-ttu-id="45715-179">[**マイニングモデル予測**] タブには、自転車購入者である可能性がある潜在顧客の連絡先情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45715-179">The **Mining Model Prediction** tab displays contact information for potential customers who are likely to be bike buyers.</span></span> <span data-ttu-id="45715-180">**結果列の確率**は、予測が正しいかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="45715-180">The **Probability of result** column indicates the probability of the prediction being correct.</span></span> <span data-ttu-id="45715-181">これらの結果を使用すると、メールを送信する対象となる潜在顧客を特定できます。</span><span class="sxs-lookup"><span data-stu-id="45715-181">You can use these results to determine which potential customers to target for the mailing.</span></span>  
  
3.  <span data-ttu-id="45715-182">この時点で、結果を保存できます。</span><span class="sxs-lookup"><span data-stu-id="45715-182">At this point, you can save the results.</span></span> <span data-ttu-id="45715-183">この場合、3 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="45715-183">You have three options:</span></span>  
  
    -   <span data-ttu-id="45715-184">結果内のデータ行を右クリックし、[**コピー** ] をクリックして、その値 (および列見出し) だけをクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="45715-184">Right-click a row of data in the results, and select **Copy** to save just that value (and the column heading) to the Clipboard.</span></span>  
  
    -   <span data-ttu-id="45715-185">結果内の任意の行を右クリックし、[**すべてコピー** ] を選択して、結果セット全体 (列見出しを含む) をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="45715-185">Right-click any row in the results, and select **Copy All** to copy the entire result set, including column headings, to the Clipboard.</span></span>  
  
    -   <span data-ttu-id="45715-186">[**クエリ結果の保存**] をクリックして、次のようにして結果を直接データベースに保存します。</span><span class="sxs-lookup"><span data-stu-id="45715-186">Click **Save query result** to save the results directly to a database as follows:</span></span>  
  
        1.  <span data-ttu-id="45715-187">[**データマイニングのクエリ結果の保存**] ダイアログボックスで、データソースを選択するか、新しいデータソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="45715-187">In the **Save Data Mining Query Result** dialog box, select a data source, or define a new data source.</span></span>  
  
        2.  <span data-ttu-id="45715-188">クエリの結果が保存されるテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="45715-188">Type a name for the table that will contain the query results.</span></span>  
  
        3.  <span data-ttu-id="45715-189">テーブルを作成して既存のデータソースビューに追加するには、[ **DSV に追加**] オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="45715-189">Use the option, **Add to DSV**, to create the table and add it to an existing data source view.</span></span> <span data-ttu-id="45715-190">これは、モデルのすべての関連テーブル (トレーニングデータ、予測ソースデータ、クエリ結果など) を同じデータソースビューに保持する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="45715-190">This is useful if you want to keep all related tables for a model-such as training data, prediction source data, and query results-in the same data source view.</span></span>  
  
        4.  <span data-ttu-id="45715-191">[**存在する場合は上書き**する] オプションを使用して、既存のテーブルを最新の結果に更新します。</span><span class="sxs-lookup"><span data-stu-id="45715-191">Use the option, **Overwrite if exists**, to update an existing table with the latest results.</span></span>  
  
             <span data-ttu-id="45715-192">予測クエリに列を追加した場合、予測クエリで列の名前またはデータ型を変更した場合、または保存先テーブルで ALTER ステートメントを実行した場合、このオプションを使用してテーブルを上書きする必要があります。</span><span class="sxs-lookup"><span data-stu-id="45715-192">You must use the option to overwrite the table if you have added any columns to the prediction query, changed the names or data types of any columns in the prediction query, or if you have run any ALTER statements on the destination table.</span></span>  
  
             <span data-ttu-id="45715-193">また、複数の列に同じ名前 (既定の列名の**式**など) がある場合は、名前が重複している列の別名を作成する必要があります。そうしないと、デザイナーが SQL Server に結果を保存しようとしたときにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="45715-193">Also, if multiple columns have the same name (for example, the default column name **Expression**) you must create an alias for the columns with duplicate names, or an error will be raised when the designer tries to save the results to SQL Server.</span></span> <span data-ttu-id="45715-194">SQL Server では、複数の列に同じ名前が含まれることが許可されないためです。</span><span class="sxs-lookup"><span data-stu-id="45715-194">The reason is that SQL Server does not allow multiple columns to have the same name.</span></span>  
  
             <span data-ttu-id="45715-195">詳細については、「[[データマイニングクエリ結果の保存] ダイアログボックス &#40;マイニングモデル予測ビュー&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45715-195">For more information, see [Save Data Mining Query Result Dialog Box &#40;Mining Model Prediction View&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="45715-196">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="45715-196">Next Task in Lesson</span></span>  
 [<span data-ttu-id="45715-197">構造データでのドリルスルーの使用 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="45715-197">Using Drillthrough on Structure Data &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="45715-198">参照</span><span class="sxs-lookup"><span data-stu-id="45715-198">See Also</span></span>  
 [<span data-ttu-id="45715-199">予測クエリ ビルダーを使用した予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="45715-199">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
