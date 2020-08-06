---
title: 系列へのツールヒントの表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4c9606ff-e1c3-4cf7-a4e7-bb16f1a9e8ab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9113ec843b3b9255f380b17ee1ab6b360fa1f60d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644308"
---
# <a name="show-tooltips-on-a-series-report-builder-and-ssrs"></a><span data-ttu-id="7ba32-102">系列へのツールヒントの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7ba32-102">Show ToolTips on a Series (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7ba32-103">グラフの系列上の各データ ポイントにツールヒントを追加すると、表示されたレポートのデータ ポイントにユーザーがマウス カーソルを合わせたときにデータ ポイントに関連する情報 (グループ名、データ ポイントの値、系列の合計に対するデータ ポイントの比率など) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ba32-103">You can add a ToolTip to each data point on the series of a chart to display information related to the data point, such as the group name, the value of the data point, or the percentage of the data point relative to the series total when users hover over the data point in a rendered report.</span></span>  
  
 <span data-ttu-id="7ba32-104">計算系列にはツールヒントを追加できません。</span><span class="sxs-lookup"><span data-stu-id="7ba32-104">You cannot add a ToolTip to a calculated series.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-tooltip-on-each-data-point"></a><span data-ttu-id="7ba32-105">各データ ポイントにツールヒントを指定するには</span><span class="sxs-lookup"><span data-stu-id="7ba32-105">To specify a ToolTip on each data point</span></span>  
  
1.  <span data-ttu-id="7ba32-106">系列を右クリックするか、 **[値]** 領域のフィールドを右クリックし、 **[系列のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ba32-106">Right-click on the series or right-click on the field in the **Values** area, and click **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="7ba32-107">**[系列データ]** をクリックし、 **ToolTip** プロパティに文字列または式を入力します。</span><span class="sxs-lookup"><span data-stu-id="7ba32-107">Click **Series Data** and, for the **ToolTip** property, type in a string or expression.</span></span> <span data-ttu-id="7ba32-108">グラフ固有のキーワードを使用して、グラフ上の別の要素を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="7ba32-108">You can use any chart-specific keyword to represent another element on the chart.</span></span> <span data-ttu-id="7ba32-109">詳細については、「 [グラフでのデータ ポイントの書式設定 (レポート ビルダーおよび SSRS)](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ba32-109">For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba32-110">参照</span><span class="sxs-lookup"><span data-stu-id="7ba32-110">See Also</span></span>  
 <span data-ttu-id="7ba32-111">[グラフ上のデータポイントの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ba32-111">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7ba32-112">[レポートビルダーおよび SSRS &#40;凡例項目のテキストを変更&#41;](chart-legend-change-item-text-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="7ba32-112">[Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span></span>  
 <span data-ttu-id="7ba32-113">[グラフの系列の色の書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ba32-113">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7ba32-114">レポートへのドリルスルー アクションの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7ba32-114">Add a Drillthrough Action on a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
