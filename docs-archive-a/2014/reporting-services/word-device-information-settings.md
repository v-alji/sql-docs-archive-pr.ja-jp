---
title: Word デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddd145c5073003a8dc189e3ed9b1bbb25dc11d09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631514"
---
# <a name="word-device-information-settings"></a><span data-ttu-id="fad81-102">Word デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="fad81-102">Word Device Information Settings</span></span>
  <span data-ttu-id="fad81-103">次の表は、 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 形式で表示するためのデバイス情報設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="fad81-103">The following table lists the device information settings for rendering in [!INCLUDE[ofprword](../includes/ofprword-md.md)] format.</span></span>  
  
|<span data-ttu-id="fad81-104">設定</span><span class="sxs-lookup"><span data-stu-id="fad81-104">Setting</span></span>|<span data-ttu-id="fad81-105">値</span><span class="sxs-lookup"><span data-stu-id="fad81-105">Value</span></span>|  
|-------------|-----------|  
|`AutoFit`|<span data-ttu-id="fad81-106">`False`.</span><span class="sxs-lookup"><span data-stu-id="fad81-106">`False`.</span></span> <span data-ttu-id="fad81-107">Word のすべての表で AutoFit が `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fad81-107">AutoFit is set to `false` set on any Word table.</span></span><br /><br /> <span data-ttu-id="fad81-108">`True`.</span><span class="sxs-lookup"><span data-stu-id="fad81-108">`True`.</span></span> <span data-ttu-id="fad81-109">`true`Word のすべての表で、[自動調整をに設定する。</span><span class="sxs-lookup"><span data-stu-id="fad81-109">AutoFit is set to `true` on every Word table.</span></span><br /><br /> <span data-ttu-id="fad81-110">`Never`.</span><span class="sxs-lookup"><span data-stu-id="fad81-110">`Never`.</span></span> <span data-ttu-id="fad81-111">Word の表で AutoFit 値が設定されず、動作が Word の既定値に戻ります。</span><span class="sxs-lookup"><span data-stu-id="fad81-111">AutoFit values are not set on any Word table and behavior reverts to the Word default.</span></span><br /><br /> <span data-ttu-id="fad81-112">`Default`.</span><span class="sxs-lookup"><span data-stu-id="fad81-112">`Default`.</span></span> <span data-ttu-id="fad81-113">各論理ページごとに、物理的な描画領域 (余白を除いた物理ページの幅) よりも幅の狭い表で AutoFit が設定されます。</span><span class="sxs-lookup"><span data-stu-id="fad81-113">AutoFit is set on tables that are narrower than the physical drawing area (physical page width excluding margins) per logical page.</span></span>|  
|`ExpandToggles`|<span data-ttu-id="fad81-114">表示と非表示の切り替えが可能なすべてのアイテムを完全に展開した状態で表示するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="fad81-114">Indicates whether all items that can be toggled should render in their fully-expanded state.</span></span> <span data-ttu-id="fad81-115">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="fad81-115">The default value is `false`.</span></span>|  
|`FixedPageWidth`|<span data-ttu-id="fad81-116">DOC ファイルに書き込まれるページの幅がレポート本文内で最大のページの幅に合わせて拡大されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="fad81-116">Indicates whether the Page Width written to the DOC file will grow to accommodate the width of the largest page in the Report Body.</span></span> <span data-ttu-id="fad81-117">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="fad81-117">The default value is `false`.</span></span>|  
|<span data-ttu-id="fad81-118">**OmitHyperlinks**</span><span class="sxs-lookup"><span data-stu-id="fad81-118">**OmitHyperlinks**</span></span>|<span data-ttu-id="fad81-119">ハイパーリンク アクションが設定されているすべてのアイテムでそのアクションを省略するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="fad81-119">Indicates whether to omit the Hyperlink action on all items where it is set.</span></span> <span data-ttu-id="fad81-120">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="fad81-120">The default value is `false`</span></span>|  
|`OmitDrillthroughs`|<span data-ttu-id="fad81-121">ドリルスルー アクションが設定されているすべてのアイテムでそのアクションを省略するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="fad81-121">Indicates whether to omit the Drillthrough action on all items where it is set.</span></span> <span data-ttu-id="fad81-122">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="fad81-122">The default value is `false`</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fad81-123">参照</span><span class="sxs-lookup"><span data-stu-id="fad81-123">See Also</span></span>  
 <span data-ttu-id="fad81-124">[表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="fad81-124">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="fad81-125">[RSReportServer.Configで表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="fad81-125">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="fad81-126">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="fad81-126">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
