---
title: 円グラフの値の開始位置を円の最上部にする (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed010eeaf3e4d581cce2f7242144c4f73ec2895b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631519"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a><span data-ttu-id="00a66-102">円グラフの値の開始位置を円の最上部にする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="00a66-102">Start Pie Chart Values at the Top of the Pie (Report Builder and SSRS)</span></span>
  <span data-ttu-id="00a66-103">円グラフでは、既定でデータセットの最初の値が円の最上部から 90 度の位置から開始されます。</span><span class="sxs-lookup"><span data-stu-id="00a66-103">By default in pie charts, the first value in the dataset starts at 90 degrees from the top of the pie.</span></span> <span data-ttu-id="00a66-104">最初の値の開始位置を最上部にすることが望ましい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="00a66-104">You may prefer that the first value start from the top.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a><span data-ttu-id="00a66-105">円グラフの開始位置を円の最上部にするには</span><span class="sxs-lookup"><span data-stu-id="00a66-105">To Start the Pie Chart at the Top of the Pie</span></span>  
  
1.  <span data-ttu-id="00a66-106">円グラフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="00a66-106">Click the pie itself.</span></span>  
  
2.  <span data-ttu-id="00a66-107">**プロパティ** ペインが開いていない場合は、 **[表示]** タブの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00a66-107">If the **Properties** pane is not open, on the **View** tab, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="00a66-108">**プロパティ**ペインの [**カスタム属性**] で、 **PieStartAngle**を**0**から**270**に変更します。</span><span class="sxs-lookup"><span data-stu-id="00a66-108">In the **Properties** pane, under **Custom Attributes**, change **PieStartAngle** from **0** to **270**.</span></span>  
  
4.  <span data-ttu-id="00a66-109">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="00a66-109">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="00a66-110">最初の値の開始位置が円グラフの最上部になります。</span><span class="sxs-lookup"><span data-stu-id="00a66-110">The first value now starts at the top of the pie chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a66-111">参照</span><span class="sxs-lookup"><span data-stu-id="00a66-111">See Also</span></span>  
 <span data-ttu-id="00a66-112">[グラフの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="00a66-112">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="00a66-113">レポートビルダーおよび SSRS&#41;&#40;円グラフ</span><span class="sxs-lookup"><span data-stu-id="00a66-113">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
