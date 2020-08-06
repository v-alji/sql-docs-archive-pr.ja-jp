---
title: マイニングモデルへのフィルターの適用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filters [data mining]
- filtering input rows [Analysis Services]
- filtering data [Analysis Services]
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
author: minewiskan
ms.author: owend
ms.openlocfilehash: d9f3147c36e69d9c2249d5bf6d1ba201799c6e27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643023"
---
# <a name="apply-a-filter-to-a-mining-model"></a><span data-ttu-id="60a66-102">マイニング モデルへのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="60a66-102">Apply a Filter to a Mining Model</span></span>
  <span data-ttu-id="60a66-103">入れ子になったテーブルがマイニング構造に含まれている場合は、ケース テーブル、入れ子になったテーブル、またはその両方にフィルターを適用できます。</span><span class="sxs-lookup"><span data-stu-id="60a66-103">If your mining structure contains a nested table, you can apply a filter to the case table, the nested table, or both.</span></span>  
  
 <span data-ttu-id="60a66-104">次の手順は、ケース フィルター、入れ子になったテーブル行に適用するフィルターの両方を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="60a66-104">The following procedure demonstrates how to create both kinds of filters: case filters, and filters on the nested table rows.</span></span>  
  
 <span data-ttu-id="60a66-105">ケース テーブルの条件は、収入が 30000 ～ 40000 である顧客に限定することです。</span><span class="sxs-lookup"><span data-stu-id="60a66-105">The condition on the case table restricts customers to those with income between 30000 and 40000.</span></span> <span data-ttu-id="60a66-106">入れ子になったテーブルの条件は、特定の品目を購入していない顧客に限定することです。</span><span class="sxs-lookup"><span data-stu-id="60a66-106">The condition on the nested table restricts the customers to those who did not purchase a particular item.</span></span>  
  
 <span data-ttu-id="60a66-107">この例で作成された、完全なフィルター条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="60a66-107">The complete filter condition created in this example is as follows:</span></span>  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### <a name="to-create-a-case-filter-on-a-mining-model"></a><span data-ttu-id="60a66-108">マイニング モデルに対してケース フィルターを作成するには</span><span class="sxs-lookup"><span data-stu-id="60a66-108">To create a case filter on a mining model</span></span>  
  
1.  <span data-ttu-id="60a66-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、フィルターを適用するマイニング モデルが含まれているマイニング構造をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60a66-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model you want to filter.</span></span>  
  
2.  <span data-ttu-id="60a66-110">**[マイニング モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="60a66-110">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="60a66-111">モデルを選択し、右クリックしてショートカット メニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="60a66-111">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="60a66-112">または</span><span class="sxs-lookup"><span data-stu-id="60a66-112">-or-</span></span>  
  
     <span data-ttu-id="60a66-113">モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-113">Select the model.</span></span> <span data-ttu-id="60a66-114">次に、 **[マイニング モデル]** メニューの **[モデル フィルターの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60a66-114">Then, on the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
4.  <span data-ttu-id="60a66-115">**[モデル フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** ボックスのグリッドの先頭行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60a66-115">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
5.  <span data-ttu-id="60a66-116">データ ソースに 1 つのフラット テーブルが含まれる場合、ドロップダウン リストには該当のテーブルの列名のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-116">If the data source contains a single flat table, the drop-down list displays only the names of the columns in that table.</span></span>  
  
     <span data-ttu-id="60a66-117">マイニング構造に複数のテーブルが含まれる場合、リストにはソース テーブルの名前が示されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-117">If the mining structure contains multiple tables, the list shows the names of the source tables.</span></span> <span data-ttu-id="60a66-118">テーブルを選択するまで列名は表示されません。</span><span class="sxs-lookup"><span data-stu-id="60a66-118">The column names do not display until a table has been selected.</span></span>  
  
     <span data-ttu-id="60a66-119">マイニング構造にケース テーブルと入れ子になったテーブルが含まれる場合は、ドロップダウン リストにケース テーブルの列、入れ子になったテーブルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-119">If the mining structure contains a case table and a nested table, the drop-down list shows columns from the case table, and the name of the nested table.</span></span>  
  
6.  <span data-ttu-id="60a66-120">ドロップダウン リストから列を選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-120">Select a column from the drop-down list.</span></span>  
  
     <span data-ttu-id="60a66-121">テキスト ボックスの左側のアイコンが変化して、選択されたアイテムがテーブルであるか列であるかが示されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-121">The icon at the left side of the text box changes to indicate that the selected item is a table or a column.</span></span>  
  
7.  <span data-ttu-id="60a66-122">**[演算子]** ボックスをクリックし、一覧から演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-122">Click the **Operator** text box and select an operator from the list.</span></span> <span data-ttu-id="60a66-123">有効な演算子は、選択した列のデータ型によって変わります。</span><span class="sxs-lookup"><span data-stu-id="60a66-123">The valid operators change depending on the data type of the column you selected.</span></span>  
  
8.  <span data-ttu-id="60a66-124">**[値]** ボックスをクリックし、ボックスに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="60a66-124">Click the **Value** text box, and type a value in the box.</span></span>  
  
     <span data-ttu-id="60a66-125">たとえば、列としてを選択し、 `Income` 大なり演算子 (>) を選択して、「」と入力し `30000` ます。</span><span class="sxs-lookup"><span data-stu-id="60a66-125">For example, select `Income` as the column, select the greater than operator (>), and then type `30000`.</span></span>  
  
9. <span data-ttu-id="60a66-126">グリッドの次の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60a66-126">Click the next row in the grid.</span></span>  
  
     <span data-ttu-id="60a66-127">作成したフィルター条件が [式] ボックスに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-127">The filter condition that you created is automatically added to the Expression text box.</span></span> <span data-ttu-id="60a66-128">たとえば、`[Income] > '30000'` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="60a66-128">For example, `[Income] > '30000'`</span></span>  
  
10. <span data-ttu-id="60a66-129">グリッドの次の行の **[ルールの適用条件]** ボックスをクリックし、条件を追加します。</span><span class="sxs-lookup"><span data-stu-id="60a66-129">Click the **AND/OR** text box in the next row of the grid to add a condition.</span></span>  
  
     <span data-ttu-id="60a66-130">たとえば、BETWEEN 条件を作成するには、 `AND` 論理オペランドのドロップダウンリストからを選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-130">For example, to create a BETWEEN condition, select `AND` from the drop-down list of logical operands.</span></span>  
  
11. <span data-ttu-id="60a66-131">演算子を選択し、手順 7. と手順 8. に示したように値を入力します。</span><span class="sxs-lookup"><span data-stu-id="60a66-131">Select an operator and type a value as described in Steps 7 and 8.</span></span>  
  
     <span data-ttu-id="60a66-132">たとえば、 `Income` 列としてをもう一度選択し、小なり演算子 (<) を選択して、「」と入力し `40000` ます。</span><span class="sxs-lookup"><span data-stu-id="60a66-132">For example, select `Income` as the column again, select the less than operator (<), and then type `40000`.</span></span>  
  
12. <span data-ttu-id="60a66-133">グリッドの次の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60a66-133">Click the next row in the grid.</span></span>  
  
13. <span data-ttu-id="60a66-134">[式] ボックスのフィルター条件が自動的に更新され、新しい条件が追加されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-134">The filter condition in the Expression text box is automatically updated to include the new condition.</span></span> <span data-ttu-id="60a66-135">完成した式は次のようになります。 `[Income] > '30000'AND [Income] < '40000'`</span><span class="sxs-lookup"><span data-stu-id="60a66-135">The completed expression is as follows: `[Income] > '30000'AND [Income] < '40000'`</span></span>  
  
### <a name="to-add-a-filter-on-the-nested-table-in-a-mining-model"></a><span data-ttu-id="60a66-136">マイニング モデルの入れ子になったテーブルにフィルターを追加するには</span><span class="sxs-lookup"><span data-stu-id="60a66-136">To add a filter on the nested table in a mining model</span></span>  
  
1.  <span data-ttu-id="60a66-137">[ \*\* \<name> モデルフィルター\*\* ] ダイアログボックスで、[**マイニング構造列**] の下のグリッドの空の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60a66-137">In the **\<name>Model Filter** Dialog box, click an empty row in the grid under **Mining Structure Column**.</span></span>  
  
2.  <span data-ttu-id="60a66-138">ドロップダウン リストから、入れ子になったテーブルの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-138">Select the name of the nested table from the drop-down list.</span></span>  
  
     <span data-ttu-id="60a66-139">テキスト ボックスの左側のアイコンが変化して、選択されたアイテムがテーブルの名前であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-139">The icon at the left side of the text box changes to indicate that the selected item is the name of a table.</span></span>  
  
3.  <span data-ttu-id="60a66-140">**[演算子]** ボックスをクリックし、 **[次の値を含む]** または **[次の値を含まない]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-140">Click the **Operator** text box and select **Contains** or **Not Contain**.</span></span>  
  
     <span data-ttu-id="60a66-141">ケース テーブルでは入れ子になったテーブルの特定の値を含むケースのみに制限しているため、 **[モデル フィルター]** ダイアログ ボックスで入れ子になったテーブルに対して選択できる条件はこれだけです。</span><span class="sxs-lookup"><span data-stu-id="60a66-141">These are the only conditions available for the nested table in the **Model Filter** dialog box, because you are restricting the case table to only those cases that contain a certain value in the nested table.</span></span> <span data-ttu-id="60a66-142">次の手順で入れ子になったテーブルの条件に値を設定します。</span><span class="sxs-lookup"><span data-stu-id="60a66-142">You will set the value for the condition on the nested table in the next step.</span></span>  
  
4.  <span data-ttu-id="60a66-143">[**値**] ボックスをクリックし、[ **..** .] ボタンをクリックして式を作成します。</span><span class="sxs-lookup"><span data-stu-id="60a66-143">Click the **Value** box, and then click the **(...)** button to build an expression.</span></span>  
  
     <span data-ttu-id="60a66-144">[ \*\* \<name> フィルター\*\* ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-144">The **\<name>Filter** dialog box opens.</span></span> <span data-ttu-id="60a66-145">このダイアログ ボックスでは、現在のテーブルにのみ条件を設定できます。ここでは、入れ子になったテーブルです。</span><span class="sxs-lookup"><span data-stu-id="60a66-145">This dialog box can set conditions only on the current table, which in this case is the nested table.</span></span>  
  
5.  <span data-ttu-id="60a66-146">**[マイニング構造列]** ボックスをクリックし、入れ子になったテーブル列のドロップダウン リストから列名を選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-146">Click the **Mining Structure Column** box and select a column name from the dropdown lists of nested table columns.</span></span>  
  
6.  <span data-ttu-id="60a66-147">**[演算子]** をクリックし、列に対して有効な演算子の一覧から演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-147">Click **Operator** and select an operator from the list of valid operators for the column.</span></span>  
  
7.  <span data-ttu-id="60a66-148">**[値]** をクリックし、値を入力します。</span><span class="sxs-lookup"><span data-stu-id="60a66-148">Click **Value** and type a value.</span></span>  
  
     <span data-ttu-id="60a66-149">たとえば、[**マイニング構造列**] には、を選択し `Model` ます。</span><span class="sxs-lookup"><span data-stu-id="60a66-149">For example, for **Mining Structure Column,** select `Model`.</span></span> <span data-ttu-id="60a66-150">[**演算子**] で、を選択し、 `<>` 値を入力し `Water Bottle` ます。</span><span class="sxs-lookup"><span data-stu-id="60a66-150">For **Operator**, select `<>`, and type the value `Water Bottle`.</span></span> <span data-ttu-id="60a66-151">この条件で次のフィルター式が作成されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-151">This condition creates the following filter expression:</span></span>  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  <span data-ttu-id="60a66-152">入れ子になったテーブルの属性数に制限はないため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では選択できる値の一覧を表示しません。</span><span class="sxs-lookup"><span data-stu-id="60a66-152">Because the number of nested table attributes is potentially unlimited, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not supply a list of possible values from which to select.</span></span> <span data-ttu-id="60a66-153">値を正確に入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60a66-153">You must type the exact value.</span></span> <span data-ttu-id="60a66-154">また、入れ子になったテーブルに LIKE 演算子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="60a66-154">Also, you cannot use a LIKE operator in a nested table.</span></span>  
  
1.  <span data-ttu-id="60a66-155">必要に応じて条件を追加します。条件を組み合わせるに `AND` は、 `OR` **[** **条件**] グリッドの左側にある [または] ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="60a66-155">Add more conditions as necessary, combining the conditions by selecting `AND` or `OR` in the **AND/OR** box at the left side of the **Conditions** grid.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  <span data-ttu-id="60a66-156">**[モデル フィルター]** ダイアログ ボックスで、 **[フィルター]** ダイアログ ボックスを使用して作成した条件を確認します。</span><span class="sxs-lookup"><span data-stu-id="60a66-156">In the **Model Filter** dialog box, review the conditions that you created by using the **Filter** dialog box.</span></span> <span data-ttu-id="60a66-157">入れ子になったテーブルの条件は、ケース テーブルの条件に追加され、フィルター条件の完全なセットは **[式]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="60a66-157">The conditions for the nested table are appended to the conditions for the case table, and the complete set of filter conditions is displayed in the **Expression** text box.</span></span>  
  
3.  <span data-ttu-id="60a66-158">必要に応じて、 **[クエリの編集]** をクリックして、フィルター式を手動で変更できます。</span><span class="sxs-lookup"><span data-stu-id="60a66-158">Optionally, click **Edit Query** to manually change the filter expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60a66-159">フィルター式の一部を手動で変更すると、グリッドが無効になり、その後はテキスト編集モードでしかフィルター式を操作できなくなります。</span><span class="sxs-lookup"><span data-stu-id="60a66-159">If you change any part of a filter expression manually, the grid will be disabled and thereafter you must work with the filter expression in text edit mode only.</span></span> <span data-ttu-id="60a66-160">グリッド編集モードに戻すには、フィルター式を消去して最初からやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="60a66-160">To restore grid editing mode, you must clear the filter expression and start over.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="60a66-161">参照</span><span class="sxs-lookup"><span data-stu-id="60a66-161">See Also</span></span>  
 <span data-ttu-id="60a66-162">[マイニングモデルのフィルター &#40;Analysis Services データマイニング&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="60a66-162">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="60a66-163">[マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="60a66-163">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="60a66-164">マイニング モデルからのフィルターの削除</span><span class="sxs-lookup"><span data-stu-id="60a66-164">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
  
