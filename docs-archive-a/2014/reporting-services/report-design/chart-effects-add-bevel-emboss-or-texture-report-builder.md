---
title: グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92c5d4af47b7889b9ba5ec421706848f8822075b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644333"
---
# <a name="add-bevel-emboss-and-texture-styles-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="22f9d-102">グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="22f9d-102">Add Bevel, Emboss, and Texture Styles to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="22f9d-103">特定のグラフの種類を使用する場合、グラフの視覚的な効果を高めるために、描画効果を指定できます。</span><span class="sxs-lookup"><span data-stu-id="22f9d-103">When using certain chart types, you can specify a drawing effect to increase the visual impact of your chart.</span></span> <span data-ttu-id="22f9d-104">このような描画効果を適用できるのは、グラフの系列だけです。</span><span class="sxs-lookup"><span data-stu-id="22f9d-104">These drawing effects are only applied to the series of your chart.</span></span> <span data-ttu-id="22f9d-105">その他のグラフ要素には影響しません。</span><span class="sxs-lookup"><span data-stu-id="22f9d-105">They have no effect on any other chart element.</span></span>  
  
 <span data-ttu-id="22f9d-106">円グラフまたはドーナツ グラフの一種を使用する場合、画像に適用できる傾斜やエンボスの効果と同様、ぼかしや凹状の描画スタイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="22f9d-106">When you are using any variant of a pie or doughnut chart, you can specify a soft edge or concave drawing style, similar to bevel or emboss effects that can be applied to an image.</span></span>  
  
 <span data-ttu-id="22f9d-107">横棒グラフまたは縦棒グラフの一種を使用する場合、円柱、くさび形、グラデーションなどのテクスチャのスタイルを、個々の横棒および縦棒に適用できます。</span><span class="sxs-lookup"><span data-stu-id="22f9d-107">When you are using any variant of a bar or column chart, you can apply texture styles, such as cylinder, wedge, and light-to-dark, to the individual bars or columns.</span></span>  
  
 <span data-ttu-id="22f9d-108">多くのグラフ要素では、これらの描画スタイルに加え、罫線および影を追加することで、奥行を持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="22f9d-108">In addition to these drawing styles, you can add borders and shadows to many chart elements to give the illusion of depth.</span></span> <span data-ttu-id="22f9d-109">その他のグラフの書式設定方法の詳細については、「 [グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22f9d-109">For more information on other ways to format the chart, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a><span data-ttu-id="22f9d-110">円グラフまたはドーナツ グラフに傾斜またはエンボスのスタイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="22f9d-110">To add bevel or emboss styles to a pie or doughnut chart</span></span>  
  
1.  <span data-ttu-id="22f9d-111">**[表示]** タブで、 **[プロパティ]** を選択してプロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="22f9d-111">On the **View** tab, select **Properties** to open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="22f9d-112">強調する円グラフまたはドーナツ グラフを選択します。</span><span class="sxs-lookup"><span data-stu-id="22f9d-112">Select the pie or doughnut chart that you want to enhance.</span></span> <span data-ttu-id="22f9d-113">グラフ全体ではなく、グラフのデータ フィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="22f9d-113">Select a data field in the chart, not the entire chart.</span></span>  
  
3.  <span data-ttu-id="22f9d-114">プロパティ ペインで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="22f9d-114">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="22f9d-115">PieDrawingStyle で、ドロップダウン リストからスタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="22f9d-115">For PieDrawingStyle, select a style from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22f9d-116">3D と、傾斜またはエンボスのスタイルを同じグラフに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="22f9d-116">You can't have 3D and bevel or emboss styles on the same chart.</span></span> <span data-ttu-id="22f9d-117">グラフで 3D を有効にした場合は、PieDrawingStyle プロパティが表示されません。</span><span class="sxs-lookup"><span data-stu-id="22f9d-117">If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.</span></span>  
  
 <span data-ttu-id="22f9d-118">![凹型描画スタイルの円グラフ](../media/rs-piedrawingeffects-concave.gif "凹型描画スタイルの円グラフ")</span><span class="sxs-lookup"><span data-stu-id="22f9d-118">![Pie chart with concave drawing style](../media/rs-piedrawingeffects-concave.gif "Pie chart with concave drawing style")</span></span>  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a><span data-ttu-id="22f9d-119">横棒グラフまたは縦棒グラフにテクスチャのスタイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="22f9d-119">To add texture styles to a bar or column chart</span></span>  
  
1.  <span data-ttu-id="22f9d-120">強調する横棒グラフまたは縦棒グラフを選択します。</span><span class="sxs-lookup"><span data-stu-id="22f9d-120">Select the bar or column chart that you want to enhance.</span></span> <span data-ttu-id="22f9d-121">グラフ全体ではなく、グラフのデータ フィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="22f9d-121">Select a data field in the chart, not the entire chart.</span></span>  
  
2.  <span data-ttu-id="22f9d-122">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="22f9d-122">Open the Properties pane.</span></span>  
  
3.  <span data-ttu-id="22f9d-123">**[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="22f9d-123">Expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="22f9d-124">DrawingStyle で、ドロップダウン リストからスタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="22f9d-124">For DrawingStyle, select a style from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22f9d-125">3D と、傾斜またはエンボスのスタイルを同じグラフに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="22f9d-125">You can't have 3D and bevel or emboss styles on the same chart.</span></span> <span data-ttu-id="22f9d-126">グラフで 3D を有効にした場合は、PieDrawingStyle プロパティが表示されません。</span><span class="sxs-lookup"><span data-stu-id="22f9d-126">If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.</span></span>  
  
 <span data-ttu-id="22f9d-127">![LightToDark 描画効果付きの横棒グラフ](../media/rs-bardrawingeffects-lighttodark.gif "LightToDark 描画効果付きの横棒グラフ")</span><span class="sxs-lookup"><span data-stu-id="22f9d-127">![Bar chart with LightToDark drawing effect](../media/rs-bardrawingeffects-lighttodark.gif "Bar chart with LightToDark drawing effect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f9d-128">参照</span><span class="sxs-lookup"><span data-stu-id="22f9d-128">See Also</span></span>  
 <span data-ttu-id="22f9d-129">[横棒グラフ (レポート ビルダーおよび SSRS)](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22f9d-129">[Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="22f9d-130">[縦棒グラフ &#40;レポート ビルダーおよび SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22f9d-130">[Column Charts &#40;Report Builder and SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="22f9d-131">[円グラフ &#40;レポート ビルダーおよび SSRS&#41;](pie-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22f9d-131">[Pie Charts &#40;Report Builder and SSRS&#41;](pie-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="22f9d-132">グラフの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="22f9d-132">Formatting a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
