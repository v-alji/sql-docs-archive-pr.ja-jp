---
title: レンダリングの動作 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8f873ef9-27a3-40e5-b58b-6774f8027a58
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d6a6aa91c547f4739b172f9303ac9e61bde5771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721146"
---
# <a name="rendering-behaviors-report-builder--and-ssrs"></a><span data-ttu-id="5fae3-102">レンダリングの動作 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5fae3-102">Rendering Behaviors (Report Builder  and SSRS)</span></span>
  <span data-ttu-id="5fae3-103">選択したレンダラーによっては、レポートをレンダリングする際に、レポート本文とそのコンテンツに特定の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-103">Depending on the renderer you select, certain rules are applied to the report body and its contents when rendering a report.</span></span> <span data-ttu-id="5fae3-104">レポート アイテムが 1 ページにまとめられる際の方法は、次に示す要因の組み合わせによって決まります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-104">How report items fit together on a page is determined by the combination of these factors:</span></span>  
  
-   <span data-ttu-id="5fae3-105">レンダリングの規則。</span><span class="sxs-lookup"><span data-stu-id="5fae3-105">Rendering rules.</span></span>  
  
-   <span data-ttu-id="5fae3-106">レポート アイテムの幅と高さ。</span><span class="sxs-lookup"><span data-stu-id="5fae3-106">The width and height of report items.</span></span>  
  
-   <span data-ttu-id="5fae3-107">レポート本文のサイズ。</span><span class="sxs-lookup"><span data-stu-id="5fae3-107">The size of the report body.</span></span>  
  
-   <span data-ttu-id="5fae3-108">ページの幅と高さ。</span><span class="sxs-lookup"><span data-stu-id="5fae3-108">The width and height of the page.</span></span>  
  
-   <span data-ttu-id="5fae3-109">レンダラー固有の改ページ調整。</span><span class="sxs-lookup"><span data-stu-id="5fae3-109">Renderer-specific support for paging.</span></span>  
  
 <span data-ttu-id="5fae3-110">このトピックでは、Reporting Services で適用される一般的な規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fae3-110">This topic discusses the general rules that are applied by Reporting Services.</span></span> <span data-ttu-id="5fae3-111">詳細については、「[レポート アイテムのレンダリング &#40;レポート ビルダーおよび SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md)」、「[データ領域の表示 &#40;レポート ビルダーおよび SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md)」、「[データの表示 &#40;レポート ビルダーおよび SSRS&#41;](rendering-data-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fae3-111">For more information, see [Rendering Report Items &#40;Report Builder and SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md), [Rendering Data Regions &#40;Report Builder and SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md), and [Rendering Data &#40;Report Builder and SSRS&#41;](rendering-data-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="general-behaviors-for-html-mhtml-word-and-excel-soft-page-break-renderers"></a><span data-ttu-id="5fae3-112">HTML、MHTML、Word、および Excel の一般的な動作 (ソフト改ページ レンダラー)</span><span class="sxs-lookup"><span data-stu-id="5fae3-112">General Behaviors for HTML, MHTML, Word, and Excel (Soft Page-Break Renderers)</span></span>  
 <span data-ttu-id="5fae3-113">HTML 形式や MHTML 形式でエクスポートされたレポートは、コンピューター画面での操作性を重視して最適化され、ページの長さは固定的ではありません。</span><span class="sxs-lookup"><span data-stu-id="5fae3-113">Reports exported using HTML and MHTML formats are optimized for a computer screen-based experience where pages can be various lengths.</span></span> <span data-ttu-id="5fae3-114">改ページは、レポート本文内のおおよその位置に、垂直方向にのみ挿入されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-114">Page breaks are inserted vertically only at approximate locations within the report body.</span></span> <span data-ttu-id="5fae3-115">おおよその位置は、[プロパティ] ペインにある対話的な高さ設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-115">These approximate locations are determined by the interactive height setting in the Properties pane.</span></span> <span data-ttu-id="5fae3-116">たとえば、対話的な高さが 5 インチに設定されているとします。</span><span class="sxs-lookup"><span data-stu-id="5fae3-116">For example, suppose the interactive height is set to 5 inches.</span></span> <span data-ttu-id="5fae3-117">レポートをレンダリングすると、このページの高さは約 5 インチになります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-117">When the report is rendered, the page height is approximately 5 inches in length.</span></span> <span data-ttu-id="5fae3-118">Word および Excel の改ページは論理的な改ページによって調整されるため、対話的な高さの設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-118">Word and Excel paginate based on logical page breaks and ignore the interactive height setting.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fae3-119">ソフト改ページ レンダラーでレポートがどのように表示されるかを確認するには、レポートのプレビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="5fae3-119">To determine how a report will appear in a soft page-break renderer, use Report Preview.</span></span> <span data-ttu-id="5fae3-120">HTML、MHTML、Word、または Excel 形式で表示した場合と同じように、レポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-120">The report appears as it would in a HTML, MHTML, Word, or Excel format.</span></span>  
  
 <span data-ttu-id="5fae3-121">レポートを HTML、MHTML、Word、または Excel にエクスポートする場合は、次の一般的な規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-121">When exporting a report to HTML, MHTML, Word, or Excel, the following general rules are followed:</span></span>  
  
-   <span data-ttu-id="5fae3-122">レポート アイテムには、論理的な改ページ (明示的に挿入した改ページ) が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-122">Logical page breaks, the page breaks that you explicitly insert, are applied to report items.</span></span> <span data-ttu-id="5fae3-123">たとえば、各グループ間に改ページを挿入した場合、これらの改ページが、レポートのレンダリング時に適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-123">For example, if you insert a page break between each group, they are applied when the report is rendered.</span></span>  
  
-   <span data-ttu-id="5fae3-124">ページの高さとレポート アイテムの出現回数に基づいて、おおよそのレイアウトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-124">An approximate layout is created using the page height and the number of times that the report item appears.</span></span> <span data-ttu-id="5fae3-125">たとえば、テキスト ボックスの高さが 0.5 インチで、繰り返し 5 回出現する場合、2.5 インチが確保されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-125">For example, if a text box is .5 inches in height and repeats five times in the report, 2.5 inches are reserved.</span></span>  
  
-   <span data-ttu-id="5fae3-126">対話的な高さの設定に基づいて、複数のソフト改ページが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-126">Multiple soft page breaks are inserted based on the interactive height setting.</span></span> <span data-ttu-id="5fae3-127">HTML および ReportViewer コントロールでこの動作を抑制し、明示的な改ページでのみ制御するようにする場合は、 **対話的な高さ** の値を 0 または極端に大きな値に設定します。</span><span class="sxs-lookup"><span data-stu-id="5fae3-127">To suppress in HTML and the ReportViewer controls, and control pagination only with explicit page breaks, set the **interactive height** value to 0 or an extremely large number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5fae3-128">ソフト改ページ レンダラーでは、対話的な幅の設定は使用されません。</span><span class="sxs-lookup"><span data-stu-id="5fae3-128">The interactive width setting is not used in the soft page break renderers.</span></span>  
  
-   <span data-ttu-id="5fae3-129">ひとまとまりとして扱う必要のあるウィンドウ、孤立したアイテム、およびレポート アイテムがきちんと収まるように、レポート ページが拡大される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-129">Report pages can grow to accommodate widows, orphans and report items that need to be kept together.</span></span> <span data-ttu-id="5fae3-130">そのため、レポートが画面の幅を超えることもありますが、その場合はスライダー バーを使って閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-130">This means that the report can extend beyond the screen width and can be viewed by using slider bars.</span></span>  
  
-   <span data-ttu-id="5fae3-131">レポートには、垂直方向にのみ改ページが適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-131">Pagination is applied to reports vertically only.</span></span>  
  
-   <span data-ttu-id="5fae3-132">ページ余白は適用されません。</span><span class="sxs-lookup"><span data-stu-id="5fae3-132">Page margins are not applied.</span></span>  
  
## <a name="general-behaviors-for-pdf-image-and-print-hard-page-break-renderers"></a><span data-ttu-id="5fae3-133">PDF、画像、および印刷の一般的な動作 (ハード改ページ レンダラー)</span><span class="sxs-lookup"><span data-stu-id="5fae3-133">General Behaviors for PDF, Image, and Print (Hard Page-Break Renderers)</span></span>  
 <span data-ttu-id="5fae3-134">PDF および画像を使ってエクスポートされたレポートでは、書籍のように、常に一定のページ サイズで閲覧される印刷物としての見やすさが重視されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-134">Reports exported using PDF and Image are optimized for a book-like or printed experience where pages are a consistent size.</span></span> <span data-ttu-id="5fae3-135">改ページは、レポート本文内の特定の位置に、垂直方向および水平方向に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-135">Page breaks are inserted vertically and horizontally at specific locations within the report body.</span></span> <span data-ttu-id="5fae3-136">その位置は、ページの幅と高さの設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-136">These specific locations are determined by the page width and page height settings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fae3-137">ハード改ページ レンダラーでレポートがどのように表示されるかを確認するには、印刷プレビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="5fae3-137">To determine how a report will appear in a hard page-break renderer, use Print Preview.</span></span> <span data-ttu-id="5fae3-138">PDF 形式または画像形式で表示した場合と同じようにレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-138">The report appears as it would in a PDF or Image format.</span></span>  
  
-   <span data-ttu-id="5fae3-139">ページ番号は、左から右、次に、上から下へと付けられます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-139">Pages are numbered sequentially from left to right, then top to bottom.</span></span>  
  
-   <span data-ttu-id="5fae3-140">レポート アイテムには、論理的な改ページ (明示的に挿入した改ページ) が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-140">Logical page breaks, the page breaks that you explicitly insert, are applied to report items.</span></span> <span data-ttu-id="5fae3-141">このような改ページによって、レポート アイテムが強制的に次のページに移動される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-141">These page breaks can cause report items to push other items to the next page.</span></span>  
  
-   <span data-ttu-id="5fae3-142">ひとまとまりとして扱う必要のあるレポート アイテムの途中で、物理的な改ページが生じる場合は、それらのアイテムを次のページに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-142">If a physical page break occurs through report items that must be kept together, the items that must be kept together are moved to the next page.</span></span>  
  
-   <span data-ttu-id="5fae3-143">ページ サイズの制約により、アイテムをすべてまとめて表示したり、繰り返し表示したりできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-143">Because of page size constraints, it may not be possible to keep all the items together or to repeat items.</span></span> <span data-ttu-id="5fae3-144">その場合、レポート アイテムをページ上に収める関係上、他のアイテムと一緒に繰り返し表示するための特定の規則が無視される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fae3-144">If that occurs, the renderer might ignore certain rules for repeating with another item in order to allow the report item to fit on the page.</span></span>  
  
-   <span data-ttu-id="5fae3-145">テキスト ボックスが大きすぎて縦方向の使用可能なページ領域内に収まらないなど、アイテムを 1 つにまとめることができなかった場合、そのアイテムは、ページの物理的な境界でクリッピングされ、残りの部分が次のページから表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-145">If an item cannot be kept together, for example a text box that grows too large to fit within the vertical usable page area, then the item will be clipped at the physical page boundary and will continue on the next page.</span></span>  
  
-   <span data-ttu-id="5fae3-146">レポートには、垂直方向と水平方向の改ページが適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-146">Pagination is applied to reports vertically and horizontally.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5fae3-147">ハード改ページ レンダラーでは、対話的な幅の設定は使用されません。</span><span class="sxs-lookup"><span data-stu-id="5fae3-147">The interactive width setting is not used in the hard page break renderers.</span></span>  
  
## <a name="minimum-spacing-between-report-items"></a><span data-ttu-id="5fae3-148">レポート アイテム間の最小間隔</span><span class="sxs-lookup"><span data-stu-id="5fae3-148">Minimum Spacing Between Report Items</span></span>  
 <span data-ttu-id="5fae3-149">レポート本文内のレポート アイテムは、その内容に合わせて拡大されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-149">Report items grow within the report body to accommodate their contents.</span></span> <span data-ttu-id="5fae3-150">たとえば、マトリックス データ領域は通常、レポートのレンダリング時にページの境界を越えて拡大されます。また、テキスト ボックスの高さは、式から返されたデータに応じて調整されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-150">For example, a matrix data region typically expands across and down the page when the report is rendered, and the height of a text box adjusts depending on the data returned from an expression.</span></span>  
  
 <span data-ttu-id="5fae3-151">レポート レイアウトで定義された、レポート アイテム間の最小間隔は維持されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-151">Renderers maintain the minimum space between report items that you define in the report layout.</span></span> <span data-ttu-id="5fae3-152">レポート レイアウト上で、あるレポート アイテムを別のレポート アイテムに隣接するように配置した場合、レポート アイテム間の距離には最小距離が適用され、レポートが上下左右に拡大されても、この距離が保たれます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-152">When you place a report item adjacent to another on the report layout, the distance between the report items becomes the minimum distance that must be maintained as the report grows horizontally or vertically.</span></span> <span data-ttu-id="5fae3-153">たとえば、レポートにマトリックス データ領域を追加した後、そのマトリックスの 0.25 インチ右側に四角形を追加した場合、マトリックスのサイズが大きくなっても、その間隔が維持されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-153">For example, if you add a matrix data region to a report and then add a rectangle .25 inches to the right of the matrix, that space is maintained as the matrix grows.</span></span> <span data-ttu-id="5fae3-154">各アイテムは、左側にあるアイテムとの間の最小距離が維持されるように右に移動します。</span><span class="sxs-lookup"><span data-stu-id="5fae3-154">Each item moves to the right to maintain the minimum distance from items that end to the left of it.</span></span>  
  
## <a name="page-headers-and-footers"></a><span data-ttu-id="5fae3-155">ページ ヘッダーとページ フッター</span><span class="sxs-lookup"><span data-stu-id="5fae3-155">Page Headers and Footers</span></span>  
 <span data-ttu-id="5fae3-156">ページ ヘッダーとページ フッターは、レンダリングされた各ページの最上部と最下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-156">Page headers and footers appear at the top and bottom of each rendered page.</span></span> <span data-ttu-id="5fae3-157">ページ ヘッダーとページ フッターには、罫線の色、罫線のスタイル、および罫線の幅を定義できます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-157">You can format the page header and footer so that there is a border color, border style, and border width.</span></span> <span data-ttu-id="5fae3-158">背景色や背景画像を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-158">You can also add a background color or background image.</span></span> <span data-ttu-id="5fae3-159">選択した形式によっては、これらの書式設定オプションがすべてレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-159">These formatting options are all rendered, depending on the format that you choose.</span></span>  
  
 <span data-ttu-id="5fae3-160">HTML 形式または MHTML 形式でレンダリングした場合、ページ ヘッダーおよびページ フッターには次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-160">The following rules apply to page headers and footers when rendered in the HTML or MHTML rendering format:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fae3-161">Excel でのヘッダーとフッターの表示方法の詳細については、「[Microsoft Excel へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fae3-161">For information about how Excel renders headers and footers, see [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="5fae3-162">Word でのヘッダーとフッターの表示方法の詳細については、「[Microsoft Word へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fae3-162">For information about how Word renders headers and footers, see [Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="5fae3-163">ヘッダーとフッターが存在する場合、すべてのページの使用可能なページ領域内の最上部と最下部にレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-163">When present, the header and footer is rendered at the top and bottom of every page within the usable page area.</span></span>  
  
-   <span data-ttu-id="5fae3-164">ヘッダーまたはフッターが非表示にされているページでは、それらがレンダリングされなくても、使用可能なページ領域内には、ヘッダーまたはフッターの高さに必要な領域が確保されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-164">On pages where the header or footer is hidden, the height of the header or footer is still reserved within the usable page area, even though the header or footer is not rendered.</span></span>  
  
-   <span data-ttu-id="5fae3-165">ヘッダーまたはフッターの内容がその境界を越えた場合、ヘッダーまたはフッターのサイズがその内容に応じて拡大されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-165">If the contents of the header or footer grows beyond the boundaries of the header or footer, the header or footer increases in size to accommodate the contents.</span></span>  
  
 <span data-ttu-id="5fae3-166">PDF 形式または画像形式でレンダリングした場合、ページ ヘッダーおよびページ フッターには次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-166">The following rules apply to page headers and footers when rendered in the PDF or Image rendering format:</span></span>  
  
-   <span data-ttu-id="5fae3-167">ヘッダーまたはフッターは、すべてのページの使用可能なページ領域内の最上部と最下部にレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-167">The header or footer is rendered at the top and bottom of every page within the usable page area.</span></span>  
  
-   <span data-ttu-id="5fae3-168">ヘッダーまたはフッターが非表示にされているページでは、それらがレンダリングされなくても、使用可能なページ領域内には、ヘッダーまたはフッターの高さに必要な領域が確保されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-168">On pages where the header or footer is hidden, the height of the header or footer is still reserved within the usable page area, even though the header or footer is not rendered.</span></span>  
  
-   <span data-ttu-id="5fae3-169">ヘッダーとフッターは拡大も縮小もされません。</span><span class="sxs-lookup"><span data-stu-id="5fae3-169">The header and footer do not grow or shrink.</span></span> <span data-ttu-id="5fae3-170">ヘッダーまたはフッターは、その作成時に指定された高さですべてのページにレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-170">They are rendered on every page at the height specified when you created the header or footer.</span></span>  
  
-   <span data-ttu-id="5fae3-171">レポート内の列数に関係なく、1 ページあたりに存在するヘッダーとフッターはそれぞれ 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="5fae3-171">Regardless of the number of columns within the report, there is only one header and footer per page.</span></span>  
  
-   <span data-ttu-id="5fae3-172">ヘッダーまたはフッターの内容がその境界を越えた場合、内容がクリッピングされます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-172">If the contents of the header or footer grow beyond the boundaries of the header or footer, the contents are clipped.</span></span>  
  
-   <span data-ttu-id="5fae3-173">レポートをサブレポートとしてレンダリングした場合、元の RDL ファイル内で定義されたヘッダーおよびフッターはレンダリングされません。</span><span class="sxs-lookup"><span data-stu-id="5fae3-173">Headers and footers that are defined in the original RDL file are not rendered when the report is rendered as a subreport.</span></span>  
  
## <a name="logical-page-breaks"></a><span data-ttu-id="5fae3-174">論理的な改ページ</span><span class="sxs-lookup"><span data-stu-id="5fae3-174">Logical Page Breaks</span></span>  
 <span data-ttu-id="5fae3-175">論理的な改ページとは、ユーザーによってレポート アイテムやレポート グループの前または後に挿入される改ページをいいます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-175">Logical page breaks are page breaks that you insert before or after report items or groups.</span></span> <span data-ttu-id="5fae3-176">改ページを使用することにより、レポートのレンダリング時またはエクスポート時に最も見やすくなるような形で、その内容をレポート ページに収めることができます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-176">Page breaks help to determine how the content is fitted to a report page for optimal viewing when rendering or exporting the report.</span></span>  
  
 <span data-ttu-id="5fae3-177">論理的な改ページのレンダリングには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-177">The following rules apply when rendering logical page breaks:</span></span>  
  
-   <span data-ttu-id="5fae3-178">常に非表示になるレポート アイテムや、可視性が別のレポート アイテムのクリックによって制御されるレポート アイテムでは、論理的な改ページが無視されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-178">Logical page breaks are ignored for report items that are constantly hidden and for report items where the visibility is controlled by clicking another report item.</span></span>  
  
-   <span data-ttu-id="5fae3-179">表示と非表示が条件に応じて変わるアイテムには、レポートをレンダリングした時点で可視状態であった場合に、論理的な改ページが適用されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-179">Logical page breaks are applied on conditionally visible items if they are currently visible at the time the report is rendered.</span></span>  
  
-   <span data-ttu-id="5fae3-180">論理的な改ページが適用されたレポート アイテムと、そのピア レポート アイテム間のスペースは確保されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-180">Space is preserved between the report item with the logical page break and its peer report items.</span></span>  
  
-   <span data-ttu-id="5fae3-181">レポート アイテムの前に論理的な改ページが挿入されている場合、そのレポート アイテムは強制的に次のページに移動されます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-181">Logical page breaks that are inserted before a report item push the report item down to the next page.</span></span> <span data-ttu-id="5fae3-182">レポート アイテムは、次のページの一番上にレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="5fae3-182">The report item is rendered at the top of the next page.</span></span>  
  
-   <span data-ttu-id="5fae3-183">テーブル セルまたはマトリックス セル内のアイテムで定義された論理的な改ページは保持されません。</span><span class="sxs-lookup"><span data-stu-id="5fae3-183">Logical page breaks defined on items in table or matrix cells are not kept.</span></span> <span data-ttu-id="5fae3-184">これは、一覧にあるアイテムには当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="5fae3-184">This does not apply to items in lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fae3-185">参照</span><span class="sxs-lookup"><span data-stu-id="5fae3-185">See Also</span></span>  
 <span data-ttu-id="5fae3-186">[さまざまなレポート表示拡張機能の対話機能 &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="5fae3-186">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="5fae3-187">[HTML での表示 &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/rendering-to-html-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5fae3-187">[Rendering to HTML &#40;Report Builder and SSRS&#41;](../report-builder/rendering-to-html-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5fae3-188">ページ レイアウトとレンダリング &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fae3-188">Page Layout and Rendering &#40;Report Builder and SSRS&#41;</span></span>](page-layout-and-rendering-report-builder-and-ssrs.md)  
  
  
