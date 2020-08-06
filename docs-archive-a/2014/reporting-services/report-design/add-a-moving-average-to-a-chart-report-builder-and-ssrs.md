---
title: グラフへの移動平均の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bc16d0cb45a3240148f931009a836c231b442b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631554"
---
# <a name="add-a-moving-average-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="6375c-102">グラフへの移動平均の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="6375c-102">Add a Moving Average to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6375c-103">移動平均は、定義された期間にわたって計算される、系列内のデータの平均です。</span><span class="sxs-lookup"><span data-stu-id="6375c-103">A moving average is an average of the data in your series, calculated over a defined period of time.</span></span> <span data-ttu-id="6375c-104">移動平均をグラフに表示すると、重要な傾向を特定することができます。</span><span class="sxs-lookup"><span data-stu-id="6375c-104">The moving average can be shown on the chart to identify significant trends.</span></span>  
  
 <span data-ttu-id="6375c-105">移動平均式は、技術的分析で最も一般的に使用される価格指標です。</span><span class="sxs-lookup"><span data-stu-id="6375c-105">The Moving Average formula is the most popular price indicator used in technical analyses.</span></span> <span data-ttu-id="6375c-106">他にも、平均値、中央値、標準偏差など、多くの式をグラフ上の系列から算出することができます。</span><span class="sxs-lookup"><span data-stu-id="6375c-106">Many other formulas, including mean, median and standard deviation, can also be derived from a series on the chart.</span></span> <span data-ttu-id="6375c-107">移動平均を指定する場合、各式には、指定する必要のあるパラメーターが 1 つ以上設定されていることがあります。</span><span class="sxs-lookup"><span data-stu-id="6375c-107">When specifying a moving average, each formula may have one or more parameters that must be specified.</span></span>  
  
 <span data-ttu-id="6375c-108">デザイン モードで移動平均式を追加した際に、追加される線系列は、視覚的なプレースホルダーにすぎません。</span><span class="sxs-lookup"><span data-stu-id="6375c-108">When a moving average formula is added in Design mode, the line series that is added is only a visual placeholder.</span></span> <span data-ttu-id="6375c-109">グラフでは、レポート処理中に各式のデータ ポイントが計算されます。</span><span class="sxs-lookup"><span data-stu-id="6375c-109">The chart will calculate the data points of each formula during report processing.</span></span>  
  
 <span data-ttu-id="6375c-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、傾向線の組み込みサポートは提供されていません。</span><span class="sxs-lookup"><span data-stu-id="6375c-110">Built-in support for trend lines is not available in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-calculated-moving-average-to-a-series-on-the-chart"></a><span data-ttu-id="6375c-111">計算される移動平均をグラフ上の系列に追加するには</span><span class="sxs-lookup"><span data-stu-id="6375c-111">To add a calculated moving average to a series on the chart</span></span>  
  
1.  <span data-ttu-id="6375c-112">**[値]** 領域内のフィールドを右クリックし、 **[計算系列の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6375c-112">Right-click on a field in the **Values** area and click **Add Calculated Series**.</span></span> <span data-ttu-id="6375c-113">**[計算系列のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6375c-113">The **Calculated Series Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="6375c-114">**[式]** ボックスの一覧の **[移動平均]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6375c-114">Select the **Moving average** option from the **Formula** drop-down list.</span></span>  
  
3.  <span data-ttu-id="6375c-115">移動平均の期間を表す整数値を **[期間]** に指定します。</span><span class="sxs-lookup"><span data-stu-id="6375c-115">Specify an integer value for the **Period** that represents the period of the moving average.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6375c-116">期間は、移動平均の計算に使用する日数です。</span><span class="sxs-lookup"><span data-stu-id="6375c-116">The period is the number of days used to calculate a moving average.</span></span> <span data-ttu-id="6375c-117">x 軸で日付/時刻値が指定されていない場合、期間は、移動平均の計算に使用されるデータ ポイント数で表されます。</span><span class="sxs-lookup"><span data-stu-id="6375c-117">If date/time values are not specified on the x-axis, the period is represented by the number of data points used to calculate a moving average.</span></span> <span data-ttu-id="6375c-118">データ ポイントが 1 つしか存在しない場合は、移動平均式による計算は行われません。</span><span class="sxs-lookup"><span data-stu-id="6375c-118">If there is only one data point, the moving average formula does not calculate.</span></span> <span data-ttu-id="6375c-119">移動平均の計算は、2 番目のポイントから開始されます。</span><span class="sxs-lookup"><span data-stu-id="6375c-119">The moving average is calculated starting at the second point.</span></span> <span data-ttu-id="6375c-120">**[最初のポイントから開始する]** チェック ボックスをオンにすると、移動平均の計算は最初のポイントから開始されます。</span><span class="sxs-lookup"><span data-stu-id="6375c-120">If you specify the **Start from first point** option, the chart will start the moving average at the first point.</span></span> <span data-ttu-id="6375c-121">データ ポイントが 1 つしか存在しない場合、計算された移動平均のポイントは、元の系列の最初のポイントと同じになります。</span><span class="sxs-lookup"><span data-stu-id="6375c-121">If there is only one data point, the point in the calculated moving average will be identical to the first point in your original series.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6375c-122">参照</span><span class="sxs-lookup"><span data-stu-id="6375c-122">See Also</span></span>  
 <span data-ttu-id="6375c-123">[グラフの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6375c-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6375c-124">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6375c-124">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6375c-125">グラフ &#40;レポートビルダーと SSRS&#41;に空のポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="6375c-125">Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;</span></span>](add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  
