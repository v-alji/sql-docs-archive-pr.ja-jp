---
title: テーブルまたはマトリックスへの対話的な並べ替えの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10121"
- sql12.rtp.rptdesigner.textboxproperties.intrctvsort.f1
ms.assetid: 05819637-729b-4cf6-82de-91a99f184ec6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c0c453a8ea338ab9a09d7552c064f2eb85add985
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739355"
---
# <a name="add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs"></a><span data-ttu-id="5ed11-102">テーブルまたはマトリックスへの対話的な並べ替えの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5ed11-102">Add Interactive Sort to a Table or Matrix (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5ed11-103">ユーザーがテーブルやマトリックス内で行と列の並べ替え順序を変更できるようにするには、対話的な並べ替えボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-103">Add interactive sort buttons to enable users to change the sort order of rows and columns in tables and matrices.</span></span> <span data-ttu-id="5ed11-104">この機能は、ユーザーとの対話が可能な、HTML などの表示形式でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5ed11-104">This feature is supported only in rendering formats that support user interaction, such as HTML.</span></span>  
  
 <span data-ttu-id="5ed11-105">対話的な並べ替えボタンを作成する場合は、並べ替えの対象、並べ替え基準、および並べ替えの適用範囲を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-105">When you create an interactive sort button, you must specify what to sort, what to sort by, and the scope to which to apply the sort.</span></span> <span data-ttu-id="5ed11-106">たとえば、詳細行を顧客名ごとに並べ替えたり、カテゴリ グループ内のサブカテゴリ グループ値を売上順に並べ替えたり、カテゴリ グループ値とサブカテゴリ グループ値を合計に基づいて並べ替えたりできます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-106">For example, you can sort detail rows by customer last name, subcategory group values within a category group by sales, or category and subcategory group values combined by totals.</span></span>  
  
 <span data-ttu-id="5ed11-107">レポートを表示すると、対話的な並べ替えをサポートする列には、並べ替え順序に応じて方向が変わる矢印のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-107">When you view the report, columns that support interactive sorting have arrow icons that change to indicate the sort order.</span></span> <span data-ttu-id="5ed11-108">対話的な並べ替えボタンを初めてクリックすると、アイテムは昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-108">The first time you click an interactive sort button, items are sorted in ascending order.</span></span> <span data-ttu-id="5ed11-109">2 回目以降は、ボタンをクリックするたびに昇順と降順が切り替わります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-109">Subsequent clicks toggle the sort order between ascending and descending order.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="in-this-article"></a><a name="BackToTop"></a> <span data-ttu-id="5ed11-110">この記事の内容</span><span class="sxs-lookup"><span data-stu-id="5ed11-110">In this Article</span></span>  
 [<span data-ttu-id="5ed11-111">グループのないテーブルの詳細行の並べ替え</span><span class="sxs-lookup"><span data-stu-id="5ed11-111">Sorting Detail Rows for a Table with No Groups</span></span>](#SortingDetailRows)  
  
 [<span data-ttu-id="5ed11-112">テーブルまたはマトリックスの最上位レベル親行グループの並べ替え</span><span class="sxs-lookup"><span data-stu-id="5ed11-112">Sorting a Top Level Parent Row Group for a Table or Matrix</span></span>](#SortingTopLevelParent)  
  
 [<span data-ttu-id="5ed11-113">グループの子グループまたは詳細行の並べ替え</span><span class="sxs-lookup"><span data-stu-id="5ed11-113">Sorting Child Groups or Detail Rows for a Group</span></span>](#SortingChildGroups)  
  
 [<span data-ttu-id="5ed11-114">複雑なグループ式に基づく行の並べ替え</span><span class="sxs-lookup"><span data-stu-id="5ed11-114">Sorting Rows Based on a Complex Group Expression</span></span>](#SortingMultipleRowGroups)  
  
 [<span data-ttu-id="5ed11-115">複数のデータ領域の並べ替え順序の同期</span><span class="sxs-lookup"><span data-stu-id="5ed11-115">Synchronizing Sort Order for Multiple Data Regions</span></span>](#SynchronizingSortOrder)  
  
##  <a name="sorting-detail-rows-for-a-table-with-no-groups"></a><a name="SortingDetailRows"></a> <span data-ttu-id="5ed11-116">グループのないテーブルの詳細行の並べ替え</span><span class="sxs-lookup"><span data-stu-id="5ed11-116">Sorting Detail Rows for a Table with No Groups</span></span>  
 <span data-ttu-id="5ed11-117">ユーザーが列見出しをクリックすることにより、その列に表示されている値に基づいてテーブル内の詳細行を並べ替えられるようにするには、対話的な並べ替えボタンを列見出しに追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-117">Add an interactive sort button to a column header to enable a user to click the column header and sort the details rows in a table by the value displayed in that column.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-the-table-by-value"></a><span data-ttu-id="5ed11-118">テーブルを値で並べ替えるための対話的な並べ替えボタンを列見出しに追加するには</span><span class="sxs-lookup"><span data-stu-id="5ed11-118">To add an interactive sort button to a column header to sort the table by value</span></span>  
  
1.  <span data-ttu-id="5ed11-119">レポート デザイン ビュー内のグループのないテーブルで、対話的な並べ替えボタンを追加する列見出しにあるテキスト ボックスを右クリックして、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-119">In report design view, in a table with no groups, right-click the text box in the column header to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="5ed11-120">**[対話的な並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-120">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="5ed11-121">**[このテキスト ボックスでの対話的な並べ替えを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-121">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="5ed11-122">**[並べ替えの対象の選択]** で、 **[詳細行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-122">In **Choose what to sort**, click **Detail rows**.</span></span>  
  
5.  <span data-ttu-id="5ed11-123">**[並べ替え]** で、並べ替え式を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-123">In **Sort by**, specify a sort expression.</span></span> <span data-ttu-id="5ed11-124">ドロップダウン リストから、並べ替えアクションを定義する列に対応するフィールドを選択します (たとえば、"Title" という列見出しの場合は、" `[Title]`" を選択)。</span><span class="sxs-lookup"><span data-stu-id="5ed11-124">From the drop-down list, select the field that corresponds to the column for which you are defining a sort action (for example, for a column heading named "Title", choose `[Title]`).</span></span> <span data-ttu-id="5ed11-125">並べ替え式の指定は必須です。</span><span class="sxs-lookup"><span data-stu-id="5ed11-125">Specifying a sort expression is required.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="5ed11-126">対話的な並べ替えボタンを追加する列ごとに、手順 1. ～ 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-126">Repeat steps 1-6 for every column to which you want to add an interactive sort button.</span></span>  
  
 <span data-ttu-id="5ed11-127">並べ替えアクションを確認するには、 **[実行]** をクリックしてレポートをプレビューし、対話的な並べ替えボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-127">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="5ed11-128">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="5ed11-128">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-a-top-level-parent-row-group-for-a-table-or-matrix"></a><a name="SortingTopLevelParent"></a> <span data-ttu-id="5ed11-129">テーブルまたはマトリックスの最上位レベル親行グループの並べ替え</span><span class="sxs-lookup"><span data-stu-id="5ed11-129">Sorting a Top-Level Parent Row Group for a Table or Matrix</span></span>  
 <span data-ttu-id="5ed11-130">ユーザーが列見出しをクリックすることにより、その列に表示されている値に基づいてテーブルまたはマトリックス内の親グループ行を並べ替えられるようにするには、対話的な並べ替えボタンを列見出しに追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-130">Add an interactive sort button to a column header to enable a user to click the column header and sort the parent group rows in a table or matrix by the value displayed in that column.</span></span> <span data-ttu-id="5ed11-131">子グループの順序は変更されません。</span><span class="sxs-lookup"><span data-stu-id="5ed11-131">The order of child groups remains unchanged.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-groups"></a><span data-ttu-id="5ed11-132">グループを並べ替えるための対話的な並べ替えボタンを列見出しに追加するには</span><span class="sxs-lookup"><span data-stu-id="5ed11-132">To add an interactive sort button to a column header to sort groups</span></span>  
  
1.  <span data-ttu-id="5ed11-133">レポート デザイン ビュー内のテーブルまたはマトリックスで、対話的な並べ替えボタンを追加するグループの列見出しにあるテキスト ボックスを右クリックして、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-133">In a table or matrix in report design view, right-click the text box in the column header for the group to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="5ed11-134">**[対話的な並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-134">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="5ed11-135">**[このテキスト ボックスでの対話的な並べ替えを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-135">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="5ed11-136">**[並べ替えの対象の選択]** で、 **[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-136">In **Choose what to sort**, click **Groups**.</span></span>  
  
5.  <span data-ttu-id="5ed11-137">ドロップダウン リストから、並べ替えるグループの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-137">From the drop-down list, select the name of the group that you are sorting.</span></span> <span data-ttu-id="5ed11-138">単一のグループ式に基づくグループの場合は、 **[並べ替え]** にグループ式が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-138">For groups based on simple group expressions, the **Sort by** value is populated with group expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5ed11-139">複雑なグループ式の場合は、 **[並べ替え]** をグループ式と同じ値に手動で設定してください。</span><span class="sxs-lookup"><span data-stu-id="5ed11-139">For complex group expressions, manually set the **Sort by** expression to the same value as the group expression.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="5ed11-140">並べ替えアクションを確認するには、 **[実行]** をクリックしてレポートをプレビューし、対話的な並べ替えボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-140">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="5ed11-141">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="5ed11-141">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-child-groups-or-detail-rows-for-a-group"></a><a name="SortingChildGroups"></a> <span data-ttu-id="5ed11-142">グループの子グループまたは詳細行の並べ替え</span><span class="sxs-lookup"><span data-stu-id="5ed11-142">Sorting Child Groups or Detail Rows for a Group</span></span>  
 <span data-ttu-id="5ed11-143">ユーザーが親グループ内の子グループの値を並べ替えたり、最も内側にある子グループの詳細行を並べ替えたりできるようにするには、対話的な並べ替えボタンをグループ ヘッダー行に追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-143">Add an interactive sort button to a group header row to enable the user to sort the values of a child group from a parent group or to sort the detail rows for the innermost child group.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-text-box-in-a-group-row-header-to-sort-child-groups-or-detail-rows"></a><span data-ttu-id="5ed11-144">子グループまたは詳細行を並べ替えるための対話的な並べ替えボタンをグループ行ヘッダーのテキスト ボックスに追加するには</span><span class="sxs-lookup"><span data-stu-id="5ed11-144">To add an interactive sort button to a text box in a group row header to sort child groups or detail rows</span></span>  
  
1.  <span data-ttu-id="5ed11-145">レポート デザイン ビューで、対話的な並べ替えボタンを追加するグループ ヘッダー行にあるテキスト ボックスを右クリックして、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-145">In report design view, right-click the text box in the group header row to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="5ed11-146">**[対話的な並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-146">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="5ed11-147">**[このテキスト ボックスでの対話的な並べ替えを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-147">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="5ed11-148">**[並べ替えの対象の選択]** で、以下のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-148">In **Choose what to sort**, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="5ed11-149">**[詳細]** 詳細行を並べ替えるには、 **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-149">**Details** Click **Details** to sort the detail rows.</span></span> <span data-ttu-id="5ed11-150">ドロップダウン リストから、並べ替えの基準にするフィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-150">From the drop-down list, select the field to sort by.</span></span> <span data-ttu-id="5ed11-151">このオプションを選択した場合は、並べ替えの基準にする値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-151">For this option, you must specify the value to sort by.</span></span>  
  
    -   <span data-ttu-id="5ed11-152">**[グループ]** 子グループの値を並べ替えるには、 **[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-152">**Groups** Click **Groups** to sort the child group values.</span></span> <span data-ttu-id="5ed11-153">このオプションを選択した場合、 **[並べ替え]** には、グループ式が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-153">For this option, the **Sort by** expression is automatically filled in from the group expression.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="5ed11-154">並べ替えアクションを確認するには、 **[実行]** をクリックしてレポートをプレビューし、対話的な並べ替えボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-154">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="5ed11-155">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="5ed11-155">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-rows-based-on-a-complex-group-expression"></a><a name="SortingMultipleRowGroups"></a> <span data-ttu-id="5ed11-156">複雑なグループ式に基づく行の並べ替え</span><span class="sxs-lookup"><span data-stu-id="5ed11-156">Sorting Rows Based on a Complex Group Expression</span></span>  
 <span data-ttu-id="5ed11-157">ユーザーが列見出しをクリックすることにより、親グループと子グループの組み合わせを並べ替えられるようにするには、対話的な並べ替えボタンを列見出しに追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-157">Add an interactive sort button to a column header to enable a user to click the column header and sort the combined parent and child groups.</span></span> <span data-ttu-id="5ed11-158">この機能を実現するには、両方のグループを複合したものにグループ式を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-158">To achieve this affect, you must change the group expression to be a composite of both groups.</span></span> <span data-ttu-id="5ed11-159">たとえば、ある店舗の在庫合計を表示するマトリックスがあり、色とサイズの両方でアイテムがグループ化されているとします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-159">For example, suppose a matrix displays inventory totals for a store for items grouped by both color and size.</span></span> <span data-ttu-id="5ed11-160">この場合に、色とサイズの組み合わせに基づいて行を並べ替えるには、色とサイズのグループを別々に定義するのではなく、色とサイズの組み合わせに基づいたグループを 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-160">To sort the rows based on the combination of color and size, instead of having a separate group for color and a separate group for size, you can define a group based on the combination of color and size.</span></span> <span data-ttu-id="5ed11-161">グループ式の定義の詳細については、「[グループ式の例 &#40;レポート ビルダーおよび SSRS&#41;](expression-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed11-161">For more information about defining group expressions, see [Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5ed11-162">次の手順では、Tablix データ領域部分を指定する用語が使用されています。</span><span class="sxs-lookup"><span data-stu-id="5ed11-162">In the following procedure, terms specify tablix data region areas.</span></span> <span data-ttu-id="5ed11-163">詳細については、「[Tablix データ領域部分 &#40;レポート ビルダーおよび SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed11-163">For more information, see [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5ed11-164">通常、複数のグループに基づいて行を並べ替える場合は、列グループにかかわらず、並べ替えられた行の合計を表示することが必要となります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-164">Typically, when you sort rows based on multiple groups, you want to see totals for the sorted rows, regardless of column groups.</span></span> <span data-ttu-id="5ed11-165">この手順では、列グループが使用されません。</span><span class="sxs-lookup"><span data-stu-id="5ed11-165">In this procedure, no column groups are used.</span></span> <span data-ttu-id="5ed11-166">まず、マトリックスを追加して、既定の列グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-166">You start by adding a matrix and removing the default column group.</span></span> <span data-ttu-id="5ed11-167">または、テーブルを追加して、詳細グループを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-167">Alternatively, you could start by adding a table and removing the details group.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-multiple-groups"></a><span data-ttu-id="5ed11-168">複数のグループを並べ替えるための対話的な並べ替えボタンを列見出しに追加するには</span><span class="sxs-lookup"><span data-stu-id="5ed11-168">To add an interactive sort button to a column header to sort multiple groups</span></span>  
  
1.  <span data-ttu-id="5ed11-169">レポート デザイン ビューで、マトリックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-169">In report design view, add a matrix.</span></span>  
  
2.  <span data-ttu-id="5ed11-170">数値フィールドをデータ セルにドラッグして、データセットとマトリックスを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-170">Drag a numeric field to the data cell to link the dataset to the matrix.</span></span>  
  
     <span data-ttu-id="5ed11-171">次に、複数のフィールドを指定するグループ式、およびグループ値の表示に使用するグループ ヘッダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-171">Next, you will create a group with a group expression that specifies multiple fields, and a group header to use to display the group values.</span></span>  
  
3.  <span data-ttu-id="5ed11-172">マトリックスがデザイン画面で選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-172">Verify that the matrix is selected on the design surface.</span></span> <span data-ttu-id="5ed11-173">グループ化ペインに、既定の行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-173">The Grouping pane displays a default row and column group.</span></span>  
  
4.  <span data-ttu-id="5ed11-174">行グループ ペインで、既定の行グループを右クリックし、 **[グループの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-174">In the Row Groups pane, right-click the default row group, and then click **Edit Group**.</span></span> <span data-ttu-id="5ed11-175">**[グループのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-175">The **Group Properties** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="5ed11-176">**[名前]** で、グループ化する複数のグループを指定する名前で、既定の名前を置換します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-176">In **Name**, replace the default name with a name that specifies the multiple groups that you want to group by.</span></span>  
  
6.  <span data-ttu-id="5ed11-177">**[グループ式]** の **[グループ化の条件]** で、式 ( **[fx]** ) ボタンをクリックして **[式]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-177">In **Group expressions**, in **Group on**, click the Expression (**fx**) button to open the **Expression** dialog box.</span></span>  
  
7.  <span data-ttu-id="5ed11-178">グループ化するすべてのフィールドを指定する式を入力します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-178">Type the expression that specifies all fields that you want to group by.</span></span> <span data-ttu-id="5ed11-179">たとえば、グループ式 `=Fields!Color.Value & Fields!Size.Value`では、Color というフィールドと Size というフィールドが組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-179">For example, the following group expression combines a field named Color and a field named Size: `=Fields!Color.Value & Fields!Size.Value`.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="5ed11-180">グループが定義されました。</span><span class="sxs-lookup"><span data-stu-id="5ed11-180">You have now defined the group.</span></span> <span data-ttu-id="5ed11-181">次に、表示するフィールドをマトリックスの Tablix 本体領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-181">Next, drag the fields to display to the tablix body area of the matrix.</span></span> <span data-ttu-id="5ed11-182">手順 7. でグループ化するように選択したフィールドを、Tablix 本体領域のそれぞれの列に追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-182">Add the fields that you chose to group by in step 7 to the tablix body area, each in its own column.</span></span>  
  
     <span data-ttu-id="5ed11-183">このシナリオの場合、Tablix 行グループ領域の最初の列は不要です。</span><span class="sxs-lookup"><span data-stu-id="5ed11-183">For this scenario, the first column in the tablix row groups area is not needed.</span></span> <span data-ttu-id="5ed11-184">列を削除するには、列見出しを右クリックして、 **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-184">To delete the column, right-click the column header, and then click **Delete Columns**.</span></span> <span data-ttu-id="5ed11-185">新しいダイアログ ボックスが開き、列に関連付けられているグループを削除するかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-185">A dialog box asks whether to delete the associated groups.</span></span> <span data-ttu-id="5ed11-186">**[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-186">Click **No**.</span></span> <span data-ttu-id="5ed11-187">行グループ領域が削除され、Tablix 本体領域のみが残ります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-187">The row group area is deleted and only the tablix body area remains.</span></span>  
  
     <span data-ttu-id="5ed11-188">次に、既定の列のグループを削除します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-188">Next, you will remove the default column group.</span></span>  
  
9. <span data-ttu-id="5ed11-189">列グループ ペインで、既定の列グループを右クリックし、 **[グループの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-189">In the Column Groups pane, right-click the default column group, and then click **Delete Group**.</span></span> <span data-ttu-id="5ed11-190">新しいダイアログ ボックスが開き、グループとそれに関連した行および列を削除するか、グループのみを削除するかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-190">A dialog box asks whether to delete the group and related rows and columns or the group only.</span></span> <span data-ttu-id="5ed11-191">**[グループのみを削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-191">Click **Delete group only**.</span></span> <span data-ttu-id="5ed11-192">列グループが削除され、列グループ領域が削除されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-192">The column group is deleted, and the column group area is deleted.</span></span> <span data-ttu-id="5ed11-193">Tablix 本体領域のみが残ります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-193">Only the tablix body area remains.</span></span>  
  
     <span data-ttu-id="5ed11-194">次に、マトリックス全体にまたがるテキスト ボックスに対話的な並べ替えボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-194">Next, you will add an interactive sort button to the text box that spans the matrix.</span></span>  
  
10. <span data-ttu-id="5ed11-195">最初の行のテキスト ボックス内をクリックして、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-195">Click in the text box in the first row and then click **Text Box Properties**.</span></span>  
  
11. <span data-ttu-id="5ed11-196">**[対話的な並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-196">Click **Interactive Sorting**.</span></span>  
  
12. <span data-ttu-id="5ed11-197">**[このテキスト ボックスでの対話的な並べ替えを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-197">Select **Enable interactive sorting on this text box**.</span></span>  
  
13. <span data-ttu-id="5ed11-198">**[並べ替えの対象の選択]** で、 **[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-198">In **Choose what to sort**, click **Groups**.</span></span>  
  
14. <span data-ttu-id="5ed11-199">ドロップダウン リストから、手順 5. で作成したグループの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-199">From the drop-down list, select the name of the group you created in step 5.</span></span> <span data-ttu-id="5ed11-200">グループ式が **[並べ替え]** ボックスに自動的にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-200">The group expression is automatically copied to the **Sort by** text box.</span></span>  
  
15. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="5ed11-201">並べ替えボタンがテキスト ボックスに追加されました。</span><span class="sxs-lookup"><span data-stu-id="5ed11-201">You have added the sort button to the text box.</span></span>  
  
16. <span data-ttu-id="5ed11-202">(省略可) グループ値を表示する列では、重複値を非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-202">(Optional) You can suppress duplicate values in the columns that display group values.</span></span> <span data-ttu-id="5ed11-203">レポート デザイン画面で、繰り返し値を非表示にするテキスト ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-203">On the report design surface, click the text box that displays the value for which you want to hide repeating values.</span></span> <span data-ttu-id="5ed11-204">プロパティ ペインで、 **[HideDuplicates]** までスクロールして、このマトリックスに関連付けられたデータセットの名前をドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-204">In the Properties pane, scroll to **HideDuplicates**, and from the drop-down list, select the name of the dataset that is linked to this matrix.</span></span>  
  
 <span data-ttu-id="5ed11-205">並べ替えアクションを確認するには、 **[実行]** をクリックしてレポートをプレビューし、対話的な並べ替えボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-205">To verify the sort action, click **Run** to preview the report, and then click the interactive sort button.</span></span> <span data-ttu-id="5ed11-206">グループ式の値の組み合わせによってマトリックスが並べ替えられます。ただし、個々の値はそれぞれの列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-206">The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.</span></span>  
  
 <span data-ttu-id="5ed11-207">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="5ed11-207">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="synchronizing-sort-order-for-multiple-data-regions"></a><a name="SynchronizingSortOrder"></a> <span data-ttu-id="5ed11-208">複数のデータ領域の並べ替え順序の同期</span><span class="sxs-lookup"><span data-stu-id="5ed11-208">Synchronizing Sort Order for Multiple Data Regions</span></span>  
 <span data-ttu-id="5ed11-209">ユーザーが 1 つの並べ替えボタンをクリックすることによって、複数のデータ領域を並べ替えられるようにする、対話的な並べ替えボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-209">Add an interactive sort button that enables a user to click one sort button and sort multiple data regions.</span></span> <span data-ttu-id="5ed11-210">対話的な並べ替えボタンを作成する場合は、複数のデータ領域の並べ替えを同じレポート データセットに基づいて同期するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-210">When you create an interactive sort button, you can specify whether to synchronize the sort for multiple data regions based on the same report dataset.</span></span> <span data-ttu-id="5ed11-211">たとえば、マトリックスおよびデータをグラフィカルに表示するグラフが含まれたレポートがあるとします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-211">For example, a report might include a matrix and a chart that graphically displays the data.</span></span> <span data-ttu-id="5ed11-212">ユーザーがこのマトリックス内の行の並べ替え順序を変更すると、それと同じ並べ替え順序がグラフに自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-212">When a user changes the sort order of the rows in the matrix, the chart automatically displays the same sort order.</span></span>  
  
 <span data-ttu-id="5ed11-213">並べ替え順序を同期するには、並べ替えるデータ領域またはグループに同一の並べ替え式を使用し、並べ替えの範囲が両方のデータ領域に共通の先祖になるように定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-213">To synchronize the sort order, you must use identical sort expressions for the data regions or groups to sort, and define the scope for the sort to be a mutual ancestor of both data regions.</span></span> <span data-ttu-id="5ed11-214">共通の先祖は、両方のデータ領域が関連付けられているデータセットになる場合も、両方のデータ領域を内部に表示するデータ領域になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-214">The mutual ancestor can be either the dataset to which both data regions are linked or a containing data region within which both data regions appear.</span></span> <span data-ttu-id="5ed11-215">たとえば、同じデータセットからのデータを表示し、同じ一覧に含まれているマトリックスとグラフが両方ともレポートに含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-215">For example, assume a report has both a matrix and a chart that display data from the same dataset and that are contained in a list.</span></span> <span data-ttu-id="5ed11-216">並べ替えアクションを同期するには、マトリックス内の列の 1 つで対話的な並べ替えを指定し、並べ替えの範囲を一覧に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed11-216">To synchronize the sort action, you must specify the interactive sort on a column in the matrix and set the scope to the list.</span></span> <span data-ttu-id="5ed11-217">ユーザーがこのマトリックスを並べ替えると、グラフも並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-217">When the user sorts the matrix, the chart is also sorted.</span></span>  
  
#### <a name="to-synchronize-sort-order-with-a-chart-for-an-interactive-sort-button-on-a-matrix-data-region"></a><span data-ttu-id="5ed11-218">マトリックス データ領域上の対話的な並べ替えボタンによる並べ替え順序をグラフと同期するには</span><span class="sxs-lookup"><span data-stu-id="5ed11-218">To synchronize sort order with a chart for an interactive sort button on a matrix data region</span></span>  
  
1.  <span data-ttu-id="5ed11-219">レポート デザイン ビューで、レポートにマトリックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-219">In report design view, add a matrix to the report.</span></span>  
  
2.  <span data-ttu-id="5ed11-220">数量や売上を表すフィールドなど、数値形式のデータセット フィールドをマトリックスのデータ セルに追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-220">Add a numeric dataset field to the matrix data cell, for example, a field representing quantity or sales.</span></span>  
  
3.  <span data-ttu-id="5ed11-221">行グループを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-221">Define a row group.</span></span> <span data-ttu-id="5ed11-222">既定で、グループの並べ替え順序は、グループ式と同じ式に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-222">By default, the sort order for the group is set to the same expression as the group expression.</span></span>  
  
4.  <span data-ttu-id="5ed11-223">円グラフなどのグラフをレポートに追加します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-223">Add a chart to the report, for example, a pie chart.</span></span>  
  
5.  <span data-ttu-id="5ed11-224">手順 2. で選択したフィールドを **グラフ データ** ペインの **[値]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-224">Drag the field you chose in step 2 to the **Value** area of the **Chart Data** pane.</span></span>  
  
6.  <span data-ttu-id="5ed11-225">グループ化するように選択したフィールドを **[カテゴリ グループ]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-225">Drag the field you chose to group by to the **Category Groups** area.</span></span>  
  
     <span data-ttu-id="5ed11-226">マトリックス行グループとグラフ カテゴリ グループのグループ式は同一でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="5ed11-226">The group expression for the matrix row group and the chart category group must be identical.</span></span>  
  
7.  <span data-ttu-id="5ed11-227">カテゴリ グループを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-227">Right-click the category group, and then click **Category Group Properties**.</span></span>  
  
8.  <span data-ttu-id="5ed11-228">**[並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-228">Click **Sorting**.</span></span>  
  
9. <span data-ttu-id="5ed11-229">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-229">Click **Add**.</span></span> <span data-ttu-id="5ed11-230">新しい並べ替え行が、並べ替えオプションのグリッドに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-230">A new sort row is added to the sorting options grid.</span></span>  
  
10. <span data-ttu-id="5ed11-231">[並べ替え] ボックスの一覧から、手順 6. でグループ化するように選択したフィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-231">In Sort by, from the drop-down list, choose the same field that you chose in step 6 to group by.</span></span>  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
12. <span data-ttu-id="5ed11-232">マトリックスで、対話的な並べ替えボタンを追加する列見出しにあるテキスト ボックスを右クリックして、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-232">In the matrix, right-click the text box in the column header to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
13. <span data-ttu-id="5ed11-233">**[対話的な並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-233">Click **Interactive Sorting**.</span></span>  
  
14. <span data-ttu-id="5ed11-234">**[このテキスト ボックスでの対話的な並べ替えを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-234">Select **Enable interactive sorting on this text box**.</span></span>  
  
15. <span data-ttu-id="5ed11-235">**[並べ替えの対象の選択]** で、 **[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-235">In **Choose what to sort**, click **Groups**.</span></span>  
  
16. <span data-ttu-id="5ed11-236">**[グループ]** ボックスの一覧から、並べ替えるグループの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-236">From the drop-down list under **Groups**, select the name of the group that you are sorting.</span></span> <span data-ttu-id="5ed11-237">このグループのグループ式が **[並べ替え]** の値に自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-237">The group expression for this group is automatically set for the **Sort by** value.</span></span>  
  
17. <span data-ttu-id="5ed11-238">**[この並べ替えを次の内部にある他のグループやデータ領域にも適用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-238">Select **Also apply this sort to other groups and data regions within**.</span></span> <span data-ttu-id="5ed11-239">テキスト ボックスに、"SalesData" などのデータセットの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="5ed11-239">In the text box, type the name of the dataset, for example, "SalesData".</span></span>  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="5ed11-240">並べ替えアクションを確認するには、 **[実行]** をクリックしてレポートをプレビューし、対話的な並べ替えボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed11-240">To verify the sort action, click **Run** to preview the report, and then click the interactive sort button.</span></span> <span data-ttu-id="5ed11-241">グループ式の値の組み合わせによってマトリックスが並べ替えられます。ただし、個々の値はそれぞれの列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ed11-241">The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.</span></span>  
  
 <span data-ttu-id="5ed11-242">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="5ed11-242">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed11-243">参照</span><span class="sxs-lookup"><span data-stu-id="5ed11-243">See Also</span></span>  
 <span data-ttu-id="5ed11-244">[データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5ed11-244">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5ed11-245">[対話的な並べ替え &#40;レポート ビルダーおよび SSRS&#41;](interactive-sort-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5ed11-245">[Interactive Sort &#40;Report Builder and SSRS&#41;](interactive-sort-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5ed11-246">[データ領域内のデータの並べ替え (レポート ビルダーおよび SSRS)](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5ed11-246">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5ed11-247">Tablix データ領域の柔軟性について &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5ed11-247">Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)  
  
  
