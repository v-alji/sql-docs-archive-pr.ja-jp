---
title: '[最適化] ([マップビューポートのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.optimization.f1
- "10522"
ms.assetid: 8c0310ba-eedd-4c9f-95bd-1f9e2a1a8ed3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1adbeccdedb8d80900047790d94ff35568460ff4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741550"
---
# <a name="map-viewport-properties-dialog-box-optimization"></a><span data-ttu-id="4c5af-102">[最適化] ([マップ ビューポートのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="4c5af-102">Map Viewport Properties Dialog Box, Optimization</span></span>
  <span data-ttu-id="4c5af-103">**[マップ ビューポートのプロパティ]** ダイアログ ボックスの **[最適化]** を選択すると、レポート内のマップを表示するための解像度を制御できます。</span><span class="sxs-lookup"><span data-stu-id="4c5af-103">Select **Optimization** for the **Map Viewport Properties** dialog box to help control the resolution for viewing a map in a report.</span></span>  
  
 <span data-ttu-id="4c5af-104">空間データがレポートに埋め込まれている場合は、解像度が高くなるほど、レポートに格納されるデータ量が多くなります。</span><span class="sxs-lookup"><span data-stu-id="4c5af-104">When spatial data is embedded in the report, higher resolution means more data is stored in the report.</span></span> <span data-ttu-id="4c5af-105">空間データがレポートに埋め込まれていない場合は、解像度が高くなるほど、レポート プロセッサがマップ詳細を作成するのに要する時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="4c5af-105">When spatial data is not embedded in the report, higher resolution means that the report processor spends more time creating the map details.</span></span> <span data-ttu-id="4c5af-106">解像度が低くなるほど、レポートの描画に要する時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="4c5af-106">Lower resolution means less time waiting for the report to render.</span></span>  
  
 <span data-ttu-id="4c5af-107">**式** ([fx]) ボタンをクリックし、オプションの値を設定する式を編集します。\*\*</span><span class="sxs-lookup"><span data-stu-id="4c5af-107">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4c5af-108">Options</span><span class="sxs-lookup"><span data-stu-id="4c5af-108">Options</span></span>  
 <span data-ttu-id="4c5af-109">**パフォーマンス**</span><span class="sxs-lookup"><span data-stu-id="4c5af-109">**Performance**</span></span>  
 <span data-ttu-id="4c5af-110">マップを簡略化して詳細を表示しないようにするには、ポインターを **[パフォーマンス]** 方向にスライドします。</span><span class="sxs-lookup"><span data-stu-id="4c5af-110">Slide the pointer closer to **Performance** to simplify the map and display less detail.</span></span>  
  
 <span data-ttu-id="4c5af-111">**Quality**</span><span class="sxs-lookup"><span data-stu-id="4c5af-111">**Quality**</span></span>  
 <span data-ttu-id="4c5af-112">マップに詳細を表示するには、ポインターを **[品質]** 方向にスライドします。</span><span class="sxs-lookup"><span data-stu-id="4c5af-112">Slide the pointer closer to **Quality** to draw the map with greater detail.</span></span>  
  
 <span data-ttu-id="4c5af-113">**[マップの解像度]**</span><span class="sxs-lookup"><span data-stu-id="4c5af-113">**Map resolution**</span></span>  
 <span data-ttu-id="4c5af-114">マップの解像度を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5af-114">Specify a map resolution.</span></span> <span data-ttu-id="4c5af-115">この値は、描画されたマップに表示する最小の詳細データをポイント単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5af-115">This value specifies the smallest detail that you want to see in the rendered map in points.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5af-116">参照</span><span class="sxs-lookup"><span data-stu-id="4c5af-116">See Also</span></span>  
 <span data-ttu-id="4c5af-117">[マップ &#40;レポート ビルダーおよび SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4c5af-117">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4c5af-118">レポートのトラブルシューティング: マップ レポート &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4c5af-118">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
