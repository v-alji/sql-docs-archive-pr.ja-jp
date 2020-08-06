---
title: グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f0826a202969b432e53b3c57ddfe80680ba99e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711718"
---
# <a name="empty-and-null-data-points-in-charts-report-builder-and-ssrs"></a><span data-ttu-id="52add-102">グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="52add-102">Empty and Null Data Points in Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="52add-103">グラフ内に空の値または NULL 値を持つフィールドを表示しようとすると、予期したとおりにグラフが表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="52add-103">If you are displaying fields with empty or null values in your chart, the chart may not look as you expect.</span></span> <span data-ttu-id="52add-104">グラフでは、指定したグラフの種類によって空の値の処理方法が異なります。</span><span class="sxs-lookup"><span data-stu-id="52add-104">Charts process empty values differently depending on the specified chart type:</span></span>  
  
-   <span data-ttu-id="52add-105">グラフの種類が線形のグラフ (横棒グラフ、縦棒グラフ、散布図、折れ線グラフ、面グラフ、または範囲グラフ) の場合、空の値は、空白 (すきま) としてグラフに表示されます。</span><span class="sxs-lookup"><span data-stu-id="52add-105">If the chart type is a linear chart type (bar, column, scatter, line, area, range), empty values are displayed as empty spaces or "gaps" in the chart.</span></span> <span data-ttu-id="52add-106">空のポイントを示すには、空のポイントのプレースホルダーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52add-106">If you want to indicate empty points, you must add empty point placeholders.</span></span> <span data-ttu-id="52add-107">詳細については、「[空のポイントをグラフに追加する &#40;レポートビルダーと SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52add-107">For more information, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="52add-108">グラフの種類が連続性のある線形のグラフ (面グラフ、横棒グラフ、縦棒グラフ、折れ線グラフ、散布図) の場合、空のデータ ポイントが、系列の連続性を維持するようにグラフに追加されます。</span><span class="sxs-lookup"><span data-stu-id="52add-108">If the chart type is a contiguous, linear chart type (area, bar, column, line, scatter), empty data points are added to the chart to maintain continuity in the series.</span></span>  
  
-   <span data-ttu-id="52add-109">グラフの種類が線形のグラフ以外 (極座標グラフ、円グラフ、ドーナツ グラフ、じょうごグラフ、またはピラミッド グラフ) の場合、空の値はグラフに表示されません。</span><span class="sxs-lookup"><span data-stu-id="52add-109">If the chart type is a nonlinear chart type (polar, pie, doughnut, funnel or pyramid), empty values are omitted from display on the chart.</span></span>  
  
-   <span data-ttu-id="52add-110">図形グラフでは、NULL 値が省略されます。</span><span class="sxs-lookup"><span data-stu-id="52add-110">In shape chart types, null values are omitted.</span></span>  
  
 <span data-ttu-id="52add-111">空のデータ ポイント付きのグラフについては、サンプル レポートに例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="52add-111">An example of a chart with empty data points is available as a sample report.</span></span> <span data-ttu-id="52add-112">このサンプルレポートのダウンロードの詳細については、「 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [サンプルレポートのレポートビルダーとレポートデザイナー](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52add-112">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="removing-empty-or-null-values"></a><span data-ttu-id="52add-113">空の値または NULL 値の削除</span><span class="sxs-lookup"><span data-stu-id="52add-113">Removing Empty or Null Values</span></span>  
 <span data-ttu-id="52add-114">重要なデータを見やすくするには、空の値をデータセットから削除することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="52add-114">To avoid obscuring important data, consider removing empty values from your dataset.</span></span> <span data-ttu-id="52add-115">NULL 値をフィルター処理するには、クエリで NOT IS NULL 句を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="52add-115">To filter nulls, you can use the NOT IS NULL clause in your query.</span></span> <span data-ttu-id="52add-116">また、0 以外の値だけが表示されるように指定するフィルター式を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="52add-116">Alternatively, you can add a filtering expression that specifies that you only want to display values not equal to zero.</span></span> <span data-ttu-id="52add-117">詳細については、「 [データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](add-dataset-filters-data-region-filters-and-group-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52add-117">For more information, see [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
## <a name="fields-with-no-values-in-a-chart"></a><span data-ttu-id="52add-118">グラフ内の値がないフィールド</span><span class="sxs-lookup"><span data-stu-id="52add-118">Fields with No Values in a Chart</span></span>  
 <span data-ttu-id="52add-119">返されたデータセット内の値が含まれていないフィールドについては、データ ポイントを含まない空のグラフが表示されますが、系列の名前 (通常はフィールド名) は凡例項目として追加されます。</span><span class="sxs-lookup"><span data-stu-id="52add-119">If a field does not contain any values in the returned dataset, the chart displays an empty chart with no data points, but the series name (typically the field name) is added as a legend item.</span></span>  
  
 <span data-ttu-id="52add-120">この動作は、返されたデータセット内のデータが 0 行である場合とは異なります (この状況は、レポートがパラメーター化されており、選択した値によって空の結果セットが返される場合に発生します)。</span><span class="sxs-lookup"><span data-stu-id="52add-120">This behavior differs from the case where there are zero rows of data in the returned dataset, which can occur when the report is parameterized and the selected value returns an empty result set.</span></span> <span data-ttu-id="52add-121">データセット クエリによって返されるデータが 0 行の場合は、表示できるデータがないことを示すメッセージが実行時に表示されます。</span><span class="sxs-lookup"><span data-stu-id="52add-121">If your dataset query returns zero rows of data, a message is displayed at run time to indicate that no data can be shown.</span></span> <span data-ttu-id="52add-122">**[プロパティ]** ペインでレポートの NoDataMessage キャプションを変更することによって、このメッセージをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="52add-122">You can customize this message by modifying the NoDataMessage caption for the report in the **Properties** pane.</span></span> <span data-ttu-id="52add-123">詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="52add-123">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52add-124">参照</span><span class="sxs-lookup"><span data-stu-id="52add-124">See Also</span></span>  
 <span data-ttu-id="52add-125">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52add-125">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52add-126">[グラフの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52add-126">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52add-127">[レポート &#40;レポートビルダーおよび SSRS&#41;にグラフを追加する](add-a-chart-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52add-127">[Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="52add-128">グラフのトラブルシューティング &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="52add-128">Troubleshoot Charts &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-charts-report-builder-and-ssrs.md)  
  
  
