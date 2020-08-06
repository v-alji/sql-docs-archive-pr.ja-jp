---
title: マトリックスとグラフでの同じデータの表示 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1262f283-9fc2-4bc1-9c79-457f7642abc7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7746ce1f06d4dcc67c51ddc40714f19a3ff83d51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721164"
---
# <a name="display-the-same-data-on-a-matrix-and-a-chart-report-builder"></a><span data-ttu-id="709f1-102">マトリックスとグラフでの同じデータの表示 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="709f1-102">Display the Same Data on a Matrix and a Chart (Report Builder)</span></span>
  <span data-ttu-id="709f1-103">マトリックスとグラフで同じデータを表示するには、フィルター、グループ、並べ替え、およびデータに対して同じデータセットを指定するだけでなく、同じ式も指定するプロパティを両方のデータ領域に対して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="709f1-103">When you want to show the same data in a matrix and a chart, you must set properties on both data regions to specify the same dataset, and also the same expressions for filters, groups, sorts, and data.</span></span>  
  
 <span data-ttu-id="709f1-104">両方のデータ領域が同じデータ先祖 (レポート データセット) を持つようになるので、対話的な並べ替えボタンをマトリックスに追加することにより、ユーザーがこのボタンをクリックしたときに、マトリックスとグラフの両方の並べ替え順序を変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="709f1-104">Because both data regions will have the same ancestor for data (the report dataset), you can add an interactive sort button to the matrix that, when the user clicks it, changes the sort order for both the matrix and the chart.</span></span> <span data-ttu-id="709f1-105">詳細については、「 [テーブルまたはマトリックスへの対話的な並べ替えの追加 (レポート ビルダーおよび SSRS)](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="709f1-105">For more information, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="709f1-106">マトリックスの列グループの値をグラフの凡例として使用するには、グラフ上の系列データの色を指定してから、グループ値を表示するマトリックス セル内のテキスト ボックスの背景を塗りつぶす色として、それと同じ色を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="709f1-106">To use the matrix column group values as a legend for the chart, you must specify the colors for the series data on the chart, and then use the same colors as the fill colors for the background of the text boxes in the matrix cell that displays the group values.</span></span> <span data-ttu-id="709f1-107">詳細については、「[複数の図形グラフでの色の統一 &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="709f1-107">For more information, see [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="709f1-108">グループ定義に関するグループ値が多すぎると、実行時にレポートが煩雑な外観になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="709f1-108">At run-time, your report may appear cluttered if there are too many group values for your group definitions.</span></span> <span data-ttu-id="709f1-109">このような場合は、値をフィルター選択したり、グループを組み合わせたり、グループが自動的に結合されるようにしきい値を調整したりすることが必要となります。</span><span class="sxs-lookup"><span data-stu-id="709f1-109">You might need to filter values, combine groups, or adjust the threshold for the chart to combine groups for you.</span></span> <span data-ttu-id="709f1-110">詳細については、「 [同じデータセットへの複数のデータ領域のリンク (レポート ビルダーおよび SSRS)](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="709f1-110">For more information, see [Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-matrix-and-chart-to-display-the-same-data"></a><span data-ttu-id="709f1-111">マトリックスとグラフを追加して同じデータを表示するには</span><span class="sxs-lookup"><span data-stu-id="709f1-111">To add a matrix and chart to display the same data</span></span>  
  
1.  <span data-ttu-id="709f1-112">デザイン ビューでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="709f1-112">Open a report in design view.</span></span>  
  
2.  <span data-ttu-id="709f1-113">**[挿入]** タブの **[データ領域]** グループで **[マトリックス]** をクリックし、レポート本文またはレポート本文内の四角形の中をクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-113">From the **Insert** tab, in the **Data Regions** group, click **Matrix**, and then click the report body or in a rectangle in the report body.</span></span> <span data-ttu-id="709f1-114">マトリックスがレポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-114">A matrix is added to the report.</span></span>  
  
3.  <span data-ttu-id="709f1-115">**[挿入]** タブの **[データ領域]** グループで **[グラフ]** をクリックし、グラフの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="709f1-115">From the **Insert** tab, in the **Data Regions** group, click **Chart**, and then select the chart type.</span></span> <span data-ttu-id="709f1-116">グラフがレポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-116">A chart is added to the report.</span></span>  
  
4.  <span data-ttu-id="709f1-117">(省略可) **[挿入]** タブの **[レポート アイテム]** グループで **[四角形]** をクリックし、レポートをクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-117">(Optional) From the **Insert** tab, in the **Report Items** group, click **Rectangle**, and then click the report.</span></span> <span data-ttu-id="709f1-118">四角形がレポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-118">A rectangle is added to the report.</span></span> <span data-ttu-id="709f1-119">手順 2. および 3. で追加したマトリックスとグラフを四角形にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="709f1-119">Drag the matrix and chart from steps 2 and 3 into the rectangle.</span></span>  
  
     <span data-ttu-id="709f1-120">四角形のコンテナーに複数のデータ領域を配置すると、レポートを確認するときに、マトリックスとグラフの表示方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="709f1-120">By placing multiple data regions in the rectangle container, you help control how the matrix and chart render when you view the report.</span></span>  
  
     <span data-ttu-id="709f1-121">次に示す手順では、マトリックスとグラフで表示する同じデータセット フィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="709f1-121">In the next few steps, you will choose the same dataset field to display in the matrix and to display in the chart.</span></span>  
  
5.  <span data-ttu-id="709f1-122">レポート データ ペインから、数値データセット フィールドをマトリックス内のデータ セルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="709f1-122">From the Report Data pane, drag a numeric dataset field to the Data cell in the matrix.</span></span>  
  
     <span data-ttu-id="709f1-123">既定で、グループ値の計算には、集計関数 Sum が使用されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-123">By default, the aggregate function Sum is used for calculating the group value.</span></span> <span data-ttu-id="709f1-124">マトリックス内の集計関数を変更した場合は、グラフの集計関数も変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="709f1-124">If you change the aggregate function in the matrix, you must change in the chart also.</span></span>  
  
6.  <span data-ttu-id="709f1-125">マトリックスで、データが含まれたセルを右クリックして、 **[テキスト ボックスのプロパティ]** 、 **[数値]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-125">In the matrix, right-click the cell with data, click **Text Box Properties**, and then click **Number**.</span></span> <span data-ttu-id="709f1-126">データセット フィールド値の適切な形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="709f1-126">Choose an appropriate format for the dataset field value.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="709f1-127">手順 3. で選択したのと同じデータセット フィールドをグラフの **[値]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="709f1-127">Drag the same dataset field you chose in step 3 to the **Values** area on the chart.</span></span>  
  
9. <span data-ttu-id="709f1-128">グラフで Y 軸を右クリックして、 **[軸のプロパティ]** 、 **[数値]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-128">In the chart, right-click the Y axis, click **Axis Properties**, and then click **Number**.</span></span> <span data-ttu-id="709f1-129">手順 4. で使用したのと同じデータ形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="709f1-129">Choose the same format for the data that you chose in step 4.</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="709f1-130">次に示す手順では、マトリックスの行グループとグラフの系列グループを同じ式に設定し、グラフの系列グループの並べ替え順序を設定します。</span><span class="sxs-lookup"><span data-stu-id="709f1-130">In the next few steps, you will set the matrix row group and the chart series group to the same expression, and also set the sort order for the chart series group.</span></span>  
  
11. <span data-ttu-id="709f1-131">レポート データ ペインから、マトリックス行に関してグループ化するデータセット フィールドを行グループ ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="709f1-131">From the Report Data pane, drag the dataset field that you want to group by for matrix rows to the Row Groups pane.</span></span>  
  
     <span data-ttu-id="709f1-132">既定では、マトリックス行グループによって、グループ式と同じ並べ替え式が追加されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-132">By default, the matrix row group adds a sort expression that is the same as the group expression.</span></span>  
  
12. <span data-ttu-id="709f1-133">手順 9. で使用したのと同じデータセット フィールドをグラフの **[系列グループ]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="709f1-133">Drag the same dataset field that you used in step 9 to the **Series Groups** area for the chart.</span></span>  
  
13. <span data-ttu-id="709f1-134">**[系列グループ]** 領域内のグループを右クリックし、 **[系列グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-134">Right-click the group in the **Series Groups** area, and then click **Series Group Properties**.</span></span>  
  
14. <span data-ttu-id="709f1-135">**[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-135">Click **Sorting**.</span></span>  
  
15. <span data-ttu-id="709f1-136">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-136">Click **Add**.</span></span> <span data-ttu-id="709f1-137">新しい行が並べ替え式のグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-137">A new row appears in the sort expressions grid.</span></span>  
  
16. <span data-ttu-id="709f1-138">**[並べ替え]** のドロップダウン リストから、手順 9 でグループ化に使用するように選択したデータセット フィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="709f1-138">In **Sort by**, from the drop-down list, choose the dataset field that you chose to group by in step 9.</span></span>  
  
17. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="709f1-139">次に示す手順では、マトリックスの列グループとグラフのカテゴリ グループを同じ式に設定し、グラフのカテゴリ グループの並べ替え順序を設定します。</span><span class="sxs-lookup"><span data-stu-id="709f1-139">In the next few steps, you will set the matrix column group and the chart category group to the same expression, and also set the sort order for the chart category group.</span></span>  
  
18. <span data-ttu-id="709f1-140">レポート データ ペインから、マトリックス列に関してグループ化するデータセット フィールドを列グループ ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="709f1-140">From the Report Data pane, drag the dataset field that you want to group by for matrix columns to the Column Groups pane.</span></span>  
  
     <span data-ttu-id="709f1-141">既定では、マトリックス列グループによって、グループ式と同じ並べ替え式が追加されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-141">By default, the matrix column group adds a sort expression that is the same as the group expression.</span></span>  
  
19. <span data-ttu-id="709f1-142">手順 16. で使用したのと同じデータセット フィールドをグラフの **[カテゴリ グループ]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="709f1-142">Drag the same dataset field that you used in step 16 to the **Category Groups** area for the chart.</span></span>  
  
20. <span data-ttu-id="709f1-143">**[カテゴリ グループ]** 領域内のグループを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-143">Right-click the group in the **CategoryGroups** area, and then click **Category Group Properties**.</span></span>  
  
21. <span data-ttu-id="709f1-144">**[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-144">Click **Sorting**.</span></span>  
  
22. <span data-ttu-id="709f1-145">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="709f1-145">Click **Add**.</span></span> <span data-ttu-id="709f1-146">新しい行が並べ替え式のグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-146">A new row appears in the sort expressions grid.</span></span>  
  
23. <span data-ttu-id="709f1-147">**[並べ替え]** のドロップダウン リストから、手順 16 でグループ化に使用するように選択したデータセット フィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="709f1-147">In **Sort by**, from the drop-down list, choose the dataset field that you chose to group by in step 16.</span></span>  
  
24. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
25. <span data-ttu-id="709f1-148">結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="709f1-148">Preview the result.</span></span> <span data-ttu-id="709f1-149">マトリックスの行グループと列グループに、グラフの系列グループとカテゴリ グループと同じデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="709f1-149">The matrix row and column groups display the same data as the chart series and category groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="709f1-150">参照</span><span class="sxs-lookup"><span data-stu-id="709f1-150">See Also</span></span>  
 <span data-ttu-id="709f1-151">[同じデータセットへの複数のデータ領域のリンク &#40;レポート ビルダーおよび SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="709f1-151">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="709f1-152">[データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="709f1-152">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="709f1-153">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="709f1-153">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="709f1-154">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="709f1-154">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
