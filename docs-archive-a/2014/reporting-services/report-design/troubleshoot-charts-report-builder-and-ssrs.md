---
title: グラフのトラブルシューティング (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b931b50545ba2b8d7c4c06cc5c48d6415a05470a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717445"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a><span data-ttu-id="85724-102">グラフのトラブルシューティング (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="85724-102">Troubleshoot Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="85724-103">グラフを使用するときに役立つヒントを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="85724-103">These issues can be helpful when working with charts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a><span data-ttu-id="85724-104">グラフの値軸で件数がカウントされ、値が合計されない</span><span class="sxs-lookup"><span data-stu-id="85724-104">Why does my chart count, not sum, the values on the value axis?</span></span>  
 <span data-ttu-id="85724-105">ほとんどの種類のグラフでは、正確に描画するために値軸 (通常は Y 軸) に数値が必要です。</span><span class="sxs-lookup"><span data-stu-id="85724-105">Most chart types require numeric values along the value axis, which is typically the y-axis, in order to draw correctly.</span></span> <span data-ttu-id="85724-106">値フィールドのデータ型が `String` の場合、フィールドに数字が入っていても、グラフでは数値を表示できません。</span><span class="sxs-lookup"><span data-stu-id="85724-106">If the data type of your value field is `String`, the chart cannot display a numeric value, even if there are numerals in the fields.</span></span> <span data-ttu-id="85724-107">その代わり、グラフには、そのフィールドに値が格納されている行の総数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="85724-107">Instead, the chart displays a count of the total number of rows that contain a value in that field.</span></span> <span data-ttu-id="85724-108">この動作を回避するには、値系列に使用するフィールドに、書式設定された数値を格納した文字列ではなく、数値データ型を設定してください。</span><span class="sxs-lookup"><span data-stu-id="85724-108">To avoid this behavior, make sure that the fields that you use for value series have numeric data types, as opposed to strings that contain formatted numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85724-109">参照</span><span class="sxs-lookup"><span data-stu-id="85724-109">See Also</span></span>  
 [<span data-ttu-id="85724-110">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="85724-110">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
