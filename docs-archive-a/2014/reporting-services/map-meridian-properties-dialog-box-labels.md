---
title: '[ラベル] ([マップの経線のプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapmeridianproperties.labels.f1
- "10518"
ms.assetid: 47650a82-3b0c-4e32-8565-e9332bdcf4d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 146e2062185b4b4cd07ab791bd7552e9fd0064cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741553"
---
# <a name="map-meridian-properties-dialog-box-labels"></a><span data-ttu-id="074ca-102">[ラベル] ([マップの経線のプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="074ca-102">Map Meridian Properties Dialog Box, Labels</span></span>
  <span data-ttu-id="074ca-103">[ **MapMeridian のプロパティ**] ダイアログボックスを使用すると、マップビューポートの垂直グリッドのラベルオプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="074ca-103">Use the **MapMeridian Properties** dialog box to change label options for the vertical grid in the map viewport.</span></span> <span data-ttu-id="074ca-104">経線は、ビューポートに指定された座標系に応じて、次の値を表します。</span><span class="sxs-lookup"><span data-stu-id="074ca-104">A meridian represents the following value depending on the specified coordinate system for the viewport:</span></span>  
  
-   <span data-ttu-id="074ca-105">**平面**。</span><span class="sxs-lookup"><span data-stu-id="074ca-105">**Planar**.</span></span> <span data-ttu-id="074ca-106">Y 座標。</span><span class="sxs-lookup"><span data-stu-id="074ca-106">The Y coordinate.</span></span>  
  
-   <span data-ttu-id="074ca-107">**地理的**。</span><span class="sxs-lookup"><span data-stu-id="074ca-107">**Geographic**.</span></span> <span data-ttu-id="074ca-108">現在の投影法での緯度。</span><span class="sxs-lookup"><span data-stu-id="074ca-108">The longitude for the current projection.</span></span>  
  
 <span data-ttu-id="074ca-109">**式** ([fx]) ボタンをクリックし、オプションの値を設定する式を編集します。\*\*</span><span class="sxs-lookup"><span data-stu-id="074ca-109">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="074ca-110">Options</span><span class="sxs-lookup"><span data-stu-id="074ca-110">Options</span></span>  
 <span data-ttu-id="074ca-111">**間隔**</span><span class="sxs-lookup"><span data-stu-id="074ca-111">**Interval**</span></span>  
 <span data-ttu-id="074ca-112">経線間の間隔を指定する度数を整数値で入力します。</span><span class="sxs-lookup"><span data-stu-id="074ca-112">Type an integer value in degrees that specifies the interval between meridians.</span></span> <span data-ttu-id="074ca-113">既定では、 **[自動]** が選択されます。</span><span class="sxs-lookup"><span data-stu-id="074ca-113">By default, **Auto** is selected.</span></span> <span data-ttu-id="074ca-114">**[自動]** は、値が空間データによって自動的に決定されることを示します。</span><span class="sxs-lookup"><span data-stu-id="074ca-114">**Auto** indicates that value is automatically determined by spatial data.</span></span>  
  
 <span data-ttu-id="074ca-115">**[ラベルを表示]**</span><span class="sxs-lookup"><span data-stu-id="074ca-115">**Show labels**</span></span>  
 <span data-ttu-id="074ca-116">経線のラベルを表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="074ca-116">Select this option to display labels for the meridians.</span></span>  
  
 <span data-ttu-id="074ca-117">**配置**</span><span class="sxs-lookup"><span data-stu-id="074ca-117">**Placement**</span></span>  
 <span data-ttu-id="074ca-118">ビューポートの上、中央部、および下を基準にラベルを表示する位置を選択します。</span><span class="sxs-lookup"><span data-stu-id="074ca-118">Select a location to display the labels relative to the top, center, and bottom of the viewport.</span></span> <span data-ttu-id="074ca-119">既定の位置は **[近く]** です。</span><span class="sxs-lookup"><span data-stu-id="074ca-119">The default placement is **Near**.</span></span>  
  
-   <span data-ttu-id="074ca-120">**[近く]** ラベルを左端に表示します。</span><span class="sxs-lookup"><span data-stu-id="074ca-120">**Near** Display labels at the left edge.</span></span>  
  
-   <span data-ttu-id="074ca-121">**[1/4]** 左端と中央部の間の中間地点にラベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="074ca-121">**One Quarter** Display labels half way between the left edge and the center.</span></span>  
  
-   <span data-ttu-id="074ca-122">**[中央揃え]** 中央部にラベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="074ca-122">**Center** Display labels at the center.</span></span>  
  
-   <span data-ttu-id="074ca-123">**[3/4]** 中央部と右端の間の中間地点にラベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="074ca-123">**Three Quarters** Display labels half way between the center and the right edge.</span></span>  
  
-   <span data-ttu-id="074ca-124">**[遠く]** ラベルを右端に表示します。</span><span class="sxs-lookup"><span data-stu-id="074ca-124">**Far** Display labels at the right edge.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074ca-125">参照</span><span class="sxs-lookup"><span data-stu-id="074ca-125">See Also</span></span>  
 [<span data-ttu-id="074ca-126">マップ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="074ca-126">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
