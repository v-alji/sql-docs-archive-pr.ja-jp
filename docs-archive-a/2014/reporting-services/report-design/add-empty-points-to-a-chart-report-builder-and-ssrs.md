---
title: 空のポイントのグラフへの追加 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53d891c58210bcd51cd4e49f2f9a691a7729c884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737962"
---
# <a name="add-empty-points-to-the-chart-report-builder-and-ssrs"></a><span data-ttu-id="29c7d-102">空のポイントのグラフへの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="29c7d-102">Add Empty Points to the Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="29c7d-103">NULL 値は、系列内のデータ ポイント間の空白 (すきま) としてグラフに表示されます。</span><span class="sxs-lookup"><span data-stu-id="29c7d-103">Null values are shown on the chart as empty spaces or gaps between data points in a series.</span></span> <span data-ttu-id="29c7d-104">空のポイントとは、NULL 値によって作成された空白に挿入できるデータ ポイントのことです。</span><span class="sxs-lookup"><span data-stu-id="29c7d-104">Empty points are data points that can be inserted in the empty space created by null values.</span></span>  
  
 <span data-ttu-id="29c7d-105">既定では、空のポイントは、値が含まれている前のデータ ポイントと次のデータ ポイントの平均値を求めることによって計算されます。</span><span class="sxs-lookup"><span data-stu-id="29c7d-105">By default, empty points are calculated by taking the average of the previous and next data points that contain a value.</span></span> <span data-ttu-id="29c7d-106">この既定の動作を変更して、すべての空のポイントが値ゼロのデータ ポイントとして挿入されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="29c7d-106">You can change this so that all empty points are inserted at zero.</span></span>  
  
 <span data-ttu-id="29c7d-107">詳細については、「[グラフ内の空のデータ ポイントおよび NULL データ ポイント &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29c7d-107">For more information, see [Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-empty-points-on-a-chart"></a><span data-ttu-id="29c7d-108">空のポイントをグラフ上で指定するには</span><span class="sxs-lookup"><span data-stu-id="29c7d-108">To specify empty points on a chart</span></span>  
  
1.  <span data-ttu-id="29c7d-109">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="29c7d-109">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="29c7d-110">デザイン画面で、NULL 値が含まれている系列を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="29c7d-110">On the design surface, right-click the series that contains null values.</span></span> <span data-ttu-id="29c7d-111">系列のプロパティが [プロパティ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="29c7d-111">The properties for the series are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="29c7d-112">**[EmptyPoint]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-112">Expand the **EmptyPoint** node.</span></span>  
  
4.  <span data-ttu-id="29c7d-113">Color プロパティの色の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-113">Select a color value for the Color property.</span></span>  
  
5.  <span data-ttu-id="29c7d-114">**[EmptyPoint]** ノードで [Marker] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-114">In the **EmptyPoint** node, expand the Marker node.</span></span>  
  
6.  <span data-ttu-id="29c7d-115">MarkerType プロパティのマーカーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-115">Select a marker type for the MarkerType property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="29c7d-116">空のポイントを横棒グラフ、縦棒グラフ、または散布図に追加するには、マーカーの種類を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29c7d-116">You must select a marker type to add empty points to a bar, column or scatter chart.</span></span> <span data-ttu-id="29c7d-117">ただし、面グラフ、折れ線グラフ、およびレーダー グラフの場合は、マーカーを指定しなくても空白 (すきま) が自動的に塗りつぶされるので、マーカーの種類の選択は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="29c7d-117">However, for area, line and radar charts, selecting a marker type is optional because the chart fills in the empty space or gap without requiring a marker to be specified.</span></span>  
  
7.  <span data-ttu-id="29c7d-118">空のポイントの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-118">Set the value of the empty point.</span></span>  
  
    1.  <span data-ttu-id="29c7d-119">プロパティ ペインで、 **[CustomAttributes]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-119">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
    2.  <span data-ttu-id="29c7d-120">EmptyPointValue プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-120">Set the EmptyPointValue property.</span></span> <span data-ttu-id="29c7d-121">前のデータ ポイントと次のデータ ポイントの平均値で空のポイントを挿入するには、 **[Average]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-121">To insert empty points at an average of the previous and next data points, select **Average**.</span></span> <span data-ttu-id="29c7d-122">値ゼロのデータ ポイントとして空のポイントを挿入するには、 **[Zero]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="29c7d-122">To insert empty points at zero, select **Zero**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c7d-123">参照</span><span class="sxs-lookup"><span data-stu-id="29c7d-123">See Also</span></span>  
 <span data-ttu-id="29c7d-124">[データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="29c7d-124">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="29c7d-125">[グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="29c7d-125">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="29c7d-126">[グラフへのスケール区切りの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="29c7d-126">[Add Scale Breaks to a Chart &#40;Report Builder and SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="29c7d-127">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="29c7d-127">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
