---
title: グラフへの 3D 効果の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4fcd90452e32b760bc446ac5d085ed00520a2f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644336"
---
# <a name="add-3d-effects-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="dc170-102">グラフへの 3D 効果の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="dc170-102">Add 3D Effects to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dc170-103">3 次元 (3D) 効果を使用すると、グラフに奥行を与え、グラフの視覚的な効果を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="dc170-103">Three-dimensional (3D) effects can be used to provide depth and add visual impact to your chart.</span></span> <span data-ttu-id="dc170-104">たとえば、分割円グラフの特定のスライスを強調する場合は、そのスライスが最初に目に留まるように、グラフのパースペクティブを回転および変更することができます。</span><span class="sxs-lookup"><span data-stu-id="dc170-104">For example, if you want to emphasize a particular slice of an exploded pie chart, you can rotate and change the perspective of the chart so that people notice that slice first.</span></span> <span data-ttu-id="dc170-105">グラフに 3D 効果を適用すると、グラデーションの色および陰影のスタイルはすべて無効になります。</span><span class="sxs-lookup"><span data-stu-id="dc170-105">When 3D effects are applied to your chart, all gradient colors and hatching styles are disabled.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a><span data-ttu-id="dc170-106">範囲グラフ、面グラフ、折れ線グラフ、散布図、または極座標グラフに 3D 効果を適用するには</span><span class="sxs-lookup"><span data-stu-id="dc170-106">To apply 3D effects to a Range, Area, Line, Scatter or Polar chart</span></span>  
  
1.  <span data-ttu-id="dc170-107">グラフ領域内の任意の場所を右クリックし、 **[3D 効果]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-107">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="dc170-108">**[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc170-108">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="dc170-109">**[3D オプション]** で、 **[3D の有効化]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="dc170-109">In **3D Options**, select the **Enable 3D** option.</span></span>  
  
3.  <span data-ttu-id="dc170-110">(省略可) **[3D オプション]** では、3D の角度とシーンのオプションに関連するさまざまなプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="dc170-110">(Optional) In **3D Options**, you can set a variety of properties relating to 3D angles and scene options.</span></span> <span data-ttu-id="dc170-111">これらのプロパティの詳細については、「 [グラフに対する 3D、傾斜、およびその他の効果 &#40;レポート ビルダーおよび SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-111">For more information about these properties, see [3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md).</span></span>  
  
4.  <span data-ttu-id="dc170-112">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-112">Click **OK**.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-funnel-chart"></a><span data-ttu-id="dc170-113">じょうごグラフに 3D 効果を適用するには</span><span class="sxs-lookup"><span data-stu-id="dc170-113">To apply 3D effects to a Funnel chart</span></span>  
  
1.  <span data-ttu-id="dc170-114">グラフ領域内の任意の場所を右クリックし、 **[3D 効果]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-114">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="dc170-115">**[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc170-115">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="dc170-116">**[3D オプション]** で、 **[3D の有効化]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="dc170-116">In **3D Options**, select the **Enable 3D** option.</span></span> <span data-ttu-id="dc170-117">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-117">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="dc170-118">(省略可) じょうごグラフの外観をカスタマイズするには、[プロパティ] ペインに移動し、じょうごグラフ固有のプロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="dc170-118">(Optional) To customize the funnel chart visual appearance, you can go to the Properties pane and change properties specific to the funnel chart.</span></span>  
  
    1.  <span data-ttu-id="dc170-119">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="dc170-119">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="dc170-120">デザイン画面で、じょうごグラフの任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-120">On the design surface, click anywhere on the funnel.</span></span> <span data-ttu-id="dc170-121">じょうごグラフの系列のプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc170-121">The properties for the series of the funnel chart are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="dc170-122">**[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="dc170-122">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
    4.  <span data-ttu-id="dc170-123">**[Funnel3DDrawingStyle]** プロパティでは、じょうごグラフを四角形と円形のどちらで表示するかを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc170-123">For the **Funnel3DDrawingStyle** property, select whether the funnel will be shown with as circular or square.</span></span>  
  
    5.  <span data-ttu-id="dc170-124">**[Funnel3DRotationAngle]** プロパティでは、-10 ～ 10 の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="dc170-124">For the **Funnel3DRotationAngle** property, set a value between -10 and 10.</span></span> <span data-ttu-id="dc170-125">これにより、3D じょうごグラフで表示する傾きの角度が決まります。</span><span class="sxs-lookup"><span data-stu-id="dc170-125">This will determine the degree of tilt that will be displayed on the 3D funnel chart.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-pie-chart"></a><span data-ttu-id="dc170-126">円グラフに 3D 効果を適用するには</span><span class="sxs-lookup"><span data-stu-id="dc170-126">To apply 3D effects to a Pie chart</span></span>  
  
1.  <span data-ttu-id="dc170-127">グラフ領域内の任意の場所を右クリックし、[3D 効果] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-127">Right-click anywhere inside the chart area and select 3D Effects.</span></span> <span data-ttu-id="dc170-128">**[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc170-128">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="dc170-129">**[3D オプション]** で、 **[3D の有効化]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="dc170-129">In **3D Options**, select the **Enable 3D** option.</span></span> <span data-ttu-id="dc170-130">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-130">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="dc170-131">(省略可) **[回転]** ボックスに、円グラフの左右反転を表す整数値を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc170-131">(Optional) In **Rotation**, type an integer value that represents the horizontal rotation of the pie chart.</span></span>  
  
4.  <span data-ttu-id="dc170-132">(省略可) **[傾斜]** ボックスに、円グラフの上下反転の傾斜を表す整数値を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc170-132">(Optional) In **Inclination**, type an integer value that represents the vertical tilt rotation of the pie chart.</span></span>  
  
5.  <span data-ttu-id="dc170-133">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-133">Click **OK**.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a><span data-ttu-id="dc170-134">横棒グラフまたは縦棒グラフに 3D 効果を適用するには</span><span class="sxs-lookup"><span data-stu-id="dc170-134">To apply 3D effects to a Bar or Column chart</span></span>  
  
1.  <span data-ttu-id="dc170-135">グラフ領域内の任意の場所を右クリックし、 **[3D 効果]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-135">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="dc170-136">**[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc170-136">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="dc170-137">**[3D の有効化]** オプションをオンにします。</span><span class="sxs-lookup"><span data-stu-id="dc170-137">Select the **Enable 3D** option.</span></span> <span data-ttu-id="dc170-138">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-138">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="dc170-139">(省略可) **[系列のクラスタリングを有効にする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="dc170-139">(Optional) Select the **Enable series clustering** option.</span></span> <span data-ttu-id="dc170-140">グラフに横棒グラフまたは縦棒グラフの系列が複数含まれている場合、このチェック ボックスをオンにすると系列がクラスター化されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc170-140">If your chart contains multiple bar or column chart series, this option will display the series as clustered.</span></span> <span data-ttu-id="dc170-141">既定では、横棒グラフまたは縦棒グラフの複数の系列は並んで表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc170-141">By default, multiple bar or column series are shown side-by-side.</span></span>  
  
4.  <span data-ttu-id="dc170-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-142">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="dc170-143">(省略可) 横棒グラフまたは縦棒グラフに円柱の効果を追加するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="dc170-143">(Optional) To add cylinder effects to a bar or column chart, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="dc170-144">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="dc170-144">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="dc170-145">デザイン画面で、系列内のいずれかの棒をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc170-145">On the design surface, click any of the bars in the series.</span></span> <span data-ttu-id="dc170-146">系列のプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc170-146">The properties for the series are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="dc170-147">**[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="dc170-147">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
    4.  <span data-ttu-id="dc170-148">**[DrawingStyle]** プロパティで、値に **[Cylinder]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc170-148">For the **DrawingStyle** property, specify the **Cylinder** value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc170-149">参照</span><span class="sxs-lookup"><span data-stu-id="dc170-149">See Also</span></span>  
 <span data-ttu-id="dc170-150">[グラフに対する 3D、傾斜、およびその他の効果 &#40;レポート ビルダーおよび SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="dc170-150">[3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span></span>  
 <span data-ttu-id="dc170-151">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc170-151">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dc170-152">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dc170-152">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
