---
title: グラフの余白の追加または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d8bad99591964540bcd14fc5609560a3d324515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719593"
---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="4e168-102">グラフの余白の追加または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4e168-102">Add or Remove Margins from a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4e168-103">縦棒グラフおよび散布図では、横余白が X 軸の両端に自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="4e168-103">In Column and Scatter chart types, the chart automatically adds side margins on the ends of the x-axis.</span></span> <span data-ttu-id="4e168-104">横棒グラフでは、横余白が Y 軸の両端に自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="4e168-104">In Bar chart types, the chart automatically adds side margins on the ends of the y-axis.</span></span> <span data-ttu-id="4e168-105">その他すべての種類のグラフでは、横余白は追加されません。</span><span class="sxs-lookup"><span data-stu-id="4e168-105">In all other chart types, the chart does not add side margins.</span></span> <span data-ttu-id="4e168-106">余白のサイズは変更できません。</span><span class="sxs-lookup"><span data-stu-id="4e168-106">You cannot change the size of the margin.</span></span>  
  
 <span data-ttu-id="4e168-107">このトピックは、円グラフ、ドーナツ グラフ、じょうごグラフ、またはピラミッド グラフには当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="4e168-107">This topic does not apply to pie, doughnut, funnel, or pyramid chart types.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-or-disable-side-margins"></a><span data-ttu-id="4e168-108">横余白を有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="4e168-108">To enable or disable side margins</span></span>  
  
1.  <span data-ttu-id="4e168-109">軸を右クリックし、 **[軸のプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4e168-109">Right-click the axis and select **Axis Properties**.</span></span> <span data-ttu-id="4e168-110">**[縦軸のプロパティ]** ダイアログ ボックスまたは **[横軸のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e168-110">The **Vertical** or **HorizontalAxis Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="4e168-111">**[軸のオプション]** ページで、 **[横余白]** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4e168-111">On the **Axis Options** page, set the **Side margins** property:</span></span>  
  
    -   <span data-ttu-id="4e168-112">**[自動]** グラフの種類に基づいて横余白を追加するかどうかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="4e168-112">**Auto** The chart will determine whether to add a side margin based on the chart type.</span></span>  
  
    -   <span data-ttu-id="4e168-113">**[無効]** 横棒グラフ、縦棒グラフ、および散布図では、横余白はなしになります。</span><span class="sxs-lookup"><span data-stu-id="4e168-113">**Disabled** Bar, column, and scatter charts will have no side margins.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e168-114">参照</span><span class="sxs-lookup"><span data-stu-id="4e168-114">See Also</span></span>  
 <span data-ttu-id="4e168-115">[グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e168-115">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e168-116">[[軸のプロパティ] ダイアログ ボックス、[軸のオプション] &#40;レポート ビルダーおよび SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e168-116">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e168-117">[軸の間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e168-117">[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e168-118">[日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e168-118">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4e168-119">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4e168-119">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
