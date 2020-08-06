---
title: マイニングモデルでの入れ子になったテーブルのフィルター処理 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1e6ce2936a3c6763ea41999b2724c0fe8c79301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739013"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="a627e-102">マイニング モデルでの入れ子になったテーブルのフィルター処理 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="a627e-102">Filtering a Nested Table in a Mining Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="a627e-103">モデルの作成と検証が完了したら、顧客データのサブセットに焦点を絞ります。</span><span class="sxs-lookup"><span data-stu-id="a627e-103">After you have created and explored the model, you decide that you want to focus on a subset of the customer data.</span></span> <span data-ttu-id="a627e-104">たとえば、特定の品目が入っているバスケットのみを分析したり、一定期間に何も購入しなかった顧客の人口統計を分析したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a627e-104">For example, you might want to analyze only the baskets that contain a specific item, or to analyze the demographics of customers who have not purchased anything in a certain period.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="a627e-105">を使用すると、マイニング モデルで使用されるデータをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="a627e-105">provides the ability to filter the data that is used in a mining model.</span></span> <span data-ttu-id="a627e-106">この機能は、別のデータを使用するために新しいデータソースビューを設定する必要がないため、便利です。</span><span class="sxs-lookup"><span data-stu-id="a627e-106">This feature is useful because you do not need to set up a new data source view to use different data.</span></span> <span data-ttu-id="a627e-107">「基本的なデータ マイニング チュートリアル」では、ケース テーブルに条件を適用することでフラット テーブルのデータをフィルター処理する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="a627e-107">In the Basic Data Mining Tutorial, you learned how to filter data from a flat table by applying conditions to the case table.</span></span> <span data-ttu-id="a627e-108">ここでは、入れ子になったテーブルに適用するフィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="a627e-108">In this task, you create a filter that applies to a nested table.</span></span>  
  
## <a name="filters-on-nested-vs-case-tables"></a><span data-ttu-id="a627e-109">入れ子になったテーブルとケース テーブルでのフィルターの違い</span><span class="sxs-lookup"><span data-stu-id="a627e-109">Filters on Nested vs. Case Tables</span></span>  
 <span data-ttu-id="a627e-110">データ ソース ビューにケース テーブルと入れ子になったテーブルが含まれている場合は、アソシエーション モデルで使用されているデータ ソース ビューと同様に、ケース テーブルの値、入れ子になったテーブルでの値の有無、または両方の組み合わせをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="a627e-110">If your data source view contains a case table and a nested table, like the data source view used in the Association model, you can filter on values from the case table, the presence or absence of a value in the nested table, or some combination of both.</span></span>  
  
 <span data-ttu-id="a627e-111">ここでは、まずアソシエーション モデルのコピーを作成し、関連する新しいモデルに IncomeGroup 属性と Region 属性を追加して、ケース テーブルでこれらの属性をフィルター処理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a627e-111">In this task, you will first make a copy of the Association model and then add the IncomeGroup and Region attributes to the new related model, so that you can filter on those attributes in the case table.</span></span>  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a><span data-ttu-id="a627e-112">アソシエーション モデルのコピーを作成して変更するには</span><span class="sxs-lookup"><span data-stu-id="a627e-112">To create and modify a copy of the Association model</span></span>  
  
1.  <span data-ttu-id="a627e-113">の [**マイニングモデル**] タブで、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] `Association` モデルを右クリックし、[**新しいマイニングモデル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-113">In the **Mining Models** tab of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click the `Association` model, and select **New Mining Model**.</span></span>  
  
2.  <span data-ttu-id="a627e-114">[**モデル名**] に「」と入力 `Association Filtered` します。</span><span class="sxs-lookup"><span data-stu-id="a627e-114">For **Model Name**, type `Association Filtered`.</span></span> <span data-ttu-id="a627e-115">[**アルゴリズム名**] で、[ **Microsoft アソシエーションルール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a627e-115">For **Algorithm Name**, select **Microsoft Association Rules**.</span></span> <span data-ttu-id="a627e-116">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-116">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="a627e-117">アソシエーションのフィルター選択されたモデルの列で、IncomeGroup 行をクリックし、値を**Ignore**から**Input**に変更します。</span><span class="sxs-lookup"><span data-stu-id="a627e-117">In the column for the Association Filtered model, click the IncomeGroup row and change the value from **Ignore** to **Input**.</span></span>  
  
 <span data-ttu-id="a627e-118">次に、新しいアソシエーション モデルでケース テーブルに対してフィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="a627e-118">Next, you will create a filter on the case table in the new association model.</span></span> <span data-ttu-id="a627e-119">このフィルターでは、対象の地域または収入レベルの顧客のみがモデルに渡されます。</span><span class="sxs-lookup"><span data-stu-id="a627e-119">The filter will pass to the model only the customers in the target region or with the target income level.</span></span> <span data-ttu-id="a627e-120">さらに、買い物かごに 1 つ以上の品目が入っていた顧客のみがモデルで使用されるように指定する 2 番目のフィルター条件を追加します。</span><span class="sxs-lookup"><span data-stu-id="a627e-120">Then, you will add a second set of filter conditions to specify that the model uses only customers whose shopping baskets contained at least one item.</span></span>  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a><span data-ttu-id="a627e-121">マイニング モデルにフィルターを追加するには</span><span class="sxs-lookup"><span data-stu-id="a627e-121">To add a filter to a mining model</span></span>  
  
1.  <span data-ttu-id="a627e-122">[**マイニングモデル**] タブで、フィルター処理されたモデルの関連付けを右クリックし、[**モデルフィルターの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-122">In the **Mining Models** tab, right-click the model Association Filtered, and select **Set Model Filter**.</span></span>  
  
2.  <span data-ttu-id="a627e-123">**[モデル フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** ボックスのグリッドの先頭行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-123">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
3.  <span data-ttu-id="a627e-124">[**マイニング構造列**] ボックスで、[IncomeGroup] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a627e-124">In the **Mining Structure Column** text box, select IncomeGroup.</span></span>  
  
     <span data-ttu-id="a627e-125">テキスト ボックスの左側のアイコンが変化して、選択されたアイテムが列であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="a627e-125">The icon at the left side of the text box changes to indicate that the selected item is a column.</span></span>  
  
4.  <span data-ttu-id="a627e-126">[**演算子**] ボックスをクリックし、 **=** 一覧から演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="a627e-126">Click the **Operator** text box and select the **=** operator from the list.</span></span>  
  
5.  <span data-ttu-id="a627e-127">[**値**] テキストボックスをクリックし、ボックスに「」と入力し `High` ます。</span><span class="sxs-lookup"><span data-stu-id="a627e-127">Click the **Value** text box, and type `High` in the box.</span></span>  
  
6.  <span data-ttu-id="a627e-128">グリッドの次の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-128">Click the next row in the grid.</span></span>  
  
7.  <span data-ttu-id="a627e-129">グリッドの次の行の [ **AND** ] テキストボックスをクリックし、[ **or**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a627e-129">Click the **AND/OR** text box in the next row of the grid and select **OR**.</span></span>  
  
8.  <span data-ttu-id="a627e-130">[**マイニング構造列**] ボックスで、[IncomeGroup] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a627e-130">In the **Mining Structure Column** text box, select IncomeGroup.</span></span> <span data-ttu-id="a627e-131">[**値**] テキストボックスに「」と入力 `Moderate` します。</span><span class="sxs-lookup"><span data-stu-id="a627e-131">In the **Value** text box, type `Moderate`.</span></span>  
  
     <span data-ttu-id="a627e-132">作成したフィルター条件が [**式**] テキストボックスに自動的に追加され、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="a627e-132">The filter condition that you created is automatically added to the **Expression** text box, and should appears as follows:</span></span>  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. <span data-ttu-id="a627e-133">グリッド内の次の行をクリックし、既定値としての演算子**をそのままにします。**</span><span class="sxs-lookup"><span data-stu-id="a627e-133">Click the next row in the grid, leaving the operator as the default, **AND**.</span></span>  
  
10. <span data-ttu-id="a627e-134">[**演算子**] には、既定値の [ **Contains**] をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="a627e-134">For **Operator**, leave the default value, **Contains**.</span></span> <span data-ttu-id="a627e-135">[**値**] テキストボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-135">Click the **Value** text box.</span></span>  
  
11. <span data-ttu-id="a627e-136">[**フィルター** ] ダイアログボックスの [**マイニング構造列**] の最初の行で、[] を選択し `Model` ます。</span><span class="sxs-lookup"><span data-stu-id="a627e-136">In the **Filter** dialog box, in the first row under **Mining Structure Column**, select `Model`.</span></span>  
  
12. <span data-ttu-id="a627e-137">[**演算子**] で [ **IS not NULL**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a627e-137">For **Operator**, select **IS NOT NULL**.</span></span> <span data-ttu-id="a627e-138">[**値**] テキストボックスは空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="a627e-138">Leave the **Value** text box blank.</span></span> <span data-ttu-id="a627e-139">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-139">Click **OK**.</span></span>  
  
     <span data-ttu-id="a627e-140">[**モデルフィルター** ] ダイアログボックスの [**式**] ボックスのフィルター条件は、入れ子になったテーブルに新しい条件が含まれるように自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="a627e-140">The filter condition in the **Expression** text box of the **Model Filter** dialog box is automatically updated to include the new condition on the nested table.</span></span> <span data-ttu-id="a627e-141">完成した式は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a627e-141">The completed expression is as follows:</span></span>  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a><span data-ttu-id="a627e-142">ドリルスルーを有効にして、フィルター選択されたモデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="a627e-142">To enable drillthrough and to process the filtered model</span></span>  
  
1.  <span data-ttu-id="a627e-143">[**マイニングモデル**] タブで、 `Association Filtered` モデルを右クリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-143">In the **Mining Models** tab, right-click the `Association Filtered` model, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a627e-144">**Allowdrillthrough スルー**プロパティを**True**に変更します。</span><span class="sxs-lookup"><span data-stu-id="a627e-144">Change the **AllowDrillThrough** property to **True**.</span></span>  
  
3.  <span data-ttu-id="a627e-145">`Association Filtered`マイニングモデルを右クリックし、[**モデルの処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a627e-145">Right-click the `Association Filtered` mining model, and select **Process Model**.</span></span>  
  
4.  <span data-ttu-id="a627e-146">エラーメッセージで [**はい]** をクリックして、新しいモデルをデータベースに配置し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a627e-146">Click **Yes** in the error message to deploy the new model to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
5.  <span data-ttu-id="a627e-147">[**マイニング構造の処理**] ダイアログボックスで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a627e-147">In the **Process Mining Structure** dialog box, click **Run**.</span></span>  
  
6.  <span data-ttu-id="a627e-148">処理が完了したら、[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを終了し、もう一度 [**閉じる**] をクリックして [**マイニング構造の処理**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a627e-148">When processing is complete click **Close** to exit the **Process Progress** dialog box, and click **Close** again to exit the **Process Mining Structure** dialog box.</span></span>  
  
 <span data-ttu-id="a627e-149">Microsoft 汎用コンテンツ ツリー ビューアーで NODE_SUPPORT の値を参照すると、フィルター選択されたモデルに含まれているケースの数が元のモデルよりも少ないことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a627e-149">You can verify by using the Microsoft Generic Content Tree viewer and looking at the value for NODE_SUPPORT that the filtered model contains fewer cases than the original model.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a627e-150">解説</span><span class="sxs-lookup"><span data-stu-id="a627e-150">Remarks</span></span>  
 <span data-ttu-id="a627e-151">ここで作成した入れ子になったテーブルのフィルターでは、そのテーブルに少なくとも 1 つの行があるかどうかのみがチェックされますが、特定の製品の有無を確認するフィルター条件を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a627e-151">The nested table filter that you just created checks only for the presence of at least one row in the nested table; however, you can also create filter conditions that check for the presence of specific products.</span></span>  <span data-ttu-id="a627e-152">たとえば、次のようなフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a627e-152">For example, you could create the following filter:</span></span>  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 <span data-ttu-id="a627e-153">このステートメントでは、ケース テーブルの顧客を水筒 (water bottle) の購入者のみに制限しています。</span><span class="sxs-lookup"><span data-stu-id="a627e-153">This statement means that you are restricting the customers from the case table to only those who have purchased a water bottle.</span></span> <span data-ttu-id="a627e-154">ただし、入れ子になったテーブルの属性数には制限がないため、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では選択できる値の一覧が表示されません。</span><span class="sxs-lookup"><span data-stu-id="a627e-154">However, because the number of nested table attributes is potentially unlimited, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not supply a list of possible values from which to select.</span></span> <span data-ttu-id="a627e-155">代わりに、値を正確に入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a627e-155">Instead, you must type the exact value.</span></span>  
  
 <span data-ttu-id="a627e-156">[クエリの**編集**] をクリックして、フィルター式を手動で変更できます。</span><span class="sxs-lookup"><span data-stu-id="a627e-156">You can click **Edit Query** to manually change the filter expression.</span></span> <span data-ttu-id="a627e-157">ただし、フィルター式の一部を手動で変更すると、グリッドが無効になり、その後はテキスト編集モードのみでフィルター式を操作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a627e-157">However, if you change any part of a filter expression manually, the grid will be disabled and thereafter you must work with the filter expression in text edit mode only.</span></span> <span data-ttu-id="a627e-158">グリッド編集モードに戻すには、フィルター式を消去して最初からやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a627e-158">To restore grid editing mode, you must clear the filter expression and start over.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a627e-159">入れ子になったテーブル フィルターで LIKE 演算子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a627e-159">You cannot use the LIKE operator in a nested table filter.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a627e-160">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="a627e-160">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a627e-161">&#41;の関連付けの予測 &#40;中級者向けデータマイニングチュートリアル</span><span class="sxs-lookup"><span data-stu-id="a627e-161">Predicting Associations &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="a627e-162">参照</span><span class="sxs-lookup"><span data-stu-id="a627e-162">See Also</span></span>  
 <span data-ttu-id="a627e-163">[モデルフィルターの構文と例 &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a627e-163">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="a627e-164">マイニング モデルのフィルター &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="a627e-164">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
