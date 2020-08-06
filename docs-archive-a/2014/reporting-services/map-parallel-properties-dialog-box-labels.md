---
title: '[ラベル] ([マップの並列プロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapparallelproperties.labels.f1
- "10519"
ms.assetid: 4560a7e4-e19b-4a6e-8ef4-e963497e01ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c08baa31ad8ee65f1f096ecf4304803a79e0fbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631641"
---
# <a name="map-parallel-properties-dialog-box-labels"></a><span data-ttu-id="0721d-102">[ラベル] ([マップの緯線のプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="0721d-102">Map Parallel Properties Dialog Box, Labels</span></span>
  <span data-ttu-id="0721d-103">[ **Mapparallel のプロパティ**] ダイアログボックスを使用すると、マップビューポートの水平グリッドのラベルオプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="0721d-103">Use the **MapParallel Properties** dialog box to change label options for the horizontal grid in the map viewport.</span></span> <span data-ttu-id="0721d-104">緯線とは、ビューポートに指定された座標系に応じて、次の値を表します。</span><span class="sxs-lookup"><span data-stu-id="0721d-104">A parallel represents the following value depending on the specified coordinate system for the viewport:</span></span>  
  
-   <span data-ttu-id="0721d-105">**2.**</span><span class="sxs-lookup"><span data-stu-id="0721d-105">**Planar.**</span></span> <span data-ttu-id="0721d-106">X 座標。</span><span class="sxs-lookup"><span data-stu-id="0721d-106">The X coordinate.</span></span>  
  
-   <span data-ttu-id="0721d-107">**地理的.**</span><span class="sxs-lookup"><span data-stu-id="0721d-107">**Geographic.**</span></span> <span data-ttu-id="0721d-108">現在の投影法での緯度。</span><span class="sxs-lookup"><span data-stu-id="0721d-108">The latitude for the current projection.</span></span>  
  
 <span data-ttu-id="0721d-109">**式** ([fx]) ボタンをクリックし、オプションの値を設定する式を編集します。\*\*</span><span class="sxs-lookup"><span data-stu-id="0721d-109">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0721d-110">Options</span><span class="sxs-lookup"><span data-stu-id="0721d-110">Options</span></span>  
 <span data-ttu-id="0721d-111">**間隔**</span><span class="sxs-lookup"><span data-stu-id="0721d-111">**Interval**</span></span>  
 <span data-ttu-id="0721d-112">緯線間の間隔を指定する度数を整数値で入力します。</span><span class="sxs-lookup"><span data-stu-id="0721d-112">Type an integer value in degrees that specifies the interval between parallels.</span></span> <span data-ttu-id="0721d-113">既定では、 **[自動]** が選択されます。</span><span class="sxs-lookup"><span data-stu-id="0721d-113">By default, **Auto** is selected.</span></span> <span data-ttu-id="0721d-114">このオプションが **[自動]** に設定されている場合、値はマップ データセットからのデータによって決まります。</span><span class="sxs-lookup"><span data-stu-id="0721d-114">If this option is set to **Auto**, the value is determined by the data from the map dataset.</span></span>  
  
 <span data-ttu-id="0721d-115">**[ラベルを表示]**</span><span class="sxs-lookup"><span data-stu-id="0721d-115">**Show labels**</span></span>  
 <span data-ttu-id="0721d-116">緯線のラベルを表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0721d-116">Select this option to display labels for the parallels.</span></span>  
  
 <span data-ttu-id="0721d-117">**配置**</span><span class="sxs-lookup"><span data-stu-id="0721d-117">**Placement**</span></span>  
 <span data-ttu-id="0721d-118">ビューポートの上、中央部、および下を基準にラベルを表示する位置を選択します。</span><span class="sxs-lookup"><span data-stu-id="0721d-118">Select a location to display the labels relative to the top, center, and bottom of the viewport.</span></span> <span data-ttu-id="0721d-119">既定の位置は **[近く]** です。</span><span class="sxs-lookup"><span data-stu-id="0721d-119">The default placement is **Near**.</span></span>  
  
-   <span data-ttu-id="0721d-120">**[近く]** ラベルを上に表示します。</span><span class="sxs-lookup"><span data-stu-id="0721d-120">**Near** Display labels at the top.</span></span>  
  
-   <span data-ttu-id="0721d-121">**[1/4]** 上部と中央部の間の中間地点にラベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="0721d-121">**One Quarter** Display labels half way between the top and the center.</span></span>  
  
-   <span data-ttu-id="0721d-122">**[中央揃え]** 中央部にラベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="0721d-122">**Center** Display labels at the center.</span></span>  
  
-   <span data-ttu-id="0721d-123">**[3/4]** 中央部と下部の間の中間地点にラベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="0721d-123">**Three Quarters** Display labels half way between the center and the bottom.</span></span>  
  
-   <span data-ttu-id="0721d-124">**[遠く]** ラベルを下部に表示します。</span><span class="sxs-lookup"><span data-stu-id="0721d-124">**Far** Display labels at the bottom.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0721d-125">参照</span><span class="sxs-lookup"><span data-stu-id="0721d-125">See Also</span></span>  
 <span data-ttu-id="0721d-126">[マップ &#40;レポート ビルダーおよび SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0721d-126">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0721d-127">マップの凡例、カラー スケール、および関連付けられているルールの変更 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0721d-127">Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;</span></span>](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
