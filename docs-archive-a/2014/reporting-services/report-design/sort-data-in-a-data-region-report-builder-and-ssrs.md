---
title: データ領域内のデータの並べ替え (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2fcb9be2-1daa-4c92-ad00-5f63cdf39f70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc1fb458066bb942a490b08c0faad876dd3d5438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739223"
---
# <a name="sort-data-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="8af49-102">データ領域内のデータの並べ替え (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="8af49-102">Sort Data in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8af49-103">レポートを初めて実行したときのデータ領域内のデータの並べ替え順序を変更するには、データ領域またはグループに対して並べ替え式を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8af49-103">To change the sort order of data in a data region when a report first runs, you must set the sort expression on the data region or group.</span></span> <span data-ttu-id="8af49-104">既定で、グループの並べ替え式は、グループ式と同じ値に自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8af49-104">By default, the sort expression for a group is automatically set to the same value as the group expression.</span></span>  
  
-   <span data-ttu-id="8af49-105">Tablix データ領域では、詳細グループも含め、各グループのデータ領域に対して並べ替え式を設定します。</span><span class="sxs-lookup"><span data-stu-id="8af49-105">In a tablix data region, set the sort expression for the data region or for each group, including the details group.</span></span> <span data-ttu-id="8af49-106">tablix データ領域に詳細グループが 1 つしかない場合は、データ領域または詳細グループでクエリの並べ替え式の効果が同じになるように定義できます。</span><span class="sxs-lookup"><span data-stu-id="8af49-106">If you have only one details group in a tablix data region, you can define a sort expression in the query, on the data region, or on the details group and they all have the same effect.</span></span>  
  
-   <span data-ttu-id="8af49-107">グラフ データ領域では、カテゴリおよび系列グループの並べ替え式を設定して、各グループの並べ替え順序を制御します。</span><span class="sxs-lookup"><span data-stu-id="8af49-107">In a chart data region, set the sort expression for the Category and Series groups to control the sort order for each group.</span></span> <span data-ttu-id="8af49-108">グラフの凡例に表示される色の順序は、カテゴリ グループ内のデータ ポイントに対して設定されている並べ替え式によって決まります。</span><span class="sxs-lookup"><span data-stu-id="8af49-108">The order for colors in a chart legend is determined by the sort expression for the data points in the Category group.</span></span>  
  
-   <span data-ttu-id="8af49-109">ゲージには範囲を基準とした単一の値が表示されます。そのため、ゲージ データ領域では、データの並べ替えが必要とならないのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="8af49-109">In a gauge data region, you do not typically need to sort data because the gauge displays a single value relative to a range.</span></span> <span data-ttu-id="8af49-110">ゲージのデータを並べ替える必要がある場合は、最初にグループを定義し、次にグループの並べ替え式を設定します。</span><span class="sxs-lookup"><span data-stu-id="8af49-110">If you do need sort data in a gauge, you must first define a group, and then set the sort expression for the group.</span></span>  
  
 <span data-ttu-id="8af49-111">詳細については、「 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8af49-111">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8af49-112">tablix データ領域の場合は、対話的な並べ替えボタンを列見出しの上に追加して、ユーザーがグループまたは詳細行の並べ替え順序を変更できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8af49-112">For a tablix data region, you can also add an interactive sort button to the top of a column header to provide the user with the ability to change the sort order of groups or detail rows.</span></span> <span data-ttu-id="8af49-113">詳細については、「[対話的な並べ替え (レポート ビルダーおよび SSRS)](interactive-sort-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8af49-113">For more information, see [Interactive Sort &#40;Report Builder and SSRS&#41;](interactive-sort-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-sort-data-in-a-tablix-data-region"></a><span data-ttu-id="8af49-114">Tablix データ領域内のデータを並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="8af49-114">To sort data in a Tablix data region</span></span>  
  
1.  <span data-ttu-id="8af49-115">デザイン画面で、行ハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-115">On the design surface, right-click a row handle, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="8af49-116">**[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-116">Click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="8af49-117">各並べ替え式について、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8af49-117">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="8af49-118">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-118">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="8af49-119">データの並べ替えに使用する式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-119">Type or select an expression by which to sort the data.</span></span>  
  
    3.  <span data-ttu-id="8af49-120">**[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-120">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="8af49-121">**[昇順で並べ替え]** を選択すると、式が昇順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-121">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="8af49-122">**[降順で並べ替え]** を選択すると、式が降順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-122">**Z-A** sorts the expression in descending order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-values-in-a-group-including-the-details-group-for-a-tablix"></a><span data-ttu-id="8af49-123">Tablix で詳細グループを含むグループ内の値を並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="8af49-123">To sort values in a group, including the details group, for a Tablix</span></span>  
  
1.  <span data-ttu-id="8af49-124">デザイン画面で、Tablix データ領域内をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-124">On the design surface, click in the tablix data region to select it.</span></span> <span data-ttu-id="8af49-125">グループ化ペインに、この Tablix データ領域の行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8af49-125">The Grouping pane displays the row groups and column groups for the Tablix data region.</span></span>  
  
2.  <span data-ttu-id="8af49-126">行グループ ペインで、グループ名を右クリックし、 **[グループの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-126">In the Row Groups pane, right-click the group name, and then click **Edit Group**.</span></span>  
  
3.  <span data-ttu-id="8af49-127">**[Tablix のグループ]** ダイアログ ボックスで **[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-127">In the **Tablix Group** dialog box, click **Sort**.</span></span>  
  
4.  <span data-ttu-id="8af49-128">各並べ替え式について、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8af49-128">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="8af49-129">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-129">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="8af49-130">データの並べ替えに使用する式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-130">Type or select an expression by which to sort the data.</span></span>  
  
    3.  <span data-ttu-id="8af49-131">**[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-131">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="8af49-132">**[昇順で並べ替え]** を選択すると、式が昇順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-132">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="8af49-133">**[降順で並べ替え]** を選択すると、式が降順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-133">**Z-A** sorts the expression in descending order.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-x-axis-labels-in-alphabetical-order-on-a-chart"></a><span data-ttu-id="8af49-134">グラフで X 軸ラベルをアルファベット順に並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="8af49-134">To sort x-axis labels in alphabetical order on a chart</span></span>  
  
1.  <span data-ttu-id="8af49-135">[カテゴリ フィールド] ドロップ ゾーンでフィールドを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-135">Right-click a field in the Category Field drop-zone and click **Category GroupProperties**.</span></span>  
  
2.  <span data-ttu-id="8af49-136">**[カテゴリ グループのプロパティ]** ダイアログ ボックスの **[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-136">In the **Category Group Properties** dialog box, click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="8af49-137">各並べ替え式について、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8af49-137">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="8af49-138">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-138">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="8af49-139">グループ化フィールドと一致する式を選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-139">Select the expression that matches your grouping field.</span></span> <span data-ttu-id="8af49-140">**[グループ化]** をクリックすると、グループ化フィールドの式を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8af49-140">You can verify the expression for the grouping field by clicking **Grouping**.</span></span>  
  
    3.  <span data-ttu-id="8af49-141">**[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-141">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="8af49-142">**[昇順で並べ替え]** を選択すると、式がアルファベットの昇順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-142">**A-Z** sorts the expression in ascending alphabetical order.</span></span> <span data-ttu-id="8af49-143">**[降順で並べ替え]** を選択すると、式がアルファベットの降順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-143">**Z-A** sorts the expression in descending alphabetical order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-the-data-points-in-ascending-or-descending-order-on-a-chart"></a><span data-ttu-id="8af49-144">グラフ上のデータ ポイントを昇順または降順で並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="8af49-144">To sort the data points in ascending or descending order on a chart</span></span>  
  
1.  <span data-ttu-id="8af49-145">[カテゴリ フィールド] ドロップ ゾーンでフィールドを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-145">Right-click a field in the Category Field drop zone and click **Category GroupProperties**.</span></span>  
  
2.  <span data-ttu-id="8af49-146">**[カテゴリ グループのプロパティ]** ダイアログ ボックスの **[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-146">In the **Category Group Properties** dialog box, click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="8af49-147">各並べ替え式について、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8af49-147">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="8af49-148">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-148">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="8af49-149">データ フィールドと一致する式を選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-149">Select the expression that matches your data field.</span></span> <span data-ttu-id="8af49-150">ほとんどの場合、これは、 `=Sum(Fields!Quantity.Value)`などの集計値です。</span><span class="sxs-lookup"><span data-stu-id="8af49-150">In most cases, this is an aggregated value, such as `=Sum(Fields!Quantity.Value)`.</span></span>  
  
    3.  <span data-ttu-id="8af49-151">**[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-151">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="8af49-152">**[昇順で並べ替え]** を選択すると、式が昇順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-152">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="8af49-153">**[降順で並べ替え]** を選択すると、式が降順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-153">**Z-A** sorts the expression in descending order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-data-in-ascending-or-descending-order-for-display-on-a-gauge"></a><span data-ttu-id="8af49-154">ゲージ上に表示するデータを昇順または降順で並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="8af49-154">To sort data in ascending or descending order for display on a gauge</span></span>  
  
1.  <span data-ttu-id="8af49-155">ゲージを右クリックして、 **[データ グループの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-155">Right-click the gauge and click **Add Data Group**.</span></span>  
  
2.  <span data-ttu-id="8af49-156">**[ゲージ パネル グループのプロパティ]** ダイアログ ボックスで、必要に応じて **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-156">In the **Gauge Panel GroupProperties** dialog box, click **General** if necessary.</span></span>  
  
3.  <span data-ttu-id="8af49-157">**[グループ式]** の **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-157">In **Group expressions**, click **Add**.</span></span>  
  
4.  <span data-ttu-id="8af49-158">**[グループ化の条件]** で、データのグループ化に使用する式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-158">In **Group on**, type or select an expression by which to group the data.</span></span>  
  
5.  <span data-ttu-id="8af49-159">手順 3. と 4. を繰り返して、使用するグループ式をすべて追加します。</span><span class="sxs-lookup"><span data-stu-id="8af49-159">Repeat steps 3 and 4 until you have added all the group expressions you want to use.</span></span>  
  
6.  <span data-ttu-id="8af49-160">**[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-160">Click **Sorting**.</span></span>  
  
7.  <span data-ttu-id="8af49-161">各並べ替え式について、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8af49-161">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="8af49-162">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8af49-162">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="8af49-163">グループ化フィールドと一致する式を選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-163">Select the expression that matches your grouping field.</span></span> <span data-ttu-id="8af49-164">**[グループ化]** をクリックすると、グループ化フィールドの式を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8af49-164">You can verify the expression for the grouping field by clicking **Grouping**.</span></span>  
  
    3.  <span data-ttu-id="8af49-165">**[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。</span><span class="sxs-lookup"><span data-stu-id="8af49-165">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="8af49-166">**[昇順で並べ替え]** を選択すると、式が昇順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-166">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="8af49-167">**[降順で並べ替え]** を選択すると、式が降順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="8af49-167">**Z-A** sorts the expression in descending order.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="8af49-168">ゲージ内のデータをグループ化する方法の詳細については、「[ゲージ &#40;レポート ビルダーおよび SSRS&#41;](gauges-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8af49-168">For more information about how data is grouped in a gauge, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af49-169">参照</span><span class="sxs-lookup"><span data-stu-id="8af49-169">See Also</span></span>  
 <span data-ttu-id="8af49-170">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="8af49-170">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="8af49-171">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8af49-171">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8af49-172">[グラフの軸ラベルの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8af49-172">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8af49-173">複数の図形グラフでの色の統一 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8af49-173">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](shape-charts-report-builder-and-ssrs.md)  
  
  
