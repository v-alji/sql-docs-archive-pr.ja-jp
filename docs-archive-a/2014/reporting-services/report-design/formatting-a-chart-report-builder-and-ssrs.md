---
title: グラフの書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10214"
- sql12.rtp.rptdesigner.calculatedseriesproperties.fill.f1
- sql12.rtp.rptdesigner.serieslabelproperties.fill.f1
- sql12.rtp.rptdesigner.legendproperties.fill.f1
- "10149"
- sql12.rtp.rptdesigner.seriesproperties.shadow.f1
- sql12.rtp.rptdesigner.seriesproperties.markers.f1
- "10255"
- sql12.rtp.rptdesigner.charttitleproperties.fill.f1
- "10154"
- "10170"
- "10173"
- sql12.rtp.rptdesigner.seriesproperties.fill.f1
- "10169"
- "10158"
- sql12.rtp.rptdesigner.chartareaproperties.fill.f1
- sql12.rtp.rptdesigner.charttitleproperties.shadow.f1
- "10246"
- "10150"
- sql12.rtp.rptdesigner.calculatedseriesproperties.borders.f1
- sql12.rtp.rptdesigner.chartproperties.fill.f1
- "10159"
- sql12.rtp.rptdesigner.majorgridlineproperties.gridlineoptions.f1
- "10160"
- sql12.rtp.rptdesigner.serieslabelproperties.font.f1
- "10182"
- "10163"
- "10164"
- "10253"
- "10216"
- "10171"
- "10257"
- sql12.rtp.rptdesigner.chartareaproperties.border.f1
- sql12.rtp.rptdesigner.calculatedseriesproperties.shadow.f1
- sql12.rtp.rptdesigner.chartproperties.border.f1
- sql12.rtp.rptdesigner.minorgridlineproperties.gridlineoptions.f1
- sql12.rtp.rptdesigner.chartareaproperties.shadow.f1
- sql12.rtp.rptdesigner.charttitleproperties.borders.f1
- sql12.rtp.rptdesigner.charttitleproperties.font.f1
- "10247"
ms.assetid: d3984300-c766-42f8-b7c4-863123d67c99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af164d4db9b6439f0634d113652b95939827b0f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634842"
---
# <a name="formatting-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="627c3-102">グラフの書式設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="627c3-102">Formatting a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="627c3-103">グラフのデータを定義し、そのデータが希望どおりに表示されるようになったら、書式を追加して、全体的な外観を改善したり主要なデータ ポイントを強調したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="627c3-103">After you have defined the data for your chart and it is appearing the way you want, you can add formatting to improve the overall appearance and highlight key data points.</span></span> <span data-ttu-id="627c3-104">最も一般的な書式設定オプションは、グラフ要素を右クリックして表示されるショートカット メニューを使用すると表示できるプロパティ ダイアログ ボックスから変更できます。</span><span class="sxs-lookup"><span data-stu-id="627c3-104">The most common formatting options can be modified from the Properties dialog box that are found when you right-click a chart element to display its shortcut menu.</span></span> <span data-ttu-id="627c3-105">各グラフ要素には、独自のダイアログ ボックスがあります。</span><span class="sxs-lookup"><span data-stu-id="627c3-105">Each chart element has its own dialog box.</span></span> <span data-ttu-id="627c3-106">グラフ要素の詳細については、「 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="627c3-106">For more information about chart elements, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="627c3-107">グラフに関連するプロパティはすべてプロパティ ペインにありますが、これらのプロパティの多くはダイアログ ボックスから設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="627c3-107">All properties that relate to the chart are located in the Properties pane, but many of these properties can also be set from a dialog box.</span></span> <span data-ttu-id="627c3-108">系列の書式を設定する場合は、カスタム属性を使用して系列固有のプロパティを指定できます。カスタム属性は、プロパティ ペイン内にある、プロパティの **[CustomAttributes]** カテゴリのみで操作できます。</span><span class="sxs-lookup"><span data-stu-id="627c3-108">If you are formatting the series, you can specify series-specific properties using custom attributes, which can only be found in the **CustomAttributes** category of properties, located in the Properties pane.</span></span>  
  
 <span data-ttu-id="627c3-109">使用する手順の数を最小限に抑えてグラフの書式を効率的に設定するには、罫線のスタイル、パレット、および描画スタイルを既定値から変更します。</span><span class="sxs-lookup"><span data-stu-id="627c3-109">To effectively format the chart using a minimal number of steps, change the default border style, palette and drawing style.</span></span> <span data-ttu-id="627c3-110">この 3 つの機能は、グラフの外観に最も大きな変化をもたらします。</span><span class="sxs-lookup"><span data-stu-id="627c3-110">These three features produce the largest visible change on the chart.</span></span> <span data-ttu-id="627c3-111">描画スタイルを適用できるのは、円グラフ、ドーナツ グラフ、横棒グラフ、および縦棒グラフだけです。</span><span class="sxs-lookup"><span data-stu-id="627c3-111">Drawing styles are only applicable to pie, doughnut, bar and column charts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="627c3-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="627c3-112">In This Section</span></span>  
 [<span data-ttu-id="627c3-113">グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="627c3-113">Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="627c3-114">パレットを使用して色を定義する方法、独自の色パレットを定義する方法、および式に基づいて色を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="627c3-114">Discusses how colors are defined using a palette, how you can define your own color palette, and how to define colors based on an expression.</span></span>  
  
 [<span data-ttu-id="627c3-115">グラフの軸ラベルの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="627c3-115">Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="627c3-116">グリッド線、目盛り、およびタイトルを表示する方法と、軸スケール上の数値と日付の書式を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="627c3-116">Discusses how to display gridlines, tick marks, and titles, and how to format numbers and dates on the axis scale.</span></span>  
  
 [<span data-ttu-id="627c3-117">グラフの凡例の書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="627c3-117">Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-formatting-report-builder.md)  
 <span data-ttu-id="627c3-118">グラフの凡例内のアイテムの順序変更と書式設定を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="627c3-118">Discusses how to re-order and format items in the chart legend.</span></span>  
  
 [<span data-ttu-id="627c3-119">グラフでのデータ ポイントの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="627c3-119">Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="627c3-120">グラフ上のすべての系列に対するデータ ポイント ラベルの配置とデータ ポイント マーカーの書式設定を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="627c3-120">Discusses how to position data point labels and format data point markers for every series on the chart.</span></span>  
  
 [<span data-ttu-id="627c3-121">グラフに対する 3D、傾斜、およびその他の効果 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="627c3-121">3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-3d-bevel-and-other-report-builder.md)  
 <span data-ttu-id="627c3-122">グラフに適用できるさまざまな 3D 効果について説明します。</span><span class="sxs-lookup"><span data-stu-id="627c3-122">Discusses various 3D effects that you can apply to a chart.</span></span>  
  
 [<span data-ttu-id="627c3-123">グラフへの枠線の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="627c3-123">Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="627c3-124">グラフに枠線を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="627c3-124">Explains how to add a border frame to a chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="627c3-125">参照</span><span class="sxs-lookup"><span data-stu-id="627c3-125">See Also</span></span>  
 <span data-ttu-id="627c3-126">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="627c3-126">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="627c3-127">[グラフへの枠線の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="627c3-127">[Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="627c3-128">[パレットを使用したグラフの色の定義 &#40;レポート ビルダーおよび SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="627c3-128">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="627c3-129">グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="627c3-129">Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
