---
title: マップの凡例、カラースケール、および関連付けられているルールの変更 (レポートビルダーと SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.maprulesdistribution.f1
- "10512"
- "10539"
- "10533"
- sql12.rtp.rptdesigner.mappointlayerproperties.typerules.f1
- "10534"
- sql12.rtp.rptdesigner.maplegendproperties.general.f1
- sql12.rtp.rptdesigner.mapdistancescaleproperties.general.f1
- "10516"
- sql12.rtp.rptdesigner.mapcolorscaleproperties.labels.f1
- sql12.rtp.rptdesigner.maplegendtitleproperties.general.f1
- "10514"
- sql12.rtp.rptdesigner.shared.mapruleslegend.f1
- sql12.rtp.rptdesigner.mapcolorscaleproperties.general.f1
- sql12.rtp.rptdesigner.shared.embeddedlabels.f1
- "10513"
- sql12.rtp.rptdesigner.mappointlayerproperties.sizerules.f1
- sql12.rtp.rptdesigner.mapcolorscaletitleproperties.general.f1
- "10510"
- "10509"
- "10540"
- "10517"
ms.assetid: a1d691b2-c5ae-420f-af60-b7c54a7385a4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 17220c12e672ce49d3c5b1023f2a00db04e7613e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634261"
---
# <a name="change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs"></a><span data-ttu-id="4d9f5-102">マップの凡例、カラー スケール、および関連付けられているルールの変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4d9f5-102">Change Map Legends, Color Scale, and Associated Rules (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4d9f5-103">マップには、マップの凡例、カラー スケール、および距離スケールを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-103">A map can contain map legends, a color scale, and a distance scale.</span></span> <span data-ttu-id="4d9f5-104">これらのマップ要素は、マップに表示されているデータをユーザーが解釈する際に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-104">These parts of a map help users interpret the data visualization on the map.</span></span>  
  
 <span data-ttu-id="4d9f5-105">凡例には、次のマップ要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-105">Legends include the following parts of a map:</span></span>  
  
-   <span data-ttu-id="4d9f5-106">**マップの凡例** 分析データの解釈に役立つガイドを表示します。マップ レイヤー上のマップ要素の表示は、分析データによって変化します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-106">**Map legend** Displays a guide to help interpret the analytical data that varies the display of a map elements on a map layer.</span></span> <span data-ttu-id="4d9f5-107">マップには、複数の凡例を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-107">A map can have multiple legends.</span></span> <span data-ttu-id="4d9f5-108">マップ レイヤーごとに使用する凡例を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-108">For each map layer, you A specify which legend to use.</span></span> <span data-ttu-id="4d9f5-109">凡例では、複数のマップ レイヤーへのガイドを提供できます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-109">A legend can provide a guide to more than one map layer.</span></span>  
  
-   <span data-ttu-id="4d9f5-110">**カラー スケール** マップ上の色の解釈に役立つガイドを表示します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-110">**Color scale** Displays a guide to help interpret colors on the map.</span></span> <span data-ttu-id="4d9f5-111">マップには、1 つのカラー スケールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-111">A map has one color scale.</span></span> <span data-ttu-id="4d9f5-112">複数のレイヤーで、カラー スケールのデータを提供できます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-112">Multiple layers can provide the data for the color scale.</span></span>  
  
-   <span data-ttu-id="4d9f5-113">**距離スケール** マップのスケールの解釈に役立つガイドを表示します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-113">**Distance scale** Displays a guide to help interpret the scale of the map.</span></span> <span data-ttu-id="4d9f5-114">マップには、1 つの距離スケールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-114">A map has one distance scale.</span></span> <span data-ttu-id="4d9f5-115">距離スケールは、現在のマップ ビューポートのズーム値によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-115">The current map viewport zoom value determines the distance scale.</span></span>  
  
 <span data-ttu-id="4d9f5-116">![rs_MapElements](../media/rs-mapelements.gif "rs_MapElements")</span><span class="sxs-lookup"><span data-stu-id="4d9f5-116">![rs_MapElements](../media/rs-mapelements.gif "rs_MapElements")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a><a name="Viewport"></a> <span data-ttu-id="4d9f5-117">ビューポートを基準とする凡例の相対位置を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-117">To change the position of a legend relative to the viewport</span></span>  
  
#### <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a><span data-ttu-id="4d9f5-118">ビューポートを基準とする凡例の相対位置を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-118">To change the position of a legend relative to the viewport</span></span>  
  
1.  <span data-ttu-id="4d9f5-119">デザインビューで、凡例を右クリックし、[ _\<report item->_ **プロパティ**] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-119">In Design view, right-click the legend and open the _\<report item->_**Properties** page.</span></span>  
  
2.  <span data-ttu-id="4d9f5-120">**[位置]** で、ビューポートを基準とする凡例の相対的な表示位置をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-120">In **Position**, click the location that specifies where to display the legend relative to the viewport.</span></span>  
  
3.  <span data-ttu-id="4d9f5-121">ビューポートの外に凡例を表示するには、[ \*\* \<report item> ビューポートの外側に表示\*\*] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-121">To display the legend outside the viewport, select **Show \<report item> outside viewport**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d9f5-122">プレビューすると、凡例に関連したルールからの結果が存在する場合にのみ、マップの凡例およびカラー スケールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-122">In preview, map legends and the color scale appear only when there are results from the rules related to that legend.</span></span> <span data-ttu-id="4d9f5-123">表示するアイテムが存在しない場合、表示レポートに凡例は表示されません。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-123">If there are no items to display, the legend does not appear in the rendered report.</span></span>  
  
  
  
##  <a name="to-change-the-layout-of-a-map-legend"></a><a name="MapLegend"></a> <span data-ttu-id="4d9f5-124">マップの凡例のレイアウトを変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-124">To change the layout of a map legend</span></span>  
  
#### <a name="to-change-the-layout-of-a-map-legend"></a><span data-ttu-id="4d9f5-125">マップの凡例のレイアウトを変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-125">To change the layout of a map legend</span></span>  
  
1.  <span data-ttu-id="4d9f5-126">デザイン ビューで、凡例を右クリックし、 **[凡例のプロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-126">In Design view, right-click the legend and open the **Legend Properties** page.</span></span>  
  
2.  <span data-ttu-id="4d9f5-127">**[凡例のレイアウト]** で、凡例に使用するテーブル レイアウトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-127">In **Legend layout**, click the table layout that you want to use for the legend.</span></span> <span data-ttu-id="4d9f5-128">別のオプションをクリックすると、デザイン画面のレイアウトが変更されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-128">As you click different options, the layout on the design surface changes.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-show-or-hide-a-map-legend-title"></a><a name="MapLegendTitle"></a> <span data-ttu-id="4d9f5-129">マップの凡例のタイトルを表示または非表示にするには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-129">To show or hide a map legend title</span></span>  
  
#### <a name="to-show-or-hide-a-map-legend-title"></a><span data-ttu-id="4d9f5-130">マップの凡例のタイトルを表示または非表示にするには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-130">To show or hide a map legend title</span></span>  
  
-   <span data-ttu-id="4d9f5-131">デザイン画面でマップの凡例を右クリックし、 **[凡例のタイトルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-131">Right-click the map legend on the design surface, and then click **Show Legend Title**.</span></span>  
  
  
  
##  <a name="to-show-or-hide-a-color-scale-title"></a><a name="ColorScaleTitle"></a> <span data-ttu-id="4d9f5-132">カラー スケールのタイトルを表示または非表示にするには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-132">To show or hide a color scale title</span></span>  
  
#### <a name="to-show-or-hide-a-color-scale-title"></a><span data-ttu-id="4d9f5-133">カラー スケールのタイトルを表示または非表示にするには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-133">To show or hide a color scale title</span></span>  
  
-   <span data-ttu-id="4d9f5-134">デザイン画面でカラー スケールを右クリックし、 **[カラー スケールのタイトルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-134">Right-click the color scale on the design surface, and then click **Show Color Scale Title**.</span></span>  
  
  
  
##  <a name="to-move-items-out-of-the-first-legend"></a><a name="MoveItems"></a> <span data-ttu-id="4d9f5-135">最初の凡例からアイテムを移動するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-135">To move items out of the first legend</span></span>  
 <span data-ttu-id="4d9f5-136">追加の凡例を必要な数だけ作成し、各マップ レイヤーのルールを更新して、ルールの結果を表示する凡例を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-136">Create as many additional legends as you need and then update the rules for each map layer specify which legend to display the rule results in.</span></span>  
  
#### <a name="to-create-a-new-legend"></a><span data-ttu-id="4d9f5-137">新しい凡例を作成するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-137">To create a new legend</span></span>  
  
-   <span data-ttu-id="4d9f5-138">デザイン ビューで、マップ ビューポートの外部でマップを右クリックし、 **[凡例の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-138">In Design view, right-click the map outside the map viewport, and then click **Add Legend**.</span></span>  
  
     <span data-ttu-id="4d9f5-139">新しい凡例がマップに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-139">A new legend appears on the map.</span></span>  
  
#### <a name="to-display-rule-results-in-a-legend"></a><span data-ttu-id="4d9f5-140">ルールの結果を凡例に表示するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-140">To display rule results in a legend</span></span>  
  
1.  <span data-ttu-id="4d9f5-141">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-141">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-142">目的のデータが含まれているレイヤーを右クリックし、[色のルール] をクリックし _\<map element type\>_ **Color Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-142">Right-click the layer that has the data that you want and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-143">**[凡例]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-143">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="4d9f5-144">**[この凡例に表示]** ボックスの一覧で、ルールの結果を表示する凡例の名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-144">In the **Show in this legend** drop-down list, click the name of the legend to display the rule results in.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-a-template-style"></a><a name="TemplateStyle"></a> <span data-ttu-id="4d9f5-145">テンプレート スタイルに基づいてマップ要素の色を変えるには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-145">To vary map element colors based on a template style</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-a-template-style"></a><span data-ttu-id="4d9f5-146">テンプレート スタイルに基づいてマップ要素の色を変えるには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-146">To vary map element colors based on a template style</span></span>  
  
1.  <span data-ttu-id="4d9f5-147">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-147">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-148">目的のデータが含まれているレイヤーを右クリックし、[色のルール] をクリックし _\<map element type\>_ **Color Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-148">Right-click the layer that has the data that you want and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-149">**[テンプレート スタイルを適用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-149">Click **Apply template style**.</span></span>  
  
     <span data-ttu-id="4d9f5-150">テンプレート スタイルは、フォント、罫線のスタイル、およびカラー パレットを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-150">A template style specifies font, border style, and color palette.</span></span> <span data-ttu-id="4d9f5-151">個々のマップ要素には、それぞれ異なる色が、マップ ウィザードまたはマップ レイヤー ウィザードで指定されたテーマのカラー パレットから割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-151">Each map element is assigned a different color from the color palette for the theme that was specified in the Map Wizard or Map Layer Wizard.</span></span> <span data-ttu-id="4d9f5-152">関連付けられた分析データが存在しないレイヤーには常にこのオプションが適用されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-152">This is the only option that applies to layers that do not have associated analytical data.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-color-palette"></a><a name="ColorPalette"></a> <span data-ttu-id="4d9f5-153">カラー パレットに基づいてマップ要素の色を変えるには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-153">To vary map element colors based on color palette</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-color-palette"></a><span data-ttu-id="4d9f5-154">カラー パレットに基づいてマップ要素の色を変えるには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-154">To vary map element colors based on color palette</span></span>  
  
1.  <span data-ttu-id="4d9f5-155">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-155">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-156">目的のデータが含まれているレイヤーを右クリックし、[色のルール] をクリックし _\<map element type\>_ **Color Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-156">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-157">**[色パレットを使用してデータを表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-157">Click **Visualize data by using color palette**.</span></span>  
  
     <span data-ttu-id="4d9f5-158">このオプションでは、指定したカスタムのパレットまたは組み込みのパレットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-158">This option uses a built-in or custom palette that you specify.</span></span> <span data-ttu-id="4d9f5-159">マップ要素には、関連する分析データに基づき、それぞれ異なる色または色の濃淡がパレットから割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-159">Based on related analytical data, each map element is assigned a different color or shade of color from the palette.</span></span>  
  
4.  <span data-ttu-id="4d9f5-160">色によって視覚化する分析データが格納されているフィールドの名前を **[データ フィールド]** に入力します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-160">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="4d9f5-161">**[パレット]** のドロップダウン リストから、使用するパレットの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-161">In **Palette**, from the drop-down list, select the name of the palette to use.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-color-ranges"></a><a name="ColorRanges"></a> <span data-ttu-id="4d9f5-162">色の範囲に基づいてマップ要素の色を変えるには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-162">To vary map element colors based on color ranges</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-color-ranges"></a><span data-ttu-id="4d9f5-163">色の範囲に基づいてマップ要素の色を変えるには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-163">To vary map element colors based on color ranges</span></span>  
  
1.  <span data-ttu-id="4d9f5-164">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-164">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-165">目的のデータが含まれているレイヤーを右クリックし、[色のルール] をクリックし _\<map element type\>_ **Color Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-165">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-166">**[色の範囲を使用してデータを表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-166">Click **Visualize data by using color ranges**.</span></span>  
  
     <span data-ttu-id="4d9f5-167">このオプションを選択すると、このページで指定された開始色、中間色、および終了色と、 **[分布]** ページで指定したオプションとに基づき、関連する分析データがいくつかの範囲に分類されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-167">This option, combined with the start, middle, and end colors that you specify on this page and the options that you specify on the **Distribution** page, divide the related analytical data into ranges.</span></span> <span data-ttu-id="4d9f5-168">関連付けられているデータおよび該当する範囲に基づき、それぞれのマップ要素には適切な色がレポート プロセッサによって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-168">The report processor assigns the appropriate color to each map element based on the its associated data and the range that it falls into.</span></span>  
  
4.  <span data-ttu-id="4d9f5-169">色によって視覚化する分析データが格納されているフィールドの名前を **[データ フィールド]** に入力します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-169">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="4d9f5-170">範囲の下限に使用する色を **[開始色]** に指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-170">In **Start color**, specify the color to use for the lowest range.</span></span>  
  
6.  <span data-ttu-id="4d9f5-171">範囲の中間に使用する色を **[中間の色]** に指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-171">In **Middle color**, specify the color to use for the middle range.</span></span>  
  
7.  <span data-ttu-id="4d9f5-172">範囲の上限に使用する色を **[終了色]** に指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-172">In **End color**, specify the color to use for the highest range.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-custom-colors"></a><a name="CustomColors"></a> <span data-ttu-id="4d9f5-173">カスタム色に基づいてマップ要素の色を変えるには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-173">To vary map element colors based on custom colors</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-custom-colors"></a><span data-ttu-id="4d9f5-174">カスタム色に基づいてマップ要素の色を変えるには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-174">To vary map element colors based on custom colors</span></span>  
  
1.  <span data-ttu-id="4d9f5-175">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-175">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-176">目的のデータが含まれているレイヤーを右クリックし、[色のルール] をクリックし _\<map element type\>_ **Color Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-176">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-177">**[作成した色を使用してデータを表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-177">Click **Visualize data by using custom colors**.</span></span>  
  
     <span data-ttu-id="4d9f5-178">このオプションを選択した場合、指定した色の一覧が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-178">This option uses the list of colors that you specify.</span></span> <span data-ttu-id="4d9f5-179">マップ要素には、関連する分析データに基づき、一覧から色が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-179">Based on related analytical data, each map element is assigned a color from the list.</span></span> <span data-ttu-id="4d9f5-180">マップ要素が多く色が足りない場合は、どの色も割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-180">If there are more map elements than colors, no color is assigned.</span></span>  
  
4.  <span data-ttu-id="4d9f5-181">色によって視覚化する分析データが格納されているフィールドの名前を **[データ フィールド]** に入力します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-181">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="4d9f5-182">**[作成した色]** の **[追加]** をクリックして、個々のカスタム色を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-182">In **Custom colors**, click **Add** to specify each custom color.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-set-distribution-options-for-a-legend"></a><a name="DistributionOptions"></a> <span data-ttu-id="4d9f5-183">凡例の分布オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-183">To set distribution options for a legend</span></span>  
  
#### <a name="to-set-distribution-options-for-a-legend"></a><span data-ttu-id="4d9f5-184">凡例の分布オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-184">To set distribution options for a legend</span></span>  
  
1.  <span data-ttu-id="4d9f5-185">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-185">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-186">目的のデータが含まれているレイヤーを右クリックし、[色のルール] をクリックし _\<map element type\>_ **Color Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-186">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-187">[**使用してデータ**を表示する] オプションを選択し \<rule type\> ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-187">Select the **Visualize data by using** \<rule type\> option.</span></span> <span data-ttu-id="4d9f5-188">分布オプションを使用するには、レイヤーに関連付けられている分析データに基づき、 **[分布]** ページで範囲を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-188">To use distribution options, you must create ranges on the **Distribution** page based on analytical data that is associated with the layer.</span></span>  
  
4.  <span data-ttu-id="4d9f5-189">**[分布]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-189">Click **Distribution**.</span></span>  
  
5.  <span data-ttu-id="4d9f5-190">次のいずれかの分布タイプを選択します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-190">Select one of the following distribution types:</span></span>  
  
    -   <span data-ttu-id="4d9f5-191">**[等間隔]** 。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-191">**EqualInterval**.</span></span> <span data-ttu-id="4d9f5-192">データを一定の間隔に区分する範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-192">Specifies ranges that divide the data into equal range intervals.</span></span>  
  
    -   <span data-ttu-id="4d9f5-193">**[均等割り付け]** 。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-193">**EqualDistribution**.</span></span> <span data-ttu-id="4d9f5-194">個々のアイテム数が均等になるようにデータを区分する範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-194">Specifies ranges that divide that data so that each range has an equal number of items.</span></span>  
  
    -   <span data-ttu-id="4d9f5-195">**[最適]** 。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-195">**Optimal**.</span></span> <span data-ttu-id="4d9f5-196">釣り合いのとれた部分範囲を形成するように分布が自動的に調整されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-196">Specifies ranges that automatically adjust distribution to create balanced subranges.</span></span>  
  
    -   <span data-ttu-id="4d9f5-197">**カスタム**:</span><span class="sxs-lookup"><span data-stu-id="4d9f5-197">**Custom**.</span></span> <span data-ttu-id="4d9f5-198">範囲の数を独自に指定して、値の分布を制御します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-198">Specify your own number of ranges to control the distribution of values.</span></span>  
  
     <span data-ttu-id="4d9f5-199">分布のオプションの詳細については、「[ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-199">For more information about distribution options, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
6.  <span data-ttu-id="4d9f5-200">**[部分範囲の数]** に、使用する部分範囲の数を入力します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-200">In **Number of subranges**, type the number of subranges to use.</span></span> <span data-ttu-id="4d9f5-201">分布タイプが **[最適]** の場合は、部分範囲の数が自動的に計算されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-201">When the distribution type is **Optimal**, the number of subranges is automatically calculated.</span></span>  
  
7.  <span data-ttu-id="4d9f5-202">**[範囲の開始]** に範囲の最小値を入力します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-202">In **Range start**, type a minimum range value.</span></span> <span data-ttu-id="4d9f5-203">この値よりも小さい値はすべて、範囲の下限と同じと見なされます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-203">All values less than this number are the same as the range minimum.</span></span>  
  
8.  <span data-ttu-id="4d9f5-204">**[範囲の終了]** に範囲の最大値を入力します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-204">In **Range end**, type a maximum range value.</span></span> <span data-ttu-id="4d9f5-205">この値を超える値はすべて、範囲の上限と同じと見なされます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-205">All values larger than this number are the same as the range maximum.</span></span>  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-contents-of-a-rule-legend"></a><a name="RuleLegend"></a> <span data-ttu-id="4d9f5-206">ルールの凡例の内容を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-206">To change the contents of a rule legend</span></span>  
  
#### <a name="to-change-the-contents-of-a-color-size-width-or-marker-type-legend"></a><span data-ttu-id="4d9f5-207">色、サイズ、幅、またはマーカーの種類の凡例の内容を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-207">To change the contents of a color, size, width, or marker type legend</span></span>  
  
1.  <span data-ttu-id="4d9f5-208">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-208">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-209">目的のデータが含まれているレイヤーを右クリックし、[ルール] をクリックし _\<map element type\>_ **Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-209">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-210">を使用した**データの視覚化**が選択されていることを確認し \<*rule type*> ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-210">Verify that **Visualize data by using** \<*rule type*> is selected.</span></span>  
  
4.  <span data-ttu-id="4d9f5-211">**[データ フィールド]** で、レイヤー上に視覚化しようとしている分析データが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-211">In **Data field**, verify that the analytical data that you are visualizing on the layer is selected.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d9f5-212">ドロップダウン リストにフィールドが表示されない場合は、レイヤーを右クリックし、 **[レイヤー データ]** をクリックして [分析データ] ([マップ レイヤー データのプロパティ] ダイアログ ボックス) ページを開き、このレイヤーに対する分析データが指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-212">If no fields appear in the drop-down list, right-click the layer, and then click **Layer Data** to open the Map Layer Data Properties Dialog Box, Analytical Data page and verify that you have specified analytical data for this layer.</span></span>  
  
5.  <span data-ttu-id="4d9f5-213">**[凡例]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-213">Click **Legend**.</span></span>  
  
6.  <span data-ttu-id="4d9f5-214">**[この凡例に表示]** で、ルールの結果を表示するのに使用するマップの凡例を選択します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-214">In **Show in this legend**, select the map legend to use to display the rule results.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-contents-of-the-color-scale"></a><a name="ColorScale"></a> <span data-ttu-id="4d9f5-215">カラー スケールの内容を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-215">To change the contents of the color scale</span></span>  
  
#### <a name="to-change-the-contents-of-the-color-scale-or-a-color-legend"></a><span data-ttu-id="4d9f5-216">カラー スケールまたは色の凡例の内容を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-216">To change the contents of the color scale or a color legend</span></span>  
  
1.  <span data-ttu-id="4d9f5-217">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-217">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-218">目的のデータが含まれているレイヤーを右クリックし、[色のルール] をクリックし _\<map element type\>_ **Color Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-218">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-219">使用する色ルールを選択します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-219">Select the color rule option to use.</span></span> <span data-ttu-id="4d9f5-220">マップの凡例またはカラースケールにアイテムを表示するには、[オプション**を使用してデータを視覚化**する] のいずれかを選択する必要があり \<rule type> ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-220">To display items in a map legend or color scale, you must select one of the **Visualize data by using** \<rule type> options.</span></span>  
  
4.  <span data-ttu-id="4d9f5-221">**[データ フィールド]** で、レイヤー上に視覚化しようとしている分析データが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-221">In **Data field**, verify that the analytical data that you are visualizing on the layer is selected.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d9f5-222">ドロップダウン リストにフィールドが表示されない場合は、レイヤーを右クリックし、 **[レイヤー データ]** をクリックして [分析データ] ([マップ レイヤー データのプロパティ] ダイアログ ボックス) ページを開き、このレイヤーに対する分析データが指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-222">If no fields appear in the drop-down list, right-click the layer, and then click **Layer Data** to open the Map Layer Data Properties Dialog Box, Analytical Data page and verify that you have specified analytical data for this layer.</span></span>  
  
5.  <span data-ttu-id="4d9f5-223">**[凡例]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-223">Click **Legend**.</span></span>  
  
6.  <span data-ttu-id="4d9f5-224">ルールの結果をカラー スケールに表示するには、 **[カラー スケールのオプション]** で **[カラー スケールに表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-224">In **Color scale options**, select **Show in color scale** to display the rule results in the color scale.</span></span> <span data-ttu-id="4d9f5-225">このオプションは複数の色ルールに対して指定できます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-225">You can specify this option for more than one color rule.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-remove-all-items-from-a-legend"></a><a name="HideItems"></a> <span data-ttu-id="4d9f5-226">すべてのアイテムを凡例から削除するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-226">To remove all items from a legend</span></span>  
  
#### <a name="to-hide-items-based-on-a-rule"></a><span data-ttu-id="4d9f5-227">ルールに基づいてアイテムを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-227">To hide items based on a rule</span></span>  
  
1.  <span data-ttu-id="4d9f5-228">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-228">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-229">目的のデータが含まれているレイヤーを右クリックし、[ルール] をクリックし _\<map element type\>_ **Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-229">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-230">**[凡例]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-230">Click **Legend**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-format-of-content-in-a-legend"></a><a name="ChangeFormatItems"></a> <span data-ttu-id="4d9f5-231">凡例の内容の書式を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-231">To change the format of content in a legend</span></span>  
 <span data-ttu-id="4d9f5-232">マップの凡例に関連付けられているルールの凡例オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-232">Set legend options for the rule that is associated with the map legend.</span></span>  
  
#### <a name="to-change-the-format-of-content-in-a-legend"></a><span data-ttu-id="4d9f5-233">凡例の内容の書式を変更するには</span><span class="sxs-lookup"><span data-stu-id="4d9f5-233">To change the format of content in a legend</span></span>  
  
1.  <span data-ttu-id="4d9f5-234">デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-234">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="4d9f5-235">目的のデータが含まれているレイヤーを右クリックし、[ルール] をクリックし _\<map element type\>_ **Rule**ます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-235">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="4d9f5-236">**[凡例]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-236">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="4d9f5-237">**[凡例のテキスト]** には、凡例に表示するデータを指定するキーワードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-237">**Legend text** displays keywords that specify which data appears in the legend.</span></span> <span data-ttu-id="4d9f5-238">マップ キーワードとカスタム書式を使用すると、凡例のテキストの書式を制御できます。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-238">Use map keywords and custom formats to help control the format of legend text.</span></span> <span data-ttu-id="4d9f5-239">たとえば、 #FROMVALUE {C2} は小数点以下 2 桁の通貨書式を示します。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-239">For example, #FROMVALUE {C2} specifies a currency format with two decimal places.</span></span> <span data-ttu-id="4d9f5-240">詳細については、「 [ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d9f5-240">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="4d9f5-241">参照</span><span class="sxs-lookup"><span data-stu-id="4d9f5-241">See Also</span></span>  
 <span data-ttu-id="4d9f5-242">[マップ &#40;レポート ビルダーおよび SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4d9f5-242">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4d9f5-243">[マップまたはマップ レイヤーの追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4d9f5-243">[Add, Change, or Delete a Map or Map Layer &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4d9f5-244">[マップまたはマップ レイヤーのデータと表示のカスタマイズ &#40;レポート ビルダーおよび SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4d9f5-244">[Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4d9f5-245">[レポートのトラブルシューティング: マップ レポート (レポート ビルダーおよび SSRS)](troubleshoot-reports-map-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4d9f5-245">[Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;](troubleshoot-reports-map-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4d9f5-246">マップ ウィザードおよびマップ レイヤー ウィザードのページ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4d9f5-246">Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;</span></span>](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)  
  
  
