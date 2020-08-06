---
title: 他のアプリケーションからのレポートの印刷 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58fee2cf31601dc638eebd69a13727a805408ac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717523"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a><span data-ttu-id="7f8c7-102">他のアプリケーションからのレポートの印刷 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7f8c7-102">Print Reports from Other Applications (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7f8c7-103">レポート ビルダーには、他のアプリケーションでレポートを簡単に表示できるエクスポート オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-103">Report Builder provides an export option that allows you to easily view a report in other applications.</span></span> <span data-ttu-id="7f8c7-104">`Export` コマンドは、レポートをブラウザーまたは Web ベース アプリケーションで開くときにレポートの上部に表示される [レポート] ツール バーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-104">The `Export` command is available on the report toolbar that appears at the top of a report when you open it in a browser or Web-based application.</span></span> <span data-ttu-id="7f8c7-105">レポートをエクスポートすると、レポートは別のアプリケーションで表示されます。たとえば、レポートを Excel にエクスポートすると、 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]でレポートが開きます。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-105">Exporting a report displays it in a different application (for example, exporting a report to Excel opens the report in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]).</span></span> <span data-ttu-id="7f8c7-106">印刷を実行する場合は、必要な印刷機能がアプリケーションに備わっている場合にのみレポートのエクスポートをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-106">For printing purposes, exporting a report is recommended only if the application has specific printing features that you want to use.</span></span>  
  
 <span data-ttu-id="7f8c7-107">レポートを別のアプリケーションにエクスポートするには、該当するアプリケーションがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-107">To export a report to another application, you must have that application installed.</span></span> <span data-ttu-id="7f8c7-108">たとえば、Acrobat (PDF) 形式でエクスポートするには、コンピューターにあらかじめ Adobe Acrobat Reader がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-108">For example, you must have Adobe Acrobat Reader installed on your computer before you can export to the Acrobat (PDF) format.</span></span> <span data-ttu-id="7f8c7-109">TIFF 形式でレポートをエクスポートする場合は、レポート サーバーにより、TIFF ファイル形式に関連付けられている表示アプリケーションでレポートが開かれます。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-109">If you choose to export a report to TIFF format, the report server places the report in a viewing application that is associated with the TIFF file type.</span></span> <span data-ttu-id="7f8c7-110">インストールされている [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のバージョンにより異なりますが、この表示アプリケーションには、通常 Windows 画像と FAX ビューアーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-110">Although the application used depends on which version of [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows you have, typically this tool is Windows Picture and Fax Viewer.</span></span> <span data-ttu-id="7f8c7-111">既定の解像度は、画面の解像度に合わせて、96 DPI になります。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-111">The default resolution corresponds to a screen resolution of 96 dots per inch (DPI).</span></span> <span data-ttu-id="7f8c7-112">Windows 画像と Fax ビューアーの解像度は、プリンターの機能に合わせて、300 DPI または 600 DPI に上げることができます。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-112">You can increase the resolution in Windows Picture and Fax Viewer to 300 DPI or 600 DPI to match the capabilities of your printer.</span></span> <span data-ttu-id="7f8c7-113">解像度の調整方法の詳細については、Windows の製品マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-113">For more information about adjusting the resolution, see the Windows product documentation.</span></span>  
  
 <span data-ttu-id="7f8c7-114">Web アーカイブ (MHTML) を選択した場合、レポートは既定のブラウザーにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-114">If you choose Web archive (also known as MHTML), the report is exported to your default browser.</span></span> <span data-ttu-id="7f8c7-115">ブラウザーから印刷すると、レポートのパス情報がすべてのページの下部に追加される場合があります。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-115">Printing from the browser may result in report path information being added at the bottom of every page.</span></span> <span data-ttu-id="7f8c7-116">多くの場合、ブラウザーのオプションを設定して、印刷ページにパス情報が印刷されないように設定できます。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-116">In most cases, you can set browser options to omit path information on a printed page.</span></span> <span data-ttu-id="7f8c7-117">詳細については、使用しているブラウザーの製品マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f8c7-117">For more information, see the product documentation for the browser you are using.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f8c7-118">参照</span><span class="sxs-lookup"><span data-stu-id="7f8c7-118">See Also</span></span>  
 <span data-ttu-id="7f8c7-119">[レポートの印刷 &#40;レポートビルダーと SSRS&#41;](print-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7f8c7-119">[Print a Report &#40;Report Builder and SSRS&#41;](print-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7f8c7-120">[印刷コントロール &#40;レポートビルダーと SSRS を使用してブラウザーからレポートを印刷&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7f8c7-120">[Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7f8c7-121">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7f8c7-121">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7f8c7-122">[レポートを別の種類のファイルとしてエクスポートする &#40;レポートビルダーと SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7f8c7-122">[Export a Report as Another File Type &#40;Report Builder and SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7f8c7-123">レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7f8c7-123">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
