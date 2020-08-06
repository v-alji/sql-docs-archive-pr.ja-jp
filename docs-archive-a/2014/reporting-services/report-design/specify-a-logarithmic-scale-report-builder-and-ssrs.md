---
title: 対数スケールの指定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2cc422a6f95a420445dc604d08a23e8f8e65c95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631527"
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a><span data-ttu-id="a7a3c-102">対数スケールの指定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a7a3c-102">Specify a Logarithmic Scale (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a7a3c-103">対数比例するデータがある場合は、グラフ上での対数スケールの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-103">If you have data that is logarithmically proportional, you may want to consider using a logarithmic scale on the chart.</span></span> <span data-ttu-id="a7a3c-104">これにより、データの管理が容易になり、グラフの外観が向上します。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-104">This helps improve the appearance of the chart by making your data more manageable.</span></span> <span data-ttu-id="a7a3c-105">ほとんどの対数スケールでは、底に 10 を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-105">Most logarithmic scales use a base of 10.</span></span>  
  
 <span data-ttu-id="a7a3c-106">この機能は値軸でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-106">This feature is only available on the value axis.</span></span> <span data-ttu-id="a7a3c-107">通常、値軸は縦軸 (Y 軸) です。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-107">The value axis is usually the vertical, or y-axis.</span></span> <span data-ttu-id="a7a3c-108">ただし、横棒グラフの値軸は横軸 (X 軸) です。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-108">On bar charts, however, it is the horizontal, or x-axis.</span></span>  
  
 <span data-ttu-id="a7a3c-109">軸が対数の場合、その軸に関連するその他すべてのプロパティは、対数スケールで示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-109">If your axis is logarithmic, all other properties relating to the axis will be scaled logarithmically.</span></span> <span data-ttu-id="a7a3c-110">たとえば、10 を底とする対数スケールを軸で指定した場合、軸の間隔を 2 に設定すると、10 の 2 乗 (つまり 100) の増分率で間隔が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-110">For example, if you specify a base-10 logarithmic scale on your axis, setting an axis interval of 2 will generate intervals in magnitudes of 10 to the power of 2, or 100.</span></span> <span data-ttu-id="a7a3c-111">つまり、軸の値は既定の 1、10、100、1000、10000 ではなく、1、100、10000 という値を取ります。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-111">This means your axis values will read 1, 100, 10000, instead of the default result of 1, 10, 100, 1000, 10000.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-logarithmic-scale"></a><span data-ttu-id="a7a3c-112">対数スケールを指定するには</span><span class="sxs-lookup"><span data-stu-id="a7a3c-112">To specify a logarithmic scale</span></span>  
  
1.  <span data-ttu-id="a7a3c-113">グラフの Y 軸を右クリックし、 **[縦軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-113">Right-click the y-axis of your chart, and click **VerticalAxis Properties**.</span></span> <span data-ttu-id="a7a3c-114">**[縦軸のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-114">The **VerticalAxis Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="a7a3c-115">**[軸のオプション]** で、 **[対数スケールを使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-115">In **Axis Options**, select **Uselogarithmic scale**.</span></span>  
  
3.  <span data-ttu-id="a7a3c-116">**[対数の底]** ボックスに、対数の底を正の値で入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-116">In the **Logbase** text box, type a positive value for the logarithmic base.</span></span> <span data-ttu-id="a7a3c-117">値を指定しなかった場合、対数の底は既定値の 10 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a7a3c-117">If no value is specified, the logarithmic base defaults to 10.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a3c-118">参照</span><span class="sxs-lookup"><span data-stu-id="a7a3c-118">See Also</span></span>  
 <span data-ttu-id="a7a3c-119">[グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a7a3c-119">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a7a3c-120">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a7a3c-120">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a7a3c-121">[日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a7a3c-121">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a7a3c-122">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a7a3c-122">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
