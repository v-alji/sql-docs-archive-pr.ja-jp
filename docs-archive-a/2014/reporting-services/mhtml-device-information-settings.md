---
title: MHTML デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 076a0179871775984799fc8ce5366a220f812867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643207"
---
# <a name="mhtml-device-information-settings"></a><span data-ttu-id="7d982-102">MHTML デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="7d982-102">MHTML Device Information Settings</span></span>
  <span data-ttu-id="7d982-103">次の表は、Web アーカイブ (MHTML) 形式でレポートを表示するためのデバイス情報設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="7d982-103">The following table lists the device information settings for rendering reports in Web archive (MHTML) format.</span></span>  
  
|<span data-ttu-id="7d982-104">設定</span><span class="sxs-lookup"><span data-stu-id="7d982-104">Setting</span></span>|<span data-ttu-id="7d982-105">値</span><span class="sxs-lookup"><span data-stu-id="7d982-105">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="7d982-106">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="7d982-106">**JavaScript**</span></span>|<span data-ttu-id="7d982-107">表示レポートで JavaScript がサポートされるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7d982-107">Indicates whether JavaScript is supported in the rendered report.</span></span>|  
|<span data-ttu-id="7d982-108">**OutlookCompat**</span><span class="sxs-lookup"><span data-stu-id="7d982-108">**OutlookCompat**</span></span>|<span data-ttu-id="7d982-109">Outlook でレポートの外観をよくする追加のメタデータを使用して表示するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7d982-109">Indicates whether to render with extra metadata that makes the report look better in Outlook.</span></span> <span data-ttu-id="7d982-110">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="7d982-110">The default value is `true`.</span></span>|  
|<span data-ttu-id="7d982-111">**MHTML Fragment**</span><span class="sxs-lookup"><span data-stu-id="7d982-111">**MHTML Fragment**</span></span>|<span data-ttu-id="7d982-112">完全な MHTML ドキュメントの代わりに MHTML を断片として作成するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7d982-112">Indicates whether an MHTML fragment is created in place of a full MHTML document.</span></span> <span data-ttu-id="7d982-113">MHTML の断片には、TABLE 要素のレポート コンテンツが含まれ、HTML 要素と BODY 要素が省略されます。</span><span class="sxs-lookup"><span data-stu-id="7d982-113">An MHTML fragment includes the report content in a TABLE element and omits the HTML and BODY elements.</span></span> <span data-ttu-id="7d982-114">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="7d982-114">The default value is `false`.</span></span>|  
|<span data-ttu-id="7d982-115">**DataVisualizationFitSizing**</span><span class="sxs-lookup"><span data-stu-id="7d982-115">**DataVisualizationFitSizing**</span></span>|<span data-ttu-id="7d982-116">Tablix 内でのデータの視覚エフェクトの調整動作を示します。</span><span class="sxs-lookup"><span data-stu-id="7d982-116">Indicates data visualization fit behavior when inside a tablix.</span></span> <span data-ttu-id="7d982-117">これには、グラフ、ゲージ、およびマップが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7d982-117">This includes chart, gauge, and map.</span></span><br /><br /> <span data-ttu-id="7d982-118">有効な値は、 **Approximate** および **Exact**です。</span><span class="sxs-lookup"><span data-stu-id="7d982-118">The possible values are **Approximate** and **Exact**.</span></span><br /><br /> <span data-ttu-id="7d982-119">既定値は **Approximate**です。</span><span class="sxs-lookup"><span data-stu-id="7d982-119">The default value is **Approximate**.</span></span> <span data-ttu-id="7d982-120">この設定を **rsreportserver.config** ファイルから削除すると、既定の動作は **Exact**になります。</span><span class="sxs-lookup"><span data-stu-id="7d982-120">If the setting is removed from the **rsreportserver.config** file then the default behavior is **Exact**.</span></span><br /><br /> <span data-ttu-id="7d982-121">**Exact** を有効にした場合は、正確なサイズを特定する処理に時間がかかることがあるため、パフォーマンスに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d982-121">Enabling **Exact** may have performance impact because the processing to determine the exact size may take longer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d982-122">参照</span><span class="sxs-lookup"><span data-stu-id="7d982-122">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="7d982-123">[表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="7d982-123">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="7d982-124">[RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="7d982-124">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="7d982-125">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="7d982-125">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
