---
title: 画像ファイルへのエクスポート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dc1c8539b39a99c252ebfcb0275b674f657de6c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640751"
---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a><span data-ttu-id="11bd6-102">画像ファイルへのエクスポート (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="11bd6-102">Exporting to an Image File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="11bd6-103">画像表示拡張機能では、レポートがビットマップまたはメタファイルとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="11bd6-103">The Image rendering extension renders a report to a bitmap or metafile.</span></span> <span data-ttu-id="11bd6-104">画像表示拡張機能では、既定でレポートの TIFF ファイルが生成されます。このファイルは、複数のページに表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="11bd6-104">By default, the Image rendering extension produces a TIFF file of the report, which can be viewed in multiple pages.</span></span> <span data-ttu-id="11bd6-105">クライアントは、受信した画像をイメージ ビューアーで表示したり、印刷したりできます。</span><span class="sxs-lookup"><span data-stu-id="11bd6-105">When the client receives the image, it can be displayed in an image viewer and printed.</span></span> <span data-ttu-id="11bd6-106">ここでは、画像レンダラー固有の情報を提供し、また表示規則の例外について説明します。</span><span class="sxs-lookup"><span data-stu-id="11bd6-106">This topic provides Image renderer-specific information and describes exceptions to the rendering rules.</span></span>  
  
 <span data-ttu-id="11bd6-107">画像表示拡張機能では、 [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]でサポートされている形式 (BMP、EMF、EMFPlus、GIF、JPEG、PNG、TIFF) でファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="11bd6-107">The Image rendering extension can generate files in any of the formats supported by [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]: BMP, EMF, EMFPlus, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="11bd6-108">TIFF 形式の場合、プライマリ ストリームのファイル名は *ReportName*.tif です。</span><span class="sxs-lookup"><span data-stu-id="11bd6-108">For TIFF format, the file name of the primary stream is *ReportName*.tif.</span></span> <span data-ttu-id="11bd6-109">その他の形式の場合は、1 ファイルが 1 ページに表示されます。ファイル名は *ReportName_Page.ext*</span><span class="sxs-lookup"><span data-stu-id="11bd6-109">For all other formats, which render as a single page per file, the file name is *ReportName_Page.ext* where.</span></span> <span data-ttu-id="11bd6-110">(*ext* は選択した形式のファイル拡張子) です。</span><span class="sxs-lookup"><span data-stu-id="11bd6-110">*ext* is the file extension for the chosen format.</span></span> <span data-ttu-id="11bd6-111">画像としてサポートされている別の形式でファイルを作成するには、上記の文字列のいずれかを **OutputFormatDeviceInfo** 設定で指定します。</span><span class="sxs-lookup"><span data-stu-id="11bd6-111">To produce a file in another Image-supported format, specify any of the above listed strings in the **OutputFormatDeviceInfo** setting.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="supported-image-formats"></a><a name="SupportedImageFormats"></a> <span data-ttu-id="11bd6-112">サポートされている画像形式</span><span class="sxs-lookup"><span data-stu-id="11bd6-112">Supported Image Formats</span></span>  
 <span data-ttu-id="11bd6-113">次の表は、各画像レンダラー形式のファイルの拡張子と MimeType を示しています。</span><span class="sxs-lookup"><span data-stu-id="11bd6-113">The following table shows the file extension and MimeType for each Image renderer format.</span></span>  
  
|<span data-ttu-id="11bd6-114">**Type**</span><span class="sxs-lookup"><span data-stu-id="11bd6-114">**Type**</span></span>|<span data-ttu-id="11bd6-115">**拡張子**</span><span class="sxs-lookup"><span data-stu-id="11bd6-115">**Extension**</span></span>|<span data-ttu-id="11bd6-116">**Mime**</span><span class="sxs-lookup"><span data-stu-id="11bd6-116">**MIMEType**</span></span>|  
|--------------|-------------------|------------------|  
|<span data-ttu-id="11bd6-117">BMP</span><span class="sxs-lookup"><span data-stu-id="11bd6-117">BMP</span></span>|<span data-ttu-id="11bd6-118">bmp</span><span class="sxs-lookup"><span data-stu-id="11bd6-118">bmp</span></span>|<span data-ttu-id="11bd6-119">image/bmp</span><span class="sxs-lookup"><span data-stu-id="11bd6-119">image/bmp</span></span>|  
|<span data-ttu-id="11bd6-120">GIF</span><span class="sxs-lookup"><span data-stu-id="11bd6-120">GIF</span></span>|<span data-ttu-id="11bd6-121">GIF</span><span class="sxs-lookup"><span data-stu-id="11bd6-121">gif</span></span>|<span data-ttu-id="11bd6-122">image/gif</span><span class="sxs-lookup"><span data-stu-id="11bd6-122">image/gif</span></span>|  
|<span data-ttu-id="11bd6-123">JPEG</span><span class="sxs-lookup"><span data-stu-id="11bd6-123">JPEG</span></span>|<span data-ttu-id="11bd6-124">jpeg</span><span class="sxs-lookup"><span data-stu-id="11bd6-124">jpeg</span></span>|<span data-ttu-id="11bd6-125">image/jpeg</span><span class="sxs-lookup"><span data-stu-id="11bd6-125">image/jpeg</span></span>|  
|<span data-ttu-id="11bd6-126">PNG</span><span class="sxs-lookup"><span data-stu-id="11bd6-126">PNG</span></span>|<span data-ttu-id="11bd6-127">png</span><span class="sxs-lookup"><span data-stu-id="11bd6-127">png</span></span>|<span data-ttu-id="11bd6-128">image/png</span><span class="sxs-lookup"><span data-stu-id="11bd6-128">image/png</span></span>|  
|<span data-ttu-id="11bd6-129">TIFF</span><span class="sxs-lookup"><span data-stu-id="11bd6-129">TIFF</span></span>|<span data-ttu-id="11bd6-130">tif</span><span class="sxs-lookup"><span data-stu-id="11bd6-130">tif</span></span>|<span data-ttu-id="11bd6-131">image/tiff</span><span class="sxs-lookup"><span data-stu-id="11bd6-131">image/tiff</span></span>|  
|<span data-ttu-id="11bd6-132">EMF</span><span class="sxs-lookup"><span data-stu-id="11bd6-132">EMF</span></span>|<span data-ttu-id="11bd6-133">EMF</span><span class="sxs-lookup"><span data-stu-id="11bd6-133">emf</span></span>|<span data-ttu-id="11bd6-134">image/emf</span><span class="sxs-lookup"><span data-stu-id="11bd6-134">image/emf</span></span>|  
|<span data-ttu-id="11bd6-135">EMFPlus</span><span class="sxs-lookup"><span data-stu-id="11bd6-135">EMFPlus</span></span>|<span data-ttu-id="11bd6-136">EMF</span><span class="sxs-lookup"><span data-stu-id="11bd6-136">emf</span></span>|<span data-ttu-id="11bd6-137">image/emf</span><span class="sxs-lookup"><span data-stu-id="11bd6-137">image/emf</span></span>|  
  
  
##  <a name="rendering-multiple-pages"></a><a name="RenderingMultiplePages"></a> <span data-ttu-id="11bd6-138">複数ページの表示</span><span class="sxs-lookup"><span data-stu-id="11bd6-138">Rendering Multiple Pages</span></span>  
 <span data-ttu-id="11bd6-139">1 つのファイルで複数のページのドキュメントをサポートしているファイル形式は TIFF だけです。</span><span class="sxs-lookup"><span data-stu-id="11bd6-139">TIFF is the only format that supports multiple page documents in a single file.</span></span> <span data-ttu-id="11bd6-140">JPG や PNG などの他の形式では、一度に出力できるのは 1 ページで、ページごとに表示拡張機能を個別に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="11bd6-140">Other formats, such as JPG or PNG, output one page at a time and require a separate call to the rendering extension for each page.</span></span>  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="11bd6-141">双</span><span class="sxs-lookup"><span data-stu-id="11bd6-141">Interactivity</span></span>  
 <span data-ttu-id="11bd6-142">このレンダラーで生成されたすべての画像形式では、対話機能がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="11bd6-142">Interactivity is not supported in any Image formats generated by this renderer.</span></span> <span data-ttu-id="11bd6-143">次の対話型要素は表示されません。</span><span class="sxs-lookup"><span data-stu-id="11bd6-143">The following interactive elements are not rendered:</span></span>  
  
-   <span data-ttu-id="11bd6-144">ハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="11bd6-144">Hyperlinks</span></span>  
  
-   <span data-ttu-id="11bd6-145">表示/非表示</span><span class="sxs-lookup"><span data-stu-id="11bd6-145">Show or Hide</span></span>  
  
-   <span data-ttu-id="11bd6-146">ドキュメント マップ</span><span class="sxs-lookup"><span data-stu-id="11bd6-146">Document Map</span></span>  
  
-   <span data-ttu-id="11bd6-147">ドリルスルー リンクまたはクリックスルー リンク</span><span class="sxs-lookup"><span data-stu-id="11bd6-147">Drillthrough or clickthrough links</span></span>  
  
-   <span data-ttu-id="11bd6-148">エンド ユーザー並べ替え</span><span class="sxs-lookup"><span data-stu-id="11bd6-148">End user sort</span></span>  
  
-   <span data-ttu-id="11bd6-149">固定ヘッダー</span><span class="sxs-lookup"><span data-stu-id="11bd6-149">Fixed headers</span></span>  
  
-   <span data-ttu-id="11bd6-150">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="11bd6-150">Bookmarks</span></span>  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="11bd6-151">デバイス情報の設定</span><span class="sxs-lookup"><span data-stu-id="11bd6-151">Device Information Settings</span></span>  
 <span data-ttu-id="11bd6-152">デバイス情報設定を変更することによって、このレンダラーの既定の設定の一部を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="11bd6-152">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="11bd6-153">詳細については、「 [画像デバイス情報設定](../image-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11bd6-153">For more information, see [Image Device Information Settings](../image-device-information-settings.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="11bd6-154">参照</span><span class="sxs-lookup"><span data-stu-id="11bd6-154">See Also</span></span>  
 <span data-ttu-id="11bd6-155">[Reporting Services &#40;レポートビルダーおよび SSRS&#41;での改ページ](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11bd6-155">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="11bd6-156">[レポートビルダーおよび SSRS&#41;&#40;レンダリング動作](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11bd6-156">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="11bd6-157">[さまざまなレポート表示拡張機能の対話機能 &#40;レポートビルダーと SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="11bd6-157">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="11bd6-158">[レポートビルダーおよび SSRS&#41;&#40;レポートアイテムのレンダリング](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11bd6-158">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="11bd6-159">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="11bd6-159">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
