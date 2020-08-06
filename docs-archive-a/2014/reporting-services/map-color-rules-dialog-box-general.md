---
title: '[全般] ([マップの色のルール] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10541"
- sql12.rtp.rptdesigner.shared.mapcolorrulesgeneral.f1
ms.assetid: 14ff5fc1-4cf8-4a45-9d98-47a1bf1c52c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0dffc6c0b31400cb4eb9cecbbada1a52f8f41443
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644830"
---
# <a name="map-color-rules-dialog-box-general"></a><span data-ttu-id="84ff6-102">[全般] ([マップの色のルールのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="84ff6-102">Map Color Rules Dialog Box, General</span></span>
  <span data-ttu-id="84ff6-103">**[マップの色のルールのプロパティ]** ダイアログ ボックスの **[全般]** を選択すると、このレイヤー上のマップ要素の色オプションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="84ff6-103">Select **General** on the **Color Rules Properties** dialog box to define color options for map elements on this layer.</span></span> <span data-ttu-id="84ff6-104">マップ要素には、多角形、線、およびポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="84ff6-104">Map elements include polygons, lines, and points.</span></span> <span data-ttu-id="84ff6-105">データセット フィールドまたは空間データ ソース フィールドからの空間データと分析データに基づいてマップ要素間のリレーションシップを作成している場合に、色ルールを適用できます。</span><span class="sxs-lookup"><span data-stu-id="84ff6-105">Color rules can be applied when you have created a relationship between map elements based on spatial data and analytical data from a dataset field or from a spatial data source field.</span></span>  
  
 <span data-ttu-id="84ff6-106">基本の色と 2 番目の色に異なる色を使用する装飾用のグラデーションを指定して、レイヤー上のすべてのマップ要素を表示するには、[マップの多角形のプロパティ] ダイアログ ボックスの **[塗りつぶし]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-106">To display all map elements on a layer by specifying a decorative gradient with different primary and secondary colors, use the **Fill** page of the Map Polygon Properties Dialog Box.</span></span> <span data-ttu-id="84ff6-107">色ルールはレイヤーの表示プロパティよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="84ff6-107">Color rules take precedence over display properties for a layer.</span></span> <span data-ttu-id="84ff6-108">詳細については、「[マップまたはマップ レイヤーのデータと表示のカスタマイズ (レポート ビルダーおよび SSRS)](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84ff6-108">For more information, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="84ff6-109">Options</span><span class="sxs-lookup"><span data-stu-id="84ff6-109">Options</span></span>  
 <span data-ttu-id="84ff6-110">**[テンプレート スタイルを適用する]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-110">**Apply template style**</span></span>  
 <span data-ttu-id="84ff6-111">ウィザードで選択したテーマか、多角形、線、またはポイント レイヤーのプロパティで設定したテーマに基づく色を使用します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-111">Select this option to use color based on the theme that was chosen in the wizard or set in the Polygon, Line, or Point layer properties.</span></span> <span data-ttu-id="84ff6-112">テーマを適用すると、マップの色、フォント、および罫線に対して既定のオプションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="84ff6-112">A theme sets default options for color, font, and borders for the map.</span></span> <span data-ttu-id="84ff6-113">このオプションを選択した場合、各マップ要素に色を割り当てるルールは適用されません。</span><span class="sxs-lookup"><span data-stu-id="84ff6-113">For this option, no rule is applied to assign colors to each map element.</span></span>  
  
 <span data-ttu-id="84ff6-114">**[色パレットを使用してデータを表示する]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-114">**Visualize data by using color palette**</span></span>  
 <span data-ttu-id="84ff6-115">特定のカラー パレットの色を使用して、分析データを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-115">Select this option to visualize analytical data by using colors from a specific color palette.</span></span>  
  
 <span data-ttu-id="84ff6-116">**[色の範囲を使用してデータを表示する]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-116">**Visualize data by using color ranges**</span></span>  
 <span data-ttu-id="84ff6-117">各マップ要素の色の範囲を使用して、分析データを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-117">Select this option to visualize analytical data by using a range of colors for each map element.</span></span> <span data-ttu-id="84ff6-118">たとえば、赤を開始色、黄を中間の色、緑を終了色として指定した場合、範囲の下限の値は赤、範囲の中間の値は黄、範囲の上限の値は緑になります。</span><span class="sxs-lookup"><span data-stu-id="84ff6-118">For example, when you specify Red as a start color, Yellow as a middle color, and Green as an end color, values in the low range are Red, values in the middle range are Yellow, and values in the top range are Green.</span></span>  
  
 <span data-ttu-id="84ff6-119">**[作成した色を使用してデータを表示する]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-119">**Visualize data by using custom colors**</span></span>  
 <span data-ttu-id="84ff6-120">独自の色のリストを指定して、分析データを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-120">Select this option to visualize analytical data by specifying your own list of colors.</span></span>  
  
 <span data-ttu-id="84ff6-121">**[データ フィールド]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-121">**Data field**</span></span>  
 <span data-ttu-id="84ff6-122">このオプションは、いずれかのデータ視覚化オプションを選択した場合に表示されます。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="84ff6-122">This option appears when you select one of the **Visualize data** options.</span></span>  
  
 <span data-ttu-id="84ff6-123">使用する分析データ フィールドをドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-123">Select the analytical data field to use from the drop-down list.</span></span> <span data-ttu-id="84ff6-124">リストには、空間データのソースに応じて、空間データ ソースからのフィールドと、空間データと分析データ間のリレーションシップを持つレポート データセットからのフィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84ff6-124">Depending on the source of spatial data, the list displays fields from the spatial data source and from a report dataset that has a relationship between the spatial data and analytical data.</span></span> <span data-ttu-id="84ff6-125">このようなリレーションシップを作成するには、選択したマップ レイヤーの [分析データ] ページでデータ オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-125">To create such a relationship, set the data options on the Analytical Data page for the selected map layer.</span></span>  
  
 <span data-ttu-id="84ff6-126">**スロープ**</span><span class="sxs-lookup"><span data-stu-id="84ff6-126">**Palette**</span></span>  
 <span data-ttu-id="84ff6-127">カラー パレットの名前を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-127">Type or select the name of the color palette.</span></span>  
  
 <span data-ttu-id="84ff6-128">**[開始色]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-128">**Start color**</span></span>  
 <span data-ttu-id="84ff6-129">データ範囲の下限のデータに使用する色を指定します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-129">Specify the color to use for data at the low end of the data range.</span></span>  
  
 <span data-ttu-id="84ff6-130">**[中間の色]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-130">**Middle color**</span></span>  
 <span data-ttu-id="84ff6-131">データ範囲の中間のデータに使用する色を指定します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-131">Specify the color to use for data in the middle of the data range.</span></span> <span data-ttu-id="84ff6-132">この範囲を削除するには、 **[色なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-132">Select **No Color** to remove this range.</span></span>  
  
 <span data-ttu-id="84ff6-133">**[終了色]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-133">**End color**</span></span>  
 <span data-ttu-id="84ff6-134">データ範囲の上限のデータに使用する色を指定します。</span><span class="sxs-lookup"><span data-stu-id="84ff6-134">Specify the color to use for data at the high end of the data range.</span></span>  
  
 <span data-ttu-id="84ff6-135">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="84ff6-135">**Add**</span></span>  
 <span data-ttu-id="84ff6-136">色ルールの独自の色を指定するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84ff6-136">Click **Add** to specify your own colors for the color rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ff6-137">参照</span><span class="sxs-lookup"><span data-stu-id="84ff6-137">See Also</span></span>  
 <span data-ttu-id="84ff6-138">[マップ &#40;レポート ビルダーおよび SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="84ff6-138">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="84ff6-139">マップの凡例、カラー スケール、および関連付けられているルールの変更 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84ff6-139">Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;</span></span>](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
