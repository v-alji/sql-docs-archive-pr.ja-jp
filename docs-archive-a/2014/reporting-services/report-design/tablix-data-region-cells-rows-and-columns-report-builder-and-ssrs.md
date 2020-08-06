---
title: Tablix データ領域のセル、行、および列 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10058"
- "10057"
- sql12.rtp.rptdesigner.deleterows.f1
- sql12.rtp.rptdesigner.deletecolumns.f1
ms.assetid: 70eef636-6d8c-495e-83fc-dc0fe9771658
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fc5ee01368c02781f86a04f4b93f7db873fcb0dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640619"
---
# <a name="tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs"></a><span data-ttu-id="b851b-102">Tablix データ領域のセル、行、および列 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="b851b-102">Tablix Data Region Cells, Rows, and Columns (Report Builder) and SSRS</span></span>
  <span data-ttu-id="b851b-103">レポートの Tablix データ領域の行および列にデータを表示する方法を制御するには、詳細データ、グループ データ、ラベル、および合計に対して行と列を指定する方法を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b851b-103">To control how the rows and columns of a tablix data region display data in a report, you must understand how to specify rows and columns for detail data, for group data, and for labels and totals.</span></span> <span data-ttu-id="b851b-104">多くの場合、テーブル、マトリックス、または一覧の既定の構造を使用してデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-104">In many cases, you can use the default structures for a table, matrix, or list to display your data.</span></span> <span data-ttu-id="b851b-105">詳細については、「[テーブル &#40;レポートビルダーと ssrs&#41;](tables-report-builder-and-ssrs.md)」、「[マトリックス &#40;レポートビルダーと ssrs&#41;](create-a-matrix-report-builder-and-ssrs.md)」、または「 [&#40;レポートビルダーと ssrs&#41;の一覧](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b851b-105">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md), [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md), or [Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b851b-106">Tablix データ領域では、詳細行および詳細列に詳細データが表示され、グループ行およびグループ列にグループ化されたデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-106">A tablix data region displays detail data on detail rows and detail columns and grouped data on group rows and group columns.</span></span> <span data-ttu-id="b851b-107">Tablix データ領域に行グループおよび列グループを追加すると、データを表示するための行および列が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-107">When you add row groups and column groups to a tablix data region, rows and columns on which to display the data are automatically added.</span></span> <span data-ttu-id="b851b-108">行および列を手動で追加および削除して、Tablix データ領域をカスタマイズし、レポートでデータを表示する方法を制御することができます。</span><span class="sxs-lookup"><span data-stu-id="b851b-108">You can manually add and remove rows and columns to customize a tablix data region and control the way your data displays in the report.</span></span>  
  
 <span data-ttu-id="b851b-109">Tablix データ領域のカスタマイズ方法を理解するには、まず、デザイン画面で Tablix データ領域を選択したときに表示される視覚的な手掛かりの意味を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b851b-109">To understand how to customize a tablix data region, you should first understand how to interpret the visual cues you see when you select a tablix data region on the design surface.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="understanding-tablix-visual-cues"></a><span data-ttu-id="b851b-110">Tablix の視覚的な手掛かりについて</span><span class="sxs-lookup"><span data-stu-id="b851b-110">Understanding Tablix Visual Cues</span></span>  
 <span data-ttu-id="b851b-111">Tablix データ領域に表示される視覚的な手掛かりは、Tablix データ領域を操作して必要なデータを表示する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b851b-111">Visual cues on a tablix data region help you work with a tablix data region to display the data you want.</span></span>  
  
### <a name="row-and-column-handles"></a><span data-ttu-id="b851b-112">行ハンドルと列ハンドル</span><span class="sxs-lookup"><span data-stu-id="b851b-112">Row and Column Handles</span></span>  
 <span data-ttu-id="b851b-113">Tablix データ領域を選択すると、行ハンドルと列ハンドルのグラフィックが各行および列の目的を示します。</span><span class="sxs-lookup"><span data-stu-id="b851b-113">When you select a tablix data region, the row and column handle graphics indicate the purpose of each row and column.</span></span> <span data-ttu-id="b851b-114">ハンドルは、グループ内に含まれている行および列、またはグループの外にある行および列を示します。</span><span class="sxs-lookup"><span data-stu-id="b851b-114">Handles indicate rows and columns that are inside a group or outside a group.</span></span> <span data-ttu-id="b851b-115">次の表で、さまざまなハンドル表示について説明します。</span><span class="sxs-lookup"><span data-stu-id="b851b-115">The following table shows a variety of handle displays.</span></span>  
  
|<span data-ttu-id="b851b-116">アイコン</span><span class="sxs-lookup"><span data-stu-id="b851b-116">Icon</span></span>|<span data-ttu-id="b851b-117">説明</span><span class="sxs-lookup"><span data-stu-id="b851b-117">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="b851b-118">![詳細行の 3 本の平行線がある行ハンドル](../media/rs-icontablix-detailsrow.gif "詳細行の 3 本の平行線がある行ハンドル")</span><span class="sxs-lookup"><span data-stu-id="b851b-118">![Row handle with 3 parallel lines for details row](../media/rs-icontablix-detailsrow.gif "Row handle with 3 parallel lines for details row")</span></span>|<span data-ttu-id="b851b-119">行グループ階層に詳細グループのみ</span><span class="sxs-lookup"><span data-stu-id="b851b-119">Only the details group on the row group hierarchy</span></span>|  
|<span data-ttu-id="b851b-120">![詳細行と 1 つの外部グループがある行ハンドル](../media/rs-icontablix-groupwithdetails.gif "詳細行と 1 つの外部グループがある行ハンドル")</span><span class="sxs-lookup"><span data-stu-id="b851b-120">![Row handle with details row and one outer group](../media/rs-icontablix-groupwithdetails.gif "Row handle with details row and one outer group")</span></span>|<span data-ttu-id="b851b-121">1 つの外部グループと子詳細グループ</span><span class="sxs-lookup"><span data-stu-id="b851b-121">One outer group and the child details group</span></span>|  
|<span data-ttu-id="b851b-122">![入れ子になったグループを示す 2 つの平行な角かっこ](../media/rs-icontablix-nestedgroupnodetails.gif "入れ子になったグループを示す 2 つの平行な角かっこ")</span><span class="sxs-lookup"><span data-stu-id="b851b-122">![Two parallel brackets showing nested groups](../media/rs-icontablix-nestedgroupnodetails.gif "Two parallel brackets showing nested groups")</span></span>|<span data-ttu-id="b851b-123">1 つの外部グループ、1 つの内部グループがあり、詳細グループはなし</span><span class="sxs-lookup"><span data-stu-id="b851b-123">One outer group, one inner group; no details group</span></span>|  
|<span data-ttu-id="b851b-124">![入れ子と詳細を示す 2 つの角かっこと三重線](../media/rs-icontablix-nestedgroupwithdetails.gif "入れ子と詳細を示す 2 つの角かっこと三重線")</span><span class="sxs-lookup"><span data-stu-id="b851b-124">![2 brackets & 3 stacked lines for nested & details](../media/rs-icontablix-nestedgroupwithdetails.gif "2 brackets & 3 stacked lines for nested & details")</span></span>|<span data-ttu-id="b851b-125">1 つの外部グループ、1 つの内部グループ、および子詳細グループ</span><span class="sxs-lookup"><span data-stu-id="b851b-125">One outer group, one inner group, and the child details group</span></span>|  
|<span data-ttu-id="b851b-126">![フッター行がある 1 つの外部グループ、1 つの内部グループ](../media/rs-icontablix-nestedgroupwithparentfooter.gif "フッター行がある 1 つの外部グループ、1 つの内部グループ")</span><span class="sxs-lookup"><span data-stu-id="b851b-126">![One outer group with footer row, one inner group](../media/rs-icontablix-nestedgroupwithparentfooter.gif "One outer group with footer row, one inner group")</span></span>|<span data-ttu-id="b851b-127">合計のフッター行のある 1 つの外部グループと、1 つの内部グループ</span><span class="sxs-lookup"><span data-stu-id="b851b-127">One outer group with a footer row for totals and one inner group</span></span>|  
|<span data-ttu-id="b851b-128">![外部グループの角かっこ、内部グループの角かっこ、詳細](../media/rs-icontablix-nestedgroupwithdetailsandtotals.gif "外部グループの角かっこ、内部グループの角かっこ、詳細")</span><span class="sxs-lookup"><span data-stu-id="b851b-128">![outer group bracket, inner group bracket, details](../media/rs-icontablix-nestedgroupwithdetailsandtotals.gif "outer group bracket, inner group bracket, details")</span></span>|<span data-ttu-id="b851b-129">合計のフッター行のある 1 つの外部グループ、合計のフッター行のある 1 つの内部グループ、および 1 つの詳細行</span><span class="sxs-lookup"><span data-stu-id="b851b-129">One outer group with a footer row for totals, one inner group with a footer row for totals, and one details row</span></span>|  
|<span data-ttu-id="b851b-130">![親ヘッダーとフッター、および子グループ](../media/rs-icontablix-nestedgroupwithparentheaderandfooter.gif "親ヘッダーとフッター、および子グループ")</span><span class="sxs-lookup"><span data-stu-id="b851b-130">![parent header and footer, and also child group](../media/rs-icontablix-nestedgroupwithparentheaderandfooter.gif "parent header and footer, and also child group")</span></span>|<span data-ttu-id="b851b-131">ラベルのヘッダーと合計のフッターのある 1 つの外部グループと、内部グループがあり、詳細グループはなし</span><span class="sxs-lookup"><span data-stu-id="b851b-131">One outer group with a header for labels and a footer for totals, and an inner group; no details group</span></span>|  
  
### <a name="group-rows"></a><span data-ttu-id="b851b-132">グループ行</span><span class="sxs-lookup"><span data-stu-id="b851b-132">Group Rows</span></span>  
 <span data-ttu-id="b851b-133">グループの内側の行は、一意のグループ値ごとに 1 回繰り返され、通常、集計サマリで使用されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-133">Rows inside a group repeat once per unique group value and are typically used for aggregate summaries.</span></span> <span data-ttu-id="b851b-134">グループの外側の行は、グループに関して 1 回繰り返され、ラベルや小計に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-134">Rows outside a group repeat once with respect to the group and are used for labels or subtotals.</span></span> <span data-ttu-id="b851b-135">Tablix セルを選択すると、Tablix データ領域内の行ハンドル、列ハンドル、および角かっこによって、セルが属するグループを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-135">When you select a tablix cell, row and column handles and brackets inside the tablix data region show the groups to which a cell belongs.</span></span> <span data-ttu-id="b851b-136">この図は、次の視覚的手掛かりを示しています。</span><span class="sxs-lookup"><span data-stu-id="b851b-136">This figure displays the following visual cues:</span></span>  
  
-   <span data-ttu-id="b851b-137">グループの関連付けを示す行ハンドルと列ハンドル</span><span class="sxs-lookup"><span data-stu-id="b851b-137">Row and column handles that indicate group associations.</span></span>  
  
-   <span data-ttu-id="b851b-138">選択したセルの最も内側のグループ メンバーシップを示す、強調表示されたグループ インジケーター</span><span class="sxs-lookup"><span data-stu-id="b851b-138">Highlighted group indicators that show the innermost group membership for a selected cell.</span></span>  
  
-   <span data-ttu-id="b851b-139">選択されたセルのすべてのグループ メンバーシップを示すグループ インジケーター</span><span class="sxs-lookup"><span data-stu-id="b851b-139">Group indicators that show all group memberships for a selected cell.</span></span>  
  
 <span data-ttu-id="b851b-140">![詳細行および入れ子になった行のグループがあるテーブル](../media/rs-tablixrowgroupvisualcues.gif "詳細行および入れ子になった行のグループがあるテーブル")</span><span class="sxs-lookup"><span data-stu-id="b851b-140">![Table with detail and nested row groups](../media/rs-tablixrowgroupvisualcues.gif "Table with detail and nested row groups")</span></span>  
  
### <a name="total-rows"></a><span data-ttu-id="b851b-141">合計行</span><span class="sxs-lookup"><span data-stu-id="b851b-141">Total Rows</span></span>  
 <span data-ttu-id="b851b-142">行および列グループを追加した後、列の合計を表示する行や、行の合計を表示する列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-142">After you add row and column groups, you can add a row to display totals for columns and a column to display totals for rows.</span></span> <span data-ttu-id="b851b-143">次の図に、行グループ、列グループ、合計行、および合計列のあるマトリックスを示します。</span><span class="sxs-lookup"><span data-stu-id="b851b-143">The following figure shows a matrix with both row and column groups, and a total row and a total column.</span></span>  
  
 <span data-ttu-id="b851b-144">![Tablix データ領域](../media/rs-tablixparts.gif "Tablix データ領域")</span><span class="sxs-lookup"><span data-stu-id="b851b-144">![Tablix data region](../media/rs-tablixparts.gif "Tablix data region")</span></span>  
  
### <a name="grouping-pane"></a><span data-ttu-id="b851b-145">グループ化ペイン</span><span class="sxs-lookup"><span data-stu-id="b851b-145">Grouping Pane</span></span>  
 <span data-ttu-id="b851b-146">グループ化ペインには、デザイン画面で現在選択されている Tablix データ領域の行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-146">The Grouping pane displays the row and column groups for the currently selected tablix data region on the design surface.</span></span> <span data-ttu-id="b851b-147">次の図に、この Tablix データ領域のグループ化ペインを示します。</span><span class="sxs-lookup"><span data-stu-id="b851b-147">The following figure shows the Grouping pane for this tablix data region.</span></span>  
  
 <span data-ttu-id="b851b-148">![入れ子になった行と列のグループのグループ化ペイン](../media/rs-basictablixdesigngroupingpanedefaultview.gif "入れ子になった行と列のグループのグループ化ペイン")</span><span class="sxs-lookup"><span data-stu-id="b851b-148">![Grouping pane for nested row and column groups](../media/rs-basictablixdesigngroupingpanedefaultview.gif "Grouping pane for nested row and column groups")</span></span>  
  
 <span data-ttu-id="b851b-149">行グループ ペインに、親グループ Category と子グループ Subcat が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-149">The Row Groups pane shows the parent group Category and child group Subcat.</span></span> <span data-ttu-id="b851b-150">列グループ ペインには、親グループ Geography と子グループ CountryRegion、および Geography グループに隣接する Year グループも表示されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-150">The Column groups pane shows the parent group Geography and child group CountryRegion, and also the Year group, which is an adjacent group to the Geography group.</span></span> <span data-ttu-id="b851b-151">行グループ ペインで Subcat グループを選択すると、グループ バーが濃いオレンジ色になり、対応する行グループのメンバー セルがデザイン画面で選択されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-151">When you select the Subcat group in the Row Groups pane, the group bar turns a darker shade of orange, and the corresponding row group member cell is selected on the design surface.</span></span>  
  
## <a name="displaying-data-on-rows-and-columns"></a><span data-ttu-id="b851b-152">行と列のデータの表示</span><span class="sxs-lookup"><span data-stu-id="b851b-152">Displaying Data on Rows and Columns</span></span>  
 <span data-ttu-id="b851b-153">行および行グループと、列および列グループには同じ関係があります。</span><span class="sxs-lookup"><span data-stu-id="b851b-153">Rows and row groups and columns and column groups have identical relationships.</span></span> <span data-ttu-id="b851b-154">次に、Tablix データ領域の行に詳細データとグループ データを表示する行を追加する方法について説明します。詳細データとグループ化されたデータを表示する列を追加する場合も基本的な方法は同じです。</span><span class="sxs-lookup"><span data-stu-id="b851b-154">The following discussion describes how to add rows to display detail and group data on rows in a tablix data region, but the same principles apply to adding columns to display detail and grouped data.</span></span>  
  
 <span data-ttu-id="b851b-155">Tablix データ領域の各行は、各行グループの内側または外側のいずれかにあります。</span><span class="sxs-lookup"><span data-stu-id="b851b-155">For each row in a tablix data region, a row is either inside or outside each row group.</span></span> <span data-ttu-id="b851b-156">行が行グループの内側にある場合、グループの一意の値ごとに行が 1 回繰り返されます。これを、 *グループ インスタンス*といいます。</span><span class="sxs-lookup"><span data-stu-id="b851b-156">If the row is inside a row group, it repeats once for every unique value of the group, known as a *group instance*.</span></span> <span data-ttu-id="b851b-157">行が行グループの外側にある場合、そのグループに対して行が 1 回繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-157">If the row is outside a row group, it repeats only once in relation to that group.</span></span> <span data-ttu-id="b851b-158">すべての行グループの外側にある行は静的で、データ領域について 1 回のみ繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-158">Rows outside all row groups are static and repeat only once for the data region.</span></span> <span data-ttu-id="b851b-159">たとえば、テーブルのヘッダー行またはフッター行は、静的な行です。</span><span class="sxs-lookup"><span data-stu-id="b851b-159">For example, a table header or footer row is a static row.</span></span> <span data-ttu-id="b851b-160">少なくとも 1 つのグループがあり、繰り返された行は動的です。</span><span class="sxs-lookup"><span data-stu-id="b851b-160">Rows that repeat with at least one group are dynamic.</span></span>  
  
 <span data-ttu-id="b851b-161">入れ子になっているグループの場合、行は、親グループの内側で、子グループの外側に配置できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-161">When you have nested groups, a row can be inside a parent group but outside a child group.</span></span> <span data-ttu-id="b851b-162">行は、親グループ内のグループ値ごとに繰り返されますが、表示されるのは、子グループに対して 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="b851b-162">The row repeats for every group value in the parent group, but displays only once in relation to the child group.</span></span> <span data-ttu-id="b851b-163">グループのラベルまたは合計を表示するには、グループの外側に行を追加します。</span><span class="sxs-lookup"><span data-stu-id="b851b-163">To display labels or totals for a group, add a row outside the group.</span></span> <span data-ttu-id="b851b-164">グループ インスタンスごとに変わるデータを表示するには、グループの内側に行を追加します。</span><span class="sxs-lookup"><span data-stu-id="b851b-164">To display data that changes for every group instance, add a row inside the group.</span></span>  
  
 <span data-ttu-id="b851b-165">詳細グループの場合、各詳細行は詳細グループの内側にあります。</span><span class="sxs-lookup"><span data-stu-id="b851b-165">When you have detail groups, each detail row is inside the detail group.</span></span> <span data-ttu-id="b851b-166">行は、データセット クエリの結果セット内の値ごとに繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-166">The row repeats for every value in the dataset query result set.</span></span>  
  
 <span data-ttu-id="b851b-167">グループ階層の詳細については、「[グループについて (レポート ビルダーおよび SSRS)](understanding-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b851b-167">For more information about group hierarchies, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b851b-168">次の図に、入れ子になった行グループと詳細グループのある Tablix データ領域を示します。</span><span class="sxs-lookup"><span data-stu-id="b851b-168">The following figure shows a tablix data region with nested row groups and a details group.</span></span>  
  
 <span data-ttu-id="b851b-169">![[デザイン] ビュー、グループとテーブルに合計行を追加](../media/rs-basictablegroupstotalscolordesign.gif "[デザイン] ビュー、グループとテーブルに合計行を追加")</span><span class="sxs-lookup"><span data-stu-id="b851b-169">![Design view, add total rows to group and table](../media/rs-basictablegroupstotalscolordesign.gif "Design view, add total rows to group and table")</span></span>  
  
 <span data-ttu-id="b851b-170">Tablix データ領域に詳細データを表示する場合、詳細グループは最も内側の子グループです。</span><span class="sxs-lookup"><span data-stu-id="b851b-170">For a tablix data region that displays detail data, the details group is the innermost child group.</span></span> <span data-ttu-id="b851b-171">詳細グループに追加される行は、この Tablix データ領域にリンクされているデータセットのクエリの結果セットに含まれている行ごとに 1 回繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-171">Rows that you add to a details group repeat once per row in the result set for the query for the dataset linked to this tablix data region.</span></span> <span data-ttu-id="b851b-172">次の図に、表示されたレポートの最後のページを示します。</span><span class="sxs-lookup"><span data-stu-id="b851b-172">The following figure shows the last page of the rendered report.</span></span> <span data-ttu-id="b851b-173">この図には、最新の詳細行と、最新の発注の小計行が示されています。</span><span class="sxs-lookup"><span data-stu-id="b851b-173">In this figure, you can see the last detail rows and the subtotal row for the last order.</span></span>  
  
 <span data-ttu-id="b851b-174">![プレビュー、グループ合計があるテーブル、最後の行](../media/rs-basictablegroupstotalscolorpreviewbottom.gif "プレビュー、グループ合計があるテーブル、最後の行")</span><span class="sxs-lookup"><span data-stu-id="b851b-174">![Preview, Table with Group Totals, last rows](../media/rs-basictablegroupstotalscolorpreviewbottom.gif "Preview, Table with Group Totals, last rows")</span></span>  
  
 <span data-ttu-id="b851b-175">Tablix データ領域内の各列についても同様です。</span><span class="sxs-lookup"><span data-stu-id="b851b-175">For each column in a tablix data region, the same principles apply.</span></span> <span data-ttu-id="b851b-176">たとえば、列は、各列グループの内側または外側のいずれかにあり、合計を表示するには、グループの外側に列を追加します。</span><span class="sxs-lookup"><span data-stu-id="b851b-176">For example, a column is either inside or outside each column group; to display totals, add a column outside the group.</span></span>  
  
 <span data-ttu-id="b851b-177">グループに関連付けられている行および列を削除するため、そのグループを削除できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-177">To remove rows and columns associated to a group, you can delete the group.</span></span> <span data-ttu-id="b851b-178">グループを削除する場合、グループ定義のみを削除する方法と、グループおよび関連付けられているすべての行および列を削除する方法があります。</span><span class="sxs-lookup"><span data-stu-id="b851b-178">When you delete a group, you have the choice between deleting the group definition only or deleting the group and all its associated rows and columns.</span></span> <span data-ttu-id="b851b-179">グループのみを削除すると、データ領域で行および列レイアウトが維持されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-179">By deleting just the group, you preserve the row and column layout on the data region.</span></span> <span data-ttu-id="b851b-180">グループとその関連行および列を削除すると、そのグループに関連付けられているすべての静的な行および列 (グループ ヘッダーおよびフッターを含む) と、動的な行および列 (グループ インスタンスを含む) が削除されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-180">When you delete the group and its related rows and columns, you are deleting all static rows and columns (including group headers and footers) and dynamic rows and columns (including group instances) that are associated with that group.</span></span>  
  
 <span data-ttu-id="b851b-181">行および列の追加または削除の詳細な手順については、「[列の挿入または削除 (レポート ビルダーおよび SSRS)](insert-or-delete-a-row-report-builder-and-ssrs.md)」および「[列の挿入または削除 (レポート ビルダーおよび SSRS)](insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b851b-181">For step-by-step instructions about adding or deleting rows and columns, see [Insert or Delete a Row &#40;Report Builder and SSRS&#41;](insert-or-delete-a-row-report-builder-and-ssrs.md) and [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
## <a name="understanding-tablix-cells"></a><span data-ttu-id="b851b-182">Tablix セルについて</span><span class="sxs-lookup"><span data-stu-id="b851b-182">Understanding Tablix Cells</span></span>  
 <span data-ttu-id="b851b-183">Tablix セルは 4 つの Tablix 領域 (Tablix 本体、Tablix 行グループ領域、Tablix 列グループ領域、または Tablix コーナー) のいずれかに属します。</span><span class="sxs-lookup"><span data-stu-id="b851b-183">Tablix cells belong to one of four tablix areas: the tablix body, tablix row or tablix column group areas, or the tablix corner.</span></span> <span data-ttu-id="b851b-184">各セルにはデータセット内の任意の値を表示できますが、セルごとの既定の機能はその場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b851b-184">Although each cell can potentially display any value in the dataset, the default function for each cell is determined by its location.</span></span> <span data-ttu-id="b851b-185">Tablix 領域の詳細については、「[Tablix データ領域部分 (レポート ビルダーおよび SSRS)](tablix-data-region-areas-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b851b-185">For detailed information about tablix areas, see [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b851b-186">既定では、Tablix 行および列グループ領域内のセルはグループ メンバーを表します。</span><span class="sxs-lookup"><span data-stu-id="b851b-186">By default, cells in tablix row and column group areas represent group members.</span></span> <span data-ttu-id="b851b-187">グループのメンバーは、レポート定義で複数のツリー構造に分類されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-187">Group members are organized into multiple tree structures in the report definition.</span></span> <span data-ttu-id="b851b-188">行グループ階層は水平方向に展開します。</span><span class="sxs-lookup"><span data-stu-id="b851b-188">The row group hierarchy expands horizontally.</span></span> <span data-ttu-id="b851b-189">列グループ階層は垂直方向に展開します。</span><span class="sxs-lookup"><span data-stu-id="b851b-189">The column group hierarchy expands vertically.</span></span> <span data-ttu-id="b851b-190">グループを作成すると、これらのセルが自動的に追加され、実行時にグループの一意の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-190">These cells are added automatically when you create a group, and display the unique values for a group at run time.</span></span>  
  
 <span data-ttu-id="b851b-191">行および列グループ領域の両方が存在する場合は、Tablix コーナーのセルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-191">Cells in the tablix corner are created when there are both row and column group areas.</span></span> <span data-ttu-id="b851b-192">この領域にセルを結合してラベルを作成したり、別のレポート アイテムを埋め込んだりできます。</span><span class="sxs-lookup"><span data-stu-id="b851b-192">You can merge cells in this area to create a label or embed another report item.</span></span>  
  
 <span data-ttu-id="b851b-193">Tablix 本体領域のセルには、セルが詳細行または詳細列内にある場合は詳細データを、セルがグループ行またはグループ列内にある場合は集計グループ データを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-193">Cells in the tablix body area can display detail data when the cell is in a detail row or column and aggregated group data when the cell is in a group row or column.</span></span> <span data-ttu-id="b851b-194">セルのデータのスコープは、そのセルが属する最も内側の行グループと最も内側の列グループの交点です。</span><span class="sxs-lookup"><span data-stu-id="b851b-194">The scope for the data in a cell is the intersection of the innermost row group and innermost column group to which the cell belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b851b-195">各セルについて表示される実際のデータは、セルに含まれているレポート アイテムの評価済みの式 (通常、テキスト ボックス) です。</span><span class="sxs-lookup"><span data-stu-id="b851b-195">The actual data that is displayed for each cell is the evaluated expression for the report item that the cell contains, which is typically a text box.</span></span> <span data-ttu-id="b851b-196">詳細行または詳細列に属するセルの場合、式は既定で詳細データ (例: **[LineTotal]**) になります。</span><span class="sxs-lookup"><span data-stu-id="b851b-196">In a cell that belongs to a detail row or column, the expression defaults to the detail data (for example, **[LineTotal])**.</span></span> <span data-ttu-id="b851b-197">詳細行または詳細列に属さないセルの場合、式は既定で集計関数 (例: **Sum[LineTotal]**) になります。</span><span class="sxs-lookup"><span data-stu-id="b851b-197">In a cell that does not belong to a detail row or column, the expression defaults to an aggregate function (for example, **Sum[LineTotal])**.</span></span> <span data-ttu-id="b851b-198">セルがグループ行またはグループ列に属していても、式で集計関数が指定されていない場合、グループ内の最初の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b851b-198">If an expression does not specify an aggregate function even though the cell belongs to a group row or column, the first value in the group is displayed.</span></span> <span data-ttu-id="b851b-199">集計の詳細については、「[合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b851b-199">For more information about aggregates, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
### <a name="merging-and-splitting-cells"></a><span data-ttu-id="b851b-200">セルの結合と分割</span><span class="sxs-lookup"><span data-stu-id="b851b-200">Merging and Splitting Cells</span></span>  
 <span data-ttu-id="b851b-201">Tablix 領域内では、隣接する複数のセルを結合できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-201">Inside a tablix area, you can merge multiple adjacent cells together.</span></span> <span data-ttu-id="b851b-202">たとえば、複数の列または行にまたがるラベルのセルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-202">For example, you can create cells for labels that span multiple columns or rows.</span></span>  
  
 <span data-ttu-id="b851b-203">Tablix コーナー領域では、一度に 1 方向にのみセルを結合できます。たとえば、列を水平方向に結合したり、行を垂直方向に結合したりできます。</span><span class="sxs-lookup"><span data-stu-id="b851b-203">In the tablix corner area, cells can be combined in only one direction at a time: horizontally across columns or vertically down rows.</span></span> <span data-ttu-id="b851b-204">セルのブロックを結合するには、まずセルを水平方向に結合します。</span><span class="sxs-lookup"><span data-stu-id="b851b-204">To merge a block of cells, merge the cells horizontally first.</span></span> <span data-ttu-id="b851b-205">すべてのセルを各行内の 1 つのセルに結合した後、隣接するセルを選択し (列内のすべての隣接するセルを選択できます)、結合します。</span><span class="sxs-lookup"><span data-stu-id="b851b-205">After all cells have been merged into a single cell in each row, select adjacent cells (you can select all adjacent cells in a column) and merge them.</span></span>  
  
 <span data-ttu-id="b851b-206">Tablix 本体領域では、セルは水平方向にのみ結合できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-206">In the tablix body area, cells can only be merged horizontally.</span></span> <span data-ttu-id="b851b-207">垂直方向のセルの結合はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b851b-207">Merging cells vertically is not supported.</span></span>  
  
 <span data-ttu-id="b851b-208">詳細については、「[データ領域内のセルの結合 &#40;レポート ビルダーおよび SSRS&#41;](merge-cells-in-a-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b851b-208">For more information, see [Merge Cells in a Data Region &#40;Report Builder and SSRS&#41;](merge-cells-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b851b-209">以前に結合したセルを分割できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-209">You can split a cell that was previously merged.</span></span> <span data-ttu-id="b851b-210">セルを水平方向に列に分割するか、垂直方向に行に分割できます。</span><span class="sxs-lookup"><span data-stu-id="b851b-210">You can split cells horizontally across columns or vertically down rows.</span></span> <span data-ttu-id="b851b-211">セルを、セルのブロックに分割するには、最初にセルを水平方向に分割し、次に、垂直方向に必要な数だけ分割します。</span><span class="sxs-lookup"><span data-stu-id="b851b-211">To split a cell into a block of cells, split the cell horizontally first, and then split vertically as many times as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b851b-212">参照</span><span class="sxs-lookup"><span data-stu-id="b851b-212">See Also</span></span>  
 [<span data-ttu-id="b851b-213">Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b851b-213">Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](../tablix-data-region-report-builder-and-ssrs.md)  
  
  