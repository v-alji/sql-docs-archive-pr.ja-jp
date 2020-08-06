---
title: ゲージへの最小値または最大値の設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b4c260c0-5a88-4f30-8977-eb5cc78fc146
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 344122dbff647a8c35b838ecce637602f202864b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632896"
---
# <a name="set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="ac791-102">ゲージへの最小値または最大値の設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ac791-102">Set a Minimum or Maximum on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ac791-103">複数のグループが定義されるグラフとは異なり、ゲージには 1 つの値しか表示されません。</span><span class="sxs-lookup"><span data-stu-id="ac791-103">Unlike the chart, where multiple groups are defined, the gauge only shows one value.</span></span> <span data-ttu-id="ac791-104">レポート ビルダーおよびレポート デザイナーは、ゲージに表示される値のコンテキストや相対的な有意性を判断することができないため、スケールの最小値と最大値は独自に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac791-104">Since Report Builder and Report Designer determine the context or relative significance of the one value that you are trying to show on the gauge, you must define the minimum and maximum of the scale.</span></span> <span data-ttu-id="ac791-105">たとえば、データの値が 0 ～ 10 のランキングを表している場合は、最小値を 0 に、最大値を 10 に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac791-105">For example, if your data values are rankings between 0 and 10, you will want to set the minimum to 0 and maximum to 10.</span></span> <span data-ttu-id="ac791-106">間隔の数は、最小値と最大値として指定された値に基づいて自動的に計算されます。</span><span class="sxs-lookup"><span data-stu-id="ac791-106">The interval numbers are calculated automatically based on the values specified for the minimum and maximum.</span></span> <span data-ttu-id="ac791-107">既定では、最小値と最大値はそれぞれ 0 および 100 に設定されますが、これらは恣意的な値であり、必要に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac791-107">By default, the minimum and maximum are set to 0 and 100, but this is an arbitrary value that you should change.</span></span> <span data-ttu-id="ac791-108">アプリケーションによって値がパーセンテージとして計算されることはありません。</span><span class="sxs-lookup"><span data-stu-id="ac791-108">The application does not calculate your value as a percentage.</span></span>  
  
 <span data-ttu-id="ac791-109">値の範囲が大きい場合は (0 ～ 10000 など)、乗数を使って、ゲージに表示されるゼロの数を減らすことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ac791-109">If the range of your values is large, for example from 0 to 10000, consider using a multiplier to reduce the number of zeroes on the gauge.</span></span> <span data-ttu-id="ac791-110">乗数によって小さくなるのは、ゲージ上に表示される数値の尺度だけです。値そのものが小さくなるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ac791-110">The multiplier will only reduce the scale of the numbers on the gauge, not the value itself.</span></span>  
  
 <span data-ttu-id="ac791-111">式を使用して **[最小]** オプションと **[最大]** オプションの値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ac791-111">You can use expressions to set the values of the **Minimum** and **Maximum** options.</span></span> <span data-ttu-id="ac791-112">詳細については、「[式 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac791-112">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-minimum-and-maximum-on-the-gauge"></a><span data-ttu-id="ac791-113">ゲージに最小値または最大値を設定するには</span><span class="sxs-lookup"><span data-stu-id="ac791-113">To set the minimum and maximum on the gauge</span></span>  
  
1.  <span data-ttu-id="ac791-114">スケールを右クリックし、 **[スケールのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac791-114">Right-click on the scale and select **Scale Properties**.</span></span> <span data-ttu-id="ac791-115">**[スケールのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac791-115">The **Scale Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ac791-116">**[全般]** で、 **[最小]** の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac791-116">In **General**, specify a value for **Minimum**.</span></span> <span data-ttu-id="ac791-117">既定では、この値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="ac791-117">By default, this value is 0.</span></span> <span data-ttu-id="ac791-118">必要に応じて、 **式** ([*fx*]) ボタンをクリックし、オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="ac791-118">Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.</span></span>  
  
3.  <span data-ttu-id="ac791-119">**[最大]** の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac791-119">Specify a value for **Maximum**.</span></span> <span data-ttu-id="ac791-120">既定では、この値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="ac791-120">By default, this value is 100.</span></span> <span data-ttu-id="ac791-121">必要に応じて、 **式** ([*fx*]) ボタンをクリックし、オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="ac791-121">Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="ac791-122">(省略可) 最小と最大の値が大きい場合は、 **[スケール ラベルの乗数値]** オプションに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac791-122">(Optional) If the values for your minimum and maximum are large, specify a value for the **Multiply scale labels by** option.</span></span> <span data-ttu-id="ac791-123">尺度を小さくするための乗数は、小数値を使って指定します。</span><span class="sxs-lookup"><span data-stu-id="ac791-123">To specify a multiplier that reduces your scale, use a decimal number.</span></span> <span data-ttu-id="ac791-124">たとえば、0 ～ 1000 の尺度が存在する場合は、乗数値を「0.01」とすることで 0 ～ 10 の尺度に変更できます。</span><span class="sxs-lookup"><span data-stu-id="ac791-124">For example, if you have a scale from 0 to 1000, you can specify a multiplier value of 0.01 to reduce the scale to read 0 to 10.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac791-125">参照</span><span class="sxs-lookup"><span data-stu-id="ac791-125">See Also</span></span>  
 <span data-ttu-id="ac791-126">[ゲージのスケールの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ac791-126">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ac791-127">[ゲージのポインターの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ac791-127">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ac791-128">ゲージ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ac791-128">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
