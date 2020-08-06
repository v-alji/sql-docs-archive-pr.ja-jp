---
title: マップまたはマップ レイヤーのデータと表示のカスタマイズ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10521"
- sql12.rtp.rptdesigner.shared.shadowdv.f1
- "10515"
- "10512"
- "10520"
- "10523"
- sql12.rtp.rptdesigner.mapgroupproperties.variables.f1
- sql12.rtp.rptdesigner.mapgroupproperties.filter.f1
- sql12.rtp.rptdesigner.shared.number.f1
- sql12.rtp.rptdesigner.shared.font.f1
- sql12.rtp.rptdesigner.mapgroupproperties.general.f1
- "10507"
ms.assetid: fdd9b994-d138-4990-a291-279b0249eb72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05987cea7ebde9d3587ade3f567eeb8ccef5e8fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721206"
---
# <a name="customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs"></a><span data-ttu-id="2c60f-102">マップまたはマップ レイヤーのデータと表示のカスタマイズ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2c60f-102">Customize the Data and Display of a Map or Map Layer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2c60f-103">ウィザードを使用してマップまたはマップ レイヤーをレポートに追加した後、必要に応じてレポート内のマップの体裁を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-103">After you add a map or map layer to a report by using a wizard, you might want to change the way the map looks in the report.</span></span> <span data-ttu-id="2c60f-104">改善のヒントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-104">You can make improvements by considering the following ideas:</span></span>  
  
-   <span data-ttu-id="2c60f-105">マップ上のデータをユーザーにわかりやすく示すには、凡例やカラー スケールを追加し、ラベルやツールヒントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-105">To help your users understand how to interpret the data display on a map, you can add legends and a color scale, and add labels and tooltips.</span></span>  
  
-   <span data-ttu-id="2c60f-106">マップを読みやすくするには、中心およびズーム レベルを変更し、距離スケールを追加して、背景グリッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-106">To make the map easier to read, change the center and zoom level, add a distance scale, and display a background grid.</span></span>  
  
-   <span data-ttu-id="2c60f-107">レポートの実行時にマップの描画時間を制御するには、解像度を調整してマップ要素を単純化します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-107">To help control map drawing time when you run the report, you can adjust the resolution to simplify the map elements.</span></span>  
  
-   <span data-ttu-id="2c60f-108">マップ要素をレポート定義に埋め込んで、個々の要素の表示方法を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-108">You can embed map elements in the report definition, and then change how individual elements appear.</span></span> <span data-ttu-id="2c60f-109">たとえば、主要オフィスの所在地を画鋲付きで表示し、それ以外のオフィス所在地は円で表示します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-109">For example, you can display the primary office location with a pushpin and other office locations with circles.</span></span>  
  
-   <span data-ttu-id="2c60f-110">独自のデータ グループ式を指定して、カスタマイズした地域を追加できます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-110">You can add customized regions by specifying your own data group expressions.</span></span>  
  
-   <span data-ttu-id="2c60f-111">ポイントが埋め込まれているマップ レイヤー上の特定のポイントを指定し、そこにカスタム ロケーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-111">You can add a custom location at a  point that you specify on a map layer that has embedded points.</span></span> <span data-ttu-id="2c60f-112">ポイント レイヤーでは、カスタム ポイントに対する値および表示プロパティを他のポイントとは別に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-112">You can set the value and display properties for custom points independently from other points on a point layer.</span></span>  
  
-   <span data-ttu-id="2c60f-113">より詳細な情報を提供するには、各レイヤーのマップ要素にリンクを追加し、ユーザーがそれをクリックすれば関連するレポートが開くようにします。</span><span class="sxs-lookup"><span data-stu-id="2c60f-113">To provide more detail, you can add links to map elements on each layer that a user can click to open related reports.</span></span>  
  
 <span data-ttu-id="2c60f-114">レポートの改善のヒントについては、「[レポートの計画 &#40;レポート ビルダー&#41;](planning-a-report-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c60f-114">For more ideas about improving a report, see [Planning a Report &#40;Report Builder&#41;](planning-a-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="2c60f-115">表示オプションは、レポートを表示したときのマップまたはマップの構成部分の表示方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-115">Display options affect the way a map or the parts of a map appear when you view the report.</span></span> <span data-ttu-id="2c60f-116">マップ上の領域の境界やフォントなど、マップの外観を制御するオプションもあれば、</span><span class="sxs-lookup"><span data-stu-id="2c60f-116">Some options control the appearance of the map, such as the borders and fonts or the area represented on the map.</span></span> <span data-ttu-id="2c60f-117">その他のオプションは、バブル サイズ、マーカーの種類、ラベル、ツールヒントなどの各レイヤーのコンテンツを制御します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-117">Other options control the content of each layer, such as bubble sizes, marker types, labels, or tooltips.</span></span>  
  
 <span data-ttu-id="2c60f-118">マップ レポート アイテムは、マップ自体、マップ ビューポート、一連のタイトル、一連の凡例 (凡例、カラー スケール、および距離スケール)、一連のレイヤー、各レイヤーの一連のマップ要素 (多角形、線、点) などの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-118">A map report item includes the following parts: the map itself, a map viewport, a set of titles, a set of legends (legend, color scale, and distance scale), a set of layers, a set of map elements on each layer (polygons or lines or points).</span></span> <span data-ttu-id="2c60f-119">マップを構成する各部分に関して、具体的にどのプロパティ ダイアログ ボックスで表示オプションを制御すればよいかという点については、以降のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c60f-119">Use the information in the following sections to understand which property dialog box controls the display options for different parts of a map.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="change-options-for-the-map"></a><a name="Map"></a> <span data-ttu-id="2c60f-120">マップのオプションを変更する</span><span class="sxs-lookup"><span data-stu-id="2c60f-120">Change Options for the Map</span></span>  
 <span data-ttu-id="2c60f-121">マップ レポート アイテムでは、次のような要素を制御できます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-121">On a map report item, you can control the following:</span></span>  
  
-   <span data-ttu-id="2c60f-122">複数のタイトルを追加する。</span><span class="sxs-lookup"><span data-stu-id="2c60f-122">Add multiple titles.</span></span>  
  
-   <span data-ttu-id="2c60f-123">複数の凡例を追加する。</span><span class="sxs-lookup"><span data-stu-id="2c60f-123">Add multiple legends.</span></span> <span data-ttu-id="2c60f-124">凡例の内容を変更するには、追加の凡例を作成した後、ルールを変更して、各ルールによって作成された凡例アイテムをどの凡例に表示するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-124">To change the contents of a legend, you need to create additional legends and then change the rules to specify in which legend to enter the legend items created by each rule.</span></span>  
  
-   <span data-ttu-id="2c60f-125">レイヤーを追加する。</span><span class="sxs-lookup"><span data-stu-id="2c60f-125">Add more layers.</span></span>  
  
-   <span data-ttu-id="2c60f-126">距離スケールまたはカラー スケールの表示/非表示を切り替える。</span><span class="sxs-lookup"><span data-stu-id="2c60f-126">Hide or show the distance scale or color scale.</span></span>  
  
-   <span data-ttu-id="2c60f-127">影を指定して奥行を表す。</span><span class="sxs-lookup"><span data-stu-id="2c60f-127">Provide the illusion of depth by specifying a shadow.</span></span>  
  
 <span data-ttu-id="2c60f-128">これらのオプションを変更するには、マップを右クリックして **[マップ]** をクリックし、オプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-128">To change these options, right-click the map, click **Map**, and change the options.</span></span>  
  
 
  
##  <a name="change-options-for-the-viewport"></a><a name="Viewport"></a> <span data-ttu-id="2c60f-129">ビューポートのオプションを変更する</span><span class="sxs-lookup"><span data-stu-id="2c60f-129">Change Options for the Viewport</span></span>  
 <span data-ttu-id="2c60f-130">レポートに表示されるマップの表示を変更するには、ビューポートのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-130">Use the viewport options to change the view of the map that appears in your report.</span></span>  
  
 <span data-ttu-id="2c60f-131">空間データのソースによって提供される領域データが、レポートに表示する範囲を超えることもあります。</span><span class="sxs-lookup"><span data-stu-id="2c60f-131">The source of spatial data might provide more area than you need to display in the report.</span></span> <span data-ttu-id="2c60f-132">ビューポートを使用すると、中心やズーム レベルを設定したり、マップの領域を切り抜いたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-132">You can use the viewport to set the center, the zoom level, and to crop the area for the map.</span></span>  
  
 <span data-ttu-id="2c60f-133">ビューポートに対して設定できるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2c60f-133">The following options can be set for the viewport:</span></span>  
  
-   <span data-ttu-id="2c60f-134">座標系を選択する。地理座標系の場合は投影法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-134">Choose the coordinate system and, for a geographic coordinate system, choose the projection.</span></span>  
  
-   <span data-ttu-id="2c60f-135">マップの中心を選択する。</span><span class="sxs-lookup"><span data-stu-id="2c60f-135">Choose the center for the map.</span></span>  
  
-   <span data-ttu-id="2c60f-136">マップのビューを切り抜く。</span><span class="sxs-lookup"><span data-stu-id="2c60f-136">Crop the view for the map.</span></span>  
  
-   <span data-ttu-id="2c60f-137">ズーム レベルを設定する。</span><span class="sxs-lookup"><span data-stu-id="2c60f-137">Set the zoom level.</span></span>  
  
-   <span data-ttu-id="2c60f-138">解像度と単純化。</span><span class="sxs-lookup"><span data-stu-id="2c60f-138">Resolution and simplification.</span></span> <span data-ttu-id="2c60f-139">線や多角形の描画にかかる時間を優先するか、アウトラインの詳細度を優先するかを検討します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-139">Choose a balance between drawing time and detailed outlines for lines and polygons.</span></span>  
  
 <span data-ttu-id="2c60f-140">これらのオプションを変更するには、マップ ビューポートを右クリックして、 [[マップ ビューポートのプロパティ] ダイアログ ボックスの [全般]](../map-viewport-properties-dialog-box-general.md) ページおよび関連ページを使用してください。</span><span class="sxs-lookup"><span data-stu-id="2c60f-140">To change these options, right-click the map viewport, use the [Map Viewport Properties Dialog Box, General](../map-viewport-properties-dialog-box-general.md) page and related pages.</span></span>  
  

  
##  <a name="change-options-for-the-legends"></a><a name="Legends"></a> <span data-ttu-id="2c60f-141">凡例のオプションを変更する</span><span class="sxs-lookup"><span data-stu-id="2c60f-141">Change Options for the Legends</span></span>  
 <span data-ttu-id="2c60f-142">凡例は、マップ上に表示されているデータをユーザーが解釈する際に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-142">Legends help users interpret the data on a map.</span></span>  
  
 <span data-ttu-id="2c60f-143">既定では、レイヤーに指定したすべてのルールがアイテムを最初の凡例に追加します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-143">By default, all rules that you specify for a layer add items to the first legend.</span></span> <span data-ttu-id="2c60f-144">また、すべての色ルールは、カラー スケールに値を表示します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-144">In addition, all color rules display values in the color scale.</span></span>  
  
-   <span data-ttu-id="2c60f-145">ビューポートを基準とする凡例の位置など、凡例の外観に関する表示オプションを変更するには、凡例そのもののオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-145">To change the display options for the appearance of the legend, including its position relative to the viewport, set options on the legend itself.</span></span>  
  
-   <span data-ttu-id="2c60f-146">凡例の内容やその形式を変更するには、レイヤーの対応するルールの凡例オプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-146">To change the contents or the format of contents for a legend, change the legend options for the corresponding rules for a layer.</span></span>  
  
 <span data-ttu-id="2c60f-147">詳細については、「 [マップの凡例、カラー スケール、および関連付けられているルールの変更 &#40;レポート ビルダーおよび SSRS&#41;](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c60f-147">For more information, see [Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="change-options-for-the-layer"></a><a name="Layer"></a> <span data-ttu-id="2c60f-148">レイヤーのオプションを変更する</span><span class="sxs-lookup"><span data-stu-id="2c60f-148">Change Options for the Layer</span></span>  
 <span data-ttu-id="2c60f-149">マップのレイヤーを表示するには、マップをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-149">To display the layers for a map, click the map to select it.</span></span> <span data-ttu-id="2c60f-150">マップ ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-150">The Map pane appears.</span></span> <span data-ttu-id="2c60f-151">レイヤーのオプションを変更するには、レイヤーを右クリックしてショートカット メニューを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-151">To change options for a layer, right-click the layer and use the shortcut menu.</span></span>  
  
 <span data-ttu-id="2c60f-152">レイヤーは、空間データ ソースから返される空間データに応じて、多角形レイヤー、線レイヤー、ポイント レイヤーの 3 種類に大別されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-152">A layer can be one of three types based on the spatial data that is returned by the spatial data source: a polygon layer, a line layer, or a point layer.</span></span>  
  
 <span data-ttu-id="2c60f-153">レイヤーに対して設定できるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2c60f-153">The following options can be set for the layer:</span></span>  
  
-   <span data-ttu-id="2c60f-154">関連付けられている分析データおよび対応フィールド。</span><span class="sxs-lookup"><span data-stu-id="2c60f-154">The associated analytical data and match fields.</span></span> <span data-ttu-id="2c60f-155">マップ ペインには、空間データのソースがレイヤー名の下に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-155">The source of the spatial data is listed on the Map pane under the name of the layer.</span></span> <span data-ttu-id="2c60f-156">ソースが埋め込まれている場合、レイヤーのマップ要素はレポート定義の一部分として存在します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-156">When the source is embedded, the map elements for the layer are part of the report definition.</span></span> <span data-ttu-id="2c60f-157">ソースが埋め込まれていない場合、空間データは実行時に取得され、レポートの処理時にレポート プロセッサによってレイヤーのマップ要素が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-157">If the source is not embedded, then the spatial data is retrieved at run time and the report processor creates the map elements for the layer when the report is processed.</span></span> <span data-ttu-id="2c60f-158">レイヤー上のデータに関するオプションを変更するには、[マップ レイヤー] ダイアログ ボックスの [分析データ] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-158">To change data options on the layer, use the Analytical Data page in the Map Layer dialog box.</span></span>  
  
-   <span data-ttu-id="2c60f-159">レイヤーの描画順序。</span><span class="sxs-lookup"><span data-stu-id="2c60f-159">Layer drawing order.</span></span> <span data-ttu-id="2c60f-160">マップ ペインに一覧表示されているレイヤーの順序は、レイヤーの描画順序とは逆になります。</span><span class="sxs-lookup"><span data-stu-id="2c60f-160">The order that you see the layers listed in the Map pane is the reverse drawing order for the layers.</span></span> <span data-ttu-id="2c60f-161">一覧の最後のレイヤーが最初に描画されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-161">The last layer in the list is drawn first.</span></span> <span data-ttu-id="2c60f-162">たとえば、ポイント レイヤーのポイントを多角形レイヤーの多角形よりも前面に表示させる場合、ポイント レイヤーを先頭にし、多角形レイヤーを 2 番目にします。</span><span class="sxs-lookup"><span data-stu-id="2c60f-162">For example, if you want the points on a point layer to appear on top of the polygons in the polygon layer, the point layer should be first and the polygon layer second.</span></span>  
  
-   <span data-ttu-id="2c60f-163">レイヤーの可視性 (透明度を含む)。</span><span class="sxs-lookup"><span data-stu-id="2c60f-163">Layer visibility, including transparency.</span></span> <span data-ttu-id="2c60f-164">レイヤーを通して別のレイヤーが透けて見えるようにするには、透明度を 0 より大きい値にします。</span><span class="sxs-lookup"><span data-stu-id="2c60f-164">To have one layer show through another layer, set the transparency to a value higher than 0.</span></span> <span data-ttu-id="2c60f-165">100% の値はレイヤーが非表示であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-165">A value of 100% means the layer is not visible.</span></span> <span data-ttu-id="2c60f-166">個々のレイヤーに対して何らかの作業を行う場合、マップ ペインの **[表示]** アイコンをクリックすることにより、各レイヤーを簡単に表示または非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-166">To work with an individual layer, you can easily show or hide each layer independently by using the **Visibility** icon in the Map pane.</span></span> <span data-ttu-id="2c60f-167">また、ズーム レベルのオプションを設定することにより、レイヤー上のマップ要素が表示または非表示になるタイミングを、ズーム レベルに基づいて指定することができます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-167">You can also set zoom level options to specify when to show or hide map elements on the layer based on the zoom level.</span></span>  
  
-   <span data-ttu-id="2c60f-168">現在のビューポートの中心およびズーム レベルに対し、Bing マップのタイル レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-168">Add a Bing map tile layer for the current viewport center and zoom level.</span></span> <span data-ttu-id="2c60f-169">タイル レイヤーの地理座標を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c60f-169">You do not need to specify the geographic coordinates for a tile layer.</span></span> <span data-ttu-id="2c60f-170">座標系を [地理]、投影法を [Mercator] に指定した場合に、Bing Maps サーバーが利用可能であり、レポート サーバーがこの機能をサポートするように構成されていれば、タイルは自動的にビューポート領域に合わせて読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-170">Tiles are automatically loaded to match the viewport area when the coordinate system is Geographic, the projection is Mercator, the Bing Maps servers are available, and when the report server has been configured to support this feature.</span></span> <span data-ttu-id="2c60f-171">各レポートで、タイルを取得する際にセキュリティで保護された接続を使用するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-171">For each report, you can specify whether to use a secure connection to retrieve tiles.</span></span>  
  
 <span data-ttu-id="2c60f-172">レイヤーの詳細については、「[マップまたはマップ レイヤーの追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c60f-172">For more information about layers, see [Add, Change, or Delete a Map or Map Layer &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="change-data-grouping-for-the-layer"></a><a name="DataGrouping"></a> <span data-ttu-id="2c60f-173">レイヤーのデータ グループを変更する</span><span class="sxs-lookup"><span data-stu-id="2c60f-173">Change Data Grouping for the Layer</span></span>  
 <span data-ttu-id="2c60f-174">独自の図形の空間データをどのように集計するかをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-174">You can customize the way to aggregate spatial data for your own shapes.</span></span> <span data-ttu-id="2c60f-175">レイヤーのグループ プロパティを設定するには、レイヤーのマップ ペインおよびプロパティ ペインでレイヤーを選択し、 **[グループ]** をクリックしてから参照ボタン [...] をクリックし、グループ プロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-175">To set the group properties for a layer, select the layer in the Map pane, and in the Properties pane for the layer, click **Group**, and then click the ellipsis (...) to open the Group properties.</span></span> <span data-ttu-id="2c60f-176">このダイアログ ボックスでは、グループ式の指定、グループ変数の作成、およびグループ化に使用するデータのフィルター処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-176">In this dialog box, you can specify group expressions, create group variables, and filter data that is used for grouping.</span></span>  
  
 <span data-ttu-id="2c60f-177">グループ式は、空間データとの間にリレーションシップを持つ分析データをレイヤー上の各マップ要素に対してどのように集計するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-177">The group expression specifies how analytical data that has a relationship to spatial data is aggregated for each map element on the layer.</span></span> <span data-ttu-id="2c60f-178">既定では、グループ式は、空間データと分析データの間のリレーションシップに対して指定された対応フィールドのセットです。</span><span class="sxs-lookup"><span data-stu-id="2c60f-178">By default, the group expression is the set of match fields that was specified for the relationship between the spatial data and the analytical data.</span></span> <span data-ttu-id="2c60f-179">たとえば、国または地域の市区町村の場所と人口規模を表示するバブル マップの場合、同じ名前を持つ複数の市区町村が存在する可能性があるため、対応フィールドには、市区町村名を示す [City] と地域名を示す [Region] が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-179">For example, for a bubble map that displays city locations and population size for a country or region, the match fields include city name [City] and region name [Region] because there can be multiple cities with the same name.</span></span> <span data-ttu-id="2c60f-180">対応するグループ式には、[City] と [Region] の 2 つのフィールドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-180">The corresponding group expression includes two fields: [City] and [Region].</span></span>  
  
 <span data-ttu-id="2c60f-181">詳細については、「 [Map Tips: How To Import Shapefiles Into SQL Server and Aggregate Spatial Data (マップ ヒント: シェープファイルの SQL Server へのインポートと空間データの集計方法)](https://go.microsoft.com/fwlink/?LinkID=214991)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c60f-181">For more information, see [Map Tips: How To Import Shapefiles Into SQL Server and Aggregate Spatial Data](https://go.microsoft.com/fwlink/?LinkID=214991).</span></span>  
  
 
  
##  <a name="change-options-for-the-map-elements-on-the-layer"></a><a name="MapElements"></a> <span data-ttu-id="2c60f-182">レイヤー上のマップ要素のオプションを変更する</span><span class="sxs-lookup"><span data-stu-id="2c60f-182">Change Options for the Map Elements on the Layer</span></span>  
 <span data-ttu-id="2c60f-183">マップ要素とは、空間データに基づく、レイヤー上のポイント、線、または多角形をいいます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-183">Map elements are the points, lines, or polygons on a layer that are based on the spatial data.</span></span> <span data-ttu-id="2c60f-184">マップ要素に関して設定できるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2c60f-184">For map elements, the following options can be set.</span></span> <span data-ttu-id="2c60f-185">これらのオプションは、埋め込みのマップ要素であるかどうかに関係なく、レイヤー上のすべてのマップ要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-185">These options apply to all map elements on the layer, whether or not they are embedded:</span></span>  
  
-   <span data-ttu-id="2c60f-186">ラベル、ラベルの可視性、ラベルのオフセット、および書式設定。</span><span class="sxs-lookup"><span data-stu-id="2c60f-186">Labels, label visibility, label offset, and formatting.</span></span>  
  
-   <span data-ttu-id="2c60f-187">境界および塗りつぶし。</span><span class="sxs-lookup"><span data-stu-id="2c60f-187">Borders and fill.</span></span>  
  
-   <span data-ttu-id="2c60f-188">ドリルスルー アクション。</span><span class="sxs-lookup"><span data-stu-id="2c60f-188">Drillthrough actions.</span></span>  
  
-   <span data-ttu-id="2c60f-189">表示オプション。</span><span class="sxs-lookup"><span data-stu-id="2c60f-189">Display options.</span></span>  
  
 <span data-ttu-id="2c60f-190">マップ要素の表示オプションは、レイヤー、マップ要素、マップ要素のルール、および、埋め込みマップ要素のオーバーライド オプションに基づく、一定の優先順位に従って適用されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-190">Display options for map elements follow a precedence order based on the layer, the map element, rules for the map element, and override options for embedded map elements.</span></span>  
  
 <span data-ttu-id="2c60f-191">これらのオプションを変更するには、マップ要素を右クリックし、埋め込みプロパティのダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-191">To change these options, right-click the map element, use the embedded properties dialog box.</span></span> <span data-ttu-id="2c60f-192">たとえば、埋め込み多角形には [マップの埋め込み多角形のプロパティ] ダイアログ ボックスの [全般] ページおよび関連するページを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-192">For example, for an embedded polygon, use the Map Embedded Polygon Properties Dialog Box, General page and related pages.</span></span>  
  

  
##  <a name="understanding-display-option-precedence"></a><a name="Precedence"></a> <span data-ttu-id="2c60f-193">表示オプションの優先順位について</span><span class="sxs-lookup"><span data-stu-id="2c60f-193">Understanding Display Option Precedence</span></span>  
 <span data-ttu-id="2c60f-194">マップ レイヤー上に表示されるポイント、線、または多角形の外観を制御するには、表示オプションをどこで設定すればよいかや、どのオプションが優先されるかをきちんと理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c60f-194">When you want to control the display appearance of a point, line, or polygon on a map layer, you must understand where display options can be set and which options have a higher precedence.</span></span> <span data-ttu-id="2c60f-195">以下に、表示オプションを優先順位の低いものから順に示します。</span><span class="sxs-lookup"><span data-stu-id="2c60f-195">The following display options are listed from lowest to highest.</span></span> <span data-ttu-id="2c60f-196">この一覧で優先順位の低い表示オプションは、優先順位の高い表示オプションによってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-196">Higher display options override lower display options in this list:</span></span>  
  
-   <span data-ttu-id="2c60f-197">レイヤーのオプション。</span><span class="sxs-lookup"><span data-stu-id="2c60f-197">Layer options.</span></span>  
  
-   <span data-ttu-id="2c60f-198">各レイヤー上のポイント、線、または多角形のオプション。</span><span class="sxs-lookup"><span data-stu-id="2c60f-198">Points, Lines, or Polygons options on each layer.</span></span> <span data-ttu-id="2c60f-199">これは、レポートの処理時にマップ要素が動的に取得されるか、マップ要素がレポート定義に埋め込まれているかに関係なく適用されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-199">This applies whether the map elements are dynamically retrieved when the report is processed or whether they the map elements are embedded in the report definition.</span></span> <span data-ttu-id="2c60f-200">たとえば、レイヤー上のすべての要素に対して塗りつぶしの色を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-200">For example, you specify a fill color for all elements on a layer.</span></span>  
  
-   <span data-ttu-id="2c60f-201">ルール。</span><span class="sxs-lookup"><span data-stu-id="2c60f-201">Rules.</span></span> <span data-ttu-id="2c60f-202">レイヤー上のすべてのマップ要素には、色、サイズ、幅、またはマーカーの種類を制御するルールを設定できます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-202">You can set rules to control color, size, width, or marker type for all map elements on a layer.</span></span> <span data-ttu-id="2c60f-203">設定できるルールはマップ要素の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="2c60f-203">The rules that you can set depend on the type of map element.</span></span>  
  
    -   <span data-ttu-id="2c60f-204">色ルール。</span><span class="sxs-lookup"><span data-stu-id="2c60f-204">Color Rules.</span></span> <span data-ttu-id="2c60f-205">ポイント、線、多角形のマーカー、および多角形の中心点のマーカーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-205">Apply to markers for points, lines, polygons, and markers for polygon center points.</span></span>  
  
    -   <span data-ttu-id="2c60f-206">サイズ ルール。</span><span class="sxs-lookup"><span data-stu-id="2c60f-206">Size Rules.</span></span> <span data-ttu-id="2c60f-207">ポイントのマーカーおよび多角形の中心点のマーカーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-207">Apply to markers for points and markers for polygon center points.</span></span>  
  
    -   <span data-ttu-id="2c60f-208">幅ルール。</span><span class="sxs-lookup"><span data-stu-id="2c60f-208">Width Rules.</span></span> <span data-ttu-id="2c60f-209">線の幅に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-209">Applies to line widths.</span></span>  
  
    -   <span data-ttu-id="2c60f-210">マーカーの種類ルール。</span><span class="sxs-lookup"><span data-stu-id="2c60f-210">Marker Type Rules.</span></span> <span data-ttu-id="2c60f-211">ポイントのマーカーおよび多角形の中心点のマーカーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-211">Applies to markers for points and markers for polygon center points.</span></span>  
  
-   <span data-ttu-id="2c60f-212">レイヤー上の埋め込みのポイント、線、または多角形に対して個別に適用されているオーバーライド オプション。</span><span class="sxs-lookup"><span data-stu-id="2c60f-212">Override options for individual embedded points, lines, or polygons on a layer.</span></span> <span data-ttu-id="2c60f-213">変更を加えた場合、その変更は永続的に保持されます。</span><span class="sxs-lookup"><span data-stu-id="2c60f-213">Changes that you make are permanent.</span></span> <span data-ttu-id="2c60f-214">これらの変更を元に戻すには、そのレイヤーのデータを再度読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c60f-214">To revert these changes, you must reload the data for the layer.</span></span>  
  
 <span data-ttu-id="2c60f-215">詳細については、「 [ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c60f-215">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="2c60f-216">参照</span><span class="sxs-lookup"><span data-stu-id="2c60f-216">See Also</span></span>  
 <span data-ttu-id="2c60f-217">[マップ ウィザードおよびマップ レイヤー ウィザードのページ &#40;レポート ビルダーおよび SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c60f-217">[Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2c60f-218">マップ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2c60f-218">Maps &#40;Report Builder and SSRS&#41;</span></span>](maps-report-builder-and-ssrs.md)  
  
  
