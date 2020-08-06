---
title: '[全般] ([マップビューポートのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d760d6a0572cbbd1bd948eab382c0727eb276c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631640"
---
# <a name="map-viewport-properties-dialog-box-general"></a><span data-ttu-id="20811-102">[全般] ([マップ ビューポートのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="20811-102">Map Viewport Properties Dialog Box, General</span></span>
  <span data-ttu-id="20811-103">**[マップ ビューポートのプロパティ]** ダイアログ ボックスの **[全般]** を選択すると、座標系、投影法、および境界に関するオプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="20811-103">Select **General** on the **Map Viewport Properties** dialog box to change the coordinate system, the projection, and the boundary options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="20811-104">Options</span><span class="sxs-lookup"><span data-stu-id="20811-104">Options</span></span>  
 <span data-ttu-id="20811-105">**座標系**</span><span class="sxs-lookup"><span data-stu-id="20811-105">**Coordinate system**</span></span>  
 <span data-ttu-id="20811-106">マップ データで使用する座標系の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="20811-106">Indicate the type of coordinate system that the map data uses.</span></span>  
  
-   <span data-ttu-id="20811-107">**[平面]** たとえば、建築計画のようにマップ データが XY 座標で表されている場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20811-107">**Planar** Choose this option when map data is in X and Y coordinates, for example, for building plans.</span></span>  
  
-   <span data-ttu-id="20811-108">**[地理]** たとえば、市区町村の場所のようにマップ データが経度/緯度座標で表されている場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20811-108">**Geographic** Choose this option when map data is in longitude and latitude coordinates, for example, for city locations.</span></span>  
  
 <span data-ttu-id="20811-109">**射影**</span><span class="sxs-lookup"><span data-stu-id="20811-109">**Projection**</span></span>  
 <span data-ttu-id="20811-110">地理的座標を 2 次元表面に投影する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="20811-110">Specify the method to use to project geographic coordinates onto a two-dimensional surface.</span></span> <span data-ttu-id="20811-111">視覚化対象のデータと互換性のある投影法を選択してください。</span><span class="sxs-lookup"><span data-stu-id="20811-111">Choose a projection that is compatible with the data that you are visualizing.</span></span> <span data-ttu-id="20811-112">投影法の影響を受ける 4 つの空間プロパティは、領域、形状、距離、および方向です。</span><span class="sxs-lookup"><span data-stu-id="20811-112">The four spatial properties that are affected by projection are area, shape, distance, and direction.</span></span> <span data-ttu-id="20811-113">地球の表示に関して適切な投影法を選択できるかどうかは、中心ビュー、マップの境界、および拡大 (縮小) 率に依存します。</span><span class="sxs-lookup"><span data-stu-id="20811-113">For views of the earth, a good choice of projection depends on the center view, the map boundaries, and the zoom factor.</span></span>  
  
 <span data-ttu-id="20811-114">以下の各投影法では、1 つ以上のこれらの空間プロパティが維持されます。</span><span class="sxs-lookup"><span data-stu-id="20811-114">Each of the following projections preserves one or more of these spatial properties:</span></span>  
  
-   <span data-ttu-id="20811-115">**[Equirectangular]** 経度と緯度を直交座標として使用するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20811-115">**Equirectangular** Choose this option to use longitude and latitude as rectangular coordinates.</span></span>  
  
-   <span data-ttu-id="20811-116">**[Mercator]** 一般的な投影法であり、狭い領域に適していて、赤道周辺の歪みを小さく抑えることができます。また、この投影法は、メルカトル投影法が使用されている既存のタイル レイヤーにマップ レイヤーを追加する場合にも使用します。</span><span class="sxs-lookup"><span data-stu-id="20811-116">**Mercator** Choose this popular projection for smaller areas, for less distortion around the equator, or when you want to add a map layer with an existing tile layer that uses the Mercator projection.</span></span>  
  
-   <span data-ttu-id="20811-117">**[Robinson]** このオプションを選択すると、赤道から極地までの広い領域の歪みを小さく抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="20811-117">**Robinson** Choose this option for less distortion of large areas that span from the equator to the poles.</span></span> <span data-ttu-id="20811-118">Arthur H. Robinson によって 1963 年に考案された方法です。</span><span class="sxs-lookup"><span data-stu-id="20811-118">Developed by Arthur H. Robinson in 1963.</span></span>  
  
-   <span data-ttu-id="20811-119">**[Fahey]** このオプションを選択すると、赤道から極地までの広い領域の歪みを小さく抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="20811-119">**Fahey** Choose this option for less distortion of large areas that span from the equator to the poles.</span></span> <span data-ttu-id="20811-120">Lawrence Fahey によって 1975 年に考案された方法です。</span><span class="sxs-lookup"><span data-stu-id="20811-120">Developed by Lawrence Fahey in 1975.</span></span>  
  
-   <span data-ttu-id="20811-121">**[Eckert1]** このオプションを選択した場合、緯線に平行直線が使用され、経線に直線が使用されます。</span><span class="sxs-lookup"><span data-stu-id="20811-121">**Eckert1** Choose this option to use equally spaced parallels in latitude and straight lines for meridians in longitude.</span></span>  
  
-   <span data-ttu-id="20811-122">**[Eckert3]** このオプションを選択した場合、緯線に平行直線が使用され、経線に曲線が使用されます。</span><span class="sxs-lookup"><span data-stu-id="20811-122">**Eckert3** Choose this option to use equally spaced parallels in latitude and curved lines for meridians in longitude.</span></span>  
  
-   <span data-ttu-id="20811-123">**[HammerAitoff]** このオプションは、極地の地図や世界地図に使用します。</span><span class="sxs-lookup"><span data-stu-id="20811-123">**HammerAitoff** Choose this option for polar maps or world maps.</span></span>  
  
-   <span data-ttu-id="20811-124">**[Wagner3]** このオプションは、世界地図に使用します。</span><span class="sxs-lookup"><span data-stu-id="20811-124">**Wagner3** Choose this option for world maps.</span></span>  
  
-   <span data-ttu-id="20811-125">**[Bonne]** 地図帳でよく見かけるような世界地図を表示するには、このオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="20811-125">**Bonne** Choose this option to view the world as it appears in an atlas.</span></span>  
  
 <span data-ttu-id="20811-126">**[改ページのオプション]**</span><span class="sxs-lookup"><span data-stu-id="20811-126">**Page break options**</span></span>  
 <span data-ttu-id="20811-127">コンテンツをレポート ページにどのように収めるかを指定するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20811-127">Select options to indicate how content is fitted to a report page.</span></span>  
  
 <span data-ttu-id="20811-128">**[境界オプション]**</span><span class="sxs-lookup"><span data-stu-id="20811-128">**Boundary options**</span></span>  
 <span data-ttu-id="20811-129">座標の下限および上限を指定して、レポートに表示するマップを制御します。</span><span class="sxs-lookup"><span data-stu-id="20811-129">Specify the lower and upper boundaries for coordinates to control which part of the map appears in the report.</span></span>  
  
 <span data-ttu-id="20811-130">**[X の最小値]**</span><span class="sxs-lookup"><span data-stu-id="20811-130">**Minimum X**</span></span>  
 <span data-ttu-id="20811-131">最小の X 値です。</span><span class="sxs-lookup"><span data-stu-id="20811-131">Lowest X value.</span></span> <span data-ttu-id="20811-132">**[平面]** に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20811-132">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="20811-133">**[X の最大値]**</span><span class="sxs-lookup"><span data-stu-id="20811-133">**Maximum X**</span></span>  
 <span data-ttu-id="20811-134">最大の X 値です。</span><span class="sxs-lookup"><span data-stu-id="20811-134">Highest X value.</span></span> <span data-ttu-id="20811-135">**[平面]** に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20811-135">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="20811-136">**[Y の最小値]**</span><span class="sxs-lookup"><span data-stu-id="20811-136">**Minimum Y**</span></span>  
 <span data-ttu-id="20811-137">最小の Y 値です。</span><span class="sxs-lookup"><span data-stu-id="20811-137">Lowest Y value.</span></span> <span data-ttu-id="20811-138">**[平面]** に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20811-138">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="20811-139">**[Y の最大値]**</span><span class="sxs-lookup"><span data-stu-id="20811-139">**Maximum Y**</span></span>  
 <span data-ttu-id="20811-140">最大の Y 値です。</span><span class="sxs-lookup"><span data-stu-id="20811-140">Highest Y value.</span></span> <span data-ttu-id="20811-141">**[平面]** に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20811-141">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="20811-142">**[最小経度]**</span><span class="sxs-lookup"><span data-stu-id="20811-142">**Minimum Longitude**</span></span>  
 <span data-ttu-id="20811-143">最小経度です。</span><span class="sxs-lookup"><span data-stu-id="20811-143">Lowest longitude value.</span></span> <span data-ttu-id="20811-144">**[地理]** に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20811-144">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="20811-145">**[最大経度]**</span><span class="sxs-lookup"><span data-stu-id="20811-145">**Maximum Longitude**</span></span>  
 <span data-ttu-id="20811-146">最大経度です。</span><span class="sxs-lookup"><span data-stu-id="20811-146">Highest longitude value.</span></span> <span data-ttu-id="20811-147">**[地理]** に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20811-147">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="20811-148">**[最小緯度]**</span><span class="sxs-lookup"><span data-stu-id="20811-148">**Minimum Latitude**</span></span>  
 <span data-ttu-id="20811-149">最小緯度です。</span><span class="sxs-lookup"><span data-stu-id="20811-149">Lowest latitude value.</span></span> <span data-ttu-id="20811-150">**[地理]** に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20811-150">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="20811-151">**[最大緯度]**</span><span class="sxs-lookup"><span data-stu-id="20811-151">**Maximum Latitude**</span></span>  
 <span data-ttu-id="20811-152">最大緯度です。</span><span class="sxs-lookup"><span data-stu-id="20811-152">Highest latitude value.</span></span> <span data-ttu-id="20811-153">**[地理]** に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20811-153">Available for **Geographic** only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20811-154">参照</span><span class="sxs-lookup"><span data-stu-id="20811-154">See Also</span></span>  
 [<span data-ttu-id="20811-155">マップ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="20811-155">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
