---
title: テーブル内のグラフまたはマトリックスでのデータの整列 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e4278cd9f0dd5526770b43d2c6d94a8b87158cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644344"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a><span data-ttu-id="3d1d2-102">テーブル内のグラフまたはマトリックスでのデータの整列 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="3d1d2-102">Align the Data in a Chart in a Table or Matrix (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3d1d2-103">スパークラインとデータ バーは小さく単純なグラフであり、余分な情報を最小限に抑えて多くの情報を伝えます。</span><span class="sxs-lookup"><span data-stu-id="3d1d2-103">Sparklines and data bars are small, simple charts that convey a lot of information with little extraneous detail.</span></span> <span data-ttu-id="3d1d2-104">このオプションをオンにすると、基礎となるデータに欠落した値がある場合でも、スパークラインおよびデータ バーの値がテーブルまたはマトリックスのさまざまなセルに整列します。</span><span class="sxs-lookup"><span data-stu-id="3d1d2-104">When you check this option, the values in your sparklines and data bars will align across the different cells in the table or matrix, even if there are missing values in the data they are based on.</span></span>  
  
 <span data-ttu-id="3d1d2-105">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span><span class="sxs-lookup"><span data-stu-id="3d1d2-105">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span></span>  
  
 <span data-ttu-id="3d1d2-106">次の画像には、各従業員の毎日の売り上げが縦棒グラフで示されています。</span><span class="sxs-lookup"><span data-stu-id="3d1d2-106">In this image, the column chart shows daily sales for each employee.</span></span> <span data-ttu-id="3d1d2-107">売り上げのない日にはグラフが空白になり、後続の日が横に整列していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3d1d2-107">Note that for days that an employee has no sales, the chart leaves a blank and aligns subsequent days horizontally.</span></span> <span data-ttu-id="3d1d2-108">また、異なるグラフのサイズを互いに相対させてグラフを縦にも並べています。</span><span class="sxs-lookup"><span data-stu-id="3d1d2-108">It also aligns the charts vertically by making the sizes of the different charts relative to each other.</span></span> <span data-ttu-id="3d1d2-109">詳細については、「 [スパークラインとデータ バー (レポート ビルダーおよび SSRS)](sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d1d2-109">For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="align-the-data-in-a-sparkline-or-data-bar"></a><span data-ttu-id="3d1d2-110">スパークラインまたはデータ バー内のデータの整列</span><span class="sxs-lookup"><span data-stu-id="3d1d2-110">Align the data in a sparkline or data bar</span></span>  
  
1.  <span data-ttu-id="3d1d2-111">スパークラインまたはデータ バーをクリックし、 **[水平軸のプロパティ]** または **[垂直軸のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d1d2-111">Click in the sparkline or data bar, and then click **Horizontal Axis Properties** or **Vertical Axis Properties**.</span></span>  
  
2.  <span data-ttu-id="3d1d2-112">**[軸のオプション]** タブで **[軸を整列する]** ボックスをオンにし、ドロップダウン ボックスで軸を整列するグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="3d1d2-112">On the **Axis Options** tab, check the **Align axes in** box, and then in the dropdown box, select the group on which to align the axis.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d1d2-113">参照</span><span class="sxs-lookup"><span data-stu-id="3d1d2-113">See Also</span></span>  
 <span data-ttu-id="3d1d2-114">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3d1d2-114">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3d1d2-115">スパークラインとデータ バーの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3d1d2-115">Add Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
