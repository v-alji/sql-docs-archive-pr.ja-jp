---
title: ゲージへのスナップ間隔の設定 (レポートビルダーと SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdc2a621c4406791838d97e93f47cd32fa9d5f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719460"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="341bc-102">ゲージへのスナップ間隔の設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="341bc-102">Set a Snapping Interval on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="341bc-103">スナップ間隔とは、値を丸める際の倍数を定義するものです。</span><span class="sxs-lookup"><span data-stu-id="341bc-103">A snapping interval defines the multiple to which values are rounded.</span></span> <span data-ttu-id="341bc-104">既定では、ゲージは、データ ペインで指定したフィールドの正確な値を指し示します。</span><span class="sxs-lookup"><span data-stu-id="341bc-104">By default, the gauge will point to the exact value of the field you have specified in the data pane.</span></span> <span data-ttu-id="341bc-105">ただし必要であれば、事前に設定した間隔に合わせて、正確な値を切り上げたり、切り捨てたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="341bc-105">However, you may want to round the exact value up or down so that the pointer will snap to a preset interval.</span></span> <span data-ttu-id="341bc-106">たとえば、ゲージの値が 34.2 であるとき、スナップ間隔として 5 を指定した場合、ゲージ ポインターが指し示す値は 35 になります。</span><span class="sxs-lookup"><span data-stu-id="341bc-106">For example, if the value on your gauge is 34.2 and you specify a snapping interval of 5, the gauge pointer will point to 35.</span></span> <span data-ttu-id="341bc-107">ゲージの値が 31.2 であるとき、スナップ間隔として 5 を指定した場合、ゲージ ポインターが指し示す値は 30 になります。</span><span class="sxs-lookup"><span data-stu-id="341bc-107">If the value on your gauge is 31.2 and you specify a snapping interval of 5, the gauge pointer will point to 30.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a><span data-ttu-id="341bc-108">ゲージにスナップ間隔を設定するには</span><span class="sxs-lookup"><span data-stu-id="341bc-108">To set a snapping interval on a gauge</span></span>  
  
1.  <span data-ttu-id="341bc-109">ゲージに表示されている任意の数値をクリックし、スケールを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="341bc-109">Click anywhere on the numbers of the gauge to highlight the scale.</span></span>  
  
2.  <span data-ttu-id="341bc-110">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="341bc-110">Open the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="341bc-111">プロパティペインが表示されない場合は、[**表示**] タブをクリックし、[**プロパティ**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="341bc-111">If you do not see the Properties pane, click the **View** tab and then select the **Properties** checkbox.</span></span>  
  
3.  <span data-ttu-id="341bc-112">**ポインター**のプロパティで、[...] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="341bc-112">In the **Pointers** property, click the (...) button.</span></span> <span data-ttu-id="341bc-113">ポインター コレクション エディターが開きます。</span><span class="sxs-lookup"><span data-stu-id="341bc-113">The Pointer Collection Editor opens.</span></span>  
  
4.  <span data-ttu-id="341bc-114">**SnappingEnabled**プロパティをに設定し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="341bc-114">Set the **SnappingEnabled** property to `True`.</span></span>  
  
5.  <span data-ttu-id="341bc-115">**SnappingInterval**を、スナップ間隔を表す値に設定します。</span><span class="sxs-lookup"><span data-stu-id="341bc-115">Set the **SnappingInterval** to a value that represents the snapping interval.</span></span> <span data-ttu-id="341bc-116">実際の値を指定の倍数に丸めた位置までポインターがスナップされます。</span><span class="sxs-lookup"><span data-stu-id="341bc-116">The pointer will be snapped to the nearest round multiple of the value that you have specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341bc-117">参照</span><span class="sxs-lookup"><span data-stu-id="341bc-117">See Also</span></span>  
 <span data-ttu-id="341bc-118">[ゲージのスケールの書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="341bc-118">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="341bc-119">[ゲージのポインターの書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="341bc-119">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="341bc-120">ゲージ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="341bc-120">Gauges &#40;Report Builder and SSRS&#41;</span></span>](report-design/gauges-report-builder-and-ssrs.md)  
  
  
