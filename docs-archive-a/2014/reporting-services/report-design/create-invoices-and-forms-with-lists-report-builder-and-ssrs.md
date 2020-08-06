---
title: リスト (レポートビルダーと SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c33231a5-b3a8-42e4-95bc-d05bdf2222f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9afb0dfabe5ccc3962d43eef30031a728514135
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634875"
---
# <a name="lists-report-builder-and-ssrs"></a><span data-ttu-id="88e70-102">一覧 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="88e70-102">Lists (Report Builder and SSRS)</span></span>
  <span data-ttu-id="88e70-103">一覧データ領域は、レポート データセットのグループまたは行ごとに繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="88e70-103">A list data region repeats with each group or row in the report dataset.</span></span> <span data-ttu-id="88e70-104">一覧は、他のデータ領域と関連付けて自由形式レポートや、請求書などのフォームを作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="88e70-104">A list can be used to create free-form reports or forms, such as invoices, or in conjunction with other data regions.</span></span> <span data-ttu-id="88e70-105">任意の数のレポート アイテムを含んでいる一覧を定義できます。</span><span class="sxs-lookup"><span data-stu-id="88e70-105">You can define lists that contain any number of report items.</span></span> <span data-ttu-id="88e70-106">一覧を他の一覧内に入れ子にして、複数のデータ グループを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="88e70-106">A list can be nested within another list to provide multiple groups of data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88e70-107">一覧は、レポート パーツとしてレポートとは別にパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="88e70-107">You can publish lists separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="88e70-108">一覧の利用をすぐに開始するには、「[チュートリアル: 自由形式のレポートの作成 &#40;レポート ビルダー&#41;](../tutorial-creating-a-free-form-report-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88e70-108">To quickly get started with lists, see [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../tutorial-creating-a-free-form-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="88e70-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサンプル レポートには、一覧を使用したレポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="88e70-109">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sample reports include a report that uses a list.</span></span> <span data-ttu-id="88e70-110">一覧に関する知識は、レポート ビルダーまたはレポート デザイナーでサンプル レポートのレポート定義を詳しく調べるか、表示されたレポートをレポート ビルダーまたはレポート デザイナーでプレビューすることによって身に付けることができます。</span><span class="sxs-lookup"><span data-stu-id="88e70-110">You can learn about lists by exploring the report definition of the sample report in Report Builder or Report Designer or by previewing the rendered report in Report Builder or Report Designer.</span></span> <span data-ttu-id="88e70-111">サンプル レポートのダウンロードの詳細については、「 [(SSRS) Reporting Services のサンプル](https://go.microsoft.com/fwlink/?LinkID=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88e70-111">For more information about downloading the sample reports, see [(SSRS) Reporting Services Samples](https://go.microsoft.com/fwlink/?LinkID=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-list-to-your-report"></a><a name="AddingList"></a><span data-ttu-id="88e70-112">レポートへのリストの追加</span><span class="sxs-lookup"><span data-stu-id="88e70-112">Adding a List to Your Report</span></span>  
 <span data-ttu-id="88e70-113">リボンの [挿入] タブからデザイン画面に一覧を追加します。</span><span class="sxs-lookup"><span data-stu-id="88e70-113">Add a list to the design surface from the Insert tab on ribbon.</span></span> <span data-ttu-id="88e70-114">既定では、一覧にはまず詳細グループに関連付けられた行に 1 つのセルがあります。</span><span class="sxs-lookup"><span data-stu-id="88e70-114">By default, the list initially has a single cell in a row associated with the detail group.</span></span>  
  
 <span data-ttu-id="88e70-115">![デザイン画面上の [新しい一覧] レポート アイテム](../media/rs-listtemplatenew.gif "デザイン画面上の [新しい一覧] レポート アイテム")</span><span class="sxs-lookup"><span data-stu-id="88e70-115">![New List report item on the design surface](../media/rs-listtemplatenew.gif "New List report item on the design surface")</span></span>  
  
 <span data-ttu-id="88e70-116">デザイン画面で一覧を選択すると、次の図に示すように、行および列のハンドルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="88e70-116">When you select a list on the design surface, row and column handles appear, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="88e70-117">![ツールボックスから追加された新しい一覧、選択](../media/rs-listtemplatenewselected.gif "ツールボックスから追加された新しい一覧、選択")</span><span class="sxs-lookup"><span data-stu-id="88e70-117">![New List added from Toolbox, selected](../media/rs-listtemplatenewselected.gif "New List added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="88e70-118">一覧を追加する際には、まず Tablix データ領域に基づくテンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="88e70-118">The list you start with is a template based on the tablix data region.</span></span> <span data-ttu-id="88e70-119">一覧の追加後、フィルター、並べ替え、グループ式を指定することにより一覧のコンテンツや外観を変更したり、レポート ページ全体での一覧の表示を変更することによりデザインの拡張を継続できます。</span><span class="sxs-lookup"><span data-stu-id="88e70-119">After you add a list, you can continue to enhance the design by changing the content or appearance of the list by specifying filter, sort, or group expressions, or changing the way the list displays across report pages.</span></span> <span data-ttu-id="88e70-120">詳細については、「 [レポート ページでの Tablix データ領域の表示の制御 &#40;レポート ビルダーおよび SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88e70-120">For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).</span></span> <span data-ttu-id="88e70-121">一覧は 1 つの列と行が基本ですが、入れ子、隣接する行グループや列グループ、または詳細行を追加することにより、一覧のデザイン展開を継続できます。</span><span class="sxs-lookup"><span data-stu-id="88e70-121">Although the list starts with a single column and row, you can further continue to develop your list design by adding nested or adjacent row groups or column groups, or adding additional detail rows.</span></span> <span data-ttu-id="88e70-122">詳細については、「[Tablix データ領域の柔軟性について &#40;レポート ビルダーおよび SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88e70-122">For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="displaying-data-in-a-free-form-layout"></a><a name="DisplayingLayout"></a> <span data-ttu-id="88e70-123">自由形式のレイアウトでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="88e70-123">Displaying Data in a Free-form Layout</span></span>  
 <span data-ttu-id="88e70-124">グリッドではなく自由形式のレイアウトでレポート データを編成するには、一覧をデザイン画面に追加します。</span><span class="sxs-lookup"><span data-stu-id="88e70-124">To organize report data in a free-form layout instead of a grid, you can add a list to the design surface.</span></span> <span data-ttu-id="88e70-125">レポート データ ペインからセルにフィールドをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="88e70-125">Drag fields from the Report Data pane to the cell.</span></span> <span data-ttu-id="88e70-126">既定では、セルにはコンテナーとして機能する四角形が含まれています。</span><span class="sxs-lookup"><span data-stu-id="88e70-126">By default, the cell contains a rectangle that acts as a container.</span></span> <span data-ttu-id="88e70-127">コンテナーで各フィールドを移動させ、目的のデザインを取得します。</span><span class="sxs-lookup"><span data-stu-id="88e70-127">Move each field in the container until you have the design you want.</span></span> <span data-ttu-id="88e70-128">四角形のコンテナーにテキスト ボックスをドラッグする際に表示されるスナップラインを使用して、垂直および水平方向の端を合わせます。</span><span class="sxs-lookup"><span data-stu-id="88e70-128">Use the snaplines that appear when you drag text boxes in the rectangle container to help you align edges vertically and horizontally.</span></span> <span data-ttu-id="88e70-129">セルのサイズを調整して、不要な空白を削除します。</span><span class="sxs-lookup"><span data-stu-id="88e70-129">Remove unwanted white space by adjusting the size of the cell.</span></span> <span data-ttu-id="88e70-130">詳細については、「[行の高さまたは列の幅の変更 &#40;レポート ビルダーおよび SSRS&#41;](change-row-height-or-column-width-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88e70-130">For more information, see [Change Row Height or Column Width &#40;Report Builder and SSRS&#41;](change-row-height-or-column-width-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="88e70-131">次の図には、注文情報を表示する一覧を示します。一覧には、Date、Order、Qty、Product、LineTotal のフィールドおよび画像が含まれます。</span><span class="sxs-lookup"><span data-stu-id="88e70-131">The following figure shows a list that displays information about an order, including these fields: Date, Order, Qty, Product, LineTotal, and an image.</span></span>  
  
 <span data-ttu-id="88e70-132">![デザイン ビューの一覧、4 つのフィールドと画像](../media/rs-basiclistformdesign.gif "デザイン ビューの一覧、4 つのフィールドと画像")</span><span class="sxs-lookup"><span data-stu-id="88e70-132">![List in design view, 4 fields and an image](../media/rs-basiclistformdesign.gif "List in design view, 4 fields and an image")</span></span>  
  
 <span data-ttu-id="88e70-133">プレビューでは、一覧は次の図で示されるとおり、自由形式でフィールド データを表示します。</span><span class="sxs-lookup"><span data-stu-id="88e70-133">In Preview, the list repeats to display the field data in the free-form format, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="88e70-134">![4 つのフィールドと 1 つの画像がある一覧のプレビュー](../media/rs-basiclistformpreview.gif "4 つのフィールドと 1 つの画像がある一覧のプレビュー")</span><span class="sxs-lookup"><span data-stu-id="88e70-134">![Preview for List with 4 fields and one image](../media/rs-basiclistformpreview.gif "Preview for List with 4 fields and one image")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88e70-135">これらの図に表示される点線は、各フィールド値の自由形式レイアウトを示すために含まれます。</span><span class="sxs-lookup"><span data-stu-id="88e70-135">The dotted lines displays in these figures are included to show the free-form layout for each field value.</span></span> <span data-ttu-id="88e70-136">通常、運用レポートでは点線は使用されません。</span><span class="sxs-lookup"><span data-stu-id="88e70-136">Typically, you would not use dotted lines in a production report.</span></span>  
  

  
##  <a name="displaying-data-with-one-level-of-grouping"></a><a name="DisplayingGrouping"></a> <span data-ttu-id="88e70-137">単一グループ化レベルでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="88e70-137">Displaying Data with One Level of Grouping</span></span>  
 <span data-ttu-id="88e70-138">一覧は自動的にコンテナーを提供するため、一覧を使用してグループ化されたデータを複数のビューで表示できます。</span><span class="sxs-lookup"><span data-stu-id="88e70-138">Because a list automatically provides a container, you can use a list to display grouped data with multiple views.</span></span> <span data-ttu-id="88e70-139">グループを指定するように既定の一覧を変更するには、詳細グループを編集し、新しい名前を指定し、グループ式を指定します。</span><span class="sxs-lookup"><span data-stu-id="88e70-139">To change the default list to specify a group, edit the Details group, specify a new name, and specify a group expression.</span></span>  
  
 <span data-ttu-id="88e70-140">たとえば、同じデータの異なるビューを示すテーブルやグラフを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="88e70-140">For example, you can embed a table and a chart that show different views of the same dataset.</span></span> <span data-ttu-id="88e70-141">一覧にグループを追加して、入れ子レポート アイテムが各グループ値につき 1 回繰り返されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="88e70-141">You can add a group to the list so that the nested report items will repeat once for every group value.</span></span> <span data-ttu-id="88e70-142">次の図には、製品カテゴリでグループ化された一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="88e70-142">The following figure shows a list grouped by product category.</span></span> <span data-ttu-id="88e70-143">詳細行がないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="88e70-143">Notice that there is no detail row.</span></span> <span data-ttu-id="88e70-144">2 つのテーブルは、一覧で並列の入れ子になっています。</span><span class="sxs-lookup"><span data-stu-id="88e70-144">Two tables are nested side by side in the list.</span></span> <span data-ttu-id="88e70-145">最初のテーブルには、サブカテゴリが売上合計と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="88e70-145">The first table displays the subcategories with total sales.</span></span> <span data-ttu-id="88e70-146">2 番目のテーブルには、地域によってグループ化されたカテゴリが、サブカテゴリの分布を示すグラフと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="88e70-146">The second table displays the category grouped by geographical area, with a chart that shows the distribution of subcategories.</span></span>  
  
 <span data-ttu-id="88e70-147">![2 つのテーブルが含まれるリスト、一方はグラフが入れ子](../media/rs-basiclistgroupdesign.gif "2 つのテーブルが含まれるリスト、一方はグラフが入れ子")</span><span class="sxs-lookup"><span data-stu-id="88e70-147">![A list with 2 tables, one with nested chart](../media/rs-basiclistgroupdesign.gif "A list with 2 tables, one with nested chart")</span></span>  
  
 <span data-ttu-id="88e70-148">プレビューでは、テーブルに自転車のすべてのサブカテゴリの売上合計が表示され、その横のテーブルには、地域ごとの売上の内訳が示されます。</span><span class="sxs-lookup"><span data-stu-id="88e70-148">In Preview, the table displays total sales for all subcategories of bicycles, and the table beside it displays the breakdown of sales per geographical area.</span></span> <span data-ttu-id="88e70-149">テーブルおよびグラフのカスタム パレットの背景色を指定する式を使用すると、最初のテーブルにグラフの色の凡例が示されます。</span><span class="sxs-lookup"><span data-stu-id="88e70-149">By using an expression to specify the background color for the table and a custom palette for the chart, the first table also provides the legend for the chart colors.</span></span>  
  
 <span data-ttu-id="88e70-150">![プレビュー、2 つのテーブル、一方はグラフが入れ子](../media/rs-basiclistgrouppreview.gif "プレビュー、2 つのテーブル、一方はグラフが入れ子")</span><span class="sxs-lookup"><span data-stu-id="88e70-150">![Preview, 2 tables, one with nested chart](../media/rs-basiclistgrouppreview.gif "Preview, 2 tables, one with nested chart")</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="88e70-151">参照</span><span class="sxs-lookup"><span data-stu-id="88e70-151">See Also</span></span>  
 <span data-ttu-id="88e70-152">[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="88e70-152">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 [<span data-ttu-id="88e70-153">式の例 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="88e70-153">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
