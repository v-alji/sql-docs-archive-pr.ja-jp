---
title: マイニングモデルのフィルター (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- filter syntax [data mining]
- models [Analysis Services], filtering
- filters [data mining]
- filtering data [Analysis Services]
ms.assetid: 0f29c19c-4be3-4bc7-ab60-f4130a10d59c
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4e2c82c977f734948e107773e439ca154f6cfdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632779"
---
# <a name="filters-for-mining-models-analysis-services---data-mining"></a><span data-ttu-id="84733-102">マイニング モデルのフィルター選択 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="84733-102">Filters for Mining Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="84733-103">データに基づくモデル フィルターは、マイニング構造内のデータのサブセットを使用するマイニング モデルを作成するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="84733-103">Data-based model filtering helps you create mining models that use subsets of data in a mining structure.</span></span> <span data-ttu-id="84733-104">フィルターを使用すると、包括的なデータ ソース ビューに基づいて 1 つのマイニング構造を作成できるため、マイニング構造とデータ ソースを柔軟に設計できます。</span><span class="sxs-lookup"><span data-stu-id="84733-104">Filtering gives you flexibility when you design your mining structures and data sources, because you can create a single mining structure, based on a comprehensive data source view.</span></span> <span data-ttu-id="84733-105">つまり、さまざまなモデルのトレーニングとテストを行う場合に、データの各サブセットに対して個別の構造と関連モデルを作成する代わりに、データの一部だけを使用するためのフィルターを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="84733-105">You can then create filters to use only a part of that data for training and testing a variety of models, instead of building a different structure and related model for each subset of data.</span></span>  
  
 <span data-ttu-id="84733-106">たとえば、Customers テーブルと関連テーブルに、データ ソース ビューを定義します。</span><span class="sxs-lookup"><span data-stu-id="84733-106">For example, you define the data source view on the Customers table and related tables.</span></span> <span data-ttu-id="84733-107">次に、必要とするすべてのフィールドを含むマイニング構造を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="84733-107">Next, you define a single mining structure that includes all the fields you need.</span></span> <span data-ttu-id="84733-108">最後に、Region などの特定の顧客属性に基づいてフィルター処理されるモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="84733-108">Finally, you create a model that is filtered on a particular customer attribute, such as Region.</span></span> <span data-ttu-id="84733-109">その後、このモデルをコピーし、フィルター条件を変更するだけで、別の地域に基づく新しいモデルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="84733-109">You can then easily make a copy of that model, and change just the filter condition to generate a new model based on a different region.</span></span>  
  
 <span data-ttu-id="84733-110">この機能が役立つ実際的なシナリオには、次のような場合があります。</span><span class="sxs-lookup"><span data-stu-id="84733-110">Some real-life scenarios where you might benefit from this feature include the following:</span></span>  
  
-   <span data-ttu-id="84733-111">性別や地域など、複数の不連続値に対して個別のモデルを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="84733-111">Creating separate models for discrete values such as gender, regions, and so forth.</span></span> <span data-ttu-id="84733-112">たとえば、衣料品店では、1 つのデータ ソースにすべての顧客の売上データが含まれていても、顧客の統計区分を使用して性別に基づく個別のモデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="84733-112">For example, a clothing store might use customer demographics to build separate models by gender, even though the sales data comes from a single data source for all customers.</span></span>  
  
-   <span data-ttu-id="84733-113">20 ～ 30 才、20 ～ 40 才、20 ～ 25 才など、同じデータの複数のグループ分けを作成およびテストして、モデルを試す場合。</span><span class="sxs-lookup"><span data-stu-id="84733-113">Experimenting with models by creating and then testing multiple groupings of the same data, such as ages 20-30 vs. ages 20-40 vs. ages 20-25.</span></span>  
  
-   <span data-ttu-id="84733-114">特定の品目を 2 個以上購入した顧客のケースのみをモデルに含めるようにするなど、入れ子になったテーブルの内容に複雑なフィルターを指定する場合。</span><span class="sxs-lookup"><span data-stu-id="84733-114">Specifying complex filters on nested table contents, such as requiring that a case be included in the model only if the customer has purchased at least two of a particular item.</span></span>  
  
 <span data-ttu-id="84733-115">ここでは、マイニング モデルのフィルターを作成、使用、および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="84733-115">This section explains how to build, use, and manage filters on mining models.</span></span>  
  
## <a name="creating-model-filters"></a><span data-ttu-id="84733-116">モデル フィルターの作成</span><span class="sxs-lookup"><span data-stu-id="84733-116">Creating Model Filters</span></span>  
 <span data-ttu-id="84733-117">フィルターは、次の方法で作成および適用できます。</span><span class="sxs-lookup"><span data-stu-id="84733-117">You can create and apply filters in the following ways:</span></span>  
  
-   <span data-ttu-id="84733-118">データ マイニング デザイナーの **[マイニング モデル]** タブで、フィルター エディターのダイアログ ボックスを利用して条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="84733-118">Using the **Mining Models** tab in Data Mining Designer to build conditions with the help of filter editor dialog boxes.</span></span>  
  
-   <span data-ttu-id="84733-119">マイニングモデルのプロパティにフィルター式を直接入力し `Filter` ます。</span><span class="sxs-lookup"><span data-stu-id="84733-119">Typing a filter expression directly into the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="84733-120">AMO を使用して、モデルのフィルター条件をプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="84733-120">Setting filter conditions on a model programmatically, by using AMO.</span></span>  
  
### <a name="creating-model-filters-using-data-mining-designer"></a><span data-ttu-id="84733-121">データ マイニング デザイナーによるモデル フィルターの作成</span><span class="sxs-lookup"><span data-stu-id="84733-121">Creating Model Filters using Data Mining Designer</span></span>  
 <span data-ttu-id="84733-122">データ マイニング デザイナーでは、マイニング モデルの `Filter` プロパティを変更することによってモデルをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="84733-122">You filter a model in Data Mining Designer by changing the `Filter` property of the mining model.</span></span> <span data-ttu-id="84733-123">**[プロパティ]** ペインにフィルター式を直接入力することも、フィルターのダイアログ ボックスを開いて条件を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="84733-123">You can either type a filter expression directly into the **Properties** pane, or you can open a filter dialog box to build conditions.</span></span>  
  
 <span data-ttu-id="84733-124">フィルターのダイアログ ボックスは 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="84733-124">There are two filter dialog boxes.</span></span> <span data-ttu-id="84733-125">最初のダイアログ ボックスでは、ケース テーブルに適用する条件を作成できます。</span><span class="sxs-lookup"><span data-stu-id="84733-125">The first lets you create conditions that are applied to the case table.</span></span> <span data-ttu-id="84733-126">データ ソースに複数のテーブルが含まれる場合は、まずテーブルを選択してから列を選択し、その列に適用する演算子と条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="84733-126">If the data source contains multiple tables, first you select a table, and then you select a column and specify operators and conditions that apply to that column.</span></span> <span data-ttu-id="84733-127">演算子を使用すると、複数の条件をリンクでき `AND` / `OR` ます。</span><span class="sxs-lookup"><span data-stu-id="84733-127">You can link multiple conditions by using `AND`/`OR` operators.</span></span> <span data-ttu-id="84733-128">値の定義に使用できる演算子は、列に含まれている値が不連続値か連続値かによって異なります。</span><span class="sxs-lookup"><span data-stu-id="84733-128">The operators that are available for defining values depend on whether the column contains discrete or continuous values.</span></span> <span data-ttu-id="84733-129">たとえば、連続値には、`greater than` 演算子および `less than` 演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="84733-129">For example, with continuous values, you can use `greater than` and `less than` operators.</span></span> <span data-ttu-id="84733-130">一方、不連続値に対しては、`= (equal to)` 演算子、`!= (not equal to)` 演算子、および `is null` 演算子のみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="84733-130">However, for discrete values, you can only use `= (equal to)`, `!= (not equal to)`, and `is null` operators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84733-131">`LIKE` キーワードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="84733-131">The `LIKE` keyword is not supported.</span></span> <span data-ttu-id="84733-132">複数の不連続属性を含める場合は、個々の条件を作成し、それらを `OR` 演算子で結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84733-132">If you want to include multiple discrete attributes, you must create separate conditions and link them by using the `OR` operator.</span></span>  
  
 <span data-ttu-id="84733-133">条件が複雑な場合、2 番目のフィルター ダイアログ ボックスを使用して、一度に 1 つのテーブルを処理するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="84733-133">If the conditions are complex, you can use the second filter dialog box to work with one table at a time.</span></span> <span data-ttu-id="84733-134">2 番目のフィルター ダイアログ ボックスを閉じると、式が評価された後、ケース テーブルの他の列で設定されたフィルター条件と結合されます。</span><span class="sxs-lookup"><span data-stu-id="84733-134">When you close the second filter dialog box, the expression is evaluated and then combined with filter conditions that have been set on other columns in the case table.</span></span>  
  
### <a name="creating-filters-on-nested-tables"></a><span data-ttu-id="84733-135">入れ子になったテーブルに対するフィルターの作成</span><span class="sxs-lookup"><span data-stu-id="84733-135">Creating Filters on Nested Tables</span></span>  
 <span data-ttu-id="84733-136">入れ子になったテーブルがデータ ソース ビューに含まれている場合は、2 番目のフィルター ダイアログ ボックスを使用して、入れ子になったテーブル内の行に対する条件を作成できます。</span><span class="sxs-lookup"><span data-stu-id="84733-136">If the data source view contains nested tables, you can use the second filter dialog box to build conditions on the rows in the nested tables.</span></span>  
  
 <span data-ttu-id="84733-137">たとえば、顧客に関連したケース テーブルがあり、入れ子になったテーブルに顧客が購入した製品が表示されている場合、入れ子になったテーブルのフィルターで `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`という構文を使用すると、特定の品目を購入した顧客を選択するフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="84733-137">For example, if your case table is related to customers, and the nested table shows the products that a customer has purchased, you can create a filter for customers who have purchased particular items by using the following syntax in the nested table filter: `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`.</span></span>  
  
 <span data-ttu-id="84733-138">また、`EXISTS` または `NOT EXISTS` のキーワードとサブクエリを使用すると、入れ子になったテーブルに特定の値があるかどうかに基づいてフィルター処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="84733-138">You can also filter on the existence of a particular value in the nested table by using the `EXISTS` or `NOT EXISTS` keywords and a subquery.</span></span> <span data-ttu-id="84733-139">これにより、 `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`のような条件を作成できます。</span><span class="sxs-lookup"><span data-stu-id="84733-139">This lets you create conditions such as `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`.</span></span> <span data-ttu-id="84733-140">入れ子になったテーブルに値 `EXISTS SELECT(<subquery>)` を持つ行が 1 つ以上含まれている場合、`Water Bottle` から `true` が返されます。</span><span class="sxs-lookup"><span data-stu-id="84733-140">The `EXISTS SELECT(<subquery>)` returns `true` if the nested table contains at least one row that includes the value, `Water Bottle`.</span></span>  
  
 <span data-ttu-id="84733-141">ケース テーブルに対する条件と入れ子になったテーブルに対する条件は、結合することができます。</span><span class="sxs-lookup"><span data-stu-id="84733-141">You can combine conditions on the case table with conditions on the nested table.</span></span> <span data-ttu-id="84733-142">たとえば、次の構文には、ケース テーブルに対する条件 (`Age > 30` )、入れ子になったテーブルに対するサブクエリ (`EXISTS (SELECT * FROM Products)`)、および入れ子になったテーブルに対する複数の条件 (`WHERE ProductName='Milk'  AND Quantity>2`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="84733-142">For example, the following syntax includes a condition on the case table (`Age > 30` ), a subquery on the nested table (`EXISTS (SELECT * FROM Products)`), and multiple conditions on the nested table (`WHERE ProductName='Milk'  AND Quantity>2`) ).</span></span>  
  
```  
(Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity>2) )  
```  
  
 <span data-ttu-id="84733-143">フィルターの作成が完了したら、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]によってフィルター テキストが評価され、DMX 式に変換された後、モデルと共に保存されます。</span><span class="sxs-lookup"><span data-stu-id="84733-143">When you have finished building the filter, the filter text is evaluated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], translated to a DMX expression, and then saved with the model.</span></span>  
  
 <span data-ttu-id="84733-144">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のフィルター ダイアログ ボックスの使用方法については、「 [マイニング モデルへのフィルターの適用](apply-a-filter-to-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84733-144">For instructions on how to use the filter dialog boxes in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
## <a name="managing-mining-model-filters"></a><span data-ttu-id="84733-145">マイニング モデルのフィルターの管理</span><span class="sxs-lookup"><span data-stu-id="84733-145">Managing Mining Model Filters</span></span>  
 <span data-ttu-id="84733-146">データに基づくモデル フィルターを使用すると、同一の構造に基づく複数のモデルを簡単に作成できるため、マイニング構造とマイニング モデルの管理作業が大幅に簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="84733-146">Data-based model filtering greatly simplifies the task of managing mining structures and mining models, because you can easily create multiple models that are based on the same structure.</span></span> <span data-ttu-id="84733-147">既存のマイニング モデルをすばやくコピーして、フィルター条件だけを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="84733-147">You can also quickly make copies of existing mining models and then change only the filter condition.</span></span> <span data-ttu-id="84733-148">ただし、フィルターは混乱を招くこともあります。</span><span class="sxs-lookup"><span data-stu-id="84733-148">However, filters can lead to some confusion.</span></span>  
  
 <span data-ttu-id="84733-149">ここでは、マイニング モデルに対するフィルターを管理し解釈する方法について、よくされる質問とその回答を示します。</span><span class="sxs-lookup"><span data-stu-id="84733-149">Here are some frequently asked questions about how to manage and interpret filters on mining models:</span></span>  
  
### <a name="how-can-i-tell-whether-a-filter-is-being-used"></a><span data-ttu-id="84733-150">フィルターが使用されているかどうか確認する方法は?</span><span class="sxs-lookup"><span data-stu-id="84733-150">How can I tell whether a filter is being used?</span></span>  
 <span data-ttu-id="84733-151">フィルターがモデルに適用されているかどうか判断する方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="84733-151">There are multiple ways to determine whether a filter is applied to a model:</span></span>  
  
-   <span data-ttu-id="84733-152">デザイナーで、[**マイニングモデル**] タブをクリックし、[**プロパティ**] を開いて、 `Filter` マイニングモデルのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="84733-152">In the designer, click the **Mining Models** tab, open **Properties**, and view the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="84733-153">DMV (DMSCHEMA_MINING_MODELS) はフィルターのテキストを含む列を出力します。</span><span class="sxs-lookup"><span data-stu-id="84733-153">The DMV, DMSCHEMA_MINING_MODELS, outputs a column that contains the text of the filter.</span></span> <span data-ttu-id="84733-154">DMV に対して次のクエリを使用して、モデルとフィルターの名前を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="84733-154">You can use the following query on a DMV to return the names of models and their filters:</span></span>  
  
    ```  
    SELECT MODEL_NAME, [FILTER]   
    FROM $SYSTEM.DMSCHEMA_MINING_MODELS  
  
    ```  
  
-   <span data-ttu-id="84733-155">AMO で MiningModel オブジェクトの Filter プロパティの値を取得するか、XMLA で Filter 要素を検査することができます。</span><span class="sxs-lookup"><span data-stu-id="84733-155">You can get the value of the Filter property of the MiningModel object in AMO, or inspect the Filter element in XMLA.</span></span>  
  
 <span data-ttu-id="84733-156">フィルターの内容を反映するように、モデルの名前付け規則を決めることもできます。</span><span class="sxs-lookup"><span data-stu-id="84733-156">You might also establish a naming convention for models to reflect the contents of the filter.</span></span> <span data-ttu-id="84733-157">こうすると、関連する複数のモデルどうしを区別しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="84733-157">This can make it easier to tell related models apart.</span></span>  
  
### <a name="how-can-i-save-a-filter"></a><span data-ttu-id="84733-158">フィルターを保存する方法は?</span><span class="sxs-lookup"><span data-stu-id="84733-158">How can I save a filter?</span></span>  
 <span data-ttu-id="84733-159">フィルター式はスクリプトとして保存され、関連付けられたマイニング モデルまたは入れ子になったテーブルと共に格納されます。</span><span class="sxs-lookup"><span data-stu-id="84733-159">The filter expression is saved as a script that is stored with the associated mining model or nested table.</span></span> <span data-ttu-id="84733-160">フィルター テキストを削除した場合、復元するにはフィルター式を手動で再作成するしかありません。</span><span class="sxs-lookup"><span data-stu-id="84733-160">If you delete the filter text, it can only be restored by manually re-creating the filter expression.</span></span> <span data-ttu-id="84733-161">このため、複雑なフィルター式を作成する場合は、フィルター テキストのバックアップ コピーを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="84733-161">Therefore, if you create complex filter expressions, you should create a backup copy of the filter text.</span></span>  
  
### <a name="why-cant-i-see-any-effects-from-the-filter"></a><span data-ttu-id="84733-162">フィルターの効果を確認できないのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="84733-162">Why can't I see any effects from the filter?</span></span>  
 <span data-ttu-id="84733-163">フィルター式の変更や追加を行った場合、フィルターの効果を確認するには、構造およびモデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84733-163">Whenever you change or add a filter expression, you must reprocess the structure and model before you can view the effects of the filter.</span></span>  
  
### <a name="why-do-i-see-filtered-attributes-in-prediction-query-results"></a><span data-ttu-id="84733-164">フィルター選択された属性が予測クエリの結果に表示されるのはなぜですか?</span><span class="sxs-lookup"><span data-stu-id="84733-164">Why do I see filtered attributes in prediction query results?</span></span>  
 <span data-ttu-id="84733-165">フィルターをモデルに適用すると、フィルターはモデルをトレーニングする際に使用するケースの選択にのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="84733-165">When you apply a filter to a model, it affects only the selection of cases used for training the model.</span></span> <span data-ttu-id="84733-166">フィルターはモデルにとって既知の属性には影響しません。また、データ ソースに存在するデータを変更したり抑制することもありません。</span><span class="sxs-lookup"><span data-stu-id="84733-166">The filter does not affect the attributes known to the model, or change or suppress data that is present in the data source.</span></span> <span data-ttu-id="84733-167">その結果、モデルに対するクエリは、その他の種類のケースに関する予測を返すことができ、モデルで使用される値のドロップダウン リストには、フィルターによって除外された属性値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84733-167">As a result, queries against the model can return predictions for other types of cases, and dropdown lists of values used by the model might show attribute values excluded by the filter.</span></span>  
  
 <span data-ttu-id="84733-168">たとえば、20 ～ 30 歳の女性が関係するケースだけを使用して [Bike Buyer] モデルをトレーニングするとします。</span><span class="sxs-lookup"><span data-stu-id="84733-168">For example, suppose you train the [Bike Buyer] model using only cases involving women aged 20-30.</span></span> <span data-ttu-id="84733-169">その場合でも、自転車を購入する男性の確率を予測する予測クエリを実行したり、年齢が 30 ～ 40 歳の女性の結果を予測することができます。</span><span class="sxs-lookup"><span data-stu-id="84733-169">You can still run a prediction query that predicts the probability of a man buying a bike, or predict the outcome for a woman aged 30-40.</span></span> <span data-ttu-id="84733-170">これは、データ ソースに存在する属性と値は理論的に可能な項目を定義し、ケースはトレーニングに使用される実際に発生した項目を定義するためです。</span><span class="sxs-lookup"><span data-stu-id="84733-170">That is because the attributes and values present in the data source define what is theoretically possible, while the cases define the occurrences used for training.</span></span> <span data-ttu-id="84733-171">ただし、トレーニング データにターゲット値を持つケースが含まれないため、このクエリは非常に小さな確率を返します。</span><span class="sxs-lookup"><span data-stu-id="84733-171">However, these queries would return very small probabilities, because the training data does not contain any cases with the target values.</span></span>  
  
 <span data-ttu-id="84733-172">モデルの属性値を完全に隠すか匿名化する必要がある場合は、さまざまな選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="84733-172">If you need to completely hide or anonymize attribute values in the model, there are various options:</span></span>  
  
-   <span data-ttu-id="84733-173">入力されるデータに、データ ソース ビューまたはリレーショナル データ ソースの定義の一部としてフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="84733-173">Filter the incoming data as part of the definition of the data source view, or in the relational data source.</span></span>  
  
-   <span data-ttu-id="84733-174">属性値をマスクまたはエンコードします。</span><span class="sxs-lookup"><span data-stu-id="84733-174">Mask or encode the attribute value.</span></span>  
  
-   <span data-ttu-id="84733-175">除外された値をマイニング構造定義の一部としてカテゴリに折りたたみます。</span><span class="sxs-lookup"><span data-stu-id="84733-175">Collapse excluded values into a category as part of the mining structure definition.</span></span>  
  
## <a name="related-resources"></a><span data-ttu-id="84733-176">関連リソース</span><span class="sxs-lookup"><span data-stu-id="84733-176">Related Resources</span></span>  
 <span data-ttu-id="84733-177">フィルター構文の詳細およびフィルター式の例については、「 [モデル フィルターの構文と例 (Analysis Services - データ マイニング)](model-filter-syntax-and-examples-analysis-services-data-mining.md)という構文を使用すると、特定の品目を購入した顧客を選択するフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="84733-177">For more information about filter syntax, and examples of filter expressions, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="84733-178">マイニング モデルのテスト時にモデル フィルターを使用する方法については、「 [精度チャートの種類の選択とグラフのオプションの設定](choose-an-accuracy-chart-type-and-set-chart-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84733-178">For information about how to use model filters when you are testing a mining model, see [Choose an Accuracy Chart Type and Set Chart Options](choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84733-179">参照</span><span class="sxs-lookup"><span data-stu-id="84733-179">See Also</span></span>  
 <span data-ttu-id="84733-180">[モデルフィルターの構文と例 &#40;Analysis Services データマイニング&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="84733-180">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="84733-181">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="84733-181">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  
