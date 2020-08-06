---
title: データ領域にデータがないことを示すメッセージの設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9ed38ef14eb8f89753b4b3d7af3324ef0e88fa52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713869"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="800e5-102">データ領域にデータがないことを示すメッセージの設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="800e5-102">Set a No Data Message for a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="800e5-103">データのないデータ領域の代わりに表示レポートに表示するテキストを指定するときは、テーブル、マトリックス、または一覧データ領域に対して NoRowsMessage プロパティを、グラフ データ領域に対して NoDataMessage を、マップのカラー スケールに対して NoDataText を、それぞれ設定します。</span><span class="sxs-lookup"><span data-stu-id="800e5-103">When you want to specify text to show in the rendered report in place of a data region that has no data, set the NoRowsMessage property for a table, matrix, or list data region, the NoDataMessage for a chart data region, and the NoDataText for the color scale for a map.</span></span> <span data-ttu-id="800e5-104">実行時にレポート プロセッサによってレポートの各データセットに対しクエリが実行されますが、データセット クエリによって結果セットが生成されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="800e5-104">At run time, the report processor runs the query for each dataset in a report and the dataset query may produce no result set.</span></span> <span data-ttu-id="800e5-105">空のデータセットにバインドされるデータ領域に対し、空のデータ領域を表示する代わりに表示するテキストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="800e5-105">For a data region bound to an empty dataset, you can specify text to display instead of displaying an empty data region.</span></span> <span data-ttu-id="800e5-106">また、サブレポートのデータセットに実行時のデータがない場合、サブレポートに対し NoRowsMessage プロパティを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="800e5-106">You can also set the NoRowsMessage property for a subreport when no datasets in the subreport have data at run time.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a><span data-ttu-id="800e5-107">テーブル、マトリックス、リストに NoRowsMessage プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="800e5-107">To set the NoRowsMessage property for a table, matrix, or list</span></span>  
  
1.  <span data-ttu-id="800e5-108">[デザイン] ビューで、デザイン画面のテーブル、マトリックス、一覧データ領域、またはサブレポートをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="800e5-108">In Design view, click the table, matrix, or list data region or subreport on the design surface to select it.</span></span> <span data-ttu-id="800e5-109">選択したアイテムのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="800e5-109">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="800e5-110">プロパティペインで、プロパティフィールドにメッセージとして表示するテキストを入力し `NoRowsMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="800e5-110">In the Properties pane, type the text that you want to display as a message in `NoRowsMessage` property field.</span></span>  
  
     <span data-ttu-id="800e5-111">または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="800e5-111">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a><span data-ttu-id="800e5-112">グラフに NoDataMessage プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="800e5-112">To set the NoDataMessage property for a chart</span></span>  
  
1.  <span data-ttu-id="800e5-113">[デザイン] ビューで、デザイン画面のグラフをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="800e5-113">In Design view, click the chart on the design surface to select it.</span></span> <span data-ttu-id="800e5-114">選択したアイテムのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="800e5-114">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="800e5-115">プロパティペインで、のノードを展開し `NoDataMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="800e5-115">In the Properties pane, expand the node for `NoDataMessage`.</span></span>  
  
3.  <span data-ttu-id="800e5-116">[**キャプション**] に、プロパティフィールドにメッセージとして表示するテキストを入力し `NoDataMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="800e5-116">In **Caption**, type the text that you want to display as a message in `NoDataMessage` property field.</span></span>  
  
     <span data-ttu-id="800e5-117">または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="800e5-117">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a><span data-ttu-id="800e5-118">サブレポートに NoRowsMessage を設定するには</span><span class="sxs-lookup"><span data-stu-id="800e5-118">To set the NoRowsMessage for a subreport</span></span>  
  
1.  <span data-ttu-id="800e5-119">[デザイン] ビューで、デザイン画面のサブレポートをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="800e5-119">In Design view, click the subreport on the design surface to select it.</span></span> <span data-ttu-id="800e5-120">選択したアイテムのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="800e5-120">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="800e5-121">プロパティペインで、プロパティフィールドにメッセージとして表示するテキストを入力し `NoRowsMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="800e5-121">In the Properties pane, type the text that you want to display as a message in `NoRowsMessage` property field.</span></span>  
  
     <span data-ttu-id="800e5-122">または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="800e5-122">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a><span data-ttu-id="800e5-123">マップのカラー スケールに NoDataText プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="800e5-123">To set the NoDataText property for a color scale for a map</span></span>  
  
1.  <span data-ttu-id="800e5-124">[デザイン] ビューで、マップのカラー スケールをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="800e5-124">In Design view, click the color scale on the map to select it.</span></span> <span data-ttu-id="800e5-125">選択したアイテムのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="800e5-125">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="800e5-126">プロパティペインの [] に、 `NoDataText` データ値のない色のラベルとして表示するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="800e5-126">In the Properties pane, in `NoDataText`, type the text that you want to display as a label for colors with no data value.</span></span>  
  
     <span data-ttu-id="800e5-127">または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="800e5-127">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="800e5-128">参照</span><span class="sxs-lookup"><span data-stu-id="800e5-128">See Also</span></span>  
 <span data-ttu-id="800e5-129">[サブレポート &#40;レポート ビルダーおよび SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="800e5-129">[Subreports &#40;Report Builder and SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="800e5-130">[テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="800e5-130">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="800e5-131">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="800e5-131">[Charts &#40;Report Builder and SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="800e5-132">[マップ &#40;レポート ビルダーおよび SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="800e5-132">[Maps &#40;Report Builder and SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="800e5-133">サブレポート (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="800e5-133">Subreports &#40;Report Builder and SSRS&#41;</span></span>](../report-design/subreports-report-builder-and-ssrs.md)  
  
  
