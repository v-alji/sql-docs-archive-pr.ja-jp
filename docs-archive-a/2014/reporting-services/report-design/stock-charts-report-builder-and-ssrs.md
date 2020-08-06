---
title: 株価チャート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f75ca11e-b7f5-4ac0-ba17-fe6f82742dad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0f8c9c7dbc750bdb477f2ea1d96aa03f7ad022f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631518"
---
# <a name="stock-charts-report-builder-and-ssrs"></a><span data-ttu-id="f0bfb-102">株価チャート (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="f0bfb-102">Stock Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f0bfb-103">株価チャートは、各データ ポイントに最大 4 つの値を使用する、財務データや科学的データ向けに特別にデザインされています。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-103">A stock chart is specifically designed for financial or scientific data that uses up to four values per data point.</span></span> <span data-ttu-id="f0bfb-104">これらの値は、金融株価データをプロットする際に使用される、高値、安値、始値、終値に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-104">These values align with the high, low, open and close values that are used to plot financial stock data.</span></span> <span data-ttu-id="f0bfb-105">この種類のグラフでは、マーカーを使用して始値と終値を表示します。マーカーは、通常、線または三角形です。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-105">This chart type displays opening and closing values by using markers, which are typically lines or triangles.</span></span> <span data-ttu-id="f0bfb-106">次の例では、始値が左側のマーカーで示され、終値が右側のマーカーで示されています。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-106">In the following example, the opening values are shown by the markers on the left, and the closing values are shown by the markers on the right.</span></span>  
  
 <span data-ttu-id="f0bfb-107">![株価チャート](../media/rs-stockchart.gif "株価チャート")</span><span class="sxs-lookup"><span data-stu-id="f0bfb-107">![Stock chart](../media/rs-stockchart.gif "Stock chart")</span></span>  
  
 <span data-ttu-id="f0bfb-108">株価チャートについては、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] レポート ビルダーのサンプル レポートに例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-108">An example of a stock chart is available as a sample [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="f0bfb-109">このサンプルレポートのダウンロードの詳細については、「 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [サンプルレポートのレポートビルダーとレポートデザイナー](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-109">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="f0bfb-110">バリエーション</span><span class="sxs-lookup"><span data-stu-id="f0bfb-110">Variations</span></span>  
  
-   <span data-ttu-id="f0bfb-111">**ローソク足**:</span><span class="sxs-lookup"><span data-stu-id="f0bfb-111">**Candlestick**.</span></span> <span data-ttu-id="f0bfb-112">ローソク足チャートは、特殊な形式の株価チャートです。このチャートでは、四角形を使用して、始値から終値までの範囲が示されます。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-112">The candlestick chart is a specialized form of the stock chart, wherein boxes are used to show the range between the open and close values.</span></span> <span data-ttu-id="f0bfb-113">株価チャートと同様、ローソク足チャートでは、各データ ポイントに最大 4 つの値を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-113">Like the stock chart, the candlestick chart can display up to four values per data point.</span></span>  
  
## <a name="data-considerations-for-stock-charts"></a><span data-ttu-id="f0bfb-114">株価チャートのデータに関する注意点</span><span class="sxs-lookup"><span data-stu-id="f0bfb-114">Data Considerations for Stock Charts</span></span>  
  
-   <span data-ttu-id="f0bfb-115">年間の株価の動向など、多数の株価データ ポイントを表示する場合、各データ ポイントの始値、終値、高値、安値をそれぞれ区別することは困難です。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-115">When presenting many stock data points, such as annual stock price trend, it is difficult to distinguish each open, close, high and low value of each data point.</span></span> <span data-ttu-id="f0bfb-116">この場合は、株価チャートの代わりに折れ線グラフの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-116">In this scenario, consider using a line chart instead of a stock chart.</span></span>  
  
-   <span data-ttu-id="f0bfb-117">軸ラベルが生成されると、通常、ラベル付けは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-117">When axis labels are generated, labeling usually begins at zero.</span></span>  <span data-ttu-id="f0bfb-118">一般に、株価は、他のデータセットと同じようには変動しません。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-118">In general, stock prices do not fluctuate to the same degree as other data sets.</span></span> <span data-ttu-id="f0bfb-119">このため、データを見やすくする目的で、必要に応じて軸ラベルが 0 から始まらないようにします。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-119">For this reason, you may want to disable the axis labels from starting at zero, in order to get a better view of your data.</span></span> <span data-ttu-id="f0bfb-120">これを行うには、 **[軸のプロパティ]** ダイアログ ボックスまたは [プロパティ] ウィンドウで、 **IncludeZero** を **False** に設定します。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-120">To do this, set **IncludeZero** to **false** in the **Axis Properties** dialog box or the Properties window.</span></span> <span data-ttu-id="f0bfb-121">グラフの軸ラベルを作成する方法の詳細については、「[グラフの軸ラベルの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-121">For more information about how the chart generates axis labels, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f0bfb-122">には、価格指標、相対力指数、MACD など、株価チャートで使用する多くの計算式が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f0bfb-122">provides many calculated formulas for use with stock charts, including Price Indicator, Relative Strength Index, MACD and more.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0bfb-123">参照</span><span class="sxs-lookup"><span data-stu-id="f0bfb-123">See Also</span></span>  
 <span data-ttu-id="f0bfb-124">[範囲グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0bfb-124">[Range Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f0bfb-125">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0bfb-125">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f0bfb-126">[グラフの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0bfb-126">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f0bfb-127">[[軸のオプション] ([軸のプロパティ] ダイアログ ボックス) &#40;レポート ビルダーおよび SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="f0bfb-127">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)</span></span>  
  
  
