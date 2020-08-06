---
title: グループ単位でのヘッダーとフッターの表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8eb7d648-4df2-491a-96cb-99e55629d617
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: adbb3674a16fc77d04ac3ac490a284894588c657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640700"
---
# <a name="display-headers-and-footers-with-a-group-report-builder-and-ssrs"></a><span data-ttu-id="03af1-102">グループ単位でのヘッダーとフッターの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="03af1-102">Display Headers and Footers with a Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="03af1-103">Tablix データ領域では、グループに関連付けられている動的行と一緒に、静的行 (グループ ヘッダー、グループ フッターなど) を表示するかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="03af1-103">You can help control whether a static row, such as a group header or footer, renders with dynamic rows that are associated with a group in a tablix data region.</span></span>  
  
 <span data-ttu-id="03af1-104">複数のページですべての列見出しまたは行見出しを繰り返し表示するには、Tablix データ領域のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="03af1-104">To repeat all the column headings or row headings on multiple pages, you can set properties for the tablix data region.</span></span> <span data-ttu-id="03af1-105">詳細については、「[複数のページへの行および列ヘッダーの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03af1-105">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="03af1-106">入れ子になったグループに関連付けられている動的行と動的列の表示動作、または、ラベルや小計に関連付けられている静的行と静的列の表示動作を制御するには、Tablix メンバーのプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03af1-106">To control the rendering behavior for dynamic rows and columns that are associated with nested groups, or for static rows and columns that are associated with labels or subtotals, you must set properties for the tablix member.</span></span> <span data-ttu-id="03af1-107">Tablix メンバーは、静的な行または列、あるいは動的な行または列を表します。</span><span class="sxs-lookup"><span data-stu-id="03af1-107">A tablix member represents a static or dynamic row or column.</span></span> <span data-ttu-id="03af1-108">静的メンバーが表示されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="03af1-108">A static member repeats once.</span></span> <span data-ttu-id="03af1-109">たとえば、代表的な静的行に、総計行があります。</span><span class="sxs-lookup"><span data-stu-id="03af1-109">For example, a grand total row is a static row.</span></span> <span data-ttu-id="03af1-110">動的メンバーは、1 グループにつき 1 回表示されます。</span><span class="sxs-lookup"><span data-stu-id="03af1-110">A dynamic member repeats once for each group instance.</span></span> <span data-ttu-id="03af1-111">たとえば、特定のグループに対し [Territory] というグループ式が割り当てられているとき、そのグループに関連付けられている行は、一意の区域 (territory) 値ごとに 1 回表示されることになります。</span><span class="sxs-lookup"><span data-stu-id="03af1-111">For example, a row that is associated with a group that has the group expression [Territory] repeats once for each unique value for territory.</span></span> <span data-ttu-id="03af1-112">Tablix のメンバーに関する詳細については、「[Tablix データ領域のセル、行、および列 &#40;レポート ビルダーおよび SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03af1-112">For more information about tablix members, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="03af1-113">Tablix メンバーのプロパティを設定するには、グループ化ペインで Tablix メンバーを選択し、プロパティ ペインで **KeepWithGroup**、 **KeepTogether**、および **RepeatOnNewPage** の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="03af1-113">You can select a tablix member in the Grouping pane and set the properties **KeepWithGroup**, **KeepTogether**, and **RepeatOnNewPage** in the Properties pane.</span></span> <span data-ttu-id="03af1-114">グループ ヘッダーとグループ フッターをグループと同じページに表示するには、 **KeepWithGroup** を使用します。</span><span class="sxs-lookup"><span data-stu-id="03af1-114">Use **KeepWithGroup** to help display group headers and footers on the same page as the group.</span></span> <span data-ttu-id="03af1-115">グループの行または列と一緒に静的メンバーを表示するには、 **KeepTogether** を使用します。</span><span class="sxs-lookup"><span data-stu-id="03af1-115">Use **KeepTogether** to help display static members with the rows or columns of a group.</span></span> <span data-ttu-id="03af1-116">**KeepWithGroup** 値によって指定された行グループ メンバーの少なくとも 1 つの完全なインスタンスが表示されるページごとにグループ ヘッダーまたはグループ フッターを繰り返すには、 **RepeatOnNewPage** を使用します。</span><span class="sxs-lookup"><span data-stu-id="03af1-116">Use **RepeatOnNewPage** to repeat the group header or footer on every page that displays at least one complete instance of the row group member designated by the **KeepWithGroup** value.</span></span> <span data-ttu-id="03af1-117">列グループ メンバーに対して、**RepeatOnNewPage** はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="03af1-117">**RepeatOnNewPage** is not supported for column group members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03af1-118">**KeepWithGroup**、**KeepTogether**、および **RepeatOnNewPage** は、グループ化ペインの **[詳細設定モード]** を使用して設定できるグループ メンバーのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="03af1-118">**KeepWithGroup**, **KeepTogether**, and **RepeatOnNewPage** are group member properties that you can set by using the **Advanced Mode** of the Grouping pane.</span></span> <span data-ttu-id="03af1-119">詳細については、「[グループ化ペイン &#40;レポート ビルダー&#41;](grouping-pane-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03af1-119">For more information, see [Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-a-static-row-with-a-set-of-dynamic-rows-associated-with-a-row-group"></a><span data-ttu-id="03af1-120">静的行を行グループに関連付けられている一連の動的行と一緒に表示するには</span><span class="sxs-lookup"><span data-stu-id="03af1-120">To keep a static row with a set of dynamic rows associated with a row group</span></span>  
  
1.  <span data-ttu-id="03af1-121">デザイン画面で、Tablix データ領域の任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-121">On the design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="03af1-122">グループ化ペインに、データ領域の行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03af1-122">The Grouping pane displays the row and column groups for the data region.</span></span>  
  
2.  <span data-ttu-id="03af1-123">グループ化ペインの右側にある下矢印をクリックし、 **[詳細設定モード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03af1-123">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="03af1-124">行グループ ペインには、行グループ階層の静的メンバーおよび動的メンバーが階層的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="03af1-124">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy.</span></span>  
  
3.  <span data-ttu-id="03af1-125">グループ行と共に維持する行ヘッダーまたは行フッターに対応する静的メンバーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03af1-125">Click the static member that corresponds to the row header or footer that you want to keep with the group rows.</span></span> <span data-ttu-id="03af1-126">プロパティ ペインに **[Tablix メンバー]** プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03af1-126">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
4.  <span data-ttu-id="03af1-127">プロパティ ペインで、 **KeepWithGroup**をクリックし、ドロップダウン リストから次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-127">In the Properties pane, click **KeepWithGroup**, and then choose one of the following values from the drop-down list:</span></span>  
  
    -   <span data-ttu-id="03af1-128">**[なし]** 選択した行グループのメンバーと共にこのメンバーを維持しない場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-128">**None** Select this option to indicate no preference for keeping this member with the members of the selected row group.</span></span>  
  
    -   <span data-ttu-id="03af1-129">**[前]** 前のグループのメンバーと共にこのメンバーを維持する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-129">**Before** Select this option to keep this member with the members of the previous group.</span></span> <span data-ttu-id="03af1-130">このオプションはグループ フッター行に使用できます。</span><span class="sxs-lookup"><span data-stu-id="03af1-130">You might use this for group footer rows.</span></span>  
  
    -   <span data-ttu-id="03af1-131">**[後]** 次のグループのメンバーと共にこのメンバーを維持する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-131">**After** Select this option to keep this member with the members of the following group.</span></span> <span data-ttu-id="03af1-132">このオプションはグループ ヘッダー行に使用できます。</span><span class="sxs-lookup"><span data-stu-id="03af1-132">You might use this for group header rows.</span></span>  
  
5.  <span data-ttu-id="03af1-133">(省略可) レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="03af1-133">(Optional) Preview the report.</span></span> <span data-ttu-id="03af1-134">レポート レンダラーは、可能な限り、指定された行グループ メンバーと共にこのメンバーを維持します。</span><span class="sxs-lookup"><span data-stu-id="03af1-134">Where possible, the report renderer keeps this member with the specified row group members.</span></span>  
  
### <a name="to-keep-a-static-column-with-a-set-of-dynamic-columns-associated-with-a-column-group"></a><span data-ttu-id="03af1-135">静的列を列グループに関連付けられている一連の動的列と一緒に表示するには</span><span class="sxs-lookup"><span data-stu-id="03af1-135">To keep a static column with a set of dynamic columns associated with a column group</span></span>  
  
1.  <span data-ttu-id="03af1-136">デザイン画面で、Tablix データ領域の任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-136">On the design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="03af1-137">グループ化ペインに、データ領域の行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03af1-137">The Grouping pane displays the row and column groups for the data region.</span></span>  
  
2.  <span data-ttu-id="03af1-138">グループ化ペインの右側にある下矢印をクリックし、 **[詳細設定モード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03af1-138">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="03af1-139">列グループ ペインには、列グループ階層の静的メンバーおよび動的メンバーが階層的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="03af1-139">The Column Groups pane displays the hierarchical static and dynamic members for the column group hierarchy.</span></span>  
  
3.  <span data-ttu-id="03af1-140">グループ列と共に維持する静的列に対応する静的メンバーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03af1-140">Click the static member that corresponds to the static column that you want to keep with the group columns.</span></span> <span data-ttu-id="03af1-141">プロパティ ペインに **[Tablix メンバー]** プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03af1-141">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
4.  <span data-ttu-id="03af1-142">プロパティ ペインで、 **KeepWithGroup**をクリックし、ドロップダウン リストから次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-142">In the Properties pane, click **KeepWithGroup**, and then choose one of the following values from the drop-down list:</span></span>  
  
    -   <span data-ttu-id="03af1-143">**[なし]** 選択した列グループのメンバーと共にこのメンバーを維持しない場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-143">**None** Select this option to indicate no preference for keeping this member with the members of the selected column group.</span></span>  
  
    -   <span data-ttu-id="03af1-144">**[前]** 前のグループのメンバーと共にこのメンバーを維持する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-144">**Before** Select this option to keep this member with the members of the previous group.</span></span> <span data-ttu-id="03af1-145">このオプションは、指定した列グループ メンバーの前に表示する列ラベルに使用できます。</span><span class="sxs-lookup"><span data-stu-id="03af1-145">You might use this for column labels that display before the specified column group members.</span></span>  
  
    -   <span data-ttu-id="03af1-146">**[後]** 次のグループのメンバーと共にこのメンバーを維持する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="03af1-146">**After** Select this option to keep this member with the members of the following group.</span></span> <span data-ttu-id="03af1-147">このオプションは、指定した列グループ メンバーの後に表示する列の合計に使用できます。</span><span class="sxs-lookup"><span data-stu-id="03af1-147">You might use this for column totals that display after the specified column group members.</span></span>  
  
5.  <span data-ttu-id="03af1-148">(省略可) レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="03af1-148">(Optional) Preview the report.</span></span> <span data-ttu-id="03af1-149">可能な限り、レポート レンダラーは指定された列グループ メンバーと共にこのメンバーを維持します。</span><span class="sxs-lookup"><span data-stu-id="03af1-149">Where possible, the report renderer keeps this member with the specified column group members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03af1-150">参照</span><span class="sxs-lookup"><span data-stu-id="03af1-150">See Also</span></span>  
 <span data-ttu-id="03af1-151">[Tablix データ領域のセル、行、および列 &#40;レポートビルダー&#41; および SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03af1-151">[Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03af1-152">[Tablix データ領域の領域 &#40;レポートビルダーと SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03af1-152">[Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03af1-153">[Tablix データ領域 &#40;レポートビルダーと SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03af1-153">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03af1-154">[テーブル &#40;レポートビルダーと SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03af1-154">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03af1-155">[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03af1-155">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="03af1-156">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="03af1-156">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="03af1-157">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="03af1-157">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
