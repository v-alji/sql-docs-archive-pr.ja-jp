---
title: PDF ファイルへのエクスポート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f22497b7-f6c1-4c7b-b831-8c731e26ae37
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b4a324ad40d01d302196fe40ffb4232deb62a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631617"
---
# <a name="exporting-to-a-pdf-file-report-builder-and-ssrs"></a><span data-ttu-id="442cf-102">PDF ファイルへのエクスポート (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="442cf-102">Exporting to a PDF File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="442cf-103">PDF 表示拡張機能を使用すると、Adobe Acrobat および PDF 1.3 をサポートするその他のサードパーティ製 PDF ビューアーで開くことのできるファイルとしてレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-103">The PDF rendering extension renders a report to files that can be opened in Adobe Acrobat and other third-party PDF viewers that support PDF 1.3.</span></span> <span data-ttu-id="442cf-104">PDF 1.3 は Adobe Acrobat 4 以降のバージョンと互換性がありますが、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では Adobe Acrobat 6 以降がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="442cf-104">Although PDF 1.3 is compatible with Adobe Acrobat 4.0 and later versions, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supports Adobe Acrobat 6 or later.</span></span> <span data-ttu-id="442cf-105">この表示拡張機能では、レポートの表示処理に Adobe 製のソフトウェアは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="442cf-105">The rendering extension does not require Adobe software to render the report.</span></span> <span data-ttu-id="442cf-106">ただし、レポートを PDF 形式で表示または印刷するには、Adobe Acrobat などの PDF ビューアーが必要です。</span><span class="sxs-lookup"><span data-stu-id="442cf-106">However, PDF viewers such as Adobe Acrobat are required to view or print a report in PDF format.</span></span>  
  
 <span data-ttu-id="442cf-107">PDF 表示拡張機能では ANSI 文字がサポートされ、日本語、韓国語、繁体中国語、簡体中国語、キリル文字、ヘブライ語、アラビア語の Unicode 文字を変換できます (一部制限事項があります)。</span><span class="sxs-lookup"><span data-stu-id="442cf-107">The PDF rendering extension supports ANSI characters and can translate Unicode characters from Japanese, Korean, Traditional Chinese, Simplified Chinese, Cyrillic, Hebrew, and Arabic with certain limitations.</span></span> <span data-ttu-id="442cf-108">制限の詳細については、「[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](export-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="442cf-108">For more information about the limitations, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="442cf-109">PDF レンダラーは物理的なページ レンダラーなので、HTML や Excel などの他のレンダラーとは異なり、改ページ機能があります。</span><span class="sxs-lookup"><span data-stu-id="442cf-109">The PDF renderer is a physical page renderer and, therefore, has pagination behavior that differs from other renderers such as HTML and Excel.</span></span> <span data-ttu-id="442cf-110">ここでは、PDF レンダラー固有の情報を提供し、規則の例外について説明します。</span><span class="sxs-lookup"><span data-stu-id="442cf-110">This topic provides PDF renderer-specific information and describes exceptions to the rules.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="font-embedding"></a><a name="FontRequirements"></a><span data-ttu-id="442cf-111">フォントの埋め込み</span><span class="sxs-lookup"><span data-stu-id="442cf-111">Font Embedding</span></span>  
 <span data-ttu-id="442cf-112">PDF 表示拡張機能は、可能な場合、レポートを PDF ファイルで表示するために必要な各フォントのサブセットを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="442cf-112">When possible, the PDF rendering extension embeds the subset of each font that is needed to display the report in the PDF file.</span></span> <span data-ttu-id="442cf-113">レポートに使用されているフォントが、レポート サーバーにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="442cf-113">Fonts that are used in the report must be installed on the report server.</span></span> <span data-ttu-id="442cf-114">レポート サーバーは、レポートを PDF 形式で生成する際に、レポートで参照されるフォントに保存されている情報を使用して、PDF ファイル内の文字マッピングを作成します。</span><span class="sxs-lookup"><span data-stu-id="442cf-114">When the report server generates a report in PDF format, it uses the information stored in the font referenced by the report to create character mappings within the PDF file.</span></span> <span data-ttu-id="442cf-115">参照されているフォントがレポート サーバーにインストールされていないと、結果の PDF ファイルに適切なマッピングが作成されず、正しく表示されなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="442cf-115">If the referenced font is not installed on the report server, the resulting PDF file might not contain the correct mappings and might not display correctly when viewed.</span></span>  
  
 <span data-ttu-id="442cf-116">フォントは、次の条件が該当する場合、PDF ファイルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="442cf-116">Fonts are embedded in the PDF file when the following conditions apply:</span></span>  
  
-   <span data-ttu-id="442cf-117">フォントの埋め込みがフォントの作成者によって許可されている。</span><span class="sxs-lookup"><span data-stu-id="442cf-117">Font embedding privileges are granted by the font author.</span></span> <span data-ttu-id="442cf-118">インストールされているフォントには、そのフォントの作成者がドキュメントへのフォントの埋め込みを許可しているかどうかを示すプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="442cf-118">Installed fonts include a property that indicates whether the font author intends to allow embedding a font in a document.</span></span> <span data-ttu-id="442cf-119">このプロパティの値が EMBED_NOEMBEDDING である場合、フォントは PDF ファイルに埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="442cf-119">If the property value is EMBED_NOEMBEDDING, the font is not embedded in the PDF file.</span></span> <span data-ttu-id="442cf-120">詳細については、msdn.microsoft.com の「TTGetEmbeddingType」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="442cf-120">For more information, see "TTGetEmbeddingType" on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="442cf-121">TrueType フォントである。</span><span class="sxs-lookup"><span data-stu-id="442cf-121">The Font is TrueType.</span></span>  
  
-   <span data-ttu-id="442cf-122">フォントがレポート内の可視アイテムによって参照されている。</span><span class="sxs-lookup"><span data-stu-id="442cf-122">Fonts are referenced by visible items in a report.</span></span> <span data-ttu-id="442cf-123">フォントを参照しているアイテムの "非表示" プロパティが True の場合、レンダリング データを表示する必要がないため、そのフォントはファイルに追加されません。</span><span class="sxs-lookup"><span data-stu-id="442cf-123">If a font is referenced by an item that has the Hidden property set to True, the font is not needed to display rendered data and will not be included in the file.</span></span> <span data-ttu-id="442cf-124">レンダリングされたレポート データを表示する必要がある場合にのみ、フォントの埋め込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="442cf-124">Fonts are embedded only when they are needed to display the rendered report data.</span></span>  
  
 <span data-ttu-id="442cf-125">以上の条件をすべて満たしている場合、フォントは PDF ファイルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="442cf-125">If all of these conditions are met for a font, the font is embedded in the PDF file.</span></span> <span data-ttu-id="442cf-126">以上の条件が 1 つでも満たされなかった場合、そのフォントは PDF ファイルに埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="442cf-126">If one or more of these conditions is not met, the font is not embedded in the PDF file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="442cf-127">ただし、条件が満たされていても、フォントが PDF ファイルに埋め込まれないという状況が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="442cf-127">Although the conditions are met, there is one circumstance under which fonts are not embedded in the PDF file.</span></span> <span data-ttu-id="442cf-128">使用されているフォントが、一般に標準の Type 1 フォントまたは Base 14 フォントとして知られている PDF 仕様のフォントの場合、フォントは ANSI コンテンツには埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="442cf-128">If the fonts used are the ones in the PDF specification that are commonly known as standard type 1 fonts or the base fourteen fonts, then fonts are not embedded for ANSI content.</span></span>  
  
  
  
### <a name="fonts-on-the-client-computer"></a><span data-ttu-id="442cf-129">クライアント コンピューター上のフォント</span><span class="sxs-lookup"><span data-stu-id="442cf-129">Fonts on the Client Computer</span></span>  
 <span data-ttu-id="442cf-130">フォントが PDF ファイルに埋め込まれている場合、レポートを閲覧するコンピューター (クライアント コンピューター) にフォントがインストールされている必要はありません。フォントがインストールされていなくても、レポートは正しく表示されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-130">When a font is embedded in the PDF file, the computer that is used to view the report (the client computer) does not need to have the font installed for the report to display correctly.</span></span>  
  
 <span data-ttu-id="442cf-131">フォントが PDF ファイルに埋め込まれていない場合、レポートを正しく表示するためには、クライアント コンピューターに適切なフォントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="442cf-131">When a font is not embedded in the PDF file, the client computer must have the correct font installed for the report to display correctly.</span></span> <span data-ttu-id="442cf-132">クライアント コンピューターにフォントがインストールされていなかった場合、PDF ファイルには、サポートされていない文字の代わりに疑問符 (?) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-132">If the font is not installed on the client computer, the PDF file displays a question mark character (?) for unsupported characters.</span></span>  
  
### <a name="verifying-fonts-in-a-pdf-file"></a><span data-ttu-id="442cf-133">PDF ファイル内のフォントの検証</span><span class="sxs-lookup"><span data-stu-id="442cf-133">Verifying Fonts in a PDF File</span></span>  
 <span data-ttu-id="442cf-134">PDF 出力に差異が発生することが最も多い状況は、ラテン文字以外の文字をサポートしないフォントがレポートで使用されているときに、ラテン文字以外の文字がレポートに追加された場合です。</span><span class="sxs-lookup"><span data-stu-id="442cf-134">Differences in PDF output occur most often when a font that does not support non-Latin characters is used in a report and then non-Latin characters are added to the report.</span></span> <span data-ttu-id="442cf-135">PDF 表示出力をレポート サーバーとクライアント コンピューターの両方でテストし、レポートが正しく表示されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="442cf-135">You should test the PDF rendering output on both the report server and the client computers to verify that the report renders correctly.</span></span>  
  
 <span data-ttu-id="442cf-136">レポートのプレビュー表示やエクスポートした HTML 表示を過信しないでください。プレビューの場合はグラフィカル デザイン インターフェイスによって、HTML の場合は Microsoft Internet Explorer によって、それぞれフォントが自動的に置き換えられるため、レポートが正しく表示されているように見えます。</span><span class="sxs-lookup"><span data-stu-id="442cf-136">Do not rely on viewing the report in Preview or exporting to HTML because the report will look correct due to automatic font substitution performed by the graphical design interface or by Microsoft Internet Explorer, respectively.</span></span> <span data-ttu-id="442cf-137">Unicode グリフがサーバーに存在しない場合、文字は疑問符 (?) で置き換えられることがあります。</span><span class="sxs-lookup"><span data-stu-id="442cf-137">If there are Unicode Glyphs missing on the server, you may see characters replaced with a question mark (?).</span></span> <span data-ttu-id="442cf-138">フォントがクライアントに存在しない場合、文字は四角形 ( ) で置き換えられることがあります。</span><span class="sxs-lookup"><span data-stu-id="442cf-138">If there is a font missing on the client, you may see characters replaced with boxes (□).</span></span>  
  
 <span data-ttu-id="442cf-139">PDF ファイルに埋め込まれているフォントは、ファイルと共に保存される Fonts プロパティにメタデータとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-139">The fonts that are embedded in the PDF file are included in the Fonts property that is saved with the file, as metadata.</span></span>  
  
##  <a name="metadata"></a><a name="Metadata"></a> <span data-ttu-id="442cf-140">メタデータ</span><span class="sxs-lookup"><span data-stu-id="442cf-140">Metadata</span></span>  
 <span data-ttu-id="442cf-141">PDF 表示拡張機能では、レポート レイアウトに加えて PDF ドキュメント情報ディクショナリに次のメタデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="442cf-141">In addition to the report layout, the PDF rendering extension writes the following metadata to the PDF Document Information Dictionary.</span></span>  
  
|<span data-ttu-id="442cf-142">PDF プロパティ</span><span class="sxs-lookup"><span data-stu-id="442cf-142">PDF property</span></span>|<span data-ttu-id="442cf-143">作成元</span><span class="sxs-lookup"><span data-stu-id="442cf-143">Created from</span></span>|  
|------------------|------------------|  
|`Title`|<span data-ttu-id="442cf-144">`Name` RDL 要素の `Report` 属性です。</span><span class="sxs-lookup"><span data-stu-id="442cf-144">The `Name` attribute of the `Report` RDL element.</span></span>|  
|`Author`|<span data-ttu-id="442cf-145">`Author` RDL 要素です。</span><span class="sxs-lookup"><span data-stu-id="442cf-145">The `Author` RDL element.</span></span>|  
|`Subject`|<span data-ttu-id="442cf-146">`Description` RDL 要素です。</span><span class="sxs-lookup"><span data-stu-id="442cf-146">The `Description` RDL element.</span></span>|  
|`Creator`|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="442cf-147">製品の名前およびバージョンです。</span><span class="sxs-lookup"><span data-stu-id="442cf-147">product name and version.</span></span>|  
|`Producer`|<span data-ttu-id="442cf-148">表示拡張機能の名前とバージョンです。</span><span class="sxs-lookup"><span data-stu-id="442cf-148">Rendering extension name and version.</span></span>|  
|`CreationDate`|<span data-ttu-id="442cf-149">PDF `datetime` 形式でのレポートの実行時間です。</span><span class="sxs-lookup"><span data-stu-id="442cf-149">Report execution time in PDF `datetime` format.</span></span>|  
  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="442cf-150">双</span><span class="sxs-lookup"><span data-stu-id="442cf-150">Interactivity</span></span>  
 <span data-ttu-id="442cf-151">PDF では、いくつかの対話型要素がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="442cf-151">Some interactive elements are supported in PDF.</span></span> <span data-ttu-id="442cf-152">具体的な動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="442cf-152">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="442cf-153">表示/非表示</span><span class="sxs-lookup"><span data-stu-id="442cf-153">Show and Hide</span></span>  
 <span data-ttu-id="442cf-154">PDF では、動的な表示/非表示要素がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="442cf-154">Dynamic show and hide elements are not supported in PDF.</span></span> <span data-ttu-id="442cf-155">PDF ドキュメントは、レポート内にあるすべてのアイテムの現在の状態に合わせて表示されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-155">The PDF document is rendered to match the current state of any items in the report.</span></span> <span data-ttu-id="442cf-156">たとえば、レポートを最初に実行したときにアイテムが表示されている場合、そのアイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-156">For example, if the item is displayed when the report is run initially, then the item is rendered.</span></span> <span data-ttu-id="442cf-157">切り替え可能な画像は、レポートのエクスポート時に非表示になっている場合、表示されません。</span><span class="sxs-lookup"><span data-stu-id="442cf-157">Images that can be toggled are not rendered, if they are hidden when the report is exported.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="442cf-158">ドキュメント マップ</span><span class="sxs-lookup"><span data-stu-id="442cf-158">Document Map</span></span>  
 <span data-ttu-id="442cf-159">ドキュメント マップ ラベルがレポートに存在する場合、PDF ファイルにドキュメント アウトラインが追加されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-159">If there are any document map labels present in the report, a document outline is added to the PDF file.</span></span> <span data-ttu-id="442cf-160">各ドキュメント マップ ラベルは、ドキュメント アウトラインのエントリとして、レポートに表示される順番で表示されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-160">Each document map label appears as an entry in the document outline in the order that it appears in the report.</span></span> <span data-ttu-id="442cf-161">Acrobat で、対象のブックマークがドキュメント アウトラインに追加されるのは、そのブックマークが存在するページが表示されている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="442cf-161">In Acrobat, a target bookmark is added to the document outline only if the page it is on is rendered.</span></span>  
  
 <span data-ttu-id="442cf-162">1 ページしか表示されていない場合、ドキュメント アウトラインは追加されません。</span><span class="sxs-lookup"><span data-stu-id="442cf-162">If only a single page is rendered, no document outline is added.</span></span> <span data-ttu-id="442cf-163">ドキュメント マップは、レポート内の入れ子レベルを反映するために階層状に配置されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-163">The document map is arranged hierarchically to reflect the level of nesting in the report.</span></span> <span data-ttu-id="442cf-164">ドキュメントアウトラインは、Acrobat の [ブックマーク] タブに表示されます。ドキュメントアウトライン内のエントリをクリックすると、ドキュメントはブックマークが付けられた場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="442cf-164">The document outline is accessible in Acrobat under the Bookmarks tab. Clicking an entry within the document outline causes the document to go to the bookmarked location.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="442cf-165">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="442cf-165">Bookmarks</span></span>  
 <span data-ttu-id="442cf-166">PDF 表示では、ブックマークはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="442cf-166">Bookmarks are not supported in PDF rendering.</span></span>  
  
### <a name="drillthrough-links"></a><span data-ttu-id="442cf-167">ドリルスルー リンク</span><span class="sxs-lookup"><span data-stu-id="442cf-167">Drillthrough Links</span></span>  
 <span data-ttu-id="442cf-168">PDF 表示では、ドリルスルー リンクはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="442cf-168">Drillthrough links are not supported in PDF rendering.</span></span> <span data-ttu-id="442cf-169">ドリルスルー リンクはクリック可能なリンクとして表示されず、詳細レポートはドリルスルーの対象に接続できません。</span><span class="sxs-lookup"><span data-stu-id="442cf-169">The drillthrough links are not rendered as clickable links and drillthrough reports cannot connect to the target of the drillthrough.</span></span>  
  
### <a name="hyperlinks"></a><span data-ttu-id="442cf-170">ハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="442cf-170">Hyperlinks</span></span>  
 <span data-ttu-id="442cf-171">レポート内のハイパーリンクは、PDF ファイル内でクリック可能なリンクとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-171">Hyperlinks in reports are rendered as clickable links in the PDF file.</span></span> <span data-ttu-id="442cf-172">クリックすると、Acrobat により、既定のクライアント ブラウザーが起動し、ハイパーリンクの URL に移動できます。</span><span class="sxs-lookup"><span data-stu-id="442cf-172">When clicked, Acrobat will open the default client browser and navigate to the hyperlink URL.</span></span>  
  
  
  
##  <a name="compression"></a><a name="Compression"></a><span data-ttu-id="442cf-173">機能</span><span class="sxs-lookup"><span data-stu-id="442cf-173">Compression</span></span>  
 <span data-ttu-id="442cf-174">画像の圧縮は、画像の元のファイルの種類に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="442cf-174">Image compression is based on the original file type of the image.</span></span> <span data-ttu-id="442cf-175">PDF 表示拡張機能は、既定で PDF ファイルを圧縮します。</span><span class="sxs-lookup"><span data-stu-id="442cf-175">The PDF rendering extension compresses PDF files by default.</span></span>  
  
 <span data-ttu-id="442cf-176">PDF ファイルに含まれる画像の圧縮を可能な限り保持するために、JPEG 画像は JPEG として保存され、その他の種類の画像はすべて BMP として保存されます。</span><span class="sxs-lookup"><span data-stu-id="442cf-176">To preserve any compression for images included in the PDF file when possible, JPEG images are stored as JPEG and all other image types are stored as BMP.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="442cf-177">PDF ファイルは PNG 画像の埋め込みをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="442cf-177">PDF files don't support embedding PNG images.</span></span>  
  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="442cf-178">デバイス情報の設定</span><span class="sxs-lookup"><span data-stu-id="442cf-178">Device Information Settings</span></span>  
 <span data-ttu-id="442cf-179">デバイス情報設定を変更することによって、このレンダラーの既定の設定の一部を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="442cf-179">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="442cf-180">詳細については、「 [PDF Device Information Settings](../pdf-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="442cf-180">For more information, see [PDF Device Information Settings](../pdf-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="442cf-181">参照</span><span class="sxs-lookup"><span data-stu-id="442cf-181">See Also</span></span>  
 <span data-ttu-id="442cf-182">[Reporting Services &#40;レポートビルダーおよび SSRS&#41;での改ページ](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="442cf-182">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="442cf-183">[レポートビルダーおよび SSRS&#41;&#40;レンダリング動作](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="442cf-183">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="442cf-184">[さまざまなレポート表示拡張機能の対話機能 &#40;レポートビルダーと SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="442cf-184">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="442cf-185">[レポートビルダーおよび SSRS&#41;&#40;レポートアイテムのレンダリング](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="442cf-185">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="442cf-186">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="442cf-186">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
