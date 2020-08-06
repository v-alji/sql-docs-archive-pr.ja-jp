---
title: HTML での表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf559b0a-499a-4d74-b520-b382b87e0b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 44f43d079aa81b566a39fe053bdf80c7800fc500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633778"
---
# <a name="rendering-to-html-report-builder-and-ssrs"></a><span data-ttu-id="e09f8-102">HTML での表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e09f8-102">Rendering to HTML (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e09f8-103">HTML 表示拡張機能では、HTML 形式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="e09f8-103">The HTML rendering extension renders a report in HTML format.</span></span> <span data-ttu-id="e09f8-104">また、完全な HTML ページを生成することも、他の HTML ページに埋め込むための HTML の一部分を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-104">The rendering extension can also produce fully formed HTML pages or fragments of HTML to embed in other HTML pages.</span></span> <span data-ttu-id="e09f8-105">すべての HTML は、UTF-8 エンコードで生成されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-105">All HTML is generated with UTF-8 encoding.</span></span>  
  
 <span data-ttu-id="e09f8-106">HTML 表示拡張機能は、レポート マネージャーで実行する場合など、ブラウザーで表示されるレポートの既定の表示拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="e09f8-106">The HTML rendering extension is the default rendering extension for reports that are viewed in a browser, including when run in Report Manager.</span></span>  
  
 <span data-ttu-id="e09f8-107">HTML 表示拡張機能は、レポート マネージャーで実行する場合など、ブラウザーで表示されるレポートの既定の表示拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="e09f8-107">The HTML rendering extension is the default rendering extension for reports that are viewed in a browser, including when run in Report Manager.</span></span> <span data-ttu-id="e09f8-108">HTML 表示拡張機能を使用すると、HTML を部分的に表示することも、完全な HTML ドキュメントとして表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-108">The HTML rendering extension can render HTML as a fragment or as a full HTML document.</span></span> <span data-ttu-id="e09f8-109">HTML が部分的な場合、HTML ドキュメントの `HEAD` タグ、`HTML` タグ、および `BODY` タグは削除されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-109">If the HTML is a fragment, the `HEAD`, `HTML`, and `BODY` tags of the HTML document are removed.</span></span> <span data-ttu-id="e09f8-110">表示されるのは、`BODY` タグのコンテンツのみです。</span><span class="sxs-lookup"><span data-stu-id="e09f8-110">Only the contents of the `BODY` tag are rendered.</span></span> <span data-ttu-id="e09f8-111">これは、他のアプリケーションで作成した HTML に HTML を埋め込む場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e09f8-111">This is useful for embedding the HTML in the HTML produced by another application.</span></span>  
  
 <span data-ttu-id="e09f8-112">状況によっては、レポート パラメーターを使用して、レポートが HTML で表示される際にスクリプト インジェクション攻撃を開始することも可能であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e09f8-112">In some scenarios, report parameters can be used to launch script injection attacks when rendering reports to HTML.</span></span> <span data-ttu-id="e09f8-113">レポートのセキュリティ保護の詳細については、「 [レポートとリソースの保護](../security/secure-reports-and-resources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e09f8-113">For more information about securing reports, see [Secure Reports and Resources](../security/secure-reports-and-resources.md).</span></span>  
  
 <span data-ttu-id="e09f8-114">ブラウザーの詳細については、「 [Planning for Reporting Services」および「Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e09f8-114">For more information about browsers, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rendering-in-mhtml"></a><a name="RenderingMHTML"></a> <span data-ttu-id="e09f8-115">MHTML での表示</span><span class="sxs-lookup"><span data-stu-id="e09f8-115">Rendering in MHTML</span></span>  
 <span data-ttu-id="e09f8-116">HTML 表示拡張機能を使用すると、MHTML (MIME Encapsulation of Aggregate HTML Documents) でレポートを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-116">The HTML rendering extension can also render reports in MHTML (MIME Encapsulation of Aggregate HTML Documents).</span></span> <span data-ttu-id="e09f8-117">MHTML は、HTML を拡張して、画像などのエンコードされているオブジェクトを HTML ドキュメントに埋め込むことができるようにしたものです。</span><span class="sxs-lookup"><span data-stu-id="e09f8-117">MHTML extends HTML to embed encoded objects, such as images, in the HTML document.</span></span> <span data-ttu-id="e09f8-118">MHTML 表示拡張機能を使用すると、画像、ドキュメント、その他のバイナリ ファイルなどのリソースを、レポート HTML 内部の MIME 構造として単一のファイルに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-118">Using the MHTML rendering extension, you can embed resources such as images, documents, or other binary files as MIME structures within the report HTML, into a single file.</span></span> <span data-ttu-id="e09f8-119">また、MHTML レポートは、すべてのリソースがレポートの中に含まれるので、電子メール メッセージに埋め込むのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-119">MHTML reports are also useful for embedding within e-mail messages because all resources are included with the report.</span></span> <span data-ttu-id="e09f8-120">実際に MHTML を表示するのは HTML 表示拡張機能ですが、この機能を MHTML 表示拡張機能と呼ぶこともあります。</span><span class="sxs-lookup"><span data-stu-id="e09f8-120">Although it is actually the HTML rendering extension that renders MHTML, this functionality may also be referred to as the MHTML rendering extension.</span></span>  
  
##  <a name="browser-support"></a><a name="BrowserSupport"></a><span data-ttu-id="e09f8-121">ブラウザーサポート</span><span class="sxs-lookup"><span data-stu-id="e09f8-121">Browser Support</span></span>  
 <span data-ttu-id="e09f8-122">この表示拡張機能では、次のブラウザー バージョンをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e09f8-122">This rendering extension supports the following browser versions:</span></span>  
  
-   <span data-ttu-id="e09f8-123">Internet Explorer 5.5 以降</span><span class="sxs-lookup"><span data-stu-id="e09f8-123">Internet Explorer 5.5 and later</span></span>  
  
-   <span data-ttu-id="e09f8-124">Firefox 1.5 以降</span><span class="sxs-lookup"><span data-stu-id="e09f8-124">Firefox 1.5 and later</span></span>  
  
-   <span data-ttu-id="e09f8-125">Safari 3.0 以降</span><span class="sxs-lookup"><span data-stu-id="e09f8-125">Safari 3.0 and later</span></span>  
  
 <span data-ttu-id="e09f8-126">各ブラウザーで適切に処理されるようにするため、表示されるレポートはブラウザーによって多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e09f8-126">Due to cross browser considerations, the rendered report may vary slightly from browser to browser.</span></span> <span data-ttu-id="e09f8-127">たとえば、テキスト ボックスには WritingMode というプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-127">For example, the text box contains a property called WritingMode.</span></span> <span data-ttu-id="e09f8-128">このプロパティは Firefox でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e09f8-128">This property is not supported in Firefox.</span></span>  
  
##  <a name="html-specific-rendering-rules"></a><a name="HTMLSpecificRenderingRules"></a> <span data-ttu-id="e09f8-129">HTML 固有の表示規則</span><span class="sxs-lookup"><span data-stu-id="e09f8-129">HTML-Specific Rendering Rules</span></span>  
 <span data-ttu-id="e09f8-130">表示する際は、次の HTML 固有の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-130">The following HTML-specific rules are applied when rendering:</span></span>  
  
-   <span data-ttu-id="e09f8-131">各 `ReportItems` コレクション内にアイテムが複数存在する場合は、レンダラーによって、すべてのアイテムを格納するための HTML テーブル構造が構築されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-131">The renderer builds an HTML table structure to contain all of the items in each `ReportItems` collection, if there is more than one.</span></span>  
  
-   <span data-ttu-id="e09f8-132">テーブル構造内の各アイテムは 1 つのセルを占有します。</span><span class="sxs-lookup"><span data-stu-id="e09f8-132">Every item within the table structure occupies a single cell.</span></span>  
  
-   <span data-ttu-id="e09f8-133">空のセルをできる限りまとめて HTML のサイズを小さくします。</span><span class="sxs-lookup"><span data-stu-id="e09f8-133">Empty cells are collapsed together as much as possible to reduce the size of the HTML.</span></span>  
  
-   <span data-ttu-id="e09f8-134">ブラウザーでテーブルを表示する速度を上げるために、上端に空のセルの行が追加され、左端に 1 列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-134">A row of empty cells is added to the top edge and another column to the left edge to improve the speed at which browsers can render the table.</span></span>  
  
-   <span data-ttu-id="e09f8-135">テーブルのアイテムが格納されていない行や列、つまりアイテムの間隔は、幅と高さが固定されています。</span><span class="sxs-lookup"><span data-stu-id="e09f8-135">Table rows or columns that contain no items, just gaps between items, are given fixed widths and heights.</span></span>  
  
-   <span data-ttu-id="e09f8-136">その他すべての行と列は、各レポート アイテムのサイズに応じて拡張できます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-136">All other rows and columns are allowed to grow depending on the size of each report item.</span></span>  
  
-   <span data-ttu-id="e09f8-137">すべての座標とレポート アイテム サイズはミリメートルに変換されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-137">All coordinates and report item sizes are converted to millimeters.</span></span> <span data-ttu-id="e09f8-138">スタイル プロパティなどの他のすべてのサイズは、元の単位のままになります。</span><span class="sxs-lookup"><span data-stu-id="e09f8-138">All other sizes, including style properties, retain their original units.</span></span> <span data-ttu-id="e09f8-139">0.2 mm に満たないサイズや位置の差は 0 mm として扱われます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-139">Size and position differences smaller than .2mm are treated as 0mm.</span></span>  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="e09f8-140">双</span><span class="sxs-lookup"><span data-stu-id="e09f8-140">Interactivity</span></span>  
 <span data-ttu-id="e09f8-141">HTML では、いくつかの対話型要素がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e09f8-141">Some interactive elements are supported in HTML.</span></span> <span data-ttu-id="e09f8-142">具体的な動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="e09f8-142">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="e09f8-143">表示/非表示</span><span class="sxs-lookup"><span data-stu-id="e09f8-143">Show and Hide</span></span>  
 <span data-ttu-id="e09f8-144">表示の切り替えが可能なレポート アイテムは、切り替えイメージの展開 (+) と折りたたみ (-) と共に表示され、クリック可能です。</span><span class="sxs-lookup"><span data-stu-id="e09f8-144">A report item whose visibility can be toggled is rendered with a +/- toggle image and is clickable.</span></span> <span data-ttu-id="e09f8-145">アイテムをクリックすると、変更後の表示/非表示状態で出力を再表示するために、サーバーへのコールバックが行われます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-145">When the item is clicked, a call back to the server takes place in order to re-render the output with the changed show or hide state.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="e09f8-146">ドキュメント マップ</span><span class="sxs-lookup"><span data-stu-id="e09f8-146">Document Map</span></span>  
 <span data-ttu-id="e09f8-147">ドキュメント マップ ラベルが表示されると、ビューアー コントロールのドキュメント マップを使用することでそのラベルに移動できます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-147">Document map labels are rendered and can be navigated to by using the document map in the viewer control.</span></span> <span data-ttu-id="e09f8-148">データ領域のヘッダーが省略される場合、ラベルは最初の子セルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-148">For omitted data region headers, labels are rendered on the first child cell.</span></span> <span data-ttu-id="e09f8-149">子セルが存在しない場合、ラベルはその前にある子に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-149">If there is no child cell present, the label is rendered on the child that precedes it.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="e09f8-150">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="e09f8-150">Bookmarks</span></span>  
 <span data-ttu-id="e09f8-151">ブックマーク リンクは、ハイパーリンクとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-151">Bookmark links are rendered and appear as hyperlinks.</span></span> <span data-ttu-id="e09f8-152">ブックマーク対象が表示されると、ブックマーク リンクをクリックすることでその対象に移動できます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-152">Bookmark targets are rendered and can be navigated to by clicking the bookmark links.</span></span> <span data-ttu-id="e09f8-153">ブックマーク リンクをクリックすると、レポート内で最初に出現する対象のブックマーク ラベルに移動します。さらに、可能な場合は、ブックマーク リンクがウィンドウの上部に表示されるようにブラウザーがスクロールされます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-153">When a bookmark link is clicked, the report goes to the first occurrence of the target bookmark label and, when possible, the browser is scrolled so that the bookmark link is at the top of the window.</span></span> <span data-ttu-id="e09f8-154">HTML アンカー ( \<a> ) タグは、ブックマークターゲットをマークするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-154">HTML anchor (\<a>) tags are used to mark bookmark targets.</span></span>  
  
### <a name="interactive-sorting"></a><span data-ttu-id="e09f8-155">対話的な並べ替え</span><span class="sxs-lookup"><span data-stu-id="e09f8-155">Interactive Sorting</span></span>  
 <span data-ttu-id="e09f8-156">テキスト ボックスでユーザーによる並べ替えが定義されている場合、HTML 表示拡張機能により、テキスト ボックス内で各項目の右側に並べ替えアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-156">If a text box has user sort defined, the HTML rendering extension renders the sort icons in the text box to the right of its contents.</span></span> <span data-ttu-id="e09f8-157">ユーザーによる並べ替えが定義されているテキスト ボックスがレポートに含まれている場合は、JavaScript が表示されます。このスクリプトにより、並べ替えイメージをクリックしたときにサーバーへのポストバックが行われます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-157">If a report contains any text box where user sort is defined, JavaScript is rendered that causes a postback to the server when the sort image is clicked.</span></span>  
  
### <a name="hyperlinks-and-drillthrough"></a><span data-ttu-id="e09f8-158">ハイパーリンクとドリルスルー</span><span class="sxs-lookup"><span data-stu-id="e09f8-158">Hyperlinks and Drillthrough</span></span>  
 <span data-ttu-id="e09f8-159">ハイパーリンクとドリルスルーリンクは、定義されているアイテムを HTML アンカー () タグで囲むことによって、レポートアイテムのハイパーリンクとして表示され \<a> ます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-159">Hyperlinks and drillthrough links are rendered as hyperlinks on report items using the HTML anchor (\<a>) tags around the item on which they are defined.</span></span>  
  
### <a name="search"></a><span data-ttu-id="e09f8-160">検索</span><span class="sxs-lookup"><span data-stu-id="e09f8-160">Search</span></span>  
 <span data-ttu-id="e09f8-161">検索機能を使用すると、ユーザーは、レポート内で文字列を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-161">The Search feature allows users to search for a string of text within the report.</span></span>  
  
 <span data-ttu-id="e09f8-162">追加の検索機能は、ReportViewer Web フォーム コントロールによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-162">Additional search and find functionality is provided by the ReportViewer Web Forms control.</span></span>  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="e09f8-163">デバイス情報の設定</span><span class="sxs-lookup"><span data-stu-id="e09f8-163">Device Information Settings</span></span>  
 <span data-ttu-id="e09f8-164">デバイス情報設定を変更することによって、このレンダラーに関する既定の設定の一部 (表示モードなど) を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="e09f8-164">You can change some default settings for this renderer, including which mode to render in, by changing the device information settings.</span></span> <span data-ttu-id="e09f8-165">詳細については、「 [HTML デバイス情報設定](../html-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e09f8-165">For more information, see [HTML Device Information Settings](../html-device-information-settings.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="e09f8-166">参照</span><span class="sxs-lookup"><span data-stu-id="e09f8-166">See Also</span></span>  
 <span data-ttu-id="e09f8-167">[Reporting Services &#40;レポートビルダーおよび SSRS&#41;での改ページ](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e09f8-167">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e09f8-168">[レポートビルダーおよび SSRS&#41;&#40;レンダリング動作](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e09f8-168">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e09f8-169">[さまざまなレポート表示拡張機能の対話機能 &#40;レポートビルダーと SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="e09f8-169">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="e09f8-170">[レポートビルダーおよび SSRS&#41;&#40;レポートアイテムのレンダリング](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e09f8-170">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e09f8-171">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e09f8-171">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
