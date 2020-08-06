---
title: レポートページでの Tablix データ領域の表示の制御 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f81c48cc-f038-4f57-988d-e9a3cbb46424
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3a3f01dc722d94f72b8bf348415e7dd7fa85132
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634901"
---
# <a name="controlling-the-tablix-data-region-display-on-a-report-page-report-builder-and-ssrs"></a><span data-ttu-id="7d883-102">レポート ページでの Tablix データ領域の表示の制御 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7d883-102">Controlling the Tablix Data Region Display on a Report Page (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7d883-103">このトピックでは、レポートに表示されたときの Tablix データ領域の表示方法を変更するために使用する、Tablix データ領域のプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7d883-103">This topic describes properties for a tablix data region that you can modify to change the way a tablix data region appears when you view it in a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="controlling-the-appearance-of-data"></a><span data-ttu-id="7d883-104">データの外観の制御</span><span class="sxs-lookup"><span data-stu-id="7d883-104">Controlling the Appearance of Data</span></span>  
 <span data-ttu-id="7d883-105">次の機能を使用して、Tablix データ領域の外観を制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-105">The following features help control the appearance of a tablix data region:</span></span>  
  
-   <span data-ttu-id="7d883-106">**データの書式設定:**</span><span class="sxs-lookup"><span data-stu-id="7d883-106">**Formatting data.**</span></span> <span data-ttu-id="7d883-107">テーブル、マトリックス、または一覧のデータを書式設定するには、セル内のテキスト ボックスの書式設定のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="7d883-107">To format data in a table, matrix, or list, set the format properties of the text box in the cell.</span></span> <span data-ttu-id="7d883-108">複数のセルのプロパティを同時に設定できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-108">You can set properties for multiple cells at the same time.</span></span> <span data-ttu-id="7d883-109">グラフ内のデータを書式設定するには、系列の書式設定のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="7d883-109">To format data in a chart, set formatting properties on the series.</span></span> <span data-ttu-id="7d883-110">詳細については、「[レポート アイテムの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md)」と「[グラフの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-110">For more information, see [Formatting Report Items &#40;Report Builder and SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md) and [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7d883-111">**式を作成する。**</span><span class="sxs-lookup"><span data-stu-id="7d883-111">**Writing expressions**.</span></span> <span data-ttu-id="7d883-112">詳細については、「[レポートでの式の使用 &#40;レポート ビルダーおよび SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)」および「[式の例 &#40;レポート ビルダーおよび SSRS&#41;](expression-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-112">For more information, see [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md), and [Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7d883-113">**並べ替え順序を制御する。**</span><span class="sxs-lookup"><span data-stu-id="7d883-113">**Controlling sort order**.</span></span> <span data-ttu-id="7d883-114">並べ替え順序を制御するには、データ領域の並べ替え式を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d883-114">To control the sort order, you must define sort expressions on the data region.</span></span> <span data-ttu-id="7d883-115">グループに関連付けられている行と列の並べ替え順序を制御するには、グループ (詳細グループを含む) の並べ替え式を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d883-115">To control sort order for rows and columns that are associated with a group, you must define sort expressions on the group, including the details groups.</span></span> <span data-ttu-id="7d883-116">ユーザーが Tablix データ領域またはそのグループを並べ替えることができるように対話的な並べ替えボタンを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="7d883-116">You can also add interactive sort buttons to enable the user to sort a tablix data region or its groups.</span></span> <span data-ttu-id="7d883-117">詳細については、「[データ領域内のデータの並べ替え &#40;レポート ビルダーおよび SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-117">For more information, see [Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7d883-118">**データが存在しない場合にメッセージを表示する。**</span><span class="sxs-lookup"><span data-stu-id="7d883-118">**Displaying a message when there is no data**.</span></span> <span data-ttu-id="7d883-119">実行時にレポート データセットのデータが存在しない場合、データ領域に代わりに表示する独自のメッセージを記述できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-119">When no data exists for a report dataset at run time, you can write your own message to display in place of the data region.</span></span> <span data-ttu-id="7d883-120">詳細については、「[データ領域にデータがないことを示すメッセージの設定 &#40;レポート ビルダーおよび SSRS&#41;](../report-data/set-a-no-data-message-for-a-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-120">For more information, see [Set a No Data Message for a Data Region &#40;Report Builder and SSRS&#41;](../report-data/set-a-no-data-message-for-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7d883-121">**条件付きでデータを非表示にする。**</span><span class="sxs-lookup"><span data-stu-id="7d883-121">**Conditionally hiding data**.</span></span> <span data-ttu-id="7d883-122">データ領域またはデータ領域の一部を表示または非表示にするかどうかを条件付きで制御するには、Hidden プロパティを `True` または式に設定します。</span><span class="sxs-lookup"><span data-stu-id="7d883-122">To conditionally control whether to show or hide a data region or parts of a data region, you can set the Hidden property to `True` or to an expression.</span></span> <span data-ttu-id="7d883-123">式には、レポート パラメーターへの参照を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7d883-123">Expressions can include references to report parameters.</span></span> <span data-ttu-id="7d883-124">詳細データを表示するかどうかをユーザーが決定できるように、切り替えアイテムを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7d883-124">You can also specify a toggle item, so that user can decide to display detail data.</span></span> <span data-ttu-id="7d883-125">詳細については、「[ドリルダウン アクション &#40;レポート ビルダーおよび SSRS&#41;](drilldown-action-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-125">For more information, see [Drilldown Action &#40;Report Builder and SSRS&#41;](drilldown-action-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7d883-126">**セルを結合しています。**</span><span class="sxs-lookup"><span data-stu-id="7d883-126">**Merging cells.**</span></span> <span data-ttu-id="7d883-127">テーブル内の複数の連続するセルを 1 つのセルに結合できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-127">Multiple contiguous cells within a table can be combined into a single cell.</span></span> <span data-ttu-id="7d883-128">これは、列の結合またはセルの結合と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="7d883-128">This is known as a column span or a cell merge.</span></span> <span data-ttu-id="7d883-129">セルは水平方向または垂直方向にのみ結合できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-129">Cells can only be combined horizontally or vertically.</span></span> <span data-ttu-id="7d883-130">セルを結合する場合、最初のセルのデータのみが保持されます。</span><span class="sxs-lookup"><span data-stu-id="7d883-130">When you merge cells, only the data in the first cell is preserved.</span></span> <span data-ttu-id="7d883-131">その他のセル内のデータは削除されます。</span><span class="sxs-lookup"><span data-stu-id="7d883-131">Data in other cells is removed.</span></span> <span data-ttu-id="7d883-132">結合されたセルは、元の列に分割できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-132">Merged cells can be split into their original columns.</span></span> <span data-ttu-id="7d883-133">詳細については、「[データ領域内のセルの結合 &#40;レポート ビルダーおよび SSRS&#41;](merge-cells-in-a-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-133">For more information, see [Merge Cells in a Data Region &#40;Report Builder and SSRS&#41;](merge-cells-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
## <a name="controlling-tablix-data-region-position-and-expansion-on-a-page"></a><span data-ttu-id="7d883-134">ページ上の Tablix データ領域の位置および拡張の制御</span><span class="sxs-lookup"><span data-stu-id="7d883-134">Controlling Tablix Data Region Position and Expansion on a Page</span></span>  
 <span data-ttu-id="7d883-135">次の機能を使用して、表示されたレポートにおける Tablix データ領域の表示方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-135">The following features help control the way a tablix data region displays in a rendered report:</span></span>  
  
-   <span data-ttu-id="7d883-136">**その他のレポート アイテムに対する Tablix データ領域の位置を制御する。**</span><span class="sxs-lookup"><span data-stu-id="7d883-136">**Controlling the position of a tablix data region in relation to other report items**.</span></span> <span data-ttu-id="7d883-137">Tablix データ領域は、レポート デザイン画面上のその他のレポート アイテムの上、横、または下に配置できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-137">A tablix data region can be positioned above, next to, or below other report items on the report design surface.</span></span> <span data-ttu-id="7d883-138">実行時に、Tablix データ領域は、リンクされたデータセット用に取得されたデータに応じて [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] によって拡張され、必要に応じてピア レポート アイテムが移動します。</span><span class="sxs-lookup"><span data-stu-id="7d883-138">At run time, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] expands the tablix data region as needed for the data retrieved for the linked dataset, moving peer report items aside as needed.</span></span> <span data-ttu-id="7d883-139">Tablix を別のレポート アイテムの横に固定するには、レポート アイテムをピアとして設定して、それらの相対的位置を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d883-139">To anchor a tablix next to another report item, you must make the report items peers and adjust their relative positions.</span></span> <span data-ttu-id="7d883-140">詳しくは、「[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d883-140">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7d883-141">**拡張方向を変更する。**</span><span class="sxs-lookup"><span data-stu-id="7d883-141">**Changing the Expansion Direction**.</span></span> <span data-ttu-id="7d883-142">Tablix データ領域がページの左から右 (LTR) に拡張するのか、右から左 (RTL) に拡張するのかを制御するには、[プロパティ] ウィンドウからアクセスできる Direction プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="7d883-142">To control whether a tablix data region expands across the page from left-to-right (LTR) or from right-to-left (RTL), use the Direction property, which can be accessed through the Properties window.</span></span> <span data-ttu-id="7d883-143">詳細については、「[データ領域の表示 &#40;レポート ビルダーおよび SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-143">For more information, see [Rendering Data Regions &#40;Report Builder and SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md).</span></span>  
  
## <a name="controlling-how-a-tablix-data-region-renders-on-a-page"></a><span data-ttu-id="7d883-144">ページ上の Tablix データ領域の表示方法の制御</span><span class="sxs-lookup"><span data-stu-id="7d883-144">Controlling How a Tablix Data Region Renders on a Page</span></span>  
 <span data-ttu-id="7d883-145">次の方法で、レポートにおける Tablix データ領域の表示方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-145">The following list describes ways that you can help control how a tablix data region appears in a report:</span></span>  
  
-   <span data-ttu-id="7d883-146">**ページングを制御する。**</span><span class="sxs-lookup"><span data-stu-id="7d883-146">**Controlling paging**.</span></span> <span data-ttu-id="7d883-147">各レポート ページに表示されるデータの量を制御するには、データ領域で改ページを設定します。</span><span class="sxs-lookup"><span data-stu-id="7d883-147">To control the amount of data that displays on each report page, you can set page breaks on data regions.</span></span> <span data-ttu-id="7d883-148">改ページは、グループに対しても設定できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-148">You can also set page breaks on groups.</span></span> <span data-ttu-id="7d883-149">改ページを設定すると、各ページ上で処理する必要のあるデータの量が少なくなり、オンデマンド表示パフォーマンスに影響を与える場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d883-149">Page breaks can affect the on-demand rendering performance by reducing the amount of data that needs to be processed on each page.</span></span> <span data-ttu-id="7d883-150">詳細については、「[Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)」および「[改ページの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-150">For more information, see [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) and [Add a Page Break &#40;Report Builder and SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7d883-151">**行ヘッダーの右側または左側にデータを表示する。**</span><span class="sxs-lookup"><span data-stu-id="7d883-151">**Displaying data on either side of row headers**.</span></span> <span data-ttu-id="7d883-152">行ヘッダーは Tablix データ領域の横以外にも表示できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-152">You are not limited to displaying row headers on the side of a tablix data region.</span></span> <span data-ttu-id="7d883-153">行ヘッダーを列の間に移動して、データ列を行ヘッダーの前に表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="7d883-153">You can move the row headers between columns, so that columns of data appear before the row headers.</span></span> <span data-ttu-id="7d883-154">そのためには、マトリックスの GroupsBeforeRowHeaders プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="7d883-154">To do this, modify the GroupsBeforeRowHeaders property for the matrix.</span></span> <span data-ttu-id="7d883-155">このプロパティは、[プロパティ] ウィンドウからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7d883-155">You can access this property through the Properties window.</span></span> <span data-ttu-id="7d883-156">このプロパティの値には、整数値を使用します。たとえば、この値に 2 を指定すると、行ヘッダーを含む列の前にデータ領域列データの 2 つのグループ インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d883-156">The value for this property is an integer; for example, a value of 2 will display two groups instances of data region column data before displaying the column containing the row headers.</span></span>  
  
## <a name="controlling-how-tablix-row-and-column-groups-render"></a><span data-ttu-id="7d883-157">Tablix の行グループおよび列グループの表示方法の制御</span><span class="sxs-lookup"><span data-stu-id="7d883-157">Controlling How Tablix Row and Column Groups Render</span></span>  
 <span data-ttu-id="7d883-158">Tablix データ領域のグループの表示を制御する方法は、グループ構造によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7d883-158">To control how a tablix data region groups render depends on the group structure.</span></span> <span data-ttu-id="7d883-159">Tablix データ領域には、次の図に示すように 4 つの領域を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7d883-159">A tablix data region can have four areas, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="7d883-160">![Tablix データ領域領域](../media/rs-tablixareas.gif "Tablix データ領域部分")</span><span class="sxs-lookup"><span data-stu-id="7d883-160">![Tablix data region areas](../media/rs-tablixareas.gif "Tablix data region areas")</span></span>  
  
 <span data-ttu-id="7d883-161">行グループ領域と列グループ領域にはグループ ヘッダーがあります。</span><span class="sxs-lookup"><span data-stu-id="7d883-161">The row group area and column group area contain group headers.</span></span> <span data-ttu-id="7d883-162">Tablix データ領域にグループ ヘッダーがある場合、 **[Tablix のプロパティ]** ダイアログ ボックスの **[全般]** ページのプロパティを設定することにより、行と列の繰り返し方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="7d883-162">When a tablix data region has group headers, you control how rows and columns repeat by setting properties on the **General** page of the **Tablix Properties** dialog Box.</span></span>  
  
 <span data-ttu-id="7d883-163">Tablix データ領域に Tablix 本体領域しかない場合、グループ ヘッダーはありません。</span><span class="sxs-lookup"><span data-stu-id="7d883-163">If a tablix data region has only a tablix body area, there are no group headers.</span></span> <span data-ttu-id="7d883-164">静的および動的な Tablix メンバーだけになります。</span><span class="sxs-lookup"><span data-stu-id="7d883-164">There are only static and dynamic tablix members.</span></span> <span data-ttu-id="7d883-165">静的メンバーは、Tablix の行グループまたは列グループに対して 1 回表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d883-165">A static member displays once in relation to a tablix row or column group.</span></span> <span data-ttu-id="7d883-166">動的メンバーは、一意のグループ値ごとに 1 回表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d883-166">A dynamic member repeats once for every unique group value.</span></span> <span data-ttu-id="7d883-167">たとえば、販売注文を表示する Tablix データ領域の場合、販売注文の列名は静的行メンバーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-167">For example, in a tablix data region that displays a sales order, the column names in the sales order can be displayed on a static row member.</span></span> <span data-ttu-id="7d883-168">販売注文の各行は、動的行メンバーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d883-168">Each line in the sales order is displayed on a dynamic row member.</span></span>  
  
 <span data-ttu-id="7d883-169">Tablix メンバーの表示方法は、プロパティ ペインでプロパティを設定することによって制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-169">You can help control how a tablix member renders by setting properties in the Properties pane.</span></span> <span data-ttu-id="7d883-170">詳細については、「[グループ化ペイン &#40;レポート ビルダー&#41;](grouping-pane-report-builder.md)」の「詳細設定モード」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-170">For more information, see "Advanced mode" in [Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md).</span></span>  
  
 <span data-ttu-id="7d883-171">次の方法で、レポートにおける Tablix データ領域の表示方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-171">The following list describes ways that you can help control how a tablix data region appears in a report:</span></span>  
  
-   <span data-ttu-id="7d883-172">**複数ページで行および列のヘッダーを繰り返して表示する。** Tablix データ領域にまたがる各ページに、行および列ヘッダーを表示できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-172">**Repeating row and column headers on multiple pages**.You can display row and column headers on each page that a tablix data region spans.</span></span> <span data-ttu-id="7d883-173">詳細については、「[複数のページへの行および列ヘッダーの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-173">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7d883-174">**スクロール時に行および列ヘッダーを固定する。**</span><span class="sxs-lookup"><span data-stu-id="7d883-174">**Keeping row and column headers in view when scrolling**.</span></span> <span data-ttu-id="7d883-175">ブラウザーを使用してレポートをスクロールする際に、ビューの行および列ヘッダーを固定するかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d883-175">You can control whether to keep the row and column headers in view when you scroll a report using a browser.</span></span> <span data-ttu-id="7d883-176">詳細については、「[レポートのスクロール時にヘッダーを表示したままにする &#40;レポート ビルダーおよび SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-176">For more information, see [Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="7d883-177">別の形式にレポートをエクスポートすることが、ページ上の Tablix データ領域の表示に与える影響の詳細については、「[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d883-177">For more information about how exporting a report to different formats affects the way a tablix data region renders on a page, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d883-178">参照</span><span class="sxs-lookup"><span data-stu-id="7d883-178">See Also</span></span>  
 <span data-ttu-id="7d883-179">[同じデータセットへの複数のデータ領域のリンク &#40;レポートビルダーと SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d883-179">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d883-180">[入れ子になったデータ領域 &#40;レポートビルダーと SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d883-180">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d883-181">[合計、集計、および組み込みコレクションの式のスコープ &#40;レポートビルダーと SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span><span class="sxs-lookup"><span data-stu-id="7d883-181">[Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span></span>  
 <span data-ttu-id="7d883-182">[改ページ、見出し、列、および行の制御 &#40;レポートビルダーと SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d883-182">[Controlling Page Breaks, Headings, Columns, and Rows &#40;Report Builder and SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d883-183">[Tablix データ領域 &#40;レポートビルダーと SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d883-183">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d883-184">[テーブル &#40;レポートビルダーと SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d883-184">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d883-185">[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d883-185">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d883-186">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d883-186">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7d883-187">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7d883-187">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  