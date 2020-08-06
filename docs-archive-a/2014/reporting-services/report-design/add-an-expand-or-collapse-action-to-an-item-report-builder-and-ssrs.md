---
title: アイテムへの展開または折りたたみアクションの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49f07ad6-242b-4861-8fc1-91ca78c36d6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 331c6a14a4a898ffcdf86f274c00e7ad3c801ec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712742"
---
# <a name="add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs"></a><span data-ttu-id="d2dc1-102">アイテムへの展開または折りたたみアクションの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d2dc1-102">Add an Expand or Collapse Action to an Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d2dc1-103">レポート アイテムの展開と折りたたみや、グループと関連付けられているテーブルやマトリックスの行と列の展開と折りたたみを、ユーザーが対話形式で行うようにできます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-103">You can enable a user to interactively expand or collapse report items, or expand or collapse rows and columns associated with a group for a table or matrix.</span></span> <span data-ttu-id="d2dc1-104">アイテムの展開と折りたたみをユーザーが行うようにするには、アイテムの表示プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-104">To allow users to expand or collapse an item, you set the visibility properties for that item.</span></span> <span data-ttu-id="d2dc1-105">表示の設定は HTML レポート ビューアーで行い、 *ドリルダウン* アクションと呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-105">Setting visibility works in an HTML report viewer, and is sometimes called a *drilldown* action.</span></span>  
  
 <span data-ttu-id="d2dc1-106">レポート デザイン ビューで、展開と折りたたみの切り替えアイコンを表示するテキスト ボックスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-106">In report design view, you specify the name of the text box where you want to display the expand and collapse toggle icons.</span></span> <span data-ttu-id="d2dc1-107">表示されたレポートには、内容の他にプラス (+) 記号またはマイナス (-) 記号がテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-107">In the rendered report, the text box displays a plus (+) or minus (-) sign in addition to its contents.</span></span> <span data-ttu-id="d2dc1-108">ユーザーが表示切替をクリックすると、レポート表示が更新され、レポートのアイテムの現在の表示設定に基づいて表示/非表示が切り替わります。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-108">When the user clicks the toggle, the report display is refreshed to show or hide the report item, based on the current visibility settings for items in the report.</span></span>  
  
 <span data-ttu-id="d2dc1-109">通常、展開/折りたたみアクションは、最初に要約データのみを表示し、ユーザーがプラス記号をクリックして詳細データを表示できるようにするときに使用します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-109">Typically, the expand and collapse action is used to initially display only summary data and to enable the user to click the plus sign to show detail data.</span></span> <span data-ttu-id="d2dc1-110">たとえば、ドリルダウン レポートのように、グラフの値を表示するテーブルを最初に非表示にしたり、行グループまたは列グループが入れ子にされた子グループを非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-110">For example, you can initially hide a table that displays values for a chart, or hide child groups for a table with nested row or column groups, as in a drilldown report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-expand-and-collapse-action-to-a-group"></a><span data-ttu-id="d2dc1-111">グループに展開/折りたたみアクションを追加するには</span><span class="sxs-lookup"><span data-stu-id="d2dc1-111">To add expand and collapse action to a group</span></span>  
  
1.  <span data-ttu-id="d2dc1-112">レポート デザイン ビューで、テーブルまたはマトリックスをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-112">In report design view, click the table or matrix to select it.</span></span> <span data-ttu-id="d2dc1-113">グループ化ペインに行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-113">The Grouping pane displays the row and column groups.</span></span>  
  
     <span data-ttu-id="d2dc1-114">![グループ化ペイン](../media/groupingpane.png "グループ化ペイン")</span><span class="sxs-lookup"><span data-stu-id="d2dc1-114">![Grouping Pane](../media/groupingpane.png "Grouping Pane")</span></span>  
  
     <span data-ttu-id="d2dc1-115">グループ化ペインが表示されない場合は、 **[表示]** メニューをクリックしてから、 **[グループ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-115">If the Grouping pane does not appear, click the **View** menu and then click **Grouping**.</span></span>  
  
2.  <span data-ttu-id="d2dc1-116">[グループ化] ペインのタイトル バー内を右クリックし、 **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-116">Right-click anywhere in the title bar of the Grouping pane, and then click **Advanced**.</span></span> <span data-ttu-id="d2dc1-117">[グループ化] ペインのモードが切り替わり、行と列の基になる表示構造がデザイン画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-117">The Grouping pane mode toggles to show the underlying display structure for rows and columns on the design surface.</span></span>  
  
     <span data-ttu-id="d2dc1-118">![[詳細設定モード] メニューでのグループ化ペイン](../media/groupingpane-advancedmode.png "[詳細設定モード] メニューでのグループ化ペイン")</span><span class="sxs-lookup"><span data-stu-id="d2dc1-118">![Grouping Pane with Advanced Mode menu](../media/groupingpane-advancedmode.png "Grouping Pane with Advanced Mode menu")</span></span>  
  
3.  <span data-ttu-id="d2dc1-119">適切なグループ ペインで、関連する行または列を非表示にする行グループまたは列グループの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-119">In the appropriate group pane, click the name of the row group or column group for which you want to hide the associated rows or columns.</span></span> <span data-ttu-id="d2dc1-120">グループが選択されると、[プロパティ] ペインに **[Tablix メンバー]** プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-120">The group is selected and the Properties pane shows the **Tablix Member** properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2dc1-121">プロパティ ペインが表示されない場合は、リボンの **[表示]** をクリックしてから **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-121">If you do not see the Properties pane, click **View** on the Ribbon and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="d2dc1-122">で `Hidden` 、次のいずれかのオプションを選択して、レポートを初めて実行するときに、このレポートアイテムの表示を設定します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-122">In `Hidden`, choose one of the following options to set the visibility of this report item the first time you run a report:</span></span>  
  
    -   <span data-ttu-id="d2dc1-123">`False`レポートアイテムを表示する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-123">Select `False` to display the report item.</span></span>  
  
    -   <span data-ttu-id="d2dc1-124">`True`レポートアイテムを非表示にする場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-124">Select `True` to hide the report item.</span></span>  
  
    -   <span data-ttu-id="d2dc1-125">選択すると **\<Expression>** 、[**式**] ダイアログボックスが開き、実行時に評価される式を作成して、表示/非表示を決定します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-125">Select **\<Expression>** to open the **Expression** dialog box to create an expression that is evaluated at run time to determine the visibility.</span></span>  
  
5.  <span data-ttu-id="d2dc1-126">**[切り替えアイテム]** で、ドロップダウン ボックスから、切り替えイメージを追加するテキスト ボックスの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-126">In **ToggleItem**, from the drop-down box, select the name of a text box to which to add the toggle image.</span></span>  
  
     <span data-ttu-id="d2dc1-127">次の図で、色の行グループは、ユーザーが関連する行を展開したり折りたたんだりできるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-127">In the following image, the Color row group is configured enable users to expand and collapse associated rows.</span></span>  
  
     <span data-ttu-id="d2dc1-128">![展開する行グループの構成](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "展開する行グループの構成")</span><span class="sxs-lookup"><span data-stu-id="d2dc1-128">![Configuring a row group to be expanded](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "Configuring a row group to be expanded")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2dc1-129">切り替えイメージが付いたテキスト ボックスを、関連する行または列を非表示にする行グループまたは列グループにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-129">The text box with the toggle image cannot be the row or column group for which you want to hide the associated rows or columns.</span></span> <span data-ttu-id="d2dc1-130">非表示にするアイテムと同じグループまたは先祖グループに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-130">It must either be in the same group as the item that is being hidden or in an ancestor group.</span></span> <span data-ttu-id="d2dc1-131">たとえば、子グループに関連付けられている行の表示を切り替えるには、親グループに関連付けられている行のテキスト ボックスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-131">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span>  
  
6.  <span data-ttu-id="d2dc1-132">切り替えをテストするには、レポートを実行し、切り替えイメージが付いたテキスト ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-132">To test the toggle, run the report and click the text box with the toggle image.</span></span> <span data-ttu-id="d2dc1-133">レポート表示が更新されて、表示/非表示が切り替えられた行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-133">The report display refreshes to show row groups and column groups with their toggled visibility.</span></span>  
  
     <span data-ttu-id="d2dc1-134">![展開可能な行グループを含むレポートの実行](../media/expandcollapse-runreport-rowgroup.png "展開可能な行グループを含むレポートの実行")</span><span class="sxs-lookup"><span data-stu-id="d2dc1-134">![Running report with expandable row group](../media/expandcollapse-runreport-rowgroup.png "Running report with expandable row group")</span></span>  
  
### <a name="to-add-expand-and-collapse-action-to-a-report-item"></a><span data-ttu-id="d2dc1-135">レポート アイテムに展開/折りたたみアクションを追加するには</span><span class="sxs-lookup"><span data-stu-id="d2dc1-135">To add expand and collapse action to a report item</span></span>  
  
1.  <span data-ttu-id="d2dc1-136">レポートデザインビューで、表示または非表示にするレポートアイテムを右クリックし、[プロパティ] をクリックし *\<report item>* **Properties**ます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-136">In report design view, right-click the report item to show or hide, and then click *\<report item>* **Properties**.</span></span> <span data-ttu-id="d2dc1-137">*\<report item>* レポートアイテムの [**プロパティ**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-137">The *\<report item>* **Properties** dialog box for the report item opens.</span></span>  
  
2.  <span data-ttu-id="d2dc1-138">**[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-138">Click **Visibility**.</span></span>  
  
3.  <span data-ttu-id="d2dc1-139">**[レポートの初期実行時]** で、次のいずれかのオプションを選択し、レポートの初期実行時にこのレポート アイテムの表示を設定します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-139">In **When the report is initially run**, choose one of the following options to set the visibility of this report item the first time you run a report:</span></span>  
  
    -   <span data-ttu-id="d2dc1-140">レポート アイテムを表示する場合は、 **[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-140">Select **Show** to display the report item.</span></span>  
  
    -   <span data-ttu-id="d2dc1-141">レポート アイテムを非表示にする場合は、 **[非表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-141">Select **Hide** to hide the report item.</span></span>  
  
    -   <span data-ttu-id="d2dc1-142">実行時に評価される式を使用して表示/非表示を指定するには、 **[式を基に表示/非表示を切り替える]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-142">Select **Show or hide based on an expression** to use an expression evaluated at run time to determine the visibility.</span></span> <span data-ttu-id="d2dc1-143">式を作成するには、**[fx]** をクリックして **[式]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-143">Click (**fx**) to open the **Expression** dialog box to create an expression.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d2dc1-144">表示/非表示を設定する式を指定する場合、レポート アイテムの Hidden プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-144">When you specify an expression for visibility, you are setting the Hidden property of the report item.</span></span> <span data-ttu-id="d2dc1-145">式を評価した値が `Boolean` 値の `True` の場合はアイテムが非表示になり、`False` の場合はアイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-145">The expression evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span>  
  
4.  <span data-ttu-id="d2dc1-146">**[次のレポート アイテムでの表示の切り替えを可能にする]** で、ドロップダウン ボックスから、切り替えイメージを表示するレポート内のテキスト ボックスの名前を入力または選択します (Textbox1 など)。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-146">In **Display can be toggled by this report item**, from the drop-down box, type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span>  
  
     <span data-ttu-id="d2dc1-147">次の図で、テーブルはユーザーが展開したり折りたたんだりできるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-147">In the following image, the table is configured to enable users to expand and collapse it.</span></span> <span data-ttu-id="d2dc1-148">このテーブルの表示は、[製品テーブル] テキスト ボックスで切り替えられます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-148">The display of the table is toggled by the Products Table text box.</span></span>  
  
     <span data-ttu-id="d2dc1-149">![展開するレポート テーブルの構成](../media/expandcollapse-reporttable.png "展開するレポート テーブルの構成")</span><span class="sxs-lookup"><span data-stu-id="d2dc1-149">![Configure a report table to be expanded](../media/expandcollapse-reporttable.png "Configure a report table to be expanded")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2dc1-150">選択するテキスト ボックスは、このレポート アイテムの現在のスコープまたはコンテナー スコープ (レポート本文を含む、レポート本文までのスコープ) に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-150">The text box that you choose must be in the current or containing scope for this report item (up to and including the report body).</span></span> <span data-ttu-id="d2dc1-151">たとえば、グラフの表示を切り替えるには、レポート本文や四角形など、グラフと同じコンテナー スコープにあるテキスト ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-151">For example, to toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span> <span data-ttu-id="d2dc1-152">テキスト ボックスは、同じまたは上位のコンテナー階層に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-152">The text box must be in the same container hierarchy or higher.</span></span>  
  
5.  <span data-ttu-id="d2dc1-153">切り替えをテストするには、レポートを実行し、切り替えイメージが付いたテキスト ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-153">To test the toggle, run the report and click the text box with the toggle image.</span></span> <span data-ttu-id="d2dc1-154">レポート表示が更新されて、表示/非表示が切り替えられたレポート アイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2dc1-154">The report display refreshes to show report items with their toggled visibility.</span></span>  
  
     <span data-ttu-id="d2dc1-155">![展開されたテーブルを含むレポートの実行](../media/expandcollapse-runreport-reporttable.png "展開されたテーブルを含むレポートの実行")</span><span class="sxs-lookup"><span data-stu-id="d2dc1-155">![Running report with an expanding table](../media/expandcollapse-runreport-reporttable.png "Running report with an expanding table")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2dc1-156">参照</span><span class="sxs-lookup"><span data-stu-id="d2dc1-156">See Also</span></span>  
 <span data-ttu-id="d2dc1-157">[ドリルダウンアクション &#40;レポートビルダーと SSRS&#41;](drilldown-action-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d2dc1-157">[Drilldown Action &#40;Report Builder and SSRS&#41;](drilldown-action-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d2dc1-158">アイテムを非表示にする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d2dc1-158">Hide an Item &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/hide-an-item-report-builder-and-ssrs.md)  
  
  
