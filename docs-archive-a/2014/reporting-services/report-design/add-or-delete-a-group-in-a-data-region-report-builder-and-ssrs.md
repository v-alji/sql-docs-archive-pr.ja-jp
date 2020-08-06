---
title: データ領域でのグループの追加または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4de53c3c-c6fc-49ce-b692-3609fc0b3ec5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c355ca87db578d47181935e1ca6bc48e75bf8b8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719605"
---
# <a name="add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="0c70b-102">データ領域でのグループの追加または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="0c70b-102">Add or Delete a Group in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0c70b-103">計算や表示の対象として、特定の値または式のセットによってデータを整理する場合は、グループをデータ領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-103">Add a group to a data region when you want to organize data by a specific value or set of expressions, for display and calculations.</span></span> <span data-ttu-id="0c70b-104">グループには、データセットのどのデータがそのグループに含まれるかを示す名前と式を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-104">A group has a name and an expression that identifies which data from a dataset belongs to the group.</span></span> <span data-ttu-id="0c70b-105">グループの詳細については、「 [グループについて (レポート ビルダーおよび SSRS)](understanding-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c70b-105">For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="0c70b-106">Tablix データ領域で、テーブル、マトリックス、または一覧をクリックすると、グループ化ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-106">In a tablix data region, click in the table, matrix, or list to display the Grouping pane.</span></span> <span data-ttu-id="0c70b-107">親グループまたは子グループを作成するには、データセット フィールドを [列グループと行グループ] ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-107">Drag dataset fields to the Row Group and Column Group pane to create parent or child groups.</span></span> <span data-ttu-id="0c70b-108">既存のグループを右クリックして、隣接するグループを追加します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-108">Right-click an existing group to add an adjacent group.</span></span> <span data-ttu-id="0c70b-109">定義上、詳細グループは最も内側のグループで、子グループとしてのみ追加できます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-109">By definition, the details group is the innermost group and can only be added as a child group.</span></span> <span data-ttu-id="0c70b-110">既存のグループを削除するには、右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-110">Right-click an existing group to delete it.</span></span> <span data-ttu-id="0c70b-111">グループ値が表示される行および列が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-111">Rows and columns on which to display group values are automatically added for you.</span></span> <span data-ttu-id="0c70b-112">詳細については、「 [テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c70b-112">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="0c70b-113">グラフ データ領域で、グラフをクリックすると、ドロップ ゾーンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-113">In a Chart data region, click in the chart to display the drop-zones.</span></span> <span data-ttu-id="0c70b-114">データセット フィールドをカテゴリ ドロップ ゾーンと系列ドロップ ゾーンにドラッグすると、グループが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-114">Create groups by dragging dataset fields to the category and series drop zones.</span></span> <span data-ttu-id="0c70b-115">入れ子になったグループを追加するには、複数のフィールドをドロップ ゾーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-115">To add nested groups, add multiple fields to the drop-zone.</span></span>  
  
 <span data-ttu-id="0c70b-116">グループは既定では、ゲージ内で定義されていません。</span><span class="sxs-lookup"><span data-stu-id="0c70b-116">Groups are not defined in a gauge by default.</span></span> <span data-ttu-id="0c70b-117">ゲージの既定の動作では、特定のフィールド内のすべての値が 1 つの値に集計され、ゲージに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-117">The default behavior for the gauge is to aggregate all values in the specified field into one value that is displayed on the gauge.</span></span> <span data-ttu-id="0c70b-118">詳しくは、「 [ゲージ &#40;レポート ビルダーおよび SSRS&#41;](gauges-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0c70b-118">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-parent-or-child-row-or-column-group-to-a-tablix-data-region"></a><span data-ttu-id="0c70b-119">親行、子行、または列グループを Tablix データ領域に追加するには</span><span class="sxs-lookup"><span data-stu-id="0c70b-119">To add a parent or child row or column group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="0c70b-120">フィールドを、 **[レポート データ]** ペインから **[行グループ]** ペインまたは **[列グループ]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-120">Drag a field from the **Report Data** pane to the **Row Groups** pane or the **Column Groups** pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c70b-121">グループ化ペインが表示されない場合は、[表示] タブの **[グループ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-121">If you do not see the Grouping pane, on the View tab, click **Grouping**.</span></span>  
  
2.  <span data-ttu-id="0c70b-122">グループを既存のグループの親グループまたは子グループとして配置するには、ガイド バーを使用してグループの上位または下位の階層にフィールドをドロップします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-122">Drop the field above or below the group hierarchy using the guide bar to place the group as a parent group or a child group to an existing group.</span></span>  
  
     <span data-ttu-id="0c70b-123">既定の名前、グループ式、およびフィールド名に基づく並べ替え式がグループに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-123">The group is added with a default name, group expression, and sort expression that is based on the field name.</span></span>  
  
### <a name="to-add-an-adjacent-row-or-column-group-to-a-tablix-data-region"></a><span data-ttu-id="0c70b-124">隣接する行または列グループを Tablix データ領域に追加するには</span><span class="sxs-lookup"><span data-stu-id="0c70b-124">To add an adjacent row or column group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="0c70b-125">グループ化ペインで、追加するグループを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-125">In the Grouping pane, right-click a group that is a peer to the group that you want to add.</span></span> <span data-ttu-id="0c70b-126">**[グループの追加]** をクリックし、 **[前に隣接]** または **[後に隣接]** をクリックして、グループを追加する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-126">Click **Add Group**, and then click **Adjacent Before** or **Adjacent After** to specify where to add the group.</span></span> <span data-ttu-id="0c70b-127">**[Tablix のグループ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-127">The **Tablix Group** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="0c70b-128">**[名前]** に、グループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-128">In **Name**, type a name for the group.</span></span>  
  
3.  <span data-ttu-id="0c70b-129">**[グループ式]** で、式を入力するか式ボタン ( **[fx]** ) をクリックして、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-129">In **Group expression**, type an expression or click the expression button (**fx**) to create an expression.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="0c70b-130">新しいグループがグループ化ペインに追加され、グループ値を表示する行または列がデザイン画面の Tablix データ領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-130">A new group is added to the Grouping pane and a row or column on which to display group values is added to the tablix data region on the design surface.</span></span>  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a><span data-ttu-id="0c70b-131">詳細グループを Tablix データ領域に追加するには</span><span class="sxs-lookup"><span data-stu-id="0c70b-131">To add a details group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="0c70b-132">グループ化ペインで、最も内側の子グループであり、 **詳細** グループではないグループを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-132">In the Grouping pane, right-click a group that is the innermost child group, but not the **Details** group.</span></span> <span data-ttu-id="0c70b-133">**[グループの追加]** をクリックし、 **[子グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-133">Click **Add Group**, and then click **Child Group**.</span></span> <span data-ttu-id="0c70b-134">**[Tablix のグループ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-134">The **Tablix Group** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="0c70b-135">**[グループ式]** で式を空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-135">In **Group expression**, leave the expression blank.</span></span> <span data-ttu-id="0c70b-136">詳細グループには式がありません。</span><span class="sxs-lookup"><span data-stu-id="0c70b-136">A details group has no expression.</span></span>  
  
3.  <span data-ttu-id="0c70b-137">**[詳細データの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-137">Select **Show detail data**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="0c70b-138">グループ化ペインで新しい詳細グループが子グループとして追加され、手順 1. で選択したグループの行ハンドルに詳細グループ アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-138">A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon.</span></span> <span data-ttu-id="0c70b-139">Tablix データ領域に関する詳細については、「[Tablix データ領域のセル、行、および列 &#40;レポート ビルダーおよび SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c70b-139">For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-edit-a-row-or-column-group-in-a-tablix-data-region"></a><span data-ttu-id="0c70b-140">Tablix データ領域の行または列グループを編集するには</span><span class="sxs-lookup"><span data-stu-id="0c70b-140">To edit a row or column group in a tablix data region</span></span>  
  
1.  <span data-ttu-id="0c70b-141">レポート デザイン画面で、Tablix データ領域の任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-141">On the report design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="0c70b-142">グループ化ペインに行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-142">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="0c70b-143">グループを右クリックし、 **[グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-143">Right-click the group, and then click **Group Properties**.</span></span>  
  
3.  <span data-ttu-id="0c70b-144">**[名前]** ボックスに、グループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-144">In **Name**, type the name of the group.</span></span>  
  
4.  <span data-ttu-id="0c70b-145">**[グループ式]** で、単純な式を入力または選択するか、式ボタン ( **[fx]** ) をクリックして、グループ式を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-145">In **Group expressions**, type or select a simple expression, or click the Expression (**fx**) button to create a group expression.</span></span>  
  
5.  <span data-ttu-id="0c70b-146">**[追加]** をクリックして追加の式を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-146">Click **Add** to create additional expressions.</span></span> <span data-ttu-id="0c70b-147">指定するすべての式が論理 AND を使用して結合され、このグループのデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-147">All expressions you specify are combined using a logical AND to specify data for this group.</span></span>  
  
6.  <span data-ttu-id="0c70b-148">(省略可) **[改ページ]** をクリックして、改ページ オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-148">(Optional) Click **Page Breaks** to set page break options.</span></span>  
  
7.  <span data-ttu-id="0c70b-149">(省略可) **[並べ替え]** をクリックし、グループ内の値の並べ替え順を指定する式を選択または入力します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-149">(Optional) Click **Sorting** to select or type expressions that specify the sort order for values in the group.</span></span>  
  
8.  <span data-ttu-id="0c70b-150">(省略可) **[表示]** タブをクリックし、アイテムの表示オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-150">(Optional) Click **Visibility** to select the visibility options for the item.</span></span>  
  
9. <span data-ttu-id="0c70b-151">(省略可) **[フィルター]** をクリックし、このグループにフィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-151">(Optional) Click **Filters** to set filters for this group.</span></span>  
  
10. <span data-ttu-id="0c70b-152">(省略可) **[変数]** をクリックし、このグループを対象とし、任意の子グループからアクセス可能な変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-152">(Optional) Click **Variables** to define variables scoped to this group and accessible from any child groups.</span></span>  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-group-from-a-tablix-data-region"></a><span data-ttu-id="0c70b-153">Tablix データ領域からグループを削除するには</span><span class="sxs-lookup"><span data-stu-id="0c70b-153">To delete a group from a tablix data region</span></span>  
  
1.  <span data-ttu-id="0c70b-154">グループ化ペインで、グループを右クリックし、 **[グループの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-154">In the Grouping pane, right-click the group, and then click **Delete Group**.</span></span>  
  
2.  <span data-ttu-id="0c70b-155">**[グループの削除]** ダイアログ ボックスで、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-155">In the **Delete Group** dialog box, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="0c70b-156">**[グループおよび関連する行と列を削除する]** グループ定義およびグループ データを表示するすべての関連する行を削除する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-156">**Delete group and related rows and columns** Choose this option to delete the group definition and all related rows that display group data.</span></span> <span data-ttu-id="0c70b-157">詳細グループでは、同じ行が詳細データとグループ データの両方に属している場合、詳細データ行のみが削除されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-157">For the details group, if the same row belongs to both detail and group data, only the detail data rows are deleted.</span></span>  
  
    -   <span data-ttu-id="0c70b-158">**[グループのみを削除]** Tablix データ領域の構造を変えずにグループ定義のみを削除する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-158">**Delete group only** Choose this option to keep the structure of the tablix data region the same and delete only the group definition.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-details-group-from-a-tablix-data-region"></a><span data-ttu-id="0c70b-159">Tablix データ領域から詳細グループを削除するには</span><span class="sxs-lookup"><span data-stu-id="0c70b-159">To delete a details group from a tablix data region</span></span>  
  
1.  <span data-ttu-id="0c70b-160">グループ化ペインで、詳細グループを右クリックし、 **[グループの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c70b-160">In the Grouping pane, right-click the details group, and then click **Delete Group**.</span></span>  
  
2.  <span data-ttu-id="0c70b-161">**[グループの削除]** ダイアログ ボックスで、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-161">In the **Delete Group** dialog box, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="0c70b-162">**[グループおよび関連する行と列を削除する]** グループ定義およびグループ データを表示するすべての関連する行を削除する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-162">**Delete group and related rows and columns** Choose this option to delete the group definition and all related rows that display group data.</span></span> <span data-ttu-id="0c70b-163">詳細グループでは、同じ行が詳細データとグループ データの両方に属している場合、詳細データ行のみが削除されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-163">For the details group, if the same row belongs to both detail and group data, only the detail data rows are deleted.</span></span>  
  
    -   <span data-ttu-id="0c70b-164">**[グループのみを削除]** Tablix データ領域の構造を変えずにグループ定義のみを削除する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-164">**Delete group only** Choose this option to keep the structure of the tablix data region the same and delete only the group definition.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="0c70b-165">詳細グループが削除されます。</span><span class="sxs-lookup"><span data-stu-id="0c70b-165">The details group is deleted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c70b-166">詳細行を削除したら、各セルの式には適切な集計式が指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-166">Verify that after you remove a details row, the expression in each cell specifies an aggregate expression where appropriate.</span></span> <span data-ttu-id="0c70b-167">必要に応じて、式を編集して集計関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c70b-167">If necessary, edit the expression to specify aggregate functions as needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c70b-168">参照</span><span class="sxs-lookup"><span data-stu-id="0c70b-168">See Also</span></span>  
 <span data-ttu-id="0c70b-169">[レポート変数コレクションとグループ変数コレクションの参照 (レポート ビルダーおよび SSRS)](built-in-collections-report-and-group-variables-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="0c70b-169">[Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md) </span></span>  
 <span data-ttu-id="0c70b-170">[グループ式の例 &#40;レポート ビルダーおよび SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0c70b-170">[Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0c70b-171">[データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0c70b-171">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0c70b-172">[Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0c70b-172">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0c70b-173">[テーブル &#40;レポート ビルダーおよび SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0c70b-173">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0c70b-174">[マトリックス &#40;レポート ビルダーおよび SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0c70b-174">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0c70b-175">[一覧 &#40;レポート ビルダーおよび SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0c70b-175">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0c70b-176">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0c70b-176">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
