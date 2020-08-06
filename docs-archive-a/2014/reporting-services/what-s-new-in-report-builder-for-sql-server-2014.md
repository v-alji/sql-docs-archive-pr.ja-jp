---
title: SQL Server 2014 | のレポートビルダーの&#39;の新機能Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ce72af225130bc3f081a53008a303c5213db636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641971"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a><span data-ttu-id="4221f-102">SQL Server 2014 のレポートビルダーの新&#39;</span><span class="sxs-lookup"><span data-stu-id="4221f-102">What&#39;s New in Report Builder for SQL Server 2014</span></span>
  <span data-ttu-id="4221f-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では、いくつかの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能が導入されています。</span><span class="sxs-lookup"><span data-stu-id="4221f-103">The [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] introduces a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features.</span></span>  
  
 <span data-ttu-id="4221f-104">このリリースの他の製品およびテクノロジの機能の詳細について [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] は、「 [SQL Server 2014 の新](../sql-server/what-s-new-in-sql-server-2016.md)機能」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4221f-104">For information about features in this release for other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="4221f-105">このリリースの新機能に関する最新の情報とリソースについては、 [SQL Server Reporting Services (SSRS) の新機能に関する追加情報](https://go.microsoft.com/fwlink/?LinkId=207147)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4221f-105">For the most recent information and resources regarding new features in this release, see [Additional information on what is new in SQL Server Reporting Services (SSRS)](https://go.microsoft.com/fwlink/?LinkId=207147).</span></span>  
  
##  <a name="excel-renderer-for-microsoft-excel-2007-2010-and-microsoft-excel-2003"></a><a name="ExcelRenderer"></a><span data-ttu-id="4221f-106">Microsoft Excel 2007-2010 および Microsoft Excel 2003 用 excel レンダラー</span><span class="sxs-lookup"><span data-stu-id="4221f-106">Excel Renderer for Microsoft Excel 2007-2010 and Microsoft Excel 2003</span></span>  
 <span data-ttu-id="4221f-107">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で新しく採用された [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Excel 表示拡張機能では、インストールされている Word/Excel/PowerPoint 用 Microsoft Office 互換機能パックによって、レポートが [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 および [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 と互換性のある Excel 文書として表示されます。</span><span class="sxs-lookup"><span data-stu-id="4221f-107">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Excel rendering extension, new in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], renders a report as an Excel document that is compatible with [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 as well as [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint installed.</span></span> <span data-ttu-id="4221f-108">形式は Office Open XML で、ファイルのファイル拡張子は .xlsx です。</span><span class="sxs-lookup"><span data-stu-id="4221f-108">The format is Office Open XML and the file extension of files is .xlsx.</span></span>  
  
 <span data-ttu-id="4221f-109">この Excel 表示拡張機能では、Excel 2003 と互換性のある以前のバージョンの制約が取り除かれています。</span><span class="sxs-lookup"><span data-stu-id="4221f-109">This Excel-rendering extension removes limitations of the earlier version, compatible with Excel 2003.</span></span> <span data-ttu-id="4221f-110">表示拡張機能で強化された点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4221f-110">The following lists the improvement in the rendering extension:</span></span>  
  
-   <span data-ttu-id="4221f-111">ワークシートあたりの最大行数: 1,048,576 行</span><span class="sxs-lookup"><span data-stu-id="4221f-111">Maximum rows per worksheet is 1,048,576.</span></span>  
  
-   <span data-ttu-id="4221f-112">ワークシートあたりの最大列数: 16,384</span><span class="sxs-lookup"><span data-stu-id="4221f-112">Maximum columns per worksheet is 16,384.</span></span>  
  
-   <span data-ttu-id="4221f-113">ワークシート内で使用できる色の数: 約 1,600 万色 (24 ビット カラー)</span><span class="sxs-lookup"><span data-stu-id="4221f-113">Number of colors allowed in a worksheet is approximately 16 million (24-bit color).</span></span>  
  
-   <span data-ttu-id="4221f-114">ZIP 圧縮によるファイル サイズの削減</span><span class="sxs-lookup"><span data-stu-id="4221f-114">ZIP compression provides smaller files sizes.</span></span>  
  
 <span data-ttu-id="4221f-115">詳細については、「 [Microsoft Excel へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)で操作できます。</span><span class="sxs-lookup"><span data-stu-id="4221f-115">For more information, see [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="word-renderer-for-microsoft-word-2007-2010-and-microsoft-word-2003"></a><a name="WordRenderer"></a><span data-ttu-id="4221f-116">Microsoft Word 2007-2010 および Microsoft Word 2003 用 word レンダラー</span><span class="sxs-lookup"><span data-stu-id="4221f-116">Word Renderer for Microsoft Word 2007-2010 and Microsoft Word 2003</span></span>  
 <span data-ttu-id="4221f-117">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で新しく採用された [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Word 表示拡張機能では、インストールされている Word/Excel/PowerPoint 用 [!INCLUDE[ofprword](../includes/ofprword-md.md)] Office 互換機能パックによって、レポートが [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 および [!INCLUDE[msCoName](../includes/msconame-md.md)] 2003 と互換性のある Word 文書として表示されます。</span><span class="sxs-lookup"><span data-stu-id="4221f-117">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Word rendering extension, new in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], renders a report as a Word document that is compatible with [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 as well as [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003 with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Compatibility Pack for Word, Excel, and PowerPoint installed.</span></span> <span data-ttu-id="4221f-118">形式は Office Open XML で、ファイルのファイル拡張子は docx です。</span><span class="sxs-lookup"><span data-stu-id="4221f-118">The format is Office Open XML and the file extension of files is docx.</span></span>  
  
 <span data-ttu-id="4221f-119">エクスポートされたレポートで Word 2007-2010 の新機能が利用できるようになる点に加え、エクスポートされたレポートの \*.docx ファイルのサイズが小さくなる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="4221f-119">In addition to making the features that are new in Word 2007-2010 available to exported reports, \*.docx files of exported reports tend to be smaller.</span></span> <span data-ttu-id="4221f-120">Word レンダラーを使用してエクスポートされたレポートは通常、Word 2003 レンダラーを使用してエクスポートされた同じレポートよりもサイズがかなり小さくなります。</span><span class="sxs-lookup"><span data-stu-id="4221f-120">Reports exported by using the Word renderer are typically significantly smaller than the same reports exported by using the Word 2003 renderer.</span></span>  
  
 <span data-ttu-id="4221f-121">詳細については、「 [Microsoft Word へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)で操作できます。</span><span class="sxs-lookup"><span data-stu-id="4221f-121">For more information, see [Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4221f-122">参照</span><span class="sxs-lookup"><span data-stu-id="4221f-122">See Also</span></span>  
 [<span data-ttu-id="4221f-123">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="4221f-123">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
