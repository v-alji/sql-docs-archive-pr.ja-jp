---
title: 'チュートリアル: マップ レポート (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8d831356-7efa-40cc-ae95-383b3eecf833
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b737bb3fe74eb3524f2944a7458cb4837b1aeedf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737788"
---
# <a name="tutorial-map-report-report-builder"></a><span data-ttu-id="13681-102">チュートリアル: マップ レポート (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="13681-102">Tutorial: Map Report (Report Builder)</span></span>
  <span data-ttu-id="13681-103">このチュートリアルでは、地図を背景としてレポート データを表示するときに使用できるマップ機能について学習できます。</span><span class="sxs-lookup"><span data-stu-id="13681-103">This tutorial is designed to help you learn about the map features you can use to display report data against a geographic background.</span></span>  
  
 <span data-ttu-id="13681-104">マップは、空間データに基づいています。空間データは通常、ポイント、線、および多角形で構成され</span><span class="sxs-lookup"><span data-stu-id="13681-104">Maps are based on spatial data that typically consists of points, lines, and polygons.</span></span> <span data-ttu-id="13681-105">(郡の輪郭を表す多角形、道路を表す線、市区町村の場所を表すポイントなど)、</span><span class="sxs-lookup"><span data-stu-id="13681-105">For example, a polygon can represent the outline of a county, a line can represent a road, and a point can represent the location of a city.</span></span> <span data-ttu-id="13681-106">種類ごとに異なるマップ レイヤーにマップ要素のセットとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-106">Each type of spatial data is displayed on a separate map layer as a set of map elements.</span></span>  
  
 <span data-ttu-id="13681-107">マップ要素の表示を変化させるには、マップ要素をデータセットの分析データに対応付ける値を持つフィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="13681-107">To vary the appearance of map elements, you specify a field that has values that match the map elements with analytical data from a dataset.</span></span> <span data-ttu-id="13681-108">色やサイズなどのプロパティをデータの範囲に基づいて変化させるルールを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="13681-108">You can also define rules that vary color, size, or other properties based on ranges of data.</span></span>  
  
 <span data-ttu-id="13681-109">このチュートリアルでは、New York 州の郡にある店舗の場所を表示するマップ レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="13681-109">In this tutorial, you will build a map report that displays store locations in New York state counties.</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="13681-110">学習内容</span><span class="sxs-lookup"><span data-stu-id="13681-110">What You Will Learn</span></span>  
 <span data-ttu-id="13681-111">このチュートリアルでは、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="13681-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="13681-112">マップ ウィザードを使用して多角形レイヤーを含むマップを作成する</span><span class="sxs-lookup"><span data-stu-id="13681-112">Create a Map with a Polygon Layer from the Map Wizard</span></span>](#Map)  
  
2.  [<span data-ttu-id="13681-113">店舗の場所を表示するマップのポイント レイヤーを追加する</span><span class="sxs-lookup"><span data-stu-id="13681-113">Add a Map Point Layer to Display Store Locations</span></span>](#PointLayer)  
  
3.  [<span data-ttu-id="13681-114">ルートを表示するマップの線レイヤーを追加する</span><span class="sxs-lookup"><span data-stu-id="13681-114">Add a Map Line Layer to Display a Route</span></span>](#LineLayer)  
  
4.  [<span data-ttu-id="13681-115">Bing Maps のタイル背景を追加する</span><span class="sxs-lookup"><span data-stu-id="13681-115">Add a Bing Maps Tile Background</span></span>](#TileLayer)  
  
5.  [<span data-ttu-id="13681-116">レイヤーを透明にする</span><span class="sxs-lookup"><span data-stu-id="13681-116">Make a Layer Transparent</span></span>](#Transparent)  
  
6.  [<span data-ttu-id="13681-117">郡の色を売上に基づいて変化させる</span><span class="sxs-lookup"><span data-stu-id="13681-117">Vary County Color Based on Sales</span></span>](#Vary)  
  
    1.  [<span data-ttu-id="13681-118">空間データと分析データの間にリレーションシップを構築する</span><span class="sxs-lookup"><span data-stu-id="13681-118">Build a Relationship between Spatial and Analytical Data</span></span>](#Relationship)  
  
    2.  [<span data-ttu-id="13681-119">多角形の色ルールを指定する</span><span class="sxs-lookup"><span data-stu-id="13681-119">Specify Color Rules for Polygons</span></span>](#ColorRules)  
  
    3.  [<span data-ttu-id="13681-120">カラー スケールのデータを通貨形式に変更する</span><span class="sxs-lookup"><span data-stu-id="13681-120">Format the Data in the Color Scale as Currency</span></span>](#ColorScale)  
  
    4.  [<span data-ttu-id="13681-121">新しい凡例を作成する</span><span class="sxs-lookup"><span data-stu-id="13681-121">Create a New Legend</span></span>](#NewLegend)  
  
    5.  [<span data-ttu-id="13681-122">凡例と色ルールを関連付ける</span><span class="sxs-lookup"><span data-stu-id="13681-122">Associate Legend and Color Rules</span></span>](#Associate)  
  
    6.  [<span data-ttu-id="13681-123">データのない郡から色をクリアする</span><span class="sxs-lookup"><span data-stu-id="13681-123">Clear Color from Counties with No Data</span></span>](#NoData)  
  
7.  [<span data-ttu-id="13681-124">カスタム ポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="13681-124">Add a Custom Point</span></span>](#CustomPoint)  
  
8.  [<span data-ttu-id="13681-125">マップ ビューの中心を設定する</span><span class="sxs-lookup"><span data-stu-id="13681-125">Center the Map View</span></span>](#CenterView)  
  
9. [<span data-ttu-id="13681-126">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="13681-126">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="13681-127">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="13681-127">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="13681-128">このチュートリアルでは、ウィザードに関する複数の手順を、データセットの作成とテーブルの作成の 2 つの手順にまとめて示します。</span><span class="sxs-lookup"><span data-stu-id="13681-128">In this tutorial, the steps for the wizard are consolidated into two procedures: one to create the dataset and one to create a table.</span></span> <span data-ttu-id="13681-129">レポート サーバーの参照、データ ソースの選択、データセットの作成、およびウィザードの実行に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 &#40;レポート ビルダー&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13681-129">For step-by-step instructions about how to browse to a report server, choose a data source, create a dataset, and run the wizard, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="13681-130">このチュートリアルの推定所要時間: 30 分。</span><span class="sxs-lookup"><span data-stu-id="13681-130">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13681-131">必要条件</span><span class="sxs-lookup"><span data-stu-id="13681-131">Requirements</span></span>  
 <span data-ttu-id="13681-132">要件の詳細については、[「チュートリアルの前提条件 (レポート ビルダー)」](../reporting-services/report-builder-tutorials.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13681-132">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-map-with-a-polygon-layer-from-the-map-wizard"></a><a name="Map"></a><span data-ttu-id="13681-133">1. マップウィザードを使用して多角形レイヤーを含むマップを作成する</span><span class="sxs-lookup"><span data-stu-id="13681-133">1. Create a Map with a Polygon Layer from the Map Wizard</span></span>  
 <span data-ttu-id="13681-134">マップをマップ ギャラリーからレポートに追加します。</span><span class="sxs-lookup"><span data-stu-id="13681-134">Add a map to your report from the map gallery.</span></span> <span data-ttu-id="13681-135">このマップには、New York 州の郡を表示するレイヤーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="13681-135">The map has one layer that displays the counties in New York state.</span></span> <span data-ttu-id="13681-136">各郡の図形は、マップ ギャラリーのマップに埋め込まれている空間データに基づく多角形です。</span><span class="sxs-lookup"><span data-stu-id="13681-136">The shape of each county is a polygon based on spatial data that is embedded in the map from the map gallery.</span></span>  
  
#### <a name="to-add-a-map-with-the-map-wizard-in-a-new-report"></a><span data-ttu-id="13681-137">新しいレポートでマップ ウィザードを使用してマップを追加するには</span><span class="sxs-lookup"><span data-stu-id="13681-137">To add a map with the map wizard in a new report</span></span>  
  
1.  <span data-ttu-id="13681-138">[**スタート**] をクリックし、[**プログラム**]、[レポートビルダー] の順にポイントし、[ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder\*\*\*\*レポートビルダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-138">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="13681-139">[作業の開始] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-139">The Getting Started dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13681-140">[はじめに] ダイアログボックスが表示されない場合は、[レポートビルダー] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-140">If the Getting Started dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="13681-141">左側のウィンドウで、[**レポート**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13681-141">In the left pane, verify that **Report** is selected.</span></span>  
  
3.  <span data-ttu-id="13681-142">右ペインで、 **[マップ ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-142">In the right pane, click **Map Wizard**.</span></span>  
  
4.  <span data-ttu-id="13681-143">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-143">Click **Create**.</span></span>  
  
5.  <span data-ttu-id="13681-144">**[空間データのソースを選択**] ページで、[**マップギャラリー** ] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13681-144">**Choose a source of spatial data** page, verify that **Map gallery** is selected.</span></span>  
  
6.  <span data-ttu-id="13681-145">[マップギャラリー] ペインで、[ **USA**] の **[都道府県] を展開し**、[**ニューヨーク**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-145">In the Map Gallery pane, expand **States by County** under **USA**, and click **New York**.</span></span>  
  
     <span data-ttu-id="13681-146">[マップ プレビュー] ペインに、New York の郡マップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-146">The Map Preview pane displays the New York county map.</span></span>  
  
7.  <span data-ttu-id="13681-147">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-147">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="13681-148">[**空間データとマップビューのオプションを選択**] ページで、既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="13681-148">On the **Choose spatial data and map view options** page, accept the defaults.</span></span> <span data-ttu-id="13681-149">既定では、マップ ギャラリーのマップ要素は自動的にレポート定義に埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="13681-149">By default, map elements from a map gallery will automatically be embedded in the report definition.</span></span>  
  
9. <span data-ttu-id="13681-150">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-150">Click **Next**.</span></span>  
  
10. <span data-ttu-id="13681-151">**[マップの視覚エフェクトを選択]** ページで、 **[基本マップ]** が選択されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-151">On the **Choose map visualization** page, verify **Basic Map** is selected, and click **Next**.</span></span>  
  
11. <span data-ttu-id="13681-152">**[配色テーマとデータの視覚エフェクトを選択]** ページで、 **[ラベルの表示]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="13681-152">On the **Choose color theme and data visualization** page, select the **Display labels** option.</span></span>  
  
12. <span data-ttu-id="13681-153">**[単色マップ]** チェック ボックスがオンになっている場合はオフにします。</span><span class="sxs-lookup"><span data-stu-id="13681-153">If it is selected, clear the **Single color map** option.</span></span>  
  
13. <span data-ttu-id="13681-154">[**データフィールド**] ボックスの一覧の [#COUNTYNAME] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-154">From the **Data field** drop-down list, click #COUNTYNAME.</span></span> <span data-ttu-id="13681-155">ウィザードの [マップ プレビュー] ペインに次のアイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-155">The Map Preview pane in the wizard displays the following items:</span></span>  
  
    -   <span data-ttu-id="13681-156">" **マップのタイトル**" というテキストを含むタイトル。</span><span class="sxs-lookup"><span data-stu-id="13681-156">A title with the text **Map Title**.</span></span>  
  
    -   <span data-ttu-id="13681-157">New York の郡を表示するマップ。各郡は異なる色で表示され、郡の領域に収まる場所に郡の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-157">A map that displays counties in New York where each county is a different color and the county name appears wherever it fits over the county area.</span></span>  
  
    -   <span data-ttu-id="13681-158">タイトルとアイテム 1 ～ 5 の一覧を含む凡例。</span><span class="sxs-lookup"><span data-stu-id="13681-158">A legend that contains a title and a list of items 1 through 5.</span></span>  
  
    -   <span data-ttu-id="13681-159">値 0 ～ 160 および色なしを含むカラー スケール。</span><span class="sxs-lookup"><span data-stu-id="13681-159">A color scale that contains values 0 to 160 and no color.</span></span>  
  
    -   <span data-ttu-id="13681-160">キロメートル (km) およびマイル (mi) を表示する距離スケール。</span><span class="sxs-lookup"><span data-stu-id="13681-160">A distance scale that displays kilometers (km) and miles (mi).</span></span>  
  
14. <span data-ttu-id="13681-161">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-161">Click **Finish**.</span></span>  
  
     <span data-ttu-id="13681-162">デザイン画面にマップが追加されます。</span><span class="sxs-lookup"><span data-stu-id="13681-162">The map is added to the design surface.</span></span>  
  
15. <span data-ttu-id="13681-163">マップをクリックして選択し、[**マップレイヤー] ペイン**を表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-163">Click the map to select it and display the **Map Layers Pane**.</span></span> <span data-ttu-id="13681-164">[**マップレイヤー] ペイン**には、レイヤーの種類の1つの多角形レイヤーが**埋め込ま**れて表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-164">The **Map Layers Pane** shows one polygon layer of layer type **Embedded**.</span></span> <span data-ttu-id="13681-165">各郡は、このレイヤー上の埋め込みマップ要素となります。</span><span class="sxs-lookup"><span data-stu-id="13681-165">Each county is an embedded map element on this layer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13681-166">[**マップレイヤー** ] ペインが表示されない場合は、現在のビューの外側に表示されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13681-166">If you do not see the **Map Layers** pane, it might be displayed outside your current view.</span></span> <span data-ttu-id="13681-167">デザイン ビュー ウィンドウの下部にあるスクロール バーを使用して、ビューを変更してください。</span><span class="sxs-lookup"><span data-stu-id="13681-167">Use the scroll bar at the bottom of the Design view window to change your view.</span></span> <span data-ttu-id="13681-168">または、[**表示**] タブで [**プロパティ**] または [**レポートデータ**] オプションをオフにして、より多くのデザイン領域を提供します。</span><span class="sxs-lookup"><span data-stu-id="13681-168">Alternatively, in the **View** tab, clear the **Properties** or the **Report Data** option to provide more design surface area.</span></span>  
  
16. <span data-ttu-id="13681-169">マップのタイトルを右クリックし、[**タイトルのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-169">Right-click the map title, and then click **Title Properties**.</span></span>  
  
17. <span data-ttu-id="13681-170">タイトルのテキストを " **Sales By Store**" に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="13681-170">Replace the title text with **Sales by Store**.</span></span>  
  
18. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
19. <span data-ttu-id="13681-171">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-171">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-172">表示されたレポートには、マップのタイトル、マップ、および距離スケールが表示されています。</span><span class="sxs-lookup"><span data-stu-id="13681-172">The rendered report displays the map title, the map, and the distance scale.</span></span> <span data-ttu-id="13681-173">郡はマップの多角形レイヤーにあります。</span><span class="sxs-lookup"><span data-stu-id="13681-173">The counties are on a map polygon layer.</span></span> <span data-ttu-id="13681-174">各郡は多角形で、カラー パレットからそれぞれ異なる色が割り当てられていますが、色はデータとは関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="13681-174">Each county is a polygon that varies by color from a color palette, but the colors are not associated with any data.</span></span> <span data-ttu-id="13681-175">距離スケールには、距離がキロメートル単位とマイル単位の両方で表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-175">The distance scale displays distances in both kilometers and miles.</span></span>  
  
 <span data-ttu-id="13681-176">マップの凡例とカラー スケールは、各郡に分析データが関連付けられていないため、まだ表示されません。</span><span class="sxs-lookup"><span data-stu-id="13681-176">The map legend and color scale do not yet appear because there is no analytical data associated with each county.</span></span> <span data-ttu-id="13681-177">このチュートリアルで後ほど分析データを追加します。</span><span class="sxs-lookup"><span data-stu-id="13681-177">You will add analytical data later in this tutorial.</span></span>  
  
##  <a name="2-add-a-map-point-layer-to-display-store-locations"></a><a name="PointLayer"></a><span data-ttu-id="13681-178">2. 店舗の場所を表示するマップのポイントレイヤーを追加する</span><span class="sxs-lookup"><span data-stu-id="13681-178">2. Add a Map Point Layer to Display Store Locations</span></span>  
 <span data-ttu-id="13681-179">マップ レイヤー ウィザードを使用して、店舗の場所を表示するポイント レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="13681-179">Use the map layer wizard to add a point layer that displays the locations of stores.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13681-180">このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="13681-180">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="13681-181">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="13681-181">This makes the query quite long.</span></span> <span data-ttu-id="13681-182">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="13681-182">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="13681-183">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="13681-183">This is for learning purposes only.</span></span>  
  
#### <a name="to-add-a-point-layer-based-on-a-sql-server-spatial-query"></a><span data-ttu-id="13681-184">SQL Server 空間クエリに基づいてポイント レイヤーを追加するには</span><span class="sxs-lookup"><span data-stu-id="13681-184">To add a point layer based on a SQL Server spatial query</span></span>  
  
1.  <span data-ttu-id="13681-185">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-185">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-186">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-186">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="13681-187">ツールバーの **[レイヤーの新規作成]** ボタン ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard") をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-187">On the toolbar, click the **New layer wizard** button ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard").</span></span>  
  
3.  <span data-ttu-id="13681-188">**[空間データのソースを選択]** ページで、 **[SQL Server 空間クエリ]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-188">On the **Choose a source of spatial data** page, select **SQL Server spatial query**, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="13681-189">[**空間データを SQL Server したデータセットの選択**] ページで、[ **SQL Server 空間データを含む新しいデータセットを追加する**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-189">On the **Choose a dataset with SQL Server spatial data** page, click **Add a new dataset with SQL Server spatial data**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="13681-190">**[SQL Server 空間データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-190">On the **Choose a connection to a SQL Server spatial data source** page, select an existing data source or browse to the report server and select a data source.</span></span>  
  
6.  <span data-ttu-id="13681-191">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-191">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="13681-192">[クエリのデザイン] ページで、[**テキストとして編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-192">On the Design a Query page, click **Edit as Text**.</span></span>  
  
8.  <span data-ttu-id="13681-193">クエリ ペインに次のテキストを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="13681-193">Paste the following text in the query pane:</span></span>  
  
    ```  
    Select 114 as StoreKey, 'Contoso Albany Store' as StoreName, 1125 as SellingArea, 'Albany' as City, 'Albany' as County,   
     CAST(1000000 as money) as Sales, CAST('POINT(-73.7472924218681 42.6564617079878)' as geography) AS SpatialLocation  
    UNION ALL SELECT 115 AS StoreKey, 'Contoso New York No.1 Store' AS  StoreName, 500 as SellingArea, 'New York' AS City, 'New York City' as County,  
     CAST('2000000' as money) as Sales, CAST('POINT(-73.9922069374483 40.7549638237402)' as geography) AS SpatialLocation  
    UNION ALL Select 116 as StoreKey, 'Contoso Rochester No.1 Store' as StoreName, 462 as SellingArea, 'Rochester' as City,  'Monroe' as County,    
     CAST(3000000 as money) as Sales, CAST('POINT(-77.624041566786 43.1547066024338)' as geography)  AS SpatialLocation  
    UNION ALL Select 117 as StoreKey, 'Contoso New York No.2 Store' as StoreName, 700 as SellingArea, 'New York' as City,'New York City' as County,    
      CAST(4000000 as money) as Sales, CAST('POINT(-73.9712488 40.7830603)' as geography) AS SpatialLocation  
    UNION ALL Select 118 as StoreKey, 'Contoso Syracuse Store' as StoreName, 680 as SellingArea, 'Syracuse' as City, 'Onondaga' as County,  
     CAST(5000000 as money) as Sales, CAST('POINT(-76.1349120532546 43.0610223535974)' as geography) AS SpatialLocation  
    UNION ALL Select 120 as StoreKey, 'Contoso Plattsburgh Store' as StoreName, 560 as SellingArea, 'Plattsburgh' as City,  'Clinton' as County,  
     CAST(6000000 as money) as Sales, CAST('POINT(-73.4728622833178 44.7028831413324)' as geography) AS SpatialLocation  
    UNION ALL Select 121 as StoreKey, 'Contoso Brooklyn Store' as StoreName, 1125 as SellingArea, 'Brooklyn' as City, 'New York City' as County,  
     CAST(7000000 as money) as Sales, CAST('POINT (-73.9638533447143 40.6785123489351)' as geography) AS SpatialLocation  
    UNION ALL Select 122 as StoreKey, 'Contoso Oswego Store' as StoreName, 500 as SellingArea, 'Oswego' as City, 'Oswego' as County,    
     CAST(8000000 as money) as Sales, CAST('POINT(-76.4602850815536 43.4353224527794)' as geography) AS SpatialLocation  
    UNION ALL Select 123 as StoreKey, 'Contoso Ithaca Store' as StoreName, 460 as SellingArea, 'Ithaca' as City, 'Tompkins' as County,  
     CAST(9000000 as money) as Sales, CAST('POINT(-76.5001866085881 42.4310489934743)' as geography) AS SpatialLocation  
    UNION ALL Select 124 as StoreKey, 'Contoso Rochester No.2 Store' as StoreName, 700 as SellingArea, 'Rochester' as City, 'Monroe' as County,    
     CAST(100000 as money) as Sales, CAST('POINT(-77.6240415667866 43.1547066024338)' as geography) AS SpatialLocation  
    UNION ALL Select 125 as StoreKey, 'Contoso Queens Store' as StoreName, 700 as SellingArea,'Queens' as City, 'New York City' as County,  
     CAST(500000 as money) as Sales, CAST('POINT(-73.7930979029883 40.7152781765927)' as geography) AS SpatialLocation  
    UNION ALL Select 126 as StoreKey, 'Contoso Elmira Store' as StoreName, 680 as SellingArea, 'Elmira' as City, 'Chemung' as County,  
     CAST(800000 as money) as Sales, CAST('POINT(-76.7397414783301 42.0736492742663)' as geography) AS SpatialLocation  
    UNION ALL Select 127 as StoreKey, 'Contoso Poestenkill Store' as StoreName, 455 as SellingArea, 'Poestenkill' as City, 'Rensselaer' as County,    
    CAST(1500000 as money) as Sales, CAST('POINT(-73.5626737425063 42.6940551238618)' as geography) AS SpatialLocation  
    ```  
  
9. <span data-ttu-id="13681-194">クエリデザイナーのツールバーで、[**実行**] (**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-194">On the query designer toolbar, click **Run** (**!**).</span></span>  
  
     <span data-ttu-id="13681-195">結果セットには、7 つの列 (StoreKey、StoreName、SellingArea、City、County、Sales、SpatialLocation) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-195">The result set displays seven columns: StoreKey, StoreName, SellingArea, City, County, Sales, and SpatialLocation.</span></span> <span data-ttu-id="13681-196">このデータは、消費者向けの商品を販売している New York 州内の店舗を表しています。</span><span class="sxs-lookup"><span data-stu-id="13681-196">This data represents a set of stores in New York State that sell consumer goods.</span></span> <span data-ttu-id="13681-197">結果セットの各行には、店舗識別子、店舗名、商品の展示に使用できる面積、店舗の所在地の市および郡、売上合計、および所在地の経度と緯度が含まれています。</span><span class="sxs-lookup"><span data-stu-id="13681-197">Each row in the result set contains a store identifier, store name, the area available for product display, the city and county where the store is located, the sales total, and the spatial location in longitude and latitude.</span></span> <span data-ttu-id="13681-198">展示面積の範囲は 455 ～ 1125 平方フィートです。</span><span class="sxs-lookup"><span data-stu-id="13681-198">The display area ranges from 455 square feet to 1125 square feet.</span></span>  
  
10. <span data-ttu-id="13681-199">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-199">Click **Next**.</span></span>  
  
     <span data-ttu-id="13681-200">DataSet1 という名前のレポート データセットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="13681-200">The report dataset named DataSet1 is created for you.</span></span> <span data-ttu-id="13681-201">ウィザードを完了した後、レポート データを使用して、このデータセットのフィールド コレクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="13681-201">After you complete the wizard, you can use the Report Data to its field collection.</span></span>  
  
11. <span data-ttu-id="13681-202">[**空間データとマップビューのオプションを選択**] ページで、**空間フィールド**がで、レイヤーの種類が [ポイント] であることを確認し `SpatialLocation` ます。 **Layer type** **Point**</span><span class="sxs-lookup"><span data-stu-id="13681-202">On the **Choose a spatial data and map view options** page, verify that the **Spatial field** is `SpatialLocation` and that the **Layer type** is **Point**.</span></span> <span data-ttu-id="13681-203">このページの他の項目は、既定の設定をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="13681-203">Accept the other defaults on this page.</span></span>  
  
     <span data-ttu-id="13681-204">マップ ビューに、各店舗の場所を示す円が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-204">The map view displays circles that mark the location of each store.</span></span>  
  
12. <span data-ttu-id="13681-205">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-205">Click **Next**.</span></span>  
  
13. <span data-ttu-id="13681-206">分析データによって異なるマーカーを表示するマップの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="13681-206">Specify a map type that displays markers that vary by analytic data.</span></span> <span data-ttu-id="13681-207">[マップの視覚エフェクトの選択] ページで、[**分析マーカーマップ**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-207">On the Choose map visualization page, click **Analytical Marker Map**, and then click **Next**.</span></span>  
  
14. <span data-ttu-id="13681-208">[**分析データセットの選択**] ページで、[DataSet1] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-208">On the **Choose the analytical dataset** page, click DataSet1.</span></span> <span data-ttu-id="13681-209">このデータセットには、新しいポイント レイヤーに表示される分析データと空間データの両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="13681-209">This dataset contains both analytical data and spatial data that will be displayed on the new point layer.</span></span>  
  
15. <span data-ttu-id="13681-210">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-210">Click **Next**.</span></span>  
  
16. <span data-ttu-id="13681-211">[**配色テーマとデータの視覚エフェクトを選択**] ページで、[**マーカーの色を使用してデータを表示する**] オプションをオフにし、[マーカーの**種類を使用してデータを表示する**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-211">On the **Choose color theme and data visualization** page, clear the **Use marker colors to visualize data** option, and then select the option **Use marker types to visualize data**.</span></span>  
  
17. <span data-ttu-id="13681-212">[**データフィールド**] で、 `[Sum(SellingArea)]` 店舗が製品を表示するために確保する領域のサイズで、マーカーの種類を変更します。</span><span class="sxs-lookup"><span data-stu-id="13681-212">In **Data field**, select `[Sum(SellingArea)]` to vary marker types by the size of the area a store sets aside to display the products.</span></span>  
  
18. <span data-ttu-id="13681-213">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-213">Click **Finish**.</span></span>  
  
     <span data-ttu-id="13681-214">マップ レイヤーがレポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="13681-214">The map layer is added to the report.</span></span> <span data-ttu-id="13681-215">凡例には、SellingArea の値に基づくマーカーの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-215">The legend displays marker types based on SellingArea values.</span></span>  
  
     <span data-ttu-id="13681-216">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-216">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="13681-217">**[マップ レイヤー]** ペインに、空間データ ソースの種類が **DataRegion**である新しいレイヤー PointLayer1 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-217">The **Map Layer** pane displays a new layer, PointLayer1, with spatial data source type **DataRegion**.</span></span>  
  
19. <span data-ttu-id="13681-218">凡例のタイトルを追加します。</span><span class="sxs-lookup"><span data-stu-id="13681-218">Add a legend title.</span></span> <span data-ttu-id="13681-219">凡例のタイトルを右クリックし、[**凡例のタイトルのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-219">Right-click the legend title, and then click **Legend Title Properties**.</span></span>  
  
20. <span data-ttu-id="13681-220">タイトルを削除し、「**表示領域 (平方フィート)**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="13681-220">Delete the title, and type **Display Area (Square Feet)**.</span></span>  
  
21. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
22. <span data-ttu-id="13681-221">ウィザードによって設定された既定値を確認します。</span><span class="sxs-lookup"><span data-stu-id="13681-221">View the default values that were set by the wizard.</span></span> <span data-ttu-id="13681-222">[**マップレイヤー] ペイン**で、ポイントレイヤーを右クリックし、[**マーカーの種類のルール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-222">In the **Map Layers Pane**, right-click the point layer, and then click **Marker Type Rule**.</span></span>  
  
     <span data-ttu-id="13681-223">[**全般**] タブのマーカーは、凡例に表示される順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-223">On the **General** tab, the markers are listed in the order in which they appear in the legend.</span></span> <span data-ttu-id="13681-224">[**配布**] タブの [部分範囲の数] は5です。</span><span class="sxs-lookup"><span data-stu-id="13681-224">On the **Distribution** tab, the number of subranges is 5.</span></span> <span data-ttu-id="13681-225">[**凡例**] タブで、各範囲の開始値と終了値を表示するように凡例のテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="13681-225">On the **Legend** tab, the legend text is set to display the start and end value in each range.</span></span>  
  
23. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
24. <span data-ttu-id="13681-226">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-226">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-227">マップには、New York 州にある店舗の場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-227">The map displays the locations of stores in New York state.</span></span> <span data-ttu-id="13681-228">各店舗のマーカーの種類は展示面積に基づいています。</span><span class="sxs-lookup"><span data-stu-id="13681-228">The marker type for each store is based on the display area.</span></span> <span data-ttu-id="13681-229">展示面積の 5 つの範囲が自動的に計算されます。</span><span class="sxs-lookup"><span data-stu-id="13681-229">Five ranges of display area were automatically calculated for you.</span></span>  
  
##  <a name="3-add-a-map-line-layer-to-display-a-route"></a><a name="LineLayer"></a><span data-ttu-id="13681-230">3. ルートを表示するためのマップの線レイヤーを追加する</span><span class="sxs-lookup"><span data-stu-id="13681-230">3. Add a Map Line Layer to Display a Route</span></span>  
 <span data-ttu-id="13681-231">マップ レイヤー ウィザードを使用して、2 つの店舗間のルートを表示するマップ レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="13681-231">Use the map layer wizard to add a map layer that displays a route between two stores.</span></span> <span data-ttu-id="13681-232">このチュートリアルではパスを 3 つの店舗の場所から作成しますが、</span><span class="sxs-lookup"><span data-stu-id="13681-232">In this tutorial, the path is created from three store locations.</span></span> <span data-ttu-id="13681-233">ビジネス アプリケーションでは店舗間の最適なルートにすることができます。</span><span class="sxs-lookup"><span data-stu-id="13681-233">In a business application, the path might be the best route between stores.</span></span>  
  
#### <a name="to-add-a-line-layer-to-map"></a><span data-ttu-id="13681-234">マップに線レイヤーを追加するには</span><span class="sxs-lookup"><span data-stu-id="13681-234">To add a line layer to map</span></span>  
  
1.  <span data-ttu-id="13681-235">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-235">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-236">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-236">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="13681-237">ツールバーの [**レイヤーの新規作成ウィザード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-237">On the toolbar, click **New layer wizard**.</span></span>  
  
3.  <span data-ttu-id="13681-238">[**空間データのソースを選択**] ページで、[**空間クエリ SQL Server** ] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-238">On the **Choose a source of spatial data** page, select **SQL Server spatial query** and click **Next**.</span></span>  
  
4.  <span data-ttu-id="13681-239">**[SQL Server 空間データを含むデータセットの選択]** ページで、 **[SQL Server 空間データを含む新しいデータセットの追加]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-239">On the **Choose a dataset with SQL Server spatial data** page, click **Add a new dataset with SQL Server spatial data** and click **Next**.</span></span>  
  
5.  <span data-ttu-id="13681-240">[ **SQL Server 空間データソースへの接続の選択**] で、最初の手順で作成したデータソースの [DataSource1] を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-240">On the **Choose a connection to a SQL Server spatial data source**, select DataSource1, the data source that you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="13681-241">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-241">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="13681-242">[**クエリのデザイン**] ページで、[**テキストとして編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-242">On the **Design a Query** page, click **Edit as Text**.</span></span> <span data-ttu-id="13681-243">クエリ デザイナーがテキスト ベース モードに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="13681-243">The query designer switches to text-based mode.</span></span>  
  
8.  <span data-ttu-id="13681-244">クエリ ペインに次のテキストを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="13681-244">Paste the following text in the query pane:</span></span>  
  
    ```  
    SELECT N'Path' AS Name, CAST('LINESTRING(  
       -76.5001866085881 42.4310489934743,  
       -76.4602850815536 43.4353224527794,  
       -73.4728622833178 44.7028831413324)' AS geography) as Route  
    ```  
  
9. <span data-ttu-id="13681-245">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-245">Click **Next**.</span></span>  
  
     <span data-ttu-id="13681-246">3 つの店舗を接続するパスがマップに表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-246">A path appears on the map that connects three stores.</span></span>  
  
10. <span data-ttu-id="13681-247">**[空間データとマップ ビューのオプションを選択]** ページで、 **[空間フィールド]** が **Route** であり、 **[レイヤーの種類]** が **[線]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13681-247">On the **Choose spatial data and map view options** page, verify that the **Spatial field** is **Route** and that the **Layer type** is **Line**.</span></span> <span data-ttu-id="13681-248">他の項目は既定の設定をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="13681-248">Accept the other defaults.</span></span>  
  
     <span data-ttu-id="13681-249">マップ ビューに、New York 州の北部にある店舗から New York 州の南部にある店舗へのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-249">The map view displays a path from a store in the northern part of New York state to a store in the southern part of New York state.</span></span>  
  
11. <span data-ttu-id="13681-250">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-250">Click **Next**.</span></span>  
  
12. <span data-ttu-id="13681-251">**[マップの視覚エフェクトを選択]** ページで、 **[基本線マップ]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-251">On the **Choose map visualization** page, click **Basic Line Map**, and then click **Next**.</span></span>  
  
13. <span data-ttu-id="13681-252">**[配色テーマとデータの視覚エフェクトを選択]** で、 **[単色マップ]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-252">On the **Choose color theme and data visualization**, select the option **Single color map**.</span></span> <span data-ttu-id="13681-253">選択したテーマに基づく 1 つの色でパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-253">The path appears as a single color based on the selected theme.</span></span>  
  
14. <span data-ttu-id="13681-254">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-254">Click **Finish**.</span></span>  
  
 <span data-ttu-id="13681-255">マップには、空間データソースの種類が**DataSet**の新しい線レイヤーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-255">The map displays a new line layer with spatial data source type **DataSet**.</span></span> <span data-ttu-id="13681-256">この例では、空間データがデータセットから得られますが、線に分析データは関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="13681-256">In this example, the spatial data comes from a dataset but no analytical data is associated with the line.</span></span>  
  
##  <a name="4-add-a-bing-maps-tile-background"></a><a name="TileLayer"></a><span data-ttu-id="13681-257">4. Bing Maps のタイル背景を追加する</span><span class="sxs-lookup"><span data-stu-id="13681-257">4. Add a Bing Maps Tile Background</span></span>  
 <span data-ttu-id="13681-258">Bing Maps のタイル背景を表示するマップ レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="13681-258">Add a map layer that displays a Bing Maps tile background.</span></span>  
  
#### <a name="to-add-a-virtual-earth-tile-background"></a><span data-ttu-id="13681-259">Virtual Earth タイル背景を追加するには</span><span class="sxs-lookup"><span data-stu-id="13681-259">To add a Virtual Earth tile background</span></span>  
  
1.  <span data-ttu-id="13681-260">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-260">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-261">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-261">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="13681-262">ツールバーの **[レイヤーの追加]**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer") をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-262">On the toolbar, click **Add Layer**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer").</span></span>  
  
3.  <span data-ttu-id="13681-263">ドロップダウン リストで、 **[タイル レイヤー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-263">From the drop-down list, click **Tile Layer**.</span></span>  
  
     <span data-ttu-id="13681-264">**[マップ レイヤー]** ペインの最後のレイヤーは TileLayer1 です。</span><span class="sxs-lookup"><span data-stu-id="13681-264">The last layer in the **Map Layer** pane is TileLayer1.</span></span> <span data-ttu-id="13681-265">既定では、タイル レイヤーには道路地図スタイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-265">By default, the tile layer displays the road map style.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13681-266">ウィザードでも、 **[空間データとマップ ビューのオプションを選択]** ページでタイル レイヤーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="13681-266">In the wizard, you can also add a tile layer on the **Choose spatial data and map view options** page.</span></span> <span data-ttu-id="13681-267">そのためには、 **[このマップ ビューに Bing Maps の背景を追加する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-267">To do this, select **Add a Bing Maps background for this map view**.</span></span> <span data-ttu-id="13681-268">表示されるレポートのタイルの背景では、現在のマップ ビューポートの中心およびズーム レベルに基づいて Bing Maps のタイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-268">In a rendered report, the tile background displays Bing Maps tiles for the current map viewport center and zoom level.</span></span>  
  
4.  <span data-ttu-id="13681-269">TileLayer1 の下矢印をクリックし、[**タイルのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-269">Click the down arrow on TileLayer1, and then click **Tile Properties**.</span></span>  
  
5.  <span data-ttu-id="13681-270">[**種類**] で [**航空写真**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-270">In **Type**, select **Aerial**.</span></span> <span data-ttu-id="13681-271">航空写真ビューには、テキストは含まれません。</span><span class="sxs-lookup"><span data-stu-id="13681-271">The aerial view does not contain text.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="5-make-a-layer-transparent"></a><a name="Transparent"></a><span data-ttu-id="13681-272">5. レイヤーを透明にする</span><span class="sxs-lookup"><span data-stu-id="13681-272">5. Make a Layer Transparent</span></span>  
 <span data-ttu-id="13681-273">レイヤー上のアイテムが別のレイヤーを通して見えるようにするには、レイヤーの順序と各レイヤーの透明度を、目的の効果が得られるように調整します。</span><span class="sxs-lookup"><span data-stu-id="13681-273">To let the items on one layer show through another layer, you can adjust the order of layers and the transparency of each layer to get the effect that you want.</span></span>  
  
#### <a name="to-set-the-transparency-of-a-layer"></a><span data-ttu-id="13681-274">レイヤーの透明度を設定するには</span><span class="sxs-lookup"><span data-stu-id="13681-274">To set the transparency of a layer</span></span>  
  
1.  <span data-ttu-id="13681-275">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-275">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-276">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-276">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="13681-277">PolygonLayer1 の下矢印をクリックし、[**レイヤーデータ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-277">Click the down arrow on PolygonLayer1, and then click **Layer Data**.</span></span> <span data-ttu-id="13681-278">**[マップの多角形レイヤーのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-278">The **Map Polygon Layer Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="13681-279">**[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-279">Click **Visibility**.</span></span>  
  
5.  <span data-ttu-id="13681-280">[**透明度 (%)**] に「 **30**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="13681-280">In **Transparency (%)**, type **30**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="13681-281">デザイン画面に郡が半透明で表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-281">The design surface displays the counties as semi-transparent.</span></span>  
  
##  <a name="6-vary-county-color-based-on-sales"></a><a name="Vary"></a><span data-ttu-id="13681-282">6. 売上に基づいて郡の色を変更する</span><span class="sxs-lookup"><span data-stu-id="13681-282">6. Vary County Color Based on Sales</span></span>  
 <span data-ttu-id="13681-283">レポート プロセッサにより、マップ ウィザードの最後のページで選択したテーマに基づいてカラー パレットから色値が自動的に割り当てられるため、多角形レイヤー上の各郡は異なる色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-283">Each county on the polygon layer has a different color because the report processor automatically assigns a color value from the color palette based on the theme that you chose on the last page of the map wizard.</span></span>  
  
 <span data-ttu-id="13681-284">以降の手順では、各郡の店舗売上の範囲に特定の色を関連付ける色ルールを指定します。</span><span class="sxs-lookup"><span data-stu-id="13681-284">In the following steps, specify a color rule to associate specific colors with a range of store sales for each county.</span></span> <span data-ttu-id="13681-285">赤、黄、緑の各色は、売上高が相対的に高い、中程度、または低いことを示します。</span><span class="sxs-lookup"><span data-stu-id="13681-285">The colors red-yellow-green indicate relative high-middle-low sales.</span></span> <span data-ttu-id="13681-286">カラー スケールを通貨形式に変更します。</span><span class="sxs-lookup"><span data-stu-id="13681-286">Format the color scale to show currency.</span></span> <span data-ttu-id="13681-287">新しい凡例に年間売上高の範囲を表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-287">Display the annual sales ranges in a new legend.</span></span> <span data-ttu-id="13681-288">店舗のない郡については、どの色も使用しないことで、関連付けられたデータがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="13681-288">For counties that do not contain stores, use no color to show that there is no associated data.</span></span>  
  
###  <a name="6a-build-a-relationship-between-spatial-and-analytical-data"></a><a name="Relationship"></a><span data-ttu-id="13681-289">6a.</span><span class="sxs-lookup"><span data-stu-id="13681-289">6a.</span></span> <span data-ttu-id="13681-290">空間データと分析データの間にリレーションシップを構築する</span><span class="sxs-lookup"><span data-stu-id="13681-290">Build a Relationship between Spatial and Analytical Data</span></span>  
 <span data-ttu-id="13681-291">分析データに基づいて郡の図形を色分けするには、まず分析データを空間データに関連付けておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="13681-291">To vary the county shapes by color based on analytical data, you first must associate the analytical data with the spatial data.</span></span> <span data-ttu-id="13681-292">このチュートリアルでは、郡の名前を使用してデータを対応させます。</span><span class="sxs-lookup"><span data-stu-id="13681-292">In this tutorial, you will use the county name to match on.</span></span>  
  
##### <a name="to-build-a-relationship-between-spatial-data-and-analytical-data"></a><span data-ttu-id="13681-293">空間データと分析データの間にリレーションシップを構築するには</span><span class="sxs-lookup"><span data-stu-id="13681-293">To build a relationship between spatial data and analytical data</span></span>  
  
1.  <span data-ttu-id="13681-294">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-294">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-295">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-295">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="13681-296">PolygonLayer1 の下矢印をクリックし、[**レイヤーデータ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-296">Click the down arrow on PolygonLayer1, and then click **Layer Data**.</span></span> <span data-ttu-id="13681-297">**[マップの多角形レイヤーのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-297">The **Map Polygon Layer Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="13681-298">**[分析データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-298">Click **Analytical data**.</span></span>  
  
5.  <span data-ttu-id="13681-299">ドロップダウン リストから [DataSet1] を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-299">From the drop-down list, select DataSet1.</span></span> <span data-ttu-id="13681-300">このデータセットは、郡の空間データ クエリを指定したときにウィザードによって作成されたものです。</span><span class="sxs-lookup"><span data-stu-id="13681-300">This dataset was created by the wizard when you specified the spatial data query for the counties.</span></span>  
  
6.  <span data-ttu-id="13681-301">[**一致させるフィールド**] で、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-301">In **Fields to match on**, click **Add**.</span></span> <span data-ttu-id="13681-302">新しい行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="13681-302">A new row is added.</span></span>  
  
7.  <span data-ttu-id="13681-303">[**空間データセットから**] のドロップダウンリストから、[COUNTYNAME] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-303">In **From spatial dataset**, from the drop-down list, click COUNTYNAME.</span></span>  
  
8.  <span data-ttu-id="13681-304">[**分析データセットから**] のドロップダウンリストから [郡] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-304">In **From analytical dataset**, from the drop-down list, click [County].</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="13681-305">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-305">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-306">空間データ ソースおよび分析データセットから対応フィールドを指定することで、レポート プロセッサではマップ要素に基づいて分析データをグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="13681-306">By specifying a match field from the spatial data source and from the analytical dataset, you enable the report processor to group analytical data based on the map elements.</span></span> <span data-ttu-id="13681-307">データバインド マップ要素には、指定した値の適切な対応が含まれています。</span><span class="sxs-lookup"><span data-stu-id="13681-307">A data-bound map element has a successful match for the values that you specified.</span></span>  
  
 <span data-ttu-id="13681-308">店舗がある各郡には、ウィザードで選択したスタイルのカラー パレットに基づく色が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="13681-308">Each county that contains a store has a color that is based on the color palette for the style that you chose in the wizard.</span></span>  
  
###  <a name="6b-specify-color-rules-for-polygons"></a><a name="ColorRules"></a><span data-ttu-id="13681-309">6b.</span><span class="sxs-lookup"><span data-stu-id="13681-309">6b.</span></span> <span data-ttu-id="13681-310">多角形の色ルールを指定する</span><span class="sxs-lookup"><span data-stu-id="13681-310">Specify Color Rules for Polygons</span></span>  
 <span data-ttu-id="13681-311">各郡の色を店舗売上に基づいて変化させるルールを作成するには、範囲の値、その範囲内で表示する部分範囲の数、および使用する色を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13681-311">To create a rule that varies the color of each county based store sales, you must specify the range values, the number of divisions within that range that you want to display, and the colors to use.</span></span>  
  
##### <a name="to-specify-color-rules-for-all-polygons-that-have-associated-data"></a><span data-ttu-id="13681-312">データが関連付けられているすべての多角形の色ルールを指定するには</span><span class="sxs-lookup"><span data-stu-id="13681-312">To specify color rules for all polygons that have associated data</span></span>  
  
1.  <span data-ttu-id="13681-313">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-313">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-314">PolygonLayer1 の下矢印をクリックし、[**多角形の色のルール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-314">Click the down arrow on PolygonLayer1, and then click **Polygon Color Rule**.</span></span> <span data-ttu-id="13681-315">**[マップの色のルールのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-315">The **Map Color Rules Properties** dialog box opens.</span></span> <span data-ttu-id="13681-316">色ルールのオプションとして **[色パレットを使用してデータを表示する]** が選択されています。</span><span class="sxs-lookup"><span data-stu-id="13681-316">Notice that the color rule option **Visualize data by using color palette** is selected.</span></span> <span data-ttu-id="13681-317">このオプションは、ウィザードによって設定されたものです。</span><span class="sxs-lookup"><span data-stu-id="13681-317">This option was set by the wizard.</span></span>  
  
3.  <span data-ttu-id="13681-318">**[色の範囲を使用してデータを表示する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-318">Select **Visualize data by using color ranges**.</span></span> <span data-ttu-id="13681-319">パレット オプションが、開始色、中間色、および終了色のオプションで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="13681-319">The palette option is replaced by start color, middle color, and end color options.</span></span>  
  
4.  <span data-ttu-id="13681-320">郡の売上高について値の範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="13681-320">Define range values for sales per county.</span></span> <span data-ttu-id="13681-321">**[データ フィールド]** のドロップダウン リストで `[Sum(Sales)]`を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-321">In **Data field**, from the drop-down list, select `[Sum(Sales)]`.</span></span>  
  
5.  <span data-ttu-id="13681-322">通貨が 1,000 単位で表示されるようにするために、式を次のように変更します。 `=Sum(Fields!Sales.Value)/1000`</span><span class="sxs-lookup"><span data-stu-id="13681-322">To change the format to display currency in thousands, change the expression to the following: `=Sum(Fields!Sales.Value)/1000`</span></span>  
  
6.  <span data-ttu-id="13681-323">**[最初の色]** を **[赤]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="13681-323">Change **Start color** to **Red**.</span></span>  
  
7.  <span data-ttu-id="13681-324">**[最後の色]** を **[緑]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="13681-324">Change **End color** to **Green**.</span></span>  
  
     <span data-ttu-id="13681-325">**[赤]** は低い売上高、 **[黄]** は中程度の売上高、 **[緑]** は高い売上高を表します。</span><span class="sxs-lookup"><span data-stu-id="13681-325">**Red** represents low sales values, **Yellow** represents middle sales values, and **Green** represents high sales values.</span></span> <span data-ttu-id="13681-326">レポート プロセッサでは、これらの値と、 **[分布]** ページで選択したオプションに基づいて、色の範囲が計算されます。</span><span class="sxs-lookup"><span data-stu-id="13681-326">The report processor calculates a range of colors based on these values and the options that you choose on the **Distribution** page.</span></span>  
  
8.  <span data-ttu-id="13681-327">**[分布]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-327">Click **Distribution**.</span></span>  
  
9. <span data-ttu-id="13681-328">分布の種類が **[最適]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13681-328">Verify that the distribution type is **Optimal**.</span></span> <span data-ttu-id="13681-329">手順 5 の式の場合、最適な分布では、各範囲のアイテム数と各範囲の大きさとのバランスが取れるような部分範囲に値が分布されます。</span><span class="sxs-lookup"><span data-stu-id="13681-329">For the expression from step 5, optimal distribution divides the values into subranges that balance the number of items in each range and the span for each range.</span></span>  
  
10. <span data-ttu-id="13681-330">このページの他のオプションについては、既定の値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="13681-330">Accept the default values for other options on this page.</span></span> <span data-ttu-id="13681-331">最適な分布タイプを選択した場合は、レポートを実行すると部分範囲の数が計算されます。</span><span class="sxs-lookup"><span data-stu-id="13681-331">When you select the optimal distribution type, the number of subranges are calculated when the report runs.</span></span>  
  
11. <span data-ttu-id="13681-332">**[凡例]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-332">Click **Legend**.</span></span>  
  
12. <span data-ttu-id="13681-333">**[カラー スケールのオプション]** で、 **[カラー スケールに表示]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13681-333">In **Color scale options**, verify that **Show in color scale** is selected.</span></span>  
  
13. <span data-ttu-id="13681-334">**[この凡例に表示]** のドロップダウン リストで、空白行を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-334">In **Show in this legend**, from the drop-down list, select the blank line.</span></span> <span data-ttu-id="13681-335">ここでは、色の範囲をカラー スケールだけで表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-335">For now, you will show the color ranges only in the color scale.</span></span>  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="13681-336">カラー スケールには、赤、橙、黄、黄緑、緑の 5 色が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-336">The color scale displays five colors: red, orange, yellow, yellow green, and green.</span></span> <span data-ttu-id="13681-337">各色は、郡別の売上に基づいて自動的に計算された売上範囲を表しています。</span><span class="sxs-lookup"><span data-stu-id="13681-337">Each color represents a sales range that is automatically calculated based on the sales by county.</span></span>  
  
###  <a name="6c-format-the-data-in-the-color-scale-as-currency"></a><a name="ColorScale"></a><span data-ttu-id="13681-338">6c.</span><span class="sxs-lookup"><span data-stu-id="13681-338">6c.</span></span> <span data-ttu-id="13681-339">カラー スケールのデータを通貨形式に変更する</span><span class="sxs-lookup"><span data-stu-id="13681-339">Format the Data in the Color Scale as Currency</span></span>  
 <span data-ttu-id="13681-340">既定では、一般的な形式がデータに適用されますが、</span><span class="sxs-lookup"><span data-stu-id="13681-340">By default, data has a general format.</span></span> <span data-ttu-id="13681-341">形式をカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="13681-341">You can apply custom formats.</span></span>  
  
##### <a name="to-set-the-format-for-the-color-scale"></a><span data-ttu-id="13681-342">カラー スケールの形式を設定するには</span><span class="sxs-lookup"><span data-stu-id="13681-342">To set the format for the color scale</span></span>  
  
1.  <span data-ttu-id="13681-343">カラースケールを右クリックし、[**カラースケールのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-343">Right-click the color scale, and then click **Color Scale Properties**.</span></span>  
  
2.  <span data-ttu-id="13681-344">[**数値**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-344">Click **Number**.</span></span>  
  
3.  <span data-ttu-id="13681-345">[**カテゴリ**] で、[**通貨**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-345">In **Category**, click **Currency**.</span></span>  
  
4.  <span data-ttu-id="13681-346">[**小数点以下桁数**] に「 **0**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="13681-346">In **Decimal places**, type **0**.</span></span> <span data-ttu-id="13681-347">この形式は、通貨に小数点以下を表示しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="13681-347">This format specifies no decimal places for currency.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="13681-348">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-348">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-349">カラー スケールで、各範囲の年間売上高が通貨形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-349">The color scale displays annual sales in currency format for each range.</span></span>  
  
###  <a name="6d-create-a-new-legend"></a><a name="NewLegend"></a><span data-ttu-id="13681-350">6d.</span><span class="sxs-lookup"><span data-stu-id="13681-350">6d.</span></span> <span data-ttu-id="13681-351">新しい凡例を作成する</span><span class="sxs-lookup"><span data-stu-id="13681-351">Create a New Legend</span></span>  
 <span data-ttu-id="13681-352">既定では、すべてのルールが最初の凡例に表示されますが、</span><span class="sxs-lookup"><span data-stu-id="13681-352">By default, all rules display in the first legend.</span></span> <span data-ttu-id="13681-353">マップをより見やすく表示するために凡例を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="13681-353">To improve the display for a map, you can add legends.</span></span>  
  
 <span data-ttu-id="13681-354">既定の表示を変更するには、2 つの手順を実行する必要があります。まず新しい凡例を作成し、次に、その新しい凡例にマップ レイヤーのルールの結果を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="13681-354">To change the default display, there are two steps: create a new legend and then associate the rule results for a map layer with the new legend.</span></span>  
  
##### <a name="to-create-a-new-legend"></a><span data-ttu-id="13681-355">新しい凡例を作成するには</span><span class="sxs-lookup"><span data-stu-id="13681-355">To create a new legend</span></span>  
  
1.  <span data-ttu-id="13681-356">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-356">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-357">ビューポートの外側のマップを右クリックし、[**凡例の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-357">Right-click the map outside the viewport, and then click **Add Legend**.</span></span> <span data-ttu-id="13681-358">マップの既定の位置に凡例が追加されます。</span><span class="sxs-lookup"><span data-stu-id="13681-358">A new legend is added to the map at a default location.</span></span>  
  
3.  <span data-ttu-id="13681-359">凡例を右クリックし、[凡例の**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-359">Right-click the legend, and then click **Legend Properties**.</span></span>  
  
4.  <span data-ttu-id="13681-360">[**位置のオプション**] で、ビューポートを基準とする凡例の相対的な表示位置をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-360">In **Position options**, click the location that specifies where you want the legend to appear relative to the viewport.</span></span> <span data-ttu-id="13681-361">選択した位置に合わせてデザイン画面上のマップが変化します。</span><span class="sxs-lookup"><span data-stu-id="13681-361">The map on the design surface changes to show the effect of your selections.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="13681-362">凡例の [**タイトル**] をクリックして、凡例のタイトルを選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-362">Click **Title** on the legend to select the legend title.</span></span>  
  
7.  <span data-ttu-id="13681-363">[**タイトル**] をもう一度クリックして、テキストの挿入モードに入ります。</span><span class="sxs-lookup"><span data-stu-id="13681-363">Click **Title** again to enter insert mode for the text.</span></span> <span data-ttu-id="13681-364">[**タイトル**] を「 **Sales (千)**」に置き換え、テキストの外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-364">Replace **Title** by **Sales (Thousands)**, and then click outside the text.</span></span>  
  
 <span data-ttu-id="13681-365">タイトルが表示されるように凡例が拡張されます。</span><span class="sxs-lookup"><span data-stu-id="13681-365">The legend expands to display the title.</span></span>  
  
###  <a name="6e-associate-legend-and-color-rules"></a><a name="Associate"></a><span data-ttu-id="13681-366">6e.</span><span class="sxs-lookup"><span data-stu-id="13681-366">6e.</span></span> <span data-ttu-id="13681-367">凡例と色ルールを関連付ける</span><span class="sxs-lookup"><span data-stu-id="13681-367">Associate Legend and Color Rules</span></span>  
 <span data-ttu-id="13681-368">各凡例には、ルールの結果セットを 1 つ以上表示できます。</span><span class="sxs-lookup"><span data-stu-id="13681-368">Each legend can display one or more sets of rule results.</span></span>  
  
##### <a name="to-associate-a-legend-with-color-rules"></a><span data-ttu-id="13681-369">凡例を色ルールに関連付けるには</span><span class="sxs-lookup"><span data-stu-id="13681-369">To associate a legend with color rules</span></span>  
  
1.  <span data-ttu-id="13681-370">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-370">Double-click the map to display the **Map Layer** pane.</span></span>  
  
2.  <span data-ttu-id="13681-371">PolygonLayer1 の下矢印をクリックし、[**多角形の色のルール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-371">Click the down arrow on PolygonLayer1, and then click **Polygon Color Rule**.</span></span> <span data-ttu-id="13681-372">**[マップの色のルールのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-372">The **Map Color Rules Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="13681-373">**[凡例]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-373">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="13681-374">[**カラースケールのオプション**] で、[**カラースケールに表示]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="13681-374">In **Color scale options**, clear **Show in color scale**.</span></span>  
  
5.  <span data-ttu-id="13681-375">[**凡例のオプション**] のドロップダウンリストから、[Legend2] を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-375">In **Legend options**, from the drop-down list, select Legend2.</span></span> <span data-ttu-id="13681-376">凡例テキストのオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-376">The legend text option appears.</span></span> <span data-ttu-id="13681-377">既定では、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] の一般的な書式設定文字列が凡例テキストに対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="13681-377">By default, legend text is formatted with a general [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] format string.</span></span> <span data-ttu-id="13681-378">N0 の 0 は、小数部がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="13681-378">The 0 in N0 specifies no decimal digits.</span></span>  
  
6.  <span data-ttu-id="13681-379">[**凡例のテキスト**] で、次の書式を使用して、10進数を含まない通貨を指定します。`#FROMVALUE {C0} - #TOVALUE {C0}`</span><span class="sxs-lookup"><span data-stu-id="13681-379">In **Legend text**, use the following format to specify currency with no decimal digits: `#FROMVALUE {C0} - #TOVALUE {C0}`</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="13681-380">デザイン画面で、通貨形式のサンプル データを含む色の範囲が凡例に表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-380">On the design surface, the legend displays the color ranges with sample data formatted as currency.</span></span>  
  
8.  <span data-ttu-id="13681-381">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-381">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-382">店舗と売上が関連付けられている郡が、色のルールに従って表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-382">The counties that have associated stores and sales display according to the color rules.</span></span> <span data-ttu-id="13681-383">売上が関連付けられていない郡の色はありません。</span><span class="sxs-lookup"><span data-stu-id="13681-383">Counties that have no sales have no color.</span></span>  
  
###  <a name="6f-change-color-for-counties-with-no-data"></a><a name="NoData"></a><span data-ttu-id="13681-384">6f.</span><span class="sxs-lookup"><span data-stu-id="13681-384">6f.</span></span> <span data-ttu-id="13681-385">データがない郡の色を変更する</span><span class="sxs-lookup"><span data-stu-id="13681-385">Change Color for Counties with No Data</span></span>  
 <span data-ttu-id="13681-386">レイヤー上のすべてのマップ要素の既定の表示オプションを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="13681-386">You can set the default display options for all map elements on a layer.</span></span> <span data-ttu-id="13681-387">これらの表示オプションよりも色ルールが優先されます。</span><span class="sxs-lookup"><span data-stu-id="13681-387">Color rules take precedence over these display options.</span></span>  
  
##### <a name="to-set-the-display-properties-for-all-elements-on-a-layer"></a><span data-ttu-id="13681-388">レイヤー上のすべての要素に対して表示プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="13681-388">To set the display properties for all elements on a layer</span></span>  
  
1.  <span data-ttu-id="13681-389">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-389">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-390">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-390">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="13681-391">PolygonLayer1 の下向き矢印をクリックし、 **[多角形のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-391">Click the down arrow on PolygonLayer1, and then click **Polygon Properties**.</span></span> <span data-ttu-id="13681-392">**[マップの多角形のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-392">The **Map Polygon Properties** dialog box opens.</span></span> <span data-ttu-id="13681-393">このダイアログ ボックスで設定した表示オプションは、ルールに基づく表示オプションが適用される前にレイヤー上のすべての多角形に適用されます。</span><span class="sxs-lookup"><span data-stu-id="13681-393">Display options set in this dialog box apply to all polygons on the layer before rule-based display options are applied.</span></span>  
  
4.  <span data-ttu-id="13681-394">[**塗りつぶし**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-394">Click **Fill**.</span></span>  
  
5.  <span data-ttu-id="13681-395">塗りつぶしのスタイルが実線であることを確認し**ます。**</span><span class="sxs-lookup"><span data-stu-id="13681-395">Verify that the fill style is **Solid.**</span></span> <span data-ttu-id="13681-396">になっていることを確認します。グラデーションやパターンはすべての色に適用されます。</span><span class="sxs-lookup"><span data-stu-id="13681-396">Gradients and patterns apply to all colors.</span></span>  
  
6.  <span data-ttu-id="13681-397">[**色**] で、下矢印をクリックし、[**薄いスチール Blue**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-397">In **Color**, click the down arrow, and then click **Light Steel Blue**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="13681-398">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-398">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-399">データが関連付けられていない郡が青で表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-399">Counties that have no associated data display as blue.</span></span> <span data-ttu-id="13681-400">指定した色ルールの**赤**から**緑**の色で、分析データが関連付けられている郡のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-400">Only counties that have associated analytical data appear in the **Red** through **Green** colors from the color rules that you specified.</span></span>  
  
##  <a name="7-add-a-custom-point"></a><a name="CustomPoint"></a><span data-ttu-id="13681-401">7. カスタムポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="13681-401">7. Add a Custom Point</span></span>  
 <span data-ttu-id="13681-402">まだ構築されていない新しいストアを表すには、ポイントを指定し、**画鋲**マーカーの種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="13681-402">To represent a new store that has not yet been built, specify a point and use the **PushPin** marker type.</span></span>  
  
#### <a name="to-add-a-custom-point"></a><span data-ttu-id="13681-403">カスタム ポイントを追加するには</span><span class="sxs-lookup"><span data-stu-id="13681-403">To add a custom point</span></span>  
  
1.  <span data-ttu-id="13681-404">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-404">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-405">マップをダブルクリックして **[マップ レイヤー]** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="13681-405">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="13681-406">ツールバーの [**レイヤーの追加**] をクリックし、[**ポイントレイヤー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-406">On the toolbar, click **Add Layer**, and then click **Point Layer**.</span></span>  
  
     <span data-ttu-id="13681-407">新しいポイント レイヤーがマップに追加されます。</span><span class="sxs-lookup"><span data-stu-id="13681-407">A new point layer is added to the map.</span></span> <span data-ttu-id="13681-408">既定では、ポイント レイヤーの空間データの種類は **[埋め込み]** になります。</span><span class="sxs-lookup"><span data-stu-id="13681-408">By default, the point layer has spatial data type **Embedded**.</span></span>  
  
3.  <span data-ttu-id="13681-409">PointLayer2 の下矢印をクリックし、[**ポイントの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-409">Click the down arrow on PointLayer2, and then click **Add Point**.</span></span>  
  
4.  <span data-ttu-id="13681-410">マップ ビューポートにポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="13681-410">Move the pointer over the map viewport.</span></span> <span data-ttu-id="13681-411">カーソルが十字に変化します。</span><span class="sxs-lookup"><span data-stu-id="13681-411">The cursor changes to crosshairs.</span></span>  
  
5.  <span data-ttu-id="13681-412">マップ上でポイントを追加する場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-412">Click the location on the map where you want to add a point.</span></span> <span data-ttu-id="13681-413">このチュートリアルでは、ルートの始点の隣の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-413">In this tutorial, click a location in a county next to the start of the route.</span></span> <span data-ttu-id="13681-414">レイヤー上のクリックした場所に、円で示されるポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="13681-414">A point marked by a circle is added to the layer at the location where you clicked.</span></span> <span data-ttu-id="13681-415">既定では、ポイントが選択された状態になります。</span><span class="sxs-lookup"><span data-stu-id="13681-415">By default, the point is selected.</span></span>  
  
6.  <span data-ttu-id="13681-416">追加したポイントを右クリックし、 **[埋め込みポイントのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-416">Right-click the point you added, and then click **Embedded Point Properties**.</span></span>  
  
7.  <span data-ttu-id="13681-417">[**このレイヤーのポイントオプションを上書き**する] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-417">Select the option **Override point options for this layer**.</span></span> <span data-ttu-id="13681-418">ダイアログ ボックスに追加のページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-418">Additional pages appear in the dialog box.</span></span> <span data-ttu-id="13681-419">ここで設定したオプションは、レイヤーまたは色ルールの表示オプションよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="13681-419">Values that you set here take precedence over display options for the layer or for color rules.</span></span>  
  
8.  <span data-ttu-id="13681-420">[**マーカー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-420">Click **Marker**.</span></span>  
  
9. <span data-ttu-id="13681-421">[**マーカーの種類**] で [**星**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="13681-421">For **Marker type**, select **Star**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="13681-422">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-422">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-423">追加した新しいポイントは、**星形**で表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-423">The new point you added appears as a **Star**.</span></span>  
  
#### <a name="to-add-a-label-for-the-custom-point"></a><span data-ttu-id="13681-424">カスタム ポイントに対してラベルを追加するには</span><span class="sxs-lookup"><span data-stu-id="13681-424">To add a label for the custom point</span></span>  
  
1.  <span data-ttu-id="13681-425">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-425">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-426">追加したポイントを右クリックし、[**埋め込みポイントのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-426">Right-click the point you just added, and then click **Embedded Point Properties**.</span></span>  
  
3.  <span data-ttu-id="13681-427">[**ラベル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-427">Click **Labels**.</span></span>  
  
4.  <span data-ttu-id="13681-428">[**ラベルのテキスト**] に「 **New Store**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="13681-428">In **Label text**, type **New Store**.</span></span>  
  
5.  <span data-ttu-id="13681-429">**[位置]** で **[上]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-429">In **Placement**, click **Top**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="13681-430">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-430">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-431">店舗の場所の上にラベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-431">The label appears above the store location.</span></span>  
  
##  <a name="center-the-map-view"></a><a name="CenterView"></a><span data-ttu-id="13681-432">マップビューの中央揃え</span><span class="sxs-lookup"><span data-stu-id="13681-432">Center the Map View</span></span>  
 <span data-ttu-id="13681-433">マップ ビューポートの中心とズーム レベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="13681-433">Change the map viewport center and zoom level.</span></span>  
  
#### <a name="to-change-the-viewport"></a><span data-ttu-id="13681-434">ビューポートを変更するには</span><span class="sxs-lookup"><span data-stu-id="13681-434">To change the viewport</span></span>  
  
1.  <span data-ttu-id="13681-435">マップビューポートを右クリックし、[**ビューポートのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-435">Right-click the map viewport, and then click **Viewport Properties**.</span></span>  
  
2.  <span data-ttu-id="13681-436">[**中心とズーム] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-436">Click **Center and Zoom**.</span></span>  
  
3.  <span data-ttu-id="13681-437">[**ビューの中心とズームレベルを設定**する] オプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13681-437">Verify that the option **Set a view center and zoom level** is selected.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="13681-438">マップ ビューポートをクリックして、ビューポートの中心を目的の場所までドラッグします。</span><span class="sxs-lookup"><span data-stu-id="13681-438">Left-click the map viewport, and drag the center of the viewport to the location that you want.</span></span>  
  
6.  <span data-ttu-id="13681-439">マウス ホイールを使用してビューポートのズーム レベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="13681-439">Use the mouse wheel to change the zoom level of the viewport.</span></span>  
  
7.  <span data-ttu-id="13681-440">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="13681-440">Preview the report.</span></span>  
  
 <span data-ttu-id="13681-441">デザイン ビューでは、デザイン画面やビューのマップはサンプル データに基づいています。</span><span class="sxs-lookup"><span data-stu-id="13681-441">In Design view, the map on the display surface and the view is based on sample data.</span></span> <span data-ttu-id="13681-442">表示されたレポートでは、指定したビューがマップ ビューの中心になります。</span><span class="sxs-lookup"><span data-stu-id="13681-442">In the rendered report, the map view is centered on the view that you specified.</span></span>  
  
##  <a name="add-a-report-title"></a><a name="Title"></a><span data-ttu-id="13681-443">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="13681-443">Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="13681-444">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="13681-444">To add a report title</span></span>  
  
1.  <span data-ttu-id="13681-445">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-445">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="13681-446">「 **Sales in New York Stores** 」と入力し、テキスト ボックスの外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-446">Type **Sales in New York Stores** and then click outside the text box.</span></span>  
  
 <span data-ttu-id="13681-447">このタイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="13681-447">This title will appear at the top of the report.</span></span> <span data-ttu-id="13681-448">ページ ヘッダーが定義されていない場合は、レポート本文の最上部にあるアイテムがレポート ヘッダーに相当します。</span><span class="sxs-lookup"><span data-stu-id="13681-448">Items at the top of the report body when there is no page header defined are the equivalent of a report header.</span></span>  
  
##  <a name="save-the-report"></a><a name="Save"></a><span data-ttu-id="13681-449">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="13681-449">Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="13681-450">レポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="13681-450">To save the report</span></span>  
  
1.  <span data-ttu-id="13681-451">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13681-451">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="13681-452">レポート ビルダー のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-452">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="13681-453">**[名前]** に、「 **Store Sales in New York**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="13681-453">In **Name**, type **Store Sales in New York**.</span></span>  
  
 <span data-ttu-id="13681-454">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13681-454">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="13681-455">次の手順</span><span class="sxs-lookup"><span data-stu-id="13681-455">Next Steps</span></span>  
 <span data-ttu-id="13681-456">これで、レポートにマップを追加する方法のチュートリアルは終了です。</span><span class="sxs-lookup"><span data-stu-id="13681-456">This concludes the walkthrough for how to add a map to your report.</span></span>  
  
 <span data-ttu-id="13681-457">詳細については、「 [Maps &#40;レポートビルダーと SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) 」と「blogs.msdn.com 上の[SQL Server Reporting Services の空間データの地図調整](https://go.microsoft.com/fwlink/?LinkId=152771)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13681-457">For more information, see [Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) and the blog entry [Cartographic Adjustment of Spatial Data for SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=152771) on blogs.msdn.com.</span></span>  
  
 <span data-ttu-id="13681-458">詳細については、「[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13681-458">For more tutorials, see [Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13681-459">参照</span><span class="sxs-lookup"><span data-stu-id="13681-459">See Also</span></span>  
 <span data-ttu-id="13681-460">[チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="13681-460">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="13681-461">[SQL Server 2014 のレポートビルダー](report-builder/report-builder-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="13681-461">[Report Builder in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="13681-462">[マップウィザードとマップレイヤーウィザード &#40;レポートビルダーと SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="13681-462">[Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="13681-463">ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="13681-463">Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
