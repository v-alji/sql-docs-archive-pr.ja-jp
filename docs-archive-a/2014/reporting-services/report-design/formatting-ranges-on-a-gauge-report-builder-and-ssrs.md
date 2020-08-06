---
title: ゲージの範囲の書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29574c58eef6f18d685b48dd8d695a5fc42c3e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711686"
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="5bea8-102">ゲージの範囲の書式設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5bea8-102">Formatting Ranges on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5bea8-103">ゲージ範囲は、ゲージ上の値の重要なサブセクションを示す、ゲージ スケール上のゾーンまたは領域です。</span><span class="sxs-lookup"><span data-stu-id="5bea8-103">A gauge range is a zone or area on the gauge scale that indicates an important subsection of values on the gauge.</span></span> <span data-ttu-id="5bea8-104">ゲージ範囲を使用すると、ポインター値が特定の値範囲に入る時期を視覚的に示すことができます。</span><span class="sxs-lookup"><span data-stu-id="5bea8-104">Using a gauge range, you can visually indicate when the pointer value has gone into a certain span of values.</span></span> <span data-ttu-id="5bea8-105">範囲は、開始値と終了値で定義されます。</span><span class="sxs-lookup"><span data-stu-id="5bea8-105">Ranges are defined by a start value and an end value.</span></span>  
  
 <span data-ttu-id="5bea8-106">また、範囲を使用して、ゲージのさまざまなセクションを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="5bea8-106">You can also use ranges to define different sections of a gauge.</span></span> <span data-ttu-id="5bea8-107">たとえば、0 ～ 10 の値を持つゲージで、0 ～ 3 の値を持つ赤色の範囲を定義し、4 ～ 7 の値を持つ黄色の範囲を定義し、8 ～ 10 の値を持つ緑色の範囲を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="5bea8-107">For example, on a gauge with values from 0 to 10, you can define a red range that has a value from 0 to 3, a yellow range that has a value from 4 to 7 and a green range that has a value from 8 to 10.</span></span> <span data-ttu-id="5bea8-108">指定した開始値が指定した終了値よりも大きい場合は、開始値が終了値になり、終了値が開始値になるように値が交換されます。</span><span class="sxs-lookup"><span data-stu-id="5bea8-108">If the start value that you specified is greater than the end value that you specified, the values are swapped so that the start value is the end value and the end value is the start value.</span></span>  
  
 <span data-ttu-id="5bea8-109">範囲は、スケールにポインターを配置するのと同じように配置することができます。</span><span class="sxs-lookup"><span data-stu-id="5bea8-109">You can position the range in the same way that you position pointers on a scale.</span></span> <span data-ttu-id="5bea8-110">**[位置]** プロパティと **[スケールからの距離]** プロパティで範囲の位置を決定します。</span><span class="sxs-lookup"><span data-stu-id="5bea8-110">The **Position** and **Distance from scale** properties determine the position of the range.</span></span> <span data-ttu-id="5bea8-111">詳しくは、「 [ゲージ &#40;レポート ビルダーおよび SSRS&#41;](gauges-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5bea8-111">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5bea8-112">参照</span><span class="sxs-lookup"><span data-stu-id="5bea8-112">See Also</span></span>  
 <span data-ttu-id="5bea8-113">[ゲージのスケールの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5bea8-113">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5bea8-114">[ゲージのポインターの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5bea8-114">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5bea8-115">[ゲージへの最小値または最大値の設定 &#40;レポート ビルダーおよび SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5bea8-115">[Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5bea8-116">[チュートリアル: レポートへの KPI の追加 &#40;レポート ビルダー&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="5bea8-116">[Tutorial: Adding a KPI to Your Report &#40;Report Builder&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="5bea8-117">ゲージ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5bea8-117">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
