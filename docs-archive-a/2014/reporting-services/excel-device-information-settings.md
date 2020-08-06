---
title: Excel デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d71c83195c8f91984bbbce95bd00402928fdb36e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719611"
---
# <a name="excel-device-information-settings"></a><span data-ttu-id="52169-102">Excel  デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="52169-102">Excel Device Information Settings</span></span>
  <span data-ttu-id="52169-103">次の表は、 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 形式で表示するためのデバイス情報設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="52169-103">The following table lists the device information settings for rendering in [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] format.</span></span>  
  
|<span data-ttu-id="52169-104">設定</span><span class="sxs-lookup"><span data-stu-id="52169-104">Setting</span></span>|<span data-ttu-id="52169-105">値</span><span class="sxs-lookup"><span data-stu-id="52169-105">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="52169-106">**OmitDocumentMap**</span><span class="sxs-lookup"><span data-stu-id="52169-106">**OmitDocumentMap**</span></span>|<span data-ttu-id="52169-107">ドキュメント マップをサポートするレポートで、ドキュメント マップを省略するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="52169-107">Indicates whether to omit the document map for reports that support it.</span></span> <span data-ttu-id="52169-108">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="52169-108">The default value is `false`.</span></span>|  
|<span data-ttu-id="52169-109">**OmitFormulas**</span><span class="sxs-lookup"><span data-stu-id="52169-109">**OmitFormulas**</span></span>|<span data-ttu-id="52169-110">表示レポートで式を省略するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="52169-110">Indicates whether to omit formulas from the rendered report.</span></span> <span data-ttu-id="52169-111">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="52169-111">The default value is `false`.</span></span>|  
|<span data-ttu-id="52169-112">`SimplePageHeade`rs</span><span class="sxs-lookup"><span data-stu-id="52169-112">`SimplePageHeade`rs</span></span>|<span data-ttu-id="52169-113">レポートのページ ヘッダーを Excel ページのヘッダーに表示するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="52169-113">Indicates whether the page header of the report is rendered to the Excel page header.</span></span> <span data-ttu-id="52169-114">`false` の値は、ページ ヘッダーがワークシートの 1 行目に表示されることを示します。</span><span class="sxs-lookup"><span data-stu-id="52169-114">A value of `false` indicates that the page header is rendered to the first row of the worksheet.</span></span> <span data-ttu-id="52169-115">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="52169-115">The default value is `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52169-116">参照</span><span class="sxs-lookup"><span data-stu-id="52169-116">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="52169-117">[表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="52169-117">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="52169-118">[RSReportServer.Configで表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="52169-118">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="52169-119">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="52169-119">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
