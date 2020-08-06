---
title: マップまたはマップ レイヤーの追加、変更、または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10526"
- sql12.rtp.rptdesigner.maptilelayerproperties.general.f1
- "10529"
- "10525"
- "10535"
- sql12.rtp.rptdesigner.mappolygonlayerproperties.general.f1
- sql12.rtp.rptdesigner.shared.layervisibility.f1
- sql12.rtp.rptdesigner.mappointlayerproperties.general.f1
- sql12.rtp.rptdesigner.shared.layerfilters.f1
- "10524"
- sql12.rtp.rptdesigner.maplayerproperties.general.f1
- sql12.rtp.rptdesigner.maplinelayerproperties.general.f1
- "10532"
- "10528"
- "10527"
- sql12.rtp.rptdesigner.maplayerproperties.analyticaldata.f1
ms.assetid: 6e89815e-187e-45bf-bf63-3d5c4a246360
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4e9fd178d36ee3322c0bd94dd44d621439139b71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640729"
---
# <a name="add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs"></a><span data-ttu-id="2cb09-102">マップまたはマップ レイヤーの追加、変更、または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2cb09-102">Add, Change, or Delete a Map or Map Layer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2cb09-103">マップは、レイヤーのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="2cb09-103">A map is a collection of layers.</span></span> <span data-ttu-id="2cb09-104">マップをレポートに追加する場合は、先にレイヤーを定義します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-104">When you add a map to a report, you define the first layer.</span></span> <span data-ttu-id="2cb09-105">追加のレイヤーを作成するには、マップ レイヤー ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-105">You can create additional layers by using the map layer wizard.</span></span>  
  
 <span data-ttu-id="2cb09-106">レイヤーの追加/削除、またはレイヤーのオプションを変更する一番簡単な方法は、マップ レイヤー ウィザードを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="2cb09-106">The easiest way to add, remove, or change options for a layer is to use the map layer wizard.</span></span> <span data-ttu-id="2cb09-107">マップ ペインから手動でオプションを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-107">You can also change options manually from the Map pane.</span></span> <span data-ttu-id="2cb09-108">**マップ** ペインを表示するには、レポート デザイン画面のマップ内をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-108">To display the **Map** pane, click in the map on the report design surface.</span></span> <span data-ttu-id="2cb09-109">次の図に、このペインの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-109">The following figure displays the parts of the pane:</span></span>  
  
 <span data-ttu-id="2cb09-110">![rsMapLayerZone](../media/rsmaplayerzone.gif "rsMapLayerZone")</span><span class="sxs-lookup"><span data-stu-id="2cb09-110">![rsMapLayerZone](../media/rsmaplayerzone.gif "rsMapLayerZone")</span></span>  
  
 <span data-ttu-id="2cb09-111">マップ レイヤーは、マップ ペインに表示されるとおりに、背面から前面の順に描画されます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-111">Map layers are drawn from bottom to top in the order that they appear in the Map pane.</span></span> <span data-ttu-id="2cb09-112">上の図では、タイル レイヤーが最初に描画され、多角形レイヤーが最後に描画されます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-112">In the previous figure, the tile layer is drawn first and the polygon layer is drawn last.</span></span> <span data-ttu-id="2cb09-113">先に描画されたレイヤー上のマップ要素は、後から描画されるレイヤーによって隠されてしまう場合があります。</span><span class="sxs-lookup"><span data-stu-id="2cb09-113">Layers that are drawn later might hide map elements on layers that are drawn earlier.</span></span> <span data-ttu-id="2cb09-114">マップ ペインのツール バーにある方向キーを使用すると、レイヤーの順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-114">You can change the order of layers by using the arrow keys on the Map pane toolbar.</span></span> <span data-ttu-id="2cb09-115">レイヤーの表示/非表示を切り替えるには、表示アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-115">To show or hide layers, toggle the visibility icon.</span></span> <span data-ttu-id="2cb09-116">レイヤーの透明度を変更するには `Visibility` 、[**レイヤーデータ**のプロパティ] ダイアログボックスのページを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-116">You can change the transparency of a layer on the `Visibility` page of the **Layer Data** properties dialog box.</span></span>  
  
 <span data-ttu-id="2cb09-117">次の表では、 **マップ** ペインのツール バー アイコンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-117">The following table displays the toolbar icons for the **Map** pane.</span></span>  
  
|<span data-ttu-id="2cb09-118">Symbol</span><span class="sxs-lookup"><span data-stu-id="2cb09-118">Symbol</span></span>|<span data-ttu-id="2cb09-119">説明</span><span class="sxs-lookup"><span data-stu-id="2cb09-119">Description</span></span>|<span data-ttu-id="2cb09-120">使用する場合</span><span class="sxs-lookup"><span data-stu-id="2cb09-120">When to use</span></span>|  
|------------|-----------------|-----------------|  
|<span data-ttu-id="2cb09-121">![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")</span><span class="sxs-lookup"><span data-stu-id="2cb09-121">![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")</span></span>|<span data-ttu-id="2cb09-122">マップ レイヤー ウィザード</span><span class="sxs-lookup"><span data-stu-id="2cb09-122">Map Layer Wizard</span></span>|<span data-ttu-id="2cb09-123">ウィザードを使用してレイヤーを追加するには、 **[レイヤーの新規作成ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-123">To add a layer by using a wizard, click **New layer wizard**.</span></span>|  
|<span data-ttu-id="2cb09-124">![rs_IconMapAddLayer](../../tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")</span><span class="sxs-lookup"><span data-stu-id="2cb09-124">![rs_IconMapAddLayer](../../tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")</span></span>|<span data-ttu-id="2cb09-125">レイヤーの追加</span><span class="sxs-lookup"><span data-stu-id="2cb09-125">Add Layer</span></span>|<span data-ttu-id="2cb09-126">レイヤーを手動で追加するには、 **[レイヤーの追加]** をクリックし、追加するマップ レイヤーの種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-126">To manually add a layer, click **Add Layer**, and then click the type of map layer to add.</span></span>|  
|<span data-ttu-id="2cb09-127">![rs_IconMapPolygonLayer](../media/rs-iconmappolygonlayer.gif "rs_IconMapPolygonLayer")</span><span class="sxs-lookup"><span data-stu-id="2cb09-127">![rs_IconMapPolygonLayer](../media/rs-iconmappolygonlayer.gif "rs_IconMapPolygonLayer")</span></span>|<span data-ttu-id="2cb09-128">多角形レイヤー</span><span class="sxs-lookup"><span data-stu-id="2cb09-128">Polygon Layer</span></span>|<span data-ttu-id="2cb09-129">多角形座標のセットに基づく領域または形状を表示するマップ レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-129">Add a map layer that displays areas or shapes that are based sets of polygon coordinates.</span></span>|  
|<span data-ttu-id="2cb09-130">![rs_IconMapLineLayer](../media/rs-iconmaplinelayer.gif "rs_IconMapLineLayer")</span><span class="sxs-lookup"><span data-stu-id="2cb09-130">![rs_IconMapLineLayer](../media/rs-iconmaplinelayer.gif "rs_IconMapLineLayer")</span></span>|<span data-ttu-id="2cb09-131">線レイヤー</span><span class="sxs-lookup"><span data-stu-id="2cb09-131">Line Layer</span></span>|<span data-ttu-id="2cb09-132">線座標のセットに基づくパスまたはルートを表示するマップ レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-132">Add a map layer that displays paths or routes that are based on sets of line coordinates.</span></span>|  
|<span data-ttu-id="2cb09-133">![rs_IconMapPointLayer](../media/rs-iconmappointlayer.gif "rs_IconMapPointLayer")</span><span class="sxs-lookup"><span data-stu-id="2cb09-133">![rs_IconMapPointLayer](../media/rs-iconmappointlayer.gif "rs_IconMapPointLayer")</span></span>|<span data-ttu-id="2cb09-134">ポイント レイヤー</span><span class="sxs-lookup"><span data-stu-id="2cb09-134">Point Layer</span></span>|<span data-ttu-id="2cb09-135">ポイント座標のセットに基づく場所を表示するマップ レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-135">Add a map layer that displays locations that are based on sets of point coordinates.</span></span>|  
|<span data-ttu-id="2cb09-136">![rs_IconMapTileLayer](../media/rs-iconmaptilelayer.gif "rs_IconMapTileLayer")</span><span class="sxs-lookup"><span data-stu-id="2cb09-136">![rs_IconMapTileLayer](../media/rs-iconmaptilelayer.gif "rs_IconMapTileLayer")</span></span>|<span data-ttu-id="2cb09-137">タイル レイヤー</span><span class="sxs-lookup"><span data-stu-id="2cb09-137">Tile Layer</span></span>|<span data-ttu-id="2cb09-138">ビューポートによって定義された現在のマップ ビュー領域に対応する Bing のマップ タイルを表示するマップ レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-138">Add a map layer that displays Bing Map tiles that correspond to the current map view area that is defined by the viewport.</span></span>|  
  
 <span data-ttu-id="2cb09-139">マップ ペインの一番下にはマップ ビュー領域があります。</span><span class="sxs-lookup"><span data-stu-id="2cb09-139">At the bottom of the Map pane is the Map view area.</span></span> <span data-ttu-id="2cb09-140">マップの中心またはズーム オプションを変更するには、方向キーを使用してビューの中心を調整し、スライダーを使用してズーム レベルを調整します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-140">To change the center or zoom options for the map, use the arrow keys to adjust the view center and the slider to adjust the zoom level.</span></span>  
  
 <span data-ttu-id="2cb09-141">レイヤーの詳細については、「 [マップ (レポート ビルダーおよび SSRS)](maps-report-builder-and-ssrs.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-141">For more information about layers, see [Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="to-add-a-layer-from-the-map-layer-wizard"></a><a name="AddLayer"></a> <span data-ttu-id="2cb09-142">マップ レイヤー ウィザードを使用してレイヤーを追加するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-142">To add a layer from the map layer wizard</span></span>  
  
-   <span data-ttu-id="2cb09-143">リボンで **[挿入]** メニューの **[マップ]** をクリックしてから、 **[マップ] Wizard.** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-143">From the Ribbon, on the **Insert** menu, click **Map**, and then click **Map Wizard.**</span></span> <span data-ttu-id="2cb09-144">このウィザードを使用すると、既存のマップにレイヤーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-144">The wizard enables you to add a layer to the existing map.</span></span> <span data-ttu-id="2cb09-145">マップ ウィザードとマップ レイヤー ウィザードに含まれるページはほとんど同じです。</span><span class="sxs-lookup"><span data-stu-id="2cb09-145">Most wizard pages are identical between the map wizard and the map layer wizard.</span></span>  
  
     <span data-ttu-id="2cb09-146">詳細については、「 [マップ ウィザードおよびマップ レイヤー ウィザードのページ &#40;レポート ビルダーおよび SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb09-146">For more information, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-change-options-for-a-layer-by-using-the-map-layer-wizard"></a><a name="ChangeLayer"></a> <span data-ttu-id="2cb09-147">マップ レイヤー ウィザードを使用してレイヤーのオプションを変更するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-147">To change options for a layer by using the map layer wizard</span></span>  
  
-   <span data-ttu-id="2cb09-148">マップ レイヤー ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-148">Run the map layer wizard.</span></span> <span data-ttu-id="2cb09-149">このウィザードを使用すると、マップ レイヤー ウィザードを使用して作成したレイヤーのオプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-149">This wizard enables you to change options for a layer that you created by using the map layer wizard.</span></span> <span data-ttu-id="2cb09-150">マップ ペインでレイヤーを右クリックし、ツール バーの [レイヤー ウィザード] ボタンをクリックします (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard"))。</span><span class="sxs-lookup"><span data-stu-id="2cb09-150">In the Map pane, right-click the layer, and on the toolbar, click the layer wizard button (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")).</span></span>  
  
     <span data-ttu-id="2cb09-151">詳細については、「 [マップ ウィザードおよびマップ レイヤー ウィザードのページ &#40;レポート ビルダーおよび SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb09-151">For more information, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-add-a-point-line-or-polygon-layer-from-the-map-pane-toolbar"></a><a name="AddVectorLayer"></a> <span data-ttu-id="2cb09-152">マップ ペインのツール バーを使用してポイント レイヤー、線レイヤー、または多角形レイヤーを追加するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-152">To add a point, line, or polygon layer from the Map pane toolbar</span></span>  
  
1.  <span data-ttu-id="2cb09-153">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-153">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-154">ツール バーの **[レイヤーの追加]** をクリックし、ドロップダウン リストで、追加するレイヤーの種類( **[ポイント]** 、 **[線]** 、または **[多角形]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-154">On the toolbar, click the **Add Layer** button, and from the drop-down list, click the type of layer that you want to add: **Point**, **Line**, or **Polygon**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2cb09-155">マップ レイヤーを追加してから手動で構成することもできますが、新規レイヤーの追加にはマップ レイヤー ウィザードを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-155">Although you can add a map layer and configure it manually, we recommend that you use the map layer wizard to add new layers.</span></span> <span data-ttu-id="2cb09-156">マップ ペインのツール バーからこのウィザードを起動するには、[レイヤー ウィザード] ボタンをクリックします (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard"))。</span><span class="sxs-lookup"><span data-stu-id="2cb09-156">To launch the wizard from the Map pane toolbar, click the layer wizard button (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")).</span></span>  
  
3.  <span data-ttu-id="2cb09-157">レイヤーを右クリックし、 **[レイヤー データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-157">Right-click the layer, and then click **Layer Data**.</span></span>  
  
4.  <span data-ttu-id="2cb09-158">**[空間データのソース]** で、空間データのソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-158">In **Use spatial data from**, select the source of spatial data.</span></span> <span data-ttu-id="2cb09-159">オプションは、選択した内容によって異なります。</span><span class="sxs-lookup"><span data-stu-id="2cb09-159">Options vary based on your selection.</span></span>  
  
     <span data-ttu-id="2cb09-160">レポートの分析データをこのレイヤー上に視覚化するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2cb09-160">If you want to visualize analytical from your report on this layer, do the following:</span></span>  
  
    1.  <span data-ttu-id="2cb09-161">**[分析データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-161">Click **Analytical data**.</span></span>  
  
    2.  <span data-ttu-id="2cb09-162">**[分析データセット]** で、分析データと空間データの間にリレーションシップを構築するための分析データと対応フィールドを含んでいるデータセットの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-162">In **Analytical dataset**, click the name of the dataset that contains analytical data and the match fields to build a relationship between analytical and spatial data.</span></span>  
  
    3.  <span data-ttu-id="2cb09-163">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-163">Click **Add**.</span></span>  
  
    4.  <span data-ttu-id="2cb09-164">空間データセットの対応フィールドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-164">Type the name of the match field from the spatial dataset.</span></span>  
  
    5.  <span data-ttu-id="2cb09-165">分析データセットの対応フィールドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-165">Type the name of the match field from the analytical dataset.</span></span>  
  
     <span data-ttu-id="2cb09-166">空間データと分析データをリンクする方法の詳細については、「[マップまたはマップ レイヤーのデータと表示のカスタマイズ (レポート ビルダーおよび SSRS)](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb09-166">For more information about linking spatial and analytical data, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-filter-analytical-data-for-the-layer"></a><a name="FilterAnalyticalData"></a> <span data-ttu-id="2cb09-167">レイヤーの分析データをフィルター処理するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-167">To filter analytical data for the layer</span></span>  
  
1.  <span data-ttu-id="2cb09-168">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-168">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-169">マップ ペインでレイヤーを右クリックして、  **[レイヤー データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-169">Right-click the layer in the Map pane, and then click  **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="2cb09-170">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-170">Click **Filters**.</span></span>  
  
4.  <span data-ttu-id="2cb09-171">マップ表示で使用される分析データを制限するフィルター式を定義します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-171">Define a filter equation to limit the analytical data that is used in the map display.</span></span> <span data-ttu-id="2cb09-172">詳細については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb09-172">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-control-point-properties-for-a-point-layer-or-for-polygon-center-points"></a><a name="PointProperties"></a> <span data-ttu-id="2cb09-173">ポイント レイヤーまたは多角形の中心点のポイント プロパティを制御するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-173">To control point properties for a point layer or for polygon center points</span></span>  
  
1.  <span data-ttu-id="2cb09-174">**[マップ ポイントのプロパティ]** ダイアログ ボックスの **[全般]** を選択すると、次のマップ要素のラベル、ツールヒント、およびマーカーの種類に関するオプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-174">Select **General** on the **Map Point Properties** dialog box to change label, tooltip, and marker type options for the following map elements:</span></span>  
  
    -   <span data-ttu-id="2cb09-175">ポイント レイヤー上のすべての動的ポイントまたは埋め込みポイント。</span><span class="sxs-lookup"><span data-stu-id="2cb09-175">All dynamic or embedded points on a point layer.</span></span> <span data-ttu-id="2cb09-176">ポイントの色ルール、サイズ ルール、およびマーカーの種類ルールは、これらのオプションをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-176">Color rules, size rules, and marker type rules for points override these options.</span></span> <span data-ttu-id="2cb09-177">特定の埋め込みポイントのオプションをオーバーライドするには、「 [[マーカー] ([マップの埋め込みポイントのプロパティ] ダイアログ ボックス)](../map-embedded-point-properties-dialog-box-marker.md) 」ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-177">To override options for a specific embedded point, use the [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) page.</span></span>  
  
    -   <span data-ttu-id="2cb09-178">多角形レイヤー上のすべての動的多角形または埋め込み多角形の中心点。</span><span class="sxs-lookup"><span data-stu-id="2cb09-178">The center point for all dynamic or embedded polygons on a polygon layer.</span></span> <span data-ttu-id="2cb09-179">中心点の色ルール、サイズ ルール、およびマーカーの種類ルールは、これらのオプションをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-179">Color rules, size rules, and marker type rules for center points override these options.</span></span> <span data-ttu-id="2cb09-180">特定の中心点のオプションをオーバーライドするには、「 [[マーカー] ([マップの埋め込みポイントのプロパティ] ダイアログ ボックス)](../map-embedded-point-properties-dialog-box-marker.md) 」ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-180">To override options for a specific center point, use the [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) page.</span></span>  

##  <a name="to-specify-embedded-data-as-a-source-of-spatial-data"></a><a name="Embedded"></a> <span data-ttu-id="2cb09-181">空間データのソースとして埋め込みデータを指定するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-181">To specify embedded data as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="2cb09-182">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-182">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-183">レイヤーを右クリックし、 **[レイヤー データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-183">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="2cb09-184">**[空間データのソース]** で、 **[レポートに埋め込まれたデータ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-184">In **Use spatial data from**, select **Data embedded in report**.</span></span>  
  
4.  <span data-ttu-id="2cb09-185">マップ要素を既存のレポートから読み込む場合、または ESRI ファイルに基づいてマップ要素を作成する場合は、 **[参照]** をクリックし、ファイルをポイントして、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-185">To load map elements from an existing report or to create map elements based on an ESRI file, click **Browse**, point to the file, and then click **Open**.</span></span> <span data-ttu-id="2cb09-186">マップ要素が現在のレポート定義に埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-186">The map elements are embedded in this report definition.</span></span> <span data-ttu-id="2cb09-187">ポイントする空間データは、レイヤーの種類に対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cb09-187">The spatial data that you point to must match the layer type.</span></span> <span data-ttu-id="2cb09-188">たとえば、ポイント レイヤーの場合は、ポイント座標のセットを指定する空間データをポイントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cb09-188">For example, for a point layer, you must point to spatial data that specifies sets of point coordinates.</span></span>  
  
5.  <span data-ttu-id="2cb09-189">**[空間フィールド]** で、空間データが格納されているフィールドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-189">In **Spatial field**, specify the name of the field that contains spatial data.</span></span> <span data-ttu-id="2cb09-190">場合によっては、空間データのソースに対してこの名前を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cb09-190">You might need to determine this name from the source of spatial data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2cb09-191">フィールドの名前がわからず ESRI シェープファイルを参照した場合は、このオプションの代わりに **[ESRI シェープファイルにリンク]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-191">If you do not know the name of the field and you browsed to an ESRI Shapefile, use the **Link to ESRI shape file option** instead of this option.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-an-esri-shapefile-as-a-source-of-spatial-data"></a><a name="ESRI"></a> <span data-ttu-id="2cb09-192">空間データのソースとして ESRI シェープファイルを指定するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-192">To specify an ESRI Shapefile as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="2cb09-193">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-193">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-194">レイヤーを右クリックし、 **[レイヤー データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-194">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="2cb09-195">**[空間データのソース]** で、 **[ESRI シェープファイルにリンク]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-195">In **Use spatial data from**, select **Link to ESRI Shapefile**.</span></span>  
  
4.  <span data-ttu-id="2cb09-196">**[ファイル名]** に ESRI シェープファイルの場所を入力するか、 **[参照]** をクリックし、ESRI シェープファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-196">In **File name**, type the location of an ESRI Shapefile, or click **Browse** to select an ESRI Shapefile.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2cb09-197">シェープファイルがローカル コンピューター上に格納されている場合、空間データはレポート定義に埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-197">If the Shapefile is on your local computer, the spatial data is embedded in the report definition.</span></span> <span data-ttu-id="2cb09-198">レポートの処理時にデータが動的に取得されるようにするには、ESRI .shp ファイルとその .dbf サポート ファイルをレポート サーバーにアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cb09-198">To retrieve the data dynamically when the report is processed, you must upload the ESRI .shp file and its .dbf support file to the report server.</span></span> <span data-ttu-id="2cb09-199">詳細については、 [Reporting Services のドキュメント](https://go.microsoft.com/fwlink/?linkid=121312) (SQL Server オンライン ブック) の「ファイルまたはレポートをアップロードする方法 (レポート マネージャー)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb09-199">For more information, see " How to: Upload a File or Report (Report Manager)" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-a-report-dataset-field-as-a-source-of-spatial-data"></a><a name="DatasetField"></a> <span data-ttu-id="2cb09-200">空間データのソースとしてレポート データセット フィールドを指定するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-200">To specify a report dataset field as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="2cb09-201">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-201">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-202">レイヤーを右クリックし、 **[レイヤー データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-202">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="2cb09-203">**[空間データのソース]** で、 **[データセットの空間フィールド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-203">In **Use spatial data from**, select **Spatial field in a dataset**.</span></span>  
  
4.  <span data-ttu-id="2cb09-204">**[データセット名]** で、目的の空間データが格納されているレポート内のデータセットの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-204">In **Dataset name**, click the name of a dataset in the report that contains that spatial data that you want.</span></span>  
  
5.  <span data-ttu-id="2cb09-205">**[空間フィールド名]** で、空間データが格納されているデータセット内のフィールドの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-205">In **Spatial field name**, click the name of the field in the dataset that contains spatial data.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-add-a-tile-layer"></a><a name="TileLayer"></a> <span data-ttu-id="2cb09-206">タイル レイヤーを追加するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-206">To add a tile layer</span></span>  
  
1.  <span data-ttu-id="2cb09-207">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-207">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-208">ツール バーの **[レイヤーの追加]** ボタンをクリックし、ドロップダウン リストで **[タイル レイヤー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-208">On the toolbar, click the **Add Layer** button, and from the drop-down list, click **Tile Layer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2cb09-209">レポート内での Bing のマップ タイルの使用については、「 [追加使用条件](https://go.microsoft.com/fwlink/?LinkId=151371) 」および「 [プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=151372)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb09-209">For more information about the use of Bing map tiles in your report, see [Additional Terms of Use](https://go.microsoft.com/fwlink/?LinkId=151371) and [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=151372).</span></span>  
  
3.  <span data-ttu-id="2cb09-210">マップ ペイン内でタイル レイヤーを右クリックし、 **[タイルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-210">Right-click the tile layer in the Map pane, and then click **Tile Properties**.</span></span>  
  
4.  <span data-ttu-id="2cb09-211">**[タイルのオプション]** で、タイル スタイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-211">In **Tile options**, select a tile style.</span></span> <span data-ttu-id="2cb09-212">Bing のマップ タイルが使用可能である場合は、選択したスタイルでデザイン画面上のレイヤーが更新されます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-212">If the Bing map tiles are available, the layer on the design surface updates with the style that you select.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2cb09-213">マップまたはマップ レイヤー ウィザード内で多角形レイヤー、線レイヤー、またはポイント レイヤーを追加するときに、タイル レイヤーを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-213">A tile layer can also be added when you add a polygon, line, or point layer in the Map or Map Layer wizard.</span></span> <span data-ttu-id="2cb09-214">**[空間データとマップ ビューのオプションを選択]** ページで、 **[このマップ ビューに Bing Maps の背景を追加する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-214">On the **Choose spatial data and map view options** page, select the option **Add a Bing Maps background for this map view**.</span></span>  

##  <a name="to-change-the-drawing-order-of-a-layer"></a><a name="DrawingOrder"></a> <span data-ttu-id="2cb09-215">レイヤーの描画順を変更するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-215">To change the drawing order of a layer</span></span>  
  
1.  <span data-ttu-id="2cb09-216">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-216">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-217">マップ ペイン内のレイヤーをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-217">Click the layer in the Map pane to select it.</span></span>  
  
3.  <span data-ttu-id="2cb09-218">マップ ペインのツール バーの上矢印または下矢印をクリックし、各レイヤーの描画順を変更します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-218">On the Map pane toolbar, click the up or down arrow to change the drawing order of each layer.</span></span>  

##  <a name="to-change-the-transparency-of-a-polygon-line-or-point-layer"></a><a name="Transparency"></a> <span data-ttu-id="2cb09-219">多角形レイヤー、線レイヤー、またはポイント レイヤーの透明度を変更するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-219">To change the transparency of a polygon, line, or point layer</span></span>  
  
1.  <span data-ttu-id="2cb09-220">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-220">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-221">レイヤーを右クリックし、 **[レイヤー データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-221">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="2cb09-222">[`Visibility`] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-222">Click `Visibility`.</span></span>  
  
4.  <span data-ttu-id="2cb09-223">**[透明度オプション]** で、透明度を表す値 (たとえば、「 **40**」) を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-223">In **Transparency options**, type a value that represents the percentage transparency, for example, **40**.</span></span> <span data-ttu-id="2cb09-224">透明度が 0% の場合、レイヤーは不透明になります。</span><span class="sxs-lookup"><span data-stu-id="2cb09-224">Zero (0) % transparency means that the layer is opaque.</span></span> <span data-ttu-id="2cb09-225">透明度が 100% の場合、レポート内にレイヤーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="2cb09-225">100% transparency means that you will not see the layer in the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-change-the-transparency-of-a-tile-layer"></a><a name="TileTransparency"></a> <span data-ttu-id="2cb09-226">タイル レイヤーの透明度を変更するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-226">To change the transparency of a tile layer</span></span>  
  
1.  <span data-ttu-id="2cb09-227">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-227">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-228">レイヤーを右クリックし、 **[タイルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-228">Right-click the layer, and then click **Tile Properties**.</span></span>  
  
3.  <span data-ttu-id="2cb09-229">[`Visibility`] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-229">Click `Visibility`.</span></span>  
  
4.  <span data-ttu-id="2cb09-230">**[透明度オプション]** で、透明度を表す値 (たとえば、「 **40**」) を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-230">In **Transparency options**, type a value that represents the percentage transparency, for example, **40**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-a-secure-connection-for-a-tile-layer"></a><a name="Secure"></a> <span data-ttu-id="2cb09-231">タイル レイヤーにセキュリティで保護された接続を指定するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-231">To specify a secure connection for a tile layer</span></span>  
  
1.  <span data-ttu-id="2cb09-232">マップ ペインが表示されるまでマップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-232">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2cb09-233">マップ ペイン内のタイル レイヤーをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-233">In the Map pane, click the tile layer to select it.</span></span> <span data-ttu-id="2cb09-234">プロパティ ペインにタイル レイヤーのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-234">The Properties pane displays the tile layer properties.</span></span>  
  
3.  <span data-ttu-id="2cb09-235">プロパティ ペインで、UseSecureConnection を **True**に設定します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-235">In the Properties pane, set UseSecureConnection to **True**.</span></span>  
  
 <span data-ttu-id="2cb09-236">Bing Maps Web サービスの接続は、HTTP SSL (Secure Sockets Layer) サービスを使用してこのレイヤーの Bing マップ タイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-236">The connection for the Bing Maps Web service will use the HTTP SSL (Secure Sockets Layer) service to retrieve Bing map tiles for this layer.</span></span>  

##  <a name="to-specify-the-language-for-tile-labels"></a><a name="Language"></a> <span data-ttu-id="2cb09-237">タイル ラベルの言語を指定するには</span><span class="sxs-lookup"><span data-stu-id="2cb09-237">To specify the language for tile labels</span></span>  
  
1.  <span data-ttu-id="2cb09-238">既定では、ラベルを表示するタイル スタイルには、レポート ビルダー用に既定ロケールとして指定されている言語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-238">By default, for tile styles that display labels, the language is determined from the default locale for Report Builder.</span></span> <span data-ttu-id="2cb09-239">次の方法でタイル ラベルの言語設定をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-239">You can customize the language setting for tile labels in the following ways.</span></span>  
  
    -   <span data-ttu-id="2cb09-240">ビューポートの外でマップをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-240">Click the map outside the viewport to select the map.</span></span> <span data-ttu-id="2cb09-241">プロパティ ペインで、TileLanguage プロパティに対してドロップダウン リストからカルチャ値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-241">In the Properties pane, for the TileLanguage property, select a culture value from the drop-down list.</span></span>  
  
    -   <span data-ttu-id="2cb09-242">レポートの背景をクリックしてそのレポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-242">Click the report background to select the report.</span></span> <span data-ttu-id="2cb09-243">プロパティ ペインで、Language プロパティに対してドロップダウン リストからカルチャ値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-243">In the Properties pane, from for the Language property, select a culture value from the drop-down list.</span></span>  
  
     <span data-ttu-id="2cb09-244">タイル ラベルの言語設定の優先順位は、レポート プロパティ Language、レポート ビルダーの既定ロケール、マップ プロパティ TileLanguage の順です。</span><span class="sxs-lookup"><span data-stu-id="2cb09-244">The order of precedence for setting the tile label language is: report property Language, default locale for Report Builder, and map property TileLanguage.</span></span>  

##  <a name="to-conditionally-hide-a-layer-based-on-viewport-zoom-level"></a><a name="ConditionalHide"></a> <span data-ttu-id="2cb09-245">ビューポートのズーム レベルに基づいてレイヤーを条件付きで非表示にするには</span><span class="sxs-lookup"><span data-stu-id="2cb09-245">To conditionally hide a layer based on viewport zoom level</span></span>  
  
1.  <span data-ttu-id="2cb09-246">`Visibility`マップレイヤーの表示を制御するオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-246">Set `Visibility` options to control the display for a map layer.</span></span>  
  
    -   <span data-ttu-id="2cb09-247">マップ レイヤー ペインで、レイヤーを右クリックして選択し、[マップ レイヤー] ツール バーの [プロパティ] をクリックして **[マップ レイヤーのプロパティ]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-247">In the Map Layers pane, right-click a layer to select it, and on the Map Layers toolbar, click Properties to open **Map Layer Properties**.</span></span>  
  
    -   <span data-ttu-id="2cb09-248">[`Visibility`] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb09-248">Click `Visibility`.</span></span>  
  
    -   <span data-ttu-id="2cb09-249">[レイヤーの表示] で、 **[ズーム値を基に表示/非表示を切り替える]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-249">In Layer visibility, select **Show or hide based on zoom value**.</span></span>  
  
    -   <span data-ttu-id="2cb09-250">レイヤーを表示するときのズームの最小値と最大値を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-250">Enter minimum and maximum zoom values for when display the layer.</span></span>  
  
    -   <span data-ttu-id="2cb09-251">省略可能。</span><span class="sxs-lookup"><span data-stu-id="2cb09-251">Optional.</span></span> <span data-ttu-id="2cb09-252">透明度の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cb09-252">Enter a value for transparency.</span></span>  
  
     <span data-ttu-id="2cb09-253">条件付きでレイヤーを非表示にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2cb09-253">You can also conditionally hide the layer.</span></span> <span data-ttu-id="2cb09-254">詳細については、「[アイテムを非表示にする (レポート ビルダーおよび SSRS)](../report-builder/hide-an-item-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb09-254">For more information, see [Hide an Item &#40;Report Builder and SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="2cb09-255">参照</span><span class="sxs-lookup"><span data-stu-id="2cb09-255">See Also</span></span>  
 <span data-ttu-id="2cb09-256">[マップ &#40;レポート ビルダーおよび SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2cb09-256">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2cb09-257">レポートのトラブルシューティング: マップ レポート &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb09-257">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
