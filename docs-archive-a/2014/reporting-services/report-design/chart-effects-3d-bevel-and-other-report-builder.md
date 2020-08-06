---
title: グラフに対する 3D、傾斜、およびその他の効果 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10156"
ms.assetid: 18ef2119-2931-43ae-9078-f39b460462dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f505a0226d1c95a1c0c7c3caffde2be60f407b43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644337"
---
# <a name="3d-bevel-and-other-effects-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="a7a76-102">グラフに対する 3D、傾斜、およびその他の効果 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a7a76-102">3D, Bevel, and Other Effects in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a7a76-103">3 次元 (3D) 効果を使用すると、グラフに奥行を与え、グラフの視覚的な効果を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-103">Three-dimensional (3D) effects can be used to provide depth and add visual impact to your chart.</span></span> <span data-ttu-id="a7a76-104">たとえば、分割円グラフの特定のスライスを強調する場合は、そのスライスが最初に目に留まるように、グラフのパースペクティブを回転および変更することができます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-104">For example, if you want to emphasize a particular slice of an exploded pie chart, you can rotate and change the perspective of the chart so that people notice that slice first.</span></span> <span data-ttu-id="a7a76-105">グラフに 3D 効果を適用すると、グラデーションの色および陰影のスタイルはすべて無効になります。</span><span class="sxs-lookup"><span data-stu-id="a7a76-105">When 3D effects are applied to your chart, all gradient colors and hatching styles are disabled.</span></span>  
  
 <span data-ttu-id="a7a76-106">3 次元効果は個々のグラフに適用することができます。また、2 次元グラフと 3 次元グラフの両方を同じレポートに表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-106">Three-dimensional effects can be applied to individual charts, and it is possible to display both two-dimensional and three-dimensional charts on the same report.</span></span>  
  
 <span data-ttu-id="a7a76-107">すべての種類のグラフでは、 **[グラフ領域のプロパティ]** ダイアログ ボックスで **[3D の有効化]** チェック ボックスをオンにすることにより、グラフ領域に 3 次元効果を適用できます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-107">For all chart types, you can add three-dimensional effects to a chart area in the **Chart Area Properties** dialog box by selecting **Enable 3D**.</span></span> <span data-ttu-id="a7a76-108">詳細については、「 [グラフへの 3D 効果の追加 (レポート ビルダーおよび SSRS)](chart-effects-add-3d-effects-report-builder.md)チェック ボックスをオンにすることにより、グラフ領域に 3 次元効果を適用できます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-108">For more information, see [Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-3d-effects-report-builder.md).</span></span>  
  
 <span data-ttu-id="a7a76-109">グラフの視覚的な効果を高めるには、傾斜、エンボス、およびテクスチャのスタイルを横棒グラフ、縦棒グラフ、円グラフ、およびドーナツ グラフに追加する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="a7a76-109">Another way to add visual impact to charts is by adding bevel, emboss and texture styles in bar, column, pie and doughnut charts.</span></span> <span data-ttu-id="a7a76-110">詳細については、「[グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 (レポート ビルダーおよび SSRS)](chart-effects-add-bevel-emboss-or-texture-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7a76-110">For more information, see [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="coordinate-based-three-dimensional-charts"></a><span data-ttu-id="a7a76-111">座標ベースの 3 次元グラフ</span><span class="sxs-lookup"><span data-stu-id="a7a76-111">Coordinate-Based Three-Dimensional Charts</span></span>  
 <span data-ttu-id="a7a76-112">座標ベースのグラフ (縦棒グラフ、横棒グラフ、面グラフ、散布図、折れ線グラフ、範囲グラフ) を使用している場合、3 次元効果を適用すると、"z 軸" と呼ばれる 3 つ目の軸がグラフに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-112">When working with coordinate-based chart types (Column, Bar, Area, Point, Line and Range), three-dimensional effects display the chart with a third axis, known as the "z-axis".</span></span> <span data-ttu-id="a7a76-113">この 3 つ目の軸の導入により、さまざまな視覚的な機能強化をグラフに適用することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="a7a76-113">The introduction of this third axis allows you to apply a variety of visual enhancements to your chart.</span></span>  
  
### <a name="changing-the-white-space-in-a-3d-chart"></a><span data-ttu-id="a7a76-114">3D グラフ内の空白の変更</span><span class="sxs-lookup"><span data-stu-id="a7a76-114">Changing the White Space in a 3D Chart</span></span>  
 <span data-ttu-id="a7a76-115">3 次元モードでグラフ領域を表示すると、各系列は、グラフの z 軸に沿って個別の行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-115">When you display a chart area in three-dimensional mode, each series is shown in a separate row along the z-axis of the chart.</span></span> <span data-ttu-id="a7a76-116">各系列の間の間隔を変更するには、[3D 効果] ダイアログ ボックスの **[ポイントのギャップの深さ]** プロパティを変更することにより、グラフのポイントのギャップの深さを変更します。</span><span class="sxs-lookup"><span data-stu-id="a7a76-116">To change the amount of space between each series, modify the chart's point gap depth by changing the **Point Gap Depth** property in the 3D Effects dialog box.</span></span>  
  
### <a name="changing-the-projection-of-a-3d-chart"></a><span data-ttu-id="a7a76-117">3D グラフの投影の変更</span><span class="sxs-lookup"><span data-stu-id="a7a76-117">Changing the Projection of a 3D Chart</span></span>  
 <span data-ttu-id="a7a76-118">3D 投影には、斜投影と透視投影の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="a7a76-118">There are two types of 3D projections: oblique and perspective.</span></span> <span data-ttu-id="a7a76-119">グラフに斜投影を適用すると、2 次元グラフに奥行が加わります。</span><span class="sxs-lookup"><span data-stu-id="a7a76-119">An oblique projection to the chart adds a depth dimension to a two-dimensional chart.</span></span> <span data-ttu-id="a7a76-120">z 軸は横軸と縦軸から等しい角度で描画されます。横軸と縦軸は、2 次元グラフと同様、直角に交わっています。</span><span class="sxs-lookup"><span data-stu-id="a7a76-120">The z-axis is drawn at equal angles from the horizontal and vertical axes, which remain perpendicular to each other just as in a two-dimensional chart.</span></span>  
  
 <span data-ttu-id="a7a76-121">透視投影を適用すると、ビュー平面が推定され、その地点を視点としてグラフが再描画されて、グラフが変換されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-121">Perspective projection transforms the chart by estimating a view plane and re-drawing the chart as if it were being viewed from that point.</span></span> <span data-ttu-id="a7a76-122">**[回転]** ボックスの値を使用すると、視点を "地面の高さ" (0) から頭上 (90) まで垂直方向に移動できます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-122">The **Rotation** value shifts the view vertically from "ground level" at 0 to overhead at 90.</span></span> <span data-ttu-id="a7a76-123">**[傾斜]** ボックスの値を使用すると、表示角度を左または右へ移動できます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-123">The **Inclination** value shifts the viewing angle to the left or right.</span></span> <span data-ttu-id="a7a76-124">値が 0 の場合は、グラフの 2 次元表示と同じです。</span><span class="sxs-lookup"><span data-stu-id="a7a76-124">A value of 0 is equivalent to a two-dimensional view of the chart.</span></span> <span data-ttu-id="a7a76-125">**[奥行]** ボックスの値では、投影を表示する際に使用されるゆがみの比率を定義します。</span><span class="sxs-lookup"><span data-stu-id="a7a76-125">The **Perspective** value defines the percentage of distortion that will be used when displaying the projection.</span></span> <span data-ttu-id="a7a76-126">この種類の投影では、グラフの比率は維持されますが、グラフはゆがんで見えるため、奥行の度合いを低くして使用する方が効果的です。</span><span class="sxs-lookup"><span data-stu-id="a7a76-126">This type of projection maintains the proportions of your chart, but the chart's appearance becomes distorted, so it is most effective to use a lower degree of perspective.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7a76-127">斜投影と透視投影は異なる種類の投影なので、同じグラフで併用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7a76-127">The oblique and perspective projections are separate types of projections, so they cannot be used together on the same chart.</span></span>  
  
### <a name="clustering-data"></a><span data-ttu-id="a7a76-128">データのクラスター化</span><span class="sxs-lookup"><span data-stu-id="a7a76-128">Clustering Data</span></span>  
 <span data-ttu-id="a7a76-129">2D グラフでは、複数の系列のデータが並んで表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-129">In 2D charts, multiple series of data appear side-by-side.</span></span> <span data-ttu-id="a7a76-130">クラスター化を行うと、各系列が 3D グラフの個別の行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-130">Clustering shows individual series in separate rows on a 3D chart.</span></span> <span data-ttu-id="a7a76-131">たとえば、3 つの系列のデータ ポイントを含むグラフがある場合、クラスター化により、3 つの系列それぞれが z 軸に沿って個別の行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-131">For example, if you have a chart that contains three series of data points, clustering will display each of the three series on a separate row along the z-axis.</span></span> <span data-ttu-id="a7a76-132">既定では、3D で表示されるグラフの種類はすべてクラスター化されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-132">By default, all chart types shown in 3D are clustered.</span></span>  
  
 <span data-ttu-id="a7a76-133">横棒グラフと縦棒グラフでは、クラスター化を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-133">Clustering can be disabled for bar and column charts.</span></span> <span data-ttu-id="a7a76-134">クラスター化を無効にすると、横棒グラフおよび縦棒グラフの複数の系列が 1 行に並んで表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-134">When clustering is disabled, multiple bar and column series are displayed side-by-side in one row.</span></span>  
  
## <a name="shape-based-three-dimensional-charts"></a><span data-ttu-id="a7a76-135">図形ベースの 3 次元グラフ</span><span class="sxs-lookup"><span data-stu-id="a7a76-135">Shape-Based Three-Dimensional Charts</span></span>  
 <span data-ttu-id="a7a76-136">図形ベースのグラフ (円グラフ、ドーナツ グラフ、じょうごグラフ、ピラミッド グラフ) で使用できる 3 次元効果は、座標ベースのグラフよりも少なくなります。</span><span class="sxs-lookup"><span data-stu-id="a7a76-136">Shape-based chart types (Pie, Doughnut, Funnel, Pyramid) have fewer three-dimensional effects available.</span></span> <span data-ttu-id="a7a76-137">図形ベースのグラフを使用している場合、変更できるのは回転と傾斜の値のみです。</span><span class="sxs-lookup"><span data-stu-id="a7a76-137">When working with shape-based chart types, you can change the rotation and inclination values only.</span></span>  
  
## <a name="rotations"></a><span data-ttu-id="a7a76-138">回転</span><span class="sxs-lookup"><span data-stu-id="a7a76-138">Rotations</span></span>  
 <span data-ttu-id="a7a76-139">グラフは、-90 ～ 90°の範囲で水平方向と垂直方向に回転できます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-139">Charts can be rotated horizontally and vertically from -90 to 90 degrees.</span></span> <span data-ttu-id="a7a76-140">水平方向の角度に正の値を指定すると、グラフは x 軸を中心に反時計回りに回転します。一方、垂直方向の角度に正の値を指定すると、グラフは y 軸を中心に時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="a7a76-140">A positive horizontal angle will rotate the chart counter-clockwise around the x-axis, while a positive vertical angle will rotate the chart clockwise around the y-axis.</span></span>  
  
## <a name="highlighting-3d-effects"></a><span data-ttu-id="a7a76-141">3D 効果の強調表示</span><span class="sxs-lookup"><span data-stu-id="a7a76-141">Highlighting 3D Effects</span></span>  
 <span data-ttu-id="a7a76-142">強調表示のスタイルは、 **Shading** プロパティを使用して 3D グラフに追加することができます。このプロパティは、グラフ領域を選択すると、プロパティ ペインの [Area3DStyle] の下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-142">You can add highlighting styles to a 3D chart via the **Shading** property, which appears under Area3DStyle in the Properties pane when the chart area is selected.</span></span> <span data-ttu-id="a7a76-143">単純な光源のスタイルでは、グラフ領域の要素に同じ色合いが適用されます。</span><span class="sxs-lookup"><span data-stu-id="a7a76-143">A simple lighting style applies the same hue to the chart area elements.</span></span> <span data-ttu-id="a7a76-144">写実的なスタイルでは、指定された光源の角度に応じて、グラフ領域の要素の色合いが変わります。</span><span class="sxs-lookup"><span data-stu-id="a7a76-144">A realistic style changes the hues of the chart area elements depending on a specified lighting angle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a76-145">参照</span><span class="sxs-lookup"><span data-stu-id="a7a76-145">See Also</span></span>  
 <span data-ttu-id="a7a76-146">[グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a7a76-146">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a7a76-147">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a7a76-147">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a7a76-148">グラフへの 3D 効果の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a7a76-148">Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-3d-effects-report-builder.md)  
  
  
