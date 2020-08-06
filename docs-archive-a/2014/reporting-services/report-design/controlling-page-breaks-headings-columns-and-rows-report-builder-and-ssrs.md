---
title: 改ページ、見出し、列、および行の制御 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8fa41f-a727-4f23-8efb-fd9bb0d4cd1d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7dae06129ee5dc9962538e8d025dca9966325f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643172"
---
# <a name="controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs"></a><span data-ttu-id="8ae30-102">改ページ、見出し、列、および行の制御 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="8ae30-102">Controlling Page Breaks, Headings, Columns, and Rows (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8ae30-103">レポートは、改ページによって複数のページに分割され表示および印刷されます。</span><span class="sxs-lookup"><span data-stu-id="8ae30-103">A page break divides a report into separate pages for viewing and printing.</span></span> <span data-ttu-id="8ae30-104">改ページを使用すると、レポートのプレビュー時または他のファイル形式へのエクスポート時に、表示が最適化されるようにコンテンツをレポート ページに収めることができます。</span><span class="sxs-lookup"><span data-stu-id="8ae30-104">Page breaks determine how the content is fitted to a report page for optimal viewing when you preview a report or export it to a different file format.</span></span>  
  
 <span data-ttu-id="8ae30-105">さらに、サイズの大きいレポートでは、改ページを追加することによって、レポート処理時のパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="8ae30-105">Adding page breaks also improves the performance of large reports when the are processed.</span></span> <span data-ttu-id="8ae30-106">レンダリングが完了したページが 1 ページずつ表示され、他のページはバックグラウンドでレンダリングされるため、</span><span class="sxs-lookup"><span data-stu-id="8ae30-106">A rendered page is displayed while the rest of the pages are rendered in the background.</span></span> <span data-ttu-id="8ae30-107">他のページが表示されるのを待つ間に、レポートの最初のページを読むことができます。</span><span class="sxs-lookup"><span data-stu-id="8ae30-107">This allows you to begin viewing the initial pages of the report while waiting for additional pages to become available.</span></span>  
  
 <span data-ttu-id="8ae30-108">改ページは、テーブル、マトリックス、一覧、グラフ、ゲージ、画像などのレポート アイテムに追加できます。</span><span class="sxs-lookup"><span data-stu-id="8ae30-108">Page breaks can be added to report items such as a table, matrix, list, chart, gauge, or image.</span></span> <span data-ttu-id="8ae30-109">さらに、テーブル、マトリックス、または一覧のグループにも追加できます。</span><span class="sxs-lookup"><span data-stu-id="8ae30-109">You can also add page breaks to groups in a table, matrix, or list.</span></span> <span data-ttu-id="8ae30-110">改ページは、グループの前、後、またはグループの間に追加できます。</span><span class="sxs-lookup"><span data-stu-id="8ae30-110">Page breaks can be added before, after, and between groups.</span></span> <span data-ttu-id="8ae30-111">既定では、グループ間の改ページはレポートに追加されません。</span><span class="sxs-lookup"><span data-stu-id="8ae30-111">Page breaks between groups are not added to the report by default.</span></span>  
  
 <span data-ttu-id="8ae30-112">詳細については、「[複数のページへの行および列ヘッダーの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)」と「[レポートのスクロール時にヘッダーを表示したままにする &#40;レポート ビルダーおよび SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ae30-112">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) and [Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ae30-113">参照</span><span class="sxs-lookup"><span data-stu-id="8ae30-113">See Also</span></span>  
 <span data-ttu-id="8ae30-114">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8ae30-114">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8ae30-115">[レポート ページでの Tablix データ領域の表示の制御 &#40;レポート ビルダーおよび SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md) </span><span class="sxs-lookup"><span data-stu-id="8ae30-115">[Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md) </span></span>  
 <span data-ttu-id="8ae30-116">[グループ化ペイン &#40;レポート ビルダー&#41;](grouping-pane-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="8ae30-116">[Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md) </span></span>  
 [<span data-ttu-id="8ae30-117">グループ単位でのヘッダーとフッターの表示 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8ae30-117">Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;</span></span>](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)  
  
  
