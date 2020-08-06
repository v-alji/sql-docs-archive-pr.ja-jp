---
title: フィルターの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10ae54e7-0e8a-4dff-995d-05516c51d076
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61a5444c437027d92a9f054e74cbcac6af5cc776
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742830"
---
# <a name="add-a-filter-report-builder-and-ssrs"></a><span data-ttu-id="6bf85-102">フィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="6bf85-102">Add a Filter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6bf85-103">計算や表示の対象として特定の値だけを含めたり除外したりするには、データセット、データ領域、またはグループにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-103">Add a filter to a dataset, data region, or group when you want to include or exclude specific values for calculations or display.</span></span> <span data-ttu-id="6bf85-104">実行時には、フィルターが最初にデータセットに適用され、次にデータ領域に適用された後、グループに (グループ階層の上から順に) 適用されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-104">Filters are applied at run time first on the dataset, and then on the data region, and then on the group, in top-down order for group hierarchies.</span></span> <span data-ttu-id="6bf85-105">テーブル、マトリックス、または一覧では、行グループ、列グループ、および隣接するグループに対するフィルターが別々に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-105">In a table, matrix, or list, filters for row groups, column groups, and adjacent groups are applied independently.</span></span> <span data-ttu-id="6bf85-106">グラフでは、カテゴリ グループと系列グループに対するフィルターが別々に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-106">In a chart, filters for category groups and series groups are applied independently.</span></span>  
  
 <span data-ttu-id="6bf85-107">フィルターを追加するには、少なくとも 1 つのフィルター式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bf85-107">To add a filter, you must specify one or more filter equations.</span></span> <span data-ttu-id="6bf85-108">フィルター式は、フィルターの対象となるデータを識別する式、演算子、および、比較対象の値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-108">A filter equation consists of an expression that identifies the data that you want to filter, an operator, and the value to compare to.</span></span> <span data-ttu-id="6bf85-109">フィルターの対象となるデータとその比較対象となる値とでは、データ型を一致させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bf85-109">The data types of the filtered data and the value must match.</span></span> <span data-ttu-id="6bf85-110">データセットまたはデータ領域の集計値に対するフィルター処理はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6bf85-110">Filtering on aggregate values for a dataset or data region is not supported.</span></span>  
  
 <span data-ttu-id="6bf85-111">グラフ内のデータ ポイントをフィルター処理するには、カテゴリ グループまたは系列グループに対するフィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-111">To filter data points in a chart, you can set a filter on a category group or a series group.</span></span> <span data-ttu-id="6bf85-112">既定では、組み込み関数 Sum を使って、同じグループに属する値が系列内の個々のデータ ポイントとして集計されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-112">By default, the chart uses the built-in function Sum to aggregate values that belong to the same group into an individual data point in the series.</span></span> <span data-ttu-id="6bf85-113">系列の集計関数を変更する場合は、フィルター式の集計関数を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bf85-113">If you change the aggregate function of a series, you must change the aggregate function in the filter expression.</span></span>  
  
 <span data-ttu-id="6bf85-114">埋め込みデータセットと共有データセットのフィルター処理の詳細については、「[データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bf85-114">For more information about filtering embedded and shared datasets, see [Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-filter-on-a-data-region"></a><span data-ttu-id="6bf85-115">データ領域に対してフィルターを設定するには</span><span class="sxs-lookup"><span data-stu-id="6bf85-115">To set a filter on a data region</span></span>  
  
1.  <span data-ttu-id="6bf85-116">**[デザイン]** ビューでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-116">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="6bf85-117">デザイン画面でデータ領域を選択し、[プロパティ] を右クリックし _\<data region>_ **Properties**ます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-117">Select the data region on the design surface, and then right-click _\<data region>_**Properties**.</span></span> <span data-ttu-id="6bf85-118">ゲージの場合は、 **[ゲージ パネルのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-118">For a gauge, select **Gauge Panel Properties**.</span></span> <span data-ttu-id="6bf85-119">[ _\<data region>_ **プロパティ**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-119">The _\<data region>_**Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6bf85-120">Tablix データ領域でコーナー セル、行、または列のハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-120">On a Tablix data region, right-click the corner cell or a row or column handle, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="6bf85-121">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-121">Click **Filters**.</span></span> <span data-ttu-id="6bf85-122">現在のフィルター式の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-122">This displays the current list of filter equations.</span></span> <span data-ttu-id="6bf85-123">既定では、何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="6bf85-123">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="6bf85-124">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-124">Click **Add**.</span></span> <span data-ttu-id="6bf85-125">新しい空のフィルター式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-125">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="6bf85-126">**[式]** で、フィルター処理の対象となるフィールドの式を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-126">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="6bf85-127">式を編集するには、式 ( *[fx]* ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-127">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="6bf85-128">ドロップダウン ボックスから、手順 5. で作成した式のデータ型と同じデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-128">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="6bf85-129">**[演算子]** ボックスで、 **[式]** ボックスの値と **[値]** ボックスの値とを比較するための演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-129">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="6bf85-130">選択した演算子によって、次の手順で使用する値の数が異なります。</span><span class="sxs-lookup"><span data-stu-id="6bf85-130">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="6bf85-131">**[値]** ボックスで、 **[式]** の値を評価するフィルター用の式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-131">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="6bf85-132">フィルター式の例については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bf85-132">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-tablix-row-or-column-group"></a><span data-ttu-id="6bf85-133">Tablix の行グループまたは列グループに対してフィルターを設定するには</span><span class="sxs-lookup"><span data-stu-id="6bf85-133">To set a filter on a Tablix row or column group</span></span>  
  
1.  <span data-ttu-id="6bf85-134">**[デザイン]** ビューでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-134">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="6bf85-135">デザイン画面で、テーブル、マトリックス、または一覧のデータ領域を右クリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-135">Right-click the table, matrix, or list data region on the design surface to select it.</span></span> <span data-ttu-id="6bf85-136">[グループ化] ペインに、選択した項目のグループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-136">The Grouping pane displays the groups for the selected item.</span></span>  
  
3.  <span data-ttu-id="6bf85-137">[グループ化] ペインで、グループを右クリックし、 **[グループの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-137">In the Grouping pane, right-click the group, and then click **Edit Group**.</span></span> <span data-ttu-id="6bf85-138">**[Tablix のグループ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-138">The **Tablix Group** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="6bf85-139">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-139">Click **Filters**.</span></span> <span data-ttu-id="6bf85-140">現在のフィルター式の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-140">This displays the current list of filter equations.</span></span> <span data-ttu-id="6bf85-141">既定では、何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="6bf85-141">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="6bf85-142">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-142">Click **Add**.</span></span> <span data-ttu-id="6bf85-143">新しい空のフィルター式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-143">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="6bf85-144">**[式]** で、フィルター処理の対象となるフィールドの式を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-144">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="6bf85-145">式を編集するには、式 ( *[fx]* ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-145">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="6bf85-146">ドロップダウン ボックスから、手順 5. で作成した式のデータ型と同じデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-146">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="6bf85-147">**[演算子]** ボックスで、 **[式]** ボックスの値と **[値]** ボックスの値とを比較するための演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-147">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="6bf85-148">選択した演算子によって、次の手順で使用する値の数が異なります。</span><span class="sxs-lookup"><span data-stu-id="6bf85-148">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="6bf85-149">**[値]** ボックスで、 **[式]** の値を評価するフィルター用の式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-149">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="6bf85-150">フィルター式の例については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bf85-150">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-category-group"></a><span data-ttu-id="6bf85-151">グラフのカテゴリ グループに対してフィルターを設定するには</span><span class="sxs-lookup"><span data-stu-id="6bf85-151">To set a filter on a Chart category group</span></span>  
  
1.  <span data-ttu-id="6bf85-152">**[デザイン]** ビューでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-152">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="6bf85-153">デザイン画面で、グラフを 2 回クリックして、データ、系列、およびカテゴリ フィールドのドロップ ゾーンを表示します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-153">On the design surface, click the chart twice to bring up data, series and category field drop zones.</span></span>  
  
3.  <span data-ttu-id="6bf85-154">カテゴリ フィールドのドロップ ゾーン内のフィールドを右クリックし、 **[カテゴリ グループのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-154">Right-click on a field contained in the category field drop zone and select **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="6bf85-155">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-155">Click **Filters**.</span></span> <span data-ttu-id="6bf85-156">現在のフィルター式の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-156">This displays the current list of filter equations.</span></span> <span data-ttu-id="6bf85-157">既定では、何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="6bf85-157">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="6bf85-158">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-158">Click **Add**.</span></span> <span data-ttu-id="6bf85-159">新しい空のフィルター式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-159">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="6bf85-160">**[式]** で、フィルター処理の対象となるフィールドの式を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-160">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="6bf85-161">式を編集するには、式 ( *[fx]* ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-161">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="6bf85-162">ドロップダウン ボックスから、手順 5. で作成した式のデータ型と同じデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-162">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="6bf85-163">**[演算子]** ボックスで、 **[式]** ボックスの値と **[値]** ボックスの値とを比較するための演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-163">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="6bf85-164">選択した演算子によって、次の手順で使用する値の数が異なります。</span><span class="sxs-lookup"><span data-stu-id="6bf85-164">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="6bf85-165">**[値]** ボックスで、 **[式]** の値を評価するフィルター用の式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-165">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="6bf85-166">フィルター式の例については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bf85-166">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-series-group"></a><span data-ttu-id="6bf85-167">グラフの系列グループに対してフィルターを設定するには</span><span class="sxs-lookup"><span data-stu-id="6bf85-167">To set a filter on a Chart series group</span></span>  
  
1.  <span data-ttu-id="6bf85-168">**[デザイン]** ビューでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-168">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="6bf85-169">デザイン画面で、グラフを 2 回クリックして、データ、系列、およびカテゴリ フィールドのドロップ ゾーンを表示します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-169">On the design surface, click the chart twice to bring up data, series and category field drop zones.</span></span>  
  
3.  <span data-ttu-id="6bf85-170">系列フィールドのドロップ ゾーン内のフィールドを右クリックし、 **[系列グループのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-170">Right-click on a field contained in the series field drop zone and select **Series Group Properties**.</span></span>  
  
4.  <span data-ttu-id="6bf85-171">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-171">Click **Filters**.</span></span> <span data-ttu-id="6bf85-172">現在のフィルター式の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-172">This displays the current list of filter equations.</span></span> <span data-ttu-id="6bf85-173">既定では、何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="6bf85-173">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="6bf85-174">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-174">Click **Add**.</span></span> <span data-ttu-id="6bf85-175">新しい空のフィルター式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bf85-175">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="6bf85-176">**[式]** で、フィルター処理の対象となるフィールドの式を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-176">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="6bf85-177">式を編集するには、式 ( *[fx]* ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bf85-177">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="6bf85-178">ドロップダウン ボックスから、手順 5. で作成した式のデータ型と同じデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-178">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="6bf85-179">**[演算子]** ボックスで、 **[式]** ボックスの値と **[値]** ボックスの値とを比較するための演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-179">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="6bf85-180">選択した演算子によって、次の手順で使用する値の数が異なります。</span><span class="sxs-lookup"><span data-stu-id="6bf85-180">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="6bf85-181">**[値]** ボックスで、 **[式]** の値を評価するフィルター用の式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="6bf85-181">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="6bf85-182">フィルター式の例については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bf85-182">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6bf85-183">参照</span><span class="sxs-lookup"><span data-stu-id="6bf85-183">See Also</span></span>  
 <span data-ttu-id="6bf85-184">[データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="6bf85-184">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="6bf85-185">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6bf85-185">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6bf85-186">[ゲージ &#40;レポート ビルダーおよび SSRS&#41;](gauges-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6bf85-186">[Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6bf85-187">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6bf85-187">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6bf85-188">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6bf85-188">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
